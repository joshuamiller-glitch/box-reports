# DS3_STACK_C - chop-week / stack-state de-risking (D3SKC, 2026-10-28). Research only.

## Plain line
**13 cells (11 de-risk + 2 size-up controls), 0 PASS / 0 CANDIDATE / 0 LEAD / 11 DEAD. None of the 11 de-risk rules beats uniform scaling of the stack: in PRE every cell has a negative change in weekly Sharpe (-0.005 to -0.074), a negative or placebo-indistinguishable lot-matched worst-20 effect, and a raw mean cost of -0.5k to -15.6k/wk. The stack's weekly/daily P&L shows no usable serial dependence on the downside: a bad week/stretch does not predict a bad next stretch. The size-UP controls were better than placebo in PRE (rank 0.98-0.99 on both statistics: sizing UP after a drawdown / after a bad week-to-date improved Sharpe), the opposite sign to the de-risk idea, but they do not hold in HOLD (E1 HOLD dSharpe -0.006, LM gain on HOLD's worst-5 weeks -49k; E2 -44k), miss the best-of-60 null, and add lots in the worst weeks, so they are a control reading, not a candidate.** Prereg sha256 `2905f01ef598f9bf68fa7f8c169825f4a00a11b94807a1ecf285804e2d788144` (l2vast/ds3/prereg/STK_C_prereg.md), written and logged before any cell was scored. Best-of-F: F_C = 13; program F_total taken as 60 (G7 uses the max of 60 placebo draws, p95).

Best de-risk cell regardless of verdict (by lot-matched worst-20 gain in PRE): **B1_CONS2** (halve the next day after 2 consecutive realised losing days): raw PRE -6.4k/wk (MDE 10.6k), LM mean -1.1k, SD -9.5% (c = 0.889, so the SD fall is the lot cut), LM gain on the PRE worst-20 weeks +122k (placebo rank 0.87, not 0.95), but dSharpe -0.015 (fails G1) and placebo rank on dSharpe 0.45; HOLD dSharpe +0.040 and HOLD LM +3.1k, 2023 span dSharpe -0.052 (fails G5), 2023/2024/2025 yearly dSharpe all <= 0. Failed gates: G1, G3, G5, G6, G7. **No PRE-selected rule is carried to F from section C** (selection rule: highest PRE dSharpe among cells passing G1-G3; none pass G1). If F wants a conservative defensive layer anyway, B1_CONS2 is the only one with a positive LM worst-20 effect in PRE, HOLD and the fixed all-window W20F (+353k LM on W20F), but it is not statistically separable from a blunt 0.89x scale-down.

## Method (what was fixed; see the prereg for the full text)
- Data: l2vast/ds3/out/dv2a/stack_trades.parquet (live stack: ST10+HM10+WT7+KB/SM/PE at the frozen weights, exact lock engine, baseline WF 45,947/wk on the full audit span). Rows with label day after 2026-02-06 were dropped at load and never inspected (UNTOUCHED rule; the audit file extends to 2026-10-16). Scored weeks 2023-04-03..2026-02-06 = 149 weeks: X 44 (2023-04..2024-01), PRE 74 (2024-02..2025-06, week Monday label day), HOLD 31 (2025-07..2026-02-06). Baseline mean WF(PRE+HOLD) on this cut is 47,926/wk; PRE SD of weekly P&L (SDW, the unit of the X thresholds) = 133,462 $/wk.
- Rule multiplier m applied to a trade's lots at ENTRY; trade P&L = m x gross - sweep for the m>1 cells (lock logic is in nominal-lot R, so P&L is linear in lots). State = the RULE-MODIFIED stack's realised P&L at entry time (event simulation: a trade's P&L is released at its exit_et; day rules use completed label days only). The 50-contract concurrent cap is NOT applied to the size-up controls.
- Lot-matched (LM) = cell minus c x unchanged stack, c = lot-seconds-weighted mean multiplier in the window (uniform scaling to the same average lots). MDE = 2.8 x SD(paired weekly diff)/sqrt(n). Placebo = 200 circular shifts of the cell's entry-order multiplier vector (keeps frequency and clustering, breaks the link to the state), scored on PRE dSharpe and PRE LM W20P gain; best-of-60 = p95 of the max of 60 draws.
- Worst-20: W20F = 20 worst weeks of the unchanged stack over all 149 weeks (total -3,534k); W20P = 20 worst of PRE (total -2,287k, re-derived on PRE only). Own-sorted worst-20 of each cell also given. Caution: selecting the base's worst weeks in-sample, any independent variation regresses toward the mean, so raw "saved in bad weeks" is biased in favour of de-risking; the LM and placebo columns are the unbiased reads.
- Cell definitions are in the prereg; D1 uses losing trade exits (pnl < 0) in the last two completed days as a PROXY for TH cuts + stop-outs (the trade table has no exit-reason column); threshold = 33 losing exits per 2 days (PRE 80th pct of the unchanged stack).

## Table 1 - PRE (2024-02..2025-06, 74 wk): raw and lot-matched, placebo
| cell | entries affected | lot-time affected | c (lot mult) | d mean/wk | MDE | LM mean | SD (base 133.5k) | maxDD (base -409k) | worst wk (base -307k) | dSharpe/wk | LM gain W20P | placebo rank dSh | rank LM | best-of-60 p95 dSh |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A1_WTD_H1.0 | 8% | 7% | 0.951 | -2.5k | 7.1k | -0.1k | 131.7k | -360k | -221k | -0.014 | -146.8k | 0.43 | 0.04 | +0.080 |
| A2_WTD_H1.5 | 3% | 2% | 0.981 | -2.8k | 5.3k | -1.9k | 135.5k | -452k | -266k | -0.026 | -249.7k | 0.01 | 0.00 | +0.026 |
| A3_WTD_H2.0 | 1% | 1% | 0.995 | -0.5k | 2.5k | -0.2k | 134.1k | -386k | -284k | -0.005 | -47.1k | 0.14 | 0.02 | +0.020 |
| A4_WTD_B1.5 | 3% | 2% | 0.963 | -5.6k | 10.7k | -3.8k | 139.5k | -495k | -228k | -0.056 | -499.3k | 0.01 | 0.00 | +0.069 |
| B1_CONS2 | 22% | 22% | 0.889 | -6.4k | 10.6k | -1.1k | 120.8k | -471k | -221k | -0.015 | +122.4k | 0.45 | 0.87 | +0.080 |
| B2_CONS3 | 11% | 11% | 0.944 | -5.2k | 9.6k | -2.5k | 125.8k | -481k | -266k | -0.020 | +6.4k | 0.26 | 0.51 | +0.067 |
| C1_DD20_1.5 | 24% | 26% | 0.849 | -12.1k | 11.3k | -4.9k | 125.5k | -546k | -266k | -0.074 | -276.6k | 0.03 | 0.01 | +0.078 |
| C2_DD40_1.5 | 34% | 38% | 0.825 | -9.0k | 12.3k | -0.6k | 119.6k | -410k | -248k | -0.033 | -64.8k | 0.35 | 0.35 | +0.054 |
| C3_DD60_1.5 | 42% | 44% | 0.790 | -12.3k | 13.2k | -2.2k | 116.9k | -488k | -248k | -0.054 | -144.4k | 0.20 | 0.15 | +0.067 |
| C4_DD40_1.0 | 52% | 54% | 0.726 | -15.6k | 14.7k | -2.4k | 107.3k | -370k | -221k | -0.058 | -66.0k | 0.20 | 0.30 | +0.078 |
| D1_STRESS2D | 16% | 9% | 0.934 | -8.3k | 9.4k | -5.1k | 123.0k | -403k | -279k | -0.037 | -55.5k | 0.09 | 0.28 | +0.072 |
| E1_UP_DD40 | 22% | 26% | 1.102 | +7.9k | 9.3k | +3.0k | 141.3k | -366k | -366k | +0.036 | +264.7k | 0.99 | 0.99 | +0.059 |
| E2_UP_WTD1.5 | 3% | 2% | 1.019 | +2.8k | 5.3k | +1.9k | 133.5k | -367k | -348k | +0.021 | +246.8k | 0.98 | 1.00 | +0.024 |

## Table 2 - HOLD (2025-07..2026-02-06, 31 wk) and X (2023-04..2024-01, 44 wk)
| cell | HOLD d mean | MDE | LM mean | LM MDE | dSharpe | LM gain base-worst-5 | X d mean | X dSharpe | X LM gain worst-5 |
|---|---|---|---|---|---|---|---|---|---|
| A1_WTD_H1.0 | +1.9k | 11.3k | +3.0k | 10.6k | +0.031 | +122.0k | -2.9k | -0.028 | +7.5k |
| A2_WTD_H1.5 | +1.7k | 4.5k | +2.1k | 4.3k | +0.020 | +43.9k | -1.4k | -0.015 | -30.7k |
| A3_WTD_H2.0 | +0.4k | 1.1k | +0.4k | 1.0k | +0.004 | +10.7k | +0.0k | +0.000 | +0.0k |
| A4_WTD_B1.5 | +3.4k | 9.1k | +4.2k | 8.6k | +0.040 | +87.8k | -2.8k | -0.030 | -61.4k |
| B1_CONS2 | -1.2k | 18.4k | +3.1k | 14.9k | +0.040 | +168.3k | -6.4k | -0.052 | -72.1k |
| B2_CONS3 | -0.0k | 10.4k | +2.1k | 9.6k | +0.015 | +77.2k | -5.0k | -0.045 | -59.8k |
| C1_DD20_1.5 | -8.4k | 24.1k | -2.8k | 20.5k | -0.015 | +84.3k | +0.0k | +0.008 | +70.3k |
| C2_DD40_1.5 | -17.4k | 26.6k | -6.5k | 20.3k | -0.070 | -29.2k | -2.1k | +0.002 | +94.1k |
| C3_DD60_1.5 | -19.4k | 27.0k | -7.8k | 20.6k | -0.085 | -41.3k | -5.7k | -0.025 | +60.2k |
| C4_DD40_1.0 | -13.7k | 25.7k | -1.3k | 18.9k | -0.037 | -59.4k | -7.0k | -0.042 | +33.1k |
| D1_STRESS2D | -2.8k | 13.1k | -0.5k | 13.1k | -0.015 | +34.9k | +0.1k | +0.002 | +34.8k |
| E1_UP_DD40 | +7.5k | 21.7k | +2.6k | 18.5k | -0.006 | -49.3k | +3.0k | +0.001 | -13.8k |
| E2_UP_WTD1.5 | -1.7k | 4.6k | -2.1k | 4.3k | -0.020 | -44.1k | +1.4k | +0.015 | +30.6k |

## Table 3 - worst-20 weeks (fixed W20F on all 149 wk; W20P re-derived on PRE only) and the trade-off line ($/wk)
| cell | W20F base | W20F cell | W20F gain | W20F LM gain | own-sorted W20 cell (base -3,534k) | W20P base | W20P cell | W20P LM gain | given up per good week (raw / LM) | saved per bad W20F week (raw / LM) |
|---|---|---|---|---|---|---|---|---|---|---|
| A1_WTD_H1.0 | -3,534k | -3,222k | +312.5k | +185.0k | -3,238k | -2,287k | -2,321k | -146.8k | -4.4k / -1.7k | +15.6k / +9.3k |
| A2_WTD_H1.5 | -3,534k | -3,542k | -7.5k | -50.5k | -3,617k | -2,287k | -2,494k | -249.7k | -1.6k / -0.7k | -0.4k / -2.5k |
| A3_WTD_H2.0 | -3,534k | -3,558k | -23.7k | -32.7k | -3,558k | -2,287k | -2,323k | -47.1k | +0.0k / +0.2k | -1.2k / -1.6k |
| A4_WTD_B1.5 | -3,534k | -3,549k | -15.1k | -100.9k | -3,830k | -2,287k | -2,701k | -499.3k | -3.2k / -1.5k | -0.8k / -5.0k |
| B1_CONS2 | -3,534k | -2,792k | +742.2k | +353.4k | -2,876k | -2,287k | -1,911k | +122.4k | -11.9k / -3.9k | +37.1k / +17.7k |
| B2_CONS3 | -3,534k | -3,142k | +392.1k | +198.7k | -3,254k | -2,287k | -2,153k | +6.4k | -7.8k / -3.8k | +19.6k / +9.9k |
| C1_DD20_1.5 | -3,534k | -3,077k | +456.9k | -3.9k | -3,178k | -2,287k | -2,219k | -276.6k | -12.5k / -3.0k | +22.8k / -0.2k |
| C2_DD40_1.5 | -3,534k | -2,723k | +810.9k | +146.1k | -2,926k | -2,287k | -1,951k | -64.8k | -16.3k / -2.6k | +40.5k / +7.3k |
| C3_DD60_1.5 | -3,534k | -2,679k | +854.8k | +77.4k | -2,896k | -2,287k | -1,951k | -144.4k | -20.3k / -4.2k | +42.7k / +3.9k |
| C4_DD40_1.0 | -3,534k | -2,593k | +940.8k | -7.8k | -2,794k | -2,287k | -1,726k | -66.0k | -21.9k / -2.3k | +47.0k / -0.4k |
| D1_STRESS2D | -3,534k | -3,342k | +192.1k | +38.8k | -3,408k | -2,287k | -2,191k | -55.5k | -6.9k / -3.7k | +9.6k / +1.9k |
| E1_UP_DD40 | -3,534k | -3,887k | -352.9k | +107.9k | -3,949k | -2,287k | -2,256k | +264.7k | +10.1k / +0.6k | -17.6k / +5.4k |
| E2_UP_WTD1.5 | -3,534k | -3,529k | +4.9k | +47.8k | -3,565k | -2,287k | -2,083k | +246.8k | +1.6k / +0.7k | +0.2k / +2.4k |

## Table 4 - by calendar year: change in weekly mean $ (dSharpe) vs unchanged stack
| cell | 2023 (n) | 2024 | 2025 | 2026 (5 wk) |
|---|---|---|---|---|
| A1_WTD_H1.0 | -2.5k (-0.023) | -0.3k (+0.008) | -3.0k (-0.017) | +3.2k (+0.030) |
| A2_WTD_H1.5 | -1.6k (-0.016) | -1.8k (-0.014) | -1.1k (-0.008) | +0.0k (+0.000) |
| A3_WTD_H2.0 | +0.0k (+0.000) | -0.7k (-0.007) | +0.2k (+0.003) | +0.0k (+0.000) |
| A4_WTD_B1.5 | -3.1k (-0.032) | -3.6k (-0.032) | -2.3k (-0.020) | +0.0k (+0.000) |
| B1_CONS2 | -5.1k (-0.040) | -7.8k (-0.019) | -3.8k (-0.001) | +2.2k (+0.116) |
| B2_CONS3 | -4.1k (-0.037) | -7.7k (-0.033) | -0.1k (+0.011) | -6.7k (-0.037) |
| C1_DD20_1.5 | +0.0k (+0.007) | -11.2k (-0.065) | -9.8k (-0.035) | -10.5k (-0.054) |
| C2_DD40_1.5 | -2.3k (-0.003) | -7.7k (-0.021) | -11.6k (-0.041) | -38.7k (-0.224) |
| C3_DD60_1.5 | -6.4k (-0.038) | -12.3k (-0.051) | -11.7k (-0.042) | -49.4k (-0.310) |
| C4_DD40_1.0 | -4.8k (-0.024) | -15.7k (-0.064) | -12.5k (-0.026) | -43.5k (-0.263) |
| D1_STRESS2D | +0.8k (+0.009) | -3.9k (-0.011) | -9.2k (-0.054) | -9.1k (-0.027) |
| E1_UP_DD40 | +3.4k (+0.007) | +8.3k (+0.034) | +6.7k (-0.002) | +4.9k (+0.021) |
| E2_UP_WTD1.5 | +1.6k (+0.016) | +1.8k (+0.009) | +1.1k (+0.004) | +0.0k (+0.000) |

## Table 5 - gates (T = pass)
| cell | G1 | G2 | G3 | G4 | G5 | G6 | G7 | verdict |
|---|---|---|---|---|---|---|---|---|
| A1_WTD_H1.0 | F | T | F | T | F | F | F | DEAD |
| A2_WTD_H1.5 | F | T | F | T | F | F | F | DEAD |
| A3_WTD_H2.0 | F | T | F | T | F | F | F | DEAD |
| A4_WTD_B1.5 | F | T | F | T | F | F | F | DEAD |
| B1_CONS2 | F | T | F | T | F | F | F | DEAD |
| B2_CONS3 | F | T | F | T | F | F | F | DEAD |
| C1_DD20_1.5 | F | F | F | F | T | F | F | DEAD |
| C2_DD40_1.5 | F | T | F | F | T | F | F | DEAD |
| C3_DD60_1.5 | F | T | F | F | F | F | F | DEAD |
| C4_DD40_1.0 | F | F | F | F | F | F | F | DEAD |
| D1_STRESS2D | F | T | F | F | T | F | F | DEAD |
| E1_UP_DD40 | T | T | T | F | F | T | F | CONTROL (direction NOT OK) |
| E2_UP_WTD1.5 | T | T | T | F | T | T | F | CONTROL (direction NOT OK) |

## Trade-off line, plain (W20F = 20 worst weeks, 129 other weeks; raw / lot-matched)
- Best de-risk by W20F: C4_DD40_1.0 (DD40, 1.0 SDW; halves lots 52% of the time): own-sorted worst-20 -2,793k vs -3,534k (+741k = +$37k per bad week saved), but costs -21.9k/wk in the 129 good weeks; lot-matched +/- -2.3k given / -0.4k saved. In words: "these rules would have turned the 20 worst weeks from -3,534k to -2,593k (C4, on the fixed set) and cost $21.9k/wk in the other weeks" - but a uniform 0.726x would have given most of that (LM saved only -0.4k/wk). Same for C2_DD40_1.5: W20F -3,534k -> -2,723k, costs -16.3k/wk in good weeks; LM saved +7.3k/wk per bad week vs LM given -2.6k per good week (positive net LM on W20F, but PRE W20P LM -65k and HOLD LM worst-5 -29k: not stable).
- B1_CONS2: W20F -3,534k -> -2,792k (+742k), costs -11.9k/wk in good weeks; LM +17.7k per bad week vs -3.9k per good week; the best LM trade-off on the all-window set, but PRE placebo rank is 0.45 (dSharpe) / 0.87 (LM W20P).
- Week-to-date rules (A1-A4) fire in only 1-8% of entries; A2-A4 do nothing in the worst weeks beyond uniform scaling (LM W20F gain -33k..-101k); A4 (block until Monday) makes PRE maxDD worse (-495k vs -409k) and has rank 0.00 on both placebo statistics (in the wrong direction: the placebo shifts do better): after a -1.5 SDW week-to-date the rest of the week is NOT worse than usual (HOLD raw +3.4k, +1.9k/wk for A1: the stack tends to recover within the week).

## Stability / direction
- Direction (E controls): size-up beats uniform scaling in PRE (dSharpe +0.036/+0.021, ranks 0.98-0.99) - i.e. the realised-state drawdown/week-to-date carry a (mild) mean-reverting component in PRE, not momentum - but the effect disappears in HOLD (dSharpe -0.006/-0.020) and in X (+0.001/+0.015, tiny). DIRECTION-OK flags are in Table 5 (both controls beat their de-risk twin). This is consistent with de-risking after losses being wrong-signed, not a tradable result (the stack would hold more lots on its worst days: E1 PRE worst week -366k vs -307k base).
- HOLD for the de-risk cells is mildly positive for A/B rules (dSharpe +0.004..+0.040) and negative for C/D rules (-0.015..-0.085): no rule family is positive in all windows. Year-by-year dSharpe: B1_CONS2 -0.040/-0.019/-0.001/+0.116 (2023/24/25/26, 5 weeks), C2 -0.003/-0.021/-0.041/-0.224. 2023 span: no de-risk cell has dSharpe > 0 except C1 (+0.008), C2 (+0.002) and D1 (+0.002), all of which fail PRE.
- Best-of-60 null: p95 of the max placebo dSharpe is +0.02..+0.08 and of LM W20P gain 84k..446k; no de-risk cell reaches either.

## Disclosures
- PRE, HOLD and X were scored in ONE run (stk_c_run.py, run once after the prereg was hashed); there was no staged PRE-then-HOLD look, so the logged-holdout step (s48score.log_holdout_look) was NOT used. No selection was made between PRE and HOLD (all 13 cells fixed in the prereg; nothing was re-run or re-parameterised), and the verdicts are 11 DEAD on PRE gates regardless of HOLD. The per-cell HOLD columns are therefore descriptive. Trials ledger: 13 cells appended.
- Before the run, the only output was the identity check (m = 1 reproduces the unchanged stack to 0.0 $, 19,898 trades, 149 weeks); no cell number was seen before the prereg hash.
- The 'ex-post worst-20' bias of "saved in bad weeks" is stated above; the LM and placebo statistics are the ones used for gates.
- Caveats: realised P&L is attributed at exit, state at entry; open trades are never resized (a mid-week halve does not shrink the position already in the market); the weekly cap/sweep is not re-simulated for the size-up cells; the exit-reason proxy for D1.

## Files
- Prereg l2vast/ds3/prereg/STK_C_prereg.md (+ .sha256 = 2905f01ef598f9bf68fa7f8c169825f4a00a11b94807a1ecf285804e2d788144). Code l2vast/ds3/code/stk_c/ (stk_c.py, stk_c_run.py, stk_c_report.py). Outputs l2vast/ds3/out/stk_c/: stk_c_results.json (all metrics, gates, yearly), stk_c_weekly_all.csv (all 149 weeks, base + 13 cells), **stk_c_pre_weekly.parquet** (PRE-only per-cell weekly series: 74 weeks x base + 13 cells, for the combine step F).
