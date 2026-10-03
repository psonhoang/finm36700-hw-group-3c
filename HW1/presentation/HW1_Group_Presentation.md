# HW1 四人汇报分工与英文讲稿

## 最终提交文件

**书面作业主体：`HW1_Writeup.html`。配套代码：`HW1_Harvard_Endowment.ipynb`。** 两者一起提交，满足题目要求的 write-up along with supporting code。HTML 可在浏览器中打印另存为 PDF，是否需要转换取决于课程平台接受的格式。若平台允许，可附 `multi_asset_etf_data.xlsx`，方便复现。`README.md`、`results/` 和本讲稿是辅助材料。

Notebook 已包含文字回答，但 HTML 是更清楚的必交题阅读版本。汇报前在提交文件上补齐四位成员姓名。下面使用 Speaker 1–4 作为称呼，避免猜测成员姓名。

## 分工与展示顺序

默认总时长约 12 分钟。每位成员准备约 3 分钟，实际时长取决于语速、指图和停顿。四位成员都应熟悉数据口径和最后的结论。

| 成员 | 负责的内容 | 对应报告 | 汇报时展示 | 主要结论 |
|---|---|---|---|---|
| Speaker 1 | 案例背景、数据处理、单资产统计 | Data preparation；2.1 | 资产类别表、summary statistics | SHV 超额收益口径；SPY Sharpe 最高，BWX 最低 |
| Speaker 2 | 相关性、TIPS 与国内外债券比较 | 2.2 | 相关性热图；TIP / IEF / BWX 统计表 | 分散化取决于相关性；TIP 在样本中的三项指标优于这两个债券 ETF |
| Speaker 3 | 切点组合、权重解释、TIPS 情景分析 | 2.3–2.4 | 切点权重表；TIPS 情景表；前沿图辅助说明 | 权重不按单资产 Sharpe 排序；TIPS 权重对均值估计敏感 |
| Speaker 4 | EW / RP / MV 比较、融资解释、结论 | 3；Validation and limitations | 三种策略表现表和柱状图 | 相同目标下 MV 样本内最好；不能直接解释为未来业绩 |

汇报顺序与报告顺序一致。无需朗读全部权重，也无需在主汇报中介绍全部 EXTRA。Speaker 3 的数字较多，可以把完整权重表保留在屏幕上，只讲最有解释力的几项。

讲稿正文为可直接朗读的英文。方括号中的提示只用于展示，不读出来。各人的最后一句已包含衔接。数字适当四舍五入，完整精度见 notebook。

## Speaker 1 — Background, data, and summary statistics

**展示：报告开头、Data preparation、2.1 的资产统计表。**

### English script

Good afternoon. Our group will present the Harvard Endowment case in four parts. We will first introduce the data, then discuss correlations and TIPS, examine the optimal portfolio, and compare three allocation methods.

The case asks whether Treasury Inflation-Protected Securities, or TIPS, should be treated as a separate asset class. Harvard needs its endowment to support spending while preserving purchasing power. That makes inflation exposure relevant to its asset allocation. Our empirical exercise uses nominal ETF returns, so it illustrates the investment opportunity set rather than directly measuring Harvard's spending risk.

We use the official course dataset, with 186 monthly observations from February 2011 through July 2026. We treat SHV as the risk-free proxy and subtract its monthly return from each risky asset's return. We exclude QAI from the main analysis, leaving ten risky ETFs.

We checked that our calculated excess returns match the workbook's excess-return sheet. We also verified that the sample has no missing or duplicate months.

All reported statistics are annualized. We multiply the monthly mean by twelve and monthly volatility by the square root of twelve. The annual Sharpe ratio is the annual mean excess return divided by annual volatility. These means are arithmetic annualized returns, rather than compounded growth rates.

[Show the summary-statistics table.]

SPY, our domestic equity proxy, has the highest Sharpe ratio, approximately zero point nine zero. Its annual mean excess return is 12.70 percent, with volatility of 14.14 percent. BWX, our foreign government bond proxy, has the lowest Sharpe ratio, approximately negative zero point two one. Its mean excess return is negative 1.72 percent.

These statistics describe each asset individually. They do not tell us how much of each asset belongs in an optimal portfolio, because diversification also matters.

Our second speaker will now explain the correlation results and compare TIPS with domestic and foreign bonds.

## Speaker 2 — Correlations and the historical performance of TIPS

**展示：2.2 的相关性热图及 TIP / IEF / BWX 对比表。**

### English script

Thank you. I will discuss how the assets move together and how TIPS performed relative to other bonds.

Our main correlation matrix uses monthly excess returns. We exclude the diagonal and count each pair only once when identifying the highest and lowest correlations.

[Point to PSP and SPY in the correlation heatmap.]

The highest correlation is between PSP and SPY, at approximately zero point eight seven. PSP is a listed private-equity proxy, so its strong relationship with public equity is relevant. It should not be interpreted as a return series for unlisted private-equity funds. Holding both ETFs therefore provides limited diversification against broad equity movements.

[Point to DBC and IEF.]

The lowest correlation is between DBC, our commodity proxy, and IEF, our domestic Treasury bond proxy. Their correlation is approximately negative zero point three one. This negative relationship can help reduce portfolio volatility, although it is a historical estimate and may change over time.

Next, we compare TIP with IEF and BWX. TIP has an annual mean excess return of 1.28 percent, volatility of 4.97 percent, and a Sharpe ratio of approximately zero point two six.

IEF has an annual mean excess return of 0.86 percent, volatility of 6.21 percent, and a Sharpe ratio of approximately zero point one four. BWX has a negative mean excess return and a negative Sharpe ratio.

In this sample, TIP therefore has a higher mean excess return, lower volatility, and higher Sharpe ratio than both bond alternatives.

However, that does not automatically imply a large positive optimal weight. The optimizer considers TIP's contribution after accounting for all the other assets. Also, a TIPS ETF can lose value when real interest rates rise, even though the underlying bonds have inflation protection.

Our third speaker will now show how these asset-level results translate into portfolio weights and why the assumed return on TIPS matters.

## Speaker 3 — Tangency portfolio and TIPS sensitivity

**展示：2.3 切点权重及表现；2.4 情景表。前沿图可作辅助，不必逐线解释。**

### English script

Thank you. I will present the tangency portfolio and our two TIPS experiments.

With a risk-free asset, the optimal risky direction is the inverse covariance matrix multiplied by the expected excess-return vector. We normalize this direction so the risky weights sum to one. This gives the tangency portfolio. Our calculation allows short positions because the empirical questions do not impose position bounds.

[Show the tangency weights.]

The weights do not follow the ranking of individual Sharpe ratios. For example, IEF has a relatively low standalone Sharpe ratio but the largest positive weight, at approximately 132 percent. SPY has a weight of approximately 126 percent, while BWX is shorted at approximately 118 percent.

TIP also has a negative weight, approximately minus 19 percent, despite its positive standalone Sharpe ratio. These allocations reflect the whole covariance matrix and the assets' contributions to the combined portfolio. Positive and negative positions offset, allowing individual weights to exceed 100 percent.

The tangency portfolio has an annual mean excess return of 16.17 percent, volatility of 10.96 percent, and a Sharpe ratio of approximately one point four seven six.

[Show the TIPS scenario comparison.]

First, we remove TIP. The optimal Sharpe ratio falls only slightly, to approximately one point four seven five. TIPS therefore provides a positive but small improvement in the estimated opportunity set under the baseline assumptions. Its negative weight shows that this improvement comes through permitting a short position in this particular optimization.

Second, we increase TIP's expected monthly excess return by twelve basis points, while keeping covariances unchanged. This is an annualized increase of 1.44 percentage points.

The TIP weight then changes from minus 19 percent to approximately positive 126 percent, and the adjusted-model Sharpe ratio rises to approximately one point five seven five.

That improvement is hypothetical. Applying the new weights to the unchanged historical returns gives a lower Sharpe ratio, approximately one point three five nine.

Our interpretation is that TIPS deserves separate attention, but its optimal allocation is highly sensitive to expected-return estimates. The model does not establish a reliable large long position simply from historical data.

Our final speaker will compare three allocation methods at the same return target and discuss the practical implications.

## Speaker 4 — Allocation comparison and conclusion

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

## 数字速查表

这张表供排练或问答使用，不需要全部朗读。Mean 均为年化超额收益。

| 项目 | Annual mean excess | Annual volatility | Annual Sharpe |
|---|---:|---:|---:|
| SPY | 12.70% | 14.14% | 0.8979 |
| TIP | 1.28% | 4.97% | 0.2568 |
| IEF | 0.86% | 6.21% | 0.1384 |
| BWX | −1.72% | 8.19% | −0.2096 |
| Baseline tangency | 16.17% | 10.96% | 1.4758 |
| Tangency without TIP | 15.54% | 10.54% | 1.4745 |
| Higher TIP mean: adjusted model | 13.27% | 8.42% | 1.5749 |
| Higher TIP mean: original history | 11.45% | 8.42% | 1.3592 |
| EW at common target | 12.00% | 27.53% | 0.4359 |
| RP at common target | 12.00% | 32.61% | 0.3679 |
| MV at common target | 12.00% | 8.13% | 1.4758 |

**不要混淆两个 MV 结果：** Section 2 的切点组合将风险资产权重规范化至合计 100%，所以均值是 16.17%；Section 3 把同一方向缩放至 12% 年化超额均值，所以波动率降至 8.13%。正比例缩放不改变 Sharpe。

**不要把百分比和百分点混淆：** TIP 权重从 −19.20% 到 126.17%，是增加约 145.37 个百分点。月度均值增加 0.0012 是增加 0.12 个百分点，即 12 bp；年化增加 1.44 个百分点。

## Common questions — English answers

### 1. Why use excess returns?

We want to measure the return above the risk-free proxy. Subtracting SHV puts all risky assets on the same excess-return basis and makes the Sharpe calculation consistent with the optimization.

### 2. If TIP outperforms the other bonds, why is its optimal weight negative?

Standalone performance and portfolio contribution are different. A positive standalone Sharpe does not guarantee a positive weight. In the unconstrained solution, TIP's expected return is insufficient relative to its covariance exposures and the hedging opportunities provided by the other assets.

### 3. Why can portfolio weights exceed 100 percent?

The model permits long and short positions. A long weight above 100 percent can be offset by short positions. When we scale to a target return, the residual SHV position balances the total budget. These results assume frictionless financing.

### 4. Why does removing TIP reduce both the tangency mean and volatility?

The unit-budget tangency portfolio changes when we change the investment universe, so its mean and volatility both change. A lower volatility at a lower mean is not automatically an improvement. We compare Sharpe ratios, and we also report volatility at a common return target.

### 5. Does the higher Sharpe in the TIP scenario mean that investors actually earned more?

No. We changed an expected-return assumption, not realized history. The adjusted-model Sharpe is approximately 1.575, while the same weights evaluated on the original historical returns have a Sharpe of approximately 1.359.

### 6. Why is risk parity more volatile than equal weighting here?

The assignment uses inverse variance, which puts substantial weight on low-volatility bond ETFs. Their expected excess returns are low, so more leverage is needed to reach the common return target. The comparison must therefore include the scaling and the full covariance matrix.

### 7. Why does MV outperform in sample?

It minimizes variance for the target mean using the same sample moments on which we measure performance. This is an optimization result, not evidence of guaranteed future superiority. Estimation error and changing market conditions can weaken its out-of-sample performance.

### 8. Should Harvard treat TIPS as a separate asset class?

We think separate tracking is justified by their distinct inflation and real-interest-rate exposures. However, our baseline nominal-return sample shows only a small improvement in maximum Sharpe, and the weight is sensitive to the expected-return assumption. The final policy decision should also account for real spending needs and position constraints.

### 9. Why are these results different from HMC's original exhibits?

The case's exhibits use historical capital-market assumptions, real returns, and allocation bounds. Our empirical exercise uses a later ETF dataset, nominal excess returns, and unconstrained positions. They answer related questions but do not use the same inputs or feasible portfolios.

### 10. What did the optional out-of-sample exercise show?

In the specified expanding-window exercise over 2016 through 2025, MV's annualized Sharpe was approximately 0.780, compared with 0.622 for equal weighting, 0.331 for inverse-variance risk parity, and 0.596 for the regularized strategy. The final weights were estimated through 2023 and held over both 2024 and 2025. These outcomes are specific to that sample and assume no trading or financing costs.

## 排练时的操作建议

1. 提前打开 `HW1_Writeup.html`，四个人按报告顺序滚动展示。主讲时用表和图解释，不逐行读代码。
2. 每人熟悉自己的部分和衔接句，同时都能回答 SHV、年化、逆方差 RP、TIPS 月度调整、样本内与样本外这五个问题。
3. 如果总时间压缩至 8 分钟：Speaker 1 删去数据核对细节；Speaker 2 不展开 PSP 的代理局限；Speaker 3 只保留 IEF / TIP 的权重例子及两个情景的 Sharpe；Speaker 4 保留方法定义、三组表现和结论。
4. 确认图上的年化 mean 是 excess return，切点权重与 12% 目标下的 MV 权重属于不同缩放；不要把调整后的预期表现说成历史实现收益。

所有数字来自本次已执行的 notebook 和 `results/` 中的结果文件。
