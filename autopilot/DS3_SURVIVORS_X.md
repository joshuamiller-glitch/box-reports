# DS3_SURVIVORS_X - flat-stop survivors (EC_FLAT{40,45,50}{K,U,A,M} on LPB_BASE; JN04RM_FLAT{40,45,50}K on the JN04RM base), exact, Shadow only, no PASS claim
Updated 2026-11-13 10:47Z. Prereg autopilot/SURVIVORS_X_PREREG.md. Months done per set: EC_FLAT45K 43/43, EC_FLAT40K 43/43, EC_FLAT50K 43/43, EC_FLAT45U 12/43, EC_FLAT40U 1/43, EC_FLAT50U 0/43, EC_FLAT45A 12/43, EC_FLAT40A 0/43, EC_FLAT50A 0/43, EC_FLAT45M 12/43, EC_FLAT40M 0/43, EC_FLAT50M 0/43, JN04RM_FLAT45K 43/43, JN04RM_FLAT40K 43/43, JN04RM_FLAT50K 43/43
Fill model: flat-stop market exit at next-1-s mid -/+ 0.80 pt (live loss-cut is 1.19-1.20 adverse => savings overstated ~0.4 pt). Windows PRE/X/GAP/WF need all 43 months; sets missing months are labelled.

## 1. Trend-week clause (L6M weekly check, exact)
# Weekly check, L6M (ISO weeks with trading days in 2026-05..10; weeks at the month edges are partial; exact engine; Shadow only)

| week | LPB_BASE | JN04RM | EC_FLAT45K | EC_FLAT40K | EC_FLAT50K | EC_FLAT45U | EC_FLAT45A | EC_FLAT45M | JN04RM_FLAT45K | JN04RM_FLAT40K | JN04RM_FLAT50K |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 202638 (best of LPB_BASE) | 88836 | 72104 | 84896 | 78991 | 91066 | 90022 | 92338 | 89140 | 69691 | 69619 | 73422 |
| 202623 (best of LPB_BASE) | 73836 | 68072 | 71789 | 74374 | 68748 | 75544 | 73827 | 73258 | 59775 | 59375 | 56962 |
| 202625 (best of LPB_BASE) | 59099 | 59990 | 58199 | 60023 | 58643 | 61529 | 39940 | 59936 | 59515 | 61822 | 59522 |
| 202639 (best of LPB_BASE) | 57178 | 52634 | 43511 | 46640 | 52887 | 58233 | 57563 | 58179 | 40468 | 41816 | 47257 |
| 202633 (best of LPB_BASE) | 52499 | 36328 | 60366 | 62371 | 57785 | 45345 | 50735 | 52469 | 40954 | 44916 | 38617 |
| 202644 (worst of LPB_BASE) | -51253 | -16664 | -48569 | -45889 | -53032 | -47279 | -42353 | -49556 | -17116 | -16051 | -15353 |
| 202636 (worst of LPB_BASE) | -44984 | -25704 | -41425 | -42588 | -37758 | -35184 | -43861 | -45194 | -21809 | -22520 | -19341 |
| 202621 (worst of LPB_BASE) | -39976 | -39092 | -33209 | -36988 | -34899 | -41688 | -35158 | -40616 | -34871 | -35168 | -33595 |
| 202635 (worst of LPB_BASE) | -23667 | -15995 | -23846 | -26989 | -27638 | -28756 | -25552 | -24041 | -15523 | -15220 | -17310 |
| 202637 (worst of LPB_BASE) | -8573 | 679 | -13749 | -13645 | -11350 | -23118 | -12234 | -10290 | -1797 | -410 | -4673 |

JN04RM: LPB_BASE winning weeks 20 of 27; of those, JN04RM turn losing: 1; weeks where JN04RM beats LPB_BASE: 13 of 27; sum over the 5 best LPB_BASE weeks 289128 vs 331449

EC_FLAT45K: LPB_BASE winning weeks 20 of 27; of those, EC_FLAT45K turn losing: 0; weeks where EC_FLAT45K beats LPB_BASE: 14 of 27; sum over the 5 best LPB_BASE weeks 318762 vs 331449

EC_FLAT40K: LPB_BASE winning weeks 20 of 27; of those, EC_FLAT40K turn losing: 0; weeks where EC_FLAT40K beats LPB_BASE: 15 of 27; sum over the 5 best LPB_BASE weeks 322399 vs 331449

EC_FLAT50K: LPB_BASE winning weeks 20 of 27; of those, EC_FLAT50K turn losing: 0; weeks where EC_FLAT50K beats LPB_BASE: 14 of 27; sum over the 5 best LPB_BASE weeks 329129 vs 331449

EC_FLAT45U: LPB_BASE winning weeks 20 of 27; of those, EC_FLAT45U turn losing: 0; weeks where EC_FLAT45U beats LPB_BASE: 14 of 27; sum over the 5 best LPB_BASE weeks 330674 vs 331449

EC_FLAT45A: LPB_BASE winning weeks 20 of 27; of those, EC_FLAT45A turn losing: 0; weeks where EC_FLAT45A beats LPB_BASE: 15 of 27; sum over the 5 best LPB_BASE weeks 314403 vs 331449

EC_FLAT45M: LPB_BASE winning weeks 20 of 27; of those, EC_FLAT45M turn losing: 0; weeks where EC_FLAT45M beats LPB_BASE: 14 of 27; sum over the 5 best LPB_BASE weeks 332983 vs 331449

JN04RM_FLAT45K: LPB_BASE winning weeks 20 of 27; of those, JN04RM_FLAT45K turn losing: 1; weeks where JN04RM_FLAT45K beats LPB_BASE: 14 of 27; sum over the 5 best LPB_BASE weeks 270403 vs 331449

JN04RM_FLAT40K: LPB_BASE winning weeks 20 of 27; of those, JN04RM_FLAT40K turn losing: 2; weeks where JN04RM_FLAT40K beats LPB_BASE: 15 of 27; sum over the 5 best LPB_BASE weeks 277548 vs 331449

JN04RM_FLAT50K: LPB_BASE winning weeks 20 of 27; of those, JN04RM_FLAT50K turn losing: 1; weeks where JN04RM_FLAT50K beats LPB_BASE: 13 of 27; sum over the 5 best LPB_BASE weeks 275781 vs 331449



## EC_FLAT45K (43/43 months)
### windows / WF / rule 2a
```
EC_FLAT45K
         cell window  mean_all  mean_ref_all  dmean_all     mean        dd    dd_ref  cut   dmean  eq_cut       w20   w20_ref  calmar  mean_ref  wf2w_beat_pct  wf2w_cut  wf2w_mean  months
0  EC_FLAT45K    L1M    1814.1         340.7     1473.4  18608.4   48568.8   51252.7  5.2  1069.8    14.7    7256.4    1363.0    19.9   17538.5           16.5       2.9      -83.3      43
1  EC_FLAT45K    L3M   11624.0       11956.7     -332.7   8966.7   79019.9   77224.2 -2.3   778.5     7.8  151111.9  155436.8     5.9    8188.2           16.5       2.9      -83.3      43
2  EC_FLAT45K    L6M   19992.6       18696.8     1295.7  19051.8   79019.9   77224.2 -2.3  1894.2     7.8  141385.6  102383.9    12.5   17157.6           16.5       2.9      -83.3      43
3  EC_FLAT45K   HOLD   16376.0       15236.3     1139.6  15992.1   83267.6   78842.0 -5.6   817.6     4.9 -331684.1 -377467.2    10.0   15174.5           16.5       2.9      -83.3      43
4  EC_FLAT45K    PRE   10254.7       11685.4    -1430.8  10570.1   96849.9   99479.4  2.6 -1187.2    12.3 -534241.4 -529227.7     5.7   11757.3           16.5       2.9      -83.3      43
5  EC_FLAT45K     X'    1877.5        1333.6      543.9   2859.5  117663.6  122552.7  4.0   306.9    13.5 -299923.9 -321242.1     1.3    2552.6           16.5       2.9      -83.3      43

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

SUMMARY EC_FLAT45K: fails 3 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
covered sessions 20 of 20
ACCEPT EC_FLAT45K FAIL fails=3/20

```
### behavioural scorecard
EC_FLAT45K L6M (stack, per week): full stops 12.8/wk $-23274; give-backs 9.2/wk (9.0 round-trips) realised $-13722, forgone vs target $34912; same-side losing runs max 12, p95 6, $-53101 lost on 3rd-and-later; no-new-evidence re-entries 40.5/wk $873; recoveries cut 12.8/wk $45077, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $4898/wk, losers avoided $4330/wk, net +1371 $/wk; pnl $21155/wk.
EC_FLAT45K HOLD (stack, per week): full stops 11.9/wk $-22193; give-backs 8.1/wk (7.8 round-trips) realised $-11981, forgone vs target $30406; same-side losing runs max 12, p95 6, $-44714 lost on 3rd-and-later; no-new-evidence re-entries 32.7/wk $1760; recoveries cut 11.4/wk $39931, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $4229/wk, losers avoided $3894/wk, net +1287 $/wk; pnl $16638/wk.
EC_FLAT45K PRE (stack, per week): full stops 9.0/wk $-17802; give-backs 5.3/wk (4.9 round-trips) realised $-7545, forgone vs target $19449; same-side losing runs max 11, p95 4, $-23596 lost on 3rd-and-later; no-new-evidence re-entries 14.3/wk $-220; recoveries cut 6.2/wk $21108, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $3348/wk, losers avoided $2759/wk, net -1449 $/wk; pnl $10434/wk.
EC_FLAT45K X' (stack, per week): full stops 10.1/wk $-18198; give-backs 3.7/wk (3.2 round-trips) realised $-4893, forgone vs target $12931; same-side losing runs max 8, p95 4, $-12676 lost on 3rd-and-later; no-new-evidence re-entries 3.5/wk $669; recoveries cut 2.4/wk $9730, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $2166/wk, losers avoided $2297/wk, net +547 $/wk; pnl $1890/wk.


## EC_FLAT40K (43/43 months)
### windows / WF / rule 2a
```
EC_FLAT40K
         cell window  mean_all  mean_ref_all  dmean_all     mean        dd    dd_ref   cut   dmean  eq_cut       w20   w20_ref  calmar  mean_ref  wf2w_beat_pct  wf2w_cut  wf2w_mean  months
0  EC_FLAT40K    L1M     840.1         340.7      499.3 -12694.4   45888.8   51252.7  10.5  3485.5     9.8    3360.2    1363.0   -14.4  -16179.8           16.5       2.9     -457.1      43
1  EC_FLAT40K    L3M   10831.2       11956.7    -1125.5  10541.5   83221.3   77224.2  -7.8 -2101.0    -8.6  140805.3  155436.8     6.6   12642.6           16.5       2.9     -457.1      43
2  EC_FLAT40K    L6M   19006.9       18696.8      310.0  17706.4   83221.3   77224.2  -7.8  -131.6    -8.6  116427.1  102383.9    11.1   17838.0           16.5       2.9     -457.1      43
3  EC_FLAT40K   HOLD   15535.8       15236.3      299.4  16483.3   83734.1   78842.0  -6.2    46.3    -7.0 -358355.2 -377467.2    10.2   16437.0           16.5       2.9     -457.1      43
4  EC_FLAT40K    PRE   10546.2       11685.4    -1139.2  10525.3   93305.9   99479.4   6.2  -960.1     5.5 -530665.0 -529227.7     5.9   11485.4           16.5       2.9     -457.1      43
5  EC_FLAT40K     X'    2123.8        1333.6      790.2   1408.1  111569.8  122552.7   9.0   469.3     8.3 -279219.5 -321242.1     0.7     938.8           16.5       2.9     -457.1      43

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

SUMMARY EC_FLAT40K: fails 3 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
covered sessions 20 of 20
ACCEPT EC_FLAT40K FAIL fails=3/20

```
### behavioural scorecard
EC_FLAT40K L6M (stack, per week): full stops 12.5/wk $-22984; give-backs 9.2/wk (9.0 round-trips) realised $-13425, forgone vs target $34566; same-side losing runs max 12, p95 6, $-53612 lost on 3rd-and-later; no-new-evidence re-entries 42.0/wk $668; recoveries cut 12.3/wk $44028, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $7428/wk, losers avoided $6646/wk, net +328 $/wk; pnl $20112/wk.
EC_FLAT40K HOLD (stack, per week): full stops 11.7/wk $-21941; give-backs 8.0/wk (7.8 round-trips) realised $-11723, forgone vs target $30054; same-side losing runs max 12, p95 6, $-45114 lost on 3rd-and-later; no-new-evidence re-entries 34.0/wk $1389; recoveries cut 10.9/wk $38864, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $6383/wk, losers avoided $5889/wk, net +409 $/wk; pnl $15760/wk.
EC_FLAT40K PRE (stack, per week): full stops 8.7/wk $-17511; give-backs 5.4/wk (5.0 round-trips) realised $-7629, forgone vs target $19679; same-side losing runs max 9, p95 5, $-23816 lost on 3rd-and-later; no-new-evidence re-entries 14.8/wk $-351; recoveries cut 5.8/wk $20333, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $3866/wk, losers avoided $3786/wk, net -1152 $/wk; pnl $10730/wk.
EC_FLAT40K X' (stack, per week): full stops 10.0/wk $-18037; give-backs 3.9/wk (3.3 round-trips) realised $-4797, forgone vs target $12999; same-side losing runs max 8, p95 4, $-12933 lost on 3rd-and-later; no-new-evidence re-entries 4.0/wk $668; recoveries cut 2.4/wk $9600, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $2253/wk, losers avoided $2428/wk, net +795 $/wk; pnl $2138/wk.


## EC_FLAT50K (43/43 months)
### windows / WF / rule 2a
```
EC_FLAT50K
         cell window  mean_all  mean_ref_all  dmean_all     mean        dd    dd_ref  cut  dmean  eq_cut       w20   w20_ref  calmar  mean_ref  wf2w_beat_pct  wf2w_cut  wf2w_mean  months
0  EC_FLAT50K    L1M     922.0         340.7      581.2   -437.6   53031.7   51252.7 -3.5   12.5    -1.0    3687.8    1363.0    -0.4    -450.1           20.3       9.2     -193.9      43
1  EC_FLAT50K    L3M   12173.7       11956.7      217.0  16334.7   76745.6   77224.2  0.6 -367.0     3.0  158258.1  155436.8    11.1   16701.7           20.3       9.2     -193.9      43
2  EC_FLAT50K    L6M   19500.9       18696.8      804.1  20144.5   76745.6   77224.2  0.6  483.3     3.0  126175.8  102383.9    13.6   19661.1           20.3       9.2     -193.9      43
3  EC_FLAT50K   HOLD   16045.4       15236.3      809.0  15673.2   84159.6   78842.0 -6.7  498.7    -4.2 -362267.5 -377467.2     9.7   15174.5           20.3       9.2     -193.9      43
4  EC_FLAT50K    PRE   11449.6       11685.4     -235.8  11378.8   90299.5   99479.4  9.2 -120.8    11.4 -529190.3 -529227.7     6.6   11499.6           20.3       9.2     -193.9      43
5  EC_FLAT50K     X'    1330.0        1333.6       -3.6   1788.4  115243.8  122552.7  6.0  193.0     8.2 -307142.2 -321242.1     0.8    1595.4           20.3       9.2     -193.9      43

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

SUMMARY EC_FLAT50K: fails 3 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
covered sessions 20 of 20
ACCEPT EC_FLAT50K FAIL fails=3/20

```
### behavioural scorecard
EC_FLAT50K L6M (stack, per week): full stops 14.8/wk $-25798; give-backs 9.2/wk (9.1 round-trips) realised $-13862, forgone vs target $35101; same-side losing runs max 12, p95 6, $-52287 lost on 3rd-and-later; no-new-evidence re-entries 38.8/wk $636; recoveries cut 13.4/wk $46233, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $2882/wk, losers avoided $3282/wk, net +851 $/wk; pnl $20635/wk.
EC_FLAT50K HOLD (stack, per week): full stops 13.8/wk $-24620; give-backs 8.1/wk (7.8 round-trips) realised $-12125, forgone vs target $30573; same-side losing runs max 12, p95 6, $-43986 lost on 3rd-and-later; no-new-evidence re-entries 31.4/wk $1292; recoveries cut 11.9/wk $40924, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $2657/wk, losers avoided $2853/wk, net +890 $/wk; pnl $16241/wk.
EC_FLAT50K PRE (stack, per week): full stops 10.2/wk $-19501; give-backs 5.3/wk (4.9 round-trips) realised $-7593, forgone vs target $19546; same-side losing runs max 11, p95 4, $-22957 lost on 3rd-and-later; no-new-evidence re-entries 13.5/wk $67; recoveries cut 6.3/wk $21478, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $2383/wk, losers avoided $2213/wk, net -233 $/wk; pnl $11649/wk.
EC_FLAT50K X' (stack, per week): full stops 10.6/wk $-18834; give-backs 3.5/wk (3.0 round-trips) realised $-4884, forgone vs target $12784; same-side losing runs max 7, p95 4, $-12506 lost on 3rd-and-later; no-new-evidence re-entries 3.1/wk $694; recoveries cut 2.5/wk $9857, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $1591/wk, losers avoided $1706/wk, net -4 $/wk; pnl $1339/wk.


## EC_FLAT45U (12/43 months)
### windows / WF / rule 2a
```
EC_FLAT45U
         cell window  mean_all  mean_ref_all  dmean_all     mean       dd   dd_ref   cut   dmean  eq_cut       w20   w20_ref  calmar  mean_ref  months
0  EC_FLAT45U    L1M    2981.9         340.7     2641.1 -14100.2  47278.7  51252.7   7.8  2079.7     7.0   11927.5    1363.0   -15.5  -16179.8      12
1  EC_FLAT45U    L3M   11463.2       11956.7     -493.5  14345.0  87057.2  77224.2 -12.7   677.4   -13.7  149021.5  155436.8     8.6   13667.5      12
2  EC_FLAT45U    L6M   17977.2       18696.8     -719.6  19621.0  87057.2  77224.2 -12.7  -166.6   -13.7   78742.5  102383.9    11.7   19787.7      12
3  EC_FLAT45U   HOLD   15321.2       15236.3       84.8  14850.4  87057.2  78842.0 -10.4   451.2   -11.4 -387657.6 -377467.2     8.9   14399.3      12

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

SUMMARY EC_FLAT45U: fails 3 of 16 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
covered sessions 16 of 20
ACCEPT EC_FLAT45U FAIL fails=3/20

```
### behavioural scorecard
EC_FLAT45U L6M (stack, per week): full stops 21.4/wk $-29899; give-backs 9.1/wk (9.0 round-trips) realised $-13940, forgone vs target $35415; same-side losing runs max 12, p95 6, $-51327 lost on 3rd-and-later; no-new-evidence re-entries 37.3/wk $-547; recoveries cut 13.6/wk $46652, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $244/wk, losers avoided $456/wk, net -761 $/wk; pnl $19022/wk.
EC_FLAT45U HOLD (stack, per week): full stops 20.0/wk $-28211; give-backs 8.0/wk (7.8 round-trips) realised $-12002, forgone vs target $30516; same-side losing runs max 12, p95 6, $-43496 lost on 3rd-and-later; no-new-evidence re-entries 30.1/wk $608; recoveries cut 12.2/wk $41577, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $308/wk, losers avoided $489/wk, net +87 $/wk; pnl $15439/wk.
EC_FLAT45U PRE: months missing (17 of 17), window not scored
EC_FLAT45U X': months missing (10 of 10), window not scored


## EC_FLAT45A (12/43 months)
### windows / WF / rule 2a
```
EC_FLAT45A
         cell window  mean_all  mean_ref_all  dmean_all     mean       dd   dd_ref   cut   dmean  eq_cut       w20   w20_ref  calmar  mean_ref  months
0  EC_FLAT45A    L1M    9401.5         340.7     9060.8 -13119.9  42352.9  51252.7  17.4  3059.9    13.7   37606.0    1363.0   -16.1  -16179.8      12
1  EC_FLAT45A    L3M   14474.4       11956.7     2517.7   9266.8  81646.7  77224.2  -5.7   472.2   -10.4  188166.7  155436.8     5.9    8794.5      12
2  EC_FLAT45A    L6M   19034.5       18696.8      337.6  16717.2  81646.7  77224.2  -5.7  -731.4   -10.4   96233.8  102383.9    10.6   17448.6      12
3  EC_FLAT45A   HOLD   15173.8       15236.3      -62.6  13962.2  81646.7  78842.0  -3.6  -594.4    -8.1 -357741.6 -377467.2     8.9   14556.6      12

```
### acceptance_p7
```
 best L6M P7 sessions of the reference) and the frozen live week: re-entry winners after NEW EVIDENCE
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +27616 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +23369 (8 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +23252 (7 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +22466 (6 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +22396 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 1 ($+8402); all re-entry winners (any evidence) reference 13, set 12
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)

SUMMARY EC_FLAT45A: fails 3 of 16 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
covered sessions 16 of 20
ACCEPT EC_FLAT45A FAIL fails=3/20

```
### behavioural scorecard
EC_FLAT45A L6M (stack, per week): full stops 20.8/wk $-36120; give-backs 9.0/wk (8.9 round-trips) realised $-14037, forgone vs target $35198; same-side losing runs max 12, p95 6, $-51067 lost on 3rd-and-later; no-new-evidence re-entries 37.2/wk $199; recoveries cut 13.5/wk $46419, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $2488/wk, losers avoided $1171/wk, net +357 $/wk; pnl $20141/wk.
EC_FLAT45A HOLD (stack, per week): full stops 20.0/wk $-34956; give-backs 7.9/wk (7.7 round-trips) realised $-12281, forgone vs target $30706; same-side losing runs max 12, p95 6, $-43257 lost on 3rd-and-later; no-new-evidence re-entries 29.8/wk $1093; recoveries cut 12.1/wk $41257, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $2252/wk, losers avoided $1372/wk, net -64 $/wk; pnl $15287/wk.
EC_FLAT45A PRE: months missing (17 of 17), window not scored
EC_FLAT45A X': months missing (10 of 10), window not scored


## EC_FLAT45M (12/43 months)
### windows / WF / rule 2a
```
EC_FLAT45M
         cell window  mean_all  mean_ref_all  dmean_all     mean       dd   dd_ref  cut  dmean  eq_cut       w20   w20_ref  calmar  mean_ref  months
0  EC_FLAT45M    L1M    1129.7         340.7      789.0  18024.9  49555.7  51252.7  3.3  486.3     2.9    4519.0    1363.0    18.9   17538.5      12
1  EC_FLAT45M    L3M   12109.7       11956.7      153.0  13976.4  79524.9  77224.2 -3.0  308.9    -3.4  157426.0  155436.8     9.1   13667.5      12
2  EC_FLAT45M    L6M   18466.6       18696.8     -230.3  17279.9  79524.9  77224.2 -3.0  -73.4    -3.4   96840.4  102383.9    11.3   17353.3      12
3  EC_FLAT45M   HOLD   14906.0       15236.3     -330.3  14254.5  79524.9  78842.0 -0.9 -255.4    -1.3 -380890.5 -377467.2     9.3   14509.9      12

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

SUMMARY EC_FLAT45M: fails 3 of 16 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
covered sessions 16 of 20
ACCEPT EC_FLAT45M FAIL fails=3/20

```
### behavioural scorecard
EC_FLAT45M L6M (stack, per week): full stops 22.9/wk $-37793; give-backs 9.1/wk (9.0 round-trips) realised $-14032, forgone vs target $35497; same-side losing runs max 12, p95 6, $-51247 lost on 3rd-and-later; no-new-evidence re-entries 37.4/wk $-320; recoveries cut 13.3/wk $45975, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $244/wk, losers avoided $58/wk, net -244 $/wk; pnl $19540/wk.
EC_FLAT45M HOLD (stack, per week): full stops 21.5/wk $-35980; give-backs 8.1/wk (7.9 round-trips) realised $-12222, forgone vs target $30890; same-side losing runs max 12, p95 6, $-43670 lost on 3rd-and-later; no-new-evidence re-entries 30.2/wk $730; recoveries cut 12.0/wk $41170, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $237/wk, losers avoided $67/wk, net -342 $/wk; pnl $15010/wk.
EC_FLAT45M PRE: months missing (17 of 17), window not scored
EC_FLAT45M X': months missing (10 of 10), window not scored


## JN04RM_FLAT45K (43/43 months)
### windows / WF / rule 2a
```
JN04RM_FLAT45K
             cell window  mean_all  mean_ref_all  dmean_all     mean       dd    dd_ref   cut   dmean  eq_cut       w20   w20_ref  calmar  mean_ref  wf2w_beat_pct  wf2w_cut  wf2w_mean  months
0  JN04RM_FLAT45K    L1M    4328.1         340.7     3987.3  11476.1  26857.7   51252.7  47.6 -6062.5    44.5   17312.3    1363.0    22.2   17538.5           74.7      12.5    -3557.4      43
1  JN04RM_FLAT45K    L3M   12054.4       11956.7       97.7  14485.3  39129.2   77224.2  49.3 -2738.9    46.4  156707.3  155436.8    19.2   17224.1           74.7      12.5    -3557.4      43
2  JN04RM_FLAT45K    L6M   18870.3       18696.8      173.5  20309.8  39129.2   77224.2  49.3 -1185.1    46.4  160684.7  102383.9    27.0   21494.8           74.7      12.5    -3557.4      43
3  JN04RM_FLAT45K   HOLD   12823.3       15236.3    -2413.1  13304.3  87042.0   78842.0 -10.4 -1564.4   -16.8 -262124.0 -377467.2     7.9   14868.7           74.7      12.5    -3557.4      43
4  JN04RM_FLAT45K    PRE    7684.6       11685.4    -4000.9   7198.3  69989.3   99479.4  29.6 -3350.1    25.5 -367951.9 -529227.7     5.3   10548.4           74.7      12.5    -3557.4      43
5  JN04RM_FLAT45K     X'    2340.8        1333.6     1007.1   2781.6  63498.5  122552.7  48.2   229.0    45.2 -195468.3 -321242.1     2.3    2552.6           74.7      12.5    -3557.4      43

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

SUMMARY JN04RM_FLAT45K: fails 4 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
covered sessions 20 of 20
ACCEPT JN04RM_FLAT45K FAIL fails=4/20

```
### behavioural scorecard
JN04RM_FLAT45K L6M (stack, per week): full stops 12.9/wk $-21317; give-backs 10.0/wk (9.8 round-trips) realised $-11217, forgone vs target $28117; same-side losing runs max 13, p95 6, $-44160 lost on 3rd-and-later; no-new-evidence re-entries 45.9/wk $2648; recoveries cut 14.6/wk $38498, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $5321/wk, losers avoided $4203/wk, net +437 $/wk; pnl $19967/wk.
JN04RM_FLAT45K HOLD (stack, per week): full stops 12.1/wk $-20080; give-backs 8.7/wk (8.4 round-trips) realised $-9659, forgone vs target $24375; same-side losing runs max 13, p95 6, $-37546 lost on 3rd-and-later; no-new-evidence re-entries 36.6/wk $1906; recoveries cut 12.5/wk $32652, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $4363/wk, losers avoided $4077/wk, net +462 $/wk; pnl $12959/wk.
JN04RM_FLAT45K PRE (stack, per week): full stops 9.1/wk $-16195; give-backs 5.5/wk (5.1 round-trips) realised $-5636, forgone vs target $14648; same-side losing runs max 11, p95 5, $-18844 lost on 3rd-and-later; no-new-evidence re-entries 16.0/wk $-160; recoveries cut 6.8/wk $16065, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $2860/wk, losers avoided $2283/wk, net -1590 $/wk; pnl $7819/wk.
JN04RM_FLAT45K X' (stack, per week): full stops 10.1/wk $-17063; give-backs 3.7/wk (3.1 round-trips) realised $-3602, forgone vs target $9978; same-side losing runs max 8, p95 4, $-10315 lost on 3rd-and-later; no-new-evidence re-entries 3.8/wk $668; recoveries cut 2.4/wk $6258, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $2001/wk, losers avoided $2183/wk, net +809 $/wk; pnl $2356/wk.


## JN04RM_FLAT40K (43/43 months)
### windows / WF / rule 2a
```
JN04RM_FLAT40K
             cell window  mean_all  mean_ref_all  dmean_all     mean       dd    dd_ref   cut   dmean  eq_cut       w20   w20_ref  calmar  mean_ref  wf2w_beat_pct  wf2w_cut  wf2w_mean  months
0  JN04RM_FLAT40K    L1M    2655.2         340.7     2314.4   8890.6  22753.7   51252.7  55.6 -8647.9    51.2   10620.7    1363.0    20.3   17538.5           75.9      16.2    -4026.2      43
1  JN04RM_FLAT40K    L3M   11526.7       11956.7     -429.9  13824.9  38149.5   77224.2  50.6 -3399.2    45.7  149847.6  155436.8    18.8   17224.1           75.9      16.2    -4026.2      43
2  JN04RM_FLAT40K    L6M   18183.2       18696.8     -513.6  19552.6  38149.5   77224.2  50.6 -1942.2    45.7  138834.8  102383.9    26.7   21494.8           75.9      16.2    -4026.2      43
3  JN04RM_FLAT40K   HOLD   11869.4       15236.3    -3366.9  12236.1  81186.0   78842.0  -3.0 -2632.6   -13.2 -270927.5 -377467.2     7.8   14868.7           75.9      16.2    -4026.2      43
4  JN04RM_FLAT40K    PRE    7388.4       11685.4    -4297.0   6902.1  83403.9   99479.4  16.2 -3646.3     7.8 -375632.0 -529227.7     4.3   10548.4           75.9      16.2    -4026.2      43
5  JN04RM_FLAT40K     X'    2214.9        1333.6      881.3   2764.9  57216.0  122552.7  53.3   212.2    48.7 -191427.9 -321242.1     2.5    2552.6           75.9      16.2    -4026.2      43

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

SUMMARY JN04RM_FLAT40K: fails 4 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
covered sessions 20 of 20
ACCEPT JN04RM_FLAT40K FAIL fails=4/20

```
### behavioural scorecard
JN04RM_FLAT40K L6M (stack, per week): full stops 12.7/wk $-20930; give-backs 10.0/wk (9.8 round-trips) realised $-11137, forgone vs target $28135; same-side losing runs max 13, p95 7, $-44253 lost on 3rd-and-later; no-new-evidence re-entries 47.5/wk $2488; recoveries cut 14.0/wk $37470, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $7197/wk, losers avoided $6009/wk, net -290 $/wk; pnl $19240/wk.
JN04RM_FLAT40K HOLD (stack, per week): full stops 11.9/wk $-19804; give-backs 8.6/wk (8.4 round-trips) realised $-9501, forgone vs target $24169; same-side losing runs max 13, p95 6, $-37741 lost on 3rd-and-later; no-new-evidence re-entries 37.9/wk $1480; recoveries cut 11.9/wk $31474, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $6246/wk, losers avoided $5613/wk, net -499 $/wk; pnl $11998/wk.
JN04RM_FLAT40K PRE (stack, per week): full stops 8.9/wk $-15869; give-backs 5.5/wk (5.2 round-trips) realised $-5674, forgone vs target $14751; same-side losing runs max 12, p95 5, $-19250 lost on 3rd-and-later; no-new-evidence re-entries 16.8/wk $-381; recoveries cut 6.3/wk $15257, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $3232/wk, losers avoided $2886/wk, net -1891 $/wk; pnl $7517/wk.
JN04RM_FLAT40K X' (stack, per week): full stops 10.1/wk $-17007; give-backs 3.8/wk (3.3 round-trips) realised $-3534, forgone vs target $10074; same-side losing runs max 8, p95 4, $-10580 lost on 3rd-and-later; no-new-evidence re-entries 4.3/wk $556; recoveries cut 2.3/wk $6125, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $2224/wk, losers avoided $2287/wk, net +682 $/wk; pnl $2229/wk.


## JN04RM_FLAT50K (43/43 months)
### windows / WF / rule 2a
```
JN04RM_FLAT50K
             cell window  mean_all  mean_ref_all  dmean_all     mean       dd    dd_ref   cut   dmean  eq_cut       w20   w20_ref  calmar  mean_ref  wf2w_beat_pct  wf2w_cut  wf2w_mean  months
0  JN04RM_FLAT50K    L1M    4143.6         340.7     3802.8  10642.3  27513.3   51252.7  46.3 -6896.2    39.9   16574.2    1363.0    20.1   17538.5           87.3      22.8    -3317.2      43
1  JN04RM_FLAT50K    L3M   12061.3       11956.7      104.6  14345.8  41324.0   77224.2  46.5 -2878.4    40.1  156796.4  155436.8    18.1   17224.1           87.3      22.8    -3317.2      43
2  JN04RM_FLAT50K    L6M   17869.6       18696.8     -827.2  19198.5  41324.0   77224.2  46.5 -2296.3    40.1  131515.6  102383.9    24.2   21494.8           87.3      22.8    -3317.2      43
3  JN04RM_FLAT50K   HOLD   12476.7       15236.3    -2759.6  13022.4  76827.5   78842.0   2.6 -3517.7    -9.1 -273687.4 -377467.2     8.8   16540.1           87.3      22.8    -3317.2      43
4  JN04RM_FLAT50K    PRE    8494.7       11685.4    -3190.7   7978.2  72122.2   99479.4  27.5 -2570.2    18.8 -354254.3 -529227.7     5.8   10548.4           87.3      22.8    -3317.2      43
5  JN04RM_FLAT50K     X'    1830.3        1333.6      496.7   2362.6  59334.0  122552.7  51.6  -190.0    45.8 -202998.7 -321242.1     2.1    2552.6           87.3      22.8    -3317.2      43

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

SUMMARY JN04RM_FLAT50K: fails 4 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
covered sessions 20 of 20
ACCEPT JN04RM_FLAT50K FAIL fails=4/20

```
### behavioural scorecard
JN04RM_FLAT50K L6M (stack, per week): full stops 15.1/wk $-24034; give-backs 10.1/wk (9.9 round-trips) realised $-11415, forgone vs target $28364; same-side losing runs max 13, p95 6, $-43953 lost on 3rd-and-later; no-new-evidence re-entries 44.7/wk $2244; recoveries cut 14.8/wk $38795, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $3236/wk, losers avoided $2851/wk, net -622 $/wk; pnl $18909/wk.
JN04RM_FLAT50K HOLD (stack, per week): full stops 14.1/wk $-22559; give-backs 8.7/wk (8.4 round-trips) realised $-9800, forgone vs target $24516; same-side losing runs max 13, p95 6, $-37246 lost on 3rd-and-later; no-new-evidence re-entries 35.6/wk $1377; recoveries cut 12.7/wk $33012, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $2758/wk, losers avoided $2873/wk, net +88 $/wk; pnl $12585/wk.
JN04RM_FLAT50K PRE (stack, per week): full stops 10.3/wk $-17661; give-backs 5.5/wk (5.1 round-trips) realised $-5660, forgone vs target $14672; same-side losing runs max 11, p95 5, $-18334 lost on 3rd-and-later; no-new-evidence re-entries 15.1/wk $113; recoveries cut 6.8/wk $16254, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $2236/wk, losers avoided $1870/wk, net -766 $/wk; pnl $8643/wk.
JN04RM_FLAT50K X' (stack, per week): full stops 10.7/wk $-17827; give-backs 3.5/wk (3.0 round-trips) realised $-3581, forgone vs target $9766; same-side losing runs max 7, p95 4, $-10042 lost on 3rd-and-later; no-new-evidence re-entries 3.4/wk $741; recoveries cut 2.4/wk $6347, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $1562/wk, losers avoided $1658/wk, net +295 $/wk; pnl $1842/wk.

