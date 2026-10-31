# DS3_HALT_RULES - T-HALT-RESUME: section A triggers x section C resumes, forgone vs avoided, stack line (GOV-1)

Research only; UNTOUCHED never read (cap 20260206). Engine = the D6-faithful lock engine validated in DS3_GOVERNOR_FIDELITY.md (integer half-up min-1 lots, live lots K6 2 / P6 7 / U6 4 / H6 4-2 / M6 2 / A6 1, 70/30 integer split, A6 market, Native 1.28, N basis, per-book day/week locks + combined 12R(K6) week lock). Preregs: HALT_RESUME_GOV_prereg.md sha256 8aeaa000...97a... (grid fixed before scoring) and HALT_RESUME_GOV_prereg_addendum.md sha256 5095b33a... (regime/combined/learned) in DECISIONS.md. Code `l2vast/ds3/code/govfid/hr_*.py`; every cell: `l2vast/ds3/out/govfid/hr_table_full.csv`.

Mechanics: the paper track is the baseline lock-engine stream (each signal the book would have taken, same fills and brackets); a halt is decided at a signal from trades that closed before it; halted signals are REMOVED from the lock engine (halted books absent, locks and re-entries real, open trades run to their brackets); freed lots idle (equal-risk factor reported instead of re-allocation, labelled structure). The "stack as it is" is the D6-faithful baseline incl. the live week-floor (12R per book + combined 12R of K6). Delta = cell minus baseline, $k per week, MDE in brackets = 2.8 x SE of the paired weekly delta.

## 1. Page 1

**1786 cells scored** (1,302 performance/equity cells: 62 triggers x 12 resumes + 3 half-size-first resumes, book scope; + 372 stack-scope; + 484 regime / combined / learned). **Median delta vs the stack as it is: L3M -13.0k, L6M -12.8k, HOLD -11.9k, PRE -4.3k, X' +2.3k. Share of cells with delta > 0: L3M 8%, L6M 7%, HOLD 7%, PRE 12%, X' 74%. Cells beating their own MDE (delta > MDE): L3M 0, L6M 0, HOLD 0, PRE 0, X' 0.**

Cells with delta > 0 in L6M AND HOLD AND PRE AND X': **18 of 1786** (all inside MDE; the median halted share of the carried cells in L6M is 0.4%, i.e. they barely halt). Cells with delta > 0 in L6M and HOLD: 112. No cell clears its MDE in any window. Verdict: halting is NULL on this stack; the live week floor plus day locks already do the work. Tier: DEAD for performance halts; LEAD-at-best for a handful of regime/calendar cells (section 5); CANDIDATE-RECENT not reached.

## 2. Families (book scope unless marked; median over the cells of a family)

| family | cells | delta>0 L6M | median d L3M | L6M | HOLD | PRE | X' | best d L6M (cell) | median halted share L6M | gain forgone / loss avoided (L6M, median) | median P(beat random halts) L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| MAE-profile shift | 8 | 0% | -11.3 | -8.5 | -7.2 | -2.2 | +0.7 | -0.8 (mae20/mem) | 3.7% | 1.41 | 0.57 |
| STACK-level equity: 2-sigma band | 6 | 0% | -24.7 | -18.7 | -17.0 | -4.5 | +1.3 | -13.8 (band30/w2) | 25.7% | 1.66 | 0.12 |
| STACK-level equity: INVERSE control (trade only below MA) | 18 | 0% | -24.1 | -28.7 | -26.5 | -11.2 | +8.5 | -18.9 (eqma50inv/w2) | 78.0% | 1.30 | 0.61 |
| STACK-level equity: negative slope | 12 | 0% | -35.2 | -33.7 | -31.7 | -13.0 | +9.2 | -25.1 (slope20/w2) | 66.0% | 1.47 | 0.06 |
| STACK-level equity: trade only above MA | 18 | 0% | -29.1 | -28.5 | -28.5 | -12.5 | +6.6 | -18.6 (eqma50/w2) | 64.5% | 1.42 | 0.17 |
| STACK-level perf: 2/3 losing days in a row | 12 | 0% | -6.9 | -7.9 | -10.1 | -6.0 | +5.0 | -1.1 (ld3/day) | 7.4% | 2.30 | 0.80 |
| STACK-level perf: N consecutive losers | 24 | 0% | -25.9 | -24.2 | -23.2 | -7.5 | -0.4 | -2.7 (streak6/w2) | 40.6% | 1.51 | 0.19 |
| STACK-level perf: book day P&L below -X R | 18 | 0% | -31.4 | -31.7 | -28.6 | -10.0 | +3.9 | -19.2 (day_1.5/w2) | 54.9% | 1.41 | 0.41 |
| STACK-level perf: drawdown from rolling peak | 54 | 0% | -31.9 | -33.3 | -29.9 | -14.1 | +7.3 | -22.5 (ddt20_8/w2) | 73.0% | 1.43 | 0.15 |
| STACK-level perf: losing week | 12 | 0% | -22.9 | -27.1 | -28.7 | -7.2 | +8.4 | -18.9 (lw0/w2) | 35.2% | 1.73 | 0.06 |
| STACK-level perf: rolling 1/2/4-week P&L | 54 | 33% | -12.1 | -9.7 | -9.9 | -5.1 | +2.4 | +0.0 (wk4_2/day) | 5.1% | 2.09 | 0.27 |
| STACK-level perf: rolling K-trade P&L < -X R | 72 | 0% | -32.5 | -29.1 | -27.8 | -12.3 | +5.7 | -17.1 (rs20_5/w2) | 52.5% | 1.50 | 0.10 |
| STACK-level perf: rolling profit factor | 24 | 0% | -31.3 | -31.6 | -30.4 | -13.5 | +7.9 | -20.1 (pf20_0.8/w2) | 62.1% | 1.42 | 0.09 |
| STACK-level perf: rolling win rate | 12 | 0% | -27.9 | -18.7 | -19.1 | -7.0 | +0.7 | -9.5 (wr20/w2) | 36.2% | 1.54 | 0.20 |
| STACK-level perf: z-score of last-K mean | 36 | 0% | -25.4 | -17.1 | -15.8 | -7.5 | +1.8 | -1.0 (z20_2.0/w2) | 25.4% | 1.50 | 0.34 |
| combined AND (perf & regime) | 192 | 27% | -0.4 | -0.4 | -0.3 | -0.1 | +0.0 | +1.2 (AND:wk2_3:reg_er_60/day) | 1.0% | 1.63 | 0.39 |
| combined OR (perf | regime) | 192 | 1% | -14.8 | -14.5 | -13.4 | -3.3 | +2.1 | +0.2 (OR:z20_1.5:map_dow/day) | 21.5% | 1.46 | 0.30 |
| equity: 2-sigma band | 15 | 0% | -5.7 | -9.4 | -8.1 | -2.9 | -1.7 | -7.0 (band30/ses) | 10.7% | 1.70 | 0.42 |
| equity: INVERSE control (trade only below MA) | 45 | 0% | -26.4 | -30.0 | -29.5 | -13.7 | +6.0 | -13.5 (eqma20inv/ses) | 76.4% | 1.30 | 0.61 |
| equity: negative slope | 30 | 0% | -20.2 | -21.0 | -20.5 | -6.7 | +6.8 | -11.4 (slope20/ses) | 38.3% | 1.40 | 0.38 |
| equity: trade only above MA | 45 | 0% | -25.8 | -23.3 | -22.1 | -9.2 | +3.3 | -7.9 (eqma50/w2) | 38.4% | 1.45 | 0.28 |
| learned (walk-forward logistic) | 3 | 0% | -0.3 | -0.2 | -0.6 | -2.7 | +0.0 | -0.2 (L:real:0.65/mem) | 0.8% | 1.23 | 0.70 |
| learned, shuffled-label placebo | 6 | 50% | -0.2 | -0.7 | -0.9 | -1.6 | +0.1 | +0.2 (L:sh2:0.6/mem) | 0.8% | 1.23 | 0.59 |
| perf: 2/3 losing days in a row | 30 | 0% | -13.9 | -13.8 | -12.6 | -4.8 | +5.6 | -4.2 (ld3/ses) | 14.1% | 1.82 | 0.25 |
| perf: N consecutive losers | 60 | 0% | -5.9 | -4.7 | -4.3 | -2.4 | +2.5 | -0.5 (streak6/day) | 7.6% | 1.42 | 0.45 |
| perf: book day P&L below -X R | 45 | 33% | -17.9 | -14.8 | -13.7 | -3.8 | -0.0 | +0.0 (day_3.0/ses) | 23.7% | 1.37 | 0.29 |
| perf: drawdown from rolling peak | 135 | 4% | -11.9 | -10.4 | -9.5 | -4.2 | +1.5 | +0.5 (ddd5_8/w3) | 21.2% | 1.41 | 0.42 |
| perf: losing week | 30 | 0% | -9.9 | -16.3 | -16.8 | -7.3 | +6.5 | -4.2 (lw2/ses) | 24.3% | 1.54 | 0.23 |
| perf: rolling 1/2/4-week P&L | 135 | 2% | -6.1 | -6.5 | -6.1 | -3.2 | +2.4 | +0.1 (wk4_5/day) | 12.0% | 1.39 | 0.57 |
| perf: rolling K-trade P&L < -X R | 180 | 8% | -10.0 | -11.1 | -10.5 | -3.5 | +0.6 | +1.0 (rs5_5/day) | 15.7% | 1.51 | 0.60 |
| perf: rolling profit factor | 60 | 0% | -18.4 | -19.8 | -18.9 | -7.8 | +3.3 | -10.5 (pf20_0.8/ma) | 35.1% | 1.43 | 0.35 |
| perf: rolling win rate | 30 | 0% | -10.6 | -9.3 | -8.2 | -1.1 | +3.4 | -2.6 (wr10/ses) | 11.4% | 1.49 | 0.75 |
| perf: z-score of last-K mean | 90 | 8% | -5.3 | -4.5 | -4.4 | -1.0 | -0.0 | +0.4 (z10_2.0/mon) | 7.7% | 1.59 | 0.33 |
| regime: per-book PRE+X' map (vol/dow/daytype/event) | 8 | 50% | +0.0 | -1.0 | -0.8 | +0.1 | +0.2 | +0.6 (map_dow/day) | 3.9% | 1.39 | 0.21 |
| regime: persistent chop/xasset state | 75 | 11% | -14.4 | -16.1 | -13.5 | -6.0 | +3.6 | +1.3 (reg_xasset_120/day) | 26.6% | 1.37 | 0.41 |

Reading: "gain forgone / loss avoided" above 1 means the halted signals were on net winners (the halt gave up more than it saved). Performance triggers sit near 1.0-1.2 in the recent windows; in X' (2023-24) halting helped (median delta positive), in PRE and 2025-26 it hurt: the value of halting by period decays toward negative as the stack got better.

## 3. Resume rules (performance/equity triggers, book scope; median delta, $k/wk)

| resume | cells | d L3M | L6M | HOLD | PRE | X' | median halted share L6M | P(beat random) L6M |
|---|---|---|---|---|---|---|---|---|
| day | 62 | -9.8 | -10.0 | -8.8 | -2.7 | +0.9 | 14.4% | 0.57 |
| day +half-size-first | 62 | -12.0 | -12.2 | -11.2 | -4.5 | +2.7 | 14.4% | 0.61 |
| hi | 62 | -24.4 | -18.9 | -20.8 | -12.5 | +2.7 | 45.3% | 0.29 |
| ma | 62 | -8.0 | -9.8 | -8.8 | -3.6 | +2.9 | 15.7% | 0.23 |
| mon | 62 | -15.4 | -15.2 | -13.6 | -2.8 | +0.7 | 29.4% | 0.83 |
| n2 | 62 | -11.9 | -10.4 | -9.2 | -2.9 | +1.9 | 20.2% | 0.59 |
| n3 | 62 | -14.9 | -11.3 | -10.6 | -4.8 | +2.4 | 25.9% | 0.69 |
| n5 | 62 | -15.8 | -12.5 | -11.1 | -4.8 | +1.9 | 33.1% | 0.87 |
| p10 | 62 | -12.5 | -11.9 | -11.9 | -4.4 | +2.2 | 21.6% | 0.34 |
| p5 | 62 | -9.4 | -10.0 | -8.8 | -4.3 | +2.7 | 15.9% | 0.46 |
| ses | 62 | -10.4 | -9.8 | -8.4 | -1.4 | +1.4 | 9.4% | 0.34 |
| ses +half-size-first | 62 | -7.8 | -10.5 | -9.2 | -3.1 | +2.2 | 9.4% | 0.34 |
| w2 | 62 | -7.2 | -9.4 | -8.1 | -3.5 | +2.2 | 13.9% | 0.32 |
| w2 +half-size-first | 62 | -8.4 | -12.1 | -11.1 | -3.2 | +2.7 | 13.9% | 0.32 |
| w3 | 62 | -11.8 | -11.4 | -10.7 | -4.1 | +2.8 | 20.3% | 0.38 |

## 4. Carried cells (delta > 0 in L6M, HOLD, PRE and X'); excess over the random-halt placebo

| scope | trigger | resume | half | d L3M | d L6M (MDE) | d HOLD | d PRE | d X' | halted share L6M | P(beat random) L6M / HOLD / PRE / X' |
|---|---|---|---|---|---|---|---|---|---|---|
| book | rs5_5 | p5 | 0 | +0.6 | +0.8 (2.9) | +0.7 | +0.6 | +2.1 | 3.0% | 0.89 / 0.90 / 0.94 / 0.34 |
| book | rs5_5 | ses | 2 | +0.2 | +0.8 (2.7) | +0.7 | +0.6 | +0.4 | 1.1% | 0.56 / 0.55 / 0.55 / 0.45 |
| book | map_dow | day | 0 | +1.6 | +0.6 (1.8) | +0.4 | +0.1 | +2.7 | 3.2% | 0.85 / 0.80 / 0.91 / 0.71 |
| book | map_dow | mem | 0 | +1.6 | +0.6 (1.8) | +0.4 | +0.1 | +2.7 | 3.2% | 0.91 / 0.90 / 0.90 / 0.77 |
| book | reg_ci_120 | rev | 0 | -0.1 | +0.4 (0.8) | +0.3 | +0.7 | +0.1 | 0.4% | 0.69 / 0.64 / 0.78 / 0.37 |
| book | rs5_5 | w2 | 2 | +0.1 | +0.4 (2.9) | +0.3 | +0.4 | +1.1 | 2.1% | 0.73 / 0.87 / 0.76 / 0.08 |
| book | AND:rs20_3:reg_ci_60 | ses | 0 | +0.0 | +0.3 (0.8) | +0.3 | +0.1 | +0.0 | 0.0% | 0.00 / 0.62 / 0.36 / 0.00 |
| book | AND:rs20_3:reg_ci_60 | mem | 0 | +0.0 | +0.3 (0.8) | +0.3 | +0.1 | +0.1 | 0.0% | 0.00 / 0.64 / 0.37 / 0.54 |
| book | reg_ci_120 | ses | 0 | -0.5 | +0.2 (1.1) | +0.2 | +1.1 | +0.1 | 0.3% | 0.59 / 0.53 / 0.96 / 0.45 |
| book | reg_ci_120 | mem | 0 | -0.5 | +0.2 (1.1) | +0.2 | +0.6 | +0.1 | 0.3% | 0.66 / 0.63 / 0.58 / 0.44 |
| book | AND:ddt20_5:reg_ci_60 | ses | 0 | +0.0 | +0.2 (0.4) | +0.1 | +0.2 | +0.0 | 0.1% | 0.00 / 0.53 / 0.82 / 0.62 |
| book | AND:ddt20_5:reg_ci_60 | mem | 0 | +0.0 | +0.2 (0.4) | +0.1 | +0.0 | +0.1 | 0.1% | 0.00 / 0.48 / 0.65 / 0.74 |
| book | AND:streak4:reg_xasset_60 | ses | 0 | -0.5 | +0.1 (1.2) | +0.1 | +0.2 | +2.3 | 0.2% | 0.29 / 0.45 / 0.72 / 0.98 |
| book | AND:wk2_3:map_vol | ses | 0 | +0.2 | +0.1 (0.5) | +0.0 | +0.4 | +0.9 | 0.4% | 0.83 / 0.78 / 0.99 / 0.50 |
| book | AND:streak4:reg_xasset_60 | day | 0 | -0.5 | +0.0 (1.1) | +0.0 | +0.5 | +2.5 | 0.2% | 0.30 / 0.44 / 0.95 / 0.99 |
| book | reg_ci_120 | day | 0 | -0.2 | +0.0 (0.9) | +0.0 | +1.0 | +0.6 | 0.8% | 0.41 / 0.43 / 0.72 / 0.86 |
| book | OR:z20_1.5:map_dow | ses | 0 | +0.9 | +0.0 (1.8) | +0.4 | +0.3 | +3.0 | 4.5% | 0.71 / 0.76 / 0.99 / 0.57 |
| book | AND:streak4:reg_xasset_60 | mem | 0 | -0.5 | +0.0 (1.1) | +0.0 | +0.1 | +2.6 | 0.2% | 0.88 / 0.87 / 0.92 / 0.94 |

A carried cell is called CONFIRMED only if delta > MDE, LEAD if positive in all four windows with P(beat random) >= 0.90 in L6M and HOLD, else noise. See section 6.

## 5. Regime, map, combined, learned (median/best, with the cells that are positive in L6M and HOLD)

| trigger | resume | scope | d L3M | L6M | HOLD | PRE | X' | halted share L6M | P(beat random) L6M / HOLD |
|---|---|---|---|---|---|---|---|---|---|
| reg_xasset_120 | day | book | +1.9 | +1.3 | +0.4 | -0.2 | +0.5 | 6.5% | 0.99 / 1.00 |
| AND:wk2_3:reg_er_60 | day | book | +0.9 | +1.2 | +1.6 | -2.7 | +0.9 | 8.8% | 0.89 / 0.95 |
| AND:wk2_3:reg_er_60 | ses | book | -0.4 | +0.8 | +1.1 | -3.6 | +0.7 | 5.3% | 0.71 / 0.83 |
| AND:wk2_3:reg_er_60 | mem | book | -0.7 | +0.8 | +1.1 | -2.1 | +0.9 | 4.4% | 0.64 / 0.77 |
| AND:streak4:reg_xasset_60 | w2 | book | -0.9 | +0.6 | +0.5 | -0.6 | +2.5 | 0.4% | 0.49 / 0.62 |
| map_dow | mem | book | +1.6 | +0.6 | +0.4 | +0.1 | +2.7 | 3.2% | 0.91 / 0.90 |
| map_dow | day | book | +1.6 | +0.6 | +0.4 | +0.1 | +2.7 | 3.2% | 0.85 / 0.80 |
| reg_ci_30 | rev | book | +1.1 | +0.4 | +0.3 | +0.7 | -2.2 | 2.0% | 0.63 / 0.62 |
| reg_ci_120 | rev | book | -0.1 | +0.4 | +0.3 | +0.7 | +0.1 | 0.4% | 0.69 / 0.64 |
| AND:rs20_3:reg_ci_60 | mem | book | +0.0 | +0.3 | +0.3 | +0.1 | +0.1 | 0.0% | 0.00 / 0.64 |
| AND:rs20_3:reg_ci_60 | day | book | +0.0 | +0.3 | +0.3 | +0.1 | -0.0 | 0.0% | 0.00 / 0.74 |
| AND:rs20_3:reg_ci_60 | ses | book | +0.0 | +0.3 | +0.3 | +0.1 | +0.0 | 0.0% | 0.00 / 0.62 |
| AND:z20_1.5:reg_xasset_60 | mem | book | +0.4 | +0.3 | +0.3 | -0.1 | -0.0 | 0.1% | 0.69 / 0.63 |
| AND:wk2_3:reg_ci_60 | w2 | book | +0.4 | +0.2 | +0.1 | -0.0 | -0.1 | 0.5% | 0.00 / 0.00 |
| AND:z20_1.5:reg_xasset_60 | ses | book | +0.4 | +0.2 | +0.2 | -0.0 | -0.0 | 0.3% | 0.39 / 0.43 |
| OR:z20_1.5:map_dow | day | book | +2.0 | +0.2 | +0.1 | -1.1 | +2.8 | 6.3% | 0.76 / 0.72 |
| reg_ci_120 | ses | book | -0.5 | +0.2 | +0.2 | +1.1 | +0.1 | 0.3% | 0.59 / 0.53 |
| reg_ci_120 | mem | book | -0.5 | +0.2 | +0.2 | +0.6 | +0.1 | 0.3% | 0.66 / 0.63 |
| AND:wk2_3:reg_ci_60 | day | book | +0.3 | +0.2 | +0.1 | -0.0 | +0.0 | 0.3% | 0.00 / 0.75 |
| AND:ddt20_5:reg_ci_60 | ses | book | +0.0 | +0.2 | +0.1 | +0.2 | +0.0 | 0.1% | 0.00 / 0.53 |
| AND:rs10_3:reg_ci_60 | mem | book | +0.0 | +0.2 | +0.1 | -0.1 | -0.0 | 0.1% | 0.00 / 0.00 |
| AND:rs10_3:reg_ci_60 | ses | book | +0.0 | +0.2 | +0.1 | +0.1 | -0.0 | 0.1% | 0.00 / 0.00 |
| AND:ddt20_5:reg_ci_60 | mem | book | +0.0 | +0.2 | +0.1 | +0.0 | +0.1 | 0.1% | 0.00 / 0.48 |
| AND:z20_1.5:map_vol | w2 | book | +0.3 | +0.1 | +0.1 | -0.1 | -0.0 | 0.2% | 0.00 / 0.00 |
| AND:rs10_3:map_vol | mem | book | +0.3 | +0.1 | +0.1 | +0.5 | -1.0 | 0.3% | 0.70 / 0.75 |

Learned walk-forward classifier vs its shuffled-label placebo (same code, labels permuted in training):

| cell | d L3M | L6M | HOLD | PRE | X' | halted share L6M |
|---|---|---|---|---|---|---|
| L:real:0.55 | -2.1 | -2.3 | -2.8 | -4.3 | +3.1 | 6.7% |
| L:real:0.6 | -0.3 | -0.2 | -0.6 | -2.7 | -0.7 | 0.8% |
| L:real:0.65 | -0.3 | -0.2 | -0.3 | +0.5 | +0.0 | 0.1% |
| L:sh1:0.55 | -0.4 | -4.7 | -4.4 | -4.6 | +0.6 | 4.0% |
| L:sh1:0.6 | -0.6 | -4.7 | -4.1 | -1.8 | -0.4 | 0.9% |
| L:sh1:0.65 | +0.3 | +0.1 | +0.1 | -1.5 | -0.8 | 0.1% |
| L:sh2:0.55 | -2.0 | -1.3 | -1.5 | -4.2 | +2.1 | 5.2% |
| L:sh2:0.6 | +0.1 | +0.2 | -0.4 | +0.8 | +1.7 | 0.8% |
| L:sh2:0.65 | +0.0 | +0.0 | +0.0 | +0.3 | -0.6 | 0.0% |

Not run (named): HMM chop state, negative-autocorrelation measure, release-window minutes (day flags only), the "everything together" macro-day stack halt, day-of-week and session splits of every cell (the per-book map_dow cell is the DOW halt), quarter-by-quarter drift (window drift X' / PRE / HOLD / L6M is in section 2), block-bootstrap CIs on the delta (the MDE column is the paired-weekly 2.8 x SE).

## 6. Placebos

Random-halt placebo (same number of episodes and the same durations per book, positions shuffled, 100 seeds, paper-track estimator) for all 1786 cells. Over the 930 performance/equity cells: median P(beat random) L6M 0.46, HOLD 0.50, PRE 0.72, X' 0.14; cells with P >= 0.90 in L6M and HOLD: 68 (7.3%); P >= 0.90 in all four windows: 0. (A rule with no information gives about 10% by chance.) Shuffled-performance placebo (halt keyed to another book's results) is stored in `shuf_*` (paper-track $ delta over the window) in hr_table_full.csv.

## 7. Lag cost and equal-risk

Lag (mean r of the first 5 trades after a halt starts minus the book mean r; positive = the book was still good after the halt, i.e. the halt reacted late/wrongly): performance cells median +0.001 R; first 5 trades after a resume: +0.009 R. Equal-risk (SD ratio of the stack weekly series; factor > 1 = the halt lowered weekly SD): median factor L6M 1.13, PRE 1.15; median equal-risk delta (mean x factor minus baseline mean) L6M -7.7k, PRE -1.9k: the SD reduction never pays for the mean given up (structure: lots could be raised by the factor, but the mean forgone is larger).

## 8. Top 15 by L6M delta (shown to quantify selection; best-of-F, not a result)

| scope | trigger | resume | half | d L3M | L6M (MDE) | HOLD | PRE | X' | share L6M | P(beat random) L6M/HOLD |
|---|---|---|---|---|---|---|---|---|---|---|
| book | reg_xasset_120 | day | 0 | +1.9 | +1.3 (9.3) | +0.4 | -0.2 | +0.5 | 6.5% | 0.99/1.00 |
| book | AND:wk2_3:reg_er_60 | day | 0 | +0.9 | +1.2 (4.6) | +1.6 | -2.7 | +0.9 | 8.8% | 0.89/0.95 |
| book | rs5_5 | day | 0 | -0.1 | +1.0 (2.7) | +0.8 | +0.8 | -0.1 | 2.2% | 0.77/0.79 |
| book | rs30_5 | n2 | 0 | +1.8 | +0.9 (2.3) | +0.6 | -1.9 | -0.4 | 6.1% | 0.95/0.86 |
| book | rs5_5 | p5 | 0 | +0.6 | +0.8 (2.9) | +0.7 | +0.6 | +2.1 | 3.0% | 0.89/0.90 |
| book | rs5_5 | ses | 2 | +0.2 | +0.8 (2.7) | +0.7 | +0.6 | +0.4 | 1.1% | 0.56/0.55 |
| book | AND:wk2_3:reg_er_60 | ses | 0 | -0.4 | +0.8 (4.6) | +1.1 | -3.6 | +0.7 | 5.3% | 0.71/0.83 |
| book | AND:wk2_3:reg_er_60 | mem | 0 | -0.7 | +0.8 (3.4) | +1.1 | -2.1 | +0.9 | 4.4% | 0.64/0.77 |
| book | AND:streak4:reg_xasset_60 | w2 | 0 | -0.9 | +0.6 (3.0) | +0.5 | -0.6 | +2.5 | 0.4% | 0.49/0.62 |
| book | reg_xasset_120 | ses | 0 | -0.9 | +0.6 (7.5) | -0.4 | +0.2 | -1.7 | 3.8% | 0.91/0.96 |
| book | rs5_5 | w2 | 0 | -0.2 | +0.6 (2.9) | +0.5 | -1.9 | -0.7 | 2.1% | 0.67/0.76 |
| book | map_dow | day | 0 | +1.6 | +0.6 (1.8) | +0.4 | +0.1 | +2.7 | 3.2% | 0.85/0.80 |
| book | map_dow | mem | 0 | +1.6 | +0.6 (1.8) | +0.4 | +0.1 | +2.7 | 3.2% | 0.91/0.90 |
| book | rs30_5 | mon | 0 | +1.1 | +0.5 (2.7) | -0.1 | -1.4 | -1.3 | 9.3% | 0.94/0.83 |
| book | ddd5_8 | w3 | 0 | +0.9 | +0.5 (1.5) | +0.4 | -2.2 | -0.2 | 4.8% | 0.81/0.80 |