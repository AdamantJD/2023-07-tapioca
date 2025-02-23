# Summary

Time-Weighted Escrowed TAP & twAML

It allows user to vote in governance proposals and received share of revenue generated by protocol.
https://docs.tapioca.xyz/tapioca/token-economy/twtap

Global information
- totalParticipants
- averageMagnitude
- totalDeposited
- cumulativeMagnitude

Each participant has
- averageMagnitude;
- hasVotingPower; // if amount is more than 0.1 % of totalDeposited.
- divergenceForce; // 0 negative, 1 positive
- tapReleased; // allow restaking while rewards may still accumulate
- expiry; // expiry timestamp. Big enough for over 2 billion years..
- tapAmount; // amount of TAP locked
- multiplier; // Votes = multiplier * tapAmount
- lastInactive; // One week BEFORE the staker gets a share of rewards
- lastActive; // Last week that the staker shares in rewards

For each week
- Net Active Votes = active votes in the previous week - the votes known to expire this
- Total Distribution Per Vote

# Checklists
- [ ] LayerZero-based ONFT-721
- [ ] Minted by locking TAP for user-selected amount and duration
- [ ] Once locked, a twTAP position cannot be modified, whatsoever. This means no early unlocks, or even increasing lock time.
- [ ] At the end of the user-selected lock duration, the twTAP NFT can be burned, and the user reclaims the underlying TAP escrowed.
 -[ ] twTAP holders get voting power and weekly ETH yield. 
 -[ ] Delegation of twTAP gives up both voting power and weekly ETH yield. 
 
 -[ ] Participation of twTAP locking
 -[ ] Exit of twTAP locking
 -[ ] Weekly distribution per vote
 
## Safety of twAML(Time Weighted Escrowing Average Magnitude Lock)

low usage, low demand = larger discount
high usage, high demand = smaller discount

```
totalParticipants = total twTAP locking participants
averageMagnitude = average magnitude of each participants
totalDeposited = total amount deposited
cumulative = total sum of each participant's magnitude 
```

For each participant with lock duration, amount
```
magnitude = sqrt(duration * duration + _cumulative * _cumulative) - _cumulative;
multiplier = _magnitude * _cumulative;
voting power = amount * multiplier

if amount > 0.1 % of totalDeposited 
    averageMagnitude =
                (pool.averageMagnitude + magnitude) /
                pool.totalParticipants;
```

## Flaws in the Game Rule
Token whale can lock minimum amount(0.1 % of total deposit) of TAP with very long lock duration to manipulate average magnitude of the whole system higher and higher.

It will make other normal user's voting power weeker.

Other possibliity is to frontrun other participant's locking tx to manipulate average magnitude of the whole system, therefore weakening victim's reward and voting power.

Wrong calculation of average found.

## Recommendation
magnitude should take considerataion of lock amount not just duration.

Minium amount to participate will increase manipulating cost of hacker.

## Reference
twTAP.sol

twAML.sol