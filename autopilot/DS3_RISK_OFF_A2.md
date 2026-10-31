# DS3_RISK_OFF_A2 - T-RISK-OFF, ORDER BOOK + PROGRESS/PATH families (agent RO-2, 2026-10-31)

Research only; no live/execution/chart change; UNTOUCHED never read (cache capped 20260206). Prereg `autopilot/RO2_RISK_OFF_prereg.md` sha256 `09c33504fc8756ac513aac571925f4bff3ee43c6108da55d9902f80749c5f1e1` (also in DECISIONS.md, written before any cell was scored). Code `l2vast/ds3/code/riskoff2/`, outputs `l2vast/ds3/out/riskoff/ro2/` (cell table in NTE-2's schema: `ro2_PRE_X_table.parquet`; per-day cell sums `cells/`; placebos `plc/`; recent look `recent_look.parquet`). NTE-2 writes DS3_RISK_OFF_A.md for the other families; the lead merges.

## Page 1 - the answer: NULL. Hold the original stop. Moving the stop on a book event or a path event loses against hold in the selection windows, in the recent windows and in the walk-forward re-selection chain; the one bit of structure (a few small-book cells positive in L6M, HOLD and L3M) is inside its MDE and not placebo-beaten.

1. **10,752 valid cells** (33 triggers x plain / book-WITH gate x 16 stop destinations x under-water / in-profit / always x min age 0/1/2/5 min; 12,672 grid cells before the invalid ones: BE-type destinations are undefined under water and a destination must be tighter than the original stop and >= 1 pt behind the last close), scored on identical entries against hold-the-original-stop, target unchanged, on the MEASURED stop basis (live 2.45; Native 1.28 and join-fix 0.5 beside), for the six live books K6 P6 U6 H6 M6 A6 (per planned lot = per contract on this single-entry base; the lot split and the lock engine are in section 8). Pooled over the six books: **36 of 10,752 cells are positive in PRE, 2,392 in X', 36 in both**; the median cell earns -1.06 pt/trade (order book) and -0.77 (path) over PRE+X'; the best pooled cell has t = 0.45.
2. **Multiplicity:** White reality check / Romano-Wolf over the cells of a family in PRE+X' (circular block bootstrap, 5-day blocks, 500 draws): L6 order book best-cell p = 0.99 (best MIC_B|HALF|IP|5, 0.053 pt/trade), L6 path p = 0.99 (best VEL_10+G|HALF|IP|5); **0 survivors in any of the 14 family x scope tests** (best per-book p: 0.35..1.00). Cumulative count: 12,672 grid cells x 7 scopes (UF_TRIALS side=riskoff_ro2); DEAD_CELLS gets 75,264 rows (program RISKOFF_RO2).
3. **Selection (PRE and X' only) and ONE recent look per group:** candidates = positive in both PRE and X' with >= 150 fires in each: L6 36, H6 375, M6 367, P6 104, U6 6, K6 4, A6 4. Placebo (200 random-tighten draws, same fire count, same time since entry, same book x month, same state and destination rule) was run for the top 150 per family at L6 and the top 30 per book and family (209 cell-scope rows); 111 were carried (random-tighten rank >= 0.95 in PRE+X'; note that random-time tightening is itself a heavy loser, -0.4 to -0.5 pt/trade, so beating it is a low bar; the bar is hold). Recent look at the 111 carried rows: **L6 pooled 0 of 36 positive in L6M** (median -0.56), M6 0/34, P6 0/22, A6 0/1, H6 6/12 in L6M but 1 in HOLD, U6 6/6.
4. **Tiers (honest):** CONFIRMED (carried, >= 0 in L6M and HOLD, L6M placebo rank >= 0.90) = **0** in both groups. LEAD = **2 families, 7 rows of near-duplicate variants, both inside MDE and not placebo-beaten in L6M** (section 6): U6 "60-s move against >= 20 pts -> stop to 1.5 ATR behind price" (+1.08 L6M, +1.29 HOLD, +2.4 L3M pts/trade, 138 fires in L6M, MDE 3.95, L6M rank 0.82) and H6 "imbalance flipped against (and the book is not WITH) -> MAE+15, in profit" (+0.52 L6M, MDE 1.9, rank 0.70; lock-engine stack -1.3k/wk [6.7] L6M, -2.2k PRE). Everything else DEAD.
5. **Walk-forward (the forward-facing answer):** re-pick the best of all cells on the trailing 6 months every month (>= 100 fires), apply it the next month (hold if none positive), 2024-04..2026-02: L6 order-book chain **-0.44**, path chain **-0.34**, all-cells **-0.48** pt/trade (L6M -0.06). Per book the chain is negative for every book except U6-all in the recent half-year (+0.2, noise on 1,700 trades). The "best of F" is not a rule.
6. **The directive's example, scored as a named extra pair cell (counted in the multiplicity):** moving K6's stop to MAE+10 when support is pulled z >= 2 after the trade has been -30 (under water): PRE -0.49, X' +0.33, L3M +0.71, L6M +0.37, HOLD +0.21 pt/contract/trade vs hold. It FAILS the PRE gate (negative in the selection windows), so the positive recent windows are not selection-legal and not a finding. In L6M it touches 656 of 1257 K6 trades (52%), avoids a full stop on 66% of the trades it touches and forfeits a target on 8.5%. The simple trigger without the MAE>=30 condition (PUL_2 -> MAE+10, under water) is -2.27 pt/trade in L6M at L6 (stack -30.9k/wk, MDE 20.7k).
7. **Equal risk (structure):** the worst-20-weeks factor (hold / rule on the lock-engine stack at live lots) of the canon cells is 0.83x to 1.12x - a stop move that loses 1 to 2 pt/trade does not cut the worst weeks enough to allow more lots; scaled to equal worst-20 the L6M stack delta stays at -17k to -39k $/wk for the canon cells. There is no "best risk-off rule overall" in these two families: **the best rule is hold the original stop** (factor 1.00).
8. **Why it loses (order of touch, MAEMFE):** two thirds of runners come back through entry before going to target, so a stop moved to BE / BE+k / lock X% / ATR / structure sits on the retest. Stops avoided are real (L6M, PUL_2 -> MAE+10 under water, 4525 touched trades: a full stop avoided on 2264 = 50% of them, 37 pts saved each, 84,317 pts) but the forfeited targets cost more (1226 = 27% of the touched trades, 77 pts each, -94,681 pts) and the rest (time exits hit by the moved stop) -2,526 pts: net -12,890 pts over 5,671 trades = -2.27 pt/trade. Section 7 gives the same bookkeeping for every canon cell (avoided 24-64% of the touched trades, forfeited 6-43%).

## 1. Setup and definitions
* Universe: library base-bracket trades of the six D6 live books (K6=KB, P6=PE, U6=SM, H6=HM, M6=MV, A6=PB), 20230401..20260206, 25,941 trades in the six books (44,370 in the store); decision grid = the THP/L2H 10-s cache (every 10 s of every open trade, 39.5 M rows, book features exactly as DS3_L2_FEATURE_DEFS.md). **P6 = library entry, not the 45-s confirmed entry** (see caveats). Windows: L3M 20251106.., L6M 20250801.., HOLD 20250701.., PRE 20240201..20250630, X' 20230401..20240131, all capped 20260206.
* Action = where the stop sits. A fired trigger moves the stop (live from the next second) to the destination if it is tighter than the original stop and >= 1.0 pt behind the last 10-s close (never to or through the market); first fire per trade; target unchanged; the exit second of the original trade is not re-scanned (original stands). Moved and original stops both fill at level minus c (live 2.45 headline, Native 1.28, join-fix 0.5); target = year correction; time exit 0.995; fee 0.242.
* Triggers (33 x gate): ORDER BOOK against - IMB_A (sided imb5 <= -0.3, 2 rows), IMB_B (flip: <= -0.2 now, >= +0.1 sixty s ago), DEL_A/B (60-s delta / volume <= -0.25 / -0.5 and 10-s delta < 0), PUL_2/PUL_3 (support pulled z >= 2 / 3: pulled_sup10, log1p, robust z vs the same ET 30-min bucket over the prior 6 months), WALL (largest-level-behind / median >= 3.5 within the last 6 rows, now <= 1.8), ICE_30/60 (ahead-side iceberg ratio >= 30 / 60), SWP_3/SWP_8 (sweeps against >= 3 in 10 s / >= 8 in 30 s), THICK_13/15 (total depth within 8 ticks >= 1.3 / 1.5 x normal), MIC_A/B (microprice against). PATH - PB_x_y (MFE >= x% of target, then a pullback >= y% of the MFE), VEL_v (60-s move against >= v pts), STL_n (no new MFE for n s), STLB_n (the same with the book against), MAER_r (MAE >= 30 and recovered >= r pts off the worst). **+G** = the trigger is suppressed when the book is WITH (imb5 >= +0.2, microprice with, delta60 > 0): the "support is holding, leave the stop alone" gate. Not built (no per-second store): absorption price, signal-bar extreme, FVG/OB edge, VWAP band, POC destinations; "book turning WITH" is used as the gate and as the re-widen condition, not as a tighten trigger.
* Destinations: BE, BE+2/4/8 ticks, MAE+5/10/15 pts (beyond the worst point), S1M / S5M (extreme of the last 5 completed 1-m / 3 completed 5-m bars, one tick beyond), BOOK (largest resting level behind price within 10 levels, >= 2x the median level, one tick behind), ATR1 / ATR15 / ATR2 (x 1-m ATR14 behind price), HALF (halfway to target), LOCK25 / LOCK50 (% of open profit).

## 2. Selection-window tables (PRE and X' only; pts/contract/trade vs hold; six live books pooled; live basis 2.45 unless named)
### By trigger (cells = destinations x states x ages x gate; fire = median share of trades the cell touches in PRE; both+ = cells positive in PRE and X' at the live basis)
| trigger | fam | cells | fire_PX | med_PX | best_PX | pos_live | pos_native | pos_join | best_join | bothpos |
|---|---|---|---|---|---|---|---|---|---|---|
| DEL_B | book | 328 | 16% | -0.646 | -0.162 | 0% | 0% | 1% | 0.044 | 0 |
| PUL_3 | book | 328 | 23% | -0.696 | -0.108 | 0% | 1% | 6% | 0.112 | 0 |
| MIC_B | book | 328 | 27% | -0.739 | 0.063 | 5% | 5% | 8% | 0.231 | 0 |
| IMB_A | book | 328 | 22% | -0.775 | -0.170 | 0% | 0% | 0% | -0.038 | 0 |
| MIC_A | book | 328 | 32% | -0.916 | -0.251 | 0% | 0% | 0% | -0.014 | 0 |
| ICE_60 | book | 328 | 43% | -0.998 | -0.378 | 0% | 0% | 0% | -0.109 | 0 |
| THICK_15 | book | 328 | 29% | -1.114 | -0.288 | 0% | 0% | 5% | 0.050 | 0 |
| DEL_A | book | 328 | 31% | -1.154 | -0.183 | 0% | 0% | 5% | 0.103 | 0 |
| THICK_13 | book | 328 | 36% | -1.179 | -0.380 | 0% | 0% | 5% | 0.098 | 0 |
| IMB_B | book | 328 | 42% | -1.254 | -0.401 | 0% | 0% | 5% | 0.072 | 0 |
| SWP_8 | book | 328 | 46% | -1.296 | -0.458 | 0% | 0% | 5% | 0.205 | 0 |
| PUL_2 | book | 328 | 43% | -1.307 | -0.549 | 0% | 0% | 0% | -0.031 | 0 |
| WALL | book | 304 | 46% | -1.340 | -0.286 | 0% | 5% | 5% | 0.272 | 0 |
| ICE_30 | book | 328 | 50% | -1.439 | -0.629 | 0% | 0% | 5% | 0.164 | 0 |
| SWP_3 | book | 328 | 51% | -1.458 | -0.541 | 0% | 0% | 5% | 0.226 | 0 |
| PB_75_50 | path | 312 | 13% | -0.087 | 0.035 | 9% | 53% | 68% | 0.231 | 0 |
| PB_75_25 | path | 328 | 20% | -0.091 | 0.097 | 12% | 60% | 65% | 0.395 | 20 |
| VEL_20 | path | 328 | 11% | -0.213 | -0.019 | 0% | 2% | 10% | 0.089 | 0 |
| MAER_15 | path | 328 | 18% | -0.307 | 0.108 | 2% | 7% | 16% | 0.426 | 0 |
| MAER_10 | path | 328 | 18% | -0.324 | -0.054 | 0% | 2% | 12% | 0.152 | 0 |
| MAER_5 | path | 328 | 18% | -0.348 | -0.054 | 0% | 1% | 11% | 0.114 | 0 |
| PB_50_25 | path | 328 | 34% | -0.554 | -0.294 | 0% | 0% | 11% | 0.165 | 0 |
| PB_50_50 | path | 312 | 27% | -0.558 | -0.294 | 0% | 0% | 0% | -0.039 | 0 |
| VEL_10 | path | 328 | 36% | -0.810 | 0.083 | 5% | 5% | 5% | 0.313 | 16 |
| STLB_1200 | path | 328 | 26% | -1.126 | -0.227 | 0% | 0% | 5% | 0.013 | 0 |
| PB_25_25 | path | 328 | 44% | -1.128 | -0.338 | 0% | 0% | 5% | 0.165 | 0 |
| PB_25_50 | path | 312 | 41% | -1.159 | -0.734 | 0% | 0% | 0% | -0.317 | 0 |
| STLB_600 | path | 328 | 32% | -1.263 | -0.189 | 0% | 5% | 5% | 0.128 | 0 |
| STL_1200 | path | 328 | 28% | -1.279 | -0.378 | 0% | 0% | 0% | -0.044 | 0 |
| VEL_5 | path | 328 | 47% | -1.299 | -0.211 | 0% | 5% | 5% | 0.276 | 0 |
| STL_600 | path | 328 | 35% | -1.318 | -0.289 | 0% | 0% | 5% | 0.143 | 0 |
| STLB_300 | path | 328 | 37% | -1.342 | -0.298 | 0% | 0% | 5% | 0.094 | 0 |
| STL_300 | path | 328 | 41% | -1.422 | -0.362 | 0% | 0% | 5% | 0.161 | 0 |

### By destination
| dest | cells | med_PX | best_PX | med_join | best_join | pos_live | bothpos |
|---|---|---|---|---|---|---|---|
| HALF | 480 | -0.292 | 0.083 | 0.097 | 0.313 | 7% | 16 |
| MAE15 | 792 | -0.701 | -0.054 | -0.481 | 0.025 | 0% | 0 |
| MAE10 | 792 | -0.845 | -0.089 | -0.557 | 0.015 | 0% | 0 |
| ATR2 | 792 | -0.926 | 0.097 | -0.542 | 0.328 | 2% | 12 |
| S5M | 792 | -1.051 | -0.133 | -0.688 | 0.033 | 0% | 0 |
| ATR15 | 792 | -1.061 | -0.069 | -0.594 | 0.214 | 0% | 0 |
| S1M | 792 | -1.071 | -0.065 | -0.627 | 0.165 | 0% | 0 |
| BE8 | 528 | -1.086 | 0.013 | -0.525 | 0.166 | 2% | 0 |
| BOOK | 768 | -1.093 | 0.108 | -0.476 | 0.426 | 1% | 0 |
| LOCK25 | 528 | -1.108 | 0.075 | -0.535 | 0.264 | 6% | 8 |
| MAE5 | 792 | -1.111 | -0.145 | -0.772 | -0.083 | 0% | 0 |
| BE4 | 528 | -1.133 | -0.047 | -0.531 | 0.103 | 0% | 0 |
| ATR1 | 792 | -1.143 | -0.083 | -0.621 | 0.184 | 0% | 0 |
| BE | 528 | -1.157 | -0.050 | -0.585 | 0.096 | 0% | 0 |
| LOCK50 | 528 | -1.171 | 0.019 | -0.535 | 0.228 | 2% | 0 |
| BE2 | 528 | -1.180 | -0.046 | -0.615 | 0.101 | 0% | 0 |

### The book-WITH gate (+G minus plain, paired on identical trigger / destination / state / age; 0.000 = the trigger already implies "against", the gate never bites)
| trigger | d_mean | frac_better | fire_plain | fire_gate |
|---|---|---|---|---|
| DEL_A | +0.000 | 0% | 7501.0 | 7501.0 |
| DEL_B | +0.000 | 0% | 3915.5 | 3915.5 |
| ICE_30 | -0.021 | 39% | 12016.0 | 11880.5 |
| ICE_60 | +0.059 | 88% | 10477.0 | 10233.0 |
| IMB_A | +0.000 | 0% | 5344.0 | 5344.0 |
| IMB_B | +0.000 | 0% | 10164.0 | 10164.0 |
| MAER_10 | +0.009 | 72% | 4442.0 | 4431.0 |
| MAER_15 | +0.004 | 56% | 4442.0 | 4431.0 |
| MAER_5 | +0.002 | 62% | 4442.0 | 4431.0 |
| MIC_A | +0.000 | 0% | 7738.0 | 7738.0 |
| MIC_B | +0.000 | 0% | 6397.0 | 6397.0 |
| PB_25_25 | -0.008 | 23% | 10659.5 | 10642.5 |
| PB_25_50 | -0.002 | 35% | 9852.5 | 9837.5 |
| PB_50_25 | +0.001 | 42% | 8230.0 | 8208.0 |
| PB_50_50 | -0.003 | 22% | 6580.0 | 6569.0 |
| PB_75_25 | -0.002 | 26% | 4887.0 | 4868.0 |
| PB_75_50 | -0.004 | 14% | 3166.0 | 3159.0 |
| PUL_2 | +0.017 | 63% | 10296.0 | 10173.0 |
| PUL_3 | +0.046 | 80% | 5675.5 | 5418.0 |
| STLB_1200 | +0.000 | 0% | 6165.0 | 6165.0 |
| STLB_300 | +0.000 | 0% | 8991.0 | 8991.0 |
| STLB_600 | +0.000 | 0% | 7693.0 | 7693.0 |
| STL_1200 | +0.002 | 32% | 6821.0 | 6814.0 |
| STL_300 | +0.003 | 39% | 9939.0 | 9916.0 |
| STL_600 | -0.003 | 24% | 8513.0 | 8511.0 |
| SWP_3 | -0.008 | 34% | 12345.0 | 12292.0 |
| SWP_8 | +0.002 | 55% | 11157.0 | 11127.5 |
| THICK_13 | +0.040 | 84% | 8755.5 | 8628.5 |
| THICK_15 | +0.066 | 98% | 7098.0 | 6942.5 |
| VEL_10 | +0.000 | 46% | 8632.0 | 8619.0 |
| VEL_20 | +0.003 | 55% | 2596.0 | 2589.0 |
| VEL_5 | -0.001 | 46% | 11162.0 | 11145.0 |
| WALL | -0.002 | 49% | 11148.5 | 11122.0 |
The gate helps only where the trigger is not intrinsically "book against" (THICK_15 +0.066, PUL_3 +0.046, ICE_60 +0.059 pt/trade) and by far too little to turn any level positive. States (median cell): always -1.07, in-profit-only -0.91, under-water-only -0.84; min age 0/1/2/5 min: -0.98/-0.96/-0.95/-0.94: the state and age switches are second order.

## 3. Multiplicity, funnel and walk-forward
White RC / Romano-Wolf, PRE+X' (mean of per-trade day sums; family x scope):
| scope | fam | cells | best | best_mean | rc_p | studentised_p | survivors |
|---|---|---|---|---|---|---|---|
| L6 | book | 4896 | MIC_B/HALF/IP/5 | +0.053 | 0.99 | 0.99 | 0 |
| L6 | path | 5856 | VEL_10+G/HALF/IP/5 | +0.045 | 0.99 | 0.99 | 0 |
| KB | book | 4896 | PUL_3/HALF/IP/0 | +0.236 | 0.96 | 0.94 | 0 |
| KB | path | 5856 | PB_75_25/BOOK/IP/2 | +0.152 | 0.97 | 0.99 | 0 |
| PE | book | 4896 | MIC_A/HALF/IP/5 | +0.506 | 0.88 | 0.81 | 0 |
| PE | path | 5856 | VEL_10+G/HALF/IP/5 | +0.685 | 0.77 | 0.53 | 0 |
| SM | book | 4896 | PUL_3+G/BOOK/UW/0 | -0.398 | 1.00 | 1.00 | 0 |
| SM | path | 5856 | VEL_20+G/ATR2/UW/5 | +0.241 | 0.98 | 0.99 | 0 |
| HM | book | 4896 | IMB_A/BOOK/IP/2 | +0.687 | 0.85 | 0.85 | 0 |
| HM | path | 5856 | STL_600+G/HALF/IP/0 | +0.566 | 0.87 | 0.93 | 0 |
| MV | book | 4896 | MIC_B/HALF/IP/5 | +0.589 | 0.73 | 0.55 | 0 |
| MV | path | 5856 | PB_75_25/BOOK/IP/0 | +1.191 | 0.39 | 0.36 | 0 |
| PB | book | 4896 | MIC_B/HALF/IP/0 | +0.717 | 0.63 | 0.53 | 0 |
| PB | path | 5856 | STLB_300/HALF/IP/0 | +1.441 | 0.35 | 0.39 | 0 |

Funnel (rows are near-duplicates across age and gate variants):
| scope | cells | pos_PRE_and_X | candidates_n150 | placebo_listed | carried | recent_L6M_pos | L6M_and_HOLD_pos | CONFIRMED |
|---|---|---|---|---|---|---|---|---|
| ALL6 | 10752 | 36 | 36 | 36 | 36 | 0 | 0 | 0 |
| KB | 10752 | 4 | 4 | 4 | 0 | 0 | 0 | 0 |
| PE | 10752 | 160 | 104 | 60 | 22 | 0 | 0 | 0 |
| SM | 10752 | 29 | 6 | 6 | 6 | 6 | 6 | 0 |
| HM | 10752 | 391 | 375 | 59 | 12 | 6 | 1 | 0 |
| MV | 10752 | 407 | 367 | 40 | 34 | 0 | 0 | 0 |
| PB | 10752 | 20 | 4 | 4 | 1 | 0 | 0 | 0 |

Walk-forward best-of-F chain (each month: best cell by trailing-6-month mean, >= 100 fires, applied next month iff > 0; pt/contract/trade over the chain; 23 test months 2024-04..2026-02; L3M is a 3-month window, noisy):
| scope | fam | chain_all | chain_PRE | chain_HOLD | chain_L6M | chain_L3M | frac_hold |
|---|---|---|---|---|---|---|---|
| ALL6 | book | -0.444 | -0.487 | -0.352 | -0.335 | -0.170 | 0.000 |
| ALL6 | path | -0.338 | -0.373 | -0.263 | -0.276 | +0.646 | 0.043 |
| ALL6 | all | -0.482 | -0.676 | -0.067 | -0.059 | +0.287 | 0.000 |
| KB | book | -0.443 | -0.481 | -0.364 | -0.510 | +0.673 | 0.000 |
| KB | path | -0.777 | -0.788 | -0.754 | -0.933 | -0.320 | 0.000 |
| KB | all | -0.792 | -0.995 | -0.367 | -0.510 | +0.673 | 0.000 |
| PE | book | -1.125 | -0.843 | -1.735 | -1.704 | +0.711 | 0.000 |
| PE | path | -0.721 | -0.529 | -1.134 | -1.048 | +0.378 | 0.000 |
| PE | all | -1.038 | -0.584 | -2.017 | -2.014 | +0.773 | 0.000 |
| SM | book | -2.193 | -3.045 | -0.282 | -0.680 | -0.464 | 0.087 |
| SM | path | -2.051 | -2.419 | -1.223 | -0.599 | -0.198 | 0.000 |
| SM | all | -1.736 | -2.729 | +0.495 | +0.219 | +1.167 | 0.000 |
| HM | book | -1.098 | -1.160 | -0.966 | -1.176 | +0.505 | 0.000 |
| HM | path | -0.329 | -0.289 | -0.412 | -0.265 | +0.551 | 0.000 |
| HM | all | -0.764 | -0.501 | -1.315 | -1.266 | +0.352 | 0.000 |
| MV | book | -1.247 | -1.003 | -1.775 | -1.754 | -1.892 | 0.000 |
| MV | path | -0.600 | -0.492 | -0.832 | -0.857 | -0.557 | 0.000 |
| MV | all | -1.654 | -1.158 | -2.727 | -2.952 | -2.386 | 0.000 |
| PB | book | -1.076 | -0.806 | -1.662 | -1.706 | -1.958 | 0.000 |
| PB | path | -1.059 | -0.951 | -1.293 | -1.554 | -0.637 | 0.000 |
| PB | all | -0.867 | -0.690 | -1.249 | -1.246 | -1.958 | 0.000 |

## 4. Canon cells (named in the prereg before scoring) - the one recent look, live basis; stack = lock-engine D6 composite at live lots (K6 market, A6 market, others 70/30 integer, running-max locks, Native 1.28), $k/wk delta vs the stack as it is [MDE]
| cell | scope | PRE | Xp | L3M | L6M | HOLD | MDE_L6M | fire_L6M | usd_wk_L6M | avoided | forfeited | neutral | P_tgt_held | rand_rank_L6M | shuf_rank | join_L6M | stack_L6M | stack_HOLD | stack_PRE | factor |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PUL_2/MAE10/UW/0 | ALL6 | -1.21 | -0.44 | -1.34 | -2.27 | -2.05 | 2.60 | 80% | -20,326 | 2264 | 1226 | 138 | 91% | 0.12 | 0.00 | -1.80 | -30.9 [20.7] | -26.4 | -17.3 | 1.12 |
| PUL_2/MAE10/UW/0 | KB | -1.30 | +0.63 | -1.02 | -2.27 | -2.04 | 3.74 | 79% | -4,350 | 507 | 276 | 25 | 93% | 0.21 | 0.00 | -1.80 | -7.5 [10.3] | -6.1 | -4.5 | 1.00 |
| PB_50_25/LOCK50/IP/0 | ALL6 | -0.92 | +0.37 | -0.42 | -1.32 | -1.35 | 1.93 | 61% | -11,885 | 808 | 1475 | 138 | 98% | 0.46 | 0.00 | -0.76 | -23.4 [22.4] | -23.5 | -11.7 | 1.07 |
| MAER_10/MAE10/UW/0 | ALL6 | -0.30 | -0.29 | -0.90 | -0.95 | -0.99 | 1.09 | 51% | -10,585 | 1811 | 255 | 69 | 80% | 0.81 | 0.00 | -0.84 | -10.8 [13.6] | -9.4 | -4.2 | 0.83 |
| IMB_A/BE/IP/0 | ALL6 | -0.84 | -0.61 | -1.68 | -2.18 | -2.00 | 1.95 | 37% | -27,558 | 665 | 898 | 71 | 93% | 0.00 | 0.00 | -1.84 | -37.1 [21.7] | -35.4 | -11.5 | 1.02 |
| STLB_600/BE/IP/0 | ALL6 | -1.31 | -1.16 | -1.94 | -2.27 | -2.07 | 2.14 | 52% | -24,107 | 986 | 1232 | 193 | 97% | 0.01 | 0.00 | -1.78 | -39.1 [21.3] | -36.3 | -15.1 | 1.05 |
| VEL_10/ATR15/AL/0 | ALL6 | -1.46 | -0.53 | -1.82 | -2.36 | -2.02 | 2.42 | 88% | -28,013 | 2294 | 1205 | 202 | 95% | 0.69 | 0.02 | -1.87 | -35.3 [20.5] | -31.3 | -19.1 | 1.05 |
avoided / forfeited / neutral = trades touched whose moved stop was hit and the original trade went to the full stop / reached the target / timed out (L6M counts); P_tgt_held = P(target | tightened but held) among the touched trades whose moved stop was not hit. usd_wk = $/week at live lots, per-trade view (no lock engine). Canon names: PUL_2 = support pulled z >= 2; PB_50_25 = MFE >= 50% of target then 25% pullback; MAER_10 = MAE >= 30 and recovered 10 pts; IMB_A = imbalance flipped against; STLB_600 = no new MFE for 10 min with the book against; VEL_10 = 60-s move against >= 10 pts.

### The directive example family, PUL_2 & MAE>=30 (pair cells; K6 and ALL6; selection-legal columns PRE and X')
| cell | scope | PRE | X | L3M | L6M | HOLD | PRE_fire | L6M_fire | L6M_avoid | L6M_forf |
|---|---|---|---|---|---|---|---|---|---|---|
| PUL_2&MAE30/MAE5/UW/0 | ALL6 | -0.47 | -0.01 | -0.44 | -1.04 | -1.00 | 7574 | 3125 | 2107 | 461 |
| PUL_2&MAE30/MAE5/UW/0 | KB | -0.31 | +0.58 | +0.68 | -0.37 | -0.36 | 1617 | 686 | 458 | 91 |
| PUL_2&MAE30/MAE10/UW/0 | ALL6 | -0.23 | -0.08 | -0.17 | -0.53 | -0.56 | 7198 | 3016 | 2013 | 311 |
| PUL_2&MAE30/MAE10/UW/0 | KB | -0.49 | +0.33 | +0.71 | +0.37 | +0.21 | 1529 | 656 | 435 | 56 |
| PUL_2&MAE30/MAE15/UW/0 | ALL6 | -0.03 | -0.21 | -0.27 | -0.37 | -0.44 | 6686 | 2827 | 1841 | 200 |
| PUL_2&MAE30/MAE15/UW/0 | KB | -0.24 | -0.12 | +0.38 | +0.38 | +0.11 | 1429 | 629 | 409 | 34 |
| PUL_2&MAE30/ATR1/UW/0 | ALL6 | -0.34 | +0.20 | -0.97 | -1.22 | -1.11 | 7404 | 3070 | 2001 | 451 |
| PUL_2&MAE30/ATR1/UW/0 | KB | -0.35 | +0.53 | -0.51 | -1.24 | -1.05 | 1573 | 670 | 430 | 98 |
| PUL_2&MAE30/ATR15/UW/0 | ALL6 | -0.47 | +0.15 | -0.49 | -1.00 | -0.96 | 6925 | 2858 | 1787 | 340 |
| PUL_2&MAE30/ATR15/UW/0 | KB | -0.69 | +0.79 | +0.43 | -0.51 | -0.49 | 1467 | 626 | 389 | 66 |
| PUL_2&MAE30/S1M/UW/0 | ALL6 | -0.22 | +0.11 | -0.76 | -0.70 | -0.74 | 6594 | 2777 | 1814 | 477 |
| PUL_2&MAE30/S1M/UW/0 | KB | -0.50 | +0.12 | -0.06 | -0.60 | -0.47 | 1403 | 605 | 393 | 102 |
| PUL_2&MAE30/BOOK/UW/0 | ALL6 | -0.09 | +0.37 | -0.42 | -1.19 | -1.05 | 6599 | 2705 | 1844 | 653 |
| PUL_2&MAE30/BOOK/UW/0 | KB | -0.30 | +1.16 | +0.49 | -1.00 | -0.94 | 1399 | 602 | 414 | 143 |
K6 shows positive recent windows for MAE+10 / MAE+15 (+0.37 / +0.38 L6M) but negative PRE (-0.49 / -0.24): no selection-legal support; ALL6 is negative everywhere. Reported as the answer to the sentence, not as a lead.

## 5. Per-book verdicts (one verdict per book)
| book | carried | L6M_pos | L6M_and_HOLD_pos | best_carried_in_L6M | best_L6M | best_HOLD | best_MDE | verdict |
|---|---|---|---|---|---|---|---|---|
| K6 (KB) | 0 | 0 | 0 | none | n/a | n/a | n/a | DEAD: nothing carried (4 candidates, best p 0.96) |
| P6 (PE) | 22 | 0 | 0 | VEL_10+G/HALF/AL/0 | -0.22 | -0.29 | 1.55 | DEAD: 22 carried, 0 positive in L6M |
| U6 (SM) | 6 | 6 | 6 | VEL_20/ATR15/AL/1 | +1.08 | +1.29 | 3.95 | LEAD only (VEL_20 -> ATR1.5): +1.1 pt/trade, MDE 4, 138 fires, rank 0.82; stack +1.1k/wk [3.3] |
| H6 (HM) | 12 | 6 | 1 | IMB_A+G/MAE15/IP/5 | +0.52 | +0.44 | 1.92 | LEAD only (imb flip gated -> MAE+15 in profit): +0.5 [1.9], rank 0.70, HOLD +0.44; stack -1.3k/wk [6.7]; the ungated MAER_10 -> MAE+15 in profit is +0.10 L6M / -0.12 HOLD (stack +0.2k [1.3]) |
| M6 (MV) | 34 | 0 | 0 | PB_75_25/BE8/IP/0 | -0.78 | -0.77 | 1.76 | DEAD: PRE/X' positive (PB_75_25 -> lock25) flips to -0.84 L6M |
| A6 (PB) | 1 | 0 | 0 | MIC_B+G/S5M/UW/0 | -3.84 | -3.43 | 2.78 | DEAD: 1 carried, -3.8 L6M |

## 6. LEAD cells (not CONFIRMED) - state-machine versions (ratchet, re-widen) and the stack line
| cell | scope | why | once_PRE | once_X | once_L6M | once_HOLD | ratchet_L6M | rewiden_L6M | stack_PRE | stack_X | stack_L6M | stack_HOLD | rewiden_stack_L6M | factor |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| IMB_A+G/MAE15/IP/5 | HM | RECENT+ | +0.16 | +1.07 | +0.52 | +0.44 | +0.52 | +0.22 | -2.2 | +0.8 | -1.3 [6.7] | -1.2 | +0.2 | 0.99 |
| VEL_20+G/ATR15/AL/2 | SM | RECENT+ | +0.19 | +0.85 | +0.98 | +1.17 | +1.21 | +0.81 | -0.8 | -0.0 | +1.0 [3.3] | +1.0 | -0.1 | 1.04 |
| VEL_20/ATR15/AL/2 | SM | RECENT+ | +0.17 | +0.87 | +0.98 | +1.18 | +1.21 | +0.81 | -0.8 | -0.0 | +1.0 [3.3] | +1.0 | -0.1 | 1.04 |
| VEL_20+G/ATR15/AL/0 | SM | RECENT+ | +0.10 | +0.91 | +1.08 | +1.27 | +1.05 | +0.51 | -0.9 | -0.0 | +1.1 [3.3] | +1.0 | -0.1 | 1.04 |
| VEL_20+G/ATR15/AL/1 | SM | RECENT+ | +0.10 | +0.91 | +1.08 | +1.27 | +1.05 | +0.51 | -0.9 | -0.0 | +1.1 [3.3] | +1.0 | -0.1 | 1.04 |
| VEL_20/ATR15/AL/1 | SM | RECENT+ | +0.07 | +0.93 | +1.08 | +1.29 | +1.06 | +0.51 | -0.9 | -0.0 | +1.1 [3.3] | +1.1 | -0.1 | 1.04 |
| VEL_20/ATR15/AL/0 | SM | RECENT+ | +0.07 | +0.93 | +1.08 | +1.29 | +1.06 | +0.51 | -0.9 | -0.0 | +1.1 [3.3] | +1.1 | -0.1 | 1.04 |
| VEL_10+G/HALF/AL/0 | ALL6 | TOPL6 | +0.10 | +0.05 | -0.30 | -0.29 | -0.30 | -0.25 | -2.4 | -1.0 | -10.4 [9.5] | -9.2 | -9.0 | 1.07 |
| VEL_10+G/HALF/AL/1 | ALL6 | TOPL6 | +0.10 | +0.05 | -0.30 | -0.29 | -0.30 | -0.25 | -2.4 | -1.0 | -10.4 [9.5] | -9.2 | -9.0 | 1.07 |
| VEL_10+G/HALF/IP/1 | ALL6 | TOPL6 | +0.10 | +0.05 | -0.30 | -0.29 | -0.30 | -0.25 | -2.4 | -1.0 | -10.4 [9.5] | -9.2 | -9.0 | 1.07 |
| PB_75_25+G/LOCK25/IP/0 | MV | TOPBOOK | +0.47 | +1.14 | -0.84 | -0.91 | -0.92 | -0.92 | -0.2 | +0.5 | -1.1 [1.2] | -1.2 | -1.2 | 1.01 |
| PB_75_25+G/LOCK25/AL/0 | MV | TOPBOOK | +0.47 | +1.14 | -0.84 | -0.91 | -0.92 | -0.92 | -0.2 | +0.5 | -1.1 [1.2] | -1.2 | -1.2 | 1.01 |
| MAER_10/MAE15/IP/1 | HM | TOPBOOK | +0.29 | +0.06 | +0.10 | -0.12 | +0.10 | +0.08 | +0.4 | -0.4 | +0.2 [1.3] | +0.2 | +0.2 | 1.00 |
| MAER_15/MAE15/IP/0 | HM | TOPBOOK | +0.29 | +0.06 | +0.10 | -0.12 | +0.10 | +0.08 | +0.4 | -0.4 | +0.2 [1.3] | +0.2 | +0.2 | 1.00 |
| VEL_10+G/HALF/AL/2 | PE | TOPBOOK | +0.68 | +0.02 | -0.22 | -0.29 | -0.22 | -0.23 | -0.0 | +0.3 | -4.3 [8.0] | -4.3 | -4.3 | 1.02 |
| VEL_10+G/HALF/IP/2 | PE | TOPBOOK | +0.68 | +0.02 | -0.22 | -0.29 | -0.22 | -0.23 | -0.0 | +0.3 | -4.3 [8.0] | -4.3 | -4.3 | 1.02 |
once = first fire only (the grid); ratchet = tighten further when the trigger fires again at a tighter level; rewiden = go back to the original stop when the book has been WITH for 30 s (book triggers) or a new MFE is made (path triggers), re-arm after. Stack = lock-engine D6 composite delta $k/wk [MDE]. SM cells: 345 patched exits in the engine; the lock-engine view of U6 is +1.1k/wk L6M, +1.0k HOLD but -0.9k PRE and -0.0k X': the sign flips between windows, so LEAD at most.

## 7. Why the stop move loses: the order-of-touch bookkeeping (PRE+X', six books, first-fire, selection-legal)
| cell | window | fires | stops_avoided | pts_saved | targets_forfeited | pts_lost | neutral | P_target_if_held | delta |
|---|---|---|---|---|---|---|---|---|---|
| PB_50_25/LOCK50/IP/0 | PRE | 8711 | 2122 | 72.63 | 3632 | -46.94 | 376 | 99% | -0.92 |
| PB_50_25/LOCK50/IP/0 | X' | 3057 | 713 | 72.83 | 1087 | -47.87 | 336 | 97% | +0.37 |
| PUL_2/MAE10/UW/0 | PRE | 10582 | 5620 | 34.38 | 2545 | -80.02 | 324 | 89% | -1.21 |
| PUL_2/MAE10/UW/0 | X' | 3059 | 1505 | 38.48 | 706 | -78.60 | 251 | 87% | -0.44 |
| IMB_A/BE/IP/0 | PRE | 5575 | 1865 | 60.00 | 2055 | -59.87 | 277 | 93% | -0.84 |
| IMB_A/BE/IP/0 | X' | 2878 | 933 | 60.00 | 953 | -61.04 | 286 | 86% | -0.61 |
| VEL_10/ATR15/AL/0 | PRE | 12583 | 5954 | 34.75 | 3052 | -72.38 | 497 | 95% | -1.46 |
| VEL_10/ATR15/AL/0 | X' | 4290 | 1995 | 37.20 | 1029 | -69.60 | 449 | 90% | -0.53 |
| STLB_600/BE/IP/0 | PRE | 7593 | 2690 | 60.00 | 3000 | -59.86 | 495 | 97% | -1.31 |
| STLB_600/BE/IP/0 | X' | 3654 | 1242 | 60.00 | 1305 | -61.04 | 489 | 94% | -1.16 |
pts_saved / pts_lost are per event (mean over the cell's events). A stop move pays only if (avoided x saved) exceeds (forfeited x lost): saved is 13 pts (MAE+10 after recovering), 34-37 pts (MAE+10 / 1.5 ATR on a book or velocity trigger) or 60-73 pts (BE / lock 50 in profit) and lost is 46-106 pts; the touched trades avoid a full stop in 24-64% of cases and forfeit a target in 6-43%, which is where the sign is decided; the remaining part of each cell's delta is the touched trades whose original exit was a time exit.

## 8. Units, stack line and caveats
* Per planned lot = per contract here (single-entry hold-to-bracket base, all six books). The 70/30 split (F leg now, add on a 3-pt dip) and the integer half-up lots are only in the lock-engine stack line, which patches the moved exits into ss2_lib rows (exit second re-scanned from the decision, p0 += f1 - f0 with the engine's own formula). **Not patched: P6 rows whose entry is the 45-s confirmed one** (entry differs from the base-bracket trade; the cache has no path state at that entry), i.e. the stack line understates what a book rule does to P6 in NY-AM / NY-PM; P6 per-trade rows are on the library entry.
* Decision grid is 10 s (the cache); a stop move is live from the next second. Moves use the 10-s book snapshot at the decision second. wall_tgt / wall_stop are not carriers (data horizon; DS3_L2_FEATURE_DEFS.md). Features with 10-s or 60-s aggregation: see the feature definitions.
* Selection uses PRE and X' only; the recent columns were written to a sealed file and opened only for the carried and canon cells after the carry list was frozen (the file `recent_sealed.parquet`); the focus set (state machine, stack line) is a subset of the carried and canon cells.
* Comparators from the earlier programmes (cuts, not stop moves): THL loss rule A30/k3 -1.41 pt/trade L6M (cut at -30 with own-side pulled >= 3x a median level), THP profit rule B20 -0.49 (DS3_THL_L2.md). Stop moves in this report are in the same range or worse at the same state in the recent windows; the live path TH and the L2 health rules are not re-run here.
* BUG note for NTE-2: `code/ntexp2/ro_lib.py` `ctx()` builds the row->trade map with `np.repeat(arange(nT), re-rs)`; the cache is sorted by tid and `ro_start` is not monotone, so the map agrees with the true one on 0.015% of rows (fix used here: `tr[rs[c]:re[c]] = c`, verified against `tid.npy` on 100% of rows). Any table built on `X.tr` / `X.rdpos` / `X.E_r` before the fix is wrong.
* Export for the combinations: `out/riskoff/ro2/ro2_PRE_X_table.parquet` (NTE-2 schema: fam BOOK/PATH, trig with +G, dest sw1/sw5 = S1M/S5M, gate under/profit/always, age in seconds, scope ALL6 + six books; PRE and X' only, live basis); `cells/*.npz` hold per-day sums for every cell (all windows) for anyone who needs them.

## 9. Plain sentences (directive section D)
* Moving K6's stop to MAE+10 when support is pulled z >= 2 after the trade has been -30 earns +0.37 pt per contract per K6 trade in the last 6 months on 52% of trades (it avoids a full stop on 435 of the 656 it touches and forfeits a target on 56, 8.5%), but it was -0.49 in PRE: not a finding.
* The best risk-off rule overall in the order-book and path families is to hold the original stop; at equal worst-20-weeks no tested rule allows more than 1.12x lots, and every such rule still loses $17-39k/wk against the stack as it is in L6M (canon cells).
* Nothing in these two families goes to THP_POLICY.txt (profit/loss tighten rules): no CONFIRMED cell; the trigger features that would be needed (imb5_s, microprice offset, pulled_sup10 with the causal bucket z, maxlv_behind_rel/k, 60-s px velocity, sec_since_mfe) are already in the L2H cache / DS3_THL2_NEEDS.md; the causal z of pulled_sup10 (prior 6 months, ET 30-min bucket) is new and would need D6 to keep a 6-month bucket table.