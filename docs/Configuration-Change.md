# Configuration Change

## Overview
The configuration for Tangerine is round based configuration, which is allowed to be changed and applied in upcoming rounds on the fly without shutting down or forking the system. 
Each configuration will become effective two rounds after updating. Configurable parameters including:
- MinStake: minimum stake required for becoming a bp.
- LockupPeriod: time required for funds available for withdrawing after unstake.
- MinGasPrice: minimum gas price.
- LambdaBA, LambdaDKG: period for each step for Tangerine Byzantine Agreement and Tangerine DKG protocol.
- NotaryParamAlpha, NotaryParamBeta: parameter for calculating notary set size. Refer to [Selection of notary set size](Selection-of-the-notary-set-size.md).
- RoundLength: the number of blocks in a round.
- MinBlockInterval: the minimum interval of timestamps between blocks on the blockchain.
- FineValues: penalty for not following protocol. Refer to [Rule for the Tangerine node set](Rule-for-the-node-set.md).

