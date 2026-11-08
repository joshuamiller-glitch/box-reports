# DS3_TH_STATE_A - program A (L2 loss, remaining families: A2 book-flip triggers, A4 post-cut blackout, A5 lot-scaled arms beyond the grid, A6 sustained-cut cells, A7 HM path rule) on the S1-COMB base

**Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched; the per-book COMB procedure fails the out-of-sample walk-forward (DS3_TH_STATE.md section 5) so S1-COMB is an in-sample base**

Prereg: autopilot/DS3_TH_STATE_AB_PREREG.md (sha256 4e5836fb... logged in DECISIONS.md before any candidate result; two later addenda, section 9). Selection data: label days 2023-04-01..2026-10-31; the live week 2026-11-01..11-05 is held out (180 of the 187 live trades are D7-book trades with a day file; the 7 X-book trades are outside the seven S1 books). Old DS3_TH_REDO_*.md pages stay VOID and are not edited.

## 1. Verdict

**No cell of program A ENTERS vs S1-COMB.** Every per-book best rule below fails at least one gate (column "failed gates"); the S1-COMB cell stays the live cell of this base for every book.
LEAD (positive S with recents, tolerant gate and drawdown first, but a null or the walk-forward fails -> best-of-F, not a rule): K7 A4 A4_N15_both, P7 A4 A4_N15_same, P7 A6 A6a_D2_X20, U7 A5 A5_a25_g+0.25.

Every cell is scored per book on the S1-COMB trade list (21,067 trades, 43 months): the other books stay at their S1-COMB cell, so the stack delta of a book-cell is that book alone. Windows are USD/week of the delta vs S1-COMB with the carrying week dropped (windows >= 8 weeks), (MDE = 2.8 sd/sqrt(n)); S = min(L6M, PRE). Because S1-COMB is itself an in-sample best-of-8,400 cell per book, an improvement over it is a second-stage selection and every table is read with that in mind. first-order Tier S (world W0: hold-to-bracket proxy, re-entries/locks ignored) unless a row says ENGINE.

## 2. Reference rows (same base, same windows)

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| S1-COMB vs NEVER-CUT, engine (TH_STATE_BASE_S1.md section 4; = DS3_TH_STATE.md section 6) | +12301 (+17228) | +11780 (+13411) | +10145 (+13982) | +9975 (+10798) | +7031 (+7518) | +914 (+13193) | +2142 (+4192) | +973 (+2986) |
| S1-COMB vs NEVER-CUT, first-order W0 (this page; USD/week, (MDE)) | +18904 (+11979) | +11464 (+13415) | +13888 (+14962) | +7454 (+10893) | +2161 (+7612) | +7728 (+10164) | -736 (+4618) | +382 (+3437) |
| NEVER-CUT = 0 by definition; PLAIN6060 engine run | see section 8 |

NEVER-CUT and PLAIN6060 are reference rows only, never candidates. In the first-order world the NEVER-CUT row is the hold-to-bracket proxy; PLAIN6060 (no TH of any kind) differs from it only by the profit-side TH and is an engine run of BASE-S1 (section 8).

## 3. Families and exact definitions

Common: S1-COMB cell of the trade's unit c0 = (ARM0, MULT0, W0, PERS0, newMae0, var0) (TH_STATE_BASE_S1.md section 2); decision at the end of exchange second s, exit executes at s+1 at mid(s+1) -+ 0.80 pt, a bracket touch in (s, s+1] wins; unreal = side*(mid - entry).

* **A2 book-flip add-on** (24 cells = 4 features x 6 strength quantiles; persistence 1, arm 30): fire at the first second with -unreal >= 30 pt AND F >= thr; the earliest of {S1-COMB cut, flip} exits. Against side = ask for a long, bid for a short. imb: a(s) = opp5/(own5+opp5) over the top-5 sizes, F = a(s) - a(s-10) (the against share rose over 10 s = the book flipped against the position); ice: refill events on the against-side best level in the last 30 s (best price unchanged s-1->s, a print at that price, size up), thr = max(1, q); dlt: (aggressive volume against - with the position over the last 10 s)/MedLevel; swp: max over the last 3 s of the 1-s aggressive volume against the position / MedLevel. Thresholds = q-quantiles of F over all selection rows with -unreal >= 30 (feature distribution only): imb: q50 0, q70 0.04839, q80 0.08036, q90 0.1287, q95 0.1722, q99 0.2649; ice: q50 1, q70 1, q80 1, q90 1, q95 2, q99 3; dlt: q50 0, q70 1.179, q80 2.321, q90 5.107, q95 9.215, q99 24.61; swp: q50 0.4203, q70 0.9869, q80 1.605, q90 2.993, q95 5.064, q99 13.68.
* **A4 post-cut blackout** (10 cells per book = N in {0,5,15,30,60} min x {same-side, both-sides}; N=0 is S1-COMB): after a StateCut exit the book takes no signal (same side only / either side) for N min. First order: blocked trades removed sequentially (a removed trade cannot start a blackout), delta = -net of the removed trades, locks/re-entries ignored. **Finding: the S1 base has NO post-cut blackout** - the D7 v1.2 blackout (U7, 30 min, same side) is set only inside the old ThL2Cut branch, which the S1 base removes, so a live U7 blackout armed by the TH-L2-S cut is a feature of D7 v1.5 that the base does not model (row A_U7LIVE below).
* **A5 lot-scaled arm beyond the grid** (28 cells = ARM0 in {20,25,30,35,40,45,50} x gamma in {-1,-0.25,+0.25,+1}): arm = clip(ARM0 x (lots/4)^gamma, 15, 50) pt; MULT/W/PERS/newMae of the unit COMB cell unchanged (gamma = -0.5 / +0.5 are V1 / V2 of STATE-SCORE and are not repeated; its core axes ARM/MULT/window/persistence/newMae per book x session are not repeated either).
* **A6 sustained cut** (19 cells). A6a (15 = dwell D in {2,5,10,20,30} s x depth X in {20,30,40} pt): the S1-COMB condition (including its persistence) first fires at s0; the cut is CONFIRMED at the end of second s0+D only if -unreal >= X on every second s0..s0+D (exit at s0+D+1); if the price recovers above -X inside the dwell the cut is cancelled and the state machine resumes from s0+1 with the run reset. A6b (4, lots >= 2 only): floor(lots/2) lots are cut at the S1-COMB firing, the remainder is held to the bracket or cut at s0+Dh s (Dh in {10,30,60}) if -unreal >= 15 pt.
* **A7 HM path rule** (H7 only, 9 cells x ADDTO/ALONE): DS3_THL_HM_RETEST family L6_a{20,25,30}_r3_w{10,20,30} (eligibility = adverse excursion >= a pt, 3 of 3 of {4-pt adverse momentum over w s, no new adverse extreme for w s with recovery <= 4 pt, efficiency over w s < 0.35}, evaluated each second) on the H7 trades (H7 is the 5-min HM successor).

## 4. Best rule per book and family (all windows, nulls, walk-forward, live week)

Columns: USD/week delta vs S1-COMB, carrying week dropped; placebo p v1 (prereg-literal eligibility) / v2 (like-for-like: L1 rows within 6 pt of the adverse extreme; identical for A cells); family p = placebo-world max-stat over the whole program (36 worlds; A4: random-removal worlds), program cell family = A2+A5+A6+A7; walk-forward = purged monthly refit of the family procedure on the trailing 12 months (total USD 2024-01..2026-10; L6M/PRE of the out-of-sample series); live week = first-order delta on the 180 live trades.

| book | family | rule (cell) | tier | nfire | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | MDE L6M/PRE | placebo p v1/v2 | family p | walk-fwd (total; L6M/PRE) | live week | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7 | A2 | A2_swp_q99 | E3 | 3287 | -623 | -708 | -818 | -960 | -576 | +235 | -1128 | +395 | +1921/+1354 | 0.001/0.001 | 1.000 | -173707; -1417/-907 | +332 | no gain over S1-COMB |
| K7 | A4 | A4_N15_both | E1 | 678 | -622 | +91 | +53 | +496 | +468 | +946 | +294 | -69 | +1366/+542 | 0.002/0.002 | 0.030 | +27090; +429/+309 | n/a | LEAD (best-of-F) |
| K7 | A5 | A5_a25_g+0.25 | E2 | 853 | -374 | -924 | -790 | -2 | -409 | -454 | -203 | +175 | +1444/+697 | 0.001/0.001 | 1.000 | -35330; -1015/-299 | -730 | no gain over S1-COMB |
| K7 | A6 | A6b_Dh60 | E2 | 153 | -30 | -40 | +22 | -54 | -49 | -81 | -10 | -6 | +154/+42 | 0.869/0.869 | 0.973 | -20851; -37/-4 | +0 | no gain over S1-COMB |
| P7 | A2 | A2_dlt_q99 | E3 | 2215 | -6101 | +1174 | -3245 | -2429 | +663 | +1397 | -2051 | +441 | +7012/+3997 | 0.001/0.001 | 1.000 | -380172; -2765/-2258 | -6788 | no gain over S1-COMB |
| P7 | A4 | A4_N15_same | E1 | 151 | +805 | +578 | +420 | +296 | +182 | -807 | +331 | +107 | +3340/+1014 | 0.048/0.048 | 0.229 | -4118; -151/-208 | n/a | LEAD (best-of-F) |
| P7 | A5 | A5_a50_g-1.00 | E1 | 1687 | -5473 | -558 | +550 | +1948 | +2189 | +5832 | -1249 | +514 | +8324/+4656 | 0.001/0.001 | 0.027 | -35470; -4032/-116 | -6646 | no gain over S1-COMB |
| P7 | A6 | A6a_D2_X20 | E1 | 1979 | -118 | -160 | +8 | +134 | +181 | +345 | +157 | +20 | +481/+135 | 0.001/0.001 | 0.027 | +45343; -766/+77 | +700 | LEAD (best-of-F) |
| M7 | A2 | A2_ice_q95 | E4 | 1207 | +610 | +317 | +181 | +211 | +169 | -91 | -27 | +164 | +480/+635 | 0.001/0.001 | 0.027 | -31246; +109/-323 | +74 | no gain over S1-COMB |
| M7 | A4 | A4_N15_same | E1 | 273 | -97 | -173 | +48 | +619 | +363 | +412 | -86 | -17 | +1010/+306 | 0.518/0.518 | 0.985 | -30623; -114/-251 | n/a | no gain over S1-COMB |
| M7 | A5 | A5_a45_g+1.00 | E3 | 2470 | -646 | -1234 | -1231 | -552 | -338 | +216 | -589 | +35 | +2330/+1011 | 0.001/0.001 | 1.000 | +33070; -254/-557 | -2066 | no gain over S1-COMB |
| M7 | A6 | A6b_Dh10 | E2 | 373 | +22 | +21 | +20 | -8 | +12 | +56 | +10 | -5 | +60/+25 | 0.001/0.001 | 0.027 | +56740; -100/-120 | -425 | no gain over S1-COMB |
| U7 | A2 | A2_dlt_q99 | E1 | 585 | +1155 | +1301 | +992 | +696 | +1111 | +1335 | -238 | +646 | +2182/+1362 | 0.019/0.019 | 1.000 | -58672; -79/-593 | +0 | no gain over S1-COMB |
| U7 | A5 | A5_a25_g+0.25 | E1 | 32 | -1453 | +479 | +446 | +92 | +23 | +2 | +136 | +0 | +946/+174 | 0.001/0.001 | 0.027 | -25375; -447/-30 | +0 | LEAD (best-of-F) |
| U7 | A6 | A6b_Dh10 | E1 | 82 | +8 | +72 | +18 | +7 | -11 | +1 | -7 | +0 | +91/+16 | 0.085/0.085 | 0.135 | +2013; -88/+0 | +88 | no gain over S1-COMB |
| A7 | A2 | A2_ice_q99 | E1 | 156 | +0 | +17 | +12 | +35 | +56 | +21 | -81 | +84 | +53/+259 | 0.056/0.056 | 1.000 | -19711; +92/-173 | +0 | no gain over S1-COMB |
| A7 | A5 | A5_a30_g+0.25 | E1 | 69 | +461 | +310 | +390 | +346 | +125 | +69 | -3 | +15 | +359/+101 | 0.002/0.002 | 0.054 | -4068; -261/+0 | +53 | no gain over S1-COMB |
| A7 | A6 | A6a_D2_X20 | E2 | 101 | -6 | +4 | +8 | -4 | -1 | -2 | -2 | +1 | +19/+5 | 0.010/0.010 | 0.054 | -2134; -139/+0 | +52 | no gain over S1-COMB |
| H7 | A2 | A2_ice_q99 | E1 | 288 | -258 | -32 | +14 | +10 | +30 | +275 | -34 | +135 | +344/+526 | 0.015/0.015 | 0.514 | -55140; -251/+61 | +0 | no gain over S1-COMB |
| H7 | A4 | A4_N60_both | E2 | 31 | -239 | -149 | +174 | -108 | -44 | +0 | -42 | +0 | +460/+296 | 0.718/0.718 | 0.751 | +0; +0/+0 | n/a | no gain over S1-COMB |
| H7 | A5 | A5_a25_g+0.25 | E2 | 46 | -160 | -368 | -269 | +140 | -140 | -340 | +46 | +0 | +1108/+62 | 0.001/0.001 | 0.027 | -26476; -765/-148 | +0 | best-of-F |
| H7 | A6 | A6b_Dh30 | E2 | 142 | -34 | +1 | -69 | -129 | -82 | -324 | +2 | -5 | +176/+20 | 0.003/0.003 | 1.000 | -19675; +135/-7 | +0 | no gain over S1-COMB |
| H7 | A7 | A7_a30_w20_add | E2 | 376 | -690 | -859 | -413 | -24 | -170 | +166 | +102 | +543 | +1093/+607 | 1.000/0.003 | 0.324 | -70188; -1249/+31 | +0 | no gain over S1-COMB |
| O7 | A2 | A2_imb_q99 | E2 | 54 | +0 | +0 | +0 | +0 | +1 | +0 | +10 | -21 | +0/+18 | 0.998/0.998 | 1.000 | -4188; -80/+26 | +0 | no gain over S1-COMB |
| O7 | A5 | A5_a20_g+0.25 | E3 | 269 | +214 | +184 | +204 | +56 | -155 | -130 | -208 | +81 | +398/+293 | 0.073/0.073 | 1.000 | -9733; -97/-159 | +0 | no gain over S1-COMB |
| O7 | A6 | A6a_D2_X20 | E1 | 164 | +4 | +3 | +11 | +4 | +11 | +12 | -5 | +2 | +24/+14 | 0.931/0.931 | 1.000 | -1778; -27/-45 | +0 | no gain over S1-COMB |

## 5. Best rule per book of program A (policy lines)

| book | best family (tier, then S) | cell | tier | S = min(L6M, PRE) | L6M | PRE | verdict vs S1-COMB | failed gates | policy-file / parameter lines | grammar gaps |
|---|---|---|---|---|---|---|---|---|---|---|
| K7 | A4 | A4_N15_both | E1 | +294 | +496 | +294 | LEAD (best-of-F) | L6M/PRE not above MDE (+496>+1366, +294>+542) | `ThL2BlackoutMins=15; ThL2BlackoutBooks="K7"; ThL2BlackoutSameSideOnly=false` | per-book minutes and per-book same-side/both-sides flag (today one global ThL2BlackoutMins / SameSideOnly); the blackout must be armed by the TH-L2-S state cut exit (today only ThL2Cut sets it; the S1 base has no blackout at all) |
| P7 | A4 | A4_N15_same | E1 | +296 | +296 | +331 | LEAD (best-of-F) | L6M/PRE not above MDE (+296>+3340, +331>+1014); family p=0.229; walk-forward | `ThL2BlackoutMins=15; ThL2BlackoutBooks="P7"; ThL2BlackoutSameSideOnly=true` | per-book minutes and per-book same-side/both-sides flag (today one global ThL2BlackoutMins / SameSideOnly); the blackout must be armed by the TH-L2-S state cut exit (today only ThL2Cut sets it; the S1 base has no blackout at all) |
| M7 | A4 | A4_N15_same | E1 | -86 | +619 | -86 | no gain over S1-COMB | L6M/PRE not above MDE (+619>+1010, -86>+306); placebo p=0.518; family p=0.985; walk-forward | `KEEP the S1-COMB cell: no cell of this program improves it on min(L6M, PRE); best-of-family for the record: ThL2BlackoutMins=15; ThL2BlackoutBooks="M7"; ThL2BlackoutSameSideOnly=true` |  |
| U7 | A5 | A5_a25_g+0.25 | E1 | +92 | +92 | +136 | LEAD (best-of-F) | L6M/PRE not above MDE (+92>+946, +136>+174); walk-forward | `loss U7 * pct<=-clip(25*(lots/4)^+0.25,15,50)/60 pulled_mult>=60 cut   # COMB cell U7: ARM 30 MULT 60 W 15 PERS 5 newMae off var V2; PERS=5 W=15` | lots feature and an arithmetic expression in the pct threshold (lot-scaled arm); persist field (PERS=5); per-rule pulled window W=15 s |
| A7 | A5 | A5_a30_g+0.25 | E1 | -3 | +346 | -3 | no gain over S1-COMB | L6M/PRE not above MDE (+346>+359, -3>+101); walk-forward | `KEEP the S1-COMB cell: no cell of this program improves it on min(L6M, PRE); best-of-family for the record: loss A7 * pct<=-clip(30*(lots/4)^+0.25,15,50)/60 pulled_mult>=60 cut   # COMB cell A7: ARM 30 MULT 60 W 15 PERS 3 newMae off var V0; PERS=3 W=15` |  |
| H7 | A2 | A2_ice_q99 | E1 | -34 | +10 | -34 | no gain over S1-COMB | L6M/PRE not above MDE (+10>+344, -34>+526); family p=0.514; walk-forward | `KEEP the S1-COMB cell: no cell of this program improves it on min(L6M, PRE); best-of-family for the record: loss H7 * pct<=-0.2500 pulled_mult>=30 secs_ext<=10 cut; loss H7 * pct<=-0.5000 ice_against>=3 cut   # A2 add-on (earliest of the two lines)` |  |
| O7 | A6 | A6a_D2_X20 | E1 | -5 | +4 | -5 | no gain over S1-COMB | L6M/PRE not above MDE (+4>+24, -5>+14); placebo p=0.931; family p=1.000; walk-forward | `KEEP the S1-COMB cell: no cell of this program improves it on min(L6M, PRE); best-of-family for the record: loss O7 * pct<=-0.6250 pulled_mult>=20 cut  confirm 2 s while pct<=-0.3333   # COMB cell O7: ARM 25 MULT 20 W 10 PERS 10 newMae off var V0; PERS=10 W=10` |  |


Fields/grammar the D7 policy file lacks for these rules (all books): persist field (condition true for N consecutive seconds); per-rule pulled window (today one global ThL2PulledSecs); scale 0.5 action in the loss grammar; lots feature (lot-scaled arm); entry-session scope (D7 `session` matches the CURRENT session, the scored scope is the ENTRY session); per-book blackout minutes / same-side flag; per-book L1 windows and evaluation frequency; ALONE mode per book (state cut off, path on).

### 5a. A4 blackout, every cell

| book | cell | removed trades | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | MDE L6M/PRE | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7 | A4_N5_same | 46 | +539 | +297 | +167 | +49 | +113 | +109 | +33 | +0 | +437/+146 | E4 |
| K7 | A4_N15_same | 208 | +417 | -1 | +93 | +331 | +222 | +598 | +34 | -84 | +734/+317 | E4 |
| K7 | A4_N30_same | 399 | +63 | -215 | +393 | +599 | +28 | +35 | +113 | -105 | +1086/+458 | E4 |
| K7 | A4_N60_same | 604 | +838 | +7 | +45 | +501 | +398 | +469 | +297 | -160 | +1266/+526 | E4 |
| K7 | A4_N5_both | 307 | -345 | +913 | +808 | +740 | +592 | +152 | +100 | +101 | +1250/+463 | E1 |
| K7 | A4_N15_both | 678 | -622 | +91 | +53 | +496 | +468 | +946 | +294 | -69 | +1366/+542 | E1 |
| K7 | A4_N30_both | 1005 | -1845 | -548 | +115 | +1017 | +197 | +117 | +338 | -132 | +2073/+715 | E4 |
| K7 | A4_N60_both | 1388 | -573 | +262 | +478 | -148 | +146 | +624 | +469 | -203 | +2177/+825 | E2 |
| P7 | A4_N5_same | 32 | +831 | +0 | -298 | -209 | -187 | +0 | +84 | +0 | +1810/+343 | E2 |
| P7 | A4_N15_same | 151 | +805 | +578 | +420 | +296 | +182 | -807 | +331 | +107 | +3340/+1014 | E1 |
| P7 | A4_N30_same | 336 | +3471 | +1168 | +1641 | +1953 | +1355 | +1853 | +66 | +523 | +4620/+1505 | E4 |
| P7 | A4_N60_same | 512 | -393 | -232 | -782 | +114 | -721 | +281 | -467 | +673 | +5757/+1837 | E4 |
| P7 | A4_N5_both | 83 | -365 | +9 | -292 | -537 | +242 | +817 | +74 | +55 | +1874/+983 | E2 |
| P7 | A4_N15_both | 440 | -1878 | -2078 | -3413 | -1356 | -553 | +376 | +763 | -517 | +4506/+2491 | E4 |
| P7 | A4_N30_both | 877 | +3589 | +1814 | -2052 | -151 | +1103 | -3152 | +631 | -1586 | +6718/+3333 | E4 |
| P7 | A4_N60_both | 1275 | +1009 | -2655 | +649 | -224 | -2763 | -6930 | -245 | -1871 | +6975/+4148 | E4 |
| M7 | A4_N5_same | 119 | +185 | -126 | +9 | +119 | +210 | +288 | +12 | +0 | +707/+182 | E4 |
| M7 | A4_N15_same | 273 | -97 | -173 | +48 | +619 | +363 | +412 | -86 | -17 | +1010/+306 | E1 |
| M7 | A4_N30_same | 479 | -490 | -340 | -443 | -292 | +75 | +102 | -215 | -162 | +1449/+535 | E4 |
| M7 | A4_N60_same | 718 | +174 | +162 | -441 | -96 | +587 | +1593 | -74 | -62 | +1965/+563 | E4 |
| M7 | A4_N5_both | 301 | +375 | -66 | -196 | +77 | +70 | -96 | -132 | -73 | +895/+450 | E4 |
| M7 | A4_N15_both | 575 | +382 | +655 | +197 | +833 | +404 | -392 | -28 | -130 | +1019/+594 | E4 |
| M7 | A4_N30_both | 876 | -21 | +390 | -260 | +712 | +162 | -1048 | -246 | +5 | +1482/+629 | E4 |
| M7 | A4_N60_both | 1268 | +694 | +966 | +861 | +897 | +388 | +762 | -306 | +15 | +1912/+804 | E1 |
| U7 | A4_N5_both | 4 | +0 | +0 | +0 | +0 | +0 | +0 | -0 | +0 | +0/+128 | E5 |
| U7 | A4_N15_both | 7 | +0 | +0 | +0 | +0 | +0 | +0 | -49 | +0 | +0/+186 | E5 |
| U7 | A4_N30_both | 9 | +0 | +0 | -100 | +22 | +11 | +0 | -49 | +0 | +241/+186 | E5 |
| U7 | A4_N60_both | 14 | +0 | +217 | +45 | -266 | -224 | +0 | -97 | +0 | +640/+229 | E5 |
| A7 | A4_N5_same | 2 | +0 | +0 | +0 | +0 | +0 | +0 | +0 | +0 | +0/+0 | E5 |
| A7 | A4_N15_same | 8 | +287 | +86 | +57 | +123 | +37 | +0 | +0 | +0 | +163/+0 | E5 |
| A7 | A4_N30_same | 13 | +287 | +86 | +120 | +163 | +56 | +0 | +0 | +0 | +231/+0 | E5 |
| A7 | A4_N60_same | 21 | +661 | +171 | +213 | +268 | +108 | +0 | +0 | +0 | +382/+0 | E5 |
| A7 | A4_N5_both | 2 | +0 | +0 | +0 | +0 | +0 | +0 | +0 | +0 | +0/+0 | E5 |
| A7 | A4_N15_both | 9 | +287 | +86 | +120 | +172 | +61 | +0 | +0 | +0 | +202/+0 | E5 |
| A7 | A4_N30_both | 17 | +287 | +180 | +174 | +189 | +69 | +0 | +0 | +0 | +305/+0 | E5 |
| A7 | A4_N60_both | 29 | +848 | +93 | +316 | +366 | +133 | +0 | +0 | +0 | +444/+0 | E5 |
| H7 | A4_N30_same | 1 | +0 | +0 | +0 | +0 | +0 | +0 | +0 | +0 | +0/+0 | E5 |
| H7 | A4_N60_same | 15 | -239 | -149 | +75 | +36 | -29 | +0 | -39 | +0 | +217/+226 | E5 |
| H7 | A4_N5_both | 1 | +0 | +0 | +0 | +0 | +0 | +0 | +0 | +0 | +0/+0 | E5 |
| H7 | A4_N15_both | 6 | +0 | +0 | +0 | +85 | +42 | +0 | +25 | +0 | +237/+50 | E5 |
| H7 | A4_N30_both | 12 | +0 | +0 | +0 | +85 | +97 | +0 | +44 | +0 | +237/+133 | E5 |
| H7 | A4_N60_both | 31 | -239 | -149 | +174 | -108 | -44 | +0 | -42 | +0 | +460/+296 | E2 |


### 5b. Heat of the other A families (per book)

**A2**

| book | A2 |
|---|---|
| K7 | cells with nfire>=30: 24; S>0: 0; best S -472 (A2_ice_q99); median S -1263 |
| P7 | cells with nfire>=30: 24; S>0: 0; best S -1456 (A2_ice_q99); median S -6439 |
| M7 | cells with nfire>=30: 24; S>0: 0; best S -27 (A2_ice_q95); median S -481 |
| U7 | cells with nfire>=30: 24; S>0: 0; best S -238 (A2_dlt_q99); median S -864 |
| A7 | cells with nfire>=30: 24; S>0: 0; best S -81 (A2_ice_q99); median S -466 |
| H7 | cells with nfire>=30: 24; S>0: 1; best S +58 (A2_dlt_q99); median S -501 |
| O7 | cells with nfire>=30: 24; S>0: 1; best S +27 (A2_imb_q95); median S -55 |


**A5**

| book | A5 |
|---|---|
| K7 | cells with nfire>=30: 28; S>0: 0; best S -203 (A5_a25_g+0.25); median S -617 |
| P7 | cells with nfire>=30: 28; S>0: 0; best S -670 (A5_a50_g-0.25); median S -4769 |
| M7 | cells with nfire>=30: 28; S>0: 1; best S +27 (A5_a20_g-1.00); median S -479 |
| U7 | cells with nfire>=30: 27; S>0: 4; best S +132 (A5_a25_g-0.25); median S -213 |
| A7 | cells with nfire>=30: 25; S>0: 0; best S -3 (A5_a30_g+0.25); median S -248 |
| H7 | cells with nfire>=30: 28; S>0: 1; best S +46 (A5_a25_g+0.25); median S -765 |
| O7 | cells with nfire>=30: 28; S>0: 0; best S -38 (A5_a20_g-0.25); median S -122 |


**A6**

| book | A6 |
|---|---|
| K7 | cells with nfire>=30: 19; S>0: 1; best S +18 (A6a_D20_X20); median S -204 |
| P7 | cells with nfire>=30: 19; S>0: 5; best S +150 (A6a_D10_X20); median S -264 |
| M7 | cells with nfire>=30: 19; S>0: 1; best S +41 (A6a_D10_X40); median S -100 |
| U7 | cells with nfire>=30: 19; S>0: 0; best S -7 (A6b_Dh10); median S -145 |
| A7 | cells with nfire>=30: 15; S>0: 0; best S -4 (A6a_D10_X20); median S -109 |
| H7 | cells with nfire>=30: 19; S>0: 0; best S -129 (A6b_Dh30); median S -579 |
| O7 | cells with nfire>=30: 15; S>0: 0; best S -5 (A6a_D2_X20); median S -95 |


**A7**

| book | A7 |
|---|---|
| K7 | cells with nfire>=30: 0; S>0: 0; best S n/a (-); median S n/a |
| P7 | cells with nfire>=30: 0; S>0: 0; best S n/a (-); median S n/a |
| M7 | cells with nfire>=30: 0; S>0: 0; best S n/a (-); median S n/a |
| U7 | cells with nfire>=30: 0; S>0: 0; best S n/a (-); median S n/a |
| A7 | cells with nfire>=30: 0; S>0: 0; best S n/a (-); median S n/a |
| H7 | cells with nfire>=30: 18; S>0: 0; best S -24 (A7_a30_w20_add); median S -374 |
| O7 | cells with nfire>=30: 0; S>0: 0; best S n/a (-); median S n/a |


## 6. Finalist policies: first-order, live week, engine cascade

| policy | what | first-order stack delta vs S1-COMB (USD/week (MDE)): L1M / L2M / L3M / L6M / HOLD / MID / PRE / X' | live week (first-order, USD) | by book |
|---|---|---|---|---|
| A_BO | A4 blackout: K7 15 min both sides, P7 15 min same side | +182(+3674) / -49(+2471) / +551(+2813) / -365(+3585) / +134(+2415) / +736(+3459) / +236(+1135) / +84(+408) | +721 | K7 +721 |
| A_U7LIVE | U7 30 min same-side blackout armed by the state cut (the D7 v1.2 live rule, absent from the S1 base) | +0(+0) / +0(+0) / +0(+0) / +0(+0) / +0(+0) / +0(+0) / +0(+0) / +0(+0) | +0 |  |
| A_STACK | P7 dwell 2s/20pt (A6a) + U7, H7 lot-scaled arm 25x(lots/4)^0.25 (A5) + K7/P7/U7 blackouts (A4) | -1548(+7155) / +1526(+2290) / +2174(+3205) / -132(+4251) / +127(+2684) / +1584(+3833) / +463(+1156) / +37(+439) | +1421 | K7 +721, P7 +700 |


Engine cascade (replica engine, true fills, re-entries and locks included), policy vs the S1-COMB engine run on the same months, USD/week net of the 4.84 fee proxy, carrying week dropped, label day of the exit (STATE-SCORE stage-2 convention); (MDE):

| policy | what | months run | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M with/without | maxDD PRE with/without |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A_BO | A4 blackout: K7 15 min both sides, P7 15 min same side | 9 (202602..202610) | +720 (+7359) | +392 (+4944) | -712 (+4088) | -1172 (+5316) | +390 (+3243) | +68 (+4832) | n/a | n/a | +93162/+79709 | n/a |
| A_U7LIVE | U7 30 min same-side blackout armed by the state cut (the D7 v1.2 live rule, absent from the S1 base) | 8 (202603..202610) | +0 (+0) | +0 (+0) | -100 (+279) | +22 (+241) | +11 (+117) | +0 (+0) | n/a | n/a | +79709/+79709 | n/a |
| A_STACK | P7 dwell 2s/20pt (A6a) + U7, H7 lot-scaled arm 25x(lots/4)^0.25 (A5) + K7/P7/U7 blackouts (A4) | 8 (202603..202610) | -2543 (+9233) | +412 (+3284) | -210 (+3161) | -229 (+5711) | +113 (+3056) | -1143 (+5365) | n/a | n/a | +90066/+79709 | n/a |


## 7. ENTER verdict per finalist policy (vs S1-COMB, engine cascade)

| policy | engine L6M (MDE) | engine PRE (MDE) | above MDE on both | drawdown not worse L6M / PRE | live week (first-order, USD) | components ENTER | policy verdict |
|---|---|---|---|---|---|---|---|
| A_BO | -1172 (+5316) | +0 (+0) | no | worse / ok | +721 | no | NOT ENTER (not above MDE, drawdown, components fail nulls/walk-forward) |
| A_U7LIVE | +22 (+241) | +0 (+0) | no | ok / ok | +0 | no | NOT ENTER (not above MDE, components fail nulls/walk-forward) |
| A_STACK | -229 (+5711) | +0 (+0) | no | worse / ok | +1421 | no | NOT ENTER (not above MDE, drawdown, components fail nulls/walk-forward) |


A policy ENTERS only if every component rule ENTERS in section 4 (placebo v1+v2, family, walk-forward, live, above MDE) AND the engine cascade is above MDE on L6M and PRE, drawdown not worse and the live week is not negative. The X' window is absent from the engine rows (months 2023-04..2024-01 are not in the engine run; the first-order X' column in section 6 covers it).

## 8. PLAIN6060 and NEVER-CUT reference rows

PLAIN6060 (no TH of any kind) engine months available: 43 (202304..202610) of 43; windows without data show n/a.

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| S1-COMB vs PLAIN6060 (engine) | +12301 (+17228) | +11780 (+13411) | +10145 (+13982) | +9975 (+10798) | +7031 (+7518) | +914 (+13193) | +2142 (+4192) | +973 (+2986) |
| A_BO vs PLAIN6060 (engine, 9 months) | +13021 (+15442) | +11459 (+13377) | +13749 (+10666) | +9576 (+11658) | +6991 (+7120) | +8355 (+13144) | n/a | n/a |
| A_U7LIVE vs PLAIN6060 (engine, 8 months) | +12301 (+17228) | +11997 (+13026) | +10190 (+13752) | +9901 (+10648) | +5612 (+6242) | +414 (+12561) | n/a | n/a |
| A_STACK vs PLAIN6060 (engine, 8 months) | +9757 (+13397) | +10084 (+12290) | +8404 (+12560) | +10404 (+11230) | +6083 (+6656) | +6746 (+14192) | n/a | n/a |


NEVER-CUT engine rows exist only through the stage-2 comparison (S1-COMB vs never-cut, section 2); the S1 NOCUT base run was not started by BASE-S1 (0 months at the time of writing).

## 9. Method notes, deviations, caveats

* Tier S is first-order (world W0): each trade as if alone on its 1-s path to the bracket proxy; the engine rows in section 6 carry re-entries, locks, caps and true fills and are the cascade check. The W0 S1-COMB vs NEVER-CUT row differs from the engine row (section 2): first-order is a screening statistic, not an expected P&L.
* S1-COMB itself passes the engine regression exactly (an empty-spec rule reproduces the S1-COMB trade list of 2026-10 trade for trade).
* Addendum 1 (DECISIONS.md, before any family-null number was read): the first family null (signal circularly shifted inside each trade, 80 worlds) was discarded because it leaks look-ahead (the later rows of a losing trade carry its outcome; shifted TH_LIVE scored +600k vs -200k real on K7). It was replaced by the prereg-literal Westfall-Young placebo worlds (random exits of the same acting trades, shared uniforms, per-world maximum over the program's cells; 36 worlds). The same flaw very likely inflates the shifted-block family null of DS3_TH_STATE.md section 5 (null mean above the observed best cell); that page should be re-read with this in mind.
* Addendum 1b: the prereg-literal placebo eligibility for L1 cells (adverse extreme >= ThMinPoints, any later second) lets a random exit land after a rebound and is kinder than the rule; the like-for-like version v2 (rows within 6 pt of the adverse extreme) was added after the first placebo pass and both are reported; the gate requires both.
* Zero rows: a book whose best cell has S <= 0 keeps the S1-COMB cell; the best-of-family cell is shown for the record only.
* Dead ledger: dead_lookup found no prior match for any family before scoring (A2 flip, A4 blackout, A5 lot arm, A6 dwell, B1/B2 L1 cells); one row per family-book best is appended to DEAD_CELLS.csv after the run with program tags THS2_A / THS2_B (append only).
* Seal safety: manifest_after.json sha256 759f2258daac9d28 before and after (unchanged); private trees /mnt/l2/l2vast/_th_state/s2/; at most 2 replica processes.

## 10. Files and shas

  - aaa1a9f963c1d16b  s2_kern.py
  - 20d096cce0a18d0e  s2_common.py
  - 410455c36ebd066d  s2_fam.py
  - 0097f02e50c49ebb  s2_scan.py
  - ebf0b25681b60f24  s2_thr.py
  - 1ae4bed3152fe3b5  s2_stats.py
  - 8408998db9c490dd  s2_select.py
  - 4d94496b202f4401  s2_placebo.py
  - 911b3fada750e59b  s2_final.py
  - c38289af0ca6849f  s2_policy.py
  - 5bb893a7511d8780  s2_engine.py
  - dfa18c85e7126303  s2_eng_run.py
  - b30f6ce5adaee890  s2_eng_eval.py
  - b760fbd1a0e5f0a2  run_null.py
  - 2374849698951f78  run_world0.py
  - prereg DS3_TH_STATE_AB_PREREG.md sha256 4e5836fb6ba863ab3a7a682b1ff1c6457a09022af1aa071bb8f58da040563e26 (DECISIONS.md, before any candidate result)
  - data: /mnt/l2/l2vast/_th_state/s2/ (A/ tier S arrays, eng/ engine trade lists per policy and month, policies_v1.json)
