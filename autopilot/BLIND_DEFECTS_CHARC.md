# BLIND_DEFECTS_CHARC - independent check of the P7 gap (live +86,010 on 53 trades vs engine P6 +2,404 on 43), CHAR-C, 2026-11-06
Read-only on every sealed file; variant runs of the sealed harness only (code/find_c/bd_*.py; my process of blind_run.py with SLOTS=1 and the X cells zeroed reproduces the sealed P6 list exactly: 43 trades, +2,403.61, lots identical). Live file read after the seal (DECISIONS 2026-11-06T15:59Z). Mapping: live P7Strat = engine book P6 = engine tag PE = the PB3B_R5_P1 pullback entries (NOT the pb7 file, which feeds A6/A7). No PASS claim; research only.

## Answer in seven lines
1. Signal logic: the engine's own PB3B pullback machine (pb3_core2.events2(5,1,0,1) on the blind 1-min tape, same code path as blind_pe.py) produces a raw signal within +-150 s and in the same direction for **53 of 53** live P7 entries (52 within 120 s; the last, Tue 10:20:15 long, is a NY-session entry 135 s after its 10:18:00 signal = the 45-s NY confirmation delay). So the live P7 entries are the engine's signals; the gap is not a wrong signal definition.
2. But the engine does not trade all of them: the signal list that enters the engine (base_PE_blind, 80 rows in the week) is **thinned upstream** from the 260 raw events by the library generator's one-position-at-a-time rule applied to the NOMINAL 60-pt / 1R bracket trade (gen_core2: `if bar<=busy: continue`, busy = exit bar of the previous NOMINAL library trade). The live strategy and the engine's own exits (target / TH-L2 cut / policy cut) close positions earlier, and live re-enters on the next raw signal; the engine never sees it.
3. Classification of the 53 live P7 trades: **32 ENGINE-HAD-IT** (same minute, same side; lots equal in 30, differ in 2), **3 ENGINE-MISSED-IT with a signal row** (2 killed by the P0 signal-state SkipTop3 slot -> lots 0; 1 on Thu 10:39 passed lots/blocks and was not traded: engine lock / daily cap, inferred), **18 ENGINE-MISSED-IT because the raw signal is removed upstream** (17 sit inside a still-open nominal library trade of an earlier row; 1 is the last tape bar, Thu 11:04:30, dropped by `bar>=N-2`).
4. Classification of the engine's 43 P6 trades: **32 LIVE-HAD-IT, 11 LIVE-DID-NOT**: 5 while a live P7 position was open (the engine entered because its de-overlap uses nominal exits), 6 with live flat (Tue 03:07..08:29 five longs; Wed 07:43 and 08:05 shorts) after the live book had banked +16,700 / +9,060 on those label days (live book lock / +5R entry cap consistent; R definition not confirmed) - the engine, whose cuts keep its day smaller, kept trading.
5. P&L decomposition of the +83.6k gap (live 86,010 - engine 2,404): matched 32 trades: live +32,445 vs engine -1,221 = **+33.7k from exits** (3 trades live Target / engine TH-L2 cut: live +20,380 vs engine -11,025 = +31.4k; 17 both-cut: live -50,310 vs engine -55,290 = +5.0k; 12 both-target: -2.7k); live-only 21 trades **+53.6k** (18 upstream-thinned +39.2k, 3 with a signal row +14.4k); engine-only 11 trades +3.6k (subtracts from the gap).
6. Quantity: live qty equals the engine lots on 30 of 32 matched trades (4/7/2 ladder), qty 1/3/5 = the 70% initial leg when the 30% dip add is not filled (7->5, 4->3, 2->1), qty 10 = P0 old-panel lots; the lot ladder is not the explanation.
7. Ranking of explanations for the gap (my read; BASE-4 owns the ranking): (a) upstream nominal-bracket de-overlap removes 18 re-entries (+39.2k live) and mis-times 5 engine entries; (b) exit divergence on matched trades (+33.7k, 3 trades dominate: the engine's TH-L2 panel cut fires on trades that live took to the 60-pt target; engine 27 thl2_cut trades -79.2k vs live 25 cuts/locks -73.6k, engine 16 targets +81.6k vs live 28 targets +159.6k); (c) signal-state SkipTop3 slot in P0 (2 live trades +8.4k killed); (d) end-of-tape drop (+6.0k); (e) book lock / entry cap path dependence (+6.0k live Thu 10:39 not traded; 6 engine trades live did not take).

## 1. Every live P7 trade (53) against the engine
| # | live entry (ET) | side | qty | live exit | live net $ | class | engine P6 lots | engine exit | engine net $ | why |
|--|--|--|--|--|--|--|--|--|--|--|
| 1 | 2026-11-01 18:36:00 | L | 4 | P7_Target | +4805 | ENGINE-MISSED-IT (signal row existed) |  |  |  | lots 0 after the signal-state (P7 SkipTop3 4-slot) rule; session/ER/zone lots were 7/4/4 | row lots 0.0 l1/l2/l3 7.0/4.0/4.0 per 0 |
| 2 | 2026-11-01 19:11:03 | L | 10 | P7_Target | +12010 | ENGINE-MISSED-IT (raw signal removed upstream) |  |  |  | nominal 60pt/1R library trade of row 2026-11-01 19:05:00 (bracket side 1) still open until 2026-11-01 20:38:00 |
| 3 | 2026-11-01 20:45:00 | L | 4 | P7_Target | +4810 | ENGINE-MISSED-IT (raw signal removed upstream) |  |  |  | nominal 60pt/1R library trade of row 2026-11-01 20:39:00 (bracket side 1) still open until 2026-11-01 21:02:00 |
| 4 | 2026-11-01 23:03:00 | L | 2 | P7_ThL2Cut | -1405 | ENGINE-MISSED-IT (raw signal removed upstream) |  |  |  | nominal 60pt/1R library trade of row 2026-11-01 21:11:00 (bracket side 1) still open until 2026-11-02 00:44:00 |
| 5 | 2026-11-02 01:51:01 | S | 4 | P7_Target | +4800 | ENGINE-HAD-IT | 4 | target | +4843 |  |
| 6 | 2026-11-02 03:23:01 | S | 2 | P7_ThL2Cut | -2050 | ENGINE-HAD-IT | 2 | thl2_cut | -1248 |  |
| 7 | 2026-11-02 05:01:00 | S | 3 | P7_Target | +3605 | ENGINE-MISSED-IT (signal row existed) |  |  |  | lots 0 after the signal-state (P7 SkipTop3 4-slot) rule; session/ER/zone lots were 4/2/2 | row lots 0.0 l1/l2/l3 4.0/2.0/2.0 per 0 |
| 8 | 2026-11-02 07:51:01 | S | 2 | P7_PolicyCut | -1350 | ENGINE-HAD-IT | 2 | thl2_cut | -1591 |  |
| 9 | 2026-11-02 10:02:15 | S | 4 | P7_PolicyCut | -2865 | ENGINE-MISSED-IT (raw signal removed upstream) |  |  |  | nominal 60pt/1R library trade of row 2026-11-02 09:42:00 (bracket side -1) still open until 2026-11-02 10:14:00 |
| 10 | 2026-11-02 11:51:45 | S | 2 | P7_Target | +2400 | ENGINE-MISSED-IT (raw signal removed upstream) |  |  |  | nominal 60pt/1R library trade of row 2026-11-02 11:40:00 (bracket side -1) still open until 2026-11-02 12:28:00 |
| 11 | 2026-11-02 18:47:01 | S | 4 | P7_PolicyCut | -2405 | ENGINE-HAD-IT | 4 | thl2_cut | -2501 |  |
| 12 | 2026-11-02 20:42:01 | S | 4 | P7_ThL2Cut | -2495 | ENGINE-MISSED-IT (raw signal removed upstream) |  |  |  | nominal 60pt/1R library trade of row 2026-11-02 18:48:00 (bracket side -1) still open until 2026-11-02 23:05:00 |
| 13 | 2026-11-02 21:20:00 | S | 4 | P7_Target | +4795 | ENGINE-MISSED-IT (raw signal removed upstream) |  |  |  | nominal 60pt/1R library trade of row 2026-11-02 18:48:00 (bracket side -1) still open until 2026-11-02 23:05:00 |
| 14 | 2026-11-02 22:50:00 | S | 7 | P7_Target | +8400 | ENGINE-MISSED-IT (raw signal removed upstream) |  |  |  | nominal 60pt/1R library trade of row 2026-11-02 18:48:00 (bracket side -1) still open until 2026-11-02 23:05:00 |
| 15 | 2026-11-03 00:01:00 | S | 7 | P7_Target | +8405 | ENGINE-MISSED-IT (raw signal removed upstream) |  |  |  | nominal 60pt/1R library trade of row 2026-11-02 23:15:00 (bracket side -1) still open until 2026-11-03 00:33:00 |
| 16 | 2026-11-03 10:20:15 | L | 4 | P7_ThL2Cut | -2745 | ENGINE-MISSED-IT (raw signal removed upstream) |  |  |  | nominal 60pt/1R library trade of row 2026-11-03 10:19:00 (bracket side 1) still open until 2026-11-03 10:59:00 |
| 17 | 2026-11-03 10:46:30 | L | 4 | P7_Target | +3600 | ENGINE-MISSED-IT (raw signal removed upstream) |  |  |  | nominal 60pt/1R library trade of row 2026-11-03 10:19:00 (bracket side 1) still open until 2026-11-03 10:59:00 |
| 18 | 2026-11-03 11:57:00 | L | 3 | P7_Target | +3605 | ENGINE-MISSED-IT (raw signal removed upstream) |  |  |  | nominal 60pt/1R library trade of row 2026-11-03 11:54:00 (bracket side 1) still open until 2026-11-03 12:08:00 |
| 19 | 2026-11-03 18:13:03 | L | 7 | P7_PolicyCut | -6510 | ENGINE-MISSED-IT (raw signal removed upstream) |  |  |  | nominal 60pt/1R library trade of row 2026-11-03 18:04:00 (bracket side 1) still open until 2026-11-03 18:17:00 |
| 20 | 2026-11-03 18:56:01 | S | 4 | P7_PolicyCut | -1405 | ENGINE-HAD-IT | 4 | thl2_cut | -2894 |  |
| 21 | 2026-11-03 20:03:00 | S | 7 | P7_ThL2Cut | -4210 | ENGINE-HAD-IT | 7 | thl2_cut | -4537 |  |
| 22 | 2026-11-03 20:30:00 | S | 7 | P7_Target | +8390 | ENGINE-HAD-IT | 7 | target | +9081 |  |
| 23 | 2026-11-03 20:44:00 | S | 7 | P7_PolicyCut | -5215 | ENGINE-HAD-IT | 7 | thl2_cut | -4476 |  |
| 24 | 2026-11-03 21:34:00 | S | 7 | P7_Target | +8415 | ENGINE-HAD-IT | 7 | target | +8570 |  |
| 25 | 2026-11-03 21:56:00 | S | 4 | P7_Target | +4800 | ENGINE-HAD-IT | 4 | thl2_cut | -2515 |  |
| 26 | 2026-11-03 22:15:00 | S | 4 | P7_ThL2Cut | -2440 | ENGINE-HAD-IT | 4 | thl2_cut | -3287 |  |
| 27 | 2026-11-03 22:52:00 | S | 7 | P7_PolicyCut | -5035 | ENGINE-HAD-IT | 7 | thl2_cut | -4750 |  |
| 28 | 2026-11-03 23:07:00 | S | 4 | P7_PolicyCut | -2700 | ENGINE-HAD-IT | 4 | thl2_cut | -2643 |  |
| 29 | 2026-11-03 23:18:01 | S | 4 | P7_Target | +4795 | ENGINE-HAD-IT | 4 | target | +4926 |  |
| 30 | 2026-11-04 00:30:00 | L | 7 | P7_Target | +7190 | ENGINE-HAD-IT | 7 | target | +8608 |  |
| 31 | 2026-11-04 00:53:00 | L | 7 | P7_PolicyCut | -4030 | ENGINE-HAD-IT | 7 | thl2_cut | -4500 |  |
| 32 | 2026-11-04 01:31:01 | L | 7 | P7_Target | +8410 | ENGINE-MISSED-IT (raw signal removed upstream) |  |  |  | nominal 60pt/1R library trade of row 2026-11-04 00:54:00 (bracket side 1) still open until 2026-11-04 02:12:00 |
| 33 | 2026-11-04 02:45:00 | L | 4 | P7_Target | +4800 | ENGINE-HAD-IT | 4 | target | +4971 |  |
| 34 | 2026-11-04 03:36:00 | L | 4 | P7_PolicyCut | -4105 | ENGINE-HAD-IT | 4 | thl2_cut | -2473 |  |
| 35 | 2026-11-04 05:02:01 | L | 1 | P7_Target | +1200 | ENGINE-HAD-IT | 2 | target | +1673 |  |
| 36 | 2026-11-04 06:45:00 | L | 4 | P7_ThL2Cut | -3200 | ENGINE-HAD-IT | 4 | thl2_cut | -3007 |  |
| 37 | 2026-11-04 07:25:00 | S | 5 | P7_BookLock | -90 | ENGINE-HAD-IT | 7 | thl2_cut | -5137 |  |
| 38 | 2026-11-04 18:48:00 | S | 4 | P7_Target | +4800 | ENGINE-HAD-IT | 4 | target | +4994 |  |
| 39 | 2026-11-04 19:27:00 | S | 7 | P7_Target | +8390 | ENGINE-HAD-IT | 7 | thl2_cut | -4527 |  |
| 40 | 2026-11-04 21:11:00 | L | 4 | P7_Target | +4795 | ENGINE-HAD-IT | 4 | target | +4856 |  |
| 41 | 2026-11-04 21:31:00 | L | 4 | P7_ThL2Cut | -2655 | ENGINE-HAD-IT | 4 | thl2_cut | -2607 |  |
| 42 | 2026-11-04 21:42:02 | L | 4 | P7_PolicyCut | -2620 | ENGINE-MISSED-IT (raw signal removed upstream) |  |  |  | nominal 60pt/1R library trade of row 2026-11-04 21:32:00 (bracket side 1) still open until 2026-11-04 21:52:00 |
| 43 | 2026-11-05 00:14:00 | S | 7 | P7_Target | +8385 | ENGINE-HAD-IT | 7 | target | +8476 |  |
| 44 | 2026-11-05 01:34:00 | S | 4 | P7_ThL2Cut | -3640 | ENGINE-HAD-IT | 4 | thl2_cut | -2517 |  |
| 45 | 2026-11-05 02:02:00 | L | 2 | P7_Target | +2405 | ENGINE-HAD-IT | 2 | target | +1673 |  |
| 46 | 2026-11-05 02:53:04 | L | 7 | P7_Target | +7190 | ENGINE-HAD-IT | 7 | thl2_cut | -3983 |  |
| 47 | 2026-11-05 03:33:02 | L | 2 | P7_ThL2Cut | -1295 | ENGINE-HAD-IT | 2 | thl2_cut | -1259 |  |
| 48 | 2026-11-05 04:01:00 | L | 4 | P7_ThL2Cut | -2765 | ENGINE-MISSED-IT (raw signal removed upstream) |  |  |  | nominal 60pt/1R library trade of row 2026-11-05 03:34:00 (bracket side 1) still open until 2026-11-05 04:04:00 |
| 49 | 2026-11-05 05:13:00 | L | 2 | P7_Target | +2400 | ENGINE-HAD-IT | 2 | target | +2422 |  |
| 50 | 2026-11-05 07:58:00 | S | 7 | P7_PolicyCut | -4485 | ENGINE-HAD-IT | 7 | thl2_cut | -5861 |  |
| 51 | 2026-11-05 08:09:00 | S | 4 | P7_PolicyCut | -1875 | ENGINE-MISSED-IT (raw signal removed upstream) |  |  |  | nominal 60pt/1R library trade of row 2026-11-05 07:59:00 (bracket side -1) still open until 2026-11-05 08:46:00 |
| 52 | 2026-11-05 10:39:00 | S | 5 | P7_Target | +6000 | ENGINE-MISSED-IT (signal row existed) |  |  |  | row passed blocks and lots (7): not traded -> engine book lock / daily cap on the engine P6 label-day path (inferred, see text) | row lots 7.0 l1/l2/l3 7.0/7.0/7.0 per 2 |
| 53 | 2026-11-05 11:04:30 | S | 5 | P7_Target | +6000 | ENGINE-MISSED-IT (raw signal removed upstream) |  |  |  | previous row 2026-11-05 11:01:00 nominal exit 2026-11-05 11:01:00 (<= entry): other thinning (cooldown / same-bar / session) |
Reading of "why" for the 18 upstream rows: the quoted library trade is the earlier base_PE row whose NOMINAL 60 pt / 1R bracket trade (exit at target/stop at et_out) was still running at the time of the live entry; gen_core2 skips every later event until that nominal exit. The live trade that entered inside it had exited earlier (cut or target), so live was flat and re-entered.

## 2. Every engine P6 trade (43) against the live file
| # | engine P6 entry (ET) | side | lots | engine exit | engine net $ | class | live P7 (qty / exit / net $) | why not live |
|--|--|--|--|--|--|--|--|--|
| 1 | Mon 11-02 00:53:00 | L | 4 | thl2_cut | -2659 | LIVE-DID-NOT |  | live P7 position open (entered 2026-11-01 23:03:00, 2 lots) |
| 2 | Mon 11-02 01:51:01 | S | 4 | target | +4843 | LIVE-HAD-IT | 4 / P7_Target / +4800 |  |
| 3 | Mon 11-02 03:23:00 | S | 2 | thl2_cut | -1248 | LIVE-HAD-IT | 2 / P7_ThL2Cut / -2050 |  |
| 4 | Mon 11-02 07:51:01 | S | 2 | thl2_cut | -1591 | LIVE-HAD-IT | 2 / P7_PolicyCut / -1350 |  |
| 5 | Mon 11-02 18:47:01 | S | 4 | thl2_cut | -2501 | LIVE-HAD-IT | 4 / P7_PolicyCut / -2405 |  |
| 6 | Mon 11-02 23:14:00 | S | 7 | thl2_cut | -3819 | LIVE-DID-NOT |  | live P7 position open (entered 2026-11-02 22:50:00, 7 lots) |
| 7 | Tue 11-03 00:58:00 | S | 4 | thl2_cut | +7716 | LIVE-DID-NOT |  | live P7 position open (entered 2026-11-03 00:01:00, 7 lots) |
| 8 | Tue 11-03 03:07:00 | L | 4 | thl2_cut | -2207 | LIVE-DID-NOT |  | live flat: no live P7 entry; live P7 realised on this label day before then +16700 (live BookLock/daily cap inferred; R definition not confirmed) |
| 9 | Tue 11-03 04:38:00 | L | 4 | target | +4877 | LIVE-DID-NOT |  | live flat: no live P7 entry; live P7 realised on this label day before then +16700 (live BookLock/daily cap inferred; R definition not confirmed) |
| 10 | Tue 11-03 05:18:00 | L | 4 | thl2_cut | -2447 | LIVE-DID-NOT |  | live flat: no live P7 entry; live P7 realised on this label day before then +16700 (live BookLock/daily cap inferred; R definition not confirmed) |
| 11 | Tue 11-03 07:45:00 | L | 2 | target | +2449 | LIVE-DID-NOT |  | live flat: no live P7 entry; live P7 realised on this label day before then +16700 (live BookLock/daily cap inferred; R definition not confirmed) |
| 12 | Tue 11-03 08:29:00 | L | 4 | target | +3346 | LIVE-DID-NOT |  | live flat: no live P7 entry; live P7 realised on this label day before then +16700 (live BookLock/daily cap inferred; R definition not confirmed) |
| 13 | Tue 11-03 18:23:00 | L | 7 | thl2_cut | -4613 | LIVE-DID-NOT |  | live P7 position open (entered 2026-11-03 18:13:03, 7 lots) |
| 14 | Tue 11-03 18:56:01 | S | 4 | thl2_cut | -2894 | LIVE-HAD-IT | 4 / P7_PolicyCut / -1405 |  |
| 15 | Tue 11-03 20:03:00 | S | 7 | thl2_cut | -4537 | LIVE-HAD-IT | 7 / P7_ThL2Cut / -4210 |  |
| 16 | Tue 11-03 20:30:00 | S | 7 | target | +9081 | LIVE-HAD-IT | 7 / P7_Target / +8390 |  |
| 17 | Tue 11-03 20:44:00 | S | 7 | thl2_cut | -4476 | LIVE-HAD-IT | 7 / P7_PolicyCut / -5215 |  |
| 18 | Tue 11-03 21:34:00 | S | 7 | target | +8570 | LIVE-HAD-IT | 7 / P7_Target / +8415 |  |
| 19 | Tue 11-03 21:56:00 | S | 4 | thl2_cut | -2515 | LIVE-HAD-IT | 4 / P7_Target / +4800 |  |
| 20 | Tue 11-03 22:15:00 | S | 4 | thl2_cut | -3287 | LIVE-HAD-IT | 4 / P7_ThL2Cut / -2440 |  |
| 21 | Tue 11-03 22:52:00 | S | 7 | thl2_cut | -4750 | LIVE-HAD-IT | 7 / P7_PolicyCut / -5035 |  |
| 22 | Tue 11-03 23:07:00 | S | 4 | thl2_cut | -2643 | LIVE-HAD-IT | 4 / P7_PolicyCut / -2700 |  |
| 23 | Tue 11-03 23:18:01 | S | 4 | target | +4926 | LIVE-HAD-IT | 4 / P7_Target / +4795 |  |
| 24 | Wed 11-04 00:30:00 | L | 7 | target | +8608 | LIVE-HAD-IT | 7 / P7_Target / +7190 |  |
| 25 | Wed 11-04 00:53:00 | L | 7 | thl2_cut | -4500 | LIVE-HAD-IT | 7 / P7_PolicyCut / -4030 |  |
| 26 | Wed 11-04 02:45:00 | L | 4 | target | +4971 | LIVE-HAD-IT | 4 / P7_Target / +4800 |  |
| 27 | Wed 11-04 03:36:00 | L | 4 | thl2_cut | -2473 | LIVE-HAD-IT | 4 / P7_PolicyCut / -4105 |  |
| 28 | Wed 11-04 05:02:00 | L | 2 | target | +1673 | LIVE-HAD-IT | 1 / P7_Target / +1200 |  |
| 29 | Wed 11-04 06:45:00 | L | 4 | thl2_cut | -3007 | LIVE-HAD-IT | 4 / P7_ThL2Cut / -3200 |  |
| 30 | Wed 11-04 07:25:00 | S | 7 | thl2_cut | -5137 | LIVE-HAD-IT | 5 / P7_BookLock / -90 |  |
| 31 | Wed 11-04 07:43:00 | S | 7 | target | +5856 | LIVE-DID-NOT |  | live flat: no live P7 entry; live P7 realised on this label day before then +9060 (live BookLock/daily cap inferred; R definition not confirmed) |
| 32 | Wed 11-04 08:05:00 | S | 7 | thl2_cut | -4873 | LIVE-DID-NOT |  | live flat: no live P7 entry; live P7 realised on this label day before then +9060 (live BookLock/daily cap inferred; R definition not confirmed) |
| 33 | Wed 11-04 18:48:00 | S | 4 | target | +4994 | LIVE-HAD-IT | 4 / P7_Target / +4800 |  |
| 34 | Wed 11-04 19:27:00 | S | 7 | thl2_cut | -4527 | LIVE-HAD-IT | 7 / P7_Target / +8390 |  |
| 35 | Wed 11-04 21:11:00 | L | 4 | target | +4856 | LIVE-HAD-IT | 4 / P7_Target / +4795 |  |
| 36 | Wed 11-04 21:31:00 | L | 4 | thl2_cut | -2607 | LIVE-HAD-IT | 4 / P7_ThL2Cut / -2655 |  |
| 37 | Thu 11-05 00:14:00 | S | 7 | target | +8476 | LIVE-HAD-IT | 7 / P7_Target / +8385 |  |
| 38 | Thu 11-05 01:34:00 | S | 4 | thl2_cut | -2517 | LIVE-HAD-IT | 4 / P7_ThL2Cut / -3640 |  |
| 39 | Thu 11-05 02:02:00 | L | 2 | target | +1673 | LIVE-HAD-IT | 2 / P7_Target / +2405 |  |
| 40 | Thu 11-05 02:53:04 | L | 7 | thl2_cut | -3983 | LIVE-HAD-IT | 7 / P7_Target / +7190 |  |
| 41 | Thu 11-05 03:33:02 | L | 2 | thl2_cut | -1259 | LIVE-HAD-IT | 2 / P7_ThL2Cut / -1295 |  |
| 42 | Thu 11-05 05:13:00 | L | 2 | target | +2422 | LIVE-HAD-IT | 2 / P7_Target / +2400 |  |
| 43 | Thu 11-05 07:58:00 | S | 7 | thl2_cut | -5861 | LIVE-HAD-IT | 7 / P7_PolicyCut / -4485 |  |
## 3. P7 quantity per live trade vs the engine's lots
Rows are live qty; matched = trades present in both. Engine lots only take 2/4/7 (session table x ER ladder x zone half); live qty has 1/3/5/10 as well. Trade-level pairs: 30 of 32 matched equal; Wed 05:02 live 1 vs engine 2; Wed 07:25 live 5 vs engine 7 (live P7_BookLock exit 4 s after entry, -90 vs engine -5,137 thl2_cut). 5 = 70% of 7, 3 = 70% of 4, 1 = 70% of 2 (initial leg only); the unmatched live qty 10 (Sun 19:11) is a P0 old-panel lot size, the engine had no row.
| live qty | n live trades | engine lots on matched trades |
|--|--|--|
| 1 | 1 | 2x1 |
| 2 | 7 | 2x5 |
| 3 | 2 | - |
| 4 | 24 | 4x14 |
| 5 | 3 | 7x1 |
| 7 | 15 | 7x11 |
| 10 | 1 | - |
## Evidence and caveats
* Signal reconstruction: events from `pb3_core2.events2(5,1,0,1)` on the engine's own blind 1-min tape (te_tape_bar_blind.npz, bars from the NQ tables), run through the preamble of blind_pe.py; I did NOT rebuild the 1-min bars separately from the 1-s tables in the time available, so the tape-independence of the signal check rests on the engine tape. 260 raw events in the week vs 80 rows in base_PE_blind; 52/53 live entries within 120 s of a same-side raw event, 53/53 within 150 s.
* Engine side: blind_run.py unchanged (imported), SLOTS=1 (as in the sealed run), X cells zeroed in P0 (as blind_sens does); 43 trades +2,403.61, lots identical to the sealed list. Per-row lots stages (session/slot, ER, zone) from lots_ts2.live_lots(stages=True).
* Inferred, not tested by a variant run: the Thu 10:39 non-trade (engine lock/daily-cap path) and the live entry-cap explanation of the 6 live-flat engine trades (needs the lock R in dollars; lock_rules.py defines R = planned lots x stop x $20, so +5R is large at 4-7 lots; the live BookLock exit on Wed 07:25 proves a live lock is active but its parameters are not in the file).
* Not tested: a variant run of the engine with the unthinned raw events (gen_core2 without nominal `busy`) would quantify (a) directly; it needs base_PE and the d-table rebuilt (REDO chain), which I did not touch. Suggested first test for BASE-4: regenerate base_PE_blind rows with `busy` released after the ENGINE's own exit and compare with live.
* Anomalies in the sealed engine ledger for BASE-4 (net vs own prices): Tue 00:58 short 4 lots thl2_cut entry 28109.75 exit 28128.50 (a 18.75-pt loss) is booked +7,715.80; Tue 22:52 and Wed 00:53 7-lot thl2_cut rows net 900-1,000 worse than price x lots; three target rows (Tue 08:29 4 lots +3,346 vs 4,800; Wed 07:43 7 lots +5,856 vs 8,400; Wed 05:02 2 lots +1,673 vs 2,400) are about 70% of the nominal = 70% leg only (the 30% add not filled).
* Files: /mnt/l2/l2vast/find_c/blind/{bd_pe_slots1.pkl, bd_M.pkl, bd_classLive.pkl, bd_eng1.pkl}; code l2vast/ds3/code/find_c/{bd_run.py, bd_match.py, bd_ev.py, bd_class.py, bd_md.py}.
