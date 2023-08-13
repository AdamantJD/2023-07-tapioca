Summary
 - [arbitrary-send-erc20](#arbitrary-send-erc20) (1 results) (High)
 - [arbitrary-send-eth](#arbitrary-send-eth) (1 results) (High)
 - [controlled-delegatecall](#controlled-delegatecall) (5 results) (High)
 - [msg-value-loop](#msg-value-loop) (1 results) (High)
 - [divide-before-multiply](#divide-before-multiply) (12 results) (Medium)
 - [locked-ether](#locked-ether) (1 results) (Medium)
 - [reentrancy-no-eth](#reentrancy-no-eth) (1 results) (Medium)
 - [unchecked-lowlevel](#unchecked-lowlevel) (3 results) (Medium)
 - [uninitialized-local](#uninitialized-local) (3 results) (Medium)
 - [unused-return](#unused-return) (8 results) (Medium)
 - [write-after-write](#write-after-write) (1 results) (Medium)
 - [shadowing-local](#shadowing-local) (21 results) (Low)
 - [missing-zero-check](#missing-zero-check) (10 results) (Low)
 - [calls-loop](#calls-loop) (2 results) (Low)
 - [reentrancy-benign](#reentrancy-benign) (5 results) (Low)
 - [reentrancy-events](#reentrancy-events) (24 results) (Low)
 - [timestamp](#timestamp) (1 results) (Low)
 - [assembly](#assembly) (27 results) (Informational)
 - [pragma](#pragma) (1 results) (Informational)
 - [cyclomatic-complexity](#cyclomatic-complexity) (3 results) (Informational)
 - [solc-version](#solc-version) (33 results) (Informational)
 - [low-level-calls](#low-level-calls) (13 results) (Informational)
 - [missing-inheritance](#missing-inheritance) (1 results) (Informational)
 - [naming-convention](#naming-convention) (202 results) (Informational)
 - [similar-names](#similar-names) (3 results) (Informational)
 - [too-many-digits](#too-many-digits) (2 results) (Informational)
 - [unused-state](#unused-state) (24 results) (Informational)
 - [immutable-states](#immutable-states) (8 results) (Optimization)
## arbitrary-send-erc20
Impact: High
Confidence: High
 - [ ] ID-0
[BaseTOFT._wrap(address,address,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L348-L361) uses arbitrary from in transferFrom: [IERC20(erc20).safeTransferFrom(_fromAddress,address(this),_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L359)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L348-L361


## arbitrary-send-eth
Impact: High
Confidence: Medium
 - [ ] ID-1
[BaseTOFTMarketModule.remove(bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L204-L258) sends eth to arbitrary user
        Dangerous calls:
        - [IMagnetar(removeParams.marketHelper).withdrawToChain{value: withdrawParams.withdrawLzFeeAmount}(ybAddress,to,assetId,withdrawParams.withdrawLzChainId,LzLib.addressToBytes32(to),IYieldBoxBase(ybAddress).toAmount(assetId,removeParams.share,false),removeParams.share,withdrawParams.withdrawAdapterParams,address(to),withdrawParams.withdrawLzFeeAmount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L239-L256)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L204-L258


## controlled-delegatecall
Impact: High
Confidence: Medium
 - [ ] ID-2
[BaseTOFT._executeModule(BaseTOFT.Module,bytes,bool)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L403-L415) uses delegatecall to a input-controlled function id
        - [(success,returnData) = module.delegatecall(_data)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L411)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L403-L415


 - [ ] ID-3
[BaseTOFTLeverageModule.leverageDown(address,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L148-L203) uses delegatecall to a input-controlled function id
        - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.leverageDownInternal.selector,amount,swapData,externalData,lzData,leverageFor))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L184-L193)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L148-L203


 - [ ] ID-4
[BaseTOFTMarketModule.borrow(address,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L126-L178) uses delegatecall to a input-controlled function id
        - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.borrowInternal.selector,_to,borrowParams,withdrawParams,approvals))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L160-L168)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L126-L178


 - [ ] ID-5
[BaseTOFTStrategyModule.strategyDeposit(address,uint16,bytes,uint64,bytes,IERC20)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L122-L171) uses delegatecall to a input-controlled function id
        - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.depositToYieldbox.selector,assetId,amount,share,_erc20,address(this),onBehalfOf))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L152-L162)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L122-L171


 - [ ] ID-6
[BaseTOFTOptionsModule.exercise(address,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L153-L219) uses delegatecall to a input-controlled function id
        - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.exerciseInternal.selector,optionsData.from,optionsData.oTAPTokenID,optionsData.paymentToken,optionsData.tapAmount,optionsData.target,tapSendData,approvals))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L189-L200)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L153-L219


## msg-value-loop
Impact: High
Confidence: Medium
 - [ ] ID-7
[TapiocaWrapper.executeCalls(TapiocaWrapper.ExecutionCall[])](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L131-L148) use msg.value in a loop: [(success,results[i]) = address(_call[i].toft).call{value: msg.value}(_call[i].bytecode)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L141-L143)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L131-L148


## divide-before-multiply
Impact: Medium
Confidence: Medium
 - [ ] ID-8
[BytesLib.concatStorage(bytes,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226) performs a multiplication on the result of a division:
        - [sstore(uint256,uint256)(sc_concatStorage_asm_0,mload(uint256)(mc_concatStorage_asm_0) / mask_concatStorage_asm_0 * mask_concatStorage_asm_0)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L223)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226


 - [ ] ID-9
[BytesLib.concatStorage(bytes,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226) performs a multiplication on the result of a division:
        - [sstore(uint256,uint256)(_preBytes,fslot_concatStorage_asm_0 + mload(uint256)(_postBytes + 0x20) / 0x100 ** 32 - mlength_concatStorage_asm_0 * 0x100 ** 32 - newlength_concatStorage_asm_0 + mlength_concatStorage_asm_0 * 2)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L115-L140)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226


 - [ ] ID-10
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L126)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-11
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L124)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-12
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L123)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-13
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L121)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-14
[BytesLib.equalStorage(bytes,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L439-L509) performs a multiplication on the result of a division:
        - [fslot_equalStorage_asm_0 = fslot_equalStorage_asm_0 / 0x100 * 0x100](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L466)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L439-L509


 - [ ] ID-15
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
        - [inverse = (3 * denominator) ^ 2](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L117)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-16
[BytesLib.concatStorage(bytes,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226) performs a multiplication on the result of a division:
        - [sstore(uint256,uint256)(sc_concatStorage_asm_0,mload(uint256)(mc_concatStorage_asm_0) / mask_concatStorage_asm_0 * mask_concatStorage_asm_0)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L189)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226


 - [ ] ID-17
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L122)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-18
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [prod0 = prod0 / twos](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L105)
        - [result = prod0 * inverse](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L132)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-19
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L125)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


## locked-ether
Impact: Medium
Confidence: High
 - [ ] ID-20
Contract locking ether found:
        Contract [Balancer](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L34-L343) has payable functions:
         - [Balancer.rebalance(address,uint16,uint256,uint256,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L172-L212)
         - [Balancer.receive()](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L342)
        But does not have a function to withdraw the ether

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L34-L343


## reentrancy-no-eth
Impact: Medium
Confidence: Medium
 - [ ] ID-21
Reentrancy in [Balancer.rebalance(address,uint16,uint256,uint256,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L172-L212):
        External calls:
        - [ITapiocaOFT(_srcOft).extractUnderlying(_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L198)
        - [_sendNative(_srcOft,_amount,_dstChainId,_slippage)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L204)
                - [routerETH.swapETH(_dstChainId,_oft,abi.encodePacked(connectedOFTs[_oft][_dstChainId].dstOft),_amount,_computeMinAmount(_amount,_slippage))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L288-L294)
        - [_sendToken(_srcOft,_amount,_dstChainId,_slippage,_ercData)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L207)
                - [erc20.approve(address(router),_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L321)
                - [router.swap(_dstChainId,_srcPoolId,_dstPoolId,_oft,_amount,_computeMinAmount(_amount,_slippage),_lzTxParams,_lzTxParams.dstNativeAddr,0x)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L322-L332)
        State variables written after the call(s):
        - [connectedOFTs[_srcOft][_dstChainId].rebalanceable -= _amount](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L210)
        [Balancer.connectedOFTs](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L49) can be used in cross function reentrancies:
        - [Balancer._sendNative(address,uint256,uint16,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L280-L295)
        - [Balancer._sendToken(address,uint256,uint16,uint256,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L297-L333)
        - [Balancer.addRebalanceAmount(address,uint16,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L250-L262)
        - [Balancer.checker(address,uint16)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L137-L160)
        - [Balancer.connectedOFTs](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L49)
        - [Balancer.initConnectedOFT(address,uint16,address,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L219-L244)
        - [Balancer.onlyValidDestination(address,uint16)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L111-L115)
        - [Balancer.rebalance(address,uint16,uint256,uint256,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L172-L212)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L172-L212


## unchecked-lowlevel
Impact: Medium
Confidence: Medium
 - [ ] ID-22
[Address.sendValue(address,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L60-L65) ignores return value by [(success) = recipient.call{value: amount}()](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L63)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L60-L65


 - [ ] ID-23
[BaseTOFT._safeTransferETH(address,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L379-L382) ignores return value by [(sent) = to.call{value: amount}()](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L380)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L379-L382


 - [ ] ID-24
[BaseTOFTLeverageModule._safeTransferETH(address,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L279-L282) ignores return value by [(sent) = to.call{value: amount}()](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L280)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L279-L282


## uninitialized-local
Impact: Medium
Confidence: Medium
 - [ ] ID-25
[BaseTOFTLeverageModule.leverageDownInternal(uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageExternalContractsData,IUSDOBase.ILeverageLZData,address).approvals](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L228) is a local variable never initialized

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L228


 - [ ] ID-26
[Balancer.checker(address,uint16).ercData](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L141) is a local variable never initialized

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L141


 - [ ] ID-27
[BaseTOFT._extractModule(BaseTOFT.Module).module](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L385) is a local variable never initialized

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L385


## unused-return
Impact: Medium
Confidence: Medium
 - [ ] ID-28
[BaseTOFTStrategyModule.depositToYieldbox(uint256,uint256,uint256,IERC20,address,address)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L173-L186) ignores return value by [yieldBox.depositAsset(_assetId,_from,_to,_amount,_share)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L185)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L173-L186


 - [ ] ID-29
[OFTCoreV2._estimateSendFee(uint16,bytes32,uint256,bool,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L70-L74) ignores return value by [lzEndpoint.estimateFees(_dstChainId,address(this),payload,_useZro,_adapterParams)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L73)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L70-L74


 - [ ] ID-30
[BaseTOFTStrategyModule.depositToYieldbox(uint256,uint256,uint256,IERC20,address,address)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L173-L186) ignores return value by [_erc20.approve(address(yieldBox),_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L184)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L173-L186


 - [ ] ID-31
[Balancer._sendToken(address,uint256,uint16,uint256,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L297-L333) ignores return value by [erc20.approve(address(router),_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L321)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L297-L333


 - [ ] ID-32
[BaseTOFTLeverageModule.leverageDownInternal(uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageExternalContractsData,IUSDOBase.ILeverageLZData,address)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L205-L267) ignores return value by [(amountOut) = ISwapper(externalData.swapper).swap(_swapperData,swapData.amountOutMin,address(this),swapData.data)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L218-L223)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L205-L267


 - [ ] ID-33
[BaseTOFTStrategyModule._retrieveFromYieldBox(uint256,uint256,uint256,address,address)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L240-L248) ignores return value by [yieldBox.withdraw(_assetId,_from,_to,_amount,_share)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L247)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L240-L248


 - [ ] ID-34
[OFTCoreV2._estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L76-L80) ignores return value by [lzEndpoint.estimateFees(_dstChainId,address(this),payload,_useZro,_adapterParams)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L79)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L76-L80


 - [ ] ID-35
[BaseTOFTLeverageModule.leverageDownInternal(uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageExternalContractsData,IUSDOBase.ILeverageLZData,address)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L205-L267) ignores return value by [IERC20(erc20).approve(externalData.swapper,amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L215)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L205-L267


## write-after-write
Impact: Medium
Confidence: High
 - [ ] ID-36
[BaseTOFT._executeModule(BaseTOFT.Module,bytes,bool).success](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L407) is written in both
        [success = true](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L408)
        [(success,returnData) = module.delegatecall(_data)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L411)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L407


## shadowing-local
Impact: Low
Confidence: High
 - [ ] ID-37
[BaseTOFTLeverageModule.constructor(address,address,IYieldBoxBase,string,string,uint8,uint256)._name](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L29) shadows:
        - [ERC20._name](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L42) (state variable)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L29


 - [ ] ID-38
[BaseTOFTLeverageModule.constructor(address,address,IYieldBoxBase,string,string,uint8,uint256)._symbol](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L30) shadows:
        - [ERC20._symbol](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L43) (state variable)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L30


 - [ ] ID-39
[BaseTOFT.constructor(address,address,IYieldBoxBase,string,string,uint8,uint256,address,address,address,address)._name](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L54) shadows:
        - [ERC20._name](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L42) (state variable)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L54


 - [ ] ID-40
[BaseTOFTOptionsModule.constructor(address,address,IYieldBoxBase,string,string,uint8,uint256)._symbol](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L24) shadows:
        - [ERC20._symbol](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L43) (state variable)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L24


 - [ ] ID-41
[BaseTOFTMarketModule.constructor(address,address,IYieldBoxBase,string,string,uint8,uint256)._symbol](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L29) shadows:
        - [ERC20._symbol](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L43) (state variable)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L29


 - [ ] ID-42
[ERC20Permit.constructor(string).name](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L44) shadows:
        - [ERC20.name()](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L62-L64) (function)
        - [IERC20Metadata.name()](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L17) (function)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L44


 - [ ] ID-43
[TapiocaOFT.constructor(address,address,IYieldBoxBase,string,string,uint8,uint256,address,address,address,address)._symbol](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/TapiocaOFT.sol#L38) shadows:
        - [ERC20._symbol](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L43) (state variable)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/TapiocaOFT.sol#L38


 - [ ] ID-44
[OFTV2.constructor(string,string,uint8,address).decimals](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L14) shadows:
        - [ERC20.decimals()](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L87-L89) (function)
        - [IERC20Metadata.decimals()](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L27) (function)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L14


 - [ ] ID-45
[BaseTOFTMarketModule.constructor(address,address,IYieldBoxBase,string,string,uint8,uint256)._name](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L28) shadows:
        - [ERC20._name](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L42) (state variable)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L28


 - [ ] ID-46
[BaseTOFTOptionsModule.constructor(address,address,IYieldBoxBase,string,string,uint8,uint256)._name](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L23) shadows:
        - [ERC20._name](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L42) (state variable)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L23


 - [ ] ID-47
[BaseTOFTStrategyModule.constructor(address,address,IYieldBoxBase,string,string,uint8,uint256)._name](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L24) shadows:
        - [ERC20._name](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L42) (state variable)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L24


 - [ ] ID-48
[TapiocaOFT.constructor(address,address,IYieldBoxBase,string,string,uint8,uint256,address,address,address,address)._name](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/TapiocaOFT.sol#L37) shadows:
        - [ERC20._name](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L42) (state variable)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/TapiocaOFT.sol#L37


 - [ ] ID-49
[BaseTOFTStrategyModule.constructor(address,address,IYieldBoxBase,string,string,uint8,uint256)._symbol](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L25) shadows:
        - [ERC20._symbol](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L43) (state variable)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L25


 - [ ] ID-50
[mTapiocaOFT.constructor(address,address,IYieldBoxBase,string,string,uint8,uint256,address,address,address,address)._symbol](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L54) shadows:
        - [ERC20._symbol](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L43) (state variable)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L54


 - [ ] ID-51
[OFTV2.constructor(string,string,uint8,address)._symbol](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L13) shadows:
        - [ERC20._symbol](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L43) (state variable)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L13


 - [ ] ID-52
[BaseTOFTStorage.constructor(address,address,IYieldBoxBase,string,string,uint8,uint256)._symbol](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L50) shadows:
        - [ERC20._symbol](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L43) (state variable)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L50


 - [ ] ID-53
[mTapiocaOFT.constructor(address,address,IYieldBoxBase,string,string,uint8,uint256,address,address,address,address)._name](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L53) shadows:
        - [ERC20._name](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L42) (state variable)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L53


 - [ ] ID-54
[TapiocaWrapper.constructor(address)._owner](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L67) shadows:
        - [Ownable._owner](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/access/Ownable.sol#L21) (state variable)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L67


 - [ ] ID-55
[OFTV2.constructor(string,string,uint8,address)._name](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L13) shadows:
        - [ERC20._name](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L42) (state variable)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L13


 - [ ] ID-56
[BaseTOFTStorage.constructor(address,address,IYieldBoxBase,string,string,uint8,uint256)._name](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L49) shadows:
        - [ERC20._name](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L42) (state variable)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L49


 - [ ] ID-57
[BaseTOFT.constructor(address,address,IYieldBoxBase,string,string,uint8,uint256,address,address,address,address)._symbol](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L55) shadows:
        - [ERC20._symbol](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L43) (state variable)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L55


## missing-zero-check
Impact: Low
Confidence: Medium
 - [ ] ID-58
[BaseTOFTMarketModule.borrow(address,uint16,bytes,uint64,bytes).module](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L127) lacks a zero-check on :
                - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.borrowInternal.selector,_to,borrowParams,withdrawParams,approvals))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L160-L168)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L127


 - [ ] ID-59
[BaseTOFTOptionsModule.exercise(address,uint16,bytes,uint64,bytes).module](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L154) lacks a zero-check on :
                - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.exerciseInternal.selector,optionsData.from,optionsData.oTAPTokenID,optionsData.paymentToken,optionsData.tapAmount,optionsData.target,tapSendData,approvals))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L189-L200)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L154


 - [ ] ID-60
[BaseTOFTLeverageModule.leverageDown(address,uint16,bytes,uint64,bytes).module](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L149) lacks a zero-check on :
                - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.leverageDownInternal.selector,amount,swapData,externalData,lzData,leverageFor))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L184-L193)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L149


 - [ ] ID-61
[BaseTOFTLeverageModule.leverageDown(address,uint16,bytes,uint64,bytes).leverageFor](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L162) lacks a zero-check on :
                - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.leverageDownInternal.selector,amount,swapData,externalData,lzData,leverageFor))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L184-L193)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L162


 - [ ] ID-62
[BaseTOFTStrategyModule.strategyDeposit(address,uint16,bytes,uint64,bytes,IERC20).onBehalfOf](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L151) lacks a zero-check on :
                - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.depositToYieldbox.selector,assetId,amount,share,_erc20,address(this),onBehalfOf))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L152-L162)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L151


 - [ ] ID-63
[BaseTOFTStorage.constructor(address,address,IYieldBoxBase,string,string,uint8,uint256)._erc20](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L47) lacks a zero-check on :
                - [erc20 = _erc20](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L61)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L47


 - [ ] ID-64
[Owned.setOwner(address).newOwner](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@rari-capital/solmate/src/auth/Owned.sol#L39) lacks a zero-check on :
                - [owner = newOwner](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@rari-capital/solmate/src/auth/Owned.sol#L40)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@rari-capital/solmate/src/auth/Owned.sol#L39


 - [ ] ID-65
[BaseTOFTStrategyModule.strategyDeposit(address,uint16,bytes,uint64,bytes,IERC20).module](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L123) lacks a zero-check on :
                - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.depositToYieldbox.selector,assetId,amount,share,_erc20,address(this),onBehalfOf))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L152-L162)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L123


 - [ ] ID-66
[TapiocaWrapper.executeTOFT(address,bytes,bool)._toft](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L116) lacks a zero-check on :
                - [(success,result) = address(_toft).call{value: msg.value}(_bytecode)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L120)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L116


 - [ ] ID-67
[LzApp.setPrecrime(address)._precrime](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L118) lacks a zero-check on :
                - [precrime = _precrime](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L119)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L118


## calls-loop
Impact: Low
Confidence: Medium
 - [ ] ID-68
[TapiocaWrapper.executeCalls(TapiocaWrapper.ExecutionCall[])](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L131-L148) has external calls inside a loop: [(success,results[i]) = address(_call[i].toft).call{value: msg.value}(_call[i].bytecode)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L141-L143)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L131-L148


 - [ ] ID-69
[TapiocaWrapper.harvestFees()](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L97-L102) has external calls inside a loop: [harvestableTapiocaOFTs[i].harvestFees()](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L99)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L97-L102


## reentrancy-benign
Impact: Low
Confidence: Medium
 - [ ] ID-70
Reentrancy in [BaseTOFTMarketModule.remove(bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L204-L258):
        External calls:
        - [_callApproval(approvals)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L227)
                - [IPermitBorrow(approvals[i].target).permitBorrow(approvals[i].owner,approvals[i].spender,approvals[i].value,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L263-L277)
                - [IPermitAll(approvals[i].target).permitAll(approvals[i].owner,approvals[i].spender,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L279-L292)
                - [IERC20Permit(approvals[i].target).permit(approvals[i].owner,approvals[i].spender,approvals[i].value,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L294-L308)
        State variables written after the call(s):
        - [approve(removeParams.market,removeParams.share)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L230)
                - [_allowances[owner][spender] = amount](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L324)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L204-L258


 - [ ] ID-71
Reentrancy in [BaseTOFTMarketModule.borrowInternal(bytes32,ITapiocaOFT.IBorrowParams,ICommonData.IWithdrawParams,ICommonData.IApproval[])](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L180-L202):
        External calls:
        - [_callApproval(approvals)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L187)
                - [IPermitBorrow(approvals[i].target).permitBorrow(approvals[i].owner,approvals[i].spender,approvals[i].value,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L263-L277)
                - [IPermitAll(approvals[i].target).permitAll(approvals[i].owner,approvals[i].spender,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L279-L292)
                - [IERC20Permit(approvals[i].target).permit(approvals[i].owner,approvals[i].spender,approvals[i].value,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L294-L308)
        State variables written after the call(s):
        - [approve(address(borrowParams.marketHelper),borrowParams.amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L191)
                - [_allowances[owner][spender] = amount](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L324)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L180-L202


 - [ ] ID-72
Reentrancy in [BaseTOFT._wrap(address,address,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L348-L361):
        External calls:
        - [IERC20(erc20).safeTransferFrom(_fromAddress,address(this),_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L359)
        State variables written after the call(s):
        - [_mint(_toAddress,_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L360)
                - [_balances[account] += amount](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L267)
        - [_mint(_toAddress,_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L360)
                - [_totalSupply += amount](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L264)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L348-L361


 - [ ] ID-73
Reentrancy in [BaseTOFTStrategyModule.strategyWithdraw(uint16,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L188-L235):
        External calls:
        - [_retrieveFromYieldBox(_assetId,_amount,_share,_from,address(this))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L206)
                - [yieldBox.withdraw(_assetId,_from,_to,_amount,_share)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L247)
        State variables written after the call(s):
        - [_debitFrom(address(this),lzEndpoint.getChainId(),LzLib.addressToBytes32(address(this)),_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L208-L213)
                - [_allowances[owner][spender] = amount](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L324)
        - [_debitFrom(address(this),lzEndpoint.getChainId(),LzLib.addressToBytes32(address(this)),_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L208-L213)
                - [_balances[account] = accountBalance - amount](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L293)
        - [_debitFrom(address(this),lzEndpoint.getChainId(),LzLib.addressToBytes32(address(this)),_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L208-L213)
                - [_totalSupply -= amount](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L295)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L188-L235


 - [ ] ID-74
Reentrancy in [BaseTOFT._executeOnDestination(BaseTOFT.Module,bytes,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L417-L439):
        External calls:
        - [(success,returnData) = _executeModule(_module,_data,true)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L425-L429)
                - [(success,returnData) = module.delegatecall(_data)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L411)
        State variables written after the call(s):
        - [_storeFailedMessage(_srcChainId,_srcAddress,_nonce,_payload,returnData)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L431-L437)
                - [failedMessages[_srcChainId][_srcAddress][_nonce] = keccak256(bytes)(_payload)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L33)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L417-L439


## reentrancy-events
Impact: Low
Confidence: Medium
 - [ ] ID-75
Reentrancy in [BaseTOFTStrategyModule.strategyDeposit(address,uint16,bytes,uint64,bytes,IERC20)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L122-L171):
        External calls:
        - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.depositToYieldbox.selector,assetId,amount,share,_erc20,address(this),onBehalfOf))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L152-L162)
        - [IERC20(address(this)).safeTransfer(onBehalfOf,amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L165)
        Event emitted after the call(s):
        - [ReceiveFromChain(_srcChainId,onBehalfOf,amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L170)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L122-L171


 - [ ] ID-76
Reentrancy in [BaseTOFTLeverageModule.initMultiSell(address,uint256,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageExternalContractsData,bytes,ICommonData.IApproval[])](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L45-L77):
        External calls:
        - [_lzSend(lzData.lzSrcChainId,lzPayload,address(lzData.refundAddress),lzData.zroPaymentAddress,airdropAdapterParams,msg.value)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L68-L75)
                - [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
        Event emitted after the call(s):
        - [SendToChain(lzData.lzSrcChainId,msg.sender,senderBytes,0)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L76)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L45-L77


 - [ ] ID-77
Reentrancy in [BaseTOFTOptionsModule.exerciseOption(ITapiocaOptionsBrokerCrossChain.IExerciseOptionsData,ITapiocaOptionsBrokerCrossChain.IExerciseLZData,ITapiocaOptionsBrokerCrossChain.IExerciseLZSendTapData,ICommonData.IApproval[])](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L73-L116):
        External calls:
        - [_lzSend(lzData.lzDstChainId,lzPayload,address(optionsData.from),lzData.zroPaymentAddress,adapterParams,msg.value)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L101-L108)
                - [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
        Event emitted after the call(s):
        - [SendToChain(lzData.lzDstChainId,optionsData.from,toAddress,optionsData.paymentTokenAmount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L110-L115)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L73-L116


 - [ ] ID-78
Reentrancy in [BaseTOFTStrategyModule.sendToStrategy(address,address,uint256,uint256,uint256,uint16,ICommonData.ISendOptions)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L47-L80):
        External calls:
        - [_lzSend(lzDstChainId,lzPayload,address(_from),options.zroPaymentAddress,LzLib.buildDefaultAdapterParams(options.extraGasLimit),msg.value)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L70-L77)
                - [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
        Event emitted after the call(s):
        - [SendToChain(lzDstChainId,_from,toAddress,amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L79)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L47-L80


 - [ ] ID-79
Reentrancy in [OFTCoreV2._send(address,uint16,bytes32,uint256,address,address,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L94-L105):
        External calls:
        - [_lzSend(_dstChainId,lzPayload,_refundAddress,_zroPaymentAddress,_adapterParams,msg.value)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L102)
                - [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
        Event emitted after the call(s):
        - [SendToChain(_dstChainId,_from,_toAddress,amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L104)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L94-L105


 - [ ] ID-80
Reentrancy in [BaseTOFTMarketModule.remove(bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L204-L258):
        External calls:
        - [_callApproval(approvals)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L227)
                - [IPermitBorrow(approvals[i].target).permitBorrow(approvals[i].owner,approvals[i].spender,approvals[i].value,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L263-L277)
                - [IPermitAll(approvals[i].target).permitAll(approvals[i].owner,approvals[i].spender,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L279-L292)
                - [IERC20Permit(approvals[i].target).permit(approvals[i].owner,approvals[i].spender,approvals[i].value,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L294-L308)
        Event emitted after the call(s):
        - [Approval(owner,spender,amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L325)
                - [approve(removeParams.market,removeParams.share)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L230)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L204-L258


 - [ ] ID-81
Reentrancy in [BaseTOFTMarketModule.sendToYBAndBorrow(address,address,uint16,bytes,ITapiocaOFT.IBorrowParams,ICommonData.IWithdrawParams,ICommonData.ISendOptions,ICommonData.IApproval[])](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L87-L124):
        External calls:
        - [_lzSend(lzDstChainId,lzPayload,address(_from),options.zroPaymentAddress,airdropAdapterParams,msg.value)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L114-L121)
                - [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
        Event emitted after the call(s):
        - [SendToChain(lzDstChainId,_from,toAddress,borrowParams.amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L123)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L87-L124


 - [ ] ID-82
Reentrancy in [BaseTOFTMarketModule.borrow(address,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L126-L178):
        External calls:
        - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.borrowInternal.selector,_to,borrowParams,withdrawParams,approvals))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L160-L168)
        - [IERC20(address(this)).safeTransfer(_from,borrowParams.amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L172)
        Event emitted after the call(s):
        - [ReceiveFromChain(_srcChainId,_from,borrowParams.amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L177)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L126-L178


 - [ ] ID-83
Reentrancy in [BaseTOFTOptionsModule.exercise(address,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L153-L219):
        External calls:
        - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.exerciseInternal.selector,optionsData.from,optionsData.oTAPTokenID,optionsData.paymentToken,optionsData.tapAmount,optionsData.target,tapSendData,approvals))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L189-L200)
        - [IERC20(address(this)).safeTransfer(optionsData.from,optionsData.paymentTokenAmount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L206-L209)
        Event emitted after the call(s):
        - [ReceiveFromChain(_srcChainId,optionsData.from,optionsData.paymentTokenAmount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L214-L218)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L153-L219


 - [ ] ID-84
Reentrancy in [mTapiocaOFT.extractUnderlying(uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L141-L152):
        External calls:
        - [_safeTransferETH(msg.sender,_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L146)
                - [(sent) = to.call{value: amount}()](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L380)
        - [IERC20(erc20).safeTransfer(msg.sender,_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L148)
        External calls sending eth:
        - [_safeTransferETH(msg.sender,_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L146)
                - [(sent) = to.call{value: amount}()](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L380)
        Event emitted after the call(s):
        - [Rebalancing(msg.sender,_amount,_isNative)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L151)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L141-L152


 - [ ] ID-85
Reentrancy in [BaseTOFTStrategyModule.strategyWithdraw(uint16,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L188-L235):
        External calls:
        - [_retrieveFromYieldBox(_assetId,_amount,_share,_from,address(this))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L206)
                - [yieldBox.withdraw(_assetId,_from,_to,_amount,_share)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L247)
        - [_lzSend(_srcChainId,lzSendBackPayload,address(this),_zroPaymentAddress,,address(this).balance)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L219-L226)
                - [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
        External calls sending eth:
        - [_lzSend(_srcChainId,lzSendBackPayload,address(this),_zroPaymentAddress,,address(this).balance)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L219-L226)
                - [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
        Event emitted after the call(s):
        - [ReceiveFromChain(_srcChainId,_from,_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L234)
        - [SendToChain(_srcChainId,_from,LzLib.addressToBytes32(address(this)),_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L227-L232)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L188-L235


 - [ ] ID-86
Reentrancy in [BaseTOFTOptionsModule.triggerSendFrom(uint16,bytes,address,uint256,ISendFrom.LzCallParams,ICommonData.IApproval[])](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L39-L71):
        External calls:
        - [_lzSend(lzDstChainId,lzPayload,address(msg.sender),zroPaymentAddress,airdropAdapterParams,msg.value)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L56-L63)
                - [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
        Event emitted after the call(s):
        - [SendToChain(lzDstChainId,msg.sender,LzLib.addressToBytes32(msg.sender),0)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L65-L70)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L39-L71


 - [ ] ID-87
Reentrancy in [TapiocaWrapper.harvestFees()](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L97-L102):
        External calls:
        - [harvestableTapiocaOFTs[i].harvestFees()](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L99)
        Event emitted after the call(s):
        - [HarvestFees(msg.sender)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L101)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L97-L102


 - [ ] ID-88
Reentrancy in [BaseTOFTMarketModule.borrowInternal(bytes32,ITapiocaOFT.IBorrowParams,ICommonData.IWithdrawParams,ICommonData.IApproval[])](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L180-L202):
        External calls:
        - [_callApproval(approvals)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L187)
                - [IPermitBorrow(approvals[i].target).permitBorrow(approvals[i].owner,approvals[i].spender,approvals[i].value,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L263-L277)
                - [IPermitAll(approvals[i].target).permitAll(approvals[i].owner,approvals[i].spender,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L279-L292)
                - [IERC20Permit(approvals[i].target).permit(approvals[i].owner,approvals[i].spender,approvals[i].value,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L294-L308)
        Event emitted after the call(s):
        - [Approval(owner,spender,amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L325)
                - [approve(address(borrowParams.marketHelper),borrowParams.amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L191)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L180-L202


 - [ ] ID-89
Reentrancy in [BaseTOFT._executeOnDestination(BaseTOFT.Module,bytes,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L417-L439):
        External calls:
        - [(success,returnData) = _executeModule(_module,_data,true)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L425-L429)
                - [(success,returnData) = module.delegatecall(_data)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L411)
        Event emitted after the call(s):
        - [MessageFailed(_srcChainId,_srcAddress,_nonce,_payload,_reason)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L34)
                - [_storeFailedMessage(_srcChainId,_srcAddress,_nonce,_payload,returnData)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L431-L437)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L417-L439


 - [ ] ID-90
Reentrancy in [BaseTOFTLeverageModule.leverageDown(address,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L148-L203):
        External calls:
        - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.leverageDownInternal.selector,amount,swapData,externalData,lzData,leverageFor))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L184-L193)
        - [IERC20(address(this)).safeTransfer(leverageFor,amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L197)
        Event emitted after the call(s):
        - [ReceiveFromChain(_srcChainId,leverageFor,amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L202)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L148-L203


 - [ ] ID-91
Reentrancy in [BaseTOFT._wrap(address,address,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L348-L361):
        External calls:
        - [IERC20(erc20).safeTransferFrom(_fromAddress,address(this),_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L359)
        Event emitted after the call(s):
        - [Transfer(address(0),account,amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L269)
                - [_mint(_toAddress,_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L360)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L348-L361


 - [ ] ID-92
Reentrancy in [BaseTOFTLeverageModule.sendForLeverage(uint256,address,IUSDOBase.ILeverageLZData,IUSDOBase.ILeverageSwapData,IUSDOBase.ILeverageExternalContractsData)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L79-L108):
        External calls:
        - [_lzSend(lzData.lzDstChainId,lzPayload,address(lzData.refundAddress),lzData.zroPaymentAddress,lzData.dstAirdropAdapterParam,msg.value)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L99-L106)
                - [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
        Event emitted after the call(s):
        - [SendToChain(lzData.lzDstChainId,msg.sender,senderBytes,amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L107)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L79-L108


 - [ ] ID-93
Reentrancy in [BaseTOFTOptionsModule.sendFromDestination(bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L118-L151):
        External calls:
        - [_callApproval(approvals)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L139)
                - [IPermitBorrow(approvals[i].target).permitBorrow(approvals[i].owner,approvals[i].spender,approvals[i].value,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L262-L276)
                - [IPermitAll(approvals[i].target).permitAll(approvals[i].owner,approvals[i].spender,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L278-L291)
                - [IERC20Permit(approvals[i].target).permit(approvals[i].owner,approvals[i].spender,approvals[i].value,approvals[i].deadline,approvals[i].v,approvals[i].r,approvals[i].s)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L293-L307)
        - [ISendFrom(address(this)).sendFrom{value: address(this).balance}(from,lzDstChainId,LzLib.addressToBytes32(from),amount,callParams)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L142-L148)
        External calls sending eth:
        - [ISendFrom(address(this)).sendFrom{value: address(this).balance}(from,lzDstChainId,LzLib.addressToBytes32(from),amount,callParams)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L142-L148)
        Event emitted after the call(s):
        - [ReceiveFromChain(lzDstChainId,from,0)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L150)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L118-L151


 - [ ] ID-94
Reentrancy in [OFTCoreV2._sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,address,address,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L119-L131):
        External calls:
        - [_lzSend(_dstChainId,lzPayload,_refundAddress,_zroPaymentAddress,_adapterParams,msg.value)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L128)
                - [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
        Event emitted after the call(s):
        - [SendToChain(_dstChainId,_from,_toAddress,amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L130)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L119-L131


 - [ ] ID-95
Reentrancy in [BaseTOFTMarketModule.removeCollateral(address,address,uint16,address,ICommonData.IWithdrawParams,ITapiocaOFT.IRemoveParams,ICommonData.IApproval[],bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L44-L76):
        External calls:
        - [_lzSend(lzDstChainId,lzPayload,address(from),zroPaymentAddress,adapterParams,msg.value)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L66-L73)
                - [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
        Event emitted after the call(s):
        - [SendToChain(lzDstChainId,from,toAddress,0)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L75)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L44-L76


 - [ ] ID-96
Reentrancy in [BaseTOFTStrategyModule.retrieveFromStrategy(address,uint256,uint256,uint256,uint16,address,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L89-L120):
        External calls:
        - [_lzSend(lzDstChainId,lzPayload,address(msg.sender),zroPaymentAddress,airdropAdapterParam,msg.value)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L111-L118)
                - [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
        Event emitted after the call(s):
        - [SendToChain(lzDstChainId,msg.sender,toAddress,amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L119)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L89-L120


 - [ ] ID-97
Reentrancy in [BaseTOFTStrategyModule.strategyWithdraw(uint16,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L188-L235):
        External calls:
        - [_retrieveFromYieldBox(_assetId,_amount,_share,_from,address(this))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L206)
                - [yieldBox.withdraw(_assetId,_from,_to,_amount,_share)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L247)
        Event emitted after the call(s):
        - [Approval(owner,spender,amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L325)
                - [_debitFrom(address(this),lzEndpoint.getChainId(),LzLib.addressToBytes32(address(this)),_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L208-L213)
        - [Transfer(account,address(0),amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L298)
                - [_debitFrom(address(this),lzEndpoint.getChainId(),LzLib.addressToBytes32(address(this)),_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L208-L213)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L188-L235


 - [ ] ID-98
Reentrancy in [Balancer.rebalance(address,uint16,uint256,uint256,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L172-L212):
        External calls:
        - [ITapiocaOFT(_srcOft).extractUnderlying(_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L198)
        - [_sendNative(_srcOft,_amount,_dstChainId,_slippage)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L204)
                - [routerETH.swapETH(_dstChainId,_oft,abi.encodePacked(connectedOFTs[_oft][_dstChainId].dstOft),_amount,_computeMinAmount(_amount,_slippage))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L288-L294)
        - [_sendToken(_srcOft,_amount,_dstChainId,_slippage,_ercData)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L207)
                - [erc20.approve(address(router),_amount)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L321)
                - [router.swap(_dstChainId,_srcPoolId,_dstPoolId,_oft,_amount,_computeMinAmount(_amount,_slippage),_lzTxParams,_lzTxParams.dstNativeAddr,0x)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L322-L332)
        Event emitted after the call(s):
        - [Rebalanced(_srcOft,_dstChainId,_slippage,_amount,_isNative)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L211)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L172-L212


## timestamp
Impact: Low
Confidence: Medium
 - [ ] ID-99
[ERC20Permit.permit(address,address,uint256,uint256,uint8,bytes32,bytes32)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L49-L68) uses timestamp for comparisons
        Dangerous comparisons:
        - [require(bool,string)(block.timestamp <= deadline,ERC20Permit: expired deadline)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L58)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L49-L68


## assembly
Impact: Informational
Confidence: High
 - [ ] ID-100
[BytesLib.toUint8(bytes,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L308-L317) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L312-L314)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L308-L317


 - [ ] ID-101
[BytesLib.concat(bytes,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L13-L89) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L23-L86)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L13-L89


 - [ ] ID-102
[BytesLib.toUint16(bytes,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L319-L328) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L323-L325)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L319-L328


 - [ ] ID-103
[ExcessivelySafeCall.excessivelySafeCall(address,uint256,uint16,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L23-L58) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L37-L56)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L23-L58


 - [ ] ID-104
[LzLib.getGasLimit(bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L47-L52) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L49-L51)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L47-L52


 - [ ] ID-105
[ECDSA.tryRecover(bytes32,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L55-L72) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L63-L67)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L55-L72


 - [ ] ID-106
[BytesLib.toUint96(bytes,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L352-L361) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L356-L358)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L352-L361


 - [ ] ID-107
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L66-L70)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L86-L93)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L100-L109)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-108
[Create2.deploy(uint256,bytes32,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Create2.sol#L30-L42) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Create2.sol#L38-L40)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Create2.sol#L30-L42


 - [ ] ID-109
[BytesLib.equalStorage(bytes,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L439-L509) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L449-L506)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L439-L509


 - [ ] ID-110
[BytesLib.toUint32(bytes,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L330-L339) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L334-L336)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L330-L339


 - [ ] ID-111
[BytesLib.toBytes32(bytes,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L385-L394) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L389-L391)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L385-L394


 - [ ] ID-112
[Strings.toString(uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L18-L38) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L24-L26)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L30-L32)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L18-L38


 - [ ] ID-113
[LzApp._getGasLimit(bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L63-L68) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L65-L67)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L63-L68


 - [ ] ID-114
[BytesLib.concatStorage(bytes,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L92-L225)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226


 - [ ] ID-115
[ExcessivelySafeCall.excessivelySafeStaticCall(address,uint256,uint16,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L75-L109) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L89-L107)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L75-L109


 - [ ] ID-116
[Create2.computeAddress(bytes32,bytes32,address)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Create2.sol#L56-L82) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Create2.sol#L62-L81)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Create2.sol#L56-L82


 - [ ] ID-117
[BaseTOFTStorage._getRevertMsg(bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L67-L78) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L73-L76)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L67-L78


 - [ ] ID-118
[BytesLib.toAddress(bytes,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297-L306) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L301-L303)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297-L306


 - [ ] ID-119
[Address._revert(bytes,string)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L231-L243) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L236-L239)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L231-L243


 - [ ] ID-120
[BytesLib.toUint128(bytes,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L363-L372) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L367-L369)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L363-L372


 - [ ] ID-121
[BytesLib.toUint256(bytes,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L374-L383) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L378-L380)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L374-L383


 - [ ] ID-122
[BytesLib.toUint64(bytes,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L341-L350) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L345-L347)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L341-L350


 - [ ] ID-123
[BytesLib.slice(bytes,uint256,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L228-L295) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L242-L292)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L228-L295


 - [ ] ID-124
[BytesLib.equal(bytes,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L396-L437) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L399-L434)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L396-L437


 - [ ] ID-125
[ExcessivelySafeCall.swapSelector(bytes4,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L120-L135) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L126-L134)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L120-L135


 - [ ] ID-126
[LzLib.decodeAdapterParams(bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L55-L70) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L57-L60)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L65-L68)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L55-L70


## pragma
Impact: Informational
Confidence: High
 - [ ] ID-127
Different versions of Solidity are used:
        - Version used: ['>=0.5.0', '>=0.6.0', '>=0.7.6', '>=0.8.0', '>=0.8.0<0.9.0', '^0.8.0', '^0.8.1', '^0.8.18', '^0.8.9']
        - [>=0.5.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroEndpoint.sol#L3)
        - [>=0.5.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroReceiver.sol#L3)
        - [>=0.5.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroUserApplicationConfig.sol#L3)
        - [>=0.5.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/ICommonOFT.sol#L3)
        - [>=0.5.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/IOFTReceiverV2.sol#L3)
        - [>=0.5.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/IOFTV2.sol#L3)
        - [>=0.6.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L3)
        - [>=0.7.6](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L2)
        - [>=0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@rari-capital/solmate/src/auth/Owned.sol#L2)
        - [>=0.8.0<0.9.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L9)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/access/Ownable.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Context.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Counters.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Create2.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/introspection/ERC165.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/introspection/IERC165.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L3)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L3)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L3)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L3)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L3)
        - [^0.8.1](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L4)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/TapiocaOFT.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/tapioca-periph/contracts/interfaces/ICommonData.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/tapioca-periph/contracts/interfaces/IMagnetar.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/tapioca-periph/contracts/interfaces/IMarket.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/tapioca-periph/contracts/interfaces/IPermitAll.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/tapioca-periph/contracts/interfaces/IPermitBorrow.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/tapioca-periph/contracts/interfaces/ISendFrom.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/tapioca-periph/contracts/interfaces/ISingularity.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/tapioca-periph/contracts/interfaces/IStargateRouter.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/tapioca-periph/contracts/interfaces/ISwapper.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/tapioca-periph/contracts/interfaces/ITapiocaOFT.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/tapioca-periph/contracts/interfaces/ITapiocaOptionLiquidityProvision.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/tapioca-periph/contracts/interfaces/ITapiocaOptionsBroker.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/tapioca-periph/contracts/interfaces/IUSDO.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/tapioca-periph/contracts/interfaces/IYieldBoxBase.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/enums/YieldBoxTokenType.sol#L2)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroEndpoint.sol#L3


## cyclomatic-complexity
Impact: Informational
Confidence: High
 - [ ] ID-128
[BaseTOFTOptionsModule._callApproval(ICommonData.IApproval[])](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L259-L314) has a high cyclomatic complexity (13).

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L259-L314


 - [ ] ID-129
[BaseTOFTMarketModule._callApproval(ICommonData.IApproval[])](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L260-L315) has a high cyclomatic complexity (13).

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L260-L315


 - [ ] ID-130
[BaseTOFTLeverageModule._callApproval(ICommonData.IApproval[])](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L284-L339) has a high cyclomatic complexity (13).

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L284-L339


## solc-version
Impact: Informational
Confidence: High
 - [ ] ID-131
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L4


 - [ ] ID-132
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L4


 - [ ] ID-133
Pragma version[>=0.6.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L3


 - [ ] ID-134
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L4


 - [ ] ID-135
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L4


 - [ ] ID-136
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol#L4


 - [ ] ID-137
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Context.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Context.sol#L4


 - [ ] ID-138
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L4


 - [ ] ID-139
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L3


 - [ ] ID-140
Pragma version[>=0.7.6](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L2


 - [ ] ID-141
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L4


 - [ ] ID-142
Pragma version[>=0.5.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroUserApplicationConfig.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroUserApplicationConfig.sol#L3


 - [ ] ID-143
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L4


 - [ ] ID-144
Pragma version[^0.8.1](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L4


 - [ ] ID-145
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L3


 - [ ] ID-146
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L3


 - [ ] ID-147
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L3


 - [ ] ID-148
Pragma version[>=0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@rari-capital/solmate/src/auth/Owned.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@rari-capital/solmate/src/auth/Owned.sol#L2


 - [ ] ID-149
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Counters.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Counters.sol#L4


 - [ ] ID-150
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol#L4


 - [ ] ID-151
Pragma version[>=0.8.0<0.9.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L9) is too complex

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L9


 - [ ] ID-152
Pragma version[>=0.5.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroReceiver.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroReceiver.sol#L3


 - [ ] ID-153
Pragma version[>=0.5.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroEndpoint.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroEndpoint.sol#L3


 - [ ] ID-154
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/introspection/ERC165.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/introspection/ERC165.sol#L4


 - [ ] ID-155
Pragma version[>=0.5.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/ICommonOFT.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/ICommonOFT.sol#L3


 - [ ] ID-156
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L4


 - [ ] ID-157
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Create2.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Create2.sol#L4


 - [ ] ID-158
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L3


 - [ ] ID-159
Pragma version[>=0.5.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/IOFTReceiverV2.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/IOFTReceiverV2.sol#L3


 - [ ] ID-160
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/access/Ownable.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/access/Ownable.sol#L4


 - [ ] ID-161
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/introspection/IERC165.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/introspection/IERC165.sol#L4


 - [ ] ID-162
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/enums/YieldBoxTokenType.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/enums/YieldBoxTokenType.sol#L2


 - [ ] ID-163
Pragma version[>=0.5.0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/IOFTV2.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/IOFTV2.sol#L3


## low-level-calls
Impact: Informational
Confidence: High
 - [ ] ID-164
Low level call in [TapiocaWrapper.executeTOFT(address,bytes,bool)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L115-L124):
        - [(success,result) = address(_toft).call{value: msg.value}(_bytecode)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L120)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L115-L124


 - [ ] ID-165
Low level call in [Address.functionCallWithValue(address,bytes,uint256,string)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L128-L137):
        - [(success,returndata) = target.call{value: value}(data)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L135)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L128-L137


 - [ ] ID-166
Low level call in [BaseTOFTLeverageModule.leverageDown(address,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L148-L203):
        - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.leverageDownInternal.selector,amount,swapData,externalData,lzData,leverageFor))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L184-L193)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L148-L203


 - [ ] ID-167
Low level call in [BaseTOFT._safeTransferETH(address,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L379-L382):
        - [(sent) = to.call{value: amount}()](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L380)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L379-L382


 - [ ] ID-168
Low level call in [BaseTOFTMarketModule.borrow(address,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L126-L178):
        - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.borrowInternal.selector,_to,borrowParams,withdrawParams,approvals))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L160-L168)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L126-L178


 - [ ] ID-169
Low level call in [BaseTOFT._executeModule(BaseTOFT.Module,bytes,bool)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L403-L415):
        - [(success,returnData) = module.delegatecall(_data)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L411)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L403-L415


 - [ ] ID-170
Low level call in [Address.sendValue(address,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L60-L65):
        - [(success) = recipient.call{value: amount}()](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L63)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L60-L65


 - [ ] ID-171
Low level call in [BaseTOFTStrategyModule.strategyDeposit(address,uint16,bytes,uint64,bytes,IERC20)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L122-L171):
        - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.depositToYieldbox.selector,assetId,amount,share,_erc20,address(this),onBehalfOf))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L152-L162)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L122-L171


 - [ ] ID-172
Low level call in [TapiocaWrapper.executeCalls(TapiocaWrapper.ExecutionCall[])](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L131-L148):
        - [(success,results[i]) = address(_call[i].toft).call{value: msg.value}(_call[i].bytecode)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L141-L143)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L131-L148


 - [ ] ID-173
Low level call in [BaseTOFTLeverageModule._safeTransferETH(address,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L279-L282):
        - [(sent) = to.call{value: amount}()](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L280)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L279-L282


 - [ ] ID-174
Low level call in [Address.functionStaticCall(address,bytes,string)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L155-L162):
        - [(success,returndata) = target.staticcall(data)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L160)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L155-L162


 - [ ] ID-175
Low level call in [Address.functionDelegateCall(address,bytes,string)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L180-L187):
        - [(success,returndata) = target.delegatecall(data)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L185)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L180-L187


 - [ ] ID-176
Low level call in [BaseTOFTOptionsModule.exercise(address,uint16,bytes,uint64,bytes)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L153-L219):
        - [(success,reason) = module.delegatecall(abi.encodeWithSelector(this.exerciseInternal.selector,optionsData.from,optionsData.oTAPTokenID,optionsData.paymentToken,optionsData.tapAmount,optionsData.target,tapSendData,approvals))](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L189-L200)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L153-L219


## missing-inheritance
Impact: Informational
Confidence: High
 - [ ] ID-177
[BaseTOFTOptionsModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L16-L315) should inherit from [ITapiocaOptionsBrokerCrossChain](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/tapioca-periph/contracts/interfaces/ITapiocaOptionsBroker.sol#L7-L36)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L16-L315


## naming-convention
Impact: Informational
Confidence: High
 - [ ] ID-178
Parameter [BaseOFTV2.estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)._dstGasForCall](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36


 - [ ] ID-179
Parameter [TapiocaWrapper.createTOFT(address,bytes,bytes32,bool)._linked](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L158) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L158


 - [ ] ID-180
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._srcChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-181
Parameter [BaseOFTV2.sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,ICommonOFT.LzCallParams)._dstGasForCall](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21


 - [ ] ID-182
Parameter [BytesLib.equalStorage(bytes,bytes)._preBytes](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L440) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L440


 - [ ] ID-183
Parameter [BaseTOFTStrategyModule.depositToYieldbox(uint256,uint256,uint256,IERC20,address,address)._to](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L179) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L179


 - [ ] ID-184
Parameter [Balancer.initConnectedOFT(address,uint16,address,bytes)._dstOft](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L222) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L222


 - [ ] ID-185
Parameter [LzApp.setConfig(uint16,uint16,uint256,bytes)._version](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84


 - [ ] ID-186
Parameter [BaseTOFTStrategyModule.strategyWithdraw(uint16,bytes)._payload](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L190) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L190


 - [ ] ID-187
Parameter [ExcessivelySafeCall.swapSelector(bytes4,bytes)._newSelector](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L120) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L120


 - [ ] ID-188
Parameter [BytesLib.concatStorage(bytes,bytes)._postBytes](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91


 - [ ] ID-189
Parameter [LzApp.setTrustedRemoteAddress(uint16,bytes)._remoteChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L107) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L107


 - [ ] ID-190
Parameter [ExcessivelySafeCall.swapSelector(bytes4,bytes)._buf](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L120) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L120


 - [ ] ID-191
Parameter [Balancer.rebalance(address,uint16,uint256,uint256,bytes)._dstChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L174) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L174


 - [ ] ID-192
Variable [BaseTOFTStorage._decimalCache](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L32) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L32


 - [ ] ID-193
Parameter [BytesLib.toUint128(bytes,uint256)._start](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L363) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L363


 - [ ] ID-194
Parameter [BytesLib.equal(bytes,bytes)._preBytes](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L396) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L396


 - [ ] ID-195
Parameter [BytesLib.equalStorage(bytes,bytes)._postBytes](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L441) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L441


 - [ ] ID-196
Parameter [BaseOFTV2.sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,ICommonOFT.LzCallParams)._amount](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21


 - [ ] ID-197
Parameter [BytesLib.toUint64(bytes,uint256)._bytes](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L341) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L341


 - [ ] ID-198
Parameter [BytesLib.toBytes32(bytes,uint256)._bytes](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L385) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L385


 - [ ] ID-199
Parameter [LzApp.setTrustedRemote(uint16,bytes)._path](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L102) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L102


 - [ ] ID-200
Parameter [BaseTOFTLeverageModule.leverageDown(address,uint16,bytes,uint64,bytes)._nonce](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L152) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L152


 - [ ] ID-201
Parameter [BaseOFTV2.sendFrom(address,uint16,bytes32,uint256,ICommonOFT.LzCallParams)._callParams](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17


 - [ ] ID-202
Parameter [LzApp.isTrustedRemote(uint16,bytes)._srcAddress](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L135) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L135


 - [ ] ID-203
Parameter [Balancer.checker(address,uint16)._dstChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L139) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L139


 - [ ] ID-204
Parameter [LzLib.buildAdapterParams(LzLib.AirdropParams,uint256)._airdropParams](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L21) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L21


 - [ ] ID-205
Parameter [mTapiocaOFT.updateConnectedChain(uint256,bool)._status](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L118) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L118


 - [ ] ID-206
Parameter [BaseTOFTStrategyModule.strategyDeposit(address,uint16,bytes,uint64,bytes,IERC20)._srcAddress](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L125) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L125


 - [ ] ID-207
Parameter [BytesLib.toAddress(bytes,uint256)._start](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297


 - [ ] ID-208
Parameter [LzApp.setConfig(uint16,uint16,uint256,bytes)._chainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84


 - [ ] ID-209
Parameter [mTapiocaOFT.unwrap(address,uint256)._toAddress](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L104) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L104


 - [ ] ID-210
Parameter [BytesLib.toUint8(bytes,uint256)._start](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L308) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L308


 - [ ] ID-211
Parameter [LzApp.forceResumeReceive(uint16,bytes)._srcAddress](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L96) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L96


 - [ ] ID-212
Parameter [NonblockingLzApp.retryMessage(uint16,bytes,uint64,bytes)._nonce](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46


 - [ ] ID-213
Parameter [BytesLib.toUint8(bytes,uint256)._bytes](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L308) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L308


 - [ ] ID-214
Parameter [ExcessivelySafeCall.excessivelySafeStaticCall(address,uint256,uint16,bytes)._calldata](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L79) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L79


 - [ ] ID-215
Parameter [BytesLib.toBytes32(bytes,uint256)._start](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L385) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L385


 - [ ] ID-216
Parameter [BaseOFTV2.estimateSendFee(uint16,bytes32,uint256,bool,bytes)._adapterParams](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32


 - [ ] ID-217
Parameter [ExcessivelySafeCall.excessivelySafeCall(address,uint256,uint16,bytes)._maxCopy](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L26) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L26


 - [ ] ID-218
Parameter [BytesLib.toAddress(bytes,uint256)._bytes](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297


 - [ ] ID-219
Parameter [LzApp.setReceiveVersion(uint16)._version](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L92) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L92


 - [ ] ID-220
Parameter [mTapiocaOFT.updateBalancerState(address,bool)._status](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L133) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L133


 - [ ] ID-221
Parameter [BaseOFTV2.estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)._amount](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36


 - [ ] ID-222
Parameter [BaseOFTV2.sendFrom(address,uint16,bytes32,uint256,ICommonOFT.LzCallParams)._toAddress](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17


 - [ ] ID-223
Parameter [BaseOFTV2.sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,ICommonOFT.LzCallParams)._payload](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21


 - [ ] ID-224
Parameter [LzApp.lzReceive(uint16,bytes,uint64,bytes)._srcChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35


 - [ ] ID-225
Parameter [ExcessivelySafeCall.excessivelySafeCall(address,uint256,uint16,bytes)._calldata](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L27) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L27


 - [ ] ID-226
Parameter [Balancer.checker(address,uint16)._srcOft](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L138) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L138


 - [ ] ID-227
Parameter [BytesLib.toUint128(bytes,uint256)._bytes](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L363) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L363


 - [ ] ID-228
Parameter [BaseTOFTStrategyModule.depositToYieldbox(uint256,uint256,uint256,IERC20,address,address)._erc20](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L177) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L177


 - [ ] ID-229
Parameter [LzLib.decodeAdapterParams(bytes)._adapterParams](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L55) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L55


 - [ ] ID-230
Parameter [TapiocaWrapper.executeTOFT(address,bytes,bool)._bytecode](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L117) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L117


 - [ ] ID-231
Parameter [OFTCoreV2.setUseCustomAdapterParams(bool)._useCustomAdapterParams](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L62) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L62


 - [ ] ID-232
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._srcAddress](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-233
Parameter [Balancer.initConnectedOFT(address,uint16,address,bytes)._dstChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L221) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L221


 - [ ] ID-234
Parameter [BaseOFTV2.sendFrom(address,uint16,bytes32,uint256,ICommonOFT.LzCallParams)._dstChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17


 - [ ] ID-235
Parameter [BaseTOFTLeverageModule.multiHop(bytes)._payload](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L111) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L111


 - [ ] ID-236
Parameter [BytesLib.toUint32(bytes,uint256)._bytes](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L330) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L330


 - [ ] ID-237
Parameter [mTapiocaOFT.wrap(address,address,uint256)._toAddress](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L90) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L90


 - [ ] ID-238
Parameter [BaseOFTV2.estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)._toAddress](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36


 - [ ] ID-239
Parameter [BaseTOFTMarketModule.borrow(address,uint16,bytes,uint64,bytes)._payload](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L131) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L131


 - [ ] ID-240
Parameter [BaseOFTV2.estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)._dstChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36


 - [ ] ID-241
Parameter [mTapiocaOFT.updateBalancerState(address,bool)._balancer](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L132) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L132


 - [ ] ID-242
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._nonce](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-243
Parameter [BaseTOFTStrategyModule.depositToYieldbox(uint256,uint256,uint256,IERC20,address,address)._share](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L176) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L176


 - [ ] ID-244
Parameter [NonblockingLzApp.retryMessage(uint16,bytes,uint64,bytes)._payload](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46


 - [ ] ID-245
Parameter [NonblockingLzApp.nonblockingLzReceive(uint16,bytes,uint64,bytes)._payload](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37


 - [ ] ID-246
Parameter [TapiocaWrapper.executeTOFT(address,bytes,bool)._revertOnFailure](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L118) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L118


 - [ ] ID-247
Parameter [LzApp.setTrustedRemote(uint16,bytes)._srcChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L102) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L102


 - [ ] ID-248
Parameter [mTapiocaOFT.updateConnectedChain(uint256,bool)._chain](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L117) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L117


 - [ ] ID-249
Parameter [BytesLib.equal(bytes,bytes)._postBytes](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L396) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L396


 - [ ] ID-250
Parameter [LzApp.setMinDstGas(uint16,uint16,uint256)._dstChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L123) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L123


 - [ ] ID-251
Parameter [BytesLib.toUint256(bytes,uint256)._start](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L374) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L374


 - [ ] ID-252
Contract [mTapiocaOFT](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L9-L153) is not in CapWords

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L9-L153


 - [ ] ID-253
Parameter [BaseTOFTMarketModule.sendToYBAndBorrow(address,address,uint16,bytes,ITapiocaOFT.IBorrowParams,ICommonData.IWithdrawParams,ICommonData.ISendOptions,ICommonData.IApproval[])._to](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L89) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L89


 - [ ] ID-254
Parameter [BaseOFTV2.sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,ICommonOFT.LzCallParams)._callParams](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21


 - [ ] ID-255
Parameter [BaseTOFTStrategyModule.sendToStrategy(address,address,uint256,uint256,uint256,uint16,ICommonData.ISendOptions)._from](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L48) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L48


 - [ ] ID-256
Parameter [LzApp.lzReceive(uint16,bytes,uint64,bytes)._payload](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35


 - [ ] ID-257
Parameter [BytesLib.toUint256(bytes,uint256)._bytes](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L374) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L374


 - [ ] ID-258
Parameter [BaseTOFTLeverageModule.leverageDown(address,uint16,bytes,uint64,bytes)._payload](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L153) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L153


 - [ ] ID-259
Parameter [LzApp.setMinDstGas(uint16,uint16,uint256)._packetType](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L123) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L123


 - [ ] ID-260
Parameter [LzApp.setTrustedRemoteAddress(uint16,bytes)._remoteAddress](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L107) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L107


 - [ ] ID-261
Parameter [LzLib.buildAirdropAdapterParams(uint256,LzLib.AirdropParams)._params](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L37) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L37


 - [ ] ID-262
Parameter [BaseTOFTOptionsModule.exercise(address,uint16,bytes,uint64,bytes)._nonce](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L157) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L157


 - [ ] ID-263
Parameter [BaseOFTV2.estimateSendFee(uint16,bytes32,uint256,bool,bytes)._toAddress](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32


 - [ ] ID-264
Parameter [TapiocaWrapper.createTOFT(address,bytes,bytes32,bool)._erc20](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L155) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L155


 - [ ] ID-265
Parameter [LzApp.getConfig(uint16,uint16,address,uint256)._version](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L79) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L79


 - [ ] ID-266
Variable [EIP712._TYPE_HASH](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L37) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L37


 - [ ] ID-267
Struct [IStargateRouterBase.lzTxObj](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/tapioca-periph/contracts/interfaces/IStargateRouter.sol#L6-L10) is not in CapWords

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/tapioca-periph/contracts/interfaces/IStargateRouter.sol#L6-L10


 - [ ] ID-268
Parameter [TapiocaWrapper.executeCalls(TapiocaWrapper.ExecutionCall[])._call](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L132) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L132


 - [ ] ID-269
Parameter [Balancer.rebalance(address,uint16,uint256,uint256,bytes)._ercData](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L177) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L177


 - [ ] ID-270
Parameter [BytesLib.concatStorage(bytes,bytes)._preBytes](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91


 - [ ] ID-271
Parameter [LzApp.lzReceive(uint16,bytes,uint64,bytes)._srcAddress](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35


 - [ ] ID-272
Parameter [TapiocaWrapper.createTOFT(address,bytes,bytes32,bool)._salt](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L157) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L157


 - [ ] ID-273
Parameter [BaseOFTV2.estimateSendFee(uint16,bytes32,uint256,bool,bytes)._amount](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32


 - [ ] ID-274
Parameter [BaseTOFTMarketModule.borrow(address,uint16,bytes,uint64,bytes)._nonce](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L130) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L130


 - [ ] ID-275
Parameter [LzApp.getConfig(uint16,uint16,address,uint256)._chainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L79) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L79


 - [ ] ID-276
Parameter [LzApp.setMinDstGas(uint16,uint16,uint256)._minGas](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L123) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L123


 - [ ] ID-277
Parameter [LzApp.isTrustedRemote(uint16,bytes)._srcChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L135) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L135


 - [ ] ID-278
Parameter [BytesLib.slice(bytes,uint256,uint256)._start](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L230) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L230


 - [ ] ID-279
Parameter [BaseTOFTStrategyModule.sendToStrategy(address,address,uint256,uint256,uint256,uint16,ICommonData.ISendOptions)._to](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L49) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L49


 - [ ] ID-280
Parameter [LzApp.forceResumeReceive(uint16,bytes)._srcChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L96) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L96


 - [ ] ID-281
Parameter [BaseTOFTLeverageModule.leverageDown(address,uint16,bytes,uint64,bytes)._srcAddress](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L151) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L151


 - [ ] ID-282
Parameter [BaseOFTV2.estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)._payload](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36


 - [ ] ID-283
Parameter [BytesLib.concat(bytes,bytes)._preBytes](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L14) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L14


 - [ ] ID-284
Parameter [LzLib.buildAirdropAdapterParams(uint256,LzLib.AirdropParams)._uaGas](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L37) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L37


 - [ ] ID-285
Parameter [ExcessivelySafeCall.excessivelySafeCall(address,uint256,uint16,bytes)._gas](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L25) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L25


 - [ ] ID-286
Variable [EIP712._CACHED_THIS](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L33) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L33


 - [ ] ID-287
Parameter [NonblockingLzApp.nonblockingLzReceive(uint16,bytes,uint64,bytes)._nonce](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37


 - [ ] ID-288
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._to](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-289
Parameter [ExcessivelySafeCall.excessivelySafeStaticCall(address,uint256,uint16,bytes)._maxCopy](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L78) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L78


 - [ ] ID-290
Parameter [BaseOFTV2.sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,ICommonOFT.LzCallParams)._toAddress](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21


 - [ ] ID-291
Parameter [LzLib.buildAdapterParams(LzLib.AirdropParams,uint256)._uaGasLimit](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L21) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L21


 - [ ] ID-292
Parameter [BaseOFTV2.sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,ICommonOFT.LzCallParams)._from](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21


 - [ ] ID-293
Parameter [BaseTOFTOptionsModule.exercise(address,uint16,bytes,uint64,bytes)._srcChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L155) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L155


 - [ ] ID-294
Parameter [mTapiocaOFT.wrap(address,address,uint256)._fromAddress](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L89) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L89


 - [ ] ID-295
Parameter [BaseTOFTStrategyModule.strategyDeposit(address,uint16,bytes,uint64,bytes,IERC20)._nonce](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L126) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L126


 - [ ] ID-296
Parameter [BaseTOFTMarketModule.sendToYBAndBorrow(address,address,uint16,bytes,ITapiocaOFT.IBorrowParams,ICommonData.IWithdrawParams,ICommonData.ISendOptions,ICommonData.IApproval[])._from](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L88) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L88


 - [ ] ID-297
Parameter [BytesLib.slice(bytes,uint256,uint256)._bytes](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L229) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L229


 - [ ] ID-298
Parameter [NonblockingLzApp.retryMessage(uint16,bytes,uint64,bytes)._srcAddress](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46


 - [ ] ID-299
Variable [ERC20Permit._PERMIT_TYPEHASH_DEPRECATED_SLOT](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L37) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L37


 - [ ] ID-300
Parameter [BaseTOFTStrategyModule.depositToYieldbox(uint256,uint256,uint256,IERC20,address,address)._from](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L178) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L178


 - [ ] ID-301
Function [IERC20Permit.DOMAIN_SEPARATOR()](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L59) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L59


 - [ ] ID-302
Parameter [Balancer.rebalance(address,uint16,uint256,uint256,bytes)._slippage](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L175) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L175


 - [ ] ID-303
Parameter [NonblockingLzApp.retryMessage(uint16,bytes,uint64,bytes)._srcChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46


 - [ ] ID-304
Parameter [BaseTOFTStrategyModule.strategyDeposit(address,uint16,bytes,uint64,bytes,IERC20)._erc20](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L128) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L128


 - [ ] ID-305
Parameter [Balancer.rebalance(address,uint16,uint256,uint256,bytes)._srcOft](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L173) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L173


 - [ ] ID-306
Parameter [TapiocaOFT.unwrap(address,uint256)._amount](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/TapiocaOFT.sol#L87) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/TapiocaOFT.sol#L87


 - [ ] ID-307
Parameter [ExcessivelySafeCall.excessivelySafeStaticCall(address,uint256,uint16,bytes)._gas](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L77) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L77


 - [ ] ID-308
Parameter [BaseOFTV2.estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)._adapterParams](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36


 - [ ] ID-309
Parameter [LzApp.setPayloadSizeLimit(uint16,uint256)._dstChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L130) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L130


 - [ ] ID-310
Parameter [LzLib.bytes32ToAddress(bytes32)._bytes32Address](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L74) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L74


 - [ ] ID-311
Parameter [OFTV2.setLdChain(uint16,bool)._isLdChain](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L36


 - [ ] ID-312
Parameter [BaseOFTV2.sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,ICommonOFT.LzCallParams)._dstChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21


 - [ ] ID-313
Parameter [BaseOFTV2.estimateSendFee(uint16,bytes32,uint256,bool,bytes)._useZro](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32


 - [ ] ID-314
Variable [EIP712._CACHED_CHAIN_ID](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L32) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L32


 - [ ] ID-315
Parameter [ExcessivelySafeCall.excessivelySafeCall(address,uint256,uint16,bytes)._target](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L24) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L24


 - [ ] ID-316
Parameter [BaseTOFTStrategyModule.depositToYieldbox(uint256,uint256,uint256,IERC20,address,address)._amount](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L175) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L175


 - [ ] ID-317
Parameter [BaseOFTV2.sendFrom(address,uint16,bytes32,uint256,ICommonOFT.LzCallParams)._amount](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17


 - [ ] ID-318
Function [ERC20Permit.DOMAIN_SEPARATOR()](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L81-L83) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L81-L83


 - [ ] ID-319
Parameter [BaseOFTV2.sendFrom(address,uint16,bytes32,uint256,ICommonOFT.LzCallParams)._from](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17


 - [ ] ID-320
Parameter [TapiocaWrapper.createTOFT(address,bytes,bytes32,bool)._bytecode](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L156) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L156


 - [ ] ID-321
Parameter [BaseTOFTStrategyModule.strategyWithdraw(uint16,bytes)._srcChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L189) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L189


 - [ ] ID-322
Parameter [BaseTOFTStrategyModule.retrieveFromStrategy(address,uint256,uint256,uint256,uint16,address,bytes)._from](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L90) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L90


 - [ ] ID-323
Parameter [BaseTOFTOptionsModule.sendFromDestination(bytes)._payload](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L118) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L118


 - [ ] ID-324
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._payload](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-325
Parameter [mTapiocaOFT.wrap(address,address,uint256)._amount](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L91) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L91


 - [ ] ID-326
Parameter [NonblockingLzApp.nonblockingLzReceive(uint16,bytes,uint64,bytes)._srcAddress](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37


 - [ ] ID-327
Parameter [BytesLib.toUint16(bytes,uint256)._start](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L319) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L319


 - [ ] ID-328
Parameter [Balancer.initConnectedOFT(address,uint16,address,bytes)._ercData](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L223) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L223


 - [ ] ID-329
Parameter [BaseTOFTMarketModule.borrow(address,uint16,bytes,uint64,bytes)._srcChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L128) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L128


 - [ ] ID-330
Parameter [Balancer.addRebalanceAmount(address,uint16,uint256)._amount](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L253) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L253


 - [ ] ID-331
Parameter [BaseTOFTStrategyModule.strategyDeposit(address,uint16,bytes,uint64,bytes,IERC20)._payload](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L127) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L127


 - [ ] ID-332
Parameter [BaseTOFTOptionsModule.exercise(address,uint16,bytes,uint64,bytes)._srcAddress](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L156) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L156


 - [ ] ID-333
Parameter [BaseTOFTMarketModule.borrow(address,uint16,bytes,uint64,bytes)._srcAddress](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L129) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L129


 - [ ] ID-334
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._amount](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-335
Parameter [TapiocaOFT.wrap(address,address,uint256)._amount](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/TapiocaOFT.sol#L72) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/TapiocaOFT.sol#L72


 - [ ] ID-336
Parameter [BaseOFTV2.estimateSendFee(uint16,bytes32,uint256,bool,bytes)._dstChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32


 - [ ] ID-337
Parameter [BaseTOFTMarketModule.remove(bytes)._payload](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L204) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L204


 - [ ] ID-338
Parameter [LzApp.lzReceive(uint16,bytes,uint64,bytes)._nonce](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35


 - [ ] ID-339
Parameter [BaseOFTV2.estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)._useZro](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36


 - [ ] ID-340
Parameter [LzApp.setSendVersion(uint16)._version](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L88) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L88


 - [ ] ID-341
Parameter [LzApp.setConfig(uint16,uint16,uint256,bytes)._configType](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84


 - [ ] ID-342
Parameter [BytesLib.concat(bytes,bytes)._postBytes](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L15) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L15


 - [ ] ID-343
Parameter [LzApp.getConfig(uint16,uint16,address,uint256)._configType](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L79) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L79


 - [ ] ID-344
Parameter [LzLib.getGasLimit(bytes)._adapterParams](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L47) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L47


 - [ ] ID-345
Parameter [ExcessivelySafeCall.excessivelySafeStaticCall(address,uint256,uint16,bytes)._target](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L76) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L76


 - [ ] ID-346
Parameter [BytesLib.toUint16(bytes,uint256)._bytes](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L319) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L319


 - [ ] ID-347
Parameter [BaseTOFTOptionsModule.exercise(address,uint16,bytes,uint64,bytes)._payload](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L158) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L158


 - [ ] ID-348
Parameter [NonblockingLzApp.nonblockingLzReceive(uint16,bytes,uint64,bytes)._srcChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37


 - [ ] ID-349
Parameter [BytesLib.toUint32(bytes,uint256)._start](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L330) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L330


 - [ ] ID-350
Parameter [BytesLib.toUint64(bytes,uint256)._start](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L341) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L341


 - [ ] ID-351
Parameter [LzApp.setPayloadSizeLimit(uint16,uint256)._size](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L130) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L130


 - [ ] ID-352
Parameter [mTapiocaOFT.unwrap(address,uint256)._amount](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L104) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L104


 - [ ] ID-353
Parameter [TapiocaWrapper.executeTOFT(address,bytes,bool)._toft](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L116) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/TapiocaWrapper.sol#L116


 - [ ] ID-354
Variable [EIP712._HASHED_NAME](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L35) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L35


 - [ ] ID-355
Parameter [Balancer.initConnectedOFT(address,uint16,address,bytes)._srcOft](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L220) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L220


 - [ ] ID-356
Parameter [BaseTOFTStrategyModule.depositToYieldbox(uint256,uint256,uint256,IERC20,address,address)._assetId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L174) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L174


 - [ ] ID-357
Parameter [TapiocaOFT.wrap(address,address,uint256)._toAddress](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/TapiocaOFT.sol#L71) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/TapiocaOFT.sol#L71


 - [ ] ID-358
Parameter [BytesLib.toUint96(bytes,uint256)._bytes](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L352) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L352


 - [ ] ID-359
Parameter [BaseTOFTMarketModule.borrowInternal(bytes32,ITapiocaOFT.IBorrowParams,ICommonData.IWithdrawParams,ICommonData.IApproval[])._to](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L181) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L181


 - [ ] ID-360
Parameter [BaseTOFTLeverageModule.leverageDown(address,uint16,bytes,uint64,bytes)._srcChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L150) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L150


 - [ ] ID-361
Parameter [LzApp.setConfig(uint16,uint16,uint256,bytes)._config](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84


 - [ ] ID-362
Parameter [LzLib.addressToBytes32(address)._address](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L78) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L78


 - [ ] ID-363
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._gasForCall](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-364
Parameter [TapiocaOFT.unwrap(address,uint256)._toAddress](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/TapiocaOFT.sol#L86) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/TapiocaOFT.sol#L86


 - [ ] ID-365
Parameter [Balancer.rebalance(address,uint16,uint256,uint256,bytes)._amount](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L176) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L176


 - [ ] ID-366
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._from](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-367
Parameter [BytesLib.toUint96(bytes,uint256)._start](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L352) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L352


 - [ ] ID-368
Parameter [Balancer.addRebalanceAmount(address,uint16,uint256)._dstChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L252) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L252


 - [ ] ID-369
Parameter [mTapiocaOFT.extractUnderlying(uint256)._amount](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L141) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/mTapiocaOFT.sol#L141


 - [ ] ID-370
Parameter [LzApp.setPrecrime(address)._precrime](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L118) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L118


 - [ ] ID-371
Parameter [OFTV2.setLdChain(uint16,bool)._chainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L36


 - [ ] ID-372
Parameter [LzApp.getTrustedRemoteAddress(uint16)._remoteChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L112) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L112


 - [ ] ID-373
Variable [EIP712._CACHED_DOMAIN_SEPARATOR](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L31) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L31


 - [ ] ID-374
Parameter [LzLib.buildDefaultAdapterParams(uint256)._uaGas](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L30) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L30


 - [ ] ID-375
Parameter [BytesLib.slice(bytes,uint256,uint256)._length](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L231) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L231


 - [ ] ID-376
Parameter [BaseTOFTStrategyModule.strategyDeposit(address,uint16,bytes,uint64,bytes,IERC20)._srcChainId](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L124) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L124


 - [ ] ID-377
Parameter [Balancer.addRebalanceAmount(address,uint16,uint256)._srcOft](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L251) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/Balancer.sol#L251


 - [ ] ID-378
Variable [EIP712._HASHED_VERSION](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L36


 - [ ] ID-379
Parameter [TapiocaOFT.wrap(address,address,uint256)._fromAddress](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/TapiocaOFT.sol#L70) is not in mixedCase

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/TapiocaOFT.sol#L70


## similar-names
Impact: Informational
Confidence: Medium
 - [ ] ID-380
Variable [BaseTOFTOptionsModule._callApproval(ICommonData.IApproval[]).reason_scope_0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L287) is too similar to [BaseTOFTOptionsModule._callApproval(ICommonData.IApproval[]).reason_scope_1](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L303)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L287


 - [ ] ID-381
Variable [BaseTOFTLeverageModule._callApproval(ICommonData.IApproval[]).reason_scope_0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L312) is too similar to [BaseTOFTLeverageModule._callApproval(ICommonData.IApproval[]).reason_scope_1](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L328)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L312


 - [ ] ID-382
Variable [BaseTOFTMarketModule._callApproval(ICommonData.IApproval[]).reason_scope_0](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L288) is too similar to [BaseTOFTMarketModule._callApproval(ICommonData.IApproval[]).reason_scope_1](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L304)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L288


## too-many-digits
Impact: Informational
Confidence: Medium
 - [ ] ID-383
[BytesLib.toAddress(bytes,uint256)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297-L306) uses literals with too many digits:
        - [tempAddress = mload(uint256)(_bytes + 0x20 + _start) / 0x1000000000000000000000000](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L302)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297-L306


 - [ ] ID-384
[ExcessivelySafeCall.slitherConstructorConstantVariables()](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L4-L136) uses literals with too many digits:
        - [LOW_28_MASK = 0x00000000ffffffffffffffffffffffffffffffffffffffffffffffffffffffff](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L5-L6)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L4-L136


## unused-state
Impact: Informational
Confidence: High
 - [ ] ID-385
[BaseTOFTStorage.PT_SEND_FROM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L41) is never used in [BaseTOFTLeverageModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L21-L340)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L41


 - [ ] ID-386
[BaseTOFTStorage.PT_TAP_EXERCISE](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L40) is never used in [BaseTOFTMarketModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L20-L316)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L40


 - [ ] ID-387
[BaseTOFTStorage.PT_SEND_FROM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L41) is never used in [BaseTOFTStrategyModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L16-L249)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L41


 - [ ] ID-388
[BaseTOFTStorage.PT_MARKET_MULTIHOP_SELL](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L37) is never used in [BaseTOFTStrategyModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L16-L249)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L37


 - [ ] ID-389
[BaseTOFTStorage.PT_MARKET_REMOVE_COLLATERAL](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L36) is never used in [BaseTOFTOptionsModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L16-L315)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L36


 - [ ] ID-390
[BaseTOFTStorage.PT_YB_SEND_SGL_BORROW](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L38) is never used in [BaseTOFTStrategyModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L16-L249)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L38


 - [ ] ID-391
[BaseTOFTStorage.PT_SEND_FROM](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L41) is never used in [BaseTOFTMarketModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L20-L316)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L41


 - [ ] ID-392
[BaseTOFTStorage.PT_TAP_EXERCISE](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L40) is never used in [BaseTOFTStrategyModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L16-L249)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L40


 - [ ] ID-393
[BaseTOFTStorage.PT_MARKET_MULTIHOP_SELL](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L37) is never used in [BaseTOFTOptionsModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L16-L315)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L37


 - [ ] ID-394
[BaseTOFTStorage.PT_LEVERAGE_MARKET_DOWN](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L39) is never used in [BaseTOFTMarketModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L20-L316)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L39


 - [ ] ID-395
[BaseTOFTStorage.PT_YB_SEND_STRAT](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L34) is never used in [BaseTOFTLeverageModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L21-L340)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L34


 - [ ] ID-396
[BaseTOFTStorage.PT_YB_RETRIEVE_STRAT](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L35) is never used in [BaseTOFTMarketModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L20-L316)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L35


 - [ ] ID-397
[BaseTOFTStorage.PT_MARKET_REMOVE_COLLATERAL](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L36) is never used in [BaseTOFTStrategyModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L16-L249)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L36


 - [ ] ID-398
[BaseTOFTStorage.PT_LEVERAGE_MARKET_DOWN](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L39) is never used in [BaseTOFTStrategyModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L16-L249)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L39


 - [ ] ID-399
[BaseTOFTStorage.PT_TAP_EXERCISE](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L40) is never used in [BaseTOFTLeverageModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L21-L340)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L40


 - [ ] ID-400
[BaseTOFTStorage.PT_YB_SEND_SGL_BORROW](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L38) is never used in [BaseTOFTLeverageModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L21-L340)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L38


 - [ ] ID-401
[BaseTOFTStorage.PT_MARKET_MULTIHOP_SELL](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L37) is never used in [BaseTOFTMarketModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L20-L316)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L37


 - [ ] ID-402
[BaseTOFTStorage.PT_LEVERAGE_MARKET_DOWN](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L39) is never used in [BaseTOFTOptionsModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L16-L315)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L39


 - [ ] ID-403
[BaseTOFTStorage.PT_YB_RETRIEVE_STRAT](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L35) is never used in [BaseTOFTOptionsModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L16-L315)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L35


 - [ ] ID-404
[BaseTOFTStorage.PT_YB_SEND_SGL_BORROW](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L38) is never used in [BaseTOFTOptionsModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L16-L315)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L38


 - [ ] ID-405
[BaseTOFTStorage.PT_YB_RETRIEVE_STRAT](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L35) is never used in [BaseTOFTLeverageModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L21-L340)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L35


 - [ ] ID-406
[BaseTOFTStorage.PT_YB_SEND_STRAT](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L34) is never used in [BaseTOFTMarketModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L20-L316)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L34


 - [ ] ID-407
[BaseTOFTStorage.PT_MARKET_REMOVE_COLLATERAL](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L36) is never used in [BaseTOFTLeverageModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L21-L340)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L36


 - [ ] ID-408
[BaseTOFTStorage.PT_YB_SEND_STRAT](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L34) is never used in [BaseTOFTOptionsModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L16-L315)

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L34


## immutable-states
Impact: Optimization
Confidence: High
 - [ ] ID-409
[BaseTOFT.optionsModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L39) should be immutable

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L39


 - [ ] ID-410
[BaseTOFTStorage._decimalCache](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L32) should be immutable

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L32


 - [ ] ID-411
[BaseTOFT.marketModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L36) should be immutable

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L36


 - [ ] ID-412
[BaseTOFTStorage.hostChainID](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L30) should be immutable

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L30


 - [ ] ID-413
[BaseTOFT.leverageModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L30) should be immutable

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L30


 - [ ] ID-414
[BaseTOFT.strategyModule](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L33) should be immutable

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFT.sol#L33


 - [ ] ID-415
[BaseTOFTStorage.erc20](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L28) should be immutable

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L28


 - [ ] ID-416
[BaseTOFTStorage.yieldBox](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L26) should be immutable

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/main/contracts/tOFT/BaseTOFTStorage.sol#L26

