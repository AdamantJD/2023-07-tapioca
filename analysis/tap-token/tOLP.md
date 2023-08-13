# Summary

Tapioca Option Liquidity Provision (tOLP) is an ERC721 token that represents a locked Singularity position.
tOLP tokens are minted when a user locks their Singularity position and can be burned only when the position is unlocked to get back the Singularity position.
It is used in TapiocaOptionBroker (tOB) to participate in the twAML system and receive oTAP.

Its actions:
- Mint tOLP tokens when a user locks their Singularity position.
- Burn tOLP tokens when a user unlocks their Singularity position.

Each token has lock position info
- Singularity market YieldBox asset ID
- amount of tOLR tokens locked.
- time when the tokens were locked
- duration of the lock

Each singularity market
- Singularity market YieldBox asset ID
- Total amount of tOLR tokens deposited, used for pool share calculation
- Pool weight to calculate emission

# Checklists
- [ ] Lock/Unlock mechanism
- [ ] register/unregister singularity assets with weight
- [ ] Exercising options

# Functions

|  Contract  |         Type        |       Bases      |                  |                 |
|:----------:|:-------------------:|:----------------:|:----------------:|:---------------:|
|     └      |  **Function Name**  |  **Visibility**  |  **Mutability**  |  **Modifiers**  |
| **TapiocaOptionLiquidityProvision** | Implementation | ERC721, ERC721Permit, BaseBoringBatchable, Pausable, BoringOwnable |||
| └ | <Constructor> | Public ❗️ | 🛑  | ERC721 ERC721Permit |
| └ | getLock | External ❗️ |   |NO❗️ |
| └ | getSingularities | External ❗️ |   |NO❗️ |
| └ | getSingularityPools | External ❗️ |   |NO❗️ |
| └ | getTotalPoolDeposited | External ❗️ |   |NO❗️ |
| └ | isApprovedOrOwner | External ❗️ |   |NO❗️ |
| └ | lock | External ❗️ | 🛑  |NO❗️ |
| └ | unlock | External ❗️ | 🛑  |NO❗️ |
| └ | setSGLPoolWEight | External ❗️ | 🛑  | onlyOwner updateTotalSGLPoolWeights |
| └ | registerSingularity | External ❗️ | 🛑  | onlyOwner updateTotalSGLPoolWeights |
| └ | unregisterSingularity | External ❗️ | 🛑  | onlyOwner updateTotalSGLPoolWeights |
| └ | _computeSGLPoolWeights | Internal 🔒 |   | |
| └ | _isPositionActive | Internal 🔒 |   | |
| └ | onERC1155Received | External ❗️ |   |NO❗️ |
||||||

# Reference
TapiocaOptionLiquidityProvision.sol