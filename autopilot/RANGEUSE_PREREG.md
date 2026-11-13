# T-RANGEUSE preregistration (W-RU), 2026-11-13, logged before any scoring
Order: autopilot/DIRECTIVE_UW_3PART_20261113.md PART 2. Research only, shadow, no PASS claim.
Base: exact engine JN05W2, all layers ON (identity: empty rule = 598 trades / net 25943.82 on 202610). Windows L3M (2026-08..10), L6M (2026-05..10) first; then HOLD (2025-11..2026-10), PREUW (2024-10..2025-06).
Forecasts (walk-forward, expanding, min 120 days, refit every 10 trading days, ridge, as in ur_forecast.wf) of session ln range at reading R0 prior close / R1 08:30 / R2 09:30 / R3 10:00 ET, trade uses the reading by its signal clock:
 (a) benchmark ATR-only (ur_forecast.bench default), (b) ATR + IV term group (NDX/QQQ/SPX iv_term cols), (c) full UW model (ATR + iv_term + SPX:flip QQQ:flip SPX:gamma ALL4:gamma NDX:iv_level SPX:iv_level tide).
Forecast in points = exp(pred) * prior-close price proxy; dial multiplier m = clip(F / Fref, lo, hi), Fref = expanding median of the same forecast (past only); tercile cut points expanding (past only).
Dials 1-8 exactly as in the order. Question per dial = gain of (b) and (c) over (a) on the same dial and same threshold family, also showing no-rule row.
Scoring: drawdown first (maxDD, worst week, full stops/wk, best-5 weeks kept, winning weeks turned losing) then mean $/wk; tolerant gate; lead only if it holds in BOTH recent (L3M/L6M) and older (HOLD/PREUW); placebo = forecast tags shifted 11/23/37 days, family null = permuted forecasts within month; walk-forward bi-weekly of every pick; measured fills. Event vs non-event day split after W-CAL flags land.
First-order screen on T2_JN05W2 trade table ranks; exact re-runs (own hook module ru_hooks.py, no shared engine edits) for finalists. No PASS claims.
