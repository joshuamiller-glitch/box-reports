# REPORT FA4 - direct no-edge calibration of the full gate pipeline (gates 1-7)

Written 2026-10-17 by research worker FA. Analysis only; gates, thresholds and scoring code are those of ap_sw_pipe.py (score stage) and t3_score.py, unaltered. Code: code/census/night_ins/ap_sw_nullcal.py (copy of the pipeline's selection/score logic with random worlds; the pipeline's SW chance script ap_sw_chance.py counted gate 3 only). Data: outputs/autopilot/FA4_cells.csv, FA4_screened.csv, b/nullcal/. Nothing purchased.

## 1. Design

* **World.** A whole real grid of an SW family on NQ is re-run with no edge, then put through the real pipeline: clean-only selection (>=100 clean trades, positive weekly Sharpe in both clean halves, top 10 per group), then scoring on the pair window exactly as the pipeline does at the 20% additive share (sleeve scaled to the pair's clean weekly SD).
* **Two no-edge worlds.** (a) **Random-entry**: same trade count, random valid entry rows, alternating sides (timing destroyed; the ap_sw_chance.py null). (b) **Sign-randomised**: the family's real entry rows, exits and filters, but each entry's side set by a hash of the entry row and the world, so neighbouring parameter cells share the same entries and sides (keeps the real timing structure and neighbour dependence that plateau needs, kills direction edge).
* **Families / grid shapes** (all NQ, real grids): 5-min trend family SW1 (96 cells, regime-gated ST/Donchian/EMA trend), fade family SW2 (96, VWAP-band and RSI fades), time-of-day family SW5 (288, clock-anchored entries), ML daily family SW13 (16, daily frozen LightGBM at the open), and SW19 (48, prior-day reference levels) **as the substitute for the FVG-style limit family: the FVG limit simulator (RZ, 1-tick trade-through fills) is not part of the SW engine and was not re-implemented; this row is therefore not an FVG calibration**. Every family has >= 2,080 grid cells per world type.
* **Gates** applied cumulatively, later gates computed only for cells that passed all earlier ones: 3 (uplift >= +0.10 each span), worst week, 4a own null (100 random-entry replicates of the cell at p95 on all-in standalone Sharpe), 4b bootstrap lower bound > 0 (3,000 block draws), 6 worst-decile correlation <= +0.30, 5a plateau (the +-25% neighbours re-run in the same world, >= 75% keep >= 75% of the uplift), 5b 2x slippage (same entries, 2 ticks per side). Gates 1 (pre-registration), 2 (selection, clean only) and 7 (executable spec) hold by construction. Passing 5b is the FOUND-PENDING condition (FOUND adds replication).

## 2. Result - cumulative pass rate per gate (both worlds pooled)

25,664 no-edge grid cells, 3,202 selected cells.

| gate | cells passing (cumulative) | % of selected cells | per 1,000 grid cells | % of previous gate |
|---|---|---|---|---|
| 2 clean-only selection (>=100 clean trades, both clean halves positive, top 10) | 3202 | 100.00% | 124.77 |  |
| 3 uplift >= +0.10 on clean, H1, H2 at 20% | 113 | 3.53% | 4.40 | 4% |
| 3b worst week not worse by more than 20% (all-in) | 63 | 1.97% | 2.45 | 56% |
| 4a own timing-destroyed null p95 on standalone Sharpe | 56 | 1.75% | 2.18 | 89% |
| 4b bootstrap 90% lower bound of the uplift > 0 | 34 | 1.06% | 1.32 | 61% |
| 6 worst-decile correlation with the pair <= +0.30 | 31 | 0.97% | 1.21 | 91% |
| 5a plateau >= 75% of +-25% neighbours keep >= 75% of the uplift | 0 | 0.00% | 0.00 | 0% |
| 5b 2x slippage uplift >= +0.10 on each span | 0 | 0.00% | 0.00 |  |

Random-entry world (12,832 cells, 1503 selected): 1503 / 59 / 35 / 31 / 18 / 17 / 0 / 0 (selection, 3, 3b, 4a, 4b, 6, 5a, 5b). Sign-randomised world (12,832 cells, 1699 selected): 1699 / 54 / 28 / 25 / 16 / 14 / 0 / 0.

By family and world:

| family / world | grid cells | selected | gate 3 | 3b | 4a null | 4b boot | 6 wd corr | 5a plateau | 5b 2x slip |
|---|---|---|---|---|---|---|---|---|---|
| SW13_NQ | 2,080 | 469 | 13 | 7 | 6 | 4 | 4 | 0 | 0 |
| SW13_NQ_SIGN | 2,080 | 657 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| SW19_NQ | 2,112 | 298 | 10 | 6 | 6 | 4 | 4 | 0 | 0 |
| SW19_NQ_SIGN | 2,112 | 328 | 12 | 0 | 0 | 0 | 0 | 0 | 0 |
| SW1_NQ | 4,224 | 438 | 17 | 11 | 9 | 5 | 4 | 0 | 0 |
| SW1_NQ_SIGN | 4,224 | 432 | 30 | 20 | 18 | 12 | 10 | 0 | 0 |
| SW2_NQ | 2,112 | 218 | 15 | 8 | 7 | 3 | 3 | 0 | 0 |
| SW2_NQ_SIGN | 2,112 | 202 | 8 | 4 | 4 | 4 | 4 | 0 | 0 |
| SW5_NQ | 2,304 | 80 | 4 | 3 | 3 | 2 | 2 | 0 | 0 |
| SW5_NQ_SIGN | 2,304 | 80 | 4 | 4 | 3 | 0 | 0 | 0 | 0 |

## 3. Reading

1. **Gate 3 chance per selected cell is 3.5% (113/3202), 0.44 per 100 grid cells**, consistent with the 5.9% (SW rule, iid) of FA1 and the observed 4.6-5.0% in the real SW sweeps.
2. **The own-null gate does not discriminate for clean-selected no-edge cells: 56 of the 63 that clear worst-week pass it (89%)**, because the cell's all-in standalone Sharpe contains the clean span it was selected on while the random-entry null replicates were not selected. FA1 had assumed 5% nominal to 48%; the direct measure is 89%. The bootstrap gate then passes 61% (34/56), worst-decile correlation 91% (31/34).
3. **LEAD-grade rate (through gates 3, 4a, 4b, 6): 31 of 3,202 selected cells = 0.97%, 1.21 per 1,000 grid cells.** Applied to the 2,603 cells the program read, that is about 25 false LEAD-grade cells expected, against 65 report-level LEAD labels (13-14 independent registry leads): LEAD status carries little information, as FA1 concluded (its 1-43 range brackets this).
4. **Plateau removes every one: 0 of 31 no-edge cells that reach it pass** (plateau share of the survivors: random-entry mean 0.04, sign-randomised mean 0.21, maximum 0.50; the gate needs 0.75). 2x slippage is never reached. **Full-gate (FOUND-PENDING-equivalent) no-edge pass rate: 0 of 25,664 grid cells and 0 of 3,202 selected cells. 95% upper bound (rule of three): 0.117 per 1,000 grid cells, 0.094% per selected cell.**
5. **Resulting expected false FOUND-PENDING for the program: 0 (point), at most 2.4 (95% upper bound) over the 2,603 cells read**, versus the FA1 chain estimate of 0.06-11 (central 0.5-2.2), which assumed plateau/2x-slip/spec pass rates of 5-25% that the direct calibration puts below 9% (0/31, 95% upper bound 9.4%) and in these worlds at 0. Observed: 4 FOUND-PENDING signals. At face value the gate set is therefore a strong filter against no-edge cells of these shapes, and the 4 survivors are unlikely to be purely noise through the gates; what remains uncertain is edge that is real but regime-specific (the clean-window premium), which no no-edge null tests. This does not change any status: FOUND stays 0 and replication/live weeks are still required.

## 4. Limitations (stated, not softened)

* The plateau test of a random-entry cell uses independent random draws for its neighbours, which makes plateau nearly impossible by construction; the sign-randomised world (shared entries) is the fairer test and also gives 0 of 14 (max share 0.50), but it keeps real timing, so a family whose real signal timing carries edge would behave differently. Neighbour sets are small (2-12 cells), so a 0.75 share is coarse.
* SW13 sign world: the daily-ML cell has few distinct entry rows and the hash side rule gave 0 gate-3 passes in 657 selected cells; its information is in the random-entry world only (13 of 469 reach gate 3, 4 reach gate 6, 0 plateau).
* The FVG-style limit-order family and the K4 daily GBM walk-forward were not reproduced in this engine (see section 1); the ML-daily and levels rows are proxies. A calibration of those engines needs their own simulators and would be a new run, not part of this task.
* One instrument (NQ), the 20% share, additive framing only; 0 observed means an upper bound of 0.12 per 1,000 cells, not zero. Sample sizes of the gates after 4b (34, 31) are small.

DONE FA4
