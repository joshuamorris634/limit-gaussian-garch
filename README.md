# GARCH(1,1) with Limit-Gaussian Innovations - Simulation Study

Code for my MSc thesis investigating the limit-Gaussian distribution as an innovation specification for the GARCH(1,1) model, comparing its finite-sample estimation performance against the Gaussian QMLE and Student-t MLE via a Monte Carlo simulation study.

## Repository Contents

```
├── simulation.ipynb    # All-in-one simulation notebook
├── README.md           # Project overview
└── requirements.txt    # Required Python packages
```

## What the Notebook Does

- Simulates GARCH(1,1) processes under three innovation DGPs: 
  limit-Gaussian, Gaussian, and Student-t
- Estimates model parameters using limit-Gaussian MLE, Gaussian QMLE, 
  and Student-t MLE across N=100 Monte Carlo replications of length T=1000
- Reports summary tables of parameter RMSE, aggregated volatility RMSE, 
  and shape parameter recovery
- Generates a representative volatility path figure comparing estimated 
  and true conditional volatility paths across DGPs
- Computes single-replication diagnostics including parameter estimates, 
  persistence estimates, and volatility RMSE for the representative replication
- Reports Monte Carlo bias, MCSD, and RMSE tables for detailed 
  assessment of estimator precision and accuracy

## Requirements

```
numpy
pandas
scipy
arch
joblib
matplotlib
```

Install via:

```
pip install numpy pandas scipy arch joblib matplotlib
```

## Runtime

The full simulation (T=1000, N=100) takes approximately 11 hours on a standard laptop. To run a quick test, set T=200, N=5 in the simulation parameters.

## Note on Output

Due to the computational cost of the full simulation, output is not stored in the notebook. All key results are reported in the thesis.
