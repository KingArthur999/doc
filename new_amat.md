# AMAT 主网第一版与第三版对比

> 第一版数据取自主网历史快照区块 `1971414`；第三版数据查询于主网区块 `2025154`。余额、累计量和 Pair 储备属于动态数据，后续会随业务变化。

## 合约地址

| 合约 | 第一版 | 第三版 | 前后端配置位置 |
|---|---|---|---|
| AMAT | `0x3EE2e767957EdBF92ACE6ADE7AC7Ae24d894eEe3` | `0x58D394C52BAcbF37c0AcbF76Ed4B9F3fC1348BBA` | `swap-web` 的 `hnt`；`rwa-web` 的 `amat` |
| HNS | `0xFB81DEf8FCE7CA5CE970AFf0A92b391223122F37` | `0xA117a533E14B41B015d739FD9cF85Ee7d9a9333c` | 两个前端 `addr-prod.js` 的 `hns` |
| Factory | `0x57cec2862d1AEcB782FCD9CCa3D73623223df617` | `0xe5b2C36C8d6d022F7109912648e8b1425B257275` | 不直接配置，由 Router 绑定 |
| AMAT/WAMAX Pair | `0x8c00Cf5EE9134Ad45Fb022B9a7794FCFD48F389a` | `0xa579F7Ce98170232d74CE6Fd1cA21C0192390aDE` | Swap、AddLiquidity 链上配置 |
| Router | `0x1C3726C2d8f96FE29395E3AE75e6187BE15e16d7` | `0xD5C3EF7A8CBc52A47187507110854614dc5498e5` | Swap 链上配置 |
| ProxyAdmin | `0xA5cCbd613ab7d8A07A84B228F46f1466FE2CB5ed` | `0x02D6bb6db7aE7D91C45b88A7e9ac122712960aCF` | 仅升级脚本和运维记录 |
| Stake Proxy | `0x2121C8bb3B25e4DDFB3AFd66fBA1a98D1Ad8519b` | `0x566c977de3379D771638bb3E07aEcE995E0Ba1C6` | 两个前端的 `stake`；Go 签名服务 `StakeAddr` |
| Stake Implementation | `0x7859961cb68A1Be7E3cc521ba3A0443Fd53f4974` | `0xFa4332C3B4500aaC371769c9787135a4De7D21D9` | 不配置到业务端 |
| Swap Proxy | `0x3c589859C3244B5Ec581C18a0e4326c540fFb073` | `0xcAA81433BF992bD74155eCA13f9050e73FCC2D6f` | 两个前端的 `swap` |
| Swap Implementation | `0x74FeFD008cA6AA982aF02d683e31F7811dFF9f3E` | `0x34a8A7A767d12657e3F843DC3166015d7BC416a0` | 不配置到业务端 |
| AddLiquidity Proxy | `0x08abC66F6360874aB94B1752D58647a5A86bd959` | `0x3B9638F36F53F81bEF433299f381B416cCF4F7F1` | `rwa-web` 的 `addLiquidityByAdmin` |
| AddLiquidity Implementation | `0xbf451ba7aB185e01B72FBC98fEa8ABF199be3f27` | `0x80C53b0445F4f75AA81Af0Df2DC6804f3eB28dc3` | 不配置到业务端 |
| RewardShare Proxy | `0x0E4625EA092fA1C3755738BcCF165af68A3F2e51` | `0x37402f5F208Ad74e96aAEFC8182637a6e2960aB4` | `rwa-web` 的 `rewardShare` |
| RewardShare Implementation | `0xC4B3115D55c1B1E6a2485069773824e5E46059D4` | `0xB942c7843a8c94f1bf7b8BBB215DfaFeCc699Da1` | 不配置到业务端 |
| PoolBurn Proxy | `0x9556284ec62D914368a56f82788c21048BaFA804` | `0xfD6702009572eC6635b1b9C8FB0E91Fc3fcdA487` | Swap 链上配置 |
| PoolBurn Implementation | `0x147F32F89aC7CB65B31dEF43296F629F0C576FA7` | `0x6f779bfDeE996Ce52dfBd3ADfa2990e13561E6aD` | 不配置到业务端 |

外部合约两版一致：USDT `0x2eDE...2064`、WAMAX `0x18b7...F0a9`、AMAX/USDT Pair `0x1aBf...Ec3e`、AMAX/USDT Router `0xA4D0...F9eD`、Invitation `0x3333...3333`。

## AMAT Token

| 参数/状态 | 第一版 | 第三版 |
|---|---:|---:|
| Owner | `0x5B2020...baC95` | `0x69fedC...0591D` |
| Emergency | `0x990Faf...E3897` | `0x69d29C...d0E0C` |
| 是否暂停 | 是 | 否，转账已开放 |
| totalSupply | `105,306,038.735783367061063206 AMAT` | `105,300,083.308724551048451097 AMAT` |
| 合约自身 AMAT 余额 | `20,266.1033 AMAT` | `0 AMAT` |
| 合约原生 AMAX 余额 | `1.009 AMAX` | `0 AMAX` |

## HNS Token

| 参数/状态 | 第一版 | 第三版 |
|---|---:|---:|
| Owner | `0x5B2020...baC95` | `0x69fedC...0591D` |
| Emergency | `0x990Faf...E3897` | `0x69d29C...d0E0C` |
| 是否暂停 | 是 | 否，转账已开放 |
| totalSupply | `97,609,075.475977 HNS` | `97,608,523.5731815 HNS` |
| 合约自身 HNS 余额 | `94,900.923298 HNS` | `0 HNS` |
| 合约原生 AMAX 余额 | `0.7 AMAX` | `0 AMAX` |

## Factory

| 参数/状态 | 第一版 | 第三版 |
|---|---|---|
| Owner | `0x990Faf...E3897` | `0x69fedC...0591D` |
| feeTo | 零地址 | 零地址 |
| feeToSetter | `0x990Faf...E3897` | `0xFE7133...Fa7cB` |
| Pair 数量 | `3` | `1` |
| 合约余额 | `0` | `0` |

## AMAT/WAMAX Pair

| 参数/状态 | 第一版 | 第三版 |
|---|---:|---:|
| Owner | `0x990Faf...E3897` | `0x69fedC...0591D` |
| token0 | WAMAX | WAMAX |
| token1 | 第一版 AMAT | 第三版 AMAT |
| WAMAX 储备 | 历史快照时已提取，为 `0` | `3,022,984.560014677591401242` |
| AMAT 储备 | 历史快照时已提取，为 `0` | `31,161,686.257669564327137259` |
| 价格 | 迁移基准约 `0.097009659 AMAX/AMAT` | 约 `0.097009659 AMAX/AMAT` |
| LP totalSupply | `3.162277660168379331` | `9,695,293.748686652821114957` |
| 部署账号 authorized | 是 | 是 |
| 最终 Owner authorized | 否 | 否 |

## Router

| 参数/状态 | 第一版 | 第三版 |
|---|---|---|
| Owner | `0x990Faf...E3897` | `0x69fedC...0591D` |
| Factory | 第一版 Factory | 第三版 Factory |
| WETH | WAMAX | WAMAX |
| 部署账号 authorized | 是 | 是 |
| 最终 Owner authorized | 否 | 是 |
| 合约余额 | `0` | `0` |

## ProxyAdmin

| 参数/状态 | 第一版 | 第三版 |
|---|---|---|
| Owner | `0x5B2020...baC95` | `0x69fedC...0591D` |
| 管理范围 | 第一版 5 个代理 | 第三版 5 个代理 |
| 合约余额 | `0` | `0` |

## Stake

| 参数/状态 | 第一版 | 第三版 |
|---|---:|---:|
| Owner | `0x5B2020...baC95` | `0x69fedC...0591D` |
| signer | `0xc25Ece...ceAf1` | `0x5f5261...6F4` |
| 手续费接收 | `0x990Faf...E3897` | `0xFE7133...Fa7cB` |
| AMAT/HNS 铸造比例 | `50% / 50%` | `50% / 50%` |
| HNS 参考价格 | `1` | `1` |
| AMAT 参考价格 | 链上 AMM 现货价 | `0.092672702499218719` |
| 价格有效期 priceMaxAge | 无 | `0`，不限制过期 |
| 质押周期步长 | `1,800 秒` | `1,800 秒` |
| 最小质押值 | `1` | `1` |
| needNotPayFee | `false` | `false` |
| AMAT 余额/可用奖励 | `21,850,999.758820357685786015` | `999,999.9994` |
| HNS 余额 | `0` | `0` |
| 原生 AMAX 余额 | `0.1` | `0` |
| 部署账号 Operator | 第一版旧部署账号：是 | 否 |
| 最终 Owner Operator | 否 | 否 |

## Swap

| 参数/状态 | 第一版 | 第三版 |
|---|---:|---:|
| Owner | `0x5B2020...baC95` | `0x69fedC...0591D` |
| 卖出开关 isSellOpen | 开启 | 开启 |
| canSellGlobal | `false` | `false` |
| notBurnGlobal | `false` | `false` |
| is210Now | `false` | `false` |
| sellAmountDaily | `1 AMAT` | `20,000 AMAT` |
| 单日全局卖出上限 | `10,000,000 AMAT` | `10,000,000 AMAT` |
| 单日全局买入上限 | `2,000,000 AMAT` | `2,000,000 AMAT` |
| slip | `10%` | `10%` |
| sellSlip | `6%` | `6%` |
| buyShareSlip | `15%` | `15%` |
| sharePercent | `4%` | `4%` |
| buyGiveMorePercent | `4.5%` | `4.5%` |
| Pair 增加比例 | `20%` | `20%` |
| isIncrease2PairPool | `true` | `true` |
| burnMul | `2` | `2` |
| burnAmountTarget | `97,900,000 AMAT` | `97,900,000 AMAT` |
| burnAmount | `70,052,828.300757400683287947 AMAT` | `70,052,828.330157400683287947 AMAT` |
| 额外 AMAX 接收比例 | `0` | `0` |
| 额外 AMAX 接收地址 | `0x9c95BE...EC7b16` | `0xe0096B...a5b4d` |
| AMAT/HNS/WAMAX/AMAX 余额 | 接近 `0` | 全部 `0` |
| 部署账号 Operator | 第一版旧部署账号：是 | 否 |
| 最终 Owner Operator | 否 | 否 |

## AddLiquidityByAdmin

| 参数/状态 | 第一版 | 第三版 |
|---|---:|---:|
| Owner | `0x5B2020...baC95` | `0x69fedC...0591D` |
| Pair | 第一版 Pair | 第三版 Pair |
| AMAX/WAMAX 最低储备阈值 | `2,000,000 AMAX` | `3,000,000 AMAX` |
| AMAT/HNS/WAMAX/AMAX 余额 | `0` | `0` |
| 部署账号 Operator | 第一版旧部署账号：是 | 否 |
| 最终 Owner Operator | 否 | 是 |

## RewardShare

| 参数/状态 | 第一版 | 第三版 |
|---|---|---|
| Owner | `0x5B2020...baC95` | `0x69fedC...0591D` |
| 75% 接收地址 admin1 | `0x21246a...16588` | `0x93019d...eEac8` |
| 25% 接收地址 admin2 | `0xE369fe...76c51` | `0x25cb73...ff0Dc` |
| token | 零地址，分配原生 AMAX | 零地址，分配原生 AMAX |
| 分配比例 | `75% / 25%` | `75% / 25%` |
| AMAT/HNS/WAMAX/AMAX 余额 | 接近 `0` | 全部 `0` |
| 部署账号 Operator | 第一版旧部署账号：是 | 否 |
| 最终 Owner Operator | 否 | 否 |

## PoolBurn

| 参数/状态 | 第一版 | 第三版 |
|---|---:|---:|
| Owner | `0x990Faf...E3897` | `0x69fedC...0591D` |
| Token | 第一版 AMAT | 第三版 AMAT |
| AMAT 余额 | `53,155,519.111710224091371552` | `53,155,516.891285669621768796` |
| HNS/WAMAX/AMAX 余额 | `0` | `0` |
| 部署账号 Operator | 第一版旧部署账号：是 | 否 |
| 最终 Owner Operator | 否 | 否 |

## 第三版账号配置

| 功能 | 当前地址 | 修改方式 |
|---|---|---|
| 部署账号/当前 Owner | `0x69fedCD10A446F1e277b9aFAe4C371e59A40591D` | 部署脚本；后续由各合约 `transferOwnership()` 转移 |
| 最终 Owner | `0x5B20201ABe1b550F685Fff837f3749AfE21baC95` | 权限和 LP 最终接收账号 |
| AMAT/HNS Emergency | `0x69d29C97ab2C41e882262ab5a51d56c4808d0E0C` | `setEmergency(address)` |
| Stake signer | `0x5f5261D5EE00cf77fff47667846C4Af47F6Cc6F4` | `Stake.setSigner(address)`；同步 Go 签名服务 |
| Stake 手续费接收 | `0xFE713348F8178C646927D3F31ade1A6448cFa7cB` | `Stake.setFeeRev(address)` |
| Swap 额外 AMAX 接收 | `0xe0096BF586D637447860Cc567F755192ddEa5b4d` | `Swap.setMoreTakeOutToAddr(0,address)` |
| RewardShare 75% 接收 | `0x93019dBdBd6eBEd325f6b8D5BBE4faBc41EeEac8` | `RewardShare.set1stAddr(address)` |
| RewardShare 25% 接收 | `0x25cb73F7314d8C318E6DdaeEfd58d418a1aff0Dc` | `RewardShare.set2ndAddr(address)` |

## 待完成权限收尾

- 第三版所有合约 Owner 及 ProxyAdmin Owner 仍是部署账号，尚未转给最终 Owner。
- 部署账号在 Stake、Swap、AddLiquidity、RewardShare、PoolBurn 的 Operator 权限均已移除。
- 部署账号仍有 Pair 和 Router 的 `authorized` 权限；最终 Owner 只有 Router `authorized` 权限。
- LP Token 已转给最终 Owner，仅保留 Pair 创建时永久锁定的最小 LP。

> 项目路径：`/Users/charliejiang/work/contracts/amax-contracts-swap-single-tx-latest`。Go 签名服务需配置第三版 Stake 地址、signer 地址及对应私钥；Owner 私钥不得放入业务后端。
