# JOIN_RECON - live stop-join vs replay, per attempt (BK2, 2026-10-24; calibration, not a new test, no trials appended)

> **UPDATE 2026-10-25: sections 0-4 were written before the 10-19..10-23 L2 tape was on disk. Section 5 (end of file) replays every attempt with that tape, corrects the 1-hour clock, and answers the 0.47 vs 0.78 question; where they differ, section 5 governs.**

Research only. Sources: live file `data/live/StratTrades_DualStrat2_<acct>.csv` (account id withheld), NT8 order trace `data/live/nt8log_trace.20261021..23*.txt` (order callbacks, ms) and `nt8log_latest.txt`; replay = struct48 T4 stop-join machinery (`t4_replay.run_arm` / `exit_arms`, exec_engine_l2 on raw mbp-10, prop queue, 5 ms) re-run unedited on the only live-adjacent week with L2 on disk, **W42 = 2026-10-12..10-16** (127 Set A rows, 55 stop exits; files `raw/NQ/ext/*/glbx-mdp3-20261012..16`; continuous symbol NQ.v.0 -> instrument 261401 (NQZ6), verified from the file symbology). Live days 10-20..10-23 have NO L2 on disk; nothing is fabricated for them: the per-attempt rows below are live-only, and the replay column is the matched-week and long-run distribution, not a per-trade reconstruction. Code: `autopilot/join_recon/` (bk2_parse.py, bk2_live.py, bk2_create.py, bk2_table.py, bk2_replay.py, bk2_replay_lat.py, bk2_report.py); outputs `l2vast/struct48/out/BK2/` (R/X/F/XLAT_W42.parquet), `autopilot/join_recon/join_attempts.csv`.

## 0. Headline

1. The live-vs-replay exit-quality gap is a **fill-rate effect, not an exit-quality effect.** Replay conditional on outcome (all 6,604 stop exits Feb-2023..Oct-2026, XJ3 queue): join filled **+0.52 pt** vs the stop level, join failed -> market fallback **-4.26 pt** (trade-through rule: +0.53 / -3.78). Live: filled **+0.52** (n=8), fallback **-4.25** (n=9). Same numbers. The headline -2.01 (live) vs -0.52 (replay) is just 8/17 vs 78% fills: 0.47 x 0.52 + 0.53 x (-4.26) = -2.0.
2. The fill rate itself: live 8/17 = 0.47 [0.23, 0.72]. Replay fill rate is strongly time-of-day dependent: **0.83-0.85 in 08:00-18:00 ET, 0.57-0.68 in 18:00-08:00 ET** (XJ3 queue 0.60-0.68; trade-through 0.57-0.64). 14 of the 17 live attempts happened 18:00-08:00 ET (9 in 18-22, 4 in 22-02, 1 in 02-08; 1 in 08-12, 2 in 12-18); reweighting the replay rates to the live time-of-day mix gives expected **0.69 (queue) / 0.65 (trade-through)**, so P(<= 8 of 17) = **0.05 / 0.09** (Poisson-binomial), not the 0.005 that the 0.78 headline implies. The matched replay week W42 itself fills 0.64 (queue) / 0.62 (trade-through) on 55 exits; P(<= 8/17 | 0.62) = 0.15. The live rate is low but not outside what the replay predicts for this exit mix. The gap is concentrated in the 18:00-22:00 ET block (live 3/9 vs replay 0.64-0.68, P ~ 0.04-0.06, exploratory, post hoc).
3. **Latency is NOT the cause.** Live create->Working is 85-258 ms (median 111; replay assumes 5 ms). Replaying W42 with 25/50/100/150/250/500 ms of latency *raises* the join fill rate (queue 0.64 -> 0.73/0.76/0.75/0.78/0.76/0.80) and does not hurt exit price (-0.77 -> -0.40 pt at 150 ms): a late order joins after the spike, in the bounce. (A feed lag larger than ~0.5 s, or the interaction with the stop-run, cannot be excluded without L2 for the live days.)
4. **Mechanism of the failures: price runs away.** All 5 traced non-fills went to market after the 3.0 s timer at a price **2.8-10.0 pts (mean 5.5) beyond the join limit in the adverse direction**; in the matched replay week 14 of 17 (XJ3) / 14 of 21 (XJ3t) failures are "tape never returned to our price within 3 s" (touch drifted 2-3 pts away; mean adverse 3-s extension 4.0-4.3 pts vs 2.2 for fills), the rest are queue-starved (traded at our price, not enough). No evidence of a wrong-side or mis-priced join (section 3).
5. **Data-integrity finding (live CSV):** one ST trade is missing from `StratTrades_DualStrat2` - entry 14 lots Buy 2026-10-21 04:00:00-04:00:31 (avg 29905.73), flattened 04:34:01.6 by a market `Close` at 29842.52 (63.2 pts ~ -$17.7k at 14 lots) after the strategy created a stop-join at 04:34:01.570 and 31 ms later ran CancelAllOrders + Position.Close (the join was cancelled in 12 ms and never rested). It is a 19th stop-level event (join bypassed); it is not in the CSV, so W43 live net and trade count in FORWARD_REGISTER (39 Set A trades, -184,580) understate by this trade; the join rate with the bypass counted as a failure is 8/18 = 0.44.
6. **Clock finding:** CSV and trace times are **Eastern (UTC-4 in October)**, not Central: the embedded UTC stamps in the trace JSON (e.g. `2026-10-21T07:26:16.512Z`) coincide with trace/CSV `03:26:16`. `LIVE_RECON.md` (and `pairP2/live_vs_replay_p9.py`, default tz America/Chicago) shift all times +1 h. Anything matched to the tape (entry slip vs mid, join-trigger lookups, time-of-day buckets) must use CSV time + 4 h = UTC. The ET column in LIVE_RECON.md is one hour late; the summary numbers there (slips) are unaffected.

## 1. Every live join attempt (18 CSV stop exits: 17 join attempts + 1 broker-rejected; plus the bypassed 19th)

Times ET (CSV clock). "join vs nominal" = side-adjusted (join limit - nominal stop), + = better than the stop level. "fallback vs join" negative = the market ran away against us after the limit was placed. Rows 1-7 are 2026-10-20: the retained NT8 trace starts 10-21 00:00, so no order lifecycle exists for them (CSV exit names only). Nominal stop = entry avg -/+ 60 pts.

| # | exit ET | book | pos | join created->working ms | join limit | nominal stop | join vs nominal (pts, + = better) | outcome / mechanism | first fill s | worked s | fallback avg px | fallback vs join (pts, - = ran away) | live exit vs nominal (pts) | trace |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 10-20 14:33:10 | HM | long |  |  | 29719.63 |  | filled (CSV only; no order trace) |  |  |  |  | +2.12 | N |
| 2 | 10-20 14:42:57 | ST | long |  |  | 29687.30 |  | failed -> market (CSV only; no order trace) |  |  |  |  | -7.30 | N |
| 3 | 10-20 18:42:29 | ST | long |  |  | 29911.14 |  | failed -> market (CSV only; no order trace) |  |  |  |  | -0.89 | N |
| 4 | 10-20 21:00:11 | ST | long |  |  | 29906.50 |  | filled (CSV only; no order trace) |  |  |  |  | +0.75 | N |
| 5 | 10-20 21:00:59 | HM | long |  |  | 29890.48 |  | failed -> market (CSV only; no order trace) |  |  |  |  | -2.23 | N |
| 6 | 10-20 23:55:09 | HM | long |  |  | 29922.61 |  | rejected (position-limit per user; ST fallback 3 s later) |  |  |  |  | -2.11 | N |
| 7 | 10-20 23:55:12 | ST | long |  |  | 29923.98 |  | failed -> market (CSV only; no order trace) |  |  |  |  | -0.98 | N |
| 8 | 10-21 03:26:17 | ST | short | 118 | 29901.25 | 29901.23 | -0.02 | filled <1 s (tape traded back to the limit) | 0.01 | 0.83 |  |  | -0.02 | Y |
| 9 | 10-21 09:43:21 | ST | long | 258 | 29802.50 | 29802.14 | +0.36 | partial 1/14 at 2.7 s, rest market (13 lots; a stray callback 8 h later shows filled=2, ignored) | 2.74 | 2.78 | 29799.35 | -3.15 | -3.39 | Y |
| 10 | 10-21 20:05:31 | HM | short | 111 | 29825.00 | 29825.86 | +0.86 | no fill; tape ran away 6.1 pts beyond the limit in 3 s |  | 3.19 | 29831.07 | -6.07 | -5.89 | Y |
| 11 | 10-22 19:02:44 | HM | long | 141 | 29092.75 | 29091.32 | +1.43 | no fill; tape ran away 2.8 pts beyond the limit in 3 s |  | 3.22 | 29089.93 | -2.82 | -1.82 | Y |
| 12 | 10-22 20:14:49 | ST | short | 130 | 29122.25 | 29123.13 | +0.88 | no fill; tape ran away 9.9 pts beyond the limit in 3 s |  | 3.04 | 29132.20 | -9.95 | -10.12 | Y |
| 13 | 10-22 20:47:08 | ST | short | 85 | 29160.00 | 29161.46 | +1.46 | filled <1 s (tape traded back to the limit) | 0.79 | 0.99 |  |  | +1.46 | Y |
| 14 | 10-22 21:53:34 | HM | long | 109 | 29142.00 | 29140.86 | +1.14 | no fill; tape ran away 5.8 pts beyond the limit in 3 s |  | 3.05 | 29136.25 | -5.75 | -5.61 | Y |
| 15 | 10-22 21:56:14 | ST | long | 118 | 29118.75 | 29119.32 | -0.57 | filled late (2.5 s, queue) | 2.54 | 2.54 |  |  | -0.57 | Y |
| 16 | 10-23 01:26:40 | HM | long | 94 | 29113.50 | 29113.29 | +0.21 | filled <1 s (tape traded back to the limit) | 0.69 | 0.80 |  |  | +0.21 | Y |
| 17 | 10-23 01:28:36 | ST | long | 99 | 29107.00 | 29107.80 | -0.80 | filled <1 s (tape traded back to the limit) | 0.33 | 0.56 |  |  | -0.80 | Y |
| 18 | 10-23 01:42:00 | HM | short | 109 | 29172.50 | 29173.50 | +1.00 | filled <1 s (tape traded back to the limit) | 0.86 | 2.27 |  |  | +1.00 | Y |
| 19 | 10-21 04:34:01 | ST | long | (join cancelled 12 ms after creation) | 29845.00 | 29845.75 | -0.75 | bypassed: CancelAllOrders + Position.Close 31 ms after the join was created -> market Sell 14 @ 29842.52 | | | 29842.52 | | -3.23 | Y (not in CSV) |

Totals (17 attempts, rejected excluded): joined 8, fell back 9; rejected 1 (row 6). Traced attempts (rows 8-18, n=11): joined 6 (first fill 0.01, 0.33, 0.69, 0.79, 0.86, 2.54 s; median 0.74 s after Working), partial 1 (1/14 lots at 2.74 s), none 4. Timer behaviour is as specified (worked 3.04-3.22 s before the cancel -> market). Create->Working latency 85-258 ms (median 111; filled 104, failed 130).

## 2. Matched-week replay (W42) and long-run replay, same definitions

| quantity | live (W43, n) | replay W42 (queue / trade-through) | replay all history Feb-2023..Oct-09-2026 (queue / trade-through) | replay 2026 only |
|---|---|---|---|---|
| join full-fill rate | 8/17 = 0.47 [0.23, 0.72] | 0.636 / 0.618 (n=55) | 0.776 / 0.747 (n=6,604) | 0.756 / 0.728 |
| expected under the live time-of-day mix | | | 0.688 / 0.654 | 0.70 / 0.67 |
| exit vs stop, join filled | +0.52 (8) | +0.64 (35) / +0.63 (34) | +0.52 / +0.53 | +0.59 / +0.62 |
| exit vs stop, join failed -> market | -4.25 (9) | -3.44 (17) / -3.28 (21) | -4.26 / -3.78 | -4.17 / -3.90 |
| exit vs stop, all stop exits | -2.01 (18) | -0.77 / -0.86 | -0.46 / -0.56 | -0.52 / -0.61 |
| plain market exit (EM arm) | | -1.36 | -1.45 | |
| median first fill after trigger | 0.74 s after Working (~0.85 s after create) | 0.15 s / 0.21 s | | |

By ET hour block, replay full-fill rate (XJ3 queue / XJ3t, all history): 18-22: 0.680 / 0.643 (n=585); 22-02: 0.597 / 0.567 (457); 02-08: 0.669 / 0.631 (1,350); 08-12: 0.847 / 0.826 (2,676); 12-18: 0.835 / 0.805 (1,536). Live by block: 18-22 3/9, 22-02 3/4, 02-08 1/1, 08-12 0/1, 12-18 1/2. Weekly replay fill rate (weeks with >= 20 exits, 140 weeks): mean 0.776, SD 0.082, minimum 0.545 (XJ3t: 0.747 / 0.086 / 0.512): week-to-week variation is large; a 17-attempt sample has binomial SD 0.12 on top.

Matched-week replay tape features at the join (W42, XJ3 trade, 55 exits): median spread at the trigger 3 ticks (0.75 pt), queue ahead 1-2 lots, mid-trigger touch. For failures vs fills: traded volume at/through our price within 3 s median 0 vs 19; touch drift after 3 s -2.0 to -2.75 ticks vs +0.8; adverse extension 3 s: 4.0-4.3 pts vs 2.2. Latency ablation (W42, 55 exits, queue): fill 0.64/0.73/0.76/0.75/0.78/0.76/0.80 at 5/25/50/100/150/250/500 ms; exit vs stop -0.77/-0.61/-0.69/-0.52/-0.40/-0.46/-0.33 (trade-through: 0.62/0.65/0.75/0.67/0.73/0.73/0.76 and -0.86 ... -0.44).

## 3. Hypotheses ranked by evidence (why live joins fail more than the 0.78 headline)

| rank | hypothesis | evidence | verdict |
|---|---|---|---|
| 1 | Composition: the live week's stop exits were overnight/evening, where the same replay fills 0.57-0.68, plus week-to-week and n=17 noise | replay rate reweighted to the live time-of-day mix 0.69 / 0.65 (P(<=8/17) 0.05 / 0.09); matched week W42 0.64 / 0.62 (P 0.15); weekly SD 0.08; outcome-conditional exit quality identical live vs replay | explains most of the 0.78 -> 0.47 gap and ALL of the -0.52 -> -2.01 slip gap once fills are accounted; residual (live 3/9 in 18-22 ET vs 0.64-0.68, P ~0.05) is post hoc |
| 2 | Price runs away before the limit can fill (stop-run continues; the touch leaves the limit) | 5/5 traced non-fills filled at market 2.8-10.0 pts beyond the limit; replay failures: 14/17 and 14/21 with zero tape at/through our price in 3 s; adverse 3-s extension 4.0-4.3 vs 2.2 | the mechanism of the failures (not an independent cause of the gap); consistent live and replay |
| 3 | Queue / hidden size: our 14 lots wait behind more size than the prop queue assumes (live first fills take 0.7-0.9 s from create vs 0.15-0.21 s in replay; fills arrive in 3-9 lot increments) | slower live first fills; partial 1/14 at 2.74 s (row 9); replay trade-through rule lowers the replay rate only 0.636 -> 0.618 | plausible, small, not separable with N=11 traces |
| 4 | Latency / feed lag | live create->Working 85-258 ms; W42 ablation: fill rate UP, slip no worse at 25-500 ms | **contradicted** for latency up to 500 ms; feed lag of the strategy's tick stream relative to the exchange tape cannot be measured without live-day L2 |
| 5 | Position-limit clash | row 6: HM join rejected 10-20 23:55:09, ST fallback fills 3 s later (both books stopped together; 28 open + 28 working = 56 > 50, per the user); replay clash share 8.2% vs live 8.3%, 1.06 rejections/week; trace holds no Rejected join state (10-21..23 clean) | explains 1/18; not the rate gap |
| 6 | Join placed on the wrong side / mispriced | all 12 traced joins are own-side exit orders (Sell/SellShort to close longs, BuyToCover to close shorts) with limit within [-0.8, +1.5] pts of the nominal stop (half-spread); filled and failed joins have the same offset range (filled -0.8..+1.46, failed +0.36..+1.43) | no evidence |
| 7 | Join bypassed / CSV omission | row 19: join created and cancelled by a strategy CancelAllOrders + Position.Close in 31 ms; trade missing from the CSV | 1 event; denominator 8/18 = 0.44; needs the strategy source/print to identify the branch |

Not tested, requires data the box does not have: whether the strategy's tick feed lags the CME tape (would act on trigger time), exact queue position at placement, and the true 'trigger' instant (Last print) for each live attempt.

## 4. Minimum data needed to settle it

1. **NQ mbp-10 for the live days (blocked: Databento key not in env, Saturday extension pending the user):** daily files 2026-10-20, 10-21, 10-22, 10-23 (about 2.8-3.4 GB total; only 14:00 ET 10-20 .. 02:00 ET 10-23 are needed). With them: replay each of the 18+1 attempts at its true CreateOrder timestamp (ms in the trace) - per-attempt fill/no-fill, queue ahead and tape return, measured feed lag (live create time minus the tape time of the first trade at/through the stop), and the per-trade expected exit price for the live-minus-replay column in LIVE_RECON. The 10-24 weekend extension alone (10-24 is a Saturday) adds no trades; the live days above are what is needed. Only then can 'latency/feed lag' (rank 4) and 'queue' (rank 3) be separated.
2. **The 10-20 NT8 trace** (nt8log_trace.20261020.*): 7 of the 18 attempts (incl. the rejection) have no order lifecycle.
3. **Strategy ExecLogCsv (P9_NT8_SPEC section 5)** pushed with the daily files: best bid/ask and sizes at every join placement would answer ranks 2-4 without L2.
4. **Sample size:** the fill rate needs about 90 attempts (about 5 live weeks at 18 stop exits/week) for a +-0.10 interval; until then, treat 0.47 as consistent with the overnight-mix replay prediction of 0.65-0.69 and plan for an exit slip of about -1 to -2 pts on stop exits at that mix, which is the cost the T4 skip-join / wait variants were scored against.
5. The CSV clock (ET) and the missing 04:00 ST trade should be fixed in LIVE_RECON.md / FORWARD_REGISTER.md by their owner (not edited here).


## 5. With 10-20..23 tape (added 2026-10-25, EXT agent; per-trade replay on the new weekly L2 part)

**Supersedes the "no L2 on disk" statements above.** NQ mbp-10 for 2026-10-19..10-23 (job GLBX-20261025-DSDKAWJBDU, `raw/NQ/ext/GLBX-20261025-*`, NQZ6 = instrument 261401) was bought on 2026-10-25 under the weekly L2 extension (ruling 6). Code `autopilot/join_recon2/` (jb_prep.py, jb_worker.py, jb_stats.py, jb_summary.py, jb_tables.py, jb_n19.py; clock scans jb_scan*.py), outputs `join_recon2/summary.json`, `join_replay_per_attempt.csv`, `entry_slip_per_trade.csv`, `tape_mid_T0.csv`, `table_final.md`. Engine = `exec_engine_l2` (prop queue, hid 0, `touch` join, 3.0 s life then market fallback, `stk1000000`), the same call as `t4_replay.exit_arms` (struct48 T4), run unedited; 14 lots.

### 5.1 Clocks (what is time-aligned to what)
* CSV and trace times are US Eastern (UTC = ET + 4 h in October 2026). Fixed in code (originals backed up): `pairP2/live_vs_replay_p9.py` default tz Chicago -> New_York (`.bak_pre_et_fix_20261025`); `forward/ap_forward_register.py` CSV tz Chicago -> ET (`.bak_pre_et_ext1025`); `LIVE_RECON.md` (+1 h on every ET column) regenerated (`LIVE_RECON.md.bak_pre_et_fix_20261025`). `join_attempts.csv` was already ET.
* The trace stamps run ahead of the exchange clock: replaying the 427 traced entry-slice market orders (31 trades, 1 lot each) on the tape at (Submitted stamp + delta), lat 0, gives an exact fill-price match of 27% at delta = 0 and **82.3% at delta = -30 ms** (mean live-minus-replay price -0.001 pt; cliff between -20 and -15 ms; 76-82% over -35..-20 ms). Every replay below uses **exchange arrival = Submitted - 27 ms** (the 82.6% / -0.013 pt figures in 5.4 are at -27 ms). Create -> Submitted is 52-78 ms in the join log (145 ms once, row 9).
* Strategy trigger -> CreateOrder lag: the first tape print at/through the nominal stop (entry avg -/+ 60) precedes the logged CreateOrder by a median **104 ms** (48-160 ms in 11 of 12 traced events, one 913 ms outlier = #15); the trigger instant used below is that print (the "true trigger"). Feed delay and clock offset are not separable.

### 5.2 Every attempt: replay vs live vs tape
Replay A = engine at the true trigger (first print at/through nominal, +5 ms, join at the touch at arrival). "As-live" = the live strategy's own behaviour: limit price fixed at what the strategy logged (stale by the create -> arrival time), arrival at Submitted - 27 ms. Rows 1-7 (10-20) have no order trace: trigger and arrival are inferred from the tape, "M2" = limit at the touch of tape-time trigger + 73 ms, arrival + 135 ms; "E" = trigger anchored on the CSV exit time minus 4.1 s (fallback orders start 3.7-4.7 s after the join); both are sensitivity only.

| # | exit ET (CSV) | book/side | live outcome | tape trigger ET (first print at/through nominal) | create-trigger lag ms | replay A (queue) joined | replay A (trade-through rule) | as-live replay (stale limit, arrival Submitted-27 ms), joined | tape 3 s after arrival: vol at / through limit; first trade at limit; adverse extension (pts) | live exit px / replay A exit px |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 10-20 14:33:10 | HM L | filled (CSV) | 14:33:09.315 |  | 14.00/14 | 14/14 | M2 14/14 | 77 / 72 lots; first 0.01 s; adv ext 1.50 | 29721.75 / 29720.50 |
| 2 | 10-20 14:42:57 | ST L | no fill -> mkt (CSV) | 14:42:53.216 |  | 2.00/14 | 0/14 | M2 0/14; E 14 | 0 / 0 lots; first  s; adv ext 7.75 | 29680.00 / 29682.00 |
| 3 | 10-20 18:42:29 | ST L | no fill -> mkt (CSV) | 18:42:29.278 |  | 14.00/14 | 14/14 | M2 14/14; E 14 | 5 / 3 lots; first 0.08 s; adv ext 1.75 | 29910.25 / 29912.75 |
| 4 | 10-20 21:00:11 | ST L | filled (CSV) | 21:00:10.423 |  | 14.00/14 | 14/14 | M2 14/14 | 29 / 17 lots; first 0.02 s; adv ext 2.50 | 29907.25 / 29907.00 |
| 5 | 10-20 21:00:59 | HM L | no fill -> mkt (CSV) | 21:00:56.073 |  | 14.00/14 | 14/14 | M2 14/14; E 0 | 8 / 4 lots; first 1.98 s; adv ext 3.75 | 29888.25 / 29890.25 |
| 6 | 10-20 23:55:09 | HM L | REJECTED (position limit) | 23:55:09.154 |  | 14.00/14 | 14/14 | M2 14/14 | 25 / 21 lots; first 0.52 s; adv ext 1.75 | 29920.50 / 29922.25 |
| 7 | 10-20 23:55:12 | ST L | no fill -> mkt (CSV) | 23:55:09.052 |  | 14.00/14 | 14/14 | M2 14/14; E 0 | 7 / 4 lots; first 2.13 s; adv ext 3.00 | 29923.00 / 29923.25 |
| 8 | 10-21 03:26:17 | ST S | filled 14/14 | 03:26:16.384 | 101 | 14.00/14 | 14/14 | see note | 14 / 0 lots; first 0.01 s; adv ext 3.75 | 29901.25 / 29901.50 |
| 9 | 10-21 09:43:21 | ST L | 1/14 + 13 mkt | 09:43:17.606 | 116 | 0.25/14 | 0/14 | 0/14 | 1 / 0 lots; first 2.83 s; adv ext 6.50 | 29798.75 / 29799.38 |
| 10 | 10-21 20:05:31 | HM S | no fill -> mkt | 20:05:27.193 | 83 | 0.00/14 | 0/14 | 0/14 | 0 / 0 lots; first  s; adv ext 6.50 | 29831.75 / 29831.45 |
| 11 | 10-22 19:02:44 | HM L | no fill -> mkt | 19:02:39.979 | 116 | 0.00/14 | 0/14 | 0/14 | 0 / 0 lots; first  s; adv ext 5.25 | 29089.50 / 29088.11 |
| 12 | 10-22 20:14:49 | ST S | no fill -> mkt | 20:14:45.898 | 48 | 0.00/14 | 0/14 | 0/14 | 0 / 0 lots; first  s; adv ext 11.00 | 29133.25 / 29132.23 |
| 13 | 10-22 20:47:08 | ST S | filled 14/14 | 20:47:07.658 | 122 | 14.00/14 | 14/14 | 14/14 | 15 / 0 lots; first 0.81 s; adv ext 5.25 | 29160.00 / 29160.50 |
| 14 | 10-22 21:53:34 | HM L | no fill -> mkt | 21:53:30.235 | 97 | 0.00/14 | 0/14 | 0/14 | 0 / 0 lots; first  s; adv ext 4.50 | 29135.25 / 29137.62 |
| 15 | 10-22 21:56:14 | ST L | filled 14/14 | 21:56:10.517 | 913 | 14.00/14 | 0/14 | 14/14 | 24 / 9 lots; first 2.58 s; adv ext 3.25 | 29118.75 / 29118.50 |
| 16 | 10-23 01:26:40 | HM L | filled 14/14 | 01:26:39.597 | 160 | 14.00/14 | 14/14 | 14/14 | 20 / 6 lots; first 0.71 s; adv ext 2.50 | 29113.50 / 29113.75 |
| 17 | 10-23 01:28:36 | ST L | filled 14/14 | 01:28:35.575 | 106 | 14.00/14 | 14/14 | 14/14 | 14 / 0 lots; first 0.37 s; adv ext 1.50 | 29107.00 / 29106.75 |
| 18 | 10-23 01:42:00 | HM S | filled 14/14 | 01:41:58.005 | 76 | 14.00/14 | 0/14 | 14/14 | 17 / 0 lots; first 0.91 s; adv ext 1.75 | 29172.50 / 29172.50 |

Notes. Row 3: the CSV exit (18:42:29) precedes the first print at/through the nominal stop (18:42:29.278) - the live strategy fired >3 s before the tape reached its own stop level; trigger unidentified (the CSV second is truncated, 1 s at most). Row 6 is the broker-rejected HM join (replay shows what an accepted order would have done). Row 8: the as-live replay is timing-borderline: the live limit equals the ask at the then-quote, so the result flips with +/-30 ms of arrival (filled at arrivals <= -45 ms, engine "expired unfilled" -35..-27 ms, 4.6/14 + market at >= -20 ms); the live fill was 14/14 in 0.014 s. Row 9: live 1/14 at 2.74 s; replay 0.25 lot (prop queue gives fractional lots). Row 15/18: the trade-through rule (needs a print one tick through) does not fill; the queue rule and the live order did.

### 5.3 Result (exact Clopper-Pearson 95% CIs)
| quantity | value | CI |
|---|---|---|
| live full joins, 17 attempts (rejected excluded) | 8/17 = 0.471 | [0.230, 0.722] |
| **replay A on the same 17 triggers (queue rule)** | **11/17 = 0.647** | [0.383, 0.858] |
| replay A, trade-through rule | 9/17 = 0.529 | [0.278, 0.770] |
| per-attempt outcome agreement live vs replay A (full vs not full) | 14/17 = 0.824 | [0.566, 0.962] |
| ...on the 11 traced attempts (rows 8-18) | **11/11** (live 6 full + 1 partial + 4 none; replay 6 full + 0.25 lot + 4 none) | [0.715, 1.000] |
| ...on the 6 untraced attempts (10-20) | 3/6 (live 2 full; replay 5 full) | [0.118, 0.882] |
| discordant pairs | 3 (replay fill / live fail: rows 3, 5, 7), 0 the other way | exact McNemar p = 0.25 |
| as-live replay (stale limit) on rows 9-18 | 10/10 outcomes equal live | row 8 timing-borderline |
| exit px vs nominal stop (pts, + better), 11 traced: live / replay A | -2.32 / -2.15; live minus replay -0.18 (SD 0.96; SE 0.29) | t95 [-0.82, +0.47] |
| create-minus-trigger lag (ms), 12 traced | median 104 (48..160; 913 once) | |

Reading: (1) **No mechanism gap is visible where an order trace exists**: the exact engine reproduces all 11 traced outcomes and the exit prices within 0.2 pt on average (seven of 11 exits equal within 0.5 pt; the largest misses are rows 14 and 11, -2.4 / +1.4 pt, market fallbacks in a moving tape). The four traced non-fills and the partial are all "price runs away": zero volume at or through the limit in 3 s (rows 10-12, 14) or 1 lot at 2.83 s (row 9); adverse extension 4.5-11.0 pts; every fill had 14-24 lots printing at or through the limit, the first within 0.01-2.58 s. (2) **The 0.78 -> 0.47 gap is mostly the mix of triggers**: the same engine on the live triggers gives 0.65 (queue) / 0.53 (trade-through), which is what the earlier time-of-day reweighting predicted (0.65-0.69) and inside the live CI; by ET block (live / replay A): 00-02 3/3 / 3/3, 02-08 1/1 / 1/1, 08-12 0/1 / 0/1, 12-18 1/2 / 1/2, 18-22 3/9 / 5/9, 22-24 0/1 / 1/1. (3) The residual 0.65 -> 0.47 is three 10-20 attempts (rows 3, 5, 7; 18:42, 21:00, 23:55 ET) with no order trace and an uncertain trigger (row 3 impossible under the 60-pt rule; rows 5, 7: replay fills in 3-8 lots of volume at the limit, the live join did not): p = 0.25, not distinguishable from noise or from the position-limit episode at 23:55 (rows 6-7); not shown to be a mechanism. Verdict on the question asked: the 18:00-22:00 composition explains the headline; no engine-vs-live mechanism difference is detectable in the 11 traced events; a systematic difference of up to roughly 30 percentage points in fill probability per attempt cannot be excluded with n = 17.

### 5.4 Entry slip (F1 entry-slip part; now that mids exist)
Pts per lot, + adverse, ST+HM 14-lot trades (n = 29 incl. the omitted 04:00 trade), against the L2 mid at each slice's exchange-clock order time (traced slices: actual Submitted stamps, 21 trades; others: first slice at the trigger minute + 0.45 s, 2 s apart): **live 0.458 (1.83 ticks) t95 [0.244, 0.672]; replay of the same slices 0.529 (2.12 ticks) [0.466, 0.592]**; traced 21 trades only: live 0.591 vs replay 0.560 (+0.03 pt); exact fill price per slice 82.6%, mean live-replay -0.013 pt. By book: ST 0.34 (n=17), HM 0.63 (n=12). The earlier replay expectation S14x1 (ST 1.90 / HM 1.77 ticks = 0.475 / 0.44 pt) is inside the live interval. Against the **single mid at the trigger minute** (what "mid at trigger" gives when the 14 lots are staggered over ~26 s) the slip is -0.41 pt [-2.45, +1.63] (n=29): dominated by the price drift during the stagger (SD of the per-trade value 5.4 pt), so it is not a cost measure. 8-lot ST/HM trades (10-23 day session, untraced, assumed cadence): live 0.075 [-0.196, 0.346] vs replay 0.321 (n = 11). WT (7-lot, a different strategy; slice cadence unknown) not replayed meaningfully. Files: `join_recon2/entry_slip_per_trade.csv`.

### 5.5 The bypassed 19th event and the omitted trade (flag for the user)
* 2026-10-21 04:34:01 ET (ST long, 14 lots): first print at/through the nominal 29845.75 at 04:34:01.480 (29844.25); CreateOrder 04:34:01.570 (limit 29845.00), CancelAllOrders and Position.Close 31 ms later; the join never rested. Live market sell 14 @ 29842.52 (-3.23 pt vs nominal). Replay market sell 14 at create + 31 ms: 29842.29 (arrival + 31 ms) / 29842.64 (+60 ms) / 29843.30 (+0..5 ms) - the live price sits inside that band, so the book-walking market model is accurate to ~0.1-0.8 pt here. **Counterfactual: the same join left resting would have filled 14/14 at 29845.00 about 0.26 s after create (queue and trade-through rules; tape: 20 lots at/through the limit within 0.23 s)**: the bypass cost 2.48 pt = $694 on this trade.
* **That trade is missing from `StratTrades_DualStrat2_<acct>.csv`**: ST Buy 14, entry 2026-10-21 04:00:00 ET (14 slices, avg 29905.73, traced), flattened by the market Close at 29842.52: -63.21 pt = **-$17,699 gross, about -$17,767 after $4.84/lot** (user estimate ~ -$17.7k). W43 live net in FORWARD_REGISTER/FWD_AB_SETS therefore understates losses by this amount (CSV 39 Set A trades, 18 stop exits; with the trade 40 and 19). Nothing else changed.

### 5.6 What remains unknown
* Why rows 3, 5, 7 (10-20, no trace) failed live while the engine fills them: the 10-20 NT8 trace was not retained; the strategy's trigger rule there is inferred (row 3 contradicts the nominal-stop rule). Position-limit interaction (rows 6-7) is not modelled in the replay (books independent).
* Queue position and hidden size at the live placement: only the engine's prop-queue estimate; the 14-lot fills in 0.4-2.6 s are matched by the engine, but with n = 6 fills the queue model is untested against alternatives (trade-through rule fails rows 15 and 18, so it is the pessimistic bound).
* Arrival time is calibrated on 427 entry slices (+/-5 ms); the join (limit) path (Create -> Submitted -> Working 85-258 ms in the log) has no exchange-side timestamp, and row 8 shows a +/-30 ms sensitivity.
* The strategy's logged join limit equals the touch at (CreateOrder - 27 ms) in only 4/11 cases (others within 0.25-1.25 pt): its own quote source/time is not known (rank 4 in section 3 stays open at the feed-lag level, but latency itself is not a cause: the engine reproduces the outcomes with the real arrival times).
* n = 17: a 95% interval for the true fill rate stays about +/-0.25 wide; the weekly extension adds ~18 attempts per week.
