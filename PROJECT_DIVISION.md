# Project Dependency Structure for 3-Student Division

```
┌─────────────────────────────────────────────────────────────────┐
│                    PHASE 1: Visualization                       │
│              (Data Loading & Exploratory Analysis)              │
│                                                                 │
│  - Load train.csv, test.csv, store.csv                         │
│  - Exploratory Data Analysis (EDA)                             │
│  - Correlation heatmaps                                        │
│  - Sales trends by store/holiday/promo                         │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│                    PHASE 2: Feature Engineering                 │
│              (Data Preparation & Transformation)                │
│                                                                 │
│  - Merge sales + store tables                                  │
│  - Create temporal features (day, month, week)                 │
│  - Lag features & moving averages                              │
│  - Fourier features for seasonality                            │
│  - Handle missing data & normalization                         │
│  - Train/Val/Test split (time-aware)                           │
└────────┬────────────────────────────────────────────┬───────────┘
         │                                            │
         ▼                                            ▼
    ┌─────────────────────┐              ┌──────────────────────┐
    │  PHASE 3: Models    │              │  PHASE 4: Advanced   │
    │  (Regression)       │              │  (Classification &   │
    │                     │              │   Uncertainty)       │
    │ - Baseline (linear) │              │                      │
    │ - XGBoost/LightGBM  │              │ - Multi-step         │
    │ - Hyperparameter    │              │   forecasting        │
    │   tuning            │              │ - Quantile           │
    │ - SHAP analysis     │              │   regression         │
    │ - Error analysis    │              │ - 3-class classifier │
    │                     │              │ - ROC-AUC & F1       │
    └──────────┬──────────┘              └──────────┬───────────┘
               │                                    │
               └────────────────┬───────────────────┘
                                ▼
                    ┌──────────────────────────┐
                    │   PHASE 5: Deep Models   │
                    │  (LSTM, TCN, Optuna)     │
                    │                          │
                    │ - LSTM/TCN architecture  │
                    │ - Hyperparameter search  │
                    │ - Full uncertainty       │
                    │ - SHAP interpretation    │
                    └──────────┬───────────────┘
                               ▼
                    ┌──────────────────────────┐
                    │  PHASE 6: Final Report   │
                    │  (Documentation)         │
                    │                          │
                    │ - Combine all results    │
                    │ - Comparison metrics     │
                    │ - Visualizations         │
                    │ - Conclusions            │
                    └──────────────────────────┘
```

---

## **Recommended 3-Student Division**

### **👤 Student 1: Data & Feature Engineering Lead**
**Phases:** 1 → 2 (foundational)

**Tasks:**
- Load and explore all three CSV files
- Create visualizations (trends, correlations, distributions)
- Merge train + store data
- Engineer temporal features (day/month/week/year)
- Create lag features (Sales_t-1, Sales_t-7, etc.)
- Compute moving averages (7-day, 30-day)
- Handle missing values & outliers
- Normalize/scale data
- Create train/validation/test splits
- **Deliverable:** Clean `processed_data.csv` + feature documentation

**Dependencies:** None (starting point)
**Blocks:** Students 2 & 3 until features are ready

---

### **👤 Student 2: Classical ML Models & Analysis**
**Phases:** 3 (depends on Phase 2)

**Tasks:**
- Load processed features from Student 1
- Implement baseline models (linear regression, moving average)
- Train XGBoost & LightGBM with hyperparameter tuning
- Implement store-aware cross-validation
- Calculate RMSE/MAE/R² on validation set
- Perform SHAP feature importance analysis
- Error analysis (identify worst predictions)
- Compare model performances
- **Deliverable:** Trained models + `predictions_val.csv` + analysis report

**Dependencies:** 
- ✅ Requires Phase 2 output (features)
- ✅ Can work independently of Student 3

---

### **👤 Student 3: Advanced Methods & Uncertainty**
**Phases:** 4 → 5 (depends on Phase 2, can benefit from Phase 3)

**Tasks:**
- Load processed features from Student 1
- Implement multi-step forecasting (7-day ahead)
- Build quantile regression for uncertainty bounds
- Implement 3-class sales classifier (low/medium/high)
- Calculate classification metrics (ROC-AUC, F1)
- Build LSTM model for sequence forecasting
- Build TCN model (temporal convolutional)
- Hyperparameter optimization with Optuna
- Integrate SHAP for deep model interpretation
- **Deliverable:** Advanced models + uncertainty estimates + `predictions_test.csv`

**Dependencies:**
- ✅ Requires Phase 2 output (features)
- ✅ Optional: Can reference Student 2's SHAP insights for comparison

---

## **Communication Points**

| Milestone | What Student 1 Delivers | What Student 2 Needs | What Student 3 Needs |
|-----------|------------------------|----------------------|----------------------|
| **Week 1** | EDA report + feature list | ✓ Ready | ✓ Ready |
| **Week 2** | `processed_data.csv` | ✓ Start training | ✓ Start building |
| **Week 3** | Feature importance suggestions | Can refine features | Can refine features |
| **Week 4** | Final feature set | Finalize models | Finalize models |
| **Week 5** | - | Deliver predictions + metrics | Deliver predictions + uncertainty |
| **Week 6** | - | - | Final report <br> (compile all results) |

---

## **Risk Mitigation**

⚠️ **If Student 1 is delayed:** Students 2 & 3 can start with raw data + simple features
⚠️ **If Student 2 is delayed:** doesn't affect Student 3
⚠️ **If Student 3 is delayed:** Student 2's models can serve as backup
✅ **Best practice:** Share processed data early, even if not 100% finalized
