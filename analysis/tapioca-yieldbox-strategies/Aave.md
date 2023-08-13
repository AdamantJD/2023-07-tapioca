# Summary

Singularity is place is a place where all USDO stablecoins are minted and burnt.

It allows user to deposit collateral and mint USDO, or repay USDO and withdraw collateral.

# Checklists
- [ ] Mint/Burn
- [ ] Borrow/Repay
- [ ] Penrose fee collection

- [ ] Total Debt, Max Debt, Start Debt
- MinDebtRate, MaxDebtRate, debtRateAgainstEthMarket liquidationMultiplier
- [ ] Eth Market and Eth Market Debt rate

- [ ] Variable Debt rate calculation
Debt rate = (Current Debt / Max Debt) * (Max Rate - Min Rate) + Min Rate (Weighted Average)

- [ ] Every borrow operation should decrease borrow allownace in share amount.
- [ ] Updating operator for user
- [ ] Addind/Removing Collaterals
- [ ] Liquidation of Bad Postion
- [ ] Call batching
- [ ] Yieldbox integration
- [ ] owner of the contract is Penrose
- [ ] interest rate is not fixed, but dynamic based on the main BigBang market, minDebtRate, maxDebtRate and debtRateAgainstEthMarket
- [ ]  Only allowed operator should be able to move funds.
- [ ] Buy/Sell Collateral
- [ ] transfer/transferFrom should be disabled for BigBang.

# Functions

|  Contract  |         Type        |       Bases      |                  |                 |
|:----------:|:-------------------:|:----------------:|:----------------:|:---------------:|
|     └      |  **Function Name**  |  **Visibility**  |  **Mutability**  |  **Modifiers**  |
||||||
| **BigBang** | Implementation | BoringOwnable, Market |||
| └ | <Constructor> | Public ❗️ | 🛑  | MarketERC20 |
| └ | init | External ❗️ | 🛑  | onlyOnce |
| └ | getTotalDebt | External ❗️ |   |NO❗️ |
| └ | getDebtRate | Public ❗️ |   |NO❗️ |
| └ | execute | External ❗️ | 🛑  |NO❗️ |
| └ | updateOperator | External ❗️ | 🛑  |NO❗️ |
| └ | accrue | Public ❗️ | 🛑  |NO❗️ |
| └ | borrow | Public ❗️ | 🛑  | notPaused solvent |
| └ | repay | Public ❗️ | 🛑  | notPaused allowedBorrow |
| └ | addCollateral | Public ❗️ | 🛑  | allowedBorrow notPaused |
| └ | removeCollateral | Public ❗️ | 🛑  | notPaused solvent allowedBorrow |
| └ | liquidate | External ❗️ | 🛑  | notPaused |
| └ | buyCollateral | External ❗️ | 🛑  | notPaused solvent |
| └ | sellCollateral | External ❗️ | 🛑  | notPaused solvent |
| └ | transfer | Public ❗️ | 🛑  |NO❗️ |
| └ | transferFrom | Public ❗️ | 🛑  |NO❗️ |
| └ | refreshPenroseFees | External ❗️ | 🛑  | onlyOwner notPaused |
| └ | setBigBangConfig | External ❗️ | 🛑  | onlyOwner |
| └ | _accrue | Internal 🔒 | 🛑  | |
| └ | _addCollateral | Internal 🔒 | 🛑  | |
| └ | _liquidateUser | Private 🔐 | 🛑  | |
| └ | _extractLiquidationFees | Private 🔐 | 🛑  | |
| └ | _closedLiquidation | Private 🔐 | 🛑  | |
| └ | _addTokens | Internal 🔒 | 🛑  | |
| └ | _removeCollateral | Internal 🔒 | 🛑  | |
| └ | _repay | Internal 🔒 | 🛑  | |
| └ | _borrow | Internal 🔒 | 🛑  | |
| └ | _updateBorrowAndCollateralShare | Private 🔐 | 🛑  | |
