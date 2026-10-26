# IDEAS_FV15 - five new pre-registered family ideas (no running; for dispatch)

Written 2026-10-17 by the ICT/FV worker. Novelty check: each idea was grepped (case-insensitive keywords below) against LEDGER.md, GAPMAP.md, BACKLOG.md, BACKLOG2.md and every autopilot/REPORT_*.md; zero hits unless stated. Every idea would run through the standard machinery (clean-only selection 2023-08..2025-07, H1/H2 read once, own timing-destroyed null 200 replicates, family-level selection-corrected null, plateau +-25%, 2x slippage, ERA flag, worst-decile corr <= +0.30, library save), in both the sleeve framing (ap_ict_stage2/verify) and the live-pair framing (ap_pz_core.pipeline2 with the 8/8 pair as base). Nothing below has been run.

## I1. Realised semivariance asymmetry (signed jump variation)
- Mechanism: the balance of upside versus downside squared 5-minute returns over the trailing 1-3 hours (RS+ minus RS-, divided by RV) measures whether recent variance came from jumps up or down. Asymmetric jump arrival clusters (news/flow bursts decay slowly), so the sign of the semivariance imbalance may predict the next 30-240 minutes beyond plain return momentum; unlike return momentum it is robust to a single large bar. Used as a sleeve (continue or fade with a 1.5 ATR stop, time exit 60/120/240 min) and as a pair tilt/switch at the flip (aligned imbalance).
- Data: 1-min NQ/ES/RTY/YM on disk (2023-26, plus 2013-22 for the ERA flag via data/autopilot/ohlcv1m). No purchase.
- Grid: window {60,120,180} min x sampling {1,5} min x threshold {0.2,0.4,0.6} x {continue, fade} = 36 setups per instrument; family null across the 36.
- Novelty grep: "semivar|realized skew|jump asymmetr" zero hits (SW27 is claimed for single-bar jump shocks, which is a different statistic).

## I2. Volume-clock bars for structure detection
- Mechanism: information arrives in proportion to traded volume, not clock time; time-bar ATR and bar counts are distorted by the intraday volume cycle (the 03:00-08:00 ET lull and the 09:30/15:00 surges). Rebuilding the detectors with equal-volume bars (bar closes every V contracts, V = k x trailing 20-day median 1-min volume x tf minutes) gives impulses, swings and breakouts whose size distribution is stationary across the day; the question is whether an unchanged rule (3-bar impulse, 20-bar swing breakout, 5-bar trend) has more edge in volume time than in clock time at the same average bar count.
- Data: 1-min volume on disk (series_*.npz volume field); tick-level volume-clock only needed for tick replay (NQ trades on disk 2023-26).
- Grid: three rule archetypes x k {0.5,1,2} x {long/short symmetric} = about 27 setups; the null is the same rule in time bars with matched trade counts (timing-destroyed) plus a volume-shuffle null (bar boundaries moved randomly, volume totals preserved).
- Novelty grep: "volume bars|dollar bars|volume-time|equal-volume|event-time" zero hits.

## I3. Open-type classification at the RTH open (Dalton-style open drive / test-drive / rejection-reverse / auction)
- Mechanism: the character of the first 5-30 minutes relative to the overnight range and the prior-day value area (price accepted or rejected outside it, one-time-framing versus overlapping bars) separates days with trend-type auction from rotational days; trend days carry the day's range, rotational days mean-revert. Deterministic rules classify the open at 10:00 ET into four types from the 09:30-10:00 bars, then the type conditions (a) a sleeve entry at 10:00 (with/against) with time exit at 15:30, and (b) the pair's size on that day (day-level tilt, no intraday look-ahead).
- Data: 1-min on disk (overnight range, prior-day value area from 1-min volume-at-price); ERA flag available from 2013.
- Grid: 4 open types x {with, against} x {sleeve stop 1.0/1.5 ATR} x {hold to 13:00, 15:30} = 32 setups; type definitions fixed ex-ante (no tuning).
- Novelty grep: "open drive|dalton|open type|open-auction|market profile|TPO" zero hits.

## I4. Time-symmetry pullback trigger (duration instead of depth)
- Mechanism: IMP3 and the FVG line trigger on price depth (limit at 50% of the move); a different anchor is elapsed time: corrections often last a stable fraction of the impulse duration. A market-on-trigger entry once the correction has lasted k times the impulse duration (k in {0.5,1,1.5}) and has retraced at least 25% (so it is a pullback, not a pause) tests whether the timing axis carries information that the depth axis does not, with the depth-permutation null replaced by a duration-permutation null (durations permuted among setups).
- Data: 1-min on disk; ERA 2013-22 available.
- Grid: impulse definition fixed at the IMP3 primary (so no new impulse tuning), k x 3 min-retrace levels x 2 stop rules = 18 setups. Because it reuses the IMP3 impulse it must be reported against the IMP3 family null and counted as one additional selection round.
- Novelty grep: "time symmetry|price-time|swing duration|correction duration" zero hits.

## I5. Initial-balance (first-hour) extension asymmetry
- Mechanism: the 09:30-10:30 range (initial balance) is the day's first accepted value area; a break and hold outside it, measured by the number of closes beyond and the volume on the break, predicts range extension, while a failed break (close back inside within N minutes) predicts a rotation to the opposite IB edge. Sleeve: enter on the confirmed break (with) or on the failed break (against), stop at the opposite side of the break bar, exit at the IB-range multiple or 15:55; pair use: day-level tilt after 10:30 (size for the afternoon flips).
- Data: 1-min on disk; ERA from 2013.
- Grid: IB length {30,60} x confirmation closes {1,2,3} x action {break-with, failed-break-against} x target {1,1.5 IB range} = 24 setups.
- Novelty grep: "initial balance|IB break|IB extension" zero hits (opening-range 30-minute rules exist in the ICT and earlier work and are a different, shorter anchor; ORB tests do not condition on hold/failure).

## Notes for dispatch
- I2 and I4 are mechanism changes of the FVG/IMP3 line (volume axis, time axis); the coordinator has declared that line exhausted for price-depth variants, so run them only as the explicit time/volume-axis tests above and count each as one selection round in the family null.
- I1, I3 and I5 are independent of the FVG line and can be dispatched in parallel; each needs about 1.5 hours with up to 8 cores.
