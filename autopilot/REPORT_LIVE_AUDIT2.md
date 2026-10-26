# REPORT_LIVE_AUDIT2: why live and engine entries differ, ManageLoss port, live parameters

Sources: outputs/h2/DualStrat.cs (the one authorised file; no credentials were present or copied), outputs/h2/StratTrades_DualStrat_<acct>.csv (204 usable rows; ST+HM 197).
Code: code/census/night_ins/ap_th_port.py (numba ManageLoss kernel), ap_th_validate.py, ap_th_replay.py (state-consistent replay), ap_live_vs_engine.py (weekly fidelity row), ap_ddmin_audit2.py.

## 1. Answer in four lines
1. The live book is ONE state machine per book that, after a Trade Health (TH) LossExit, resets to flat and takes the very next flip (ResetTrade in OnExecutionUpdate; nothing suppresses re-entry; confirmed in the C#). The TH-off engine never frees the book that early, so its position path, and therefore its entry set, diverges. This is state divergence, not different signals (reverse test: the engine following live exits accepts 120/120 ST and 76/77 HM live entries as raw signals).
2. With the ported ManageLoss and the live TH schedule (ST on throughout; HM on until 2026-10-09 14:12, off afterwards) the replay re-matches 180 of 197 live entries (91.4%, 150 s rule) against 105 of 197 for the TH-off engine. With the per-book day/week rules on, 174 of 197 (88.3%).
3. Exit validation (replay from each live entry fill, live entry price, 60/1.0R bracket): exit TYPE agrees on 95-96% of 195 exits (pass, >= 90%); type AND time within 2 minutes agrees on 81-84% (below 90%). TH rows are therefore labelled PROVISIONAL. The timing miss comes from tick-level information the 1-second rows do not carry (section 3).
4. Gap decomposition (ST+HM, window 2026-10-04 18:00 to the log end 2026-10-16 04:30): TH-off engine without limits $171.2k, live $32.3k. Per-book day/week rules explain $66.0k (47%), unknown chart start times $37.3k (27%), TH loss exits $89.0k (64%), residual -$53.4k (-39%, the live book did better than the replay; section 5).

## 2. What ManageLoss does (verbatim logic) and how it maps to 1-second rows
Cadence: ON TICK. OnMarketData handles only Last ticks. For every Last tick: now = Globals.Now (real time) or tick time (replay); one price sample is stored per >= 100 ms and trimmed to (max window + 5 s) = 35 s; for each book in a trade, AdvExt (adverse extreme) is updated on every tick that is strictly worse than AdvExt (long: px < AdvExt; short: px > AdvExt) with AdvExtTime = now; AdvExt and AdvExtTime are initialised at the entry fill price and fill time. Then, if ThOn, ManageLoss(book, px, now) runs:

| step | C# | value |
|---|---|---|
| guard | return if Triggered or ExitPending | |
| eligibility | worst = EntryPx - AdvExt (long) or AdvExt - EntryPx (short); Eligible latches when worst >= MinPoints | ST 15, HM 10, WT 10 |
| cadence | at most one evaluation per ThEvalFrequencySecs of tick time (LastEval) | 1 s |
| C0 momentum | price at the last sample with T <= now - 30 s; adverse move (pAgo - px for long, px - pAgo for short) >= 4 pts. False if the buffer has no sample that old | window 30 s, 4 pts |
| C1 stall | now - AdvExtTime >= 30 s and recovery (px - AdvExt long, AdvExt - px short) <= 4 pts | 30 s, 4 pts |
| C2 efficiency | over samples in [now - 30 s, now], needs >= 2 samples and the oldest buffered sample <= now - 30 s: abs(last - first) / path < 0.35 (path > 0) | 30 s, 0.35 |
| trigger | count >= min(Required, 3) | ST 3, HM 3, WT 2 |
| exit | RequestBookExit "LossExit": cancel the book's own stop and target, wait >= 400 ms until both are terminal, then one MARKET exit for the book's quantity | |

Mapping (ap_th_port.th_scan, one second at a time, stop checked first as in natural_se): evaluation clock now = end of each 1-second row; price = row close SC; AdvExt from the row low (long) or high (short), AdvExtTime = row start + 0.5 s; the samples are the row closes (rows exist only for seconds with trades, which reproduces the "oldest sample must be <= now - 30 s" rule: a window needs a row in [now - 35 s, now - 30 s]); path option 0 = sum of absolute close-to-close moves, option 1 = also routed through the row low/high in minimum-path order (the tick path is somewhat longer than either). Exit fill = close of the next row (400 ms cancel wait plus market latency); a stop or target touched in that row wins (the OCO race). Stop-market fills at the stop with the engine's gap rule; target fills at the level.

## 3. Validation on the live log
Method: for each of 195 ST/HM live exits (ComboLock rows excluded: external to TH), start the scan at the live entry second with the live entry price and a 60-point stop and 1.0R target, TH settings per book below, HM TH off after 2026-10-09 14:12 (its last LossExit; every later HM exit is a Target or a Stop, 11 of those 14 stops would be LossExits if HM TH were still on).

| path | exit type match | type and time within 2 min |
|---|---|---|
| closes only | 94.9% | 83.6% |
| closes plus in-second extremes | 96.4% | 81.0% (HM 85.5%, ST 78.2%) |

Parameter fit (grid over MinPoints 10..25, Required 2/3, shared window 30/60, momentum 4/6/8, pullback 4/6, efficiency 0.35/0.5): the file values (ST 15/3, HM 10/3, 30 s windows, 4/4/0.35) are the best cell for BOTH books, so the file defaults equal the chart values for TH. Time-of-day dependence of the timing agreement: Asia 72%, London 87%, NY 92% (thin markets make the 1-second close a poor stand-in for the tick path). Median time difference 1 s, 25% exactly 0, 75th percentile +19 s (live later than the replay), 90th +380 s: the replay fires slightly more often than the live (5-6 LossExit predictions vs live Target/Stop in the whole window, worth about $50k of swing at $9.6k per trade).
Label: exit-type criterion passed (95-96%), timing criterion NOT passed (81-84%): all TH rows in the lever B tables are PROVISIONAL; match_rate in the manifest is the 2-minute figure.

Entry re-match under the state-consistent replay (signals with the busy gate, TH per the live schedule, start at each book's first live trade, 150 s rule):
| engine variant | engine trades | live entries re-matched | engine net |
|---|---|---|---|
| TH off, no limits | 179 | 119 (60%) | $133.9k |
| TH off, per-book limits | 118 | 96 (49%) | $67.9k |
| TH live schedule, no limits | 268 | 180 (91.4%) | -$17.7k |
| TH live schedule, per-book limits | 216 | 174 (88.3%) | -$21.1k |
Matched pairs by live exit type give nearly the same dollars (ST Target $292.7k live vs $291.3k engine; ST LossExit -$280.6k vs -$263.3k; HM Stop -$115.6k vs -$116.6k): the port is right at pair level. The 17 live entries that do not re-match are all consequences of an engine TH exit that fired at a different time than the live one (the engine was still in, or already out of, a trade). They net +$44k live (9 Targets, 6 LossExits, 2 Stops).
Week 2026-10-12 onward with the actual live config (ST TH on, HM off), via ap_live_vs_engine.py: entries matched 92%, exit type 95.6%, exit time within 2 min 83.3%.

## 4. The remaining rules that shape the entry set (from the C#)
- Entries: Calculate.OnBarClose, 1-minute chart; a flip is evaluated on bar close and a market order goes in at the next bar. An entry needs: book enabled, flat (InTrade false), no ExitPending, no EntryOrder pending, not DayHalt/WeekHalt, not time-blocked. A flip that arrives while the book is in a trade is DROPPED (log text "flip SKIPPED"); there is no deferral except the FlipOther mode (PendingSide, 3 bars), which is not the default.
- OppositeEntry = AsIs: books are virtual and independent; a book enters regardless of the other book. The broker nets. So the live book-level entry set does NOT depend on lot netting. The "engine skipped although flat" entries in AUDIT2 draft (36) are an engine-account artefact (the netted entry has no row in the netted engine); the pre-netting streams in lever C avoid it.
- After a LossExit: ResetTrade, flat, next flip is taken. No cool-down.
- Time guards (ET of the chart): Asia 15:00-17:00 and NY 09:00-10:00 block entries (guards are bar-time minutes), own flatten at 16:55 ET (SessionFlat, blocks until 18:00). Same windows as the engine's BLOCKED/BLK arrays. All weekdays on, Sunday session on.
- Per-book realized limits (CheckLimits, once per bar, live only): day profit 48,000 (5R), day loss 19,200 (2R), week loss 57,600 (6R); on a hit the book flattens ("DayHalt"/"WeekHalt") and takes no entries until the next session (week: Monday). Counters persist in a state file across restarts. WT: 31,500 / 12,600 / 37,800.
- Combined lock (CheckComboLock, every >= 2 s on ticks, realized plus open across the books): profit cap 5R, give-back arm 2R, give-back 67%, ComboLockFromHHmm 0, loss floor 0, week floor 0, max trades per session 0 (off). R = StQty x StStopPts x 20 = $9,600 (taken from the ST book). Resets at the first bar of each session. On a hit: all books flatten ("ComboLock"), DayHalt, no re-entry until the next session. Active since 2026-10-15 on the chart; first firing 2026-10-16 04:30:11.
- HM VWAP: reset when the fixed UTC-4 calendar date changes (HmVwapAnchor FixedMidnightUtc4), the research clock.
- Warm-up: TradeInHistorical false, so the chart enters real time FLAT with BarsRequiredToTrade 250; a restart loses any open virtual position and restarts with no state. The chart start/restart times are UNKNOWN (user left the template placeholder); each book's effective start is inferred from the first live trade per day (section 6) and is a source of uncertainty, not a measured quantity.

## 5. Gap decomposition (ST+HM, 2026-10-04 18:00 to 2026-10-16 04:30, replay engine)
| step | net | change | share of the gap from "no limits" |
|---|---|---|---|
| TH-off engine, no limits, from 10-04 18:00 | $171.2k | | |
| + per-book day/week rules (live) | $105.1k | -$66.0k | 47% |
| + books start at their first live trade (start time effect) | $67.9k | -$37.3k | 27% |
| + TH on with the live schedule | -$21.1k | -$89.0k | 64% |
| live actual | $32.3k | +$53.4k | -38% (residual) |
Notes: (i) the earlier $247k TH-off figure covered the full 10 sessions through 10-16 17:00 and the as-tested account rules; the replay window stops at the log end 10-16 04:30 so levels differ, the ordering of causes is the point. (ii) The residual is positive because the live TH exited later than the 1-second replay on about 5 trades that then ended in Targets, plus the 17 live-only entries that happened to be winners; it is sampling noise of tick-level path timing, not a missed rule. (iii) Live-only vs engine-only entries: live-only 17 (+$44k), engine-only 88 (-$10k) in the TH-live replay. (iv) If ST TH is turned off (decision from 2026-10-20) the live book follows the TH-off engine path again; section 7 gives the fidelity script.
Per-cause counts of the earlier TH-off mismatch (engine-only 96): per-book day rule 32, live busy 18 (state), before the book first live trade 12, after the log end 12, unexplained 19, lag 3. Live-only (92): engine still in a trade the live closed by a TH LossExit 44, signal exists and engine flat 36 (engine-side netting artefact), engine in a trade live never took 10, other 1, no engine signal 1. Lag of matched entries: median 0 s, min -120 s, max +6 s (entries are at the bar open +0..6 s).

## 6. Each book's first and last live trade per label day
| book | day | first | last | n |
|---|---|---|---|---|
| ST | 10-06 | 10-05 20:08 | 10-06 14:21 | 8 |
| ST | 10-07 | 10-06 18:27 | 10-07 14:05 | 17 |
| ST | 10-08 | 10-07 19:03 | 10-08 08:16 | 17 |
| ST | 10-09 | 10-08 20:10 | 10-08 21:33 | 4 |
| ST | 10-12 | 10-11 19:02 | 10-11 21:01 | 3 |
| ST | 10-13 | 10-12 18:01 | 10-13 14:55 | 21 |
| ST | 10-14 | 10-13 18:22 | 10-14 14:32 | 20 |
| ST | 10-15 | 10-14 18:18 | 10-15 10:24 | 20 |
| ST | 10-16 | 10-15 18:01 | 10-16 04:27 | 10 |
| HM | 10-05 | 10-04 19:45 | 10-04 19:45 | 1 |
| HM | 10-06 | 10-05 20:35 | 10-06 14:06 | 8 |
| HM | 10-07 | 10-06 20:11 | 10-07 14:32 | 13 |
| HM | 10-08 | 10-07 18:33 | 10-08 13:26 | 14 |
| HM | 10-09 | 10-08 19:26 | 10-09 14:12 | 11 |
| HM | 10-12 | 10-11 22:22 | 10-12 12:47 | 5 |
| HM | 10-13 | 10-12 18:24 | 10-13 02:04 | 6 |
| HM | 10-14 | 10-13 18:23 | 10-14 12:06 | 8 |
| HM | 10-15 | 10-14 18:08 | 10-15 04:50 | 8 |
| HM | 10-16 | 10-15 18:56 | 10-16 04:30 | 3 |
Gaps: HM did not trade at all between 10-04 19:45 and 10-05 20:35 (the 10-05 session start is the unknown restart), ST first trade 10-05 20:08. ST stops after 10-08 21:33 and 10-11 21:01 may reflect the ST day-loss rule (-2R) halting the book (the live sessions 10-09 and 10-12 have only 4 and 3 ST trades); not verified trade by trade. No chart start time is stated anywhere; treat the 10-04/10-05 start as unknown.

## 7. Live parameter values (DualStrat.cs SetDefaults; TH values confirmed by the fit in section 3; chart-saved values were not read)
| field | ST | HM | WT |
|---|---|---|---|
| enabled (default) | true | true | false (traded 10-04 evening only, so the chart enabled it that evening) |
| quantity | 8 | 8 | 7 default (the log shows fewer) |
| engine | Supertrend ATR 120 (RMA), mult 2.0, Close source, EMA 200 filter | HMA 20/55 on (Close - session VWAP), slow-HMA slope confirm, EMA 200 filter, VWAP reset on the UTC-4 date | Wilder ATR ratchet, ATR 20 mult 2.0, EMA 100 filter |
| stop / target | 60 pts / 1.0R = 60 pts | 60 / 1.0R | 45 / 0.75R |
| ThOn (default in file) | false in file, TRUE live (77 LossExits) | false in file, TRUE live until 10-09 14:12 and FALSE after | true |
| MinPoints / Required | 15 / 3 | 10 / 3 | 10 / 2 |
| shared windows | momentum 30 s / 4 pts; stall 30 s / pullback 4 pts; efficiency 30 s / 0.35; evaluation every 1 s | same | same |
| day profit / day loss / week loss | 48,000 / 19,200 / 57,600 | same | 31,500 / 12,600 / 37,800 |
Combined lock: ComboProfitCapR 5.0, ComboGiveBackArmR 2.0, ComboGiveBackPct 67, ComboLockFromHHmm 0, ComboLossFloorR 0, ComboWeekFloorR 0, MaxTradesPerSession 0. Other: OppositeEntry AsIs, UseEasternDstAuto, GuardAsia 15:00-17:00, GuardNy 09:00-10:00, GuardLondon off, FlattenAtHHmm 16:55, BarsRequiredToTrade 250, ExitOnSessionClose 30 s.
DDMIN grid centres: ST (60, 1.0R, TH 15/3), HM (60, 1.0R, TH 10/3), WT (45, 0.75R, TH 10/2) with the TH-off base as the reference (user decision: ST TH off live from 2026-10-20). Note WT-10 in the research stack is the 10-minute Wilder x3 trail (60/60), different from the chart's WT (1-minute ATR 20 x 2.0, stop 45, 0.75R): the DDMIN WT geometry grid should include 45/0.75R.

## 8. Weekly live-vs-engine reconciliation (TH off from 2026-10-20)
Script: code/census/night_ins/ap_live_vs_engine.py <trade log csv> [from date] [off|st|on]. Metrics: entries matched (live entry with an engine entry of the same book and side within 150 s), exit type match and exit time within 120 s on matched pairs (ComboLock/DayHalt/WeekHalt excluded), live net vs engine net per label day (engine has the per-book day/week rules, not the combined lock) overall and on matched pairs. It writes outputs/autopilot/live_vs_engine_<week>.csv and appends LIVE_VS_ENGINE.csv. Pass bar suggestion: entries >= 90%, type >= 90%, matched P&L within 10%.

## 9. TH-on base
The coordinator decision makes TH-off the forward live base, so no TH-on full-span base is rebuilt: DDMIN/SMOOTH/DAYRULES/PORTFOLIO stay centred on the TH-off base (1.46/2.83/2.48/1.90). TH is scored as lever B only, PROVISIONAL. Caveat for lever B: the replay shows the TH exits cost about $89k in this 10-session window; a TH-on gain in the engine would need the 2-minute timing validation to improve before it is trusted.
