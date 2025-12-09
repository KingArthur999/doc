下面帮你整理了 **Uniswap（V2/V3 通用）常见错误信息（message）+ 对应中文提示 + 出错原因总结**
非常适合前端判断、用户提示、钱包报错解析。

---

# ✅ **💥 Uniswap 常见报错全集（最全版本，前端可直接用）**

以下报错均来自主流 DEX（UniswapV2、V3、Pancake、SushiSwap、Router 合约）。

---

# 🟦 **一、滑点 / 路径 / 价格相关**

---

## 1️⃣ `UniswapV2Router: INSUFFICIENT_OUTPUT_AMOUNT`

**中文提示：滑点太低（实际得到的代币数量达不到你的最低要求）**
**原因：**

* 你设置的 `amountOutMin` 太小
* 价格变化导致滑点不足
* 税币导致输出变少

---

## 2️⃣ `UniswapV2Router: EXCESSIVE_INPUT_AMOUNT`

**中文提示：输入数量超出预期（滑点太低）**
**原因：**

* 你设置的 `amountInMax` 太小
* 实际需要的输入比你愿意支付的更多

---

## 3️⃣ `UniswapV2Router: INSUFFICIENT_A_AMOUNT / INSUFFICIENT_B_AMOUNT`

**中文提示：添加流动性时数量不足**
**原因：**

* 添加 LP 时你的 A 或 B 代币数量太低
* LP 完全不平衡
* A/B 比例错误

---

## 4️⃣ `"K"` / `"UniswapV2: K"`

**中文提示：无效的价格或内部错误（恒定乘积不成立）**
**原因：**

* 某个 token **Transfer 税导致输出不匹配**
* 你转入的数量不等于实际入池数量
* Token 有 fee、burn 或反射功能

---

## 5️⃣ `UniswapV2: INSUFFICIENT_LIQUIDITY`

**中文提示：流动性不足**
**原因：**

* 交易金额超过池子实际储备
* Token 刚上线，池子太小

---

## 6️⃣ `UniswapV2: INSUFFICIENT_INPUT_AMOUNT`

**中文提示：输入数量太小（小于 1 wei）**
**原因：**

* 小额交易被截断
* amountIn 太低

---

# 🟩 **二、授权 / 余额 / Token 本身相关**

---

## 7️⃣ `TRANSFER_FROM_FAILED`

**中文提示：授权不足 或 Token 不标准**
**原因：**

* 用户没有 `approve()`
* 某些代币 transferFrom 返回 false
* 某些奇葩币不符合 ERC20

---

## 8️⃣ `ERC20: transfer amount exceeds balance`

**中文提示：余额不足**
**原因：**

* 用户余额不足
* 合约 transfer 时余额不够

---

## 9️⃣ `ERC20: insufficient allowance`

**中文提示：授权不足**
**原因：**

* approve 数量 < swap 所需数量

---

## 🔟 `ERC20: transfer to the zero address`

**中文提示：目标地址无效**
**原因：**

* 部分税币拒绝向 0 地址转账
* 代币内部检查失败

---

# 🟧 **三、路由器 / Pair / 合约调用问题**

---

## 1️⃣1️⃣ `PancakeRouter: EXPIRED`

**中文提示：交易过期（deadline 过期）**
**原因：**

* 你设置的 `deadline < 当前时间`

---

## 1️⃣2️⃣ `TRANSFER_FAILED`

**中文提示：代币 transfer 失败**
**原因：**

* token 的 transfer 返回 false
* token 是 honeypot
* token 有手续费导致不兼容

---

## 1️⃣3️⃣ `Call to non-contract`

**中文提示：调用的不是合约地址**
**原因：**

* Pair 没有创建
* Router 地址写错
* 自建链上 factory 不匹配

---

## 1️⃣4️⃣ `execution reverted`

**中文提示：合约主动回滚（通用错误）**
**原因：非常多**
例如：

* owner 限制
* paused
* 自定义 require

---

# 🟥 **四、流动性池 Pair 相关**

---

## 1️⃣5️⃣ `UniswapV2: INSUFFICIENT_LIQUIDITY_MINTED`

**中文提示：铸造 LP 时收到的 LP 数量不足**
**原因：**

* 你添加的 token 数太少
* 池子最小流动性过高

---

## 1️⃣6️⃣ `UniswapV2: INSUFFICIENT_LIQUIDITY_BURNED`

**中文提示：移除 LP 时收到的数量太少**
**原因：**

* LP 数量不足
* 池子流动性太小

---

# 🟪 **五、自定义税币（fee/onTransfer）专用报错**

---

## 1️⃣7️⃣ `TransferHelper: TRANSFER_FROM_FAILED`

**中文提示：可能是税币，transferFrom 不符合标准**
**原因：**

* Token 内部扣税，导致 router 收到的数量不对
* Fee-on-transfer 代币必须使用支持的路由版本

---

## 1️⃣8️⃣ 条件自带的 revert，例如：

```
"transfer buy status error"
"transfer sell status error"
"error"
```

**中文提示：代币内部逻辑拒绝交易**
**原因：**

* tradeStatus = 0
* 未开放交易
* 地址不在白名单
* 合约限制买卖

👉 **这类报错来自你自己的 ACCA 合约里的 require。**

---

# 🔥 **六、前端可用的判断模板（建议收藏）**

```js
function parseSwapError(error) {
    const msg = error?.data?.message || error?.message || "";

    if (msg.includes("INSUFFICIENT_OUTPUT_AMOUNT"))
        return "滑点太低，请提高滑点";

    if (msg.includes("EXCESSIVE_INPUT_AMOUNT"))
        return "滑点太低，请提高滑点";

    if (msg.includes("INSUFFICIENT_LIQUIDITY"))
        return "流动性不足";

    if (msg.includes("K"))
        return "代币带税或价格错误";

    if (msg.includes("insufficient allowance"))
        return "授权额度不足";

    if (msg.includes("transfer amount exceeds balance"))
        return "余额不足";

    if (msg.includes("TRANSFER_FROM_FAILED"))
        return "授权不足或币不标准";

    if (msg.includes("EXPIRED"))
        return "交易已过期，请重新发起";

    if (msg.includes("trade status error"))
        return "合约未开启交易";

    return "交易失败，请检查交易参数";
}
```

---

# 📘 如果你愿意，我还能帮你：

✔ 整理适配你自家链 EVA 的 Router/Pairs 错误分析
✔ 为你写一个“万能 Swap 错误翻译器”
✔ 为你的前端写一段可复用的错误捕获模块

你需要进一步增强前端吗？
