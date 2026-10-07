# Interpretable ML for CO₂ Adsorption on Biomass-Derived Porous Carbons

Predicting CO₂ uptake (mmol/g) of biomass waste-derived porous carbons from
textural properties, elemental composition, temperature and pressure, using a
performance-weighted (entropy-TOPSIS) ensemble of tree/boosting models.

- **Data:** Yuan et al. (2021), 527 data points collected from peer-reviewed publications
- **Method reference:** Fan et al. (2026), interpretable ensemble ML for CO₂ adsorption (MgO sorbents)
- Scope: this model is trained on porous-carbon data and is **not** an MgO model.

## Folder layout

```
data/raw/        original CSV, never edited
notebooks/       numbered notebooks, run in order
artifacts/       cleaned data, split assignments, configs, saved models
results/         metric tables and figures
```

## Setup

```
pip install -r requirements.txt
jupyter notebook
```

## Roadmap

- [ ] 01 Load and audit: schema, missing values, duplicates, physical sanity checks
- [ ] 02 Clean and split: drop exact duplicate, assign `row_id`, save cleaned data + train/val/test split
- [ ] 03 EDA (train rows only) and baselines (Dummy, Ridge)
- [ ] 04 Compare six models (RF, Extra Trees, GBR, XGBoost, LightGBM, CatBoost) with 5-fold CV
- [ ] 05 Optuna tuning (objective: mean CV RMSE)
- [ ] 06 Entropy-TOPSIS ensemble vs simple average vs best single model
- [ ] 07 Final evaluation on the untouched test set (once)
- [ ] 08 SHAP explanations + export model bundle
- [ ] 09 Streamlit prediction app

## Rules this project follows

1. The raw CSV is never modified.
2. The test set is not looked at (not even in EDA) until notebook 07.
3. Every preprocessing step is fitted on training data only, inside a Pipeline.
