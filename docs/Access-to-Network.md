# Access Tangerine Network

There are a few options on how to access Tangerine networks. The first is to use the public Tangerine RPC endpoint, the second one is to run a fullnode and sync the fullnode locally.

## Public RPC Endpoints

The public RPC endpoints are available at:

|Network|RESTful|WebSocket|Chain ID|
|---|---|---|---|
|Mainnet|https://mainnet-rpc.tangerine-network.io|wss://mainnet-rpc.tangerine-network.io/ws|411|
|Testnet|https://testnet-rpc.tangerine-network.io|wss://testnet-rpc.tangerine-network.io/ws|374|

Point your Tangerine/Ethereum client to this RPC endpoint and you should be able to read from and send transactions to Tangerine networks.

## Syncing Fullnode

The testnet could be synchronized with the following command:

```
gtan --testnet
```

If you don't know how to build the `gtan` binary, please follow the wiki page [here](Building-Tangerine.md).

It may take a few hours before your fullnode is fully-synchronised.  When it does, you can now point your Tangerine/Ethereum client to http://localhost:8545

Note: Tangerine's current testnet is still unstable, it might be reset at some point. If it does, you might have to remove the data directory (`$HOME/.tangerine` on Linux, and `$HOME/Library/Tangerine` on MacOS) and re-sync the node.
