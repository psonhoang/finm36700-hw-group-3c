# Speaker 4 — Allocation comparison and conclusion

**展示：Section 3 的收益与波动率表、柱状图；必要时指向 residual SHV weight。**

### English script

Thank you. I will compare equal weighting, the assignment's risk-parity rule, and mean-variance allocation.

To make the comparison meaningful, we scale every strategy to the same expected monthly excess return of one percent. This corresponds to an arithmetic annualized excess mean of twelve percent.

Equal weighting starts with identical weights across the ten risky assets. The assignment defines risk parity as inverse-variance weighting, so assets with lower individual variance receive larger weights. This differs from a portfolio that explicitly equalizes each asset's risk contribution.

Mean-variance allocation uses the covariance-adjusted expected-return direction described by our third speaker.

After scaling, the risky weights do not necessarily sum to one. The remaining weight is allocated to SHV. A negative SHV weight represents borrowing under the model's financing assumption.

[Show the allocation-performance table and chart.]

All three strategies achieve the same twelve-percent annual mean excess return in sample. Equal weighting has annual volatility of 27.53 percent and a Sharpe ratio of approximately zero point four four. Inverse-variance risk parity has volatility of 32.61 percent and a Sharpe ratio of approximately zero point three seven.

Mean-variance allocation has volatility of only 8.13 percent and a Sharpe ratio of approximately one point four eight. It therefore gives the lowest volatility and highest Sharpe at the common target.

This is an in-sample result: mean-variance allocation is optimized using the same data on which we evaluate it. The inverse-variance strategy emphasizes low-volatility bonds, but their low excess returns require substantial leverage to reach the target. Consequently, lower individual asset volatility does not guarantee lower portfolio volatility after scaling.

We also checked the analytical mean-variance weights against an independent numerical optimization and obtained matching results.

Our conclusion is that diversification and covariance matter as much as individual asset performance. TIPS has distinct inflation exposure, but its estimated optimal weight is sensitive to assumptions. Implementing an allocation for Harvard would also require position limits, financing costs, and consideration of spending needs.

Thank you. We are happy to take questions.
