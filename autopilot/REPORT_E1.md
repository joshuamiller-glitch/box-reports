# REPORT E1 - denoised signals (ES / composite / residual) driving the live ST and HM rules, executed on NQ

E1 denoised signals: the live ST/HM signal logic computed on (a) ES bars, (b) a volatility-normalised ES+NQ composite price path, (c) the NQ-minus-beta*ES residual path, with orders and brackets on NQ.


Engine: 1-minute NQ (p1_core account; fixed 60/60 bracket; live rules: per-book 5R/-2R, day lock 8R/2R/67 percent, week floor 8R), 1 tick/side + $34.88/8 lots, window 2023-02..2026-10; uplift is against the SAME engine run with the live NQ signals (not against the 1-second live pair; engine baseline weekly Sharpe clean/H1/H2 1.65/2.60/2.04 vs 1.46/2.83/2.30 for the live pair).

## Descriptives (2023-08..2026-10, trades after the live per-book rules and locks)

| source | trades | trades/day | avg pts | win rate | whipsaws (stop within 10 min) | whipsaw share | net $ | Sharpe clean/H1/H2 |
|---|---|---|---|---|---|---|---|---|
| live NQ signals | 6230 | 7.85 | +3.59 | 53.0% | 206 | 3.3% | 2,816,378 | 1.65 / 2.60 / 2.04 |
| (a) ES bars -> NQ execution | 6243 | 7.88 | +3.27 | 52.7% | 244 | 3.9% | 2,312,604 | 0.89 / 3.71 / 1.53 |
| (b) composite ES+NQ vol-normalised path | 6198 | 7.82 | +2.66 | 52.2% | 241 | 3.9% | 1,728,134 | 0.80 / 2.68 / 0.81 |
| (c) NQ minus beta x ES residual path | 6467 | 8.16 | +2.46 | 52.2% | 243 | 3.8% | 1,799,111 | 0.51 / 0.74 / 3.22 |

## (a) ES bars -> NQ execution
**Verdict: NO** (1/6 gates; replication 0/2). Win rate 52.7% vs 53.0% live-signal engine; trades/day 7.88 vs 7.85; all-in uplift -0.409.

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: -0.761 / +1.108 / -0.506
- [FAIL] 3 worst week not worse (all-in): -81,523 vs -78,823
- [PASS] 4 own null p95 on all-in uplift: real -0.409 vs p95 -1.264 (median -2.331, rank 1.00, n=60)
- [FAIL] 4 bootstrap 90% CI >0: [-1.187, +0.330]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 8
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.832 / +0.957 / -0.479
- Replication H0 2023-02..07: -0.932 -> FAIL; alternating months odd/even: -0.917 / +0.236 -> FAIL (need >= -0.205); cross-instrument and newest weeks not applicable.

Plateau neighbours (variant minus same-parameter NQ-signal engine, all-in): es|stp x0.75: -0.575; es|stp x1.25: -0.369; es|stm x0.75: -0.197; es|stm x1.25: -0.462; es|hf x0.75: -0.355; es|hf x1.25: -0.784; es|hs x0.75: -0.366; es|hs x1.25: -0.206

## (b) composite ES+NQ vol-normalised path
**Verdict: NO** (0/6 gates; replication 0/2). Win rate 52.2% vs 53.0% live-signal engine; trades/day 7.82 vs 7.85; all-in uplift -0.797.

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: -0.848 / +0.086 / -1.221
- [FAIL] 3 worst week not worse (all-in): -85,643 vs -78,823
- [FAIL] 4 own null p95 on all-in uplift: real -0.797 vs p95 -0.485 (median -1.147, rank 0.75, n=60)
- [FAIL] 4 bootstrap 90% CI >0: [-1.418, -0.195]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 8
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.750 / -0.120 / -1.360
- Replication H0 2023-02..07: -0.577 -> FAIL; alternating months odd/even: -1.180 / -0.305 -> FAIL (need >= -0.398); cross-instrument and newest weeks not applicable.

Plateau neighbours (variant minus same-parameter NQ-signal engine, all-in): comp|stp x0.75: -0.658; comp|stp x1.25: -0.445; comp|stm x0.75: -0.312; comp|stm x1.25: -0.151; comp|hf x0.75: +0.362; comp|hf x1.25: -0.487; comp|hs x0.75: -0.373; comp|hs x1.25: -0.073

## (c) NQ minus beta x ES residual path
**Verdict: NO** (0/6 gates; replication 0/2). Win rate 52.2% vs 53.0% live-signal engine; trades/day 8.16 vs 7.85; all-in uplift -0.691.

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: -1.143 / -1.854 / +1.189
- [FAIL] 3 worst week not worse (all-in): -86,903 vs -78,823
- [FAIL] 4 own null p95 on all-in uplift: real -0.691 vs p95 +0.299 (median -0.386, rank 0.25, n=60)
- [FAIL] 4 bootstrap 90% CI >0: [-1.816, +0.432]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 8
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -1.379 / -1.772 / +1.142
- Replication H0 2023-02..07: -1.307 -> FAIL; alternating months odd/even: -1.061 / -0.235 -> FAIL (need >= -0.346); cross-instrument and newest weeks not applicable.

Plateau neighbours (variant minus same-parameter NQ-signal engine, all-in): resid|stp x0.75: -1.026; resid|stp x1.25: -0.643; resid|stm x0.75: -0.377; resid|stm x1.25: -0.291; resid|hf x0.75: -0.849; resid|hf x1.25: -0.954; resid|hs x0.75: -0.841; resid|hs x1.25: -0.951

## Reading
The question was whether denoising lifts win rate by 2-5 points at similar trade count (the D3 lever that moves net most). See the descriptives table: any variant that does not change win rate by >= 2 points cannot move net through that lever.

Executability: NT8 strategy with three data series (NQ, ES, optional); composite/residual paths computed bar by bar in OnBarUpdate (rolling 390-minute volatility and 20-day beta); signal logic unchanged (ST 120/2.0 close, HM 20/55 HMA of close-VWAP, EMA200); orders and brackets on NQ. Margin unchanged. ERA: not run (ES long series would allow 2013-22 but the pair has no edge there).

DONE E1