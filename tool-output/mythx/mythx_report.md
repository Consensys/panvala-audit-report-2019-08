# MythX Analysis Results

## ParameterStore

```
Reading contract all_flat.sol... done
Compiling with Solidity version: v0.5.0+commit.1d4f565a
(node:26893) V8: soljson-v0.5.0+commit.1d4f565a.js:3 Invalid asm.js: Invalid member of stdlib
 ›   Warning: all_flat.sol:1084:1: Warning: Experimental features are turned on. Do not use experimental features on live deployments.
 ›   pragma experimental ABIEncoderV2;
 ›   ^-------------------------------^
 ›
Compiling contract all_flat.sol... done
Analyzing contract ParameterStore... done

UUID: d831af18-d8eb-4474-9ee7-25b621f68fd9
API Version: v1.4.28.4
Harvey Version: 0.0.27
Maestro Version: 1.2.16
Maru Version: 0.4.8
Mythril Version: 0.21.12

Report found: 0 issues
Covered instructions: undefined
Covered paths: undefined
Selected compiler version: vUnknown

Covered instructions: 3407
Covered paths: 134
Selected compiler version: vundefined

Title: (SWC-101) Integer Overflow and Underflow
Severity: High
Head: integer overflow
Description: An arithmetic operation led to an integer overflow. Since this is often not intended, make sure you take appropriate precautions when performing arithmetic operations.
Source code:

all_flat.sol 12:33
--------------------------------------------------
d integers, reverts on overflo
--------------------------------------------------

==================================================
```

## TokenCapacitor

```
Reading contract TokenCapacitor.sol... done
Compiling with Solidity version: v0.5.0+commit.1d4f565a
(node:17689) V8: soljson-v0.5.0+commit.1d4f565a.js:3 Invalid asm.js: Invalid member of stdlib
 ›   Warning: ParameterStore.sol:2:1: Warning: Experimental features are turned on. Do not use experimental features on live deployments.
 ›   pragma experimental ABIEncoderV2;
 ›   ^-------------------------------^
 ›
 ›   Warning: TokenCapacitor.sol:2:1: Warning: Experimental features are turned on. Do not use experimental features on live deployments.
 ›   pragma experimental ABIEncoderV2;
 ›   ^-------------------------------^
 ›
 ›   Warning: Gatekeeper.sol:2:1: Warning: Experimental features are turned on. Do not use experimental features on live deployments.
 ›   pragma experimental ABIEncoderV2;
 ›   ^-------------------------------^
 ›
Compiling contract TokenCapacitor.sol... done
Analyzing contract TokenCapacitor... done

UUID: d3787b3f-3172-4290-870d-10dcc9666e65
API Version: v1.4.28.4
Harvey Version: 0.0.27
Maestro Version: 1.2.16
Maru Version: 0.4.8
Mythril Version: 0.21.11

Report found: 0 issues
Covered instructions: 0
Covered paths: 0
Selected compiler version: vUnknown

Done
```

## Gatekeeper

```
Reading contract Gatekeeper.sol... done
Compiling with Solidity version: v0.5.0+commit.1d4f565a
(node:17610) V8: soljson-v0.5.0+commit.1d4f565a.js:3 Invalid asm.js: Invalid member of stdlib
 ›   Warning: ParameterStore.sol:2:1: Warning: Experimental features are turned on. Do not use experimental features on live deployments.
 ›   pragma experimental ABIEncoderV2;
 ›   ^-------------------------------^
 ›
 ›   Warning: TokenCapacitor.sol:2:1: Warning: Experimental features are turned on. Do not use experimental features on live deployments.
 ›   pragma experimental ABIEncoderV2;
 ›   ^-------------------------------^
 ›
 ›   Warning: Gatekeeper.sol:2:1: Warning: Experimental features are turned on. Do not use experimental features on live deployments.
 ›   pragma experimental ABIEncoderV2;
 ›   ^-------------------------------^
 ›
Compiling contract Gatekeeper.sol... done
Analyzing contract Gatekeeper... done

UUID: 6aa048de-a7d0-445f-8bbe-6909aaeafa47
API Version: v1.4.28.4
Harvey Version: 0.0.27
Maestro Version: 1.2.16
Maru Version: 0.4.8
Mythril Version: 0.21.11

Report found: 0 issues
Covered instructions: undefined
Covered paths: undefined
Selected compiler version: vUnknown

Covered instructions: 0
Covered paths: 0
Selected compiler version: vundefined

Done
```
