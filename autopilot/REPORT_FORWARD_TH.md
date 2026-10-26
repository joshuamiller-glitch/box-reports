# REPORT_FORWARD_TH - forward TH-cut counterfactual (user job 3, 2026-10-25)

Research only. Code `autopilot/forward/ap_forward_th.py`; cache `forward/series/FORWARD_TH_CF.json`; statistics + per-trade table `forward/series/FORWARD_TH.json`; the same section is rendered in `autopilot/FORWARD_REGISTER.md` ("Forward TH-cut counterfactual"). Live files are referred to by their data/live names; no account number is written into any new file.

## Headline

* **50 ST loss-side TH cuts** in the live files from trading day 10-13 on (entries from 2026-10-12 18:00 ET): 46 in the pair file (`StratTrades_DualStrat_<acct>.csv`, 10-12..10-16, 8 lots, TH on) and 4 in the DualStrat2 file (10-23 only, 8 lots; TH was off in the 14-lot period 10-20..10-23 morning). All 50 replayed on direct mbp-10 (10-13..10-23, 9 trading days, nothing pending).
* **Paired mean (cut minus no-cut): +5.58 pts/trade = +$893/trade, 95% session-block bootstrap CI [-$1,897, +$3,611] (-11.8..+22.3 pts); total +$44,639 over 9 trading days = +$24,799 per 5-day week.** The CI includes zero. P(d>0) = 0.74.
* **Detectable effect (80% power, 5% two-sided): 24.4 pts/trade = $3,942/trade = about $108k/week.** The test could not have seen anything smaller than that; with 46 cuts in the first (4-day) week and 4 in the second, a single week's MDE is $45k (W43) to $153k (W42) in d-dollars. A null here is therefore uninformative at any plausible per-cut size (the audit's loss-side estimate is a system-level -$0.1M..-$0.5M per 31 months, not a per-cut number).
* **Shape of the effect**: without the cut 38 of 50 trades would have gone on to the stop (cut saved on average ~+35 pts each) and 12 of 50 to the 60-pt target (cut gave up ~-80 pts each); the cut was better in 76% of trades but the 24% winners it killed carry the cost. Net +5.6 pts/trade, SD of d 50 pts.
* **Knock-on caveat (important)**: 30 of the 50 cuts are followed by a live same-book entry that happened before the no-cut trade would have ended; those later trades would not exist without the cut. The sequence view (A = live, B = no TH; B drops later entries inside a no-cut holding) gives A-B = +$25.7k for the DualStrat2 file (4 cuts) and -$5.9k for the pair file (26 kept cuts +$5.5k, 27 dropped live trades -$11.4k): the pair-file number is the per-trade +$22.3k pushed to roughly zero/negative once the extra attempts the cut made possible are accounted for, which is the audit's mechanism (cuts buy extra attempts that lose on average). The paired per-trade statistic is the object asked for; the sequence view is informational and ignores signals B could have taken that A missed.

## Weekly table and statistics (as rendered in FORWARD_REGISTER.md)

## Forward TH-cut counterfactual (user job 3, 2026-10-25; code forward/ap_forward_th.py; full method and caveats REPORT_FORWARD_TH.md)

Object: every live ST trade closed by the TH LOSS-side cut (exit name ends LossExit), replayed WITHOUT the cut on the real mbp-10 tape (exec_engine_l2, live entry as anchor, 60/60 bracket, 16:55 ET flatten, stop exits through the live stop-join model XJ3). Paired difference d = cut P&L - no-cut P&L per cut trade (+ = TH helped). Weeks start Sunday 18:00 ET; W42 is partial (trading days 10-13..10-16), W43 informational. Only complete rows from 10-13 on; days without mbp-10 on disk are PENDING_L2 (never imputed).

Identification: exitName ends 'LossExit' (loss-side TH cut; ProfitExit = profit-side cut) in data/live/StratTrades_*.csv, trading day >= 20261013 (entries from 2026-10-12 18:00 ET). Cuts by file/book: DualStrat2 file HM CUT_LOSS n=3; DualStrat2 file ST CUT_LOSS n=4; DualStrat2 file ST CUT_PROFIT n=4; DualStrat2 file WT CUT_LOSS n=7; pair file (DualStrat) ST CUT_LOSS n=46. Trace logs (nt8log_trace.*, nt8log_latest): 5 files, 0 LossExit lines (trace window ends before the 10-23 TH-on period; the CSV is the identification of record).

| week | ST loss-cuts | replayed | pending L2 | mean d pts/trade | mean d $/trade | 95% CI $/trade (session-block bootstrap, 10,000) | d $ in week | MDE80 $ for this week alone | P(d>0) | DualStrat2 file n / d $ | pair file n / d $ |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 2026-W42 (partial, from 10-13; informational) | 46 | 46 | 0 | +3.03 | +485 | [-2,247, +3,307] | +22,314 | 152,801 | 0.64 | - | 46 / +22,314 |
| 2026-W43 (informational) | 4 | 4 | 0 | +34.88 | +5,581 | [+4,942, +6,411] | +22,325 | 45,058 | 1.00 | 4 / +22,325 | - |
| **cumulative (10-13 on)** | 50 | 50 | 0 | +5.58 | +893 | [-1,897, +3,611] | +44,639 | 107,646/wk | 0.74 | | |

Cumulative ST loss-cut: n=50 cuts in 9 replayed trading days; mean d +5.58 pts/trade (95% CI [-11.80, +22.29]) = +893 $/trade (CI [-1,897, +3,611]); +24,799 $/5-day week (total +44,639); cut better in 76% of trades; SD of d 50.3 pts. **Detectable effect (80% power, 5% two-sided, = 2.8 x bootstrap SE): 24.4 pts/trade = $3,942/trade = $107,646/wk.** A null here means 'could not have seen less than that'; with a handful of cuts per week the weekly MDE is far larger still.

| class (informational except ST loss) | n | mean d pts | mean d $ | 95% CI $/trade | $/5-day wk | MDE80 $/trade |
|---|---|---|---|---|---|---|
| ST LOSS ALL | 50 | +5.58 | +893 | [-1,897, +3,611] | +24,799 | 3,942 |
| ST LOSS DualStrat2 file | 4 | +34.88 | +5,581 | [+4,942, +6,411] | +22,325 | 1,119 |
| ST LOSS pair file | 46 | +3.03 | +485 | [-2,247, +3,307] | +27,892 | 4,042 |
| ST LOSS second file | 0 | - | - | - | - | - |
| HM LOSS | 3 | -9.66 | -1,545 | [-11,435, +8,240] | -4,635 | 13,122 |
| WT LOSS | 7 | -10.32 | -1,445 | [-4,680, +3,155] | -10,115 | 5,837 |
| ST PROFIT CUT | 4 | +19.03 | +3,045 | [-6,048, +12,138] | +12,180 | 12,749 |
| HM PROFIT CUT | 0 | - | - | - | - | - |

Knock-on caveat (informational, not the paired test): 30 of the 50 replayed ST cuts are followed by a LIVE same-book entry before the no-cut trade would have ended, i.e. without the cut the book would have been busy and that later trade would not exist. Sequence view per file (A = live, B = no TH, later entries inside a no-cut holding dropped): DualStrat2 file: 4 kept cuts d +22,325 + 1 dropped live trades +3,419 = A-B +25,744 $; pair file (DualStrat): 26 kept cuts d +5,474 + 27 dropped live trades -11,382 = A-B -5,909 $.

Second account: no StratTrades file for a second account exists in data/live (the Sim files hold no ST loss-cut in the window), so there is no second-file row; it appears automatically when such a file arrives. Bootstrap basis: trading-day x session (Asia 18-02, London 02-09:30, NY 09:30-18 ET) blocks, 10,000 draws; rows with fewer than 5 blocks use trade-level resampling (flagged in FORWARD_TH.json).

Machinery check on the live trades that were NOT cut (same replay, n=120): outcome class agrees in 119/120 (live targets reproduced as targets 65/66, live stops as stops 54/54); stop-exit pts live -61.31 vs replay XJ3 -61.36.

## Identification of the cut rows

* Rule: in `data/live/StratTrades_*.csv`, `exitName` ends `LossExit` (ST_LossExit / HM_LossExit / WT_LossExit = DualStrat `ManageLoss` -> `RequestBookExit(b,"LossExit")`, DualStrat.cs ~l.683-785; ST 15/3/30, HM 10/3/30, WT 10/2/30, eval 1 s). `ProfitExit` (ST profit-side module) is the profit-side cut and is shown separately (informational). Rows grouped to trades by (file, book, entry time, exit time, exit name, side); quantity-weighted.
* Counts from 10-13 (all files): ST loss 50 (pair file 46, DualStrat2 file 4), HM loss 3 and WT loss 7 (DualStrat2 file, 10-23 only), ST profit-side 4 (DualStrat2 file 10-23). The pair file has no HM/WT cut in the window (HM/WT TH off there); <sim-acct> and <sim-acct> hold no ST/HM/WT cut in the window (<sim-acct> LossExit rows are 10-04/05, before it).
* NT8 trace cross-check: `nt8log_trace.20261021..23*` and `nt8log_latest.txt` contain **0** LossExit order names or "TradeHealth-LOSS TRIGGERED" prints; the trace stops at 2026-10-23 10:05 ET, 17 minutes before the first 10-23 cut (10:24:46), and starts 10-21, after the pair-file cuts. So the trace neither confirms nor contradicts; it is consistent with TH being off 10-21..10-23 10:05. The CSV is the identification of record. (A scan for the string runs in every summary, so a later trace that contains cuts is counted automatically.)
* Second account: no StratTrades file for a second account exists in data/live (files: DualStrat2 and DualStrat for the same live account, <sim-acct>, <sim-acct>; the 10-24 NT8 log shows DualStrat2 being enabled on another account, with no trades file yet). There is therefore no "second file" row; one appears automatically when a file arrives. Per-file rows are given instead (DualStrat2 file vs pair file).

## Replay method

* Per cut trade: same signal and entry (the live entry average is the anchor: the engine fills the market entry at bar open + 0.45 s with qty live lots, then the bracket is shifted by the live-minus-engine entry difference so stop/target sit at live entry -/+ 60 pts for ST/HM, -/+ 45 / 33.75 for WT). Natural exit = first of target (resting limit, prop queue), stop, 16:55:02 ET flatten (DualStrat FlattenAtHHmm 1655). Stop and flatten exits go through the live stop-join model XJ3 (touch join, 3.0 s, then market; as in JOIN_RECON / firm_replay.exit_arms); the resting-stop-market variant is stored as a sensitivity (ST mean d +6.09 pts / +$974 per trade, CI [-$1,809, +$3,707], same conclusion). Engine: `exec_engine_l2` on raw NQ mbp-10 (instrument NQZ6), qmodel prop, latency 5 ms, no self impact.
* Pairing: d = (cut P&L) - (no-cut P&L), both in pts from the live entry price, dollars = pts x lots x $20. Entry cost and commission are common and cancel. Positive d = the TH cut helped. The live cut price is the actual fill.
* **Machinery check** on the 120 live trades that were not cut (ST/HM/WT Target and Stop exits, same replay): outcome class reproduced in 119/120 (live targets as targets 65/66; live stops as stops 54/54); mean replay-minus-live exit price -0.03 pts on agreeing trades; stop-exit pts live -61.31 vs replay XJ3 -61.36.
* Statistics: session-block bootstrap (blocks = trading day x session, Asia 18:00-02:00 / London 02:00-09:30 / NY 09:30-18:00 ET by entry; 11 blocks in the cumulative set), 10,000 draws, percentile CI on the per-trade mean; rows with fewer than 5 blocks (DualStrat2 file alone, HM, WT, profit-side) resample trades and are flagged. MDE80 = 2.8 x bootstrap SE. $/wk = total d / (replayed trading days / 5). Weeks start Sunday 18:00 ET; a week is the ISO week of its Monday label day; W42 is the partial week from 10-13 (labels 10-13..10-16), W43 informational, W44+ appended automatically.
* Heavy replays: `corepool.py run 1 1` workers, 4 at a time, about 13 GB each, one trading day per worker (about 4 min per day here); results cached per trade key, so each push replays only days not yet in the cache.

## HM and WT (informational, same statistic)

HM loss cuts n=3 (10-23): mean d -9.7 pts/trade (-$1,545), CI [-$11.4k, +$8.2k], MDE80 $13.1k/trade. WT loss cuts n=7 (10-23): -10.3 pts (-$1,445), CI [-$4.7k, +$3.2k], MDE80 $5.8k. ST profit-side cuts n=4: +19.0 pts (+$3,045), CI [-$6.0k, +$12.1k], MDE80 $12.7k. All three include zero and are far below detectability; they are shown so the machinery is exercised, not as evidence.

## Caveats

* **Knock-on / path dependence** (above): the paired statistic holds the later sequence fixed; the real cost/benefit of TH also runs through the extra attempts, the day-loss rule and the combo lock, none of which a per-trade replay captures. Pair-file cuts are 8-lot single-order entries with stop-market OCO in live (no stop-join); the XJ3 counterfactual is applied to them as instructed, the market-stop sensitivity is the era-matched variant.
* The CSV omits at least one trade (the 10-21 04:00 ST long, flattened 04:34 by a Close; JOIN_RECON section 5); it is not a cut, so no effect here, but other omissions would be invisible. The DualStrat2 file has two WT_Target rows with entry 0001-01-01 (excluded; not cuts). For the 10-23 rows `pnlNet` differs from price x lots by about 1.4% in total (the file total is -$203.6k vs -$206.6k from prices); the paired figure uses prices for both arms.
* Clocks: CSV and trace times are US Eastern (UTC = ET + 4 h in October 2026); the script converts with the zone (not a fixed offset), consistent with the corrected defaults in `live_vs_replay_p9.py` and `ap_forward_register.py`.
* Entry slices: the DualStrat2 file's 14/8-lot entries are 1-lot slices 2 s apart in live; the replay uses one market order (the bracket is anchored to the live average), a sub-point effect on the stop/target levels. The 8-lot slice schedule on 10-23 could not be checked (the trace ends before it). The 16:55 flatten is the DualStrat default; opening guards (Asia/NY) block entries only. One ST profit-cut entry (10-23 12:37) sits 8.5 pts from the engine fill (live entry anomaly); it only affects the informational profit-side row.
* Detectable effect: see headline. The CI narrows only as 1/sqrt(n) in session blocks (11 blocks so far).
* Only trading days with mbp-10 on disk are replayed (10-13..10-23 now). Later days stay PENDING_L2 in the table until the weekly L2 extension lands; nothing is imputed from bars.

## Update hook

* `ap_forward_th.py compute` is chain step `g_forward_th` in `forward/ap_live_arrival.py` (new, 7200 s timeout, run just before step f), so each live push (a) re-reads all StratTrades files, (b) finds cut rows without a cached result, (c) replays their label days on the L2 on disk via corepool (4 workers, >=16 GB free each), (d) recomputes `FORWARD_TH.json`; step f (`ap_forward_register.py all`) then renders the section into FORWARD_REGISTER.md (`render()` imports `ap_forward_th.lines()`; also run by the paper_all watcher). Originals backed up as `ap_live_arrival.py.bak_pre_fwdth_20261025` and `ap_forward_register.py.bak_pre_fwdth_20261025`.
* **The running arrival daemon (started before this change) holds the old chain in memory and needs a restart (`nohup nice -n 10 python3 ap_live_arrival.py &`) to run step g on the next push.** I did not restart it. The step was verified with `python3 ap_live_arrival.py --once` (log lines `g_forward_th` / `f_fwd_register` in `autopilot/live_arrival.log`) and by `ap_forward_th.py summary`.
