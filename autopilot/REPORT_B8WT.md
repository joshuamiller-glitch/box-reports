# REPORT B8WT - conditional WT-10 sleeve (on only after a losing pair stretch), separate account
**Verdict: NO.** Switching WT-10 on only when the pair's trailing N-week P&L < 0 keeps a small positive uplift but loses most of the static sleeve's: selected N=4 (clean), 20% share, additive: **+0.12 / +0.07 / +0.10 (clean/H1/H2)** vs static WT-10 **+0.37 / +0.42 / +0.31** and vs pair 1.46/2.83/2.30. It fails the +0.10 gate on H1 (and at 10% on all spans), does not beat a matched random on/off switch (rank 58/34/55/51% vs p95 needed), and is significantly worse than the static sleeve (bootstrap CI of cond - static [-0.44, -0.11]). The static WT-10 verdict (LEAD, plateau fail, no modern replication; REPORT_WT2) is unchanged. ERA FLAG: negative pre-2023. Cells 24 (N 4/8/13 x share 10/20/30/50 x add/cr), runtime 6 s (+23 s WT rebuild for 2x slippage). Registered as B8WT in PREREG_AUTOPILOT.md before the first run.

## Set-up and fill model
- Pair: library/PAIR (B.Cfg(wk_floor=8, wk_loss_pb=None), clean-process series, weekly Sharpe clean/H1/H2/all 1.46/2.83/2.30/1.86, reproduced). Sleeve: WT-10 (ATR14 / mult 3 / no EMA / 10-min / 60-60 bracket, TH off) = library/WT10, 8 NQ, its OWN account rules (5R/-2R day, own day lock, week floor 8R), no netting with the pair; scaled so sleeve weekly sigma = share x pair clean weekly sigma (WT2 construction; K=2.155; rules linear in size). Fill: market entry at next 1-min open after the signal bar, 1 tick/side + commission; 2x slippage = 2 ticks/side (WT trades rebuilt on the 1-second engine, size fixed).
- Rule: ON in ISO week t iff the pair's realised P&L over weeks t-N..t-1 is < 0 (known Monday open; pair history from 2023-02-10, so the clean span has its full lookback). N selected on CLEAN only (sum of clean additive uplift at 20%, add + cr): N=4 0.147, N=8 0.009, N=13 0.080 -> N=4. H1/H2 read once afterwards. N=8 also shown.
- Code: code/census/night_ins/ap_b8wt_{core,run,s2,era,slip}.py; outputs/autopilot/b8wt/{stage1,stage2,era,slip_res}.pkl.

## Why: mechanism check
ON fraction (all-in weeks): N=4 30%, N=8 17%, N=13 9% (N=13: never on in H1/H2). Next-week sleeve P&L when ON vs OFF (all-in, per week): N=4 $21.9k vs $16.4k (pair $28.9k vs $10.5k), N=8 $4.8k vs $20.8k, N=13 $13.3k vs $18.5k. There is no stable "WT earns more after pair losses" effect: N=4 is mildly positive, N=8/13 negative, and the pair itself is NOT weaker after losing stretches (pair earns more in ON weeks for N=4/8: mean reversion). The N=4 uplift is therefore just exposure: the conditional equals the equal-exposure static sleeve (share x on-fraction) and a matched random switch (mean random-switch uplift clean/H1/H2/all +0.109/+0.126/+0.086/+0.110 vs real +0.123/+0.072/+0.098/+0.110).

## All 12 additive cells (uplift vs pair, all spans) with static for reference
| N | share | clean | H1 | H2 | all | static clean/H1/H2 | ON frac clean/H1/H2 |
|---|---|---|---|---|---|---|---|
| 4 | 10% | +0.07 | +0.04 | +0.05 | +0.06 | +0.19/+0.24/+0.17 | 35/14/28% |
| 4 | 20% | +0.12 | +0.07 | +0.10 | +0.11 | +0.37/+0.42/+0.31 | same |
| 4 | 30% | +0.17 | +0.10 | +0.14 | +0.15 | +0.52/+0.57/+0.41 | same |
| 4 | 50% | +0.25 | +0.14 | +0.19 | +0.22 | +0.75/+0.76/+0.54 | same |
| 8 | 10% | +0.02 | +0.01 | -0.01 | +0.01 | as above | 25/7/6% |
| 8 | 20% | +0.03 | +0.01 | -0.03 | +0.02 | | |
| 8 | 30% | +0.04 | +0.02 | -0.04 | +0.02 | | |
| 8 | 50% | +0.05 | +0.03 | -0.08 | +0.02 | | |
| 13 | 10% | +0.03 | 0.00 | 0.00 | +0.02 | | 14/0/0% |
| 13 | 20% | +0.05 | 0.00 | 0.00 | +0.03 | | |
| 13 | 30% | +0.07 | 0.00 | 0.00 | +0.05 | | |
| 13 | 50% | +0.11 | 0.00 | 0.00 | +0.07 | | |
Constant-risk framing at 20%, N=4 (Sharpe clean/H1/H2/all): cond 1.48/2.77/2.34/1.88 vs static 1.91/3.33/2.66/2.31 vs pair 1.46/2.83/2.30/1.86 (conditional cr: H1 below the pair).

## Gate checklist (selected N=4, 20% additive; other shares in the table)
| gate | result | pass |
|---|---|---|
| 1 pre-registered, clean-only selection, H1/H2 once | yes | PASS |
| 3 uplift >= +0.10 clean/H1/H2 (10/20/30/50%) | 20%: +0.12/+0.07/+0.10 (H2 0.098); 10%: 0.07/0.04/0.05; 30%: 0.17/0.10/0.14; 50%: 0.25/0.14/0.19 | FAIL (all four shares fail somewhere; H1 below 0.10 up to 30%) |
| 3 worst week not worse than share | all-in worst week -90.3k vs pair -82.5k: 9.4% worse at 20% (limit 20%); 1.5/9.4/17.3/33.2% at 10/20/30/50 | PASS |
| 4 own null: matched random on/off switch (1000 draws, same ON-week count) p95 of uplift | real 0.12/0.07/0.10/0.11 vs p95 0.21/0.37/0.30/0.20; rank 58/34/55/51% | FAIL |
| 4 circular-shift null (reported; gating for hedge claim) | rank 57/31/52/46%, p95 0.23/0.37/0.33/0.20 | FAIL as hedge |
| 4 WT-10's own random-entry null on standalone Sharpe | cited from REPORT_WT: pass for the sleeve; the switch adds no timing value | cited |
| 4 bootstrap 90% CI all-in uplift vs pair (3000 weekly resamples) | [+0.01, +0.22] | PASS (barely) |
| 4 bootstrap CI of cond - static | [-0.44, -0.11] (N=8: [-0.55, -0.19]) | FAIL (conditional significantly worse than static) |
| 5 plateau (N 3/5 x share 15/20/25, plus share-only; 8 neighbours, keep >= 75% of the all-in +0.11) | 7 of 8 keep (N3 s15 does not) | PASS but on a base that fails gate 3 (vacuous) |
| 5 2x slippage (20%, N=4, same K) | +0.109/+0.069/+0.085 (all +0.099) vs 1x +0.123/+0.072/+0.098 | FAIL (H1/H2 < 0.10, as at 1x) |
| 6 worst-decile corr of contribution with pair | -0.52 (N=8: -0.20), but the sleeve is ON in only 24% (N=4) / 12% (N=8) of the pair's worst-decile weeks | PASS, thin |
| 7 executable | NT8: WT-10 strategy in its own account (NinjaTrader Brokerage via Rithmic) + a Monday-open enable flag from the pair's trailing 4-week realised P&L (account export or small script); margin ~NQ intraday per contract x 3.4 contracts at 20% (sleeve), overnight ~$22k assumed | spec only |

## Insurance metrics, N=4 20% (clean / H1 / H2 / all)
| framing | Sharpe | Sortino | MAR | CVaR5 $ | CVaR10 $ | maxDD $ | worst wk $ | %neg wk |
|---|---|---|---|---|---|---|---|---|
| pair | 1.46/2.83/2.30/1.86 | 2.78/6.09/4.69/3.63 | 4.75/3.91/3.50/9.59 | -78.7k/-77.6k/-81.1k/-79.2k | -78.0k/-66.0k/-79.2k/-78.2k | 280k/152k/217k/280k | -81.9k/-78.3k/-82.5k/-82.5k | 43/39/44/43 |
| cond add | 1.58/2.90/2.39/1.97 | 3.03/6.41/4.91/3.88 | 5.54/4.12/3.56/10.91 | -80.4k/-77.6k/-78.5k/-79.8k | -78.9k/-66.0k/-77.6k/-78.5k | 266k/152k/226k/266k | -90.3k/-78.3k/-79.7k/-90.3k | 42/39/44/42 |
| static add | 1.83/3.25/2.60/2.23 | 3.66/7.51/5.58/4.61 | 7.55/4.97/4.00/14.68 | -83.6k/-82.2k/-83.6k/-84.6k | -79.4k/-66.3k/-77.7k/-79.3k | 224k/149k/215k/224k | -90.3k/-91.0k/-91.1k/-91.1k | 42/36/44/42 |
| cond cr | 1.48/2.77/2.34/1.88 | 2.78/5.87/4.74/3.63 | 5.64/3.77/3.46/11.37 | -77.9k/-77.6k/-78.5k/-78.1k | -77.3k/-66.0k/-73.6k/-77.2k | 230k/152k/215k/230k | -79.9k/-78.3k/-79.7k/-79.9k | 42/39/39/41 |
| static cr | 1.91/3.33/2.66/2.31 | 3.86/7.76/5.72/4.81 | 8.17/5.25/4.12/15.78 | -68.1k/-66.7k/-68.2k/-69.1k | -63.9k/-54.8k/-63.0k/-64.0k | 175k/118k/172k/175k | -74.9k/-75.4k/-75.6k/-75.6k | 40/32/39/39 |
INSURANCE (rep_common spirit): conditional additive NO (worst week 9.4% worse, CVaR5 slightly worse, maxDD -5% only); conditional constant-risk NO (all-in worst week 3.2% better, CVaR5 1.4% better, maxDD 18% lower, but H1 unchanged). The static constant-risk WT-10 blend is the insurance-like version (all-in worst week 8.3% better, CVaR5 12.8% better, maxDD 38% lower), and the switch discards that.

## Era and replication (not gating; REPORT_WT2 already holds the static WT-10 era flag)
- 2013-2022 (WT-10 scaled-bracket history vs the 1-min-engine pair, ON fraction 57-61%): conditional uplift at 20% N=4/8/13 = -0.116 / -0.113 / -0.115 vs static -0.266; fixed 60-pt bracket: -0.034 / -0.013 / +0.023 vs static +0.009; WT standalone Sharpe -1.38 (scaled) / +0.06 (fixed); pair -0.78 on that engine. **ERA FLAG: negative pre-2023** (gross edge absent for WT, per WT2). The switch is never better than static there either, except N=13 fixed (+0.023 vs +0.009, immaterial).
- Replication (reported though no gate passed): H0 2023-02-10..07-31 (26 weeks, 11 ON weeks, WT history series at fixed bracket): cond -0.01, static -0.11 -> no support. Odd/even month split of the selected cell (20%): odd months uplift clean/H1/H2/all +0.08/0.00/-0.27/+0.00, even months +0.16/+0.14/+0.36/+0.21; the effect is not stable across the two halves. ES/RTY not applicable (WT-10 NQ-only here). Newest live weeks: none beyond 2026-10-13.
- Mechanism (one sentence): there is none beyond exposure scaling, since the pair's weekly P&L is not positively autocorrelated and WT is not a better hedge after pair losses. Does not depend on current structure; it simply contains no signal.

## Conclusion
The conditional version does not beat the static WT-10 sleeve and does not beat a random switch with the same on-count; it is dominated by running WT-10 always on in its separate account (that remains the LEAD from WT2 with its failed plateau and missing modern replication). Library: conditional N=4 sleeve saved as B8WT_cond4_WT10 (tag 'conditional', verdict NO).

DONE B8WT
