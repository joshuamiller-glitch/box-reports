# REPLACEMENT CANDIDATES: 200-draw drift check (same method as WIDE_BRACKET_EDGE.md): real one-position bare trades vs 200 random-entry draws (same bracket, same long/short counts, random day and time in the session window); up/down = NQ up weeks / down weeks (weekly change of the 1-s series, 107 up and 78 down weeks); pts per trade after costs. UNTESTED IDEAS until the exact rows land.

| session | cell | bracket | n (L/S) | real pts | random pts | beat all / L / S | long pts | short pts | NQ-up weeks real vs random (n) | NQ-down weeks real vs random (n) | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|
| AS | trig_levels_mmove|retest_native|{"M": 3, "tol": 0.0} | 60/60 | 975 (484/491) | +6.64 | -0.52 | 1.00 / 1.00 / 1.00 | +6.87 | +6.42 | +6.06 vs -0.34 (510) | +7.28 vs -0.76 (465) | **EDGE BEYOND DRIFT** |
| AS | trig_trend_ma_kama|price|{"len": 20, "width": 0.5} | 60/60 | 1138 (595/543) | +6.58 | -0.43 | 1.00 / 1.00 / 1.00 | +7.71 | +5.35 | +5.64 vs -0.31 (599) | +7.62 vs -0.58 (539) | **EDGE BEYOND DRIFT** |
| AS | trig_levels_fibr_dev|false_break|{"M": 3, "k": 0.5} | 60/60 | 1757 (904/853) | +3.80 | -0.60 | 1.00 / 1.00 / 1.00 | +5.13 | +2.40 | +3.75 vs -0.41 (892) | +3.86 vs -0.86 (865) | **EDGE BEYOND DRIFT** |
| NY | trig_levels_prior_day|false_break|{"M": 1, "k": 0.0} | 120/120 | 3125 (1543/1582) | +13.63 | -0.41 | 1.00 / 1.00 / 1.00 | +12.66 | +14.57 | +14.81 vs -0.33 (1685) | +12.25 vs -0.51 (1440) | **EDGE BEYOND DRIFT** |
| NY | trig_levels_fib60|retest|{"M": 6, "tol": 0.0} | 120/120 | 1134 (533/601) | +6.89 | -0.56 | 1.00 / 0.98 / 0.98 | +8.68 | +5.30 | +13.28 vs -1.00 (592) | -0.09 vs +0.01 (542) | **MOSTLY DRIFT** |
| NY | trig_levels_piv_wf|retest|{"M": 3, "tol": 0.5} | 120/120 | 1838 (875/963) | +8.23 | -0.63 | 1.00 / 1.00 / 1.00 | +8.52 | +7.96 | +6.34 vs -0.97 (1015) | +10.56 vs -0.19 (823) | **EDGE BEYOND DRIFT** |
| NY | trig_tape_vpin|fade_native|{"N": 600, "thr": 0.12} | 60/60 | 736 (350/386) | +5.96 | -0.54 | 1.00 / 1.00 / 0.94 | +9.29 | +2.94 | +4.21 vs -0.83 (456) | +8.80 vs -0.16 (280) | **EDGE BEYOND DRIFT** |
| NP | trig_book_cancel|canc_follow|{"L": 100, "z": 2.0} | 90/90 | 1779 (1116/663) | +6.15 | -0.60 | 1.00 / 1.00 / 1.00 | +4.37 | +9.15 | +7.41 vs +1.26 (962) | +4.67 vs -3.04 (817) | **EDGE BEYOND DRIFT** |
| NP | trig_levels_trendline|reject_native|{"conf": "body", "tol": 1.0} | 90/90 | 5265 (2567/2698) | +4.32 | -0.55 | 1.00 / 1.00 / 1.00 | +4.06 | +4.57 | +4.50 vs -0.72 (2828) | +4.11 vs -0.33 (2437) | **EDGE BEYOND DRIFT** |
