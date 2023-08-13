Summary
 - [arbitrary-send-erc20](#arbitrary-send-erc20) (1 results) (High)
 - [arbitrary-send-eth](#arbitrary-send-eth) (2 results) (High)
 - [controlled-delegatecall](#controlled-delegatecall) (5 results) (High)
 - [delegatecall-loop](#delegatecall-loop) (1 results) (High)
 - [encode-packed-collision](#encode-packed-collision) (1 results) (High)
 - [name-reused](#name-reused) (3 results) (High)
 - [uninitialized-state](#uninitialized-state) (30 results) (High)
 - [divide-before-multiply](#divide-before-multiply) (29 results) (Medium)
 - [incorrect-equality](#incorrect-equality) (10 results) (Medium)
 - [reentrancy-no-eth](#reentrancy-no-eth) (22 results) (Medium)
 - [unchecked-lowlevel](#unchecked-lowlevel) (2 results) (Medium)
 - [uninitialized-local](#uninitialized-local) (9 results) (Medium)
 - [unused-return](#unused-return) (16 results) (Medium)
 - [write-after-write](#write-after-write) (1 results) (Medium)
 - [shadowing-local](#shadowing-local) (12 results) (Low)
 - [missing-zero-check](#missing-zero-check) (10 results) (Low)
 - [calls-loop](#calls-loop) (4 results) (Low)
 - [reentrancy-benign](#reentrancy-benign) (25 results) (Low)
 - [reentrancy-events](#reentrancy-events) (65 results) (Low)
 - [timestamp](#timestamp) (19 results) (Low)
 - [assembly](#assembly) (31 results) (Informational)
 - [boolean-equal](#boolean-equal) (5 results) (Informational)
 - [pragma](#pragma) (1 results) (Informational)
 - [cyclomatic-complexity](#cyclomatic-complexity) (4 results) (Informational)
 - [dead-code](#dead-code) (3 results) (Informational)
 - [solc-version](#solc-version) (62 results) (Informational)
 - [low-level-calls](#low-level-calls) (22 results) (Informational)
 - [missing-inheritance](#missing-inheritance) (4 results) (Informational)
 - [naming-convention](#naming-convention) (206 results) (Informational)
 - [similar-names](#similar-names) (9 results) (Informational)
 - [too-many-digits](#too-many-digits) (6 results) (Informational)
 - [unimplemented-functions](#unimplemented-functions) (1 results) (Informational)
 - [unused-state](#unused-state) (26 results) (Informational)
 - [constable-states](#constable-states) (22 results) (Optimization)
 - [immutable-states](#immutable-states) (5 results) (Optimization)
## arbitrary-send-erc20
Impact: High
Confidence: High
 - [ ] ID-0
[YieldBox.depositAsset(uint256,address,address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L118-L160) uses arbitrary from in transferFrom: [IERC20(asset.contractAddress).safeTransferFrom(from,address(asset.strategy),amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L144)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L118-L160


## arbitrary-send-eth
Impact: High
Confidence: Medium
 - [ ] ID-1
[USDOLeverageModule.leverageUpInternal(uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageExternalContractsData,IUSDOBase.ILeverageLZData,address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L190-L252) sends eth to arbitrary user
        Dangerous calls:
        - [ITapiocaOFT(externalData.tOft).sendToYBAndBorrow{value: address(this).balance}(address(this),leverageFor,lzData.lzSrcChainId,lzData.srcAirdropAdapterParam,ITapiocaOFT.IBorrowParams(amountOut,0,externalData.magnetar,externalData.srcMarket),ICommonData.IWithdrawParams(false,0,false,0,0x),ICommonData.ISendOptions(lzData.srcExtraGasLimit,lzData.zroPaymentAddress),approvals)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L226-L251)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L190-L252


 - [ ] ID-2
[YieldBox.depositETHAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L196-L219) sends eth to arbitrary user
        Dangerous calls:
        - [wrappedNative.deposit{value: amount}()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L211)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L196-L219


## controlled-delegatecall
Impact: High
Confidence: Medium
 - [ ] ID-3
[USDOOptionsModule.exercise(address,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L138-L204) uses delegatecall to a input-controlled function id
        - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.exerciseInternal.selector,optionsData.from,optionsData.oTAPTokenID,optionsData.paymentToken,optionsData.tapAmount,optionsData.target,tapSendData,approvals))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L174-L185)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L138-L204


 - [ ] ID-4
[USDOMarketModule.lend(address,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L134-L189) uses delegatecall to a input-controlled function id
        - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.lendInternal.selector,to,lendParams,approvals,withdrawParams))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L168-L176)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L134-L189


 - [ ] ID-5
[Singularity._executeModule(Singularity.Module,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L618-L629) uses delegatecall to a input-controlled function id
        - [(success,returnData) = module.delegatecall(_data)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L625)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L618-L629


 - [ ] ID-6
[BaseUSDO._executeModule(BaseUSDO.Module,bytes,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L361-L373) uses delegatecall to a input-controlled function id
        - [(success,returnData) = module.delegatecall(_data)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L369)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L361-L373


 - [ ] ID-7
[USDOLeverageModule.leverageUp(address,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L133-L188) uses delegatecall to a input-controlled function id
        - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.leverageUpInternal.selector,amount,swapData,externalData,lzData,leverageFor))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L169-L178)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L133-L188


## delegatecall-loop
Impact: High
Confidence: Medium
 - [ ] ID-8
[BaseBoringBatchable.batch(bytes[],bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L38-L45) has delegatecall inside a loop in a payable function: [(success,result) = address(this).delegatecall(calls[i])](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L40)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L38-L45


## encode-packed-collision
Impact: High
Confidence: High
 - [ ] ID-9
[YieldBoxURIBuilder.uri(Asset,NativeToken,uint256,address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxURIBuilder.sol#L79-L135) calls abi.encodePacked() with multiple dynamic arguments:
        - [string(abi.encodePacked(data:application/json;base64,,abi.encodePacked({"name":",details.name,","symbol":",details.symbol,",,,,"properties":{"strategy":",uint256(uint160(address(asset.strategy))).toHexString(20),","tokenType":",details.tokenType,",properties,string(abi.encodePacked(,"tokenId":,asset.tokenId.toString())),}}).encode()))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxURIBuilder.sol#L110-L134)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxURIBuilder.sol#L79-L135


## name-reused
Impact: High
Confidence: High
 - [ ] ID-10
IERC165 is re-used:
        - [IERC165](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC165.sol#L4-L6)
        - [IERC165](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/introspection/IERC165.sol#L15-L25)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC165.sol#L4-L6


 - [ ] ID-11
ERC20 is re-used:
        - [ERC20](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/ERC20.sol#L19-L121)
        - [ERC20](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L35-L389)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/ERC20.sol#L19-L121


 - [ ] ID-12
IERC20 is re-used:
        - [IERC20](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC20.sol#L4-L30)
        - [IERC20](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol#L9-L82)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC20.sol#L4-L30


## uninitialized-state
Impact: High
Confidence: High
 - [ ] ID-13
[Market.assetId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L32) is never initialized. It is used in:
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)
        - [SGLCommon._addTokens(address,address,uint256,uint256,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L174-L194)
        - [SGLCommon._addAsset(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L197-L219)
        - [SGLCommon._removeAsset(address,address,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L223-L251)
        - [SGLLiquidation._orderBookLiquidation(address[],uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L97-L202)
        - [SGLLiquidation._extractLiquidationFees(uint256,uint256,address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L270-L292)
        - [SGLLiquidation._liquidateUser(address,uint256,ISwapper,uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L294-L368)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L32


 - [ ] ID-14
[Market.EXCHANGE_RATE_PRECISION](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L82) is never initialized. It is used in:
        - [Market._computeMaxBorrowableAmount(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L385-L398)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [Market._computeMaxAndMinLTVInAsset(uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L428-L440)
        - [SGLLiquidation._computeAssetAmountToSolvency(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L70-L95)
        - [SGLLiquidation._orderBookLiquidation(address[],uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L97-L202)
        - [SGLLiquidation._updateBorrowAndCollateralShare(address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L204-L268)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L82


 - [ ] ID-15
[Market.assetId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L32) is never initialized. It is used in:
        - [SGLLendingCommon._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L58-L80)
        - [SGLLendingCommon._repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98)
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)
        - [SGLCommon._addTokens(address,address,uint256,uint256,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L174-L194)
        - [SGLCommon._addAsset(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L197-L219)
        - [SGLCommon._removeAsset(address,address,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L223-L251)
        - [SGLLeverage.multiHopBuyCollateral(address,uint256,uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageExternalContractsData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L21-L56)
        - [SGLLeverage.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137)
        - [SGLLeverage.buyCollateral(address,uint256,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L147-L186)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L32


 - [ ] ID-16
[SGLStorage.liquidationQueue](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L46) is never initialized. It is used in:
        - [SGLLiquidation.liquidate(address[],uint256[],ISwapper,bytes,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L29-L65)
        - [SGLLiquidation._orderBookLiquidation(address[],uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L97-L202)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L46


 - [ ] ID-17
[Market.assetId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L32) is never initialized. It is used in:
        - [SGLLendingCommon._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L58-L80)
        - [SGLLendingCommon._repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98)
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)
        - [SGLCommon._addTokens(address,address,uint256,uint256,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L174-L194)
        - [SGLCommon._addAsset(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L197-L219)
        - [SGLCommon._removeAsset(address,address,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L223-L251)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L32


 - [ ] ID-18
[Market.penrose](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L23) is never initialized. It is used in:
        - [SGLLeverage.multiHopBuyCollateral(address,uint256,uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageExternalContractsData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L21-L56)
        - [SGLLeverage.multiHopSellCollateral(address,uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageExternalContractsData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L58-L88)
        - [SGLLeverage.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137)
        - [SGLLeverage.buyCollateral(address,uint256,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L147-L186)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L23


 - [ ] ID-19
[Market.userCollateralShare](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L59) is never initialized. It is used in:
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [Market.computeLiquidatorReward(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L356-L365)
        - [Market._computeMaxBorrowableAmount(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L385-L398)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [Market._computeAllowanceAmountInAsset(address,uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L464-L478)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L59


 - [ ] ID-20
[SGLStorage.fullUtilizationMinusMax](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L59) is never initialized. It is used in:
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L59


 - [ ] ID-21
[SGLStorage.minimumInterestPerSecond](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L61) is never initialized. It is used in:
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L61


 - [ ] ID-22
[SGLStorage.startingInterestPerSecond](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L64) is never initialized. It is used in:
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)
        - [SGLCommon._accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L139-L163)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L64


 - [ ] ID-23
[SGLStorage.interestElasticity](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L63) is never initialized. It is used in:
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L63


 - [ ] ID-24
[Market.asset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L30) is never initialized. It is used in:
        - [SGLStorage.symbol()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L154-L166)
        - [SGLStorage.name()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L169-L181)
        - [SGLStorage.decimals()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L184-L186)
        - [SGLLeverage.multiHopBuyCollateral(address,uint256,uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageExternalContractsData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L21-L56)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L30


 - [ ] ID-25
[SGLStorage.minimumTargetUtilization](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L57) is never initialized. It is used in:
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L57


 - [ ] ID-26
[Market.collateralId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L28) is never initialized. It is used in:
        - [SGLLendingCommon._addCollateral(address,address,bool,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L16-L38)
        - [SGLLendingCommon._removeCollateral(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L41-L55)
        - [Market._computeMaxBorrowableAmount(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L385-L398)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [Market._computeMaxAndMinLTVInAsset(uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L428-L440)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L28


 - [ ] ID-27
[Market.asset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L30) is never initialized. It is used in:
        - [SGLStorage.symbol()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L154-L166)
        - [SGLStorage.name()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L169-L181)
        - [SGLStorage.decimals()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L184-L186)
        - [SGLLiquidation._updateBorrowAndCollateralShare(address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L204-L268)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L30


 - [ ] ID-28
[Market.collateral](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L26) is never initialized. It is used in:
        - [SGLStorage.symbol()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L154-L166)
        - [SGLStorage.name()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L169-L181)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L26


 - [ ] ID-29
[Market.collateral](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L26) is never initialized. It is used in:
        - [SGLStorage.symbol()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L154-L166)
        - [SGLStorage.name()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L169-L181)
        - [SGLLiquidation._updateBorrowAndCollateralShare(address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L204-L268)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L26


 - [ ] ID-30
[Market.asset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L30) is never initialized. It is used in:
        - [SGLStorage.symbol()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L154-L166)
        - [SGLStorage.name()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L169-L181)
        - [SGLStorage.decimals()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L184-L186)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L30


 - [ ] ID-31
[Market.yieldBox](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L21) is never initialized. It is used in:
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)
        - [SGLCommon._addTokens(address,address,uint256,uint256,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L174-L194)
        - [SGLCommon._addAsset(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L197-L219)
        - [SGLCommon._removeAsset(address,address,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L223-L251)
        - [Market._computeMaxBorrowableAmount(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L385-L398)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [Market._computeMaxAndMinLTVInAsset(uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L428-L440)
        - [SGLLiquidation._computeAssetAmountToSolvency(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L70-L95)
        - [SGLLiquidation._orderBookLiquidation(address[],uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L97-L202)
        - [SGLLiquidation._updateBorrowAndCollateralShare(address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L204-L268)
        - [SGLLiquidation._extractLiquidationFees(uint256,uint256,address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L270-L292)
        - [SGLLiquidation._liquidateUser(address,uint256,ISwapper,uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L294-L368)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L21


 - [ ] ID-32
[SGLStorage.maximumTargetUtilization](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L58) is never initialized. It is used in:
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L58


 - [ ] ID-33
[Market.yieldBox](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L21) is never initialized. It is used in:
        - [SGLLendingCommon._addCollateral(address,address,bool,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L16-L38)
        - [SGLLendingCommon._removeCollateral(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L41-L55)
        - [SGLLendingCommon._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L58-L80)
        - [SGLLendingCommon._repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98)
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)
        - [SGLCommon._addTokens(address,address,uint256,uint256,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L174-L194)
        - [SGLCommon._addAsset(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L197-L219)
        - [SGLCommon._removeAsset(address,address,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L223-L251)
        - [Market._computeMaxBorrowableAmount(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L385-L398)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [Market._computeMaxAndMinLTVInAsset(uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L428-L440)
        - [SGLLeverage.multiHopBuyCollateral(address,uint256,uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageExternalContractsData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L21-L56)
        - [SGLLeverage.multiHopSellCollateral(address,uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageExternalContractsData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L58-L88)
        - [SGLLeverage.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137)
        - [SGLLeverage.buyCollateral(address,uint256,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L147-L186)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L21


 - [ ] ID-34
[Market.collateralId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L28) is never initialized. It is used in:
        - [SGLLendingCommon._addCollateral(address,address,bool,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L16-L38)
        - [SGLLendingCommon._removeCollateral(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L41-L55)
        - [Market._computeMaxBorrowableAmount(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L385-L398)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [Market._computeMaxAndMinLTVInAsset(uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L428-L440)
        - [SGLLeverage.multiHopBuyCollateral(address,uint256,uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageExternalContractsData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L21-L56)
        - [SGLLeverage.multiHopSellCollateral(address,uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageExternalContractsData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L58-L88)
        - [SGLLeverage.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137)
        - [SGLLeverage.buyCollateral(address,uint256,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L147-L186)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L28


 - [ ] ID-35
[Market.collateralId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L28) is never initialized. It is used in:
        - [Market._computeMaxBorrowableAmount(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L385-L398)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [Market._computeMaxAndMinLTVInAsset(uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L428-L440)
        - [SGLLiquidation._computeAssetAmountToSolvency(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L70-L95)
        - [SGLLiquidation._orderBookLiquidation(address[],uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L97-L202)
        - [SGLLiquidation._updateBorrowAndCollateralShare(address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L204-L268)
        - [SGLLiquidation._liquidateUser(address,uint256,ISwapper,uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L294-L368)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L28


 - [ ] ID-36
[Market.yieldBox](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L21) is never initialized. It is used in:
        - [SGLLendingCommon._addCollateral(address,address,bool,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L16-L38)
        - [SGLLendingCommon._removeCollateral(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L41-L55)
        - [SGLLendingCommon._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L58-L80)
        - [SGLLendingCommon._repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98)
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)
        - [SGLCommon._addTokens(address,address,uint256,uint256,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L174-L194)
        - [SGLCommon._addAsset(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L197-L219)
        - [SGLCommon._removeAsset(address,address,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L223-L251)
        - [Market._computeMaxBorrowableAmount(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L385-L398)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [Market._computeMaxAndMinLTVInAsset(uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L428-L440)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L21


 - [ ] ID-37
[Market.collateral](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L26) is never initialized. It is used in:
        - [SGLStorage.symbol()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L154-L166)
        - [SGLStorage.name()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L169-L181)
        - [SGLLeverage.multiHopSellCollateral(address,uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageExternalContractsData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L58-L88)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L26


 - [ ] ID-38
[Market.penrose](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L23) is never initialized. It is used in:
        - [SGLLiquidation._extractLiquidationFees(uint256,uint256,address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L270-L292)
        - [SGLLiquidation._liquidateUser(address,uint256,ISwapper,uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L294-L368)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L23


 - [ ] ID-39
[Market.EXCHANGE_RATE_PRECISION](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L82) is never initialized. It is used in:
        - [Market._computeMaxBorrowableAmount(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L385-L398)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [Market._computeMaxAndMinLTVInAsset(uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L428-L440)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L82


 - [ ] ID-40
[Market.asset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L30) is never initialized. It is used in:
        - [SGLStorage.symbol()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L154-L166)
        - [SGLStorage.name()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L169-L181)
        - [SGLStorage.decimals()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L184-L186)
        - [SGLBorrow.borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L21-L36)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L30


 - [ ] ID-41
[SGLStorage.maximumInterestPerSecond](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L62) is never initialized. It is used in:
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L62


 - [ ] ID-42
[Market.userBorrowPart](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L57) is never initialized. It is used in:
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [Market.computeLiquidatorReward(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L356-L365)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L57


## divide-before-multiply
Impact: Medium
Confidence: Medium
 - [ ] ID-43
[Base64.encode(bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L11-L69) performs a multiplication on the result of a division:
        - [encodedLen = 4 * ((data.length + 2) / 3)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L18)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L11-L69


 - [ ] ID-44
[Market._computeMaxAndMinLTVInAsset(uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L428-L440) performs a multiplication on the result of a division:
        - [max = (collateralAmount * EXCHANGE_RATE_PRECISION) / _exchangeRate](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L438)
        - [min = (max * collateralizationRate) / FEE_PRECISION](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L439)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L428-L440


 - [ ] ID-45
[BytesLib.concatStorage(bytes,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226) performs a multiplication on the result of a division:
        - [sstore(uint256,uint256)(sc_concatStorage_asm_0,mload(uint256)(mc_concatStorage_asm_0) / mask_concatStorage_asm_0 * mask_concatStorage_asm_0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L223)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226


 - [ ] ID-46
[BytesLib.concatStorage(bytes,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226) performs a multiplication on the result of a division:
        - [sstore(uint256,uint256)(_preBytes,fslot_concatStorage_asm_0 + mload(uint256)(_postBytes + 0x20) / 0x100 ** 32 - mlength_concatStorage_asm_0 * 0x100 ** 32 - newlength_concatStorage_asm_0 + mlength_concatStorage_asm_0 * 2)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L115-L140)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226


 - [ ] ID-47
[Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425) performs a multiplication on the result of a division:
        - [yieldBox.toAmount(collateralId,collateralShare * (EXCHANGE_RATE_PRECISION / FEE_PRECISION) * collateralizationRate,false) >= (borrowPart * _totalBorrow.elastic * _exchangeRate) / _totalBorrow.base](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L414-L424)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425


 - [ ] ID-48
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L126)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-49
[SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137) performs a multiplication on the result of a division:
        - [feeAmount = (extraAmount * protocolFee) / FEE_PRECISION](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L106)
        - [feeFraction = (feeAmount * _totalAsset.base) / fullAssetAmount](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L107)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137


 - [ ] ID-50
[SGLLiquidation._computeAssetAmountToSolvency(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L70-L95) performs a multiplication on the result of a division:
        - [collateralAmountInAsset = yieldBox.toAmount(collateralId,(collateralShare * (EXCHANGE_RATE_PRECISION / FEE_PRECISION) * lqCollateralizationRate),false) / _exchangeRate](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L81-L87)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L70-L95


 - [ ] ID-51
[BigBang.getDebtRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L180-L201) performs a multiplication on the result of a division:
        - [debtPercentage = ((_currentDebt - debtStartPoint) * DEBT_PRECISION) / (_maxDebtPoint - debtStartPoint)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L192-L193)
        - [debt = ((maxDebtRate - minDebtRate) * debtPercentage) / DEBT_PRECISION + minDebtRate](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L194-L196)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L180-L201


 - [ ] ID-52
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L124)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-53
[SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137) performs a multiplication on the result of a division:
        - [underFactor = ((minimumTargetUtilization - utilization) * FACTOR_PRECISION) / minimumTargetUtilization](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L113-L114)
        - [scale = interestElasticity + (underFactor * underFactor * elapsedTime)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L115-L116)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137


 - [ ] ID-54
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L123)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-55
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L121)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-56
[Market._computeMaxBorrowableAmount(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L385-L398) performs a multiplication on the result of a division:
        - [collateralAmountInAsset = yieldBox.toAmount(collateralId,(userCollateralShare[user] * (EXCHANGE_RATE_PRECISION / FEE_PRECISION) * collateralizationRate),false) / _exchangeRate](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L389-L397)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L385-L398


 - [ ] ID-57
[Market.computeClosingFactor(uint256,uint256,uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L256-L297) performs a multiplication on the result of a division:
        - [collateralPartInAssetScaled = collateralPartInAsset / (10 ** (collateralPartDecimals - 18))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L273-L275)
        - [liquidationStartsAt = (collateralPartInAssetScaled * collateralizationRate) / (10 ** ratesPrecision)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L283-L284)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L256-L297


 - [ ] ID-58
[BytesLib.equalStorage(bytes,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L439-L509) performs a multiplication on the result of a division:
        - [fslot_equalStorage_asm_0 = fslot_equalStorage_asm_0 / 0x100 * 0x100](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L466)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L439-L509


 - [ ] ID-59
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
        - [inverse = (3 * denominator) ^ 2](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L117)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-60
[BytesLib.concatStorage(bytes,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226) performs a multiplication on the result of a division:
        - [sstore(uint256,uint256)(sc_concatStorage_asm_0,mload(uint256)(mc_concatStorage_asm_0) / mask_concatStorage_asm_0 * mask_concatStorage_asm_0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L189)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226


 - [ ] ID-61
[SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137) performs a multiplication on the result of a division:
        - [overFactor = ((utilization - maximumTargetUtilization) * FACTOR_PRECISION) / fullUtilizationMinusMax](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L125-L126)
        - [scale_scope_0 = interestElasticity + (overFactor * overFactor * elapsedTime)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L127-L128)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137


 - [ ] ID-62
[RebaseLibrary.toBase(Rebase,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L12-L25) performs a multiplication on the result of a division:
        - [base = (elastic * total.base) / total.elastic](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L20)
        - [roundUp && (base * total.elastic) / total.base < elastic](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L21)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L12-L25


 - [ ] ID-63
[YieldBoxRebase._toAmount(uint256,uint256,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L41-L61) performs a multiplication on the result of a division:
        - [amount = (share * totalAmount) / totalShares_](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L55)
        - [roundUp && (amount * totalShares_) / totalAmount < share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L58)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L41-L61


 - [ ] ID-64
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L122)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-65
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [prod0 = prod0 / twos](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L105)
        - [result = prod0 * inverse](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L132)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-66
[Market.computeClosingFactor(uint256,uint256,uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L256-L297) performs a multiplication on the result of a division:
        - [collateralPartInAssetScaled = collateralPartInAsset / (10 ** (collateralPartDecimals - 18))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L273-L275)
        - [numerator = borrowPartScaled - ((collateralizationRate * collateralPartInAssetScaled) / (10 ** ratesPrecision))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L287-L289)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L256-L297


 - [ ] ID-67
[SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137) performs a multiplication on the result of a division:
        - [extraAmount = (uint256(_totalBorrow.elastic) * _accrueInfo.interestPerSecond * elapsedTime) / 1e18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L99-L103)
        - [feeAmount = (extraAmount * protocolFee) / FEE_PRECISION](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L106)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137


 - [ ] ID-68
[YieldBoxRebase._toShares(uint256,uint256,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L18-L38) performs a multiplication on the result of a division:
        - [share = (amount * totalShares_) / totalAmount](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L32)
        - [roundUp && (share * totalAmount) / totalShares_ < amount](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L35)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L18-L38


 - [ ] ID-69
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L125)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-70
[BoringMath.muldiv(uint256,uint256,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/BoringMath.sol#L20-L30) performs a multiplication on the result of a division:
        - [result = (value * mul) / div](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/BoringMath.sol#L26)
        - [roundUp && (result * div) / mul < value](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/BoringMath.sol#L27)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/BoringMath.sol#L20-L30


 - [ ] ID-71
[RebaseLibrary.toElastic(Rebase,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L28-L41) performs a multiplication on the result of a division:
        - [elastic = (base * total.elastic) / total.base](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L36)
        - [roundUp && (elastic * total.base) / total.elastic < base](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L37)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L28-L41


## incorrect-equality
Impact: Medium
Confidence: High
 - [ ] ID-72
[Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425) uses a dangerous strict equality:
        - [borrowPart == 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L408)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425


 - [ ] ID-73
[SGLCommon._removeAsset(address,address,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L223-L251) uses a dangerous strict equality:
        - [totalAsset.base == 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L229)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L223-L251


 - [ ] ID-74
[SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137) uses a dangerous strict equality:
        - [_totalBorrow.base == 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L81)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137


 - [ ] ID-75
[SGLLiquidation._orderBookLiquidation(address[],uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L97-L202) uses a dangerous strict equality:
        - [borrowAmount == 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L115)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L97-L202


 - [ ] ID-76
[BigBang.getDebtRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L180-L201) uses a dangerous strict equality:
        - [totalBorrow.elastic == 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L182)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L180-L201


 - [ ] ID-77
[Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333) uses a dangerous strict equality:
        - [borrowPart == 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L314)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333


 - [ ] ID-78
[BigBang._accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L512-L541) uses a dangerous strict equality:
        - [elapsedTime == 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L516)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L512-L541


 - [ ] ID-79
[SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137) uses a dangerous strict equality:
        - [fullAssetAmount == 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L61-L64)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137


 - [ ] ID-80
[SGLCommon._addAsset(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L197-L219) uses a dangerous strict equality:
        - [allShare == 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L207-L209)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L197-L219


 - [ ] ID-81
[SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137) uses a dangerous strict equality:
        - [elapsedTime == 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L68)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137


## reentrancy-no-eth
Impact: Medium
Confidence: Medium
 - [ ] ID-82
Reentrancy in [BigBang.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424):
        External calls:
        - [_removeCollateral(from,address(swapper),share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L394)
                - [yieldBox.transfer(address(this),to,collateralId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L717)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L390)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_removeCollateral(from,address(swapper),share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L394)
                - [userCollateralShare[from] -= share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L714)
        [Market.userCollateralShare](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L59) can be used in cross function reentrancies:
        - [BigBang._addCollateral(address,address,bool,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L543-L558)
        - [Market._computeAllowanceAmountInAsset(address,uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L464-L478)
        - [Market._computeMaxBorrowableAmount(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L385-L398)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [BigBang._liquidateUser(address,uint256,ISwapper,uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L560-L637)
        - [BigBang._removeCollateral(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L709-L718)
        - [BigBang._updateBorrowAndCollateralShare(address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L769-L824)
        - [Market.computeLiquidatorReward(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L356-L365)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [Market.userCollateralShare](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L59)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424


 - [ ] ID-83
Reentrancy in [SGLLiquidation._orderBookLiquidation(address[],uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L97-L202):
        External calls:
        - [yieldBox.transfer(address(this),address(liquidationQueue),collateralId,allCollateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L166-L171)
        - [liquidationQueue.executeBids(yieldBox.toAmount(collateralId,allCollateralShare,true),swapData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L174-L177)
        - [yieldBox.transfer(address(this),msg.sender,assetId,callerShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L193)
        State variables written after the call(s):
        - [totalAsset.elastic += uint128(returnedShare - callerShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L195)
        [SGLStorage.totalAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L44) can be used in cross function reentrancies:
        - [SGLCommon._accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L139-L163)
        - [SGLLiquidation._extractLiquidationFees(uint256,uint256,address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L270-L292)
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)
        - [SGLLiquidation._orderBookLiquidation(address[],uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L97-L202)
        - [SGLStorage.totalAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L44)
        - [SGLStorage.totalSupply()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L191-L193)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L97-L202


 - [ ] ID-84
Reentrancy in [SGLLeverage.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137):
        External calls:
        - [_removeCollateral(from,address(swapper),share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L107)
                - [yieldBox.transfer(address(this),to,collateralId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L49)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L103)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_removeCollateral(from,address(swapper),share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L107)
                - [userCollateralShare[from] -= share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L46)
        [Market.userCollateralShare](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L59) can be used in cross function reentrancies:
        - [SGLLendingCommon._addCollateral(address,address,bool,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L16-L38)
        - [Market._computeMaxBorrowableAmount(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L385-L398)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [SGLLendingCommon._removeCollateral(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L41-L55)
        - [Market.computeLiquidatorReward(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L356-L365)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [Market.userCollateralShare](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L59)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137


 - [ ] ID-85
Reentrancy in [BigBang.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424):
        External calls:
        - [_removeCollateral(from,address(swapper),share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L394)
                - [yieldBox.transfer(address(this),to,collateralId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L717)
        - [(amountOut,shareOut) = swapper.swap(swapData,minAmountOut,from,dexData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L404-L409)
        - [_repay(from,from,partOut)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L422)
                - [yieldBox.withdraw(assetId,from,address(this),amount,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L732)
                - [IUSDOBase(address(asset)).burn(address(this),toBurn)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L735)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L390)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_repay(from,from,partOut)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L422)
                - [(totalBorrow,amount) = totalBorrow.sub(part,true)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L726)
        [Market.totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L51) can be used in cross function reentrancies:
        - [BigBang._accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L512-L541)
        - [BigBang._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L742-L767)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [BigBang._repay(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L721-L739)
        - [BigBang._updateBorrowAndCollateralShare(address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L769-L824)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [BigBang.getDebtRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L180-L201)
        - [BigBang.getTotalDebt()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L175-L177)
        - [BigBang.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424)
        - [Market.totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L51)
        - [_repay(from,from,partOut)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L422)
                - [userBorrowPart[to] -= part](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L728)
        [Market.userBorrowPart](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L57) can be used in cross function reentrancies:
        - [BigBang._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L742-L767)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [BigBang._liquidateUser(address,uint256,ISwapper,uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L560-L637)
        - [BigBang._repay(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L721-L739)
        - [BigBang._updateBorrowAndCollateralShare(address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L769-L824)
        - [Market.computeLiquidatorReward(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L356-L365)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [BigBang.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424)
        - [Market.userBorrowPart](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L57)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424


 - [ ] ID-86
Reentrancy in [SGLBorrow.borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L21-L36):
        External calls:
        - [(part,share) = _borrow(from,to,amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L35)
                - [yieldBox.transfer(address(this),to,assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L79)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L25)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [(part,share) = _borrow(from,to,amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L35)
                - [totalAsset = _totalAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L77)
        [SGLStorage.totalAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L44) can be used in cross function reentrancies:
        - [SGLCommon._accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L139-L163)
        - [SGLLendingCommon._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L58-L80)
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)
        - [SGLLendingCommon._repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98)
        - [SGLStorage.totalAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L44)
        - [SGLStorage.totalSupply()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L191-L193)
        - [(part,share) = _borrow(from,to,amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L35)
                - [(totalBorrow,part) = totalBorrow.add(amount + feeAmount,true)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L65)
        [Market.totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L51) can be used in cross function reentrancies:
        - [SGLCommon._accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L139-L163)
        - [SGLLendingCommon._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L58-L80)
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [SGLLendingCommon._repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [Market.totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L51)
        - [(part,share) = _borrow(from,to,amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L35)
                - [userBorrowPart[from] += part](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L70)
        [Market.userBorrowPart](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L57) can be used in cross function reentrancies:
        - [SGLLendingCommon._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L58-L80)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [SGLLendingCommon._repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98)
        - [Market.computeLiquidatorReward(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L356-L365)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [Market.userBorrowPart](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L57)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L21-L36


 - [ ] ID-87
Reentrancy in [BigBang.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424):
        External calls:
        - [_removeCollateral(from,address(swapper),share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L394)
                - [yieldBox.transfer(address(this),to,collateralId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L717)
        - [(amountOut,shareOut) = swapper.swap(swapData,minAmountOut,from,dexData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L404-L409)
        - [_repay(from,from,partOwed)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L418)
                - [yieldBox.withdraw(assetId,from,address(this),amount,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L732)
                - [IUSDOBase(address(asset)).burn(address(this),toBurn)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L735)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L390)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_repay(from,from,partOwed)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L418)
                - [(totalBorrow,amount) = totalBorrow.sub(part,true)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L726)
        [Market.totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L51) can be used in cross function reentrancies:
        - [BigBang._accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L512-L541)
        - [BigBang._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L742-L767)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [BigBang._repay(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L721-L739)
        - [BigBang._updateBorrowAndCollateralShare(address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L769-L824)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [BigBang.getDebtRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L180-L201)
        - [BigBang.getTotalDebt()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L175-L177)
        - [BigBang.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424)
        - [Market.totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L51)
        - [_repay(from,from,partOwed)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L418)
                - [userBorrowPart[to] -= part](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L728)
        [Market.userBorrowPart](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L57) can be used in cross function reentrancies:
        - [BigBang._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L742-L767)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [BigBang._liquidateUser(address,uint256,ISwapper,uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L560-L637)
        - [BigBang._repay(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L721-L739)
        - [BigBang._updateBorrowAndCollateralShare(address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L769-L824)
        - [Market.computeLiquidatorReward(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L356-L365)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [BigBang.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424)
        - [Market.userBorrowPart](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L57)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424


 - [ ] ID-88
Reentrancy in [BigBang.borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L242-L255):
        External calls:
        - [(part,share) = _borrow(from,to,amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L254)
                - [IUSDOBase(address(asset)).mint(address(this),amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L758)
                - [asset.approve(address(yieldBox),amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L761)
                - [yieldBox.depositAsset(assetId,address(this),to,amount,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L762)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L246)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [(part,share) = _borrow(from,to,amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L254)
                - [(totalBorrow,part) = totalBorrow.add(amount + feeAmount,true)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L749)
        [Market.totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L51) can be used in cross function reentrancies:
        - [BigBang._accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L512-L541)
        - [BigBang._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L742-L767)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [BigBang._repay(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L721-L739)
        - [BigBang._updateBorrowAndCollateralShare(address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L769-L824)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [BigBang.getDebtRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L180-L201)
        - [BigBang.getTotalDebt()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L175-L177)
        - [BigBang.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424)
        - [Market.totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L51)
        - [(part,share) = _borrow(from,to,amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L254)
                - [userBorrowPart[from] += part](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L755)
        [Market.userBorrowPart](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L57) can be used in cross function reentrancies:
        - [BigBang._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L742-L767)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [BigBang._liquidateUser(address,uint256,ISwapper,uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L560-L637)
        - [BigBang._repay(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L721-L739)
        - [BigBang._updateBorrowAndCollateralShare(address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L769-L824)
        - [Market.computeLiquidatorReward(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L356-L365)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [BigBang.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424)
        - [Market.userBorrowPart](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L57)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L242-L255


 - [ ] ID-89
Reentrancy in [BigBang.buyCollateral(address,uint256,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L336-L375):
        External calls:
        - [yieldBox.transfer(from,address(swapper),assetId,supplyShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L349)
        - [(None,borrowShare) = _borrow(from,address(swapper),borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L353)
                - [IUSDOBase(address(asset)).mint(address(this),amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L758)
                - [asset.approve(address(yieldBox),amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L761)
                - [yieldBox.depositAsset(assetId,address(this),to,amount,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L762)
        - [(amountOut,collateralShare) = swapper.swap(swapData,minAmountOut,from,dexData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L365-L370)
        - [_addCollateral(from,from,false,0,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L374)
                - [yieldBox.transfer(from,address(this),_tokenId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L704)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L343)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_addCollateral(from,from,false,0,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L374)
                - [userCollateralShare[to] += share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L553)
        [Market.userCollateralShare](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L59) can be used in cross function reentrancies:
        - [BigBang._addCollateral(address,address,bool,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L543-L558)
        - [Market._computeAllowanceAmountInAsset(address,uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L464-L478)
        - [Market._computeMaxBorrowableAmount(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L385-L398)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [BigBang._liquidateUser(address,uint256,ISwapper,uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L560-L637)
        - [BigBang._removeCollateral(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L709-L718)
        - [BigBang._updateBorrowAndCollateralShare(address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L769-L824)
        - [Market.computeLiquidatorReward(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L356-L365)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [Market.userCollateralShare](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L59)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L336-L375


 - [ ] ID-90
Reentrancy in [BigBang.removeCollateral(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L296-L302):
        External calls:
        - [_removeCollateral(from,to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L301)
                - [yieldBox.transfer(address(this),to,collateralId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L717)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L300)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_removeCollateral(from,to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L301)
                - [userCollateralShare[from] -= share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L714)
        [Market.userCollateralShare](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L59) can be used in cross function reentrancies:
        - [BigBang._addCollateral(address,address,bool,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L543-L558)
        - [Market._computeAllowanceAmountInAsset(address,uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L464-L478)
        - [Market._computeMaxBorrowableAmount(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L385-L398)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [BigBang._liquidateUser(address,uint256,ISwapper,uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L560-L637)
        - [BigBang._removeCollateral(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L709-L718)
        - [BigBang._updateBorrowAndCollateralShare(address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L769-L824)
        - [Market.computeLiquidatorReward(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L356-L365)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [Market.userCollateralShare](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L59)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L296-L302


 - [ ] ID-91
Reentrancy in [SGLLeverage.multiHopSellCollateral(address,uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageExternalContractsData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L58-L88):
        External calls:
        - [_removeCollateral(from,address(this),share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L71)
                - [yieldBox.transfer(address(this),to,collateralId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L49)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L64)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_removeCollateral(from,address(this),share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L71)
                - [userCollateralShare[from] -= share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L46)
        [Market.userCollateralShare](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L59) can be used in cross function reentrancies:
        - [SGLLendingCommon._addCollateral(address,address,bool,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L16-L38)
        - [Market._computeMaxBorrowableAmount(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L385-L398)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [SGLLendingCommon._removeCollateral(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L41-L55)
        - [Market.computeLiquidatorReward(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L356-L365)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [Market.userCollateralShare](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L59)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L58-L88


 - [ ] ID-92
Reentrancy in [SGLLeverage.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137):
        External calls:
        - [_removeCollateral(from,address(swapper),share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L107)
                - [yieldBox.transfer(address(this),to,collateralId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L49)
        - [(amountOut,shareOut) = swapper.swap(swapData,minAmountOut,from,dexData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L117-L122)
        - [_repay(from,from,false,partOut)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L135)
                - [yieldBox.transfer(from,address(this),_assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L192)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L103)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_repay(from,from,false,partOut)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L135)
                - [_yieldBoxShares[to][_asset_sig] += share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L184)
        [SGLStorage._yieldBoxShares](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L49) can be used in cross function reentrancies:
        - [SGLCommon._addTokens(address,address,uint256,uint256,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L174-L194)
        - [SGLLendingCommon._removeCollateral(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L41-L55)
        - [_repay(from,from,false,partOut)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L135)
                - [totalAsset.elastic = totalShare + uint128(share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L96)
        [SGLStorage.totalAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L44) can be used in cross function reentrancies:
        - [SGLCommon._accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L139-L163)
        - [SGLLendingCommon._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L58-L80)
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)
        - [SGLLendingCommon._repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98)
        - [SGLStorage.totalAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L44)
        - [SGLStorage.totalSupply()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L191-L193)
        - [_repay(from,from,false,partOut)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L135)
                - [(totalBorrow,amount) = totalBorrow.sub(part,true)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L89)
        [Market.totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L51) can be used in cross function reentrancies:
        - [SGLCommon._accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L139-L163)
        - [SGLLendingCommon._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L58-L80)
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [SGLLendingCommon._repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [SGLLeverage.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137)
        - [Market.totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L51)
        - [_repay(from,from,false,partOut)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L135)
                - [userBorrowPart[to] -= part](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L91)
        [Market.userBorrowPart](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L57) can be used in cross function reentrancies:
        - [SGLLendingCommon._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L58-L80)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [SGLLendingCommon._repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98)
        - [Market.computeLiquidatorReward(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L356-L365)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [SGLLeverage.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137)
        - [Market.userBorrowPart](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L57)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137


 - [ ] ID-93
Reentrancy in [SGLLendingCommon._repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98):
        External calls:
        - [_addTokens(from,to,assetId,share,uint256(totalShare),skim)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L95)
                - [yieldBox.transfer(from,address(this),_assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L192)
        State variables written after the call(s):
        - [totalAsset.elastic = totalShare + uint128(share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L96)
        [SGLStorage.totalAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L44) can be used in cross function reentrancies:
        - [SGLCommon._accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L139-L163)
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)
        - [SGLStorage.totalAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L44)
        - [SGLStorage.totalSupply()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L191-L193)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98


 - [ ] ID-94
Reentrancy in [BigBang.refreshPenroseFees(address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L442-L462):
        External calls:
        - [asset.approve(address(yieldBox),totalFees)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L450)
        - [yieldBox.depositAsset(assetId,address(this),msg.sender,totalFees,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L452-L458)
        State variables written after the call(s):
        - [totalFees = 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L460)
        [BigBang.totalFees](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L50) can be used in cross function reentrancies:
        - [BigBang.refreshPenroseFees(address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L442-L462)
        - [BigBang.totalFees](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L50)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L442-L462


 - [ ] ID-95
Reentrancy in [SGLCollateral.removeCollateral(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCollateral.sol#L35-L41):
        External calls:
        - [_removeCollateral(from,to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCollateral.sol#L40)
                - [yieldBox.transfer(address(this),to,collateralId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L49)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCollateral.sol#L39)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_removeCollateral(from,to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCollateral.sol#L40)
                - [userCollateralShare[from] -= share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L46)
        [Market.userCollateralShare](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L59) can be used in cross function reentrancies:
        - [SGLLendingCommon._addCollateral(address,address,bool,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L16-L38)
        - [Market._computeMaxBorrowableAmount(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L385-L398)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [SGLLendingCommon._removeCollateral(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L41-L55)
        - [Market.computeLiquidatorReward(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L356-L365)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [Market.userCollateralShare](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L59)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCollateral.sol#L35-L41


 - [ ] ID-96
Reentrancy in [SGLLeverage.buyCollateral(address,uint256,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L147-L186):
        External calls:
        - [yieldBox.transfer(from,address(swapper),assetId,supplyShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L160)
        - [(None,borrowShare) = _borrow(from,address(swapper),borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L164)
                - [yieldBox.transfer(address(this),to,assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L79)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L154)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [(None,borrowShare) = _borrow(from,address(swapper),borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L164)
                - [totalAsset = _totalAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L77)
        [SGLStorage.totalAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L44) can be used in cross function reentrancies:
        - [SGLCommon._accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L139-L163)
        - [SGLLendingCommon._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L58-L80)
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)
        - [SGLLendingCommon._repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98)
        - [SGLStorage.totalAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L44)
        - [SGLStorage.totalSupply()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L191-L193)
        - [(None,borrowShare) = _borrow(from,address(swapper),borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L164)
                - [(totalBorrow,part) = totalBorrow.add(amount + feeAmount,true)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L65)
        [Market.totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L51) can be used in cross function reentrancies:
        - [SGLCommon._accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L139-L163)
        - [SGLLendingCommon._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L58-L80)
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [SGLLendingCommon._repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [SGLLeverage.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137)
        - [Market.totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L51)
        - [(None,borrowShare) = _borrow(from,address(swapper),borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L164)
                - [userBorrowPart[from] += part](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L70)
        [Market.userBorrowPart](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L57) can be used in cross function reentrancies:
        - [SGLLendingCommon._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L58-L80)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [SGLLendingCommon._repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98)
        - [Market.computeLiquidatorReward(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L356-L365)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [SGLLeverage.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137)
        - [Market.userBorrowPart](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L57)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L147-L186


 - [ ] ID-97
Reentrancy in [SGLLeverage.buyCollateral(address,uint256,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L147-L186):
        External calls:
        - [yieldBox.transfer(from,address(swapper),assetId,supplyShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L160)
        - [(None,borrowShare) = _borrow(from,address(swapper),borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L164)
                - [yieldBox.transfer(address(this),to,assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L79)
        - [(amountOut,collateralShare) = swapper.swap(swapData,minAmountOut,from,dexData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L176-L181)
        - [_addCollateral(from,from,false,0,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L185)
                - [yieldBox.transfer(from,address(this),_assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L192)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L154)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_addCollateral(from,from,false,0,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L185)
                - [userCollateralShare[to] += share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L26)
        [Market.userCollateralShare](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L59) can be used in cross function reentrancies:
        - [SGLLendingCommon._addCollateral(address,address,bool,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L16-L38)
        - [Market._computeMaxBorrowableAmount(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L385-L398)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [SGLLendingCommon._removeCollateral(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L41-L55)
        - [Market.computeLiquidatorReward(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L356-L365)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [Market.userCollateralShare](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L59)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L147-L186


 - [ ] ID-98
Reentrancy in [SGLLeverage.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137):
        External calls:
        - [_removeCollateral(from,address(swapper),share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L107)
                - [yieldBox.transfer(address(this),to,collateralId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L49)
        - [(amountOut,shareOut) = swapper.swap(swapData,minAmountOut,from,dexData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L117-L122)
        - [_repay(from,from,false,partOwed)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L131)
                - [yieldBox.transfer(from,address(this),_assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L192)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L103)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_repay(from,from,false,partOwed)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L131)
                - [_yieldBoxShares[to][_asset_sig] += share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L184)
        [SGLStorage._yieldBoxShares](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L49) can be used in cross function reentrancies:
        - [SGLCommon._addTokens(address,address,uint256,uint256,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L174-L194)
        - [SGLLendingCommon._removeCollateral(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L41-L55)
        - [_repay(from,from,false,partOwed)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L131)
                - [totalAsset.elastic = totalShare + uint128(share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L96)
        [SGLStorage.totalAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L44) can be used in cross function reentrancies:
        - [SGLCommon._accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L139-L163)
        - [SGLLendingCommon._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L58-L80)
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)
        - [SGLLendingCommon._repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98)
        - [SGLStorage.totalAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L44)
        - [SGLStorage.totalSupply()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L191-L193)
        - [_repay(from,from,false,partOwed)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L131)
                - [(totalBorrow,amount) = totalBorrow.sub(part,true)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L89)
        [Market.totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L51) can be used in cross function reentrancies:
        - [SGLCommon._accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L139-L163)
        - [SGLLendingCommon._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L58-L80)
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [SGLLendingCommon._repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [SGLLeverage.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137)
        - [Market.totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L51)
        - [_repay(from,from,false,partOwed)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L131)
                - [userBorrowPart[to] -= part](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L91)
        [Market.userBorrowPart](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L57) can be used in cross function reentrancies:
        - [SGLLendingCommon._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L58-L80)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [SGLLendingCommon._repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98)
        - [Market.computeLiquidatorReward(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L356-L365)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [SGLLeverage.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137)
        - [Market.userBorrowPart](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L57)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137


 - [ ] ID-99
Reentrancy in [SGLLiquidation._extractLiquidationFees(uint256,uint256,address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L270-L292):
        External calls:
        - [yieldBox.transfer(address(this),penrose.feeTo(),assetId,feeShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L281)
        - [yieldBox.transfer(address(this),msg.sender,assetId,callerShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L282)
        State variables written after the call(s):
        - [totalAsset.elastic += uint128(returnedShare - feeShare - callerShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L284)
        [SGLStorage.totalAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L44) can be used in cross function reentrancies:
        - [SGLCommon._accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L139-L163)
        - [SGLLiquidation._extractLiquidationFees(uint256,uint256,address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L270-L292)
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)
        - [SGLLiquidation._orderBookLiquidation(address[],uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L97-L202)
        - [SGLStorage.totalAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L44)
        - [SGLStorage.totalSupply()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L191-L193)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L270-L292


 - [ ] ID-100
Reentrancy in [BigBang.buyCollateral(address,uint256,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L336-L375):
        External calls:
        - [yieldBox.transfer(from,address(swapper),assetId,supplyShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L349)
        - [(None,borrowShare) = _borrow(from,address(swapper),borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L353)
                - [IUSDOBase(address(asset)).mint(address(this),amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L758)
                - [asset.approve(address(yieldBox),amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L761)
                - [yieldBox.depositAsset(assetId,address(this),to,amount,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L762)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L343)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [(None,borrowShare) = _borrow(from,address(swapper),borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L353)
                - [(totalBorrow,part) = totalBorrow.add(amount + feeAmount,true)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L749)
        [Market.totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L51) can be used in cross function reentrancies:
        - [BigBang._accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L512-L541)
        - [BigBang._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L742-L767)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [BigBang._repay(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L721-L739)
        - [BigBang._updateBorrowAndCollateralShare(address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L769-L824)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [BigBang.getDebtRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L180-L201)
        - [BigBang.getTotalDebt()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L175-L177)
        - [BigBang.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424)
        - [Market.totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L51)
        - [(None,borrowShare) = _borrow(from,address(swapper),borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L353)
                - [userBorrowPart[from] += part](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L755)
        [Market.userBorrowPart](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L57) can be used in cross function reentrancies:
        - [BigBang._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L742-L767)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [BigBang._liquidateUser(address,uint256,ISwapper,uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L560-L637)
        - [BigBang._repay(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L721-L739)
        - [BigBang._updateBorrowAndCollateralShare(address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L769-L824)
        - [Market.computeLiquidatorReward(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L356-L365)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [BigBang.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424)
        - [Market.userBorrowPart](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L57)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L336-L375


 - [ ] ID-101
Reentrancy in [USDO.flashLoan(IERC3156FlashBorrower,address,uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L81-L104):
        External calls:
        - [require(bool,string)(receiver.onFlashLoan(msg.sender,token,amount,fee,data) == FLASH_MINT_CALLBACK_SUCCESS,USDO: failed)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L93-L97)
        State variables written after the call(s):
        - [_burn(address(receiver),amount + fee)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L102)
                - [_balances[account] = accountBalance - amount](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L293)
        [ERC20._balances](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L36) can be used in cross function reentrancies:
        - [ERC20._burn(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L285-L301)
        - [ERC20._mint(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L259-L272)
        - [ERC20._transfer(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L226-L248)
        - [ERC20.balanceOf(address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L101-L103)
        - [_burn(address(receiver),amount + fee)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L102)
                - [_totalSupply -= amount](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L295)
        [ERC20._totalSupply](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L40) can be used in cross function reentrancies:
        - [ERC20._burn(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L285-L301)
        - [ERC20._mint(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L259-L272)
        - [ERC20.totalSupply()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L94-L96)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L81-L104


 - [ ] ID-102
Reentrancy in [SGLLeverage.multiHopBuyCollateral(address,uint256,uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageExternalContractsData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L21-L56):
        External calls:
        - [_addCollateral(from,from,false,0,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L41)
                - [yieldBox.transfer(from,address(this),_assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L192)
        - [(borrowShare) = _borrow(from,from,borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L44)
                - [yieldBox.transfer(address(this),to,assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L79)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L28)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [(borrowShare) = _borrow(from,from,borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L44)
                - [totalAsset = _totalAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L77)
        [SGLStorage.totalAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L44) can be used in cross function reentrancies:
        - [SGLCommon._accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L139-L163)
        - [SGLLendingCommon._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L58-L80)
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)
        - [SGLLendingCommon._repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98)
        - [SGLStorage.totalAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L44)
        - [SGLStorage.totalSupply()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L191-L193)
        - [(borrowShare) = _borrow(from,from,borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L44)
                - [(totalBorrow,part) = totalBorrow.add(amount + feeAmount,true)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L65)
        [Market.totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L51) can be used in cross function reentrancies:
        - [SGLCommon._accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L139-L163)
        - [SGLLendingCommon._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L58-L80)
        - [SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [SGLLendingCommon._repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [SGLLeverage.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137)
        - [Market.totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L51)
        - [(borrowShare) = _borrow(from,from,borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L44)
                - [userBorrowPart[from] += part](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L70)
        [Market.userBorrowPart](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L57) can be used in cross function reentrancies:
        - [SGLLendingCommon._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L58-L80)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [SGLLendingCommon._repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98)
        - [Market.computeLiquidatorReward(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L356-L365)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [SGLLeverage.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137)
        - [Market.userBorrowPart](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L57)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L21-L56


 - [ ] ID-103
Reentrancy in [SGLLeverage.multiHopBuyCollateral(address,uint256,uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageExternalContractsData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L21-L56):
        External calls:
        - [_addCollateral(from,from,false,0,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L41)
                - [yieldBox.transfer(from,address(this),_assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L192)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L28)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_addCollateral(from,from,false,0,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L41)
                - [userCollateralShare[to] += share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L26)
        [Market.userCollateralShare](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L59) can be used in cross function reentrancies:
        - [SGLLendingCommon._addCollateral(address,address,bool,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L16-L38)
        - [Market._computeMaxBorrowableAmount(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L385-L398)
        - [Market._isSolvent(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L402-L425)
        - [SGLLendingCommon._removeCollateral(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L41-L55)
        - [Market.computeLiquidatorReward(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L356-L365)
        - [Market.computeTVLInfo(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L305-L333)
        - [Market.userCollateralShare](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L59)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L21-L56


## unchecked-lowlevel
Impact: Medium
Confidence: Medium
 - [ ] ID-104
[BoringAddress.sendNative(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L15-L19) ignores return value by [(success) = to.call{value: amount}()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L17)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L15-L19


 - [ ] ID-105
[Address.sendValue(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L60-L65) ignores return value by [(success) = recipient.call{value: amount}()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L63)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L60-L65


## uninitialized-local
Impact: Medium
Confidence: Medium
 - [ ] ID-106
[SGLLiquidation._orderBookLiquidation(address[],uint256,bytes).allBorrowAmount](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L103) is a local variable never initialized

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L103


 - [ ] ID-107
[SGLLiquidation._orderBookLiquidation(address[],uint256,bytes).allCollateralShare](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L102) is a local variable never initialized

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L102


 - [ ] ID-108
[SGLLiquidation._orderBookLiquidation(address[],uint256,bytes).allBorrowPart](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L104) is a local variable never initialized

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L104


 - [ ] ID-109
[USDOLeverageModule.leverageUpInternal(uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageExternalContractsData,IUSDOBase.ILeverageLZData,address).approvals](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L225) is a local variable never initialized

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L225


 - [ ] ID-110
[BaseUSDO._extractModule(BaseUSDO.Module).module](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L345) is a local variable never initialized

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L345


 - [ ] ID-111
[Penrose.registerSingularityMasterContract(address,IPenrose.ContractType).mc](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L326) is a local variable never initialized

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L326


 - [ ] ID-112
[Penrose.registerBigBangMasterContract(address,IPenrose.ContractType).mc](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L348) is a local variable never initialized

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L348


 - [ ] ID-113
[YieldBoxURIBuilder.uri(Asset,NativeToken,uint256,address).details](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxURIBuilder.sol#L85) is a local variable never initialized

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxURIBuilder.sol#L85


 - [ ] ID-114
[Singularity._extractModule(Singularity.Module).module](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L601) is a local variable never initialized

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L601


## unused-return
Impact: Medium
Confidence: Medium
 - [ ] ID-115
[SGLLiquidation.liquidate(address[],uint256[],ISwapper,bytes,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L29-L65) ignores return value by [(bidAvail,bidAmount) = liquidationQueue.getNextAvailBidPool()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L41-L42)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L29-L65


 - [ ] ID-116
[SGLLiquidation._orderBookLiquidation(address[],uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L97-L202) ignores return value by [liquidationQueue.executeBids(yieldBox.toAmount(collateralId,allCollateralShare,true),swapData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L174-L177)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L97-L202


 - [ ] ID-117
[BigBang._liquidateUser(address,uint256,ISwapper,uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L560-L637) ignores return value by [swapper.swap(swapData,minAssetMount,address(this),)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L618)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L560-L637


 - [ ] ID-118
[OFTCoreV2._estimateSendFee(uint16,bytes32,uint256,bool,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L70-L74) ignores return value by [lzEndpoint.estimateFees(_dstChainId,address(this),payload,_useZro,_adapterParams)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L73)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L70-L74


 - [ ] ID-119
[SGLLeverage.multiHopBuyCollateral(address,uint256,uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageExternalContractsData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L21-L56) ignores return value by [yieldBox.withdraw(assetId,from,address(this),0,borrowShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L47)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L21-L56


 - [ ] ID-120
[BigBang.refreshPenroseFees(address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L442-L462) ignores return value by [asset.approve(address(yieldBox),totalFees)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L450)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L442-L462


 - [ ] ID-121
[BigBang._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L742-L767) ignores return value by [asset.approve(address(yieldBox),amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L761)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L742-L767


 - [ ] ID-122
[USDOLeverageModule.leverageUpInternal(uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageExternalContractsData,IUSDOBase.ILeverageLZData,address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L190-L252) ignores return value by [(amountOut) = ISwapper(externalData.swapper).swap(_swapperData,swapData.amountOutMin,address(this),swapData.data)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L209-L214)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L190-L252


 - [ ] ID-123
[BigBang.refreshPenroseFees(address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L442-L462) ignores return value by [yieldBox.depositAsset(assetId,address(this),msg.sender,totalFees,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L452-L458)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L442-L462


 - [ ] ID-124
[Penrose._depositFeesToYieldBox(IMarket,ISwapper,IPenrose.SwapData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L500-L540) ignores return value by [(amount,None) = swapper.swap(swapData,dexData.minAssetAmount,feeTo,)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L529-L534)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L500-L540


 - [ ] ID-125
[USDOLeverageModule.leverageUpInternal(uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageExternalContractsData,IUSDOBase.ILeverageLZData,address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L190-L252) ignores return value by [IERC20(swapData.tokenOut).approve(externalData.tOft,amountOut)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L217)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L190-L252


 - [ ] ID-126
[BigBang._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L742-L767) ignores return value by [yieldBox.depositAsset(assetId,address(this),to,amount,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L762)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L742-L767


 - [ ] ID-127
[SGLLeverage.multiHopSellCollateral(address,uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageExternalContractsData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L58-L88) ignores return value by [(amountOut) = yieldBox.withdraw(collateralId,address(this),address(this),0,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L72-L78)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L58-L88


 - [ ] ID-128
[OFTCoreV2._estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L76-L80) ignores return value by [lzEndpoint.estimateFees(_dstChainId,address(this),payload,_useZro,_adapterParams)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L79)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L76-L80


 - [ ] ID-129
[BigBang._repay(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L721-L739) ignores return value by [yieldBox.withdraw(assetId,from,address(this),amount,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L732)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L721-L739


 - [ ] ID-130
[SGLLiquidation._liquidateUser(address,uint256,ISwapper,uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L294-L368) ignores return value by [swapper.swap(swapData,minAssetAmount,address(this),)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L350)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L294-L368


## write-after-write
Impact: Medium
Confidence: High
 - [ ] ID-131
[BaseUSDO._executeModule(BaseUSDO.Module,bytes,bool).success](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L365) is written in both
        [success = true](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L366)
        [(success,returnData) = module.delegatecall(_data)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L369)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L365


## shadowing-local
Impact: Low
Confidence: High
 - [ ] ID-132
[USDO.flashLoan(IERC3156FlashBorrower,address,uint256,bytes).token](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L83) shadows:
        - [OFTV2.token()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L26-L28) (function)
        - [BaseOFTV2.token()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L42) (function)
        - [ICommonOFT.token()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/ICommonOFT.sol#L38) (function)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L83


 - [ ] ID-133
[ERC20Permit.constructor(string).name](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L44) shadows:
        - [ERC20.name()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L62-L64) (function)
        - [IERC20Metadata.name()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L17) (function)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L44


 - [ ] ID-134
[OFTV2.constructor(string,string,uint8,address).decimals](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L14) shadows:
        - [ERC20.decimals()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L87-L89) (function)
        - [IERC20Metadata.decimals()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L27) (function)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L14


 - [ ] ID-135
[IYieldBox.owner(uint256).owner](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L29) shadows:
        - [IYieldBox.owner(uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L29) (function)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L29


 - [ ] ID-136
[IYieldBox.wrappedNative().wrappedNative](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L8) shadows:
        - [IYieldBox.wrappedNative()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L8) (function)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L8


 - [ ] ID-137
[OFTV2.constructor(string,string,uint8,address)._symbol](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L13) shadows:
        - [ERC20._symbol](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L43) (state variable)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L13


 - [ ] ID-138
[USDO.flashFee(address,uint256).token](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L65) shadows:
        - [OFTV2.token()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L26-L28) (function)
        - [BaseOFTV2.token()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L42) (function)
        - [ICommonOFT.token()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/ICommonOFT.sol#L38) (function)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L65


 - [ ] ID-139
[BaseUSDO.constructor(address,IYieldBoxBase,address,address,address,address)._owner](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L70) shadows:
        - [Ownable._owner](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/access/Ownable.sol#L21) (state variable)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L70


 - [ ] ID-140
[NativeTokenFactory.createToken(string,string,uint8,string).uri](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/NativeTokenFactory.sol#L90) shadows:
        - [ERC1155.uri(uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC1155.sol#L123-L125) (function)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/NativeTokenFactory.sol#L90


 - [ ] ID-141
[OFTV2.constructor(string,string,uint8,address)._name](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L13) shadows:
        - [ERC20._name](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L42) (state variable)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L13


 - [ ] ID-142
[USDO.constructor(address,IYieldBoxBase,address,address,address,address)._owner](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L38) shadows:
        - [Ownable._owner](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/access/Ownable.sol#L21) (state variable)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L38


 - [ ] ID-143
[IYieldBox.totalSupply(uint256).totalSupply](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L31) shadows:
        - [IYieldBox.totalSupply(uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L31) (function)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L31


## missing-zero-check
Impact: Low
Confidence: Medium
 - [ ] ID-144
[USDOLeverageModule.leverageUp(address,uint16,bytes,uint64,bytes).module](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L134) lacks a zero-check on :
                - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.leverageUpInternal.selector,amount,swapData,externalData,lzData,leverageFor))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L169-L178)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L134


 - [ ] ID-145
[USDOMarketModule.lend(address,uint16,bytes,uint64,bytes).module](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L135) lacks a zero-check on :
                - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.lendInternal.selector,to,lendParams,approvals,withdrawParams))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L168-L176)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L135


 - [ ] ID-146
[USDOMarketModule.lend(address,uint16,bytes,uint64,bytes).to](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L144) lacks a zero-check on :
                - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.lendInternal.selector,to,lendParams,approvals,withdrawParams))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L168-L176)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L144


 - [ ] ID-147
[BoringOwnable.transferOwnership(address,bool,bool).newOwner](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L27) lacks a zero-check on :
                - [pendingOwner = newOwner](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L41)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L27


 - [ ] ID-148
[USDOOptionsModule.exercise(address,uint16,bytes,uint64,bytes).module](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L139) lacks a zero-check on :
                - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.exerciseInternal.selector,optionsData.from,optionsData.oTAPTokenID,optionsData.paymentToken,optionsData.tapAmount,optionsData.target,tapSendData,approvals))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L174-L185)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L139


 - [ ] ID-149
[Penrose.constructor(YieldBox,IERC20,IERC20,address)._owner](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L90) lacks a zero-check on :
                - [owner = _owner](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L94)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L90


 - [ ] ID-150
[USDOLeverageModule.leverageUp(address,uint16,bytes,uint64,bytes).leverageFor](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L147) lacks a zero-check on :
                - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.leverageUpInternal.selector,amount,swapData,externalData,lzData,leverageFor))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L169-L178)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L147


 - [ ] ID-151
[Penrose.setFeeTo(address).feeTo_](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L455) lacks a zero-check on :
                - [feeTo = feeTo_](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L456)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L455


 - [ ] ID-152
[Penrose.setBigBangEthMarket(address)._market](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L263) lacks a zero-check on :
                - [bigBangEthMarket = _market](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L264)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L263


 - [ ] ID-153
[LzApp.setPrecrime(address)._precrime](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L118) lacks a zero-check on :
                - [precrime = _precrime](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L119)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L118


## calls-loop
Impact: Low
Confidence: Medium
 - [ ] ID-154
[Penrose.executeMarketFn(address[],bytes[],bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L424-L450) has external calls inside a loop: [(success[i],result[i]) = mc[i].call(data[i])](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L444)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L424-L450


 - [ ] ID-155
[BaseBoringBatchable.batch(bytes[],bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L38-L45) has external calls inside a loop: [(success,result) = address(this).delegatecall(calls[i])](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L40)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L38-L45


 - [ ] ID-156
[Singularity.execute(bytes[],bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L181-L195) has external calls inside a loop: [(success,result) = address(this).delegatecall(calls[i])](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L188-L190)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L181-L195


 - [ ] ID-157
[BigBang.execute(bytes[],bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L209-L223) has external calls inside a loop: [(success,result) = address(this).delegatecall(calls[i])](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L216-L218)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L209-L223


## reentrancy-benign
Impact: Low
Confidence: Medium
 - [ ] ID-158
Reentrancy in [BaseUSDO._executeOnDestination(BaseUSDO.Module,bytes,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L375-L397):
        External calls:
        - [(success,returnData) = _executeModule(_module,_data,true)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L383-L387)
                - [(success,returnData) = module.delegatecall(_data)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L369)
        State variables written after the call(s):
        - [_storeFailedMessage(_srcChainId,_srcAddress,_nonce,_payload,returnData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L389-L395)
                - [failedMessages[_srcChainId][_srcAddress][_nonce] = keccak256(bytes)(_payload)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L33)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L375-L397


 - [ ] ID-159
Reentrancy in [Penrose.registerBigBang(address,bytes,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L395-L409):
        External calls:
        - [_contract = deploy(mc,data,useCreate2)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L406)
                - [IMasterContract(cloneAddress).init{value: msg.value}(data)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L64)
        State variables written after the call(s):
        - [isMarketRegistered[_contract] = true](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L407)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L395-L409


 - [ ] ID-160
Reentrancy in [SGLLeverage.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137):
        External calls:
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L103)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_allowedBorrow(from,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L106)
                - [allowanceBorrow[from][msg.sender] -= share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/MarketERC20.sol#L89)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137


 - [ ] ID-161
Reentrancy in [SGLBorrow.repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L45-L56):
        External calls:
        - [updateExchangeRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L51)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L53)
                - [accrueInfo = _accrueInfo](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L160)
        - [_accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L53)
                - [totalAsset = _totalAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L162)
        - [_accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L53)
                - [totalBorrow = _totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L161)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L45-L56


 - [ ] ID-162
Reentrancy in [BigBang.borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L242-L255):
        External calls:
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L246)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_allowedBorrow(from,allowanceShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L253)
                - [allowanceBorrow[from][msg.sender] -= share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/MarketERC20.sol#L89)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L242-L255


 - [ ] ID-163
Reentrancy in [Penrose.registerSingularity(address,bytes,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L362-L376):
        External calls:
        - [_contract = deploy(mc,data,useCreate2)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L373)
                - [IMasterContract(cloneAddress).init{value: msg.value}(data)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L64)
        State variables written after the call(s):
        - [isMarketRegistered[_contract] = true](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L374)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L362-L376


 - [ ] ID-164
Reentrancy in [USDO.flashLoan(IERC3156FlashBorrower,address,uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L81-L104):
        External calls:
        - [require(bool,string)(receiver.onFlashLoan(msg.sender,token,amount,fee,data) == FLASH_MINT_CALLBACK_SUCCESS,USDO: failed)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L93-L97)
        State variables written after the call(s):
        - [_approve(address(receiver),address(this),_allowance - (amount + fee))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L101)
                - [_allowances[owner][spender] = amount](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L324)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L81-L104


 - [ ] ID-165
Reentrancy in [SGLLeverage.multiHopSellCollateral(address,uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageExternalContractsData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L58-L88):
        External calls:
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L64)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_allowedBorrow(from,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L70)
                - [allowanceBorrow[from][msg.sender] -= share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/MarketERC20.sol#L89)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L58-L88


 - [ ] ID-166
Reentrancy in [BigBang.buyCollateral(address,uint256,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L336-L375):
        External calls:
        - [yieldBox.transfer(from,address(swapper),assetId,supplyShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L349)
        - [(None,borrowShare) = _borrow(from,address(swapper),borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L353)
                - [IUSDOBase(address(asset)).mint(address(this),amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L758)
                - [asset.approve(address(yieldBox),amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L761)
                - [yieldBox.depositAsset(assetId,address(this),to,amount,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L762)
        - [(amountOut,collateralShare) = swapper.swap(swapData,minAmountOut,from,dexData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L365-L370)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L343)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_allowedBorrow(from,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L373)
                - [allowanceBorrow[from][msg.sender] -= share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/MarketERC20.sol#L89)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L336-L375


 - [ ] ID-167
Reentrancy in [Singularity.init(bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L62-L142):
        External calls:
        - [updateExchangeRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L119)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [EXCHANGE_RATE_PRECISION = _exchangeRatePrecision](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L131-L133)
        - [EXCHANGE_RATE_PRECISION = 1e18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L131-L133)
        - [borrowOpeningFee = 50](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L124)
        - [callerFee = 1000](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L122)
        - [collateralizationRate = 75000](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L129)
        - [fullUtilizationMinusMax = FULL_UTILIZATION - maximumTargetUtilization](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L141)
        - [liquidationBonusAmount = 1e4](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L137)
        - [liquidationMultiplier = 12000](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L127)
        - [lqCollateralizationRate = 25000](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L130)
        - [maxLiquidatorReward = 1e4](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L136)
        - [maximumTargetUtilization = 5e17](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L140)
        - [minLiquidatorReward = 1e3](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L135)
        - [minimumTargetUtilization = 3e17](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L139)
        - [protocolFee = 10000](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L123)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L62-L142


 - [ ] ID-168
Reentrancy in [SGLLeverage.buyCollateral(address,uint256,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L147-L186):
        External calls:
        - [yieldBox.transfer(from,address(swapper),assetId,supplyShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L160)
        - [(None,borrowShare) = _borrow(from,address(swapper),borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L164)
                - [yieldBox.transfer(address(this),to,assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L79)
        - [(amountOut,collateralShare) = swapper.swap(swapData,minAmountOut,from,dexData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L176-L181)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L154)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_allowedBorrow(from,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L184)
                - [allowanceBorrow[from][msg.sender] -= share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/MarketERC20.sol#L89)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L147-L186


 - [ ] ID-169
Reentrancy in [SGLLeverage.multiHopBuyCollateral(address,uint256,uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageExternalContractsData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L21-L56):
        External calls:
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L28)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_allowedBorrow(from,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L40)
                - [allowanceBorrow[from][msg.sender] -= share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/MarketERC20.sol#L89)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L21-L56


 - [ ] ID-170
Reentrancy in [USDOMarketModule.lendInternal(address,IUSDOBase.ILendOrRepayParams,ICommonData.IApproval[],ICommonData.IWithdrawParams)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L191-L241):
        External calls:
        - [_callApproval(approvals)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L198)
                - [IPermitBorrow(approvals[i].target).permitBorrow(approvals[i].owner,approvals[i].spender,approvals[i].value,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L246-L260)
                - [IPermitAll(approvals[i].target).permitAll(approvals[i].owner,approvals[i].spender,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L262-L275)
                - [IERC20Permit(approvals[i].target).permit(approvals[i].owner,approvals[i].spender,approvals[i].value,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L277-L291)
        State variables written after the call(s):
        - [approve(address(lendParams.marketHelper),lendParams.depositAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L202)
                - [_allowances[owner][spender] = amount](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L324)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L191-L241


 - [ ] ID-171
Reentrancy in [SGLLendingCommon._removeCollateral(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L41-L55):
        External calls:
        - [yieldBox.transfer(address(this),to,collateralId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L49)
        State variables written after the call(s):
        - [_yieldBoxShares[from][COLLATERAL_SIG] = 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L51)
        - [_yieldBoxShares[from][COLLATERAL_SIG] -= share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L53)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L41-L55


 - [ ] ID-172
Reentrancy in [BigBang.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424):
        External calls:
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L390)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_allowedBorrow(from,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L393)
                - [allowanceBorrow[from][msg.sender] -= share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/MarketERC20.sol#L89)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424


 - [ ] ID-173
Reentrancy in [SGLCollateral.removeCollateral(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCollateral.sol#L35-L41):
        External calls:
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCollateral.sol#L39)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [allowedBorrow(from,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCollateral.sol#L39)
                - [allowanceBorrow[from][msg.sender] -= share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/MarketERC20.sol#L89)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCollateral.sol#L35-L41


 - [ ] ID-174
Reentrancy in [BigBang.removeCollateral(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L296-L302):
        External calls:
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L300)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [allowedBorrow(from,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L300)
                - [allowanceBorrow[from][msg.sender] -= share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/MarketERC20.sol#L89)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L296-L302


 - [ ] ID-175
Reentrancy in [BigBang.liquidate(address[],uint256[],ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L309-L326):
        External calls:
        - [(_exchangeRate) = updateExchangeRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L316)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L317)
                - [accrueInfo = _accrueInfo](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L538)
        - [_accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L317)
                - [totalBorrow = _totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L537)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L309-L326


 - [ ] ID-176
Reentrancy in [BigBang.init(bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L101-L169):
        External calls:
        - [updateExchangeRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L146)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [EXCHANGE_RATE_PRECISION = _exchangeRatePrecision](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L152-L154)
        - [EXCHANGE_RATE_PRECISION = 1e18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L152-L154)
        - [_isEthMarket = collateralId == penrose.wethAssetId()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L156)
        - [borrowOpeningFee = 50](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L167)
        - [callerFee = 90000](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L148)
        - [collateralizationRate = 75000](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L150)
        - [debtRateAgainstEthMarket = _debtRateAgainstEth](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L158)
        - [debtStartPoint = _debtStartPoint](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L161)
        - [liquidationBonusAmount = 1e4](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L166)
        - [liquidationMultiplier = 12000](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L168)
        - [maxDebtRate = _debtRateMax](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L159)
        - [maxLiquidatorReward = 1e4](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L165)
        - [minDebtRate = _debtRateMin](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L160)
        - [minLiquidatorReward = 1e3](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L164)
        - [protocolFee = 10000](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L149)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L101-L169


 - [ ] ID-177
Reentrancy in [BigBang.repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L263-L274):
        External calls:
        - [updateExchangeRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L269)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L271)
                - [accrueInfo = _accrueInfo](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L538)
        - [accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L271)
                - [totalBorrow = _totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L537)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L263-L274


 - [ ] ID-178
Reentrancy in [SGLBorrow.borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L21-L36):
        External calls:
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L25)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_allowedBorrow(from,allowanceShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L33)
                - [allowanceBorrow[from][msg.sender] -= share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/MarketERC20.sol#L89)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L21-L36


 - [ ] ID-179
Reentrancy in [SGLLiquidation.liquidate(address[],uint256[],ISwapper,bytes,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L29-L65):
        External calls:
        - [(_exchangeRate) = updateExchangeRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L37)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [_accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L38)
                - [accrueInfo = _accrueInfo](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L160)
        - [_accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L38)
                - [totalAsset = _totalAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L162)
        - [_accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L38)
                - [totalBorrow = _totalBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L161)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L29-L65


 - [ ] ID-180
Reentrancy in [Singularity.removeAsset(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L219-L227):
        External calls:
        - [share = _removeAsset(from,to,fraction,true)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L225)
                - [yieldBox.transfer(address(this),to,assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L243)
        State variables written after the call(s):
        - [_allowedLend(from,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L226)
                - [allowance[from][msg.sender] -= share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/MarketERC20.sol#L80)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L219-L227


 - [ ] ID-181
Reentrancy in [SGLCommon._removeAsset(address,address,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L223-L251):
        External calls:
        - [yieldBox.transfer(address(this),to,assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L243)
        State variables written after the call(s):
        - [_yieldBoxShares[from][ASSET_SIG] = 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L246)
        - [_yieldBoxShares[from][ASSET_SIG] -= share](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L248)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L223-L251


 - [ ] ID-182
Reentrancy in [Market.updateExchangeRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L340-L351):
        External calls:
        - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        State variables written after the call(s):
        - [exchangeRate = rate](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L345)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L340-L351


## reentrancy-events
Impact: Low
Confidence: Medium
 - [ ] ID-183
Reentrancy in [BigBang.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424):
        External calls:
        - [_removeCollateral(from,address(swapper),share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L394)
                - [yieldBox.transfer(address(this),to,collateralId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L717)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L390)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogRemoveCollateral(from,to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L716)
                - [_removeCollateral(from,address(swapper),share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L394)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424


 - [ ] ID-184
Reentrancy in [SGLLiquidation._orderBookLiquidation(address[],uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L97-L202):
        External calls:
        - [yieldBox.transfer(address(this),address(liquidationQueue),collateralId,allCollateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L166-L171)
        - [liquidationQueue.executeBids(yieldBox.toAmount(collateralId,allCollateralShare,true),swapData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L174-L177)
        - [yieldBox.transfer(address(this),msg.sender,assetId,callerShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L193)
        Event emitted after the call(s):
        - [LogAddAsset(address(liquidationQueue),address(this),returnedShare - callerShare,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L196-L201)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L97-L202


 - [ ] ID-185
Reentrancy in [BigBang.removeCollateral(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L296-L302):
        External calls:
        - [_removeCollateral(from,to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L301)
                - [yieldBox.transfer(address(this),to,collateralId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L717)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L300)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogRemoveCollateral(from,to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L716)
                - [_removeCollateral(from,to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L301)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L296-L302


 - [ ] ID-186
Reentrancy in [USDOLeverageModule.initMultiHopBuy(address,uint256,uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageExternalContractsData,bytes,ICommonData.IApproval[])](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L27-L60):
        External calls:
        - [_lzSend(lzData.lzSrcChainId,lzPayload,address(lzData.refundAddress),lzData.zroPaymentAddress,airdropAdapterParams,msg.value)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L51-L58)
                - [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
        Event emitted after the call(s):
        - [SendToChain(lzData.lzSrcChainId,msg.sender,senderBytes,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L59)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L27-L60


 - [ ] ID-187
Reentrancy in [SGLCollateral.removeCollateral(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCollateral.sol#L35-L41):
        External calls:
        - [_removeCollateral(from,to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCollateral.sol#L40)
                - [yieldBox.transfer(address(this),to,collateralId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L49)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCollateral.sol#L39)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogRemoveCollateral(from,to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L48)
                - [_removeCollateral(from,to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCollateral.sol#L40)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCollateral.sol#L35-L41


 - [ ] ID-188
Reentrancy in [BigBang.liquidate(address[],uint256[],ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L309-L326):
        External calls:
        - [(_exchangeRate) = updateExchangeRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L316)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        - [_closedLiquidation(users,maxBorrowParts,swapper,_exchangeRate,collateralToAssetSwapData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L319-L325)
                - [yieldBox.transfer(address(this),penrose.feeTo(),assetId,feeShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L648)
                - [yieldBox.transfer(address(this),msg.sender,assetId,callerShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L649)
                - [yieldBox.transfer(address(this),address(swapper),collateralId,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L596-L601)
                - [swapper.swap(swapData,minAssetMount,address(this),)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L618)
        Event emitted after the call(s):
        - [Liquidated(msg.sender,_users,callerShare,feeShare,borrowAmount,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L629-L636)
                - [_closedLiquidation(users,maxBorrowParts,swapper,_exchangeRate,collateralToAssetSwapData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L319-L325)
        - [LogRemoveCollateral(user,address(swapper),collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L587)
                - [_closedLiquidation(users,maxBorrowParts,swapper,_exchangeRate,collateralToAssetSwapData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L319-L325)
        - [LogRepay(address(swapper),user,borrowAmount,borrowPart)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L588)
                - [_closedLiquidation(users,maxBorrowParts,swapper,_exchangeRate,collateralToAssetSwapData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L319-L325)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L309-L326


 - [ ] ID-189
Reentrancy in [SGLLeverage.multiHopBuyCollateral(address,uint256,uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageExternalContractsData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L21-L56):
        External calls:
        - [_addCollateral(from,from,false,0,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L41)
                - [yieldBox.transfer(from,address(this),_assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L192)
        - [(borrowShare) = _borrow(from,from,borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L44)
                - [yieldBox.transfer(address(this),to,assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L79)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L28)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogBorrow(from,to,amount,feeAmount,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L71)
                - [(borrowShare) = _borrow(from,from,borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L44)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L21-L56


 - [ ] ID-190
Reentrancy in [SGLCommon._addAsset(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L197-L219):
        External calls:
        - [_addTokens(from,to,assetId,share,totalAssetShare,skim)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L217)
                - [yieldBox.transfer(from,address(this),_assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L192)
        Event emitted after the call(s):
        - [LogAddAsset(address(yieldBox),to,share,fraction)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L218)
        - [LogAddAsset(from,to,share,fraction)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L218)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L197-L219


 - [ ] ID-191
Reentrancy in [OFTCoreV2._send(address,uint16,bytes32,uint256,address,address,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L94-L105):
        External calls:
        - [_lzSend(_dstChainId,lzPayload,_refundAddress,_zroPaymentAddress,_adapterParams,msg.value)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L102)
                - [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
        Event emitted after the call(s):
        - [SendToChain(_dstChainId,_from,_toAddress,amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L104)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L94-L105


 - [ ] ID-192
Reentrancy in [USDOOptionsModule.exercise(address,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L138-L204):
        External calls:
        - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.exerciseInternal.selector,optionsData.from,optionsData.oTAPTokenID,optionsData.paymentToken,optionsData.tapAmount,optionsData.target,tapSendData,approvals))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L174-L185)
        - [IERC20(address(this)).safeTransfer(optionsData.from,optionsData.paymentTokenAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L191-L194)
        Event emitted after the call(s):
        - [ReceiveFromChain(_srcChainId,optionsData.from,optionsData.paymentTokenAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L199-L203)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L138-L204


 - [ ] ID-193
Reentrancy in [Penrose.withdrawAllMarketFees(IMarket[],ISwapper[],IPenrose.SwapData[])](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L232-L248):
        External calls:
        - [_withdrawAllProtocolFees(swappers_,swapData_,markets_)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L245)
                - [feeShares = market.refreshPenroseFees(feeTo)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L508)
                - [yieldBox.transfer(address(this),address(swapper),assetId,feeShares)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L514-L519)
                - [(amount,None) = swapper.swap(swapData,dexData.minAssetAmount,feeTo,)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L529-L534)
                - [yieldBox.transfer(address(this),feeTo,assetId,feeShares)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L536)
        Event emitted after the call(s):
        - [ProtocolWithdrawal(markets_,block.timestamp)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L247)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L232-L248


 - [ ] ID-194
Reentrancy in [Market.updateExchangeRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L340-L351):
        External calls:
        - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogExchangeRate(rate)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L346)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L340-L351


 - [ ] ID-195
Reentrancy in [BigBang._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L742-L767):
        External calls:
        - [IUSDOBase(address(asset)).mint(address(this),amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L758)
        - [asset.approve(address(yieldBox),amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L761)
        - [yieldBox.depositAsset(assetId,address(this),to,amount,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L762)
        Event emitted after the call(s):
        - [LogBorrow(from,to,amount,feeAmount,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L766)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L742-L767


 - [ ] ID-196
Reentrancy in [USDOOptionsModule.triggerSendFrom(uint16,bytes,address,uint256,ISendFrom.LzCallParams,ICommonData.IApproval[])](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L24-L56):
        External calls:
        - [_lzSend(lzDstChainId,lzPayload,address(msg.sender),zroPaymentAddress,airdropAdapterParams,msg.value)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L41-L48)
                - [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
        Event emitted after the call(s):
        - [SendToChain(lzDstChainId,msg.sender,LzLib.addressToBytes32(msg.sender),0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L50-L55)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L24-L56


 - [ ] ID-197
Reentrancy in [USDOLeverageModule.sendForLeverage(uint256,address,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageExternalContractsData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L62-L91):
        External calls:
        - [_lzSend(lzData.lzDstChainId,lzPayload,address(lzData.refundAddress),lzData.zroPaymentAddress,lzData.dstAirdropAdapterParam,msg.value)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L82-L89)
                - [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
        Event emitted after the call(s):
        - [SendToChain(lzData.lzDstChainId,msg.sender,senderBytes,amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L90)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L62-L91


 - [ ] ID-198
Reentrancy in [YieldBox.depositNFTAsset(uint256,address,address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L168-L188):
        External calls:
        - [IERC721(asset.contractAddress).safeTransferFrom(from,address(asset.strategy),asset.tokenId)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L181)
        - [asset.strategy.deposited(1)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L183)
        Event emitted after the call(s):
        - [Deposited(msg.sender,from,to,assetId,1,1,1,1,true)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L185)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L168-L188


 - [ ] ID-199
Reentrancy in [USDOLeverageModule.leverageUp(address,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L133-L188):
        External calls:
        - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.leverageUpInternal.selector,amount,swapData,externalData,lzData,leverageFor))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L169-L178)
        - [IERC20(address(this)).safeTransfer(leverageFor,amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L182)
        Event emitted after the call(s):
        - [ReceiveFromChain(_srcChainId,leverageFor,amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L187)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L133-L188


 - [ ] ID-200
Reentrancy in [SGLBorrow.repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L45-L56):
        External calls:
        - [updateExchangeRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L51)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        - [amount = _repay(from,to,skim,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L55)
                - [yieldBox.transfer(from,address(this),_assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L192)
        Event emitted after the call(s):
        - [LogRepay(address(yieldBox),to,amount,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L97)
                - [amount = _repay(from,to,skim,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L55)
        - [LogRepay(from,to,amount,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L97)
                - [amount = _repay(from,to,skim,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L55)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L45-L56


 - [ ] ID-201
Reentrancy in [SGLLeverage.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137):
        External calls:
        - [_removeCollateral(from,address(swapper),share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L107)
                - [yieldBox.transfer(address(this),to,collateralId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L49)
        - [(amountOut,shareOut) = swapper.swap(swapData,minAmountOut,from,dexData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L117-L122)
        - [_repay(from,from,false,partOut)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L135)
                - [yieldBox.transfer(from,address(this),_assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L192)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L103)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogRepay(address(yieldBox),to,amount,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L97)
                - [_repay(from,from,false,partOut)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L135)
        - [LogRepay(from,to,amount,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L97)
                - [_repay(from,from,false,partOut)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L135)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137


 - [ ] ID-202
Reentrancy in [SGLBorrow.borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L21-L36):
        External calls:
        - [(part,share) = _borrow(from,to,amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L35)
                - [yieldBox.transfer(address(this),to,assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L79)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L25)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogBorrow(from,to,amount,feeAmount,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L71)
                - [(part,share) = _borrow(from,to,amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L35)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L21-L36


 - [ ] ID-203
Reentrancy in [BigBang.repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L263-L274):
        External calls:
        - [updateExchangeRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L269)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogAccrue(extraAmount,_accrueInfo.debtRate)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L540)
                - [accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L271)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L263-L274


 - [ ] ID-204
Reentrancy in [SGLLendingCommon._addCollateral(address,address,bool,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L16-L38):
        External calls:
        - [_addTokens(from,to,collateralId,share,oldTotalCollateralShare,skim)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L29-L36)
                - [yieldBox.transfer(from,address(this),_assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L192)
        Event emitted after the call(s):
        - [LogAddCollateral(address(yieldBox),to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L37)
        - [LogAddCollateral(from,to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L37)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L16-L38


 - [ ] ID-205
Reentrancy in [BigBang.buyCollateral(address,uint256,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L336-L375):
        External calls:
        - [yieldBox.transfer(from,address(swapper),assetId,supplyShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L349)
        - [(None,borrowShare) = _borrow(from,address(swapper),borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L353)
                - [IUSDOBase(address(asset)).mint(address(this),amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L758)
                - [asset.approve(address(yieldBox),amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L761)
                - [yieldBox.depositAsset(assetId,address(this),to,amount,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L762)
        - [(amountOut,collateralShare) = swapper.swap(swapData,minAmountOut,from,dexData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L365-L370)
        - [_addCollateral(from,from,false,0,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L374)
                - [yieldBox.transfer(from,address(this),_tokenId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L704)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L343)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogAddCollateral(address(yieldBox),to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L557)
                - [_addCollateral(from,from,false,0,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L374)
        - [LogAddCollateral(from,to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L557)
                - [_addCollateral(from,from,false,0,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L374)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L336-L375


 - [ ] ID-206
Reentrancy in [Penrose.setUsdoToken(address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L291-L311):
        External calls:
        - [usdoAssetId = uint96(yieldBox.registerAsset(TokenType.ERC20,_usdoToken,emptyStrategies[_usdoToken],0))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L302-L309)
        Event emitted after the call(s):
        - [UsdoTokenUpdated(_usdoToken,usdoAssetId)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L310)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L291-L311


 - [ ] ID-207
Reentrancy in [SGLLendingCommon._repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98):
        External calls:
        - [_addTokens(from,to,assetId,share,uint256(totalShare),skim)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L95)
                - [yieldBox.transfer(from,address(this),_assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L192)
        Event emitted after the call(s):
        - [LogRepay(address(yieldBox),to,amount,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L97)
        - [LogRepay(from,to,amount,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L97)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L83-L98


 - [ ] ID-208
Reentrancy in [Penrose.registerSingularity(address,bytes,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L362-L376):
        External calls:
        - [_contract = deploy(mc,data,useCreate2)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L373)
                - [IMasterContract(cloneAddress).init{value: msg.value}(data)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L64)
        Event emitted after the call(s):
        - [RegisterSingularity(_contract,mc)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L375)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L362-L376


 - [ ] ID-209
Reentrancy in [BaseUSDO._executeOnDestination(BaseUSDO.Module,bytes,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L375-L397):
        External calls:
        - [(success,returnData) = _executeModule(_module,_data,true)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L383-L387)
                - [(success,returnData) = module.delegatecall(_data)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L369)
        Event emitted after the call(s):
        - [MessageFailed(_srcChainId,_srcAddress,_nonce,_payload,_reason)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L34)
                - [_storeFailedMessage(_srcChainId,_srcAddress,_nonce,_payload,returnData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L389-L395)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L375-L397


 - [ ] ID-210
Reentrancy in [BigBang.buyCollateral(address,uint256,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L336-L375):
        External calls:
        - [yieldBox.transfer(from,address(swapper),assetId,supplyShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L349)
        - [(None,borrowShare) = _borrow(from,address(swapper),borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L353)
                - [IUSDOBase(address(asset)).mint(address(this),amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L758)
                - [asset.approve(address(yieldBox),amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L761)
                - [yieldBox.depositAsset(assetId,address(this),to,amount,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L762)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L343)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogBorrow(from,to,amount,feeAmount,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L766)
                - [(None,borrowShare) = _borrow(from,address(swapper),borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L353)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L336-L375


 - [ ] ID-211
Reentrancy in [SGLBorrow.repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L45-L56):
        External calls:
        - [updateExchangeRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L51)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogAccrue(0,0,startingInterestPerSecond,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L151)
                - [_accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L53)
        - [LogAccrue(extraAmount,feeFraction,_accrueInfo.interestPerSecond,utilization)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L153-L158)
                - [_accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L53)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L45-L56


 - [ ] ID-212
Reentrancy in [BigBang.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424):
        External calls:
        - [_removeCollateral(from,address(swapper),share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L394)
                - [yieldBox.transfer(address(this),to,collateralId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L717)
        - [(amountOut,shareOut) = swapper.swap(swapData,minAmountOut,from,dexData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L404-L409)
        - [_repay(from,from,partOut)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L422)
                - [yieldBox.withdraw(assetId,from,address(this),amount,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L732)
                - [IUSDOBase(address(asset)).burn(address(this),toBurn)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L735)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L390)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogRepay(from,to,amount,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L738)
                - [_repay(from,from,partOut)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L422)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424


 - [ ] ID-213
Reentrancy in [Penrose.registerBigBang(address,bytes,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L395-L409):
        External calls:
        - [_contract = deploy(mc,data,useCreate2)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L406)
                - [IMasterContract(cloneAddress).init{value: msg.value}(data)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L64)
        Event emitted after the call(s):
        - [RegisterBigBang(_contract,mc)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L408)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L395-L409


 - [ ] ID-214
Reentrancy in [SGLLiquidation._liquidateUser(address,uint256,ISwapper,uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L294-L368):
        External calls:
        - [yieldBox.transfer(address(this),address(swapper),collateralId,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L330-L335)
        - [swapper.swap(swapData,minAssetAmount,address(this),)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L350)
        - [(feeShare,callerShare) = _extractLiquidationFees(borrowShare,callerReward,address(swapper))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L352-L356)
                - [yieldBox.transfer(address(this),penrose.feeTo(),assetId,feeShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L281)
                - [yieldBox.transfer(address(this),msg.sender,assetId,callerShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L282)
        Event emitted after the call(s):
        - [Liquidated(msg.sender,_users,callerShare,feeShare,borrowAmount,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L360-L367)
        - [LogAddAsset(swapper,address(this),extraShare - feeShare - callerShare,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L286-L291)
                - [(feeShare,callerShare) = _extractLiquidationFees(borrowShare,callerReward,address(swapper))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L352-L356)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L294-L368


 - [ ] ID-215
Reentrancy in [SGLLeverage.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137):
        External calls:
        - [_removeCollateral(from,address(swapper),share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L107)
                - [yieldBox.transfer(address(this),to,collateralId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L49)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L103)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogRemoveCollateral(from,to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L48)
                - [_removeCollateral(from,address(swapper),share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L107)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137


 - [ ] ID-216
Reentrancy in [SGLLeverage.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137):
        External calls:
        - [_removeCollateral(from,address(swapper),share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L107)
                - [yieldBox.transfer(address(this),to,collateralId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L49)
        - [(amountOut,shareOut) = swapper.swap(swapData,minAmountOut,from,dexData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L117-L122)
        - [_repay(from,from,false,partOwed)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L131)
                - [yieldBox.transfer(from,address(this),_assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L192)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L103)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogRepay(address(yieldBox),to,amount,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L97)
                - [_repay(from,from,false,partOwed)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L131)
        - [LogRepay(from,to,amount,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L97)
                - [_repay(from,from,false,partOwed)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L131)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137


 - [ ] ID-217
Reentrancy in [SGLLeverage.buyCollateral(address,uint256,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L147-L186):
        External calls:
        - [yieldBox.transfer(from,address(swapper),assetId,supplyShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L160)
        - [(None,borrowShare) = _borrow(from,address(swapper),borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L164)
                - [yieldBox.transfer(address(this),to,assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L79)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L154)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogBorrow(from,to,amount,feeAmount,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L71)
                - [(None,borrowShare) = _borrow(from,address(swapper),borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L164)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L147-L186


 - [ ] ID-218
Reentrancy in [Singularity.setLiquidationQueueConfig(ILiquidationQueue,address,address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L576-L595):
        External calls:
        - [liquidationQueue.setBidExecutionSwapper(_bidExecutionSwapper)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L588)
        Event emitted after the call(s):
        - [UsdoSwapperUpdated(_usdoSwapper)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L592)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L576-L595


 - [ ] ID-219
Reentrancy in [USDO.flashLoan(IERC3156FlashBorrower,address,uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L81-L104):
        External calls:
        - [require(bool,string)(receiver.onFlashLoan(msg.sender,token,amount,fee,data) == FLASH_MINT_CALLBACK_SUCCESS,USDO: failed)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L93-L97)
        Event emitted after the call(s):
        - [Approval(owner,spender,amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L325)
                - [_approve(address(receiver),address(this),_allowance - (amount + fee))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L101)
        - [Transfer(account,address(0),amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L298)
                - [_burn(address(receiver),amount + fee)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L102)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L81-L104


 - [ ] ID-220
Reentrancy in [BigBang.repay(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L263-L274):
        External calls:
        - [updateExchangeRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L269)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        - [amount = _repay(from,to,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L273)
                - [yieldBox.withdraw(assetId,from,address(this),amount,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L732)
                - [IUSDOBase(address(asset)).burn(address(this),toBurn)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L735)
        Event emitted after the call(s):
        - [LogRepay(from,to,amount,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L738)
                - [amount = _repay(from,to,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L273)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L263-L274


 - [ ] ID-221
Reentrancy in [YieldBox.depositETHAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L196-L219):
        External calls:
        - [wrappedNative.deposit{value: amount}()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L211)
        - [wrappedNative.safeTransfer(address(asset.strategy),amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L213)
        - [asset.strategy.deposited(amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L214)
        External calls sending eth:
        - [wrappedNative.deposit{value: amount}()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L211)
        Event emitted after the call(s):
        - [Deposited(msg.sender,msg.sender,to,assetId,amount,share,amountOut,shareOut,false)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L216)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L196-L219


 - [ ] ID-222
Reentrancy in [SGLLeverage.multiHopBuyCollateral(address,uint256,uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageExternalContractsData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L21-L56):
        External calls:
        - [_addCollateral(from,from,false,0,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L41)
                - [yieldBox.transfer(from,address(this),_assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L192)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L28)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogAddCollateral(address(yieldBox),to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L37)
                - [_addCollateral(from,from,false,0,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L41)
        - [LogAddCollateral(from,to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L37)
                - [_addCollateral(from,from,false,0,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L41)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L21-L56


 - [ ] ID-223
Reentrancy in [BigBang.liquidate(address[],uint256[],ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L309-L326):
        External calls:
        - [(_exchangeRate) = updateExchangeRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L316)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogAccrue(extraAmount,_accrueInfo.debtRate)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L540)
                - [_accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L317)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L309-L326


 - [ ] ID-224
Reentrancy in [BigBang._addCollateral(address,address,bool,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L543-L558):
        External calls:
        - [_addTokens(from,collateralId,share,oldTotalCollateralShare,skim)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L556)
                - [yieldBox.transfer(from,address(this),_tokenId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L704)
        Event emitted after the call(s):
        - [LogAddCollateral(address(yieldBox),to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L557)
        - [LogAddCollateral(from,to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L557)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L543-L558


 - [ ] ID-225
Reentrancy in [BigBang._liquidateUser(address,uint256,ISwapper,uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L560-L637):
        External calls:
        - [yieldBox.transfer(address(this),address(swapper),collateralId,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L596-L601)
        - [swapper.swap(swapData,minAssetMount,address(this),)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L618)
        - [(feeShare,callerShare) = _extractLiquidationFees(returnedShare,borrowShare,callerReward)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L622-L626)
                - [yieldBox.transfer(address(this),penrose.feeTo(),assetId,feeShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L648)
                - [yieldBox.transfer(address(this),msg.sender,assetId,callerShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L649)
        Event emitted after the call(s):
        - [Liquidated(msg.sender,_users,callerShare,feeShare,borrowAmount,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L629-L636)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L560-L637


 - [ ] ID-226
Reentrancy in [SGLLiquidation.liquidate(address[],uint256[],ISwapper,bytes,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L29-L65):
        External calls:
        - [(_exchangeRate) = updateExchangeRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L37)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        - [_orderBookLiquidation(users,_exchangeRate,usdoToBorrowedSwapData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L49-L53)
                - [yieldBox.transfer(address(this),address(liquidationQueue),collateralId,allCollateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L166-L171)
                - [liquidationQueue.executeBids(yieldBox.toAmount(collateralId,allCollateralShare,true),swapData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L174-L177)
                - [yieldBox.transfer(address(this),msg.sender,assetId,callerShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L193)
        Event emitted after the call(s):
        - [Liquidated(msg.sender,users,callerShare,returnedShare - callerShare,allBorrowAmount,allCollateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L184-L191)
                - [_orderBookLiquidation(users,_exchangeRate,usdoToBorrowedSwapData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L49-L53)
        - [LogAddAsset(address(liquidationQueue),address(this),returnedShare - callerShare,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L196-L201)
                - [_orderBookLiquidation(users,_exchangeRate,usdoToBorrowedSwapData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L49-L53)
        - [LogRemoveCollateral(user,address(liquidationQueue),collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L134-L138)
                - [_orderBookLiquidation(users,_exchangeRate,usdoToBorrowedSwapData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L49-L53)
        - [LogRepay(address(liquidationQueue),user,borrowAmount,borrowPart)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L139-L144)
                - [_orderBookLiquidation(users,_exchangeRate,usdoToBorrowedSwapData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L49-L53)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L29-L65


 - [ ] ID-227
Reentrancy in [BigBang.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424):
        External calls:
        - [_removeCollateral(from,address(swapper),share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L394)
                - [yieldBox.transfer(address(this),to,collateralId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L717)
        - [(amountOut,shareOut) = swapper.swap(swapData,minAmountOut,from,dexData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L404-L409)
        - [_repay(from,from,partOwed)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L418)
                - [yieldBox.withdraw(assetId,from,address(this),amount,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L732)
                - [IUSDOBase(address(asset)).burn(address(this),toBurn)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L735)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L390)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogRepay(from,to,amount,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L738)
                - [_repay(from,from,partOwed)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L418)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424


 - [ ] ID-228
Reentrancy in [YieldBox.depositAsset(uint256,address,address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L118-L160):
        External calls:
        - [IERC20(asset.contractAddress).safeTransferFrom(from,address(asset.strategy),amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L144)
        - [IERC1155(asset.contractAddress).safeTransferFrom(from,address(asset.strategy),asset.tokenId,amount,)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L151)
        - [asset.strategy.deposited(amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L155)
        Event emitted after the call(s):
        - [Deposited(msg.sender,from,to,assetId,amount,share,amountOut,shareOut,false)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L157)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L118-L160


 - [ ] ID-229
Reentrancy in [USDOMarketModule.lendInternal(address,IUSDOBase.ILendOrRepayParams,ICommonData.IApproval[],ICommonData.IWithdrawParams)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L191-L241):
        External calls:
        - [_callApproval(approvals)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L198)
                - [IPermitBorrow(approvals[i].target).permitBorrow(approvals[i].owner,approvals[i].spender,approvals[i].value,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L246-L260)
                - [IPermitAll(approvals[i].target).permitAll(approvals[i].owner,approvals[i].spender,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L262-L275)
                - [IERC20Permit(approvals[i].target).permit(approvals[i].owner,approvals[i].spender,approvals[i].value,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L277-L291)
        Event emitted after the call(s):
        - [Approval(owner,spender,amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L325)
                - [approve(address(lendParams.marketHelper),lendParams.depositAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L202)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L191-L241


 - [ ] ID-230
Reentrancy in [SGLLiquidation.liquidate(address[],uint256[],ISwapper,bytes,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L29-L65):
        External calls:
        - [(_exchangeRate) = updateExchangeRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L37)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogAccrue(0,0,startingInterestPerSecond,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L151)
                - [_accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L38)
        - [LogAccrue(extraAmount,feeFraction,_accrueInfo.interestPerSecond,utilization)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L153-L158)
                - [_accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L38)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L29-L65


 - [ ] ID-231
Reentrancy in [YieldBox._withdrawNFT(Asset,uint256,address,address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L251-L265):
        External calls:
        - [asset.strategy.withdraw(to,1)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L260)
        Event emitted after the call(s):
        - [Withdraw(msg.sender,from,to,assetId,1,1,1,1)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L262)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L251-L265


 - [ ] ID-232
Reentrancy in [USDOOptionsModule.sendFromDestination(bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L103-L136):
        External calls:
        - [_callApproval(approvals)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L124)
                - [IPermitBorrow(approvals[i].target).permitBorrow(approvals[i].owner,approvals[i].spender,approvals[i].value,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L247-L261)
                - [IPermitAll(approvals[i].target).permitAll(approvals[i].owner,approvals[i].spender,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L263-L276)
                - [IERC20Permit(approvals[i].target).permit(approvals[i].owner,approvals[i].spender,approvals[i].value,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L278-L292)
        - [ISendFrom(address(this)).sendFrom{value: address(this).balance}(from,lzDstChainId,LzLib.addressToBytes32(from),amount,callParams)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L127-L133)
        External calls sending eth:
        - [ISendFrom(address(this)).sendFrom{value: address(this).balance}(from,lzDstChainId,LzLib.addressToBytes32(from),amount,callParams)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L127-L133)
        Event emitted after the call(s):
        - [ReceiveFromChain(lzDstChainId,from,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L135)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L103-L136


 - [ ] ID-233
Reentrancy in [USDOMarketModule.sendAndLendOrRepay(address,address,uint16,address,IUSDOBase.ILendOrRepayParams,ICommonData.IApproval[],ICommonData.IWithdrawParams,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L60-L102):
        External calls:
        - [_lzSend(lzDstChainId,lzPayload,address(_from),zroPaymentAddress,adapterParams,msg.value)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L87-L94)
                - [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
        Event emitted after the call(s):
        - [SendToChain(lzDstChainId,_from,toAddress,lendParams.depositAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L96-L101)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L60-L102


 - [ ] ID-234
Reentrancy in [SGLLiquidation.liquidate(address[],uint256[],ISwapper,bytes,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L29-L65):
        External calls:
        - [(_exchangeRate) = updateExchangeRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L37)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        - [_closedLiquidation(users,maxBorrowParts,swapper,_exchangeRate,collateralToAssetSwapData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L58-L64)
                - [yieldBox.transfer(address(this),penrose.feeTo(),assetId,feeShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L281)
                - [yieldBox.transfer(address(this),msg.sender,assetId,callerShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L282)
                - [yieldBox.transfer(address(this),address(swapper),collateralId,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L330-L335)
                - [swapper.swap(swapData,minAssetAmount,address(this),)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L350)
        Event emitted after the call(s):
        - [Liquidated(msg.sender,_users,callerShare,feeShare,borrowAmount,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L360-L367)
                - [_closedLiquidation(users,maxBorrowParts,swapper,_exchangeRate,collateralToAssetSwapData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L58-L64)
        - [LogAddAsset(swapper,address(this),extraShare - feeShare - callerShare,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L286-L291)
                - [_closedLiquidation(users,maxBorrowParts,swapper,_exchangeRate,collateralToAssetSwapData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L58-L64)
        - [LogRemoveCollateral(user,address(swapper),collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L321)
                - [_closedLiquidation(users,maxBorrowParts,swapper,_exchangeRate,collateralToAssetSwapData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L58-L64)
        - [LogRepay(address(swapper),user,borrowAmount,borrowPart)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L322)
                - [_closedLiquidation(users,maxBorrowParts,swapper,_exchangeRate,collateralToAssetSwapData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L58-L64)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L29-L65


 - [ ] ID-235
Reentrancy in [USDOMarketModule.removeAsset(address,address,uint16,address,bytes,ICommonData.ICommonExternalContracts,IUSDOBase.IRemoveAndRepay,ICommonData.IApproval[])](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L30-L58):
        External calls:
        - [_lzSend(lzDstChainId,lzPayload,address(from),zroPaymentAddress,adapterParams,msg.value)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L48-L55)
                - [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
        Event emitted after the call(s):
        - [SendToChain(lzDstChainId,from,LzLib.addressToBytes32(to),0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L57)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L30-L58


 - [ ] ID-236
Reentrancy in [OFTCoreV2._sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,address,address,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L119-L131):
        External calls:
        - [_lzSend(_dstChainId,lzPayload,_refundAddress,_zroPaymentAddress,_adapterParams,msg.value)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L128)
                - [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
        Event emitted after the call(s):
        - [SendToChain(_dstChainId,_from,_toAddress,amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L130)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L119-L131


 - [ ] ID-237
Reentrancy in [Penrose._depositFeesToYieldBox(IMarket,ISwapper,IPenrose.SwapData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L500-L540):
        External calls:
        - [feeShares = market.refreshPenroseFees(feeTo)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L508)
        - [yieldBox.transfer(address(this),address(swapper),assetId,feeShares)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L514-L519)
        - [(amount,None) = swapper.swap(swapData,dexData.minAssetAmount,feeTo,)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L529-L534)
        - [yieldBox.transfer(address(this),feeTo,assetId,feeShares)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L536)
        Event emitted after the call(s):
        - [LogYieldBoxFeesDeposit(feeShares,amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L539)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L500-L540


 - [ ] ID-238
Reentrancy in [SGLLiquidation._extractLiquidationFees(uint256,uint256,address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L270-L292):
        External calls:
        - [yieldBox.transfer(address(this),penrose.feeTo(),assetId,feeShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L281)
        - [yieldBox.transfer(address(this),msg.sender,assetId,callerShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L282)
        Event emitted after the call(s):
        - [LogAddAsset(swapper,address(this),extraShare - feeShare - callerShare,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L286-L291)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L270-L292


 - [ ] ID-239
Reentrancy in [BoringFactory.deploy(address,bytes,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67):
        External calls:
        - [IMasterContract(cloneAddress).init{value: msg.value}(data)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L64)
        Event emitted after the call(s):
        - [LogDeploy(masterContract,data,cloneAddress)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L66)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67


 - [ ] ID-240
Reentrancy in [SGLLeverage.multiHopSellCollateral(address,uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageExternalContractsData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L58-L88):
        External calls:
        - [_removeCollateral(from,address(this),share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L71)
                - [yieldBox.transfer(address(this),to,collateralId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L49)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L64)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogRemoveCollateral(from,to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L48)
                - [_removeCollateral(from,address(this),share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L71)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L58-L88


 - [ ] ID-241
Reentrancy in [SGLLiquidation._orderBookLiquidation(address[],uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L97-L202):
        External calls:
        - [yieldBox.transfer(address(this),address(liquidationQueue),collateralId,allCollateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L166-L171)
        - [liquidationQueue.executeBids(yieldBox.toAmount(collateralId,allCollateralShare,true),swapData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L174-L177)
        Event emitted after the call(s):
        - [Liquidated(msg.sender,users,callerShare,returnedShare - callerShare,allBorrowAmount,allCollateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L184-L191)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L97-L202


 - [ ] ID-242
Reentrancy in [USDOOptionsModule.exerciseOption(ITapiocaOptionsBrokerCrossChain.IExerciseOptionsData,ITapiocaOptionsBrokerCrossChain.IExerciseLZData,ITapiocaOptionsBrokerCrossChain.IExerciseLZSendTapData,ICommonData.IApproval[])](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L58-L101):
        External calls:
        - [_lzSend(lzData.lzDstChainId,lzPayload,address(optionsData.from),lzData.zroPaymentAddress,adapterParams,msg.value)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L86-L93)
                - [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
        Event emitted after the call(s):
        - [SendToChain(lzData.lzDstChainId,optionsData.from,toAddress,optionsData.paymentTokenAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L95-L100)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L58-L101


 - [ ] ID-243
Reentrancy in [BigBang.borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L242-L255):
        External calls:
        - [(part,share) = _borrow(from,to,amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L254)
                - [IUSDOBase(address(asset)).mint(address(this),amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L758)
                - [asset.approve(address(yieldBox),amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L761)
                - [yieldBox.depositAsset(assetId,address(this),to,amount,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L762)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L246)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogBorrow(from,to,amount,feeAmount,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L766)
                - [(part,share) = _borrow(from,to,amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L254)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L242-L255


 - [ ] ID-244
Reentrancy in [YieldBox._withdrawFungible(Asset,uint256,address,address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L274-L300):
        External calls:
        - [asset.strategy.withdraw(to,amount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L295)
        Event emitted after the call(s):
        - [Withdraw(msg.sender,from,to,assetId,amount,share,amountOut,shareOut)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L297)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L274-L300


 - [ ] ID-245
Reentrancy in [USDOMarketModule.lend(address,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L134-L189):
        External calls:
        - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.lendInternal.selector,to,lendParams,approvals,withdrawParams))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L168-L176)
        - [IERC20(address(this)).safeTransfer(to,lendParams.depositAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L180-L183)
        Event emitted after the call(s):
        - [ReceiveFromChain(_srcChainId,to,lendParams.depositAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L188)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L134-L189


 - [ ] ID-246
Reentrancy in [SGLLeverage.buyCollateral(address,uint256,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L147-L186):
        External calls:
        - [yieldBox.transfer(from,address(swapper),assetId,supplyShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L160)
        - [(None,borrowShare) = _borrow(from,address(swapper),borrowAmount)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L164)
                - [yieldBox.transfer(address(this),to,assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L79)
        - [(amountOut,collateralShare) = swapper.swap(swapData,minAmountOut,from,dexData)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L176-L181)
        - [_addCollateral(from,from,false,0,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L185)
                - [yieldBox.transfer(from,address(this),_assetId,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L192)
        - [solvent(from)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L154)
                - [(updated,rate) = oracle.get()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L341)
        Event emitted after the call(s):
        - [LogAddCollateral(address(yieldBox),to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L37)
                - [_addCollateral(from,from,false,0,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L185)
        - [LogAddCollateral(from,to,share)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L37)
                - [_addCollateral(from,from,false,0,collateralShare)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L185)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L147-L186


 - [ ] ID-247
Reentrancy in [BigBang._repay(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L721-L739):
        External calls:
        - [yieldBox.withdraw(assetId,from,address(this),amount,0)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L732)
        - [IUSDOBase(address(asset)).burn(address(this),toBurn)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L735)
        Event emitted after the call(s):
        - [LogRepay(from,to,amount,part)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L738)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L721-L739


## timestamp
Impact: Low
Confidence: Medium
 - [ ] ID-248
[ERC20Permit.permit(address,address,uint256,uint256,uint8,bytes32,bytes32)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L49-L68) uses timestamp for comparisons
        Dangerous comparisons:
        - [require(bool,string)(block.timestamp <= deadline,ERC20Permit: expired deadline)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L58)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L49-L68


 - [ ] ID-249
[YieldBoxPermit.permitAll(address,address,uint256,uint8,bytes32,bytes32)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L72-L90) uses timestamp for comparisons
        Dangerous comparisons:
        - [require(bool,string)(block.timestamp <= deadline,YieldBoxPermit: expired deadline)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L80)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L72-L90


 - [ ] ID-250
[BigBang._repay(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L721-L739) uses timestamp for comparisons
        Dangerous comparisons:
        - [toBurn > 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L734)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L721-L739


 - [ ] ID-251
[BigBang._accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L512-L541) uses timestamp for comparisons
        Dangerous comparisons:
        - [elapsedTime == 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L516)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L512-L541


 - [ ] ID-252
[MarketERC20._permit(bool,address,address,uint256,uint256,uint8,bytes32,bytes32)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/MarketERC20.sol#L251-L284) uses timestamp for comparisons
        Dangerous comparisons:
        - [require(bool,string)(block.timestamp <= deadline,ERC20Permit: expired deadline)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/MarketERC20.sol#L261)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/MarketERC20.sol#L251-L284


 - [ ] ID-253
[SGLLiquidation._computeAssetAmountToSolvency(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L70-L95) uses timestamp for comparisons
        Dangerous comparisons:
        - [borrowPart == 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L76)
        - [borrowPart >= collateralAmountInAsset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L91-L94)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L70-L95


 - [ ] ID-254
[YieldBoxPermit.permit(address,address,uint256,uint256,uint8,bytes32,bytes32)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L42-L61) uses timestamp for comparisons
        Dangerous comparisons:
        - [require(bool,string)(block.timestamp <= deadline,YieldBoxPermit: expired deadline)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L51)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L42-L61


 - [ ] ID-255
[BigBang._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L742-L767) uses timestamp for comparisons
        Dangerous comparisons:
        - [require(bool,string)(totalBorrowCap == 0 || totalBorrow.elastic <= totalBorrowCap,BigBang: borrow cap reached)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L750-L753)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L742-L767


 - [ ] ID-256
[BigBang._updateBorrowAndCollateralShare(address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L769-L824) uses timestamp for comparisons
        Dangerous comparisons:
        - [borrowPart > userBorrowPart[user]](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L801)
        - [maxBorrowPart > availableBorrowPart](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L797-L799)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L769-L824


 - [ ] ID-257
[SGLLiquidation._orderBookLiquidation(address[],uint256,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L97-L202) uses timestamp for comparisons
        Dangerous comparisons:
        - [borrowAmount == 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L115)
        - [require(bool,string)(allBorrowAmount != 0,SGL: solvent)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L152)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L97-L202


 - [ ] ID-258
[BigBang.getDebtRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L180-L201) uses timestamp for comparisons
        Dangerous comparisons:
        - [totalBorrow.elastic == 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L182)
        - [_currentDebt >= _maxDebtPoint](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L190)
        - [debt > maxDebtRate](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L198)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L180-L201


 - [ ] ID-259
[SGLCommon._addTokens(address,address,uint256,uint256,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L174-L194) uses timestamp for comparisons
        Dangerous comparisons:
        - [require(bool,string)(share <= yieldBox.balanceOf(address(this),_assetId) - total,SGL: too much)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L187-L190)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L174-L194


 - [ ] ID-260
[SGLLendingCommon._borrow(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L58-L80) uses timestamp for comparisons
        Dangerous comparisons:
        - [require(bool,string)(totalBorrowCap == 0 || totalBorrow.base <= totalBorrowCap,SGL: borrow cap reached)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L66-L69)
        - [require(bool,string)(_totalAsset.base >= 1000,SGL: min limit)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L75)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L58-L80


 - [ ] ID-261
[SGLLeverage.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137) uses timestamp for comparisons
        Dangerous comparisons:
        - [shareOwed <= shareOut](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L130)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L97-L137


 - [ ] ID-262
[SGLCommon._getInterestRate()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137) uses timestamp for comparisons
        Dangerous comparisons:
        - [elapsedTime == 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L68)
        - [_totalBorrow.base == 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L81)
        - [_accrueInfo.interestPerSecond != startingInterestPerSecond](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L83)
        - [utilization < minimumTargetUtilization](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L112)
        - [_accrueInfo.interestPerSecond < minimumInterestPerSecond](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L121)
        - [utilization > maximumTargetUtilization](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L124)
        - [newInterestPerSecond > maximumInterestPerSecond](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L132)
        - [fullAssetAmount == 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L61-L64)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L35-L137


 - [ ] ID-263
[SGLCommon._addAsset(address,address,bool,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L197-L219) uses timestamp for comparisons
        Dangerous comparisons:
        - [_totalAsset.base + uint128(fraction) < 1000](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L210)
        - [allShare == 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L207-L209)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L197-L219


 - [ ] ID-264
[BigBang.sellCollateral(address,uint256,uint256,ISwapper,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424) uses timestamp for comparisons
        Dangerous comparisons:
        - [shareOwed <= shareOut](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L417)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L384-L424


 - [ ] ID-265
[ERC20.permit(address,address,uint256,uint256,uint8,bytes32,bytes32)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/ERC20.sol#L102-L120) uses timestamp for comparisons
        Dangerous comparisons:
        - [require(bool,string)(block.timestamp < deadline,ERC20: Expired)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/ERC20.sol#L112)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/ERC20.sol#L102-L120


 - [ ] ID-266
[SGLCommon._removeAsset(address,address,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L223-L251) uses timestamp for comparisons
        Dangerous comparisons:
        - [totalAsset.base == 0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L229)
        - [require(bool,string)(_totalAsset.base >= 1000,SGL: min limit)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L240)
        - [share > _yieldBoxShares[from][ASSET_SIG]](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L245)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L223-L251


## assembly
Impact: Informational
Confidence: High
 - [ ] ID-267
[BytesLib.toUint8(bytes,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L308-L317) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L312-L314)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L308-L317


 - [ ] ID-268
[BytesLib.concat(bytes,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L13-L89) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L23-L86)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L13-L89


 - [ ] ID-269
[Base64.encode(bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L11-L69) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L23-L66)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L11-L69


 - [ ] ID-270
[BytesLib.toUint16(bytes,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L319-L328) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L323-L325)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L319-L328


 - [ ] ID-271
[ExcessivelySafeCall.excessivelySafeCall(address,uint256,uint16,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L23-L58) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L37-L56)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L23-L58


 - [ ] ID-272
[LzLib.getGasLimit(bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L47-L52) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L49-L51)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L47-L52


 - [ ] ID-273
[ECDSA.tryRecover(bytes32,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L55-L72) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L63-L67)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L55-L72


 - [ ] ID-274
[BytesLib.toUint96(bytes,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L352-L361) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L356-L358)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L352-L361


 - [ ] ID-275
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L66-L70)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L86-L93)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L100-L109)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-276
[BytesLib.equalStorage(bytes,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L439-L509) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L449-L506)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L439-L509


 - [ ] ID-277
[BytesLib.toUint32(bytes,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L330-L339) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L334-L336)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L330-L339


 - [ ] ID-278
[BytesLib.toBytes32(bytes,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L385-L394) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L389-L391)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L385-L394


 - [ ] ID-279
[Strings.toString(uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L18-L38) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L24-L26)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L30-L32)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L18-L38


 - [ ] ID-280
[LzApp._getGasLimit(bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L63-L68) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L65-L67)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L63-L68


 - [ ] ID-281
[BoringAddress.isContract(address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L7-L13) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L9-L11)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L7-L13


 - [ ] ID-282
[BytesLib.concatStorage(bytes,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L92-L225)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226


 - [ ] ID-283
[ExcessivelySafeCall.excessivelySafeStaticCall(address,uint256,uint16,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L75-L109) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L89-L107)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L75-L109


 - [ ] ID-284
[Market._getRevertMsg(bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L372-L383) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L378-L381)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L372-L383


 - [ ] ID-285
[BoringFactory.deploy(address,bytes,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L45-L51)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L53-L59)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67


 - [ ] ID-286
[BytesLib.toAddress(bytes,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297-L306) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L301-L303)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297-L306


 - [ ] ID-287
[Address._revert(bytes,string)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L231-L243) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L236-L239)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L231-L243


 - [ ] ID-288
[BytesLib.toUint128(bytes,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L363-L372) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L367-L369)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L363-L372


 - [ ] ID-289
[BytesLib.toUint256(bytes,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L374-L383) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L378-L380)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L374-L383


 - [ ] ID-290
[BytesLib.toUint64(bytes,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L341-L350) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L345-L347)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L341-L350


 - [ ] ID-291
[BaseBoringBatchable._getRevertMsg(bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L19-L29) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L24-L27)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L19-L29


 - [ ] ID-292
[BaseUSDOStorage._getRevertMsg(bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L87-L98) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L93-L96)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L87-L98


 - [ ] ID-293
[Penrose._getRevertMsg(bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L472-L483) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L478-L481)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L472-L483


 - [ ] ID-294
[BytesLib.slice(bytes,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L228-L295) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L242-L292)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L228-L295


 - [ ] ID-295
[BytesLib.equal(bytes,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L396-L437) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L399-L434)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L396-L437


 - [ ] ID-296
[ExcessivelySafeCall.swapSelector(bytes4,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L120-L135) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L126-L134)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L120-L135


 - [ ] ID-297
[LzLib.decodeAdapterParams(bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L55-L70) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L57-L60)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L65-L68)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L55-L70


## boolean-equal
Impact: Informational
Confidence: High
 - [ ] ID-298
[ERC1155._requireTransferAllowed(address,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC1155.sol#L78-L80) compares to a boolean constant:
        -[require(bool,string)(_from == msg.sender || _approved || isApprovedForAll[_from][msg.sender] == true,Transfer not allowed)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC1155.sol#L79)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC1155.sol#L78-L80


 - [ ] ID-299
[Penrose.registeredBigBangMasterContract(address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L181-L187) compares to a boolean constant:
        -[require(bool,string)(isBigBangMasterContractRegistered[mc] == true,Penrose: MC not registered)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L182-L185)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L181-L187


 - [ ] ID-300
[Penrose.registerSingularityMasterContract(address,IPenrose.ContractType)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L317-L333) compares to a boolean constant:
        -[require(bool,string)(isSingularityMasterContractRegistered[mcAddress] == false,Penrose: MC registered)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L321-L324)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L317-L333


 - [ ] ID-301
[Penrose.registeredSingularityMasterContract(address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L173-L179) compares to a boolean constant:
        -[require(bool,string)(isSingularityMasterContractRegistered[mc] == true,Penrose: MC not registered)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L174-L177)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L173-L179


 - [ ] ID-302
[Penrose.registerBigBangMasterContract(address,IPenrose.ContractType)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L339-L355) compares to a boolean constant:
        -[require(bool,string)(isBigBangMasterContractRegistered[mcAddress] == false,Penrose: MC registered)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L343-L346)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L339-L355


## pragma
Impact: Informational
Confidence: High
 - [ ] ID-303
Different versions of Solidity are used:
        - Version used: ['>=0.5.0', '>=0.6.0', '>=0.7.6', '>=0.8.0<0.9.0', '^0.8.0', '^0.8.1', '^0.8.18', '^0.8.9']
        - [>=0.5.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroEndpoint.sol#L3)
        - [>=0.5.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroReceiver.sol#L3)
        - [>=0.5.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroUserApplicationConfig.sol#L3)
        - [>=0.5.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/ICommonOFT.sol#L3)
        - [>=0.5.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/IOFTReceiverV2.sol#L3)
        - [>=0.5.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/IOFTV2.sol#L3)
        - [>=0.6.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L3)
        - [>=0.7.6](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L2)
        - [>=0.8.0<0.9.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L9)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L25)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L4)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IStrategy.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/ERC20WithoutStrategy.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L5)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/ERC20.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC1155.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC1155TokenReceiver.sol#L3)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC165.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC20.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721TokenReceiver.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IMasterContract.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/access/Ownable.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Context.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Counters.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/introspection/ERC165.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/introspection/IERC165.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L3)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L3)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L3)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L3)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L3)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L3)
        - [^0.8.1](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L4)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Test.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/MarketERC20.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCollateral.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLendingCommon.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/IBidder.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/IBigBang.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/ICommonData.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/IERC3156FlashBorrower.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/IERC3156FlashLender.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/ILiquidationQueue.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/IMagnetar.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/IMarket.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/IOracle.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/IPenrose.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/IPermitAll.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/IPermitBorrow.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/ISendFrom.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/ISingularity.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/ISwapper.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/ITapiocaOFT.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/ITapiocaOptionLiquidityProvision.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/ITapiocaOptionsBroker.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/IUSDO.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/IYieldBoxBase.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/AssetRegister.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/BoringMath.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC1155.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC1155TokenReceiver.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC721TokenReceiver.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/NativeTokenFactory.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L24)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L3)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxURIBuilder.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/enums/YieldBoxTokenType.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IStrategy.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IWrappedNative.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/ERC20WithoutStrategy.sol#L2)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroEndpoint.sol#L3


## cyclomatic-complexity
Impact: Informational
Confidence: High
 - [ ] ID-304
[USDOOptionsModule._callApproval(ICommonData.IApproval[])](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L244-L299) has a high cyclomatic complexity (13).

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L244-L299


 - [ ] ID-305
[Market.setMarketConfig(uint256,IOracle,bytes,address,uint256,uint256,uint256,uint256,uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L158-L240) has a high cyclomatic complexity (12).

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L158-L240


 - [ ] ID-306
[USDOMarketModule._callApproval(ICommonData.IApproval[])](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L243-L298) has a high cyclomatic complexity (13).

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L243-L298


 - [ ] ID-307
[USDOLeverageModule._callApproval(ICommonData.IApproval[])](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L254-L309) has a high cyclomatic complexity (13).

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L254-L309


## dead-code
Impact: Informational
Confidence: Medium
 - [ ] ID-308
[Singularity._executeViewModule(Singularity.Module,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L631-L642) is never used and should be removed

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L631-L642


 - [ ] ID-309
[SGLCommon._getAmountForBorrowPart(uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L254-L258) is never used and should be removed

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCommon.sol#L254-L258


 - [ ] ID-310
[SGLStorage._accrue()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L195) is never used and should be removed

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L195


## solc-version
Impact: Informational
Confidence: High
 - [ ] ID-311
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/ERC20WithoutStrategy.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/ERC20WithoutStrategy.sol#L2


 - [ ] ID-312
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L4


 - [ ] ID-313
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/AssetRegister.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/AssetRegister.sol#L2


 - [ ] ID-314
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L4


 - [ ] ID-315
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L2


 - [ ] ID-316
Pragma version[>=0.6.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L3


 - [ ] ID-317
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L4


 - [ ] ID-318
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC20.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC20.sol#L2


 - [ ] ID-319
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L4


 - [ ] ID-320
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol#L4


 - [ ] ID-321
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L3


 - [ ] ID-322
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L24) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L24


 - [ ] ID-323
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Context.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Context.sol#L4


 - [ ] ID-324
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L2


 - [ ] ID-325
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC1155TokenReceiver.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC1155TokenReceiver.sol#L3


 - [ ] ID-326
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L4


 - [ ] ID-327
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/NativeTokenFactory.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/NativeTokenFactory.sol#L2


 - [ ] ID-328
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L3


 - [ ] ID-329
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721TokenReceiver.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721TokenReceiver.sol#L2


 - [ ] ID-330
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC1155.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC1155.sol#L2


 - [ ] ID-331
Pragma version[>=0.7.6](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L2


 - [ ] ID-332
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L4


 - [ ] ID-333
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L2


 - [ ] ID-334
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L3


 - [ ] ID-335
Pragma version[>=0.5.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroUserApplicationConfig.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroUserApplicationConfig.sol#L3


 - [ ] ID-336
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/BoringMath.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/BoringMath.sol#L2


 - [ ] ID-337
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC165.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC165.sol#L2


 - [ ] ID-338
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L2


 - [ ] ID-339
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L4


 - [ ] ID-340
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IStrategy.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IStrategy.sol#L2


 - [ ] ID-341
Pragma version[^0.8.1](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L4


 - [ ] ID-342
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L3


 - [ ] ID-343
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L3


 - [ ] ID-344
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L3


 - [ ] ID-345
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721.sol#L2


 - [ ] ID-346
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Counters.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Counters.sol#L4


 - [ ] ID-347
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol#L4


 - [ ] ID-348
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC721TokenReceiver.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC721TokenReceiver.sol#L2


 - [ ] ID-349
Pragma version[>=0.8.0<0.9.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L9) is too complex

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L9


 - [ ] ID-350
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L2


 - [ ] ID-351
Pragma version[>=0.5.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroReceiver.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroReceiver.sol#L3


 - [ ] ID-352
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/ERC20.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/ERC20.sol#L2


 - [ ] ID-353
Pragma version[>=0.5.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroEndpoint.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroEndpoint.sol#L3


 - [ ] ID-354
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L2


 - [ ] ID-355
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/introspection/ERC165.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/introspection/ERC165.sol#L4


 - [ ] ID-356
Pragma version[>=0.5.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/ICommonOFT.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/ICommonOFT.sol#L3


 - [ ] ID-357
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L4


 - [ ] ID-358
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxURIBuilder.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxURIBuilder.sol#L2


 - [ ] ID-359
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L2


 - [ ] ID-360
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L2


 - [ ] ID-361
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L3


 - [ ] ID-362
Pragma version[>=0.5.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/IOFTReceiverV2.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/IOFTReceiverV2.sol#L3


 - [ ] ID-363
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IWrappedNative.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IWrappedNative.sol#L2


 - [ ] ID-364
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IMasterContract.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IMasterContract.sol#L2


 - [ ] ID-365
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/access/Ownable.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/access/Ownable.sol#L4


 - [ ] ID-366
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L5) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L5


 - [ ] ID-367
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC1155TokenReceiver.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC1155TokenReceiver.sol#L2


 - [ ] ID-368
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/introspection/IERC165.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/introspection/IERC165.sol#L4


 - [ ] ID-369
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC1155.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC1155.sol#L2


 - [ ] ID-370
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L2


 - [ ] ID-371
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/enums/YieldBoxTokenType.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/enums/YieldBoxTokenType.sol#L2


 - [ ] ID-372
Pragma version[>=0.5.0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/IOFTV2.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/IOFTV2.sol#L3


## low-level-calls
Impact: Informational
Confidence: High
 - [ ] ID-373
Low level call in [BoringERC20.safeName(IERC20)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L45-L48):
        - [(success,data) = address(token).staticcall(abi.encodeWithSelector(SIG_NAME))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L46)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L45-L48


 - [ ] ID-374
Low level call in [Address.functionCallWithValue(address,bytes,uint256,string)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L128-L137):
        - [(success,returndata) = target.call{value: value}(data)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L135)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L128-L137


 - [ ] ID-375
Low level call in [USDOOptionsModule.exercise(address,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L138-L204):
        - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.exerciseInternal.selector,optionsData.from,optionsData.oTAPTokenID,optionsData.paymentToken,optionsData.tapAmount,optionsData.target,tapSendData,approvals))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L174-L185)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L138-L204


 - [ ] ID-376
Low level call in [BaseBoringBatchable.batch(bytes[],bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L38-L45):
        - [(success,result) = address(this).delegatecall(calls[i])](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L40)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L38-L45


 - [ ] ID-377
Low level call in [Singularity._executeModule(Singularity.Module,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L618-L629):
        - [(success,returnData) = module.delegatecall(_data)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L625)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L618-L629


 - [ ] ID-378
Low level call in [USDOMarketModule.lend(address,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L134-L189):
        - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.lendInternal.selector,to,lendParams,approvals,withdrawParams))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L168-L176)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L134-L189


 - [ ] ID-379
Low level call in [BoringERC20.safeTransferFrom(IERC20,address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L97-L105):
        - [(success,data) = address(token).call(abi.encodeWithSelector(SIG_TRANSFER_FROM,from,to,amount))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L103)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L97-L105


 - [ ] ID-380
Low level call in [BoringERC20.safeSymbol(IERC20)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L37-L40):
        - [(success,data) = address(token).staticcall(abi.encodeWithSelector(SIG_SYMBOL))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L38)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L37-L40


 - [ ] ID-381
Low level call in [Singularity._executeViewModule(Singularity.Module,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L631-L642):
        - [(success,returnData) = module.staticcall(_data)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L638)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L631-L642


 - [ ] ID-382
Low level call in [BoringERC20.safeTotalSupply(IERC20)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L71-L75):
        - [(success,data) = address(token).staticcall(abi.encodeWithSelector(SIG_TOTALSUPPLY))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L72)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L71-L75


 - [ ] ID-383
Low level call in [BoringERC20.safeBalanceOf(IERC20,address)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L62-L66):
        - [(success,data) = address(token).staticcall(abi.encodeWithSelector(SIG_BALANCE_OF,to))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L63)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L62-L66


 - [ ] ID-384
Low level call in [BoringAddress.sendNative(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L15-L19):
        - [(success) = to.call{value: amount}()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L17)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L15-L19


 - [ ] ID-385
Low level call in [BoringERC20.safeDecimals(IERC20)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L53-L56):
        - [(success,data) = address(token).staticcall(abi.encodeWithSelector(SIG_DECIMALS))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L54)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L53-L56


 - [ ] ID-386
Low level call in [BigBang.execute(bytes[],bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L209-L223):
        - [(success,result) = address(this).delegatecall(calls[i])](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L216-L218)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L209-L223


 - [ ] ID-387
Low level call in [Address.sendValue(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L60-L65):
        - [(success) = recipient.call{value: amount}()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L63)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L60-L65


 - [ ] ID-388
Low level call in [BoringERC20.safeTransfer(IERC20,address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L82-L89):
        - [(success,data) = address(token).call(abi.encodeWithSelector(SIG_TRANSFER,to,amount))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L87)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L82-L89


 - [ ] ID-389
Low level call in [Penrose.executeMarketFn(address[],bytes[],bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L424-L450):
        - [(success[i],result[i]) = mc[i].call(data[i])](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L444)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L424-L450


 - [ ] ID-390
Low level call in [Address.functionStaticCall(address,bytes,string)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L155-L162):
        - [(success,returndata) = target.staticcall(data)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L160)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L155-L162


 - [ ] ID-391
Low level call in [USDOLeverageModule.leverageUp(address,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L133-L188):
        - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.leverageUpInternal.selector,amount,swapData,externalData,lzData,leverageFor))](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L169-L178)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L133-L188


 - [ ] ID-392
Low level call in [Address.functionDelegateCall(address,bytes,string)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L180-L187):
        - [(success,returndata) = target.delegatecall(data)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L185)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L180-L187


 - [ ] ID-393
Low level call in [Singularity.execute(bytes[],bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L181-L195):
        - [(success,result) = address(this).delegatecall(calls[i])](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L188-L190)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L181-L195


 - [ ] ID-394
Low level call in [BaseUSDO._executeModule(BaseUSDO.Module,bytes,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L361-L373):
        - [(success,returnData) = module.delegatecall(_data)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L369)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L361-L373


## missing-inheritance
Impact: Informational
Confidence: High
 - [ ] ID-395
[Singularity](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L37-L645) should inherit from [IMasterContract](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IMasterContract.sol#L4-L10)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L37-L645


 - [ ] ID-396
[USDO](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L24-L123) should inherit from [IUSDO](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/IUSDO.sol#L116)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L24-L123


 - [ ] ID-397
[USDOOptionsModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L16-L300) should inherit from [ITapiocaOptionsBrokerCrossChain](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/tapioca-periph/contracts/interfaces/ITapiocaOptionsBroker.sol#L7-L36)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L16-L300


 - [ ] ID-398
[BigBang](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L39-L825) should inherit from [IMasterContract](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IMasterContract.sol#L4-L10)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L39-L825


## naming-convention
Impact: Informational
Confidence: High
 - [ ] ID-399
Parameter [BaseOFTV2.estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)._dstGasForCall](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36


 - [ ] ID-400
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._srcChainId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-401
Parameter [USDOOptionsModule.exercise(address,uint16,bytes,uint64,bytes)._srcAddress](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L141) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L141


 - [ ] ID-402
Parameter [BaseOFTV2.sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,ICommonOFT.LzCallParams)._dstGasForCall](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21


 - [ ] ID-403
Parameter [BytesLib.equalStorage(bytes,bytes)._preBytes](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L440) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L440


 - [ ] ID-404
Parameter [LzApp.setConfig(uint16,uint16,uint256,bytes)._version](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84


 - [ ] ID-405
Parameter [USDOMarketModule.lend(address,uint16,bytes,uint64,bytes)._nonce](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L138) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L138


 - [ ] ID-406
Parameter [ExcessivelySafeCall.swapSelector(bytes4,bytes)._newSelector](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L120) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L120


 - [ ] ID-407
Parameter [Market.setMarketConfig(uint256,IOracle,bytes,address,uint256,uint256,uint256,uint256,uint256,uint256,uint256)._maxLiquidatorReward](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L167) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L167


 - [ ] ID-408
Parameter [BytesLib.concatStorage(bytes,bytes)._postBytes](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91


 - [ ] ID-409
Parameter [LzApp.setTrustedRemoteAddress(uint16,bytes)._remoteChainId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L107) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L107


 - [ ] ID-410
Parameter [ExcessivelySafeCall.swapSelector(bytes4,bytes)._buf](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L120) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L120


 - [ ] ID-411
Parameter [Market.computeLiquidatorReward(address,uint256)._exchangeRate](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L358) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L358


 - [ ] ID-412
Parameter [BytesLib.toUint128(bytes,uint256)._start](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L363) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L363


 - [ ] ID-413
Parameter [Singularity.setLiquidationQueueConfig(ILiquidationQueue,address,address)._usdoSwapper](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L579) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L579


 - [ ] ID-414
Parameter [BytesLib.equal(bytes,bytes)._preBytes](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L396) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L396


 - [ ] ID-415
Parameter [BytesLib.equalStorage(bytes,bytes)._postBytes](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L441) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L441


 - [ ] ID-416
Parameter [BaseOFTV2.sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,ICommonOFT.LzCallParams)._amount](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21


 - [ ] ID-417
Parameter [USDOMarketModule.remove(bytes)._payload](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L104) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L104


 - [ ] ID-418
Parameter [BytesLib.toUint64(bytes,uint256)._bytes](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L341) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L341


 - [ ] ID-419
Parameter [BytesLib.toBytes32(bytes,uint256)._bytes](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L385) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L385


 - [ ] ID-420
Parameter [LzApp.setTrustedRemote(uint16,bytes)._path](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L102) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L102


 - [ ] ID-421
Parameter [BaseOFTV2.sendFrom(address,uint16,bytes32,uint256,ICommonOFT.LzCallParams)._callParams](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17


 - [ ] ID-422
Parameter [LzApp.isTrustedRemote(uint16,bytes)._srcAddress](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L135) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L135


 - [ ] ID-423
Parameter [LzLib.buildAdapterParams(LzLib.AirdropParams,uint256)._airdropParams](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L21) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L21


 - [ ] ID-424
Parameter [Singularity.yieldBoxShares(address,uint256)._user](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L165) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L165


 - [ ] ID-425
Parameter [BytesLib.toAddress(bytes,uint256)._start](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297


 - [ ] ID-426
Parameter [USDOLeverageModule.leverageUp(address,uint16,bytes,uint64,bytes)._srcAddress](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L136) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L136


 - [ ] ID-427
Parameter [BaseUSDO.sendAndLendOrRepay(address,address,uint16,address,IUSDOBase.ILendOrRepayParams,ICommonData.IApproval[],ICommonData.IWithdrawParams,bytes)._to](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L315) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L315


 - [ ] ID-428
Parameter [LzApp.setConfig(uint16,uint16,uint256,bytes)._chainId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84


 - [ ] ID-429
Parameter [BytesLib.toUint8(bytes,uint256)._start](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L308) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L308


 - [ ] ID-430
Parameter [LzApp.forceResumeReceive(uint16,bytes)._srcAddress](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L96) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L96


 - [ ] ID-431
Parameter [NonblockingLzApp.retryMessage(uint16,bytes,uint64,bytes)._nonce](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46


 - [ ] ID-432
Parameter [BytesLib.toUint8(bytes,uint256)._bytes](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L308) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L308


 - [ ] ID-433
Parameter [ExcessivelySafeCall.excessivelySafeStaticCall(address,uint256,uint16,bytes)._calldata](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L79) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L79


 - [ ] ID-434
Parameter [BaseUSDO.setConservator(address)._conservator](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L105) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L105


 - [ ] ID-435
Parameter [BytesLib.toBytes32(bytes,uint256)._start](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L385) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L385


 - [ ] ID-436
Parameter [BaseOFTV2.estimateSendFee(uint16,bytes32,uint256,bool,bytes)._adapterParams](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32


 - [ ] ID-437
Parameter [USDOMarketModule.lend(address,uint16,bytes,uint64,bytes)._srcChainId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L136) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L136


 - [ ] ID-438
Parameter [ExcessivelySafeCall.excessivelySafeCall(address,uint256,uint16,bytes)._maxCopy](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L26) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L26


 - [ ] ID-439
Parameter [Penrose.setUsdoToken(address)._usdoToken](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L291) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L291


 - [ ] ID-440
Parameter [Market.setBorrowCap(uint256)._cap](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L151) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L151


 - [ ] ID-441
Parameter [BytesLib.toAddress(bytes,uint256)._bytes](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297


 - [ ] ID-442
Parameter [LzApp.setReceiveVersion(uint16)._version](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L92) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L92


 - [ ] ID-443
Parameter [BaseOFTV2.estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)._amount](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36


 - [ ] ID-444
Parameter [BaseOFTV2.sendFrom(address,uint16,bytes32,uint256,ICommonOFT.LzCallParams)._toAddress](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17


 - [ ] ID-445
Parameter [Singularity.setSingularityConfig(uint256,uint256,uint256,uint256,uint64,uint64,uint256)._maximumTargetUtilization](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L493) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L493


 - [ ] ID-446
Parameter [BaseOFTV2.sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,ICommonOFT.LzCallParams)._payload](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21


 - [ ] ID-447
Variable [Domain._DOMAIN_SEPARATOR](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L15) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L15


 - [ ] ID-448
Parameter [LzApp.lzReceive(uint16,bytes,uint64,bytes)._srcChainId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35


 - [ ] ID-449
Parameter [ExcessivelySafeCall.excessivelySafeCall(address,uint256,uint16,bytes)._calldata](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L27) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L27


 - [ ] ID-450
Parameter [USDOMarketModule.lend(address,uint16,bytes,uint64,bytes)._payload](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L139) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L139


 - [ ] ID-451
Parameter [BytesLib.toUint128(bytes,uint256)._bytes](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L363) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L363


 - [ ] ID-452
Parameter [LzLib.decodeAdapterParams(bytes)._adapterParams](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L55) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L55


 - [ ] ID-453
Parameter [Penrose.setConservator(address)._conservator](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L281) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L281


 - [ ] ID-454
Parameter [USDO.mint(address,uint256)._amount](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L109) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L109


 - [ ] ID-455
Parameter [Market.setMarketConfig(uint256,IOracle,bytes,address,uint256,uint256,uint256,uint256,uint256,uint256,uint256)._oracleData](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L161) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L161


 - [ ] ID-456
Parameter [OFTCoreV2.setUseCustomAdapterParams(bool)._useCustomAdapterParams](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L62) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L62


 - [ ] ID-457
Parameter [Market.setMarketConfig(uint256,IOracle,bytes,address,uint256,uint256,uint256,uint256,uint256,uint256,uint256)._callerFee](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L163) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L163


 - [ ] ID-458
Parameter [Singularity.setLiquidationQueueConfig(ILiquidationQueue,address,address)._liquidationQueue](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L577) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L577


 - [ ] ID-459
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._srcAddress](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-460
Parameter [Market.setMarketConfig(uint256,IOracle,bytes,address,uint256,uint256,uint256,uint256,uint256,uint256,uint256)._borrowOpeningFee](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L159) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L159


 - [ ] ID-461
Parameter [BaseOFTV2.sendFrom(address,uint16,bytes32,uint256,ICommonOFT.LzCallParams)._dstChainId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17


 - [ ] ID-462
Function [ERC20.DOMAIN_SEPARATOR()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/ERC20.sol#L90-L92) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/ERC20.sol#L90-L92


 - [ ] ID-463
Parameter [BytesLib.toUint32(bytes,uint256)._bytes](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L330) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L330


 - [ ] ID-464
Parameter [USDOMarketModule.lend(address,uint16,bytes,uint64,bytes)._srcAddress](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L137) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L137


 - [ ] ID-465
Parameter [BaseUSDO.setBurnerStatus(address,bool)._status](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L134) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L134


 - [ ] ID-466
Parameter [BaseUSDO.setMaxFlashMintable(uint256)._val](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L88) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L88


 - [ ] ID-467
Parameter [BaseOFTV2.estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)._toAddress](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36


 - [ ] ID-468
Parameter [BaseOFTV2.estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)._dstChainId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36


 - [ ] ID-469
Parameter [USDOOptionsModule.exercise(address,uint16,bytes,uint64,bytes)._payload](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L143) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L143


 - [ ] ID-470
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._nonce](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-471
Parameter [USDO.burn(address,uint256)._amount](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L118) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L118


 - [ ] ID-472
Parameter [NonblockingLzApp.retryMessage(uint16,bytes,uint64,bytes)._payload](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46


 - [ ] ID-473
Parameter [NonblockingLzApp.nonblockingLzReceive(uint16,bytes,uint64,bytes)._payload](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37


 - [ ] ID-474
Parameter [LzApp.setTrustedRemote(uint16,bytes)._srcChainId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L102) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L102


 - [ ] ID-475
Function [MarketERC20.DOMAIN_SEPARATOR()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/MarketERC20.sol#L124-L126) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/MarketERC20.sol#L124-L126


 - [ ] ID-476
Parameter [BytesLib.equal(bytes,bytes)._postBytes](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L396) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L396


 - [ ] ID-477
Parameter [LzApp.setMinDstGas(uint16,uint16,uint256)._dstChainId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L123) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L123


 - [ ] ID-478
Parameter [BytesLib.toUint256(bytes,uint256)._start](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L374) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L374


 - [ ] ID-479
Parameter [USDOOptionsModule.exercise(address,uint16,bytes,uint64,bytes)._nonce](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L142) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L142


 - [ ] ID-480
Parameter [BaseOFTV2.sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,ICommonOFT.LzCallParams)._callParams](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21


 - [ ] ID-481
Parameter [LzApp.lzReceive(uint16,bytes,uint64,bytes)._payload](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35


 - [ ] ID-482
Parameter [USDOLeverageModule.leverageUp(address,uint16,bytes,uint64,bytes)._srcChainId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L135) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L135


 - [ ] ID-483
Parameter [BytesLib.toUint256(bytes,uint256)._bytes](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L374) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L374


 - [ ] ID-484
Parameter [LzApp.setMinDstGas(uint16,uint16,uint256)._packetType](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L123) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L123


 - [ ] ID-485
Parameter [LzApp.setTrustedRemoteAddress(uint16,bytes)._remoteAddress](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L107) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L107


 - [ ] ID-486
Parameter [LzLib.buildAirdropAdapterParams(uint256,LzLib.AirdropParams)._params](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L37) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L37


 - [ ] ID-487
Parameter [BaseOFTV2.estimateSendFee(uint16,bytes32,uint256,bool,bytes)._toAddress](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32


 - [ ] ID-488
Parameter [BaseUSDO.sendAndLendOrRepay(address,address,uint16,address,IUSDOBase.ILendOrRepayParams,ICommonData.IApproval[],ICommonData.IWithdrawParams,bytes)._from](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L314) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L314


 - [ ] ID-489
Parameter [Market.setMarketConfig(uint256,IOracle,bytes,address,uint256,uint256,uint256,uint256,uint256,uint256,uint256)._totalBorrowCap](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L168) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L168


 - [ ] ID-490
Parameter [LzApp.getConfig(uint16,uint16,address,uint256)._version](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L79) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L79


 - [ ] ID-491
Parameter [Market.setMarketConfig(uint256,IOracle,bytes,address,uint256,uint256,uint256,uint256,uint256,uint256,uint256)._oracle](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L160) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L160


 - [ ] ID-492
Variable [EIP712._TYPE_HASH](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L37) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L37


 - [ ] ID-493
Parameter [BaseUSDO.setMinterStatus(address,bool)._for](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L125) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L125


 - [ ] ID-494
Variable [Domain.DOMAIN_SEPARATOR_CHAIN_ID](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L16) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L16


 - [ ] ID-495
Parameter [BaseUSDO.setFlashMintFee(uint256)._val](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L96) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L96


 - [ ] ID-496
Parameter [BytesLib.concatStorage(bytes,bytes)._preBytes](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91


 - [ ] ID-497
Parameter [LzApp.lzReceive(uint16,bytes,uint64,bytes)._srcAddress](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35


 - [ ] ID-498
Parameter [BaseOFTV2.estimateSendFee(uint16,bytes32,uint256,bool,bytes)._amount](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32


 - [ ] ID-499
Parameter [BigBang.setBigBangConfig(uint256,uint256,uint256,uint256)._liquidationMultiplier](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L470) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L470


 - [ ] ID-500
Parameter [USDOMarketModule.sendAndLendOrRepay(address,address,uint16,address,IUSDOBase.ILendOrRepayParams,ICommonData.IApproval[],ICommonData.IWithdrawParams,bytes)._to](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L62) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L62


 - [ ] ID-501
Parameter [LzApp.getConfig(uint16,uint16,address,uint256)._chainId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L79) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L79


 - [ ] ID-502
Parameter [LzApp.setMinDstGas(uint16,uint16,uint256)._minGas](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L123) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L123


 - [ ] ID-503
Parameter [LzApp.isTrustedRemote(uint16,bytes)._srcChainId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L135) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L135


 - [ ] ID-504
Parameter [USDO.burn(address,uint256)._from](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L118) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L118


 - [ ] ID-505
Function [Penrose._getMasterContractLength(IPenrose.MasterContract[])](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L542-L577) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L542-L577


 - [ ] ID-506
Parameter [Market.setBorrowOpeningFee(uint256)._val](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L142) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L142


 - [ ] ID-507
Parameter [BytesLib.slice(bytes,uint256,uint256)._start](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L230) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L230


 - [ ] ID-508
Parameter [LzApp.forceResumeReceive(uint16,bytes)._srcChainId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L96) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L96


 - [ ] ID-509
Parameter [BaseOFTV2.estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)._payload](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36


 - [ ] ID-510
Parameter [BytesLib.concat(bytes,bytes)._preBytes](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L14) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L14


 - [ ] ID-511
Parameter [LzLib.buildAirdropAdapterParams(uint256,LzLib.AirdropParams)._uaGas](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L37) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L37


 - [ ] ID-512
Parameter [ExcessivelySafeCall.excessivelySafeCall(address,uint256,uint16,bytes)._gas](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L25) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L25


 - [ ] ID-513
Variable [EIP712._CACHED_THIS](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L33) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L33


 - [ ] ID-514
Parameter [NonblockingLzApp.nonblockingLzReceive(uint16,bytes,uint64,bytes)._nonce](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37


 - [ ] ID-515
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._to](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-516
Parameter [ExcessivelySafeCall.excessivelySafeStaticCall(address,uint256,uint16,bytes)._maxCopy](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L78) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L78


 - [ ] ID-517
Parameter [BaseOFTV2.sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,ICommonOFT.LzCallParams)._toAddress](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21


 - [ ] ID-518
Parameter [LzLib.buildAdapterParams(LzLib.AirdropParams,uint256)._uaGasLimit](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L21) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L21


 - [ ] ID-519
Parameter [BaseOFTV2.sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,ICommonOFT.LzCallParams)._from](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21


 - [ ] ID-520
Parameter [USDOOptionsModule.exercise(address,uint16,bytes,uint64,bytes)._srcChainId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L140) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L140


 - [ ] ID-521
Parameter [Singularity.setSingularityConfig(uint256,uint256,uint256,uint256,uint64,uint64,uint256)._liquidationMultiplier](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L491) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L491


 - [ ] ID-522
Parameter [BytesLib.slice(bytes,uint256,uint256)._bytes](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L229) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L229


 - [ ] ID-523
Parameter [Singularity.setSingularityConfig(uint256,uint256,uint256,uint256,uint64,uint64,uint256)._minimumTargetUtilization](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L492) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L492


 - [ ] ID-524
Parameter [BigBang.setBigBangConfig(uint256,uint256,uint256,uint256)._minDebtRate](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L467) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L467


 - [ ] ID-525
Parameter [NonblockingLzApp.retryMessage(uint16,bytes,uint64,bytes)._srcAddress](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46


 - [ ] ID-526
Variable [ERC20Permit._PERMIT_TYPEHASH_DEPRECATED_SLOT](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L37) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L37


 - [ ] ID-527
Function [IERC20Permit.DOMAIN_SEPARATOR()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L59) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L59


 - [ ] ID-528
Variable [MarketERC20._PERMIT_TYPEHASH_DEPRECATED_SLOT](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/MarketERC20.sol#L45) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/MarketERC20.sol#L45


 - [ ] ID-529
Parameter [NonblockingLzApp.retryMessage(uint16,bytes,uint64,bytes)._srcChainId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46


 - [ ] ID-530
Parameter [Market.setMarketConfig(uint256,IOracle,bytes,address,uint256,uint256,uint256,uint256,uint256,uint256,uint256)._conservator](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L162) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L162


 - [ ] ID-531
Parameter [Singularity.setSingularityConfig(uint256,uint256,uint256,uint256,uint64,uint64,uint256)._interestElasticity](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L496) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L496


 - [ ] ID-532
Parameter [Penrose.addBigBang(address,address)._contract](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L416) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L416


 - [ ] ID-533
Parameter [BigBang.setBigBangConfig(uint256,uint256,uint256,uint256)._debtRateAgainstEthMarket](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L469) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L469


 - [ ] ID-534
Parameter [USDOOptionsModule.sendFromDestination(bytes)._payload](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L103) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L103


 - [ ] ID-535
Parameter [ExcessivelySafeCall.excessivelySafeStaticCall(address,uint256,uint16,bytes)._gas](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L77) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L77


 - [ ] ID-536
Parameter [BaseOFTV2.estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)._adapterParams](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36


 - [ ] ID-537
Parameter [LzApp.setPayloadSizeLimit(uint16,uint256)._dstChainId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L130) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L130


 - [ ] ID-538
Parameter [LzLib.bytes32ToAddress(bytes32)._bytes32Address](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L74) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L74


 - [ ] ID-539
Parameter [OFTV2.setLdChain(uint16,bool)._isLdChain](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L36


 - [ ] ID-540
Parameter [BaseOFTV2.sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,ICommonOFT.LzCallParams)._dstChainId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21


 - [ ] ID-541
Parameter [BaseOFTV2.estimateSendFee(uint16,bytes32,uint256,bool,bytes)._useZro](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32


 - [ ] ID-542
Variable [SGLStorage.ASSET_SIG](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L50-L51) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L50-L51


 - [ ] ID-543
Variable [EIP712._CACHED_CHAIN_ID](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L32) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L32


 - [ ] ID-544
Parameter [ExcessivelySafeCall.excessivelySafeCall(address,uint256,uint16,bytes)._target](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L24) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L24


 - [ ] ID-545
Parameter [BaseOFTV2.sendFrom(address,uint16,bytes32,uint256,ICommonOFT.LzCallParams)._amount](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17


 - [ ] ID-546
Parameter [Market.computeTVLInfo(address,uint256)._exchangeRate](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L307) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L307


 - [ ] ID-547
Function [ERC20Permit.DOMAIN_SEPARATOR()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L81-L83) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L81-L83


 - [ ] ID-548
Parameter [BaseOFTV2.sendFrom(address,uint16,bytes32,uint256,ICommonOFT.LzCallParams)._from](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17


 - [ ] ID-549
Variable [SGLStorage.COLLATERAL_SIG](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L52-L53) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L52-L53


 - [ ] ID-550
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._payload](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-551
Parameter [NonblockingLzApp.nonblockingLzReceive(uint16,bytes,uint64,bytes)._srcAddress](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37


 - [ ] ID-552
Parameter [BytesLib.toUint16(bytes,uint256)._start](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L319) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L319


 - [ ] ID-553
Parameter [USDOLeverageModule.leverageUp(address,uint16,bytes,uint64,bytes)._nonce](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L137) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L137


 - [ ] ID-554
Parameter [Penrose.addSingularity(address,address)._contract](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L383) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L383


 - [ ] ID-555
Parameter [Market.setMarketConfig(uint256,IOracle,bytes,address,uint256,uint256,uint256,uint256,uint256,uint256,uint256)._collateralizationRate](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L169) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L169


 - [ ] ID-556
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._amount](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-557
Parameter [BaseOFTV2.estimateSendFee(uint16,bytes32,uint256,bool,bytes)._dstChainId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32


 - [ ] ID-558
Parameter [USDOLeverageModule.multiHop(bytes)._payload](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L93) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L93


 - [ ] ID-559
Parameter [LzApp.lzReceive(uint16,bytes,uint64,bytes)._nonce](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35


 - [ ] ID-560
Parameter [Singularity.setLiquidationQueueConfig(ILiquidationQueue,address,address)._bidExecutionSwapper](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L578) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L578


 - [ ] ID-561
Parameter [BaseOFTV2.estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)._useZro](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36


 - [ ] ID-562
Parameter [Singularity.setSingularityConfig(uint256,uint256,uint256,uint256,uint64,uint64,uint256)._lqCollateralizationRate](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L490) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L490


 - [ ] ID-563
Parameter [LzApp.setSendVersion(uint16)._version](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L88) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L88


 - [ ] ID-564
Parameter [USDO.mint(address,uint256)._to](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L109) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/USDO.sol#L109


 - [ ] ID-565
Parameter [LzApp.setConfig(uint16,uint16,uint256,bytes)._configType](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84


 - [ ] ID-566
Parameter [BytesLib.concat(bytes,bytes)._postBytes](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L15) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L15


 - [ ] ID-567
Parameter [LzApp.getConfig(uint16,uint16,address,uint256)._configType](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L79) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L79


 - [ ] ID-568
Parameter [Penrose.setBigBangEthMarket(address)._market](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L263) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L263


 - [ ] ID-569
Parameter [LzLib.getGasLimit(bytes)._adapterParams](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L47) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L47


 - [ ] ID-570
Parameter [ExcessivelySafeCall.excessivelySafeStaticCall(address,uint256,uint16,bytes)._target](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L76) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L76


 - [ ] ID-571
Parameter [BytesLib.toUint16(bytes,uint256)._bytes](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L319) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L319


 - [ ] ID-572
Parameter [USDOMarketModule.sendAndLendOrRepay(address,address,uint16,address,IUSDOBase.ILendOrRepayParams,ICommonData.IApproval[],ICommonData.IWithdrawParams,bytes)._from](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L61) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L61


 - [ ] ID-573
Parameter [NonblockingLzApp.nonblockingLzReceive(uint16,bytes,uint64,bytes)._srcChainId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37


 - [ ] ID-574
Parameter [BytesLib.toUint32(bytes,uint256)._start](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L330) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L330


 - [ ] ID-575
Parameter [BytesLib.toUint64(bytes,uint256)._start](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L341) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L341


 - [ ] ID-576
Parameter [LzApp.setPayloadSizeLimit(uint16,uint256)._size](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L130) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L130


 - [ ] ID-577
Variable [EIP712._HASHED_NAME](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L35) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L35


 - [ ] ID-578
Function [YieldBoxPermit.DOMAIN_SEPARATOR()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L109-L111) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L109-L111


 - [ ] ID-579
Parameter [Singularity.setSingularityConfig(uint256,uint256,uint256,uint256,uint64,uint64,uint256)._maximumInterestPerSecond](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L495) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L495


 - [ ] ID-580
Parameter [Market.setMarketConfig(uint256,IOracle,bytes,address,uint256,uint256,uint256,uint256,uint256,uint256,uint256)._liquidationBonusAmount](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L165) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L165


 - [ ] ID-581
Parameter [BigBang.setBigBangConfig(uint256,uint256,uint256,uint256)._maxDebtRate](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L468) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/bigBang/BigBang.sol#L468


 - [ ] ID-582
Parameter [BytesLib.toUint96(bytes,uint256)._bytes](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L352) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L352


 - [ ] ID-583
Parameter [BaseUSDO.setBurnerStatus(address,bool)._for](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L134) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L134


 - [ ] ID-584
Parameter [LzApp.setConfig(uint16,uint16,uint256,bytes)._config](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84


 - [ ] ID-585
Parameter [LzLib.addressToBytes32(address)._address](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L78) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L78


 - [ ] ID-586
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._gasForCall](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-587
Parameter [Market.setMarketConfig(uint256,IOracle,bytes,address,uint256,uint256,uint256,uint256,uint256,uint256,uint256)._minLiquidatorReward](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L166) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L166


 - [ ] ID-588
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._from](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-589
Parameter [BytesLib.toUint96(bytes,uint256)._start](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L352) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L352


 - [ ] ID-590
Parameter [Singularity.yieldBoxShares(address,uint256)._assetId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L166) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L166


 - [ ] ID-591
Parameter [LzApp.setPrecrime(address)._precrime](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L118) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L118


 - [ ] ID-592
Parameter [OFTV2.setLdChain(uint16,bool)._chainId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L36


 - [ ] ID-593
Parameter [LzApp.getTrustedRemoteAddress(uint16)._remoteChainId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L112) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L112


 - [ ] ID-594
Variable [SGLStorage._yieldBoxShares](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L49) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L49


 - [ ] ID-595
Variable [EIP712._CACHED_DOMAIN_SEPARATOR](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L31) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L31


 - [ ] ID-596
Parameter [LzLib.buildDefaultAdapterParams(uint256)._uaGas](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L30) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L30


 - [ ] ID-597
Parameter [Penrose.setBigBangEthMarketDebtRate(uint256)._rate](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L256) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/Penrose.sol#L256


 - [ ] ID-598
Variable [Market.EXCHANGE_RATE_PRECISION](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L82) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L82


 - [ ] ID-599
Parameter [USDOLeverageModule.leverageUp(address,uint16,bytes,uint64,bytes)._payload](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L138) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L138


 - [ ] ID-600
Parameter [BytesLib.slice(bytes,uint256,uint256)._length](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L231) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L231


 - [ ] ID-601
Parameter [Market.setMarketConfig(uint256,IOracle,bytes,address,uint256,uint256,uint256,uint256,uint256,uint256,uint256)._protocolFee](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L164) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L164


 - [ ] ID-602
Variable [EIP712._HASHED_VERSION](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L36


 - [ ] ID-603
Parameter [BaseUSDO.setMinterStatus(address,bool)._status](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L125) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L125


 - [ ] ID-604
Parameter [Singularity.setSingularityConfig(uint256,uint256,uint256,uint256,uint64,uint64,uint256)._minimumInterestPerSecond](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L494) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L494


## similar-names
Impact: Informational
Confidence: Medium
 - [ ] ID-605
Variable [Singularity.setSingularityConfig(uint256,uint256,uint256,uint256,uint64,uint64,uint256)._maximumTargetUtilization](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L493) is too similar to [Singularity.setSingularityConfig(uint256,uint256,uint256,uint256,uint64,uint64,uint256)._minimumTargetUtilization](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L492)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L493


 - [ ] ID-606
Variable [USDOLeverageModule._callApproval(ICommonData.IApproval[]).reason_scope_0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L282) is too similar to [USDOLeverageModule._callApproval(ICommonData.IApproval[]).reason_scope_1](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L298)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L282


 - [ ] ID-607
Variable [BaseERC1155Strategy.constructor(IYieldBox,address,uint256)._contractAddress](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L64) is too similar to [IStrategy.contractAddress().contractAddress_](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IStrategy.sol#L36)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L64


 - [ ] ID-608
Variable [BaseERC20Strategy.constructor(IYieldBox,address)._contractAddress](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L54) is too similar to [IStrategy.contractAddress().contractAddress_](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IStrategy.sol#L36)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L54


 - [ ] ID-609
Variable [SGLStorage.maximumTargetUtilization](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L58) is too similar to [SGLStorage.minimumTargetUtilization](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L57)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L58


 - [ ] ID-610
Variable [SGLStorage.maximumInterestPerSecond](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L62) is too similar to [SGLStorage.minimumInterestPerSecond](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L61)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L62


 - [ ] ID-611
Variable [Singularity.setSingularityConfig(uint256,uint256,uint256,uint256,uint64,uint64,uint256)._maximumInterestPerSecond](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L495) is too similar to [Singularity.setSingularityConfig(uint256,uint256,uint256,uint256,uint64,uint64,uint256)._minimumInterestPerSecond](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L494)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L495


 - [ ] ID-612
Variable [USDOOptionsModule._callApproval(ICommonData.IApproval[]).reason_scope_0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L272) is too similar to [USDOOptionsModule._callApproval(ICommonData.IApproval[]).reason_scope_1](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L288)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L272


 - [ ] ID-613
Variable [USDOMarketModule._callApproval(ICommonData.IApproval[]).reason_scope_0](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L271) is too similar to [USDOMarketModule._callApproval(ICommonData.IApproval[]).reason_scope_1](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L287)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L271


## too-many-digits
Impact: Informational
Confidence: Medium
 - [ ] ID-614
[BoringFactory.deploy(address,bytes,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67) uses literals with too many digits:
        - [mstore(uint256,uint256)(clone_deploy_asm_0 + 0x28,0x5af43d82803e903d91602b57fd5bf30000000000000000000000000000000000)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L49)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67


 - [ ] ID-615
[BoringFactory.deploy(address,bytes,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67) uses literals with too many digits:
        - [mstore(uint256,uint256)(clone_deploy_asm_0,0x3d602d80600a3d3981f3363d3d373d3d3d363d73000000000000000000000000)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L47)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67


 - [ ] ID-616
[BytesLib.toAddress(bytes,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297-L306) uses literals with too many digits:
        - [tempAddress = mload(uint256)(_bytes + 0x20 + _start) / 0x1000000000000000000000000](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L302)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297-L306


 - [ ] ID-617
[BoringFactory.deploy(address,bytes,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67) uses literals with too many digits:
        - [mstore(uint256,uint256)(clone_deploy_asm_1,0x3d602d80600a3d3981f3363d3d373d3d3d363d73000000000000000000000000)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L55)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67


 - [ ] ID-618
[BoringFactory.deploy(address,bytes,bool)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67) uses literals with too many digits:
        - [mstore(uint256,uint256)(clone_deploy_asm_1 + 0x28,0x5af43d82803e903d91602b57fd5bf30000000000000000000000000000000000)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L57)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67


 - [ ] ID-619
[ExcessivelySafeCall.slitherConstructorConstantVariables()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L4-L136) uses literals with too many digits:
        - [LOW_28_MASK = 0x00000000ffffffffffffffffffffffffffffffffffffffffffffffffffffffff](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L5-L6)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L4-L136


## unimplemented-functions
Impact: Informational
Confidence: High
 - [ ] ID-620
[BaseERC1155Strategy](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L59-L68) does not implement functions:
        - [BaseStrategy._currentBalance()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L20)
        - [BaseStrategy._deposited(uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L34)
        - [BaseStrategy._withdraw(address,uint256)](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L41)
        - [IStrategy.description()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IStrategy.sol#L26)
        - [IStrategy.name()](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IStrategy.sol#L23)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L59-L68


## unused-state
Impact: Informational
Confidence: High
 - [ ] ID-621
[BaseUSDOStorage.PT_LEVERAGE_MARKET_UP](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L44) is never used in [USDOOptionsModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L16-L300)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L44


 - [ ] ID-622
[Market.FEE_PRECISION_DECIMALS](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L84) is never used in [Singularity](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/Singularity.sol#L37-L645)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L84


 - [ ] ID-623
[BaseUSDOStorage.FLASH_MINT_CALLBACK_SUCCESS](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L38-L39) is never used in [USDOOptionsModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L16-L300)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L38-L39


 - [ ] ID-624
[BaseUSDOStorage.PT_SEND_FROM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L46) is never used in [USDOMarketModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L21-L299)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L46


 - [ ] ID-625
[BaseUSDOStorage.PT_YB_SEND_SGL_LEND_OR_REPAY](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L43) is never used in [USDOLeverageModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L19-L310)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L43


 - [ ] ID-626
[Market.FEE_PRECISION_DECIMALS](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L84) is never used in [SGLLeverage](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L10-L187)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L84


 - [ ] ID-627
[BaseUSDOStorage.FLASH_MINT_CALLBACK_SUCCESS](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L38-L39) is never used in [USDOLeverageModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L19-L310)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L38-L39


 - [ ] ID-628
[Market.FEE_PRECISION_DECIMALS](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L84) is never used in [SGLCollateral](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCollateral.sol#L8-L42)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L84


 - [ ] ID-629
[BaseUSDOStorage.PT_YB_SEND_SGL_LEND_OR_REPAY](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L43) is never used in [USDOOptionsModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L16-L300)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L43


 - [ ] ID-630
[BaseUSDOStorage.PT_TAP_EXERCISE](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L45) is never used in [USDOMarketModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L21-L299)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L45


 - [ ] ID-631
[SGLStorage.FULL_UTILIZATION](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L143) is never used in [SGLLeverage](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLeverage.sol#L10-L187)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L143


 - [ ] ID-632
[BaseUSDOStorage.PT_MARKET_MULTIHOP_BUY](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L41) is never used in [USDOOptionsModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L16-L300)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L41


 - [ ] ID-633
[BaseUSDOStorage.PT_MARKET_MULTIHOP_BUY](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L41) is never used in [USDOMarketModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L21-L299)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L41


 - [ ] ID-634
[Market.FEE_PRECISION_DECIMALS](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L84) is never used in [SGLBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L8-L57)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L84


 - [ ] ID-635
[BaseUSDOStorage.PT_MARKET_REMOVE_ASSET](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L42) is never used in [USDOLeverageModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L19-L310)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L42


 - [ ] ID-636
[BaseUSDOStorage.PT_SEND_FROM](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L46) is never used in [USDOLeverageModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L19-L310)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L46


 - [ ] ID-637
[BaseUSDOStorage.PT_MARKET_REMOVE_ASSET](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L42) is never used in [USDOOptionsModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L16-L300)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L42


 - [ ] ID-638
[BaseUSDOStorage.FLASH_MINT_FEE_PRECISION](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L37) is never used in [USDOLeverageModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L19-L310)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L37


 - [ ] ID-639
[BaseUSDOStorage.PT_TAP_EXERCISE](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L45) is never used in [USDOLeverageModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOLeverageModule.sol#L19-L310)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L45


 - [ ] ID-640
[BaseUSDOStorage.FLASH_MINT_CALLBACK_SUCCESS](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L38-L39) is never used in [USDOMarketModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L21-L299)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L38-L39


 - [ ] ID-641
[SGLStorage.FULL_UTILIZATION](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L143) is never used in [SGLLiquidation](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLLiquidation.sol#L10-L399)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L143


 - [ ] ID-642
[SGLStorage.FULL_UTILIZATION](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L143) is never used in [SGLBorrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLBorrow.sol#L8-L57)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L143


 - [ ] ID-643
[BaseUSDOStorage.FLASH_MINT_FEE_PRECISION](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L37) is never used in [USDOMarketModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L21-L299)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L37


 - [ ] ID-644
[SGLStorage.FULL_UTILIZATION](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L143) is never used in [SGLCollateral](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLCollateral.sol#L8-L42)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L143


 - [ ] ID-645
[BaseUSDOStorage.PT_LEVERAGE_MARKET_UP](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L44) is never used in [USDOMarketModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOMarketModule.sol#L21-L299)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L44


 - [ ] ID-646
[BaseUSDOStorage.FLASH_MINT_FEE_PRECISION](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L37) is never used in [USDOOptionsModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/modules/USDOOptionsModule.sol#L16-L300)

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L37


## constable-states
Impact: Optimization
Confidence: High
 - [ ] ID-647
[Market.assetId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L32) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L32


 - [ ] ID-648
[SGLStorage.minimumTargetUtilization](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L57) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L57


 - [ ] ID-649
[SGLStorage.COLLATERAL_SIG](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L52-L53) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L52-L53


 - [ ] ID-650
[Market.collateral](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L26) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L26


 - [ ] ID-651
[Market.penrose](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L23) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L23


 - [ ] ID-652
[BaseUSDOStorage.paused](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L30) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L30


 - [ ] ID-653
[Market.EXCHANGE_RATE_PRECISION](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L82) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L82


 - [ ] ID-654
[SGLStorage.minimumInterestPerSecond](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L61) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L61


 - [ ] ID-655
[Market.liquidationMultiplier](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L77) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L77


 - [ ] ID-656
[SGLStorage.liquidationQueue](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L46) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L46


 - [ ] ID-657
[Market.yieldBox](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L21) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L21


 - [ ] ID-658
[SGLStorage.lqCollateralizationRate](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L55) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L55


 - [ ] ID-659
[SGLStorage.maximumTargetUtilization](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L58) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L58


 - [ ] ID-660
[SGLStorage.fullUtilizationMinusMax](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L59) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L59


 - [ ] ID-661
[SGLStorage.maximumInterestPerSecond](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L62) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L62


 - [ ] ID-662
[Market.totalCollateralShare](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L53) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L53


 - [ ] ID-663
[Market.collateralId](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L28) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L28


 - [ ] ID-664
[SGLStorage.ASSET_SIG](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L50-L51) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L50-L51


 - [ ] ID-665
[SGLStorage.interestElasticity](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L63) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L63


 - [ ] ID-666
[SGLStorage.startingInterestPerSecond](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L64) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/singularity/SGLStorage.sol#L64


 - [ ] ID-667
[Market.asset](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L30) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/markets/Market.sol#L30


 - [ ] ID-668
[BaseUSDOStorage.conservator](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L22) should be constant

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L22


## immutable-states
Impact: Optimization
Confidence: High
 - [ ] ID-669
[BaseUSDO.leverageModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L59) should be immutable

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L59


 - [ ] ID-670
[BaseUSDO.marketModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L62) should be immutable

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L62


 - [ ] ID-671
[BaseUSDO.optionsModule](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L65) should be immutable

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDO.sol#L65


 - [ ] ID-672
[BaseUSDOStorage.maxFlashMint](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L35) should be immutable

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L35


 - [ ] ID-673
[BaseUSDOStorage.flashMintFee](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L33) should be immutable

https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/main/contracts/usd0/BaseUSDOStorage.sol#L33


INFO:Slither:. analyzed (113 contracts with 88 detectors), 674 result(s) found
