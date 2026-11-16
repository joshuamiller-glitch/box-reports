# DS3_TARGET_REPLAY_DYN - STEP 1 dynamic-target families h, j, k (W-RP2), first version 2026-11-16
> VALIDATION (W-DV, FIRST PASS, 2026-11-16): trials counted dynamic rules h/j/k (35 rule names x 15 scopes, TRIALS_LEDGER.csv TB-hr TB-jr TB-k); correction none (replay screen); PBO not fitted; number shown is IN-SAMPLE; data end 2026-10-31.

VERDICT (data ends 2026-10-30; FIRST PASS, replay only, not engine): the dynamic exits are weak drawdown tools on JL2. Of 22 scopes (15 book|session cells and 7 books), 8 have a rule that passes the mean gate (cell mean >= -5%), cuts whole-stack DD over 43 months AND the HOLD path, and is not isolated on its neighbour surface; the cuts are small (best 2-9%) and mostly structure targets with a trailing or real-exit remainder (h_NOR_HT15/HT20/HR, h_VWP_HR) or give-back (k_F60_B30/B40, k_F40_B40 on K7 nyam). The ES/RTY/NKD turn-against exits (family j) cut DD up to 8-17% in HP but destroy 70-85% of the cell mean (they fire on 1-min noise once NQ is +15), so none passes the gate except 4 odd cells; K7 asia, K7 london, M7 nyam, O7 and P7 nyam have no gated rule at all (the JSON lists the best by DD with gate_mean_ok=false). Replay ignores freed-book re-entries (PATH EFFECT = FREED-BOOK REPLACEMENT, generic: earlier exits free the book and weaker re-signals follow, so the DD cuts here are first-order and the engine decides).

FIRST PASS labels: every row is REPLAY ONLY (no engine, no controls). Rows are merged into W-RP's ranking via /mnt/l2/l2vast/_replay/arr_hjk_v1.npz (W-RP schema: id|rpts, id|ppts, id|xsec) and /mnt/l2/l2vast/_replay/step1_top2_dyn.json (same schema as step1_top2.json, plus gate_mean_ok, isolated, neighbours_agree).

BASIS: JL2 = TL3_EV_JN05W2JL2, 18,979 trades, 43 months 202304..202610, real entry and real exit kept; alternative exit = earlier of alternative firing and real exit (real exit second excluded unless the real exit is Target); 1-s paths from the state tape (/mnt/l2/l2vast/_th_state/days); dollars BASE lots, engine fee $1.18 RT (column @4.84 reprices the cell mean at $4.84 RT, -$3.66 per base contract); live x1.75 rounding NOT applied here (W-RP's rp_score applies it on merge); partials: half the base lots at the partial price, half remainder. DD = whole stack (only the scope's trades altered) by Globex-day label, worst week Mon-Sun by label, HP = 2025-11-17..12-10 DD, HOLD = 20251101..20260430, L6M = 20260501..20261031. Mean gate on the scope's own mean, FULL43 $/wk. Rank = DD43 cut% + HP cut%. Surface: neighbours = adjacent variants (h: AT, M2, HR, HT30, HT20, HT15 order; k: F/B grid; j: other lookback / other sigma); ISOLATED when fewer than half the neighbours cut DD in both 43 months and HP.

DEFINITIONS (chosen where unspecified):
- h levels, frozen at the entry second from data up to it: prior-day high/low (previous Globex-day file), overnight high/low (18:00 to 09:30 ET running), session high/low and anchored VWAP with +-1/2 sigma (volume-weighted, tape trades; session start ET asia 18:00, london 03:00, nyam 09:30, nypm 13:00), 5-min swing high/low (strength 2, confirmed two bars later), round 50s. Target = nearest level with distance in [+15,+58] in the trade direction. Level sets: ALL, NOR (all except round 50s), R50 (round 50s only), VWP (VWAP and bands only). Variants: AT (limit at level, touch fills), M2 (2 pts before), HR (half off at level, rest keeps the real exit), HT15/HT20/HT30 (half off at level, rest trails 15/20/30 pts from the previous-second extreme, real exit stays as backstop; the trail cannot extend beyond the real exit).
- j: ES/RTY/NKD 1-min panel (/mnt/l2/l2vast/_th_cross/min1.npz, causal log price, completed bars only: bar ts <= s-60); signed return over 1 or 5 min against the trade side beyond 0 or 0.5 sigma (sigma = trailing 240-min std of 1-min returns x sqrt(n)); fires only while NQ mid pnl >= +15; fill = 1-s mid - 0.8. Each market alone and any-2-of-3. NKD is missing in ~34% of minutes (no signal then).
- k: best = running max of 1-s mid pnl; exit when best >= B (20/30/40) and give-back >= f (40/50/60%) of best; fill = mid - 0.8 slip.
- Fees on partials unchanged; no extra fee for the split. Rows not run: families i (MBO) are outside this agent.

CODE: code/th_rp2/rp2_replay.py, rp2_score.py; scores for every cell x rule (1,078 rows): /mnt/l2/l2vast/_replay/rp2/scores.csv.

## Per-scope tables (book|session cells and per-book aggregates; a book rule applies to the same rule across all its sessions)

### A7|asia  (baseline cell mean +710/wk, cell DD43 -13,724; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 +689)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_NOR_HT15 | 282/1156 | +678 (-4.5%) | -71,311 (+4.2%) | -43,527 | -69,479 (+6.6%) | -69,479 (+6.6%) | -24,326 (-7.8%) | +476 / -250 | +658 | +28/-89/-94/+40 | ok 1/1 |
| h_NOR_HT20 | 282/1156 | +678 (-4.6%) | -71,461 (+4.0%) | -43,527 | -69,624 (+6.4%) | -69,624 (+6.4%) | -23,991 (-6.3%) | +477 / -277 | +657 | +39/-94/-94/+33 | ok 2/2 |
| h_NOR_HR | 282/1156 | +690 (-2.9%) | -72,508 (+2.5%) | -43,527 | -71,914 (+3.3%) | -71,914 (+3.3%) | -23,361 (-3.5%) | +225 / -134 | +669 | +21/-45/-63/+15 | ok 2/2 |
| h_VWP_HR | 168/1156 | +681 (-4.1%) | -73,622 (+1.0%) | -43,527 | -73,622 (+1.0%) | -73,622 (+1.0%) | -23,293 (-3.2%) | -28 / -20 | +660 | +26/-60/-29/-42 | ok 2/2 |

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_NOR_HT15 | 282/1156 | +678 (-4.5%) | -71,311 (+4.2%) | -43,527 | -69,479 (+6.6%) | -69,479 (+6.6%) | -24,326 (-7.8%) | +476 / -250 | +658 | +28/-89/-94/+40 | ok 1/1 |
| h_NOR_AT | 282/1156 | +670 (-5.7%) | -71,399 (+4.0%) | -43,527 | -69,427 (+6.7%) | -69,427 (+6.7%) | -24,213 (-7.3%) | +450 / -267 | +649 | +41/-91/-126/+29 | ok 1/1 |

### H7|asia  (baseline cell mean +769/wk, cell DD43 -41,186; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 +744)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| k_F60_B30 | 287/698 | +748 (-2.8%) | -71,231 (+4.3%) | -44,384 | -67,418 (+9.4%) | -67,418 (+9.4%) | -25,786 (-14.3%) | -636 / +868 | +722 | +209/-226/+75/-133 | ok 3/3 |
| k_F40_B40 | 234/698 | +747 (-2.9%) | -71,729 (+3.6%) | -44,924 | -68,765 (+7.6%) | -68,765 (+7.6%) | -24,092 (-6.8%) | -296 / +394 | +722 | +427/-563/+234/-177 | ok 2/2 |
| k_F60_B40 | 177/698 | +788 (+2.5%) | -71,397 (+4.0%) | -45,254 | -69,538 (+6.5%) | -69,538 (+6.5%) | -24,357 (-7.9%) | -79 / +533 | +762 | +309/-499/+220/+37 | ok 2/2 |
| h_VWP_HR | 145/698 | +738 (-4.1%) | -74,188 (+0.3%) | -44,153 | -74,188 (+0.3%) | -74,188 (+0.3%) | -22,433 (+0.6%) | -69 / +63 | +712 | +73/-58/-87/-40 | ok 1/2 |

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_ALL_AT | 432/698 | +491 (-36.2%) | -73,631 (+1.0%) | -43,732 | -62,784 (+15.6%) | -62,784 (+15.6%) | -25,393 (-12.5%) | -664 / +325 | +466 | +557/-926/-363/-268 | ok 1/1 |
| k_F60_B20 | 393/698 | +536 (-30.3%) | -71,433 (+4.0%) | -44,624 | -65,042 (+12.6%) | -65,042 (+12.6%) | -25,366 (-12.4%) | -1475 / +645 | +511 | +504/-559/-72/-712 | ok 1/2 |

### H7|nyam  (baseline cell mean +86/wk, cell DD43 -23,026; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 +79)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| k_F40_B40 | 115/358 | +16 (-81.7%) | -72,633 (+2.4%) | -42,713 | -72,633 (+2.4%) | -72,633 (+2.4%) | -22,565 (+0.0%) | +121 / +46 | +9 | -14/-167/-130/+58 | ok 2/2 |
| k_F50_B40 | 101/358 | +11 (-87.7%) | -72,743 (+2.2%) | -42,731 | -72,743 (+2.2%) | -72,743 (+2.2%) | -22,565 (+0.0%) | +111 / +5 | +4 | +14/-187/-142/+44 | ok 3/3 |

### K7|asia  (baseline cell mean +1249/wk, cell DD43 -26,763; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 +1195)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_ALL_M2 | 1563/2609 | +482 (-61.4%) | -71,645 (+3.7%) | -41,295 | -66,337 (+10.8%) | -66,337 (+10.8%) | -23,242 (-3.0%) | -1660 / -1240 | +427 | -126/-380/-793/-1462 | ok 2/2 |
| j_ES_L1_s00 | 1742/2609 | +328 (-73.7%) | -72,975 (+1.9%) | -40,264 | -65,505 (+12.0%) | -65,505 (+12.0%) | -25,993 (-15.2%) | -2059 / -1942 | +274 | +49/-575/-838/-1950 | ISOLATED 0/1 |

### K7|london  (baseline cell mean +442/wk, cell DD43 -26,299; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 +406)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| j_ES_L1_s00 | 1191/1820 | -40 (-109.2%) | -72,400 (+2.7%) | -43,368 | -72,400 (+2.7%) | -72,400 (+2.7%) | -20,453 (+9.4%) | +174 / -1084 | -77 | -274/-392/-747/-325 | ISOLATED 0/1 |
| j_any2_L1_s00 | 1172/1820 | -50 (-111.2%) | -72,695 (+2.3%) | -43,438 | -72,695 (+2.3%) | -72,695 (+2.3%) | -20,453 (+9.4%) | +238 / -1192 | -86 | -237/-491/-732/-309 | ISOLATED 0/1 |

### K7|nyam  (baseline cell mean +48/wk, cell DD43 -40,394; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 +18)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| k_F40_B40 | 467/1634 | +104 (+118.0%) | -72,138 (+3.0%) | -42,287 | -71,484 (+3.9%) | -71,484 (+3.9%) | -23,088 (-2.3%) | +329 / +362 | +75 | +69/+3/+36/+95 | ok 2/2 |
| k_F50_B20 | 893/1634 | +144 (+201.6%) | -72,168 (+3.0%) | -37,052 | -72,168 (+3.0%) | -72,168 (+3.0%) | -24,417 (-8.2%) | +402 / +233 | +115 | +194/+16/+91/+46 | ok 3/3 |
| k_F50_B40 | 415/1634 | +86 (+79.2%) | -72,197 (+3.0%) | -42,051 | -72,197 (+3.0%) | -72,197 (+3.0%) | -23,208 (-2.9%) | +323 / +368 | +56 | -22/+12/+52/+94 | ok 3/3 |
| k_F60_B40 | 371/1634 | +70 (+47.0%) | -72,293 (+2.8%) | -42,121 | -72,291 (+2.8%) | -72,291 (+2.8%) | -22,565 (+0.0%) | +319 / +302 | +41 | +6/-39/+18/+96 | ok 2/2 |
| h_ALL_HT20 | 1028/1634 | +65 (+34.8%) | -72,603 (+2.4%) | -38,083 | -72,603 (+2.4%) | -72,603 (+2.4%) | -24,030 (-6.5%) | -81 / +346 | +35 | -50/+10/+256/-157 | ok 2/2 |
| h_ALL_HT30 | 1028/1634 | +87 (+82.5%) | -72,697 (+2.3%) | -38,355 | -72,697 (+2.3%) | -72,697 (+2.3%) | -24,130 (-6.9%) | -21 / +455 | +58 | -75/-14/+307/-76 | ok 2/2 |

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_ALL_M2 | 1063/1634 | +3 (-93.7%) | -72,241 (+2.9%) | -37,052 | -70,717 (+5.0%) | -70,717 (+5.0%) | -24,800 (-9.9%) | -73 / +373 | -27 | -44/-202/+255/-170 | ok 2/2 |
| k_F40_B40 | 467/1634 | +104 (+118.0%) | -72,138 (+3.0%) | -42,287 | -71,484 (+3.9%) | -71,484 (+3.9%) | -23,088 (-2.3%) | +329 / +362 | +75 | +69/+3/+36/+95 | ok 2/2 |

### K7|nypm  (baseline cell mean +456/wk, cell DD43 -35,118; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 +431)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_NOR_HR | 674/1241 | +439 (-3.9%) | -73,448 (+1.3%) | -42,322 | -73,448 (+1.3%) | -73,448 (+1.3%) | -22,565 (+0.0%) | -277 / +35 | +413 | +78/-51/+30/-122 | ok 2/2 |

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_NOR_HT15 | 674/1241 | +415 (-9.0%) | -72,783 (+2.2%) | -41,243 | -72,312 (+2.8%) | -72,312 (+2.8%) | -22,565 (+0.0%) | -522 / +33 | +390 | +141/-116/+65/-239 | ok 1/1 |
| h_NOR_AT | 674/1241 | +421 (-7.8%) | -72,820 (+2.1%) | -41,116 | -72,495 (+2.6%) | -72,495 (+2.6%) | -22,565 (+0.0%) | -554 / +71 | +395 | +157/-101/+60/-244 | ok 1/1 |

### M7|london  (baseline cell mean -357/wk, cell DD43 -109,235; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 -409)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_NOR_HT15 | 1195/2420 | -82 (+76.9%) | -73,342 (+1.4%) | -41,821 | -73,342 (+1.4%) | -73,342 (+1.4%) | -22,687 (-0.5%) | -32 / -313 | -134 | -24/+503/+524/-16 | ok 1/1 |
| h_NOR_HT20 | 1195/2420 | -111 (+68.9%) | -73,484 (+1.2%) | -41,926 | -73,484 (+1.2%) | -73,484 (+1.2%) | -22,467 (+0.4%) | -101 / -234 | -163 | -49/+445/+501/-12 | ok 1/2 |
| h_NOR_M2 | 1245/2420 | -128 (+64.0%) | -73,663 (+1.0%) | -42,603 | -73,663 (+1.0%) | -73,663 (+1.0%) | -22,937 (-1.6%) | -100 / -280 | -180 | -42/+376/+557/-69 | ok 2/2 |
| h_ALL_HT15 | 1452/2420 | -104 (+70.8%) | -73,889 (+0.7%) | -40,927 | -73,889 (+0.7%) | -73,889 (+0.7%) | -21,393 (+5.2%) | +105 / +116 | -156 | -207/+361/+453/+303 | ok 1/1 |
| h_ALL_HT20 | 1452/2420 | -120 (+66.4%) | -74,032 (+0.5%) | -41,082 | -74,032 (+0.5%) | -74,032 (+0.5%) | -21,575 (+4.4%) | +73 / +218 | -172 | -226/+305/+442/+331 | ok 1/2 |
| h_NOR_AT | 1195/2420 | -138 (+61.3%) | -74,310 (+0.1%) | -42,163 | -74,310 (+0.1%) | -74,310 (+0.1%) | -22,577 (-0.1%) | -203 / -391 | -190 | -77/+532/+459/-126 | ok 1/1 |

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| j_RTY_L1_s00 | 1554/2420 | -522 (-46.2%) | -72,224 (+2.9%) | -42,069 | -69,849 (+6.1%) | -69,849 (+6.1%) | -20,684 (+8.3%) | +108 / -364 | -573 | -580/-244/+56/+175 | ISOLATED 0/1 |
| j_ES_L1_s00 | 1515/2420 | -545 (-52.6%) | -71,851 (+3.4%) | -41,654 | -71,088 (+4.5%) | -71,088 (+4.5%) | -20,924 (+7.3%) | -42 / -428 | -596 | -584/-182/+21/+69 | ISOLATED 0/1 |

### M7|nyam  (baseline cell mean +337/wk, cell DD43 -21,245; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 +309)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_VWP_M2 | 476/1550 | +211 (-37.4%) | -70,746 (+4.9%) | -42,125 | -68,732 (+7.6%) | -68,732 (+7.6%) | -23,121 (-2.5%) | -280 / +152 | +183 | -200/-116/+124/-261 | ok 2/2 |
| h_VWP_AT | 465/1550 | +239 (-28.9%) | -71,060 (+4.5%) | -42,085 | -70,064 (+5.8%) | -70,064 (+5.8%) | -23,081 (-2.3%) | -285 / +197 | +211 | -175/-82/+136/-231 | ok 1/1 |

### O7|nyam  (baseline cell mean +472/wk, cell DD43 -14,950; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 +464)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_VWP_HR | 220/465 | +361 (-23.7%) | -74,756 (-0.5%) | -43,563 | -74,727 (-0.4%) | -74,727 (-0.4%) | -22,565 (+0.0%) | -74 / -255 | +352 | +94/-230/-173/-94 | ISOLATED 0/2 |
| h_NOR_HR | 283/465 | +299 (-36.7%) | -75,281 (-1.2%) | -43,715 | -75,281 (-1.2%) | -75,281 (-1.2%) | -22,565 (+0.0%) | -138 / -392 | +291 | +48/-335/-170/-167 | ISOLATED 0/2 |

### P7|asia  (baseline cell mean +2962/wk, cell DD43 -63,819; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 +2870)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| k_F50_B40 | 530/1969 | +2850 (-3.8%) | -85,510 (-14.9%) | -40,491 | -78,585 (-5.6%) | -78,585 (-5.6%) | -24,982 (-10.7%) | -654 / -1291 | +2758 | +233/+133/-336/-433 | ISOLATED 0/3 |
| k_F40_B40 | 599/1969 | +2898 (-2.1%) | -87,564 (-17.7%) | -39,936 | -77,331 (-3.9%) | -77,331 (-3.9%) | -23,980 (-6.3%) | -1103 / -984 | +2806 | +302/+116/-120/-527 | ISOLATED 0/2 |

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_R50_M2 | 987/1969 | +2103 (-29.0%) | -75,252 (-1.1%) | -38,583 | -70,737 (+4.9%) | -70,737 (+4.9%) | -28,866 (-27.9%) | -2496 / -1612 | +2011 | -218/+182/-1369/-1686 | ISOLATED 0/2 |
| h_ALL_HR | 1205/1969 | +2221 (-25.0%) | -74,693 (-0.4%) | -39,796 | -74,693 (-0.4%) | -74,693 (-0.4%) | -22,560 (+0.0%) | -1710 / -1208 | +2129 | -164/-222/-1234/-1048 | ISOLATED 0/2 |

### P7|london  (baseline cell mean +117/wk, cell DD43 -86,599; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 +81)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_NOR_HR | 776/1494 | +122 (+4.1%) | -77,221 (-3.8%) | -42,532 | -77,221 (-3.8%) | -77,221 (-3.8%) | -23,008 (-2.0%) | -148 / -241 | +86 | +67/-79/+184/-154 | ISOLATED 0/2 |
| h_R50_HR | 625/1494 | +114 (-2.6%) | -77,558 (-4.2%) | -41,599 | -77,558 (-4.2%) | -77,558 (-4.2%) | -23,029 (-2.1%) | -222 / +114 | +78 | -71/-41/+116/-15 | ISOLATED 0/2 |
| h_NOR_HT15 | 776/1494 | +116 (-0.5%) | -78,397 (-5.4%) | -41,356 | -78,397 (-5.4%) | -78,397 (-5.4%) | -22,949 (-1.7%) | -342 / -422 | +81 | +134/-178/+386/-344 | ISOLATED 0/1 |
| h_NOR_HT30 | 776/1494 | +123 (+5.7%) | -79,007 (-6.2%) | -41,986 | -79,007 (-6.2%) | -79,007 (-6.2%) | -23,389 (-3.7%) | -292 / -270 | +88 | +108/-210/+353/-228 | ISOLATED 0/2 |
| h_NOR_HT20 | 776/1494 | +141 (+20.8%) | -79,137 (-6.4%) | -41,386 | -79,137 (-6.4%) | -79,137 (-6.4%) | -23,052 (-2.2%) | -72 / -348 | +106 | +115/-219/+350/-158 | ISOLATED 0/2 |
| h_R50_HT15 | 625/1494 | +134 (+15.1%) | -79,687 (-7.1%) | -40,221 | -79,687 (-7.1%) | -79,687 (-7.1%) | -23,434 (-3.9%) | -264 / +273 | +99 | -114/-129/+238/+69 | ISOLATED 0/1 |

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| j_NKD_L1_s00 | 832/1494 | -154 (-231.8%) | -73,913 (+0.7%) | -41,653 | -73,913 (+0.7%) | -73,913 (+0.7%) | -22,686 (-0.5%) | -1082 / -60 | -189 | -260/-522/+395/-586 | ISOLATED 0/1 |
| j_NKD_L1_s05 | 800/1494 | -160 (-236.6%) | -75,380 (-1.3%) | -41,653 | -73,007 (+1.9%) | -73,007 (+1.9%) | -22,871 (-1.4%) | -922 / +32 | -195 | -286/-516/+283/-475 | ISOLATED 0/1 |

### P7|nyam  (baseline cell mean +93/wk, cell DD43 -21,407; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 +88)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_R50_M2 | 104/241 | +19 (-79.8%) | -73,618 (+1.1%) | -44,182 | -71,402 (+4.0%) | -71,402 (+4.0%) | -22,565 (+0.0%) | -122 / -40 | +14 | -151/-85/+112/-143 | ok 2/2 |
| k_F40_B30 | 95/241 | -8 (-108.3%) | -73,618 (+1.1%) | -44,333 | -72,453 (+2.6%) | -72,453 (+2.6%) | -22,565 (+0.0%) | -144 / -78 | -12 | -111/-60/-8/-182 | ok 3/3 |

### U7|asia  (baseline cell mean +1145/wk, cell DD43 -30,643; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 +1114)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_VWP_HT20 | 143/686 | +1103 (-3.7%) | -75,677 (-1.7%) | -43,527 | -75,677 (-1.7%) | -75,677 (-1.7%) | -26,374 (-16.9%) | -586 / -356 | +1072 | +210/+448/-400/-409 | ISOLATED 0/2 |
| h_VWP_HT30 | 143/686 | +1132 (-1.1%) | -75,677 (-1.7%) | -43,527 | -75,677 (-1.7%) | -75,677 (-1.7%) | -26,615 (-17.9%) | -410 / -312 | +1101 | +196/+418/-367/-295 | ISOLATED 0/2 |
| h_VWP_HR | 143/686 | +1109 (-3.2%) | -75,677 (-1.7%) | -43,527 | -75,677 (-1.7%) | -75,677 (-1.7%) | -24,767 (-9.8%) | -355 / -166 | +1078 | +118/+232/-259/-220 | ISOLATED 0/2 |

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_NOR_HT15 | 216/686 | +1027 (-10.3%) | -69,322 (+6.8%) | -43,527 | -68,622 (+7.8%) | -68,622 (+7.8%) | -32,687 (-44.9%) | -620 / -55 | +996 | +149/+243/-422/-396 | ok 1/1 |
| h_NOR_HT20 | 216/686 | +1038 (-9.3%) | -69,522 (+6.6%) | -43,527 | -68,822 (+7.5%) | -68,822 (+7.5%) | -30,902 (-36.9%) | -460 / -192 | +1008 | +116/+242/-364/-377 | ok 2/2 |

### U7|london  (baseline cell mean +267/wk, cell DD43 -32,127; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 +244)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_VWP_HT30 | 114/638 | +397 (+48.8%) | -76,066 (-2.2%) | -43,527 | -74,281 (+0.2%) | -74,281 (+0.2%) | -24,491 (-8.5%) | -272 / +277 | +374 | -158/+183/+415/+28 | ok 1/2 |
| h_VWP_M2 | 119/638 | +353 (+32.2%) | -75,817 (-1.9%) | -43,527 | -74,639 (-0.3%) | -74,639 (-0.3%) | -25,789 (-14.3%) | -486 / +341 | +330 | -126/+90/+457/-111 | ok 1/2 |
| k_F60_B30 | 256/638 | +281 (+5.4%) | -74,551 (-0.2%) | -45,785 | -63,954 (+14.0%) | -63,954 (+14.0%) | -26,219 (-16.2%) | -418 / +132 | +258 | -52/+170/+192/-259 | ISOLATED 0/3 |
| k_F40_B40 | 212/638 | +345 (+29.1%) | -75,523 (-1.5%) | -47,238 | -72,129 (+3.1%) | -72,129 (+3.1%) | -25,259 (-11.9%) | -97 / -50 | +321 | +20/+126/+200/-66 | ISOLATED 0/2 |
| k_F50_B40 | 184/638 | +367 (+37.4%) | -75,073 (-0.9%) | -47,903 | -72,771 (+2.2%) | -72,771 (+2.2%) | -25,669 (-13.8%) | +64 / -240 | +343 | +34/+90/+283/-48 | ISOLATED 0/3 |
| k_F60_B40 | 163/638 | +379 (+42.0%) | -76,048 (-2.2%) | -48,633 | -72,468 (+2.6%) | -72,468 (+2.6%) | -25,989 (-15.2%) | +113 / -134 | +356 | +41/+121/+213/+28 | ISOLATED 0/2 |

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_NOR_HT30 | 382/638 | -15 (-105.7%) | -73,549 (+1.1%) | -46,647 | -64,571 (+13.2%) | -64,571 (+13.2%) | -25,945 (-15.0%) | -895 / +212 | -39 | -627/-145/+281/-524 | ok 2/2 |
| k_F60_B30 | 256/638 | +281 (+5.4%) | -74,551 (-0.2%) | -45,785 | -63,954 (+14.0%) | -63,954 (+14.0%) | -26,219 (-16.2%) | -418 / +132 | +258 | -52/+170/+192/-259 | ISOLATED 0/3 |

### A7  (baseline cell mean +710/wk, cell DD43 -13,724; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 +689)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_NOR_HT15 | 282/1156 | +678 (-4.5%) | -71,311 (+4.2%) | -43,527 | -69,479 (+6.6%) | -69,479 (+6.6%) | -24,326 (-7.8%) | +476 / -250 | +658 | +28/-89/-94/+40 | ok 1/1 |
| h_NOR_HT20 | 282/1156 | +678 (-4.6%) | -71,461 (+4.0%) | -43,527 | -69,624 (+6.4%) | -69,624 (+6.4%) | -23,991 (-6.3%) | +477 / -277 | +657 | +39/-94/-94/+33 | ok 2/2 |
| h_NOR_HR | 282/1156 | +690 (-2.9%) | -72,508 (+2.5%) | -43,527 | -71,914 (+3.3%) | -71,914 (+3.3%) | -23,361 (-3.5%) | +225 / -134 | +669 | +21/-45/-63/+15 | ok 2/2 |
| h_VWP_HR | 168/1156 | +681 (-4.1%) | -73,622 (+1.0%) | -43,527 | -73,622 (+1.0%) | -73,622 (+1.0%) | -23,293 (-3.2%) | -28 / -20 | +660 | +26/-60/-29/-42 | ok 2/2 |

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_NOR_HT15 | 282/1156 | +678 (-4.5%) | -71,311 (+4.2%) | -43,527 | -69,479 (+6.6%) | -69,479 (+6.6%) | -24,326 (-7.8%) | +476 / -250 | +658 | +28/-89/-94/+40 | ok 1/1 |
| h_NOR_AT | 282/1156 | +670 (-5.7%) | -71,399 (+4.0%) | -43,527 | -69,427 (+6.7%) | -69,427 (+6.7%) | -24,213 (-7.3%) | +450 / -267 | +649 | +41/-91/-126/+29 | ok 1/1 |

### H7  (baseline cell mean +855/wk, cell DD43 -46,603; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 +823)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| k_F60_B40 | 263/1056 | +817 (-4.4%) | -72,855 (+2.1%) | -44,515 | -67,969 (+8.6%) | -67,969 (+8.6%) | -24,357 (-7.9%) | +15 / +580 | +786 | +316/-605/+89/+65 | ok 2/2 |

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| k_F60_B20 | 603/1056 | +502 (-41.3%) | -72,498 (+2.6%) | -43,885 | -63,658 (+14.4%) | -63,658 (+14.4%) | -26,316 (-16.6%) | -1726 / +704 | +470 | +486/-715/-154/-888 | ok 1/2 |
| k_F40_B20 | 683/1056 | +475 (-44.5%) | -73,842 (+0.8%) | -43,640 | -63,603 (+14.5%) | -63,603 (+14.5%) | -25,769 (-14.2%) | -1448 / +607 | +443 | +607/-950/-274/-750 | ISOLATED 0/2 |

### K7  (baseline cell mean +2196/wk, cell DD43 -47,076; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 +2050)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| j_ES_L1_s00 | 4739/7304 | +464 (-78.9%) | -69,520 (+6.6%) | -33,912 | -61,724 (+17.0%) | -64,332 (+13.5%) | -21,925 (+2.8%) | -1942 / -2911 | +318 | -83/-1803/-1906/-2440 | ok 1/1 |
| j_any2_L1_s00 | 4676/7304 | +438 (-80.0%) | -69,257 (+6.9%) | -35,261 | -64,516 (+13.3%) | -64,516 (+13.3%) | -20,013 (+11.3%) | -1907 / -3240 | +293 | -12/-1973/-1857/-2482 | ok 1/1 |

### M7  (baseline cell mean -20/wk, cell DD43 -63,866; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 -100)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_NOR_HT20 | 2013/3970 | +52 (+360.4%) | -70,891 (+4.7%) | -38,796 | -70,765 (+4.9%) | -70,765 (+4.9%) | -22,086 (+2.1%) | -483 / +60 | -28 | -283/+188/+718/-364 | ok 2/2 |
| h_NOR_HT15 | 2013/3970 | +92 (+561.6%) | -71,554 (+3.8%) | -38,541 | -70,392 (+5.4%) | -70,392 (+5.4%) | -22,461 (+0.5%) | -418 / -18 | +12 | -215/+239/+745/-365 | ok 1/1 |
| h_NOR_AT | 2013/3970 | +18 (+189.7%) | -71,331 (+4.1%) | -38,653 | -71,331 (+4.1%) | -71,331 (+4.1%) | -22,197 (+1.6%) | -716 / -106 | -62 | -353/+284/+740/-534 | ok 1/1 |
| h_NOR_M2 | 2092/3970 | +30 (+247.7%) | -72,587 (+2.4%) | -37,802 | -71,244 (+4.2%) | -71,244 (+4.2%) | -22,717 (-0.7%) | -693 / -137 | -50 | -255/+195/+821/-583 | ok 2/2 |
| h_VWP_HT30 | 1070/3970 | -15 (+23.2%) | -72,451 (+2.6%) | -39,974 | -72,451 (+2.6%) | -72,451 (+2.6%) | -22,079 (+2.2%) | -385 / -601 | -95 | +96/+155/+247/-482 | ok 2/2 |
| h_NOR_HR | 2013/3970 | -1 (+94.9%) | -72,866 (+2.1%) | -41,090 | -72,866 (+2.1%) | -72,866 (+2.1%) | -22,062 (+2.2%) | -358 / -53 | -81 | -177/+142/+370/-267 | ok 2/2 |

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| k_F60_B20 | 2077/3970 | -342 (-1610.2%) | -70,462 (+5.3%) | -36,612 | -70,462 (+5.3%) | -70,462 (+5.3%) | -22,904 (-1.5%) | -350 / -86 | -422 | -573/-589/+275/-272 | ok 1/2 |
| h_NOR_HT20 | 2013/3970 | +52 (+360.4%) | -70,891 (+4.7%) | -38,796 | -70,765 (+4.9%) | -70,765 (+4.9%) | -22,086 (+2.1%) | -483 / +60 | -28 | -283/+188/+718/-364 | ok 2/2 |

### O7  (baseline cell mean +472/wk, cell DD43 -14,950; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 +464)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_VWP_HR | 220/465 | +361 (-23.7%) | -74,756 (-0.5%) | -43,563 | -74,727 (-0.4%) | -74,727 (-0.4%) | -22,565 (+0.0%) | -74 / -255 | +352 | +94/-230/-173/-94 | ISOLATED 0/2 |
| h_NOR_HR | 283/465 | +299 (-36.7%) | -75,281 (-1.2%) | -43,715 | -75,281 (-1.2%) | -75,281 (-1.2%) | -22,565 (+0.0%) | -138 / -392 | +291 | +48/-335/-170/-167 | ISOLATED 0/2 |

### P7  (baseline cell mean +3171/wk, cell DD43 -43,061; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 +3039)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| j_NKD_L1_s05 | 2141/3704 | +961 (-69.7%) | -73,337 (+1.4%) | -37,780 | -70,564 (+5.2%) | -70,564 (+5.2%) | -28,903 (-28.1%) | -5917 / -3382 | +829 | -541/-1632/-1642/-4142 | ok 1/1 |
| j_ES_L5_s00 | 2161/3704 | +527 (-83.4%) | -73,634 (+1.0%) | -36,734 | -73,634 (+1.0%) | -73,634 (+1.0%) | -26,430 (-17.1%) | -6286 / -5598 | +395 | -762/-1574/-2217/-4963 | ISOLATED 0/1 |

### U7  (baseline cell mean +1412/wk, cell DD43 -43,794; whole-stack DD43 -74,402, worst wk -43,527, HP DD -74,402, HOLD DD -74,402, L6M DD -22,565; ref @4.84 +1358)

Mean gate passed, ranked non-isolated first then DD43+HP cut (top 6):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_VWP_HT30 | 257/1324 | +1529 (+8.3%) | -75,555 (-1.6%) | -43,527 | -75,555 (-1.6%) | -75,555 (-1.6%) | -28,597 (-26.7%) | -682 / -35 | +1475 | +38/+601/+49/-266 | ISOLATED 0/2 |
| h_VWP_HR | 257/1324 | +1430 (+1.3%) | -75,655 (-1.7%) | -43,527 | -75,655 (-1.7%) | -75,655 (-1.7%) | -26,307 (-16.6%) | -546 / -38 | +1376 | +60/+299/-47/-246 | ISOLATED 0/2 |
| h_VWP_HT20 | 257/1324 | +1468 (+4.0%) | -75,920 (-2.0%) | -43,527 | -75,920 (-2.0%) | -75,920 (-2.0%) | -29,767 (-31.9%) | -969 / -232 | +1414 | +65/+611/+42/-516 | ISOLATED 0/2 |
| h_VWP_HT15 | 257/1324 | +1465 (+3.8%) | -76,050 (-2.2%) | -43,527 | -76,050 (-2.2%) | -76,050 (-2.2%) | -31,117 (-37.9%) | -1054 / -165 | +1411 | +60/+655/+3/-526 | ISOLATED 0/1 |
| h_VWP_AT | 257/1324 | +1449 (+2.6%) | -76,909 (-3.4%) | -43,527 | -76,909 (-3.4%) | -76,909 (-3.4%) | -31,559 (-39.9%) | -1092 / -75 | +1395 | +121/+599/-95/-493 | ISOLATED 0/1 |
| h_VWP_M2 | 263/1324 | +1367 (-3.1%) | -77,349 (-4.0%) | -43,527 | -77,349 (-4.0%) | -77,349 (-4.0%) | -32,316 (-43.2%) | -1276 / -81 | +1313 | +97/+502/-127/-632 | ISOLATED 0/2 |

Best by DD ignoring the gate (top 2, for the record):

| rule | alt/n | cell mean $/wk (d%) | whole-stack DD43 (cut%) | worst wk | HP DD (cut%) | HOLD DD (cut%) | L6M DD (cut%) | d$/wk L6M / HOLD | cell mean @4.84 | d$/wk by yr 23/24/25/26 | surface |
|--|--|--|--|--|--|--|--|--|--|--|--|
| h_NOR_HT15 | 598/1324 | +988 (-30.0%) | -70,103 (+5.8%) | -45,537 | -58,795 (+21.0%) | -58,795 (+21.0%) | -35,815 (-58.7%) | -1780 / +26 | +934 | -340/-9/-44/-1132 | ok 1/1 |
| h_NOR_HT20 | 598/1324 | +970 (-31.3%) | -70,297 (+5.5%) | -45,847 | -58,870 (+20.9%) | -58,870 (+20.9%) | -34,625 (-53.4%) | -1597 / -77 | +916 | -402/-83/-22/-1082 | ok 2/2 |

