# DS3_SURVIVORS_X - flat-stop survivors (EC_FLAT{40,45,50}{K,U,A,M} on LPB_BASE; JN04RM_FLAT{40,45,50}K on the JN04RM base), exact, Shadow only, no PASS claim
Updated 2026-11-12 15:22Z. Prereg autopilot/SURVIVORS_X_PREREG.md. Months done per set: EC_FLAT45K 24/43, EC_FLAT40K 3/43, EC_FLAT50K 3/43, EC_FLAT45U 3/43, EC_FLAT40U 0/43, EC_FLAT50U 0/43, EC_FLAT45A 2/43, EC_FLAT40A 0/43, EC_FLAT50A 0/43, EC_FLAT45M 2/43, EC_FLAT40M 0/43, EC_FLAT50M 0/43, JN04RM_FLAT45K 2/43, JN04RM_FLAT40K 2/43, JN04RM_FLAT50K 2/43
Fill model: flat-stop market exit at next-1-s mid -/+ 0.80 pt (live loss-cut is 1.19-1.20 adverse => savings overstated ~0.4 pt). Windows PRE/X/GAP/WF need all 43 months; sets missing months are labelled.

## 1. Trend-week clause (L6M weekly check, exact)
# Weekly check, L6M (ISO weeks with trading days in 2026-05..10; weeks at the month edges are partial; exact engine; Shadow only)

| week | LPB_BASE | JN04RM | EC_FLAT45K |
|--|--|--|--|
| 202638 (best of LPB_BASE) | 88836 | 72104 | 84896 |
| 202623 (best of LPB_BASE) | 73836 | 68072 | 71789 |
| 202625 (best of LPB_BASE) | 59099 | 59990 | 58199 |
| 202639 (best of LPB_BASE) | 57178 | 52634 | 43511 |
| 202633 (best of LPB_BASE) | 52499 | 36328 | 60366 |
| 202644 (worst of LPB_BASE) | -51253 | -16664 | -48569 |
| 202636 (worst of LPB_BASE) | -44984 | -25704 | -41425 |
| 202621 (worst of LPB_BASE) | -39976 | -39092 | -33209 |
| 202635 (worst of LPB_BASE) | -23667 | -15995 | -23846 |
| 202637 (worst of LPB_BASE) | -8573 | 679 | -13749 |

JN04RM: LPB_BASE winning weeks 20 of 27; of those, JN04RM turn losing: 1; weeks where JN04RM beats LPB_BASE: 13 of 27; sum over the 5 best LPB_BASE weeks 289128 vs 331449

EC_FLAT45K: LPB_BASE winning weeks 20 of 27; of those, EC_FLAT45K turn losing: 0; weeks where EC_FLAT45K beats LPB_BASE: 14 of 27; sum over the 5 best LPB_BASE weeks 318762 vs 331449



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

