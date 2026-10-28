# DS3_SDISC_1 - neighbourhoods of the ICT seeds per session (D3SD1, item 1), 2026-10-28

Per-family files DS3_SDISC_1_<IF|FV|OB|BOS|SWEEP|CRT|SB>.md hold the per-session top-10 tables. Prereg l2vast/ds3/prereg/SD1_prereg.md sha256 c17787358ff27ceea3087579bfca06e1b10423641a5b8959f20786dfec7df817; PREHOLD sha256 40cf2203d428793d9e640b92c1f1766d8db2a585e314248ddc0a56fffb5a6521 (autopilot/DS3_SDISC_1_PREHOLD.md). Screen: 826 builds x 5 confs (IC families) x 6 sessions (+8 clock windows for SB) x 6 exits x 2 flat rules = 182,986 cell-sessions with trades, 172,976 with n_PRE>=100 (F). PREHOLD list 415 cells (top 10 per family-session by MEASURED effect t, flat duplicates collapsed, max 2 per build, plus the 3 seeds); ONE HOLD and ONE X look.

## Verdict lines (tier on MEASURED, analytic; no replay yet)
- **22 of 415 listed cells are SESSION-CANDIDATE on the MEASURED basis (0 SESSION-PASS: best-of-F cleared by none); 99 on the STORED basis (2 PASS), so the stored basis flatters the list about 4x.** Every MEASURED candidate is a long-stop (>=20 pt) bracket cell (mostly 60/60 run-to-bracket on limit entries or 20/20 on market entries); NO structural-pair short-stop IC cell survives MEASURED except 2 OB/sweep ones (see tables). The three seeds: IF ASIA 30s eb sz8 sg10 none STR/S: PRE stored 2.13 / MEAS -0.84, HOLD MEAS -2.12, X MEAS -1.63 -> DEAD-IN-HOLD; IF ASIA 30s eb sz8 sg10 none STR/R: PRE stored 2.20 / MEAS -0.96, HOLD MEAS -2.08, X MEAS -1.42 -> DEAD-IN-HOLD; CRT LONDON H15/1m close-ib 1m STR/S: PRE stored 2.27 / MEAS -0.39, HOLD MEAS -3.04, X MEAS -1.91 -> DEAD-IN-HOLD; CRT LONDON H15/1m close-ib 1m STR/R: PRE stored 2.21 / MEAS -0.51, HOLD MEAS -3.06, X MEAS -1.98 -> DEAD-IN-HOLD; IF NYAM 15s eb sz8 sg10 none STR/S: PRE stored 2.53 / MEAS -0.42, HOLD MEAS -1.36, X MEAS -1.17 -> DEAD-IN-HOLD; IF NYAM 15s eb sz8 sg10 none STR/R: PRE stored 2.65 / MEAS -0.46, HOLD MEAS -1.61, X MEAS -1.24 -> DEAD-IN-HOLD.
- **THE 2023 SPAN (X, 2023-04..2024-01), reported prominently:** of the 22 MEASURED candidates, X MEASURED mean is > 0 in 5; ASIA/LONDON candidates are negative in 2023 (2m ea imp2.0 brk0.5 mom B20/20/S -1.4, 2m box-dev break-retest B30/30/R -1.3, T500 L3 resp-b mkt B60/60/S 0.4, 15s box-prior sweep-retest STR/S -1.6, 15s eb sz8 sg10 deliv B60/60/R -1.0). Same pattern as D3SS2: the ICT edge is a 2024+ phenomenon; X is a label, not a gate.
- **ASIA**: 3 new session-book candidates (MEASURED); best by HOLD: IF [limit] 15s eb sz8 sg10 deliv B60/60/R MEAS PRE 6.41 HOLD 3.66 X -0.99, $/wk@1k-risk HOLD 859; BOS [market] 2m box-dev break-retest B30/30/R MEAS PRE 2.58 HOLD 1.40 X -1.34, $/wk@1k-risk HOLD 414; SWEEP [market] 15s box-prior sweep-retest STR/S MEAS PRE 2.63 HOLD 0.31 X -1.62, $/wk@1k-risk HOLD 1869.
- **LONDON**: 2 new session-book candidates (MEASURED); best by HOLD: BOS [market] T500 L3 resp-b mkt B60/60/S MEAS PRE 6.93 HOLD 2.00 X 0.38, $/wk@1k-risk HOLD 58; OB [limit] 2m ea imp2.0 brk0.5 mom B20/20/S MEAS PRE 3.18 HOLD 1.63 X -1.42, $/wk@1k-risk HOLD 112.
- **PRE**: 1 new session-book candidates (MEASURED); best by HOLD: CRT [market] H30/T500 close-ib T500 B40/40/R MEAS PRE 6.69 HOLD 4.60 X -5.56, $/wk@1k-risk HOLD 236.
- **NYAM**: 5 new session-book candidates (MEASURED); best by HOLD: BOS [market] 2m box-dev break-retest B60/60/R MEAS PRE 4.35 HOLD 3.57 X -8.62, $/wk@1k-risk HOLD 281; OB [limit] 5s eb imp2.0 brk0.5 mom B60/60/R MEAS PRE 4.06 HOLD 2.27 X 0.04, $/wk@1k-risk HOLD 511; BOS [market] 2m box-N12 break-retest B60/60/R MEAS PRE 6.10 HOLD 1.32 X -4.08, $/wk@1k-risk HOLD 144.
- **NYPM**: 9 new session-book candidates (MEASURED); best by HOLD: OB [limit] 30s eb imp1.0 brk1.0 none B60/60/R MEAS PRE 2.42 HOLD 7.55 X -5.38, $/wk@1k-risk HOLD 1674; CRT [market] H30/T500 close-ib T500 B50/50/R MEAS PRE 4.78 HOLD 5.46 X -2.66, $/wk@1k-risk HOLD 720; IF [limit] 15s eb sz16 sg10 none B60/60/R MEAS PRE 2.86 HOLD 4.04 X 0.24, $/wk@1k-risk HOLD 1062.
- **CLOSE**: 2 new session-book candidates (MEASURED); best by HOLD: OB [limit] T500 eb imp1.5 brk0.5 pd B20/20/R MEAS PRE 3.76 HOLD 0.98 X -1.67, $/wk@1k-risk HOLD 58; OB [limit] 15s eb imp1.5 brk0.5 mom B20/20/R MEAS PRE 1.07 HOLD 0.41 X -0.60, $/wk@1k-risk HOLD 156.

## Which entry type and bar size each session likes (all 172976 screened cells; rate = share with PRE MEASURED effect CI>0, chance level 2.5%; limit cells carry no entry cost on MEASURED, a proxy)

**entry type**

| parent   |   limit |   market |   stop |
|:---------|--------:|---------:|-------:|
| ASIA     |   0.015 |    0.009 |  0.008 |
| LONDON   |   0.011 |    0.01  |  0.003 |
| PRE      |   0.042 |    0.018 |  0.005 |
| NYAM     |   0.048 |    0.019 |  0.01  |
| NYPM     |   0.022 |    0.016 |  0.006 |
| CLOSE    |   0.033 |    0.008 |  0.002 |

**bar size**

| parent   |   T500 |   30s |   15s |   10s |    5s |    1m |    2m |
|:---------|-------:|------:|------:|------:|------:|------:|------:|
| ASIA     |  0.025 | 0.009 | 0.009 | 0.012 | 0.002 | 0.009 | 0.022 |
| LONDON   |  0.017 | 0.005 | 0.001 | 0.002 | 0.002 | 0.005 | 0.034 |
| PRE      |  0.062 | 0.034 | 0.016 | 0.025 | 0.018 | 0.033 | 0.013 |
| NYAM     |  0.033 | 0.02  | 0.022 | 0.018 | 0.023 | 0.037 | 0.072 |
| NYPM     |  0.015 | 0.006 | 0.007 | 0.005 | 0.005 | 0.041 | 0.044 |
| CLOSE    |  0.016 | 0.018 | 0.03  | 0.015 | 0.016 | 0.023 | 0.011 |

**family**

| parent   |   BOS |   CRT |    FV |    IF |    OB |      SB |   SWEEP |
|:---------|------:|------:|------:|------:|------:|--------:|--------:|
| ASIA     | 0.012 | 0.001 | 0.017 | 0.012 | 0.006 |   0.007 |   0.002 |
| LONDON   | 0.005 | 0.01  | 0.014 | 0.004 | 0.014 |   0     |   0.002 |
| PRE      | 0.002 | 0.091 | 0.025 | 0.032 | 0.019 |   0.022 |   0.005 |
| NYAM     | 0.02  | 0.008 | 0.035 | 0.024 | 0.06  |   0.013 |   0.005 |
| NYPM     | 0.004 | 0.026 | 0.028 | 0.008 | 0.008 |   0.013 |   0.036 |
| CLOSE    | 0.008 | 0.021 | 0.016 | 0.016 | 0.03  | nan     |   0.029 |

**exit pair**

| parent   |   B20/20 |   B30/30 |   B40/40 |   B50/50 |   B60/60 |   STR |
|:---------|---------:|---------:|---------:|---------:|---------:|------:|
| ASIA     |    0.004 |    0.009 |    0.011 |    0.018 |    0.026 | 0.003 |
| LONDON   |    0.016 |    0.008 |    0.011 |    0.008 |    0.01  | 0.001 |
| PRE      |    0.048 |    0.036 |    0.027 |    0.022 |    0.017 | 0.016 |
| NYAM     |    0.044 |    0.036 |    0.021 |    0.035 |    0.041 | 0.012 |
| NYPM     |    0.021 |    0.013 |    0.019 |    0.019 |    0.026 | 0.003 |
| CLOSE    |    0.061 |    0.033 |    0.009 |    0.003 |    0.004 | 0.001 |

**flat S=session end / R=run**

| parent   |     R |     S |
|:---------|------:|------:|
| ASIA     | 0.015 | 0.008 |
| LONDON   | 0.006 | 0.012 |
| PRE      | 0.028 | 0.027 |
| NYAM     | 0.037 | 0.026 |
| NYPM     | 0.019 | 0.015 |
| CLOSE    | 0.019 | 0.019 |

## Caveats
- MEASURED here is analytic from the 1-s path trade rows (stop slip from DS3_DN_STOPFILL by lots/year, no mapped stop credit, P9 target correction only for >=40 pt targets). Limit-entry cells fill on trade-through only and carry no entry slip on MEASURED; the D3SA replay treats entries as market +1 tick, so limit survivors need their own replay (entry kind is a column of survivors_for_A.parquet). CONSERVATIVE = stress label.
- The ledger seeds reproduce (IF 30s eb ASIA n 3164 vs 3116, tpw 42.2 vs 41.5) but their edge vs random-in-session on STORED is small and negative on MEASURED: the stored edge is the mapped stop credit that the same-distance random entry also earns.
- 172,976 cell-sessions over heavily overlapping entries: the F-label is conservative against the nominal count; best-of-F cleared none. Sessions are books of their own (no cross-session carry); sequencing within a session book.
- CLOSE (15:00-16:54) entries are blocked by the live DS2 rules; any CLOSE finding needs a block change.
- STR-cell placebo is a single-exit approximation of the family exits (scale-out structures are collapsed for the placebo only).

Files: out/sd1/stage1_tf*.parquet, stage1_all_n100.parquet, stage2_tiers.parquet/.csv, survivors_cells.csv, survivors_for_A.parquet (103 survivor cells, 238165 trade rows; columns t_ent st tt t_fl lc as out/ssa/entries.parquet + cell, session, window, ekind).
