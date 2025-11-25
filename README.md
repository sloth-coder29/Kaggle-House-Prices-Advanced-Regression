# Kaggle - House Prices: Advanced Regression Techniques

## 專案介紹
本專案參與 Kaggle 房價預測競賽，透過資料前處理、特徵工程以及 Stacking Ensemble（ElasticNet + LightGBM + XGBoost）進行回歸分析，成功達成高準確度預測。

| 指標 | 分數 |
|------|------|
| Public LB (RMSLE) | **0.122** |
| 模型架構 | ElasticNet + LightGBM + XGBoost（Stacking） |
| 特徵工程 | 偏態修正、缺值處理、One-Hot Encoding |

---

## 專案流程
```text
資料讀取與清理
       ↓
特徵工程（偏態修正、缺值填補 → One-Hot Encoding）
       ↓
個別模型訓練（ElasticNet / LightGBM / XGBoost）
       ↓
Stacking Ensemble
       ↓
Cross Validation → RMSLE 評估

