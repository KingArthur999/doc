# AMAT 主网第一版、第三版、第四版与第五版对比

> 第一版数据取自主网历史快照区块 `1971414`；第三版余额数据查询于主网区块 `2025154`，权限状态复核于区块 `2025497`；第四版是当前生产版本。第五版于 2026-09-03 完成独立合约部署，并在区块 `2115181` 通过链上验收；目前尚未迁移资金、初始化历史销毁量、添加流动性、开放交易、切换前后端或转移 Owner，不能视为已上线版本。

## 合约地址

| 合约 | 第一版 | 第三版 | 第四版 | 第五版（候选） | 前后端配置位置 |
|---|---|---|---|---|---|
| AMAT | `0x3EE2e767957EdBF92ACE6ADE7AC7Ae24d894eEe3` | `0x58D394C52BAcbF37c0AcbF76Ed4B9F3fC1348BBA` | `0xa8A4682Ed533d7c073e3DcddB2c1c861d4bA23eF` | `0x6D7dF211d2573EA3dA2c23028d1303f186f46181` | `swap-web` 的 `hnt`；`rwa-web` 的 `amat` |
| HNS | `0xFB81DEf8FCE7CA5CE970AFf0A92b391223122F37` | `0xA117a533E14B41B015d739FD9cF85Ee7d9a9333c` | 复用第三版 `0xA117a533E14B41B015d739FD9cF85Ee7d9a9333c` | `0x6bB6fbd678Be5D56f9E9fbB86f4b346702979564` | 两个前端 `addr-prod.js` 的 `hns` |
| Factory | `0x57cec2862d1AEcB782FCD9CCa3D73623223df617` | `0xe5b2C36C8d6d022F7109912648e8b1425B257275` | `0x740eD20D6b58ceE7E53742cC15B74e8B278C5ed5` | `0xeA314d53f5749b0f69ee3891913Afb62DC8323E5` | 不直接配置，由 Router 绑定 |
| AMAT/WAMAX Pair | `0x8c00Cf5EE9134Ad45Fb022B9a7794FCFD48F389a` | `0xa579F7Ce98170232d74CE6Fd1cA21C0192390aDE` | `0xe20713428E413Cf18F4607471f7ca0FF186bfb72` | `0x81aF4468D0a11aFeF876EA8D72bE4c76ff34134A` | Swap、AddLiquidity 链上配置 |
| Router | `0x1C3726C2d8f96FE29395E3AE75e6187BE15e16d7` | `0xD5C3EF7A8CBc52A47187507110854614dc5498e5` | `0x95D012FDe9be6940fbdbcF3FE5Ec39A3a6Cc5EdB` | `0xE455B45113F98f96382a4f85f748B65952194486` | Swap 链上配置 |
| ProxyAdmin | `0xA5cCbd613ab7d8A07A84B228F46f1466FE2CB5ed` | `0x02D6bb6db7aE7D91C45b88A7e9ac122712960aCF` | `0x103f298cdb2692895aDE6A09241c327c6f73d812` | `0xbE96E30182743af28b81b0A9609705239F547B12` | 仅升级脚本和运维记录 |
| Stake Proxy | `0x2121C8bb3B25e4DDFB3AFd66fBA1a98D1Ad8519b` | `0x566c977de3379D771638bb3E07aEcE995E0Ba1C6` | `0x960b934cFf63D14F529eB7345B8aA7CE6ddCFd96` | `0x8c2363Ae0711ad67Fcf4059B1DF734d36D42e654` | 两个前端的 `stake`；Go 签名服务 `StakeAddr` |
| Stake Implementation | `0x7859961cb68A1Be7E3cc521ba3A0443Fd53f4974` | `0xFa4332C3B4500aaC371769c9787135a4De7D21D9` | `0x742Ac0e913D6880f2DDf3536628D9Eacb072E3CE` | `0x74f837e6CEeB30a63335De363bECED393518665E` | 不配置到业务端 |
| Swap Proxy | `0x3c589859C3244B5Ec581C18a0e4326c540fFb073` | `0xcAA81433BF992bD74155eCA13f9050e73FCC2D6f` | `0x9d7F3eDE438286368065E4173820D0C553e5a679` | `0x41196B43b7312386A553661D5267EF89223a6FBb` | 两个前端的 `swap` |
| Swap Implementation | `0x74FeFD008cA6AA982aF02d683e31F7811dFF9f3E` | `0x34a8A7A767d12657e3F843DC3166015d7BC416a0` | `0xbba46A96ebFd05a3f5C4E589a69651259B452D95` | `0x707f5c8Bc56C1Fe0B936B9b1721e4EB061d852A3` | 不配置到业务端 |
| AddLiquidity Proxy | `0x08abC66F6360874aB94B1752D58647a5A86bd959` | `0x3B9638F36F53F81bEF433299f381B416cCF4F7F1` | `0xa2A14f347125f6E0be0D0A406Fa177Aa7540Fc8E` | `0x39030C26EB5036F5F6e3eBE044Db7B6cb0032623` | `rwa-web` 的 `addLiquidityByAdmin` |
| AddLiquidity Implementation | `0xbf451ba7aB185e01B72FBC98fEa8ABF199be3f27` | `0x80C53b0445F4f75AA81Af0Df2DC6804f3eB28dc3` | `0x865e2367896c1a613B28b46FC282f730891D4086` | `0xe90c6CcD85fEBed3C3c2d9f39d81EFA55b728bb6` | 不配置到业务端 |
| RewardShare Proxy | `0x0E4625EA092fA1C3755738BcCF165af68A3F2e51` | `0x37402f5F208Ad74e96aAEFC8182637a6e2960aB4` | `0x50de5040664B28370a5DFeDCC3bb1607538D9e1b` | `0x45212D5be13322C53c58EFed885f14f75a8af2e9` | `rwa-web` 的 `rewardShare` |
| RewardShare Implementation | `0xC4B3115D55c1B1E6a2485069773824e5E46059D4` | `0xB942c7843a8c94f1bf7b8BBB215DfaFeCc699Da1` | `0x2d03D260fC5cA4a24DB29a799a23B78BC0c6179e` | `0x9bE65f61b097911933060d157Df85891D1753e42` | 不配置到业务端 |
| PoolBurn Proxy | `0x9556284ec62D914368a56f82788c21048BaFA804` | `0xfD6702009572eC6635b1b9C8FB0E91Fc3fcdA487` | `0x61c7Bcf84C11D438587AfB00857EB27eFd6E4F16` | `0x5a86D81685507825F6946E4c4B59de8C7298B4C8` | Swap 链上配置 |
| PoolBurn Implementation | `0x147F32F89aC7CB65B31dEF43296F629F0C576FA7` | `0x6f779bfDeE996Ce52dfBd3ADfa2990e13561E6aD` | `0x262987CC7700aDae42354575665cF3B319abdc25` | `0xb7f3D4C6335A0239745C3A2c455190BE8767a08f` | 不配置到业务端 |

外部合约各版一致：USDT `0x2eDE...2064`、WAMAX `0x18b7...F0a9`、AMAX/USDT Pair `0x1aBf...Ec3e`、AMAX/USDT Router `0xA4D0...F9eD`、Invitation `0x3333...3333`。

## AMAT Token

| 参数/状态 | 第一版 | 第三版 | 第四版 |
|---|---:|---:|---:|
| Owner | `0x5B2020...baC95` | `0x5B2020...baC95` | `0x69fedC...0591D`（待转移） |
| Emergency | `0x990Faf...E3897` | `0x69d29C...d0E0C` | `0x5B2020...baC95` |
| 是否暂停 | 是 | 否，转账已开放 | 否，转账已开放 |
| totalSupply | `105,306,038.735783367061063206 AMAT` | `105,300,083.308724551048451097 AMAT` | `104,858,424.114474635630963198 AMAT` |
| 黑名单功能 | 无 | 无 | 有，Owner 可添加/删除 |
| 合约自身 AMAT 余额 | `20,266.1033 AMAT` | `0 AMAT` | `0 AMAT` |
| 合约原生 AMAX 余额 | `1.009 AMAX` | `0 AMAX` | `0 AMAX` |

## HNS Token

| 参数/状态 | 第一版 | 第三版 | 第四版 |
|---|---:|---:|---:|
| Owner | `0x5B2020...baC95` | `0x5B2020...baC95` | 复用第三版，`0x5B2020...baC95` |
| Emergency | `0x990Faf...E3897` | `0x69d29C...d0E0C` | 复用第三版，`0x69d29C...d0E0C` |
| 是否暂停 | 是 | 否，转账已开放 | 复用第三版，未暂停 |
| totalSupply | `97,609,075.475977 HNS` | `97,608,523.5731815 HNS` | `97,568,398.32921 HNS`（复用合约当前值） |
| 合约自身 HNS 余额 | `94,900.923298 HNS` | `0 HNS` | `0 HNS` |
| 合约原生 AMAX 余额 | `0.7 AMAX` | `0 AMAX` | `0 AMAX` |

## Factory

| 参数/状态 | 第一版 | 第三版 | 第四版 |
|---|---|---|---|
| Owner | `0x990Faf...E3897` | `0x5B2020...baC95` | `0x69fedC...0591D`（待转移） |
| feeTo | 零地址 | 零地址 | 零地址 |
| feeToSetter | `0x990Faf...E3897` | `0xFE7133...Fa7cB` | `0xFE7133...Fa7cB` |
| Pair 数量 | `3` | `1` | `1` |
| 合约余额 | `0` | `0` | `0` |

## AMAT/WAMAX Pair

| 参数/状态 | 第一版 | 第三版 | 第四版 |
|---|---:|---:|---:|
| Owner | `0x990Faf...E3897` | `0x5B2020...baC95` | `0x69fedC...0591D`（待转移） |
| token0 | WAMAX | WAMAX | WAMAX |
| token1 | 第一版 AMAT | 第三版 AMAT | 第四版 AMAT |
| WAMAX 储备 | 历史快照时已提取，为 `0` | `3,022,984.560014677591401242` | `3,022,985.012161371171741010` |
| AMAT 储备 | 历史快照时已提取，为 `0` | `31,161,686.257669564327137259` | `31,161,907.563537117651396668` |
| 价格 | 迁移基准约 `0.097009659 AMAX/AMAT` | 约 `0.097009659 AMAX/AMAT` | 约 `0.097009 AMAX/AMAT` |
| LP totalSupply | `3.162277660168379331` | `9,695,293.748686652821114957` | `9,704,590.212327637505676223` |
| 部署账号 authorized | 是 | 否 | 是（待移除） |
| 最终 Owner authorized | 否 | 是 | 否（待配置） |

## Router

| 参数/状态 | 第一版 | 第三版 | 第四版 |
|---|---|---|---|
| Owner | `0x990Faf...E3897` | `0x5B2020...baC95` | `0x69fedC...0591D`（待转移） |
| Factory | 第一版 Factory | 第三版 Factory | 第四版 Factory |
| WETH | WAMAX | WAMAX | WAMAX |
| 部署账号 authorized | 是 | 否 | 是（待移除） |
| 最终 Owner authorized | 否 | 是 | 是 |
| 合约余额 | `0` | `0` | `0` |

## ProxyAdmin

| 参数/状态 | 第一版 | 第三版 | 第四版 |
|---|---|---|---|
| Owner | `0x5B2020...baC95` | `0x5B2020...baC95` | `0x69fedC...0591D`（待转移） |
| 管理范围 | 第一版 5 个代理 | 第三版 5 个代理 | 第四版 5 个代理 |
| 合约余额 | `0` | `0` | `0` |

## Stake

| 参数/状态 | 第一版 | 第三版 | 第四版 |
|---|---:|---:|---:|
| Owner | `0x5B2020...baC95` | `0x5B2020...baC95` | `0x69fedC...0591D`（待转移） |
| signer | `0xc25Ece...ceAf1` | `0x5f5261...6F4` | `0x5f5261...6F4` |
| 手续费接收 | `0x990Faf...E3897` | `0xFE7133...Fa7cB` | `0xFE7133...Fa7cB` |
| AMAT/HNS 铸造比例 | `50% / 50%` | `50% / 50%` | `50% / 50%` |
| HNS 参考价格 | `1` | `1` | `1` |
| AMAT 参考价格 | 链上 AMM 现货价 | `0.092672702499218719` | `Swap.getHntPrice()` 实时价；当前 `priceHnt()` 返回 `0.08664` |
| 价格有效期 priceMaxAge | 无 | `0`，不限制过期 | `0`，实时价逻辑不依赖过期时间 |
| 质押周期步长 | `1,800 秒` | `1,800 秒` | `1,800 秒` |
| 最小质押值 | `1` | `1` | `1` |
| needNotPayFee | `false` | `false` | `false` |
| AMAT 余额/可用奖励 | `21,850,999.758820357685786015` | `999,999.9994` | `298,610.452254241436647946`，其中可用奖励约 `298,610.452194241436647946` |
| HNS 余额 | `0` | `0` | `0` |
| 原生 AMAX 余额 | `0.1` | `0` | `0` |
| 部署账号 Operator | 第一版旧部署账号：是 | 否 | 是（待移除） |
| 最终 Owner Operator | 否 | 否 | 否 |

## Swap

| 参数/状态 | 第一版 | 第三版 | 第四版 |
|---|---:|---:|---:|
| Owner | `0x5B2020...baC95` | `0x5B2020...baC95` | `0x69fedC...0591D`（待转移） |
| 卖出开关 isSellOpen | 开启 | 开启 | 开启 |
| canSellGlobal | `false` | `false` | `true` |
| notBurnGlobal | `false` | `false` | `false` |
| is210Now | `false` | `false` | `false` |
| sellAmountDaily | `1 AMAT` | `20,000 AMAT` | `20,000 AMAT` |
| 单日全局卖出上限 | `10,000,000 AMAT` | `10,000,000 AMAT` | `0`，沿用第三版当前链上配置 |
| 单日全局买入上限 | `2,000,000 AMAT` | `2,000,000 AMAT` | `0`，沿用第三版当前链上配置 |
| slip | `10%` | `10%` | `10%` |
| sellSlip | `6%` | `6%` | `6%` |
| buyShareSlip | `15%` | `15%` | `15%` |
| sharePercent | `4%` | `4%` | `4%` |
| buyGiveMorePercent | `4.5%` | `4.5%` | `4.5%` |
| Pair 增加比例 | `20%` | `20%` | `20%` |
| isIncrease2PairPool | `true` | `true` | `true` |
| burnMul | `2` | `2` | `2` |
| burnAmountTarget | `97,900,000 AMAT` | `97,900,000 AMAT` | `97,900,000 AMAT` |
| burnAmount | `70,052,828.300757400683287947 AMAT` | `70,052,828.330157400683287947 AMAT` | `70,052,828.333097400683287947 AMAT` |
| 额外 AMAX 接收比例 | `0` | `0` | `0` |
| 额外 AMAX 接收地址 | `0x9c95BE...EC7b16` | `0xe0096B...a5b4d` | `0xe0096B...a5b4d` |
| AMAT/HNS/WAMAX/AMAX 余额 | 接近 `0` | 全部 `0` | 全部 `0` |
| 部署账号 Operator | 第一版旧部署账号：是 | 否 | 是（待移除） |
| 最终 Owner Operator | 否 | 否 | 否 |

## AddLiquidityByAdmin

| 参数/状态 | 第一版 | 第三版 | 第四版 |
|---|---:|---:|---:|
| Owner | `0x5B2020...baC95` | `0x5B2020...baC95` | `0x69fedC...0591D`（待转移） |
| Pair | 第一版 Pair | 第三版 Pair | 第四版 Pair |
| AMAX/WAMAX 最低储备阈值 | `2,000,000 AMAX` | `3,000,000 AMAX` | `3,000,000 AMAX` |
| AMAT/HNS/WAMAX/AMAX 余额 | `0` | `0` | `0` |
| 部署账号 Operator | 第一版旧部署账号：是 | 否 | 否 |
| 最终 Owner Operator | 否 | 是 | 是 |

## RewardShare

| 参数/状态 | 第一版 | 第三版 | 第四版 |
|---|---|---|---|
| Owner | `0x5B2020...baC95` | `0x5B2020...baC95` | `0x69fedC...0591D`（待转移） |
| 75% 接收地址 admin1 | `0x21246a...16588` | `0x93019d...eEac8` | `0x93019d...eEac8` |
| 25% 接收地址 admin2 | `0xE369fe...76c51` | `0x25cb73...ff0Dc` | `0x25cb73...ff0Dc` |
| token | 零地址，分配原生 AMAX | 零地址，分配原生 AMAX | 零地址，分配原生 AMAX |
| 分配比例 | `75% / 25%` | `75% / 25%` | `75% / 25%` |
| AMAT/HNS/WAMAX/AMAX 余额 | 接近 `0` | 全部 `0` | 全部 `0` |
| 部署账号 Operator | 第一版旧部署账号：是 | 否 | 是（待移除） |
| 最终 Owner Operator | 否 | 否 | 否 |

## PoolBurn

| 参数/状态 | 第一版 | 第三版 | 第四版 |
|---|---:|---:|---:|
| Owner | `0x990Faf...E3897` | `0x5B2020...baC95` | `0x69fedC...0591D`（待转移） |
| Token | 第一版 AMAT | 第三版 AMAT | 第四版 AMAT |
| AMAT 余额 | `53,155,519.111710224091371552` | `53,155,516.891285669621768796` | `53,155,283.635961770719202990` |
| HNS/WAMAX/AMAX 余额 | `0` | `0` | `0` |
| 部署账号 Operator | 第一版旧部署账号：是 | 否 | 否 |
| 最终 Owner Operator | 否 | 否 | 否 |

## 第三版账号配置

| 功能 | 当前地址 | 修改方式 |
|---|---|---|
| 原部署账号 | `0x69fedCD10A446F1e277b9aFAe4C371e59A40591D` | 已移除 Owner、Operator、Token 白名单及 Pair/Router authorized 权限 |
| 最终 Owner | `0x5B20201ABe1b550F685Fff837f3749AfE21baC95` | 当前所有合约 Owner、ProxyAdmin Owner、Pair/Router authorized 及 LP 持有人 |
| AMAT/HNS Emergency | `0x69d29C97ab2C41e882262ab5a51d56c4808d0E0C` | `setEmergency(address)` |
| Stake signer | `0x5f5261D5EE00cf77fff47667846C4Af47F6Cc6F4` | `Stake.setSigner(address)`；同步 Go 签名服务 |
| Stake 手续费接收 | `0xFE713348F8178C646927D3F31ade1A6448cFa7cB` | `Stake.setFeeRev(address)` |
| Swap 额外 AMAX 接收 | `0xe0096BF586D637447860Cc567F755192ddEa5b4d` | `Swap.setMoreTakeOutToAddr(0,address)` |
| RewardShare 75% 接收 | `0x93019dBdBd6eBEd325f6b8D5BBE4faBc41EeEac8` | `RewardShare.set1stAddr(address)` |
| RewardShare 25% 接收 | `0x25cb73F7314d8C318E6DdaeEfd58d418a1aff0Dc` | `RewardShare.set2ndAddr(address)` |

## 第三版权限状态

- AMAT、HNS、Factory、Pair、Router、Stake、Swap、AddLiquidity、RewardShare、PoolBurn 和 ProxyAdmin 的 Owner 均已转给最终 Owner。
- 部署账号的 Stake、Swap、AddLiquidity、RewardShare、PoolBurn Operator 权限均为 `false`。
- 部署账号的 AMAT/HNS 白名单及 Pair/Router `authorized` 权限均为 `false`。
- 最终 Owner 的 AMAT/HNS 白名单及 Pair/Router `authorized` 权限均为 `true`。
- AMAT/HNS Emergency 仍为独立地址 `0x69d29C...d0E0C`；Factory `feeToSetter` 仍为 `0xFE7133...Fa7cB`。
- LP Token 已转给最终 Owner，仅保留 Pair 创建时永久锁定的最小 LP。

## 第四版账号配置核对

| 功能 | 第四版链上当前地址 | 核对结果 | 修改方式 |
|---|---|---|---|
| 部署账号 / 当前 Owner | `0x69fedCD10A446F1e277b9aFAe4C371e59A40591D` | 仍是所有第四版新合约及 ProxyAdmin Owner，待最终转移 | 各合约 `transferOwnership(address)` |
| 最终 Owner | `0x5B20201ABe1b550F685Fff837f3749AfE21baC95` | LP 持有人；尚未接收第四版新合约 Owner | 由部署账号统一转移 |
| AMAT Emergency | `0x5B20201ABe1b550F685Fff837f3749AfE21baC95` | 与第三版独立 Emergency 不同；当前为最终 Owner | `AMAT.setEmergency(address)` |
| HNS Emergency | `0x69d29C97ab2C41e882262ab5a51d56c4808d0E0C` | 正确，复用第三版配置 | `HNS.setEmergency(address)` |
| Stake signer | `0x5f5261D5EE00cf77fff47667846C4Af47F6Cc6F4` | 正确；Go 服务必须使用对应私钥 | `Stake.setSigner(address)` |
| Stake 手续费接收 | `0xFE713348F8178C646927D3F31ade1A6448cFa7cB` | 正确 | `Stake.setFeeRev(address)` |
| Factory feeToSetter | `0xFE713348F8178C646927D3F31ade1A6448cFa7cB` | 正确 | `Factory.setFeeToSetterByOwner(address)` |
| Swap 额外 AMAX 接收 | `0xe0096BF586D637447860Cc567F755192ddEa5b4d` | 正确；接收比例当前为 `0` | `Swap.setMoreTakeOutToAddr(0,address)` |
| RewardShare 75% 接收 | `0x93019dBdBd6eBEd325f6b8D5BBE4faBc41EeEac8` | 正确 | `RewardShare.set1stAddr(address)` |
| RewardShare 25% 接收 | `0x25cb73F7314d8C318E6DdaeEfd58d418a1aff0Dc` | 正确 | `RewardShare.set2ndAddr(address)` |

第四版权限现状：

- 部署账号仍是 AMAT、Factory、Pair、Router、Stake、Swap、AddLiquidity、RewardShare、PoolBurn 和 ProxyAdmin Owner。
- 部署账号仍是 Pair/Router authorized，并保留 AMAT 白名单；最终 Owner 是 Router authorized 和 AMAT 白名单，但尚不是 Pair authorized。
- Stake、Swap、RewardShare 的部署账号 Operator 仍为 `true`；AddLiquidity 的部署账号 Operator 已移除，最终 Owner Operator 为 `true`。
- PoolBurn 的部署账号及最终 Owner Operator 均为 `false`。
- 因此业务收款账号和 signer 配置正确，但最终 Owner/Operator/authorized 权限迁移尚未完成。

## 第四版当前阶段

- 已部署第四版 AMAT、Factory、Pair、Router、ProxyAdmin 和 5 个业务代理；HNS 继续使用第三版合约。
- 第四版 AMAT 已完成历史销毁量初始化、余额迁移和转账开放；当前总供应量约 `104,858,424.114474635630963198 AMAT`。
- Pair 已加入约 `3,022,985.012161 WAMAX` 与 `31,161,907.563537 AMAT`，LP Token 已由最终 Owner 持有。
- Stake 当前持有约 `298,610.452254 AMAT`；PoolBurn 当前持有约 `53,155,283.635962 AMAT`。
- Swap `isSellOpen=true`、`canSellGlobal=true`；AddLiquidity 最低储备阈值已设置为 `3,000,000 AMAX`。
- 新合约 Owner 和 ProxyAdmin Owner 仍是部署账号 `0x69fedC...0591D`，尚未统一转给最终 Owner。
- HNS 的 Owner、Emergency、暂停状态和 totalSupply 在第四版部署前后没有变化。
- Go 服务需要切换第四版 Stake，并重置第四版事件读取游标；Java、用户前端和 Swap 前端需要切换第四版地址。

> 第四版部署记录：`deployments/evamain-v4-contracts.json`，合约仓库提交 `081913e`。截至本次核验，线上 `amatthing.xyz` 与 `superswaps.xyz` 的构建包仍使用第三版 AMAT、Stake 和 Swap 地址。

## 第五版候选部署

第五版是主网上单独部署的一整套新合约，配置来源为第四版区块 `2115012` 的实时快照。部署脚本和独立验收均已通过，Hardhat 回归测试结果为 `120 passing`。

### 当前状态

| 项目 | 第五版当前值 |
|---|---|
| 当前 Owner | 部署账号 `0x69fedCD10A446F1e277b9aFAe4C371e59A40591D`，尚未转给最终 Owner |
| 最终 Owner | `0x5B20201ABe1b550F685Fff837f3749AfE21baC95` |
| AMAT | 已暂停；总量 `210,000,000 AMAT`；尚未初始化历史销毁 |
| HNS | 新部署；未暂停；总量 `100,000,000 HNS`；尚未初始化历史销毁 |
| Pair | WAMAX、AMAT 储备均为 `0`，LP totalSupply 为 `0` |
| Stake / PoolBurn | AMAT 余额均为 `0`，尚未注资 |
| Swap | `burnAmount=0`、`isSellOpen=false`、`canSellGlobal=false` |
| AddLiquidity 最低储备阈值 | `0`，添加流动性后再设置 |
| 前后端 | 尚未切换，第四版继续运行 |

### 已镜像的业务配置

| 配置 | 第五版值 |
|---|---|
| Stake signer | `0x5f5261D5EE00cf77fff47667846C4Af47F6Cc6F4` |
| Stake 手续费接收 | `0xFE713348F8178C646927D3F31ade1A6448cFa7cB` |
| AMAT/HNS 质押比例 | `50% / 50%` |
| HNS 参考价格 | `1 USDT` |
| 质押周期步长 | `1,800 秒` |
| 全平台每日买入额度 | `100,000,000 AMAT` |
| 单账号每日买入额度 | `100,000,000 AMAT` |
| 全平台每日卖出额度 | `10 AMAT` |
| 单账号每日卖出额度 | `10 AMAT` |
| 买入费率 | `0%` |
| 卖出 Token 费率 | `6%` |
| 卖出 AMAX 分润 | `4%` |
| RewardShare 75% 接收 | `0x93019dBdBd6eBEd325f6b8D5BBE4faBc41EeEac8` |
| RewardShare 25% 接收 | `0x25cb73F7314d8C318E6DdaeEfd58d418a1aff0Dc` |
| Swap 额外 AMAX 接收 | `0xe0096BF586D637447860Cc567F755192ddEa5b4d`，比例为 `0` |
| Factory feeToSetter | `0xFE713348F8178C646927D3F31ade1A6448cFa7cB` |

### 待执行工作

1. 初始化 AMAT/HNS 历史销毁量和 Swap `burnAmount`。
2. 按确认后的快照迁移 Token 余额，并给 Stake、PoolBurn 注资。
3. 按第四版价格添加 AMAT/WAMAX 流动性，设置最低储备阈值。
4. 小额测试买入、卖出、质押和领取流程。
5. 切换 Go、Java、两个前端及监听任务的合约地址和起始区块。
6. 移除部署账号 Operator、authorized 和 Token 白名单权限。
7. 设置 Emergency，并将全部 Owner 和 ProxyAdmin Owner 转给最终 Owner。
8. 最终验收后再开放 AMAT 转账与 Swap 交易。

> 第五版部署记录：`deployments/evamain-v5-contracts-only.json`。主网链上独立验收通过区块：`2115181`。当前第五版仅为候选部署，不应配置到生产前后端。
