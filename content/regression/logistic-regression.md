---
title: "Logistic Regression"
description: "二元反應變數、Odds Ratio 與 SAS"
category: "regression"
tags:
  - regression
  - odds-ratio
order: 1
---
# Logistic Regression

## 1. Overview
Logistic Regression（羅吉斯迴歸）用於建模二元反應變數，例如是否罹病、是否通過考試。它透過 logit 連結將事件機率與解釋變數關聯起來。

## 2. Definition
令 $Y\in\{0,1\}$，$p=P(Y=1\mid X)$。勝算（odds）為 $p/(1-p)$，**Odds Ratio（OR）** 比較兩組的勝算。

## 3. Formula
$$\log\left(\frac{p}{1-p}\right)=\beta_0+\beta_1 X$$

$\beta_0$ 是截距，$\beta_1$ 是 $X$ 每增加一單位的 log-odds 變化；在其他條件不變時，$e^{\beta_1}$ 為對應 OR。

## 4. Assumptions
- 反應變數為二元，且事件編碼清楚。
- 觀測值獨立，或採用能處理群聚的模型。
- 連續解釋變數與 logit 的關係需適當建模，不要求機率與 $X$ 呈線性。
- 避免完全分離與嚴重多重共線性。

## 5. Example
**假設性例子：** 研究每週運動時數 $X$ 與是否達到某健康目標 $Y$ 的關係。假設估計 $\hat\beta_1=0.4$，則每多一小時運動，估計勝算乘以 $e^{0.4}\approx1.49$，不代表機率直接增加 49%。

## 6. Code
SAS 範例（假設資料集 `example` 有 `Y` 與 `X` 欄位）：

```sas
proc logistic data=example;
    model Y(event='1') = X;
run;
```

`event='1'` 明確指定要建模的事件。這段程式碼是教學示例，未宣稱已執行。

## 7. Interpretation
SAS 的 **Parameter Estimates** 顯示係數及其檢定；**Odds Ratio Estimates** 顯示 OR 與信賴區間。若 $OR>1$，代表 $X$ 增加與事件勝算增加相關；仍須結合信賴區間與研究設計，不可直接推論因果。

## 8. Common Mistakes
- **錯誤：** OR=1.5 表示事件機率增加 50%。**正確：** 是勝算乘以 1.5，機率變化取決於基準機率。
- **錯誤：** 係數為正代表因果效果。**正確：** 迴歸係數本身只描述條件關聯，因果解釋需要額外假設。
