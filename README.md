# GARCH(1,1) with Limit-Gaussian Innovations

Code for my MSci thesis investigating the limit-Gaussian distribution as an innovation specification for the GARCH(1,1) model, comparing its finite-sample estimation performance against the Gaussian (Q)MLE and Student-t (Q)MLE via a Monte Carlo simulation study, and 
applying the proposed specification to monthly macroeconomic 
inflation indicators.

## Repository Contents

```
├── simulation.ipynb              # All-in-one simulation notebook
├── empirical_application.ipynb   # Empirical application to macroeconomic data
├── README.md                     # Project overview
└── requirements.txt              # Required Python packages
```

## What the Notebook Does

### simulation.ipynb
- Simulates GARCH(1,1) processes under three innovation DGPs: 
  limit-Gaussian, Gaussian, and Student-t
- Estimates model parameters using limit-Gaussian (Q)MLE, Gaussian (Q)MLE, 
  and Student-t (Q)MLE across N=100 Monte Carlo replications of length T=1000
- Reports summary tables of parameter RMSE, aggregated volatility RMSE, 
  and shape parameter recovery
- Generates a representative volatility path figure comparing estimated 
  and true conditional volatility paths across DGPs
- Computes single-replication diagnostics including parameter estimates, 
  persistence estimates, and volatility RMSE for the representative replication
- Reports Monte Carlo bias, MCSD, and RMSE tables for detailed 
  assessment of estimator precision and accuracy

### empirical_application.ipynb
- Downloads five post-2010 monthly macroeconomic inflation series 
  (US PPI, China CPI, US CPI, Euro HICP, UK CPI) from the FRED 
  database via the `fredapi` package
- Reports descriptive statistics including skewness and excess 
  kurtosis of both raw returns and standardised residuals for 
  each series
- Fits GARCH(1,1) models under limit-Gaussian, Gaussian, and 
  Student-t innovation specifications to each series
- Reports estimated parameters and log-likelihood for each specification
- Compares in-sample fit via information criteria (AIC, BIC, AICc, 
  HQIC)
- Generates distribution histograms overlaid with fitted Gaussian 
  densities

## Requirements

```
numpy
pandas
scipy
arch
joblib
matplotlib
fredapi
```

Install via:

```
pip install numpy pandas scipy arch joblib matplotlib fredapi
```

## Data Access

The empirical application downloads data automatically from the 
Federal Reserve Economic Data (FRED) database via the `fredapi` 
package. A free API key is required, available at 
https://fred.stlouisfed.org/docs/api/api_key.html (registration 
takes approximately 2 minutes). Replace `"your_key_here"` in 
Cell 3 of `empirical_application.ipynb` with your API key before 
running.

## Runtime

- `aimulation.ipynb`: approximately 11 hours at T=1000, N=100 on 
  a standard laptop. To run a quick test, set T=200, N=5 in the 
  simulation parameters.
- `empirical_application.ipynb`: approximately 5 minutes.
