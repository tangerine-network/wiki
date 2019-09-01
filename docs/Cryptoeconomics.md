# Tangerine Network Cryptoeconomics

Tangerine Foundation  Last Modified 2019/7/30    v1.0

*This document describes the current plan and vision for the Tangerine Network platform. While we intend to attempt to realize this vision, please recognize that it is dependent on a number of factors and subject to a wide range of risks. We do not guarantee, represent or warrant any of the statements in this document, because they are based on our current beliefs, expectations and assumptions, about which there can be no assurance due to various anticipated and unanticipated events that may occur. Please know that we seek to achieve the vision laid out in our whitepaper and website, but that you cannot rely on any of it coming true. Blockchain, cryptocurrencies, other aspects of our technology and these markets are in their infancy and will be subject to many challenges, competition and a changing environment.


## Token Allocation
The total supply of TAN tokens is fixed at **200 million**. The genesis token supply is **50 million** TAN and the other **150 million** TAN will be minted as mining rewards after Tangerine mainnet launches. The token allocation is shown below:

<p align="center">
  <img src="https://i.imgur.com/h4fw4Vd.png" width="500">
  <br></br>
  <b> Figure 1. Token Allocation </b>
</p>

* 75% for Miner’s Reward

	For rewarding miners that actively participate in network consensus and smart contract executions on Tangerine Network.

* 25% for Genesis Supply

	The genesis supply allocation is mostly used as stakes for genesis block proposer nodes. There are no private placement or any kind of token sale for Tangerine Network. For detailed allocation, please read bellow.


## Mining Model
Nodes that actively participate in validating transactions will get TAN tokens as mining rewards based on Tangerine’s Proof of Participation Model.

### Proof-of-Participation Model
* Validator Eligibility

A node is eligible to join as a validator if its TAN token deposit reaches the threshold of 1 million TAN. The deposit can come from the node itself or from any other accounts that support the node. It takes 2 epochs (2 hours) for the deposit to become effective, and another 24 hours for deposit withdrawals to become effective.

* Symmetric Validator Power

The validating power and the probability to be selected as a block producer among all validators are both fair and symmetric, meaning that the expected mining rewards of each validator will be the same as well.

* Mining Rewards

A validator earns transaction processing fees, gas fees, and mining rewards when it actively produces blocks and acks to other blocks.


## Adaptive Mining Mechanism
Tangerine adopts a novel adaptive mining mechanism that can self-adjust the token minting velocity. The token minting velocity is proportional to the participation rate of mining. If the demand of TAN token is strong, it will attract more token holders to participate in mining for rewards, hence the minting velocity will increase, and vice versa. This will make sure the system can keep demand and supply balanced by itself.


The formula of minting velocity is stated below:
<p align="center">
  <img src="https://i.imgur.com/zkco21K.png" width="400">
</p>
r is total supply growth rate (the annual growth rate of total supply), vis node mining velocity (the annual mining rate of each node), and  is mining participation rate (the percentage of deposited tokens in validators relative to current total token circulation).
Initially, v is 18% and will alter based on the total minted tokens under a half-life condition.
The relation between node mining velocity and minted tokens is shown below:

* v= 18% when mainnet launches.

* v= 9% after 75 million TAN tokens are minted.

* v= 4.5% after another 37.5 million TAN tokens are minted,  and so on.

As an example, inniitialy each node can mine 1M * 18% = 180K TAN tokens per year. As total minted tokens hit 75M TAN, the annual mining rate per node will decrease from 18% to 9%, and as total minted tokens hit 125M TAN, the annual per node mining rate will decrease further from 9% to 4.5%, and so on.

<p align="center">
  <img src="https://i.imgur.com/tpzzyjV.png" width="600">
  <br></br>
  <b> Figure 2. Node Mining Velocity Half-Life Threshold </b>
</p>


## Mining Rewards in Circulation
Now, let’s consider the influence of mining participation rate. For example, the genesis supply of TAN token is 50M, if 25M tokens are deposited in validating nodes, the mining participation rate will be 50%. So the total supply growth rate will be 18% * 50% = 9%.
The total mining rewards in circulation based on different participation rates (30%, 60%) is shown in the figure below:
<p align="center">
  <img src="https://i.imgur.com/x3Tdj2p.png" width="600">
  <br></br>
  <b> Figure 3. Total Mining Rewards in Circulation </b>
</p>

Assuming the mining participation rate is fixed at 60%, r(total supply growth rate) per year is shown below:
<p align="center">
  <img src="https://i.imgur.com/HAhuKYm.png" width="600">
  <br></br>
  <b> Figure 4. Total Mining Rewards in Circulation </b>
</p>


## Genesis Allocation
As stated above, the genesis supply is 50 million TAN and the allocation is shown below:
<p align="center">
  <img src="https://i.imgur.com/hkoOHeR.png" width="600">
  <br></br>
  <b> Figure 5. Genesis Supply Allocation </b>
</p>


* 60% to genesis block proposers. The genesis block proposers consists of blockchain companies and universities mainly in Taiwan and Singapore. The maximum nodes the genesis supply can stakeis (50M * 60%) / 1M = 30 nodes.
* 20% to tech development. This allocation is mainly used to pay as salaries to the developers and bug bounties.
* 10% to marketing and promotion of Tangerine Network.
* 5% to the Tangerine Foundation for misc. operations.
* 5% for listing on top 5 exchanges in the world.

## DISCLAIMER
**PLEASE READ THIS DISCLAIMER SECTION CAREFULLY.  CONSULT LEGAL AND FINANCIAL EXPERTS FOR FURTHER GUIDANCE.**
The following information may be incomplete and in no way implies a contractual relationship. While we make every effort to ensure that all information in this Whitepaper is accurate and up to date, such material in no way constitutes professional advice. Tangerine Foundation neither guarantees nor accepts responsibility for the accuracy, reliability, or completeness of this content. The content may be subject to change at any time without prior notice. Individuals intending to purchase platform token should seek independent professional advice prior to acting on any of the information contained in this paper.

**Disclaimer – TAN Tokens and Tangerine Foundation**

1. Not Securities.
Use and purchase of the TAN Tokens carries significant financial risk.  Tangerine Foundation hereby expressly disclaims that the transactions taking place on its platform pertain in any way to an offering of securities in any jurisdiction or that any documents published on its platform are solicitations for investment.

2. Security of Platform.
You acknowledge that information you store or transfer through Tangerine Foundation may become irretrievably lost or corrupted or temporarily unavailable due to a variety of causes, including software failures, protocol changes by third party providers, internet outages, force majeure event or other disasters including third party DDOS attacks, scheduled or unscheduled maintenance, or other causes either within or outside Tangerine Foundation’s control.  You are solely responsible for backing up and maintaining duplicate copies of any information you store or transfer through Tangerine Foundation’ services

3. No Responsibilities for TAN Tokens
Use and purchase of the TAN Tokens carries significant financial risk. Tangerine Foundation does not provide token purchase, financial, or legal advice. The documents provided to you cannot substitute for professional advice and independent factual verification. You warrant that you have conducted your own research and analysis, independently verify any information upon which you wish to rely, consider your own personal circumstances and goals, and obtain independent financial advice from appropriate professionals before making any token purchase decision or taking any other action including without limitation purchasing any TAN Tokens. You further acknowledge and agree that Tangerine Foundation has no obligation of due diligence or fiduciary duty toward you.

4. No Liability.
Neither Tangerine Foundation nor any person or entity associated with it, including but not limited to its agents, servants, employees, insurers, attorneys, successors, and assigns, will be liable, whether in contract, tort (including negligence), or otherwise, for any damage, expense, or other loss you may suffer arising out of any use of the TAN Tokens.

5. Technology - Sophistication.
Tokens are often described in exceedingly technical language; a comprehensive understanding of applied cryptography and computer science is required in order to appreciate inherent risks.  You represent and warrant that you have sufficient knowledge, market sophistication, experience, and/or professional advice sufficient to undertake a prudent evaluation of the merits and risks of purchasing the TAN Tokens. You agree to bear sole responsibility for the aforementioned purchase.

6. Technology - No guarantee.
Neither Tangerine Foundation nor its affiliates owns or controls any of the underlying software through which blockchain networks are formed. Neither Tangerine Foundation nor its affiliates makes any guarantee of functionality, security, or availability of such software and networks.

7. Technology - Forks.
The blockchain technology underlying tokens is subject to change at any time, including changes in operating rules (commonly referred to as “forks”), and blockchain networks may go offline as a result of bugs, hard forks, or a number of other unforeseeable reasons. Such changes may materially and adversely affect the value or function of the TAN Tokens. You agree that you are fully responsible for monitoring such changes and agree to bear all risks arising therefrom or relating thereto.

8. Technology - Malicious Nodes.
Some nodes in the Tangerine Foundation network may be malicious and attempt to get rewarded without corresponding contribution; also, attackers may try to ruin the Tangerine Foundation ecosystem if they only suffer from minimal penalties. We need strong guarantees to protect the network from malicious attacks to ensure that the transactions are secured and the ecosystem is sustainable. Some attacks that could threaten a blockchain network are listed and discussed as follows:
Sybil Attack
Malicious nodes could create multiple Sybil identities to strive for more rewards or cheat the network. In general, the proof mechanism should have established barriers to prevent Sybil attacks; however, there is no guarantee such barriers will always be successful.
Out-of- Work Attack
While an attacker can control a lot of nodes, the nodes could be used to make some troubles on a distributed computing network. The nodes controlled by malicious attackers could be called zombies. An attack methodology is to ask the zombie nodes to quit or go on a strike at one time. On Tangerine Foundation network, the zombie nodes may take AI jobs but fail to complete them or return invalid results. If an AI job is assigned to a group of which most are zombie nodes, the AI job would receive unauthentic results or just simply fail.
Outsourcing Attack
Malicious nodes may outsource their jobs to other nodes, such that they may earn the rewards easily without consuming the corresponding computing power. On Tangerine Foundation network, nodes should present their capabilities to strive for taking jobs. Validation of node capabilities based on Proof-of-Intelligence may mitigate the behavior of outsourcing attack because the malicious nodes would lose their jobs if they do not endeavor to execute the same; however, there is no guarantee this approach will always be successful.
Cyber-attacks
In the event of a cyberattack on the TAN Tokens or the Tangerine Foundation, the TAN Tokens may be adversely affected. Neither Tangerine Foundation nor its affiliates makes any guarantee that it may foresee, prevent, mitigate, or take corrective action in the event of such attack.

9. Regulatory Measures
Crypto-tokens are being, or may be overseen by the regulatory authorities of various jurisdictions. Tangerine Foundation may receive queries, notices, warnings, requests, or rulings from one or more regulatory authorities from time to time or may even be ordered to suspend or discontinue any action in connection with the TAN Tokens. The development of the TAN Tokens may be seriously affected, hindered, or terminated as a result.

10. Illiquidity and Price Volatility
There may not be a demand for TAN Tokens. Tangerine Foundation is not responsible for the circulation and trading of TAN Tokens on the market. Tokens, if traded on markets, usually have extremely volatile prices. Fluctuations in price over short periods of time frequently occur, which price may be denominated in Bitcoin, Ether, US Dollars or any other fiat currency. Such fluctuations could result from market forces (including speculations), regulatory changes, technical innovations, availability of exchanges, and other objective factors and represent changes in the balance of supply and demand.
Tangerine Foundation does not make any representation or warranty, explicit or implicit, as to the usability or the value of the TAN Tokens. You understand and accept that there is no warranty or assurance that you will receive any benefits through the TAN Tokens.

11. Compliance by Users.
You acknowledge and agree that Tangerine Foundation is not responsible for determining whether or which laws, rules, or regulations apply or may apply to your transactions (including, without limitation, any anti-money laundering laws, securities laws and tax laws). You acknowledge and agree that you are in compliance with all such laws, rules, or regulations as may be applicable to your transactions. Without limiting the foregoing, you acknowledge and agree that you are solely responsible for all tax obligations arising from your purchase of the TAN Tokens. You further acknowledge and agree that Tangerine Foundation shall not be liable, whether directly or indirectly, for any of your tax obligations.
Applicable law, regulation, and executive orders may require Tangerine Foundation to, upon request by government agencies, disclose information regarding your account(s). In the event such disclosure is compelled, you agree that Tangerine Foundation may disclose information regarding your accounts. While Tangerine Foundation will endeavor to, where commercially reasonable, give you prior notice of such disclosure, Tangerine Foundation makes no guarantees that such prior notice will be made.
