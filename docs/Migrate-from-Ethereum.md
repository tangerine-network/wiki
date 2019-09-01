# Migrate from Ethereum

Tangerine's version of EVM is almost the same as the original EVM, therefore Tangerine version of Solidity is almost the same as the original Solidity. If you have built a smart contract on Ethereum, you can usually deploy the exact same contract onto Tangerine without any modification.

However, there are still some minor differences between the Tangerine's version of Solidity and its Ethereum counterpart to look out for, as listed below:

## Gas Limit

In Tangerine, **there is no unspent gas**.

If the actual execution of a transaction costs less gas than the set amount, **you still have to pay for the gas amount you've set**. So please set the gas amount wisely.

The reason for this is that in Tangerine, transaction are not executed at the time they get packed into a block. So the number of transactions that can get into a block depends on the gas amount set in the transactions, not the actual gas amount consumed while executing the transactions.

## On-Chain Random Oracle

This is more of an additional feature than Ethereum's EVM.

Tangerine provides [On-chain Random Oracle](On-Chain-Random-Oracle.md). This means you can get unbiased random seeds in your smart contract easily and at low cost.

Here's a simple Solidity smart contract that utilizes Tangerine's on-chain randomness,
```
pragma solidity ^0.5.2;

import "github.com/byzantine-lab/tangerine-random-lib/RandomLib.sol";

contract Hello {
    uint256 public value;

    event UpdateNumber(uint256 _value);

    function update() public {
        value = Random.rand();
        emit UpdateNumber(value);
    }

    function get() public view returns (uint256) {
        return value;
    }
}
```
The `Random.rand()` function call used in the contract gives you the random seed generated from the threshold signature of a group of block producing nodes.
