# DS3_UW_FLOWALERTS - UW flow alerts as entry triggers and filters (W-FA)

**VERDICT: weak/null-level so far, no PASS - first-order streams: 253944 sign-gate passes vs 242939 in the shifted-event placebos (ratio 1.05); exact-engine runs still queued (shared admission). Flow-alert triggers and filters are NOT a lead unless the table in section 4b/5 shows a set that beats its placebo in BOTH windows.**

Updated 2026-11-14T00:40Z by fa_cycle.sh (loop, every 3 h). Research/shadow only. No PASS claims. Prereg: autopilot/FLOWALERTS_PREREG.md (sha in DECISIONS.md).

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
(exact runs queued/waiting for admission - none finished yet)


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
| TSLA|AGG|1440 | all | skipOpp | skip | 3 | 511 | 0.3 | -12066.6 | -12066.6 | -9258.7 | 12066.6 | 2290.8 | 1952.0 | -294.6 | -54.1 | 0.8 | 0.6 |
| AAPL|SWP|1440 | all | skipAct | skip | 3 | 1097 | 0.3 | -13569.1 | -11057.9 | -7239.5 | 11057.9 | -126.2 | 241.8 | -173.8 | 7.5 | 0.6 | 0.5 |
| TSLA|ALL|1440 | all | skipOpp | skip | 3 | 529 | 0.2 | -12066.6 | -11057.9 | -7239.5 | 11057.9 | 1683.6 | 504.0 | -332.2 | 27.7 | 0.5 | 0.5 |
| IWM|AGG|1440 | asia | skipAct | skip | 3 | 526 | 0.2 | -11386.0 | -11057.9 | -7239.5 | 11057.9 | 1192.8 | 71.3 | 677.1 | -113.1 | 0.7 | 0.6 |
| IWM|AGG|1440 | all | skipAct | skip | 3 | 1104 | 0.2 | -12716.6 | -9859.1 | -6019.3 | 9859.1 | 413.3 | -497.5 | 477.5 | -24.6 | 0.6 | 0.8 |
| MSFT|D15|1440 | asia | skipAl | skip | 1 | 864 | 0.2 | -18466.8 | -3443.8 | -7239.5 | 3443.8 | 716.0 | 387.8 | 611.1 | -72.2 | 0.6 | 0.7 |
| AAPL|ALL|1440 | asia | skipAl | skip | 3 | 274 | 0.2 | -10003.3 | -10003.3 | -7239.5 | 10003.3 | 206.5 | 203.9 | 659.8 | -224.8 | 0.6 | 0.7 |
| QQQ|AGG|1440 | asia | skipOpp | skip | 0 | 2040 | 0.2 | -9110.8 | -9110.8 | -6792.8 | 9110.8 | 2252.1 | -543.9 | -214.0 | 16.1 | 0.6 | 0.5 |
| IWM|ALL|1440 | london | skipAl | skip | 1 | 919 | 0.2 | -10255.0 | -9419.5 | -1568.7 | 9419.5 | 775.6 | -617.9 | 605.9 | -37.9 | 0.4 | 0.6 |
| TSLA|AGG|1440 | london | skipAct | skip | 3 | 320 | 0.2 | -6149.1 | -6149.1 | -10185.1 | 6149.1 | 1495.5 | 1046.7 | 392.7 | -192.6 | 1.0 | 0.6 |
| MEGA7|D6P|1440 | london | skipAct | skip | 3 | 348 | 0.1 | -5837.1 | -5837.1 | -8704.7 | 6149.1 | 1045.2 | 497.4 | 123.1 | -68.7 | 0.5 | 0.5 |
| AAPL|SWP|1440 | london | skipAct | skip | 3 | 357 | 0.1 | -6149.1 | -6149.1 | -7239.5 | 6149.1 | 399.9 | 473.7 | -236.4 | 20.5 | 0.7 | 0.5 |
| MEGA7|AGG|5 | rth | skipOpp | skip | 0 | 1320 | 0.1 | -712.2 | -712.2 | -8470.5 | 712.2 | 752.5 | -391.1 | -328.4 | 29.1 | 0.5 | 0.5 |
| SPY|CALL|1440 | rth | skipOpp | skip | 1 | 651 | 0.1 | -2088.0 | -2088.0 | -2406.9 | 2088.0 | 78.2 | 397.1 | 392.3 | -67.7 | 0.7 | 0.6 |
| QQQ|D0|1440 | rth | skipAct | skip | 2 | 584 | 0.1 | -2088.0 | -2088.0 | -2159.9 | 2088.0 | 882.6 | 672.2 | -12.3 | -29.3 | 0.7 | 0.5 |
| AAPL|PUT|1440 | rth | skipAl | skip | 1 | 794 | 0.1 | -2088.0 | -2088.0 | -1753.3 | 2088.0 | 1073.7 | -537.9 | 440.9 | -28.9 | 0.7 | 0.6 |

Reference JN05W2 (same trades): 

| window | mean | dd | worst | stops | best5 | w2l | n | imp |
|---|---|---|---|---|---|---|---|---|
| L3M | 13705.0 | 36371.0 | -36371.0 | 9.0 | 1.0 | 0.0 | 1612.0 | 0.0 |
| L6M | 23154.0 | 36371.0 | -36371.0 | 10.0 | 1.0 | 0.0 | 3965.0 | 0.0 |
| OLDER | 11912.0 | 76186.0 | -68947.0 | 10.0 | 1.0 | 0.0 | 9547.0 | 0.0 |
| HOLD | 17215.0 | 63185.0 | -55145.0 | 10.0 | 1.0 | 0.0 | 7284.0 | 0.0 |
| PREUW | 11570.0 | 76186.0 | -52547.0 | 9.0 | 1.0 | 0.0 | 4383.0 | 0.0 |
