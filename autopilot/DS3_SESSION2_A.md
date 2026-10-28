# DS3_SESSION2_A - live-latency direct re-run of the session-candidate cell-sessions (D3SA, T-SESSION-2 item A revised)
Status 2026-10-28 REPLAY DONE AND SCORED (plan below kept as written). Prereg l2vast/ds3/prereg/SSA_prereg.md sha256 73f0a1cab5b210ace5f503abf3b69e061ea24ccfc5468eca3736baa65cc8e762 (DECISIONS.md, before any fill is read). Research only; UNTOUCHED never read.

## 1. Scope (stated)
ALL 409 SESSION-CANDIDATE/SESSION-PASS cell-sessions (324 cells, 94 clusters), not only the 94 representatives: for the fixed-bracket families the replay entries are shared across cells (599,158 cell-session trades collapse to 347,170 unique entries), so all 348 PHASE-1 cell-sessions cost little more than the 54 reps. PHASE 2 (61 cell-sessions, 40 of the 94 reps: T-PB 20, H4 5, TB4 8, TR1 5, e1 3, G2 7, PRO 3, T-BRACKET 5, d4a 3, xte/xtr1 2) have dynamic exits (trail/flip/BE) that the stored rows cannot reduce to stop/target ticks; they are scored on the families' existing direct replays (basis label MEASURED-PROXY) or listed NOT-RERUNNABLE with the reason. Nothing is dropped.
The 27 pair legs and 5 carriers are re-scored from these series (a leg in PHASE 2 uses its proxy series).

## 2. Replay design
- Span: label days 2023-04-03..2026-02-06 (35 months 2023-04..2026-02; the 2023 stored-fill rows start 2023-02 but the X span starts 2023-04; raw NQ mbp-10 covers 2023-02..2026-10, so coverage does not limit).
- Inputs: out/ssa/entries.parquet (ssa_prep.py): per unique entry t_ent (stored entry instant, UTC ns), side, stop/target ticks (rows' bracket/stop/target; IC/SF tgt_d), forced-flat instant, lot class. BA-family rows use the firm_replay.prep timing (et_in - 60 s; exit instant + 300 s unless TimeBlock); IC/SF use the stored entry second and the xi-minute exit instant + 360 s. Session window filter on the ledger entry ET.
- Worker (ssa_direct.py, structure of rvq_direct/open_direct/ba_replay): one worker per month; per label day one pass over the 24-h book (p9_replay.fast_day_iter), two run_program calls (V0+V1 share a control set; VC separate): THREE fill bases in one pass. Output R_YYYY-MM.parquet; claim (O_EXCL) and done markers in /mnt/l2/l2vast/ds3_ssa; orchestrator holds a lock and waits for >= 32 GB MemAvailable before each launch (SSA_MEM_NEED), 90 s between launches, no retries, no kills, SIGSTOP-friendly (no state in the process other than the day loop; a stopped worker resumes).
- Fills: MEASURED V0 = market +1 tick (book walked at the cell's lot class 1/2/5/10), stop-market walking the 10 displayed levels (DN_STOPFILL method), target at touch + P9 year x Target correction (applied in scoring); V1 = same with +1 s; CONSERVATIVE VC = +3 s, +1 tick, stop + 2 ticks, 1-tick trade-through target. Costs $4.84 RT/contract.
- Not replayed (stated): own-order market impact; queue position of resting orders only enters through the 'back' model on stops/targets that rest (targets under VC); the entries themselves are markets, so IC/SF limit-at-zone fills of the source are replaced by a market +1 tick at the stored entry instant (the live-latency assumption).
- Known limits written in advance: the P9 target correction is calibrated on 60-pt brackets and is applied as defined even to the 4-8-pt-stop IC/SF cells (sensitivity MEAS-nocorr printed); the session-book lock is the session book's own, not the live stack's.

## 3. Cost estimate
347,170 unique entries / 35 months = 4.4k-15.7k per month (median 10.1k), about 500 per label day, two engine calls per day. Precedent (ba_replay, 150 cells, same machinery): 17-23 min per month per worker. Estimate 25-40 min per worker-month; 35 months at <= 12 concurrent workers = 3 waves = about 1.5-2.5 h wall-clock after the governor admits them. Memory per worker: one 24-h day of mbp-10 (about the BA workers'), the launch gate is 32 GB available (the user's rule), cap 12 workers. Output about 1M rows (about 100 MB). Scoring (CPU, no L2): minutes.
Trades x months: 347,170 entries x 3 bases over 35 months. Pair/carrier re-score and C, D: CPU only.

## 4. Governor
replay_governor.py: backup replay_governor.py.bak_pre_ssa_20261028, then 'ssa_direct.py' appended to PRIO_ALLOW (logged in DECISIONS.md). The governor is a running process; PRIO_ALLOW is read at start, so main must restart it (SIGTERM, restart, SIGCONT) — requested by message. No worker is launched until main confirms.

## 5. Results (replay done 2026-10-28 20:47Z; scoring rules fixed in the prereg and addendum)
Status: replay complete (pass 1: 35 months, 2024-06 re-run once after a memguard kill; pass 2: 22 months for the PB7/TB4 entries). The D6 legs are in DS3_SESSION2_A_D6.md (per-leg three-basis tables, pairs, sizing advice, Sim spec); item C in DS3_SESSION2_C.md; the D6 line in DS3_SESSION2_D_D6LINE.md and DS3_SESSION2_D.md. Per cell-session numbers for all 351 replayed cell-sessions (stored vs measured vs conservative: pts/trade, $/wk with and without lock, MDE, PRE/HOLD/halves/X/by year, break-even) are in out/ssa/cs_scores.csv.

**Verdict line.** Of the 94 cluster representatives 56 were replayable and 3 survive live latency on MEASURED (5 at 1-s delay); 38 have dynamic exits and are not replayed here. Of the 27 passing pairs 19 are complete and none has a positive measured HOLD add (the other 8 contain a non-replayed partner leg plus an IC/CRT leg that fails alone). The IC/SF family (99 + 12 cell-sessions) is dead on the measured basis (5 and 0 pass), because the mapped +4 pt stop credit in the stored rows does not exist for a stop-market.
- 94 cluster representatives (best PRE-t cell of each cluster50): 56 replayed on the three bases, 38 not replayed (dynamic exits / no fixed bracket). MEASURED SESSION-CANDIDATE/PASS (V0): **3 of 56** replayed reps; at 1-s delay 5; with CONS stress yes: 3.
- clusters with ANY replayed cell that passes MEASURED: 9 of 57 clusters that have a replayed cell (the 94 clusters in total; the rest have no replayable cell).
- all replayed cell-sessions: 351; MEASURED candidates 146; at 1-s delay 149; CONS stress yes 144; harsh stress yes 131.

| family                  |   cell_sessions |   measured_candidate |   stress_yes |
|:------------------------|----------------:|---------------------:|-------------:|
| BA bracket-assign rows  |              21 |                    6 |           18 |
| BA bracket-assign rows2 |              79 |                   33 |           61 |
| BA bracket-assign rows3 |             119 |                   94 |          116 |
| G3 fam                  |               3 |                    1 |            2 |
| ICT-IC (IC blocks)      |              99 |                    5 |            8 |
| ICT-SF (silver/fvg SF)  |              12 |                    0 |            0 |
| SB (silver-bullet SB)   |               5 |                    3 |            4 |
| T-ENTRY pb4 (TB4)       |               2 |                    0 |            1 |
| T-PB (pullback/PBX TP)  |               1 |                    0 |            1 |
| TSO EM                  |               1 |                    0 |            0 |
| TSO HM10                |               5 |                    3 |            5 |
| TSO SM                  |               1 |                    0 |            1 |
| TSO ST10                |               3 |                    1 |            2 |

Best 5 clusters (best measured cell per cluster, by MEASURED HOLD $/wk after the session-book lock; $ at the lot class, session book alone):

| cell                  | sess   | family                  |   S_hold_mean |   M0_hold_mean |   M0_hold_mde |   M0_pre_mean |   M0_x_mean |   M0_hold_dwk |   M0_hold_dwk_lock |   C_hold_mean | survives_stress   |
|:----------------------|:-------|:------------------------|--------------:|---------------:|--------------:|--------------:|------------:|--------------:|-------------------:|--------------:|:------------------|
| IF_5m_tg_pd           | LONDON | ICT-IC (IC blocks)      |          8.72 |           2.55 |          7.83 |          1.96 |        0.41 |       1963.32 |            1697.68 |          3.18 | yes               |
| ba/A_t40_s75          | NY-AM  | BA bracket-assign rows  |          6.17 |           2.79 |          5.29 |          0.66 |        0.41 |       1369.14 |            1568.66 |          4.81 | yes               |
| ba2/HM_t120_sst       | NY-AM  | BA bracket-assign rows2 |         14.35 |          10.45 |         15.32 |          6.32 |        1.19 |       1676.42 |            1530.84 |         12.06 | yes               |
| ba/SS_HM_ASIA_t75_s60 | ASIA   | BA bracket-assign rows  |          7.65 |           4.96 |          8.52 |          2.96 |       -3.04 |        834.59 |             831.05 |          7.14 | yes               |
| ba2/KB_t90_s90        | NY-AM  | BA bracket-assign rows2 |          3.92 |           1.37 |         13.8  |          7.46 |        8.48 |        216.38 |             402.99 |          1.99 | yes               |

Tier note: 'NOT-MEASURED-CANDIDATE' in cs_scores.csv means a stored SESSION-CANDIDATE that fails a HOLD gate on MEASURED; nothing is dropped from the ledger. 'survives stress' = the three HOLD gates on the preregistered CONSERVATIVE basis; 'survives_stress_harsh' adds the P9 target correction (disclosed extra column).
