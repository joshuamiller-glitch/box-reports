INBOX ORDER 20261116_1954Z_calibrate-the-pass-rule (research only)
Priority: beside the 21:00Z deadline work on server 1; use server 2 for the
extra draws. Applies to every study from now on.

The pass rule written this morning ("real cell beats ALL 6 controls on
stack max DD in HOLD AND L6M, mean not worse than -5%") was written in a
hurry and is probably too blunt. Max DD is decided by a few weeks and is
noisy; six draws cannot place a result in a distribution; and some
controls are the wrong kind. Fix it before more verdicts are issued.

1. CALIBRATE THE CURRENT RULE AGAINST KNOWN ANSWERS (first, small):
   through the exact engine on JL2, HOLD and L6M:
   a. planted edges of realistic size: a rule that truly removes 5%, 10%
      and 20% of stack max DD at flat mean, and one that adds +3% / +6%
      mean at flat DD (plant from each signal's own future R, as in the
      existing planted-edge checks), 20 seeds each;
   b. pure noise rules with the same skip / exit / size frequency,
      20 seeds.
   Report: share of planted seeds that PASS the current rule (power) and
   share of noise seeds that pass (false positives). If power for the
   10% DD plant is under 50%, the rule is rejecting real effects: say so
   plainly.

2. REPLACE "BEATS ALL SIX" WITH A PERCENTILE:
   at least 30 control draws per candidate (server 2), report the real
   cell's percentile among them on (a) max DD, (b) worst week, (c) mean,
   per window. No single-draw comparisons.

3. JUDGE DRAWDOWN BY RESAMPLING: week-clustered bootstrap (2,000
   resamples of the weekly P&L difference path): P(max DD shallower),
   P(worst week better), 90% interval of the mean change. Report beside
   the percentile.

4. RIGHT CONTROL FOR EACH FAMILY (persistent draw throughout):
   - skip rules: random skip, same keep share, same book x session;
   - exit rules (give-back, partial, trail, target change): a random exit
     with the same share of trades exited early and the same distribution
     of minutes-since-entry and open profit at exit; NOT "the same rule on
     half the trades", which is a diluted copy of the rule, not a control;
   - condition-based rules (against-the-day, squeeze, tape speed): the
     real rule with the condition label shifted 11 / 23 / 37 sessions and
     with shuffled labels;
   - count rules (M7 London cap): random block with the same block rate
     after the same number of closes.
   Measure and print each control's realised frequency vs the real rule;
   more than 0.05 apart = invalid, redraw.

5. TIERS instead of one gate (the user's standard is tolerant: recent
   must work, older may be a little worse):
   CONFIRMED: >= 90th percentile on DD or on mean in L6M and L3M, the
     other not below the 40th; P(DD shallower) >= 0.80; not below the
     25th percentile on DD in HOLD and the older windows.
   LEAD: >= 75th percentile on DD or mean in the recent windows, nothing
     below the 25th.
   FAIL: below that.
   Run the step-1 plants and noise through THESE tiers too and report
   power and false-positive rate for each tier. Adjust the cut-offs so
   noise reaches CONFIRMED under 5% of the time, and report the cut-offs
   you ended with.

6. RE-SCORE today's candidates under the corrected rule and show old
   verdict beside new: M7 London cap 3; give-back H7 Asia, H7 NY AM,
   K7 NY AM, P7 Asia, P7 NY AM; A7 Asia target 45; against-the-day by
   session VWAP skip; against-the-day target 20 (M7, O7 NY AM); U7 Asia
   40x40; London skip k=1.25 true points; the three profit lines as
   designed vs as coded.
   Page: autopilot/DS3_PASS_RULE.md. Step 1 result in the 21:00Z note if
   it is in; steps 2-6 as they land, first table by 23:30Z.
