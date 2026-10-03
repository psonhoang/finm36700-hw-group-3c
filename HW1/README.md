# HW1 使用与提交说明

已按课程网页 Harvard's Endowment 的要求完成。书面回答采用英文，方便用于课程作业。

## 建议提交

- `HW1_Writeup.html`：只包含必交题的英文书面回答、计算表和图。可在浏览器打开，用打印功能另存为 PDF。
- `HW1_Harvard_Endowment.ipynb`：完整代码与已运行结果，并附 READING 和全部 EXTRA 部分，明确标注为非必交。
- `multi_asset_etf_data.xlsx`：官方原始数据，复现时与 notebook 放在同一目录。

提交前补上小组成员姓名，并按课程平台的格式要求上传。

## 四人汇报材料

`presentation/HW1_Group_Presentation.html` 是完整排练指南，包含约 12 分钟的四人分工、每人的英文讲稿、衔接句、数字速查表和 10 个常见问题的英文回答。同目录的 `Speaker_1_Script.md` 至 `Speaker_4_Script.md` 是个人讲稿。讲稿是汇报辅助材料，书面作业仍为 `HW1_Writeup.html`，配套代码仍为 `HW1_Harvard_Endowment.ipynb`。

## 运行

在此目录使用 Python 3.10 或更高版本：

```bash
python -m pip install -r requirements.txt
jupyter notebook HW1_Harvard_Endowment.ipynb
```

也可以在 VS Code 或 JupyterLab 中打开 notebook。选择 Python 内核，执行 Restart Kernel and Run All。运行不需要联网，会更新 `results/` 中的 CSV 和图表。

## 数据与口径

题目：https://markhendricks.github.io/finm-portfolio/case_studies/Harvard%27s%20Endowment.html

数据：https://uchicago.box.com/s/w3oqz9iy0kav3n3l4pa04p6etndo2ez2

2026-10-03 下载官方 Box 中的 `multi_asset_etf_data.xlsx`，文件 ID 2003613248823。数据自身标注截至 2026-07-31。原始文件 SHA256：`86d22f4940fc8558c9620b808e101d5c486eb802975dec6e3f4430953d664025`。

- 必交部分使用 2011-02 至 2026-07 的完整样本，共 186 个月。若课程指定其他截止日期，可修改 notebook 顶部的 `ANALYSIS_END` 后重跑。现有 HTML 报告是本次数据的静态结果，不会随重跑自动更新。
- SHV 作为无风险代理，逐月从其他资产的总收益中扣除；必交部分剔除 QAI。
- 均值乘 12，波动率乘 sqrt(12)，Sharpe 按同一规则年化，均值不是复合年化收益率。
- TIPS 预期收益增加 0.0012 按月度调整，即年化增加 1.44 个百分点。
- 题目定义的 RP 是逆方差加权，不是通常的等风险贡献模型。
- 1% 月度目标是超额收益目标。缩放后风险资产权重不必合计为 100%，SHV 余额补足总资金。
- EXTRA 的 OOS 使用题目指定的 2024–2025；扩展窗口最后一次以 2023 年底训练，固定用于 2024 和 2025。

当前数据版本修正了旧 SHV 收益，并更新了 HYG 的部分历史值；因此不能直接套用旧年份作业的数字。

## 已完成的验证

Notebook 全部代码单元已执行，无错误。已检查官方超额收益表与自行相减结果一致、无缺失或重复月份、协方差正定、资金与目标收益恒等式、样本外不使用未来数据，以及 MV 的解析解与独立数值优化一致。
