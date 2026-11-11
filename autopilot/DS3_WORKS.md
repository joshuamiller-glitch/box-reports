# DS3_WORKS - T-WORKS expand-what-works (aggregate page; built by W-J; 2026-11-11T14:00:06Z; Shadow only, no PASS claims)

Sections A, B, C are the workers' own pages (DS3_WORKS_A/B/C.md) merged below. Section D is W-J: the reference rows (JN04RM vs LPB_BASE), the JN05 composition and the REFIT 2026-11-22 preview. Every number is exact-engine, live panel base (P7 day cap 8,400 + table 7,4,0,4,0,0 + P7 cut 40/5x/w5/p3), reference LPB_BASE, ROLLFIX1.

## D0. Reference rows (exact, rule mode, 43 months)

| cell | window | mean $/wk | mean_ref (LPB_BASE) | maxDD | maxDD_ref | cut % | d mean | WF beat % | label |
|--|--|--|--|--|--|--|--|--|--|
| JN04RM | L1M | 10653 | 17539 | 27056 | 51253 | +47.2 | -6886 | 90 |  |
| JN04RM | L3M | 15022 | 17224 | 41699 | 77224 | +46.0 | -2202 | 90 |  |
| JN04RM | L6M | 19862 | 21495 | 41699 | 77224 | +46.0 | -1633 | 90 | OK-PRIOR (allow 25.0%, WF 90%) |
| JN04RM | HOLD | 12954 | 16540 | 72757 | 78842 | +7.7 | -3586 | 90 |  |
| JN04RM | PRE | 8714 | 10548 | 66714 | 99479 | +32.9 | -1834 | 90 |  |
| JN04RM | X' | 2195 | 2553 | 64077 | 122553 | +47.7 | -357 | 90 |  |

LPB_BASE is the reference itself (cut 0, d mean 0 by construction).

## D1. Harness reproduction check

| month | trades JN04RM / JN05W_REF | net JN04RM | net JN05W_REF | trade-by-trade identical (book, lots, entry_ns, exit_ns, net) |
|--|--|--|--|--|
| 202610 | 858 / 858 | 20778.50 | 20778.50 | IDENTICAL |
| 202608 | 695 / 695 | 38461.34 | 38461.34 | IDENTICAL |

Verdict: JN04RM reproduced through the W-J harness to the dollar.

## D2. JN05 composition and REFIT preview (W-J)

Status at the first build: harness ready, no A/B/C winners have landed, so JN05 has not been composed or scored.

Harness (code/th_works_j; reads and runs only; shared files append-only). mkset.py builds a set json as a copy of JN04RM with overrides (jnrule config, cde state rule, hooks/hooklist, mtab table, zact). run_one.sh runs ONE set per job through the IJK driver (jbjobs, JointRep, ROLLFIX1 patched engine) with one worker, gated on MemAvail of at least 62 GB sustained 60 s and aborting under 41 GB. score_w.py scores any runs_rf cell against the live panel base reference LPB_BASE on L1M, L3M, L6M, HOLD, PRE and X', with the bi-weekly walk-forward over the 43 contiguous months and the rule 2a label. A month of the full stack takes about four minutes on one worker, so a full 43-month set is about three hours on one worker. The new composition names carry the prefix JN05W because the name JN05 is already taken by an old IJK first-order stack (set json JN05.json, HOLD runs only).

Reproduction: JN04RM re-run through this harness as the set JN05W_REF (identical config, one set per job) is identical trade by trade to the stored JN04RM in 202610 (858 trades, net 20,778.50) and 202608 (695 trades, net 38,461.34); see D1. The scorer also reproduces the stored lpb_rm_scores.csv for JN04RM to the digit (L6M cut +46.0, mean 19,862 against LPB_BASE 21,495; HOLD +7.7; PRE +32.9; X' +47.7; WF 90%).

Plan once winners land. Candidate layers per family: dial layers from DS3_WORKS_A (performance gates, volatility dial, exposure caps), regime-conditional exits from DS3_WORKS_B, P7 re-entry and Asia rules from DS3_WORKS_C, plus the existing leads JX01 to JX07 (being re-run one set per job by SZ-CDE) and the C2 regime stacks. Each layer enters as top-K from its own page, then coordinate descent in the exact engine on top of JN04RM, one set per job, L6M then HOLD then PRE then X', then the 43-month walk-forward. Rule 2a floors apply: PRE mean not worse than the 25% floor, recents-first ranking. The two live weeks (frozen week 11-01..05 only; 11-09..11 live data is not on the box) are replayed through the engine replay (code/th_r13) with the JN05W rules at the end.

Not yet available: JN05W composition, live-week replay, REFIT 2026-11-22 preview with JN05W. For reference the existing first-order REFIT dry run (DS3_JOINT_2.md C3) does not select the four JN04 layers on the 26-week training window.


## A. Generalise the dials (W-A)

(DS3_WORKS_A.md has not landed yet at 2026-11-11T14:00:06Z)


## B. Regime-conditional exits (W-B)

(DS3_WORKS_B.md has not landed yet at 2026-11-11T14:00:06Z)


## C. P7 anatomy (W-C)

Source DS3_WORKS_C.md (mtime 2026-11-11T13:39:17Z UTC), included verbatim, read only:

# DS3_WORKS_C - T-WORKS Part C (P7 anatomy), W-C, page 2026-11-11 13:39Z (C1 anatomy; C2-C4 running)
Label: PRE-PROOF, post-hoc, descriptive, Shadow only, no PASS claim. Prereg autopilot/WORKS_C_PREREG.md (sha in DECISIONS.md 13:35Z). Source: the exact LPB_BASE trade list (live panel base: P7 day cap 8,400, 7/4/4, P7 cut 40/5x/w5/p3, no JN04 dials), 4,958 P7 trades 2023-04..2026-10, plus the 53 P7 trades of the frozen live week 11-01..05 (data/live_frozen reconstructed file; live fees proxied at $4.84 per contract). Features are causal at the signal second (NQ 1-min bars, ER(20) on 5-min, atr_rel = 5-min ATR over its 20-day norm, LOT state = P7 shadow Calmar over the last 10 label days from the same list). Code code/th_works/c1_build.py, c1_cells.py, c1_excess.py, c1_page.py; table /mnt/l2/l2vast/_th_works/c/c1_cells.csv.

## C1 in plain sentences
1. P7 earns $897k over the 3.5 years in this base, $237k in L6M, and $0k in the live week (28 targets, 24 cuts, 1 BookLock). Its 20 worst weeks lose $552k together. Winners are targets at a flat 60 points (mean about +$4,000 per trade in L6M) and losers are StateCuts at a mean of about -$3,000 per trade; P7 wins only about 45 percent of its trades, so the week is decided by the cut rate.
2. A worst-20 week is not a busy week (26.5 P7 trades in both the worst and the other weeks). It is a week where 62 percent of trades end as StateCuts against 50 percent in other weeks, i.e. the same entries, but the trend continues through the cut instead of reverting to target.
3. Where the worst weeks sit (excess loss = worst-week net minus what the same cell earns per trade in other weeks): Asia is the largest carrier (284 trades in worst weeks, mean -$1,475 against +$580 in other weeks, 76 percent of the worst-20 loss; Asia is also where 80 percent of the 3.5-year profit comes from). By lots, 7-lot trades (all Asia in the live table) lose -$3,557 per trade in worst weeks against +$1,037 otherwise: 98 trades carry -$349k of the -$552k. 4-lot trades are flat over the whole history (-$3 per trade outside worst weeks) and lose -$1,240 in worst weeks.
4. Trend state matters, a result that matches the live week: signals taken WITH a session move of more than 1 ATR (the trend is already running in the trade direction, 3,270 trades) carry 66 percent of the worst-20 loss, and entries after a P7 loss, within 30 minutes of the last P7 exit, and with K7/U7/M7 already open on the same side are all over-represented. These are one regime seen from several sides: a trending Asia session where P7 keeps re-entering the same direction, gets cut, and re-enters. In L6M the worst 5 weeks (202644, 202631, 202636, 202635, 202621) show the same shape: with-trend, short side (87 percent of the L6M worst-5 loss is on the short side), inside 30 minutes of the last exit (96 percent), third-or-later trade of the session (72 percent).
5. What the table says about the dials: LOT state "cold" (Calmar10 < 1) is true for 3,000 of 4,958 trades, and cold trades earn MORE per trade in L6M (+$357) than warm ones (+$55) while also carrying 73 percent of the worst-20 loss. So the LOT dial (halve when cold) cuts both the winners and the losers of a state that is cold 60 percent of the time; it is a drawdown dial, not a profit dial, and in the live week all 53 P7 trades were taken cold (Calmar10 mean 0.07) so the JN04 LOT dial would have been halving lots all week while 28 targets paid +$159k (this is an inference from the LPB shadow Calmar, to be confirmed by replaying JN04RM on the live week). This is the same finding as the loss-cut page: the dials are right in chop and wrong in trend.
6. ER(20) and atr_rel do not separate the carriers cleanly. ER above 0.45 has the worst per-trade loss in worst weeks (-$2,269 against +$798 otherwise) but ER below 0.15 loses little in worst weeks (-$208 per trade); atr_rel above 1.6 is the only atr bucket negative in L6M (-$373 per trade, -$70k net) but earned +$27 per trade over 3.5 years. The live week was atr_rel above 1.6 for 27 of 53 trades and made +$39k there. So REG (atr_rel >= 1.3) is a poor stand-alone chop/trend flag for P7; the cleaner conditional flags in the table are "with-trend entry" and "same-side re-entry inside 30 minutes".
7. Side: shorts carry 54 percent of the 3.5-year worst-week loss and 87 percent in L6M; the whole L6M bad stretch is short Asia (308 trades, +$956 other weeks, -$1,175 in worst-5 weeks).
8. Live week: 53 trades, +$84.8k net of proxy fees. 24 StateCuts/PolicyCuts cost -$74k and 28 targets made +$159k. 33 of 53 trades were the 3rd or later P7 trade of the session, 29 were taken inside 30 minutes of the previous P7 exit (+$52.9k), 33 were with-trend. The with-trend and within-30-minutes cells were the winners that week; in the five worst L6M weeks the same cells were the losers. That is the regime flag problem in one sentence: the same cell wins in a trend that persists and loses when it stalls, so a causal flag must be about persistence of the session move, not about the cell.

## Worst-20 P7 weeks of the 3.5 years (LPB_BASE trades)
| ISO week | P7 trades | net $ | StateCut share % | Asia share % | mean lots | mean atr_rel |
|---|---|---|---|---|---|---|
| 202644 | 40 | -43324 | 70 | 78 | 4.0 | 1.34 |
| 202411 | 19 | -41863 | 58 | 42 | 3.6 | 1.54 |
| 202528 | 25 | -34733 | 72 | 48 | 3.2 | 1.13 |
| 202331 | 26 | -31799 | 58 | 35 | 3.7 | 1.94 |
| 202436 | 35 | -31352 | 66 | 46 | 3.3 | 1.66 |
| 202515 | 73 | -30999 | 55 | 66 | 3.5 | 2.93 |
| 202329 | 14 | -29606 | 64 | 43 | 3.4 | 1.69 |
| 202604 | 24 | -29549 | 71 | 46 | 3.5 | 1.81 |
| 202409 | 24 | -28036 | 62 | 33 | 3.0 | 1.49 |
| 202517 | 32 | -27072 | 53 | 59 | 3.8 | 0.94 |
| 202541 | 22 | -25793 | 64 | 45 | 3.8 | 1.45 |
| 202434 | 20 | -24356 | 70 | 45 | 3.3 | 1.15 |
| 202533 | 16 | -24142 | 62 | 50 | 3.2 | 1.40 |
| 202447 | 16 | -23135 | 62 | 75 | 4.6 | 1.18 |
| 202318 | 10 | -22701 | 70 | 60 | 4.9 | 1.13 |
| 202428 | 15 | -22213 | 60 | 60 | 3.6 | 1.43 |
| 202631 | 42 | -21798 | 60 | 64 | 3.8 | 1.29 |
| 202606 | 39 | -21032 | 62 | 59 | 3.7 | 2.14 |
| 202326 | 21 | -19455 | 67 | 24 | 2.7 | 1.70 |
| 202346 | 16 | -18651 | 62 | 44 | 3.3 | 1.13 |

## The P7 table (every cell: all 3.5 years, L6M, the live week, and the share of the worst-20-week loss it carries)
Cell definitions: ER bucket = ER(20) of 5-min closes at the signal; atr_rel = 5-min ATR(14) / 20-day median of daily medians; LOT cold = P7 shadow Calmar over the previous 10 label days < 1.0; P7 order = 1st / 2nd / 3rd or later P7 signal of the same session-day; since last P7 exit = minutes between the previous P7 exit and this signal; side vs session move = (signal close minus first close of the session) x side in 5-min ATRs; K7/U7/M7 open = another of those books holds lots at the signal second, same side or opposite. The "exit" rows are outcomes, not features.

| cut | cell | n 3.5y | net $k | mean $/trade | win % | n L6M | net $k | mean | win % | n live wk | net $k | mean | win % | worst-20-wk net $k | share of worst-20 loss % |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| session | asia | 2246 | +719 | +320 | 45 | 558 | +202 | +362 | 47 | 31 | +69 | +2220 | 55 | -419 | 76 |
| session | london | 1520 | +224 | +147 | 45 | 330 | +58 | +175 | 47 | 15 | +0 | +9 | 40 | -76 | 14 |
| session | nyam | 1192 | -46 | -38 | 44 | 129 | -23 | -179 | 42 | 7 | +16 | +2266 | 71 | -57 | 10 |
| lots | 1 | 879 | +154 | +175 | 49 | 145 | +46 | +317 | 54 | 1 | +1 | +1195 | 100 | +1 | -0 |
| lots | 2 | 1212 | -99 | -82 | 40 | 232 | +1 | +4 | 42 | 7 | +1 | +148 | 43 | -44 | 8 |
| lots | 3 | 245 | +485 | +1979 | 74 | 42 | +102 | +2424 | 81 | 2 | +7 | +3590 | 100 | +44 | -8 |
| lots | 4 | 1764 | -243 | -138 | 40 | 394 | -32 | -81 | 42 | 24 | +8 | +351 | 42 | -238 | 43 |
| lots | 5 | 61 | +224 | +3678 | 79 | 15 | +80 | +5323 | 93 | 3 | +12 | +3946 | 67 | +34 | -6 |
| lots | 7 | 797 | +376 | +472 | 46 | 189 | +40 | +213 | 43 | 15 | +43 | +2879 | 60 | -349 | 63 |
| ER(20) 5-min | .15-.3 | 1454 | -57 | -39 | 42 | 311 | -32 | -102 | 42 | 19 | +19 | +1000 | 47 | -127 | 23 |
| ER(20) 5-min | .3-.45 | 1158 | +282 | +243 | 45 | 223 | +67 | +302 | 46 | 10 | +39 | +3876 | 60 | -181 | 33 |
| ER(20) 5-min | <.15 | 1463 | +252 | +172 | 45 | 331 | +131 | +397 | 50 | 15 | +11 | +754 | 53 | -30 | 5 |
| ER(20) 5-min | >.45 | 882 | +415 | +471 | 48 | 152 | +70 | +459 | 47 | 9 | +16 | +1749 | 56 | -213 | 39 |
| atr_rel | .8-1 | 785 | +344 | +438 | 48 | 218 | +185 | +849 | 52 | 5 | +17 | +3382 | 60 | -65 | 12 |
| atr_rel | 1-1.3 | 920 | +262 | +285 | 46 | 272 | +56 | +206 | 48 | 15 | +14 | +944 | 47 | -148 | 27 |
| atr_rel | 1.3-1.6 | 616 | +0 | +1 | 41 | 132 | +19 | +142 | 43 | 4 | +11 | +2856 | 75 | -108 | 20 |
| atr_rel | <.8 | 850 | +247 | +291 | 46 | 208 | +47 | +224 | 45 | 2 | +3 | +1683 | 50 | -109 | 20 |
| atr_rel | >1.6 | 1774 | +49 | +28 | 44 | 187 | -70 | -373 | 41 | 27 | +39 | +1443 | 52 | -122 | 22 |
| LOT state (Calmar10 of P7) | cold | 3000 | +707 | +236 | 45 | 600 | +214 | +357 | 47 | 53 | +85 | +1600 | 53 | -400 | 73 |
| LOT state (Calmar10 of P7) | na | 10 | +7 | +701 | 50 | 0 |  |  |  | 0 |  |  |  | +0 | -0 |
| LOT state (Calmar10 of P7) | warm | 1948 | +183 | +94 | 44 | 417 | +23 | +55 | 45 | 0 |  |  |  | -152 | 27 |
| P7 order in session | 1st | 2213 | +548 | +248 | 46 | 267 | +152 | +569 | 50 | 10 | +6 | +604 | 50 | -163 | 29 |
| P7 order in session | 2nd | 1349 | +198 | +147 | 43 | 242 | -26 | -106 | 41 | 10 | +35 | +3495 | 70 | -163 | 30 |
| P7 order in session | 3rd+ | 1396 | +151 | +108 | 44 | 508 | +110 | +217 | 47 | 33 | +44 | +1328 | 48 | -226 | 41 |
| since last P7 exit | 1-2h | 597 | +102 | +171 | 45 | 105 | +22 | +210 | 44 | 6 | -1 | -178 | 50 | -57 | 10 |
| since last P7 exit | 2-6h | 332 | +27 | +82 | 45 | 39 | -16 | -400 | 46 | 3 | +8 | +2594 | 67 | -19 | 3 |
| since last P7 exit | 30-60m | 971 | +14 | +14 | 43 | 230 | +34 | +150 | 47 | 11 | +21 | +1893 | 64 | -142 | 26 |
| since last P7 exit | <30m | 2351 | +436 | +185 | 45 | 529 | +75 | +142 | 45 | 29 | +53 | +1824 | 48 | -221 | 40 |
| since last P7 exit | >6h | 706 | +313 | +443 | 47 | 114 | +121 | +1059 | 54 | 4 | +4 | +1094 | 50 | -113 | 20 |
| last P7 trade | after_loss | 2736 | +346 | +127 | 44 | 547 | +68 | +124 | 45 | 26 | +53 | +2023 | 62 | -341 | 62 |
| last P7 trade | after_win | 2221 | +546 | +246 | 46 | 470 | +169 | +360 | 48 | 27 | +32 | +1193 | 44 | -211 | 38 |
| last P7 trade | none | 1 | +5 | +4795 | 100 | 0 |  |  |  | 0 |  |  |  | +0 | -0 |
| side vs session move | against<1 | 456 | -110 | -242 | 40 | 82 | +24 | +292 | 50 | 4 | +2 | +561 | 50 | -44 | 8 |
| side vs session move | against>1atr | 486 | +62 | +127 | 42 | 110 | +14 | +130 | 45 | 11 | +14 | +1269 | 45 | -95 | 17 |
| side vs session move | with<1 | 745 | +295 | +397 | 47 | 148 | +60 | +406 | 47 | 5 | +7 | +1462 | 60 | -50 | 9 |
| side vs session move | with>1atr | 3270 | +645 | +197 | 45 | 677 | +138 | +204 | 46 | 33 | +61 | +1858 | 55 | -362 | 66 |
| K7/U7/M7 open | KUM none | 1813 | +35 | +19 | 43 | 401 | +39 | +97 | 45 | 22 | +16 | +714 | 45 | -193 | 35 |
| K7/U7/M7 open | KUM opp only | 601 | +34 | +57 | 43 | 107 | +7 | +61 | 46 | 2 | +2 | +1131 | 50 | -109 | 20 |
| K7/U7/M7 open | KUM same | 2544 | +828 | +326 | 47 | 509 | +191 | +376 | 48 | 29 | +67 | +2305 | 59 | -249 | 45 |
| any other book open | any same | 2943 | +983 | +334 | 47 | 593 | +194 | +327 | 47 | 31 | +60 | +1946 | 55 | -354 | 64 |
| any other book open | none | 1445 | -91 | -63 | 42 | 320 | +39 | +122 | 45 | 20 | +22 | +1111 | 50 | -108 | 20 |
| any other book open | opp only | 570 | +5 | +9 | 42 | 104 | +4 | +37 | 45 | 2 | +2 | +1131 | 50 | -90 | 16 |
| side | long | 2480 | +442 | +178 | 45 | 465 | +58 | +125 | 43 | 23 | +35 | +1539 | 57 | -253 | 46 |
| side | short | 2478 | +455 | +184 | 45 | 552 | +179 | +324 | 49 | 30 | +49 | +1647 | 50 | -299 | 54 |
| exit | BookLock | 22 | -47 | -2125 | 0 | 11 | -22 | -2009 | 0 | 1 | -0 | -114 | 0 | -7 | 1 |
| exit | RollFlat | 13 | +1 | +63 | 69 | 2 | -0 | -159 | 50 | 0 |  |  |  | +0 | -0 |
| exit | StackCut | 10 | -17 | -1749 | 10 | 0 |  |  |  | 0 |  |  |  | -14 | 2 |
| exit | StateCut | 2564 | -7459 | -2909 | 0 | 519 | -1590 | -3064 | 0 | 24 | -74 | -3084 | 0 | -1061 | 192 |
| exit | Stop | 13 | -30 | -2276 | 15 | 3 | -3 | -972 | 33 | 0 |  |  |  | -12 | 2 |
| exit | StopJoin | 71 | -132 | -1857 | 0 | 10 | -25 | -2493 | 0 | 0 |  |  |  | -26 | 5 |
| exit | StopJoinFallback | 39 | -74 | -1887 | 0 | 3 | -5 | -1672 | 0 | 0 |  |  |  | -12 | 2 |
| exit | Target | 2186 | +8644 | +3954 | 100 | 468 | +1883 | +4023 | 100 | 28 | +159 | +5676 | 100 | +580 | -105 |
| exit | TimeBlock | 40 | +11 | +268 | 57 | 1 | -1 | -667 | 0 | 0 |  |  |  | +0 | -0 |

## Excess-loss ranking (worst-20 weeks of 3.5 years, then L6M worst-5 weeks; excess = worst-week net minus n_worst x cell mean in other weeks)
```
ALL 3.5y, worst-20 weeks, 1-way
             cell    n  n_worst  worst_mean  other_mean    excess  worst_net
      sess_n=asia 2246      284     -1475.0       580.0 -583742.0  -418993.0
       lot_b=cold 3000      405      -988.0       426.0 -572692.0  -399988.0
trend_b=with>1atr 3270      344     -1052.0       344.0 -480290.0  -361888.0
         lots_b=7  797       98     -3557.0      1037.0 -450160.0  -348544.0
prev_b=after_loss 2736      354      -962.0       288.0 -442668.0  -340582.0
     side_b=short 2478      282     -1060.0       343.0 -395715.0  -298927.0
   kum_b=KUM same 2544      258      -966.0       471.0 -370985.0  -249355.0
      side_b=long 2480      247     -1023.0       311.0 -329547.0  -252686.0
       gap_b=<30m 2351      260      -848.0       314.0 -302180.0  -220536.0
        er_b=>.45  882       94     -2269.0       798.0 -288243.0  -213252.0
       ord_b=3rd+ 1396      183     -1233.0       310.0 -282388.0  -225567.0
 prev_b=after_win 2221      175     -1206.0       370.0 -275766.0  -211031.0
         lots_b=4 1764      192     -1240.0        -3.0 -237542.0  -238162.0
        ord_b=1st 2213      209      -779.0       355.0 -236837.0  -162714.0
ALL 3.5y, worst-20 weeks, 2-way
                              cell    n  n_worst  worst_mean  other_mean    excess  worst_net
          sess_n=asia & lot_b=cold 1364      220     -1449.0       755.0 -484876.0  -318692.0
            sess_n=asia & lots_b=7  797       98     -3557.0      1037.0 -450160.0  -348544.0
             lots_b=7 & lot_b=cold  486       80     -3608.0      1426.0 -402760.0  -288674.0
   sess_n=asia & trend_b=with>1atr 1228      161     -1620.0       704.0 -374179.0  -260899.0
   sess_n=asia & prev_b=after_loss 1312      189     -1427.0       516.0 -367182.0  -269699.0
    lot_b=cold & prev_b=after_loss 1663      269      -920.0       423.0 -361136.0  -247353.0
    lot_b=cold & trend_b=with>1atr 1960      263      -954.0       361.0 -346043.0  -251027.0
      lots_b=7 & trend_b=with>1atr  549       70     -3513.0      1142.0 -325871.0  -245914.0
        sess_n=asia & side_b=short 1129      158     -1348.0       658.0 -317066.0  -213047.0
         lot_b=cold & side_b=short 1551      219      -970.0       473.0 -316124.0  -212489.0
      sess_n=asia & kum_b=KUM same  934      108     -1676.0       941.0 -282620.0  -180976.0
  trend_b=with>1atr & side_b=short 1697      197     -1023.0       387.0 -277749.0  -201439.0
         sess_n=asia & side_b=long 1117      126     -1634.0       503.0 -269379.0  -205946.0
  prev_b=after_loss & side_b=short 1372      185     -1016.0       429.0 -267331.0  -188045.0
          lot_b=cold & side_b=long 1449      186     -1008.0       377.0 -257636.0  -187499.0
    gap_b=<30m & trend_b=with>1atr 1832      198      -890.0       399.0 -255264.0  -176280.0
       lot_b=cold & kum_b=KUM same 1532      199      -745.0       538.0 -255199.0  -148224.0
prev_b=after_loss & kum_b=KUM same 1353      167     -1045.0       458.0 -251030.0  -174556.0
L6M worst-5 weeks, 1-way
             cell   n  n_worst  worst_mean  other_mean    excess  worst_net
trend_b=with>1atr 677      122      -911.0       450.0 -166036.0  -111167.0
     side_b=short 552       97     -1049.0       616.0 -161562.0  -101776.0
       gap_b=<30m 529       80     -1399.0       416.0 -145232.0  -111916.0
      sess_n=asia 558      116      -629.0       623.0 -145176.0   -72958.0
       lot_b=cold 600      105      -642.0       568.0 -127087.0   -67405.0
       ord_b=3rd+ 508       86      -970.0       459.0 -122917.0   -83412.0
 prev_b=after_win 470       58     -1043.0       557.0  -92833.0   -60505.0
         lots_b=7 189       38     -1676.0       689.0  -89844.0   -63675.0
prev_b=after_loss 547      113      -495.0       285.0  -88141.0   -55958.0
   kum_b=KUM none 401       68      -973.0       315.0  -87606.0   -66183.0
        er_b=>.45 152       29     -1557.0       934.0  -72251.0   -45160.0
       lot_b=warm 417       66      -743.0       205.0  -62575.0   -49058.0
L6M worst-5 weeks, 2-way
                              cell   n  n_worst  worst_mean  other_mean    excess  worst_net
        sess_n=asia & side_b=short 308       65     -1175.0       956.0 -138509.0   -76382.0
    gap_b=<30m & trend_b=with>1atr 398       62     -1688.0       391.0 -128931.0  -104671.0
  trend_b=with>1atr & side_b=short 393       73     -1117.0       648.0 -128847.0   -81512.0
   sess_n=asia & trend_b=with>1atr 352       77      -871.0       736.0 -123797.0   -67099.0
          sess_n=asia & gap_b=<30m 283       55     -1622.0       614.0 -122981.0   -89221.0
          sess_n=asia & ord_b=3rd+ 311       66     -1065.0       665.0 -114204.0   -70291.0
          sess_n=asia & lot_b=cold 339       74      -663.0       863.0 -112904.0   -49035.0
trend_b=with>1atr & kum_b=KUM none 275       51     -1768.0       442.0 -112705.0   -90176.0
         lot_b=cold & side_b=short 350       63     -1069.0       693.0 -111033.0   -67366.0
    lot_b=cold & trend_b=with>1atr 390       71     -1003.0       435.0 -102081.0   -71186.0
      lots_b=7 & trend_b=with>1atr 150       30     -2426.0       876.0  -99061.0   -72781.0
         ord_b=3rd+ & side_b=short 297       54     -1182.0       636.0  -98174.0   -63814.0
P7 trades per week mean n worst20 vs other: 26.45 26.520958083832337
stop/cut rate worst vs other 0.6238185255198487 0.5044027997290584
        size                                     sum                                              
lots_b     1     2     3      4     5      7       1        2        3        4        5         7
half                                                                                              
2023H1   NaN   9.0   3.0   34.0   NaN   29.0     NaN   1628.0  -1922.0 -26218.0      NaN   -7164.0
2023H2   4.0  19.0   7.0   76.0   3.0   56.0  1670.0    518.0  -5627.0 -60299.0   2257.0   -5171.0
2024H1   1.0  18.0   8.0   86.0  11.0   60.0 -1629.0   5910.0   8593.0 -11058.0  45698.0   11054.0
2024H2   3.0  29.0   8.0  136.0  11.0   90.0  1982.0 -28992.0  28777.0  75073.0  35835.0   -4765.0
2025H1  12.0  25.0  22.0  168.0   7.0  145.0  1621.0  -1620.0  72417.0 -76278.0  21901.0  104756.0
2025H2   3.0  22.0  
```

## Open questions for the rest of Part C
Caveats: cells overlap heavily (Asia, 7 lots, cold and with-trend are mostly the same trades), so the excess ranking says where the loss sits, not which flag is causal; LOT cold uses the LPB shadow Calmar (no JN04 gating), and in the live week the Calmar history is the LPB list to 10-30 plus the 11-02..05 live trades (11-01..2 gap); live week trades have no layer features beyond what the signal second gives (no NTZ/zone state).
Running now (exact, JN04RM base, one set per job via jbjobs, 1 worker): C3 blackout sets WC3_S60, S15, S120, B30, B60, then C2 sets WC2_A5, A4, A6, L5, STKA (7/4/4 Asia lots 5/4/6, London 5, STACK on Asia+London). Next: first-order flag-conditional blackout screen from this table; rest-of-session hook; C4 spec.

