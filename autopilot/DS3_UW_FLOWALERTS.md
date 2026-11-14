# DS3_UW_FLOWALERTS - UW flow alerts as entry triggers and filters (W-FA)

**VERDICT: weak/null-level so far, no PASS - first-order streams: 253944 sign-gate passes vs 242939 in the shifted-event placebos (ratio 1.05); exact-engine runs still queued (shared admission). Flow-alert triggers and filters are NOT a lead unless the table in section 4b/5 shows a set that beats its placebo in BOTH windows.**

Updated 2026-11-14T01:05Z by fa_cycle.sh (loop, every 3 h). Research/shadow only. No PASS claims. Prereg: autopilot/FLOWALERTS_PREREG.md (sha in DECISIONS.md).

## 1. How deep is the alert history (honest)

The alert endpoint honours time windows: full per-day history exists for 2024-10-01..2026-11-12 (553 weekday files per ticker, IWM QQQ SPY DIA NVDA AAPL MSFT AMZN META GOOGL TSLA). Index options: SPXW and SPX alerts exist from about 2025-03-03 (nothing before), NDX/NDXP return ZERO alerts on this plan (NDX flow is only available as tape trades since 2025-07-21, used as proxy below). Metals/oil ETFs (GLD GDX SLV USO XLE XOP): alerts returned rows for current dates; not pulled by W-UB3 (phase FM never ran); not part of this deliverable unless added later. CAVEAT FIXED: the first pull (W-UB3 phase F) stopped at 2,400 rows per day (12 pages) and walked newest first, so on busy days (QQQ/SPY from 2026-09-21, NVDA TSLA 9-10 days, META 2) only the afternoon survived; W-FA re-pulled those days deep (up to 80 pages) into /mnt/l2/l2vast/_uwfa/raw/ which supersedes. Alert rules present: RepeatedHits (+Ascending/DescendingFill, VolumeOverOi, OtmEarningsFloor) - the "repeated hits on the same strike" feature is the alert rule itself plus a causal 30-min same-chain count (rep30).

| ticker | alerts | days | first | last | med_per_day | max_day | days_ge_2400_after_fix | deep_repull_days |
|---|---|---|---|---|---|---|---|---|
| QQQ | 452480 | 531 | 20241001 | 20261112 | 239.0 | 14084 | 39 | 39 |
| SPY | 594578 | 531 | 20241001 | 20261112 | 317.0 | 21114 | 39 | 39 |
| IWM | 68191 | 532 | 20241001 | 20261112 | 64.0 | 1573 | 0 | 0 |
| SPXW | 236001 | 423 | 20250310 | 20261112 | 223.0 | 10914 | 0 | 444 |
| SPX | 33140 | 423 | 20250310 | 20261112 | 70.0 | 361 | 0 | 444 |
| NVDA | 217878 | 531 | 20241001 | 20261112 | 236.0 | 8059 | 9 | 9 |
| AAPL | 65534 | 531 | 20241001 | 20261112 | 58.0 | 1629 | 0 | 0 |
| MSFT | 39422 | 531 | 20241001 | 20261112 | 43.0 | 1575 | 0 | 0 |
| AMZN | 49052 | 531 | 20241001 | 20261112 | 51.0 | 1273 | 0 | 0 |
| META | 62853 | 531 | 20241001 | 20261112 | 64.0 | 4136 | 2 | 2 |
| GOOGL | 35543 | 531 | 20241001 | 20261112 | 39.0 | 1044 | 0 | 0 |
| TSLA | 243808 | 531 | 20241001 | 20261112 | 299.0 | 4418 | 10 | 10 |

Timestamps: usable at created_at + 120 s (ASSUMED). Measured created_at minus trade end_time = median 7 s (that is alert creation lag, not delivery lag). Forward register: running (pid in ps: fwd_alerts.py), no RTH session recorded yet (first session Mon 2026-11-16 09:25 ET); measured delivery lag (our arrival minus created_at) will be reported here.

Tape proxies (same features from every trade >= $50k, /uw/tape_big, since 2025-07-21; multileg removed; UW sweep tag is empty in this file, so sweep/block cannot be proxied; ask/bid side from the tape tag; no OI so no opening proxy): groups T_SPX T_NDX T_QQQ T_SPY T_IWM T_MEGA7 T_NVDA T_TSLA run through the identical screen (window OLDER is only 2025-07..2026-05 for them).


## 1b. How to read this page (caveats that change the answer)
1. The "gate" in section 3 is the tolerant SIGN gate (net > 0 and excess over the every-minute clock > 0 in L3M, L6M and OLDER). Roughly 4% of cells pass by chance; what matters is the ratio to the placebo columns (events shifted 11 / 23 / 37 weekdays) and whether the best real cell beats the best placebo cell. The family is ~100k cells per session and direction, so a best t-stat of 2.5 to 3 is what pure noise produces.
2. Filter drawdown gains (section 5) are mostly ONE WEEK. JN05W2 max DD in L3M and L6M is a single week (ISO 2026-W44, -$36.4k); older windows are W28-2025 (-$68.9k), W06-2026 (-$55.1k), W08-2025, W13-2026. A rule that happens to skip a few trades in that week "improves DD" by up to $12k in all windows that contain it. Several unrelated rules show the identical DD gain for this reason. Trust only the exact placebos in 4c.
3. The count of gate passes among filter rules falls with the placebo shift distance (749 real, 417 at 11 d, 213 at 23 d, 64 at 37 d): the alert features carry slowly varying market-activity information (a volatility-regime proxy), not direction. The direction-free rule (skipAct: skip when |flow| is large) passes about as often as the directional ones.
4. The every-day clock baseline (4a) is not zero: the short side in NY AM made about +$2.0k/wk standalone in L6M in the harness, and Asia short +$0.5k. Trigger books must be compared with that, not with zero.
5. Exact-engine results are path dependent: one skipped trade changed a month by +$24k in TL3_UW_FF1 (202607, 202609). Month-to-month noise of that size is why every exact number is shown next to three exact placebos.
6. Alert timing: usable at created_at + 120 s (ASSUMED, not measured; measured creation lag after the trade is 7 s median). The forward register (fwd_alerts.py) measures real delivery lag from Mon 2026-11-16.
7. ES: first-order screen and harness only (the injection hook and live books are NQ). Tape proxies cover SPX/NDX since 2025-07-21 only; the sweep tag is empty in tape_big.
8. Price windows end 2026-11-10 (last 1-min bar on the box); alerts exist to 2026-11-12.


## 2. Best per session (exact engine, JN05W2 base all layers ON; delta = injected/filtered stack minus JN05W2 on the same months, $/wk and max DD in $; negative dDD = smaller drawdown)
Windows: L6M = 2026-05..10; OLDER = 2025-11..2026-04. Plain strength is judged against the exact placebos in section 4c and the every-day clock (4a). Nothing here is a PASS; a "weak lead" would still need the forward register.

| session | kind | what | L6M_dMean | L6M_dDD | OLDER_dMean | OLDER_dDD | strength | set |
|---|---|---|---|---|---|---|---|---|
| nyam | BOOK | SPX prem>=250k any openP anyside dte=1-5 put burst1 fade (Eb1_S30_Tnone_X30) | 392.0 | 0.0 | nan | nan | pending (months running) | TL3_UW_FA1 |
| asia | BOOK | IWM prem>=50k any any aggr dte=1-5 put carry q0.75 follow (Eb3_S30_Tnone_XSE) | -18.0 | -903.0 | nan | nan | pending (months running) | TL3_UW_FA2 |
| london | BOOK | GOOGL prem>=50k any any anyside dte=6+ both carry q0.75 follow (Emkt_Sa2_T45_X60) | 394.0 | -2557.0 | nan | nan | pending (months running) | TL3_UW_FA3 |
| pre | BOOK | QQQ prem>=50k any openP aggr dte=6+ both carry q0.50 fade (Eb1_Sa2_Ta2_X60) | 363.0 | -1009.0 | nan | nan | pending (months running) | TL3_UW_FA4 |
| asia | BOOK | QQQ prem>=1000k nonsweep any aggr dte=any put carry q0.50 fade (Emkt_S90_Ta1_XSE) | 36.0 | -2031.0 | nan | nan | pending (months running) | TL3_UW_FA5 |
| nypm | BOOK | MEGA7 prem>=50k any openP aggr dte=1-5 call burst3 follow (Emkt_S45_Tnone_X120) | 205.0 | -1034.0 | nan | nan | pending (months running) | TL3_UW_FA6 |
| all | FILTER | TSLA/AGG/1440 skipOpp thr 1.73e+07 skip | nan | nan | nan | nan | pending (months running) | TL3_UW_FF1 |
| asia | FILTER | MSFT/D15/1440 skipAl thr 4.25e+05 skip | nan | nan | nan | nan | pending (months running) | TL3_UW_FF2 |
| london | FILTER | SPY/D15/1440 skipOpp thr 1.5e+06 skip | nan | nan | nan | nan | pending (months running) | TL3_UW_FF3 |
| all | FILTER | AAPL/SWP/1440 skipAct thr 4.03e+06 skip | nan | nan | nan | nan | pending (months running) | TL3_UW_FF4 |

## 3. First-order trigger screen (alerts, all groups), session by session
Event = first qualifying alert (or n-th within 10 min) per label day x session x direction, entry at the open of the first 1-min bar >= created_at+120 s, exit at the close of minute +h (1/5/15/60 min; carry streams also SE = session end) truncated at session end. Net $ per contract per event after measured NQ cost (0.23 pt entry + 0.23 pt exit + $4.84; ES 1 tick/side assumed). Windows: L3M L6M OLDER(before L6M start) HOLD PREUW; window ends at the last 1-min price day (2026-11-10). LEAD gate = net>0 and excess over the every-minute clock drift >0 in L3M, L6M and OLDER with n_L6M>=15, n_OLDER>=15, n_L3M>=5. "gates" below counts cells passing that SIGN gate; the same screen on events shifted 11/23/37 weekdays gives the placebo columns (mean of 3 draws for count, max of 3 for best S; S = min of the three window nets). A family is only interesting if gates and best S clearly beat the placebo columns.

### 3a. Alert streams (groups QQQ SPY IWM SPX MEGA7 NVDA AAPL MSFT AMZN META GOOGL TSLA)
| sess | mode | inst | cells | gates | pl_gates | gate_ratio | bestS | pl_bestS | bestS_minus_placebo_max |
|---|---|---|---|---|---|---|---|---|---|
| asia | fade | ES | 112365 | 8075 | 5994.3 | 1.3 | 491.7 | 616.9 | -125.2 |
| asia | fade | NQ | 112365 | 14425 | 10861.0 | 1.3 | 818.3 | 1059.0 | -240.7 |
| asia | follow | ES | 112365 | 5304 | 7332.7 | 0.7 | 509.0 | 485.8 | 23.3 |
| asia | follow | NQ | 112365 | 9630 | 12172.3 | 0.8 | 780.1 | 1132.4 | -352.3 |
| london | fade | ES | 112365 | 3207 | 4749.7 | 0.7 | 532.7 | 533.9 | -1.2 |
| london | fade | NQ | 112365 | 8423 | 9487.0 | 0.9 | 1004.0 | 1048.6 | -44.7 |
| london | follow | ES | 112365 | 5541 | 3365.0 | 1.6 | 591.0 | 607.1 | -16.1 |
| london | follow | NQ | 112365 | 9704 | 8854.7 | 1.1 | 1065.7 | 1081.7 | -16.0 |
| pre | fade | ES | 112365 | 5407 | 4975.7 | 1.1 | 237.7 | 330.5 | -92.8 |
| pre | fade | NQ | 112365 | 10781 | 9428.0 | 1.1 | 415.2 | 621.8 | -206.7 |
| pre | follow | ES | 112365 | 5967 | 7502.0 | 0.8 | 308.9 | 290.6 | 18.3 |
| pre | follow | NQ | 112365 | 8970 | 12766.0 | 0.7 | 601.0 | 537.0 | 64.0 |
| nyam | fade | ES | 262209 | 15232 | 9150.7 | 1.7 | 797.8 | 657.7 | 140.1 |
| nyam | fade | NQ | 262209 | 24279 | 21829.7 | 1.1 | 1547.8 | 1631.0 | -83.2 |
| nyam | follow | ES | 262209 | 9773 | 12355.3 | 0.8 | 855.5 | 736.0 | 119.5 |
| nyam | follow | NQ | 262209 | 22475 | 21580.3 | 1.0 | 1325.3 | 1565.1 | -239.8 |
| nypm | fade | ES | 149844 | 2514 | 2200.0 | 1.1 | 351.4 | 308.5 | 42.9 |
| nypm | fade | NQ | 149844 | 8109 | 6714.0 | 1.2 | 645.7 | 648.1 | -2.4 |
| nypm | follow | ES | 149844 | 2278 | 2081.7 | 1.1 | 316.3 | 363.9 | -47.6 |
| nypm | follow | NQ | 149844 | 7626 | 6802.0 | 1.1 | 554.1 | 547.3 | 6.8 |

### 3b. Tape-derived proxies (groups T_*; tape since 2025-07-21)
| sess | mode | inst | cells | gates | pl_gates | gate_ratio | bestS | pl_bestS | bestS_minus_placebo_max |
|---|---|---|---|---|---|---|---|---|---|
| asia | fade | ES | 32340 | 2600 | 3014.7 | 0.9 | 302.0 | 485.9 | -183.9 |
| asia | fade | NQ | 32340 | 4500 | 4789.3 | 0.9 | 795.7 | 1005.3 | -209.6 |
| asia | follow | ES | 32340 | 2116 | 1640.0 | 1.3 | 277.9 | 526.4 | -248.5 |
| asia | follow | NQ | 32340 | 3896 | 3417.3 | 1.1 | 1053.5 | 1155.1 | -101.7 |
| london | fade | ES | 32340 | 1664 | 1401.3 | 1.2 | 410.9 | 551.8 | -140.9 |
| london | fade | NQ | 32340 | 3600 | 3050.7 | 1.2 | 991.3 | 877.2 | 114.1 |
| london | follow | ES | 32340 | 1364 | 1214.7 | 1.1 | 384.3 | 487.1 | -102.7 |
| london | follow | NQ | 32340 | 2424 | 3040.0 | 0.8 | 848.0 | 997.0 | -148.9 |
| pre | fade | ES | 32340 | 3664 | 2061.3 | 1.8 | 195.2 | 222.0 | -26.9 |
| pre | fade | NQ | 32340 | 6036 | 3593.3 | 1.7 | 413.2 | 428.8 | -15.6 |
| pre | follow | ES | 32340 | 1164 | 2549.3 | 0.5 | 187.2 | 209.1 | -22.0 |
| pre | follow | NQ | 32340 | 2304 | 4530.7 | 0.5 | 373.2 | 499.2 | -126.0 |
| nyam | fade | ES | 73140 | 3212 | 3092.0 | 1.0 | 795.2 | 553.8 | 241.4 |
| nyam | fade | NQ | 73140 | 7024 | 7800.0 | 0.9 | 1280.9 | 1872.5 | -591.6 |
| nyam | follow | ES | 73140 | 3568 | 3610.7 | 1.0 | 865.0 | 657.0 | 208.0 |
| nyam | follow | NQ | 73140 | 8128 | 8085.3 | 1.0 | 1133.6 | 1347.6 | -214.0 |
| nypm | fade | ES | 40800 | 1344 | 602.7 | 2.2 | 246.5 | 116.1 | 130.4 |
| nypm | fade | NQ | 40800 | 3340 | 2214.7 | 1.5 | 506.0 | 264.6 | 241.4 |
| nypm | follow | ES | 40800 | 1184 | 712.0 | 1.7 | 156.6 | 142.4 | 14.2 |
| nypm | follow | NQ | 40800 | 3092 | 2317.3 | 1.3 | 342.2 | 363.3 | -21.1 |

### 3c. Best per session, NQ (ranked by the weakest window t-stat; n>=20 L6M/OLDER, >=8 L3M)
| session | g | mode | h | pool | stream | net_L3M | net_L6M | net_OLDER | n_L3M | n_L6M | n_OLDER | t_L6M | t_OLDER | St | exc_L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| asia | QQQ | fade | 60 | both | QQQ prem>=1000k nonsweep any aggr dte=any put carry q0.50 | 519.3 | 589.2 | 318.4 | 30.0 | 61.0 | 102.0 | 3.4 | 2.3 | 2.3 | 602.9 |
| asia | IWM | follow | SE | both | IWM prem>=50k any any aggr dte=1-5 put carry q0.75 | 1815.0 | 1376.8 | 551.8 | 16.0 | 28.0 | 78.0 | 2.2 | 2.3 | 2.2 | 1393.7 |
| asia | AAPL | fade | 5 | both | AAPL prem>=1000k nonsweep openP anyside dte=6+ call carry q0.50 | 284.6 | 242.8 | 586.9 | 19.0 | 28.0 | 22.0 | 2.7 | 2.1 | 2.1 | 256.9 |
| london | T_NDX | follow | SE | bull | T_NDX prem>=50k nonsweep any anyside dte=any put carry q0.50 | 1449.5 | 1014.7 | 848.0 | 17.0 | 35.0 | 36.0 | 2.6 | 2.8 | 2.6 | 972.9 |
| london | T_NDX | follow | SE | bull | T_NDX prem>=50k any any aggr dte=any put carry q0.50 | 1449.5 | 1014.7 | 848.0 | 17.0 | 35.0 | 36.0 | 2.6 | 2.8 | 2.6 | 972.9 |
| london | T_NDX | follow | SE | bull | T_NDX prem>=50k any any anyside dte=any put carry q0.50 | 1449.5 | 1014.7 | 848.0 | 17.0 | 35.0 | 36.0 | 2.6 | 2.8 | 2.6 | 972.9 |
| nyam | SPX | fade | 15 | bear | SPX prem>=250k any openP anyside dte=1-5 put burst1 | 926.3 | 745.2 | 524.1 | 15.0 | 31.0 | 50.0 | 2.8 | 3.0 | 2.7 | 745.6 |
| nyam | QQQ | follow | 60 | bull | QQQ prem>=50k sweep openP anyside dte=any put burst1 | 800.1 | 691.1 | 318.1 | 61.0 | 115.0 | 314.0 | 2.8 | 2.9 | 2.7 | 593.4 |
| nyam | T_SPX | fade | SE | bear | T_SPX prem>=250k nonsweep any aggr dte=0 put carry q0.75 | 3046.0 | 1867.6 | 1124.5 | 8.0 | 21.0 | 35.0 | 3.4 | 2.6 | 2.6 | 1683.2 |
| nypm | MEGA7 | follow | 60 | bear | MEGA7 prem>=50k any openP aggr dte=1-5 call burst3 | 1148.1 | 624.6 | 508.0 | 19.0 | 34.0 | 20.0 | 2.4 | 2.2 | 2.2 | 551.2 |
| nypm | IWM | fade | 60 | bull | IWM prem>=50k nonsweep any aggr dte=6+ call burst2 | 636.6 | 526.7 | 257.4 | 31.0 | 46.0 | 109.0 | 2.3 | 2.2 | 2.1 | 453.3 |
| nypm | SPY | follow | 15 | both | SPY prem>=250k any openP anyside dte=any call burst2 | 183.3 | 192.7 | 123.8 | 61.0 | 131.0 | 181.0 | 2.7 | 2.0 | 2.0 | 206.9 |
| pre | QQQ | fade | 15 | bull | QQQ prem>=50k any openP aggr dte=6+ both carry q0.50 | 523.6 | 325.8 | 164.5 | 17.0 | 30.0 | 93.0 | 2.6 | 2.7 | 2.6 | 328.8 |
| pre | QQQ | fade | 60 | bull | QQQ prem>=50k sweep openP anyside dte=6+ call carry q0.50 | 753.3 | 496.7 | 327.8 | 17.0 | 35.0 | 72.0 | 2.2 | 2.5 | 2.2 | 471.5 |
| pre | QQQ | fade | SE | bull | QQQ prem>=50k sweep openP anyside dte=6+ call carry q0.50 | 753.3 | 496.7 | 327.8 | 17.0 | 35.0 | 72.0 | 2.2 | 2.5 | 2.2 | 471.5 |

### 3c. Best per session, ES (ranked by the weakest window t-stat; n>=20 L6M/OLDER, >=8 L3M)
| session | g | mode | h | pool | stream | net_L3M | net_L6M | net_OLDER | n_L3M | n_L6M | n_OLDER | t_L6M | t_OLDER | St | exc_L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| asia | TSLA | follow | 60 | both | TSLA prem>=250k any any aggr dte=any both carry q0.75 | 228.2 | 183.1 | 147.2 | 14.0 | 31.0 | 104.0 | 2.1 | 2.0 | 2.0 | 212.5 |
| asia | IWM | follow | SE | both | IWM prem>=50k any openP aggr dte=any put carry q0.50 | 479.4 | 310.6 | 165.4 | 31.0 | 60.0 | 186.0 | 1.8 | 1.9 | 1.8 | 339.8 |
| asia | T_NDX | follow | 5 | both | T_NDX prem>=1000k nonsweep any aggr dte=0 put carry q0.50 | 276.4 | 213.7 | 138.1 | 12.0 | 29.0 | 23.0 | 2.4 | 2.0 | 1.8 | 243.5 |
| london | T_IWM | fade | SE | bear | T_IWM prem>=50k nonsweep any aggr dte=1-5 both carry q0.50 | 706.9 | 698.3 | 360.2 | 16.0 | 28.0 | 44.0 | 3.7 | 2.6 | 2.4 | 648.1 |
| london | T_IWM | fade | SE | bear | T_IWM prem>=50k nonsweep any anyside dte=1-5 both carry q0.50 | 706.9 | 698.3 | 360.2 | 16.0 | 28.0 | 44.0 | 3.7 | 2.6 | 2.4 | 648.1 |
| london | T_IWM | fade | SE | bear | T_IWM prem>=50k any any anyside dte=1-5 both carry q0.50 | 706.9 | 698.3 | 360.2 | 16.0 | 28.0 | 44.0 | 3.7 | 2.6 | 2.4 | 648.1 |
| nyam | T_SPX | fade | SE | bear | T_SPX prem>=50k any any anyside dte=0 put carry q0.75 | 1641.4 | 895.6 | 632.7 | 10.0 | 26.0 | 40.0 | 3.2 | 2.6 | 2.6 | 891.9 |
| nyam | T_SPX | fade | SE | bear | T_SPX prem>=50k nonsweep any aggr dte=0 put carry q0.75 | 1641.4 | 895.6 | 632.7 | 10.0 | 26.0 | 40.0 | 3.2 | 2.6 | 2.6 | 891.9 |
| nyam | T_SPX | fade | SE | bear | T_SPX prem>=50k nonsweep any anyside dte=0 put carry q0.75 | 1641.4 | 895.6 | 632.7 | 10.0 | 26.0 | 40.0 | 3.2 | 2.6 | 2.6 | 891.9 |
| nypm | AAPL | fade | 60 | both | AAPL prem>=50k sweep any aggr dte=1-5 call burst1 | 221.8 | 176.1 | 168.6 | 46.0 | 76.0 | 124.0 | 2.3 | 2.1 | 2.1 | 197.6 |
| nypm | IWM | fade | 60 | bull | IWM prem>=50k nonsweep any aggr dte=6+ call burst2 | 280.6 | 219.6 | 134.0 | 31.0 | 46.0 | 109.0 | 2.2 | 2.0 | 2.0 | 220.8 |
| nypm | MEGA7 | fade | 60 | both | MEGA7 prem>=1000k nonsweep openP anyside dte=any both burst3 | 622.9 | 368.0 | 156.2 | 9.0 | 23.0 | 43.0 | 2.7 | 1.9 | 1.9 | 389.1 |
| pre | AAPL | follow | 60 | bear | AAPL prem>=250k any any aggr dte=1-5 call carry q0.50 | 528.9 | 313.7 | 177.8 | 10.0 | 27.0 | 49.0 | 2.3 | 1.9 | 1.9 | 317.1 |
| pre | AAPL | follow | SE | bear | AAPL prem>=250k any any aggr dte=1-5 call carry q0.50 | 528.9 | 313.7 | 177.8 | 10.0 | 27.0 | 49.0 | 2.3 | 1.9 | 1.9 | 317.1 |
| pre | SPY | fade | 60 | bull | SPY prem>=50k nonsweep openP aggr dte=0 call carry q0.50 | 290.8 | 190.2 | 116.2 | 20.0 | 40.0 | 88.0 | 1.8 | 2.0 | 1.8 | 193.6 |


## 3d. Feature by feature (NQ, alert groups pooled, entry sessions as columns): cell = real gate passes / placebo mean gate passes ; mean net $ L6M real minus placebo (per cell average)
A feature value only matters if the ratio is clearly above 1 AND the net difference is positive in more than one session; values near 1.0 / 0 mean the feature adds nothing beyond the family noise. Fade and follow shown separately.

| feature | value | mode | asia | london | pre | nyam | nypm |
|---|---|---|---|---|---|---|---|
| premium floor | 1000000.0 | follow | 0.81 ; +10 | 0.98 ; +45 | 0.53 ; -44 | 0.90 ; -37 | 1.39 ; -18 |
| premium floor | 250000.0 | follow | 0.78 ; +12 | 1.09 ; +39 | 0.69 ; -0 | 1.03 ; -8 | 1.08 ; +20 |
| premium floor | 50000.0 | follow | 0.79 ; +2 | 1.14 ; +33 | 0.78 ; +10 | 1.10 ; -15 | 1.09 ; +10 |
| premium floor | 1000000.0 | fade | 1.66 ; -10 | 0.89 ; -45 | 1.38 ; +44 | 1.15 ; +37 | 1.24 ; +18 |
| premium floor | 250000.0 | fade | 1.24 ; -12 | 0.89 ; -39 | 1.13 ; +0 | 1.14 ; +8 | 1.10 ; -20 |
| premium floor | 50000.0 | fade | 1.29 ; -2 | 0.89 ; -33 | 1.07 ; -10 | 1.08 ; +15 | 1.27 ; -10 |

| feature | value | mode | asia | london | pre | nyam | nypm |
|---|---|---|---|---|---|---|---|
| sweep vs non-sweep (block-like) | any | follow | 0.74 ; -2 | 1.08 ; +40 | 0.70 ; -9 | 1.03 ; -37 | 1.16 ; +10 |
| sweep vs non-sweep (block-like) | nonsweep | follow | 0.84 ; -11 | 1.09 ; +24 | 0.72 ; +4 | 1.04 ; -46 | 1.12 ; +16 |
| sweep vs non-sweep (block-like) | sweep | follow | 0.80 ; +43 | 1.13 ; +51 | 0.69 ; -10 | 1.07 ; +47 | 1.05 ; -7 |
| sweep vs non-sweep (block-like) | any | fade | 1.37 ; +2 | 0.82 ; -40 | 1.15 ; +9 | 1.13 ; +37 | 1.25 ; -10 |
| sweep vs non-sweep (block-like) | nonsweep | fade | 1.34 ; +11 | 0.88 ; -24 | 0.99 ; -4 | 1.10 ; +46 | 1.27 ; -16 |
| sweep vs non-sweep (block-like) | sweep | fade | 1.24 ; -43 | 1.01 ; -51 | 1.37 ; +10 | 1.10 ; -47 | 1.04 ; +7 |

| feature | value | mode | asia | london | pre | nyam | nypm |
|---|---|---|---|---|---|---|---|
| opening proxy (all_opening or size>=25% of OI) | any | follow | 0.82 ; +0 | 1.20 ; +37 | 0.67 ; -20 | 0.98 ; -36 | 1.06 ; +13 |
| opening proxy (all_opening or size>=25% of OI) | openP | follow | 0.75 ; +15 | 0.97 ; +38 | 0.74 ; +13 | 1.14 ; +4 | 1.21 ; +1 |
| opening proxy (all_opening or size>=25% of OI) | any | fade | 1.41 ; -0 | 0.95 ; -37 | 1.24 ; +20 | 1.08 ; +36 | 1.28 ; -13 |
| opening proxy (all_opening or size>=25% of OI) | openP | fade | 1.22 ; -15 | 0.81 ; -38 | 1.02 ; -13 | 1.15 ; -4 | 1.11 ; -1 |

| feature | value | mode | asia | london | pre | nyam | nypm |
|---|---|---|---|---|---|---|---|
| ask/bid-side share | aggr | follow | 0.80 ; +4 | 1.09 ; +35 | 0.68 ; -7 | 1.02 ; -19 | 1.09 ; +10 |
| ask/bid-side share | any | follow | 0.78 ; +11 | 1.11 ; +41 | 0.72 ; -3 | 1.06 ; -15 | 1.15 ; +4 |
| ask/bid-side share | aggr | fade | 1.35 ; -4 | 0.91 ; -35 | 1.12 ; +7 | 1.11 ; +19 | 1.19 ; -10 |
| ask/bid-side share | any | fade | 1.30 ; -11 | 0.86 ; -41 | 1.16 ; +3 | 1.11 ; +15 | 1.22 ; -4 |

| feature | value | mode | asia | london | pre | nyam | nypm |
|---|---|---|---|---|---|---|---|
| DTE bucket | 0 | follow | 0.87 ; -23 | 1.22 ; +5 | 1.23 ; +67 | 1.05 ; -82 | 0.80 ; +26 |
| DTE bucket | 1-5 | follow | 0.77 ; +25 | 0.83 ; +57 | 0.97 ; +63 | 1.06 ; -21 | 1.05 ; +26 |
| DTE bucket | 6+ | follow | 0.82 ; +6 | 1.28 ; +29 | 0.56 ; -58 | 1.08 ; +7 | 1.29 ; -5 |
| DTE bucket | any | follow | 0.76 ; +9 | 1.09 ; +47 | 0.64 ; -30 | 0.99 ; -3 | 1.19 ; -6 |
| DTE bucket | 0 | fade | 1.72 ; +23 | 1.15 ; -5 | 0.87 ; -67 | 1.20 ; +82 | 1.15 ; -26 |
| DTE bucket | 1-5 | fade | 1.02 ; -25 | 1.20 ; -57 | 1.00 ; -63 | 1.34 ; +21 | 1.22 ; -26 |
| DTE bucket | 6+ | fade | 1.44 ; -6 | 0.74 ; -29 | 1.31 ; +58 | 1.01 ; -7 | 1.22 ; +5 |
| DTE bucket | any | fade | 1.33 ; -9 | 0.85 ; -47 | 1.18 ; +30 | 1.05 ; +3 | 1.22 ; +6 |

| feature | value | mode | asia | london | pre | nyam | nypm |
|---|---|---|---|---|---|---|---|
| call vs put | both | follow | 0.67 ; -12 | 1.00 ; +39 | 0.67 ; -13 | 1.01 ; -25 | 1.07 ; +2 |
| call vs put | call | follow | 0.65 ; -48 | 1.05 ; +3 | 0.68 ; -9 | 1.01 ; -7 | 1.04 ; -4 |
| call vs put | put | follow | 1.18 ; +88 | 1.30 ; +72 | 0.79 ; +10 | 1.12 ; -18 | 1.27 ; +26 |
| call vs put | both | fade | 1.45 ; +12 | 0.90 ; -39 | 1.18 ; +13 | 1.07 ; +25 | 1.22 ; -2 |
| call vs put | call | fade | 1.84 ; +48 | 0.99 ; -3 | 1.11 ; +9 | 1.18 ; +7 | 1.24 ; +4 |
| call vs put | put | fade | 0.86 ; -88 | 0.79 ; -72 | 1.13 ; -10 | 1.10 ; +18 | 1.16 ; -26 |

| feature | value | mode | asia | london | pre | nyam | nypm |
|---|---|---|---|---|---|---|---|
| burst n within 10 min (1 = first alert) | 0.5 | follow | 0.83 ; +9 | 1.10 ; +31 | 0.72 ; -4 | 0.93 ; -34 | - |
| burst n within 10 min (1 = first alert) | 0.75 | follow | 0.73 ; +6 | 1.09 ; +44 | 0.68 ; -5 | 0.94 ; -13 | - |
| burst n within 10 min (1 = first alert) | 1 | follow | - | - | - | 1.05 ; -31 | 1.03 ; -0 |
| burst n within 10 min (1 = first alert) | 2 | follow | - | - | - | 1.19 ; -0 | 1.29 ; +17 |
| burst n within 10 min (1 = first alert) | 3 | follow | - | - | - | 1.38 ; -0 | 1.13 ; +6 |
| burst n within 10 min (1 = first alert) | 0.5 | fade | 1.30 ; -9 | 0.86 ; -31 | 1.12 ; +4 | 1.11 ; +34 | - |
| burst n within 10 min (1 = first alert) | 0.75 | fade | 1.37 ; -6 | 0.93 ; -44 | 1.17 ; +5 | 1.00 ; +13 | - |
| burst n within 10 min (1 = first alert) | 1 | fade | - | - | - | 1.20 ; +31 | 1.18 ; +0 |
| burst n within 10 min (1 = first alert) | 2 | fade | - | - | - | 1.09 ; +0 | 1.13 ; -17 |
| burst n within 10 min (1 = first alert) | 3 | fade | - | - | - | 1.17 ; +0 | 1.41 ; -6 |


## 4. Trade level: harness screen (NOT the reported number) -> exact-engine injection (REPORTED)
Harness $/wk (standalone book, equal-$ risk lots) - the live gates cut standalone profit ~85%, so these are screens only.

| name | sess | mode | stream | best_cell | n_ev | mean_L3M | mean_L6M | mean_HOLD | mean_PREUW | dd_L6M | worst_L6M | stops_wk | pl_same_L6M | pl_best_L6M | wf_mean | wf_dd |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES_asia_TSLA_follow_10 | asia | follow | TSLA prem>=250k any any aggr dte=any both carry q0.75 | Emkt_S30_Ta2_XSE | 136 | 882.0 | 900.0 | 611.0 | -48.0 | 1219.0 | -1219.0 | 0.0 | -319,-701,-165 | 499,58,348 | 61.0 | 4700.0 |
| ES_london_T_IWM_fade_11 | london | fade | T_IWM prem>=50k nonsweep any aggr dte=1-5 both carry q0.50 | Emkt_S60_Tnone_XSE | 72 | 828.0 | 492.0 | 584.0 | nan | 2368.0 | -1184.0 | 0.0 | 104,-340,-24 | 959,196,610 | 119.0 | 4314.0 |
| ES_nyam_T_SPX_fade_13 | nyam | fade | T_SPX prem>=50k any any anyside dte=0 put carry q0.75 | Eb5_S60_T90_X120 | 67 | 700.0 | 552.0 | 264.0 | nan | 1184.0 | -1184.0 | 0.0 | 98,-34,11 | 188,566,1855 | 341.0 | 9413.0 |
| ES_nypm_AAPL_fade_14 | nypm | fade | AAPL prem>=50k sweep any aggr dte=1-5 call burst1 | Emkt_Sa2_T60_X60 | 578 | 1505.0 | 1033.0 | 466.0 | 193.0 | 1243.0 | -923.0 | 1.0 | -1,-280,185 | 417,306,333 | 8.0 | 8739.0 |
| ES_pre_AAPL_follow_12 | pre | follow | AAPL prem>=250k any any aggr dte=1-5 call carry q0.50 | Emkt_S60_T60_X60 | 78 | 446.0 | 320.0 | 304.0 | 35.0 | 1184.0 | -1184.0 | 0.0 | -114,211,99 | 123,489,352 | 38.0 | 2492.0 |
| NQ_asia_IWM_follow_1 | asia | follow | IWM prem>=50k any any aggr dte=1-5 put carry q0.75 | Eb3_S30_Tnone_XSE | 112 | 2847.0 | 1453.0 | 780.0 | 69.0 | 3682.0 | -1227.0 | 0.0 | 520,-106,-273 | 585,81,399 | 20.0 | 6121.0 |
| NQ_asia_QQQ_fade_0 | asia | fade | QQQ prem>=1000k nonsweep any aggr dte=any put carry q0.50 | Emkt_S90_Ta1_XSE | 169 | 685.0 | 530.0 | 289.0 | 70.0 | 1386.0 | -1334.0 | 0.0 | 139,-131,-8 | 204,489,402 | 109.0 | 5357.0 |
| NQ_london_GOOGL_follow_3 | london | follow | GOOGL prem>=50k any any anyside dte=6+ both carry q0.75 | Emkt_Sa2_T45_X60 | 157 | 1203.0 | 683.0 | 544.0 | 100.0 | 1459.0 | -1459.0 | 0.0 | -87,209,-180 | 52,501,343 | 220.0 | 3626.0 |
| NQ_london_T_NDX_follow_2 | london | follow | T_NDX prem>=50k any any aggr dte=any put carry q0.50 | Eb3_Sa2_T60_XSE | 74 | 101.0 | 413.0 | 210.0 | nan | 2493.0 | -2493.0 | 0.0 | -165,-188,429 | 11,163,660 | -21.0 | 5232.0 |
| NQ_nyam_QQQ_follow_7 | nyam | follow | QQQ prem>=50k sweep openP anyside dte=any put burst1 | Eb3_S90_T30_X120 | 848 | 90.0 | 548.0 | 268.0 | 97.0 | 1814.0 | -1814.0 | 0.0 | 193,-307,400 | 844,368,913 | 601.0 | 15324.0 |
| NQ_nyam_SPX_fade_6 | nyam | fade | SPX prem>=250k any openP anyside dte=1-5 put burst1 | Eb1_S30_Tnone_X30 | 168 | 1517.0 | 1361.0 | 710.0 | 252.0 | 2455.0 | -1227.0 | 0.0 | 614,-277,-274 | 702,401,511 | 157.0 | 3126.0 |
| NQ_nypm_IWM_fade_9 | nypm | fade | IWM prem>=50k nonsweep any aggr dte=6+ call burst2 | Emkt_Sa2_T30_X120 | 364 | 664.0 | 507.0 | 376.0 | 120.0 | 508.0 | -508.0 | 0.0 | 456,-178,154 | 1177,1031,445 | -30.0 | 9531.0 |
| NQ_nypm_MEGA7_follow_8 | nypm | follow | MEGA7 prem>=50k any openP aggr dte=1-5 call burst3 | Emkt_S45_Tnone_X120 | 143 | 1819.0 | 1111.0 | 571.0 | 99.0 | 1244.0 | -914.0 | 0.0 | 428,153,47 | 1103,254,207 | 196.0 | 1840.0 |
| NQ_pre_QQQ_fade_4 | pre | fade | QQQ prem>=50k any openP aggr dte=6+ both carry q0.50 | Eb1_Sa2_Ta2_X60 | 125 | 651.0 | 501.0 | 408.0 | 61.0 | 1006.0 | -1006.0 | 0.0 | -114,-1,37 | 156,376,391 | 203.0 | 2361.0 |
| NQ_pre_QQQ_fade_5 | pre | fade | QQQ prem>=50k sweep openP anyside dte=6+ call carry q0.50 | Eb1_Sa2_T30_X30 | 113 | 538.0 | 337.0 | 263.0 | 191.0 | 1105.0 | -1105.0 | 0.0 | -84,273,104 | 257,433,391 | 90.0 | 3587.0 |

### 4a. Every-day clock baseline (drift control, harness, same grid, one event per weekday at the session start; $/wk) - a trigger book must beat this, not zero

| session | direction | best_cell | L3M | L6M | HOLD | PREUW | dd_L6M | max_L6M_any_cell |
|---|---|---|---|---|---|---|---|---|
| asia | long | Emkt_S30_Ta1_X120 | 264.0 | 337.0 | 541.0 | -55.0 | 4533.0 | 481.0 |
| asia | short | Eb3_S45_Ta2_X120 | 481.0 | 524.0 | 213.0 | 28.0 | 1978.0 | 2265.0 |
| london | long | Eb3_S90_Ta2_X15 | 263.0 | 303.0 | 174.0 | 98.0 | 1456.0 | 936.0 |
| london | short | Eb3_S60_T30_X15 | 120.0 | 190.0 | 85.0 | -123.0 | 1298.0 | 1270.0 |
| pre | long | Eb3_S60_T60_X30 | 58.0 | 275.0 | 223.0 | -64.0 | 1633.0 | 394.0 |
| pre | short | Eb1_S30_T30_X60 | 1508.0 | 795.0 | 816.0 | 457.0 | 3756.0 | 1136.0 |
| nyam | long | Eb3_Sa2_T90_X120 | 1221.0 | 691.0 | 698.0 | 732.0 | 3018.0 | 1235.0 |
| nyam | short | Eb5_S30_Tnone_X60 | 2525.0 | 1992.0 | 1149.0 | -536.0 | 6136.0 | 2108.0 |
| nypm | long | Eb1_S90_T45_X60 | 372.0 | 488.0 | -63.0 | -18.0 | 3372.0 | 492.0 |
| nypm | short | Eb1_S90_Ta2_XSE | 1321.0 | 816.0 | 738.0 | 350.0 | 3998.0 | 1669.0 |

### 4b. Exact engine (JN05W2 base, all layers ON), windows L3M (2026-08..10), L6M (2026-05..10), OLDER = months 2025-11..2026-04 (the HOLD year minus L6M), PREUW = 2024-10..2025-06; a row appears only when ALL months of the window are done; stack vs reference on the same months: $/wk, max DD, worst week, full stops/wk, best-5 weeks kept, winning weeks turned losing
| set | desc | window | weeks | ref_mean | inj_mean | d_mean | ref_dd | inj_dd | ref_worst | inj_worst | ref_stops | inj_stops | best5_kept | w2l | uw1_mean | uw1_n |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TL3_UW_FA1 | BOOK NQ_nyam_SPX_fade_6 Eb1_S30_Tnone_X30 | L3M | 11 | 16819.4 | 16937.3 | 117.8 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.4 | 1.0 | 0 | 84.2 | 6.0 |
| TL3_UW_FA1 | BOOK NQ_nyam_SPX_fade_6 Eb1_S30_Tnone_X30 | L6M | 25 | 23240.9 | 23633.3 | 392.4 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.7 | 1.0 | 0 | 417.4 | 13.0 |
| TL3_UW_FA2 | BOOK NQ_asia_IWM_follow_1 Eb3_S30_Tnone_XSE | L3M | 11 | 16819.4 | 16679.2 | -140.2 | 36370.5 | 35467.9 | -36370.5 | -35467.9 | 11.3 | 11.8 | 1.0 | 0 | -65.2 | 10.0 |
| TL3_UW_FA2 | BOOK NQ_asia_IWM_follow_1 Eb3_S30_Tnone_XSE | L6M | 25 | 23240.9 | 23222.7 | -18.2 | 36370.5 | 35467.9 | -36370.5 | -35467.9 | 10.5 | 10.8 | 1.0 | 0 | 14.8 | 14.0 |
| TL3_UW_FA3 | BOOK NQ_london_GOOGL_follow_3 Emkt_Sa2_T45_X60 | L3M | 11 | 16819.4 | 17649.1 | 829.7 | 36370.5 | 33813.4 | -36370.5 | -33813.4 | 11.3 | 11.4 | 1.0 | 0 | 938.7 | 17.0 |
| TL3_UW_FA3 | BOOK NQ_london_GOOGL_follow_3 Emkt_Sa2_T45_X60 | L6M | 25 | 23240.9 | 23634.7 | 393.8 | 36370.5 | 33813.4 | -36370.5 | -33813.4 | 10.5 | 10.7 | 1.0 | 0 | 537.6 | 26.0 |
| TL3_UW_FA4 | BOOK NQ_pre_QQQ_fade_4 Eb1_Sa2_Ta2_X60 | L3M | 11 | 16819.4 | 17258.6 | 439.1 | 36370.5 | 35361.7 | -36370.5 | -35361.7 | 11.3 | 11.4 | 1.0 | 0 | 439.1 | 7.0 |
| TL3_UW_FA4 | BOOK NQ_pre_QQQ_fade_4 Eb1_Sa2_Ta2_X60 | L6M | 25 | 23240.9 | 23603.8 | 362.9 | 36370.5 | 35361.7 | -36370.5 | -35361.7 | 10.5 | 10.6 | 1.0 | 0 | 362.9 | 13.0 |
| TL3_UW_FA5 | BOOK NQ_asia_QQQ_fade_0 Emkt_S90_Ta1_XSE | L3M | 11 | 16819.4 | 16125.5 | -694.0 | 36370.5 | 34339.6 | -36370.5 | -34284.4 | 11.3 | 11.6 | 1.0 | 0 | -227.1 | 24.0 |
| TL3_UW_FA5 | BOOK NQ_asia_QQQ_fade_0 Emkt_S90_Ta1_XSE | L6M | 25 | 23240.9 | 23276.6 | 35.7 | 36370.5 | 34339.6 | -36370.5 | -34284.4 | 10.5 | 10.8 | 1.0 | 0 | 112.0 | 55.0 |
| TL3_UW_FA6 | BOOK NQ_nypm_MEGA7_follow_8 Emkt_S45_Tnone_X120 | L3M | 11 | 16819.4 | 16964.0 | 144.6 | 36370.5 | 35336.7 | -36370.5 | -35336.7 | 11.3 | 11.6 | 1.0 | 0 | 144.6 | 8.0 |
| TL3_UW_FA6 | BOOK NQ_nypm_MEGA7_follow_8 Emkt_S45_Tnone_X120 | L6M | 25 | 23240.9 | 23445.7 | 204.8 | 36370.5 | 35336.7 | -36370.5 | -35336.7 | 10.5 | 10.8 | 1.0 | 0 | 204.8 | 17.0 |
| TL3_UW_FF1 | FILTER {'feat': 'TSLA/AGG/1440', 'rule': 'skipOpp', 'thr': 17258967.3, 'act': 'skip', 'seg': 'all'} | L3M | 11 | 16819.4 | 20433.8 | 3614.4 | 36370.5 | 25922.6 | -36370.5 | -25922.6 | 11.3 | 10.9 | 1.0 | 0 | nan | nan |
| TL3_UW_FF2 | FILTER {'feat': 'MSFT/D15/1440', 'rule': 'skipAl', 'thr': 425092.0, 'act': 'skip', 'seg': 'asia'} | L3M | 11 | 16819.4 | 17162.9 | 343.5 | 36370.5 | 29825.7 | -36370.5 | -15870.2 | 11.3 | 9.9 | 0.9 | 2 | nan | nan |

### 4c. Exact placebo: same book/filter with events (features) shifted 11 / 23 / 37 weekdays, run through the same exact engine (delta vs JN05W2 on the same months, $/wk and max DD $)

| set | desc | L3M_real dMean/dDD | L6M_real dMean/dDD | beats all 3 placebos in L6M and OLDER (DD and mean) |
|---|---|---|---|---|
| TL3_UW_FA1 | BOOK NQ_nyam_SPX_fade_6 Eb1_S30_Tnone_X30 | +118 / -0 | +392 / +0 | pending |
| TL3_UW_FA2 | BOOK NQ_asia_IWM_follow_1 Eb3_S30_Tnone_XSE | -140 / -903 | -18 / -903 | pending |
| TL3_UW_FA3 | BOOK NQ_london_GOOGL_follow_3 Emkt_Sa2_T45_X60 | +830 / -2557 | +394 / -2557 | pending |
| TL3_UW_FA4 | BOOK NQ_pre_QQQ_fade_4 Eb1_Sa2_Ta2_X60 | +439 / -1009 | +363 / -1009 | pending |
| TL3_UW_FF1 | FILTER {'feat': 'TSLA/AGG/1440', 'rule': 'skipOpp', 'thr': 17258967.3, 'act': 'skip', 'seg': 'all'} | +3614 / -10448 | nan | pending |
| TL3_UW_FF2 | FILTER {'feat': 'MSFT/D15/1440', 'rule': 'skipAl', 'thr': 425092.0, 'act': 'skip', 'seg': 'asia'} | +343 / -6545 | nan | pending |
| TL3_UW_FF3 | FILTER {'feat': 'SPY/D15/1440', 'rule': 'skipOpp', 'thr': 1504430.0, 'act': 'skip', 'seg': 'london'} | nan | nan | pending |
| TL3_UW_FF4 | FILTER {'feat': 'AAPL/SWP/1440', 'rule': 'skipAct', 'thr': 4034864.5, 'act': 'skip', 'seg': 'all'} | nan | nan | pending |


## 5. Filters on the live books (JN05W2 trades, first-order trade removal; exact-engine skip/size hook runs follow)
Features are signed alert premium (calls/ask-side/puts-bid-side direction) in trailing windows 5/15/60/1440 min at the signal second, aligned with the trade side (>0 flow agrees with the trade). Rules: skip or half-size when flow is OPPOSED (skipOpp) or ALIGNED (skipAl) beyond thr (0 = any sign, else quantile 50/75/90 of |feature|). Segments asia / london / rth (pre+NY) / all. Metrics are deltas versus JN05W2 for L3M, L6M, OLDER (before L6M start, from 2024-10); DD-first gate: max DD smaller, worst week not worse, mean not lower by more than 3% in ALL THREE windows.

Family null (same rules, features queried k weekdays away): 

| shift | rules | gate_pass | best_score_gated | best_score_any |
|---|---|---|---|---|
| 0.0 | 24488.0 | 749.0 | 0.3 | 0.5 |
| 11.0 | 24518.0 | 417.0 | 0.3 | 0.4 |
| 23.0 | 24494.0 | 213.0 | 0.2 | 0.4 |
| 37.0 | 24482.0 | 64.0 | 0.3 | 0.5 |

Best gated rules per segment (score = mean relative DD improvement over the 3 windows):

| feat | seg | rule | act | q | nrem | sc | dd_L3M | dd_L6M | dd_OLDER | worst_L6M | mean_L3M | mean_L6M | mean_OLDER | mean_removed | imp_L6M | imp_OLDER |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TSLA/AGG/1440 | all | skipOpp | skip | 3 | 511 | 0.3 | -12066.6 | -12066.6 | -9258.7 | 12066.6 | 2290.8 | 1952.0 | -294.6 | -54.1 | 0.8 | 0.6 |
| AAPL/SWP/1440 | all | skipAct | skip | 3 | 1097 | 0.3 | -13569.1 | -11057.9 | -7239.5 | 11057.9 | -126.2 | 241.8 | -173.8 | 7.5 | 0.6 | 0.5 |
| TSLA/ALL/1440 | all | skipOpp | skip | 3 | 529 | 0.2 | -12066.6 | -11057.9 | -7239.5 | 11057.9 | 1683.6 | 504.0 | -332.2 | 27.7 | 0.5 | 0.5 |
| IWM/AGG/1440 | asia | skipAct | skip | 3 | 526 | 0.2 | -11386.0 | -11057.9 | -7239.5 | 11057.9 | 1192.8 | 71.3 | 677.1 | -113.1 | 0.7 | 0.6 |
| IWM/AGG/1440 | all | skipAct | skip | 3 | 1104 | 0.2 | -12716.6 | -9859.1 | -6019.3 | 9859.1 | 413.3 | -497.5 | 477.5 | -24.6 | 0.6 | 0.8 |
| MSFT/D15/1440 | asia | skipAl | skip | 1 | 864 | 0.2 | -18466.8 | -3443.8 | -7239.5 | 3443.8 | 716.0 | 387.8 | 611.1 | -72.2 | 0.6 | 0.7 |
| AAPL/ALL/1440 | asia | skipAl | skip | 3 | 274 | 0.2 | -10003.3 | -10003.3 | -7239.5 | 10003.3 | 206.5 | 203.9 | 659.8 | -224.8 | 0.6 | 0.7 |
| QQQ/AGG/1440 | asia | skipOpp | skip | 0 | 2040 | 0.2 | -9110.8 | -9110.8 | -6792.8 | 9110.8 | 2252.1 | -543.9 | -214.0 | 16.1 | 0.6 | 0.5 |
| IWM/ALL/1440 | london | skipAl | skip | 1 | 919 | 0.2 | -10255.0 | -9419.5 | -1568.7 | 9419.5 | 775.6 | -617.9 | 605.9 | -37.9 | 0.4 | 0.6 |
| TSLA/AGG/1440 | london | skipAct | skip | 3 | 320 | 0.2 | -6149.1 | -6149.1 | -10185.1 | 6149.1 | 1495.5 | 1046.7 | 392.7 | -192.6 | 1.0 | 0.6 |
| MEGA7/D6P/1440 | london | skipAct | skip | 3 | 348 | 0.1 | -5837.1 | -5837.1 | -8704.7 | 6149.1 | 1045.2 | 497.4 | 123.1 | -68.7 | 0.5 | 0.5 |
| AAPL/SWP/1440 | london | skipAct | skip | 3 | 357 | 0.1 | -6149.1 | -6149.1 | -7239.5 | 6149.1 | 399.9 | 473.7 | -236.4 | 20.5 | 0.7 | 0.5 |
| MEGA7/AGG/5 | rth | skipOpp | skip | 0 | 1320 | 0.1 | -712.2 | -712.2 | -8470.5 | 712.2 | 752.5 | -391.1 | -328.4 | 29.1 | 0.5 | 0.5 |
| SPY/CALL/1440 | rth | skipOpp | skip | 1 | 651 | 0.1 | -2088.0 | -2088.0 | -2406.9 | 2088.0 | 78.2 | 397.1 | 392.3 | -67.7 | 0.7 | 0.6 |
| QQQ/D0/1440 | rth | skipAct | skip | 2 | 584 | 0.1 | -2088.0 | -2088.0 | -2159.9 | 2088.0 | 882.6 | 672.2 | -12.3 | -29.3 | 0.7 | 0.5 |
| AAPL/PUT/1440 | rth | skipAl | skip | 1 | 794 | 0.1 | -2088.0 | -2088.0 | -1753.3 | 2088.0 | 1073.7 | -537.9 | 440.9 | -28.9 | 0.7 | 0.6 |

Reference JN05W2 (same trades): 

| window | mean | dd | worst | stops | best5 | w2l | n | imp |
|---|---|---|---|---|---|---|---|---|
| L3M | 13705.0 | 36371.0 | -36371.0 | 9.0 | 1.0 | 0.0 | 1612.0 | 0.0 |
| L6M | 23154.0 | 36371.0 | -36371.0 | 10.0 | 1.0 | 0.0 | 3965.0 | 0.0 |
| OLDER | 11912.0 | 76186.0 | -68947.0 | 10.0 | 1.0 | 0.0 | 9547.0 | 0.0 |
| HOLD | 17215.0 | 63185.0 | -55145.0 | 10.0 | 1.0 | 0.0 | 7284.0 | 0.0 |
| PREUW | 11570.0 | 76186.0 | -52547.0 | 9.0 | 1.0 | 0.0 | 4383.0 | 0.0 |
