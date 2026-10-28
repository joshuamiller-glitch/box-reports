T-STACK — fix the stack where the audit says it loses (2026-10-28, after DS3_DIV2_A_AUDIT)

Research only. No live, execution-server or chart change. UNTOUCHED never read. Redact account ids. These are sizing / lock / block / timeframe rules on the EXISTING books, so per the user's standing rule they are live-eligible once scored; nothing goes live from this file.

The audit (DS3_DIV2_A_AUDIT): the stack loses on 48% of days; 64% of losing-day dollars are range days; losses concentrate in 12 of 46 half-hour entry slots; the 20 worst weeks (-$3.5M at 10-lot scale) are chop weeks where every book but SM loses together; the stack earns 55% of its P&L in the lowest-ATR tercile, so "skip quiet days" is the wrong lever. Every program that tried to ADD a book to fill this is 0 for ~300 cells. This program instead changes how the stack itself behaves on those days, slots and weeks. Selection discipline is the whole game here: every slot, threshold and day-type is chosen on PRE only (2024-02..2025-06), written to the prereg before HOLD is read, and the placebo is the same rule with shifted/random slots, thresholds or labels. Paired by week vs the unchanged stack, exact lock engine, MDE beside every mean, by year, 2023 span. F = total cells across the program for best-of-N.

A. Slot rules (the 12 loss slots)
Re-derive the loss slots on PRE only (do not reuse the audit's list, which saw all data): per book and pooled, the half-hour entry slots whose PRE mean is negative with CI below 0 (and a looser list: negative point estimate, >= 30 trades).
Cells: block entries in the PRE slots (strict list / loose list) per book and all; halve lots in those slots; block only when the slot is also a range-day (first-hour range < 0.7x 20-day median, known by 10:30 for RTH slots). Placebo: block 12 random slots (200 draws), shifted-by-one-slot. Report what the block does on HOLD, in the 20 worst weeks, and whether the blocked slots are the same slots in HOLD (stability table: PRE-negative slots that stay negative in HOLD, with the binomial null).

B. Range-day rules (the 64%)
Ex-ante range-day labels that exist by 10:00/10:30 ET: first-30/60-min range vs 20-day median (< 0.5, 0.7, 0.85x), overnight range vs median, first-hour close-to-open vs range (< 0.3 = overlap), number of 1-min bar direction flips in the first hour, ES/NQ first-hour agreement. Cells (<= 12): on a flagged day, from 10:30, (a) halve all trend books, (b) stop new entries on trend books, (c) raise TH-loss threshold / widen nothing — exits are dead, so no exit cells; (d) SM unchanged while others halved (the audit's SM exception, tested not assumed). Also the ex-post reference (what perfect range-day knowledge would be worth) so the ex-ante rules are judged as a share of it. Placebo: shuffled day labels. Include the Friday/opex/holiday-eve variants as separate cells only if PRE flags them.

C. Chop-week rules (the 20 worst weeks)
Week-level de-risking triggered by the stack's own state, known at the time: (a) stack P&L week-to-date below -X (X = 1, 1.5, 2 x the stack's weekly SD) -> halve lots for the rest of the week (and: block until Monday); (b) N consecutive losing days (2, 3); (c) stack drawdown from its 20-day equity high > Y -> lots x 0.5 until recovered (the equity-curve rule, 20/40/60-day variants); (d) count of TH cuts + stop-outs in the last 2 days above its PRE 80th percentile -> halve; (e) the opposite sign for (c) as the control (size UP in drawdown) so the direction of the effect is shown, not assumed. Cells <= 15. Report mean, SD, maxDD, worst week, worst-20-weeks $, by year; the explicit trade-off line: dollars given up in good weeks vs dollars saved in bad ones, and the lot-matched version.

D. Same-direction concurrency (all books lose together)
Stack-level caps the books do not have today: max total lots in one direction (20, 30, 40 at the 10-lot scale), max books in one direction (2, 3, 4; later books skipped or halved), and "first book in a direction takes the slot" vs "largest edge book keeps it" (edge rank from PRE). Exact lock engine, concurrency on the 1-s path. Cells <= 9. Report the share of entries affected and what the cap does in the worst 20 weeks vs the best 20.

E. Timeframe of the trend books (SM survives chop; the others do not)
Test whether slower bars make a trend book chop-resistant without losing the trend weeks: KB on 3/5/10-min (3 is live), PE regime on the 5/10/15-min Supertrend (5 is live), ST on 1/3/5-min (1 is live), HM on 1/3/5. Cells <= 12, each paired vs its live-bar sibling, exact engine, direct basis where the series exists. Report per book: weekly mean, worst-20-weeks $, correlation to SM, and the mix question — does the stack with the slower sibling replacing or added to the fast one improve worst-20-weeks without losing WF mean.

F. Combine (only cells that pass A-E individually)
The best one rule from each of A-E, stacked in order of PRE effect, each added only if HOLD worst-20-weeks improves and HOLD mean does not fall by more than its MDE; placebo for the combination = the same number of random rules. Verdict line: the stack as it is vs the stack with the rule set — WF mean, SD, maxDD, worst week, worst-20-weeks $, by year, 2023 span — and the plain sentence "these rules would have turned the worst 20 weeks from -$X to -$Y and cost $Z/wk in the other weeks."

G. Spec for anything live-eligible
Each surviving rule as a one-paragraph plain-English rule plus the exact parameters (ET times, thresholds, lot multipliers, which books), codeable into DualStrat2/DS3/DS5 as a sizing/block layer without reading the study, with its DualStrat2 vs DS3 vs DS5 applicability stated.

Reporting
DS3_STACK_A..F.md never-empty-handed (top cells regardless of verdict, failed gate, MDE, stability tables); MORNING.md every 2 h; DS3_STACK_FINAL.md with the F verdict line and the G specs. Use all cores; CPU-only except the E direct replays (memory-aware, lowest priority).
