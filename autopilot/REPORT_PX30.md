# REPORT PX30

**NO - weekend-gap fade ensemble (NQ ES RTY GC CL ZN, equal vol, fresh pre-registration), primary thr 0.25 / N=2 fade: additive uplift at 20% clean/H1/H2 0.11/-0.31/0.19 (all-in 0.07), bootstrap lo -0.07, plateau 0.50, wd corr 0.57; SMALL-SAMPLE (80 pair-window trades); standalone Sharpe pair window 0.72, 2013-26 0.59; replication legs holding 2 of 3 (H0 fail, ES/RTY PASS, alt-month PASS); FOUND 0. ERA FLAG: positive pre-2023.**

Cure attempt for the weekend-gap fade lead (T1b/Z3/W6/RW6/V3). Parent failure: H1 uplift negative, bootstrap lo < 0, plateau, small sample. Code ap_pd1_run.py / ap_pd1_doc.py (prefix ap_pd*), outputs outputs/autopilot/pd1/. Runtime 70 s (4-worker pool).

## Pre-registration and span honesty
Registered in PREREG_AUTOPILOT.md ("PX30", before any run): fixed rule (Monday gap >= thr x ATR20, first N 30-min bars confirm the gap direction, fade at the open of bar N+1, exit at the open of the last bar of the label day, no stop), fixed ensemble weights (equal $7,000 per ATR20 risk per instrument, i.e. equal volatility; no optimisation), 9-cell grid thr {0.1875,0.25,0.3125} x N {1,2,3}, primary cell declared in advance (thr 0.25, N 2, grid centre), exact plateau (4 one-parameter neighbours, >= 3 of 4 keep >= 75% of all-in uplift at 20%), replication legs defined up front.
**Non-virgin spans (disclosure).** The parents read clean, H1 and H2 for T1_0.25_{1,2,4}_fade on the same six markets (T1b), and H1/H2 for the daily-bar variants (Z3/W6/V3/RW6). Therefore clean, H1 and H2 are NON-VIRGIN for this lead; H1/H2 numbers here cannot support FOUND by themselves. The pre-declared primary avoids a new selection step, but its neighbours thr 0.1875/0.3125 and N=3 are new cells on already-seen data. Near-virgin sources: H0 (2023-02-10..07-31, never scored for the parents), the alternating-month split (fixed cell), the ES+RTY sleeve (NOT independent: ES and RTY were in the parents' pooled selection). Newest live weeks: data ends 2026-10-14, nothing newer than the parents' read (n/a). No parameter was chosen on H1/H2.

Fill model: market entry at the open of bar N+1 (30-min bars, back-adjusted), time exit at the open of the last bar of the label day, no stop, one position per instrument per Monday; slippage 1 tick/side + $4.36/contract round trip, 2x slippage = 2 ticks/side; extra round trip when a roll falls inside the trade. Baseline B.Cfg(wk_floor=8, wk_loss_pb=None) in a clean process (clean/H1/H2 1.46/2.83/2.30).

## Grid (all 9 cells shown for transparency; selection is clean-only)
| cell | trades pair win | clean eligible | Sh clean | Sh 2013-22 | yrs>0 | uplift@20% clean | H1 | H2 | all-in |
|---|---|---|---|---|---|---|---|---|---|
| T1_0.1875_1_fade | 118 | False | 0.56 | 0.52 | 7 | 0.07 | -0.15 | 0.17 | 0.07 |
| T1_0.1875_2_fade | 110 | True | 0.58 | 0.55 | 8 | 0.08 | -0.41 | 0.15 | 0.03 |
| T1_0.1875_3_fade | 112 | False | 0.41 | 0.50 | 7 | 0.04 | -0.29 | 0.10 | 0.02 |
| T1_0.25_1_fade | 88 | True | 0.87 | 0.56 | 7 | 0.12 | -0.11 | 0.20 | 0.11 |
| T1_0.25_2_fade | 80 | True | 0.79 | 0.59 | 7 | 0.11 | -0.31 | 0.19 | 0.07 |
| T1_0.25_3_fade | 83 | False | 0.65 | 0.54 | 6 | 0.08 | -0.28 | 0.14 | 0.05 |
| T1_0.3125_1_fade | 69 | True | 0.84 | 0.58 | 9 | 0.11 | -0.32 | 0.17 | 0.07 |
| T1_0.3125_2_fade | 68 | True | 0.85 | 0.62 | 9 | 0.12 | -0.34 | 0.19 | 0.08 |
| T1_0.3125_3_fade | 70 | True | 0.75 | 0.58 | 8 | 0.10 | -0.27 | 0.14 | 0.06 |

Clean-only best-of-9 (eligibility: weekly Sharpe > 0 in both clean halves and >= 40 pair-window trades): T1_0.25_1_fade. Primary: T1_0.25_2_fade, eligible True.

## Standalone and own timing-destroyed null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| T1_0.25_2_fade | 0.59 | 7 | 0.79 | -1.86 | 1.30 | 0.72 | 0.59 | 0.66 | 0.96 | 0.30 | 0.99 |

SMALL-SAMPLE FLAG: 80 trades in the pair window (< 100); 2013-22 trades 167. Long-history Sharpe next to it: 2013-22 0.59, 2013-26 0.59, positive in 7 of 10 dev years. Note the own-null p95 (pair window) is 0.66 against real 0.72 (rank 0.96).

## Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk; k = 9.1 at 100%)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| T1_0.25_2_fade | 9.1 | 10% | 0.06 | -0.15 | 0.14 | 0.05 | 8 | -0.03 | 0.08 | 0.57 | 0.10 | NO |
| T1_0.25_2_fade | 9.1 | 20% | 0.11 | -0.31 | 0.19 | 0.07 | 15 | -0.07 | 0.08 | 0.57 | 0.10 | NO |
| T1_0.25_2_fade | 9.1 | 30% | 0.14 | -0.47 | 0.17 | 0.07 | 23 | -0.12 | 0.08 | 0.57 | 0.10 | NO |
| T1_0.25_2_fade | 9.1 | 50% | 0.16 | -0.78 | 0.06 | 0.01 | 38 | -0.26 | 0.08 | 0.57 | 0.10 | NO |

## Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| T1_0.25_2_fade | 10% | -5.0 | 2.3 | 8.6 | 17.8 | 10/10 | 10/9 | NO |
| T1_0.25_2_fade | 20% | -9.9 | 4.6 | 17.2 | 29.2 | 20/20 | 18/18 | NO |
| T1_0.25_2_fade | 30% | -14.9 | 6.9 | 25.2 | 38.1 | 30/30 | 26/25 | NO |
| T1_0.25_2_fade | 50% | -24.8 | 3.5 | 36.1 | 55.8 | 47/49 | -2/20 | NO |

## Plateau, 2x slippage, alternate baseline
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| T1_0.25_2_fade | 0.07 | 4 | 0.50 | 0.03 / 0.06 | 0.10 / -0.32 / 0.18 / 0.07 | 0.69 | 0.11 / -0.22 / 0.19 / 0.09 |

Neighbour all-in uplifts @20%: thr 0.1875: 0.03, thr 0.3125: 0.08, N 1: 0.11, N 3: 0.05.

## Selection-corrected null (100 replicates, full selection pipeline re-run on timing-destroyed versions of all 9 cells)
Real clean-selected cell T1_0.25_1_fade: clean standalone Sharpe 0.87 vs null selected-cell median 0.86 / p95 1.60 (rank 0.51); clean additive uplift @20% 0.12 vs null median 0.15 / p95 0.30 (rank 0.36; primary rank 0.35). Chance of clearing the +0.10 uplift gate on clean, H1 and H2 together under the null selection: 1% of replicates (single run: 100 reps, so the resolution is 1%). Reading: the clean-span standalone Sharpe is not distinguishable from what a selected random-timing Monday-to-close trade earns in this window (clean is a bull sample, a random-side null still reaches median 0.86); the gate-relevant evidence is the pair-window own-null rank above plus the replication legs.

## Replication legs (same sign and >= 50% of the primary's clean uplift 0.11 at 20%)
- H0 (2023-02-10..2023-07-31): 1 trade(s) in the window across six markets (Monday gaps >= 0.25 ATR with confirmation are rare); additive uplift 0.008, pair weekly Sharpe 0.67. Verdict: fail (degenerate sample, not evidence either way).
- ES/RTY 2023-26 cross-instrument (ES+RTY sleeve, own clean scale; not independent of the parents' selection, 23 trades): uplift clean/H1/H2/all 0.22/-0.29/0.22/0.15. Verdict: PASS. The strength sits in ES/RTY only; NQ leg 0.02/-0.09/0.01, GC+CL+ZN 0.01/-0.39/0.16; the 2013-22 Sharpe of RTY is -0.03 (2017-22 only) and GC is negative in the pair window.
- Alternating-month split (pair window, k fixed from clean): | direction | fixed primary: select-span uplift | read-span uplift | best-of-9 on select span | its select uplift | its read uplift |
|---|---|---|---|---|---|
| odd->even | 0.09 | 0.09 | T1_0.25_1_fade | 0.13 | 0.12 |
| even->odd | 0.09 | 0.09 | T1_0.3125_2_fade | 0.14 | 0.05 |
Verdict: PASS for the fixed primary (both parities positive; select-within-split also reported above).
| group | n trades pair window | standalone Sh clean | pair win | 2013-26 | 2013-22 | add uplift @20% clean | H1 | H2 | all-in |
|---|---|---|---|---|---|---|---|---|---|
| ES+RTY | 23 | 1.28 | 1.09 | 0.51 | 0.26 | 0.22 | -0.29 | 0.22 | 0.15 |
| NQ | 15 | 0.25 | 0.41 | 0.29 | 0.25 | 0.02 | -0.09 | 0.01 | 0.01 |
| GC+CL+ZN | 42 | 0.34 | 0.39 | 0.57 | 0.88 | 0.01 | -0.39 | 0.16 | -0.01 |
| ES | 11 | 1.21 | 1.08 | 0.60 | 0.44 | 0.20 | -0.22 | 0.17 | 0.14 |
| RTY | 12 | 1.32 | 1.04 | 0.31 | -0.03 | 0.23 | -0.36 | 0.26 | 0.16 |
| GC | 11 | -0.72 | -0.69 | -0.12 | 0.09 | -0.18 | -1.48 | -0.05 | -0.33 |
| CL | 20 | 0.77 | 0.44 | 0.58 | 0.87 | 0.10 | -0.67 | -0.37 | -0.19 |
| ZN | 11 | 0.35 | 0.42 | 0.37 | 0.41 | 0.01 | 0.07 | 0.11 | 0.03 |

## ERA FLAG (reported, not gating): positive pre-2023
Price ratio (2013-22 / 2023-26 median raw price, six markets) 0.59. Weekly Sharpe 2013-22: gross 0.68, net at fixed cost 0.59, net at price-scaled cost 0.63. Per trade ($, at $7,000 per ATR20 risk): 2013-22 gross 1,253 / net fixed 1,080 / net price-scaled 1,151; 2023-26 gross 1,971 / net fixed 1,869 / net price-scaled 1,911. The edge is cost-insensitive (about 1,000+ per trade against a cost of ~100-200) and is positive in the pre-2023 era, so the failure is not a cost-era effect; it is a small-sample, H1-reversal and correlation-with-worst-weeks problem.

## Insurance metric set (sleeve scaled; pair+30% add vs pair)
| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| T1_0.25_2_fade | clean | 0.79 | 718,886 | -95,096 | -47,906 | -26,130 | 129,346 | 3.71 | 5.56 | 5 | 1.60 | -81,874 | -78,736 | 247,894 | 6.24 | 44 | 1.46 | -81,874 | -78,736 | 280,110 |
| T1_0.25_2_fade | H1 | -1.86 | -238,911 | -133,449 | -95,379 | -82,386 | 256,649 | -2.02 | -0.93 | 25 | 2.36 | -80,921 | -79,604 | 152,927 | 3.41 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| T1_0.25_2_fade | H2 | 1.30 | 875,950 | -86,474 | -76,337 | -65,230 | 285,509 | 7.47 | 3.07 | 19 | 2.47 | -101,559 | -93,433 | 225,317 | 4.54 | 47 | 2.30 | -82,524 | -81,089 | 217,425 |
| T1_0.25_2_fade | all | 0.72 | 1,355,925 | -133,449 | -74,438 | -54,116 | 324,887 | 2.98 | 4.17 | 11 | 1.92 | -101,559 | -82,586 | 247,894 | 12.47 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |

## Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| T1_0.25_2_fade | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | fail (0.50) | fail | fail (0.57) | NO |

Replication: 2 of 3 available legs hold; FOUND-PENDING would additionally require all 7 gates. Gates failing: G3 uplift (H1 {f(A[0.2]["H1_dsharpe"])}; 10% share clean {f(A[0.1]["clean_dsharpe"])}), G4 bootstrap, G5 plateau, G5 2x slip, G6 wd corr. Own-null (pair window) PASS.
The positive worst-decile correlation (0.57) matters: in the pair's worst weeks the gap-fade sleeve loses with it, so it is not a hedge and does not help the insurance question (constant-risk framing is NO at every share).

## Executability and margin
NT8 spec: on each Monday label day (Sunday 18:00 ET open) per instrument compute gap = (first bar open - Friday last-bar close)/ATR20(20 prior label days, daily true range), require |gap| >= 0.25 and the first 2 30-min bars both closing beyond the open in the gap direction, then a market order against the gap at the open of the 3rd bar (Sunday ~19:00 ET); exit by market at the open of the last 30-min bar of the label day. Instruments: NQ ES RTY GC CL ZN at NinjaTrader Brokerage via Rithmic (all CME/CBOT/NYMEX/COMEX), fills in Sunday-evening thin liquidity (modelled at 1 tick/side; real Sunday slippage can exceed it, the 2x test covers 2 ticks). The NQ leg nets against the pair's NQ positions only if the pair is flat (it is rarely trading Sunday evening); library class NQ_INTRADAY (conservative). Contracts at 20% share (median ATR20): NQ: 1.9 ct x $17,000 = $31,772, ES: 3.7 ct x $12,000 = $44,843, RTY: 6.1 ct x $7,000 = $42,974, GC: 2.9 ct x $11,000 = $31,758, CL: 5.9 ct x $7,000 = $41,630, ZN: 22.9 ct x $2,200 = $50,360.

Library: saved as PX30_gapfade_ens (volmatch, NQ_INTRADAY class, tag small-sample). UPD lines appended to GAPMAP_UPDATES.md.

Mechanism and structure dependence: thin Sunday-open flow overshoots then reverts; plausibly depends on current Sunday liquidity structure; no pre-2023 dependence found (positive pre-2023).
Multiplicity: 9 cells x 5% = 0.45 expected chance passes of a p95 null; the selection-corrected null above is the finer accounting.

DONE PX30
