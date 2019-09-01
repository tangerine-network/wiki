# DKGSet

DKGSet will run several tasks during a round (or `epoch` described in Tangerine Consensus Algorithm).

Suppose the interval `[0, T)` and `[T, 2T)` are round `r` and `r+1`, respectively. (`T` is the round interval defined in Governance Contract)

The time `t` is the Consensus Timestamp of the delivered block.

## @ t = T/2
* DKGSet_r starts the TSIG protocol to generate `CRS_r+1 = TSIG(CRS_r)`. DKGSet_r+1 is then decided.
* After DKGSet_r+1 is decided, DKGSet_r+1 register their DKG ID. ([Phase 1 of DKG + TSIG Protocol](DKG-TSIG-Protocol.md#phase-1-id-registration))

## @ t = T * 2 / 3
* DKGSet_r+1 starts the DKG protocol ([Phase 2 of DKG + TSIG Protocol](DKG-TSIG-Protocol.md#phase-2-secret-key-share-exchange))

## @ t = [T, 2T)
* DKGSet_r+1 calculate the `Block.Randomness = TSIG(Block.Hash)` using TSIG protocol for each block confirmed in the round `r+1`. ([On Chain Random Oracle](On-Chain-Random-Oracle.md))


# Special Case for Round 0
* `CRS_0` is defined in Genesis state.
* No DKGSet and `Block.Randomness`.
* `CRS_1` = `HASH(CRS_0)`
