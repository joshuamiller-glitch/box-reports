# REPORT_L2_S4 - trackS4 (tranches 2/5, T6, T7) and the S130 LEAD (2026-10-22)
Scope: ~85 L2 families on NQ/ES/RTY (real exec_engine_l2 fills, FEES std 4.84 RT, M2 12/3/3 tilt, signflip nulls, F_eff 200), all REPORT-ONLY. Index lines in outputs/MECHANISM_INDEX.md; AUTOPILOT.md carries the result blocks.
## Summary
No best-of-F pass, no CONFIRMED. One LEAD: S130_DAYTYPE_ES (Sharpe 1.50, signflip rank 0.996, gates a-d pass; best-of-F rank 0.45). Chance of >= 1 rank >= 0.99 among ~85 families ~0.57. Sub-5-min / book-structure families are cost-bound (~-$14 net per trade, ~0.9e9 simulated cell-trades); lookahead bug in S19 ROUND found and fixed (void read discarded).
## S130_DAYTYPE: frozen ES cells, raw vs own-trailing-20-day-rank forms (REPLICATION RULE; RTY informational)
Frozen-book Sharpe / signflip rank / $ per week at the size where OOS maxDD = $210k / last 8 weeks (pair $50.0k/wk); M2 12/3/3 refit Sharpe / null rank:
- ES  raw 1.78 / 0.999 / $8.8k / +$11.5k; M2 1.50 / 0.992.  rank 1.77 / 0.999 / $8.4k / +$9.0k; M2 1.62 / 0.996.
- NQ  raw 1.00 / 0.972 / $3.6k / -$8.6k; M2 1.01 / 0.965.   rank 1.01 / 0.974 / $4.1k / -$11.5k; M2 0.95 / 0.956 (gates c,d fail).
- RTY raw -0.33 / 0.27 / -$0.5k / -$3.0k; M2 -0.66 / 0.15.  rank -0.30 / 0.30 / -$0.4k / -$1.2k; M2 -1.26 / 0.02 (informational only).
Table: outputs/l2vast/S130_REPLICATION_TABLE.csv. ES S130 at maxDD-matched size pays $7.5-8.8k/wk = 15-18% of the pair's weekly income.
## REVERSE TEST (for the record; NQ is not LEAD-grade): NQ-fitted cells -> ES, no refit
NQ last-fit-window (2025-08..2026-07) tilt weights per cell (28 raw / 29 rank cells), ES unit scale from ES's own SD over the same calendar fit window, evaluated on ES OOS 2024-02.. (141 weeks) and the full ES sample (167 weeks):
- raw : Sharpe -0.44, signflip rank 0.24, -$1.0k/wk at the $210k-DD size, last 8 wk +$1.9k (full sample: -0.56 / 0.16 / -$0.9k).
- rank: Sharpe -0.76, signflip rank 0.11, -$1.2k/wk, last 8 wk -$0.2k (full sample: -0.84 / 0.07 / -$1.0k).
So the NQ-selected cell weights do not transfer to ES (the NQ last fit window is the stretch where NQ S130 lost, H2 net -7); the cross-instrument support for S130 is therefore only the same-sign family-level reads (ES 1.5-1.8, NQ 0.95-1.0), not cell-level agreement. Files: outputs/l2vast/S130_REVERSE_NQ_to_ES.csv, LEAD_FREEZE_S130_NQ_reverse.json.
## Forward shadow (REPORT-ONLY)
Registered Wed 2026-10-21. Feed = weekly ES L2 extension (already inside the Saturday NQ+ES+RTY buy, $31.70/wk, under the $40 cap). Forward clock = first FULL ISO week after registration, 2026-W44 (Mon 10-26..Fri 10-30, data bought Sat 10-31); 2026-10-12..10-23 are PRE-FORWARD (not counted). ES forward CONFIRMED = >= 26 forward weeks, net > 0, forward sign-flip rank >= 0.99 (RTY informational). Scripts: outputs/l2vast/standS4/s130_shadow.py (weekly), outputs/autopilot/forward/ap_shadow_s130.py (lines() hook, wired into ap_m2_paperall.py md_lines), series/SHADOW_S130.json; runbook step 15e. Frozen cells: outputs/l2vast/LEAD_FREEZE_S130_ES.json (29 cells, usd_per_book_unit 36,684.9).
