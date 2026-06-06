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


## EXP002 - Model Understanding
  - Extract feature importance
  - Inspect top 20 features
  - Look at feature distributions of top features