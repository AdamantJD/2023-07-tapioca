## Summary
Make it unchecked.

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/master/contracts/markets/MarketERC20.sol#L245-L249
```solidity
    function _useNonce(
        address owner
    ) internal virtual returns (uint256 current) {
+       unchecked {
            current = _nonces[owner]++; // @audit - unchecked.
+        }
    }
```