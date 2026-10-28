# DS3_SDISC_2A - session-native re-search of the six big entry families (D3SD2A)

Written 2026-10-28 20:59Z. Research only; no live, execution-server or chart change; UNTOUCHED (after 2026-02-06) never read; no account ids. Prereg l2vast/ds3/prereg/SDISC_2A_prereg.md sha256 a6f9dc264a01670083a663b938d7abcdcb1c8e434e64684ff49d9499b3d655d5; PREHOLD autopilot/DS3_SDISC_2A_PREHOLD.md sha256 a714f336948e9a545b6ca6d20a4feacf1f262e309298a998982d7d203e3c1eb9 (hashed before HOLD/X were read; one HOLD and one X look per cell-session logged in out/sd2a/looks.jsonl; first run's MEASURED recipe had a stop-classification bug, fixed, same list, see DECISIONS.md). Code l2vast/ds3/code/sd2a/, outputs l2vast/ds3/out/sd2a/.

## Verdict lines (one per session)

- **ASIA: 4 SESSION-CANDIDATE cell-sessions on the analytic MEASURED basis (T-ENTRY 1, T-PB 2, T-TREND-TR1 1); best by HOLD: TB4C_range_24_range_80_ST5_SW38_T1 (T-ENTRY) +3.25 pts/trade MEASURED (MDE 10.9 pts), PRE +5.97, X(2023) -0.01.** None is a SESSION-PASS (best-of-F not cleared). Stored-only (dynamic exits, MEASURED n/a): E1A_RENKOC5_A3_r48. 
- **LONDON: 2 SESSION-CANDIDATE cell-sessions on the analytic MEASURED basis (T-ENTRY 1, T-TREND-TR1 1); best by HOLD: TR1B_reg1m_n60_t3_r0.5 (T-TREND-TR1) +6.54 pts/trade MEASURED (MDE 11.1 pts), PRE +3.51, X(2023) +2.71.** None is a SESSION-PASS (best-of-F not cleared). 
- **PREOPEN: 2 SESSION-CANDIDATE cell-sessions on the analytic MEASURED basis (T-ENTRY 1, T-TREND-TR1 1); best by HOLD: TB4B_tick_17_tick_1000_ST60_SW38_T3 (T-ENTRY) +12.17 pts/trade MEASURED (MDE 24.2 pts), PRE +11.37, X(2023) -2.06.** None is a SESSION-PASS (best-of-F not cleared). Stored-only (dynamic exits, MEASURED n/a): B5_T3_A. 
- **NY-AM: 6 SESSION-CANDIDATE cell-sessions on the analytic MEASURED basis (PRO 1, T-ENTRY 4, T-PB 1); best by HOLD: PRO3B_OPEN0930_DRV38_T1 (PRO) +7.90 pts/trade MEASURED (MDE 17.7 pts), PRE +8.45, X(2023) -3.20.** None is a SESSION-PASS (best-of-F not cleared). 
- **NY-PM: 4 SESSION-CANDIDATE cell-sessions on the analytic MEASURED basis (PRO 2, T-ENTRY 1, T-PB 1); best by HOLD: TB4B_tick_28_tick_2000_ST10_E20_1_T3 (T-ENTRY) +7.49 pts/trade MEASURED (MDE 12.1 pts), PRE +5.50, X(2023) -0.74.** None is a SESSION-PASS (best-of-F not cleared). 
- **CLOSE: no SESSION-CANDIDATE in these six families on the MEASURED basis.** Stored-only (dynamic exits, MEASURED n/a): B3_F01. 
- **NY: 3 SESSION-CANDIDATE cell-sessions on the analytic MEASURED basis (PRO 1, T-PB 1, T-TREND-TR1 1); best by HOLD: PRO3B_OPEN0930_DRV38_T1 (PRO) +7.90 pts/trade MEASURED (MDE 17.7 pts), PRE +8.45, X(2023) -3.20.** None is a SESSION-PASS (best-of-F not cleared). 

All alive counts are ANALYTIC MEASURED (entry +1 tick, mapped stop credit removed, stop slip 0.85 pt at 1 lot); the analytic is about 0.8 pt/trade optimistic against the one replay check available (PB7 ASIA), the replay of out/sd2a/survivors_for_A.parquet decides. No family produced a SESSION-PASS: no PRE p-value clears p x F_tot < 0.05 (F_tot=5,100 screened cell-sessions).

## Tier table (rows = tier, columns = family)

| tier                           |   Footprint |   PRO |   T-CHOP |   T-ENTRY |   T-PB |   T-TREND-TR1 |
|:-------------------------------|------------:|------:|---------:|----------:|-------:|--------------:|
| DEAD-IN-HOLD                   |          11 |    20 |        5 |        19 |     16 |            17 |
| MEASURED-FAIL                  |           1 |     1 |        0 |         1 |     10 |             3 |
| SESSION-CANDIDATE              |           0 |     4 |        0 |         8 |      5 |             4 |
| STORED-CANDIDATE(MEASURED n/a) |           0 |     0 |        2 |         1 |      0 |             0 |

## Alive by family x session (SESSION-CANDIDATE, MEASURED)

| session   |   PRO |   T-ENTRY |   T-PB |   T-TREND-TR1 |
|:----------|------:|----------:|-------:|--------------:|
| ASIA      |     0 |         1 |      2 |             1 |
| LONDON    |     0 |         1 |      0 |             1 |
| NY        |     1 |         0 |      1 |             1 |
| NY-AM     |     1 |         4 |      1 |             0 |
| NY-PM     |     2 |         1 |      1 |             0 |
| PREOPEN   |     0 |         1 |      0 |             1 |

## New session books found (alive cell-session whose pooled index verdict is DEAD or pooled PRE mean <= 0)

| session   |   alive |   new_books |
|:----------|--------:|------------:|
| ASIA      |       5 |           3 |
| CLOSE     |       1 |           1 |
| LONDON    |       2 |           1 |
| NY        |       3 |           2 |
| NY-AM     |       6 |           2 |
| NY-PM     |       4 |           3 |
| PREOPEN   |       3 |           3 |

Caveat: the PREHOLD overlap with SS2 is large; of the alive cell-sessions 15 of 24 were also looked at in SS2 (reread); the truly new HOLD looks are the NY pooled session cells, the MEASURED-selected winners and the pooled-winner comparators.

## Is the optimum session-specific? (all six families)

| fam         |   median |   min |   max |   count |
|:------------|---------:|------:|------:|--------:|
| Footprint   |    -0.08 | -0.26 |  0.11 |      10 |
| PRO         |    -0.06 | -0.29 |  0.02 |      10 |
| T-CHOP      |     0.16 | -0.14 |  0.45 |      10 |
| T-ENTRY     |    -0    | -0.29 |  0.36 |      10 |
| T-PB        |    -0.15 | -0.28 |  0.44 |      10 |
| T-TREND-TR1 |     0.1  | -0.16 |  0.36 |      10 |

Median cross-session Spearman correlation of PRE cell means is about zero in every family (CHOP and TR1 mildly positive): the cell that wins one session tells you nothing about the others, so the Asia-optimal parameter set is not the NY one. But the HOLD test of the session-tuned winner against one global (pooled) winner on the same session's trades is NOT significant in any family x session (all 95% CIs include zero, MDE 8k-36k $/wk): the session-specific optimum exists in the PRE data, its out-of-sample advantage over a global pick cannot be demonstrated at this sample size.

Tuning test summary: 26 comparisons, session-tuned minus pooled weekly $ positive in 13, CI excludes zero in 0.

## Survivors for the replay

out/sd2a/survivors_for_A.parquet: 37 cell-sessions (21 prereg members + calibration MEASURED-FAIL), 33,743 trade rows, 30,522 unique entries (uid from 20,000,000), 60/60 bracket (240/240 ticks), 1 lot class, flat 16:55 ET. Only the fixed 60/60 class can be replayed; CHOP, FP structure-stop cells, E1A renko and other dynamic exits are stored-basis only.

## Per family files

- autopilot/DS3_SDISC_2A_T-ENTRY.md
- autopilot/DS3_SDISC_2A_T-TREND-TR1.md
- autopilot/DS3_SDISC_2A_T-CHOP.md
- autopilot/DS3_SDISC_2A_Footprint.md
- autopilot/DS3_SDISC_2A_PRO.md
- autopilot/DS3_SDISC_2A_T-PB.md

## Limits
- Stored grids only; no family was regenerated with an extended parameter grid (not cheap/exact here; stated per family file).
- Placebo is the SS2 weekly sign-flip, not random-minute-in-session with the same bracket (needs a bar simulator per family).
- Exit-model gap: stored F1 rows carry ~50% non-bracket exits (trend/time) that the replay bracket+flat cannot reproduce; a replay MEASURED number is for the bracket+flat variant of the entries.
- HOLD rows of cell-sessions that SS2 had selected were read once already (disclosed in the prereg).