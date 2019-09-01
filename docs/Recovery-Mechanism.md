# Recovery Mechanism

Tangerine's automatic recovery mechanism will kick in in the catastrophic event that complete Tangerine Network shutdown to ensure Tangerine can still reach consensus even without Tangerine consensus algorithm.

Nodes in the last notary set will vote on the external decentralized blockchain to determine which block height to be the point of recovery. Once a particular block height `h` has more than half of the notary set voted, the recovery consensus is reached. Block height of `h+1` will be an empty block and Tangerine consensus algorithm will continue running at height `h+2`.
