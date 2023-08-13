# Summary

The TAP token is the backbone of the Tapioca DAO token economy. TAP was carefully crafted with a unique and novel approach to tokenomics design to be sustainably distributed over a long-term horizon with economic growth and value retention as the foremost doctrines. The end goal is to reach a ubiquitous distribution of the TAP token to facilitate maximal decentralization of the Tapioca DAO ecosystem. Notably, there are no emissions of TAP itself, nor Tapioca feature any liquidity mining programs.

It allows user to deposit collateral and mint USDO, or repay USDO and withdraw collateral.

## Tokenomics
//  Allocation:
// =========
// * DSO: 53,313,405(Starting)
// * DAO: 8m
// * Contributors: 15m
// * Early supporters: 3,686,595
// * Supporters: 12.5m
// * LBP: 5m
// * Airdrop: 2.5m
// == 100M ==

# Checklists
- [ ] Fixed supply of 100M
- [ ] Layer-zero based OFT v2
- [ ] Emission rate 0.88%
- [ ] Weekly emission schedule formula
- extractTAP from weekly emission by minter

- [ ] removeTAP from `msg.sender`

# LayerZero Packet Types

- [ ] PT_LOCK_TWTAP - lockTwTapPosition
- [ ] PT_UNLOCK_TWTAP - unlockTwTapPosition
- [ ] PT_CLAIM_REWARDS - claimRewards
- [ ] PT_SEND - send
- [ ] PT_SEND_AND_CALL - sendAndCall

# Invariants

```
dso_supply[week] > dso_supply[week - 1]
```
```
emissionForWeek[week] >= mintedInWeek[week]
```
```
dso_supply -= mintedInWeek[week - 1];
mintedInWeek[week]; = (dso_supply * decay_rate) / DECAY_RATE_DECIMAL;
```


# Reference
TapOFT.sol

BaseTapOFT.sol