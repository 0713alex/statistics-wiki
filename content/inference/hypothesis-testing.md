---
title: "Hypothesis Testing"
description: "H₀、H₁、p-value 與統計決策"
category: "inference"
tags:
  - inference
  - p-value
order: 1
---
# Hypothesis Testing

## 1. Overview
假設檢定（Hypothesis Testing）用樣本證據評估特定母體主張是否與資料相容。常見情境包括比較平均數、比例及判斷變數是否相關。

## 2. Definition
**虛無假設** $H_0$ 通常描述「沒有差異」或「參數等於某值」；**對立假設** $H_1$ 描述希望檢驗的其他可能性。**p-value** 是在 $H_0$ 及檢定模型成立時，觀察到目前或更極端檢定統計量的機率。

## 3. Formula
以已知母體標準差的單樣本 Z 檢定為例：

$$Z=\frac{\bar X-\mu_0}{\sigma/\sqrt n}$$

其中 $\bar X$ 為樣本平均數，$\mu_0$ 為 $H_0$ 指定平均數，$\sigma$ 為已知母體標準差，$n$ 為樣本數。

## 4. Assumptions
- 資料來自適當的抽樣設計，觀測值獨立（或模型正確處理相依性）。
- 上述 Z 檢定假設母體標準差已知，且樣本平均數具有常態或適當近似分布。
- 檢定方法必須符合資料尺度及研究設計。

## 5. Example
**假設性例子：** 一間工廠宣稱產品平均重量為 500 g。抽樣 100 件，平均為 503 g，假設已知 $\sigma=10$ g。檢定 $H_0:\mu=500$ 對 $H_1:\mu\ne500$。

$$Z=\frac{503-500}{10/\sqrt{100}}=3$$

雙尾 p-value 約為 0.0027，因此在顯著水準 0.05 下拒絕 $H_0$。

## 6. Code
以下為可用於上述假設情境的 R 計算示例（非實際執行輸出）：

```r
z <- (503 - 500) / (10 / sqrt(100))
p_value <- 2 * pnorm(-abs(z))
print(p_value)
```

## 7. Interpretation
若 p-value 小於預先設定的 $\alpha$，則拒絕 $H_0$；否則是「未能拒絕」，**不是證明 $H_0$ 正確**。統計顯著不一定代表實務效果很大。

## 8. Common Mistakes
- **錯誤：** p-value 是 $H_0$ 為真的機率。**正確：** 它是在 $H_0$ 成立下衡量資料極端程度的機率。
- **錯誤：** p-value 大於 0.05 表示兩組完全相同。**正確：** 僅表示目前證據不足以拒絕 $H_0$。
