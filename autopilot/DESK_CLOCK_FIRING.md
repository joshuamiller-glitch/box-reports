# DESK_CLOCK_FIRING (W-DYNC, order 2255Z step 1; written before anyone reads the scorecard). 27 Nov ~23:10Z
Source: exact-engine trade rows of the v0.2 DESK sets already run (DKMAIN = main row; sets A = book alone, M = in the live mix), runs_rf/<set>/<month>/trades.parquet, exit_name ExAlgoAll_CL (the clock rule) ; minutes to the bell = the book's session end (Asia 02:00 ET, London 08:30, NY AM 12:00, NY PM 17:00) minus the exit time. All finished months at the time of reading (24-37 per set; the first 8 + 12 forward months). Full table incl. DKNOGATE / DKNOSEAT sets: code/th_dync/desk_clock_firing.csv (script desk_clock_firing.py).
## ANSWER FIRST
The clock rule fired far outside 30 minutes: across the DKMAIN sets 16465 clock exits, 14631 of them (89%) with MORE than 30 minutes to the bell. On NY MF1 it is 1,792 of 1,810 clock exits (63% of ALL that book's exits), NP MF2 498 of 498, LO MF3 3,062 of 3,608, Asia books in the table. Only NY MF4 (narrow stop/target) fires near the bell (median 7.6 minutes). The logic error the relay described is real and large: the rerun as v0.2.1 is NOT skipped.
| book | set | months | trades | clock exits | share of exits | > 30 min left | 10-30 | 1-10 | <= 1 | median min to bell | p10 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| AS MF1 | A | 37 | 1492 | 514 | 34% | 514 | 0 | 0 | 0 | 426.1 | 313.6 |
| AS MF1 | M | 37 | 5371 | 525 | 10% | 525 | 0 | 0 | 0 | 424.4 | 308.3 |
| AS MF2 | A | 37 | 522 | 184 | 35% | 181 | 2 | 1 | 0 | 307.4 | 139.0 |
| AS MF2 | M | 37 | 5644 | 177 | 3% | 174 | 1 | 2 | 0 | 309.3 | 166.8 |
| AS MF3 | A | 37 | 2987 | 801 | 27% | 791 | 9 | 1 | 0 | 243.6 | 67.2 |
| AS MF3 | M | 37 | 5707 | 621 | 11% | 610 | 11 | 0 | 0 | 214.8 | 64.7 |
| LO MF1 | A | 37 | 1120 | 274 | 24% | 148 | 82 | 44 | 0 | 44.5 | 7.9 |
| LO MF1 | M | 37 | 5752 | 274 | 5% | 148 | 82 | 44 | 0 | 44.5 | 7.9 |
| LO MF3 | A | 37 | 4972 | 3608 | 73% | 3062 | 357 | 189 | 0 | 176.4 | 19.1 |
| LO MF3 | M | 37 | 8904 | 3608 | 40% | 3062 | 357 | 189 | 0 | 176.4 | 19.1 |
| NP MF2 | A | 24 | 759 | 498 | 66% | 498 | 0 | 0 | 0 | 165.4 | 96.7 |
| NP MF2 | M | 24 | 4844 | 476 | 10% | 476 | 0 | 0 | 0 | 169.4 | 97.6 |
| NP MF3 | A | 24 | 753 | 114 | 15% | 114 | 0 | 0 | 0 | 88.9 | 78.0 |
| NP MF3 | M | 24 | 4484 | 106 | 2% | 106 | 0 | 0 | 0 | 89.6 | 82.5 |
| NY MF1 | A | 24 | 2852 | 1810 | 64% | 1792 | 13 | 5 | 0 | 123.2 | 78.7 |
| NY MF1 | M | 24 | 12403 | 1807 | 15% | 1791 | 11 | 5 | 0 | 123.2 | 78.8 |
| NY MF2 | A | 24 | 1751 | 228 | 13% | 165 | 48 | 15 | 0 | 60.9 | 14.2 |
| NY MF2 | M | 24 | 10839 | 224 | 2% | 165 | 47 | 12 | 0 | 62.4 | 14.8 |
| NY MF4 | A | 24 | 2007 | 69 | 3% | 3 | 17 | 49 | 0 | 7.6 | 2.4 |
| NY MF4 | M | 24 | 10142 | 70 | 1% | 3 | 17 | 50 | 0 | 6.9 | 2.4 |
| NY MF5 | A | 24 | 2188 | 242 | 11% | 153 | 78 | 11 | 0 | 40.0 | 15.2 |
| NY MF5 | M | 24 | 10818 | 235 | 2% | 150 | 76 | 9 | 0 | 40.4 | 15.6 |
Reading the columns: share of exits = clock exits / all exits of that set; the last two columns are minutes to the bell at firing (median and 10th percentile).
## AMENDMENT v0.2.1 (change no. 4, reason 'logic error in the clock rule')
Clock rule applies only when 30 minutes or fewer remain to the session bell (ONE fixed value); 'one minute left in profit -> all' unchanged; nothing else changes. Code: DESK param clock_max_min (None = v0.2 as it ran; 30 = v0.2.1); config code/th_dync/desk_configs_v021.json (params_desk and params_desk_risk with clock_max_min 30). The class default stays v0.2 so the v0.2 config and rows keep their label.
## RERUN
All v0.2 sets are to be rerun as v0.2.1 (class -2, rows_c0_0first.txt) by W-DYNH from desk_configs_v021.json (set names to be chosen by W-DYNH, e.g. DK21MAIN / DK21NOSEAT / DK21NOGATE); the v0.2 rows stay labelled. Scorecard and tape review are read on v0.2.1.
