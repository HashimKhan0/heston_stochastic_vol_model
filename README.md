# Heston Stochastic Volatility Model

An implementation and exploration of the **Heston (1993) stochastic volatility model** in Python: Monte Carlo simulation of correlated price and variance paths, semi-analytical option pricing via the characteristic function, and an analysis of how the model's parameters shape price dynamics.

## The model

Under the risk-neutral measure:

$$dS_t = r S_t\,dt + \sqrt{v_t}\,S_t\,dW_t^S$$

$$dv_t = \kappa(\theta - v_t)\,dt + \sigma\sqrt{v_t}\,dW_t^v, \qquad d\langle W^S, W^v\rangle_t = \rho\,dt$$

| Parameter | Meaning |
|---|---|
| κ | speed of mean reversion of variance |
| θ | long-run variance |
| σ | volatility of volatility |
| ρ | correlation between price and variance shocks (drives skew) |
| v₀ | initial variance |

## What's in the repo

| File | Contents |
|---|---|
| `heston.ipynb` | Heston characteristic function, European call pricing by numerical integration, and Monte Carlo simulation of correlated price/variance paths. Compares paths under strong positive vs. negative ρ. |
| `analysis.ipynb` | Effect of mean-reversion speed: simulates variance and price paths under fast (κ = 5) vs. slow (κ = 0.5) mean reversion and compares summary statistics. |
| `explore.ipynb` | Motivation from real data: AAPL daily returns and rolling volatility (2022–2024) showing that volatility is not constant. |
| `analysis.tex` | Write-up (in progress). |

## Running it

```bash
pip install -r requirements.txt
jupyter notebook heston.ipynb
```

## Tech stack

Python · NumPy · SciPy · pandas · matplotlib / seaborn / plotly · yfinance · py_vollib
