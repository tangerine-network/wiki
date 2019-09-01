# Rules for the Tangerine Network node set

We introduce the rule for node set and give a brief explanation to the functions in Tangerine Network [governance contract](https://testnet.tangerine.garden/address/0x246FcDE58581e2754f215A523C0718C4BFc8041Fj).


## Active condition (permission to be in notary set)
  You must deposit enough stake in the governance contract to get the qualification to be selected in the notary set.
  Sometimes nodes who violate the rule for notary set will be fined some coin. This leads nodes unqualified to be selected in the notary set. Nodes can be re-qualify after paying the fine.

## Reward
  The reward of each block is calculated as

    block_Reward = mining_Velocity * total_Staked * round_Interval / (365*24*60*60)

  For example, 100 nodes with each staked 1M TAN and mining velocity is 18.75%, the reward of each block is

    100 * 1M * 18.75% * 1 / (365*24*60*60) = 0.5945586 TAN

  You can find the parameter information via [governance statistic](https://testnet.tangerine.garden/governance) page.

  From the description above, the expected reward for each node in 1 day is

    100 * 1M * 18.75% * 1 / 365 /100 = 513.7 TAN

## Penalty
Nodes shall not engage in any of the following conducts:

1. Forking or trying to fork blocks at the same height by proposing multiple blocks
2. Forking or trying to fork votes by submitting multiple votes in the same iteration in the Byzantine Agreement (BA)
3. Engaging in malicious behaviors in Distributed Key Generation, including without limitation sending wrong secret shares to other nodes, and such behaviors have been complained by other nodes
4. Producing wrong Share-Sig by sending wrong share signature to common reference string (CRS) or in commit-vote
5. Failing to finish distributed key generation (DKG)
6. Failing to propose any blocks during a whole epoch

For 1. to 4., the entire stake will be confiscated immediately by Tangerine Network. For 5., a fine of the `1 TAN` will be imposed and no blocks can be produced until such fine is paid under the governance contract.  For 6., a fine of the `100 TAN` will be imposed and no blocks can be produced until such fine is paid under the governance contract.
<!--- Block Reward*86400/total Node --->

Nodes can pay the fine in the governance contract, see [payFine](Governance-Contract.md#pay-fine).

## Recovery
Currently, Tangerine Network's [recovery](Recovery-Mechanism.md) is built on top of the Ethereum mainnet. All nodes are required to deposit at least **5 Ether** to the same node address. Ether used for recovery will be returned after Tangerine Network successfully recovered. However, if Tangerine Network failed to recover and result in a hard fork, the stakes of nodes that did not deposit enough amount of Ether will be confiscated.
