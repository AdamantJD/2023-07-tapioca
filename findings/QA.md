## Summary
`operator` is defined but never used.

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/master/contracts/markets/bigBang/BigBang.sol#L46
```solidity
    mapping(address => mapping(address => bool)) public operators; // @audit - no check for operators
```
