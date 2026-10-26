# REPORT MONEY_GATES56 - gates 5 (exact +-25% plateau) and 6 (2x slippage) for three MONEY top-50 representatives (2026-10-17)

**Verdicts: (1) RY5_E1_K4_a0.25_sg+1: BELOW - fails gate 1 (basis): its sleeve E1 is the BASIS-VOID FVG family; the 4.37 Sharpe is the placement-order artifact, on executable order handling E1 is negative (net R/trade -0.03, standalone Sharpe -2.3/-0.6/-0.3 first-fill-wins). Gates 5 and 6 pass numerically on the frozen basis but are moot. (2) T3S1 fvg_n20 tf5: gate 5 passes on all-in Sharpe (8/10 = 80%) and fails on clean Sharpe (7/10 = 70%); gate 6 passes; PAIR-GRADE only on the all-in definition and it is NOISE under MONEY's best-of-N gate 3 (rank 0.95); call it BELOW (plateau on clean, gate 3). (3) T3S1 roc_n60 tf1 adx20: BELOW - plateau 5/10 = 50% fails; gate 6 passes (H2 net only $82k, Sharpe 0.35).**

Definitions (applied identically to both T3S1 books, B10 NT8-faithful harness v5_p1_common/b10_core, pre-specified before the runs): slippage convention of the pair (0.5 pt per round trip = 1 tick/side) is the base for BOTH books - the library series MONEY ranked carry NO slippage (pts exactly +-60, commission only). Gate 5 = share of the exact +-25% neighbours (every numeric parameter x0.75 and x1.25, integers rounded: signal n, tf, EMA length, confirmation parameters, bracket 60 pt stop+target) whose standalone weekly Sharpe is >= 75% of the base book's; pass if >= 75% of neighbours. Metric printed for all-in (2023-08..2026-10-16) and for clean. Gate 6 = standalone net > 0 on clean, H1 and H2 at 2 ticks/side (1.0 pt RT). Net in $ at the book's native size (10 NQ at R=$12,000). V5 P1/P2 judged the same family on ADDITIVE uplift >= +0.10 at 20% share with 2x slippage and on mean-uplift retention, which is a different (stricter) criterion; the standalone results below are consistent with it (standalone net stays positive at 2x slippage, the additive uplift does not clear +0.10 on every span).

## (2) T3S1_G_G_v1/G_G6_fvg_n20_tf5_e200_t5 (5-min FVG trend, EMA200, 5-min MTF confirmation, market entry, 60/60)
Base (slippage 0 = as MONEY ranked / 1 tick per side / 2 ticks per side), Sharpe clean/H1/H2/all and net $k clean/H1/H2/all:
- 0 tick: trades 2865; Sharpe 2.55 / 4.27 / 2.00 / 2.65; net $k 1,378 / 612 / 506 / 2,497
- 1 tick/side: trades 2865; Sharpe 2.28 / 4.02 / 1.73 / 2.39; net $k 1,234 / 572 / 437 / 2,243
- 2 ticks/side: trades 2865; Sharpe 2.02 / 3.76 / 1.46 / 2.12; net $k 1,090 / 533 / 368 / 1,990

Plateau (1 tick/side; retention = neighbour Sharpe / base Sharpe):
| neighbour | trades | all-in Sharpe | retention all-in | clean Sharpe | retention clean |
|---|---|---|---|---|---|
| stop45 | 3532 | 1.89 | 79% | 1.73 | 76% |
| nx0.75 | 2746 | 2.21 | 93% | 2.09 | 91% |
| ema150 | 2864 | 2.34 | 98% | 2.21 | 97% |
| ema250 | 2865 | 2.39 | 100% | 2.28 | 100% |
| nx1.25 | 2917 | 2.12 | 89% | 2.00 | 88% |
| tf6 | 2684 | 1.06 | 44% | 1.38 | 61% |
| tf4 | 3095 | 2.24 | 94% | 1.62 | 71% |
| stop75 | 2542 | 1.02 | 43% | 1.12 | 49% |
| mtf6 | 2783 | 2.33 | 98% | 1.99 | 87% |
| mtf4 | 2952 | 2.16 | 90% | 2.07 | 91% |

Gate 5: all-in 8/10 = 80% (PASS); clean 7/10 = 70% (FAIL).
Gate 6: 2 ticks/side net $k clean/H1/H2 = 1,090 / 533 / 368 -> PASS.

## (3) T3S1_G_G_v1/G_G4_roc_n60_tf1_e200_adx20 (1-min ROC 60, EMA200, ADX>20, market entry, 60/60)
Base (slippage 0 = as MONEY ranked / 1 tick per side / 2 ticks per side), Sharpe clean/H1/H2/all and net $k clean/H1/H2/all:
- 0 tick: trades 3389; Sharpe 2.50 / 2.74 / 1.04 / 2.25; net $k 1,703 / 522 / 247 / 2,472
- 1 tick/side: trades 3389; Sharpe 2.26 / 2.50 / 0.70 / 1.98; net $k 1,529 / 475 / 164 / 2,168
- 2 ticks/side: trades 3389; Sharpe 2.01 / 2.26 / 0.35 / 1.71; net $k 1,354 / 427 / 82 / 1,864

Plateau (1 tick/side; retention = neighbour Sharpe / base Sharpe):
| neighbour | trades | all-in Sharpe | retention all-in | clean Sharpe | retention clean |
|---|---|---|---|---|---|
| stop45 | 4521 | 0.93 | 47% | 0.77 | 34% |
| nx1.25 | 3355 | 0.45 | 23% | 0.37 | 16% |
| nx0.75 | 3470 | 0.64 | 32% | 0.56 | 25% |
| ema150 | 3405 | 1.70 | 86% | 1.77 | 79% |
| ema250 | 3393 | 2.17 | 109% | 2.79 | 124% |
| adxthr25 | 2442 | 1.64 | 83% | 1.31 | 58% |
| adxper18 | 2687 | 1.31 | 66% | 0.95 | 42% |
| stop75 | 2907 | 0.74 | 37% | 0.76 | 34% |
| adxthr15 | 4037 | 2.05 | 103% | 1.55 | 69% |
| adxper10 | 3918 | 1.78 | 90% | 1.52 | 67% |

Gate 5: all-in 5/10 = 50% (FAIL); clean 2/10 = 20% (FAIL).
Gate 6: 2 ticks/side net $k clean/H1/H2 = 1,354 / 427 / 82 -> PASS.

## (1) RY5_E1_K4_a0.25_sg+1
- What it is: the FVG E1 limit-order sleeve (tf3+tf5+tf15 pullback members, tick-replay fills) with each trade's size multiplied by clip(1 + a*z, 0.5, 1.5), z = clip((pbar-0.5)/0.1,-1,1) from the K4 ensemble (a = 0.25). REPORT_RY5: paired CI of the all-in uplift difference vs unmodified E1 is [-0.023, +0.037]: the K4 factor adds nothing (+0.03 standalone Sharpe: 4.37 vs 4.34 for E1 alone; the sg=-1 control is 4.22).
- **Basis (decisive):** E1's trades come from independently replayed resting limit orders, then sequenced by `res[i,0]==1 and pl[i] >= busy` in placement order (ap_fv_e1.trades): the look-ahead that AMENDMENT FVG-REALIZABLE voids (REPORT_ICT s. 26-27, REPORT_FVG_REALIZABLE). On executable order handling E1 reads net R/trade -0.035 and standalone weekly Sharpe -2.26/-0.57/-0.30 (first-fill-wins), -1.47/+0.51/-0.16 (one at a time), -2.17/-0.54/-0.48 (newest replaces), -1.80/+0.34/-1.22 (stack 2); only the frozen placement-order row reads +4.2/+4.4/+5.2. The library book RY5 inherits that artifact (MONEY removed BASIS-VOID books at load, but RY5 is a derived book built on E1 trades and was not on the void list). **Gate 1 fails; BELOW (void basis). Gates 5/6 below are on the frozen (artifact) series for completeness only.**
- Gate 5 on the series as built: neighbours a x0.75/x1.25 (0.1875, 0.3125) and z width x0.75/x1.25 (0.075, 0.125): all four retain 99.8-100.1% of the all-in and clean Sharpe (4.36-4.37 all-in) - trivially, since the factor moves size by at most +-25% x z. The E1 parameter plateau (shared parameters +-25%, 16/16 in REPORT_ICT) is also a frozen-basis result. No executable neighbour set exists.
- Gate 6 on the series as built (2x slippage = +1 tick adverse on every entry and +1 tick on every non-target exit): Sharpe 3.03 / 3.39 / 4.50 (all-in 3.41), net $k 2,354 / 1,042 / 1,563 (native units): positive on every span; with the entry tick only 3.48/3.69/4.83.
- Drift/clock-matched null: not run. ap_null_dm.py serves the b2356 daily harness, the I-series and the B pipelines; the E1 sleeve is a two-sided intraday limit book (long share 50.1% tf3, 50.9% tf5, 52.1% tf15 - it is not long-only), so the drift argument does not apply, and any null built on the independent-replay sequencing would reproduce the artifact (the FVG depth-permutation null itself averaged +3.8 Sharpe under random depth). The honest test of this sleeve is the NT8 paper run (score_fvg_paper.py).
- Library action recommended to the owner of MONEY: mark RY5_E1_K4_* (and any book built on ap_fv_e1.trades / fill_FV_* sequencing) BASIS-VOID; the top-50 ranking changes accordingly.

## Summary
| book | gate 5 plateau | gate 6 2x slip | other | verdict |
|---|---|---|---|---|
| RY5_E1_K4_a0.25_sg+1 | trivial pass on the frozen series (K4 neighbours 100%) | pass on the frozen series | gate 1 FAIL: E1 basis-void; K4 adds +0.03 | BELOW |
| T3S1 G6 fvg_n20 tf5 e200 t5 | all-in 80% PASS, clean 70% FAIL | PASS ($1,090k / 533k / 368k) | MONEY gate 3 best-of-N rank 0.95 (NOISE); 1-tick Sharpe 2.39 vs 2.65 as ranked | BELOW (borderline; passes 5/6 only on all-in) |
| T3S1 G4 roc_n60 tf1 e200 adx20 | 50% FAIL (stop 45/75, n 45/75, ADX period 18 fail) | PASS ($1,354k / 427k / 82k; H2 Sharpe 0.35) | rank 0.51 (NOISE); 1-tick Sharpe 1.98 vs 2.25 as ranked | BELOW |
Code: ap_mg_gates.py (T3S1 books; results mg_gates_t3s1.pkl), ap_mg_ry5.py. 
DONE MONEY_GATES56

