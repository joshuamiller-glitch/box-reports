# DS3_ZONES_2 - zones, second pass: the consistent few, pre-registered as a set (Z2, 36-hour plan section 1)
Research only; no live, execution-server or chart change; UNTOUCHED never read (own masks, capped 20260206: X' 20230401..20240131, PRE 20240201..20250630, HOLD 20250701.., L6M 20250801.., L3M 20251106.. view, 2026 20260101..). Prereg autopilot/ZONES2_prereg.md (sha256 cbc197a333387fce0c154e571ed8a6421024a54168795e097d443a36f75cf006, logged in DECISIONS.md before any P&L statistic). Code l2vast/ds3/code/zones2/, outputs l2vast/ds3/out/zones2/. Units: points per signal in the planned-lot unit on the 70/30 base (SPL, the live base) unless said otherwise, N basis (no target-fill correction; M and LIVE-P9 side by side in section 4), minus the unfiltered base, week-clustered SE, MDE = 2.8 SE. Stack = exact lock engine, 6 books, $/week at the engine's configured lots (the lots of the DS3 stack lines; stack base 26.4k/wk L6M, 15.2k HOLD, 34.9k PRE, 8.0k X', -9.1k 2026), stack MDE for these rules 23-34k/wk.

## Page 1 - verdict (plain sentences)
**The set looks good in every window and it is not a rule.** The 11 lines (list below) were chosen after looking at the sign of dP(target) in all windows, so every window is in-sample for the set; I report PRE and X' separately and label everything post-hoc-selected. Skipping a signal when any of the 11 fresh lines lies between entry and target within 20 pts (19% of signals, 56 signals a week in L6M) adds +0.28 / +0.45 / +0.36 / +0.45 / +0.47 pts per signal in PRE / X' / L6M / HOLD / L3M (each inside its MDE of 0.6 / 1.0 / 0.9 / 1.0 / 1.3; pooled over all 2023-04..2026-02 +0.36, t 2.2, Newey-West t 3.1 before any selection adjustment), 11 of 12 quarters positive, and +8.9k / +3.2k / +30.1k / +26.7k $/wk on the lock-engine stack in PRE / X' / L6M / HOLD (stack MDE 23-34k; weekly delta correlation with the stack -0.5 to -0.6). Halving the size is half of that; re-targeting to the line minus 2 ticks is +0.21 / +0.33 / +0.30 / +0.42 / +0.49 (stack +0.4k / -3.7k / +16.0k / +14.7k).
**What kills it as a forward rule:** (1) the same selection rule fitted on PRE and X' only (what a forward user would have had) picks eight different lines whose skip gain is -0.28 / -0.31 / -0.34 in L6M / HOLD / L3M and whose dP(target) turns positive; (2) the quarterly walk-forward re-selection chain (7 refits, the rule applied to everything seen so far) earns -0.26 pts per signal out of sample for skip (-0.19 re-target, -0.13 half size), negative in 6 of 7 quarters, and the LAST re-fit (2026-01, five weeks) is negative for skip and half size and flat for re-target (see table): this is the forward-facing answer and it is no; (3) the result lives in the first 20 pts: at D = 30 the PRE and X' gains are 0.00 / +0.09 and at D = 40 it is negative in PRE, X', L6M and HOLD and at 75% of the target negative in all five windows (knife edge); (4) only fresh lines carry it (touched lines: PRE -0.37, X' -0.10); (5) it is book-specific and unstable: L6M skip gain HM +1.83, KB +1.03, MV +0.99, SM +0.76, ST +0.49 but MA -1.60, PE -0.35, PB -0.37, WT -0.19, and HM is -0.41 in X'; (6) validity layer: deflated Sharpe 0.004 (about 2.5 million cumulative trials), probability of backtest overfitting 0.61, family reality check best-cell p 0.50 (L6M) / 0.55 (HOLD), studentised stepdown survivors in the recent windows are only near-zero bracket cells (+0.04..+0.06 pts, PRE about 0).
**The level information itself is small.** For the re-target the real lines beat the random-level placebo with the same distance distribution (rank 1.00 in every window) and the shuffled-day placebo (1.00) but not by much over the SAME fired signals with permuted distances (rank 0.96 / 0.72 / 0.87 / 0.96 in PRE / X' / L6M / HOLD): most of the re-target gain is which signals fire and the shorter target (STRUCTURE), a few hundredths of a point is where the line sits. Against the selection itself: the same rule run on outcomes shuffled within book x week x target-distance selects a median 2 streams (8 or more in 3% of draws) and their skip gain is near zero (PRE +0.04, L6M +0.04, HOLD +0.09, P(null >= real) 0.00 in four windows, X' 0.11); random 8-stream sets with the same fire rate lose -0.22 to -0.41 in PRE / L6M / HOLD / L3M (+0.11 in X'). So the set is not a pure noise pick, and still the rule that builds it does not travel forward.
**The opposite uses fail outright.** Target = the next set line beyond 30 pts instead of the fixed target: -0.26 / -0.38 / -0.27 / -0.27 (t -3.0 pooled; the fixed target is better; stack -2.6k L6M, -5.1k HOLD). Resting the 30% at the nearest set line behind the entry instead of the 3-pt dip: -0.12 / -0.08 / -0.55 / -0.39 (stack about 0 recent, -10.6k PRE). Waiting for the trade-through and 70% now + 30% behind the line: +0.09 / +0.02 and +0.02 / +0.01 (L6M / HOLD), stack -4.3k / -9.4k and -0.4k / -2.3k. Stacked lines (two within 5 pts) are a smaller subset (9 signals a week) with the same signs and no extra edge.
**HTF lid test (4-h / daily FVG, OB, BRK, CRT, prior-day H/L between signal and target, D up to 60, 2,160 cells): null.** Skipping or re-targeting longs into a lid loses (all-array skip D = 60: -0.66 PRE, -1.45 L6M); the 4-h array subset at D = 20 is flat (-0.01 / +0.23 / -0.02 / -0.03); the HM-only 4-h array skip reproduces the NTZ-1 lead (+0.04 / +0.10 / +0.32 / +0.31 / +0.30) and stays a lead. Taking shorts from a bearish array (sizing x1.5) is the base rate, not location: its rank among random fire sets is 0.00-0.53. Two lid cells clear the placebo gates: a near-zero bracket cell (iFVG 4h, 70/30-behind, +0.04 L6M) and a half-size cell on the 303 breakout arrays (+0.09 L6M, +0.03 PRE); neither has a stack gain in the recent windows.
**Tier:** LEAD, shadow only (post-hoc-selected; recent windows positive; fails the forward chain; every window inside MDE; DSR 0.004). Nothing for D6 to turn ON; the shadow rule and its forward test are in section 8.
**Multiplicity:** set N = 11 chosen from 586 streams after seeing all windows; cells scored 3,130 (set / each alone / stacked / chooser / R30) + 2,160 (lid) = 5,290, plus 36 forward-test cells = 5,326 (participation-ratio effective number 27 and 16); cumulative with earlier programs the deflation uses about 2.5 million trials (UF_TRIALS sum of n_cells).

## 1. The set (N = 11), post-hoc-selected, exact definitions for D6
Rule (applied to the 586 streams of DS3_POI_MAP with rows): adjusted dP(target) < 0 in PRE, X', L6M, HOLD and L3M at D = 20 and at D = 40 (fresh, pooled), each of the four non-L3M windows <= -0.025 at D = 20, n(ahead) >= 50 per window (>= 30 in L3M). 8 streams pass; 3 more were added because the user named them (two have a positive L3M, one fails D = 40). Sign agreement alone is cheap: 82 streams in the four non-L3M windows at D = 20, 50 in all five, 24 in all five at both D. Table: out/zones2/set_selection_table.csv. Near misses (all-sign at both D but weaker): ARR|BRK|30s, ARR|FVG|1h, ARR|FVG|1m, ARR|FVG|30s, ARR|iFVG_CE|45s, ARR|iplFVG|10m, FIB|ext127|5m, FIB|ote705_up|1h, FIB|ret79|15m, PRF|b1|day, PRF|b1|month, PRF|hvn0|sess, PRF|poc|sess, PRF|poc|sw1h, PRF|vwap|day, SWG|f3H|45s.
| stream | origin | dP PRE | dP X' | dP L6M | dP HOLD | dP L3M | n L3M |
|---|---|---|---|---|---|---|---|
| MAS|ich_kijun|1h | named + rule | -0.059 | -0.089 | -0.099 | -0.068 | -0.103 | 95 |
| PRF|lvn1|sw1h | named + rule | -0.070 | -0.065 | -0.082 | -0.086 | -0.076 | 84 |
| PDX|day|M | named (fails the rule) | -0.050 | -0.084 | -0.169 | -0.107 | -0.115 | 36 |
| PRF|vah|sw15 | named (fails the rule) | -0.074 | -0.036 | -0.038 | -0.038 | +0.029 | 112 |
| CRT|M|4h | named + rule | -0.086 | -0.028 | -0.108 | -0.116 | -0.047 | 73 |
| MAS|kc_up|4h | named + rule | -0.049 | -0.078 | -0.105 | -0.089 | -0.308 | 36 |
| PIV|cam_H3|rth | named (fails the rule) | -0.068 | -0.057 | -0.077 | -0.091 | +0.030 | 64 |
| PRF|hvn0|sw1h | named + rule | -0.031 | -0.032 | -0.087 | -0.101 | -0.199 | 77 |
| FIB|ote62_up|15m | rule | -0.027 | -0.041 | -0.032 | -0.032 | -0.047 | 140 |
| FIB|ote705_up|15m | rule | -0.047 | -0.028 | -0.107 | -0.103 | -0.090 | 118 |
| FIB|ote79_up|15m | rule | -0.041 | -0.027 | -0.060 | -0.080 | -0.038 | 127 |
Definitions (causal: usable only after the source bar or segment has closed; all are LINES, support or resistance by side; computable live from bars and the 1-s tape):
* PDX|day|M = (high + low)/2 of the previous completed Globex day (18:00-17:00 ET), active the whole next day.
* MAS|ich_kijun|1h = (highest high of the last 26 closed 1-h bars + lowest low of the same 26)/2, updated at each 1-h close.
* MAS|kc_up|4h = EMA20(close) + 2 x ATR10 (simple mean of the last 10 true ranges) of closed 4-h bars (bars anchored 18:00 ET), updated at each 4-h close.
* CRT|M|4h = (high + low)/2 of the last CLOSED 4-h bar.
* PIV|cam_H3|rth = Close + 1.1 x (High - Low)/4 of the previous completed RTH session (09:30-16:00 ET).
* PRF|vah|sw15 = value-area high (70% of volume, POC-outward expansion, 1-s volume spread uniformly over the ticks of each second) of the volume profile of the leg between the last two confirmed fractal-2/2 pivots of the 15-m bars; replaced at the next pivot confirmation.
* PRF|lvn1|sw1h = second-lowest trough of the Gaussian-smoothed (2-pt sigma) profile of the leg between the last two confirmed fractal-2/2 pivots of the 1-h bars (trough prominence >= 8% of the peak); PRF|hvn0|sw1h = the highest peak (prominence >= 10%) of the same profile.
* FIB|ote705_up|15m = L3 + 0.705 x (H3 - L3) with H3 = highest of the last 3 confirmed fractal-2/2 swing highs and L3 = lowest of the last 3 swing lows on 15-m bars (range >= 4 pts); ote62_up uses 0.62 and ote79_up 0.79.
"Ahead" = between the entry and the target (distance to the line <= the signal's target distance); "fresh" = not touched since formation; "touched" = already touched at least once (the store has no exact touch count, so 'touched once' is reported as touched >= 1); "any" = nearest fresh or touched. Stacked POI = two set lines, both ahead within D, whose distances differ by <= 5 pts.

## 2. Primary cells (fixed before the numbers were read)
Pts per signal vs the unfiltered base, N basis; per contract = rule pts per contract of final position minus base per contract (L6M); skipped-signal mean = the base P&L of the signals the rule touched (L6M, the cost of the filter beside the gain); stack in $k/week; placebo ranks = share of draws the real cell beats (300 draws; random-level = same fire count per book x session x target-bin x side stratum with distances sampled from the real pool; permuted-distance = distances permuted among the same fired signals, degenerate (0.00 / 1.00) for skip and half-size, which do not use the distance; shuffled-day = the whole ahead vector from another day of the same book x side x session).
| cell | PRE | X' | L6M | HOLD | L3M | MDE L6M/HOLD | per contract L6M | fires/wk L6M | skipped-signal mean L6M | stack Δ PRE/X/L6M/HOLD/Y26 $k/wk | rank vs random-level (PRE/X/L6M/HOLD) | vs permuted-distance | vs shuffled-day |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ahead|SET|var=fresh|d=20pts|act=rt|base=SPL | +0.21 | +0.33 | +0.30 | +0.42 | +0.49 | 0.90/0.98 | +0.37 | 56 | -2.32 | +0.4k / -3.7k / +16.0k / +14.7k / +21.7k | 1.00/1.00/1.00/1.00 | 0.96/0.72/0.87/0.96 | 1.00/1.00/1.00/1.00 |
| ahead|SET|var=fresh|d=20pts|act=skip|base=SPL | +0.28 | +0.45 | +0.36 | +0.45 | +0.47 | 0.93/1.03 | +1.03 | 56 | -2.32 | +8.9k / +3.2k / +30.1k / +26.7k / +30.9k | 1.00/1.00/1.00/1.00 | 0.00/1.00/0.00/0.00 | 1.00/1.00/1.00/1.00 |
| ahead|SET|var=fresh|d=20pts|act=z50|base=SPL | +0.14 | +0.23 | +0.18 | +0.23 | +0.24 | 0.47/0.51 | +0.47 | 56 | -2.32 | +1.2k / +2.5k / +16.9k / +14.5k / +7.5k | 1.00/1.00/1.00/1.00 | 0.00/1.00/0.00/0.00 | 1.00/1.00/1.00/1.00 |
| ahead|SET|var=fresh|d=20pts|act=wt|base=SPL | -0.03 | +0.30 | +0.09 | +0.02 | +0.23 | 0.46/0.46 | +0.21 | 56 | -2.32 | -5.9k / +2.1k / -4.3k / -9.4k / -3.2k | 0.82/1.00/0.98/0.97 | 0.16/0.29/0.01/0.01 | 0.84/0.99/0.99/0.97 |
| ahead|SET|var=fresh|d=20pts|act=b73|base=SPL | -0.02 | +0.04 | +0.02 | +0.01 | +0.06 | 0.13/0.13 | +0.06 | 56 | -2.32 | -7.4k / -0.8k / -0.4k / -2.3k / -8.4k | 0.67/0.97/1.00/0.99 | 0.03/0.06/0.02/0.02 | 0.68/0.98/0.99/0.98 |
| ahead|SET|var=fresh|d=20pts|act=rt|base=MKT | +0.21 | +0.29 | +0.31 | +0.44 | +0.46 | 0.91/0.97 | +0.34 | 56 | -2.02 | +1.9k / -1.4k / +13.4k / +10.9k / +23.4k | 1.00/0.99/1.00/1.00 | 0.82/0.81/0.99/0.99 | 1.00/1.00/1.00/1.00 |
| tc|SET|var=fresh|d=cap60|act=tc|base=SPL | -0.26 | -0.38 | -0.27 | -0.27 | -0.10 | 0.58/0.55 | -0.27 | 90 | +3.00 | -7.6k / -9.5k / -2.6k / -5.1k / +10.6k | 0.02/0.01/0.25/0.24 | 0.33/0.00/0.20/0.24 | 0.02/0.00/0.21/0.19 |
| r30|SET|var=fresh|d=30pts|act=r30s0|base=SPL | -0.12 | -0.08 | -0.55 | -0.39 | -0.05 | 0.89/0.91 | -0.11 | 175 | +3.59 | -10.6k / +5.5k / +0.5k / -0.1k / +19.1k | 0.86/0.85/0.95/0.98 |  |  |
| r30|SET|var=fresh|d=30pts|act=r30s1|base=SPL | -0.16 | -0.17 | -0.56 | -0.40 | -0.07 | 0.89/0.91 | -0.12 | 175 | +3.59 | -11.6k / +3.3k / +0.5k / -0.1k / +18.7k | 0.84/0.77/0.99/1.00 |  |  |

Bases for the SET at D = 20 fresh (SPL base), gain per signal:
| action | basis | PRE | X' | L6M | HOLD | L3M |
|---|---|---|---|---|---|---|
| skip | M | +0.49 | +0.62 | +0.67 | +0.78 | +0.73 |
| skip | N | +0.28 | +0.45 | +0.36 | +0.45 | +0.47 |
| skip | LIVE | +0.60 | +0.79 | +0.78 | +0.89 | +0.83 |
| rt | M | +0.09 | +0.22 | +0.13 | +0.23 | +0.34 |
| rt | N | +0.21 | +0.33 | +0.30 | +0.42 | +0.49 |
| rt | LIVE | +0.18 | +0.35 | +0.20 | +0.31 | +0.40 |
| z50 | M | +0.24 | +0.31 | +0.34 | +0.39 | +0.37 |
| z50 | N | +0.14 | +0.23 | +0.18 | +0.23 | +0.24 |
| z50 | LIVE | +0.30 | +0.39 | +0.39 | +0.45 | +0.41 |
| wt | M | +0.01 | +0.33 | +0.14 | +0.07 | +0.26 |
| wt | N | -0.03 | +0.30 | +0.09 | +0.02 | +0.23 |
| wt | LIVE | +0.05 | +0.39 | +0.17 | +0.11 | +0.28 |
| b73 | M | -0.02 | +0.04 | +0.02 | +0.01 | +0.06 |
| b73 | N | -0.02 | +0.04 | +0.02 | +0.01 | +0.06 |
| b73 | LIVE | -0.01 | +0.06 | +0.04 | +0.03 | +0.07 |

## 3. The grid: D (pts and % of the target distance), actions, SET fresh, 70/30 base
| D | action | PRE | X' | L6M | HOLD | L3M | MDE L6M | fires/wk L6M | stack PRE/X/L6M/HOLD $k/wk |
|---|---|---|---|---|---|---|---|---|---|
| 10pts | skip | +0.25 | +0.29 | +0.05 | +0.14 | +0.17 | 0.49 | 25 | +9.3k / +2.8k / +15.6k / +15.9k |
| 10pts | rt | +0.24 | +0.22 | +0.05 | +0.13 | +0.20 | 0.49 | 25 | +4.8k / +0.3k / +6.7k / +7.8k |
| 10pts | z50 | +0.12 | +0.14 | +0.03 | +0.07 | +0.09 | 0.24 | 25 | +1.9k / +3.7k / +10.6k / +9.3k |
| 10pts | wt | -0.03 | +0.18 | +0.11 | +0.05 | +0.15 | 0.21 | 25 | -3.8k / -0.5k / +6.8k / +3.6k |
| 10pts | b73 | +0.01 | +0.06 | +0.01 | +0.00 | +0.02 | 0.07 | 25 | -3.6k / -0.8k / +1.6k / +1.3k |
| 15pts | skip | +0.25 | +0.43 | +0.25 | +0.34 | +0.36 | 0.73 | 41 | +9.5k / +3.2k / +21.9k / +19.8k |
| 15pts | rt | +0.22 | +0.32 | +0.22 | +0.31 | +0.31 | 0.73 | 41 | +2.2k / -2.5k / +11.4k / +11.0k |
| 15pts | z50 | +0.12 | +0.22 | +0.12 | +0.17 | +0.18 | 0.36 | 41 | +1.2k / +2.3k / +11.4k / +9.1k |
| 15pts | wt | -0.08 | +0.15 | +0.11 | +0.06 | +0.25 | 0.36 | 41 |  |
| 15pts | b73 | -0.03 | +0.03 | +0.02 | +0.01 | +0.06 | 0.11 | 41 |  |
| 20pts | skip | +0.28 | +0.45 | +0.36 | +0.45 | +0.47 | 0.93 | 56 | +8.9k / +3.2k / +30.1k / +26.7k |
| 20pts | rt | +0.21 | +0.33 | +0.30 | +0.42 | +0.49 | 0.90 | 56 | +0.4k / -3.7k / +16.0k / +14.7k |
| 20pts | z50 | +0.14 | +0.23 | +0.18 | +0.23 | +0.24 | 0.47 | 56 | +1.2k / +2.5k / +16.9k / +14.5k |
| 20pts | wt | -0.03 | +0.30 | +0.09 | +0.02 | +0.23 | 0.46 | 56 | -5.9k / +2.1k / -4.3k / -9.4k |
| 20pts | b73 | -0.02 | +0.04 | +0.02 | +0.01 | +0.06 | 0.13 | 56 | -7.4k / -0.8k / -0.4k / -2.3k |
| 30pts | skip | -0.00 | +0.09 | +0.34 | +0.37 | +0.51 | 1.17 | 83 | -2.6k / -0.4k / +23.4k / +19.4k |
| 30pts | rt | +0.07 | +0.12 | +0.39 | +0.51 | +0.46 | 1.08 | 83 | -6.2k / -8.4k / +7.4k / +6.9k |
| 30pts | z50 | -0.00 | +0.04 | +0.17 | +0.19 | +0.26 | 0.58 | 83 |  |
| 30pts | wt | -0.14 | +0.25 | +0.04 | -0.15 | +0.33 | 0.91 | 83 | -7.2k / +0.1k / -4.9k / -12.6k |
| 30pts | b73 | -0.07 | -0.03 | +0.00 | -0.03 | +0.06 | 0.20 | 83 | -8.4k / -1.1k / -0.8k / -3.6k |
| 40pts | skip | -0.11 | -0.31 | -0.09 | -0.04 | +0.10 | 1.35 | 102 | -7.3k / -7.3k / +15.0k / +11.1k |
| 40pts | rt | -0.01 | -0.03 | +0.24 | +0.36 | +0.34 | 1.13 | 102 | -10.4k / -10.4k / +0.7k / -0.1k |
| 40pts | z50 | -0.06 | -0.15 | -0.05 | -0.02 | +0.05 | 0.68 | 102 |  |
| 40pts | wt | -0.25 | +0.03 | -0.30 | -0.46 | +0.25 | 1.11 | 102 |  |
| 40pts | b73 | -0.09 | -0.10 | -0.14 | -0.16 | -0.07 | 0.28 | 102 |  |
| 25pct | skip | +0.23 | +0.52 | +0.27 | +0.37 | +0.35 | 0.69 | 37 | +7.6k / +3.9k / +24.3k / +22.6k |
| 25pct | rt | +0.20 | +0.35 | +0.23 | +0.33 | +0.31 | 0.71 | 37 | +1.3k / -2.4k / +15.1k / +14.0k |
| 25pct | z50 | +0.11 | +0.26 | +0.14 | +0.19 | +0.17 | 0.35 | 37 | -0.3k / +1.8k / +13.6k / +11.2k |
| 25pct | wt | -0.08 | +0.24 | +0.13 | +0.08 | +0.28 | 0.30 | 37 |  |
| 25pct | b73 | -0.02 | +0.05 | +0.02 | +0.02 | +0.05 | 0.09 | 37 |  |
| 50pct | skip | +0.00 | +0.09 | +0.29 | +0.32 | +0.52 | 1.16 | 77 | -1.1k / -0.2k / +18.8k / +14.2k |
| 50pct | rt | +0.06 | +0.11 | +0.37 | +0.47 | +0.49 | 1.10 | 77 | -5.6k / -7.9k / +6.8k / +6.4k |
| 50pct | z50 | +0.00 | +0.04 | +0.15 | +0.16 | +0.26 | 0.58 | 77 | -3.4k / +0.9k / +9.0k / +6.3k |
| 50pct | wt | -0.18 | +0.32 | +0.08 | -0.10 | +0.39 | 0.86 | 77 |  |
| 50pct | b73 | -0.07 | -0.04 | +0.01 | -0.03 | +0.06 | 0.18 | 77 |  |
| 75pct | skip | -0.11 | -0.38 | -0.48 | -0.37 | -0.23 | 1.40 | 106 | -8.4k / -9.5k / +7.9k / +5.7k |
| 75pct | rt | -0.03 | -0.07 | +0.03 | +0.16 | +0.24 | 1.15 | 106 | -10.1k / -11.3k / -7.4k / -7.7k |
| 75pct | z50 | -0.05 | -0.19 | -0.24 | -0.19 | -0.11 | 0.70 | 106 |  |
| 75pct | wt | -0.31 | +0.04 | -0.52 | -0.61 | +0.07 | 1.38 | 106 |  |
| 75pct | b73 | -0.10 | -0.10 | -0.19 | -0.20 | -0.12 | 0.31 | 106 |  |

Freshness (D = 20): 
| freshness | action | PRE | X' | L6M | HOLD | L3M | fires/wk L6M |
|---|---|---|---|---|---|---|---|
| fresh | skip | +0.28 | +0.45 | +0.36 | +0.45 | +0.47 | 56 |
| fresh | rt | +0.21 | +0.33 | +0.30 | +0.42 | +0.49 | 56 |
| touched | skip | -0.37 | -0.10 | +0.15 | +0.12 | +0.44 | 80 |
| touched | rt | -0.39 | -0.35 | +0.06 | +0.04 | +0.28 | 80 |
| any | skip | -0.24 | +0.13 | +0.20 | +0.28 | +0.66 | 119 |
| any | rt | -0.29 | -0.12 | +0.10 | +0.21 | +0.47 | 119 |

Stacked POI (two set lines within 5 pts) against the any-of-set:
| set | freshness | action | PRE | X' | L6M | HOLD | L3M | fires/wk L6M |
|---|---|---|---|---|---|---|---|---|
| ahead | fresh | skip | +0.28 | +0.45 | +0.36 | +0.45 | +0.47 | 56.4 |
| ahead | fresh | rt | +0.21 | +0.33 | +0.30 | +0.42 | +0.49 | 56.4 |
| ahead | any | skip | -0.24 | +0.13 | +0.20 | +0.28 | +0.66 | 119.1 |
| ahead | any | rt | -0.29 | -0.12 | +0.10 | +0.21 | +0.47 | 119.1 |
| stacked | fresh | skip | +0.14 | +0.27 | +0.16 | +0.13 | +0.13 | 8.6 |
| stacked | fresh | rt | +0.13 | +0.21 | +0.06 | +0.08 | +0.09 | 8.6 |
| stacked | any | skip | +0.34 | +0.35 | +0.40 | +0.37 | +0.45 | 26.7 |
| stacked | any | rt | +0.31 | +0.17 | +0.24 | +0.25 | +0.33 | 26.7 |

Each alone (D = 20 fresh, 70/30 base; skip and re-target):
| unit | action | PRE | X' | L6M | HOLD | L3M | fires/wk L6M |
|---|---|---|---|---|---|---|---|
| SET | skip | +0.28 | +0.45 | +0.36 | +0.45 | +0.47 | 56.4 |
| SET | rt | +0.21 | +0.33 | +0.30 | +0.42 | +0.49 | 56.4 |
| MAS|ich_kijun|1h | skip | +0.09 | +0.40 | +0.21 | +0.16 | +0.20 | 8.4 |
| MAS|ich_kijun|1h | rt | +0.08 | +0.26 | +0.16 | +0.13 | +0.22 | 8.4 |
| PRF|lvn1|sw1h | skip | +0.05 | +0.19 | +0.04 | +0.08 | +0.05 | 5.1 |
| PRF|lvn1|sw1h | rt | +0.03 | +0.09 | +0.01 | +0.06 | -0.03 | 5.1 |
| PDX|day|M | skip | +0.02 | +0.23 | +0.16 | +0.11 | +0.08 | 3.7 |
| PDX|day|M | rt | +0.05 | +0.24 | +0.14 | +0.11 | +0.12 | 3.7 |
| PRF|vah|sw15 | skip | +0.15 | +0.09 | -0.01 | +0.00 | -0.07 | 9.2 |
| PRF|vah|sw15 | rt | +0.11 | +0.07 | +0.06 | +0.07 | +0.02 | 9.2 |
| CRT|M|4h | skip | +0.10 | +0.10 | +0.11 | +0.15 | +0.01 | 6.0 |
| CRT|M|4h | rt | +0.07 | +0.13 | +0.05 | +0.10 | +0.02 | 6.0 |
| MAS|kc_up|4h | skip | -0.01 | +0.05 | +0.02 | +0.02 | +0.21 | 3.2 |
| MAS|kc_up|4h | rt | -0.01 | -0.00 | +0.04 | +0.04 | +0.19 | 3.2 |
| PIV|cam_H3|rth | skip | +0.03 | -0.00 | +0.09 | +0.12 | -0.06 | 5.3 |
| PIV|cam_H3|rth | rt | -0.00 | +0.09 | +0.09 | +0.11 | -0.02 | 5.3 |
| PRF|hvn0|sw1h | skip | +0.01 | +0.01 | +0.09 | +0.14 | +0.28 | 5.8 |
| PRF|hvn0|sw1h | rt | +0.03 | -0.02 | +0.05 | +0.11 | +0.27 | 5.8 |
| FIB|ote62_up|15m | skip | +0.03 | +0.15 | -0.01 | -0.00 | +0.11 | 10.1 |
| FIB|ote62_up|15m | rt | -0.02 | +0.06 | -0.11 | -0.08 | -0.08 | 10.1 |
| FIB|ote705_up|15m | skip | +0.08 | +0.03 | +0.20 | +0.22 | +0.22 | 8.9 |
| FIB|ote705_up|15m | rt | +0.05 | -0.09 | +0.16 | +0.17 | +0.21 | 8.9 |
| FIB|ote79_up|15m | skip | +0.02 | -0.03 | +0.06 | +0.13 | +0.07 | 9.6 |
| FIB|ote79_up|15m | rt | +0.01 | +0.00 | +0.03 | +0.09 | +0.03 | 9.6 |

## 4. Per book / session / side (SET, D = 20, fresh, 70/30 base; skip, then re-target)
| group | PRE | X' | L6M | HOLD | L3M | n sig L6M | fired L6M | kept/contract L6M | skipped-signal mean L6M |
|---|---|---|---|---|---|---|---|---|---|
| ALL | +0.28 | +0.45 | +0.36 | +0.45 | +0.47 | 9741 | 1522 | +1.03 | -2.32 |
| DN | -0.48 | +0.81 | +0.44 | +0.50 | -0.96 | 701 | 104 | +1.48 | -2.95 |
| HM | +0.38 | -0.41 | +1.83 | +1.80 | +1.10 | 909 | 190 | +3.46 | -8.78 |
| KB | +0.22 | +1.06 | +1.03 | +1.05 | +2.50 | 1257 | 233 | +1.58 | -5.57 |
| MA | -0.05 | -1.73 | -1.60 | -0.76 | -2.87 | 407 | 104 | -0.03 | +6.26 |
| MV | +0.56 | +2.14 | +0.99 | +1.10 | +0.84 | 1131 | 180 | +1.60 | -6.20 |
| PB | +0.19 | +0.84 | -0.37 | -0.01 | -1.01 | 866 | 45 | +0.03 | +7.16 |
| PE | +0.65 | +0.07 | -0.35 | -0.48 | +0.07 | 1194 | 136 | -0.29 | +3.09 |
| SM | -0.53 | +0.78 | +0.76 | +0.56 | +2.43 | 314 | 87 | +2.28 | -2.74 |
| ST | +0.44 | +0.51 | +0.49 | +0.58 | +1.22 | 1256 | 153 | +1.16 | -4.03 |
| WT | +0.33 | -0.09 | -0.19 | -0.07 | -0.16 | 1706 | 290 | +0.15 | +1.10 |
| asia | +0.44 | +1.19 | +0.79 | +1.02 | +1.22 | 2678 | 653 | +2.37 | -3.25 |
| close | +6.87 | -1.49 | +13.73 | +12.08 | +20.93 | 22 | 9 | +19.35 | -33.55 |
| london | +0.70 | +0.18 | -0.15 | -0.33 | +0.21 | 2050 | 371 | +0.90 | +0.82 |
| nyam | -0.26 | -0.49 | +0.40 | +0.41 | -0.15 | 2784 | 249 | +0.68 | -4.48 |
| nypm | +0.07 | +1.06 | -0.26 | -0.08 | -0.06 | 1718 | 188 | -0.09 | +2.34 |
| pre | +0.90 | +0.72 | +1.50 | +2.17 | +1.65 | 489 | 52 | +1.94 | -14.12 |
| short | +0.06 | +0.96 | +0.75 | +0.86 | +0.55 | 4875 | 465 | +1.20 | -7.85 |
| long | +0.50 | -0.03 | -0.02 | +0.04 | +0.39 | 4866 | 1057 | +0.79 | +0.11 |

Re-target:
| group | PRE | X' | L6M | HOLD | L3M | n sig L6M | fired L6M | kept/contract L6M | skipped-signal mean L6M |
|---|---|---|---|---|---|---|---|---|---|
| ALL | +0.21 | +0.33 | +0.30 | +0.42 | +0.49 | 9741 | 1522 | +0.37 | -2.32 |
| DN | -0.40 | +1.13 | -0.04 | +0.18 | -0.79 | 701 | 104 | +0.12 | -2.95 |
| HM | +0.46 | -0.53 | +2.23 | +2.29 | +1.65 | 909 | 190 | +2.42 | -8.78 |
| KB | +0.04 | +0.61 | +0.46 | +0.64 | +1.96 | 1257 | 233 | +0.49 | -5.57 |
| MA | -0.09 | -1.81 | -1.72 | -1.13 | -2.69 | 407 | 104 | -1.58 | +6.26 |
| MV | +0.61 | +1.91 | +0.78 | +0.73 | +0.63 | 1131 | 180 | +0.83 | -6.20 |
| PB | +0.20 | +0.51 | -0.08 | +0.39 | -0.70 | 866 | 45 | -0.05 | +7.16 |
| PE | +0.35 | -0.22 | -0.20 | -0.18 | +0.20 | 1194 | 136 | -0.19 | +3.09 |
| SM | -0.92 | +0.95 | +0.54 | +0.41 | +2.51 | 314 | 87 | +0.66 | -2.74 |
| ST | +0.40 | +0.14 | +0.40 | +0.50 | +1.06 | 1256 | 153 | +0.47 | -4.03 |
| WT | +0.24 | +0.16 | -0.09 | -0.06 | -0.07 | 1706 | 290 | -0.07 | +1.10 |
| asia | +0.35 | +1.04 | +0.80 | +1.20 | +1.16 | 2678 | 653 | +0.96 | -3.25 |
| close | +4.42 | +0.64 | +17.07 | +15.02 | +24.66 | 22 | 9 | +17.63 | -33.55 |
| london | +0.46 | +0.21 | -0.14 | -0.35 | +0.09 | 2050 | 371 | -0.05 | +0.82 |
| nyam | -0.19 | -0.73 | +0.14 | +0.14 | -0.04 | 2784 | 249 | +0.16 | -4.48 |
| nypm | +0.10 | +1.03 | -0.07 | -0.01 | +0.14 | 1718 | 188 | -0.06 | +2.34 |
| pre | +0.61 | +0.39 | +0.97 | +1.81 | +1.35 | 489 | 52 | +1.01 | -14.12 |
| short | +0.05 | +0.90 | +0.74 | +0.90 | +0.70 | 4875 | 465 | +0.78 | -7.85 |
| long | +0.37 | -0.21 | -0.13 | -0.06 | +0.27 | 4866 | 1057 | -0.06 | +0.11 |

The 'close' rows are 22 signals in L6M: ignore. The session columns that carry the L6M gain are Asia (+0.79) and the pre-open hour (+1.50); London, NY-PM are zero or negative.

## 5. Is it selection? (the post-hoc test)
Shuffled-outcome null for the SELECTION rule (outcomes permuted within book x week x target-distance bin, the same rule re-applied to all 689 streams, skip gain of what it selects; the null selects 0-12 streams, median 2) and random 8-stream sets with the same fire rate:
| window | real objective-8 set, skip D20 | selection-on-shuffled-outcomes (n=210 draws), mean [P(null>=real)] | random 8-stream sets, fire-matched (n=17), mean [P(rand>=real)] |
|---|---|---|---|
| PRE | +0.23 | +0.04 [0.000] | -0.27 [0.000] |
| X' | +0.42 | +0.21 [0.110] | +0.11 [0.059] |
| L6M | +0.35 | +0.04 [0.000] | -0.41 [0.000] |
| HOLD | +0.45 | +0.09 [0.000] | -0.30 [0.000] |
| L3M | +0.68 | +0.14 [0.000] | -0.22 [0.000] |

Forward test of the rule (fit on the earlier windows only, evaluate the later ones; 70/30 base, N, pts per signal):
| fit on | N | evaluated | skip | rt | z50 | fires |
|---|---|---|---|---|---|---|
| PRE+X | 8 | L6M | -0.28 (MDE 0.57) | -0.15 | -0.14 | 424 |
| PRE+X | 8 | HOLD | -0.31 (MDE 0.55) | -0.18 | -0.16 | 511 |
| PRE+X | 8 | L3M | -0.34 (MDE 0.67) | -0.21 | -0.17 | 178 |
| PRE+X | 8 | Y26 | -0.14 (MDE 0.52) | -0.05 | -0.07 | 69 |
| PRE+X | 11 | L6M | -0.35 (MDE 0.68) | -0.15 | -0.17 | 619 |
| PRE+X | 11 | HOLD | -0.31 (MDE 0.68) | -0.18 | -0.15 | 747 |
| PRE+X | 11 | L3M | -0.48 (MDE 0.90) | -0.26 | -0.24 | 264 |
| PRE+X | 11 | Y26 | -0.18 (MDE 0.75) | -0.03 | -0.09 | 97 |
| PRE+X+Jul-Nov25 | 8 | L3M | -0.05 (MDE 0.81) | +0.13 | -0.03 | 495 |
| PRE+X+Jul-Nov25 | 8 | Y26 | -0.51 (MDE 1.15) | -0.32 | -0.26 | 210 |
| PRE+X+Jul-Nov25 | 11 | L3M | +0.01 (MDE 1.31) | +0.24 | +0.00 | 858 |
| PRE+X+Jul-Nov25 | 11 | Y26 | -0.37 (MDE 2.20) | -0.19 | -0.19 | 360 |

Quarterly walk-forward chain (refit on everything before the date, 4 equal-trade training chunks all negative at D = 20 and D = 40, top 8; test the next quarter only; the last row is the re-fit a user would run now):
| refit date (test = next quarter) | streams passing rule | signals in test quarter | fired | skip pts/signal | rt pts/signal | z50 pts/signal |
|---|---|---|---|---|---|---|
| 20240401 | 0 | 2997 | 0 | +0.00 | +0.00 | +0.00 |
| 20240701 | 6 | 5004 | 902 | -0.51 | -0.33 | -0.26 |
| 20241001 | 7 | 3701 | 405 | -0.64 | -0.53 | -0.32 |
| 20250101 | 7 | 5180 | 377 | -0.09 | -0.17 | -0.04 |
| 20250401 | 1 | 5929 | 76 | -0.11 | -0.11 | -0.05 |
| 20250701 | 3 | 3379 | 157 | +0.09 | +0.15 | +0.05 |
| 20251001 | 8 | 5195 | 602 | -0.49 | -0.36 | -0.24 |
| 20260101 | 5 | 2229 | 142 | -0.19 | +0.03 | -0.10 |
Chained out-of-sample over 33614 signals: skip -0.26, re-target -0.19, half size -0.13 pts per signal. Lines the chain keeps re-picking: ich_kijun 1h (2 of 7 refits), PIV cam_H3 day (4), FIB OTE zone / ret62 15m (4), PRF lvn1 sw1h (3), CRT M 4h (2): some persistence exists, but the pooled forward result is negative.

## 6. Lid test: 4-h / daily arrays between the signal and the target (2,160 cells)
Arrays: ARR FVG / iFVG / iplFVG / OB / BRK on 4h and 1d (10), CRT H and L of the last 4-h bar (2), prior-day H and L (the daily CRT range edges, 2); each alone, ARR4H, ARR1D, CRT+PDX edges, ALL14. Fresh, 70/30 base, pts per signal (the full grid with MKT base and 'any' freshness is in rowsL.parquet):
| array set | D | action | PRE | X' | L6M | HOLD | L3M | MDE L6M | fires/wk L6M |
|---|---|---|---|---|---|---|---|---|---|
| ARR4H | 20 | skip | -0.01 | +0.23 | -0.02 | -0.03 | -0.14 | 0.40 | 12 |
| ARR4H | 20 | rt | -0.07 | +0.12 | +0.01 | +0.02 | -0.08 | 0.35 | 12 |
| ARR4H | 40 | skip | -0.08 | +0.04 | -0.40 | -0.37 | -0.41 | 0.72 | 30 |
| ARR4H | 40 | rt | -0.13 | +0.45 | -0.25 | -0.20 | -0.30 | 0.49 | 30 |
| ARR4H | 60 | skip | -0.07 | +0.14 | -0.43 | -0.42 | -0.29 | 0.83 | 43 |
| ARR4H | 60 | rt | -0.22 | +0.55 | -0.36 | -0.24 | -0.34 | 0.51 | 43 |
| ARR1D | 20 | skip | -0.01 | -0.03 | +0.01 | +0.02 | -0.01 | 0.13 | 2 |
| ARR1D | 20 | rt | +0.01 | +0.00 | -0.02 | -0.00 | +0.02 | 0.13 | 2 |
| ARR1D | 40 | skip | -0.08 | +0.13 | -0.00 | +0.04 | +0.07 | 0.47 | 7 |
| ARR1D | 40 | rt | -0.01 | +0.12 | -0.03 | -0.01 | +0.14 | 0.30 | 7 |
| ARR1D | 60 | skip | -0.09 | +0.02 | -0.30 | -0.24 | -0.17 | 0.54 | 14 |
| ARR1D | 60 | rt | -0.02 | -0.03 | -0.10 | -0.09 | +0.06 | 0.32 | 14 |
| CRTPDX | 20 | skip | -0.35 | +0.23 | -0.35 | -0.18 | -0.27 | 0.57 | 27 |
| CRTPDX | 20 | rt | -0.22 | +0.22 | -0.32 | -0.13 | -0.35 | 0.50 | 27 |
| CRTPDX | 40 | skip | -0.48 | -0.28 | -0.69 | -0.40 | -0.40 | 0.90 | 63 |
| CRTPDX | 40 | rt | -0.30 | +0.01 | -0.54 | -0.29 | -0.53 | 0.73 | 63 |
| CRTPDX | 60 | skip | -0.62 | -0.20 | -1.22 | -0.92 | -1.16 | 0.98 | 87 |
| CRTPDX | 60 | rt | -0.42 | +0.01 | -0.70 | -0.46 | -0.69 | 0.72 | 87 |
| ALL14 | 20 | skip | -0.36 | +0.21 | -0.29 | -0.16 | -0.26 | 0.57 | 36 |
| ALL14 | 20 | rt | -0.25 | +0.23 | -0.27 | -0.10 | -0.31 | 0.49 | 36 |
| ALL14 | 40 | skip | -0.54 | -0.71 | -0.87 | -0.58 | -0.31 | 0.94 | 84 |
| ALL14 | 40 | rt | -0.37 | +0.15 | -0.57 | -0.30 | -0.42 | 0.83 | 84 |
| ALL14 | 60 | skip | -0.66 | -1.06 | -1.45 | -1.14 | -0.96 | 0.98 | 118 |
| ALL14 | 60 | rt | -0.51 | +0.04 | -0.85 | -0.58 | -0.67 | 0.83 | 118 |

By side (long = into the lid; short = away from a lid above it is not tested here, see take-from) and the HM-only reproduction of the NTZ-1 lead:
| group | array set | D | action | PRE | X' | L6M | HOLD | L3M | fired L6M |
|---|---|---|---|---|---|---|---|---|---|
| long | ARR4H | 20 | skip | -0.07 | +0.22 | -0.06 | -0.05 | -0.14 | 153 |
| long | ARR4H | 60 | skip | +0.26 | +0.12 | -0.19 | -0.19 | -0.15 | 586 |
| long | ARR1D | 20 | skip | -0.05 | +0.15 | -0.01 | -0.01 | +0.01 | 30 |
| long | ARR1D | 60 | skip | -0.25 | +0.24 | -0.14 | -0.13 | -0.39 | 181 |
| long | CRTPDX | 20 | skip | -0.22 | +0.14 | -0.27 | +0.04 | -0.31 | 401 |
| long | CRTPDX | 60 | skip | -0.51 | -0.69 | -1.24 | -0.87 | -1.36 | 1229 |
| short | ARR4H | 20 | skip | +0.05 | +0.24 | +0.01 | -0.01 | -0.13 | 184 |
| short | ARR4H | 60 | skip | -0.40 | +0.17 | -0.68 | -0.66 | -0.42 | 574 |
| short | ARR1D | 20 | skip | +0.03 | -0.22 | +0.02 | +0.05 | -0.02 | 29 |
| short | ARR1D | 60 | skip | +0.08 | -0.21 | -0.47 | -0.36 | +0.03 | 188 |
| short | CRTPDX | 20 | skip | -0.48 | +0.33 | -0.43 | -0.41 | -0.23 | 318 |
| short | CRTPDX | 60 | skip | -0.73 | +0.32 | -1.21 | -0.98 | -0.97 | 1120 |
| HM | ARR4H | 20 | skip | +0.04 | +0.10 | +0.32 | +0.31 | +0.30 | 39 |
| HM | ARR4H | 60 | skip | +0.13 | -0.40 | +0.34 | +0.13 | +1.16 | 137 |
| HM | ARR1D | 20 | skip | +0.03 | +0.02 | -0.27 | -0.18 | -0.12 | 10 |
| HM | ARR1D | 60 | skip | -0.07 | -0.31 | -0.69 | -0.50 | -0.67 | 51 |
| HM | CRTPDX | 20 | skip | -0.60 | -0.00 | -0.42 | -0.01 | -1.09 | 62 |
| HM | CRTPDX | 60 | skip | -0.91 | +0.14 | -1.44 | -1.02 | -0.75 | 259 |

Take shorts from it / longs from a bullish array behind the entry (array between the entry and the STOP, same direction as the trade): size x1.5 (u150, freshness any) and take-only-those (onlyfrom, which loses the other signals and is -1.6 to -3.3 per signal):
| array set | D | var | action | PRE | X' | L6M | HOLD | L3M | rank vs random fire L6M | fires/wk |
|---|---|---|---|---|---|---|---|---|---|---|
| ARR4H | 20 | any | u150 | +0.10 | +0.19 | +0.14 | +0.03 | +0.42 | 0.01 | 82 |
| ARR4H | 20 | fresh | onlyfrom | -1.62 | -0.55 | -3.20 | -2.51 | -1.85 |  | 359 |
| ARR4H | 60 | any | u150 | +0.12 | -0.20 | +0.70 | +0.49 | +0.59 |  | 129 |
| ARR4H | 60 | fresh | onlyfrom | -1.63 | -0.73 | -3.00 | -2.35 | -1.88 |  | 345 |
| ARR1D | 20 | any | u150 | +0.03 | +0.16 | -0.28 | -0.23 | -0.61 |  | 85 |
| ARR1D | 20 | fresh | onlyfrom | -1.55 | -0.44 | -3.22 | -2.56 | -1.87 |  | 360 |
| ARR1D | 60 | any | u150 | +0.10 | +0.37 | -0.09 | -0.09 | -0.39 |  | 104 |
| ARR1D | 60 | fresh | onlyfrom | -1.55 | -0.28 | -3.26 | -2.63 | -1.83 |  | 358 |
| CRTPDX | 20 | any | u150 | -0.00 | +0.44 | +0.69 | +0.63 | +0.54 |  | 73 |
| CRTPDX | 20 | fresh | onlyfrom | -1.60 | -0.34 | -3.24 | -2.57 | -1.87 |  | 360 |
| CRTPDX | 60 | any | u150 | +0.10 | +0.17 | +0.96 | +0.72 | +0.54 | 0.53 | 175 |
| CRTPDX | 60 | fresh | onlyfrom | -1.62 | -0.21 | -2.98 | -2.45 | -1.91 |  | 340 |
| ALL14 | 20 | any | u150 | +0.04 | +0.42 | +0.61 | +0.48 | +0.48 | 0.00 | 190 |
| ALL14 | 20 | fresh | onlyfrom | -1.61 | -0.57 | -3.17 | -2.49 | -1.85 |  | 358 |
| ALL14 | 60 | any | u150 | +0.19 | +0.25 | +1.26 | +0.98 | +0.75 | 0.31 | 271 |
| ALL14 | 60 | fresh | onlyfrom | -1.69 | -0.80 | -2.97 | -2.46 | -1.98 |  | 329 |

Lid cells that clear every placebo gate (rank >= 0.95 against random fire and shuffled-day in PRE, X', L6M, HOLD):
| unit | D | var | act | base | g_PRE | g_X | g_L6M | g_HOLD | g_L3M | st_PRE | st_X | st_L6M | st_HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ARR|iFVG|4h | 60 | fresh | b73 | MKT | 0.02 | 0.02 | 0.04 | 0.01 | 0.0 | -411.44 | -335.54 | -3540.93 | -3496.12 |
| ARR|BRK|4h | 60 | any | z50 | MKT | 0.03 | 0.11 | 0.09 | 0.02 | 0.14 | 1226.29 | -628.4 | 793.3 | -731.1 |

## 7. Validity layer (QUANT-LAYER)
* Family A (3,130 cells): White best-cell reality check p: PRE 0.52, X' 0.69, L6M 0.50, HOLD 0.55, L3M 0.35; studentised stepdown (Romano-Wolf) survivors: PRE 0, X' 0, L6M 3, HOLD 7, L3M 78 - the recent survivors are bracket cells of +0.04..+0.06 pts (b73 / wait) with PRE about 0, not the skip rules. Lid family (2,160 cells): best-cell p 0.99 / 0.90 / 0.29 / 0.38 / 0.51, survivors 0 / 0 / 30 / 8 / 4 (again near-zero bracket cells and the base-rate u150 cells). Effective numbers of independent cells 27 and 16.
* PBO (CSCV, weekly, family A) 0.61 (prob. OOS loss 0.56). Deflated Sharpe of the primary cells with 2,472,938 trials: skip 0.004, re-target 0.001.
* Pooled 2023-04..2026-02 (before selection adjustment): skip +0.36 (SE 0.16, t 2.2, NW t 3.1), re-target +0.28 (t 1.9), wait +0.05 (t 0.6), 70/30-behind -0.00, target chooser -0.29 (t -3.0), R30 -0.18..-0.22 (t -1.2..-1.5).
* Weekly stack: the skip delta is negatively correlated with the stack base (PRE -0.49, X' -0.57, L6M -0.62, HOLD -0.62); the lock-engine worst-20 weeks improve (L6M -39k -> +4k, HOLD -85k -> -38k) and the L6M max drawdown falls 551k -> 299k, but the weekly delta SD is 54-72k so the stack MDE (23-34k) exceeds the PRE and X' deltas (+8.9k, +3.2k) and the recent ones (+30k, +27k on the stack run) are about one MDE.
* Gain concentration: the skip gain is the net of very large offsetting avoided winners and losers (top-5%-of-trades share 8.5x the total); the gain per touched signal is 2.3 pts, so a skip is not slippage-limited.
* Latency: the skip decision is taken at the signal second from lines known earlier; a 1-s or 3-s delay changes nothing for skip / half size (no order is sent). Re-target / wait / behind-line variants were scored at the signal second only; the 1-s / 3-s sweep was not run for them (they are not candidates).
The one-page quant header for the three primary cells that carry a gain (every column the library can compute; promote_ok is False because the stack correlation column is not wired to the library and the cell is not promotable anyway):
| cell | pts_per_contract | ci_lo | ci_hi | L3M | L6M | HOLD | PRE | Xp | trades_per_week | fire_rate | n_cells | rc_p_program | rw_survives | dsr | pbo | placebo_rank | neighbourhood_mean | breakeven_slip | capacity_contracts | top5_share | stack_corr | regime | drift_sign_count | plain_sentence | promote_ok |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SET fresh D20 skip SPL (N, per planned lot per signal) | 0.363 | -0.282 | 1.081 | 0.473 | 0.363 | 0.453 | 0.282 | 0.452 | 347.893 | 0.156 | 3130 | 0.498 | N | 0.004 | 0.611 | fire L6M 1.00 / day 1.00 / perm 0.00 | 0.234 | 2.321 | no fills added (removes/shifts entries) | 8.465 | None | all books; strongest asia/HM (see session table) | 11/12 | post-hoc set: positive in-sample in every window, fails the PRE+X-only forward test and the quarterly walk-forward chain | False |
| SET fresh D20 rt SPL (N, per planned lot per signal) | 0.305 | -0.284 | 0.995 | 0.490 | 0.305 | 0.423 | 0.206 | 0.331 | 347.893 | 0.156 | 3130 | 0.498 | N | 0.001 | 0.611 | fire L6M 1.00 / day 1.00 / perm 0.87 | 0.193 | 1.952 | no fills added (removes/shifts entries) | 11.225 | None | all books; strongest asia/HM (see session table) | 10/12 | post-hoc set: positive in-sample in every window, fails the PRE+X-only forward test and the quarterly walk-forward chain | False |
| SET fresh D20 z50 SPL (N, per planned lot per signal) | 0.181 | -0.141 | 0.541 | 0.237 | 0.181 | 0.226 | 0.141 | 0.226 | 347.893 | 0.156 | 3130 | 0.498 | N | 0.004 | 0.611 | fire L6M 1.00 / day 1.00 / perm 0.00 | 0.117 | 1.161 | no fills added (removes/shifts entries) | 8.465 | None | all books; strongest asia/HM (see session table) | 11/12 | post-hoc set: positive in-sample in every window, fails the PRE+X-only forward test and the quarterly walk-forward chain | False |

## 8. For D6 and the Sunday brief
* ON: nothing from this section.
* SHADOW (paper, forward register, frozen now): `entry * * poi_set_ahead(types = the 11 lines above, fresh, D = 20 pts) -> skip` and, as the milder arm, `-> lotmult 0.5` (D6 group-05 vocabulary: entry book regime poi_ahead(type, tf, D) -> skip | lotmult x | target poi-2t; the set needs the 11 lines as a published rolling file: prior-day mid, 15-m swing-leg VAH, 1-h swing-leg LVN2 / HVN1, 1-h kijun, 4-h CRT mid, 4-h Keltner upper, RTH Camarilla H3, three 15-m OTE levels). In-sample numbers to beat in the forward register: skip +0.36 pts per signal L6M, 56 touched signals a week, stack Delta +30.1k / wk L6M (+26.7k HOLD), half size +16.9k / +14.5k; pre-registered forward verdict: positive per signal AND positive stack over >= 13 forward weeks, with the walk-forward chain's result (-0.26) as the sceptic's prior.
* OFF: re-target to line - 2 ticks as a rule (the gain is structure: permuted-distance rank 0.72-0.96), wait for the trade-through, 70% now + 30% behind the line, the set as a target chooser, the set as the place to rest the 30%, any 4-h / daily lid skip or re-target, sizing up shorts from a lid.
* Open question (non-blocking, MORNING.md): do you want the set run as the shadow arm above, or is the forward chain's negative enough to close the zones line? Default: shadow, no live change.

## 9. Notes
* dead_lookup: the single-stream D = 20 fresh cells for these streams were already scored in NTZ-1 (DEAD_CELLS program NTZ1); the skip / half-size / wait / 70-30-behind numbers here reproduce them to 6 decimals (e.g. ich_kijun 1h, market base, L6M skip +0.196). The re-target differs by 0.01-0.02 because here a line closer than 2.5 pts (target < 2 pts) means the trade is skipped, in NTZ-1 it was left as the base. New in this section: the any-of-set union, D as % of the target, the stacked variant, the target chooser, the 30%-at-the-line rest, the lid family, the selection placebo and the forward chain.
* The 'touched once' freshness is 'touched at least once' (no touch count in the store). Latency sweep (1 s / 3 s) was not run for the sim actions.
* DEAD_CELLS +5,290 rows (program ZONES2), UF_TRIALS side plan36_zones2 (n_cells 5,326, n_effective 43), RECENT_WINS rows out/recent_wins/zones2.csv (1,564 L3M/L6M/HOLD-positive rows, 426 also PRE and X' positive, all labelled post-hoc-selected; none promoted).

## 10. Files
out/zones2/: rowsA.parquet (3,130 cells x 7 windows x 19 groups x 3 bases), rowsL.parquet (2,160 lid cells), rowsB_*.pkl / rowsBL_*.pkl (placebo draws and stack deltas), cells_A.csv / cells_L.csv (spec strings), set_selection_table.csv, valid_family.json, rc_family.json, neff.json, fwd.pkl, chain.pkl, selpl_*.pkl, randsets.pkl, qv_header.csv / .md, stack_cells.csv, lid_placebo.csv, stkcorr.pkl. Code: zones2/zl.py (plumbing), runA / runL / runB / runBL (drivers), selplacebo / randsets / fwd / chain (selection tests), valid / rc / hdr / stkcorr / tabs / tabs2 / mkreport (analysis).
