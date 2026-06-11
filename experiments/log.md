# Experiment Log

## EXP001 - LightGBM Baseline

- Features: raw features only
- Model: LightGBM
- Params:
  - n_estimators: 1000
  - learning_rate: 0.05
- Validation:
  - method: train_test_split (20%)
  - stratified: yes
- CV Score: 0.8905518958846678
- Public LB: 0.89163
- Private LB: 0.88923
- Observations:
  - Validation closely matched leaderboard.
  - Baseline validation appears reliable.
- Notes:
  - baseline model working
- Questions to learn:
  - why optimizing logloss ≠ optimizing AUC
  - when to tweak objective
  - when to use custom loss


## EXP002 - Model Understanding and Stratified K-Fold

- Extract feature importance
- Inspect top 20 features
- Look at feature distributions of top features
- Features: raw features only
- Model: LightGBM
- Validation:
  - method: 5-fold stratified CV
- Test Predictions: averaged fold predictions
- Comparisons:
  - EXP001 CV vs EXP002 CV
  - EXP001 LB vs EXP002 LB
- Experimental results:
  - Fold AUCs:
    - 0.892906
    - 0.894271
    - 0.885365
    - 0.891848
    - 0.893381
  - Mean AUC: 0.891554
  - Std AUC: 0.003192
  - OOF AUC: 0.891594
- CV Score: 0.891594
- Public LB: 0.89611
- Private LB: 0.89327
- Observations:
  - OOF and mean AUC almost identical.
  - Validation appears reliable.
  - One weaker fold (Fold 3), but overall model stable.
  - 5-fold ensemble significantly outperformed single model.
  - Gain of ~0.004 private AUC.
  - Averaging predictions reduced variance.


## EXP003 - Row Statistics Features

- Hypothesis: positive and negative examples differ in row-level distribution.
- Features added:
  - row_mean
  - row_std
  - row_min
  - row_max
- Baseline OOF: 0.891594
- New OOF: 0.891727
- Private LB: 0.89324
- Gain vs EXP002: 
  - OOF: +0.000133
  - LB: -0.00003
- Stddev AUC: 0.003140
- Conclusion:
  - Marginal improvement.
  - No strong evidence that row-level aggregates add substantial signal.