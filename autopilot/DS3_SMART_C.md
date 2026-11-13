# DS3_SMART_C — T-SMART items B4 (MNQ granularity), C1 (dead slots), C2 (risk budget reallocation), C3 (add to winners), C4 (trade count), W-SM5

Generated 2026-11-13 17:57Z UTC. Bases JN05W2 (live panel + F3 + E1 + C22 + BR3S + FLAT45K) and JN05W2J (same five on JN04RM), exact 43 months. Exact engine, one set per job, shared-memory cache, admission tag SMARTC. Shadow only, no PASS claim. Prereg autopilot/SMART_C_PREREG.md (sha in DECISIONS.md).

**CAVEAT on every number here: the engine P7 state cut fires in the engine but did not fire live on 2026-11-11 (autopilot/DS3_P7_CUT_FIDELITY.md); the bases and these cells inherit the engine cut.**

**Lots:** the reference trades average K7 1.1, A7 1.0, M7 1.2, U7 2.6, P7 3.3 NQ lots (JN05W2), well below the user lots (K7 4, M7 4, U7 7, P7 12/7/7, H7 7, A7 2; caps x1.75). Count and slot rules transfer unchanged; fixed-dollar rules scale by the lots ratio; C2 multipliers are ratios and transfer; C3 adds need >= 3 lots on the first entry to be non-trivial (K7/A7/M7 at 1-2 lots round the add away) — at the user lots they are not inert.

## 0. Trend-week clause first, then L6M / HOLD (exact; a set appears only when its 6 L6M months are DONE; PRE / X' / GAP follow for cells with L6M cut >= 5% and d mean >= -$1,000/wk)

| set | months | ref | 5 best wks kept | winning wks turned losing | L6M cut % | L6M d mean/wk (all wks) | HOLD cut % | HOLD d mean/wk | PRE cut / d mean | X' cut / d mean | WF cut / beat |
|--|--|--|--|--|--|--|--|--|--|--|--|
| SC_C1_half | 12 | JN05W2 | 93% ($295k of $316k) | 0 of 20 | 9.7 | -2341 | 10.8 | -1997 | - / - | - / - | - |
| SC_C1_q | 12 | JN05W2 | 89% ($280k of $316k) | 2 of 20 | 9.7 | -3898 | 3.6 | -2307 | - / - | - / - | - |
| SC_C1_zero | 12 | JN05W2 | 81% ($257k of $316k) | 3 of 20 | -3.3 | -6470 | -36.5 | -6380 | - / - | - / - | - |
| SC_C1s_lh_x0 | 12 | JN05W2 | 100% ($316k of $316k) | 0 of 20 | 0.0 | -246 | -1.9 | -170 | - / - | - / - | - |
| SC_C1s_lunch_x0 | 12 | JN05W2 | 98% ($311k of $316k) | 0 of 20 | 0.0 | -1036 | -2.5 | 67 | - / - | - / - | - |
| SC_C2_calmar | 12 | JN05W2 | 106% ($337k of $316k) | 1 of 20 | -38.9 | -948 | 6.2 | 184 | - / - | - / - | - |
| SC_C2_exp | 12 | JN05W2 | 107% ($339k of $316k) | 0 of 20 | -37.7 | -1522 | -17.2 | -118 | - / - | - / - | - |
| SC_C3_ALL_v40_f33 | 12 | JN05W2 | 82% ($260k of $316k) | 5 of 20 | -85.6 | -11382 | -106.9 | -9360 | - / - | - / - | - |
| SC_C3_P7_v25_f33 | 12 | JN05W2 | 64% ($202k of $316k) | 7 of 20 | -41.6 | -13486 | -40.7 | -9809 | - / - | - / - | - |
| SC_C3_P7_v25_f50 | 12 | JN05W2 | 66% ($209k of $316k) | 6 of 20 | -63.1 | -13852 | -3.7 | -10381 | - / - | - / - | - |
| SC_C3_P7_v40_f33 | 1 | JN05W2 | (running) |||||||||
| SC_C3_P7_v40_f33_nobe | 12 | JN05W2 | 97% ($306k of $316k) | 1 of 20 | 13.8 | 1424 | -96.8 | -565 | - / - | - / - | - |
| SC_C3_P7_v40_f50 | 12 | JN05W2 | 76% ($240k of $316k) | 3 of 20 | -26.2 | -10060 | -192.2 | -11895 | - / - | - / - | - |
| SC_C3_P7_v60_f33 | 12 | JN05W2 | 85% ($269k of $316k) | 4 of 20 | 8.5 | -2034 | -50.0 | -4231 | - / - | - / - | - |
| SC_C3_P7_v60_f50 | 12 | JN05W2 | 85% ($268k of $316k) | 3 of 20 | 20.7 | -1144 | -177.7 | -4880 | - / - | - / - | - |
| SC_C4_max2 | 12 | JN05W2 | 51% ($161k of $316k) | 0 of 20 | -98.2 | -7770 | -64.8 | -6877 | - / - | - / - | - |
| SC_C4_max3 | 1 | JN05W2 | (running) |||||||||
| SC_C4_max4 | 12 | JN05W2 | 62% ($197k of $316k) | 1 of 20 | -10.4 | -4197 | 8.4 | -2168 | - / - | - / - | - |

cut % = maxDD of the stack vs the base set (positive = shallower); d mean = all-weeks mean difference ($/wk) vs the base on the same months; the same-side run columns of score_sc (run_max / run_p95) are in the per-set files /mnt/l2/l2vast/_th_smart_c/score_<SET>.csv.

## 1. Acceptance (trader test) and behavioural scorecard a-e per set with L6M complete

- **SC_C1_half** acceptance_p7: `ACCEPTANCE P7 SC_C1_half  2026-11-13 07:16Z   (months 7: 202604..202610; reference LPB_BASE months 43)`; scorecard text /mnt/l2/l2vast/_th_works/q/sc/sc_SC_C1_half.txt
- **SC_C1_q** acceptance_p7: `ACCEPTANCE P7 SC_C1_q  2026-11-13 01:10Z   (months 6: 202605..202610; reference LPB_BASE months 43)`; scorecard text /mnt/l2/l2vast/_th_works/q/sc/sc_SC_C1_q.txt
- **SC_C1_zero** acceptance_p7: `ACCEPTANCE P7 SC_C1_zero  2026-11-13 03:41Z   (months 6: 202605..202610; reference LPB_BASE months 43)`; scorecard text /mnt/l2/l2vast/_th_works/q/sc/sc_SC_C1_zero.txt
- **SC_C1s_lh_x0** acceptance_p7: `ACCEPTANCE P7 SC_C1s_lh_x0  2026-11-13 05:44Z   (months 7: 202604..202610; reference LPB_BASE months 43)`; scorecard text /mnt/l2/l2vast/_th_works/q/sc/sc_SC_C1s_lh_x0.txt
- **SC_C1s_lunch_x0** acceptance_p7: `ACCEPTANCE P7 SC_C1s_lunch_x0  2026-11-13 05:14Z   (months 6: 202605..202610; reference LPB_BASE months 43)`; scorecard text /mnt/l2/l2vast/_th_works/q/sc/sc_SC_C1s_lunch_x0.txt
- **SC_C2_calmar** acceptance_p7: `ACCEPTANCE P7 SC_C2_calmar  2026-11-13 03:11Z   (months 6: 202605..202610; reference LPB_BASE months 43)`; scorecard text /mnt/l2/l2vast/_th_works/q/sc/sc_SC_C2_calmar.txt
- **SC_C2_exp** acceptance_p7: `ACCEPTANCE P7 SC_C2_exp  2026-11-13 01:40Z   (months 6: 202605..202610; reference LPB_BASE months 43)`; scorecard text /mnt/l2/l2vast/_th_works/q/sc/sc_SC_C2_exp.txt
- **SC_C3_ALL_v40_f33** acceptance_p7: `ACCEPTANCE P7 SC_C3_ALL_v40_f33  2026-11-13 04:43Z   (months 6: 202605..202610; reference LPB_BASE months 43)`; scorecard text /mnt/l2/l2vast/_th_works/q/sc/sc_SC_C3_ALL_v40_f33.txt
- **SC_C3_P7_v25_f33** acceptance_p7: `ACCEPTANCE P7 SC_C3_P7_v25_f33  2026-11-13 04:43Z   (months 6: 202605..202610; reference LPB_BASE months 43)`; scorecard text /mnt/l2/l2vast/_th_works/q/sc/sc_SC_C3_P7_v25_f33.txt
- **SC_C3_P7_v25_f50** acceptance_p7: `ACCEPTANCE P7 SC_C3_P7_v25_f50  2026-11-13 06:15Z   (months 7: 202604..202610; reference LPB_BASE months 43)`; scorecard text /mnt/l2/l2vast/_th_works/q/sc/sc_SC_C3_P7_v25_f50.txt
- **SC_C3_P7_v40_f33_nobe** acceptance_p7: `ACCEPTANCE P7 SC_C3_P7_v40_f33_nobe  2026-11-13 06:15Z   (months 6: 202605..202610; reference LPB_BASE months 43)`; scorecard text /mnt/l2/l2vast/_th_works/q/sc/sc_SC_C3_P7_v40_f33_nobe.txt
- **SC_C3_P7_v40_f50** acceptance_p7: `ACCEPTANCE P7 SC_C3_P7_v40_f50  2026-11-13 03:41Z   (months 6: 202605..202610; reference LPB_BASE months 43)`; scorecard text /mnt/l2/l2vast/_th_works/q/sc/sc_SC_C3_P7_v40_f50.txt
- **SC_C3_P7_v60_f33** acceptance_p7: `ACCEPTANCE P7 SC_C3_P7_v60_f33  2026-11-13 01:10Z   (months 6: 202605..202610; reference LPB_BASE months 43)`; scorecard text /mnt/l2/l2vast/_th_works/q/sc/sc_SC_C3_P7_v60_f33.txt
- **SC_C3_P7_v60_f50** acceptance_p7: `ACCEPTANCE P7 SC_C3_P7_v60_f50  2026-11-13 05:44Z   (months 6: 202605..202610; reference LPB_BASE months 43)`; scorecard text /mnt/l2/l2vast/_th_works/q/sc/sc_SC_C3_P7_v60_f50.txt
- **SC_C4_max2** acceptance_p7: `ACCEPTANCE P7 SC_C4_max2  2026-11-13 04:12Z   (months 6: 202605..202610; reference LPB_BASE months 43)`; scorecard text /mnt/l2/l2vast/_th_works/q/sc/sc_SC_C4_max2.txt
- **SC_C4_max4** acceptance_p7: `ACCEPTANCE P7 SC_C4_max4  2026-11-13 03:42Z   (months 7: 202604..202610; reference LPB_BASE months 43)`; scorecard text /mnt/l2/l2vast/_th_works/q/sc/sc_SC_C4_max4.txt

## 2. First-order screens on the exact reference trades (screen only: lots are not re-rounded, paths do not change; EXACT overstates/understates; the exact rows above are the verdict)

### Base JN05W2

| cell | L6M cut % | HOLD | PRE | X' | L6M d mean/wk | HOLD d mean/wk | PRE | X' | 5 best L6M wks kept | winning wks turned losing |
|--|--|--|--|--|--|--|--|--|--|--|
| C1_half | 14.0 | 5.7 | 17.1 | 0.0 | -3739.0 | -3390.0 | -69.0 | -956.0 | 89% | 0 |
| C1_q | 11.7 | 2.4 | 16.7 | 0.0 | -4404.0 | -2896.0 | 76.0 | -736.0 | 85% | 0 |
| C1_qz | 23.4 | -11.4 | 32.6 | 0.0 | -8808.0 | -5793.0 | 153.0 | -1473.0 | 70% | 1 |
| C1_zero | 28.1 | -23.9 | 33.4 | 0.0 | -7477.0 | -6781.0 | -139.0 | -1911.0 | 77% | 2 |
| C1s_close_1500_1800_x0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 100% | 0 |
| C1s_close_1500_1800_x0.5 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 100% | 0 |
| C1s_last_hour14_15_x0.0 | 0.0 | -1.9 | 4.3 | 6.4 | -246.0 | -170.0 | 92.0 | -25.0 | 100% | 0 |
| C1s_last_hour14_15_x0.5 | 0.0 | -0.9 | 2.1 | 3.2 | -123.0 | -85.0 | 46.0 | -13.0 | 100% | 0 |
| C1s_lunch12_13_x0.0 | 0.0 | -0.7 | -2.9 | -1.5 | -1462.0 | -355.0 | -303.0 | -184.0 | 95% | 0 |
| C1s_lunch12_13_x0.5 | 0.0 | -0.4 | -1.4 | -0.7 | -731.0 | -177.0 | -152.0 | -92.0 | 98% | 0 |
| C1s_open0930_0935_x0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 100% | 0 |
| C1s_open0930_0935_x0.5 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 100% | 0 |
| C1s_open1800_1805_x0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 2.0 | 0.0 | 100% | 0 |
| C1s_open1800_1805_x0.5 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 1.0 | 0.0 | 100% | 0 |
| C2_calmar | -28.1 | 8.4 | 13.2 | 0.0 | 638.0 | 1083.0 | 71.0 | -389.0 | 110% | 0 |
| C2_exp | -5.6 | 1.2 | 8.5 | 0.0 | 424.0 | 640.0 | 422.0 | -344.0 | 107% | 0 |
| C4_max2 | -70.9 | -0.7 | 14.7 | 1.6 | -6224.0 | -5221.0 | -1241.0 | -255.0 | 52% | 0 |
| C4_max3 | 0.8 | 16.4 | 0.1 | 0.0 | -4277.0 | -2978.0 | -118.0 | 11.0 | 51% | 0 |
| C4_max4 | -16.8 | 8.5 | -5.2 | 0.0 | -3405.0 | -2381.0 | 252.0 | 5.0 | 64% | 0 |

### Base JN05W2J

| cell | L6M cut % | HOLD | PRE | X' | L6M d mean/wk | HOLD d mean/wk | PRE | X' | 5 best L6M wks kept | winning wks turned losing |
|--|--|--|--|--|--|--|--|--|--|--|
| C1_half | 25.7 | 8.6 | 27.0 | 0.0 | -2615.0 | -2285.0 | -333.0 | -872.0 | 88% | 0 |
| C1_q | 12.6 | 0.2 | 19.4 | 0.0 | -2148.0 | -1771.0 | -203.0 | -686.0 | 89% | 0 |
| C1_qz | 25.2 | -27.2 | 33.7 | -8.9 | -4297.0 | -3543.0 | -407.0 | -1372.0 | 77% | 1 |
| C1_zero | 51.4 | -5.6 | 35.4 | 0.0 | -5229.0 | -4571.0 | -667.0 | -1744.0 | 76% | 2 |
| C1s_close_1500_1800_x0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 100% | 0 |
| C1s_close_1500_1800_x0.5 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 100% | 0 |
| C1s_last_hour14_15_x0.0 | -5.0 | -8.2 | 1.7 | 5.6 | -346.0 | -260.0 | 91.0 | 15.0 | 99% | 0 |
| C1s_last_hour14_15_x0.5 | -2.5 | -4.1 | 3.1 | 4.4 | -173.0 | -130.0 | 45.0 | 7.0 | 100% | 0 |
| C1s_lunch12_13_x0.0 | -5.0 | -6.5 | -4.2 | -3.2 | -844.0 | -153.0 | -330.0 | -150.0 | 98% | 0 |
| C1s_lunch12_13_x0.5 | -2.5 | -3.3 | -2.1 | -1.0 | -422.0 | -77.0 | -165.0 | -75.0 | 99% | 0 |
| C1s_open0930_0935_x0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 100% | 0 |
| C1s_open0930_0935_x0.5 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 100% | 0 |
| C1s_open1800_1805_x0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 17.0 | 9.0 | 2.0 | 0.0 | 100% | 0 |
| C1s_open1800_1805_x0.5 | 0.0 | 0.0 | 0.0 | 0.0 | 9.0 | 4.0 | 1.0 | 0.0 | 100% | 0 |
| C2_calmar | 9.1 | 9.1 | 2.7 | 0.0 | 1852.0 | 1797.0 | 453.0 | -491.0 | 108% | 1 |
| C2_exp | 9.8 | 5.2 | 1.9 | 0.0 | 1339.0 | 1242.0 | 720.0 | -360.0 | 107% | 0 |
| C4_max2 | -83.2 | -39.5 | 16.0 | -10.1 | -6105.0 | -5008.0 | -1220.0 | -357.0 | 55% | 1 |
| C4_max3 | 29.4 | 1.1 | 3.6 | -3.0 | -3773.0 | -2852.0 | -121.0 | -104.0 | 57% | 0 |
| C4_max4 | 0.2 | -21.5 | -0.5 | 0.0 | -2703.0 | -2344.0 | 303.0 | 17.0 | 80% | 1 |

Cells: C1_half / zero / q = bi-weekly refit slot tables (book x 30-min ET slot, trailing 26 wk of reference trades, n>=8): slot sum < 0 -> x0.5 (half), x0 (zero), worst quartile -> x0.5 (q); qz = worst quartile -> x0. C1s_* = fixed windows. C2_exp / calmar = constant-risk lots multiplier per book (clip 0.5-1.5). C4_maxN = at most N entries per book per session.

## 3. C4 where the net sits: trade number within the book-session (JN05W2 reference, 43 months; 5 = 5th or later)

| book | nth | trades | net $ | net / trade $ |
|--|--|--|--|--|
| A7 | 1 | 684 | 60322 | 88 |
| A7 | 2 | 267 | 44256 | 166 |
| A7 | 3 | 117 | 11090 | 95 |
| A7 | 4 | 46 | 14425 | 314 |
| A7 | 5 | 42 | 2836 | 68 |
| H7 | 1 | 892 | 149861 | 168 |
| H7 | 2 | 140 | 14533 | 104 |
| H7 | 3 | 14 | 1 | 0 |
| H7 | 4 | 2 | 1423 | 712 |
| K7 | 1 | 2936 | 213138 | 73 |
| K7 | 2 | 1843 | 65015 | 35 |
| K7 | 3 | 984 | 47716 | 48 |
| K7 | 4 | 543 | -11323 | -21 |
| K7 | 5 | 772 | 65816 | 85 |
| M7 | 1 | 1664 | 85208 | 51 |
| M7 | 2 | 1143 | 26694 | 23 |
| M7 | 3 | 606 | 12033 | 20 |
| M7 | 4 | 305 | -26768 | -88 |
| M7 | 5 | 267 | -44795 | -168 |
| O7 | 1 | 451 | 80149 | 178 |
| O7 | 2 | 1 | -567 | -567 |
| P7 | 1 | 2233 | 444454 | 199 |
| P7 | 2 | 1291 | 260326 | 202 |
| P7 | 3 | 592 | 74186 | 125 |
| P7 | 4 | 309 | 72561 | 235 |
| P7 | 5 | 323 | 81994 | 254 |
| U7 | 1 | 1094 | 319741 | 292 |
| U7 | 2 | 204 | -23140 | -113 |
| U7 | 3 | 30 | 45672 | 1522 |
| U7 | 4 | 3 | 8397 | 2799 |

M7 trades 4+ lose (−$71k net over 43 months) and K7/P7 3rd+ trades still pay; the cap cells above show what a blanket cap costs.

## 4. B4 MNQ granularity: what expressing a book in MNQ costs

Fees per FEES.md: NQ RT $4.84 per contract, MNQ RT $1.78 per contract (PROXY: MES value). One NQ lot = 10 MNQ = $17.80 RT, i.e. +$12.96 per NQ-equivalent lot per round trip. Slip per MNQ order is assumed equal to NQ in points (unmeasured). The engine point value is $20 hard-coded and lots are integers, so MNQ lots are NOT simulated; this is a fee recomputation on the exact JN05W2 trades.

| book | trades | NQ lots | fee NQ $ (43 mo) | fee MNQ $ | net $ | net $/wk | extra fee $/wk if all in MNQ | extra fee as % of book net/wk |
|--|--|--|--|--|--|--|--|--|
| A7 | 1156 | 1156 | 5595 | 20577 | 132929 | 711 | 80 | 11% |
| H7 | 1048 | 1875 | 9075 | 33375 | 165819 | 887 | 130 | 15% |
| K7 | 7078 | 8120 | 39301 | 144536 | 380362 | 2034 | 563 | 28% |
| M7 | 3985 | 4681 | 22656 | 83322 | 52372 | 280 | 324 | 116% |
| O7 | 452 | 452 | 2188 | 8046 | 79582 | 426 | 31 | 7% |
| P7 | 4748 | 15342 | 74255 | 273088 | 933520 | 4992 | 1063 | 21% |
| U7 | 1331 | 3476 | 16824 | 61873 | 350670 | 1875 | 241 | 13% |

Reading: to be worth expressing K7 / M7 / A7 in MNQ, a partial-exit / staggered-target / 0.5x structure has to add more than $12.96 per NQ-equivalent lot per round trip (K7 about $14 per trade at its 1.1 average lots, about $563/wk). The best exact partial-lot K7 cell so far (BO_K7x3_RUNG_T30_f0p5_fl2_through1, 3x lots, L6M) adds about +$1.76k/wk over its own 3x reference on about 480 NQ lots/wk, i.e. about $3.7 per lot, below the MNQ fee premium; no K7/M7/A7 partial cell from T-BUILD-ON or near-zone clears it on the exact rows read so far (exact MNQ re-run needs fractional lots in the engine, not built).
