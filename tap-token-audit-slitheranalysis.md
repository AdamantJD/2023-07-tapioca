**THIS CHECKLIST IS NOT COMPLETE**. Use `--show-ignored-findings` to show all the results.
Summary
 - [arbitrary-send-eth](#arbitrary-send-eth) (1 results) (High)
 - [delegatecall-loop](#delegatecall-loop) (1 results) (High)
 - [name-reused](#name-reused) (8 results) (High)
 - [unchecked-transfer](#unchecked-transfer) (9 results) (High)
 - [divide-before-multiply](#divide-before-multiply) (24 results) (Medium)
 - [incorrect-equality](#incorrect-equality) (5 results) (Medium)
 - [reentrancy-no-eth](#reentrancy-no-eth) (6 results) (Medium)
 - [uninitialized-local](#uninitialized-local) (3 results) (Medium)
 - [unused-return](#unused-return) (16 results) (Medium)
 - [shadowing-local](#shadowing-local) (13 results) (Low)
 - [events-maths](#events-maths) (1 results) (Low)
 - [missing-zero-check](#missing-zero-check) (12 results) (Low)
 - [calls-loop](#calls-loop) (3 results) (Low)
 - [reentrancy-benign](#reentrancy-benign) (12 results) (Low)
 - [reentrancy-events](#reentrancy-events) (25 results) (Low)
 - [timestamp](#timestamp) (22 results) (Low)
 - [assembly](#assembly) (48 results) (Informational)
 - [boolean-equal](#boolean-equal) (2 results) (Informational)
 - [pragma](#pragma) (1 results) (Informational)
 - [costly-loop](#costly-loop) (6 results) (Informational)
 - [dead-code](#dead-code) (2 results) (Informational)
 - [solc-version](#solc-version) (56 results) (Informational)
 - [low-level-calls](#low-level-calls) (5 results) (Informational)
 - [naming-convention](#naming-convention) (277 results) (Informational)
 - [similar-names](#similar-names) (16 results) (Informational)
 - [too-many-digits](#too-many-digits) (5 results) (Informational)
 - [unused-state](#unused-state) (1 results) (Informational)
 - [constable-states](#constable-states) (1 results) (Optimization)
 - [immutable-states](#immutable-states) (5 results) (Optimization)

## arbitrary-send-eth
Impact: High
Confidence: Medium
 - [ ] ID-0
[BaseTapOFT._claimRewards(uint16,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L198-L245) sends eth to arbitrary user
	Dangerous calls:
	- [ISendFrom(address(rewardTokens[i])).sendFrom{value: rewardClaimSendParams[i].ethValue}(address(this),_srcChainId,LzLib.addressToBytes32(to),IERC20(rewardTokens[i]).balanceOf(address(this)),rewardClaimSendParams[i].callParams)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L229-L237)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L198-L245


## delegatecall-loop
Impact: High
Confidence: Medium
 - [ ] ID-1
[BaseBoringBatchable.batch(bytes[],bool)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L35-L42) has delegatecall inside a loop in a payable function: [(success,result) = address(this).delegatecall(calls[i])](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L37)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L35-L42


## name-reused
Impact: High
Confidence: High
 - [ ] ID-2
ILayerZeroUserApplicationConfig is re-used:
	- [ILayerZeroUserApplicationConfig](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroUserApplicationConfig.sol#L5-L25)
	- [ILayerZeroUserApplicationConfig](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/interfaces/ILayerZeroUserApplicationConfig.sol#L5-L25)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroUserApplicationConfig.sol#L5-L25


 - [ ] ID-3
ILayerZeroEndpoint is re-used:
	- [ILayerZeroEndpoint](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroEndpoint.sol#L7-L87)
	- [ILayerZeroEndpoint](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/interfaces/ILayerZeroEndpoint.sol#L7-L87)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroEndpoint.sol#L7-L87


 - [ ] ID-4
NonblockingLzApp is re-used:
	- [NonblockingLzApp](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L13-L57)
	- [NonblockingLzApp](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/lzApp/NonblockingLzApp.sol#L13-L57)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L13-L57


 - [ ] ID-5
ExcessivelySafeCall is re-used:
	- [ExcessivelySafeCall](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L4-L136)
	- [ExcessivelySafeCall](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/ExcessivelySafeCall.sol#L4-L136)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L4-L136


 - [ ] ID-6
ILayerZeroReceiver is re-used:
	- [ILayerZeroReceiver](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroReceiver.sol#L5-L12)
	- [ILayerZeroReceiver](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/interfaces/ILayerZeroReceiver.sol#L5-L12)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroReceiver.sol#L5-L12


 - [ ] ID-7
LzApp is re-used:
	- [LzApp](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L14-L139)
	- [LzApp](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/lzApp/LzApp.sol#L14-L139)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L14-L139


 - [ ] ID-8
BytesLib is re-used:
	- [BytesLib](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L12-L510)
	- [BytesLib](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L12-L510)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L12-L510


 - [ ] ID-9
IERC20 is re-used:
	- [IERC20](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC20.sol#L4-L26)
	- [IERC20](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol#L9-L82)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC20.sol#L4-L26


## unchecked-transfer
Impact: High
Confidence: Medium
 - [ ] ID-10
[LTap.redeem()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L46-L51) ignores return value by [tapToken.transfer(msg.sender,amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L50)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L46-L51


 - [ ] ID-11
[TwTAP.participate(address,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L252-L348) ignores return value by [tapOFT.transferFrom(msg.sender,address(this),_amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L260)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L252-L348


 - [ ] ID-12
[TapiocaOptionBroker._processOTCDeal(ERC20,PaymentTokenOracle,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L508-L536) ignores return value by [_paymentToken.transferFrom(msg.sender,address(this),discountedPaymentAmount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L530-L534)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L508-L536


 - [ ] ID-13
[TwTAP._releaseTap(uint256,address)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L522-L568) ignores return value by [tapOFT.transfer(_to,releasedAmount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L565)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L522-L568


 - [ ] ID-14
[AirdropBroker._processOTCDeal(ERC20,PaymentTokenOracle,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L487-L515) ignores return value by [tapOFT.transfer(msg.sender,tapAmount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L514)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L487-L515


 - [ ] ID-15
[TapiocaOptionBroker.collectPaymentTokens(address[])](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L479-L497) ignores return value by [paymentToken.transfer(paymentTokenBeneficiary,paymentToken.balanceOf(address(this)))](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L491-L494)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L479-L497


 - [ ] ID-16
[AirdropBroker.collectPaymentTokens(address[])](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L365-L383) ignores return value by [paymentToken.transfer(paymentTokenBeneficiary,paymentToken.balanceOf(address(this)))](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L377-L380)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L365-L383


 - [ ] ID-17
[AirdropBroker._processOTCDeal(ERC20,PaymentTokenOracle,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L487-L515) ignores return value by [_paymentToken.transferFrom(msg.sender,address(this),discountedPaymentAmount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L509-L513)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L487-L515


 - [ ] ID-18
[LTap.deposit(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L41-L44) ignores return value by [tapToken.transferFrom(msg.sender,address(this),amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L42)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L41-L44


## divide-before-multiply
Impact: Medium
Confidence: Medium
 - [ ] ID-19
[BytesLib.concatStorage(bytes,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226) performs a multiplication on the result of a division:
	- [sstore(uint256,uint256)(sc_concatStorage_asm_0,mload(uint256)(mc_concatStorage_asm_0) / mask_concatStorage_asm_0 * mask_concatStorage_asm_0)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L223)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226


 - [ ] ID-20
[BytesLib.concatStorage(bytes,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226) performs a multiplication on the result of a division:
	- [sstore(uint256,uint256)(_preBytes,fslot_concatStorage_asm_0 + mload(uint256)(_postBytes + 0x20) / 0x100 ** 32 - mlength_concatStorage_asm_0 * 0x100 ** 32 - newlength_concatStorage_asm_0 + mlength_concatStorage_asm_0 * 2)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L115-L140)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226


 - [ ] ID-21
[BytesLib.concatStorage(bytes,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L91-L226) performs a multiplication on the result of a division:
	- [sstore(uint256,uint256)(sc_concatStorage_asm_0,mload(uint256)(mc_concatStorage_asm_0) / mask_concatStorage_asm_0 * mask_concatStorage_asm_0)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L223)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L91-L226


 - [ ] ID-22
[FullMath.muldiv(uint256,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L6-L106) performs a multiplication on the result of a division:
	- [denominator = denominator / twos](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L65)
	- [inv *= 2 - denominator * inv](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L91)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L6-L106


 - [ ] ID-23
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
	- [denominator = denominator / twos](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
	- [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L126)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-24
[BytesLib.concatStorage(bytes,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L91-L226) performs a multiplication on the result of a division:
	- [sstore(uint256,uint256)(_preBytes,fslot_concatStorage_asm_0 + mload(uint256)(_postBytes + 0x20) / 0x100 ** 32 - mlength_concatStorage_asm_0 * 0x100 ** 32 - newlength_concatStorage_asm_0 + mlength_concatStorage_asm_0 * 2)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L115-L140)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L91-L226


 - [ ] ID-25
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
	- [denominator = denominator / twos](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
	- [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L124)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-26
[BytesLib.equalStorage(bytes,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L439-L509) performs a multiplication on the result of a division:
	- [fslot_equalStorage_asm_0 = fslot_equalStorage_asm_0 / 0x100 * 0x100](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L466)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L439-L509


 - [ ] ID-27
[FullMath.muldiv(uint256,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L6-L106) performs a multiplication on the result of a division:
	- [denominator = denominator / twos](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L65)
	- [inv *= 2 - denominator * inv](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L94)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L6-L106


 - [ ] ID-28
[FullMath.muldiv(uint256,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L6-L106) performs a multiplication on the result of a division:
	- [denominator = denominator / twos](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L65)
	- [inv *= 2 - denominator * inv](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L92)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L6-L106


 - [ ] ID-29
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
	- [denominator = denominator / twos](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
	- [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L123)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-30
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
	- [denominator = denominator / twos](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
	- [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L121)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-31
[FullMath.muldiv(uint256,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L6-L106) performs a multiplication on the result of a division:
	- [denominator = denominator / twos](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L65)
	- [inv *= 2 - denominator * inv](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L90)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L6-L106


 - [ ] ID-32
[BytesLib.equalStorage(bytes,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L439-L509) performs a multiplication on the result of a division:
	- [fslot_equalStorage_asm_0 = fslot_equalStorage_asm_0 / 0x100 * 0x100](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L466)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L439-L509


 - [ ] ID-33
[FullMath.muldiv(uint256,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L6-L106) performs a multiplication on the result of a division:
	- [prod0 = prod0 / twos](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L70)
	- [result = prod0 * inv](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L104)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L6-L106


 - [ ] ID-34
[BytesLib.concatStorage(bytes,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L91-L226) performs a multiplication on the result of a division:
	- [sstore(uint256,uint256)(sc_concatStorage_asm_0,mload(uint256)(mc_concatStorage_asm_0) / mask_concatStorage_asm_0 * mask_concatStorage_asm_0)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L189)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L91-L226


 - [ ] ID-35
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
	- [denominator = denominator / twos](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
	- [inverse = (3 * denominator) ^ 2](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L117)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-36
[BytesLib.concatStorage(bytes,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226) performs a multiplication on the result of a division:
	- [sstore(uint256,uint256)(sc_concatStorage_asm_0,mload(uint256)(mc_concatStorage_asm_0) / mask_concatStorage_asm_0 * mask_concatStorage_asm_0)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L189)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226


 - [ ] ID-37
[FullMath.muldiv(uint256,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L6-L106) performs a multiplication on the result of a division:
	- [denominator = denominator / twos](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L65)
	- [inv *= 2 - denominator * inv](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L95)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L6-L106


 - [ ] ID-38
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
	- [denominator = denominator / twos](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
	- [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L122)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-39
[FullMath.muldiv(uint256,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L6-L106) performs a multiplication on the result of a division:
	- [denominator = denominator / twos](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L65)
	- [inv *= 2 - denominator * inv](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L93)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L6-L106


 - [ ] ID-40
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
	- [prod0 = prod0 / twos](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L105)
	- [result = prod0 * inverse](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L132)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-41
[FullMath.muldiv(uint256,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L6-L106) performs a multiplication on the result of a division:
	- [denominator = denominator / twos](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L65)
	- [inv = (3 * denominator) ^ 2](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L86)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L6-L106


 - [ ] ID-42
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
	- [denominator = denominator / twos](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
	- [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L125)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


## incorrect-equality
Impact: Medium
Confidence: High
 - [ ] ID-43
[TwTAP.distributeReward(uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L429-L449) uses a dangerous strict equality:
	- [require(bool,string)(lastProcessedWeek == currentWeek(),twTAP: Advance week first)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L433-L436)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L429-L449


 - [ ] ID-44
[Vesting.claim()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L110-L121) uses a dangerous strict equality:
	- [_claimable == 0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L113)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L110-L121


 - [ ] ID-45
[TWAML.computeTarget(uint256,uint256,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L132-L144) uses a dangerous strict equality:
	- [_cumulative == 0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L138)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L132-L144


 - [ ] ID-46
[Vesting._vested(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L167-L173) uses a dangerous strict equality:
	- [start == 0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L168)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L167-L173


 - [ ] ID-47
[TwTAP.claimable(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L166-L242) uses a dangerous strict equality:
	- [votes == 0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L179)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L166-L242


## reentrancy-no-eth
Impact: Medium
Confidence: Medium
 - [ ] ID-48
Reentrancy in [TwTAP._claimRewardsOn(uint256,address,IERC20[])](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L499-L519):
	External calls:
	- [rewardTokens[claimableIndex].safeTransfer(_to,amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L514)
	State variables written after the call(s):
	- [claimed[_tokenId][claimableIndex] += amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L513)
	[TwTAP.claimed](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L100) can be used in cross function reentrancies:
	- [TwTAP._claimRewards(uint256,address)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L483-L496)
	- [TwTAP._claimRewardsOn(uint256,address,IERC20[])](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L499-L519)
	- [TwTAP.claimable(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L166-L242)
	- [TwTAP.claimed](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L100)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L499-L519


 - [ ] ID-49
Reentrancy in [TwTAP._claimRewards(uint256,address)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L483-L496):
	External calls:
	- [rewardTokens[i].safeTransfer(_to,amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L492)
	State variables written after the call(s):
	- [claimed[_tokenId][i] += amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L491)
	[TwTAP.claimed](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L100) can be used in cross function reentrancies:
	- [TwTAP._claimRewards(uint256,address)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L483-L496)
	- [TwTAP._claimRewardsOn(uint256,address,IERC20[])](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L499-L519)
	- [TwTAP.claimable(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L166-L242)
	- [TwTAP.claimed](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L100)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L483-L496


 - [ ] ID-50
Reentrancy in [BaseTapOFT._lockTwTapPosition(uint16,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L125-L149):
	External calls:
	- [twTap.participate(to,amount,duration)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L138-L148)
	State variables written after the call(s):
	- [_transferFrom(address(this),to,amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L144)
		- [_balances[from] = fromBalance - amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L239)
		- [_balances[to] += amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L242)
	[ERC20._balances](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L36) can be used in cross function reentrancies:
	- [ERC20._burn(address,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L285-L301)
	- [ERC20._mint(address,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L259-L272)
	- [ERC20._transfer(address,address,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L226-L248)
	- [ERC20.balanceOf(address)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L101-L103)
	- [_transferFrom(address(this),to,amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L147)
		- [_balances[from] = fromBalance - amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L239)
		- [_balances[to] += amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L242)
	[ERC20._balances](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L36) can be used in cross function reentrancies:
	- [ERC20._burn(address,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L285-L301)
	- [ERC20._mint(address,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L259-L272)
	- [ERC20._transfer(address,address,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L226-L248)
	- [ERC20.balanceOf(address)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L101-L103)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L125-L149


 - [ ] ID-51
Reentrancy in [TapiocaOptionBroker.participate(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L212-L292):
	External calls:
	- [tOLP.transferFrom(msg.sender,address(this),_tOLPTokenID)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L230)
	State variables written after the call(s):
	- [twAML[lock.sglAssetID] = pool](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L263)
	[TapiocaOptionBroker.twAML](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L73) can be used in cross function reentrancies:
	- [TapiocaOptionBroker.exitPosition(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L296-L345)
	- [TapiocaOptionBroker.participate(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L212-L292)
	- [TapiocaOptionBroker.twAML](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L73)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L212-L292


 - [ ] ID-52
Reentrancy in [TapiocaOptionLiquidityProvision.unlock(uint256,IERC20,address)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L207-L250):
	External calls:
	- [yieldBox.transfer(address(this),_to,lockPosition.sglAssetID,sharesOut)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L241-L246)
	State variables written after the call(s):
	- [activeSingularities[_singularity].totalDeposited -= lockPosition.amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L247)
	[TapiocaOptionLiquidityProvision.activeSingularities](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L61) can be used in cross function reentrancies:
	- [TapiocaOptionLiquidityProvision._computeSGLPoolWeights()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L336-L345)
	- [TapiocaOptionLiquidityProvision.activeSingularities](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L61)
	- [TapiocaOptionLiquidityProvision.getSingularityPools()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L126-L143)
	- [TapiocaOptionLiquidityProvision.getTotalPoolDeposited(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L146-L152)
	- [TapiocaOptionLiquidityProvision.lock(address,IERC20,uint128,uint128)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L171-L201)
	- [TapiocaOptionLiquidityProvision.registerSingularity(IERC20,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L276-L293)
	- [TapiocaOptionLiquidityProvision.setSGLPoolWEight(IERC20,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L259-L270)
	- [TapiocaOptionLiquidityProvision.unlock(uint256,IERC20,address)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L207-L250)
	- [TapiocaOptionLiquidityProvision.unregisterSingularity(IERC20)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L297-L329)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L207-L250


 - [ ] ID-53
Reentrancy in [TapiocaOptionLiquidityProvision.lock(address,IERC20,uint128,uint128)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L171-L201):
	External calls:
	- [yieldBox.transfer(msg.sender,address(this),sglAssetID,sharesIn)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L186)
	State variables written after the call(s):
	- [activeSingularities[_singularity].totalDeposited += _amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L187)
	[TapiocaOptionLiquidityProvision.activeSingularities](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L61) can be used in cross function reentrancies:
	- [TapiocaOptionLiquidityProvision._computeSGLPoolWeights()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L336-L345)
	- [TapiocaOptionLiquidityProvision.activeSingularities](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L61)
	- [TapiocaOptionLiquidityProvision.getSingularityPools()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L126-L143)
	- [TapiocaOptionLiquidityProvision.getTotalPoolDeposited(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L146-L152)
	- [TapiocaOptionLiquidityProvision.lock(address,IERC20,uint128,uint128)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L171-L201)
	- [TapiocaOptionLiquidityProvision.registerSingularity(IERC20,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L276-L293)
	- [TapiocaOptionLiquidityProvision.setSGLPoolWEight(IERC20,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L259-L270)
	- [TapiocaOptionLiquidityProvision.unlock(uint256,IERC20,address)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L207-L250)
	- [TapiocaOptionLiquidityProvision.unregisterSingularity(IERC20)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L297-L329)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L171-L201


## uninitialized-local
Impact: Medium
Confidence: Medium
 - [ ] ID-54
[TwTAP.participate(address,uint256,uint256).divergenceForce](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L266) is a local variable never initialized

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L266


 - [ ] ID-55
[TapiocaOptionBroker.participate(uint256).divergenceForce](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L236) is a local variable never initialized

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L236


 - [ ] ID-56
[Vesting.registerUser(address,uint256).data](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L136) is a local variable never initialized

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L136


## unused-return
Impact: Medium
Confidence: Medium
 - [ ] ID-57
[TapiocaOptionBroker.exerciseOption(uint256,ERC20,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L351-L409) ignores return value by [(oTAPPosition) = oTAP.attributes(_oTAPTokenID)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L357)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L351-L409


 - [ ] ID-58
[AirdropBroker.exerciseOption(uint256,ERC20,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L224-L276) ignores return value by [(aoTapOption) = aoTAP.attributes(_aoTAPTokenID)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L230-L232)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L224-L276


 - [ ] ID-59
[TapiocaOptionBroker.getOTCDealDetails(uint256,ERC20,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L145-L204) ignores return value by [(paymentTokenValuation) = paymentTokenOracle.oracle.peek(paymentTokenOracle.oracleData)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L194-L196)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L145-L204


 - [ ] ID-60
[TapiocaOptionBroker.exitPosition(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L296-L345) ignores return value by [(oTAPPosition) = oTAP.attributes(_oTAPTokenID)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L300)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L296-L345


 - [ ] ID-61
[AirdropBroker.getOTCDealDetails(uint256,ERC20,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L141-L191) ignores return value by [(paymentTokenValuation) = paymentTokenOracle.oracle.peek(paymentTokenOracle.oracleData)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L181-L183)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L141-L191


 - [ ] ID-62
[OFTCoreV2._estimateSendFee(uint16,bytes32,uint256,bool,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L70-L74) ignores return value by [lzEndpoint.estimateFees(_dstChainId,address(this),payload,_useZro,_adapterParams)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L73)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L70-L74


 - [ ] ID-63
[TapiocaOptionBroker.exitPosition(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L296-L345) ignores return value by [(lock) = tOLP.getLock(oTAPPosition.tOLP)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L301)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L296-L345


 - [ ] ID-64
[BaseTapOFT._lockTwTapPosition(uint16,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L125-L149) ignores return value by [twTap.participate(to,amount,duration)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L138-L148)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L125-L149


 - [ ] ID-65
[ONFT721Core.estimateSendBatchFee(uint16,bytes,uint256[],bool,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L37-L40) ignores return value by [lzEndpoint.estimateFees(_dstChainId,address(this),payload,_useZro,_adapterParams)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L39)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L37-L40


 - [ ] ID-66
[AirdropBroker._processOTCDeal(ERC20,PaymentTokenOracle,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L487-L515) ignores return value by [(paymentTokenValuation) = _paymentTokenOracle.oracle.get(_paymentTokenOracle.oracleData)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L497-L499)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L487-L515


 - [ ] ID-67
[TapiocaOptionBroker.getOTCDealDetails(uint256,ERC20,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L145-L204) ignores return value by [(oTAPPosition) = oTAP.attributes(_oTAPTokenID)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L159)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L145-L204


 - [ ] ID-68
[AirdropBroker.newEpoch()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L280-L294) ignores return value by [(_epochTAPValuation) = tapOracle.get(tapOracleData)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L291)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L280-L294


 - [ ] ID-69
[AirdropBroker.getOTCDealDetails(uint256,ERC20,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L141-L191) ignores return value by [(aoTapOption) = aoTAP.attributes(_aoTAPTokenID)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L155-L157)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L141-L191


 - [ ] ID-70
[OFTCoreV2._estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L76-L80) ignores return value by [lzEndpoint.estimateFees(_dstChainId,address(this),payload,_useZro,_adapterParams)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L79)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L76-L80


 - [ ] ID-71
[TapiocaOptionBroker._processOTCDeal(ERC20,PaymentTokenOracle,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L508-L536) ignores return value by [(paymentTokenValuation) = _paymentTokenOracle.oracle.get(_paymentTokenOracle.oracleData)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L518-L520)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L508-L536


 - [ ] ID-72
[TapiocaOptionBroker.newEpoch()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L413-L432) ignores return value by [(None,epochTAPValuation) = tapOracle.get(tapOracleData)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L430)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L413-L432


## shadowing-local
Impact: Low
Confidence: High
 - [ ] ID-73
[ERC20Permit.constructor(string).name](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L44) shadows:
	- [ERC20.name()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L62-L64) (function)
	- [IERC20Metadata.name()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L17) (function)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L44


 - [ ] ID-74
[ONFT721.constructor(string,string,uint256,address)._symbol](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721.sol#L12) shadows:
	- [ERC721._symbol](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L27) (state variable)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721.sol#L12


 - [ ] ID-75
[BaseTapOFT.constructor(string,string,uint8,address)._symbol](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L46) shadows:
	- [ERC20._symbol](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L43) (state variable)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L46


 - [ ] ID-76
[OFTV2.constructor(string,string,uint8,address).decimals](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L14) shadows:
	- [ERC20.decimals()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L87-L89) (function)
	- [IERC20Metadata.decimals()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L27) (function)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L14


 - [ ] ID-77
[IYieldBox.owner(uint256).owner](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L29) shadows:
	- [IYieldBox.owner(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L29) (function)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L29


 - [ ] ID-78
[IYieldBox.wrappedNative().wrappedNative](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L8) shadows:
	- [IYieldBox.wrappedNative()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L8) (function)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L8


 - [ ] ID-79
[OFTV2.constructor(string,string,uint8,address)._symbol](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L13) shadows:
	- [ERC20._symbol](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L43) (state variable)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L13


 - [ ] ID-80
[ONFT721.constructor(string,string,uint256,address)._name](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721.sol#L12) shadows:
	- [ERC721._name](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L24) (state variable)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721.sol#L12


 - [ ] ID-81
[OFTV2.constructor(string,string,uint8,address)._name](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L13) shadows:
	- [ERC20._name](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L42) (state variable)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L13


 - [ ] ID-82
[IYieldBox.totalSupply(uint256).totalSupply](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L31) shadows:
	- [IYieldBox.totalSupply(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L31) (function)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L31


 - [ ] ID-83
[ERC721Permit.constructor(string).name](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ERC4494.sol#L45) shadows:
	- [ERC721.name()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L79-L81) (function)
	- [IERC721Metadata.name()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/extensions/IERC721Metadata.sol#L16) (function)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ERC4494.sol#L45


 - [ ] ID-84
[TwTAP.constructor(address,address,address,uint256,uint256)._owner](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L117) shadows:
	- [Ownable._owner](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/access/Ownable.sol#L21) (state variable)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L117


 - [ ] ID-85
[BaseTapOFT.constructor(string,string,uint8,address)._name](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L45) shadows:
	- [ERC20._name](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L42) (state variable)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L45


## events-maths
Impact: Low
Confidence: Medium
 - [ ] ID-86
[Vesting.init(IERC20,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L151-L162) should emit an event for: 
	- [seeded = _seededAmount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L160) 

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L151-L162


## missing-zero-check
Impact: Low
Confidence: Medium
 - [ ] ID-87
[BoringOwnable.transferOwnership(address,bool,bool).newOwner](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L27) lacks a zero-check on :
		- [pendingOwner = newOwner](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L41)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L27


 - [ ] ID-88
[AOTAP.constructor(address)._owner](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L40) lacks a zero-check on :
		- [owner = _owner](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L42)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L40


 - [ ] ID-89
[TapiocaOptionBroker.setPaymentTokenBeneficiary(address)._paymentTokenBeneficiary](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L472) lacks a zero-check on :
		- [paymentTokenBeneficiary = _paymentTokenBeneficiary](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L474)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L472


 - [ ] ID-90
[AirdropBroker.setPaymentTokenBeneficiary(address)._paymentTokenBeneficiary](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L358) lacks a zero-check on :
		- [paymentTokenBeneficiary = _paymentTokenBeneficiary](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L360)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L358


 - [ ] ID-91
[TapiocaOptionBroker.constructor(address,address,address,address,uint256,address)._paymentTokenBeneficiary](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L85) lacks a zero-check on :
		- [paymentTokenBeneficiary = _paymentTokenBeneficiary](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L89)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L85


 - [ ] ID-92
[LzApp.setPrecrime(address)._precrime](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/lzApp/LzApp.sol#L118) lacks a zero-check on :
		- [precrime = _precrime](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/lzApp/LzApp.sol#L119)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/lzApp/LzApp.sol#L118


 - [ ] ID-93
[TapiocaOptionBroker.constructor(address,address,address,address,uint256,address)._owner](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L87) lacks a zero-check on :
		- [owner = _owner](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L94)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L87


 - [ ] ID-94
[AirdropBroker.constructor(address,address,address,address,address)._paymentTokenBeneficiary](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L102) lacks a zero-check on :
		- [paymentTokenBeneficiary = _paymentTokenBeneficiary](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L105)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L102


 - [ ] ID-95
[AirdropBroker.constructor(address,address,address,address,address)._owner](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L103) lacks a zero-check on :
		- [owner = _owner](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L109)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L103


 - [ ] ID-96
[Vesting.constructor(uint256,uint256,address)._owner](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L67) lacks a zero-check on :
		- [owner = _owner](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L72)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L67


 - [ ] ID-97
[LzApp.setPrecrime(address)._precrime](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L118) lacks a zero-check on :
		- [precrime = _precrime](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L119)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L118


 - [ ] ID-98
[TapiocaOptionLiquidityProvision.constructor(address,address)._owner](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L69) lacks a zero-check on :
		- [owner = _owner](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L75)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L69


## calls-loop
Impact: Low
Confidence: Medium
 - [ ] ID-99
[BaseBoringBatchable.batch(bytes[],bool)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L35-L42) has external calls inside a loop: [(success,result) = address(this).delegatecall(calls[i])](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L37)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L35-L42


 - [ ] ID-100
[TapiocaOptionBroker.collectPaymentTokens(address[])](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L479-L497) has external calls inside a loop: [paymentToken.transfer(paymentTokenBeneficiary,paymentToken.balanceOf(address(this)))](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L491-L494)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L479-L497


 - [ ] ID-101
[AirdropBroker.collectPaymentTokens(address[])](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L365-L383) has external calls inside a loop: [paymentToken.transfer(paymentTokenBeneficiary,paymentToken.balanceOf(address(this)))](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L377-L380)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L365-L383


## reentrancy-benign
Impact: Low
Confidence: Medium
 - [ ] ID-102
Reentrancy in [TapiocaOptionLiquidityProvision.lock(address,IERC20,uint128,uint128)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L171-L201):
	External calls:
	- [yieldBox.transfer(msg.sender,address(this),sglAssetID,sharesIn)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L186)
	- [_safeMint(_to,tokenId)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L191)
		- [retval = IERC721Receiver(to).onERC721Received(_msgSender(),from,tokenId,data)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L436-L447)
	State variables written after the call(s):
	- [lockPosition.lockTime = uint128(block.timestamp)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L195)
	- [lockPosition.sglAssetID = uint128(sglAssetID)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L196)
	- [lockPosition.lockDuration = _lockDuration](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L197)
	- [lockPosition.amount = _amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L198)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L171-L201


 - [ ] ID-103
Reentrancy in [TapiocaOptionLiquidityProvision.lock(address,IERC20,uint128,uint128)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L171-L201):
	External calls:
	- [yieldBox.transfer(msg.sender,address(this),sglAssetID,sharesIn)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L186)
	State variables written after the call(s):
	- [tokenId = ++ tokenCounter](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L190)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L171-L201


 - [ ] ID-104
Reentrancy in [TapiocaOptionBroker.newEpoch()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L413-L432):
	External calls:
	- [epochTAP = tapOFT.emitForWeek()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L426)
	State variables written after the call(s):
	- [_emitToGauges(epochTAP)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L427)
		- [singularityGauges[epoch][sglPools[i].sglAssetID] = quotaPerSingularity](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L572-L574)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L413-L432


 - [ ] ID-105
Reentrancy in [LTap.deposit(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L41-L44):
	External calls:
	- [tapToken.transferFrom(msg.sender,address(this),amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L42)
	State variables written after the call(s):
	- [_mint(msg.sender,amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L43)
		- [_balances[account] += amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L267)
	- [_mint(msg.sender,amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L43)
		- [_totalSupply += amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L264)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L41-L44


 - [ ] ID-106
Reentrancy in [TwTAP.participate(address,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L252-L348):
	External calls:
	- [tapOFT.transferFrom(msg.sender,address(this),_amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L260)
	- [_safeMint(_participant,tokenId)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L310)
		- [to.isContract()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L435)
		- [retval = IERC721Receiver(to).onERC721Received(_msgSender(),from,tokenId,data)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L436-L447)
	State variables written after the call(s):
	- [participants[tokenId] = Participation(pool.averageMagnitude,hasVotingPower,divergenceForce,false,uint56(expiry),uint88(_amount),uint24(multiplier),uint40(w0),uint40(w1))](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L328-L338)
	- [weekTotals[w0 + 1].netActiveVotes += int256(votes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L343)
	- [weekTotals[w1 + 1].netActiveVotes -= int256(votes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L344)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L252-L348


 - [ ] ID-107
Reentrancy in [AOTAP.mint(address,uint128,uint128,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L109-L124):
	External calls:
	- [_safeMint(_to,tokenId)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L116)
		- [retval = IERC721Receiver(to).onERC721Received(_msgSender(),from,tokenId,data)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L436-L447)
	State variables written after the call(s):
	- [option.expiry = _expiry](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L119)
	- [option.discount = _discount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L120)
	- [option.amount = _amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L121)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L109-L124


 - [ ] ID-108
Reentrancy in [TwTAP.participate(address,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L252-L348):
	External calls:
	- [tapOFT.transferFrom(msg.sender,address(this),_amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L260)
	State variables written after the call(s):
	- [tokenId = ++ mintedTWTap](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L309)
	- [twAML = pool](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L300)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L252-L348


 - [ ] ID-109
Reentrancy in [TapiocaOptionBroker.newEpoch()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L413-L432):
	External calls:
	- [epochTAP = tapOFT.emitForWeek()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L426)
	- [(None,epochTAPValuation) = tapOracle.get(tapOracleData)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L430)
	State variables written after the call(s):
	- [(None,epochTAPValuation) = tapOracle.get(tapOracleData)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L430)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L413-L432


 - [ ] ID-110
Reentrancy in [BaseTapOFT._lockTwTapPosition(uint16,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L125-L149):
	External calls:
	- [twTap.participate(to,amount,duration)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L138-L148)
	State variables written after the call(s):
	- [_transferFrom(address(this),to,amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L144)
		- [_allowances[owner][spender] = amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L324)
	- [_transferFrom(address(this),to,amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L147)
		- [_allowances[owner][spender] = amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L324)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L125-L149


 - [ ] ID-111
Reentrancy in [OTAP.mint(address,uint128,uint128,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L96-L111):
	External calls:
	- [_safeMint(_to,tokenId)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L103)
		- [retval = IERC721Receiver(to).onERC721Received(_msgSender(),from,tokenId,data)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L436-L447)
	State variables written after the call(s):
	- [option.expiry = _expiry](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L106)
	- [option.discount = _discount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L107)
	- [option.tOLP = _tOLP](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L108)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L96-L111


 - [ ] ID-112
Reentrancy in [AirdropBroker.newEpoch()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L280-L294):
	External calls:
	- [(_epochTAPValuation) = tapOracle.get(tapOracleData)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L291)
	State variables written after the call(s):
	- [epochTAPValuation = uint128(_epochTAPValuation)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L292)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L280-L294


 - [ ] ID-113
Reentrancy in [TapiocaOptionBroker.participate(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L212-L292):
	External calls:
	- [tOLP.transferFrom(msg.sender,address(this),_tOLPTokenID)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L230)
	State variables written after the call(s):
	- [participants[_tOLPTokenID] = Participation(hasVotingPower,divergenceForce,pool.averageMagnitude)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L272-L276)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L212-L292


## reentrancy-events
Impact: Low
Confidence: Medium
 - [ ] ID-114
Reentrancy in [OFTCoreV2._send(address,uint16,bytes32,uint256,address,address,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L94-L105):
	External calls:
	- [_lzSend(_dstChainId,lzPayload,_refundAddress,_zroPaymentAddress,_adapterParams,msg.value)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L102)
		- [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
	Event emitted after the call(s):
	- [SendToChain(_dstChainId,_from,_toAddress,amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L104)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L94-L105


 - [ ] ID-115
Reentrancy in [LTap.deposit(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L41-L44):
	External calls:
	- [tapToken.transferFrom(msg.sender,address(this),amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L42)
	Event emitted after the call(s):
	- [Transfer(address(0),account,amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L269)
		- [_mint(msg.sender,amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L43)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L41-L44


 - [ ] ID-116
Reentrancy in [AOTAP.mint(address,uint128,uint128,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L109-L124):
	External calls:
	- [_safeMint(_to,tokenId)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L116)
		- [retval = IERC721Receiver(to).onERC721Received(_msgSender(),from,tokenId,data)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L436-L447)
	Event emitted after the call(s):
	- [Mint(_to,tokenId,option)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L123)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L109-L124


 - [ ] ID-117
Reentrancy in [ONFT721Core._send(address,uint16,bytes,uint256[],address,address,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L50-L64):
	External calls:
	- [_lzSend(_dstChainId,payload,_refundAddress,_zroPaymentAddress,_adapterParams,msg.value)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L62)
		- [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/lzApp/LzApp.sol#L53)
	Event emitted after the call(s):
	- [SendToChain(_dstChainId,_from,_toAddress,_tokenIds)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L63)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L50-L64


 - [ ] ID-118
Reentrancy in [BaseTapOFT.claimRewards(address,uint256,address[],uint16,address,bytes,IRewardClaimSendFromParams[])](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L163-L196):
	External calls:
	- [_lzSend(lzDstChainId,lzPayload,address(msg.sender),zroPaymentAddress,adapterParams,msg.value)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L181-L188)
		- [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
	Event emitted after the call(s):
	- [SendToChain(lzDstChainId,msg.sender,LzLib.addressToBytes32(to),0)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L190-L195)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L163-L196


 - [ ] ID-119
Reentrancy in [TapiocaOptionBroker.newEpoch()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L413-L432):
	External calls:
	- [epochTAP = tapOFT.emitForWeek()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L426)
	- [(None,epochTAPValuation) = tapOracle.get(tapOracleData)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L430)
	Event emitted after the call(s):
	- [NewEpoch(epoch,epochTAP,epochTAPValuation)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L431)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L413-L432


 - [ ] ID-120
Reentrancy in [BaseTapOFT._claimRewards(uint16,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L198-L245):
	External calls:
	- [twTap.claimAndSendRewards(tokenID,rewardTokens)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L225-L244)
	Event emitted after the call(s):
	- [CallFailedBytes(_srcChainId,_payload,_reason_scope_0)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L243)
	- [CallFailedStr(_srcChainId,_payload,_reason)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L241)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L198-L245


 - [ ] ID-121
Reentrancy in [AirdropBroker.exerciseOption(uint256,ERC20,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L224-L276):
	External calls:
	- [_processOTCDeal(_paymentToken,paymentTokenOracle,chosenAmount,aoTapOption.discount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L262-L267)
		- [(paymentTokenValuation) = _paymentTokenOracle.oracle.get(_paymentTokenOracle.oracleData)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L497-L499)
		- [_paymentToken.transferFrom(msg.sender,address(this),discountedPaymentAmount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L509-L513)
		- [tapOFT.transfer(msg.sender,tapAmount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L514)
	Event emitted after the call(s):
	- [ExerciseOption(cachedEpoch,msg.sender,_paymentToken,_aoTAPTokenID,chosenAmount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L269-L275)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L224-L276


 - [ ] ID-122
Reentrancy in [BaseTapOFT._unlockTwTapPosition(uint16,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L291-L324):
	External calls:
	- [_amount = twTap.exitPositionAndSendTap(tokenID)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L310-L323)
	Event emitted after the call(s):
	- [CallFailedBytes(_srcChainId,_payload,_reason_scope_0)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L322)
	- [CallFailedStr(_srcChainId,_payload,_reason)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L320)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L291-L324


 - [ ] ID-123
Reentrancy in [TapiocaOptionLiquidityProvision.lock(address,IERC20,uint128,uint128)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L171-L201):
	External calls:
	- [yieldBox.transfer(msg.sender,address(this),sglAssetID,sharesIn)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L186)
	- [_safeMint(_to,tokenId)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L191)
		- [retval = IERC721Receiver(to).onERC721Received(_msgSender(),from,tokenId,data)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L436-L447)
	Event emitted after the call(s):
	- [Mint(_to,uint128(sglAssetID),lockPosition)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L200)
	- [Transfer(address(0),to,tokenId)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L305)
		- [_safeMint(_to,tokenId)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L191)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L171-L201


 - [ ] ID-124
Reentrancy in [TwTAP.participate(address,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L252-L348):
	External calls:
	- [tapOFT.transferFrom(msg.sender,address(this),_amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L260)
	Event emitted after the call(s):
	- [AMLDivergence(pool.cumulative,pool.averageMagnitude,pool.totalParticipants)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L301-L305)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L252-L348


 - [ ] ID-125
Reentrancy in [AirdropBroker.participate(bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L199-L218):
	External calls:
	- [aoTAPTokenID = _participatePhase1()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L208)
		- [oTAPTokenID = aoTAP.mint(msg.sender,expiry,uint128(PHASE_1_DISCOUNT),_eligibleAmount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L399-L404)
	- [aoTAPTokenID = _participatePhase2(_data)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L210)
		- [oTAPTokenID = aoTAP.mint(msg.sender,expiry,discount,eligibleAmount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L436)
	- [aoTAPTokenID = _participatePhase3(_data)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L212)
		- [oTAPTokenID = aoTAP.mint(msg.sender,expiry,discount,eligibleAmount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L461)
	- [aoTAPTokenID = _participatePhase4()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L214)
		- [oTAPTokenID = aoTAP.mint(msg.sender,expiry,uint128(PHASE_4_DISCOUNT),_eligibleAmount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L474-L479)
	Event emitted after the call(s):
	- [Participate(cachedEpoch,aoTAPTokenID)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L217)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L199-L218


 - [ ] ID-126
Reentrancy in [BaseTapOFT._lockTwTapPosition(uint16,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L125-L149):
	External calls:
	- [twTap.participate(to,amount,duration)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L138-L148)
	Event emitted after the call(s):
	- [Approval(owner,spender,amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L325)
		- [_transferFrom(address(this),to,amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L147)
	- [Approval(owner,spender,amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L325)
		- [_transferFrom(address(this),to,amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L144)
	- [CallFailedBytes(_srcChainId,_payload,_reason_scope_0)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L146)
	- [CallFailedStr(_srcChainId,_payload,_reason)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L143)
	- [Transfer(from,to,amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L245)
		- [_transferFrom(address(this),to,amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L147)
	- [Transfer(from,to,amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L245)
		- [_transferFrom(address(this),to,amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L144)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L125-L149


 - [ ] ID-127
Reentrancy in [AirdropBroker.newEpoch()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L280-L294):
	External calls:
	- [(_epochTAPValuation) = tapOracle.get(tapOracleData)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L291)
	Event emitted after the call(s):
	- [NewEpoch(epoch,epochTAPValuation)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L293)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L280-L294


 - [ ] ID-128
Reentrancy in [TapiocaOptionBroker.exerciseOption(uint256,ERC20,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L351-L409):
	External calls:
	- [_processOTCDeal(_paymentToken,paymentTokenOracle,chosenAmount,oTAPPosition.discount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L395-L400)
		- [(paymentTokenValuation) = _paymentTokenOracle.oracle.get(_paymentTokenOracle.oracleData)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L518-L520)
		- [_paymentToken.transferFrom(msg.sender,address(this),discountedPaymentAmount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L530-L534)
		- [tapOFT.extractTAP(msg.sender,tapAmount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L535)
	Event emitted after the call(s):
	- [ExerciseOption(cachedEpoch,msg.sender,_paymentToken,_oTAPTokenID,chosenAmount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L402-L408)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L351-L409


 - [ ] ID-129
Reentrancy in [BaseTapOFT.lockTwTapPosition(address,uint256,uint256,uint16,address,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L88-L123):
	External calls:
	- [_lzSend(lzDstChainId,lzPayload,address(msg.sender),zroPaymentAddress,adapterParams,msg.value)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L108-L115)
		- [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
	Event emitted after the call(s):
	- [SendToChain(lzDstChainId,msg.sender,LzLib.addressToBytes32(to),0)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L117-L122)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L88-L123


 - [ ] ID-130
Reentrancy in [TwTAP.participate(address,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L252-L348):
	External calls:
	- [tapOFT.transferFrom(msg.sender,address(this),_amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L260)
	- [_safeMint(_participant,tokenId)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L310)
		- [to.isContract()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L435)
		- [retval = IERC721Receiver(to).onERC721Received(_msgSender(),from,tokenId,data)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L436-L447)
	Event emitted after the call(s):
	- [Participate(_participant,_amount,multiplier)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L346)
	- [Transfer(address(0),to,tokenId)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L305)
		- [_safeMint(_participant,tokenId)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L310)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L252-L348


 - [ ] ID-131
Reentrancy in [TwTAP._releaseTap(uint256,address)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L522-L568):
	External calls:
	- [tapOFT.transfer(_to,releasedAmount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L565)
	Event emitted after the call(s):
	- [ExitPosition(_tokenId,releasedAmount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L567)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L522-L568


 - [ ] ID-132
Reentrancy in [TapiocaOptionBroker.exitPosition(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L296-L345):
	External calls:
	- [oTAP.burn(_oTAPTokenID)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L339)
	- [tOLP.transferFrom(address(this),otapOwner,oTAPPosition.tOLP)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L342)
	Event emitted after the call(s):
	- [ExitPosition(epoch,oTAPPosition.tOLP,lock.amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L344)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L296-L345


 - [ ] ID-133
Reentrancy in [BaseTapOFT.unlockTwTapPosition(address,uint256,uint16,address,bytes,ICommonOFT.LzCallParams)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L258-L289):
	External calls:
	- [_lzSend(lzDstChainId,lzPayload,address(msg.sender),zroPaymentAddress,adapterParams,msg.value)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L274-L281)
		- [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
	Event emitted after the call(s):
	- [SendToChain(lzDstChainId,msg.sender,LzLib.addressToBytes32(to),0)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L283-L288)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L258-L289


 - [ ] ID-134
Reentrancy in [TapiocaOptionBroker.participate(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L212-L292):
	External calls:
	- [tOLP.transferFrom(msg.sender,address(this),_tOLPTokenID)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L230)
	- [oTAPTokenID = oTAP.mint(msg.sender,lock.lockTime + lock.lockDuration,uint128(target),_tOLPTokenID)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L279-L284)
	Event emitted after the call(s):
	- [Participate(epoch,lock.sglAssetID,pool.totalDeposited,lock,target)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L285-L291)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L212-L292


 - [ ] ID-135
Reentrancy in [OFTCoreV2._sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,address,address,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L119-L131):
	External calls:
	- [_lzSend(_dstChainId,lzPayload,_refundAddress,_zroPaymentAddress,_adapterParams,msg.value)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L128)
		- [lzEndpoint.send{value: _nativeFee}(_dstChainId,trustedRemote,_payload,_refundAddress,_zroPaymentAddress,_adapterParams)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L53)
	Event emitted after the call(s):
	- [SendToChain(_dstChainId,_from,_toAddress,amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L130)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L119-L131


 - [ ] ID-136
Reentrancy in [OTAP.mint(address,uint128,uint128,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L96-L111):
	External calls:
	- [_safeMint(_to,tokenId)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L103)
		- [retval = IERC721Receiver(to).onERC721Received(_msgSender(),from,tokenId,data)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L436-L447)
	Event emitted after the call(s):
	- [Mint(_to,tokenId,option)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L110)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L96-L111


 - [ ] ID-137
Reentrancy in [TapiocaOptionBroker.participate(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L212-L292):
	External calls:
	- [tOLP.transferFrom(msg.sender,address(this),_tOLPTokenID)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L230)
	Event emitted after the call(s):
	- [AMLDivergence(epoch,pool.cumulative,pool.averageMagnitude,pool.totalParticipants)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L264-L269)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L212-L292


 - [ ] ID-138
Reentrancy in [TapiocaOptionLiquidityProvision.unlock(uint256,IERC20,address)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L207-L250):
	External calls:
	- [yieldBox.transfer(address(this),_to,lockPosition.sglAssetID,sharesOut)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L241-L246)
	Event emitted after the call(s):
	- [Burn(_to,lockPosition.sglAssetID,lockPosition)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L249)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L207-L250


## timestamp
Impact: Low
Confidence: Medium
 - [ ] ID-139
[TwTAP.getParticipation(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L155-L163) uses timestamp for comparisons
	Dangerous comparisons:
	- [participant.expiry < block.timestamp](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L159)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L155-L163


 - [ ] ID-140
[AirdropBroker.newEpoch()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L280-L294) uses timestamp for comparisons
	Dangerous comparisons:
	- [require(bool,string)(block.timestamp >= lastEpochUpdate + EPOCH_DURATION,adb: too soon)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L281-L284)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L280-L294


 - [ ] ID-141
[ERC20Permit.permit(address,address,uint256,uint256,uint8,bytes32,bytes32)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L49-L68) uses timestamp for comparisons
	Dangerous comparisons:
	- [require(bool,string)(block.timestamp <= deadline,ERC20Permit: expired deadline)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L58)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L49-L68


 - [ ] ID-142
[LTap.redeem()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L46-L51) uses timestamp for comparisons
	Dangerous comparisons:
	- [require(bool,string)(block.timestamp > lockedUntil,Still locked)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L47)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L46-L51


 - [ ] ID-143
[TapiocaOptionBroker.newEpoch()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L413-L432) uses timestamp for comparisons
	Dangerous comparisons:
	- [require(bool,string)(block.timestamp >= lastEpochUpdate + EPOCH_DURATION,tOB: too soon)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L414-L417)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L413-L432


 - [ ] ID-144
[Vesting.registerUser(address,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L130-L146) uses timestamp for comparisons
	Dangerous comparisons:
	- [start > 0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L131)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L130-L146


 - [ ] ID-145
[ERC721Permit.permit(address,uint256,uint256,uint8,bytes32,bytes32)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ERC4494.sol#L47-L74) uses timestamp for comparisons
	Dangerous comparisons:
	- [require(bool,string)(block.timestamp <= deadline,ERC721Permit: expired deadline)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ERC4494.sol#L55)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ERC4494.sol#L47-L74


 - [ ] ID-146
[TapiocaOptionLiquidityProvision.unlock(uint256,IERC20,address)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L207-L250) uses timestamp for comparisons
	Dangerous comparisons:
	- [require(bool,string)(block.timestamp >= lockPosition.lockTime + lockPosition.lockDuration,tOLP: Lock not expired)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L215-L219)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L207-L250


 - [ ] ID-147
[TwTAP.participate(address,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L252-L348) uses timestamp for comparisons
	Dangerous comparisons:
	- [hasVotingPower = _amount >= computeMinWeight(pool.totalDeposited,MIN_WEIGHT_FACTOR)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L275-L276)
	- [divergenceForce = _duration > pool.cumulative](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L284)
	- [pool.cumulative > pool.averageMagnitude](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L290)
	- [require(bool,string)(expiry < type()(uint56).max,twTAP: too long)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L313)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L252-L348


 - [ ] ID-148
[TwTAP.claimable(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L166-L242) uses timestamp for comparisons
	Dangerous comparisons:
	- [votes == 0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L179)
	- [week <= position.lastInactive](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L186)
	- [position.lastActive < week](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L189)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L166-L242


 - [ ] ID-149
[TapiocaOptionLiquidityProvision._isPositionActive(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L348-L354) uses timestamp for comparisons
	Dangerous comparisons:
	- [(lockPosition.lockTime + lockPosition.lockDuration) >= block.timestamp](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L351-L353)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L348-L354


 - [ ] ID-150
[TwTAP._releaseTap(uint256,address)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L522-L568) uses timestamp for comparisons
	Dangerous comparisons:
	- [require(bool,string)(position.expiry <= block.timestamp,twTAP: Lock not expired)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L530)
	- [pool.cumulative > position.averageMagnitude](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L544)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L522-L568


 - [ ] ID-151
[Vesting.init(IERC20,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L151-L162) uses timestamp for comparisons
	Dangerous comparisons:
	- [start > 0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L152)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L151-L162


 - [ ] ID-152
[TapOFT.extractTAP(address,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L220-L229) uses timestamp for comparisons
	Dangerous comparisons:
	- [require(bool,string)(emissionForWeek[week] >= _amount,exceeds allowable amount)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L225)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L220-L229


 - [ ] ID-153
[TapOFT.timestampToWeek(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L173-L182) uses timestamp for comparisons
	Dangerous comparisons:
	- [timestamp == 0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L176)
	- [timestamp < emissionsStartTime](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L179)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L173-L182


 - [ ] ID-154
[AirdropBroker.getOTCDealDetails(uint256,ERC20,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L141-L191) uses timestamp for comparisons
	Dangerous comparisons:
	- [require(bool,string)(aoTapOption.expiry > block.timestamp,adb: Option expired)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L158)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L141-L191


 - [ ] ID-155
[TwTAP.advanceWeek(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L397-L421) uses timestamp for comparisons
	Dangerous comparisons:
	- [goal - week > _limit](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L403)
	- [week < goal](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L408)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L397-L421


 - [ ] ID-156
[TapiocaOptionBroker.exitPosition(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L296-L345) uses timestamp for comparisons
	Dangerous comparisons:
	- [require(bool,string)(block.timestamp >= lock.lockTime + lock.lockDuration,tOB: Lock not expired)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L303-L306)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L296-L345


 - [ ] ID-157
[TwTAP.distributeReward(uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L429-L449) uses timestamp for comparisons
	Dangerous comparisons:
	- [require(bool,string)(lastProcessedWeek == currentWeek(),twTAP: Advance week first)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L433-L436)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L429-L449


 - [ ] ID-158
[AirdropBroker.exerciseOption(uint256,ERC20,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L224-L276) uses timestamp for comparisons
	Dangerous comparisons:
	- [require(bool,string)(aoTapOption.expiry > block.timestamp,adb: Option expired)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L233)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L224-L276


 - [ ] ID-159
[Vesting._vested(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L167-L173) uses timestamp for comparisons
	Dangerous comparisons:
	- [start == 0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L168)
	- [block.timestamp < start + cliff](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L170)
	- [block.timestamp >= start + duration](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L171)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L167-L173


 - [ ] ID-160
[Vesting.claim()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L110-L121) uses timestamp for comparisons
	Dangerous comparisons:
	- [start == 0 || seeded == 0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L111)
	- [_claimable == 0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L113)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L110-L121


## assembly
Impact: Informational
Confidence: High
 - [ ] ID-161
[BytesLib.toUint8(bytes,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L308-L317) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L312-L314)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L308-L317


 - [ ] ID-162
[BytesLib.concat(bytes,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L13-L89) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L23-L86)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L13-L89


 - [ ] ID-163
[FullMath.muldiv(uint256,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L6-L106) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L21-L25)
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L33-L35)
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L50-L52)
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L54-L57)
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L64-L66)
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L69-L71)
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L75-L77)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L6-L106


 - [ ] ID-164
[BytesLib.toUint16(bytes,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L319-L328) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L323-L325)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L319-L328


 - [ ] ID-165
[BytesLib.toUint128(bytes,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L363-L372) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L367-L369)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L363-L372


 - [ ] ID-166
[BytesLib.concat(bytes,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L13-L89) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L23-L86)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L13-L89


 - [ ] ID-167
[BytesLib.toUint64(bytes,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L341-L350) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L345-L347)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L341-L350


 - [ ] ID-168
[ExcessivelySafeCall.excessivelySafeCall(address,uint256,uint16,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L23-L58) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L37-L56)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L23-L58


 - [ ] ID-169
[BytesLib.slice(bytes,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L228-L295) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L242-L292)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L228-L295


 - [ ] ID-170
[LzLib.getGasLimit(bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L47-L52) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L49-L51)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L47-L52


 - [ ] ID-171
[ECDSA.tryRecover(bytes32,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L55-L72) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L63-L67)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L55-L72


 - [ ] ID-172
[BytesLib.toBytes32(bytes,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L385-L394) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L389-L391)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L385-L394


 - [ ] ID-173
[ExcessivelySafeCall.excessivelySafeStaticCall(address,uint256,uint16,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/ExcessivelySafeCall.sol#L75-L109) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/ExcessivelySafeCall.sol#L89-L107)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/ExcessivelySafeCall.sol#L75-L109


 - [ ] ID-174
[BytesLib.toUint96(bytes,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L352-L361) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L356-L358)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L352-L361


 - [ ] ID-175
[BytesLib.toAddress(bytes,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L297-L306) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L301-L303)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L297-L306


 - [ ] ID-176
[TwTAP._getChainId()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L571-L577) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L573-L575)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L571-L577


 - [ ] ID-177
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L66-L70)
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L86-L93)
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L100-L109)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-178
[BytesLib.equalStorage(bytes,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L439-L509) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L449-L506)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L439-L509


 - [ ] ID-179
[BytesLib.toUint32(bytes,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L330-L339) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L334-L336)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L330-L339


 - [ ] ID-180
[BytesLib.toBytes32(bytes,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L385-L394) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L389-L391)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L385-L394


 - [ ] ID-181
[MerkleProof._efficientHash(bytes32,bytes32)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/MerkleProof.sol#L215-L222) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/MerkleProof.sol#L217-L221)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/MerkleProof.sol#L215-L222


 - [ ] ID-182
[BytesLib.concatStorage(bytes,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L91-L226) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L92-L225)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L91-L226


 - [ ] ID-183
[BytesLib.toUint16(bytes,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L319-L328) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L323-L325)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L319-L328


 - [ ] ID-184
[Strings.toString(uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Strings.sol#L18-L38) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Strings.sol#L24-L26)
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Strings.sol#L30-L32)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Strings.sol#L18-L38


 - [ ] ID-185
[LzApp._getGasLimit(bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L63-L68) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L65-L67)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L63-L68


 - [ ] ID-186
[ERC721._checkOnERC721Received(address,address,uint256,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L429-L451) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L443-L445)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L429-L451


 - [ ] ID-187
[BaseBoringBatchable._getRevertMsg(bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L17-L26) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L21-L24)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L17-L26


 - [ ] ID-188
[BytesLib.toUint256(bytes,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L374-L383) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L378-L380)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L374-L383


 - [ ] ID-189
[BytesLib.equal(bytes,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L396-L437) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L399-L434)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L396-L437


 - [ ] ID-190
[BytesLib.toUint32(bytes,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L330-L339) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L334-L336)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L330-L339


 - [ ] ID-191
[BytesLib.concatStorage(bytes,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L92-L225)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91-L226


 - [ ] ID-192
[BytesLib.toUint8(bytes,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L308-L317) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L312-L314)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L308-L317


 - [ ] ID-193
[ExcessivelySafeCall.excessivelySafeStaticCall(address,uint256,uint16,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L75-L109) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L89-L107)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L75-L109


 - [ ] ID-194
[BytesLib.toAddress(bytes,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297-L306) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L301-L303)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297-L306


 - [ ] ID-195
[ExcessivelySafeCall.excessivelySafeCall(address,uint256,uint16,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/ExcessivelySafeCall.sol#L23-L58) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/ExcessivelySafeCall.sol#L37-L56)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/ExcessivelySafeCall.sol#L23-L58


 - [ ] ID-196
[Address._revert(bytes,string)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Address.sol#L231-L243) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Address.sol#L236-L239)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Address.sol#L231-L243


 - [ ] ID-197
[BytesLib.toUint128(bytes,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L363-L372) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L367-L369)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L363-L372


 - [ ] ID-198
[BytesLib.toUint256(bytes,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L374-L383) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L378-L380)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L374-L383


 - [ ] ID-199
[BytesLib.toUint64(bytes,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L341-L350) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L345-L347)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L341-L350


 - [ ] ID-200
[LzApp._getGasLimit(bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/lzApp/LzApp.sol#L63-L68) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/lzApp/LzApp.sol#L65-L67)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/lzApp/LzApp.sol#L63-L68


 - [ ] ID-201
[BytesLib.toUint96(bytes,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L352-L361) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L356-L358)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L352-L361


 - [ ] ID-202
[BytesLib.slice(bytes,uint256,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L228-L295) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L242-L292)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L228-L295


 - [ ] ID-203
[BytesLib.equalStorage(bytes,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L439-L509) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L449-L506)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L439-L509


 - [ ] ID-204
[BytesLib.equal(bytes,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L396-L437) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L399-L434)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L396-L437


 - [ ] ID-205
[ExcessivelySafeCall.swapSelector(bytes4,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/ExcessivelySafeCall.sol#L120-L135) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/ExcessivelySafeCall.sol#L126-L134)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/ExcessivelySafeCall.sol#L120-L135


 - [ ] ID-206
[ExcessivelySafeCall.swapSelector(bytes4,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L120-L135) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L126-L134)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L120-L135


 - [ ] ID-207
[LzLib.decodeAdapterParams(bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L55-L70) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L57-L60)
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L65-L68)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L55-L70


 - [ ] ID-208
[ONFT721Core._nonblockingLzReceive(uint16,bytes,uint64,bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L66-L89) uses assembly
	- [INLINE ASM](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L76-L78)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L66-L89


## boolean-equal
Impact: Informational
Confidence: High
 - [ ] ID-209
[AirdropBroker._participatePhase3(bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L442-L462) compares to a boolean constant:
	-[require(bool,string)(userParticipation[tokenIDToAddress][3] == false,adb: Already participated)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L449-L452)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L442-L462


 - [ ] ID-210
[AirdropBroker._participatePhase2(bytes)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L410-L437) compares to a boolean constant:
	-[require(bool,string)(userParticipation[msg.sender][subPhase] == false,adb: Already participated)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L425-L428)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L410-L437


## pragma
Impact: Informational
Confidence: High
 - [ ] ID-211
Different versions of Solidity are used:
	- Version used: ['0.8.18', '>=0.5.0', '>=0.6.0', '>=0.7.6', '>=0.8.0<0.9.0', '^0.8.0', '^0.8.1', '^0.8.18', '^0.8.9']
	- [0.8.18](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L2)
	- [>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroEndpoint.sol#L3)
	- [>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroReceiver.sol#L3)
	- [>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroUserApplicationConfig.sol#L3)
	- [>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/ICommonOFT.sol#L3)
	- [>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/IOFTReceiverV2.sol#L3)
	- [>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/IOFTV2.sol#L3)
	- [>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/interfaces/ILayerZeroEndpoint.sol#L3)
	- [>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/interfaces/ILayerZeroReceiver.sol#L3)
	- [>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/interfaces/ILayerZeroUserApplicationConfig.sol#L3)
	- [>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/IONFT721.sol#L3)
	- [>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/IONFT721Core.sol#L3)
	- [>=0.6.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L3)
	- [>=0.7.6](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L2)
	- [>=0.7.6](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/ExcessivelySafeCall.sol#L2)
	- [>=0.8.0<0.9.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L9)
	- [>=0.8.0<0.9.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L9)
	- [ABIEncoderV2](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L3)
	- [ABIEncoderV2](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L3)
	- [ABIEncoderV2](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L2)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L2)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC20.sol#L2)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/access/Ownable.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/security/Pausable.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/security/ReentrancyGuard.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC1155/IERC1155.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC1155/IERC1155Receiver.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/IERC721.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/extensions/IERC721Metadata.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Context.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Counters.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Strings.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/MerkleProof.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/introspection/ERC165.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/introspection/IERC165.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L4)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L3)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L3)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L3)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L3)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L3)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ERC4494.sol#L3)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/lzApp/LzApp.sol#L3)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/lzApp/NonblockingLzApp.sol#L3)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721.sol#L3)
	- [^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L3)
	- [^0.8.1](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Address.sol#L4)
	- [^0.8.18](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L2)
	- [^0.8.18](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L2)
	- [^0.8.18](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L2)
	- [^0.8.18](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L2)
	- [^0.8.18](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L2)
	- [^0.8.18](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L2)
	- [^0.8.18](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L2)
	- [^0.8.18](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L2)
	- [^0.8.18](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L2)
	- [^0.8.18](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L2)
	- [^0.8.18](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/tapioca-periph/contracts/interfaces/ICommonData.sol#L2)
	- [^0.8.18](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/tapioca-periph/contracts/interfaces/IMarket.sol#L2)
	- [^0.8.18](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/tapioca-periph/contracts/interfaces/IOracle.sol#L2)
	- [^0.8.18](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/tapioca-periph/contracts/interfaces/ISendFrom.sol#L2)
	- [^0.8.18](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/tapioca-periph/contracts/interfaces/ISingularity.sol#L2)
	- [^0.8.18](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/tapioca-periph/contracts/interfaces/ITapiocaOFT.sol#L2)
	- [^0.8.18](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/tapioca-periph/contracts/interfaces/ITapiocaOptionLiquidityProvision.sol#L2)
	- [^0.8.18](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/tapioca-periph/contracts/interfaces/ITapiocaOptionsBroker.sol#L2)
	- [^0.8.18](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/tapioca-periph/contracts/interfaces/IUSDO.sol#L2)
	- [^0.8.9](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/enums/YieldBoxTokenType.sol#L2)
	- [^0.8.9](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L2)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L2


## costly-loop
Impact: Informational
Confidence: Medium
 - [ ] ID-212
[TapiocaOptionLiquidityProvision.unregisterSingularity(IERC20)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L297-L329) has costly operations inside a loop:
	- [delete sglAssetIDToAddress[sglAssetID]](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L319)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L297-L329


 - [ ] ID-213
[TapiocaOptionLiquidityProvision.unregisterSingularity(IERC20)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L297-L329) has costly operations inside a loop:
	- [singularities.pop()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L313)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L297-L329


 - [ ] ID-214
[TapiocaOptionLiquidityProvision.unregisterSingularity(IERC20)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L297-L329) has costly operations inside a loop:
	- [delete activeSingularities[singularity]](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L311)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L297-L329


 - [ ] ID-215
[TapiocaOptionLiquidityProvision.unregisterSingularity(IERC20)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L297-L329) has costly operations inside a loop:
	- [singularities.pop()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L322)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L297-L329


 - [ ] ID-216
[TapiocaOptionLiquidityProvision.unregisterSingularity(IERC20)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L297-L329) has costly operations inside a loop:
	- [delete sglAssetIDToAddress[sglAssetID]](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L312)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L297-L329


 - [ ] ID-217
[TapiocaOptionLiquidityProvision.unregisterSingularity(IERC20)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L297-L329) has costly operations inside a loop:
	- [delete activeSingularities[singularity]](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L318)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L297-L329


## dead-code
Impact: Informational
Confidence: Medium
 - [ ] ID-218
[TwTAP._getChainId()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L571-L577) is never used and should be removed

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L571-L577


 - [ ] ID-219
[BaseTapOFT._callApproval(ICommonData.IApproval[])](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L332-L354) is never used and should be removed

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L332-L354


## solc-version
Impact: Informational
Confidence: High
 - [ ] ID-220
Pragma version[>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/IONFT721.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/IONFT721.sol#L3


 - [ ] ID-221
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L4


 - [ ] ID-222
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L4


 - [ ] ID-223
Pragma version[>=0.6.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L3


 - [ ] ID-224
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L4


 - [ ] ID-225
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC20.sol#L2) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC20.sol#L2


 - [ ] ID-226
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L4


 - [ ] ID-227
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol#L4


 - [ ] ID-228
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Context.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Context.sol#L4


 - [ ] ID-229
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L4


 - [ ] ID-230
Pragma version[>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/IONFT721Core.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/IONFT721Core.sol#L3


 - [ ] ID-231
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L3


 - [ ] ID-232
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/security/ReentrancyGuard.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/security/ReentrancyGuard.sol#L4


 - [ ] ID-233
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721.sol#L3


 - [ ] ID-234
Pragma version[>=0.7.6](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L2) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L2


 - [ ] ID-235
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Strings.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Strings.sol#L4


 - [ ] ID-236
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L3


 - [ ] ID-237
Pragma version[>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/interfaces/ILayerZeroUserApplicationConfig.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/interfaces/ILayerZeroUserApplicationConfig.sol#L3


 - [ ] ID-238
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/lzApp/NonblockingLzApp.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/lzApp/NonblockingLzApp.sol#L3


 - [ ] ID-239
Pragma version[>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/interfaces/ILayerZeroEndpoint.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/interfaces/ILayerZeroEndpoint.sol#L3


 - [ ] ID-240
Pragma version[>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroUserApplicationConfig.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroUserApplicationConfig.sol#L3


 - [ ] ID-241
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC1155/IERC1155Receiver.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC1155/IERC1155Receiver.sol#L4


 - [ ] ID-242
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/MerkleProof.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/MerkleProof.sol#L4


 - [ ] ID-243
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol#L4


 - [ ] ID-244
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L4


 - [ ] ID-245
Pragma version[^0.8.1](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Address.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Address.sol#L4


 - [ ] ID-246
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L3


 - [ ] ID-247
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L3


 - [ ] ID-248
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L3


 - [ ] ID-249
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/extensions/IERC721Metadata.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/extensions/IERC721Metadata.sol#L4


 - [ ] ID-250
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Counters.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Counters.sol#L4


 - [ ] ID-251
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol#L4


 - [ ] ID-252
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ERC4494.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ERC4494.sol#L3


 - [ ] ID-253
Pragma version[>=0.8.0<0.9.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L9) is too complex

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L9


 - [ ] ID-254
Pragma version[>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroReceiver.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroReceiver.sol#L3


 - [ ] ID-255
Pragma version[>=0.7.6](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/ExcessivelySafeCall.sol#L2) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/ExcessivelySafeCall.sol#L2


 - [ ] ID-256
Pragma version[>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroEndpoint.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/interfaces/ILayerZeroEndpoint.sol#L3


 - [ ] ID-257
Pragma version[^0.8.9](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L2) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L2


 - [ ] ID-258
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/introspection/ERC165.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/introspection/ERC165.sol#L4


 - [ ] ID-259
Pragma version[>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/ICommonOFT.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/ICommonOFT.sol#L3


 - [ ] ID-260
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L4


 - [ ] ID-261
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/lzApp/LzApp.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/lzApp/LzApp.sol#L3


 - [ ] ID-262
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L2) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L2


 - [ ] ID-263
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/security/Pausable.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/security/Pausable.sol#L4


 - [ ] ID-264
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/IERC721.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/IERC721.sol#L4


 - [ ] ID-265
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L3


 - [ ] ID-266
Pragma version[>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/IOFTReceiverV2.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/IOFTReceiverV2.sol#L3


 - [ ] ID-267
Pragma version[>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/interfaces/ILayerZeroReceiver.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/interfaces/ILayerZeroReceiver.sol#L3


 - [ ] ID-268
Pragma version[>=0.8.0<0.9.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L9) is too complex

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L9


 - [ ] ID-269
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/access/Ownable.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/access/Ownable.sol#L4


 - [ ] ID-270
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/introspection/IERC165.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/introspection/IERC165.sol#L4


 - [ ] ID-271
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L4


 - [ ] ID-272
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L2) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L2


 - [ ] ID-273
Pragma version[^0.8.9](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/enums/YieldBoxTokenType.sol#L2) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/enums/YieldBoxTokenType.sol#L2


 - [ ] ID-274
Pragma version[>=0.5.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/IOFTV2.sol#L3) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/IOFTV2.sol#L3


 - [ ] ID-275
Pragma version[^0.8.0](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC1155/IERC1155.sol#L4) allows old versions

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC1155/IERC1155.sol#L4


## low-level-calls
Impact: Informational
Confidence: High
 - [ ] ID-276
Low level call in [Address.functionCallWithValue(address,bytes,uint256,string)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Address.sol#L128-L137):
	- [(success,returndata) = target.call{value: value}(data)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Address.sol#L135)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Address.sol#L128-L137


 - [ ] ID-277
Low level call in [BaseBoringBatchable.batch(bytes[],bool)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L35-L42):
	- [(success,result) = address(this).delegatecall(calls[i])](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L37)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L35-L42


 - [ ] ID-278
Low level call in [Address.sendValue(address,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Address.sol#L60-L65):
	- [(success) = recipient.call{value: amount}()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Address.sol#L63)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Address.sol#L60-L65


 - [ ] ID-279
Low level call in [Address.functionStaticCall(address,bytes,string)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Address.sol#L155-L162):
	- [(success,returndata) = target.staticcall(data)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Address.sol#L160)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Address.sol#L155-L162


 - [ ] ID-280
Low level call in [Address.functionDelegateCall(address,bytes,string)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Address.sol#L180-L187):
	- [(success,returndata) = target.delegatecall(data)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Address.sol#L185)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/Address.sol#L180-L187


## naming-convention
Impact: Informational
Confidence: High
 - [ ] ID-281
Parameter [BaseOFTV2.estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)._dstGasForCall](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36


 - [ ] ID-282
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._srcChainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-283
Parameter [BaseOFTV2.sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,ICommonOFT.LzCallParams)._dstGasForCall](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21


 - [ ] ID-284
Parameter [OTAP.isApprovedOrOwner(address,uint256)._spender](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L61) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L61


 - [ ] ID-285
Parameter [BytesLib.equalStorage(bytes,bytes)._preBytes](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L440) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L440


 - [ ] ID-286
Parameter [LzApp.setConfig(uint16,uint16,uint256,bytes)._version](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84


 - [ ] ID-287
Parameter [AirdropBroker.setPaymentToken(ERC20,IOracle,bytes)._paymentToken](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L345) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L345


 - [ ] ID-288
Parameter [ONFT721Core.estimateSendFee(uint16,bytes,uint256,bool,bytes)._useZro](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L33) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L33


 - [ ] ID-289
Parameter [TwTAP.exitPositionAndSendTap(uint256)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L388) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L388


 - [ ] ID-290
Parameter [TWAML.computeMagnitude(uint256,uint256)._cumulative](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L125) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L125


 - [ ] ID-291
Parameter [ExcessivelySafeCall.swapSelector(bytes4,bytes)._newSelector](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L120) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L120


 - [ ] ID-292
Variable [AirdropBroker.PHASE_2_AMOUNT_PER_USER](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L77) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L77


 - [ ] ID-293
Variable [AirdropBroker.PHASE_2_DISCOUNT_PER_USER](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L78) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L78


 - [ ] ID-294
Parameter [ONFT721Core.sendFrom(address,uint16,bytes,uint256,address,address,bytes)._zroPaymentAddress](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L42) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L42


 - [ ] ID-295
Parameter [BytesLib.concatStorage(bytes,bytes)._postBytes](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91


 - [ ] ID-296
Parameter [AirdropBroker.registerUserForPhase(uint256,address[],uint256[])._phase](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L325) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L325


 - [ ] ID-297
Parameter [LzApp.setTrustedRemoteAddress(uint16,bytes)._remoteChainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L107) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L107


 - [ ] ID-298
Parameter [AirdropBroker.participate(bytes)._data](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L200) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L200


 - [ ] ID-299
Parameter [TwTAP.participate(address,uint256,uint256)._participant](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L253) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L253


 - [ ] ID-300
Parameter [ExcessivelySafeCall.swapSelector(bytes4,bytes)._buf](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L120) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L120


 - [ ] ID-301
Parameter [BytesLib.toUint128(bytes,uint256)._start](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L363) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L363


 - [ ] ID-302
Parameter [AirdropBroker.setPhase2MerkleRoots(bytes32[4])._merkleRoots](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L319) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L319


 - [ ] ID-303
Parameter [BytesLib.equal(bytes,bytes)._preBytes](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L396) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L396


 - [ ] ID-304
Parameter [BytesLib.equalStorage(bytes,bytes)._postBytes](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L441) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L441


 - [ ] ID-305
Parameter [OTAP.tokenURI(uint256)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L55) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L55


 - [ ] ID-306
Parameter [BaseOFTV2.sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,ICommonOFT.LzCallParams)._amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21


 - [ ] ID-307
Parameter [BytesLib.toUint64(bytes,uint256)._bytes](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L341) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L341


 - [ ] ID-308
Parameter [AirdropBroker.setTapOracle(IOracle,bytes)._tapOracle](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L309) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L309


 - [ ] ID-309
Parameter [AirdropBroker.getOTCDealDetails(uint256,ERC20,uint256)._aoTAPTokenID](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L142) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L142


 - [ ] ID-310
Parameter [BytesLib.toBytes32(bytes,uint256)._bytes](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L385) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L385


 - [ ] ID-311
Parameter [LzApp.setTrustedRemote(uint16,bytes)._path](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L102) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L102


 - [ ] ID-312
Constant [TapOFT.decay_rate](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L45) is not in UPPER_CASE_WITH_UNDERSCORES

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L45


 - [ ] ID-313
Parameter [ONFT721Core.estimateSendBatchFee(uint16,bytes,uint256[],bool,bytes)._tokenIds](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L37) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L37


 - [ ] ID-314
Parameter [BaseOFTV2.sendFrom(address,uint16,bytes32,uint256,ICommonOFT.LzCallParams)._callParams](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17


 - [ ] ID-315
Parameter [TapiocaOptionLiquidityProvision.getTotalPoolDeposited(uint256)._sglAssetId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L147) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L147


 - [ ] ID-316
Parameter [LzApp.isTrustedRemote(uint16,bytes)._srcAddress](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L135) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L135


 - [ ] ID-317
Parameter [OTAP.setTokenURI(uint256,string)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L83) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L83


 - [ ] ID-318
Parameter [OTAP.mint(address,uint128,uint128,uint256)._discount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L99) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L99


 - [ ] ID-319
Parameter [TapiocaOptionLiquidityProvision.unlock(uint256,IERC20,address)._to](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L210) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L210


 - [ ] ID-320
Parameter [LzLib.buildAdapterParams(LzLib.AirdropParams,uint256)._airdropParams](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L21) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L21


 - [ ] ID-321
Parameter [TapOFT.setGovernanceChainIdentifier(uint256)._identifier](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L141) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L141


 - [ ] ID-322
Parameter [ONFT721Core.estimateSendBatchFee(uint16,bytes,uint256[],bool,bytes)._dstChainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L37) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L37


 - [ ] ID-323
Parameter [AOTAP.attributes(uint256)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L83) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L83


 - [ ] ID-324
Parameter [TapiocaOptionBroker.collectPaymentTokens(address[])._paymentTokens](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L480) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L480


 - [ ] ID-325
Parameter [BytesLib.toAddress(bytes,uint256)._start](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297


 - [ ] ID-326
Variable [TwTAP.HOST_CHAIN_ID](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L111) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L111


 - [ ] ID-327
Parameter [LzApp.setConfig(uint16,uint16,uint256,bytes)._chainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84


 - [ ] ID-328
Parameter [ONFT721Core.estimateSendBatchFee(uint16,bytes,uint256[],bool,bytes)._adapterParams](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L37) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L37


 - [ ] ID-329
Parameter [BytesLib.toUint8(bytes,uint256)._start](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L308) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L308


 - [ ] ID-330
Parameter [TapiocaOptionLiquidityProvision.isApprovedOrOwner(address,uint256)._spender](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L155) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L155


 - [ ] ID-331
Parameter [LzApp.forceResumeReceive(uint16,bytes)._srcAddress](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L96) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L96


 - [ ] ID-332
Parameter [NonblockingLzApp.retryMessage(uint16,bytes,uint64,bytes)._nonce](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46


 - [ ] ID-333
Parameter [ONFT721Core.sendFrom(address,uint16,bytes,uint256,address,address,bytes)._dstChainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L42) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L42


 - [ ] ID-334
Parameter [BytesLib.toUint8(bytes,uint256)._bytes](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L308) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L308


 - [ ] ID-335
Parameter [ONFT721Core.sendFrom(address,uint16,bytes,uint256,address,address,bytes)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L42) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L42


 - [ ] ID-336
Parameter [ExcessivelySafeCall.excessivelySafeStaticCall(address,uint256,uint16,bytes)._calldata](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L79) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L79


 - [ ] ID-337
Parameter [ONFT721Core.estimateSendFee(uint16,bytes,uint256,bool,bytes)._toAddress](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L33) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L33


 - [ ] ID-338
Parameter [BytesLib.toBytes32(bytes,uint256)._start](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L385) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L385


 - [ ] ID-339
Parameter [ONFT721Core.setDstChainIdToBatchLimit(uint16,uint256)._dstChainIdToBatchLimit](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L140) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L140


 - [ ] ID-340
Parameter [BaseOFTV2.estimateSendFee(uint16,bytes32,uint256,bool,bytes)._adapterParams](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32


 - [ ] ID-341
Parameter [ONFT721Core.sendBatchFrom(address,uint16,bytes,uint256[],address,address,bytes)._refundAddress](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L46) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L46


 - [ ] ID-342
Parameter [TwTAP.getParticipation(uint256)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L156) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L156


 - [ ] ID-343
Parameter [ExcessivelySafeCall.excessivelySafeCall(address,uint256,uint16,bytes)._maxCopy](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L26) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L26


 - [ ] ID-344
Parameter [TwTAP.claimable(uint256)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L167) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L167


 - [ ] ID-345
Parameter [TWAML.computeTarget(uint256,uint256,uint256,uint256)._magnitude](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L135) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L135


 - [ ] ID-346
Parameter [BytesLib.toAddress(bytes,uint256)._bytes](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297


 - [ ] ID-347
Parameter [LzApp.setReceiveVersion(uint16)._version](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L92) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L92


 - [ ] ID-348
Parameter [BaseOFTV2.estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)._amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36


 - [ ] ID-349
Parameter [TapiocaOptionBroker.setPaymentToken(ERC20,IOracle,bytes)._paymentToken](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L459) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L459


 - [ ] ID-350
Parameter [TWAML.computeMinWeight(uint256,uint256)._totalWeight](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L116) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L116


 - [ ] ID-351
Parameter [TwTAP.exitPosition(uint256)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L380) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L380


 - [ ] ID-352
Parameter [BaseOFTV2.sendFrom(address,uint16,bytes32,uint256,ICommonOFT.LzCallParams)._toAddress](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17


 - [ ] ID-353
Parameter [BaseOFTV2.sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,ICommonOFT.LzCallParams)._payload](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21


 - [ ] ID-354
Parameter [LzApp.lzReceive(uint16,bytes,uint64,bytes)._srcChainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35


 - [ ] ID-355
Parameter [ExcessivelySafeCall.excessivelySafeCall(address,uint256,uint16,bytes)._calldata](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L27) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L27


 - [ ] ID-356
Parameter [TapiocaOptionBroker.exerciseOption(uint256,ERC20,uint256)._oTAPTokenID](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L352) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L352


 - [ ] ID-357
Parameter [BytesLib.toUint128(bytes,uint256)._bytes](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L363) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L363


 - [ ] ID-358
Parameter [LzLib.decodeAdapterParams(bytes)._adapterParams](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L55) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L55


 - [ ] ID-359
Parameter [TapiocaOptionLiquidityProvision.unlock(uint256,IERC20,address)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L208) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L208


 - [ ] ID-360
Parameter [OFTCoreV2.setUseCustomAdapterParams(bool)._useCustomAdapterParams](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L62) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L62


 - [ ] ID-361
Parameter [TapOFT.extractTAP(address,uint256)._to](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L220) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L220


 - [ ] ID-362
Parameter [ONFT721Core.sendBatchFrom(address,uint16,bytes,uint256[],address,address,bytes)._tokenIds](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L46) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L46


 - [ ] ID-363
Parameter [AirdropBroker.collectPaymentTokens(address[])._paymentTokens](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L366) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L366


 - [ ] ID-364
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._srcAddress](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-365
Constant [TwTAP.dMIN](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L83) is not in UPPER_CASE_WITH_UNDERSCORES

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L83


 - [ ] ID-366
Parameter [TapOFT.extractTAP(address,uint256)._amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L220) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L220


 - [ ] ID-367
Parameter [TapiocaOptionLiquidityProvision.lock(address,IERC20,uint128,uint128)._amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L175) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L175


 - [ ] ID-368
Parameter [TapiocaOptionLiquidityProvision.lock(address,IERC20,uint128,uint128)._to](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L172) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L172


 - [ ] ID-369
Parameter [AOTAP.mint(address,uint128,uint128,uint256)._to](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L110) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L110


 - [ ] ID-370
Parameter [BaseOFTV2.sendFrom(address,uint16,bytes32,uint256,ICommonOFT.LzCallParams)._dstChainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17


 - [ ] ID-371
Parameter [TapiocaOptionBroker.getOTCDealDetails(uint256,ERC20,uint256)._oTAPTokenID](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L146) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L146


 - [ ] ID-372
Parameter [ONFT721Core.setMinGasToTransferAndStore(uint256)._minGasToTransferAndStore](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L128) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L128


 - [ ] ID-373
Parameter [BytesLib.toUint32(bytes,uint256)._bytes](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L330) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L330


 - [ ] ID-374
Parameter [Vesting.registerUser(address,uint256)._user](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L130) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L130


 - [ ] ID-375
Parameter [AirdropBroker.registerUserForPhase(uint256,address[],uint256[])._users](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L326) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L326


 - [ ] ID-376
Parameter [ONFT721Core.sendBatchFrom(address,uint16,bytes,uint256[],address,address,bytes)._zroPaymentAddress](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L46) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L46


 - [ ] ID-377
Parameter [BaseOFTV2.estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)._toAddress](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36


 - [ ] ID-378
Parameter [AirdropBroker.setTapOracle(IOracle,bytes)._tapOracleData](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L310) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L310


 - [ ] ID-379
Parameter [BaseOFTV2.estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)._dstChainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36


 - [ ] ID-380
Parameter [AirdropBroker.getOTCDealDetails(uint256,ERC20,uint256)._paymentToken](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L143) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L143


 - [ ] ID-381
Parameter [AOTAP.mint(address,uint128,uint128,uint256)._amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L113) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L113


 - [ ] ID-382
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._nonce](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-383
Parameter [NonblockingLzApp.retryMessage(uint16,bytes,uint64,bytes)._payload](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46


 - [ ] ID-384
Parameter [NonblockingLzApp.nonblockingLzReceive(uint16,bytes,uint64,bytes)._payload](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37


 - [ ] ID-385
Parameter [AOTAP.isApprovedOrOwner(address,uint256)._spender](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L75) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L75


 - [ ] ID-386
Parameter [TapiocaOptionBroker.participate(uint256)._tOLPTokenID](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L213) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L213


 - [ ] ID-387
Parameter [TapiocaOptionLiquidityProvision.unlock(uint256,IERC20,address)._singularity](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L209) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L209


 - [ ] ID-388
Parameter [OTAP.burn(uint256)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L115) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L115


 - [ ] ID-389
Parameter [TwTAP.claimRewards(uint256,address)._to](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L353) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L353


 - [ ] ID-390
Parameter [LzApp.setTrustedRemote(uint16,bytes)._srcChainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L102) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L102


 - [ ] ID-391
Parameter [TapiocaOptionBroker.exitPosition(uint256)._oTAPTokenID](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L296) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L296


 - [ ] ID-392
Parameter [BytesLib.equal(bytes,bytes)._postBytes](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L396) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L396


 - [ ] ID-393
Variable [AirdropBroker.PCNFT](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L48) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L48


 - [ ] ID-394
Parameter [TwTAP.claimRewards(uint256,address)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L353) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L353


 - [ ] ID-395
Parameter [LzApp.setMinDstGas(uint16,uint16,uint256)._dstChainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L123) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L123


 - [ ] ID-396
Parameter [BytesLib.toUint256(bytes,uint256)._start](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L374) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L374


 - [ ] ID-397
Parameter [TWAML.computeTarget(uint256,uint256,uint256,uint256)._dMin](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L133) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L133


 - [ ] ID-398
Parameter [BaseOFTV2.sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,ICommonOFT.LzCallParams)._callParams](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21


 - [ ] ID-399
Parameter [TapiocaOptionBroker.setTapOracle(IOracle,bytes)._tapOracleData](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L448) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L448


 - [ ] ID-400
Parameter [LzApp.lzReceive(uint16,bytes,uint64,bytes)._payload](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35


 - [ ] ID-401
Parameter [ONFT721Core.sendFrom(address,uint16,bytes,uint256,address,address,bytes)._refundAddress](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L42) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L42


 - [ ] ID-402
Parameter [BytesLib.toUint256(bytes,uint256)._bytes](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L374) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L374


 - [ ] ID-403
Variable [TapOFT.dso_supply](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L42) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L42


 - [ ] ID-404
Parameter [OTAP.attributes(uint256)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L69) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L69


 - [ ] ID-405
Parameter [LzApp.setMinDstGas(uint16,uint16,uint256)._packetType](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L123) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L123


 - [ ] ID-406
Parameter [LzApp.setTrustedRemoteAddress(uint16,bytes)._remoteAddress](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L107) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L107


 - [ ] ID-407
Parameter [ONFT721Core.sendFrom(address,uint16,bytes,uint256,address,address,bytes)._toAddress](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L42) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L42


 - [ ] ID-408
Parameter [LzLib.buildAirdropAdapterParams(uint256,LzLib.AirdropParams)._params](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L37) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L37


 - [ ] ID-409
Parameter [TapiocaOptionBroker.getOTCDealDetails(uint256,ERC20,uint256)._paymentToken](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L147) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L147


 - [ ] ID-410
Parameter [BaseOFTV2.estimateSendFee(uint16,bytes32,uint256,bool,bytes)._toAddress](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32


 - [ ] ID-411
Parameter [Vesting.claimable(address)._user](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L85) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L85


 - [ ] ID-412
Parameter [AirdropBroker.setPaymentToken(ERC20,IOracle,bytes)._oracleData](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L347) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L347


 - [ ] ID-413
Parameter [TwTAP.participate(address,uint256,uint256)._duration](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L255) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L255


 - [ ] ID-414
Parameter [LzApp.getConfig(uint16,uint16,address,uint256)._version](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L79) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L79


 - [ ] ID-415
Variable [EIP712._TYPE_HASH](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L37) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L37


 - [ ] ID-416
Parameter [TapiocaOptionBroker.setTapOracle(IOracle,bytes)._tapOracle](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L447) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L447


 - [ ] ID-417
Parameter [AOTAP.mint(address,uint128,uint128,uint256)._discount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L112) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L112


 - [ ] ID-418
Parameter [ONFT721Core.sendBatchFrom(address,uint16,bytes,uint256[],address,address,bytes)._toAddress](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L46) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L46


 - [ ] ID-419
Parameter [TwTAP.participate(address,uint256,uint256)._amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L254) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L254


 - [ ] ID-420
Parameter [ONFT721Core.sendFrom(address,uint16,bytes,uint256,address,address,bytes)._from](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L42) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L42


 - [ ] ID-421
Parameter [TapiocaOptionBroker.exerciseOption(uint256,ERC20,uint256)._paymentToken](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L353) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L353


 - [ ] ID-422
Parameter [AOTAP.tokenURI(uint256)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L69) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L69


 - [ ] ID-423
Parameter [BytesLib.concatStorage(bytes,bytes)._preBytes](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L91


 - [ ] ID-424
Parameter [ONFT721Core.clearCredits(bytes)._payload](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L92) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L92


 - [ ] ID-425
Parameter [LzApp.lzReceive(uint16,bytes,uint64,bytes)._srcAddress](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35


 - [ ] ID-426
Constant [TapiocaOptionBroker.dMAX](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L76) is not in UPPER_CASE_WITH_UNDERSCORES

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L76


 - [ ] ID-427
Parameter [BaseOFTV2.estimateSendFee(uint16,bytes32,uint256,bool,bytes)._amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32


 - [ ] ID-428
Parameter [LzApp.getConfig(uint16,uint16,address,uint256)._chainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L79) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L79


 - [ ] ID-429
Parameter [LzApp.setMinDstGas(uint16,uint16,uint256)._minGas](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L123) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L123


 - [ ] ID-430
Parameter [TwTAP.distributeReward(uint256,uint256)._rewardTokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L430) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L430


 - [ ] ID-431
Parameter [LzApp.isTrustedRemote(uint16,bytes)._srcChainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L135) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L135


 - [ ] ID-432
Parameter [TwTAP.claimAndSendRewards(uint256,IERC20[])._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L362) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L362


 - [ ] ID-433
Parameter [BytesLib.slice(bytes,uint256,uint256)._start](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L230) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L230


 - [ ] ID-434
Parameter [AirdropBroker.exerciseOption(uint256,ERC20,uint256)._paymentToken](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L226) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L226


 - [ ] ID-435
Parameter [ONFT721Core.sendFrom(address,uint16,bytes,uint256,address,address,bytes)._adapterParams](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L42) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L42


 - [ ] ID-436
Parameter [LzApp.forceResumeReceive(uint16,bytes)._srcChainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L96) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L96


 - [ ] ID-437
Parameter [AirdropBroker.exerciseOption(uint256,ERC20,uint256)._tapAmount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L227) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L227


 - [ ] ID-438
Parameter [BaseOFTV2.estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)._payload](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36


 - [ ] ID-439
Parameter [BytesLib.concat(bytes,bytes)._preBytes](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L14) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L14


 - [ ] ID-440
Parameter [LzLib.buildAirdropAdapterParams(uint256,LzLib.AirdropParams)._uaGas](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L37) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L37


 - [ ] ID-441
Parameter [ExcessivelySafeCall.excessivelySafeCall(address,uint256,uint16,bytes)._gas](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L25) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L25


 - [ ] ID-442
Variable [EIP712._CACHED_THIS](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L33) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L33


 - [ ] ID-443
Parameter [NonblockingLzApp.nonblockingLzReceive(uint16,bytes,uint64,bytes)._nonce](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37


 - [ ] ID-444
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._to](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-445
Parameter [ExcessivelySafeCall.excessivelySafeStaticCall(address,uint256,uint16,bytes)._maxCopy](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L78) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L78


 - [ ] ID-446
Parameter [BaseOFTV2.sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,ICommonOFT.LzCallParams)._toAddress](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21


 - [ ] ID-447
Parameter [LzLib.buildAdapterParams(LzLib.AirdropParams,uint256)._uaGasLimit](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L21) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L21


 - [ ] ID-448
Parameter [BaseOFTV2.sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,ICommonOFT.LzCallParams)._from](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21


 - [ ] ID-449
Parameter [AirdropBroker.setPaymentTokenBeneficiary(address)._paymentTokenBeneficiary](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L358) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L358


 - [ ] ID-450
Parameter [LTap.setLockedUntil(uint256)._lockedUntil](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L53) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L53


 - [ ] ID-451
Parameter [TwTAP.claimAndSendRewards(uint256,IERC20[])._rewardTokens](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L363) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L363


 - [ ] ID-452
Parameter [BytesLib.slice(bytes,uint256,uint256)._bytes](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L229) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L229


 - [ ] ID-453
Constant [TwTAP.dMAX](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L82) is not in UPPER_CASE_WITH_UNDERSCORES

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L82


 - [ ] ID-454
Parameter [TapOFT.setMinter(address)._minter](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L160) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L160


 - [ ] ID-455
Parameter [NonblockingLzApp.retryMessage(uint16,bytes,uint64,bytes)._srcAddress](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46


 - [ ] ID-456
Variable [ERC20Permit._PERMIT_TYPEHASH_DEPRECATED_SLOT](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L37) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L37


 - [ ] ID-457
Function [IERC20Permit.DOMAIN_SEPARATOR()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L59) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L59


 - [ ] ID-458
Parameter [ONFT721Core.estimateSendFee(uint16,bytes,uint256,bool,bytes)._dstChainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L33) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L33


 - [ ] ID-459
Parameter [TwTAP.releaseTap(uint256,address)._to](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L373) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L373


 - [ ] ID-460
Parameter [NonblockingLzApp.retryMessage(uint16,bytes,uint64,bytes)._srcChainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L46


 - [ ] ID-461
Parameter [ONFT721Core.sendBatchFrom(address,uint16,bytes,uint256[],address,address,bytes)._adapterParams](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L46) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L46


 - [ ] ID-462
Parameter [ExcessivelySafeCall.excessivelySafeStaticCall(address,uint256,uint16,bytes)._gas](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L77) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L77


 - [ ] ID-463
Parameter [BaseOFTV2.estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)._adapterParams](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36


 - [ ] ID-464
Parameter [LzApp.setPayloadSizeLimit(uint16,uint256)._dstChainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L130) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L130


 - [ ] ID-465
Parameter [LzLib.bytes32ToAddress(bytes32)._bytes32Address](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L74) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L74


 - [ ] ID-466
Parameter [OFTV2.setLdChain(uint16,bool)._isLdChain](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L36


 - [ ] ID-467
Parameter [BaseOFTV2.sendAndCall(address,uint16,bytes32,uint256,bytes,uint64,ICommonOFT.LzCallParams)._dstChainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L21


 - [ ] ID-468
Parameter [BaseOFTV2.estimateSendFee(uint16,bytes32,uint256,bool,bytes)._useZro](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32


 - [ ] ID-469
Parameter [TapiocaOptionBroker.getOTCDealDetails(uint256,ERC20,uint256)._tapAmount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L148) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L148


 - [ ] ID-470
Parameter [OTAP.isApprovedOrOwner(address,uint256)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L62) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L62


 - [ ] ID-471
Variable [EIP712._CACHED_CHAIN_ID](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L32) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L32


 - [ ] ID-472
Parameter [ONFT721Core.estimateSendFee(uint16,bytes,uint256,bool,bytes)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L33) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L33


 - [ ] ID-473
Parameter [ExcessivelySafeCall.excessivelySafeCall(address,uint256,uint16,bytes)._target](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L24) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L24


 - [ ] ID-474
Parameter [ONFT721Core.estimateSendBatchFee(uint16,bytes,uint256[],bool,bytes)._toAddress](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L37) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L37


 - [ ] ID-475
Parameter [TapOFT.removeTAP(uint256)._amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L233) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L233


 - [ ] ID-476
Parameter [BaseOFTV2.sendFrom(address,uint16,bytes32,uint256,ICommonOFT.LzCallParams)._amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17


 - [ ] ID-477
Function [ERC20Permit.DOMAIN_SEPARATOR()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L81-L83) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L81-L83


 - [ ] ID-478
Parameter [BaseOFTV2.sendFrom(address,uint16,bytes32,uint256,ICommonOFT.LzCallParams)._from](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L17


 - [ ] ID-479
Parameter [TWAML.computeTarget(uint256,uint256,uint256,uint256)._dMax](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L134) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L134


 - [ ] ID-480
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._payload](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-481
Parameter [TapiocaOptionBroker.setPaymentToken(ERC20,IOracle,bytes)._oracle](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L460) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L460


 - [ ] ID-482
Parameter [Vesting.vested(address)._user](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L96) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L96


 - [ ] ID-483
Parameter [TapiocaOptionBroker.exerciseOption(uint256,ERC20,uint256)._tapAmount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L354) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L354


 - [ ] ID-484
Parameter [NonblockingLzApp.nonblockingLzReceive(uint16,bytes,uint64,bytes)._srcAddress](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37


 - [ ] ID-485
Parameter [BytesLib.toUint16(bytes,uint256)._start](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L319) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L319


 - [ ] ID-486
Parameter [TapiocaOptionLiquidityProvision.lock(address,IERC20,uint128,uint128)._lockDuration](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L174) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L174


 - [ ] ID-487
Parameter [TapiocaOptionLiquidityProvision.getLock(uint256)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L113) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L113


 - [ ] ID-488
Parameter [OTAP.mint(address,uint128,uint128,uint256)._expiry](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L98) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L98


 - [ ] ID-489
Parameter [ONFT721Core.setDstChainIdToTransferGas(uint16,uint256)._dstChainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L134) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L134


 - [ ] ID-490
Parameter [ONFT721Core.estimateSendFee(uint16,bytes,uint256,bool,bytes)._adapterParams](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L33) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L33


 - [ ] ID-491
Parameter [TWAML.computeMagnitude(uint256,uint256)._timeWeight](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L124) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L124


 - [ ] ID-492
Parameter [TapiocaOptionLiquidityProvision.lock(address,IERC20,uint128,uint128)._singularity](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L173) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L173


 - [ ] ID-493
Function [ERC721.__unsafe_increaseBalance(address,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L503-L505) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L503-L505


 - [ ] ID-494
Parameter [TwTAP.advanceWeek(uint256)._limit](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L397) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L397


 - [ ] ID-495
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-496
Parameter [TWAML.computeTarget(uint256,uint256,uint256,uint256)._cumulative](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L136) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L136


 - [ ] ID-497
Variable [TapiocaOptionBroker.EPOCH_DURATION](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L78) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L78


 - [ ] ID-498
Parameter [BaseOFTV2.estimateSendFee(uint16,bytes32,uint256,bool,bytes)._dstChainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L32


 - [ ] ID-499
Parameter [AirdropBroker.exerciseOption(uint256,ERC20,uint256)._aoTAPTokenID](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L225) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L225


 - [ ] ID-500
Parameter [LzApp.lzReceive(uint16,bytes,uint64,bytes)._nonce](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L35


 - [ ] ID-501
Parameter [AOTAP.isApprovedOrOwner(address,uint256)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L76) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L76


 - [ ] ID-502
Parameter [BaseOFTV2.estimateSendAndCallFee(uint16,bytes32,uint256,bytes,uint64,bool,bytes)._useZro](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/BaseOFTV2.sol#L36


 - [ ] ID-503
Parameter [LzApp.setSendVersion(uint16)._version](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L88) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L88


 - [ ] ID-504
Parameter [LzApp.setConfig(uint16,uint16,uint256,bytes)._configType](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84


 - [ ] ID-505
Parameter [ONFT721Core.setDstChainIdToBatchLimit(uint16,uint256)._dstChainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L140) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L140


 - [ ] ID-506
Parameter [BytesLib.concat(bytes,bytes)._postBytes](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L15) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L15


 - [ ] ID-507
Parameter [LzApp.getConfig(uint16,uint16,address,uint256)._configType](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L79) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L79


 - [ ] ID-508
Parameter [AOTAP.mint(address,uint128,uint128,uint256)._expiry](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L111) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L111


 - [ ] ID-509
Parameter [LzLib.getGasLimit(bytes)._adapterParams](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L47) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L47


 - [ ] ID-510
Parameter [ExcessivelySafeCall.excessivelySafeStaticCall(address,uint256,uint16,bytes)._target](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L76) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L76


 - [ ] ID-511
Parameter [OTAP.mint(address,uint128,uint128,uint256)._to](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L97) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L97


 - [ ] ID-512
Parameter [BytesLib.toUint16(bytes,uint256)._bytes](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L319) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L319


 - [ ] ID-513
Parameter [NonblockingLzApp.nonblockingLzReceive(uint16,bytes,uint64,bytes)._srcChainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/NonblockingLzApp.sol#L37


 - [ ] ID-514
Parameter [BaseTapOFT.setTwTap(address)._twTap](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L326) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/BaseTapOFT.sol#L326


 - [ ] ID-515
Parameter [BytesLib.toUint32(bytes,uint256)._start](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L330) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L330


 - [ ] ID-516
Parameter [BytesLib.toUint64(bytes,uint256)._start](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L341) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L341


 - [ ] ID-517
Parameter [LzApp.setPayloadSizeLimit(uint16,uint256)._size](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L130) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L130


 - [ ] ID-518
Parameter [Vesting.registerUser(address,uint256)._amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L130) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L130


 - [ ] ID-519
Variable [EIP712._HASHED_NAME](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L35) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L35


 - [ ] ID-520
Parameter [AirdropBroker.getOTCDealDetails(uint256,ERC20,uint256)._tapAmount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L144) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L144


 - [ ] ID-521
Parameter [AOTAP.exists(uint256)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L89) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L89


 - [ ] ID-522
Parameter [TwTAP.distributeReward(uint256,uint256)._amount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L431) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L431


 - [ ] ID-523
Constant [TapiocaOptionBroker.dMIN](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L77) is not in UPPER_CASE_WITH_UNDERSCORES

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L77


 - [ ] ID-524
Parameter [ONFT721Core.sendBatchFrom(address,uint16,bytes,uint256[],address,address,bytes)._dstChainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L46) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L46


 - [ ] ID-525
Parameter [OTAP.exists(uint256)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L75) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L75


 - [ ] ID-526
Parameter [AirdropBroker.setPaymentToken(ERC20,IOracle,bytes)._oracle](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L346) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L346


 - [ ] ID-527
Parameter [TapiocaOptionBroker.setPaymentToken(ERC20,IOracle,bytes)._oracleData](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L461) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L461


 - [ ] ID-528
Parameter [TapiocaOptionBroker.setPaymentTokenBeneficiary(address)._paymentTokenBeneficiary](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L472) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L472


 - [ ] ID-529
Parameter [TWAML.computeMinWeight(uint256,uint256)._minWeightFactor](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L117) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L117


 - [ ] ID-530
Parameter [BytesLib.toUint96(bytes,uint256)._bytes](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L352) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L352


 - [ ] ID-531
Function [ERC721Permit.DOMAIN_SEPARATOR()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ERC4494.sol#L87-L89) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ERC4494.sol#L87-L89


 - [ ] ID-532
Parameter [AOTAP.burn(uint256)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L128) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L128


 - [ ] ID-533
Parameter [LzApp.setConfig(uint16,uint16,uint256,bytes)._config](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L84


 - [ ] ID-534
Parameter [AOTAP.setTokenURI(uint256,string)._tokenURI](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L97) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L97


 - [ ] ID-535
Parameter [Vesting.init(IERC20,uint256)._seededAmount](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L151) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L151


 - [ ] ID-536
Parameter [LzLib.addressToBytes32(address)._address](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L78) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L78


 - [ ] ID-537
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._gasForCall](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-538
Parameter [AOTAP.setTokenURI(uint256,string)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L97) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/aoTAP.sol#L97


 - [ ] ID-539
Parameter [OFTCoreV2.callOnOFTReceived(uint16,bytes,uint64,bytes32,address,uint256,bytes,uint256)._from](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTCoreV2.sol#L51


 - [ ] ID-540
Parameter [BytesLib.toUint96(bytes,uint256)._start](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L352) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L352


 - [ ] ID-541
Parameter [AirdropBroker.registerUserForPhase(uint256,address[],uint256[])._amounts](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L327) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L327


 - [ ] ID-542
Parameter [OTAP.mint(address,uint128,uint128,uint256)._tOLP](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L100) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L100


 - [ ] ID-543
Parameter [LzApp.setPrecrime(address)._precrime](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L118) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L118


 - [ ] ID-544
Parameter [TapiocaOptionLiquidityProvision.isApprovedOrOwner(address,uint256)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L156) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionLiquidityProvision.sol#L156


 - [ ] ID-545
Parameter [OFTV2.setLdChain(uint16,bool)._chainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L36) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/token/oft/v2/OFTV2.sol#L36


 - [ ] ID-546
Parameter [LzApp.getTrustedRemoteAddress(uint16)._remoteChainId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L112) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/lzApp/LzApp.sol#L112


 - [ ] ID-547
Variable [EIP712._CACHED_DOMAIN_SEPARATOR](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L31) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L31


 - [ ] ID-548
Parameter [ONFT721Core.sendBatchFrom(address,uint16,bytes,uint256[],address,address,bytes)._from](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L46) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L46


 - [ ] ID-549
Parameter [LzLib.buildDefaultAdapterParams(uint256)._uaGas](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L30) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/libraries/LzLib.sol#L30


 - [ ] ID-550
Parameter [TwTAP.releaseTap(uint256,address)._tokenId](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L373) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L373


 - [ ] ID-551
Parameter [OTAP.setTokenURI(uint256,string)._tokenURI](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L83) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/oTAP.sol#L83


 - [ ] ID-552
Variable [ERC721Permit._PERMIT_TYPEHASH_DEPRECATED_SLOT](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ERC4494.sol#L38) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ERC4494.sol#L38


 - [ ] ID-553
Parameter [ONFT721Core.setDstChainIdToTransferGas(uint16,uint256)._dstChainIdToTransferGas](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L134) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L134


 - [ ] ID-554
Parameter [Vesting.init(IERC20,uint256)._token](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L151) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L151


 - [ ] ID-555
Parameter [BytesLib.slice(bytes,uint256,uint256)._length](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L231) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L231


 - [ ] ID-556
Parameter [ONFT721Core.estimateSendBatchFee(uint16,bytes,uint256[],bool,bytes)._useZro](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L37) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/token/onft/ONFT721Core.sol#L37


 - [ ] ID-557
Variable [EIP712._HASHED_VERSION](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L36) is not in mixedCase

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L36


## similar-names
Impact: Informational
Confidence: Medium
 - [ ] ID-558
Variable [TapiocaOptionBroker.exerciseOption(uint256,ERC20,uint256)._paymentToken](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L353) is too similar to [TapiocaOptionBroker.paymentTokens](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L69)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L353


 - [ ] ID-559
Variable [TwTAP.participate(address,uint256,uint256)._participant](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L253) is too similar to [TwTAP.participants](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L79)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L253


 - [ ] ID-560
Variable [TapiocaOptionBroker._processOTCDeal(ERC20,PaymentTokenOracle,uint256,uint256)._paymentToken](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L509) is too similar to [TapiocaOptionBroker.paymentTokens](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L69)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L509


 - [ ] ID-561
Variable [TWAML.computeMinWeight(uint256,uint256)._totalWeight](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L116) is too similar to [TapiocaOptionBroker._emitToGauges(uint256).totalWeights](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L561)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/twAML.sol#L116


 - [ ] ID-562
Variable [AirdropBroker.PHASE_3_DISCOUNT](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L85) is too similar to [AirdropBroker.PHASE_4_DISCOUNT](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L93)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L85


 - [ ] ID-563
Variable [AirdropBroker._processOTCDeal(ERC20,PaymentTokenOracle,uint256,uint256)._paymentToken](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L488) is too similar to [AirdropBroker.paymentTokens](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L54)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L488


 - [ ] ID-564
Variable [AirdropBroker.getOTCDealDetails(uint256,ERC20,uint256)._paymentToken](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L143) is too similar to [AirdropBroker.paymentTokens](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L54)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L143


 - [ ] ID-565
Variable [AirdropBroker.PHASE_1_DISCOUNT](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L69) is too similar to [AirdropBroker.PHASE_4_DISCOUNT](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L93)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L69


 - [ ] ID-566
Variable [TapiocaOptionBroker.EPOCH_DURATION](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L78) is too similar to [TapiocaOptionBroker.constructor(address,address,address,address,uint256,address)._epochDuration](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L86)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L78


 - [ ] ID-567
Variable [AirdropBroker.PHASE_2_AMOUNT_PER_USER](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L77) is too similar to [AirdropBroker.PHASE_3_AMOUNT_PER_USER](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L84)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L77


 - [ ] ID-568
Variable [AirdropBroker.PHASE_1_DISCOUNT](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L69) is too similar to [AirdropBroker.PHASE_3_DISCOUNT](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L85)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L69


 - [ ] ID-569
Variable [TapiocaOptionBroker.setPaymentToken(ERC20,IOracle,bytes)._paymentToken](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L459) is too similar to [TapiocaOptionBroker.paymentTokens](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L69)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L459


 - [ ] ID-570
Variable [AirdropBroker.phase1Users](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L68) is too similar to [AirdropBroker.phase4Users](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L92)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L68


 - [ ] ID-571
Variable [TapiocaOptionBroker.getOTCDealDetails(uint256,ERC20,uint256)._paymentToken](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L147) is too similar to [TapiocaOptionBroker.paymentTokens](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L69)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/options/TapiocaOptionBroker.sol#L147


 - [ ] ID-572
Variable [AirdropBroker.setPaymentToken(ERC20,IOracle,bytes)._paymentToken](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L345) is too similar to [AirdropBroker.paymentTokens](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L54)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L345


 - [ ] ID-573
Variable [AirdropBroker.exerciseOption(uint256,ERC20,uint256)._paymentToken](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L226) is too similar to [AirdropBroker.paymentTokens](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L54)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/option-airdrop/AirdropBroker.sol#L226


## too-many-digits
Impact: Informational
Confidence: Medium
 - [ ] ID-574
[ExcessivelySafeCall.slitherConstructorConstantVariables()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/ExcessivelySafeCall.sol#L4-L136) uses literals with too many digits:
	- [LOW_28_MASK = 0x00000000ffffffffffffffffffffffffffffffffffffffffffffffffffffffff](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/ExcessivelySafeCall.sol#L5-L6)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/ExcessivelySafeCall.sol#L4-L136


 - [ ] ID-575
[BytesLib.toAddress(bytes,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297-L306) uses literals with too many digits:
	- [tempAddress = mload(uint256)(_bytes + 0x20 + _start) / 0x1000000000000000000000000](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L302)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/BytesLib.sol#L297-L306


 - [ ] ID-576
[BytesLib.toAddress(bytes,uint256)](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L297-L306) uses literals with too many digits:
	- [tempAddress = mload(uint256)(_bytes + 0x20 + _start) / 0x1000000000000000000000000](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L302)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/src/contracts/util/BytesLib.sol#L297-L306


 - [ ] ID-577
[TapOFT.slitherConstructorConstantVariables()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L26-L256) uses literals with too many digits:
	- [decay_rate = 8800000000000000](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L45)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/TapOFT.sol#L26-L256


 - [ ] ID-578
[ExcessivelySafeCall.slitherConstructorConstantVariables()](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L4-L136) uses literals with too many digits:
	- [LOW_28_MASK = 0x00000000ffffffffffffffffffffffffffffffffffffffffffffffffffffffff](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L5-L6)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/node_modules/tapioca-sdk/dist/contracts/util/ExcessivelySafeCall.sol#L4-L136


## unused-state
Impact: Informational
Confidence: High
 - [ ] ID-579
[TwTAP.baseURI](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L112) is never used in [TwTAP](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L71-L587)

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L112


## constable-states
Impact: Optimization
Confidence: High
 - [ ] ID-580
[TwTAP.baseURI](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L112) should be constant 

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L112


## immutable-states
Impact: Optimization
Confidence: High
 - [ ] ID-581
[Vesting.duration](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L26) should be immutable 

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L26


 - [ ] ID-582
[TwTAP.creation](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L107) should be immutable 

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/governance/twTAP.sol#L107


 - [ ] ID-583
[LTap.tapToken](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L24) should be immutable 

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L24


 - [ ] ID-584
[LTap.maxLockedUntil](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L26) should be immutable 

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/tokens/LTap.sol#L26


 - [ ] ID-585
[Vesting.cliff](https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L23) should be immutable 

https://github.com/Tapioca-Audit/tap-token-audit/master/tree/contracts/Vesting.sol#L23


INFO:Slither:. analyzed (81 contracts with 88 detectors), 586 result(s) found
