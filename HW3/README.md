# HW3 — Barnstable and Long-Run Risk, VaR, and Decomposing Private Equity

Completed per the course web-book case [Barnstable and Long-Run Risk](https://markhendricks.github.io/finm-portfolio/case_studies/Barnstable%20and%20Long-Run%20Risk.html) and the exercises [VaR of Equity Portfolio](https://markhendricks.github.io/finm-portfolio/exercises/VaR%20of%20Equity%20Portfolio.html) and [Decomposing Private Equity](https://markhendricks.github.io/finm-portfolio/exercises/Decomposing%20PE.html).

## Submission

- `HW3_Barnstable_VaR_PE.ipynb`: code, answers, and results for the graded parts only. That is Barnstable Section 2 (Part A), the VaR exercise (Part B), and the PE decomposition exercise (Part C). The Barnstable READING section is not included.
- `barnstable_analysis_data.xlsx`: official data for the Barnstable case (monthly, 1926-01 to 2025-12), downloaded from the course Box folder on 2026-10-18.
- `private_equity_data.xlsx`: official data for Parts B and C (weekly, 2015-01 to 2025-10).
- `Barnstable Long-Run Risk.ipynb`, `VaR Equity Portfolio.ipynb`, `Decomposing PE.ipynb`, and the HBS case PDF: original problem statements.

Keep both data files in the same directory as the notebook when re-running.

## Running

With Python 3.10+:

```bash
python -m pip install -r requirements.txt
jupyter nbconvert --to notebook --execute --inplace HW3_Barnstable_VaR_PE.ipynb
```

You can also open the notebook in Jupyter or VS Code and choose "Restart Kernel and Run All". No network access is needed. Rerunning updates the CSVs and PNGs in `results/`.

## Conventions

- Barnstable: means are annualized with ×12 and volatilities with ×√12. Excess log return = log(1+r^m) − log(1+r^f). The underperformance probability is p(h) = Φ(−√h · SR), where SR is the Sharpe ratio of excess log returns.
- VaR: the exercise lets us choose any 4 stocks. We use the listed PE managers `APO, BX, KKR, CG` from `private_equity_data.xlsx` (weekly total returns). VaR/CVaR are weekly and not annualized. Conditional volatility assumes a zero mean (root mean squared return) and uses data through t−1. The rolling window is 26 weeks, and z = −1.65.
- PE decomposition: weekly excess returns (over `SHV`) from the `excess returns` sheet, annualized with 52. The `total returns` sheet in this file is computed from unadjusted prices, so distributions are left out. This mainly affects the bond ETFs (`AGG, HYG, IEF, SHV`).
