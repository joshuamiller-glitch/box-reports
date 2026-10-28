# DS3_SESSION2_A - live-latency direct re-run of the session-candidate cell-sessions (D3SA, T-SESSION-2 item A revised)
Status 2026-10-28 PLAN WRITTEN, replay NOT started (waiting for the governor restart). Prereg l2vast/ds3/prereg/SSA_prereg.md sha256 73f0a1cab5b210ace5f503abf3b69e061ea24ccfc5468eca3736baa65cc8e762 (DECISIONS.md, before any fill is read). Research only; UNTOUCHED never read.

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

## 5. Results
(pending the replay)
