# SIZER_LIVE_DEF - the live ER(20) 5-min sizer as coded in the D7 research engine and reproduced by V13T_LIVE (S4b, T-SIZER prep, 2026-11-02)
SOURCE: the DS7 chart code is not on this disk; the definition below is the engine code the live panel was specified against: l2vast/ds3/code/sundaystack2/ss2_lib.py (er_mult, lot_tables, integer-lot rounding), d7base/d7lib.py (BASE: er=True, er_thr=0.30, er_hi=1.5, er_lo=0.5, er_books = all six, running-max SizeMult), and the feature builder code/trendgate/tg_series.py + tg_lib.eff_ratio. Anything the live DS7 does beyond this (a finer ladder than the binary one, A06 slots, B02 quiet) is NOT in the engine and is listed as OPEN at the bottom.
## 1. The sizer
* **Feature:** Kaufman efficiency ratio ER(20) on 5-minute closes: ER = |c[i] - c[i-20]| / sum_{j=i-19..i} |c[j] - c[j-1]| (20 bar-to-bar changes, 21 closes; 0 if the path sum is 0; NaN until 21 bars). Direction-agnostic (unsigned).
* **Bars:** 5-minute bars built from the tick-built 1-minute library bars by epoch buckets, key = (t_close_1m - 60) // 300, bar timestamp = the close second of its last 1-minute bar (so a 5-min bar is stamped at its end). Prices in the continuous (back-adjusted) frame. No partial bars (partial 1-min bars excluded).
* **Evaluation second:** the signal second (the library entry_ts of the signal); the feature is read from the LAST CLOSED 5-min bar: index = searchsorted(bar_close_times, signal_second, 'right') - 1, i.e. the latest bar whose close second is <= the signal second (the bar in progress is not used). At 5-minute boundaries a signal in the closing second sees that bar.
* **Ladder (binary):** ER >= 0.30 -> multiplier 1.5 (up-size); ER < 0.30 -> 0.5; ER NaN -> 1.0. In V13T_LIVE no taken signal has a NaN ER (0 of 18,384). No x1.0 state and no x0.25 state from ER alone.
* **Books and sessions:** applied to all six core books (K6=KB, P6=PE, U6=SM, H6=HM, M6=MV, A6=PB) in every session with live lots.
* **Combination with the zone HALF layer (the "double halving"):** the engine multiplies the two factors: mer = ER multiplier x (0.5 if the signal is in the 7-line zone set at D20, else 1) -> the stored per-row multiplier takes the values 0.25 (zone & low ER), 0.5, 0.75 (zone & high ER), 1.5 (no x1.0). Lots = floor(session_lots x mer + 0.5), minimum 1 for mer > 0 (integer, round half up); the governors (day lock / 12R week floor give-back) keep the UNROUNDED multiplier; the day/week floors use the running-max SizeMult over the book's TAKEN signals of the day.
* **Session lots (live11):** K6 2/2/-/1/2/- (asia, london, pre, nyam, nypm, close) as coded K7; P6 7 asia/london/nyam; U6 4 asia/london; H6 4 asia + 1 nyam; M6 2 london + 1 nyam; A6 1 asia; NY-AM 1 lot for K/H/M.
## 2. Single rounding vs sequential rounding (the P7 "7 -> 4 -> 2" case)
The engine rounds ONCE after multiplying (7 x 0.5 x 0.5 = 1.75 -> 2) so a P7 05:00 signal in a zone with low ER gives 2, equal to the live 7 -> 4 -> 2. The two differ when the second factor is 1.5 or 0.75: sequential rounding gives 7 -> 4 (zone half) -> 6 (x1.5) while the engine gives floor(7 x 0.75 + 0.5) = 5. In V13T_LIVE this affects 353 of the 2,606 taken zone-layer rows (163 of 505 PE rows, mean +0.32 lot per PE zone row if sequential were live). OPEN: which one the live code does (the worked case in the order only shows the low-ER branch, where both agree).
## 3. Lots distribution reproduced by V13T_LIVE (lock none, 18,384 taken signals with live lots, 2023-04..2026-10-30)
| multiplier | share of taken signals |
|---|---|
| x0.25 (zone half & ER < 0.30) | 8.9% |
| x0.50 (ER < 0.30) | 47.6% |
| x0.75 (zone half & ER >= 0.30) | 5.3% |
| x1.00 | 0.0% |
| x1.50 (ER >= 0.30) | 38.3% |
Share of signals with ER >= 0.30: 43.5%. Mean session lots 3.32, mean effective lots 3.16 (integer rounded), max 11 (PE 7 x 1.5 = 10.5 -> 11). Per book (n, session lots, effective lots, mean multiplier, % down-sized, % up-sized): HM 2,504, 3.14, 2.66, 0.83, 65%/35%; KB 5,997, 1.79, 1.63, 0.81, 67%/33%; MV 2,988, 1.52, 1.64, 0.89, 61%/39%; PB 1,046, 1.00, 1.59, 1.11, 41%/59%; PE 4,479, 7.00, 6.69, 0.89, 60%/40%; SM 1,370, 4.00, 3.79, 0.95, 56%/44%. By session mean multiplier asia 0.88, london 0.90, nyam 0.86, nypm 0.80. The overnight observation (11 of 12 signals sized, ER 0.07-0.44 -> x0.25-1.5) is consistent: ER 0.07 -> 0.5 (0.25 in a zone), ER 0.44 -> 1.5 (0.75 in a zone), PE 7 lots -> 2..11. Per-row data: /mnt/l2/l2vast/ds3_zones3_new/e2/sizer_rows2.pkl.
## 4. Five worked rows (V13T_LIVE taken signals; tid, label day, book, session, ER, in the zone layer, session lots, multiplier, effective lots)
| # | tid | day | book / session | ER(20) 5m | zone | session lots | ER ladder | zone | mer | lots |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 6002576 | 2024-12-26 | PE / nyam | 0.125 | yes | 7 | 0.5 | 0.5 | 0.25 | floor(7 x 0.25 + 0.5) = 2 |
| 2 | 6004198 | 2025-08-06 | PE / nyam | 0.292 | no | 7 | 0.5 | 1 | 0.5 | floor(3.5 + 0.5) = 4 |
| 3 | 6003874 | 2025-05-29 | PE / london | 0.430 | no | 7 | 1.5 | 1 | 1.5 | floor(10.5 + 0.5) = 11 |
| 4 | 5000871 | 2024-10-14 | SM / asia | 0.386 | yes | 4 | 1.5 | 0.5 | 0.75 | floor(3.0 + 0.5) = 3 |
| 5 | 4003208 | 2025-03-12 | KB / asia | 0.177 | yes | 2 | 0.5 | 0.5 | 0.25 | max(1, floor(0.5 + 0.5)) = 1 |
## 5. OPEN items (need the DS7 source or the user)
(a) Is the live ladder exactly binary at 0.30 (the engine is), or finer (the overnight text lists x0.25 as an ER outcome; here x0.25 only arises from ER x zone)? (b) Single vs sequential rounding of the zone half and the ER factor (section 2). (c) A06 slots and B02 quiet: not in the engine, not modelled. (d) Whether the live ER bar is the last closed 5-min bar at the signal second (as coded) or the bar open at the signal second. (e) The ER price frame is the continuous back-adjusted frame (roll gaps removed); live uses the chart's own series.
