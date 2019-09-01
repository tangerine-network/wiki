# Running a RPC node

## Content

- [Overview](#overview)
- [System Requirement](#system-requirement)
- [Software Instruction](#software-instruction)

## Overview

A RPC node is the data access layer of blockchains. It usually won't join the mining process but only try to sync the latest confirmed state from other nodes. With those datum in hands, a RPC node can provide these functionalities:
- Pack and send transactions
- Allow other services (like **wallet** or **explorer**) to access states on blockchains in standard way, like **jsonrpc**.

## System Requirement

Refer to [System requirement](BP-Node-Operation-Guide.md#system-requirement) section in BP node operation guide.

## Software Instruction

Different from running a BP node, you don't have to
- create a node key
- register your node

The command line to start a RPC node is different, too:
```
docker run -v $PWD:/mnt -it byzantinelab/go-tangerine \
        --datadir=/mnt/datadir \
        --syncmode=fast \
        --rpc \
        --rpcapi=eth,net,web3 \
        --rpcaddr=0.0.0.0 \
        --rpcvhosts=* \
        --rpccorsdomain=* \
        --ws \
        --wsapi=eth,net,web3 \
        --wsaddr=0.0.0.0 \
        --wsorigins=* \
        --cache=1024 \
        --gcmode=archive \
        --metrics \
        --pprof \
        --pprofaddr=0.0.0.0
```
You should be able to see these logs, which simply means your RPC node tries to sync blocks from other peers and it would take a while. If not, make sure tcp/30303 and udp/30303 is not blocked by the firewall.
```
...
INFO [04-18|12:23:33.783] Imported new state entries  ...
INFO [04-18|12:23:35.647] Imported new state entries  ...
INFO [04-18|12:23:37.714] Imported new block receipts ...
INFO [04-18|12:23:38.471] Imported new block receipts ...
...
```
To make sure your RPC node is ready for usage, you can try to get the count of blocks it received via this command:
```
curl -X POST \
     -H "Content-Type: application/json" \
     --data '{"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":1}' \
     http://localhost:8545
```
You should be able to see something similar in return (**0xd482e** is the hex form of **870062**):
```
{"jsonrpc":"2.0","id":1,"result":"0xd482e"}
```

### RPC Node for Testnet

It simply to launch a RPC node for testnet by adding network flag `--testnet`:
```
docker run -v $PWD:/mnt -it byzantinelab/go-tangerine \
        --testnet \
        --datadir=/mnt/datadir \
        --syncmode=fast \
        --rpc \
        --rpcapi=eth,net,web3 \
        --rpcaddr=0.0.0.0 \
        --rpcvhosts=* \
        --rpccorsdomain=* \
        --ws \
        --wsapi=eth,net,web3 \
        --wsaddr=0.0.0.0 \
        --wsorigins=* \
        --cache=1024 \
        --gcmode=archive \
        --metrics \
        --pprof \
        --pprofaddr=0.0.0.0
```
