# REPORT_L2_FOUND_A: L2-VAST foundation A (ingest + verify + book-state engine)
Status: COMPLETE 2026-10-20. NQ 45 months (2023-02..2026-10-11), ES 39 and RTY 39 months (2023-08..2026-10-11), all GLBX.MDP3 mbp-10 (v.0 front-month continuous), plus the NQ overnight 100ms pass (S29). No purchases, key via env only, no labels or P&L read.

## Deliverables
* outputs/l2vast/TABLES.md: every column, units, as-of semantics (bin END `ts`, state as of the last consistent F_LAST snapshot, no look-ahead; sparse bins).
* data/l2vast (symlink to /mnt/l2/l2vast)/tables/<SYM>/{100ms,1s,1min,sweeps,vpin,tape,events_L13,qa}/<YYYY-MM>.parquet; NQ also 100ms_night. Raw monthly files kept at data/l2vast/raw/<SYM>/<JOB>/ (557 GB).
* outputs/l2vast/VERIFY_A.md (per-month checks), READY.md (per-month list), INGEST_LOG.csv (timing, disk), PREREG_A_INGEST.md.
* Code: outputs/l2vast/l2v_kernel.py (numba book-state kernel), l2v_reduce.py (month reducer; `--night` for overnight), l2v_pipe.py (download+reduce orchestrator with memory/load gate), l2v_verify.py / l2v_verify_all.py, l2v_night.py, l2v_ready_sync.py.

## Tables
100ms (ET 09:30-16:15, lite columns), 1s and 1min (all hours, full: 10-level sizes, counts, imbalance 1/3/5/10 plain/level-decayed/time-decayed, depth slope and liquidity within N ticks, microprice, spread, trades with aggressor signed volume, large lots (3 thresholds), sweeps, add/cancel/modify by side and level band, OFI 1 and 5 levels, touch depletion by trades vs cancels, trade-driven touch clears and spread-heal refill time), `sweeps` (event-level refill, as-of ts_done), `vpin` (volume-clock buckets NQ 250/ES 750/RTY 100), `tape` (all trades with aggressor and pre-trade touch), `events_L13` (every A/C/M at levels 1-3 plus trades, ET 09:30-16:00, with post-event touch and level size/count, for queue-position fills), `qa`.

## Verification (VERIFY_A.md; full-month, every month)
* 1-min trade volume vs existing ohlcv-1m (same instrument_id and minute): total ratio 0.99998-1.00000 (NQ), 0.99999-1.0 (ES), 0.99996-1.0 (RTY); OHLC match >= 99.7% of minutes (>= 99.87% ES/RTY), mid-minus-close p99 <= 3 ticks. References exist for 35 NQ, 35 ES, 22 RTY months (the existing ohlcv-1m files do not cover the remaining months, so those are unverified against bars).
* Pair-engine ticks (data/ticks/*.npz, ms of ts_recv + price): >= 98.4% of ticks found in our tape (NQ, 6 days per month checked). Tape carries ~3x more records than the ticks (all trade records vs de-duplicated ticks).
* Book reconstruction (A/C records, levels 1-8, sampled on 3 large days per month): adds exact (NQ 1710 mismatches in 2.66e9 checks, ES 4/3.4e8, RTY 18/8.4e7); cancels 96-99% exact (1.0-3.8% mismatches: cancels coinciding with fills or cross-packet ordering).
* Anomalies: ts_recv < ts_event never; ts_event decreasing 5-13 times per month (clamped in binning); crossed consistent snapshots up to 34k/month NQ (~2e-4, auction/open transitions), locked ~70-90/month; trade outside prior book <= 103/month. All kept and counted in qa; filter with spread_t > 0.
* Not verified: expected per-day record counts (no independent reference); the volume ratio and the trading-day calendar in ohlcv-1m stand in for them.

## Data properties worth knowing
* Databento v.0 continuous: only the front contract's book is in the files (instrument_id switches at the roll dates in data/l2vast/meta/instr_map.json); second-month books would need a new purchase (not made).
* RTY prices are float32 (1e-4 error): compare in ticks.
* T records carry the pre-fill book; the fill appears in the following C record. State is read only at F_LAST records.

## Throughput, disk, resources
* Download ~20-35 MB/s per stream (2-3 streams); reduction is CPU-bound ~0.1-0.3 M records/s per process; a month takes 12-30 min per core depending on load (box load 25-70 shared with other agents). Wall time for 123 months about 17 h incl. restarts (OOM kills when other jobs held ~60 GB RAM; limited to 6-9 reducers by RESOURCE_POLICY.md, streaming writes, automatic retry).
* Disk after the user's DISK directive: tables 165 GB (NQ 81 + night incl., ES 54, RTY 30), raw 557 GB on /mnt/l2 (3.5 TB, 22% used). Per NQ month: events 1.0 GB, 100ms 0.29, 1s 0.16, tape 0.07, sweeps 0.04, 1min 0.004.
* Design decisions (DECISIONS.md): event store windowed only while disk was binding; after the move to /mnt/l2 widened to full RTH for all three instruments; 100ms for all three at RTH.

## Not done / caveats
* ES/RTY overnight 100ms (only on request; raw kept, `l2v_reduce.py RAW SYM --night`).
* Full-day (non-RTH) event store not built; trades are in `tape` at all hours.
* Second-month contract books (S54): need a new purchase, not available.
