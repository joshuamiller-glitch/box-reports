# ASIA BOTH-SIDE SCREEN + NULL (W-SHORT for W-ASIA, order 1014Z item 5; refreshed 02:03Z UTC)

The 1307 Asia ladder cells whose screen mode was long/short but whose engine sets traded BOTH sides, re-screened as mode = both (same row / module / variant / params / bracket). (a) screen numbers from the grid cache on the both-side stream: L6M / L3M points, trades, persistence, prior years in R per week, R0 (same thresholds: L6M > 0, L3M > 0, >= 100 trades, persistence > 0.60, no RED prior year) and own-stop (2 stops; only where the own-stop array exists). (b) random-entry draws with the SAME bracket on the both-side stream (gr3 mode 0: same count and side mix as the real both-side signals), p = (1 + k) / (1 + n): 30 draws for all cells, 200 for the beating cells; p_L6M / p_ALL / p_PRIOR as in the R3 ladder. Priority: beating cells (ids from NEW_BOOK_BEATS_LIVE_ASIA.md) first. Data: code/th_short/pulled_r3/asia_bothside.csv (all cells, all columns).

Drawn so far: 1304 of 1307 cells (beating 15 of 15). R0 on the both-side stream passes for 16 of 1307 cells (os2 positive: 701 of 1023 with the array).

## Beating cells (priority)

| id | bar | trigger.variant params | bracket | old screen mode | L6M / L3M pts (both) | trades | persist | R/wk L6M | prior yrs R/wk 23/24/25 | R0 both-side | own-stop 2 L6M / L3M | n draws | p_L6M | p_ALL | p_PRIOR | beats of 30 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Lf77e374b | tm240 | bands_donchian.break {"n": 10, "buf": 0.0} | plain60/60 | long | +1918 / +1317 | 705 | 0.51 | +1.230 | 0.024 / 0.074 / -0.094 | FAIL | 1891 / 1004 | 200 | 0.055 | 0.025 | 0.075 | 28 |
| L0a809c2e | kagi_40 | trend_ma_t3.price_native {"len": 13, "width": 0.25} | plain60/60 | long | +1343 / +64 | 430 | 0.55 | +0.861 | 0.203 / 0.010 / 0.446 | FAIL |  /  | 200 | 0.085 | 0.060 | 0.040 | 29 |
| L63ff9ae8 | time_m_4 | momentum_rsi.mom {"len": 10, "lvl": 60} | plain60/60 | long | +1147 / +1050 | 598 | 0.60 | +0.735 | 0.076 / 0.185 / 0.264 | FAIL | 357 / 646 | 200 | 0.124 | 0.005 | 0.005 | 28 |
| Lcb276f27 | tm120 | bands_atrchan.break_ema_native {"clk": 5, "k": 1.5} | sym8u | long | +500 / +41 | 334 | 0.57 | +0.196 | 0.191 / 0.197 / -0.035 | FAIL | 146 / -4 | 200 | 0.219 | 0.010 | 0.015 | 21 |
| La5b5d03a | time_m_2 | bands_atrchan.break_ema_native {"clk": 5, "k": 1.5} | sym8u | long | +856 / +59 | 337 | 0.57 | +0.336 | 0.200 / 0.166 / -0.059 | FAIL | 486 / 14 | 200 | 0.199 | 0.005 | 0.015 | 24 |
| L0b1d7882 | tm30 | bands_vwap.break {"minbars": 10, "k": 1.0} | plain60/60 | long | +311 / +65 | 562 | 0.49 | +0.199 | 0.073 / 0.018 / -0.164 | FAIL | 263 / -171 | 200 | 0.234 | 0.060 | 0.129 | 27 |
| Leee81e35 | vol_750 | bands_atrchan.break_ext {"n": 20, "atr": 14, "k": 2.0} | asym15u/30u | long | +1643 / +276 | 285 | 0.55 | +0.527 | 0.156 / -0.042 / 0.195 | FAIL | 2118 / 241 | 200 | 0.124 | 0.010 | 0.065 | 28 |
| L17ce266f | tm240 | momentum_rsi.mom {"len": 10, "lvl": 60} | plain60/60 | long | +1085 / +930 | 598 | 0.62 | +0.696 | 0.068 / 0.206 / 0.185 | FAIL | 115 / 521 | 200 | 0.090 | 0.010 | 0.010 | 27 |
| L5c9e11b3 | vol_750 | momentum_mvote.v3of5 {"scale": 0.25, "thr": 0.25} | plain60/60 | long | +2123 / +1424 | 566 | 0.62 | +1.361 | 0.354 / 0.627 / 0.423 | FAIL | 1945 / 1304 | 200 | 0.065 | 0.005 | 0.005 | 27 |
| Lda55d973 | vol_750 | momentum_stoch.zone_break_native {"len": 9, "lvl": 80} | plain60/60 | long | +3050 / +1542 | 672 | 0.56 | +1.955 | 0.056 / 0.242 / 0.145 | FAIL | 1861 / 1535 | 200 | 0.005 | 0.010 | 0.025 | 30 |
| L1edb9fab | tm300 | pullback_ema.depth {"len": 10, "w": 0.5} | plain60/60 | long | +1803 / +1552 | 796 | 0.50 | +1.155 | 0.068 / 0.489 / 0.216 | FAIL |  /  | 200 | 0.080 | 0.005 | 0.015 | 27 |
| L7c368a4f | time_m_5 | pullback_ema.depth {"len": 10, "w": 0.5} | plain60/60 | long | +1829 / +1631 | 795 | 0.54 | +1.172 | 0.067 / 0.478 / 0.263 | FAIL | 158 / 609 | 200 | 0.055 | 0.005 | 0.005 | 26 |
| L5d9e7166 | tm240 | momentum_rsi.mom_native {"len": 10, "lvl": 60} | plain60/60 | long | +1085 / +930 | 598 | 0.62 | +0.696 | 0.068 / 0.206 / 0.185 | FAIL | 115 / 521 | 200 | 0.090 | 0.015 | 0.015 | 24 |
| Ledfbf4d2 | vol_350 | bands_bollinger.break_native {"clk": 20, "k": 1.5} | plain60/60 | long | +1722 / +1065 | 663 | 0.62 | +1.104 | 0.232 / 0.434 / 0.290 | FAIL | 1957 / 1230 | 200 | 0.090 | 0.010 | 0.005 | 27 |
| L05222ff9 | time_m_4 | momentum_rsi.mom_native {"len": 10, "lvl": 60} | plain60/60 | long | +1147 / +1050 | 598 | 0.60 | +0.735 | 0.076 / 0.185 / 0.264 | FAIL | 357 / 646 | 200 | 0.065 | 0.005 | 0.020 | 26 |

## All drawn cells: counts

| cells drawn | R0 pass (both-side) | p_L6M <= 0.05 | p_L6M <= 0.20 | p_ALL <= 0.05 | beat >= 24 of 30 | beat >= 27 of 30 |
|---|---|---|---|---|---|---|
| 1304 | 16 | 48 | 413 | 548 | 497 | 246 |

Note: the null comparison here is stage-A / B per cell (screen, random entries with the same bracket on the both-side stream); the calibrated pass rule (false-discovery rate by mode and statistic) is in the CALIBRATION sections of SURVIVOR_COUNTS.md; both-side Asia cells had the lowest measured FDR there.
