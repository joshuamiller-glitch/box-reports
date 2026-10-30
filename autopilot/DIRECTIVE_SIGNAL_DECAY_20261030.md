# T-SIGNAL-DECAY — user directive pasted 2026-10-30 (verbatim)

T-SIGNAL-DECAY — exit when the edge is spent, not when price says so: every invalidation / decay definition for every book, per contract (2026-10-30)

Research only. No live, execution-server or chart change. UNTOUCHED never read. MEASURED fills (market exit at the path +1 tick; the live-calibrated basis beside it; conservative = stress label only). Per-contract pts/trade primary; stack $/wk on the exact lock engine second. Session as a column; nothing killed on the pooled number. RECENT FIRST. Prereg per section; every cell to DEAD_CELLS.csv. Data: the THP/THL 1-s path trees (every in-trade second), the signal engines' own state series (Keltner, Supertrend, HMA/VWAP, PB levels, Donchian, MV vote, PB7, CRT, iFVG, O6), l2feat, the regime tags. Runs beside the L2 cycles and T-CONFIRM-LAYER.

The idea (institutional practice, untested here)

A position is held for as long as the forecast that opened it is alive; when the forecast is spent or invalidated, the position is closed — up or down — rather than waiting for a price-based stop or target. Every exit tested so far keyed on PRICE (path, book, brackets). This program keys on the SIGNAL.

A. Invalidation exits — the setup's own premise is no longer true (per book; each as its own cell family)
KB (Keltner break 3m): price closes back inside the channel; back inside the midline; the channel flips; EMA-200 side flips; the break bar's low/high is lost.
ST / U6 (Supertrend 1m / 10m): Supertrend flips (the live opposite-flip exit) and the EARLIER versions: price closes beyond the Supertrend line without the flip; the line stops moving for N bars; ATR regime change.
HM (HMA-VWAP cross 1m): HMA slope flattens (|slope| < k) / turns; price closes back across VWAP; the HMA-55 re-crosses; the EMA-200 filter flips.
PE / PB3B (pullback): the pullback low/high (the swing that defined the entry) is taken out; the trend regime (ST10) flips; the level (EMA-20 / Keltner mid / swing zone) is lost on a close; the 1-min structure makes a lower high (long) / higher low (short) after entry (CHoCH).
PB7 / A6: the same on its own level and regime definitions; MV (momentum vote): the vote drops below the entry threshold / flips; DN (Donchian): price closes back inside the Donchian channel / mid; CR (CRT): the swept range's edge is re-broken; iFVG: the inverted gap is re-inverted; O6: the drive's open is re-crossed.
GENERIC, every book: a 1-min / 3-min / 5-min close against the entry beyond the signal bar's extreme; BOS/CHoCH against the trade on 1m / 5m / 15m; the opposite signal of ANY other live book (cross-book invalidation); a VWAP cross against; a Supertrend-1m flip against (for the non-ST books). Each invalidation × action: exit at market at once / exit at the bar close / tighten the stop to the invalidation level / exit half; × a minimum age (0 / 1 / 2 / 5 min since entry) and × "only when under water" / "only in profit" / always. Vs hold-to-bracket, lot-matched, same entries. Report, per book, the share of trades the exit touches, the saved-loss vs forfeited-win split in dollars, and P(target | invalidated but held) so the user sees what the premise is actually worth.

B. Decay exits — the forecast horizon is spent
Time since entry: 5 / 10 / 15 / 20 / 30 / 45 / 60 / 90 / 120 min and the session end, as a hard exit and as a tighten (stop to entry / to MAE+X) — the clean version of the time-exit grid, per contract and per session (the horizon of a 60/60 bracket is NOT the same in Asia and NY AM; report the realised median time-to-target per book/session beside it).
Progress-based horizon: exit if the trade has not reached +X% of the target within T min (X = 25/50, T = 5/10/20/30); "flat-line" exits (range of the last N min < k ATR while in profit / under water).
Edge-based horizon: the book's historical conditional expectation E[remaining pts | time since entry, unrealised] from the path trees, re-fitted walk-forward (3-month windows): exit when it falls below the exit cost (1 pt) — the direct "alpha is spent" rule; per book / session / regime; the same with the hazard model's P(target before stop) below 50% / 40%.
Volatility-scaled horizon: the horizon in ATR-time (bars × ATR) instead of clock time.

C. The forecast re-score (the true institutional form)
Every book's entry has an implicit forecast. Make it explicit: at every in-trade minute, re-run the book's own signal logic and a walk-forward model of the next-60-min move from the signal's features (signal strength, regime, HTF context, the confirmation catalogue of T-CONFIRM-LAYER where built, book state) — "would this book enter here now?"; exit when the re-scored forecast turns against the position (or below a threshold), tighten when it weakens, add (within the book's lots) when it strengthens (the latter only as a reported variant). Walk-forward 3-month weekly re-fit; shuffled-feature placebo; per book / session; the drift by quarter.

D. Combinations and the stack
Best invalidation + best decay per book, jointly, on the stack with the lock engine (re-entry effect included: an early exit frees the book for the next signal — report the re-entry P&L separately); equal-risk scaling frame (EQR) reported but labelled structure; vs hold-to-bracket, vs the live path TH rules, vs the L2 health rules the user runs.

E. Controls and gates
Random exits at the same rate and at the same time-since-entry distribution; shuffled-signal invalidations (another day's signal state); the N basis and live-cal basis; per-contract CI and MDE; White RC per section; a rule is CANDIDATE only ≥ 0 per contract in the last 6 months AND HOLD with placebo beaten; CANDIDATE-RECENT reported as such.

F. Report and publish
DS3_DECAY_A_INVALIDATION.md, DS3_DECAY_B_HORIZON.md, DS3_DECAY_C_RESCORE.md, DS3_DECAY_FINAL.md: one verdict line per book and the plain sentences "when KB's break is lost on a 3-min close, exiting at market saves X pts per contract on Y% of trades in the last 6 months (MDE Z); the trades it exits would have reached the target W% of the time"; "PE's edge is spent after T minutes in session S". Anything ≥ 0: profit / loss rules in THP_POLICY.txt in D6's vocabulary (D6 has every engine's state live, so an invalidation rule is a one-line feature: kb_inside_channel, st_flip, hm_slope, pb_low_lost, bos_against_5m, mins_in_trade), named exactly in DS3_THL2_NEEDS.md for adding. MORNING.md every 2 h.
