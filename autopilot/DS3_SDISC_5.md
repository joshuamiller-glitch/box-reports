# DS3_SDISC_5 - session-specific brackets and management (T-SESSION-DISCOVER item 5, agent D3SD56, 2026-10-28)
Research only; nothing live; UNTOUCHED never read. Prereg l2vast/ds3/prereg/SD56_5_prereg.md sha256 86e3599f77d2f884ef469567f14f4a55ab39c051cea2ade3e02da0c1388abddb; PREHOLD autopilot/DS3_SDISC_5_PREHOLD.md sha256 60cd141dc0d2f22c8898fdd8022ff241008cff67d79ed5bf2e273c0efb574857 (both in DECISIONS.md before any HOLD/X number); one HOLD+X look (out/sd56/looks.jsonl). Code l2vast/ds3/code/sd56/, data out/sd56/ (item5_stageA_pre.csv 936 cells PRE, item5_stageB.csv/item5_tiers.csv 63 PREHOLD cells, item5_weekly.parquet, survivors_for_A.parquet).

## Verdict (plain)
- **There is no session whose bracket or management beats the stored 60/60 run-to-bracket by more than its MDE on the MEASURED basis, and tight brackets lose everywhere.** Every symmetric bracket under 40 pt has a negative average PRE mean in every session (15/15 -1.5 to -2.1 pts/trade, 30/30 -0.7 to -1.3) because the MEASURED stop excess (0.6-0.8 pt) and the P9 target correction (-1.4 to -4.3 pt) are paid on every exit; the 20/30 and 30/20 asymmetric pairs lose the same way. The sub-minute ICT cells do NOT want 20/30 on MEASURED; the only X-stream cell PRE-significant in LONDON is IF_5m_tg_pd at 60/60 and it fails HOLD (-3.0).
- **ASIA:** 7 of 11 PRE-selected cells are PRE-significant (EM, HM, PE, SM at 40-60 pt) and 0 pass HOLD (HOLD +1.3, +2.2, +0.2, +0.8, -0.05, +1.9, -0.6; every one has H25 <= 0 or H26 < 0 or lands inside its MDE of 5-17 pts); against a random-in-session entry with the same side, bracket and management the PRE-selected ASIA cells are BELOW random in HOLD (effect -1.0 to -10.3, rank 0.00-0.35): the ASIA positive mean of the stored 60/60 books is session drift that random entries earn too, not entry timing. This repeats the D3SA caveat for ba2/KB, SM and TB4.
- **NY-AM:** one SESSION-CANDIDATE on MEASURED: X SB_HM_st_vw_5 at target 60 / stop 40, run-to-bracket (silver-bullet HM structure entry; PRE +4.39 CI lo >0, HOLD +4.57, H25 +3.73, H26 +9.58, 2023 span -0.41), but HOLD 4.57 is inside its MDE 12.7, HOLD-vs-random -0.9 (rank 0.38) and best-of-F (p 0.16 vs 0.05/936) is not cleared. The live-engine NY-AM cells (HM, ST, KB) reach no PRE significance in this grid (the ba2/HM_t75_s90 +5.45 of D3SA is a 75/90 cell on the ledger sequence, outside this grid; its stream here is scored at 60/60 and the grid pairs).
- **LONDON, PRE, NY-PM:** nothing PRE-significant that survives (LONDON 1 PRE-significant, HOLD -3.0; PRE session 0; NY-PM 0). CLOSE: no cell exists (stack engines are entry-blocked 15:00-16:54; no ledger cell is alive there).
- **Flat vs run vs carry (handoff):** flat-at-session-end is statistically the same as run-to-bracket (PRE paired by bracket: ASIA +0.18, LONDON -0.13, NY-AM -0.14, NY-PM +0.63, PRE +0.38 pt/trade, all inside any cell's MDE of 3-17). The carry-with-tightened-stop (stop to 0.5 x the original distance from the session-end mark) loses in EVERY session (-2.1 to -5.5 pt/trade vs run; 0 of the cells beat run in any session): tightening converts winners that were still running into stops. Verdict: no handoff; ASIA/LONDON/NY trades may run to bracket or flat at the session end with equal expectation; flat caps overlap with the next session and removes the overnight gap risk at no measured cost.
- Survivors for the D3SA replay: out/sd56/survivors_for_A.parquet (13 PRE-significant cells, 9,260 entries, same columns as entries.parquet plus cell/session/mode/tier_analytic); the carry cell is flagged (the tightened leg is not expressible in the entries layout).


## Counts per session (F = 936 cells screened, 63 listed in the PREHOLD, best-of-F p threshold 0.05/936 = 5.3e-5)
| session   |   listed |   pre_sig |   candidate |   passed |
|:----------|---------:|----------:|------------:|---------:|
| ASIA      |       15 |         7 |           0 |        0 |
| LONDON    |       10 |         1 |           0 |        0 |
| NY-AM     |       15 |         5 |           1 |        0 |
| NY-PM     |       15 |         0 |           0 |        0 |
| PRE       |        8 |         0 |           0 |        0 |

## Symmetric/asymmetric/structure bracket pattern (PRE MEASURED mean pts/trade, run mode, averaged over the session's streams; all 13 brackets)
| bracket   |   ASIA |   LONDON |   NY-AM |   NY-PM |   PRE |
|:----------|-------:|---------:|--------:|--------:|------:|
| s15       |  -1.49 |    -1.66 |   -1.73 |   -2.10 | -2.03 |
| s20       |  -0.66 |    -1.10 |   -1.31 |   -2.01 | -2.00 |
| s30       |  -0.71 |    -0.99 |   -1.33 |   -1.22 | -1.29 |
| s40       |   2.03 |    -0.01 |   -0.48 |   -0.72 | -3.72 |
| s50       |   2.09 |     0.39 |    1.18 |   -0.60 | -2.17 |
| s60       |   3.69 |     1.42 |    3.48 |   -0.16 | -3.06 |
| st1       |  -0.12 |    -0.78 |   -0.11 |    0.24 | -3.06 |
| st15      |  -0.57 |    -1.10 |    0.78 |    0.62 | -1.32 |
| st2       |   0.59 |    -1.44 |    1.89 |    1.60 | -0.10 |
| t20s30    |  -0.84 |    -1.19 |   -1.70 |   -1.43 | -1.96 |
| t30s20    |  -0.38 |    -1.13 |   -0.69 |   -2.24 | -1.16 |
| t40s60    |   3.45 |     1.08 |   -0.02 |   -1.21 | -3.87 |
| t60s40    |   2.96 |    -0.29 |    2.35 |   -0.13 | -2.90 |

## Handoff, PRE only, paired by (stream, bracket) over all cells
| session   |   cells |   flat-run mean |   flat-run share>0 |   carry-run mean |   carry-run share>0 |
|:----------|--------:|----------------:|-------------------:|-----------------:|--------------------:|
| ASIA      |   65.00 |            0.18 |               0.71 |            -3.78 |                0.00 |
| LONDON    |   65.00 |           -0.13 |               0.54 |            -2.07 |                0.00 |
| NY-AM     |   65.00 |           -0.14 |               0.37 |            -2.45 |                0.00 |
| NY-PM     |   65.00 |            0.63 |               0.88 |            -2.75 |                0.00 |
| PRE       |   52.00 |            0.38 |               0.48 |            -5.48 |                0.00 |
PRE-only because the HOLD look is restricted to the PREHOLD cells (the flat/carry cells at the run-selected bracket were not listed). Carry never wins; flat ~ run.

## ASIA - all PREHOLD cells (PRE-selected per stream x mode + the 60/60 run baseline), MEASURED analytic, pts/trade net; $/wk at $1,000 risk with the -2R/+5R session-book lock
| stream   | bracket   | mode   | role     |   n PRE |   PRE pts |   PRE CI lo |   PRE MDE |   n HOLD |   HOLD pts |   HOLD MDE |   H25 |   H26 |   X 2023 |   PRE $/wk |   HOLD $/wk |   HOLD vs random |   rank | tier          | failed gate                |
|:---------|:----------|:-------|:---------|--------:|----------:|------------:|----------:|---------:|-----------:|-----------:|------:|------:|---------:|-----------:|------------:|-----------------:|-------:|:--------------|:---------------------------|
| EM       | t20s30    | carry  | selected |     311 |      0.60 |       -1.95 |      3.64 |      165 |      -5.90 |       5.34 | -7.55 |  1.51 |    -4.95 |      89.06 |    -1139.51 |            -4.00 |   0.00 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H25<=0 |
| EM       | t40s60    | flat   | selected |     260 |      6.09 |        2.45 |      5.19 |      134 |       1.34 |       8.27 | -1.42 | 13.40 |    -0.29 |     422.11 |       90.31 |            -2.65 |   0.16 | NOT-CONFIRMED | H25<=0                     |
| EM       | s60       | run    | baseline |     249 |      3.42 |       -3.37 |      9.71 |      128 |      -0.26 |      15.11 | -3.04 | 11.82 |    -2.04 |     227.39 |      -55.09 |            -5.21 |   0.06 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H25<=0 |
| EM       | s40       | run    | selected |     282 |      5.62 |        1.67 |      5.64 |      145 |       2.20 |       9.48 | -0.58 | 14.89 |    -0.76 |     433.50 |      198.95 |            -1.00 |   0.35 | NOT-CONFIRMED | H25<=0                     |
| HM       | t40s60    | flat   | selected |     723 |      3.41 |        1.04 |      3.39 |      346 |       0.18 |       5.08 | -1.01 |  4.49 |    -0.25 |     630.88 |       50.11 |            -5.29 |   0.00 | NOT-CONFIRMED | H25<=0                     |
| HM       | s60       | run    | baseline |     610 |      2.33 |       -1.46 |      5.42 |      284 |       4.52 |       8.64 |  4.39 |  5.04 |     2.43 |     416.77 |      902.43 |            -2.61 |   0.13 | NOT-CONFIRMED | PRE CI<=0                  |
| HM       | t40s60    | run    | selected |     723 |      3.42 |        0.42 |      4.28 |      346 |       0.79 |       5.71 | -0.27 |  4.62 |    -0.24 |     682.08 |      249.30 |            -5.53 |   0.00 | NOT-CONFIRMED | H25<=0                     |
| KB       | t40s60    | flat   | selected |     899 |      2.07 |       -0.60 |      3.81 |      444 |      -1.22 |       4.98 | -3.36 |  5.50 |     1.15 |     536.61 |      -57.70 |            -3.49 |   0.00 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H25<=0 |
| KB       | s60       | run    | baseline |     748 |      3.37 |       -0.64 |      5.74 |      354 |       1.70 |       8.63 | -1.47 | 12.36 |    -2.07 |     569.49 |      732.90 |            -4.45 |   0.01 | NOT-CONFIRMED | PRE CI<=0, H25<=0          |
| KB       | t40s60    | run    | selected |     899 |      2.71 |       -0.38 |      4.41 |      444 |       0.86 |       5.59 | -0.69 |  5.74 |     1.34 |     635.47 |      381.25 |            -2.23 |   0.13 | NOT-CONFIRMED | PRE CI<=0, H25<=0          |
| PE       | t60s40    | flat   | selected |     700 |      3.03 |        0.49 |      3.63 |      320 |      -0.05 |       6.69 |  0.16 | -0.75 |    -1.94 |     452.91 |      106.29 |            -7.66 |   0.00 | NOT-CONFIRMED | HOLD<=0, H26<=0            |
| PE       | s60       | run    | baseline |     699 |      1.57 |       -2.89 |      6.37 |      320 |       1.90 |       8.33 |  2.81 | -1.14 |    -4.35 |     261.41 |      218.92 |            -8.13 |   0.01 | NOT-CONFIRMED | PRE CI<=0, H26<=0          |
| PE       | t60s40    | run    | selected |     700 |      3.17 |        0.03 |      4.48 |      320 |       1.91 |       7.41 |  2.64 | -0.52 |    -5.02 |     503.35 |      431.18 |            -7.47 |   0.00 | NOT-CONFIRMED | H26<=0                     |
| SM       | s60       | flat   | selected |     242 |      4.79 |       -0.34 |      7.33 |      113 |      -0.65 |      12.37 | -2.27 |  5.71 |     0.21 |     305.88 |      -18.65 |            -8.93 |   0.00 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H25<=0 |
| SM       | s60       | run    | selected |     242 |      7.73 |        0.10 |     10.89 |      113 |      -0.55 |      16.69 |  0.64 | -5.24 |     1.57 |     514.99 |        2.22 |           -10.33 |   0.01 | NOT-CONFIRMED | HOLD<=0, H26<=0            |

## LONDON - all PREHOLD cells (PRE-selected per stream x mode + the 60/60 run baseline), MEASURED analytic, pts/trade net; $/wk at $1,000 risk with the -2R/+5R session-book lock
| stream        | bracket   | mode   | role     |   n PRE |   PRE pts |   PRE CI lo |   PRE MDE |   n HOLD |   HOLD pts |   HOLD MDE |   H25 |   H26 |   X 2023 |   PRE $/wk |   HOLD $/wk |   HOLD vs random |   rank | tier          | failed gate                        |
|:--------------|:----------|:-------|:---------|--------:|----------:|------------:|----------:|---------:|-----------:|-----------:|------:|------:|---------:|-----------:|------------:|-----------------:|-------:|:--------------|:-----------------------------------|
| EM            | s60       | run    | baseline |     329 |     -1.20 |       -6.84 |      8.06 |      138 |      -0.04 |      11.89 | -1.02 |  4.87 |    -5.53 |    -120.16 |       -0.07 |            -7.29 |   0.04 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H25<=0         |
| EM            | s50       | run    | selected |     352 |      0.56 |       -4.42 |      7.11 |      144 |      -0.08 |      11.36 | -0.74 |  3.07 |    -7.49 |       1.79 |       -4.14 |            -5.15 |   0.05 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H25<=0         |
| HM            | s60       | run    | baseline |     719 |     -0.94 |       -5.05 |      5.88 |      313 |      -0.68 |       8.63 | -0.62 | -0.90 |     1.25 |    -311.11 |     -427.96 |            -6.33 |   0.00 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H25<=0, H26<=0 |
| HM            | t60s40    | run    | selected |     858 |      0.25 |       -3.00 |      4.64 |      365 |      -2.56 |       6.04 | -3.49 |  0.95 |     0.57 |      12.89 |     -602.67 |            -6.20 |   0.00 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H25<=0         |
| KB            | s60       | run    | baseline |     871 |     -0.83 |       -4.52 |      5.26 |      359 |      -1.48 |       8.81 | -2.60 |  3.36 |     0.87 |    -137.47 |     -251.50 |            -4.78 |   0.02 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H25<=0         |
| X:IF_3m_tg_pd | s40       | flat   | selected |     359 |      2.11 |       -1.38 |      4.99 |      172 |      -1.03 |       8.27 |  0.20 | -7.64 |    -1.10 |     201.99 |      -93.82 |             2.00 |   0.88 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H26<=0         |
| X:IF_3m_tg_pd | s60       | run    | baseline |     295 |      2.85 |       -4.12 |      9.95 |      137 |       7.62 |      15.01 |  9.81 | -2.71 |     3.42 |     224.97 |      690.42 |             5.65 |   0.96 | NOT-CONFIRMED | PRE CI<=0, H26<=0                  |
| X:IF_3m_tg_pd | t40s60    | run    | selected |     327 |      3.39 |       -2.15 |      7.92 |      151 |       0.25 |      10.80 |  1.67 | -6.93 |     0.90 |     301.98 |       61.56 |             1.80 |   0.76 | NOT-CONFIRMED | PRE CI<=0, H26<=0                  |
| X:IF_5m_tg_pd | s60       | flat   | selected |     258 |      4.00 |       -0.99 |      7.13 |      111 |      -4.21 |      12.97 | -7.73 | 20.20 |     1.32 |     275.19 |     -275.80 |             2.95 |   0.89 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H25<=0         |
| X:IF_5m_tg_pd | s60       | run    | selected |     258 |      7.25 |        0.39 |      9.79 |      111 |      -3.02 |      17.27 | -6.66 | 22.21 |     0.29 |     498.47 |     -171.37 |             3.14 |   0.82 | NOT-CONFIRMED | HOLD<=0, H25<=0                    |

## PRE - all PREHOLD cells (PRE-selected per stream x mode + the 60/60 run baseline), MEASURED analytic, pts/trade net; $/wk at $1,000 risk with the -2R/+5R session-book lock
| stream        | bracket   | mode   | role     |   n PRE |   PRE pts |   PRE CI lo |   PRE MDE |   n HOLD |   HOLD pts |   HOLD MDE |    H25 |    H26 |   X 2023 |   PRE $/wk |   HOLD $/wk |   HOLD vs random |   rank | tier          | failed gate                        |
|:--------------|:----------|:-------|:---------|--------:|----------:|------------:|----------:|---------:|-----------:|-----------:|-------:|-------:|---------:|-----------:|------------:|-----------------:|-------:|:--------------|:-----------------------------------|
| HM            | s60       | run    | baseline |     183 |     -7.38 |      -15.44 |     11.52 |       68 |       2.00 |      20.09 |  -0.15 |  13.15 |    -4.83 |    -360.09 |       84.87 |            -3.02 |   0.25 | NOT-CONFIRMED | PRE CI<=0, H25<=0                  |
| HM            | st2       | run    | selected |     184 |      3.74 |       -6.28 |     14.31 |       67 |       1.34 |      21.17 |  -3.95 |  28.27 |   -13.39 |     133.50 |       55.77 |             1.64 |   0.65 | NOT-CONFIRMED | PRE CI<=0, H25<=0                  |
| KB            | s60       | run    | baseline |     302 |     -2.11 |       -7.70 |      7.99 |      120 |      -3.78 |      14.18 |   0.73 | -23.86 |     0.34 |    -169.62 |     -318.06 |            -8.20 |   0.00 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H26<=0         |
| ST            | t60s40    | flat   | selected |     336 |      0.60 |       -3.20 |      5.43 |      134 |      -7.93 |       6.97 |  -7.38 | -10.89 |     2.78 |      51.87 |     -664.26 |            -2.72 |   0.05 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H25<=0, H26<=0 |
| ST            | s60       | run    | baseline |     316 |      0.84 |       -5.65 |      9.28 |      131 |     -15.28 |       9.53 | -16.50 |  -8.53 |     5.08 |      40.78 |    -1250.99 |            -6.32 |   0.00 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H25<=0, H26<=0 |
| ST            | s30       | run    | selected |     379 |      0.80 |       -2.38 |      4.54 |      147 |      -9.42 |       6.11 |  -9.97 |  -6.45 |     1.98 |     177.33 |    -1614.81 |            -2.99 |   0.03 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H25<=0, H26<=0 |
| X:IF_3m_tg_so | s60       | run    | baseline |     170 |     -3.59 |      -12.39 |     12.56 |       77 |       3.50 |      15.94 |   2.86 |   6.98 |    -5.55 |    -162.89 |      168.48 |             3.51 |   0.83 | NOT-CONFIRMED | PRE CI<=0                          |
| X:IF_3m_tg_so | st15      | run    | selected |     182 |      0.05 |       -3.81 |      5.52 |       82 |       6.37 |       5.29 |   7.08 |   2.95 |    -2.25 |     -40.93 |      653.40 |             6.42 |   1.00 | NOT-CONFIRMED | PRE CI<=0                          |

## NY-AM - all PREHOLD cells (PRE-selected per stream x mode + the 60/60 run baseline), MEASURED analytic, pts/trade net; $/wk at $1,000 risk with the -2R/+5R session-book lock
| stream          | bracket   | mode   | role     |   n PRE |   PRE pts |   PRE CI lo |   PRE MDE |   n HOLD |   HOLD pts |   HOLD MDE |   H25 |   H26 |   X 2023 |   PRE $/wk |   HOLD $/wk |   HOLD vs random |   rank | tier              | failed gate                        |
|:----------------|:----------|:-------|:---------|--------:|----------:|------------:|----------:|---------:|-----------:|-----------:|------:|------:|---------:|-----------:|------------:|-----------------:|-------:|:------------------|:-----------------------------------|
| HM              | st1       | flat   | selected |     489 |      1.63 |       -2.58 |      6.01 |      206 |       2.32 |      10.67 | -1.29 | 23.49 |    -4.58 |     190.37 |      251.53 |            -2.20 |   0.14 | NOT-CONFIRMED     | PRE CI<=0, H25<=0                  |
| HM              | s60       | run    | baseline |     478 |      1.29 |       -3.26 |      6.50 |      201 |       3.59 |      11.07 |  0.81 | 18.27 |    -2.98 |     136.58 |      454.39 |            -7.14 |   0.03 | NOT-CONFIRMED     | PRE CI<=0                          |
| HM              | st2       | run    | selected |     408 |      4.21 |       -4.45 |     12.38 |      179 |       4.95 |      16.96 |  4.93 |  5.03 |    -4.33 |     327.35 |      812.53 |            -2.61 |   0.28 | NOT-CONFIRMED     | PRE CI<=0                          |
| KB              | s60       | flat   | selected |     751 |      2.25 |       -1.28 |      5.04 |      348 |      -1.57 |       7.61 | -1.07 | -3.89 |     1.72 |     468.19 |     -347.57 |           -10.10 |   0.00 | NOT-CONFIRMED     | PRE CI<=0, HOLD<=0, H25<=0, H26<=0 |
| KB              | s60       | run    | selected |     751 |      2.62 |       -1.05 |      5.23 |      348 |      -0.83 |       9.26 |  0.16 | -5.37 |     1.47 |     494.93 |     -104.64 |            -9.60 |   0.01 | NOT-CONFIRMED     | PRE CI<=0, HOLD<=0, H26<=0         |
| ST              | s60       | run    | baseline |     772 |      1.27 |       -2.90 |      5.96 |      370 |       3.73 |       6.29 |  3.19 |  6.28 |    -3.23 |      25.33 |      792.82 |            -4.19 |   0.06 | NOT-CONFIRMED     | PRE CI<=0                          |
| ST              | t40s60    | run    | selected |     864 |      0.94 |       -2.05 |      4.28 |      421 |       1.82 |       5.48 |  1.51 |  3.18 |    -3.72 |     106.22 |      372.68 |            -3.49 |   0.02 | NOT-CONFIRMED     | PRE CI<=0                          |
| X:SB_HM_st_sig0 | t60s40    | carry  | selected |     183 |      6.26 |        0.58 |      8.11 |       99 |       1.97 |      16.59 | -2.05 | 16.04 |     5.87 |     290.79 |      122.12 |            -1.21 |   0.42 | NOT-CONFIRMED     | H25<=0                             |
| X:SB_HM_st_sig0 | t60s40    | flat   | selected |     183 |      6.91 |        1.31 |      7.99 |       99 |       1.51 |      16.94 | -2.36 | 15.08 |     5.96 |     322.23 |       93.67 |            -3.25 |   0.23 | NOT-CONFIRMED     | H25<=0                             |
| X:SB_HM_st_sig0 | s60       | run    | baseline |     183 |      6.66 |        0.26 |      9.15 |       99 |       2.62 |      18.65 | -1.90 | 18.43 |     3.59 |     324.97 |       92.57 |            -7.71 |   0.08 | NOT-CONFIRMED     | H25<=0                             |
| X:SB_HM_st_sig0 | t60s40    | run    | selected |     183 |      7.35 |        1.82 |      7.89 |       99 |       2.95 |      17.38 | -0.79 | 16.04 |     6.12 |     343.63 |      182.37 |            -2.47 |   0.29 | NOT-CONFIRMED     | H25<=0                             |
| X:SB_HM_st_vw_5 | t60s40    | carry  | selected |     339 |      1.98 |       -2.47 |      6.35 |      146 |      -1.12 |      11.47 | -2.15 |  5.00 |    -5.69 |     178.93 |     -102.53 |            -1.34 |   0.38 | NOT-CONFIRMED     | PRE CI<=0, HOLD<=0, H25<=0         |
| X:SB_HM_st_vw_5 | t60s40    | flat   | selected |     339 |      3.63 |       -0.31 |      5.63 |      146 |       3.77 |      10.60 |  2.40 | 11.95 |    -1.00 |     328.46 |      344.20 |            -1.66 |   0.37 | NOT-CONFIRMED     | PRE CI<=0                          |
| X:SB_HM_st_vw_5 | s60       | run    | baseline |     338 |      5.56 |       -0.22 |      8.25 |      146 |       3.28 |      13.56 |  2.17 |  9.89 |    -1.57 |     488.23 |      195.20 |            -5.44 |   0.07 | NOT-CONFIRMED     | PRE CI<=0                          |
| X:SB_HM_st_vw_5 | t60s40    | run    | selected |     339 |      4.39 |        0.00 |      6.27 |      146 |       4.57 |      12.74 |  3.73 |  9.58 |    -0.41 |     397.15 |      417.15 |            -0.91 |   0.38 | SESSION-CANDIDATE | best-of-F                          |

## NY-PM - all PREHOLD cells (PRE-selected per stream x mode + the 60/60 run baseline), MEASURED analytic, pts/trade net; $/wk at $1,000 risk with the -2R/+5R session-book lock
| stream   | bracket   | mode   | role     |   n PRE |   PRE pts |   PRE CI lo |   PRE MDE |   n HOLD |   HOLD pts |   HOLD MDE |    H25 |    H26 |   X 2023 |   PRE $/wk |   HOLD $/wk |   HOLD vs random |   rank | tier          | failed gate                        |
|:---------|:----------|:-------|:---------|--------:|----------:|------------:|----------:|---------:|-----------:|-----------:|-------:|-------:|---------:|-----------:|------------:|-----------------:|-------:|:--------------|:-----------------------------------|
| EM       | st2       | carry  | selected |     169 |      1.62 |       -5.16 |      9.68 |       54 |       4.06 |      14.55 |   4.25 |   2.81 |   -10.38 |      -7.11 |      297.20 |             1.19 |   0.55 | NOT-CONFIRMED | PRE CI<=0                          |
| EM       | st2       | flat   | selected |     169 |      4.73 |       -1.49 |      8.89 |       54 |      11.75 |      15.22 |   6.09 |  49.75 |    -5.30 |     228.17 |      658.28 |             6.08 |   0.94 | NOT-CONFIRMED | PRE CI<=0                          |
| EM       | s60       | run    | baseline |     149 |      0.58 |       -8.15 |     12.47 |       50 |       5.24 |      19.67 |   2.48 |  22.21 |    -4.73 |      40.71 |      163.72 |            -9.37 |   0.06 | NOT-CONFIRMED | PRE CI<=0                          |
| EM       | st2       | run    | selected |     169 |      3.71 |       -2.97 |      9.54 |       54 |       9.71 |      13.66 |   6.57 |  30.86 |    -6.42 |     181.63 |      556.66 |             4.10 |   0.83 | NOT-CONFIRMED | PRE CI<=0                          |
| HM       | st2       | flat   | selected |     589 |      3.57 |       -0.81 |      6.26 |      247 |      -4.82 |       5.82 |  -3.34 | -11.82 |    -0.05 |     689.69 |    -1359.79 |            -7.10 |   0.00 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H25<=0, H26<=0 |
| HM       | s60       | run    | baseline |     583 |     -1.80 |       -5.91 |      5.87 |      234 |      -0.52 |       9.43 |   0.92 |  -6.94 |     0.36 |    -333.30 |     -170.52 |            -7.91 |   0.00 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H26<=0         |
| HM       | st2       | run    | selected |     589 |      0.95 |       -3.13 |      5.83 |      247 |      -8.00 |       7.60 |  -8.59 |  -5.15 |    -0.09 |     299.03 |    -1928.37 |            -9.15 |   0.00 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H25<=0, H26<=0 |
| KB       | s60       | flat   | selected |     815 |      1.28 |       -2.17 |      4.92 |      328 |      -1.90 |       7.34 |  -1.90 |  -1.95 |    -1.09 |     363.77 |     -599.89 |            -6.07 |   0.00 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H25<=0, H26<=0 |
| KB       | s60       | run    | selected |     815 |      0.74 |       -3.31 |      5.79 |      328 |      -0.32 |       7.32 |   0.01 |  -1.96 |    -3.57 |     275.35 |     -294.72 |            -5.93 |   0.01 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H26<=0         |
| SM       | st2       | flat   | selected |     110 |      7.98 |       -5.17 |     18.79 |       32 |       3.43 |      34.54 |  -8.91 |  40.44 |     1.18 |     286.48 |       -8.31 |            -7.77 |   0.18 | NOT-CONFIRMED | PRE CI<=0, H25<=0                  |
| SM       | s60       | run    | baseline |     110 |      0.04 |       -9.45 |     13.55 |       32 |       1.52 |      28.96 |  -8.86 |  32.69 |    -7.93 |       1.04 |       30.48 |           -19.96 |   0.00 | NOT-CONFIRMED | PRE CI<=0, H25<=0                  |
| SM       | st1       | run    | selected |     110 |      3.79 |       -5.33 |     13.02 |       32 |      -0.78 |      29.34 | -10.34 |  27.89 |     2.70 |     139.95 |     -103.56 |            -4.77 |   0.20 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H25<=0         |
| ST       | st2       | flat   | selected |     782 |      2.54 |       -1.72 |      6.08 |      341 |      -1.75 |       5.54 |  -1.31 |  -4.02 |    -1.48 |     858.18 |     -518.53 |            -3.04 |   0.08 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H25<=0, H26<=0 |
| ST       | s60       | run    | baseline |     708 |     -0.34 |       -4.28 |      5.63 |      302 |      -1.97 |       5.90 |  -2.37 |   0.07 |    -2.84 |     -46.35 |     -399.19 |            -7.31 |   0.01 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H25<=0         |
| ST       | st2       | run    | selected |     782 |      0.06 |       -4.20 |      6.09 |      341 |      -3.44 |       6.13 |  -3.36 |  -3.89 |    -1.65 |     348.44 |     -538.72 |            -3.74 |   0.04 | NOT-CONFIRMED | PRE CI<=0, HOLD<=0, H25<=0, H26<=0 |

## Never empty-handed: top 10 of all 936 PRE-screened cells by PRE t (n_pre >= 100), regardless of verdict (PRE only; HOLD exists only for the PREHOLD cells above)
| session   | stream          | bracket   | mode   |   n_pre |   mean_pre |   lo_pre |   mde_pre |   t_pre |   dwk_lock_pre |
|:----------|:----------------|:----------|:-------|--------:|-----------:|---------:|----------:|--------:|---------------:|
| ASIA      | EM              | t40s60    | flat   |     260 |       6.09 |     2.45 |      5.19 |    3.28 |         422.11 |
| ASIA      | EM              | s40       | flat   |     282 |       5.12 |     1.69 |      4.90 |    2.93 |         385.92 |
| ASIA      | HM              | t40s60    | flat   |     723 |       3.41 |     1.04 |      3.39 |    2.82 |         630.88 |
| ASIA      | EM              | s40       | run    |     282 |       5.62 |     1.67 |      5.64 |    2.79 |         433.50 |
| ASIA      | HM              | s60       | flat   |     610 |       3.90 |     0.99 |      4.15 |    2.63 |         613.62 |
| NY-AM     | X:SB_HM_st_sig0 | t60s40    | run    |     183 |       7.35 |     1.82 |      7.89 |    2.61 |         343.63 |
| ASIA      | EM              | t60s40    | flat   |     272 |       5.29 |     1.16 |      5.90 |    2.51 |         384.95 |
| ASIA      | EM              | t60s40    | run    |     272 |       6.36 |     1.28 |      7.26 |    2.45 |         472.25 |
| NY-AM     | X:SB_HM_st_sig0 | t60s40    | flat   |     183 |       6.91 |     1.31 |      7.99 |    2.42 |         322.23 |
| ASIA      | PE              | t60s40    | flat   |     700 |       3.03 |     0.49 |      3.63 |    2.33 |         452.91 |

## Bases and caveats
- MEASURED is ANALYTIC here: kernel on the 1-s path (identical to firmlib.sim_rrt on 2,187 trades) plus the D3SA replay's mean costs by lot class (stop excess, entry slip, P9 target correction). Matched-trade check against the D3SA replay: correlation 0.994, median absolute difference 0 (cids 1569 and 1616); target exits agree exactly, stops +0.08 / +0.27 pt, time exits +/-0.25 pt. The replay of the survivors (survivors_for_A.parquet) is the real test.
- Streams are session books (one open trade per stream, other sessions not traded), not the ledger sequences: that changes which signals are taken (the D3SA cell for ba2/HM_t75_s90 NY-AM shows +10.1 PRE vs +7.0 here at the same bracket because the ledger sequence is blocked by earlier all-day trades). Tier results therefore do not equal the ledger's.
- Stored basis is not available for these brackets (the stored rows have one bracket each), so the stored column of the survivors flow is replaced by the analytic MEASURED screen. Carried trades are scored at the MEASURED basis with the same stop excess for the tightened stop.
- ICT/X streams (IF_5m_tg_pd, IF_3m_tg_pd, IF_3m_tg_so, SB_HM_*) use the stored entry minute, entered at the next minute open (no look-ahead) as a MARKET entry; ICT limit-zone entries are not replayable from the stored rows (D3SA caveat 1). They are a labelled sensitivity.
- Best-of-F: 936 cells; nothing reaches 5.3e-5. Tiers are labels under the session rule (never killed for being one-session). The random-in-session placebo uses 100 draws per window per cell, same side, same bracket and management, one random minute in the same session and label day per original trade.
