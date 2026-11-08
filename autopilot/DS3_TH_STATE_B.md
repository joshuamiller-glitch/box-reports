# DS3_TH_STATE_B - program B (L1 loss: B1 DS3 TH-loss grid alone and on top of the state cut, B2 THL_BOOKS cells, B3 stacks on the A finalists) on the S1-COMB base

**Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched; the per-book COMB procedure fails the out-of-sample walk-forward (DS3_TH_STATE.md section 5) so S1-COMB is an in-sample base**

Prereg: autopilot/DS3_TH_STATE_AB_PREREG.md (sha256 4e5836fb... logged in DECISIONS.md before any candidate result; two later addenda, section 9). Selection data: label days 2023-04-01..2026-10-31; the live week 2026-11-01..11-05 is held out (180 of the 187 live trades are D7-book trades with a day file; the 7 X-book trades are outside the seven S1 books). Old DS3_TH_REDO_*.md pages stay VOID and are not edited.

## 1. Verdict

**No cell of program B ENTERS vs S1-COMB.** Every per-book best rule below fails at least one gate (column "failed gates"); the S1-COMB cell stays the live cell of this base for every book.
LEAD (positive S with recents, tolerant gate and drawdown first, but a null or the walk-forward fails -> best-of-F, not a rule): K7 B1 B1_4127, K7 B1_alone B1a_7428, P7 B1 B1_12765, M7 B1 B1_7085, U7 B1 B1_7001, U7 B1_alone B1a_7409, A7 B1 B1_1909, H7 B1 B1_13517, O7 B1 B1_7430.

Every cell is scored per book on the S1-COMB trade list (21,067 trades, 43 months): the other books stay at their S1-COMB cell, so the stack delta of a book-cell is that book alone. Windows are USD/week of the delta vs S1-COMB with the carrying week dropped (windows >= 8 weeks), (MDE = 2.8 sd/sqrt(n)); S = min(L6M, PRE). Because S1-COMB is itself an in-sample best-of-8,400 cell per book, an improvement over it is a second-stage selection and every table is read with that in mind. first-order Tier S (world W0: hold-to-bracket proxy, re-entries/locks ignored) unless a row says ENGINE.

## 2. Reference rows (same base, same windows)

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| S1-COMB vs NEVER-CUT, engine (TH_STATE_BASE_S1.md section 4; = DS3_TH_STATE.md section 6) | +12301 (+17228) | +11780 (+13411) | +10145 (+13982) | +9975 (+10798) | +7031 (+7518) | +914 (+13193) | +2142 (+4192) | +973 (+2986) |
| S1-COMB vs NEVER-CUT, first-order W0 (this page; USD/week, (MDE)) | +18904 (+11979) | +11464 (+13415) | +13888 (+14962) | +7454 (+10893) | +2161 (+7612) | +7728 (+10164) | -736 (+4618) | +382 (+3437) |
| NEVER-CUT = 0 by definition; PLAIN6060 engine run | see section 8 |

NEVER-CUT and PLAIN6060 are reference rows only, never candidates. In the first-order world the NEVER-CUT row is the hold-to-bracket proxy; PLAIN6060 (no TH of any kind) differs from it only by the profit-side TH and is an engine run of BASE-S1 (section 8).

## 3. Families and exact definitions

Path features on the 1-s trade-print path (last price per second, forward-filled; the per-second low/high give the adverse extreme, DS7 AdvExt: strictly new extreme). Votes as DS7.cs ManageLoss / rules_replica._l1_loss: eligible once the adverse extreme >= ThMinPoints; evaluated at the first eligible second and then every `freq` s; momentum = price now worse than w s ago by >= pts; stall = adverse extreme >= st s old AND recovery from it <= pullback; efficiency = |net|/path over ew s < thr (path = mean of the 1-s last-price path and the minimal first/low/high/last path inside each second; validated against the engine's own eff30/eff60 rows, correlation .80/.88, bias +-0.03). Fire when votes >= min(ThRequired, 3). Fire at s -> exit at s+1, mid -+ 0.80 (the engine re-runs use the engine's own request_exit latency path).

* **B1** 14,580 cells = ThMin {10,15,20,30,40} x ThRequired {2,3,4} x momentum (window {15,30,60} s x points {3,5,8}) x stall (seconds {30,60,90} x pullback {2,4,6}) x efficiency (window {30,60,120} x threshold {.30,.40}) x frequency {1,10} s, per book, two modes: **AddToPath** (state cut kept, earliest exit wins; D7 `ThL2Mode=AddToPath`) and **path-only** (state cut off, path on = the prereg ALONE; D7 `ReplacePath` means the opposite: path off, L2 on = the S1-COMB row).
* **B2** the 8 of 18 mappable THL_BOOKS cells (KB->K7, SM->U7, PE->P7, MV->M7 x {TH_LIVE: 15 pt, 3 of 3, 30 s windows (4 pt, 30 s stall/4 pt, eff .35); MAE15: 15 pt, 0 votes}); MA and DN have no D7 book, the 6 TIME_ONLY cells are placebos (the placebo machinery, not cells).
* **B3** the best B1 cells (AddToPath) stacked on the A finalist policy A_STACK (policy B3_ADD_ON_ASTACK); ReplacePath (path off) = the A policy alone.

## 4. Best rule per book and family (all windows, nulls, walk-forward, live week)

Columns: USD/week delta vs S1-COMB, carrying week dropped; placebo p v1 (prereg-literal eligibility) / v2 (like-for-like: L1 rows within 6 pt of the adverse extreme; identical for A cells); family p = placebo-world max-stat over the whole program (36 worlds; A4: random-removal worlds), program cell family = B1+B1_alone+B2; walk-forward = purged monthly refit of the family procedure on the trailing 12 months (total USD 2024-01..2026-10; L6M/PRE of the out-of-sample series); live week = first-order delta on the 180 live trades.

| book | family | rule (cell) | tier | nfire | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | MDE L6M/PRE | placebo p v1/v2 | family p | walk-fwd (total; L6M/PRE) | live week | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7 | B1 | B1_4127 | E1 | 959 | +708 | -131 | +384 | +478 | -192 | -506 | +174 | +155 | +1087/+710 | 1.000/0.128 | 1.000 | -51282; -284/-172 | -2111 | LEAD (best-of-F) |
| K7 | B1_alone | B1a_7428 | E1 | 2815 | -750 | -253 | +566 | +353 | +293 | +148 | +207 | +596 | +2651/+1299 | 1.000/0.001 | 0.946 | -1409; -289/-70 | -2920 | LEAD (best-of-F) |
| K7 | B2 | B2_K7_TH_LIVE_add | E3 | 4412 | -706 | +376 | -287 | -863 | -977 | -1425 | -1322 | +330 | +2923/+1794 | 1.000/0.001 | 1.000 | -247100; -897/-1337 | -4254 | no gain over S1-COMB |
| P7 | B1 | B1_12765 | E1 | 631 | +3446 | +2680 | +3031 | +1751 | +899 | +1903 | +875 | +445 | +2184/+1093 | 1.000/0.950 | 1.000 | -327764; +88/-2861 | +0 | LEAD (best-of-F) |
| P7 | B1_alone | B1a_13356 | E1 | 2374 | -7793 | +5349 | +4141 | +629 | +1570 | +4421 | -463 | +653 | +7043/+3492 | 1.000/0.001 | 1.000 | -115733; -1268/-1871 | +18434 | no gain over S1-COMB |
| P7 | B2 | B2_P7_TH_LIVE_alone | E3 | 3498 | -15418 | -2053 | -2496 | -6343 | -5371 | -9843 | -6023 | +1964 | +11596/+7430 | 1.000/0.001 | 1.000 | -1006994; -6343/-6483 | -37191 | no gain over S1-COMB |
| M7 | B1 | B1_7085 | E1 | 522 | +323 | +394 | +832 | +725 | +294 | +236 | +192 | +232 | +830/+331 | 1.000/0.007 | 0.135 | -110830; -895/-941 | -276 | LEAD (best-of-F) |
| M7 | B1_alone | B1a_13337 | E4 | 2392 | -2516 | -1969 | -1960 | +160 | +372 | -1785 | +122 | +245 | +2955/+852 | 1.000/0.001 | 1.000 | +45939; -125/-617 | +2271 | best-of-F |
| M7 | B2 | B2_M7_TH_LIVE_alone | E3 | 3166 | -472 | +162 | +186 | -337 | -291 | -1476 | -1211 | +304 | +2160/+1452 | 1.000/0.001 | 1.000 | -155346; -281/-1303 | -1934 | no gain over S1-COMB |
| U7 | B1 | B1_7001 | E1 | 357 | +1203 | +1271 | +810 | +717 | +1178 | +2697 | +568 | +353 | +2117/+1048 | 1.000/0.001 | 0.162 | -17851; -81/-48 | +0 | LEAD (best-of-F) |
| U7 | B1_alone | B1a_7409 | E1 | 386 | +3319 | +2108 | +1338 | +597 | +1210 | +1687 | +266 | +924 | +3039/+911 | 1.000/0.004 | 1.000 | -84218; -2365/-397 | -243 | LEAD (best-of-F) |
| U7 | B2 | B2_U7_TH_LIVE_add | E2 | 855 | -764 | -1045 | -393 | -11 | +253 | -965 | -932 | -220 | +3656/+2076 | 1.000/0.001 | 1.000 | -138376; -11/-1290 | +2955 | no gain over S1-COMB |
| A7 | B1 | B1_1909 | E1 | 170 | +362 | +159 | +607 | +111 | -14 | +248 | +105 | +101 | +677/+213 | 1.000/0.047 | 0.405 | -22386; +273/-198 | +0 | LEAD (best-of-F) |
| A7 | B1_alone | B1a_7297 | E1 | 414 | -1042 | +551 | +467 | +192 | -161 | -24 | -70 | +157 | +760/+315 | 0.421/0.010 | 1.000 | -37908; -338/-204 | +480 | no gain over S1-COMB |
| H7 | B1 | B1_13517 | E1 | 149 | +115 | +145 | +97 | +193 | +125 | +72 | +196 | +124 | +174/+125 | 0.950/0.552 | 1.000 | -41672; -1166/+140 | +0 | LEAD (best-of-F) |
| H7 | B1_alone | B1a_1417 | E2 | 534 | -2521 | -157 | -22 | -113 | -51 | -176 | +58 | +106 | +1899/+858 | 1.000/0.005 | 1.000 | -45924; -1354/+144 | +670 | no gain over S1-COMB |
| O7 | B1 | B1_7430 | E1 | 103 | +44 | +29 | +46 | +44 | +3 | +37 | +31 | +41 | +58/+128 | 1.000/0.099 | 0.676 | -11117; +154/-123 | +0 | LEAD (best-of-F) |
| O7 | B1_alone | B1a_4108 | E4 | 220 | +105 | -35 | -7 | +48 | -6 | -161 | +42 | -1 | +104/+196 | 1.000/0.991 | 0.270 | -15939; +31/-193 | +0 | best-of-F |

## 5. Best rule per book of program B (policy lines)

| book | best family (tier, then S) | cell | tier | S = min(L6M, PRE) | L6M | PRE | verdict vs S1-COMB | failed gates | policy-file / parameter lines | grammar gaps |
|---|---|---|---|---|---|---|---|---|---|---|
| K7 | B1_alone | B1a_7428 | E1 | +207 | +353 | +207 | LEAD (best-of-F) | L6M/PRE not above MDE (+353>+2651, +207>+1299); placebo p=1.000; family p=0.946; walk-forward; live week -2920 | `K7ThOn=true; K7ThMinPoints=20; K7ThRequired=3; ThMomentumWindowSecs=30; ThMomentumPoints=8; ThStallSeconds=90; ThPullbackPoints=4; ThEfficiencyWindowSecs=30; ThEfficiencyThreshold=0.3; ThEvalFrequencySecs=1; path only: state cut OFF for the book, path TH on (no per-book mode; ReplacePath turns the PATH off)` | per-book (not shared) momentum/stall/efficiency windows and points; none beyond the per-book windows; ALONE mode (L2 off, path on) per book |
| P7 | B1 | B1_12765 | E1 | +875 | +1751 | +875 | LEAD (best-of-F) | L6M/PRE not above MDE (+1751>+2184, +875>+1093); placebo p=1.000; family p=1.000; walk-forward | `P7ThOn=true; P7ThMinPoints=40; P7ThRequired=3; ThMomentumWindowSecs=15; ThMomentumPoints=5; ThStallSeconds=30; ThPullbackPoints=4; ThEfficiencyWindowSecs=120; ThEfficiencyThreshold=0.3; ThEvalFrequencySecs=10; ThL2Mode=AddToPath (state cut kept, earliest wins)` | per-book (not shared) momentum/stall/efficiency windows and points; ThEvalFrequencySecs per book; ALONE mode (L2 off, path on) per book |
| M7 | B1 | B1_7085 | E1 | +192 | +725 | +192 | LEAD (best-of-F) | L6M/PRE not above MDE (+725>+830, +192>+331); placebo p=1.000; family p=0.135; walk-forward; live week -276 | `M7ThOn=true; M7ThMinPoints=20; M7ThRequired=3; ThMomentumWindowSecs=15; ThMomentumPoints=8; ThStallSeconds=60; ThPullbackPoints=6; ThEfficiencyWindowSecs=60; ThEfficiencyThreshold=0.3; ThEvalFrequencySecs=10; ThL2Mode=AddToPath (state cut kept, earliest wins)` | per-book (not shared) momentum/stall/efficiency windows and points; ThEvalFrequencySecs per book; ALONE mode (L2 off, path on) per book |
| U7 | B1 | B1_7001 | E1 | +568 | +717 | +568 | LEAD (best-of-F) | L6M/PRE not above MDE (+717>+2117, +568>+1048); placebo p=1.000; family p=0.162; walk-forward | `U7ThOn=true; U7ThMinPoints=20; U7ThRequired=3; ThMomentumWindowSecs=15; ThMomentumPoints=5; ThStallSeconds=90; ThPullbackPoints=4; ThEfficiencyWindowSecs=60; ThEfficiencyThreshold=0.3; ThEvalFrequencySecs=10; ThL2Mode=AddToPath (state cut kept, earliest wins)` | per-book (not shared) momentum/stall/efficiency windows and points; ThEvalFrequencySecs per book; ALONE mode (L2 off, path on) per book |
| A7 | B1 | B1_1909 | E1 | +105 | +111 | +105 | LEAD (best-of-F) | L6M/PRE not above MDE (+111>+677, +105>+213); placebo p=1.000; family p=0.405; walk-forward | `A7ThOn=true; A7ThMinPoints=10; A7ThRequired=3; ThMomentumWindowSecs=60; ThMomentumPoints=8; ThStallSeconds=90; ThPullbackPoints=2; ThEfficiencyWindowSecs=30; ThEfficiencyThreshold=0.3; ThEvalFrequencySecs=10; ThL2Mode=AddToPath (state cut kept, earliest wins)` | per-book (not shared) momentum/stall/efficiency windows and points; ThEvalFrequencySecs per book; ALONE mode (L2 off, path on) per book |
| H7 | B1 | B1_13517 | E1 | +193 | +193 | +196 | LEAD (best-of-F) | placebo p=0.950; family p=1.000; walk-forward | `H7ThOn=true; H7ThMinPoints=40; H7ThRequired=3; ThMomentumWindowSecs=60; ThMomentumPoints=8; ThStallSeconds=30; ThPullbackPoints=4; ThEfficiencyWindowSecs=60; ThEfficiencyThreshold=0.3; ThEvalFrequencySecs=10; ThL2Mode=AddToPath (state cut kept, earliest wins)` | per-book (not shared) momentum/stall/efficiency windows and points; ThEvalFrequencySecs per book; ALONE mode (L2 off, path on) per book |
| O7 | B1 | B1_7430 | E1 | +31 | +44 | +31 | LEAD (best-of-F) | L6M/PRE not above MDE (+44>+58, +31>+128); placebo p=1.000; family p=0.676; walk-forward | `O7ThOn=true; O7ThMinPoints=20; O7ThRequired=3; ThMomentumWindowSecs=30; ThMomentumPoints=8; ThStallSeconds=90; ThPullbackPoints=4; ThEfficiencyWindowSecs=30; ThEfficiencyThreshold=0.4; ThEvalFrequencySecs=1; ThL2Mode=AddToPath (state cut kept, earliest wins)` | per-book (not shared) momentum/stall/efficiency windows and points; none beyond the per-book windows; ALONE mode (L2 off, path on) per book |


Fields/grammar the D7 policy file lacks for these rules (all books): persist field (condition true for N consecutive seconds); per-rule pulled window (today one global ThL2PulledSecs); scale 0.5 action in the loss grammar; lots feature (lot-scaled arm); entry-session scope (D7 `session` matches the CURRENT session, the scored scope is the ENTRY session); per-book blackout minutes / same-side flag; per-book L1 windows and evaluation frequency; ALONE mode per book (state cut off, path on).

### 5a. Heat of B per book

**B1**

| book | B1 |
|---|---|
| K7 | cells with nfire>=30: 14580; S>0: 112; best S +174 (B1_4127); median S -1087 |
| P7 | cells with nfire>=30: 14580; S>0: 558; best S +875 (B1_12765); median S -6806 |
| M7 | cells with nfire>=30: 14522; S>0: 1904; best S +192 (B1_7085); median S -682 |
| U7 | cells with nfire>=30: 14530; S>0: 344; best S +568 (B1_7001); median S -973 |
| A7 | cells with nfire>=30: 14472; S>0: 574; best S +105 (B1_1909); median S -446 |
| H7 | cells with nfire>=30: 14450; S>0: 1596; best S +238 (B1_12960); median S -462 |
| O7 | cells with nfire>=30: 10894; S>0: 832; best S +31 (B1_7430); median S -145 |


**B1_alone**

| book | B1_alone |
|---|---|
| K7 | cells with nfire>=30: 14580; S>0: 94; best S +313 (B1a_9889); median S -1197 |
| P7 | cells with nfire>=30: 14580; S>0: 34; best S +709 (B1a_13363); median S -7125 |
| M7 | cells with nfire>=30: 14580; S>0: 48; best S +122 (B1a_13337); median S -898 |
| U7 | cells with nfire>=30: 14580; S>0: 42; best S +266 (B1a_7409); median S -1091 |
| A7 | cells with nfire>=30: 14580; S>0: 16; best S +82 (B1a_1167); median S -582 |
| H7 | cells with nfire>=30: 14580; S>0: 0; best S -113 (B1a_1417); median S -1159 |
| O7 | cells with nfire>=30: 14580; S>0: 160; best S +42 (B1a_4108); median S -122 |


**B2**

| book | B2 |
|---|---|
| K7 | cells with nfire>=30: 4; S>0: 0; best S -1322 (B2_K7_TH_LIVE_add); median S -1776 |
| P7 | cells with nfire>=30: 4; S>0: 0; best S -6343 (B2_P7_TH_LIVE_alone); median S -11852 |
| M7 | cells with nfire>=30: 4; S>0: 0; best S -1211 (B2_M7_TH_LIVE_alone); median S -1356 |
| U7 | cells with nfire>=30: 4; S>0: 0; best S -932 (B2_U7_TH_LIVE_add); median S -1762 |
| A7 | cells with nfire>=30: 0; S>0: 0; best S n/a (-); median S n/a |
| H7 | cells with nfire>=30: 0; S>0: 0; best S n/a (-); median S n/a |
| O7 | cells with nfire>=30: 0; S>0: 0; best S n/a (-); median S n/a |


## 6. Finalist policies: first-order, live week, engine cascade

| policy | what | first-order stack delta vs S1-COMB (USD/week (MDE)): L1M / L2M / L3M / L6M / HOLD / MID / PRE / X' | live week (first-order, USD) | by book |
|---|---|---|---|---|
| B_ADD | B1 AddToPath, best cell per book (books with S>0) | +6200(+5389) / +5193(+4427) / +4624(+4677) / +2969(+3747) / +1722(+3163) / +4574(+5455) / +1256(+2157) / +1068(+1565) | -2386 | K7 -2111, M7 -276 |
| B_ALONE | B1 path-only, best cell per book (books with S>0) | +158(+4292) / +2337(+5923) / +826(+5373) / +1642(+4480) / +1249(+3380) / -741(+5729) / +2(+1792) / +2061(+1391) | -892 | K7 -2920, M7 +2271, U7 -243 |
| B3_ADD_ON_ASTACK | B3: B_ADD cells added to the A_STACK state variants (AddToPath) | +4583(+8098) / +4730(+5466) / +5957(+4432) / +3792(+5632) / +2274(+3828) / +2023(+8442) / +1576(+2480) / +1036(+1571) | -966 | K7 -1390, P7 +700, M7 -276 |


Engine cascade (replica engine, true fills, re-entries and locks included), policy vs the S1-COMB engine run on the same months, USD/week net of the 4.84 fee proxy, carrying week dropped, label day of the exit (STATE-SCORE stage-2 convention); (MDE):

| policy | what | months run | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M with/without | maxDD PRE with/without |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B_ADD | B1 AddToPath, best cell per book (books with S>0) | 8 (202603..202610) | +1032 (+9778) | +3535 (+8253) | +830 (+7389) | +2000 (+5164) | +1085 (+3251) | +2405 (+7941) | n/a | n/a | +76456/+79709 | n/a |
| B_ALONE | B1 path-only, best cell per book (books with S>0) | 8 (202603..202610) | -6345 (+8825) | -3596 (+5700) | -4048 (+4398) | -1685 (+5686) | -960 (+3357) | +2041 (+7138) | n/a | n/a | +89328/+79709 | n/a |
| B3_ADD_ON_ASTACK | B3: B_ADD cells added to the A_STACK state variants (AddToPath) | 8 (202603..202610) | -4996 (+12945) | -371 (+10044) | -1766 (+8066) | -1495 (+7053) | +396 (+4047) | +2418 (+7753) | n/a | n/a | +87163/+79709 | n/a |


## 7. ENTER verdict per finalist policy (vs S1-COMB, engine cascade)

| policy | engine L6M (MDE) | engine PRE (MDE) | above MDE on both | drawdown not worse L6M / PRE | live week (first-order, USD) | components ENTER | policy verdict |
|---|---|---|---|---|---|---|---|
| B_ADD | +2000 (+5164) | +0 (+0) | no | ok / ok | -2386 | no | NOT ENTER (not above MDE, live week, components fail nulls/walk-forward) |
| B_ALONE | -1685 (+5686) | +0 (+0) | no | worse / ok | -892 | no | NOT ENTER (not above MDE, drawdown, live week, components fail nulls/walk-forward) |
| B3_ADD_ON_ASTACK | -1495 (+7053) | +0 (+0) | no | worse / ok | -966 | no | NOT ENTER (not above MDE, drawdown, live week, components fail nulls/walk-forward) |


A policy ENTERS only if every component rule ENTERS in section 4 (placebo v1+v2, family, walk-forward, live, above MDE) AND the engine cascade is above MDE on L6M and PRE, drawdown not worse and the live week is not negative. The X' window is absent from the engine rows (months 2023-04..2024-01 are not in the engine run; the first-order X' column in section 6 covers it).

## 8. PLAIN6060 and NEVER-CUT reference rows

PLAIN6060 (no TH of any kind) engine months available: 43 (202304..202610) of 43; windows without data show n/a.

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| S1-COMB vs PLAIN6060 (engine) | +12301 (+17228) | +11780 (+13411) | +10145 (+13982) | +9975 (+10798) | +7031 (+7518) | +914 (+13193) | +2142 (+4192) | +973 (+2986) |
| B_ADD vs PLAIN6060 (engine, 8 months) | +13333 (+25462) | +5100 (+25861) | +8956 (+17532) | +11164 (+12170) | +5729 (+6991) | -1122 (+13538) | n/a | n/a |
| B_ALONE vs PLAIN6060 (engine, 8 months) | +5955 (+22051) | +6278 (+17074) | +4240 (+15546) | +8876 (+10634) | +4975 (+6469) | -720 (+11446) | n/a | n/a |
| B3_ADD_ON_ASTACK vs PLAIN6060 (engine, 8 months) | +7305 (+23381) | +1615 (+21451) | +6641 (+15299) | +9171 (+13252) | +5008 (+7385) | +4265 (+14233) | n/a | n/a |


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
