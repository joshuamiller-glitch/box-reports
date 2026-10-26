# DIRECTIVE T-SBS (received 2026-10-26, verbatim)

T-SBS — Stoic market-structure family: SBS, Golden SBS, Range Model, and the stacked model. New entry family for DS3; same V2 rules (prereg ≤ 30 cells, mechanism + predicted effect + MDE, standalone + paired vs ST where overlapping + equal-risk + mix-into-DS3, long/short, by session, quiet/wide, placebo vs best-of-N null, 2023-04..2024-01 second holdout, main holdout once, ledger, executability flag). Runs beside T-STRUCT-FIB and shares its swing detector.

Common machinery (one implementation, every cell uses it)
Swing detector: fractal length L ∈ {3, 5, 8, 12} bars; a swing high = highest high with L lower highs each side (mirror for lows). Confirmed only after L bars (no look-ahead; the identity audit must pass).
Signal bars: {15 s, 30 s, 1, 3, 5, 15 min} and {250, 500, 1000-tick}, {5, 10-pt range}. Parent/context bars: {5, 15, 60 min}. Only combinations where the signal bar is faster than the parent bar.
Sweep = trade beyond the reference level by ≥ {1, 3} ticks then a close back on the original side within {1, 3} signal bars.
Reversal response at point 5 (confirmation SBS) = one of: (a) double-bottom/top: second low within {3, 6} ticks of the sweep low then a close above the intervening high; (b) close above the high of the sweep bar; (c) structural flip on the signal bar (first higher-high after a lower-low sequence); (d) KB-style band re-cross. Score each as its own cell.
Execution: DS2's P9 (slices, stop-join) for market/stop entries; resting limits fill by trade-through only. Flat 16:55; DS2 session windows; also an "all hours" column since the sequence runs overnight.

S1. SBS, confirmation version (five stages)
Point 1 = break of a swing high (selected swing: the most recent L-swing; also the parent-bar swing). Point 2 = first pullback low after the break. Point 3 = push to a new high (required / not required: both). Point 4 = sweep of the point-2 low. Point 5 = reversal response → entry: buy-stop above the response bar high (and market-on-close variant). Stop: beyond the sweep extreme + {0, 5} pts (and the fixed 60 control). Targets: point-3 extreme (TP1) then {1×, 2×} the point-2→point-3 leg; fixed 60 control; scale-out 50% at TP1 as a variant. Time-outs: entry cancelled if no point 5 within {10, 30, 60} min of the sweep.

S2. Golden SBS (resting entry, no confirmation)
Expansion = origin low → extreme high of the selected local move (the point-1 break leg). Resting limit at 0.618 of that expansion, valid only if 0.618 lies beyond the point-2 low (strict) — also the loose version without the point-2 condition. Stop beyond the expansion origin + {0, 5}. Exit all at 0.236 (as written); variants: 0.236 then runner to 0.0 with a trail; fixed 60 control. Cancel if untouched within {30, 60} min or if price breaks the origin first.

S3. Stoic Range Model as the context layer
Range = the parent-bar box: high/low of {the prior session, the overnight session, the last N parent bars with N ∈ {12, 24}, the developing session so far}; mid = 50%. Setup A sweep-and-retest: poke beyond a boundary, reclaim inside, retest holds (one close back inside followed by a close that does not re-break) → enter toward the mid; TP1 mid, TP2 opposite boundary; stop beyond the sweep extreme. Setup B break-and-retest: leave the box, retest the boundary from outside and hold → enter in the break direction; TP1 = 1× range height, TP2 = 2×; stop back through the retest. Score standalone, and as the gate for S1/S2 (SBS allowed only at a boundary of the parent range).

S4. The stacked model (tweet: SBS → hourly fib zone → 5-min structural flip → hourly high/low)
Context: 60-min swing fib from the last 60-min impulse; POI zone = 0.5–0.618 (also 0.618–0.786). Trigger: an SBS sweep inside the zone on the {1, 3, 5-min} bar, then the structural flip (first higher-high / lower-low) on the 5-min (also 1-min). Entry on the flip bar close or stop beyond it; stop beyond the sweep; target = the 60-min swing high/low; fixed 60 control; scale-out at 50% of the distance as a variant.

S5. Controls and placebos
Random-level sweeps (same count, random reference levels), time-shifted sequences, the mirror (fade the SBS entry), and the plain sweep-and-reclaim trigger from T-ENTRY as the baseline each S-cell must beat paired.

Reporting
SBS_LEADERBOARD.md: family / cell / signal bar / parent bar / L / entry type / stop / target / trades per week / win rate with the required-vs-observed hurdle at its R multiple / avg win-loss / paired vs baseline sweep trigger / standalone WF-holdout-2023 / equal-risk $/wk / DS3 marginal Sharpe / placebo / executability (second and tick bars are native NT8 bar types; the swing detector and fib anchors are plain OnBarClose logic). Verdict line: "SBS family: N PASS, M CANDIDATE. Best: <cell>, X trades/wk, R r, win w vs required q, DS3 marginal +S." Parameter-level spec for any PASS. No live recommendation.
