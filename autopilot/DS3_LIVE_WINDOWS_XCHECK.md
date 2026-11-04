# DS3_LIVE_WINDOWS_XCHECK - independent cross-check of ZL-2's DIS-BJ (live no-new-entry windows on the Q1-A ts2 base) (DIS-BR), BASE-4, 2026-11-04T23:19Z

Research only, nothing live, no PASS, no engine edits. Scope note l2vast/ds3/prereg/DISBR_scope.md sha256 323db9b3bb2b814d359a713655aa105406cf66c7dceb1c7b67bb56be153d4474 (DECISIONS.md, logged before any number and before ZL-2's numbers were opened). Code l2vast/ds3/code/disbr/ (br_lib, br_run, br_run2, br_run3, br_an, br_an2, br_doc); data /mnt/l2/l2vast/ds3_base4/br_runs*.pkl, br_mine.json. My numbers (br_mine.json, written 23:15Z) preceded my reading of ZL-2's interim line (MORNING.md, DIS-BJ INTERIM); DS3_LIVE_WINDOWS_BASE.md had not landed, so the comparison is with that interim line. Two later runs (18:04 window, signal-second convention) were made AFTER seeing ZL-2's numbers, to isolate the cause of a difference; they are marked.

## Answer
**ZL-2's DIS-BJ numbers are reproduced.** Validation: blocking only 09:00-09:29 and 15:00-16:54 leaves the base at exactly $2520149.07 (there are 0 live library rows in either window). With the live windows my independent run (extra_skip on the entry minute) gives, for the window set ZL-2 uses (09:00-09:59 + 18:00-18:04 + 15:00-16:54) and the signal-second clock test, total $2462264 (ZL-2 $2,462k), mean 16545/wk with the carrying weeks dropped (16.5k), maxDD HOLD 91168 / PRE 64885 / L6M 59964 / X' 77536 / 2026 59964 (91k / 65k / 60k / 77.5k / 60k), worst day -37181 (-37.2k), worst week -59964 (-60.0k), Calmar 0.213 (0.21): every figure agrees to within 1%. The base itself: $2,520,149.07, mean 17.7k/wk (dropped weeks), HOLD maxDD $122025. The windows cost $57885 (-2.3%) in total and cut the HOLD maxDD from 122025 to 91168 (-25%), the worst week from -62576 to -59964, but raise the X' maxDD from 49417 to 77536: the 09:30-09:59 block costs about $138k (PE +98k, HM +29k, KB +17k, MV -12k marginal) and the 18:00-18:04 block ADDS about $73k (Asia entries removed: PE -60k, KB -12k).
**The one disagreement > 2% is a definition, not an error:** which clock the window test uses for PE. With the entry (fill) second as the clock (PE: the 45-second confirmation fill; lots_ts2.entry_ts) my W3 gives total $2461177, X' maxDD $65680 (-15% vs ZL-2) and worst day $-38106; with the SIGNAL second (PE: the trigger, before the 45-s confirmation) every ZL-2 number is reproduced (table below). 1,831 of 74,914 library rows have a signal minute different from the entry minute (PE confirmations). Which one D7 uses is UNVERIFIED (no D7 source on the box): a no-new-entry window tested at signal time blocks the confirmation from starting; tested at fill time it blocks PE signals fired just before the window whose fill lands inside it.

## 1. Is "the engine blocks 09:00-09:29 only" exactly true? No (checked in the lot tables and the entry-minute distribution)
* The live11 lot table (lots_ts2.session_lots = book lots x session factor) has a ZERO factor for the library session label **pre** for ALL books and for **close** for all books. The label **pre** covers entry minutes 08:30-09:29 (5,057 rows, min 510 / max 569): the engine therefore blocks **08:30-09:29**, not only 09:00-09:29. There are 0 live (lots > 0) rows with entry in 08:30-09:29. **close** covers 15:00-15:14; the label **nypm** has rows to 16:17 but its live rows end at 14:57 (KB nypm; other books have 0 nypm lots), so 15:00-16:54 has 0 live rows (570 non-live rows). The library has entries at every other clock minute.
* NOT blocked in the base: **09:30-09:59** (2,178 live library rows: HM 401, KB 643, MV 586, PE 548, all nyam) and **18:00-18:05** (824 live rows: HM asia 187, KB asia 402, PB asia 39, PE asia 196; 18:00-18:04: 775 rows). Library rows are before the one-position rule; the engine takes 21,397 trades in the base, 19,096 with the 18:04 variant of the live windows (signal-second convention 19,025).
* **"O7 exempt"** means nothing for this base: the base has the six books K6/P6/U6/H6/M6/A6 (= KB, PE, SM, HM, MV, PB) and no O7 rows (O7, the NY-AM pullback, is a Shadow line outside the six books), so all six are "non-exempt" and the block applies to all of them. If O7 were traded live, its NY-AM entries would be exempt from the 09:00-09:59 block and add to the stack on top of these numbers.

## 2. My results (TH on, live lots, ts2 base; $; weekly means with the carrying weeks dropped except mean/wk(all); maxDD weekly-cumulative in the harness windows)
| variant | total | mean/wk (all 187 wks) | mean/wk (dropped) | maxDD HOLD | PRE | L6M | X' | 2026 | worst day / week | Calmar (ALL, dropped) |
|--|--|--|--|--|--|--|--|--|--|--|
| base | 2520149 | 13477 | 17716 | 122025 | 75057 | 62576 | 49417 | 62576 | -38106 / -62576 | 0.236 |
| V0: 09:00-09:29 + 15:00-16:54 only | 2520149 | 13477 | 17716 | 122025 | 75057 | 62576 | 49417 | 62576 | -38106 / -62576 | 0.236 |
| V1 as specified: + 09:30-09:59 + 18:00-18:05 (entry second) | 2455260 | 13130 | 16550 | 89839 | 69248 | 59964 | 66676 | 59964 | -38106 / -59964 | 0.239 |
| V1a: 09:30-09:59 only (entry second) | 2389039 | 12776 | 16849 | 110577 | 72275 | 61244 | 64999 | 61244 | -38106 / -61244 | 0.209 |
| V1b: 18:00-18:05 only (entry second) | 2587767 | 13838 | 17406 | 101966 | 79535 | 61295 | 36206 | 61295 | -38106 / -61295 | 0.219 |
| [after seeing ZL-2] 18:00-18:04 only (entry second) | 2593086 | 13867 | 17535 | 103295 | 75845 | 61295 | 37907 | 61295 | -38106 / -61295 | 0.231 |
| [after] W3 = 09:00-09:59 + 18:00-18:04 (entry second) | 2461177 | 13161 | 16683 | 91168 | 65558 | 59964 | 65680 | 59964 | -38106 / -59964 | 0.230 |
| [after] 09:30-09:59 only (SIGNAL second) | 2381884 | 12737 | 16656 | 110577 | 71864 | 61244 | 78745 | 61244 | -37817 / -61244 | 0.212 |
| [after] W3 (SIGNAL second) = ZL-2's window set and clock | 2462264 | 13167 | 16545 | 91168 | 64885 | 59964 | 77536 | 59964 | -37181 / -59964 | 0.213 |
(V0 and base are identical to the cent.)

## 3. Removed-entry effect by book / session / year (marginal: base minus variant, engine cube, locks re-run; positive = the base earned that much more)
* **09:30-09:59 (entry second)** - by book: K6 +16769, P6 +97985, H6 +28645, M6 -12290; by session: nyam +132804, nypm -1693; by year: 2023 +35217, 2024 +32253, 2025 +92374, 2026 -28734.
* **18:00-18:04 (entry second)** - by book: K6 -12302, P6 -60053, H6 +2418, A6 -3001; by session: asia -91840, london +27012, nyam -11059, nypm +2950; by year: 2023 -31872, 2024 -30482, 2025 +7916, 2026 -18500.
* **both windows, 18:00-18:04 (entry second)** - by book: K6 -7567, P6 +50923, H6 +30908, M6 -12290, A6 -3001; by session: asia -91840, london +27012, nyam +133823, nypm -10023; by year: 2023 +1572, 2024 +3628, 2025 +108331, 2026 -54559.
Book tags: K6 = KB, P6 = PE, U6 = SM (no entries in these windows), H6 = HM, M6 = MV, A6 = PB. Removed live library rows by year (V1): {'2023': 392, '2024': 621, '2025': 910, '2026': 1079} (total 3002 rows, 6148 lots). ZL-2's "removed trades" (standalone P&L of the trades taken in the base: 09:30-09:59 1,791 trades +$144k, 18:00-18:04 895 trades -$81k; PE +119k / HM +28k / KB +15k / MV -18k) is a different measure from my marginal (system effect with replacements and locks): +$138k and -$73k in total, signs and sizes consistent; by book PE (+119k vs +98k) and MV (-18k vs -12k) differ because of the clock convention and the marginal effect.

## 4. Comparison with ZL-2 (MORNING.md DIS-BJ INTERIM; DS3_LIVE_WINDOWS_BASE.md not yet landed)
| quantity | ZL-2 | mine (same windows and clock) | difference |
|--|--|--|--|
| W1 total (18:00-18:04) | $2,593,000 | $2,593,086 | 0.00% |
| W2 total (09:30-09:59, signal second) | $2,382,000 | $2,381,884 | -0.00% |
| W3 total | $2,462,000 | $2,462,264 | 0.01% |
| W3 mean/wk (dropped weeks) | 16,500 | 16,544 | 0.27% |
| W3 HOLD maxDD | 91,000 | 91,167 | 0.18% |
| W3 PRE maxDD | 65,000 | 64,884 | -0.18% |
| W3 L6M maxDD | 60,000 | 59,963 | -0.06% |
| W3 X' maxDD | 77,500 | 77,536 | 0.05% |
| W3 2026 maxDD | 60,000 | 59,963 | -0.06% |
| W3 worst day | -37,200 | -37,181 | -0.05% |
| W3 worst week | -60,000 | -59,963 | -0.06% |
| W3 Calmar | 0.21 | 0.21 | 1.61% |
| W1 HOLD maxDD | 103,000 | 103,295 | 0.29% |
| W2 X' maxDD | 79,000 | 78,744 | -0.32% |
| base X' maxDD ('was') | 49,000 | 49,417 | 0.85% |
| base HOLD maxDD | 122,000 | 122,024 | 0.02% |
All within 2% when the clock is the signal second (the 1% on mean/wk is ZL-2 rounding 16,545 to 16.5k). **With the entry-second clock** the same comparison differs by more than 2% in: X' maxDD (W3 65680 vs 77,500, -15%; W2 64999 vs 79,000), worst day (-38106 vs -37,200, 2.4%), PRE maxDD (65558 vs 65,000), and the delta of W2 (-131110 vs -138k, -5%); totals still agree within 0.3%.

## 5. Consequences and open items (not decisions)
* The pre-existing statement "engine blocks 09:00-09:29 only" should read "the lot tables give zero lots to every entry from 08:30 to 09:29 (library session pre) and from 15:00 on; nothing is blocked at 09:30-09:59 or 18:00-18:05 today".
* X' (2023-04..2024-01) is very sensitive to the clock convention (65.7k vs 77.5k) because a few PE confirmation fills near the window edges move 2023 P&L; HOLD / PRE / L6M / 2026 are not (<= 1.2%).
* Open for the D7 owner / user: (a) is the window tested at the signal or at the order/fill time for P7 (45-s confirmation); (b) is 18:00-18:04 or 18:00-18:05 the Asia block (the one extra minute changes the total by $5k); (c) the 09:00-09:59 block itself is disputed in the sources (ZL-2's EVIDENCE CONFLICT in MORNING.md); the 09:30-09:59 part is what costs about $138k over the history (2025 +$92k of it).
* Limits: one engine, one seed of locks (no lock-phase averaging); marginal effects include replacement trades; the base is the Q1-A ts2 reference; no PA9 here.
