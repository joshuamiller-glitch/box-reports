# DS3_WORKS_B - T-WORKS part B (W-B) incl. P7 FIX part B and D5. PAGE 2, 2026-11-11T22:08Z (date -u). Page 1 (17:35Z) is kept below unchanged.

STATUS: Shadow only, post-hoc, no PASS claims, PRE-PROOF. Preregs WORKS_B_PREREG.md (sha 2167fd1caa1fdef7) and WORKS_B_P7FIX_PREREG.md (sha 39e1955d48481866); context tags P7_CONTEXT_DEFS.md (shared with W-C). All rows exact, one set per job, LPB_BASE reference, cut = stack maxDD cut % (negative = deeper), dmean = $/week, eq = equal-mean cut. Hook identity to the dollar: WB_X_ID (context cut hook), WB_D5_ID (entry-skip hook), WB_ID, WB_BR_ID.

## 0. Plain sentences (page 2)
1. Context-dependent P7 cut (P7 FIX B): choosing the cut by ENTRY context works and the reverse is a clear loser. Fresh trade (1st/2nd P7 trade of the session, not chasing, 30 minutes or more after the last P7 exit) gets the slow V2 line (45/5x/w5/p10); a re-entry or chasing trade gets a fast line. With the fast line 25/20x/w5/p1 (WB_X_FR_F4, 43 months): L6M cut +34.8 percent / +4,435 $/wk, HOLD -11.7 / +310, PRE +22.0 / +1,207, X' +36.3 / -190; equal-mean +49.0 / +12.7 / +39.0 / +50.2; bi-weekly WF vs LPB_BASE +20.75 percent OOS cut, mean -241 $/wk, beats 24 percent of 74 periods. L6M-only rows (6 months, other windows not yet run): fast 30/10x/w5/p2 +30.6 / +2,129 (WB_X_FR_F3), 30/5x/w5/p5 +31.5 / +194, 35/5x/w5/p3 +34.4 / -33, 40/5x/w5/p3 +21.0 / +1,811; the REVERSE control (fresh fast, re-entry V2) is -20.1 / -1,939; by side (short 40/5x/p3, long V2) +22.0 / +3,216; V2 uniform +15.4 / +1,483; by lots (>=5 lots fast): 4 of 6 months. Rule 2a label for FR_F4: HOLD drawdown is 11.7 percent deeper (floor -5), so it is RECENTS-ONLY, not a standing change; V2 is the floor so every P7 trade still carries a loss line.
2. Behavioural scorecard (standing principle 19:45Z, W-Q tool, L6M stack per week; LPB_BASE: full stops 24.5/wk -$40.1k, give-backs 9.1/wk, same-side losing runs max 12 / p95 6, no-new-evidence re-entries 37.3/wk): FR_F4 does NOT pass: full stops 25.7/wk (-$44.7k), give-backs 9.4/wk, runs max 13 / p95 7, no-new-evidence 44.2/wk; its gain is smaller losses per cut ("winners skipped 9.4k, losers avoided 8.8k, net +2.6k per week vs LPB_BASE"), not fewer failures. The same is true of never cutting (full stops 36.4/wk, -$94.8k) and of the cut-only-after-a-trend-day rule WB_B2_FPRI (32.4/wk, -$75.4k, runs max 12). A finalist must halve (a), (b), (c); no flag or context cut in part B does, so the repeat-after-failure defect has to be fixed by the entry-side governors (W-C/W-A), not by the cut line. The only thing the cut contributes is cost per failure.
3. P7 cut conditional on the prior day (WB_B2_FPRI = cut ON only when the prior day trended, F_PRIOR; 43 months): L6M +30.7 / +4,119, HOLD +9.9 / +1,103, PRE +7.6 / +364, X' -6.0 / -682 (eq +13.1); WF +17.6 percent OOS cut, +1,389 $/wk, beats 28 percent. The best exact conditional cut by the drawdown-first rule (L6M, HOLD, PRE all positive) but it triples full stops (32.4/wk, scorecard fail), and the day-level family max-stat test (86 flag x direction day mixtures of the cut-on / cut-off exact runs) puts the best mean cut at 17.3 vs a null 95th percentile of 24.1 (p 0.69): the cut-on/off split is as good as random mixing. WB_B2_STK5 (cut off while the stack Calmar5 >= 1): L6M 0.0 / +2,159, HOLD +2.1 / -845, PRE -1.3 / +44, X' +33.8 / +798, WF 0.0 / +596; never cutting (WB_C_NONE): +19.1/+10.4/+27.4 (L6M/PRE/X') and -19.1 HOLD, WF +9.95 / +350.
4. Frozen live week and the context tags: 48 of the 53 live P7 trades are "re-entry or chasing" (only 5 fresh, +10.3k), so the context cut is the fast line on nearly the whole trend week: of the 24 live P7 cuts, 22 are on re-entry/chasing trades (16 saves -$27.9k and 6 recoveries +$61.9k if held), 2 on fresh trades (1 save -$1.9k, 1 recovery +$7.2k). The fast line therefore does NOT spare the recoveries of last week; the week-turn test (no trend week turned losing) cannot be shown for a cut rule, because the live week's recoveries are re-entry trades. The 11-09..11 live week is not on the box.
5. D5 book exhaustion at the signal second (PTR 1-s features, push = max over the previous 60 s, P7/K7/M7 16,652 signals, first-order, 1,034 skip/half cells; leg-based divergence not built, W-C owns D3): no feature removes more worst-20-week losers than best-20-week winners for P7 (best ratio 0.95: pulled_against15 push >= 45 removes -$173k in the worst 20 weeks and +$189k in the best 20). The only selective cell is Asia: sweep_against (ticks the own-side best price retreated in one second) max of the last 60 s >= 16 skips 226 Asia P7 trades: removed worst-20 -$25.4k vs best-20 -$4.9k. Exact (WB_D5_SW, L6M only): +2.8 percent / +1,758 $/wk (eq +11.0), L1M -8.1; the other windows are not run. Reported, not promoted.
6. Carried from page 1 (unchanged): conditional cut-off flags (REG15) lose; near-target stand-in take loses in L6M (-9.1 / -1,253); conditional retarget 8 ticks when atr_rel < 1.3 (WB_B4_R8C) L6M +26.1 / +51, HOLD +8.1 / +460, PRE -10.6 / +227, X' +5.2 / -50, RECENTS-ONLY; `regime` (DayRegime, daily vol_lo/mid/hi at 10:30 ET) cannot carry a per-signal flag, a new per-book `EntryRegime` field is needed (v1.8); the entry-context tag (fresh / rechase) is exactly that field: the policy file's third column would match `r.Regime == b.EntryRegime` with values fresh / rechase, and the cut line per tag goes in the same row as the existing loss-cut grammar.
7. Profit side (conditional protection, exact, P7): WB_B3_P3 (`profit P7 * pct>=0.5 pulled_against_mult>=10 take win=5 persist=5` ON only when stack Calmar10 < 1), 43 months: L6M +23.2 / -710, HOLD +24.8 / -598, PRE -9.9 / -1,370, X' +13.2 / -51; WF -14.6 percent OOS cut, -1,624 $/wk: fails PRE and WF. Clips 11.9 fills per week in L6M (scorecard e), net -$2.4k/wk vs LPB_BASE.

## 1. Exact rows (this page)
| set | months | cut_L1M | dmean_L1M | eq_cut_L1M | cut_L3M | dmean_L3M | eq_cut_L3M | cut_L6M | dmean_L6M | eq_cut_L6M | cut_HOLD | dmean_HOLD | eq_cut_HOLD | cut_PRE | dmean_PRE | eq_cut_PRE | cut_X' | dmean_X' | eq_cut_X' |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| WB_C_V2 | 6 | 1.2 | 6120.8 | 8.5 | 15.4 | 2960.5 | 21.6 | 15.4 | 1482.9 | 21.6 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_X_FR_C0 | 6 | -3.8 | -1202.2 | 4.4 | 21.0 | 2447.9 | 27.2 | 21.0 | 1810.8 | 27.2 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_X_FR_F2 | 6 | 2.4 | -465.3 | 2.2 | 34.4 | -257.9 | 34.3 | 34.4 | -32.7 | 34.3 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_X_FR_F3 | 6 | 10.3 | 853.8 | 20.9 | 30.6 | 1838.6 | 38.8 | 30.6 | 2129.0 | 38.8 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_X_FR_F4 | 43 | 27.1 | 2824.3 | 43.0 | 34.8 | 2781.6 | 49.0 | 34.8 | 4435.1 | 49.0 | -11.7 | 310.3 | 12.7 | 22.0 | 1207.1 | 39.0 | 36.3 | -189.8 | 50.2 |
| WB_X_FR_F5 | 6 | 21.7 | 1862.3 | 22.5 | 31.5 | 2591.1 | 32.2 | 31.5 | 194.4 | 32.2 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_X_REV | 6 | 3.6 | -276.5 | -7.5 | -20.1 | -2604.4 | -34.0 | -20.1 | -1939.2 | -34.0 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_X_SIDE | 6 | 13.7 | 1438.8 | 27.2 | 22.0 | 4239.5 | 34.2 | 22.0 | 3216.4 | 34.2 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_X_LOTS | 6 | 1.2 | 6120.8 | 8.5 | 15.4 | 2960.5 | 21.6 | 15.4 | 1482.9 | 21.6 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_B2_FPRI | 43 | 9.4 | 705.4 | 25.8 | 30.7 | 7365.2 | 43.2 | 30.7 | 4119.1 | 43.2 | 9.9 | 1103.2 | 26.2 | 7.6 | 363.7 | 24.3 | -6.0 | -681.5 | 13.1 |
| WB_B2_STK5 | 43 | 0.0 | -402.6 | 10.4 | 0.0 | 484.0 | 10.4 | 0.0 | 2159.2 | 10.4 | 2.1 | -845.1 | 12.2 | -1.3 | 44.4 | 9.2 | 33.8 | 797.6 | 40.6 |
| WB_B3_P3 | 43 | 21.2 | 2559.7 | 17.5 | 23.2 | 4378.9 | 19.6 | 23.2 | -710.0 | 19.6 | 24.8 | -597.9 | 21.3 | -9.9 | -1369.5 | -15.1 | 13.2 | -51.0 | 9.2 |
| WB_D5_SW | 6 | -8.1 | -418.7 | 1.0 | 2.8 | -62.3 | 11.0 | 2.8 | 1757.5 | 11.0 | nan | nan | nan | nan | nan | nan | nan | nan | nan |

Context-cut sets: WB_X_FR_Fn = fresh V2 / re-entry-or-chasing fast line Fn (F2 35/5x/p3, F3 30/10x/p2, F4 25/20x/p1, F5 30/5x/p5, C0 40/5x/p3); WB_X_REV reverse; WB_X_LOTS/SIDE by lots/side; all windows shown only when complete; L6M-only rows are screens.

## 2. Worst-10 P7 sessions (L6M, by LPB_BASE P7 session P&L), entry by entry: LPB_BASE vs WB_X_FR_F4 vs WB_B2_FPRI (times are UTC entry minutes; exit name and $ per trade)
### session start 07-27 22:00 UTC, session 0, LPB P7 session P&L -14274
- LPB_BASE: total -14274 over 8 trades: -22:38 4L StateCut -3007; -00:11 4L Target 4800; -01:06 5L Target 5984; -01:23 7L StateCut -5705; -02:14 4L StateCut -3254; +03:54 4L StateCut -3694; +04:43 4L StateCut -3394; -05:40 7L StateCut -6005
- WB_X_FR_F4: total -10462 over 7 trades: -22:38 4L StateCut -2412; -00:11 4L StateCut -2204; -00:51 4L Target 4800; -01:23 7L StateCut -3990; -02:14 4L StateCut -1934; -02:27 4L StateCut -2209; +03:54 4L StateCut -2514
- WB_B2_FPRI: total -8562 over 4 trades: -22:38 4L Target 1105; -00:32 4L StopJoin -4710; -00:51 4L Target 4800; -01:23 7L StopJoinFallback -9758
### session start 05-27 13:30 UTC, session 3, LPB P7 session P&L -13000
- LPB_BASE: total -13000 over 5 trades: -14:11 4L StateCut -3374; -14:33 3L StateCut -2449; -15:00 4L StateCut -3654; -15:20 2L StateCut -1759; -15:39 2L StateCut -1764
- WB_X_FR_F4: total -8630 over 5 trades: -14:11 4L StateCut -1844; -14:33 3L StateCut -1894; -15:00 4L StateCut -1964; -15:20 2L StateCut -1799; -15:39 2L StateCut -1129
- WB_B2_FPRI: total 16 over 2 trades: -14:11 4L Target 4790; -15:00 4L StopJoinFallback -4775
### session start 09-09 22:00 UTC, session 0, LPB P7 session P&L -12681
- LPB_BASE: total -12681 over 3 trades: -23:01 4L StateCut -3274; -01:07 4L StateCut -3349; +05:07 7L StateCut -6059
- WB_X_FR_F4: total -3764 over 3 trades: -23:01 4L StateCut -2884; -01:07 4L StateCut -2079; +04:47 1L Target 1199
- WB_B2_FPRI: total 1239 over 3 trades: -23:01 4L Target 4790; -02:17 4L StopJoin -4750; +04:47 1L Target 1199
### session start 08-25 22:00 UTC, session 0, LPB P7 session P&L -12662
- LPB_BASE: total -12662 over 4 trades: +22:09 7L StateCut -5810; -00:04 7L Target 6004; -01:09 7L StateCut -5718; +03:03 7L StateCut -7138
- WB_X_FR_F4: total -9542 over 3 trades: +22:09 7L StateCut -7263; -00:04 7L Target 6004; -01:09 7L StopJoinFallback -8283
- WB_B2_FPRI: total -9358 over 1 trades: +22:09 7L StopJoinFallback -9358
### session start 05-05 22:00 UTC, session 0, LPB P7 session P&L -12366
- LPB_BASE: total -12366 over 2 trades: +23:48 7L StateCut -6223; -00:48 7L StateCut -6143
- WB_X_FR_F4: total -11754 over 2 trades: +23:48 7L StateCut -4998; -00:48 7L StateCut -6756
- WB_B2_FPRI: total -12366 over 2 trades: +23:48 7L StateCut -6223; -00:48 7L StateCut -6143
### session start 09-30 22:00 UTC, session 0, LPB P7 session P&L -12188
- LPB_BASE: total -12188 over 2 trades: -23:08 7L StateCut -6615; +00:01 7L StateCut -5573
- WB_X_FR_F4: total -8498 over 1 trades: -23:08 7L StopJoin -8498
- WB_B2_FPRI: total -8498 over 1 trades: -23:08 7L StopJoin -8498
### session start 05-15 06:00 UTC, session 1, LPB P7 session P&L -11920
- LPB_BASE: total -11920 over 8 trades: -06:07 4L StateCut -3344; -06:21 4L StateCut -3714; +06:56 1L Target 1199; +07:28 2L StateCut -1699; -09:12 1L Target 1199; -09:42 4L StateCut -3294; -10:40 2L StateCut -1464; +11:01 2L BookLock -802
- WB_X_FR_F4: total -7617 over 10 trades: -06:07 4L StateCut -2004; -06:21 4L StateCut -2244; +06:56 1L Target 1199; +07:28 2L StateCut -1679; -09:12 1L Target 1199; -09:42 4L StateCut -2094; -10:40 2L StateCut -1139; +11:01 2L StateCut -984; +11:52 2L StateCut -1069; -12:25 1L Target 1199
- WB_B2_FPRI: total -9962 over 6 trades: -06:07 4L StopJoin -3425; +06:56 1L Target 1199; +07:28 2L StopJoin -2342; -09:12 1L Target 1199; -09:42 4L StopJoinFallback -4630; -10:40 2L BookLock -1962
### session start 10-07 22:00 UTC, session 0, LPB P7 session P&L -11851
- LPB_BASE: total -11851 over 2 trades: +22:21 7L StateCut -5873; -00:56 7L StateCut -5978
- WB_X_FR_F4: total -12082 over 2 trades: +22:21 7L StateCut -6979; -00:56 7L StateCut -5103
- WB_B2_FPRI: total 1588 over 2 trades: +22:21 7L StopJoinFallback -6808; -04:10 7L Target 8397
### session start 06-17 22:00 UTC, session 0, LPB P7 session P&L -11837
- LPB_BASE: total -11837 over 2 trades: -23:42 7L StateCut -6615; +00:31 7L StateCut -5221
- WB_X_FR_F4: total -11178 over 2 trades: -23:42 7L StateCut -7578; +00:31 7L StateCut -3600
- WB_B2_FPRI: total -14022 over 2 trades: -23:42 7L StopJoin -8148; +00:31 7L StopJoin -5873
### session start 06-02 22:00 UTC, session 0, LPB P7 session P&L -11538
- LPB_BASE: total -11538 over 2 trades: +22:12 7L StateCut -5710; -23:35 7L StateCut -5828
- WB_X_FR_F4: total -11048 over 2 trades: +22:12 7L StateCut -7163; -23:35 7L StateCut -3885
- WB_B2_FPRI: total -8643 over 1 trades: +22:12 7L StopJoin -8643


## 3. Missing / next
11-09..11 live week; JN04RM-base versions of the winners (IJK jbjobs driver) and the exact JN05 joint with W-J; WB_X_LOTS (2 months to go), WB_X_FR_F2/F3/F5/SIDE other windows (F4 first); D5 other windows; scorecard on the four-window finalists once W-Q posts the acceptance file.

---- PAGE 1 (17:35Z) ----
# DS3_WORKS_B - T-WORKS part B (W-B): regime flag and regime-conditional exits. Page 1, 2026-11-11T17:34Z (date -u)

STATUS: Shadow only, post-hoc, no PASS claims, PRE-PROOF. Prereg autopilot/WORKS_B_PREREG.md (sha256 2167fd1caa1fdef7, DECISIONS.md). Base LPB_BASE exact (ROLL-fixed engine); every exact row below is one set per job, 43 months unless the months column says fewer; a window is shown only when all its months ran. cut = stack maxDD cut vs LPB_BASE in % (negative = deeper), dmean = mean change in dollars per week, eq_cut = equal-mean cut. Code code/th_works_b (wb_flags, wb_state, wb_hooks, wb_score). Hook identity tests passed to the dollar (WB_ID cut hook, WB_BR_ID bracket hook: 904 trades, 202,420.96 identical to LPB_BASE on 202606).

## 0. Plain sentences (page 1)
1. No causal flag from the working dials separates the live trend week from choppy weeks well. Last week (frozen file 11-02..05, 53 P7 trades) the P7 LOT gate was cold on every signal (Calmar10 below 1 all four days, even though P7 made 24.8k, 21.2k, 9.1k, 31.0k shadow base-lot dollars on the four days) because the ten days before were losses; "cold" therefore marks chop in history but was a lagging, wrong signal in the live trend week. ER(20) at the signal sat at the median of all weeks (percentile 0.38 of weekly share at 0.30), REG hot (atr_rel >= 1.3) was high (live week share 0.60 vs median 0.46, percentile 0.76; atr_rel >= 1.1: 0.81 vs 0.59, percentile 0.86), the family H day flags were the sharpest (F_ER share 0.23 vs median 0.07, percentile 0.94; F_ER2 0.23, percentile 0.80). Persistence: LOT and stack-Calmar states last 13-24 P7 signals; REG and ER20 flip every 2 signals (P(same next signal) 0.52-0.75), F_ER 0.89, F_PRIOR 0.91 (8 signals).
2. The P7 state cut (40/5x/w5/p3) is NOT earning its place in the exact engine on three of four windows: never cutting P7 (WB_C_NONE) gives stack maxDD cut +19.1 percent L6M, +10.4 PRE, +27.4 X' (mean +2,180, +964, +46 dollars per week) and loses only in HOLD (-19.1 percent, mean -1,016). Bi-weekly WF of NONE vs LPB_BASE: +9.95 percent OOS cut, mean +350, beats LPB in 14.9 percent of the 74 periods. The first-order hold-universe screen had said the opposite (never cut: -33.9 percent L6M); exact decides (re-entries and locks free up).
3. Conditional loss cut. Per-trade first-order regret (hold-to-bracket minus the cut, P7 StateCut trades, week-block bootstrap): REG hot atr_rel >= 1.5 (+338 per cut, 90 percent CI 45 to 642), >= 1.8 (+345, 64 to 639) and ER20 >= 0.30 with LOT warm (+530, 103 to 985) are the flags where the cut costs more; F_ER (trend day so far) goes the OTHER way (cut saves 1,184 per trade more on F_ER days). EXACT: switching the P7 cut off when atr_rel >= 1.5 (WB_B2_REG15, L6M) is worse: cut -11.1 percent, dmean -579. Switching it off when the stack Calmar5 >= 1 (WB_B2_STK5, 40 of 43 months): L6M cut 0.0 / mean +2,159, PRE -1.3 / +44, HOLD +2.1 / -845; one cut-active-only-after-a-trend-day set (WB_B2_FPRI, F_PRIOR) shows L6M +30.7 / +4,119 on 7 months (other windows running). Family max-stat over 86 flag x direction day-level mixtures of the two exact runs (cut on / cut off): best mean cut 17.3 vs null max 95th percentile 24.1, p 0.69: no flag beats random mixing of cut and no-cut days at the day level, so no conditional cut is claimed; the finding is the NONE row.
4. Live replay of the cuts (frozen week, hold-to-bracket counterfactual on the 1-s mid path, no re-entries): P7 24 cuts = 17 saves (-29.9k) and 7 recoveries (+69.1k), net hold better by +39.3k; K7 30 cuts: 25 saves (-15.0k), 5 recoveries (+11.4k); M7 13 cuts: 11 saves (-7.0k), 2 recoveries (+7.9k). No flag keeps the saves and drops the recoveries: with cut OFF in the trend state the P7 week gains +30.7k for ER20 >= 0.35, +29.1k for atr_rel >= 1.3, +19.6k for hot and ER20 >= 0.30, but each of these states still contains 4 to 9 saves; LOT warm and stack warm 10-day flags are never true in the live week (0 trend cuts), so they change nothing. The second live week (11-09..11) is NOT on the box: no trade log, no shadow P&L after 11-05, no MBO state days after 11-05 (NQ 1-min OHLCV to 11-10 exists in data/ext_20261110 but not the P&L history the LOT and stack flags need).
5. Conditional profit protection (first-order screens on the LPB_BASE cache, P7 first; exact sets WB_B3_P2/P3/P4 started): the best P7 profit lines lower four-window drawdown only by 16-19 percent at a mean cost of 300 to 3,400 dollars per week, conditioning on chop (ER20 >= 0.30 and LOT warm; stack warm; hot and ER20) raises the worst-window cut from 16.3 to about 19 percent at the same mean cost. In the live week the P7 lines clip 8-10 of 28 targets in either ER state (ER20 does not separate the live week), so the conditional line saves little there (P7 pct>=0.5 ahead_rel>=1.5 take: trend state net +6.5k, chop state -24.8k). K7/M7/U7 (three live lines) conditional vs unconditional: first-order K7 best unconditional line 6.5 percent worst-window cut, conditional on LOT warm 6.1 (no gain), M7 conditional on hot and ER20 trend 4.7 vs 1.2, U7 only in not-dead-tape 5.4 vs 0.0; all below 7 percent and all at a negative mean, none promoted yet.
6. Near-target (B4). The live stand-in as the exact engine can express it (K7/P7/M7 take when price is within 3 pts of target and the favourable extreme is 5 s old, mid-based: policy line `profit K7 * pct>=0.95 secs_fav>=5 take win=5 persist=1`, the same for P7 and M7) is WORSE than no stand-in in L6M: cut -9.1 percent, dmean -1,253 dollars per week (WB_B4_ST). First-order (EX universe, never-cut reference, 43 months) agrees: the stand-in costs 206.7k on K7/P7/M7 (P7 -120.5k) with a worst-window cut of -1.4 to 7.8 percent. The scored replacement is a REGIME RETARGET instead of a take: pull the target in by 8 ticks (2 pts, 58 instead of 60) on K7/P7/M7 only when atr_rel < 1.3 (chop), full 60 target otherwise (WB_B4_R8C): L6M +26.1 percent / +51 dollars per week, HOLD +8.1 / +460, PRE -10.6 / +227, X' +5.2 / -50, L1M -5.8; the unconditional 8-tick retarget (WB_B4_R8A, L6M only so far) is +24.2 / -287. It passes L6M and HOLD and fails PRE on drawdown, so the label is RECENTS-ONLY (rule 2a), and the bi-weekly WF vs LPB_BASE is -10.6 percent OOS cut, beats 12 percent of periods. Stand-in plus conditional retarget (WB_B4_STR8C, L6M): +24.4 / -218 (the take adds nothing).
7. Brackets (B5): P7 stop 45 / target 60 always (WB_B5_P7_4560, L6M): +5.5 / +1,556 (equal-mean +13.4); P7 target 45 when atr_rel < 1.5, else 60 (WB_B5_P_T45): L6M +42.9 / -2,026; P7 target 90 when atr_rel >= 1.5 (WB_B5_P_T90): -6.0 / -590 (trend extension does not pay in L6M). Only L6M exists for these; the chop short target buys drawdown at a mean cost, not a free lunch.
8. Field answer: `regime` (third column of the policy file) can NOT carry the flag as built. DayRegime in DS7.cs is a once-a-day string (vol_lo / vol_mid / vol_hi) set at 10:30 ET from the overnight range vs its median and never reset; rules match it (or the session name) for profit, loss-cut and bracket lines (lines 2136 and 2189). The flags above are per-signal and change every few signals. A new feature is needed: a per-book EntryRegime string ("chop" / "trend", or "cold"/"hot" for LOT/REG) written at signal time from the 5-min ATR (REG, already computed for JN04) and, for stack/LOT states, the daily shadow ledger, stored on the Book and matched by the same third column token (v1.8 field `EntryRegime`, rule match `r.Regime == b.EntryRegime`); the REG-based retarget above needs only atr_rel at signal, which the live code already has.

## 1. B1 flag table (P7 signals, 43 months; trend-direction flags; live week = frozen file 11-02..05, 53 P7 trades)
live_pctile = percentile of the live-week share among all weeks; regret columns = P7 cut regret in dollars per cut trade (hold minus cut), trend state vs chop state, difference with 90 percent week-block bootstrap interval (first-order, hold-universe).
| flag | on_rate | week_share_median | live_week_share | live_pctile | p_same_next_signal | median_run_signals | day_to_day_agree | regret_trend | regret_chop | diff | ci_lo | ci_hi |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER20>=0.25 | 0.516 | 0.526 | 0.509 | 0.46 | 0.519 | 2 | 0.523 | -31 | -4 | -27 | -298 | 260 |
| ER20>=0.30 | 0.424 | 0.44 | 0.396 | 0.38 | 0.529 | 2 | 0.479 | -12 | -23 | 11 | -336 | 284 |
| ER20>=0.35 | 0.337 | 0.333 | 0.321 | 0.44 | 0.579 | 2 | 0.526 | -41 | -5 | -36 | -418 | 343 |
| ER20>=0.40 | 0.255 | 0.25 | 0.226 | 0.36 | 0.642 | 2 | 0.639 | -46 | -8 | -38 | -323 | 313 |
| REG hot atr_rel>=1.1 | 0.598 | 0.588 | 0.811 | 0.86 | 0.708 | 2 | 0.67 | 8 | -65 | 73 | -196 | 330 |
| REG hot atr_rel>=1.3 | 0.482 | 0.455 | 0.604 | 0.76 | 0.707 | 2 | 0.623 | 66 | -107 | 173 | -116 | 455 |
| REG hot atr_rel>=1.5 | 0.396 | 0.375 | 0.547 | 0.81 | 0.717 | 2 | 0.637 | 179 | -159 | 338 | 45 | 642 |
| REG hot atr_rel>=1.8 | 0.294 | 0.3 | 0.321 | 0.55 | 0.75 | 2 | 0.712 | 222 | -124 | 345 | 64 | 639 |
| dead atr_rel<=0.6 (chop-ish) | 0.044 | 0.0 | 0.0 | 0.27 | 0.937 | 2 | 0.929 | -909 | 12 | -921 | -1569 | -297 |
| dead atr_rel<=0.9 (chop-ish) | 0.245 | 0.231 | 0.075 | 0.16 | 0.761 | 2 | 0.721 | 11 | -26 | 37 | -316 | 394 |
| LOT warm (P7 Cal10>=1) | 0.399 | 0.235 | 0.0 | 0.21 | 0.975 | 23 | 0.867 | 146 | -131 | 277 | -22 | 547 |
| LOT warm Cal10>=2 | 0.252 | 0.0 | 0.0 | 0.29 | 0.978 | 19 | 0.883 | -51 | -7 | -45 | -362 | 284 |
| STACK warm Cal5>=1 | 0.419 | 0.389 | 0.302 | 0.42 | 0.951 | 13 | 0.736 | 96 | -98 | 194 | -75 | 452 |
| STACK warm Cal10>=1 | 0.491 | 0.389 | 0.0 | 0.17 | 0.975 | 18 | 0.866 | -71 | 34 | -105 | -372 | 135 |
| STACK warm Cal20>=1 | 0.572 | 0.56 | 0.0 | 0.18 | 0.986 | 24 | 0.924 | -55 | 32 | -87 | -366 | 182 |
| F_ER | 0.09 | 0.065 | 0.226 | 0.94 | 0.887 | 3 | 0.87 | -1089 | 95 | -1184 | -1684 | -665 |
| F_ER2 | 0.153 | 0.154 | 0.226 | 0.8 | 0.817 | 2 | 0.785 | 120 | -47 | 168 | -205 | 512 |
| F_PRIOR | 0.361 | 0.314 | 0.189 | 0.28 | 0.909 | 8 | 0.515 | -16 | -19 | 3 | -269 | 256 |
| ER20>=0.30 & LOT warm | 0.171 | 0.091 | 0.0 | 0.21 | 0.81 | 2 | 0.76 | 413 | -117 | 530 | 103 | 985 |
| ER20>=0.30 | F_ER | 0.448 | 0.458 | 0.491 | 0.62 | 0.532 | 2 | 0.479 | -55 | 13 | -68 | -364 | 244 |
| hot1.3 & ER20>=0.30 | 0.196 | 0.19 | 0.264 | 0.77 | 0.732 | 2 | 0.76 | 142 | -64 | 206 | -170 | 612 |

## 2. Exact rows (vs LPB_BASE; this page 1)
| set | months | cut_L1M | dmean_L1M | eq_cut_L1M | cut_L3M | dmean_L3M | eq_cut_L3M | cut_L6M | dmean_L6M | eq_cut_L6M | cut_HOLD | dmean_HOLD | eq_cut_HOLD | cut_PRE | dmean_PRE | eq_cut_PRE | cut_X' | dmean_X' | eq_cut_X' |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| WB_C_NONE | 43 | 3.3 | -345.6 | 13.4 | 19.1 | 5552.3 | 27.6 | 19.1 | 2180.2 | 27.6 | -19.1 | -1015.8 | -6.6 | 10.4 | 964.1 | 19.8 | 27.4 | 45.5 | 35.0 |
| WB_B2_REG15 | 6 | -16.4 | -2228.9 | -20.2 | -11.1 | -2546.6 | -14.7 | -11.1 | -578.6 | -14.7 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_B2_STK5 | 40 | 0.0 | -402.6 | 10.4 | 0.0 | 484.0 | 10.4 | 0.0 | 2159.2 | 10.4 | 2.1 | -845.1 | 12.2 | -1.3 | 44.4 | 9.2 | 33.8 | 797.6 | 40.6 |
| WB_B2_FPRI | 7 | 9.4 | 705.4 | 25.8 | 30.7 | 7365.2 | 43.2 | 30.7 | 4119.1 | 43.2 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_B3_P4 | 4 | -2.1 | -4156.8 | -96.2 | 32.2 | -1706.7 | -30.2 | nan | nan | nan | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_B4_ST | 6 | -2.6 | 282.0 | -9.9 | -9.1 | 396.3 | -16.8 | -9.1 | -1253.3 | -16.8 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_B4_R8A | 6 | -9.5 | -2048.5 | -11.2 | 24.2 | 803.4 | 23.1 | 24.2 | -287.2 | 23.1 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_B4_R8C | 43 | -5.8 | -1049.6 | -5.5 | 26.1 | 789.8 | 26.3 | 26.1 | 51.3 | 26.3 | 8.1 | 460.1 | 8.4 | -10.6 | 227.2 | -10.3 | 5.2 | -50.2 | 5.4 |
| WB_B4_STR8C | 6 | -4.2 | -274.4 | -5.4 | 24.4 | 923.8 | 23.6 | 24.4 | -218.2 | 23.6 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_B5_P7_4560 | 6 | 0.0 | 1995.4 | 8.4 | 5.5 | 1256.6 | 13.4 | 5.5 | 1556.1 | 13.4 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_B5_P_T90 | 6 | -7.2 | -1036.3 | -11.0 | -6.0 | -1176.8 | -9.7 | -6.0 | -590.4 | -9.7 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_B5_P_T45 | 6 | 14.0 | 4219.7 | 4.5 | 42.9 | 1159.7 | 36.6 | 42.9 | -2025.9 | 36.6 | nan | nan | nan | nan | nan | nan | nan | nan | nan |

Exact notes: WB_C_NONE = P7 cut off (43 months). WB_B2_REG15 = cut off when atr_rel >= 1.5. WB_B2_STK5 = cut off when stack Calmar5 >= 1 (40 of 43 months; X' column is from the months shown only when the window is complete). WB_B2_FPRI = cut active only when the prior day trended (7 months). WB_B3_P4 = P7 `profit P7 * pct>=0.7 pulled_against_mult>=5 tighten 10 win=5 persist=1` ON in chop (hot1.3 and ER20 >= 0.30 false), 4 months, no complete window yet. WB_B4_* = K7/P7/M7 near-target / retarget; WB_B5_* = P7 brackets (L6M).

## 3. Live-week replay summary (frozen week; flag state at the signal second; hold-to-bracket counterfactual; data /mnt/l2/l2vast/_works_b/live_cut_replay.csv)
Cuts by book and kind (hold minus live, dollars): see section 0 item 4. P7 lines flagged per cut: of the 7 recoveries (rows 11-03 x2, 11-04 x3, 11-05 x2) atr_rel >= 1.3 was true on 5, ER20 >= 0.30 on 3, hot and ER20 on 2; of the 17 saves atr_rel >= 1.3 was true on 9, ER20 >= 0.30 on 6. The flag would have switched off 5 of the 7 recovery cuts and 9 of the 17 saves (REG), i.e. it does not keep the saves.

## 4. Missing
11-09..11 live trades and shadow P&L; MBO state days after 11-05 (NQ OHLCV 1-min to 11-10 only). Exact conditional sets still queued: WB_B2_ERLOT, WB_B2_FER (reverse control), WB_B3_P1/P2/P3, other windows of WB_B2_FPRI and WB_B3_P4; first-order K7/M7 conditional cut not run exact.
