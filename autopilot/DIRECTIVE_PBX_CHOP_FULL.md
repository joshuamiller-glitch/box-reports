# DIRECTIVE T-PBX + T-CHOP full scope (received 2026-10-27, verbatim; replaces the two short pastes of 2026-10-27: T-PBX addendum and T-CHOP item 2)

T-PBX (pullback books that fit the trade) and T-CHOP (books that earn when the trend books do not) — full scope. Replaces the two short pastes of 2026-10-27 (T-PBX addendum, T-CHOP item 2). Priority: both run as item 1b and item 2 of DIRECTIVE_PRIORITY_1027, immediately after the D3XT exit replay months land; they share the swing detector, the tick-built bar library, the 1-s / 100-ms book tables and the replay governor. Same V2 rules: mechanism + predicted effect + MDE per cell, preregs of ≤ 30 cells (as many preregs as the grid needs — the ledger carries all of them; nothing is dropped for being "too many"), paired tests on identical entries, placebo vs best-of-N null, 2023-04..2024-01 second holdout, main holdout once per prereg group, equal-risk columns, mix-into-DS3 at the 50-cap, executability flag per cell.
0. The two placebos that decide everything

Every cell in both tracks is scored against BOTH:

(a) timing-destroyed (random entry time, same bracket) — the usual null; and
(b) random-in-regime: random entry time inside the same regime direction (T-PBX) or inside the same chop-gate window (T-CHOP), same bracket, same lots. This is the P9 placebo that showed PB3B's pullback adds nothing over its regime. A cell PASSes only if it beats (b); beating (a) alone is "regime beta" and is labelled so. Report rank against both, with the best-of-N line for the whole prereg group.
1. T-PBX — pullback entries × brackets × exits × bars × tape
1.1 Entries (all scored as the same object: a pullback inside a trend regime)
The scored cells: PB3B_R5_P1, PB3B_R5_P2, PB_ST10_SWZ_T3, PRO_ER5_EMA5, PRO_ER4_EMA5, PB3B_R60_P2.
Regimes: Supertrend(ATR10×3) on 5 / 10 / 15-min; EMA200 on 5-min; KAMA slope on 5-min; the momentum ensemble sign (TR1A_ens_s0.5_k4) as a regime; higher-high/higher-low structure on 5-min swings.
Levels: EMA20 (1-min, 5-min), Keltner mid, 38–62% of the last impulse (fractal L = 2, 3, 5), anchored VWAP from the flip bar / session open / last swing low, VWAP ±1σ, developing VAH/VAL/POC, prior-session VAH/VAL/POC, overnight H/L, the flip level itself, the previous pullback low; first touch vs second touch; confluence ≥ 2 levels within 5 pts.
Pullback END defined by the tape (from the book tables, P1 of T-PULLBACK PRO, run this time): passive absorption at the level (resting size hit without price moving through; refill), aggressor flip (cumulative delta over the retrace turns to the trend side; same-side run-length ends), book imbalance at ±3 / ±5 levels reverting to the trend side, large-print cluster on the trend side, sweep-and-reclaim of the pullback low within N s. Footprint versions: delta flip on the bar at the level, stacked imbalance (3+ diagonal imbalances ≥ 300%) on the trend side, unfinished auction at the extreme, absorption footprint (high volume, no range) at the level.
Price triggers: close back through the level (T1), arming-bar break (T2, library), extreme-bar break (T2x), RSI(2) < 10 / > 90 (T3), inside-bar break, 2-bar reversal, CCI(14) washout cross from < −100 (the CCI filter), the first higher-low after the extreme on the trigger bar.
1.2 Bars (level and trigger bars; the regime stays on minutes)

1-min, 15-s, 30-s; 250 / 500 / 1,000-tick; 5 / 10-pt range; Renko 5 / 10 (standard and UniRenko-style with wick); volume 1,000 / 2,500 contracts; dollar bars $25M / $50M; 5-min. Built from the tick file with the AS-OF rule (usable only when complete); truncation-invariance audit on every bar type. Executability: NT8-native (minute, second, tick, range, Renko, volume) vs custom BarsType (dollar, UniRenko) — flagged.

1.3 Entry order types

Market on the trigger bar close (next-bar open); resting limit AT the level, filled by trade-through on the real book, cancel on time-out {10, 30 min} or on invalidation; stop-entry above the trigger bar's high (level + 1 tick, MAPPED with the stop-fill caveat); 3-rung ladder (level, −5, −10 pts, 1/3 each); scale-in on the second touch. Paired per-trade cost and fill rate for each; the limit and ladder variants carry their fill rate as a column, not as an assumption.

1.4 Stops (the risk side — the point of the track)

Pullback extreme +5 / +10 pts; 1× / 1.5× ATR(14) of the trigger bar below the level; below the last 5-min higher-low −5; fixed 20 / 30 / 40 / 60 (controls). Lots = fixed-R: $12,000 risk per trade whatever the stop (lots = round(12000 / (stop × 20)), capped so the 50-lot line holds beside DS2), and the fixed-10-lot sensitivity.

1.5 Exits (scored on identical entries; the half that has never been settled)

Fixed 1R / 1.5R / 2R / 3R; the impulse high (measured move); the next level above (VAH, prior high, overnight high); chandelier trail k = 2 / 2.5 / 3 × ATR(22) on the 1-min and the 5-min; Supertrend band trail (1-min, 5-min); swing-structure trail (below the last higher-low −5, updated on each new 5-min swing); parabolic SAR; opposite 5-min flip (OPP exit); breakeven at +1R then trail 20 / 30; profit-lock (+1.5R → stop to +0.5R; +2R → trail 20); time stops 60 / 120 min; "no target, trail only"; 50% at 1R + runner on a structure trail (two-leg direct replay as SO2). Also the exits from D3XT as they PASS/CANDIDATE there.

1.6 Design

Entry family × bar × order type × stop × exit is ~10^5 cells. Prereg in blocks: (i) each entry family on 1-min, market entry, full stop × exit grid (≤ 30 per block); (ii) the best stop × exit per family across all bars; (iii) the best bar × bracket per family across order types; (iv) the tape-defined ends and footprint triggers on the best (bar, bracket) only; (v) the full stack for the top 3 cells overall with the robustness block (full stability surface, day-block bootstrap maxDD, VIX terciles, fill sensitivity 5 / 50 / 150 ms, cost 1× / 1.5× / 2×, capacity to 42 lots, counter-trend mirror, long/short, by session, quiet/wide). Direct L2 replay for every market / stop-join cell that reaches block (ii); limits by trade-through on the book; stop-entries mapped and labelled.

2. T-CHOP — books for the sessions the trend stack loses
2.1 The target, stated up front

Not "beats ST". A book with weekly correlation ≤ 0.2 to the DS2+DS3 trend stack, positive mean in the stack's losing weeks and in the FAILPRED chop sessions, and positive marginal Sharpe / negative ΔmaxDD when added to KB+SM+PE at the 50-cap. Sharpe 0.8 with correlation −0.2 is a PASS-shaped result; report every cell that gets within reach of it even when its standalone $/wk is a third of ST's.

2.2 Mean-reversion / range entries
Dip-buy family: RSI(2) < 10 / 5 (long) and > 90 / 95 (short) on NQ, ES, RTY, YM (the forward-register sleeves ES_RSI2_t10, NM_E_*, RSI2C/T, RTY_IBS as named cells); IBS < 0.2 / > 0.8; 3-day / 2-day down close; z-score of close vs 20 / 60-bar regression ≤ −2 → long at the turn.
Band fades: Bollinger(20, 2) outside-and-back; Keltner(20, 2) outside-and-back; VWAP ±2σ / ±3σ touch-and-reject; developing VA edge rejection; anchored-VWAP band from the session open.
Range model (the Stoic range model as a mean-reversion book, not a breakout): prior-day H/L, overnight H/L, opening range, N-bar box (12 / 24 parent bars) — sweep beyond and close back inside → target mid / opposite boundary; Asia-range fade in London; London-range fade in NY.
Failed-breakout fades: the mirror of every DS3 flip book — KB / SM / PE signal that fails to reach +15 pts within N bars and closes back through the level → fade to the signal origin; stop beyond the failed-break extreme.
Overnight gap fill (gap ≥ 0.3 / 0.5 ATR20 at 18:00 / 09:30, fade toward the prior close); first-hour reversal (09:30 drive reverses by 10:30); end-of-Asia reversal (the 45%-fail Asia sessions: 02:00–03:00 ET fade of the Asia drift); FOMC / 08:30-release mean reversion after the first 10 min.
Tape-defined exhaustion (the FOOTPRINT family, run here): absorption at a range extreme, aggressor exhaustion (run-length of same-side trades ends with a large print against), delta divergence at a new high/low, stacked imbalance against the move, unfinished-auction fill, iceberg detection at the extreme (refill count ≥ 3), book-thin side reversing. Each as its own entry on the extreme of the move, stop beyond the extreme +5.
Cross-asset: NQ fade when ES does not confirm the new extreme (relative-strength divergence); fade when ZN moves against equities.
2.3 Chop gates (conditioning, not filters — report both gated and ungated)

Efficiency ratio (10 / 20 / 30 bars) ≤ 0.3 / 0.4; ADX(14) < 20 / 25 on 5-min; Supertrend flip count in the last 60 / 120 min ≥ 2 / 3 (the "flip-chop" signature of the failing sessions); ATR(10) / ATR(50) ≤ 0.8; the compression forecaster P(quiet) ≥ 0.6; realised-vol tercile; session (Asia, London, NY as columns); the FAILPRED session label (post-hoc, for the P&L-by-session column only, never as an entry gate).

2.4 Bars, orders, brackets, exits

Bars: the full 1.2 list plus 5-min and 15-min for the band/range families. Orders: resting limit at the band / boundary (trade-through fills, time-out, invalidation), market on the reclaim bar, stop-entry on the reversal bar. Stops: beyond the extreme +5 / +10, 1× ATR14, fixed 20 / 30 (NOT 60 — these are not 60-pt trades). Targets: the mean (VWAP / EMA20 / mid), the opposite band, 1R / 1.5R, time stop 30 / 60 / 120 min, exit on the trend book's flip (hand off to the trend stack). Lots fixed-R at $6,000 and $12,000 per trade; equal-risk to ST10's weekly SD.

2.5 Design

Blocks of ≤ 30: (i) each entry family ungated on its natural bar with its natural bracket; (ii) gates × the best cell per family; (iii) bars × order types on the best gated cell per family; (iv) tape exhaustion entries on the best two families' extremes; (v) the top 5 by the 2.1 target with the full robustness block and the 50-cap concurrency replay beside DS2 + DS3. Direct L2 replay on NQ for every finalist; ES / RTY / YM mapped with disclosed fill models (and direct where the book data exists).

3. Reporting — never empty-handed

Both finals (DS3_PBX_FINAL.md, DS3_CHOP_FINAL.md) carry, in this order:

The verdict line and the PASS / CANDIDATE list.
The top 10 cells by the track's own target metric regardless of verdict, each with: which gate it failed, by how much, the MDE of that gate, and what forward evidence (weeks) would settle it. "0 PASS" on its own is not an acceptable final.
One RECOMMENDED-FOR-SIM cell per track (the best deliverable cell with a positive direct-basis holdout and a non-negative DS3 marginal line), with a parameter-level DS3_SPEC_<cell>.md and the forward-register entry, whether or not it PASSes. If nothing meets even that, say exactly which gate blocks it and show the random-in-regime placebo beside it.
The structural read: which axis moved the paired delta at all (bar, order type, stop, exit, gate, tape) and which did nothing, with the interaction table and CIs — so the next track is aimed, not a re-run.
The power statement: per-trade and weekly MDE for each family, and the smallest effect the design could have seen. Honesty rule unchanged: no gate is loosened, no cell is DEAD solely for earning less than ST at equal lots, duplicates are flagged, every holdout look is logged.
4. Compute

Tape layer and tick-built bars built once and shared (the FOOTPRINT prereg's tables); month-major replay under the governor; 90% floor on items 1 (exits), 1b (PBX) and 2 (CHOP) in that order; memory gate 32 GB, no replay kills. ETA per block in MORNING.md every edition.
