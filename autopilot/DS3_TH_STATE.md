# DS3_TH_STATE - TH-L2-S state cut: best cut per book, scored on the exact 1-s MBP-10 state arrays
**Label: TH-L2-S on exact 1-s MBP-10; entries from the replica engine (not live-matched); first-order Stage 1 + cascade Stage 2.** Prereg: autopilot/PREREG_TH_L2_S.md (Amendment 2) with sha lines in DECISIONS.md. Selection data: label days 2023-04-01..2026-10-31; the blind/live week 2026-11-01..11-05 was held out of selection.
Caveats: replica entries are NOT live-matched (about 100 of 187 blind-week trades match); Stage 1 scores each trade as if alone (re-entries/locks ignored); hold-to-bracket = stop signal -+ 60 / target fill average +- 60 (O7 40/90) with the stop/target at the level and time exits at 16:55 ET (O7 16:00) with the same 0.80 cost; deltas are USD per week at live lots, gross (fees cancel), carrying week dropped in windows of >= 8 weeks, MDE = 2.8 sd/sqrt(n).

## 1. Verdict
Deliverable: the best state cut per book (section 2) with policy lines and the fields the grammar lacks. Plain reading of the evidence:
1. In sample (selection data to 2026-10-31) the combined per-book policy beats the live cell and both references on L6M and PRE with the carrying week dropped: Stage 1 vs hold-to-bracket L6M +10655, PRE +250; vs the live cell L6M +10827, PRE +997. Stage 2 (engine cascade, 43 months, fee proxy net) vs the engine never-cut run: L6M +9975 (MDE 10798), PRE +2142 (MDE 4192); vs the engine live-cut HOLD run: L6M +7179, PRE +8047. Both Stage 2 gains are BELOW their MDE, and the PRE stack drawdown with the policy is worse than without it (150123 vs 141791). The carrying week of the L6M gain is ISO week 202630 (+43092 USD of +292478 total in L6M).
2. It does NOT hold out of sample: (a) purged monthly walk-forward of the per-book procedure is negative (total -384272 USD vs the fixed live cell -99685, 2024-01..2026-10); (b) the held-out live week (187 trades) gives -32043 USD for the combined policy vs the actual live exits (per-book cells without session overrides -223, best uniform cell +1389, live cell on state -15708); (c) the family max-stat null (200 worlds, per-book best-of-8,400 re-selection on shifted state) has p = 1.0: the observed best-cell sum +3365 is below the null mean +8450. The random-timing placebo is clean (p = 0.001), i.e. a cut at the state-flagged second beats a cut at a random second of the same trade, but a random thinning of the same arm families does as well.
3. The live cell (30/30x/5 s/p1/newMae) on exact state is about zero vs the engine never-cut run (Stage 2 L6M +354, PRE +653) and negative vs hold-to-bracket in Stage 1 PRE (-747): as coded it does not earn its place; the best uniform cell (30/10x/5s/p10/mae/V0) is -848 / +1082 vs never-cut (Stage 2 L6M / PRE).
4. Reference, ARM-only cut (no state condition, cut as soon as -unreal >= ARM, pooled, Stage 1 USD/week vs hold-to-bracket, L6M / PRE): 15: -15346 / -21978; 20: -13286 / -21414; 25: -4988 / -21106; 30: +788 / -15450; 35: +5951 / -9908; 40: +10614 / -8354; 45: +4471 / -3618; 50: +3000 / -2526. A plain tighter stop wins in the last six months and loses heavily in PRE; the state condition removes most of the PRE damage but does not add a stable edge on top (point 2).
5. Which one to code: the per-book table below is the exact in-sample answer requested. Because the walk-forward, the held-out week and the family null do not support it, the evidence-weighted choice is to code the per-book table ONLY as a shadow/forward-test line next to the live cell, and not to treat its in-sample L6M gain as an expected live gain. "No cut" is a reference row and was not a candidate.

## 2. Best cut per book (exact definition) and policy lines
Definition for every cell: per exchange second s (row interval (s-1, s]); own side = bid for longs, ask for shorts; cancelled_s = sum over own-side levels present at s-1 of max(0, size(s-1) - size(s) - traded at that price in (s-1, s]); pulledW = sum of cancelled over the last W seconds; MedLevel = 0.001 EWMA of (top-5 bid + top-5 ask)/10 each second; fire at second s when -unreal >= ARM (unreal on the per-second mid vs the fill average) AND pulledW >= MULT x MedLevel AND (newMae off OR the adverse extreme was set within the last W seconds, ties count) for PERS consecutive seconds; decision at the end of second s, exit executes at second s+1 at mid(s+1) -+ 0.80 pt; a bracket touch in (s, s+1] wins. W is applied to the pulled window and the newMae window together. Tie rule in the selection: lexicographic key, simpler cell wins (fewer of persistence > 1, newMae on, V1/V2, then lower PERS/window/ARM). Sessions are ENTRY sessions (asia 18:00-02:00 ET, london -08:30, pre -09:30, nyam -12:00, nypm -15:00, close).
| book | ARM pts | ARM % of stop | MULT | W s | PERS s | newMae | arm variant | stage-1 flags (recent/tolerant/dd-first/sign) | nfire/ntrades | L6M | PRE | X' vs hold | L6M vs live | PRE vs live | live cell L6M / PRE vs hold |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7 | 45 | 0.750 | 10 | 2 | 3 | off | V2 | True/True/True/2 | 2049/8623 | +1401 | +31 | +54 | +924 | -54 | -198 / +152 |
| P7 | 45 | 0.750 | 5 | 5 | 10 | off | V0 | True/True/True/2 | 2442/6016 | +6023 | +500 | +1172 | +3494 | +789 | +1101 / +139 |
| M7 | 30 | 0.500 | 10 | 2 | 2 | off | V0 | True/True/True/2 | 2290/4788 | +1281 | +285 | +47 | +647 | +159 | +17 / +202 |
| U7 | 30 | 0.500 | 60 | 15 | 5 | off | V2 | True/True/True/2 | 125/1484 | +905 | +121 | +122 | +529 | +51 | +595 / -8 |
| A7 | 30 | 0.500 | 60 | 15 | 3 | off | V0 | True/True/True/2 | 125/1230 | +731 | +41 | +14 | +411 | +77 | +142 / -2 |
| H7 | 15 | 0.250 | 30 | 10 | 2 | on | V1 | True/True/True/2 | 315/1141 | +1444 | +24 | +84 | +1563 | +82 | +26 / +2 |
| O7 | 25 | 0.625 | 20 | 10 | 10 | off | V0 | True/True/True/2 | 169/506 | +129 | +15 | +90 | +185 | -1 | +39 / +13 |

Session overrides (unit key better than the book cell and L6M gain >= 0.5 MDE): P7_0: 50/5x/3s/p3/mae/V1 (gain L6M +3018, MDE 4924); H7_3: 35/20x/2s/p1/nomae/V2 (gain L6M +161, MDE 299)

Policy-file lines in the D7 grammar (`loss <book> <session|*> conds cut`; fields in DS7.cs ManagePolicy/Feature: pct, mins, secs_ext, dd, recov, vel30, eff120, delta60, imb5/10, wall_*, pulled_mult, ice_against, ahead_rel, tot_rel). Expressible part per book, and the fields the user must add:
- `loss K7 * pct<=-0.7500 pulled_mult>=10 cut` # PERS=3 W=2 V2 clip(ARM*sqrt(lots/4),15,50); needs: pulled_mult must use the exact state definition (net-of-trades cancels over the last window_s seconds / MedLevel) with a per-rule window = 2 s; persistence field: condition true for 3 consecutive seconds; lots-scaled arm (feature lots)
- `loss P7 * pct<=-0.7500 pulled_mult>=5 cut` # PERS=10 W=5 V0 fixed points; needs: pulled_mult must use the exact state definition (net-of-trades cancels over the last window_s seconds / MedLevel) with a per-rule window = 5 s; persistence field: condition true for 10 consecutive seconds
- `loss M7 * pct<=-0.5000 pulled_mult>=10 cut` # PERS=2 W=2 V0 fixed points; needs: pulled_mult must use the exact state definition (net-of-trades cancels over the last window_s seconds / MedLevel) with a per-rule window = 2 s; persistence field: condition true for 2 consecutive seconds
- `loss U7 * pct<=-0.5000 pulled_mult>=60 cut` # PERS=5 W=15 V2 clip(ARM*sqrt(lots/4),15,50); needs: pulled_mult must use the exact state definition (net-of-trades cancels over the last window_s seconds / MedLevel) with a per-rule window = 15 s; persistence field: condition true for 5 consecutive seconds; lots-scaled arm (feature lots)
- `loss A7 * pct<=-0.5000 pulled_mult>=60 cut` # PERS=3 W=15 V0 fixed points; needs: pulled_mult must use the exact state definition (net-of-trades cancels over the last window_s seconds / MedLevel) with a per-rule window = 15 s; persistence field: condition true for 3 consecutive seconds
- `loss H7 * pct<=-0.2500 pulled_mult>=30 secs_ext<=10 cut` # PERS=2 W=10 V1 clip(ARM*sqrt(4/lots),15,50); needs: pulled_mult must use the exact state definition (net-of-trades cancels over the last window_s seconds / MedLevel) with a per-rule window = 10 s; persistence field: condition true for 2 consecutive seconds; lots-scaled arm (feature lots)
- `loss O7 * pct<=-0.6250 pulled_mult>=20 cut` # PERS=10 W=10 V0 fixed points; needs: pulled_mult must use the exact state definition (net-of-trades cancels over the last window_s seconds / MedLevel) with a per-rule window = 10 s; persistence field: condition true for 10 consecutive seconds
Fields the grammar lacks (all books): (a) pulled_mult must be the exact state quantity (cancels net of trades, own side, window W, MedLevel EWMA 0.001) with a per-rule window (today one global ThL2PulledSecs and the old per-print PulledSupport); (b) `persist` (consecutive seconds the whole condition holds); (c) `lots` feature for the V1/V2 lot-scaled arm; (d) the session field matches the CURRENT session at evaluation (Regime = SessionNames[SessionIndex(now)]), while the scored scope is the ENTRY session: add entry_session or accept the difference; (e) evaluation once per second with a 1 s decision latency and the 0.80 pt exit cost is how it was scored. pct is relative to the book stop distance (60 pt; O7 40).
Machine-readable: /mnt/l2/l2vast/_th_state/score/loss_finalists.json

## 3. Stage 1 combined policy, uniform, live cell and references (USD/week, selection data through 2026-10-31, vs hold-to-bracket)
| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| COMB vs hold-to-bracket | +21881 | +22680 | +16582 | +10655 | +4376 | +9824 | +250 | +1387 |
| PERBOOK vs hold-to-bracket | +16962 | +17956 | +11981 | +7186 | +3617 | +4681 | +612 | +1335 |
| COMB_V0 vs hold-to-bracket | +15747 | +9250 | +11144 | +6172 | +1307 | +4453 | -643 | +1636 |
| UNIF vs hold-to-bracket | +7912 | +10255 | +7455 | +6974 | +2604 | +3731 | +105 | +286 |
| LIVE vs hold-to-bracket | +2295 | -902 | -1925 | +500 | +441 | +4917 | -747 | +86 |
| COMB vs live cell | +19586 | +15958 | +19908 | +10827 | +4003 | +10182 | +997 | +1194 |
| PERBOOK vs live cell | +14667 | +11939 | +15292 | +7351 | +1719 | +9110 | +742 | +1142 |
| COMB_V0 vs live cell | +13451 | +13788 | +14456 | +6337 | +1192 | +8642 | +815 | +1444 |
| UNIF vs live cell | +5617 | +6346 | +5362 | +4545 | +1115 | -4892 | -944 | +116 |
| REFERENCE hold-to-bracket weekly level (net of 4.84 fee) | -21447 | -10987 | -9197 | +12089 | +12245 | +449 | +18801 | +2331 |
COMB incl. the live week (windows as of 2026-11-05):
| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| COMB vs hold-to-bracket | -759 | +15167 | +20156 | +12237 | +2340 | +9824 | +250 | +1387 |
| LIVE cell vs hold-to-bracket | -4182 | -4809 | -5193 | -295 | -294 | +4917 | -747 | +86 |
COMB = per-book cells + session overrides; PERBOOK = per-book cells only; COMB_V0 = per-book cells restricted to fixed-point arms; UNIF = best single cell pooled over books (30/10x/5s/p10/mae/V0). nfire: COMB 7570, PERBOOK 7584, UNIF 3711, LIVE 1759 of ~24k trades.

## 4. Grid heat (8,400 cells = 3 arm variants x 2,800; pooled over books; S = min(L6M, PRE) USD/week vs hold-to-bracket)
Share of cells with S > 0 by axis value and the best S (V0 fixed-point grid, ARM x MULT, max over W/PERS/newMae):
- arm: 15.0: 30% pos, max +1020; 20.0: 30% pos, max +1377; 25.0: 30% pos, max +1338; 30.0: 30% pos, max +1222; 35.0: 30% pos, max +805; 40.0: 20% pos, max +1714; 45.0: 20% pos, max +1509; 50.0: 20% pos, max +615
- mult: 5.0: 0% pos, max +1714; 10.0: 10% pos, max +770; 20.0: 10% pos, max +956; 30.0: 20% pos, max +1020; 60.0: 40% pos, max +1377; 100.0: 50% pos, max +214; 200.0: 40% pos, max +85
- win: 2.0: 20% pos, max +1714; 3.0: 20% pos, max +1020; 5.0: 30% pos, max +1006; 10.0: 30% pos, max +867; 15.0: 20% pos, max +1377
- pers: 1.0: 30% pos, max +935; 2.0: 30% pos, max +1020; 3.0: 20% pos, max +1509; 5.0: 20% pos, max +1714; 10.0: 20% pos, max +1377
- newmae: 0.0: 30% pos, max +1714; 1.0: 20% pos, max +1509
- var: 0: 30% pos, max +1714; 1: 20% pos, max +1008; 2: 30% pos, max +1377

| ARM \ MULT | 5.0 | 10.0 | 20.0 | 30.0 | 60.0 | 100.0 | 200.0 |
|---|---|---|---|---|---|---|---|
| 15.0 | -55 | +192 | +552 | +567 | +933 | +158 | +85 |
| 20.0 | +37 | +247 | +735 | +981 | +1041 | +214 | +49 |
| 25.0 | +450 | +390 | +824 | +614 | +668 | +189 | +49 |
| 30.0 | +52 | +678 | +521 | +535 | +1221 | +119 | +19 |
| 35.0 | +7 | +406 | +799 | +415 | +715 | +129 | +19 |
| 40.0 | +1714 | +184 | +631 | +301 | +452 | +193 | +0 |
| 45.0 | +1509 | +673 | +591 | +315 | +473 | +100 | +0 |
| 50.0 | +184 | +259 | +295 | +268 | +615 | +15 | +0 |

## 5. Nulls and walk-forward
- Placebo (random exit among seconds with -unreal >= the arm, same fired trades, 1,000 draws): COMB S_obs = +250, placebo mean -2575, p95 -2253, p = 0.001.
- Family max-stat (200 worlds; each world shifts pulled/age blocks within each trade, re-selects the best cell per book from 8,400): combined observed best-cell S sum +3365 vs world mean +8450, p95 +9611, p = 1.000; per book p: K7 1.000, P7 1.000, M7 1.000, U7 1.000, A7 1.000, H7 0.985, O7 0.975.
- Purged walk-forward by month (2024-01..2026-10, 7-day purge, training = weeks before the cut; simplified key without drawdown-first, older-window sign standing in for PRE/X'), delta vs hold-to-bracket USD/week:
| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| per-book procedure (recents key) | total -384272 | -3251 | -2487 | -2579 | +1191 | -1732 | +4948 | -2318 | -107 |
| uniform cell chosen by the same key | total -84414 | +17576 | +1941 | +110 | +864 | -1006 | +1543 | -773 | +559 |
| per-book, all-history mean key | total -505932 | +5704 | +5870 | +3203 | +1203 | -1486 | +113 | -4129 | +274 |
| per-book, all-history key, V0 only | total -402775 | +8030 | -2177 | -2257 | -1899 | -272 | +406 | -3864 | +184 |
| live cell (fixed) | total -99685 | +2295 | -902 | -1925 | +500 | +441 | +4917 | -747 | +0 |
Out-of-sample the per-book procedure loses to the fixed live cell on the totals; the in-sample per-book gains are selection effects of choosing among 8,400 cells per book on 13- and 26-week recents.

## 6. Stage 2 (replica engine cascade, re-entries/locks included; per-second state rule, exit at s+1 with 0.80 pt)
Reference rows: engine never-cut run (hist/A2 trades_nocut) and engine live-cut HOLD run; USD/week net of the 4.84 fee proxy, carrying week dropped. Months run per row in the count column.
| row | months | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|
| COMB per-book policy vs engine never-cut | 43 | +12301 | +11780 | +10145 | +9975 | +7031 | +914 | +2142 | +973 |
| best uniform cell vs engine never-cut | 43 | +1194 | -204 | -1877 | -848 | +372 | +3402 | +1082 | +136 |
| live cell 30/30/5/1/mae vs engine never-cut | 43 | -54 | -1585 | -1365 | +354 | +427 | +3844 | +653 | +77 |
| COMB per-book policy vs engine live-cut HOLD | 43 | +2830 | +1247 | +7270 | +7179 | +4360 | -7369 | +8047 | -3294 |
| best uniform cell vs engine live-cut HOLD | 43 | -8277 | -3075 | -3430 | -3325 | -3959 | -4882 | +5785 | -3357 |
| live cell 30/30/5/1/mae vs engine live-cut HOLD | 43 | -9525 | -1405 | -1135 | -3442 | -2314 | +114 | +4522 | -3503 |
| engine never-cut level (weekly net) | | -6820 | +17939 | +9740 | +15529 | +12323 | +7725 | +11743 | +1353 |
| engine live-cut HOLD level (weekly net) | | +2651 | +19061 | +11111 | +18098 | +14471 | +13335 | +6404 | +3990 |

## 7. Live week held-out (187 live trades, entries/lots/actual exits from the frozen live file; first-order; cut decisions on the state arrays; bracket proxy = actual exit time)
Actual live net P&L +104095 USD with 92 live cut exits. Delta = state-cut result minus the actual exit, USD at live lots (negative = the actual live exit was better).
| policy | cuts fired | delta USD | by book (cuts / delta) |
|---|---|---|---|
| COMB | 24 | -32043 | A7 2 / +256; H7 1 / +82; K7 12 / +1501; M7 3 / -2271; P7 5 / -31852; U7 1 / +243 |
| PERBOOK | 20 | -223 | A7 2 / +256; K7 12 / +1501; M7 3 / -2271; P7 2 / +49; U7 1 / +243 |
| UNIF | 14 | +1389 | A7 2 / -1792; K7 5 / +550; M7 4 / +1060; P7 3 / +1570 |
| LIVE | 10 | -15708 | A7 3 / +235; K7 2 / +841; M7 3 / -3419; P7 2 / -13364 |

## 8. P7 (7-lot arm, Test 2)
- sess0: ntr 2507, live cell total -13188; best cell 50/5x/3s/p3/mae/V1: L6M +5091, PRE +645, total +189216 (flags {'recent': True, 'tolerant': True, 'ddfirst': True, 'sign': 2, 'score': 4850.0})
- sess1: ntr 1958, live cell total +8632; best cell 30/30x/10s/p5/mae/V1: L6M +5113, PRE +383, total +73588 (flags {'recent': True, 'tolerant': True, 'ddfirst': True, 'sign': 2, 'score': 5100.0})
- sess3: ntr 1551, live cell total -22485; best cell 35/30x/10s/p3/mae/V2: L6M +2427, PRE +7, total +25810 (flags {'recent': True, 'tolerant': True, 'ddfirst': True, 'sign': 2, 'score': 2450.0})
- lots<=4: ntr 4087, live cell total +21676; best cell 25/30x/10s/p10/nomae/V1: L6M +4332, PRE +51, total +44910 (flags {'recent': True, 'tolerant': True, 'ddfirst': True, 'sign': 2, 'score': 4350.0})
- lots>4: ntr 1929, live cell total -48718; best cell 35/10x/5s/p2/mae/V2: L6M +3829, PRE +208, total -278 (flags {'recent': True, 'tolerant': True, 'ddfirst': True, 'sign': 2, 'score': 3850.0})
P7 slices (ARM 30, W 5, newMae on; var/persistence/MULT): v0_p1_m30 L6M +1101 PRE +139 tot -27042; v0_p1_m100 L6M +0 PRE +22 tot -7415; v0_p3_m30 L6M +748 PRE -85 tot +4029; v0_p3_m100 L6M +0 PRE +21 tot -7418; v0_p5_m30 L6M +168 PRE +136 tot +11904; v0_p5_m100 L6M +0 PRE +0 tot -11927; v0_p10_m30 L6M +0 PRE +0 tot +0; v0_p10_m100 L6M +0 PRE +0 tot +0; v1_p1_m30 L6M +1559 PRE -239 tot -60231; v1_p1_m100 L6M +65 PRE +40 tot +1862; v1_p3_m30 L6M +1231 PRE +132 tot +11766; v1_p3_m100 L6M +65 PRE +21 tot -2158; v1_p5_m30 L6M +235 PRE +130 tot +21122; v1_p5_m100 L6M +65 PRE +0 tot -6175; v1_p10_m30 L6M +0 PRE +0 tot +0; v1_p10_m100 L6M +0 PRE +0 tot +0; v2_p1_m30 L6M +161 PRE -212 tot -5082; v2_p1_m100 L6M +0 PRE +22 tot +4063; v2_p3_m30 L6M +634 PRE +118 tot -7589; v2_p3_m100 L6M +0 PRE +21 tot +1302; v2_p5_m30 L6M +187 PRE +63 tot +12328; v2_p5_m100 L6M +0 PRE +0 tot -2786; v2_p10_m30 L6M +0 PRE +0 tot +0; v2_p10_m100 L6M +0 PRE +0 tot +0
