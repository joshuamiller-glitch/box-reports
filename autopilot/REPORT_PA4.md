# REPORT PA4 (task PA-L2) - 2026-10-16

## (a) Databento batch job status (read-only list_jobs/list_files; no purchases, no new jobs; key used from env only)
| job | what | state |
|---|---|---|
| GLBX-20261013-Y3PCQ4MKV3 | NQ mbp-10 (A5, $2,024.78) | processing (still; ~3 days since submit) |
| GLBX-20261015-XDLHWMFQ3R | RTY mbp-10 ($547.68) | processing |
| GLBX-20261015-9K3KUU8MSD | ES mbp-10 ($1,303.05) | DONE: 42 files, 181.3 GB total (monthly 2023-08..2026-10-11) |

Download of an already-paid batch job carries no extra charge (Databento bills at job submission). Disk: 186 GB free vs 181 GB for all of ES -> NOT downloaded in full.
Downloaded 2 months only (6.3 GB): data/databento/mbp10/ES/glbx-mdp3-20260901-20260930.mbp-10.dbn.zst, ...20261001-20261011.mbp-10.dbn.zst, manifest.json, metadata.json.
Remaining ES months: download on demand (c.batch.download(job_id=..., filename_to_download=...)); about 4.4 GB/month average; free ~180 GB after this -> download in <=2-3 month batches or per-month process-then-delete.
Existing watchers: outputs/a5/L2WATCH.* will fire on NQ (marker outputs/a5/L2-DONE). RTY/ES not watched by it.
Format: dbn mbp-10 per record 92 B; prices int64 1e-9; trade side flag measured 'A' = SELLER-initiated (prints at bid), 'B' = buyer-initiated (100% agreement with quote rule, n=127,087 ES trades): T records leave the book unchanged and the executed size appears in the *following* 'C' record at the same price (queue model handles this).

## (b) Scaffolding (all in outputs/autopilot/, prefix ap_pa4_*; outputs in outputs/autopilot/pa4/)
- ap_pa4_loader.py: load_dbn (time-window streaming), load_csv, synthetic_events, trade_sign (quote rule / side flag), to_seconds + regularise (per-second: mid, spread_t, imb1/5/10, dep_b5/a5/dep5, micro, wmid, buy/sell/signed vol, trade/add/cancel counts, cancel vol by side), mid_bars (A4 mid OHLC). CLI prints a describe() and writes parquet.
- ap_pa4_queue.py: numba queue-position simulator. limit(): queue ahead = displayed size at arrival, trades at price deplete queue, trades through fill, cancels ahead = cancel_frac x true cancels (fill-removal C records after trades excluded), marketable limits take liquidity, latency, timeout, optional market fallback. stop(): trigger on first trade print, stop-market walks the book, stop-limit (offset ticks) with queue and fallback. Batch APIs for order tables.
- ap_pa4_build.py: single streaming pass over a monthly dbn -> per-second parquet (+ per-window event npz for the queue sim). Throughput ~270k rec/s/process => ~1 h per ES month (run months in parallel, <=4 processes).
- ap_pa4_items.py: item15, item97, item98, a4_mid_bars/a4_supertrend_compare, e_filters (E38/39/40/44/45/47), feats_at (no look-ahead, lag 1 s), with PRE-REGISTERED grids (GRID15/97/98) and a --selftest. Trade-level evaluators: they output per-trade modified exits / deltas; the pair gates must still be run through the clean-process pair harness (not wired here: needs live pair trade list with exit_reason, stop_px, target_px).
- ap_pa4_test_queue.py (log pa4/ap_pa4_test_queue.log): toy book with hand-computed fills (partial/complete, cancel absorption, marketable, stop-market/limit), monotonicity of fill rate in cancel_frac on synthetic and on real ES, 1-hour real ES sample (2026-10-01 13:30-14:30 UTC, 3.1M events).
- pa4/PREREG_PA4_L2.md: pre-registration text for items 15, 97, 98, A4 and E38-47 (grids final; 41 uses queue model; 42/43/46 stubs).
- pa4/ap_pa4_es_sample_sec.parquet: 30 min of real per-second ES features.

Test results: side convention agreement 1.0; toy asserts pass; ES real sample, buy limit in 30 s: join best bid fill rate 94.5% / 94.8% / 95.8% at cancel_frac 0/0.5/1 (median queue ahead 20 lots), improve one tick 99.5% (these are open-hour numbers, fill != profitable: adverse selection must be measured via post-fill mid drift on the pair data); 2-tick-below sell stops: stop-market mean slippage 0.237 tick, stop-limit(2t)+fallback 0.227 tick (ES RTH open, not thin hours). Item 15 null calibration on synthetic books: mean d_pts ~0 across 8 seeds. These are plumbing checks, NOT research results.

## How to launch each item in one command (once pair trades table T.parquet exists)
Preparation per month (1 command): `python3 -I outputs/autopilot/ap_pa4_build.py <month.dbn.zst> ES outputs/autopilot/pa4/ES_2026-09_sec.parquet [--windows W.parquet --ev-dir outputs/autopilot/pa4/ev_ES_2026-09]`
- 15:  `python3 -I outputs/autopilot/ap_pa4_items.py --item 15 --trades T.parquet --sec SEC.parquet --out outputs/autopilot/pa4/ap_pa4_i15.json`
- 97:  `... --item 97 --trades T.parquet --sec SEC.parquet --events EV.npz --out ...`  (events cover [entry, exit+30 s] of target trades)
- 98:  `... --item 98 --trades T.parquet --sec SEC.parquet --events EV.npz --out ...`  (events cover [stop_since, exit+60 s] of stop trades in thin hours)
- A4:  `python3 -I ap_pa4_loader.py <nq file> --sym NQ --out nq_sec.parquet` then ap_pa4_items.a4_mid_bars / a4_supertrend_compare
- E38/39/40/44/45/47: `... --item 38 --trades T.parquet --sec SEC.parquet --out ...` (feature table at entries; add the filter in the pair harness)
- Self-test of any item: `python3 -I ap_pa4_items.py --item 15 --selftest`
Caveats: the NQ file is the decisive one (not landed); E41/42/43/46 are spec-only; the cancel_frac assumption is the biggest model risk (report 0 and 1 bounds); event windows from sequential dbn scanning cost ~1 h per month; no L2 for pre-2023-08.

DONE PA4
