# REPORT PA6 - VOLUME-CLIMAX EXIT (D01 x M5, H1-H2), live pair
**Verdict: NO. Selected (5, 30): weekly Sharpe uplift -0.15 clean / +0.24 H1 / -0.29 H2 (needed +0.10 each); all-in -0.14; bootstrap CI [-0.50, +0.23]; plateau 0.00 of 4; null all-in rank 0.09. Pool of 5, 6 cells, runtime <1 min**

## Set-up and fill model
- Rows: 13,089 live pair rows (ROWS_corrected_engine.parquet, 2023-02-10..2026-10-13) replayed from the fill on 1-second bars (ap_g11_c_core, as K14/K17) with the 60/60 bracket until the trigger bar, exit at that 1-min bar close; rows closed externally (kind 1) exit at the trigger close; untouched rows/later signals keep live P&L; modified rows re-run through the live account B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (baseline 1.46/2.83/2.30). Fill 1 tick/side + $34.88 per 8 lots; 2x slippage SLIP_PT 1.0. Triggers use data through the trigger bar only.
- Rule: At the close of 1-min bar f (entry+1 <= f < exit) exit at that close if NQ volume[f] >= k x mean(volume at the same ET minute over the previous 20 sessions) AND the bar closed in the trade direction AND the trade is >= X points in profit at that close. Grid 6: k {3,5} x X {10,20,30} points.
- Null (timing-destroyed, best-of-grid, as K14): the volume-ratio series circularly shifted by a random whole number of days in [7,400] (time of day preserved), the identical rule over the full 6-cell grid, best clean uplift per draw, 100 draws, linear delta-P&L on the baseline account.
- Selection clean only (max clean uplift of 6 cells); H1/H2 read once for the carried cell (grid table prints all spans for transparency). Fired rows per cell: (3, 10) 4225; (3, 20) 3579; (3, 30) 2827; (5, 10) 1927; (5, 20) 1619; (5, 30) 1229.
- Disclosure: pre-registered in PREREG_AUTOPILOT.md (block PA4/PA5/PA6/PA7) before the first run; no earlier H1/H2 look at this observable. Pair-change framing only (exit rule, no separate book; additive/constant-risk n/a). ES/RTY cross-check not run (NQ gates fail). Pair rows start 2023-02: ERA flag n/a; pre-2023 not testable.

## Grid, uplift per cell (weekly Sharpe vs the live pair; all spans printed for transparency, only the clean-selected cell was read for H1/H2)
| cell | clean | H1 | H2 | all-in |
|---|---|---|---|---|
| (3, 10) | -1.446 | -0.092 | -1.728 | -1.259 |
| (3, 20) | -0.944 | -0.772 | -1.461 | -1.037 |
| (3, 30) | -0.643 | -0.433 | +0.087 | -0.428 |
| (5, 10) | -0.821 | -0.864 | -0.849 | -0.848 |
| (5, 20) | -0.600 | +0.152 | -1.015 | -0.600 |
| (5, 30) **(selected)** | -0.151 | +0.238 | -0.292 | -0.136 |

## Result for the carried cell: (5, 30)
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.31 | -0.151 | +0.041 |
| H1 | 2.83 | 3.07 | +0.238 | -0.026 |
| H2 | 2.30 | 2.00 | -0.292 | -0.284 |
| all | 1.86 | 1.72 | -0.136 | -0.045 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank): clean -0.151 vs -0.015 / 0.55; H1 +0.238 vs +0.630 / 0.70; H2 -0.292 vs +0.622 / 0.00; all -0.136 vs +0.113 / 0.09
- bootstrap 90% CI of all-in uplift: [-0.502, +0.233]
- plateau: 0.00 of 4 neighbours keep >= 75% of the all-in uplift; neighbours: k x0.75 -0.486; k x1.25 +0.046; X x0.75 -0.565; X x1.25 -0.265
- alternating-month split (pre-registered): select (5, 30) (-0.180) reads -0.080 on the other half; select (3, 30) (-0.066) reads -1.086 on the other half
- H0 (2023-02-10..07-31) uplift: +1.514; replications counted (alt-month, H0): 1 of 2 needed (newest live weeks and ES/RTY not available / not applicable for this pair-row family)
- worst-week (candidate vs pair): clean -80.4k vs -81.9k; H1 -77.5k vs -78.3k; H2 -82.5k vs -82.5k; all -82.5k vs -82.5k; weekly corr with pair 0.913 (pair change, no hedge claim; worst-decile corr n/a)

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.31 | 2.24 | 3.39 | -78.9k | -78.4k | 358k | -80.4k | 41.0 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 3.07 | 6.11 | 4.57 | -77.4k | -70.6k | 147k | -77.5k | 25.0 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 cand | 2.00 | 3.96 | 2.94 | -80.2k | -78.7k | 227k | -82.5k | 47.2 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all cand | 1.72 | 3.10 | 7.14 | -79.1k | -78.3k | 358k | -82.5k | 39.9 |

## Reading
A volume climax in the trade direction while in profit is not an exhaustion signal for this pair: every cell cuts winners that the pair would have held to the 60-pt target or the opposite flip (cells fire on 1,200-4,200 rows, 9-32% of rows), and clean uplift is negative in all 6 cells (-0.15 to -1.45). The carried cell (5, 30) has clean -0.15, H1 +0.24, H2 -0.29. Truncating winners reverses the pair's trend-following edge, as in C2-G1 (unconditional) and J0 (stagnation).

## Executability / era / replication
NT8: needs only 1-minute NQ volume and a 20-session same-minute volume table inside the strategy (OHLCV, no order flow); exit by market order at the close of the trigger bar. Margin unchanged (exits only). Executable. Era: pair rows start 2023-02, ERA flag n/a. Replication: alt-month and H0 as listed in the checklist; newest live weeks and ES/RTY not run. Fill model: market exit at the trigger bar close, 1 tick/side + commission; executable at NinjaTrader Brokerage via Rithmic. Files: code/census/night_ins/ap_pa1_exit.py, ap_pa1_exit_rep.py; outputs/autopilot/pa6/ (pa6_all.pkl, pa6_summary.json), log pa6.log.

DONE PA6
