# DS3_NEXT_FEATURES_F3 - T-NEXT-FEATURES items 3 (hold-or-take by location) and 4 (flat cut by context). W-F3. Shadow only, no PASS claim.
Updated 2026-11-14 18:17Z. Directive autopilot/DIRECTIVE_T_NEXT_FEATURES_20261112.md; prereg autopilot/NEXTF3_PREREG.md (sha in DECISIONS.md). BASE = JN05W2 (LPB panel + F3 + E1 + C22 + BR3S + FLAT45K, exact 43 months, W-J). Item-4 sets keep FLAT45K on K7 unless the cell says replace. Exact sets run one per job (jn05_run2.py, TP engine, tag NEXTF); months done: NC_U7_T10_15F 43/43, NC_U7_T20_15F 43/43, NC_U7_T20_15A 12/43, NC_K7_T20_20RC 43/43, NC_K7_F55_45 12/43, NC_A7_T10_10F 43/43, NC_M7_T10_10A 12/43, NC_K7_T30_10RC 12/43, NH_P7_A9_N20 12/43, NH_P7_B9_X10N30 12/43, NH_U7_B7_X20N60 12/43, NH_M7_C9_F2 43/43, NH_M7_B9_X10N60 43/43, NH_P7_B7_X10N60 12/43, NH_U7_B7_X30N120 43/43

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
| NC_K7_T30_10RC | 248061 | 3 | 1 | 13 |
| NH_P7_A9_N20 | 233975 | 0 | 0 | 11 |
| NH_P7_B9_X10N30 | 220114 | 0 | 0 | 12 |
| NH_U7_B7_X20N60 | 247664 | 1 | 0 | 14 |
| NH_M7_C9_F2 | 257263 | 1 | 0 | 13 |
| NH_M7_B9_X10N60 | 257215 | 1 | 0 | 14 |
| NH_P7_B7_X10N60 | 208417 | 2 | 1 | 12 |
| NH_U7_B7_X30N120 | 255545 | 2 | 0 | 10 |


## 2.NC_U7_T10_15F (43/43 months)
### windows vs JN05W2 (nf_score)
```
NC_U7_T10_15F
            cell     ref window  mean_all  ref_all  dmean_all       dd   dd_ref   cut  eq_cut  w20cut  wf2w_beat_pct  wf2w_cut  wf2w_mean  months
0  NC_U7_T10_15F  JN05W2    L1M    3190.3    606.3     2584.0  31571.5  36370.5  13.2    16.6   426.2           16.5       0.0       24.5      43
1  NC_U7_T10_15F  JN05W2    L3M   17258.8  16015.2     1243.6  32116.9  36370.5  11.7    15.2     7.8           16.5       0.0       24.5      43
2  NC_U7_T10_15F  JN05W2    L6M   25709.5  25136.9      572.6  32116.9  36370.5  11.7    15.2     7.7           16.5       0.0       24.5      43
3  NC_U7_T10_15F  JN05W2   HOLD   18288.4  17489.3      799.1  61073.1  63185.1   3.3     7.1     8.6           16.5       0.0       24.5      43
4  NC_U7_T10_15F  JN05W2    PRE   10077.8  10167.9      -90.0  76960.6  76186.1  -1.0     2.9    -0.0           16.5       0.0       24.5      43
5  NC_U7_T10_15F  JN05W2     X'    3834.3   3585.1      249.2  45375.7  55325.6  18.0    21.2     1.6           16.5       0.0       24.5      43

```
### windows vs LPB_BASE (score_w)
```
NC_U7_T10_15F
            cell window  mean_all  mean_ref_all  dmean_all     mean       dd    dd_ref   cut    dmean  eq_cut       w20   w20_ref  calmar  mean_ref  wf2w_beat_pct  wf2w_cut  wf2w_mean  months
0  NC_U7_T10_15F    L1M    3190.3         340.7     2849.5  -5737.3  31571.5   51252.7  38.4  10442.5    51.8   12761.0    1363.0    -9.4  -16179.8           44.3      -5.1      -61.5      43
1  NC_U7_T10_15F    L3M   17258.8       11956.7     5302.1  17430.8  32116.9   77224.2  58.4   2505.5    67.5  224363.9  155436.8    28.2   14925.3           44.3      -5.1      -61.5      43
2  NC_U7_T10_15F    L6M   25709.5       18696.8     7012.7  23852.2  32116.9   77224.2  58.4   5191.8    67.5  283907.1  102383.9    38.6   18660.5           44.3      -5.1      -61.5      43
3  NC_U7_T10_15F   HOLD   18288.4       15236.3     3052.0  17232.5  61073.1   78842.0  22.5   2081.8    39.4 -239322.9 -377467.2    14.7   15150.7           44.3      -5.1      -61.5      43
4  NC_U7_T10_15F    PRE   10077.8       11685.4    -1607.6  10270.2  76960.6   99479.4  22.6  -2322.2    39.5 -440816.3 -529227.7     6.9   12592.4           44.3      -5.1      -61.5      43
5  NC_U7_T10_15F     X'    3834.3        1333.6     2500.7   4427.3  45375.7  122552.7  63.0   1874.6    71.0 -217141.7 -321242.1     5.1    2552.6           44.3      -5.1      -61.5      43

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

SUMMARY NC_U7_T10_15F: fails 1 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->1', '0->0']
covered sessions 20 of 20
ACCEPT NC_U7_T10_15F PASS fails=1/20

```
### behavioural scorecard (ref JN05W2)
NC_U7_T10_15F L6M (stack, per week): full stops 10.6/wk $-19315; give-backs 7.6/wk (7.4 round-trips) realised $-10489, forgone vs target $28044; same-side losing runs max 13, p95 6, $-44516 lost on 3rd-and-later; no-new-evidence re-entries 32.9/wk $1001; recoveries cut 12.2/wk $47901, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $0/wk, losers avoided $127/wk, net +606 $/wk; pnl $27204/wk.
NC_U7_T10_15F HOLD (stack, per week): full stops 10.2/wk $-19356; give-backs 6.8/wk (6.7 round-trips) realised $-9378, forgone vs target $25472; same-side losing runs max 13, p95 6, $-37234 lost on 3rd-and-later; no-new-evidence re-entries 26.2/wk $1800; recoveries cut 11.1/wk $43961, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $24/wk, losers avoided $162/wk, net +822 $/wk; pnl $18863/wk.
NC_U7_T10_15F PRE (stack, per week): full stops 9.0/wk $-19125; give-backs 4.8/wk (4.4 round-trips) realised $-6545, forgone vs target $17459; same-side losing runs max 9, p95 4, $-21068 lost on 3rd-and-later; no-new-evidence re-entries 12.9/wk $1012; recoveries cut 6.7/wk $24619, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $65/wk, losers avoided $34/wk, net -92 $/wk; pnl $10254/wk.
NC_U7_T10_15F X' (stack, per week): full stops 11.0/wk $-22275; give-backs 3.5/wk (3.1 round-trips) realised $-4614, forgone vs target $12263; same-side losing runs max 8, p95 4, $-12107 lost on 3rd-and-later; no-new-evidence re-entries 3.6/wk $505; recoveries cut 2.5/wk $8955, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $0/wk, losers avoided $113/wk, net +251 $/wk; pnl $3859/wk.


## 2.NC_U7_T20_15F (43/43 months)
### windows vs JN05W2 (nf_score)
```
NC_U7_T20_15F
            cell     ref window  mean_all  ref_all  dmean_all       dd   dd_ref  cut  eq_cut  w20cut  wf2w_beat_pct  wf2w_cut  wf2w_mean  months
0  NC_U7_T20_15F  JN05W2    L1M    2318.8    606.3     1712.5  35057.5  36370.5  3.6     7.1   282.4           15.2       0.0       87.7      43
1  NC_U7_T20_15F  JN05W2    L3M   16946.4  16015.2      931.2  35057.5  36370.5  3.6     7.1     5.8           15.2       0.0       87.7      43
2  NC_U7_T20_15F  JN05W2    L6M   25646.4  25136.9      509.5  35057.5  36370.5  3.6     7.1     7.2           15.2       0.0       87.7      43
3  NC_U7_T20_15F  JN05W2   HOLD   18130.0  17489.3      640.7  62676.1  63185.1  0.8     4.4     5.5           15.2       0.0       87.7      43
4  NC_U7_T20_15F  JN05W2    PRE   10345.8  10167.9      177.9  76183.6  76186.1  0.0     3.7     0.0           15.2       0.0       87.7      43
5  NC_U7_T20_15F  JN05W2     X'    3615.7   3585.1       30.6  52653.8  55325.6  4.8     8.3     0.0           15.2       0.0       87.7      43

```
### windows vs LPB_BASE (score_w)
```
NC_U7_T20_15F
            cell window  mean_all  mean_ref_all  dmean_all     mean       dd    dd_ref   cut   dmean  eq_cut       w20   w20_ref  calmar  mean_ref  wf2w_beat_pct  wf2w_cut  wf2w_mean  months
0  NC_U7_T20_15F    L1M    2318.8         340.7     1978.0  -6899.3  35057.5   51252.7  31.6  9280.5    46.3    9275.0    1363.0   -10.2  -16179.8           44.3      -5.1      -30.6      43
1  NC_U7_T20_15F    L3M   16946.4       11956.7     4989.7  17092.4  35057.5   77224.2  54.6  2167.1    64.4  220303.4  155436.8    25.4   14925.3           44.3      -5.1      -30.6      43
2  NC_U7_T20_15F    L6M   25646.4       18696.8     6949.6  23786.6  35057.5   77224.2  54.6  5126.1    64.4  282588.0  102383.9    35.3   18660.5           44.3      -5.1      -30.6      43
3  NC_U7_T20_15F   HOLD   18130.0       15236.3     2893.6  17071.0  62676.1   78842.0  20.5  1920.3    37.6 -247261.2 -377467.2    14.2   15150.7           44.3      -5.1      -30.6      43
4  NC_U7_T20_15F    PRE   10345.8       11685.4    -1339.6  10541.8  76183.6   99479.4  23.4 -2050.6    39.9 -440471.8 -529227.7     7.2   12592.4           44.3      -5.1      -30.6      43
5  NC_U7_T20_15F     X'    3615.7        1333.6     2282.1   4203.6  52653.8  122552.7  57.0  1650.9    66.3 -220738.5 -321242.1     4.2    2552.6           44.3      -5.1      -30.6      43

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

SUMMARY NC_U7_T20_15F: fails 1 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->1', '0->0']
covered sessions 20 of 20
ACCEPT NC_U7_T20_15F PASS fails=1/20

```
### behavioural scorecard (ref JN05W2)
NC_U7_T20_15F L6M (stack, per week): full stops 10.7/wk $-19717; give-backs 7.6/wk (7.4 round-trips) realised $-10489, forgone vs target $28044; same-side losing runs max 13, p95 6, $-44604 lost on 3rd-and-later; no-new-evidence re-entries 32.9/wk $1001; recoveries cut 12.2/wk $47901, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $0/wk, losers avoided $127/wk, net +539 $/wk; pnl $27137/wk.
NC_U7_T20_15F HOLD (stack, per week): full stops 10.4/wk $-19857; give-backs 6.8/wk (6.7 round-trips) realised $-9378, forgone vs target $25472; same-side losing runs max 13, p95 6, $-37419 lost on 3rd-and-later; no-new-evidence re-entries 26.2/wk $1805; recoveries cut 11.1/wk $44031, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $24/wk, losers avoided $162/wk, net +659 $/wk; pnl $18700/wk.
NC_U7_T20_15F PRE (stack, per week): full stops 9.0/wk $-19371; give-backs 4.9/wk (4.5 round-trips) realised $-6627, forgone vs target $17655; same-side losing runs max 9, p95 4, $-21121 lost on 3rd-and-later; no-new-evidence re-entries 12.9/wk $986; recoveries cut 6.7/wk $24619, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $16/wk, losers avoided $34/wk, net +181 $/wk; pnl $10526/wk.
NC_U7_T20_15F X' (stack, per week): full stops 11.0/wk $-22576; give-backs 3.6/wk (3.1 round-trips) realised $-4638, forgone vs target $12342; same-side losing runs max 8, p95 4, $-12101 lost on 3rd-and-later; no-new-evidence re-entries 3.6/wk $392; recoveries cut 2.5/wk $8955, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $0/wk, losers avoided $-0/wk, net +31 $/wk; pnl $3639/wk.


## 2.NC_U7_T20_15A (12/43 months)
### windows vs JN05W2 (nf_score)
```
NC_U7_T20_15A
            cell     ref window  mean_all  ref_all  dmean_all       dd   dd_ref   cut  eq_cut  w20cut  months
0  NC_U7_T20_15A  JN05W2    L1M    3013.1    606.3     2406.8  32421.5  36370.5  10.9    12.0   397.0      12
1  NC_U7_T20_15A  JN05W2    L3M   16931.1  16015.2      915.9  33509.9  36370.5   7.9     9.1     5.7      12
2  NC_U7_T20_15A  JN05W2    L6M   25109.7  25136.9      -27.2  33509.9  36370.5   7.9     9.1     1.9      12
3  NC_U7_T20_15A  JN05W2   HOLD   17558.7  17489.3       69.4  68240.6  63185.1  -8.0    -6.6    -0.4      12

```
### windows vs LPB_BASE (score_w)
```
NC_U7_T20_15A
            cell window  mean_all  mean_ref_all  dmean_all     mean       dd   dd_ref   cut    dmean  eq_cut       w20   w20_ref  calmar  mean_ref  months
0  NC_U7_T20_15A    L1M    3013.1         340.7     2672.4  -5973.5  32421.5  51252.7  36.7  10206.4    49.2   12052.5    1363.0    -9.6  -16179.8      12
1  NC_U7_T20_15A    L3M   16931.1       11956.7     4974.4  17075.8  33509.9  77224.2  56.6   2150.5    65.1  220104.4  155436.8    26.5   14925.3      12
2  NC_U7_T20_15A    L6M   25109.7       18696.8     6412.9  23228.5  33509.9  77224.2  56.6   4568.0    65.1  268500.5  102383.9    36.0   18660.5      12
3  NC_U7_T20_15A   HOLD   17558.7       15236.3     2322.4  16488.5  68240.6  78842.0  13.4   1337.8    30.5 -262839.3 -377467.2    12.6   15150.7      12

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

SUMMARY NC_U7_T20_15A: fails 1 of 16 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->1', '0->0']
covered sessions 16 of 20
ACCEPT NC_U7_T20_15A PASS fails=1/20

```
### behavioural scorecard (ref JN05W2)
NC_U7_T20_15A L6M (stack, per week): full stops 10.3/wk $-18613; give-backs 7.5/wk (7.4 round-trips) realised $-10470, forgone vs target $27976; same-side losing runs max 13, p95 6, $-44331 lost on 3rd-and-later; no-new-evidence re-entries 32.8/wk $805; recoveries cut 12.0/wk $47526, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $390/wk, losers avoided $582/wk, net -29 $/wk; pnl $26570/wk.
NC_U7_T20_15A HOLD (stack, per week): full stops 10.0/wk $-18572; give-backs 6.8/wk (6.7 round-trips) realised $-9331, forgone vs target $25378; same-side losing runs max 13, p95 6, $-37424 lost on 3rd-and-later; no-new-evidence re-entries 26.2/wk $1720; recoveries cut 11.0/wk $43849, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $284/wk, losers avoided $480/wk, net +71 $/wk; pnl $18113/wk.
NC_U7_T20_15A PRE: months missing (17 of 17), window not scored
NC_U7_T20_15A X': months missing (10 of 10), window not scored


## 2.NC_K7_T20_20RC (43/43 months)
### windows vs JN05W2 (nf_score)
```
NC_K7_T20_20RC
             cell     ref window  mean_all  ref_all  dmean_all       dd   dd_ref   cut  eq_cut  w20cut  wf2w_beat_pct  wf2w_cut  wf2w_mean  months
0  NC_K7_T20_20RC  JN05W2    L1M    2231.2    606.3     1624.9  27605.1  36370.5  24.1    22.9   268.0           30.4       2.6     -187.8      43
1  NC_K7_T20_20RC  JN05W2    L3M   17447.2  16015.2     1432.0  27605.1  36370.5  24.1    22.9     8.9           30.4       2.6     -187.8      43
2  NC_K7_T20_20RC  JN05W2    L6M   25076.1  25136.9      -60.8  27605.1  36370.5  24.1    22.9     2.3           30.4       2.6     -187.8      43
3  NC_K7_T20_20RC  JN05W2   HOLD   17797.0  17489.3      307.7  62730.7  63185.1   0.7    -0.8     7.4           30.4       2.6     -187.8      43
4  NC_K7_T20_20RC  JN05W2    PRE    9935.6  10167.9     -232.3  72420.5  76186.1   4.9     3.5    -1.2           30.4       2.6     -187.8      43
5  NC_K7_T20_20RC  JN05W2     X'    3373.4   3585.1     -211.7  55049.3  55325.6   0.5    -1.0    -3.2           30.4       2.6     -187.8      43

```
### windows vs LPB_BASE (score_w)
```
NC_K7_T20_20RC
             cell window  mean_all  mean_ref_all  dmean_all     mean       dd    dd_ref   cut    dmean  eq_cut       w20   w20_ref  calmar  mean_ref  wf2w_beat_pct  wf2w_cut  wf2w_mean  months
0  NC_K7_T20_20RC    L1M    2231.2         340.7     1890.4  -4730.3  27605.1   51252.7  46.1  11449.6    56.8    8924.7    1363.0    -8.9  -16179.8           44.3      -5.3     -425.7      43
1  NC_K7_T20_20RC    L3M   17447.2       11956.7     5490.6  17671.5  27605.1   77224.2  64.3   2746.2    71.3  226814.0  155436.8    33.3   14925.3           44.3      -5.3     -425.7      43
2  NC_K7_T20_20RC    L6M   25076.1       18696.8     6379.3  23272.6  27605.1   77224.2  64.3   4612.1    71.3  269730.6  102383.9    43.8   18660.5           44.3      -5.3     -425.7      43
3  NC_K7_T20_20RC   HOLD   17797.0       15236.3     2560.7  16770.2  62730.7   78842.0  20.4   1619.5    36.2 -242283.7 -377467.2    13.9   15150.7           44.3      -5.3     -425.7      43
4  NC_K7_T20_20RC    PRE    9935.6       11685.4    -1749.8  10186.0  72420.5   99479.4  27.2  -2406.4    41.6 -445817.7 -529227.7     7.3   12592.4           44.3      -5.3     -425.7      43
5  NC_K7_T20_20RC     X'    3373.4        1333.6     2039.8   4024.8  55049.3  122552.7  55.1   1472.1    64.0 -227881.7 -321242.1     3.8    2552.6           44.3      -5.3     -425.7      43

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

SUMMARY NC_K7_T20_20RC: fails 1 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->1', '0->0']
covered sessions 20 of 20
ACCEPT NC_K7_T20_20RC PASS fails=1/20

```
### behavioural scorecard (ref JN05W2)
NC_K7_T20_20RC L6M (stack, per week): full stops 11.2/wk $-21326; give-backs 7.6/wk (7.4 round-trips) realised $-10539, forgone vs target $28093; same-side losing runs max 13, p95 6, $-45039 lost on 3rd-and-later; no-new-evidence re-entries 33.6/wk $1214; recoveries cut 12.0/wk $47425, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $1317/wk, losers avoided $1831/wk, net -64 $/wk; pnl $26534/wk.
NC_K7_T20_20RC HOLD (stack, per week): full stops 10.7/wk $-21074; give-backs 6.8/wk (6.6 round-trips) realised $-9373, forgone vs target $25443; same-side losing runs max 13, p95 6, $-37866 lost on 3rd-and-later; no-new-evidence re-entries 27.0/wk $1994; recoveries cut 10.9/wk $43563, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $1280/wk, losers avoided $1457/wk, net +216 $/wk; pnl $18257/wk.
NC_K7_T20_20RC PRE (stack, per week): full stops 9.2/wk $-20052; give-backs 4.8/wk (4.4 round-trips) realised $-6623, forgone vs target $17611; same-side losing runs max 9, p95 4, $-21530 lost on 3rd-and-later; no-new-evidence re-entries 13.3/wk $646; recoveries cut 6.7/wk $24655, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $917/wk, losers avoided $732/wk, net -236 $/wk; pnl $10109/wk.
NC_K7_T20_20RC X' (stack, per week): full stops 11.0/wk $-22631; give-backs 3.5/wk (3.0 round-trips) realised $-4585, forgone vs target $12261; same-side losing runs max 8, p95 4, $-12143 lost on 3rd-and-later; no-new-evidence re-entries 3.9/wk $287; recoveries cut 2.5/wk $8955, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $147/wk, losers avoided $398/wk, net -213 $/wk; pnl $3395/wk.


## 2.NC_K7_F55_45 (12/43 months)
### windows vs JN05W2 (nf_score)
```
NC_K7_F55_45
           cell     ref window  mean_all  ref_all  dmean_all       dd   dd_ref  cut  eq_cut  w20cut  months
0  NC_K7_F55_45  JN05W2    L1M     538.8    606.3      -67.5  36370.5  36370.5  0.0    -0.3   -11.1      12
1  NC_K7_F55_45  JN05W2    L3M   15681.5  16015.2     -333.7  36370.5  36370.5  0.0    -0.3    -2.1      12
2  NC_K7_F55_45  JN05W2    L6M   25242.1  25136.9      105.2  36370.5  36370.5  0.0    -0.3    -0.7      12
3  NC_K7_F55_45  JN05W2   HOLD   17467.3  17489.3      -22.0  67041.6  63185.1 -6.1    -6.4    -1.4      12

```
### windows vs LPB_BASE (score_w)
```
NC_K7_F55_45
           cell window  mean_all  mean_ref_all  dmean_all     mean       dd   dd_ref   cut   dmean  eq_cut       w20   w20_ref  calmar  mean_ref  months
0  NC_K7_F55_45    L1M     538.8         340.7      198.1  -7189.9  36370.5  51252.7  29.0  8989.9    43.4    2155.2    1363.0   -10.3  -16179.8      12
1  NC_K7_F55_45    L3M   15681.5       11956.7     3724.8  15752.7  36370.5  77224.2  52.9   827.4    62.4  203859.1  155436.8    22.5   14925.3      12
2  NC_K7_F55_45    L6M   25242.1       18696.8     6545.3  23381.6  36370.5  77224.2  52.9  4721.2    62.4  261777.9  102383.9    33.4   18660.5      12
3  NC_K7_F55_45   HOLD   17467.3       15236.3     2231.0  16402.9  67041.6  78842.0  15.0  1252.2    32.1 -265312.2 -377467.2    12.7   15150.7      12

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

SUMMARY NC_K7_F55_45: fails 1 of 16 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->1', '0->0']
covered sessions 16 of 20
ACCEPT NC_K7_F55_45 PASS fails=1/20

```
### behavioural scorecard (ref JN05W2)
NC_K7_F55_45 L6M (stack, per week): full stops 12.2/wk $-22764; give-backs 7.6/wk (7.5 round-trips) realised $-10580, forgone vs target $28232; same-side losing runs max 13, p95 6, $-44591 lost on 3rd-and-later; no-new-evidence re-entries 32.4/wk $1291; recoveries cut 12.4/wk $48308, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $855/wk, losers avoided $713/wk, net +111 $/wk; pnl $26710/wk.
NC_K7_F55_45 HOLD (stack, per week): full stops 12.1/wk $-22875; give-backs 6.9/wk (6.7 round-trips) realised $-9441, forgone vs target $25642; same-side losing runs max 13, p95 6, $-37573 lost on 3rd-and-later; no-new-evidence re-entries 26.0/wk $1699; recoveries cut 11.2/wk $44407, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $734/wk, losers avoided $983/wk, net -92 $/wk; pnl $17950/wk.
NC_K7_F55_45 PRE: months missing (17 of 17), window not scored
NC_K7_F55_45 X': months missing (10 of 10), window not scored


## 2.NC_A7_T10_10F (43/43 months)
### windows vs JN05W2 (nf_score)
```
NC_A7_T10_10F
            cell     ref window  mean_all  ref_all  dmean_all       dd   dd_ref  cut  eq_cut  w20cut  wf2w_beat_pct  wf2w_cut  wf2w_mean  months
0  NC_A7_T10_10F  JN05W2    L1M     191.3    606.3     -415.0  36370.5  36370.5  0.0     0.5   -68.5            1.3       1.1      -11.0      43
1  NC_A7_T10_10F  JN05W2    L3M   16234.3  16015.2      219.1  36370.5  36370.5  0.0     0.5     1.4            1.3       1.1      -11.0      43
2  NC_A7_T10_10F  JN05W2    L6M   25442.6  25136.9      305.7  36370.5  36370.5  0.0     0.5     0.8            1.3       1.1      -11.0      43
3  NC_A7_T10_10F  JN05W2   HOLD   17383.6  17489.3     -105.8  63185.1  63185.1  0.0     0.5     0.3            1.3       1.1      -11.0      43
4  NC_A7_T10_10F  JN05W2    PRE   10116.7  10167.9      -51.2  74737.6  76186.1  1.9     2.4    -2.0            1.3       1.1      -11.0      43
5  NC_A7_T10_10F  JN05W2     X'    3612.6   3585.1       27.5  55325.6  55325.6  0.0     0.5     0.2            1.3       1.1      -11.0      43

```
### windows vs LPB_BASE (score_w)
```
NC_A7_T10_10F
            cell window  mean_all  mean_ref_all  dmean_all     mean       dd    dd_ref   cut   dmean  eq_cut       w20   w20_ref  calmar  mean_ref  wf2w_beat_pct  wf2w_cut  wf2w_mean  months
0  NC_A7_T10_10F    L1M     191.3         340.7     -149.5  -7743.2  36370.5   51252.7  29.0  8436.6    43.8     765.1    1363.0   -11.1  -16179.8           44.3      -5.4     -251.2      43
1  NC_A7_T10_10F    L3M   16234.3       11956.7     4277.6  16357.4  36370.5   77224.2  52.9  1432.1    62.7  211045.7  155436.8    23.4   14925.3           44.3      -5.4     -251.2      43
2  NC_A7_T10_10F    L6M   25442.6       18696.8     6745.7  23554.8  36370.5   77224.2  52.9  4894.3    62.7  265652.0  102383.9    33.7   18660.5           44.3      -5.4     -251.2      43
3  NC_A7_T10_10F   HOLD   17383.6       15236.3     2147.2  16300.1  63185.1   78842.0  19.9  1149.5    36.5 -260993.3 -377467.2    13.4   15150.7           44.3      -5.4     -251.2      43
4  NC_A7_T10_10F    PRE   10116.7       11685.4    -1568.7  10371.4  74737.6   99479.4  24.9 -2221.0    40.5 -449594.1 -529227.7     7.2   12592.4           44.3      -5.4     -251.2      43
5  NC_A7_T10_10F     X'    3612.6        1333.6     2279.0   4200.4  55325.6  122552.7  54.9  1647.7    64.2 -220395.5 -321242.1     3.9    2552.6           44.3      -5.4     -251.2      43

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

SUMMARY NC_A7_T10_10F: fails 1 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->1', '0->0']
covered sessions 20 of 20
ACCEPT NC_A7_T10_10F PASS fails=1/20

```
### behavioural scorecard (ref JN05W2)
NC_A7_T10_10F L6M (stack, per week): full stops 10.9/wk $-21035; give-backs 7.6/wk (7.4 round-trips) realised $-10547, forgone vs target $28150; same-side losing runs max 13, p95 6, $-44798 lost on 3rd-and-later; no-new-evidence re-entries 32.8/wk $1150; recoveries cut 12.2/wk $47913, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $98/wk, losers avoided $101/wk, net +323 $/wk; pnl $26922/wk.
NC_A7_T10_10F HOLD (stack, per week): full stops 10.6/wk $-21005; give-backs 6.9/wk (6.7 round-trips) realised $-9423, forgone vs target $25564; same-side losing runs max 13, p95 6, $-37690 lost on 3rd-and-later; no-new-evidence re-entries 26.2/wk $1757; recoveries cut 11.1/wk $44069, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $427/wk, losers avoided $188/wk, net -109 $/wk; pnl $17933/wk.
NC_A7_T10_10F PRE (stack, per week): full stops 9.2/wk $-19986; give-backs 4.8/wk (4.5 round-trips) realised $-6621, forgone vs target $17626; same-side losing runs max 9, p95 4, $-21190 lost on 3rd-and-later; no-new-evidence re-entries 12.9/wk $942; recoveries cut 6.8/wk $24679, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $33/wk, losers avoided $18/wk, net -52 $/wk; pnl $10293/wk.
NC_A7_T10_10F X' (stack, per week): full stops 11.0/wk $-22551; give-backs 3.6/wk (3.1 round-trips) realised $-4618, forgone vs target $12321; same-side losing runs max 8, p95 4, $-12079 lost on 3rd-and-later; no-new-evidence re-entries 3.7/wk $365; recoveries cut 2.5/wk $8955, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $0/wk, losers avoided $22/wk, net +28 $/wk; pnl $3636/wk.


## 2.NC_M7_T10_10A (12/43 months)
### windows vs JN05W2 (nf_score)
```
NC_M7_T10_10A
            cell     ref window  mean_all  ref_all  dmean_all       dd   dd_ref  cut  eq_cut  w20cut  months
0  NC_M7_T10_10A  JN05W2    L1M     124.1    606.3     -482.2  37766.2  36370.5 -3.8    -6.1   -79.5      12
1  NC_M7_T10_10A  JN05W2    L3M   15016.8  16015.2     -998.4  37766.2  36370.5 -3.8    -6.1    -6.2      12
2  NC_M7_T10_10A  JN05W2    L6M   24394.8  25136.9     -742.1  37766.2  36370.5 -3.8    -6.1    -9.1      12
3  NC_M7_T10_10A  JN05W2   HOLD   17405.2  17489.3      -84.1  61677.6  63185.1  2.4     0.3     1.1      12

```
### windows vs LPB_BASE (score_w)
```
NC_M7_T10_10A
            cell window  mean_all  mean_ref_all  dmean_all     mean       dd   dd_ref   cut   dmean  eq_cut       w20   w20_ref  calmar  mean_ref  months
0  NC_M7_T10_10A    L1M     124.1         340.7     -216.7  -8756.0  37766.2  51252.7  26.3  7423.8    38.7     496.2    1363.0   -12.1  -16179.8      12
1  NC_M7_T10_10A    L3M   15016.8       11956.7     3060.1  15123.0  37766.2  77224.2  51.1   197.6    59.3  195218.7  155436.8    20.8   14925.3      12
2  NC_M7_T10_10A    L6M   24394.8       18696.8     5698.0  22425.0  37766.2  77224.2  51.1  3764.5    59.3  239597.3  102383.9    30.9   18660.5      12
3  NC_M7_T10_10A   HOLD   17405.2       15236.3     2168.8  16302.5  61677.6  78842.0  21.8  1151.8    34.9 -258716.8 -377467.2    13.7   15150.7      12

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

SUMMARY NC_M7_T10_10A: fails 1 of 16 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->1', '0->0']
covered sessions 16 of 20
ACCEPT NC_M7_T10_10A PASS fails=1/20

```
### behavioural scorecard (ref JN05W2)
NC_M7_T10_10A L6M (stack, per week): full stops 11.0/wk $-21124; give-backs 7.4/wk (7.3 round-trips) realised $-10463, forgone vs target $27920; same-side losing runs max 13, p95 6, $-46052 lost on 3rd-and-later; no-new-evidence re-entries 34.0/wk $588; recoveries cut 11.6/wk $46016, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $732/wk, losers avoided $420/wk, net -785 $/wk; pnl $25813/wk.
NC_M7_T10_10A HOLD (stack, per week): full stops 10.5/wk $-20850; give-backs 6.7/wk (6.5 round-trips) realised $-9273, forgone vs target $25201; same-side losing runs max 13, p95 6, $-38447 lost on 3rd-and-later; no-new-evidence re-entries 27.4/wk $1633; recoveries cut 10.3/wk $42200, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $522/wk, losers avoided $698/wk, net -50 $/wk; pnl $17992/wk.
NC_M7_T10_10A PRE: months missing (17 of 17), window not scored
NC_M7_T10_10A X': months missing (10 of 10), window not scored


## 2.NC_K7_T30_10RC (12/43 months)
### windows vs JN05W2 (nf_score)
```
NC_K7_T30_10RC
             cell     ref window  mean_all  ref_all  dmean_all       dd   dd_ref  cut  eq_cut  w20cut  months
0  NC_K7_T30_10RC  JN05W2    L1M     630.8    606.3       24.5  36265.5  36370.5  0.3    -0.8     4.0      12
1  NC_K7_T30_10RC  JN05W2    L3M   16250.5  16015.2      235.3  36265.5  36370.5  0.3    -0.8     1.5      12
2  NC_K7_T30_10RC  JN05W2    L6M   23973.2  25136.9    -1163.7  36265.5  36370.5  0.3    -0.8    -9.7      12
3  NC_K7_T30_10RC  JN05W2   HOLD   17054.8  17489.3     -434.6  61325.1  63185.1  2.9     1.9    -6.5      12

```
### windows vs LPB_BASE (score_w)
```
NC_K7_T30_10RC
             cell window  mean_all  mean_ref_all  dmean_all     mean       dd   dd_ref   cut   dmean  eq_cut       w20   w20_ref  calmar  mean_ref  months
0  NC_K7_T30_10RC    L1M     630.8         340.7      290.0  -7157.3  36265.5  51252.7  29.2  9022.5    40.2    2523.0    1363.0   -10.3  -16179.8      12
1  NC_K7_T30_10RC    L3M   16250.5       11956.7     4293.8  16375.0  36265.5  77224.2  53.0  1449.7    60.3  211256.7  155436.8    23.5   14925.3      12
2  NC_K7_T30_10RC    L6M   23973.2       18696.8     5276.4  22076.2  36265.5  77224.2  53.0  3415.7    60.3  237956.3  102383.9    31.7   18660.5      12
3  NC_K7_T30_10RC   HOLD   17054.8       15236.3     1818.4  15989.2  61325.1  78842.0  22.2   838.5    34.3 -278633.2 -377467.2    13.6   15150.7      12

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

SUMMARY NC_K7_T30_10RC: fails 1 of 16 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->1', '0->0']
covered sessions 16 of 20
ACCEPT NC_K7_T30_10RC PASS fails=1/20

```
### behavioural scorecard (ref JN05W2)
NC_K7_T30_10RC L6M (stack, per week): full stops 11.2/wk $-21420; give-backs 7.5/wk (7.4 round-trips) realised $-10478, forgone vs target $27983; same-side losing runs max 13, p95 6, $-44688 lost on 3rd-and-later; no-new-evidence re-entries 32.6/wk $966; recoveries cut 12.0/wk $47275, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $2327/wk, losers avoided $733/wk, net -1231 $/wk; pnl $25367/wk.
NC_K7_T30_10RC HOLD (stack, per week): full stops 10.8/wk $-21168; give-backs 6.9/wk (6.7 round-trips) realised $-9369, forgone vs target $25522; same-side losing runs max 13, p95 6, $-37543 lost on 3rd-and-later; no-new-evidence re-entries 26.1/wk $1733; recoveries cut 10.9/wk $43578, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $1273/wk, losers avoided $574/wk, net -447 $/wk; pnl $17595/wk.
NC_K7_T30_10RC PRE: months missing (17 of 17), window not scored
NC_K7_T30_10RC X': months missing (10 of 10), window not scored


## 2.NH_P7_A9_N20 (12/43 months)
### windows vs JN05W2 (nf_score)
```
NH_P7_A9_N20
           cell     ref window  mean_all  ref_all  dmean_all       dd   dd_ref   cut  eq_cut  w20cut  months
0  NH_P7_A9_N20  JN05W2    L1M    1497.7    606.3      891.4  38972.5  36370.5  -7.2   -11.1   147.0      12
1  NH_P7_A9_N20  JN05W2    L3M   15811.7  16015.2     -203.5  45439.7  36370.5 -24.9   -29.6    -1.3      12
2  NH_P7_A9_N20  JN05W2    L6M   24863.8  25136.9     -273.1  45439.7  36370.5 -24.9   -29.6     8.6      12
3  NH_P7_A9_N20  JN05W2   HOLD   16618.3  17489.3     -871.0  85568.0  63185.1 -35.4   -40.5   -22.7      12

```
### windows vs LPB_BASE (score_w)
```
NH_P7_A9_N20
           cell window  mean_all  mean_ref_all  dmean_all     mean       dd   dd_ref   cut    dmean  eq_cut       w20   w20_ref  calmar  mean_ref  months
0  NH_P7_A9_N20    L1M    1497.7         340.7     1157.0  -6046.5  38972.5  51252.7  24.0  10133.3    37.3    5990.9    1363.0    -8.1  -16179.8      12
1  NH_P7_A9_N20    L3M   15811.7       11956.7     3855.0  14759.3  45439.7  77224.2  41.2   -166.0    51.5  205551.9  155436.8    16.9   14925.3      12
2  NH_P7_A9_N20    L6M   24863.8       18696.8     6166.9  24720.7  45439.7  77224.2  41.2   4329.3    51.5  286329.2  102383.9    28.3   20391.4      12
3  NH_P7_A9_N20   HOLD   16618.3       15236.3     1382.0  16386.5  85568.0  78842.0  -8.5    387.4    10.5 -321013.0 -377467.2    10.0   15999.2      12

```
### acceptance_p7
```
6M P7 sessions of the reference) and the frozen live week: re-entry winners after NEW EVIDENCE
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +24852 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +11560 (5 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +20721 (6 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +14734 (5 trades, 1 such winners $+4790)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net -8341 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 3 ($+14354); all re-entry winners (any evidence) reference 13, set 13
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)

SUMMARY NH_P7_A9_N20: fails 1 of 16 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->1', '0->0']
covered sessions 16 of 20
ACCEPT NH_P7_A9_N20 PASS fails=1/20

```
### behavioural scorecard (ref JN05W2)
NH_P7_A9_N20 L6M (stack, per week): full stops 11.2/wk $-21364; give-backs 7.0/wk (6.8 round-trips) realised $-8925, forgone vs target $23691; same-side losing runs max 13, p95 6, $-44627 lost on 3rd-and-later; no-new-evidence re-entries 33.6/wk $684; recoveries cut 12.3/wk $48020, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $3756/wk, losers avoided $3176/wk, net -289 $/wk; pnl $26309/wk.
NH_P7_A9_N20 HOLD (stack, per week): full stops 10.8/wk $-21199; give-backs 6.2/wk (5.9 round-trips) realised $-7821, forgone vs target $21106; same-side losing runs max 13, p95 6, $-37721 lost on 3rd-and-later; no-new-evidence re-entries 26.5/wk $1021; recoveries cut 11.0/wk $43477, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $3841/wk, losers avoided $3259/wk, net -1015 $/wk; pnl $17027/wk.
NH_P7_A9_N20 PRE: months missing (17 of 17), window not scored
NH_P7_A9_N20 X': months missing (10 of 10), window not scored


## 2.NH_P7_B9_X10N30 (12/43 months)
### windows vs JN05W2 (nf_score)
```
NH_P7_B9_X10N30
              cell     ref window  mean_all  ref_all  dmean_all       dd   dd_ref   cut  eq_cut  w20cut  months
0  NH_P7_B9_X10N30  JN05W2    L1M    2849.3    606.3     2243.0  38857.5  36370.5  -6.8    -8.9   370.0      12
1  NH_P7_B9_X10N30  JN05W2    L3M   16729.6  16015.2      714.4  42008.2  36370.5 -15.5   -17.7     4.5      12
2  NH_P7_B9_X10N30  JN05W2    L6M   25362.0  25136.9      225.1  42008.2  36370.5 -15.5   -17.7     8.9      12
3  NH_P7_B9_X10N30  JN05W2   HOLD   17689.1  17489.3      199.7  75443.1  63185.1 -19.4   -21.7    -3.3      12

```
### windows vs LPB_BASE (score_w)
```
NH_P7_B9_X10N30
              cell window  mean_all  mean_ref_all  dmean_all     mean       dd   dd_ref   cut    dmean  eq_cut       w20   w20_ref  calmar  mean_ref  months
0  NH_P7_B9_X10N30    L1M    2849.3         340.7     2508.6  -5377.9  38857.5  51252.7  24.2  10802.0    38.9   11397.3    1363.0    -7.2  -16179.8      12
1  NH_P7_B9_X10N30    L3M   16729.6       11956.7     4773.0  15888.6  42008.2  77224.2  45.6    963.2    56.2  217485.3  155436.8    19.7   14925.3      12
2  NH_P7_B9_X10N30    L6M   25362.0       18696.8     6665.1  25303.5  42008.2  77224.2  45.6   4912.1    56.2  287182.4  102383.9    31.3   20391.4      12
3  NH_P7_B9_X10N30   HOLD   17689.1       15236.3     2452.7  17510.0  75443.1  78842.0   4.3   1510.8    22.9 -270232.1 -377467.2    12.1   15999.2      12

```
### acceptance_p7
```
essions of the reference) and the frozen live week: re-entry winners after NEW EVIDENCE
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +24852 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +12698 (5 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +23257 (6 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +16251 (5 trades, 1 such winners $+4790)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net -10146 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 4 ($+18192); all re-entry winners (any evidence) reference 13, set 14
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)

SUMMARY NH_P7_B9_X10N30: fails 1 of 16 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->1', '0->0']
covered sessions 16 of 20
ACCEPT NH_P7_B9_X10N30 PASS fails=1/20

```
### behavioural scorecard (ref JN05W2)
NH_P7_B9_X10N30 L6M (stack, per week): full stops 11.3/wk $-21623; give-backs 7.3/wk (6.7 round-trips) realised $-8371, forgone vs target $24405; same-side losing runs max 13, p95 6, $-44470 lost on 3rd-and-later; no-new-evidence re-entries 33.4/wk $773; recoveries cut 12.2/wk $48358, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $2537/wk, losers avoided $2792/wk, net +238 $/wk; pnl $26836/wk.
NH_P7_B9_X10N30 HOLD (stack, per week): full stops 10.9/wk $-21349; give-backs 6.6/wk (6.0 round-trips) realised $-7452, forgone vs target $22226; same-side losing runs max 13, p95 6, $-37498 lost on 3rd-and-later; no-new-evidence re-entries 26.6/wk $1079; recoveries cut 11.1/wk $44272, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $2205/wk, losers avoided $2247/wk, net +205 $/wk; pnl $18247/wk.
NH_P7_B9_X10N30 PRE: months missing (17 of 17), window not scored
NH_P7_B9_X10N30 X': months missing (10 of 10), window not scored


## 2.NH_U7_B7_X20N60 (12/43 months)
### windows vs JN05W2 (nf_score)
```
NH_U7_B7_X20N60
              cell     ref window  mean_all  ref_all  dmean_all       dd   dd_ref  cut  eq_cut  w20cut  months
0  NH_U7_B7_X20N60  JN05W2    L1M    5948.2    606.3     5341.9  34476.5  36370.5  5.2     6.1   881.1      12
1  NH_U7_B7_X20N60  JN05W2    L3M   16888.8  16015.2      873.6  34476.5  36370.5  5.2     6.1     5.5      12
2  NH_U7_B7_X20N60  JN05W2    L6M   26112.6  25136.9      975.7  34476.5  36370.5  5.2     6.1    13.6      12
3  NH_U7_B7_X20N60  JN05W2   HOLD   18424.1  17489.3      934.8  65155.4  63185.1 -3.1    -2.2    13.2      12

```
### windows vs LPB_BASE (score_w)
```
NH_U7_B7_X20N60
              cell window  mean_all  mean_ref_all  dmean_all     mean       dd   dd_ref   cut   dmean  eq_cut       w20   w20_ref  calmar  mean_ref  months
0  NH_U7_B7_X20N60    L1M    5948.2         340.7     5607.4  19423.1  34476.5  51252.7  32.7  1884.5    48.5   23792.7    1363.0    29.3   17538.5      12
1  NH_U7_B7_X20N60    L3M   16888.8       11956.7     4932.1  16794.6  34476.5  77224.2  55.4  1869.2    65.8  219554.4  155436.8    25.3   14925.3      12
2  NH_U7_B7_X20N60    L6M   26112.6       18696.8     7415.8  24360.1  34476.5  77224.2  55.4  5699.7    65.8  299534.8  102383.9    36.7   18660.5      12
3  NH_U7_B7_X20N60   HOLD   18424.1       15236.3     3187.8  17414.3  65155.4  78842.0  17.4  2263.6    36.7 -227185.4 -377467.2    13.9   15150.7      12

```
### acceptance_p7
```
sessions of the reference) and the frozen live week: re-entry winners after NEW EVIDENCE
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +25963 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +14034 (5 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +21574 (5 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +17327 (5 trades, 1 such winners $+4790)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net -4895 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 4 ($+20390); all re-entry winners (any evidence) reference 13, set 14
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)

SUMMARY NH_U7_B7_X20N60: fails 1 of 16 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->1', '0->0']
covered sessions 16 of 20
ACCEPT NH_U7_B7_X20N60 PASS fails=1/20

```
### behavioural scorecard (ref JN05W2)
NH_U7_B7_X20N60 L6M (stack, per week): full stops 10.7/wk $-19659; give-backs 8.1/wk (7.2 round-trips) realised $-8462, forgone vs target $27516; same-side losing runs max 13, p95 6, $-43942 lost on 3rd-and-later; no-new-evidence re-entries 32.8/wk $1535; recoveries cut 12.2/wk $47811, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $391/wk, losers avoided $537/wk, net +1032 $/wk; pnl $27631/wk.
NH_U7_B7_X20N60 HOLD (stack, per week): full stops 10.3/wk $-19574; give-backs 7.2/wk (6.4 round-trips) realised $-7616, forgone vs target $24819; same-side losing runs max 13, p95 6, $-37006 lost on 3rd-and-later; no-new-evidence re-entries 26.2/wk $2022; recoveries cut 11.1/wk $44000, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $237/wk, losers avoided $381/wk, net +961 $/wk; pnl $19003/wk.
NH_U7_B7_X20N60 PRE: months missing (17 of 17), window not scored
NH_U7_B7_X20N60 X': months missing (10 of 10), window not scored


## 2.NH_M7_C9_F2 (43/43 months)
### windows vs JN05W2 (nf_score)
```
NH_M7_C9_F2
          cell     ref window  mean_all  ref_all  dmean_all       dd   dd_ref  cut  eq_cut  w20cut  wf2w_beat_pct  wf2w_cut  wf2w_mean  months
0  NH_M7_C9_F2  JN05W2    L1M     392.2    606.3     -214.1  35506.0  36370.5  2.4     4.1   -35.3           15.2       0.0       46.8      43
1  NH_M7_C9_F2  JN05W2    L3M   16466.0  16015.2      450.8  35506.0  36370.5  2.4     4.1     2.8           15.2       0.0       46.8      43
2  NH_M7_C9_F2  JN05W2    L6M   25426.5  25136.9      289.6  35506.0  36370.5  2.4     4.1     1.0           15.2       0.0       46.8      43
3  NH_M7_C9_F2  JN05W2   HOLD   17673.9  17489.3      184.5  60368.4  63185.1  4.5     6.1     4.5           15.2       0.0       46.8      43
4  NH_M7_C9_F2  JN05W2    PRE   10239.7  10167.9       71.9  75962.4  76186.1  0.3     2.0     0.4           15.2       0.0       46.8      43
5  NH_M7_C9_F2  JN05W2     X'    3733.4   3585.1      148.3  54293.6  55325.6  1.9     3.6     0.6           15.2       0.0       46.8      43

```
### windows vs LPB_BASE (score_w)
```
NH_M7_C9_F2
          cell window  mean_all  mean_ref_all  dmean_all     mean       dd    dd_ref   cut   dmean  eq_cut       w20   w20_ref  calmar  mean_ref  wf2w_beat_pct  wf2w_cut  wf2w_mean  months
0  NH_M7_C9_F2    L1M     392.2         340.7       51.4  -7508.0  35506.0   51252.7  30.7  8671.9    44.9    1568.6    1363.0   -11.0  -16179.8           45.6      -5.1     -181.0      43
1  NH_M7_C9_F2    L3M   16466.0       11956.7     4509.4  16531.3  35506.0   77224.2  54.0  1605.9    63.4  214058.4  155436.8    24.2   14925.3           45.6      -5.1     -181.0      43
2  NH_M7_C9_F2    L6M   25426.5       18696.8     6729.6  23447.0  35506.0   77224.2  54.0  4786.5    63.4  266290.2  102383.9    34.3   18660.5           45.6      -5.1     -181.0      43
3  NH_M7_C9_F2   HOLD   17673.9       15236.3     2437.5  16551.5  60368.4   78842.0  23.4  1400.9    39.1 -250037.1 -377467.2    14.3   15150.7           45.6      -5.1     -181.0      43
4  NH_M7_C9_F2    PRE   10239.7       11685.4    -1445.7  10496.1  75962.4   99479.4  23.6 -2096.3    39.2 -438914.8 -529227.7     7.2   12592.4           45.6      -5.1     -181.0      43
5  NH_M7_C9_F2     X'    3733.4        1333.6     2399.8   4397.2  54293.6  122552.7  55.7  1844.6    64.7 -219442.4 -321242.1     4.2    2552.6           45.6      -5.1     -181.0      43

```
### acceptance_p7
```
 L6M P7 sessions of the reference) and the frozen live week: re-entry winners after NEW EVIDENCE
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +25963 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +14034 (5 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +21574 (5 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +17327 (5 trades, 1 such winners $+4790)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net -4895 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 4 ($+20390); all re-entry winners (any evidence) reference 13, set 14
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)

SUMMARY NH_M7_C9_F2: fails 1 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->1', '0->0']
covered sessions 20 of 20
ACCEPT NH_M7_C9_F2 PASS fails=1/20

```
### behavioural scorecard (ref JN05W2)
NH_M7_C9_F2 L6M (stack, per week): full stops 11.2/wk $-21421; give-backs 8.2/wk (6.8 round-trips) realised $-9686, forgone vs target $27972; same-side losing runs max 13, p95 6, $-44449 lost on 3rd-and-later; no-new-evidence re-entries 33.0/wk $1353; recoveries cut 12.4/wk $48201, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $146/wk, losers avoided $137/wk, net +306 $/wk; pnl $26905/wk.
NH_M7_C9_F2 HOLD (stack, per week): full stops 10.7/wk $-21048; give-backs 7.5/wk (6.0 round-trips) realised $-8431, forgone vs target $25359; same-side losing runs max 13, p95 6, $-37163 lost on 3rd-and-later; no-new-evidence re-entries 26.2/wk $2110; recoveries cut 11.1/wk $44047, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $427/wk, losers avoided $515/wk, net +190 $/wk; pnl $18231/wk.
NH_M7_C9_F2 PRE (stack, per week): full stops 9.2/wk $-20018; give-backs 5.2/wk (4.1 round-trips) realised $-6092, forgone vs target $17666; same-side losing runs max 9, p95 4, $-20988 lost on 3rd-and-later; no-new-evidence re-entries 12.9/wk $1001; recoveries cut 6.7/wk $24435, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $167/wk, losers avoided $85/wk, net +73 $/wk; pnl $10418/wk.
NH_M7_C9_F2 X' (stack, per week): full stops 11.0/wk $-22500; give-backs 3.8/wk (2.8 round-trips) realised $-4153, forgone vs target $12185; same-side losing runs max 8, p95 4, $-11840 lost on 3rd-and-later; no-new-evidence re-entries 3.6/wk $369; recoveries cut 2.5/wk $8914, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $110/wk, losers avoided $92/wk, net +149 $/wk; pnl $3758/wk.


## 2.NH_M7_B9_X10N60 (43/43 months)
### windows vs JN05W2 (nf_score)
```
NH_M7_B9_X10N60
              cell     ref window  mean_all  ref_all  dmean_all       dd   dd_ref  cut  eq_cut  w20cut  wf2w_beat_pct  wf2w_cut  wf2w_mean  months
0  NH_M7_B9_X10N60  JN05W2    L1M    1191.6    606.3      585.3  35214.3  36370.5  3.2     5.0    96.5           10.1       0.0       86.1      43
1  NH_M7_B9_X10N60  JN05W2    L3M   17342.4  16015.2     1327.2  35214.3  36370.5  3.2     5.0     8.3           10.1       0.0       86.1      43
2  NH_M7_B9_X10N60  JN05W2    L6M   25817.8  25136.9      680.9  35214.3  36370.5  3.2     5.0     4.4           10.1       0.0       86.1      43
3  NH_M7_B9_X10N60  JN05W2   HOLD   17938.7  17489.3      449.4  61559.7  63185.1  2.6     4.4     8.0           10.1       0.0       86.1      43
4  NH_M7_B9_X10N60  JN05W2    PRE   10157.7  10167.9      -10.2  83265.6  76186.1 -9.3    -7.2    -0.8           10.1       0.0       86.1      43
5  NH_M7_B9_X10N60  JN05W2     X'    3626.2   3585.1       41.1  58738.1  55325.6 -6.2    -4.2    -0.1           10.1       0.0       86.1      43

```
### windows vs LPB_BASE (score_w)
```
NH_M7_B9_X10N60
              cell window  mean_all  mean_ref_all  dmean_all     mean       dd    dd_ref   cut   dmean  eq_cut       w20   w20_ref  calmar  mean_ref  wf2w_beat_pct  wf2w_cut  wf2w_mean  months
0  NH_M7_B9_X10N60    L1M    1191.6         340.7      850.9  -7066.6  35214.3   51252.7  31.3  9113.3    46.2    4766.5    1363.0   -10.4  -16179.8           44.3      -5.1     -168.9      43
1  NH_M7_B9_X10N60    L3M   17342.4       11956.7     5385.7  17529.0  35214.3   77224.2  54.4  2603.6    64.3  225450.6  155436.8    25.9   14925.3           44.3      -5.1     -168.9      43
2  NH_M7_B9_X10N60    L6M   25817.8       18696.8     7120.9  23834.7  35214.3   77224.2  54.4  5174.2    64.3  275189.9  102383.9    35.2   18660.5           44.3      -5.1     -168.9      43
3  NH_M7_B9_X10N60   HOLD   17938.7       15236.3     2702.3  16812.1  61559.7   78842.0  21.9  1661.5    38.9 -240661.7 -377467.2    14.2   15150.7           44.3      -5.1     -168.9      43
4  NH_M7_B9_X10N60    PRE   10157.7       11685.4    -1527.7  10427.6  83265.6   99479.4  16.3 -2164.8    34.5 -444304.8 -529227.7     6.5   12592.4           44.3      -5.1     -168.9      43
5  NH_M7_B9_X10N60     X'    3626.2        1333.6     2292.6   4266.7  58738.1  122552.7  52.1  1714.1    62.5 -220893.8 -321242.1     3.8    2552.6           44.3      -5.1     -168.9      43

```
### acceptance_p7
```
sessions of the reference) and the frozen live week: re-entry winners after NEW EVIDENCE
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +25963 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +14034 (5 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +21574 (5 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +17327 (5 trades, 1 such winners $+4790)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net -4895 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 4 ($+20390); all re-entry winners (any evidence) reference 13, set 14
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)

SUMMARY NH_M7_B9_X10N60: fails 1 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->1', '0->0']
covered sessions 20 of 20
ACCEPT NH_M7_B9_X10N60 PASS fails=1/20

```
### behavioural scorecard (ref JN05W2)
NH_M7_B9_X10N60 L6M (stack, per week): full stops 11.2/wk $-21416; give-backs 7.0/wk (6.8 round-trips) realised $-9933, forgone vs target $26697; same-side losing runs max 13, p95 6, $-44479 lost on 3rd-and-later; no-new-evidence re-entries 33.0/wk $1387; recoveries cut 12.5/wk $48391, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $1172/wk, losers avoided $1214/wk, net +720 $/wk; pnl $27319/wk.
NH_M7_B9_X10N60 HOLD (stack, per week): full stops 10.7/wk $-21044; give-backs 6.2/wk (6.0 round-trips) realised $-8750, forgone vs target $23962; same-side losing runs max 13, p95 6, $-37125 lost on 3rd-and-later; no-new-evidence re-entries 26.2/wk $2162; recoveries cut 11.1/wk $44052, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $1138/wk, losers avoided $1389/wk, net +462 $/wk; pnl $18504/wk.
NH_M7_B9_X10N60 PRE (stack, per week): full stops 9.2/wk $-19989; give-backs 4.6/wk (4.1 round-trips) realised $-6259, forgone vs target $16906; same-side losing runs max 9, p95 4, $-21078 lost on 3rd-and-later; no-new-evidence re-entries 12.9/wk $1053; recoveries cut 6.7/wk $24629, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $427/wk, losers avoided $337/wk, net -10 $/wk; pnl $10335/wk.
NH_M7_B9_X10N60 X' (stack, per week): full stops 11.0/wk $-22607; give-backs 3.4/wk (2.8 round-trips) realised $-4203, forgone vs target $11632; same-side losing runs max 8, p95 4, $-11903 lost on 3rd-and-later; no-new-evidence re-entries 3.7/wk $333; recoveries cut 2.5/wk $8869, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $280/wk, losers avoided $71/wk, net +41 $/wk; pnl $3650/wk.


## 2.NH_P7_B7_X10N60 (12/43 months)
### windows vs JN05W2 (nf_score)
```
NH_P7_B7_X10N60
              cell     ref window  mean_all  ref_all  dmean_all       dd   dd_ref  cut  eq_cut  w20cut  months
0  NH_P7_B7_X10N60  JN05W2    L1M    1029.7    606.3      423.4  36055.6  36370.5  0.9   -15.0    69.8      12
1  NH_P7_B7_X10N60  JN05W2    L3M   15824.7  16015.2     -190.5  36055.6  36370.5  0.9   -15.0    -1.2      12
2  NH_P7_B7_X10N60  JN05W2    L6M   22618.7  25136.9    -2518.2  36055.6  36370.5  0.9   -15.0    -5.2      12
3  NH_P7_B7_X10N60  JN05W2   HOLD   15293.5  17489.3    -2195.9  64253.2  63185.1 -1.7   -18.0     0.7      12

```
### windows vs LPB_BASE (score_w)
```
NH_P7_B7_X10N60
              cell window  mean_all  mean_ref_all  dmean_all     mean       dd   dd_ref   cut    dmean  eq_cut       w20   w20_ref  calmar  mean_ref  months
0  NH_P7_B7_X10N60    L1M    1029.7         340.7      689.0  -3833.2  36055.6  51252.7  29.7  12346.6    35.3    4118.9    1363.0    -5.5  -16179.8      12
1  NH_P7_B7_X10N60    L3M   15824.7       11956.7     3868.0  14297.6  36055.6  77224.2  53.3   -627.7    57.0  205720.6  155436.8    20.6   14925.3      12
2  NH_P7_B7_X10N60    L6M   22618.7       18696.8     3921.8  22157.5  36055.6  77224.2  53.3   1766.1    57.0  250011.3  102383.9    32.0   20391.4      12
3  NH_P7_B7_X10N60   HOLD   15293.5       15236.3       57.1  14923.7  64253.2  78842.0  18.5  -1075.4    25.0 -259974.8 -377467.2    12.1   15999.2      12

```
### acceptance_p7
```
P7 sessions of the reference) and the frozen live week: re-entry winners after NEW EVIDENCE
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +25763 (6 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +10861 (7 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +19013 (6 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +22294 (5 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net -8973 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 3 ($+12166); all re-entry winners (any evidence) reference 13, set 17
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)

SUMMARY NH_P7_B7_X10N60: fails 0 of 16 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
covered sessions 16 of 20
ACCEPT NH_P7_B7_X10N60 PASS fails=0/20

```
### behavioural scorecard (ref JN05W2)
NH_P7_B7_X10N60 L6M (stack, per week): full stops 11.0/wk $-20737; give-backs 6.2/wk (5.9 round-trips) realised $-6441, forgone vs target $17587; same-side losing runs max 13, p95 6, $-42783 lost on 3rd-and-later; no-new-evidence re-entries 34.1/wk $473; recoveries cut 12.6/wk $49490, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $7255/wk, losers avoided $5344/wk, net -2665 $/wk; pnl $23934/wk.
NH_P7_B7_X10N60 HOLD (stack, per week): full stops 10.7/wk $-20845; give-backs 5.8/wk (5.2 round-trips) realised $-5321, forgone vs target $16157; same-side losing runs max 13, p95 6, $-35963 lost on 3rd-and-later; no-new-evidence re-entries 27.1/wk $1470; recoveries cut 11.3/wk $45356, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $5754/wk, losers avoided $4932/wk, net -2241 $/wk; pnl $15800/wk.
NH_P7_B7_X10N60 PRE: months missing (17 of 17), window not scored
NH_P7_B7_X10N60 X': months missing (10 of 10), window not scored


## 2.NH_U7_B7_X30N120 (43/43 months)
### windows vs JN05W2 (nf_score)
```
NH_U7_B7_X30N120
               cell     ref window  mean_all  ref_all  dmean_all       dd   dd_ref  cut  eq_cut  w20cut  wf2w_beat_pct  wf2w_cut  wf2w_mean  months
0  NH_U7_B7_X30N120  JN05W2    L1M    5204.3    606.3     4598.0  34476.5  36370.5  5.2     6.6   758.4           10.1       0.0      100.8      43
1  NH_U7_B7_X30N120  JN05W2    L3M   16730.4  16015.2      715.2  36449.9  36370.5 -0.2     1.3     4.5           10.1       0.0      100.8      43
2  NH_U7_B7_X30N120  JN05W2    L6M   26173.8  25136.9     1036.9  36449.9  36370.5 -0.2     1.3    10.7           10.1       0.0      100.8      43
3  NH_U7_B7_X30N120  JN05W2   HOLD   18160.4  17489.3      671.1  63212.1  63185.1 -0.0     1.5     3.0           10.1       0.0      100.8      43
4  NH_U7_B7_X30N120  JN05W2    PRE   10288.1  10167.9      120.2  81926.6  76186.1 -7.5    -5.9     1.4           10.1       0.0      100.8      43
5  NH_U7_B7_X30N120  JN05W2     X'    3462.2   3585.1     -122.8  59311.6  55325.6 -7.2    -5.6     0.2           10.1       0.0      100.8      43

```
### windows vs LPB_BASE (score_w)
```
NH_U7_B7_X30N120
               cell window  mean_all  mean_ref_all  dmean_all     mean       dd    dd_ref   cut   dmean  eq_cut       w20   w20_ref  calmar  mean_ref  wf2w_beat_pct  wf2w_cut  wf2w_mean  months
0  NH_U7_B7_X30N120    L1M    5204.3         340.7     4863.6  18431.2  34476.5   51252.7  32.7   892.7    48.4   20817.2    1363.0    27.8   17538.5           45.6      -5.1     -275.0      43
1  NH_U7_B7_X30N120    L3M   16730.4       11956.7     4773.7  16840.9  36449.9   77224.2  52.8  1915.6    63.8  217495.4  155436.8    24.0   14925.3           45.6      -5.1     -275.0      43
2  NH_U7_B7_X30N120    L6M   26173.8       18696.8     7476.9  24346.9  36449.9   77224.2  52.8  5686.4    63.8  291948.9  102383.9    34.7   18660.5           45.6      -5.1     -275.0      43
3  NH_U7_B7_X30N120   HOLD   18160.4       15236.3     2924.0  17107.7  63212.1   78842.0  19.8  1957.1    38.5 -253834.7 -377467.2    14.1   15150.7           45.6      -5.1     -275.0      43
4  NH_U7_B7_X30N120    PRE   10288.1       11685.4    -1397.3  10545.1  81926.6   99479.4  17.6 -2047.3    36.9 -434490.1 -529227.7     6.7   12592.4           45.6      -5.1     -275.0      43
5  NH_U7_B7_X30N120     X'    3462.2        1333.6     2128.6   4044.4  59311.6  122552.7  51.6  1491.7    62.9 -220225.1 -321242.1     3.5    2552.6           45.6      -5.1     -275.0      43

```
### acceptance_p7
```
ssions of the reference) and the frozen live week: re-entry winners after NEW EVIDENCE
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +25963 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +14034 (5 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +21574 (5 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +17327 (5 trades, 1 such winners $+4790)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net -4895 (9 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 4 ($+20390); all re-entry winners (any evidence) reference 13, set 14
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)

SUMMARY NH_U7_B7_X30N120: fails 1 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->1', '0->0']
covered sessions 20 of 20
ACCEPT NH_U7_B7_X30N120 PASS fails=1/20

```
### behavioural scorecard (ref JN05W2)
NH_U7_B7_X30N120 L6M (stack, per week): full stops 10.9/wk $-19942; give-backs 8.0/wk (7.2 round-trips) realised $-9097, forgone vs target $27652; same-side losing runs max 13, p95 6, $-44403 lost on 3rd-and-later; no-new-evidence re-entries 32.9/wk $1275; recoveries cut 12.2/wk $47811, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $147/wk, losers avoided $-0/wk, net +1097 $/wk; pnl $27696/wk.
NH_U7_B7_X30N120 HOLD (stack, per week): full stops 10.4/wk $-19895; give-backs 7.2/wk (6.5 round-trips) realised $-8105, forgone vs target $25242; same-side losing runs max 13, p95 6, $-37242 lost on 3rd-and-later; no-new-evidence re-entries 26.3/wk $1870; recoveries cut 11.1/wk $44077, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $166/wk, losers avoided $91/wk, net +690 $/wk; pnl $18732/wk.
NH_U7_B7_X30N120 PRE (stack, per week): full stops 9.0/wk $-19232; give-backs 5.0/wk (4.4 round-trips) realised $-5973, forgone vs target $17413; same-side losing runs max 9, p95 4, $-21102 lost on 3rd-and-later; no-new-evidence re-entries 12.8/wk $1076; recoveries cut 6.7/wk $24633, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $24/wk, losers avoided $78/wk, net +122 $/wk; pnl $10468/wk.
NH_U7_B7_X30N120 X' (stack, per week): full stops 10.9/wk $-21862; give-backs 3.7/wk (3.0 round-trips) realised $-4396, forgone vs target $12292; same-side losing runs max 8, p95 4, $-11805 lost on 3rd-and-later; no-new-evidence re-entries 3.6/wk $531; recoveries cut 2.5/wk $8955, clipped fills 0.0/wk $0; vs JN05W2: winners skipped $0/wk, losers avoided $-0/wk, net -124 $/wk; pnl $3485/wk.


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

