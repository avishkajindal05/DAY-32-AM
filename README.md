# Day 32 | AM Session — Decision Trees & Random Forest
**Week 6 | IIT Gandhinagar — PG Diploma in AI-ML & Agentic AI Engineering**

---

## Assignment Overview

| Field | Detail |
|---|---|
| **Topics** | Gini impurity, entropy, information gain, overfitting & pruning, DT hyperparameters, bagging & bootstrap, feature randomness, RF hyperparameters, feature importance, GridSearchCV, RandomizedSearchCV, cross-validation |
| **Estimated Time** | 60–90 minutes |
| **Submission** | GitHub commit + Jupyter notebook pushed to repo, link in Slack `#daily-standup` |
| **Due** | Next day 09:15 AM |

---

## File Structure

```
D32_AM_DT_RandomForest/
│
├── README.md                          ← This file
│
├── D32_AM_DT_RandomForest.ipynb       ← Main notebook (Parts A, C, D)
│
├── D32_AM_PartB_ExtraTrees.ipynb      ← Part B notebook (Extra Trees)
│
└── extra_trees_comparison.md          ← Part B written analysis
```

---

## Part-wise Breakdown

### Part A — Concept Application (40%)
**File:** `D32_AM_DT_RandomForest.ipynb` → Sections A.1–A.6

| Step | What's done |
|---|---|
| A.1 | Synthetic loan dataset — 2000 records, 6 features (`annual_income`, `credit_score`, `loan_amount`, `employment_years`, `debt_to_income`, `num_credit_cards`), target: `approved` |
| A.2 | Decision Tree (`max_depth=4`) trained; automated top-3 rule extractor function extracts human-readable IF-THEN rules with accuracy & sample coverage |
| A.3 | Random Forest tuned with `RandomizedSearchCV` (30 iterations, 5-fold CV, scoring=`roc_auc`) |
| A.4 | Model comparison: Accuracy, F1-Score, ROC-AUC + bar chart |
| A.5 | Feature importance: MDI (`feature_importances_`) vs Permutation Importance (`sklearn.inspection`) side-by-side |
| A.6 | 1-paragraph bank deployment recommendation |

**Outputs generated:**
- `decision_tree_plot.png`
- `model_comparison.png`
- `feature_importance_comparison.png`

---

### Part B — Stretch Problem (30%)
**Files:** `D32_AM_PartB_ExtraTrees.ipynb` + `extra_trees_comparison.md`

| Step | What's done |
|---|---|
| B.1 | Visual demo: RF exhaustive threshold search vs ET random threshold selection |
| B.2 | Speed benchmark across `n_estimators = [50, 100, 200, 300, 500]` with speedup table |
| B.3 | Full metric comparison (Accuracy, F1, ROC-AUC) + 5-fold CV boxplot |
| B.4 | Feature importance MDI comparison (RF vs ET) |
| Written | `extra_trees_comparison.md` — splitting mechanics, speed analysis, when to use each |

**Outputs generated:**
- `threshold_comparison.png`
- `speed_comparison.png`
- `cv_comparison.png`
- `et_feature_importance.png`

---

### Part C — Interview Ready (20%)
**File:** `D32_AM_DT_RandomForest.ipynb` → Section C

| Question | What's done |
|---|---|
| **Q1 — Conceptual** | Bias-variance tradeoff explained with 3-panel diagram: bias-variance curve, bagging flow (bootstrap → trees → majority vote), error decomposition bar for unpruned DT / DT depth=4 / RF |
| **Q2 — Coding** | `plot_overfitting_curve(X, y, max_depths)` — reusable function, trains DTs at each depth, plots train vs test accuracy, marks optimal depth automatically |
| **Q3 — Debug** | Analysis of RF with identical train=test=0.95: not a problem — well-generalised model with `max_depth=3` regularisation. Reproduced with code + gap calculation |

**Outputs generated:**
- `bias_variance_diagram.png`
- `overfitting_curve.png`

---

### Part D — AI-Augmented Task (10%)
**File:** `D32_AM_DT_RandomForest.ipynb` → Section D

- Full matplotlib infographic: DT vs RF vs Logistic Regression for a non-technical audience
- Each model has: analogy, ★ ratings (Interpretability / Speed / Accuracy), When to Use panel, Pros panel, Cons panel
- Critique section: what the AI-generated visual gets right, what it oversimplifies, and corrections applied

**Output generated:**
- `model_infographic.png`

---

## How to Run

```bash
# 1. Install dependencies (if not already available)
pip install scikit-learn pandas numpy matplotlib scipy

# 2. Run main notebook
jupyter notebook D32_AM_DT_RandomForest.ipynb

# 3. Run Part B notebook
jupyter notebook D32_AM_PartB_ExtraTrees.ipynb
```

> All notebooks use `random_state=42` throughout for reproducibility.  
> Run cells top-to-bottom in order — no hidden state dependencies.

---

## Key Concepts Demonstrated

| Concept | Where |
|---|---|
| Gini impurity / entropy | DT training, Part A.2 |
| Overfitting & pruning | `max_depth` comparison, Part C Q2 |
| Bagging & bootstrap | RF training, C Q1 diagram |
| Feature randomness | ET vs RF splitting, Part B.1 |
| RandomizedSearchCV | Part A.3 |
| Cross-validation (5-fold) | Part A.3, Part B.3 |
| Permutation importance | Part A.5 |
| Bias-variance tradeoff | Part C Q1 |

---

## Model Results Summary

| Model | Accuracy | F1 | ROC-AUC | Interpretability |
|---|---|---|---|---|
| Decision Tree (depth=4) | ~0.91 | ~0.91 | ~0.94 | ★★★★★ |
| Random Forest (tuned) | ~0.93 | ~0.93 | ~0.97 | ★★☆☆☆ |
| Extra Trees (default) | ~0.93 | ~0.92 | ~0.97 | ★★☆☆☆ |

*Exact values vary slightly with random seed and hardware.*

---

*Day 32 | AM Session | IIT Gandhinagar — AI-ML & Agentic AI Engineering*
