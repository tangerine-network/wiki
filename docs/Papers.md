# Tangerine papers

## Fair Byzantine Agreements for Blockchains

Author: Tzu-Wei Chao, Hao Chung, Po-Chun Kuo\
(Submitted on 8 Jul 2019)

<p align="center">
  <img src="https://i.imgur.com/MS0vZxT.png">
</p>


Byzantine general problem is the core problem of the consensus algorithm, 
and many protocols are proposed recently to improve the decentralization level, 
the performance and the security of the blockchain. There are two challenging 
issues when the blockchain is operating in practice. First, the outcomes of the 
consensus algorithm are usually related to the incentive model, so whether each 
participant's value has an equal probability of being chosen becomes essential. 
However, the issues of fairness are not captured in the traditional security 
definition of Byzantine agreement. Second, the blockchain should be resistant to 
network failures, such as cloud services shut down or malicious attack, while 
remains the high performance most of the time. \
This paper has two main contributions. First, we propose a novel notion called 
fair validity for Byzantine agreement. Intuitively, fair validity lower-bounds 
the expected numbers that honest nodes' values being decided if the protocol is 
executed many times. However, we also show that any Byzantine agreement could 
not achieve fair validity in an asynchronous network, so we focus on synchronous 
protocols. This leads to our second contribution: we propose a fair, responsive 
and partition-resilient Byzantine agreement protocol tolerating up to 1/3 
corruptions. Fairness means that our protocol achieves fair validity. 
Responsiveness means that the termination time only depends on the actual 
network delay instead of depending on any pre-determined time bound. 
Partition-resilience means that the safety still holds even if the network is 
partitioned, and the termination will hold if the partition is resolved.

[Paper Link](https://arxiv.org/abs/1907.03437)