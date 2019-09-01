# Exchange Integration Guide

This guide provides all the necessary details for integrating Tangerine with your exchange.

## Wallet
Tangerine TX signature algorithm is exactly the same as Ethereum (secp256k1), you can use existing Ethereum wallet with Tangerine.

## RPC
Tangerine RPC is compatible with Ethereum. In theory, you can use existing Ethereum module with Tangerine by replacing the RPC endpoint:

|Network|RESTful|WebSocket|Chain ID|
|---|---|---|---|
|Mainnet|https://mainnet-rpc.tangerine-network.io|wss://mainnet-rpc.tangerine-network.io/ws|373|
|Testnet|https://testnet-rpc.tangerine-network.io|wss://testnet-rpc.tangerine-network.io/ws|374|

Since Tangerine produce around 1 block per second, it may incur a heavier load on your database infrastructure. Make sure you have enough DB instance to handle the load.

## Starting a RPC Node

Refer to [Running a RPC node](RPC-Node-Operation-Guide.md) for instructions to launch a RPC node by yourself.

## Deposit Confirmation

Tangerine consensus algorithm has explicit finality, meaning you only need to wait for **1 block confirmation** to credit the deposit. If you really want to make sure, you can wait for 2 confirmations to be sure.

## Explorer

Explorer link is as follows:

|Network|Explorer|
|---|---|
|Mainnet|https://tangerine.garden|
|Testnet|https://testnet.tangerine.garden|
