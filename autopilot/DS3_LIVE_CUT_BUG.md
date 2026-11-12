# DS3_LIVE_CUT_BUG - literal-port harness for the live cut, v1.4-literal line, per-book lines (W-R, 2026-11-12 ~19:50Z)
Order: autopilot/DIRECTIVE_LIVE_CUT_BUG_20261112.md (user 19:15Z). Companion to DS3_P7_CUT_FIDELITY.md. Shadow only, no PASS claim. Chart clock = Eastern UTC-5 (user confirmed; fits the stop-touch times found in the fidelity page).

## 0. STATUS
- **BLOCKER (item 1 proper): the v1.9a source is not on the box.** ~/DS7.cs is the v1.4 file of Nov 7 00:22 (433,192 bytes): `grep -c "StateTick\|StatePulled\|ManagePolicyState\|StateOnPrint"` = 0. The literal v1.9a port (StateTick, StateStore, StateCancelSide, StatePulled, StateOnPrint, DepthLive, loss loop of ManagePolicyState) and the line where it diverges from the engine therefore CANNOT be named yet. The harness it plugs into is built and verified (below); `PortV19A` in code/th_p7fid/arrival.py is the stub. A nohup watcher (pid in /mnt/l2/l2vast/_p7fid/watch.log; code/th_p7fid/watch_ds7.sh) polls ~/DS7.cs every 10 min (mtime after 2026-11-12 00:00Z or size != 433192) and appends a MORNING line when it changes.
- **M7 events (11:30:45Z at -40, 12:21:31Z at -53.6) need NQ mbp-10 for 08:00-14:00Z.** The first buy attempt was refused by the licence window (CME historical data lags live by about 8 h: "end before 11:13Z" at 19:13Z); the lead's retry loop (code/th_survivors/retry_buy_c.sh, every 30 min) lands it from about 22:00Z. The same watcher then runs code/th_p7fid/m7_events.py (both-side v1.4-literal series around each cut second; entry price and side of the two live M7 trades are not on the box, so both sides are printed) and appends a MORNING line.
- What is done now: (a) arrival-order harness, (c) v1.4-literal series for the three P7 trades, (d) per-book line table. All v1.4-literal numbers are labelled NOT the v1.9a code.

## 1. (a) Arrival-order MBP-10 harness (code/th_p7fid/arrival.py)
- Input: raw CME mbp-10 records of one instrument (NQZ6) in arrival order.
- Every non-trade record is converted into the operations NT8 delivers to OnMarketDepth: the 10-level side book before/after is diffed into Remove / Add / Update at a POSITION; each op is applied with the literal array code of DS7.cs v1.4 OnMarketDepth (20-slot depBidPx/Sz, depAskPx/Sz, depBidN/AskN; Remove shifts up, Add shifts down, Update overwrites and raises N). depLast = event time.
- Every T record is an OnMarketData Last print (book unchanged); the port callbacks are on_depth(ts,side,op,pos,px,sz,H) and on_print(ts,px,sz,H) with H = the arrays.
- Verification: after every record the harness array equals the record's side book: 0 mismatches over 1.14 M records / 1.96 M depth operations (trade 1: 282,969 records, 477,920 ops; trade 2: 563,452 / 984,118; trade 3: 296,564 / 502,479).
- Stated limits: mbp-10 shows 10 levels (NT8 positions 0-19; levels 10-19 absent), op types are inferred from book diffs not from NT8's own event granularity, no L1 Bid/Ask events (lastBid/lastAsk = book top at the print), clock = ts_recv.
- The v1.9a port drops in as a Port subclass; nothing else changes.

## 2. (c) v1.4-LITERAL line (NOT the v1.9a code) for the three P7 trades
Code: code/th_p7fid/v14port.py = DS7.cs v1.4 L2OnPrint, L2OnDepthSnapshot (MedLevel EWMA 0.001 of top-5 mean), L2ThSnapshot (per-print pulled log, trades netted per price), PulledSupport (5 s), DepthLive (<120 s, >=5 levels each side), ManageThL2 loss loop (one evaluation per >= 1.0 s elapsed, AdvExtTime on strictly worse price, newMae = within 5 s). Evaluated on print price. Two rules run on it: the v1.4 live line (arm 30 pts, 30x, newMae) and the v1.5+ line values on the same definitions (arm 40 pts, 5x, newMae, 3 consecutive evaluations).

| trade (UTC) | evals with u<=-40 | with mult>=5 | + newMae | v1.4 line first fire (30 pts, 30x) | 40/5x/p3 on v1.4 definitions first fire | engine (state base) decision | per-print replica |
|---|---|---|---|---|---|---|---|
| 1 SHORT 00:11Z | 27 | 27 | 18 | 00:16:32.0 at -32.1 | 00:16:37.96 at -46.6 | 00:16:37 | 00:16:40 |
| 2 SHORT 00:58Z | 41 | 40 | 27 | 01:26:15.8 at -39.2 | 01:27:30.10 at -41.7 | 01:27:29 | 01:27:29 |
| 3 LONG 02:31Z | 29 | 25 | 15 | 02:43:16.4 at -34.5 | 02:43:23.61 at -44.8 | 02:43:24 | 02:43:24 |
Readings:
1. **The v1.4 code path fires too, and earlier.** Even the OLD v1.4 live line (30 pts, 30x) would have cut all three at -32, -39 and -35 pts (6-60 s before the new line's fire). So the silence is not specific to the v1.5+ state cut or to its thresholds; with correct inputs the v1.4 and the v1.5+ lines all fire on these three trades. What the live code saw as pulled / MedLevel / unreal, or whether the loop ran at all, differs.
2. **Definitions spread about 1.5-1.7x between the three computations, all far above threshold.** v1.4-literal mult vs engine state-base ratio5 at the same second: median 1.72x, 1.47x, 1.59x (engine 15.3, 12.2, 11.1 median; v1.4-literal 26.1, 19.3, 20.9). The v1.4 literal counts per print snapshot, the state base per second; both are >= 5 almost everywhere below -40.
3. MedLevel (v1.4 EWMA at the end of each window): 1.97, 2.21, 2.04 contracts.
4. Mark: the arrival-order array logic is not the cause of any difference (0 mismatches), so a live difference cannot come from array maintenance as written in v1.4.

#### Trade 1 SHORT 19:11 CT (00:11Z) - v1.4-literal (arrival-order harness) next to the engine state base and the per-print replica

| UTC | unreal | v1.4-lit pulled5 | v1.4-lit MedLevel | v1.4-lit mult | engine ratio5 | replica mult | secs since adv ext | arm40+5x+newMae | run (evals) |
|---|---|---|---|---|---|---|---|---|---|
| 00:16:35.243 | -40.8 | 113 | 2.04 | 55.4 | 32.2 | 57.6 | 1 | yes | 1 |
| 00:16:37.957 | -46.6 | 98 | 2.03 | 48.3 | 18.0 | 40.2 | 0 | yes | 3 |
| 00:16:43.098 | -42.6 | 42 | 2.02 | 20.8 | 9.8 | 20.7 | 5 | no | 0 |
| 00:16:48.840 | -42.3 | 31 | 2.02 | 15.4 | 10.9 | 15.8 | 11 | no | 0 |
| 00:16:52.987 | -43.3 | 45 | 2.01 | 22.4 | 10.9 | 23.3 | 15 | no | 0 |
| 00:16:56.023 | -43.8 | 73 | 2.00 | 36.4 | 23.5 | 37.3 | 18 | no | 0 |
| 00:17:00.302 | -50.6 | 59 | 2.00 | 29.5 | 19.7 | 30.9 | 1 | yes | 1 |
| 00:17:02.488 | -54.8 | 96 | 2.00 | 48.1 | 13.7 | 48.4 | 0 | yes | 3 |
| 00:17:06.320 | -54.3 | 52 | 1.99 | 26.1 | 14.8 | 26.0 | 4 | yes | 6 |
| 00:17:10.749 | -55.3 | 28 | 1.99 | 14.1 | 12.6 | 14.0 | 3 | yes | 9 |
| 00:17:14.252 | -58.8 | 21 | 1.98 | 10.6 | 15.9 | 10.6 | 0 | yes | 11 |

#### Trade 2 SHORT 19:58 CT (00:58Z) - v1.4-literal (arrival-order harness) next to the engine state base and the per-print replica

| UTC | unreal | v1.4-lit pulled5 | v1.4-lit MedLevel | v1.4-lit mult | engine ratio5 | replica mult | secs since adv ext | arm40+5x+newMae | run (evals) |
|---|---|---|---|---|---|---|---|---|---|
| 01:26:18.282 | -41.0 | 78 | 1.99 | 39.3 | 25.2 | 39.8 | 1 | yes | 1 |
| 01:27:04.439 | -40.5 | 9 | 1.98 | 4.5 | 9.6 | 4.5 | 46 | no | 0 |
| 01:27:21.606 | -41.0 | 25 | 1.99 | 12.6 | 12.2 | 13.1 | 63 | no | 0 |
| 01:27:27.134 | -41.7 | 22 | 1.99 | 11.1 | 9.6 | 11.1 | 0 | yes | 1 |
| 01:27:30.096 | -41.7 | 32 | 1.99 | 16.1 | 13.3 | 16.1 | 2 | yes | 3 |
| 01:27:34.496 | -44.5 | 33 | 1.99 | 16.6 | 10.1 | 18.1 | 1 | yes | 6 |
| 01:27:38.884 | -46.0 | 30 | 2.01 | 15.0 | 12.2 | 15.5 | 2 | yes | 8 |
| 01:27:43.692 | -45.7 | 37 | 2.07 | 17.9 | 16.3 | 17.9 | 4 | yes | 11 |
| 01:27:47.823 | -44.7 | 54 | 2.25 | 24.0 | 10.4 | 23.1 | 2 | yes | 2 |
| 01:27:48.848 | -42.0 | 64 | 2.25 | 28.5 | 10.4 | 26.7 | 3 | yes | 3 |
| 01:27:52.270 | -41.7 | 69 | 2.25 | 30.7 | 4.7 | 31.2 | 6 | no | 0 |
| 01:27:58.375 | -41.5 | 29 | 2.24 | 12.9 | 11.5 | 13.0 | 12 | no | 0 |
| 01:28:03.297 | -44.5 | 24 | 2.24 | 10.7 | 7.3 | 10.7 | 17 | no | 0 |
| 01:28:07.634 | -43.2 | 49 | 2.23 | 22.0 | 20.3 | 22.0 | 22 | no | 0 |
| 01:28:11.066 | -47.5 | 47 | 2.23 | 21.1 | 11.5 | 21.6 | 25 | no | 0 |
| 01:28:15.504 | -49.2 | 56 | 2.23 | 25.1 | 7.3 | 27.0 | 3 | yes | 3 |
| 01:28:19.144 | -50.7 | 43 | 2.23 | 19.3 | 12.0 | 19.3 | 2 | yes | 5 |
| 01:28:23.311 | -58.5 | 98 | 2.25 | 43.5 | 10.4 | 44.5 | 1 | yes | 8 |

#### Trade 3 LONG 21:31 CT (02:31Z) - v1.4-literal (arrival-order harness) next to the engine state base and the per-print replica

| UTC | unreal | v1.4-lit pulled5 | v1.4-lit MedLevel | v1.4-lit mult | engine ratio5 | replica mult | secs since adv ext | arm40+5x+newMae | run (evals) |
|---|---|---|---|---|---|---|---|---|---|
| 02:43:20.725 | -40.2 | 98 | 2.01 | 48.7 | 20.0 | 59.7 | 1 | yes | 1 |
| 02:43:23.610 | -44.8 | 86 | 2.00 | 42.9 | 16.5 | 53.0 | 1 | yes | 3 |
| 02:43:35.424 | -40.8 | 57 | 1.99 | 28.6 | 18.0 | 29.9 | 12 | no | 0 |
| 02:44:07.448 | -41.0 | 5 | 1.99 | 2.5 | 7.0 | 2.5 | 44 | no | 0 |
| 02:44:22.105 | -41.2 | 10 | 1.99 | 5.0 | 9.1 | 5.0 | 59 | no | 0 |
| 02:44:28.938 | -40.5 | 14 | 2.01 | 7.0 | 6.0 | 6.9 | 66 | no | 0 |
| 02:44:36.152 | -40.2 | 4 | 2.02 | 2.0 | 8.0 | 2.0 | 73 | no | 0 |
| 02:44:41.856 | -40.5 | 4 | 2.02 | 2.0 | 4.0 | 3.4 | 79 | no | 0 |
| 02:45:09.130 | -41.0 | 38 | 2.06 | 18.5 | 11.6 | 21.8 | 106 | no | 0 |
| 02:45:13.301 | -47.5 | 48 | 2.07 | 23.2 | 11.1 | 20.6 | 0 | yes | 1 |
| 02:45:16.376 | -49.2 | 50 | 2.07 | 24.2 | 9.6 | 24.1 | 3 | yes | 3 |
| 02:45:20.165 | -52.8 | 43 | 2.06 | 20.9 | 14.6 | 20.8 | 1 | yes | 6 |

## 3. Where could the live difference sit? (what the v1.4 text makes checkable now)
Checks that need only the NT8 Output log of 2026-11-11 (chart 19:11-19:18, 19:58-20:29, 21:31-21:46), no source:
- **Shadow mode:** v1.4 ManageThL2 with ThL2Mode = Shadow prints `<time> P7 SHADOW TH-L2 CUT at <u> pts: <n> contracts of support cancelled ...` and does NOT exit (L1606-1607: `if (shadow) { ... return; }`). If v1.9a's P7 state cut is in a Shadow-like mode the Output log shows the cut line at the engine times (00:16:37Z = 19:16:37, 01:27:29Z = 20:27:29, 02:43:24Z = 21:43:24 chart) and no exit. Grep for "SHADOW", "TH-L2 CUT", "StateCut", "POLICY CUT" at those times.
- **DepthLive false:** v1.4 prints once `D6 POLICY: no Level 2 depth events on <instrument> - rules using imb5/imb10/wall_* are skipped` when DepthLive is false (no depth event for 120 s or < 5 levels a side) and the whole L2 loop returns silently. Grep for that line on 11-11.
- **ExitPending / Bip / NoBracket gate** (L1574): returns before any evaluation; ExitPending is set while a StopJoin rests (3 s) or a previous exit is pending - not during the -40..-60 walk.
- **Eval throttle:** v1.4 uses `(now - ThL2LastEval).TotalSeconds < 1` on `now` = Globals.Now in realtime: one evaluation per >= 1 s of wall-clock; harmless here (evaluations at 1.0-2.0 s spacing still fire).
- th_eval.csv of 11-11 (v1.5+ per-evaluation log) answers it directly: unreal, pulled, MedLevel, newMae, DepthLive, decision per evaluation.

## 4. Item 4: per-book lines - v1.4 source / policy vs what the engine assumes (ready to check against v1.9a)
Sources: ~/DS7.cs v1.4 (L443-444 defaults, L485-486, L553-583 stop modes, L1572-1610 ManageThL2, L2173 ManagePolicy), GATE0_ANSWERS_1106.md s1/s3/s6 (policy file in force), engine: SB.specs()['S1-COMB'] (code/th_redo/state_base_b.py) and code/th_r13/panel_installed.json. Book = DS7 tag (K7=st, U7=u5, P7=p5, M7=pb, H7=h6, A7=a6). The v1.5+ per-book state-cut lines installed live (v1.9a) are NOT on the box; the user stated only P7 `pct<=-0.667 pulled_mult>=5 win=5 persist=3` and the two M7 cuts (-40, -53.6).
| book | v1.4 source: L2 loss cut | v1.4 policy file (GATE0 s6) | stop exit mode in v1.4 source | engine assumes (S1-COMB state cut, arm pts / mult x / window s / persist s / newMae) | to check in v1.9a |
|---|---|---|---|---|---|
| K7 (st) | ManageThL2 loss: ThL2LossMinPts 30 (global), 30x, 5 s, newMae; skipped if ExitPending / Bip != 0 / NoBracket | `loss * * pct<=-0.50 pulled_mult>=30 secs_ext<=5 cut` (30 pts of 60; all books); profit lines Mon 08:05-08:15 only: K7 `pct>=0.7 tot_rel>=1.2 tighten 30` | JoinThenMarket (StopJoin, 3 s) | 45 / 10x / 2 / 3 / newMae off (all six sessions) | the K7 state line (user's FLAT45K spec assumes it stays on); StopJoin |
| U7 (u5) | same global line | same loss line; profit `pct>=0.17 tot_rel>=1.5 take` Mon 08:05-08:15 only | JoinThenMarket | 30 / 60x / 15 / 5 / off | state line and the 30-min same-side post-cut blackout |
| H7 (h6) | same | same; profit `pct>=0.3 ahead_rel>=1.5 take` (Mon only) | Native (not assigned in the source, enum default; GATE0 s3 says K7/H7 JoinThenMarket - the source assigns H7 nothing) | 15 / 30x / 10 / 2 / newMae on (sessions 0,1,2,4,5); session 3 (NY-AM): 35 / 20x / 2 / 1 / off | H7 bug exits on 11-08/09 night; which line replaced them |
| A7 (a6) | same | same | Native | 30 / 60x / 15 / 3 / off | A7 had its own cut ON in v1.4 (GATE0 s5) |
| M7 (pb) | same | same | JoinThenMarket | 30 / 10x / 2 / 2 / off (all sessions) | the two live M7 cuts (-40, -53.6) prove a cut path that fires on M7: compare its line with P7's (same code path?) |
| P7 (p5) | same | same; profit `pct>=0.5 ahead_rel>=1.5 take` (Mon only) | JoinThenMarket (source L574: p5 gets StStopExitMode; GATE0 s3 said Native - the source and the live StopJoin exits agree) | live panel override from 2026-11-09 20:30Z: 40 / 5x / 5 / 3 / off on every P7 session (S1-COMB itself: session 0 50/5x/3/3/newMae on, sessions 1-5 45/5x/5/10/off) | NO FIRE on the three 11-11 trades although engine, replica and v1.4-literal all fire; M7 fired the same night |
Notes: (i) the engine's per-book cells are fitted/selected lines of the state sizer, not copies of a live file - whether each is what v1.9a has installed is exactly the check this table prepares. (ii) The M7 live cuts fired on 11-12 (the same day, hours after the P7 stops): if M7 and P7 share one code path, what differs is the book (M7 line is 30 pts / 10x / 2 s / 2) or the state at the time (P7 trades ran at 00:11-02:46Z = 19:11-21:46 chart; M7 cuts at 11:30 and 12:21Z = 06:30 and 07:21 chart). (iii) With the v1.4 definitions the engine-assumed lines for K7/U7/H7/A7/M7 all fire on this same night's clean book more easily than the 30x line (mult 10/60/30/60/10 x MedLevel 2).

(iv) Stop-exit modes: GATE0 s3 (user, v1.4) says K7/H7 = JoinThenMarket and P7/U7/M7/A7/O7 = Native; the v1.4 source assigns JoinThenMarket to st (K7), pb (M7), u5 (U7), p5 (P7) and to nothing for h6 (H7), a6 (A7), o6 (O7, explicit Native). The live StopJoin exits of P7 match the source. The engine (sim JOIN_BOOKS = K7, M7, U7, P7) agrees with the source; H7 is the one book where GATE0 and the source disagree - confirm in v1.9a.

## 5. Next (not done)
1. When ~/DS7.cs is v1.9a (watcher): write PortV19A against the harness (StateTick -> per-second rows, StateStore, StateCancelSide cancelled-size definition, StatePulled window, StateOnPrint, DepthLive, ManagePolicyState loss loop), replay the three P7 trades and the two M7 cuts, print per second live-port pulled / MedLevel / mult next to the engine's, name the first diverging line.
2. When the 08:00-14:00Z batch lands (watcher): M7 both-side series; match side/entry from the live M7 file if the user supplies it.
3. Items 3 (JN05W2_NOCUT / JN05W2J_NOCUT, the `loss P7 * pct<=-0.70 win=1 persist=1 cut` stand-in on all windows) are for the exact-engine agents (W-J / W-C), not for this replay agent.

Files: code/th_p7fid/{arrival.py, v14port.py, run_v14.py, m7_events.py, watch_ds7.sh}; data /mnt/l2/l2vast/_p7fid/{v14_p7.pkl, v14_tables.md}; companion autopilot/DS3_P7_CUT_FIDELITY.md.
