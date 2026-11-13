# DS3_NEAR_ZONE_2 - T-NEAR-ZONE worker W-N2: families k l r s t u v and the near-zone JOINT stage (page written Fri Nov 13 06:00:52 UTC 2026)

STATUS: Shadow only, first-order on the LPB_BASE stored 1-s paths (43 months; L6M = 2026-05-12..10-30, 24 weeks), post-hoc, no PASS claims. Exact engine rows for the live-replayable joint finalists are queued (section 7); nothing on this page is exact yet unless section 7 says so. Prereg: NEAR_ZONE_2_PREREG.md (sha in DECISIONS.md, logged before any k/l/r/s/t/u/v cell was scored). W-N's page with families a-g and h-q is DS3_NEAR_ZONE.md; this page uses its kernel, its fill models and its definitions unchanged.

Definitions (same as W-N): d = new P&L minus live-rule P&L per trade; net = removed (give-backs, fired non-fills that had reached 80% of target) minus clipped (fired trades that filled the target under live rules) plus other saves (fired non-fills outside the 80% zone); give-back event = MFE >= 80% and closed below 50% of target; round-trip = closed <= breakeven; strict trader test = no trade that reached 90% closes below 50% and none that reached 80% closes at or below breakeven. Key = min(net L6M, net 43 months) per week; for the learned exit the second number is the out-of-sample 2024+ weekly net. Market exit = next-second mid minus 1.2 pt (the profit-side take slip is unmeasured; 0.57 / 1.6 not re-run here); resting stop-limit floors and passive limits are optimistic upper bounds. P7 is shown first at 12/7/7 lots (P7x) and also at the installed 7/4/4.

## 0. EXACT VERDICT (supersedes section 1, which is first-order and overstated)

Exact L6M (6 of 6 months, engine with the live panel base) is the verdict. First-order overstated every P7 12/7/7 joint set: B1 (spread + two s rules) +4,679 first-order became -2,537 a week exact, B2 -1,236, D3 -6,046, the learned-exit set V1 -7,478; only the single s rule (C4, same-side book took a target within 600 s, arm 0.7 take) stays positive at 12/7/7, +2,950 a week exact against +6,113 first-order. The reason is the entry stream: early exits free the book, which re-enters, and the first-order frame cannot see that. Small books: K7 B1/D2 +1.2k exact (first-order -188 / -70: sign flipped, one window, not trusted), U7 C4 +1,038, others within +-700. Exact rows: all sets above for L6M; HOLD, PRE and X' months for the P7 12/7/7 sets B1, B2, D3, S5, V1 are queued (feeder pid in section 8) and are NOT exact until the table in section 7 shows 12 / 29 months. Not exact: all h-q families (no engine order hooks), W-N's staggered / move-target / touched-not-filled rows (W-N's page owns them), every first-order table on this page.

Scorecard note: the stack reference (LPB_BASE) has 9.1 give-backs and 9.0 round-trips a week across all seven books; a P7-only rule can remove at most the P7 share (about 2 a week), so 7.0-7.2 a week left is the other six books plus the entries the rule changed. NearTarget exits are counted as clip-type by the tool; give-backs removed are visible as the drop from 9.1.

- NEAR_N2_P7x_B1 (P7): EXACT L6M stack -2537 $/wk vs reference, rule book -2537 $/wk, stack maxDD cut 20.8%, 417 NearTarget exits; give-backs 7.2/wk, round-trips 7.0/wk (stack, scorecard);
- NEAR_N2_P7x_B2 (P7): EXACT L6M stack -1236 $/wk vs reference, rule book -1236 $/wk, stack maxDD cut 3.3%, 437 NearTarget exits; give-backs 7.0/wk, round-trips 7.0/wk (stack, scorecard);
- NEAR_N2_P7x_D3 (P7): EXACT L6M stack -6046 $/wk vs reference, rule book -6046 $/wk, stack maxDD cut 0.1%, 386 NearTarget exits; give-backs 7.2/wk, round-trips 7.0/wk (stack, scorecard);
- NEAR_N2_P7x_C4 (P7): EXACT L6M stack +2950 $/wk vs reference, rule book +2950 $/wk, stack maxDD cut 14.2%, 176 NearTarget exits; give-backs 7.7/wk, round-trips 7.6/wk (stack, scorecard);
- NEAR_N2_P7_B1 (P7): EXACT L6M stack -627 $/wk vs reference, rule book -627 $/wk, stack maxDD cut 38.5%, 676 NearTarget exits; give-backs 7.1/wk, round-trips 7.0/wk (stack, scorecard);
- NEAR_N2_P7_B2 (P7): EXACT L6M stack -692 $/wk vs reference, rule book -692 $/wk, stack maxDD cut 37.6%, 679 NearTarget exits;
- NEAR_N2_P7_D3 (P7): EXACT L6M stack -1779 $/wk vs reference, rule book -1779 $/wk, stack maxDD cut 24.6%, 613 NearTarget exits; give-backs 7.2/wk, round-trips 7.0/wk (stack, scorecard);
- NEAR_N2_P7_C4 (P7): EXACT L6M stack +666 $/wk vs reference, rule book +666 $/wk, stack maxDD cut 26.0%, 260 NearTarget exits; give-backs 8.4/wk, round-trips 8.3/wk (stack, scorecard);
- NEAR_N2_K7_B1 (K7): EXACT L6M stack +1159 $/wk vs reference, rule book +602 $/wk, stack maxDD cut 11.7%, 636 NearTarget exits; give-backs 5.9/wk, round-trips 5.8/wk (stack, scorecard);
- NEAR_N2_K7_D2 (K7): EXACT L6M stack +1212 $/wk vs reference, rule book +654 $/wk, stack maxDD cut 12.6%, 458 NearTarget exits; give-backs 6.0/wk, round-trips 5.8/wk (stack, scorecard);
- NEAR_N2_K7_C3 (K7): EXACT L6M stack +30 $/wk vs reference, rule book +30 $/wk, stack maxDD cut -0.0%, 12 NearTarget exits; give-backs 9.1/wk, round-trips 8.8/wk (stack, scorecard);
- NEAR_N2_M7_B1 (M7): EXACT L6M stack -234 $/wk vs reference, rule book -234 $/wk, stack maxDD cut -1.4%, 306 NearTarget exits; give-backs 7.2/wk, round-trips 7.1/wk (stack, scorecard);
- NEAR_N2_M7_D2 (M7): EXACT L6M stack -266 $/wk vs reference, rule book -266 $/wk, stack maxDD cut -0.0%, 282 NearTarget exits; give-backs 7.2/wk, round-trips 7.1/wk (stack, scorecard);
- NEAR_N2_M7_C3 (M7): EXACT L6M stack +113 $/wk vs reference, rule book +113 $/wk, stack maxDD cut 1.3%, 9 NearTarget exits; give-backs 9.0/wk, round-trips 8.8/wk (stack, scorecard);
- NEAR_N2_U7_B1 (U7): EXACT L6M stack +166 $/wk vs reference, rule book +166 $/wk, stack maxDD cut 7.5%, 143 NearTarget exits; give-backs 8.4/wk, round-trips 8.3/wk (stack, scorecard);
- NEAR_N2_U7_B2 (U7): EXACT L6M stack +156 $/wk vs reference, rule book +156 $/wk, stack maxDD cut 7.5%, 143 NearTarget exits; give-backs 8.4/wk, round-trips 8.3/wk (stack, scorecard);
- NEAR_N2_U7_D3 (U7): EXACT L6M stack -653 $/wk vs reference, rule book -653 $/wk, stack maxDD cut -7.8%, 145 NearTarget exits; give-backs 8.5/wk, round-trips 8.4/wk (stack, scorecard);
- NEAR_N2_U7_C4 (U7): EXACT L6M stack +1038 $/wk vs reference, rule book +1038 $/wk, stack maxDD cut 9.7%, 113 NearTarget exits; give-backs 8.6/wk, round-trips 8.5/wk (stack, scorecard);
- NEAR_N2_H7_B1 (H7): EXACT L6M stack -78 $/wk vs reference, rule book -100 $/wk, stack maxDD cut -1.1%, 80 NearTarget exits; give-backs 8.6/wk, round-trips 8.5/wk (stack, scorecard);
- NEAR_N2_A7_B1 (A7): EXACT L6M stack +703 $/wk vs reference, rule book +237 $/wk, stack maxDD cut 0.5%, 191 NearTarget exits; give-backs 8.4/wk, round-trips 8.3/wk (stack, scorecard);
- NEAR_N2_O7_B1 (O7): EXACT L6M stack -15 $/wk vs reference, rule book -15 $/wk, stack maxDD cut 0.5%, 11 NearTarget exits; give-backs 9.0/wk, round-trips 9.0/wk (stack, scorecard);
- NEAR_N2_P7x_S5 (P7): EXACT L6M stack -1804 $/wk vs reference, rule book -1804 $/wk, stack maxDD cut 17.4%, 437 NearTarget exits; give-backs 7.2/wk, round-trips 7.0/wk (stack, scorecard);
- NEAR_N2_P7_S5 (P7): EXACT L6M stack +1311 $/wk vs reference, rule book +1311 $/wk, stack maxDD cut 33.8%, 625 NearTarget exits; give-backs 7.3/wk, round-trips 7.0/wk (stack, scorecard);
- NEAR_N2_P7x_V1 (P7): EXACT L6M stack -7478 $/wk vs reference, rule book -7478 $/wk, stack maxDD cut -10.5%, 389 NearTarget exits; give-backs 7.2/wk, round-trips 7.1/wk (stack, scorecard);

## 1. Headline (plain sentences) - FIRST-ORDER, see section 0

- **P7 at 12/7/7 lots** (live-replayable joint set B-best: u: spread>=3 ticks arm=0.8 persist=3 + s: same-side target exit <=300 s ago arm=0.7 take + s: same-side book took target (<=600 s) arm=0.7 take): per week on L6M it removed 22427 give-back dollars and clipped 23539 dollars of fills (18.0 fills a week), net +4679 a week on L6M and +1552 a week over 43 months; give-back events fall from 2.05 to 0.04 a week and round-trips from 2.05 to 0.04; the strict trader test does not pass (1 trade(s) that reached 90% still close below 50%, 1 that reached 80% close at or below breakeven, against 24 and 50 under live rules). Stack drawdown cut 25.9% on L6M.
- **P7 at 7/4/4 (installed)** (live-replayable joint set B-best: s: same-side target exit <=300 s ago arm=0.7 take + a: ladder m1=0.7 f1=0.65 / .9 f2=0.7 / .95 f3=0.9 mode=1 + t: clock m_sessch<=40min arm=0.9 take): per week on L6M it removed 12098 give-back dollars and clipped 18489 dollars of fills (17.0 fills a week), net +2661 a week on L6M and +893 a week over 43 months; give-back events fall from 2.05 to 0.04 a week and round-trips from 2.05 to 0.00; the strict trader test does not pass (1 trade(s) that reached 90% still close below 50%, 0 that reached 80% close at or below breakeven, against 24 and 50 under live rules). Stack drawdown cut 55.1% on L6M.
- **K7** (live-replayable joint set B-best: a: ladder m1=0.8 f1=0.65 / .9 f2=0.7 / .95 f3=0.7 mode=1 + s: same-side book took target (<=600 s) arm=0.7 take): per week on L6M it removed 6513 give-back dollars and clipped 7850 dollars of fills (18.5 fills a week), net -188 a week on L6M and -778 a week over 43 months; give-back events fall from 3.19 to 0.08 a week and round-trips from 3.19 to 0.00; the strict trader test does not pass (1 trade(s) that reached 90% still close below 50%, 0 that reached 80% close at or below breakeven, against 36 and 78 under live rules). Stack drawdown cut 4.5% on L6M.
- **M7** (live-replayable joint set B-best: a: ladder m1=0.8 f1=0.65 / .9 f2=0.8 / .95 f3=0.8 mode=1 + t: clock m_sessch<=5min arm=0.8 take + s: same-side target exit <=180 s ago arm=0.7 floor.6): per week on L6M it removed 3682 give-back dollars and clipped 3807 dollars of fills (8.5 fills a week), net +441 a week on L6M and -135 a week over 43 months; give-back events fall from 1.92 to 0.08 a week and round-trips from 1.92 to 0.00; the strict trader test does not pass (2 trade(s) that reached 90% still close below 50%, 0 that reached 80% close at or below breakeven, against 23 and 47 under live rules). Stack drawdown cut 5.4% on L6M.
- **U7** (live-replayable joint set B-best: a: ladder m1=0.7 f1=0.65 / .9 f2=0.7 / .95 f3=0.7 mode=1 + a: ladder m1=0.7 f1=0.65 / .9 f2=0.8 / .95 f3=0.8 mode=1 + k: absorb aggw10>=3.7 & d_prog10<=4 arm=0.8 persist=1 floor.6): per week on L6M it removed 3317 give-back dollars and clipped 4551 dollars of fills (4.4 fills a week), net +758 a week on L6M and +100 a week over 43 months; give-back events fall from 0.65 to 0.00 a week and round-trips from 0.65 to 0.00; the strict trader test PASSES. Stack drawdown cut 15.5% on L6M.
- **H7** (live-replayable joint set B-best: b: rev arm=0.8 X=4 N=5): per week on L6M it removed 1444 give-back dollars and clipped 1293 dollars of fills (2.5 fills a week), net +152 a week on L6M and +130 a week over 43 months; give-back events fall from 0.53 to 0.00 a week and round-trips from 0.53 to 0.00; the strict trader test PASSES. Stack drawdown cut 1.4% on L6M.
- **A7** (live-replayable joint set B-best: r: es_dd300<=-2 bps arm=0.8 persist=3 + a: ladder m1=0.8 f1=0.65 / .9 f2=0.7 / .95 f3=0.9 mode=1 + s: same-side book took target (<=600 s) arm=0.7 take): per week on L6M it removed 1115 give-back dollars and clipped 1857 dollars of fills (5.7 fills a week), net -221 a week on L6M and -163 a week over 43 months; give-back events fall from 0.65 to 0.00 a week and round-trips from 0.65 to 0.00; the strict trader test PASSES. Stack drawdown cut -2.1% on L6M.
- **O7** (live-replayable joint set B-best: c: flow pulled_against_mult>=20 arm=0.8 persist=3 dd>=2 + s: opposite-side signal in 120 s arm=0.7 take): per week on L6M it removed 137 give-back dollars and clipped 155 dollars of fills (0.3 fills a week), net -17 a week on L6M and -22 a week over 43 months; give-back events fall from 0.12 to 0.00 a week and round-trips from 0.04 to 0.00; the strict trader test PASSES. Stack drawdown cut 0.6% on L6M.

What the families say. (1) The tape does not predict a reversal near the target better than the position of the price itself. The learned exit (section 4) gets out-of-sample AUC 0.77-0.78 for "target fills before price retraces to 50%", and about 0.77 of that is carried by where the trade is (distance to the target, MFE, drawdown from the high, seconds since the high, seconds in the zone); adding any feature group moves it by no more than 0.003 AUC in either direction (book/flow -0.0005 and +0.0015, ES/RTY +0.0009 and +0.0006, clock +0.0008 and -0.0014, other books +0.0016 and -0.0034; two test blocks, 2026Q2 and October 2026). So every near-zone rule that scores well here is, in effect, a floor or an early take chosen by location; the microstructure, cross-market and clock families add timing at best and are mostly the same exit one or two seconds earlier. (2) The one family that behaves like new information is s: a profit-taking cluster (another book on the same side has just filled its target) and, on the small books, an opposite-side signal. It carries the largest forward-placebo gap, but it is also the rule that clips the most fills; it is listed with its clipped dollars in every row, never alone. (3) Read removed, clipped and other saves separately: on P7 the positive net of the best sets comes from the other saves (exits at 70-80% of target on trades that never reach 80% and then fail), not from the zone itself; the zone alone (removed minus clipped) is about zero or negative once the strict test is imposed, and mode D is that view. Every rule that makes the strict trader test pass on P7 does so by exiting at 70% (arm 0.7) or by a floor at 65% on touch, and pays by clipping about 17 fills a week on L6M, which is what the tables below price: about eight fills clipped for every give-back event removed.

## 2. Joint stage over all families a-v (the deliverable)

Method. Registry per book = top 3 cells of each of W-N's families a b c d e f (W-N's merged g combinations are left out: the joint stage is the composition, and a set must stay at 3 rules) and h i j o p q (p, q market-exit floors; h touched-not-filled; i queue step-in; j move-target; o level target; their exit rows were added by a patched copy of nz_kern2, nz_kern2x.py, so exits can be ordered in time), plus my k l r s t u uH(HOLD veto) and v (learned): about 60 rules per book. W-N's m (staggered limits) and n (runner) are partial-lot structures and are NOT in the composition (no single exit time); they stay W-N's rows. A set = at most 3 rules; the earliest exit wins; at most one scale rule (bank) per set. Objective J = min(net L6M, net out-of-sample 2024+) per week minus 100 dollars per week for each strict-test violation on L6M (mode A: all rules; mode B: only rules the exact hook and the frozen live week can run, i.e. without h-q; mode C: B with no strict penalty = the best-net view; mode D = the order's own key: B with the net replaced by removed minus clipped, i.e. without the other saves outside the 80% zone). Search = greedy add then swap coordinate descent (3 passes) plus 1,000 random 2-3 rule combinations per mode; the "minimal" set is the smallest set with J >= 90% of the best J. First-order budget: every candidate set costs about 10-20 ms (vectorised earliest-exit combination plus metrics), so the full search is a few minutes per book. Exact budget (honest): one set-month is about 4 minutes of engine time and a set needs 6 months for L6M, 12 for L6M+HOLD and 29 for all windows, so the exact stage can only cover the sets listed in section 7, one set per job, ordered L6M, then HOLD, then PRE; it is gated by MemAvail >= 62 GB and nothing runs until the engine queue has room.

### P7 at 12/7/7 lots

| set | rules | net $/wk L6M / 43 m | removed / clipped / other saves $/wk (L6M) | clipped fills/wk | give-backs/wk before -> after | round-trips/wk before -> after | strict L6M 90/80 (live rules) | net $/wk L3M / L1M | net $/wk L6M at slip 0.57 / 1.6 | net $/wk HOLD / PRE / X' | L6M weeks with a gain / worst week $ | 5 best weeks delta $ | stack maxDD cut % L6M / HOLD / PRE / X' | live week (delta $; strict 90/80; live rules) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A-best | p: noise floor arm=0.9: ext - 0.75 x ATR14(1m) + s: same-side target exit <=300 s ago arm=0.7 take + j: move-target to wall-1: arm=0.8 wall_ahead[8]>=3 persist=1 | 7290 / 1972 | 20526 / 18533 / 5298 | 17.4 | 2.05 -> 0.33 | 2.05 -> 0.20 | 3 / 5 (24 / 50) | 10490 / 7743 | 8856 / 6296 | 3230 / 2111 / -905 | 60% / -25877 | -14315 | 27.2 / 18.8 / 11.8 / 16.2 | not replayable first-order (needs print/queue extracts) |
| A-descent | a: ladder m1=0.7 f1=0.65 / .9 f2=0.8 / .95 f3=0.9 mode=1 + s: same-side target exit <=300 s ago arm=0.7 take + o: level target all m=0.8: target = level - 2 ticks | 4785 / 1638 | 20937 / 31779 / 15627 | 17.2 | 2.05 -> 0.04 | 2.05 -> 0.00 | 1 / 0 (24 / 50) | 6213 / 4588 | 6430 / 3740 | 1478 / 2125 / 291 | 44% / -30867 | -41453 | 48.5 / 29.2 / 31.0 / 41.7 | not replayable first-order (needs print/queue extracts) |
| B-best | u: spread>=3 ticks arm=0.8 persist=3 + s: same-side target exit <=300 s ago arm=0.7 take + s: same-side book took target (<=600 s) arm=0.7 take | 4679 / 1552 | 22427 / 23539 / 5791 | 18.0 | 2.05 -> 0.04 | 2.05 -> 0.04 | 1 / 1 (24 / 50) | 8179 / 4308 | 6309 / 3644 | 2662 / 1897 / -402 | 56% / -33991 | -33217 | 25.9 / 6.0 / 22.3 / 26.2 | -10854; 2 / 0 (1 / 3) |
| B-minimal | s: same-side target exit <=300 s ago arm=0.7 take + a: ladder m1=0.7 f1=0.65 / .9 f2=0.8 / .95 f3=0.9 mode=1 | 4550 / 1497 | 20910 / 31987 / 15627 | 17.0 | 2.05 -> 0.04 | 2.05 -> 0.00 | 1 / 0 (24 / 50) | 5902 / 4547 | 6172 / 3520 | 1166 / 2031 / 142 | 48% / -31894 | -42011 | 48.3 / 29.1 / 30.8 / 41.7 | -40692; 0 / 0 (1 / 3) |
| C-best | s: same-side book took target (<=600 s) arm=0.7 take | 6113 / 1408 | 11922 / 11600 / 5791 | 8.1 | 2.05 -> 1.06 | 2.05 -> 1.06 | 11 / 26 (24 / 50) | 10379 / 1919 | 6896 / 5616 | 3573 / 587 / -1279 | 44% / -18308 | 17975 | 19.7 / 16.9 / 10.9 / -11.6 | -24943; 1 / 3 (1 / 3) |
| D-best | s: same-side book took target (<=600 s) arm=0.8 take + u: spread>=3 ticks arm=0.8 persist=3 | 2520 / 1292 | 22897 / 20377 / -0 | 17.9 | 2.05 -> 0.04 | 2.05 -> 0.04 | 1 / 1 (24 / 50) | 2639 / 5477 | 4100 / 1518 | 1758 / 2212 / -100 | 52% / -30864 | -66946 | 15.8 / -1.3 / 25.2 / 31.4 | -4417; 2 / 0 (1 / 3) |
| D-descent | u: spread>=3 ticks arm=0.8 persist=3 + s: same-side book took target (<=600 s) arm=0.8 take | 2520 / 1292 | 22897 / 20377 / -0 | 17.9 | 2.05 -> 0.04 | 2.05 -> 0.04 | 1 / 1 (24 / 50) | 2639 / 5477 | 4100 / 1518 | 1758 / 2212 / -100 | 52% / -30864 | -66946 | 15.8 / -1.3 / 25.2 / 31.4 | -4417; 2 / 0 (1 / 3) |
| D-minimal | u: spread>=3 ticks arm=0.8 persist=3 | 1967 / 1519 | 22650 / 20682 / -0 | 17.7 | 2.05 -> 0.12 | 2.05 -> 0.08 | 2 / 2 (24 / 50) | 1811 / 4363 | 3538 / 970 | 1612 / 2488 / 690 | 52% / -30905 | -66497 | 13.6 / -1.6 / 24.5 / 33.9 | -5180; 2 / 0 (1 / 3) |

### P7 at 7/4/4 (installed)

| set | rules | net $/wk L6M / 43 m | removed / clipped / other saves $/wk (L6M) | clipped fills/wk | give-backs/wk before -> after | round-trips/wk before -> after | strict L6M 90/80 (live rules) | net $/wk L3M / L1M | net $/wk L6M at slip 0.57 / 1.6 | net $/wk HOLD / PRE / X' | L6M weeks with a gain / worst week $ | 5 best weeks delta $ | stack maxDD cut % L6M / HOLD / PRE / X' | live week (delta $; strict 90/80; live rules) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A-best | c: flow pulled_against_mult>=5 arm=0.8 persist=1 dd>=0 + o: level target all m=0.7: target = level - 2 ticks + s: same-side book took target (<=600 s) arm=0.7 take | 1983 / 847 | 12921 / 14296 / 3359 | 18.5 | 2.05 -> 0.04 | 2.05 -> 0.04 | 1 / 1 (24 / 50) | 3806 / 2052 | 2945 / 1372 | 1666 / 1600 / -853 | 44% / -21452 | -21186 | 34.2 / -4.0 / 28.2 / 14.8 | not replayable first-order (needs print/queue extracts) |
| B-best | s: same-side target exit <=300 s ago arm=0.7 take + a: ladder m1=0.7 f1=0.65 / .9 f2=0.7 / .95 f3=0.9 mode=1 + t: clock m_sessch<=40min arm=0.9 take | 2661 / 893 | 12098 / 18489 / 9052 | 17.0 | 2.05 -> 0.04 | 2.05 -> 0.00 | 1 / 0 (24 / 50) | 3645 / 2520 | 3602 / 2064 | 846 / 1155 / 146 | 44% / -18576 | -24544 | 55.1 / 19.0 / 21.0 / 36.6 | -23737; 0 / 0 (1 / 3) |
| B-minimal | s: same-side target exit <=300 s ago arm=0.7 take + a: ladder m1=0.7 f1=0.65 / .9 f2=0.8 / .95 f3=0.9 mode=1 | 2632 / 880 | 12108 / 18528 / 9052 | 17.0 | 2.05 -> 0.04 | 2.05 -> 0.00 | 1 / 0 (24 / 50) | 3433 / 2645 | 3573 / 2035 | 700 / 1187 / 109 | 48% / -18461 | -24106 | 53.6 / 18.4 / 21.0 / 36.8 | -23737; 0 / 0 (1 / 3) |
| C-best | s: same-side book took target (<=600 s) arm=0.7 take | 3563 / 827 | 6919 / 6711 / 3355 | 8.1 | 2.05 -> 1.06 | 2.05 -> 1.06 | 11 / 26 (24 / 50) | 6041 / 1125 | 4016 / 3274 | 2074 / 348 / -735 | 44% / -10613 | 10642 | 30.4 / 4.7 / 2.0 / -8.2 | -14550; 1 / 3 (1 / 3) |
| D-best | u: spread>=3 ticks arm=0.8 persist=1 + t: clock m_sessch<=40min arm=0.9 floor.6 | 1684 / 737 | 13293 / 11609 / 0 | 18.3 | 2.05 -> 0.04 | 2.05 -> 0.04 | 1 / 1 (24 / 50) | 1291 / 3222 | 2611 / 1095 | 1153 / 1291 / 1 | 52% / -17122 | -35487 | 15.4 / -8.4 / 13.0 / 30.3 | +1828; 0 / 0 (1 / 3) |
| D-minimal | u: spread>=3 ticks arm=0.8 persist=1 | 1684 / 735 | 13293 / 11609 / 0 | 18.3 | 2.05 -> 0.04 | 2.05 -> 0.04 | 1 / 1 (24 / 50) | 1291 / 3222 | 2611 / 1095 | 1153 / 1281 / 10 | 52% / -17122 | -35487 | 15.4 / -8.4 / 13.0 / 30.6 | +1828; 0 / 0 (1 / 3) |

### K7

| set | rules | net $/wk L6M / 43 m | removed / clipped / other saves $/wk (L6M) | clipped fills/wk | give-backs/wk before -> after | round-trips/wk before -> after | strict L6M 90/80 (live rules) | net $/wk L3M / L1M | net $/wk L6M at slip 0.57 / 1.6 | net $/wk HOLD / PRE / X' | L6M weeks with a gain / worst week $ | 5 best weeks delta $ | stack maxDD cut % L6M / HOLD / PRE / X' | live week (delta $; strict 90/80; live rules) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A-best | a: ladder m1=0.8 f1=0.65 / .9 f2=0.7 / .95 f3=0.9 mode=1 + o: level target all m=0.8: target = level - 2 ticks + j: move-target to wall-1: arm=0.8 wall_ahead[20]>=3 persist=1 | 59 / -658 | 6737 / 6839 / 162 | 23.9 | 3.19 -> 0.00 | 3.19 -> 0.00 | 0 / 0 (36 / 78) | -513 / -1991 | 462 / -196 | -1265 / -853 / -362 | 40% / -4246 | -7174 | 7.1 / 5.0 / 5.1 / 5.5 | not replayable first-order (needs print/queue extracts) |
| B-best | a: ladder m1=0.8 f1=0.65 / .9 f2=0.7 / .95 f3=0.7 mode=1 + s: same-side book took target (<=600 s) arm=0.7 take | -188 / -778 | 6513 / 7850 / 1149 | 18.5 | 3.19 -> 0.08 | 3.19 -> 0.00 | 1 / 0 (36 / 78) | -1027 / -3728 | 144 / -399 | -1372 / -1037 / -372 | 32% / -6459 | -12009 | 4.5 / 4.8 / 5.0 / 2.5 | +1542; 0 / 0 (2 / 5) |
| C-best | t: clock m_rel<=3min arm=0.9 take | 294 / -16 | 438 / 143 / 0 | 0.2 | 3.19 -> 3.23 | 3.19 -> 2.99 | 37 / 73 (36 / 78) | 311 / 1102 | 302 / 289 | -234 / 19 / -70 | 16% / -1190 | 4015 | 0.0 / 0.0 / -0.0 / -2.5 | +0; 2 / 5 (2 / 5) |
| D-best | d: bank arm=0.8 F=0.33 mkt lt=1 / floor 0.6 + a: ladder m1=0.8 f1=0.65 / .9 f2=0.7 / .95 f3=0.7 mode=1 | -70 / -613 | 6361 / 6431 / 0 | 13.1 | 3.19 -> 0.16 | 3.19 -> 0.00 | 3 / 0 (36 / 78) | -401 / -1926 | 175 / -226 | -1473 / -762 / -205 | 36% / -6040 | -6925 | 7.2 / 3.5 / 3.2 / 7.9 | +2329; 0 / 0 (2 / 5) |
| D-descent | a: ladder m1=0.8 f1=0.65 / .9 f2=0.7 / .95 f3=0.7 mode=1 | -70 / -613 | 6361 / 6431 / 0 | 13.1 | 3.19 -> 0.16 | 3.19 -> 0.00 | 3 / 0 (36 / 78) | -401 / -1926 | 175 / -226 | -1473 / -762 / -205 | 36% / -6040 | -6925 | 7.2 / 3.5 / 3.2 / 7.9 | +2329; 0 / 0 (2 / 5) |

### M7

| set | rules | net $/wk L6M / 43 m | removed / clipped / other saves $/wk (L6M) | clipped fills/wk | give-backs/wk before -> after | round-trips/wk before -> after | strict L6M 90/80 (live rules) | net $/wk L3M / L1M | net $/wk L6M at slip 0.57 / 1.6 | net $/wk HOLD / PRE / X' | L6M weeks with a gain / worst week $ | 5 best weeks delta $ | stack maxDD cut % L6M / HOLD / PRE / X' | live week (delta $; strict 90/80; live rules) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A-best | a: ladder m1=0.8 f1=0.65 / .9 f2=0.8 / .95 f3=0.9 mode=1 + q: arrival: fast<=150s mid slow>600s floors 0.8/0.8/0.6 + s: same-side target exit <=180 s ago arm=0.7 floor.6 | 297 / -183 | 3770 / 4039 / 566 | 10.5 | 1.92 -> 0.00 | 1.92 -> 0.00 | 0 / 0 (23 / 47) | -40 / 1744 | 483 / 179 | 368 / -424 / -105 | 48% / -5570 | -7712 | 4.8 / 1.3 / -5.8 / -17.1 | not replayable first-order (needs print/queue extracts) |
| B-best | a: ladder m1=0.8 f1=0.65 / .9 f2=0.8 / .95 f3=0.8 mode=1 + t: clock m_sessch<=5min arm=0.8 take + s: same-side target exit <=180 s ago arm=0.7 floor.6 | 441 / -135 | 3682 / 3807 / 566 | 8.5 | 1.92 -> 0.08 | 1.92 -> 0.00 | 2 / 0 (23 / 47) | 62 / 2077 | 599 / 342 | 341 / -386 / -37 | 52% / -5275 | -7714 | 5.4 / 1.3 / -5.5 / -16.6 | +857; 0 / 0 (2 / 2) |
| C-best | t: clock m_sessch<=5min arm=0.9 floor.6 | 109 / 46 | 231 / 123 / -0 | 0.2 | 1.92 -> 1.88 | 1.92 -> 1.76 | 22 / 43 (23 / 47) | 101 / -200 | 114 / 105 | 11 / -16 / 161 | 16% / -1020 | -1020 | 2.8 / 0.0 / -0.7 / -1.3 | -598; 2 / 2 (2 / 2) |
| D-best | t: clock m_sessch<=5min arm=0.8 take + a: ladder m1=0.8 f1=0.65 / .9 f2=0.8 / .95 f3=0.8 mode=1 | 292 / -124 | 3685 / 3394 / 0 | 8.0 | 1.92 -> 0.08 | 1.92 -> 0.00 | 2 / 0 (23 / 47) | 118 / 1691 | 437 / 199 | 371 / -379 / 48 | 48% / -4148 | -7842 | 6.3 / 1.1 / -6.6 / -12.2 | +1028; 0 / 0 (2 / 2) |
| D-descent | a: ladder m1=0.8 f1=0.65 / .9 f2=0.8 / .95 f3=0.8 mode=1 + t: clock m_sessch<=5min arm=0.8 take | 292 / -124 | 3685 / 3394 / 0 | 8.0 | 1.92 -> 0.08 | 1.92 -> 0.00 | 2 / 0 (23 / 47) | 118 / 1691 | 437 / 199 | 371 / -379 / 48 | 48% / -4148 | -7842 | 6.3 / 1.1 / -6.6 / -12.2 | +1028; 0 / 0 (2 / 2) |

### U7

| set | rules | net $/wk L6M / 43 m | removed / clipped / other saves $/wk (L6M) | clipped fills/wk | give-backs/wk before -> after | round-trips/wk before -> after | strict L6M 90/80 (live rules) | net $/wk L3M / L1M | net $/wk L6M at slip 0.57 / 1.6 | net $/wk HOLD / PRE / X' | L6M weeks with a gain / worst week $ | 5 best weeks delta $ | stack maxDD cut % L6M / HOLD / PRE / X' | live week (delta $; strict 90/80; live rules) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A-best | s: same-side book took target (<=600 s) arm=0.7 take + j: move-target to wall-1: arm=0.8 wall_ahead[20]>=3 persist=1 | 1029 / 120 | 3491 / 3390 / 929 | 5.3 | 0.65 -> 0.00 | 0.65 -> 0.00 | 0 / 0 (4 / 16) | 1315 / 1566 | 1250 / 889 | 19 / 401 / -436 | 56% / -6717 | -9014 | 18.2 / -0.5 / 15.6 / 0.4 | not replayable first-order (needs print/queue extracts) |
| B-best | a: ladder m1=0.7 f1=0.65 / .9 f2=0.7 / .95 f3=0.7 mode=1 + a: ladder m1=0.7 f1=0.65 / .9 f2=0.8 / .95 f3=0.8 mode=1 + k: absorb aggw10>=3.7 & d_prog10<=4 arm=0.8 persist=1 floor.6 | 758 / 100 | 3317 / 4551 / 1992 | 4.4 | 0.65 -> 0.00 | 0.65 -> 0.00 | 0 / 0 (4 / 16) | 740 / 2300 | 950 / 636 | 196 / 219 / -69 | 56% / -8140 | -16250 | 15.5 / -7.1 / 15.8 / 0.4 | +0; 0 / 0 (0 / 0) |
| B-descent | a: ladder m1=0.7 f1=0.65 / .9 f2=0.8 / .95 f3=0.8 mode=1 + t: clock m_rel<=10min arm=0.9 take | 750 / 99 | 3317 / 4560 / 1992 | 4.4 | 0.65 -> 0.00 | 0.65 -> 0.00 | 0 / 0 (4 / 16) | 724 / 2300 | 942 / 627 | 196 / 222 / -69 | 56% / -8140 | -16250 | 15.6 / -7.1 / 15.8 / 0.4 | +0; 0 / 0 (0 / 0) |
| B-minimal | a: ladder m1=0.7 f1=0.65 / .9 f2=0.8 / .95 f3=0.8 mode=1 | 746 / 98 | 3317 / 4563 / 1992 | 4.4 | 0.65 -> 0.00 | 0.65 -> 0.00 | 0 / 0 (4 / 16) | 719 / 2300 | 939 / 624 | 196 / 219 / -69 | 56% / -8140 | -16250 | 15.5 / -7.1 / 15.8 / 0.4 | +0; 0 / 0 (0 / 0) |
| C-best | s: same-side book took target (<=600 s) arm=0.7 take | 1189 / 144 | 2834 / 2574 / 929 | 3.7 | 0.65 -> 0.12 | 0.65 -> 0.12 | 1 / 3 (4 / 16) | 1481 / 2746 | 1340 / 1092 | 64 / 307 / -524 | 56% / -6724 | -11512 | 10.7 / -4.5 / 0.2 / -1.8 | -333; 0 / 0 (0 / 0) |
| D-best | e: stall arm=0.8 N=3 ticks=2 work=20s + uH: HOLD veto micro>=0.6 persist=1 ladder (0.6, 0.75, 0.9) + e: stall arm=0.8 N=3 ticks=1 work=20s | 333 / -264 | 3556 / 3223 / -0 | 5.0 | 0.65 -> 0.00 | 0.65 -> 0.00 | 0 / 0 (4 / 16) | 598 / 1422 | 535 / 204 | 272 / -325 / -592 | 52% / -6296 | -8889 | 7.7 / 0.0 / 14.0 / -5.7 | -678; 0 / 0 (0 / 0) |
| D-descent | e: stall arm=0.8 N=3 ticks=1 work=20s + s: same-side target exit <=300 s ago arm=0.8 take + f: zone arm=.8 N=30 take | 320 / -274 | 3563 / 3244 / -0 | 5.3 | 0.65 -> 0.00 | 0.65 -> 0.00 | 0 / 0 (4 / 16) | 617 / 1615 | 533 / 184 | 215 / -328 / -605 | 52% / -5602 | -6165 | 7.0 / -0.8 / 11.7 / -5.3 | -715; 0 / 0 (0 / 0) |

### H7

| set | rules | net $/wk L6M / 43 m | removed / clipped / other saves $/wk (L6M) | clipped fills/wk | give-backs/wk before -> after | round-trips/wk before -> after | strict L6M 90/80 (live rules) | net $/wk L3M / L1M | net $/wk L6M at slip 0.57 / 1.6 | net $/wk HOLD / PRE / X' | L6M weeks with a gain / worst week $ | 5 best weeks delta $ | stack maxDD cut % L6M / HOLD / PRE / X' | live week (delta $; strict 90/80; live rules) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A-best | b: rev arm=0.8 X=4 N=5 + h: touched-not-filled: printed >= T-4 tick(s), hit inside after 0 s, slip 0.25 + o: level target round m=0.8: target = level - 2 ticks | 190 / 146 | 1455 / 1266 / -0 | 3.0 | 0.53 -> 0.00 | 0.53 -> 0.00 | 0 / 0 (4 / 13) | 866 / 1405 | 265 / 142 | 357 / -118 / 521 | 40% / -4309 | -14511 | 1.5 / 3.5 / -4.3 / 13.9 | not replayable first-order (needs print/queue extracts) |
| B-best | b: rev arm=0.8 X=4 N=5 | 152 / 130 | 1444 / 1293 / -0 | 2.5 | 0.53 -> 0.00 | 0.53 -> 0.00 | 0 / 0 (4 / 13) | 774 / 1158 | 216 / 111 | 236 / -100 / 557 | 44% / -4309 | -15006 | 1.4 / 3.4 / -3.0 / 11.2 | -303; 0 / 0 (0 / 0) |
| C-best | s: same-side book took target (<=600 s) arm=0.8 take | 467 / 0 | 1072 / 605 / -0 | 1.5 | 0.53 -> 0.16 | 0.53 -> 0.16 | 0 / 4 (4 / 13) | 576 / 1815 | 507 / 441 | -46 / 77 / -261 | 32% / -2560 | -7829 | 1.1 / 0.0 / -5.0 / 1.7 | +0; 0 / 0 (0 / 0) |

### A7

| set | rules | net $/wk L6M / 43 m | removed / clipped / other saves $/wk (L6M) | clipped fills/wk | give-backs/wk before -> after | round-trips/wk before -> after | strict L6M 90/80 (live rules) | net $/wk L3M / L1M | net $/wk L6M at slip 0.57 / 1.6 | net $/wk HOLD / PRE / X' | L6M weeks with a gain / worst week $ | 5 best weeks delta $ | stack maxDD cut % L6M / HOLD / PRE / X' | live week (delta $; strict 90/80; live rules) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A-best | a: ladder m1=0.8 f1=0.65 / .9 f2=0.7 / .95 f3=0.9 mode=1 + s: same-side book took target (<=600 s) arm=0.7 take + j: move-target to wall-1: arm=0.8 wall_ahead[12]>=3 persist=1 | -195 / -140 | 1130 / 1846 / 522 | 6.5 | 0.65 -> 0.00 | 0.65 -> 0.00 | 0 / 0 (4 / 16) | -522 / -875 | -101 / -254 | -300 / -177 / -51 | 40% / -2874 | -6277 | -1.5 / -0.8 / -1.2 / -2.1 | not replayable first-order (needs print/queue extracts) |
| B-best | r: es_dd300<=-2 bps arm=0.8 persist=3 + a: ladder m1=0.8 f1=0.65 / .9 f2=0.7 / .95 f3=0.9 mode=1 + s: same-side book took target (<=600 s) arm=0.7 take | -221 / -163 | 1115 / 1857 / 522 | 5.7 | 0.65 -> 0.00 | 0.65 -> 0.00 | 0 / 0 (4 / 16) | -620 / -976 | -137 / -274 | -346 / -201 / -52 | 36% / -3202 | -7018 | -2.1 / -1.0 / -1.6 / -2.2 | +1274; 0 / 0 (1 / 2) |
| B-descent | a: ladder m1=0.8 f1=0.65 / .9 f2=0.7 / .95 f3=0.9 mode=1 + s: same-side book took target (<=600 s) arm=0.7 take + r: es_dd300<=-2 bps arm=0.8 persist=3 | -221 / -162 | 1115 / 1857 / 522 | 5.7 | 0.65 -> 0.00 | 0.65 -> 0.00 | 0 / 0 (4 / 16) | -620 / -976 | -137 / -274 | -346 / -201 / -52 | 36% / -3202 | -7018 | -2.1 / -1.0 / -1.6 / -2.2 | +1274; 0 / 0 (1 / 2) |
| C-best | t: clock m_sessch<=20min arm=0.9 take + s: same-side book took target (<=600 s) arm=0.7 take | 1 / -9 | 718 / 1239 / 522 | 4.4 | 0.65 -> 0.25 | 0.65 -> 0.25 | 0 / 6 (4 / 16) | -242 / -294 | 65 / -40 | -187 / -32 / -3 | 52% / -2314 | -2379 | 0.7 / 0.3 / -0.4 / -1.9 | -159; 1 / 1 (1 / 2) |
| D-best | a: ladder m1=0.8 f1=0.65 / .9 f2=0.7 / .95 f3=0.9 mode=1 + r: es_dd300<=-2 bps arm=0.8 persist=3 | -328 / -172 | 1082 / 1409 / 0 | 4.3 | 0.65 -> 0.04 | 0.65 -> 0.00 | 0 / 0 (4 / 16) | -619 / -532 | -266 / -367 | -331 / -219 / 10 | 40% / -2590 | -5484 | -2.9 / -0.8 / -1.5 / -1.5 | +1783; 0 / 0 (1 / 2) |

### O7

| set | rules | net $/wk L6M / 43 m | removed / clipped / other saves $/wk (L6M) | clipped fills/wk | give-backs/wk before -> after | round-trips/wk before -> after | strict L6M 90/80 (live rules) | net $/wk L3M / L1M | net $/wk L6M at slip 0.57 / 1.6 | net $/wk HOLD / PRE / X' | L6M weeks with a gain / worst week $ | 5 best weeks delta $ | stack maxDD cut % L6M / HOLD / PRE / X' | live week (delta $; strict 90/80; live rules) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A-best | c: flow pulled_against_mult>=20 arm=0.8 persist=3 dd>=2 + s: opposite-side signal in 120 s arm=0.7 take + o: level target pd m=0.8: target = level - 2 ticks | -17 / -8 | 137 / 155 / 0 | 0.3 | 0.12 -> 0.00 | 0.04 -> 0.00 | 0 / 0 (2 / 1) | -165 / 0 | -12 / -21 | 68 / -43 / 36 | 12% / -1110 | -146 | 0.6 / 0.1 / -0.0 / -0.4 | not replayable first-order (needs print/queue extracts) |
| B-best | c: flow pulled_against_mult>=20 arm=0.8 persist=3 dd>=2 + s: opposite-side signal in 120 s arm=0.7 take | -17 / -22 | 137 / 155 / 0 | 0.3 | 0.12 -> 0.00 | 0.04 -> 0.00 | 0 / 0 (2 / 1) | -165 / 0 | -12 / -21 | 68 / -54 / -11 | 12% / -1110 | -146 | 0.6 / 0.1 / -0.0 / -0.4 | +0; 0 / 0 (0 / 0) |
| C-best | s: opposite-side signal in 120 s arm=0.7 floor.6 + s: same-side target exit <=300 s ago arm=0.8 floor.6 | 0 / 4 | 0 / -0 / 0 | 0.0 | 0.12 -> 0.12 | 0.04 -> 0.04 | 2 / 1 (2 / 1) | 0 / 0 | 0 / 0 | -25 / 14 / 7 | 0% / 0 | 0 | 0.0 / 0.1 / 0.0 / -1.0 | +0; 0 / 0 (0 / 0) |
| C-descent | s: opposite-side signal in 120 s arm=0.7 take | 0 / 4 | 0 / -0 / 0 | 0.0 | 0.12 -> 0.12 | 0.04 -> 0.04 | 2 / 1 (2 / 1) | 0 / 0 | 0 / 0 | 4 / 5 / -5 | 0% / 0 | 0 | 0.0 / 0.1 / 0.0 / -0.4 | +0; 0 / 0 (0 / 0) |
| D-descent | c: flow pulled_against_mult>=20 arm=0.8 persist=3 dd>=2 | -17 / -25 | 137 / 155 / 0 | 0.3 | 0.12 -> 0.00 | 0.04 -> 0.00 | 0 / 0 (2 / 1) | -165 / 0 | -12 / -21 | 64 / -54 / -12 | 12% / -1110 | -146 | 0.6 / 0.0 / -0.0 / 0.0 | +0; 0 / 0 (0 / 0) |


How to read a row: "rules" are in the order of the registry; "removed / clipped" are $ per week on L6M; "give-backs/wk before -> after" counts events (MFE >= 80% closing below 50%); "strict L6M 90/80" is the number of trades that still fail the trader test (in brackets the live-rule counts); "5 best weeks delta" is the change in $ over the five best L6M weeks of the book, which is the trend-week check of the standing principle; stack maxDD cut is from the first-order stack replay (W-N's FO.score), larger is better. Live week = the frozen week 11-02..05 replayed from the stored 1-s paths, first-order.

Stability over time (net $/wk by half-year, first-order, same sets; 2023H1 starts 2023-04):

| book | set | rules | 2023H1 | 2023H2 | 2024H1 | 2024H2 | 2025H1 | 2025H2 | 2026H1 | 2026H2 |
|---|---|---|---|---|---|---|---|---|---|---|
| P7 at 12/7/7 lots | B-best | u: spread>=3 ticks arm=0.8 persist=3 + s: same-side target exit <=300 s ago arm=0.7 take + s: same-side book t | 2213 | -737 | -2094 | 2040 | 3272 | -1358 | 2111 | 5687 |
| P7 at 12/7/7 lots | C-best | s: same-side book took target (<=600 s) arm=0.7 take | -416 | -427 | -3279 | 1347 | 2292 | 1399 | 3004 | 6182 |
| P7 at 7/4/4 (installed) | B-best | s: same-side target exit <=300 s ago arm=0.7 take + a: ladder m1=0.7 f1=0.65 / .9 f2=0.7 / .95 f3=0.9 mode=1 + | 1506 | -167 | -1594 | -465 | 4232 | -1626 | 2120 | 2405 |
| P7 at 7/4/4 (installed) | C-best | s: same-side book took target (<=600 s) arm=0.7 take | -240 | -239 | -1889 | 784 | 1336 | 833 | 1753 | 3592 |
| K7 | B-best | a: ladder m1=0.8 f1=0.65 / .9 f2=0.7 / .95 f3=0.7 mode=1 + s: same-side book took target (<=600 s) arm=0.7 tak | -128 | -272 | -1214 | -1541 | -403 | -833 | -893 | -299 |
| K7 | C-best | t: clock m_rel<=3min arm=0.9 take | 24 | -49 | -269 | 126 | 104 | -164 | -207 | 324 |
| M7 | B-best | a: ladder m1=0.8 f1=0.65 / .9 f2=0.8 / .95 f3=0.8 mode=1 + t: clock m_sessch<=5min arm=0.8 take + s: same-side | -390 | 291 | -50 | -434 | -572 | -642 | 946 | -120 |
| M7 | C-best | t: clock m_sessch<=5min arm=0.9 floor.6 | 32 | 95 | 179 | 7 | -87 | -105 | 157 | 50 |
| U7 | B-best | a: ladder m1=0.7 f1=0.65 / .9 f2=0.7 / .95 f3=0.7 mode=1 + a: ladder m1=0.7 f1=0.65 / .9 f2=0.8 / .95 f3=0.8 m | -76 | -447 | 1085 | -1066 | 1010 | -489 | 175 | 526 |
| U7 | C-best | s: same-side book took target (<=600 s) arm=0.7 take | -384 | -659 | 1212 | -601 | 422 | 3 | 339 | 698 |
| H7 | B-best | b: rev arm=0.8 X=4 N=5 | 511 | 464 | -449 | 201 | -75 | 80 | 12 | 187 |
| H7 | C-best | s: same-side book took target (<=600 s) arm=0.8 take | 124 | -482 | -226 | 38 | 327 | -69 | 96 | 193 |
| A7 | B-best | r: es_dd300<=-2 bps arm=0.8 persist=3 + a: ladder m1=0.8 f1=0.65 / .9 f2=0.7 / .95 f3=0.9 mode=1 + s: same-sid | -37 | 31 | -234 | -93 | -321 | -9 | -213 | -290 |
| A7 | C-best | t: clock m_sessch<=20min arm=0.9 take + s: same-side book took target (<=600 s) arm=0.7 take | -47 | 77 | -78 | -6 | -42 | 136 | -17 | -90 |
| O7 | B-best | c: flow pulled_against_mult>=20 arm=0.8 persist=3 dd>=2 + s: opposite-side signal in 120 s arm=0.7 take | -66 | 19 | 21 | -109 | -37 | -30 | 73 | -27 |
| O7 | C-best | s: opposite-side signal in 120 s arm=0.7 floor.6 + s: same-side target exit <=300 s ago arm=0.8 floor.6 | -64 | 67 | 9 | 41 | 0 | -31 | 4 | 0 |

Read this before trusting any number above: the profit-taking-cluster rule (family s) loses in 2023 and 2024H1 and earns in every half-year since 2024H2, with the largest weekly gain in the latest half-year; the L6M figures are the best-looking window, not an average of the 43 months (the 43-month column is 4 to 5 times smaller). The rule is a recent-regime result until it holds in an exact run and in the bi-weekly walk-forward.

Bi-weekly walk-forward (the primary evidence under the recents-first rule; first-order): at each 2-week block the set with the best trailing 26-week net (minus 100 dollars per violation) is picked from the 1,042 candidates (registry singles + 1,000 random 2-3 sets, mode B rules) and applied to the next block.

| book | candidates | weeks | walk-forward net $/wk (2024-04..2026-10) | of which L6M | blocks (2 wk) with a gain | worst 2-week block $ | set switches / distinct sets | best fixed set in hindsight $/wk |
|---|---|---|---|---|---|---|---|---|
| P7 at 12/7/7 lots | 1042 | 136 | 1593 | 2337 | 51% | -60882 | 28 / 21 | 2363 (s: same-side book took target (<=600 s) arm=0.7 take) |
| P7 at 7/4/4 (installed) | 1042 | 136 | 598 | 1394 | 51% | -35508 | 36 / 24 | 1381 (s: same-side book took target (<=600 s) arm=0.7 take) |
| K7 | 1042 | 136 | -270 | -43 | 26% | -6729 | 27 / 9 | 8 (t: clock m_rel<=3min arm=0.9 take) |
| M7 | 1042 | 136 | -185 | 304 | 32% | -5998 | 27 / 18 | 19 (s: same-side target exit <=180 s ago arm=0.8 floor.6 + t: clock m_sessch<=5min arm=0.9 floor.6) |
| U7 | 1042 | 136 | -144 | 29 | 32% | -10117 | 35 / 23 | 312 (s: same-side book took target (<=600 s) arm=0.7 take) |

Only P7 survives the walk-forward with a positive number, and it does so with a block that loses 35-61 thousand dollars in two weeks and a gain in only about half of the blocks; K7, M7 and U7 are negative walk-forward, so for them the first-order L6M figures above are in-sample selection, not an edge.

Per book x session (mode B, strict penalty, 300 random sets + descent per session; each set is applied to that session's trades only, the other sessions keep the live rule):

| book | session | trades (43 m) | rules (mode B, strict penalty) | net $/wk L6M | net $/wk 2024+ | strict L6M 90/80 |
|---|---|---|---|---|---|---|
| P7 at 12/7/7 lots | asia | 1768 | c: flow pulled_against_mult>=5 arm=0.8 persist=1 dd>=0 + r: es_dd300<=-1 bps arm=0.8 persist=1 + s: same-side book took target (<=600 s) arm=0.7 take | 4231 | 1961 | 0 / 0 |
| P7 at 12/7/7 lots | london | 1208 | a: ladder m1=0.7 f1=0.65 / .9 f2=0.7 / .95 f3=0.8 mode=1 + c: flow pulled_against_mult>=5 arm=0.8 persist=1 dd>=0 + r: rty_pown5>=2x arm=0.8 persist=1 | 1535 | 201 | 0 / 0 |
| P7 at 12/7/7 lots | nyam | 961 | u: spread>=3 ticks arm=0.8 persist=3 + t: clock m_sessch<=40min arm=0.8 floor.6 | 506 | 152 | 0 / 0 |
| P7 at 7/4/4 (installed) | asia | 1768 | c: flow pulled_against_mult>=5 arm=0.8 persist=1 dd>=0 + r: es_dd300<=-1 bps arm=0.8 persist=1 + s: same-side book took target (<=600 s) arm=0.7 take | 2468 | 1144 | 0 / 0 |
| P7 at 7/4/4 (installed) | london | 1208 | a: ladder m1=0.7 f1=0.65 / .9 f2=0.7 / .95 f3=0.9 mode=1 + c: flow pulled_against_mult>=5 arm=0.8 persist=1 dd>=0 + r: es_dd300<=-1 bps arm=0.8 persist=1 | 878 | 114 | 0 / 0 |
| P7 at 7/4/4 (installed) | nyam | 961 | f: zone arm=.8 N=30 floor 0.65 + t: clock m_sessch<=40min arm=0.8 floor.6 | 724 | 81 | 0 / 0 |
| K7 | asia | 1893 | a: ladder m1=0.8 f1=0.65 / .9 f2=0.7 / .95 f3=0.7 mode=1 | -187 | -181 | 0 / 0 |
| K7 | london | 1378 | a: ladder m1=0.8 f1=0.65 / .9 f2=0.7 / .95 f3=0.8 mode=1 + s: same-side book took target (<=600 s) arm=0.7 take + f: zone arm=.8 N=30 floor 0.8 | 189 | -176 | 0 / 0 |
| K7 | nyam | 1301 | uH: HOLD veto micro>=0.3 persist=1 ladder (0.6, 0.75, 0.9) + s: same-side book took target (<=600 s) arm=0.8 take | -39 | -215 | 0 / 0 |
| K7 | nypm | 1055 | v: learned arm=0.8 p*<0.35 persist=3 + t: clock m_rel<=3min arm=0.9 take + s: same-side book took target (<=600 s) arm=0.8 floor.6 | 119 | -222 | 0 / 0 |
| M7 | london | 2058 | a: ladder m1=0.8 f1=0.65 / .9 f2=0.8 / .95 f3=0.8 mode=1 + s: same-side target exit <=180 s ago arm=0.7 floor.6 + t: clock m_sessch<=5min arm=0.8 take | 757 | -22 | 0 / 0 |
| M7 | nyam | 1365 | u: imbalance flip imb5<=-0.1 arm=0.8 persist=1 + v: learned arm=0.7 p*<0.75 persist=3 + s: same-side target exit <=180 s ago arm=0.8 floor.6 | -95 | -96 | 0 / 0 |
| U7 | asia | 567 | s: same-side book took target (<=600 s) arm=0.7 take | 1656 | 457 | 0 / 0 |
| U7 | london | 551 | e: stall arm=0.8 N=3 ticks=2 work=20s + e: stall arm=0.8 N=3 ticks=1 work=20s + f: zone arm=.8 N=30 take | 294 | 91 | 0 / 0 |
| H7 | asia | 554 | b: rev arm=0.8 X=4 N=5 | 29 | 38 | 0 / 0 |
| H7 | nyam | 327 | u: spread>=3 ticks arm=0.8 persist=5 | 108 | 16 | 0 / 0 |
| A7 | asia | 956 | a: ladder m1=0.8 f1=0.65 / .9 f2=0.7 / .95 f3=0.9 mode=1 + s: same-side book took target (<=600 s) arm=0.7 take + r: es_dd300<=-2 bps arm=0.8 persist=3 | -221 | -204 | 0 / 0 |
| O7 | nyam | 341 | c: flow pulled_against_mult>=20 arm=0.8 persist=3 dd>=2 + s: opposite-side signal in 120 s arm=0.7 take | -17 | -19 | 0 / 0 |

Standing-principle scorecard status. Items b (give-backs, round-trips) and e (fills clipped, net) are in the table above, first-order. Items a (full stops) and c/d (same-side re-entry streaks, no-new-evidence entries) are untouched by exit-side rules in this frame: a rule that exits earlier can only change a stop into a smaller loss. The exact scorecard (code/th_works_q/behavior_scorecard.py <SET>) is run on each exact set as soon as its months are done; exits are named NearTarget so the tool counts them as clip-type exits.

## 3. Family tables (first-order, best cell per family by key; strict-pass cell when one exists)

| book | family | rule (best by key) | net $/wk L6M / 43 m | removed / clipped $/wk (L6M) | clipped fills/wk | strict L6M (90%->below 50% / 80%-><=0) vs live-rule counts | p_plc / p_fam |
|---|---|---|---|---|---|---|---|
| P7 at 12/7/7 lots | k | absorb aggw30>=19 & d_prog30<=3 arm=0.9 persist=1 take | 3952 / 724 | 7994 / 4042 | 2.8 | 17 / 31 vs 24 / 50 | 0.67 / 0.75 |
| P7 at 12/7/7 lots | l | decay d_vr10<=0.1 arm=0.9 persist=3 dd>=0 | 4493 / 991 | 11516 / 7023 | 11.1 | 1 / 27 vs 24 / 50 | 0.00 / 0.00 |
| P7 at 12/7/7 lots | r | es_dd300<=-1 bps & NQ at high(secs_fav<=10) arm=0.7 persist=1 | 1551 / 1194 | 13193 / 19881 | 11.7 | 13 / 17 vs 24 / 50 | 0.00 / 0.00 |
| P7 at 12/7/7 lots | s | same-side book took target (<=600 s) arm=0.7 take | 6113 / 1408 | 11922 / 11600 | 8.1 | 11 / 26 vs 24 / 50 | 0.00 / 0.00 |
| P7 at 12/7/7 lots | t | clock m_rel<=30min arm=0.9 floor.6 | 693 / 545 | 1243 / 550 | 0.1 | 25 / 47 vs 24 / 50 | 0.17 / 0.50 |
| P7 at 12/7/7 lots | u | spread>=4 ticks arm=0.9 persist=1 | 5714 / 2084 | 11499 / 5785 | 14.4 | 3 / 27 vs 24 / 50 | 0.00 / 0.00 |
| P7 at 12/7/7 lots | u strict-pass | spread>=3 ticks arm=0.7 persist=1 | 3253 / 1166 | 21426 / 34171 | 18.7 | 0 / 0 vs 24 / 50 | 0.00 / 0.42 |
| P7 at 12/7/7 lots | uH | HOLD veto F_behind_rel_f>=1.2 persist=1 ladder (0.5, 0.7, 0.85) | 1702 / 418 | 19026 / 17325 | 7.5 | 81 / 2 vs 24 / 50 | 0.00 / 0.00 |
| P7 at 12/7/7 lots | v (OOS 2024+) | learned arm=0.8 p*<0.75 persist=1 | 2583 / 1000 (OOS) | 22920 / 20337 | 18.1 | 2 / 1 vs 24 / 50 | 0.00 / 0.00 |
| P7 at 7/4/4 (installed) | k | absorb aggw30>=19 & d_prog30<=3 arm=0.9 persist=1 take | 2299 / 421 | 4638 / 2339 | 2.8 | 17 / 31 vs 24 / 50 | 0.67 / 0.75 |
| P7 at 7/4/4 (installed) | l | decay d_vr10<=0.1 arm=0.9 persist=3 dd>=0 | 2624 / 583 | 6681 / 4057 | 11.1 | 1 / 27 vs 24 / 50 | 0.00 / 0.00 |
| P7 at 7/4/4 (installed) | r | es_dd300<=-1 bps & NQ at high(secs_fav<=10) arm=0.7 persist=1 | 887 / 706 | 7618 / 11492 | 11.7 | 13 / 17 vs 24 / 50 | 0.00 / 0.00 |
| P7 at 7/4/4 (installed) | s | same-side book took target (<=600 s) arm=0.7 take | 3563 / 827 | 6919 / 6711 | 8.1 | 11 / 26 vs 24 / 50 | 0.00 / 0.00 |
| P7 at 7/4/4 (installed) | t | clock m_rel<=30min arm=0.9 floor.6 | 402 / 315 | 716 / 314 | 0.1 | 25 / 47 vs 24 / 50 | 0.17 / 0.50 |
| P7 at 7/4/4 (installed) | u | spread>=4 ticks arm=0.9 persist=1 | 3339 / 1217 | 6673 / 3334 | 14.4 | 3 / 27 vs 24 / 50 | 0.00 / 0.00 |
| P7 at 7/4/4 (installed) | u strict-pass | spread>=3 ticks arm=0.7 persist=1 | 1882 / 686 | 12406 / 19792 | 18.7 | 0 / 0 vs 24 / 50 | 0.00 / 0.42 |
| P7 at 7/4/4 (installed) | uH | HOLD veto F_behind_rel_f>=1.2 persist=1 ladder (0.5, 0.7, 0.85) | 989 / 248 | 11021 / 10032 | 7.5 | 81 / 2 vs 24 / 50 | 0.00 / 0.00 |
| P7 at 7/4/4 (installed) | v (OOS 2024+) | learned arm=0.8 p*<0.75 persist=1 | 1509 / 589 (OOS) | 13274 / 11765 | 18.1 | 2 / 1 vs 24 / 50 | 0.00 / 0.00 |
| K7 | k | absorb aggw30>=19 & d_prog30<=3 arm=0.9 persist=3 floor.6 | 849 / -65 | 1734 / 885 | 1.2 | 38 / 60 vs 36 / 78 | 0.83 / 1.00 |
| K7 | l | intensity prate<=0.3 arm=0.9 persist=10 dd>=3 | 137 / -210 | 1462 / 1326 | 3.5 | 35 / 60 vs 36 / 78 | 0.08 / 0.08 |
| K7 | r | es_dd300<=-3 bps & NQ at high(secs_fav<=10) arm=0.9 persist=5 | 68 / -23 | 166 / 98 | 0.2 | 34 / 76 vs 36 / 78 | 0.75 / 0.83 |
| K7 | s | opposite-side signal in 120 s arm=0.7 take | 630 / 438 | 428 / 69 | 0.0 | 37 / 76 vs 36 / 78 | 0.00 / 0.00 |
| K7 | t | clock m_flat<=60min arm=0.9 floor.6 | 8 / 11 | 39 / 31 | 0.0 | 36 / 77 vs 36 / 78 | 0.92 / 0.92 |
| K7 | u | microprice against<=-1 tick arm=0.7 persist=5 | 748 / -25 | 2141 / 2573 | 4.3 | 68 / 52 vs 36 / 78 | 0.33 / 0.42 |
| K7 | u strict-pass | spread>=3 ticks arm=0.8 persist=1 | -920 / -1109 | 7029 / 7949 | 28.0 | 0 / 0 vs 36 / 78 | 1.00 / 1.00 |
| K7 | uH | HOLD veto F_behind_rel_f>=1.5 persist=1 ladder (0.4, 0.6, 0.8) | -366 / -684 | 5556 / 5922 | 9.0 | 97 / 1 vs 36 / 78 | 1.00 / 1.00 |
| K7 | v (OOS 2024+) | learned arm=0.9 p*<0.2 persist=5 | 392 / -326 (OOS) | 2541 / 2149 | 3.4 | 27 / 44 vs 36 / 78 | 0.92 / 0.92 |
| M7 | k | absorb aggw10>=3.7 & d_prog10<=2 arm=0.9 persist=1 floor.6 | 412 / 68 | 1634 / 1223 | 2.1 | 8 / 25 vs 23 / 47 | 0.75 / 0.83 |
| M7 | l | vr30<=.25 & prate<=0.5 arm=0.9 persist=10 dd>=0 | 77 / -5 | 1046 / 969 | 2.1 | 21 / 35 vs 23 / 47 | 0.42 / 0.58 |
| M7 | r | es_dd300<=-5 bps arm=0.9 persist=1 | 513 / 86 | 1513 / 1000 | 1.5 | 30 / 25 vs 23 / 47 | 0.00 / 0.50 |
| M7 | r strict-pass | rty_pown5>=2x arm=0.8 persist=3 | -168 / -394 | 3885 / 4053 | 12.6 | 0 / 0 vs 23 / 47 | 0.92 / 1.00 |
| M7 | s | opposite-side signal in 120 s arm=0.7 take | 340 / 237 | 377 / 163 | 0.1 | 26 / 45 vs 23 / 47 | 0.33 / 0.33 |
| M7 | t | clock m_sessch<=5min arm=0.9 floor.6 | 109 / 46 | 231 / 123 | 0.2 | 22 / 43 vs 23 / 47 | 0.75 / 0.75 |
| M7 | u | own depth behind thin behind_rel<=0.7 arm=0.9 persist=5 | 518 / 92 | 1445 / 927 | 2.2 | 20 / 29 vs 23 / 47 | 0.00 / 0.00 |
| M7 | u strict-pass | imbalance flip imb5<=-0.1 arm=0.7 persist=1 | 413 / -343 | 3773 / 5873 | 14.1 | 0 / 0 vs 23 / 47 | 0.00 / 1.00 |
| M7 | uH | HOLD veto F_imb5_0>=0.2 persist=1 ladder (0.4, 0.6, 0.8) | 136 / -200 | 3188 / 3053 | 4.5 | 50 / 0 vs 23 / 47 | 0.58 / 1.00 |
| M7 | v (OOS 2024+) | learned arm=0.9 p*<0.2 persist=5 | 316 / 61 (OOS) | 1438 / 1121 | 1.8 | 16 / 27 vs 23 / 47 | 0.42 / 0.42 |
| U7 | k | absorb aggw30>=19 & d_prog30<=0 arm=0.8 persist=3 take | 227 / -40 | 1637 / 1410 | 1.1 | 8 / 8 vs 4 / 16 | 1.00 / 1.00 |
| U7 | l | intensity prate<=0.3 arm=0.7 persist=10 dd>=0 | 356 / 40 | 1832 / 2756 | 2.2 | 18 / 6 vs 4 / 16 | 0.33 / 0.83 |
| U7 | l strict-pass | decay d_vr10<=0.5 arm=0.8 persist=3 dd>=0 | 38 / -368 | 3508 / 3470 | 4.6 | 0 / 0 vs 4 / 16 | 0.25 / 1.00 |
| U7 | r | es_dd300<=-1 bps & NQ at high(secs_fav<=10) arm=0.7 persist=3 | 1476 / 294 | 2744 / 2337 | 2.8 | 1 / 4 vs 4 / 16 | 0.00 / 0.00 |
| U7 | r strict-pass | rty_dd300<=-1 bps & NQ at high(secs_fav<=10) arm=0.7 persist=1 | 601 / -66 | 3421 / 4710 | 5.2 | 0 / 0 vs 4 / 16 | 0.50 / 1.00 |
| U7 | s | same-side target exit <=180 s ago arm=0.8 take | 735 / 189 | 1938 / 1203 | 2.7 | 2 / 7 vs 4 / 16 | 0.25 / 0.25 |
| U7 | t | clock m_rel<=10min arm=0.9 floor.6 | -34 / -126 | 48 / 82 | 0.0 | 4 / 16 vs 4 / 16 | 0.00 / 0.33 |
| U7 | u | microprice against<=-1 tick arm=0.7 persist=3 | 849 / 296 | 2276 / 2803 | 2.5 | 15 / 7 vs 4 / 16 | 0.67 / 0.67 |
| U7 | u strict-pass | spread>=4 ticks arm=0.7 persist=1 | 186 / -32 | 3465 / 5311 | 5.6 | 0 / 0 vs 4 / 16 | 0.50 / 1.00 |
| U7 | uH | HOLD veto F_imb5_0>=0.2 persist=1 ladder (0.6, 0.75, 0.9) | 532 / -486 | 3175 / 2643 | 2.8 | 0 / 0 vs 4 / 16 | 0.58 / 0.75 |
| U7 | uH strict-pass | HOLD veto F_imb5_0>=0.2 persist=1 ladder (0.6, 0.75, 0.9) | 532 / -486 | 3175 / 2643 | 2.8 | 0 / 0 vs 4 / 16 | 0.58 / 0.75 |
| U7 | v (OOS 2024+) | learned arm=0.7 p*<0.2 persist=5 | 1227 / -4 (OOS) | 3093 / 3724 | 2.6 | 8 / 0 vs 4 / 16 | 0.75 / 1.00 |
| H7 | k | absorb aggw10>=3.7 & d_prog10<=0 arm=0.8 persist=1 take | 149 / 74 | 1413 / 1264 | 2.5 | 3 / 0 vs 4 / 13 | 0.42 / 0.50 |
| H7 | l | decay d_vr10<=0.1 arm=0.8 persist=5 dd>=3 | 73 / 52 | 1435 / 1361 | 2.8 | 1 / 0 vs 4 / 13 | 0.08 / 0.17 |
| H7 | l strict-pass | push-decay prog30_chg<=-8 arm=0.7 persist=10 dd>=0 | -117 / -113 | 1352 / 1866 | 3.1 | 0 / 0 vs 4 / 13 | 0.25 / 1.00 |
| H7 | r | es_pown5>=4x arm=0.9 persist=5 | 94 / 108 | 216 / 122 | 0.2 | 4 / 10 vs 4 / 13 | 0.00 / 0.00 |
| H7 | r strict-pass | rty_dd300<=-1 bps arm=0.8 persist=1 | 205 / 41 | 1467 / 1262 | 3.1 | 0 / 0 vs 4 / 13 | 0.25 / 1.00 |
| H7 | s | opposite-side signal in 120 s arm=0.7 take | 72 / 154 | 176 / 141 | 0.1 | 6 / 14 vs 4 / 13 | 0.33 / 0.67 |
| H7 | t | clock m_rel<=3min arm=0.7 take | 73 / 90 | 73 / -0 | 0.0 | 3 / 12 vs 4 / 13 | 0.17 / 0.33 |
| H7 | u | spread>=4 ticks arm=0.8 persist=1 | 110 / 88 | 1460 / 1350 | 3.1 | 2 / 0 vs 4 / 13 | 0.50 / 0.50 |
| H7 | u strict-pass | spread>=3 ticks arm=0.8 persist=5 | 96 / 58 | 1459 / 1363 | 3.2 | 0 / 0 vs 4 / 13 | 0.00 / 0.75 |
| H7 | uH | HOLD veto F_imb5_0>=0.2 persist=3 ladder (0.4, 0.6, 0.8) | -108 / 10 | 1077 / 1185 | 1.4 | 16 / 0 vs 4 / 13 | 0.42 / 0.75 |
| H7 | v (OOS 2024+) | learned arm=0.9 p*<0.35 persist=5 | 19 / 49 (OOS) | 372 / 353 | 0.5 | 1 / 9 vs 4 / 13 | 0.58 / 0.67 |
| A7 | k | absorb aggw30>=19 & d_prog30<=0 arm=0.8 persist=3 floor.6 | 63 / 6 | 550 / 488 | 0.8 | 8 / 9 vs 4 / 16 | 0.00 / 0.00 |
| A7 | l | intensity prate<=0.3 arm=0.8 persist=10 dd>=3 | -106 / -163 | 777 / 882 | 2.2 | 10 / 3 vs 4 / 16 | 0.25 / 0.25 |
| A7 | l strict-pass | push-decay prog30_chg<=-16 arm=0.8 persist=3 dd>=0 | -375 / -218 | 1138 / 1513 | 5.5 | 0 / 0 vs 4 / 16 | 0.00 / 1.00 |
| A7 | r | es_dd300<=-3 bps & NQ at high(secs_fav<=10) arm=0.7 persist=3 | 91 / 16 | 73 / 57 | 0.1 | 5 / 15 vs 4 / 16 | 0.00 / 0.00 |
| A7 | r strict-pass | rty_dd300<=-1 bps arm=0.8 persist=5 | -432 / -205 | 1141 / 1574 | 5.6 | 0 / 0 vs 4 / 16 | 0.17 / 1.00 |
| A7 | s | opposite-side signal in 120 s arm=0.8 floor.6 | 91 / 111 | 130 / 40 | 0.0 | 5 / 16 vs 4 / 16 | 0.00 / 0.00 |
| A7 | t | clock m_flat<=60min arm=0.7 floor.6 | 0 / 2 | 0 / -0 | 0.0 | 4 / 16 vs 4 / 16 | 0.33 / 0.42 |
| A7 | u | own depth behind thin behind_rel<=0.5 arm=0.8 persist=5 | -8 / -89 | 436 / 445 | 1.0 | 10 / 9 vs 4 / 16 | 0.25 / 0.25 |
| A7 | u strict-pass | imbalance flip imb5<=-0.1 arm=0.7 persist=1 | -469 / -227 | 1129 / 2470 | 6.7 | 0 / 0 vs 4 / 16 | 0.00 / 1.00 |
| A7 | uH | HOLD veto ownwall8>=6 persist=1 ladder (0.4, 0.6, 0.8) | -391 / -209 | 887 / 1278 | 2.5 | 21 / 0 vs 4 / 16 | 1.00 / 1.00 |
| A7 | v (OOS 2024+) | learned arm=0.8 p*<0.2 persist=5 | -356 / -239 (OOS) | 982 / 1337 | 2.4 | 5 / 0 vs 4 / 16 | 0.33 / 0.67 |
| O7 | k | absorb aggw30>=8 & d_prog30<=6 arm=0.9 persist=1 floor.6 | 13 / 22 | 13 / -0 | 0.0 | 1 / 1 vs 2 / 1 | 0.25 / 0.42 |
| O7 | k strict-pass | absorb aggw30>=19 & d_prog30<=0 arm=0.8 persist=1 take | -21 / -39 | 122 / 143 | 0.3 | 0 / 0 vs 2 / 1 | 0.25 / 1.00 |
| O7 | l | intensity prate<=0.3 arm=0.9 persist=10 dd>=3 | 0 / 0 | 0 / -0 | 0.0 | 2 / 1 vs 2 / 1 | 1.00 / 1.00 |
| O7 | l strict-pass | decay d_vr60<=0.5 arm=0.8 persist=10 dd>=0 | -33 / -62 | 117 / 149 | 0.3 | 0 / 0 vs 2 / 1 | 0.75 / 1.00 |
| O7 | r | es_stalled>=120s & NQ at high(secs_fav<=10) arm=0.7 persist=1 | 81 / 38 | 28 / 94 | 0.3 | 1 / 1 vs 2 / 1 | 0.08 / 0.08 |
| O7 | r strict-pass | es_pown5>=4x arm=0.8 persist=3 | -39 / -42 | 97 / 136 | 0.3 | 0 / 0 vs 2 / 1 | 0.42 / 1.00 |
| O7 | s | opposite-side signal in 120 s arm=0.7 take | 0 / 4 | 0 / -0 | 0.0 | 2 / 1 vs 2 / 1 | 0.25 / 1.00 |
| O7 | t | clock m_rel<=10min arm=0.9 floor.6 | 7 / 16 | 7 / -0 | 0.0 | 1 / 1 vs 2 / 1 | 0.75 / 1.00 |
| O7 | t strict-pass | clock m_rel<=30min arm=0.8 take | -78 / -39 | 142 / 220 | 0.6 | 0 / 0 vs 2 / 1 | 1.00 / 1.00 |
| O7 | u | microprice against<=-1 tick arm=0.7 persist=3 | 71 / 27 | 71 / -0 | 0.0 | 2 / 0 vs 2 / 1 | 0.17 / 0.17 |
| O7 | u strict-pass | spread>=4 ticks arm=0.7 persist=1 | 49 / -55 | 114 / 263 | 0.6 | 0 / 0 vs 2 / 1 | 0.00 / 1.00 |
| O7 | uH | HOLD veto ownwall8>=3 persist=1 ladder (0.5, 0.7, 0.85) | -97 / -55 | 105 / 202 | 0.2 | 4 / 0 vs 2 / 1 | 0.58 / 0.92 |
| O7 | uH strict-pass | HOLD veto F_imb5_0>=0.2 persist=1 ladder (0.6, 0.75, 0.9) | -114 / -65 | 109 / 223 | 0.3 | 0 / 0 vs 2 / 1 | 0.75 / 1.00 |
| O7 | v (OOS 2024+) | learned arm=0.9 p*<0.2 persist=3 | -4 / 17 (OOS) | 24 / 28 | 0.0 | 0 / 1 vs 2 / 1 | 0.50 / 0.50 |

Reading note. p_plc / p_fam are forward-only time-shift placebos (every fire exits a random 10-300 s later, 12 reps; the smallest possible p is 0.08, read 0.00 as <= 0.08). A p_fam of 0.00 means no cell of the family under shifted exits reached this cell's key. For the v rows the placebo is the same shift applied to the walk-forward P series. Families k (absorption) and t (clock) are weak (p_fam 0.25-0.75 on most books): not distinguishable from a random exit delay. Families l, r, u, s clear the placebo on P7 but, as section 1 shows, they are floors by location. On the other books only a few cells clear it (K7: s; M7: u, and r on the placebo but not on the family null; U7: r; H7: r; A7: k, r and s; O7: nothing), and their keys are small (under $300 a week, K7 s $438); none of them holds in the walk-forward below.

## 4. Family v: learned exit

Per second in the zone (MFE >= 70% of target, price still above 50%): P(target fills before price retraces to 50%). 64 features = every per-second feature of W-N's flow set + my book/flow (aggressor volume, print intensity, spread, microprice, imbalance, own wall), ES/RTY 1-s state, clock, other-book events + the trade's own path (pct, drawdown, seconds since high, velocity ratios). Model: 12-leaf monotone histogram GBDT (monotone constraints on 29 features), purged walk-forward by quarter from 2024Q1 (train on every month before the block start minus one month), 3 seeds (different row subsets), 15.3 M zone seconds. Out-of-sample AUC over all blocks 0.756; last blocks 0.774 (2026Q2) and 0.779 (October 2026).

Ablation (2026Q2 block / October 2026 block, AUC): location only 0.7713 / 0.7783; + clock 0.7721 / 0.7769; + price-path velocity 0.7715 / 0.7794; + book/flow 0.7708 / 0.7798; + ES/RTY 0.7722 / 0.7789; + other books 0.7729 / 0.7749; everything 0.7744 / 0.7790. Top features by out-of-sample permutation importance (AUC drop, last walk-forward block): d_dist_tgt 0.2608; m_flat 0.0029; d_secs_zone 0.0027; d_mfe_pts 0.0017; d_pct 0.0010; d_secs_fav 0.0006; m_rel 0.0004; d_dd 0.0002.

Plain 2-3 condition rewrite. Because the model is location, the plain rewrite is the floor ladder (W-N's family a) plus one tape condition; the best 2-condition rewrites scored through the kernel (grid2_vplain: top permutation features, 5 quantile thresholds, arm .8/.9, persist 3) do not beat the learned cells and mostly reduce to "take at 90% after 3 s". There is no short rule from the tape here that the ladder does not already contain; this is a result, not a gap: the near-zone reversal is not forecastable from the tape in this feature set.

## 4b. HOLD-OR-TAKE table (T-BUILD-ON item 5; extends family v)

Table: for every zone second (MFE >= 70% of target, price above 50%) the cell = (pct of target bin .7/.8/.9/.95, seconds since the favourable extreme bin 5/30/120, drawdown from it 2/5/10 pt, seconds in the zone 60/300/1200). EV(hold) of a cell = mean terminal value of the base trade from all rows in the cell (target fill = full target, otherwise the terminal mid minus 1.2 pt); value now = price minus 1.2 pt market slip (state slip until measured). Rule: exit at the first second where EV(hold) < value now (cell needs 300 rows). The table is refit every 2 weeks on the trailing 26 weeks (trades before the block) and applied to the next block, so every number is walk-forward from 2024-04; per book, and per book x session (sessions with enough rows).

| book | rule | net $/wk L6M | net $/wk 2024-04+ (walk-forward) | removed / clipped $/wk L6M | strict L6M 90/80 (live rules) |
|---|---|---|---|---|---|
| P7 at 12/7/7 lots | hold-or-take table book refit bi-weekly 26wk | 1956 | 556 | 21861 / 31900 | 14 / 0 (24 / 50) |
| P7 at 7/4/4 (installed) | hold-or-take table book refit bi-weekly 26wk | 1140 | 333 | 12657 / 18480 | 14 / 0 (24 / 50) |
| P7 at 12/7/7 lots | hold-or-take table book x session refit bi-weekly 26wk | 2314 | 846 | 21124 / 31215 | 6 / 2 (24 / 50) |
| P7 at 7/4/4 (installed) | hold-or-take table book x session refit bi-weekly 26wk | 1344 | 500 | 12232 / 18088 | 6 / 2 (24 / 50) |
| K7 | hold-or-take table book refit bi-weekly 26wk | -774 | -1351 | 6541 / 10779 | 0 / 2 (36 / 78) |
| K7 | hold-or-take table book x session refit bi-weekly 26wk | -518 | -1401 | 6337 / 10514 | 7 / 3 (36 / 78) |
| M7 | hold-or-take table book refit bi-weekly 26wk | 229 | -401 | 3715 / 5769 | 6 / 1 (23 / 47) |
| M7 | hold-or-take table book x session refit bi-weekly 26wk | 276 | -375 | 3562 / 5773 | 6 / 3 (23 / 47) |
| U7 | hold-or-take table book refit bi-weekly 26wk | -32 | -107 | 3424 / 5146 | 3 / 0 (4 / 16) |
| U7 | hold-or-take table book x session refit bi-weekly 26wk | 120 | -139 | 3110 / 4740 | 0 / 1 (4 / 16) |
| H7 | hold-or-take table book refit bi-weekly 26wk | -278 | -136 | 1370 / 1869 | 0 / 1 (4 / 13) |
| H7 | hold-or-take table book x session refit bi-weekly 26wk | -369 | -140 | 941 / 1530 | 2 / 5 (4 / 13) |
| A7 | hold-or-take table book refit bi-weekly 26wk | -506 | -256 | 1137 / 1910 | 0 / 0 (4 / 16) |
| A7 | hold-or-take table book x session refit bi-weekly 26wk | -506 | -256 | 1137 / 1910 | 0 / 0 (4 / 16) |
| O7 | hold-or-take table book refit bi-weekly 26wk | -284 | -153 | 10 / 294 | 1 / 1 (2 / 1) |
| O7 | hold-or-take table book x session refit bi-weekly 26wk | -284 | -153 | 10 / 294 | 1 / 1 (2 / 1) |

Plain 2-3 condition rewrite (best of 140 cells per book, fixed over the whole sample, so in-sample): 

| book | rule | net $/wk L6M / 43 m | strict 90/80 |
|---|---|---|---|
| P7 at 12/7/7 lots | plain: pct>=0.9 AND drawdown from high >= 2 pt AND secs since high >= 0 -> take | 4471 / 1145 | 1 / 27 |
| P7 at 7/4/4 (installed) | plain: pct>=0.9 AND drawdown from high >= 2 pt AND secs since high >= 0 -> take | 2613 / 674 | 1 / 27 |
| K7 | plain: pct>=0.95 AND drawdown from high >= 8 pt AND secs since high >= 60 -> take | 152 / -233 | 25 / 64 |
| M7 | plain: pct>=0.9 AND drawdown from high >= 12 pt AND secs since high >= 0 -> take | 390 / 27 | 1 / 24 |
| U7 | plain: pct>=0.7 AND drawdown from high >= 8 pt AND secs since high >= 60 -> take | 822 / -78 | 16 / 0 |
| H7 | plain: pct>=0.8 AND drawdown from high >= 8 pt AND secs since high >= 0 -> take | 116 / 108 | 0 / 0 |
| A7 | plain: pct>=0.95 AND drawdown from high >= 3 pt AND secs since high >= 0 -> take | -144 / -61 | 2 / 14 |
| O7 | plain: pct>=0.95 AND drawdown from high >= 8 pt AND secs since high >= 0 -> take | -11 / -9 | 2 / 1 |

Reading. The table is the learned exit again, so it inherits the finding of section 4: it is a location rule. Walk-forward it is positive only on P7 (book x session version, +2,314 L6M / +846 a week since 2024-04 at 12/7/7), marginal elsewhere and negative on K7, U7, H7, A7, O7; on P7 it clips about 1,600 fills for about 21 thousand dollars a week removed and 31 thousand clipped (L6M), and it still leaves 6 trades that reached 90% closing below 50%. Against the references from W-N on the same L6M window: best ladder P7x +4,235 (strict 3 / 0), best staggered P7x +8,320 (strict 4 / 25, first-order, optimistic limit fills), U7 ladder +746 (strict 0 / 0) against table -32 / +120. So no table beats the best ladder or the staggered rungs; the plain rewrite is "pct >= 90% and drawdown from the high >= 2 pt -> take" for P7 (L6M +4,471 at 12/7/7, 1 / 27 strict violations), which is the same family as W-N's ladder. v1.8 fields: `dd_from_high_pts`, `secs_since_high` (both exist in the stand-in grammar), and a table-lookup action only if a table is ever preferred over the ladder (not recommended). Exact for finalists is not queued: the table does not beat the ladder, so it is not a finalist behind the P7 governor sets.

## 5. Trader test lists (20 largest give-backs, L6M and frozen live week, live rules vs finalist) - mode B best set per book

#### P7 at 12/7/7 lots - set B-best (u: spread>=3 ticks arm=0.8 persist=3 + s: same-side target exit <=300 s ago arm=0.7 take + s: same-side book took target (<=600 s) arm=0.7 take)

L6M, 20 largest give-backs under live rules and under the finalist:

| time | book | lots | MFE % | closed at % live rules | closed at % finalist |
|---|---|---|---|---|---|
| 08-26 03:03Z | P7 | 12 | 93 | -85 | 79 |
| 09-10 05:07Z | P7 | 12 | 96 | -72 | 85 |
| 07-28 05:40Z | P7 | 12 | 94 | -71 | 67 |
| 10-20 05:16Z | P7 | 12 | 86 | -72 | 73 |
| 07-02 22:07Z | P7 | 12 | 80 | -74 | 78 |
| 09-11 02:43Z | P7 | 12 | 89 | -50 | 68 |
| 06-29 01:23Z | P7 | 12 | 95 | -32 | 85 |
| 06-01 00:38Z | P7 | 12 | 91 | -29 | 77 |
| 06-19 05:03Z | P7 | 12 | 92 | -27 | 86 |
| 05-22 10:05Z | P7 | 7 | 84 | -100 | 81 |
| 06-25 10:42Z | P7 | 7 | 92 | -89 | 85 |
| 07-24 03:10Z | P7 | 12 | 99 | -3 | 76 |
| 07-13 23:23Z | P7 | 7 | 95 | -77 | 78 |
| 08-13 14:24Z | P7 | 7 | 96 | -71 | 81 |
| 07-02 15:16Z | P7 | 7 | 88 | -78 | 86 |
| 07-23 15:25Z | P7 | 7 | 97 | -66 | 68 |
| 08-07 01:39Z | P7 | 7 | 93 | -72 | 79 |
| 09-08 10:18Z | P7 | 7 | 90 | -71 | 76 |
| 06-04 00:40Z | P7 | 7 | 86 | -77 | 72 |
| 07-28 02:14Z | P7 | 7 | 95 | -67 | 78 |

Frozen live week (46 trades with a path): it removed give-backs worth $50981 and clipped 27 fills worth $61835

| time | book | lots | MFE % | closed at % live rules | closed at % finalist |
|---|---|---|---|---|---|
| 11-03 23:13Z | P7 | 12 | 84 | -77 | 76 |
| 11-04 05:53Z | P7 | 12 | 81 | -48 | 75 |
| 11-02 23:47Z | P7 | 7 | 91 | -50 | 87 |

#### P7 at 7/4/4 (installed) - set B-best (s: same-side target exit <=300 s ago arm=0.7 take + a: ladder m1=0.7 f1=0.65 / .9 f2=0.7 / .95 f3=0.9 mode=1 + t: clock m_sessch<=40min arm=0.9 take)

L6M, 20 largest give-backs under live rules and under the finalist:

| time | book | lots | MFE % | closed at % live rules | closed at % finalist |
|---|---|---|---|---|---|
| 08-26 03:03Z | P7 | 7 | 93 | -85 | 65 |
| 09-10 05:07Z | P7 | 7 | 96 | -72 | 65 |
| 07-28 05:40Z | P7 | 7 | 94 | -71 | 65 |
| 10-20 05:16Z | P7 | 7 | 86 | -72 | 73 |
| 07-02 22:07Z | P7 | 7 | 80 | -74 | 65 |
| 09-11 02:43Z | P7 | 7 | 89 | -50 | 68 |
| 06-29 01:23Z | P7 | 7 | 95 | -32 | 65 |
| 06-01 00:38Z | P7 | 7 | 91 | -29 | 77 |
| 06-19 05:03Z | P7 | 7 | 92 | -27 | 65 |
| 05-22 10:05Z | P7 | 4 | 84 | -100 | 65 |
| 06-25 10:42Z | P7 | 4 | 92 | -89 | 65 |
| 07-24 03:10Z | P7 | 7 | 99 | -3 | 65 |
| 07-13 23:23Z | P7 | 4 | 95 | -77 | 65 |
| 08-13 14:24Z | P7 | 4 | 96 | -71 | 90 |
| 07-02 15:16Z | P7 | 4 | 88 | -78 | 86 |
| 08-07 01:39Z | P7 | 4 | 93 | -72 | 70 |
| 06-04 00:40Z | P7 | 4 | 86 | -77 | 65 |
| 07-28 02:14Z | P7 | 4 | 95 | -67 | 57 |
| 07-23 15:25Z | P7 | 4 | 97 | -66 | 65 |
| 10-19 03:21Z | P7 | 4 | 94 | -69 | 65 |

Frozen live week (46 trades with a path): it removed give-backs worth $24963 and clipped 26 fills worth $48700

| time | book | lots | MFE % | closed at % live rules | closed at % finalist |
|---|---|---|---|---|---|
| 11-03 23:13Z | P7 | 7 | 84 | -77 | 46 |
| 11-04 05:53Z | P7 | 7 | 81 | -48 | 65 |
| 11-02 23:47Z | P7 | 4 | 91 | -50 | 59 |

#### K7 - set B-best (a: ladder m1=0.8 f1=0.65 / .9 f2=0.7 / .95 f3=0.7 mode=1 + s: same-side book took target (<=600 s) arm=0.7 take)

L6M, 20 largest give-backs under live rules and under the finalist:

| time | book | lots | MFE % | closed at % live rules | closed at % finalist |
|---|---|---|---|---|---|
| 09-18 06:51Z | K7 | 2 | 98 | -101 | 83 |
| 06-04 11:36Z | K7 | 2 | 95 | -98 | 70 |
| 10-21 16:42Z | K7 | 2 | 95 | -96 | 70 |
| 07-27 06:03Z | K7 | 2 | 94 | -97 | 92 |
| 07-07 16:45Z | K7 | 2 | 91 | -96 | 70 |
| 07-31 05:09Z | K7 | 2 | 87 | -98 | 70 |
| 08-26 03:21Z | K7 | 2 | 88 | -96 | 65 |
| 08-05 22:24Z | K7 | 2 | 80 | -103 | 57 |
| 07-17 10:30Z | K7 | 2 | 86 | -83 | 73 |
| 10-08 18:18Z | K7 | 2 | 97 | -71 | 70 |
| 07-14 05:45Z | K7 | 2 | 92 | -66 | 67 |
| 07-07 06:57Z | K7 | 2 | 89 | -69 | 87 |
| 06-22 06:54Z | K7 | 2 | 90 | -66 | 65 |
| 10-27 12:18Z | K7 | 2 | 90 | -59 | 70 |
| 05-15 17:54Z | K7 | 2 | 81 | -65 | 65 |
| 07-13 04:24Z | K7 | 2 | 85 | -39 | 65 |
| 06-23 03:33Z | K7 | 2 | 80 | -32 | 75 |
| 05-18 18:39Z | K7 | 1 | 84 | -123 | 65 |
| 06-11 04:21Z | K7 | 1 | 86 | -115 | 75 |
| 05-15 12:27Z | K7 | 1 | 90 | -106 | 72 |

Frozen live week (52 trades with a path): it removed give-backs worth $8899 and clipped 17 fills worth $7357

| time | book | lots | MFE % | closed at % live rules | closed at % finalist |
|---|---|---|---|---|---|
| 11-03 23:06Z | K7 | 2 | 88 | -74 | 50 |
| 11-05 08:12Z | K7 | 1 | 98 | -58 | 71 |
| 11-03 15:57Z | K7 | 1 | 82 | -54 | 63 |
| 11-04 19:33Z | K7 | 1 | 83 | -50 | 65 |
| 11-05 02:18Z | K7 | 1 | 84 | -48 | 67 |
| 11-02 01:09Z | K7 | 1 | 95 | 45 | 65 |

#### M7 - set B-best (a: ladder m1=0.8 f1=0.65 / .9 f2=0.8 / .95 f3=0.8 mode=1 + t: clock m_sessch<=5min arm=0.8 take + s: same-side target exit <=180 s ago arm=0.7 floor.6)

L6M, 20 largest give-backs under live rules and under the finalist:

| time | book | lots | MFE % | closed at % live rules | closed at % finalist |
|---|---|---|---|---|---|
| 05-22 10:05Z | M7 | 2 | 85 | -100 | 65 |
| 07-22 06:46Z | M7 | 2 | 98 | -76 | 80 |
| 09-18 06:56Z | M7 | 2 | 98 | -73 | 80 |
| 06-04 11:36Z | M7 | 2 | 95 | -65 | 68 |
| 06-02 07:33Z | M7 | 2 | 93 | -67 | 65 |
| 06-23 06:58Z | M7 | 2 | 98 | -58 | 61 |
| 09-08 09:57Z | M7 | 2 | 88 | -65 | 65 |
| 07-30 07:29Z | M7 | 2 | 96 | -54 | 80 |
| 07-08 06:14Z | M7 | 2 | 86 | -53 | 52 |
| 10-28 14:35Z | M7 | 1 | 82 | -129 | 65 |
| 10-26 08:40Z | M7 | 1 | 92 | -101 | 65 |
| 05-20 15:16Z | M7 | 1 | 90 | -94 | 50 |
| 10-21 06:05Z | M7 | 1 | 80 | -100 | 51 |
| 09-15 08:30Z | M7 | 1 | 81 | -94 | 65 |
| 07-06 14:13Z | M7 | 1 | 86 | -83 | 65 |
| 09-30 07:16Z | M7 | 1 | 97 | -72 | 80 |
| 10-21 10:02Z | M7 | 1 | 92 | -72 | 80 |
| 10-05 08:43Z | M7 | 1 | 85 | -78 | 65 |
| 07-14 15:08Z | M7 | 1 | 96 | -67 | 80 |
| 06-04 06:10Z | M7 | 1 | 82 | -79 | 65 |

Frozen live week (23 trades with a path): it removed give-backs worth $3233 and clipped 5 fills worth $2376

| time | book | lots | MFE % | closed at % live rules | closed at % finalist |
|---|---|---|---|---|---|
| 11-05 10:08Z | M7 | 1 | 98 | -62 | 80 |
| 11-02 15:22Z | M7 | 1 | 95 | -59 | 80 |
| 11-02 11:58Z | M7 | 1 | 87 | 70 | 59 |

#### U7 - set B-best (a: ladder m1=0.7 f1=0.65 / .9 f2=0.7 / .95 f3=0.7 mode=1 + a: ladder m1=0.7 f1=0.65 / .9 f2=0.8 / .95 f3=0.8 mode=1 + k: absorb aggw10>=3.7 & d_prog10<=4 arm=0.8 persist=1 floor.6)

L6M, 20 largest give-backs under live rules and under the finalist:

| time | book | lots | MFE % | closed at % live rules | closed at % finalist |
|---|---|---|---|---|---|
| 09-02 09:00Z | U7 | 4 | 83 | -99 | 65 |
| 05-27 23:40Z | U7 | 4 | 86 | -95 | 65 |
| 06-08 05:40Z | U7 | 4 | 81 | -99 | 65 |
| 10-15 23:30Z | U7 | 4 | 94 | -61 | 65 |
| 08-04 00:40Z | U7 | 4 | 85 | -59 | 61 |
| 05-14 09:30Z | U7 | 4 | 85 | -57 | 65 |
| 05-19 07:10Z | U7 | 4 | 82 | -61 | 65 |
| 07-31 06:40Z | U7 | 2 | 97 | -106 | 65 |
| 07-30 01:30Z | U7 | 2 | 100 | -98 | 65 |
| 09-10 01:00Z | U7 | 2 | 82 | -110 | 57 |
| 10-19 08:00Z | U7 | 2 | 92 | -100 | 65 |
| 07-28 08:30Z | U7 | 2 | 84 | -101 | 65 |
| 10-26 10:50Z | U7 | 2 | 85 | -100 | 65 |
| 10-20 02:00Z | U7 | 2 | 83 | -92 | 65 |
| 08-23 23:30Z | U7 | 2 | 85 | -79 | 65 |
| 08-14 00:50Z | U7 | 2 | 82 | -56 | 65 |

Frozen live week (5 trades with a path): it removed give-backs worth $0 and clipped 0 fills worth $0

| time | book | lots | MFE % | closed at % live rules | closed at % finalist |
|---|---|---|---|---|---|


## 6. v1.8 actions and grammar the winners need (names of missing fields)

- Floor ladder on MFE: `profit <book> * mfe_pct>=0.7 floor 0.65` / `mfe_pct>=0.9 floor 0.70` / `mfe_pct>=0.95 floor 0.90` with action stop-limit at the floor (mode=1; v1.7 has pct but no persistent MFE-armed floor ladder and no resting stop-limit action). Fill model for the resting floor is an upper bound until measured.
- Cross-book event field: `peer_tgt_age` (seconds since another book's same-side Target exit; also `peer_tgt_n600`) for the family-s rule `pct>=0.7 peer_tgt_age<=300 take`; and `opp_sig_age` for the opposite-side-signal rule on the small books. Both are available in the engine (the hook logs Target exits and entries).
- Clock fields: `mins_to_sessch` (02:00, 09:30, 12:00, 18:00 ET) and `mins_to_flat` (16:55 ET) for `pct>=0.9 mins_to_sessch<=40 take`. The roll cannot be scored: the state file's roll flag is zero on every day, and the engine flattens at 23:59:59Z the day before each quarterly roll (14 roll flats with a path in 43 months, 3 of them had reached 70% of target and 2 of those gave it back, 97/84/73% -> 95/21/10%): too few to say anything, listed as an empty result. Scheduled release days (FOMC, CPI) are NOT in the data: the family-t release slots here are the fixed 08:30 / 10:00 / 14:00 ET weekday times, which is a limit.
- Book fields used by the u rules: `spread_ticks`, `behind_rel` (own-side depth8 / slot norm), `imb5`. HOLD veto (`uH`): a `hold_if` clause on the floor (support behind: own wall >= k x MedLevel or imbalance with the trade) - needed only if a HOLD rule survives the exact stage; first-order it loses to the plain ladder on every book.
- From W-N (not mine): move-target, staggered limits, touched-not-filled, runner need engine order hooks; they are first-order only.

## 7. Exact stage (status; one set per job through the SZ-CORE queue, file exact_queue_6g_nz2.txt, hook code/th_nz2/nz2_hooks.py)

Hook: private, same mechanics as W-N's nz_hooks (decision at the close of second j on the 1-s state tape, exit event at the next second, market slip 1.2 or the nz_kern limit model), but it runs a SET of rules from the kernel (a-g incl. flow with real F, my k l r s t u uH and the walk-forward learned exit) with earliest-exit wins, and computes the day features for ES/RTY (fd_series), clock and the other-book events (it logs Target exits and entries inside the engine). Parity test of the feature path and kernel against the first-order cache on 36 P7 trades (August 2026): identical fire sets for 7 of 7 test cells (absorption, decay, ES drawdown, peer target, clock, spread, HOLD veto).

| set | book | rules | months done / planned | EXACT stack Delta $/wk vs reference L6M / HOLD (months used) | EXACT book Delta $/wk L6M | EXACT stack maxDD cut % L6M / HOLD | NearTarget exits n / $ (L6M) |
|---|---|---|---|---|---|---|---|
| NEAR_N2_P7x_B1 | P7 | u: spread>=3 ticks arm=0.8 persist=3 + s: same-side target exit <=300 s ago arm=0.7 take + s: same-side book took target (<=600 s) arm=0.7 take | 6 / 39 | -2537 (6/6) / - | -2537 | 20.8 / - | 417 / 2146357 |
| NEAR_N2_P7x_B2 | P7 | s: same-side target exit <=300 s ago arm=0.7 take + a: ladder m1=0.7 f1=0.65 / .9 f2=0.8 / .95 f3=0.9 mode=1 | 6 / 39 | -1236 (6/6) / - | -1236 | 3.3 / - | 437 / 2044369 |
| NEAR_N2_P7x_D3 | P7 | s: same-side book took target (<=600 s) arm=0.8 take + u: spread>=3 ticks arm=0.8 persist=3 | 6 / 39 | -6046 (6/6) / - | -6046 | 0.1 / - | 386 / 2042318 |
| NEAR_N2_P7x_C4 | P7 | s: same-side book took target (<=600 s) arm=0.7 take | 6 / 29 | +2950 (6/6) / - | +2950 | 14.2 / - | 176 / 984153 |
| NEAR_N2_P7_B1 | P7 | s: same-side target exit <=300 s ago arm=0.7 take + a: ladder m1=0.7 f1=0.65 / .9 f2=0.7 / .95 f3=0.9 mode=1 + t: clock m_sessch<=40min arm=0.9 take | 6 / 29 | -627 (6/6) / - | -627 | 38.5 / - | 676 / 1838177 |
| NEAR_N2_P7_B2 | P7 | s: same-side target exit <=300 s ago arm=0.7 take + a: ladder m1=0.7 f1=0.65 / .9 f2=0.8 / .95 f3=0.9 mode=1 | 6 / 29 | -692 (6/6) / - | -692 | 37.6 / - | 679 / 1848252 |
| NEAR_N2_P7_D3 | P7 | u: spread>=3 ticks arm=0.8 persist=1 + t: clock m_sessch<=40min arm=0.9 floor.6 | 6 / 29 | -1779 (6/6) / - | -1779 | 24.6 / - | 613 / 1933535 |
| NEAR_N2_P7_C4 | P7 | s: same-side book took target (<=600 s) arm=0.7 take | 6 / 29 | +666 (6/6) / - | +666 | 26.0 / - | 260 / 850372 |
| NEAR_N2_K7_B1 | K7 | a: ladder m1=0.8 f1=0.65 / .9 f2=0.7 / .95 f3=0.7 mode=1 + s: same-side book took target (<=600 s) arm=0.7 take | 6 / 29 | +1159 (6/6) / - | +602 | 11.7 / - | 636 / 622452 |
| NEAR_N2_K7_D2 | K7 | d: bank arm=0.8 F=0.33 mkt lt=1 / floor 0.6 + a: ladder m1=0.8 f1=0.65 / .9 f2=0.7 / .95 f3=0.7 mode=1 | 6 / 29 | +1212 (6/6) / - | +654 | 12.6 / - | 458 / 417828 |
| NEAR_N2_K7_C3 | K7 | t: clock m_rel<=3min arm=0.9 take | 6 / 29 | +30 (6/6) / - | +30 | -0.0 / - | 12 / 9162 |
| NEAR_N2_M7_B1 | M7 | a: ladder m1=0.8 f1=0.65 / .9 f2=0.8 / .95 f3=0.8 mode=1 + t: clock m_sessch<=5min arm=0.8 take + s: same-side target exit <=180 s ago arm=0.7 floor.6 | 6 / 29 | -234 (6/6) / - | -234 | -1.4 / - | 306 / 290864 |
| NEAR_N2_M7_D2 | M7 | t: clock m_sessch<=5min arm=0.8 take + a: ladder m1=0.8 f1=0.65 / .9 f2=0.8 / .95 f3=0.8 mode=1 | 6 / 29 | -266 (6/6) / - | -266 | -0.0 / - | 282 / 274977 |
| NEAR_N2_M7_C3 | M7 | t: clock m_sessch<=5min arm=0.9 floor.6 | 6 / 29 | +113 (6/6) / - | +113 | 1.3 / - | 9 / 5556 |
| NEAR_N2_U7_B1 | U7 | a: ladder m1=0.7 f1=0.65 / .9 f2=0.7 / .95 f3=0.7 mode=1 + a: ladder m1=0.7 f1=0.65 / .9 f2=0.8 / .95 f3=0.8 mode=1 + k: absorb aggw10>=3.7 & d_prog10<=4 arm=0.8 persist=1 floor.6 | 6 / 29 | +166 (6/6) / - | +166 | 7.5 / - | 143 / 294527 |
| NEAR_N2_U7_B2 | U7 | a: ladder m1=0.7 f1=0.65 / .9 f2=0.8 / .95 f3=0.8 mode=1 | 6 / 29 | +156 (6/6) / - | +156 | 7.5 / - | 143 / 294251 |
| NEAR_N2_U7_D3 | U7 | e: stall arm=0.8 N=3 ticks=2 work=20s + uH: HOLD veto micro>=0.6 persist=1 ladder (0.6, 0.75, 0.9) + e: stall arm=0.8 N=3 ticks=1 work=20s | 6 / 29 | -653 (6/6) / - | -653 | -7.8 / - | 145 / 369461 |
| NEAR_N2_U7_C4 | U7 | s: same-side book took target (<=600 s) arm=0.7 take | 6 / 29 | +1038 (6/6) / - | +1038 | 9.7 / - | 113 / 262091 |
| NEAR_N2_H7_B1 | H7 | b: rev arm=0.8 X=4 N=5 | 6 / 29 | -78 (6/6) / - | -100 | -1.1 / - | 80 / 108927 |
| NEAR_N2_A7_B1 | A7 | r: es_dd300<=-2 bps arm=0.8 persist=3 + a: ladder m1=0.8 f1=0.65 / .9 f2=0.7 / .95 f3=0.9 mode=1 + s: same-side book took target (<=600 s) arm=0.7 take | 6 / 29 | +703 (6/6) / - | +237 | 0.5 / - | 191 / 167414 |
| NEAR_N2_O7_B1 | O7 | c: flow pulled_against_mult>=20 arm=0.8 persist=3 dd>=2 + s: opposite-side signal in 120 s arm=0.7 take | 6 / 29 | -15 (6/6) / - | -15 | 0.5 / - | 11 / 14846 |
| NEAR_N2_P7x_S5 | P7 | asia:c: flow pulled_against_mult>=5 arm=0.8 persist=1 dd>=0 ; asia:r: es_dd300<=-1 bps arm=0.8 persist=1 ; asia:s: same-side book took target (<=600 s) arm=0.7 take ; london:a: ladder m1=0.7 f1=0.65 / .9 f2=0.7 / .95 f3=0.8 mode=1 ; london:c: flow pulled_against_mult>=5 arm=0.8 persist=1 dd>=0 ; london:r: rty_pown5>=2x arm=0.8 persist=1 ; nyam:u: spread>=3 ticks arm=0.8 persist=3 ; nyam:t: clock m_sessch<=40min arm=0.8 floor.6 | 6 / 12 | -1804 (6/6) / - | -1804 | 17.4 / - | 437 / 2185520 |
| NEAR_N2_P7_S5 | P7 | asia:c: flow pulled_against_mult>=5 arm=0.8 persist=1 dd>=0 ; asia:r: es_dd300<=-1 bps arm=0.8 persist=1 ; asia:s: same-side book took target (<=600 s) arm=0.7 take ; london:a: ladder m1=0.7 f1=0.65 / .9 f2=0.7 / .95 f3=0.9 mode=1 ; london:c: flow pulled_against_mult>=5 arm=0.8 persist=1 dd>=0 ; london:r: es_dd300<=-1 bps arm=0.8 persist=1 ; nyam:f: zone arm=.8 N=30 floor 0.65 ; nyam:t: clock m_sessch<=40min arm=0.8 floor.6 | 6 / 12 | +1311 (6/6) / - | +1311 | 33.8 / - | 625 / 1890537 |
| NEAR_N2_P7x_V1 | P7 | learned arm=0.8 p*<0.75 persist=1 | 6 / 12 | -7478 (6/6) / - | -7478 | -10.5 / - | 389 / 2052964 |
| PTR_P7_NZX00 | P7 | reference P7 12/7/7 (W-N identity set) | 12 / 12 | - | - | - | - |

Exact versus first-order, set by set and month (book P7 for the P7 sets, trade by trade on the entry timestamp). Matched trades are the same entries in both runs: there the hook reproduces the first-order outcome of the rule to within a few dollars per trade (median difference about $15). The gap in the totals is the entry stream: an early exit frees the book, which then re-enters (trades only in the new run) while some entries of the reference never happen (trades only in the reference); the first-order frame cannot see that, so the exact column decides.

| set | month | exact book Delta $ vs reference | first-order Delta $ (same trades) | matched trades: exact / first-order Delta $ | trades only in the new run (n / $) | trades only in the reference (n / $) | NearTarget exits |
|---|---|---|---|---|---|---|---|
| NEAR_N2_A7_B1 | 202605 | -66 | 827 | 1470 / 1448 (42 matched) | 9 / 2061 | 3 / 3596 | 21 |
| NEAR_N2_A7_B1 | 202606 | 2790 | 289 | 2319 / 1219 (64 matched) | 23 / 8394 | 14 / 7923 | 48 |
| NEAR_N2_A7_B1 | 202607 | 2138 | 426 | 999 / 855 (65 matched) | 19 / 76 | 7 / -1063 | 42 |
| NEAR_N2_A7_B1 | 202608 | -2587 | 142 | 784 / 502 (41 matched) | 6 / -4048 | 3 / -677 | 18 |
| NEAR_N2_A7_B1 | 202609 | -1500 | -4072 | -3195 / -3275 (37 matched) | 11 / -433 | 6 / -2127 | 27 |
| NEAR_N2_A7_B1 | 202610 | 5433 | -4044 | -4270 / -3008 (59 matched) | 21 / 10252 | 14 / 548 | 35 |
| NEAR_N2_H7_B1 | 202605 | 737 | 705 | 737 / 705 (27 matched) | 0 / 0 | 0 / 0 | 9 |
| NEAR_N2_H7_B1 | 202606 | -308 | -1264 | -308 / -1264 (41 matched) | 0 / 0 | 0 / 0 | 20 |
| NEAR_N2_H7_B1 | 202607 | -4958 | -5085 | -4958 / -5085 (37 matched) | 0 / 0 | 0 / 0 | 18 |
| NEAR_N2_H7_B1 | 202608 | -986 | 1273 | 1316 / 1273 (32 matched) | 1 / -2302 | 0 / 0 | 9 |
| NEAR_N2_H7_B1 | 202609 | 801 | 3880 | 801 / 3880 (28 matched) | 0 / 0 | 0 / 0 | 8 |
| NEAR_N2_H7_B1 | 202610 | 2104 | 4798 | 3078 / 4798 (35 matched) | 1 / -974 | 0 / 0 | 16 |
| NEAR_N2_K7_B1 | 202605 | 7874 | 2895 | -886 / -1972 (199 matched) | 58 / 3793 | 27 / -4967 | 92 |
| NEAR_N2_K7_B1 | 202606 | -1679 | 3349 | 2068 / 4603 (264 matched) | 108 / 6226 | 54 / 9973 | 130 |
| NEAR_N2_K7_B1 | 202607 | 10095 | 5430 | 2649 / 6496 (314 matched) | 78 / 15400 | 58 / 7954 | 133 |
| NEAR_N2_K7_B1 | 202608 | -1777 | -1567 | 1514 / -632 (211 matched) | 62 / -3125 | 35 / 166 | 77 |
| NEAR_N2_K7_B1 | 202609 | 18694 | 3806 | 3345 / 3730 (211 matched) | 56 / 1219 | 34 / -14130 | 99 |
| NEAR_N2_K7_B1 | 202610 | -17432 | -15444 | -15409 / -13601 (249 matched) | 65 / -1057 | 35 / 965 | 105 |
| NEAR_N2_K7_C3 | 202605 | -7488 | -2265 | -2569 / -2265 (223 matched) | 2 / -124 | 3 / 4795 | 3 |
| NEAR_N2_K7_C3 | 202606 | -214 | 1031 | 1041 / 1031 (318 matched) | 4 / -1255 | 0 / 0 | 2 |
| NEAR_N2_K7_C3 | 202607 | 5634 | 4420 | 4435 / 4420 (372 matched) | 1 / 1199 | 0 / 0 | 3 |
| NEAR_N2_K7_C3 | 202608 | -559 | -563 | -559 / -563 (246 matched) | 0 / 0 | 0 / 0 | 1 |
| NEAR_N2_K7_C3 | 202609 | 0 | 0 | 0 / 0 (245 matched) | 0 / 0 | 0 / 0 | 0 |
| NEAR_N2_K7_C3 | 202610 | 3404 | 4564 | 4582 / 4564 (284 matched) | 6 / -1178 | 0 / 0 | 3 |
| NEAR_N2_K7_D2 | 202605 | 4798 | 1553 | 604 / 1720 (208 matched) | 55 / -4054 | 18 / -8247 | 68 |
| NEAR_N2_K7_D2 | 202606 | 1003 | 251 | 1557 / 569 (270 matched) | 105 / 3761 | 48 / 4315 | 108 |
| NEAR_N2_K7_D2 | 202607 | -1350 | 4399 | -1002 / -2361 (316 matched) | 66 / 10367 | 56 / 10716 | 93 |
| NEAR_N2_K7_D2 | 202608 | 5112 | -1562 | 149 / -1245 (214 matched) | 59 / -1307 | 32 / -6270 | 60 |
| NEAR_N2_K7_D2 | 202609 | 26650 | 4389 | 4249 / 6016 (198 matched) | 40 / 7455 | 47 / -14946 | 59 |
| NEAR_N2_K7_D2 | 202610 | -19082 | -7977 | -15953 / -11760 (245 matched) | 61 / -1983 | 39 / 1145 | 70 |
| NEAR_N2_M7_B1 | 202605 | 2400 | 1247 | 641 / 1675 (155 matched) | 12 / 5355 | 2 / 3596 | 47 |
| NEAR_N2_M7_B1 | 202606 | 1638 | 11278 | 11654 / 13141 (189 matched) | 28 / -7908 | 13 / 2108 | 43 |
| NEAR_N2_M7_B1 | 202607 | 2202 | -3905 | -1556 / -1829 (184 matched) | 33 / 4501 | 12 / 743 | 64 |
| NEAR_N2_M7_B1 | 202608 | -10860 | -8581 | -7449 / -7595 (125 matched) | 21 / -6485 | 9 / -3075 | 42 |
| NEAR_N2_M7_B1 | 202609 | -195 | 775 | 514 / 1452 (123 matched) | 33 / 4168 | 8 / 4877 | 57 |
| NEAR_N2_M7_B1 | 202610 | -1314 | 8604 | 2914 / 6041 (153 matched) | 28 / -7796 | 10 / -3567 | 53 |
| NEAR_N2_M7_C3 | 202605 | -604 | 376 | 383 / 376 (157 matched) | 1 / -987 | 0 / 0 | 2 |
| NEAR_N2_M7_C3 | 202606 | 2249 | 2242 | 2249 / 2242 (202 matched) | 0 / 0 | 0 / 0 | 1 |
| NEAR_N2_M7_C3 | 202607 | 0 | 0 | 0 / 0 (196 matched) | 0 / 0 | 0 / 0 | 0 |
| NEAR_N2_M7_C3 | 202608 | 0 | 0 | 0 / 0 (134 matched) | 0 / 0 | 0 / 0 | 0 |
| NEAR_N2_M7_C3 | 202609 | 2134 | 2127 | 2134 / 2127 (131 matched) | 0 / 0 | 0 / 0 | 2 |
| NEAR_N2_M7_C3 | 202610 | -809 | -827 | -809 / -827 (163 matched) | 0 / 0 | 0 / 0 | 4 |
| NEAR_N2_M7_D2 | 202605 | 1132 | 107 | -506 / 536 (154 matched) | 13 / 6433 | 3 / 4795 | 46 |
| NEAR_N2_M7_D2 | 202606 | -2718 | 5320 | 5618 / 7124 (189 matched) | 27 / -6228 | 13 / 2108 | 40 |
| NEAR_N2_M7_D2 | 202607 | -1091 | -2835 | 398 / -330 (182 matched) | 30 / 1652 | 14 / 3141 | 56 |
| NEAR_N2_M7_D2 | 202608 | -8304 | -7479 | -6490 / -6621 (125 matched) | 19 / -4889 | 9 / -3075 | 38 |
| NEAR_N2_M7_D2 | 202609 | 3858 | 1991 | 1664 / 2669 (124 matched) | 30 / 4677 | 7 / 2484 | 51 |
| NEAR_N2_M7_D2 | 202610 | 152 | 7004 | 4299 / 7432 (153 matched) | 28 / -7714 | 10 / -3567 | 51 |
| NEAR_N2_O7_B1 | 202605 | 821 | 817 | 821 / 817 (12 matched) | 0 / 0 | 0 / 0 | 1 |
| NEAR_N2_O7_B1 | 202606 | -537 | -540 | -537 / -540 (14 matched) | 0 / 0 | 0 / 0 | 1 |
| NEAR_N2_O7_B1 | 202607 | 1423 | 1412 | 1423 / 1412 (11 matched) | 0 / 0 | 0 / 0 | 3 |
| NEAR_N2_O7_B1 | 202608 | 79 | 72 | 79 / 72 (10 matched) | 0 / 0 | 0 / 0 | 2 |
| NEAR_N2_O7_B1 | 202609 | -2174 | -2188 | -2174 / -2188 (11 matched) | 0 / 0 | 0 / 0 | 4 |
| NEAR_N2_O7_B1 | 202610 | 0 | 0 | 0 / 0 (9 matched) | 0 / 0 | 0 / 0 | 0 |
| NEAR_N2_P7_B1 | 202605 | -4170 | -12572 | -32415 / -19944 (115 matched) | 106 / 38025 | 24 / 9781 | 111 |
| NEAR_N2_P7_B1 | 202606 | -15190 | 688 | -31320 / -3492 (178 matched) | 62 / 46963 | 25 / 30833 | 116 |
| NEAR_N2_P7_B1 | 202607 | 9233 | 15671 | 11591 / 23397 (208 matched) | 68 / 22326 | 6 / 24685 | 134 |
| NEAR_N2_P7_B1 | 202608 | -9395 | 3306 | -5205 / -3587 (149 matched) | 72 / -9923 | 21 / -5733 | 101 |
| NEAR_N2_P7_B1 | 202609 | 5165 | 33119 | 16179 / 26573 (150 matched) | 93 / 3191 | 20 / 14205 | 125 |
| NEAR_N2_P7_B1 | 202610 | -2058 | 10440 | -11477 / -1834 (123 matched) | 68 / 13484 | 41 / 4065 | 89 |
| NEAR_N2_P7_B2 | 202605 | -2353 | -11802 | -33467 / -20883 (116 matched) | 105 / 36104 | 23 / 4990 | 110 |
| NEAR_N2_P7_B2 | 202606 | -17308 | 2224 | -29809 / -1955 (178 matched) | 62 / 43334 | 25 / 30833 | 117 |
| NEAR_N2_P7_B2 | 202607 | 9232 | 15378 | 9635 / 23103 (208 matched) | 66 / 24281 | 6 / 24685 | 135 |
| NEAR_N2_P7_B2 | 202608 | -9578 | 2396 | -6115 / -4497 (149 matched) | 72 / -9196 | 21 / -5733 | 101 |
| NEAR_N2_P7_B2 | 202609 | 4121 | 30785 | 15030 / 25599 (150 matched) | 93 / 3296 | 20 / 14205 | 126 |
| NEAR_N2_P7_B2 | 202610 | -2251 | 10958 | -12692 / -3067 (123 matched) | 68 / 14506 | 41 / 4065 | 90 |
| NEAR_N2_P7_C4 | 202605 | -11639 | -18198 | -18865 / -18198 (135 matched) | 9 / -3558 | 4 / -10784 | 32 |
| NEAR_N2_P7_C4 | 202606 | -4299 | 6006 | -8280 / 1882 (194 matched) | 28 / 11383 | 9 / 7401 | 44 |
| NEAR_N2_P7_C4 | 202607 | -5622 | 15735 | 5963 / 6437 (211 matched) | 20 / -10947 | 3 / 637 | 55 |
| NEAR_N2_P7_C4 | 202608 | 36822 | 23991 | 26259 / 28369 (164 matched) | 26 / 17013 | 6 / 6450 | 38 |
| NEAR_N2_P7_C4 | 202609 | 14285 | 49018 | 26989 / 37470 (154 matched) | 46 / -18432 | 16 / -5728 | 52 |
| NEAR_N2_P7_C4 | 202610 | -12090 | 4660 | -498 / 4455 (146 matched) | 22 / 508 | 18 / 12100 | 39 |
| NEAR_N2_P7_D3 | 202605 | -27265 | -29253 | -40987 / -24245 (122 matched) | 61 / 15474 | 17 / 1752 | 86 |
| NEAR_N2_P7_D3 | 202606 | -32696 | 7085 | -24380 / 1465 (182 matched) | 38 / 20641 | 21 / 28957 | 111 |
| NEAR_N2_P7_D3 | 202607 | 25536 | 37892 | 32242 / 46964 (198 matched) | 52 / 23256 | 16 / 29961 | 125 |
| NEAR_N2_P7_D3 | 202608 | 20115 | 6428 | -116 / 3666 (148 matched) | 52 / 15400 | 22 / -4832 | 97 |
| NEAR_N2_P7_D3 | 202609 | -15550 | -3181 | -10519 / -483 (152 matched) | 51 / 17483 | 18 / 22514 | 106 |
| NEAR_N2_P7_D3 | 202610 | -16757 | 13347 | -24575 / -5415 (139 matched) | 53 / 5817 | 25 / -2001 | 88 |
| NEAR_N2_P7x_B1 | 202605 | 9105 | -56778 | -25935 / -47807 (80 matched) | 55 / 23267 | 14 / -11772 | 66 |
| NEAR_N2_P7x_B1 | 202606 | -77082 | 4890 | -55139 / -7727 (116 matched) | 35 / 41855 | 13 / 63799 | 81 |
| NEAR_N2_P7x_B1 | 202607 | -61073 | 42707 | -9103 / 39741 (107 matched) | 41 / 11582 | 20 / 63552 | 58 |
| NEAR_N2_P7x_B1 | 202608 | 78748 | 41627 | 8246 / 26135 (109 matched) | 61 / 61653 | 41 / -8849 | 88 |
| NEAR_N2_P7x_B1 | 202609 | -25799 | 45689 | -27415 / 3801 (87 matched) | 45 / 6842 | 16 / 5226 | 64 |
| NEAR_N2_P7x_B1 | 202610 | 9638 | 17848 | -10567 / 2673 (91 matched) | 36 / 7454 | 18 / -12751 | 60 |
| NEAR_N2_P7x_B2 | 202605 | 32037 | -20165 | -24998 / -60001 (76 matched) | 56 / 35360 | 18 / -21675 | 69 |
| NEAR_N2_P7x_B2 | 202606 | -32958 | 3524 | -66742 / -20583 (109 matched) | 49 / 77337 | 20 / 43553 | 85 |
| NEAR_N2_P7x_B2 | 202607 | -28823 | 27033 | 4061 / 18379 (99 matched) | 55 / 19396 | 28 / 52280 | 70 |
| NEAR_N2_P7x_B2 | 202608 | 37634 | 3826 | -14302 / -11384 (120 matched) | 65 / 15902 | 30 / -36034 | 87 |
| NEAR_N2_P7x_B2 | 202609 | -30599 | 53224 | -257 / 10832 (82 matched) | 59 / -18308 | 21 / 12034 | 65 |
| NEAR_N2_P7x_B2 | 202610 | -9681 | 18838 | -26998 / -6278 (93 matched) | 45 / 4008 | 16 / -13310 | 61 |
| NEAR_N2_P7x_C4 | 202605 | 9848 | -31486 | 8571 / -26085 (91 matched) | 14 / -10592 | 3 / -11868 | 23 |
| NEAR_N2_P7x_C4 | 202606 | -8453 | 9991 | -32348 / -12074 (123 matched) | 17 / 21651 | 6 / -2244 | 31 |
| NEAR_N2_P7x_C4 | 202607 | -14774 | 27280 | 8569 / 13666 (119 matched) | 27 / -21640 | 8 / 1702 | 30 |
| NEAR_N2_P7x_C4 | 202608 | 73374 | 40882 | 33980 / 32854 (125 matched) | 33 / 30266 | 25 / -9128 | 35 |
| NEAR_N2_P7x_C4 | 202609 | 7571 | 84607 | 14338 / 28852 (96 matched) | 23 / -19381 | 7 / -12614 | 30 |
| NEAR_N2_P7x_C4 | 202610 | 9715 | 7951 | -3373 / -1286 (104 matched) | 14 / 8080 | 5 / -5008 | 27 |
| NEAR_N2_P7x_D3 | 202605 | 26300 | -47757 | -22782 / -42189 (80 matched) | 52 / 37310 | 14 / -11772 | 64 |
| NEAR_N2_P7x_D3 | 202606 | -108400 | 714 | -73983 / -21755 (113 matched) | 32 / 37769 | 16 / 72186 | 71 |
| NEAR_N2_P7x_D3 | 202607 | -57361 | 59516 | -2978 / 48929 (103 matched) | 39 / 7541 | 24 / 61924 | 57 |
| NEAR_N2_P7x_D3 | 202608 | 33440 | 10611 | -12947 / 1741 (108 matched) | 49 / 27506 | 42 / -18880 | 78 |
| NEAR_N2_P7x_D3 | 202609 | -40788 | 631 | -54050 / -18517 (88 matched) | 40 / 13699 | 15 / 436 | 60 |
| NEAR_N2_P7x_D3 | 202610 | -11604 | 22691 | -12132 / -2011 (90 matched) | 33 / -7257 | 19 / -7785 | 56 |
| NEAR_N2_U7_B1 | 202605 | 16543 | 14684 | 14995 / 14684 (52 matched) | 1 / 1548 | 0 / 0 | 22 |
| NEAR_N2_U7_B1 | 202606 | -11972 | -12092 | -11972 / -12092 (48 matched) | 0 / 0 | 0 / 0 | 22 |
| NEAR_N2_U7_B1 | 202607 | -3701 | 4159 | -3701 / 4159 (63 matched) | 0 / 0 | 0 / 0 | 36 |
| NEAR_N2_U7_B1 | 202608 | 359 | 3519 | -916 / 3519 (41 matched) | 1 / 1275 | 0 / 0 | 21 |
| NEAR_N2_U7_B1 | 202609 | -5835 | -3532 | -4175 / -2487 (49 matched) | 2 / 743 | 1 / 2403 | 23 |
| NEAR_N2_U7_B1 | 202610 | 8967 | 9529 | 8967 / 9529 (41 matched) | 0 / 0 | 0 / 0 | 19 |
| NEAR_N2_U7_B2 | 202605 | 16543 | 14684 | 14995 / 14684 (52 matched) | 1 / 1548 | 0 / 0 | 22 |
| NEAR_N2_U7_B2 | 202606 | -11972 | -12092 | -11972 / -12092 (48 matched) | 0 / 0 | 0 / 0 | 22 |
| NEAR_N2_U7_B2 | 202607 | -3701 | 4159 | -3701 / 4159 (63 matched) | 0 / 0 | 0 / 0 | 36 |
| NEAR_N2_U7_B2 | 202608 | 83 | 3243 | -1192 / 3243 (41 matched) | 1 / 1275 | 0 / 0 | 21 |
| NEAR_N2_U7_B2 | 202609 | -5835 | -3532 | -4175 / -2487 (49 matched) | 2 / 743 | 1 / 2403 | 23 |
| NEAR_N2_U7_B2 | 202610 | 8967 | 9529 | 8967 / 9529 (41 matched) | 0 / 0 | 0 / 0 | 19 |
| NEAR_N2_U7_C4 | 202605 | 20671 | 15774 | 15781 / 15774 (51 matched) | 1 / 2398 | 1 / -2492 | 19 |
| NEAR_N2_U7_C4 | 202606 | -7581 | -6290 | -7581 / -6290 (48 matched) | 0 / 0 | 0 / 0 | 21 |
| NEAR_N2_U7_C4 | 202607 | -4978 | -887 | -4978 / -887 (63 matched) | 0 / 0 | 0 / 0 | 23 |
| NEAR_N2_U7_C4 | 202608 | 11307 | 14933 | 9612 / 14933 (41 matched) | 1 / 1695 | 0 / 0 | 17 |
| NEAR_N2_U7_C4 | 202609 | -3746 | -7275 | -7110 / -7275 (50 matched) | 1 / 3364 | 0 / 0 | 19 |
| NEAR_N2_U7_C4 | 202610 | 11521 | 11378 | 11521 / 11378 (41 matched) | 0 / 0 | 0 / 0 | 14 |
| NEAR_N2_U7_D3 | 202605 | 8792 | 11978 | 8792 / 11978 (52 matched) | 0 / 0 | 0 / 0 | 22 |
| NEAR_N2_U7_D3 | 202606 | -8581 | -9749 | -8581 / -9749 (48 matched) | 0 / 0 | 0 / 0 | 25 |
| NEAR_N2_U7_D3 | 202607 | -9180 | -4591 | -9180 / -4591 (63 matched) | 0 / 0 | 0 / 0 | 30 |
| NEAR_N2_U7_D3 | 202608 | -1482 | 1972 | -3390 / 1972 (41 matched) | 1 / 1908 | 0 / 0 | 25 |
| NEAR_N2_U7_D3 | 202609 | -12778 | -179 | -1010 / 726 (48 matched) | 2 / -6967 | 2 / 4800 | 23 |
| NEAR_N2_U7_D3 | 202610 | 6126 | 5892 | 6126 / 5892 (41 matched) | 0 / 0 | 0 / 0 | 20 |

## 8. Processes (keep running to 12:00Z)

9581 python3 -u nz2_page.py
2324965 python3 -u nz2_exact.py chain
3052907 python3 -u nz2_feed.py

Caveats stated once. First-order; engine market exits are about 0.4 pt cheaper than the 1.2 pt used here; "other books" and the opposite-signal rule use the base stack's own trade list (the exact hook uses the engine's own events); ES/RTY features are 1-s mid and 5-s cancel flow, not a full book; h-q cannot be replayed on the frozen live week (no print/queue extracts for it), so mode A sets show "not replayable" for the live week; the learned exit uses the walk-forward fold models for each trade's quarter (none before 2024Q1) and the all-data model for the live week.
