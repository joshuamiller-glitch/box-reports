# DS3_SPEC_RVW1_F30 - NQ last-hour VWAP-reversion close book (T-CLOSE block 1 CANDIDATE), parameter-level forward spec - D3CL1, 2026-10-27
Research output for the Sim leader; NOT a live recommendation, no live/chart/execution change. Tier: **CANDIDATE** (fails only the harness best-of-N gate; see DS3_CLOSE_BLOCK1.md). Deliverable from NT8 BARS (1-minute chart, OnBarClose) - no ticks, no L2.

## 1. Rule (exact)
- Instrument/bars: NQ front month, 1-minute chart, ET clock, full cash sessions only (skip half days / cash holidays / days with a missing RTH bar run).
- Series (all from 09:30 ET RTH bars of the current day, restarted each day; NOT the NT8 built-in session VWAP): typical price tp = (H+L+C)/3 of each 1-min bar; VWAP_t = sum(tp*Vol)/sum(Vol) from the 09:30 bar through bar t; dev_t = Close_t - VWAP_t; sigma_t = POPULATION standard deviation of dev_s over all bars s = 09:30 .. t (expanding, includes bar t).
- Signal evaluation: ONCE per day on the close of the 15:29 bar (bar ending 15:30:00): z = dev/sigma at that bar. Trigger iff |z| >= 1.0. Side = toward VWAP: LONG if z <= -1.0, SHORT if z >= +1.0. (z >= 2.0 is the RVW2 sibling, not part of this book.)
- Entry: market order, 10 lots, at 15:30:00 (fills at the open of the 15:30 bar in the model). One trade per day; no re-entry.
- Exit (OCO bracket from the fill): target limit +30 pts, stop-market -30 pts; if neither, MARKET exit at 16:00:00 (time exit; NT8: submit at the close of the 15:59 bar). Stop beats target if both inside one bar/second.
- No signal after 15:30; no trailing; no scale-out.
## 2. Window, size, locks, concurrency
- Operating window: a single decision at 15:30:00 and a flat book by 16:00:00; the live stack is flat 15:00-16:54 (no overlap); K4 holds overnight from 16:17 (no overlap, and this book is flat at 16:00).
- Lots: fixed 10 (R12k = 20 lots and R6k = 10 lots sizing table: DS3_CLOSE_BLOCK2.md SIZE). Max loss per trade = 30 pts x $20 x 10 = $6,000 + slippage/fees. Peak 10 lots; the 50-contract cap is not binding.
- Own locks: none needed beyond the bracket (one trade/day, max -$6.0k); in the harness it was scored under the stack's per-book thresholds ('stk': day -2R/+5R of R=$12,000, give-back 2R keep 50%, week floor -12R), which never bind on one trade per day. Account-level week floor of the stack applies as usual.
## 3. Expectation (basis M = mapped conservative; basis T = tape-direct-style; 10 lots, fees $4.84 RT; weekly $, 142 WF weeks 2024-02..2026-10-16)
| | WF mean | WF SD | maxDD | HOLD (2025-07+) mean | 2023-04..2024-01 mean | L8W mean | 2x-cost WFPRE / HOLD |
|---|---|---|---|---|---|---|---|
| M | +2,144 | 9,585 | 56,317 | +900 | +1,107 | -2,720 | +1,487 / -1,378 |
| T | +1,725 | 10,270 | 69,769 | +577 | +1,325 | -1,551 | +1,967 / -223 |
3.19 trades/wk; win 60% vs required 54% (M), PF 1.31. Stack-add (vs live stack, WF): d mean +2,144 [CI 560, 3,774], d Sharpe +0.12, d maxDD -6,220 (M); +1,725 / +0.09 / -3,614 (T). Weekly paired MDE 2,252 (M): the stack-add is within the MDE; ~157 forward weeks (M) / 278 (T) are needed to separate it from zero at the weekly level. Per-trade: beats same-rule-random-clock (200 draws, repeat) by +6.60 pts [2.95, 10.17] (M) and +5.10 [1.02, 8.98] (T), rank 1.00 both; also beats bracket-beta (d) and random-in-regime (c).
## 4. Caveats (must be read with the numbers)
- **No-quote fill caveat:** the 15:30 entry has no quote/print tape in the harness (tape extracted only 15:45-16:15 ET). M fills at the 15:30 bar open; T at the 1-s close of the entry second +/-1 tick with no spread/depth model. Edge per trade is thin (net ~ +2 to +3 pts after cost vs a 30-pt bracket): the 2x-cost HOLD mean is NEGATIVE (-1,378/wk M), so a fill 1-2 ticks worse than modelled removes the holdout edge. A 15:30 quote-fill check (extract 15:25-15:35 books) is a block-3/4 item.
- Fails the harness best-of-N gate (effect 6.8 vs family-null p95 129; per-bracket-class supplementary null p95 26.6 all signals / 10.2 excluding the 5 signals with n<110, still above 6.8). Last 8 weeks (L8W) are negative.
- HOLD (b)-effect +3.39 pts [0.24, 6.90] (M, 200 draws) but T +1.31 [-2.3, 5.3]: the effect halves out-of-sample.
- The year breakdown (per trade, M): 2023 +359, 2024 +821, 2025 +795, 2026 +296 $; Monday/Tuesday weak.
## 5. Forward-register entry (parameter level)
- cell_id: ds3_TCLOSE_RVW1_F30; object: sleeve (NQ last-hour VWAP reversion, standalone, adds to the stack); tier CANDIDATE; start: first full session after registration; expectation = WF mean/SD above (basis M; T as the floor), trades/wk 3.19; log per trade: z, side, fill price vs the 15:30 bar open, exit type, points; verdict rules as the register (PROMOTE >= 6 weeks z >= -1 sign right; RETIRE >= 8 weeks z < -2).
- Machine-readable entry and daily series: l2vast/ds3/out/tclose_b1/forward_entry_ds3_TCLOSE_RVW1_F30.json, RVW1_F30_daily_{M,T}.parquet, RVW1_F30_expectation.json (NOT copied into struct48/paper_all: the lead decides; the file follows that schema).
- Source: autopilot/DS3_CLOSE_BLOCK1.md; code l2vast/ds3/code/close3 (c3_signals.py RVW1, c3_patch.py F30); prereg TCLOSE_B1_CL7 sha256 in DECISIONS.md.
