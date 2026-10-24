# HW4 — DFA: The Factors

Completed per Sections 2 and 3 of the course DFA case: *The Factors* (questions 1–5) and *CAPM* (questions 1–5).

## Submission

- `HW4_DFA_Factors.ipynb`: code, answers, and results for Sections 2 and 3.
- `dfa_analysis_data.xlsx`: official data from the course Box folder (monthly, 1926-07 to 2026-08, Ken French Data Library). Uses the `factors` and `portfolios (total returns)` sheets.

Keep the data file in the same directory as the notebook when re-running.

## Running

With Python 3.10+:

```bash
python -m pip install -r requirements.txt
jupyter nbconvert --to notebook --execute --inplace HW4_DFA_Factors.ipynb
```

You can also open the notebook in Jupyter or VS Code and choose "Restart Kernel and Run All". No network access is needed. Rerunning updates the CSVs and PNGs in `results/`.

## Conventions

- `Mkt-RF`, `SMB`, and `HML` are already excess returns, so `RF` is not subtracted from them. The 25 portfolios are total returns and are converted to excess returns with `RF`.
- Means are annualized with ×12, volatilities and Sharpe ratios with ×√12. VaR(.05) is the monthly 5th percentile and is not annualized.
- Section 2 subsamples: 1926-07 to 1980-12, 1981-01 to 2001-12, and 2002-01 to 2026-08. The full sample (1926-07 to 2026-08) is also used for the Question 3 correlation matrix and the Question 4 cumulative-return plot.
- Cumulative returns are the growth of $1, ∏(1 + r), applied to the factor excess returns.
- Section 3 uses January 1981 to August 2026. Alphas and Treynor ratios are annualized with ×12, information ratios with ×√12. The joint test H uses monthly alphas, the residual covariance matrix, and the monthly market Sharpe ratio, compared with χ²(25).
