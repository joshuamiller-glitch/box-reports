# DS3_SESSION2_B_pool - B6: the 31,097-series library pool, which cells were re-run with an entry clock (D3SB3)

Written 2026-10-28. Research only. Pool = l2vast/ds3/out/pool.parquet (31,098 rows incl. 10 live-book rows). Rule applied: re-run a family only if the generating rule is on disk AND the stored series can be reproduced; otherwise listed as not re-runnable. Never guessed.

## 1. Re-run and scored (13,808 pool series = 44%; 13,864 cells re-run, 56 of which are not in the pool)
| pool family | pool series | cells re-run | generating code | reproduction | F | F_eff | tiers after one HOLD look | report |
|---|---|---|---|---|---|---|---|---|
| C5M1_ES + C5M1_NQ | 2,650 | 2,928 | code/census/night_ins/ap_c5_m1_core.py (numba, nt8sim) | 2,928/2,928: daily $ identical to real_<sym>.pkl up to 2026-10-13 and 2013-22 trade count | 20,496 | 1,750 | 0 PASS, 26 CANDIDATE (23 cells, 17 clusters) | DS3_SESSION2_B_pool_c5m1.md |
| C7P1_{6E,6J,CL,GC,ZB,ZN} | 6,235 | 6,720 | ap_c7_p1_core.py | 6,720/6,720 | 47,040 | 4,914 | 0 PASS, 17 CANDIDATE (13 clusters) | DS3_SESSION2_B_pool_c7p1.md |
| C10S1_{NQ,ES,GC,CL,ZN,6E,6J} | 2,992 | 4,200 | ap_c10_s1_core.py | 4,200/4,200 | 28,420 | 2,261 | 0 PASS, 36 CANDIDATE (29 cells, 13 clusters) | DS3_SESSION2_B_pool_c10s1.md |
| V5P2 (NQ) | 1,931 | 2,016 (sampled grid) | v5_p2_core.py | 2,016/2,016 (days <= 2026-10-12) | 14,112 | 9,422 | 0 PASS, 49 CANDIDATE (43 cells, 42 clusters) | DS3_SESSION2_B_pool_v5p2.md |

Reproduction detail: the stored real_*.pkl series were produced before the 2026-10-19 end-of-day fix and before the series extension to 2026-10-23, so the re-run uses the core's own ENDI_LEGACY switch and is compared only on days up to 2026-10-13 (the scoring window ends 2026-02-06). Every cell matched (rtol 1e-4); out/sb3/pool_<mod>/repro_*.json. Trades carry entry bar index, ET entry minute (bar start), net $ at the pool's own contract count (C5/V5: 8 NQ/ES contracts; C7/C10: 1 contract), basis MAPPED (NT8sim fills), side not stored by the trade record (0; clustering by entry minute only). Instruments other than NQ are scored with the NQ session map (ET clock), as the directive prescribes; they cannot go to the NQ replay.

## 2. Reconstructible in principle, NOT re-run in this pass (state of evidence)
| pool family (series) | what exists | why not re-run |
|---|---|---|
| T3S1_* (5,639+) | outputs/t3/s1/S1_series_axis.pkl, code night_ins/t3_s1_score.py | a RE-SCORING library: daily series gathered from B10 harness captures, G/BB 'alone' books and B10 books files (many tracks); no trade table or entry clock at this level; each source track would have to be re-run separately |
| ICT (1,082 + 280) | ap_ict_core.py, ap_ict_grid.py | cell grid reconstructible, but 163 IC/SF cells already have rows in the ledger and the remainder needs the ICT level builders (ap_ict_levels.py) to be run end to end; not cheap, not done |
| WT432 (382) | ap_wt_core.py, ap_wt2_alt.py | multi-stage account/lock accounting (acct3) around the signals; stored series is post-accounting; not done |
| B1/B4/B7/B10/B11/FU3/B6ALL + legacy variants (~3,900) | ap_b_pipe*.py, nt8sim cores, real_<sym>.pkl | only the selected/scored cells were saved to the pool; per-instrument grids; reconstructible by the same pattern as C7P1 but not done in this pass |
| T3S3 (218), T4D/T4B/T4E (280), FV14/16/17/19, SW*, Q*, BM*, C1F1, remaining one-off tracks (~7,000, 330+ families of 1-90 series) | one script per track (hundreds under night_ins) | no common runner; each needs its own study; listed as not re-runnable here |
Totals: re-run 13,808 pool series; listed as not re-runnable / not done 17,290 (including the 10 live-book rows, which are the DS2 components already in the ledger).

## 3. Where the alive cells go
Survivors from these four families that are NQ fixed-bracket ('brk') cells were turned into replay entries (out/sb3/survivors_for_A.parquet); dynamic-exit cells (opp / trail / time) and non-NQ cells are listed in out/sb3/survivors_not_replayable.csv with the reason.
