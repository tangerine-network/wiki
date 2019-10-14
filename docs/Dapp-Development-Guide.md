# DApp Development Guide

> #### Migrate from Ethereum
> If you have already developed DApps on Ethereum, you can skip to [Migrate from Ethereum](Migrate-DApp-from-Ethereum.md) and learn what the differences between Tangerine and Ethereum are.

## Introduction

DApps are decentralized applications built on top of blockchain platforms like Tangerine or Ethereum. At the heart of every DApps are smart contracts. Smart contracts are programs compiled into VM bytecode and deployed onto the blockchain platform.

After deployment, a smart contract resides on an address, just like any other regular account. Everyone in the system can interact with the smart contract by sending transactions to the contract address.

Currently, Tangerine uses the same account system as Ethereum. Tangerine also has its default VM built from VM Ethereum's virtual machine (EVM). So DApp development on Tangerine is *almost* the same as on Ethereum.

Some special functions are provided through precompiled contract, e.g on chain randomness.

To use the on chain randomess feature, please see the read me of [Tangerine Network RNG Library](https://github.com/tangerine-network/random-lib)

## Solidity

The most commonly used language to develop a Tangerine/Ethereum DApp is Solidity, which we will introduce briefly in the [next section](Solidity.md).

Tangerine's version of EVM is almost the same as the original EVM, therefore Tangerine version of Solidity is almost the same as the original Solidity. If you have built a smart contract on Ethereum, you can usually deploy the exact same contract onto Tangerine without any modification.

However, there are still some minor differences between the Tangerine's version of Solidity and its Ethereum counterpart, because of the boost in performance and the [On-chain Random Oracle](On-Chain-Random-Oracle.md) that Tangerine provides. We will cover these differences in [Migrate from Ethereum](Migrate-from-Ethereum.md).

## Remix IDE

[Remix](https://remix.dxn.ninja) is a web-based integrated development environment, built for Tangerine.

With Remix IDE, you can develop, compile, deploy and debug your smart contracts easily from the same interface.

## Truffle

If you are developing apps with truffle, all you need to do as add the following network config into your truffle config:

```
  networks: {
    ...
    "tangerine-mainnet": {
      network_id: 373,
      gasPrice: 24e9,
      provider: function() {
        return new HDWalletProvider(mnemonic, "https://mainnet-rpc.tangerine-network.io");
      },
    },
    "tangerine-testnet": {
      network_id: 374,
      gasPrice: 24e9,
      provider: function() {
        return new HDWalletProvider(mnemonic, "https://testnet-rpc.tangerine-network.io");
      },
    },
  }
```

## Interact With Smart Contracts

Once you have deployed your smart contracts on chain, the next step is to interact with your contract from your UI, which can either be a web app or a native mobile app. [This section](Interact-with-Contracts.md) shows you how it's done.

## Tools and Libraries

Tangerine provides a wide range of tools and libraries for DApp development, listed [HERE](Tools-and-Libraries.md).
