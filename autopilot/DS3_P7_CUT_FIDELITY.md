# DS3_P7_CUT_FIDELITY - live 2026-11-11 night: three P7 full stops, state cut never fired (W-R, 2026-11-12 ~19:00Z)
Shadow only, no PASS claim. Order: autopilot/DIRECTIVE_P7_CUT_FIDELITY_20261112.md. Code: code/th_p7fid/ (build_night.py, trades.py, eng_state.py, rep_l2.py, sens.py, tags_f3.py, series_tbl.py). Data: raw NQ mbp-10 bought for this order (batch GLBX-20261112-C4QA7CL36C, UTC 11-12 00:00-08:00, $0.83) + the 11-10/11-11 files of the earlier batch; private builds under /mnt/l2/l2vast/_p7fid/.

## 0. HEADLINE
1. **The engine cut fires on all three trades, with room to spare, and so does the literal per-print replica.** Engine state cut (arm 40 pts = pct -0.667 of 60, pulled(5 s)/MedLevel >= 5, adverse extreme within 5 s, persist 3 s) decides at 00:16:37Z (-45.6 pts at exit), 01:27:29Z (-43.1) and 02:43:24Z (-43.2) = 19:16:37, 20:27:29, 21:43:24 on the chart clock, i.e. 38 s, 55 s and 117 s BEFORE the live stop fills. The replica rule (per-print snapshot, print price, once per second) fires at 00:16:40, 01:27:29, 02:43:24 (0-3 s from the engine). The cut would have saved about $1.7k, $1.7k and $1.5k at 6 lots (total $4.9k) against the three live stops (-$20.9k).
2. **So the live cut was silent for a reason that is on the live side, not in the engine.** The margins say it is not a small definitional difference: the engine would still cut with MedLevel inflated 3-4x (mult 15-20 instead of 5), with persist up to 10-20 s, with arm up to 54-58 pts, and without the newMae test. A live cut that is inert for 3 of 3 trades through -40 .. -60 needs a gate that is closed or a scale error >= 4x (candidates in section 5; the live per-evaluation log forward_register/th_eval.csv for 11-11 decides it).
3. **What it means: the engine's P7 cut is a near-universal hard stop at about -42 pts, not a rare event.** LPB_BASE L6M: P7 StateCut 20.8 per week (541 of 1,060 trades, median -42.3 pts, mean -$3,078) against 0.62 full stops per week (the 0.4 figure). If the live cut does not fire, live P7 behaves like WB_C_NONE (cut off, exact): 15.7 full stops per week, 19.3 targets per week. Three full stops in one night is ordinary for that world. Every P7 result that depends on the cut (WG_*, WB_X_FR_F3, JN04RM/JN05W stacks, the 0.4/wk figure, behavioural scorecard on full stops) describes a live cut that is not currently running. Section 6.
4. **Chart clock is UTC-5 (CDT), not Central Standard.** The stop levels are touched in the raw 1-s mid at 00:17:15Z (chart 19:17:15 = StopJoin second to the second), 01:28:24-27Z (20:28:24) and 02:45:21Z (21:45:21); entry prices match the book at 00:11Z, 00:58Z, 02:31Z. All timestamps below are UTC with chart = UTC - 5 h. (If DS7's chart/PC clock stayed on CDT after 11-01, every chart-clock time in forward_register/live logs is +1 h vs ET on the NY clock D7 uses for sessions; worth checking the session clock D7 applies.)
5. **Tags:** all three would be tagged **rechase** (T1 chase_k 2.31, T2 chase_k 2.31, T3 third P7 trade of the session). WB_X_FR_F3 therefore runs its fast line 30/10x/w5/p2 and, in the engine, cuts them at -37.6, -32.3 and -33.3 pts (about $2.7k, $3.0k, $2.7k better than the live stops each, $8.4k in total). But F3's cut only exists if the live cut fires at all.

## 1. Trades as reconstructed (6 lots, $20 per point, fee $4.84 per contract)
Live exit fills as given in the order (StopJoin); unrealised from the given average entry; mid = 1-s top-of-book mid of the NQ mbp-10 (state-base row, 1-s clock; row s decides at the end of the second and exits at the next row's mid -/+ 0.80 pt adverse).

| # | trade (chart CDT) | UTC | entry avg | live stop fill | live pts | live $ |
|---|---|---|---|---|---|---|
| 1 | SHORT 19:11 | 00:11Z, StopJoin 00:17:15Z | 28188.42 | 28248.75 | -60.33 | -7,269 |
| 2 | SHORT 19:58 | 00:58Z, StopJoin 01:28:24Z | 28211.04 | 28268.25 | -57.21 | -6,894 |
| 3 | LONG 21:31 | 02:31Z, StopJoin 02:45:21Z | 28337.50 | 28281.75 | -55.75 | -6,719 |

Time from first -40 to the stop: T1 00:16:35 -> 00:17:15 (40 s), T2 01:26:18 -> 01:28:24 (126 s), T3 02:43:20 -> 02:45:21 (121 s).

## 2. Did the engine cut fire? (question 1)
Engine = the state-base cut kernel of the exact engine (code/th_state_s2ab/s2_kern.fire_state on the 1-s state rows built from the same raw file with code/th_state), live panel line P7 40/5x/w5/p3. NOT a full exact-engine run (the engine would also need its own signal/entry for these trades; the entries are taken from live).

| trade | engine decision (UTC) | exit mid (UTC) | exit pts after 0.80 | $ | live stop $ | engine minus live |
|---|---|---|---|---|---|---|
| 1 | 00:16:37 | 00:16:38 | -46.4 | -5,595 | -7,269 | +1,674 |
| 2 | 01:27:29 | 01:27:30 | -43.1 | -5,205 | -6,894 | +1,689 |
| 3 | 02:43:24 | 02:43:25 | -43.2 | -5,210 | -6,719 | +1,509 |
Replica (literal L2 port, per-print snapshot rows, pulled = own-side cancelled size net of trades in the last 5 s summed over snapshot rows, MedLevel = EWMA 0.001 of the top-5 bid+ask mean level size, evaluated at the first print of each second, loss rule u<=-40, pulled/MedLevel>=5, secs_ext<=5, 3 consecutive qualifying seconds): fires 00:16:40 (-46.6 pts print), 01:27:29 (-42.0), 02:43:24 (-44.5); same with strict "new low only" adverse-extreme timing.

## 3. pulled_mult series from -40 to the stop (question 2)
Every 4th second (plus the fire and the stop second). state-base ratio5 = engine definition (own-side cancelled size in the 5 s window per second row, net of trades per price, over the 1-s row MedLevel); replica = literal per-print definition. They differ by about 2x in pulled contracts (replica counts every print-snapshot row, the state base counts per second) and both are far above 5. "ext age" = seconds since the last adverse extreme (ties count) = the newMae clock (must be <= 5).
Condition counts: replica evaluations with u<=-40 and pulled_mult>=5: 35/35, 54/55, 30/36 (T1, T2, T3); with the newMae test as well: 22, 37, 16 evaluations.

#### Trade 1 SHORT 19:11 CT (00:11Z): entry 28188.42 stop-fill 28248.75; engine decision 00:16:37

| UTC | chart(CDT) | unreal pts | pct of 60 | state-base ratio5 (pulled/MedLevel) | secs since adverse ext | replica pulled5 (contracts) | replica MedLevel | replica pulled_mult | engine/replica cut condition (arm40, mult5, ext<=5) |
|---|---|---|---|---|---|---|---|---|---|
| 00:16:35 | 19:16:35 | -40.2 | -0.67 | 32.2 | 0 | 118 | 2.05 | 57.6 | ok |
| 00:16:37 | 19:16:37 | -40.2 | -0.67 | 18.0 | 1 | 82 | 2.04 | 40.2 | ok |
| 00:16:41 | 19:16:41 | -45.6 | -0.76 | 15.3 | 2 | 72 | 2.03 | 35.4 | ok |
| 00:16:45 | 19:16:45 | -40.3 | -0.67 | 5.5 | 6 | n/a (no print) | |  | ext age>5 |
| 00:16:49 | 19:16:49 | -41.5 | -0.69 | 13.1 | 10 | 31 | 2.02 | 15.3 | ext age>5 |
| 00:16:53 | 19:16:53 | -45.2 | -0.75 | 19.7 | 14 | 65 | 2.02 | 32.3 | ext age>5 |
| 00:16:57 | 19:16:57 | -48.0 | -0.80 | 30.7 | 0 | n/a (no print) | |  | ok |
| 00:17:01 | 19:17:01 | -53.7 | -0.90 | 21.9 | 0 | 83 | 2.01 | 41.4 | ok |
| 00:17:05 | 19:17:05 | -53.7 | -0.90 | 18.6 | 0 | 74 | 2.00 | 37.0 | ok |
| 00:17:09 | 19:17:09 | -57.3 | -0.96 | 14.2 | 2 | 39 | 1.99 | 19.6 | ok |
| 00:17:13 | 19:17:13 | -56.5 | -0.94 | 13.1 | 6 | 14 | 1.99 | 7.0 | ext age>5 |
| 00:17:15 | 19:17:15 | -59.6 | -0.99 | 14.8 | 0 | 31 | 1.99 | 15.6 | ok |

#### Trade 2 SHORT 19:58 CT (00:58Z): entry 28211.04 stop-fill 28268.25; engine decision 01:27:29

| UTC | chart(CDT) | unreal pts | pct of 60 | state-base ratio5 (pulled/MedLevel) | secs since adverse ext | replica pulled5 (contracts) | replica MedLevel | replica pulled_mult | engine/replica cut condition (arm40, mult5, ext<=5) |
|---|---|---|---|---|---|---|---|---|---|
| 01:26:18 | 20:26:18 | -40.5 | -0.67 | 25.2 | 0 | 79 | 1.98 | 39.8 | ok |
| 01:27:05 | 20:27:05 | -40.7 | -0.68 | 13.3 | 46 | 13 | 1.98 | 6.6 | ext age>5 |
| 01:27:26 | 20:27:26 | -40.6 | -0.68 | 10.6 | 67 | 32 | 1.98 | 16.1 | ext age>5 |
| 01:27:29 | 20:27:29 | -42.6 | -0.71 | 13.3 | 0 | 35 | 1.99 | 17.6 | ok |
| 01:27:33 | 20:27:33 | -43.3 | -0.72 | 13.3 | 0 | 34 | 1.99 | 17.1 | ok |
| 01:27:37 | 20:27:37 | -45.6 | -0.76 | 18.6 | 0 | 50 | 1.99 | 25.1 | ok |
| 01:27:41 | 20:27:41 | -44.7 | -0.75 | 15.3 | 1 | 37 | 2.07 | 17.9 | ok |
| 01:27:45 | 20:27:45 | -47.0 | -0.78 | 14.7 | 0 | 29 | 2.09 | 13.9 | ok |
| 01:27:49 | 20:27:49 | -44.0 | -0.73 | 9.4 | 3 | 87 | 2.25 | 38.7 | ok |
| 01:27:53 | 20:27:53 | -40.5 | -0.67 | 5.2 | 7 | 64 | 2.24 | 28.5 | ext age>5 |
| 01:27:58 | 20:27:58 | -41.0 | -0.68 | 11.5 | 12 | 29 | 2.24 | 13.0 | ext age>5 |
| 01:28:02 | 20:28:02 | -42.5 | -0.71 | 10.4 | 16 | n/a (no print) | |  | ext age>5 |
| 01:28:06 | 20:28:06 | -47.2 | -0.79 | 22.4 | 0 | 40 | 2.23 | 17.9 | ok |
| 01:28:10 | 20:28:10 | -46.7 | -0.78 | 17.7 | 4 | 54 | 2.23 | 24.2 | ok |
| 01:28:14 | 20:28:14 | -50.0 | -0.83 | 14.1 | 0 | 70 | 2.23 | 31.4 | ok |
| 01:28:18 | 20:28:18 | -51.3 | -0.86 | 13.0 | 0 | n/a (no print) | |  | ok |
| 01:28:22 | 20:28:22 | -56.0 | -0.93 | 6.8 | 0 | 64 | 2.25 | 28.4 | ok |
| 01:28:24 | 20:28:24 | -57.6 | -0.96 | 11.5 | 1 | 109 | 2.25 | 48.5 | ok |

#### Trade 3 LONG 21:31 CT (02:31Z): entry 28337.50 stop-fill 28281.75; engine decision 02:43:24

| UTC | chart(CDT) | unreal pts | pct of 60 | state-base ratio5 (pulled/MedLevel) | secs since adverse ext | replica pulled5 (contracts) | replica MedLevel | replica pulled_mult | engine/replica cut condition (arm40, mult5, ext<=5) |
|---|---|---|---|---|---|---|---|---|---|
| 02:43:20 | 21:43:20 | -40.6 | -0.68 | 20.0 | 0 | 121 | 2.03 | 59.7 | ok |
| 02:43:24 | 21:43:24 | -44.8 | -0.75 | 16.5 | 1 | 89 | 2.02 | 44.1 | ok |
| 02:43:35 | 21:43:35 | -40.5 | -0.68 | 18.0 | 12 | 60 | 2.01 | 29.9 | ext age>5 |
| 02:43:39 | 21:43:39 | -41.5 | -0.69 | 15.5 | 16 | 39 | 2.00 | 19.5 | ext age>5 |
| 02:44:02 | 21:44:02 | -40.1 | -0.67 | 15.6 | 39 | 26 | 2.00 | 13.0 | ext age>5 |
| 02:44:07 | 21:44:07 | -40.4 | -0.67 | 7.0 | 44 | 5 | 2.00 | 2.5 | ext age>5 |
| 02:44:21 | 21:44:21 | -40.0 | -0.67 | 7.0 | 58 | n/a (no print) | |  | ext age>5 |
| 02:44:26 | 21:44:26 | -41.0 | -0.68 | 8.0 | 63 | 18 | 2.02 | 8.9 | ext age>5 |
| 02:44:30 | 21:44:30 | -40.5 | -0.68 | 7.5 | 67 | 16 | 2.02 | 7.9 | ext age>5 |
| 02:44:37 | 21:44:37 | -40.4 | -0.67 | 7.5 | 74 | n/a (no print) | |  | ext age>5 |
| 02:44:42 | 21:44:42 | -40.5 | -0.68 | 4.0 | 79 | n/a (no print) | |  | ratio<5 |
| 02:45:10 | 21:45:10 | -40.2 | -0.67 | 10.6 | 107 | 46 | 2.07 | 22.2 | ext age>5 |
| 02:45:14 | 21:45:14 | -48.8 | -0.81 | 8.6 | 0 | n/a (no print) | |  | ok |
| 02:45:18 | 21:45:18 | -48.9 | -0.81 | 11.1 | 2 | 38 | 2.08 | 18.3 | ok |
| 02:45:21 | 21:45:21 | -53.8 | -0.90 | 13.6 | 0 | 55 | 2.07 | 26.6 | ok |

## 4. Margins: how far would the cut be from not firing? (question 3 start)
Engine state-cut kernel, per trade, parameter pushed until it stops firing (everything else live):
| | T1 | T2 | T3 |
|---|---|---|---|
| largest pulled_mult threshold that still cuts (live 5) | 20 | 20 | 15 |
| = MedLevel inflation needed to silence it | 4.0x | 4.0x | 3.0x |
| largest persistence that still cuts (live 3 s) | 15 s | 20 s | 10 s |
| largest arm that still cuts (live 40 pts) | 56 | 58 | 54 |
| fires without newMae | yes | yes | yes |
| pulled window 2/3/5/10/15 s | all fire | all fire | all fire |
MedLevel on this night is 1.6-3.3 contracts per level (median 2.05; Asia-hours p10-p90 1.7-2.9 on every day 11-02..11-11 as well), i.e. the 5x threshold is about 10 contracts cancelled on one side in 5 s. On a clean NQ book that happens in nearly every adverse second below -40.

## 5. Why did live not cut? (question 3). What is established, what is not
Established (this page): (a) engine and the literal replica cut, 38-117 s before the stop; (b) the cut condition is satisfied with margin 3-4x in MedLevel, 10-20 s in persistence; (c) clean-book MedLevel is about 2 contracts for the whole week 11-02..11-11 (Asia-hours median 1.8-2.6, p10-p90 1.7-2.9), so no day is special; (d) in the frozen week 11-01..05 the same MedLevel/cancel definitions reproduced 92 of 92 live cuts within 2 s of the 30x policy line (T-REPLICA), i.e. the old live loss line agreed with this clean-book arithmetic at least while the old per-print code ran.
Not established (needs live data not on the box): which live gate was closed on 11-11. Candidates ranked by what they would require of the data:
1. **v1.5/v1.5a state-cut path not evaluating.** The cut is a different code path since v1.5 (state mid, win, persist) and misbehaved on 11-08/09 (10 bug exits at -9,868..-24,370 pts, foreign-level mid). v1.5a rejects levels > 5% from the NQ last close; if the state mid / DepthLive / ExitPending / persist counter is then never satisfied (stale last close, mid undefined after the reject, persist counted over evaluations that need a print every second, counter reset by an unrelated condition), the cut is inert for the whole trade. Evidence for: it must be a gate or a >= 4x scale error; the old per-print rule matched live through 11-05. Needed: v1.5a source and forward_register/th_eval.csv rows of 11-11 (unreal, pulled, MedLevel, newMae/secs_ext, DepthLive, decision per evaluation) for these three trades.
2. **MedLevel scale >= 3-4x clean.** A book still polluted with ES/RTY levels (ES level sizes are tens to hundreds of contracts against NQ 2) inflates the top-5 mean by far more than 4x, silencing any mult-5 test while the old 30x line was already less sensitive. The 11-09 finding says v1.5a removes them; whether the MedLevel EWMA (0.001 per print, memory about 1,000 prints, a couple of minutes at night) is fed from the filtered book is not visible. th_eval.csv MedLevel column answers this in one line (expected 1.8-2.6).
3. **Cancelled-size definition.** The two definitions here differ by 2x and both fire; a live definition 4x smaller (for example counting only levels that vanish inside the best, ignoring size reductions, or netting trades twice) would be silent. Same file answers it (pulled column).
4. **Persistence 3 counted in evaluations that need a print each second.** Silences only if prints are sparse; of the seconds spent at -40 or worse 88%, 87% and 77% had a print (41, 60 and 43 such seconds) and persistence up to 10-20 s would still fire. Unlikely alone.
5. **Six lots / StopJoin / ExitPending.** The cut arm has no lot scaling in v1.4; StopJoin starts only at the 60 stop. Not a cause unless v1.5a changed it.
6. **Native 80 catastrophe stop** is behind the 60 worked stop and cannot suppress the cut.
Not a cause: the book was clean in this feed (NQ-only mbp-10), the engine MedLevel is at its usual 2.

## 6. What it means for every P7 cut result so far (question 3 end)
- The engine's P7 StateCut is the P7 stop in practice: 20.8 per week, median -42.3 pts, 51% of P7 trades (LPB_BASE, L6M 2026-05..10, 26 weeks, exact engine trades). Full stops: 0.62 per week (Stop 0.12, StopJoin 0.38, StopJoinFallback 0.12). With the cut off (WB_C_NONE, exact): P7 full stops 15.7 per week, targets 19.3 per week (LPB_BASE 18.8), P7 net about +$2.3k per week better than with the cut in L6M (W-B: stack maxDD cut +19.1%, mean +2,180 per week; worse in HOLD -19.1%).
- If the live cut stays inert, the live book is the WB_C_NONE world, whose P7 drawdown, full stops, give-backs and same-side losing runs are those of 15.7 full stops per week. Our scorecard (24.5 full stops per week stack, P7 only 0.4-0.6) describes a live system that is not running.
- Voided until the live cut is shown firing (the cut parameter is irrelevant if it never evaluates): WG_E1/WL_E1 interaction with the cut, WB_X_FR_F3 (cut lines only), WM_X_LOTS (cut by lots), every JN04RM/JN05W stack that contains the P7 cut, S6/C22 and FLAT45K results that were measured with the P7 cut on (FLAT45K is K7, not affected), the 0.4 full stops per week claim and the behavioural scorecard line (a) for P7. The no-cut worlds (WB_C_NONE and sets built on it) are the live-relevant ones.
- Not voided: results that do not depend on the P7 cut (entry gates measured against a no-cut reference, K7/U7/M7/A7 lines that have their own live evidence - but check the same gate for them: if v1.5a broke the state cut for P7 it broke it for all books; the 11-08/09 bug exits were H7 and M7).
- The engine's fill assumption (0.80 adverse on market exits vs 1.19-1.20 live) is a separate, smaller correction (0.4 pt per exit, about $48 per six lots).

## 7. Tags and WB_X_FR_F3 for the three trades (question 4)
P7_CONTEXT_DEFS: fresh = n_sess <= 2, not chasing (chase_k <= 1.0), gap >= 30 min from the last P7 exit; chase_k = (signal price - session open) x side / ATR5, session open = first 1-min bar open of the Asia session (18:00 ET = 23:00Z): 28306.25; ATR5 = 5-min Wilder ATR(14) at the last completed bar, rebuilt from the prints here. Assumption: these three were the only P7 entries of the session (any earlier P7 entry would only push n_sess up; the live P7 file for the night is not on the box).
| trade | ATR5 | chase_k | n_sess | gap | tag |
|---|---|---|---|---|---|
| 1 SHORT 00:11Z | 50.95 | 2.31 | 1 | none | rechase (chasing: price 118 below the session open) |
| 2 SHORT 00:58Z | 41.29 | 2.31 | 2 | 41 min | rechase (chasing) |
| 3 LONG 02:31Z | 36.64 | 0.85 | 3 | 63 min | rechase (third entry) |
WB_X_FR_F3 lines in the engine state kernel (exit = next-row mid -0.80, 6 lots):
| trade | live panel 40/5x/w5/p3 | F3 fast 30/10x/w5/p2 (this tag) | F3 fresh 45/5x/w5/p10 (not applicable) |
|---|---|---|---|
| 1 | 00:16:37, -46.4 pts, $-5,595 | **00:16:33, -37.6 pts, $-4,545** | 00:17:06, -58.5, $-7,050 |
| 2 | 01:27:29, -43.1 pts, $-5,205 | **01:18:18, -32.3 pts, $-3,900** | 01:28:19, -51.3, $-6,180 |
| 3 | 02:43:24, -43.2 pts, $-5,210 | **02:43:13, -33.3 pts, $-4,025** | 02:45:22, -52.2, $-6,290 |
Live stops: -$7,269, -$6,894, -$6,719. So F3's fast line would have cut all three, earlier, and saved $2.7k, $3.0k, $2.7k each. All of this holds only if the live cut can fire at all (section 5/6). Note the 8%-fresh warning from V19_SPEC_F3 (June 2026): here 3 of 3 are rechase, consistent with F3 acting as the fast line on nearly every trade.

## 8. Needed from live to close the diagnosis
forward_register/th_eval.csv for 2026-11-11 (all TH-L2/state-cut evaluations of P7 between 00:11Z and 02:46Z), the v1.5a source (state-cut path, MedLevel feed, last-close reject), the DS7 startup/NT8 log of that night (which version and policy file were loaded; was the state cut enabled for P7), the live P7 trade file for 11-11 (all entries, to confirm n_sess), and the chart-clock setting (CDT stamps).
