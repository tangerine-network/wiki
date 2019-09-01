# BP Node Operation Guide

- [BP Node Operation Guide](#bp-node-operation-guide)
  - [Objective](#objective)
  - [Background](#background)
  - [Overview](#overview)
  - [Environment Setup](#environment-setup)
    - [System Requirement](#system-requirement)
    - [Hardware Requirement](#hardware-requirement)
    - [Software requirement](#software-requirement)
  - [Software Instruction](#software-instruction)
    - [Network Time Protocol Setting](#network-time-protocol-setting)
    - [Network confirmation](#network-confirmation)
    - [Generate Node Key](#generate-node-key)
    - [Register & Run your Node](#register--run-your-node)
    - [Troubleshooting](#troubleshooting)
    - [Operation](#operation)
  - [Mining Mechanism](#mining-mechanism)
    - [Tangerine Mining Economy and Mining Rewards](#tangerine-mining-economy-and-mining-rewards)


## Objective
The document will contain essential instructions and knowledge for a node operator to successfully run a Tangerine BP node.

## Background
For node operator to easily establish a Tangerine BP node and continuously run the node for mining rewards, Tangerine foundation provides the well-designed software supporting the mining mechanism on Tangerine blockchain.

## Overview
The guide has 3 sections, providing the required knowledge for a node operator to: Set up node, run software, and collect mining rewards.

## Environment Setup
How to set up AWS/GCP server?

For AWS, please follow https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/welcome.html

For GCP, please follow https://cloud.google.com/compute/docs/quickstart-linux

### System Requirement
Running Tangerine BP node has the following requirement:

### Hardware Requirement

| Tier | CPU | Memory | Bandwidth | Estimated Cost |
| ---  | --- | ---    | ---       | ---            |
| Minimum  | 4 Cores 2.0+ GHz | 8 GB | 200Mbps | 200~400 USD/mth |
| Recommend| 8 Cores 2.0+ GHz | 16 GB| 200Mbps | 600~800 USD/mth |

### Software requirement
 - OS: Linux 64 bit.
 - Docker image: byzantinelab/go-tangerine
 - Docker
 - Public IP or behind UPnP-enabled router

## Software Instruction

### Network Time Protocol Setting

NTP (Network Time Protocol) is required to keep the system clock in-synced.
Install `ntpd` or `chronyd` in Linux; `chronycontrol` in macOS.
Start it and it will synchronize the local time automatically.

### Network confirmation

Please make sure `TCP/30303` and `UDP/30303` is exposed, or else your node is likely to be disconnected from the reset of the network.


### Generate Node Key
A node key is required to operate a BP node. Run the following command to generate a node key:

    docker run -v $PWD:/mnt -it byzantinelab/tangerine-tools \
        nodekey generate /mnt/node.key

This show output content similar to the following

    Node Address: 0x93aA8C9C77De627E665F0b4015B7271B9Be89E83
    Public Key:0x046272a157cbffa00677be00b08c9d47f295539b07e53360754579ad5e933a638ba58dcf850484e7d40b8bc163a920082b2500ee54968db7155c6231c7e4eed592

Please store the address and public key which will be used to register a fullnode.
A file node.key can be found under the current working directory. node.key is very important as it contains the node private key. Please save this file securely.

### Register & Run your Node
1. Start the BP node. Use the following command to launch the BP node:

```
docker run --restart always \
    -v $PWD:/mnt \
    -p 30303:30303/tcp \
    -p 30303:30303/udp  \
    -it byzantinelab/go-tangerine:latest \
    --bp \
    --nodekey=/mnt/node.key \
    --datadir=/mnt/datadir \
    --syncmode=fast\
    --cache=1024 \
    --gcmode=archive \
    (--testnet)
```

The parameter `testnet` is only for the testnet of Tangerine Network.

Please make sure you have enough disk space in the current working directory

For more detail instruction about `gtan`, go to https://github.com/byzantine-lab/go-tangerine or use

    docker run -v $PWD:/mnt -it byzantinelab/go-tangerine --help

2. Install [Chrome or Firefox wallet extension](Create-Wallet.md).
3. Send some TAN to your node key address, 500 TAN should suffice. These TAN are required for the node to send transaction and interact with the consensus protocol. You need to replenish them if it ran out.
4. Send 5 ETH (Ethereum mainnet Ether, use Rinkeby Ether for testnet) to your node key address. This is a very **important** step. Since Tangerine relies on Ethereum mainnet to recover itself in case there is a catastrophic network failure. There are penalties if a BP node failed to propose recovery vote due to insufficient Ether in their node key address, see [Rules for node set](Rule-for-the-node-set.md) for more details.
5. Goto the [Governance contract page on Tangerine Garden](https://testnet.tangerine.garden/address/0x246FcDE58581e2754f215A523C0718C4BFc8041F).
6. Navigate to the `Write` tab and select `register` from the dropdown menu.

7. Fill in the information like below; currently, you need 1M TAN to run a BP node. If you don't have enough testnet TAN, ask @wnhuang (telegram) for it.

  - Node Public Key (the public key generated above and should not duplicate)
  - Name of the node (maximum length: 32 bytes)
  - Contact email (maximum length: 32 bytes)
  - Node Location (maximum length: 32 bytes)
  - Website URL (maximum length: 128 bytes)

![Register in Governance Contract Page](https://i.imgur.com/hlaXgyS.png)
The user whose stake is locked (bought TAN coin in private-sale), please contact Tangerine Foundation and provide the information below.

7. Hit send to register your node.

After this, you are successfully staked and the configuration will start to take effect after 2 epochs (2400 blocks).

Note that, the account of node.key and the account to send TAN coin to governance contract are not necessary to be the same. We strongly suggest using different keys to manage the risk.


### Troubleshooting

Here is a check list for trouble shooting issues with fullndoe:

1. Does the node have Public IP? or is it behind router that has UPnP support?
2. Firewall configuration for TCP/30303 and UDP/30303 are allowed.
3. NTP (Network Time Protocol) services installed?

### Operation

A BP node need to be online at all time, but since network between each BP nodes could be unstable, it's possible for connections between peers to be temporarily disconnected. In this case, DKG setup might fail and your node could be fined. Please read [here](Rules-for-the-node-set.md#Penalty) for more explaination on the penalty.

## Mining Mechanism

### Tangerine Mining Economy and Mining Rewards
Please read [this document](Cryptoeconomics.md)

As an example, initially, each node can expectedly mine 1M * 18.75% = 187.5K TAN coin per year (before total minted tokens hit 1.5B TAN).
