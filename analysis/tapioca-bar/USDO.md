# Summary

USDO is LayerZero OFT(Omni-fungible token) CDP-backed stablecoin issued by Tapioca DAO.

Tapioca Users have access to the following operations:
-  Depositing supported tokens into a CDP.
-  Withdrawing  supported tokens from a CDP.
-  Minting USDO from a CDP.
-  Burning USDO to pay off debt.
-  Repaying debt using underlying tokens.
-  Liquidating someone else's collateral to pay off bad debt
-  Flashloan/Flashmint
-  Cross-chain Market, Leverage, Options features by modules

In addition, the contract has 4 types of privileged roles : 
- owner:
    - set max flash mintable amount
    - set flash mint fee
    
- minter
- burner
- conservator

- On
● Transfer the admin role to a different address (must be accepted by the new admin).
● Configure the Alchemist's parameters, including limits, fees and the addresses of the
transmuter and protocol fee receiver.
● Reset (“snap”) the expected value of a yield token to the current value. Since deposits,
withdrawals and liquidations are blocked if the value of a yield token suddenly drops
significantly below its expected value, this can prevent the contract from becoming
unusable if the yield token doesn’t recover, or takes too long to recover.
# Mint/Burn
- Only allowed minter/burner should be able to mint/burn
- LTV ratio should be under 90 percent.
- Insolvent debt should be eligible to bw liquidated.

# Flashload/Flashmint
- Loan receiver should return amount+fee
- After Flashloan should only decrease total supply should decrease.
- Flash fee amount should be propotional to flash loan amount.
- Should not reenter.
- Should not lend more than 100k
- Approval should decrease by amount + fee after flashloan.
- Flashmint fee is 10%, Fee collection mechanism

# ERC20 features
- [ ] Tranfer/Approval mechanism
- [ ] Meta-transaction feature by signature

# Omni-chain feature
- [ ] OFTv2

# Conversator
- Only conservator can pause/unpause
- When paused, mint/burn/flashloan operation should be blocked.

# Omni-chain features
- Safety of delegatecall-based Module system should be checked.
- Market Modules
    - [ ] sendAndLendOrRepay sends to YieldBox over layer and lends asset to market
    - [ ] removeAsset removeAssetAndRepay on Magnetar from the destination layer
- Leverage Modules
    - [ ] Inits multiHopBuyCollateral
    - [ ] sends USDO to a specific chain and performs a leverage up operation

- Options Modules
    - [ ] Triggers a sendFrom to another layer from destination
    - [ ] Exercise an oTAP position

# Reference
USDO.sol

BaseUSDO.sol

ERC20Permit.sol

USDOLeverageModule.sol

USDOMarketModule.sol

USDOOptionsModule.sol