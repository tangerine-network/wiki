## Content

- [Contract Write Function](#contract-write-function)
- [Contract Read Function](#contract-read-function)

## Contract Write function 
In this section, we briefly introduce some functions that Tangerine governance provides to write in.

### Register
1. In Tangerine wallet, switch to the `owner's account`.
2. Navigate to the `Write` tab of the governance contract and select `register` from the dropdown menu.
3. Fill in the information like below; currently, you need 1M TAN to run a BP node.
  - Node Public Key (you must hold the corresponding secret key)
  - Name of the node
  - Contact email
  - Node Location
  - Website URL 
4. Click `Send` and `confirm` in Tangerine wallet.

### Pay Fine
1. In Tangerine wallet, switch to the account to pay the fine (it doesn't has to be the owner of that node)
2. Navigate to the `Write tab of the governance contract and select `payFine` from the dropdown menu.
3. Fill in the amount of fine to pay, and the address of that node.
4. Click `Send` and `confirm` in Tangerine wallet.

> NOTE: Don't worry to over pay the fine, the transaction would succeed when the amount you pay matches the fine of that node.

### Stake/Unstake
After registering, each node owner can continue depositing more stake into Tangerine governance contract.  This is super easy to achieve in Tangerine governance contract. 
 1. Switch to the `owner account` in Tangerine wallet. 
 2. Navigate to the `Write` tab and select `stake` from the dropdown menu.
 3. Fill the amount of stake in the contract.
 4. Click `Send` and `confirm` in Tangerine wallet.

On the other hand, each node owner can also unstake from Tangerine governance contract. This is almost identical to operating stake function.
 1. Switch to the `owner account` in Tangerine wallet.
 2. Navigate to the `Write` tab and select `unstake` from the dropdown menu.
 3. Fill the amount of unstake in the contract.
 4. Click `Send` and `confirm` in Tangerine wallet.

To ensure the stability of Tangerine blockchain, the duration to withdraw the unstake coin is set 24 epochs, which corresponds around 1 day in real-world time. In the duration, the node can still propose block and earn the reward, but the node sill can be fined if violating any rule.
Note that, each node can only unstake once until the unstake is withdrawn.

### Withdraw
After unstaking and wait for 24 epochs, the node can withdraw the stake.
 1. Switch to the `owner account` in Tangerine wallet.
 2. Navigate to the `Write` tab and select `withdraw` from the dropdown menu.
 3. Click `Send` and `confirm` in Tangerine wallet.

### Transfer Node Owner 
A node owner can also transfer the owner right to others. 
 1. Switch to the `owner account` in Tangerine wallet. 
 2. Navigate to the `Write` tab and select `TransferNodeOwnership` from the dropdown menu.
 3. Fill the `address` of the new owner.
 4. Click `Send` and `confirm` in Tangerine wallet.

> WARNING: This is an IRREDUCIBLE operation. No one can recover if you transfer to a wrong address. Please double-check the address is correct.

## Contract Read function
<!-- Most of the information can be found in Tangerine Garden website. To prevent in case, we introduce a method to read the status of Tangerine blockchain. -->

The latest system parameters can be found in the governance contract. We introduce some fruquently used functions.

### nodes
`nodes` returns the status of a node, where the input is the order of the node. The order of a node can be query by the function `nodesOffsetByAddress`.

### nodeLength
`nodeLength` returns the current size of the node set.

### nodesOffsetByAddress
`nodesOffsetByAddress` returns the order of a node, where the input is the address of the node.

### minStake
`minStake` returns the minimum stake required to join the node set.