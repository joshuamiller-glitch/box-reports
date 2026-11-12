# DS3_SURVIVORS_X - flat-stop survivors (EC_FLAT{40,45,50}{K,U,A,M} on LPB_BASE; JN04RM_FLAT{40,45,50}K on the JN04RM base), exact, Shadow only, no PASS claim
Updated 2026-11-12 16:53Z. Prereg autopilot/SURVIVORS_X_PREREG.md. Months done per set: EC_FLAT45K 24/43, EC_FLAT40K 4/43, EC_FLAT50K 4/43, EC_FLAT45U 4/43, EC_FLAT40U 0/43, EC_FLAT50U 0/43, EC_FLAT45A 4/43, EC_FLAT40A 0/43, EC_FLAT50A 0/43, EC_FLAT45M 4/43, EC_FLAT40M 0/43, EC_FLAT50M 0/43, JN04RM_FLAT45K 6/43, JN04RM_FLAT40K 6/43, JN04RM_FLAT50K 5/43
Fill model: flat-stop market exit at next-1-s mid -/+ 0.80 pt (live loss-cut is 1.19-1.20 adverse => savings overstated ~0.4 pt). Windows PRE/X/GAP/WF need all 43 months; sets missing months are labelled.

## 1. Trend-week clause (L6M weekly check, exact)
# Weekly check, L6M (ISO weeks with trading days in 2026-05..10; weeks at the month edges are partial; exact engine; Shadow only)

| week | LPB_BASE | JN04RM | EC_FLAT45K | JN04RM_FLAT45K | JN04RM_FLAT40K |
|--|--|--|--|--|--|
| 202638 (best of LPB_BASE) | 88836 | 72104 | 84896 | 69691 | 69619 |
| 202623 (best of LPB_BASE) | 73836 | 68072 | 71789 | 59775 | 59375 |
| 202625 (best of LPB_BASE) | 59099 | 59990 | 58199 | 59515 | 61822 |
| 202639 (best of LPB_BASE) | 57178 | 52634 | 43511 | 40468 | 41816 |
| 202633 (best of LPB_BASE) | 52499 | 36328 | 60366 | 40954 | 44916 |
| 202644 (worst of LPB_BASE) | -51253 | -16664 | -48569 | -17116 | -16051 |
| 202636 (worst of LPB_BASE) | -44984 | -25704 | -41425 | -21809 | -22520 |
| 202621 (worst of LPB_BASE) | -39976 | -39092 | -33209 | -34871 | -35168 |
| 202635 (worst of LPB_BASE) | -23667 | -15995 | -23846 | -15523 | -15220 |
| 202637 (worst of LPB_BASE) | -8573 | 679 | -13749 | -1797 | -410 |

JN04RM: LPB_BASE winning weeks 20 of 27; of those, JN04RM turn losing: 1; weeks where JN04RM beats LPB_BASE: 13 of 27; sum over the 5 best LPB_BASE weeks 289128 vs 331449

EC_FLAT45K: LPB_BASE winning weeks 20 of 27; of those, EC_FLAT45K turn losing: 0; weeks where EC_FLAT45K beats LPB_BASE: 14 of 27; sum over the 5 best LPB_BASE weeks 318762 vs 331449

JN04RM_FLAT45K: LPB_BASE winning weeks 20 of 27; of those, JN04RM_FLAT45K turn losing: 1; weeks where JN04RM_FLAT45K beats LPB_BASE: 14 of 27; sum over the 5 best LPB_BASE weeks 270403 vs 331449

JN04RM_FLAT40K: LPB_BASE winning weeks 20 of 27; of those, JN04RM_FLAT40K turn losing: 2; weeks where JN04RM_FLAT40K beats LPB_BASE: 15 of 27; sum over the 5 best LPB_BASE weeks 277548 vs 331449



## EC_FLAT45K (24/43 months)
### windows / WF / rule 2a
```
EC_FLAT45K
         cell window  mean_all  mean_ref_all  dmean_all     mean       dd   dd_ref  cut   dmean  eq_cut       w20   w20_ref  calmar  mean_ref  months
0  EC_FLAT45K    L1M    1814.1         340.7     1473.4  18608.4  48568.8  51252.7  5.2  1069.8    14.7    7256.4    1363.0    19.9   17538.5      24
1  EC_FLAT45K    L3M   11624.0       11956.7     -332.7   8966.7  79019.9  77224.2 -2.3   778.5     7.8  151111.9  155436.8     5.9    8188.2      24
2  EC_FLAT45K    L6M   19992.6       18696.8     1295.7  19051.8  79019.9  77224.2 -2.3  1894.2     7.8  141385.6  102383.9    12.5   17157.6      24
3  EC_FLAT45K   HOLD   16376.0       15236.3     1139.6  15992.1  83267.6  78842.0 -5.6   817.6     4.9 -331684.1 -377467.2    10.0   15174.5      24

```
### acceptance_p7
```
 best L6M P7 sessions of the reference) and the frozen live week: re-entry winners after NEW EVIDENCE
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +28883 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +23369 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +23252 (7 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +22466 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +22396 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 1 ($+8402); all re-entry winners (any evidence) reference 13, set 13
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)

SUMMARY EC_FLAT45K: fails 3 of 19 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
covered sessions 19 of 20
ACCEPT EC_FLAT45K FAIL fails=3/20

```
### behavioural scorecard
EC_FLAT45K L6M (stack, per week): full stops 12.8/wk $-23274; give-backs 9.2/wk (9.0 round-trips) realised $-13722, forgone vs target $34912; same-side losing runs max 12, p95 6, $-53101 lost on 3rd-and-later; no-new-evidence re-entries 40.5/wk $873; recoveries cut 12.8/wk $45077, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $4898/wk, losers avoided $4330/wk, net +1371 $/wk; pnl $21155/wk.
EC_FLAT45K HOLD (stack, per week): full stops 11.9/wk $-22193; give-backs 8.1/wk (7.8 round-trips) realised $-11981, forgone vs target $30406; same-side losing runs max 12, p95 6, $-44714 lost on 3rd-and-later; no-new-evidence re-entries 32.7/wk $1760; recoveries cut 11.4/wk $39931, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $4229/wk, losers avoided $3894/wk, net +1287 $/wk; pnl $16638/wk.
EC_FLAT45K PRE: months missing (5 of 17), window not scored
EC_FLAT45K X': months missing (10 of 10), window not scored


## JN04RM_FLAT45K (6/43 months)
### windows / WF / rule 2a
```
JN04RM_FLAT45K
             cell window  mean_all  mean_ref_all  dmean_all     mean       dd   dd_ref   cut   dmean  eq_cut       w20   w20_ref  calmar  mean_ref  months
0  JN04RM_FLAT45K    L1M    4328.1         340.7     3987.3  11476.1  26857.7  51252.7  47.6 -6062.5    44.5   17312.3    1363.0    22.2   17538.5       6
1  JN04RM_FLAT45K    L3M   12054.4       11956.7       97.7  14485.3  39129.2  77224.2  49.3 -2738.9    46.4  156707.3  155436.8    19.2   17224.1       6
2  JN04RM_FLAT45K    L6M   18870.3       18696.8      173.5  20309.8  39129.2  77224.2  49.3 -1185.1    46.4  160684.7  102383.9    27.0   21494.8       6

```
### acceptance_p7
```
6M P7 sessions of the reference) and the frozen live week: re-entry winners after NEW EVIDENCE
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +22883 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +11869 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +12634 (9 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +9563 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +12231 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 1 ($+4790); all re-entry winners (any evidence) reference 13, set 14
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)

SUMMARY JN04RM_FLAT45K: fails 4 of 15 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
covered sessions 15 of 20
ACCEPT JN04RM_FLAT45K FAIL fails=4/20

```
### behavioural scorecard
JN04RM_FLAT45K L6M (stack, per week): full stops 12.9/wk $-21317; give-backs 10.0/wk (9.8 round-trips) realised $-11217, forgone vs target $28117; same-side losing runs max 13, p95 6, $-44160 lost on 3rd-and-later; no-new-evidence re-entries 45.9/wk $2648; recoveries cut 14.6/wk $38498, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $5321/wk, losers avoided $4203/wk, net +437 $/wk; pnl $19967/wk.
JN04RM_FLAT45K HOLD: months missing (6 of 12), window not scored
JN04RM_FLAT45K PRE: months missing (17 of 17), window not scored
JN04RM_FLAT45K X': months missing (10 of 10), window not scored


## JN04RM_FLAT40K (6/43 months)
### windows / WF / rule 2a
```
JN04RM_FLAT40K
             cell window  mean_all  mean_ref_all  dmean_all     mean       dd   dd_ref   cut   dmean  eq_cut       w20   w20_ref  calmar  mean_ref  months
0  JN04RM_FLAT40K    L1M    2655.2         340.7     2314.4   8890.6  22753.7  51252.7  55.6 -8647.9    51.2   10620.7    1363.0    20.3   17538.5       6
1  JN04RM_FLAT40K    L3M   11526.7       11956.7     -429.9  13824.9  38149.5  77224.2  50.6 -3399.2    45.7  149847.6  155436.8    18.8   17224.1       6
2  JN04RM_FLAT40K    L6M   18183.2       18696.8     -513.6  19552.6  38149.5  77224.2  50.6 -1942.2    45.7  138834.8  102383.9    26.7   21494.8       6

```
### acceptance_p7
```
6M P7 sessions of the reference) and the frozen live week: re-entry winners after NEW EVIDENCE
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +22883 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +11869 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +12634 (9 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +9563 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +12231 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 1 ($+4790); all re-entry winners (any evidence) reference 13, set 14
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)

SUMMARY JN04RM_FLAT40K: fails 4 of 15 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
covered sessions 15 of 20
ACCEPT JN04RM_FLAT40K FAIL fails=4/20

```
### behavioural scorecard
JN04RM_FLAT40K L6M (stack, per week): full stops 12.7/wk $-20930; give-backs 10.0/wk (9.8 round-trips) realised $-11137, forgone vs target $28135; same-side losing runs max 13, p95 7, $-44253 lost on 3rd-and-later; no-new-evidence re-entries 47.5/wk $2488; recoveries cut 14.0/wk $37470, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $7197/wk, losers avoided $6009/wk, net -290 $/wk; pnl $19240/wk.
JN04RM_FLAT40K HOLD: months missing (6 of 12), window not scored
JN04RM_FLAT40K PRE: months missing (17 of 17), window not scored
JN04RM_FLAT40K X': months missing (10 of 10), window not scored

