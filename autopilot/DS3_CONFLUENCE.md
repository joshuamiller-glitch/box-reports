# DS3_CONFLUENCE - combinations, controls, frontier (W-CF3) - FIRST PAGE, PARTIAL


<!--LADDER-->
## Size ladder, step 1: the staircase (W-CF3; tables only, no engine; rungs fixed on data up to 2025-04-30, tested 2025-05..2026-10)

VERDICT (data ends 2026-10-30; ): out of sample the count of agreeing independent clusters does not climb: Spearman(count, R) is between -0.07 and +0.07 in every book-session cell, and the shuffled-count test is below 0.05 only in P7 Asia and P7 London (rho 0.055 / 0.056, p 0.033 each, one of 13 cells each such that about 0.6 would be expected by chance). The nonsense ladder built by the same selection (top conditions of the 200 meaningless Block 18 columns by training |z|) climbs about as much (rho -0.17 to +0.10, two cells with p < 0.03). No ladder is worth running on the engine on this evidence; the staircase should be re-read when more of the new blocks are folded in. No PASS claim.

Method: each condition of the joined library (21,094) alone in the cell's training window; outcome R clipped at +-3; day-clustered z; "passes alone" bar = 99th percentile of |z| of the first 100 nonsense columns in the same cell and window; stable sign across training years (>= 30 yes and 30 no in a year); one vote per redundancy cluster (cluster_0.85 ids); count = clusters in their favourable state. Hold-out check: pass rate of the last 100 nonsense columns at that bar.

| cell | train / test trades | bar |z| | real passers alone (rate) | nonsense hold-out pass rate | clusters voting | Spearman(count,R) test | shuffled-count p | nonsense ladder rho (p) |
|--|--|--|--|--|--|--|--|--|
| A7|0 | 439 / 717 | 2.54 | 869 (4.1 %) | 0.0 % | 783 | 0.044 | 0.103 | -0.039 (0.850) |
| H7|0 | 360 / 340 | 2.19 | 1192 (5.7 %) | 3.0 % | 1048 | 0.069 | 0.113 | 0.078 (0.053) |
| K7|0 | 1026 / 1570 | 2.47 | 664 (3.1 %) | 3.0 % | 526 | -0.006 | 0.577 | 0.019 (0.190) |
| K7|1 | 768 / 1013 | 2.41 | 703 (3.3 %) | 4.0 % | 604 | 0.026 | 0.240 | 0.021 (0.230) |
| K7|3 | 918 / 647 | 2.10 | 818 (3.9 %) | 1.0 % | 685 | -0.069 | 0.970 | -0.056 (0.887) |
| K7|4 | 698 / 438 | 2.15 | 1143 (5.4 %) | 0.0 % | 965 | -0.022 | 0.783 | -0.038 (0.813) |
| M7|1 | 1175 / 1314 | 2.24 | 577 (2.7 %) | 3.0 % | 486 | 0.014 | 0.217 | 0.011 (0.317) |
| M7|3 | 874 / 622 | 2.29 | 697 (3.3 %) | 3.0 % | 581 | 0.017 | 0.367 | 0.089 (0.003) |
| P7|0 | 907 / 1254 | 2.38 | 929 (4.4 %) | 2.0 % | 735 | 0.055 | 0.033 | 0.034 (0.083) |
| P7|1 | 710 / 827 | 2.48 | 617 (2.9 %) | 2.0 % | 531 | 0.056 | 0.033 | 0.007 (0.360) |
| P7|3 | 655 / 395 | 2.29 | 836 (4.0 %) | 2.0 % | 707 | -0.069 | 0.913 | 0.021 (0.410) |
| U7|0 | 327 / 359 | 2.38 | 1575 (7.5 %) | 1.0 % | 1312 | -0.020 | 0.680 | 0.100 (0.020) |
| U7|1 | 338 / 307 | 2.14 | 1387 (6.6 %) | 2.0 % | 1205 | -0.049 | 0.897 | -0.168 (1.000) |

Calibration finding (Block 18): at the nonsense 99th-percentile bar, real conditions pass alone at 2.7-7.5 % per cell against 0-4 % for the hold-out nonsense, i.e. only about 1.5-3 times the nonsense rate, so most "passers" are still noise; with 600-1,500 passers per cell the count has hundreds of voting clusters and the staircase averages them into nothing. A higher bar (z above the nonsense maximum) and a short pre-specified list per cell are the next step; the per-rung R / $ / win rate / MFE / MAE tables are in /mnt/l2/l2vast/_confl/cf3/ladder_stairs.pkl (code ladder_stair.py).
<!--/LADDER-->


<!--FIX-->
## Fixed test: every signal gated, kept trades sized (W-CF3; directive DIRECTIVE_FIX_TESTS_20261115 PART A)

Gate = decision computed on the FULL signal universe (191,520 signals incl. the replacement signals that appear when a skip frees the book); the hook looks up every entry the engine evaluates; `found` = share of executed trades whose signal had a table decision. Engine: JN05W2, all layers ON, measured fills, engine fee 1.18 (the $4.84 column reprices at 3.66 per contract per trade), base lots (x1.75 live beside). Gate judged as a gate: expectancy per trade and per R, max DD in $ and R, worst week, profit factor, $/wk after sizing. Matched-count percentile = share of equal-count random subsets (within month) of the BASE trades of the cell that the gated cell beats on expectancy / has a WORSE drawdown than. R of a trade uses the signal bracket (stp_pts) from the universe.

### A6 sanity check (planted +0.3 R on trades where c_A_trend_15m, c_D_sess_side and c_E_ret15_with are all true; table-level and engine)

```
L3M PLANT +0.0R gated: n 1304 exp $120 expR 0.056 DD $103361 DD_R 60.5 ww -47069 PF 1.16 | ungated base: n 1875 exp $134 expR 0.046 DD $52233 DD_R 20.8 ww -36371 PF 1.17 | matched-count pctl exp 0.426 dd 0.000 | trades with all three true in gated set 1.00, signals found in table 1.00
L3M PLANT +0.3R gated: n 1304 exp $753 expR 0.356 DD $16150 DD_R 6.4 ww 15211 PF 2.91 | ungated base: n 1875 exp $444 expR 0.187 DD $15807 DD_R 9.0 ww 6734 PF 1.72 | matched-count pctl exp 1.000 dd 0.596 | trades with all three true in gated set 1.00, signals found in table 1.00
L6M PLANT +0.0R gated: n 2863 exp $175 expR 0.070 DD $103361 DD_R 60.5 ww -47069 PF 1.24 | ungated base: n 4169 exp $158 expR 0.061 DD $52233 DD_R 20.8 ww -36371 PF 1.20 | matched-count pctl exp 0.813 dd 0.000 | trades with all three true in gated set 1.00, signals found in table 1.00
L6M PLANT +0.3R gated: n 2863 exp $805 expR 0.370 DD $16150 DD_R 6.4 ww -2149 PF 3.06 | ungated base: n 4169 exp $471 expR 0.204 DD $21148 DD_R 9.0 ww 2279 PF 1.76 | matched-count pctl exp 1.000 dd 0.898 | trades with all three true in gated set 1.00, signals found in table 1.00
```

A6 READING (engine part): the +0.3 R plant is recovered on EXPECTANCY and NOT on drawdown.
- Expectancy: gated planted $753 / 0.356 R per trade vs base planted $444 / 0.187 R in L3M (L6M $805 / 0.370 vs $471 / 0.204): the R gain of +0.169 (L3M) and +0.166 (L6M) equals the expected 0.30 x (1 - 0.45) = 0.165, and the matched-count percentile on expectancy is 1.000 in both windows. Unplanted (the same gate on real outcomes): 0.056 R vs 0.046 R, percentile 0.43 (L3M) / 0.81 (L6M): no real edge in these three conditions, correctly not flagged.
- Drawdown: planted DD $16,150 vs $15,807 (L3M) and $16,150 vs $21,148 (L6M); matched-count DD percentile 0.596 and 0.898, below the 0.95 the order requires. So the pipeline DOES NOT pass its own drawdown control on a planted edge that doubles expectancy: the drawdown criterion has too little power at 3-6 month windows (and it is the stack, in which the same big losing days occur whichever trades are kept). Consequence: a drawdown-percentile bar of 0.95 on 3-6 month windows cannot be the pass/fail rule for a gate; judge by expectancy (per trade and per R) with the matched-count and shuffled controls, and report drawdown as a secondary number with the longer windows (HOLD / full) where power is higher.
- The UNPLANTED engine gate is worse on drawdown than every random subset of the same size (DD $103,361 vs $52,233, DD_R 60.5 vs 20.8, percentile 0.000): keeping only 'all three true' signals concentrates the book on trend-aligned days and the engine run gives a much deeper drawdown than a random subset of the base trades. This is a path effect (which trades the stack can take after the skips) that the table-level screen cannot see; it is the reason every checklist needs its engine run.
- What this proves: the hook, the full-universe table (found = 100 % of executed signals had a decision), the replacement handling and the scoring chain recover an edge that exists in outcomes. What it does not prove: that a real edge would survive the engine's path effects; the plant is added after the fact to the trade file.

A1 READING (FIRST PASS, P7 Asia USER_SET_V0 all-5 only; the other 12 sets are still running): with EVERY signal gated the old verdict flips.
- OLD (taken-only table): the cell kept 219 of 243 trades in L3M (replacements filled the freed slots), expectancy fell from $408 to $80 per trade and the STACK drawdown rose from $52k to $78k.
- NEW skip-only: 84 trades kept in L3M (158 in L6M of 575), expectancy $922 (L6M $887) vs $408 ($545) per trade, 0.091 R (0.123) vs 0.078 R (0.118), cell max DD $17,964 vs $39,663 in L3M (-55 %) and $18,945 vs $39,663 in L6M, stack drawdown unchanged ($52,182 vs $52,233); matched-count percentile for expectancy 0.947 / 0.933 and for drawdown 0.863 / 0.957; profit factor 1.61 / 1.56 vs 1.24 / 1.33. $/wk of the cell falls (L3M 5,956 vs 7,634; L6M 5,190 vs 11,598).
- A2 skip + size: x1.5 gives L3M $8,040/wk (above the base 7,634) with cell DD $27,067 (-32 %), expectancy percentile 1.000, stack DD $52,690; in L6M x1.5 gives only $7,209/wk (base 11,598) at DD $27,338 (-31 %); x2 and x(1/share, cap 3) raise $/wk modestly and raise the cell DD back toward the base (x3: L6M DD $49,282, stack DD $56,428). Realised lots/wk (L6M) 98 base, 28 skip-only, 40 / 47 / 57 sized: the P7 caps and integer lots stop the sized versions from restoring the lost lots.
- So a P7-Asia all-5 gate is a real drawdown and per-trade gain in the engine; whether it is a gain in dollars depends on the window and on re-sizing; older windows (HOLD, PRE, X'; USER_SET_V0 was negative in 2023) are not scored yet. Flag PATH EFFECT UNEXPLAINED stays on this row until the diagnostics land (here the stack drawdown did not change).

### A1/A2 P7 Asia and K7 Asia: OLD (taken-only table, replacements ungated) vs NEW (every signal gated), skip-only and skip + size

**P7A_V0all5, Asia, window L3M**

| set | cell trades | $/trade | R/trade | max DD $ | max DD R | worst wk $ | PF | $/wk | $/wk x1.75 | $/wk @4.84 | lots/wk | matched pctl exp / DD | stack DD $ | stack $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| JN05W2 base | 243 | 408 | 0.078 | 39663 | 8.5 | -31051 | 1.24 | 7634 | 13360 | 7324 | 85 | - / - | 52233 | 19346 |
| OLD skip-only (TL3_CF_U3) | 219 | 80 | 0.019 | 38887 | 8.0 | -26139 | 1.04 | 1345 | 2354 | 1067 | 76 | 0.002 / 0.322 | 78338 | 11570 |
| NEW K | 84 | 922 | 0.091 | 17964 | 3.7 | -15431 | 1.61 | 5956 | 10423 | 5851 | 29 | 0.946 / 0.858 | 52182 | 15013 |
| NEW S15 | 84 | 1244 | 0.118 | 27067 | 3.4 | -23274 | 1.58 | 8040 | 14069 | 7886 | 42 | 0.996 / 0.512 | 52690 | 18863 |
| NEW S2 | 82 | 1523 | 0.121 | 32750 | 3.2 | -28957 | 1.61 | 9609 | 16815 | 9426 | 50 | 1.000 / 0.338 | 52182 | 20543 |
| NEW SI | 76 | 1856 | 0.134 | 36187 | 2.6 | -31115 | 1.57 | 10850 | 18987 | 10631 | 60 | 1.000 / 0.196 | 54567 | 20550 |

**P7A_SL2ge4, Asia, window L3M**

| set | cell trades | $/trade | R/trade | max DD $ | max DD R | worst wk $ | PF | $/wk | $/wk x1.75 | $/wk @4.84 | lots/wk | matched pctl exp / DD | stack DD $ | stack $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| JN05W2 base | 243 | 408 | 0.078 | 39663 | 8.5 | -31051 | 1.24 | 7634 | 13360 | 7324 | 85 | - / - | 52233 | 19346 |
| OLD skip-only (TL3_CF_U6) | 217 | 229 | 0.040 | 39348 | 6.6 | -28522 | 1.13 | 3826 | 6696 | 3546 | 77 | 0.038 / 0.262 | 84575 | 13679 |
| NEW K | 106 | 324 | 0.055 | 32783 | 6.2 | -21193 | 1.18 | 2642 | 4623 | 2500 | 39 | 0.478 / 0.360 | 83867 | 12671 |
| NEW S15 | 104 | 341 | 0.046 | 45759 | 5.3 | -26879 | 1.13 | 2726 | 4770 | 2523 | 55 | 0.468 / 0.070 | 94202 | 11471 |
| NEW S2 | 102 | 795 | 0.071 | 51422 | 5.0 | -38700 | 1.28 | 6237 | 10915 | 5998 | 65 | 0.920 / 0.048 | 107559 | 13662 |

**K7A_V0ge4, Asia, window L3M**

| set | cell trades | $/trade | R/trade | max DD $ | max DD R | worst wk $ | PF | $/wk | $/wk x1.75 | $/wk @4.84 | lots/wk | matched pctl exp / DD | stack DD $ | stack $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| JN05W2 base | 333 | 86 | 0.056 | 9732 | 8.1 | -4188 | 1.16 | 2195 | 3841 | 2084 | 30 | - / - | 52233 | 19346 |
| OLD skip-only (TL3_CF_U1) | 261 | 119 | 0.086 | 16826 | 9.4 | -3101 | 1.22 | 2388 | 4179 | 2300 | 24 | 0.840 / 0.060 | 45259 | 18945 |
| NEW K | 211 | 155 | 0.127 | 10445 | 5.2 | -4376 | 1.29 | 2510 | 4392 | 2438 | 20 | 0.898 / 0.544 | 46424 | 18135 |

**K7A_V0ge3, Asia, window L3M**

| set | cell trades | $/trade | R/trade | max DD $ | max DD R | worst wk $ | PF | $/wk | $/wk x1.75 | $/wk @4.84 | lots/wk | matched pctl exp / DD | stack DD $ | stack $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| JN05W2 base | 333 | 86 | 0.056 | 9732 | 8.1 | -4188 | 1.16 | 2195 | 3841 | 2084 | 30 | - / - | 52233 | 19346 |
| OLD skip-only (TL3_CF_U2) | 280 | 128 | 0.086 | 10577 | 7.0 | -3379 | 1.25 | 2760 | 4830 | 2668 | 25 | 0.928 / 0.572 | 43297 | 19742 |

**P7A_V0all5, Asia, window L6M**

| set | cell trades | $/trade | R/trade | max DD $ | max DD R | worst wk $ | PF | $/wk | $/wk x1.75 | $/wk @4.84 | lots/wk | matched pctl exp / DD | stack DD $ | stack $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| JN05W2 base | 575 | 545 | 0.118 | 39663 | 8.5 | -31051 | 1.33 | 11598 | 20297 | 11240 | 98 | - / - | 52233 | 24470 |
| OLD skip-only (TL3_CF_U3) | 475 | 348 | 0.072 | 38887 | 8.0 | -26139 | 1.19 | 6129 | 10726 | 5832 | 81 | 0.018 / 0.462 | 78338 | 18429 |
| NEW K | 158 | 887 | 0.123 | 18945 | 3.8 | -15431 | 1.56 | 5190 | 9083 | 5089 | 28 | 0.934 / 0.962 | 52182 | 15796 |
| NEW S15 | 155 | 1256 | 0.136 | 27338 | 3.4 | -23274 | 1.56 | 7209 | 12616 | 7064 | 40 | 0.998 / 0.714 | 52690 | 19086 |
| NEW S2 | 150 | 1429 | 0.123 | 37276 | 3.5 | -28957 | 1.54 | 7939 | 13893 | 7768 | 47 | 1.000 / 0.288 | 52182 | 20248 |
| NEW SI | 142 | 1376 | 0.109 | 49282 | 3.0 | -31115 | 1.38 | 7236 | 12663 | 7027 | 57 | 0.998 / 0.114 | 56428 | 17918 |

**P7A_SL2ge4, Asia, window L6M**

| set | cell trades | $/trade | R/trade | max DD $ | max DD R | worst wk $ | PF | $/wk | $/wk x1.75 | $/wk @4.84 | lots/wk | matched pctl exp / DD | stack DD $ | stack $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| JN05W2 base | 575 | 545 | 0.118 | 39663 | 8.5 | -31051 | 1.33 | 11598 | 20297 | 11240 | 98 | - / - | 52233 | 24470 |
| OLD skip-only (TL3_CF_U6) | 496 | 384 | 0.077 | 42087 | 6.9 | -28522 | 1.21 | 7051 | 12340 | 6733 | 87 | 0.016 / 0.208 | 84575 | 18228 |
| NEW K | 250 | 662 | 0.133 | 32783 | 6.2 | -21193 | 1.38 | 6130 | 10727 | 5965 | 45 | 0.764 / 0.574 | 83867 | 17663 |
| NEW S15 | 245 | 866 | 0.120 | 45759 | 5.3 | -26879 | 1.36 | 7855 | 13747 | 7621 | 64 | 0.948 / 0.158 | 94202 | 17748 |

**K7A_V0ge4, Asia, window L6M**

| set | cell trades | $/trade | R/trade | max DD $ | max DD R | worst wk $ | PF | $/wk | $/wk x1.75 | $/wk @4.84 | lots/wk | matched pctl exp / DD | stack DD $ | stack $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| JN05W2 base | 787 | 88 | 0.067 | 16767 | 9.7 | -8074 | 1.16 | 2567 | 4491 | 2442 | 34 | - / - | 52233 | 24470 |
| OLD skip-only (TL3_CF_U1) | 590 | 139 | 0.105 | 17345 | 9.4 | -4447 | 1.27 | 3032 | 5306 | 2938 | 26 | 0.974 / 0.474 | 45259 | 24897 |
| NEW K | 455 | 144 | 0.113 | 11103 | 7.2 | -4376 | 1.27 | 2421 | 4238 | 2347 | 20 | 0.914 / 0.842 | 46424 | 22458 |

**K7A_V0ge3, Asia, window L6M**

| set | cell trades | $/trade | R/trade | max DD $ | max DD R | worst wk $ | PF | $/wk | $/wk x1.75 | $/wk @4.84 | lots/wk | matched pctl exp / DD | stack DD $ | stack $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| JN05W2 base | 787 | 88 | 0.067 | 16767 | 9.7 | -8074 | 1.16 | 2567 | 4491 | 2442 | 34 | - / - | 52233 | 24470 |
| OLD skip-only (TL3_CF_U2) | 634 | 116 | 0.077 | 15054 | 7.0 | -5480 | 1.22 | 2712 | 4746 | 2612 | 27 | 0.892 / 0.654 | 43297 | 23919 |

### A5 single conditions per session as size / target (exact engine, session = all books of the session; prereg autopilot/CONFLUENCE_SINGLE_PER_SESSION_PREREG.md sha 8e1e0a42645dc378)

**window L3M** (reference: JN05W2 same session)

| set | cell trades | $/trade | R/trade | max DD $ | max DD R | worst wk $ | PF | $/wk | $/wk x1.75 | $/wk @4.84 | lots/wk | matched pctl exp / DD | stack DD $ | stack $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| A1 go (S15) NQ 5-min Supertrend with the trade | 879 | 184 | 0.052 | 47874 | 16.1 | -41224 | 1.19 | 12418 | 21732 | 11850 | 155 | 0.000 / 1.000 | 55081 | 16003 |
| A2 go (S15) NQ 5-min ADX/DI with the trade (B5 NQ  | 875 | 216 | 0.053 | 43302 | 17.4 | -39416 | 1.23 | 14558 | 25476 | 13985 | 156 | 0.937 / 0.980 | 54453 | 16138 |
| A3 go (S15) NQ 5-min squeeze momentum with the tra | 875 | 234 | 0.047 | 54170 | 17.7 | -35221 | 1.25 | 15781 | 27616 | 15197 | 159 | 1.000 / 0.000 | 58793 | 19495 |
| A4 go (S15) NQ 15-min price holding the 21 with th | 865 | 254 | 0.057 | 39833 | 16.7 | -24098 | 1.28 | 16926 | 29621 | 16361 | 154 | 1.000 / 0.977 | 64099 | 18528 |
| A5 go (S15) RTY 15-min Supertrend with the trade | 880 | 192 | 0.058 | 40315 | 15.8 | -20902 | 1.21 | 13007 | 22762 | 12460 | 149 | 0.030 / 1.000 | 61616 | 20915 |
| A6 go (S15) NQ 5-min EMA stack (20/50 order) with  | 867 | 275 | 0.058 | 45192 | 17.5 | -29457 | 1.30 | 18325 | 32069 | 17752 | 157 | 1.000 / 0.783 | 68216 | 22567 |
| L1 go (S15) ZN moving with the trade over 60 min ( | 653 | 116 | 0.017 | 54335 | 30.0 | -30130 | 1.14 | 5810 | 10167 | 5462 | 95 | 1.000 / 0.977 | 49909 | 20698 |
| L2 against (S15) 3 of 4 indexes (ES RTY YM MEGA) ADX/DI | 662 | 89 | 0.031 | 57935 | 26.5 | -32516 | 1.13 | 4510 | 7893 | 4231 | 76 | 0.993 / 0.947 | 49667 | 20400 |
| L3 against (S15) ES 1-min Supertrend with the trade | 665 | 98 | 0.039 | 58456 | 23.7 | -37942 | 1.14 | 5004 | 8757 | 4708 | 81 | 1.000 / 0.950 | 55046 | 20002 |

**window L6M** (reference: JN05W2 same session)

| set | cell trades | $/trade | R/trade | max DD $ | max DD R | worst wk $ | PF | $/wk | $/wk x1.75 | $/wk @4.84 | lots/wk | matched pctl exp / DD | stack DD $ | stack $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| A1 go (S15) NQ 5-min Supertrend with the trade | 2022 | 252 | 0.085 | 47874 | 16.1 | -41224 | 1.27 | 18871 | 33023 | 18230 | 175 | 0.000 / 1.000 | 55081 | 23381 |
| A2 go (S15) NQ 5-min ADX/DI with the trade (B5 NQ  | 2000 | 248 | 0.083 | 52537 | 20.4 | -39416 | 1.26 | 18342 | 32099 | 17705 | 174 | 0.060 / 0.023 | 54453 | 22412 |
| A3 go (S15) NQ 5-min squeeze momentum with the tra | 2006 | 268 | 0.081 | 54170 | 17.7 | -35221 | 1.28 | 19947 | 34908 | 19292 | 179 | 0.993 / 0.000 | 58793 | 24617 |
| A4 go (S15) NQ 15-min price holding the 21 with th | 1997 | 311 | 0.090 | 39833 | 17.0 | -24098 | 1.34 | 23013 | 40274 | 22373 | 175 | 1.000 / 0.980 | 64099 | 26520 |
| A5 go (S15) RTY 15-min Supertrend with the trade | 2033 | 268 | 0.098 | 40315 | 15.8 | -20902 | 1.30 | 20158 | 35276 | 19552 | 165 | 1.000 / 1.000 | 61616 | 27448 |
| A6 go (S15) NQ 5-min EMA stack (20/50 order) with  | 1997 | 338 | 0.090 | 45192 | 17.5 | -29457 | 1.38 | 25025 | 43793 | 24393 | 172 | 1.000 / 0.763 | 68216 | 29175 |
| L1 go (S15) ZN moving with the trade over 60 min ( | 1334 | 44 | 0.001 | 54335 | 31.7 | -30130 | 1.05 | 2155 | 3770 | 1820 | 91 | 0.653 / 0.960 | 49909 | 23749 |
| L2 against (S15) 3 of 4 indexes (ES RTY YM MEGA) ADX/DI | 1398 | 66 | 0.014 | 57935 | 26.5 | -32516 | 1.10 | 3441 | 6022 | 3161 | 76 | 1.000 / 0.937 | 49667 | 25982 |

<!--/FIX-->

VERDICT: SUPERSEDED BY THE FIXED TEST (top section when present). The tests below were built wrongly in two ways: (1) the exact-engine checklist gates (section 3b) applied only to signals JN05W2 took, so replacement signals passed ungated; (2) the stack-wide search and its stack-wide bar (section 4) are set aside. Nothing below is a verdict on confluence; A6 (planted-edge sanity check) comes first in the fixed test. Pre-registered USER_SET_V0 / SL lists remain table-level leads: P7 Asia, K7 Asia (see section 1). No PASS claim.

Basis: exact-engine taken trades JN05W2, base lots, engine fee $1.18/contract (pnl) - the $4.84 column pnl484 is carried in the table; skipped signals are not in the table yet (taken only); all numbers are in-sample FULL HISTORY for the pre-registered list (nothing tuned, so no search bias; 45 book-session x rule cells were looked at, so about 0.1 passes by chance are expected at the 5 % level on both tests). Code code/th_confl_cf3; data /mnt/l2/l2vast/_confl/cf3/.

## 1. USER_SET_V0 (step 4d, untuned, registered DECISIONS.md sha 13e2d06bd31c20a1; columns c_U_1..c_U_5 by W-CF1, unknown = 0)
Stack-wide, full history (matched-count control: 500 random subsets of the same size within book/session/month; percentile = share of random subsets the checklist beats; DD percentile = share with a WORSE max drawdown):

| rule | trades kept | per day | $/trade | all trades $/trade | max DD | all-trades DD | expectancy pctl | DD pctl | bootstrap 95 % interval of $/trade |
|--|--|--|--|--|--|--|--|--|--|
| all 5 | 4,457 | 4.8 | 152 | 106 | 58,726 | 92,243 | 0.99 | 0.68 | 72 .. 232 |
| at least 4 | 11,206 | 12.1 | 141 | 106 | 112,370 | 92,243 | 1.00 | 0.13 | 86 .. 192 |
| at least 3 | 15,321 | 16.5 | 125 | 106 | 98,040 | 92,243 | 0.99 | 0.37 | 80 .. 169 |

Reading: the list picks better-than-average entries (expectancy percentile 0.99-1.00 against equal-count random subsets), but the drawdown is NOT better than random subsets of the same size (DD percentile 0.68 / 0.13 / 0.37 versus the 0.95 required), so by the step 5 rule it is "fewer trades, a better average, no drawdown protection" stack-wide. It stays above the 3 trades/day floor at every k. Recent windows: all-5 at L3M/L6M has 233/234 $/trade versus 134/159 for all entries but max DD equal to the all-trades DD (52,670 vs 52,233, the 2026-W44 week); older windows X' (2023-04..2024-01) is the exception: 19 vs 50 $/trade.

Cells where a rule beats both 95th-percentile tests (n >= 150 full history), of 45 cell-rule combinations:
- K7 Asia (K7|0), at least 4: 1,116 of 2,596 trades, $174 vs $89 per trade, max DD 16,126 vs 26,763 (-40 %); expectancy pctl 1.00, DD pctl 0.95. Windows: L3M 221 vs 86 (DD 6,891 vs 9,732), L6M 188 vs 88, HOLD 213 vs 111, PRE 174 vs 78, GAP 112 vs 83; X' 11 vs 24 (fails). 
- K7 Asia, at least 3: 1,590 trades, $131 vs $89, DD 18,458 vs 26,763 (-31 %); pctl 0.98 / 0.96; positive in all six windows including X' (81 vs 24).
- P7 Asia (P7|0), all 5: 352 of 2,161 trades, $1,032 vs $424 per trade, DD 29,674 vs 75,069 (-60 %), pctl 1.00 / 0.97; but only 96 trades in L6M and 45 in L3M (floor 40 met in L6M), X' fails (-44 vs 122), GAP weak (111 vs 494). P7 has the heavy tail (7-lot stops): the R-based rerun is queued.
- Not yet done for these: walk-forward consistency is trivial for a fixed list (nothing is refit) so the evidence is the window table above; W44-removed and the $4.84 column are in user_set_v0.csv (K7 Asia at least 4 with W44 removed: $180 per trade, DD unchanged because the W44 week is outside this cell's drawdown); the exact-engine verdict (take/skip gate on top of the live stack, all layers ON) is pending the hook identity run (TL3_CF_ID).
- Tolerant programme gate (DD cut > -2 %, mean $/wk not lower than -3 %) mostly FAILS for a skip rule because $/wk falls when trades are skipped; it passes for K7 Asia at least 4 only in L3M. The gate was written for sizing dials; for a gate on entries the relevant tests are expectancy and DD per the order.

Full table: /mnt/l2/l2vast/_confl/cf3/user_set_v0.csv (every book-session cell, three rules, seven windows).


## 1b. The three USER_SET_V0 leads re-checked (R units, fixed list in 2-week blocks, heavy tail, leave-one-month-out; output /mnt/l2/l2vast/_confl/cf3/userset_leads.txt)
The list is fixed, so nothing is chosen on a trailing window; "walk-forward" here is the out-of-sample behaviour by time slice.

| lead | R per trade kept vs all | max DD in R kept vs all | matched-count pctl in R: expectancy / drawdown | 2-week blocks kept beats all | by year kept vs all $/trade (n kept) | mean without the top 10 wins | leave-one-month-out $/trade |
|--|--|--|--|--|--|--|--|
| K7 Asia, at least 4 | 0.106 vs 0.053 | 12.3 vs 16.7 | 0.997 / 0.85 | 51 of 92 (55 %) | 2023 -79 vs 5 (90); 2024 159 vs 72 (208); 2025 215 vs 71 (333); 2026 200 vs 126 (485) | 154 | 157 .. 185 |
| K7 Asia, at least 3 | 0.073 vs 0.053 | 13.9 vs 16.7 | 0.93 / 0.82 | 59 of 93 (63 %) | 2023 47 vs 5; 2024 106 vs 72; 2025 117 vs 71; 2026 168 vs 126 | 117 | 117 .. 142 |
| P7 Asia, all 5 | 0.200 vs 0.077 | 4.0 vs 12.3 | 0.998 / 0.997 | 32 of 55 (58 %) | 2023 -100 vs 94 (22); 2024 1,112 vs 452 (69); 2025 1,243 vs 504 (113); 2026 1,002 vs 436 (148) | 816 | 907 .. 1,083 |

Reading. In $ the K7 Asia at least 4 pass both 95th-percentile tests (drawdown pctl 0.951); in R the drawdown percentile falls to 0.85, so K7 Asia is a better-expectancy filter with a drawdown benefit that is only borderline: lead, not confirmed. P7 Asia all-5 passes in both units (R drawdown 4.0 vs 12.3 R, pctl 0.997), is not a tail artefact (mean 816 without its top 10 wins, 907-1,083 leaving any one month out, top 5 wins are 12 % of its total), the exit mix is not different (Target 49 % vs 44 %), and it is positive in 2024, 2025, 2026 but NEGATIVE in 2023 (X', 22 trades, -$100 vs +$94): the older window does not hold, so under the rule "must hold in recent AND older windows" it is a RECENT-ONLY lead (2.5 years, 330 trades). The per-block hit rate (55-63 %) says the gain arrives as many modest edges rather than a few blocks. Floors: K7 Asia L6M 340 / 467 trades, P7 L6M 96, full history 1,116 / 1,590 / 352 (all above 40 and 150). Next: exact-engine take/skip gate on the live stack (needs TL3_CF_ID identity first).

## 1c. Search-level control bar versus library size (bit-light search, code cf3_big.py; in-sample best lift-t, greedy must-have list or best-k score; shuffled = outcomes permuted within book/session/month)
K7 Asia, 10 shuffles (the 50-shuffle run and STACK run are in progress): library 50 conditions: real 4.8, shuffled median 5.1, 95th pctl 5.7; 150 conditions: real 8.7, shuffled 6.9 / 7.3; 330 conditions: real 9.4, shuffled 8.0 / 9.0 (max 9.0). The bar rises with the library as the order expects, and the real best only clears it at 150 and 330 columns. Files bar_*.csv.

## 4. The joined library (all column sets) - stack-wide search, shuffled-outcome bar by library size, walk-forward (W-CF3, 2026-11-15)
Library: 21,094 yes/no conditions on the 19,798 TAKEN signals (engine $ outcomes), from W-CF1 (A B C D E K L S T U and M 5,537), W-CF4 (osc 3,047, trend 3,221, smc 1,858, irl 273, ml 216, vol 441), W-CF5 (named systems 4,200), W-CF6 (1,314), W-CF2 (F-J and other-market states 626); columns with fewer than 50 yes or 50 no dropped. Raw v_* values are not conditions. Skipped-signal rows are NOT used in any result (hypothetical points only as a screen, none run yet). Redundancy clusters (outcome-free, random-projection correlation, |phi| >= 0.85): 16,330 clusters (13,204 singletons, largest 28; 1,323 clusters span more than one block), so most columns are NOT near-duplicates at this threshold. The search runs on one leader per cluster (16,330) chosen without looking at outcomes.

**Search-level control bar by library size** (in-sample best lift-t of greedy must-have list or best-k score, STACK, 50 shuffles of outcomes within book/session/month; file bigbar_STACK_0.85_pnl.csv):

| library (random leaders) | real best | shuffled median | shuffled 95th | shuffled max | share of shuffles >= real |
|--|--|--|--|--|--|
| 50 | 10.9 | 7.7 | 8.5 | 8.6 | 0.00 |
| 150 | 12.3 | 9.5 | 11.5 | 12.7 | 0.02 |
| 330 | 13.6 | 12.6 | 14.8 | 16.0 | 0.26 |
| 1,000 | 21.5 | 19.2 | 22.8 | 23.1 | 0.14 |
| 3,000 | 25.0 | 23.8 | 26.8 | 29.3 | 0.32 |
| 16,330 (all) | 28.5 | 29.2 | 32.8 | 34.3 | 0.62 |

Reading: the bar rises steeply with the library, and from 330 conditions up the best checklist found on real outcomes is no better than what the same search finds on shuffled outcomes. The small-library rows pass only because a few columns (book / session / state conditions) carry a real but small effect; adding the other 20,000 conditions adds search power for noise, not signal. Nothing found by search on the full library beats its own shuffled bar.

**Walk-forward of the whole library, stack-wide** (trailing 52 weeks, 2-week refits, first test 2023-10-16, greedy over leaders, minimum kept share of the training window = strictness; matched-count control 1,000 subsets; files wfbig_*.json):

| strictness (min kept share) | OOS trades kept (per day) | $/trade kept vs all | max DD kept vs all | expectancy / DD percentile | item stability across refits | 95 % bootstrap of $/trade |
|--|--|--|--|--|--|--|
| minimum 60 trades | 240 (0.3) | 334 vs 117 | 30,589 vs 92,243 | 0.83 / 0.59 | 0.15 | -113 .. 800 |
| 10 % | 1,691 (2.2) | 152 vs 117 | 72,020 vs 92,243 | 0.31 / 0.15 | 0.13 | -3 .. 302 |
| 20 % | 3,329 (4.2) | 235 vs 117 | 122,156 vs 92,243 | 0.99 / 0.01 | 0.17 | 122 .. 345 |
| 40 % | 6,823 (8.7) | 152 vs 117 | 137,032 vs 92,243 | 0.90 / 0.01 | 0.18 | 71 .. 228 |

Reading: no strictness passes. The loosest versions raise expectancy but make the drawdown WORSE than random subsets of the same size (DD percentile 0.01); the tightest has too few trades (0.3 per day, below the 3 per day floor) and a bootstrap interval spanning zero; the chosen items change at almost every refit (Jaccard 0.13-0.18, i.e. noise). Verdict for the stack-wide search on the full library: fewer trades, no drawdown protection, unstable items. No exact-engine run is justified for it. Next: the same by book and session (cells), the per-block importance table (running: blocks_STACK.csv, real minus shuffled 95th percentile for each block alone and added to the base blocks), and 50 shuffled walk-forward reruns for any cell with a lead. Reminder: universe-wide significance counts are not findings.

## 5. Pre-specified small lists (registered before scoring: autopilot/CONFLUENCE_SMALL_LISTS_PREREG.md, sha256[:16] 1c1580364fd5b5f4, DECISIONS.md)
One item per family (trend, level, VWAP, volume/tape, momentum), plain standard item, chosen by definition not by outcomes. Same controls as USER_SET_V0 (matched-count 500 draws; full-history in-sample; results /mnt/l2/l2vast/_confl/cf3/lists_SL*.csv). Stack-wide none passes (drawdown percentiles 0.03-0.74). Cells passing both 95th tests, of 48 cell-rule combinations per list: SL1 0; SL3 0; SL2 (slower: 60-min trend, monthly open, weekly VWAP, 15-min relative volume >= 1, 60-min efficiency ratio >= 0.3 with the trade) 2: P7 Asia at least 4 (707 of 2,161 trades, $839 vs $424 per trade, max DD 36,080 vs 75,069, pctl 1.00 / 0.99) and K7 NY AM all 5 (119 trades, below the 150 floor, ignored). SL3 has 70 % unknown items in the overnight sessions (opening-range and RTH VWAP exist only in RTH), so it is not a fair test outside RTH.
Reading: P7 Asia improves under two independent pre-specified lists (USER_SET_V0 all-5, SL2 at least 4), which is a better sign than either alone, but the lists overlap in what they say (trend / VWAP side), the cell is the one with the 7-lot heavy tail, and the older window of USER_SET_V0 (2023) was negative; both are in-sample on full history. Exact-engine sets TL3_CF_U3 (V0 all-5) and TL3_CF_U6 (SL2 at least 4) with 3 random-skip placebos each are running; the engine, not the table, decides.

## 6. L3 (MBO) leads from W-CF2 through the matched-count controls (stack-wide, taken signals, engine $ at base lots; not pre-registered: found by W-CF2's step 3, 8 variants tested here; code l3_leads.py)
| condition (H2 = value vs previous 20 trading days) | side kept | kept (of 19,785) | $/trade kept vs all | max DD kept vs all | matched-count pctl exp / DD | bootstrap 95 % of $/trade | by year kept vs all |
|--|--|--|--|--|--|--|--|
| arrival imbalance (60 s) LOW | yes | 3,861 (about 4/day) | 222 vs 106 | 42,526 vs 92,243 | 1.00 / 0.99 | 144 .. 294 | 2023 92 vs 32; 2024 277 vs 114; 2025 190 vs 99; 2026 266 vs 138 |
| same, the complement (skip these) | no | 15,924 | 78 vs 106 | 75,273 vs 92,243 | 0.00 / 0.99 | 41 .. 114 | all years below the average |
| contra-side resting size (300 s) LOW | yes | 3,372 | 213 vs 106 | 71,714 vs 92,243 | 1.00 / 0.52 | 117 .. 306 | 2023 180 vs 32; 2024 183; 2025 223; 2026 246 |
| contra-side resting size (60 s) HIGH | yes | 3,868 | 12 vs 106 | 127,908 vs 92,243 | 0.00 / 0.02 | -59 .. 84 | negative or flat every year (a veto: its complement 128 vs 106, pctl 1.00 / 0.35) |
| spoof-like ahead (300 s) LOW | yes | 10,444 | 146 vs 106 | 89,230 vs 92,243 | 0.87 / 0.27 | 92 .. 197 | positive but small, fails the drawdown test |

Reading: arrival-imbalance-LOW is the first single condition to pass the table-level expectancy AND drawdown tests (both above the 95th percentile of equal-count random subsets within book/session/month), positive in all four years, about 4 trades per day (above the 3/day floor), and the largest drawdown cut seen (-54 %). Caveats: it needs L3 (MBO) data, which D7 does not have live (a live L3 feed is a new feed: W-CF2 has the quote); the drift-robust form needs the previous 20 days of the same L3 series; 8 variants were tested, so treat the pctl 0.99 with caution; table-level, in-sample on full history, no walk-forward of a chosen item (the item is fixed, so out-of-sample = by-year line above); the earlier one-year spoof-like lead is not confirmed (W-CF2). Exact-engine sets TL3_CF_U7 (skip signals where the condition is NO) with 3 random-skip placebos are queued; the engine decides, because a skip frees the book for a later signal.

## 2. Machinery and its validation (steps 4-5)
Built and tested on a stand-in table: planted +$800/+$1,500 edge recovered by greedy and by the 2-week walk-forward (905 vs 219 $/trade OOS, DD cut 6x, matched-count controls pass); shuffled outcomes rejected; a leak (open-trade results in 'previous trade' columns) produced a fake 3x OOS edge and was removed (W-CF1 informed; v1 table defines L columns over closed trades only).
First run of the searched families on the PARTIAL table (A, E, L categories only, 271 conditions), stack-wide walk-forward (trailing 52 weeks, 2-week refits, first test 2023-10-16): score on positive-alone items 7.3 trades/day $184 vs $117 per trade but max DD 75k vs 92k and DD percentile 0.33; one-per-category 0.70; cluster score 0.09; greedy must-have list 0.57 trades/day $527 vs $117, DD percentile 0.87, items change on most refits (stability 0.34); gradient boosting (upper bound) 9 trades/day $175, DD worse than all trades. None passes the matched-count test on drawdown. The full run on the v1 table (with U) is in progress; the 50 shuffled-outcome search reruns and the per-block importance table follow once the M, F-J and Block 2-5 columns are in.

<!--ENG-->
## 3b. Engine numbers for the USER_SET_V0 leads (exact engine, JN05W2 base, all layers ON, hook cf_hooks as a skip gate on top; engine fee $1.18; base lots; official weekly basis of jv_score; reference JN05W2)

Skip rule applies to the signals in the entry table (taken JN05W2 signals); signals that appear only because a skipped one freed the book pass through UNGATED, so the engine result is the honest effect of "skip these", not of "run the checklist on every signal". Placebos = same number of skips drawn at random within book/session/month (PB1-3).

### L1M

| rule | weeks | engine maxDD | JN05W2 | engine DD cut % | DD cut % W44 removed | tolerant gate (DD cut > -2 %, mean >= -3 %) | worst wk | d worst wk | d mean $/wk | d mean % | d mean @4.84 | placebo DD cut % (3 draws) | placebo d mean | table-level DD cut % / d $/wk % |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| K7 Asia >=4 | 4 | 25918 | 36371 | 28.7 | - | yes | -25918 | 10453 | 578 | 95.3 | 566 | 16.7, 27.4, 22.8 | -3301, -2001, -2959 | - |
| K7 Asia >=3 | 4 | 26182 | 36371 | 28.0 | - | yes | -26182 | 10188 | 583 | 96.1 | 569 | 19.3, 31.5, 20.3 | -1258, -1064, -1069 | - |
| P7 Asia all5 | 4 | 34516 | 36371 | 5.1 | - | no | -34516 | 1855 | -4152 | -684.8 | -4159 | -6.2, -9.2, 22.3 | -2499, -4251, -553 | - |
| stack >=4 gate | 4 | 35584 | 36371 | 2.2 | - | no | -35584 | 787 | -2044 | -337.2 | -2045 | -7.6, -7.9, 57.8 | -471, -7133, 176 | - |
| K7 Asia >=4 + P7 Asia all5 | 4 | 22160 | 36371 | 39.1 | - | no | -22160 | 14211 | -1768 | -291.7 | -1780 | 50.3, 56.3, 16.6 | -2101, -2676, -5953 | - |
| P7 Asia SL2 >=4 | 4 | 32520 | 36371 | 10.6 | - | no | -32520 | 3851 | -1824 | -300.9 | -1831 | 66.5, 34.8, 21.0 | 4565, -1818, -2455 | - |
| L3 arrival imbalance low (stack gate) | 4 | 48077 | 36371 | -32.2 | - | no | -48077 | -11707 | -7240 | -1194.1 | -7146 | 12.8, -3.8, -26.4 | -7163, -6674, -8125 | - |

### L3M

| rule | weeks | engine maxDD | JN05W2 | engine DD cut % | DD cut % W44 removed | tolerant gate (DD cut > -2 %, mean >= -3 %) | worst wk | d worst wk | d mean $/wk | d mean % | d mean @4.84 | placebo DD cut % (3 draws) | placebo d mean | table-level DD cut % / d $/wk % |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| K7 Asia >=4 | 13 | 29877 | 36371 | 17.9 | 2.1 | yes | -25918 | 10453 | -279 | -1.7 | -273 | 11.5, 27.4, 22.8 | -1955, -667, -986 | 29.2 / 16 |
| K7 Asia >=3 | 13 | 26962 | 36371 | 25.9 | 11.7 | yes | -26182 | 10188 | 426 | 2.7 | 426 | 19.3, 14.5, 20.3 | -17, -1093, -374 | 21.2 / 17 |
| P7 Asia all5 | 13 | 64194 | 36371 | -76.5 | -110.2 | no | -42821 | -6450 | -7040 | -44.0 | -6998 | -62.1, -61.7, -63.0 | -6953, -7816, -5642 | 67.8 / -63 |
| stack >=4 gate | 13 | 88768 | 36371 | -144.1 | -190.7 | no | -55749 | -19379 | -6508 | -40.6 | -6437 | -53.9, -106.8, -2.8 | -10024, -13344, -1780 | -32.4 / -10 |
| K7 Asia >=4 + P7 Asia all5 | 13 | 63479 | 36371 | -74.5 | -107.9 | no | -40963 | -4593 | -6701 | -41.8 | -6652 | -57.3, -12.6, -71.9 | -6851, -6381, -9972 | - |
| P7 Asia SL2 >=4 | 13 | 68124 | 36371 | -87.3 | -123.1 | no | -44624 | -8254 | -6273 | -39.2 | -6240 | -60.5, -38.7, -77.1 | -2239, -3387, -9401 | - |
| L3 arrival imbalance low (stack gate) | 13 | 59805 | 36371 | -64.4 | -95.9 | no | -48077 | -11707 | -14345 | -89.6 | -14185 | -58.3, -89.1, -93.3 | -15198, -13801, -13201 | - |

### L6M

| rule | weeks | engine maxDD | JN05W2 | engine DD cut % | DD cut % W44 removed | tolerant gate (DD cut > -2 %, mean >= -3 %) | worst wk | d worst wk | d mean $/wk | d mean % | d mean @4.84 | placebo DD cut % (3 draws) | placebo d mean | table-level DD cut % / d $/wk % |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| K7 Asia >=4 | 26 | 29877 | 36371 | 17.9 | 2.1 | yes | -25918 | 10453 | 774 | 3.1 | 783 | 11.5, 27.4, 22.8 | -3349, 349, -2084 | 53.7 / -8 |
| K7 Asia >=3 | 26 | 26962 | 36371 | 25.9 | 11.7 | yes | -26640 | 9731 | -285 | -1.1 | -272 | 19.3, 14.5, 20.3 | -890, 36, 378 | 39.3 / -4 |
| P7 Asia all5 | 26 | 64194 | 36371 | -76.5 | -110.2 | no | -42821 | -6450 | -6154 | -24.5 | -6095 | -62.1, -61.7, -63.0 | -7209, -8162, -6821 | 67.8 / -64 |
| stack >=4 gate | 26 | 88768 | 36371 | -144.1 | -190.7 | no | -55749 | -19379 | -7006 | -27.9 | -6895 | -53.9, -106.8, -13.4 | -6373, -11562, -8601 | -32.4 / -18 |
| K7 Asia >=4 + P7 Asia all5 | 26 | 63479 | 36371 | -74.5 | -107.9 | no | -40963 | -4593 | -5601 | -22.3 | -5528 | -57.3, -17.5, -71.9 | -9020, -6166, -9638 | - |
| P7 Asia SL2 >=4 | 26 | 68124 | 36371 | -87.3 | -123.1 | no | -44624 | -8254 | -5806 | -23.1 | -5764 | - | - | - |
| L3 arrival imbalance low (stack gate) | 26 | 59805 | 36371 | -64.4 | -95.9 | no | -48077 | -11707 | -15162 | -60.3 | -14931 | - | - | - |

### HOLD

| rule | weeks | engine maxDD | JN05W2 | engine DD cut % | DD cut % W44 removed | tolerant gate (DD cut > -2 %, mean >= -3 %) | worst wk | d worst wk | d mean $/wk | d mean % | d mean @4.84 | placebo DD cut % (3 draws) | placebo d mean | table-level DD cut % / d $/wk % |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| K7 Asia >=4 | 52 | 59657 | 63185 | 5.6 | 5.6 | yes | -52768 | 2378 | 208 | 1.2 | 209 | 7.1, 9.8, -8.5 | -2286, -107, -1564 | 46.9 / -16 |
| K7 Asia >=3 | 52 | 60776 | 63185 | 3.8 | 3.8 | yes | -54669 | 476 | -190 | -1.1 | -187 | -14.5, -3.3, -2.0 | -452, -366, -26 | 20.7 / -16 |
| P7 Asia all5 | 52 | 64194 | 63185 | -1.6 | -1.6 | no | -52050 | 3095 | -3880 | -22.2 | -3845 | -6.2, -39.0, -42.8 | -4626, -5770, -3853 | 82.1 / -57 |
| stack >=4 gate | 52 | 88768 | 63185 | -40.5 | -40.5 | no | -61944 | -6799 | -3510 | -20.1 | -3419 | -7.4, -19.1, 18.4 | -3541, -6432, -4578 | 24.9 / -22 |
| K7 Asia >=4 + P7 Asia all5 | 52 | 63479 | 63185 | -0.5 | -0.5 | no | -51949 | 3196 | -4625 | -26.4 | -4578 | -43.0, -19.7, -38.3 | -5415, -4158, -5395 | - |
| P7 Asia SL2 >=4 | 52 | 77232 | 63185 | -22.2 | -22.2 | no | -46871 | 8274 | -3798 | -21.7 | -3767 | - | - | - |
| L3 arrival imbalance low (stack gate) | 52 | 108597 | 63185 | -71.9 | -71.9 | no | -48077 | 7068 | -9256 | -52.9 | -9057 | - | - | - |

### PRE

| rule | weeks | engine maxDD | JN05W2 | engine DD cut % | DD cut % W44 removed | tolerant gate (DD cut > -2 %, mean >= -3 %) | worst wk | d worst wk | d mean $/wk | d mean % | d mean @4.84 | placebo DD cut % (3 draws) | placebo d mean | table-level DD cut % / d $/wk % |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| K7 Asia >=4 | 75 | 71043 | 76186 | 6.8 | - | yes | -52547 | 0 | 59 | 0.6 | 63 | - | - | 38.1 / -5 |
| K7 Asia >=3 | 75 | 85605 | 76186 | -12.4 | - | no | -52547 | 0 | 131 | 1.3 | 136 | - | - | 34.2 / -1 |
| P7 Asia all5 | 75 | 102865 | 76186 | -35.0 | - | no | -56155 | -3608 | -2289 | -22.5 | -2271 | - | - | 45.3 / -52 |
| stack >=4 gate | 75 | 89892 | 76186 | -18.0 | - | no | -40933 | 11614 | -691 | -6.8 | -625 | - | - | -21.8 / -25 |
| K7 Asia >=4 + P7 Asia all5 | 75 | 97401 | 76186 | -27.8 | - | no | -56155 | -3608 | -1885 | -18.5 | -1866 | - | - | - |

### X'

| rule | weeks | engine maxDD | JN05W2 | engine DD cut % | DD cut % W44 removed | tolerant gate (DD cut > -2 %, mean >= -3 %) | worst wk | d worst wk | d mean $/wk | d mean % | d mean @4.84 | placebo DD cut % (3 draws) | placebo d mean | table-level DD cut % / d $/wk % |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| K7 Asia >=4 | 44 | 51268 | 55326 | 7.3 | - | no | -26516 | -4853 | -198 | -5.5 | -196 | - | - | 46.4 / -83 |
| K7 Asia >=3 | 44 | 55895 | 55326 | -1.0 | - | yes | -26504 | -4840 | -79 | -2.2 | -78 | - | - | 42.4 / 86 |
| P7 Asia all5 | 44 | 71918 | 55326 | -30.0 | - | no | -30158 | -8494 | 813 | 22.7 | 812 | - | - | 61.5 / -104 |
| stack >=4 gate | 44 | 56512 | 55326 | -2.1 | - | no | -33434 | -11770 | -1394 | -38.9 | -1358 | - | - | 23.4 / -28 |
| K7 Asia >=4 + P7 Asia all5 | 44 | 67328 | 55326 | -21.7 | - | no | -30989 | -9325 | 763 | 21.3 | 763 | - | - | - |

### GAP

| rule | weeks | engine maxDD | JN05W2 | engine DD cut % | DD cut % W44 removed | tolerant gate (DD cut > -2 %, mean >= -3 %) | worst wk | d worst wk | d mean $/wk | d mean % | d mean @4.84 | placebo DD cut % (3 draws) | placebo d mean | table-level DD cut % / d $/wk % |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| K7 Asia >=4 | 18 | 67001 | 68947 | 2.8 | - | yes | -67001 | 1946 | 439 | 3.5 | 435 | - | - | 53.0 / -36 |
| K7 Asia >=3 | 18 | 69339 | 68947 | -0.6 | - | yes | -69339 | -392 | -339 | -2.7 | -343 | - | - | 23.9 / -32 |
| P7 Asia all5 | 18 | 89715 | 68947 | -30.1 | - | no | -71195 | -2249 | -1875 | -15.1 | -1855 | - | - | 29.0 / -96 |
| stack >=4 gate | 18 | 87831 | 68947 | -27.4 | - | no | -67714 | 1233 | 194 | 1.6 | 253 | - | - | 34.8 / -31 |
| K7 Asia >=4 + P7 Asia all5 | 18 | 86902 | 68947 | -26.0 | - | no | -69250 | -303 | -1774 | -14.3 | -1757 | - | - | - |

<!--/ENG-->

## 3. Open items (what runs next)
CF hook identity PROVEN: TL3_CF_ID 202610 = 598 trades / 25,943.82, row-identical to JN05W2. Skip side-effect check TL3_CF_SK1 (3 signals skipped, 1 halved, all in 202610): trade count stays 598 but total moves to 28,574.50 because a skipped signal frees the book and a later signal of the same book is taken instead (5 trades dropped, 5 new, 3 resized): a table-level skip rule overstates or understates what the live stack does, so every finalist needs its exact-engine run. Skipped-signal rows, $/R double controls, frontier per book/session, size by score, redundancy clusters across 3,144 + 3,652 indicator columns, USER_SET controls on R: pending.

For the build list (W-JV): USER_SET_V0 needs only D7's own 5-min and 15-min bars and the session / prior-day levels and prior-day profile D7 already keeps (CCI 14, EMA 8/21, Bollinger-Keltner squeeze, session opens/highs/lows, prior-day POC and value area); no new feed. The 'no high-volume node between entry and target' part of item 3 needs the prior-day profile only. 
