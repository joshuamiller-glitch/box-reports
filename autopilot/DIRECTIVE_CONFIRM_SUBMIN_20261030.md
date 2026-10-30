# T-CONFIRM-LAYER ADDENDUM 3 — SUB-MINUTE MA EVENTS AND PRICE-MOVEMENT EVENTS — user directive pasted 2026-10-30 (verbatim)

T-CONFIRM-LAYER ADDENDUM 3 — sub-minute MA events and price-movement events as the confirmation (user, 2026-10-30)

Applies to T-CONFIRM-LAYER v2, COMBOS, BARS. Same scoring. These are explicit cell families on 1 s, 5 s, 15 s, 30 s, 45 s (and 1 m, 2 m, 3 m for comparison), on every bar type in the BARS addendum where the event is defined.

1. Moving-average EVENTS (every MA type in the catalogue: EMA / SMA / HMA / WMA / DEMA / TEMA / KAMA / VIDYA / ALMA / T3 / JMA / VWMA; periods 5 / 8 / 9 / 13 / 20 / 21 / 33 / 34 / 50 / 55 / 89 / 100 / 200)
CROSS: fast over slow in the signal's direction (every pair with fast < slow from the period list, e.g. 8/21, 9/21, 13/34, 20/50, 50/200), on the bar close; also the "cross held for N bars" version (N = 1 / 2 / 3).
RECLAIM: price closes back across the MA in the signal's direction after being on the wrong side (the first close, and the second consecutive close).
SLOPE: the MA's slope turns in the signal's direction (sign change of the 1-, 3-, 5-bar slope); slope exceeds k × ATR per bar; HMA colour flip.
RIBBON: the full ribbon (8/13/21/34/55) re-stacks in the signal's direction; price re-enters / exits the ribbon.
DISTANCE: price's distance from the MA (in ATR or ticks) crosses back below a threshold (the pullback has reached the MA) / expands beyond it (the move has resumed).
VWAP / session-VWAP / anchored-VWAP cross, reclaim and band re-entry on the same sub-minute timeframes. Each × the six mechanics (market at the event; limit at the MA / VWAP level; dip + event; event already present as filter; event count as sizer; both stop styles) × the three bases, with the random-timing placebo (same event type on a shuffled day) and the time-matched random-confirmation control.

2. Price-MOVEMENT events on sub-minute bars (no indicator)
N consecutive closes in the signal's direction (N = 2 / 3 / 4 / 5) on 15 s / 30 s / 45 s.
Micro-structure: a new sub-minute swing low/high in favour (fractal 3/5), a micro BOS / CHoCH on 15 s / 30 s, break of the last sub-minute bar's extreme, a sub-minute inside-bar break, the first higher low (long) / lower high (short) after the signal.
Velocity / acceleration: price change over the last 5 / 10 / 15 / 30 s in favour exceeding k × the session's normal; acceleration turning in favour after a deceleration; "the pullback has stalled" (range of the last 10 / 15 s < k ticks) then the first tick in favour.
Tick-speed / intensity: prints per second above 1 σ with net direction in favour; a burst of ≥ N prints in 5 s in favour.
Sub-minute momentum oscillators: ROC / RSI(2) / CCI(5) on 15 s / 30 s crossing back in favour (the sub-minute versions of the oscillator triggers, run explicitly).
Sub-minute range contraction then expansion (NR4 / NR7 on 15-s bars then the break). Each × the six mechanics × the three bases × placebos, as above; all also as members in the COMBOS search (e.g. "15-s EMA-8/21 cross ∧ 5-m FVG ∧ book absorption", "30-s reclaim of VWAP ∧ POC ∧ three 15-s closes in favour").

3. Report
Added to DS3_CONFIRM_4 (MA/trend) and a new DS3_CONFIRM_SUBMIN.md: per event × timeframe × mechanic × base, per contract first, fill rate, time from signal to confirmation (median), the skipped-signal cost; the plain sentence "waiting for the 15-s EMA-8/21 cross after the KB signal adds X pts per contract on Y% of signals with a median wait of Z s (MDE W)".
