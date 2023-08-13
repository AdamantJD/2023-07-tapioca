# Summary

oTAP is NFT-based call option that provides right to buy TAP at 5~50% discount based on AML.

It has option broker which exercise option with discounted buy price to buy TAP, thus creating POL(Protocol Owned Liquidty) and floor price for TAP.

Each token id has 
- expiry timestamp
- discount in basis points
- tOLP token ID


# Checklists
- [ ] Mint/Burn
- [ ] Broker claim mechanism 
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
| **OTAP** | Implementation | ERC721, ERC721Permit, BaseBoringBatchable |||
| └ | <Constructor> | Public ❗️ | 🛑  | ERC721 ERC721Permit |
| └ | tokenURI | Public ❗️ |   |NO❗️ |
| └ | isApprovedOrOwner | External ❗️ |   |NO❗️ |
| └ | attributes | External ❗️ |   |NO❗️ |
| └ | exists | External ❗️ |   |NO❗️ |
| └ | setTokenURI | External ❗️ | 🛑  |NO❗️ |
| └ | mint | External ❗️ | 🛑  | onlyBroker |
| └ | burn | External ❗️ | 🛑  |NO❗️ |
| └ | brokerClaim | External ❗️ | 🛑  |NO❗️ |
||||||
| **Domain** | Implementation |  |||
| └ | _calculateDomainSeparator | Private 🔐 |   | |
| └ | <Constructor> | Public ❗️ | 🛑  |NO❗️ |
| └ | _domainSeparator | Internal 🔒 |   | |
| └ | _getDigest | Internal 🔒 |   | |
||||||
| **ERC20Data** | Implementation |  |||
||||||
| **ERC20** | Implementation | IERC20, Domain |||
| └ | transfer | Public ❗️ | 🛑  |NO❗️ |
| └ | transferFrom | Public ❗️ | 🛑  |NO❗️ |
| └ | approve | Public ❗️ | 🛑  |NO❗️ |
| └ | DOMAIN_SEPARATOR | External ❗️ |   |NO❗️ |
| └ | permit | External ❗️ | 🛑  |NO❗️ |
||||||
| **ERC20WithSupply** | Implementation | IERC20, ERC20 |||
| └ | _mint | Internal 🔒 | 🛑  | |
| └ | _burn | Internal 🔒 | 🛑  | |
||||||
| **IERC20** | Interface |  |||
| └ | totalSupply | External ❗️ |   |NO❗️ |
| └ | balanceOf | External ❗️ |   |NO❗️ |
| └ | allowance | External ❗️ |   |NO❗️ |
| └ | approve | External ❗️ | 🛑  |NO❗️ |
| └ | permit | External ❗️ | 🛑  |NO❗️ |
||||||
| **RebaseLibrary** | Library |  |||
| └ | toBase | Internal 🔒 |   | |
| └ | toElastic | Internal 🔒 |   | |
| └ | add | Internal 🔒 |   | |
| └ | sub | Internal 🔒 |   | |
| └ | add | Internal 🔒 |   | |
| └ | sub | Internal 🔒 |   | |
| └ | addElastic | Internal 🔒 | 🛑  | |
| └ | subElastic | Internal 🔒 | 🛑  | |
||||||
| **BoringERC20** | Library |  |||
| └ | returnDataToString | Internal 🔒 |   | |
| └ | safeSymbol | Internal 🔒 |   | |
| └ | safeName | Internal 🔒 |   | |
| └ | safeDecimals | Internal 🔒 |   | |
| └ | safeBalanceOf | Internal 🔒 |   | |
| └ | safeTransfer | Internal 🔒 | 🛑  | |
| └ | safeTransferFrom | Internal 🔒 | 🛑  | |
||||||
| **YieldBoxRebase** | Library |  |||
| └ | _toShares | Internal 🔒 |   | |
| └ | _toAmount | Internal 🔒 |   | |
||||||
| **IStrategy** | Interface |  |||
| └ | yieldBox | External ❗️ |   |NO❗️ |
| └ | name | External ❗️ |   |NO❗️ |
| └ | description | External ❗️ |   |NO❗️ |
| └ | tokenType | External ❗️ |   |NO❗️ |
| └ | contractAddress | External ❗️ |   |NO❗️ |
| └ | tokenId | External ❗️ |   |NO❗️ |
| └ | currentBalance | External ❗️ |   |NO❗️ |
| └ | withdrawable | External ❗️ |   |NO❗️ |
| └ | cheapWithdrawable | External ❗️ |   |NO❗️ |
| └ | deposited | External ❗️ | 🛑  |NO❗️ |
| └ | withdraw | External ❗️ | 🛑  |NO❗️ |
||||||
| **IYieldBox** | Interface |  |||
| └ | wrappedNative | External ❗️ |   |NO❗️ |
| └ | assets | External ❗️ |   |NO❗️ |
| └ | nativeTokens | External ❗️ |   |NO❗️ |
| └ | owner | External ❗️ |   |NO❗️ |
| └ | totalSupply | External ❗️ |   |NO❗️ |
| └ | setApprovalForAsset | External ❗️ | 🛑  |NO❗️ |
| └ | depositAsset | External ❗️ | 🛑  |NO❗️ |
| └ | withdraw | External ❗️ | 🛑  |NO❗️ |
| └ | transfer | External ❗️ | 🛑  |NO❗️ |
| └ | batchTransfer | External ❗️ | 🛑  |NO❗️ |
| └ | transferMultiple | External ❗️ | 🛑  |NO❗️ |
| └ | toShare | External ❗️ |   |NO❗️ |
| └ | toAmount | External ❗️ |   |NO❗️ |
||||||
| **ERC1155TokenReceiver** | Implementation | IERC1155TokenReceiver |||
| └ | onERC1155Received | External ❗️ |   |NO❗️ |
| └ | onERC1155BatchReceived | External ❗️ |   |NO❗️ |
||||||
| **ERC1155** | Implementation | IERC1155 |||
| └ | supportsInterface | Public ❗️ |   |NO❗️ |
| └ | balanceOfBatch | External ❗️ |   |NO❗️ |
| └ | _mint | Internal 🔒 | 🛑  | |
| └ | _burn | Internal 🔒 | 🛑  | |
| └ | _transferSingle | Internal 🔒 | 🛑  | |
| └ | _transferBatch | Internal 🔒 | 🛑  | |
| └ | _requireTransferAllowed | Internal 🔒 |   | |
| └ | safeTransferFrom | External ❗️ | 🛑  |NO❗️ |
| └ | safeBatchTransferFrom | External ❗️ | 🛑  |NO❗️ |
| └ | setApprovalForAll | External ❗️ | 🛑  |NO❗️ |
| └ | uri | External ❗️ |   |NO❗️ |
||||||
| **BoringMath** | Library |  |||
| └ | to128 | Internal 🔒 |   | |
| └ | to64 | Internal 🔒 |   | |
| └ | to32 | Internal 🔒 |   | |
| └ | muldiv | Internal 🔒 |   | |
||||||
| **YieldBox** | Implementation | YieldBoxPermit, BoringBatchable, NativeTokenFactory, ERC721TokenReceiver, ERC1155TokenReceiver |||
| └ | <Constructor> | Public ❗️ | 🛑  | YieldBoxPermit |
| └ | _tokenBalanceOf | Internal 🔒 |   | |
| └ | depositAsset | Public ❗️ | 🛑  | allowed |
| └ | depositNFTAsset | Public ❗️ | 🛑  | allowed |
| └ | depositETHAsset | Public ❗️ |  💵 |NO❗️ |
| └ | withdraw | Public ❗️ | 🛑  | allowed |
| └ | _withdrawNFT | Internal 🔒 | 🛑  | |
| └ | _withdrawFungible | Internal 🔒 | 🛑  | |
| └ | transfer | Public ❗️ | 🛑  | allowed |
| └ | batchTransfer | Public ❗️ | 🛑  |NO❗️ |
| └ | _transferBatch | Internal 🔒 | 🛑  | |
| └ | transferMultiple | Public ❗️ | 🛑  | allowed |
| └ | setApprovalForAll | External ❗️ | 🛑  |NO❗️ |
| └ | _setApprovalForAll | Internal 🔒 | 🛑  | |
| └ | setApprovalForAsset | External ❗️ | 🛑  |NO❗️ |
| └ | _setApprovalForAsset | Internal 🔒 | 🛑  | |
| └ | uri | External ❗️ |   |NO❗️ |
| └ | name | External ❗️ |   |NO❗️ |
| └ | symbol | External ❗️ |   |NO❗️ |
| └ | decimals | External ❗️ |   |NO❗️ |
| └ | assetTotals | External ❗️ |   |NO❗️ |
| └ | toShare | External ❗️ |   |NO❗️ |
| └ | toAmount | External ❗️ |   |NO❗️ |
| └ | amountOf | External ❗️ |   |NO❗️ |
| └ | deposit | Public ❗️ | 🛑  |NO❗️ |
| └ | depositETH | Public ❗️ |  💵 |NO❗️ |
||||||
| **IWrappedNative** | Interface | IERC20 |||
| └ | deposit | External ❗️ |  💵 |NO❗️ |
| └ | withdraw | External ❗️ | 🛑  |NO❗️ |
||||||
| **ERC721TokenReceiver** | Implementation | IERC721TokenReceiver |||
| └ | onERC721Received | External ❗️ |   |NO❗️ |
||||||
| **AssetRegister** | Implementation | ERC1155 |||
| └ | <Constructor> | Public ❗️ | 🛑  |NO❗️ |
| └ | assetCount | Public ❗️ |   |NO❗️ |
| └ | _registerAsset | Internal 🔒 | 🛑  | |
| └ | registerAsset | Public ❗️ | 🛑  |NO❗️ |
| └ | setApprovalForAsset | External ❗️ | 🛑  |NO❗️ |
||||||
| **NativeTokenFactory** | Implementation | AssetRegister |||
| └ | transferOwnership | Public ❗️ | 🛑  | onlyOwner |
| └ | claimOwnership | Public ❗️ | 🛑  |NO❗️ |
| └ | createToken | Public ❗️ | 🛑  |NO❗️ |
| └ | mint | Public ❗️ | 🛑  | onlyOwner |
| └ | burn | Public ❗️ | 🛑  | allowed |
| └ | batchMint | Public ❗️ | 🛑  | onlyOwner |
| └ | batchBurn | Public ❗️ | 🛑  |NO❗️ |
||||||
| **YieldBoxURIBuilder** | Implementation |  |||
| └ | name | External ❗️ |   |NO❗️ |
| └ | symbol | External ❗️ |   |NO❗️ |
| └ | decimals | External ❗️ |   |NO❗️ |
| └ | uri | External ❗️ |   |NO❗️ |
||||||
| **YieldBoxPermit** | Implementation | EIP712 |||
| └ | <Constructor> | Public ❗️ | 🛑  | EIP712 |
| └ | permit | Public ❗️ | 🛑  |NO❗️ |
| └ | _setApprovalForAsset | Internal 🔒 | 🛑  | |
| └ | permitAll | Public ❗️ | 🛑  |NO❗️ |
| └ | _setApprovalForAll | Internal 🔒 | 🛑  | |
| └ | nonces | Public ❗️ |   |NO❗️ |
| └ | DOMAIN_SEPARATOR | External ❗️ |   |NO❗️ |
| └ | _useNonce | Internal 🔒 | 🛑  | |
||||||
| **TapiocaOptionBroker** | Implementation | Pausable, BoringOwnable, TWAML |||
| └ | <Constructor> | Public ❗️ | 🛑  |NO❗️ |
| └ | getOTCDealDetails | External ❗️ |   |NO❗️ |
| └ | participate | External ❗️ | 🛑  |NO❗️ |
| └ | exitPosition | External ❗️ | 🛑  |NO❗️ |
| └ | exerciseOption | External ❗️ | 🛑  |NO❗️ |
| └ | newEpoch | External ❗️ | 🛑  |NO❗️ |
| └ | oTAPBrokerClaim | External ❗️ | 🛑  |NO❗️ |
| └ | setTapOracle | External ❗️ | 🛑  | onlyOwner |
| └ | setPaymentToken | External ❗️ | 🛑  | onlyOwner |
| └ | setPaymentTokenBeneficiary | External ❗️ | 🛑  | onlyOwner |
| └ | collectPaymentTokens | External ❗️ | 🛑  | onlyOwner |
| └ | _processOTCDeal | Internal 🔒 | 🛑  | |
| └ | _getDiscountedPaymentAmount | Internal 🔒 |   | |
| └ | _emitToGauges | Internal 🔒 | 🛑  | |
||||||
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
| **TapOFT** | Implementation | BaseTapOFT, ERC20Permit |||
| └ | <Constructor> | Public ❗️ | 🛑  | BaseTapOFT ERC20Permit |
| └ | setGovernanceChainIdentifier | External ❗️ | 🛑  | onlyOwner |
| └ | updatePause | External ❗️ | 🛑  | onlyOwner |
| └ | setMinter | External ❗️ | 🛑  | onlyOwner |
| └ | decimals | Public ❗️ |   |NO❗️ |
| └ | timestampToWeek | External ❗️ |   |NO❗️ |
| └ | getCurrentWeek | External ❗️ |   |NO❗️ |
| └ | getCurrentWeekEmission | External ❗️ |   |NO❗️ |
| └ | emitForWeek | External ❗️ | 🛑  | notPaused |
| └ | extractTAP | External ❗️ | 🛑  | notPaused |
| └ | removeTAP | External ❗️ | 🛑  | notPaused |
| └ | _timestampToWeek | Internal 🔒 |   | |
| └ | _getChainId | Private 🔐 |   | |
| └ | _computeEmission | Internal 🔒 |   | |
||||||
| **BaseTapOFT** | Implementation | OFTV2 |||
| └ | <Constructor> | Public ❗️ | 🛑  | OFTV2 |
| └ | _nonblockingLzReceive | Internal 🔒 | 🛑  | |
| └ | lockTwTapPosition | External ❗️ |  💵 |NO❗️ |
| └ | _lockTwTapPosition | Internal 🔒 | 🛑  | |
| └ | claimRewards | External ❗️ |  💵 |NO❗️ |
| └ | _claimRewards | Internal 🔒 | 🛑  | |
| └ | unlockTwTapPosition | External ❗️ |  💵 |NO❗️ |
| └ | _unlockTwTapPosition | Internal 🔒 | 🛑  | |
| └ | setTwTap | External ❗️ | 🛑  | onlyOwner |
| └ | <Receive Ether> | External ❗️ |  💵 |NO❗️ |
| └ | _callApproval | Private 🔐 | 🛑  | |
||||||
| **TwTAP** | Implementation | TWAML, ONFT721, ERC721Permit |||
| └ | <Constructor> | Public ❗️ | 🛑  | ONFT721 ERC721Permit |
| └ | currentWeek | Public ❗️ |   |NO❗️ |
| └ | getParticipation | Public ❗️ |   |NO❗️ |
| └ | claimable | Public ❗️ |   |NO❗️ |
| └ | participate | External ❗️ | 🛑  |NO❗️ |
| └ | claimRewards | External ❗️ | 🛑  |NO❗️ |
| └ | claimAndSendRewards | External ❗️ | 🛑  |NO❗️ |
| └ | releaseTap | External ❗️ | 🛑  |NO❗️ |
| └ | exitPosition | External ❗️ | 🛑  |NO❗️ |
| └ | exitPositionAndSendTap | External ❗️ | 🛑  |NO❗️ |
| └ | advanceWeek | Public ❗️ | 🛑  |NO❗️ |
| └ | distributeReward | External ❗️ | 🛑  |NO❗️ |
| └ | addRewardToken | External ❗️ | 🛑  | onlyOwner |
| └ | _requireClaimPermission | Internal 🔒 |   | |
| └ | _claimRewards | Internal 🔒 | 🛑  | |
| └ | _claimRewardsOn | Internal 🔒 | 🛑  | |
| └ | _releaseTap | Internal 🔒 | 🛑  | |
| └ | _getChainId | Internal 🔒 |   | |
| └ | supportsInterface | Public ❗️ |   |NO❗️ |
||||||
| **FullMath** | Implementation |  |||
| └ | muldiv | Internal 🔒 |   | |
||||||
| **TWAML** | Implementation | FullMath |||
| └ | computeMinWeight | Internal 🔒 |   | |
| └ | computeMagnitude | Internal 🔒 |   | |
| └ | computeTarget | Internal 🔒 |   | |
| └ | sqrt | Internal 🔒 |   | |


 Legend

|  Symbol  |  Meaning  |
|:--------:|-----------|
|    🛑    | Function can modify state |
|    💵    | Function is payable |


# Reference
oTAP.sol
TapiocaOptionBroker.sol