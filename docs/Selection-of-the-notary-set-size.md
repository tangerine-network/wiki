# Selection of the Notary Set Size

As mention in our consensus algorithm, we follow the hypergeometric distribution to decide the size of notary set.

Given a node set of size N, the ratio R of Byzantine nodes, and the notary set of size n, then, the probability that more than 1/3 of notary set is Byzantine nodes is

<p align="center">
  <img src="https://imgur.com/wszheq8.png" width="250">
</p>

We set the probability to be 10^-8; that is, there is less than one fault during 10000 years in expectation (notary set is re-selected every hour).
Assume R=1/5. We can derive the proper size of the notary set according to the equation and the result is shown in the following figure.


<p align="center">
  <img src="https://i.imgur.com/ylQP4Qu.png">
</p>

For convenience, we give two curves to approximate the data points.
The first one is y = 70.5 ln(x) - 264, which is the purple dash line and the second one is y = 74 ln(x) - 264, which is the green dash line.
The following table is the resilience ratio to the Byzantine given the size of notary set and probability 10^-8.



| node set size | notary set size | resilience | notary set size | resilience |
| -------- | -------- | -------- | --- | --- |
| 200 | 110 | 0.199 | 123 | 0.220 |
| 400 | 159 | 0.197 | 174 | 0.207 |
| 600 | 187 | 0.194 | 203 | 0.202 |
| 800 | 208 | 0.197 | 224 | 0.202 |
| 1000 | 223 | 0.197 | 252 | 0.202 |
| 1500 | 252 | 0.199 | 270 | 0.204 |
| 2000 | 272 | 0.199 | 291 | 0.207 |
| 4000 | 321 | 0.207 | 342 | 0.209 |


Tangerine mainnet will use y = 70.5 ln(x) - 264 to decide the size of the notary set under different sizes of the node set.
