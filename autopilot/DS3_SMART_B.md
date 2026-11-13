# DS3_SMART_B - T-SMART items B1/B2/B3/B5 (W-SM4)

Shadow only. No PASS claims. Prereg: SMART_B_PREREG.md (sha line in DECISIONS.md). **Caveat on every page: the engine state cut fires in the engine but did not fire live on 2026-11-11 (DS3_P7_CUT_FIDELITY.md); every cut-dependent number below describes a cut that is not running live.**

## B1. COST AUDIT (delivered before any rule)

Base: exact JN05W2 trade list (live panel base + F3+E1+C22+BR3S+FLAT45K), L6M = 202605..202610 (26.0 weeks) and HOLD = 202511..202604 (25.5 weeks). Code code/th_smart_b/b1_cost_audit.py, tables /mnt/l2/l2vast/_smart_b/b1_*.csv.

**Method.** cost$ = fees + live-excess slip. Fees = **$4.84 per contract round trip** (FEES.md standard; NB the engine files carry net_fee at $1.18/contract, the NT commission-only figure, so engine net_fee understates cost by $3.66/contract; every number here uses 4.84). Live-excess slip = live minus engine fill model, measured on the 187 frozen live trades and the DN stop-fill study: entry market slices +0.23 pt (FILL_MODEL_V3 tie-out), market cut-type exits +0.40 pt (live 1.19-1.20 vs engine 0.80), stop exits +0.44 pt (DN_STOPFILL 1.44 vs engine 1.0), targets 0 (85 of 86 live targets filled at nominal), plus +1.36 pt on market/stop exits that start 08:30-08:44 ET (DN_STOPFILL H0830 contrast). Engine-modelled slip (cuts 0.80, stops 1.0) is already inside gross and is shown separately (column mod). **Limits:** the slip parameters are means from one live week (cuts n=99, entries n=149, stops n=2 plus the DN replay), not per-slot measurements; take-side slip is unmeasured (set 0); entry slip vs the signal mid is not separable here. Cost per contract is lot-invariant, so the cost-per-contract rows transfer unchanged to the user's lots; per-trade rows scale with lots (K7 4, M7 4, U7 7, P7 12/7/7, H7 7, A7 2 are 1.1-3.5x the cell lots).

### B1.0 Cost per contract by order type
| order type | fee $/contract RT | live-excess slip pt | live-excess $/contract | engine-modelled slip pt (inside gross) |
|---|---|---|---|---|
| entry market slice (each contract) | 4.84 | 0.23 | 4.60 | first print signal+1 s |
| target exit | incl. | 0.00 | 0 | 0 |
| market cut-type exit (StateCut, EarlyCut, StackCut, BookLock, TimeBlock) | incl. | 0.40 | 8.00 | 0.80 |
| stop exit (Stop, StopJoin, StopJoinFallback) | incl. | 0.44 | 8.80 | 1.00 |
| 08:30-08:44 ET market/stop exit | incl. | +1.36 | +27.2 | n/a |

Whole round trip per contract (fee + excess): target 9.4; cut 17.4; stop 18.2; 08:30 cut/stop 44.6.

### B1.1 By book, L6M
| book | n | lots | gross | fee | exc | mod | cost | net | cost_per_trade | cost/contract $ | cost_pct_gross | gross/wk $ | cost/wk $ |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 | 353 | 353.0 | 20714.0 | 1708.5 | 3182.2 | 3312.0 | 4890.7 | 15823.3 | 13.9 | 13.9 | 23.6 | 796.7 | 188.1 |
| H7 | 176 | 329.0 | 53349.5 | 1592.4 | 2971.0 | 2992.0 | 4563.4 | 48786.1 | 25.9 | 13.9 | 8.60 | 2051.9 | 175.5 |
| K7 | 1553 | 1780.0 | 132978.0 | 8615.2 | 16666.4 | 15952.0 | 25281.6 | 107696.4 | 16.3 | 14.2 | 19.0 | 5114.5 | 972.4 |
| M7 | 733 | 874.0 | 2181.0 | 4230.2 | 8605.2 | 8660.0 | 12835.4 | -10654.4 | 17.5 | 14.7 | 588.5 | 83.9 | 493.7 |
| O7 | 46 | 46.0 | 10742.0 | 222.6 | 471.6 | 556.0 | 694.2 | 10047.8 | 15.1 | 15.1 | 6.50 | 413.2 | 26.7 |
| P7 | 1037 | 3469.0 | 344598.5 | 16790.0 | 32491.8 | 32216.0 | 49281.8 | 295316.7 | 47.5 | 14.2 | 14.3 | 13253.8 | 1895.5 |
| U7 | 271 | 731.0 | 105205.5 | 3538.0 | 6395.4 | 6412.0 | 9933.4 | 95272.1 | 36.7 | 13.6 | 9.40 | 4046.4 | 382.1 |

### B1.1 By book, HOLD
| book | n | lots | gross | fee | exc | mod | cost | net | cost_per_trade | cost/contract $ | cost_pct_gross | gross/wk $ | cost/wk $ |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 | 211 | 211.0 | 21519.5 | 1021.2 | 1902.6 | 1916.0 | 2923.8 | 18595.7 | 13.9 | 13.9 | 13.6 | 843.9 | 114.7 |
| H7 | 131 | 251.0 | -17527.5 | 1214.8 | 2519.4 | 2784.0 | 3734.2 | -21261.7 | 28.5 | 14.9 | nan | -687.4 | 146.4 |
| K7 | 1194 | 1399.0 | 53270.0 | 6771.2 | 13306.6 | 12844.0 | 20077.8 | 33192.2 | 16.8 | 14.4 | 37.7 | 2089.0 | 787.4 |
| M7 | 675 | 805.0 | -2765.0 | 3896.2 | 8345.4 | 8068.0 | 12241.6 | -15006.6 | 18.1 | 15.2 | nan | -108.4 | 480.1 |
| O7 | 58 | 58.0 | 17614.0 | 280.7 | 584.4 | 676.0 | 865.1 | 16748.9 | 14.9 | 14.9 | 4.90 | 690.7 | 33.9 |
| P7 | 801 | 2694.0 | 206462.5 | 13039.0 | 25730.0 | 25456.0 | 38769.0 | 167693.5 | 48.4 | 14.4 | 18.8 | 8096.6 | 1520.4 |
| U7 | 213 | 559.0 | 19923.5 | 2705.6 | 5265.8 | 5520.0 | 7971.4 | 11952.1 | 37.4 | 14.3 | 40.0 | 781.3 | 312.6 |

### B1.2 By book x session, L6M (cost_pct_gross blank = gross <= 0)
| book | sess | n | lots | gross | fee | exc | cost | net | cost_per_trade | cost_pct_gross |
|---|---|---|---|---|---|---|---|---|---|---|
| A7 | asia | 353 | 353.0 | 20714.0 | 1708.5 | 3182.2 | 4890.7 | 15823.3 | 13.9 | 23.6 |
| H7 | asia | 140 | 293.0 | 48496.5 | 1418.1 | 2652.6 | 4070.7 | 44425.8 | 29.1 | 8.40 |
| H7 | nyam | 36 | 36.0 | 4853.0 | 174.2 | 318.4 | 492.6 | 4360.4 | 13.7 | 10.2 |
| K7 | asia | 787 | 925.0 | 70387.5 | 4477.0 | 8415.0 | 12892.0 | 57495.5 | 16.4 | 18.3 |
| K7 | london | 427 | 488.0 | 11891.5 | 2361.9 | 4984.8 | 7346.7 | 4544.8 | 17.2 | 61.8 |
| K7 | nyam | 188 | 188.0 | 5175.0 | 909.9 | 1745.6 | 2655.5 | 2519.5 | 14.1 | 51.3 |
| K7 | nypm | 151 | 179.0 | 45524.0 | 866.4 | 1521.0 | 2387.4 | 43136.6 | 15.8 | 5.20 |
| M7 | london | 519 | 660.0 | -8433.0 | 3194.4 | 6620.0 | 9814.4 | -18247.4 | 18.9 | nan |
| M7 | nyam | 214 | 214.0 | 10614.0 | 1035.8 | 1985.2 | 3021.0 | 7593.0 | 14.1 | 28.5 |
| O7 | nyam | 46 | 46.0 | 10742.0 | 222.6 | 471.6 | 694.2 | 10047.8 | 15.1 | 6.50 |
| P7 | asia | 575 | 2472.0 | 316184.0 | 11964.5 | 22482.4 | 34446.9 | 281737.1 | 59.9 | 10.9 |
| P7 | london | 346 | 755.0 | 14035.5 | 3654.2 | 7734.6 | 11388.8 | 2646.7 | 32.9 | 81.1 |
| P7 | nyam | 116 | 242.0 | 14379.0 | 1171.3 | 2274.8 | 3446.1 | 10932.9 | 29.7 | 24.0 |
| U7 | asia | 157 | 437.0 | 66271.5 | 2115.1 | 3748.6 | 5863.7 | 60407.8 | 37.3 | 8.80 |
| U7 | london | 114 | 294.0 | 38934.0 | 1423.0 | 2646.8 | 4069.8 | 34864.2 | 35.7 | 10.5 |

### B1.3 By book x exit type, L6M ($ per trade, per contract)
| book | xt | n | lots | gross | cost | net | cost_per_trade | per_contract | net_per_trade |
|---|---|---|---|---|---|---|---|---|---|
| A7 | cut | 77 | 77.0 | -62841.0 | 1370.1 | -64211.1 | 17.8 | 17.8 | -833.9 |
| A7 | stop | 104 | 104.0 | -122845.0 | 1897.0 | -124742.0 | 18.2 | 18.2 | -1199.4 |
| A7 | target | 172 | 172.0 | 206400.0 | 1623.7 | 204776.3 | 9.40 | 9.44 | 1190.6 |
| H7 | cut | 72 | 147.0 | -83620.5 | 2563.7 | -86184.2 | 35.6 | 17.4 | -1197.0 |
| H7 | stop | 22 | 32.0 | -35685.0 | 583.7 | -36268.7 | 26.5 | 18.2 | -1648.6 |
| H7 | target | 82 | 150.0 | 172655.0 | 1416.0 | 171239.0 | 17.3 | 9.44 | 2088.3 |
| K7 | cut | 860 | 982.0 | -794932.0 | 17588.5 | -812520.5 | 20.5 | 17.9 | -944.8 |
| K7 | stop | 12 | 12.0 | -11185.0 | 273.3 | -11458.3 | 22.8 | 22.8 | -954.9 |
| K7 | target | 681 | 786.0 | 939095.0 | 7419.8 | 931675.2 | 10.9 | 9.44 | 1368.1 |
| M7 | cut | 410 | 495.0 | -364769.0 | 8877.6 | -373646.6 | 21.7 | 17.9 | -911.3 |
| M7 | stop | 33 | 37.0 | -43465.0 | 729.3 | -44194.3 | 22.1 | 19.7 | -1339.2 |
| M7 | target | 290 | 342.0 | 410415.0 | 3228.5 | 407186.5 | 11.1 | 9.44 | 1404.1 |
| O7 | cut | 16 | 16.0 | -5538.0 | 279.0 | -5817.0 | 17.4 | 17.4 | -363.6 |
| O7 | stop | 15 | 15.0 | -10720.0 | 273.6 | -10993.6 | 18.2 | 18.2 | -732.9 |
| O7 | target | 15 | 15.0 | 27000.0 | 141.6 | 26858.4 | 9.40 | 9.44 | 1790.6 |
| P7 | cut | 582 | 1976.0 | -1350691.5 | 34869.4 | -1385560.9 | 59.9 | 17.6 | -2380.7 |
| P7 | stop | 13 | 30.0 | -33245.0 | 601.6 | -33846.6 | 46.3 | 20.1 | -2603.6 |
| P7 | target | 442 | 1463.0 | 1728535.0 | 13810.7 | 1714724.3 | 31.2 | 9.44 | 3879.5 |
| U7 | cut | 42 | 107.0 | -75864.5 | 1866.1 | -77730.6 | 44.4 | 17.4 | -1850.7 |
| U7 | stop | 90 | 235.0 | -279730.0 | 4395.2 | -284125.2 | 48.8 | 18.7 | -3156.9 |
| U7 | target | 139 | 389.0 | 460800.0 | 3672.2 | 457127.8 | 26.4 | 9.44 | 3288.7 |

### B1.4 Slots (book x session x 30-min ET entry slot, n >= 15) L6M
**(a) cost > positive gross edge: 4 slots**
| book | sess | slot | n | lots | gross | cost | net | cost_pct_gross |
|---|---|---|---|---|---|---|---|---|
| P7 | london | 05:30 | 25 | 58.0 | 62.5 | 845.1 | -782.6 | 1352.2 |
| K7 | asia | 01:00 | 40 | 52.0 | 7.50 | 738.9 | -731.4 | 9851.7 |
| P7 | london | 02:00 | 19 | 43.0 | 246.5 | 613.9 | -367.4 | 249.1 |
| M7 | nyam | 11:00 | 41 | 41.0 | 277.5 | 587.0 | -309.5 | 211.5 |

**(b) cost = 40% or more of positive gross: 4 slots (worst 25)**
| book | sess | slot | n | lots | gross | cost | net | cost_pct_gross |
|---|---|---|---|---|---|---|---|---|
| P7 | asia | 20:30 | 50 | 217.0 | 3763.5 | 3122.1 | 641.4 | 83.0 |
| P7 | london | 04:30 | 33 | 77.0 | 2181.5 | 1112.5 | 1069.0 | 51.0 |
| K7 | london | 04:00 | 46 | 46.0 | 1317.5 | 670.2 | 647.3 | 50.9 |
| K7 | london | 05:00 | 29 | 29.0 | 984.0 | 410.6 | 573.4 | 41.7 |

**(c) gross <= 0 before any cost (worst 15 of 39 slots)**
| book | sess | slot | n | lots | gross | cost | net |
|---|---|---|---|---|---|---|---|
| P7 | asia | 22:00 | 46 | 190.0 | -19164.5 | 2873.6 | -22038.1 |
| P7 | asia | 20:00 | 44 | 159.0 | -16254.0 | 2389.0 | -18643.0 |
| P7 | asia | 19:30 | 28 | 115.0 | -15394.0 | 1677.6 | -17071.6 |
| P7 | asia | 21:30 | 36 | 161.0 | -15281.5 | 2391.8 | -17673.3 |
| U7 | london | 03:00 | 18 | 46.0 | -14695.5 | 705.4 | -15400.9 |
| P7 | asia | 23:30 | 25 | 110.0 | -13613.0 | 1662.4 | -15275.4 |
| M7 | london | 06:30 | 32 | 37.0 | -12723.0 | 609.3 | -13332.3 |
| A7 | asia | 19:30 | 18 | 18.0 | -12169.0 | 297.1 | -12466.1 |
| P7 | london | 04:00 | 38 | 82.0 | -11947.5 | 1246.1 | -13193.6 |
| M7 | london | 07:00 | 40 | 46.0 | -11597.5 | 762.2 | -12359.7 |
| P7 | london | 06:30 | 26 | 57.0 | -11510.5 | 882.1 | -12392.6 |
| A7 | asia | 21:00 | 40 | 40.0 | -10625.5 | 596.8 | -11222.3 |
| P7 | london | 07:00 | 24 | 60.0 | -9653.0 | 974.4 | -10627.4 |
| M7 | nyam | 10:00 | 84 | 84.0 | -9006.5 | 1237.0 | -10243.5 |
| K7 | london | 06:30 | 24 | 29.0 | -8451.0 | 496.2 | -8947.2 |

### B1.4 Slots (book x session x 30-min ET entry slot, n >= 15) HOLD
**(a) cost > positive gross edge: 2 slots**
| book | sess | slot | n | lots | gross | cost | net | cost_pct_gross |
|---|---|---|---|---|---|---|---|---|
| M7 | london | 04:30 | 38 | 50.0 | 398.0 | 714.4 | -316.4 | 179.5 |
| P7 | asia | 18:30 | 64 | 268.0 | 3604.0 | 3725.1 | -121.1 | 103.4 |

**(b) cost = 40% or more of positive gross: 8 slots (worst 25)**
| book | sess | slot | n | lots | gross | cost | net | cost_pct_gross |
|---|---|---|---|---|---|---|---|---|
| K7 | london | 02:30 | 15 | 20.0 | 285.5 | 284.8 | 0.70 | 99.8 |
| A7 | asia | 00:30 | 15 | 15.0 | 243.0 | 208.8 | 34.2 | 85.9 |
| M7 | london | 04:00 | 36 | 45.0 | 1051.5 | 703.2 | 348.3 | 66.9 |
| M7 | london | 05:00 | 36 | 51.0 | 1213.5 | 758.2 | 455.3 | 62.5 |
| M7 | london | 02:30 | 27 | 31.0 | 1064.0 | 473.4 | 590.6 | 44.5 |
| M7 | london | 06:00 | 23 | 28.0 | 908.0 | 400.3 | 507.7 | 44.1 |
| M7 | nyam | 10:00 | 82 | 82.0 | 2847.5 | 1170.9 | 1676.6 | 41.1 |
| M7 | london | 02:00 | 89 | 118.0 | 4145.0 | 1675.5 | 2469.5 | 40.4 |

**(c) gross <= 0 before any cost (worst 15 of 37 slots)**
| book | sess | slot | n | lots | gross | cost | net |
|---|---|---|---|---|---|---|---|
| M7 | nyam | 11:30 | 42 | 42.0 | -16393.5 | 664.5 | -17058.0 |
| P7 | asia | 20:30 | 34 | 130.0 | -16316.0 | 1979.2 | -18295.2 |
| K7 | nypm | 12:00 | 28 | 33.0 | -15640.0 | 527.5 | -16167.5 |
| K7 | nyam | 11:30 | 47 | 47.0 | -15130.5 | 723.7 | -15854.2 |
| M7 | london | 06:30 | 25 | 33.0 | -12047.5 | 597.1 | -12644.6 |
| P7 | asia | 01:00 | 18 | 82.0 | -11548.5 | 1243.7 | -12792.2 |
| K7 | nyam | 11:00 | 38 | 38.0 | -10158.0 | 576.3 | -10734.3 |
| A7 | asia | 20:30 | 18 | 18.0 | -8610.0 | 281.9 | -8891.9 |
| P7 | asia | 23:30 | 18 | 82.0 | -8485.5 | 1238.1 | -9723.6 |
| K7 | london | 07:00 | 29 | 36.0 | -7652.5 | 621.4 | -8273.9 |
| K7 | asia | 01:00 | 19 | 27.0 | -7098.0 | 406.9 | -7504.9 |
| H7 | asia | 18:00 | 15 | 33.0 | -6965.0 | 497.1 | -7462.1 |
| M7 | london | 08:00 | 27 | 37.0 | -6925.0 | 830.1 | -7755.1 |
| K7 | london | 04:00 | 34 | 34.0 | -6794.0 | 513.0 | -7307.0 |
| P7 | nyam | 11:30 | 32 | 62.0 | -6682.5 | 938.9 | -7621.4 |


## B5 / B3 / B2 EXACT RESULTS (generated 2026-11-13 02:18Z UTC)

Hook code/th_smart_b/sb_hooks.py (outermost hooklist entry on JN05W2 = SB_*, JN05W2J = SBJ_*); prereg SMART_B_PREREG.md. Each cell is scored vs its base on the same months. **Caveat: the engine state cut fires in the engine but did not fire live on 11-11 (DS3_P7_CUT_FIDELITY.md).** Passive limits fill on a print through the level by 1 tick (touch variants are the optimistic bound). cut % = stack maxDD vs base (positive = shallower); d mean = all-weeks mean difference ($/wk); "d mean live-excess adj" adds the change in live-excess slip cost (B1 parameters) to the L6M all-weeks d mean (limit fills avoid market-exit excess; engine slip is inside gross). A window appears only when all its months are present.

| set | base | months | 5 best wks kept | winning wks turned losing | L6M cut % | L6M d mean/wk | L6M d mean live-excess adj | L6M run max/p95 | HOLD cut % | HOLD d mean/wk | PRE cut % | X' cut % | GAP cut % | WF cut / beat |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| **B5 duplicate risk** | | | | | | | | | | | | | | |
| SB_DUP120S | JN05W2 | 1 | running | | | | | | | | | | | |
| SB_DUP60S | JN05W2 | 4 | running | | | | | | | | | | | |
| **B3 stop join** | | | | | | | | | | | | | | |
| SB_SJ0 | JN05W2 | 6 | 101% ($319k of $316k) | 0 of 20 | -0.1 | 561 | 556 | 13/6 | - | - | - | - | - | - |
| SB_SJ1 | JN05W2 | 1 | running | | | | | | | | | | | |
| **B3 work the cut** | | | | | | | | | | | | | | |
| SB_WK1 | JN05W2 | 6 | 100% ($317k of $316k) | 0 of 20 | -3.8 | 807 | 803 | 13/6 | - | - | - | - | - | - |
| SB_WK2 | JN05W2 | 1 | running | | | | | | | | | | | |
| **B2 slices / split** | | | | | | | | | | | | | | |
| SB_SLALL | JN05W2 | 6 | 111% ($350k of $316k) | 1 of 20 | -37.7 | -522 | -610 | 12/6 | - | - | - | - | - | - |
| SB_SP100 | JN05W2 | 4 | running | | | | | | | | | | | |
| **B2 passive entry** | | | | | | | | | | | | | | |
| SB_LE_bid0_T5M | JN05W2 | 1 | running | | | | | | | | | | | |
| SB_LE_mid0_T10M | JN05W2 | 1 | running | | | | | | | | | | | |

Not run in this pass: stop-limit cut, target one tick inside, depth-conditional passive entry, per-slot refit (see prereg). Behavioural scorecard a-e and acceptance_p7 are run on cells that complete L6M+HOLD (code/th_works_q/behavior_scorecard.py, code/th_works_c/acceptance_p7.py).

## B5 first-order screen + forward placebo (JN05W2 trade lists, 500 draws of equal size from the same book mix)

A trade is flagged when an earlier trade of ANOTHER book on the SAME side entered within w seconds (first fill). skip/half gain = $/wk if the flagged trades were skipped/halved (first-order, entry stream unchanged; exact is the verdict). ifprofit proxy uses the first trade's FINAL result (hindsight: an upper bound, NOT tradable; the exact SB_DUP*P cells use the first book's unrealised P&L at the signal).

| window | w | flagged | flagged_pct | flagged_net | skip_gain_wk | half_gain_wk | ifprofit_proxy_gain_wk | placebo_skip_mean_wk | placebo_q95_wk | p_skip |
|---|---|---|---|---|---|---|---|---|---|---|
| L6M | 60 | 213 | 5.1 | 35680 | -1372 | -686 | 6296 | -1314 | 613 | 0.528 |
| L6M | 120 | 385 | 9.2 | 62481 | -2403 | -1202 | 9367 | -2089 | 310 | 0.612 |
| L6M | 300 | 669 | 16.0 | 87672 | -3372 | -1686 | 15344 | -3499 | -468 | 0.486 |
| HOLD | 60 | 172 | 5.2 | 52376 | -2054 | -1027 | 4514 | -651 | 1351 | 0.85 |
| HOLD | 120 | 275 | 8.4 | 58259 | -2285 | -1142 | 6696 | -954 | 1597 | 0.814 |
| HOLD | 300 | 504 | 15.4 | 55055 | -2159 | -1080 | 12263 | -1412 | 1373 | 0.656 |

Reading: the flagged second-book entries are net winners in both windows (flagged_net > 0) and skipping them is indistinguishable from skipping a random set of the same book mix (p_skip 0.5-0.85): duplicate same-side entries are not a cost leak on this base at first order.