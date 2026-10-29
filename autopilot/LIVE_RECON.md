# LIVE_RECON - live fill vs replay expectation, per trade (generated 2026-10-29 18:29 ET; source <repo>/data/live/StratTrades_DualStrat2_<acct>.csv)

Replay fill = the corrected P9 replay expectations (per-trade matched-signal replay needs L2 for the day; the per-trade L2 replay of the 18 stop joins with the 10-20..23 tape is in JOIN_RECON.md section 5 / join_recon2/join_replay_per_attempt.csv; the replay column below stays the replay MEAN for that exit class (comparison basis of the earlier version): all stops -0.52 pts, market fallback -1.74 pts; entry S14x1 mean 1.90 (ST) / 1.77 (HM) ticks vs mid at decision). Signal reference for entry slip: REF.csv mid if present, else 1-min bar open if the NQ series covers the minute, else "-".
NQ 1-min series ends 2026-10-23 20:59:00 UTC.

## Summary

- trades 61, with entry reference 39; stop exits 21: live avg 2.45 pts worse than nominal vs replay 0.52; live minus replay per stop exit -1.23 pts (negative = worse than replay).
- entry slip vs reference: mean -0.47 pts (n=39)

## Per trade

| wk | book | side | qty | slices | entry ET | entry px | ref | ref src | entry slip pts | exit ET | exit | exit px | exit vs nominal pts | replay expected | live-replay | pnl $ |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2026-W43 | HM | L | 14 | 1 | 10-20 13:55:00 | 29779.63 | 29783.75 | L2 tape mid at trigger | -4.12 | 10-20 14:33:10 | HM_StopJoin | 29721.75 | +2.12 | -0.52 | +2.64 | -16,205 |
| 2026-W43 | ST | L | 14 | 1 | 10-20 13:21:00 | 29747.30 | 29742.38 | L2 tape mid at trigger | +4.92 | 10-20 14:42:57 | ST_StopJoinFallback | 29680.00 | -7.30 | -1.74 | -5.56 | -18,640 |
| 2026-W43 | ST | L | 14 | 1 | 10-20 18:26:00 | 29971.14 | 29965.38 | L2 tape mid at trigger | +5.76 | 10-20 18:42:29 | ST_StopJoinFallback | 29910.25 | -0.89 | -1.74 | +0.85 | -16,730 |
| 2026-W43 | ST | L | 14 | 1 | 10-20 19:41:00 | 29892.16 | 29895.75 | L2 tape mid at trigger | -3.59 | 10-20 20:12:16 | ST_Target | 29952.25 | - | - | - | 16,825 |
| 2026-W43 | ST | L | 14 | 1 | 10-20 20:25:00 | 29966.50 | 29967.12 | L2 tape mid at trigger | -0.62 | 10-20 21:00:11 | ST_StopJoin | 29907.25 | +0.75 | -0.52 | +1.27 | -16,590 |
| 2026-W43 | HM | L | 14 | 1 | 10-20 20:12:00 | 29950.48 | 29949.38 | L2 tape mid at trigger | +1.10 | 10-20 21:00:59 | HM_StopJoinFallback | 29888.25 | -2.23 | -1.74 | -0.49 | -17,200 |
| 2026-W43 | HM | L | 14 | 1 | 10-20 21:54:00 | 29982.61 | 29981.88 | L2 tape mid at trigger | +0.74 | 10-20 23:55:09 | HM_StopJoinRejected | 29920.50 | -2.11 | -0.52 | -1.59 | -17,205 |
| 2026-W43 | ST | L | 14 | 1 | 10-20 21:46:00 | 29983.98 | 29983.25 | L2 tape mid at trigger | +0.73 | 10-20 23:55:12 | ST_StopJoinFallback | 29923.00 | -0.98 | -1.74 | +0.76 | -16,910 |
| 2026-W43 | ST | S | 14 | 1 | 10-21 01:25:00 | 29883.32 | 29868.75 | L2 tape mid at trigger | -14.57 | 10-21 02:21:45 | ST_Target | 29823.25 | - | - | - | 16,820 |
| 2026-W43 | ST | S | 14 | 1 | 10-21 02:40:00 | 29841.23 | 29836.88 | L2 tape mid at trigger | -4.35 | 10-21 03:26:17 | ST_StopJoin | 29901.25 | -0.02 | -0.52 | +0.50 | -16,805 |
| 2026-W43 | ST | L | 14 | 1 | 10-21 08:59:00 | 29862.14 | 29863.12 | L2 tape mid at trigger | -0.99 | 10-21 09:43:21 | ST_StopJoinFallback | 29798.75 | -3.39 | -1.74 | -1.65 | -17,520 |
| 2026-W43 | HM | S | 14 | 1 | 10-21 19:05:01 | 29824.39 | 29824.00 | L2 tape mid at trigger | -0.39 | 10-21 19:54:39 | HM_Target | 29764.50 | - | - | - | 16,770 |
| 2026-W43 | HM | S | 14 | 1 | 10-21 19:58:00 | 29765.86 | 29767.38 | L2 tape mid at trigger | +1.51 | 10-21 20:05:31 | HM_StopJoinFallback | 29831.75 | -5.89 | -1.74 | -4.15 | -18,260 |
| 2026-W43 | ST | S | 14 | 1 | 10-21 20:16:00 | 29826.07 | 29827.38 | L2 tape mid at trigger | +1.31 | 10-21 21:19:46 | ST_Target | 29766.00 | - | - | - | 16,820 |
| 2026-W43 | ST | S | 14 | 1 | 10-21 21:20:00 | 29762.70 | 29773.38 | L2 tape mid at trigger | +10.67 | 10-21 21:51:05 | ST_ComboLock | 29768.00 | - | - | - | -1,330 |
| 2026-W43 | HM | S | 14 | 1 | 10-21 21:21:01 | 29772.68 | 29767.75 | L2 tape mid at trigger | -4.93 | 10-21 21:51:05 | HM_ComboLock | 29766.25 | - | - | - | 1,925 |
| 2026-W43 | HM | L | 14 | 1 | 10-22 18:26:01 | 29151.32 | 29145.50 | L2 tape mid at trigger | +5.82 | 10-22 19:02:44 | HM_StopJoinFallback | 29089.50 | -1.82 | -1.74 | -0.08 | -17,190 |
| 2026-W43 | ST | S | 14 | 1 | 10-22 18:32:00 | 29115.70 | 29110.88 | L2 tape mid at trigger | -4.83 | 10-22 19:33:54 | ST_Target | 29055.75 | - | - | - | 16,785 |
| 2026-W43 | HM | S | 14 | 1 | 10-22 19:03:03 | 29092.71 | 29089.88 | L2 tape mid at trigger | -2.83 | 10-22 20:10:08 | HM_Target | 29032.75 | - | - | - | 16,790 |
| 2026-W43 | ST | S | 14 | 1 | 10-22 20:02:00 | 29063.13 | 29057.00 | L2 tape mid at trigger | -6.13 | 10-22 20:14:49 | ST_StopJoinFallback | 29133.25 | -10.12 | -1.74 | -8.38 | -19,340 |
| 2026-W43 | ST | S | 14 | 1 | 10-22 20:20:00 | 29101.46 | 29096.50 | L2 tape mid at trigger | -4.96 | 10-22 20:47:08 | ST_StopJoin | 29160.00 | +1.46 | -0.52 | +1.98 | -16,390 |
| 2026-W43 | HM | L | 14 | 1 | 10-22 20:15:00 | 29127.64 | 29133.75 | L2 tape mid at trigger | -6.11 | 10-22 20:50:03 | HM_Target | 29187.75 | - | - | - | 16,830 |
| 2026-W43 | ST | L | 14 | 1 | 10-22 21:20:00 | 29128.55 | 29119.88 | L2 tape mid at trigger | +8.67 | 10-22 21:28:06 | ST_Target | 29188.50 | - | - | - | 16,785 |
| 2026-W43 | HM | L | 14 | 1 | 10-22 21:43:00 | 29200.86 | 29200.12 | L2 tape mid at trigger | +0.74 | 10-22 21:53:34 | HM_StopJoinFallback | 29135.25 | -5.61 | -1.74 | -3.87 | -18,090 |
| 2026-W43 | ST | L | 14 | 1 | 10-22 21:41:00 | 29179.32 | 29170.62 | L2 tape mid at trigger | +8.69 | 10-22 21:56:14 | ST_StopJoin | 29118.75 | -0.57 | -0.52 | -0.05 | -16,960 |
| 2026-W43 | HM | L | 14 | 1 | 10-22 23:57:02 | 29173.29 | 29178.25 | L2 tape mid at trigger | -4.96 | 10-23 01:26:40 | HM_StopJoin | 29113.50 | +0.21 | -0.52 | +0.73 | -16,740 |
| 2026-W43 | ST | L | 14 | 1 | 10-22 23:29:00 | 29167.80 | 29168.75 | L2 tape mid at trigger | -0.95 | 10-23 01:28:36 | ST_StopJoin | 29107.00 | -0.80 | -0.52 | -0.28 | -17,025 |
| 2026-W43 | HM | S | 14 | 1 | 10-23 01:27:01 | 29113.50 | 29115.62 | L2 tape mid at trigger | +2.12 | 10-23 01:42:00 | HM_StopJoin | 29172.50 | +1.00 | -0.52 | +1.52 | -16,520 |
| 2026-W43 | ST | L | 8 | 1 | 10-23 10:22:00 | 29155.09 | 29152.88 | L2 tape mid at trigger | +2.22 | 10-23 10:24:46 | ST_LossExit | 29126.75 | - | - | - | -4,460 |
| 2026-W43 | ST | S | 8 | 1 | 10-23 10:27:00 | 29089.50 | 29092.62 | L2 tape mid at trigger | +3.12 | 10-23 10:29:05 | ST_LossExit | 29114.00 | - | - | - | -3,870 |
| 2026-W43 | ST | L | 8 | 1 | 10-23 10:30:00 | 29146.88 | 29142.88 | L2 tape mid at trigger | +4.01 | 10-23 10:32:45 | ST_ProfitExit | 29168.25 | - | - | - | 3,470 |
| 2026-W43 | ST | L | 8 | 1 | 10-23 11:27:00 | 29280.97 | 29279.75 | L2 tape mid at trigger | +1.22 | 10-23 11:30:29 | ST_LossExit | 29249.50 | - | - | - | -4,980 |
| 2026-W43 | ST | L | 8 | 1 | 10-23 11:50:00 | 29269.25 | 29272.88 | L2 tape mid at trigger | -3.62 | 10-23 12:00:15 | ST_ProfitExit | 29287.25 | - | - | - | 2,890 |
| 2026-W43 | HM | L | 8 | 1 | 10-23 11:53:00 | 29267.88 | 29268.50 | L2 tape mid at trigger | -0.62 | 10-23 12:14:26 | HM_LossExit | 29259.75 | - | - | - | -1,255 |
| 2026-W43 | ST | L | 8 | 1 | 10-23 12:37:00 | 29249.16 | 29259.00 | L2 tape mid at trigger | -9.84 | 10-23 12:48:25 | ST_ProfitExit | 29260.50 | - | - | - | 1,865 |
| 2026-W43 | HM | S | 8 | 1 | 10-23 12:54:00 | 29201.84 | 29200.50 | L2 tape mid at trigger | -1.34 | 10-23 12:56:47 | HM_LossExit | 29213.25 | - | - | - | -1,810 |
| 2026-W43 | ST | S | 8 | 1 | 10-23 13:25:00 | 29154.13 | 29151.25 | L2 tape mid at trigger | -2.88 | 10-23 13:39:09 | ST_LossExit | 29170.00 | - | - | - | -2,510 |
| 2026-W43 | ST | S | 8 | 1 | 10-23 14:04:00 | 29179.50 | 29179.38 | L2 tape mid at trigger | -0.12 | 10-23 14:41:54 | ST_ProfitExit | 29156.50 | - | - | - | 3,695 |
| 2026-W43 | HM | S | 8 | 1 | 10-23 14:39:00 | 29161.34 | 29162.50 | L2 tape mid at trigger | +1.16 | 10-23 16:45:46 | HM_LossExit | 29176.00 | - | - | - | -2,315 |
| 2026-W44 | ST | L | 10 | 1 | 10-25 18:29:00 | 29269.65 | - | - | - | 10-25 18:45:23 | ST_Target | 29329.75 | - | - | - | 12,020 |
| 2026-W44 | ST | L | 10 | 1 | 10-25 19:03:00 | 29301.43 | - | - | - | 10-25 19:06:42 | ST_LossExit | 29264.00 | - | - | - | -7,405 |
| 2026-W44 | ST | S | 10 | 1 | 10-25 19:47:00 | 29120.83 | - | - | - | 10-25 19:54:31 | ST_LossExit | 29148.50 | - | - | - | -5,370 |
| 2026-W44 | HM | S | 10 | 1 | 10-25 19:51:00 | 29105.45 | - | - | - | 10-25 20:06:33 | HM_StopJoinFallback | 29172.50 | -7.05 | -1.74 | -5.31 | -13,335 |
| 2026-W44 | ST | S | 10 | 1 | 10-25 20:04:00 | 29120.13 | - | - | - | 10-25 20:06:38 | ST_StopJoinFallback | 29185.50 | -5.37 | -1.74 | -3.63 | -12,935 |
| 2026-W44 | ST | S | 10 | 1 | 10-25 21:05:00 | 29064.33 | - | - | - | 10-25 21:22:23 | ST_LossExit | 29088.75 | - | - | - | -4,755 |
| 2026-W44 | ST | S | 10 | 1 | 10-25 21:41:00 | 29099.83 | - | - | - | 10-25 21:45:47 | ST_Target | 29039.75 | - | - | - | 12,015 |
| 2026-W44 | ST | S | 10 | 1 | 10-25 22:01:00 | 29138.25 | - | - | - | 10-25 22:07:06 | ST_LossExit | 29162.50 | - | - | - | -4,765 |
| 2026-W44 | HM | L | 10 | 1 | 10-25 21:55:00 | 29165.63 | - | - | - | 10-25 22:20:48 | HM_StopJoinFallback | 29102.75 | -2.88 | -1.74 | -1.14 | -12,460 |
| 2026-W44 | ST | S | 10 | 1 | 10-25 23:10:00 | 29098.38 | - | - | - | 10-26 00:04:35 | ST_LossExit | 29129.00 | - | - | - | -6,045 |
| 2026-W44 | ST | L | 10 | 1 | 10-26 02:16:00 | 29164.45 | - | - | - | 10-26 02:18:10 | ST_LossExit | 29148.00 | - | - | - | -3,245 |
| 2026-W44 | ST | S | 10 | 1 | 10-26 02:20:00 | 29131.35 | - | - | - | 10-26 02:28:51 | ST_Target | 29071.25 | - | - | - | 12,020 |
| 2026-W44 | ST | S | 10 | 1 | 10-26 02:36:01 | 29078.50 | - | - | - | 10-26 03:02:17 | ST_LossExit | 29118.00 | - | - | - | -7,820 |
| 2026-W44 | ST | S | 10 | 1 | 10-26 03:28:00 | 29105.78 | - | - | - | 10-26 03:31:33 | ST_LossExit | 29131.50 | - | - | - | -5,055 |
| 2026-W44 | ST | L | 10 | 1 | 10-26 03:33:00 | 29139.25 | - | - | - | 10-26 03:36:42 | ST_LossExit | 29126.00 | - | - | - | -2,565 |
| 2026-W44 | ST | S | 10 | 1 | 10-26 03:40:00 | 29112.15 | - | - | - | 10-26 04:08:22 | ST_Target | 29052.25 | - | - | - | 11,980 |
| 2026-W44 | ST | S | 10 | 1 | 10-26 04:09:00 | 29060.95 | - | - | - | 10-26 04:27:33 | ST_LossExit | 29102.75 | - | - | - | -8,250 |
| 2026-W44 | ST | L | 10 | 1 | 10-26 05:24:01 | 29200.38 | - | - | - | 10-26 06:21:25 | ST_LossExit | 29150.25 | - | - | - | -9,945 |
| 2026-W44 | ST | L | 10 | 1 | 10-26 08:44:03 | 29291.18 | - | - | - | 10-26 08:56:11 | ST_LossExit | 29270.25 | - | - | - | -4,100 |
| 2026-W44 | ST | L | 10 | 1 | 10-26 10:05:00 | 29232.95 | - | - | - | 10-26 10:11:07 | ST_ProfitExit | 29256.75 | - | - | - | 4,845 |
| 2026-W44 | ST | L | 10 | 1 | 10-26 10:37:00 | 29344.60 | - | - | - | 10-26 10:39:28 | ST_ProfitExit | 29371.25 | - | - | - | 5,400 |
| 2026-W44 | HM | L | 10 | 1 | 10-26 10:43:00 | 29400.88 | - | - | - | 10-26 10:44:58 | HM_ProfitExit | 29411.25 | - | - | - | 2,150 |

## DS3 live reconciliation (DS3 file): fills vs the direct-replay model, lock events

| book | trades | entry slip pts vs bar open (n) | replay entry | stop-exit slip pts worse (n) | replay | market-fallback worse (n) | replay | target fill vs nominal (n) | lock-named exits |
|---|---|---|---|---|---|---|---|---|---|
| KB | 14 | PENDING (no tape mids/bars cover the entries) | +0.45 | PENDING/none | 0.52 | PENDING/none | 1.74 | +0.02 (4) | 1 |
| PE | 40 | PENDING (no tape mids/bars cover the entries) | +0.45 | -1.14 (2) | 0.52 | PENDING/none | 1.74 | -0.00 (12) | 1 |
| SM | 2 | PENDING (no tape mids/bars cover the entries) | +0.45 | PENDING/none | 0.52 | PENDING/none | 1.74 | +0.10 (1) | 0 |
| TOTAL | 56 | PENDING (no tape mids/bars cover the entries) | +0.45 | -1.14 (2) | 0.52 | PENDING/none | 1.74 | +0.01 (17) | 2 |

Lock events: exit names matching the lock regex are counted per book above; NT8-log DS3 lock lines: 0. $ check at R = $12,000 x lots/10 per book (12,000 x lots/10, per book): per-book day <= -2R or >= +5R, entries after the crossing = **8 violations** [('PE', '2026-10-27', '03:25'), ('PE', '2026-10-27', '06:08'), ('PE', '2026-10-27', '08:15'), ('PE', '2026-10-27', '08:55'), ('PE', '2026-10-27', '11:38')]. Give-back (+2R arm, keep 50%) and week floor (-12R) are visible only through the exit names / log; the $ check covers the day -2R/+5R lines.

Replay model: direct-L2 S10x1 slicing + XJ3 stop-join; plain Market entries (Mode 1) should show MORE entry slip than the replay number. Entry slip is PENDING until the extended tape (or REF.csv) covers the entry minutes.


## DS5 live reconciliation (DS5 file): fills vs the direct-replay model, lock events

| book | trades | entry slip pts vs bar open (n) | replay entry | stop-exit slip pts worse (n) | replay | market-fallback worse (n) | replay | target fill vs nominal (n) | lock-named exits |
|---|---|---|---|---|---|---|---|---|---|
| MIX | 1 | PENDING (no tape mids/bars cover the entries) | +0.45 | PENDING/none | 0.52 | PENDING/none | 1.74 | PENDING/none | 0 |
| TOTAL | 1 | PENDING (no tape mids/bars cover the entries) | +0.45 | PENDING/none | 0.52 | PENDING/none | 1.74 | PENDING/none | 0 |

Lock events: exit names matching the lock regex are counted per book above; NT8-log DS3 lock lines: 0. $ check at R = $12,000 x lots/10 per book (12,000 x lots/10, per book): per-book day <= -2R or >= +5R, entries after the crossing = **0 violations**. Give-back (+2R arm, keep 50%) and week floor (-12R) are visible only through the exit names / log; the $ check covers the day -2R/+5R lines.

Replay model: direct-L2 S10x1 slicing + XJ3 stop-join; plain Market entries (Mode 1) should show MORE entry slip than the replay number. Entry slip is PENDING until the extended tape (or REF.csv) covers the entry minutes.

