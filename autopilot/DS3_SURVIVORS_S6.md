# DS3_SURVIVORS_S6 - S6 desk-state cap, "stop trying when behind" (W-S), page 2026-11-12 15:12Z; Shadow only, no PASS claim; recents first, PRE/X' tolerant per rule 2a

Rule: skip every NEW entry of every book once the stack has closed >= N trades in the label day (17:00 ET roll) AND the stack day P&L is <= -2 R. Hook code/th_screens/scr_hooks.py (feature conj), one set per job, TP engine. Cells JN05W_S6_C22 / C18 / C14 on the live panel base (reference LPB_BASE) and JN05W_S6_C22_RM / C18_RM / C14_RM on JN04RM. The first-order screen (3.5 years, LPB trade list) is in DS3_SCREENS.md. Months present are stated per cell; a window is scored only when all its months are present.

## JN05W_S6_C22 (stack closes today >= 22 AND stack day P&L <= -2 R (R = $1,200)) vs LPB_BASE (live panel base) - 24 of 43 months present
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | 42.4 | +11328 | 29541 | 51253 | 12 / 1 |
| L3M | 43.9 | +7529 | 43357 | 77224 | 223 / 155 |
| L6M | 43.9 | +3078 | 43357 | 77224 | 130 / 102 |
| HOLD | 10.9 | +2543 | 70281 | 78842 | -297 / -377 |
TREND-WEEK CLAUSE (L6M, ): the reference's 5 best weeks sum to $+331449 and the cell's same weeks to $+344869; winning weeks turned losing: 2 of 19; $ given up inside winning weeks: -83487; sum of the 20 worst weeks cell +183845 vs ref +154669.
TREND-WEEK CLAUSE (HOLD, ): the reference's 5 best weeks sum to $+376655 and the cell's same weeks to $+389560; winning weeks turned losing: 2 of 37; $ given up inside winning weeks: -101033; sum of the 20 worst weeks cell -289670 vs ref -370271.
TREND-WEEK CLAUSE (all 3.5 years): pending, 24 of 43 months present.

## JN05W_S6_C22_RM (stack closes today >= 22 AND stack day P&L <= -2 R (R = $1,200)) vs JN04RM (dials on) - 24 of 43 months present
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | 53.5 | +4828 | 12571 | 27056 | 18 / 15 |
| L3M | 24.6 | +4048 | 31434 | 41699 | 200 / 164 |
| L6M | 5.9 | +2612 | 39221 | 41699 | 169 / 138 |
| HOLD | 25.4 | +2067 | 54311 | 72757 | -223 / -285 |
TREND-WEEK CLAUSE (L6M, ): the reference's 5 best weeks sum to $+299107 and the cell's same weeks to $+317127; winning weeks turned losing: 0 of 19; $ given up inside winning weeks: -45556; sum of the 20 worst weeks cell +212515 vs ref +180775.
TREND-WEEK CLAUSE (HOLD, ): the reference's 5 best weeks sum to $+323722 and the cell's same weeks to $+326680; winning weeks turned losing: 2 of 36; $ given up inside winning weeks: -73477; sum of the 20 worst weeks cell -217029 vs ref -281405.
TREND-WEEK CLAUSE (all 3.5 years): pending, 24 of 43 months present.

## JN05W_S6_C22V19 (V19 reading: trades OPENED since the roll >= 22 AND realised day P&L <= -2 R) vs LPB_BASE (live panel base) - 10 of 43 months present
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | 45.0 | -2598 | 28201 | 51253 | 17 / 1 |
| L3M | 45.7 | +5305 | 41961 | 77224 | 242 / 155 |
| L6M | 45.7 | +3289 | 41961 | 77224 | 127 / 102 |
TREND-WEEK CLAUSE (L6M, ): the reference's 5 best weeks sum to $+331449 and the cell's same weeks to $+347166; winning weeks turned losing: 2 of 19; $ given up inside winning weeks: -94825; sum of the 20 worst weeks cell +180747 vs ref +154669.
TREND-WEEK CLAUSE (HOLD): pending, 10 of 12 months present.
TREND-WEEK CLAUSE (all 3.5 years): pending, 10 of 43 months present.

## JN05W_S6_C22V19_RM (V19 reading: trades OPENED since the roll >= 22 AND realised day P&L <= -2 R) vs JN04RM (dials on) - 9 of 43 months present
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | 62.0 | +5594 | 10275 | 27056 | 20 / 15 |
| L3M | 14.6 | +3787 | 35592 | 41699 | 197 / 164 |
| L6M | 8.5 | +2307 | 38141 | 41699 | 161 / 138 |
TREND-WEEK CLAUSE (L6M, ): the reference's 5 best weeks sum to $+299107 and the cell's same weeks to $+316662; winning weeks turned losing: 0 of 19; $ given up inside winning weeks: -54130; sum of the 20 worst weeks cell +205344 vs ref +180775.
TREND-WEEK CLAUSE (HOLD): pending, 9 of 12 months present.
TREND-WEEK CLAUSE (all 3.5 years): pending, 9 of 43 months present.

## JN05W_S6_C18 (stack closes today >= 18 AND stack day P&L <= -2 R) vs LPB_BASE (live panel base) - 11 of 43 months present
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | 40.9 | -3002 | 30299 | 51253 | 13 / 1 |
| L3M | 48.1 | +5306 | 40054 | 77224 | 240 / 155 |
| L6M | 48.1 | +2654 | 40054 | 77224 | 118 / 102 |
TREND-WEEK CLAUSE (L6M, ): the reference's 5 best weeks sum to $+331449 and the cell's same weeks to $+340975; winning weeks turned losing: 2 of 19; $ given up inside winning weeks: -117036; sum of the 20 worst weeks cell +168780 vs ref +154669.
TREND-WEEK CLAUSE (HOLD): pending, 11 of 12 months present.
TREND-WEEK CLAUSE (all 3.5 years): pending, 11 of 43 months present.

## JN05W_S6_C18_RM (stack closes today >= 18 AND stack day P&L <= -2 R) vs JN04RM (dials on) - 11 of 43 months present
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | 65.0 | +5862 | 9469 | 27056 | 21 / 15 |
| L3M | 15.1 | +1387 | 35386 | 41699 | 194 / 164 |
| L6M | 15.1 | +2386 | 35386 | 41699 | 158 / 138 |
TREND-WEEK CLAUSE (L6M, ): the reference's 5 best weeks sum to $+299107 and the cell's same weeks to $+317388; winning weeks turned losing: 1 of 19; $ given up inside winning weeks: -54762; sum of the 20 worst weeks cell +201806 vs ref +180775.
TREND-WEEK CLAUSE (HOLD): pending, 11 of 12 months present.
TREND-WEEK CLAUSE (all 3.5 years): pending, 11 of 43 months present.

## JN05W_S6_C14 (stack closes today >= 14 AND stack day P&L <= -2 R) vs LPB_BASE (live panel base) - 23 of 43 months present
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | 51.0 | -838 | 25105 | 51253 | 25 / 1 |
| L3M | 13.1 | +4036 | 67129 | 77224 | 230 / 155 |
| L6M | 13.1 | +2149 | 67129 | 77224 | 92 / 102 |
| HOLD | 12.0 | +1539 | 69365 | 78842 | -315 / -377 |
TREND-WEEK CLAUSE (L6M, ): the reference's 5 best weeks sum to $+331449 and the cell's same weeks to $+338108; winning weeks turned losing: 2 of 19; $ given up inside winning weeks: -132998; sum of the 20 worst weeks cell +139761 vs ref +154669.
TREND-WEEK CLAUSE (HOLD, ): the reference's 5 best weeks sum to $+376655 and the cell's same weeks to $+383084; winning weeks turned losing: 3 of 37; $ given up inside winning weeks: -202061; sum of the 20 worst weeks cell -312029 vs ref -370271.
TREND-WEEK CLAUSE (all 3.5 years): pending, 23 of 43 months present.

## JN05W_S6_C14_RM (stack closes today >= 14 AND stack day P&L <= -2 R) vs JN04RM (dials on) - 23 of 43 months present
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | 85.2 | +993 | 4012 | 27056 | 35 / 15 |
| L3M | -17.8 | +1071 | 49103 | 41699 | 193 / 164 |
| L6M | -17.8 | +2326 | 49103 | 41699 | 145 / 138 |
| HOLD | 7.7 | +1925 | 67178 | 72757 | -242 / -285 |
TREND-WEEK CLAUSE (L6M, ): the reference's 5 best weeks sum to $+299107 and the cell's same weeks to $+315865; winning weeks turned losing: 2 of 19; $ given up inside winning weeks: -87063; sum of the 20 worst weeks cell +190281 vs ref +180775.
TREND-WEEK CLAUSE (HOLD, ): the reference's 5 best weeks sum to $+323722 and the cell's same weeks to $+318013; winning weeks turned losing: 6 of 36; $ given up inside winning weeks: -149906; sum of the 20 worst weeks cell -237420 vs ref -281405.
TREND-WEEK CLAUSE (all 3.5 years): pending, 23 of 43 months present.

## Acceptance test (acceptance_p7.py; judged on the months present, stated by the tool)
### JN05W_S6_C22
```
ACCEPTANCE P7 JN05W_S6_C22  2026-11-12 15:12Z   (months 24: 202411..202610; reference LPB_BASE months 43)
| scope | who | sessions | max run | p95 | mean | sessions with run>=3 | n 3rd+ losers | $ lost on 3rd+ losers | entries 3rd+ attempt without new evidence (n / $) | losing 3rd+ no-evidence violations | bigger 2nd attempts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| all P7 | LPB_BASE (live ref) | 1222 | 6 | 2.0 | 1.03 | 42 | 51 | -122209 | 78 / -18843 | 47 | 83 |
| all P7 | JN05W_S6_C22 | 1182 | 6 | 2.0 | 1.01 | 38 | 47 | -115355 | 70 / -22773 | 43 | 72 |
| Asia | LPB_BASE (live ref) | 515 | 6 | 2.0 | 1.06 | 20 | 25 | -76868 | 33 / -24040 | 23 | 26 |
| Asia | JN05W_S6_C22 | 515 | 6 | 2.0 | 1.06 | 19 | 24 | -75159 | 32 / -22331 | 22 | 26 |
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +28883 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +23369 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +23252 (7 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +22466 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +22396 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 1 ($+8402); all re-entry winners (any evidence) reference 13, set 13
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)
SUMMARY JN05W_S6_C22: fails 3 of 18 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT JN05W_S6_C22 FAIL fails=3/20
```
### JN05W_S6_C22_RM
```
ACCEPTANCE P7 JN05W_S6_C22_RM  2026-11-12 15:12Z   (months 24: 202411..202610; reference LPB_BASE months 43)
| scope | who | sessions | max run | p95 | mean | sessions with run>=3 | n 3rd+ losers | $ lost on 3rd+ losers | entries 3rd+ attempt without new evidence (n / $) | losing 3rd+ no-evidence violations | bigger 2nd attempts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| all P7 | LPB_BASE (live ref) | 1222 | 6 | 2.0 | 1.03 | 42 | 51 | -122209 | 78 / -18843 | 47 | 83 |
| all P7 | JN05W_S6_C22_RM | 1322 | 6 | 2.0 | 1.05 | 56 | 70 | -75651 | 114 / -1297 | 67 | 47 |
| Asia | LPB_BASE (live ref) | 515 | 6 | 2.0 | 1.06 | 20 | 25 | -76868 | 33 / -24040 | 23 | 26 |
| Asia | JN05W_S6_C22_RM | 515 | 6 | 2.0 | 1.10 | 24 | 33 | -42786 | 55 / +687 | 31 | 34 |
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +22883 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +11869 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +12634 (9 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +9563 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +12231 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 1 ($+4790); all re-entry winners (any evidence) reference 13, set 14
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)
SUMMARY JN05W_S6_C22_RM: fails 4 of 18 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT JN05W_S6_C22_RM FAIL fails=4/20
```
### JN05W_S6_C22V19
```
ACCEPTANCE P7 JN05W_S6_C22V19  2026-11-12 15:12Z   (months 10: 202601..202610; reference LPB_BASE months 43)
| scope | who | sessions | max run | p95 | mean | sessions with run>=3 | n 3rd+ losers | $ lost on 3rd+ losers | entries 3rd+ attempt without new evidence (n / $) | losing 3rd+ no-evidence violations | bigger 2nd attempts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| all P7 | LPB_BASE (live ref) | 490 | 5 | 2.0 | 1.18 | 23 | 27 | -57771 | 42 / +7303 | 25 | 40 |
| all P7 | JN05W_S6_C22V19 | 466 | 5 | 2.0 | 1.15 | 19 | 23 | -52462 | 35 / +3027 | 21 | 32 |
| Asia | LPB_BASE (live ref) | 216 | 4 | 2.2 | 1.25 | 11 | 12 | -33600 | 19 / +6957 | 11 | 12 |
| Asia | JN05W_S6_C22V19 | 216 | 4 | 2.0 | 1.25 | 10 | 11 | -31891 | 18 / +8666 | 10 | 12 |
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +28883 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +23369 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +23252 (7 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +22466 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +22396 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 1 ($+8402); all re-entry winners (any evidence) reference 13, set 13
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)
SUMMARY JN05W_S6_C22V19: fails 3 of 16 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT JN05W_S6_C22V19 FAIL fails=3/20
```
### JN05W_S6_C22V19_RM
```
ACCEPTANCE P7 JN05W_S6_C22V19_RM  2026-11-12 15:13Z   (months 9: 202602..202610; reference LPB_BASE months 43)
| scope | who | sessions | max run | p95 | mean | sessions with run>=3 | n 3rd+ losers | $ lost on 3rd+ losers | entries 3rd+ attempt without new evidence (n / $) | losing 3rd+ no-evidence violations | bigger 2nd attempts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| all P7 | LPB_BASE (live ref) | 439 | 5 | 2.0 | 1.21 | 21 | 25 | -55305 | 39 / +7372 | 23 | 37 |
| all P7 | JN05W_S6_C22V19_RM | 475 | 5 | 2.3 | 1.20 | 24 | 30 | -32823 | 54 / +8782 | 29 | 24 |
| Asia | LPB_BASE (live ref) | 195 | 4 | 3.0 | 1.30 | 11 | 12 | -33600 | 19 / +6957 | 11 | 11 |
| Asia | JN05W_S6_C22V19_RM | 195 | 4 | 3.0 | 1.33 | 12 | 16 | -19851 | 33 / +12163 | 15 | 19 |
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +22883 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +11869 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +12634 (9 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +9563 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +12231 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 1 ($+4790); all re-entry winners (any evidence) reference 13, set 14
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)
SUMMARY JN05W_S6_C22V19_RM: fails 4 of 16 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT JN05W_S6_C22V19_RM FAIL fails=4/20
```
### JN05W_S6_C18
```
ACCEPTANCE P7 JN05W_S6_C18  2026-11-12 15:13Z   (months 11: 202512..202610; reference LPB_BASE months 43)
| scope | who | sessions | max run | p95 | mean | sessions with run>=3 | n 3rd+ losers | $ lost on 3rd+ losers | entries 3rd+ attempt without new evidence (n / $) | losing 3rd+ no-evidence violations | bigger 2nd attempts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| all P7 | LPB_BASE (live ref) | 543 | 5 | 2.0 | 1.16 | 24 | 28 | -61020 | 43 / +9700 | 25 | 43 |
| all P7 | JN05W_S6_C18 | 504 | 5 | 2.0 | 1.12 | 19 | 23 | -52507 | 35 / +8628 | 20 | 31 |
| Asia | LPB_BASE (live ref) | 238 | 4 | 2.0 | 1.23 | 11 | 12 | -33600 | 19 / +6957 | 11 | 14 |
| Asia | JN05W_S6_C18 | 238 | 4 | 2.0 | 1.23 | 9 | 10 | -28687 | 17 / +11870 | 9 | 14 |
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +28883 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +23369 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +23252 (7 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +22466 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +22396 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 1 ($+8402); all re-entry winners (any evidence) reference 13, set 13
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)
SUMMARY JN05W_S6_C18: fails 3 of 16 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT JN05W_S6_C18 FAIL fails=3/20
```
### JN05W_S6_C18_RM
```
ACCEPTANCE P7 JN05W_S6_C18_RM  2026-11-12 15:13Z   (months 11: 202512..202610; reference LPB_BASE months 43)
| scope | who | sessions | max run | p95 | mean | sessions with run>=3 | n 3rd+ losers | $ lost on 3rd+ losers | entries 3rd+ attempt without new evidence (n / $) | losing 3rd+ no-evidence violations | bigger 2nd attempts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| all P7 | LPB_BASE (live ref) | 543 | 5 | 2.0 | 1.16 | 24 | 28 | -61020 | 43 / +9700 | 25 | 43 |
| all P7 | JN05W_S6_C18_RM | 576 | 5 | 2.0 | 1.14 | 27 | 33 | -34934 | 58 / +8774 | 31 | 29 |
| Asia | LPB_BASE (live ref) | 238 | 4 | 2.0 | 1.23 | 11 | 12 | -33600 | 19 / +6957 | 11 | 14 |
| Asia | JN05W_S6_C18_RM | 238 | 4 | 2.1 | 1.26 | 12 | 15 | -18292 | 31 / +11319 | 14 | 23 |
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +22883 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +11869 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +12634 (9 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +9563 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +12231 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 1 ($+4790); all re-entry winners (any evidence) reference 13, set 14
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)
SUMMARY JN05W_S6_C18_RM: fails 4 of 16 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT JN05W_S6_C18_RM FAIL fails=4/20
```
### JN05W_S6_C14
```
ACCEPTANCE P7 JN05W_S6_C14  2026-11-12 15:13Z   (months 23: 202412..202610; reference LPB_BASE months 43)
| scope | who | sessions | max run | p95 | mean | sessions with run>=3 | n 3rd+ losers | $ lost on 3rd+ losers | entries 3rd+ attempt without new evidence (n / $) | losing 3rd+ no-evidence violations | bigger 2nd attempts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| all P7 | LPB_BASE (live ref) | 1178 | 6 | 2.0 | 1.04 | 42 | 51 | -122209 | 76 / -24842 | 47 | 83 |
| all P7 | JN05W_S6_C14 | 1077 | 6 | 2.0 | 1.01 | 33 | 41 | -100416 | 60 / -21567 | 38 | 61 |
| Asia | LPB_BASE (live ref) | 494 | 6 | 2.0 | 1.07 | 20 | 25 | -76868 | 32 / -27637 | 23 | 26 |
| Asia | JN05W_S6_C14 | 494 | 6 | 2.0 | 1.06 | 17 | 22 | -66170 | 29 / -16939 | 20 | 26 |
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +28883 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +23369 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +23252 (7 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +22466 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +22396 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 1 ($+8402); all re-entry winners (any evidence) reference 13, set 10
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)
SUMMARY JN05W_S6_C14: fails 3 of 17 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT JN05W_S6_C14 FAIL fails=3/20
```
### JN05W_S6_C14_RM
```
ACCEPTANCE P7 JN05W_S6_C14_RM  2026-11-12 15:13Z   (months 23: 202412..202610; reference LPB_BASE months 43)
| scope | who | sessions | max run | p95 | mean | sessions with run>=3 | n 3rd+ losers | $ lost on 3rd+ losers | entries 3rd+ attempt without new evidence (n / $) | losing 3rd+ no-evidence violations | bigger 2nd attempts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| all P7 | LPB_BASE (live ref) | 1178 | 6 | 2.0 | 1.04 | 42 | 51 | -122209 | 76 / -24842 | 47 | 83 |
| all P7 | JN05W_S6_C14_RM | 1202 | 6 | 2.0 | 1.03 | 49 | 60 | -65500 | 98 / -741 | 57 | 41 |
| Asia | LPB_BASE (live ref) | 494 | 6 | 2.0 | 1.07 | 20 | 25 | -76868 | 32 / -27637 | 23 | 26 |
| Asia | JN05W_S6_C14_RM | 494 | 6 | 2.0 | 1.09 | 22 | 28 | -37049 | 48 / +2824 | 26 | 34 |
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +22883 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +11869 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +12634 (9 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +9563 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +12231 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 1 ($+4790); all re-entry winners (any evidence) reference 13, set 14
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)
SUMMARY JN05W_S6_C14_RM: fails 4 of 17 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT JN05W_S6_C14_RM FAIL fails=4/20
```
## Behavioural scorecard (items a-e, W-Q tool)
### JN05W_S6_C22 (ref LPB_BASE)
```
JN05W_S6_C22 L6M (stack, per week): full stops 20.3/wk $-33387; give-backs 7.7/wk (7.6 round-trips) realised $-12041, forgone vs target $31027; same-side losing runs max 12, p95 6, $-46529 lost on 3rd-and-later; no-new-evidence re-entries 30.4/wk $-835; recoveries cut 11.5/wk $41517, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $15685/wk, losers avoided $17456/wk, net +1760 $/wk; pnl $21544/wk.
JN05W_S6_C22 HOLD (stack, per week): full stops 20.0/wk $-33171; give-backs 7.1/wk (6.9 round-trips) realised $-11035, forgone vs target $28123; same-side losing runs max 12, p95 6, $-39520 lost on 3rd-and-later; no-new-evidence re-entries 24.6/wk $715; recoveries cut 10.3/wk $36841, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $11306/wk, losers avoided $13210/wk, net +1898 $/wk; pnl $17250/wk.
JN05W_S6_C22 PRE: months missing (9 of 17), window not scored
JN05W_S6_C22 X': months missing (10 of 10), window not scored

```
### JN05W_S6_C22_RM (ref JN04RM)
```
JN05W_S6_C22_RM L6M (stack, per week): full stops 20.7/wk $-31442; give-backs 8.1/wk (8.0 round-trips) realised $-9419, forgone vs target $23764; same-side losing runs max 11, p95 6, $-36548 lost on 3rd-and-later; no-new-evidence re-entries 33.9/wk $1462; recoveries cut 12.3/wk $33652, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $18024/wk, losers avoided $19769/wk, net +2025 $/wk; pnl $21555/wk.
JN05W_S6_C22_RM HOLD (stack, per week): full stops 20.1/wk $-30642; give-backs 7.4/wk (7.3 round-trips) realised $-8620, forgone vs target $21715; same-side losing runs max 11, p95 6, $-32081 lost on 3rd-and-later; no-new-evidence re-entries 26.6/wk $1072; recoveries cut 10.7/wk $29015, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $13307/wk, losers avoided $14948/wk, net +1777 $/wk; pnl $14274/wk.
JN05W_S6_C22_RM PRE: months missing (9 of 17), window not scored
JN05W_S6_C22_RM X': months missing (10 of 10), window not scored

```
### JN05W_S6_C22V19 (ref LPB_BASE)
```
JN05W_S6_C22V19 L6M (stack, per week): full stops 20.0/wk $-32883; give-backs 7.6/wk (7.5 round-trips) realised $-11973, forgone vs target $30862; same-side losing runs max 12, p95 6, $-45975 lost on 3rd-and-later; no-new-evidence re-entries 29.9/wk $-866; recoveries cut 11.4/wk $41187, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $16807/wk, losers avoided $18781/wk, net +1974 $/wk; pnl $21758/wk.
JN05W_S6_C22V19 HOLD: months missing (2 of 12), window not scored
JN05W_S6_C22V19 PRE: months missing (17 of 17), window not scored
JN05W_S6_C22V19 X': months missing (10 of 10), window not scored

```
### JN05W_S6_C22V19_RM (ref JN04RM)
```
JN05W_S6_C22V19_RM L6M (stack, per week): full stops 20.3/wk $-30880; give-backs 8.0/wk (7.9 round-trips) realised $-9302, forgone vs target $23501; same-side losing runs max 11, p95 6, $-36074 lost on 3rd-and-later; no-new-evidence re-entries 33.1/wk $1104; recoveries cut 12.1/wk $33024, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $19585/wk, losers avoided $21158/wk, net +1714 $/wk; pnl $21244/wk.
JN05W_S6_C22V19_RM HOLD: months missing (3 of 12), window not scored
JN05W_S6_C22V19_RM PRE: months missing (17 of 17), window not scored
JN05W_S6_C22V19_RM X': months missing (10 of 10), window not scored

```
### JN05W_S6_C18 (ref LPB_BASE)
```
JN05W_S6_C18 L6M (stack, per week): full stops 19.0/wk $-31433; give-backs 7.0/wk (7.0 round-trips) realised $-11098, forgone vs target $28670; same-side losing runs max 12, p95 6, $-43655 lost on 3rd-and-later; no-new-evidence re-entries 27.3/wk $-639; recoveries cut 10.6/wk $39249, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $23832/wk, losers avoided $25355/wk, net +1286 $/wk; pnl $21069/wk.
JN05W_S6_C18 HOLD: months missing (1 of 12), window not scored
JN05W_S6_C18 PRE: months missing (17 of 17), window not scored
JN05W_S6_C18 X': months missing (10 of 10), window not scored

```
### JN05W_S6_C18_RM (ref JN04RM)
```
JN05W_S6_C18_RM L6M (stack, per week): full stops 19.6/wk $-30107; give-backs 7.7/wk (7.6 round-trips) realised $-8988, forgone vs target $22748; same-side losing runs max 10, p95 6, $-33999 lost on 3rd-and-later; no-new-evidence re-entries 31.0/wk $2011; recoveries cut 11.8/wk $32393, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $23488/wk, losers avoided $24832/wk, net +1600 $/wk; pnl $21130/wk.
JN05W_S6_C18_RM HOLD: months missing (1 of 12), window not scored
JN05W_S6_C18_RM PRE: months missing (17 of 17), window not scored
JN05W_S6_C18_RM X': months missing (10 of 10), window not scored

```
### JN05W_S6_C14 (ref LPB_BASE)
```
JN05W_S6_C14 L6M (stack, per week): full stops 17.1/wk $-28045; give-backs 6.3/wk (6.2 round-trips) realised $-10133, forgone vs target $26265; same-side losing runs max 11, p95 6, $-40699 lost on 3rd-and-later; no-new-evidence re-entries 24.4/wk $-810; recoveries cut 9.3/wk $35278, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $35742/wk, losers avoided $35936/wk, net +318 $/wk; pnl $20102/wk.
JN05W_S6_C14 HOLD (stack, per week): full stops 17.4/wk $-29219; give-backs 6.1/wk (5.9 round-trips) realised $-9734, forgone vs target $24949; same-side losing runs max 11, p95 5, $-35470 lost on 3rd-and-later; no-new-evidence re-entries 20.1/wk $775; recoveries cut 8.8/wk $32803, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $25890/wk, losers avoided $26468/wk, net +644 $/wk; pnl $15996/wk.
JN05W_S6_C14 PRE: months missing (10 of 17), window not scored
JN05W_S6_C14 X': months missing (10 of 10), window not scored

```
### JN05W_S6_C14_RM (ref JN04RM)
```
JN05W_S6_C14_RM L6M (stack, per week): full stops 18.4/wk $-28144; give-backs 7.0/wk (7.0 round-trips) realised $-8327, forgone vs target $21063; same-side losing runs max 10, p95 6, $-31641 lost on 3rd-and-later; no-new-evidence re-entries 28.7/wk $2299; recoveries cut 10.7/wk $29589, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $29896/wk, losers avoided $31014/wk, net +1069 $/wk; pnl $20599/wk.
JN05W_S6_C14_RM HOLD (stack, per week): full stops 18.2/wk $-27844; give-backs 6.6/wk (6.4 round-trips) realised $-7693, forgone vs target $19595; same-side losing runs max 10, p95 6, $-28303 lost on 3rd-and-later; no-new-evidence re-entries 22.8/wk $1640; recoveries cut 9.5/wk $26193, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $22894/wk, losers avoided $24232/wk, net +1310 $/wk; pnl $13808/wk.
JN05W_S6_C14_RM PRE: months missing (10 of 17), window not scored
JN05W_S6_C14_RM X': months missing (10 of 10), window not scored

```