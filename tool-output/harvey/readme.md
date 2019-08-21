# Steps for Running the Harvey Fuzzer

## Install and start Ganache CLI

```
$ npm install -g windows-build-tools (optional)
$ npm install -g ganache-cli
$ ganache-cli -a=1
```

You will need to keep Ganache CLI running in the background for the steps below.


## Set up and deploy Panvala contracts

```
$ cd panvala/governance-contracts
$ vi package.json (see diff output below for changes)
$ vi truffle-config.js (see diff output below for changes)
$ git diff
diff --git a/governance-contracts/package.json b/governance-contracts/package.json
index 933afc9..a0d01bd 100644
--- a/governance-contracts/package.json
+++ b/governance-contracts/package.json
@@ -10,10 +10,10 @@
         "compile": "yarn sol-lint && truffle compile",
         "coverage": "solidity-coverage",
         "lint": "eslint",
-        "migrate": "truffle migrate",
+        "migrate": "truffle migrate --network harvey",
         "sol-lint": "solhint ./contracts/**/*.sol",
         "fix": "eslint --fix ./",
-        "test": "yarn lint ./ && truffle test"
+        "test": "truffle test"
     },
     "author": "",
     "license": "ISC",
diff --git a/governance-contracts/truffle-config.js b/governance-contracts/truffle-config.js
index 5b3b6a2..c4346a5 100644
--- a/governance-contracts/truffle-config.js
+++ b/governance-contracts/truffle-config.js
@@ -63,7 +63,7 @@ module.exports = {
     // tab if you use this network and you must also set the `host`, `port` and `network_id`
     // options below to some value.
     //
-    development: {
+    harvey: {
       host: '127.0.0.1', // Localhost (default: none)
       port: 8545, // Standard Ethereum port (default: none)
       network_id: '*', // Any network (default: none)
$ yarn install
$ yarn migrate
```

If the last command is successful its output should include the address of each deployed
contract. We will need this later.


## Generate analysis configuration

Now, we will use a [Python script](https://github.com/ConsenSys/generate-harvey-config) to
connect to the running Ganache CLI instance. The script will collect all the transactions
to generate an analysis configuration for the fuzzer. Please follow the installation
instructions from its readme.

```
$ python generate-harvey-config.py > panvala-config.json
```

This produces a JSON file that you need to edit. Most importantly, you need to edit the
field `address-under-test` by filling in the address at which the contract was deployed
(see output from `yarn migrate` above).

Additionally, you will probably want to edit the time limit. I would recommend 28800
(secs) for longer fuzzing campaigns and 3600 (secs) for short ones.


## Run Harvey fuzzer

You will need to install the [Harvey CLI](https://github.com/ConsenSys/harvey-cli). Please
follow the installation instructions from its readme.

```
$ cat panvala-config.json | harvey-cli > harvey-output.json
```

This will generate a report with all the issues that Harvey detected.

## Check functional properties with Harvey

You may want to encode additional functional properties in the code such that they can be
checked automatically by Harvey. Here is a small example:

```
pragma solidity ^0.5.0;

import "openzeppelin-solidity/contracts/token/ERC20/ERC20.sol";
import "openzeppelin-solidity/contracts/token/ERC20/ERC20Detailed.sol";

contract BasicToken is ERC20, ERC20Detailed {
    constructor(string memory _name, string memory _symbol, uint8 _decimals, uint _initialSupply)
        public
        ERC20Detailed(_name, _symbol, _decimals)
    {
        // Creator gets the initial supply
        _mint(msg.sender, _initialSupply);
    }

    event AssertionFailed(string message);

    function Double(uint256 x) public returns (uint256) {
        uint256 res = 2*x;
        if (res < x) {
            emit AssertionFailed("postcondition of Double failed");
        }
        return res;
    }

    int256 private x;
    function IncrX(int256 amount) public {
        x += amount;
    }

    function CheckInvariant() public {
        if (x < 0) {
            emit AssertionFailed("x is less than 0");
        }
        if (42 < x) {
            emit AssertionFailed("x is greater than 42");
        }
    }
}
```

Harvey will report any assertion violation (in other words, a reachable invalid opcode on
the EVM-level) that it is able to trigger. However, the compiler inserts such assertions
for many constructs and you might want to only focus on ones you add explicitly.  To
support this use case, Harvey reports a more detailed and specific issue when reaching an
instruction that emits a `AssertionFailed(string message)` event. You can easily use the
message to identify the location in the source code. In the above example, we use it to
check an assertion/postcondition for function `Double` and an invariant in function
`CheckInvariant`.

Harvey will detect all three property violation and report them as follows:

```
...
        {
            "swc-id": "SWC-110",
            "title": "assertion failed",
            "details": "A user-provided assertion failed with message 'postcondition of Double failed'. Make sure the user-provided assertion is correct.",
            "code-hash": "0x7f91bb961e848f8f85e08b7f3574f0598cc7f045dcb442e2f56effc516979a25",
            "function-signature": "4235ca4b",
            "bytecode-offset": 1757,
            "stack-trace": [],
            "time-secs": 75.3449932,
            "test-case": {
...
        {
            "swc-id": "SWC-110",
            "title": "assertion failed",
            "details": "A user-provided assertion failed with message 'x is greater than 42'. Make sure the user-provided assertion is correct.",
            "code-hash": "0x7f91bb961e848f8f85e08b7f3574f0598cc7f045dcb442e2f56effc516979a25",
            "function-signature": "85ddff02",
            "bytecode-offset": 2006,
            "stack-trace": [],
            "time-secs": 140.9781851,
            "test-case": {
...
        {
            "swc-id": "SWC-110",
            "title": "assertion failed",
            "details": "A user-provided assertion failed with message 'x is less than 0'. Make sure the user-provided assertion is correct.",
            "code-hash": "0x7f91bb961e848f8f85e08b7f3574f0598cc7f045dcb442e2f56effc516979a25",
            "function-signature": "85ddff02",
            "bytecode-offset": 1898,
            "stack-trace": [],
            "time-secs": 541.3610103,
            "test-case": {
...
```
