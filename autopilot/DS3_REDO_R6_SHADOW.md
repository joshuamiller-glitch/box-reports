# DS3_REDO_R6_SHADOW - T-STACK-REDO R6: shadow lines (signal-state rules, X1-X5, flip-level) re-scored on the state base S1b-COMB (REDO-R6, 2026-11-10 00:36Z)
**Label: PRE-PROOF (entries not live-matched, S1b base), post-hoc, Shadow only, NOTHING promoted, no PASS claims. FIRST-ORDER SCREEN for sections A and C (sz_core, ROLL-EXCL, all weeks for maxDD, carrying week dropped from means); EXACT runs of the TOP-5 per family are queued with SZ-CORE (prefix R6_, tier 2, file exact_queue_6_r6.txt, 39 months x 10 sets); status [FIRST-ORDER SCREEN ONLY] until they land. Section B uses its own trade simulation (tape fills), not the engine.**
Prereg: DS3_REDO_R6_PREREG.md (sha 0ad953ad...) and DS3_REDO_R6_PREREG_BC.md (sha f5e35563...; X grid was run once ~18:25Z before its sha line, disclosed there; the sha line is stamped 18:28Z). Code code/th_sz_r6/. Standing rule: every layer stays ON; "off" rows are references only.
## 0. Summary block
| setting | live value | best on the state base | holds OOS? | change recommended | panel field |
|--|--|--|--|--|--|
| Signal-state rule 1 (H7 Slope SkipBot3) | Shadow | H7 Slope HalveBot r=100 q=0.25 (eq-mean cut L6M/PRE/X' 1/1/2, d mean 162 $/wk, placebo p 0.15/0.13) | no: placebo p .15/.13, family p 1.0, H7 WF -2.1% | no | Ss1Mode/Ss1Template |
| Signal-state rule 2 (K7 St1Dist SkipTop3) | Shadow | K7 Slope SkipTop r=200 q=0.25 (eq-mean cut L6M/PRE/X' 7/6/-2, d mean 447 $/wk, placebo p 0.13/0.28) | no (placebo p > .10, family p 1.0) | no | Ss2* |
| Signal-state rule 3 (P7 St1Dist SizeHi) | Shadow (UP cell, never promoted) | P7 Slope SkipTop r=exp q=0.50 (eq-mean cut L6M/PRE/X' 12/33/43, d mean -4098 $/wk, placebo p 0.14/0.17) | partly: P7 WF OOS cut 35% but at -3.0k/wk mean (not equal mean; equal-lots 35%); placebo p .14/.17, family p 1.0 -> no | no | Ss3* |
| Signal-state rule 4 (H7 St1Dist SkipBot3) | Shadow | see H7 table | no | no | Ss4* |
| X1-X5 (2 lots, Shadow, no cut, caps 12000/-4800) | Shadow | best cell X|X4|lots4|K7cell|cap1 (stack cut L6M 2.7, PRE 0.8) | no: the full X set deepens the stack maxDD L6M by 48% | no; keep Shadow | X1Mode..X5Mode |
| Flip-level (break 10, valid 4 h, reach 40, Shadow = skip) | Shadow | brk 15 valid 8h reach 60 skip (eq-mean cut L6M/PRE/X' 12/12/45, d mean 3152; placebo p 0.57/0.80); live cell eq-mean cut 15/14/23, d mean 3461, placebo p 0.23/0.67 | no: mean-type, placebo p > .10 everywhere, family p 1.0 | no (stay Shadow) | FlipMode, FlipBreakPts, FlipValidHours, FlipReachPts |
## 1. What the DS7 quantities are here (proxy statement)
St1Dist and Slope are NOT proxies: they are recomputed exactly as DS7.cs SsFeature (1-min bars, last closed bar close, Supertrend(10,3) hl2 line, ATR14 Wilder, EMA20 5 bars back) from the library aux bars (to 2026-10-30); St1Dist ties the stored EINT1 feature to 7e-7 (E in place of the bar close), Slope = stored sig_slope x 5 (same ranks). The SZ-FGH proxies (dip size, EMA/TWAP slope, zone distance) were NOT used, because the real feature is reproducible. Differences vs live: rank history = the library signal list per book (all generator signals; DS7 also counts untaken signals), first 100 signals per book passive (4% of trades), no ES/RTY. Live-week features after 10-30 come from nq1m_state bars (recomputed, tie to aux: median |dist diff| 0.033 ATR, 90th pct 0.16). Verdict labels carry PRE-PROOF.
## 2. A. Signal-state rules: base-change proof and old-vs-new (every previously published cell)
Base change: old EINT1_RULES_DD (DS3_ONE_CONVENTION composite, per-print cut base, cap 2026-02-06) vs S1b-COMB (SZ_BASE_PROOF: cuts 56% -> 38% of exits, stops 3% -> 14%, L6M maxDD 105k -> 82k). Numbers below are NOT identical to the dollar (testing-defect check passed). Old 'cut' = minus the old page's maxDD change.
| rule (DS7 v1.4 Shadow) | OLD page EINT1_RULES_DD (old frame, as-is stack, lock off, cap 2026-02-06): maxDD cut % L6M / PRE / X' ; placebo rank L6M; OLD label | NEW first-order on S1b-COMB: cut % L6M / PRE / X' ; placebo p L6M | NEW label | same-to-the-dollar? |
|--|--|--|--|--|
| R1_H7_Slope_SkipBot | +17 / -19 / -9; .26; no (RISK-KEEP fail) | -2.3 / 1.5 / -5.6 ; 0.33 | no | no (differs) |
| R2_K7_St1Dist_SkipTop | -2 / +5 / -9; .57; no | -17.3 / 2.9 / -5.6 ; 0.99 | no | no (differs) |
| R3_P7_St1Dist_SizeHi | +14 / -18 / -6; .25; no | -29.2 / 9.1 / -57.1 ; 0.64 | UP (report, never promoted) | no (differs) |
| R4_H7_St1Dist_SkipBot | 0 / +14 / -5; .81; no | -4.2 / -7.4 / 2.2 ; 0.17 | no | no (differs) |

### 2. Reference rows (DS7 v1.4 settings, all Shadow; cells as the live code would act if switched Live)
| rule | id | nfire (lots changed) | maxDD cut % L6M / PRE / X' / HOLD (equal lots) | EQUAL-MEAN cut % L6M / PRE / X' / HOLD | d mean L6M $/wk | w20 cut % L6M / PRE | SEL (eq-mean cut avg) | placebo p L6M / PRE | family p | live-week delta $ | label |
|--|--|--|--|--|--|--|--|--|--|--|--|
| REF R1_H7_Slope_SkipBot | 0fbc1280 | 312 (1%) | -2.3 / 1.5 / -5.6 / 1.6 | -1.9 / 1.9 / -5.1 / 2.0 | 97 | 1.9 / -1.4 | -1.7 | 0.33 / 0.02 | 1.00 | 0 | no |
| REF R2_K7_St1Dist_SkipTop | f798ecfa | 2146 (10%) | -17.3 / 2.9 / -5.6 / 5.8 | -17.3 / 2.9 / -5.6 / 5.8 | -0 | -5.3 / -1.1 | -6.7 | 0.99 / 0.58 | 1.00 | 4400 | no |
| REF R3_P7_St1Dist_SizeHi | 07d05ec3 | 1675 (16%) | -29.2 / 9.1 / -57.1 / -3.7 | -45.7 / -2.6 / -77.3 / -17.0 | -2634 | 34.1 / 0.7 | -41.9 | 0.64 / 0.23 | 1.00 | 30383 | UP (report, never promoted) |
| REF R4_H7_St1Dist_SkipBot | 429814c8 | 621 (3%) | -4.2 / -7.4 / 2.2 / -0.3 | -6.6 / -9.9 / -0.1 / -2.6 | -571 | 11.3 / -0.7 | -5.5 | 0.17 / 0.81 | 1.00 | 1370 | no |
| REF RALL_live_shadow_set | aff85195 | 4490 (21%) | -22.4 / 7.9 / -18.8 / 1.7 | -47.3 / -10.8 / -43.0 / -18.3 | -3999 | 34.0 / -11.0 | -33.7 | 0.89 / 0.44 | 1.00 | 10221 | no |

Control bases (first-order):
| ref | NOCUT control (cut %) | UNIF control (cut %) |
|--|--|--|
| R1_H7_Slope_SkipBot |  |  |
| R2_K7_St1Dist_SkipTop |  |  |
| R3_P7_St1Dist_SizeHi |  |  |
| R4_H7_St1Dist_SkipBot |  |  |
| RALL_live_shadow_set |  |  |
### 2b. Control bases (first-order cut % L6M / PRE / X')
(see reference rows above; control-base cuts listed with each reference row)
### 3. Per book (down-only candidates ranked by SEL = mean of the equal-mean maxDD cut over L6M / PRE / X'; live shadow rule first; UP cells listed after)
#### K7 (library book KB)  walk-forward of the picking procedure (26 w train, 7 d embargo, 34 months): equal-mean OOS maxDD cut 7.1%, mean $/wk 15242 vs ref 16547, picks changed 34/34; equal-lots variant cut 12.0%
| rule | id | nfire (lots changed) | maxDD cut % L6M / PRE / X' / HOLD (equal lots) | EQUAL-MEAN cut % L6M / PRE / X' / HOLD | d mean L6M $/wk | w20 cut % L6M / PRE | SEL (eq-mean cut avg) | placebo p L6M / PRE | family p | live-week delta $ | label |
|--|--|--|--|--|--|--|--|--|--|--|--|
| LIVE-shadow R2_K7_St1Dist_SkipTop | f798ecfa | 2146 (10%) | -17.3 / 2.9 / -5.6 / 5.8 | -17.3 / 2.9 / -5.6 / 5.8 | -0 | -5.3 / -1.1 | -6.7 | 0.99 / 0.58 | 1.00 | 4400 | no |
| K7 Slope SkipTop  r=200 q=0.25 | ef2d0ba9 | 1560 (7%) | 5.3 / 4.6 / -3.7 / -1.0 | 6.9 / 6.1 / -2.0 / 0.7 | 447 | -11.2 / -1.6 | 3.7 | 0.13 / 0.28 | 1.00 | -2340 | LEAD PRE-PROOF |
| K7 Slope SkipTop  r=exp q=0.25 | 88a71558 | 1489 (7%) | 3.1 / 3.7 / -4.4 / -1.7 | 5.3 / 6.0 / -2.0 / 0.7 | 606 | -13.5 / -0.9 | 3.1 | 0.17 / 0.42 | 1.00 | -2340 | LEAD PRE-PROOF |
| K7 Slope SkipTop  r=100 q=0.25 | 6a0f8258 | 1541 (7%) | 1.5 / 4.9 / -1.5 / -2.2 | 2.7 / 6.0 / -0.3 / -0.9 | 306 | -10.5 / -3.0 | 2.8 | 0.16 / 0.31 | 1.00 | -3540 | LEAD PRE-PROOF |
| K7 Slope HalveTop  r=200 q=0.25 | dee394d9 | 144 (1%) | 1.6 / 1.9 / 1.0 / -1.2 | 2.9 / 3.2 / 2.3 / 0.2 | 322 | -3.2 / -0.3 | 2.8 | 0.04 / 0.06 | 1.00 | 0 | CANDIDATE (own-p only; family p 1.00) PRE-PROOF |
| K7 Slope HalveTop  r=exp q=0.25 | b41ac832 | 137 (1%) | 1.6 / 1.9 / 0.0 / -1.2 | 3.0 / 3.3 / 1.5 / 0.3 | 359 | -3.8 / -0.5 | 2.6 | 0.01 / 0.04 | 1.00 | 0 | CANDIDATE (own-p only; family p 1.00) PRE-PROOF |
| UP K7 St1Dist SizeHi  r=500 q=0.50 | 435e0c8c | 578 (19%) | -6.0 / 7.2 / 8.1 / -1.6 | -3.3 / 9.5 / 10.4 / 0.9 | 602 | 6.5 / -0.6 | 5.5 | 0.46 / 0.04 | 1.00 | 3726 | UP (report, never promoted) |
| UP K7 St1Dist SizeHi  r=exp q=0.50 | af829dca | 582 (19%) | -3.8 / 5.6 / 8.1 / -4.0 | -4.7 / 4.8 / 7.3 / -5.0 | -194 | 6.0 / -0.4 | 2.5 | 0.32 / 0.10 | 1.00 | 2906 | UP (report, never promoted) |

#### P7 (library book PE)  walk-forward of the picking procedure (26 w train, 7 d embargo, 34 months): equal-mean OOS maxDD cut 35.4%, mean $/wk 13544 vs ref 16547, picks changed 34/34; equal-lots variant cut 34.8%
| rule | id | nfire (lots changed) | maxDD cut % L6M / PRE / X' / HOLD (equal lots) | EQUAL-MEAN cut % L6M / PRE / X' / HOLD | d mean L6M $/wk | w20 cut % L6M / PRE | SEL (eq-mean cut avg) | placebo p L6M / PRE | family p | live-week delta $ | label |
|--|--|--|--|--|--|--|--|--|--|--|--|
| LIVE-shadow R3_P7_St1Dist_SizeHi | 07d05ec3 | 1675 (16%) | -29.2 / 9.1 / -57.1 / -3.7 | -45.7 / -2.6 / -77.3 / -17.0 | -2634 | 34.1 / 0.7 | -41.9 | 0.64 / 0.23 | 1.00 | 30383 | UP (report, never promoted) |
| P7 Slope SkipTop  r=exp q=0.50 | 81afc0ef | 2554 (12%) | 27.7 / 44.6 / 52.7 / 41.9 | 12.3 / 32.8 / 42.6 / 29.6 | -4098 | 35.8 / -32.6 | 29.3 | 0.14 / 0.17 | 1.00 | -47350 | LEAD PRE-PROOF |
| P7 Slope SkipTop  r=500 q=0.50 | 7f7e5d87 | 2531 (12%) | 12.7 / 50.6 / 55.2 / 29.9 | -8.7 / 38.4 / 44.2 / 12.7 | -4601 | 41.8 / -32.5 | 24.7 | 0.49 / 0.04 | 1.00 | -50835 | LEAD PRE-PROOF |
| P7 Slope SkipTop  r=100 q=0.50 | fb0c6f4b | 2520 (12%) | 17.8 / 43.0 / 55.6 / 34.0 | -4.1 / 27.8 / 43.8 / 16.4 | -4904 | 33.7 / -33.3 | 22.5 | 0.31 / 0.25 | 1.00 | -47350 | LEAD PRE-PROOF |
| P7 Slope SkipTop  r=300 q=0.50 | 9d8db053 | 2533 (12%) | 9.7 / 43.6 / 55.2 / 27.5 | -10.1 / 31.2 / 45.4 / 11.6 | -4200 | 33.4 / -32.8 | 22.2 | 0.52 / 0.14 | 1.00 | -50835 | LEAD PRE-PROOF |
| P7 Slope SkipTop  r=200 q=0.50 | 5cae0b0c | 2531 (12%) | 12.7 / 43.7 / 56.8 / 29.9 | -9.8 / 29.2 / 45.7 / 11.8 | -4788 | 27.7 / -33.2 | 21.7 | 0.47 / 0.12 | 1.00 | -50835 | LEAD PRE-PROOF |
| UP P7 St1Dist SizeLo  r=300 q=0.25 | b4c2e468 | 1151 (12%) | 16.3 / -10.7 / 39.8 / -10.6 | 29.5 / 6.7 / 49.3 / 6.9 | 4335 | -24.3 / 4.0 | 28.5 | 0.01 / 0.71 | 1.00 | -15335 | UP (report, never promoted) |
| UP P7 St1Dist SizeLo  r=200 q=0.25 | deccaf4f | 1155 (12%) | 11.0 / -17.2 / 39.8 / -6.4 | 27.3 / 4.2 / 50.8 / 13.0 | 5168 | -26.2 / 5.6 | 27.4 | 0.04 / 0.85 | 1.00 | -15335 | UP (report, never promoted) |

#### U7 (library book SM)  walk-forward of the picking procedure (26 w train, 7 d embargo, 34 months): equal-mean OOS maxDD cut 7.7%, mean $/wk 15358 vs ref 16547, picks changed 34/34; equal-lots variant cut -1.0%
| rule | id | nfire (lots changed) | maxDD cut % L6M / PRE / X' / HOLD (equal lots) | EQUAL-MEAN cut % L6M / PRE / X' / HOLD | d mean L6M $/wk | w20 cut % L6M / PRE | SEL (eq-mean cut avg) | placebo p L6M / PRE | family p | live-week delta $ | label |
|--|--|--|--|--|--|--|--|--|--|--|--|
| U7 Slope HalveBot  r=exp q=0.50 | 1b9224e5 | 487 (2%) | 5.0 / 1.6 / -9.1 / 1.6 | 6.2 / 2.8 / -7.8 / 2.8 | 257 | 1.2 / 0.9 | 0.4 | 0.03 / 0.84 | 1.00 | 2020 | LEAD PRE-PROOF |
| U7 Slope HalveBot  r=500 q=0.25 | 479a3aac | 237 (1%) | 5.6 / -0.5 / -5.7 / 1.1 | 6.1 / 0.1 / -5.1 / 1.6 | 125 | -0.5 / 0.1 | 0.4 | 0.02 / 0.86 | 1.00 | 2020 | no |
| U7 Slope SkipBot  r=500 q=0.25 | 8f403f2b | 309 (1%) | 11.0 / -1.0 / -12.3 / 4.4 | 11.9 / 0.1 / -11.1 / 5.4 | 221 | -1.2 / 0.3 | 0.3 | 0.06 / 0.93 | 1.00 | 4040 | no |
| U7 Slope HalveBot  r=200 q=0.33 | 45943c97 | 328 (2%) | 6.5 / 2.1 / -10.4 / 1.6 | 6.6 / 2.3 / -10.2 / 1.8 | 41 | 2.8 / 0.7 | -0.4 | 0.02 / 0.48 | 1.00 | 2020 | LEAD PRE-PROOF |
| U7 Slope HalveBot  r=200 q=0.25 | 26b485f5 | 239 (1%) | 5.6 / -0.5 / -5.7 / 1.1 | 5.4 / -0.7 / -5.9 / 0.9 | -40 | 1.3 / -0.4 | -0.4 | 0.01 / 0.85 | 1.00 | 2020 | no |
| UP U7 Slope SizeHi  r=exp q=0.50 | e720c621 | 487 (6%) | 6.3 / -8.6 / -11.8 / -0.9 | 11.5 / -2.6 / -5.6 / 4.6 | 1462 | -17.2 / 4.2 | 1.1 | 0.07 / 0.90 | 1.00 | 3762 | UP (report, never promoted) |
| UP U7 St1Dist SizeLo  r=300 q=0.25 | 0319d772 | 266 (3%) | -8.3 / 1.1 / 1.3 / -1.7 | -5.5 / 3.7 / 3.9 / 1.0 | 602 | -4.6 / -2.3 | 0.7 | 0.68 / 0.29 | 1.00 | 1870 | UP (report, never promoted) |

#### H7 (library book HM)  walk-forward of the picking procedure (26 w train, 7 d embargo, 34 months): equal-mean OOS maxDD cut -2.1%, mean $/wk 15626 vs ref 16547, picks changed 31/34; equal-lots variant cut 0.0%
| rule | id | nfire (lots changed) | maxDD cut % L6M / PRE / X' / HOLD (equal lots) | EQUAL-MEAN cut % L6M / PRE / X' / HOLD | d mean L6M $/wk | w20 cut % L6M / PRE | SEL (eq-mean cut avg) | placebo p L6M / PRE | family p | live-week delta $ | label |
|--|--|--|--|--|--|--|--|--|--|--|--|
| LIVE-shadow R1_H7_Slope_SkipBot | 0fbc1280 | 312 (1%) | -2.3 / 1.5 / -5.6 / 1.6 | -1.9 / 1.9 / -5.1 / 2.0 | 97 | 1.9 / -1.4 | -1.7 | 0.33 / 0.02 | 1.00 | 0 | no |
| LIVE-shadow R4_H7_St1Dist_SkipBot | 429814c8 | 621 (3%) | -4.2 / -7.4 / 2.2 / -0.3 | -6.6 / -9.9 / -0.1 / -2.6 | -571 | 11.3 / -0.7 | -5.5 | 0.17 / 0.81 | 1.00 | 1370 | no |
| H7 Slope HalveBot  r=100 q=0.25 | 6c80e4ba | 131 (1%) | 0.4 / 0.3 / 1.5 / 1.0 | 1.1 / 1.0 / 2.2 / 1.7 | 162 | 0.3 / -0.7 | 1.4 | 0.15 / 0.13 | 1.00 | 0 | LEAD PRE-PROOF |
| H7 Slope HalveBot  r=200 q=0.25 | b1e01960 | 127 (1%) | -0.2 / 0.3 / 1.5 / 1.0 | 0.5 / 1.0 / 2.2 / 1.7 | 168 | 0.6 / -0.5 | 1.3 | 0.31 / 0.05 | 1.00 | 0 | no |
| H7 St1Dist HalveBot  r=100 q=0.50 | c044b197 | 368 (2%) | 2.0 / -1.7 / 6.4 / 1.6 | 1.0 / -2.7 / 5.5 / 0.6 | -249 | 5.5 / -1.2 | 1.3 | 0.02 / 0.31 | 1.00 | 685 | no |
| H7 St1Dist HalveBot  r=300 q=0.50 | 18f2f3a6 | 370 (2%) | 2.0 / -1.7 / 6.4 / 1.6 | 0.9 / -2.8 / 5.4 / 0.5 | -280 | 5.9 / -1.1 | 1.1 | 0.03 / 0.38 | 1.00 | 685 | no |
| H7 Slope HalveBot  r=300 q=0.25 | 7d6325be | 129 (1%) | -0.2 / 0.3 / 1.5 / 1.0 | 0.3 / 0.8 / 2.0 / 1.5 | 121 | 0.6 / -0.5 | 1.1 | 0.27 / 0.08 | 1.00 | 0 | no |
| UP H7 St1Dist SizeHi  r=100 q=0.50 | 6b89d980 | 368 (3%) | 4.7 / 0.9 / 11.1 / 0.5 | 6.6 / 2.9 / 12.9 / 2.5 | 484 | -6.9 / -1.2 | 7.5 | 0.05 / 0.39 | 1.00 | 1285 | UP (report, never promoted) |
| UP H7 St1Dist SizeHi  r=300 q=0.50 | 9a4c9dac | 370 (3%) | 4.7 / 0.9 / 11.1 / 0.5 | 6.5 / 2.8 / 12.8 / 2.4 | 451 | -6.4 / -0.9 | 7.3 | 0.07 / 0.34 | 1.00 | 1285 | UP (report, never promoted) |

#### M7 (library book MV)  walk-forward of the picking procedure (26 w train, 7 d embargo, 34 months): equal-mean OOS maxDD cut 6.3%, mean $/wk 15647 vs ref 16547, picks changed 34/34; equal-lots variant cut 5.8%
| rule | id | nfire (lots changed) | maxDD cut % L6M / PRE / X' / HOLD (equal lots) | EQUAL-MEAN cut % L6M / PRE / X' / HOLD | d mean L6M $/wk | w20 cut % L6M / PRE | SEL (eq-mean cut avg) | placebo p L6M / PRE | family p | live-week delta $ | label |
|--|--|--|--|--|--|--|--|--|--|--|--|
| M7 Slope SkipBot  r=100 q=0.50 | 50fa5981 | 2264 (11%) | 9.0 / 5.9 / -0.7 / 9.1 | 10.9 / 7.8 / 1.4 / 11.0 | 576 | -27.8 / -6.1 | 6.7 | 0.27 / 0.51 | 1.00 | -2425 | LEAD PRE-PROOF |
| M7 St1Dist SkipBot  r=200 q=0.50 | 179930a4 | 2210 (10%) | 12.9 / 11.0 / -16.7 / 10.9 | 16.6 / 14.9 / -11.7 / 14.8 | 1145 | -25.8 / -7.5 | 6.6 | 0.05 / 0.20 | 1.00 | -1225 | LEAD PRE-PROOF |
| M7 St1Dist SkipBot  r=500 q=0.50 | 0f931c21 | 2220 (11%) | 15.6 / 7.8 / -16.9 / 10.5 | 19.3 / 11.9 / -11.7 / 14.4 | 1165 | -27.5 / -6.9 | 6.5 | 0.03 / 0.45 | 1.00 | -2425 | LEAD PRE-PROOF |
| M7 Slope SkipBot  r=200 q=0.50 | cbd35617 | 2272 (11%) | 10.2 / 6.9 / -1.2 / 10.3 | 11.3 / 8.1 / -0.0 / 11.4 | 331 | -23.9 / -7.3 | 6.4 | 0.22 / 0.51 | 1.00 | -2425 | LEAD PRE-PROOF |
| M7 Slope SkipBot  r=500 q=0.50 | 643e1b0a | 2287 (11%) | 9.4 / 7.6 / -2.1 / 9.1 | 10.6 / 8.9 / -0.7 / 10.3 | 377 | -25.2 / -5.8 | 6.3 | 0.29 / 0.41 | 1.00 | -2425 | LEAD PRE-PROOF |
| UP M7 Slope SizeHi  r=200 q=0.50 | b3bc99dd | 508 (13%) | -0.5 / -4.8 / 7.1 / -3.3 | 2.6 / -1.5 / 10.0 / -0.1 | 782 | -0.7 / 2.8 | 3.7 | 0.02 / 0.42 | 1.00 | 1058 | UP (report, never promoted) |
| UP M7 Slope SizeHi  r=100 q=0.50 | 227ec31d | 501 (13%) | -2.0 / -5.8 / 9.4 / -4.5 | 1.2 / -2.6 / 12.2 / -1.3 | 768 | -0.3 / 3.5 | 3.6 | 0.05 / 0.54 | 1.00 | 1058 | UP (report, never promoted) |

#### A7 (library book PB)  walk-forward of the picking procedure (26 w train, 7 d embargo, 34 months): equal-mean OOS maxDD cut 0.5%, mean $/wk 16394 vs ref 16547, picks changed 27/34; equal-lots variant cut -2.9%
| rule | id | nfire (lots changed) | maxDD cut % L6M / PRE / X' / HOLD (equal lots) | EQUAL-MEAN cut % L6M / PRE / X' / HOLD | d mean L6M $/wk | w20 cut % L6M / PRE | SEL (eq-mean cut avg) | placebo p L6M / PRE | family p | live-week delta $ | label |
|--|--|--|--|--|--|--|--|--|--|--|--|
| A7 St1Dist SkipBot  r=100 q=0.50 | 514415c0 | 23 (0%) | 0.0 / 0.0 / -0.5 / -1.2 | 0.4 / 0.4 / -0.0 / -0.8 | 94 | -1.4 / 0.0 | 0.3 | 0.56 / 0.86 | 1.00 | 395 | no |
| A7 St1Dist SkipBot  r=200 q=0.50 | 62bbb6e9 | 25 (0%) | 0.0 / 0.0 / -0.5 / -1.2 | 0.2 / 0.2 / -0.3 / -1.0 | 46 | -1.4 / -0.2 | 0.0 | 0.60 / 0.92 | 1.00 | 395 | no |
| A7 St1Dist SkipBot  r=300 q=0.50 | 33803ad7 | 27 (0%) | 0.0 / 0.0 / -0.5 / -1.2 | 0.2 / 0.2 / -0.3 / -1.0 | 46 | -1.4 / -0.2 | 0.0 | 0.62 / 0.89 | 1.00 | 395 | no |
| A7 St1Dist SkipBot  r=exp q=0.50 | 135435b5 | 32 (0%) | 0.0 / 0.0 / -0.5 / -1.2 | 0.2 / 0.2 / -0.3 / -1.0 | 46 | -1.4 / 0.0 | 0.0 | 0.59 / 0.78 | 1.00 | 395 | no |
| A7 St1Dist SkipBot  r=500 q=0.50 | 833107ef | 25 (0%) | 0.0 / 0.0 / -0.5 / -1.2 | 0.2 / 0.2 / -0.3 / -1.0 | 46 | -1.4 / -0.2 | 0.0 | 0.59 / 0.82 | 1.00 | 395 | no |
| UP A7 Slope SizeHi  r=200 q=0.50 | 0be99b5d | 0 (5%) | -1.1 / 2.9 / 0.3 / -2.8 | 3.2 / 7.0 / 4.5 / 1.5 | 1118 | -9.1 / 1.5 | 4.9 | 0.55 / 0.39 | 1.00 | -1415 | UP (report, never promoted) |
| UP A7 Slope SizeHi  r=300 q=0.50 | 7a4403b6 | 0 (5%) | -1.1 / 2.9 / -0.6 / -2.8 | 3.0 / 6.9 / 3.4 / 1.3 | 1070 | -9.1 / 1.5 | 4.4 | 0.53 / 0.82 | 1.00 | -1415 | UP (report, never promoted) |

## 3b. Per book x session (best cell per book)
### 4. Per book x session (best down-only cell per book, equal lots and equal-mean; ROLL-EXCL)
| book | rule | session | trades | nfire | maxDD cut % L6M / PRE / X' | EQUAL-MEAN cut % L6M / PRE / X' | d mean L6M $/wk |
|--|--|--|--|--|--|--|--|
| K7 | K7 Slope SkipTop  r=200 q=0.25 | asia | 2383 | 1560 | -2.3 / 14.6 / 45.0 | -1.5 / 15.3 / 45.5 | 16 |
| K7 | K7 Slope SkipTop  r=200 q=0.25 | london | 1760 | 1560 | 40.1 / -5.3 / -9.2 | 62.7 / 34.4 / 32.0 | 166 |
| K7 | K7 Slope SkipTop  r=200 q=0.25 | nyam | 1686 | 1560 | 10.2 / -21.8 / -8.8 |  /  /  | 125 |
| K7 | K7 Slope SkipTop  r=200 q=0.25 | nypm | 1356 | 1560 | 42.3 / 31.8 / -29.1 | 51.5 / 42.7 / -8.4 | 230 |
| P7 | P7 Slope SkipTop  r=exp q=0.50 | asia | 2288 | 2554 | 27.7 / 9.4 / -21.5 | -4.8 / -31.2 / -76.0 | -4365 |
| P7 | P7 Slope SkipTop  r=exp q=0.50 | london | 1679 | 2554 | 17.1 / 17.0 / 20.5 |  /  /  | -1281 |
| P7 | P7 Slope SkipTop  r=exp q=0.50 | nyam | 1303 | 2554 | 45.6 / 16.8 / 57.3 |  /  /  | 1878 |
| U7 | U7 Slope HalveBot  r=exp q=0.50 | asia | 687 | 487 | -45.2 / 8.9 / -3.9 | -80.9 / -13.6 / -29.5 | -668 |
| U7 | U7 Slope HalveBot  r=exp q=0.50 | london | 686 | 487 | 15.0 / 7.1 / -14.7 | 32.4 / 26.1 / 8.7 | 218 |
| H7 | H7 Slope HalveBot  r=100 q=0.25 | asia | 701 | 131 | 5.2 / 7.5 / 7.3 | 12.3 / 14.5 / 14.2 | 162 |
| H7 | H7 Slope HalveBot  r=100 q=0.25 | nyam | 415 | 131 | 0.0 / 0.0 / 0.0 | 0.0 / 0.0 / 0.0 | 0 |
| M7 | M7 Slope SkipBot  r=100 q=0.50 | london | 2722 | 2264 | 47.8 / 16.4 / 71.6 |  /  /  | 193 |
| M7 | M7 Slope SkipBot  r=100 q=0.50 | nyam | 1803 | 2264 | 68.4 / -50.0 / 62.9 | 80.5 / 7.4 / 77.1 | 244 |
| A7 | A7 St1Dist SkipBot  r=100 q=0.50 | asia | 1160 | 23 | 13.9 / 0.0 / 15.4 | 23.2 / 10.8 / 24.6 | 94 |
## 4. B. X1-X5 on the state base (own simulation; live X books carry no L2 cut, so the S1-COMB spec default None applies)
Signals by the library definitions on the state-day tape (validated to the second vs the 11-02 span except X5 cold start); 4,482 trades 2023-04..2026-10 (X1 839, X2 737, X3 1,193, X4 981, X5 732), library fill model, 2 lots, caps 12000/-4800 per book per day; no trade alive across a roll. State-cut variants (UNIF, LIVE, K7 cells) are hypothetical. Stack = S1b-COMB + X daily. Old-vs-new: old D7 cube X1-X5 total L3M -4,209 (old) / +5,828 (new, sign change; RECENT_WINS_REDO); the engine-free simulation here is a different base again (not comparable to the dollar).
### Reference row and single books (lots 2, caps, no cut)
| cell | X trades in cell | stack d mean L6M $/wk | stack maxDD cut % L6M / HOLD / PRE / X' (negative = X deepens the stack drawdown) | w20 cut % L6M / PRE | X standalone mean $/wk L6M / PRE / X' | placebo p L6M / PRE (permuted days) | family p (432 cells) | label |
|--|--|--|--|--|--|--|--|--|
| REF (live shadow set, 2 lots, caps, no cut) X|X1+X2+X3+X4+X5|lots2|none|cap1 | 4390 | -2819 | -47.6 / -18.5 / -18.6 / 1.3 | 39.2 / 17.0 | -2819 / 629 / -226 | 0.90 / 0.92 | 1.00 | no |
| X|X1|lots2|none|cap1 | 4390 | -286 | -10.0 / -7.6 / -3.8 / 11.1 | -2.3 / 1.5 | -286 / 1605 / 661 | 0.83 / 0.80 | 1.00 | no |
| X|X2|lots2|none|cap1 | 4390 | 171 | -20.0 / 0.0 / -2.9 / -15.8 | 13.3 / -0.1 | 171 / 634 / -216 | 0.98 / 0.68 | 1.00 | no |
| X|X3|lots2|none|cap1 | 4390 | -3017 | -7.3 / -4.5 / -3.1 / -2.8 | 12.7 / 8.6 | -3017 / -608 / 627 | 0.36 / 0.62 | 1.00 | no |
| X|X4|lots2|none|cap1 | 4390 | -536 | -3.1 / -4.6 / -2.9 / 9.1 | -3.2 / 0.5 | -536 / 361 / -83 | 0.39 / 0.71 | 1.00 | no |
| X|X5|lots2|none|cap1 | 4390 | -895 | -22.0 / -0.4 / -5.9 / -10.5 | 23.4 / 5.6 | -895 / -359 / -621 | 0.99 / 0.88 | 1.00 | no |
### Top 5 cells by mean of stack cut over L6M/PRE/X' (432-cell grid)
| cell | X trades in cell | stack d mean L6M $/wk | stack maxDD cut % L6M / HOLD / PRE / X' (negative = X deepens the stack drawdown) | w20 cut % L6M / PRE | X standalone mean $/wk L6M / PRE / X' | placebo p L6M / PRE (permuted days) | family p (432 cells) | label |
|--|--|--|--|--|--|--|--|--|
| X|X4|lots4|K7cell|cap1 | 3935 | -533 | 2.7 / -1.0 / 0.8 / 23.2 | -9.7 / 0.8 | -533 / 647 / -57 | 0.20 / 0.51 | 1.00 | LEAD PRE-PROOF |
| X|X1+X3+X4|lots2|none|cap1 | 4390 | -2704 | -5.3 / -16.6 / -9.8 / 35.5 | 4.5 / 11.1 | -2704 / 497 / 801 | 0.24 / 0.95 | 1.00 | no |
| X|X4|lots4|K7cell|cap0 | 4482 | -1502 | -2.3 / -5.7 / 1.0 / 20.1 | 6.9 / 0.9 | -1502 / 1011 / 73 | 0.28 / 0.47 | 1.00 | no |
| X|X1+X3+X4|lots2|none|cap0 | 4482 | -3158 | -8.6 / -14.6 / -8.7 / 35.5 | 8.8 / 10.4 | -3158 / 780 / 801 | 0.43 / 0.79 | 1.00 | no |
| X|X4|lots4|UNIF|cap1 | 4023 | -953 | 0.7 / -4.8 / 1.3 / 15.7 | 1.4 / 5.3 | -953 / -258 / -454 | 0.12 / 0.49 | 1.00 | LEAD PRE-PROOF |
Reading: adding the X set at 2 lots deepens the stack maxDD (L6M -48%, PRE -19%); no X cell has a stack cut that beats the placebo (permuted days) with family p <= .10. Label LEAD only where L6M and PRE cuts are both positive.
## 5. C. Flip-level (DS7 v1.4 FlipEngine at 1-s bins; 20 engines x reach 5 x action {skip = mean-type, halve = cut-type} x 8 scopes)
Old (DS3_BT_SWING_FLIP_CANDIDATE, V13Y): label LEAD, MEAN-type, not RISK-KEEP. New flag rate at D40/4h/10: 6.05% of S1b-COMB trades (old 5.5%).
| window | OLD (V13Y, per-print cut base): flagged n / saved $k / placebo rank A | NEW (S1b-COMB first-order): flagged n / saved $k (= minus flagged base net) | same-to-the-dollar? |
|--|--|--|--|
| L6M | 204 / +69.8 / 0.005 | 198 / +61.8 | no |
| HOLD | 359 / +74.9 / 0.005 | 381 / +91.6 | no |
| PRE | 416 / +103.4 / 0.040 | 518 / +89.1 | no |
| X' | 155 / +50.1 / 0.075 | 249 / +45.3 | no |
### 2C. Reference row (DS7 v1.4 FlipMode Shadow: break 10, valid 4 h, reach 40, skip)
| rule | id | nfire (lots changed) | maxDD cut % L6M / PRE / X' / HOLD (equal lots) | EQUAL-MEAN cut % L6M / PRE / X' / HOLD | d mean L6M $/wk | w20 cut % L6M / PRE | SEL (eq-mean cut avg) | placebo p L6M / PRE | family p | live-week delta $ | label |
|--|--|--|--|--|--|--|--|--|--|--|--|
| REF flip brk10 valid4h reach40 skip ALL | b5e5516b | 1279 (6%) | 3.8 / 3.0 / 13.2 / 12.5 | 14.8 / 14.1 / 23.1 / 22.5 | 3461 | -32.1 / -7.7 | 17.3 | 0.23 / 0.67 | 1.00 | -1930 | LEAD PRE-PROOF |
### 3C. Per scope (ALL books and each book), best 5 by SEL, skip (mean-type) and halve (cut-type) shown separately
#### scope ALL  walk-forward of the picking procedure (skip cells; equal-mean OOS maxDD cut 4.9%, OOS mean 14076 vs ref 16547, picks changed 34/34; equal-lots variant -0.2%)
| rule | id | nfire (lots changed) | maxDD cut % L6M / PRE / X' / HOLD (equal lots) | EQUAL-MEAN cut % L6M / PRE / X' / HOLD | d mean L6M $/wk | w20 cut % L6M / PRE | SEL (eq-mean cut avg) | placebo p L6M / PRE | family p | live-week delta $ | label |
|--|--|--|--|--|--|--|--|--|--|--|--|
| skip flip brk15 valid8h reach60 skip ALL | cd8d7b17 | 3022 (14%) | 0.1 / -0.2 / 37.5 / 19.8 | 11.8 / 11.6 / 44.9 / 29.2 | 3152 | -4.4 / -9.4 | 22.8 | 0.57 / 0.80 | 1.00 | -16080 | no |
| skip flip brk15 valid4h reach40 skip ALL | 6290c22d | 1535 (7%) | 10.9 / 4.3 / 23.4 / 10.4 | 20.7 / 14.8 / 31.8 / 20.2 | 3306 | -20.5 / -9.4 | 22.4 | 0.18 / 0.66 | 1.00 | -900 | LEAD PRE-PROOF |
| skip flip brk15 valid6h reach60 skip ALL | 0b47384d | 2455 (12%) | -0.8 / 1.5 / 24.5 / 19.1 | 13.1 / 15.1 / 34.9 / 30.2 | 3778 | -9.2 / -6.9 | 21.0 | 0.50 / 0.81 | 1.00 | -10195 | no |
| skip flip brk15 valid4h reach30 skip ALL | 0ae8c1b0 | 1316 (6%) | 7.0 / 5.9 / 16.4 / 10.4 | 17.4 / 16.5 / 25.8 / 20.4 | 3389 | -25.5 / -8.0 | 19.9 | 0.19 / 0.54 | 1.00 | -1250 | LEAD PRE-PROOF |
| skip flip brk15 valid6h reach50 skip ALL | d0b62872 | 2287 (11%) | -5.8 / 3.1 / 18.1 / 15.1 | 7.9 / 15.7 / 28.7 / 26.0 | 3519 | -7.0 / -6.5 | 17.4 | 0.60 / 0.74 | 1.00 | -10415 | no |
| halve flip brk15 valid6h reach60 halve ALL | cf75f08e | 884 (4%) | 4.7 / 0.8 / 14.5 / 6.1 | 9.9 / 6.2 / 19.1 / 11.2 | 1545 | -7.6 / -3.5 | 11.8 | 0.19 / 0.74 | 1.00 | -3511 | LEAD PRE-PROOF |
| halve flip brk15 valid6h reach40 halve ALL | 3003f25e | 748 (4%) | 4.9 / 1.2 / 13.3 / 8.5 | 9.8 / 6.3 / 17.8 / 13.3 | 1463 | -10.8 / -3.5 | 11.3 | 0.20 / 0.60 | 1.00 | 660 | LEAD PRE-PROOF |
| halve flip brk15 valid4h reach60 halve ALL | 016c0298 | 590 (3%) | 4.9 / 2.9 / 12.1 / 4.0 | 9.6 / 7.7 / 16.4 / 8.7 | 1384 | -9.7 / -4.7 | 11.2 | 0.08 / 0.54 | 1.00 | 1970 | LEAD PRE-PROOF |
| halve flip brk15 valid4h reach40 halve ALL | 6ab7691d | 521 (2%) | 4.9 / 0.7 / 12.5 / 4.0 | 9.9 / 5.9 / 17.0 / 9.0 | 1476 | -12.4 / -4.2 | 10.9 | 0.16 / 0.67 | 1.00 | 660 | LEAD PRE-PROOF |
| halve flip brk10 valid4h reach40 halve ALL | 51539d09 | 448 (2%) | 5.2 / 0.7 / 9.0 / 4.2 | 10.9 / 6.7 / 14.5 / 10.0 | 1719 | -19.4 / -3.5 | 10.7 | 0.07 / 0.71 | 1.00 | 660 | LEAD PRE-PROOF |

#### scope K7  walk-forward of the picking procedure (skip cells; equal-mean OOS maxDD cut -4.9%, OOS mean 15975 vs ref 16547, picks changed 33/34; equal-lots variant -5.4%)
| rule | id | nfire (lots changed) | maxDD cut % L6M / PRE / X' / HOLD (equal lots) | EQUAL-MEAN cut % L6M / PRE / X' / HOLD | d mean L6M $/wk | w20 cut % L6M / PRE | SEL (eq-mean cut avg) | placebo p L6M / PRE | family p | live-week delta $ | label |
|--|--|--|--|--|--|--|--|--|--|--|--|
| skip flip brk15 valid4h reach50 skip K7 | a7c6ea57 | 895 (4%) | 1.6 / -2.3 / 1.1 / 2.6 | 7.0 / 3.3 / 6.5 / 7.9 | 1366 | -10.5 / 1.8 | 5.6 | 0.22 / 0.86 | 1.00 | 1170 | no |
| skip flip brk20 valid4h reach50 skip K7 | 2d242dce | 997 (5%) | 0.1 / -3.1 / 3.0 / 1.4 | 4.8 / 1.7 / 7.5 / 6.0 | 1156 | -8.0 / 2.0 | 4.7 | 0.23 / 0.86 | 1.00 | 590 | no |
| skip flip brk20 valid6h reach50 skip K7 | ac419607 | 1168 (6%) | -0.2 / -3.1 / -2.0 / 2.3 | 5.8 / 3.0 / 4.0 / 8.1 | 1492 | -11.2 / 2.1 | 4.3 | 0.34 / 0.78 | 1.00 | 1285 | no |
| halve flip brk20 valid4h reach60 halve K7 | cfa9fb1e | 94 (0%) | -0.3 / -0.8 / 1.7 / -1.2 | 0.8 / 0.4 / 2.9 / -0.0 | 247 | -3.0 / 0.6 | 1.4 | 0.48 / 0.92 | 1.00 | 0 | no |
| halve flip brk15 valid8h reach60 halve K7 | 729ce4cd | 121 (1%) | 0.7 / -1.6 / -0.6 / -1.2 | 2.5 / 0.2 / 1.2 / 0.6 | 432 | -3.2 / 0.6 | 1.3 | 0.11 / 0.95 | 1.00 | 0 | no |
| halve flip brk10 valid4h reach60 halve K7 | 4d9918a6 | 78 (0%) | -0.3 / -0.8 / 0.8 / -1.2 | 1.1 / 0.6 / 2.2 / 0.2 | 334 | -4.5 / 0.9 | 1.3 | 0.51 / 0.89 | 1.00 | 0 | no |

#### scope P7  walk-forward of the picking procedure (skip cells; equal-mean OOS maxDD cut 18.9%, OOS mean 14857 vs ref 16547, picks changed 34/34; equal-lots variant 1.3%)
| rule | id | nfire (lots changed) | maxDD cut % L6M / PRE / X' / HOLD (equal lots) | EQUAL-MEAN cut % L6M / PRE / X' / HOLD | d mean L6M $/wk | w20 cut % L6M / PRE | SEL (eq-mean cut avg) | placebo p L6M / PRE | family p | live-week delta $ | label |
|--|--|--|--|--|--|--|--|--|--|--|--|
| skip flip brk15 valid8h reach60 skip P7 | 7fbfe290 | 618 (3%) | -2.6 / 4.8 / 37.3 / 13.7 | 3.4 / 10.3 / 40.9 / 18.7 | 1466 | 11.3 / -9.4 | 18.2 | 0.49 / 0.58 | 1.00 | -9370 | no |
| skip flip brk15 valid6h reach60 skip P7 | ff7e223b | 521 (2%) | -4.1 / 4.8 / 31.1 / 14.4 | -0.3 / 8.2 / 33.6 / 17.5 | 894 | 13.5 / -8.7 | 13.8 | 0.50 / 0.55 | 1.00 | -4570 | no |
| skip flip brk15 valid6h reach40 skip P7 | 381b7896 | 427 (2%) | -4.1 / 3.0 / 30.9 / 14.4 | -0.1 / 6.8 / 33.6 / 17.7 | 957 | 8.1 / -8.6 | 13.4 | 0.47 / 0.50 | 1.00 | 0 | no |
| halve flip brk15 valid8h reach60 halve P7 | c74b5bc4 | 573 (3%) | 0.2 / 1.9 / 17.6 / 6.9 | 3.2 / 4.9 / 20.2 / 9.8 | 753 | 2.1 / -4.9 | 9.4 | 0.39 / 0.59 | 1.00 | -4171 | LEAD PRE-PROOF |
| halve flip brk15 valid6h reach60 halve P7 | 78bf4bd2 | 485 (2%) | -0.5 / 1.9 / 14.3 / 7.3 | 1.5 / 3.8 / 16.0 / 9.1 | 480 | 2.7 / -4.5 | 7.1 | 0.31 / 0.57 | 1.00 | -1771 | no |
| halve flip brk10 valid8h reach60 halve P7 | d0f8a248 | 483 (2%) | 1.6 / 0.6 / 10.7 / 7.5 | 4.4 / 3.4 / 13.2 / 10.2 | 791 | -5.0 / -4.0 | 7.0 | 0.18 / 0.66 | 1.00 | -1771 | LEAD PRE-PROOF |

#### scope U7  walk-forward of the picking procedure (skip cells; equal-mean OOS maxDD cut -4.6%, OOS mean 15412 vs ref 16547, picks changed 34/34; equal-lots variant 0.0%)
| rule | id | nfire (lots changed) | maxDD cut % L6M / PRE / X' / HOLD (equal lots) | EQUAL-MEAN cut % L6M / PRE / X' / HOLD | d mean L6M $/wk | w20 cut % L6M / PRE | SEL (eq-mean cut avg) | placebo p L6M / PRE | family p | live-week delta $ | label |
|--|--|--|--|--|--|--|--|--|--|--|--|
| skip flip brk15 valid4h reach40 skip U7 | 1ff701a3 | 117 (1%) | -0.1 / 0.0 / -0.1 / 2.4 | 5.1 / 5.2 / 5.1 / 7.4 | 1220 | -18.2 / 0.2 | 5.1 | 0.50 / 0.67 | 1.00 | 120 | no |
| skip flip brk20 valid4h reach40 skip U7 | 3d7674fc | 130 (1%) | -0.1 / 0.0 / -0.1 / 2.4 | 4.5 / 4.6 / 4.5 / 6.9 | 1081 | -16.8 / -0.4 | 4.5 | 0.52 / 0.82 | 1.00 | 120 | no |
| skip flip brk10 valid4h reach40 skip U7 | 09062498 | 100 (0%) | -0.1 / 0.0 / -0.1 / 2.4 | 3.5 / 3.6 / 3.5 / 5.9 | 1025 | -16.7 / -0.5 | 3.5 | 0.54 / 0.70 | 1.00 | 120 | no |
| halve flip brk15 valid4h reach40 halve U7 | c4ec8331 | 87 (0%) | 0.7 / 0.0 / 1.3 / 1.2 | 3.3 / 2.6 / 3.9 / 3.8 | 600 | -8.9 / 0.2 | 3.3 | 0.17 / 0.84 | 1.00 | 660 | no |
| halve flip brk20 valid4h reach40 halve U7 | 5a402d28 | 95 (0%) | 0.7 / 0.0 / 1.3 / 1.2 | 3.1 / 2.4 / 3.7 / 3.6 | 554 | -8.2 / -0.2 | 3.1 | 0.22 / 0.82 | 1.00 | 660 | no |
| halve flip brk10 valid4h reach40 halve U7 | 062e4f63 | 72 (0%) | 0.7 / 0.0 / 1.3 / 1.2 | 2.5 / 1.8 / 3.1 / 3.0 | 502 | -8.2 / -0.2 | 2.4 | 0.18 / 0.80 | 1.00 | 660 | no |

#### scope H7  walk-forward of the picking procedure (skip cells; equal-mean OOS maxDD cut 1.2%, OOS mean 16280 vs ref 16547, picks changed 29/34; equal-lots variant 0.0%)
| rule | id | nfire (lots changed) | maxDD cut % L6M / PRE / X' / HOLD (equal lots) | EQUAL-MEAN cut % L6M / PRE / X' / HOLD | d mean L6M $/wk | w20 cut % L6M / PRE | SEL (eq-mean cut avg) | placebo p L6M / PRE | family p | live-week delta $ | label |
|--|--|--|--|--|--|--|--|--|--|--|--|
| skip flip brk5 valid1h reach20 skip H7 | 50abbc4a | 6 (0%) | 0.0 / 0.0 / -0.7 / 0.0 | 0.0 / 0.0 / -0.7 / 0.0 | 0 | 0.0 / -0.3 | -0.2 | 0.94 / 0.92 | 1.00 | 0 | no |
| skip flip brk5 valid1h reach30 skip H7 | 22e4b082 | 6 (0%) | 0.0 / 0.0 / -0.7 / 0.0 | 0.0 / 0.0 / -0.7 / 0.0 | 0 | 0.0 / -0.3 | -0.2 | 0.90 / 0.94 | 1.00 | 0 | no |
| skip flip brk5 valid1h reach40 skip H7 | 3ba58207 | 6 (0%) | 0.0 / 0.0 / -0.7 / 0.0 | 0.0 / 0.0 / -0.7 / 0.0 | 0 | 0.0 / -0.3 | -0.2 | 0.96 / 0.94 | 1.00 | 0 | no |
| halve flip brk20 valid8h reach60 halve H7 | 616a6096 | 37 (0%) | 0.0 / 0.0 / 0.5 / 0.0 | 0.2 / 0.2 / 0.6 / 0.2 | 36 | -0.6 / -0.2 | 0.3 | 0.65 / 0.77 | 1.00 | 0 | no |
| halve flip brk20 valid4h reach40 halve H7 | 72294b3b | 11 (0%) | 0.0 / 0.0 / 0.5 / 0.0 | 0.0 / 0.0 / 0.5 / 0.0 | 0 | 0.0 / -0.3 | 0.2 | 0.88 / 0.88 | 1.00 | 0 | no |
| halve flip brk20 valid6h reach30 halve H7 | 3a0032b4 | 17 (0%) | 0.0 / 0.0 / 0.5 / 0.0 | 0.0 / 0.0 / 0.5 / 0.0 | 0 | 0.0 / -0.3 | 0.2 | 0.81 / 0.88 | 1.00 | 0 | no |

#### scope M7  walk-forward of the picking procedure (skip cells; equal-mean OOS maxDD cut 1.4%, OOS mean 16113 vs ref 16547, picks changed 34/34; equal-lots variant 1.9%)
| rule | id | nfire (lots changed) | maxDD cut % L6M / PRE / X' / HOLD (equal lots) | EQUAL-MEAN cut % L6M / PRE / X' / HOLD | d mean L6M $/wk | w20 cut % L6M / PRE | SEL (eq-mean cut avg) | placebo p L6M / PRE | family p | live-week delta $ | label |
|--|--|--|--|--|--|--|--|--|--|--|--|
| skip flip brk20 valid4h reach50 skip M7 | e25efbba | 244 (1%) | 0.6 / 2.6 / -1.0 / -0.4 | 3.4 / 5.3 / 1.8 / 2.4 | 655 | -8.1 / -2.5 | 3.5 | 0.34 / 0.19 | 1.00 | -1610 | LEAD PRE-PROOF |
| skip flip brk20 valid4h reach60 skip M7 | aaa8fbd1 | 246 (1%) | 0.6 / 2.6 / -1.0 / -0.4 | 3.4 / 5.3 / 1.8 / 2.4 | 655 | -8.1 / -2.5 | 3.5 | 0.47 / 0.23 | 1.00 | -1610 | LEAD PRE-PROOF |
| skip flip brk5 valid4h reach50 skip M7 | 451f6906 | 119 (1%) | 0.5 / 1.9 / 3.9 / 0.0 | 1.9 / 3.2 / 5.2 / 1.4 | 338 | -4.4 / -1.7 | 3.4 | 0.31 / 0.13 | 1.00 | -2400 | LEAD PRE-PROOF |
| halve flip brk15 valid8h reach50 halve M7 | 7fdd1d40 | 85 (0%) | 0.1 / 1.5 / 0.9 / 1.3 | 0.8 / 2.1 / 1.6 / 1.9 | 153 | -0.9 / -0.7 | 1.5 | 0.36 / 0.04 | 1.00 | -1200 | LEAD PRE-PROOF |
| halve flip brk10 valid8h reach40 halve M7 | 6f5f8063 | 66 (0%) | 0.1 / 1.5 / 0.7 / 1.3 | 0.7 / 2.1 / 1.4 / 1.9 | 149 | -1.5 / -0.6 | 1.4 | 0.48 / 0.03 | 1.00 | 0 | LEAD PRE-PROOF |
| halve flip brk15 valid8h reach40 halve M7 | 2d4f1112 | 77 (0%) | 0.1 / 1.5 / 0.9 / 1.3 | 0.7 / 2.0 / 1.5 / 1.8 | 130 | -1.6 / -0.7 | 1.4 | 0.39 / 0.07 | 1.00 | 0 | LEAD PRE-PROOF |

#### scope A7  walk-forward of the picking procedure (skip cells; equal-mean OOS maxDD cut 0.0%, OOS mean 16435 vs ref 16547, picks changed 24/34; equal-lots variant 0.0%)
| rule | id | nfire (lots changed) | maxDD cut % L6M / PRE / X' / HOLD (equal lots) | EQUAL-MEAN cut % L6M / PRE / X' / HOLD | d mean L6M $/wk | w20 cut % L6M / PRE | SEL (eq-mean cut avg) | placebo p L6M / PRE | family p | live-week delta $ | label |
|--|--|--|--|--|--|--|--|--|--|--|--|
| skip flip brk10 valid8h reach60 skip A7 | bef305e9 | 55 (0%) | 0.8 / 0.0 / 3.6 / 0.0 | 1.4 / 0.6 / 4.2 / 0.6 | 148 | -0.3 / 0.2 | 2.1 | 0.13 / 0.79 | 1.00 | -1200 | no |
| skip flip brk15 valid8h reach50 skip A7 | 8ca710f2 | 60 (0%) | 0.8 / 0.0 / 3.6 / 0.0 | 1.3 / 0.5 / 4.1 / 0.5 | 118 | -0.6 / 0.2 | 2.0 | 0.11 / 0.22 | 1.00 | -1200 | LEAD PRE-PROOF |
| skip flip brk10 valid8h reach50 skip A7 | 1393a113 | 51 (0%) | 0.8 / 0.0 / 3.6 / 0.0 | 1.3 / 0.5 / 4.1 / 0.5 | 119 | 0.1 / 0.2 | 1.9 | 0.11 / 0.74 | 1.00 | -1200 | no |
| halve flip brk5 valid1h reach20 halve A7 | 04b474cc | 0 (0%) | 0.0 / 0.0 / 0.0 / 0.0 | 0.0 / 0.0 / 0.0 / 0.0 | 0 | 0.0 / 0.0 | 0.0 |  /  |  | 0 | no |
| halve flip brk5 valid1h reach30 halve A7 | b255c8f4 | 0 (0%) | 0.0 / 0.0 / 0.0 / 0.0 | 0.0 / 0.0 / 0.0 / 0.0 | 0 | 0.0 / 0.0 | 0.0 |  /  |  | 0 | no |
| halve flip brk5 valid1h reach40 halve A7 | b68ce085 | 0 (0%) | 0.0 / 0.0 / 0.0 / 0.0 | 0.0 / 0.0 / 0.0 / 0.0 | 0 | 0.0 / 0.0 | 0.0 |  /  |  | 0 | no |

## 6. TOP-K registered
/mnt/l2/l2vast/_th_joint/layers/shadow/topK.json (layers shadow_sigstate and shadow_flip, K=5 each, live setting one, per-trade tables trades_<id>.parquet). Exact status: queued, none complete at writing.
## 7. Caveats
Walk-forward = purged monthly, 26 w train, 7 d embargo, picks by trailing weekly maxDD after scaling to the reference trailing mean (equal-mean) or at equal lots; the label's wf_ok uses the equal-mean procedure of the scope. First-order cannot see re-entries or lock interactions (exact pending). A7 signal-state cells cannot be run exact (no L2-gated sizing path). Rank windows 100-500 cut tests are in the grid (1,080 cells x 3 bases).
