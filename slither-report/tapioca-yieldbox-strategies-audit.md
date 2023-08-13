Summary
 - [arbitrary-send-erc20](#arbitrary-send-erc20) (3 results) (High)
 - [arbitrary-send-eth](#arbitrary-send-eth) (9 results) (High)
 - [delegatecall-loop](#delegatecall-loop) (1 results) (High)
 - [encode-packed-collision](#encode-packed-collision) (1 results) (High)
 - [name-reused](#name-reused) (1 results) (High)
 - [unchecked-transfer](#unchecked-transfer) (9 results) (High)
 - [divide-before-multiply](#divide-before-multiply) (20 results) (Medium)
 - [incorrect-equality](#incorrect-equality) (5 results) (Medium)
 - [locked-ether](#locked-ether) (3 results) (Medium)
 - [reentrancy-no-eth](#reentrancy-no-eth) (9 results) (Medium)
 - [unchecked-lowlevel](#unchecked-lowlevel) (6 results) (Medium)
 - [uninitialized-local](#uninitialized-local) (8 results) (Medium)
 - [unused-return](#unused-return) (76 results) (Medium)
 - [shadowing-local](#shadowing-local) (8 results) (Low)
 - [missing-zero-check](#missing-zero-check) (20 results) (Low)
 - [calls-loop](#calls-loop) (6 results) (Low)
 - [reentrancy-benign](#reentrancy-benign) (2 results) (Low)
 - [reentrancy-events](#reentrancy-events) (12 results) (Low)
 - [timestamp](#timestamp) (7 results) (Low)
 - [assembly](#assembly) (21 results) (Informational)
 - [boolean-equal](#boolean-equal) (1 results) (Informational)
 - [pragma](#pragma) (1 results) (Informational)
 - [cyclomatic-complexity](#cyclomatic-complexity) (1 results) (Informational)
 - [dead-code](#dead-code) (6 results) (Informational)
 - [solc-version](#solc-version) (68 results) (Informational)
 - [low-level-calls](#low-level-calls) (22 results) (Informational)
 - [missing-inheritance](#missing-inheritance) (9 results) (Informational)
 - [naming-convention](#naming-convention) (89 results) (Informational)
 - [reentrancy-unlimited-gas](#reentrancy-unlimited-gas) (2 results) (Informational)
 - [similar-names](#similar-names) (12 results) (Informational)
 - [too-many-digits](#too-many-digits) (6 results) (Informational)
 - [unimplemented-functions](#unimplemented-functions) (1 results) (Informational)
 - [immutable-states](#immutable-states) (34 results) (Optimization)
## arbitrary-send-erc20
Impact: High
Confidence: High
 - [ ] ID-0
[BalancerVaultMock.joinPool(bytes32,address,address,IBalancerVault.JoinPoolRequest)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerVaultMock.sol#L20-L34) uses arbitrary from in transferFrom: [IERC20(address(request.assets[1])).safeTransferFrom(sender,address(this),request.maxAmountsIn[1])](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerVaultMock.sol#L26-L30)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerVaultMock.sol#L20-L34


 - [ ] ID-1
[YieldBox.depositAsset(uint256,address,address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L118-L160) uses arbitrary from in transferFrom: [IERC20(asset.contractAddress).safeTransferFrom(from,address(asset.strategy),amount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L144)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L118-L160


 - [ ] ID-2
[BalancerVaultMock.exitPool(bytes32,address,address,IBalancerVault.ExitPoolRequest)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerVaultMock.sol#L36-L51) uses arbitrary from in transferFrom: [IERC20(stablePool).safeTransferFrom(sender,address(this),request.minAmountsOut[1])](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerVaultMock.sol#L42-L46)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerVaultMock.sol#L36-L51


## arbitrary-send-eth
Impact: High
Confidence: Medium
 - [ ] ID-3
[StargateStrategy._stake(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L231-L238) sends eth to arbitrary user
        Dangerous calls:
        - [addLiquidityRouter.addLiquidityETH{value: amount}()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L234)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L231-L238


 - [ ] ID-4
[CurveEthStEthPoolMock.safeTransferETH(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/CurveEthStEthPoolMock.sol#L35-L38) sends eth to arbitrary user
        Dangerous calls:
        - [(success) = to.call{value: value}(new bytes(0))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/CurveEthStEthPoolMock.sol#L36)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/CurveEthStEthPoolMock.sol#L35-L38


 - [ ] ID-5
[CompoundStrategy._withdraw(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/CompoundStrategy.sol#L136-L162) sends eth to arbitrary user
        Dangerous calls:
        - [INative(address(wrappedNative)).deposit{value: address(this).balance}()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/CompoundStrategy.sol#L150-L152)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/CompoundStrategy.sol#L136-L162


 - [ ] ID-6
[StargateRouterMock.safeTransferETH(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/StargateRouterMock.sol#L26-L29) sends eth to arbitrary user
        Dangerous calls:
        - [(success) = to.call{value: value}(new bytes(0))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/StargateRouterMock.sol#L27)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/StargateRouterMock.sol#L26-L29


 - [ ] ID-7
[CompoundStrategy._deposited(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/CompoundStrategy.sol#L123-L133) sends eth to arbitrary user
        Dangerous calls:
        - [cToken.mint{value: queued}()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/CompoundStrategy.sol#L128)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/CompoundStrategy.sol#L123-L133


 - [ ] ID-8
[YieldBox.depositETHAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L196-L219) sends eth to arbitrary user
        Dangerous calls:
        - [wrappedNative.deposit{value: amount}()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L211)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L196-L219


 - [ ] ID-9
[StargateStrategy._withdraw(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L241-L269) sends eth to arbitrary user
        Dangerous calls:
        - [INative(address(wrappedNative)).deposit{value: toWithdraw}()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L259)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L241-L269


 - [ ] ID-10
[LidoEthStrategy._withdraw(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/LidoEthStrategy.sol#L141-L167) sends eth to arbitrary user
        Dangerous calls:
        - [INative(address(wrappedNative)).deposit{value: obtainedEth}()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/LidoEthStrategy.sol#L159)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/LidoEthStrategy.sol#L141-L167


 - [ ] ID-11
[LidoEthStrategy._deposited(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/LidoEthStrategy.sol#L128-L138) sends eth to arbitrary user
        Dangerous calls:
        - [stEth.submit{value: queued}(address(0))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/LidoEthStrategy.sol#L133)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/LidoEthStrategy.sol#L128-L138


## delegatecall-loop
Impact: High
Confidence: Medium
 - [ ] ID-12
[BaseBoringBatchable.batch(bytes[],bool)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L38-L45) has delegatecall inside a loop in a payable function: [(success,result) = address(this).delegatecall(calls[i])](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L40)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L38-L45


## encode-packed-collision
Impact: High
Confidence: High
 - [ ] ID-13
[YieldBoxURIBuilder.uri(Asset,NativeToken,uint256,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxURIBuilder.sol#L79-L135) calls abi.encodePacked() with multiple dynamic arguments:
        - [string(abi.encodePacked(data:application/json;base64,,abi.encodePacked({"name":",details.name,","symbol":",details.symbol,",,,,"properties":{"strategy":",uint256(uint160(address(asset.strategy))).toHexString(20),","tokenType":",details.tokenType,",properties,string(abi.encodePacked(,"tokenId":,asset.tokenId.toString())),}}).encode()))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxURIBuilder.sol#L110-L134)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxURIBuilder.sol#L79-L135


## name-reused
Impact: High
Confidence: High
 - [ ] ID-14
IERC20 is re-used:
        - [IERC20](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC20.sol#L4-L30)
        - [IERC20](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol#L9-L78)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC20.sol#L4-L30


## unchecked-transfer
Impact: High
Confidence: Medium
 - [ ] ID-15
[LPStakingMock.withdraw(uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/LPStakingMock.sol#L27-L30) ignores return value by [lpToken.transfer(msg.sender,amount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/LPStakingMock.sol#L29)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/LPStakingMock.sol#L27-L30


 - [ ] ID-16
[TricryptoLiquidityPoolMock.remove_liquidity_one_coin(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L38-L45) ignores return value by [token.transferFrom(msg.sender,address(this),_token_amount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L43)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L38-L45


 - [ ] ID-17
[IncentivesControllerMock.claimRewards(address[],uint256,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/IncentivesControllerMock.sol#L27-L35) ignores return value by [token.transfer(to,100 * 10 ** 18)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/IncentivesControllerMock.sol#L33)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/IncentivesControllerMock.sol#L27-L35


 - [ ] ID-18
[LPStakingMock.deposit(uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/LPStakingMock.sol#L18-L25) ignores return value by [lpToken.transferFrom(msg.sender,address(this),amount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/LPStakingMock.sol#L24)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/LPStakingMock.sol#L18-L25


 - [ ] ID-19
[StkAaveMock.claimRewards(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/StkAaveMock.sol#L45-L49) ignores return value by [token.transfer(to,amount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/StkAaveMock.sol#L48)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/StkAaveMock.sol#L45-L49


 - [ ] ID-20
[LPStakingMock.deposit(uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/LPStakingMock.sol#L18-L25) ignores return value by [reward.transfer(msg.sender,10 * 1e18)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/LPStakingMock.sol#L22)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/LPStakingMock.sol#L18-L25


 - [ ] ID-21
[TricryptoLiquidityPoolMock.add_liquidity(uint256[3],uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L31-L36) ignores return value by [token.transfer(msg.sender,amounts[2])](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L35)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L31-L36


 - [ ] ID-22
[CurveMinterMock.mint(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/CurveMinterMock.sol#L16-L19) ignores return value by [token.transfer(msg.sender,10 * 1e18)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/CurveMinterMock.sol#L18)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/CurveMinterMock.sol#L16-L19


 - [ ] ID-23
[RouterETHMock.addLiquidityETH()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/RouterETHMock.sol#L23-L26) ignores return value by [ERC20Mock(lpToken).transfer(msg.sender,msg.value - 1)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/RouterETHMock.sol#L25)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/RouterETHMock.sol#L23-L26


## divide-before-multiply
Impact: Medium
Confidence: Medium
 - [ ] ID-24
[Base64.encode(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L11-L69) performs a multiplication on the result of a division:
        - [encodedLen = 4 * ((data.length + 2) / 3)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L18)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L11-L69


 - [ ] ID-25
[FullMath.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L14-L106) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L67)
        - [inv *= 2 - denominator * inv](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L95)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L14-L106


 - [ ] ID-26
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L101)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L120)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134


 - [ ] ID-27
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134) performs a multiplication on the result of a division:
        - [prod0 = prod0 / twos](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L104)
        - [result = prod0 * inverse](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L131)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134


 - [ ] ID-28
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L101)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L122)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134


 - [ ] ID-29
[FullMath.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L14-L106) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L67)
        - [inv *= 2 - denominator * inv](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L91)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L14-L106


 - [ ] ID-30
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L101)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L125)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134


 - [ ] ID-31
[FullMath.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L14-L106) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L67)
        - [inv *= 2 - denominator * inv](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L93)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L14-L106


 - [ ] ID-32
[FullMath.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L14-L106) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L67)
        - [inv = (3 * denominator) ^ 2](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L87)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L14-L106


 - [ ] ID-33
[FullMath.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L14-L106) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L67)
        - [inv *= 2 - denominator * inv](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L94)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L14-L106


 - [ ] ID-34
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L101)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L124)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134


 - [ ] ID-35
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L101)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L123)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134


 - [ ] ID-36
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L101)
        - [inverse *= 2 - denominator * inverse](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L121)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134


 - [ ] ID-37
[FullMath.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L14-L106) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L67)
        - [inv *= 2 - denominator * inv](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L92)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L14-L106


 - [ ] ID-38
[FullMath.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L14-L106) performs a multiplication on the result of a division:
        - [prod0 = prod0 / twos](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L72)
        - [result = prod0 * inv](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L104)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L14-L106


 - [ ] ID-39
[YieldBoxRebase._toAmount(uint256,uint256,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L41-L61) performs a multiplication on the result of a division:
        - [amount = (share * totalAmount) / totalShares_](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L55)
        - [roundUp && (amount * totalShares_) / totalAmount < share](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L58)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L41-L61


 - [ ] ID-40
[FullMath.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L14-L106) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L67)
        - [inv *= 2 - denominator * inv](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L96)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L14-L106


 - [ ] ID-41
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134) performs a multiplication on the result of a division:
        - [denominator = denominator / twos](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L101)
        - [inverse = (3 * denominator) ^ 2](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L116)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134


 - [ ] ID-42
[YieldBoxRebase._toShares(uint256,uint256,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L18-L38) performs a multiplication on the result of a division:
        - [share = (amount * totalShares_) / totalAmount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L32)
        - [roundUp && (share * totalAmount) / totalShares_ < amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L35)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L18-L38


 - [ ] ID-43
[BoringMath.muldiv(uint256,uint256,uint256,bool)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/BoringMath.sol#L20-L30) performs a multiplication on the result of a division:
        - [result = (value * mul) / div](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/BoringMath.sol#L26)
        - [roundUp && (result * div) / mul < value](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/BoringMath.sol#L27)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/BoringMath.sol#L20-L30


## incorrect-equality
Impact: Medium
Confidence: High
 - [ ] ID-44
[GlpStrategy._vestByGlp()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L253-L278) uses a dangerous strict equality:
        - [vestable == 0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L265)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L253-L278


 - [ ] ID-45
[GlpStrategy._sellGmx(uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L316-L334) uses a dangerous strict equality:
        - [gmxAmount == 0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L318)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L316-L334


 - [ ] ID-46
[GlpStrategy._getVestableAmount(IGmxVester,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L181-L249) uses a dangerous strict equality:
        - [available == 0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L186)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L181-L249


 - [ ] ID-47
[ConvexRewardPoolMock.rewards(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexRewardPoolMock.sol#L32-L36) uses a dangerous strict equality:
        - [bal == 0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexRewardPoolMock.sol#L34)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexRewardPoolMock.sol#L32-L36


 - [ ] ID-48
[GlpStrategy._vestByEsGmx()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L280-L299) uses a dangerous strict equality:
        - [vestable == 0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L294)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L280-L299


## locked-ether
Impact: Medium
Confidence: High
 - [ ] ID-49
Contract locking ether found:
        Contract [RouterETHMock](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/RouterETHMock.sol#L6-L29) has payable functions:
         - [RouterETHMock.addLiquidityETH()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/RouterETHMock.sol#L23-L26)
         - [RouterETHMock.receive()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/RouterETHMock.sol#L28)
        But does not have a function to withdraw the ether

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/RouterETHMock.sol#L6-L29


 - [ ] ID-50
Contract locking ether found:
        Contract [StargateSwapperV3](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateSwapperV3.sol#L23-L110) has payable functions:
         - [StargateSwapperV3.receive()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateSwapperV3.sol#L109)
        But does not have a function to withdraw the ether

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateSwapperV3.sol#L23-L110


 - [ ] ID-51
Contract locking ether found:
        Contract [BalancerStrategy](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L28-L302) has payable functions:
         - [BalancerStrategy.receive()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L301)
        But does not have a function to withdraw the ether

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L28-L302


## reentrancy-no-eth
Impact: Medium
Confidence: Medium
 - [ ] ID-52
Reentrancy in [ConvexTricryptoStrategy.setMultiSwapper(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L170-L175):
        External calls:
        - [rewardToken.approve(address(swapper),0)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L172)
        State variables written after the call(s):
        - [swapper = ISwapper(_swapper)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L173)
        [ConvexTricryptoStrategy.swapper](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L42) can be used in cross function reentrancies:
        - [ConvexTricryptoStrategy.compound(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L189-L215)
        - [ConvexTricryptoStrategy.compoundAmount()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L130-L145)
        - [ConvexTricryptoStrategy.constructor(IYieldBox,address,address,address,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L84-L109)
        - [ConvexTricryptoStrategy.setMultiSwapper(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L170-L175)
        - [ConvexTricryptoStrategy.swapper](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L42)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L170-L175


 - [ ] ID-53
Reentrancy in [StargateStrategy.setMultiSwapper(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L149-L154):
        External calls:
        - [stgTokenReward.approve(address(swapper),0)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L151)
        State variables written after the call(s):
        - [swapper = ISwapper(_swapper)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L152)
        [StargateStrategy.swapper](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L42) can be used in cross function reentrancies:
        - [StargateStrategy.compound(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L159-L190)
        - [StargateStrategy.compoundAmount()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L116-L135)
        - [StargateStrategy.constructor(IYieldBox,address,address,address,uint256,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L67-L95)
        - [StargateStrategy.setMultiSwapper(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L149-L154)
        - [StargateStrategy.swapper](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L42)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L149-L154


 - [ ] ID-54
Reentrancy in [TricryptoNativeStrategy.setMultiSwapper(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L132-L137):
        External calls:
        - [rewardToken.approve(address(swapper),0)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L134)
        - [rewardToken.approve(_swapper,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L135)
        State variables written after the call(s):
        - [swapper = ISwapper(_swapper)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L136)
        [TricryptoNativeStrategy.swapper](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L41) can be used in cross function reentrancies:
        - [TricryptoNativeStrategy.compound(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L151-L179)
        - [TricryptoNativeStrategy.compoundAmount()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L103-L118)
        - [TricryptoNativeStrategy.constructor(IYieldBox,address,address,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L62-L82)
        - [TricryptoNativeStrategy.setMultiSwapper(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L132-L137)
        - [TricryptoNativeStrategy.swapper](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L41)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L132-L137


 - [ ] ID-55
Reentrancy in [TricryptoLPStrategy.setMultiSwapper(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L141-L146):
        External calls:
        - [rewardToken.approve(address(swapper),0)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L143)
        - [rewardToken.approve(_swapper,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L144)
        State variables written after the call(s):
        - [swapper = ISwapper(_swapper)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L145)
        [TricryptoLPStrategy.swapper](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L42) can be used in cross function reentrancies:
        - [TricryptoLPStrategy.compound(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L160-L196)
        - [TricryptoLPStrategy.compoundAmount()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L104-L127)
        - [TricryptoLPStrategy.constructor(IYieldBox,address,address,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L63-L83)
        - [TricryptoLPStrategy.setMultiSwapper(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L141-L146)
        - [TricryptoLPStrategy.swapper](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L42)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L141-L146


 - [ ] ID-56
Reentrancy in [TricryptoLPStrategy.setTricryptoLPGetter(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L150-L155):
        External calls:
        - [wrappedNative.approve(address(lpGetter),0)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L152)
        State variables written after the call(s):
        - [lpGetter = ITricryptoLPGetter(_lpGetter)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L153)
        [TricryptoLPStrategy.lpGetter](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L46) can be used in cross function reentrancies:
        - [TricryptoLPStrategy.compound(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L160-L196)
        - [TricryptoLPStrategy.compoundAmount()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L104-L127)
        - [TricryptoLPStrategy.constructor(IYieldBox,address,address,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L63-L83)
        - [TricryptoLPStrategy.lpGetter](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L46)
        - [TricryptoLPStrategy.setTricryptoLPGetter(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L150-L155)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L150-L155


 - [ ] ID-57
Reentrancy in [BalancerStrategy._withdraw(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L191-L216):
        External calls:
        - [_vaultWithdraw(toWithdraw)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L205)
                - [(bptIn) = helpers.queryExit(poolId,address(this),address(this),exitRequest)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L244-L249)
                - [vault.exitPool(poolId,address(this),address(this),exitRequest)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L257)
        - [wrappedNative.safeTransfer(to,amount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L212)
        - [updateCache()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L213)
                - [(amountsOut) = helpers.queryExit(poolId,address(this),address(this),exitRequest)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L290-L295)
        State variables written after the call(s):
        - [updateCache()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L213)
                - [_cachedCalculatedAmount = amountsOut[index]](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L297)
        [BalancerStrategy._cachedCalculatedAmount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L47) can be used in cross function reentrancies:
        - [BalancerStrategy._currentBalance()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L130-L134)
        - [BalancerStrategy.updateCache()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L271-L299)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L191-L216


 - [ ] ID-58
Reentrancy in [ConvexTricryptoStrategy.setTricryptoLPGetter(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L179-L184):
        External calls:
        - [wrappedNative.approve(address(lpGetter),0)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L181)
        State variables written after the call(s):
        - [lpGetter = ITricryptoLPGetter(_lpGetter)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L182)
        [ConvexTricryptoStrategy.lpGetter](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L44) can be used in cross function reentrancies:
        - [ConvexTricryptoStrategy._addLiquidityAndStake(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L310-L317)
        - [ConvexTricryptoStrategy._currentBalance()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L291-L297)
        - [ConvexTricryptoStrategy._withdraw(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L320-L352)
        - [ConvexTricryptoStrategy.constructor(IYieldBox,address,address,address,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L84-L109)
        - [ConvexTricryptoStrategy.emergencyWithdraw()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L148-L156)
        - [ConvexTricryptoStrategy.lpGetter](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L44)
        - [ConvexTricryptoStrategy.setTricryptoLPGetter(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L179-L184)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L179-L184


 - [ ] ID-59
Reentrancy in [TricryptoNativeStrategy.setTricryptoLPGetter(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L141-L146):
        External calls:
        - [wrappedNative.approve(address(lpGetter),0)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L143)
        State variables written after the call(s):
        - [lpGetter = ITricryptoLPGetter(_lpGetter)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L144)
        [TricryptoNativeStrategy.lpGetter](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L45) can be used in cross function reentrancies:
        - [TricryptoNativeStrategy._addLiquidityAndStake(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L247-L252)
        - [TricryptoNativeStrategy._currentBalance()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L196-L202)
        - [TricryptoNativeStrategy._withdraw(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L216-L245)
        - [TricryptoNativeStrategy.constructor(IYieldBox,address,address,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L62-L82)
        - [TricryptoNativeStrategy.emergencyWithdraw()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L182-L190)
        - [TricryptoNativeStrategy.lpGetter](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L45)
        - [TricryptoNativeStrategy.setTricryptoLPGetter(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L141-L146)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L141-L146


 - [ ] ID-60
Reentrancy in [GlpStrategy.withdrawFees()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L117-L127):
        External calls:
        - [weth.safeTransfer(feeRecipient,feeAmount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L124)
        State variables written after the call(s):
        - [feesPending -= feeAmount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L125)
        [GlpStrategy.feesPending](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L51) can be used in cross function reentrancies:
        - [GlpStrategy._buyGlp()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L166-L178)
        - [GlpStrategy.feesPending](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L51)
        - [GlpStrategy.withdrawFees()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L117-L127)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L117-L127


## unchecked-lowlevel
Impact: Medium
Confidence: Medium
 - [ ] ID-61
[BoringAddress.sendNative(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L15-L19) ignores return value by [(success) = to.call{value: amount}()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L17)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L15-L19


 - [ ] ID-62
[CurveEthStEthPoolMock.safeTransferETH(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/CurveEthStEthPoolMock.sol#L35-L38) ignores return value by [(success) = to.call{value: value}(new bytes(0))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/CurveEthStEthPoolMock.sol#L36)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/CurveEthStEthPoolMock.sol#L35-L38


 - [ ] ID-63
[ConvexTricryptoStrategy._safeApprove(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L354-L380) ignores return value by [(successEmtptyApproval) = token.call(abi.encodeWithSelector(bytes4(keccak256(bytes)(approve(address,uint256))),to,0))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L356-L362)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L354-L380


 - [ ] ID-64
[StargateRouterMock.safeTransferETH(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/StargateRouterMock.sol#L26-L29) ignores return value by [(success) = to.call{value: value}(new bytes(0))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/StargateRouterMock.sol#L27)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/StargateRouterMock.sol#L26-L29


 - [ ] ID-65
[TransferHelper.safeTransferETH(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/libraries/TransferHelper.sol#L56-L59) ignores return value by [(success) = to.call{value: value}(new bytes(0))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/libraries/TransferHelper.sol#L57)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/libraries/TransferHelper.sol#L56-L59


 - [ ] ID-66
[Address.sendValue(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L64-L69) ignores return value by [(success) = recipient.call{value: amount}()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L67)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L64-L69


## uninitialized-local
Impact: Medium
Confidence: Medium
 - [ ] ID-67
[BalancerStrategy.updateCache().index](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L275) is a local variable never initialized

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L275


 - [ ] ID-68
[BalancerStrategy._vaultWithdraw(uint256).exitRequest](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L234) is a local variable never initialized

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L234


 - [ ] ID-69
[ConvexTricryptoStrategy._executeClaim(bytes).extrasTempData](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L233) is a local variable never initialized

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L233


 - [ ] ID-70
[BalancerStrategy.updateCache().exitRequest](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L284) is a local variable never initialized

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L284


 - [ ] ID-71
[ConvexTricryptoStrategy._executeClaim(bytes).tempData](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L220) is a local variable never initialized

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L220


 - [ ] ID-72
[YieldBoxURIBuilder.uri(Asset,NativeToken,uint256,address).details](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxURIBuilder.sol#L85) is a local variable never initialized

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxURIBuilder.sol#L85


 - [ ] ID-73
[BalancerStrategy._vaultDeposit(uint256).joinPoolRequest](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L165) is a local variable never initialized

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L165


 - [ ] ID-74
[ConvexBoosterMock.poolInfo(uint256).info](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexBoosterMock.sol#L27) is a local variable never initialized

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexBoosterMock.sol#L27


## unused-return
Impact: Medium
Confidence: Medium
 - [ ] ID-75
[StargateStrategy.setMultiSwapper(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L149-L154) ignores return value by [stgTokenReward.approve(_swapper,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L153)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L149-L154


 - [ ] ID-76
[TricryptoLPStrategy.constructor(IYieldBox,address,address,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L63-L83) ignores return value by [lpToken.approve(_lpGauge,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L79)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L63-L83


 - [ ] ID-77
[ConvexTricryptoStrategy.constructor(IYieldBox,address,address,address,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L84-L109) ignores return value by [wrappedNative.approve(_lpGetter,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L105)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L84-L109


 - [ ] ID-78
[TricryptoNativeStrategy.constructor(IYieldBox,address,address,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L62-L82) ignores return value by [rewardToken.approve(_multiSwapper,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L80)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L62-L82


 - [ ] ID-79
[StargateStrategy._currentBalance()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L214-L219) ignores return value by [(amount,None) = lpStaking.userInfo(lpStakingPid,address(this))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L216)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L214-L219


 - [ ] ID-80
[BalancerStrategy.constructor(IYieldBox,address,address,bytes32,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L58-L79) ignores return value by [IERC20(address(pool)).approve(_vault,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L78)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L58-L79


 - [ ] ID-81
[StargateStrategy.compound(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L159-L190) ignores return value by [swapper.swap(swapData,minAmount,address(this),)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L184)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L159-L190


 - [ ] ID-82
[ConvexTricryptoStrategy.setMultiSwapper(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L170-L175) ignores return value by [rewardToken.approve(_swapper,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L174)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L170-L175


 - [ ] ID-83
[TricryptoNativeStrategy.setTricryptoLPGetter(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L141-L146) ignores return value by [wrappedNative.approve(address(lpGetter),0)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L143)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L141-L146


 - [ ] ID-84
[LidoEthStrategy._deposited(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/LidoEthStrategy.sol#L128-L138) ignores return value by [stEth.submit{value: queued}(address(0))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/LidoEthStrategy.sol#L133)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/LidoEthStrategy.sol#L128-L138


 - [ ] ID-85
[ConvexTricryptoStrategy.constructor(IYieldBox,address,address,address,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L84-L109) ignores return value by [rewardToken.approve(_multiSwapper,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L108)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L84-L109


 - [ ] ID-86
[OracleLibrary.getBlockStartingTickAndLiquidity(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L120-L171) ignores return value by [(observationTimestamp,tickCumulative,secondsPerLiquidityCumulativeX128) = IUniswapV3Pool(pool).observations(observationIndex)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L139-L144)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L120-L171


 - [ ] ID-87
[BalancerStrategy.updateCache()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L271-L299) ignores return value by [(poolTokens) = vault.getPoolTokens(poolId)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L274)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L271-L299


 - [ ] ID-88
[TricryptoNativeStrategy.constructor(IYieldBox,address,address,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L62-L82) ignores return value by [IERC20(lpGetter.lpToken()).approve(_lpGauge,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L78)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L62-L82


 - [ ] ID-89
[BalancerStrategy.updateCache()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L271-L299) ignores return value by [(amountsOut) = helpers.queryExit(poolId,address(this),address(this),exitRequest)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L290-L295)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L271-L299


 - [ ] ID-90
[BalancerStrategy._vaultWithdraw(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L218-L269) ignores return value by [(poolTokens) = vault.getPoolTokens(poolId)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L222)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L218-L269


 - [ ] ID-91
[TricryptoNativeStrategy.constructor(IYieldBox,address,address,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L62-L82) ignores return value by [wrappedNative.approve(_lpGetter,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L81)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L62-L82


 - [ ] ID-92
[ConvexTricryptoStrategy.setTricryptoLPGetter(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L179-L184) ignores return value by [wrappedNative.approve(address(lpGetter),0)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L181)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L179-L184


 - [ ] ID-93
[OracleLibrary.getOldestObservationSecondsAgo(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L90-L115) ignores return value by [(observationTimestamp,initialized) = IUniswapV3Pool(pool).observations((observationIndex + 1) % observationCardinality)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L104-L106)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L90-L115


 - [ ] ID-94
[TricryptoNativeStrategy.compound(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L151-L179) ignores return value by [swapper.swap(swapData,minAmount,address(this),)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L171)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L151-L179


 - [ ] ID-95
[TricryptoLPStrategy.constructor(IYieldBox,address,address,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L63-L83) ignores return value by [lpToken.approve(_lpGetter,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L80)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L63-L83


 - [ ] ID-96
[ConvexTricryptoStrategy.emergencyWithdraw()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L148-L156) ignores return value by [rewardPool.withdrawAndUnwrap(lpBalance,false)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L152)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L148-L156


 - [ ] ID-97
[BalancerStrategy._vaultDeposit(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L149-L188) ignores return value by [(bptOut) = helpers.queryJoin(poolId,address(this),address(this),joinPoolRequest)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L171-L176)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L149-L188


 - [ ] ID-98
[CompoundStrategy.emergencyWithdraw()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/CompoundStrategy.sol#L100-L108) ignores return value by [cToken.redeem(toWithdraw)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/CompoundStrategy.sol#L104)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/CompoundStrategy.sol#L100-L108


 - [ ] ID-99
[TricryptoLPStrategy.setMultiSwapper(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L141-L146) ignores return value by [rewardToken.approve(address(swapper),0)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L143)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L141-L146


 - [ ] ID-100
[StargateStrategy.constructor(IYieldBox,address,address,address,uint256,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L67-L95) ignores return value by [stgTokenReward.approve(_swapper,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L94)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L67-L95


 - [ ] ID-101
[AaveStrategy.constructor(IYieldBox,address,address,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L58-L77) ignores return value by [wrappedNative.approve(_lendingPool,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L75)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L58-L77


 - [ ] ID-102
[TricryptoNativeStrategy.setMultiSwapper(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L132-L137) ignores return value by [rewardToken.approve(_swapper,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L135)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L132-L137


 - [ ] ID-103
[StargateStrategy.constructor(IYieldBox,address,address,address,uint256,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L67-L95) ignores return value by [stgNative.approve(_lpStaking,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L89)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L67-L95


 - [ ] ID-104
[ConvexTricryptoStrategy.compound(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L189-L215) ignores return value by [swapper.swap(swapData,minAmount,address(this),)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L208)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L189-L215


 - [ ] ID-105
[BalancerStrategy._vaultDeposit(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L149-L188) ignores return value by [(poolTokens) = vault.getPoolTokens(poolId)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L152)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L149-L188


 - [ ] ID-106
[GlpStrategy._buyGlp()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L166-L178) ignores return value by [weth.approve(address(glpManager),wethAmount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L175)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L166-L178


 - [ ] ID-107
[CompoundStrategy._withdraw(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/CompoundStrategy.sol#L136-L162) ignores return value by [cToken.redeem(toWithdraw)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/CompoundStrategy.sol#L149)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/CompoundStrategy.sol#L136-L162


 - [ ] ID-108
[TricryptoLPStrategy.setMultiSwapper(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L141-L146) ignores return value by [rewardToken.approve(_swapper,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L144)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L141-L146


 - [ ] ID-109
[BalancerStrategy.constructor(IYieldBox,address,address,bytes32,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L58-L79) ignores return value by [(_stablePool) = vault.getPool(_poolId)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L72)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L58-L79


 - [ ] ID-110
[AaveStrategy.emergencyWithdraw()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L209-L219) ignores return value by [(toWithdraw) = lendingPool.getUserAccountData(address(this))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L211-L213)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L209-L219


 - [ ] ID-111
[StargateStrategy.setMultiSwapper(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L149-L154) ignores return value by [stgTokenReward.approve(address(swapper),0)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L151)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L149-L154


 - [ ] ID-112
[ConvexTricryptoStrategy.constructor(IYieldBox,address,address,address,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L84-L109) ignores return value by [lpToken.approve(_booster,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L107)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L84-L109


 - [ ] ID-113
[LidoEthStrategy.constructor(IYieldBox,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/LidoEthStrategy.sol#L52-L63) ignores return value by [IERC20(_stEth).approve(_curvePool,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/LidoEthStrategy.sol#L62)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/LidoEthStrategy.sol#L52-L63


 - [ ] ID-114
[ConvexTricryptoStrategy.setMultiSwapper(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L170-L175) ignores return value by [rewardToken.approve(address(swapper),0)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L172)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L170-L175


 - [ ] ID-115
[YearnStrategy._withdraw(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/yearn/YearnStrategy.sol#L132-L150) ignores return value by [vault.withdraw(toWithdraw,address(this),0)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/yearn/YearnStrategy.sol#L145)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/yearn/YearnStrategy.sol#L132-L150


 - [ ] ID-116
[TricryptoLPStrategy.setTricryptoLPGetter(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L150-L155) ignores return value by [wrappedNative.approve(address(lpGetter),0)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L152)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L150-L155


 - [ ] ID-117
[TricryptoNativeStrategy._withdraw(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L216-L245) ignores return value by [lpGetter.removeLiquidityWeth(lpBalance,minAmount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L233)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L216-L245


 - [ ] ID-118
[StargateSwapperV3.queryAmountOut(uint256,address,address,address,bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateSwapperV3.sol#L54-L69) ignores return value by [(tick) = OracleLibrary.consult(pool,60)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateSwapperV3.sol#L61)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateSwapperV3.sol#L54-L69


 - [ ] ID-119
[TricryptoLPStrategy.constructor(IYieldBox,address,address,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L63-L83) ignores return value by [wrappedNative.approve(_lpGetter,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L82)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L63-L83


 - [ ] ID-120
[ConvexTricryptoStrategy._withdraw(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L320-L352) ignores return value by [rewardPool.withdrawAndUnwrap(lpBalance,false)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L334)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L320-L352


 - [ ] ID-121
[ConvexTricryptoStrategy._addLiquidityAndStake(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L310-L317) ignores return value by [booster.deposit(pid,lpAmount,true)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L315)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L310-L317


 - [ ] ID-122
[GlpStrategy._buyGlp()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L166-L178) ignores return value by [glpRewardRouter.mintAndStakeGlp(address(weth),wethAmount,0,0)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L176)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L166-L178


 - [ ] ID-123
[StargateStrategy.emergencyWithdraw()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L193-L208) ignores return value by [router.instantRedeemLocal(uint16(lpRouterPid),toWithdraw,address(this))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L201-L205)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L193-L208


 - [ ] ID-124
[StargateStrategy._withdraw(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L241-L269) ignores return value by [router.instantRedeemLocal(uint16(lpRouterPid),toWithdraw,address(this))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L253-L257)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L241-L269


 - [ ] ID-125
[CompoundStrategy.constructor(IYieldBox,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/CompoundStrategy.sol#L50-L59) ignores return value by [wrappedNative.approve(_cToken,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/CompoundStrategy.sol#L58)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/CompoundStrategy.sol#L50-L59


 - [ ] ID-126
[BalancerStrategy._vaultWithdraw(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L218-L269) ignores return value by [(bptIn) = helpers.queryExit(poolId,address(this),address(this),exitRequest)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L244-L249)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L218-L269


 - [ ] ID-127
[OracleLibrary.getOldestObservationSecondsAgo(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L90-L115) ignores return value by [(observationIndex,observationCardinality) = IUniswapV3Pool(pool).slot0()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L93-L101)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L90-L115


 - [ ] ID-128
[TricryptoNativeStrategy.setMultiSwapper(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L132-L137) ignores return value by [rewardToken.approve(address(swapper),0)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L134)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L132-L137


 - [ ] ID-129
[AaveStrategy.compound(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L138-L206) ignores return value by [swapper.swap(swapData,minAmount,address(this),)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L194)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L138-L206


 - [ ] ID-130
[BalancerStrategy.constructor(IYieldBox,address,address,bytes32,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L58-L79) ignores return value by [wrappedNative.approve(_vault,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L77)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L58-L79


 - [ ] ID-131
[TricryptoNativeStrategy.setTricryptoLPGetter(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L141-L146) ignores return value by [wrappedNative.approve(_lpGetter,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L145)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L141-L146


 - [ ] ID-132
[AaveStrategy.constructor(IYieldBox,address,address,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L58-L77) ignores return value by [rewardToken.approve(_multiSwapper,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L76)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L58-L77


 - [ ] ID-133
[OracleLibrary.getBlockStartingTickAndLiquidity(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L120-L171) ignores return value by [(tick,observationIndex,observationCardinality) = IUniswapV3Pool(pool).slot0()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L123-L131)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L120-L171


 - [ ] ID-134
[YearnStrategy.constructor(IYieldBox,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/yearn/YearnStrategy.sol#L51-L60) ignores return value by [wrappedNative.approve(address(vault),type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/yearn/YearnStrategy.sol#L59)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/yearn/YearnStrategy.sol#L51-L60


 - [ ] ID-135
[YearnStrategy._deposited(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/yearn/YearnStrategy.sol#L121-L129) ignores return value by [vault.deposit(queued,address(this))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/yearn/YearnStrategy.sol#L124)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/yearn/YearnStrategy.sol#L121-L129


 - [ ] ID-136
[StargateStrategy.constructor(IYieldBox,address,address,address,uint256,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L67-L95) ignores return value by [stgNative.approve(address(router),type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L90)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L67-L95


 - [ ] ID-137
[OracleLibrary.getOldestObservationSecondsAgo(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L90-L115) ignores return value by [(observationTimestamp,None,None,None) = IUniswapV3Pool(pool).observations(0)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L111)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L90-L115


 - [ ] ID-138
[TricryptoNativeStrategy.constructor(IYieldBox,address,address,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L62-L82) ignores return value by [IERC20(lpGetter.lpToken()).approve(_lpGetter,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L79)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L62-L82


 - [ ] ID-139
[TricryptoLPGetter._addLiquidity(address,uint256,uint256[3],uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L214-L232) ignores return value by [IERC20(_token).approve(address(liquidityPool),_amount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L222)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L214-L232


 - [ ] ID-140
[TricryptoLPStrategy.compound(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L160-L196) ignores return value by [swapper.swap(swapData,minAmount,address(this),)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L180)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L160-L196


 - [ ] ID-141
[AaveStrategy.compound(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L138-L206) ignores return value by [incentivesController.claimRewards(tokens,type()(uint256).max,address(this))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L148-L152)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L138-L206


 - [ ] ID-142
[StargateStrategy.emergencyWithdraw()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L193-L208) ignores return value by [(toWithdraw) = lpStaking.userInfo(lpStakingPid,address(this))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L196-L199)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L193-L208


 - [ ] ID-143
[ConvexTricryptoStrategy.constructor(IYieldBox,address,address,address,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L84-L109) ignores return value by [lpToken.approve(_lpGetter,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L106)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L84-L109


 - [ ] ID-144
[AaveStrategy._currentBalance()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L225-L230) ignores return value by [(amount,None,None,None,None,None) = lendingPool.getUserAccountData(address(this))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L226)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L225-L230


 - [ ] ID-145
[TricryptoLPStrategy.constructor(IYieldBox,address,address,address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L63-L83) ignores return value by [rewardToken.approve(_multiSwapper,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L81)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L63-L83


 - [ ] ID-146
[ConvexBoosterMock.constructor(address,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexBoosterMock.sol#L16-L22) ignores return value by [lpToken.approve(_crvRewards,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexBoosterMock.sol#L21)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexBoosterMock.sol#L16-L22


 - [ ] ID-147
[ConvexTricryptoStrategy.setTricryptoLPGetter(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L179-L184) ignores return value by [wrappedNative.approve(_lpGetter,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L183)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L179-L184


 - [ ] ID-148
[TricryptoLPGetter._removeLiquidity(address,uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L234-L256) ignores return value by [lpToken.approve(address(liquidityPool),_amount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L243)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L234-L256


 - [ ] ID-149
[TricryptoLPStrategy.setTricryptoLPGetter(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L150-L155) ignores return value by [wrappedNative.approve(_lpGetter,type()(uint256).max)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L154)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L150-L155


 - [ ] ID-150
[ConvexTricryptoStrategy._withdraw(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L320-L352) ignores return value by [lpGetter.removeLiquidityWeth(lpBalance,minAmount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L337)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L320-L352


## shadowing-local
Impact: Low
Confidence: High
 - [ ] ID-151
[ERC20Permit.constructor(string).name](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol#L44) shadows:
        - [ERC20.name()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L62-L64) (function)
        - [IERC20Metadata.name()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L17) (function)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol#L44


 - [ ] ID-152
[IYieldBox.owner(uint256).owner](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L29) shadows:
        - [IYieldBox.owner(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L29) (function)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L29


 - [ ] ID-153
[IYieldBox.wrappedNative().wrappedNative](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L8) shadows:
        - [IYieldBox.wrappedNative()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L8) (function)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L8


 - [ ] ID-154
[ERC20Mock.constructor(string,string,uint256,uint8,address)._symbol](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L20) shadows:
        - [ERC20._symbol](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L46) (state variable)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L20


 - [ ] ID-155
[ERC20Mock.constructor(string,string,uint256,uint8,address)._owner](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L23) shadows:
        - [Ownable._owner](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/access/Ownable.sol#L21) (state variable)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L23


 - [ ] ID-156
[ERC20Mock.constructor(string,string,uint256,uint8,address)._name](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L19) shadows:
        - [EIP712._name](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L50) (state variable)
        - [ERC20._name](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L45) (state variable)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L19


 - [ ] ID-157
[NativeTokenFactory.createToken(string,string,uint8,string).uri](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/NativeTokenFactory.sol#L90) shadows:
        - [ERC1155.uri(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC1155.sol#L123-L125) (function)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/NativeTokenFactory.sol#L90


 - [ ] ID-158
[IYieldBox.totalSupply(uint256).totalSupply](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L31) shadows:
        - [IYieldBox.totalSupply(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L31) (function)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L31


## missing-zero-check
Impact: Low
Confidence: Medium
 - [ ] ID-159
[GlpStrategy.setFeeRecipient(address).recipient](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L113) lacks a zero-check on :
                - [feeRecipient = recipient](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L114)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L113


 - [ ] ID-160
[CTokenMock.constructor(address)._underlying](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/mocks/CTokenMock.sol#L13) lacks a zero-check on :
                - [underlying = _underlying](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/mocks/CTokenMock.sol#L15)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/mocks/CTokenMock.sol#L13


 - [ ] ID-161
[BoringOwnable.transferOwnership(address,bool,bool).newOwner](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L27) lacks a zero-check on :
                - [pendingOwner = newOwner](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L41)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L27


 - [ ] ID-162
[BalancerVaultMock.constructor(address,address)._stablePool](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerVaultMock.sol#L15) lacks a zero-check on :
                - [stablePool = _stablePool](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerVaultMock.sol#L16)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerVaultMock.sol#L15


 - [ ] ID-163
[CurveEthStEthPoolMock.constructor(address)._steth](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/CurveEthStEthPoolMock.sol#L12) lacks a zero-check on :
                - [steth = _steth](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/CurveEthStEthPoolMock.sol#L13)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/CurveEthStEthPoolMock.sol#L12


 - [ ] ID-164
[TricryptoLPGetter.constructor(address,address,address,address)._usdt](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L58) lacks a zero-check on :
                - [USDT = _usdt](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L62)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L58


 - [ ] ID-165
[TricryptoLiquidityPoolMock.constructor(address)._weth](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L16) lacks a zero-check on :
                - [weth = _weth](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L17)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L16


 - [ ] ID-166
[ConvexZapMock.constructor(address,address)._reward2](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexZapMock.sol#L14) lacks a zero-check on :
                - [reward2 = _reward2](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexZapMock.sol#L16)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexZapMock.sol#L14


 - [ ] ID-167
[TricryptoLPGaugeMock.constructor(address,address)._lpToken](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLPGaugeMock.sol#L16) lacks a zero-check on :
                - [lpToken = _lpToken](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLPGaugeMock.sol#L17)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLPGaugeMock.sol#L16


 - [ ] ID-168
[ConvexRewardPoolMock.constructor(address,address)._lpToken](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexRewardPoolMock.sol#L13) lacks a zero-check on :
                - [lpToken = _lpToken](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexRewardPoolMock.sol#L14)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexRewardPoolMock.sol#L13


 - [ ] ID-169
[RouterETHMock.constructor(address,address)._stgRouter](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/RouterETHMock.sol#L10) lacks a zero-check on :
                - [stgRouter = _stgRouter](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/RouterETHMock.sol#L11)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/RouterETHMock.sol#L10


 - [ ] ID-170
[TricryptoLPGetter.constructor(address,address,address,address)._wbtc](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L59) lacks a zero-check on :
                - [WBTC = _wbtc](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L63)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L59


 - [ ] ID-171
[TricryptoLPGetter.constructor(address,address,address,address)._weth](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L60) lacks a zero-check on :
                - [WETH = _weth](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L64)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L60


 - [ ] ID-172
[RouterETHMock.constructor(address,address)._lpToken](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/RouterETHMock.sol#L10) lacks a zero-check on :
                - [lpToken = _lpToken](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/RouterETHMock.sol#L12)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/RouterETHMock.sol#L10


 - [ ] ID-173
[ConvexRewardPoolMock.constructor(address,address)._rewardToken](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexRewardPoolMock.sol#L13) lacks a zero-check on :
                - [rewardToken = _rewardToken](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexRewardPoolMock.sol#L15)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexRewardPoolMock.sol#L13


 - [ ] ID-174
[TricryptoLPGaugeMock.constructor(address,address)._rewardToken](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLPGaugeMock.sol#L16) lacks a zero-check on :
                - [rewardToken = _rewardToken](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLPGaugeMock.sol#L18)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLPGaugeMock.sol#L16


 - [ ] ID-175
[BalancerVaultMock.constructor(address,address)._weth](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerVaultMock.sol#L15) lacks a zero-check on :
                - [weth = _weth](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerVaultMock.sol#L17)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerVaultMock.sol#L15


 - [ ] ID-176
[ConvexBoosterMock.constructor(address,address,address)._crvRewards](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexBoosterMock.sol#L16) lacks a zero-check on :
                - [crvRewards = _crvRewards](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexBoosterMock.sol#L19)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexBoosterMock.sol#L16


 - [ ] ID-177
[StargateStrategy.constructor(IYieldBox,address,address,address,uint256,address,address,address)._stgEthPool](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L75) lacks a zero-check on :
                - [stgEthPool = _stgEthPool](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L79)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L75


 - [ ] ID-178
[ConvexZapMock.constructor(address,address)._reward1](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexZapMock.sol#L14) lacks a zero-check on :
                - [reward1 = _reward1](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexZapMock.sol#L15)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexZapMock.sol#L14


## calls-loop
Impact: Low
Confidence: Medium
 - [ ] ID-179
[ConvexTricryptoStrategy.compound(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L189-L215) has external calls inside a loop: [calcAmount = swapper.getOutputAmount(swapData,)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L206)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L189-L215


 - [ ] ID-180
[ConvexTricryptoStrategy._safeApprove(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L354-L380) has external calls inside a loop: [(successEmtptyApproval) = token.call(abi.encodeWithSelector(bytes4(keccak256(bytes)(approve(address,uint256))),to,0))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L356-L362)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L354-L380


 - [ ] ID-181
[ConvexTricryptoStrategy.compound(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L189-L215) has external calls inside a loop: [swapData = swapper.buildSwapData(tokens[i],address(wrappedNative),rewards[i],0,false,false)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L198-L205)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L189-L215


 - [ ] ID-182
[BaseBoringBatchable.batch(bytes[],bool)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L38-L45) has external calls inside a loop: [(success,result) = address(this).delegatecall(calls[i])](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L40)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L38-L45


 - [ ] ID-183
[ConvexTricryptoStrategy._safeApprove(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L354-L380) has external calls inside a loop: [(success,data) = token.call(abi.encodeWithSelector(bytes4(keccak256(bytes)(approve(address,uint256))),to,value))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L369-L375)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L354-L380


 - [ ] ID-184
[ConvexTricryptoStrategy.compound(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L189-L215) has external calls inside a loop: [swapper.swap(swapData,minAmount,address(this),)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L208)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L189-L215


## reentrancy-benign
Impact: Low
Confidence: Medium
 - [ ] ID-185
Reentrancy in [BalancerStrategy.updateCache()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L271-L299):
        External calls:
        - [(amountsOut) = helpers.queryExit(poolId,address(this),address(this),exitRequest)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L290-L295)
        State variables written after the call(s):
        - [_cachedCalculatedAmount = amountsOut[index]](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L297)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L271-L299


 - [ ] ID-186
Reentrancy in [BalancerStrategy._deposited(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L138-L147):
        External calls:
        - [_vaultDeposit(queued)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L141)
                - [(bptOut) = helpers.queryJoin(poolId,address(this),address(this),joinPoolRequest)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L171-L176)
                - [vault.joinPool(poolId,address(this),address(this),joinPoolRequest)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L181)
        - [updateCache()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L146)
                - [(amountsOut) = helpers.queryExit(poolId,address(this),address(this),exitRequest)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L290-L295)
        State variables written after the call(s):
        - [updateCache()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L146)
                - [_cachedCalculatedAmount = amountsOut[index]](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L297)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L138-L147


## reentrancy-events
Impact: Low
Confidence: Medium
 - [ ] ID-187
Reentrancy in [TricryptoNativeStrategy.compound(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L151-L179):
        External calls:
        - [claimable = lpGauge.claimable_tokens(address(this))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L152)
        - [minter.mint(address(lpGauge))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L155)
        - [swapper.swap(swapData,minAmount,address(this),)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L171)
        - [_addLiquidityAndStake(queued)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L175)
                - [lpAmount = lpGetter.addLiquidityWeth(amount,minAmount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L250)
                - [lpGauge.deposit(lpAmount,address(this),false)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L251)
        Event emitted after the call(s):
        - [AmountDeposited(queued)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L176)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L151-L179


 - [ ] ID-188
Reentrancy in [StargateStrategy.compound(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L159-L190):
        External calls:
        - [lpStaking.deposit(2,0)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L167)
        - [swapper.swap(swapData,minAmount,address(this),)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L184)
        - [_stake(queued)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L187)
                - [INative(address(wrappedNative)).withdraw(amount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L232)
                - [addLiquidityRouter.addLiquidityETH{value: amount}()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L234)
                - [lpStaking.deposit(lpStakingPid,toStake)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L236)
        External calls sending eth:
        - [_stake(queued)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L187)
                - [addLiquidityRouter.addLiquidityETH{value: amount}()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L234)
        Event emitted after the call(s):
        - [AmountDeposited(amount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L237)
                - [_stake(queued)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L187)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L159-L190


 - [ ] ID-189
Reentrancy in [YieldBox.depositNFTAsset(uint256,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L168-L188):
        External calls:
        - [IERC721(asset.contractAddress).safeTransferFrom(from,address(asset.strategy),asset.tokenId)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L181)
        - [asset.strategy.deposited(1)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L183)
        Event emitted after the call(s):
        - [Deposited(msg.sender,from,to,assetId,1,1,1,1,true)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L185)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L168-L188


 - [ ] ID-190
Reentrancy in [ConvexTricryptoStrategy.compound(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L189-L215):
        External calls:
        - [(rewards,tokens) = _executeClaim(data)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L191-L193)
                - [zap.claimRewards(tempData.rewardContracts,tempData.extraRewardContracts,tempData.tokenRewardContracts,tempData.tokenRewardTokens,extrasTempData.depositCrvMaxAmount,extrasTempData.minAmountOut,extrasTempData.depositCvxMaxAmount,extrasTempData.spendCvxAmount,extrasTempData.options)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L261-L271)
        - [_safeApprove(tokens[i],address(swapper),rewards[i])](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L197)
                - [(successEmtptyApproval) = token.call(abi.encodeWithSelector(bytes4(keccak256(bytes)(approve(address,uint256))),to,0))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L356-L362)
                - [(success,data) = token.call(abi.encodeWithSelector(bytes4(keccak256(bytes)(approve(address,uint256))),to,value))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L369-L375)
        - [swapper.swap(swapData,minAmount,address(this),)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L208)
        - [_addLiquidityAndStake(queued)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L213)
                - [lpAmount = lpGetter.addLiquidityWeth(amount,minAmount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L314)
                - [booster.deposit(pid,lpAmount,true)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L315)
        Event emitted after the call(s):
        - [AmountDeposited(queued)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L214)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L189-L215


 - [ ] ID-191
Reentrancy in [AaveStrategy.compound(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L138-L206):
        External calls:
        - [incentivesController.claimRewards(tokens,type()(uint256).max,address(this))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L148-L152)
        - [stakedRewardToken.claimRewards(address(this),claimable)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L159)
        - [stakedRewardToken.cooldown()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L172)
        - [stakedRewardToken.cooldown()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L175)
        - [swapper.swap(swapData,minAmount,address(this),)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L194)
        - [lendingPool.deposit(address(wrappedNative),queued,address(this),0)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L198-L203)
        Event emitted after the call(s):
        - [AmountDeposited(queued)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L204)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L138-L206


 - [ ] ID-192
Reentrancy in [StargateStrategy._stake(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L231-L238):
        External calls:
        - [INative(address(wrappedNative)).withdraw(amount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L232)
        - [addLiquidityRouter.addLiquidityETH{value: amount}()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L234)
        - [lpStaking.deposit(lpStakingPid,toStake)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L236)
        External calls sending eth:
        - [addLiquidityRouter.addLiquidityETH{value: amount}()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L234)
        Event emitted after the call(s):
        - [AmountDeposited(amount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L237)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L231-L238


 - [ ] ID-193
Reentrancy in [YieldBox.depositETHAsset(uint256,address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L196-L219):
        External calls:
        - [wrappedNative.deposit{value: amount}()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L211)
        - [wrappedNative.safeTransfer(address(asset.strategy),amount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L213)
        - [asset.strategy.deposited(amount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L214)
        External calls sending eth:
        - [wrappedNative.deposit{value: amount}()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L211)
        Event emitted after the call(s):
        - [Deposited(msg.sender,msg.sender,to,assetId,amount,share,amountOut,shareOut,false)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L216)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L196-L219


 - [ ] ID-194
Reentrancy in [YieldBox.depositAsset(uint256,address,address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L118-L160):
        External calls:
        - [IERC20(asset.contractAddress).safeTransferFrom(from,address(asset.strategy),amount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L144)
        - [IERC1155(asset.contractAddress).safeTransferFrom(from,address(asset.strategy),asset.tokenId,amount,)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L151)
        - [asset.strategy.deposited(amount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L155)
        Event emitted after the call(s):
        - [Deposited(msg.sender,from,to,assetId,amount,share,amountOut,shareOut,false)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L157)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L118-L160


 - [ ] ID-195
Reentrancy in [TricryptoLPStrategy.compound(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L160-L196):
        External calls:
        - [claimable = lpGauge.claimable_tokens(address(this))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L161)
        - [minter.mint(address(lpGauge))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L164)
        - [swapper.swap(swapData,minAmount,address(this),)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L180)
        - [lpAmount = lpGetter.addLiquidityWeth(wrappedNativeAmount,minAmount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L187-L190)
        - [lpGauge.deposit(lpAmount,address(this),false)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L191)
        Event emitted after the call(s):
        - [AmountDeposited(lpAmount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L193)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L160-L196


 - [ ] ID-196
Reentrancy in [YieldBox._withdrawNFT(Asset,uint256,address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L251-L265):
        External calls:
        - [asset.strategy.withdraw(to,1)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L260)
        Event emitted after the call(s):
        - [Withdraw(msg.sender,from,to,assetId,1,1,1,1)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L262)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L251-L265


 - [ ] ID-197
Reentrancy in [BoringFactory.deploy(address,bytes,bool)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67):
        External calls:
        - [IMasterContract(cloneAddress).init{value: msg.value}(data)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L64)
        Event emitted after the call(s):
        - [LogDeploy(masterContract,data,cloneAddress)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L66)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67


 - [ ] ID-198
Reentrancy in [YieldBox._withdrawFungible(Asset,uint256,address,address,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L274-L300):
        External calls:
        - [asset.strategy.withdraw(to,amount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L295)
        Event emitted after the call(s):
        - [Withdraw(msg.sender,from,to,assetId,amount,share,amountOut,shareOut)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L297)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L274-L300


## timestamp
Impact: Low
Confidence: Medium
 - [ ] ID-199
[OracleLibrary.getBlockStartingTickAndLiquidity(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L120-L171) uses timestamp for comparisons
        Dangerous comparisons:
        - [observationTimestamp != uint32(block.timestamp)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L145)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L120-L171


 - [ ] ID-200
[YieldBoxPermit.permitAll(address,address,uint256,uint8,bytes32,bytes32)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L72-L90) uses timestamp for comparisons
        Dangerous comparisons:
        - [require(bool,string)(block.timestamp <= deadline,YieldBoxPermit: expired deadline)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L80)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L72-L90


 - [ ] ID-201
[ERC20Permit.permit(address,address,uint256,uint256,uint8,bytes32,bytes32)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol#L49-L68) uses timestamp for comparisons
        Dangerous comparisons:
        - [require(bool,string)(block.timestamp <= deadline,ERC20Permit: expired deadline)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol#L58)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol#L49-L68


 - [ ] ID-202
[ERC20Mock.freeMint(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L55-L67) uses timestamp for comparisons
        Dangerous comparisons:
        - [require(bool,string)(mintedAt[msg.sender] + MINT_WINDOW <= block.timestamp,ERC20Mock: too early)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L58-L61)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L55-L67


 - [ ] ID-203
[YieldBoxPermit.permit(address,address,uint256,uint256,uint8,bytes32,bytes32)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L42-L61) uses timestamp for comparisons
        Dangerous comparisons:
        - [require(bool,string)(block.timestamp <= deadline,YieldBoxPermit: expired deadline)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L51)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L42-L61


 - [ ] ID-204
[AaveStrategy.compound(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L138-L206) uses timestamp for comparisons
        Dangerous comparisons:
        - [daysPassed = (currentCooldown + 1036800) < block.timestamp](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L170)
        - [daysPassed && balanceOfStkAave > 0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L171)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L138-L206


 - [ ] ID-205
[StkAaveMock.stakerRewardsToClaim(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/StkAaveMock.sol#L36-L39) uses timestamp for comparisons
        Dangerous comparisons:
        - [lastCooldown + 1036800 < block.timestamp](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/StkAaveMock.sol#L37)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/StkAaveMock.sol#L36-L39


## assembly
Impact: Informational
Confidence: High
 - [ ] ID-206
[Base64.encode(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L11-L69) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L23-L66)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L11-L69


 - [ ] ID-207
[StorageSlot.getBytesSlot(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L132-L137) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L134-L136)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L132-L137


 - [ ] ID-208
[StorageSlot.getStringSlot(string)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L112-L117) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L114-L116)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L112-L117


 - [ ] ID-209
[StorageSlot.getUint256Slot(bytes32)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L92-L97) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L94-L96)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L92-L97


 - [ ] ID-210
[ECDSA.tryRecover(bytes32,bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L55-L72) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L63-L67)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L55-L72


 - [ ] ID-211
[StorageSlot.getBooleanSlot(bytes32)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L72-L77) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L74-L76)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L72-L77


 - [ ] ID-212
[ECDSA.toEthSignedMessageHash(bytes32)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L165-L174) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L169-L173)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L165-L174


 - [ ] ID-213
[Math.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L62-L66)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L85-L92)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L99-L108)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134


 - [ ] ID-214
[FullMath.mulDiv(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L14-L106) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L26-L30)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L35-L37)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L52-L54)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L56-L59)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L66-L68)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L71-L73)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L77-L79)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L14-L106


 - [ ] ID-215
[StorageSlot.getStringSlot(bytes32)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L102-L107) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L104-L106)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L102-L107


 - [ ] ID-216
[BoringAddress.isContract(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L7-L13) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L9-L11)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L7-L13


 - [ ] ID-217
[Strings.toString(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L19-L39) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L25-L27)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L31-L33)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L19-L39


 - [ ] ID-218
[BoringFactory.deploy(address,bytes,bool)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L45-L51)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L53-L59)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67


 - [ ] ID-219
[ShortStrings.toString(ShortString)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/ShortStrings.sol#L63-L73) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/ShortStrings.sol#L68-L71)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/ShortStrings.sol#L63-L73


 - [ ] ID-220
[Address._revert(bytes,string)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L231-L243) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L236-L239)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L231-L243


 - [ ] ID-221
[StorageSlot.getAddressSlot(bytes32)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L62-L67) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L64-L66)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L62-L67


 - [ ] ID-222
[StorageSlot.getBytes32Slot(bytes32)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L82-L87) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L84-L86)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L82-L87


 - [ ] ID-223
[BaseBoringBatchable._getRevertMsg(bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L19-L29) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L24-L27)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L19-L29


 - [ ] ID-224
[StorageSlot.getBytesSlot(bytes32)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L122-L127) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L124-L126)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L122-L127


 - [ ] ID-225
[TickMath.getTickAtSqrtRatio(uint160)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L89-L245) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L102-L106)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L107-L111)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L112-L116)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L117-L121)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L122-L126)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L127-L131)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L132-L136)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L137-L140)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L147-L152)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L153-L158)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L159-L164)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L165-L170)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L171-L176)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L177-L182)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L183-L188)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L189-L194)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L195-L200)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L201-L206)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L207-L212)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L213-L218)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L219-L224)
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L225-L229)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L89-L245


 - [ ] ID-226
[ECDSA.toTypedDataHash(bytes32,bytes32)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L197-L206) uses assembly
        - [INLINE ASM](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L199-L205)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L197-L206


## boolean-equal
Impact: Informational
Confidence: High
 - [ ] ID-227
[ERC1155._requireTransferAllowed(address,bool)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC1155.sol#L78-L80) compares to a boolean constant:
        -[require(bool,string)(_from == msg.sender || _approved || isApprovedForAll[_from][msg.sender] == true,Transfer not allowed)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC1155.sol#L79)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC1155.sol#L78-L80


## pragma
Impact: Informational
Confidence: High
 - [ ] ID-228
Different versions of Solidity are used:
        - Version used: ['>=0.5.0', '>=0.6.0', '>=0.7.5', '^0.8.0', '^0.8.1', '^0.8.18', '^0.8.8', '^0.8.9']
        - [>=0.5.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/IUniswapV3Pool.sol#L2)
        - [>=0.5.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/callback/IUniswapV3SwapCallback.sol#L2)
        - [>=0.5.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolActions.sol#L2)
        - [>=0.5.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolDerivedState.sol#L2)
        - [>=0.5.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolEvents.sol#L2)
        - [>=0.5.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolImmutables.sol#L2)
        - [>=0.5.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolOwnerActions.sol#L2)
        - [>=0.5.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolState.sol#L2)
        - [>=0.6.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/libraries/TransferHelper.sol#L2)
        - [>=0.7.5](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/interfaces/ISwapRouter.sol#L2)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L25)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L4)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IStrategy.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L3)
        - [ABIEncoderV2](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L3)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L5)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC1155.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC1155TokenReceiver.sol#L3)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC165.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC20.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721TokenReceiver.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IMasterContract.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/access/Ownable.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/interfaces/IERC5267.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/security/ReentrancyGuard.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Permit.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Context.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Counters.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L5)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/SignedMath.sol#L4)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/IFeeCollector.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/IWETHToken.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/gmx/IGlpManager.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/gmx/IGmxRewardDistributor.sol#L3)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/gmx/IGmxRewardRouter.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/gmx/IGmxRewardTracker.sol#L3)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/gmx/IGmxVault.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/gmx/IGmxVester.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L2)
        - [^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L3)
        - [^0.8.1](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L4)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/interfaces/IIncentivesController.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/interfaces/ILendingPool.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/interfaces/IStkAave.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/IncentivesControllerMock.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/LendingPoolMock.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/StkAaveMock.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/interfaces/IBalancerHelpers.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/interfaces/IBalancerPool.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/interfaces/IBalancerVault.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerHelpersMock.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerPoolMock.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerVaultMock.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/CompoundStrategy.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/interfaces/ICToken.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/mocks/CTokenMock.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/interfaces/IConvexBooster.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/interfaces/IConvexRewardPool.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/interfaces/IConvexZap.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexBoosterMock.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexRewardPoolMock.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexZapMock.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ICurveMinter.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGauge.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGetter.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/CurveMinterMock.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLPGaugeMock.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/LidoEthStrategy.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/interfaces/ICurveEthStEthPool.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/interfaces/IStEth.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/CurveEthStEthPoolMock.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/StEthMock.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateSwapperV3.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/interfaces/ILPStaking.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/interfaces/IRouter.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/interfaces/IRouterETH.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/interfaces/IStargateSwapper.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/LPStakingMock.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/RouterETHMock.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/StargateRouterMock.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/StargateSwapperV3Mock.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/test.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/yearn/YearnStrategy.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/yearn/interfaces/IYearnVault.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/yearn/mocks/YearnVaultMock.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/interfaces/INative.sol#L2)
        - [^0.8.18](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/interfaces/ISwapper.sol#L2)
        - [^0.8.8](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/ShortStrings.sol#L4)
        - [^0.8.8](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L4)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/AssetRegister.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/BoringMath.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC1155.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC1155TokenReceiver.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC721TokenReceiver.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/NativeTokenFactory.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L24)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L3)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxURIBuilder.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/enums/YieldBoxTokenType.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IStrategy.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IWrappedNative.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L2)
        - [^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L2)
        - [v2](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/interfaces/ISwapRouter.sol#L3)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/IUniswapV3Pool.sol#L2


## cyclomatic-complexity
Impact: Informational
Confidence: High
 - [ ] ID-229
[TickMath.getSqrtRatioAtTick(int24)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L24-L82) has a high cyclomatic complexity (24).

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L24-L82


## dead-code
Impact: Informational
Confidence: Medium
 - [ ] ID-230
[OracleLibrary.getChainedPrice(address[],int24[])](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L214-L226) is never used and should be removed

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L214-L226


 - [ ] ID-231
[FullMath.mulDivRoundingUp(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L113-L123) is never used and should be removed

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/FullMath.sol#L113-L123


 - [ ] ID-232
[OracleLibrary.getWeightedArithmeticMeanTick(OracleLibrary.WeightedTickData[])](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L185-L206) is never used and should be removed

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L185-L206


 - [ ] ID-233
[TickMath.getTickAtSqrtRatio(uint160)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L89-L245) is never used and should be removed

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L89-L245


 - [ ] ID-234
[OracleLibrary.getOldestObservationSecondsAgo(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L90-L115) is never used and should be removed

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L90-L115


 - [ ] ID-235
[OracleLibrary.getBlockStartingTickAndLiquidity(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L120-L171) is never used and should be removed

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/OracleLibrary.sol#L120-L171


## solc-version
Impact: Informational
Confidence: High
 - [ ] ID-236
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/ECDSA.sol#L4


 - [ ] ID-237
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/AssetRegister.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/AssetRegister.sol#L2


 - [ ] ID-238
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/interfaces/IERC5267.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/interfaces/IERC5267.sol#L4


 - [ ] ID-239
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L4


 - [ ] ID-240
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L2


 - [ ] ID-241
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC20.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC20.sol#L2


 - [ ] ID-242
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/Math.sol#L4


 - [ ] ID-243
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol#L4


 - [ ] ID-244
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxRebase.sol#L3


 - [ ] ID-245
Pragma version[>=0.7.5](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/interfaces/ISwapRouter.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/interfaces/ISwapRouter.sol#L2


 - [ ] ID-246
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L24) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol#L24


 - [ ] ID-247
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Context.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Context.sol#L4


 - [ ] ID-248
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/gmx/IGmxRewardRouter.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/gmx/IGmxRewardRouter.sol#L2


 - [ ] ID-249
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC1155TokenReceiver.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC1155TokenReceiver.sol#L3


 - [ ] ID-250
Pragma version[>=0.5.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolEvents.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolEvents.sol#L2


 - [ ] ID-251
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/NativeTokenFactory.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/NativeTokenFactory.sol#L2


 - [ ] ID-252
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/security/ReentrancyGuard.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/security/ReentrancyGuard.sol#L4


 - [ ] ID-253
Pragma version[>=0.5.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolDerivedState.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolDerivedState.sol#L2


 - [ ] ID-254
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721TokenReceiver.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721TokenReceiver.sol#L2


 - [ ] ID-255
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC1155.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC1155.sol#L2


 - [ ] ID-256
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Strings.sol#L4


 - [ ] ID-257
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/Base64.sol#L2


 - [ ] ID-258
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L3


 - [ ] ID-259
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/BoringMath.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/BoringMath.sol#L2


 - [ ] ID-260
Pragma version[^0.8.8](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L4) is known to contain severe issues (https://solidity.readthedocs.io/en/latest/bugs.html)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/cryptography/EIP712.sol#L4


 - [ ] ID-261
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC165.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC165.sol#L2


 - [ ] ID-262
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol#L4


 - [ ] ID-263
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L2


 - [ ] ID-264
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol#L4


 - [ ] ID-265
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IStrategy.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IStrategy.sol#L2


 - [ ] ID-266
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/gmx/IGmxRewardDistributor.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/gmx/IGmxRewardDistributor.sol#L3


 - [ ] ID-267
Pragma version[^0.8.1](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L4


 - [ ] ID-268
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/gmx/IGmxVester.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/gmx/IGmxVester.sol#L2


 - [ ] ID-269
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Permit.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Permit.sol#L4


 - [ ] ID-270
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IERC721.sol#L2


 - [ ] ID-271
Pragma version[>=0.5.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolState.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolState.sol#L2


 - [ ] ID-272
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L2


 - [ ] ID-273
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Counters.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Counters.sol#L4


 - [ ] ID-274
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol#L4


 - [ ] ID-275
Pragma version[>=0.6.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/libraries/TransferHelper.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/libraries/TransferHelper.sol#L2


 - [ ] ID-276
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC721TokenReceiver.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC721TokenReceiver.sol#L2


 - [ ] ID-277
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L2


 - [ ] ID-278
Pragma version[>=0.5.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolOwnerActions.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolOwnerActions.sol#L2


 - [ ] ID-279
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L5) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/StorageSlot.sol#L5


 - [ ] ID-280
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IYieldBox.sol#L2


 - [ ] ID-281
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L4


 - [ ] ID-282
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxURIBuilder.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxURIBuilder.sol#L2


 - [ ] ID-283
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/IFeeCollector.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/IFeeCollector.sol#L2


 - [ ] ID-284
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/SignedMath.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/math/SignedMath.sol#L4


 - [ ] ID-285
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L2


 - [ ] ID-286
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L2


 - [ ] ID-287
Pragma version[>=0.5.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/callback/IUniswapV3SwapCallback.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/callback/IUniswapV3SwapCallback.sol#L2


 - [ ] ID-288
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IWrappedNative.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IWrappedNative.sol#L2


 - [ ] ID-289
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/IWETHToken.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/IWETHToken.sol#L2


 - [ ] ID-290
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/gmx/IGmxRewardTracker.sol#L3) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/gmx/IGmxRewardTracker.sol#L3


 - [ ] ID-291
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/gmx/IGmxVault.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/gmx/IGmxVault.sol#L2


 - [ ] ID-292
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IMasterContract.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/interfaces/IMasterContract.sol#L2


 - [ ] ID-293
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/access/Ownable.sol#L4) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/access/Ownable.sol#L4


 - [ ] ID-294
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L5) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L5


 - [ ] ID-295
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC1155TokenReceiver.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC1155TokenReceiver.sol#L2


 - [ ] ID-296
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/gmx/IGlpManager.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/interfaces/gmx/IGlpManager.sol#L2


 - [ ] ID-297
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC1155.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/ERC1155.sol#L2


 - [ ] ID-298
Pragma version[^0.8.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringOwnable.sol#L2


 - [ ] ID-299
Pragma version[^0.8.8](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/ShortStrings.sol#L4) is known to contain severe issues (https://solidity.readthedocs.io/en/latest/bugs.html)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/ShortStrings.sol#L4


 - [ ] ID-300
Pragma version[>=0.5.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolActions.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolActions.sol#L2


 - [ ] ID-301
Pragma version[>=0.5.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/IUniswapV3Pool.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/IUniswapV3Pool.sol#L2


 - [ ] ID-302
Pragma version[^0.8.9](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/enums/YieldBoxTokenType.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/enums/YieldBoxTokenType.sol#L2


 - [ ] ID-303
Pragma version[>=0.5.0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolImmutables.sol#L2) allows old versions

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolImmutables.sol#L2


## low-level-calls
Impact: Informational
Confidence: High
 - [ ] ID-304
Low level call in [BoringERC20.safeName(IERC20)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L45-L48):
        - [(success,data) = address(token).staticcall(abi.encodeWithSelector(SIG_NAME))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L46)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L45-L48


 - [ ] ID-305
Low level call in [Address.functionCallWithValue(address,bytes,uint256,string)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L128-L137):
        - [(success,returndata) = target.call{value: value}(data)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L135)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L128-L137


 - [ ] ID-306
Low level call in [SafeERC20._callOptionalReturnBool(IERC20,bytes)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol#L134-L142):
        - [(success,returndata) = address(token).call(data)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol#L139)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol#L134-L142


 - [ ] ID-307
Low level call in [TransferHelper.safeTransferETH(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/libraries/TransferHelper.sol#L56-L59):
        - [(success) = to.call{value: value}(new bytes(0))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/libraries/TransferHelper.sol#L57)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/libraries/TransferHelper.sol#L56-L59


 - [ ] ID-308
Low level call in [ConvexTricryptoStrategy._safeApprove(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L354-L380):
        - [(successEmtptyApproval) = token.call(abi.encodeWithSelector(bytes4(keccak256(bytes)(approve(address,uint256))),to,0))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L356-L362)
        - [(success,data) = token.call(abi.encodeWithSelector(bytes4(keccak256(bytes)(approve(address,uint256))),to,value))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L369-L375)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L354-L380


 - [ ] ID-309
Low level call in [Address.sendValue(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L64-L69):
        - [(success) = recipient.call{value: amount}()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L67)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L64-L69


 - [ ] ID-310
Low level call in [TransferHelper.safeApprove(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/libraries/TransferHelper.sol#L43-L50):
        - [(success,data) = token.call(abi.encodeWithSelector(IERC20.approve.selector,to,value))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/libraries/TransferHelper.sol#L48)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/libraries/TransferHelper.sol#L43-L50


 - [ ] ID-311
Low level call in [BaseBoringBatchable.batch(bytes[],bool)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L38-L45):
        - [(success,result) = address(this).delegatecall(calls[i])](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L40)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringBatchable.sol#L38-L45


 - [ ] ID-312
Low level call in [BoringERC20.safeTransferFrom(IERC20,address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L97-L105):
        - [(success,data) = address(token).call(abi.encodeWithSelector(SIG_TRANSFER_FROM,from,to,amount))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L103)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L97-L105


 - [ ] ID-313
Low level call in [BoringERC20.safeSymbol(IERC20)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L37-L40):
        - [(success,data) = address(token).staticcall(abi.encodeWithSelector(SIG_SYMBOL))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L38)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L37-L40


 - [ ] ID-314
Low level call in [CurveEthStEthPoolMock.safeTransferETH(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/CurveEthStEthPoolMock.sol#L35-L38):
        - [(success) = to.call{value: value}(new bytes(0))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/CurveEthStEthPoolMock.sol#L36)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/CurveEthStEthPoolMock.sol#L35-L38


 - [ ] ID-315
Low level call in [BoringERC20.safeTotalSupply(IERC20)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L71-L75):
        - [(success,data) = address(token).staticcall(abi.encodeWithSelector(SIG_TOTALSUPPLY))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L72)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L71-L75


 - [ ] ID-316
Low level call in [BoringERC20.safeBalanceOf(IERC20,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L62-L66):
        - [(success,data) = address(token).staticcall(abi.encodeWithSelector(SIG_BALANCE_OF,to))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L63)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L62-L66


 - [ ] ID-317
Low level call in [BoringAddress.sendNative(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L15-L19):
        - [(success) = to.call{value: amount}()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L17)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringAddress.sol#L15-L19


 - [ ] ID-318
Low level call in [StargateRouterMock.safeTransferETH(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/StargateRouterMock.sol#L26-L29):
        - [(success) = to.call{value: value}(new bytes(0))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/StargateRouterMock.sol#L27)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/StargateRouterMock.sol#L26-L29


 - [ ] ID-319
Low level call in [BoringERC20.safeDecimals(IERC20)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L53-L56):
        - [(success,data) = address(token).staticcall(abi.encodeWithSelector(SIG_DECIMALS))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L54)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L53-L56


 - [ ] ID-320
Low level call in [TransferHelper.safeTransferFrom(address,address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/libraries/TransferHelper.sol#L13-L22):
        - [(success,data) = token.call(abi.encodeWithSelector(IERC20.transferFrom.selector,from,to,value))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/libraries/TransferHelper.sol#L19-L20)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/libraries/TransferHelper.sol#L13-L22


 - [ ] ID-321
Low level call in [BoringERC20.safeTransfer(IERC20,address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L82-L89):
        - [(success,data) = address(token).call(abi.encodeWithSelector(SIG_TRANSFER,to,amount))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L87)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/libraries/BoringERC20.sol#L82-L89


 - [ ] ID-322
Low level call in [TricryptoLPStrategy.compoundAmount()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L104-L127):
        - [(success,response) = address(lpGauge).staticcall(abi.encodeWithSignature(claimable_tokens(address),address(this)))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L105-L107)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L104-L127


 - [ ] ID-323
Low level call in [Address.functionStaticCall(address,bytes,string)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L155-L162):
        - [(success,returndata) = target.staticcall(data)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L160)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L155-L162


 - [ ] ID-324
Low level call in [TransferHelper.safeTransfer(address,address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/libraries/TransferHelper.sol#L29-L36):
        - [(success,data) = token.call(abi.encodeWithSelector(IERC20.transfer.selector,to,value))](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/libraries/TransferHelper.sol#L34)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-periphery/contracts/libraries/TransferHelper.sol#L29-L36


 - [ ] ID-325
Low level call in [Address.functionDelegateCall(address,bytes,string)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L180-L187):
        - [(success,returndata) = target.delegatecall(data)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L185)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/Address.sol#L180-L187


## missing-inheritance
Impact: Informational
Confidence: High
 - [ ] ID-326
[IncentivesControllerMock](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/IncentivesControllerMock.sol#L9-L43) should inherit from [IIncentivesController](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/interfaces/IIncentivesController.sol#L4-L36)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/IncentivesControllerMock.sol#L9-L43


 - [ ] ID-327
[StargateSwapperV3](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateSwapperV3.sol#L23-L110) should inherit from [IStargateSwapper](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/interfaces/IStargateSwapper.sol#L4-L34)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateSwapperV3.sol#L23-L110


 - [ ] ID-328
[StEthMock](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/StEthMock.sol#L6-L22) should inherit from [IStEth](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/interfaces/IStEth.sol#L4-L15)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/StEthMock.sol#L6-L22


 - [ ] ID-329
[GlpStrategy](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L23-L335) should inherit from [IUniswapV3SwapCallback](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/callback/IUniswapV3SwapCallback.sol#L6-L21)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L23-L335


 - [ ] ID-330
[BalancerHelpersMock](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerHelpersMock.sol#L8-L28) should inherit from [IBalancerHelpers](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/interfaces/IBalancerHelpers.sol#L6-L20)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerHelpersMock.sol#L8-L28


 - [ ] ID-331
[CurveMinterMock](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/CurveMinterMock.sol#L7-L20) should inherit from [ICurveMinter](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ICurveMinter.sol#L4-L7)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/CurveMinterMock.sol#L7-L20


 - [ ] ID-332
[StargateSwapperV3Mock](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/StargateSwapperV3Mock.sol#L7-L37) should inherit from [IStargateSwapper](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/interfaces/IStargateSwapper.sol#L4-L34)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/StargateSwapperV3Mock.sol#L7-L37


 - [ ] ID-333
[CurveEthStEthPoolMock](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/CurveEthStEthPoolMock.sol#L7-L41) should inherit from [ICurveEthStEthPool](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/interfaces/ICurveEthStEthPool.sol#L4-L17)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/CurveEthStEthPoolMock.sol#L7-L41


 - [ ] ID-334
[BalancerPoolMock](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerPoolMock.sol#L10-L20) should inherit from [IBalancerPool](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/interfaces/IBalancerPool.sol#L4-L8)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerPoolMock.sol#L10-L20


## naming-convention
Impact: Informational
Confidence: High
 - [ ] ID-335
Function [IStkAave.REWARD_TOKEN()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/interfaces/IStkAave.sol#L5) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/interfaces/IStkAave.sol#L5


 - [ ] ID-336
Function [ITricryptoLPGauge.claimable_reward(address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGauge.sol#L27-L30) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGauge.sol#L27-L30


 - [ ] ID-337
Function [IIncentivesController.REWARD_TOKEN()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/interfaces/IIncentivesController.sol#L21) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/interfaces/IIncentivesController.sol#L21


 - [ ] ID-338
Parameter [TricryptoLiquidityPoolMock.remove_liquidity_one_coin(uint256,uint256,uint256)._token_amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L39) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L39


 - [ ] ID-339
Function [TricryptoLiquidityPoolMock.add_liquidity(uint256[3],uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L31-L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L31-L36


 - [ ] ID-340
Function [ITricryptoLPGetter.WBTC()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGetter.sol#L19) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGetter.sol#L19


 - [ ] ID-341
Parameter [TricryptoLPGetter.addLiquidityUsdt(uint256,uint256)._amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L177) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L177


 - [ ] ID-342
Parameter [ITricryptoLPGauge.withdraw(uint256,bool)._claim_rewards](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGauge.sol#L16) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGauge.sol#L16


 - [ ] ID-343
Parameter [TricryptoLPGetter.removeLiquidityWeth(uint256,uint256)._amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L143) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L143


 - [ ] ID-344
Parameter [ERC20Mock.extractTokens(uint256)._amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L51) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L51


 - [ ] ID-345
Function [TricryptoLiquidityPoolMock.remove_liquidity_one_coin(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L38-L45) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L38-L45


 - [ ] ID-346
Function [ITricryptoLPGetter.WETH()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGetter.sol#L23) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGetter.sol#L23


 - [ ] ID-347
Variable [Domain._DOMAIN_SEPARATOR](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L15) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L15


 - [ ] ID-348
Parameter [TricryptoLPGetter.removeLiquidityWeth(uint256,uint256)._minAmount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L144) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L144


 - [ ] ID-349
Contract [test](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/test.sol#L6) is not in CapWords

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/test.sol#L6


 - [ ] ID-350
Parameter [StargateRouterMock.instantRedeemLocal(uint16,uint256,address)._to](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/StargateRouterMock.sol#L19) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/StargateRouterMock.sol#L19


 - [ ] ID-351
Parameter [TricryptoLiquidityPoolMock.calc_withdraw_one_coin(uint256,uint256).token_amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L48) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L48


 - [ ] ID-352
Parameter [ConvexTricryptoStrategy.setMultiSwapper(address)._swapper](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L170) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L170


 - [ ] ID-353
Parameter [ConvexTricryptoStrategy.setTricryptoLPGetter(address)._lpGetter](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L179) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/ConvexTricryptoStrategy.sol#L179


 - [ ] ID-354
Parameter [ERC20Mock.freeMint(uint256)._val](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L55) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L55


 - [ ] ID-355
Parameter [TricryptoLPGetter.calcWethToLp(uint256)._amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L81) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L81


 - [ ] ID-356
Parameter [ITricryptoLiquidityPool.remove_liquidity_one_coin(uint256,uint256,uint256).min_amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L25) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L25


 - [ ] ID-357
Function [ITricryptoLiquidityPool.get_virtual_price()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L46) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L46


 - [ ] ID-358
Parameter [TricryptoLPGetter.addLiquidityUsdt(uint256,uint256)._minAmount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L178) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L178


 - [ ] ID-359
Variable [TricryptoLPGetter.WETH](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L36


 - [ ] ID-360
Parameter [ConvexRewardPoolMock.withdrawAndUnwrap(uint256,bool)._amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexRewardPoolMock.sol#L27) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexRewardPoolMock.sol#L27


 - [ ] ID-361
Parameter [StargateStrategy.setMultiSwapper(address)._swapper](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L149) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L149


 - [ ] ID-362
Function [ITricryptoLiquidityPool.calc_token_amount(uint256[3],bool)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L33-L36) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L33-L36


 - [ ] ID-363
Constant [GlpStrategy.gmxWethPool](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L43-L44) is not in UPPER_CASE_WITH_UNDERSCORES

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/glp/GlpStrategy.sol#L43-L44


 - [ ] ID-364
Parameter [ITricryptoLPGauge.deposit(uint256,address,bool)._claim_rewards](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGauge.sol#L13) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGauge.sol#L13


 - [ ] ID-365
Parameter [ITricryptoLiquidityPool.add_liquidity(uint256[3],uint256).min_mint_amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L14) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L14


 - [ ] ID-366
Struct [IRouter.lzTxObj](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/interfaces/IRouter.sol#L5-L9) is not in CapWords

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/interfaces/IRouter.sol#L5-L9


 - [ ] ID-367
Parameter [ConvexBoosterMock.deposit(uint256,uint256,bool)._amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexBoosterMock.sol#L38) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexBoosterMock.sol#L38


 - [ ] ID-368
Parameter [StargateRouterMock.instantRedeemLocal(uint16,uint256,address)._amountLP](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/StargateRouterMock.sol#L18) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/StargateRouterMock.sol#L18


 - [ ] ID-369
Parameter [TricryptoLPGetter.calcUsdtToLp(uint256)._amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L113) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L113


 - [ ] ID-370
Parameter [TricryptoLPGetter.addLiquidityWbtc(uint256,uint256)._minAmount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L154) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L154


 - [ ] ID-371
Parameter [TricryptoLPGetter.calcLpToUsdt(uint256)._lpAmount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L107) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L107


 - [ ] ID-372
Variable [Domain.DOMAIN_SEPARATOR_CHAIN_ID](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L16) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/Domain.sol#L16


 - [ ] ID-373
Parameter [StargateSwapperV3.setPoolFee(uint24)._newFee](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateSwapperV3.sol#L43) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateSwapperV3.sol#L43


 - [ ] ID-374
Function [ITricryptoLiquidityPool.add_liquidity(uint256[3],uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L12-L15) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L12-L15


 - [ ] ID-375
Parameter [TricryptoLPGetter.removeLiquidityUsdt(uint256,uint256)._amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L191) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L191


 - [ ] ID-376
Parameter [TricryptoLPGetter.addLiquidityWeth(uint256,uint256)._minAmount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L130) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L130


 - [ ] ID-377
Function [ITricryptoLPGauge.claim_rewards(address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGauge.sol#L18) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGauge.sol#L18


 - [ ] ID-378
Parameter [ITricryptoLiquidityPool.exchange(uint256,uint256,uint256,uint256,bool).use_eth](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L43) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L43


 - [ ] ID-379
Parameter [TricryptoLPStrategy.setMultiSwapper(address)._swapper](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L141) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L141


 - [ ] ID-380
Function [TricryptoLiquidityPoolMock.calc_token_amount(uint256[3],bool)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L54-L59) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L54-L59


 - [ ] ID-381
Parameter [TricryptoLPGetter.removeLiquidityWbtc(uint256,uint256)._minAmount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L168) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L168


 - [ ] ID-382
Function [ICurveEthStEthPool.get_dy(int128,int128,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/interfaces/ICurveEthStEthPool.sol#L12-L16) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/interfaces/ICurveEthStEthPool.sol#L12-L16


 - [ ] ID-383
Parameter [TricryptoLPGetter.addLiquidityWbtc(uint256,uint256)._amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L153) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L153


 - [ ] ID-384
Variable [ERC20Permit._PERMIT_TYPEHASH_DEPRECATED_SLOT](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol#L37) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol#L37


 - [ ] ID-385
Function [IERC20Permit.DOMAIN_SEPARATOR()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Permit.sol#L59) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Permit.sol#L59


 - [ ] ID-386
Function [TricryptoLiquidityPoolMock.calc_withdraw_one_coin(uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L47-L52) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L47-L52


 - [ ] ID-387
Function [IncentivesControllerMock.REWARD_TOKEN()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/IncentivesControllerMock.sol#L19-L21) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/IncentivesControllerMock.sol#L19-L21


 - [ ] ID-388
Parameter [ITricryptoLiquidityPool.remove_liquidity_one_coin(uint256,uint256,uint256)._token_amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L23) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L23


 - [ ] ID-389
Parameter [TricryptoLPGetter.addLiquidityWeth(uint256,uint256)._amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L129) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L129


 - [ ] ID-390
Parameter [TricryptoLPGetter.calcLpToWeth(uint256)._lpAmount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L75) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L75


 - [ ] ID-391
Parameter [ICurveMinter.mint(address)._gauge_addr](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ICurveMinter.sol#L6) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ICurveMinter.sol#L6


 - [ ] ID-392
Parameter [ITricryptoLiquidityPool.remove_liquidity(uint256,uint256[3]).min_amounts](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L19) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L19


 - [ ] ID-393
Parameter [TricryptoLPStrategy.setTricryptoLPGetter(address)._lpGetter](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L150) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPStrategy.sol#L150


 - [ ] ID-394
Function [ERC20Permit.DOMAIN_SEPARATOR()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol#L81-L83) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol#L81-L83


 - [ ] ID-395
Variable [TricryptoLPGetter.USDT](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L34) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L34


 - [ ] ID-396
Function [ITricryptoLiquidityPool.remove_liquidity(uint256,uint256[3])](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L17-L20) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L17-L20


 - [ ] ID-397
Parameter [ConvexRewardPoolMock.stakeFor(address,uint256)._amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexRewardPoolMock.sol#L23) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexRewardPoolMock.sol#L23


 - [ ] ID-398
Parameter [TricryptoLPGetter.removeLiquidityWbtc(uint256,uint256)._amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L167) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L167


 - [ ] ID-399
Parameter [ICurveEthStEthPool.exchange(int128,int128,uint256,uint256).min_dy](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/interfaces/ICurveEthStEthPool.sol#L9) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/interfaces/ICurveEthStEthPool.sol#L9


 - [ ] ID-400
Function [TricryptoLPGaugeMock.crv_token()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLPGaugeMock.sol#L21-L23) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLPGaugeMock.sol#L21-L23


 - [ ] ID-401
Parameter [ERC20Mock.mintTo(address,uint256)._amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L43) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L43


 - [ ] ID-402
Function [ITricryptoLiquidityPool.calc_withdraw_one_coin(uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L28-L31) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L28-L31


 - [ ] ID-403
Function [ITricryptoLPGauge.claimable_reward_write(address,address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGauge.sol#L22-L25) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGauge.sol#L22-L25


 - [ ] ID-404
Variable [TricryptoLPGetter.WBTC](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L35) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L35


 - [ ] ID-405
Function [TricryptoLPGaugeMock.claimable_tokens(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLPGaugeMock.sol#L38-L40) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLPGaugeMock.sol#L38-L40


 - [ ] ID-406
Parameter [TricryptoLPGetter.removeLiquidityUsdt(uint256,uint256)._minAmount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L192) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L192


 - [ ] ID-407
Parameter [ITricryptoLiquidityPool.calc_withdraw_one_coin(uint256,uint256).token_amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L29) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L29


 - [ ] ID-408
Parameter [TricryptoLPGaugeMock.deposit(uint256,address,bool)._value](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLPGaugeMock.sol#L25) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLPGaugeMock.sol#L25


 - [ ] ID-409
Function [ITricryptoLPGauge.crv_token()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGauge.sol#L8) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGauge.sol#L8


 - [ ] ID-410
Parameter [AaveStrategy.setMultiSwapper(address)._swapper](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L129) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/AaveStrategy.sol#L129


 - [ ] ID-411
Parameter [ERC20Mock.updateMintLimit(uint256)._newVal](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L47) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L47


 - [ ] ID-412
Function [YieldBoxPermit.DOMAIN_SEPARATOR()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L109-L111) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBoxPermit.sol#L109-L111


 - [ ] ID-413
Parameter [ERC20Mock.mintTo(address,uint256)._to](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L43) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L43


 - [ ] ID-414
Function [ITricryptoLPGauge.claimable_tokens(address)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGauge.sol#L20) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGauge.sol#L20


 - [ ] ID-415
Parameter [TricryptoLPGetter.calcLpToWbtc(uint256)._lpAmount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L91) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L91


 - [ ] ID-416
Parameter [TricryptoLPGetter.calcWbtcToLp(uint256)._amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L97) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L97


 - [ ] ID-417
Function [ITricryptoLiquidityPool.remove_liquidity_one_coin(uint256,uint256,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L22-L26) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L22-L26


 - [ ] ID-418
Function [ITricryptoLPGetter.USDT()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGetter.sol#L15) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLPGetter.sol#L15


 - [ ] ID-419
Parameter [TricryptoNativeStrategy.setTricryptoLPGetter(address)._lpGetter](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L141) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L141


 - [ ] ID-420
Function [CurveEthStEthPoolMock.get_dy(int128,int128,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/CurveEthStEthPoolMock.sol#L27-L33) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/CurveEthStEthPoolMock.sol#L27-L33


 - [ ] ID-421
Parameter [ITricryptoLiquidityPool.exchange(uint256,uint256,uint256,uint256,bool).min_dy](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L42) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/interfaces/ITricryptoLiquidityPool.sol#L42


 - [ ] ID-422
Function [StkAaveMock.REWARD_TOKEN()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/StkAaveMock.sol#L28-L30) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/StkAaveMock.sol#L28-L30


 - [ ] ID-423
Parameter [TricryptoNativeStrategy.setMultiSwapper(address)._swapper](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L132) is not in mixedCase

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoNativeStrategy.sol#L132


## reentrancy-unlimited-gas
Impact: Informational
Confidence: Medium
 - [ ] ID-424
Reentrancy in [ERC20Mock.withdraw(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L76-L81):
        External calls:
        - [address(msg.sender).transfer(wad)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L79)
        Event emitted after the call(s):
        - [Withdrawal(msg.sender,wad)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L80)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-mocks/contracts/ERC20Mock.sol#L76-L81


 - [ ] ID-425
Reentrancy in [CTokenMock.redeem(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/mocks/CTokenMock.sol#L27-L31):
        External calls:
        - [address(msg.sender).transfer(redeemTokens)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/mocks/CTokenMock.sol#L28)
        State variables written after the call(s):
        - [_burn(msg.sender,redeemTokens)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/mocks/CTokenMock.sol#L29)
                - [_balances[account] = accountBalance - amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L285)
        - [_burn(msg.sender,redeemTokens)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/mocks/CTokenMock.sol#L29)
                - [_totalSupply -= amount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L287)
        Event emitted after the call(s):
        - [Transfer(account,address(0),amount)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L290)
                - [_burn(msg.sender,redeemTokens)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/mocks/CTokenMock.sol#L29)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/mocks/CTokenMock.sol#L27-L31


## similar-names
Impact: Informational
Confidence: Medium
 - [ ] ID-426
Variable [IUniswapV3SwapCallback.uniswapV3SwapCallback(int256,int256,bytes).amount0Delta](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/callback/IUniswapV3SwapCallback.sol#L17) is too similar to [IUniswapV3SwapCallback.uniswapV3SwapCallback(int256,int256,bytes).amount1Delta](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/callback/IUniswapV3SwapCallback.sol#L18)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/callback/IUniswapV3SwapCallback.sol#L17


 - [ ] ID-427
Variable [IUniswapV3PoolActions.collect(address,int24,int24,uint128,uint128).amount0Requested](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolActions.sol#L47) is too similar to [IUniswapV3PoolActions.collect(address,int24,int24,uint128,uint128).amount1Requested](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolActions.sol#L48)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolActions.sol#L47


 - [ ] ID-428
Variable [BaseERC1155Strategy.constructor(IYieldBox,address,uint256)._contractAddress](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L64) is too similar to [IStrategy.contractAddress().contractAddress_](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IStrategy.sol#L36)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L64


 - [ ] ID-429
Variable [BaseERC20Strategy.constructor(IYieldBox,address)._contractAddress](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L54) is too similar to [IStrategy.contractAddress().contractAddress_](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IStrategy.sol#L36)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L54


 - [ ] ID-430
Variable [IUniswapV3PoolOwnerActions.collectProtocol(address,uint128,uint128).amount0Requested](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolOwnerActions.sol#L20) is too similar to [IUniswapV3PoolOwnerActions.collectProtocol(address,uint128,uint128).amount1Requested](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolOwnerActions.sol#L21)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolOwnerActions.sol#L20


 - [ ] ID-431
Variable [IUniswapV3PoolActions.collect(address,int24,int24,uint128,uint128).amount0Requested](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolActions.sol#L47) is too similar to [IUniswapV3PoolOwnerActions.collectProtocol(address,uint128,uint128).amount1Requested](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolOwnerActions.sol#L21)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolActions.sol#L47


 - [ ] ID-432
Variable [IConvexZap.claimRewards(address[],address[],address[],address[],uint256,uint256,uint256,uint256,uint256).depositCrvMaxAmount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/interfaces/IConvexZap.sol#L10) is too similar to [IConvexZap.claimRewards(address[],address[],address[],address[],uint256,uint256,uint256,uint256,uint256).depositCvxMaxAmount](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/interfaces/IConvexZap.sol#L12)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/interfaces/IConvexZap.sol#L10


 - [ ] ID-433
Variable [IUniswapV3PoolState.positions(bytes32).tokensOwed0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolState.sol#L95) is too similar to [IUniswapV3PoolState.positions(bytes32).tokensOwed1](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolState.sol#L96)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolState.sol#L95


 - [ ] ID-434
Variable [IUniswapV3PoolState.positions(bytes32).feeGrowthInside0LastX128](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolState.sol#L93) is too similar to [IUniswapV3PoolState.positions(bytes32).feeGrowthInside1LastX128](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolState.sol#L94)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolState.sol#L93


 - [ ] ID-435
Variable [IUniswapV3PoolState.ticks(int24).feeGrowthOutside0X128](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolState.sol#L70) is too similar to [IUniswapV3PoolState.ticks(int24).feeGrowthOutside1X128](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolState.sol#L71)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolState.sol#L70


 - [ ] ID-436
Variable [IUniswapV3PoolOwnerActions.setFeeProtocol(uint8,uint8).feeProtocol0](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolOwnerActions.sol#L10) is too similar to [IUniswapV3PoolOwnerActions.setFeeProtocol(uint8,uint8).feeProtocol1](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolOwnerActions.sol#L10)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolOwnerActions.sol#L10


 - [ ] ID-437
Variable [IUniswapV3PoolOwnerActions.collectProtocol(address,uint128,uint128).amount0Requested](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolOwnerActions.sol#L20) is too similar to [IUniswapV3PoolActions.collect(address,int24,int24,uint128,uint128).amount1Requested](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolActions.sol#L48)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@uniswap/v3-core/contracts/interfaces/pool/IUniswapV3PoolOwnerActions.sol#L20


## too-many-digits
Impact: Informational
Confidence: Medium
 - [ ] ID-438
[TickMath.getSqrtRatioAtTick(int24)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L24-L82) uses literals with too many digits:
        - [ratio = 0x100000000000000000000000000000000](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L32-L34)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/tapioca-periph/contracts/Swapper/libraries/TickMath.sol#L24-L82


 - [ ] ID-439
[BoringFactory.deploy(address,bytes,bool)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67) uses literals with too many digits:
        - [mstore(uint256,uint256)(clone_deploy_asm_0 + 0x28,0x5af43d82803e903d91602b57fd5bf30000000000000000000000000000000000)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L49)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67


 - [ ] ID-440
[BoringFactory.deploy(address,bytes,bool)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67) uses literals with too many digits:
        - [mstore(uint256,uint256)(clone_deploy_asm_0,0x3d602d80600a3d3981f3363d3d373d3d3d363d73000000000000000000000000)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L47)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67


 - [ ] ID-441
[ShortStrings.slitherConstructorConstantVariables()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/ShortStrings.sol#L40-L122) uses literals with too many digits:
        - [_FALLBACK_SENTINEL = 0x00000000000000000000000000000000000000000000000000000000000000FF](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/ShortStrings.sol#L42)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@openzeppelin/contracts/utils/ShortStrings.sol#L40-L122


 - [ ] ID-442
[BoringFactory.deploy(address,bytes,bool)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67) uses literals with too many digits:
        - [mstore(uint256,uint256)(clone_deploy_asm_1,0x3d602d80600a3d3981f3363d3d373d3d3d363d73000000000000000000000000)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L55)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67


 - [ ] ID-443
[BoringFactory.deploy(address,bytes,bool)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67) uses literals with too many digits:
        - [mstore(uint256,uint256)(clone_deploy_asm_1 + 0x28,0x5af43d82803e903d91602b57fd5bf30000000000000000000000000000000000)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L57)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/@boringcrypto/boring-solidity/contracts/BoringFactory.sol#L32-L67


## unimplemented-functions
Impact: Informational
Confidence: High
 - [ ] ID-444
[BaseERC1155Strategy](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L59-L68) does not implement functions:
        - [BaseStrategy._currentBalance()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L20)
        - [BaseStrategy._deposited(uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L34)
        - [BaseStrategy._withdraw(address,uint256)](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L41)
        - [IStrategy.description()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IStrategy.sol#L26)
        - [IStrategy.name()](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/interfaces/IStrategy.sol#L23)

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/node_modules/tapioca-sdk/dist/contracts/YieldBox/contracts/strategies/BaseStrategy.sol#L59-L68


## immutable-states
Impact: Optimization
Confidence: High
 - [ ] ID-445
[ConvexBoosterMock.lpToken](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexBoosterMock.sol#L12) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexBoosterMock.sol#L12


 - [ ] ID-446
[TricryptoLPGetter.liquidityPool](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L32) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/TricryptoLPGetter.sol#L32


 - [ ] ID-447
[ConvexBoosterMock.receiptToken](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexBoosterMock.sol#L13) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexBoosterMock.sol#L13


 - [ ] ID-448
[StkAaveMock.token](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/StkAaveMock.sol#L12) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/StkAaveMock.sol#L12


 - [ ] ID-449
[LPStakingMock.lpToken](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/LPStakingMock.sol#L10) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/LPStakingMock.sol#L10


 - [ ] ID-450
[IncentivesControllerMock.token](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/IncentivesControllerMock.sol#L12) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/IncentivesControllerMock.sol#L12


 - [ ] ID-451
[StargateStrategy.lpRouterPid](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L50) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L50


 - [ ] ID-452
[StargateStrategy.stgNative](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L51) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L51


 - [ ] ID-453
[BalancerVaultMock.stablePool](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerVaultMock.sol#L12) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerVaultMock.sol#L12


 - [ ] ID-454
[ConvexZapMock.reward2](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexZapMock.sol#L12) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexZapMock.sol#L12


 - [ ] ID-455
[TricryptoLPGaugeMock.lpToken](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLPGaugeMock.sol#L13) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLPGaugeMock.sol#L13


 - [ ] ID-456
[TricryptoLiquidityPoolMock.token](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L13) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L13


 - [ ] ID-457
[StargateSwapperV3.owner](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateSwapperV3.sol#L27) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateSwapperV3.sol#L27


 - [ ] ID-458
[TricryptoLiquidityPoolMock.weth](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L14) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLiquidityPoolMock.sol#L14


 - [ ] ID-459
[TricryptoLPGaugeMock.rewardToken](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLPGaugeMock.sol#L14) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/TricryptoLPGaugeMock.sol#L14


 - [ ] ID-460
[YearnVaultMock.asset](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/yearn/mocks/YearnVaultMock.sol#L10) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/yearn/mocks/YearnVaultMock.sol#L10


 - [ ] ID-461
[LidoEthStrategy.curveStEthPool](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/LidoEthStrategy.sol#L38) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/LidoEthStrategy.sol#L38


 - [ ] ID-462
[ConvexZapMock.reward1](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexZapMock.sol#L11) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexZapMock.sol#L11


 - [ ] ID-463
[CurveMinterMock.token](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/CurveMinterMock.sol#L10) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/curve/mocks/CurveMinterMock.sol#L10


 - [ ] ID-464
[ConvexBoosterMock.crvRewards](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexBoosterMock.sol#L14) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexBoosterMock.sol#L14


 - [ ] ID-465
[RouterETHMock.lpToken](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/RouterETHMock.sol#L8) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/RouterETHMock.sol#L8


 - [ ] ID-466
[RouterETHMock.stgRouter](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/RouterETHMock.sol#L7) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/RouterETHMock.sol#L7


 - [ ] ID-467
[ConvexRewardPoolMock.rewardToken](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexRewardPoolMock.sol#L11) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexRewardPoolMock.sol#L11


 - [ ] ID-468
[CTokenMock.underlying](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/mocks/CTokenMock.sol#L10) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/compound/mocks/CTokenMock.sol#L10


 - [ ] ID-469
[ConvexRewardPoolMock.lpToken](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexRewardPoolMock.sol#L10) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/convex/mocks/ConvexRewardPoolMock.sol#L10


 - [ ] ID-470
[StargateStrategy.lpStakingPid](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L49) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L49


 - [ ] ID-471
[LendingPoolMock.asset](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/LendingPoolMock.sol#L10) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/aave/mocks/LendingPoolMock.sol#L10


 - [ ] ID-472
[StargateRouterMock.stgToken](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/StargateRouterMock.sol#L10) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/StargateRouterMock.sol#L10


 - [ ] ID-473
[BalancerStrategy.poolId](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L37) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/BalancerStrategy.sol#L37


 - [ ] ID-474
[StargateStrategy.stgEthPool](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L43) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L43


 - [ ] ID-475
[StargateStrategy.stgTokenReward](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L52) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/StargateStrategy.sol#L52


 - [ ] ID-476
[CurveEthStEthPoolMock.steth](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/CurveEthStEthPoolMock.sol#L10) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/lido/mocks/CurveEthStEthPoolMock.sol#L10


 - [ ] ID-477
[BalancerVaultMock.weth](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerVaultMock.sol#L13) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/balancer/mocks/BalancerVaultMock.sol#L13


 - [ ] ID-478
[LPStakingMock.reward](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/LPStakingMock.sol#L11) should be immutable

https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/main/contracts/stargate/mocks/LPStakingMock.sol#L11
