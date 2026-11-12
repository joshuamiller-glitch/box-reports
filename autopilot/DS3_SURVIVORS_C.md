# DS3_SURVIVORS_C - new-evidence rule WG_E1 / WL_E1 (W-C), page 2026-11-12 13:02Z; Shadow only, no PASS claim; recents first, PRE/X' tolerant per rule 2a

Rule (P7, all sessions): skip a P7 signal that would be the 3rd or later consecutive same-side losing attempt of the session unless NEW EVIDENCE exists (a new session extreme in the trade direction beyond the extreme at the last failure, or an opposite-side P7 entry since). Hook code/th_works_c/c_gov.py, set WG_E1 (dressed base JN04RM, reference JN04RM) and WL_E1 (live panel base, reference LPB_BASE). All 43 months exact, ROLLFIX1, one set per job on the TP engine (identity checked).

## WL_E1 vs LPB_BASE (live panel base)
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | -5.4 | -90 | 53999 | 51253 | -2 / 1 |
| L3M | -0.0 | -122 | 77224 | 77224 | 143 / 155 |
| L6M | 0.0 | -416 | 77224 | 77224 | 81 / 102 |
| HOLD | -14.5 | -143 | 90307 | 78842 | -393 / -377 |
| PRE | 1.4 | -90 | 98072 | 99479 | -536 / -529 |
| X' | 0.0 | +20 | 122553 | 122553 | -321 / -321 |
| GAP 2025-07..10 | 0.0 | -204 | 24853 | 24853 | |

Bi-weekly WF (re-pick every 2 weeks, purged): maxDD cut 0.0 %, d mean -4 $/wk, beat live in 9 % of refit periods (most periods are ties because the rule rarely fires).
Rule-2a label: **OK-PRIOR**.
TREND-WEEK CLAUSE (L6M): the reference's 5 best weeks sum to $+331449 and the cell's same weeks to $+317216; winning weeks turned losing: 0 of 19; $ given up inside winning weeks: -48031; sum of the 20 worst weeks cell +131897 vs ref +154669.
TREND-WEEK CLAUSE (HOLD): the reference's 5 best weeks sum to $+376655 and the cell's same weeks to $+358501; winning weeks turned losing: 0 of 37; $ given up inside winning weeks: -52832; sum of the 20 worst weeks cell -386079 vs ref -370271.
TREND-WEEK CLAUSE (all 3.5 years): the reference's 5 best weeks sum to $+458167 and the cell's same weeks to $+445950; winning weeks turned losing: 0 of 123; $ given up inside winning weeks: -76076; sum of the 20 worst weeks cell -891215 vs ref -869001.

## WG_E1 vs JN04RM (dials on)
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | 24.8 | +613 | 20349 | 27056 | 21 / 15 |
| L3M | 0.0 | -177 | 41699 | 41699 | 165 / 164 |
| L6M | 0.0 | +20 | 41699 | 41699 | 140 / 138 |
| HOLD | -4.6 | +59 | 76110 | 72757 | -274 / -285 |
| PRE | 11.3 | -92 | 59190 | 66714 | -329 / -328 |
| X' | 0.0 | +19 | 64077 | 64077 | -222 / -222 |
| GAP 2025-07..10 | 0.0 | -15 | 23701 | 23701 | |

Bi-weekly WF (re-pick every 2 weeks, purged): maxDD cut -4.6 %, d mean +75 $/wk, beat live in 14 % of refit periods (most periods are ties because the rule rarely fires).
Rule-2a label: **OK-PRIOR**.
TREND-WEEK CLAUSE (L6M): the reference's 5 best weeks sum to $+299107 and the cell's same weeks to $+294575; winning weeks turned losing: 0 of 19; $ given up inside winning weeks: -20125; sum of the 20 worst weeks cell +181024 vs ref +180775.
TREND-WEEK CLAUSE (HOLD): the reference's 5 best weeks sum to $+323722 and the cell's same weeks to $+318557; winning weeks turned losing: 1 of 36; $ given up inside winning weeks: -23991; sum of the 20 worst weeks cell -270706 vs ref -281405.
TREND-WEEK CLAUSE (all 3.5 years): the reference's 5 best weeks sum to $+347086 and the cell's same weeks to $+343898; winning weeks turned losing: 1 of 118; $ given up inside winning weeks: -39224; sum of the 20 worst weeks cell -564833 vs ref -560640.

## Acceptance test (acceptance_p7.py; full 43 months)
### WL_E1
```
ACCEPTANCE P7 WL_E1  2026-11-12 13:02Z   (months 43: 202304..202610; reference LPB_BASE months 43)
| scope | who | sessions | max run | p95 | mean | sessions with run>=3 | n 3rd+ losers | $ lost on 3rd+ losers | entries 3rd+ attempt without new evidence (n / $) | losing 3rd+ no-evidence violations | bigger 2nd attempts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| all P7 | LPB_BASE (live ref) | 2213 | 6 | 2.0 | 0.89 | 48 | 57 | -136326 | 90 / -11382 | 53 | 110 |
| all P7 | WL_E1 | 2220 | 4 | 2.0 | 0.88 | 16 | 19 | -55395 | 0 / +0 | 0 | 109 |
| Asia | LPB_BASE (live ref) | 919 | 6 | 2.0 | 0.90 | 21 | 26 | -80482 | 37 / -10876 | 24 | 33 |
| Asia | WL_E1 | 919 | 4 | 2.0 | 0.89 | 11 | 13 | -43647 | 0 / +0 | 0 | 33 |
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +28883 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +23369 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +23252 (7 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +22466 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +22396 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 2 ($+10799); all re-entry winners (any evidence) reference 13, set 12
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)
SUMMARY WL_E1: fails 1 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT WL_E1 PASS fails=1/20
```
### WG_E1
```
ACCEPTANCE P7 WG_E1  2026-11-12 13:02Z   (months 43: 202304..202610; reference LPB_BASE months 43)
| scope | who | sessions | max run | p95 | mean | sessions with run>=3 | n 3rd+ losers | $ lost on 3rd+ losers | entries 3rd+ attempt without new evidence (n / $) | losing 3rd+ no-evidence violations | bigger 2nd attempts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| all P7 | LPB_BASE (live ref) | 2213 | 6 | 2.0 | 0.89 | 48 | 57 | -136326 | 90 / -11382 | 53 | 110 |
| all P7 | WG_E1 | 2479 | 4 | 2.0 | 0.92 | 27 | 31 | -38641 | 0 / +0 | 0 | 56 |
| Asia | LPB_BASE (live ref) | 919 | 6 | 2.0 | 0.90 | 21 | 26 | -80482 | 37 / -10876 | 24 | 33 |
| Asia | WG_E1 | 918 | 4 | 2.0 | 0.91 | 15 | 18 | -25183 | 0 / +0 | 0 | 41 |
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +22883 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +11869 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +12634 (9 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +9563 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +12231 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 2 ($+7188); all re-entry winners (any evidence) reference 13, set 13
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)
SUMMARY WG_E1: fails 2 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT WG_E1 PASS fails=2/20
```
## Behavioural scorecard (items a-e, W-Q tool)
### WL_E1 (ref LPB_BASE)
```
WL_E1 L6M (stack, per week): full stops 24.5/wk $-40067; give-backs 9.1/wk (9.0 round-trips) realised $-13952, forgone vs target $35303; same-side losing runs max 12, p95 6, $-50256 lost on 3rd-and-later; no-new-evidence re-entries 35.9/wk $-481; recoveries cut 13.3/wk $45088, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $3513/wk, losers avoided $2691/wk, net -1011 $/wk; pnl $18773/wk.
WL_E1 HOLD (stack, per week): full stops 23.0/wk $-38054; give-backs 7.9/wk (7.7 round-trips) realised $-11973, forgone vs target $30254; same-side losing runs max 12, p95 6, $-42669 lost on 3rd-and-later; no-new-evidence re-entries 28.9/wk $639; recoveries cut 12.0/wk $40466, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $2347/wk, losers avoided $2037/wk, net -430 $/wk; pnl $14922/wk.
WL_E1 PRE (stack, per week): full stops 16.9/wk $-28822; give-backs 5.2/wk (4.8 round-trips) realised $-7652, forgone vs target $19686; same-side losing runs max 11, p95 4, $-22099 lost on 3rd-and-later; no-new-evidence re-entries 12.4/wk $-267; recoveries cut 6.7/wk $22117, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $618/wk, losers avoided $762/wk, net +72 $/wk; pnl $11954/wk.
WL_E1 X' (stack, per week): full stops 17.5/wk $-28195; give-backs 3.5/wk (3.0 round-trips) realised $-4882, forgone vs target $12755; same-side losing runs max 7, p95 4, $-12208 lost on 3rd-and-later; no-new-evidence re-entries 2.7/wk $663; recoveries cut 2.5/wk $9968, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $0/wk, losers avoided $94/wk, net +94 $/wk; pnl $1437/wk.

```
### WG_E1 (ref JN04RM)
```
WG_E1 L6M (stack, per week): full stops 25.4/wk $-38079; give-backs 9.9/wk (9.8 round-trips) realised $-11307, forgone vs target $28092; same-side losing runs max 13, p95 6, $-42134 lost on 3rd-and-later; no-new-evidence re-entries 40.8/wk $1434; recoveries cut 14.8/wk $38876, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $2489/wk, losers avoided $1938/wk, net -174 $/wk; pnl $19356/wk.
WG_E1 HOLD (stack, per week): full stops 23.6/wk $-35496; give-backs 8.6/wk (8.4 round-trips) realised $-9734, forgone vs target $24323; same-side losing runs max 13, p95 6, $-36640 lost on 3rd-and-later; no-new-evidence re-entries 32.5/wk $1083; recoveries cut 12.9/wk $33401, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $1707/wk, losers avoided $1536/wk, net +246 $/wk; pnl $12743/wk.
WG_E1 PRE (stack, per week): full stops 16.8/wk $-26376; give-backs 5.3/wk (4.9 round-trips) realised $-5596, forgone vs target $14462; same-side losing runs max 11, p95 5, $-17510 lost on 3rd-and-later; no-new-evidence re-entries 13.6/wk $-31; recoveries cut 7.1/wk $16860, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $683/wk, losers avoided $678/wk, net +59 $/wk; pnl $9468/wk.
WG_E1 X' (stack, per week): full stops 17.7/wk $-27189; give-backs 3.5/wk (2.9 round-trips) realised $-3595, forgone vs target $9725; same-side losing runs max 7, p95 4, $-9959 lost on 3rd-and-later; no-new-evidence re-entries 3.0/wk $601; recoveries cut 2.5/wk $6540, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $0/wk, losers avoided $38/wk, net +38 $/wk; pnl $1585/wk.

```