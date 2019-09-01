Tangerine DKG-TSIG Protocol
===========================
### Parameter
* λ = MAX(One gossip duraion, transaction confirm latency)
* Signature = [BLS](https://en.wikipedia.org/wiki/Boneh%E2%80%93Lynn%E2%80%93Shacham)
* Curve = BLS12_381
* n = size of `notary_set`
* t = <img src="https://latex.codecogs.com/svg.latex?\inline%20\left\lfloor\frac{2n}{3}\right\rfloor%2B1" />

### Notes
* Complaints and nack complaints are stored in governance contract; therefore, the broadcast is reliable.
* Governance contract will do the sanity check for complaints and nack complaints before adding to its state.
* Once a validator proposed `DKGFinal_i`, it can no longer propose any complaint.
* After DKG finished, if successful qualify nodes size is less than <img src="https://latex.codecogs.com/svg.latex?\inline%20\left\lfloor\frac{5}{6}\right\rfloor" /> of notary set size, DKG will be rerun with different set of nodes.

Phase 1 ID Registration 
-------
### @ T < 0

Each validator registers its ID(`DKGMasterPublicKey_i`) with stake.

**After λ**

Each validator `i` broadcasts a `DKGMasterPublicKeyReady_i` message.

Validator waits until seeing more than `2t+1` `DKGGroupPublicKeyReady` message than proceeds to Phase 2.

Phase 2 Secret Key Share Exchange
-------
### @ T = 0
Each validator `i` generates `n` (`n` = # of ID registered in phase 1) secret key shares (`SK_i,0, SK_i,1, ..., SK_i,n`) of order `t` and the secret key share is sent to the corresponding validator (`SK_i,j` is sent to validator `j`) via a secure channel.

Each validator `i` broadcasts the master public key (`MPK_i = {MPK_i,0, MPK_i,1, ..., MPK_i,t}`) of order `t` associated with the secret key shares.

Phase 3 Complaint
-------
### @ T = (0, λ)
Each validator `i` calculates public key shares (`PK_0,i, PK_1,i, ..., PK_n,i`) using corresponding master public key (`PK_j,i = F(MPK_j, i)`).

Each validator `i` verifies if the secret key share `SK_j,i` is associated with the public key share of validator `j`, `PK_j,i`. If the verification fails, `i` broadcast complaint of `j`, `CMP_i,j`.


Phase 4 Nack Complaint
-------
### @ T = λ
If validator `i` did not receive `SK_j,i`, broadcast nack complaint of `j`, `NCMP_i,j`. 

Phase 5 Anti Nack Complaint
-------
### @ T = 2λ
If validator `j` sees `NCMP_i,j` for any `i`, broadcast secret key share `SK_j,i`.

Phase 6 Rebroadcast Secret
-------
### @ T = 3λ
If validator `k` receive `SK_j,i` for the first time for `i` != `k`, broadcast it again.

Phase 7 Enforce Complaint
-------
### @ T = 4λ
If validator `k` sees `SK_j,i` for `i` != `k`, verifies if the secret key share `SK_j,i` is associated with the public key share of validator `j`, `PK_j,i`. If the verification fails, `k` broadcast complaint of `j`, `CMP_k,j`.

If validator `k` sees `NCMP_i,j` for `j` != `k` and did not receive `SK_j,i`, `k` broadcast nack complaint of `j`, `NCMP_k,j`.


Phase 8 DKG Finalize
-------
### @ T = 5λ
Each validator `i` broadcast a `DKGFinal_i` message.


Phase 9 Sign with CSK
-------
### @ T = 6λ

Validator waits until seeing more than `2t+1` final message.

If there are more than `t` nack complaints to validator `j` (<img src="https://latex.codecogs.com/svg.latex?\inline%20\sum_{i}%20NCMP_{i,j}%20>%20t" /> (`i` : for all validator `i`)), then `j` is marked as **Disqualified**.

If there is **one** complaint, `CMP_i,j`, to validator `j`, then `j` is marked as **Disqualified**.

Each validator `i` determines the combined secret key, <img src="https://latex.codecogs.com/svg.latex?\inline%20CSK_{i}%20=%20\sum_{k}%20SK_{k,i}" /> (`k`: validator `k` is not marked as **Disqualified**)

If a validator `i` successfully recovered combined secret key, it will broadcast a `DKGSuccess_i` message.

Each validator `i` sign the message with `CSK_i` and broadcast the partial signature, `PSign_i`.

Each validator `i` determines the combined public key of validator `j`, <img src="https://latex.codecogs.com/svg.latex?\inline%20CPK_{j}%20=%20\sum_{k}%20PK_{k,j}" /> (`k`: validator `k` is not marked as **Disqualified**)

Phase 10 TSIG
-------
### @ T = (6λ, +inf)
If validator `i` is not **Disqualified**, verify `PSign_i` with `CPK_i`.

Collect more than `t` valid `PSign_i` and recover TSIG, `TSIG`.

Phase 11 Verify TSIG
-------
Determines the group public key, <img src="https://latex.codecogs.com/svg.latex?\inline%20GPK%20=%20\sum_{k}%20MPK_{k,0}" /> (`k`: validator `k` is not marked as **Disqualified**)

Verify `TSIG` with `GPK`.