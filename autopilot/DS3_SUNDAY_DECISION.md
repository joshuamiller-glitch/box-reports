# DS3_SUNDAY_DECISION - the Sunday composite restated: integer half-up min-1 lots, causal running-max locks, A6 = PB7, with the four decision numbers (a) sizer books, (b) K6 add, (c) NY-PM end skip, (d) the restated composite and the Sunday candidate (agent D1, 2026-10-31)

Research only; no live/execution/chart change, no credentials, no purchases. Masks capped 20260206 (windows L3M 20251106.., L6M 20250801.., HOLD 20250701.., PRE 20240201..20250630, X' 20230401..20240131); UNTOUCHED never read. Prereg `autopilot/SUNDAYDECISION_prereg.md` sha256 ead9859c048c0b1c9cac2639b31795356d25e07532398dbb841741100fd9c9e6 (DECISIONS.md, logged before any scored result was read; one pipeline smoke run is disclosed in it). Code `l2vast/ds3/code/sundaydecision/` (sdlib.py engine wrapper, pb7_build.py, run_all.py, run_extra.py, ref_orig.py, mk_doc.py, write_doc.py), outputs `l2vast/ds3/out/sundaydecision/` (res_1.28.pkl, res_2.45.pkl = per-book daily $ of every scenario, tables.pkl, pb7_rows.parquet, logs).

**How to read.** Every cell is the lock-engine stack delta vs the AS-IS stack (market entries, no rules, join stop 2.45, same live lots, same A6 = PB7 series), $k per week, with the MDE (2.8 x SE of the paired weekly delta) in brackets; `~` after a cell = the delta is INSIDE its MDE (not distinguishable from zero). Basis N (no target correction); `Native 1.28` = stop at 1.28 (A, odd day-of-month), `join 2.45 (LIVE-CAL)` = the live-calibrated join stop cost (B, even day-of-month); `A/B parity mix` = the two runs spliced by the parity of the label day (an approximation: the two lock states are not carried across days). Engine = `sundaystack2/ss2_lib.py` (causal running-max locks = D6's rule: planned-lot R x running max of the day's trend multipliers, reset at the 18:00 ET rollover, week floor on the same BookR) extended for A6 = PB7 and for integer half-up min-1 lots (`Max(1, Floor(lots x mult + 0.5))`; the locks keep the UNROUNDED trend multiplier 0.5 / 1.0 / 1.5, as D6 sets SizeMult). Live lots / sessions: K6 2 Asia/London/NY-AM/NY-PM; P6 7 Asia/London/NY-AM; U6 4 Asia/London; H6 4 Asia / 2 NY-AM; M6 2 London/NY-AM; A6 = PB7 1 Asia; lot 0 elsewhere; O6 (opening drive, 1 lot) has no series in the library and is not in any number. Splits at integer lots: K6 1/1, U6 3/1, H6 3/1 Asia and 1/1 NY-AM, P6 5/2, M6 1/1, A6 market (1 lot); the 70/30 fraction is held at the planned-lot split when the ER sizer changes the lots (3 lots from K6 2 x 1.5 become 1.5/1.5). Add slippage labels: +0.25 per add lot (model, the headline), +0.45 (stress).

## 0. Page 1

**Tie-out (0).** The SS-2 headline is reproduced to the dollar on fractional lots (library PB as A6, Native 1.28, N): +19.4 (24.1) L3M | +18.5 (17.4) L6M | +16.2 (16.8) HOLD | +4.7 (13.4) PRE | +12.5 (14.7) X'; the same engine with A6 = PB7 (Asia, 1 lot) gives +19.4 / +17.8 / +15.5 / +4.7 / +11.1, and with the PB7 rows added the engine still returns SS-2's live4 delta (+17.8 / +15.5 / +4.4 / +10.0) when A6 and M6 are set to lot 0 (identity tests in section 6).

**(a) Sizer books.** The ER sizer on P6 + K6 ONLY gives the same dollars as the sizer on all six: P6+K6 minus all six = -0.5 (9.4) L3M | +0.5 (5.5) L6M | +0.2 (5.0) HOLD | -1.0 (4.3) PRE | -0.4 (3.2) X' (Native, integer lots; join 2.45: -0.7 / +0.4 / +0.2 / -0.8 / -0.3), all inside MDE, so a 'sizer books' list of P6 K6 costs nothing in dollars; P6 carries the sizer (switch it off on P6 alone: -11.5 (11.3) L6M, K6 -2.4 (4.5), A6 -0.9 (1.4), H6 -0.1, M6 +0.6, U6 +0.9), U6 H6 M6 contribute nothing (the 'drop U6 H6 M6' list = sizer on K6 P6 A6 is the best by the numbers, +1.4 (5.3) L6M over all six and +0.9 (1.4) over P6+K6, but that is a post-hoc pick inside MDE).
**(b) K6 add.** K6 at market with the others at 70/30 is LOWER than K6 split by -2.3 (3.7) L3M | -0.7 (2.4) L6M | -0.4 (2.2) HOLD | -0.7 (1.2) PRE | +0.1 (1.1) X' (composite with the sizer, Native; join 2.45: -2.0 / -0.6 / -0.3 / -0.6 / +0.1; stress +0.45: -0.6 L6M), i.e. the K6 add is worth about +0.4 to +0.7k a week (K6's own book, 2 lots) and is indistinguishable from zero in every window: keep the split for Sunday, as ordered (the composite level is 43.5 split vs 42.8 market $k/wk L6M).
**(c) NY-PM end skip 14:40-15:00 ET.** It is a no-op at the live lots: +0.1 (1.1) L3M | +0.0 (0.8) L6M | -0.0 (0.7) HOLD | -0.2 (0.3) PRE | +0.2 (0.7) X' because only K6 (about 0.7 signals a week in the window) trades NY-PM live; the clock rule carries no dollars, ship it OFF (agrees with NP-1, DS3_NYPM_END_SKIP.md).
**(d) Restated composite, A6 = PB7, integer half-up min-1 lots, running-max locks.** +25.5 (22.5) L3M | +21.8 (17.6) L6M | +18.7 (17.5) HOLD | +6.1 (13.1)~ PRE | +11.8 (14.2)~ X' at Native 1.28 and +23.1 (21.4) | +19.5 (17.3) | +16.4 (17.2)~ | +3.6 (13.2)~ | +10.2 (14.2)~ at the join 2.45 (A/B parity mix: +23.8 / +20.4 / +17.4 / +4.8 / +11.0): L3M, L6M and (Native) HOLD clear their MDE, PRE and X' do not; replacing the library PB (all sessions) by PB7 (Asia only) lowers the integer composite by 1.0k L6M (library PB Asia only 22.4, PB7 21.8), and the integer lines sit about 4k above the fractional lines (+17.8 L6M) only because half-up rounding of the ER lots raises the average lot (no-sizer integer +8.3 vs fractional +7.7): more lots, not more edge, and the number moves with the rounding rule (section 8).
**SUNDAY CANDIDATE** = sizer P6+K6 only + K6 at market + NY-PM end skip: +22.8 (22.6) L3M | +21.6 (17.0) L6M | +18.5 (16.8) HOLD | +4.3 (11.8)~ PRE | +12.0 (13.1)~ X' (Native; join 2.45: +20.5 / +19.4 / +16.4 / +2.0 / +10.3; A/B mix +21.1 / +20.3 / +17.3 / +3.1 / +11.2; stress add slip +0.45: +21.3 L6M): it is NOT a better number than the D6 composite, it is within -0.2 (6.5) L6M of it (-2.7 L3M, -1.8 PRE, +0.1 X'), a simpler configuration at the same dollars, with the K6 add given up (-0.7k) and nothing else changed.
Honest labels: every piece is post-hoc selected (SS-2 section 8; the ER sizer thresholds 0.30 / x1.5 / x0.5 were chosen after looking at L6M / HOLD / L3M), the three comparisons above are single paired looks at recent windows, the candidate is their in-sample union, PRE and X' are inside MDE for every composite row, and the whole ER-sizer gain exists only if D6 multiplies the day and week locks by the running max (with planned-lot locks the six-book sizer is only +2.7k L6M, ER-1; the composite with planned-lot locks and integer lots is +11.2k vs +22.8k, SS-2 3b).

### THE TABLE (recent-first; cell = delta vs as-is, $k/wk (MDE); `~` = inside MDE; last column = L6M stack level, weekly mean / SD / maxDD of the weekly cumulative / sum of the 20 worst weeks, $k)

| row | stop | L3M | L6M | HOLD | PRE | X' | L6M stack level: mean / SD / maxDD(wk-cum) / worst-20 $k |
|---|---|---|---|---|---|---|---|
| **(0) TIE-OUT, fractional lots (SS-2 convention, 70/30 on all books, no rounding)** | | | | | | | |
| SS-2 engine, A6 = library PB all sessions (published +18.5 / +16.2 / +4.7 / +12.5 at Native) | Native 1.28 | +19.4 (24.1)~ | +18.5 (17.4) | +16.2 (16.8)~ | +4.7 (13.4)~ | +12.5 (14.7)~ | 42.6 / 42.1 / 27.2 / 401.3 |
| SS-2 engine, A6 = library PB all sessions (published +18.5 / +16.2 / +4.7 / +12.5 at Native) | join 2.45 (LIVE-CAL) | +17.1 (24.5)~ | +16.2 (17.8)~ | +13.9 (17.0)~ | +2.3 (13.5)~ | +10.8 (14.7)~ | 40.2 / 41.5 / 22.8 / 355.4 |
| same engine, A6 = PB7 Asia 1 lot (this report's engine) | Native 1.28 | +19.4 (24.4)~ | +17.8 (17.3) | +15.5 (17.0)~ | +4.7 (13.8)~ | +11.1 (13.8)~ | 39.5 / 39.9 / 23.6 / 366.9 |
| same engine, A6 = PB7 Asia 1 lot (this report's engine) | join 2.45 (LIVE-CAL) | +16.9 (24.8)~ | +15.3 (17.7)~ | +13.2 (17.2)~ | +2.5 (13.9)~ | +9.6 (13.8)~ | 37.1 / 39.6 / 23.6 / 316.2 |
| **AS-IS stack (market entries, no rules, join 2.45, same live lots, A6 = PB7): level $k/wk, MDE n/a** | | | | | | | |
| as-is stack mean $k/wk | join 2.45 | 12.2 | 21.7 | 21.9 | 18.6 | -3.4 | 21.7 / 43.9 / 88.0 / 58.0 |
| **(d) INTEGER half-up min-1 lots, causal running-max locks, 70/30 on all books (K6 1/1), add slip +0.25, sizer on all six books** | | | | | | | |
| D6 composite, A6 = PB7 | Native 1.28 | +25.5 (22.5) | +21.8 (17.6) | +18.7 (17.5) | +6.1 (13.1)~ | +11.8 (14.2)~ | 43.5 / 42.9 / 21.1 / 416.6 |
| D6 composite, A6 = PB7 | join 2.45 (LIVE-CAL) | +23.1 (21.4) | +19.5 (17.3) | +16.4 (17.2)~ | +3.6 (13.2)~ | +10.2 (14.2)~ | 41.2 / 42.9 / 24.0 / 371.9 |
| D6 composite, A6 = PB7 | A/B parity mix | +23.8 (21.9) | +20.4 (17.5) | +17.4 (17.4) | +4.8 (13.1)~ | +11.0 (14.2)~ | 42.2 / 43.3 / 22.9 / 386.8 |
| D6 composite, add slip +0.45 stress | Native 1.28 | +25.1 (22.4) | +21.2 (17.4) | +18.1 (17.4) | +5.8 (13.1)~ | +11.6 (14.2)~ | 42.9 / 42.6 / 21.5 / 409.8 |
| D6 composite, add slip +0.45 stress | join 2.45 (LIVE-CAL) | +22.7 (21.3) | +19.0 (17.1) | +15.9 (17.0)~ | +3.3 (13.2)~ | +10.0 (14.2)~ | 40.7 / 42.7 / 24.3 / 366.2 |
| before: integer composite, A6 = library PB all sessions (SS-2 3b) | Native 1.28 | +25.0 (22.6) | +22.8 (17.6) | +19.3 (17.3) | +7.4 (13.0)~ | +12.9 (15.0)~ | 46.8 / 45.9 / 20.6 / 442.8 |
| before: integer composite, A6 = library PB all sessions (SS-2 3b) | join 2.45 (LIVE-CAL) | +22.4 (21.8) | +20.4 (17.5) | +17.0 (17.2)~ | +4.6 (13.1)~ | +11.1 (15.0)~ | 44.4 / 45.8 / 29.9 / 398.6 |
| integer composite, A6 = library PB Asia only (sessions isolated) | Native 1.28 | +26.2 (24.1) | +22.4 (17.9) | +19.1 (17.5) | +7.0 (12.9)~ | +12.7 (14.4)~ | 45.4 / 45.0 / 25.8 / 428.2 |
| integer composite, A6 = library PB Asia only (sessions isolated) | join 2.45 (LIVE-CAL) | +23.9 (23.1) | +20.2 (17.6) | +17.0 (17.2)~ | +4.3 (13.0)~ | +11.0 (14.5)~ | 43.2 / 45.1 / 28.7 / 384.9 |
| **(a) ER sizer books list (integer composite, K6 split, +0.25)** | | | | | | | |
| sizer on all six (K6 P6 U6 H6 M6 A6) | Native 1.28 | +25.5 (22.5) | +21.8 (17.6) | +18.7 (17.5) | +6.1 (13.1)~ | +11.8 (14.2)~ | 43.5 / 42.9 / 21.1 / 416.6 |
| sizer on all six (K6 P6 U6 H6 M6 A6) | join 2.45 (LIVE-CAL) | +23.1 (21.4) | +19.5 (17.3) | +16.4 (17.2)~ | +3.6 (13.2)~ | +10.2 (14.2)~ | 41.2 / 42.9 / 24.0 / 371.9 |
| sizer on P6 + K6 ONLY | Native 1.28 | +25.0 (23.0) | +22.3 (17.3) | +18.9 (17.1) | +5.1 (11.9)~ | +11.5 (13.6)~ | 44.0 / 40.8 / 19.1 / 454.0 |
| sizer on P6 + K6 ONLY | join 2.45 (LIVE-CAL) | +22.5 (22.2) | +20.0 (17.1) | +16.6 (16.9)~ | +2.8 (12.0)~ | +9.9 (13.6)~ | 41.7 / 41.0 / 28.3 / 407.1 |
| sizer on P6 + K6 + A6 (= drop U6 H6 M6 from the list) | Native 1.28 | +25.8 (22.3) | +23.2 (17.0) | +19.8 (16.9) | +5.6 (11.9)~ | +11.6 (13.6)~ | 44.9 / 41.7 / 19.2 / 464.8 |
| sizer on P6 + K6 + A6 (= drop U6 H6 M6 from the list) | join 2.45 (LIVE-CAL) | +23.5 (21.3) | +21.0 (16.7) | +17.5 (16.6) | +3.3 (11.9)~ | +10.0 (13.6)~ | 42.7 / 41.8 / 28.4 / 421.3 |
| sizer on P6 alone | Native 1.28 | +22.0 (25.1)~ | +20.0 (17.8) | +17.0 (17.3)~ | +5.5 (11.9)~ | +10.7 (13.3)~ | 41.7 / 39.7 / 18.9 / 433.1 |
| sizer on P6 alone | join 2.45 (LIVE-CAL) | +19.8 (24.9)~ | +17.7 (17.8)~ | +14.9 (17.2)~ | +3.2 (12.0)~ | +9.1 (13.3)~ | 39.5 / 39.6 / 21.6 / 388.8 |
| sizer on K6 alone | Native 1.28 | +13.0 (20.7)~ | +10.7 (14.1)~ | +8.3 (14.4)~ | +2.0 (9.8)~ | +10.5 (11.9)~ | 32.4 / 39.8 / 51.5 / 273.2 |
| sizer on K6 alone | join 2.45 (LIVE-CAL) | +10.1 (20.3)~ | +8.3 (14.0)~ | +6.0 (14.3)~ | +0.0 (9.8)~ | +8.9 (11.9)~ | 30.0 / 40.4 / 61.1 / 224.9 |
| no sizer (lots as planned, locks planned-lot R) | Native 1.28 | +9.9 (24.1)~ | +8.3 (15.7)~ | +6.3 (15.5)~ | +2.2 (9.4)~ | +9.7 (11.8)~ | 30.0 / 39.9 / 43.9 / 202.9 |
| no sizer (lots as planned, locks planned-lot R) | join 2.45 (LIVE-CAL) | +7.4 (24.2)~ | +6.1 (15.7)~ | +4.2 (15.4)~ | +0.4 (9.4)~ | +8.1 (11.8)~ | 27.8 / 40.1 / 47.9 / 157.0 |
| stack WITHOUT U6 H6 M6 (lot 0), sizer on K6 P6 A6; base = that stack's own as-is | Native 1.28 | +22.2 (23.0)~ | +19.1 (16.7) | +16.3 (16.2) | +6.8 (10.6)~ | +8.9 (12.4)~ | 32.9 / 36.6 / 28.3 / 281.7 |
| stack WITHOUT U6 H6 M6 (lot 0), sizer on K6 P6 A6; base = that stack's own as-is | join 2.45 (LIVE-CAL) | +20.7 (22.1)~ | +17.5 (16.4) | +14.8 (15.9)~ | +5.1 (10.6)~ | +7.8 (12.4)~ | 31.4 / 36.6 / 30.3 / 252.5 |
| **(b) K6 at MARKET (no split), other books 70/30, vs K6 split** | | | | | | | |
| sizer all six, K6 split (= (d)) | Native 1.28 | +25.5 (22.5) | +21.8 (17.6) | +18.7 (17.5) | +6.1 (13.1)~ | +11.8 (14.2)~ | 43.5 / 42.9 / 21.1 / 416.6 |
| sizer all six, K6 split (= (d)) | join 2.45 (LIVE-CAL) | +23.1 (21.4) | +19.5 (17.3) | +16.4 (17.2)~ | +3.6 (13.2)~ | +10.2 (14.2)~ | 41.2 / 42.9 / 24.0 / 371.9 |
| sizer all six, K6 MARKET | Native 1.28 | +23.2 (21.3) | +21.1 (17.0) | +18.3 (17.0) | +5.4 (13.0)~ | +12.0 (13.6)~ | 42.8 / 42.8 / 25.2 / 413.4 |
| sizer all six, K6 MARKET | join 2.45 (LIVE-CAL) | +21.1 (20.7) | +19.0 (16.8) | +16.2 (16.8)~ | +3.0 (13.1)~ | +10.3 (13.6)~ | 40.7 / 42.6 / 29.3 / 372.4 |
| sizer P6+K6, K6 split | Native 1.28 | +25.0 (23.0) | +22.3 (17.3) | +18.9 (17.1) | +5.1 (11.9)~ | +11.5 (13.6)~ | 44.0 / 40.8 / 19.1 / 454.0 |
| sizer P6+K6, K6 split | join 2.45 (LIVE-CAL) | +22.5 (22.2) | +20.0 (17.1) | +16.6 (16.9)~ | +2.8 (12.0)~ | +9.9 (13.6)~ | 41.7 / 41.0 / 28.3 / 407.1 |
| sizer P6+K6, K6 MARKET | Native 1.28 | +22.7 (22.1) | +21.6 (16.8) | +18.5 (16.6) | +4.4 (11.8)~ | +11.6 (13.0)~ | 43.3 / 41.0 / 30.0 / 450.7 |
| sizer P6+K6, K6 MARKET | join 2.45 (LIVE-CAL) | +20.5 (21.7)~ | +19.4 (16.7) | +16.4 (16.5)~ | +2.2 (11.9)~ | +10.0 (12.9)~ | 41.1 / 40.9 / 34.0 / 407.2 |
| sizer P6+K6, K6 MARKET, add slip +0.45 | Native 1.28 | +22.4 (22.1) | +21.3 (16.8) | +18.2 (16.6) | +4.2 (11.8)~ | +11.4 (12.9)~ | 43.0 / 40.9 / 30.3 / 445.4 |
| sizer P6+K6, K6 MARKET, add slip +0.45 | join 2.45 (LIVE-CAL) | +20.1 (21.7)~ | +19.1 (16.7) | +16.1 (16.5)~ | +1.9 (11.8)~ | +9.8 (12.9)~ | 40.8 / 40.9 / 34.4 / 401.9 |
| **(c) NY-PM end skip 14:40:00-15:00:00 ET (clock, signal time, all books) added** | | | | | | | |
| sizer all six, K6 split, + skip | Native 1.28 | +25.6 (22.9) | +21.8 (17.8) | +18.6 (17.7) | +5.8 (13.0)~ | +12.0 (14.3)~ | 43.5 / 42.8 / 21.1 / 416.6 |
| sizer all six, K6 split, + skip | join 2.45 (LIVE-CAL) | +23.2 (21.8) | +19.5 (17.5) | +16.4 (17.4)~ | +3.4 (13.1)~ | +10.4 (14.3)~ | 41.2 / 42.9 / 24.0 / 372.0 |
| sizer P6+K6, K6 split, + skip | Native 1.28 | +25.1 (23.5) | +22.3 (17.5) | +18.9 (17.3) | +4.9 (11.9)~ | +11.7 (13.7)~ | 44.0 / 40.7 / 19.1 / 453.9 |
| sizer P6+K6, K6 split, + skip | join 2.45 (LIVE-CAL) | +22.6 (22.7)~ | +20.0 (17.3) | +16.6 (17.1)~ | +2.6 (11.9)~ | +10.1 (13.7)~ | 41.7 / 41.0 / 28.3 / 407.1 |
| sizer P6+K6, K6 market, + skip | Native 1.28 | +22.8 (22.6) | +21.6 (17.0) | +18.5 (16.8) | +4.3 (11.8)~ | +12.0 (13.1)~ | 43.3 / 40.9 / 30.0 / 450.3 |
| sizer P6+K6, K6 market, + skip | join 2.45 (LIVE-CAL) | +20.5 (22.2)~ | +19.4 (16.9) | +16.4 (16.7)~ | +2.0 (11.8)~ | +10.3 (13.1)~ | 41.1 / 40.9 / 34.0 / 407.0 |
| **SUNDAY CANDIDATE = (a) sizer P6+K6 only + (b) K6 market + (c) NY-PM end skip; integer lots, running-max locks, A6 = PB7, add slip +0.25** | | | | | | | |
| Sunday candidate | Native 1.28 | +22.8 (22.6) | +21.6 (17.0) | +18.5 (16.8) | +4.3 (11.8)~ | +12.0 (13.1)~ | 43.3 / 40.9 / 30.0 / 450.3 |
| Sunday candidate | join 2.45 (LIVE-CAL) | +20.5 (22.2)~ | +19.4 (16.9) | +16.4 (16.7)~ | +2.0 (11.8)~ | +10.3 (13.1)~ | 41.1 / 40.9 / 34.0 / 407.0 |
| Sunday candidate | A/B parity mix | +21.1 (22.6)~ | +20.3 (17.0) | +17.3 (16.8) | +3.1 (11.8)~ | +11.2 (13.1)~ | 42.0 / 41.2 / 31.6 / 421.8 |
| Sunday candidate, add slip +0.45 stress | Native 1.28 | +22.5 (22.6)~ | +21.3 (17.0) | +18.2 (16.8) | +4.0 (11.8)~ | +11.8 (13.1)~ | 43.0 / 40.9 / 30.3 / 445.0 |
| Sunday candidate, add slip +0.45 stress | join 2.45 (LIVE-CAL) | +20.2 (22.2)~ | +19.1 (16.9) | +16.1 (16.7)~ | +1.8 (11.8)~ | +10.1 (13.1)~ | 40.8 / 40.9 / 34.4 / 401.7 |
| same with sizer on all six (CANDall6) | Native 1.28 | +23.3 (21.7) | +21.1 (17.2) | +18.3 (17.1) | +5.2 (12.9)~ | +12.3 (13.7)~ | 42.8 / 42.7 / 25.2 / 413.0 |
| same with sizer on all six (CANDall6) | join 2.45 (LIVE-CAL) | +21.2 (21.1) | +19.0 (17.0) | +16.1 (16.9)~ | +2.8 (13.0)~ | +10.7 (13.7)~ | 40.7 / 42.5 / 29.3 / 372.2 |

## 1. Stack risk lines (all windows; $k per week, weekly series of the lock-engine stack)

| row | window | weeks | mean | SD | maxDD (weekly-cum) | worst-20 sum |
|---|---|---|---|---|---|---|
| as-is stack | L3M | 14 | 12.2 | 45.5 | 88.0 | 170.1 |
| as-is stack | L6M | 28 | 21.7 | 43.9 | 88.0 | 58.0 |
| as-is stack | HOLD | 32 | 21.9 | 53.8 | 144.2 | -187.1 |
| as-is stack | PRE | 75 | 18.6 | 50.4 | 162.0 | -810.6 |
| as-is stack | X' | 44 | -3.4 | 29.0 | 316.5 | -572.1 |
| D6 composite (d), Native 1.28 | L3M | 14 | 37.7 | 43.3 | 14.3 | 527.8 |
| D6 composite (d), Native 1.28 | L6M | 28 | 43.5 | 42.9 | 21.1 | 416.6 |
| D6 composite (d), Native 1.28 | HOLD | 32 | 40.5 | 52.3 | 100.9 | 178.2 |
| D6 composite (d), Native 1.28 | PRE | 75 | 24.7 | 55.7 | 222.6 | -835.5 |
| D6 composite (d), Native 1.28 | X' | 44 | 8.4 | 32.6 | 115.1 | -409.2 |
| D6 composite (d), join 2.45 | L3M | 14 | 35.3 | 43.5 | 23.6 | 494.2 |
| D6 composite (d), join 2.45 | L6M | 28 | 41.2 | 42.9 | 24.0 | 371.9 |
| D6 composite (d), join 2.45 | HOLD | 32 | 38.3 | 52.4 | 108.6 | 130.7 |
| D6 composite (d), join 2.45 | PRE | 75 | 22.3 | 55.9 | 242.9 | -889.4 |
| D6 composite (d), join 2.45 | X' | 44 | 6.8 | 32.7 | 126.7 | -445.5 |
| (a) sizer P6+K6, Native | L3M | 14 | 37.2 | 41.6 | 19.1 | 520.8 |
| (a) sizer P6+K6, Native | L6M | 28 | 44.0 | 40.8 | 19.1 | 454.0 |
| (a) sizer P6+K6, Native | HOLD | 32 | 40.8 | 49.3 | 99.5 | 225.1 |
| (a) sizer P6+K6, Native | PRE | 75 | 23.7 | 52.8 | 231.3 | -754.4 |
| (a) sizer P6+K6, Native | X' | 44 | 8.1 | 31.5 | 113.8 | -403.7 |
| K6 market, sizer all six, Native | L3M | 14 | 35.4 | 44.3 | 25.2 | 495.4 |
| K6 market, sizer all six, Native | L6M | 28 | 42.8 | 42.8 | 25.2 | 413.4 |
| K6 market, sizer all six, Native | HOLD | 32 | 40.2 | 52.5 | 99.0 | 173.2 |
| K6 market, sizer all six, Native | PRE | 75 | 24.0 | 55.6 | 221.6 | -840.7 |
| K6 market, sizer all six, Native | X' | 44 | 8.6 | 32.0 | 108.3 | -397.0 |
| SUNDAY CANDIDATE, Native 1.28 | L3M | 14 | 35.0 | 42.5 | 30.0 | 489.4 |
| SUNDAY CANDIDATE, Native 1.28 | L6M | 28 | 43.3 | 40.9 | 30.0 | 450.3 |
| SUNDAY CANDIDATE, Native 1.28 | HOLD | 32 | 40.4 | 49.5 | 97.1 | 218.5 |
| SUNDAY CANDIDATE, Native 1.28 | PRE | 75 | 22.9 | 52.6 | 229.1 | -764.6 |
| SUNDAY CANDIDATE, Native 1.28 | X' | 44 | 8.6 | 31.1 | 105.8 | -389.1 |
| SUNDAY CANDIDATE, join 2.45 | L3M | 14 | 32.7 | 42.4 | 34.0 | 457.4 |
| SUNDAY CANDIDATE, join 2.45 | L6M | 28 | 41.1 | 40.9 | 34.0 | 407.0 |
| SUNDAY CANDIDATE, join 2.45 | HOLD | 32 | 38.2 | 49.6 | 102.3 | 175.9 |
| SUNDAY CANDIDATE, join 2.45 | PRE | 75 | 20.6 | 52.7 | 247.6 | -814.8 |
| SUNDAY CANDIDATE, join 2.45 | X' | 44 | 6.9 | 31.2 | 117.3 | -424.6 |
| no sizer (integer, planned-lot locks), Native | L3M | 14 | 22.0 | 36.3 | 43.9 | 308.6 |
| no sizer (integer, planned-lot locks), Native | L6M | 28 | 30.0 | 39.9 | 43.9 | 202.9 |
| no sizer (integer, planned-lot locks), Native | HOLD | 32 | 28.2 | 44.1 | 76.1 | 15.2 |
| no sizer (integer, planned-lot locks), Native | PRE | 75 | 20.8 | 45.4 | 137.5 | -658.4 |
| no sizer (integer, planned-lot locks), Native | X' | 44 | 6.3 | 26.8 | 160.1 | -369.5 |

Reading: windows have 14 (L3M), 28 (L6M), 32 (HOLD), 75 (PRE), 44 (X') weeks, so 'worst-20' is most of L6M and L3M and is a positive number there; compare it across rows, it is not an absolute loss. The D6 composite and the candidate roughly double the L6M weekly mean of the as-is stack (21.7 -> 43.5 / 43.3) with an equal or smaller weekly SD (43.9 -> 42.9 / 40.9) and a much smaller weekly-cumulative maxDD in L6M (88 -> 21 / 30), HOLD (144 -> 101 / 97) and X' (317 -> 115 / 106). They are NOT tail-safer in PRE: maxDD 162 -> 223 (D6) / 229 (candidate) and worst-20 -811 -> -836 (D6) / -765 (candidate); the ER sizer raises the average lot (integer half-up), so these rows are not equal-risk rows. The sizer-less integer composite has the smallest SD (39.9 L6M, 26.8 X') and PRE maxDD 138 but gives up 13.5k of mean; the candidate has a lower SD than the all-six D6 composite in every window (40.9 vs 42.9 L6M, 52.6 vs 55.7 PRE) at nearly the same mean (L6M 43.3 vs 43.5, L3M 35.0 vs 37.7, PRE 22.9 vs 24.7): the sizer is off on U6 H6 M6 and K6 is at market there.

## 2. Tie-out (0) and the PB7 replacement (d) in detail

Tie-out: `ref_orig.py` runs the ORIGINAL SS-2 engine (library PB): fractional composite minus as-is = +19.4 (24.1) | +18.5 (17.4) | +16.2 (16.8) | +4.7 (13.4) | +12.5 (14.7) at Native, +17.1 / +16.2 / +13.9 / +2.3 / +10.8 at the join 2.45 (SS-2 published +18.5 / +16.2 / +4.7 / +12.5 and LIVE-CAL +16.2 / +13.9 / +2.3 / +10.8: exact); the integer line with library PB in every session = +25.0 / +22.8 / +19.3 / +7.4 / +12.9 (SS-2 section 3b: +22.8 / +19.3 / +7.4 / +12.9: exact). Decomposition of the PB -> PB7 step at integer lots, L6M Native: library PB all sessions +22.8; library PB Asia only +22.4 (-0.4, the user's A6 session list); PB7 Asia only +21.8 (-0.6, the engine). A6 itself is worth about nothing at one lot: its candidate book line is 0.5k a week (L6M), delta vs its own as-is -0.1k (section 6).

**PB7 series (what A6 is in this report).** PbEngine Pb7Rules = `bars_eng/be_lib.eng_PB7` (PB7_PB5_depth_atr0.5_W15_s+0: 10-min Supertrend(10,3) regime, level = running extreme of the regime segment -0.5 x ATR14(5-min, as-of), first touch, trigger T1 = the bar closes back in the trend direction beyond the level, W 15 min) on the aux 1-min bars, market entry at the decision second + 1 tick adverse, 60/60 bracket, flat 16:55 ET, costs stop 1.01 / time 0.995 / target year correction (N basis: target at nominal), fee 0.242. Rows `pb7_rows.parquet`: 17,031 signals 2023-04..2026-02 WITHOUT the cross-session busy rule (the lock engine re-applies the one-position rule on the live-session rows only; with the bars_eng busy rule the series is the control table `ctl_PB7` exactly: 3,418 rows, identical decision seconds, sides and exit types). Rows enter the engine as book 'PB' (tid 12,000,000+, appended last so every row-aligned cache keeps its alignment; the library PB rows are relabelled 'PBL' and are outside the stack). Identity tests (`sdlib.py`, t_sd2.py): (i) ER(20) 5m at the signal recomputed for the 4,049 library PB rows equals the stored trendgate value (max abs diff 3e-8, class agreement 100%); (ii) the 8 zone-skip feature streams recomputed with the POI kernel for the library PB rows equal the stored `features.npy` on 100% of rows; (iii) the PB rebuilt with the same mechanics vs the library PB rows: 3,999 of 4,049 library entries found by fill second (the other 50 are library-only, 103 rebuilt-only), exit type equal 99.5%, exit second equal 70% (the library fill price differs by a few ticks, which moves the 60-pt levels by those ticks; the booked points are the bracket +/-60 so the dollars are unaffected), side and session 100%.

## 3. (a) Sizer books: details

| comparison (first minus second), paired | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| sizer P6+K6 only minus all six | -0.5 (9.4)~ | +0.5 (5.5)~ | +0.2 (5.0)~ | -1.0 (4.3)~ | -0.4 (3.2)~ |
| sizer P6+K6+A6 minus all six | +0.2 (9.0)~ | +1.4 (5.3)~ | +1.1 (4.8)~ | -0.5 (4.0)~ | -0.2 (3.3)~ |
| sizer P6+K6+A6 minus P6+K6 | +0.7 (2.3)~ | +0.9 (1.4)~ | +0.9 (1.2)~ | +0.5 (0.7)~ | +0.2 (0.7)~ |
| sizer P6 alone minus all six | -3.6 (12.9)~ | -1.8 (8.0)~ | -1.7 (7.2)~ | -0.6 (4.7)~ | -1.2 (4.4)~ |
| sizer K6 alone minus all six | -12.5 (22.6)~ | -11.1 (13.2)~ | -10.4 (13.4)~ | -4.1 (8.8)~ | -1.4 (8.4)~ |
| all six minus no sizer | +15.7 (25.4)~ | +13.5 (15.4)~ | +12.3 (15.2)~ | +3.8 (8.6)~ | +2.2 (9.1)~ |
| P6+K6 minus no sizer | +15.2 (21.3)~ | +14.0 (13.2) | +12.6 (13.0)~ | +2.9 (6.7)~ | +1.8 (7.6)~ |
| all six minus U6 (sizer off on U6 only) | +1.4 (4.9)~ | +0.9 (2.8)~ | +0.6 (2.6)~ | -0.0 (1.7)~ | -0.0 (1.6)~ |
| all six minus H6 off | -1.1 (5.7)~ | -0.1 (3.8)~ | -0.0 (3.4)~ | -0.3 (2.5)~ | +0.5 (1.7)~ |
| all six minus M6 off | -0.1 (4.5)~ | +0.6 (2.6)~ | +0.6 (2.4)~ | -0.2 (1.7)~ | -0.7 (1.7)~ |
| all six minus A6 off | -0.7 (2.3)~ | -0.9 (1.4)~ | -0.9 (1.2)~ | -0.5 (0.7)~ | -0.2 (0.7)~ |
| all six minus K6 off | -3.2 (5.9)~ | -2.4 (4.5)~ | -2.0 (4.1)~ | +0.4 (2.3)~ | -0.8 (2.1)~ |
| all six minus P6 off | -11.8 (19.1)~ | -11.5 (11.3) | -10.5 (11.3)~ | -3.2 (6.8)~ | -1.0 (7.1)~ |
| stack without U6 H6 M6 (sz K6 P6 A6) minus the full stack (sz K6 P6 A6), lock-engine totals | -10.2 (13.1)~ | -12.0 (9.0) | -10.8 (8.4) | -5.9 (5.8) | -0.9 (4.9)~ |
| sizer single-book alone vs no sizer: P6 / K6 / A6 / U6 / H6 / M6 (L6M, $k) | +11.6 / +2.4 / +1.0 / -0.9 / +0.0 / -0.6 | | | | |

(Native 1.28. Join 2.45:)

| comparison (first minus second), paired | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| sizer P6+K6 only minus all six | -0.7 (9.3)~ | +0.4 (5.5)~ | +0.2 (5.0)~ | -0.8 (4.3)~ | -0.3 (3.3)~ |
| sizer P6+K6+A6 minus all six | +0.3 (9.1)~ | +1.5 (5.4)~ | +1.1 (4.9)~ | -0.4 (4.1)~ | -0.2 (3.4)~ |
| sizer P6+K6+A6 minus P6+K6 | +1.0 (1.8)~ | +1.0 (1.2)~ | +0.9 (1.1)~ | +0.5 (0.7)~ | +0.2 (0.7)~ |
| sizer P6 alone minus all six | -3.4 (13.0)~ | -1.8 (8.0)~ | -1.5 (7.2)~ | -0.5 (4.9)~ | -1.1 (4.4)~ |
| sizer K6 alone minus all six | -13.0 (22.4)~ | -11.2 (13.2)~ | -10.4 (13.4)~ | -3.6 (8.9)~ | -1.3 (8.4)~ |
| all six minus no sizer | +15.7 (25.1)~ | +13.5 (15.3)~ | +12.2 (15.2)~ | +3.2 (8.7)~ | +2.1 (9.1)~ |
| P6+K6 minus no sizer | +15.1 (21.2)~ | +13.9 (13.2) | +12.4 (13.0)~ | +2.4 (6.7)~ | +1.8 (7.7)~ |
| all six minus U6 (sizer off on U6 only) | +1.4 (4.9)~ | +1.0 (2.8)~ | +0.6 (2.6)~ | +0.0 (1.7)~ | -0.0 (1.6)~ |
| all six minus H6 off | -1.1 (5.8)~ | -0.1 (3.8)~ | -0.1 (3.5)~ | -0.2 (2.5)~ | +0.5 (1.8)~ |
| all six minus M6 off | +0.0 (4.5)~ | +0.6 (2.6)~ | +0.6 (2.4)~ | -0.1 (1.7)~ | -0.7 (1.7)~ |
| all six minus A6 off | -1.0 (1.8)~ | -1.0 (1.2)~ | -0.9 (1.1)~ | -0.5 (0.7)~ | -0.2 (0.7)~ |
| all six minus K6 off | -2.7 (6.5)~ | -2.2 (4.7)~ | -1.7 (4.2)~ | +0.4 (2.3)~ | -0.8 (2.1)~ |
| all six minus P6 off | -12.3 (19.0)~ | -11.7 (11.3) | -10.7 (11.3)~ | -2.7 (7.0)~ | -1.0 (7.1)~ |
| stack without U6 H6 M6 (sz K6 P6 A6) minus the full stack (sz K6 P6 A6), lock-engine totals | -9.5 (13.1)~ | -11.3 (9.0) | -10.1 (8.5) | -5.3 (5.8)~ | -0.4 (5.0)~ |
| sizer single-book alone vs no sizer: P6 / K6 / A6 / U6 / H6 / M6 (L6M, $k) | +11.7 / +2.2 / +1.0 / -1.0 / +0.1 / -0.6 | | | | |

Reading. (1) The whole sizer gain is P6 plus the locks: sizer on P6 alone -1.8 (8.0) below the all-six list, K6 alone -11.1 (13.2). (2) The ER-1 per-book verdicts (U6, H6, M6 DROP; K6 weak keep; P6 lean keep; A6 inconclusive) are reproduced at the integer lots of this composite with the signs ER-1 had: removing the sizer on U6 / H6 / M6 changes the stack by +0.9 / -0.1 / +0.6 (L6M), - nothing; removing it on A6 costs -0.9 (1.4) L6M, which is the one book-level difference with an MDE under 1.5k, and is the 1-to-2-lots rule on a book with one lot. (3) The sizer is worth +13.5 (15.4) L6M over no sizer on all six, +14.0 (13.2) on P6+K6 (the only row that clears its MDE), +3.8 / +2.9 in PRE: inside MDE in PRE and X'. (4) 'Drop U6 H6 M6 from the STACK' (not from the sizer list) is a different and expensive change: the stack without them is -12.0 (9.0) L6M, -10.8 (8.4) HOLD, -5.9 (5.8) PRE lower in $ level than the stack with them (same K6 P6 A6 sizer), because H6 (+4.0k) and M6 / U6 add to the composite; this table does not recommend removing books.

## 4. (b) K6 at market vs K6 split: details

| comparison (first minus second), paired | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| sizer all six: K6 market minus K6 split (add +0.25) | -2.3 (3.7)~ | -0.7 (2.4)~ | -0.4 (2.2)~ | -0.7 (1.2)~ | +0.1 (1.1)~ |
| sizer P6+K6: K6 market minus K6 split (add +0.25) | -2.3 (3.7)~ | -0.7 (2.4)~ | -0.4 (2.2)~ | -0.7 (1.1)~ | +0.1 (1.1)~ |
| sizer P6+K6+A6: K6 market minus K6 split (add +0.25) | -2.3 (3.7)~ | -0.7 (2.4)~ | -0.4 (2.2)~ | -0.7 (1.2)~ | +0.1 (1.1)~ |
| sizer all six: K6 market minus K6 split, STRESS +0.45 (split arm pays 0.45) | -2.2 (3.6)~ | -0.6 (2.4)~ | -0.3 (2.2)~ | -0.6 (1.1)~ | +0.2 (1.1)~ |
| sizer P6+K6: K6 market minus K6 split, STRESS +0.45 | -2.2 (3.6)~ | -0.6 (2.4)~ | -0.3 (2.2)~ | -0.6 (1.1)~ | +0.2 (1.1)~ |
| no sizer: K6 market minus K6 split | -1.9 (5.8)~ | -0.4 (3.1)~ | -0.3 (2.7)~ | -0.4 (1.0)~ | +0.2 (1.0)~ |
| sizer all six, ideal (no slip) both arms | -2.9 (3.9)~ | -1.0 (2.5)~ | -0.7 (2.3)~ | -0.8 (1.2)~ | +0.1 (1.1)~ |
| K6 book only (all-six sizer): market minus split | -2.3 (3.7)~ | -0.7 (2.4)~ | -0.4 (2.2)~ | -0.6 (1.2)~ | +0.1 (1.1)~ |
| composite level, K6 split / K6 market, L6M $k/wk | 43.5 / 42.8 | | | | |

(Native 1.28. Join 2.45:)

| comparison (first minus second), paired | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| sizer all six: K6 market minus K6 split (add +0.25) | -2.0 (3.2)~ | -0.6 (2.2)~ | -0.3 (2.0)~ | -0.6 (1.1)~ | +0.1 (1.1)~ |
| sizer P6+K6: K6 market minus K6 split (add +0.25) | -2.0 (3.2)~ | -0.6 (2.2)~ | -0.3 (2.0)~ | -0.6 (1.1)~ | +0.1 (1.1)~ |
| sizer P6+K6+A6: K6 market minus K6 split (add +0.25) | -2.0 (3.2)~ | -0.6 (2.2)~ | -0.3 (2.0)~ | -0.6 (1.1)~ | +0.1 (1.1)~ |
| sizer all six: K6 market minus K6 split, STRESS +0.45 (split arm pays 0.45) | -1.9 (3.2)~ | -0.5 (2.1)~ | -0.2 (2.0)~ | -0.6 (1.1)~ | +0.1 (1.1)~ |
| sizer P6+K6: K6 market minus K6 split, STRESS +0.45 | -1.9 (3.2)~ | -0.5 (2.1)~ | -0.2 (2.0)~ | -0.6 (1.1)~ | +0.1 (1.1)~ |
| no sizer: K6 market minus K6 split | -2.1 (6.2)~ | -0.7 (3.3)~ | -0.6 (2.9)~ | -0.3 (1.1)~ | +0.2 (1.1)~ |
| sizer all six, ideal (no slip) both arms | -2.5 (3.6)~ | -0.8 (2.4)~ | -0.5 (2.2)~ | -0.8 (1.1)~ | +0.0 (1.1)~ |
| K6 book only (all-six sizer): market minus split | -2.0 (3.2)~ | -0.6 (2.1)~ | -0.3 (2.0)~ | -0.6 (1.1)~ | +0.1 (1.1)~ |
| composite level, K6 split / K6 market, L6M $k/wk | 41.2 / 40.7 | | | | |

Reading. The K6 add is worth +0.4 to +0.7k/wk L6M / HOLD / PRE in the composite and -0.1 in X' (market slightly better); every cell is inside its MDE (1.1-3.7k), the sign is the same at the model (+0.25) and stress (+0.45) slippage, with and without the sizer, at Native and join. The UF-ENTRY C9 'drop the add on K6' (-3.0k L6M at research lots 5.2 on the book alone, plain stack) is a different context: scaled to 2 lots it is about -1.2k and here the K6 book alone with no sizer and the same rules is +0.2 (2.4) L6M / +0.2 (2.1) HOLD / -0.5 (1.0) PRE / +0.2 (1.0) X' (market minus split, Native, i.e. the add costs 0.2k there) - both inside MDE, neither supports a change; the decision number for the add is -0.7k a week at market (K6 split = +21.8 composite, K6 market = +21.1 L6M).

## 5. (c) NY-PM end skip 14:40:00-15:00:00 ET: details

| comparison (first minus second), paired | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| sizer all six, K6 split: + skip minus without | +0.1 (1.1)~ | +0.0 (0.8)~ | -0.0 (0.7)~ | -0.2 (0.3)~ | +0.2 (0.7)~ |
| sizer P6+K6, K6 split: + skip minus without | +0.1 (1.1)~ | +0.0 (0.8)~ | -0.0 (0.7)~ | -0.2 (0.3)~ | +0.2 (0.7)~ |
| sizer P6+K6, K6 market: + skip minus without | +0.1 (1.1)~ | -0.0 (0.8)~ | -0.0 (0.7)~ | -0.2 (0.3)~ | +0.4 (0.7)~ |
| no sizer, K6 split: + skip minus without | +0.0 (0.1)~ | -0.1 (0.4)~ | -0.1 (0.4)~ | -0.0 (0.3)~ | +0.1 (0.6)~ |
| no sizer, K6 market: + skip minus without | +0.0 (0.1)~ | -0.1 (0.4)~ | -0.1 (0.4)~ | -0.1 (0.3)~ | +0.2 (0.5)~ |
| per book, sizer P6+K6 K6 market, skip minus without: K6 / others (L6M $k) | -0.01 / -0.00 | | | | |

The skip is a signal-time clock block on every book (entry minute of the signal in [14:40, 15:00)); in the 20 minutes K6 sees about 0.7 signals a week, A6 (PB7) 1.7 but A6 trades Asia only, P6 / U6 / H6 / M6 have no NY-PM lot, so live it is a K6-only rule worth 0.0 +/- 0.8k. A signal skipped by the clock is not a child of the lock engine, so it does not feed the running max of SizeMult (NP-1's spec says it should; K6 only, negligible).

## 6. Sunday candidate, add-slippage labels, leave-one-out of the pieces

Add slippage (the modelled cost per add lot; K6 at market has no add; the +0.25 / +0.45 labels apply to the 30% adds of U6 H6 P6 M6 and to the P6 PE-confirmation add):

| add-slip label, minus the same composite with NO add slip (ideal fills) [clock skip is in the first rows only] | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| Sunday candidate (add slip +0.25 model) | -0.3 (1.1)~ | -0.3 (0.8)~ | -0.3 (0.7)~ | -0.5 (0.4) | +0.1 (0.7)~ |
| Sunday candidate STRESS +0.45 | -0.6 (1.1)~ | -0.6 (0.8)~ | -0.6 (0.7)~ | -0.8 (0.4) | -0.0 (0.7)~ |
| D6 composite (sizer all six, K6 split): +0.25 minus none | -0.8 (1.2)~ | -0.6 (0.6) | -0.6 (0.5) | -0.4 (0.1) | -0.3 (0.0) |
| D6 composite (sizer all six, K6 split): +0.45 minus none | -1.3 (1.2) | -1.2 (0.8) | -1.1 (0.7) | -0.8 (0.1) | -0.5 (0.1) |

Leave-one-out at integer lots, contribution of each piece = composite minus composite-without-it, paired (Native 1.28; `~` = inside MDE):

| composite | piece removed: contribution = composite minus composite-without (paired) | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| CAND | Asia-stopped cut | +1.1 (4.1)~ | +0.4 (3.1)~ | -0.5 (3.8)~ | -0.0 (2.3)~ | +0.3 (2.1)~ |
| CAND | PE three-bar confirmation (P6 enters at the signal, 70/30) | +7.5 (16.2)~ | +4.1 (9.8)~ | +4.3 (9.3)~ | +0.6 (5.8)~ | -1.0 (6.3)~ |
| CAND | zone skip (clock skip kept) | +6.0 (13.2)~ | +6.4 (10.0)~ | +4.6 (10.6)~ | +0.8 (8.3)~ | +4.8 (7.7)~ |
| CAND | 70/30 split (all books market; PE confirmation at market) | +6.4 (9.1)~ | +3.6 (5.1)~ | +3.6 (4.4)~ | +0.7 (3.7)~ | +0.9 (2.4)~ |
| CAND | ER sizer + running-max locks | +14.8 (21.6)~ | +13.7 (13.1) | +12.6 (13.0)~ | +2.5 (6.6)~ | +1.9 (7.7)~ |
| CAND | NY-PM end skip | +0.1 (1.1)~ | -0.0 (0.8)~ | -0.0 (0.7)~ | -0.2 (0.3)~ | +0.4 (0.7)~ |
| CAND | PE confirmation at MARKET without the 70/30 (confirmation kept) | +1.8 (3.6)~ | +1.0 (2.3)~ | +1.0 (2.2)~ | +0.0 (1.2)~ | +0.0 (1.3)~ |
| CANDall6 | Asia-stopped cut | +0.6 (3.6)~ | -0.0 (3.0)~ | -0.9 (3.8)~ | -0.1 (2.1)~ | +0.5 (2.1)~ |
| CANDall6 | PE three-bar confirmation (P6 enters at the signal, 70/30) | +7.4 (16.2)~ | +4.1 (9.8)~ | +4.3 (9.3)~ | +0.6 (5.8)~ | -1.0 (6.3)~ |
| CANDall6 | zone skip (clock skip kept) | +3.6 (11.9)~ | +3.7 (9.5)~ | +1.9 (10.2)~ | +2.1 (8.5)~ | +3.5 (7.8)~ |
| CANDall6 | 70/30 split (all books market; PE confirmation at market) | +5.7 (9.7)~ | +3.6 (5.4)~ | +3.7 (4.7)~ | +0.8 (3.8)~ | +0.7 (2.5)~ |
| CANDall6 | ER sizer + running-max locks | +15.3 (25.9)~ | +13.2 (15.3)~ | +12.3 (15.3)~ | +3.4 (8.6)~ | +2.3 (9.1)~ |
| CANDall6 | NY-PM end skip | +0.1 (1.1)~ | -0.0 (0.8)~ | -0.0 (0.7)~ | -0.2 (0.3)~ | +0.4 (0.7)~ |
| D6int | Asia-stopped cut | +0.2 (3.7)~ | -0.4 (3.1)~ | -1.3 (3.8)~ | -0.1 (2.1)~ | +0.5 (2.1)~ |
| D6int | PE three-bar confirmation (P6 enters at the signal, 70/30) | +7.4 (16.2)~ | +4.1 (9.8)~ | +4.3 (9.3)~ | +0.6 (5.8)~ | -1.0 (6.3)~ |
| D6int | zone skip | +4.9 (11.4)~ | +4.8 (9.5)~ | +2.8 (10.3)~ | +2.6 (8.5)~ | +3.4 (7.8)~ |
| D6int | 70/30 split (all books market; PE confirmation at market) | +8.0 (9.0)~ | +4.3 (5.5)~ | +4.1 (4.8)~ | +1.5 (4.1)~ | +0.6 (3.2)~ |
| D6int | ER sizer + running-max locks | +15.7 (25.4)~ | +13.5 (15.4)~ | +12.3 (15.2)~ | +3.8 (8.6)~ | +2.2 (9.1)~ |

(join 2.45:)

| composite | piece removed: contribution = composite minus composite-without (paired) | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| CAND | Asia-stopped cut | +1.2 (4.2)~ | +0.6 (3.2)~ | -0.3 (3.8)~ | +0.3 (2.3)~ | +0.6 (2.3)~ |
| CAND | PE three-bar confirmation (P6 enters at the signal, 70/30) | +8.4 (16.8)~ | +4.4 (10.2)~ | +4.7 (9.5)~ | +0.9 (5.8)~ | -0.9 (6.4)~ |
| CAND | zone skip (clock skip kept) | +7.1 (13.5)~ | +7.3 (10.3)~ | +5.3 (10.9)~ | +1.2 (8.4)~ | +5.2 (7.8)~ |
| CAND | 70/30 split (all books market; PE confirmation at market) | +6.4 (9.3)~ | +3.3 (5.2)~ | +3.4 (4.5)~ | +0.7 (3.8)~ | +0.9 (2.4)~ |
| CAND | ER sizer + running-max locks | +15.2 (21.3)~ | +14.1 (13.0) | +12.9 (13.0)~ | +1.9 (6.7)~ | +1.8 (7.7)~ |
| CAND | NY-PM end skip | +0.1 (1.2)~ | -0.0 (0.8)~ | -0.0 (0.7)~ | -0.2 (0.3)~ | +0.4 (0.7)~ |
| CAND | PE confirmation at MARKET without the 70/30 (confirmation kept) | +1.7 (3.6)~ | +1.0 (2.4)~ | +1.0 (2.2)~ | +0.0 (1.2)~ | -0.0 (1.4)~ |
| CANDall6 | Asia-stopped cut | +1.0 (3.7)~ | +0.3 (3.0)~ | -0.6 (3.8)~ | +0.2 (2.2)~ | +0.8 (2.2)~ |
| CANDall6 | PE three-bar confirmation (P6 enters at the signal, 70/30) | +8.4 (16.8)~ | +4.4 (10.2)~ | +4.7 (9.5)~ | +0.9 (5.8)~ | -0.9 (6.4)~ |
| CANDall6 | zone skip (clock skip kept) | +4.7 (12.4)~ | +4.6 (9.9)~ | +2.6 (10.4)~ | +2.4 (8.5)~ | +3.9 (7.9)~ |
| CANDall6 | 70/30 split (all books market; PE confirmation at market) | +5.6 (9.9)~ | +3.3 (5.5)~ | +3.5 (4.9)~ | +0.9 (3.8)~ | +0.7 (2.5)~ |
| CANDall6 | ER sizer + running-max locks | +15.8 (25.5)~ | +13.7 (15.2)~ | +12.6 (15.3)~ | +2.8 (8.7)~ | +2.2 (9.2)~ |
| CANDall6 | NY-PM end skip | +0.1 (1.2)~ | -0.0 (0.8)~ | -0.0 (0.7)~ | -0.2 (0.3)~ | +0.4 (0.7)~ |
| D6int | Asia-stopped cut | +0.7 (3.5)~ | -0.1 (3.1)~ | -1.0 (3.8)~ | +0.3 (2.2)~ | +0.7 (2.2)~ |
| D6int | PE three-bar confirmation (P6 enters at the signal, 70/30) | +8.4 (16.8)~ | +4.4 (10.2)~ | +4.7 (9.5)~ | +0.9 (5.8)~ | -0.9 (6.4)~ |
| D6int | zone skip | +5.6 (11.3)~ | +5.5 (9.8)~ | +3.3 (10.5)~ | +2.8 (8.6)~ | +3.9 (7.9)~ |
| D6int | 70/30 split (all books market; PE confirmation at market) | +7.6 (9.2)~ | +3.9 (5.6)~ | +3.7 (4.9)~ | +1.5 (4.1)~ | +0.6 (3.2)~ |
| D6int | ER sizer + running-max locks | +15.7 (25.1)~ | +13.5 (15.3)~ | +12.2 (15.2)~ | +3.2 (8.7)~ | +2.1 (9.1)~ |

Reading. The Asia-stopped cut contributes +0.4 (3.1) L6M, -0.5 (3.8) HOLD, 0.0 (2.3) PRE, +0.3 (2.1) X' in the Sunday candidate (+0.2/-0.4/-1.3/-0.1/+0.5 in the D6 composite; with the all-six sizer -0.0 / -0.9 / -0.1 / +0.5): zero within noise, never outside MDE, and by the SS-2 removal rule (remove only if removal improves L6M, HOLD, PRE and X' together) it stays (X' is positive). The PE three-bar confirmation contributes +4.1 (9.8) L6M, +4.3 (9.3) HOLD, +0.6 (5.8) PRE, -1.0 (6.3) X' (L3M +7.5): recent-positive, flat before, all inside MDE; the 70/30 on the confirmed P6 entry adds +1.0 (2.3) L6M over the confirmation at market. The zone skip (+6.4 (10.0) L6M) and the 70/30 split (+3.6 (5.1) L6M, with the PE confirmation at market in that arm) are positive in all four windows; the ER sizer + running-max locks is the piece that does the work (+13.7 (13.1) L6M, the only LOO cell that clears its MDE); the NY-PM skip is zero.

Per book, Sunday candidate vs as-is ($k/wk; the books' own series from the lock engine, Native 1.28):

| book | candidate $k/wk L3M | L6M | HOLD | PRE | X' | delta vs as-is L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|
| H6 | 10.3 | 9.4 | 8.2 | 2.2 | -0.0 | +4.0 | +3.4 | -0.5 | +0.8 |
| K6 | 1.6 | 4.9 | 4.1 | 3.1 | 1.2 | +1.7 | +1.5 | -0.9 | +1.4 |
| U6 | -0.9 | 0.9 | 0.9 | 2.4 | 2.1 | -0.1 | -0.3 | -0.2 | +1.5 |
| P6 | 23.4 | 26.0 | 25.3 | 12.4 | 5.9 | +15.9 | +13.7 | +6.0 | +7.5 |
| M6 | -0.1 | 1.6 | 1.6 | 1.7 | -1.1 | +0.3 | +0.2 | -0.0 | +0.4 |
| A6 (PB7) | 0.7 | 0.5 | 0.3 | 1.0 | 0.5 | -0.1 | +0.0 | -0.1 | +0.3 |

Kept trades per week:

| config (Native 1.28) | window | trades/wk kept | K6 | P6 | U6 | H6 | M6 | A6 |
|---|---|---|---|---|---|---|---|---|
| as-is | L6M | 84.3 | 23.0 | 19.4 | 6.2 | 14.4 | 15.2 | 6.1 |
| as-is | HOLD | 83.2 | 22.4 | 19.3 | 6.2 | 14.3 | 15.0 | 6.1 |
| as-is | PRE | 80.3 | 21.8 | 18.7 | 6.7 | 14.4 | 14.1 | 4.6 |
| D6 composite (d) | L6M | 89.2 | 29.2 | 20.4 | 4.4 | 13.8 | 16.0 | 5.4 |
| D6 composite (d) | HOLD | 85.6 | 27.6 | 19.6 | 4.4 | 13.2 | 15.4 | 5.3 |
| D6 composite (d) | PRE | 78.3 | 24.8 | 17.7 | 4.7 | 12.7 | 14.3 | 4.1 |
| Sunday candidate | L6M | 86.2 | 28.3 | 20.4 | 4.4 | 13.2 | 14.0 | 5.9 |
| Sunday candidate | HOLD | 82.8 | 26.7 | 19.6 | 4.3 | 12.8 | 13.6 | 5.8 |
| Sunday candidate | PRE | 75.3 | 23.7 | 17.7 | 4.8 | 12.3 | 12.7 | 4.2 |

## 7. Sensitivities and what could move the numbers

| variant (Native / join) | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| D6 composite: governors see the EFFECTIVE integer multiplier (ER-1 convention), Native 1.28 | +25.1 (22.3) | +21.0 (17.3) | +18.3 (17.0) | +5.4 (13.7)~ | +11.4 (14.1)~ |
| D6 composite: governors see the EFFECTIVE integer multiplier (ER-1 convention), join 2.45 (LIVE-CAL) | +22.3 (22.2) | +18.5 (17.3) | +15.9 (17.0)~ | +3.0 (13.7)~ | +9.7 (14.1)~ |
| Sunday candidate: effective-multiplier governors, Native 1.28 | +21.8 (22.5)~ | +20.6 (16.7) | +18.0 (16.3) | +3.5 (12.5)~ | +11.5 (13.0)~ |
| Sunday candidate: effective-multiplier governors, join 2.45 (LIVE-CAL) | +19.5 (22.6)~ | +18.4 (16.8) | +15.8 (16.3)~ | +1.2 (12.6)~ | +9.8 (13.0)~ |
| CANDall6: effective-multiplier governors, Native 1.28 | +23.1 (21.7) | +20.5 (16.8) | +18.0 (16.6) | +4.6 (13.6)~ | +11.9 (13.6)~ |
| CANDall6: effective-multiplier governors, join 2.45 (LIVE-CAL) | +20.6 (21.9)~ | +18.1 (17.0) | +15.8 (16.6)~ | +2.3 (13.6)~ | +10.2 (13.6)~ |
| fractional lots, no sizer (FRAC_nosizer) Native | +8.9 (23.1)~ | +7.7 (15.5)~ | +5.8 (15.3)~ | +2.6 (9.3)~ | +10.2 (11.7)~ |
| fractional lots, sizer all six (FRAC) Native | +19.4 (24.4)~ | +17.8 (17.3) | +15.5 (17.0)~ | +4.7 (13.8)~ | +11.1 (13.8)~ |
| integer lots, sizer all six Native (rounding adds average lots) | +25.5 (22.5) | +21.8 (17.6) | +18.7 (17.5) | +6.1 (13.1)~ | +11.8 (14.2)~ |
| integer, no sizer Native | +9.9 (24.1)~ | +8.3 (15.7)~ | +6.3 (15.5)~ | +2.2 (9.4)~ | +9.7 (11.8)~ |


* **Rounding rule.** The integer lines include the half-up rounding gain (~ +4k L6M over fractional); ER-1 measured the six-book sizer at +12.5 (half-up) / +10.5 (half-even) / +9.2 (floor) / +9.7 (fractional) L6M, so the rule D6 uses sets about +3k of the number. Governor multiplier: with the governors seeing the effective integer multiplier (ER-1 convention) instead of the trend multiplier the composite is 0.8 lower L6M (D6: +21.0 vs +21.8; candidate +20.6 vs +21.6).
* **H6 planned lot for the lock R**: the engine uses the book's largest session lot (H6 4 also on NY-AM, where the planned lot is 2); D6's BookR for a NY-AM H6 signal may be on 2 lots (smaller R, tighter locks); not run (H6 NY-AM trades about 2 a week).
* **Split after sizing**: the 70/30 fraction of the planned lot (K6 1/1) is applied to the sized lots; D6's rounding of 70% of a sized lot count is not specified.
* **Stop A/B**: the two stop variants differ by 2.2-2.3k L6M (Native better); the parity mix is a splice of two runs.
* **O6** is not in any number (no series); **M basis** (target correction) not run for the integer lots (the integer split is built on N in the library).
* Tier: CANDIDATE-RECENT at best (post-hoc-selected pieces, inside MDE in PRE and X', the cumulative-trial adjusted p is 1.00, SS-2 section 8); nothing here is PASS; the (a) (b) (c) comparisons are nulls in dollars: the sizer-books list, the K6 add and the NY-PM skip do not change the stack outside noise.

## 8. Files and bookkeeping

Pipeline: `pb7_build.py` -> `sdlib.py` (patches trades_arm: PB -> PBL, + PB7 rows; extends ER and zone features; pads the o73 caches) -> `run_all.py 1.28` / `2.45` (64 scenarios each, 2-6 s each) -> `run_extra.py` -> `mk_doc.py` -> `write_doc.py`. Scenario count reported: 64 per stop plus 3 sensitivities and 2x6 reference runs on the original engine, no selection among them. No UF_TRIALS / dead_lookup cell appended: this is a restatement of pieces already registered (SS-2, ER-1, NP-1, UF-ENTRY C9), not a new search.
