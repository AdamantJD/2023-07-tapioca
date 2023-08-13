# Summary

USDO is omni-chain CDP-backed stablecoin issued by Tapioca DAO.

USDO is LayerZero OFT(Omni-fungible token) v2 which exists across omni-chain.

Its price peg to dollar is maintained by over-collateraization by Big Bang.

It has flashmint feature.


# Checklists
- [ ] Mint/Burn
- [ ] Only allowed minter/burner should be able to mint/burn
- [ ] Flashloan/Flashmint, possible max amount is 100k USDO
- [ ] Flashloan reentrancy
- [ ] Flashmint fee is 10%, Fee collection mechanism
- [ ] Only conservator can pause/unpause. If paused, mint/burn/flashloan operation should be blocked.
- [ ] Meta-transaction feature
- [ ] Tranfer/Approval mechanism
- [ ] OFTv2
- [ ] LayerZero-based omni-chain feature
- [ ] Safety of delegatecall-based Module System
- [ ] Market Modules
    - [ ] sendAndLendOrRepay sends to YieldBox over layer and lends asset to market
    - [ ] removeAsset removeAssetAndRepay on Magnetar from the destination layer
- [ ] Leverage Modules
    - [ ] Inits multiHopBuyCollateral
    - [ ] sends USDO to a specific chain and performs a leverage up operation

- [ ] Options Modules
    - [ ] Triggers a sendFrom to another layer from destination
    - [ ] Exercise an oTAP position

# Reference
USDO.sol
BaseUSDO.sol
ERC20Permit