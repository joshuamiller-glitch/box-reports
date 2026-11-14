# DS3_SURVIVORS_J - JN05W2 (W-J; 2026-11-14T19:26:52Z; Shadow only, no PASS claims)

JN05W2 = live panel base (installed panel + P7 cut, NO JN04 layers, NO WA_C1) + F3 (WB_X_FR_F3 context cut) + E1 (WG_E1 governor) + C22 (S6 stack count and day P&L <= -2R) + BR3S (breadth_ext15 == 3 skip, P7) + FLAT45K (K7 flat -45). Hook order inner to outer: W-B context cut, W-X flat, W-S stack gate, W-C governor; BR3S through the entry-gate mixin. Reference LPB_BASE (exact, 43 months). JN05W2J = the same five on the JN04RM base (extra). Leave-one-out = one set per layer left out.

## Months done per set

| set | months DONE of 43 |
|--|--|
| JN05W2 | 43 |
| JN05W2_nF3 | 43 |
| JN05W2_nE1 | 43 |
| JN05W2_nC22 | 43 |
| JN05W2_nBR3S | 43 |
| JN05W2_nFLAT | 43 |
| JN05W2J | 43 |

## 1. Identity check (before anything)

JN05W2_ID (the same hook stack with every layer null) is identical trade by trade to LPB_EMPTY and to the stored LPB_BASE in 202610 (769 trades, net 12,236.22).

## 2. Trend-week clause (first): weekly P&L, L6M, vs LPB_BASE

# Weekly check, L6M (ISO weeks with trading days in 2026-05..10; weeks at the month edges are partial; exact engine; Shadow only)

| week | LPB_BASE | JN04RM | JN05W2 | JN05W2_nF3 | JN05W2_nE1 | JN05W2_nC22 | JN05W2_nBR3S | JN05W2_nFLAT | JN05W2J |
|--|--|--|--|--|--|--|--|--|--|
| 202638 (best of LPB_BASE) | 88836 | 72104 | 58311 | 48462 | 56397 | 61353 | 41334 | 65293 | 58011 |
| 202623 (best of LPB_BASE) | 73836 | 68072 | 52723 | 54578 | 50759 | 44642 | 61777 | 48394 | 41676 |
| 202625 (best of LPB_BASE) | 59099 | 59990 | 37787 | 47175 | 42925 | 36492 | 31806 | 44579 | 40510 |
| 202639 (best of LPB_BASE) | 57178 | 52634 | 51123 | 50967 | 49241 | 51123 | 47321 | 64789 | 39815 |
| 202633 (best of LPB_BASE) | 52499 | 36328 | 55600 | 55699 | 54176 | 55600 | 40395 | 47733 | 37387 |
| 202644 (worst of LPB_BASE) | -51253 | -16664 | -36371 | -42856 | -24205 | -41464 | -19086 | -36147 | -14035 |
| 202636 (worst of LPB_BASE) | -44984 | -25704 | -26026 | -28172 | -26026 | -42352 | -14530 | -41893 | -12417 |
| 202621 (worst of LPB_BASE) | -39976 | -39092 | -25313 | -45928 | -24194 | -31507 | -29457 | -25880 | -23965 |
| 202635 (worst of LPB_BASE) | -23667 | -15995 | 14756 | 17448 | 13437 | 6693 | -9821 | 13927 | 9907 |
| 202637 (worst of LPB_BASE) | -8573 | 679 | -4508 | -19297 | -4508 | -4672 | -1502 | 3786 | -970 |

JN04RM: LPB_BASE winning weeks 20 of 27; of those, JN04RM turn losing: 1; weeks where JN04RM beats LPB_BASE: 13 of 27; sum over the 5 best LPB_BASE weeks 289128 vs 331449

JN05W2: LPB_BASE winning weeks 20 of 27; of those, JN05W2 turn losing: 2; weeks where JN05W2 beats LPB_BASE: 16 of 27; sum over the 5 best LPB_BASE weeks 255545 vs 331449

JN05W2_nF3: LPB_BASE winning weeks 20 of 27; of those, JN05W2_nF3 turn losing: 3; weeks where JN05W2_nF3 beats LPB_BASE: 16 of 27; sum over the 5 best LPB_BASE weeks 256881 vs 331449

JN05W2_nE1: LPB_BASE winning weeks 20 of 27; of those, JN05W2_nE1 turn losing: 1; weeks where JN05W2_nE1 beats LPB_BASE: 16 of 27; sum over the 5 best LPB_BASE weeks 253498 vs 331449

JN05W2_nC22: LPB_BASE winning weeks 20 of 27; of those, JN05W2_nC22 turn losing: 2; weeks where JN05W2_nC22 beats LPB_BASE: 15 of 27; sum over the 5 best LPB_BASE weeks 249210 vs 331449

JN05W2_nBR3S: LPB_BASE winning weeks 20 of 27; of those, JN05W2_nBR3S turn losing: 0; weeks where JN05W2_nBR3S beats LPB_BASE: 15 of 27; sum over the 5 best LPB_BASE weeks 222632 vs 331449

JN05W2_nFLAT: LPB_BASE winning weeks 20 of 27; of those, JN05W2_nFLAT turn losing: 1; weeks where JN05W2_nFLAT beats LPB_BASE: 15 of 27; sum over the 5 best LPB_BASE weeks 270789 vs 331449

JN05W2J: LPB_BASE winning weeks 20 of 27; of those, JN05W2J turn losing: 1; weeks where JN05W2J beats LPB_BASE: 15 of 27; sum over the 5 best LPB_BASE weeks 217399 vs 331449

# Frozen week 11-02..05 exact re-simulation (month 202611; state days 20261102-05)

NOT POSSIBLE on this box: the exact engine needs the hist day files (_hist_replica/days) built from raw mbp-10, and the latest raw NQ file is 2026-10-31 (GLBX-20261031); only the 1-s state arrays for 11-02..05 exist. FW_LPB 202611 failed with: no day files in range. Needed: raw mbp-10 for 2026-11-02..05 into /mnt/l2/l2vast/raw/NQ/ext/ then the hist_pipe day build. Sets FW_LPB, FW_JN04RM, JN05W_E1_FW, JN05W_E1A_FW and jnr_cfg_nov.json (Nov dA threshold) are ready and run with chain_jn05.sh SET 202611. Until then the trend-week cost evidence is the L6M weekly table above (the 5 best LPB_BASE weeks).
## 3. Windows (exact; each row vs LPB_BASE; mean columns all-weeks and carry-dropped; only windows with all months present are shown)

| cell | window | mean $/wk all-weeks | LPB_BASE all-weeks | d mean all-weeks | mean (carry week dropped) | mean_ref (carry dropped) | maxDD | maxDD_ref | cut % | d mean | WF beat % | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| JN05W2 | L1M | 606 | 341 | +266 | -7190 | -16180 | 36371 | 51253 | +29.0 | +8990 | 44 |  |
| JN05W2 | L3M | 16015 | 11957 | +4059 | 16120 | 14925 | 36371 | 77224 | +52.9 | +1195 | 44 |  |
| JN05W2 | L6M | 25137 | 18697 | +6440 | 23269 | 18660 | 36371 | 77224 | +52.9 | +4608 | 44 | OK-PRIOR (allow 15.0%, WF 44%) |
| JN05W2 | HOLD | 17489 | 15236 | +2253 | 16424 | 15151 | 63185 | 78842 | +19.9 | +1273 | 44 |  |
| JN05W2 | PRE | 10168 | 11685 | -1518 | 10423 | 12592 | 76186 | 99479 | +23.4 | -2169 | 44 |  |
| JN05W2 | X' | 3585 | 1334 | +2251 | 4172 | 2553 | 55326 | 122553 | +54.9 | +1620 | 44 |  |
| JN05W2_nF3 | L1M | -1519 | 341 | -1859 | -7314 | -16180 | 42856 | 51253 | +16.4 | +8866 | 39 |  |
| JN05W2_nF3 | L3M | 15963 | 11957 | +4006 | 15839 | 14925 | 47469 | 77224 | +38.5 | +914 | 39 |  |
| JN05W2_nF3 | L6M | 21216 | 18697 | +2519 | 19536 | 18660 | 47469 | 77224 | +38.5 | +876 | 39 | OK-PRIOR (allow 15.0%, WF 39%) |
| JN05W2_nF3 | HOLD | 18237 | 15236 | +3000 | 17355 | 15151 | 56965 | 78842 | +27.7 | +2204 | 39 |  |
| JN05W2_nF3 | PRE | 11578 | 11685 | -107 | 11873 | 12592 | 85185 | 99479 | +14.4 | -719 | 39 |  |
| JN05W2_nF3 | X' | 2205 | 1334 | +872 | 2969 | 2553 | 86520 | 122553 | +29.4 | +416 | 39 |  |
| JN05W2_nE1 | L1M | 3254 | 341 | +2913 | 12406 | 17539 | 24205 | 51253 | +52.8 | -5132 | 37 |  |
| JN05W2_nE1 | L3M | 16476 | 11957 | +4520 | 16730 | 14925 | 30533 | 77224 | +60.5 | +1804 | 37 |  |
| JN05W2_nE1 | L6M | 24904 | 18697 | +6207 | 23012 | 18660 | 30533 | 77224 | +60.5 | +4352 | 37 | OK-PRIOR (allow 15.0%, WF 37%) |
| JN05W2_nE1 | HOLD | 17521 | 15236 | +2285 | 16449 | 15151 | 61283 | 78842 | +22.3 | +1299 | 37 |  |
| JN05W2_nE1 | PRE | 10762 | 11685 | -924 | 10312 | 11867 | 71392 | 99479 | +28.2 | -1555 | 37 |  |
| JN05W2_nE1 | X' | 3475 | 1334 | +2141 | 4059 | 2553 | 55326 | 122553 | +54.9 | +1507 | 37 |  |
| JN05W2_nC22 | L1M | 3170 | 341 | +2829 | 18048 | 17539 | 42163 | 51253 | +17.7 | +509 | 42 |  |
| JN05W2_nC22 | L3M | 11972 | 11957 | +15 | 12412 | 14925 | 47024 | 77224 | +39.1 | -2513 | 42 |  |
| JN05W2_nC22 | L6M | 22171 | 18697 | +3474 | 20034 | 17838 | 47024 | 77224 | +39.1 | +2196 | 42 | OK-PRIOR (allow 15.0%, WF 42%) |
| JN05W2_nC22 | HOLD | 15730 | 15236 | +494 | 16256 | 14869 | 63870 | 78842 | +19.0 | +1387 | 42 |  |
| JN05W2_nC22 | PRE | 10013 | 11685 | -1673 | 10192 | 12592 | 91066 | 99479 | +8.5 | -2401 | 42 |  |
| JN05W2_nC22 | X' | 3523 | 1334 | +2189 | 4108 | 2553 | 55326 | 122553 | +54.9 | +1556 | 42 |  |
| JN05W2_nBR3S | L1M | 8071 | 341 | +7730 | 17123 | 17539 | 19086 | 51253 | +62.8 | -416 | 46 |  |
| JN05W2_nBR3S | L3M | 14325 | 11957 | +2369 | 12075 | 5550 | 25852 | 77224 | +66.5 | +6525 | 46 |  |
| JN05W2_nBR3S | L6M | 21240 | 18697 | +2543 | 19280 | 18660 | 29457 | 77224 | +61.9 | +619 | 46 | OK-PRIOR (allow 15.0%, WF 46%) |
| JN05W2_nBR3S | HOLD | 15832 | 15236 | +595 | 14764 | 15151 | 73126 | 78842 | +7.2 | -386 | 46 |  |
| JN05W2_nBR3S | PRE | 10834 | 11685 | -851 | 11078 | 12592 | 80282 | 99479 | +19.3 | -1515 | 46 |  |
| JN05W2_nBR3S | X' | 1607 | 1334 | +273 | 2075 | 1387 | 88124 | 122553 | +28.1 | +688 | 46 |  |
| JN05W2_nFLAT | L1M | 157 | 341 | -183 | -6990 | -16180 | 36147 | 51253 | +29.5 | +9190 | 57 |  |
| JN05W2_nFLAT | L3M | 15858 | 11957 | +3901 | 16018 | 14925 | 41893 | 77224 | +45.8 | +1093 | 57 |  |
| JN05W2_nFLAT | L6M | 23665 | 18697 | +4968 | 22029 | 18660 | 41893 | 77224 | +45.8 | +3369 | 57 | OK-PRIOR (allow 15.0%, WF 57%) |
| JN05W2_nFLAT | HOLD | 16662 | 15236 | +1426 | 15723 | 15151 | 64649 | 78842 | +18.0 | +573 | 57 |  |
| JN05W2_nFLAT | PRE | 11810 | 11685 | +124 | 11345 | 11867 | 68600 | 99479 | +31.0 | -522 | 57 |  |
| JN05W2_nFLAT | X' | 3027 | 1334 | +1693 | 3129 | 1886 | 51696 | 122553 | +57.8 | +1243 | 57 |  |
| JN05W2J | L1M | 2631 | 341 | +2290 | 8186 | 17539 | 17862 | 51253 | +65.1 | -9352 | 85 |  |
| JN05W2J | L3M | 14942 | 11957 | +2985 | 17356 | 17224 | 17862 | 77224 | +76.9 | +132 | 85 |  |
| JN05W2J | L6M | 20865 | 18697 | +2168 | 22261 | 21495 | 23965 | 77224 | +69.0 | +766 | 85 | RECENT-ONLY (allow 25.0%, WF 85%) |
| JN05W2J | HOLD | 14405 | 15236 | -831 | 14628 | 14684 | 43622 | 78842 | +44.7 | -56 | 85 |  |
| JN05W2J | PRE | 7254 | 11685 | -4431 | 6903 | 10548 | 56843 | 99479 | +42.9 | -3646 | 85 |  |
| JN05W2J | X' | 3798 | 1334 | +2464 | 4055 | 2553 | 39577 | 122553 | +67.7 | +1502 | 85 |  |

## 4. Acceptance

| set | acceptance (W-C acceptance_p7) |
|--|--|
| JN05W2 | ACCEPT JN05W2 PASS fails=1/20 |
| JN05W2_nF3 | ACCEPT JN05W2_nF3 PASS fails=1/20 |
| JN05W2_nE1 | ACCEPT JN05W2_nE1 FAIL fails=4/20 |
| JN05W2_nC22 | ACCEPT JN05W2_nC22 PASS fails=1/20 |
| JN05W2_nBR3S | ACCEPT JN05W2_nBR3S PASS fails=1/20 |
| JN05W2_nFLAT | ACCEPT JN05W2_nFLAT PASS fails=1/20 |
| JN05W2J | ACCEPT JN05W2J PASS fails=1/20 |

## 5. Behavioural scorecards (W-Q behavior_scorecard.py plain words)

### JN05W2

JN05W2 L6M (stack, per week): full stops 11.2/wk $-21420; give-backs 7.6/wk (7.4 round-trips) realised $-10552, forgone vs target $28155; same-side losing runs max 13, p95 6, $-44947 lost on 3rd-and-later; no-new-evidence re-entries 32.8/wk $1128; recoveries cut 12.2/wk $47891, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $47960/wk, losers avoided $49493/wk, net +6814 $/wk; pnl $26598/wk.
JN05W2 HOLD (stack, per week): full stops 10.8/wk $-21191; give-backs 6.9/wk (6.7 round-trips) realised $-9418, forgone vs target $25560; same-side losing runs max 13, p95 6, $-37736 lost on 3rd-and-later; no-new-evidence re-entries 26.2/wk $1799; recoveries cut 11.1/wk $44000, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $44726/wk, losers avoided $44438/wk, net +2690 $/wk; pnl $18042/wk.
JN05W2 PRE (stack, per week): full stops 9.2/wk $-20035; give-backs 4.8/wk (4.5 round-trips) realised $-6621, forgone vs target $17626; same-side losing runs max 9, p95 4, $-21187 lost on 3rd-and-later; no-new-evidence re-entries 12.9/wk $988; recoveries cut 6.8/wk $24679, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $24853/wk, losers avoided $24363/wk, net -1537 $/wk; pnl $10345/wk.
JN05W2 X' (stack, per week): full stops 11.1/wk $-22687; give-backs 3.6/wk (3.1 round-trips) realised $-4638, forgone vs target $12342; same-side losing runs max 8, p95 4, $-12073 lost on 3rd-and-later; no-new-evidence re-entries 3.6/wk $392; recoveries cut 2.5/wk $8955, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $12045/wk, losers avoided $12639/wk, net +2266 $/wk; pnl $3609/wk.


### JN05W2_nF3

JN05W2_nF3 L6M (stack, per week): full stops 10.7/wk $-19808; give-backs 7.5/wk (7.4 round-trips) realised $-11396, forgone vs target $28950; same-side losing runs max 12, p95 6, $-45844 lost on 3rd-and-later; no-new-evidence re-entries 31.1/wk $181; recoveries cut 10.8/wk $40700, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $46483/wk, losers avoided $46486/wk, net +2666 $/wk; pnl $22450/wk.
JN05W2_nF3 HOLD (stack, per week): full stops 10.4/wk $-19709; give-backs 6.9/wk (6.8 round-trips) realised $-10443, forgone vs target $26762; same-side losing runs max 12, p95 6, $-39230 lost on 3rd-and-later; no-new-evidence re-entries 25.1/wk $1386; recoveries cut 9.6/wk $35126, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $41875/wk, losers avoided $40992/wk, net +3464 $/wk; pnl $18816/wk.
JN05W2_nF3 PRE (stack, per week): full stops 8.6/wk $-17370; give-backs 4.8/wk (4.5 round-trips) realised $-7104, forgone vs target $18227; same-side losing runs max 9, p95 4, $-21424 lost on 3rd-and-later; no-new-evidence re-entries 11.8/wk $1053; recoveries cut 5.6/wk $19495, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $22477/wk, losers avoided $21964/wk, net -102 $/wk; pnl $11780/wk.
JN05W2_nF3 X' (stack, per week): full stops 10.1/wk $-18183; give-backs 3.5/wk (3.0 round-trips) realised $-4489, forgone vs target $11962; same-side losing runs max 8, p95 4, $-12535 lost on 3rd-and-later; no-new-evidence re-entries 3.3/wk $583; recoveries cut 2.5/wk $10067, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $10152/wk, losers avoided $11046/wk, net +878 $/wk; pnl $2220/wk.


### JN05W2_nE1

JN05W2_nE1 L6M (stack, per week): full stops 11.2/wk $-20894; give-backs 7.7/wk (7.6 round-trips) realised $-10821, forgone vs target $29093; same-side losing runs max 12, p95 7, $-47794 lost on 3rd-and-later; no-new-evidence re-entries 35.4/wk $60; recoveries cut 12.5/wk $50709, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $46716/wk, losers avoided $48561/wk, net +6568 $/wk; pnl $26352/wk.
JN05W2_nE1 HOLD (stack, per week): full stops 10.7/wk $-20831; give-backs 6.9/wk (6.8 round-trips) realised $-9596, forgone vs target $26133; same-side losing runs max 12, p95 6, $-39319 lost on 3rd-and-later; no-new-evidence re-entries 27.8/wk $1300; recoveries cut 11.2/wk $45698, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $43719/wk, losers avoided $43878/wk, net +2723 $/wk; pnl $18075/wk.
JN05W2_nE1 PRE (stack, per week): full stops 9.2/wk $-19997; give-backs 4.9/wk (4.5 round-trips) realised $-6656, forgone vs target $17726; same-side losing runs max 8, p95 4, $-21483 lost on 3rd-and-later; no-new-evidence re-entries 13.4/wk $1492; recoveries cut 6.8/wk $24825, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $24576/wk, losers avoided $24219/wk, net -933 $/wk; pnl $10949/wk.
JN05W2_nE1 X' (stack, per week): full stops 11.1/wk $-22687; give-backs 3.6/wk (3.1 round-trips) realised $-4653, forgone vs target $12384; same-side losing runs max 8, p95 4, $-12198 lost on 3rd-and-later; no-new-evidence re-entries 3.7/wk $301; recoveries cut 2.5/wk $8955, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $12045/wk, losers avoided $12545/wk, net +2155 $/wk; pnl $3497/wk.


### JN05W2_nC22

JN05W2_nC22 L6M (stack, per week): full stops 13.3/wk $-25004; give-backs 9.4/wk (9.2 round-trips) realised $-12622, forgone vs target $33049; same-side losing runs max 13, p95 6, $-51513 lost on 3rd-and-later; no-new-evidence re-entries 41.3/wk $659; recoveries cut 14.6/wk $53939, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $35177/wk, losers avoided $33606/wk, net +3676 $/wk; pnl $23460/wk.
JN05W2_nC22 HOLD (stack, per week): full stops 12.3/wk $-23798; give-backs 8.0/wk (7.8 round-trips) realised $-10687, forgone vs target $28722; same-side losing runs max 13, p95 6, $-42820 lost on 3rd-and-later; no-new-evidence re-entries 33.2/wk $1766; recoveries cut 13.2/wk $49340, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $34030/wk, losers avoided $32139/wk, net +808 $/wk; pnl $16159/wk.
JN05W2_nC22 PRE (stack, per week): full stops 9.6/wk $-20521; give-backs 5.3/wk (4.9 round-trips) realised $-7057, forgone vs target $18755; same-side losing runs max 11, p95 4, $-22712 lost on 3rd-and-later; no-new-evidence re-entries 14.8/wk $784; recoveries cut 7.4/wk $26325, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $21154/wk, losers avoided $20588/wk, net -1695 $/wk; pnl $10187/wk.
JN05W2_nC22 X' (stack, per week): full stops 11.1/wk $-22687; give-backs 3.6/wk (3.1 round-trips) realised $-4638, forgone vs target $12342; same-side losing runs max 8, p95 4, $-12073 lost on 3rd-and-later; no-new-evidence re-entries 3.7/wk $350; recoveries cut 2.5/wk $8955, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $12045/wk, losers avoided $12609/wk, net +2203 $/wk; pnl $3546/wk.


### JN05W2_nBR3S

JN05W2_nBR3S L6M (stack, per week): full stops 10.9/wk $-21089; give-backs 7.6/wk (7.5 round-trips) realised $-11164, forgone vs target $30108; same-side losing runs max 12, p95 6, $-46937 lost on 3rd-and-later; no-new-evidence re-entries 33.2/wk $738; recoveries cut 12.5/wk $52105, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $32019/wk, losers avoided $31500/wk, net +2691 $/wk; pnl $22475/wk.
JN05W2_nBR3S HOLD (stack, per week): full stops 10.8/wk $-21439; give-backs 6.8/wk (6.7 round-trips) realised $-9843, forgone vs target $26604; same-side losing runs max 12, p95 6, $-39223 lost on 3rd-and-later; no-new-evidence re-entries 27.4/wk $1052; recoveries cut 11.5/wk $46988, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $25685/wk, losers avoided $26965/wk, net +706 $/wk; pnl $16057/wk.
JN05W2_nBR3S PRE (stack, per week): full stops 9.0/wk $-19516; give-backs 4.8/wk (4.4 round-trips) realised $-6454, forgone vs target $17471; same-side losing runs max 9, p95 5, $-21401 lost on 3rd-and-later; no-new-evidence re-entries 13.1/wk $930; recoveries cut 6.8/wk $25335, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $13708/wk, losers avoided $13919/wk, net -859 $/wk; pnl $11023/wk.
JN05W2_nBR3S X' (stack, per week): full stops 11.0/wk $-23060; give-backs 3.8/wk (3.3 round-trips) realised $-5062, forgone vs target $13465; same-side losing runs max 8, p95 4, $-12027 lost on 3rd-and-later; no-new-evidence re-entries 3.7/wk $366; recoveries cut 2.7/wk $9717, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $7269/wk, losers avoided $5714/wk, net +275 $/wk; pnl $1617/wk.


### JN05W2_nFLAT

JN05W2_nFLAT L6M (stack, per week): full stops 21.2/wk $-35397; give-backs 7.6/wk (7.5 round-trips) realised $-10723, forgone vs target $28330; same-side losing runs max 13, p95 6, $-43786 lost on 3rd-and-later; no-new-evidence re-entries 30.6/wk $-85; recoveries cut 13.2/wk $50001, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $44248/wk, losers avoided $46024/wk, net +5257 $/wk; pnl $25041/wk.
JN05W2_nFLAT HOLD (stack, per week): full stops 20.4/wk $-34798; give-backs 6.9/wk (6.7 round-trips) realised $-9538, forgone vs target $25795; same-side losing runs max 13, p95 6, $-37431 lost on 3rd-and-later; no-new-evidence re-entries 24.4/wk $944; recoveries cut 11.9/wk $46031, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $40452/wk, losers avoided $40681/wk, net +1651 $/wk; pnl $17003/wk.
JN05W2_nFLAT PRE (stack, per week): full stops 16.6/wk $-30169; give-backs 4.8/wk (4.4 round-trips) realised $-6613, forgone vs target $17552; same-side losing runs max 8, p95 4, $-20166 lost on 3rd-and-later; no-new-evidence re-entries 11.5/wk $1135; recoveries cut 7.3/wk $25978, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $21487/wk, losers avoided $21576/wk, net +133 $/wk; pnl $12016/wk.
JN05W2_nFLAT X' (stack, per week): full stops 18.4/wk $-32504; give-backs 3.4/wk (2.9 round-trips) realised $-4650, forgone vs target $12217; same-side losing runs max 7, p95 4, $-11708 lost on 3rd-and-later; no-new-evidence re-entries 3.0/wk $249; recoveries cut 2.6/wk $9188, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $9878/wk, losers avoided $10340/wk, net +1704 $/wk; pnl $3046/wk.


### JN05W2J

JN05W2J L6M (stack, per week): full stops 11.0/wk $-18853; give-backs 8.3/wk (8.1 round-trips) realised $-9133, forgone vs target $24130; same-side losing runs max 14, p95 6, $-35308 lost on 3rd-and-later; no-new-evidence re-entries 34.8/wk $1053; recoveries cut 13.1/wk $35622, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $48428/wk, losers avoided $50379/wk, net +2294 $/wk; pnl $22078/wk.
JN05W2J HOLD (stack, per week): full stops 10.7/wk $-18562; give-backs 7.4/wk (7.2 round-trips) realised $-7882, forgone vs target $20833; same-side losing runs max 14, p95 6, $-30154 lost on 3rd-and-later; no-new-evidence re-entries 27.9/wk $1460; recoveries cut 12.0/wk $32472, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $45073/wk, losers avoided $45289/wk, net -669 $/wk; pnl $14682/wk.
JN05W2J PRE (stack, per week): full stops 9.3/wk $-17063; give-backs 4.8/wk (4.4 round-trips) realised $-4833, forgone vs target $12905; same-side losing runs max 9, p95 5, $-15987 lost on 3rd-and-later; no-new-evidence re-entries 13.8/wk $895; recoveries cut 7.5/wk $17555, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $26376/wk, losers avoided $25140/wk, net -4502 $/wk; pnl $7381/wk.
JN05W2J X' (stack, per week): full stops 11.0/wk $-19738; give-backs 3.4/wk (2.9 round-trips) realised $-3342, forgone vs target $9417; same-side losing runs max 8, p95 4, $-9509 lost on 3rd-and-later; no-new-evidence re-entries 3.8/wk $329; recoveries cut 2.6/wk $5802, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $13759/wk, losers avoided $14543/wk, net +2480 $/wk; pnl $3823/wk.


## 6. Live weeks (11-02..05 and 11-06..11)

Exact engine, month 202611 (day files NQ_20261102..11 built by W-T; 11-12 stub not replayed). Reference LPB_BASE = the same engine with the live panel only. The JN04RM base is not replayed here (its inputs end 11-05). Label days; frozen live week A = 11-02..05, week B = 11-06..11 (11-09 label = Sunday-evening open).

| set | week A 11-02..05 net $ | week B 11-06..11 net $ | trades | by book (A+B) |
|--|--|--|--|--|
| LPB_BASE | 87206 | -29664 | 344 | A7 5717, H7 988, K7 22105, M7 4701, O7 5886, P7 23598, U7 -5453 |
| JN05W2 | 46665 | -9848 | 276 | A7 5124, H7 673, K7 18630, M7 5898, O7 2960, P7 6936, U7 -3404 |
| JN05W2_nF3 | 81223 | -23905 | 281 | A7 5124, H7 1342, K7 23688, M7 3890, O7 2960, P7 23716, U7 -3404 |
| JN05W2_nE1 | 69980 | -9848 | 289 | A7 5124, H7 1342, K7 26351, M7 6094, O7 2960, P7 21664, U7 -3404 |
| JN05W2_nC22 | 57644 | -19735 | 345 | A7 5124, H7 988, K7 20576, M7 4701, O7 5886, P7 6688, U7 -6053 |
| JN05W2_nBR3S | 39937 | -15490 | 264 | A7 5779, H7 673, K7 17584, M7 4591, O7 2960, P7 -2552, U7 -4588 |
| JN05W2_nFLAT | 49550 | -9643 | 284 | A7 5717, H7 673, K7 20527, M7 5898, O7 2960, P7 6936, U7 -2804 |

## 7. Worst 10 L6M P7 sessions, entry by entry

# Worst 10 L6M P7 sessions of LPB_BASE, replayed entry by entry (W-J; session key = label day + ET session index; exact engine; Shadow only)

## session 202607280 (LPB_BASE P7 net -14274)
- LPB_BASE: total -14274 over 8 trades: 22:38 4L short StateCut -3007; 00:11 4L short Target 4800; 01:06 5L short Target 5984; 01:23 7L short StateCut -5705; 02:14 4L short StateCut -3254; 03:54 4L long StateCut -3694; 04:43 4L long StateCut -3394; 05:40 7L short StateCut -6005
- JN04RM: total -6508 over 8 trades: 22:38 2L short StateCut -1433; 00:11 2L short Target 2398; 01:06 3L short Target 3601; 01:23 4L short StateCut -3464; 02:14 2L short StateCut -1684; 03:54 2L long StateCut -1719; 04:43 1L long StateCut -877; 05:40 4L short StateCut -3329
- JN05W2: total -12154 over 7 trades: 22:51 4L short StateCut -2669; 00:11 4L short Target 4800; 02:14 4L short StateCut -2624; 02:27 4L short StateCut -2449; 03:54 4L long StateCut -2624; 04:43 4L long StateCut -2474; 05:40 7L short StateCut -4115

## session 202605273 (LPB_BASE P7 net -13000)
- LPB_BASE: total -13000 over 5 trades: 14:11 4L short StateCut -3374; 14:33 3L short StateCut -2449; 15:00 4L short StateCut -3654; 15:20 2L short StateCut -1759; 15:39 2L short StateCut -1764
- JN04RM: total -6130 over 5 trades: 14:11 2L short StateCut -1759; 14:33 1L short StateCut -880; 15:00 2L short StateCut -1649; 15:20 1L short StateCut -992; 15:39 1L short StateCut -850
- JN05W2: total -5093 over 2 trades: 14:11 4L short StateCut -3184; 14:33 3L short StateCut -1909

## session 202609100 (LPB_BASE P7 net -12681)
- LPB_BASE: total -12681 over 3 trades: 23:01 4L short StateCut -3274; 01:07 4L short StateCut -3349; 05:07 7L long StateCut -6059
- JN04RM: total -6750 over 3 trades: 23:01 2L short StateCut -1659; 01:07 2L short StateCut -1659; 05:07 4L long StateCut -3432
- JN05W2: total -4394 over 3 trades: 23:01 4L short StateCut -2924; 01:07 4L short StateCut -2669; 04:47 1L long Target 1199

## session 202608260 (LPB_BASE P7 net -12662)
- LPB_BASE: total -12662 over 4 trades: 22:09 7L long StateCut -5810; 00:04 7L short Target 6004; 01:09 7L short StateCut -5718; 03:03 7L long StateCut -7138
- JN04RM: total -12662 over 4 trades: 22:09 7L long StateCut -5810; 00:04 7L short Target 6004; 01:09 7L short StateCut -5718; 03:03 7L long StateCut -7138
- JN05W2: total -7468 over 4 trades: 22:58 4L long StateCut -4244; 00:25 5L short Target 5989; 01:18 7L short StateCut -4508; 03:03 7L long StateCut -4705

## session 202605060 (LPB_BASE P7 net -12366)
- LPB_BASE: total -12366 over 2 trades: 23:48 7L long StateCut -6223; 00:48 7L short StateCut -6143
- JN04RM: total 3079 over 3 trades: 23:48 4L long StateCut -3594; 00:48 2L short StateCut -1729; 04:22 7L long Target 8402
- JN05W2: total -11754 over 2 trades: 23:48 7L long StateCut -4998; 00:48 7L short StateCut -6756

## session 202610010 (LPB_BASE P7 net -12188)
- LPB_BASE: total -12188 over 2 trades: 23:08 7L short StateCut -6615; 00:01 7L long StateCut -5573
- JN04RM: total -9974 over 2 trades: 23:08 7L short StateCut -6615; 00:01 4L long StateCut -3359
- JN05W2: total -8498 over 1 trades: 23:08 7L short StopJoin -8498

## session 202605151 (LPB_BASE P7 net -11920)
- LPB_BASE: total -11920 over 8 trades: 06:07 4L short StateCut -3344; 06:21 4L short StateCut -3714; 06:56 1L long Target 1199; 07:28 2L long StateCut -1699; 09:12 1L short Target 1199; 09:42 4L short StateCut -3294; 10:40 2L short StateCut -1464; 11:01 2L long BookLock -802
- JN04RM: total -2664 over 10 trades: 06:07 1L short StateCut -837; 06:21 1L short StateCut -957; 06:56 1L long Target 1199; 07:28 1L long StateCut -847; 09:12 1L short Target 1199; 09:42 1L short StateCut -942; 10:40 1L short StateCut -970; 11:01 1L long StateCut -857; 11:52 1L long StateCut -850; 12:25 1L short Target 1199
- JN05W2: total -9389 over 7 trades: 06:21 4L short StateCut -3884; 07:11 1L long StateCut -667; 09:12 1L short Target 1199; 09:42 4L short StateCut -2314; 10:05 2L short StateCut -1269; 11:01 2L long StateCut -1279; 11:52 2L long StateCut -1174

## session 202610080 (LPB_BASE P7 net -11851)
- LPB_BASE: total -11851 over 2 trades: 22:21 7L long StateCut -5873; 00:56 7L short StateCut -5978
- JN04RM: total -11851 over 2 trades: 22:21 7L long StateCut -5873; 00:56 7L short StateCut -5978
- JN05W2: total -8451 over 2 trades: 22:41 7L long StateCut -4578; 01:01 7L short StateCut -3874

## session 202606180 (LPB_BASE P7 net -11837)
- LPB_BASE: total -11837 over 2 trades: 23:42 7L short StateCut -6615; 00:31 7L long StateCut -5221
- JN04RM: total -2812 over 3 trades: 23:42 4L short StateCut -3759; 00:31 2L long StateCut -1456; 05:27 2L long Target 2403
- JN05W2: total -10736 over 2 trades: 23:42 7L short StateCut -7578; 00:35 7L long StateCut -3158

## session 202606030 (LPB_BASE P7 net -11538)
- LPB_BASE: total -11538 over 2 trades: 22:12 7L long StateCut -5710; 23:35 7L short StateCut -5828
- JN04RM: total -5057 over 4 trades: 22:12 4L long StateCut -3259; 23:35 4L short StateCut -3349; 01:36 1L long StateCut -847; 02:11 2L long Target 2398
- JN05W2: total -3696 over 2 trades: 22:33 4L long StateCut -4029; 01:36 2L long Target 333
