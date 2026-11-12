# DS3_NEXT_FEATURES_F3 - T-NEXT-FEATURES items 3 (hold-or-take by location) and 4 (flat cut by context). W-F3. Shadow only, no PASS claim.
Updated 2026-11-12 19:48Z. Directive autopilot/DIRECTIVE_T_NEXT_FEATURES_20261112.md; prereg autopilot/NEXTF3_PREREG.md (sha in DECISIONS.md). BASE = JN05W2 (LPB panel + F3 + E1 + C22 + BR3S + FLAT45K, exact 43 months, W-J). Item-4 sets keep FLAT45K on K7 unless the cell says replace. Exact sets run one per job (jn05_run2.py, TP engine, tag NEXTF); months done: NC_U7_T10_15F 6/43, NC_U7_T20_15F 6/43, NC_U7_T20_15A 6/43, NC_K7_T20_20RC 6/43, NC_K7_F55_45 6/43, NC_A7_T10_10F 6/43, NC_M7_T10_10A 6/43, NC_K7_T30_10RC 0/43, NH_P7_A9_N20 5/43, NH_P7_B9_X10N30 5/43, NH_U7_B7_X20N60 5/43, NH_M7_C9_F2 5/43, NH_M7_B9_X10N60 5/43, NH_P7_B7_X10N60 0/43, NH_U7_B7_X30N120 0/43

Reading rule: exact is the verdict; first-order (FO sections) only chose the cells. Mean columns: mean_all (all weeks) vs ref; dmean carry-dropped is not used here. R-vs-dollar note: both items are location rules (points / fractions of target / minutes), independent of lot size, so they transfer unchanged to the user's x1.75 lots; only the dollar P&L scales.

## 0. Identity checks (hook with no rules == JN05W2 on 202610)
```
IDENTITY NC_ID trades 598 598 net 25943.82 25943.82 IDENTICAL

IDENTITY NH_ID trades 598 598 net 25943.82 25943.82 IDENTICAL

```

## 1. Trend-week clause FIRST (L6M, exact; sum of the 5 best LPB_BASE weeks, winning weeks turned losing)

| set | 5 best LPB_BASE weeks sum (LPB_BASE 331449; JN05W2 255545) | LPB winning weeks turned losing (of 20) | JN05W2 winning weeks turned losing (of 20) | weeks beats JN05W2 (of 27) |
|--|--|--|--|--|
| NC_U7_T10_15F | 261019 | 0 | 0 | 16 |
| NC_U7_T20_15F | 261701 | 0 | 0 | 15 |
| NC_U7_T20_15A | 257255 | 0 | 0 | 16 |
| NC_K7_T20_20RC | 254442 | 2 | 0 | 11 |
| NC_K7_F55_45 | 254328 | 1 | 0 | 7 |
| NC_A7_T10_10F | 261686 | 1 | 0 | 7 |
| NC_M7_T10_10A | 253346 | 1 | 0 | 10 |


## 2.NC_U7_T10_15F (6/43 months)
### windows vs JN05W2 (nf_score)
```
NC_U7_T10_15F
            cell     ref window  mean_all  ref_all  dmean_all       dd   dd_ref   cut  eq_cut  w20cut  months
0  NC_U7_T10_15F  JN05W2    L1M    3190.3    606.3     2584.0  31571.5  36370.5  13.2    16.6   426.2       6
1  NC_U7_T10_15F  JN05W2    L3M   17258.8  16015.2     1243.6  32116.9  36370.5  11.7    15.2     7.8       6
2  NC_U7_T10_15F  JN05W2    L6M   25709.5  25136.9      572.6  32116.9  36370.5  11.7    15.2     7.7       6

```
### windows vs LPB_BASE (score_w)
```
NC_U7_T10_15F
            cell window  mean_all  mean_ref_all  dmean_all     mean       dd   dd_ref   cut    dmean  eq_cut       w20   w20_ref  calmar  mean_ref  months
0  NC_U7_T10_15F    L1M    3190.3         340.7     2849.5  -5737.3  31571.5  51252.7  38.4  10442.5    51.8   12761.0    1363.0    -9.4  -16179.8       6
1  NC_U7_T10_15F    L3M   17258.8       11956.7     5302.1  17430.8  32116.9  77224.2  58.4   2505.5    67.5  224363.9  155436.8    28.2   14925.3       6
2  NC_U7_T10_15F    L6M   25709.5       18696.8     7012.7  23852.2  32116.9  77224.2  58.4   5191.8    67.5  283907.1  102383.9    38.6   18660.5       6

```
### acceptance_p7
```
 P7 sessions of the reference) and the frozen live week: re-entry winners after NEW EVIDENCE
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +25963 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +14034 (5 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +21574 (5 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +17327 (5 trades, 1 such winners $+4790)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net -4895 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 4 ($+20390); all re-entry winners (any evidence) reference 13, set 14
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)

SUMMARY NC_U7_T10_15F: fails 1 of 15 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->1', '0->0']
covered sessions 15 of 20
ACCEPT NC_U7_T10_15F PASS fails=1/20

```
### behavioural scorecard (ref JN05W2)
NC_U7_T10_15F L6M (stack, per week): full stops 10.6/wk $-19315; give-backs 7.6/wk (7.4 round-trips) realised $-10489, forgone vs target $28044; same-side losing runs max 13, p95 6, $-44516 lost on 3rd-and-later; no-new-evidence re-entries 32.9/wk $1001; recoveries cut 12.2/wk $47901, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $0/wk, losers avoided $127/wk, net +606 $/wk; pnl $27204/wk.
NC_U7_T10_15F HOLD: months missing (6 of 12), window not scored
NC_U7_T10_15F PRE: months missing (17 of 17), window not scored
NC_U7_T10_15F X': months missing (10 of 10), window not scored


## 2.NC_U7_T20_15F (6/43 months)
### windows vs JN05W2 (nf_score)
```
NC_U7_T20_15F
            cell     ref window  mean_all  ref_all  dmean_all       dd   dd_ref  cut  eq_cut  w20cut  months
0  NC_U7_T20_15F  JN05W2    L1M    2318.8    606.3     1712.5  35057.5  36370.5  3.6     7.1   282.4       6
1  NC_U7_T20_15F  JN05W2    L3M   16946.4  16015.2      931.2  35057.5  36370.5  3.6     7.1     5.8       6
2  NC_U7_T20_15F  JN05W2    L6M   25646.4  25136.9      509.5  35057.5  36370.5  3.6     7.1     7.2       6

```
### windows vs LPB_BASE (score_w)
```
NC_U7_T20_15F
            cell window  mean_all  mean_ref_all  dmean_all     mean       dd   dd_ref   cut   dmean  eq_cut       w20   w20_ref  calmar  mean_ref  months
0  NC_U7_T20_15F    L1M    2318.8         340.7     1978.0  -6899.3  35057.5  51252.7  31.6  9280.5    46.3    9275.0    1363.0   -10.2  -16179.8       6
1  NC_U7_T20_15F    L3M   16946.4       11956.7     4989.7  17092.4  35057.5  77224.2  54.6  2167.1    64.4  220303.4  155436.8    25.4   14925.3       6
2  NC_U7_T20_15F    L6M   25646.4       18696.8     6949.6  23786.6  35057.5  77224.2  54.6  5126.1    64.4  282588.0  102383.9    35.3   18660.5       6

```
### acceptance_p7
```
 P7 sessions of the reference) and the frozen live week: re-entry winners after NEW EVIDENCE
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +25963 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +14034 (5 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +21574 (5 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +17327 (5 trades, 1 such winners $+4790)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net -4895 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 4 ($+20390); all re-entry winners (any evidence) reference 13, set 14
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)

SUMMARY NC_U7_T20_15F: fails 1 of 15 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->1', '0->0']
covered sessions 15 of 20
ACCEPT NC_U7_T20_15F PASS fails=1/20

```
### behavioural scorecard (ref JN05W2)
NC_U7_T20_15F L6M (stack, per week): full stops 10.7/wk $-19717; give-backs 7.6/wk (7.4 round-trips) realised $-10489, forgone vs target $28044; same-side losing runs max 13, p95 6, $-44604 lost on 3rd-and-later; no-new-evidence re-entries 32.9/wk $1001; recoveries cut 12.2/wk $47901, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $0/wk, losers avoided $127/wk, net +539 $/wk; pnl $27137/wk.
NC_U7_T20_15F HOLD: months missing (6 of 12), window not scored
NC_U7_T20_15F PRE: months missing (17 of 17), window not scored
NC_U7_T20_15F X': months missing (10 of 10), window not scored


## 2.NC_U7_T20_15A (6/43 months)
### windows vs JN05W2 (nf_score)
```
NC_U7_T20_15A
            cell     ref window  mean_all  ref_all  dmean_all       dd   dd_ref   cut  eq_cut  w20cut  months
0  NC_U7_T20_15A  JN05W2    L1M    3013.1    606.3     2406.8  32421.5  36370.5  10.9    12.0   397.0       6
1  NC_U7_T20_15A  JN05W2    L3M   16931.1  16015.2      915.9  33509.9  36370.5   7.9     9.1     5.7       6
2  NC_U7_T20_15A  JN05W2    L6M   25109.7  25136.9      -27.2  33509.9  36370.5   7.9     9.1     1.9       6

```
### windows vs LPB_BASE (score_w)
```
NC_U7_T20_15A
            cell window  mean_all  mean_ref_all  dmean_all     mean       dd   dd_ref   cut    dmean  eq_cut       w20   w20_ref  calmar  mean_ref  months
0  NC_U7_T20_15A    L1M    3013.1         340.7     2672.4  -5973.5  32421.5  51252.7  36.7  10206.4    49.2   12052.5    1363.0    -9.6  -16179.8       6
1  NC_U7_T20_15A    L3M   16931.1       11956.7     4974.4  17075.8  33509.9  77224.2  56.6   2150.5    65.1  220104.4  155436.8    26.5   14925.3       6
2  NC_U7_T20_15A    L6M   25109.7       18696.8     6412.9  23228.5  33509.9  77224.2  56.6   4568.0    65.1  268500.5  102383.9    36.0   18660.5       6

```
### acceptance_p7
```
 P7 sessions of the reference) and the frozen live week: re-entry winners after NEW EVIDENCE
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +25963 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +14034 (5 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +21574 (5 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +17327 (5 trades, 1 such winners $+4790)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net -4895 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 4 ($+20390); all re-entry winners (any evidence) reference 13, set 14
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)

SUMMARY NC_U7_T20_15A: fails 1 of 15 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->1', '0->0']
covered sessions 15 of 20
ACCEPT NC_U7_T20_15A PASS fails=1/20

```
### behavioural scorecard (ref JN05W2)
NC_U7_T20_15A L6M (stack, per week): full stops 10.3/wk $-18613; give-backs 7.5/wk (7.4 round-trips) realised $-10470, forgone vs target $27976; same-side losing runs max 13, p95 6, $-44331 lost on 3rd-and-later; no-new-evidence re-entries 32.8/wk $805; recoveries cut 12.0/wk $47526, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $390/wk, losers avoided $582/wk, net -29 $/wk; pnl $26570/wk.
NC_U7_T20_15A HOLD: months missing (6 of 12), window not scored
NC_U7_T20_15A PRE: months missing (17 of 17), window not scored
NC_U7_T20_15A X': months missing (10 of 10), window not scored


## 2.NC_K7_T20_20RC (6/43 months)
### windows vs JN05W2 (nf_score)
```
NC_K7_T20_20RC
             cell     ref window  mean_all  ref_all  dmean_all       dd   dd_ref   cut  eq_cut  w20cut  months
0  NC_K7_T20_20RC  JN05W2    L1M    2231.2    606.3     1624.9  27605.1  36370.5  24.1    22.9   268.0       6
1  NC_K7_T20_20RC  JN05W2    L3M   17447.2  16015.2     1432.0  27605.1  36370.5  24.1    22.9     8.9       6
2  NC_K7_T20_20RC  JN05W2    L6M   25076.1  25136.9      -60.8  27605.1  36370.5  24.1    22.9     2.3       6

```
### windows vs LPB_BASE (score_w)
```
NC_K7_T20_20RC
             cell window  mean_all  mean_ref_all  dmean_all     mean       dd   dd_ref   cut    dmean  eq_cut       w20   w20_ref  calmar  mean_ref  months
0  NC_K7_T20_20RC    L1M    2231.2         340.7     1890.4  -4730.3  27605.1  51252.7  46.1  11449.6    56.8    8924.7    1363.0    -8.9  -16179.8       6
1  NC_K7_T20_20RC    L3M   17447.2       11956.7     5490.6  17671.5  27605.1  77224.2  64.3   2746.2    71.3  226814.0  155436.8    33.3   14925.3       6
2  NC_K7_T20_20RC    L6M   25076.1       18696.8     6379.3  23272.6  27605.1  77224.2  64.3   4612.1    71.3  269730.6  102383.9    43.8   18660.5       6

```
### acceptance_p7
```
7 sessions of the reference) and the frozen live week: re-entry winners after NEW EVIDENCE
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +25963 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +14034 (5 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +21574 (5 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +17327 (5 trades, 1 such winners $+4790)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net -4895 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 4 ($+20390); all re-entry winners (any evidence) reference 13, set 14
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)

SUMMARY NC_K7_T20_20RC: fails 1 of 15 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->1', '0->0']
covered sessions 15 of 20
ACCEPT NC_K7_T20_20RC PASS fails=1/20

```
### behavioural scorecard (ref JN05W2)
NC_K7_T20_20RC L6M (stack, per week): full stops 11.2/wk $-21326; give-backs 7.6/wk (7.4 round-trips) realised $-10539, forgone vs target $28093; same-side losing runs max 13, p95 6, $-45039 lost on 3rd-and-later; no-new-evidence re-entries 33.6/wk $1214; recoveries cut 12.0/wk $47425, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $1317/wk, losers avoided $1831/wk, net -64 $/wk; pnl $26534/wk.
NC_K7_T20_20RC HOLD: months missing (6 of 12), window not scored
NC_K7_T20_20RC PRE: months missing (17 of 17), window not scored
NC_K7_T20_20RC X': months missing (10 of 10), window not scored


## 2.NC_K7_F55_45 (6/43 months)
### windows vs JN05W2 (nf_score)
```
NC_K7_F55_45
           cell     ref window  mean_all  ref_all  dmean_all       dd   dd_ref  cut  eq_cut  w20cut  months
0  NC_K7_F55_45  JN05W2    L1M     538.8    606.3      -67.5  36370.5  36370.5  0.0    -0.3   -11.1       6
1  NC_K7_F55_45  JN05W2    L3M   15681.5  16015.2     -333.7  36370.5  36370.5  0.0    -0.3    -2.1       6
2  NC_K7_F55_45  JN05W2    L6M   25242.1  25136.9      105.2  36370.5  36370.5  0.0    -0.3    -0.7       6

```
### windows vs LPB_BASE (score_w)
```
NC_K7_F55_45
           cell window  mean_all  mean_ref_all  dmean_all     mean       dd   dd_ref   cut   dmean  eq_cut       w20   w20_ref  calmar  mean_ref  months
0  NC_K7_F55_45    L1M     538.8         340.7      198.1  -7189.9  36370.5  51252.7  29.0  8989.9    43.4    2155.2    1363.0   -10.3  -16179.8       6
1  NC_K7_F55_45    L3M   15681.5       11956.7     3724.8  15752.7  36370.5  77224.2  52.9   827.4    62.4  203859.1  155436.8    22.5   14925.3       6
2  NC_K7_F55_45    L6M   25242.1       18696.8     6545.3  23381.6  36370.5  77224.2  52.9  4721.2    62.4  261777.9  102383.9    33.4   18660.5       6

```
### acceptance_p7
```
6M P7 sessions of the reference) and the frozen live week: re-entry winners after NEW EVIDENCE
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +25963 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +14034 (5 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +21574 (5 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +17327 (5 trades, 1 such winners $+4790)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net -4895 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 4 ($+20390); all re-entry winners (any evidence) reference 13, set 14
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)

SUMMARY NC_K7_F55_45: fails 1 of 15 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->1', '0->0']
covered sessions 15 of 20
ACCEPT NC_K7_F55_45 PASS fails=1/20

```
### behavioural scorecard (ref JN05W2)
NC_K7_F55_45 L6M (stack, per week): full stops 12.2/wk $-22764; give-backs 7.6/wk (7.5 round-trips) realised $-10580, forgone vs target $28232; same-side losing runs max 13, p95 6, $-44591 lost on 3rd-and-later; no-new-evidence re-entries 32.4/wk $1291; recoveries cut 12.4/wk $48308, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $855/wk, losers avoided $713/wk, net +111 $/wk; pnl $26710/wk.
NC_K7_F55_45 HOLD: months missing (6 of 12), window not scored
NC_K7_F55_45 PRE: months missing (17 of 17), window not scored
NC_K7_F55_45 X': months missing (10 of 10), window not scored


## 2.NC_A7_T10_10F (6/43 months)
### windows vs JN05W2 (nf_score)
```
(not yet)
```
### windows vs LPB_BASE (score_w)
```
(not yet)
```
### acceptance_p7
```
(not yet)
```
### behavioural scorecard (ref JN05W2)
(not yet)

## 2.NC_M7_T10_10A (6/43 months)
### windows vs JN05W2 (nf_score)
```
(not yet)
```
### windows vs LPB_BASE (score_w)
```
(not yet)
```
### acceptance_p7
```
(not yet)
```
### behavioural scorecard (ref JN05W2)
(not yet)

## 3. First-order screens that chose the cells
anomalous trades excluded 10
## FO-4. Flat cut by context (K7, U7, A7, M7) - first-order on LPB_BASE trades, 1-s paths (slip 1.2; engine uses 0.80, so each fire is ~$8/lot better in exact)

Grid per book: flat level {35,40,45,50,55} separately for FRESH and RECHASE tags (36 combos), lots-group and session splits, time condition nft (still below -X after N min; X 10/20/30, N 5/10/15/20) for all / fresh / rechase. Cells per book: K7 125, U7 115, A7 105, M7 110 (family size). net $/wk, DD cut % on the stack.

### K7: bi-weekly WF re-pick (trailing 26 wk, max net, off if <=0): OOS total $-70202 over 161 weeks (positive weeks 53%); most picked: T:nft10_5m|all x11, G:flat50|L1 x8, T:nft20_10m|rechase x7

| cell | fires | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | PRE | X' | stops saved $/wk L6M | recoveries lost $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| G:flat50|S3 | 504 | 144 | 169 | -2 | -16 | -153 | 1.0 | -0.8 | 0.4 | -4.9 | 239 | 0 |
| T:nft30_5m|rechase | 150 | 72 | 78 | -86 | 59 | 219 | 1.2 | 2.2 | -0.8 | 0.0 | 399 | -400 |
| T:nft30_15m|rechase | 256 | 16 | 33 | -186 | 208 | 317 | 0.1 | 2.1 | 2.1 | 2.2 | 596 | -562 |
| F:fresh=flat55|rechase=off | 281 | 20 | 55 | -13 | 51 | -108 | 0.3 | 0.5 | 0.5 | 1.6 | 58 | 0 |
| G:flat55|S3 | 401 | 12 | 30 | 0 | 16 | -77 | -0.1 | -0.6 | -0.1 | 0.5 | 112 | 0 |
| G:flat45|S3 | 623 | 325 | 171 | -285 | -121 | -143 | 1.5 | -1.1 | 1.4 | -4.8 | 408 | 0 |

### U7: bi-weekly WF re-pick (trailing 26 wk, max net, off if <=0): OOS total $-69491 over 161 weeks (positive weeks 43%); most picked: T:nft10_5m|rechase x11, T:nft10_5m|all x9, G:flat50|S1 x7

| cell | fires | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | PRE | X' | stops saved $/wk L6M | recoveries lost $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| T:nft20_15m|all | 134 | 103 | 280 | 350 | 215 | 19 | -0.7 | -6.8 | 4.8 | 3.9 | 1357 | -1508 |
| T:nft10_20m|fresh | 110 | 644 | 736 | -172 | 282 | 297 | -1.6 | 0.4 | -2.4 | 2.4 | 1119 | -670 |
| T:nft20_15m|fresh | 57 | 481 | 529 | 160 | 60 | 0 | 1.4 | 0.3 | 3.4 | 0.9 | 782 | -397 |
| T:nft10_15m|fresh | 111 | 694 | 611 | -67 | 190 | 76 | -0.7 | 1.4 | 3.4 | 4.8 | 1242 | -651 |
| T:nft20_5m|all | 57 | 305 | 175 | 233 | 0 | 0 | 8.0 | -4.2 | 0.3 | 0.0 | 1098 | -1070 |
| T:nft10_10m|fresh | 92 | 524 | 445 | 72 | -67 | 106 | 0.5 | 1.3 | 0.9 | 2.0 | 1107 | -893 |

### A7: bi-weekly WF re-pick (trailing 26 wk, max net, off if <=0): OOS total $-8311 over 161 weeks (positive weeks 36%); most picked: T:nft30_15m|all x10, T:nft10_20m|all x8, F:fresh=flat50|rechase=flat35 x7

| cell | fires | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | PRE | X' | stops saved $/wk L6M | recoveries lost $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| T:nft20_10m|fresh | 10 | 86 | 55 | 23 | 0 | 0 | 0.0 | 0.0 | 0.7 | 0.0 | 77 | 0 |
| T:nft10_10m|fresh | 28 | 162 | 47 | 20 | 4 | -36 | 0.0 | 0.0 | 0.7 | 0.7 | 148 | 0 |
| T:nft20_5m|fresh | 7 | 102 | 49 | 18 | 0 | 0 | 0.0 | 0.0 | 0.9 | 0.0 | 102 | 0 |
| T:nft20_15m|fresh | 19 | 55 | 58 | 23 | 14 | -101 | 0.0 | 0.8 | 0.5 | 0.0 | 58 | 0 |
| T:nft30_10m|all | 38 | 75 | 68 | -18 | 0 | 28 | 0.1 | 0.7 | 0.6 | 0.0 | 207 | -164 |
| T:nft20_20m|fresh | 22 | 105 | 10 | 25 | 36 | -93 | 0.0 | 1.0 | 0.5 | 1.3 | 97 | 0 |

### M7: bi-weekly WF re-pick (trailing 26 wk, max net, off if <=0): OOS total $1509 over 161 weeks (positive weeks 45%); most picked: F:fresh=flat40|rechase=flat55 x12, T:nft10_15m|fresh x11, T:nft10_15m|all x8

| cell | fires | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | PRE | X' | stops saved $/wk L6M | recoveries lost $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| F:fresh=flat40|rechase=off | 195 | 80 | 32 | 138 | 76 | 68 | -0.5 | 0.0 | 0.0 | -1.5 | 85 | 0 |
| T:nft10_15m|fresh | 96 | 210 | 31 | 54 | 162 | -32 | 2.2 | -1.9 | -0.8 | 2.7 | 61 | -60 |
| F:fresh=flat45|rechase=off | 134 | 40 | 30 | 63 | 92 | 82 | -0.7 | 0.0 | -0.5 | 0.8 | 69 | 0 |
| F:fresh=flat40|rechase=flat55 | 516 | 43 | 4 | 81 | -72 | 129 | -0.3 | 0.2 | 0.5 | -1.7 | 169 | 0 |
| F:fresh=flat50|rechase=off | 100 | 16 | 7 | 36 | 28 | 53 | 0.0 | 0.0 | -0.1 | 0.0 | 37 | 0 |
| F:fresh=flat40|rechase=flat50 | 693 | 35 | 49 | 56 | 28 | -253 | -0.2 | 0.5 | 0.8 | 0.1 | 355 | -91 |

## FO-3. Hold-or-take by location only (K7, U7, A7, M7, P7, H7) - first-order, nz_kern conditions, take = market exit next 1-s mid - 1.2

Cells (223 per book): A stall (arm {.6,.7,.8,.9} x secs since high {10..160}), B reversal (arm x drawdown from high X pts {6..30} over last N s {30,60,120}), C ladder floor (m,f), plus A+B, A+C, B+C combos (<= 3 plain conditions). clip = Target fills taken early ($/wk lost).

### K7: bi-weekly WF re-pick OOS total $-70904 over 161 weeks (positive weeks 17%); most picked: off x39, B rev arm=0.8 X=30pt N=30s x18, B rev arm=0.9 X=15pt N=30s x3

| cell | fires | clipped fills | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | clip $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|
| (no cell positive on L6M, HOLD and 3.5-year total) |||||||||||

### U7: bi-weekly WF re-pick OOS total $-104664 over 161 weeks (positive weeks 26%); most picked: B rev arm=0.6 X=30pt N=120s x9, B rev arm=0.7 X=30pt N=30s x6, off x6

| cell | fires | clipped fills | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | clip $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|
| B rev arm=0.7 X=30pt N=120s | 140 | 65 | 899 | 604 | 115 | -67 | -1091 | 5.2 | -0.5 | 1567 |
| B rev arm=0.7 X=20pt N=60s | 216 | 126 | 539 | 498 | 71 | 88 | -1300 | 5.2 | -3.1 | 2554 |
| B rev arm=0.7 X=20pt N=120s | 290 | 184 | 1152 | 835 | -184 | -73 | -953 | 6.7 | -4.6 | 2794 |
| B rev arm=0.8 X=30pt N=120s | 89 | 45 | 267 | 282 | 149 | -168 | -993 | 0.0 | 2.3 | 1254 |

### A7: bi-weekly WF re-pick OOS total $-35993 over 161 weeks (positive weeks 14%); most picked: B rev arm=0.8 X=30pt N=60s x10, B rev arm=0.6 X=30pt N=30s x9, B rev arm=0.6 X=30pt N=120s x7

| cell | fires | clipped fills | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | clip $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|
| (no cell positive on L6M, HOLD and 3.5-year total) |||||||||||

### M7: bi-weekly WF re-pick OOS total $-56563 over 161 weeks (positive weeks 35%); most picked: off x7, C floor m=0.9 f=0.5 x6, B rev arm=0.7 X=15pt N=30s x5

| cell | fires | clipped fills | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | clip $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|
| C floor m=0.9 f=0.2 | 154 | 70 | 248 | 43 | -30 | 178 | 14 | 2.3 | 0.1 | 532 |
| C floor m=0.9 f=0.5 | 244 | 160 | 209 | 116 | -33 | 153 | -235 | 3.2 | 1.1 | 854 |
| C floor m=0.9 f=0.6 | 302 | 217 | 283 | 192 | -65 | 83 | -165 | 3.6 | 1.5 | 863 |
| B+C rev(0.9,20pt,120s)+floor(0.9,0.5) | 281 | 197 | 208 | 143 | -67 | 121 | -190 | 3.2 | 1.5 | 905 |
| C floor m=0.9 f=0.7 | 403 | 318 | 310 | 250 | -130 | 106 | -213 | 2.8 | 1.8 | 947 |

### P7: bi-weekly WF re-pick OOS total $-124351 over 161 weeks (positive weeks 35%); most picked: B rev arm=0.9 X=10pt N=60s x9, B rev arm=0.8 X=10pt N=60s x7, B rev arm=0.9 X=20pt N=30s x5

| cell | fires | clipped fills | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | clip $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|
| B rev arm=0.7 X=10pt N=60s | 1509 | 1123 | 2375 | 789 | 172 | 131 | -1662 | 3.6 | -4.1 | 15931 |
| B rev arm=0.9 X=30pt N=30s | 28 | 7 | 205 | 206 | 124 | 0 | 5 | 0.0 | 0.0 | 77 |
| B rev arm=0.9 X=30pt N=60s | 59 | 25 | 360 | 176 | 113 | -308 | 73 | 0.0 | -2.5 | 439 |

### H7: bi-weekly WF re-pick OOS total $-28382 over 161 weeks (positive weeks 21%); most picked: B rev arm=0.6 X=20pt N=120s x7, C floor m=0.9 f=0.5 x7, B rev arm=0.6 X=15pt N=60s x6

| cell | fires | clipped fills | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | clip $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|
| B+C rev(0.9,20pt,120s)+floor(0.8,0.2) | 134 | 73 | 214 | 183 | -139 | 534 | 6 | 0.0 | 4.4 | 617 |
| C floor m=0.8 f=0.7 | 312 | 250 | 218 | 83 | -194 | 677 | 145 | -4.6 | 5.1 | 1101 |
| B+C rev(0.9,10pt,60s)+floor(0.8,0.2) | 189 | 128 | 90 | 107 | -147 | 540 | 75 | -1.8 | 3.4 | 789 |
| B+C rev(0.8,30pt,30s)+floor(0.8,0.2) | 119 | 58 | 76 | 70 | -122 | 527 | 24 | 0.0 | 4.4 | 668 |
| C floor m=0.8 f=0.2 | 118 | 57 | 137 | 99 | -144 | 527 | 24 | 0.0 | 4.4 | 607 |

