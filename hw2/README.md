# HW2 — ProShares Replication

Completed per the course web-book case [ProShares Replication](https://markhendricks.github.io/finm-portfolio/case_studies/ProShares%20Replication.html) and the Chapter 1 exercise [Unconstrained Optimization](https://markhendricks.github.io/finm-portfolio/exercises/Unconstrained%20Optimization.html).

## Submission

- `HW2_ProShares_Replication.ipynb` — code, answers, and results for the graded portions only: the ProShares case analysis (Section 1) and the Unconstrained Optimization exercise (Section 2).
- `proshares_analysis_data.xlsx` — official data for the ProShares case (monthly, Aug 2011–Sep 2025).
- `spx_returns_weekly.xlsx` — official data for the Unconstrained Optimization exercise (weekly, Jul 2015–Jun 2026).

Keep both data files in the same directory as the notebook when re-running.

## Running

With Python 3.10+:

```bash
python -m pip install -r requirements.txt
jupyter nbconvert --to notebook --execute --inplace HW2_ProShares_Replication.ipynb
```

Or open the notebook in Jupyter/VS Code and "Restart Kernel and Run All." No network access is required. Rerunning updates the CSVs and PNGs in `results/`.

## Conventions

- ProShares case: all statistics use monthly **excess returns** over the 3-month T-bill proxy `USGG3M Index`. The six "Merrill factors" are SPY/EEM/EFA/EUO/IWM (as excess returns) plus `USGG3M Index` kept as a level rate factor.
- Unconstrained Optimization exercise: per the exercise's own instructions, **total** weekly returns are used directly (not converted to excess returns); annualization uses 52 periods/year.
