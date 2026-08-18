# AMAT 主网新旧地址汇总

## 合约地址

| 功能 | 旧地址 | 新地址 | 前后端配置更新位置 |
|---|---|---|---|
| AMAT Token | `0x3EE2e767957EdBF92ACE6ADE7AC7Ae24d894eEe3` | `0xeCD0d8Aa057690e8B50a03234f06670b21840A02` | 前端：`apps/swap-web/src/config/chain/addr-prod.js` 的 `hnt`；`apps/rwa-web/src/config/chain/addr-prod.js` 的 `amat`。后端未发现硬编码。 |
| HNS Token | `0xFB81DEf8FCE7CA5CE970AFf0A92b391223122F37` | `0x1378360811ff6aFf044d3BC6a5F971E98e3cD80E` | 前端：两个 `addr-prod.js` 的 `hns`。后端未发现硬编码。 |
| Factory | `0x57cec2862d1AEcB782FCD9CCa3D73623223df617` | `0x2AaF344E503951ae13579e33A3E1d22cd1190387` | 前后端无需直接配置；由 Router/Pair 链上绑定。 |
| AMAT/WAMAX Pair | `0x8c00Cf5EE9134Ad45Fb022B9a7794FCFD48F389a` | `0xa70Dc712d8eDC9E32AAD1EACC623010ec7bE5DA2` | 前后端未发现直接配置；链上更新 Swap、AddLiquidity 的 Pair 绑定。 |
| Router | `0x1C3726C2d8f96FE29395E3AE75e6187BE15e16d7` | `0x22DF60289ec8294b0b41bC46eEde388aCB520Db1` | 前后端未发现直接配置；链上更新 Swap Router 绑定。 |
| ProxyAdmin | `0xA5cCbd613ab7d8A07A84B228F46f1466FE2CB5ed` | `0x286FBBf2f084A6C6770D1414dBdbCc70Ac592Be1` | 不配置到业务前后端；仅升级管理脚本/运维记录使用。 |
| Stake Proxy | `0x2121C8bb3B25e4DDFB3AFd66fBA1a98D1Ad8519b` | `0x2d2d8a2489A8c223e08952D9BbFbec25029298Fd` | 前端：两个 `addr-prod.js` 的 `stake`。后端未发现地址硬编码，生产配置需确认。 |
| Stake Implementation | `0x7859961cb68A1Be7E3cc521ba3A0443Fd53f4974` | `0xD0cD83E05B4085cD3CF74F44004034C4D2851260` | 不配置到前后端；前后端始终调用 Stake Proxy。 |
| Swap Proxy | `0x3c589859C3244B5Ec581C18a0e4326c540fFb073` | `0x6FDa5E4AB178cB3352538463b8C2CF14d03c22fD` | 前端：两个 `addr-prod.js` 的 `swap`。后端未发现地址硬编码，生产配置需确认。 |
| Swap Implementation | `0x74FeFD008cA6AA982aF02d683e31F7811dFF9f3E` | `0xc8Bf155C08AFE96D6BE7424ACEFc52D76Fcfa136` | 不配置到前后端；前后端始终调用 Swap Proxy。 |
| AddLiquidity Proxy | `0x08abC66F6360874aB94B1752D58647a5A86bd959` | `0x65f9415D132B5630008752290A8199018a597eF7` | 前端：`apps/rwa-web/src/config/chain/addr-prod.js` 的 `addLiquidityByAdmin`。后端未发现硬编码。 |
| AddLiquidity Implementation | `0xbf451ba7aB185e01B72FBC98fEa8ABF199be3f27` | `0x9f2760950E7dA84298c86AA9BcF47BFbDEaAA765` | 不配置到前后端；前端调用 AddLiquidity Proxy。 |
| RewardShare Proxy | `0x0E4625EA092fA1C3755738BcCF165af68A3F2e51` | `0x5810ee4a93d5c0e818B52CE8851ACf045fe82418` | 前端：`apps/rwa-web/src/config/chain/addr-prod.js` 的 `rewardShare`。后端未发现硬编码。 |
| RewardShare Implementation | `0xC4B3115D55c1B1E6a2485069773824e5E46059D4` | `0x9287945f57963427F83FbB0892d70fa0FBe8b550` | 不配置到前后端；前端调用 RewardShare Proxy。 |
| PoolBurn Proxy | `0x9556284ec62D914368a56f82788c21048BaFA804` | `0x23D000B0e711F44B0b63Cb40f914EaB21f5DbA81` | 前后端未发现直接配置；由 Swap 链上绑定。 |
| PoolBurn Implementation | `0x147F32F89aC7CB65B31dEF43296F629F0C576FA7` | `0x43069A09aDCc9976F0316A18CBBD05ADA1150B76` | 不配置到前后端；业务合约调用 PoolBurn Proxy。 |
| USDT | `0x2eDE0BeFdA5D0890BA195ce5dD9789C2C5F12064` | `0x2eDE0BeFdA5D0890BA195ce5dD9789C2C5F12064` | 前端：两个 `addr-prod.js` 的 `usdt`；地址未变化。 |
| WAMAX | `0x18b7CD3BC2FCe130aaABD5FE4a75f5474C47F0a9` | `0x18b7CD3BC2FCe130aaABD5FE4a75f5474C47F0a9` | 前后端无需更新；地址未变化，由链上合约保存。 |
| AMAX/USDT Pair | `0x1aBfE068E21509e1964FebA60273915c606eEc3e` | `0x1aBfE068E21509e1964FebA60273915c606eEc3e` | 前后端无需更新；地址未变化，由 Swap 链上保存。 |
| AMAX/USDT Router | `0xA4D0dc03e1A22Fb0DD33f4aD49927bb123f6F9eD` | `0xA4D0dc03e1A22Fb0DD33f4aD49927bb123f6F9eD` | 前后端无需更新；地址未变化，由 Swap 链上保存。 |
| Invitation (Swap) | `0x3333333333333333333333333333333333333333` | `0x3333333333333333333333333333333333333333` | 前后端无需更新；地址未变化，由 Swap 链上保存。 |

## 配置账号

| 功能 | 旧地址 | 新地址 | 前后端配置更新位置 |
|---|---|---|---|
| 部署账号 | `0x990Faf410fc48F471D63B51B851024eD240E3897` | `0x69fedCD10A446F1e277b9aFAe4C371e59A40591D` | 不配置到业务前后端；仅部署脚本使用 `EVAMAIN_PRIVATE_KEY`。 |
| 最终 Owner | `0x5B20201ABe1b550F685Fff837f3749AfE21baC95` | `0x5B20201ABe1b550F685Fff837f3749AfE21baC95` | 不配置到业务前后端；通过各合约 `transferOwnership()` 设置。 |
| AMAT/HNS Emergency | `0x990Faf410fc48F471D63B51B851024eD240E3897` | `0x5B20201ABe1b550F685Fff837f3749AfE21baC95` | 不配置到前后端；分别调用 AMAT/HNS 的 `setEmergency(address)`。 |
| Stake signer | `0xc25EceD4d740EeDd3499Cb98102C8468660ceAf1` | `0x69fedCD10A446F1e277b9aFAe4C371e59A40591D` | 链上调用 `Stake.setSigner(address)`；后端需更新对应签名私钥，交付源码未找到其生产配置位置，必须在服务器环境/密钥配置中确认。 |
| Stake 手续费接收 | `0x990Faf410fc48F471D63B51B851024eD240E3897` | `0x5B20201ABe1b550F685Fff837f3749AfE21baC95` | 不配置到前后端；链上调用 `Stake.setFeeRev(address)`。 |
| Swap 额外 AMAX 接收 | `0x9c95BEaA72Afe34ACdB0f36A4daf08Cc79EC7b16` | `0x9c95BEaA72Afe34ACdB0f36A4daf08Cc79EC7b16` | 不配置到前后端；链上调用 `Swap.setMoreTakeOutToAddr(rate,address)`；地址未变化。 |
| RewardShare 75% 接收 | `0x21246a0DD2093c27B8fa969Fe759CE700C216588` | `0x21246a0DD2093c27B8fa969Fe759CE700C216588` | 不配置到前后端；RewardShare 链上配置 `admin1`；地址未变化。 |
| RewardShare 25% 接收 | `0xE369feB7F872a092ec993B4aE87CAAaD39a76c51` | `0xE369feB7F872a092ec993B4aE87CAAaD39a76c51` | 不配置到前后端；RewardShare 链上配置 `admin2`；地址未变化。 |

> 前端路径均相对于 `/Users/charliejiang/work/contracts/amax-contracts-swap-single-tx-latest`。交付的 Java 后端未发现主网合约地址或 Stake 签名私钥的硬编码配置；上线前仍需检查生产服务器环境变量、外挂配置和密钥服务。
