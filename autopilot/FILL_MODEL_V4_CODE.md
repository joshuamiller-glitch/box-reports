# FILL_MODEL_V4_CODE - PRE-PROOF (Z1, 2026-11-07). Post-hoc. No PASS claim. Supersedes FILL_MODEL_V3 where they differ; V3 files untouched.
Source read: data/live_code/DS7.cs (sha256 54697597a7057cfd2003f3d698b62fe01358c308a87adfbbfb5a764ab0cb63a7) + GATE0_ANSWERS_1106.md s3. Code: l2vast/ds3/code/fillv4/ (fillsim.py sha256 0c8b1ed284f3194d66e3d039bf3ef80977245790d5fabddd3c04fe7ef8cdb024, test_fillsim.py 10 tests pass, tieout4.py, data.py). Log: /mnt/l2/l2vast/ds3_blind_z1/fillv4/tieout4.txt. Private trees only; fillv3/ and code/blind/ md5 manifests identical before/after; nothing written to sealed/published trees.
## 1. Live file
fillv3/data.py and blind_z1/live_cf_x.py already read code/blind/live_frozen.frozen_path() (V3 note 2026-11-06); re-verified: sha256 424c68da934136df7124004b4b1fd9a34952a1e5e3e6ba1017ad0d972a927112, 187 rows, pnlNet 104,095.00, asserted on every load. fillv4/data.py is the same reader. TIE-OUT CONFIRMED on the frozen file (numbers in 5).
## 2. What the CODE says (differs from V3 and, in two places, from the answers text)
| item | V4 rule (code line) | status |
|---|---|---|
| Slicing | 1 market lot per 2000 ms (PumpEntry 2739); dt=2, latency 1 s | CALIBRATED (V3) |
| Split | first = Math.Round(lots*70/100) banker's, rem = lots-first, ONLY K7,P7,U7,H7,M7 (L2GateBooks 441; 1474). 5 lots = 4+1 (V3 had 3+2). A7/O7/X books: no split | CODE |
| The 30% add | NOT a resting limit. Armed at the signal; ONE MARKET order for all rem lots (L2AddStage 1531) at the first print with dip >= 3 pt measured from the SIGNAL price (ArmPx), plus >= 1 L2 confirmation, evaluated at most 1/s once dip>=3 (1492-1522). Disarmed by: print through the original stop level, exit pending/target/stop filled, session lots 0, time block, opposite signal. No timeout (V3's 900 s timeout and 'fill at the dip level' were wrong) | CODE; confirmation UNCAL |
| Stop LEVEL | gate books: signal price -/+ 60 (ArmStopPx 1478, used by PlaceBracket 2791), NOT the fill average and not moved by the add. Others (A7, X): fill average -/+ 60; O7 40 | CODE |
| Target | fill AVERAGE +/- 60 (O7 90), re-based on every fill incl. the add (PlaceBracket 2795/2815). V3 fill-at-level logic kept (85/86 live, price err 0.004) | CALIBRATED |
| Strategy stop, K7 and H7 | JoinThenMarket: first print at/through the level -> limit at our touch (long sells the ask) for 3 s from that print -> cancel -> RequestBookExit -> 400 ms -> one market (PumpStopExit 2863). Modeled: join fills if a print trades at/through the joined price in [trigger+1 s, trigger+3 s]; else market at trigger+3+1.0 (cancel, UNCAL)+0.4+1.0 s, opposite touch +1.0 pt | structure CODE; all timing/fill params UNCALIBRATED |
| Strategy stop, P7/U7/M7/A7/O7 | market at touch: trigger print +1 s, opposite touch + 1.0 pt, never better than the level | UNCALIBRATED (the 1.0 pt / 1 s are V3's fit to two fills that were catastrophe-level) |
| Catastrophe | native stop-market 20 pt beyond the stop, live throughout the join window (modeled on all sliced books, per answers s3; O7 none) | UNCAL (see 3) |
| Cuts | unchanged V3 (99 live: 0.57 pt beyond the opposite touch, sd 1.94) | CALIBRATED |
## 3. Discrepancies to put to the user (not resolved by me)
(a) **The two live "_Stop" exits (M7 -80.75, K7 -83.00, 11-03 short) are NOT strategy-worked 60-pt exits.** Their names are the native `_Stop`, fills 20+ pt past the 60 level. With the code level (signal price -60, last print before the entry second as signal proxy) the 60 level had printed 87 s (M7) and 531 s (K7) before the live exit, and nothing else in the 187 trades touched a 60 level before its live exit (cuts at 30 act first). So in both cases the 60-level exit did not fire (K7 JoinThenMarket would have posted a `_StopJoin`; M7 Native would have stopped at 60). V4 on those trades exits 80-86 s / 526-531 s earlier than live at about -64 pt instead of -81/-83. Possible causes not checkable from the file: a different live stop distance in that session (K7/H7 per-session bracket strings exist, 2681), PumpStopExit not running (State/BracketPlaced), or those books' mode differing from the answers. There is therefore NO live observation of a 60-pt strategy-stop fill, join or market; every stop parameter in 2 is a code reading.
(b) In the code, Native = native stop-market AT the stop level and no strategy-worked exit and no catastrophe (NativeStopPx 2777 adds the 20 only in JoinThenMarket). Behaviourally equal to 'market at touch'; the answers' '+20 catastrophe on Native books' is not in the code. Immaterial unless gapped.
(c) DS7.cs defaults (485-486) set JoinThenMarket for ST and HM; P7/U7/A7/M7 (u5,p5,pb,... via StStopExitMode) inherit the ST mode in code, so 'Native' for them is a live setting not in the file.
## 4. Tie-out against the 187 frozen live trades (live entry/cut inputs as in V3)
| item | V3 | V4 |
|---|---|---|
| entry err all (live-model, +=live worse) | +0.23 sd 2.0 MAE 1.45 | confirm=none (every dip fills) +0.28 sd 1.88 MAE 1.29; confirm=proxy (microprice or delta-turn) +0.43 sd 1.87 MAE 1.34; no split -0.28 sd 2.15 MAE 1.58 |
| gate books, lots>=2 (n 75) | - | none +0.08 MAE 1.20; proxy +0.44 MAE 1.33; no split -1.32 MAE 1.93 |
| 1 lot | +0.48 | +0.50 |
| targets (85) | price 0.004, 92% within 2 s | price 0.004, 92% within 2 s, median +0.54 s |
| cuts (99) | sd 1.94 MAE 1.35 | identical |
| exit type | 85/86 target, 95/99 cut | target 85/86, cut 95/99, stops: 0/2 agree on time (a), same 4 target-flips as V3 |
| model pts$ (no fees) | 106,727 | 109,063 proxy / 107,823 none vs live pts$ 105,243 / pnlNet 104,095 |
Add model: 92 adds fire in both variants (live qty = filled lots, so unfilled adds are invisible: live is conditioned on fill, which favors 'none'). Proxy covers only 2 of 8 confirmations (microprice, delta-turn; imb-flip, absorption, iceberg, pulled, sweep, large-print not reconstructable) so real fill rate lies between none and proxy. Default is proxy; unfilled add = dropped. Entry error is in-sample, one week, sd ~1.9 pt per entry.
## 5. Uncalibrated list (no live observation)
join fill rule and its 3 s window, join_cancel_s 1.0, exit_gap 0.4 (code) + latency, stop_extra 1.0, stop_latency 1.0, cat fills, add confirmation, signal price = last print before the entry second (the csv has no signal price; matters for the stop level and the dip origin by up to a few points), O7 time exit (16:00 modeled as a cut-type market, not observed), lot count of adds when the add never filled (qty ambiguity).
## 6. Not done / next
Per-slice running-average target during slicing (touch inside the first 2-6 s ignored); partial join fills; H7 5-min bucket signals and day caps are engine items, not fill model. A forward check needs th_eval.csv/v1.5 logs of `_StopJoin` / `_StopJoinFallback`.
