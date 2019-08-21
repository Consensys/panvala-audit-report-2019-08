# Solium Report

**Note**: Solium does not appear to handle the return value extraction in `Gatekeeper.sol:561`.

```solidity
    (
        address[] memory resources,
        uint[] memory firstChoices,
        uint[] memory secondChoices
    ) = abi.decode(_ballots[i], (address[], uint[], uint[]));
```

```
$ solium --version                                                                                                 Solium version 1.2.4

$ solium -d governance-contracts/contracts

governance-contracts/contracts/Gatekeeper.sol
  205:23    warning    Avoid using 'now' (alias to 'block.timestamp').                            security/no-block-members
  235:16    warning    Avoid using 'now' (alias to 'block.timestamp').                            security/no-block-members
  300:16    warning    Avoid using 'now' (alias to 'block.timestamp').                            security/no-block-members
  316:29    warning    Avoid using 'now' (alias to 'block.timestamp').                            security/no-block-members
  491:28    warning    Avoid using 'now' (alias to 'block.timestamp').                            security/no-block-members
  560:12    warning    Line contains trailing whitespace                                          no-trailing-whitespace
  564:12    warning    Line contains trailing whitespace                                          no-trailing-whitespace
  627:16    error      Only use indent of 12 spaces.                                              indentation
  633:20    warning    Avoid using 'now' (alias to 'block.timestamp').                            security/no-block-members
  751:8     warning    Assignment operator must have exactly single space on both sides of it.    operator-whitespace
  964:47    warning    Avoid using 'now' (alias to 'block.timestamp').                            security/no-block-members
  985:28    warning    Avoid using 'now' (alias to 'block.timestamp').                            security/no-block-members

governance-contracts/contracts/TokenCapacitor.sol
  98:25     warning    Avoid using 'now' (alias to 'block.timestamp').    security/no-block-members
  247:11    error      Only use indent of 12 spaces.                      indentation
  248:11    error      Only use indent of 12 spaces.                      indentation
  250:11    error      Only use indent of 12 spaces.                      indentation
  258:11    error      Only use indent of 12 spaces.                      indentation
  292:28    warning    Avoid using 'now' (alias to 'block.timestamp').    security/no-block-members

governance-contracts/contracts/dev/UpgradedGatekeeper.sol
  91:11    error    Only use indent of 12 spaces.    indentation
  92:11    error    Only use indent of 12 spaces.    indentation
  97:0     error    Only use indent of 12 spaces.    indentation
  99:11    error    Only use indent of 12 spaces.    indentation
  104:0    error    Only use indent of 12 spaces.    indentation

✖ 10 errors, 13 warnings found.
```

# Solhint Report

```
$ solhint --version

2.0.0-alpha.3

$ solhint governance-contracts/contracts/*.sol  

governance-contracts/contracts/Gatekeeper.sol
  751:9   error  Expected indentation of 12 spaces but found 8  indent
  753:9   error  Expected indentation of 12 spaces but found 8  indent
  754:9   error  Expected indentation of 12 spaces but found 8  indent
  755:9   error  Expected indentation of 12 spaces but found 8  indent
  756:9   error  Expected indentation of 12 spaces but found 8  indent
  757:9   error  Expected indentation of 12 spaces but found 8  indent
  758:9   error  Expected indentation of 12 spaces but found 8  indent
  759:9   error  Expected indentation of 12 spaces but found 8  indent
  760:5   error  Expected indentation of 8 spaces but found 4   indent
  810:12  error  Indentation is incorrect                       indent

governance-contracts/contracts/TokenCapacitor.sol
  247:12  error  Expected indentation of 12 spaces but found 11  indent
  248:12  error  Expected indentation of 12 spaces but found 11  indent
  250:12  error  Expected indentation of 12 spaces but found 11  indent
  253:12  error  Expected indentation of 12 spaces but found 11  indent
  255:16  error  Expected indentation of 16 spaces but found 15  indent
  256:12  error  Expected indentation of 12 spaces but found 11  indent
  258:12  error  Expected indentation of 12 spaces but found 11  indent

✖ 17 problems (17 errors, 0 warnings)
```