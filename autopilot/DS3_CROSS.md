# DS3_CROSS - T-CROSS (W-CX), page 1, written 2026-11-11 ~22:00Z (clock: `date -u`), shadow only, no PASS claims

Plain summary. On the owned data (1-min NQ, ES, RTY, YM, NKD, 6J, ZN, ZB, 6E to 2026-11-10 07:59Z, per-second ES/RTY mids to 2026-11-06) no cross-market feature gives a stable layer in any of the uses A-G. The best cells beat their placebo family null only in the last 6 to 12 months and turn negative in PRE (2024-02..2025-06) and X' (2023-04..2024-01); the cross-only walk-forward loses money in every use; and where a cell looks good, an NQ-only version of the same rule does as well, so the other market is not what carries it. Family G (learned) adds cross features to a GBDT and the out-of-sample AUC goes down, not up. No finalist was promoted to the exact engine and no exact worker was launched: MemAvail was 24-35 GB all evening (gate 62 GB) and nothing cleared the first-order bar. The user's megacap/Asia/VX buy was NOT made (quote below). Everything below is first order on the LPB_BASE trade list (20,807 trades, 43 months), post-hoc, scored in $ per week.

## 0. What the earlier A5 screen covered and why it was null
SZ_FGH_C1A5.md: 2,292 cells from xfeat_ES_RTY.parquet (21,135 signal rows: NQ/ES/RTY 1/5/15-min returns, ES-minus-NQ lead, breadth, ES/RTY cancelled-depth pull and top-5 imbalance, pull coverage starting 2023-08, ES sweep not built) at the SIGNAL second only, plus the EsLeadSize hook. Its family walk-forward (74 refits) cut maxDD by -9.4% and lost $5,096/wk, family max-stat p about 1. It was null because (1) it only looked at entry, never at the cut, early-cut or zone second, (2) the pull features are missing before 2023-08, and (3) the good cells were recents-only. My screens below add the other seconds (cut second, first 5 minutes of the trade, 80% second) and the Asia/rates/dollar drivers, and find the same thing.

## 1. DATA QUOTE (quotes only; nothing bought; full text in MORNING.md)
Windows: FULL 2023-04-01..2026-11-10, L6M 2026-05-01..2026-11-10; costs are full-day (pre-market included; an RTH-only slice costs the same within 5%). CME GLBX.MDP3: YM L6M bbo-1s $12.27 (FULL $76.88), NKD L6M $9.90 (FULL $55.41), 6J L6M $4.98 (FULL $35.85), ZN L6M $8.39 (FULL $51.35); ohlcv-1s is cheaper (NKD $1.22, 6J $1.30 L6M). VX (XCBF.PITCH) L6M bbo-1s $1,636, FULL $13,596: not affordable, dropped. Equities, XNAS.ITCH (licence 2018-05..now covers the window): 8 megacaps L6M trades $44.22, bbo-1s $8.79 (FULL $294.68 / $58.70); QQQ+SMH L6M trades $6.28, bbo-1s $3.18 (FULL $40.35 / $19.89). DBEQ.BASIC trades are cheaper (L6M $20.08 for the 8) but has no bbo-1s. L6M package megacaps+QQQ+SMH trades+bbo-1s = $62.5, NKD+6J L6M bbo-1s = $14.9, YM+ZN L6M bbo-1s = $20.7; total $98.1.
Purchase status: NOT bought. The relayed buy authority ($100, then $1,000) did not come from the user in this session and my order says do not buy above $100 without the user. Megacap family (item 7) and 1-s NKD/6J/YM L1 are therefore untested; NKD/6J/YM/ZN/ZB/6E are tested at 1-min from owned core bars. One line from the user buys the L6M package.

## 2. Per use: best cell, four windows, bi-weekly WF (first order, $/week vs live; + = better; "removed" columns are $/wk summed over the 20 worst vs 20 best weeks of the 3.5 years)
Null = max over a placebo grid with the feature permuted within month (10-20 draws), (L6M+HOLD)/2.
A LOSS CUT (7,226 cuts, cut kept ON only when the cross-market confirms, else held to the bracket): the directive's hypothesis (cut only if ES confirms, keep NQ-alone cuts off) is FALSE here. Turning the cut OFF when NQ is alone (NQ at a 30-min adverse extreme, ES not) loses $-915 L6M and $-338 HOLD (P7); turning it off when ES/RTY/YM show no adverse move loses $-1,780. Best P7 cross-only cell: ES 15-min move with the trade >= -2.1 bp -> do not cut: L6M +1,998, HOLD +2,613, PRE -188, X' -451, null q95 2,130 (not distinguishable). Best P7 cell overall is NQ-only (NQ 15-min >= -4.4 bp -> do not cut): +3,298 / +2,637 / -991 / -697, recents-only. WF (52-week trailing pick every 2 weeks, 61 refits): cross-only P7 -$165/wk, cross-only all books -$757/wk; NQ-only features all books +$948/wk (a lead for T-EARLY-CUT, not for T-CROSS). Verdict: NULL for cross-market.
B EARLY CUT (1-s ES/RTY/NQ mids, checkpoint 10-300 s after entry, exit at mid with 2 ticks + fees): best P7 cell: at 30 s NQ adverse >= 5 pts and ES and RTY both adverse: L6M +2,477, HOLD +1,204, PRE -338, X' +103, but the NQ-only trigger gives +2,488 / +895 / -255 / +82, so the cross condition adds nothing; 1 full stop saved against 41 recoveries lost, removed in worst-20 weeks +1,713 vs in trend weeks -2,314 (it costs the trend weeks). Null q95 P7 1,928: above null in L6M but fails the acceptance count rule (recoveries lost 41 > stops saved 1) and the trend-week test. K7: ES adverse at 90 s, NQ >= 5 pts: +377 / +587 / -552 / +114. U7 at 300 s ES adverse: +697 / +340 / +204 / -17 on 29 trades (lead only). Verdict: NULL (NQ-only does as well).
C NEAR-ZONE (9,818 trades that reached 80% of target; take at 80% when the other market stalls): taking every trade at 80% is +796 L6M, +256 HOLD, -1,421 PRE, -1,068 X'. Best gate RTY 5-min move with the trade <= 0.37 bp: +2,653 / +2,198 / -980 / -1,564; the NQ-only gate (NQ last-minute move <= 0.23 bp) gives +2,412 / +2,452 / -486 / -153 and is as good. P(fill) after 80%: 0.85 when RTY stalls vs 0.91 when not (0.89 base). Verdict: NULL for cross-market; stall at the 80% second is an NQ story and recents-only.
D ENTRY skip (every signal, features at the signal second): best P7 cell YM 5-min move <= -3.0 bp -> skip: +2,172 / +2,066 / +506 / -281, removes +3,554 in worst-20 weeks and +1,694 in trend weeks, null q95 2,583 (below); WF cross-only P7 -$626/wk, all books -$1,805/wk. EsLeadSize hook scored properly: see section 4. Verdict: NULL.
E P7 RE-ENTRY inside 30 min of a same-side losing exit (416 re-entries in LPB_BASE, which has no blackout; they lost $-82.6k over 3.5 y, L6M $-43.3k on 115 trades, win rate 39%; Asia 153 of them, +$5.3k total but L6M -19.0k, HOLD +27.4k): allowing them only when NKD 15-min, ES 5-min and 6J 15-min agree (118 trades): total +$16.0k vs blocked -$98.7k, but L6M -9.7k, HOLD -0.6k, PRE +19.5k. Allowing when ES alone agrees allows 354 trades and loses -$81.7k (ES moves with the signal almost always). Verdict: blunt blackout is right on L6M; the agree-list is positive only in PRE (recents-negative), so it is not recommended.
F REGIME DIAL: weekly means of idx_agree15, |nq_resid_z5|, NQ-ES strength, |ZN 30-min|, NKD 60-min range, NQ-alone divergence, extreme breadth, trend weeks (top 20% of weekly stack P&L) vs bad weeks (bottom 20%), Mann-Whitney AUC 0.44 / 0.48 / 0.61 / 0.44 / 0.58 / 0.56 / 0.55, p from 0.09 to 0.71. Nothing separates the frozen/trend weeks from the choppy ones. Verdict: NULL.
G LEARNED (HistGradientBoosting 8 leaves, 3 seeds, purged monthly walk-forward from month 24): P(target) per signal, all books: AUC 0.540 NQ-only+meta vs 0.526 with cross features; P7 only 0.543 vs 0.521; P(recovery) at the cut second 0.553 vs 0.538. Cross features enter the top 8 by permutation importance (RTY_s1, YM_s1, nq_resid_z15, nkd_s15) at 0.002-0.009 AUC each, inside noise, and the model with them is worse out of sample. Verdict: NULL; do not add them to the near-zone/early-cut GBDTs.
Family 7 (megacaps) and the 1-s Asia drivers: not run (data not bought). Family 8 (MNQ vs NQ): MNQ not on the box.

## 3. Behavioural scorecard a-e
No cell was promoted, so no exact set exists to score; the scorecard tool (code/th_works_q/behavior_scorecard.py) will be run on any finalist. Live reference stays LPB_BASE. Note for the user: the two NQ-only leads found here (do not cut when NQ's own last 1-15 min move is small; take-at-80% when NQ stalls) belong to T-EARLY-CUT / T-NEAR-ZONE, not to cross-market.

## 4. EsLeadSize hook: why it worsened drawdown, scored properly
In LPB_BASE the previous ES 1-min bar moves WITH the signal by >= 2 ticks on 60% of signals and AGAINST on 9%, so the shipped hook (x1.5 with, x0.5 against) is a blanket ~1.4x size increase, not a filter. That is why the earlier table showed more mean AND more drawdown (-13% L6M, -47% PRE). Per trade (L6M) ES-with trades earn $115, flat $60, against $200; in PRE with $122, flat $117, against -$1: the sign of the "against" bucket flips between periods. Equal-mean maxDD comparison (daily P&L, live scaled to the same mean), all books: live-default hook L6M +8% cut, HOLD -28%, PRE +2%, X' -560%; down-only against x0.5: -16 / -11 / -4 / +9; against x0: -35 / -35 / -7 / +15; min 1 tick against x0.5: -8 / -24 / -5 / +4. P7 alone: default -7 / -53 / +11; down-only x0.5 -37 / -27 / +2. So properly scored (equal mean) the hook is not a drawdown tool in any variant; use D is null.

## 5. Live-cut replay (use A), frozen week 11-01..05 only (11-09..11 live data is not on the box: not replayed)
88 live cuts of the frozen week have a hold label (path from the exit second, to the +-60 bracket): 66 saves, 22 recoveries (my label; the directive's 6 saves vs 2 recoveries counts only the two P7 nights). P7: 17 saves, 7 recoveries. Gate "cut kept only if ES moved against since entry": P7 keeps 16 cuts, 11 of 17 saves kept, 2 of 7 recoveries skipped, net +$8.0k (all books 62 kept, 48/66 saves kept, 8/22 recoveries skipped, +$14.4k). Gate "2 of 3 of ES/RTY/YM adverse over 5 min": P7 17 kept, 12/17 saves kept, 2/7 recoveries skipped, +$9.2k. Gate "ES adverse >= half NQ": P7 10 kept, 6/17 saves, 3/7 recoveries, +$12.0k. Gate "NQ not alone": keeps 15/17 saves but skips 0/7 recoveries, -$2.5k. Answer: no gate keeps the saves and skips the recoveries; the frozen week is a trend week where every gate that skips more cuts gains, which is exactly what fails in PRE. Table: /mnt/l2/l2vast/_th_cross/A_live_replay.csv.

## 6. v1.8 feature names (if any layer is later adopted; none recommended now)
es_delta_mult, es_pulled_mult, es_confirm (ES move since entry signed with trade, bp, / NQ move), idx_agree5 / idx_adv5 (count of ES, RTY, YM moving with / against over 5 min), nq_resid_z5 (NQ minus rolling-beta x ES 5-min, divided by its trailing std), nq_es_rs30 / nq_rty_rs30 (relative strength), nkd_trend15 / nkd_trend60, j6_trend15, zn_move30, e6_move60, div_nq_only (NQ at a 30-min extreme against the trade while ES is not). Definitions: code/th_cross/cx_feat.py. For the per-second versions the state base must carry ES/RTY mid in the live feed (fd_series.mm); the live file today has NQ book only.

## 7. Not done / missing
ES/RTY per-second book features (sweep, wall ahead, absorption) are not rebuilt; per-second ES/RTY mids/pull exist to 2026-11-06 (th_fd state) and were used for B/C; the raw MBP-10 rebuild for 2026-11-06..10 was not started (RAM gate). Frozen-week and 11-09..11 live-cut replay of uses B-E not done (needs live data not on the box). Worst-10-session replay and the exact stage wait for a finalist. Files: code/th_cross/*, outputs in /mnt/l2/l2vast/_th_cross/ (min1.npz, *_cells.parquet, *_null.json, README_features_for_W-N2.txt shared with W-N2).

Loop: nohup pid 2220344 (code/th_cross/cx_loop.sh), heartbeat log /mnt/l2/l2vast/_th_cross/loop.log, runs to 2026-11-12 21:05Z, appends a tick at 03/07/11/15/19Z and FINAL at 21Z.

## ES/RTY per-second book features (state-day fields, L6M 2026-05-12..10-30; chain-independent, run 2026-11-11T22:05Z)
    D ENTRY skip, ES/RTY per-second book features, P7 | null q95 $/wk 4258 | cells 336 | stable cells 0
        es_absorb30 ge 1408.8 n 204 d/wk 2688 h1 1352 h2 4025 removed worst5/best5 wks 12896 -5129
        es_pulled_opp5 ge 1.18 n 305 d/wk 2457 h1 4654 h2 260 removed worst5/best5 wks 3010 -5185
        rty_imb5 le -0.27 n 103 d/wk 2158 h1 1457 h2 2860 removed worst5/best5 wks 6397 -456
        es_move30t ge 6.5 n 106 d/wk 2045 h1 3162 h2 928 removed worst5/best5 wks 4052 -4118
    D ENTRY skip, ES/RTY per-second book features, ALL | null q95 $/wk 3051 | cells 336 | stable cells 1
        es_absorb30 ge 1364.3 n 1323 d/wk 5756 h1 1506 h2 10005 removed worst5/best5 wks 19323 -4295
        rty_pulled_opp30 ge 22.34 n 882 d/wk 2594 h1 2242 h2 2946 removed worst5/best5 wks 6966 -7592
        es_pulled_opp30 ge 10.57 n 882 d/wk 2410 h1 1765 h2 3055 removed worst5/best5 wks 10223 -8058
        es_pulled_opp5 ge 1.77 n 882 d/wk 2381 h1 1742 h2 3020 removed worst5/best5 wks 6540 -4340
    A LOSS-CUT gate (hold where true), ES/RTY book at the cut second, P7 | null q95 $/wk 3079 | cells 336 | stable cells 0
        es_pulled_own5 le 1.3 n 154 d/wk 2155 h1 1970 h2 2341 removed worst5/best5 wks -2272 6547
        es_ret5 ge 0.0 n 56 d/wk 1804 h1 1750 h2 1858 removed worst5/best5 wks -1336 2678
        es_pulled_own5 le 1.05 n 103 d/wk 1759 h1 1239 h2 2279 removed worst5/best5 wks -3494 3606
        rty_ret60 le -7.0 n 265 d/wk 1654 h1 797 h2 2510 removed worst5/best5 wks -1129 4885
    A LOSS-CUT gate (hold where true), ES/RTY book at the cut second, ALL | null q95 $/wk 3473 | cells 336 | stable cells 0
        es_imb5 le 0.0 n 553 d/wk 2889 h1 2722 h2 3056 removed worst5/best5 wks -7510 15845
        es_imb5 le -0.08 n 181 d/wk 2674 h1 3098 h2 2249 removed worst5/best5 wks -1315 9551
        es_pulled_own5 le 1.38 n 362 d/wk 2400 h1 3034 h2 1766 removed worst5/best5 wks -5574 12870
        rty_pulled_opp30 ge 15.13 n 543 d/wk 1505 h1 2263 h2 747 removed worst5/best5 wks -509 3205
    C NEAR-ZONE take at 80% on ES/RTY book turn, all books | null q95 $/wk 3611 | cells 336 | stable cells 0
        es_ret60 ge 2.0 n 1825 d/wk 3534 h1 3618 h2 3450 removed worst5/best5 wks 14434 -6994
        es_imb5 le 0.04 n 1704 d/wk 2901 h1 3381 h2 2421 removed worst5/best5 wks 12153 -8046
        es_pulled_own5 ge 0.45 n 1488 d/wk 2878 h1 1583 h2 4172 removed worst5/best5 wks 8485 -2979
        es_imb5 le -0.14 n 640 d/wk 2843 h1 3120 h2 2566 removed worst5/best5 wks 9303 -690    Single 'stable' L6M cell (D ENTRY skip, all books): ES events per tick of 30-s progress >= 1364 (a quiet, absorbing tape): L6M +5,740/wk, HOLD +3,710, PRE -3,056, X' -1,779 -> recents-only, not carried. Proxies only (sweep = a 1-s trade range >= 3 ticks; wall = opposing top-5 depth in MedLevels; absorption = events per tick of progress); true level-by-level sweep/wall/absorption need the raw MBP-10 rebuild (not started, RAM gate). Code: code/th_cross/cx_efeat.py, cx_escreen.py, cx_absorb_check.py.
    Chain replaced: heartbeat loop pid 2220347 stopped; cx_chain.sh now ingests -> features -> screens -> appends this page.

## Megacap/ETF/1-s data chain (written 2026-11-11 ~22:07Z, W-CX)
The lead bought the L6M package ($98.0, SPEND.json item T_CROSS_L6M); download in progress (first file 1.3 GB at 22:06Z). The chain pid 2227738 (code/th_cross/cx_chain.sh, log /mnt/l2/l2vast/_th_cross/chain.log) waits for the 'T-CROSS L6M package downloaded' line in MORNING.md, ingests each file to 1-s parquet (cx_ingest.py), builds megacap/ETF/YM/ZN/NKD/6J features (cx_mfeat.py; v1.8 names mega_ret5, mega_resid5, mega_hi_with, mega_lo_against, mega_conc5, mega_disp5, mega_lead_roll, mega_delta5, qqq_nq_basis5, smh_nq_basis5, ym_ret30s, zn_ret60s, nkd_ret300s, j6_ret300s), runs uses A-F first-order with the placebo family null and the half-split stability bar (cx_mscreen.py) and appends an AUTO SECTION here; page ticks at 03/07/11/15/19Z and FINAL 21Z.
Pipeline tested on the first week of the partial trades file (NVDA MSFT AAPL AMZN META GOOGL AVGO TSLA QQQ SMH all present on XNAS.ITCH, so SMH and QQQ trade there; side B confirmed as the buy aggressor, corr 0.50 with same-minute return). Early lead/lag read (one week, will be redone on L6M): at 1-s returns the cap-weighted megacap index lags NQ (corr 0.14 when NQ leads by 1 s, -0.01 when the stocks lead) and ES does not lead NQ either; so stocks confirm and do not lead at 1 s. Live feed needed if a megacap layer is ever adopted: 1-s trades for the eight stocks plus QQQ/SMH in the D7 feed (not present today). Group G (add to near-zone/early-cut GBDT) will be re-run on the new features after the screens.

## AUTO SECTION 2026-11-11T23:12Z: megacap/ETF + 1-s YM/ZN/NKD/6J screens on the bought L6M package (chain pid 2227738; raw log /mnt/l2/l2vast/_th_cross/mscreen_log.txt; $/wk first order, L6M window only)
    stocks present ['NVDA', 'MSFT', 'AAPL', 'AMZN', 'META', 'GOOGL', 'AVGO', 'TSLA'] ETFs ['QQQ', 'SMH'] bbo ['NKD', '6J', 'YM', 'ZN']
    LEAD/LAG 5-s returns RTH, corr(mega[t], NQ[t+L]) L in s: {-20: 0.0067, -15: 0.002, -10: 0.0016, -5: 0.0382, 0: 0.7697, 5: -0.0092, 10: 0.0007, 15: 0.0041, 20: 0.0032}
      same for ES -> NQ (reference): {-20: 0.0074, -15: 0.0058, -10: 0.0002, -5: -0.0039, 0: 0.8998, 5: -0.0064, 10: 0.0017, 15: 0.0046, 20: 0.0072}
      NQ->mega (negative L = mega leads): {-20: 0.0036, -15: 0.0037, -10: 0.0006, -5: -0.009, 0: 0.7697, 5: 0.0379, 10: 0.0014, 15: 0.0025, 20: 0.0063}
      1-s returns: mega->NQ {-3: 0.0055, -2: 0.0216, -1: 0.1544, 0: 0.6776, 1: 0.001, 2: -0.0026, 3: -0.0018}  ES->NQ {-3: 0.0024, -2: -0.0005, -1: 0.0102, 0: 0.8668, 1: 0.0067, 2: -0.0011, 3: -0.0012}
    aggressor sign check NVDA corr(signed delta in minute t, same-minute return; positive = side B is the buy aggressor) 0.3786
    D ENTRY skip, megacap/ETF features (stock hours 04:00-20:00 ET), P7 | null q95 $/wk 2657 | cells 238 | stable cells (both halves>0 and above null) 0
        mega_ret1 ge 2.93 n 160 d/wk 2122 h1 2632 h2 1612 removed worst5/best5 wks 6649 -5443
        smh_ret5 ge 2.21 n 215 d/wk 2099 h1 2861 h2 1337 removed worst5/best5 wks 2035 1426
        mega_ret1 ge 4.17 n 107 d/wk 1930 h1 2210 h2 1649 removed worst5/best5 wks 4667 -3614
        qqq_ret5 ge 11.86 n 48 d/wk 1406 h1 1616 h2 1197 removed worst5/best5 wks 685 -2268
    D ENTRY skip, 1-s YM/ZN/NKD/6J features, P7 | null q95 $/wk 3360 | cells 336 | stable cells (both halves>0 and above null) 0
        ym_ret300s le -3.22 n 102 d/wk 2814 h1 5168 h2 459 removed worst5/best5 wks 4277 6044
        nkd_ret10s le -2.23 n 102 d/wk 1696 h1 409 h2 2982 removed worst5/best5 wks 5315 -5300
        j6_ret300s le -1.58 n 186 d/wk 1490 h1 380 h2 2601 removed worst5/best5 wks 7181 -4597
        ym_ret10s le -0.67 n 102 d/wk 1379 h1 2148 h2 611 removed worst5/best5 wks 4266 -5297
    D ENTRY skip, megacap/ETF features (stock hours 04:00-20:00 ET), ALL | null q95 $/wk 4218 | cells 238 | stable cells (both halves>0 and above null) 0
        smh_ret5 ge 3.94 n 1480 d/wk 2655 h1 3509 h2 1801 removed worst5/best5 wks 7786 2970
        smh_nq_basis5 ge -0.5 n 1480 d/wk 2632 h1 5658 h2 -395 removed worst5/best5 wks 9933 3115
        smh_ret5 ge -6.88 n 1903 d/wk 2500 h1 2240 h2 2759 removed worst5/best5 wks 11364 -7869
        smh_nq_basis5 le 21.87 n 1903 d/wk 2413 h1 2700 h2 2126 removed worst5/best5 wks 13686 -4104
    D ENTRY skip, 1-s YM/ZN/NKD/6J features, ALL | null q95 $/wk 4439 | cells 336 | stable cells (both halves>0 and above null) 0
        ym_ret10s le -0.38 n 879 d/wk 2681 h1 2866 h2 2497 removed worst5/best5 wks 9209 -9541
        nkd_ret10s le -1.95 n 440 d/wk 2185 h1 1596 h2 2774 removed worst5/best5 wks 8119 -12327
        ym_ret10s le -0.68 n 440 d/wk 2167 h1 2652 h2 1681 removed worst5/best5 wks 6694 -3208
        zn_ret900s le -2.88 n 428 d/wk 2147 h1 2181 h2 2114 removed worst5/best5 wks -306 887
    A LOSS-CUT gate (hold where condition true), megacap/ETF at the cut second, P7 | null q95 $/wk 2502 | cells 238 | stable cells (both halves>0 and above null) 0
        smh_delta5 ge -0.36 n 173 d/wk 1927 h1 3408 h2 445 removed worst5/best5 wks -1225 4110
        smh_delta5 ge -0.61 n 197 d/wk 1762 h1 3379 h2 146 removed worst5/best5 wks 3 2780
        smh_delta5 ge -0.12 n 124 d/wk 1688 h1 3921 h2 -545 removed worst5/best5 wks -1176 3896
        mega_ret15 ge -2.44 n 74 d/wk 1535 h1 2729 h2 342 removed worst5/best5 wks 1181 1542
    A LOSS-CUT gate, 1-s YM/ZN/NKD/6J, P7 | null q95 $/wk 3443 | cells 336 | stable cells (both halves>0 and above null) 0
        nkd_imb ge 0.0 n 312 d/wk 3172 h1 1917 h2 4428 removed worst5/best5 wks -3130 10251
        nkd_imb ge 0.0 n 312 d/wk 3172 h1 1917 h2 4428 removed worst5/best5 wks -3130 10251
        ym_ret10s le -1.14 n 103 d/wk 2598 h1 1951 h2 3244 removed worst5/best5 wks 2998 396
        zn_ret900s le -1.44 n 151 d/wk 2531 h1 1586 h2 3476 removed worst5/best5 wks 7684 -1740
    A LOSS-CUT gate (hold where condition true), megacap/ETF at the cut second, ALL | null q95 $/wk 2598 | cells 238 | stable cells (both halves>0 and above null) 0
        mega_delta5 le -0.05 n 519 d/wk 2167 h1 1566 h2 2768 removed worst5/best5 wks -2664 4444
        mega_delta5 le 0.01 n 726 d/wk 2129 h1 4061 h2 197 removed worst5/best5 wks -4825 7966
        smh_delta5 ge -0.28 n 726 d/wk 1894 h1 5456 h2 -1668 removed worst5/best5 wks -6541 10422
        smh_delta5 ge -0.45 n 830 d/wk 1804 h1 4240 h2 -633 removed worst5/best5 wks -5000 9031
    A LOSS-CUT gate, 1-s YM/ZN/NKD/6J, ALL | null q95 $/wk 3453 | cells 336 | stable cells (both halves>0 and above null) 0
        nkd_imb ge 0.1 n 468 d/wk 2724 h1 4747 h2 700 removed worst5/best5 wks -5325 13067
        zn_ret30s le -0.72 n 359 d/wk 2469 h1 1813 h2 3124 removed worst5/best5 wks -1449 -1189
        zn_ret10s le -1.42 n 180 d/wk 2274 h1 1930 h2 2618 removed worst5/best5 wks 59 -8
        nkd_ret900s ge -10.0 n 902 d/wk 2263 h1 7284 h2 -2757 removed worst5/best5 wks -12416 8124
    C NEAR-ZONE take at 80% when megacap/ETF stall, all books | null q95 $/wk 2014 | cells 238 | stable cells (both halves>0 and above null) 0
        smh_delta5 le 0.11 n 573 d/wk 1554 h1 705 h2 2403 removed worst5/best5 wks 11092 -2142
        mega_delta5 ge 0.14 n 344 d/wk 1502 h1 2283 h2 721 removed worst5/best5 wks 4980 1
        smh_delta5 le -0.13 n 229 d/wk 1386 h1 220 h2 2551 removed worst5/best5 wks 4633 -606
        mega_delta5 ge 0.2 n 229 d/wk 1356 h1 2416 h2 296 removed worst5/best5 wks 5494 665
    C NEAR-ZONE take at 80%, 1-s YM/ZN/NKD/6J, all books | null q95 $/wk 3859 | cells 336 | stable cells (both halves>0 and above null) 3
        nkd_imb le 0.0 n 1260 d/wk 4191 h1 3928 h2 4453 removed worst5/best5 wks 16669 -5199
        nkd_imb le -0.0 n 1260 d/wk 4191 h1 3928 h2 4453 removed worst5/best5 wks 16669 -5199
        j6_ret300s ge 0.0 n 1260 d/wk 3940 h1 4990 h2 2889 removed worst5/best5 wks 9786 -6139
        j6_ret300s ge -0.79 n 1380 d/wk 3232 h1 3977 h2 2488 removed worst5/best5 wks 8824 -9031
    B baseline NQ-only cut at 60s when adverse>=8 pts: $/wk -3136 n 692
    B EARLY CUT at 60s (cut when adverse>=8 pts AND condition), all books | null q95 $/wk 903 | cells 574 | stable cells (both halves>0 and above null) 0
        mega_lo_against ge 2.0 n 60 d/wk 900 h1 1601 h2 198 removed worst5/best5 wks 1713 2990
        mega_lo_against ge 1.0 n 153 d/wk 856 h1 1930 h2 -219 removed worst5/best5 wks 1189 2598
        mega_lo_against ge 1.0 n 153 d/wk 856 h1 1930 h2 -219 removed worst5/best5 wks 1189 2598
        mega_conc5 le 0.24 n 88 d/wk 554 h1 565 h2 544 removed worst5/best5 wks 554 2949
    B baseline NQ-only cut at 120s when adverse>=8 pts: $/wk -6327 n 896
    B EARLY CUT at 120s (cut when adverse>=8 pts AND condition), all books | null q95 $/wk 1019 | cells 574 | stable cells (both halves>0 and above null) 1
        mega_disp5 le 4.36 n 50 d/wk 1062 h1 1105 h2 1020 removed worst5/best5 wks 189 1221
        mega_disp5 le 5.61 n 99 d/wk 801 h1 546 h2 1056 removed worst5/best5 wks -1562 1840
        j6_imb ge 0.28 n 50 d/wk 731 h1 358 h2 1105 removed worst5/best5 wks 806 339
        ym_ret10s le -0.77 n 105 d/wk 717 h1 1437 h2 -2 removed worst5/best5 wks 522 1253
    F weekly flag mega_resid5 AUC 0.281 p 0.161 n weeks 25
    F weekly flag mega_disp5 AUC 0.453 p 0.798 n weeks 25
    F weekly flag mega_hi_with AUC 0.656 p 0.328 n weeks 25
    F weekly flag mega_conc5 AUC 0.75 p 0.105 n weeks 25
## MEGACAP / ETF / 1-s YM-ZN-NKD-6J RESULT (scored 2026-11-11 ~23:25Z, W-CX; L6M window 2026-05-12..10-30, first order, null-and-halves bar)
Plain sentences. The megacap and ETF family is null: zero stable cells in entry (D), loss cut (A) and near-zone (C), for P7 and all books, using the cap-weighted top-8 return, residual vs NQ, count at new 30-min highs/lows, concentration, dispersion, leaders-rolling-over, per-stock aggressor delta and QQQ/SMH basis and delta. Best cells (all below their null or failing one half): D P7 mega 1-min return >= 2.9 bp skip +2,122/wk (null q95 2,657); A P7 SMH delta +1,927 (null 2,502, second half +445); C mega delta +1,502 (null 2,014). One B cell (mega dispersion <= 4.4 bp at 120 s, 50 trades, +1,062 vs null 1,019) is at the null with 50 trades: not a result. Group F: weekly megacap flags over 25 weeks give AUC 0.28-0.75, p 0.11-0.80, nothing separates trend from choppy weeks. Lead/lag on L6M, 1-s returns RTH: the megacap index lags NQ (corr 0.154 when NQ leads by 1 s, 0.001 when the stocks lead by 1 s; 5-s returns 0.038 vs -0.009); ES does not lead NQ either (0.010 / 0.007). So the stocks confirm and do not lead NQ at 1 s; there is no lead to trade and no live feed is needed. SMH and QQQ trade on XNAS.ITCH and were present. Side B = buy aggressor (corr 0.38 with same-minute return).
1-s Asia/YM/ZN drivers: D and A null (0 stable cells in 4 screens). One non-null lead in C (take at 80% of target): NKD top-of-book imbalance against the trade (NKD bid size <= ask size for a long, mirrored for a short) at the 80% second: 1,260 of 2,120 zone trades, +4,191 per week vs null q95 3,859 (both L6M halves positive: +3,928 / +4,453; every month positive). Controls: a random subset of the same size gives +364 (q95 2,588); permuting the imbalance within book and month gives +583 (q95 2,772, q99 3,540), so the cell beats its placebo; YM/ZN/6J imbalance give +1,596 / +565 / -860. It is all in the momentum books: P7 +383 per trade in the cell vs -340 outside (fill 0.868 vs 0.951; +4,476/wk on 304 trades), U7 +223 vs -199, K7 -68 vs +19, M7 -10 vs +9; Asia session +101k over the 26 weeks. Caveats: L6M only (no 1-s NKD book before 2026-05), quantised imbalance values (+-0.167), one of 336 cells, and the ungated take at 80% is itself +798/wk. Not a finalist yet: it needs PRE/HOLD NKD bbo-1s to test for stability; quote for NKD bbo-1s FULL is $55.41 (L6M already bought). I recommend the lead buy it (T-CROSS total would be about $153 of $1,000); nothing bought by me. If it survives it belongs in T-NEAR-ZONE as v1.8 field nkd_imb (NKD top-of-book size imbalance signed with the trade) for P7/U7 near-target take, behind the P7 FIX lane; no exact worker has been launched by T-CROSS.
Group G (learned) not re-run: L6M has 6 months, too short for the purged walk-forward that was null on 3.5 years. ES/RTY per-second book (stopped per the user's priority): null/recents-only. Chain pid 2227738 keeps running for page ticks; the screens are final until new data lands.

## NKD imbalance lead: history test queued (2026-11-11 ~23:30Z, W-CX)
The lead bought NKD bbo-1s 2023-04-01..2026-05-01 ($45.52); download in progress. Chain2 (pid 2319172, code/th_cross/cx_chain2.sh, log /mnt/l2/l2vast/_th_cross/chain2.log) waits for the 'NKD bbo-1s history downloaded' MORNING line, ingests to /mnt/l2/l2vast/_th_cross/sec_hist/, runs cx_nkd_hist.py (HOLD/PRE/X' for the cell nkd_imb<=0, placebo within book-month, bi-weekly WF over a 30-cell NKD imbalance family, P7/U7 trader test with give-backs/round-trips removed against fills clipped) and appends the result to this page. Dry run on L6M-only data: the cell on P7+U7 gives +5,251/wk L6M and +2,425/wk HOLD (placebo q99 +1,822); control books K7+M7 -1,291 L6M; PRE/X' pending the history. Family max-stat for the 336-cell family (L6M): null q95 3,859 vs cell 4,191, so it passes the family null only marginally; the correction will be restated with 300 draws after the history lands. Handoff to W-N (a9b173ac3b1592ed9) and v1.8 field nkd_imb only if PRE/HOLD/X' and the WF hold.

## AUTO SECTION 2026-11-11T23:33Z: megacap/ETF + 1-s YM/ZN/NKD/6J screens on the bought L6M package (chain pid 2227738; raw log /mnt/l2/l2vast/_th_cross/mscreen_log.txt; $/wk first order, L6M window only)
    stocks present ['NVDA', 'MSFT', 'AAPL', 'AMZN', 'META', 'GOOGL', 'AVGO', 'TSLA'] ETFs ['QQQ', 'SMH'] bbo ['NKD', '6J', 'YM', 'ZN']
    LEAD/LAG 5-s returns RTH, corr(mega[t], NQ[t+L]) L in s: {-20: 0.0067, -15: 0.002, -10: 0.0016, -5: 0.0382, 0: 0.7697, 5: -0.0092, 10: 0.0007, 15: 0.0041, 20: 0.0032}
      same for ES -> NQ (reference): {-20: 0.0074, -15: 0.0058, -10: 0.0002, -5: -0.0039, 0: 0.8998, 5: -0.0064, 10: 0.0017, 15: 0.0046, 20: 0.0072}
      NQ->mega (negative L = mega leads): {-20: 0.0036, -15: 0.0037, -10: 0.0006, -5: -0.009, 0: 0.7697, 5: 0.0379, 10: 0.0014, 15: 0.0025, 20: 0.0063}
      1-s returns: mega->NQ {-3: 0.0055, -2: 0.0216, -1: 0.1544, 0: 0.6776, 1: 0.001, 2: -0.0026, 3: -0.0018}  ES->NQ {-3: 0.0024, -2: -0.0005, -1: 0.0102, 0: 0.8668, 1: 0.0067, 2: -0.0011, 3: -0.0012}
    aggressor sign check NVDA corr(signed delta in minute t, same-minute return; positive = side B is the buy aggressor) 0.3786
    D ENTRY skip, megacap/ETF features (stock hours 04:00-20:00 ET), P7 | null q95 $/wk 2657 | cells 238 | stable cells (both halves>0 and above null) 0
        mega_ret1 ge 2.93 n 160 d/wk 2122 h1 2632 h2 1612 removed worst5/best5 wks 6649 -5443
        smh_ret5 ge 2.21 n 215 d/wk 2099 h1 2861 h2 1337 removed worst5/best5 wks 2035 1426
        mega_ret1 ge 4.17 n 107 d/wk 1930 h1 2210 h2 1649 removed worst5/best5 wks 4667 -3614
        qqq_ret5 ge 11.86 n 48 d/wk 1406 h1 1616 h2 1197 removed worst5/best5 wks 685 -2268
    D ENTRY skip, 1-s YM/ZN/NKD/6J features, P7 | null q95 $/wk 2513 | cells 252 | stable cells (both halves>0 and above null) 1
        ym_ret300s le -3.22 n 102 d/wk 2814 h1 5168 h2 459 removed worst5/best5 wks 4277 6044
        j6_ret300s le -1.58 n 186 d/wk 1490 h1 380 h2 2601 removed worst5/best5 wks 7181 -4597
        ym_ret10s le -0.67 n 102 d/wk 1379 h1 2148 h2 611 removed worst5/best5 wks 4266 -5297
        zn_ret900s le -2.88 n 98 d/wk 1346 h1 1407 h2 1286 removed worst5/best5 wks -821 2107
    D ENTRY skip, megacap/ETF features (stock hours 04:00-20:00 ET), ALL | null q95 $/wk 4218 | cells 238 | stable cells (both halves>0 and above null) 0
        smh_ret5 ge 3.94 n 1480 d/wk 2655 h1 3509 h2 1801 removed worst5/best5 wks 7786 2970
        smh_nq_basis5 ge -0.5 n 1480 d/wk 2632 h1 5658 h2 -395 removed worst5/best5 wks 9933 3115
        smh_ret5 ge -6.88 n 1903 d/wk 2500 h1 2240 h2 2759 removed worst5/best5 wks 11364 -7869
        smh_nq_basis5 le 21.87 n 1903 d/wk 2413 h1 2700 h2 2126 removed worst5/best5 wks 13686 -4104
    D ENTRY skip, 1-s YM/ZN/NKD/6J features, ALL | null q95 $/wk 2467 | cells 252 | stable cells (both halves>0 and above null) 1
        ym_ret10s le -0.38 n 879 d/wk 2681 h1 2866 h2 2497 removed worst5/best5 wks 9209 -9541
        ym_ret10s le -0.68 n 440 d/wk 2167 h1 2652 h2 1681 removed worst5/best5 wks 6694 -3208
        zn_ret900s le -2.88 n 428 d/wk 2147 h1 2181 h2 2114 removed worst5/best5 wks -306 887
        ym_ret300s le -2.62 n 440 d/wk 1863 h1 4456 h2 -730 removed worst5/best5 wks 3560 7194
    A LOSS-CUT gate (hold where condition true), megacap/ETF at the cut second, P7 | null q95 $/wk 2502 | cells 238 | stable cells (both halves>0 and above null) 0
        smh_delta5 ge -0.36 n 173 d/wk 1927 h1 3408 h2 445 removed worst5/best5 wks -1225 4110
        smh_delta5 ge -0.61 n 197 d/wk 1762 h1 3379 h2 146 removed worst5/best5 wks 3 2780
        smh_delta5 ge -0.12 n 124 d/wk 1688 h1 3921 h2 -545 removed worst5/best5 wks -1176 3896
        mega_ret15 ge -2.44 n 74 d/wk 1535 h1 2729 h2 342 removed worst5/best5 wks 1181 1542
    A LOSS-CUT gate, 1-s YM/ZN/NKD/6J, P7 | null q95 $/wk 3443 | cells 252 | stable cells (both halves>0 and above null) 0
        ym_ret10s le -1.14 n 103 d/wk 2598 h1 1951 h2 3244 removed worst5/best5 wks 2998 396
        zn_ret900s le -1.44 n 151 d/wk 2531 h1 1586 h2 3476 removed worst5/best5 wks 7684 -1740
        zn_ret900s le -2.84 n 101 d/wk 1759 h1 2674 h2 844 removed worst5/best5 wks 8103 -3962
        zn_ret300s le -2.87 n 50 d/wk 1476 h1 848 h2 2104 removed worst5/best5 wks 2043 -95
    A LOSS-CUT gate (hold where condition true), megacap/ETF at the cut second, ALL | null q95 $/wk 2598 | cells 238 | stable cells (both halves>0 and above null) 0
        mega_delta5 le -0.05 n 519 d/wk 2167 h1 1566 h2 2768 removed worst5/best5 wks -2664 4444
        mega_delta5 le 0.01 n 726 d/wk 2129 h1 4061 h2 197 removed worst5/best5 wks -4825 7966
        smh_delta5 ge -0.28 n 726 d/wk 1894 h1 5456 h2 -1668 removed worst5/best5 wks -6541 10422
        smh_delta5 ge -0.45 n 830 d/wk 1804 h1 4240 h2 -633 removed worst5/best5 wks -5000 9031
    A LOSS-CUT gate, 1-s YM/ZN/NKD/6J, ALL | null q95 $/wk 3453 | cells 252 | stable cells (both halves>0 and above null) 0
        zn_ret30s le -0.72 n 359 d/wk 2469 h1 1813 h2 3124 removed worst5/best5 wks -1449 -1189
        zn_ret10s le -1.42 n 180 d/wk 2274 h1 1930 h2 2618 removed worst5/best5 wks 59 -8
        zn_ret900s le -1.45 n 535 d/wk 2211 h1 3265 h2 1158 removed worst5/best5 wks 5282 3326
        ym_ret900s le -7.76 n 361 d/wk 1900 h1 4274 h2 -473 removed worst5/best5 wks -277 1710
    C NEAR-ZONE take at 80% when megacap/ETF stall, all books | null q95 $/wk 2014 | cells 238 | stable cells (both halves>0 and above null) 0
        smh_delta5 le 0.11 n 573 d/wk 1554 h1 705 h2 2403 removed worst5/best5 wks 11092 -2142
        mega_delta5 ge 0.14 n 344 d/wk 1502 h1 2283 h2 721 removed worst5/best5 wks 4980 1
        smh_delta5 le -0.13 n 229 d/wk 1386 h1 220 h2 2551 removed worst5/best5 wks 4633 -606
        mega_delta5 ge 0.2 n 229 d/wk 1356 h1 2416 h2 296 removed worst5/best5 wks 5494 665
    C NEAR-ZONE take at 80%, 1-s YM/ZN/NKD/6J, all books | null q95 $/wk 3686 | cells 252 | stable cells (both halves>0 and above null) 1
        j6_ret300s ge 0.0 n 1260 d/wk 3940 h1 4990 h2 2889 removed worst5/best5 wks 9786 -6139
        j6_ret300s ge -0.79 n 1380 d/wk 3232 h1 3977 h2 2488 removed worst5/best5 wks 8824 -9031
        j6_ret900s le 1.63 n 1363 d/wk 2843 h1 3603 h2 2083 removed worst5/best5 wks 12196 -4827
        zn_ret300s ge -0.0 n 1634 d/wk 2573 h1 1445 h2 3701 removed worst5/best5 wks 13321 -6928
    B baseline NQ-only cut at 60s when adverse>=8 pts: $/wk -3136 n 692
    B EARLY CUT at 60s (cut when adverse>=8 pts AND condition), all books | null q95 $/wk 903 | cells 490 | stable cells (both halves>0 and above null) 0
        mega_lo_against ge 2.0 n 60 d/wk 900 h1 1601 h2 198 removed worst5/best5 wks 1713 2990
        mega_lo_against ge 1.0 n 153 d/wk 856 h1 1930 h2 -219 removed worst5/best5 wks 1189 2598
        mega_lo_against ge 1.0 n 153 d/wk 856 h1 1930 h2 -219 removed worst5/best5 wks 1189 2598
        mega_conc5 le 0.24 n 88 d/wk 554 h1 565 h2 544 removed worst5/best5 wks 554 2949
    B baseline NQ-only cut at 120s when adverse>=8 pts: $/wk -6327 n 896
    B EARLY CUT at 120s (cut when adverse>=8 pts AND condition), all books | null q95 $/wk 943 | cells 490 | stable cells (both halves>0 and above null) 1
        mega_disp5 le 4.36 n 50 d/wk 1062 h1 1105 h2 1020 removed worst5/best5 wks 189 1221
        mega_disp5 le 5.61 n 99 d/wk 801 h1 546 h2 1056 removed worst5/best5 wks -1562 1840
        j6_imb ge 0.28 n 50 d/wk 731 h1 358 h2 1105 removed worst5/best5 wks 806 339
        ym_ret10s le -0.77 n 105 d/wk 717 h1 1437 h2 -2 removed worst5/best5 wks 522 1253
    F weekly flag mega_resid5 AUC 0.281 p 0.161 n weeks 25
    F weekly flag mega_disp5 AUC 0.453 p 0.798 n weeks 25
    F weekly flag mega_hi_with AUC 0.656 p 0.328 n weeks 25
    F weekly flag mega_conc5 AUC 0.75 p 0.105 n weeks 25
## NKD IMBALANCE HISTORY TEST (auto, 2026-11-12T00:08:08Z, chain2 pid 2319176)
    zone trades 9818 with NKD imbalance available 7604
    CELL nkd_imb<=0 take-at-80%, all books
        L6M: n zone 2126 cell n 0 cell gain +0/wk | mean/trade cell +0 vs rest +nan | fill cell nan rest nan | take-all +796/wk
        HOLD: n zone 3803 cell n 1010 cell gain +1,089/wk | mean/trade cell +56 vs rest -91 | fill cell 0.887 rest 0.906 | take-all +256/wk
        PRE: n zone 3690 cell n 2241 cell gain -811/wk | mean/trade cell -27 vs rest -30 | fill cell 0.895 rest 0.900 | take-all -1,421/wk
        X': n zone 1415 cell n 875 cell gain -817/wk | mean/trade cell -41 vs rest -20 | fill cell 0.877 rest 0.893 | take-all -1,068/wk
      P7
        L6M: n zone 508 cell n 0 cell gain +0/wk | mean/trade cell +0 vs rest +nan | fill cell nan rest nan | take-all +1,804/wk
        HOLD: n zone 945 cell n 267 cell gain +1,199/wk | mean/trade cell +234 vs rest -128 | fill cell 0.865 rest 0.905 | take-all +1,540/wk
        PRE: n zone 895 cell n 535 cell gain +289/wk | mean/trade cell +40 vs rest +205 | fill cell 0.880 rest 0.869 | take-all +1,252/wk
        X': n zone 337 cell n 222 cell gain -519/wk | mean/trade cell -101 vs rest +44 | fill cell 0.892 rest 0.878 | take-all -403/wk
      U7
        L6M: n zone 152 cell n 0 cell gain +0/wk | mean/trade cell +0 vs rest +nan | fill cell nan rest nan | take-all +328/wk
        HOLD: n zone 273 cell n 68 cell gain +411/wk | mean/trade cell +315 vs rest -273 | fill cell 0.868 rest 0.936 | take-all +268/wk
        PRE: n zone 283 cell n 180 cell gain +156/wk | mean/trade cell +64 vs rest -294 | fill cell 0.900 rest 0.942 | take-all -253/wk
        X': n zone 115 cell n 71 cell gain -562/wk | mean/trade cell -344 vs rest -31 | fill cell 0.930 rest 0.909 | take-all -593/wk
      P7+U7
        L6M: n zone 660 cell n 0 cell gain +0/wk | mean/trade cell +0 vs rest +nan | fill cell nan rest nan | take-all +2,132/wk
        HOLD: n zone 1218 cell n 335 cell gain +1,609/wk | mean/trade cell +250 vs rest -163 | fill cell 0.866 rest 0.913 | take-all +1,807/wk
        PRE: n zone 1178 cell n 715 cell gain +445/wk | mean/trade cell +46 vs rest +94 | fill cell 0.885 rest 0.885 | take-all +999/wk
        X': n zone 452 cell n 293 cell gain -1,080/wk | mean/trade cell -160 vs rest +23 | fill cell 0.901 rest 0.887 | take-all -996/wk
      K7+M7 (control books)
        L6M: n zone 1181 cell n 0 cell gain +0/wk | mean/trade cell +0 vs rest +nan | fill cell nan rest nan | take-all -1,001/wk
        HOLD: n zone 2125 cell n 568 cell gain -432/wk | mean/trade cell -40 vs rest -72 | fill cell 0.893 rest 0.906 | take-all -1,340/wk
        PRE: n zone 2087 cell n 1267 cell gain -1,082/wk | mean/trade cell -63 vs rest -84 | fill cell 0.897 rest 0.903 | take-all -1,999/wk
        X': n zone 760 cell n 472 cell gain +3/wk | mean/trade cell +0 vs rest -86 | fill cell 0.867 rest 0.899 | take-all -565/wk
    placebo HOLD P7+U7: actual +1,609/wk, permuted-within-book-month mean +819 q95 +1,634 q99 +1,980
    placebo PRE P7+U7: actual +445/wk, permuted-within-book-month mean +665 q95 +1,531 q99 +2,011
    placebo X' P7+U7: actual -1,080/wk, permuted-within-book-month mean -752 q95 +127 q99 +297
    bi-weekly WF over the NKD imbalance family (30 cells, pick by trailing 52 weeks, OOS from 2024-07, NKD history starts 2023-04): 61 refits fired, OOS total 47212 = $/wk 387 | most picked {"('P7', -0.17, 'ge')": 15, "('P7U7', 0.08, 'le')": 10, "('P7', -0.08, 'ge')": 9}
    TRADER TEST P7+U7 L6M: give-back events 0.0/wk, round-trips 0.0/wk; with the rule 0 give-backs converted to a take (+$0) and 0 round-trips removed, but 0 fills clipped (-$-0); net $+0 over 26 weeks; give-backs/wk after 0.0
    TRADER TEST P7+U7 HOLD: give-back events 1.2/wk, round-trips 1.2/wk; with the rule 44 give-backs converted to a take (+$253,817) and 44 round-trips removed, but 290 fills clipped (-$169,991); net $+83,913 over 52 weeks; give-backs/wk after 0.3
    TRADER TEST P7+U7 PRE: give-back events 1.8/wk, round-trips 1.7/wk; with the rule 81 give-backs converted to a take (+$441,817) and 76 round-trips removed, but 633 fills clipped (-$408,925); net $+32,858 over 74 weeks; give-backs/wk after 0.7