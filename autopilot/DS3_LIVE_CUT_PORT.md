# DS3_LIVE_CUT_PORT - literal Python port of DS7.cs v1.9a state cut, replay of the 11-12 UTC P7 trades and M7 cuts (W-PORT, 2026-11-13, first finding 01:34Z)
Order: autopilot/DIRECTIVE_LIVE_CUT_PORT_20261113.md (user priority 1). Shadow only; no PASS claim. Chart clock = Eastern UTC-5. Source read: ~/DS7.cs (506,585 bytes, mtime Nov 12 20:41), not inferred.

## 0. ANSWER IN FIVE LINES
1. **The literal v1.9a port FIRES on all three P7 trades** (raw NQ mbp-10, arrival order): 00:16:39 at -45.6 pts, 01:26:17 at -40.5, 02:43:19 at -40.6 (rule pct<=-0.667 pulled_mult>=5 win=5 persist=3; arm = 0.667 x |entry-stop| = 40.2 / 38.2 / 37.2 pts; mult at the decision 14.1 / 23.6 / 18.5). The live exits were the stop touches 00:17:15, 01:28:24, 02:45:21, i.e. 36 s, 127 s, 122 s after the port's decision.
2. **No line of StateTick, StateStore, StateCancelSide, StatePulled, StateOnPrint, DepthLive or the loss loop of ManagePolicyState diverges from the engine on a clean book**: per-second pulled_mult port vs engine state base, seconds at u <= -30: median ratio 0.99 / 1.00 / 1.00, correlation 0.994 / 0.995 / 0.994; MedLevel 1.85 / 1.87 / 2.00 (engine 1.83 / 1.87 / 2.00); DepthLive false 0 s; 0 foreign levels; 0 array-vs-book mismatches over 2.77 M records / 4.68 M depth operations. So I cannot name a divergent DS7.cs line in the code I was asked to port: **it is not in this arithmetic.**
3. **The same port reproduces both live M7 cuts to the second** (section 3): with the arm read off the cut itself (40.0 pts at 11:30:44 decision, 53.4-53.6 pts at the 12:21:30 decision; long side; persist 1) the first second at which unreal reaches the arm and pulled_mult passes is exactly the live cut second, for any mult threshold 1x..15x on a 5 s window. The 12:21:31 cut at -53.6 is therefore NOT a late cut of a 40-pt line: it is a 53-pt arm reached at 12:21:30. Short-side hypotheses match neither event. This says the live StateTick / pulled / MedLevel / DepthLive / loss loop works live on 11-12 for M7.
4. **Headroom**: the P7 cut still fires before the live stop touch up to a threshold of 21x / 21x / 16.5x (clean book), against the 5x line, i.e. the live ratio pulled/MedLevel would have to be 3.3-4.2x below the clean-book value on every second of the walk. Feed distortions applied to the depth stream (conflation 250 ms / 1 s / 5 s, delay 1 s, top-5 only) do not do that (section 4: weakest case top-5, trade 3, headroom 7.5x vs the 5x line).
5. **So the P7 silence has to come from a P7-specific or evening-specific gate that is not in the arithmetic**, and which the box cannot see (section 5 lists them with line numbers and the one Output line that decides each). Needed from the user: the NT8 Output text of 11-11 chart 19:11-19:18, 19:58-20:29, 21:31-21:46 and of 11-12 chart 06:29-06:32 / 07:20-07:23 (lines "TH-STATE CUT ... rule [..]", "SHADOW", "D7 STATE: book mid", "D6 POLICY: no Level 2", "D7 TH POLICY loaded ... valid=") and the live THP_POLICY_D7.txt P7 and M7 lines.

## 1. What was ported (v19a_port.py, class PortV19A; C# line numbers in the source comments)
OnMarketDepth L1399-1412 (position bound, **5% level rejection against Closes[0][0]**, StateTick BEFORE the event, Add/Update/Remove on 20-slot arrays, depLast), OnMarketData print path L3764 (StateTick then StateOnPrint then lastPrint), DepthLive L1414 (depLast < 120 s and depBidN >= 5 and depAskN >= 5), StateTick L1651-1676 (close the previous exchange second at the FIRST event of the next one, catch-up of quiet seconds capped at 120, mid from the book top else last print, 1% mid sanity, MedLevel EWMA 0.001/s of the top-5 mean (b5+a5)/10 on live seconds), StateStore L1677 (top 10), StateCancelSide L1683 (own-side levels present at s-1, size drop net of prints at that price in the second, levels that fell out of the 10-window ignored), StatePulled L1697 (sum over the last ceil(win) closed seconds), StateOnPrint L1650, ManagePolicyState L1707-1752 loss loop (adverse-mid extreme with ties, winner -> profit engine, DepthLive/MedLevel gate, pct arm = |x| x stopDist, pulled_mult = StatePulled/stMedLevel, persist counter per rule, cut set at the close of the second). Not modelled (stated): lastBid/lastAsk events, NT8's own Add/Update/Remove granularity (inferred from book diffs; arrays equal the record book after every record), levels 10-19 (mbp-10), ThPolicyValid / regime / session / Ctx gates (rule regime '*'), ExitPending / Bip / NoBracket (assumed clear), profit-side engine, the CQG feed itself. Clock: ts_recv // 1e9 for Globals.Now.
Run: raw NQ mbp-10 11-11 23:00Z to 11-12 02:47Z (P7, warm start at the session open, one pass, 2.77 M records, 43 s) and 08:00Z to 12:25Z (M7, 2.37 M records). Files: code/th_p7fid/{v19a_port.py, run_v19a.py, run_v19a_var.py, run_v19a_m7.py, grid_m7.py, tbl_v19a.py, tbl_m7.py, mk_page.py}; data /mnt/l2/l2vast/_p7fid/{v19a_p7.pkl, v19a_var_p7_*.pkl, v19a_seclog_*.npy, v19a_p7_tables.md (every second u<=-30), v19a_m7_tables.md}. Raw data: P7 in GLBX-20261112-3MWRETB8E3 (11-11 file, 23:00-24:00Z) + GLBX-20261112-C4QA7CL36C (00:00-08:00Z); M7 in GLBX-20261112-GVL3VQXR3S (08:00-14:00Z).

## 2. The three P7 trades: port vs engine, per second
Engine columns are the state base (S1-COMB kernel) at row s+1 (its rows are labelled one second later than the port's closed second). The port's per-second series was run with the 45x ladder rule so that every second carries pulled / mult after the line would have cut; "run" = consecutive seconds with u <= -arm and mult5 >= 5 (persist 3 = cut).

#### Trade 1 SHORT 19:11 CT (00:11Z) (entry 28188.42, stop dist 60.33, arm 40.2 pts)
Literal port decision **00:16:39 at -45.6 pts, mult5 14.1** (decision at the close of that second, exit sent on the next print); engine decision 00:16:37; live: no cut, stop touched 00:17:15. Over the whole trade: 70 seconds with u <= -arm, of which 68 have mult5 >= 5. Rows below: 12 s before to 6 s after the port decision (all seconds are in the full table /mnt/l2/l2vast/_p7fid/v19a_p7_tables.md).

| UTC s | port mid | port u | pulled5 | MedLevel | mult5 | u<=-arm | run | eng u | eng ratio5 |
|---|---|---|---|---|---|---|---|---|---|
| 00:16:27 | 28210.25 | -21.8 | 18 | 1.85 | 9.7 | n | 0 | -21.8 | 9.8 |
| 00:16:28 | 28212.38 | -24.0 | 26 | 1.85 | 14.1 | n | 0 | -24.0 | 14.2 |
| 00:16:29 | 28214.38 | -26.0 | 35 | 1.85 | 18.9 | n | 0 | -26.0 | 19.1 |
| 00:16:30 | 28218.38 | -30.0 | 47 | 1.85 | 25.4 | n | 0 | -30.0 | 25.6 |
| 00:16:31 | 28221.88 | -33.5 | 53 | 1.85 | 28.7 | n | 0 | -33.5 | 30.0 |
| 00:16:32 | 28222.88 | -34.5 | 58 | 1.85 | 31.4 | n | 0 | -34.5 | 33.3 |
| 00:16:33 | 28225.25 | -36.8 | 55 | 1.85 | 29.8 | n | 0 | -36.8 | 32.7 |
| 00:16:34 | 28228.62 | -40.2 | 52 | 1.85 | 28.1 | n | 0 | -40.2 | 32.2 |
| 00:16:35 | 28229.25 | -40.8 | 38 | 1.85 | 20.6 | Y | 1 | -40.8 | 24.6 |
| 00:16:36 | 28228.62 | -40.2 | 28 | 1.85 | 15.2 | n | 0 | -40.2 | 18.0 |
| 00:16:37 | 28234.00 | -45.6 | 30 | 1.85 | 16.2 | Y | 1 | -45.6 | 18.6 |
| 00:16:38 | 28234.88 | -46.5 | 30 | 1.85 | 16.2 | Y | 2 | -46.5 | 18.6 |
| 00:16:39 | 28234.00 | -45.6 | 26 | 1.85 | 14.1 | Y | 3 | -45.6 | 15.3 |
| 00:16:40 | 28234.00 | -45.6 | 26 | 1.85 | 14.1 | Y | 4 | -45.6 | 15.3 |
| 00:16:41 | 28230.00 | -41.6 | 24 | 1.85 | 13.0 | Y | 5 | -41.6 | 14.2 |
| 00:16:42 | 28230.25 | -41.8 | 16 | 1.85 | 8.7 | Y | 6 | -41.8 | 9.8 |
| 00:16:43 | 28231.25 | -42.8 | 13 | 1.85 | 7.0 | Y | 7 | -42.8 | 7.1 |
| 00:16:44 | 28228.75 | -40.3 | 10 | 1.85 | 5.4 | Y | 8 | -40.3 | 5.5 |
| 00:16:45 | 28230.00 | -41.6 | 18 | 1.85 | 9.8 | Y | 9 | -41.6 | 9.8 |

#### Trade 2 SHORT 19:58 CT (00:58Z) (entry 28211.04, stop dist 57.21, arm 38.2 pts)
Literal port decision **01:26:17 at -40.5 pts, mult5 23.6** (decision at the close of that second, exit sent on the next print); engine decision 01:27:29; live: no cut, stop touched 01:28:24. Over the whole trade: 119 seconds with u <= -arm, of which 116 have mult5 >= 5. Rows below: 12 s before to 6 s after the port decision (all seconds are in the full table /mnt/l2/l2vast/_p7fid/v19a_p7_tables.md).

| UTC s | port mid | port u | pulled5 | MedLevel | mult5 | u<=-arm | run | eng u | eng ratio5 |
|---|---|---|---|---|---|---|---|---|---|
| 01:26:05 | 28243.25 | -32.2 | 23 | 1.86 | 12.4 | n | 0 | -32.2 | 12.4 |
| 01:26:06 | 28243.50 | -32.5 | 28 | 1.86 | 15.1 | n | 0 | -32.5 | 15.0 |
| 01:26:07 | 28242.62 | -31.6 | 25 | 1.86 | 13.4 | n | 0 | -31.6 | 13.4 |
| 01:26:08 | 28243.38 | -32.3 | 28 | 1.86 | 15.0 | n | 0 | -32.3 | 15.0 |
| 01:26:09 | 28245.12 | -34.1 | 37 | 1.86 | 19.9 | n | 0 | -34.1 | 19.9 |
| 01:26:10 | 28246.12 | -35.1 | 54 | 1.86 | 29.0 | n | 0 | -35.1 | 29.0 |
| 01:26:11 | 28246.12 | -35.1 | 54 | 1.86 | 29.0 | n | 0 | -35.1 | 29.0 |
| 01:26:12 | 28246.88 | -35.8 | 59 | 1.86 | 31.7 | n | 0 | -35.8 | 31.7 |
| 01:26:13 | 28246.38 | -35.3 | 57 | 1.86 | 30.6 | n | 0 | -35.3 | 30.6 |
| 01:26:14 | 28248.12 | -37.1 | 51 | 1.86 | 27.4 | n | 0 | -37.1 | 27.9 |
| 01:26:15 | 28250.25 | -39.2 | 42 | 1.86 | 22.5 | Y | 1 | -39.2 | 24.1 |
| 01:26:16 | 28250.50 | -39.5 | 40 | 1.87 | 21.4 | Y | 2 | -39.5 | 23.0 |
| 01:26:17 | 28251.50 | -40.5 | 44 | 1.87 | 23.6 | Y | 3 | -40.5 | 25.2 |
| 01:26:18 | 28252.00 | -41.0 | 37 | 1.87 | 19.8 | Y | 4 | -41.0 | 21.4 |
| 01:26:19 | 28249.62 | -38.6 | 26 | 1.87 | 13.9 | Y | 5 | -38.6 | 15.0 |
| 01:26:20 | 28248.75 | -37.7 | 20 | 1.87 | 10.7 | n | 0 | -37.7 | 10.7 |
| 01:26:21 | 28248.25 | -37.2 | 20 | 1.87 | 10.7 | n | 0 | -37.2 | 10.7 |
| 01:26:22 | 28248.12 | -37.1 | 13 | 1.87 | 7.0 | n | 0 | -37.1 | 7.0 |
| 01:26:23 | 28250.00 | -39.0 | 25 | 1.87 | 13.4 | Y | 1 | -39.0 | 13.4 |

#### Trade 3 LONG 21:31 CT (02:31Z) (entry 28337.50, stop dist 55.75, arm 37.2 pts)
Literal port decision **02:43:19 at -40.6 pts, mult5 18.5** (decision at the close of that second, exit sent on the next print); engine decision 02:43:24; live: no cut, stop touched 02:45:21. Over the whole trade: 128 seconds with u <= -arm, of which 117 have mult5 >= 5. Rows below: 12 s before to 6 s after the port decision (all seconds are in the full table /mnt/l2/l2vast/_p7fid/v19a_p7_tables.md).

| UTC s | port mid | port u | pulled5 | MedLevel | mult5 | u<=-arm | run | eng u | eng ratio5 |
|---|---|---|---|---|---|---|---|---|---|
| 02:43:07 | 28309.62 | -27.9 | 20 | 2.00 | 10.0 | n | 0 | -27.9 | 10.0 |
| 02:43:08 | 28309.88 | -27.6 | 18 | 2.00 | 9.0 | n | 0 | -27.6 | 9.0 |
| 02:43:09 | 28309.75 | -27.8 | 14 | 2.00 | 7.0 | n | 0 | -27.8 | 7.0 |
| 02:43:10 | 28308.50 | -29.0 | 25 | 2.00 | 12.5 | n | 0 | -29.0 | 12.5 |
| 02:43:11 | 28306.00 | -31.5 | 28 | 2.00 | 14.0 | n | 0 | -31.5 | 15.5 |
| 02:43:12 | 28304.50 | -33.0 | 37 | 2.00 | 18.5 | n | 0 | -33.0 | 21.5 |
| 02:43:13 | 28305.00 | -32.5 | 39 | 2.00 | 19.5 | n | 0 | -32.5 | 22.5 |
| 02:43:14 | 28304.62 | -32.9 | 44 | 2.00 | 22.0 | n | 0 | -32.9 | 25.0 |
| 02:43:15 | 28302.50 | -35.0 | 37 | 2.00 | 18.5 | n | 0 | -35.0 | 22.5 |
| 02:43:16 | 28303.12 | -34.4 | 26 | 2.00 | 13.0 | n | 0 | -34.4 | 15.5 |
| 02:43:17 | 28299.62 | -37.9 | 26 | 2.00 | 13.0 | Y | 1 | -37.9 | 14.5 |
| 02:43:18 | 28299.00 | -38.5 | 31 | 2.00 | 15.5 | Y | 2 | -38.5 | 17.0 |
| 02:43:19 | 28296.88 | -40.6 | 37 | 2.00 | 18.5 | Y | 3 | -40.6 | 20.0 |
| 02:43:20 | 28298.75 | -38.8 | 33 | 2.00 | 16.5 | Y | 4 | -38.8 | 17.0 |
| 02:43:21 | 28296.50 | -41.0 | 40 | 2.00 | 20.0 | Y | 5 | -41.0 | 20.5 |
| 02:43:22 | 28291.25 | -46.2 | 33 | 2.00 | 16.5 | Y | 6 | -46.2 | 16.5 |
| 02:43:23 | 28292.75 | -44.8 | 33 | 2.00 | 16.5 | Y | 7 | -44.8 | 16.5 |
| 02:43:24 | 28295.12 | -42.4 | 27 | 2.00 | 13.5 | Y | 8 | -42.4 | 13.5 |
| 02:43:25 | 28295.75 | -41.8 | 28 | 2.00 | 14.0 | Y | 9 | -41.8 | 14.0 |

## 3. The two M7 cuts (live 11:30:45Z at -40, 12:21:31Z at -53.6)
Entry price and side are not on the box. Convention (as m7_feed.py): entry = mid at the cut -/+ |u|; entry time = last touch of that price before the cut (11:23:37 and 12:13:18 for the LONG hypothesis). The port was run on both sides.
- **Short side** (entries 28175.88 / 28197.90): no line in the grid fires within +-2 s of either live cut (0 matches for each event). Long side is the only consistent one.
- **Long side**: unreal reaches -40.0 first at the 11:30:44 second and -53.6 first at the 12:21:30 second (the live cut seconds; the live StateExecute prints on the next print). Over a grid of lines (arm fixed at 40.0 / 53.4, mult 0-30 x, win 1-15 s, persist 1-3, secs_ext off/0..10) **301 lines reproduce BOTH decision seconds, all with persist 1** (e.g. 5x / 5 s / persist 1; 10x / 5 s; 2x / 2 s). Persist 2 or 3 never matches (the arm is first reached on the decision second, so a persist-2 line would have cut one second later). The engine M7 cell (30 pts, 10x, 2 s, persist 2) would have decided 11:30:35 and 12:13:38 (at -39.5 and -33.5), i.e. earlier than live: the live M7 line is a larger-arm persist-1 line (arm 40 and ~53 pts, i.e. a pct of the trade's own stop distance of about 60 and about 80 pts), not the engine cell.
- Consequence: the "late" 12:21:31 cut is the arm, not a feed delay; the pulled condition was satisfied at the first arm crossing in both events, so live pulled/MedLevel were at least as large as the line needs (anywhere from 1x to 15x on 5 s fits), which excludes a 4x live shortfall at 11:30Z and 12:21Z.
- Per second (long hypothesis, port log rule next to the engine; u from the hypothesised entry):

#### M4_s+1_log : hypothesis LONG (entry 28255.88 = mid at the cut + |u|), live M7 cut 11:30:45 at -40.0. port log rule has no arm (arm 1e9), columns show the raw series; fire columns from the sibling books

| UTC s | port mid | port u | pulled2 | pulled5 | MedLevel | mult2 | mult5 | eng ratio2 | eng ratio5 | eng med | u>=40 & mult2>=10 | u>=40 & mult5>=5 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 11:30:20 | 28225.00 | -30.9 | 8 | 24 | 2.41 | 3.3 | 9.9 | 3.3 | 9.9 | 2.41 | n | n |
| 11:30:21 | 28225.62 | -30.3 | 10 | 25 | 2.41 | 4.1 | 10.4 | 4.1 | 10.4 | 2.41 | n | n |
| 11:30:22 | 28225.38 | -30.5 | 6 | 28 | 2.41 | 2.5 | 11.6 | 2.5 | 11.6 | 2.42 | n | n |
| 11:30:23 | 28226.00 | -29.9 | 5 | 15 | 2.42 | 2.1 | 6.2 | 2.1 | 6.2 | 2.42 | n | n |
| 11:30:24 | 28228.12 | -27.8 | 1 | 15 | 2.42 | 0.4 | 6.2 | 0.4 | 6.2 | 2.42 | n | n |
| 11:30:25 | 28227.50 | -28.4 | 13 | 20 | 2.41 | 5.4 | 8.3 | 5.4 | 8.3 | 2.42 | n | n |
| 11:30:26 | 28226.12 | -29.8 | 26 | 31 | 2.41 | 10.8 | 12.8 | 10.8 | 12.8 | 2.41 | n | n |
| 11:30:27 | 28226.38 | -29.5 | 15 | 29 | 2.41 | 6.2 | 12.0 | 6.2 | 12.0 | 2.41 | n | n |
| 11:30:28 | 28226.25 | -29.6 | 4 | 30 | 2.41 | 1.7 | 12.4 | 1.7 | 12.4 | 2.41 | n | n |
| 11:30:29 | 28223.75 | -32.1 | 23 | 51 | 2.41 | 9.5 | 21.1 | 9.5 | 21.1 | 2.41 | n | n |
| 11:30:30 | 28222.62 | -33.3 | 36 | 53 | 2.41 | 14.9 | 21.9 | 14.9 | 21.9 | 2.42 | n | n |
| 11:30:31 | 28222.75 | -33.1 | 15 | 40 | 2.41 | 6.2 | 16.6 | 6.2 | 16.6 | 2.41 | n | n |
| 11:30:32 | 28222.62 | -33.3 | 1 | 39 | 2.41 | 0.4 | 16.2 | 0.4 | 16.1 | 2.42 | n | n |
| 11:30:33 | 28222.00 | -33.9 | 9 | 45 | 2.42 | 3.7 | 18.6 | 3.7 | 18.6 | 2.42 | n | n |
| 11:30:34 | 28219.12 | -36.8 | 29 | 45 | 2.41 | 12.0 | 18.6 | 12.0 | 18.6 | 2.42 | n | n |
| 11:30:35 | 28216.38 | -39.5 | 35 | 44 | 2.42 | 14.5 | 18.2 | 14.5 | 18.2 | 2.42 | n | n |
| 11:30:36 | 28217.50 | -38.4 | 14 | 44 | 2.42 | 5.8 | 18.2 | 5.8 | 18.2 | 2.42 | n | n |
| 11:30:37 | 28217.00 | -38.9 | 8 | 51 | 2.42 | 3.3 | 21.1 | 3.3 | 21.1 | 2.42 | n | n |
| 11:30:38 | 28217.50 | -38.4 | 8 | 43 | 2.42 | 3.3 | 17.8 | 3.3 | 17.8 | 2.42 | n | n |
| 11:30:39 | 28217.25 | -38.6 | 9 | 31 | 2.42 | 3.7 | 12.8 | 3.7 | 12.8 | 2.42 | n | n |
| 11:30:40 | 28216.38 | -39.5 | 23 | 31 | 2.42 | 9.5 | 12.8 | 9.5 | 12.8 | 2.42 | n | n |
| 11:30:41 | 28216.62 | -39.3 | 16 | 33 | 2.42 | 6.6 | 13.6 | 6.6 | 13.6 | 2.42 | n | n |
| 11:30:42 | 28216.00 | -39.9 | 5 | 28 | 2.42 | 2.1 | 11.6 | 2.1 | 11.6 | 2.42 | n | n |
| 11:30:43 | 28216.00 | -39.9 | 6 | 31 | 2.42 | 2.5 | 12.8 | 2.5 | 12.8 | 2.42 | n | n |
| 11:30:44 | 28215.88 | -40.0 | 8 | 27 | 2.42 | 3.3 | 11.1 | 3.3 | 11.1 | 2.42 | n | Y |
| 11:30:45 | 28214.25 | -41.6 | 23 | 31 | 2.42 | 9.5 | 12.8 | 9.5 | 12.8 | 2.42 | n | Y |
| 11:30:46 | 28215.25 | -40.6 | 18 | 29 | 2.43 | 7.4 | 12.0 | 7.4 | 12.0 | 2.43 | n | Y |
| 11:30:47 | 28216.50 | -39.4 | 0 | - | 2.43 | 0.0 | - | 0.0 | 10.7 | 2.43 | n | n |
| 11:30:48 | 28217.12 | -38.8 | 1 | - | 2.43 | 0.4 | - | 0.4 | 9.9 | 2.43 | n | n |
| 11:30:49 | 28219.00 | -36.9 | 1 | - | 2.43 | 0.4 | - | 0.4 | 7.8 | 2.43 | n | n |
| 11:30:50 | 28220.00 | -35.9 | 6 | - | 2.43 | 2.5 | - | 2.5 | 2.9 | 2.43 | n | n |

#### M5_s+1_log : hypothesis LONG (entry 28305.10 = mid at the cut + |u|), live M7 cut 12:21:31 at -53.6. port log rule has no arm (arm 1e9), columns show the raw series; fire columns from the sibling books

| UTC s | port mid | port u | pulled2 | pulled5 | MedLevel | mult2 | mult5 | eng ratio2 | eng ratio5 | eng med | u>=40 & mult2>=10 | u>=40 & mult5>=5 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 12:21:00 | 28270.62 | -34.5 | 5 | 21 | 2.22 | 2.2 | 9.4 | 2.2 | 9.4 | 2.22 | n | n |
| 12:21:01 | 28270.25 | -34.8 | 12 | 28 | 2.22 | 5.4 | 12.6 | 5.4 | 12.6 | 2.22 | n | n |
| 12:21:02 | 28269.62 | -35.5 | 16 | 27 | 2.22 | 7.2 | 12.1 | 7.2 | 12.1 | 2.22 | n | n |
| 12:21:03 | 28269.75 | -35.3 | 10 | 23 | 2.22 | 4.5 | 10.3 | 4.5 | 10.3 | 2.22 | n | n |
| 12:21:04 | 28266.00 | -39.1 | 31 | 51 | 2.22 | 13.9 | 22.9 | 13.9 | 22.9 | 2.22 | n | n |
| 12:21:05 | 28267.00 | -38.1 | 30 | 48 | 2.22 | 13.5 | 21.6 | 13.5 | 21.6 | 2.22 | n | n |
| 12:21:06 | 28263.88 | -41.2 | 24 | 63 | 2.22 | 10.8 | 28.4 | 10.8 | 28.3 | 2.22 | Y | Y |
| 12:21:07 | 28263.12 | -42.0 | 29 | 61 | 2.22 | 13.0 | 27.4 | 13.5 | 27.9 | 2.22 | Y | Y |
| 12:21:08 | 28263.88 | -41.2 | 9 | 62 | 2.22 | 4.0 | 27.9 | 4.5 | 28.3 | 2.22 | n | Y |
| 12:21:09 | 28264.12 | -41.0 | 4 | - | 2.22 | 1.8 | - | 1.8 | 15.7 | 2.22 | n | n |
| 12:21:10 | 28263.12 | -42.0 | 15 | - | 2.22 | 6.8 | - | 6.7 | 21.6 | 2.22 | n | n |
| 12:21:11 | 28263.00 | -42.1 | 16 | - | 2.22 | 7.2 | - | 7.2 | 12.1 | 2.22 | n | n |
| 12:21:12 | 28265.62 | -39.5 | 2 | - | 2.22 | 0.9 | - | 0.9 | 9.0 | 2.22 | n | n |
| 12:21:13 | 28265.25 | -39.8 | 10 | - | 2.22 | 4.5 | - | 4.5 | 12.1 | 2.22 | n | n |
| 12:21:14 | 28263.75 | -41.3 | 24 | - | 2.22 | 10.8 | - | 10.8 | 18.0 | 2.22 | Y | n |
| 12:21:15 | 28263.50 | -41.6 | 18 | - | 2.22 | 8.1 | - | 8.1 | 13.5 | 2.22 | n | n |
| 12:21:16 | 28264.38 | -40.7 | 4 | - | 2.22 | 1.8 | - | 1.8 | 12.6 | 2.22 | n | n |
| 12:21:17 | 28263.88 | -41.2 | 2 | - | 2.22 | 0.9 | - | 0.9 | 13.5 | 2.22 | n | n |
| 12:21:18 | 28260.00 | -45.1 | 33 | - | 2.22 | 14.9 | - | 16.7 | 24.8 | 2.22 | Y | n |
| 12:21:19 | 28258.12 | -47.0 | 42 | - | 2.22 | 18.9 | - | 20.7 | 23.4 | 2.22 | Y | n |
| 12:21:20 | 28256.50 | -48.6 | 26 | - | 2.22 | 11.7 | - | 12.1 | 28.8 | 2.22 | Y | n |
| 12:21:21 | 28255.50 | -49.6 | 27 | - | 2.22 | 12.2 | - | 12.6 | 34.2 | 2.22 | Y | n |
| 12:21:22 | 28256.38 | -48.7 | 13 | - | 2.22 | 5.9 | - | 5.8 | 33.7 | 2.22 | n | n |
| 12:21:23 | 28255.25 | -49.8 | 11 | - | 2.22 | 5.0 | - | 5.0 | 22.5 | 2.22 | n | n |
| 12:21:24 | 28255.00 | -50.1 | 14 | - | 2.22 | 6.3 | - | 6.3 | 19.4 | 2.22 | n | n |
| 12:21:25 | 28254.12 | -51.0 | 16 | - | 2.22 | 7.2 | - | 7.2 | 17.6 | 2.22 | n | n |
| 12:21:26 | 28254.88 | -50.2 | 12 | - | 2.22 | 5.4 | - | 5.4 | 12.2 | 2.22 | n | n |
| 12:21:27 | 28255.75 | -49.3 | 4 | - | 2.22 | 1.8 | - | 1.8 | 13.5 | 2.22 | n | n |
| 12:21:28 | 28254.62 | -50.5 | 7 | - | 2.22 | 3.2 | - | 3.2 | 10.4 | 2.22 | n | n |
| 12:21:29 | 28252.38 | -52.7 | 22 | - | 2.22 | 9.9 | - | 9.9 | 17.1 | 2.22 | n | n |
| 12:21:30 | 28251.50 | -53.6 | 28 | - | 2.22 | 12.6 | - | 12.6 | 15.7 | 2.22 | Y | n |
| 12:21:31 | 28254.12 | -51.0 | 9 | - | 2.22 | 4.1 | - | 4.0 | 15.7 | 2.22 | n | n |
| 12:21:32 | 28252.75 | -52.3 | 20 | - | 2.22 | 9.0 | - | 9.9 | 23.8 | 2.22 | n | n |
| 12:21:33 | 28254.12 | -51.0 | 20 | - | 2.22 | 9.0 | - | 9.9 | 22.5 | 2.22 | n | n |
| 12:21:34 | 28259.12 | -46.0 | 0 | - | 2.22 | 0.0 | - | 0.0 | 13.9 | 2.22 | n | n |
| 12:21:35 | 28259.50 | -45.6 | 2 | - | 2.22 | 0.9 | - | 0.9 | 10.8 | 2.22 | n | n |
| 12:21:36 | 28259.75 | -45.3 | 4 | - | 2.22 | 1.8 | - | 1.8 | 11.7 | 2.22 | n | n |
| 12:21:37 | 28260.62 | -44.5 | 10 | - | 2.22 | 4.5 | - | 4.5 | 5.4 | 2.22 | n | n |
| 12:21:38 | 28261.88 | -43.2 | 9 | - | 2.22 | 4.1 | - | 4.5 | 6.3 | 2.22 | n | n |
| 12:21:39 | 28260.88 | -44.2 | 14 | - | 2.22 | 6.3 | - | 6.7 | 12.1 | 2.22 | n | n |
| 12:21:40 | 28260.25 | -44.8 | 20 | - | 2.22 | 9.0 | - | 9.0 | 14.4 | 2.22 | n | n |

## 4. Feed hypotheses on the literal port (depth stream transformed by code/th_p7fid/feed.py; prints keep true time)
Headroom column: the highest ladder threshold (5, 7.5, 10, 15, 20, 30, 45 x) at which the cut still fires before the live stop touch.
| feed setting (literal v1.9a port, 5x / win 5 / persist 3 line) | T1 fire @5x / max ladder mult that still cuts before the live stop | T2 | T3 | seconds with DepthLive false |
|---|---|---|---|---|
| base | 00:16:39 / 20x | 01:26:17 / 20x | 02:43:19 / 15x | 0 |
| conf250 | 00:16:37 / 20x | 01:26:17 / 15x | 02:43:20 / 20x | 0 |
| conf1000 | 00:16:38 / 20x | 01:26:18 / 30x | 02:43:20 / 20x | 1 |
| conf5000 | 00:16:42 / 10x | 01:26:22 / 10x | 02:43:22 / 15x | 5 |
| delay1000 | 00:16:40 / 20x | 01:26:18 / 30x | 02:43:20 / 20x | 1 |
| top5 | 00:16:39 / 10x | 01:26:17 / 15x | 02:43:19 / 7.5x | 0 |
Reading: nothing silences the 5x line; the only setting that cuts the margin materially is top-5 only on trade 3 (7.5x), and fewer than 5 levels makes DepthLive false for every book (M7 would be silent too, and it was not). Implied orders and CQG's own event granularity cannot be tested from Databento (no outright/implied flag).

## 5. Where the live P7 cut can be silenced although the port fires (ranked by what the evidence leaves; each with the line and what decides it)
The M7 result (section 3) removes the generic suspects (StateTick running at all, DepthLive, pulled/MedLevel scale, persist counter) for the morning of 11-12. What remains differs between the P7 evening trades and the M7 morning cuts, or between the books:
1. **The P7 policy line is not the line assumed** (ThRule parse L2610-2650; evaluation L1724-1750): the regime column (L1722: matches DayRegime, the session name or the entry context 'fresh' / 'rechase'; the three P7 trades fall in the session named for hm >= 1800 or < 200, M7's cuts in the 06:30-07:21 session) or persist / win / pct differing. **Decides:** the live "D7 TH POLICY loaded ... N rules" line and the file's P7 loss lines; also the "TH-STATE CUT ... rule [raw line]" text of the M7 cuts (it prints the rule, win and arm).
2. **ThPolicyValid (L2681)**: et.AddHours(6).Date <= valid= date. An evening trade at 19:11 chart is labelled the next calendar day; a file with valid= the calendar day of the evening is invalid for the whole evening session and valid again after the 18:00 roll of the next label day only if the file was re-issued. A silent return at L1712. **Decides:** the valid= in the loaded header and whether the file was re-issued between 02:46Z and 11:30Z on 11-12.
3. **Book gates at L1673** (b.InTrade, ExitPending, Bip != 0, NoBracket) and L1710 (PolicyTriggered, StCutRule set, StShadowSeen): P7 is the JoinThenMarket book with the JN04 stack and post-stop blackout; if any of these held during the walk the loop never reaches L1724. **Decides:** a per-second diagnostic (patch below); the Output shows no "TH-STATE" text either way.
4. **PolicyStateMode = Shadow (L1853)**: the cut is then logged as "SHADOW TH-STATE CUT" and not executed (StShadowSeen). **Decides:** grep for SHADOW at 19:16:39 / 20:26:17 / 21:43:19 chart.
5. **An exception swallowed by try { StateTick(...) } catch { } (L1404, L3764)**: an exception inside ManagePolicyState aborts the second loop before stSec is advanced (L1675), so the same seconds are replayed on every event and the book never completes an evaluation; this would also be silent in the Output. A trade-specific null (b.StopPx, a rule field, SessionNames index) is the kind of thing that does it. **Decides:** the same per-second diagnostic and a Print in the catch.
6. **Evening-only feed state** (not testable from Databento): foreign (ES/RTY) depth with price 0 passing the 5% rejection (L1403 requires e.Price > 0, so a Remove with Price 0 is applied to the NQ arrays), which shrinks depBidN/depAskN and corrupts MedLevel; no ES raw for the night on the box (ES raw ends 10-31), so it could not be injected with real data.
A one-line fix for 6 independent of what is found: reject by instrument identity / keep a per-position last NQ price instead of the price test.

### Diagnostic patch proposal for DS7.cs (text only, not applied; the lead/user decides)
In ManagePolicyState, after L1719 and inside the rule loop after pulledMult is known, print once per second per book while unreal <= -20: Print(now + " " + b.Tag + " STATEDIAG u=" + unreal.ToString("0.0") + " arm=" + armPts.ToString("0.0") + " pulled=" + StatePulled(b.Side, sec, win).ToString("0") + " med=" + stMedLevel.ToString("0.00") + " mult=" + pulledMult.ToString("0.0") + " ok=" + ok + " cnt=" + cnt + " nB=" + depBidN + " nA=" + depAskN + " live=" + depthLive + " rule=[" + r.Raw + "]"); and one line at each early return of ManagePolicyState / the L1673 book filter naming the reason (valid, shadow, PolicyTriggered, StCutRule, ExitPending, Bip, NoBracket), plus Print(ex.Message) inside the two catch blocks around StateTick. One evening of this log names the gate.

## 6. Next (not done)
- Output text / policy file from the user (section 0 item 5) would close the question in minutes; I did not find any live log on the box.
- Items 3-4 of the user order (JN05W2_NOCUT / the -0.70 stand-in on all windows; K7/U7/H7/A7 lines) belong to the exact-engine agents.
