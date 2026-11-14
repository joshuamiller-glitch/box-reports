# DS3_SURVIVORS_S6 - S6 desk-state cap, "stop trying when behind" (W-S), page 2026-11-14 04:45Z; Shadow only, no PASS claim; recents first, PRE/X' tolerant per rule 2a

Rule: skip every NEW entry of every book once the stack has closed >= N trades in the label day (17:00 ET roll) AND the stack day P&L is <= -2 R. Hook code/th_screens/scr_hooks.py (feature conj), one set per job, TP engine. Cells JN05W_S6_C22 / C18 / C14 on the live panel base (reference LPB_BASE) and JN05W_S6_C22_RM / C18_RM / C14_RM on JN04RM. The first-order screen (3.5 years, LPB trade list) is in DS3_SCREENS.md. Months present are stated per cell; a window is scored only when all its months are present.

## JN05W_S6_C22 (stack closes today >= 22 AND stack day P&L <= -2 R (R = $1,200)) vs LPB_BASE (live panel base) - 43 of 43 months present
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | 42.4 | +11328 | 29541 | 51253 | 12 / 1 |
| L3M | 43.9 | +7529 | 43357 | 77224 | 223 / 155 |
| L6M | 43.9 | +3078 | 43357 | 77224 | 130 / 102 |
| HOLD | 10.9 | +2543 | 70281 | 78842 | -297 / -377 |
| PRE | 14.4 | +491 | 85153 | 99479 | -501 / -529 |
| X' | 0.0 | +0 | 122553 | 122553 | -321 / -321 |
| GAP 2025-07..10 | 0.0 | +424 | 24853 | 24853 | |

Bi-weekly WF (re-pick every 2 weeks, purged; for a fixed rule this is the fixed rule judged block by block): maxDD cut 14.4 %, d mean +677 $/wk, beat live in 44 % of refit periods.
Rule-2a label: **OK-PRIOR**.
TREND-WEEK CLAUSE (L6M, ): the reference's 5 best weeks sum to $+331449 and the cell's same weeks to $+344869; winning weeks turned losing: 2 of 19; $ given up inside winning weeks: -83487; sum of the 20 worst weeks cell +183845 vs ref +154669.
TREND-WEEK CLAUSE (HOLD, ): the reference's 5 best weeks sum to $+376655 and the cell's same weeks to $+389560; winning weeks turned losing: 2 of 37; $ given up inside winning weeks: -101033; sum of the 20 worst weeks cell -289670 vs ref -370271.
TREND-WEEK CLAUSE (all 3.5 years, ): the reference's 5 best weeks sum to $+458167 and the cell's same weeks to $+442882; winning weeks turned losing: 3 of 123; $ given up inside winning weeks: -127206; sum of the 20 worst weeks cell -776505 vs ref -869001.

## JN05W_S6_C22_RM (stack closes today >= 22 AND stack day P&L <= -2 R (R = $1,200)) vs JN04RM (dials on) - 43 of 43 months present
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | 53.5 | +4828 | 12571 | 27056 | 18 / 15 |
| L3M | 24.6 | +4048 | 31434 | 41699 | 200 / 164 |
| L6M | 5.9 | +2612 | 39221 | 41699 | 169 / 138 |
| HOLD | 25.4 | +2067 | 54311 | 72757 | -223 / -285 |
| PRE | 32.4 | +39 | 45095 | 66714 | -312 / -328 |
| X' | 0.0 | +0 | 64077 | 64077 | -222 / -222 |
| GAP 2025-07..10 | 0.0 | +280 | 23701 | 23701 | |

Bi-weekly WF (re-pick every 2 weeks, purged; for a fixed rule this is the fixed rule judged block by block): maxDD cut 0.0 %, d mean +346 $/wk, beat live in 25 % of refit periods.
Rule-2a label: **OK-PRIOR**.
TREND-WEEK CLAUSE (L6M, ): the reference's 5 best weeks sum to $+299107 and the cell's same weeks to $+317127; winning weeks turned losing: 0 of 19; $ given up inside winning weeks: -45556; sum of the 20 worst weeks cell +212515 vs ref +180775.
TREND-WEEK CLAUSE (HOLD, ): the reference's 5 best weeks sum to $+323722 and the cell's same weeks to $+326680; winning weeks turned losing: 2 of 36; $ given up inside winning weeks: -73477; sum of the 20 worst weeks cell -217029 vs ref -281405.
TREND-WEEK CLAUSE (all 3.5 years, ): the reference's 5 best weeks sum to $+347086 and the cell's same weeks to $+339823; winning weeks turned losing: 2 of 118; $ given up inside winning weeks: -105884; sum of the 20 worst weeks cell -526475 vs ref -560640.

## JN05W_S6_C22V19 (V19 reading: trades OPENED since the roll >= 22 AND realised day P&L <= -2 R) vs LPB_BASE (live panel base) - 43 of 43 months present
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | 45.0 | -2598 | 28201 | 51253 | 17 / 1 |
| L3M | 45.7 | +5305 | 41961 | 77224 | 242 / 155 |
| L6M | 45.7 | +3289 | 41961 | 77224 | 127 / 102 |
| HOLD | 8.5 | +2527 | 72147 | 78842 | -306 / -377 |
| PRE | 14.2 | +348 | 85371 | 99479 | -511 / -529 |
| X' | -7.0 | +28 | 131185 | 122553 | -329 / -321 |
| GAP 2025-07..10 | 0.0 | +353 | 24853 | 24853 | |

Bi-weekly WF (re-pick every 2 weeks, purged; for a fixed rule this is the fixed rule judged block by block): maxDD cut 14.2 %, d mean +494 $/wk, beat live in 35 % of refit periods.
Rule-2a label: **OK-PRIOR**.
TREND-WEEK CLAUSE (L6M, ): the reference's 5 best weeks sum to $+331449 and the cell's same weeks to $+347166; winning weeks turned losing: 2 of 19; $ given up inside winning weeks: -94825; sum of the 20 worst weeks cell +180747 vs ref +154669.
TREND-WEEK CLAUSE (HOLD, ): the reference's 5 best weeks sum to $+376655 and the cell's same weeks to $+389080; winning weeks turned losing: 2 of 37; $ given up inside winning weeks: -116636; sum of the 20 worst weeks cell -299350 vs ref -370271.
TREND-WEEK CLAUSE (all 3.5 years, ): the reference's 5 best weeks sum to $+458167 and the cell's same weeks to $+441802; winning weeks turned losing: 3 of 123; $ given up inside winning weeks: -144631; sum of the 20 worst weeks cell -782234 vs ref -869001.

## JN05W_S6_C22V19_RM (V19 reading: trades OPENED since the roll >= 22 AND realised day P&L <= -2 R) vs JN04RM (dials on) - 43 of 43 months present
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | 62.0 | +5594 | 10275 | 27056 | 20 / 15 |
| L3M | 14.6 | +3787 | 35592 | 41699 | 197 / 164 |
| L6M | 8.5 | +2307 | 38141 | 41699 | 161 / 138 |
| HOLD | 27.6 | +1940 | 52666 | 72757 | -221 / -285 |
| PRE | 35.0 | +95 | 43360 | 66714 | -308 / -328 |
| X' | 0.0 | +0 | 64077 | 64077 | -222 / -222 |
| GAP 2025-07..10 | 0.0 | +154 | 23701 | 23701 | |

Bi-weekly WF (re-pick every 2 weeks, purged; for a fixed rule this is the fixed rule judged block by block): maxDD cut 27.6 %, d mean +600 $/wk, beat live in 38 % of refit periods.
Rule-2a label: **OK-PRIOR**.
TREND-WEEK CLAUSE (L6M, ): the reference's 5 best weeks sum to $+299107 and the cell's same weeks to $+316662; winning weeks turned losing: 0 of 19; $ given up inside winning weeks: -54130; sum of the 20 worst weeks cell +205344 vs ref +180775.
TREND-WEEK CLAUSE (HOLD, ): the reference's 5 best weeks sum to $+323722 and the cell's same weeks to $+326215; winning weeks turned losing: 2 of 36; $ given up inside winning weeks: -86364; sum of the 20 worst weeks cell -215041 vs ref -281405.
TREND-WEEK CLAUSE (all 3.5 years, ): the reference's 5 best weeks sum to $+347086 and the cell's same weeks to $+340196; winning weeks turned losing: 2 of 118; $ given up inside winning weeks: -122020; sum of the 20 worst weeks cell -522574 vs ref -560640.

## JN05W_S6_C18 (stack closes today >= 18 AND stack day P&L <= -2 R) vs LPB_BASE (live panel base) - 43 of 43 months present
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | 40.9 | -3002 | 30299 | 51253 | 13 / 1 |
| L3M | 48.1 | +5306 | 40054 | 77224 | 240 / 155 |
| L6M | 48.1 | +2654 | 40054 | 77224 | 118 / 102 |
| HOLD | 16.6 | +2037 | 65763 | 78842 | -310 / -377 |
| PRE | 20.4 | +352 | 79203 | 99479 | -493 / -529 |
| X' | -10.4 | +0 | 135331 | 122553 | -332 / -321 |
| GAP 2025-07..10 | -14.7 | -573 | 28509 | 24853 | |

Bi-weekly WF (re-pick every 2 weeks, purged; for a fixed rule this is the fixed rule judged block by block): maxDD cut 16.2 %, d mean +367 $/wk, beat live in 44 % of refit periods.
Rule-2a label: **OK-PRIOR**.
TREND-WEEK CLAUSE (L6M, ): the reference's 5 best weeks sum to $+331449 and the cell's same weeks to $+340975; winning weeks turned losing: 2 of 19; $ given up inside winning weeks: -117036; sum of the 20 worst weeks cell +168780 vs ref +154669.
TREND-WEEK CLAUSE (HOLD, ): the reference's 5 best weeks sum to $+376655 and the cell's same weeks to $+384330; winning weeks turned losing: 3 of 37; $ given up inside winning weeks: -158721; sum of the 20 worst weeks cell -305271 vs ref -370271.
TREND-WEEK CLAUSE (all 3.5 years, ): the reference's 5 best weeks sum to $+458167 and the cell's same weeks to $+440794; winning weeks turned losing: 4 of 123; $ given up inside winning weeks: -238322; sum of the 20 worst weeks cell -767929 vs ref -869001.

## JN05W_S6_C18_RM (stack closes today >= 18 AND stack day P&L <= -2 R) vs JN04RM (dials on) - 43 of 43 months present
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | 65.0 | +5862 | 9469 | 27056 | 21 / 15 |
| L3M | 15.1 | +1387 | 35386 | 41699 | 194 / 164 |
| L6M | 15.1 | +2386 | 35386 | 41699 | 158 / 138 |
| HOLD | 36.1 | +2351 | 46484 | 72757 | -213 / -285 |
| PRE | 45.4 | -31 | 36447 | 66714 | -292 / -328 |
| X' | -1.7 | -47 | 65178 | 64077 | -225 / -222 |
| GAP 2025-07..10 | -15.4 | -1067 | 27357 | 23701 | |

Bi-weekly WF (re-pick every 2 weeks, purged; for a fixed rule this is the fixed rule judged block by block): maxDD cut 36.1 %, d mean +533 $/wk, beat live in 39 % of refit periods.
Rule-2a label: **OK-PRIOR**.
TREND-WEEK CLAUSE (L6M, ): the reference's 5 best weeks sum to $+299107 and the cell's same weeks to $+317388; winning weeks turned losing: 1 of 19; $ given up inside winning weeks: -54762; sum of the 20 worst weeks cell +201806 vs ref +180775.
TREND-WEEK CLAUSE (HOLD, ): the reference's 5 best weeks sum to $+323722 and the cell's same weeks to $+323147; winning weeks turned losing: 3 of 36; $ given up inside winning weeks: -93133; sum of the 20 worst weeks cell -209057 vs ref -281405.
TREND-WEEK CLAUSE (all 3.5 years, ): the reference's 5 best weeks sum to $+347086 and the cell's same weeks to $+337128; winning weeks turned losing: 4 of 118; $ given up inside winning weeks: -189734; sum of the 20 worst weeks cell -499190 vs ref -560640.

## JN05W_S6_C14 (stack closes today >= 14 AND stack day P&L <= -2 R) vs LPB_BASE (live panel base) - 43 of 43 months present
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | 51.0 | -838 | 25105 | 51253 | 25 / 1 |
| L3M | 13.1 | +4036 | 67129 | 77224 | 230 / 155 |
| L6M | 13.1 | +2149 | 67129 | 77224 | 92 / 102 |
| HOLD | 12.0 | +1539 | 69365 | 78842 | -315 / -377 |
| PRE | 18.4 | +196 | 81184 | 99479 | -480 / -529 |
| X' | -5.2 | +236 | 128919 | 122553 | -326 / -321 |
| GAP 2025-07..10 | -26.1 | -404 | 31341 | 24853 | |

Bi-weekly WF (re-pick every 2 weeks, purged; for a fixed rule this is the fixed rule judged block by block): maxDD cut -14.0 %, d mean -72 $/wk, beat live in 49 % of refit periods.
Rule-2a label: **OK-PRIOR**.
TREND-WEEK CLAUSE (L6M, ): the reference's 5 best weeks sum to $+331449 and the cell's same weeks to $+338108; winning weeks turned losing: 2 of 19; $ given up inside winning weeks: -132998; sum of the 20 worst weeks cell +139761 vs ref +154669.
TREND-WEEK CLAUSE (HOLD, ): the reference's 5 best weeks sum to $+376655 and the cell's same weeks to $+383084; winning weeks turned losing: 3 of 37; $ given up inside winning weeks: -202061; sum of the 20 worst weeks cell -312029 vs ref -370271.
TREND-WEEK CLAUSE (all 3.5 years, ): the reference's 5 best weeks sum to $+458167 and the cell's same weeks to $+439683; winning weeks turned losing: 6 of 123; $ given up inside winning weeks: -357828; sum of the 20 worst weeks cell -707294 vs ref -869001.

## JN05W_S6_C14_RM (stack closes today >= 14 AND stack day P&L <= -2 R) vs JN04RM (dials on) - 43 of 43 months present
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | 85.2 | +993 | 4012 | 27056 | 35 / 15 |
| L3M | -17.8 | +1071 | 49103 | 41699 | 193 / 164 |
| L6M | -17.8 | +2326 | 49103 | 41699 | 145 / 138 |
| HOLD | 7.7 | +1925 | 67178 | 72757 | -242 / -285 |
| PRE | -0.5 | -745 | 67056 | 66714 | -308 / -328 |
| X' | -15.8 | -191 | 74226 | 64077 | -232 / -222 |
| GAP 2025-07..10 | -27.4 | -1133 | 30188 | 23701 | |

Bi-weekly WF (re-pick every 2 weeks, purged; for a fixed rule this is the fixed rule judged block by block): maxDD cut 7.7 %, d mean -45 $/wk, beat live in 39 % of refit periods.
Rule-2a label: **OK-PRIOR**.
TREND-WEEK CLAUSE (L6M, ): the reference's 5 best weeks sum to $+299107 and the cell's same weeks to $+315865; winning weeks turned losing: 2 of 19; $ given up inside winning weeks: -87063; sum of the 20 worst weeks cell +190281 vs ref +180775.
TREND-WEEK CLAUSE (HOLD, ): the reference's 5 best weeks sum to $+323722 and the cell's same weeks to $+318013; winning weeks turned losing: 6 of 36; $ given up inside winning weeks: -149906; sum of the 20 worst weeks cell -237420 vs ref -281405.
TREND-WEEK CLAUSE (all 3.5 years, ): the reference's 5 best weeks sum to $+347086 and the cell's same weeks to $+334385; winning weeks turned losing: 7 of 118; $ given up inside winning weeks: -345792; sum of the 20 worst weeks cell -503655 vs ref -560640.

## Acceptance test (acceptance_p7.py; judged on the months present, stated by the tool)
### JN05W_S6_C22
```
ACCEPTANCE P7 JN05W_S6_C22  2026-11-14 04:45Z   (months 43: 202304..202610; reference LPB_BASE months 43)
| scope | who | sessions | max run | p95 | mean | sessions with run>=3 | n 3rd+ losers | $ lost on 3rd+ losers | entries 3rd+ attempt without new evidence (n / $) | losing 3rd+ no-evidence violations | bigger 2nd attempts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| all P7 | LPB_BASE (live ref) | 2213 | 6 | 2.0 | 0.89 | 48 | 57 | -136326 | 90 / -11382 | 53 | 110 |
| all P7 | JN05W_S6_C22 | 2167 | 6 | 2.0 | 0.88 | 43 | 52 | -127578 | 80 / -14617 | 48 | 99 |
| Asia | LPB_BASE (live ref) | 919 | 6 | 2.0 | 0.90 | 21 | 26 | -80482 | 37 / -10876 | 24 | 33 |
| Asia | JN05W_S6_C22 | 919 | 6 | 2.0 | 0.90 | 20 | 25 | -78772 | 36 / -9166 | 23 | 33 |
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +28883 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +23369 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +23252 (7 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +22466 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +22396 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 1 ($+8402); all re-entry winners (any evidence) reference 13, set 13
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)
SUMMARY JN05W_S6_C22: fails 3 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT JN05W_S6_C22 FAIL fails=3/20
```
### JN05W_S6_C22_RM
```
ACCEPTANCE P7 JN05W_S6_C22_RM  2026-11-14 04:45Z   (months 43: 202304..202610; reference LPB_BASE months 43)
| scope | who | sessions | max run | p95 | mean | sessions with run>=3 | n 3rd+ losers | $ lost on 3rd+ losers | entries 3rd+ attempt without new evidence (n / $) | losing 3rd+ no-evidence violations | bigger 2nd attempts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| all P7 | LPB_BASE (live ref) | 2213 | 6 | 2.0 | 0.89 | 48 | 57 | -136326 | 90 / -11382 | 53 | 110 |
| all P7 | JN05W_S6_C22_RM | 2377 | 6 | 2.0 | 0.91 | 63 | 78 | -83703 | 128 / +3843 | 75 | 54 |
| Asia | LPB_BASE (live ref) | 919 | 6 | 2.0 | 0.90 | 21 | 26 | -80482 | 37 / -10876 | 24 | 33 |
| Asia | JN05W_S6_C22_RM | 918 | 6 | 2.0 | 0.93 | 25 | 34 | -44546 | 60 / +9722 | 32 | 41 |
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +22883 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +11869 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +12634 (9 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +9563 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +12231 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 1 ($+4790); all re-entry winners (any evidence) reference 13, set 14
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)
SUMMARY JN05W_S6_C22_RM: fails 4 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT JN05W_S6_C22_RM FAIL fails=4/20
```
### JN05W_S6_C22V19
```
ACCEPTANCE P7 JN05W_S6_C22V19  2026-11-14 04:45Z   (months 43: 202304..202610; reference LPB_BASE months 43)
| scope | who | sessions | max run | p95 | mean | sessions with run>=3 | n 3rd+ losers | $ lost on 3rd+ losers | entries 3rd+ attempt without new evidence (n / $) | losing 3rd+ no-evidence violations | bigger 2nd attempts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| all P7 | LPB_BASE (live ref) | 2213 | 6 | 2.0 | 0.89 | 48 | 57 | -136326 | 90 / -11382 | 53 | 110 |
| all P7 | JN05W_S6_C22V19 | 2168 | 6 | 2.0 | 0.88 | 42 | 51 | -125984 | 79 / -13022 | 47 | 98 |
| Asia | LPB_BASE (live ref) | 919 | 6 | 2.0 | 0.90 | 21 | 26 | -80482 | 37 / -10876 | 24 | 33 |
| Asia | JN05W_S6_C22V19 | 919 | 6 | 2.0 | 0.90 | 20 | 25 | -78772 | 36 / -9166 | 23 | 33 |
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +28883 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +23369 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +23252 (7 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +22466 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +22396 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 1 ($+8402); all re-entry winners (any evidence) reference 13, set 13
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)
SUMMARY JN05W_S6_C22V19: fails 3 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT JN05W_S6_C22V19 FAIL fails=3/20
```
### JN05W_S6_C22V19_RM
```
ACCEPTANCE P7 JN05W_S6_C22V19_RM  2026-11-14 04:46Z   (months 43: 202304..202610; reference LPB_BASE months 43)
| scope | who | sessions | max run | p95 | mean | sessions with run>=3 | n 3rd+ losers | $ lost on 3rd+ losers | entries 3rd+ attempt without new evidence (n / $) | losing 3rd+ no-evidence violations | bigger 2nd attempts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| all P7 | LPB_BASE (live ref) | 2213 | 6 | 2.0 | 0.89 | 48 | 57 | -136326 | 90 / -11382 | 53 | 110 |
| all P7 | JN05W_S6_C22V19_RM | 2371 | 6 | 2.0 | 0.91 | 63 | 78 | -83703 | 127 / +1446 | 75 | 52 |
| Asia | LPB_BASE (live ref) | 919 | 6 | 2.0 | 0.90 | 21 | 26 | -80482 | 37 / -10876 | 24 | 33 |
| Asia | JN05W_S6_C22V19_RM | 918 | 6 | 2.0 | 0.93 | 25 | 34 | -44546 | 60 / +9722 | 32 | 40 |
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +22883 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +11869 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +12634 (9 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +9563 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +12231 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 1 ($+4790); all re-entry winners (any evidence) reference 13, set 14
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)
SUMMARY JN05W_S6_C22V19_RM: fails 4 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT JN05W_S6_C22V19_RM FAIL fails=4/20
```
### JN05W_S6_C18
```
ACCEPTANCE P7 JN05W_S6_C18  2026-11-14 04:46Z   (months 43: 202304..202610; reference LPB_BASE months 43)
| scope | who | sessions | max run | p95 | mean | sessions with run>=3 | n 3rd+ losers | $ lost on 3rd+ losers | entries 3rd+ attempt without new evidence (n / $) | losing 3rd+ no-evidence violations | bigger 2nd attempts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| all P7 | LPB_BASE (live ref) | 2213 | 6 | 2.0 | 0.89 | 48 | 57 | -136326 | 90 / -11382 | 53 | 110 |
| all P7 | JN05W_S6_C18 | 2138 | 6 | 2.0 | 0.87 | 41 | 50 | -122780 | 76 / -14614 | 46 | 91 |
| Asia | LPB_BASE (live ref) | 919 | 6 | 2.0 | 0.90 | 21 | 26 | -80482 | 37 / -10876 | 24 | 33 |
| Asia | JN05W_S6_C18 | 919 | 6 | 2.0 | 0.90 | 19 | 24 | -75569 | 35 / -5963 | 22 | 33 |
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +28883 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +23369 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +23252 (7 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +22466 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +22396 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 1 ($+8402); all re-entry winners (any evidence) reference 13, set 13
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)
SUMMARY JN05W_S6_C18: fails 3 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT JN05W_S6_C18 FAIL fails=3/20
```
### JN05W_S6_C18_RM
```
ACCEPTANCE P7 JN05W_S6_C18_RM  2026-11-14 04:46Z   (months 43: 202304..202610; reference LPB_BASE months 43)
| scope | who | sessions | max run | p95 | mean | sessions with run>=3 | n 3rd+ losers | $ lost on 3rd+ losers | entries 3rd+ attempt without new evidence (n / $) | losing 3rd+ no-evidence violations | bigger 2nd attempts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| all P7 | LPB_BASE (live ref) | 2213 | 6 | 2.0 | 0.89 | 48 | 57 | -136326 | 90 / -11382 | 53 | 110 |
| all P7 | JN05W_S6_C18_RM | 2341 | 6 | 2.0 | 0.90 | 61 | 75 | -80384 | 122 / +1163 | 72 | 50 |
| Asia | LPB_BASE (live ref) | 919 | 6 | 2.0 | 0.90 | 21 | 26 | -80482 | 37 / -10876 | 24 | 33 |
| Asia | JN05W_S6_C18_RM | 918 | 6 | 2.0 | 0.93 | 25 | 33 | -42986 | 58 / +8879 | 31 | 40 |
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +22883 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +11869 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +12634 (9 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +9563 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +12231 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 1 ($+4790); all re-entry winners (any evidence) reference 13, set 14
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)
SUMMARY JN05W_S6_C18_RM: fails 4 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT JN05W_S6_C18_RM FAIL fails=4/20
```
### JN05W_S6_C14
```
ACCEPTANCE P7 JN05W_S6_C14  2026-11-14 04:46Z   (months 43: 202304..202610; reference LPB_BASE months 43)
| scope | who | sessions | max run | p95 | mean | sessions with run>=3 | n 3rd+ losers | $ lost on 3rd+ losers | entries 3rd+ attempt without new evidence (n / $) | losing 3rd+ no-evidence violations | bigger 2nd attempts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| all P7 | LPB_BASE (live ref) | 2213 | 6 | 2.0 | 0.89 | 48 | 57 | -136326 | 90 / -11382 | 53 | 110 |
| all P7 | JN05W_S6_C14 | 2092 | 6 | 2.0 | 0.86 | 38 | 46 | -112639 | 72 / -7411 | 43 | 84 |
| Asia | LPB_BASE (live ref) | 919 | 6 | 2.0 | 0.90 | 21 | 26 | -80482 | 37 / -10876 | 24 | 33 |
| Asia | JN05W_S6_C14 | 919 | 6 | 2.0 | 0.90 | 18 | 23 | -69783 | 34 / -177 | 21 | 33 |
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +28883 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +23369 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +23252 (7 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +22466 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +22396 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 1 ($+8402); all re-entry winners (any evidence) reference 13, set 10
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)
SUMMARY JN05W_S6_C14: fails 3 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT JN05W_S6_C14 FAIL fails=3/20
```
### JN05W_S6_C14_RM
```
ACCEPTANCE P7 JN05W_S6_C14_RM  2026-11-14 04:47Z   (months 43: 202304..202610; reference LPB_BASE months 43)
| scope | who | sessions | max run | p95 | mean | sessions with run>=3 | n 3rd+ losers | $ lost on 3rd+ losers | entries 3rd+ attempt without new evidence (n / $) | losing 3rd+ no-evidence violations | bigger 2nd attempts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| all P7 | LPB_BASE (live ref) | 2213 | 6 | 2.0 | 0.89 | 48 | 57 | -136326 | 90 / -11382 | 53 | 110 |
| all P7 | JN05W_S6_C14_RM | 2286 | 6 | 2.0 | 0.89 | 57 | 69 | -74389 | 115 / +5959 | 66 | 49 |
| Asia | LPB_BASE (live ref) | 919 | 6 | 2.0 | 0.90 | 21 | 26 | -80482 | 37 / -10876 | 24 | 33 |
| Asia | JN05W_S6_C14_RM | 918 | 6 | 2.0 | 0.92 | 23 | 29 | -38808 | 54 / +13058 | 27 | 41 |
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +22883 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +11869 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +12634 (9 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +9563 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +12231 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 1 ($+4790); all re-entry winners (any evidence) reference 13, set 14
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)
SUMMARY JN05W_S6_C14_RM: fails 4 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT JN05W_S6_C14_RM FAIL fails=4/20
```
## Behavioural scorecard (items a-e, W-Q tool)
### JN05W_S6_C22 (ref LPB_BASE)
```
JN05W_S6_C22 L6M (stack, per week): full stops 20.3/wk $-33387; give-backs 7.7/wk (7.6 round-trips) realised $-12041, forgone vs target $31027; same-side losing runs max 12, p95 6, $-46529 lost on 3rd-and-later; no-new-evidence re-entries 30.4/wk $-835; recoveries cut 11.5/wk $41517, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $15685/wk, losers avoided $17456/wk, net +1760 $/wk; pnl $21544/wk.
JN05W_S6_C22 HOLD (stack, per week): full stops 20.0/wk $-33171; give-backs 7.1/wk (6.9 round-trips) realised $-11035, forgone vs target $28123; same-side losing runs max 12, p95 6, $-39520 lost on 3rd-and-later; no-new-evidence re-entries 24.6/wk $715; recoveries cut 10.3/wk $36841, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $11306/wk, losers avoided $13210/wk, net +1898 $/wk; pnl $17250/wk.
JN05W_S6_C22 PRE (stack, per week): full stops 16.0/wk $-27560; give-backs 4.8/wk (4.4 round-trips) realised $-7191, forgone vs target $18441; same-side losing runs max 7, p95 4, $-21131 lost on 3rd-and-later; no-new-evidence re-entries 11.0/wk $336; recoveries cut 6.0/wk $20725, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $3779/wk, losers avoided $4578/wk, net +816 $/wk; pnl $12698/wk.
JN05W_S6_C22 X' (stack, per week): full stops 17.5/wk $-28195; give-backs 3.6/wk (3.0 round-trips) realised $-4902, forgone vs target $12802; same-side losing runs max 7, p95 4, $-12302 lost on 3rd-and-later; no-new-evidence re-entries 2.7/wk $569; recoveries cut 2.5/wk $9968, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $0/wk, losers avoided $-0/wk, net +0 $/wk; pnl $1342/wk.

```
### JN05W_S6_C22_RM (ref JN04RM)
```
JN05W_S6_C22_RM L6M (stack, per week): full stops 20.7/wk $-31442; give-backs 8.1/wk (8.0 round-trips) realised $-9419, forgone vs target $23764; same-side losing runs max 11, p95 6, $-36548 lost on 3rd-and-later; no-new-evidence re-entries 33.9/wk $1462; recoveries cut 12.3/wk $33652, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $18024/wk, losers avoided $19769/wk, net +2025 $/wk; pnl $21555/wk.
JN05W_S6_C22_RM HOLD (stack, per week): full stops 20.1/wk $-30642; give-backs 7.4/wk (7.3 round-trips) realised $-8620, forgone vs target $21715; same-side losing runs max 11, p95 6, $-32081 lost on 3rd-and-later; no-new-evidence re-entries 26.6/wk $1072; recoveries cut 10.7/wk $29015, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $13307/wk, losers avoided $14948/wk, net +1777 $/wk; pnl $14274/wk.
JN05W_S6_C22_RM PRE (stack, per week): full stops 15.9/wk $-25126; give-backs 5.0/wk (4.6 round-trips) realised $-5291, forgone vs target $13685; same-side losing runs max 9, p95 4, $-16412 lost on 3rd-and-later; no-new-evidence re-entries 12.2/wk $233; recoveries cut 6.6/wk $15765, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $4095/wk, losers avoided $4436/wk, net +358 $/wk; pnl $9766/wk.
JN05W_S6_C22_RM X' (stack, per week): full stops 17.7/wk $-27189; give-backs 3.5/wk (3.0 round-trips) realised $-3615, forgone vs target $9772; same-side losing runs max 7, p95 4, $-9998 lost on 3rd-and-later; no-new-evidence re-entries 3.1/wk $562; recoveries cut 2.5/wk $6540, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $0/wk, losers avoided $-0/wk, net +0 $/wk; pnl $1547/wk.

```
### JN05W_S6_C22V19 (ref LPB_BASE)
```
JN05W_S6_C22V19 L6M (stack, per week): full stops 20.0/wk $-32883; give-backs 7.6/wk (7.5 round-trips) realised $-11973, forgone vs target $30862; same-side losing runs max 12, p95 6, $-45975 lost on 3rd-and-later; no-new-evidence re-entries 29.9/wk $-866; recoveries cut 11.4/wk $41187, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $16807/wk, losers avoided $18781/wk, net +1974 $/wk; pnl $21758/wk.
JN05W_S6_C22V19 HOLD (stack, per week): full stops 19.7/wk $-32832; give-backs 7.0/wk (6.9 round-trips) realised $-11002, forgone vs target $28043; same-side losing runs max 12, p95 6, $-39163 lost on 3rd-and-later; no-new-evidence re-entries 24.2/wk $620; recoveries cut 10.3/wk $36681, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $12160/wk, losers avoided $14078/wk, net +1881 $/wk; pnl $17233/wk.
JN05W_S6_C22V19 PRE (stack, per week): full stops 16.0/wk $-27558; give-backs 4.8/wk (4.4 round-trips) realised $-7239, forgone vs target $18553; same-side losing runs max 7, p95 4, $-21042 lost on 3rd-and-later; no-new-evidence re-entries 10.9/wk $320; recoveries cut 6.0/wk $20569, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $4080/wk, losers avoided $4791/wk, net +679 $/wk; pnl $12562/wk.
JN05W_S6_C22V19 X' (stack, per week): full stops 17.5/wk $-28249; give-backs 3.5/wk (3.0 round-trips) realised $-4908, forgone vs target $12781; same-side losing runs max 7, p95 4, $-12302 lost on 3rd-and-later; no-new-evidence re-entries 2.7/wk $569; recoveries cut 2.5/wk $9968, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $144/wk, losers avoided $27/wk, net -170 $/wk; pnl $1172/wk.

```
### JN05W_S6_C22V19_RM (ref JN04RM)
```
JN05W_S6_C22V19_RM L6M (stack, per week): full stops 20.3/wk $-30880; give-backs 8.0/wk (7.9 round-trips) realised $-9302, forgone vs target $23501; same-side losing runs max 11, p95 6, $-36074 lost on 3rd-and-later; no-new-evidence re-entries 33.1/wk $1104; recoveries cut 12.1/wk $33024, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $19585/wk, losers avoided $21158/wk, net +1714 $/wk; pnl $21244/wk.
JN05W_S6_C22V19_RM HOLD (stack, per week): full stops 19.9/wk $-30369; give-backs 7.4/wk (7.2 round-trips) realised $-8551, forgone vs target $21551; same-side losing runs max 11, p95 6, $-31637 lost on 3rd-and-later; no-new-evidence re-entries 26.1/wk $822; recoveries cut 10.6/wk $28710, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $14350/wk, losers avoided $15944/wk, net +1649 $/wk; pnl $14146/wk.
JN05W_S6_C22V19_RM PRE (stack, per week): full stops 15.9/wk $-25141; give-backs 5.0/wk (4.6 round-trips) realised $-5258, forgone vs target $13603; same-side losing runs max 9, p95 4, $-16311 lost on 3rd-and-later; no-new-evidence re-entries 12.1/wk $323; recoveries cut 6.6/wk $15693, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $4193/wk, losers avoided $4630/wk, net +438 $/wk; pnl $9847/wk.
JN05W_S6_C22V19_RM X' (stack, per week): full stops 17.7/wk $-27189; give-backs 3.5/wk (3.0 round-trips) realised $-3615, forgone vs target $9772; same-side losing runs max 7, p95 4, $-9998 lost on 3rd-and-later; no-new-evidence re-entries 3.1/wk $562; recoveries cut 2.5/wk $6540, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $0/wk, losers avoided $-0/wk, net +0 $/wk; pnl $1547/wk.

```
### JN05W_S6_C18 (ref LPB_BASE)
```
JN05W_S6_C18 L6M (stack, per week): full stops 19.0/wk $-31433; give-backs 7.0/wk (7.0 round-trips) realised $-11098, forgone vs target $28670; same-side losing runs max 12, p95 6, $-43655 lost on 3rd-and-later; no-new-evidence re-entries 27.3/wk $-639; recoveries cut 10.6/wk $39249, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $23832/wk, losers avoided $25355/wk, net +1286 $/wk; pnl $21069/wk.
JN05W_S6_C18 HOLD (stack, per week): full stops 18.9/wk $-31706; give-backs 6.7/wk (6.5 round-trips) realised $-10446, forgone vs target $26681; same-side losing runs max 12, p95 5, $-37556 lost on 3rd-and-later; no-new-evidence re-entries 22.4/wk $609; recoveries cut 9.7/wk $35290, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $17175/wk, losers avoided $18726/wk, net +1367 $/wk; pnl $16718/wk.
JN05W_S6_C18 PRE (stack, per week): full stops 15.3/wk $-26662; give-backs 4.7/wk (4.3 round-trips) realised $-7015, forgone vs target $17904; same-side losing runs max 7, p95 4, $-20491 lost on 3rd-and-later; no-new-evidence re-entries 10.2/wk $53; recoveries cut 5.6/wk $19339, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $6386/wk, losers avoided $7291/wk, net +856 $/wk; pnl $12739/wk.
JN05W_S6_C18 X' (stack, per week): full stops 17.4/wk $-28055; give-backs 3.5/wk (3.0 round-trips) realised $-4840, forgone vs target $12678; same-side losing runs max 7, p95 4, $-12302 lost on 3rd-and-later; no-new-evidence re-entries 2.7/wk $560; recoveries cut 2.5/wk $9899, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $515/wk, losers avoided $248/wk, net -267 $/wk; pnl $1075/wk.

```
### JN05W_S6_C18_RM (ref JN04RM)
```
JN05W_S6_C18_RM L6M (stack, per week): full stops 19.6/wk $-30107; give-backs 7.7/wk (7.6 round-trips) realised $-8988, forgone vs target $22748; same-side losing runs max 10, p95 6, $-33999 lost on 3rd-and-later; no-new-evidence re-entries 31.0/wk $2011; recoveries cut 11.8/wk $32393, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $23488/wk, losers avoided $24832/wk, net +1600 $/wk; pnl $21130/wk.
JN05W_S6_C18_RM HOLD (stack, per week): full stops 19.2/wk $-29502; give-backs 7.0/wk (6.8 round-trips) realised $-8132, forgone vs target $20673; same-side losing runs max 10, p95 6, $-30099 lost on 3rd-and-later; no-new-evidence re-entries 24.6/wk $1400; recoveries cut 10.2/wk $27887, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $17480/wk, losers avoided $19324/wk, net +1968 $/wk; pnl $14466/wk.
JN05W_S6_C18_RM PRE (stack, per week): full stops 15.5/wk $-24632; give-backs 4.9/wk (4.4 round-trips) realised $-5166, forgone vs target $13364; same-side losing runs max 9, p95 4, $-15849 lost on 3rd-and-later; no-new-evidence re-entries 11.3/wk $380; recoveries cut 6.3/wk $15097, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $5925/wk, losers avoided $6335/wk, net +427 $/wk; pnl $9836/wk.
JN05W_S6_C18_RM X' (stack, per week): full stops 17.6/wk $-27160; give-backs 3.5/wk (3.0 round-trips) realised $-3615, forgone vs target $9772; same-side losing runs max 7, p95 4, $-9998 lost on 3rd-and-later; no-new-evidence re-entries 3.0/wk $580; recoveries cut 2.5/wk $6540, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $181/wk, losers avoided $81/wk, net -101 $/wk; pnl $1446/wk.

```
### JN05W_S6_C14 (ref LPB_BASE)
```
JN05W_S6_C14 L6M (stack, per week): full stops 17.1/wk $-28045; give-backs 6.3/wk (6.2 round-trips) realised $-10133, forgone vs target $26265; same-side losing runs max 11, p95 6, $-40699 lost on 3rd-and-later; no-new-evidence re-entries 24.4/wk $-810; recoveries cut 9.3/wk $35278, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $35742/wk, losers avoided $35936/wk, net +318 $/wk; pnl $20102/wk.
JN05W_S6_C14 HOLD (stack, per week): full stops 17.4/wk $-29219; give-backs 6.1/wk (5.9 round-trips) realised $-9734, forgone vs target $24949; same-side losing runs max 11, p95 5, $-35470 lost on 3rd-and-later; no-new-evidence re-entries 20.1/wk $775; recoveries cut 8.8/wk $32803, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $25890/wk, losers avoided $26468/wk, net +644 $/wk; pnl $15996/wk.
JN05W_S6_C14 PRE (stack, per week): full stops 14.4/wk $-25261; give-backs 4.4/wk (4.1 round-trips) realised $-6730, forgone vs target $17139; same-side losing runs max 7, p95 4, $-19180 lost on 3rd-and-later; no-new-evidence re-entries 9.0/wk $279; recoveries cut 5.1/wk $18029, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $10198/wk, losers avoided $11099/wk, net +856 $/wk; pnl $12738/wk.
JN05W_S6_C14 X' (stack, per week): full stops 16.8/wk $-27389; give-backs 3.3/wk (2.8 round-trips) realised $-4690, forgone vs target $12254; same-side losing runs max 7, p95 4, $-12063 lost on 3rd-and-later; no-new-evidence re-entries 2.6/wk $592; recoveries cut 2.5/wk $9899, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $1451/wk, losers avoided $1351/wk, net -100 $/wk; pnl $1242/wk.

```
### JN05W_S6_C14_RM (ref JN04RM)
```
JN05W_S6_C14_RM L6M (stack, per week): full stops 18.4/wk $-28144; give-backs 7.0/wk (7.0 round-trips) realised $-8327, forgone vs target $21063; same-side losing runs max 10, p95 6, $-31641 lost on 3rd-and-later; no-new-evidence re-entries 28.7/wk $2299; recoveries cut 10.7/wk $29589, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $29896/wk, losers avoided $31014/wk, net +1069 $/wk; pnl $20599/wk.
JN05W_S6_C14_RM HOLD (stack, per week): full stops 18.2/wk $-27844; give-backs 6.6/wk (6.4 round-trips) realised $-7693, forgone vs target $19595; same-side losing runs max 10, p95 6, $-28303 lost on 3rd-and-later; no-new-evidence re-entries 22.8/wk $1640; recoveries cut 9.5/wk $26193, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $22894/wk, losers avoided $24232/wk, net +1310 $/wk; pnl $13808/wk.
JN05W_S6_C14_RM PRE (stack, per week): full stops 14.8/wk $-23649; give-backs 4.6/wk (4.2 round-trips) realised $-4903, forgone vs target $12703; same-side losing runs max 9, p95 4, $-15009 lost on 3rd-and-later; no-new-evidence re-entries 10.1/wk $200; recoveries cut 5.6/wk $13810, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $9513/wk, losers avoided $9240/wk, net -317 $/wk; pnl $9092/wk.
JN05W_S6_C14_RM X' (stack, per week): full stops 17.3/wk $-26662; give-backs 3.3/wk (2.8 round-trips) realised $-3463, forgone vs target $9345; same-side losing runs max 7, p95 4, $-9868 lost on 3rd-and-later; no-new-evidence re-entries 2.9/wk $628; recoveries cut 2.5/wk $6492, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $1304/wk, losers avoided $811/wk, net -493 $/wk; pnl $1054/wk.

```