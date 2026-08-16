## Overview
Linear Regression is the foundational algorithm for predicting a continuous target variable as a weighted linear combination of input features. It assumes the relationship between inputs and output is additive and linear — the model is essentially fitting the best straight line (or hyperplane, in higher dimensions) through the data. Despite its simplicity, it remains widely used because it's fast, interpretable, and a strong baseline against which more complex models should always be compared.

## How It Works
The model predicts: **ŷ = β₀ + β₁x₁ + β₂x₂ + ... + βₙxₙ**, where β₀ is the intercept and each βᵢ is a learned coefficient representing how much the target changes for a one-unit increase in that feature (holding others constant). The coefficients are found by minimizing the **Sum of Squared Errors (SSE)** between predicted and actual values — this is **Ordinary Least Squares (OLS)**, which has a closed-form analytical solution (the "normal equation") for smaller datasets, or can be solved iteratively via **Gradient Descent** for larger ones.

## Key Assumptions (Worth Checking Before Trusting the Model)
- **Linearity:** the relationship between features and target is actually linear
- **Independence of errors:** residuals aren't correlated with each other (violated in time series with autocorrelation)
- **Homoscedasticity:** residual variance is constant across all predicted values (not "funnel-shaped" when plotted)
- **Normality of residuals:** errors are approximately normally distributed (mainly matters for valid confidence intervals/p-values, less for prediction accuracy itself)
- **No severe multicollinearity:** features aren't highly correlated with each other, which destabilizes coefficient estimates

## Methods & Techniques
- **Regularization** — plain OLS overfits with many features or multicollinearity. Two standard fixes:
  - **Ridge Regression (L2):** adds a penalty proportional to the sum of squared coefficients, shrinking all coefficients toward zero without eliminating any — good when most features are at least somewhat useful
  - **Lasso Regression (L1):** adds a penalty proportional to the sum of absolute coefficients, which can shrink some coefficients to *exactly* zero — effectively performing automatic feature selection
  - **Elastic Net:** a weighted blend of L1 and L2, useful when you want some feature selection but also want to handle correlated features gracefully (Lasso alone tends to arbitrarily pick one of several correlated features)
- **Polynomial Regression:** extends linear regression to capture curved relationships by adding polynomial terms (x², x³, interaction terms) — still "linear" in the coefficients, just nonlinear in the original features
- **Feature scaling:** not required for plain OLS to fit correctly, but essential before regularization (Ridge/Lasso) since the penalty term is scale-sensitive — features with larger raw ranges would be penalized unfairly more/less
- **Multicollinearity diagnosis:** **Variance Inflation Factor (VIF)** to detect and address correlated predictors before trusting individual coefficient interpretations
- **Outlier handling:** OLS is sensitive to outliers (squared error penalizes large residuals heavily) — inspect residual plots and consider robust regression (Huber loss) if outliers are a concern

## Evaluation Metrics
- **R² (coefficient of determination):** proportion of variance in the target explained by the model (0 to 1, higher is better) — but always compare against **Adjusted R²** when comparing models with different numbers of features, since plain R² never decreases as you add features, even useless ones
- **RMSE (Root Mean Squared Error):** same units as the target, penalizes large errors more heavily
- **MAE (Mean Absolute Error):** more robust to outliers than RMSE, easier to interpret directly
- **Residual plots:** visually check for patterns (curvature = missing nonlinearity, funnel shape = heteroscedasticity)

## When to Use It
Best for problems with a genuinely linear (or near-linear) relationship, when interpretability matters (e.g. "each additional year of experience adds $X to predicted salary"), and as a fast, low-variance baseline before reaching for more complex models.

## Strengths & Limitations
| Strengths | Limitations |
|---|---|
| Highly interpretable coefficients | Cannot capture nonlinear relationships without manual feature engineering |
| Fast to train, even on large datasets | Sensitive to outliers |
| Well-understood statistical theory (confidence intervals, hypothesis tests) | Assumes linearity, independence, homoscedasticity |
| Good baseline / sanity check | Struggles with multicollinearity if not regularized |

---
---































































































































































