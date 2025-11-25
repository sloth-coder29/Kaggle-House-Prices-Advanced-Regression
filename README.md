# Kaggle - House Prices: Advanced Regression Techniques 

本專案參與 Kaggle 房價預測競賽，透過多種模型與特徵處理技術，預測房屋最終成交價格。針對 **高維度特徵與數據偏態問題** 進行優化，並運用 **Stacking Ensemble（ElasticNet + LightGBM + XGBoost → RidgeCV）** 提升預測準確度。

---

## 專案內容

- 目標：利用房屋相關特徵（建築年份、材質、面積等）預測最終成交價  
- 資料挑戰：
  - 特徵高度多元（類別 + 數值）
  - 嚴重的偏態分布（skewness）
  - 高維度空間中模型表現不穩定  
- 解決策略：結合特徵工程、模型融合（Stacking）、偏態修正與視覺化誤差分析

---

##  方法應用與模型設計

###  1. 特徵處理
| 類型 | 方法 |
|------|------|
| 數值特徵 | 以中位數填補缺失值 |
| 類別特徵 | 以眾數填補，後續進行 One-Hot 編碼 (`OneHotEncoder`) |
| 偏態修正 | `Yeo-Johnson Transformer` 轉換 |

---

###  2. 模型建構

| 模型 | 說明 |
|------|------|
| ElasticNet | 線性模型，結合 L1 + L2 正則化 |
| LightGBM | 快速梯度提升樹，用於高維特徵 |
| XGBoost | 強大但較重模型，用於複雜關係捕捉 |

---

###  3. 模型融合（Stacking Ensemble）

- 使用 **K-Fold Cross Validation** 建立 **Out-of-Fold (OOF) meta-features**
- Meta-model：`RidgeCV`（嶺迴歸交叉驗證）
- 提升模型穩定性與泛化能力

---

###  4. 模型監控與評估
- 使用 **Residual Plot（殘差圖）** 觀察各模型的預測誤差分布  
- 評估模型是否在特定區域過度或不足預測

---

## 成果表現

| 指標 | 成果 |
|------|------|
| 單模型 RMSE(log) | `0.11 ~ 0.18` |
| Stacking OOF CV RMSE | **`0.12373 ± 0.02034`** |
| Kaggle Public LB RMSLE |  **`0.12240`**（排行榜前段） |

---


