# REPORT K4-LIVE / K4-VPS (2026-10-19)

## Built (all in outputs/k4/)
* `k4_writer.py` (box): features, frozen models, 26-cell rules, live fetch, atomic writer (.tmp then rename), ET-clock daemon, post-close history update, late-shadow file. README.md states schedule, hard-input rule, freeze date, retrain policy.
* `vps_pkg/` -> `k4_vps.zip` (k4_writer.py pure Python deps pandas/numpy/requests, k4_model.json with trees+ridge, index_history.csv seed 2025-07-01..2026-10-16, README.md). `VPS_MATCH_20D.md` = proof table.
* Feature code equals the research code exactly (k4_validate.py: 0 mismatches incl. SKEW/VIX9D/VIX6M features); walk-forward p equals research ml_preds exactly in 2024-2026 quarters (tiny diffs 2022-23).

## Scheduler (box, cross-check only)
`systemctl --user` unavailable (no bus), cron/at absent. Installed system unit `k4-writer.service` (User=ubuntu, Restart=always, enabled at boot), ET-clock daemon: run 16:16:05 ET (write >= 16:16:30, give up 16:19:30), late shadow 16:32, history update 17:30. Kill test: restarted by systemd. Next fire at time of writing: 2026-10-19 16:16:05 EDT (20:16:05 UTC), then 16:32 shadow, 17:30 update, then Tue 10-20.

## Data-source verdict per hard input (tested from this box)
* ES/NQ/RTY/YM 16:15-bar (price at 16:16:00): no live source here. Databento key is not in the service env; historical API range ends ~8 h behind real time (GLBX end 08:40Z at 16:40Z); live entitlement unverified and not tested (no spend; only the free metadata call was made). Free Yahoo chart API works but is ~9-10 min delayed (futures). Verdict: CANNOT be sourced by 16:16:30.
* VIX/VIX3M/VVIX: CBOE delayed JSON works, ~15-16 min delayed (last trade 16:00 at 16:16); CBOE daily-history CSV works (publishes after the close). SKEW is end-of-day only. Verdict: CANNOT be sourced by 16:16:30.
* COT (CFTC fut_fin zip) works; soft.
Consequence: the box writer will log NO FILE every day (reason with feed lag), by design. The 16:32 shadow run (futures catch up ~16:26, CBOE ~16:31) writes `shadow/K4_YYYYMMDD_LATE_SHADOW.csv` for forward tracking only (not a signal file). Real-time feeds are needed: NT8 index bars (K4-VPS path) and a same-day VIX/VIX3M/VVIX series.

## Findings / unvalidated items
1. TIMING DISCREPANCY: the research price "16:16 close" is the close of the bar OPENING 16:16 ET (Databento ts_event = bar open), i.e. the price at 16:17:00; ORDERS entry_price equals it exactly. The pack says the decision bar ENDS 16:16:00 and the file is written 16:16:30, when that price does not exist yet. Deployed models use the 16:16:00 price (bar opening 16:15) and are trained on it. The pack's lag-cost study measured 16:16 close -> 16:17:00.5 print under a different convention; its immateriality finding is not re-verified.
2. SENSITIVITY: signals are threshold-fragile. Cell-index decisions agree 95% between model variants but LONG overlap is only 38-58%.
3. Cells: 18/26 computed; 8 (R9,R10,R14,RX1,RX2,RX3,RX8,RX11 = 43% of tilt weight) are dip/COT/multi-day-exit books not expressible at 16:16:30 as 1-day longs: written FLAT. RX7/RX7P shorts omitted; R4 (2-day hold) is traded as 1-day by the file contract. So the live book is not the 26-cell book the bands describe (size and band mismatch).
4. UNTOUCHED: no pair UNTOUCHED file read. But the pack refit date 2026-07-31 lies after the pair UNTOUCHED start (2026-02-06); fit follows the pack (labels < 2026-08-01), not a clean-span freeze.
5. ORDERS qty uses fixed NQ-eq ratios (ES 2.60, RTY 4.51, YM 3.57); SIGNAL_FILE says recompute daily from ADR: daily values differ up to 37% from ORDERS on single rows (fixed ratios match ORDERS within 0.2%).
6. Unhandled: December roll (Yahoo/NT8 raw prices step), early closes, holiday list beyond 2027, box R3 ridge threshold does not append new p (VPS does).
7. VPS: CBOE daily history is never available at 16:16:30, so VPS runs with STALE volatility inputs (default per directive): 11 of 20 days flip decisions vs the same-day model (VPS_MATCH_20D.md). `--strict` = no file. NT8 high/low must be full-session (second row after 17:00) else ADR ~8% low.

## Backfill vs ORDERS_20260626_20261016.csv (reconcile_core; ORDERS holds only canonical cell K4V2 + hedge)
| variant | window | days matching (K4V2 index set) | ORDERS rows matched (signal) | extra rows | qty within 1% | notes |
|---|---|---|---|---|---|---|
| V0 research-faithful (engine price 16:17:00, quarterly refit 07-01/10-01) | last 20 (09-21..10-16) | 20/20 | 6/6 = 100% | 0 | 6/6 | port validated |
| V0 | 07-01..10-16 | 76/76 | 28/28 = 100% | 0 | 18/28 (fixed vs daily ADR ratio; fixed ratios 28/28) | fill price: ORDERS fill = first print, my proxy = 16:17 bar open, within 1 tick 9/28 (informational) |
| V1 DEPLOYED (frozen 20260731, price 16:16:00) | last 20 | 16/20 | 2/6 = 33% | 3 | 2/2 | MISSING 4, EXTRA 3 |
| V1 | 07-01..10-16 | 67/76 | 18/28 = 64% | 8 | 10/18 | |
| V2 (frozen model, research price) | last 20 | 18/20 | 4/6 = 67% | 2 | 4/4 | |
| V2 | 07-01..10-16 | 69/76 | 24/28 = 86% | 9 | 14/24 | |
Side: all matched rows LONG (hedge SHORT) as ORDERS. Cause of V1/V2 mismatch: model freeze differs from the research quarterly schedule and the 1-minute earlier price; both move marginal p across 0.58. Files: backfill_summary.csv, backfill_files_V*.csv.
Example (deployed): 10-16 writes 26 LONG rows (ES and YM on K4V2) + ES hedge 1.379; ORDERS has ES only.

## Today's file (2026-10-19)
Expected: NO FILE at 16:16:30-16:19:30 (feeds 9-16 min late); 16:32 shadow file. Result is in outputs/k4/K4_WRITES.log (not awaited here; the lead should read it after 16:33 ET). Sync to C:\K4 is a user action (not done).

## Update (K4-VPS lightgbm amendment)
k4_vps.zip rebuilt: 19 LightGBM Booster text files (models/) + k4_model.json (ridge, cells, seeds). Tested in venv Python 3.12.3 / pandas 3.0.6 / numpy 2.5.4 / lightgbm 4.7.0: booster vs in-memory max abs diff 0.0; 20/20 identical to box writer with same-day vol data; stale-VIX mode still flips 11/20 days. Not tested: Windows, real NT8 export.

## Update K4-VPS v2
Schema v2 (row=1616/close), Yahoo-primary same-day vol with timestamp rule, BANDS_18CELL.json (shipped config: mean $1,075/wk, SD $10,394, Sharpe 0.75; 26-cell pack 3,128/12,534/1.80; the 1.379 ES hedge is too large for 18 cells, refit ~0.98 ES, not applied). Real Yahoo index-quote lag 915s constant => 16:16:30 run STALE daily. Identity 20/20 (same-day, Yahoo mock on-time); late mock rejected.

## Update K4-VIX / v3
DBIX.CORE trades (raw symbols VIX VIX3M VVIX VIX9D VIX6M; SKEW EOD-only, no prints) live-entitled; coverage from 2026-10-05; DBIX 16:16:00 values == CBOE daily closes on all 50 series-days; VPS identity 10/10 days, 0 flips. Zip shipped vol-path-only: writers refuse signal files while the book is incomplete (8 cells + RX7 shorts + R12/R12P SKEW). Hedge 0.98 applied (26-cell scan: 0.98 ES Sharpe 2.04/DD 71k vs 1.379 ES 1.80/74.5k). 18-cell package withdrawn (outputs/k4/withdrawn/). DBIX sample cost ~$0 logged in SPEND.json (K4-VIX_DBIX_2026-10-19).

## Update K4-EXACT
SUPERSEDES the 26-cell/18-cell material above (VOID). See autopilot/REPORT_K4_EXACT.md and outputs/k4/K4_EXACT_CELLS.csv. The shipped zip is now the 17-cell K4-EXACT writer (clock 16:17 ET, file K4_YYYYMMDD_1617.csv). The box writer is retired logic and never writes.
