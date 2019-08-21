## Sūrya's Description Report

### Files Description Table


|  File Name  |  SHA-1 Hash  |
|-------------|--------------|
| contracts/Gatekeeper.sol | cf1dafb4152218ec6a3f2994001e365c2cc3b389 |
| contracts/TokenCapacitor.sol | 0a8ed87547ae9066653c18257dd560bf378ed1c1 |
| contracts/ParameterStore.sol | 55982f874178099408caf589338851b517cf3096 |


### Contracts Description Table


|  Contract  |         Type        |       Bases      |                  |                 |
|:----------:|:-------------------:|:----------------:|:----------------:|:---------------:|
|     └      |  **Function Name**  |  **Visibility**  |  **Mutability**  |  **Modifiers**  |
||||||
| **Gatekeeper** | Implementation |  |||
| └ | \<Constructor\> | Public ❗️ | 🛑  | |
| └ | currentEpochNumber | Public ❗️ |   |NO❗️ |
| └ | epochStart | Public ❗️ |   |NO❗️ |
| └ | recommendSlate | Public ❗️ | 🛑  |NO❗️ |
| └ | slateRequests | Public ❗️ |   |NO❗️ |
| └ | stakeTokens | Public ❗️ | 🛑  |NO❗️ |
| └ | withdrawStake | Public ❗️ | 🛑  |NO❗️ |
| └ | depositVoteTokens | Public ❗️ | 🛑  |NO❗️ |
| └ | withdrawVoteTokens | Public ❗️ | 🛑  |NO❗️ |
| └ | delegateVotingRights | Public ❗️ | 🛑  |NO❗️ |
| └ | commitBallot | Public ❗️ | 🛑  |NO❗️ |
| └ | didCommit | Public ❗️ |   |NO❗️ |
| └ | getCommitHash | Public ❗️ |   |NO❗️ |
| └ | revealBallot | Public ❗️ | 🛑  |NO❗️ |
| └ | revealManyBallots | Public ❗️ | 🛑  |NO❗️ |
| └ | getFirstChoiceVotes | Public ❗️ |   |NO❗️ |
| └ | getSecondChoiceVotes | Public ❗️ |   |NO❗️ |
| └ | didReveal | Public ❗️ |   |NO❗️ |
| └ | finalizeContest | Public ❗️ | 🛑  |NO❗️ |
| └ | contestStatus | Public ❗️ |   |NO❗️ |
| └ | contestSlates | Public ❗️ |   |NO❗️ |
| └ | contestDetails | External ❗️ |   |NO❗️ |
| └ | finalizeRunoff | Public ❗️ | 🛑  |NO❗️ |
| └ | donateChallengerStakes | Public ❗️ | 🛑  |NO❗️ |
| └ | rejectSlates | Private 🔐 | 🛑  | |
| └ | getWinningSlate | Public ❗️ |   |NO❗️ |
| └ | requestPermission | Public ❗️ | 🛑  |NO❗️ |
| └ | acceptSlate | Private 🔐 | 🛑  | |
| └ | hasPermission | Public ❗️ |   |NO❗️ |
| └ | slateSubmissionDeadline | Public ❗️ |   |NO❗️ |
| └ | commitPeriodActive | Private 🔐 |   | |
||||||
| **TokenCapacitor** | Implementation |  |||
| └ | \<Constructor\> | Public ❗️ | 🛑  | |
| └ | _gatekeeper | Private 🔐 |   | |
| └ | createProposal | Public ❗️ | 🛑  |NO❗️ |
| └ | createManyProposals | Public ❗️ | 🛑  |NO❗️ |
| └ | withdrawTokens | Public ❗️ | 🛑  |NO❗️ |
| └ | donate | Public ❗️ | 🛑  |NO❗️ |
| └ | projectedUnlockedBalance | Public ❗️ |   |NO❗️ |
| └ | projectedLockedBalance | Public ❗️ |   |NO❗️ |
| └ | calculateDecay | Public ❗️ |   |NO❗️ |
| └ | updateBalancesUntil | Public ❗️ | 🛑  |NO❗️ |
| └ | updateBalances | Public ❗️ | 🛑  |NO❗️ |
||||||
| **ParameterStore** | Implementation |  |||
| └ | \<Constructor\> | Public ❗️ | 🛑  | |
| └ | init | Public ❗️ | 🛑  |NO❗️ |
| └ | get | Public ❗️ |   |NO❗️ |
| └ | getAsUint | Public ❗️ |   |NO❗️ |
| └ | getAsAddress | Public ❗️ |   |NO❗️ |
| └ | set | Private 🔐 | 🛑  | |
| └ | setInitialValue | Public ❗️ | 🛑  |NO❗️ |
| └ | createProposal | Public ❗️ | 🛑  |NO❗️ |
| └ | createManyProposals | Public ❗️ | 🛑  |NO❗️ |
| └ | setValue | Public ❗️ | 🛑  |NO❗️ |
| └ | _gatekeeper | Private 🔐 |   | |


### Legend

|  Symbol  |  Meaning  |
|:--------:|-----------|
|    🛑    | Function can modify state |
|    💵    | Function is payable |
