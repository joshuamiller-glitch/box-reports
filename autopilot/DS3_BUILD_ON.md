# DS3_BUILD_ON - T-BUILD-ON (W-BO: items 1, 3, 4, 6, 7, 8) - last update 2026-11-14 15:51Z

Page loop pid 2352035 (every 4 h from 2026-11-12 07:00Z), exact driver pid 2342528. Exact jobs: 759 of 1136 done (one set per job, one month per job), 2 BO_ workers running now. Identity of the hook path against LPB_BASE on 202610: PASSED (identical trade list).


## 1. What this page is, and the definitions used

This page covers items 1, 3, 4, 6, 7 and 8 of the T-BUILD-ON order. Item 2 (staggered targets) belongs to W-N, item 5 (hold-or-take table) to W-N2, and the JN05W composition to W-J; where item 8 (K7 two-rung targets) needs W-N's staggered-limit hook it uses that hook and says so. Everything is Shadow only. No result on this page is a PASS.

The entry tag is the one defined in autopilot/P7_CONTEXT_DEFS.md, reused unchanged and applied to each book's own trades: an entry is FRESH if it is the 1st or 2nd trade of the book in the session AND at least G minutes (15, 30 or 60) have passed since that book's last exit AND the session move in the trade direction is not more than k ATR (0.75, 1.0, 1.5, 2.0; ATR is the 5-minute ATR(14) the REG layer uses). Everything else is RECHASE. The tag is fixed at the signal second. Every lever is also run on the opposite side (the "reverse control": the same lever applied to fresh entries instead of rechase entries) so that a tag effect can be told from a generic size or target change.

An important fact about the tag: on L6M only about 13% of P7 trades are fresh at G=30, k=1.0 (134 of 1,017); the other 85% are rechase. So a rechase lot cut is close to a general lot cut, and the page therefore also reports the EQUAL-MEAN drawdown cut (the drawdown reduction left after scaling the whole stack to the same mean), which is zero by construction for a uniform size cut. A lever whose equal-mean cut is clearly positive carries information beyond size; one that is not is only a smaller position.

Two evidence layers. (a) A first-order screen: every lever is replayed on the stored full 1-second paths of the 20,807 live-panel-base trades (entry to the raw 60/60 bracket resolution), a rule acting only at or before the live exit second (otherwise the live outcome stands), measured against the same replay with no rule. It was run first, before the exact job list was frozen, as exploration only; it picks candidates and is never a result. (b) The exact engine with order hooks built in a private copy (code/th_bo/bo_hooks.py on top of the W-X hook th_ec/ec_hooks.py and the live-panel-base hook), one set per job through the TP engine, windows L1M/L3M/L6M/HOLD/PRE/X', with the bi-weekly walk-forward and the frozen week 11-01..05 to follow for finalists. The page always says which layer a number comes from.

Fill model used by the exact hooks: every market exit that a lever causes (staggered stop, time stop) fills at the next 1-second mid minus (long) or plus (short) 1.0 pt, inside the measured 0.8-1.2 pt; the probe-then-add add is a market order through the engine's own book walk; stops and targets are the engine's native fills (the stop joins passively for 3 s, then market, as live). For passive rungs (item 8 two-rung targets, run through W-N's nz_hooks) the primary model fills only on trade-through by one tick; the touch-fill model is reported beside it as the optimistic bound. In the first-order screen the target fills at the limit price (touch, optimistic) and the "q" rows require trade-through by one tick.

How the levers are implemented in the exact hook (so the rows can be read): ROWS "lots" multiply the lots at the signal second after the live sizers (floor(l*m+0.5), minimum 1, 0 skips); "T/S" change the target distance and the stop level when the bracket is first placed; "probe" replaces the live first slice (70% of the lots) by 50% or 33% and DISARMS the engine's own L2 reserve add, adding the rest by market when the 1-s mid is at least 10/25/40% of the target in favour, or N seconds after entry with the adverse excursion never worse than X pts; "stag" exits a share of the lots (1/3 or 1/2) by market when the mid is 40-75% of the stop against the entry, the remainder either keeps the live state cut (rem 0) or rides to the full stop with the state cut ignored (rem 1); "tsp/tsl" are the time stops (half or flat at N minutes if the open profit is below 10/25/40% of the target, or the open loss is still worse than 25% or 40% of the target); "clu" is the cluster filter at the signal second (skip, half the lots, or a shorter target when another book's same-side Target fill occurred within W seconds, or N of them in the last 30 minutes).

## 2. v1.8 order actions and fields this work needs (named exactly)

1. Entry tag field. A per-trade field `EntryContext` with values `fresh` / `rechase`, computed at the signal second from three inputs the strategy must keep: `SessionTradeCount` (this book's trades so far in the session, counting this one), `MinSinceLastBookExit` (minutes since this book's last exit of any kind, infinite if none), `ChaseK` (session move in the trade direction, from the session's first 1-minute open to the signal price, in 5-minute ATR(14) units). Parameters `FreshMaxTrades` (2), `FreshMinGapMin` (15/30/60), `ChaseKMax` (0.75-2.0). The tag is stored on the trade record and appears in the policy file's third column (the existing `regime` column can carry it if DayRegime is allowed to be per-trade; otherwise a new column `ctx`). Every lever below may be conditioned on `EntryContext`.
2. Per-context sizing and geometry: `LotsByContext{fresh,rechase}` (multiplier on the live lots, applied after the live sizers), `TargetPtsByContext`, `StopPtsByContext`, `PostExitBlackoutMinsByContext` (length of the post-loss blackout chosen by the context of the losing trade).
3. Partial ENTRIES (probe then add): `ProbeFraction` (0.5 or 0.33 of the planned lots replace the current first slice `SPLIT`), `AddTrigger` = {`PctOfTarget` (0.10/0.25/0.40) | `CalmSeconds` + `MaxAdverseMovePts` | `Never`}, action `AddLots(rest)` by market, `AddStopMode` = {`ReanchorAtAveragePrice` | `KeepFirstFillStop`} (the engine natively keeps the stop at the first arm level and moves only the target to the average price), `AddOnlyIfContext` (e.g. never add on rechase). The existing L2 reserve add must be switchable off for a probed entry.
4. Partial STOPS (staggered stops): action `ExitPartialMarket(lots)` with `StagStopFraction` (1/3, 1/2), `StagStopDepthPctOfStop` (0.40-0.75), `StagRemainder` = {`KeepStateCut` | `FullStopOnly`} (the second needs a per-trade switch that ignores the state cut after the partial exit). The stop order must keep working on the reduced position size.
5. TIME stops: `TimeStopMinutes` (5/10/20/40), `TimeStopMinOpenProfitPctTarget` (0.10/0.25/0.40), `TimeStopAction` = {`HalfLots` | `Flat`}, and the loss side `TimeStopMaxOpenLossPctTarget` (0.25/0.40) with the same action. Fixed to the entry clock.
6. CLUSTER filter: needs one shared strategy-level log, `LastSameSideTargetFillTime[side]` per book, so that at the signal second the book can count other books' same-side Target fills in the last `ClusterWindowSecs` (60-600) and in the last 30 min (`ClusterMinCount`), with `ClusterAction` = {`Skip` | `HalfLots` | `ShorterTargetPts`}.
7. Staggered LIMITS (belongs to W-N item 2, needed by item 8 for K7): `ExtraTargetLimits[(pctOfTarget, lots)]` resting at 2-3 prices, `FloorAfterRungFill` = {none | entry | entry+2}, remainder keeps the full target. Passive fills only on trade-through by one tick in the model; the touch-fill rows are the bound.

Bookkeeping. Prereg: autopilot/BUILD_ON_PREREG.md, sha line in DECISIONS.md before any exact BO_ cell was scored (the first-order screen was run before it, as exploration only, and said so there). dead_lookup before the exact work: 19 family-level specs, 0 EXACT/NEAR hits (nothing in these families had been scored before); append_cells after: 2,090 first-order cells (program BUILDON). Code: code/th_bo (bo_fo.py kernel, bo_cells.py grids, bo_hooks.py exact hook, bo_nz.py composition with W-N's staggered limits, bo_score.py exact rows, bo_final.py scorecard and acceptance, bo_null.py placebos, bo_wf.py walk-forward, bo_live.py frozen week). Exact sets are named BO_<book>_<cell>; one set per job; the TP engine; admission tag BUILDON, three workers at most, behind the P7FIX governor sets.


## 3. Exact rows (live panel base, order hooks in a private copy, vs LPB_BASE, same months)

Fill model of the exact runs: market exits (staggered stop, time stop) at the next 1-s mid minus or plus 1.0 pt (measured 0.8-1.2); the add of a probe-then-add is a market order through the engine book walk; stops and targets are the engine native fills. A window is shown only when every month of it is done.

| set | what it does | window | months | mean $/wk | stack dd cut % | eq-mean dd cut % | d mean $/wk | full stops/wk (ref) | $ per failure (ref) | recoveries lost $/wk | stops saved $/wk | skipped $/wk | worst-20 d $/wk | best-20 d $/wk | partial exits/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| BO_P7_1C_m0p50_T45_S60 | P7: rechase entries get lots x0.50, target 45, stop 60 (fresh full) | HOLD | 39 | 10978 | 12.1 | 9.1 | -3398 | 23.1 (23.0) | -1629 (-1651) | -31804 | 676 | 1565 | 9156 | -17876 | 0.0 |
| BO_P7_1L_G15_k1p00_m0p50 | P7: RECHASE entries get lots x0.50 (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 1.00 ATR) | HOLD | 39 | 12201 | -0.8 | 4.9 | -2479 | 23.2 (23.0) | -1629 (-1651) | -25462 | 426 | 424 | 7960 | -12821 | 0.0 |
| BO_P7_1Lrev_G60_k1p50_m0p33 | P7: FRESH entries get lots x0.33 (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 1.50 ATR) | HOLD | 39 | 14801 | -2.7 | -6.2 | -593 | 23.0 (23.0) | -1650 (-1651) | -5597 | 0 | 316 | -1605 | 1020 | 0.0 |
| BO_P7_1S_G15_k0p75_S45 | P7: RECHASE entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 0.75 ATR) | HOLD | 39 | 15354 | 7.7 | 11.4 | 180 | 22.1 (23.0) | -1665 (-1651) | -1388 | 609 | 61 | 942 | -2817 | 0.0 |
| BO_P7_1T_G30_k2p00_T45 | P7: RECHASE entries get target 45 pts (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 2.00 ATR) | HOLD | 39 | 14635 | -13.6 | -8.7 | 125 | 23.0 (23.0) | -1651 (-1651) | -12890 | 370 | 1532 | -1972 | -3182 | 0.0 |
| BO_P7_1Trev_G15_k2p00_T45 | P7: FRESH entries get target 45 pts (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 2.00 ATR) | HOLD | 39 | 14542 | 0.6 | -3.5 | -852 | 23.0 (23.0) | -1653 (-1651) | -3998 | 93 | 207 | 4586 | 207 | 0.0 |
| BO_P7_4PC_f0p50_N30_X10_fresh_s1 | P7: probe 0.50 of the lots, add the rest after 30 s with no adverse move beyond 10 pts (rechase never adds) | HOLD | 39 | 11040 | 23.9 | 19.5 | -4111 | 23.1 (23.0) | -1636 (-1651) | -25253 | 355 | 80 | 6962 | -12565 | 0.0 |
| BO_P7_6TL_N5_t0p40_flat_all | P7: at 5 min, if the open loss is still worse than 40% of the target: flat (all trades) | HOLD | 39 | 15742 | 1.1 | 3.3 | 627 | 22.9 (23.0) | -1652 (-1651) | -712 | 63 | -196 | 763 | 1165 | 1.5 |
| BO_P7_6TL_N5_t0p40_flat_rech | P7: at 5 min, if the open loss is still worse than 40% of the target: flat (rechase only) | HOLD | 39 | 15910 | 1.1 | 3.1 | 795 | 23.0 (23.0) | -1652 (-1651) | -536 | 63 | -83 | 686 | 1132 | 1.4 |
| BO_P7_7C_W600_skip | P7: another book filled a same-side target in the last 600 s: skip the signal | HOLD | 39 | 14085 | 2.1 | 7.8 | -425 | 22.9 (23.0) | -1649 (-1651) | -47 | 0 | -51 | -1863 | -3152 | 0.0 |
| BO_P7_7N_n4_half | P7: 4 or more same-side target fills by other books in the last 30 min: half the lots | HOLD | 39 | 15391 | 0.0 | 0.3 | 33 | 23.0 (23.0) | -1651 (-1651) | -47 | 0 | 0 | 0 | 0 | 0.0 |
| BO_P7_7N_n4_skip | P7: 4 or more same-side target fills by other books in the last 30 min: skip the signal | HOLD | 39 | 15375 | 0.0 | 0.2 | 16 | 23.0 (23.0) | -1651 (-1651) | 0 | 0 | 28 | 0 | 0 | 0.0 |
| BO_P7_8T_T55 | P7: single target 55 pts, stop 60 | HOLD | 39 | 16906 | 19.0 | 21.3 | 1554 | 22.9 (23.0) | -1649 (-1651) | -5543 | 223 | 1018 | 330 | -1694 | 0.0 |
| BO_P7_BL_f0_r120 | P7 post-loss same-side blackout: 0 min after a losing FRESH entry, 120 min after a losing RECHASE entry (extra to the live blackout) | HOLD | 39 | 15200 | -9.9 | -2.7 | -155 | 22.9 (23.0) | -1649 (-1651) | 0 | 0 | 1814 | 1807 | 773 | 0.0 |
| BO_P7_BL_f30_r120 | P7 post-loss same-side blackout: 30 min after a losing FRESH entry, 120 min after a losing RECHASE entry (extra to the live blackout) | HOLD | 39 | 15658 | 6.5 | 16.8 | -281 | 22.9 (23.0) | -1649 (-1651) | 0 | 0 | 1725 | 1611 | 292 | 0.0 |
| BO_P7_BL_f30_r60 | P7 post-loss same-side blackout: 30 min after a losing FRESH entry, 60 min after a losing RECHASE entry (extra to the live blackout) | HOLD | 39 | 15828 | -5.6 | 2.8 | 473 | 22.9 (23.0) | -1649 (-1651) | -57 | 0 | 1451 | 2166 | -1617 | 0.0 |
| BO_P7_BL_f30_r90 | P7 post-loss same-side blackout: 30 min after a losing FRESH entry, 90 min after a losing RECHASE entry (extra to the live blackout) | HOLD | 39 | 14913 | 4.4 | 8.1 | 404 | 22.9 (23.0) | -1647 (-1651) | 0 | 0 | 2396 | -221 | -3406 | 0.0 |
| BO_P7_NZF_all | P7 near-zone ratchet floor (80%->50%, 90%->70%, 95%->85% of target, market exit) on all entries | HOLD | 39 | 14775 | 0.9 | -0.7 | -15 | 22.9 (23.0) | -1650 (-1651) | -10334 | 352 | 766 | -1179 | -4847 | 0.0 |
| BO_K7_1C_m0p50_T30_S60 | K7: rechase entries get lots x0.50, target 30, stop 60 (fresh full) | L1M | 6 | -13288 | 9.8 | nan | 2891 | 31.9 (28.4) | -1594 (-1667) | -20569 | 9365 | -1127 | 5013 | -12448 | 0.0 |
| BO_K7_1L_G30_k1p00_m0p50 | K7: RECHASE entries get lots x0.50 (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 1.00 ATR) | L1M | 6 | -14152 | 12.4 | nan | 2028 | 31.9 (28.4) | -1602 (-1667) | -3769 | 1236 | 0 | 6341 | -9704 | 0.0 |
| BO_K7_1Lrev_G15_k2p00_m0p50 | K7: FRESH entries get lots x0.50 (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 2.00 ATR) | L1M | 6 | 17912 | -3.4 | -0.8 | 374 | 28.4 (28.4) | -1654 (-1667) | -837 | 392 | 0 | -1728 | 0 | 0.0 |
| BO_K7_1S_G30_k1p50_S45 | K7: RECHASE entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 1.50 ATR) | L1M | 6 | -14022 | 7.2 | nan | 2158 | 18.6 (28.4) | -1840 (-1667) | -7450 | 2988 | -1200 | 3671 | -9635 | 0.0 |
| BO_K7_1Srev_G60_k0p75_S45 | K7: FRESH entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 0.75 ATR) | L1M | 6 | -15770 | 1.0 | nan | 410 | 27.6 (28.4) | -1664 (-1667) | 0 | 457 | -395 | 490 | 2075 | 0.0 |
| BO_K7_1T_G60_k1p50_T30 | K7: RECHASE entries get target 30 pts (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 1.50 ATR) | L1M | 6 | -11256 | 7.9 | nan | 4924 | 29.8 (28.4) | -1704 (-1667) | -18322 | 9713 | -1140 | 4052 | -22570 | 0.0 |
| BO_K7_1Trev_G15_k1p00_T30 | K7: FRESH entries get target 30 pts (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 1.00 ATR) | L1M | 6 | -14236 | 6.9 | nan | 1944 | 29.4 (28.4) | -1652 (-1667) | -2940 | 1267 | 3126 | 3541 | -13996 | 0.0 |
| BO_K7_6TL_N10_t0p25_flat_rech | K7: at 10 min, if the open loss is still worse than 25% of the target: flat (rechase only) | L1M | 6 | 17063 | -4.7 | -5.5 | -476 | 27.6 (28.4) | -1681 (-1667) | -2924 | 2001 | -380 | -2432 | -1874 | 7.7 |
| BO_K7_6TL_N10_t0p40_half_rech | K7: at 10 min, if the open loss is still worse than 40% of the target: half the lots out (rechase only) | L1M | 6 | -387 | 0.4 | 3.1 | 63 | 28.7 (28.4) | -1663 (-1667) | -1228 | 638 | 0 | 190 | 0 | 3.1 |
| BO_K7_6TP_N10_p0p10_flat_rech | K7: at 10 min, if the open profit is below 10% of the target: flat (rechase only) | L1M | 6 | -17885 | -4.7 | nan | -1706 | 24.1 (28.4) | -1752 (-1667) | -12608 | 5711 | 3511 | 8903 | -16049 | 45.9 |
| BO_K7_7C_W300_skip | K7: another book filled a same-side target in the last 300 s: skip the signal | L1M | 6 | 16525 | 9.4 | 7.0 | -1013 | 30.1 (28.4) | -1642 (-1667) | 0 | 261 | 329 | 5844 | 685 | 0.0 |
| BO_K7_7C_W600_T30 | K7: another book filled a same-side target in the last 600 s: target 30 | L1M | 6 | 830 | 4.6 | 26.5 | 1281 | 30.1 (28.4) | -1659 (-1667) | -1680 | 1495 | -197 | 5322 | -1480 | 0.0 |
| BO_K7_7N_n2_T45 | K7: 2 or more same-side target fills by other books in the last 30 min: target 45 | L1M | 6 | -16291 | 1.2 | nan | -111 | 29.1 (28.4) | -1669 (-1667) | -1050 | 1623 | -424 | 619 | -8336 | 0.0 |
| BO_K7_7N_n3_half | K7: 3 or more same-side target fills by other books in the last 30 min: half the lots | L1M | 6 | -16180 | 0.0 | 0.0 | 0 | 28.4 (28.4) | -1667 (-1667) | 0 | 0 | 0 | 0 | 0 | 0.0 |
| BO_K7_8T_T35 | K7: single target 35 pts, stop 60 | L1M | 6 | -11872 | -1.2 | nan | 4308 | 31.1 (28.4) | -1680 (-1667) | -14000 | 9372 | 3741 | -612 | -28451 | 0.0 |
| BO_K7_8Tq_T35 | K7: single target 35 pts, stop 60 (queue-conservative: fills only on trade-through by 1 tick) | L1M | 6 | -11872 | -1.2 | nan | 4308 | 31.1 (28.4) | -1680 (-1667) | -14000 | 9372 | 3741 | -612 | -28451 | 0.0 |
| BO_K7x3_1C_m0p50_T30_S60 | K7 at 3x lots: rechase entries get lots x0.50, target 30, stop 60 (fresh full) | L1M | 6 | 17429 | 31.0 | 34.9 | -109 | 23.1 (28.4) | -2105 (-1667) | -2545 | 5960 | -519 | 15866 | -15575 | 0.0 |
| BO_K7x3_1L_G30_k1p50_m0p33 | K7 at 3x lots: RECHASE entries get lots x0.33 (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 1.50 ATR) | L1M | 6 | 12250 | 25.1 | 9.4 | -5289 | 28.7 (28.4) | -1820 (-1667) | 0 | 133 | 1828 | 15315 | -10691 | 0.0 |
| BO_K7x3_1Lrev_G15_k1p00_m0p33 | K7 at 3x lots: FRESH entries get lots x0.33 (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 1.00 ATR) | L1M | 6 | -34 | 3.4 | -21.5 | 416 | 22.1 (28.4) | -2234 (-1667) | -825 | 731 | 887 | 1743 | -496 | 0.0 |
| BO_K7x3_1S_G30_k1p50_S45 | K7 at 3x lots: RECHASE entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 1.50 ATR) | L1M | 6 | 6105 | 30.1 | 65.6 | 6555 | 17.1 (28.4) | -1918 (-1667) | -6858 | 1176 | -3704 | 15414 | 4252 | 0.0 |
| BO_K7x3_1Srev_G60_k0p75_S45 | K7 at 3x lots: FRESH entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 0.75 ATR) | L1M | 6 | 17175 | 32.5 | 26.0 | -364 | 20.3 (28.4) | -2113 (-1667) | -1360 | 630 | -983 | 16666 | -9257 | 0.0 |
| BO_K7x3_1T_G60_k1p50_T30 | K7 at 3x lots: RECHASE entries get target 30 pts (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 1.50 ATR) | L1M | 6 | -753 | 18.3 | 20.2 | -303 | 22.4 (28.4) | -2388 (-1667) | -866 | 7053 | -752 | 9400 | -10308 | 0.0 |
| BO_K7x3_1Trev_G15_k1p00_T30 | K7 at 3x lots: FRESH entries get target 30 pts (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 1.00 ATR) | L1M | 6 | -3725 | -11.6 | nan | -3275 | 22.8 (28.4) | -2342 (-1667) | -1041 | 837 | 1598 | -5920 | -3904 | 0.0 |
| BO_K7x3_3SS_f0p33_a0p60_r1_fresh | K7 at 3x lots: 0.33 of the lots go out by market at 60% of the stop (fresh entries only; remainder rides to the full stop, state cut ignored) | L1M | 6 | 23271 | 32.6 | 36.7 | 5732 | 20.3 (28.4) | -2116 (-1667) | -825 | 630 | -1597 | 16691 | 9217 | 0.0 |
| BO_K7x3_3SS_f0p50_a0p60_r1_fresh | K7 at 3x lots: 0.50 of the lots go out by market at 60% of the stop (fresh entries only; remainder rides to the full stop, state cut ignored) | L1M | 6 | 21659 | 32.6 | 31.7 | 4120 | 20.3 (28.4) | -2178 (-1667) | -825 | 900 | -563 | 16691 | 4380 | 0.0 |
| BO_K7x3_4PA_f0p33_p0p10_fresh_s0 | K7 at 3x lots: probe 0.33 of the lots, add the rest when the trade is 10% of the target in profit (rechase never adds; stop re-anchored at the average price) | L1M | 6 | 17905 | 14.3 | 95.2 | 366 | 23.4 (28.4) | -1809 (-1667) | -557 | 700 | 2246 | 7313 | -4444 | 0.0 |
| BO_K7x3_4PC_f0p33_N300_X5_all_s0 | K7 at 3x lots: probe 0.33 of the lots, add the rest after 300 s with no adverse move beyond 5 pts (all entries) | L1M | 6 | 18519 | 39.1 | 54.8 | 980 | 20.6 (28.4) | -2191 (-1667) | -1693 | 721 | -632 | 20016 | 3249 | 0.0 |
| BO_K7x3_6TL_N10_t0p25_flat_rech | K7 at 3x lots: at 10 min, if the open loss is still worse than 25% of the target: flat (rechase only) | L1M | 6 | 17052 | 32.6 | 23.4 | -486 | 20.3 (28.4) | -2116 (-1667) | -825 | 642 | 30 | 16690 | -9997 | 1.1 |
| BO_K7x3_6TP_N20_p0p40_flat_rech | K7 at 3x lots: at 20 min, if the open profit is below 40% of the target: flat (rechase only) | L1M | 6 | 16914 | 21.6 | 16.9 | -624 | 19.2 (28.4) | -1932 (-1667) | -6274 | 1320 | -439 | 15722 | 5476 | 24.1 |
| BO_K7x3_7C_W300_skip | K7 at 3x lots: another book filled a same-side target in the last 300 s: skip the signal | L1M | 6 | 20414 | 32.6 | 30.8 | 2875 | 20.3 (28.4) | -2116 (-1667) | -825 | 712 | -307 | 16690 | 8765 | 0.0 |
| BO_K7x3_7C_W600_T30 | K7 at 3x lots: another book filled a same-side target in the last 600 s: target 30 | L1M | 6 | -13004 | 18.4 | nan | 3176 | 21.4 (28.4) | -2198 (-1667) | -1035 | 1613 | -2019 | 9448 | 14332 | 0.0 |
| BO_K7x3_REF | K7 at 3x lots, no rule (comparator for the K7x3 rows) | L1M | 6 | 23230 | 32.6 | 44.8 | 5692 | 20.3 (28.4) | -2116 (-1667) | -825 | 630 | -1597 | 16690 | 9094 | 0.0 |
| BO_K7x3_RUNG_T30_f0p33_fl0_through1 | K7 at 3x lots: 0.33 of the lots rest at 30 pts, floor entry+0 after the fill, remainder keeps the 60-pt target; fill model through1 | L1M | 6 | 23230 | 32.6 | 44.8 | 5692 | 20.3 (28.4) | -2116 (-1667) | -825 | 630 | -1597 | 16690 | 9094 | 0.0 |
| BO_K7x3_RUNG_T30_f0p33_fl0_touch | K7 at 3x lots: 0.33 of the lots rest at 30 pts, floor entry+0 after the fill, remainder keeps the 60-pt target; fill model touch | L1M | 6 | 23230 | 32.6 | 44.8 | 5692 | 20.3 (28.4) | -2116 (-1667) | -825 | 630 | -1597 | 16690 | 9094 | 0.0 |
| BO_K7x3_RUNG_T30_f0p5_fl2_through1 | K7 at 3x lots: 0.5 of the lots rest at 30 pts, floor entry+2 after the fill, remainder keeps the 60-pt target; fill model through1 | L1M | 6 | 3608 | 28.9 | 65.5 | 4058 | 22.4 (28.4) | -2048 (-1667) | -1412 | 2967 | -574 | 14788 | -2614 | 0.0 |
| BO_K7x3_RUNG_T30_f0p5_fl2_touch | K7 at 3x lots: 0.5 of the lots rest at 30 pts, floor entry+2 after the fill, remainder keeps the 60-pt target; fill model touch | L1M | 6 | 3960 | 30.9 | 68.2 | 4410 | 22.8 (28.4) | -2052 (-1667) | -1412 | 2967 | -166 | 15843 | -2614 | 0.0 |
| BO_P7_1C_m0p50_T45_S60 | P7: rechase entries get lots x0.50, target 45, stop 60 (fresh full) | L1M | 39 | 13893 | 41.3 | 3.4 | -3645 | 28.4 (28.4) | -1639 (-1667) | -34050 | 808 | -4853 | 21143 | -15476 | 0.0 |
| BO_P7_1L_G15_k1p00_m0p50 | P7: RECHASE entries get lots x0.50 (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 1.00 ATR) | L1M | 39 | 14345 | 30.8 | 13.4 | -3193 | 28.4 (28.4) | -1629 (-1667) | -26278 | 0 | -4152 | 15862 | -6783 | 0.0 |
| BO_P7_1Lrev_G60_k1p50_m0p33 | P7: FRESH entries get lots x0.33 (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 1.50 ATR) | L1M | 39 | -18422 | -7.8 | nan | -2242 | 28.4 (28.4) | -1667 (-1667) | -4612 | 0 | -1595 | -3687 | 17440 | 0.0 |
| BO_P7_1S_G15_k0p75_S45 | P7: RECHASE entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 0.75 ATR) | L1M | 39 | -16225 | -6.6 | nan | -45 | 26.6 (28.4) | -1657 (-1667) | -3801 | 1265 | -1652 | -3358 | 4133 | 0.0 |
| BO_P7_1Srev_G60_k1p50_S45 | P7: FRESH entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 1.50 ATR) | L1M | 6 | -431 | 0.3 | 4.4 | 19 | 28.4 (28.4) | -1667 (-1667) | 0 | 0 | 0 | 134 | -78 | 0.0 |
| BO_P7_1T_G30_k2p00_T45 | P7: RECHASE entries get target 45 pts (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 2.00 ATR) | L1M | 39 | 3829 | 14.8 | 98.4 | 4279 | 28.4 (28.4) | -1667 (-1667) | -13755 | 0 | -3590 | 7584 | 5253 | 0.0 |
| BO_P7_1Trev_G15_k2p00_T45 | P7: FRESH entries get target 45 pts (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 2.00 ATR) | L1M | 39 | 17914 | -8.4 | -6.6 | 376 | 28.4 (28.4) | -1667 (-1667) | -3780 | 0 | -173 | -4306 | -1500 | 0.0 |
| BO_P7_3SS_f0p50_a0p60_r0_rech | P7: 0.50 of the lots go out by market at 60% of the stop (rech entries only; remainder keeps the state cut) | L1M | 6 | -16340 | 3.6 | nan | -160 | 28.0 (28.4) | -1632 (-1667) | -4753 | 282 | -1190 | 1827 | 15132 | 0.0 |
| BO_P7_4PA_f0p50_p0p10_fresh_s1 | P7: probe 0.50 of the lots, add the rest when the trade is 10% of the target in profit (rechase never adds; stop kept at the first level) | L1M | 6 | 17074 | 27.1 | 14.5 | -464 | 28.4 (28.4) | -1629 (-1667) | -25020 | 0 | -4291 | 13879 | -4932 | 0.0 |
| BO_P7_4PC_f0p50_N30_X10_fresh_s1 | P7: probe 0.50 of the lots, add the rest after 30 s with no adverse move beyond 10 pts (rechase never adds) | L1M | 39 | 15684 | 26.9 | 7.6 | -1855 | 28.4 (28.4) | -1629 (-1667) | -25024 | 0 | -4291 | 13784 | -6777 | 0.0 |
| BO_P7_6TL_N40_t0p25_flat_all | P7: at 40 min, if the open loss is still worse than 25% of the target: flat (all trades) | L1M | 6 | -14558 | 4.1 | nan | 1622 | 28.4 (28.4) | -1667 (-1667) | -3221 | 0 | -5514 | 2086 | -5522 | 3.9 |
| BO_P7_6TL_N5_t0p40_flat_all | P7: at 5 min, if the open loss is still worse than 40% of the target: flat (all trades) | L1M | 39 | -744 | -1.7 | -25.1 | -294 | 28.4 (28.4) | -1638 (-1667) | -5023 | 742 | -2229 | -883 | 0 | 2.8 |
| BO_P7_6TL_N5_t0p40_flat_rech | P7: at 5 min, if the open loss is still worse than 40% of the target: flat (rechase only) | L1M | 39 | -744 | -1.7 | -32.7 | -294 | 28.4 (28.4) | -1638 (-1667) | -4399 | 742 | -2229 | -883 | 0 | 2.5 |
| BO_P7_6TP_N5_p0p40_half_rech | P7: at 5 min, if the open profit is below 40% of the target: half the lots out (rechase only) | L1M | 6 | 1072 | 2.0 | 12.4 | 1522 | 28.0 (28.4) | -1632 (-1667) | -24704 | 371 | -307 | 6405 | -1840 | 9.1 |
| BO_P7_7C_W180_skip | P7: another book filled a same-side target in the last 180 s: skip the signal | L1M | 6 | -16180 | 0.0 | 0.0 | 0 | 28.4 (28.4) | -1667 (-1667) | 0 | 0 | 0 | 0 | 0 | 0.0 |
| BO_P7_7C_W300_half | P7: another book filled a same-side target in the last 300 s: half the lots | L1M | 6 | -450 | 0.0 | 82.5 | 0 | 28.4 (28.4) | -1639 (-1667) | 0 | 808 | 0 | 0 | 0 | 0.0 |
| BO_P7_7C_W600_skip | P7: another book filled a same-side target in the last 600 s: skip the signal | L1M | 39 | -814 | -8.1 | nan | -364 | 28.4 (28.4) | -1638 (-1667) | 0 | 0 | -7322 | -3307 | 2216 | 0.0 |
| BO_P7_7N_n2_T45 | P7: 2 or more same-side target fills by other books in the last 30 min: target 45 | L1M | 6 | 1394 | 6.8 | 37.3 | 1844 | 28.4 (28.4) | -1667 (-1667) | -945 | 0 | -1909 | 3477 | 2055 | 0.0 |
| BO_P7_7N_n4_half | P7: 4 or more same-side target fills by other books in the last 30 min: half the lots | L1M | 39 | -16180 | 0.0 | 0.0 | 0 | 28.4 (28.4) | -1667 (-1667) | 0 | 0 | 0 | 0 | 0 | 0.0 |
| BO_P7_7N_n4_skip | P7: 4 or more same-side target fills by other books in the last 30 min: skip the signal | L1M | 39 | -16180 | 0.0 | 0.0 | 0 | 28.4 (28.4) | -1667 (-1667) | 0 | 0 | 0 | 0 | 0 | 0.0 |
| BO_P7_8T_T40 | P7: single target 40 pts, stop 60 | L1M | 6 | -8839 | -0.9 | nan | -8389 | 28.0 (28.4) | -1632 (-1667) | -20020 | 0 | 5719 | -438 | -24728 | 0.0 |
| BO_P7_8T_T55 | P7: single target 55 pts, stop 60 | L1M | 39 | -3242 | -4.7 | -363.5 | -2792 | 28.4 (28.4) | -1667 (-1667) | -7782 | 0 | 1144 | -2406 | -5972 | 0.0 |
| BO_P7_8Tq_T40 | P7: single target 40 pts, stop 60 (queue-conservative: fills only on trade-through by 1 tick) | L1M | 6 | -8839 | -0.9 | nan | -8389 | 28.0 (28.4) | -1632 (-1667) | -20020 | 0 | 5719 | -438 | -24728 | 0.0 |
| BO_P7_BL_f0_r120 | P7 post-loss same-side blackout: 0 min after a losing FRESH entry, 120 min after a losing RECHASE entry (extra to the live blackout) | L1M | 39 | 20710 | 28.5 | 32.2 | 3171 | 28.4 (28.4) | -1667 (-1667) | 0 | 0 | -5234 | 14625 | 2611 | 0.0 |
| BO_P7_BL_f30_r120 | P7 post-loss same-side blackout: 30 min after a losing FRESH entry, 120 min after a losing RECHASE entry (extra to the live blackout) | L1M | 39 | 19426 | 28.5 | 28.1 | 1887 | 28.4 (28.4) | -1667 (-1667) | 0 | 0 | -5952 | 14625 | 595 | 0.0 |
| BO_P7_BL_f30_r60 | P7 post-loss same-side blackout: 30 min after a losing FRESH entry, 60 min after a losing RECHASE entry (extra to the live blackout) | L1M | 39 | 2308 | 20.9 | 52.1 | 2758 | 28.4 (28.4) | -1667 (-1667) | 0 | 0 | -2170 | 10729 | -2454 | 0.0 |
| BO_P7_BL_f30_r90 | P7 post-loss same-side blackout: 30 min after a losing FRESH entry, 90 min after a losing RECHASE entry (extra to the live blackout) | L1M | 39 | 825 | -0.5 | 97.7 | 1275 | 28.4 (28.4) | -1667 (-1667) | 0 | 0 | -1788 | -269 | 4093 | 0.0 |
| BO_P7_NZF_all | P7 near-zone ratchet floor (80%->50%, 90%->70%, 95%->85% of target, market exit) on all entries | L1M | 39 | -13285 | 0.7 | nan | 2895 | 28.4 (28.4) | -1667 (-1667) | -7333 | 0 | 778 | 384 | 15945 | 0.0 |
| BO_P7_NZF_fresh | P7 near-zone ratchet floor (80%->50%, 90%->70%, 95%->85% of target, market exit) on FRESH only (reverse control) entries | L1M | 6 | -450 | 0.0 | 8.1 | 0 | 28.4 (28.4) | -1667 (-1667) | -67 | 0 | 0 | 0 | 0 | 0.0 |
| BO_P7_NZF_rech | P7 near-zone ratchet floor (80%->50%, 90%->70%, 95%->85% of target, market exit) on RECHASE only entries | L1M | 6 | -13819 | 0.7 | nan | 2361 | 28.4 (28.4) | -1667 (-1667) | -7265 | 0 | 778 | 384 | 15945 | 0.0 |
| BO_K7_1C_m0p50_T30_S60 | K7: rechase entries get lots x0.50, target 30, stop 60 (fresh full) | L3M | 6 | 10612 | 21.3 | 29.8 | 1646 | 25.4 (23.4) | -1531 (-1662) | -17575 | 10067 | -609 | 8455 | -3946 | 0.0 |
| BO_K7_1L_G30_k1p00_m0p50 | K7: RECHASE entries get lots x0.50 (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 1.00 ATR) | L3M | 6 | 8161 | 0.1 | -11.8 | -805 | 25.4 (23.4) | -1534 (-1662) | -5237 | 2809 | 117 | 6134 | -4036 | 0.0 |
| BO_K7_1Lrev_G15_k2p00_m0p50 | K7: FRESH entries get lots x0.50 (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 2.00 ATR) | L3M | 6 | 8464 | 4.3 | 4.8 | 276 | 23.5 (23.4) | -1621 (-1662) | -1007 | 873 | 250 | -1077 | -2129 | 0.0 |
| BO_K7_1S_G30_k1p50_S45 | K7: RECHASE entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 1.50 ATR) | L3M | 6 | 10773 | -0.5 | -8.0 | -1201 | 13.0 (23.4) | -1831 (-1662) | -6684 | 3367 | 146 | 4232 | -6936 | 0.0 |
| BO_K7_1Srev_G60_k0p75_S45 | K7: FRESH entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 0.75 ATR) | L3M | 6 | 8480 | -0.8 | 1.7 | 292 | 22.5 (23.4) | -1663 (-1662) | -361 | 521 | -239 | 395 | -369 | 0.0 |
| BO_K7_1T_G60_k1p50_T30 | K7: RECHASE entries get target 30 pts (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 1.50 ATR) | L3M | 6 | 10602 | 4.4 | 17.0 | 1807 | 24.9 (23.4) | -1655 (-1662) | -14888 | 8705 | -344 | 6228 | -4902 | 0.0 |
| BO_K7_1Trev_G15_k1p00_T30 | K7: FRESH entries get target 30 pts (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 1.00 ATR) | L3M | 6 | 10077 | 12.2 | 19.8 | 1282 | 22.8 (23.4) | -1659 (-1662) | -2678 | 1747 | -1664 | 4265 | -3429 | 0.0 |
| BO_K7_6TL_N10_t0p25_flat_rech | K7: at 10 min, if the open loss is still worse than 25% of the target: flat (rechase only) | L3M | 6 | 12270 | -0.6 | -4.7 | -372 | 21.0 (23.4) | -1694 (-1662) | -2353 | 2282 | 333 | -2670 | -997 | 8.2 |
| BO_K7_6TL_N10_t0p40_half_rech | K7: at 10 min, if the open loss is still worse than 40% of the target: half the lots out (rechase only) | L3M | 6 | 11377 | 3.1 | 6.2 | 254 | 22.4 (23.4) | -1683 (-1662) | -961 | 575 | -246 | 1263 | 153 | 3.2 |
| BO_K7_6TP_N10_p0p10_flat_rech | K7: at 10 min, if the open profit is below 10% of the target: flat (rechase only) | L3M | 6 | 8216 | -1.9 | -6.3 | -749 | 17.9 (23.4) | -1739 (-1662) | -12603 | 6722 | 389 | 9685 | -3776 | 48.6 |
| BO_K7_7C_W300_skip | K7: another book filled a same-side target in the last 300 s: skip the signal | L3M | 6 | 17465 | 3.1 | 3.4 | 241 | 24.1 (23.4) | -1653 (-1662) | 0 | 65 | -793 | 2334 | 173 | 0.0 |
| BO_K7_7C_W600_T30 | K7: another book filled a same-side target in the last 600 s: target 30 | L3M | 6 | 13685 | 4.2 | 8.8 | 958 | 24.1 (23.4) | -1664 (-1662) | -1260 | 1052 | -623 | 4838 | -320 | 0.0 |
| BO_K7_7N_n2_T45 | K7: 2 or more same-side target fills by other books in the last 30 min: target 45 | L3M | 6 | 8223 | 1.0 | -3.8 | -571 | 24.1 (23.4) | -1666 (-1662) | -578 | 595 | 66 | 309 | -2309 | 0.0 |
| BO_K7_7N_n3_half | K7: 3 or more same-side target fills by other books in the last 30 min: half the lots | L3M | 6 | 11123 | 0.0 | 0.0 | 0 | 23.4 (23.4) | -1662 (-1662) | 0 | 0 | 0 | 0 | 0 | 0.0 |
| BO_K7_8T_T35 | K7: single target 35 pts, stop 60 | L3M | 6 | 10768 | 28.3 | 40.5 | 1973 | 24.2 (23.4) | -1650 (-1662) | -12294 | 7945 | 1047 | 7846 | -6807 | 0.0 |
| BO_K7_8Tq_T35 | K7: single target 35 pts, stop 60 (queue-conservative: fills only on trade-through by 1 tick) | L3M | 6 | 10768 | 28.3 | 40.5 | 1973 | 24.2 (23.4) | -1650 (-1662) | -12294 | 7945 | 1047 | 7846 | -6807 | 0.0 |
| BO_K7x3_1C_m0p50_T30_S60 | K7 at 3x lots: rechase entries get lots x0.50, target 30, stop 60 (fresh full) | L3M | 6 | 10400 | 42.7 | 64.9 | 4850 | 18.9 (23.4) | -2174 (-1662) | -3563 | 6170 | 153 | 16594 | -81 | 0.0 |
| BO_K7x3_1L_G30_k1p50_m0p33 | K7 at 3x lots: RECHASE entries get lots x0.33 (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 1.50 ATR) | L3M | 6 | 16595 | 9.3 | 3.5 | -629 | 21.9 (23.4) | -1861 (-1662) | -172 | 281 | -362 | 10978 | -4011 | 0.0 |
| BO_K7x3_1Lrev_G15_k1p00_m0p33 | K7 at 3x lots: FRESH entries get lots x0.33 (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 1.00 ATR) | L3M | 6 | 6229 | -24.7 | -48.5 | -1960 | 17.2 (23.4) | -2266 (-1662) | -1993 | 377 | 1043 | -3249 | 352 | 0.0 |
| BO_K7x3_1S_G30_k1p50_S45 | K7 at 3x lots: RECHASE entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 1.50 ATR) | L3M | 6 | 14191 | -4.9 | -1.4 | 1464 | 12.4 (23.4) | -2025 (-1662) | -6397 | 901 | -705 | 7016 | -267 | 0.0 |
| BO_K7x3_1Srev_G60_k0p75_S45 | K7 at 3x lots: FRESH entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 0.75 ATR) | L3M | 6 | 18561 | 23.2 | 26.6 | 1859 | 15.7 (23.4) | -2221 (-1662) | -763 | 493 | 265 | 21027 | 792 | 0.0 |
| BO_K7x3_1T_G60_k1p50_T30 | K7 at 3x lots: RECHASE entries get target 30 pts (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 1.50 ATR) | L3M | 6 | 19029 | 45.8 | 61.6 | 6302 | 17.1 (23.4) | -2416 (-1662) | -1432 | 5848 | 119 | 17272 | -177 | 0.0 |
| BO_K7x3_1Trev_G15_k1p00_T30 | K7 at 3x lots: FRESH entries get target 30 pts (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 1.00 ATR) | L3M | 6 | 10087 | 24.5 | 33.4 | 1899 | 16.5 (23.4) | -2327 (-1662) | -754 | 1074 | 460 | 820 | 4642 | 0.0 |
| BO_K7x3_3SS_f0p33_a0p60_r1_fresh | K7 at 3x lots: 0.33 of the lots go out by market at 60% of the stop (fresh entries only; remainder rides to the full stop, state cut ignored) | L3M | 6 | 18682 | -5.2 | -2.4 | 1458 | 15.8 (23.4) | -2254 (-1662) | -627 | 482 | 772 | 9512 | 5275 | 0.0 |
| BO_K7x3_3SS_f0p50_a0p60_r1_fresh | K7 at 3x lots: 0.50 of the lots go out by market at 60% of the stop (fresh entries only; remainder rides to the full stop, state cut ignored) | L3M | 6 | 18581 | -8.6 | -3.0 | 1357 | 15.5 (23.4) | -2244 (-1662) | -695 | 549 | 922 | 8196 | 4066 | 0.0 |
| BO_K7x3_4PA_f0p33_p0p10_fresh_s0 | K7 at 3x lots: probe 0.33 of the lots, add the rest when the trade is 10% of the target in profit (rechase never adds; stop re-anchored at the average price) | L3M | 6 | 17065 | 10.8 | 10.0 | 364 | 19.9 (23.4) | -1871 (-1662) | -1245 | 626 | -752 | 12015 | 1379 | 0.0 |
| BO_K7x3_4PC_f0p33_N300_X5_all_s0 | K7 at 3x lots: probe 0.33 of the lots, add the rest after 300 s with no adverse move beyond 5 pts (all entries) | L3M | 6 | 21121 | -2.6 | 28.5 | 3897 | 17.8 (23.4) | -2057 (-1662) | -2097 | 561 | 772 | 10447 | 2927 | 0.0 |
| BO_K7x3_6TL_N10_t0p25_flat_rech | K7 at 3x lots: at 10 min, if the open loss is still worse than 25% of the target: flat (rechase only) | L3M | 6 | 19426 | 8.2 | 12.7 | 2202 | 15.8 (23.4) | -2236 (-1662) | -1484 | 783 | 207 | 9754 | 496 | 2.5 |
| BO_K7x3_6TP_N20_p0p40_flat_rech | K7 at 3x lots: at 20 min, if the open profit is below 40% of the target: flat (rechase only) | L3M | 6 | 5797 | -2.3 | -29.9 | 246 | 14.6 (23.4) | -2055 (-1662) | -7262 | 4198 | -456 | 9218 | 1312 | 39.1 |
| BO_K7x3_7C_W300_skip | K7 at 3x lots: another book filled a same-side target in the last 300 s: skip the signal | L3M | 6 | 20309 | 11.8 | 19.5 | 3085 | 15.7 (23.4) | -2247 (-1662) | -467 | 398 | 454 | 15909 | 7926 | 0.0 |
| BO_K7x3_7C_W600_T30 | K7 at 3x lots: another book filled a same-side target in the last 600 s: target 30 | L3M | 6 | 10121 | -0.8 | 1.8 | 1327 | 16.4 (23.4) | -2286 (-1662) | -910 | 1171 | 490 | 8487 | 6306 | 0.0 |
| BO_K7x3_REF | K7 at 3x lots, no rule (comparator for the K7x3 rows) | L3M | 6 | 19968 | 0.2 | 7.6 | 2743 | 15.8 (23.4) | -2259 (-1662) | -467 | 485 | 523 | 11886 | 5433 | 0.0 |
| BO_K7x3_RUNG_T30_f0p33_fl0_through1 | K7 at 3x lots: 0.33 of the lots rest at 30 pts, floor entry+0 after the fill, remainder keeps the 60-pt target; fill model through1 | L3M | 6 | 19968 | 0.2 | 7.6 | 2743 | 15.8 (23.4) | -2259 (-1662) | -467 | 485 | 523 | 11886 | 5433 | 0.0 |
| BO_K7x3_RUNG_T30_f0p33_fl0_touch | K7 at 3x lots: 0.33 of the lots rest at 30 pts, floor entry+0 after the fill, remainder keeps the 60-pt target; fill model touch | L3M | 6 | 19968 | 0.2 | 7.6 | 2743 | 15.8 (23.4) | -2259 (-1662) | -467 | 485 | 523 | 11886 | 5433 | 0.0 |
| BO_K7x3_RUNG_T30_f0p5_fl2_through1 | K7 at 3x lots: 0.5 of the lots rest at 30 pts, floor entry+2 after the fill, remainder keeps the 60-pt target; fill model through1 | L3M | 6 | 12474 | 1.7 | 3.6 | -253 | 17.2 (23.4) | -2246 (-1662) | -1967 | 2881 | 2179 | 14948 | -553 | 0.0 |
| BO_K7x3_RUNG_T30_f0p5_fl2_touch | K7 at 3x lots: 0.5 of the lots rest at 30 pts, floor entry+2 after the fill, remainder keeps the 60-pt target; fill model touch | L3M | 6 | 12567 | 1.8 | 4.2 | -160 | 17.3 (23.4) | -2246 (-1662) | -1967 | 2881 | 2281 | 15476 | -553 | 0.0 |
| BO_P7_1C_m0p50_T45_S60 | P7: rechase entries get lots x0.50, target 45, stop 60 (fresh full) | L3M | 39 | 4879 | 43.0 | 20.2 | -671 | 23.4 (23.4) | -1643 (-1662) | -30535 | 579 | 3652 | 14083 | -17096 | 0.0 |
| BO_P7_1L_G15_k1p00_m0p50 | P7: RECHASE entries get lots x0.50 (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 1.00 ATR) | L3M | 39 | 9605 | 48.6 | 44.0 | 639 | 23.6 (23.4) | -1637 (-1662) | -26147 | 322 | -891 | 13563 | -9961 | 0.0 |
| BO_P7_1Lrev_G60_k1p50_m0p33 | P7: FRESH entries get lots x0.33 (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 1.50 ATR) | L3M | 39 | 16425 | 20.4 | 18.3 | -277 | 23.4 (23.4) | -1662 (-1662) | -4932 | 0 | -1064 | 7993 | 2712 | 0.0 |
| BO_P7_1S_G15_k0p75_S45 | P7: RECHASE entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 0.75 ATR) | L3M | 39 | 9528 | 5.7 | 12.3 | 734 | 22.6 (23.4) | -1665 (-1662) | -950 | 677 | -786 | -771 | 1307 | 0.0 |
| BO_P7_1Srev_G60_k1p50_S45 | P7: FRESH entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 1.50 ATR) | L3M | 6 | 12753 | 0.1 | 0.6 | 111 | 23.4 (23.4) | -1663 (-1662) | 0 | 23 | 0 | 90 | 83 | 0.0 |
| BO_P7_1T_G30_k2p00_T45 | P7: RECHASE entries get target 45 pts (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 2.00 ATR) | L3M | 39 | 16512 | 29.7 | 42.8 | 4538 | 23.4 (23.4) | -1665 (-1662) | -12338 | 178 | 2940 | 3593 | -2921 | 0.0 |
| BO_P7_1Trev_G15_k2p00_T45 | P7: FRESH entries get target 45 pts (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 2.00 ATR) | L3M | 39 | 17332 | 28.1 | 27.2 | 630 | 23.4 (23.4) | -1671 (-1662) | -4217 | 413 | -1447 | 10685 | 992 | 0.0 |
| BO_P7_3SS_f0p50_a0p60_r0_rech | P7: 0.50 of the lots go out by market at 60% of the stop (rech entries only; remainder keeps the state cut) | L3M | 6 | 6634 | 9.8 | 10.6 | -2161 | 23.3 (23.4) | -1649 (-1662) | -5940 | 108 | -297 | 2011 | -1005 | 0.0 |
| BO_P7_4PA_f0p50_p0p10_fresh_s1 | P7: probe 0.50 of the lots, add the rest when the trade is 10% of the target in profit (rechase never adds; stop kept at the first level) | L3M | 6 | 11629 | 41.3 | 18.8 | -3297 | 23.6 (23.4) | -1637 (-1662) | -26266 | 322 | -3570 | 7554 | -8975 | 0.0 |
| BO_P7_4PC_f0p50_N30_X10_fresh_s1 | P7: probe 0.50 of the lots, add the rest after 30 s with no adverse move beyond 10 pts (rechase never adds) | L3M | 39 | 12107 | 46.1 | 29.6 | -2819 | 23.4 (23.4) | -1637 (-1662) | -25667 | 322 | -2677 | 11481 | -9183 | 0.0 |
| BO_P7_6TL_N40_t0p25_flat_all | P7: at 40 min, if the open loss is still worse than 25% of the target: flat (all trades) | L3M | 6 | 14604 | -5.3 | -8.9 | -321 | 23.5 (23.4) | -1672 (-1662) | -1881 | 0 | -2483 | 3045 | -1360 | 3.0 |
| BO_P7_6TL_N5_t0p40_flat_all | P7: at 5 min, if the open loss is still worse than 40% of the target: flat (all trades) | L3M | 39 | 13481 | 2.8 | 7.3 | 838 | 23.4 (23.4) | -1651 (-1662) | -1256 | 280 | -347 | 138 | 1294 | 2.0 |
| BO_P7_6TL_N5_t0p40_flat_rech | P7: at 5 min, if the open loss is still worse than 40% of the target: flat (rechase only) | L3M | 39 | 13430 | 2.8 | 7.0 | 787 | 23.4 (23.4) | -1651 (-1662) | -1100 | 280 | -347 | 138 | 1294 | 1.9 |
| BO_P7_6TP_N5_p0p40_half_rech | P7: at 5 min, if the open profit is below 40% of the target: half the lots out (rechase only) | L3M | 6 | 4068 | 29.1 | 3.5 | -1482 | 23.1 (23.4) | -1645 (-1662) | -23640 | 520 | -168 | 12218 | -12019 | 7.1 |
| BO_P7_7C_W180_skip | P7: another book filled a same-side target in the last 180 s: skip the signal | L3M | 6 | 13360 | -1.3 | 2.7 | 717 | 23.4 (23.4) | -1662 (-1662) | 0 | 0 | 111 | 0 | 1225 | 0.0 |
| BO_P7_7C_W300_half | P7: another book filled a same-side target in the last 300 s: half the lots | L3M | 6 | 12138 | -1.6 | -0.6 | 164 | 23.4 (23.4) | -1653 (-1662) | -630 | 202 | 0 | 0 | 599 | 0.0 |
| BO_P7_7C_W600_skip | P7: another book filled a same-side target in the last 600 s: skip the signal | L3M | 39 | 11939 | 8.8 | 5.7 | -703 | 23.4 (23.4) | -1653 (-1662) | 0 | 0 | -3647 | 418 | 1138 | 0.0 |
| BO_P7_7N_n2_T45 | P7: 2 or more same-side target fills by other books in the last 30 min: target 45 | L3M | 6 | 9162 | -5.8 | -6.0 | 196 | 23.4 (23.4) | -1662 (-1662) | -1129 | 0 | 279 | 1738 | -556 | 0.0 |
| BO_P7_7N_n4_half | P7: 4 or more same-side target fills by other books in the last 30 min: half the lots | L3M | 39 | 14994 | 1.1 | 1.4 | 68 | 23.4 (23.4) | -1662 (-1662) | 0 | 0 | 0 | 0 | 0 | 0.0 |
| BO_P7_7N_n4_skip | P7: 4 or more same-side target fills by other books in the last 30 min: skip the signal | L3M | 39 | 12644 | 0.0 | 0.0 | 2 | 23.4 (23.4) | -1662 (-1662) | 0 | 0 | -297 | 0 | 0 | 0.0 |
| BO_P7_8T_T40 | P7: single target 40 pts, stop 60 | L3M | 6 | 11641 | 33.1 | 11.6 | -1086 | 23.4 (23.4) | -1654 (-1662) | -20230 | 169 | 2142 | 3307 | -11631 | 0.0 |
| BO_P7_8T_T55 | P7: single target 55 pts, stop 60 | L3M | 39 | 13738 | 17.3 | 22.2 | 71 | 23.4 (23.4) | -1674 (-1662) | -6014 | 195 | 1743 | -5174 | -1940 | 0.0 |
| BO_P7_8Tq_T40 | P7: single target 40 pts, stop 60 (queue-conservative: fills only on trade-through by 1 tick) | L3M | 6 | 11641 | 33.1 | 11.6 | -1086 | 23.4 (23.4) | -1654 (-1662) | -20230 | 169 | 2142 | 3307 | -11631 | 0.0 |
| BO_P7_BL_f0_r120 | P7 post-loss same-side blackout: 0 min after a losing FRESH entry, 120 min after a losing RECHASE entry (extra to the live blackout) | L3M | 39 | 13306 | 30.9 | 44.7 | 4341 | 23.3 (23.4) | -1657 (-1662) | 0 | 0 | -1 | 9415 | 280 | 0.0 |
| BO_P7_BL_f30_r120 | P7 post-loss same-side blackout: 30 min after a losing FRESH entry, 120 min after a losing RECHASE entry (extra to the live blackout) | L3M | 39 | 12709 | 30.9 | 42.3 | 3744 | 23.3 (23.4) | -1657 (-1662) | 0 | 0 | -467 | 9415 | -24 | 0.0 |
| BO_P7_BL_f30_r60 | P7 post-loss same-side blackout: 30 min after a losing FRESH entry, 60 min after a losing RECHASE entry (extra to the live blackout) | L3M | 39 | 12826 | 9.8 | 12.8 | 99 | 23.4 (23.4) | -1660 (-1662) | 0 | 0 | 1349 | 6619 | -2121 | 0.0 |
| BO_P7_BL_f30_r90 | P7 post-loss same-side blackout: 30 min after a losing FRESH entry, 90 min after a losing RECHASE entry (extra to the live blackout) | L3M | 39 | 13728 | 14.3 | 23.8 | 1754 | 23.3 (23.4) | -1657 (-1662) | 0 | 0 | 1720 | 1571 | -131 | 0.0 |
| BO_P7_NZF_all | P7 near-zone ratchet floor (80%->50%, 90%->70%, 95%->85% of target, market exit) on all entries | L3M | 39 | 14387 | 29.4 | 24.5 | -538 | 23.4 (23.4) | -1661 (-1662) | -10086 | 186 | 2321 | -4235 | 914 | 0.0 |
| BO_P7_NZF_fresh | P7 near-zone ratchet floor (80%->50%, 90%->70%, 95%->85% of target, market exit) on FRESH only (reverse control) entries | L3M | 6 | 14661 | 8.3 | 7.0 | -265 | 23.4 (23.4) | -1662 (-1662) | -1327 | 0 | -268 | -22 | -567 | 0.0 |
| BO_P7_NZF_rech | P7 near-zone ratchet floor (80%->50%, 90%->70%, 95%->85% of target, market exit) on RECHASE only entries | L3M | 6 | 12710 | 11.5 | 2.4 | -958 | 23.4 (23.4) | -1661 (-1662) | -8852 | 186 | 2401 | -2893 | 1689 | 0.0 |
| BO_K7_1C_m0p50_T30_S60 | K7: rechase entries get lots x0.50, target 30, stop 60 (fresh full) | L6M | 6 | 18099 | 21.3 | 18.2 | -709 | 26.6 (24.5) | -1496 (-1632) | -19334 | 9192 | 831 | 7504 | -4141 | 0.0 |
| BO_K7_1L_G30_k1p00_m0p50 | K7: RECHASE entries get lots x0.50 (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 1.00 ATR) | L6M | 6 | 16598 | 0.1 | -5.5 | -933 | 25.9 (24.5) | -1512 (-1632) | -5732 | 2950 | 300 | 4625 | -2920 | 0.0 |
| BO_K7_1Lrev_G15_k2p00_m0p50 | K7: FRESH entries get lots x0.50 (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 2.00 ATR) | L6M | 6 | 17171 | 4.3 | 4.3 | 13 | 24.7 (24.5) | -1608 (-1632) | -1241 | 588 | 36 | -563 | -1451 | 0.0 |
| BO_K7_1S_G30_k1p50_S45 | K7: RECHASE entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 1.50 ATR) | L6M | 6 | 20191 | -0.5 | 4.7 | 1034 | 12.8 (24.5) | -1798 (-1632) | -4960 | 4070 | 269 | 2131 | -724 | 0.0 |
| BO_K7_1Srev_G60_k0p75_S45 | K7: FRESH entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 0.75 ATR) | L6M | 6 | 17863 | -0.8 | -1.1 | -63 | 24.0 (24.5) | -1634 (-1632) | -653 | 446 | -69 | 823 | -147 | 0.0 |
| BO_K7_1T_G60_k1p50_T30 | K7: RECHASE entries get target 30 pts (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 1.50 ATR) | L6M | 6 | 18111 | 4.4 | 7.9 | 663 | 26.2 (24.5) | -1610 (-1632) | -16969 | 7391 | 199 | 4728 | -3388 | 0.0 |
| BO_K7_1Trev_G15_k1p00_T30 | K7: FRESH entries get target 30 pts (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 1.00 ATR) | L6M | 6 | 18236 | 12.2 | 16.0 | 787 | 24.4 (24.5) | -1633 (-1632) | -2482 | 885 | -693 | 2488 | -1833 | 0.0 |
| BO_K7_6TL_N10_t0p25_flat_rech | K7: at 10 min, if the open loss is still worse than 25% of the target: flat (rechase only) | L6M | 6 | 21752 | -0.6 | 2.6 | 708 | 21.6 (24.5) | -1670 (-1632) | -3236 | 2536 | -310 | 2707 | -539 | 9.9 |
| BO_K7_6TL_N10_t0p40_half_rech | K7: at 10 min, if the open loss is still worse than 40% of the target: half the lots out (rechase only) | L6M | 6 | 17881 | 3.1 | 6.0 | 527 | 23.6 (24.5) | -1647 (-1632) | -1188 | 827 | -26 | 3731 | 1398 | 4.3 |
| BO_K7_6TP_N10_p0p10_flat_rech | K7: at 10 min, if the open profit is below 10% of the target: flat (rechase only) | L6M | 6 | 16022 | -1.9 | -19.6 | -2786 | 19.2 (24.5) | -1708 (-1632) | -13388 | 6016 | 413 | 6348 | -4488 | 46.1 |
| BO_K7_7C_W300_skip | K7: another book filled a same-side target in the last 300 s: skip the signal | L6M | 6 | 19621 | 3.1 | 5.8 | 536 | 24.7 (24.5) | -1635 (-1632) | -123 | 34 | -200 | 1556 | -791 | 0.0 |
| BO_K7_7C_W600_T30 | K7: another book filled a same-side target in the last 600 s: target 30 | L6M | 6 | 17912 | 4.2 | 7.1 | 558 | 24.8 (24.5) | -1637 (-1632) | -1379 | 974 | 210 | 3225 | -1465 | 0.0 |
| BO_K7_7N_n2_T45 | K7: 2 or more same-side target fills by other books in the last 30 min: target 45 | L6M | 6 | 17630 | 1.0 | 2.0 | 181 | 24.9 (24.5) | -1636 (-1632) | -659 | 539 | 77 | 118 | -1200 | 0.0 |
| BO_K7_7N_n3_half | K7: 3 or more same-side target fills by other books in the last 30 min: half the lots | L6M | 6 | 17959 | 0.0 | 0.2 | 33 | 24.5 (24.5) | -1630 (-1632) | -98 | 48 | 0 | 0 | 122 | 0.0 |
| BO_K7_8T_T35 | K7: single target 35 pts, stop 60 | L6M | 6 | 18954 | 28.3 | 34.0 | 1505 | 25.8 (24.5) | -1617 (-1632) | -14591 | 6649 | 886 | 5092 | -5313 | 0.0 |
| BO_K7_8Tq_T35 | K7: single target 35 pts, stop 60 (queue-conservative: fills only on trade-through by 1 tick) | L6M | 6 | 18954 | 28.3 | 34.0 | 1505 | 25.8 (24.5) | -1617 (-1632) | -14591 | 6649 | 886 | 5092 | -5313 | 0.0 |
| BO_K7x3_1C_m0p50_T30_S60 | K7 at 3x lots: rechase entries get lots x0.50, target 30, stop 60 (fresh full) | L6M | 6 | 19277 | 42.7 | 52.8 | 3386 | 20.3 (24.5) | -2185 (-1632) | -4272 | 5008 | -881 | 9726 | 685 | 0.0 |
| BO_K7x3_1L_G30_k1p50_m0p33 | K7 at 3x lots: RECHASE entries get lots x0.33 (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 1.50 ATR) | L6M | 6 | 20151 | 9.3 | 13.8 | 994 | 22.3 (24.5) | -1821 (-1632) | -490 | 131 | 493 | 8583 | -1917 | 0.0 |
| BO_K7x3_1Lrev_G15_k1p00_m0p33 | K7 at 3x lots: FRESH entries get lots x0.33 (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 1.00 ATR) | L6M | 6 | 17969 | -24.7 | -24.4 | 43 | 17.3 (24.5) | -2267 (-1632) | -2074 | 310 | 1451 | -9422 | -688 | 0.0 |
| BO_K7x3_1S_G30_k1p50_S45 | K7 at 3x lots: RECHASE entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 1.50 ATR) | L6M | 6 | 17607 | -4.9 | -1.8 | 526 | 12.5 (24.5) | -2046 (-1632) | -4529 | 731 | 1220 | 1968 | 3265 | 0.0 |
| BO_K7x3_1Srev_G60_k0p75_S45 | K7 at 3x lots: FRESH entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 0.75 ATR) | L6M | 6 | 21424 | 23.2 | 35.8 | 3498 | 16.0 (24.5) | -2246 (-1632) | -1742 | 497 | 208 | 9684 | 2347 | 0.0 |
| BO_K7x3_1T_G60_k1p50_T30 | K7 at 3x lots: RECHASE entries get target 30 pts (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 1.50 ATR) | L6M | 6 | 22054 | 44.6 | 50.6 | 2392 | 18.1 (24.5) | -2398 (-1632) | -1525 | 4610 | 639 | 10590 | -941 | 0.0 |
| BO_K7x3_1Trev_G15_k1p00_T30 | K7 at 3x lots: FRESH entries get target 30 pts (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 1.00 ATR) | L6M | 6 | 19374 | 24.5 | 27.3 | 714 | 16.8 (24.5) | -2326 (-1632) | -1198 | 734 | 1009 | -4229 | 1671 | 0.0 |
| BO_K7x3_3SS_f0p33_a0p60_r1_fresh | K7 at 3x lots: 0.33 of the lots go out by market at 60% of the stop (fresh entries only; remainder rides to the full stop, state cut ignored) | L6M | 6 | 19283 | -5.2 | 2.2 | 1358 | 16.0 (24.5) | -2276 (-1632) | -1429 | 350 | 1020 | 1967 | 2520 | 0.0 |
| BO_K7x3_3SS_f0p50_a0p60_r1_fresh | K7 at 3x lots: 0.50 of the lots go out by market at 60% of the stop (fresh entries only; remainder rides to the full stop, state cut ignored) | L6M | 6 | 19692 | -8.6 | 1.1 | 1766 | 15.8 (24.5) | -2259 (-1632) | -1702 | 382 | 1000 | 1234 | 1891 | 0.0 |
| BO_K7x3_4PA_f0p33_p0p10_fresh_s0 | K7 at 3x lots: probe 0.33 of the lots, add the rest when the trade is 10% of the target in profit (rechase never adds; stop re-anchored at the average price) | L6M | 6 | 20305 | 10.8 | 15.8 | 1148 | 21.3 (24.5) | -1835 (-1632) | -1117 | 485 | 972 | 11452 | 1670 | 0.0 |
| BO_K7x3_4PC_f0p33_N300_X5_all_s0 | K7 at 3x lots: probe 0.33 of the lots, add the rest after 300 s with no adverse move beyond 5 pts (all entries) | L6M | 6 | 18378 | -2.6 | 3.2 | 1033 | 19.5 (24.5) | -2019 (-1632) | -3284 | 538 | 1598 | 1908 | 746 | 0.0 |
| BO_K7x3_6TL_N10_t0p25_flat_rech | K7 at 3x lots: at 10 min, if the open loss is still worse than 25% of the target: flat (rechase only) | L6M | 6 | 20277 | 8.2 | 10.9 | 616 | 15.7 (24.5) | -2235 (-1632) | -2459 | 656 | 919 | 4415 | 2101 | 3.3 |
| BO_K7x3_6TP_N20_p0p40_flat_rech | K7 at 3x lots: at 20 min, if the open profit is below 40% of the target: flat (rechase only) | L6M | 6 | 17586 | -2.3 | -1.0 | 233 | 15.1 (24.5) | -2119 (-1632) | -6803 | 3597 | 1393 | 12027 | -4140 | 30.2 |
| BO_K7x3_7C_W300_skip | K7 at 3x lots: another book filled a same-side target in the last 300 s: skip the signal | L6M | 6 | 19683 | 11.8 | 11.9 | 21 | 16.2 (24.5) | -2274 (-1632) | -809 | 311 | 994 | 6086 | 3952 | 0.0 |
| BO_K7x3_7C_W600_T30 | K7 at 3x lots: another book filled a same-side target in the last 600 s: target 30 | L6M | 6 | 18975 | -0.8 | 7.9 | 1622 | 16.7 (24.5) | -2324 (-1632) | -1142 | 908 | 1176 | 1138 | 3782 | 0.0 |
| BO_K7x3_REF | K7 at 3x lots, no rule (comparator for the K7x3 rows) | L6M | 6 | 19877 | 0.2 | 1.2 | 216 | 16.3 (24.5) | -2290 (-1632) | -980 | 352 | 1105 | 3404 | 2478 | 0.0 |
| BO_K7x3_RUNG_T30_f0p33_fl0_through1 | K7 at 3x lots: 0.33 of the lots rest at 30 pts, floor entry+0 after the fill, remainder keeps the 60-pt target; fill model through1 | L6M | 6 | 19865 | 0.2 | 1.2 | 204 | 16.3 (24.5) | -2290 (-1632) | -980 | 352 | 1127 | 3404 | 2478 | 0.0 |
| BO_K7x3_RUNG_T30_f0p33_fl0_touch | K7 at 3x lots: 0.33 of the lots rest at 30 pts, floor entry+0 after the fill, remainder keeps the 60-pt target; fill model touch | L6M | 6 | 19865 | 0.2 | 1.2 | 204 | 16.3 (24.5) | -2290 (-1632) | -980 | 352 | 1127 | 3404 | 2478 | 0.0 |
| BO_K7x3_RUNG_T30_f0p5_fl2_through1 | K7 at 3x lots: 0.5 of the lots rest at 30 pts, floor entry+2 after the fill, remainder keeps the 60-pt target; fill model through1 | L6M | 6 | 21634 | 1.7 | 10.7 | 1973 | 17.5 (24.5) | -2284 (-1632) | -2078 | 2130 | 1321 | 10815 | -696 | 0.0 |
| BO_K7x3_RUNG_T30_f0p5_fl2_touch | K7 at 3x lots: 0.5 of the lots rest at 30 pts, floor entry+2 after the fill, remainder keeps the 60-pt target; fill model touch | L6M | 6 | 21352 | 1.8 | 9.6 | 1691 | 17.6 (24.5) | -2287 (-1632) | -2072 | 2130 | 1484 | 11166 | -699 | 0.0 |
| BO_P7_1C_m0p50_T45_S60 | P7: rechase entries get lots x0.50, target 45, stop 60 (fresh full) | L6M | 39 | 16527 | 43.0 | 41.1 | -553 | 24.6 (24.5) | -1609 (-1632) | -34580 | 796 | 2972 | 12119 | -19082 | 0.0 |
| BO_P7_1L_G15_k1p00_m0p50 | P7: RECHASE entries get lots x0.50 (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 1.00 ATR) | L6M | 39 | 18592 | 48.6 | 51.5 | 1061 | 24.8 (24.5) | -1608 (-1632) | -27910 | 491 | 191 | 10929 | -11069 | 0.0 |
| BO_P7_1Lrev_G60_k1p50_m0p33 | P7: FRESH entries get lots x0.33 (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 1.50 ATR) | L6M | 39 | 18540 | 20.4 | 17.7 | -617 | 24.5 (24.5) | -1632 (-1632) | -5124 | 0 | 388 | 4190 | 1028 | 0.0 |
| BO_P7_1S_G15_k0p75_S45 | P7: RECHASE entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 0.75 ATR) | L6M | 39 | 17802 | 5.7 | 9.6 | 722 | 23.2 (24.5) | -1659 (-1632) | -1733 | 784 | 140 | -593 | -3606 | 0.0 |
| BO_P7_1Srev_G60_k1p50_S45 | P7: FRESH entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 1.50 ATR) | L6M | 6 | 18048 | 0.1 | 0.8 | 122 | 24.4 (24.5) | -1621 (-1632) | 0 | 65 | 0 | 221 | 128 | 0.0 |
| BO_P7_1T_G30_k2p00_T45 | P7: RECHASE entries get target 45 pts (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 2.00 ATR) | L6M | 39 | 18138 | 29.7 | 32.8 | 785 | 24.5 (24.5) | -1629 (-1632) | -14322 | 425 | 1566 | 1657 | -7224 | 0.0 |
| BO_P7_1Trev_G15_k2p00_T45 | P7: FRESH entries get target 45 pts (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 2.00 ATR) | L6M | 39 | 18391 | 28.1 | 25.1 | -766 | 24.5 (24.5) | -1636 (-1632) | -3988 | 192 | 56 | 3856 | 205 | 0.0 |
| BO_P7_3SS_f0p50_a0p60_r0_rech | P7: 0.50 of the lots go out by market at 60% of the stop (rech entries only; remainder keeps the state cut) | L6M | 6 | 17153 | 9.8 | 8.7 | -201 | 24.3 (24.5) | -1610 (-1632) | -4720 | 137 | 832 | 2159 | -6884 | 0.0 |
| BO_P7_4PA_f0p50_p0p10_fresh_s1 | P7: probe 0.50 of the lots, add the rest when the trade is 10% of the target in profit (rechase never adds; stop kept at the first level) | L6M | 6 | 16553 | 30.2 | 21.3 | -2107 | 24.8 (24.5) | -1608 (-1632) | -28525 | 477 | -487 | 397 | -12233 | 0.0 |
| BO_P7_4PC_f0p50_N30_X10_fresh_s1 | P7: probe 0.50 of the lots, add the rest after 30 s with no adverse move beyond 10 pts (rechase never adds) | L6M | 39 | 17639 | 46.1 | 43.0 | -1022 | 24.7 (24.5) | -1608 (-1632) | -27379 | 477 | -445 | 9363 | -11864 | 0.0 |
| BO_P7_6TL_N40_t0p25_flat_all | P7: at 40 min, if the open loss is still worse than 25% of the target: flat (all trades) | L6M | 6 | 18391 | -5.3 | -12.6 | -1270 | 24.6 (24.5) | -1637 (-1632) | -3015 | 0 | -1254 | 2930 | -1532 | 2.6 |
| BO_P7_6TL_N5_t0p40_flat_all | P7: at 5 min, if the open loss is still worse than 40% of the target: flat (all trades) | L6M | 39 | 17743 | 2.8 | 4.9 | 390 | 24.5 (24.5) | -1627 (-1632) | -880 | 130 | -191 | 92 | 1510 | 1.7 |
| BO_P7_6TL_N5_t0p40_flat_rech | P7: at 5 min, if the open loss is still worse than 40% of the target: flat (rechase only) | L6M | 39 | 17719 | 2.8 | 4.8 | 366 | 24.5 (24.5) | -1627 (-1632) | -807 | 130 | -191 | 92 | 1464 | 1.6 |
| BO_P7_6TP_N5_p0p40_half_rech | P7: at 5 min, if the open profit is below 40% of the target: half the lots out (rechase only) | L6M | 6 | 13795 | 29.1 | 18.3 | -2097 | 24.3 (24.5) | -1616 (-1632) | -24642 | 426 | 428 | 8989 | -15792 | 7.0 |
| BO_P7_7C_W180_skip | P7: another book filled a same-side target in the last 180 s: skip the signal | L6M | 6 | 17830 | -1.3 | 1.4 | 477 | 24.5 (24.5) | -1632 (-1632) | 0 | 0 | 258 | 0 | -329 | 0.0 |
| BO_P7_7C_W300_half | P7: another book filled a same-side target in the last 300 s: half the lots | L6M | 6 | 17466 | -1.6 | -0.9 | 113 | 24.5 (24.5) | -1628 (-1632) | -634 | 94 | -69 | 0 | -274 | 0.0 |
| BO_P7_7C_W600_skip | P7: another book filled a same-side target in the last 600 s: skip the signal | L6M | 39 | 18421 | 8.8 | 14.1 | 1068 | 24.5 (24.5) | -1628 (-1632) | 0 | 0 | -769 | 279 | -2759 | 0.0 |
| BO_P7_7N_n2_T45 | P7: 2 or more same-side target fills by other books in the last 30 min: target 45 | L6M | 6 | 19733 | -5.8 | -0.1 | 1073 | 24.5 (24.5) | -1632 (-1632) | -1860 | 0 | 734 | 1159 | -296 | 0.0 |
| BO_P7_7N_n4_half | P7: 4 or more same-side target fills by other books in the last 30 min: half the lots | L6M | 39 | 19152 | 1.1 | 1.4 | 67 | 24.5 (24.5) | -1632 (-1632) | -97 | 0 | 0 | 0 | 0 | 0.0 |
| BO_P7_7N_n4_skip | P7: 4 or more same-side target fills by other books in the last 30 min: skip the signal | L6M | 39 | 19118 | 0.0 | 0.2 | 33 | 24.5 (24.5) | -1632 (-1632) | 0 | 0 | 57 | 0 | 0 | 0.0 |
| BO_P7_8T_T40 | P7: single target 40 pts, stop 60 | L6M | 6 | 15866 | 33.1 | 19.2 | -3291 | 24.4 (24.5) | -1624 (-1632) | -22465 | 565 | 3205 | 937 | -16634 | 0.0 |
| BO_P7_8T_T55 | P7: single target 55 pts, stop 60 | L6M | 39 | 20258 | 17.3 | 19.7 | 597 | 24.5 (24.5) | -1634 (-1632) | -6301 | 91 | 1956 | -8915 | -1602 | 0.0 |
| BO_P7_8Tq_T40 | P7: single target 40 pts, stop 60 (queue-conservative: fills only on trade-through by 1 tick) | L6M | 6 | 15866 | 33.1 | 19.2 | -3291 | 24.4 (24.5) | -1624 (-1632) | -22465 | 565 | 3205 | 937 | -16634 | 0.0 |
| BO_P7_BL_f0_r120 | P7 post-loss same-side blackout: 0 min after a losing FRESH entry, 120 min after a losing RECHASE entry (extra to the live blackout) | L6M | 39 | 19097 | 30.9 | 35.4 | 1259 | 24.5 (24.5) | -1630 (-1632) | 0 | 0 | 841 | 6258 | 1112 | 0.0 |
| BO_P7_BL_f30_r120 | P7 post-loss same-side blackout: 30 min after a losing FRESH entry, 120 min after a losing RECHASE entry (extra to the live blackout) | L6M | 39 | 19713 | 30.9 | 38.5 | 2182 | 24.5 (24.5) | -1630 (-1632) | 0 | 0 | 769 | 6411 | 425 | 0.0 |
| BO_P7_BL_f30_r60 | P7 post-loss same-side blackout: 30 min after a losing FRESH entry, 60 min after a losing RECHASE entry (extra to the live blackout) | L6M | 39 | 19379 | 9.8 | 16.9 | 1541 | 24.5 (24.5) | -1628 (-1632) | -118 | 0 | 523 | 7705 | -1955 | 0.0 |
| BO_P7_BL_f30_r90 | P7 post-loss same-side blackout: 30 min after a losing FRESH entry, 90 min after a losing RECHASE entry (extra to the live blackout) | L6M | 39 | 18052 | 14.3 | 17.7 | 699 | 24.5 (24.5) | -1627 (-1632) | 0 | 0 | 2342 | 584 | -5291 | 0.0 |
| BO_P7_NZF_all | P7 near-zone ratchet floor (80%->50%, 90%->70%, 95%->85% of target, market exit) on all entries | L6M | 39 | 17646 | 29.4 | 28.3 | -280 | 24.5 (24.5) | -1628 (-1632) | -10736 | 373 | 2433 | -3604 | -4602 | 0.0 |
| BO_P7_NZF_fresh | P7 near-zone ratchet floor (80%->50%, 90%->70%, 95%->85% of target, market exit) on FRESH only (reverse control) entries | L6M | 6 | 18250 | 8.3 | 3.7 | -907 | 24.5 (24.5) | -1632 (-1632) | -1615 | 0 | 617 | -2838 | 1 | 0.0 |
| BO_P7_NZF_rech | P7 near-zone ratchet floor (80%->50%, 90%->70%, 95%->85% of target, market exit) on RECHASE only entries | L6M | 6 | 18236 | 11.5 | 3.9 | -1551 | 24.5 (24.5) | -1628 (-1632) | -9382 | 373 | 1165 | -643 | -4698 | 0.0 |
| BO_P7_1C_m0p50_T45_S60 | P7: rechase entries get lots x0.50, target 45, stop 60 (fresh full) | PRE | 39 | 10550 | 26.9 | nan | 9 | 17.0 (16.9) | -1697 (-1710) | -17181 | 243 | 389 | 13639 | -21640 | 0.0 |
| BO_P7_1L_G15_k1p00_m0p50 | P7: RECHASE entries get lots x0.50 (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 1.00 ATR) | PRE | 39 | 10552 | 16.3 | nan | 54 | 17.0 (16.9) | -1696 (-1710) | -14206 | 227 | -95 | 8874 | -17752 | 0.0 |
| BO_P7_1Lrev_G60_k1p50_m0p33 | P7: FRESH entries get lots x0.33 (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 1.50 ATR) | PRE | 39 | 10152 | -13.0 | nan | -1441 | 16.9 (16.9) | -1707 (-1710) | -7757 | 65 | -624 | 1280 | -5848 | 0.0 |
| BO_P7_1S_G15_k0p75_S45 | P7: RECHASE entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 0.75 ATR) | PRE | 39 | 11728 | 0.9 | nan | 386 | 16.4 (16.9) | -1714 (-1710) | -468 | 298 | -160 | 272 | 267 | 0.0 |
| BO_P7_1T_G30_k2p00_T45 | P7: RECHASE entries get target 45 pts (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 2.00 ATR) | PRE | 39 | 12566 | -6.7 | nan | -31 | 16.9 (16.9) | -1713 (-1710) | -6666 | 45 | 411 | 4529 | -10067 | 0.0 |
| BO_P7_1Trev_G15_k2p00_T45 | P7: FRESH entries get target 45 pts (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 2.00 ATR) | PRE | 39 | 10376 | -19.6 | nan | -1499 | 16.9 (16.9) | -1711 (-1710) | -3569 | 0 | 16 | 2395 | -5840 | 0.0 |
| BO_P7_4PC_f0p50_N30_X10_fresh_s1 | P7: probe 0.50 of the lots, add the rest after 30 s with no adverse move beyond 10 pts (rechase never adds) | PRE | 39 | 10525 | 18.0 | nan | 27 | 17.0 (16.9) | -1700 (-1710) | -14050 | 182 | -603 | 10987 | -16976 | 0.0 |
| BO_P7_6TL_N5_t0p40_flat_all | P7: at 5 min, if the open loss is still worse than 40% of the target: flat (all trades) | PRE | 39 | 12087 | 4.1 | nan | -39 | 16.9 (16.9) | -1704 (-1710) | -269 | 59 | -44 | 469 | -1120 | 0.6 |
| BO_P7_6TL_N5_t0p40_flat_rech | P7: at 5 min, if the open loss is still worse than 40% of the target: flat (rechase only) | PRE | 39 | 12057 | 4.1 | nan | -68 | 16.9 (16.9) | -1704 (-1710) | -269 | 59 | -44 | 431 | -1310 | 0.6 |
| BO_P7_7C_W600_skip | P7: another book filled a same-side target in the last 600 s: skip the signal | PRE | 39 | 11811 | 5.6 | nan | 628 | 16.9 (16.9) | -1709 (-1710) | 0 | 16 | -697 | -479 | -195 | 0.0 |
| BO_P7_7N_n4_half | P7: 4 or more same-side target fills by other books in the last 30 min: half the lots | PRE | 39 | 11877 | 0.0 | nan | -27 | 16.9 (16.9) | -1710 (-1710) | -81 | 0 | 0 | -21 | 0 | 0.0 |
| BO_P7_7N_n4_skip | P7: 4 or more same-side target fills by other books in the last 30 min: skip the signal | PRE | 39 | 11910 | 0.0 | nan | -33 | 16.9 (16.9) | -1710 (-1710) | 0 | 0 | 126 | -13 | 0 | 0.0 |
| BO_P7_8T_T55 | P7: single target 55 pts, stop 60 | PRE | 39 | 11866 | -33.2 | nan | -730 | 16.9 (16.9) | -1710 (-1710) | -3310 | 0 | 766 | 3531 | -1651 | 0.0 |
| BO_P7_BL_f0_r120 | P7 post-loss same-side blackout: 0 min after a losing FRESH entry, 120 min after a losing RECHASE entry (extra to the live blackout) | PRE | 39 | 12876 | 11.1 | nan | 291 | 16.9 (16.9) | -1711 (-1710) | 0 | 0 | -427 | 3568 | -2404 | 0.0 |
| BO_P7_BL_f30_r120 | P7 post-loss same-side blackout: 30 min after a losing FRESH entry, 120 min after a losing RECHASE entry (extra to the live blackout) | PRE | 39 | 13609 | 11.1 | nan | 1024 | 16.9 (16.9) | -1710 (-1710) | 0 | 0 | -867 | 5992 | -3409 | 0.0 |
| BO_P7_BL_f30_r60 | P7 post-loss same-side blackout: 30 min after a losing FRESH entry, 60 min after a losing RECHASE entry (extra to the live blackout) | PRE | 39 | 12330 | 10.6 | nan | 480 | 16.9 (16.9) | -1710 (-1710) | 0 | 0 | -156 | 4883 | -4308 | 0.0 |
| BO_P7_BL_f30_r90 | P7 post-loss same-side blackout: 30 min after a losing FRESH entry, 90 min after a losing RECHASE entry (extra to the live blackout) | PRE | 39 | 12272 | 18.6 | nan | 422 | 16.9 (16.9) | -1710 (-1710) | 0 | 0 | -802 | 6329 | -4043 | 0.0 |
| BO_P7_NZF_all | P7 near-zone ratchet floor (80%->50%, 90%->70%, 95%->85% of target, market exit) on all entries | PRE | 39 | 10579 | -6.8 | nan | -696 | 17.0 (16.9) | -1716 (-1710) | -5933 | 0 | 384 | 5431 | -8151 | 0.0 |
| BO_P7_1C_m0p50_T45_S60 | P7: rechase entries get lots x0.50, target 45, stop 60 (fresh full) | X' | 39 | -641 | 6.4 | nan | -487 | 17.5 (17.5) | -1606 (-1613) | -9520 | 219 | 307 | 5867 | -19474 | 0.0 |
| BO_P7_1L_G15_k1p00_m0p50 | P7: RECHASE entries get lots x0.50 (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 1.00 ATR) | X' | 39 | 1251 | 11.0 | nan | -635 | 17.5 (17.5) | -1606 (-1613) | -7612 | 129 | 1 | 5541 | -11681 | 0.0 |
| BO_P7_1Lrev_G60_k1p50_m0p33 | P7: FRESH entries get lots x0.33 (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 1.50 ATR) | X' | 39 | 3533 | 39.3 | nan | 1564 | 17.5 (17.5) | -1594 (-1613) | -5237 | 344 | 200 | 2977 | -10740 | 0.0 |
| BO_P7_1S_G15_k0p75_S45 | P7: RECHASE entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 0.75 ATR) | X' | 39 | 1251 | 0.2 | nan | 68 | 17.2 (17.5) | -1610 (-1613) | -182 | 158 | 31 | 189 | -1436 | 0.0 |
| BO_P7_1T_G30_k2p00_T45 | P7: RECHASE entries get target 45 pts (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 2.00 ATR) | X' | 39 | 1318 | -6.7 | nan | -364 | 17.5 (17.5) | -1612 (-1613) | -3802 | 184 | 206 | 1124 | -9451 | 0.0 |
| BO_P7_1Trev_G15_k2p00_T45 | P7: FRESH entries get target 45 pts (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 2.00 ATR) | X' | 39 | 900 | 3.6 | nan | -42 | 17.4 (17.5) | -1602 (-1613) | -2471 | 398 | 37 | 6978 | -11893 | 0.0 |
| BO_P7_4PC_f0p50_N30_X10_fresh_s1 | P7: probe 0.50 of the lots, add the rest after 30 s with no adverse move beyond 10 pts (rechase never adds) | X' | 39 | 963 | -3.2 | nan | -1589 | 17.5 (17.5) | -1605 (-1613) | -7512 | 137 | 890 | 7210 | -15300 | 0.0 |
| BO_P7_6TL_N5_t0p40_flat_all | P7: at 5 min, if the open loss is still worse than 40% of the target: flat (all trades) | X' | 39 | 1403 | 0.8 | nan | 11 | 17.5 (17.5) | -1613 (-1613) | 0 | 0 | 0 | 0 | 0 | 0.1 |
| BO_P7_6TL_N5_t0p40_flat_rech | P7: at 5 min, if the open loss is still worse than 40% of the target: flat (rechase only) | X' | 39 | 1594 | 0.8 | nan | -1 | 17.5 (17.5) | -1613 (-1613) | 0 | 0 | 0 | 0 | 0 | 0.1 |
| BO_P7_7C_W600_skip | P7: another book filled a same-side target in the last 600 s: skip the signal | X' | 39 | 1296 | 8.3 | nan | 101 | 17.5 (17.5) | -1613 (-1613) | 0 | 0 | 84 | 1085 | 1317 | 0.0 |
| BO_P7_7N_n4_half | P7: 4 or more same-side target fills by other books in the last 30 min: half the lots | X' | 39 | 962 | -2.9 | nan | 0 | 17.5 (17.5) | -1613 (-1613) | -82 | 0 | 0 | 0 | 0 | 0.0 |
| BO_P7_7N_n4_skip | P7: 4 or more same-side target fills by other books in the last 30 min: skip the signal | X' | 39 | 1001 | -8.7 | nan | 40 | 17.5 (17.5) | -1613 (-1613) | 0 | 0 | 152 | 0 | 0 | 0.0 |
| BO_P7_8T_T55 | P7: single target 55 pts, stop 60 | X' | 39 | 558 | 3.3 | nan | 16 | 17.5 (17.5) | -1613 (-1613) | -2059 | 0 | -10 | 4225 | -4100 | 0.0 |
| BO_P7_BL_f0_r120 | P7 post-loss same-side blackout: 0 min after a losing FRESH entry, 120 min after a losing RECHASE entry (extra to the live blackout) | X' | 39 | 868 | 4.1 | nan | -110 | 17.5 (17.5) | -1613 (-1613) | 0 | 0 | 347 | 1207 | -1445 | 0.0 |
| BO_P7_BL_f30_r120 | P7 post-loss same-side blackout: 30 min after a losing FRESH entry, 120 min after a losing RECHASE entry (extra to the live blackout) | X' | 39 | 758 | 1.8 | nan | -220 | 17.5 (17.5) | -1613 (-1613) | 0 | 0 | 329 | 1898 | -1445 | 0.0 |
| BO_P7_BL_f30_r60 | P7 post-loss same-side blackout: 30 min after a losing FRESH entry, 60 min after a losing RECHASE entry (extra to the live blackout) | X' | 39 | 733 | -1.6 | nan | -245 | 17.5 (17.5) | -1613 (-1613) | 0 | 0 | -67 | 1529 | -1445 | 0.0 |
| BO_P7_BL_f30_r90 | P7 post-loss same-side blackout: 30 min after a losing FRESH entry, 90 min after a losing RECHASE entry (extra to the live blackout) | X' | 39 | 881 | 0.7 | nan | -97 | 17.5 (17.5) | -1613 (-1613) | 0 | 0 | -181 | 1970 | -1445 | 0.0 |
| BO_P7_NZF_all | P7 near-zone ratchet floor (80%->50%, 90%->70%, 95%->85% of target, market exit) on all entries | X' | 39 | -592 | -0.3 | nan | -439 | 17.5 (17.5) | -1608 (-1613) | -3566 | 306 | -139 | 3881 | -16876 | 0.0 |

## 4. Worked rows (the five trades where each exact set differs most from the live twin, L6M months done so far)


**BO_K7_1C_m0p50_T30_S60**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 08-20 00:50 | P7 | short | 4 > 4 | n/a | Target > Target | 970 > 4795 |
| 08-05 22:24 | K7 | long | 2 > 1 | rech (1 / 199 / 2.17) | StopJoinFallback > Target | -2482 > 599 |
| 07-02 16:03 | K7 | short | 2 > 1 | rech (1 / 8 / 0.55) | Target > StateCut | 2398 > -650 |
| 09-17 22:18 | K7 | short | 2 > 1 | rech (1 / 153 / 2.02) | StopJoinFallback > Target | -2442 > 599 |
| 09-14 11:06 | K7 | long | 2 > 1 | rech (5 / 30 / -3.28) | StopJoin > Target | -2427 > 599 |


**BO_K7_1L_G30_k1p00_m0p50**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 08-27 05:18 | K7 | short | 2 > 1 | rech (6 / 1 / 2.27) | Target > StateCut | 2398 > -1170 |
| 08-31 22:51 | K7 | short | 2 > 1 | rech (1 / -1 / 2.04) | StopJoin > Target | -2177 > 1199 |
| 07-22 12:09 | K7 | short | 2 > 1 | rech (8 / 26 / 5.03) | Target > StateCut | 2393 > -672 |
| 08-07 06:30 | K7 | long | 2 > 1 | rech (1 / 0 / 2.64) | Target > StateCut | 2398 > -655 |
| 07-02 16:03 | K7 | short | 2 > 1 | rech (1 / 8 / 0.55) | Target > StateCut | 2398 > -650 |


**BO_K7_1Lrev_G15_k2p00_m0p50**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 06-22 06:54 | K7 | long | 2 > 2 | fresh (2 / 29 / 4.18) | BookLock > Target | -1592 > 2403 |
| 07-22 22:30 | K7 | short | 2 > 1 | rech (1 / 155 / 0.50) | Target > StackCut | 2398 > -1036 |
| 09-24 17:27 | K7 | short | 2 > 1 | rech (2 / 61 / -3.26) | Target > StateCut | 2393 > -720 |
| 06-29 17:27 | K7 | long | none > 2 | fresh (3 / 15 / 3.31) | none > Target | 0 > 2403 |
| 06-29 16:00 | K7 | long | none > 2 | fresh (1 / 1 / nan) | none > Target | 0 > 2398 |


**BO_K7_1S_G30_k1p50_S45**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 07-02 15:56 | P7 | short | 4 > 4 | n/a | BookLock > Target | -2145 > 4790 |
| 07-13 02:08 | P7 | short | none > 7 | n/a | none > StateCut | 0 > -5963 |
| 06-04 02:25 | P7 | short | none > 7 | n/a | none > StateCut | 0 > -5073 |
| 06-07 23:34 | P7 | long | none > 4 | n/a | none > Target | 0 > 4795 |
| 06-08 04:30 | P7 | short | none > 4 | n/a | none > Target | 0 > 4795 |


**BO_K7_1Srev_G60_k0p75_S45**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 09-24 17:27 | K7 | short | 2 > 2 | rech (2 / 61 / -3.26) | Target > StopJoinFallback | 2393 > -1732 |
| 07-08 22:12 | P7 | long | 4 > 4 | n/a | Target > Target | 4800 > 1135 |
| 07-17 16:45 | K7 | long | none > 2 | fresh (2 / 21 / 0.49) | none > Target | 0 > 2403 |
| 05-13 09:21 | K7 | short | 1 > 1 | fresh (3 / 10 / -4.12) | Target > StopJoin | 1199 > -1186 |
| 06-03 18:27 | K7 | long | none > 2 | fresh (4 / 1 / 2.01) | none > StopJoin | 0 > -2317 |


**BO_K7_1T_G60_k1p50_T30**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 08-20 00:50 | P7 | short | 4 > 4 | n/a | Target > Target | 970 > 4795 |
| 08-05 22:24 | K7 | long | 2 > 2 | rech (1 / 860 / 2.17) | StopJoinFallback > Target | -2482 > 1203 |
| 09-17 22:18 | K7 | short | 2 > 2 | rech (1 / 153 / 2.02) | StopJoinFallback > Target | -2442 > 1193 |
| 09-14 11:06 | K7 | long | 2 > 2 | rech (5 / 30 / -3.28) | StopJoin > Target | -2427 > 1203 |
| 09-18 06:51 | K7 | long | 2 > 2 | rech (2 / 40 / 3.80) | StopJoinFallback > Target | -2422 > 1203 |


**BO_K7_1Trev_G15_k1p00_T30**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 05-08 17:03 | K7 | long | 2 > 2 | fresh (1 / 9 / 3.23) | BookLock > Target | -1682 > 2398 |
| 06-22 06:54 | K7 | long | 2 > 2 | fresh (2 / 37 / 4.18) | BookLock > Target | -1592 > 2403 |
| 10-27 12:18 | K7 | long | 2 > 2 | fresh (6 / 93 / 6.48) | BookLock > Target | -1427 > 2403 |
| 08-24 16:03 | K7 | long | 2 > 2 | rech (1 / 20 / 0.27) | StopJoinFallback > Target | -2397 > 1203 |
| 10-08 22:09 | K7 | long | 2 > 2 | rech (1 / 201 / 0.51) | StopJoin > Target | -2342 > 1198 |


**BO_K7_6TL_N10_t0p25_flat_rech**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 05-08 17:03 | K7 | long | 2 > 2 | rech (2 / 0 / 3.23) | BookLock > Target | -1682 > 2398 |
| 06-22 06:54 | K7 | long | 2 > 2 | rech (2 / 29 / 4.18) | BookLock > Target | -1592 > 2403 |
| 07-02 16:03 | K7 | short | 2 > 2 | rech (1 / 8 / 0.55) | Target > BoTimeL | 2398 > -1562 |
| 10-30 12:18 | K7 | short | 2 > 2 | rech (7 / 5 / 6.83) | Target > BoTimeL | 2398 > -1147 |
| 07-08 17:09 | K7 | long | 2 > 2 | rech (3 / 2 / 4.70) | Target > BoTimeL | 2398 > -1062 |


**BO_K7_6TL_N10_t0p40_half_rech**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 06-22 06:54 | K7 | long | 2 > 2 | rech (2 / 29 / 4.18) | BookLock > Target | -1592 > 2403 |
| 07-16 02:50 | P7 | long | 4 > 4 | n/a | Target > Target | 2165 > 4795 |
| 05-22 10:42 | K7 | short | none > 2 | rech (5 / 9 / 3.65) | none > Stop | 0 > -2407 |
| 07-17 16:45 | K7 | long | none > 2 | rech (2 / 21 / 0.49) | none > Target | 0 > 2403 |
| 05-22 12:15 | K7 | long | none > 2 | rech (6 / 27 / 0.61) | none > Target | 0 > 2398 |


**BO_K7_6TP_N10_p0p10_flat_rech**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 06-22 06:54 | K7 | long | 2 > 2 | rech (2 / 29 / 4.18) | BookLock > Target | -1592 > 2403 |
| 07-02 16:03 | K7 | short | 2 > 2 | rech (1 / 8 / 0.55) | Target > BoTime | 2398 > -1562 |
| 08-20 00:50 | P7 | short | 4 > 4 | n/a | Target > Target | 970 > 4795 |
| 07-08 17:09 | K7 | long | 2 > 2 | rech (3 / 2 / 4.70) | Target > BoTime | 2398 > -1062 |
| 05-21 02:39 | K7 | long | 2 > 2 | rech (3 / 38 / 4.43) | Target > BoTime | 2403 > -1052 |


**BO_K7_7C_W300_skip**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 06-22 06:54 | K7 | long | 2 > 2 | rech (2 / 29 / 4.18) | BookLock > Target | -1592 > 2403 |
| 07-13 04:24 | K7 | short | 2 > 2 | rech (6 / 20 / 10.64) | BookLock > Target | -937 > 2398 |
| 08-11 16:48 | K7 | short | 2 > 2 | rech (1 / 2 / 1.29) | Target > BookLock | 2393 > -632 |
| 07-17 05:57 | K7 | short | none > 2 | rech (9 / 13 / 14.29) | none > StopJoinFallback | 0 > -2542 |
| 08-19 18:09 | K7 | short | none > 2 | rech (5 / 1 / 3.55) | none > StopJoinFallback | 0 > -2432 |


**BO_K7_7C_W600_T30**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 08-19 00:03 | K7 | short | 2 > 2 | rech (2 / 1 / 4.44) | StopJoin > Target | -2392 > 1198 |
| 06-03 16:27 | K7 | short | 2 > 2 | rech (1 / 3 / 1.31) | StopJoinFallback > Target | -2352 > 1198 |
| 07-27 06:03 | K7 | long | 2 > 2 | rech (1 / 2 / 0.84) | StopJoin > Target | -2327 > 1203 |
| 07-13 04:24 | K7 | short | 2 > 2 | rech (8 / 20 / 10.64) | BookLock > Target | -937 > 2398 |
| 09-07 10:57 | K7 | short | 2 > 2 | rech (2 / 2 / 3.01) | StateCut > Target | -1869 > 1198 |


**BO_K7_7N_n2_T45**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 07-27 06:03 | K7 | long | 2 > 2 | rech (1 / 2 / 0.84) | StopJoin > Target | -2327 > 1803 |
| 05-08 17:03 | K7 | long | 2 > 2 | rech (1 / 9 / 3.23) | BookLock > Target | -1682 > 2398 |
| 06-19 05:09 | K7 | short | 2 > 2 | rech (5 / 11 / 11.34) | StopJoinFallback > Target | -1647 > 1798 |
| 07-14 05:45 | K7 | long | 2 > 2 | rech (9 / 67 / 4.83) | StateCut > Target | -1604 > 1803 |
| 10-28 22:33 | K7 | short | 2 > 1 | rech (2 / 7 / 2.53) | StopJoinFallback > Target | -2387 > 899 |


**BO_K7_7N_n3_half**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 06-19 03:45 | K7 | short | 2 > 1 | rech (3 / 30 / 10.76) | Target > Target | 2398 > 1199 |
| 07-10 06:39 | K7 | short | 2 > 1 | rech (1 / 20 / 2.48) | Target > Target | 2398 > 1199 |
| 08-11 00:03 | K7 | short | 2 > 1 | rech (2 / 5 / 6.19) | StopJoinFallback > StopJoinFallback | -2377 > -1196 |
| 07-14 12:12 | K7 | short | none > 1 | rech (7 / 4 / 0.25) | none > StateCut | 0 > -777 |
| 07-14 05:45 | K7 | long | 2 > 1 | rech (9 / 67 / 4.83) | StateCut > StateCut | -1604 > -865 |


**BO_K7_8T_T35**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 07-02 16:03 | K7 | short | 2 > 2 | rech (1 / 8 / 0.55) | Target > BookLock | 2398 > -1842 |
| 08-05 22:24 | K7 | long | 2 > 2 | rech (1 / 860 / 2.17) | StopJoinFallback > Target | -2482 > 1403 |
| 09-17 22:18 | K7 | short | 2 > 2 | rech (1 / 153 / 2.02) | StopJoinFallback > Target | -2442 > 1393 |
| 09-18 06:51 | K7 | long | 2 > 2 | rech (2 / 37 / 3.80) | StopJoinFallback > Target | -2422 > 1403 |
| 08-24 16:03 | K7 | long | 2 > 2 | rech (1 / 25 / 0.27) | StopJoinFallback > Target | -2397 > 1403 |


**BO_K7_8Tq_T35**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 07-02 16:03 | K7 | short | 2 > 2 | rech (1 / 8 / 0.55) | Target > BookLock | 2398 > -1842 |
| 08-05 22:24 | K7 | long | 2 > 2 | rech (1 / 860 / 2.17) | StopJoinFallback > Target | -2482 > 1403 |
| 09-17 22:18 | K7 | short | 2 > 2 | rech (1 / 153 / 2.02) | StopJoinFallback > Target | -2442 > 1393 |
| 09-18 06:51 | K7 | long | 2 > 2 | rech (2 / 37 / 3.80) | StopJoinFallback > Target | -2422 > 1403 |
| 08-24 16:03 | K7 | long | 2 > 2 | rech (1 / 25 / 0.27) | StopJoinFallback > Target | -2397 > 1403 |


**BO_K7x3_1C_m0p50_T30_S60**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 05-18 22:16 | P7 | long | 7 > 7 | n/a | Target > Target | 8402 > 3192 |
| 09-09 10:45 | K7 | short | 2 > 3 | rech (4 / 72 / 8.64) | Target > BookLock | 2393 > -2699 |
| 05-19 04:15 | P7 | short | none > 4 | n/a | none > Target | 0 > 4790 |
| 08-05 22:24 | K7 | long | 2 > 3 | rech (1 / 1237 / 2.17) | StopJoinFallback > Target | -2482 > 1801 |
| 09-01 22:06 | K7 | short | 1 > 3 | fresh (1 / 621 / 0.96) | StateCut > Target | -660 > 3591 |


**BO_K7x3_1L_G30_k1p50_m0p33**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 07-15 22:36 | K7 | short | 1 > 3 | fresh (1 / 647 / 0.63) | StateCut > Target | -795 > 3596 |
| 05-04 10:36 | K7 | long | 1 > 3 | fresh (2 / 34 / -2.64) | StateCut > Target | -745 > 3601 |
| 09-01 22:06 | K7 | short | 1 > 3 | fresh (1 / 212 / 0.96) | StateCut > Target | -660 > 3591 |
| 08-04 16:03 | K7 | long | 2 > 4 | fresh (1 / 52 / 0.49) | Target > BookLock | 2403 > -1765 |
| 09-11 06:48 | K7 | long | 1 > 3 | fresh (1 / 55 / 1.32) | StateCut > Target | -522 > 3591 |


**BO_K7x3_1Lrev_G15_k1p00_m0p33**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 10-14 05:22 | P7 | short | none > 7 | n/a | none > Target | 0 > 8377 |
| 05-18 22:16 | P7 | long | 7 > 7 | n/a | Target > Target | 8402 > 992 |
| 09-11 10:03 | K7 | long | 2 > 4 | fresh (3 / 0 / 6.15) | Target > BookLock | 2398 > -3460 |
| 09-13 22:59 | P7 | short | 7 > 7 | n/a | Target > Target | 8397 > 3162 |
| 05-19 04:15 | P7 | short | none > 4 | n/a | none > Target | 0 > 4790 |


**BO_K7x3_1S_G30_k1p50_S45**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 05-18 22:16 | P7 | long | 7 > 7 | n/a | Target > Target | 8402 > 1887 |
| 07-13 02:08 | P7 | short | none > 7 | n/a | none > StateCut | 0 > -5963 |
| 06-11 01:57 | K7 | short | 2 > 4 | rech (6 / 13 / -3.31) | Target > StopJoinFallback | 2398 > -3560 |
| 10-14 01:30 | K7 | long | 2 > 4 | rech (2 / 20 / 1.58) | StateCut > Target | -1324 > 3596 |
| 09-10 01:48 | K7 | long | none > 4 | rech (4 / 13 / -2.38) | none > Target | 0 > 4800 |


**BO_K7x3_1Srev_G60_k0p75_S45**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 05-18 22:16 | P7 | long | 7 > 7 | n/a | Target > Target | 8402 > 992 |
| 05-06 04:15 | K7 | long | none > 4 | fresh (3 / 48 / 5.99) | none > Target | 0 > 4795 |
| 05-19 04:15 | P7 | short | none > 4 | n/a | none > Target | 0 > 4790 |
| 09-07 06:24 | K7 | long | none > 4 | fresh (1 / 11 / 2.93) | none > StopJoinFallback | 0 > -4620 |
| 09-01 22:06 | K7 | short | 1 > 3 | fresh (1 / 212 / 0.96) | StateCut > Target | -660 > 3591 |


**BO_K7x3_1T_G60_k1p50_T30**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 09-09 10:45 | K7 | short | 2 > 4 | rech (4 / 72 / 8.64) | Target > BookLock | 2393 > -4255 |
| 05-18 22:16 | P7 | long | 7 > 7 | n/a | Target > Target | 8402 > 3057 |
| 10-28 22:51 | K7 | short | none > 4 | rech (3 / 13 / 3.22) | none > StopJoinFallback | 0 > -5345 |
| 10-16 00:00 | K7 | short | none > 4 | rech (3 / 21 / 4.21) | none > StopJoinFallback | 0 > -5030 |
| 09-07 22:48 | K7 | short | none > 4 | rech (2 / 21 / 4.60) | none > StopJoinFallback | 0 > -5010 |


**BO_K7x3_1Trev_G15_k1p00_T30**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 10-14 05:22 | P7 | short | none > 7 | n/a | none > Target | 0 > 8377 |
| 05-18 22:16 | P7 | long | 7 > 7 | n/a | Target > Target | 8402 > 992 |
| 09-03 03:51 | K7 | long | none > 4 | fresh (2 / 33 / 3.59) | none > StopJoinFallback | 0 > -4900 |
| 05-07 02:03 | K7 | long | none > 4 | fresh (3 / 13 / 2.78) | none > Target | 0 > 4805 |
| 06-01 00:24 | K7 | long | none > 4 | fresh (3 / 14 / 5.83) | none > Target | 0 > 4805 |


**BO_K7x3_3SS_f0p33_a0p60_r1_fresh**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 05-18 22:16 | P7 | long | 7 > 7 | n/a | Target > Target | 8402 > 992 |
| 10-14 01:30 | K7 | long | 2 > 4 | rech (2 / 20 / 1.58) | StateCut > Target | -1324 > 3596 |
| 05-06 04:15 | K7 | long | none > 4 | rech (3 / 37 / 5.99) | none > Target | 0 > 4795 |
| 05-19 04:15 | P7 | short | none > 4 | n/a | none > Target | 0 > 4790 |
| 09-02 02:06 | K7 | short | none > 4 | rech (2 / 16 / 3.89) | none > StopJoin | 0 > -4630 |


**BO_K7x3_3SS_f0p50_a0p60_r1_fresh**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 10-14 05:22 | P7 | short | none > 7 | n/a | none > Target | 0 > 8377 |
| 05-18 22:16 | P7 | long | 7 > 7 | n/a | Target > Target | 8402 > 992 |
| 05-19 04:15 | P7 | short | none > 4 | n/a | none > Target | 0 > 4790 |
| 10-14 14:05 | P7 | short | none > 4 | n/a | none > Target | 0 > 4790 |
| 10-14 03:15 | K7 | long | none > 4 | rech (4 / 49 / 5.62) | none > StopJoinFallback | 0 > -4750 |


**BO_K7x3_4PA_f0p33_p0p10_fresh_s0**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 06-22 00:03 | K7 | long | 1 > 6 | fresh (2 / 62 / -2.86) | Target > Target | 1199 > 7208 |
| 10-25 22:30 | K7 | long | 1 > 6 | fresh (1 / 4114 / 0.83) | Target > Target | 1199 > 7188 |
| 07-02 22:18 | K7 | long | 2 > 6 | fresh (1 / 1351 / 0.65) | StateCut > StopJoinFallback | -1479 > -7432 |
| 08-04 16:03 | K7 | long | 2 > 6 | fresh (1 / 52 / 0.49) | Target > BookLock | 2403 > -2597 |
| 06-30 22:06 | K7 | long | 2 > 6 | fresh (1 / -1 / 0.83) | StateCut > StateCut | -1964 > -6853 |


**BO_K7x3_4PC_f0p33_N300_X5_all_s0**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 05-28 10:36 | K7 | short | 2 > 6 | rech (3 / 10 / -0.70) | Target > StopJoin | 2398 > -7252 |
| 09-14 17:48 | K7 | long | none > 6 | rech (3 / 17 / 4.17) | none > StopJoinFallback | 0 > -7567 |
| 05-18 22:16 | P7 | long | 7 > 7 | n/a | Target > Target | 8402 > 972 |
| 10-20 05:36 | K7 | short | none > 6 | rech (6 / 9 / 6.73) | none > StopJoinFallback | 0 > -7342 |
| 05-06 10:18 | K7 | long | none > 6 | rech (2 / 16 / 7.49) | none > Target | 0 > 7203 |


**BO_K7x3_6TL_N10_t0p25_flat_rech**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 05-18 22:16 | P7 | long | 7 > 7 | n/a | Target > Target | 8402 > 992 |
| 05-06 04:15 | K7 | long | none > 4 | rech (3 / 37 / 5.99) | none > Target | 0 > 4795 |
| 05-19 04:15 | P7 | short | none > 4 | n/a | none > Target | 0 > 4790 |
| 05-21 02:39 | K7 | long | 2 > 4 | rech (3 / 38 / 4.43) | Target > BoTimeL | 2403 > -2095 |
| 06-17 12:27 | K7 | long | 1 > 3 | rech (4 / 38 / -1.13) | StateCut > Target | -855 > 3591 |


**BO_K7x3_6TP_N20_p0p40_flat_rech**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 06-21 22:33 | K7 | short | 2 > 4 | rech (1 / 4089 / 1.31) | Target > BoTime | 2393 > -2740 |
| 07-31 00:06 | K7 | long | none > 4 | rech (4 / 4 / 3.92) | none > Target | 0 > 4805 |
| 09-08 01:39 | K7 | long | none > 4 | rech (7 / 10 / 3.64) | none > Target | 0 > 4805 |
| 10-01 03:51 | K7 | long | none > 4 | rech (5 / 28 / 12.09) | none > Target | 0 > 4805 |
| 09-30 04:57 | K7 | short | none > 4 | rech (10 / 16 / 0.97) | none > Target | 0 > 4800 |


**BO_K7x3_7C_W300_skip**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 05-18 22:16 | P7 | long | 7 > 7 | n/a | Target > Target | 8402 > 992 |
| 10-14 01:30 | K7 | long | 2 > 4 | rech (2 / 20 / 1.58) | StateCut > Target | -1324 > 3596 |
| 05-25 00:09 | K7 | long | none > 4 | rech (1 / 3971 / 8.27) | none > Target | 0 > 4805 |
| 05-06 04:15 | K7 | long | none > 4 | rech (3 / 37 / 5.99) | none > Target | 0 > 4795 |
| 05-19 04:15 | P7 | short | none > 4 | n/a | none > Target | 0 > 4790 |


**BO_K7x3_7C_W600_T30**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 05-18 22:16 | P7 | long | 7 > 7 | n/a | Target > Target | 8402 > 992 |
| 10-28 22:51 | K7 | short | none > 4 | rech (3 / 13 / 3.22) | none > StopJoinFallback | 0 > -5345 |
| 10-14 01:30 | K7 | long | 2 > 4 | rech (2 / 20 / 1.58) | StateCut > Target | -1324 > 3596 |
| 05-25 00:09 | K7 | long | none > 4 | rech (2 / 34 / 8.27) | none > Target | 0 > 4805 |
| 07-03 05:06 | K7 | long | none > 4 | rech (5 / 2 / 12.89) | none > Target | 0 > 4805 |


**BO_K7x3_7N_n2_skip**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 05-18 22:16 | P7 | long | 7 > 7 | n/a | Target > Target | 8402 > 992 |
| 10-14 01:30 | K7 | long | 2 > 4 | rech (2 / 20 / 1.58) | StateCut > Target | -1324 > 3596 |
| 05-25 00:09 | K7 | long | none > 4 | rech (1 / 3971 / 8.27) | none > Target | 0 > 4805 |
| 05-06 04:15 | K7 | long | none > 4 | rech (3 / 37 / 5.99) | none > Target | 0 > 4795 |
| 05-19 04:15 | P7 | short | none > 4 | n/a | none > Target | 0 > 4790 |


**BO_K7x3_8T_T35**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 05-18 22:16 | P7 | long | 7 > 7 | n/a | Target > Target | 8402 > 2797 |
| 10-28 22:51 | K7 | short | none > 4 | rech (3 / 13 / 3.22) | none > StopJoinFallback | 0 > -5345 |
| 08-05 22:24 | K7 | long | 2 > 4 | rech (1 / 1237 / 2.17) | StopJoinFallback > Target | -2482 > 2795 |
| 09-13 22:59 | P7 | short | 7 > 7 | n/a | Target > Target | 8397 > 3162 |
| 09-17 22:18 | K7 | short | 2 > 4 | rech (1 / 432 / 2.02) | StopJoinFallback > Target | -2442 > 2785 |


**BO_K7x3_8Tq_T35**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 05-18 22:16 | P7 | long | 7 > 7 | n/a | Target > Target | 8402 > 2797 |
| 10-28 22:51 | K7 | short | none > 4 | rech (3 / 13 / 3.22) | none > StopJoinFallback | 0 > -5345 |
| 08-05 22:24 | K7 | long | 2 > 4 | rech (1 / 1237 / 2.17) | StopJoinFallback > Target | -2482 > 2795 |
| 09-13 22:59 | P7 | short | 7 > 7 | n/a | Target > Target | 8397 > 3162 |
| 09-17 22:18 | K7 | short | 2 > 4 | rech (1 / 432 / 2.02) | StopJoinFallback > Target | -2442 > 2785 |


**BO_K7x3_REF**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 05-18 22:16 | P7 | long | 7 > 7 | n/a | Target > Target | 8402 > 992 |
| 10-14 01:30 | K7 | long | 2 > 4 | rech (2 / 20 / 1.58) | StateCut > Target | -1324 > 3596 |
| 05-06 04:15 | K7 | long | none > 4 | rech (3 / 37 / 5.99) | none > Target | 0 > 4795 |
| 05-19 04:15 | P7 | short | none > 4 | n/a | none > Target | 0 > 4790 |
| 07-15 22:36 | K7 | short | 1 > 3 | fresh (1 / 1313 / 0.63) | StateCut > Target | -795 > 3596 |


**BO_K7x3_RUNG_T30_f0p33_fl0_through1**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 05-18 22:16 | P7 | long | 7 > 7 | n/a | Target > Target | 8402 > 992 |
| 10-14 01:30 | K7 | long | 2 > 4 | rech (2 / 20 / 1.58) | StateCut > Target | -1324 > 3596 |
| 05-06 04:15 | K7 | long | none > 4 | rech (3 / 37 / 5.99) | none > Target | 0 > 4795 |
| 05-19 04:15 | P7 | short | none > 4 | n/a | none > Target | 0 > 4790 |
| 07-15 22:36 | K7 | short | 1 > 3 | fresh (1 / 1313 / 0.63) | StateCut > Target | -795 > 3596 |


**BO_K7x3_RUNG_T30_f0p33_fl0_touch**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 05-18 22:16 | P7 | long | 7 > 7 | n/a | Target > Target | 8402 > 992 |
| 10-14 01:30 | K7 | long | 2 > 4 | rech (2 / 20 / 1.58) | StateCut > Target | -1324 > 3596 |
| 05-06 04:15 | K7 | long | none > 4 | rech (3 / 37 / 5.99) | none > Target | 0 > 4795 |
| 05-19 04:15 | P7 | short | none > 4 | n/a | none > Target | 0 > 4790 |
| 07-15 22:36 | K7 | short | 1 > 3 | fresh (1 / 1313 / 0.63) | StateCut > Target | -795 > 3596 |


**BO_K7x3_RUNG_T30_f0p5_fl2_through1**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 08-17 07:12 | K7 | short | 2 > 4 | rech (2 / 0 / -1.00) | StateCut > Target | -1984 > 4230 |
| 09-13 22:59 | P7 | short | 7 > 7 | n/a | Target > Target | 8397 > 3162 |
| 05-06 16:12 | K7 | long | none > 4 | fresh (1 / 53 / 0.95) | none > StopJoinFallback | 0 > -5010 |
| 09-07 22:48 | K7 | short | none > 4 | rech (1 / 9 / 4.60) | none > StopJoinFallback | 0 > -5010 |
| 05-28 00:00 | K7 | short | none > 4 | rech (3 / 9 / 6.04) | none > StopJoinFallback | 0 > -4995 |


**BO_K7x3_RUNG_T30_f0p5_fl2_touch**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 08-17 07:12 | K7 | short | 2 > 4 | rech (2 / 0 / -1.00) | StateCut > Target | -1984 > 4230 |
| 09-13 22:59 | P7 | short | 7 > 7 | n/a | Target > Target | 8397 > 3162 |
| 05-06 16:12 | K7 | long | none > 4 | fresh (1 / 53 / 0.95) | none > StopJoinFallback | 0 > -5010 |
| 09-07 22:48 | K7 | short | none > 4 | rech (1 / 9 / 4.60) | none > StopJoinFallback | 0 > -5010 |
| 05-28 00:00 | K7 | short | none > 4 | rech (3 / 9 / 6.04) | none > StopJoinFallback | 0 > -4995 |


**BO_P7_1C_m0p50_T45_S60**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 08-26 03:03 | P7 | long | 7 > 4 | rech (4 / 39 / -3.56) | StateCut > Target | -7138 > 3605 |
| 08-12 02:49 | P7 | long | 7 > 4 | rech (3 / 10 / 3.78) | StateCut > Target | -6845 > 3605 |
| 03-03 01:02 | P7 | short | 7 > 4 | rech (2 / 0 / 4.53) | Target > StateCut | 7188 > -3239 |
| 03-11 22:42 | P7 | long | 7 > 4 | rech (1 / 872 / 2.10) | StopJoin > Target | -6658 > 3595 |
| 08-19 22:22 | P7 | long | 7 > 4 | rech (1 / 384 / 1.08) | StateCut > Target | -6135 > 3595 |


**BO_P7_1L_G15_k1p00_m0p50**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 08-26 03:03 | P7 | long | 7 > 4 | rech (4 / 39 / -3.56) | StateCut > Target | -7138 > 4805 |
| 07-30 00:17 | P7 | short | 7 > 4 | rech (2 / 36 / 6.03) | Target > StateCut | 8402 > -3474 |
| 03-11 22:42 | P7 | long | 7 > 4 | rech (1 / 872 / 2.10) | StopJoin > Target | -6658 > 4795 |
| 03-03 01:02 | P7 | short | 7 > 4 | rech (2 / 0 / 4.53) | Target > StateCut | 7188 > -3239 |
| 09-30 01:36 | P7 | short | none > 7 | fresh (2 / 23 / -1.10) | none > Target | 0 > 8407 |


**BO_P7_1Lrev_G60_k1p50_m0p33**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 12-16 01:55 | P7 | short | 7 > 7 | fresh (4 / 19 / 7.48) | Target > BookLock | 8402 > -1818 |
| 02-16 23:27 | P7 | long | 7 > 2 | rech (1 / 562 / 1.28) | Target > StateCut | 8387 > -1406 |
| 08-19 22:22 | P7 | long | 7 > 2 | rech (1 / 384 / 1.08) | StateCut > Target | -6135 > 2398 |
| 04-10 00:46 | P7 | short | none > 7 | fresh (1 / 10 / 5.25) | none > Target | 0 > 8407 |
| 05-31 23:53 | P7 | long | none > 7 | fresh (2 / 1 / 3.55) | none > Target | 0 > 8402 |


**BO_P7_1S_G15_k0p75_S45**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 04-22 05:05 | P7 | short | none > 7 | rech (3 / 5 / -4.82) | none > Stop | 0 > -8473 |
| 06-19 03:37 | P7 | short | none > 7 | rech (3 / 14 / 6.72) | none > Target | 0 > 8377 |
| 06-09 08:11 | P7 | long | 4 > 4 | rech (1 / 7 / 4.92) | Target > StopJoin | 4795 > -3425 |
| 01-20 07:03 | P7 | long | 4 > 4 | rech (1 / 11 / -0.63) | Target > StopJoin | 4805 > -3095 |
| 06-12 14:03 | P7 | long | 4 > 4 | rech (1 / 93 / 4.11) | Target > StopJoin | 4805 > -3075 |


**BO_P7_1Srev_G60_k1p50_S45**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 05-07 02:03 | K7 | long | none > 2 | n/a | none > Target | 0 > 2403 |
| 05-07 07:09 | K7 | long | none > 1 | n/a | none > StopJoinFallback | 0 > -1201 |
| 05-07 12:12 | K7 | long | none > 1 | n/a | none > Target | 0 > 1199 |
| 05-07 11:06 | K7 | long | none > 1 | n/a | none > StateCut | 0 > -655 |
| 05-22 10:05 | P7 | short | 4 > 4 | fresh (4 / 90 / 1.94) | StopJoin > StopJoin | -4820 > -4220 |


**BO_P7_1T_G30_k2p00_T45**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 08-26 03:03 | P7 | long | 7 > 7 | rech (4 / 39 / -3.56) | StateCut > Target | -7138 > 6292 |
| 08-12 02:49 | P7 | long | 7 > 7 | rech (3 / 10 / 3.78) | StateCut > Target | -6845 > 6287 |
| 03-11 22:42 | P7 | long | 7 > 7 | rech (1 / 997 / 2.10) | StopJoin > Target | -6658 > 6292 |
| 08-16 02:36 | P7 | long | 7 > 7 | rech (2 / 16 / 5.16) | StateCut > Target | -6055 > 6307 |
| 12-05 02:35 | P7 | long | 7 > 7 | rech (2 / 14 / 6.49) | StateCut > Target | -6003 > 6307 |


**BO_P7_1Trev_G15_k2p00_T45**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 04-30 22:21 | P7 | long | 7 > 7 | rech (1 / -1 / -0.32) | StateCut > Target | -6518 > 6282 |
| 10-01 22:24 | P7 | long | 7 > 7 | rech (1 / -1 / -0.35) | StateCut > Target | -6288 > 6302 |
| 07-02 22:07 | P7 | long | 7 > 7 | rech (1 / 368 / 0.64) | StateCut > Target | -6283 > 6307 |
| 02-01 23:41 | P7 | long | 7 > 7 | rech (1 / 420 / 0.38) | StateCut > Target | -6234 > 6282 |
| 08-19 22:22 | P7 | long | 7 > 7 | rech (1 / 384 / 1.08) | StateCut > Target | -6135 > 6297 |


**BO_P7_3SS_f0p50_a0p60_r0_rech**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 10-14 05:22 | P7 | short | none > 7 | rech (5 / 13 / -0.36) | none > Target | 0 > 8377 |
| 10-05 05:15 | P7 | short | 7 > 7 | rech (5 / 42 / 0.12) | Target > Target | 8407 > 477 |
| 06-17 02:22 | P7 | long | 7 > 7 | rech (4 / 8 / 27.81) | Target > Target | 8382 > 512 |
| 09-14 22:17 | P7 | short | 7 > 7 | rech (1 / 405 / 2.46) | Target > Target | 8387 > 537 |
| 06-18 23:01 | P7 | short | 7 > 7 | rech (1 / 1122 / 3.20) | Target > Target | 8407 > 857 |


**BO_P7_4PA_f0p50_p0p10_fresh_s1**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 05-18 22:16 | P7 | long | 7 > 7 | fresh (1 / 1072 / 0.72) | Target > StateCut | 8402 > -6355 |
| 08-26 03:03 | P7 | long | 7 > 5 | rech (4 / 40 / -3.56) | StateCut > Target | -7138 > 6004 |
| 10-05 05:15 | P7 | short | 7 > 4 | rech (4 / 42 / 0.12) | Target > StateCut | 8407 > -3199 |
| 07-07 06:54 | P7 | long | 4 > 4 | fresh (1 / 82 / -0.19) | Target > StateCut | 4800 > -3409 |
| 07-27 00:28 | P7 | short | 4 > 4 | fresh (2 / 39 / -2.90) | Target > StateCut | 4795 > -3289 |


**BO_P7_4PC_f0p50_N30_X10_fresh_s1**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 04-14 22:16 | P7 | short | 7 > 7 | fresh (1 / 430 / 0.83) | Target > StateCut | 8377 > -6296 |
| 03-18 22:05 | P7 | short | 7 > 7 | fresh (1 / 305 / 0.77) | Target > StateCut | 8392 > -5873 |
| 01-15 00:41 | P7 | long | 7 > 7 | fresh (1 / 478 / -2.53) | Target > StateCut | 8407 > -5805 |
| 05-28 22:21 | P7 | long | 7 > 7 | fresh (1 / 3223 / -1.39) | Target > StateCut | 8397 > -5775 |
| 02-14 23:16 | P7 | long | 7 > 7 | fresh (1 / 370 / 0.27) | Target > StateCut | 8402 > -5424 |


**BO_P7_6TL_N40_t0p25_flat_all**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 05-13 23:24 | P7 | long | 7 > 7 | rech (2 / 19 / 4.61) | Target > BoTimeL | 8392 > -3718 |
| 06-18 23:01 | P7 | short | 7 > 7 | rech (1 / 1122 / 3.20) | Target > BoTimeL | 8407 > -3388 |
| 07-30 22:45 | P7 | long | 4 > 4 | rech (2 / 17 / 2.22) | Target > BoTimeL | 4800 > -2760 |
| 10-28 01:47 | P7 | long | 4 > 4 | rech (3 / 5 / 3.30) | Target > BoTimeL | 4805 > -2675 |
| 10-07 11:28 | P7 | short | 4 > 4 | rech (5 / 7 / 10.35) | Target > BoTimeL | 4785 > -2215 |


**BO_P7_6TL_N5_t0p40_flat_all**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 08-19 23:09 | P7 | long | none > 7 | rech (3 / 2 / 4.63) | none > StateCut | 0 > -7545 |
| 07-02 14:40 | P7 | long | 4 > 4 | rech (2 / 25 / 3.25) | Target > BoTimeL | 4800 > -2700 |
| 05-08 02:34 | P7 | long | 4 > 4 | rech (4 / 12 / 11.20) | Target > BoTimeL | 4800 > -2530 |
| 02-12 23:05 | P7 | short | 4 > 4 | fresh (1 / 430 / 0.76) | Target > BoTimeL | 4800 > -2350 |
| 10-28 22:07 | P7 | short | 4 > 4 | rech (1 / 696 / 1.56) | Target > BoTimeL | 4790 > -2190 |


**BO_P7_6TL_N5_t0p40_flat_rech**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 08-19 23:09 | P7 | long | none > 7 | rech (3 / 2 / 4.63) | none > StateCut | 0 > -7545 |
| 07-02 14:40 | P7 | long | 4 > 4 | rech (2 / 25 / 3.25) | Target > BoTimeL | 4800 > -2700 |
| 05-08 02:34 | P7 | long | 4 > 4 | rech (4 / 12 / 11.20) | Target > BoTimeL | 4800 > -2530 |
| 10-28 22:07 | P7 | short | 4 > 4 | rech (1 / 696 / 1.56) | Target > BoTimeL | 4790 > -2190 |
| 03-12 14:32 | P7 | short | none > 4 | rech (1 / 68 / 3.35) | none > StateCut | 0 > -6264 |


**BO_P7_6TP_N5_p0p40_half_rech**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 06-26 02:33 | P7 | short | none > 7 | rech (9 / 9 / 8.13) | none > Target | 0 > 8407 |
| 07-30 03:31 | P7 | short | none > 7 | rech (9 / 19 / -7.56) | none > StateCut | 0 > -6173 |
| 05-13 04:38 | P7 | long | none > 7 | rech (6 / 8 / 9.08) | none > Target | 0 > 5947 |
| 07-03 02:40 | P7 | long | none > 7 | rech (4 / 14 / 5.23) | none > Target | 0 > 5494 |
| 07-13 05:01 | P7 | short | none > 7 | rech (7 / 25 / 14.59) | none > StateCut | 0 > -5320 |


**BO_P7_7C_W180_skip**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 08-19 23:06 | P7 | long | none > 7 | rech (2 / 4 / 4.23) | none > StateCut | 0 > -6103 |
| 07-22 23:19 | P7 | short | none > 7 | rech (2 / 15 / 1.83) | none > StateCut | 0 > -5830 |
| 07-09 06:09 | P7 | long | none > 4 | fresh (1 / 74 / -0.39) | none > Target | 0 > 4805 |
| 10-07 10:57 | P7 | short | none > 4 | rech (4 / 14 / 8.58) | none > Target | 0 > 4800 |
| 06-09 03:54 | P7 | long | none > 4 | rech (5 / 24 / 5.30) | none > Target | 0 > 4795 |


**BO_P7_7C_W300_half**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 07-06 04:52 | P7 | long | none > 4 | rech (9 / 33 / -3.47) | none > StateCut | 0 > -3489 |
| 07-22 23:05 | P7 | short | 7 > 4 | rech (2 / 1 / 2.10) | StateCut > StateCut | -6250 > -3499 |
| 07-06 01:58 | P7 | short | 7 > 4 | rech (5 / 7 / 3.97) | StateCut > StateCut | -5813 > -3219 |
| 09-28 01:16 | P7 | short | 4 > 2 | rech (3 / 0 / 3.09) | Target > Target | 4795 > 2393 |
| 10-07 10:53 | P7 | short | 3 > 1 | rech (4 / 10 / 9.07) | Target > Target | 3601 > 1199 |


**BO_P7_7C_W600_skip**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 08-15 05:55 | P7 | short | none > 7 | rech (3 / 4 / -4.08) | none > Target | 0 > 8397 |
| 04-06 01:17 | P7 | long | none > 7 | rech (3 / 77 / 5.71) | none > Target | 0 > 8392 |
| 11-20 00:36 | P7 | long | none > 7 | rech (2 / 36 / 5.38) | none > Target | 0 > 8387 |
| 06-23 05:52 | P7 | short | none > 7 | rech (7 / 25 / 16.40) | none > Target | 0 > 8387 |
| 08-05 04:25 | P7 | short | none > 7 | rech (8 / 16 / 12.25) | none > Target | 0 > 8382 |


**BO_P7_7N_n2_T45**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 06-03 23:12 | P7 | short | 7 > 7 | rech (3 / 15 / 1.11) | StateCut > Target | -3806 > 6292 |
| 06-01 00:38 | P7 | long | 7 > 7 | rech (3 / 17 / 6.07) | BookLock > Target | -2448 > 6277 |
| 06-23 02:37 | P7 | short | none > 7 | rech (4 / 28 / 6.53) | none > Target | 0 > 8402 |
| 09-28 12:27 | P7 | long | 4 > 4 | rech (5 / 21 / 2.09) | StateCut > Target | -3534 > 3600 |
| 07-17 08:30 | P7 | short | 4 > 4 | rech (3 / 14 / 3.82) | StateCut > Target | -3414 > 3600 |


**BO_P7_7N_n4_half**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 07-13 04:36 | P7 | long | 7 > 4 | rech (2 / 22 / 8.25) | Target > Target | 8377 > 4800 |
| 06-20 04:12 | P7 | long | 5 > 3 | rech (1 / 27 / 10.02) | Target > Target | 5999 > 3596 |
| 05-23 11:44 | P7 | short | 3 > 1 | rech (6 / 0 / 9.01) | Target > Target | 3596 > 1199 |
| 07-23 07:25 | P7 | short | 4 > 2 | rech (2 / 18 / 2.03) | Target > Target | 4785 > 2398 |
| 08-13 07:28 | P7 | long | 4 > 2 | rech (1 / 41 / 5.67) | StateCut > StateCut | -3464 > -1699 |


**BO_P7_7N_n4_skip**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 06-20 04:53 | P7 | long | none > 5 | rech (1 / 68 / 12.14) | none > Target | 0 > 6004 |
| 07-13 05:59 | P7 | short | none > 7 | fresh (2 / 105 / -6.73) | none > StateCut | 0 > -5823 |
| 07-13 08:34 | P7 | long | none > 3 | rech (1 / 11 / 4.62) | none > Target | 0 > 3591 |
| 08-13 08:11 | P7 | long | none > 4 | rech (1 / 84 / 4.70) | none > StateCut | 0 > -3364 |
| 08-13 09:08 | P7 | short | none > 2 | rech (2 / 0 / -2.25) | none > Target | 0 > 2398 |


**BO_P7_8T_T40**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 08-26 03:03 | P7 | long | 7 > 7 | rech (4 / 39 / -3.56) | StateCut > Target | -7138 > 5592 |
| 10-29 02:22 | P7 | short | 7 > 7 | rech (6 / 21 / 6.77) | StateCut > Target | -6495 > 5587 |
| 07-02 22:07 | P7 | long | 7 > 7 | fresh (1 / 365 / 0.64) | StateCut > Target | -6283 > 5607 |
| 10-08 22:09 | P7 | long | 7 > 7 | fresh (1 / 1236 / 0.51) | StateCut > Target | -6170 > 5597 |
| 07-02 01:30 | P7 | long | 7 > 7 | rech (5 / 66 / 3.07) | StateCut > Target | -6153 > 5597 |


**BO_P7_8T_T55**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 08-26 03:03 | P7 | long | 7 > 7 | rech (4 / 39 / -3.56) | StateCut > Target | -7138 > 7692 |
| 03-11 22:42 | P7 | long | 7 > 7 | rech (1 / 997 / 2.10) | StopJoin > Target | -6658 > 7692 |
| 08-19 22:22 | P7 | long | 7 > 7 | rech (1 / 384 / 1.08) | StateCut > Target | -6135 > 7697 |
| 05-10 22:21 | P7 | long | 7 > 7 | fresh (1 / 414 / 0.25) | StateCut > Target | -6133 > 7682 |
| 12-05 02:35 | P7 | long | 7 > 7 | rech (2 / 20 / 6.49) | StateCut > Target | -6003 > 7707 |


**BO_P7_8Tq_T40**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 08-26 03:03 | P7 | long | 7 > 7 | rech (4 / 39 / -3.56) | StateCut > Target | -7138 > 5592 |
| 10-29 02:22 | P7 | short | 7 > 7 | rech (6 / 21 / 6.77) | StateCut > Target | -6495 > 5587 |
| 07-02 22:07 | P7 | long | 7 > 7 | fresh (1 / 365 / 0.64) | StateCut > Target | -6283 > 5607 |
| 10-08 22:09 | P7 | long | 7 > 7 | fresh (1 / 1236 / 0.51) | StateCut > Target | -6170 > 5597 |
| 07-02 01:30 | P7 | long | 7 > 7 | rech (5 / 66 / 3.07) | StateCut > Target | -6153 > 5597 |


**BO_P7_BL_f0_r120**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 06-26 02:33 | P7 | short | none > 7 | rech (6 / 9 / 8.13) | none > Target | 0 > 8407 |
| 10-08 00:41 | P7 | short | none > 7 | rech (3 / 124 / 0.69) | none > Target | 0 > 8402 |
| 04-17 01:36 | P7 | long | none > 7 | rech (3 / 149 / 4.21) | none > Target | 0 > 8402 |
| 10-22 02:58 | P7 | short | none > 7 | rech (4 / 5 / 10.81) | none > Target | 0 > 8402 |
| 01-20 05:11 | P7 | short | none > 7 | rech (2 / 18 / 0.31) | none > Target | 0 > 8397 |


**BO_P7_BL_f30_r120**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 03-19 04:26 | P7 | short | none > 7 | rech (3 / 137 / -1.59) | none > Target | 0 > 8407 |
| 06-26 02:33 | P7 | short | none > 7 | rech (6 / 9 / 8.13) | none > Target | 0 > 8407 |
| 10-08 00:41 | P7 | short | none > 7 | rech (3 / 124 / 0.69) | none > Target | 0 > 8402 |
| 10-22 02:58 | P7 | short | none > 7 | rech (4 / 5 / 10.81) | none > Target | 0 > 8402 |
| 01-20 05:11 | P7 | short | none > 7 | rech (2 / 18 / 0.31) | none > Target | 0 > 8397 |


**BO_P7_BL_f30_r60**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 03-19 04:26 | P7 | short | none > 7 | rech (3 / 137 / -1.59) | none > Target | 0 > 8407 |
| 01-20 05:11 | P7 | short | none > 7 | rech (2 / 12 / 0.31) | none > Target | 0 > 8397 |
| 05-13 01:20 | P7 | long | none > 7 | rech (3 / 61 / 1.36) | none > Target | 0 > 8397 |
| 05-13 04:38 | P7 | long | none > 7 | rech (5 / 8 / 9.08) | none > Target | 0 > 8397 |
| 05-19 03:52 | P7 | short | none > 7 | rech (6 / 66 / 3.84) | none > Target | 0 > 8397 |


**BO_P7_BL_f30_r90**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 12-17 06:39 | P7 | long | none > 7 | rech (5 / 55 / 19.10) | none > Target | 0 > 8407 |
| 03-19 04:26 | P7 | short | none > 7 | rech (3 / 137 / -1.59) | none > Target | 0 > 8407 |
| 06-26 02:33 | P7 | short | none > 7 | rech (7 / 9 / 8.13) | none > Target | 0 > 8407 |
| 01-20 05:11 | P7 | short | none > 7 | rech (2 / 16 / 0.31) | none > Target | 0 > 8397 |
| 05-13 01:20 | P7 | long | none > 7 | rech (3 / 61 / 1.36) | none > Target | 0 > 8397 |


**BO_P7_NZF_all**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 03-11 22:42 | P7 | long | 7 > 7 | rech (1 / 997 / 2.10) | StopJoin > BoFloor | -6658 > 6974 |
| 08-19 22:22 | P7 | long | 7 > 7 | rech (1 / 384 / 1.08) | StateCut > BoFloor | -6135 > 6822 |
| 12-05 02:35 | P7 | long | 7 > 7 | rech (2 / 14 / 6.49) | StateCut > BoFloor | -6003 > 6884 |
| 08-26 03:03 | P7 | long | 7 > 7 | rech (4 / 39 / -3.56) | StateCut > BoFloor | -7138 > 5732 |
| 04-24 22:37 | P7 | short | 7 > 7 | fresh (1 / 408 / -0.43) | StateCut > BoFloor | -5905 > 6929 |


**BO_P7_NZF_fresh**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 07-02 22:07 | P7 | long | 7 > 7 | fresh (1 / 368 / 0.64) | StateCut > BoFloor | -6283 > 3314 |
| 09-08 00:46 | P7 | long | none > 7 | rech (3 / 7 / 1.32) | none > Target | 0 > 8407 |
| 08-24 23:54 | P7 | short | none > 7 | rech (2 / 3 / 3.89) | none > Target | 0 > 8402 |
| 07-03 02:40 | P7 | long | none > 7 | rech (4 / 14 / 5.23) | none > Target | 0 > 8382 |
| 05-12 00:20 | P7 | short | none > 7 | rech (2 / 14 / 0.36) | none > Target | 0 > 7183 |


**BO_P7_NZF_rech**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 08-26 03:03 | P7 | long | 7 > 7 | rech (4 / 39 / -3.56) | StateCut > BoFloor | -7138 > 5732 |
| 07-28 05:40 | P7 | short | 7 > 7 | rech (8 / 17 / 10.80) | StateCut > BoFloor | -6005 > 5727 |
| 09-10 05:07 | P7 | long | 7 > 5 | rech (3 / 17 / -0.56) | StateCut > BoFloor | -6059 > 4082 |
| 08-25 05:41 | P7 | long | none > 7 | rech (5 / 3 / 4.15) | none > Target | 0 > 8407 |
| 10-22 04:49 | P7 | short | none > 7 | rech (7 / 11 / 17.16) | none > Target | 0 > 8407 |


**BO_U7_1S_G60_k2p00_S45**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 07-20 07:40 | U7 | long | 4 > 4 | rech (2 / 40 / 3.37) | Target > StopJoinFallback | 4790 > -3815 |
| 08-07 06:30 | U7 | long | 4 > 4 | rech (1 / 300 / 2.64) | Target > StopJoin | 3596 > -2614 |
| 06-12 05:50 | U7 | short | 1 > 1 | rech (1 / 1716 / 2.47) | Target > StopJoin | 2398 > -1752 |
| 05-21 05:50 | U7 | short | 2 > 2 | rech (3 / 212 / -3.80) | Target > StopJoinFallback | 2393 > -1752 |
| 09-10 05:00 | U7 | long | none > 4 | rech (3 / 6 / 0.65) | none > StopJoinFallback | 0 > -3445 |


**BO_U7_1Srev_G15_k0p75_S45**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 07-20 07:40 | U7 | long | 4 > 4 | fresh (2 / 40 / 3.37) | Target > StopJoin | 4790 > -4430 |
| 07-08 12:10 | U7 | long | 4 > 4 | rech (1 / 382 / -3.86) | Target > StopJoin | 4790 > -3410 |
| 07-14 00:40 | U7 | long | 2 > 2 | rech (1 / 820 / 0.36) | Target > StopJoin | 2398 > -1802 |
| 07-14 00:33 | P7 | long | 4 > 4 | n/a | Target > Target | 3601 > -124 |
| 10-20 02:06 | P7 | long | 4 > 4 | n/a | Target > Target | 3601 > 11 |


**BO_U7_3SS_f0p33_a0p75_r0_rech**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 08-13 00:10 | U7 | long | 4 > 4 | rech (1 / 2226 / 1.43) | Target > Target | 4790 > 2640 |
| 07-20 07:40 | U7 | long | 4 > 4 | rech (2 / 40 / 3.37) | Target > Target | 4790 > 2643 |
| 08-07 06:30 | U7 | long | 4 > 4 | rech (1 / 300 / 2.64) | Target > Target | 3596 > 1454 |
| 09-07 10:50 | U7 | short | 4 > 4 | rech (1 / 4220 / 1.55) | Target > Target | 4785 > 2648 |
| 06-12 05:50 | U7 | short | 1 > 1 | rech (1 / 1716 / 2.47) | Target > Target | 2398 > 268 |


**BO_U7_6TL_N20_t0p40_flat_all**

| time (UTC) | book | side | lots live > new | entry tag (n_sess / gap min / chase k) | exit live > new | pnl live > new |
|--|--|--|--|--|--|--|
| 10-14 08:20 | U7 | long | 4 > 4 | rech (1 / 135 / 4.31) | StopJoinFallback > BoTimeL | -4690 > -3110 |
| 10-28 09:30 | U7 | short | 2 > 2 | fresh (1 / 1368 / 0.87) | StopJoin > BoTimeL | -2337 > -1232 |
| 09-02 23:10 | P7 | short | 4 > 4 | n/a | StateCut > StateCut | -2492 > -3524 |
| 09-04 07:00 | U7 | short | 4 > 4 | rech (1 / 323 / 2.61) | StopJoin > BoTimeL | -3509 > -2511 |
| 10-14 09:30 | U7 | short | 2 > 2 | fresh (2 / 50 / -0.01) | StopJoinFallback > BoTimeL | -2512 > -1852 |


## 4b. Behaviour scorecard (a-e) and the competent-trader acceptance test, exact finalists

The scorecard line is the stack for L6M with the set against LPB_BASE (a: full stops, b: give-backs and round-trips, c: same-side losing runs, d: entries with no new evidence, e: what it cost). The acceptance line counts how many of the 20 worst P7 sessions still take a third consecutive same-side losing entry without new evidence (PASS only if no more than 2 of 20 fail).

- LPB_BASE (the live stack, reference): (stack, per week): full stops 24.5/wk $-40052; give-backs 9.1/wk (9.0 round-trips) realised $-14009, forgone vs target $35376; same-side losing runs max 12, p95 6, $-51344 lost on 3rd-and-later; no-new-evidence re-entries 37.3/wk $-363; recoveries cut 13.7/wk $46863, clipped fills 0.0/wk $0; pnl $19784/wk. ACCEPT LPB_BASE FAIL fails=3/20.
- BO_K7_1C_m0p50_T30_S60: (stack, per week): full stops 26.6/wk $-39750; give-backs 6.1/wk (6.0 round-trips) realised $-10892, forgone vs target $27992; same-side losing runs max 12, p95 5, $-38492 lost on 3rd-and-later; no-new-evidence re-entries 42.0/wk $-305; recoveries cut 14.2/wk $47258, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $4196/wk, losers avoided $3365/wk, net -161 $/wk; pnl $19623/wk. ACCEPT BO_K7_1C_m0p50_T30_S60 FAIL fails=3/20
- BO_K7_1L_G30_k1p00_m0p50: (stack, per week): full stops 25.9/wk $-39203; give-backs 9.2/wk (9.1 round-trips) realised $-13574, forgone vs target $34384; same-side losing runs max 12, p95 6, $-51409 lost on 3rd-and-later; no-new-evidence re-entries 39.6/wk $-124; recoveries cut 14.6/wk $47839, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $1561/wk, losers avoided $1261/wk, net -1422 $/wk; pnl $18362/wk. ACCEPT BO_K7_1L_G30_k1p00_m0p50 FAIL fails=3/20
- BO_K7_1Lrev_G15_k2p00_m0p50: (stack, per week): full stops 24.7/wk $-39660; give-backs 9.1/wk (9.0 round-trips) realised $-13862, forgone vs target $35150; same-side losing runs max 12, p95 6, $-51214 lost on 3rd-and-later; no-new-evidence re-entries 37.5/wk $-445; recoveries cut 13.6/wk $46586, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $673/wk, losers avoided $636/wk, net -299 $/wk; pnl $19485/wk. ACCEPT BO_K7_1Lrev_G15_k2p00_m0p50 FAIL fails=3/20
- BO_K7_1S_G30_k1p50_S45: (stack, per week): full stops 12.8/wk $-23047; give-backs 9.3/wk (9.0 round-trips) realised $-12912, forgone vs target $34503; same-side losing runs max 12, p95 6, $-52691 lost on 3rd-and-later; no-new-evidence re-entries 40.3/wk $784; recoveries cut 12.8/wk $45072, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $5175/wk, losers avoided $4906/wk, net +1773 $/wk; pnl $21556/wk. ACCEPT BO_K7_1S_G30_k1p50_S45 FAIL fails=3/20
- BO_K7_1Srev_G60_k0p75_S45: (stack, per week): full stops 24.0/wk $-39243; give-backs 9.0/wk (8.9 round-trips) realised $-13875, forgone vs target $35094; same-side losing runs max 12, p95 6, $-51125 lost on 3rd-and-later; no-new-evidence re-entries 37.5/wk $-683; recoveries cut 13.8/wk $47015, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $1088/wk, losers avoided $1157/wk, net -294 $/wk; pnl $19490/wk. ACCEPT BO_K7_1Srev_G60_k0p75_S45 FAIL fails=3/20
- BO_K7_1T_G60_k1p50_T30: (stack, per week): full stops 26.2/wk $-42186; give-backs 6.1/wk (6.0 round-trips) realised $-10786, forgone vs target $27791; same-side losing runs max 12, p95 5, $-39787 lost on 3rd-and-later; no-new-evidence re-entries 40.1/wk $-888; recoveries cut 13.2/wk $45729, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $4303/wk, losers avoided $4103/wk, net -244 $/wk; pnl $19540/wk. ACCEPT BO_K7_1T_G60_k1p50_T30 FAIL fails=3/20
- BO_K7_1Trev_G15_k1p00_T30: (stack, per week): full stops 24.4/wk $-39800; give-backs 8.8/wk (8.8 round-trips) realised $-13632, forgone vs target $34560; same-side losing runs max 12, p95 6, $-50844 lost on 3rd-and-later; no-new-evidence re-entries 37.3/wk $259; recoveries cut 13.6/wk $46593, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $2573/wk, losers avoided $3266/wk, net +231 $/wk; pnl $20015/wk. ACCEPT BO_K7_1Trev_G15_k1p00_T30 FAIL fails=3/20
- BO_K7_6TL_N10_t0p25_flat_rech: (stack, per week): full stops 21.6/wk $-36095; give-backs 8.9/wk (8.8 round-trips) realised $-13517, forgone vs target $34270; same-side losing runs max 12, p95 6, $-51951 lost on 3rd-and-later; no-new-evidence re-entries 39.4/wk $-10; recoveries cut 13.0/wk $45388, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $3565/wk, losers avoided $3875/wk, net +1268 $/wk; pnl $21052/wk. ACCEPT BO_K7_6TL_N10_t0p25_flat_rech FAIL fails=3/20
- BO_K7_6TL_N10_t0p40_half_rech: (stack, per week): full stops 23.6/wk $-38873; give-backs 9.2/wk (9.1 round-trips) realised $-13924, forgone vs target $35066; same-side losing runs max 12, p95 6, $-52020 lost on 3rd-and-later; no-new-evidence re-entries 38.7/wk $-210; recoveries cut 13.6/wk $46531, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $1317/wk, losers avoided $1343/wk, net +889 $/wk; pnl $20673/wk. ACCEPT BO_K7_6TL_N10_t0p40_half_rech FAIL fails=3/20
- BO_K7_6TP_N10_p0p10_flat_rech: (stack, per week): full stops 19.2/wk $-32746; give-backs 9.2/wk (9.1 round-trips) realised $-13776, forgone vs target $34948; same-side losing runs max 12, p95 7, $-54132 lost on 3rd-and-later; no-new-evidence re-entries 52.7/wk $259; recoveries cut 12.7/wk $44468, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $8497/wk, losers avoided $8084/wk, net -2146 $/wk; pnl $17638/wk. ACCEPT BO_K7_6TP_N10_p0p10_flat_rech FAIL fails=3/20
- BO_K7_7C_W300_skip: (stack, per week): full stops 24.7/wk $-40321; give-backs 8.9/wk (8.8 round-trips) realised $-13894, forgone vs target $35036; same-side losing runs max 12, p95 6, $-50379 lost on 3rd-and-later; no-new-evidence re-entries 36.8/wk $-648; recoveries cut 13.6/wk $46543, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $3776/wk, losers avoided $3976/wk, net +174 $/wk; pnl $19958/wk. ACCEPT BO_K7_7C_W300_skip FAIL fails=3/20
- BO_K7_7C_W600_T30: (stack, per week): full stops 24.8/wk $-40633; give-backs 9.0/wk (8.9 round-trips) realised $-13784, forgone vs target $34956; same-side losing runs max 12, p95 6, $-50685 lost on 3rd-and-later; no-new-evidence re-entries 37.6/wk $-561; recoveries cut 13.8/wk $46840, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $1232/wk, losers avoided $1022/wk, net +275 $/wk; pnl $20059/wk. ACCEPT BO_K7_7C_W600_T30 FAIL fails=3/20
- BO_K7_7N_n2_T45: (stack, per week): full stops 24.9/wk $-40751; give-backs 8.9/wk (8.8 round-trips) realised $-13797, forgone vs target $34872; same-side losing runs max 12, p95 6, $-51120 lost on 3rd-and-later; no-new-evidence re-entries 37.6/wk $-779; recoveries cut 13.6/wk $46678, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $455/wk, losers avoided $378/wk, net -155 $/wk; pnl $19629/wk. ACCEPT BO_K7_7N_n2_T45 FAIL fails=3/20
- BO_K7_7N_n3_half: (stack, per week): full stops 24.5/wk $-40004; give-backs 9.1/wk (9.0 round-trips) realised $-13978, forgone vs target $35297; same-side losing runs max 12, p95 6, $-51353 lost on 3rd-and-later; no-new-evidence re-entries 37.3/wk $-403; recoveries cut 13.7/wk $46793, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $0/wk, losers avoided $-0/wk, net -16 $/wk; pnl $19768/wk. ACCEPT BO_K7_7N_n3_half FAIL fails=3/20
- BO_K7_8T_T35: (stack, per week): full stops 25.8/wk $-41711; give-backs 5.9/wk (5.8 round-trips) realised $-10355, forgone vs target $26774; same-side losing runs max 12, p95 5, $-42739 lost on 3rd-and-later; no-new-evidence re-entries 39.9/wk $-367; recoveries cut 13.1/wk $45907, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $6898/wk, losers avoided $6012/wk, net +374 $/wk; pnl $20158/wk. ACCEPT BO_K7_8T_T35 FAIL fails=3/20
- BO_K7_8Tq_T35: (stack, per week): full stops 25.8/wk $-41711; give-backs 5.9/wk (5.8 round-trips) realised $-10355, forgone vs target $26774; same-side losing runs max 12, p95 5, $-42739 lost on 3rd-and-later; no-new-evidence re-entries 39.9/wk $-367; recoveries cut 13.1/wk $45907, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $6898/wk, losers avoided $6012/wk, net +374 $/wk; pnl $20158/wk. ACCEPT BO_K7_8Tq_T35 FAIL fails=3/20
- BO_K7x3_1C_m0p50_T30_S60: (stack, per week): full stops 20.3/wk $-44372; give-backs 6.1/wk (6.1 round-trips) realised $-11030, forgone vs target $28471; same-side losing runs max 12, p95 5, $-38076 lost on 3rd-and-later; no-new-evidence re-entries 28.9/wk $375; recoveries cut 10.9/wk $44291, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $18037/wk, losers avoided $18917/wk, net +4372 $/wk; pnl $24156/wk. ACCEPT BO_K7x3_1C_m0p50_T30_S60 FAIL fails=3/20
- BO_K7x3_1L_G30_k1p50_m0p33: (stack, per week): full stops 22.3/wk $-40609; give-backs 8.4/wk (8.3 round-trips) realised $-13371, forgone vs target $33940; same-side losing runs max 11, p95 6, $-47219 lost on 3rd-and-later; no-new-evidence re-entries 32.7/wk $-1047; recoveries cut 12.5/wk $45305, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $11532/wk, losers avoided $11039/wk, net +117 $/wk; pnl $19901/wk. ACCEPT BO_K7x3_1L_G30_k1p50_m0p33 FAIL fails=3/20
- BO_K7x3_1Lrev_G15_k1p00_m0p33: (stack, per week): full stops 17.3/wk $-39296; give-backs 7.2/wk (7.1 round-trips) realised $-12631, forgone vs target $32837; same-side losing runs max 11, p95 5, $-43796 lost on 3rd-and-later; no-new-evidence re-entries 25.6/wk $-250; recoveries cut 10.5/wk $43499, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $25971/wk, losers avoided $24520/wk, net -1455 $/wk; pnl $18329/wk. ACCEPT BO_K7x3_1Lrev_G15_k1p00_m0p33 FAIL fails=3/20
- BO_K7x3_1S_G30_k1p50_S45: (stack, per week): full stops 12.5/wk $-25563; give-backs 7.1/wk (6.8 round-trips) realised $-11997, forgone vs target $31930; same-side losing runs max 11, p95 5, $-42132 lost on 3rd-and-later; no-new-evidence re-entries 25.5/wk $854; recoveries cut 10.1/wk $41578, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $28795/wk, losers avoided $27575/wk, net +2018 $/wk; pnl $21802/wk. ACCEPT BO_K7x3_1S_G30_k1p50_S45 FAIL fails=3/20
- BO_K7x3_1Srev_G60_k0p75_S45: (stack, per week): full stops 16.0/wk $-35826; give-backs 6.9/wk (6.8 round-trips) realised $-12245, forgone vs target $31473; same-side losing runs max 11, p95 5, $-41201 lost on 3rd-and-later; no-new-evidence re-entries 24.9/wk $4; recoveries cut 10.3/wk $43188, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $27304/wk, losers avoided $27096/wk, net +2089 $/wk; pnl $21872/wk. ACCEPT BO_K7x3_1Srev_G60_k0p75_S45 FAIL fails=3/20
- BO_K7x3_1T_G60_k1p50_T30: (stack, per week): full stops 18.1/wk $-43427; give-backs 6.1/wk (6.0 round-trips) realised $-10651, forgone vs target $27705; same-side losing runs max 12, p95 5, $-36009 lost on 3rd-and-later; no-new-evidence re-entries 26.2/wk $328; recoveries cut 10.3/wk $43588, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $25218/wk, losers avoided $24579/wk, net +3767 $/wk; pnl $23551/wk. ACCEPT BO_K7x3_1T_G60_k1p50_T30 FAIL fails=3/20
- BO_K7x3_1Trev_G15_k1p00_T30: (stack, per week): full stops 16.8/wk $-39187; give-backs 7.0/wk (6.9 round-trips) realised $-12359, forgone vs target $32019; same-side losing runs max 11, p95 5, $-41543 lost on 3rd-and-later; no-new-evidence re-entries 24.6/wk $776; recoveries cut 10.2/wk $42694, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $27402/wk, losers avoided $26393/wk, net +1888 $/wk; pnl $21672/wk. ACCEPT BO_K7x3_1Trev_G15_k1p00_T30 FAIL fails=3/20
- BO_K7x3_3SS_f0p33_a0p60_r1_fresh: (stack, per week): full stops 16.0/wk $-36492; give-backs 7.1/wk (6.8 round-trips) realised $-12343, forgone vs target $32257; same-side losing runs max 11, p95 5, $-41743 lost on 3rd-and-later; no-new-evidence re-entries 24.7/wk $-635; recoveries cut 10.3/wk $43218, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $27596/wk, losers avoided $26576/wk, net +77 $/wk; pnl $19861/wk. ACCEPT BO_K7x3_3SS_f0p33_a0p60_r1_fresh FAIL fails=3/20
- BO_K7x3_3SS_f0p50_a0p60_r1_fresh: (stack, per week): full stops 15.8/wk $-35756; give-backs 7.0/wk (6.9 round-trips) realised $-12412, forgone vs target $32082; same-side losing runs max 11, p95 5, $-42238 lost on 3rd-and-later; no-new-evidence re-entries 24.8/wk $-194; recoveries cut 10.3/wk $43177, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $27389/wk, losers avoided $26389/wk, net +443 $/wk; pnl $20227/wk. ACCEPT BO_K7x3_3SS_f0p50_a0p60_r1_fresh FAIL fails=3/20
- BO_K7x3_4PA_f0p33_p0p10_fresh_s0: (stack, per week): full stops 21.3/wk $-39123; give-backs 8.3/wk (8.1 round-trips) realised $-12859, forgone vs target $34273; same-side losing runs max 12, p95 6, $-45459 lost on 3rd-and-later; no-new-evidence re-entries 31.9/wk $-595; recoveries cut 12.7/wk $46298, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $13408/wk, losers avoided $12435/wk, net +256 $/wk; pnl $20040/wk. ACCEPT BO_K7x3_4PA_f0p33_p0p10_fresh_s0 FAIL fails=3/20
- BO_K7x3_4PC_f0p33_N300_X5_all_s0: (stack, per week): full stops 19.5/wk $-39367; give-backs 7.7/wk (7.4 round-trips) realised $-12743, forgone vs target $33211; same-side losing runs max 12, p95 5, $-47675 lost on 3rd-and-later; no-new-evidence re-entries 30.8/wk $-1171; recoveries cut 12.0/wk $45729, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $18337/wk, losers avoided $16740/wk, net +169 $/wk; pnl $19953/wk. ACCEPT BO_K7x3_4PC_f0p33_N300_X5_all_s0 FAIL fails=3/20
- BO_K7x3_6TL_N10_t0p25_flat_rech: (stack, per week): full stops 15.7/wk $-35012; give-backs 7.1/wk (6.8 round-trips) realised $-12241, forgone vs target $32417; same-side losing runs max 11, p95 5, $-42066 lost on 3rd-and-later; no-new-evidence re-entries 26.1/wk $162; recoveries cut 10.1/wk $42543, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $27157/wk, losers avoided $26239/wk, net +1962 $/wk; pnl $21746/wk. ACCEPT BO_K7x3_6TL_N10_t0p25_flat_rech FAIL fails=3/20
- BO_K7x3_6TP_N20_p0p40_flat_rech: (stack, per week): full stops 15.1/wk $-31999; give-backs 7.4/wk (6.8 round-trips) realised $-11819, forgone vs target $32811; same-side losing runs max 11, p95 5, $-42771 lost on 3rd-and-later; no-new-evidence re-entries 33.0/wk $-133; recoveries cut 10.3/wk $43504, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $25977/wk, losers avoided $24585/wk, net -1102 $/wk; pnl $18682/wk. ACCEPT BO_K7x3_6TP_N20_p0p40_flat_rech FAIL fails=3/20
- BO_K7x3_7C_W300_skip: (stack, per week): full stops 16.2/wk $-36928; give-backs 7.0/wk (6.8 round-trips) realised $-12396, forgone vs target $32133; same-side losing runs max 11, p95 5, $-40535 lost on 3rd-and-later; no-new-evidence re-entries 24.1/wk $-484; recoveries cut 10.1/wk $42288, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $28885/wk, losers avoided $27891/wk, net +1132 $/wk; pnl $20916/wk. ACCEPT BO_K7x3_7C_W300_skip FAIL fails=3/20
- BO_K7x3_7C_W600_T30: (stack, per week): full stops 16.7/wk $-38867; give-backs 7.2/wk (7.0 round-trips) realised $-12568, forgone vs target $32921; same-side losing runs max 11, p95 5, $-40884 lost on 3rd-and-later; no-new-evidence re-entries 24.7/wk $381; recoveries cut 10.3/wk $43364, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $27889/wk, losers avoided $26713/wk, net +537 $/wk; pnl $20321/wk. ACCEPT BO_K7x3_7C_W600_T30 FAIL fails=3/20
- BO_K7x3_7N_n2_skip: (stack, per week): full stops 15.9/wk $-35829; give-backs 7.0/wk (6.9 round-trips) realised $-12228, forgone vs target $31898; same-side losing runs max 11, p95 5, $-40294 lost on 3rd-and-later; no-new-evidence re-entries 24.4/wk $179; recoveries cut 10.3/wk $43600, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $29255/wk, losers avoided $27924/wk, net +1377 $/wk; pnl $21161/wk. ACCEPT BO_K7x3_7N_n2_skip FAIL fails=3/20
- BO_K7x3_8T_T35: (stack, per week): full stops 17.9/wk $-42661; give-backs 6.0/wk (5.9 round-trips) realised $-10387, forgone vs target $27002; same-side losing runs max 11, p95 5, $-40735 lost on 3rd-and-later; no-new-evidence re-entries 26.2/wk $128; recoveries cut 10.5/wk $43967, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $25905/wk, losers avoided $25189/wk, net +2674 $/wk; pnl $22458/wk. ACCEPT BO_K7x3_8T_T35 FAIL fails=3/20
- BO_K7x3_8Tq_T35: (stack, per week): full stops 17.9/wk $-42661; give-backs 6.0/wk (5.9 round-trips) realised $-10387, forgone vs target $27002; same-side losing runs max 11, p95 5, $-40735 lost on 3rd-and-later; no-new-evidence re-entries 26.2/wk $128; recoveries cut 10.5/wk $43967, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $25905/wk, losers avoided $25189/wk, net +2674 $/wk; pnl $22458/wk. ACCEPT BO_K7x3_8Tq_T35 FAIL fails=3/20
- BO_K7x3_REF: (stack, per week): full stops 16.3/wk $-37273; give-backs 7.1/wk (6.9 round-trips) realised $-12394, forgone vs target $32162; same-side losing runs max 11, p95 5, $-40804 lost on 3rd-and-later; no-new-evidence re-entries 24.5/wk $192; recoveries cut 10.2/wk $42857, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $28035/wk, losers avoided $26930/wk, net +1330 $/wk; pnl $21114/wk. ACCEPT BO_K7x3_REF FAIL fails=3/20
- BO_K7x3_RUNG_T30_f0p33_fl0_through1: (stack, per week): full stops 16.3/wk $-37273; give-backs 7.1/wk (6.9 round-trips) realised $-12394, forgone vs target $32162; same-side losing runs max 11, p95 5, $-40668 lost on 3rd-and-later; no-new-evidence re-entries 24.5/wk $192; recoveries cut 10.2/wk $42857, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $28035/wk, losers avoided $26908/wk, net +1317 $/wk; pnl $21101/wk. ACCEPT BO_K7x3_RUNG_T30_f0p33_fl0_through1 FAIL fails=3/20
- BO_K7x3_RUNG_T30_f0p33_fl0_touch: (stack, per week): full stops 16.3/wk $-37273; give-backs 7.1/wk (6.9 round-trips) realised $-12394, forgone vs target $32162; same-side losing runs max 11, p95 5, $-40668 lost on 3rd-and-later; no-new-evidence re-entries 24.5/wk $192; recoveries cut 10.2/wk $42857, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $28035/wk, losers avoided $26908/wk, net +1317 $/wk; pnl $21101/wk. ACCEPT BO_K7x3_RUNG_T30_f0p33_fl0_touch FAIL fails=3/20
- BO_K7x3_RUNG_T30_f0p5_fl2_through1: (stack, per week): full stops 17.5/wk $-40057; give-backs 7.9/wk (6.7 round-trips) realised $-11172, forgone vs target $33728; same-side losing runs max 11, p95 5, $-40991 lost on 3rd-and-later; no-new-evidence re-entries 25.9/wk $-268; recoveries cut 10.0/wk $41769, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $25291/wk, losers avoided $23970/wk, net +3244 $/wk; pnl $23027/wk. ACCEPT BO_K7x3_RUNG_T30_f0p5_fl2_through1 FAIL fails=3/20
- BO_K7x3_RUNG_T30_f0p5_fl2_touch: (stack, per week): full stops 17.6/wk $-40208; give-backs 7.9/wk (6.7 round-trips) realised $-11197, forgone vs target $33619; same-side losing runs max 11, p95 5, $-40962 lost on 3rd-and-later; no-new-evidence re-entries 26.0/wk $-147; recoveries cut 10.0/wk $41946, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $25438/wk, losers avoided $23953/wk, net +2956 $/wk; pnl $22740/wk. ACCEPT BO_K7x3_RUNG_T30_f0p5_fl2_touch FAIL fails=3/20
- BO_P7_1C_m0p50_T45_S60: (stack, per week): full stops 24.6/wk $-39629; give-backs 7.4/wk (7.3 round-trips) realised $-8906, forgone vs target $21913; same-side losing runs max 11, p95 6, $-42763 lost on 3rd-and-later; no-new-evidence re-entries 42.7/wk $2379; recoveries cut 15.1/wk $42405, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $7172/wk, losers avoided $4236/wk, net -1846 $/wk; pnl $17938/wk. ACCEPT BO_P7_1C_m0p50_T45_S60 FAIL fails=3/20
- BO_P7_1L_G15_k1p00_m0p50: (stack, per week): full stops 24.8/wk $-39858; give-backs 9.4/wk (9.4 round-trips) realised $-12201, forgone vs target $30097; same-side losing runs max 11, p95 6, $-45073 lost on 3rd-and-later; no-new-evidence re-entries 41.1/wk $1234; recoveries cut 14.4/wk $39755, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $1269/wk, losers avoided $1113/wk, net +218 $/wk; pnl $20002/wk. ACCEPT BO_P7_1L_G15_k1p00_m0p50 FAIL fails=3/20
- BO_P7_1Lrev_G60_k1p50_m0p33: (stack, per week): full stops 24.5/wk $-40052; give-backs 9.1/wk (9.0 round-trips) realised $-13722, forgone vs target $34489; same-side losing runs max 9, p95 6, $-52664 lost on 3rd-and-later; no-new-evidence re-entries 38.2/wk $-276; recoveries cut 13.9/wk $47199, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $1952/wk, losers avoided $1905/wk, net +813 $/wk; pnl $20597/wk. ACCEPT BO_P7_1Lrev_G60_k1p50_m0p33 FAIL fails=3/20
- BO_P7_1S_G15_k0p75_S45: (stack, per week): full stops 23.2/wk $-38489; give-backs 9.0/wk (8.9 round-trips) realised $-13244, forgone vs target $33799; same-side losing runs max 12, p95 6, $-50546 lost on 3rd-and-later; no-new-evidence re-entries 37.1/wk $-8; recoveries cut 12.9/wk $39008, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $2439/wk, losers avoided $2398/wk, net -40 $/wk; pnl $19744/wk. ACCEPT BO_P7_1S_G15_k0p75_S45 FAIL fails=3/20
- BO_P7_1Srev_G60_k1p50_S45: (stack, per week): full stops 24.4/wk $-39574; give-backs 9.0/wk (9.0 round-trips) realised $-13918, forgone vs target $35187; same-side losing runs max 12, p95 6, $-51307 lost on 3rd-and-later; no-new-evidence re-entries 37.3/wk $-334; recoveries cut 13.6/wk $46323, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $0/wk, losers avoided $-0/wk, net +154 $/wk; pnl $19938/wk. ACCEPT BO_P7_1Srev_G60_k1p50_S45 FAIL fails=3/20
- BO_P7_1T_G30_k2p00_T45: (stack, per week): full stops 24.5/wk $-39981; give-backs 7.4/wk (7.3 round-trips) realised $-8891, forgone vs target $21898; same-side losing runs max 12, p95 6, $-50457 lost on 3rd-and-later; no-new-evidence re-entries 39.0/wk $2042; recoveries cut 14.1/wk $50576, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $6635/wk, losers avoided $5069/wk, net -286 $/wk; pnl $19498/wk. ACCEPT BO_P7_1T_G30_k2p00_T45 FAIL fails=3/20
- BO_P7_1Trev_G15_k2p00_T45: (stack, per week): full stops 24.5/wk $-40154; give-backs 9.0/wk (8.9 round-trips) realised $-14065, forgone vs target $35008; same-side losing runs max 12, p95 6, $-52564 lost on 3rd-and-later; no-new-evidence re-entries 38.1/wk $896; recoveries cut 13.8/wk $47428, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $3219/wk, losers avoided $3505/wk, net +306 $/wk; pnl $20090/wk. ACCEPT BO_P7_1Trev_G15_k2p00_T45 PASS fails=2/20
- BO_P7_3SS_f0p50_a0p60_r0_rech: (stack, per week): full stops 24.3/wk $-39116; give-backs 9.1/wk (9.0 round-trips) realised $-13756, forgone vs target $35203; same-side losing runs max 12, p95 6, $-51304 lost on 3rd-and-later; no-new-evidence re-entries 37.6/wk $-394; recoveries cut 13.8/wk $47245, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $2000/wk, losers avoided $1169/wk, net -1106 $/wk; pnl $18678/wk. ACCEPT BO_P7_3SS_f0p50_a0p60_r0_rech FAIL fails=3/20
- BO_P7_4PA_f0p50_p0p10_fresh_s1: (stack, per week): full stops 24.8/wk $-39861; give-backs 9.4/wk (9.3 round-trips) realised $-12225, forgone vs target $30012; same-side losing runs max 13, p95 7, $-46999 lost on 3rd-and-later; no-new-evidence re-entries 41.9/wk $808; recoveries cut 14.7/wk $40936, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $2733/wk, losers avoided $3318/wk, net -924 $/wk; pnl $18860/wk. ACCEPT BO_P7_4PA_f0p50_p0p10_fresh_s1 FAIL fails=3/20
- BO_P7_4PC_f0p50_N30_X10_fresh_s1: (stack, per week): full stops 24.7/wk $-39717; give-backs 9.5/wk (9.4 round-trips) realised $-12513, forgone vs target $30789; same-side losing runs max 13, p95 6, $-46682 lost on 3rd-and-later; no-new-evidence re-entries 41.8/wk $1193; recoveries cut 14.6/wk $41002, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $1903/wk, losers avoided $2445/wk, net +129 $/wk; pnl $19913/wk. ACCEPT BO_P7_4PC_f0p50_N30_X10_fresh_s1 PASS fails=2/20
- BO_P7_6TL_N40_t0p25_flat_all: (stack, per week): full stops 24.6/wk $-40230; give-backs 9.0/wk (9.0 round-trips) realised $-13839, forgone vs target $35011; same-side losing runs max 11, p95 6, $-51740 lost on 3rd-and-later; no-new-evidence re-entries 38.1/wk $-1566; recoveries cut 13.6/wk $46185, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $2294/wk, losers avoided $3548/wk, net -1766 $/wk; pnl $18017/wk. ACCEPT BO_P7_6TL_N40_t0p25_flat_all FAIL fails=3/20
- BO_P7_6TL_N5_t0p40_flat_all: (stack, per week): full stops 24.5/wk $-39861; give-backs 9.1/wk (9.0 round-trips) realised $-14146, forgone vs target $35708; same-side losing runs max 12, p95 6, $-51370 lost on 3rd-and-later; no-new-evidence re-entries 37.7/wk $-313; recoveries cut 13.6/wk $46497, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $147/wk, losers avoided $337/wk, net +658 $/wk; pnl $20441/wk. ACCEPT BO_P7_6TL_N5_t0p40_flat_all FAIL fails=3/20
- BO_P7_6TL_N5_t0p40_flat_rech: (stack, per week): full stops 24.5/wk $-39861; give-backs 9.1/wk (9.0 round-trips) realised $-14146, forgone vs target $35708; same-side losing runs max 12, p95 6, $-51359 lost on 3rd-and-later; no-new-evidence re-entries 37.6/wk $-361; recoveries cut 13.6/wk $46497, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $147/wk, losers avoided $337/wk, net +619 $/wk; pnl $20403/wk. ACCEPT BO_P7_6TL_N5_t0p40_flat_rech FAIL fails=3/20
- BO_P7_6TP_N5_p0p40_half_rech: (stack, per week): full stops 24.3/wk $-39188; give-backs 9.4/wk (9.2 round-trips) realised $-12436, forgone vs target $34206; same-side losing runs max 12, p95 6, $-46041 lost on 3rd-and-later; no-new-evidence re-entries 41.8/wk $57; recoveries cut 14.1/wk $46611, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $1761/wk, losers avoided $1333/wk, net -3293 $/wk; pnl $16491/wk. ACCEPT BO_P7_6TP_N5_p0p40_half_rech FAIL fails=3/20
- BO_P7_7C_W180_skip: (stack, per week): full stops 24.5/wk $-40052; give-backs 9.1/wk (9.0 round-trips) realised $-14009, forgone vs target $35376; same-side losing runs max 12, p95 6, $-51471 lost on 3rd-and-later; no-new-evidence re-entries 37.4/wk $-167; recoveries cut 13.7/wk $46863, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $1171/wk, losers avoided $914/wk, net +241 $/wk; pnl $20025/wk. ACCEPT BO_P7_7C_W180_skip FAIL fails=3/20
- BO_P7_7C_W300_half: (stack, per week): full stops 24.5/wk $-39958; give-backs 9.1/wk (9.0 round-trips) realised $-13941, forgone vs target $35063; same-side losing runs max 12, p95 6, $-51447 lost on 3rd-and-later; no-new-evidence re-entries 37.3/wk $-505; recoveries cut 13.7/wk $46611, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $0/wk, losers avoided $69/wk, net -80 $/wk; pnl $19704/wk. ACCEPT BO_P7_7C_W300_half FAIL fails=3/20
- BO_P7_7C_W600_skip: (stack, per week): full stops 24.5/wk $-39955; give-backs 8.8/wk (8.8 round-trips) realised $-13173, forgone vs target $32992; same-side losing runs max 12, p95 6, $-52180 lost on 3rd-and-later; no-new-evidence re-entries 37.2/wk $167; recoveries cut 13.6/wk $45276, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $6877/wk, losers avoided $7646/wk, net +378 $/wk; pnl $20162/wk. ACCEPT BO_P7_7C_W600_skip FAIL fails=3/20
- BO_P7_7N_n2_T45: (stack, per week): full stops 24.5/wk $-40052; give-backs 8.8/wk (8.7 round-trips) realised $-13203, forgone vs target $33022; same-side losing runs max 12, p95 6, $-51411 lost on 3rd-and-later; no-new-evidence re-entries 37.4/wk $-106; recoveries cut 13.7/wk $46958, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $1468/wk, losers avoided $734/wk, net +1714 $/wk; pnl $21498/wk. ACCEPT BO_P7_7N_n2_T45 FAIL fails=3/20
- BO_P7_7N_n4_half: (stack, per week): full stops 24.5/wk $-40052; give-backs 9.1/wk (9.0 round-trips) realised $-14009, forgone vs target $35376; same-side losing runs max 12, p95 6, $-51344 lost on 3rd-and-later; no-new-evidence re-entries 37.3/wk $-363; recoveries cut 13.7/wk $46781, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $0/wk, losers avoided $-0/wk, net -29 $/wk; pnl $19755/wk. ACCEPT BO_P7_7N_n4_half FAIL fails=3/20
- BO_P7_7N_n4_skip: (stack, per week): full stops 24.5/wk $-40052; give-backs 9.1/wk (9.0 round-trips) realised $-14009, forgone vs target $35376; same-side losing runs max 12, p95 6, $-51393 lost on 3rd-and-later; no-new-evidence re-entries 37.3/wk $-363; recoveries cut 13.7/wk $46782, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $195/wk, losers avoided $138/wk, net -112 $/wk; pnl $19672/wk. ACCEPT BO_P7_7N_n4_skip FAIL fails=3/20
- BO_P7_8T_T40: (stack, per week): full stops 24.4/wk $-39654; give-backs 7.1/wk (7.0 round-trips) realised $-8235, forgone vs target $20217; same-side losing runs max 12, p95 6, $-49952 lost on 3rd-and-later; no-new-evidence re-entries 40.2/wk $1839; recoveries cut 14.4/wk $52175, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $9611/wk, losers avoided $6747/wk, net -1496 $/wk; pnl $18288/wk. ACCEPT BO_P7_8T_T40 PASS fails=2/20
- BO_P7_8T_T55: (stack, per week): full stops 24.5/wk $-40041; give-backs 8.1/wk (8.0 round-trips) realised $-10776, forgone vs target $26544; same-side losing runs max 12, p95 6, $-52098 lost on 3rd-and-later; no-new-evidence re-entries 38.3/wk $720; recoveries cut 13.7/wk $47113, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $4342/wk, losers avoided $2727/wk, net +1400 $/wk; pnl $21184/wk. ACCEPT BO_P7_8T_T55 FAIL fails=3/20
- BO_P7_8Tq_T40: (stack, per week): full stops 24.4/wk $-39654; give-backs 7.1/wk (7.0 round-trips) realised $-8235, forgone vs target $20217; same-side losing runs max 12, p95 6, $-49952 lost on 3rd-and-later; no-new-evidence re-entries 40.2/wk $1839; recoveries cut 14.4/wk $52175, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $9611/wk, losers avoided $6747/wk, net -1496 $/wk; pnl $18288/wk. ACCEPT BO_P7_8Tq_T40 PASS fails=2/20
- BO_P7_BL_f0_r120: (stack, per week): full stops 24.5/wk $-39877; give-backs 8.6/wk (8.5 round-trips) realised $-12586, forgone vs target $31448; same-side losing runs max 12, p95 6, $-45529 lost on 3rd-and-later; no-new-evidence re-entries 31.8/wk $2167; recoveries cut 12.9/wk $42212, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $16322/wk, losers avoided $15530/wk, net +2539 $/wk; pnl $22323/wk. ACCEPT BO_P7_BL_f0_r120 PASS fails=1/20
- BO_P7_BL_f30_r120: (stack, per week): full stops 24.5/wk $-39877; give-backs 8.7/wk (8.6 round-trips) realised $-12728, forgone vs target $31786; same-side losing runs max 10, p95 6, $-44859 lost on 3rd-and-later; no-new-evidence re-entries 31.3/wk $1667; recoveries cut 13.0/wk $43310, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $17703/wk, losers avoided $16983/wk, net +1503 $/wk; pnl $21287/wk. ACCEPT BO_P7_BL_f30_r120 PASS fails=1/20
- BO_P7_BL_f30_r60: (stack, per week): full stops 24.5/wk $-39881; give-backs 8.8/wk (8.8 round-trips) realised $-13155, forgone vs target $32897; same-side losing runs max 10, p95 6, $-48377 lost on 3rd-and-later; no-new-evidence re-entries 33.5/wk $3153; recoveries cut 13.5/wk $45598, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $12875/wk, losers avoided $12352/wk, net +2736 $/wk; pnl $22520/wk. ACCEPT BO_P7_BL_f30_r60 FAIL fails=3/20
- BO_P7_BL_f30_r90: (stack, per week): full stops 24.5/wk $-39787; give-backs 8.8/wk (8.8 round-trips) realised $-13213, forgone vs target $33018; same-side losing runs max 10, p95 6, $-46745 lost on 3rd-and-later; no-new-evidence re-entries 32.4/wk $470; recoveries cut 13.1/wk $43956, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $16679/wk, losers avoided $14532/wk, net -790 $/wk; pnl $18994/wk. ACCEPT BO_P7_BL_f30_r90 FAIL fails=3/20
- BO_P7_NZF_all: (stack, per week): full stops 24.5/wk $-39875; give-backs 12.1/wk (7.1 round-trips) realised $242, forgone vs target $30906; same-side losing runs max 12, p95 6, $-50354 lost on 3rd-and-later; no-new-evidence re-entries 38.7/wk $730; recoveries cut 14.0/wk $49706, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $6791/wk, losers avoided $4699/wk, net -1236 $/wk; pnl $18548/wk. ACCEPT BO_P7_NZF_all FAIL fails=3/20
- BO_P7_NZF_fresh: (stack, per week): full stops 24.5/wk $-40052; give-backs 9.6/wk (8.8 round-trips) realised $-12419, forgone vs target $35712; same-side losing runs max 12, p95 6, $-52208 lost on 3rd-and-later; no-new-evidence re-entries 37.9/wk $-76; recoveries cut 13.8/wk $47184, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $1367/wk, losers avoided $1091/wk, net +30 $/wk; pnl $19814/wk. ACCEPT BO_P7_NZF_fresh FAIL fails=3/20
- BO_P7_NZF_rech: (stack, per week): full stops 24.5/wk $-39875; give-backs 11.4/wk (7.3 round-trips) realised $-1971, forgone vs target $30831; same-side losing runs max 12, p95 6, $-50078 lost on 3rd-and-later; no-new-evidence re-entries 38.1/wk $429; recoveries cut 13.9/wk $49365, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $4448/wk, losers avoided $3283/wk, net -798 $/wk; pnl $18986/wk. ACCEPT BO_P7_NZF_rech FAIL fails=3/20
- BO_U7_1S_G60_k2p00_S45: (stack, per week): full stops 22.5/wk $-34469; give-backs 9.1/wk (9.0 round-trips) realised $-13547, forgone vs target $34726; same-side losing runs max 12, p95 6, $-51133 lost on 3rd-and-later; no-new-evidence re-entries 37.2/wk $-785; recoveries cut 13.6/wk $46530, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $390/wk, losers avoided $349/wk, net +320 $/wk; pnl $20104/wk. ACCEPT BO_U7_1S_G60_k2p00_S45 FAIL fails=3/20

## 5a. Plain-sentence reading of the first-order screen (screen evidence only; not an exact result)

**P7**

- Item 1 (entry context): the best on the mean was [1S_G30_k0.75_S45: RECHASE entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 0.75 ATR)]; on L6M it changes the stack mean by $82/week and the stack max drawdown by 1.4% (HOLD 1.8%, PRE mean $87/week), equal-mean drawdown cut 1.8%, full stops per week 0.4 to 1.8, recoveries lost $586/week, and in the 20 worst weeks $257/week against $-780/week in the 20 best weeks. the best equal-mean drawdown cut was [1C_m0.50_T45_S60: rechase entries get lots x0.50, target 45, stop 60 (fresh full)]; on L6M it changes the stack mean by $-3694/week and the stack max drawdown by 53.7% (HOLD 17.5%, PRE mean $212/week), equal-mean drawdown cut 43.5%, full stops per week 0.4 to 0.3, recoveries lost $38695/week, placebo p 0.36, family p 0.36, and in the 20 worst weeks $13696/week against $-17161/week in the 20 best weeks. The reverse control (the same cut on FRESH entries) has an equal-mean drawdown cut of only 3.5%. 
- Item 3 (staggered stops): the best on the mean was [3SS_f0.50_a0.75_r1_all: 0.50 of the lots go out by market at 75% of the stop (all trades; remainder rides to the full stop, state cut ignored)]; on L6M it changes the stack mean by $21/week and the stack max drawdown by -1.2% (HOLD -2.5%, PRE mean $50/week), equal-mean drawdown cut -1.1%, full stops per week 0.4 to 0.4, recoveries lost $337/week, and in the 20 worst weeks $-377/week against $-78/week in the 20 best weeks. the best equal-mean drawdown cut was [3SS_f0.50_a0.60_r0_rech: 0.50 of the lots go out by market at 60% of the stop (rech entries only; remainder keeps the state cut)]; on L6M it changes the stack mean by $-263/week and the stack max drawdown by 11.7% (HOLD 1.1%, PRE mean $-361/week), equal-mean drawdown cut 10.4%, full stops per week 0.4 to 0.4, recoveries lost $4036/week, placebo p 0.12, family p 0.12, and in the 20 worst weeks $1543/week against $-3760/week in the 20 best weeks. 
- Item 4 (probe then add): the best on the mean was [4PC_f0.50_N60_X10_all_s1: probe 0.50 of the lots, add the rest after 60 s with no adverse move beyond 10 pts (all entries)]; on L6M it changes the stack mean by $-417/week and the stack max drawdown by -1.0% (HOLD 1.1%, PRE mean $-630/week), equal-mean drawdown cut -3.2%, full stops per week 0.4 to 0.4, recoveries lost $5392/week, and in the 20 worst weeks $1329/week against $-1364/week in the 20 best weeks. the best equal-mean drawdown cut was [4PC_f0.50_N30_X10_fresh_s1: probe 0.50 of the lots, add the rest after 30 s with no adverse move beyond 10 pts (rechase never adds)]; on L6M it changes the stack mean by $-2811/week and the stack max drawdown by 31.2% (HOLD 10.9%, PRE mean $104/week), equal-mean drawdown cut 20.8%, full stops per week 0.4 to 0.4, recoveries lost $29820/week, placebo p 0.08, family p 0.09, and in the 20 worst weeks $10710/week against $-13209/week in the 20 best weeks. 
- Item 6 (time stop): the best on the mean was [6TL_N5_t0.40_flat_rech: at 5 min, if the open loss is still worse than 40% of the target: flat (rechase only)]; on L6M it changes the stack mean by $356/week and the stack max drawdown by 6.8% (HOLD 4.7%, PRE mean $171/week), equal-mean drawdown cut 8.4%, full stops per week 0.4 to 0.3, recoveries lost $1505/week, placebo p 0.08, family p 0.39, and in the 20 worst weeks $408/week against $-365/week in the 20 best weeks. the best equal-mean drawdown cut was [6TL_N40_t0.25_flat_all: at 40 min, if the open loss is still worse than 25% of the target: flat (all trades)]; on L6M it changes the stack mean by $381/week and the stack max drawdown by 11.8% (HOLD 3.9%, PRE mean $-793/week), equal-mean drawdown cut 13.5%, full stops per week 0.4 to 0.4, recoveries lost $2910/week, placebo p 0.11, family p 0.15, and in the 20 worst weeks $2142/week against $-1944/week in the 20 best weeks. 
- Item 7 (cluster filter): the best on the mean was [7C_W300_skip: another book filled a same-side target in the last 300 s: skip the signal]; on L6M it changes the stack mean by $996/week and the stack max drawdown by -1.5% (HOLD 0.0%, PRE mean $295/week), equal-mean drawdown cut 4.0%, full stops per week 0.4 to 0.4, recoveries lost $1128/week, and in the 20 worst weeks $73/week against $789/week in the 20 best weeks. the best equal-mean drawdown cut was [7C_W600_skip: another book filled a same-side target in the last 600 s: skip the signal]; on L6M it changes the stack mean by $-282/week and the stack max drawdown by 13.6% (HOLD 4.3%, PRE mean $258/week), equal-mean drawdown cut 12.3%, full stops per week 0.4 to 0.4, recoveries lost $5356/week, placebo p 0.09, family p 0.37, and in the 20 worst weeks $973/week against $-1285/week in the 20 best weeks. 
- Item 8 (single target 30-59): the best on the mean was [8T_T55: single target 55 pts, stop 60]; on L6M it changes the stack mean by $548/week and the stack max drawdown by 27.0% (HOLD -3.3%, PRE mean $322/week), equal-mean drawdown cut 29.0%, full stops per week 0.4 to 0.4, recoveries lost $5166/week, placebo p 0.30, family p 0.62, and in the 20 worst weeks $3222/week against $-1702/week in the 20 best weeks. the best equal-mean drawdown cut was [8T_T40: single target 40 pts, stop 60]; on L6M it changes the stack mean by $-1826/week and the stack max drawdown by 44.3% (HOLD 0.0%, PRE mean $-1239/week), equal-mean drawdown cut 38.4%, full stops per week 0.4 to 0.2, recoveries lost $25498/week, placebo p 0.12, family p 0.29, and in the 20 worst weeks $9478/week against $-13722/week in the 20 best weeks. 

**K7 at live lots**

- Item 1 (entry context): the best on the mean was [1S_G30_k2.00_S45: RECHASE entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 2.00 ATR)]; on L6M it changes the stack mean by $370/week and the stack max drawdown by -5.9% (HOLD -3.7%, PRE mean $-262/week), equal-mean drawdown cut -3.9%, full stops per week 12.6 to 19.3, recoveries lost $2600/week, and in the 20 worst weeks $1184/week against $-1229/week in the 20 best weeks. the best equal-mean drawdown cut was [1T_G60_k1.50_T30: RECHASE entries get target 30 pts (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 1.50 ATR)]; on L6M it changes the stack mean by $-163/week and the stack max drawdown by 13.1% (HOLD -2.7%, PRE mean $-1032/week), equal-mean drawdown cut 12.3%, full stops per week 12.6 to 9.3, recoveries lost $17884/week, placebo p 0.49, family p 0.56, and in the 20 worst weeks $2309/week against $-4965/week in the 20 best weeks. The reverse control (the same cut on FRESH entries) has an equal-mean drawdown cut of only 3.5%. 
- Item 3 (staggered stops): the best on the mean was [3SS_f0.50_a0.75_r0_rech: 0.50 of the lots go out by market at 75% of the stop (rech entries only; remainder keeps the state cut)]; on L6M it changes the stack mean by $-23/week and the stack max drawdown by -3.6% (HOLD -1.4%, PRE mean $-26/week), equal-mean drawdown cut -3.7%, full stops per week 12.6 to 12.6, recoveries lost $631/week, and in the 20 worst weeks $465/week against $-526/week in the 20 best weeks. the best equal-mean drawdown cut was [3SS_f0.33_a0.40_r0_fresh: 0.33 of the lots go out by market at 40% of the stop (fresh entries only; remainder keeps the state cut)]; on L6M it changes the stack mean by $76/week and the stack max drawdown by 0.2% (HOLD 1.3%, PRE mean $88/week), equal-mean drawdown cut 0.6%, full stops per week 12.6 to 12.6, recoveries lost $200/week, and in the 20 worst weeks $207/week against $-14/week in the 20 best weeks. 
- Item 4 (probe then add): the best on the mean was [4PC_f0.50_N30_X10_all_s1: probe 0.50 of the lots, add the rest after 30 s with no adverse move beyond 10 pts (all entries)]; on L6M it changes the stack mean by $-268/week and the stack max drawdown by 3.1% (HOLD -0.5%, PRE mean $-117/week), equal-mean drawdown cut 1.5%, full stops per week 12.6 to 12.6, recoveries lost $989/week, and in the 20 worst weeks $20/week against $-472/week in the 20 best weeks. the best equal-mean drawdown cut was [4PC_f0.33_N30_X10_fresh_s0: probe 0.33 of the lots, add the rest after 30 s with no adverse move beyond 10 pts (rechase never adds)]; on L6M it changes the stack mean by $-174/week and the stack max drawdown by 7.1% (HOLD -5.4%, PRE mean $-293/week), equal-mean drawdown cut 6.1%, full stops per week 12.6 to 12.6, recoveries lost $5142/week, and in the 20 worst weeks $1229/week against $-2594/week in the 20 best weeks. 
- Item 6 (time stop): the best on the mean was [6TL_N5_t0.40_half_rech: at 5 min, if the open loss is still worse than 40% of the target: half the lots out (rechase only)]; on L6M it changes the stack mean by $108/week and the stack max drawdown by 1.9% (HOLD 3.8%, PRE mean $18/week), equal-mean drawdown cut 2.5%, full stops per week 12.6 to 11.5, recoveries lost $786/week, and in the 20 worst weeks $207/week against $-557/week in the 20 best weeks. the best equal-mean drawdown cut was [6TL_N10_t0.25_flat_rech: at 10 min, if the open loss is still worse than 25% of the target: flat (rechase only)]; on L6M it changes the stack mean by $430/week and the stack max drawdown by 9.8% (HOLD -4.6%, PRE mean $-150/week), equal-mean drawdown cut 11.8%, full stops per week 12.6 to 9.2, recoveries lost $3210/week, placebo p 0.01, family p 0.03, and in the 20 worst weeks $259/week against $-1332/week in the 20 best weeks. 
- Item 7 (cluster filter): the best on the mean was [7C_W300_skip: another book filled a same-side target in the last 300 s: skip the signal]; on L6M it changes the stack mean by $476/week and the stack max drawdown by 2.7% (HOLD 3.8%, PRE mean $54/week), equal-mean drawdown cut 5.1%, full stops per week 12.6 to 11.6, recoveries lost $2056/week, placebo p 0.05, family p 0.50, and in the 20 worst weeks $209/week against $350/week in the 20 best weeks. the best equal-mean drawdown cut was [7C_W600_T30: another book filled a same-side target in the last 600 s: target 30]; on L6M it changes the stack mean by $326/week and the stack max drawdown by 3.6% (HOLD -0.1%, PRE mean $124/week), equal-mean drawdown cut 5.5%, full stops per week 12.6 to 12.3, recoveries lost $1393/week, placebo p 0.36, family p 0.44, and in the 20 worst weeks $584/week against $183/week in the 20 best weeks. 
- Item 8 (single target 30-59): the best on the mean was [8T_T55: single target 55 pts, stop 60]; on L6M it changes the stack mean by $-156/week and the stack max drawdown by -1.1% (HOLD 1.0%, PRE mean $-444/week), equal-mean drawdown cut -2.1%, full stops per week 12.6 to 12.3, recoveries lost $2398/week, and in the 20 worst weeks $-122/week against $-577/week in the 20 best weeks. the best equal-mean drawdown cut was [8Tq_T35: single target 35 pts, stop 60 (queue-conservative: fills only on trade-through by 1 tick)]; on L6M it changes the stack mean by $-1038/week and the stack max drawdown by 23.0% (HOLD -0.3%, PRE mean $-1505/week), equal-mean drawdown cut 18.6%, full stops per week 12.6 to 9.9, recoveries lost $16298/week, placebo p 0.05, family p 0.12, and in the 20 worst weeks $1812/week against $-5170/week in the 20 best weeks. 

**K7 at 3x lots (hypothetical; live K7 is 1-2 lots so partial structures are inert there)**

- Item 1 (entry context): the best on the mean was [1S_G30_k2.00_S45: RECHASE entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 2.00 ATR)]; on L6M it changes the stack mean by $1109/week and the stack max drawdown by -7.5% (HOLD 7.9%, PRE mean $-787/week), equal-mean drawdown cut -3.2%, full stops per week 12.6 to 19.3, recoveries lost $7800/week, and in the 20 worst weeks $3553/week against $-3688/week in the 20 best weeks. the best equal-mean drawdown cut was [1T_G60_k1.50_T30: RECHASE entries get target 30 pts (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 1.50 ATR)]; on L6M it changes the stack mean by $-488/week and the stack max drawdown by 47.0% (HOLD -5.1%, PRE mean $-3097/week), equal-mean drawdown cut 45.9%, full stops per week 12.6 to 9.3, recoveries lost $53653/week, placebo p 0.39, family p 0.41, and in the 20 worst weeks $6928/week against $-14894/week in the 20 best weeks. The reverse control (the same cut on FRESH entries) has an equal-mean drawdown cut of only 7.6%. 
- Item 3 (staggered stops): the best on the mean was [3SS_f0.50_a0.75_r1_fresh: 0.50 of the lots go out by market at 75% of the stop (fresh entries only; remainder rides to the full stop, state cut ignored)]; on L6M it changes the stack mean by $-7/week and the stack max drawdown by 5.9% (HOLD 5.5%, PRE mean $121/week), equal-mean drawdown cut 5.9%, full stops per week 12.6 to 12.2, recoveries lost $1013/week, and in the 20 worst weeks $592/week against $20/week in the 20 best weeks. the best equal-mean drawdown cut was [3SS_f0.33_a0.60_r1_fresh: 0.33 of the lots go out by market at 60% of the stop (fresh entries only; remainder rides to the full stop, state cut ignored)]; on L6M it changes the stack mean by $-186/week and the stack max drawdown by 17.6% (HOLD 5.5%, PRE mean $-252/week), equal-mean drawdown cut 17.0%, full stops per week 12.6 to 12.2, recoveries lost $928/week, placebo p 0.01, family p 0.02, and in the 20 worst weeks $1481/week against $-910/week in the 20 best weeks. 
- Item 4 (probe then add): the best on the mean was [4PC_f0.50_N120_X10_all_s0: probe 0.50 of the lots, add the rest after 120 s with no adverse move beyond 10 pts (all entries)]; on L6M it changes the stack mean by $-843/week and the stack max drawdown by 7.8% (HOLD 6.8%, PRE mean $-805/week), equal-mean drawdown cut 4.2%, full stops per week 12.6 to 12.8, recoveries lost $18192/week, and in the 20 worst weeks $2203/week against $-5419/week in the 20 best weeks. the best equal-mean drawdown cut was [4PC_f0.33_N300_X5_all_s0: probe 0.33 of the lots, add the rest after 300 s with no adverse move beyond 5 pts (all entries)]; on L6M it changes the stack mean by $-3410/week and the stack max drawdown by 35.2% (HOLD 18.8%, PRE mean $-2891/week), equal-mean drawdown cut 23.9%, full stops per week 12.6 to 13.2, recoveries lost $62081/week, placebo p 1.00, family p 1.00, and in the 20 worst weeks $6238/week against $-17749/week in the 20 best weeks. 
- Item 6 (time stop): the best on the mean was [6TL_N10_t0.40_half_rech: at 10 min, if the open loss is still worse than 40% of the target: half the lots out (rechase only)]; on L6M it changes the stack mean by $94/week and the stack max drawdown by 2.2% (HOLD 3.7%, PRE mean $265/week), equal-mean drawdown cut 2.6%, full stops per week 12.6 to 12.6, recoveries lost $1650/week, and in the 20 worst weeks $337/week against $-414/week in the 20 best weeks. the best equal-mean drawdown cut was [6TL_N10_t0.25_flat_rech: at 10 min, if the open loss is still worse than 25% of the target: flat (rechase only)]; on L6M it changes the stack mean by $1291/week and the stack max drawdown by 31.9% (HOLD -3.5%, PRE mean $-449/week), equal-mean drawdown cut 35.2%, full stops per week 12.6 to 9.2, recoveries lost $9629/week, placebo p 0.01, family p 0.03, and in the 20 worst weeks $777/week against $-3996/week in the 20 best weeks. 
- Item 7 (cluster filter): the best on the mean was [7C_W300_skip: another book filled a same-side target in the last 300 s: skip the signal]; on L6M it changes the stack mean by $1427/week and the stack max drawdown by 15.8% (HOLD 0.7%, PRE mean $162/week), equal-mean drawdown cut 20.0%, full stops per week 12.6 to 11.6, recoveries lost $6167/week, placebo p 0.01, family p 0.57, and in the 20 worst weeks $628/week against $1050/week in the 20 best weeks. the best equal-mean drawdown cut was [7C_W600_T30: another book filled a same-side target in the last 600 s: target 30]; on L6M it changes the stack mean by $978/week and the stack max drawdown by 17.8% (HOLD -5.6%, PRE mean $371/week), equal-mean drawdown cut 21.2%, full stops per week 12.6 to 12.3, recoveries lost $4178/week, placebo p 0.48, family p 0.48, and in the 20 worst weeks $1753/week against $550/week in the 20 best weeks. 
- Item 8 (single target 30-59): the best on the mean was [8T_T55: single target 55 pts, stop 60]; on L6M it changes the stack mean by $-467/week and the stack max drawdown by -7.1% (HOLD -11.8%, PRE mean $-1331/week), equal-mean drawdown cut -9.3%, full stops per week 12.6 to 12.3, recoveries lost $7194/week, and in the 20 worst weeks $-365/week against $-1730/week in the 20 best weeks. the best equal-mean drawdown cut was [8Tq_T35: single target 35 pts, stop 60 (queue-conservative: fills only on trade-through by 1 tick)]; on L6M it changes the stack mean by $-3115/week and the stack max drawdown by 55.5% (HOLD -12.2%, PRE mean $-4515/week), equal-mean drawdown cut 49.6%, full stops per week 12.6 to 9.9, recoveries lost $48895/week, placebo p 0.02, family p 0.04, and in the 20 worst weeks $5435/week against $-15511/week in the 20 best weeks. 

**U7**

- Item 1 (entry context): the best on the mean was [1S_G60_k2.00_S45: RECHASE entries get stop 45 pts (fresh = 1st-2nd trade of the book in the session, at least 60 min since its last exit, session move at most 2.00 ATR)]; on L6M it changes the stack mean by $515/week and the stack max drawdown by 8.6% (HOLD -8.7%, PRE mean $203/week), equal-mean drawdown cut 11.0%, full stops per week 3.3 to 4.1, recoveries lost $920/week, placebo p 0.08, family p 0.39, and in the 20 worst weeks $1461/week against $-561/week in the 20 best weeks. the best equal-mean drawdown cut was [1T_G30_k2.00_T30: RECHASE entries get target 30 pts (fresh = 1st-2nd trade of the book in the session, at least 30 min since its last exit, session move at most 2.00 ATR)]; on L6M it changes the stack mean by $-131/week and the stack max drawdown by 24.4% (HOLD -8.1%, PRE mean $-597/week), equal-mean drawdown cut 23.9%, full stops per week 3.3 to 2.8, recoveries lost $5402/week, placebo p 0.02, family p 0.03, and in the 20 worst weeks $2691/week against $-3059/week in the 20 best weeks. The reverse control (the same cut on FRESH entries) has an equal-mean drawdown cut of only -5.6%. 
- Item 3 (staggered stops): the best on the mean was [3SS_f0.33_a0.75_r0_rech: 0.33 of the lots go out by market at 75% of the stop (rech entries only; remainder keeps the state cut)]; on L6M it changes the stack mean by $57/week and the stack max drawdown by 1.4% (HOLD -4.2%, PRE mean $-4/week), equal-mean drawdown cut 1.7%, full stops per week 3.3 to 3.3, recoveries lost $502/week, placebo p 0.51, family p 0.59, and in the 20 worst weeks $403/week against $-241/week in the 20 best weeks. the best equal-mean drawdown cut was [3SS_f0.33_a0.40_r0_rech: 0.33 of the lots go out by market at 40% of the stop (rech entries only; remainder keeps the state cut)]; on L6M it changes the stack mean by $-501/week and the stack max drawdown by 9.7% (HOLD -1.4%, PRE mean $-56/week), equal-mean drawdown cut 7.6%, full stops per week 3.3 to 3.3, recoveries lost $1984/week, placebo p 0.08, family p 0.09, and in the 20 worst weeks $1011/week against $-1194/week in the 20 best weeks. 
- Item 4 (probe then add): the best on the mean was [4PC_f0.50_N30_X10_all_s1: probe 0.50 of the lots, add the rest after 30 s with no adverse move beyond 10 pts (all entries)]; on L6M it changes the stack mean by $-140/week and the stack max drawdown by 0.9% (HOLD 1.5%, PRE mean $-179/week), equal-mean drawdown cut 0.2%, full stops per week 3.3 to 3.3, recoveries lost $999/week, and in the 20 worst weeks $210/week against $-11/week in the 20 best weeks. the best equal-mean drawdown cut was [4PA_f0.50_p0.25_fresh_s0: probe 0.50 of the lots, add the rest when the trade is 25% of the target in profit (rechase never adds; stop re-anchored at the average price)]; on L6M it changes the stack mean by $-625/week and the stack max drawdown by 11.1% (HOLD -5.6%, PRE mean $-760/week), equal-mean drawdown cut 7.6%, full stops per week 3.3 to 3.4, recoveries lost $6953/week, placebo p 0.01, family p 0.01, and in the 20 worst weeks $1637/week against $-3228/week in the 20 best weeks. 
- Item 6 (time stop): the best on the mean was [6TL_N20_t0.40_flat_all: at 20 min, if the open loss is still worse than 40% of the target: flat (all trades)]; on L6M it changes the stack mean by $449/week and the stack max drawdown by 2.4% (HOLD -10.4%, PRE mean $270/week), equal-mean drawdown cut 4.9%, full stops per week 3.3 to 2.4, recoveries lost $986/week, placebo p 0.44, family p 0.78, and in the 20 worst weeks $590/week against $35/week in the 20 best weeks. the best equal-mean drawdown cut was [6TP_N20_p0.25_flat_rech: at 20 min, if the open profit is below 25% of the target: flat (rechase only)]; on L6M it changes the stack mean by $-3740/week and the stack max drawdown by 34.6% (HOLD -15.4%, PRE mean $-1840/week), equal-mean drawdown cut 20.6%, full stops per week 3.3 to 1.7, recoveries lost $7320/week, placebo p 0.01, family p 0.01, and in the 20 worst weeks $2639/week against $-6458/week in the 20 best weeks. 
- Item 7 (cluster filter): the best on the mean was [7C_W180_skip: another book filled a same-side target in the last 180 s: skip the signal]; on L6M it changes the stack mean by $466/week and the stack max drawdown by 6.2% (HOLD -5.6%, PRE mean $230/week), equal-mean drawdown cut 8.4%, full stops per week 3.3 to 2.9, recoveries lost $1543/week, placebo p 0.01, family p 1.00, and in the 20 worst weeks $735/week against $-304/week in the 20 best weeks. the best equal-mean drawdown cut was [7C_W600_skip: another book filled a same-side target in the last 600 s: skip the signal]; on L6M it changes the stack mean by $2763/week and the stack max drawdown by 32.0% (HOLD -6.3%, PRE mean $-87/week), equal-mean drawdown cut 40.6%, full stops per week 3.3 to 2.0, recoveries lost $4268/week, placebo p 0.01, family p 0.01, and in the 20 worst weeks $2068/week against $-314/week in the 20 best weeks. 
- Item 8 (single target 30-59): the best on the mean was [8T_T55: single target 55 pts, stop 60]; on L6M it changes the stack mean by $-516/week and the stack max drawdown by -5.6% (HOLD -3.4%, PRE mean $-513/week), equal-mean drawdown cut -8.4%, full stops per week 3.3 to 3.2, recoveries lost $1270/week, and in the 20 worst weeks $556/week against $-802/week in the 20 best weeks. the best equal-mean drawdown cut was [8Tq_T40: single target 40 pts, stop 60 (queue-conservative: fills only on trade-through by 1 tick)]; on L6M it changes the stack mean by $-870/week and the stack max drawdown by 16.1% (HOLD -9.5%, PRE mean $-424/week), equal-mean drawdown cut 12.5%, full stops per week 3.3 to 2.7, recoveries lost $6022/week, placebo p 0.23, family p 0.30, and in the 20 worst weeks $4098/week against $-2839/week in the 20 best weeks. 

**M7**

- Item 1 (entry context): the best on the mean was [1L_G15_k2.00_m0.50: RECHASE entries get lots x0.50 (fresh = 1st-2nd trade of the book in the session, at least 15 min since its last exit, session move at most 2.00 ATR)]; on L6M it changes the stack mean by $176/week and the stack max drawdown by 9.1% (HOLD 9.1%, PRE mean $139/week), equal-mean drawdown cut 10.0%, full stops per week 1.9 to 1.9, recoveries lost $2068/week, placebo p 0.49, family p 0.97, and in the 20 worst weeks $1761/week against $-699/week in the 20 best weeks. the best equal-mean drawdown cut was [1C_m0.50_T30_S60: rechase entries get lots x0.50, target 30, stop 60 (fresh full)]; on L6M it changes the stack mean by $89/week and the stack max drawdown by 19.2% (HOLD 14.5%, PRE mean $-31/week), equal-mean drawdown cut 19.5%, full stops per week 1.9 to 1.3, recoveries lost $9736/week, placebo p 0.02, family p 0.02, and in the 20 worst weeks $3368/week against $-2813/week in the 20 best weeks. The reverse control (the same cut on FRESH entries) has an equal-mean drawdown cut of only 3.2%. 
- Item 3 (staggered stops): the best on the mean was [3SS_f0.33_a0.60_r0_fresh: 0.33 of the lots go out by market at 60% of the stop (fresh entries only; remainder keeps the state cut)]; on L6M it changes the stack mean by $11/week and the stack max drawdown by -0.0% (HOLD -0.1%, PRE mean $17/week), equal-mean drawdown cut 0.0%, full stops per week 1.9 to 1.9, recoveries lost $76/week, and in the 20 worst weeks $47/week against $52/week in the 20 best weeks. the best equal-mean drawdown cut was [3SS_f0.33_a0.40_r0_all: 0.33 of the lots go out by market at 40% of the stop (all trades; remainder keeps the state cut)]; on L6M it changes the stack mean by $-74/week and the stack max drawdown by 2.7% (HOLD 4.5%, PRE mean $-154/week), equal-mean drawdown cut 2.3%, full stops per week 1.9 to 1.9, recoveries lost $1210/week, placebo p 0.02, family p 0.02, and in the 20 worst weeks $694/week against $-513/week in the 20 best weeks. 
- Item 4 (probe then add): the best on the mean was [4PC_f0.33_N30_X5_fresh_s0: probe 0.33 of the lots, add the rest after 30 s with no adverse move beyond 5 pts (rechase never adds)]; on L6M it changes the stack mean by $430/week and the stack max drawdown by 12.2% (HOLD 10.0%, PRE mean $91/week), equal-mean drawdown cut 14.2%, full stops per week 1.9 to 1.9, recoveries lost $2239/week, and in the 20 worst weeks $1757/week against $-803/week in the 20 best weeks. the best equal-mean drawdown cut was [4PC_f0.33_N60_X5_fresh_s0: probe 0.33 of the lots, add the rest after 60 s with no adverse move beyond 5 pts (rechase never adds)]; on L6M it changes the stack mean by $533/week and the stack max drawdown by 14.1% (HOLD 10.8%, PRE mean $62/week), equal-mean drawdown cut 16.5%, full stops per week 1.9 to 1.9, recoveries lost $2277/week, and in the 20 worst weeks $1788/week against $-760/week in the 20 best weeks. 
- Item 6 (time stop): the best on the mean was [6TL_N40_t0.40_half_all: at 40 min, if the open loss is still worse than 40% of the target: half the lots out (all trades)]; on L6M it changes the stack mean by $98/week and the stack max drawdown by 0.8% (HOLD 0.1%, PRE mean $72/week), equal-mean drawdown cut 1.3%, full stops per week 1.9 to 1.7, recoveries lost $144/week, placebo p 0.19, family p 0.98, and in the 20 worst weeks $381/week against $63/week in the 20 best weeks. the best equal-mean drawdown cut was [6TP_N5_p0.10_flat_all: at 5 min, if the open profit is below 10% of the target: flat (all trades)]; on L6M it changes the stack mean by $1155/week and the stack max drawdown by 21.8% (HOLD 17.6%, PRE mean $-1188/week), equal-mean drawdown cut 26.4%, full stops per week 1.9 to 0.8, recoveries lost $8387/week, placebo p 0.01, family p 0.01, and in the 20 worst weeks $3399/week against $-3169/week in the 20 best weeks. 
- Item 7 (cluster filter): the best on the mean was [7C_W180_skip: another book filled a same-side target in the last 180 s: skip the signal]; on L6M it changes the stack mean by $240/week and the stack max drawdown by 3.1% (HOLD -0.5%, PRE mean $109/week), equal-mean drawdown cut 4.2%, full stops per week 1.9 to 1.9, recoveries lost $611/week, placebo p 0.07, family p 0.27, and in the 20 worst weeks $227/week against $248/week in the 20 best weeks. the best equal-mean drawdown cut was [7C_W600_skip: another book filled a same-side target in the last 600 s: skip the signal]; on L6M it changes the stack mean by $895/week and the stack max drawdown by 8.8% (HOLD -1.8%, PRE mean $-40/week), equal-mean drawdown cut 13.3%, full stops per week 1.9 to 1.8, recoveries lost $1269/week, placebo p 0.01, family p 0.01, and in the 20 worst weeks $577/week against $253/week in the 20 best weeks. 
- Item 8 (single target 30-59): the best on the mean was [8T_T55: single target 55 pts, stop 60]; on L6M it changes the stack mean by $621/week and the stack max drawdown by 7.4% (HOLD 2.5%, PRE mean $-175/week), equal-mean drawdown cut 10.8%, full stops per week 1.9 to 1.8, recoveries lost $1133/week, placebo p 0.22, family p 0.52, and in the 20 worst weeks $324/week against $-128/week in the 20 best weeks. 


## 5. First-order screen (full 1-s entry-to-resolution paths, 20,807 LPB_BASE trades, base scope)


### P7 (first-order screen, 418 cells)

Each family: the cell with the best minimum of the L6M, HOLD and PRE mean change, and the cell with the best equal-mean drawdown cut. Money is $/week of the whole stack against the live stack (same kernel, no rule). dd = stack max drawdown change in percent, positive = better. fs = full stops per week (live to new). rec = recoveries lost $/wk. w20 / best20 = $/wk change in the 20 worst / 20 best stack weeks. frozen wk = $ change of the frozen live week 11-01..05 (the stack as traded was +$85.7k for P7 alone; a negative number means the rule would have cost trend-week winners). WF dd cut = purged walk-forward (monthly re-pick of the lowest-26-week-drawdown cell of the family, 7-day embargo) stack drawdown cut against no rule, positive = better. p = placebo p on the equal-mean drawdown cut (forward-only shifted labels / random level) and family-null p.

| family | cell | L6M $/wk | HOLD $/wk | PRE $/wk | L6M dd% | HOLD dd% | fs/wk | rec $/wk | w20 $/wk | best20 $/wk | frozen wk $ | WF dd cut % (family) | p_plc | p_fam |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1_combo | 1C_m0.50_T45_S60 (best key) | -3694 | -3280 | 212 | 53.7 | 17.5 | 0.4>0.3 | 38695 | 13696 | -17161 | -36440 | 32.7 | 0.36 | 0.36 |
| 1_combo | 1C_m0.50_T45_S60 (best equal-mean dd) | -3694 | -3280 | 212 | 53.7 | 17.5 | 0.4>0.3 | 38695 | 13696 | -17161 | -36440 | 32.7 | 0.36 | 0.36 |
| 1_lots | 1L_G30_k1.00_m0.50 (best key) | -2777 | -2709 | 241 | 31.9 | 9.9 | 0.4>0.4 | 29596 | 10719 | -13163 | -31463 | 32.8 | - | - |
| 1_lots | 1L_G15_k1.00_m0.50 (best equal-mean dd) | -2833 | -2576 | 103 | 32.6 | 9.9 | 0.4>0.4 | 29173 | 10499 | -12376 | -31463 | 32.8 | 0.12 | 0.94 |
| 1_lots_rev | 1Lrev_G60_k0.75_m0.50 (best key) | -530 | -134 | -337 | 1.1 | 0.1 | 0.4>0.4 | 3009 | -373 | -2202 | 2662 | -18.1 | - | - |
| 1_lots_rev | 1Lrev_G60_k1.50_m0.33 (best equal-mean dd) | -449 | 277 | -1800 | 5.9 | 7.8 | 0.4>0.4 | 5453 | 85 | -4161 | 6070 | -18.1 | 0.40 | 1.00 |
| 1_stop | 1S_G15_k0.75_S45 (best key) | 82 | 128 | 87 | 1.4 | 1.8 | 0.4>1.8 | 586 | 257 | -778 | -7924 | 2.9 | 0.02 | 1.00 |
| 1_stop | 1S_G15_k0.75_S45 (best equal-mean dd) | 82 | 128 | 87 | 1.4 | 1.8 | 0.4>1.8 | 586 | 257 | -778 | -7924 | 2.9 | 0.02 | 1.00 |
| 1_stop_rev | 1Srev_G30_k2.00_S45 (best key) | 32 | 32 | -12 | -0.3 | 0.0 | 0.4>0.7 | -0 | -31 | 10 | 199 | -1.1 | - | - |
| 1_stop_rev | 1Srev_G60_k1.50_S45 (best equal-mean dd) | -14 | 6 | -15 | 0.0 | 0.0 | 0.4>0.5 | -0 | -23 | 10 | 0 | -1.1 | 0.76 | 1.00 |
| 1_tgt | 1T_G30_k2.00_T45 (best key) | -1062 | -1047 | -67 | 38.5 | 11.6 | 0.4>0.3 | 15512 | 4573 | -6072 | -21266 | 4.1 | 0.05 | 0.63 |
| 1_tgt | 1T_G30_k2.00_T45 (best equal-mean dd) | -1062 | -1047 | -67 | 38.5 | 11.6 | 0.4>0.3 | 15512 | 4573 | -6072 | -21266 | 4.1 | 0.05 | 0.63 |
| 1_tgt_rev | 1Trev_G60_k1.00_T45 (best key) | -694 | -427 | -319 | 9.1 | -3.4 | 0.4>0.4 | 1901 | 1959 | -2596 | 6010 | -7.9 | - | - |
| 1_tgt_rev | 1Trev_G15_k2.00_T45 (best equal-mean dd) | -1589 | -795 | -681 | 17.8 | -4.7 | 0.4>0.4 | 3789 | 3405 | -2646 | 11672 | -7.9 | 0.61 | 1.00 |
| 3_stagstop | 3SS_f0.50_a0.75_r1_all (best key) | 21 | 151 | 50 | -1.2 | -2.5 | 0.4>0.4 | 337 | -377 | -78 | -4537 | -7.0 | - | - |
| 3_stagstop | 3SS_f0.50_a0.60_r0_rech (best equal-mean dd) | -263 | -541 | -361 | 11.7 | 1.1 | 0.4>0.4 | 4036 | 1543 | -3760 | -9978 | -7.0 | 0.12 | 0.12 |
| 4_probe | 4PA_f0.50_p0.10_all_s0 (best key) | -2057 | -2080 | -1244 | -4.9 | -2.8 | 0.4>0.4 | 4398 | -460 | -2424 | -15598 | 34.2 | - | - |
| 4_probe | 4PA_f0.50_p0.10_fresh_s1 (best equal-mean dd) | -3195 | -2865 | -185 | 32.5 | 11.0 | 0.4>0.4 | 30172 | 10165 | -13232 | -33020 | 34.2 | 0.06 | 0.10 |
| 4_probe_calm | 4PC_f0.50_N60_X10_all_s1 (best key) | -417 | 14 | -630 | -1.0 | 1.1 | 0.4>0.4 | 5392 | 1329 | -1364 | -14955 | 15.9 | - | - |
| 4_probe_calm | 4PC_f0.50_N30_X10_fresh_s1 (best equal-mean dd) | -2811 | -2756 | 104 | 31.2 | 10.9 | 0.4>0.4 | 29820 | 10710 | -13209 | -32261 | 15.9 | 0.08 | 0.09 |
| 6_tstop | 6TP_N40_p0.10_half_rech (best key) | -486 | -1420 | -553 | -3.5 | -1.3 | 0.4>0.4 | 6129 | 3121 | -3669 | -4150 | -9.2 | - | - |
| 6_tstop | 6TP_N5_p0.40_half_rech (best equal-mean dd) | -2709 | -5397 | -1536 | 27.8 | 0.7 | 0.4>0.3 | 26903 | 8482 | -15088 | -27635 | -9.2 | 0.04 | 0.16 |
| 6_tstop_loss | 6TL_N5_t0.40_flat_rech (best key) | 356 | 594 | 171 | 6.8 | 4.7 | 0.4>0.3 | 1505 | 408 | -365 | -14052 | 14.6 | 0.08 | 0.39 |
| 6_tstop_loss | 6TL_N40_t0.25_flat_all (best equal-mean dd) | 381 | -165 | -793 | 11.8 | 3.9 | 0.4>0.4 | 2910 | 2142 | -1944 | 0 | 14.6 | 0.11 | 0.15 |
| 7_cluster | 7C_W300_skip (best key) | 996 | 487 | 295 | -1.5 | 0.0 | 0.4>0.4 | 1128 | 73 | 789 | -2390 | 4.1 | - | - |
| 7_cluster | 7C_W600_skip (best equal-mean dd) | -282 | -435 | 258 | 13.6 | 4.3 | 0.4>0.4 | 5356 | 973 | -1285 | 13205 | 4.1 | 0.09 | 0.37 |
| 7_cluster_n | 7N_n2_half (best key) | 500 | 434 | 112 | -0.6 | 1.5 | 0.4>0.4 | 3195 | 1051 | -915 | 897 | -1.5 | - | - |
| 7_cluster_n | 7N_n2_T45 (best equal-mean dd) | 1214 | 919 | -328 | -3.9 | -1.8 | 0.4>0.4 | 1791 | 485 | 937 | -2689 | -1.5 | 0.50 | 0.84 |
| 8_rung | 8R_T40_f0.33_flNone (best key) | -720 | -583 | -247 | 25.0 | 1.5 | 0.4>0.4 | 7425 | 2915 | -3963 | -3982 | - | - | - |
| 8_rung | 8R_T40_f0.50_fl2.0 (best equal-mean dd) | -881 | -1382 | -411 | 37.3 | 0.5 | 0.4>0.3 | 18199 | 6905 | -10244 | -15902 | - | - | - |
| 8_rung_q | 8Rq_T40_f0.33_flNone (best key) | -75 | -267 | -353 | 25.0 | 1.5 | 0.4>0.4 | 7424 | 2763 | -3962 | -3982 | - | - | - |
| 8_rung_q | 8Rq_T40_f0.50_fl2.0 (best equal-mean dd) | -895 | -1389 | -629 | 37.3 | 0.5 | 0.4>0.3 | 18013 | 6491 | -10126 | -15902 | - | - | - |
| 8_target | 8T_T55 (best key) | 548 | 154 | 322 | 27.0 | -3.3 | 0.4>0.4 | 5166 | 3222 | -1702 | -11512 | 11.8 | 0.30 | 0.62 |
| 8_target | 8T_T40 (best equal-mean dd) | -1826 | -1809 | -1239 | 44.3 | 0.0 | 0.4>0.2 | 25498 | 9478 | -13722 | -12429 | 11.8 | 0.12 | 0.29 |
| 8_target_q | 8Tq_T55 (best key) | 44 | -57 | 312 | 27.4 | -3.3 | 0.4>0.4 | 5059 | 3129 | -2377 | -11512 | 11.8 | - | - |
| 8_target_q | 8Tq_T40 (best equal-mean dd) | -2181 | -1982 | -1579 | 44.3 | 0.0 | 0.4>0.2 | 25467 | 8947 | -13702 | -12429 | 11.8 | 0.11 | 0.34 |

### K7 (first-order screen, 418 cells)

Each family: the cell with the best minimum of the L6M, HOLD and PRE mean change, and the cell with the best equal-mean drawdown cut. Money is $/week of the whole stack against the live stack (same kernel, no rule). dd = stack max drawdown change in percent, positive = better. fs = full stops per week (live to new). rec = recoveries lost $/wk. w20 / best20 = $/wk change in the 20 worst / 20 best stack weeks. frozen wk = $ change of the frozen live week 11-01..05 (the stack as traded was +$85.7k for P7 alone; a negative number means the rule would have cost trend-week winners). WF dd cut = purged walk-forward (monthly re-pick of the lowest-26-week-drawdown cell of the family, 7-day embargo) stack drawdown cut against no rule, positive = better. p = placebo p on the equal-mean drawdown cut (forward-only shifted labels / random level) and family-null p.

| family | cell | L6M $/wk | HOLD $/wk | PRE $/wk | L6M dd% | HOLD dd% | fs/wk | rec $/wk | w20 $/wk | best20 $/wk | frozen wk $ | WF dd cut % (family) | p_plc | p_fam |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1_combo | 1C_m0.50_T45_S60 (best key) | -1046 | -1300 | -1108 | 8.9 | -5.9 | 12.6>11.3 | 12531 | 2432 | -4309 | 2579 | -3.7 | - | - |
| 1_combo | 1C_m0.50_T30_S60 (best equal-mean dd) | -950 | -1805 | -1392 | 8.8 | -7.4 | 12.6>9.3 | 20328 | 3092 | -6404 | 1596 | -3.7 | 0.68 | 1.00 |
| 1_lots | 1L_G15_k2.00_m0.50 (best key) | -137 | -332 | -254 | 1.8 | -5.2 | 12.6>12.6 | 4537 | 924 | -2476 | -64 | 9.8 | - | - |
| 1_lots | 1L_G30_k1.00_m0.50 (best equal-mean dd) | -282 | -420 | -298 | 7.1 | -5.2 | 12.6>12.6 | 5053 | 1229 | -2522 | 834 | 9.8 | 0.23 | 0.99 |
| 1_lots_rev | 1Lrev_G60_k2.00_m0.50 (best key) | -140 | -177 | -162 | 0.0 | 1.8 | 12.6>12.6 | 423 | 151 | -433 | 897 | -0.3 | - | - |
| 1_lots_rev | 1Lrev_G15_k2.00_m0.50 (best equal-mean dd) | -198 | -159 | -241 | 4.7 | 3.9 | 12.6>12.6 | 1081 | 563 | -595 | -298 | -0.3 | 0.27 | 1.00 |
| 1_stop | 1S_G30_k2.00_S45 (best key) | 370 | 266 | -262 | -5.9 | -3.7 | 12.6>19.3 | 2600 | 1184 | -1229 | 870 | -1.8 | - | - |
| 1_stop | 1S_G30_k1.50_S45 (best equal-mean dd) | 354 | 278 | -411 | -5.1 | -3.0 | 12.6>19.5 | 2684 | 1063 | -1333 | 870 | -1.8 | 0.08 | 1.00 |
| 1_stop_rev | 1Srev_G60_k0.75_S45 (best key) | 80 | 61 | 47 | 0.6 | 0.6 | 12.6>13.1 | 251 | -3 | -181 | 0 | -2.3 | 0.43 | 1.00 |
| 1_stop_rev | 1Srev_G60_k0.75_S45 (best equal-mean dd) | 80 | 61 | 47 | 0.6 | 0.6 | 12.6>13.1 | 251 | -3 | -181 | 0 | -2.3 | 0.43 | 1.00 |
| 1_tgt | 1T_G15_k2.00_T45 (best key) | -412 | -742 | -613 | 3.6 | 0.7 | 12.6>11.3 | 7585 | 1200 | -1696 | -2240 | -9.9 | - | - |
| 1_tgt | 1T_G60_k1.50_T30 (best equal-mean dd) | -163 | -1449 | -1032 | 13.1 | -2.7 | 12.6>9.3 | 17884 | 2309 | -4965 | -4260 | -9.9 | 0.49 | 0.56 |
| 1_tgt_rev | 1Trev_G60_k1.00_T45 (best key) | -240 | -265 | -241 | -0.0 | 2.0 | 12.6>12.6 | 601 | 41 | -597 | -300 | 0.3 | - | - |
| 1_tgt_rev | 1Trev_G15_k1.00_T30 (best equal-mean dd) | -575 | -479 | -881 | 13.4 | 8.0 | 12.6>12.2 | 2454 | -371 | -1167 | -2400 | 0.3 | 0.06 | 0.63 |
| 3_stagstop | 3SS_f0.50_a0.75_r0_rech (best key) | -23 | 18 | -26 | -3.6 | -1.4 | 12.6>12.6 | 631 | 465 | -526 | 0 | 3.9 | - | - |
| 3_stagstop | 3SS_f0.33_a0.40_r0_fresh (best equal-mean dd) | 76 | -47 | 88 | 0.2 | 1.3 | 12.6>12.6 | 200 | 207 | -14 | 0 | 3.9 | - | - |
| 4_probe | 4PA_f0.50_p0.10_all_s1 (best key) | -396 | -439 | -338 | -3.9 | -1.8 | 12.6>12.6 | 816 | -360 | -486 | -732 | 7.0 | - | - |
| 4_probe | 4PA_f0.50_p0.10_fresh_s0 (best equal-mean dd) | -434 | -559 | -309 | 6.7 | -6.1 | 12.6>12.6 | 5141 | 1267 | -2625 | 700 | 7.0 | - | - |
| 4_probe_calm | 4PC_f0.50_N30_X10_all_s1 (best key) | -268 | -268 | -117 | 3.1 | -0.5 | 12.6>12.6 | 989 | 20 | -472 | -863 | 8.3 | - | - |
| 4_probe_calm | 4PC_f0.50_N30_X10_fresh_s0 (best equal-mean dd) | -174 | -435 | -293 | 7.1 | -5.4 | 12.6>12.6 | 5142 | 1229 | -2594 | 823 | 8.3 | - | - |
| 6_tstop | 6TP_N40_p0.10_half_rech (best key) | -893 | -992 | -872 | -1.2 | 0.9 | 12.6>9.6 | 5257 | 1580 | -2401 | -2162 | -18.3 | - | - |
| 6_tstop | 6TP_N10_p0.10_flat_rech (best equal-mean dd) | -2363 | -2387 | -1120 | 22.3 | -7.4 | 12.6>5.2 | 16029 | 2612 | -8242 | -2422 | -18.3 | 0.04 | 0.04 |
| 6_tstop_loss | 6TL_N5_t0.40_half_rech (best key) | 108 | 31 | 18 | 1.9 | 3.8 | 12.6>11.5 | 786 | 207 | -557 | 1190 | 5.4 | - | - |
| 6_tstop_loss | 6TL_N10_t0.25_flat_rech (best equal-mean dd) | 430 | -134 | -150 | 9.8 | -4.6 | 12.6>9.2 | 3210 | 259 | -1332 | 1940 | 5.4 | 0.01 | 0.03 |
| 7_cluster | 7C_W300_skip (best key) | 476 | 79 | 54 | 2.7 | 3.8 | 12.6>11.6 | 2056 | 209 | 350 | -356 | 0.4 | 0.05 | 0.50 |
| 7_cluster | 7C_W600_T30 (best equal-mean dd) | 326 | -8 | 124 | 3.6 | -0.1 | 12.6>12.3 | 1393 | 584 | 183 | 55 | 0.4 | 0.36 | 0.44 |
| 7_cluster_n | 7N_n4_half (best key) | 0 | 0 | 0 | 0.0 | 0.0 | 12.6>12.6 | 47 | 0 | 0 | 0 | 1.5 | - | - |
| 7_cluster_n | 7N_n2_T45 (best equal-mean dd) | -4 | 105 | -191 | 2.0 | -0.4 | 12.6>12.5 | 661 | 183 | -88 | -300 | 1.5 | 0.32 | 0.97 |
| 8_rung | 8R_T40_f0.50_flNone (best key) | 157 | -181 | -53 | 4.5 | 1.1 | 12.6>12.6 | 1808 | 543 | -848 | -305 | - | - | - |
| 8_rung | 8R_T30_f0.33_fl0.0 (best equal-mean dd) | 939 | -389 | -394 | 12.6 | -1.7 | 12.6>11.8 | 4186 | 1131 | -2188 | -1747 | - | - | - |
| 8_rung_q | 8Rq_T40_f0.50_flNone (best key) | 157 | -181 | -48 | 4.5 | 1.1 | 12.6>12.6 | 1808 | 543 | -848 | -305 | - | - | - |
| 8_rung_q | 8Rq_T30_f0.33_fl2.0 (best equal-mean dd) | 289 | -728 | -413 | 13.0 | -1.4 | 12.6>11.8 | 4185 | 1152 | -2279 | -1547 | - | - | - |
| 8_target | 8T_T55 (best key) | -156 | -316 | -444 | -1.1 | 1.0 | 12.6>12.3 | 2398 | -122 | -577 | -640 | -7.2 | - | - |
| 8_target | 8T_T35 (best equal-mean dd) | -1038 | -1831 | -1417 | 23.0 | -0.3 | 12.6>9.9 | 16298 | 1964 | -5077 | -6455 | -7.2 | 0.08 | 0.12 |
| 8_target_q | 8Tq_T55 (best key) | -272 | -443 | -444 | -3.7 | -1.5 | 12.6>12.3 | 2332 | -84 | -522 | -640 | -7.2 | - | - |
| 8_target_q | 8Tq_T35 (best equal-mean dd) | -1038 | -1858 | -1505 | 23.0 | -0.3 | 12.6>9.9 | 16298 | 1812 | -5170 | -6455 | -7.2 | 0.05 | 0.12 |

### K7 at 3x lots (hypothetical) (first-order screen, 418 cells)

Each family: the cell with the best minimum of the L6M, HOLD and PRE mean change, and the cell with the best equal-mean drawdown cut. Money is $/week of the whole stack against the live stack (same kernel, no rule). dd = stack max drawdown change in percent, positive = better. fs = full stops per week (live to new). rec = recoveries lost $/wk. w20 / best20 = $/wk change in the 20 worst / 20 best stack weeks. frozen wk = $ change of the frozen live week 11-01..05 (the stack as traded was +$85.7k for P7 alone; a negative number means the rule would have cost trend-week winners). WF dd cut = purged walk-forward (monthly re-pick of the lowest-26-week-drawdown cell of the family, 7-day embargo) stack drawdown cut against no rule, positive = better. p = placebo p on the equal-mean drawdown cut (forward-only shifted labels / random level) and family-null p.

| family | cell | L6M $/wk | HOLD $/wk | PRE $/wk | L6M dd% | HOLD dd% | fs/wk | rec $/wk | w20 $/wk | best20 $/wk | frozen wk $ | WF dd cut % (family) | p_plc | p_fam |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1_combo | 1C_m0.50_T45_S60 (best key) | -2947 | -3511 | -3805 | 31.7 | 18.2 | 12.6>11.3 | 56873 | 10442 | -17434 | -5773 | 14.6 | - | - |
| 1_combo | 1C_m0.50_T30_S60 (best equal-mean dd) | -2864 | -4809 | -4329 | 39.0 | 14.2 | 12.6>9.3 | 73764 | 11992 | -22396 | -7655 | 14.6 | 0.55 | 0.96 |
| 1_lots | 1L_G15_k2.00_m0.50 (best key) | -1271 | -1455 | -1300 | 14.0 | 18.1 | 12.6>12.6 | 35653 | 6532 | -12734 | -13634 | 30.9 | - | - |
| 1_lots | 1L_G30_k1.50_m0.33 (best equal-mean dd) | -3373 | -2994 | -2823 | 40.0 | 30.5 | 12.6>12.6 | 68813 | 12879 | -23097 | -28132 | 30.9 | 0.12 | 0.97 |
| 1_lots_rev | 1Lrev_G30_k1.00_m0.50 (best key) | -236 | 136 | -466 | -0.5 | 0.3 | 12.6>12.6 | 4276 | 674 | -2090 | -4681 | -2.8 | - | - |
| 1_lots_rev | 1Lrev_G15_k1.00_m0.33 (best equal-mean dd) | -499 | -464 | -1850 | 9.2 | -2.1 | 12.6>12.6 | 9775 | 864 | -4105 | -6972 | -2.8 | 0.44 | 1.00 |
| 1_stop | 1S_G30_k2.00_S45 (best key) | 1109 | 797 | -787 | -7.5 | 7.9 | 12.6>19.3 | 7800 | 3553 | -3688 | 2610 | 0.6 | - | - |
| 1_stop | 1S_G30_k1.50_S45 (best equal-mean dd) | 1061 | 835 | -1233 | -6.0 | 9.2 | 12.6>19.5 | 8051 | 3190 | -3999 | 2610 | 0.6 | 0.04 | 1.00 |
| 1_stop_rev | 1Srev_G60_k0.75_S45 (best key) | 241 | 182 | 142 | 1.0 | 4.9 | 12.6>13.1 | 753 | -9 | -543 | 0 | -4.8 | 0.43 | 1.00 |
| 1_stop_rev | 1Srev_G60_k0.75_S45 (best equal-mean dd) | 241 | 182 | 142 | 1.0 | 4.9 | 12.6>13.1 | 753 | -9 | -543 | 0 | -4.8 | 0.43 | 1.00 |
| 1_tgt | 1T_G15_k2.00_T45 (best key) | -1236 | -2225 | -1840 | 12.1 | -10.5 | 12.6>11.3 | 22755 | 3601 | -5088 | -6721 | -20.5 | - | - |
| 1_tgt | 1T_G60_k1.50_T30 (best equal-mean dd) | -488 | -4348 | -3097 | 47.0 | -5.1 | 12.6>9.3 | 53653 | 6928 | -14894 | -12780 | -20.5 | 0.39 | 0.41 |
| 1_tgt_rev | 1Trev_G60_k1.00_T45 (best key) | -720 | -796 | -724 | 3.0 | -2.8 | 12.6>12.6 | 1803 | 123 | -1790 | -900 | 0.6 | - | - |
| 1_tgt_rev | 1Trev_G15_k1.00_T30 (best equal-mean dd) | -1726 | -1437 | -2642 | 32.8 | -12.2 | 12.6>12.2 | 7361 | -1113 | -3502 | -7200 | 0.6 | 0.07 | 0.99 |
| 3_stagstop | 3SS_f0.50_a0.75_r1_fresh (best key) | -7 | 30 | 121 | 5.9 | 5.5 | 12.6>12.2 | 1013 | 592 | 20 | 0 | -18.2 | - | - |
| 3_stagstop | 3SS_f0.33_a0.60_r1_fresh (best equal-mean dd) | -186 | -128 | -252 | 17.6 | 5.5 | 12.6>12.2 | 928 | 1481 | -910 | 0 | -18.2 | 0.01 | 0.02 |
| 4_probe | 4PA_f0.50_p0.25_all_s0 (best key) | -2420 | -1887 | -1731 | -1.0 | 13.5 | 12.6>13.7 | 14186 | 1201 | -5946 | -9304 | 9.8 | - | - |
| 4_probe | 4PA_f0.33_p0.10_fresh_s0 (best equal-mean dd) | -4330 | -3759 | -3718 | 31.5 | 27.1 | 12.6>12.7 | 72397 | 13254 | -23086 | -21938 | 9.8 | 0.34 | 1.00 |
| 4_probe_calm | 4PC_f0.50_N120_X10_all_s0 (best key) | -843 | -234 | -805 | 7.8 | 6.8 | 12.6>12.8 | 18192 | 2203 | -5419 | -19987 | 20.2 | - | - |
| 4_probe_calm | 4PC_f0.33_N300_X5_all_s0 (best equal-mean dd) | -3410 | -2070 | -2891 | 35.2 | 18.8 | 12.6>13.2 | 62081 | 6238 | -17749 | -23463 | 20.2 | 1.00 | 1.00 |
| 6_tstop | 6TP_N40_p0.10_half_all (best key) | -1172 | -1806 | -1758 | 1.1 | 6.4 | 12.6>12.6 | 8461 | 1963 | -5168 | -265 | -16.0 | - | - |
| 6_tstop | 6TP_N20_p0.40_flat_rech (best equal-mean dd) | -3312 | -5229 | -5008 | 27.8 | 3.2 | 12.6>5.0 | 50034 | 9895 | -20396 | -7590 | -16.0 | 0.31 | 0.36 |
| 6_tstop_loss | 6TL_N10_t0.40_half_rech (best key) | 94 | -150 | 265 | 2.2 | 3.7 | 12.6>12.6 | 1650 | 337 | -414 | 1315 | 6.4 | - | - |
| 6_tstop_loss | 6TL_N10_t0.25_flat_rech (best equal-mean dd) | 1291 | -401 | -449 | 31.9 | -3.5 | 12.6>9.2 | 9629 | 777 | -3996 | 5820 | 6.4 | 0.01 | 0.03 |
| 7_cluster | 7C_W300_skip (best key) | 1427 | 238 | 162 | 15.8 | 0.7 | 12.6>11.6 | 6167 | 628 | 1050 | -1067 | 0.7 | 0.01 | 0.57 |
| 7_cluster | 7C_W600_T30 (best equal-mean dd) | 978 | -24 | 371 | 17.8 | -5.6 | 12.6>12.3 | 4178 | 1753 | 550 | 165 | 0.7 | 0.48 | 0.48 |
| 7_cluster_n | 7N_n4_half (best key) | -48 | -23 | -26 | -1.1 | 0.0 | 12.6>12.6 | 235 | 23 | 0 | 0 | 0.0 | - | - |
| 7_cluster_n | 7N_n2_skip (best equal-mean dd) | -2045 | -778 | -691 | 17.0 | -2.8 | 12.6>11.8 | 7897 | -177 | -2353 | 8368 | 0.0 | 0.17 | 0.98 |
| 8_rung | 8R_T40_f0.33_flNone (best key) | -544 | -1089 | -936 | 12.3 | 0.3 | 12.6>12.6 | 12944 | 2104 | -3462 | -3160 | - | - | - |
| 8_rung | 8R_T30_f0.33_fl2.0 (best equal-mean dd) | 2806 | -2601 | -2805 | 56.6 | -20.2 | 12.6>9.0 | 39937 | 6087 | -10987 | -949 | - | - | - |
| 8_rung_q | 8Rq_T40_f0.33_flNone (best key) | -757 | -1193 | -1012 | 12.3 | 0.3 | 12.6>12.6 | 12944 | 2104 | -3462 | -3160 | - | - | - |
| 8_rung_q | 8Rq_T30_f0.50_fl2.0 (best equal-mean dd) | 953 | -3938 | -3947 | 55.3 | -19.2 | 12.6>9.0 | 47968 | 5930 | -13863 | -2587 | - | - | - |
| 8_target | 8T_T55 (best key) | -467 | -947 | -1331 | -7.1 | -11.8 | 12.6>12.3 | 7194 | -365 | -1730 | -1921 | -14.1 | - | - |
| 8_target | 8T_T35 (best equal-mean dd) | -3115 | -5494 | -4251 | 55.5 | -12.2 | 12.6>9.9 | 48895 | 5893 | -15230 | -19365 | -14.1 | 0.03 | 0.04 |
| 8_target_q | 8Tq_T55 (best key) | -817 | -1329 | -1331 | -12.2 | -17.3 | 12.6>12.3 | 6995 | -253 | -1567 | -1921 | -15.0 | - | - |
| 8_target_q | 8Tq_T35 (best equal-mean dd) | -3115 | -5575 | -4515 | 55.5 | -12.2 | 12.6>9.9 | 48895 | 5435 | -15511 | -19365 | -15.0 | 0.02 | 0.04 |

### U7 (first-order screen, 418 cells)

Each family: the cell with the best minimum of the L6M, HOLD and PRE mean change, and the cell with the best equal-mean drawdown cut. Money is $/week of the whole stack against the live stack (same kernel, no rule). dd = stack max drawdown change in percent, positive = better. fs = full stops per week (live to new). rec = recoveries lost $/wk. w20 / best20 = $/wk change in the 20 worst / 20 best stack weeks. frozen wk = $ change of the frozen live week 11-01..05 (the stack as traded was +$85.7k for P7 alone; a negative number means the rule would have cost trend-week winners). WF dd cut = purged walk-forward (monthly re-pick of the lowest-26-week-drawdown cell of the family, 7-day embargo) stack drawdown cut against no rule, positive = better. p = placebo p on the equal-mean drawdown cut (forward-only shifted labels / random level) and family-null p.

| family | cell | L6M $/wk | HOLD $/wk | PRE $/wk | L6M dd% | HOLD dd% | fs/wk | rec $/wk | w20 $/wk | best20 $/wk | frozen wk $ | WF dd cut % (family) | p_plc | p_fam |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1_combo | 1C_m0.50_T45_S45 (best key) | -1266 | -1442 | -1060 | 19.8 | -13.5 | 3.3>3.7 | 8702 | 4106 | -5217 | 1137 | 8.8 | - | - |
| 1_combo | 1C_m0.50_T45_S60 (best equal-mean dd) | -1079 | -1905 | -907 | 20.0 | -10.4 | 3.3>3.0 | 8055 | 3543 | -4900 | 1137 | 8.8 | 0.05 | 0.17 |
| 1_lots | 1L_G60_k1.50_m0.50 (best key) | -1009 | -1106 | -729 | 10.6 | -1.6 | 3.3>3.3 | 5847 | 1881 | -3568 | 1437 | 2.0 | - | - |
| 1_lots | 1L_G60_k1.00_m0.50 (best equal-mean dd) | -1205 | -1530 | -718 | 12.1 | -4.7 | 3.3>3.3 | 6364 | 2171 | -4169 | 1437 | 2.0 | 0.14 | 0.86 |
| 1_lots_rev | 1Lrev_G15_k2.00_m0.50 (best key) | 50 | 234 | 62 | -6.6 | -5.0 | 3.3>3.3 | 3548 | 1343 | -552 | 1527 | 0.0 | - | - |
| 1_lots_rev | 1Lrev_G15_k0.75_m0.50 (best equal-mean dd) | 452 | 531 | -158 | -8.1 | -5.9 | 3.3>3.3 | 1880 | 558 | 532 | -1105 | 0.0 | 0.69 | 1.00 |
| 1_stop | 1S_G60_k2.00_S45 (best key) | 515 | 218 | 203 | 8.6 | -8.7 | 3.3>4.1 | 920 | 1461 | -561 | 0 | 2.0 | 0.08 | 0.39 |
| 1_stop | 1S_G60_k2.00_S45 (best equal-mean dd) | 515 | 218 | 203 | 8.6 | -8.7 | 3.3>4.1 | 920 | 1461 | -561 | 0 | 2.0 | 0.08 | 0.39 |
| 1_stop_rev | 1Srev_G15_k1.00_S45 (best key) | 204 | 492 | -201 | -9.8 | -7.5 | 3.3>3.9 | 918 | -63 | 194 | 0 | 0.0 | - | - |
| 1_stop_rev | 1Srev_G15_k0.75_S45 (best equal-mean dd) | 596 | 657 | -264 | 1.2 | 0.2 | 3.3>3.8 | 502 | 75 | 406 | 0 | 0.0 | 0.43 | 0.88 |
| 1_tgt | 1T_G15_k2.00_T45 (best key) | 243 | -156 | -179 | 18.4 | -8.4 | 3.3>3.0 | 2641 | 2933 | -1218 | -600 | 5.9 | - | - |
| 1_tgt | 1T_G30_k2.00_T30 (best equal-mean dd) | -131 | -960 | -597 | 24.4 | -8.1 | 3.3>2.8 | 5402 | 2691 | -3059 | -1200 | 5.9 | 0.02 | 0.03 |
| 1_tgt_rev | 1Trev_G15_k1.00_T30 (best key) | -325 | -21 | -164 | -13.2 | -10.9 | 3.3>3.1 | 2523 | 1520 | -975 | -3010 | 0.0 | - | - |
| 1_tgt_rev | 1Trev_G60_k0.75_T45 (best equal-mean dd) | -882 | 142 | -208 | -6.2 | -4.0 | 3.3>3.3 | 1026 | 689 | -71 | -1510 | 0.0 | 0.95 | 1.00 |
| 3_stagstop | 3SS_f0.33_a0.75_r0_rech (best key) | 57 | 38 | -4 | 1.4 | -4.2 | 3.3>3.3 | 502 | 403 | -241 | 0 | -2.0 | 0.51 | 0.59 |
| 3_stagstop | 3SS_f0.33_a0.40_r0_rech (best equal-mean dd) | -501 | -292 | -56 | 9.7 | -1.4 | 3.3>3.3 | 1984 | 1011 | -1194 | 450 | -2.0 | 0.08 | 0.09 |
| 4_probe | 4PA_f0.50_p0.10_all_s0 (best key) | -280 | -258 | -202 | 6.6 | 0.5 | 3.3>3.7 | 1474 | -184 | -175 | -340 | 2.1 | - | - |
| 4_probe | 4PA_f0.50_p0.25_fresh_s0 (best equal-mean dd) | -625 | -720 | -760 | 11.1 | -5.6 | 3.3>3.4 | 6953 | 1637 | -3228 | 33 | 2.1 | 0.01 | 0.01 |
| 4_probe_calm | 4PC_f0.50_N30_X10_all_s1 (best key) | -140 | -207 | -179 | 0.9 | 1.5 | 3.3>3.3 | 999 | 210 | -11 | -66 | 10.6 | - | - |
| 4_probe_calm | 4PC_f0.50_N300_X10_all_s1 (best equal-mean dd) | -253 | -139 | -224 | 7.0 | -9.3 | 3.3>3.3 | 4807 | 728 | -23 | -3903 | 10.6 | 1.00 | 1.00 |
| 6_tstop | 6TP_N10_p0.10_half_all (best key) | -653 | -390 | -648 | 3.0 | -2.4 | 3.3>3.1 | 4199 | 2340 | -2613 | 2502 | 9.2 | - | - |
| 6_tstop | 6TP_N20_p0.25_flat_rech (best equal-mean dd) | -3740 | -2303 | -1840 | 34.6 | -15.4 | 3.3>1.7 | 7320 | 2639 | -6458 | 2145 | 9.2 | 0.01 | 0.01 |
| 6_tstop_loss | 6TL_N20_t0.40_flat_all (best key) | 449 | 725 | 270 | 2.4 | -10.4 | 3.3>2.4 | 986 | 590 | 35 | 0 | -3.9 | 0.44 | 0.78 |
| 6_tstop_loss | 6TL_N5_t0.25_flat_all (best equal-mean dd) | 807 | 952 | 263 | 12.6 | -12.1 | 3.3>2.4 | 1464 | 726 | 218 | 330 | -3.9 | 0.01 | 0.09 |
| 7_cluster | 7C_W180_skip (best key) | 466 | 219 | 230 | 6.2 | -5.6 | 3.3>2.9 | 1543 | 735 | -304 | 4069 | 0.0 | 0.01 | 1.00 |
| 7_cluster | 7C_W600_skip (best equal-mean dd) | 2763 | 916 | -87 | 32.0 | -6.3 | 3.3>2.0 | 4268 | 2068 | -314 | 4069 | 0.0 | 0.01 | 0.01 |
| 7_cluster_n | 7N_n4_half (best key) | 0 | 0 | 0 | 0.0 | 0.0 | 3.3>3.3 | -0 | 0 | 0 | 0 | 0.0 | - | - |
| 7_cluster_n | 7N_n2_T45 (best equal-mean dd) | 214 | -108 | -44 | 10.9 | -1.5 | 3.3>3.3 | 449 | 1589 | 238 | 0 | 0.0 | 0.20 | 0.20 |
| 8_rung | 8R_T40_f0.33_flNone (best key) | -13 | -122 | -63 | 7.9 | -2.4 | 3.3>3.3 | 1824 | 1335 | -822 | -802 | - | - | - |
| 8_rung | 8R_T40_f0.33_fl2.0 (best equal-mean dd) | 233 | 1 | -296 | 13.9 | -10.3 | 3.3>2.7 | 3314 | 2988 | -1549 | -802 | - | - | - |
| 8_rung_q | 8Rq_T40_f0.33_flNone (best key) | -13 | -122 | -63 | 7.9 | -2.4 | 3.3>3.3 | 1824 | 1335 | -822 | -802 | - | - | - |
| 8_rung_q | 8Rq_T40_f0.33_fl2.0 (best equal-mean dd) | 375 | 70 | -296 | 14.0 | -10.3 | 3.3>2.7 | 3175 | 2988 | -1549 | -802 | - | - | - |
| 8_target | 8T_T55 (best key) | -516 | -502 | -513 | -5.6 | -3.4 | 3.3>3.2 | 1270 | 556 | -802 | -100 | 10.9 | - | - |
| 8_target | 8T_T40 (best equal-mean dd) | -870 | -640 | -424 | 16.1 | -9.5 | 3.3>2.7 | 6022 | 4098 | -2839 | -2810 | 10.9 | 0.14 | 0.30 |
| 8_target_q | 8Tq_T45 (best key) | -642 | -521 | -265 | 8.3 | -6.9 | 3.3>2.9 | 4504 | 3761 | -2070 | -2110 | -0.4 | - | - |
| 8_target_q | 8Tq_T40 (best equal-mean dd) | -870 | -640 | -424 | 16.1 | -9.5 | 3.3>2.7 | 6022 | 4098 | -2839 | -2810 | -0.4 | 0.23 | 0.30 |

### M7 (first-order screen, 418 cells)

Each family: the cell with the best minimum of the L6M, HOLD and PRE mean change, and the cell with the best equal-mean drawdown cut. Money is $/week of the whole stack against the live stack (same kernel, no rule). dd = stack max drawdown change in percent, positive = better. fs = full stops per week (live to new). rec = recoveries lost $/wk. w20 / best20 = $/wk change in the 20 worst / 20 best stack weeks. frozen wk = $ change of the frozen live week 11-01..05 (the stack as traded was +$85.7k for P7 alone; a negative number means the rule would have cost trend-week winners). WF dd cut = purged walk-forward (monthly re-pick of the lowest-26-week-drawdown cell of the family, 7-day embargo) stack drawdown cut against no rule, positive = better. p = placebo p on the equal-mean drawdown cut (forward-only shifted labels / random level) and family-null p.

| family | cell | L6M $/wk | HOLD $/wk | PRE $/wk | L6M dd% | HOLD dd% | fs/wk | rec $/wk | w20 $/wk | best20 $/wk | frozen wk $ | WF dd cut % (family) | p_plc | p_fam |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1_combo | 1C_m0.50_T30_S60 (best key) | 89 | 155 | -31 | 19.2 | 14.5 | 1.9>1.3 | 9736 | 3368 | -2813 | -1854 | -4.2 | 0.02 | 0.02 |
| 1_combo | 1C_m0.50_T30_S60 (best equal-mean dd) | 89 | 155 | -31 | 19.2 | 14.5 | 1.9>1.3 | 9736 | 3368 | -2813 | -1854 | -4.2 | 0.02 | 0.02 |
| 1_lots | 1L_G15_k2.00_m0.50 (best key) | 176 | 383 | 139 | 9.1 | 9.1 | 1.9>1.9 | 2068 | 1761 | -699 | -2107 | 3.5 | 0.49 | 0.97 |
| 1_lots | 1L_G15_k0.75_m0.50 (best equal-mean dd) | 340 | 442 | 29 | 11.2 | 10.1 | 1.9>1.9 | 2209 | 1854 | -766 | -2485 | 3.5 | 0.41 | 0.70 |
| 1_lots_rev | 1Lrev_G60_k2.00_m0.50 (best key) | -66 | 101 | -70 | 3.4 | 2.7 | 1.9>1.9 | 470 | 219 | -266 | 816 | 2.8 | - | - |
| 1_lots_rev | 1Lrev_G15_k2.00_m0.50 (best equal-mean dd) | -40 | 104 | -93 | 3.4 | 2.7 | 1.9>1.9 | 517 | 253 | -386 | -379 | 2.8 | 0.67 | 1.00 |
| 1_stop | 1S_G60_k0.75_S45 (best key) | 21 | -52 | 35 | -0.7 | 1.3 | 1.9>4.3 | 419 | 379 | -153 | 687 | -0.1 | - | - |
| 1_stop | 1S_G15_k0.75_S45 (best equal-mean dd) | 29 | -56 | 33 | -0.5 | 1.6 | 1.9>4.3 | 419 | 424 | -174 | 687 | -0.1 | 0.17 | 1.00 |
| 1_stop_rev | 1Srev_G60_k2.00_S45 (best key) | 71 | 38 | 112 | -0.6 | -0.0 | 1.9>2.4 | -0 | 139 | 72 | 687 | -0.6 | - | - |
| 1_stop_rev | 1Srev_G30_k1.50_S45 (best equal-mean dd) | 88 | 21 | 98 | -0.6 | -0.0 | 1.9>2.3 | -0 | 155 | 96 | 0 | -0.6 | 0.67 | 1.00 |
| 1_tgt | 1T_G15_k1.50_T30 (best key) | 191 | 248 | 60 | 5.6 | 5.1 | 1.9>1.3 | 7928 | 2257 | -1809 | -4950 | -7.8 | 0.25 | 1.00 |
| 1_tgt | 1T_G15_k1.00_T30 (best equal-mean dd) | -2 | 29 | -81 | 10.6 | 8.6 | 1.9>1.3 | 8518 | 2103 | -2214 | -955 | -7.8 | 0.04 | 0.93 |
| 1_tgt_rev | 1Trev_G60_k0.75_T45 (best key) | -87 | -122 | -8 | -1.6 | -0.8 | 1.9>1.8 | 413 | -138 | -278 | 0 | 4.0 | - | - |
| 1_tgt_rev | 1Trev_G30_k2.00_T45 (best equal-mean dd) | -140 | -228 | -335 | 1.8 | 0.1 | 1.9>1.8 | 1015 | -291 | -711 | -540 | 4.0 | 0.35 | 1.00 |
| 3_stagstop | 3SS_f0.33_a0.60_r0_fresh (best key) | 11 | 19 | 17 | -0.0 | -0.1 | 1.9>1.9 | 76 | 47 | 52 | -1993 | -0.3 | - | - |
| 3_stagstop | 3SS_f0.33_a0.40_r0_all (best equal-mean dd) | -74 | -41 | -154 | 2.7 | 4.5 | 1.9>1.9 | 1210 | 694 | -513 | -2765 | -0.3 | 0.02 | 0.02 |
| 4_probe | 4PA_f0.33_p0.40_fresh_s0 (best key) | 291 | 358 | 49 | 13.4 | 10.3 | 1.9>1.9 | 2374 | 1786 | -989 | -353 | 3.2 | - | - |
| 4_probe | 4PA_f0.50_p0.25_fresh_s0 (best equal-mean dd) | 293 | 388 | 42 | 13.6 | 10.6 | 1.9>1.9 | 2313 | 1855 | -927 | -1656 | 3.2 | 0.10 | 0.17 |
| 4_probe_calm | 4PC_f0.50_N30_X5_fresh_s0 (best key) | 430 | 429 | 91 | 12.2 | 10.0 | 1.9>1.9 | 2239 | 1757 | -803 | -1264 | 4.1 | 0.10 | 0.36 |
| 4_probe_calm | 4PC_f0.50_N60_X5_fresh_s1 (best equal-mean dd) | 533 | 493 | 57 | 14.1 | 10.8 | 1.9>1.9 | 2277 | 1789 | -755 | -2485 | 4.1 | 0.01 | 0.01 |
| 6_tstop | 6TP_N40_p0.10_half_rech (best key) | -239 | -238 | -218 | -6.2 | -4.0 | 1.9>1.5 | 2102 | 697 | -346 | 2315 | -8.0 | - | - |
| 6_tstop | 6TP_N5_p0.10_flat_all (best equal-mean dd) | 1155 | 743 | -1188 | 21.8 | 17.6 | 1.9>0.8 | 8387 | 3399 | -3169 | -5962 | -8.0 | 0.01 | 0.01 |
| 6_tstop_loss | 6TL_N40_t0.40_half_all (best key) | 98 | 17 | 72 | 0.8 | 0.1 | 1.9>1.7 | 144 | 381 | 63 | 0 | 0.4 | 0.19 | 0.98 |
| 6_tstop_loss | 6TL_N5_t0.25_flat_rech (best equal-mean dd) | -28 | -97 | -155 | 4.5 | 2.4 | 1.9>1.6 | 1542 | 344 | -780 | -2602 | 0.4 | 0.17 | 0.84 |
| 7_cluster | 7C_W180_skip (best key) | 240 | 178 | 109 | 3.1 | -0.5 | 1.9>1.9 | 611 | 227 | 248 | 869 | 2.0 | 0.07 | 0.27 |
| 7_cluster | 7C_W600_skip (best equal-mean dd) | 895 | 609 | -40 | 8.8 | -1.8 | 1.9>1.8 | 1269 | 577 | 253 | -1522 | 2.0 | 0.01 | 0.01 |
| 7_cluster_n | 7N_n4_skip (best key) | 5 | 2 | 2 | 0.0 | 0.0 | 1.9>1.9 | 141 | 71 | 6 | 0 | 0.0 | 0.48 | 0.98 |
| 7_cluster_n | 7N_n2_skip (best equal-mean dd) | -71 | 50 | -8 | 4.8 | 5.2 | 1.9>1.8 | 1457 | -110 | -34 | -2395 | 0.0 | 0.13 | 0.27 |
| 8_rung | 8R_T30_f0.50_flNone (best key) | 27 | 250 | -68 | 1.8 | 3.4 | 1.9>1.9 | 1298 | 749 | -619 | 421 | - | - | - |
| 8_rung | 8R_T40_f0.33_fl2.0 (best equal-mean dd) | 340 | 323 | -432 | 2.0 | 1.8 | 1.9>1.8 | 1205 | 898 | -658 | -1602 | - | - | - |
| 8_rung_q | 8Rq_T30_f0.50_flNone (best key) | 27 | 200 | -84 | 1.8 | 3.4 | 1.9>1.9 | 1298 | 749 | -679 | 421 | - | - | - |
| 8_rung_q | 8Rq_T40_f0.33_fl2.0 (best equal-mean dd) | 245 | 229 | -432 | 2.0 | 1.8 | 1.9>1.8 | 1205 | 898 | -658 | -1602 | - | - | - |
| 8_target | 8T_T55 (best key) | 621 | 386 | -175 | 7.4 | 2.5 | 1.9>1.8 | 1133 | 324 | -128 | 2765 | 4.7 | 0.22 | 0.52 |
| 8_target | 8T_T55 (best equal-mean dd) | 621 | 386 | -175 | 7.4 | 2.5 | 1.9>1.8 | 1133 | 324 | -128 | 2765 | 4.7 | 0.22 | 0.52 |
| 8_target_q | 8Tq_T55 (best key) | 421 | 233 | -180 | 5.1 | 2.5 | 1.9>1.8 | 1113 | 157 | -173 | 2765 | -2.9 | 0.50 | 0.79 |
| 8_target_q | 8Tq_T50 (best equal-mean dd) | -13 | -160 | -467 | 10.0 | -1.2 | 1.9>1.8 | 2927 | 709 | -1265 | 420 | -2.9 | 0.34 | 0.55 |