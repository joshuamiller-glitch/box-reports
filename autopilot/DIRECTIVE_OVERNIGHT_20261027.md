# DIRECTIVE (user, 2026-10-27) OVERNIGHT PROGRAM 2026-10-27 -> 10-28 13:00Z
(Saved by lead. Account ids in the original paste replaced by [ACCT-ST/HM live book] and [ACCT-DS3 book] per the no-account-numbers rule; everything else verbatim.)

The box runs through the night on this list, in this order, memory-aware. Same V2 rules throughout (preregs <= 30 cells, both placebos, one holdout look per group, equal-risk, mix-into-stack, never-empty-handed reporting). Nothing goes live from this file; sizing/lock/block rules are flagged "live-eligible once scored" per the user's rule.

## Memory plan (the binding constraint, not CPU)
Replay workers (L2) capped at the memguard's stable count; everything else is CPU-only scoring on existing series. Order the replays strictly: (R1) DN 10-lot stop-fill study, (R2) CRT cross-instrument, (R3) near-target repricing, (R4) the un-block replays. CPU-only items (A, B, C, E, F, G) run concurrently with the replays. If free memory drops under 8 GB, pause R2-R4, never A-G. No worker kills on replay months; stale-marker check every 30 min (the 21:17Z failure must not recur).

## A. T-OPEN blocks (ii)-(iv), the families that matter most - all cores not used by replays
Score the remaining T-OPEN families on the D3O1 harness with the same bracket core and the three placebos: 3.1 opening-range breaks (all OR lengths x break definitions, stop-entry mapped + tape-through variant), 3.2 drive continuation, 3.5 first pullback, 3.6 level interaction (ON H/L, PM H/L, prior-day H/L/C, VA, naked POC, weekly/monthly opens, confluence), 3.7 IB/TPO, 3.10 footprint triggers and 3.11 L2 confirmations on the top cells; then block (iii) (full section-4 grid on the top 3 per family) and (iv) (opening-type and pre-open-feature interaction tables, the 09:29 classifier with V2 guards and the gated-P&L test). Un-block comparison on every block. Interim report every 2 h (DS3_OPEN_B2_<family>.md), DS3_OPEN_FINAL.md as the never-empty-handed final by 12:00Z.

## B. T-CLOSE blocks 2-5 + RVW1 robustness
Families 3.4 closing-range breaks, 3.5 end-of-day dip/rip into the overnight hold, 3.6 post-close 16:00-16:30, 3.7 levels into the close, 3.8 cross-asset, 3.9 footprint, 3.10 L2; the section-4 grid on the top 3; the full robustness block on RVW1|F30 (full parameter surface for z {0.75, 1.0, 1.25, 1.5} x bracket {20, 30, 40} x entry time {15:15, 15:30, 15:45}, day-block bootstrap maxDD, VIX terciles, by year, fill sensitivity, 2x cost, mirror, correlation to every live book, stack-add with the concurrency replay). Also the per-bracket-class best-of-N null the block-1 lead asked for (decision: adopt it as a secondary verdict column, do not alter the harness primary). DS3_CLOSE_FINAL.md by 12:00Z.

## C. The DN question - this decides 6 lots of the live-candidate book (CPU-light + replay R1)
10-lot stop-fill study on the real mbp-10 book: for all 4,806 DN stop orders, walk the book at the trigger second with 10 lots (and 14), report fill price vs level by hour (08:30, 09:30, quiet), by VIX tercile, by first-print size; the break-even is +4.7 pts/trade - give the measured slippage distribution and the re-scored WF/HOLD/2023 at 8 and 14 lots.
KB vs DN substitution: paired on the overlapping signals (same side within +-15 min), the stack at KB/DN splits {13/0, 8/5, 5/8, 0/13} with the exact lock engine; which split has the best HOLD maxDD per $ of mean. Report whether the two are substitutes (correlation of their weekly series, share of common entries) and which one the out-of-sample solve prefers at each cap.
DN order churn: 173 submissions/day - any exchange messaging or broker limit implication; note only.

## D. Block / un-block rules on the existing books (live-eligible once scored; replay R4, cheap)
The un-block of 09:30-09:59 was worth +$5.8k/wk in the open harness. Score as sizing/block cells on the full DS2+DS3 stack with exact locks: (a) un-block 09:30-09:59 for {ST, HM, KB, SM, PE} individually and all; (b) un-block 09:00-09:29; (c) un-block 15:00-16:54 (flat still at 16:55); (d) the 18:00-18:04 block on/off; (e) the FOMC-day NY block; each paired by week vs the live windows, placebo = shifted windows, holdout, 2023 span, by year. Verdict line names the single best-supported window change.

## E. Trade Health loss-side - the user's standing question, on the books that run it now
Paired on identical entries, direct basis where the series exists: the live TH-loss rule (15 pts / 3 of 3 / 30 s) on KB, SM, PE, DN, MV, MA and on the dip-buy basket legs (NQ/ES/RTY, where TH is the only exit before the time exit), plus the time-only and MAE-only controls, by session and by year; and the FORWARD evidence: the live [ACCT-ST/HM live book] ST book's TH cuts since 10-20 (counterfactual to the uncut bracket from the 1-s tape). One table, one verdict per book, and the honest line on whether the forward sample can distinguish anything yet.

## F. Sizing by regime (priority item 6 - live-eligible once scored; CPU-only)
On the DS2+DS3 stack and on the DS5 mix (KB 5, DN 8, SM 7, PE 5, MV 4): (a) the compression forecaster as a lot multiplier {0, 0.5, 1.0 in quiet} x {1.0, 1.5 in wide}; (b) vol-scaled lots (constant weekly $ SD per book, 4-week and 8-week lookbacks); (c) VIX-tercile lots; (d) day-of-week lots; (e) the "2023 fix": for every CANDIDATE that fails only the 2023 span (MV, KB20_S, DON widenings, PE), characterise 2023-04..2024-01 (realised vol, trend persistence, ATR ratio) and test whether (a)-(c) would have cut the 2023 loss while keeping 2024-26. Paired by week, placebo = shifted regime labels, holdout, by year. Verdict line names the one sizing rule best supported for live, with its weekly mean / SD / maxDD / worst-week deltas.

## G. Forward register and the Sim books (bookkeeping, CPU-only)
Score W44 to date for [ACCT-ST/HM live book] (ST/HM), DS3 (KB/SM/PE on [ACCT-DS3 book]), DS4 and DS5 (paper) against expectation from the live files; flag any book whose trades/wk is outside its 4-week band; add the DS5 mix as a registered portfolio row with the T-PORTFOLIO expectation; note the DS4/DS5 tick-routing incident (bogus stop touches before v1.3) and exclude those trades from identity scoring.

## H. If anything above finishes early
(1) CRT cross-instrument re-score (R2) if memory allows; (2) T-PBX block (iv) tape-defined pullback ends on the top cells; (3) the structure-bracket cells on PB3B entries (stop below the pullback low, targets prior high / 1.618) that T-PBX block (i) left mapped; (4) MAMA widening (bar 5/10/15 x fast/slow limits) since MAMA is the one PASS with ~0 correlation.

## Reporting
MORNING.md every 2 h with: per-item status, cells scored, best cell so far, slots and memory, ETA. 13:00Z edition = the morning brief: for each item one line - verdict, best cell, what it would change in DS3/DS5, and the one number the user should look at. Finals written as never-empty-handed (top 10 regardless of verdict, failed gate and MDE, recommended-for-Sim cell with spec where one exists). No gate loosened; every holdout look logged.
