Summary
 - [arbitrary-send-erc20](#arbitrary-send-erc20) (1 results) (High)
 - [arbitrary-send-eth](#arbitrary-send-eth) (2 results) (High)
 - [delegatecall-loop](#delegatecall-loop) (1 results) (High)
 - [encode-packed-collision](#encode-packed-collision) (1 results) (High)
 - [name-reused](#name-reused) (4 results) (High)
 - [unchecked-transfer](#unchecked-transfer) (2 results) (High)
 - [uninitialized-state](#uninitialized-state) (1 results) (High)
 - [divide-before-multiply](#divide-before-multiply) (19 results) (Medium)
 - [incorrect-equality](#incorrect-equality) (3 results) (Medium)
 - [locked-ether](#locked-ether) (3 results) (Medium)
 - [reentrancy-no-eth](#reentrancy-no-eth) (14 results) (Medium)
 - [tautology](#tautology) (4 results) (Medium)
 - [unchecked-lowlevel](#unchecked-lowlevel) (3 results) (Medium)
 - [uninitialized-local](#uninitialized-local) (7 results) (Medium)
 - [unused-return](#unused-return) (15 results) (Medium)
 - [shadowing-local](#shadowing-local) (5 results) (Low)
 - [missing-zero-check](#missing-zero-check) (8 results) (Low)
 - [calls-loop](#calls-loop) (1 results) (Low)
 - [reentrancy-benign](#reentrancy-benign) (5 results) (Low)
 - [reentrancy-events](#reentrancy-events) (30 results) (Low)
 - [timestamp](#timestamp) (10 results) (Low)
 - [assembly](#assembly) (12 results) (Informational)
 - [boolean-equal](#boolean-equal) (1 results) (Informational)
 - [pragma](#pragma) (1 results) (Informational)
 - [solc-version](#solc-version) (76 results) (Informational)
 - [low-level-calls](#low-level-calls) (14 results) (Informational)
 - [missing-inheritance](#missing-inheritance) (1 results) (Informational)
 - [naming-convention](#naming-convention) (28 results) (Informational)
 - [similar-names](#similar-names) (5 results) (Informational)
 - [too-many-digits](#too-many-digits) (8 results) (Informational)
 - [unimplemented-functions](#unimplemented-functions) (1 results) (Informational)
 - [unused-state](#unused-state) (1 results) (Informational)
 - [constable-states](#constable-states) (4 results) (Optimization)
 - [immutable-states](#immutable-states) (10 results) (Optimization)
## arbitrary-send-erc20
Impact: High
Confidence: High
 - [ ] ID-0
[YieldBox.depositAsset(uint256,address,address,uint256,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L118-L160) uses arbitrary from in transferFrom: [IERC20(asset.contractAddress).safeTransferFrom(from,address(asset.strategy),amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L144)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L118-L160


## arbitrary-send-eth
Impact: High
Confidence: Medium
 - [ ] ID-1
[YieldBox.depositETHAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L196-L215) sends eth to arbitrary user
        Dangerous calls:
        - [wrappedNative.deposit{value: amount}()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L207)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L196-L215


 - [ ] ID-2
[MasterContractFullCycleMock.run()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44) sends eth to arbitrary user
        Dangerous calls:
        - [yieldBox.depositETH{value: 1000}(ethStrategy,deployer,1000)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L42)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44


## delegatecall-loop
Impact: High
Confidence: Medium
 - [ ] ID-3
[BaseBoringBatchable.batch(bytes[],bool)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L35-L42) has delegatecall inside a loop in a payable function: [(success,result) = address(this).delegatecall(calls[i])](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L37)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L35-L42


## encode-packed-collision
Impact: High
Confidence: High
 - [ ] ID-4
[YieldBoxURIBuilder.uri(Asset,NativeToken,uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxURIBuilder.sol#L79-L135) calls abi.encodePacked() with multiple dynamic arguments:
        - [string(abi.encodePacked(data:application/json;base64,,abi.encodePacked({"name":",details.name,","symbol":",details.symbol,",,,,"properties":{"strategy":",uint256(uint160(address(asset.strategy))).toHexString(20),","tokenType":",details.tokenType,",properties,string(abi.encodePacked(,"tokenId":,asset.tokenId.toString())),}}).encode()))](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxURIBuilder.sol#L110-L134)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxURIBuilder.sol#L79-L135


## name-reused
Impact: High
Confidence: High
 - [ ] ID-5
IERC721Metadata is re-used:
        - [IERC721Metadata](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721.sol#L105-L117)
        - [IERC721Metadata](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/token/ERC721/extensions/IERC721Metadata.sol#L12-L27)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721.sol#L105-L117


 - [ ] ID-6
ISushiBar is re-used:
        - [ISushiBar](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingBufferStrategy.sol#L13-L17)
        - [ISushiBar](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingSimpleStrategy.sol#L14-L18)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingBufferStrategy.sol#L13-L17


 - [ ] ID-7
IERC721 is re-used:
        - [IERC721](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721.sol#L7-L100)
        - [IERC721](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/token/ERC721/IERC721.sol#L11-L145)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721.sol#L7-L100


 - [ ] ID-8
IERC165 is re-used:
        - [IERC165](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC165.sol#L4-L6)
        - [IERC165](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/introspection/IERC165.sol#L15-L25)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC165.sol#L4-L6


## unchecked-transfer
Impact: High
Confidence: Medium
 - [ ] ID-9
[SushiBarMock.enter(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/SushiBarMock.sol#L22-L39) ignores return value by [sushi.transferFrom(msg.sender,address(this),_amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/SushiBarMock.sol#L38)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/SushiBarMock.sol#L22-L39


 - [ ] ID-10
[SushiBarMock.leave(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/SushiBarMock.sol#L43-L50) ignores return value by [sushi.transfer(msg.sender,what)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/SushiBarMock.sol#L49)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/SushiBarMock.sol#L43-L50


## uninitialized-state
Impact: High
Confidence: High
 - [ ] ID-11
[Tokenizer.tokenizedAsset](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Tokenizer.sol#L12) is never initialized. It is used in:
        - [Tokenizer.deposit(uint256,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Tokenizer.sol#L14-L26)
        - [Tokenizer.withdraw(uint256,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Tokenizer.sol#L28-L32)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Tokenizer.sol#L12


## divide-before-multiply
Impact: Medium
Confidence: Medium
 - [ ] ID-12
[Base64.encode(bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L11-L69) performs a multiplication on the result of a division:
        - [encodedLen = 4 * ((data.length + 2) / 3)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L18)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L11-L69


 - [ ] ID-13
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L126)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-14
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L124)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-15
[LendingPair._isSolvent(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L180-L201) performs a multiplication on the result of a division:
        - [yieldBox.toAmount(market.collateral,((collateralShare * EXCHANGE_RATE_PRECISION) / COLLATERIZATION_RATE_PRECISION) * COLLATERIZATION_RATE,false) >= (borrowPart * market.totalBorrow.elastic * _exchangeRate) / market.totalBorrow.base](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L193-L200)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L180-L201


 - [ ] ID-16
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L123)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-17
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L121)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-18
[String.numToString(uint256,uint8)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L35-L73) performs a multiplication on the result of a division:
        - [num = number / 10 ** i](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L45)
        - [(j > 1) && (number == num * 10 ** i) && (i <= decimals)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L49)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L35-L73


 - [ ] ID-19
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
        - [inverse = (3 * denominator) ^ 2](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L117)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-20
[LendingPair.accrue(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176) performs a multiplication on the result of a division:
        - [overFactor = ((utilization - MAXIMUM_TARGET_UTILIZATION) * FACTOR_PRECISION) / FULL_UTILIZATION_MINUS_MAX](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L166)
        - [scale_scope_0 = INTEREST_ELASTICITY + (overFactor * overFactor * elapsedTime)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L167)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176


 - [ ] ID-21
[LendingPair.liquidate(uint256,address,uint256,address,ISwapper)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440) performs a multiplication on the result of a division:
        - [collateralShare = yieldBox.toShare(market.collateral,((borrowAmount * LIQUIDATION_MULTIPLIER * _exchangeRate) / LIQUIDATION_MULTIPLIER_PRECISION) * EXCHANGE_RATE_PRECISION,false)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L414-L418)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440


 - [ ] ID-22
[RebaseLibrary.toBase(Rebase,uint256,bool)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L12-L25) performs a multiplication on the result of a division:
        - [base = (elastic * total.base) / total.elastic](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L20)
        - [roundUp && (base * total.elastic) / total.base < elastic](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L21)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L12-L25


 - [ ] ID-23
[BoringMath.muldiv(uint256,uint256,uint256,bool)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/BoringMath.sol#L20-L30) performs a multiplication on the result of a division:
        - [result = (value * mul) / div](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/BoringMath.sol#L26)
        - [roundUp && (result * div) / mul < value](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/BoringMath.sol#L27)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/BoringMath.sol#L20-L30


 - [ ] ID-24
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L122)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-25
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [prod0 = prod0 / twos](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L105)
        - [result = prod0 * inverse](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L132)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-26
[LendingPair.accrue(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176) performs a multiplication on the result of a division:
        - [underFactor = ((MINIMUM_TARGET_UTILIZATION - utilization) * FACTOR_PRECISION) / MINIMUM_TARGET_UTILIZATION](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L158)
        - [scale = INTEREST_ELASTICITY + (underFactor * underFactor * elapsedTime)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L159)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176


 - [ ] ID-27
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L102)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L125)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-28
[YieldBoxRebase._toAmount(uint256,uint256,uint256,bool)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxRebase.sol#L41-L61) performs a multiplication on the result of a division:
        - [amount = (share * totalAmount) / totalShares_](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxRebase.sol#L55)
        - [roundUp && (amount * totalShares_) / totalAmount < share](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxRebase.sol#L58)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxRebase.sol#L41-L61


 - [ ] ID-29
[YieldBoxRebase._toShares(uint256,uint256,uint256,bool)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxRebase.sol#L18-L38) performs a multiplication on the result of a division:
        - [share = (amount * totalShares_) / totalAmount](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxRebase.sol#L32)
        - [roundUp && (share * totalAmount) / totalShares_ < amount](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxRebase.sol#L35)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxRebase.sol#L18-L38


 - [ ] ID-30
[RebaseLibrary.toElastic(Rebase,uint256,bool)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L28-L41) performs a multiplication on the result of a division:
        - [elastic = (base * total.elastic) / total.base](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L36)
        - [roundUp && (elastic * total.base) / total.elastic < base](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L37)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L28-L41


## incorrect-equality
Impact: Medium
Confidence: High
 - [ ] ID-31
[LendingPair.accrue(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176) uses a dangerous strict equality:
        - [market.totalBorrow.base == 0](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L139)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176


 - [ ] ID-32
[LendingPair.accrue(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176) uses a dangerous strict equality:
        - [elapsedTime == 0](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L134)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176


 - [ ] ID-33
[SushiBarMock.enter(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/SushiBarMock.sol#L22-L39) uses a dangerous strict equality:
        - [totalShares == 0 || totalSushi == 0](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/SushiBarMock.sol#L28)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/SushiBarMock.sol#L22-L39


## locked-ether
Impact: Medium
Confidence: High
 - [ ] ID-34
Contract locking ether found:
        Contract [MasterContractMock](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractMock.sol#L8-L26) has payable functions:
         - [IMasterContract.init(bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IMasterContract.sol#L9)
         - [MasterContractMock.init(bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractMock.sol#L23-L25)
        But does not have a function to withdraw the ether

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractMock.sol#L8-L26


 - [ ] ID-35
Contract locking ether found:
        Contract [MaliciousMasterContractMock](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MaliciousMasterContractMock.sol#L6-L14) has payable functions:
         - [IMasterContract.init(bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IMasterContract.sol#L9)
         - [MaliciousMasterContractMock.init(bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MaliciousMasterContractMock.sol#L7-L9)
        But does not have a function to withdraw the ether

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MaliciousMasterContractMock.sol#L6-L14


 - [ ] ID-36
Contract locking ether found:
        Contract [LendingPair](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L54-L441) has payable functions:
         - [IMasterContract.init(bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IMasterContract.sol#L9)
         - [LendingPair.init(bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L103-L105)
        But does not have a function to withdraw the ether

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L54-L441


## reentrancy-no-eth
Impact: Medium
Confidence: Medium
 - [ ] ID-37
Reentrancy in [LendingPair.borrow(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L351-L359):
        External calls:
        - [updateExchangeRate(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L356)
                - [(updated,rate) = market.oracle.get(market.oracleData)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L215)
        - [accrue(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L357)
                - [market.interestPerSecond = ((market.interestPerSecond * INTEREST_ELASTICITY) / scale).to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L160)
        - [(part,share) = _borrow(marketId,to,amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L358)
                - [yieldBox.transfer(address(this),to,market.asset,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L345)
        State variables written after the call(s):
        - [(part,share) = _borrow(marketId,to,amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L358)
                - [market.userBorrowPart[msg.sender] += part](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L339)
                - [market.totalAssetShares -= share](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L344)
        [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73) can be used in cross function reentrancies:
        - [LendingPair._addAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L271-L286)
        - [LendingPair._borrow(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L331-L346)
        - [LendingPair._isSolvent(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L180-L201)
        - [LendingPair._removeAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L302-L315)
        - [LendingPair._removeCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L244-L255)
        - [LendingPair._repay(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L362-L376)
        - [LendingPair.accrue(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176)
        - [LendingPair.addCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L230-L241)
        - [LendingPair.createMarket(uint32,uint32,IOracle,bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L107-L126)
        - [LendingPair.liquidate(uint256,address,uint256,address,ISwapper)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440)
        - [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73)
        - [LendingPair.updateExchangeRate(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L212-L224)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L351-L359


 - [ ] ID-38
Reentrancy in [YieldSwap.mint(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L45-L65):
        External calls:
        - [yieldBox.mint(pair.lpAssetId,address(0),MINIMUM_LIQUIDITY)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L56)
        - [yieldBox.mint(pair.lpAssetId,to,liquidity)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L61)
        State variables written after the call(s):
        - [pair.reserve0 = balance0.to128()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L63)
        [YieldSwap.pairs](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L26) can be used in cross function reentrancies:
        - [YieldSwap.burn(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L67-L84)
        - [YieldSwap.create(uint32,uint32)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L34-L43)
        - [YieldSwap.mint(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L45-L65)
        - [YieldSwap.pairs](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L26)
        - [YieldSwap.skim(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L108-L113)
        - [YieldSwap.swap(uint256,uint256,uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L86-L105)
        - [YieldSwap.sync(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L116-L121)
        - [pair.reserve1 = balance1.to128()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L64)
        [YieldSwap.pairs](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L26) can be used in cross function reentrancies:
        - [YieldSwap.burn(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L67-L84)
        - [YieldSwap.create(uint32,uint32)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L34-L43)
        - [YieldSwap.mint(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L45-L65)
        - [YieldSwap.pairs](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L26)
        - [YieldSwap.skim(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L108-L113)
        - [YieldSwap.swap(uint256,uint256,uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L86-L105)
        - [YieldSwap.sync(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L116-L121)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L45-L65


 - [ ] ID-39
Reentrancy in [LendingPair.borrow(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L351-L359):
        External calls:
        - [updateExchangeRate(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L356)
                - [(updated,rate) = market.oracle.get(market.oracleData)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L215)
        - [accrue(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L357)
                - [market.interestPerSecond = ((market.interestPerSecond * INTEREST_ELASTICITY) / scale).to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L160)
        State variables written after the call(s):
        - [accrue(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L357)
                - [market.lastAccrued = block.timestamp.to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L137)
                - [market.interestPerSecond = STARTING_INTEREST_PER_SECOND](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L142)
                - [market.totalBorrow.elastic += extraAmount.to128()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L152)
                - [market.interestPerSecond = ((market.interestPerSecond * INTEREST_ELASTICITY) / scale).to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L160)
                - [market.interestPerSecond = MINIMUM_INTEREST_PER_SECOND](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L163)
                - [market.interestPerSecond = newInterestPerSecond.to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L172)
        [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73) can be used in cross function reentrancies:
        - [LendingPair._addAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L271-L286)
        - [LendingPair._borrow(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L331-L346)
        - [LendingPair._isSolvent(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L180-L201)
        - [LendingPair._removeAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L302-L315)
        - [LendingPair._removeCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L244-L255)
        - [LendingPair._repay(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L362-L376)
        - [LendingPair.accrue(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176)
        - [LendingPair.addCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L230-L241)
        - [LendingPair.createMarket(uint32,uint32,IOracle,bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L107-L126)
        - [LendingPair.liquidate(uint256,address,uint256,address,ISwapper)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440)
        - [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73)
        - [LendingPair.updateExchangeRate(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L212-L224)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L351-L359


 - [ ] ID-40
Reentrancy in [YieldSwap.burn(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L67-L84):
        External calls:
        - [yieldBox.burn(pair.lpAssetId,address(this),liquidity)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L78)
        - [yieldBox.transfer(address(this),to,pair.asset0,share0)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L79)
        - [yieldBox.transfer(address(this),to,pair.asset1,share1)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L80)
        State variables written after the call(s):
        - [pair.reserve0 = yieldBox.balanceOf(address(this),pair.asset0).to128()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L82)
        [YieldSwap.pairs](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L26) can be used in cross function reentrancies:
        - [YieldSwap.burn(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L67-L84)
        - [YieldSwap.create(uint32,uint32)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L34-L43)
        - [YieldSwap.mint(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L45-L65)
        - [YieldSwap.pairs](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L26)
        - [YieldSwap.skim(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L108-L113)
        - [YieldSwap.swap(uint256,uint256,uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L86-L105)
        - [YieldSwap.sync(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L116-L121)
        - [pair.reserve1 = yieldBox.balanceOf(address(this),pair.asset1).to128()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L83)
        [YieldSwap.pairs](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L26) can be used in cross function reentrancies:
        - [YieldSwap.burn(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L67-L84)
        - [YieldSwap.create(uint32,uint32)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L34-L43)
        - [YieldSwap.mint(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L45-L65)
        - [YieldSwap.pairs](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L26)
        - [YieldSwap.skim(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L108-L113)
        - [YieldSwap.swap(uint256,uint256,uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L86-L105)
        - [YieldSwap.sync(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L116-L121)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L67-L84


 - [ ] ID-41
Reentrancy in [LendingPair.liquidate(uint256,address,uint256,address,ISwapper)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440):
        External calls:
        - [(_exchangeRate) = updateExchangeRate(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L406)
                - [(updated,rate) = market.oracle.get(market.oracleData)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L215)
        - [accrue(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L407)
                - [market.interestPerSecond = ((market.interestPerSecond * INTEREST_ELASTICITY) / scale).to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L160)
        - [swapper.swap(market.collateral,market.asset,msg.sender,borrowShare,collateralShare)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L433)
        - [yieldBox.transfer(msg.sender,address(this),market.asset,borrowShare)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L436)
        - [yieldBox.transfer(address(this),to,market.collateral,collateralShare)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L431)
        - [yieldBox.transfer(address(this),address(swapper),market.collateral,collateralShare)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L431)
        State variables written after the call(s):
        - [market.totalAssetShares += borrowShare](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L437)
        [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73) can be used in cross function reentrancies:
        - [LendingPair._addAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L271-L286)
        - [LendingPair._borrow(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L331-L346)
        - [LendingPair._isSolvent(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L180-L201)
        - [LendingPair._removeAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L302-L315)
        - [LendingPair._removeCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L244-L255)
        - [LendingPair._repay(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L362-L376)
        - [LendingPair.accrue(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176)
        - [LendingPair.addCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L230-L241)
        - [LendingPair.createMarket(uint32,uint32,IOracle,bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L107-L126)
        - [LendingPair.liquidate(uint256,address,uint256,address,ISwapper)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440)
        - [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73)
        - [LendingPair.updateExchangeRate(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L212-L224)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440


 - [ ] ID-42
Reentrancy in [LendingPair.accrue(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176):
        External calls:
        - [market.interestPerSecond = ((market.interestPerSecond * INTEREST_ELASTICITY) / scale).to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L160)
        State variables written after the call(s):
        - [market.interestPerSecond = MINIMUM_INTEREST_PER_SECOND](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L163)
        [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73) can be used in cross function reentrancies:
        - [LendingPair._addAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L271-L286)
        - [LendingPair._borrow(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L331-L346)
        - [LendingPair._isSolvent(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L180-L201)
        - [LendingPair._removeAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L302-L315)
        - [LendingPair._removeCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L244-L255)
        - [LendingPair._repay(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L362-L376)
        - [LendingPair.accrue(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176)
        - [LendingPair.addCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L230-L241)
        - [LendingPair.createMarket(uint32,uint32,IOracle,bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L107-L126)
        - [LendingPair.liquidate(uint256,address,uint256,address,ISwapper)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440)
        - [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73)
        - [LendingPair.updateExchangeRate(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L212-L224)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176


 - [ ] ID-43
Reentrancy in [Escrow.take(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Escrow.sol#L32-L37):
        External calls:
        - [yieldBox.transfer(msg.sender,offer.owner,offer.assetFrom,offer.shareFrom)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Escrow.sol#L34)
        - [yieldBox.transfer(offer.owner,msg.sender,offer.assetTo,offer.shareTo)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Escrow.sol#L35)
        State variables written after the call(s):
        - [offers[offerId].closed = true](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Escrow.sol#L36)
        [Escrow.offers](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Escrow.sol#L21) can be used in cross function reentrancies:
        - [Escrow.cancel(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Escrow.sol#L39-L42)
        - [Escrow.make(uint256,uint256,uint256,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Escrow.sol#L23-L30)
        - [Escrow.offers](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Escrow.sol#L21)
        - [Escrow.take(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Escrow.sol#L32-L37)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Escrow.sol#L32-L37


 - [ ] ID-44
Reentrancy in [LendingPair.repay(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L382-L389):
        External calls:
        - [accrue(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L387)
                - [market.interestPerSecond = ((market.interestPerSecond * INTEREST_ELASTICITY) / scale).to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L160)
        - [amount = _repay(marketId,to,part)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L388)
                - [yieldBox.transfer(msg.sender,address(this),market.asset,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L373)
        State variables written after the call(s):
        - [amount = _repay(marketId,to,part)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L388)
                - [market.userBorrowPart[to] -= part](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L370)
                - [market.totalAssetShares += share](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L374)
        [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73) can be used in cross function reentrancies:
        - [LendingPair._addAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L271-L286)
        - [LendingPair._borrow(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L331-L346)
        - [LendingPair._isSolvent(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L180-L201)
        - [LendingPair._removeAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L302-L315)
        - [LendingPair._removeCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L244-L255)
        - [LendingPair._repay(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L362-L376)
        - [LendingPair.accrue(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176)
        - [LendingPair.addCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L230-L241)
        - [LendingPair.createMarket(uint32,uint32,IOracle,bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L107-L126)
        - [LendingPair.liquidate(uint256,address,uint256,address,ISwapper)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440)
        - [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73)
        - [LendingPair.updateExchangeRate(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L212-L224)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L382-L389


 - [ ] ID-45
Reentrancy in [HelloWorld.withdraw()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L34-L37):
        External calls:
        - [yieldBox.withdraw(assetId,address(this),msg.sender,0,yieldBoxShares[msg.sender])](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L35)
        State variables written after the call(s):
        - [yieldBoxShares[msg.sender] = 0](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L36)
        [HelloWorld.yieldBoxShares](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L16) can be used in cross function reentrancies:
        - [HelloWorld.balance()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L29-L31)
        - [HelloWorld.deposit(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L21-L25)
        - [HelloWorld.withdraw()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L34-L37)
        - [HelloWorld.yieldBoxShares](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L16)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L34-L37


 - [ ] ID-46
Reentrancy in [LendingPair.removeCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L260-L268):
        External calls:
        - [accrue(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L266)
                - [market.interestPerSecond = ((market.interestPerSecond * INTEREST_ELASTICITY) / scale).to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L160)
        - [_removeCollateral(marketId,to,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L267)
                - [yieldBox.transfer(address(this),to,market.collateral,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L253)
        State variables written after the call(s):
        - [_removeCollateral(marketId,to,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L267)
                - [market.userCollateralShare[msg.sender] -= share](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L251)
                - [market.totalCollateralShare -= share](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L252)
        [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73) can be used in cross function reentrancies:
        - [LendingPair._addAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L271-L286)
        - [LendingPair._borrow(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L331-L346)
        - [LendingPair._isSolvent(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L180-L201)
        - [LendingPair._removeAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L302-L315)
        - [LendingPair._removeCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L244-L255)
        - [LendingPair._repay(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L362-L376)
        - [LendingPair.accrue(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176)
        - [LendingPair.addCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L230-L241)
        - [LendingPair.createMarket(uint32,uint32,IOracle,bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L107-L126)
        - [LendingPair.liquidate(uint256,address,uint256,address,ISwapper)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440)
        - [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73)
        - [LendingPair.updateExchangeRate(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L212-L224)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L260-L268


 - [ ] ID-47
Reentrancy in [LendingPair.updateExchangeRate(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L212-L224):
        External calls:
        - [(updated,rate) = market.oracle.get(market.oracleData)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L215)
        State variables written after the call(s):
        - [market.exchangeRate = rate](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L218)
        [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73) can be used in cross function reentrancies:
        - [LendingPair._addAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L271-L286)
        - [LendingPair._borrow(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L331-L346)
        - [LendingPair._isSolvent(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L180-L201)
        - [LendingPair._removeAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L302-L315)
        - [LendingPair._removeCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L244-L255)
        - [LendingPair._repay(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L362-L376)
        - [LendingPair.accrue(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176)
        - [LendingPair.addCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L230-L241)
        - [LendingPair.createMarket(uint32,uint32,IOracle,bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L107-L126)
        - [LendingPair.liquidate(uint256,address,uint256,address,ISwapper)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440)
        - [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73)
        - [LendingPair.updateExchangeRate(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L212-L224)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L212-L224


 - [ ] ID-48
Reentrancy in [LendingPair.liquidate(uint256,address,uint256,address,ISwapper)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440):
        External calls:
        - [(_exchangeRate) = updateExchangeRate(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L406)
                - [(updated,rate) = market.oracle.get(market.oracleData)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L215)
        - [accrue(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L407)
                - [market.interestPerSecond = ((market.interestPerSecond * INTEREST_ELASTICITY) / scale).to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L160)
        State variables written after the call(s):
        - [accrue(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L407)
                - [market.lastAccrued = block.timestamp.to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L137)
                - [market.interestPerSecond = STARTING_INTEREST_PER_SECOND](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L142)
                - [market.totalBorrow.elastic += extraAmount.to128()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L152)
                - [market.interestPerSecond = ((market.interestPerSecond * INTEREST_ELASTICITY) / scale).to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L160)
                - [market.interestPerSecond = MINIMUM_INTEREST_PER_SECOND](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L163)
                - [market.interestPerSecond = newInterestPerSecond.to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L172)
        [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73) can be used in cross function reentrancies:
        - [LendingPair._addAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L271-L286)
        - [LendingPair._borrow(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L331-L346)
        - [LendingPair._isSolvent(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L180-L201)
        - [LendingPair._removeAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L302-L315)
        - [LendingPair._removeCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L244-L255)
        - [LendingPair._repay(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L362-L376)
        - [LendingPair.accrue(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176)
        - [LendingPair.addCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L230-L241)
        - [LendingPair.createMarket(uint32,uint32,IOracle,bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L107-L126)
        - [LendingPair.liquidate(uint256,address,uint256,address,ISwapper)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440)
        - [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73)
        - [LendingPair.updateExchangeRate(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L212-L224)
        - [market.userBorrowPart[user] = availableBorrowPart - borrowPart](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L412)
        [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73) can be used in cross function reentrancies:
        - [LendingPair._addAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L271-L286)
        - [LendingPair._borrow(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L331-L346)
        - [LendingPair._isSolvent(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L180-L201)
        - [LendingPair._removeAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L302-L315)
        - [LendingPair._removeCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L244-L255)
        - [LendingPair._repay(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L362-L376)
        - [LendingPair.accrue(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176)
        - [LendingPair.addCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L230-L241)
        - [LendingPair.createMarket(uint32,uint32,IOracle,bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L107-L126)
        - [LendingPair.liquidate(uint256,address,uint256,address,ISwapper)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440)
        - [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73)
        - [LendingPair.updateExchangeRate(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L212-L224)
        - [market.userCollateralShare[user] -= collateralShare](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L420)
        [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73) can be used in cross function reentrancies:
        - [LendingPair._addAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L271-L286)
        - [LendingPair._borrow(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L331-L346)
        - [LendingPair._isSolvent(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L180-L201)
        - [LendingPair._removeAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L302-L315)
        - [LendingPair._removeCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L244-L255)
        - [LendingPair._repay(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L362-L376)
        - [LendingPair.accrue(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176)
        - [LendingPair.addCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L230-L241)
        - [LendingPair.createMarket(uint32,uint32,IOracle,bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L107-L126)
        - [LendingPair.liquidate(uint256,address,uint256,address,ISwapper)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440)
        - [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73)
        - [LendingPair.updateExchangeRate(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L212-L224)
        - [market.totalBorrow.elastic -= borrowAmount.to128()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L424)
        [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73) can be used in cross function reentrancies:
        - [LendingPair._addAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L271-L286)
        - [LendingPair._borrow(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L331-L346)
        - [LendingPair._isSolvent(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L180-L201)
        - [LendingPair._removeAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L302-L315)
        - [LendingPair._removeCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L244-L255)
        - [LendingPair._repay(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L362-L376)
        - [LendingPair.accrue(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176)
        - [LendingPair.addCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L230-L241)
        - [LendingPair.createMarket(uint32,uint32,IOracle,bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L107-L126)
        - [LendingPair.liquidate(uint256,address,uint256,address,ISwapper)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440)
        - [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73)
        - [LendingPair.updateExchangeRate(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L212-L224)
        - [market.totalBorrow.base -= borrowPart.to128()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L425)
        [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73) can be used in cross function reentrancies:
        - [LendingPair._addAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L271-L286)
        - [LendingPair._borrow(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L331-L346)
        - [LendingPair._isSolvent(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L180-L201)
        - [LendingPair._removeAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L302-L315)
        - [LendingPair._removeCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L244-L255)
        - [LendingPair._repay(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L362-L376)
        - [LendingPair.accrue(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176)
        - [LendingPair.addCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L230-L241)
        - [LendingPair.createMarket(uint32,uint32,IOracle,bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L107-L126)
        - [LendingPair.liquidate(uint256,address,uint256,address,ISwapper)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440)
        - [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73)
        - [LendingPair.updateExchangeRate(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L212-L224)
        - [market.totalCollateralShare -= collateralShare](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L426)
        [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73) can be used in cross function reentrancies:
        - [LendingPair._addAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L271-L286)
        - [LendingPair._borrow(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L331-L346)
        - [LendingPair._isSolvent(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L180-L201)
        - [LendingPair._removeAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L302-L315)
        - [LendingPair._removeCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L244-L255)
        - [LendingPair._repay(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L362-L376)
        - [LendingPair.accrue(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176)
        - [LendingPair.addCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L230-L241)
        - [LendingPair.createMarket(uint32,uint32,IOracle,bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L107-L126)
        - [LendingPair.liquidate(uint256,address,uint256,address,ISwapper)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440)
        - [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73)
        - [LendingPair.updateExchangeRate(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L212-L224)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440


 - [ ] ID-49
Reentrancy in [YieldSwap.swap(uint256,uint256,uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L86-L105):
        External calls:
        - [yieldBox.transfer(address(this),to,pair.asset0,share0Out)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L92)
        - [yieldBox.transfer(address(this),to,pair.asset1,share1Out)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L93)
        State variables written after the call(s):
        - [pair.reserve0 = balance0.to128()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L103)
        [YieldSwap.pairs](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L26) can be used in cross function reentrancies:
        - [YieldSwap.burn(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L67-L84)
        - [YieldSwap.create(uint32,uint32)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L34-L43)
        - [YieldSwap.mint(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L45-L65)
        - [YieldSwap.pairs](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L26)
        - [YieldSwap.skim(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L108-L113)
        - [YieldSwap.swap(uint256,uint256,uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L86-L105)
        - [YieldSwap.sync(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L116-L121)
        - [pair.reserve1 = balance1.to128()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L104)
        [YieldSwap.pairs](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L26) can be used in cross function reentrancies:
        - [YieldSwap.burn(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L67-L84)
        - [YieldSwap.create(uint32,uint32)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L34-L43)
        - [YieldSwap.mint(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L45-L65)
        - [YieldSwap.pairs](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L26)
        - [YieldSwap.skim(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L108-L113)
        - [YieldSwap.swap(uint256,uint256,uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L86-L105)
        - [YieldSwap.sync(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L116-L121)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L86-L105


 - [ ] ID-50
Reentrancy in [LendingPair._repay(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L362-L376):
        External calls:
        - [yieldBox.transfer(msg.sender,address(this),market.asset,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L373)
        State variables written after the call(s):
        - [market.totalAssetShares += share](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L374)
        [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73) can be used in cross function reentrancies:
        - [LendingPair._addAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L271-L286)
        - [LendingPair._borrow(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L331-L346)
        - [LendingPair._isSolvent(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L180-L201)
        - [LendingPair._removeAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L302-L315)
        - [LendingPair._removeCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L244-L255)
        - [LendingPair._repay(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L362-L376)
        - [LendingPair.accrue(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176)
        - [LendingPair.addCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L230-L241)
        - [LendingPair.createMarket(uint32,uint32,IOracle,bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L107-L126)
        - [LendingPair.liquidate(uint256,address,uint256,address,ISwapper)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440)
        - [LendingPair.markets](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L73)
        - [LendingPair.updateExchangeRate(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L212-L224)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L362-L376


## tautology
Impact: Medium
Confidence: High
 - [ ] ID-51
[RevertingERC20Mock.transferFrom(address,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/RevertingERC20Mock.sol#L40-L54) contains a tautology or contradiction:
        - [require(bool,string)(amount >= 0,TokenB: amount should be >= 0)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/RevertingERC20Mock.sol#L47)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/RevertingERC20Mock.sol#L40-L54


 - [ ] ID-52
[String.numToString(uint256,uint8)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L35-L73) contains a tautology or contradiction:
        - [i >= 0](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L65)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L35-L73


 - [ ] ID-53
[Salary.create(address,uint256,uint32,uint32,uint32,uint128)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L72-L102) contains a tautology or contradiction:
        - [require(bool,string)(cliffPercent <= 1e18,Salary: cliff too large)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L84)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L72-L102


 - [ ] ID-54
[RevertingERC20Mock.transfer(address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/RevertingERC20Mock.sol#L30-L38) contains a tautology or contradiction:
        - [require(bool,string)(amount >= 0,TokenB: amount should be > 0)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/RevertingERC20Mock.sol#L32)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/RevertingERC20Mock.sol#L30-L38


## unchecked-lowlevel
Impact: Medium
Confidence: Medium
 - [ ] ID-55
[BoringAddress.sendNative(address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L15-L19) ignores return value by [(success) = to.call{value: amount}()](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L17)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L15-L19


 - [ ] ID-56
[WETH9Mock.withdraw(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/WETH9Mock.sol#L25-L31) ignores return value by [(success,None) = msg.sender.call{value: wad}()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/WETH9Mock.sol#L29)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/WETH9Mock.sol#L25-L31


 - [ ] ID-57
[Address.sendValue(address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L60-L65) ignores return value by [(success) = recipient.call{value: amount}()](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L63)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L60-L65


## uninitialized-local
Impact: Medium
Confidence: Medium
 - [ ] ID-58
[YieldOptions.create(uint32,uint32,uint128,uint32).option](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L100) is a local variable never initialized

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L100


 - [ ] ID-59
[String.numToString(uint256,uint8).j](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L37) is a local variable never initialized

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L37


 - [ ] ID-60
[String.numToString(uint256,uint8).result](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L38) is a local variable never initialized

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L38


 - [ ] ID-61
[Salary.create(address,uint256,uint32,uint32,uint32,uint128).salary](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L91) is a local variable never initialized

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L91


 - [ ] ID-62
[YieldBoxURIBuilder.uri(Asset,NativeToken,uint256,address).details](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxURIBuilder.sol#L85) is a local variable never initialized

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxURIBuilder.sol#L85


 - [ ] ID-63
[YieldOptions.withdrawEarly(uint256,uint256,address).currencyAmount](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L227) is a local variable never initialized

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L227


 - [ ] ID-64
[YieldOptions.withdrawEarly(uint256,uint256,address).assetAmount](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L226) is a local variable never initialized

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L226


## unused-return
Impact: Medium
Confidence: Medium
 - [ ] ID-65
[MasterContractFullCycleMock.run()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44) ignores return value by [yieldBox.withdraw(id,deployer,deployer,1000,0)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L33)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44


 - [ ] ID-66
[MasterContractFullCycleMock.run()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44) ignores return value by [yieldBox.deposit(TokenType.ERC20,token,tokenStrategy,0,deployer,deployer,1000,0)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L30)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44


 - [ ] ID-67
[MasterContractFullCycleMock.run()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44) ignores return value by [yieldBox.withdraw(id,deployer,deployer,1000,0)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L39)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44


 - [ ] ID-68
[HelloWorld.deposit(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L21-L25) ignores return value by [(None,shares) = yieldBox.depositAsset(assetId,msg.sender,address(this),amount,0)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L23)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L21-L25


 - [ ] ID-69
[Tokenizer.deposit(uint256,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Tokenizer.sol#L14-L26) ignores return value by [yieldBox.createToken(string(string.concat(Tokenized ,bytes(yieldBox.name(sourceAsset)))),string(string.concat(t,bytes(yieldBox.symbol(sourceAsset)))),18,)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Tokenizer.sol#L17-L22)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Tokenizer.sol#L14-L26


 - [ ] ID-70
[MasterContractFullCycleMock.run()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44) ignores return value by [yieldBox.deposit(TokenType.ERC1155,erc1155,erc1155Strategy,42,deployer,deployer,0,1000_00000000)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L37)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44


 - [ ] ID-71
[MasterContractFullCycleMock.run()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44) ignores return value by [yieldBox.withdraw(id + 1,deployer,deployer,1000,0)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L43)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44


 - [ ] ID-72
[MasterContractFullCycleMock.run()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44) ignores return value by [yieldBox.depositETH{value: 1000}(ethStrategy,deployer,1000)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L42)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44


 - [ ] ID-73
[MasterContractFullCycleMock.run()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44) ignores return value by [yieldBox.withdraw(id,deployer,deployer,0,1000_00000000)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L34)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44


 - [ ] ID-74
[MasterContractFullCycleMock.run()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44) ignores return value by [yieldBox.withdraw(id,deployer,deployer,0,1000_00000000)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L40)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44


 - [ ] ID-75
[HelloWorld.withdraw()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L34-L37) ignores return value by [yieldBox.withdraw(assetId,address(this),msg.sender,0,yieldBoxShares[msg.sender])](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L35)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L34-L37


 - [ ] ID-76
[MasterContractFullCycleMock.run()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44) ignores return value by [yieldBox.deposit(TokenType.ERC1155,erc1155,erc1155Strategy,42,deployer,deployer,1000,0)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L36)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44


 - [ ] ID-77
[LendingPair.liquidate(uint256,address,uint256,address,ISwapper)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440) ignores return value by [swapper.swap(market.collateral,market.asset,msg.sender,borrowShare,collateralShare)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L433)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440


 - [ ] ID-78
[MasterContractFullCycleMock.run()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44) ignores return value by [yieldBox.deposit(TokenType.ERC20,token,tokenStrategy,0,deployer,deployer,0,1000_00000000)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L31)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44


 - [ ] ID-79
[MasterContractMock.deposit(uint256,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractMock.sol#L15-L17) ignores return value by [yieldBox.depositAsset(id,msg.sender,address(this),0,amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractMock.sol#L16)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractMock.sol#L15-L17


## shadowing-local
Impact: Low
Confidence: High
 - [ ] ID-80
[YieldBox._transferBatch(address,address,uint256[],uint256[]).ids](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L316) shadows:
        - [AssetRegister.ids](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/AssetRegister.sol#L30) (state variable)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L316


 - [ ] ID-81
[IYieldBox.owner(uint256).owner](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IYieldBox.sol#L29) shadows:
        - [IYieldBox.owner(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IYieldBox.sol#L29) (function)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IYieldBox.sol#L29


 - [ ] ID-82
[IYieldBox.wrappedNative().wrappedNative](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IYieldBox.sol#L8) shadows:
        - [IYieldBox.wrappedNative()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IYieldBox.sol#L8) (function)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IYieldBox.sol#L8


 - [ ] ID-83
[NativeTokenFactory.createToken(string,string,uint8,string).uri](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/NativeTokenFactory.sol#L90) shadows:
        - [ERC1155.uri(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/ERC1155.sol#L123-L125) (function)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/NativeTokenFactory.sol#L90


 - [ ] ID-84
[IYieldBox.totalSupply(uint256).totalSupply](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IYieldBox.sol#L31) shadows:
        - [IYieldBox.totalSupply(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IYieldBox.sol#L31) (function)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IYieldBox.sol#L31


## missing-zero-check
Impact: Low
Confidence: Medium
 - [ ] ID-85
[BoringOwnable.transferOwnership(address,bool,bool).newOwner](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L27) lacks a zero-check on :
                - [pendingOwner = newOwner](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L41)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L27


 - [ ] ID-86
[ERC1155ReceiverMock.onERC1155Received(address,address,uint256,uint256,bytes)._operator](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L18) lacks a zero-check on :
                - [operator = _operator](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L25)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L18


 - [ ] ID-87
[ERC1155ReceiverMock.onERC1155BatchReceived(address,address,uint256[],uint256[],bytes)._from](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L37) lacks a zero-check on :
                - [from = _from](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L44)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L37


 - [ ] ID-88
[ERC1155StrategyMock.constructor(IYieldBox,address,uint256).token](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155StrategyMock.sol#L25) lacks a zero-check on :
                - [contractAddress = token](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155StrategyMock.sol#L29)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155StrategyMock.sol#L25


 - [ ] ID-89
[ERC20StrategyMock.constructor(IYieldBox,address).token](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC20StrategyMock.sol#L26) lacks a zero-check on :
                - [contractAddress = token](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC20StrategyMock.sol#L28)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC20StrategyMock.sol#L26


 - [ ] ID-90
[ERC721StrategyMock.constructor(IYieldBox,address,uint256).token](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC721StrategyMock.sol#L24) lacks a zero-check on :
                - [contractAddress = token](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC721StrategyMock.sol#L26)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC721StrategyMock.sol#L24


 - [ ] ID-91
[ERC1155ReceiverMock.onERC1155BatchReceived(address,address,uint256[],uint256[],bytes)._operator](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L36) lacks a zero-check on :
                - [operator = _operator](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L43)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L36


 - [ ] ID-92
[ERC1155ReceiverMock.onERC1155Received(address,address,uint256,uint256,bytes)._from](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L19) lacks a zero-check on :
                - [from = _from](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L26)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L19


## calls-loop
Impact: Low
Confidence: Medium
 - [ ] ID-93
[BaseBoringBatchable.batch(bytes[],bool)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L35-L42) has external calls inside a loop: [(success,result) = address(this).delegatecall(calls[i])](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L37)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L35-L42


## reentrancy-benign
Impact: Low
Confidence: Medium
 - [ ] ID-94
Reentrancy in [YieldSwap.create(uint32,uint32)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L34-L43):
        External calls:
        - [lpAssetId = yieldBox.createToken(YieldBox LP Token,YLP,18,)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L39)
        State variables written after the call(s):
        - [pairLookup[asset0][asset1] = pairId](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L41)
        - [pairs.push(Pair(0,0,asset0,asset1,lpAssetId,0))](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L42)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L34-L43


 - [ ] ID-95
Reentrancy in [YieldOptions.create(uint32,uint32,uint128,uint32)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L94-L138):
        External calls:
        - [option.optionAssetId = yieldBox.createToken(YieldOption,string(abi.encodePacked(yo,yieldBox.symbol(option.asset),:,yieldBox.symbol(option.currency), ,String.numToString(option.price,yieldBox.decimals(option.currency)))),18,)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L105-L119)
        - [option.minterAssetId = yieldBox.createToken(YieldOptionMinter,string(abi.encodePacked(ym,yieldBox.symbol(option.asset),:,yieldBox.symbol(option.currency), ,String.numToString(option.price,yieldBox.decimals(option.currency)))),18,)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L120-L134)
        State variables written after the call(s):
        - [options.push(option)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L137)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L94-L138


 - [ ] ID-96
Reentrancy in [HelloWorld.deposit(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L21-L25):
        External calls:
        - [(None,shares) = yieldBox.depositAsset(assetId,msg.sender,address(this),amount,0)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L23)
        State variables written after the call(s):
        - [yieldBoxShares[msg.sender] += shares](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L24)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L21-L25


 - [ ] ID-97
Reentrancy in [LendingPair.createMarket(uint32,uint32,IOracle,bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L107-L126):
        External calls:
        - [marketId = yieldBox.createToken(string(abi.encodePacked(yieldBox.name(collateral_),/,yieldBox.name(asset_),-,oracle_.name(oracleData_))),string(abi.encodePacked(yieldBox.symbol(collateral_),/,yieldBox.symbol(asset_),-,oracle_.symbol(oracleData_))),18,)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L113-L118)
        State variables written after the call(s):
        - [marketList.push(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L125)
        - [(market.collateral,market.asset,market.oracle,market.oracleData) = (collateral_,asset_,oracle_,oracleData_)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L121)
        - [market.interestPerSecond = STARTING_INTEREST_PER_SECOND](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L122)
        - [market.assetId = marketId](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L123)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L107-L126


 - [ ] ID-98
Reentrancy in [Salary.create(address,uint256,uint32,uint32,uint32,uint128)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L72-L102):
        External calls:
        - [yieldBox.transfer(msg.sender,address(this),assetId,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L88)
        State variables written after the call(s):
        - [salaries.push(salary)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L99)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L72-L102


## reentrancy-events
Impact: Low
Confidence: Medium
 - [ ] ID-99
Reentrancy in [LendingPair.removeAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L321-L328):
        External calls:
        - [accrue(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L326)
                - [market.interestPerSecond = ((market.interestPerSecond * INTEREST_ELASTICITY) / scale).to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L160)
        - [share = _removeAsset(marketId,to,fraction)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L327)
                - [yieldBox.burn(marketId,msg.sender,fraction)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L311)
                - [yieldBox.transfer(address(this),to,marketId,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L314)
        Event emitted after the call(s):
        - [LogRemoveAsset(msg.sender,to,share,fraction)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L313)
                - [share = _removeAsset(marketId,to,fraction)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L327)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L321-L328


 - [ ] ID-100
Reentrancy in [LendingPair.removeCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L260-L268):
        External calls:
        - [accrue(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L266)
                - [market.interestPerSecond = ((market.interestPerSecond * INTEREST_ELASTICITY) / scale).to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L160)
        - [_removeCollateral(marketId,to,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L267)
                - [yieldBox.transfer(address(this),to,market.collateral,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L253)
        Event emitted after the call(s):
        - [LogRemoveCollateral(msg.sender,to,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L254)
                - [_removeCollateral(marketId,to,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L267)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L260-L268


 - [ ] ID-101
Reentrancy in [YieldBox._withdrawNFT(Asset,uint256,address,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L247-L261):
        External calls:
        - [asset.strategy.withdraw(to,1)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L256)
        Event emitted after the call(s):
        - [Withdraw(msg.sender,from,to,assetId,1,1,1,1)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L258)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L247-L261


 - [ ] ID-102
Reentrancy in [LendingPair._removeAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L302-L315):
        External calls:
        - [yieldBox.burn(marketId,msg.sender,fraction)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L311)
        Event emitted after the call(s):
        - [LogRemoveAsset(msg.sender,to,share,fraction)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L313)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L302-L315


 - [ ] ID-103
Reentrancy in [YieldBox.depositETHAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L196-L215):
        External calls:
        - [wrappedNative.deposit{value: amount}()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L207)
        - [wrappedNative.safeTransfer(address(asset.strategy),amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L209)
        - [asset.strategy.deposited(amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L210)
        External calls sending eth:
        - [wrappedNative.deposit{value: amount}()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L207)
        Event emitted after the call(s):
        - [Deposited(msg.sender,msg.sender,to,assetId,amount,share,amountOut,shareOut,false)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L212)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L196-L215


 - [ ] ID-104
Reentrancy in [LendingPair.borrow(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L351-L359):
        External calls:
        - [updateExchangeRate(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L356)
                - [(updated,rate) = market.oracle.get(market.oracleData)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L215)
        - [accrue(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L357)
                - [market.interestPerSecond = ((market.interestPerSecond * INTEREST_ELASTICITY) / scale).to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L160)
        - [(part,share) = _borrow(marketId,to,amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L358)
                - [yieldBox.transfer(address(this),to,market.asset,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L345)
        Event emitted after the call(s):
        - [LogBorrow(msg.sender,to,amount,part)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L340)
                - [(part,share) = _borrow(marketId,to,amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L358)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L351-L359


 - [ ] ID-105
Reentrancy in [WETH9Mock.withdraw(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/WETH9Mock.sol#L25-L31):
        External calls:
        - [(success,None) = msg.sender.call{value: wad}()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/WETH9Mock.sol#L29)
        Event emitted after the call(s):
        - [Withdrawal(msg.sender,wad)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/WETH9Mock.sol#L30)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/WETH9Mock.sol#L25-L31


 - [ ] ID-106
Reentrancy in [LendingPair.addCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L230-L241):
        External calls:
        - [yieldBox.transfer(msg.sender,address(this),market.collateral,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L239)
        Event emitted after the call(s):
        - [LogAddCollateral(msg.sender,to,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L240)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L230-L241


 - [ ] ID-107
Reentrancy in [Salary.create(address,uint256,uint32,uint32,uint32,uint128)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L72-L102):
        External calls:
        - [yieldBox.transfer(msg.sender,address(this),assetId,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L88)
        Event emitted after the call(s):
        - [LogCreate(msg.sender,recipient,assetId,cliffTimestamp,endTimestamp,cliffPercent,share,salaryId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L101)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L72-L102


 - [ ] ID-108
Reentrancy in [YieldOptions.swap(uint256,uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L274-L288):
        External calls:
        - [yieldBox.transfer(msg.sender,address(this),option.currency,currencyAmount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L282)
        - [yieldBox.transfer(address(this),msg.sender,option.asset,assetAmount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L283)
        - [yieldBox.mint(option.optionAssetId,to,currencyAmount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L284)
        Event emitted after the call(s):
        - [Swap(optionId,msg.sender,currencyAmount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L287)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L274-L288


 - [ ] ID-109
Reentrancy in [Salary._withdraw(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L164-L169):
        External calls:
        - [yieldBox.transfer(address(this),to,salaries[salaryId].assetId,pendingShare)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L167)
        Event emitted after the call(s):
        - [LogWithdraw(salaryId,to,pendingShare)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L168)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L164-L169


 - [ ] ID-110
Reentrancy in [LendingPair.liquidate(uint256,address,uint256,address,ISwapper)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440):
        External calls:
        - [(_exchangeRate) = updateExchangeRate(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L406)
                - [(updated,rate) = market.oracle.get(market.oracleData)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L215)
        - [accrue(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L407)
                - [market.interestPerSecond = ((market.interestPerSecond * INTEREST_ELASTICITY) / scale).to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L160)
        - [swapper.swap(market.collateral,market.asset,msg.sender,borrowShare,collateralShare)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L433)
        - [yieldBox.transfer(msg.sender,address(this),market.asset,borrowShare)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L436)
        - [yieldBox.transfer(address(this),to,market.collateral,collateralShare)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L431)
        - [yieldBox.transfer(address(this),address(swapper),market.collateral,collateralShare)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L431)
        Event emitted after the call(s):
        - [LogLiquidate(marketId,user,borrowPart,to,swapper)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L439)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440


 - [ ] ID-111
Reentrancy in [LendingPair.repay(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L382-L389):
        External calls:
        - [accrue(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L387)
                - [market.interestPerSecond = ((market.interestPerSecond * INTEREST_ELASTICITY) / scale).to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L160)
        - [amount = _repay(marketId,to,part)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L388)
                - [yieldBox.transfer(msg.sender,address(this),market.asset,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L373)
        Event emitted after the call(s):
        - [LogRepay(msg.sender,to,amount,part)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L375)
                - [amount = _repay(marketId,to,part)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L388)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L382-L389


 - [ ] ID-112
Reentrancy in [YieldOptions.withdrawEarly(uint256,uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L211-L248):
        External calls:
        - [yieldBox.burn(option.optionAssetId,msg.sender,amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L222)
        - [yieldBox.burn(option.minterAssetId,msg.sender,amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L223)
        - [yieldBox.transfer(address(this),to,option.currency,currencyAmount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L243)
        - [yieldBox.transfer(address(this),to,option.asset,assetAmount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L244)
        Event emitted after the call(s):
        - [Withdraw(optionId,msg.sender,amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L247)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L211-L248


 - [ ] ID-113
Reentrancy in [YieldOptions.withdraw(uint256,uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L177-L204):
        External calls:
        - [yieldBox.transfer(address(this),to,option.asset,(yieldBox.totalSupply(option.currency) * amount) / yieldBox.totalSupply(option.minterAssetId))](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L188-L193)
        - [yieldBox.transfer(address(this),to,option.asset,(yieldBox.totalSupply(option.currency) * amount) / yieldBox.totalSupply(option.minterAssetId))](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L194-L199)
        - [yieldBox.burn(option.minterAssetId,msg.sender,amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L200)
        Event emitted after the call(s):
        - [Withdraw(optionId,msg.sender,amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L203)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L177-L204


 - [ ] ID-114
Reentrancy in [YieldBox.depositAsset(uint256,address,address,uint256,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L118-L160):
        External calls:
        - [IERC20(asset.contractAddress).safeTransferFrom(from,address(asset.strategy),amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L144)
        - [IERC1155(asset.contractAddress).safeTransferFrom(from,address(asset.strategy),asset.tokenId,amount,)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L151)
        - [asset.strategy.deposited(amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L155)
        Event emitted after the call(s):
        - [Deposited(msg.sender,from,to,assetId,amount,share,amountOut,shareOut,false)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L157)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L118-L160


 - [ ] ID-115
Reentrancy in [LendingPair.borrow(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L351-L359):
        External calls:
        - [updateExchangeRate(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L356)
                - [(updated,rate) = market.oracle.get(market.oracleData)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L215)
        - [accrue(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L357)
                - [market.interestPerSecond = ((market.interestPerSecond * INTEREST_ELASTICITY) / scale).to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L160)
        Event emitted after the call(s):
        - [LogAccrue(0,STARTING_INTEREST_PER_SECOND,0)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L143)
                - [accrue(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L357)
        - [LogAccrue(extraAmount,market.interestPerSecond,utilization)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L175)
                - [accrue(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L357)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L351-L359


 - [ ] ID-116
Reentrancy in [LendingPair.addAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L292-L299):
        External calls:
        - [accrue(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L297)
                - [market.interestPerSecond = ((market.interestPerSecond * INTEREST_ELASTICITY) / scale).to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L160)
        - [fraction = _addAsset(marketId,to,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L298)
                - [yieldBox.mint(marketId,to,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L283)
                - [yieldBox.transfer(msg.sender,to,marketId,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L284)
        Event emitted after the call(s):
        - [LogAddAsset(msg.sender,to,share,fraction)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L285)
                - [fraction = _addAsset(marketId,to,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L298)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L292-L299


 - [ ] ID-117
Reentrancy in [LendingPair._repay(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L362-L376):
        External calls:
        - [yieldBox.transfer(msg.sender,address(this),market.asset,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L373)
        Event emitted after the call(s):
        - [LogRepay(msg.sender,to,amount,part)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L375)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L362-L376


 - [ ] ID-118
Reentrancy in [LendingPair.updateExchangeRate(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L212-L224):
        External calls:
        - [(updated,rate) = market.oracle.get(market.oracleData)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L215)
        Event emitted after the call(s):
        - [LogExchangeRate(rate)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L219)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L212-L224


 - [ ] ID-119
Reentrancy in [YieldBox._withdrawFungible(Asset,uint256,address,address,uint256,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L270-L296):
        External calls:
        - [asset.strategy.withdraw(to,amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L291)
        Event emitted after the call(s):
        - [Withdraw(msg.sender,from,to,assetId,amount,share,amountOut,shareOut)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L293)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L270-L296


 - [ ] ID-120
Reentrancy in [LendingPair._removeCollateral(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L244-L255):
        External calls:
        - [yieldBox.transfer(address(this),to,market.collateral,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L253)
        Event emitted after the call(s):
        - [LogRemoveCollateral(msg.sender,to,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L254)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L244-L255


 - [ ] ID-121
Reentrancy in [LendingPair.accrue(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176):
        External calls:
        - [market.interestPerSecond = ((market.interestPerSecond * INTEREST_ELASTICITY) / scale).to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L160)
        Event emitted after the call(s):
        - [LogAccrue(extraAmount,market.interestPerSecond,utilization)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L175)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176


 - [ ] ID-122
Reentrancy in [YieldBox.depositNFTAsset(uint256,address,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L168-L188):
        External calls:
        - [IERC721(asset.contractAddress).safeTransferFrom(from,address(asset.strategy),asset.tokenId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L181)
        - [asset.strategy.deposited(1)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L183)
        Event emitted after the call(s):
        - [Deposited(msg.sender,from,to,assetId,1,1,1,1,true)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L185)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L168-L188


 - [ ] ID-123
Reentrancy in [BoringFactory.deploy(address,bytes,bool)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67):
        External calls:
        - [IMasterContract(cloneAddress).init{value: msg.value}(data)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L64)
        Event emitted after the call(s):
        - [LogDeploy(masterContract,data,cloneAddress)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L66)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67


 - [ ] ID-124
Reentrancy in [LendingPair.liquidate(uint256,address,uint256,address,ISwapper)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440):
        External calls:
        - [(_exchangeRate) = updateExchangeRate(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L406)
                - [(updated,rate) = market.oracle.get(market.oracleData)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L215)
        - [accrue(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L407)
                - [market.interestPerSecond = ((market.interestPerSecond * INTEREST_ELASTICITY) / scale).to64()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L160)
        Event emitted after the call(s):
        - [LogAccrue(0,STARTING_INTEREST_PER_SECOND,0)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L143)
                - [accrue(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L407)
        - [LogAccrue(extraAmount,market.interestPerSecond,utilization)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L175)
                - [accrue(marketId)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L407)
        - [LogRemoveCollateral(user,to,collateralShare)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L421)
        - [LogRemoveCollateral(user,address(swapper),collateralShare)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L421)
        - [LogRepay(msg.sender,user,borrowAmount,borrowPart)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L422)
        - [LogRepay(address(swapper),user,borrowAmount,borrowPart)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L422)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L396-L440


 - [ ] ID-125
Reentrancy in [Salary.cancel(uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L185-L192):
        External calls:
        - [_withdraw(salaryId,salaries[salaryId].recipient)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L187)
                - [yieldBox.transfer(address(this),to,salaries[salaryId].assetId,pendingShare)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L167)
        - [yieldBox.transfer(address(this),to,salaries[salaryId].assetId,shareLeft)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L190)
        Event emitted after the call(s):
        - [LogCancel(salaryId,to,shareLeft)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L191)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L185-L192


 - [ ] ID-126
Reentrancy in [LendingPair._addAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L271-L286):
        External calls:
        - [yieldBox.mint(marketId,to,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L283)
        - [yieldBox.transfer(msg.sender,to,marketId,share)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L284)
        Event emitted after the call(s):
        - [LogAddAsset(msg.sender,to,share,fraction)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L285)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L271-L286


 - [ ] ID-127
Reentrancy in [YieldOptions.mint(uint256,uint256,address,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L149-L171):
        External calls:
        - [yieldBox.transfer(msg.sender,address(this),option.asset,amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L161)
        - [yieldBox.mint(option.optionAssetId,optionTo,amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L164)
        - [yieldBox.mint(option.minterAssetId,minterTo,amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L167)
        Event emitted after the call(s):
        - [Mint(optionId,msg.sender,amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L170)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L149-L171


 - [ ] ID-128
Reentrancy in [YieldOptions.exercise(uint256,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L254-L264):
        External calls:
        - [yieldBox.burn(option.optionAssetId,msg.sender,amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L259)
        - [yieldBox.transfer(msg.sender,address(this),option.asset,(amount * 1e18) / option.price)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L260)
        - [yieldBox.transfer(address(this),msg.sender,option.currency,amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L261)
        Event emitted after the call(s):
        - [Exercise(optionId,msg.sender,amount)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L263)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L254-L264


## timestamp
Impact: Low
Confidence: Medium
 - [ ] ID-129
[YieldOptions.exercise(uint256,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L254-L264) uses timestamp for comparisons
        Dangerous comparisons:
        - [require(bool,string)(block.timestamp < option.expiry,Option has expired)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L257)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L254-L264


 - [ ] ID-130
[Salary._available(Salary.UserSalary)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L104-L131) uses timestamp for comparisons
        Dangerous comparisons:
        - [block.timestamp < salary.cliffTimestamp](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L105)
        - [block.timestamp >= salary.endTimestamp](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L108)
        - [timeSinceCliff > 0](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L119)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L104-L131


 - [ ] ID-131
[YieldOptions.withdraw(uint256,uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L177-L204) uses timestamp for comparisons
        Dangerous comparisons:
        - [require(bool,string)(block.timestamp >= option.expiry,Option not yet expired)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L185)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L177-L204


 - [ ] ID-132
[LendingPair.accrue(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176) uses timestamp for comparisons
        Dangerous comparisons:
        - [elapsedTime == 0](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L134)
        - [market.totalBorrow.base == 0](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L139)
        - [market.interestPerSecond != STARTING_INTEREST_PER_SECOND](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L141)
        - [utilization < MINIMUM_TARGET_UTILIZATION](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L157)
        - [market.interestPerSecond < MINIMUM_INTEREST_PER_SECOND](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L162)
        - [utilization > MAXIMUM_TARGET_UTILIZATION](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L165)
        - [newInterestPerSecond > MAXIMUM_INTEREST_PER_SECOND](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L169)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L129-L176


 - [ ] ID-133
[ERC20.permit(address,address,uint256,uint256,uint8,bytes32,bytes32)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/ERC20.sol#L102-L120) uses timestamp for comparisons
        Dangerous comparisons:
        - [require(bool,string)(block.timestamp < deadline,ERC20: Expired)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/ERC20.sol#L112)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/ERC20.sol#L102-L120


 - [ ] ID-134
[YieldOptions.withdrawEarly(uint256,uint256,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L211-L248) uses timestamp for comparisons
        Dangerous comparisons:
        - [require(bool,string)(block.timestamp < option.expiry,Option not yet expired)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L219)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L211-L248


 - [ ] ID-135
[YieldOptions.mint(uint256,uint256,address,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L149-L171) uses timestamp for comparisons
        Dangerous comparisons:
        - [require(bool,string)(block.timestamp < option.expiry,Option expired)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L157)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L149-L171


 - [ ] ID-136
[ReturnFalseERC20Mock.permit(address,address,uint256,uint256,uint8,bytes32,bytes32)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ReturnFalseERC20Mock.sol#L75-L105) uses timestamp for comparisons
        Dangerous comparisons:
        - [require(bool,string)(block.timestamp < deadline,ReturnFalseERC20: Expired)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ReturnFalseERC20Mock.sol#L84)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ReturnFalseERC20Mock.sol#L75-L105


 - [ ] ID-137
[YieldBoxPermit.permit(address,address,uint256,uint256,uint8,bytes32,bytes32)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxPermit.sol#L42-L61) uses timestamp for comparisons
        Dangerous comparisons:
        - [require(bool,string)(block.timestamp <= deadline,YieldBoxPermit: expired deadline)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxPermit.sol#L51)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxPermit.sol#L42-L61


 - [ ] ID-138
[YieldBoxPermit.permitAll(address,address,uint256,uint8,bytes32,bytes32)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxPermit.sol#L72-L90) uses timestamp for comparisons
        Dangerous comparisons:
        - [require(bool,string)(block.timestamp <= deadline,YieldBoxPermit: expired deadline)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxPermit.sol#L80)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxPermit.sol#L72-L90


## assembly
Impact: Informational
Confidence: High
 - [ ] ID-139
[Base64.encode(bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L11-L69) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L23-L66)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L11-L69


 - [ ] ID-140
[Domain._domainSeparator()](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L35-L41) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L37-L39)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L35-L41


 - [ ] ID-141
[ReturnFalseERC20Mock.DOMAIN_SEPARATOR()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ReturnFalseERC20Mock.sol#L67-L73) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ReturnFalseERC20Mock.sol#L69-L71)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ReturnFalseERC20Mock.sol#L67-L73


 - [ ] ID-142
[ECDSA.tryRecover(bytes32,bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L55-L72) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L63-L67)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L55-L72


 - [ ] ID-143
[Domain.constructor()](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L23-L29) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L25-L27)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L23-L29


 - [ ] ID-144
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L66-L70)
        - [INLINE ASM](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L86-L93)
        - [INLINE ASM](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L100-L109)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L135


 - [ ] ID-145
[Strings.toString(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L18-L38) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L24-L26)
        - [INLINE ASM](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L30-L32)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L18-L38


 - [ ] ID-146
[ERC721._checkOnERC721Received(address,address,uint256,bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L429-L451) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L443-L445)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L429-L451


 - [ ] ID-147
[BoringAddress.isContract(address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L7-L13) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L9-L11)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L7-L13


 - [ ] ID-148
[BaseBoringBatchable._getRevertMsg(bytes)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L17-L26) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L21-L24)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L17-L26


 - [ ] ID-149
[BoringFactory.deploy(address,bytes,bool)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L45-L51)
        - [INLINE ASM](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L53-L59)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67


 - [ ] ID-150
[Address._revert(bytes,string)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L231-L243) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L236-L239)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L231-L243


## boolean-equal
Impact: Informational
Confidence: High
 - [ ] ID-151
[ERC1155._requireTransferAllowed(address,bool)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/ERC1155.sol#L78-L80) compares to a boolean constant:
        -[require(bool,string)(_from == msg.sender || _approved || isApprovedForAll[_from][msg.sender] == true,Transfer not allowed)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/ERC1155.sol#L79)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/ERC1155.sol#L78-L80


## pragma
Impact: Informational
Confidence: High
 - [ ] ID-152
Different versions of Solidity are used:
        - Version used: ['^0.8.0', '^0.8.1', '^0.8.9']
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L25)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxRebase.sol#L4)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IStrategy.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IYieldBox.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155StrategyMock.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC20StrategyMock.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC721StrategyMock.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/YieldBoxRebaseMock.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldApp.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/BaseBufferStrategy.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/BaseStrategy.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/ERC20WithoutStrategy.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingBufferStrategy.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingSimpleStrategy.sol#L3)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L5)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/ERC20.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC1155.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC1155TokenReceiver.sol#L3)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC165.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC20.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721TokenReceiver.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IMasterContract.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/token/ERC721/IERC721.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/token/ERC721/extensions/IERC721Metadata.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Context.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Counters.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/introspection/ERC165.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/introspection/IERC165.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxPermit.sol#L3)
        - [^0.8.1](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L4)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/AssetRegister.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/BoringMath.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/ERC1155.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/ERC1155TokenReceiver.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/ERC721Receiver.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/ERC721TokenReceiver.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/NativeTokenFactory.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L24)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxRebase.sol#L3)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxURIBuilder.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/enums/YieldBoxTokenType.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IStrategy.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IWrappedNative.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IYieldBox.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155Mock.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155StrategyMock.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC20Mock.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC20StrategyMock.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC721Mock.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC721StrategyMock.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ExternalFunctionMock.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MaliciousMasterContractMock.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L3)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractMock.sol#L3)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ReturnFalseERC20Mock.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/RevertingERC20Mock.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/SushiBarMock.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/WETH9Mock.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/YieldBoxRebaseMock.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Escrow.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Tokenizer.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldApp.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L3)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/IOracle.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/ISwapper.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/BaseBufferStrategy.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/BaseStrategy.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/ERC20WithoutStrategy.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingBufferStrategy.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingSimpleStrategy.sol#L2)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L3


## solc-version
Impact: Informational
Confidence: High
 - [ ] ID-153
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L4) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L4


 - [ ] ID-154
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/ERC1155TokenReceiver.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/ERC1155TokenReceiver.sol#L2


 - [ ] ID-155
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC20.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC20.sol#L2


 - [ ] ID-156
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L4) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L4


 - [ ] ID-157
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxPermit.sol#L3) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxPermit.sol#L3


 - [ ] ID-158
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155StrategyMock.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155StrategyMock.sol#L2


 - [ ] ID-159
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Escrow.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Escrow.sol#L2


 - [ ] ID-160
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/helloworld.sol#L2


 - [ ] ID-161
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/enums/YieldBoxTokenType.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/enums/YieldBoxTokenType.sol#L2


 - [ ] ID-162
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Context.sol#L4) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Context.sol#L4


 - [ ] ID-163
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/WETH9Mock.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/WETH9Mock.sol#L2


 - [ ] ID-164
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol#L2


 - [ ] ID-165
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IWrappedNative.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IWrappedNative.sol#L2


 - [ ] ID-166
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC1155TokenReceiver.sol#L3) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC1155TokenReceiver.sol#L3


 - [ ] ID-167
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L4) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L4


 - [ ] ID-168
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/ERC1155.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/ERC1155.sol#L2


 - [ ] ID-169
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721TokenReceiver.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721TokenReceiver.sol#L2


 - [ ] ID-170
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC1155.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC1155.sol#L2


 - [ ] ID-171
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L4) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L4


 - [ ] ID-172
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L2


 - [ ] ID-173
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/ISwapper.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/ISwapper.sol#L2


 - [ ] ID-174
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldApp.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldApp.sol#L2


 - [ ] ID-175
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L2


 - [ ] ID-176
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IStrategy.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IStrategy.sol#L2


 - [ ] ID-177
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155Mock.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155Mock.sol#L2


 - [ ] ID-178
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingBufferStrategy.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingBufferStrategy.sol#L2


 - [ ] ID-179
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L24) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBox.sol#L24


 - [ ] ID-180
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC165.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC165.sol#L2


 - [ ] ID-181
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L3) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L3


 - [ ] ID-182
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol#L4) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol#L4


 - [ ] ID-183
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L2


 - [ ] ID-184
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxURIBuilder.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxURIBuilder.sol#L2


 - [ ] ID-185
Pragma version[^0.8.1](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L4) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L4


 - [ ] ID-186
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/AssetRegister.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/AssetRegister.sol#L2


 - [ ] ID-187
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ReturnFalseERC20Mock.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ReturnFalseERC20Mock.sol#L2


 - [ ] ID-188
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/NativeTokenFactory.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/NativeTokenFactory.sol#L2


 - [ ] ID-189
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L3) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L3


 - [ ] ID-190
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/BaseBufferStrategy.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/BaseBufferStrategy.sol#L2


 - [ ] ID-191
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L2


 - [ ] ID-192
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/YieldBoxRebaseMock.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/YieldBoxRebaseMock.sol#L2


 - [ ] ID-193
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721.sol#L2


 - [ ] ID-194
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/token/ERC721/extensions/IERC721Metadata.sol#L4) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/token/ERC721/extensions/IERC721Metadata.sol#L4


 - [ ] ID-195
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Counters.sol#L4) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Counters.sol#L4


 - [ ] ID-196
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractMock.sol#L3) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractMock.sol#L3


 - [ ] ID-197
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L2


 - [ ] ID-198
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/BaseStrategy.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/BaseStrategy.sol#L2


 - [ ] ID-199
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/ERC20.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/ERC20.sol#L2


 - [ ] ID-200
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/introspection/ERC165.sol#L4) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/introspection/ERC165.sol#L4


 - [ ] ID-201
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ExternalFunctionMock.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ExternalFunctionMock.sol#L2


 - [ ] ID-202
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L2


 - [ ] ID-203
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/SushiBarMock.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/SushiBarMock.sol#L2


 - [ ] ID-204
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/token/ERC721/IERC721.sol#L4) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/token/ERC721/IERC721.sol#L4


 - [ ] ID-205
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L2


 - [ ] ID-206
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/RevertingERC20Mock.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/RevertingERC20Mock.sol#L2


 - [ ] ID-207
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Tokenizer.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Tokenizer.sol#L2


 - [ ] ID-208
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC721StrategyMock.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC721StrategyMock.sol#L2


 - [ ] ID-209
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/BoringMath.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/BoringMath.sol#L2


 - [ ] ID-210
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MaliciousMasterContractMock.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MaliciousMasterContractMock.sol#L2


 - [ ] ID-211
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/ERC721Receiver.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/ERC721Receiver.sol#L2


 - [ ] ID-212
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IYieldBox.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IYieldBox.sol#L2


 - [ ] ID-213
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/ERC721TokenReceiver.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/ERC721TokenReceiver.sol#L2


 - [ ] ID-214
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxRebase.sol#L3) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxRebase.sol#L3


 - [ ] ID-215
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IMasterContract.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IMasterContract.sol#L2


 - [ ] ID-216
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L2


 - [ ] ID-217
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/ERC20WithoutStrategy.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/ERC20WithoutStrategy.sol#L2


 - [ ] ID-218
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L5) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L5


 - [ ] ID-219
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/introspection/IERC165.sol#L4) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/introspection/IERC165.sol#L4


 - [ ] ID-220
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L4) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L4


 - [ ] ID-221
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingSimpleStrategy.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingSimpleStrategy.sol#L2


 - [ ] ID-222
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC20Mock.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC20Mock.sol#L2


 - [ ] ID-223
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L2


 - [ ] ID-224
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/IOracle.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/IOracle.sol#L2


 - [ ] ID-225
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC20StrategyMock.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC20StrategyMock.sol#L2


 - [ ] ID-226
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L2


 - [ ] ID-227
solc-0.8.9 is not recommended for deployment

 - [ ] ID-228
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC721Mock.sol#L2) allows old versions

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC721Mock.sol#L2


## low-level-calls
Impact: Informational
Confidence: High
 - [ ] ID-229
Low level call in [BoringERC20.safeName(IERC20)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L45-L48):
        - [(success,data) = address(token).staticcall(abi.encodeWithSelector(SIG_NAME))](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L46)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L45-L48


 - [ ] ID-230
Low level call in [Address.functionCallWithValue(address,bytes,uint256,string)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L128-L137):
        - [(success,returndata) = target.call{value: value}(data)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L135)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L128-L137


 - [ ] ID-231
Low level call in [BaseBoringBatchable.batch(bytes[],bool)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L35-L42):
        - [(success,result) = address(this).delegatecall(calls[i])](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L37)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L35-L42


 - [ ] ID-232
Low level call in [WETH9Mock.withdraw(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/WETH9Mock.sol#L25-L31):
        - [(success,None) = msg.sender.call{value: wad}()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/WETH9Mock.sol#L29)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/WETH9Mock.sol#L25-L31


 - [ ] ID-233
Low level call in [BoringERC20.safeTransferFrom(IERC20,address,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L97-L105):
        - [(success,data) = address(token).call(abi.encodeWithSelector(SIG_TRANSFER_FROM,from,to,amount))](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L103)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L97-L105


 - [ ] ID-234
Low level call in [BoringERC20.safeSymbol(IERC20)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L37-L40):
        - [(success,data) = address(token).staticcall(abi.encodeWithSelector(SIG_SYMBOL))](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L38)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L37-L40


 - [ ] ID-235
Low level call in [BoringERC20.safeTotalSupply(IERC20)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L71-L75):
        - [(success,data) = address(token).staticcall(abi.encodeWithSelector(SIG_TOTALSUPPLY))](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L72)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L71-L75


 - [ ] ID-236
Low level call in [BoringERC20.safeBalanceOf(IERC20,address)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L62-L66):
        - [(success,data) = address(token).staticcall(abi.encodeWithSelector(SIG_BALANCE_OF,to))](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L63)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L62-L66


 - [ ] ID-237
Low level call in [BoringAddress.sendNative(address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L15-L19):
        - [(success) = to.call{value: amount}()](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L17)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L15-L19


 - [ ] ID-238
Low level call in [BoringERC20.safeDecimals(IERC20)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L53-L56):
        - [(success,data) = address(token).staticcall(abi.encodeWithSelector(SIG_DECIMALS))](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L54)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L53-L56


 - [ ] ID-239
Low level call in [Address.sendValue(address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L60-L65):
        - [(success) = recipient.call{value: amount}()](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L63)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L60-L65


 - [ ] ID-240
Low level call in [BoringERC20.safeTransfer(IERC20,address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L82-L89):
        - [(success,data) = address(token).call(abi.encodeWithSelector(SIG_TRANSFER,to,amount))](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L87)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L82-L89


 - [ ] ID-241
Low level call in [Address.functionStaticCall(address,bytes,string)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L155-L162):
        - [(success,returndata) = target.staticcall(data)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L160)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L155-L162


 - [ ] ID-242
Low level call in [Address.functionDelegateCall(address,bytes,string)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L180-L187):
        - [(success,returndata) = target.delegatecall(data)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L185)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L180-L187


## missing-inheritance
Impact: Informational
Confidence: High
 - [ ] ID-243
[SushiBarMock](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/SushiBarMock.sol#L9-L63) should inherit from [ISushiBar](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingBufferStrategy.sol#L13-L17)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/SushiBarMock.sol#L9-L63


## naming-convention
Impact: Informational
Confidence: High
 - [ ] ID-244
Parameter [ERC1155ReceiverMock.onERC1155BatchReceived(address,address,uint256[],uint256[],bytes)._values](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L39) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L39


 - [ ] ID-245
Constant [SushiStakingBufferStrategy.sushiBar](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingBufferStrategy.sol#L30) is not in UPPER_CASE_WITH_UNDERSCORES

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingBufferStrategy.sol#L30


 - [ ] ID-246
Variable [Domain._DOMAIN_SEPARATOR](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L15) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L15


 - [ ] ID-247
Parameter [ERC1155ReceiverMock.onERC1155Received(address,address,uint256,uint256,bytes)._id](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L20) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L20


 - [ ] ID-248
Function [ERC20.DOMAIN_SEPARATOR()](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/ERC20.sol#L90-L92) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/ERC20.sol#L90-L92


 - [ ] ID-249
Variable [EIP712._TYPE_HASH](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L37) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L37


 - [ ] ID-250
Function [ReturnFalseERC20Mock.DOMAIN_SEPARATOR()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ReturnFalseERC20Mock.sol#L67-L73) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ReturnFalseERC20Mock.sol#L67-L73


 - [ ] ID-251
Parameter [ERC1155ReceiverMock.onERC1155BatchReceived(address,address,uint256[],uint256[],bytes)._data](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L40) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L40


 - [ ] ID-252
Variable [Domain.DOMAIN_SEPARATOR_CHAIN_ID](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L16) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L16


 - [ ] ID-253
Constant [SushiStakingStrategy.sushi](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingSimpleStrategy.sol#L30) is not in UPPER_CASE_WITH_UNDERSCORES

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingSimpleStrategy.sol#L30


 - [ ] ID-254
Variable [EIP712._CACHED_THIS](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L33) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L33


 - [ ] ID-255
Parameter [ERC1155ReceiverMock.onERC1155Received(address,address,uint256,uint256,bytes)._operator](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L18) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L18


 - [ ] ID-256
Parameter [ERC1155ReceiverMock.onERC1155BatchReceived(address,address,uint256[],uint256[],bytes)._operator](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L36


 - [ ] ID-257
Variable [EIP712._CACHED_CHAIN_ID](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L32) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L32


 - [ ] ID-258
Parameter [SushiBarMock.leave(uint256)._share](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/SushiBarMock.sol#L43) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/SushiBarMock.sol#L43


 - [ ] ID-259
Parameter [ERC1155ReceiverMock.onERC1155BatchReceived(address,address,uint256[],uint256[],bytes)._from](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L37) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L37


 - [ ] ID-260
Function [ERC721.__unsafe_increaseBalance(address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L503-L505) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L503-L505


 - [ ] ID-261
Constant [SushiStakingStrategy.sushiBar](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingSimpleStrategy.sol#L31) is not in UPPER_CASE_WITH_UNDERSCORES

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingSimpleStrategy.sol#L31


 - [ ] ID-262
Variable [EIP712._HASHED_NAME](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L35) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L35


 - [ ] ID-263
Function [YieldBoxPermit.DOMAIN_SEPARATOR()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxPermit.sol#L109-L111) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/YieldBoxPermit.sol#L109-L111


 - [ ] ID-264
Parameter [ERC1155ReceiverMock.onERC1155BatchReceived(address,address,uint256[],uint256[],bytes)._ids](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L38) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L38


 - [ ] ID-265
Parameter [ERC1155ReceiverMock.onERC1155Received(address,address,uint256,uint256,bytes)._value](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L21) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L21


 - [ ] ID-266
Variable [EIP712._CACHED_DOMAIN_SEPARATOR](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L31) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L31


 - [ ] ID-267
Parameter [SushiBarMock.enter(uint256)._amount](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/SushiBarMock.sol#L22) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/SushiBarMock.sol#L22


 - [ ] ID-268
Variable [EIP712._HASHED_VERSION](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L36


 - [ ] ID-269
Parameter [ERC1155ReceiverMock.onERC1155Received(address,address,uint256,uint256,bytes)._from](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L19) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L19


 - [ ] ID-270
Constant [SushiStakingBufferStrategy.sushi](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingBufferStrategy.sol#L29) is not in UPPER_CASE_WITH_UNDERSCORES

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingBufferStrategy.sol#L29


 - [ ] ID-271
Parameter [ERC1155ReceiverMock.onERC1155Received(address,address,uint256,uint256,bytes)._data](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L22) is not in mixedCase

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC1155ReceiverMock.sol#L22


## similar-names
Impact: Informational
Confidence: Medium
 - [ ] ID-272
Variable [LendingPair.MAXIMUM_INTEREST_PER_SECOND](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L88) is too similar to [LendingPair.MINIMUM_INTEREST_PER_SECOND](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L87)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L88


 - [ ] ID-273
Variable [BaseERC1155Strategy.constructor(IYieldBox,address,uint256)._contractAddress](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/BaseStrategy.sol#L64) is too similar to [IStrategy.contractAddress().contractAddress_](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IStrategy.sol#L36)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/BaseStrategy.sol#L64


 - [ ] ID-274
Variable [BaseERC20Strategy.constructor(IYieldBox,address)._contractAddress](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/BaseStrategy.sol#L54) is too similar to [IStrategy.contractAddress().contractAddress_](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IStrategy.sol#L36)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/BaseStrategy.sol#L54


 - [ ] ID-275
Variable [LendingPair.MAXIMUM_TARGET_UTILIZATION](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L80) is too similar to [LendingPair.MINIMUM_TARGET_UTILIZATION](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L79)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/lending/Lending.sol#L80


 - [ ] ID-276
Variable [BaseERC20BufferStrategy.constructor(IYieldBox,address)._contractAddress](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/BaseBufferStrategy.sol#L101) is too similar to [IStrategy.contractAddress().contractAddress_](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IStrategy.sol#L36)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/BaseBufferStrategy.sol#L101


## too-many-digits
Impact: Informational
Confidence: Medium
 - [ ] ID-277
[BoringFactory.deploy(address,bytes,bool)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67) uses literals with too many digits:
        - [mstore(uint256,uint256)(clone_deploy_asm_0 + 0x28,0x5af43d82803e903d91602b57fd5bf30000000000000000000000000000000000)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L49)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67


 - [ ] ID-278
[MasterContractFullCycleMock.run()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44) uses literals with too many digits:
        - [yieldBox.deposit(TokenType.ERC20,token,tokenStrategy,0,deployer,deployer,0,1000_00000000)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L31)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44


 - [ ] ID-279
[BoringFactory.deploy(address,bytes,bool)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67) uses literals with too many digits:
        - [mstore(uint256,uint256)(clone_deploy_asm_0,0x3d602d80600a3d3981f3363d3d373d3d3d363d73000000000000000000000000)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L47)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67


 - [ ] ID-280
[MasterContractFullCycleMock.run()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44) uses literals with too many digits:
        - [yieldBox.deposit(TokenType.ERC1155,erc1155,erc1155Strategy,42,deployer,deployer,0,1000_00000000)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L37)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44


 - [ ] ID-281
[MasterContractFullCycleMock.run()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44) uses literals with too many digits:
        - [yieldBox.withdraw(id,deployer,deployer,0,1000_00000000)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L34)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44


 - [ ] ID-282
[BoringFactory.deploy(address,bytes,bool)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67) uses literals with too many digits:
        - [mstore(uint256,uint256)(clone_deploy_asm_1,0x3d602d80600a3d3981f3363d3d373d3d3d363d73000000000000000000000000)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L55)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67


 - [ ] ID-283
[MasterContractFullCycleMock.run()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44) uses literals with too many digits:
        - [yieldBox.withdraw(id,deployer,deployer,0,1000_00000000)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L40)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/MasterContractFullCycleMock.sol#L29-L44


 - [ ] ID-284
[BoringFactory.deploy(address,bytes,bool)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67) uses literals with too many digits:
        - [mstore(uint256,uint256)(clone_deploy_asm_1 + 0x28,0x5af43d82803e903d91602b57fd5bf30000000000000000000000000000000000)](https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L57)

https://github.com/Tapioca-DAO/YieldBox/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67


## unimplemented-functions
Impact: Informational
Confidence: High
 - [ ] ID-285
[BaseERC1155Strategy](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/BaseStrategy.sol#L59-L68) does not implement functions:
        - [BaseStrategy._currentBalance()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/BaseStrategy.sol#L20)
        - [BaseStrategy._deposited(uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/BaseStrategy.sol#L34)
        - [BaseStrategy._withdraw(address,uint256)](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/BaseStrategy.sol#L41)
        - [IStrategy.description()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IStrategy.sol#L26)
        - [IStrategy.name()](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/interfaces/IStrategy.sol#L23)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/BaseStrategy.sol#L59-L68


## unused-state
Impact: Informational
Confidence: High
 - [ ] ID-286
[SushiStakingBufferStrategy._balance](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingBufferStrategy.sol#L32) is never used in [SushiStakingBufferStrategy](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingBufferStrategy.sol#L19-L56)

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingBufferStrategy.sol#L32


## constable-states
Impact: Optimization
Confidence: High
 - [ ] ID-287
[WETH9Mock.symbol](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/WETH9Mock.sol#L6) should be constant

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/WETH9Mock.sol#L6


 - [ ] ID-288
[WETH9Mock.decimals](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/WETH9Mock.sol#L7) should be constant

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/WETH9Mock.sol#L7


 - [ ] ID-289
[SushiStakingBufferStrategy._balance](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingBufferStrategy.sol#L32) should be constant

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/strategies/SushiStakingBufferStrategy.sol#L32


 - [ ] ID-290
[WETH9Mock.name](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/WETH9Mock.sol#L5) should be constant

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/WETH9Mock.sol#L5


## immutable-states
Impact: Optimization
Confidence: High
 - [ ] ID-291
[ReturnFalseERC20Mock.totalSupply](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ReturnFalseERC20Mock.sol#L12) should be immutable

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ReturnFalseERC20Mock.sol#L12


 - [ ] ID-292
[YieldApp.yieldBox](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldApp.sol#L9) should be immutable

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldApp.sol#L9


 - [ ] ID-293
[Salary.yieldBox](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L12) should be immutable

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/salary.sol#L12


 - [ ] ID-294
[Tokenizer.yieldBox](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Tokenizer.sol#L6) should be immutable

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Tokenizer.sol#L6


 - [ ] ID-295
[SushiBarMock.sushi](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/SushiBarMock.sol#L10) should be immutable

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/SushiBarMock.sol#L10


 - [ ] ID-296
[YieldOptions.yieldBox](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L86) should be immutable

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Options.sol#L86


 - [ ] ID-297
[Escrow.yieldBox](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Escrow.sol#L15) should be immutable

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/Escrow.sol#L15


 - [ ] ID-298
[RevertingERC20Mock.totalSupply](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/RevertingERC20Mock.sol#L9) should be immutable

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/RevertingERC20Mock.sol#L9


 - [ ] ID-299
[ERC20Mock.totalSupply](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC20Mock.sol#L6) should be immutable

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/mocks/ERC20Mock.sol#L6


 - [ ] ID-300
[YieldSwap.yieldBox](https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L18) should be immutable

https://github.com/Tapioca-DAO/YieldBox/blob/main/contracts/samples/YieldSwap.sol#L18
