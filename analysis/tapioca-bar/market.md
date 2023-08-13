# Summary

Base contract for BigBang & Singularity

It provides basic functionalities like exchange rate, oracle integration. asset, collateral.

# Checklists
- [ ] Penrose registry
- [ ] YieldBox registry
- [ ] AssetId & asset
- [ ] CollateralId & collateral
- [ ] Oracle & oracleData
- [ ] Exchange Rate between collateral & asset
- [ ] Conversator
- [ ] Borrowing cap(0.05 % default)
- [ ] Borrow opening fee(0.05 % default)
- [ ] Collateralization rate(default 75%)
- [ ] Liquidation caller rewards
- [ ] Protocol fee
- [ ] Liquidation multiplier(default 12%)
- [ ] Liquidation bonus mount(default 10%)
- [ ] Closing factor
- [ ] Accuring interest logic
- [ ] Solvency check logic
- [ ] TVL calculation logic
- [ ] Batch call feature
- [ ] init should be only called once by owner.
- [ ] assetId and asset should be matching at Penrose.
- [ ] collateralId and collateral should be matching at Penrose.
- [ ] asset and assetId should be only USDO.
- [ ] only conservator should be able to pause/unpause.

## Functions
|  Contract  |         Type        |       Bases      |                  |                 |
|:----------:|:-------------------:|:----------------:|:----------------:|:---------------:|
|     └      |  **Function Name**  |  **Visibility**  |  **Mutability**  |  **Modifiers**  |
||||||
| **Market** | Implementation | MarketERC20, BoringOwnable |||
| └ | setBorrowOpeningFee | External ❗️ | 🛑  | onlyOwner |
| └ | setBorrowCap | External ❗️ | 🛑  | notPaused onlyOwner |
| └ | setMarketConfig | External ❗️ | 🛑  | onlyOwner |
| └ | updatePause | External ❗️ | 🛑  |NO❗️ |
| └ | computeClosingFactor | Public ❗️ |   |NO❗️ |
| └ | computeTVLInfo | Public ❗️ |   |NO❗️ |
| └ | updateExchangeRate | Public ❗️ | 🛑  |NO❗️ |
| └ | computeLiquidatorReward | Public ❗️ |   |NO❗️ |
| └ | _accrue | Internal 🔒 | 🛑  | |
| └ | _getRevertMsg | Internal 🔒 |   | |
| └ | _computeMaxBorrowableAmount | Internal 🔒 |   | |
| └ | _isSolvent | Internal 🔒 |   | |
| └ | _computeMaxAndMinLTVInAsset | Internal 🔒 |   | |
| └ | _getCallerReward | Internal 🔒 |   | |
| └ | _computeAllowanceAmountInAsset | Internal 🔒 |   | |
| └ | _getRatio | Private 🔐 |   | |
| **MarketERC20** | Implementation | IERC20, IERC20Permit, EIP712 |||
| └ | _allowedLend | Internal 🔒 | 🛑  | |
| └ | _allowedBorrow | Internal 🔒 | 🛑  | |
| └ | <Constructor> | Public ❗️ | 🛑  | EIP712 |
| └ | totalSupply | Public ❗️ |   |NO❗️ |
| └ | nonces | Public ❗️ |   |NO❗️ |
| └ | DOMAIN_SEPARATOR | External ❗️ |   |NO❗️ |
| └ | transfer | Public ❗️ | 🛑  |NO❗️ |
| └ | transferFrom | Public ❗️ | 🛑  |NO❗️ |
| └ | approve | Public ❗️ | 🛑  |NO❗️ |
| └ | approveBorrow | Public ❗️ | 🛑  |NO❗️ |
| └ | permit | External ❗️ | 🛑  |NO❗️ |
| └ | permitBorrow | External ❗️ | 🛑  |NO❗️ |
| └ | _useNonce | Internal 🔒 | 🛑  | |
| └ | _permit | Internal 🔒 | 🛑  | |
| └ | _approveBorrow | Internal 🔒 | 🛑  | |
| └ | _approve | Internal 🔒 | 🛑  | |


 Legend

|  Symbol  |  Meaning  |
|:--------:|-----------|
|    🛑    | Function can modify state |
|    💵    | Function is payable |

# Call Graph

![Call Graph](market.svg)
