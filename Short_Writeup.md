
---


# Marketing Mix Modeling – Executive Summary

This project builds a machine learning model to **explain and forecast revenue** using weekly marketing and business driver data.

---

## 1. Data Preparation
- **Trend & Seasonality**: Explicit week indices and `weekofyear` variables capture seasonal effects.  
- **Zero-Spend Periods**: Retained to preserve causal interpretability.  
- **Missing Values**: Imputed with 0 for media spends; median or forward-fill for others.  
- **Scaling**: Standardization applied prior to regularized regression.  

---

## 2. Modeling Approach
- **ElasticNet Regression** chosen as the core model:  
  - Handles collinearity across marketing channels.  
  - Provides interpretable coefficients (elasticities, promo lift).  
- Hyperparameters tuned with **Bayesian Optimization (Optuna)**.  
- Validation via **blocked TimeSeriesSplit** ensures no look-ahead bias.  

---

## 3. Causal Framing
- **Mediator assumption**: Social/display (Facebook, TikTok, Snapchat, Instagram) stimulate search intent → drives **Google spend** → impacts revenue.  
- A two-stage approach was implemented: Google spend first modeled from social, then included as a predictor for revenue.  
- Back-door paths and post-outcome leakage avoided.  

---

## 4. Diagnostics
- Out-of-sample performance: **RMSE** and **MAPE** reported.  
- Residual analysis confirmed no severe autocorrelation.  
- Rolling-window coefficient checks demonstrated stability over time.  
- Sensitivity tests on `average_price` and `promotions` show product lever impacts.  
- Trade-off plots illustrate **price vs demand** and **Google vs Facebook allocation boundaries**.  

---

## 5. Insights & Recommendations
- **Price elasticity**: Higher `average_price` reduces revenue.  
- **Promotions**: Significant positive lift on weekly revenue.  
- **Media impact**: Google and Facebook are dominant channels, with social channels indirectly boosting Google.  
- **Decision boundaries**:  
  - Beyond certain levels, additional Google spend shows diminishing returns.  
  - Trade-off plots suggest reallocating marginal budget from social to Google can increase efficiency.  

---

## 6. Risks & Caveats
- Collinearity reduced but not eliminated; overlapping campaigns remain a challenge.  
- Mediation is modeled, but unobserved confounders (e.g., brand equity) may bias results.  
- Assumes trend/seasonality remain stable; sudden external shocks may reduce reliability.  

---
