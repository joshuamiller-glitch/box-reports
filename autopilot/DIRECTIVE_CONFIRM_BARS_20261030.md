# T-CONFIRM-LAYER ADDENDUM 2 — BAR TYPES — user directive pasted 2026-10-30 (verbatim)

T-CONFIRM-LAYER ADDENDUM 2 — BAR TYPES as the confirmation (and as the base) — "after the signal, wait for a 15-s Heikin-Ashi / footprint / range-bar / anything confirmation" (user, 2026-10-30)

Applies to T-CONFIRM-LAYER v2, the COMBOS addendum and T-SIGNAL-DECAY. Same scoring (per contract first, measured fills, recent-first, placebos, lock-engine stack line). Every bar type below is built from the 1-s tape (and the mbp-10/1-s add-cancel tables where the type needs them) for 2023-04 .. 2026-02-06 and stored once.

1. The bar-type catalogue (every item × the timeframes / sizes listed)
Heikin-Ashi on 15 s / 30 s / 45 s / 1 m / 2 m / 3 m / 5 m / 15 m: colour flip in favour; first strong body (body ≥ 70% of range, no opposing wick); two / three consecutive in favour; HA doji then flip.
Renko: brick 2 / 4 / 6 / 8 / 10 / 16 ticks (classic, and UniRenko / "better renko" with reversal 2 bricks, and median/ATR-sized bricks): reversal brick in favour; continuation brick; N bricks in favour.
Range bars: 4 / 8 / 12 / 16 / 24 pts: close in favour; two in a row; a range bar closing beyond the prior range bar's extreme.
Volume bars 250 / 500 / 1,000 / 2,000 / 5,000 contracts, tick bars 233 / 500 / 1,000 / 2,000 prints, dollar bars (equivalents): close in favour; close beyond the signal bar's extreme; N in favour.
Imbalance / run bars (Lopez de Prado): tick-imbalance, volume-imbalance, tick-run, volume-run with EWMA thresholds: a bar closing in favour; the imbalance sign.
Footprint bars on 15 s / 30 s / 1 m / 5 m (from the tape): bar delta in favour; delta divergence resolved in favour; stacked imbalances (≥ 300%, 3+ levels) in favour at/near the price; unfinished auction against the trade (bar high/low with volume both sides); POC migration in favour; absorption at the level (large volume, small range, close in favour); exhaustion against (shrinking volume at the extreme).
Volumetric (NT8 Order Flow+) equivalents: cumulative delta bar colour, delta per bar sign.
Kagi (reversal 4 / 8 / 16 ticks), Point & Figure (box 2 / 4 / 8 ticks, reversal 3), Line Break (3-line / 2-line, 1 m / 5 m): reversal in favour.
Momentum / "Kase" / LinReg / Hull-smoothed bars: colour flip; Delta-Pro / Diff bars: close in favour.
Candle anatomy on the sub-minute types (15 s / 30 s / 45 s candles themselves): engulfing, pin, inside-bar break, marubozu, three-bar reversal — in favour, at the level.

2. The same six mechanics, on the three bases, for every bar-type confirmation
(a) market when the bar-type confirmation prints (at that bar's close); (b) resting limit at the confirming bar's open / mid / extreme (e.g. the HA flip bar's open; the renko reversal brick's base; the footprint absorption level); (c) dip + bar-type confirmation (the dip of 3/5/8/10 from the signal or the running extreme, AND the 15-s HA flip / the footprint absorption / the range-bar close); (d) filter (the bar-type state already in favour at the signal); (e) count of bar-type confirmations as sizer; (f) both stop styles. Controls: plain 3-pt dip, market at signal, random bar-timing placebo (the same confirmation type on a shuffled day), time-matched random confirmations at the same rate.

3. Combinations across bar types and with everything else
Bar-type confirmations enter the COMBOS search as a family: pairs / triples / four-legged sets with the ICT arrays, levels, oscillators and book items (e.g. "15-s HA flip ∧ 5-m FVG ∧ CCI cross", "footprint absorption at the session POC ∧ renko-4 reversal", "range-bar-8 close beyond the signal bar ∧ VWAP −1σ"); nested bar types (HA flip on 15 s inside an HA trend on 5 m); the learned trees with bar-type features.

4. The live engines re-derived on every bar type (the user's "1-minute Japanese candles are best?" question, answered directly)
KB / ST / HM / PE / SM / MV / PB / DN / PB7 / CRT / iFVG recomputed on each bar type and size above (the signal logic unchanged, the bars changed; where a parameter is in bars it is kept in bars, where in minutes it is converted at the realised bars-per-minute), 60/60 control bracket, session by session, measured fills, lot-matched vs the 1-min version on the same days; per contract and stack; placebo = the same engine on a shuffled-bar-size version. The verdict per book: "KB on 8-pt range bars vs 1-min candles: X vs Y pts per contract, L6M / HOLD / PRE", with the session table. Any bar type that beats 1-min in a session is registered as a session cell (never killed by the pooled number).

5. Report
DS3_CONFIRM_BARS.md (confirmation use, per bar type × size × mechanic × base; per contract first; fill rate; the skipped-signal cost), DS3_ENGINES_ON_BARS.md (section 4: book × bar type × session table), plus the COMBOS report gains the bar-type sets. Plain sentences: "waiting for a 15-s Heikin-Ashi flip after the PE signal adds X pts per contract on Y% of signals (MDE Z)"; "KB on 4-tick renko beats KB on 1-min candles in Asia by W pts per contract (MDE V)". Anything ≥ 0: entry rules in THP_POLICY.txt and, for section 4, the engine/bar spec exact enough to build in NT8 (bar type, size, every parameter), named in DS3_THL2_NEEDS.md.
