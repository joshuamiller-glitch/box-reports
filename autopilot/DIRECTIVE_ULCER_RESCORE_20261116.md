INBOX ORDER 20261116_2028Z_use-ulcer-rescore-now (research only)

Your step-1 calibration settles it: the old rule detects a real 10% or
20% drawdown cut only 12-13% of the time. Every "not confirmed" issued
today under it is void as a negative result. Act on your own finding:

1. From now on the PRIMARY drawdown statistic is the ulcer index (RMS of
   daily drawdown), which you measured at 49 / 72 / 97% power for 5 / 10 /
   20% cuts at about 3.5% false positives. Keep max DD, worst week and
   the resampled-drawdown table beside it, but tiers are decided on ulcer
   + mean.

2. FOR THE 21:00Z PAGE (do not wait for the 30-draw runs): re-score every
   candidate that has engine results, using what already exists:
   - ulcer index change vs JL2 in HOLD and L6M (and L3M where present);
   - its percentile among whatever controls have landed (say how many);
   - week-clustered bootstrap: P(ulcer lower), P(max DD shallower),
     90% interval of the mean change;
   - tier under the calibrated rule: CONFIRMED / LEAD / FAIL / NOT ENOUGH
     CONTROLS YET.
   Candidates: M7 London cap 3; give-back H7 Asia, H7 NY AM, K7 NY AM,
   P7 Asia, P7 NY AM; A7 Asia target 45; against-the-day VWAP skip;
   against-the-day target 20 (M7, O7 NY AM); U7 Asia 40x40; the three
   profit lines as designed vs as coded; the five fixed bracket cells
   from this morning (A7 Asia 40x40, K7 NY AM 40x40 and 40x60, K7 London
   40x60); London skip k=1.25 true points.
   One table, old verdict beside new verdict. Put it at the TOP of
   DS3_BRACKET_DD_BUILD.md and in DS3_PASS_RULE.md.

3. Mean effects: your plants of +3% / +6% mean were undetectable. State
   what size of mean effect IS detectable at 80% power in HOLD + L6M, so
   the user knows the floor. If it is large, say plainly that small mean
   gains cannot be proven on 12 months and need the full 43 months or
   live incubation.

4. Queue the 30-draw controls for the candidates in the order of their
   new tier (LEAD and near-CONFIRMED first), on server 2.
