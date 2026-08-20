# AMAT 测试链合约信息

## 网络信息

| 项目 | 配置 |
|---|---|
| 网络名称 | `evatest` |
| RPC | `https://tntrpc.evascan.io/` |
| Chain ID | `12248` |
| 浏览器 | [testnet.evascan.io](https://testnet.evascan.io) |
| 原生币 | `AMAX` |
| 部署状态 | `complete` |

## 合约地址

| 功能 | 测试链地址 | 说明 |
|---|---|---|
| AMAT Token | `0xddedEeFaEfa0D1280DB56E9149c3d8dbE5C0Ab5B` | 测试链 AMAT |
| HNS Token | `0x3E1f914E07271F5Cd4B65350dcE0f8406Ef3E1Ba` | 测试链 HNS |
| Invitation | `0x937554D40deD459c7dafD4525ade8A5a8C75B5a4` | 邀请关系合约 |
| Factory | `0x3a7Ac6BE583058E75d665964485a4643A812ddD9` | AMAT/WAMAX Factory |
| AMAT/WAMAX Pair | `0x59d290f7659e1bf0ca58D480663447d9515454f6` | 测试链流动性池 |
| Router | `0x3d5202157bB3046cB37334b7d36860e23a0a29c1` | AMAT/WAMAX Router |
| ProxyAdmin | `0x0A2038D030Fe87c1BEC5FDb49B9c26858b25da1D` | 升级代理管理 |
| Stake Proxy | `0x651af62fB34Cf322f0B72Ac5d690Db655d30f74B` | 质押业务入口 |
| Stake Implementation | `0x1F9FBd6B8EB01eC54ec8319288Ec5B76D912d23C` | Stake 实现合约 |
| Swap Proxy | `0x2d0B048b2c869AC4cEEfEed8a2aD28bb25fC0c05` | 兑换业务入口 |
| Swap Implementation | `0xcBFbcB02eFD17402dB218033658654bD0de7c0F7` | Swap 实现合约 |
| AddLiquidityByAdmin Proxy | `0x473886e8dE7b85D8590E9BB976E125379A60d551` | 管理员添加流动性 |
| AddLiquidityByAdmin Implementation | `0x7A517495861521b89a3Eb3DcEb26749fc2f5d6A5` | AddLiquidity 实现合约 |
| RewardShare Proxy | `0x1C5fC87bC90f73fD85868e356C04E1266f1d62A5` | 分润业务入口 |
| RewardShare Implementation | `0x403cD983211384AB9ce9C3BFacCf183282d34C8C` | RewardShare 实现合约 |
| PoolBurn Proxy | `0xA117a533E14B41B015d739FD9cF85Ee7d9a9333c` | AMAT 销毁业务入口 |
| PoolBurn Implementation | `0x58D394C52BAcbF37c0AcbF76Ed4B9F3fC1348BBA` | PoolBurn 实现合约 |

## 外部沿用合约

| 功能 | 测试链地址 |
|---|---|
| USDT | `0x44fe1AB958095a877029352E45E6F097c62A10dd` |
| WAMAX | `0xF79112A9FDcaf145DC251B9047dFAd7D6f6527a3` |
| AMAX/USDT Factory | `0xcdE6510cE5ddf2F2Cf0eF873eA2FA6C728B8DE04` |
| AMAX/USDT Router | `0xfb36CB76e06027830C9241FF4aE2Da1387d1A97a` |
| AMAX/USDT Pair | `0xAedb33012E62c67C4179E07431BB06fA9Ea0cE31` |

## 测试部署参数

原始单位均按合约 decimals 保存：

| 参数 | 数值 |
|---|---:|
| 添加流动性 AMAT | `10,000 AMAT` |
| 添加流动性 WAMAX | `0.5 WAMAX` |
| PoolBurn AMAT | `20,000,000 AMAT` |
| Stake AMAT | `20,000,000 AMAT` |
| 测试买入 USDT | `1 USDT` |
| 测试卖出 AMAT | `0.1 AMAT` |
| 最低 Gas 余额 | `0.5 AMAX` |

## 测试范围

本次测试链部署覆盖：

- AMAT/HNS Token 部署与初始化；
- Factory 创建 AMAT/WAMAX Pair；
- Router 与 Pair 授权配置；
- Stake、Swap、AddLiquidityByAdmin、RewardShare、PoolBurn 代理及实现合约部署；
- Stake、Swap、PoolBurn 的合约间授权；
- 测试流动性、买入、卖出及销毁流程。

## 地址来源

以上地址来自部署记录：

`deployments/evatest-12248.json`

浏览器查询地址格式：

`https://testnet.evascan.io/address/<合约地址>`
