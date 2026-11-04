# DS3_ATTRIBUTION: live edge attribution by ablation on the validated reference engine (DIS-AB)

Author ZL-2, 2026-11-04. Scope note l2vast/ds3/prereg/DISAB_scope.md sha256 8083030e38a2b6ee58d97077f2b89fa4386b4af9a88b2b3c67b81098a7415c94 (DECISIONS.md, before any outcome); correction (SIG is Shadow and OFF in the ts2 reference, so 8 components, 256 subsets) logged in DECISIONS.md before any outcome. Measurement; no hypothesis test; no PASS claim; nothing live. Code l2vast/ds3/code/dis_x/ab_*.py; tables l2vast/ds3/out/dis_ab/.

## Plain sentence
At live lots the stack's 2026 profit ($35.3k/week, maxDD $63k) is mostly the TH-L2 loss cut (+$19.8k/week of the +$27k/week gain over the plain-signal stack at the same lots, almost all of it on the PE book: +$359k of +$663k), then the PE 45-second confirmation (+$4.5k), the 70/30 split (+$2.8k) and the Asia stack cut (+$2.8k), while zones (-$2.1k) and the ER ladder (-$0.6k) subtract; the plain signals at live lots made +$8.3k/week in 2026 on this engine (not negative), but with a $379k maxDD; the same component structure is NOT present in 2024 (TH +4.6k, zones +2.5k, PE confirm -1.7k), 2025 (locks +4.2k, PE confirm +3.7k, zones +2.6k, TH -3.8k) or 2023 (all small and positive, plain -$8.1k to about zero), so the stack's profit comes from different parts in different years and the TH-L2 cut in 2026 is the single largest piece; the live exits and loss controls, not the entries, carry both the profit level and the drawdown.

## Setup and tie-out
Engine d7_v13t run_v13t_ts2 hooks (Q1-A ladder, 1-second fills, live cost frame: market exit 0.80, stop cost 2.45), core six books; all 2^8 = 256 subsets of 8 switches run once (about 8 minutes on 3 workers). Tie-out: the full stack reproduces $2,520,149.07 over 935 label days (the ts2 reference); with signal-state rules ON it would be $2,269,832 (they are Shadow in D7 and OFF in the reference, so not a component). Periods: years 2023 (from 2023-04-03, 18 weeks), 2024 (53), 2025 (49), 2026 (30, to 2026-10-31); windows L6M (2026-05-01..10-31), HOLD (2025-11-01..2026-10-31), PRE (2024-02..2025-06), X' (2023-04..2024-01); weekly-cumulative maxDD; Calmar = mean weekly / maxDD; corrected carrying weeks dropped (windows by book_harness.CAR; years drop all four carrying-episode week ranges 2025 W06-09, 2026 W06-08 and W29-39, 2023 W21-41, so yearly weeks are fewer than calendar weeks).
Switches and hooks (all existing):
| key | component | hook |
|---|---|---|
| TH | TH-L2 loss cut (adverse >= 30 pts and 5-s pulled-liquidity >= 30x) | ov th_loss (profit / take lines are empty in V13T and stay empty) |
| LK | per-book locks: day give-back arm 2R keep 50%, week floor 12R, daily win/loss gates 5R/2R | OC.CFG['spec'] floor=arm=keep=0, pb_win=pb_loss=None (lock_noise.py hook) |
| ZN | zone layer: 7 zone lines HALF (D20) + OTE-62 B73 (D30) | ov zone False and the zone HALF factor removed from lots_mult (lots_ts2.live_lots stages); OTE-62 sits inside the zone switch in the engine, so it cannot be ablated separately |
| SP | 70/30 dip-3 split | ov split |
| PE | PE 45-second confirmation (NY sessions, PE book only) | ov pe |
| SL | session lot table + A06 slot halving + B02 quiet-overnight halving | lots_mult built from lots_ts2 flags (OFF = 1 lot on every live-session row) |
| ER | Q1-A ER(20) ladder (>=0.30 x1.0, else x0.5) | lots_mult and gov_mer (ladder off) |
| CUT | Asia-only stack cut 50% | ov cut |
No hook (not ablated, not hacked): the U7 blackout and K7/H7/M7 NY-AM lots are inside the V13 base; the native-stop convention is a model input; X1-X5 are outside the core; the lock stage can only be switched as a whole (arm, floor and daily gates together); OTE-62 cannot be separated from the zones; "(2) live bracket/exit definitions" has no switch because every library row is already 60/60 (sd = td = 60 for all six books), so the live bracket IS the plain bracket; the only difference is the fill-cost frame, held fixed here. Cost frame effect (nominal-cost run, xcost 0 and stop cost 0): all-off mean $/wk 2023 -1.0k, 2024 7.8k, 2025 7.7k, 2026 7.6k (live costs: -2.6k, 5.4k, 4.4k, 2.3k); full stack 1.1k, 15.7k, 19.8k, 38.9k (live costs: -0.2k, 13.8k, 17.0k, 35.3k): live fill costs take $2-5k/week.
Dead_lookup: DS3_SIZER_X_LOCK_V13T.md (60 lock cells; its windows are the old L6M/HOLD/F9 and the lock surface only, so its numbers are not identical to these windows; the LIVE lock cell there agrees in direction with LK here, small), DS3_LIVE_LOCK_NOISE_V13T.md, d7base README LOO tables (D7 v1.0d base with TH-L2 profit path rule, different definitions). No number is reused; everything below is a new run.

## 1. Nine-step path (one ordering): mean $/wk (maxDD $k; Calmar)
Step 1 = signals only (all switches off: 60/60, live-session rows, 1 lot, live cost frame, no locks); step 2 (exit definitions) is a no-op as explained; then +TH, +LK, +ZN, +SP+PE, +SL, +ER, +CUT = full stack.
| step | 2023 | 2024 | 2025 | 2026 | L6M | HOLD | PRE | X' | ALL |
|---|---|---|---|---|---|---|---|---|---|
| signals only (all off) | -2597 (73k; -0.04) | 5373 (43k; 0.12) | 4371 (84k; 0.05) | 2340 (124k; 0.02) | 3787 (95k; 0.04) | 1414 (159k; 0.01) | 5861 (50k; 0.12) | -2734 (73k; -0.04) | 3530 (124k; 0.03) |
| +TH | 697 (24k; 0.03) | 6740 (18k; 0.38) | 3803 (59k; 0.06) | 10313 (59k; 0.17) | 11890 (21k; 0.56) | 7201 (100k; 0.07) | 6197 (18k; 0.35) | 778 (24k; 0.03) | 5848 (59k; 0.10) |
| +LK | 721 (24k; 0.03) | 6735 (19k; 0.36) | 3400 (61k; 0.06) | 10417 (53k; 0.20) | 12396 (23k; 0.55) | 7600 (78k; 0.10) | 6014 (21k; 0.28) | 851 (24k; 0.04) | 5737 (61k; 0.09) |
| +ZN | 583 (22k; 0.03) | 6233 (15k; 0.41) | 3958 (51k; 0.08) | 8799 (39k; 0.23) | 10919 (23k; 0.47) | 6339 (85k; 0.07) | 5572 (19k; 0.30) | 1281 (22k; 0.06) | 5397 (51k; 0.10) |
| +SP+PE | 825 (20k; 0.04) | 6001 (20k; 0.30) | 4700 (46k; 0.10) | 10303 (23k; 0.45) | 11628 (21k; 0.55) | 7914 (55k; 0.14) | 5765 (20k; 0.29) | 1394 (20k; 0.07) | 5894 (46k; 0.13) |
| +SL | 435 (74k; 0.01) | 15126 (110k; 0.14) | 19154 (109k; 0.18) | 31119 (65k; 0.48) | 39926 (65k; 0.61) | 25490 (193k; 0.13) | 16261 (110k; 0.15) | 3898 (74k; 0.05) | 18119 (110k; 0.17) |
| +ER | -593 (52k; -0.01) | 13956 (75k; 0.19) | 17327 (72k; 0.24) | 34972 (58k; 0.60) | 43702 (58k; 0.75) | 27565 (123k; 0.22) | 15318 (75k; 0.20) | 2719 (52k; 0.05) | 17751 (75k; 0.24) |
| +CUT | -219 (49k; -0.00) | 13850 (75k; 0.18) | 16989 (71k; 0.24) | 35316 (63k; 0.56) | 43516 (63k; 0.70) | 27851 (122k; 0.23) | 15187 (75k; 0.20) | 3012 (49k; 0.06) | 17716 (75k; 0.24) |
Reading: the step "+SL" (lot sizes 2-7 per book) multiplies both P&L and drawdown; the ordering therefore hides the exit/entry effects, which is why section 3 holds the live lots fixed.

## 2. Leave-one-out from the full stack (full minus ablated): change in mean $/wk (positive = component adds profit)
| comp | 2023 | 2024 | 2025 | 2026 | L6M | HOLD | PRE | X' | ALL |
|---|---|---|---|---|---|---|---|---|---|
| TH | -638 | 2565 | -4775 | 13659 | 20017 | 7928 | 363 | 204 | 2029 |
| LK | 256 | -200 | 1061 | 625 | 1579 | 596 | 1015 | -182 | 437 |
| ZN | -3020 | 853 | 525 | -4229 | -5228 | -3305 | 688 | -331 | -745 |
| SP | 1953 | -975 | 216 | 3560 | 3737 | 2713 | -495 | 1257 | 681 |
| PE | 97 | -1944 | 2471 | 715 | -1745 | 1997 | -563 | -519 | 279 |
| SL | -1182 | 7866 | 12363 | 25046 | 32008 | 19955 | 9446 | 1509 | 11843 |
| ER | -1275 | -1089 | -1730 | 4266 | 4056 | 2421 | -890 | -1384 | -253 |
| CUT | 373 | -107 | -337 | 343 | -186 | 286 | -130 | 293 | -35 |

Change in maxDD $k (positive = the component makes the drawdown DEEPER; negative = it makes it shallower):
| comp | 2023 | 2024 | 2025 | 2026 | L6M | HOLD | PRE | X' | ALL |
|---|---|---|---|---|---|---|---|---|---|
| TH | -32 | -100 | -22 | -29 | -28 | 31 | -100 | -32 | -100 |
| LK | 0 | -15 | 0 | 7 | 7 | -27 | -15 | 0 | -15 |
| ZN | -21 | 4 | -5 | -9 | -9 | 12 | 4 | -21 | -1 |
| SP | -1 | -20 | -13 | -12 | -12 | -4 | -20 | -1 | -20 |
| PE | -22 | 2 | -5 | 1 | 1 | 40 | 2 | -22 | -2 |
| SL | 31 | 55 | 26 | 40 | 42 | 68 | 55 | 31 | 29 |
| ER | -20 | -37 | -36 | -7 | -7 | -70 | -37 | -20 | -37 |
| CUT | -2 | -0 | -1 | 4 | 4 | -1 | -0 | -2 | -0 |

## 3. Shapley mean marginal contribution (exact, from the 256 subsets, 8 components): mean $/wk
| comp | 2023 | 2024 | 2025 | 2026 | L6M | HOLD | PRE | X' | ALL |
|---|---|---|---|---|---|---|---|---|---|
| TH | 1784 | 2422 | -2930 | 11640 | 13993 | 7498 | 336 | 2645 | 2474 |
| LK | 277 | -366 | 1365 | 332 | 733 | 1166 | 808 | 90 | 422 |
| ZN | -350 | 990 | 1243 | -1823 | -3053 | -1421 | 493 | 1780 | 354 |
| SP | 928 | -542 | -106 | 1738 | 1689 | 1022 | -371 | 696 | 236 |
| PE | 695 | -895 | 1936 | 1917 | 753 | 2650 | -75 | 444 | 794 |
| SL | -1440 | 7666 | 11872 | 17613 | 23936 | 14396 | 8871 | -118 | 10071 |
| ER | -200 | -776 | -735 | 145 | -49 | -22 | -774 | -301 | -516 |
| CUT | 683 | -23 | -27 | 1414 | 1726 | 1149 | 40 | 511 | 352 |

Shapley contribution to maxDD $k (negative = the component reduces the drawdown on average over orderings; includes the SL lot-size scale):
| comp | 2023 | 2024 | 2025 | 2026 | L6M | HOLD | PRE | X' | ALL |
|---|---|---|---|---|---|---|---|---|---|
| TH | -44 | -58 | -38 | -62 | -55 | -38 | -69 | -44 | -76 |
| LK | -0 | -5 | -16 | -21 | -13 | -58 | -16 | -1 | -24 |
| ZN | -17 | -4 | -19 | -32 | -20 | -17 | -2 | -19 | -20 |
| SP | -3 | -6 | -7 | -11 | 1 | -16 | -5 | -3 | -12 |
| PE | -20 | 20 | -8 | -14 | -15 | -13 | 4 | -19 | -6 |
| SL | 83 | 97 | 95 | 88 | 82 | 146 | 129 | 84 | 111 |
| ER | -15 | -11 | -18 | -7 | -8 | -34 | -15 | -15 | -19 |
| CUT | -7 | 0 | -3 | -3 | -5 | -6 | -2 | -8 | -3 |

### 3b. Scale-neutral: live lots (SL) fixed ON, 7 components
Baseline = plain signals at live lots, all other pieces off. Plain at live lots vs full ($/wk; maxDD $k; Calmar): 2023 -8.1k, 245k, -0.03 vs -0.2k, 49k, 0.00; 2024 12.1k, 155k, 0.08 vs 13.8k, 75k, 0.18; 2025 11.1k, 295k, 0.04 vs 17.0k, 71k, 0.24; 2026 8.3k, 379k, 0.02 vs 35.3k, 63k, 0.56; L6M 16.5k, 319k vs 43.5k, 63k; HOLD 4.5k, 561k vs 27.9k, 122k; PRE 12.3k, 295k vs 15.2k, 75k; X' -8.7k, 245k vs 3.0k, 49k.
Shapley mean $/wk:
| comp | 2023 | 2024 | 2025 | 2026 | L6M | HOLD | PRE | X' | ALL |
|---|---|---|---|---|---|---|---|---|---|
| TH | 2116 | 4578 | -3801 | 19794 | 23589 | 13027 | 1324 | 3956 | 4650 |
| LK | 466 | -1390 | 4175 | -274 | -514 | 2350 | 2135 | -169 | 886 |
| ZN | 548 | 2537 | 2637 | -2055 | -4224 | -1457 | 1456 | 4204 | 1432 |
| SP | 1468 | -452 | -327 | 2820 | 2751 | 1564 | -464 | 1282 | 480 |
| PE | 1624 | -1724 | 3707 | 4450 | 2670 | 5650 | -197 | 1250 | 1709 |
| ER | 398 | -1790 | -715 | -550 | -1013 | -60 | -1594 | 195 | -941 |
| CUT | 1246 | 26 | 199 | 2823 | 3714 | 2301 | 225 | 990 | 799 |

Shapley maxDD $k:
| comp | 2023 | 2024 | 2025 | 2026 | L6M | HOLD | PRE | X' | ALL |
|---|---|---|---|---|---|---|---|---|---|
| TH | -67 | -89 | -76 | -103 | -84 | -93 | -120 | -67 | -127 |
| LK | 6 | -1 | -45 | -56 | -44 | -139 | -49 | 5 | -48 |
| ZN | -35 | -8 | -26 | -65 | -46 | -44 | -10 | -37 | -37 |
| SP | -7 | -14 | -2 | -17 | -4 | -23 | -3 | -7 | -18 |
| PE | -39 | 52 | -28 | -42 | -38 | -44 | 4 | -38 | -20 |
| ER | -40 | -16 | -40 | -25 | -31 | -80 | -36 | -38 | -44 |
| CUT | -13 | -2 | -6 | -9 | -9 | -16 | -7 | -14 | -9 |

Interaction of the TH cut with the lot size (TH effect on mean $/wk at 1 lot vs at live lots): 2023 +3.3k vs +6.5k; 2024 +1.4k vs +7.4k; 2025 -0.6k vs +0.6k; 2026 +8.0k vs +29.9k; HOLD +5.8k vs +22.2k; the cut is worth most where the lots are largest (PE 7 lots).

## 4. By book (live lots fixed, Shapley over 7 components), $k per year
| year | book | plain @ live lots ($k) | full ($k) | TH | LK | ZN | SP | PE-conf | ER | CUT |
|---|---|---|---|---|---|---|---|---|---|---|
| 2023 | KB | -139 | -9 | 56 | 25 | 37 | -7 | 0 | 14 | 5 |
| 2023 | PE | 108 | 35 | -93 | -74 | 29 | 17 | 51 | -32 | 30 |
| 2023 | SM | -19 | 61 | 34 | -16 | 50 | -7 | 0 | 17 | 2 |
| 2023 | HM | -30 | -21 | 15 | -4 | -26 | 20 | 0 | 1 | 1 |
| 2023 | MV | -30 | 5 | 28 | -3 | 4 | 2 | 0 | 6 | 0 |
| 2023 | PB | -5 | 2 | -1 | 1 | 6 | 0 | 0 | 0 | 1 |
| 2024 | KB | 196 | 135 | 2 | -15 | 1 | -23 | 0 | -23 | -2 |
| 2024 | PE | 141 | 366 | 192 | -66 | 179 | 39 | -91 | -25 | -2 |
| 2024 | SM | 104 | 71 | 9 | 4 | -5 | -21 | 0 | -18 | -1 |
| 2024 | HM | 78 | 82 | 64 | -2 | -14 | -18 | 0 | -33 | 7 |
| 2024 | MV | 77 | 36 | -25 | 4 | -22 | -2 | 0 | 4 | 0 |
| 2024 | PB | 44 | 43 | 1 | 2 | -4 | 0 | 0 | 0 | -0 |
| 2025 | KB | 72 | 35 | -29 | -13 | 3 | 8 | 0 | -6 | -0 |
| 2025 | PE | 43 | 519 | -44 | 269 | 99 | -26 | 169 | -3 | 10 |
| 2025 | SM | 154 | 74 | -35 | -9 | -37 | 22 | 0 | -8 | -12 |
| 2025 | HM | 169 | 98 | -74 | -2 | 62 | -22 | 0 | -37 | 1 |
| 2025 | MV | 23 | -34 | -44 | -11 | 11 | 3 | 0 | -16 | -1 |
| 2025 | PB | 55 | 53 | 2 | -0 | -2 | 0 | 0 | 0 | -2 |
| 2026 | KB | -96 | 74 | 82 | 66 | -4 | -13 | 0 | 28 | 12 |
| 2026 | PE | -119 | 544 | 359 | 11 | 13 | 74 | 183 | -28 | 52 |
| 2026 | SM | 95 | 127 | 67 | -7 | -52 | 8 | 0 | 13 | 4 |
| 2026 | HM | 219 | 239 | 99 | -7 | -35 | -17 | 0 | -45 | 25 |
| 2026 | MV | -44 | -21 | -7 | -7 | 5 | 11 | 0 | 20 | 1 |
| 2026 | PB | 43 | 7 | -2 | -11 | -26 | 0 | 0 | -0 | 3 |

Reading: in 2026 the PE book goes from -119k (plain, 7 lots) to +544k; the TH cut is +359k of that, the PE 45-s confirmation +183k, the split +74k, the Asia cut +52k. KB goes from -96k to +74k (TH +82k, locks +66k); HM stays near +219k to +239k (TH +99k offset by ER -45k and zones -35k); SM +95k to +127k; MV and PB near zero or negative. In 2025 the PE book's +519k is locks (+269k), PE confirmation (+169k) and zones (+99k) with TH -44k; in 2024 the PE book's +366k is TH (+192k) and zones (+179k) with the PE confirmation -91k and locks -66k; in 2023 PE earns +35k (plain +108k) with TH -93k and locks -74k.

## 5. Answers
1. 2026 profit if raw entries are negative: on this engine plain 60/60 entries at 1 lot earned +$2.3k/week in 2026 (KB -103k, PE -8k, MV -18k, SM +25k, PB +43k, HM +71k over the year), at live lots +$8.3k/week; the negative 2026 figure in DS3_SIGNALS_2013/DS3_ERA_2023 is a different object (1-minute fills, percent bracket of 84 points in 2026, all signals not just those the live book took), so the two are not in conflict only if read as different objects. The stack's $35.3k/week comes mainly from the live loss cut and the PE book at 7 lots (section 3b and 4).
2. Same component structure in 2024-25 and 2023: no. TH-L2 is positive in 2023, 2024 and 2026 but negative in 2025 (-3.8k/week at live lots); locks are material only in 2025 (+4.2k; +0.5k in 2023, -1.4k in 2024, -0.3k in 2026); zones are positive in 2023-25 (+0.5k, +2.5k, +2.6k) and negative in 2026 (-2.1k); the ER ladder is negative in 2024-26 at live lots (-1.8k, -0.7k, -0.55k) and positive only in 2023 (+0.4k); the PE confirmation is negative in 2024 (-1.7k) and positive in the other years. What is common: every year's full-stack maxDD is far below the plain-at-live-lots maxDD (49-75k vs 155-379k), so the loss-limiting stack is present in each year; the profit sources rotate.
3. HOLD/PRE drawdown: plain signals at live lots would have maxDD $561k in HOLD and $295k in PRE; the full stack has $122k and $75k. Shapley (live lots, section 3b): HOLD maxDD is reduced by locks (-139k), ER ladder (-80k), TH (-93k), zones (-44k), PE confirm (-44k), split (-23k), Asia cut (-16k); PRE by TH (-120k), locks (-49k), ER (-36k). Leave-one-out from the full stack (section 2): removing the ER ladder would deepen the HOLD drawdown by $70k and removing locks by $27k (they carry the HOLD drawdown protection), while removing TH or the PE confirmation would make the HOLD drawdown SHALLOWER by $31k and $40k (in the HOLD episode those two add drawdown even though they add profit); in PRE removing TH would deepen the drawdown by $100k, removing the split by $20k, ER $37k, locks $15k.

## Caveats
* Interactions are large (TH x lots, locks x ER governor); a single decomposition cannot be unique: the leave-one-out, the path and Shapley give different numbers by construction; Shapley is the average over all 8! orderings (exact, not 200 random ones).
* The TH-L2 cut parameters (30 pts / 5 s / 30x) come from the L2 research on 2023-26 data; its 2026 gain is therefore not an independent out-of-sample estimate for the part of 2026 inside the research window (before the 2026-02-06 research cap); the post-cap part (MID, L6M) is closer to out-of-sample but the parameter grid was chosen with the same data nearby.
* One engine, one base (V13T ts2), live cost frame; windows with carrying weeks dropped have fewer weeks (2023: 18, 2026: 30), so means are noisy: the weekly mean sd is about $30k.
* No hack of the engine; the lock stage is switched as a whole; X1-X5 outside the core.
