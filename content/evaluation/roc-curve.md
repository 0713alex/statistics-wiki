---
title: "ROC Curve & AUC"
description: "Sensitivity、Specificity 與分類評估"
category: "evaluation"
tags:
  - evaluation
  - classification
order: 1
---
# ROC Curve & AUC

## 1. Overview
ROC（Receiver Operating Characteristic）曲線描述分類器在不同閾值下的敏感度與偽陽性率之間的取捨。AUC 用單一數值概括排序辨識能力。

## 2. Definition
**Sensitivity（敏感度）** 是真正陽性中被正確預測的比例；**Specificity（特異度）** 是真正陰性中被正確預測的比例。ROC 橫軸為 $1-\text{Specificity}$，縱軸為 Sensitivity。

## 3. Formula
$$\text{Sensitivity}=\frac{TP}{TP+FN}$$

$$\text{Specificity}=\frac{TN}{TN+FP}$$

$TP$、$TN$、$FP$、$FN$ 分別是真陽性、真陰性、偽陽性與偽陰性。AUC 是 ROC 曲線下的面積。

## 4. Assumptions
- 有可信的實際類別標籤及可排序的預測分數。
- 評估資料應盡量獨立於模型訓練資料。
- AUC 不直接反映預測機率是否校準良好；類別極不平衡時也可考慮 PR 曲線。

## 5. Example
**假設性例子：** 某模型在閾值 0.5 時有 $TP=40$、$FN=10$、$TN=35$、$FP=15$。因此 Sensitivity = 0.80、Specificity = 0.70、偽陽性率 = 0.30。這只是 ROC 上的一個點，**不能由單一點算出完整 AUC**。

## 6. Code
R 範例（假設 `truth` 為 0/1 標籤、`score` 為預測機率）：

```r
library(pROC)
roc_obj <- roc(response = truth, predictor = score,
               levels = c(0, 1), direction = '<')
plot(roc_obj)
auc(roc_obj)
```

此處為程式碼範例，未提供或宣稱真實執行結果。

## 7. Interpretation
AUC 越接近 1，通常代表正負類別的排序區分能力越好；0.5 近似隨機排序。實際選擇閾值時，需考慮漏判與誤判的成本，不應只看 AUC。

## 8. Common Mistakes
- **錯誤：** AUC=0.9 代表準確率 90%。**正確：** AUC 與特定閾值下的 Accuracy 是不同指標。
- **錯誤：** ROC 曲線越好，預測機率一定越準。**正確：** ROC/AUC 評估辨識排序能力，不直接衡量校準程度。
