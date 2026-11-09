# DS3_TH_STATE_D - program D (L1 profit) on the TH-L2-S base S1-COMB
**INTERIM - S1 timer-close, superseded by T-TH-EXHAUST; interim (X4 partial: 31 of 33 months run, reference rows K7/M7/A7/H7/O7 incomplete; D6 composite and per-session overrides not run).**
**Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched; the per-book COMB procedure fails the out-of-sample walk-forward (DS3_TH_STATE.md section 5) so S1-COMB is an in-sample base**

Prereg: autopilot/DS3_TH_STATE_CD_PREREG.md (sha256 and addendum 1 in DECISIONS.md, logged before any S2-CD number). Research only, nothing live, no PASS claims. USD per week at the trade lots, net of the 4.84 fee proxy, carrying week dropped (single largest-|delta| ISO week of the window), selection data through 2026-10-31; windows L1M/L2M/L3M/L6M/HOLD as of 2026-10-31, MID, PRE, X'; `mean (mde)` = weekly mean delta and 2.8 sd/sqrt(n). Code: code/th_redo/state_profit.py (engine subclass), code/th_state_cd/ (screens, nulls, report). Private tree /mnt/l2/l2vast/_th_state/s2/CD/.

## 1. Answer first
**Every book gets a rule below; none of the 7 books ENTER** (ENTER = engine cascade beats S1-COMB on L6M AND PRE with the carrying week dropped and L6M above its MDE, drawdown-first not worse, placebo p<=.10, family p<=.10, purged walk-forward positive in L6M and PRE, held-out live week not negative). The S1-COMB base has **zero** profit-side exits in all 43 months (live ThL2 profit is OFF and the live policy file carries no profit lines in the replica), so S1-COMB equals "state cut + plain 60/60 brackets" and a profit rule is tested against exactly that.

| book | best D rule (engine-tested, best S = min(L6M, PRE) vs S1-COMB) | set | engine vs S1-COMB L6M / PRE (mde) | vs PLAIN6060 L6M / PRE | first-order S / nfire | placebo p / family p / WF | live week USD (fires) | verdict |
|---|---|---|---|---|---|---|---|---|
| K7 | scale-out: half of the lots (floor; inert on 1-lot positions) exits at a nominal limit at 0.7 x target | D1 | +214 (2206) / +284 (806) | +1214 / +408 | -47 / 602 | 1.000 / 1.000 / neg | +295 (5) | no (L6M below its MDE; placebo p 1.000; family p 1.000; purged walk-forward not positive) |
| P7 | scale-out: half of the lots (floor; inert on 1-lot positions) exits at a nominal limit at 0.7 x target | X4 | -2734 (3629) / -1685 (2227) | +6249 / +826 | +652 / 2776 | 1.000 / 1.000 / neg | -8046 (29) | no (L6M/PRE not both positive vs S1-COMB; drawdown-first worse; placebo p 1.000; family p 1.000; purged walk-forward not positive; live week -8046) |
| M7 | D1 Ph: once the favourable extreme >= 20 pt, >= 2 of 4 votes (DS7 defaults: momentum 30 s / 4 pt, stall 60 s / pull 4 pt, efficiency 60 s / .35, volatility collapse 30 s / .55) -> trail 8 pt behind the extreme | X2 | -252 (2934) / -631 (1443) | -646 / -157 | -162 / 2883 | 0.001 / 1.000 / neg | +2356 (17) | no (L6M/PRE not both positive vs S1-COMB; drawdown-first worse; family p 1.000; purged walk-forward not positive) |
| U7 | D3 ATR trail: after pct >= 0.7 of target trail 0.75 x ATR(5m,14) behind the favourable extreme, ratchets; market exit on touch | D1 | -23 (2292) / -645 (1419) | -268 / -577 | -297 / 568 | 0.001 / 1.000 / neg | +0 (0) | no (L6M/PRE not both positive vs S1-COMB; family p 1.000; purged walk-forward not positive) |
| A7 | D1 Ph: once the favourable extreme >= 30 pt, >= 4 of 4 votes (DS7 defaults: momentum 30 s / 4 pt, stall 60 s / pull 4 pt, efficiency 60 s / .35, volatility collapse 30 s / .55) -> trail 10 pt behind the extreme | D1 | -560 (1147) / -218 (457) | -588 / -228 | -183 / 474 | 0.001 / 1.000 / neg | +2032 (6) | no (L6M/PRE not both positive vs S1-COMB; drawdown-first worse; family p 1.000; purged walk-forward not positive) |
| H7 | D1 Ph: once the favourable extreme >= 15 pt, >= 4 of 4 votes (DS7 defaults: momentum 30 s / 4 pt, stall 60 s / pull 4 pt, efficiency 60 s / .35, volatility collapse 30 s / .55) -> trail 20 pt behind the extreme | D1 | -1169 (1572) / -428 (938) | -180 / -581 | -759 / 536 | 0.032 / 1.000 / neg | +1061 (3) | no (L6M/PRE not both positive vs S1-COMB; drawdown-first worse; family p 1.000; purged walk-forward not positive) |
| O7 | D3 ATR trail: after pct >= 0.7 of target trail 2 x ATR(5m,7) behind the favourable extreme, ratchets; market exit on touch | D1 | +37 (58) / +14 (150) | +143 / -79 | +23 / 44 | 0.001 / 1.000 / neg | +0 (0) | no (L6M below its MDE; family p 1.000; purged walk-forward not positive) |
| X3/X4/X5 | pooled-all-books fallback: scale-out half at pct 0.7, runner none | - | not engine-testable (no X book trades in the S1 lists; 8 X trades in the PROFIT-STATE sample) | - | S +566 | - | - | fallback `*` line, no evidence |

Reading: the engine deltas against S1-COMB are all inside their MDEs; see section 5 for the L6M/PRE/X' split and the cross-book spill-over (the "ALL" row).

## 2. Base, reference rows and the partial-exit subclass
- Base S1-COMB: replica engine (ITER14_PRM), per-book state cut TH-L2-S, 43 months 2023-04..2026-10 (TH_STATE_BASE_S1.md). Reference rows on the same base: **S1-COMB** itself (zero profit exits in 43 months, exits: Target 9527, StateCut 6694, Stop/StopJoin 3834, StackCut 435, TimeBlock 359, BookLock 213), **S1-COMB-PO** (state cut with the engine profit side forced off; 5 months re-run, trade lists identical column by column, so S1-COMB == S1-COMB-PO), **PLAIN6060** (no TH of any kind). "No cut" is not used as a candidate or verdict.
- **Partial exit (scale-out) is now supported** in a new subclass `StateProfitRep(StateBaseRep)` in code/th_redo/state_profit.py (sim.py, adapter_replica.py, rules_replica.py, state_base.py untouched): the half position exits at a nominal limit the first print that touches entry + side x pct x target (`exec_exit` with `qty = pos_qty // 2`, no price improvement, no latency, inert on 1-lot positions); the remainder keeps the bracket and the state cut; optional runner trail (D5). The engine already carried partial-quantity bookkeeping (StackCut partial, partial target fills), so only the trigger is new. Per-book rule dispatch (rule swapped per book inside manage_th_l2/manage_policy) and the PROFIT-STATE 1-s state-feature cells (`profcut`, market exit at mid(s+1) -+ 0.80) are in the same subclass.
- **Regression (scale-out off changes nothing)**: with no candidates (REG, 202304) and with inert scale-out + inert state cells on all books (REGOFF, 202305) the trade lists equal S1-COMB in every column; with the PLAIN6060 rule + inert cells (REGPLAIN, 202305, 249 trades) equal to the stored PLAIN6060 run; with the never-cut rule + inert cells (REGNOCUT, 202305, 249 trades) equal to the stored never-cut run. Zero scale-outs / profit cuts fired in those runs.

## 3. Tier S: first order on the exact 1-s path of the S1-COMB trade list (all 250 cells; best 3 per book by tier)
Decision at the end of second s from the 1-s tape/state, 1 s latency, market exit at mid(s+1) -+ 0.80, scale-out limits nominal; delta = rule exit minus the S1-COMB exit when the rule fires before it. Tiers: E1 recents (L3M and L6M > 0, L1M/L2M not below -0.5 MDE) + tolerant (PRE and X' >= -0.5 MDE) + drawdown first; E2 tolerant + dd; E3 dd; E4 any (nfire >= 30; 10 for A7/H7/O7). `S` = min(L6M, PRE).

| book | cell | tier | rule | S | L6M | PRE | X' | nfire |
|---|---|---|---|---|---|---|---|---|
| K7 | 246 | E1 | scale-out half at pct 0.7, runner none | -47 | +67 | -47 | +114 | 602 |
| K7 | 238 | E1 | scale-out half at pct 0.4, runner none | -90 | +328 | -90 | +248 | 759 |
| K7 | 242 | E1 | scale-out half at pct 0.5, runner none | -182 | +472 | -182 | +229 | 700 |
| P7 | 212 | E1 | time-decay after 10 min: shrink target by 0.25 | +840 | +3474 | +840 | -570 | 2607 |
| P7 | 246 | E1 | scale-out half at pct 0.7, runner none | +652 | +2706 | +652 | +582 | 2776 |
| P7 | 247 | E1 | scale-out half at pct 0.7, runner trail4 | +157 | +3310 | +157 | +560 | 2776 |
| M7 | 106 | E1 | Ph phmin=20 phreq=3 phtrail=12 pt | -67 | +336 | -67 | -78 | 2722 |
| M7 | 94 | E1 | Ph phmin=20 phreq=2 phtrail=8 pt | -162 | +363 | -162 | -71 | 2883 |
| M7 | 93 | E1 | Ph phmin=20 phreq=2 phtrail=6 pt | -167 | +510 | -167 | -110 | 2917 |
| U7 | 193 | E1 | ATR(5m,14) trail mult 0.75 after pct>=0.7 of target | -297 | +451 | -297 | -392 | 568 |
| U7 | 177 | E1 | ATR(5m,7) trail mult 1 after pct>=0.7 of target | -335 | +1018 | -335 | -320 | 487 |
| U7 | 209 | E1 | ATR(5m,14) trail mult 3 after pct>=0.7 of target | -411 | +262 | -411 | -443 | 269 |
| A7 | 145 | E2 | Ph phmin=30 phreq=4 phtrail=10 pt | -183 | -131 | -183 | -9 | 474 |
| A7 | 148 | E2 | Ph phmin=30 phreq=4 phtrail=20 pt | -185 | -171 | -185 | +20 | 437 |
| A7 | 146 | E2 | Ph phmin=30 phreq=4 phtrail=12 pt | -186 | -167 | -186 | +11 | 470 |
| H7 | 88 | E2 | Ph phmin=15 phreq=4 phtrail=20 pt | -759 | -759 | -413 | +105 | 536 |
| H7 | 84 | E2 | Ph phmin=15 phreq=4 phtrail=8 pt | -1001 | -1001 | -355 | +312 | 563 |
| H7 | 80 | E2 | Ph phmin=15 phreq=4 phtrail=2 pt | -1021 | -1021 | -362 | +313 | 564 |
| O7 | 185 | E2 | ATR(5m,7) trail mult 2 after pct>=0.7 of target | +23 | +23 | +32 | +64 | 44 |
| O7 | 205 | E2 | ATR(5m,14) trail mult 2 after pct>=0.7 of target | +0 | +82 | +0 | +125 | 52 |
| O7 | 186 | E2 | ATR(5m,7) trail mult 3 after pct>=0.2 of target | +0 | +0 | +45 | -162 | 62 |

Nulls: placebo = k random trades with an eligible second (the cell's own arming level; mode "armed" = any later second for pull-back exits) and a random eligible exit, 1000 draws, shared world seeds; family = Westfall-Young max-stat over every full-exit cell of the book (200 worlds, each cell keeps its own fired set); scale-out cells: placebo = half-lot random exits of the same count, family by Bonferroni over the scale-out cells. Purged walk-forward = monthly, best trailing-52-week S cell among all cells applied to the next month, 2024-01..2026-10.

## 4. Engine cascade: every finalist rule on top of the S1-COMB state cut (43 months; X4 = 2024-02..2026-10 only)
Per-book rules are run together in one engine run per set (each book carries its own rule, the other books keep S1-COMB behaviour), so a book's delta is cascaded: re-entries, locks, caps and the stack cut spill across books (see the ALL row). Sets: C0 = the 8 PROFIT-STATE per-book rules (prereg), X2 = C re-screen picks (P7, H7, A7, U7) + D extras (K7, M7), D1 = the D per-book best, X4 = D extras (P7, U7) + the live reference rows (K7, M7, A7, H7, O7).

### K7
**K7 cell 238, set X2** - scale-out: half of the lots (floor; inert on 1-lot positions) exits at a nominal limit at 0.4 x target

Policy-file line: `profit K7 * pct>=0.40 scale 0.5   # NEW ACTION `scale <fraction>` (partial exit at a limit)`

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | -778 (6316) | -158 (3722) | +78 (2731) | +150 (1959) | -614 (1127) | -1154 (1814) | +55 (896) | +172 (581) |
| engine delta vs S1-COMB (week not dropped) | -778 (6316) | -1202 (4394) | -663 (3257) | -223 (2152) | -786 (1205) | -1418 (1814) | -79 (960) | +249 (607) |
| engine delta vs PLAIN6060 | +1616 (8824) | -953 (3140) | -45 (3567) | +396 (3706) | -348 (2236) | -159 (2241) | +149 (1403) | -240 (595) |
| first order vs S1-COMB paths | +758 (3270) | +615 (3055) | +738 (2269) | +328 (1457) | -107 (963) | +160 (2063) | -90 (665) | +248 (545) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 45248 -> 36298, PRE 23120 -> 20528; stack ("ALL") delta L6M -6788, PRE -2102. Verdict: **no** (L6M below its MDE; placebo p 1.000; family p 1.000; purged walk-forward not positive).
First order: tier E1, S -90, fires 759, placebo p 1.000 (random-exit mean S +345), family p 1.000 (Bonferroni over 20 scale-out cells), purged walk-forward L6M +60 / PRE -730 -> not positive; drawdown base -> rule L6M 45248 -> 28777, PRE 23120 -> 19337. By entry session (this cell): s0 L6M +211 PRE -311 n 367; s1 L6M -183 PRE +26 n 212; s3 L6M +0 PRE +0 n 0; s4 L6M +126 PRE -78 n 180.

**K7 cell 246, set D1** - scale-out: half of the lots (floor; inert on 1-lot positions) exits at a nominal limit at 0.7 x target

Policy-file line: `profit K7 * pct>=0.70 scale 0.5   # NEW ACTION `scale <fraction>` (partial exit at a limit)`

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | +2566 (4409) | -310 (3105) | +318 (2823) | +214 (2206) | -130 (1219) | -892 (845) | +284 (806) | +91 (483) |
| engine delta vs S1-COMB (week not dropped) | +2566 (4409) | +603 (3746) | +1054 (3316) | +586 (2362) | +63 (1311) | -600 (1124) | +132 (903) | +159 (509) |
| engine delta vs PLAIN6060 | +4960 (9589) | +444 (2465) | +1394 (3926) | +1214 (3712) | +506 (2364) | +593 (2376) | +408 (1368) | -332 (651) |
| first order vs S1-COMB paths | +1400 (2701) | -266 (2516) | +95 (1954) | +67 (1257) | -192 (699) | -694 (957) | -47 (377) | +114 (429) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 45526 -> 37044, PRE 23120 -> 22994; stack ("ALL") delta L6M -6815, PRE -4839. Verdict: **no** (L6M below its MDE; placebo p 1.000; family p 1.000; purged walk-forward not positive).
First order: tier E1, S -47, fires 602, placebo p 1.000 (random-exit mean S +214), family p 1.000 (Bonferroni over 20 scale-out cells), purged walk-forward L6M +60 / PRE -730 -> not positive; drawdown base -> rule L6M 38406 -> 29414, PRE 23120 -> 22040. By entry session (this cell): s0 L6M +102 PRE -114 n 303; s1 L6M -143 PRE +59 n 163; s3 L6M +0 PRE +0 n 0; s4 L6M -28 PRE -51 n 136.

### P7
**P7 cell 212, set D1** - D4 time-decay: 10 min after entry the target moves to (1-0.25) of its distance (market exit if already beyond it)

Policy-file line: `NO D7 LINE: new action `shrinktarget <fraction>` with `mins>=10``

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | -8735 (16292) | -3982 (13755) | -1889 (11725) | -4996 (7786) | -4861 (5105) | -2443 (8632) | -1725 (4573) | +1053 (3171) |
| engine delta vs S1-COMB (week not dropped) | -8735 (16292) | -6962 (14722) | -4112 (12454) | -6070 (8062) | -4112 (5427) | -434 (9681) | -2204 (4707) | +631 (3316) |
| engine delta vs PLAIN6060 | -2521 (21160) | +2109 (20381) | +842 (17102) | +7637 (12747) | +3097 (8500) | -1053 (14101) | -394 (5713) | +1770 (4557) |
| first order vs S1-COMB paths | +1803 (13727) | -1737 (13691) | +4141 (14040) | +3474 (8833) | +3843 (5650) | +5648 (9202) | +840 (3587) | -570 (3883) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 48027 -> 45867, PRE 119255 -> 106594; stack ("ALL") delta L6M -6815, PRE -4839. Verdict: **no** (L6M/PRE not both positive vs S1-COMB; family p 1.000; purged walk-forward not positive; live week -918).
First order: tier E1, S +840, fires 2607, placebo p 0.001 (random-exit mean S +nan), family p 1.000 (random-exit-world max-cell (200 worlds, own arming level)), purged walk-forward L6M +4084 / PRE -1053 -> not positive; drawdown base -> rule L6M 48027 -> 43183, PRE 119255 -> 95980. By entry session (this cell): s0 L6M +1223 PRE +355 n 1206; s1 L6M +801 PRE +694 n 844; s3 L6M +438 PRE -711 n 557.

**P7 cell 246, set X4** - scale-out: half of the lots (floor; inert on 1-lot positions) exits at a nominal limit at 0.7 x target

Policy-file line: `profit P7 * pct>=0.70 scale 0.5   # NEW ACTION `scale <fraction>` (partial exit at a limit)`

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | -4899 (4165) | -2525 (3083) | -1684 (2245) | -2734 (3629) | -2269 (2243) | -2222 (2485) | -1685 (2227) | +0 (0) |
| engine delta vs S1-COMB (week not dropped) | -4899 (4165) | -3187 (3290) | -2207 (2532) | -1893 (4207) | -1858 (2483) | -2862 (2892) | -1109 (2725) | +0 (0) |
| engine delta vs PLAIN6060 | +1315 (10007) | +820 (6018) | +546 (3934) | +6249 (7943) | +4547 (6245) | +2811 (12812) | +826 (4554) | +0 (0) |
| first order vs S1-COMB paths | +3037 (11203) | +847 (9306) | +2686 (7453) | +2706 (4719) | +2824 (2998) | +1457 (5644) | +652 (1946) | +582 (1945) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 48027 -> 60043, PRE 119255 -> 125659; stack ("ALL") delta L6M -2270, PRE -4109. Verdict: **no** (L6M/PRE not both positive vs S1-COMB; drawdown-first worse; placebo p 1.000; family p 1.000; purged walk-forward not positive; live week -8046).
First order: tier E1, S +652, fires 2776, placebo p 1.000 (random-exit mean S +3035), family p 1.000 (Bonferroni over 20 scale-out cells), purged walk-forward L6M +4084 / PRE -1053 -> not positive; drawdown base -> rule L6M 48027 -> 37817, PRE 77992 -> 55679. By entry session (this cell): s0 L6M +731 PRE +150 n 1288; s1 L6M +899 PRE +378 n 892; s3 L6M +649 PRE -39 n 596.

### M7
**M7 cell 94, set X2** - D1 Ph: once the favourable extreme >= 20 pt, >= 2 of 4 votes (DS7 defaults: momentum 30 s / 4 pt, stall 60 s / pull 4 pt, efficiency 60 s / .35, volatility collapse 30 s / .55) -> trail 8 pt behind the extreme

Policy-file line: `NO PANEL PARAMETERS: DS7.cs has Ph parameters only for K7(St), S7(Wt), P7, H7(Hm); book M7 needs new PhOn/PhMinPoints/PhRequired/PhTrailPoints fields (Ph 20/2/8)`

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | -91 (7519) | +1006 (5117) | -304 (4029) | -252 (2934) | -379 (1939) | -2311 (2854) | -631 (1443) | -46 (1385) |
| engine delta vs S1-COMB (week not dropped) | -91 (7519) | -169 (5583) | -1016 (4209) | -757 (3155) | -630 (2027) | -1173 (4117) | -799 (1500) | -265 (1485) |
| engine delta vs PLAIN6060 | +647 (7764) | +1902 (5315) | +202 (4874) | -646 (3418) | -1244 (1996) | -1502 (3149) | -157 (1869) | -562 (1475) |
| first order vs S1-COMB paths | +468 (8864) | +1960 (4210) | +132 (3382) | +363 (2644) | -362 (1896) | -1803 (3042) | -162 (1313) | -71 (1278) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 45172 -> 45875, PRE 32941 -> 48142; stack ("ALL") delta L6M -6788, PRE -2102. Verdict: **no** (L6M/PRE not both positive vs S1-COMB; drawdown-first worse; family p 1.000; purged walk-forward not positive).
First order: tier E1, S -162, fires 2883, placebo p 0.001 (random-exit mean S -2197), family p 1.000 (random-exit-world max-cell (200 worlds, own arming level)), purged walk-forward L6M -606 / PRE -576 -> not positive; drawdown base -> rule L6M 45172 -> 40817, PRE 28279 -> 27827. By entry session (this cell): s1 L6M -406 PRE +62 n 1719; s3 L6M +108 PRE -579 n 1164.

**M7 cell 106, set D1** - D1 Ph: once the favourable extreme >= 20 pt, >= 3 of 4 votes (DS7 defaults: momentum 30 s / 4 pt, stall 60 s / pull 4 pt, efficiency 60 s / .35, volatility collapse 30 s / .55) -> trail 12 pt behind the extreme

Policy-file line: `NO PANEL PARAMETERS: DS7.cs has Ph parameters only for K7(St), S7(Wt), P7, H7(Hm); book M7 needs new PhOn/PhMinPoints/PhRequired/PhTrailPoints fields (Ph 20/3/12)`

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | -819 (3866) | +169 (3956) | -1047 (3547) | -851 (2684) | -918 (1843) | -913 (3461) | -641 (1400) | +46 (1493) |
| engine delta vs S1-COMB (week not dropped) | -819 (3866) | -654 (4181) | -1625 (3641) | -1239 (2798) | -687 (1920) | -1438 (3484) | -780 (1435) | -248 (1675) |
| engine delta vs PLAIN6060 | -81 (5318) | +1195 (4322) | -565 (4575) | -1198 (3303) | -1328 (2094) | -1141 (3320) | -154 (1794) | -537 (1677) |
| first order vs S1-COMB paths | +930 (7698) | +1751 (4185) | +99 (3380) | +336 (2654) | -419 (1951) | -1764 (3395) | -67 (1328) | -78 (1306) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 44242 -> 46464, PRE 32941 -> 45834; stack ("ALL") delta L6M -6815, PRE -4839. Verdict: **no** (L6M/PRE not both positive vs S1-COMB; drawdown-first worse; family p 1.000; purged walk-forward not positive).
First order: tier E1, S -67, fires 2722, placebo p 0.001 (random-exit mean S -2090), family p 1.000 (random-exit-world max-cell (200 worlds, own arming level)), purged walk-forward L6M -606 / PRE -576 -> not positive; drawdown base -> rule L6M 45172 -> 43616, PRE 28279 -> 27405. By entry session (this cell): s1 L6M -554 PRE +77 n 1641; s3 L6M -123 PRE -511 n 1081.

### U7
**U7 cell 193, set D1** - D3 ATR trail: after pct >= 0.7 of target trail 0.75 x ATR(5m,14) behind the favourable extreme, ratchets; market exit on touch

Policy-file line: `NO D7 LINE: new action `atrtrail <n> <mult>` with arm `pct>=0.7``

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | +2142 (3543) | -439 (3888) | -7 (2728) | -23 (2292) | +44 (2054) | -1248 (3754) | -645 (1419) | -1014 (1643) |
| engine delta vs S1-COMB (week not dropped) | +2142 (3543) | +576 (4452) | +934 (3638) | +448 (2567) | +374 (2215) | -1770 (3725) | -420 (1535) | -736 (1785) |
| engine delta vs PLAIN6060 | +2781 (4219) | -370 (4908) | +212 (3344) | -268 (2513) | -80 (2146) | -954 (2702) | -577 (1424) | -1031 (1627) |
| first order vs S1-COMB paths | +2311 (3932) | -467 (3706) | +227 (2807) | +451 (2368) | +76 (1923) | -883 (3864) | -297 (1329) | -392 (1445) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 24202 -> 20291, PRE 39175 -> 32455; stack ("ALL") delta L6M -6815, PRE -4839. Verdict: **no** (L6M/PRE not both positive vs S1-COMB; family p 1.000; purged walk-forward not positive).
First order: tier E1, S -297, fires 568, placebo p 0.001 (random-exit mean S -1936), family p 1.000 (random-exit-world max-cell (200 worlds, own arming level)), purged walk-forward L6M +186 / PRE -725 -> not positive; drawdown base -> rule L6M 24202 -> 16361, PRE 39175 -> 32663. By entry session (this cell): s0 L6M +257 PRE +14 n 312; s1 L6M -251 PRE -201 n 256.

**U7 cell 177, set X4** - D3 ATR trail: after pct >= 0.7 of target trail 1 x ATR(5m,7) behind the favourable extreme, ratchets; market exit on touch

Policy-file line: `NO D7 LINE: new action `atrtrail <n> <mult>` with arm `pct>=0.7``

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | +2331 (4437) | +688 (2239) | +459 (1484) | +111 (1740) | +164 (1851) | -1820 (3368) | -695 (1406) | +0 (0) |
| engine delta vs S1-COMB (week not dropped) | +2331 (4437) | +1295 (2604) | +896 (1834) | +451 (1925) | +494 (2037) | -1051 (3753) | -475 (1518) | +0 (0) |
| engine delta vs PLAIN6060 | +2970 (5090) | +811 (2924) | +541 (1932) | +474 (2014) | +11 (1933) | -191 (2997) | -627 (1426) | +0 (0) |
| first order vs S1-COMB paths | +2731 (5430) | -5 (4132) | +888 (3239) | +1018 (2143) | +397 (1879) | -378 (3716) | -335 (1304) | -320 (1485) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 17150 -> 21051, PRE 39175 -> 33005; stack ("ALL") delta L6M -2270, PRE -4109. Verdict: **no** (L6M/PRE not both positive vs S1-COMB; drawdown-first worse; family p 1.000; purged walk-forward not positive).
First order: tier E1, S -335, fires 487, placebo p 0.001 (random-exit mean S -1724), family p 1.000 (random-exit-world max-cell (200 worlds, own arming level)), purged walk-forward L6M +186 / PRE -725 -> not positive; drawdown base -> rule L6M 24202 -> 12753, PRE 39175 -> 32544. By entry session (this cell): s0 L6M +594 PRE -129 n 271; s1 L6M +94 PRE -315 n 216.

### A7
**A7 cell 145, set D1** - D1 Ph: once the favourable extreme >= 30 pt, >= 4 of 4 votes (DS7 defaults: momentum 30 s / 4 pt, stall 60 s / pull 4 pt, efficiency 60 s / .35, volatility collapse 30 s / .55) -> trail 10 pt behind the extreme

Policy-file line: `NO PANEL PARAMETERS: DS7.cs has Ph parameters only for K7(St), S7(Wt), P7, H7(Hm); book A7 needs new PhOn/PhMinPoints/PhRequired/PhTrailPoints fields (Ph 30/4/10)`

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | -441 (3430) | -365 (1289) | -375 (1592) | -560 (1147) | -274 (746) | -188 (1268) | -218 (457) | -19 (295) |
| engine delta vs S1-COMB (week not dropped) | -441 (3430) | -838 (1744) | +122 (2021) | -304 (1314) | -152 (808) | -380 (1276) | -295 (499) | -63 (314) |
| engine delta vs PLAIN6060 | -744 (2176) | -858 (891) | -321 (1528) | -588 (1277) | -263 (863) | -303 (1491) | -228 (479) | -18 (314) |
| first order vs S1-COMB paths | -719 (4514) | -695 (1961) | +149 (1967) | -131 (1439) | -147 (870) | -621 (1085) | -183 (440) | -9 (348) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 8059 -> 8815, PRE 7300 -> 6878; stack ("ALL") delta L6M -6815, PRE -4839. Verdict: **no** (L6M/PRE not both positive vs S1-COMB; drawdown-first worse; family p 1.000; purged walk-forward not positive).
First order: tier E2, S -183, fires 474, placebo p 0.001 (random-exit mean S -952), family p 1.000 (random-exit-world max-cell (200 worlds, own arming level)), purged walk-forward L6M -494 / PRE -320 -> not positive; drawdown base -> rule L6M 8059 -> 6224, PRE 7300 -> 5453. By entry session (this cell): s0 L6M -131 PRE -183 n 474.

### H7
**H7 cell 88, set D1** - D1 Ph: once the favourable extreme >= 15 pt, >= 4 of 4 votes (DS7 defaults: momentum 30 s / 4 pt, stall 60 s / pull 4 pt, efficiency 60 s / .35, volatility collapse 30 s / .55) -> trail 20 pt behind the extreme

Policy-file line: `PANEL HmPhOn=true; HmPhMinPoints=15; HmPhRequired=4; HmPhTrailPoints=20   (no policy-file line for Ph)`

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | -1734 (2430) | -517 (2468) | -1071 (1942) | -1169 (1572) | -509 (1178) | +515 (2421) | -428 (938) | +651 (1187) |
| engine delta vs S1-COMB (week not dropped) | -1734 (2430) | -923 (2455) | -1309 (1907) | -1749 (2219) | -812 (1433) | -311 (3199) | -595 (1036) | +447 (1293) |
| engine delta vs PLAIN6060 | +818 (3358) | +1031 (2209) | +771 (2013) | -180 (2402) | +104 (1799) | +992 (4803) | -581 (1031) | +702 (1249) |
| first order vs S1-COMB paths | -1906 (3223) | -1067 (2958) | -1370 (2293) | -759 (1699) | -122 (1131) | -312 (1615) | -413 (855) | +105 (1311) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 8078 -> 12726, PRE 19246 -> 14759; stack ("ALL") delta L6M -6815, PRE -4839. Verdict: **no** (L6M/PRE not both positive vs S1-COMB; drawdown-first worse; family p 1.000; purged walk-forward not positive).
First order: tier E2, S -759, fires 536, placebo p 0.032 (random-exit mean S +nan), family p 1.000 (random-exit-world max-cell (200 worlds, own arming level)), purged walk-forward L6M -1530 / PRE -259 -> not positive; drawdown base -> rule L6M 8078 -> 6735, PRE 19246 -> 16287. By entry session (this cell): s0 L6M -632 PRE -485 n 301; s3 L6M -242 PRE -67 n 235.

### O7
**O7 cell 185, set D1** - D3 ATR trail: after pct >= 0.7 of target trail 2 x ATR(5m,7) behind the favourable extreme, ratchets; market exit on touch

Policy-file line: `NO D7 LINE: new action `atrtrail <n> <mult>` with arm `pct>=0.7``

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | +0 (0) | +0 (0) | +0 (0) | +37 (58) | -36 (136) | +44 (122) | +14 (150) | +99 (204) |
| engine delta vs S1-COMB (week not dropped) | +0 (0) | +0 (0) | +0 (0) | +51 (68) | -67 (160) | -70 (338) | -18 (173) | +62 (224) |
| engine delta vs PLAIN6060 | +68 (116) | +134 (153) | +123 (114) | +143 (84) | +49 (176) | +79 (456) | -79 (253) | +100 (254) |
| first order vs S1-COMB paths | +0 (0) | +0 (0) | +0 (0) | +23 (37) | -48 (133) | +30 (85) | +32 (143) | +64 (225) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 8943 -> 8923, PRE 4562 -> 3941; stack ("ALL") delta L6M -6815, PRE -4839. Verdict: **no** (L6M below its MDE; family p 1.000; purged walk-forward not positive).
First order: tier E2, S +23, fires 44, placebo p 0.001 (random-exit mean S -79), family p 1.000 (random-exit-world max-cell (200 worlds, own arming level)), purged walk-forward L6M -33 / PRE -43 -> not positive; drawdown base -> rule L6M 8923 -> 8923, PRE 4562 -> 3941. By entry session (this cell): s3 L6M +23 PRE +32 n 44.

## 5. Held-out live week (2026-11-01 evening .. 11-05, 187 live trades; csv sha256 424c68da934136df7124004b4b1fd9a34952a1e5e3e6ba1017ad0d972a927112)
Each rule applied on the live 1-s path from the live entry fill to the ACTUAL live exit (first order, live lots): delta = rule exit points (mid(s+1) -+ 0.80, scale-out nominal) minus live exit points, only where the rule fires before the live exit. Reported, never selected on; trades whose exit lies beyond the tape end (2026-11-05 15:25 UTC) are excluded.

| book | cell | rule | trades | fires | delta USD | better | worse | live gross USD |
|---|---|---|---|---|---|---|---|---|
| K7 | 238 | scale-out: half of the lots (floor; inert on 1-lot positions) exits at a nominal limit at 0.4 x target | 64 | 8 | +2033 | 4 | 4 | +14845 |
| M7 | 94 | D1 Ph: once the favourable extreme >= 20 pt, >= 2 of 4 votes (DS7 defaults: momentum 30 s / 4 pt, stall 60 s / | 28 | 17 | +2356 | 7 | 10 | +6738 |
| K7 | 246 | scale-out: half of the lots (floor; inert on 1-lot positions) exits at a nominal limit at 0.7 x target | 64 | 5 | +295 | 1 | 4 | +14845 |
| P7 | 212 | D4 time-decay: 10 min after entry the target moves to (1-0.25) of its distance (market exit if already beyond  | 52 | 25 | -918 | 3 | 22 | +79302 |
| M7 | 106 | D1 Ph: once the favourable extreme >= 20 pt, >= 3 of 4 votes (DS7 defaults: momentum 30 s / 4 pt, stall 60 s / | 28 | 16 | +2917 | 7 | 9 | +6738 |
| U7 | 193 | D3 ATR trail: after pct >= 0.7 of target trail 0.75 x ATR(5m,14) behind the favourable extreme, ratchets; mark | 6 | 0 | +0 | 0 | 0 | +624 |
| A7 | 145 | D1 Ph: once the favourable extreme >= 30 pt, >= 4 of 4 votes (DS7 defaults: momentum 30 s / 4 pt, stall 60 s / | 23 | 6 | +2032 | 4 | 2 | -1415 |
| H7 | 88 | D1 Ph: once the favourable extreme >= 15 pt, >= 4 of 4 votes (DS7 defaults: momentum 30 s / 4 pt, stall 60 s / | 3 | 3 | +1061 | 2 | 1 | -775 |
| O7 | 185 | D3 ATR trail: after pct >= 0.7 of target trail 2 x ATR(5m,7) behind the favourable extreme, ratchets; market e | 3 | 0 | +0 | 0 | 0 | +660 |
| P7 | 246 | scale-out: half of the lots (floor; inert on 1-lot positions) exits at a nominal limit at 0.7 x target | 52 | 29 | -8046 | 3 | 26 | +79302 |
| U7 | 177 | D3 ATR trail: after pct >= 0.7 of target trail 1 x ATR(5m,7) behind the favourable extreme, ratchets; market e | 6 | 0 | +0 | 0 | 0 | +624 |
One week is not evidence; the table is a held-out sanity check only.

## 6. Policy-file grammar gaps (D7 grammar)
- `persist=<s>` (condition true for N consecutive seconds) is missing on profit lines; the per-rule pulled window (pulled_mult over 5 or 10 s per line), the slow-base relative depth features (tot_rel/ahead_rel on a ~2-day slot baseline), `scale <fraction>` (partial exit at a limit) and the entry-session scope (rules here are per book; session overrides were not searched) are not in the grammar; `lots` as a feature is not needed by these rules.
- D1 Ph is a panel parameter set (PhOn/PhMinPoints/PhRequired/PhTrailPoints exist only for K7(St), S7(Wt), P7 and H7(Hm)); chandelier, ATR trail and target shrink need new actions; time-decay market exits are expressible with `mins>=` and `pct<=` if the grammar accepts `pct<=` on the profit side.

## 7. Caveats
(1) Entries are replica-engine entries, not live-matched (about 100 of 187 blind-week trades match). (2) Base S1-COMB is an in-sample base: the per-book state cut fails its out-of-sample walk-forward, so every delta here is conditional on that cut. (3) First order scores each trade on the S1-COMB path alone; re-entries after a profit exit only exist in the engine cascade. (4) Scale-out and target-shrink limits fill at the nominal level on touch (no queue); the engine target fills with cumvol, so first-order scale-out is optimistic against the live queue. (5) The engine runs per-book rules together; cross-book spill-over is in the ALL row. (6) D1 votes use 1-s mids in Tier S but 100-ms print samples in the engine. (7) Placebo/family nulls are "random exit of the same count" nulls at the cell's own arming level and are lenient for early-take rules; read them together with the engine deltas and the walk-forward. (8) The live-week table is one week (first order). (9) Per-session overrides were not searched. (10) X3/X4/X5 never trade in the S1 engine lists, the pooled fallback has no evidence.
