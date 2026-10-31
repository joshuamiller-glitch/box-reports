# DS3_QUIT_RULES - T-QUIT-WHEN-UP section B: every "stop for the day" rule scored on the exact lock engine (agent QW-2, 2026-10-31)

Research only; no live / execution / chart change; UNTOUCHED never read (capped at label day 20260206). Preregs: `autopilot/QUITWHENUP_A_prereg.md` (sha 784c99ea...), `QUITWHENUP_B_prereg.md` (sha 64855684c1c3216b89d471d8c4a6e7ccaf6db67376a41f45f0d78739b31caa51) and `QUITWHENUP_B_prereg_addendum.md` (written after the selection-window scoring and before any recent look; shas in DECISIONS.md). Code `l2vast/ds3/code/quitwhenup/` (qw_cap, qw_core, qw_rules, qw_score, qw_B_sel, qw_B_look, qw_B_cells, qw_B_sens, qw_learn*, qw_B_doc); outputs `l2vast/ds3/out/quitwhenup/`.

## 0. Page 1 - the answer: a NULL. No quit rule beats the stack as it is on a recent look

1. **765 rule cells per base (8 groups) were scored on the exact lock engine, D6 composite and the stack as it is.** Looking at PRE and X' only, 146 of 765 D6 cells have a positive PRE+X' stack delta and 77 have PRE >= 0 AND X' >= 0; the largest PRE+X' gain of any stack-level cell is +1.20k/wk against an MDE of ~2-3k; the group Reality-Check p-values are G1 0.93, G2 0.78, G3 0.79, G4 0.85, G5 0.71, G6 0.90, G7 0.02, G8 0.76 (G7 is the size-UP inverse, which adds risk). Romano-Wolf survivors: 0.
2. **Tiers of the 51 looked-at cells (shortlists + canon): 14 CANDIDATE-RECENT, 23 DEAD, 11 LEAD, 3 weak (PRE+X>=0, one selection window negative).** No PASS and no CANDIDATE: every group's Reality-Check p on PRE+X' is >= 0.7 (G7 excepted: the size-UP inverse). The 14 CANDIDATE-RECENT cells (positive on PRE, X', L6M and HOLD) are all far below their MDE and are 3 distinct ideas repeated at stack / per-book / combination level: (a) **no entries after 12:00 on a chop day at noon (5-min ER20 in its lower PRE+X' tercile)**: stack +0.46k PRE+X', +0.56k L6M, +0.51k HOLD per week (MDE ~1.1k), keeps 100% of the mean, SD unchanged, random-day placebo rank 0.99, random-time rank 0.92 on PRE+X'; (b) per-book day quits at 4 own-R realised (fires on 4% of days, +1.04k L6M); (c) a Wednesday no-afternoon cell (a post-hoc weekday). None is promotable: group RC p 0.71, sub-MDE, and the ER-chop cell is one of 36 regime cells.
3. **The quit-at-+X family loses heavily at stack scale**: the stack makes its money early (Asia / London / NY-AM) and in a few big days; quitting at +2 K6-R ($4.8k, passed within hours on ~80% of days) turns the stack into a scalper: PRE+X' -7.85k / L6M -26.19k per week letting open trades run, -10.01k / -32.17k flattening. In the Rs units ($24k) the cut-off is rarely reached and the family is flat to slightly negative. Per-book day quits at the live 5R are already inside the base (identity tie-out); 4R and below are small.
4. **The directive's named rule - "stop entries at 12:00 ET when the day is up >= 2R"** (stack, K6-R, let open trades run): PRE+X' -0.55k, L6M +2.36k (MDE 2.36k), HOLD +1.98k, L3M +3.01k per week; the no-condition control "no entries after 12:00 regardless" is -0.53k PRE+X', +2.43k L6M. The recent-window gain is the NO-AFTERNOON effect, not the profit condition (the regardless control gains as much): the NY-PM trades of K6 (the only live afternoon entries; A6 trades Asia only) lost money in 2025-26 (the same story as the NY-PM end-skip, NP-1), while PRE+X' is slightly negative; the L6M block-bootstrap CI of the gain excludes zero (+0.8k .. +4.0k) and HOLD too, but the cell was named in advance, PRE+X' < 0, so it is DEAD on the selection rule and its recent gain is a regime fact (2025-26 NY-PM K6 losses), not a selected edge.
5. **The learned policy (walk-forward, weekly refit on 3 months and anchored) has out-of-sample rank IC between -0.16 and +0.14; see section 5 for the 108 cells and the shuffled-label placebo.**

## 1. Engine, tie-outs, units

Engine: `ss2_lib` lock engine (day entry test +5R realised / -2R, per-book day arm 2R keep 50% with the causal running-max SizeMult, week floor 12R) via `sundaydecision/sdlib` (A6 = PB7) with a quit overlay between the arm and the week floor (see prereg B). Tie-outs: the composite reproduces D1/SS-2 (43,493 $/wk L6M, +21.8k over the as-is stack); the capture of the engine state ties out to the engine daily P&L to 1e-9 on all 745 days; the per-book realised +5R LR cell (the live entry test) changes L6M by 0 and PRE by +0.1k (post-arm vs pre-arm realised accounting), i.e. identity within rounding; a rule that never fires (X = 1e9) returns the base to 0.0.
R units: K6-R = $2,400; Rs = $24,000 (sum of live BookR); own = each book's BookR x its running-max SizeMult. Tier definitions are in prereg B and never softened. Delta = rule minus base, stack $/week; MDE = 2.8 x paired weekly SE; "lambda" = SD_base / SD_rule over PRE+X' (>1 = the rule lowers SD) and the equal-risk delta = lambda x mean_rule - mean_base (label: STRUCTURE, it assumes you scale lots by lambda).

## 2. Group summary (selection windows only: PRE, X', PRE+X')

| base | group | cells | PRE+X' delta>0 | PRE>=0 & X>=0 | best PRE+X' delta | median | RC p (PRE+X') | PBO | RW survivors | best DSR (cum. trials) |
|---|---|---|---|---|---|---|---|---|---|---|
| D6 | G1_plus | 80 | 8 | 8 | +0.13k | -4.57k | 0.933 | 0.35 | 0 | 0.02 |
| D6 | G2_timeif | 224 | 50 | 12 | +0.92k | -0.16k | 0.779 | 0.43 | 0 | 0.31 |
| D6 | G3_trail | 72 | 15 | 15 | +1.20k | -1.90k | 0.785 | 0.21 | 0 | 0.04 |
| D6 | G4_count | 52 | 7 | 3 | +0.62k | -4.65k | 0.852 | 0.02 | 0 | 0.01 |
| D6 | G5_regime | 36 | 18 | 11 | +0.70k | -0.01k | 0.710 | 0.29 | 0 | 0.07 |
| D6 | G6_resume | 148 | 7 | 1 | +0.85k | -2.21k | 0.901 | 0.53 | 0 | 0.08 |
| D6 | G7_size | 62 | 10 | 10 | +8.87k | -0.39k | 0.024 | 0.13 | 0 | 0.02 |
| D6 | G8_combo | 91 | 31 | 17 | +0.38k | -0.04k | 0.757 | 0.12 | 0 | 0.01 |
| ASIS | G1_plus | 80 | 0 | 2 | +0.00k | -2.66k | 1.000 | 0.38 | 0 | 0.00 |
| ASIS | G2_timeif | 224 | 44 | 6 | +0.99k | -0.16k | 0.682 | 0.50 | 0 | 0.04 |
| ASIS | G3_trail | 72 | 10 | 7 | +1.85k | -1.13k | 0.649 | 0.35 | 0 | 0.24 |
| ASIS | G4_count | 52 | 2 | 0 | +0.04k | -2.94k | 0.965 | 0.53 | 0 | 0.04 |
| ASIS | G5_regime | 36 | 7 | 0 | +0.37k | -0.27k | 0.776 | 0.54 | 0 | 0.03 |
| ASIS | G6_resume | 148 | 12 | 0 | +0.99k | -1.28k | 0.855 | 0.49 | 0 | 0.07 |
| ASIS | G7_size | 62 | 16 | 10 | +8.84k | -0.19k | 0.017 | 0.00 | 1 | 0.09 |
| ASIS | G8_combo | 91 | 18 | 7 | +0.11k | -0.04k | 0.937 | 0.39 | 0 | 0.06 |

## 3.1 G1 quit at +X

Cells: 80. Top 5 by PRE+X' delta (selection windows only; the recent windows were NOT computed for cells outside the shortlist):

| cell | days fired | dPRE | dX' | dPRE+X' | MDE | mean kept | lambda | forgone/avoided $/wk |
|---|---|---|---|---|---|---|---|---|
| book plus own X=4 meas=R FL | 4% | +0.20k | +0.00k | +0.13k | 1.08k | 101% | 1.02 | -0.71k / +0.84k |
| book plus own X=4 meas=R LR | 4% | +0.20k | +0.00k | +0.13k | 1.08k | 101% | 1.02 | -0.71k / +0.84k |
| book plus own X=4 meas=RO LR | 4% | +0.20k | +0.00k | +0.12k | 1.09k | 101% | 1.02 | -0.74k / +0.86k |
| book plus own X=5 meas=R FL | 1% | +0.12k | +0.00k | +0.08k | 0.22k | 100% | 1.00 | +0.00k / +0.08k |
| book plus own X=5 meas=R LR | 1% | +0.12k | +0.00k | +0.08k | 0.22k | 100% | 1.00 | +0.00k / +0.08k |

Bottom 3:

| cell | days fired | dPRE | dX' | dPRE+X' | MDE |
|---|---|---|---|---|---|
| stack plus K6 X=1 meas=RO FL | 91% | -18.77k | -2.42k | -12.73k | 12.58k |
| stack plus K6 X=1 meas=RO LR | 91% | -16.67k | -2.53k | -11.44k | 12.15k |
| stack plus K6 X=1.5 meas=RO FL | 87% | -18.09k | +0.80k | -11.11k | 12.46k |

Shortlists (PRE+X' selection per sub-group) + prereg canon cells, ONE recent look - D6 composite:

- G1_plus_book: [18, 58, 19] (LEAD-set)
- G1_plus_stack: [12, 32, 52] (none with PRE>=0&X>=0 (top by PRE+X shown, weak/DEAD))
- canon: [42, 62, 75]

| id | cell | days fired (sel.) | dPRE | dX' | dPRE+X' (MDE) | dL3M | dL6M (MDE) | dHOLD | L6M mean kept | lambda=SD_base/SD_rule | equal-risk d (PRE+X') | L6M forgone / avoided $/wk | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 12 | stack plus Rs X=2 meas=R LR | 8% | -2.35k | +0.28k | -1.38k (3.10k) | +5.46k | +1.24k (7.34k) | +1.26k | 103% | 1.03 | -0.86k | -10.87k / +12.12k | DEAD |
| 18 | book plus own X=4 meas=R LR | 4% | +0.20k | +0.00k | +0.13k (1.08k) | +1.94k | +1.04k (1.73k) | +0.97k | 102% | 1.02 | +0.43k | -0.59k / +1.63k | CANDIDATE-RECENT |
| 19 | book plus own X=5 meas=R LR | 1% | +0.12k | +0.00k | +0.08k (0.22k) | +0.00k | +0.00k (0.00k) | +0.00k | 100% | 1.00 | -0.00k | +0.00k / +0.00k | CANDIDATE-RECENT |
| 32 | stack plus Rs X=2 meas=R FL | 8% | -2.43k | +0.14k | -1.48k (3.14k) | +5.46k | +1.09k (7.30k) | +1.04k | 103% | 1.02 | -1.06k | -11.32k / +12.41k | DEAD |
| 42 | stack plus K6 X=2 meas=RO LR | 82% | -12.01k | -0.77k | -7.85k (11.50k) | -27.92k | -26.19k (17.69k) | -23.80k | 40% | 1.71 | -0.21k | -130.61k / +104.42k | DEAD |
| 52 | stack plus Rs X=2 meas=RO LR | 9% | -3.50k | +0.14k | -2.15k (3.33k) | +4.25k | +1.27k (9.06k) | +1.17k | 103% | 1.03 | -1.61k | -13.63k / +14.89k | DEAD |
| 58 | book plus own X=4 meas=RO LR | 4% | +0.20k | +0.00k | +0.12k (1.09k) | +1.94k | +1.04k (1.73k) | +0.97k | 102% | 1.02 | +0.44k | -0.59k / +1.63k | CANDIDATE-RECENT |
| 62 | stack plus K6 X=2 meas=RO FL | 82% | -16.73k | +1.44k | -10.01k (12.58k) | -25.25k | -32.17k (20.00k) | -29.58k | 26% | 2.49 | +2.88k | -155.54k / +123.37k | DEAD |
| 75 | book plus own X=2 meas=RO FL | 38% | -3.92k | +0.52k | -2.28k (4.37k) | -0.49k | -2.13k (9.21k) | -1.58k | 95% | 1.07 | -1.15k | -24.69k / +22.57k | DEAD |

Same cells on the stack as it is (second base):

| id | cell | days fired (sel.) | dPRE | dX' | dPRE+X' (MDE) | dL3M | dL6M (MDE) | dHOLD | L6M mean kept | lambda=SD_base/SD_rule | equal-risk d (PRE+X') | L6M forgone / avoided $/wk | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 12 | stack plus Rs X=2 meas=R LR | 5% | -3.63k | +0.00k | -2.29k (2.27k) | -1.27k | -2.16k (5.75k) | -1.86k | 90% | 1.06 | -1.82k | -8.02k / +5.86k |  |
| 18 | book plus own X=4 meas=R LR | 8% | -1.34k | -0.05k | -0.86k (0.73k) | +0.12k | +0.16k (2.73k) | +0.22k | 101% | 1.02 | -0.70k | -2.56k / +2.72k |  |
| 19 | book plus own X=5 meas=R LR | 4% | +0.00k | +0.00k | +0.00k (0.00k) | +0.00k | +0.00k (0.00k) | +0.00k | 100% | 1.00 | +0.00k | +0.00k / +0.00k |  |
| 32 | stack plus Rs X=2 meas=R FL | 5% | -4.03k | +0.00k | -2.54k (2.32k) | -1.63k | -2.00k (6.00k) | -1.80k | 91% | 1.06 | -2.05k | -8.28k / +6.29k |  |
| 42 | stack plus K6 X=2 meas=RO LR | 81% | -9.88k | +5.96k | -4.02k (10.35k) | -14.32k | -16.19k (16.28k) | -17.25k | 25% | 1.47 | -0.96k | -112.73k / +96.54k |  |
| 52 | stack plus Rs X=2 meas=RO LR | 7% | -3.66k | +0.00k | -2.31k (2.52k) | -1.96k | -1.78k (5.95k) | -1.60k | 92% | 1.07 | -1.74k | -8.58k / +6.80k |  |
| 58 | book plus own X=4 meas=RO LR | 12% | -1.11k | -0.02k | -0.71k (0.87k) | +0.22k | +0.26k (3.43k) | +0.31k | 101% | 1.02 | -0.49k | -4.23k / +4.49k |  |
| 62 | stack plus K6 X=2 meas=RO FL | 81% | -15.37k | +5.92k | -7.50k (10.94k) | -12.98k | -20.19k (20.29k) | -18.59k | 7% | 2.12 | -4.18k | -135.53k / +115.34k |  |
| 75 | book plus own X=2 meas=RO FL | 54% | -6.61k | +1.78k | -3.51k (4.67k) | -2.64k | -1.01k (10.48k) | -2.32k | 95% | 1.16 | -2.36k | -27.50k / +26.49k |  |

Detail for the canon cells and the best looked-at cell of the group:

**stack plus K6 X=2 meas=RO LR** (group G1_plus, cell 42) - tier **DEAD**
- PRE+X' -7.85k/wk [95% CI weeks -15.52k .. +0.56k; 4-week blocks -16.68k .. +0.58k]; L6M -26.19k [-38.63k .. -14.42k; 4-wk -35.54k .. -17.53k]; HOLD -23.80k [-36.83k .. -10.64k]. Stack mean L6M 43.49k -> 17.30k, SD 42.85k -> 25.16k, maxDD 21.12k -> 41.13k, Sharpe 7.32 -> 4.96; worst-20-weeks (PRE+X') -981.18k -> -659.41k.
- controls: random-day placebo (real times) rank 0.73 (PRE+X') / 0.15 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.00 / 0.00 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.933; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.82; days affected 82% (sel.) / 88% (L6M).
- latency (trigger-to-order delay): 0 s -7.85k/-26.19k, 1 s -7.89k/-26.19k, 3 s -7.89k/-26.19k (PRE+X' / L6M, $/wk). Thresholds x0.5 -11.44k/-31.34k, x0.75 -8.60k/-28.41k, x1.25 -5.49k/-26.04k, x1.5 -4.73k/-25.03k (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) -7.85k / -26.19k / -23.80k; stress add-slip 0.45 -7.66k / -25.75k / -23.39k; live-cal join stop 2.45 -6.55k / -24.63k / -22.33k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -2.91k, 2024Q3 -18.68k, 2024Q4 -6.03k, 2025Q1 -24.46k, 2025Q2 -16.45k, 2025Q3 -15.67k, 2025Q4 -31.88k, 2026Q1 -29.09k; positive in 0 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon -1.43k|-12.22k, Tue -2.03k|-7.51k, Wed -1.43k|-2.13k, Thu -1.47k|-0.92k, Fri -1.62k|-4.19k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +6.69k/+5.66k/-20.32k; chop/mid/trend: +8.31k/+0.11k/-16.38k.
- per book $/wk (L6M; per planned lot in brackets): K6 -2.85k (-1.43k), P6 -16.46k (-2.35k), U6 +0.18k (+0.05k), H6 -6.46k (-1.61k), M6 -0.30k (-0.15k), A6 -1.07k (-1.07k).
- on the stack as it is (second base): PRE+X' -4.02k, L6M -16.19k (MDE 16.28k), HOLD -17.25k.

**stack plus K6 X=2 meas=RO FL** (group G1_plus, cell 62) - tier **DEAD**
- PRE+X' -10.01k/wk [95% CI weeks -18.47k .. -0.79k; 4-week blocks -20.25k .. -0.95k]; L6M -32.17k [-46.26k .. -18.42k; 4-wk -40.86k .. -23.35k]; HOLD -29.58k [-44.98k .. -13.51k]. Stack mean L6M 43.49k -> 11.33k, SD 42.85k -> 18.07k, maxDD 21.12k -> 53.69k, Sharpe 7.32 -> 4.52; worst-20-weeks (PRE+X') -981.18k -> -535.42k.
- controls: random-day placebo (real times) rank 0.46 (PRE+X') / 0.07 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.00 / 0.00 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.933; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.92; days affected 82% (sel.) / 88% (L6M).
- latency (trigger-to-order delay): 0 s -10.01k/-32.17k, 1 s -10.06k/-32.12k, 3 s -9.99k/-32.07k (PRE+X' / L6M, $/wk). Thresholds x0.5 -12.73k/-38.20k, x0.75 -11.11k/-34.65k, x1.25 -9.15k/-28.52k, x1.5 -7.50k/-30.15k (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) -10.01k / -32.17k / -29.58k; stress add-slip 0.45 -9.76k / -31.64k / -29.09k; live-cal join stop 2.45 -8.28k / -30.24k / -27.76k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -7.39k, 2024Q3 -23.13k, 2024Q4 -11.71k, 2025Q1 -31.61k, 2025Q2 -24.43k, 2025Q3 -26.01k, 2025Q4 -33.98k, 2026Q1 -21.33k; positive in 0 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon -1.71k|-15.90k, Tue -3.04k|-7.03k, Wed -1.06k|-3.50k, Thu -2.71k|+1.48k, Fri -1.65k|-8.15k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +11.22k/+3.08k/-24.84k; chop/mid/trend: +8.47k/-0.48k/-18.52k.
- per book $/wk (L6M; per planned lot in brackets): K6 -3.49k (-1.74k), P6 -20.33k (-2.90k), U6 -0.89k (-0.22k), H6 -6.32k (-1.58k), M6 -0.48k (-0.24k), A6 -1.61k (-1.61k).
- on the stack as it is (second base): PRE+X' -7.50k, L6M -20.19k (MDE 20.29k), HOLD -18.59k.

**book plus own X=2 meas=RO FL** (group G1_plus, cell 75) - tier **DEAD**
- PRE+X' -2.28k/wk [95% CI weeks -5.35k .. +0.67k; 4-week blocks -5.61k .. +0.99k]; L6M -2.13k [-8.75k .. +3.99k; 4-wk -7.81k .. +3.32k]; HOLD -1.58k [-7.43k .. +3.86k]. Stack mean L6M 43.49k -> 41.37k, SD 42.85k -> 35.15k, maxDD 21.12k -> 14.19k, Sharpe 7.32 -> 8.49; worst-20-weeks (PRE+X') -981.18k -> -908.08k.
- controls: random-day placebo (real times) rank n/a (PRE+X') / n/a (L6M); random-time placebo (uniform 09:30-14:00) rank n/a / n/a (200 draws each; n/a = per-book cell, not run); RC p of the group 0.933; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.35; days affected 38% (sel.) / 54% (L6M).
- latency (trigger-to-order delay): 0 s -2.28k/-2.13k, 1 s -2.30k/-2.32k, 3 s -2.35k/-2.35k (PRE+X' / L6M, $/wk). Thresholds x0.5 -4.71k/-16.55k, x0.75 -2.23k/-5.75k, x1.25 -1.75k/-0.31k, x1.5 -1.00k/+1.87k (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) -2.28k / -2.13k / -1.58k; stress add-slip 0.45 -2.23k / -2.11k / -1.56k; live-cal join stop 2.45 -2.17k / -1.63k / -1.15k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -7.39k, 2024Q3 -5.67k, 2024Q4 -5.06k, 2025Q1 -6.56k, 2025Q2 +1.56k, 2025Q3 -0.05k, 2025Q4 -5.24k, 2026Q1 +0.84k; positive in 2 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon -0.70k|+0.28k, Tue -0.74k|-4.28k, Wed -0.54k|+1.10k, Thu +0.20k|+0.49k, Fri -0.53k|+0.22k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +0.49k/+0.31k/-2.93k; chop/mid/trend: +0.64k/+0.58k/-3.34k.
- per book $/wk (L6M; per planned lot in brackets): K6 -0.63k (-0.31k), P6 -1.08k (-0.15k), U6 -0.01k (-0.00k), H6 -0.13k (-0.03k), M6 -0.17k (-0.08k), A6 -0.18k (-0.18k).
- on the stack as it is (second base): PRE+X' -3.51k, L6M -1.01k (MDE 10.48k), HOLD -2.32k.

**book plus own X=4 meas=R LR** (group G1_plus, cell 18) - tier **CANDIDATE-RECENT**
- PRE+X' +0.13k/wk [95% CI weeks -0.59k .. +0.89k; 4-week blocks -0.63k .. +0.94k]; L6M +1.04k [-0.01k .. +2.33k; 4-wk +0.05k .. +2.24k]; HOLD +0.97k [+0.07k .. +2.11k]. Stack mean L6M 43.49k -> 44.54k, SD 42.85k -> 43.06k, maxDD 21.12k -> 21.12k, Sharpe 7.32 -> 7.46; worst-20-weeks (PRE+X') -981.18k -> -951.22k.
- controls: random-day placebo (real times) rank n/a (PRE+X') / n/a (L6M); random-time placebo (uniform 09:30-14:00) rank n/a / n/a (200 draws each; n/a = per-book cell, not run); RC p of the group 0.933; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.23; days affected 4% (sel.) / 6% (L6M).
- latency (trigger-to-order delay): 0 s +0.13k/+1.04k, 1 s +0.13k/+1.04k, 3 s +0.13k/+1.04k (PRE+X' / L6M, $/wk). Thresholds x0.5 -1.87k/-1.87k, x0.75 -0.42k/+0.79k, x1.25 +0.08k/+0.00k, x1.5 +0.00k/+0.00k (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) +0.13k / +1.04k / +0.97k; stress add-slip 0.45 +0.13k / +1.05k / +0.98k; live-cal join stop 2.45 +0.14k / +1.07k / +1.00k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -1.71k, 2024Q3 +2.13k, 2024Q4 -0.04k, 2025Q1 +0.32k, 2025Q2 +0.52k, 2025Q3 +0.35k, 2025Q4 +2.06k, 2026Q1 +0.25k; positive in 6 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon +0.18k|+0.05k, Tue -0.02k|+0.08k, Wed -0.04k|+0.00k, Thu +0.24k|+0.30k, Fri -0.22k|+0.65k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +0.00k/+0.02k/+0.11k; chop/mid/trend: +0.32k/+0.04k/-0.24k.
- per book $/wk (L6M; per planned lot in brackets): K6 +0.09k (+0.05k), P6 +0.50k (+0.07k), U6 +0.00k (+0.00k), H6 +0.30k (+0.08k), M6 +0.14k (+0.07k), A6 +0.05k (+0.05k).
- on the stack as it is (second base): PRE+X' -0.86k, L6M +0.16k (MDE 2.73k), HOLD +0.22k.

**stack plus Rs X=2 meas=R LR** (group G1_plus, cell 12) - tier **DEAD**
- PRE+X' -1.38k/wk [95% CI weeks -3.65k .. +0.69k; 4-week blocks -3.34k .. +0.33k]; L6M +1.24k [-3.86k .. +6.34k; 4-wk -2.59k .. +5.40k]; HOLD +1.26k [-3.09k .. +5.43k]. Stack mean L6M 43.49k -> 44.74k, SD 42.85k -> 40.62k, maxDD 21.12k -> 21.12k, Sharpe 7.32 -> 7.94; worst-20-weeks (PRE+X') -981.18k -> -982.32k.
- controls: random-day placebo (real times) rank 0.16 (PRE+X') / 0.89 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.02 / 0.97 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.933; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.24; days affected 8% (sel.) / 12% (L6M).
- latency (trigger-to-order delay): 0 s -1.38k/+1.24k, 1 s -1.38k/+1.24k, 3 s -1.38k/+1.24k (PRE+X' / L6M, $/wk). Thresholds x0.5 -2.95k/-3.33k, x0.75 -2.95k/+1.38k, x1.25 -1.39k/+2.07k, x1.5 -0.69k/+2.18k (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) -1.38k / +1.24k / +1.26k; stress add-slip 0.45 -1.22k / +1.27k / +1.29k; live-cal join stop 2.45 -0.96k / +1.39k / +1.40k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -3.41k, 2024Q3 -5.04k, 2024Q4 -3.62k, 2025Q1 -3.44k, 2025Q2 +0.81k, 2025Q3 +1.57k, 2025Q4 +1.13k, 2026Q1 +1.34k; positive in 4 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon -0.33k|+0.47k, Tue -0.25k|-0.99k, Wed -0.33k|+0.00k, Thu -0.17k|+0.56k, Fri -0.32k|+1.24k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +0.00k/-0.23k/-1.17k; chop/mid/trend: +0.23k/+0.26k/-1.90k.
- per book $/wk (L6M; per planned lot in brackets): K6 +0.42k (+0.21k), P6 +1.91k (+0.27k), U6 -0.33k (-0.08k), H6 -0.84k (-0.21k), M6 +0.23k (+0.12k), A6 -0.10k (-0.10k).
- on the stack as it is (second base): PRE+X' -2.29k, L6M -2.16k (MDE 5.75k), HOLD -1.86k.

## 3.2 G2 quit at time T if up X (incl. Friday / weekday / regardless control)

Cells: 224. Top 5 by PRE+X' delta (selection windows only; the recent windows were NOT computed for cells outside the shortlist):

| cell | days fired | dPRE | dX' | dPRE+X' | MDE | mean kept | lambda | forgone/avoided $/wk |
|---|---|---|---|---|---|---|---|---|
| stack timeif K6 T=12:30 X=1 FL | 41% | -0.78k | +3.82k | +0.92k | 2.84k | 105% | 1.03 | -6.57k / +7.49k |
| stack timeif K6 T=12:30 X=0.5 FL | 45% | -0.57k | +3.38k | +0.89k | 2.97k | 105% | 1.02 | -7.00k / +7.89k |
| stack timeif K6 T=12:30 X=0 FL | 48% | -0.03k | +2.43k | +0.88k | 3.19k | 105% | 1.03 | -7.63k / +8.51k |
| stack timeif Rs T=12:30 X=0 FL | 48% | -0.03k | +2.43k | +0.88k | 3.19k | 105% | 1.03 | -7.63k / +8.51k |
| stack timeif K6 T=13:00 X=regardless FL | 80% | +0.14k | +2.07k | +0.85k | 3.49k | 105% | 1.05 | -10.05k / +10.90k |

Bottom 3:

| cell | days fired | dPRE | dX' | dPRE+X' | MDE |
|---|---|---|---|---|---|
| stack timeif K6 T=11:00 X=regardless FL | 97% | -6.58k | +3.88k | -2.71k | 6.94k |
| stack timeif K6 T=11:00 X=regardless LR | 97% | -4.31k | +1.63k | -2.11k | 4.60k |
| book timeif own T=11:00 X=regardless LR | 97% | -4.31k | +1.63k | -2.11k | 4.60k |

Shortlists (PRE+X' selection per sub-group) + prereg canon cells, ONE recent look - D6 composite:

- G2_timeif_book: [187, 62] (LEAD-set)
- G2_timeif_stack: [145, 202, 21] (LEAD-set)
- canon: [67, 72, 82, 160]

| id | cell | days fired (sel.) | dPRE | dX' | dPRE+X' (MDE) | dL3M | dL6M (MDE) | dHOLD | L6M mean kept | lambda=SD_base/SD_rule | equal-risk d (PRE+X') | L6M forgone / avoided $/wk | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 21 | stack timeif K6 T=11:00 X=2 LR dow=(4,) | 7% | +0.16k | +0.26k | +0.20k (1.62k) | -0.55k | -0.41k (3.30k) | -0.37k | 99% | 0.98 | -0.11k | -4.17k / +3.77k | LEAD |
| 62 | book timeif own T=11:30 X=2 LR | 13% | +0.10k | +0.09k | +0.10k (0.82k) | +2.53k | +1.28k (3.07k) | +1.04k | 103% | 1.00 | +0.05k | -1.63k / +2.91k | CANDIDATE-RECENT |
| 67 | stack timeif K6 T=12:00 X=2 LR | 39% | -0.70k | -0.29k | -0.55k (1.41k) | +3.01k | +2.36k (2.36k) | +1.98k | 105% | 1.01 | -0.28k | -2.50k / +4.87k | DEAD |
| 72 | stack timeif K6 T=12:00 X=regardless LR | 91% | -0.60k | -0.42k | -0.53k (1.89k) | +3.15k | +2.43k (3.62k) | +2.00k | 106% | 1.02 | -0.26k | -5.50k / +7.93k | DEAD |
| 82 | stack timeif K6 T=12:00 X=0 LR dow=(4,) | 9% | +0.11k | -0.38k | -0.07k (0.78k) | +2.17k | +1.38k (1.77k) | +1.20k | 103% | 1.00 | -0.15k | -0.29k / +1.66k | DEAD |
| 145 | stack timeif K6 T=13:00 X=regardless FL | 80% | +0.14k | +2.07k | +0.85k (3.49k) | +0.33k | -2.05k (5.56k) | -0.78k | 95% | 1.05 | +1.80k | -9.89k / +7.84k | LEAD |
| 160 | stack timeif K6 T=14:00 X=0 LR | 37% | -0.11k | -0.27k | -0.17k (0.44k) | -0.05k | +0.12k (0.60k) | +0.18k | 100% | 1.00 | -0.10k | -0.53k / +0.65k | DEAD |
| 187 | book timeif own T=14:00 X=0 LR | 44% | +0.15k | +0.05k | +0.11k (0.55k) | +0.02k | +0.06k (0.73k) | +0.09k | 100% | 1.00 | +0.15k | -0.57k / +0.64k | CANDIDATE-RECENT |
| 202 | stack timeif K6 T=12:00 X=regardless LR dow=(2,) | 18% | +0.09k | +0.67k | +0.30k (0.75k) | +1.22k | +0.89k (1.86k) | +0.57k | 102% | 1.00 | +0.26k | -1.21k / +2.10k | CANDIDATE-RECENT |

Same cells on the stack as it is (second base):

| id | cell | days fired (sel.) | dPRE | dX' | dPRE+X' (MDE) | dL3M | dL6M (MDE) | dHOLD | L6M mean kept | lambda=SD_base/SD_rule | equal-risk d (PRE+X') | L6M forgone / avoided $/wk | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 21 | stack timeif K6 T=11:00 X=2 LR dow=(4,) | 8% | +0.17k | -0.47k | -0.07k (1.22k) | -0.23k | -0.06k (2.05k) | -0.05k | 100% | 1.00 | -0.07k | -1.67k / +1.60k |  |
| 62 | book timeif own T=11:30 X=2 LR | 19% | -1.18k | +0.46k | -0.57k (0.80k) | -0.39k | -0.59k (1.81k) | -0.58k | 97% | 1.01 | -0.48k | -1.90k / +1.30k |  |
| 67 | stack timeif K6 T=12:00 X=2 LR | 37% | -0.51k | +0.06k | -0.30k (0.64k) | +0.83k | +0.53k (1.55k) | +0.55k | 102% | 1.00 | -0.32k | -0.99k / +1.52k |  |
| 72 | stack timeif K6 T=12:00 X=regardless LR | 85% | -0.90k | -0.22k | -0.65k (1.05k) | +0.99k | +0.06k (1.77k) | +0.08k | 100% | 0.99 | -0.70k | -2.45k / +2.51k |  |
| 82 | stack timeif K6 T=12:00 X=0 LR dow=(4,) | 9% | -0.15k | -0.22k | -0.18k (0.29k) | +0.27k | +0.33k (0.47k) | +0.29k | 102% | 1.00 | -0.16k | -0.21k / +0.54k |  |
| 145 | stack timeif K6 T=13:00 X=regardless FL | 66% | -0.81k | -0.64k | -0.75k (3.29k) | -0.56k | -2.23k (5.43k) | -1.56k | 90% | 1.03 | -0.45k | -7.48k / +5.25k |  |
| 160 | stack timeif K6 T=14:00 X=0 LR | 29% | +0.00k | -0.19k | -0.07k (0.24k) | +0.04k | -0.00k (0.44k) | +0.08k | 100% | 1.00 | -0.08k | -0.26k / +0.26k |  |
| 187 | book timeif own T=14:00 X=0 LR | 41% | -0.16k | +0.29k | +0.00k (0.33k) | +0.00k | -0.14k (0.50k) | -0.12k | 99% | 1.00 | -0.03k | -0.43k / +0.29k |  |
| 202 | stack timeif K6 T=12:00 X=regardless LR dow=(2,) | 18% | -0.17k | +0.28k | +0.00k (0.52k) | +0.02k | -0.03k (0.93k) | -0.10k | 100% | 1.00 | +0.00k | -1.16k / +1.14k |  |

Detail for the canon cells and the best looked-at cell of the group:

**stack timeif K6 T=12:00 X=2 LR** (group G2_timeif, cell 67) - tier **DEAD**
- PRE+X' -0.55k/wk [95% CI weeks -1.56k .. +0.36k; 4-week blocks -1.57k .. +0.42k]; L6M +2.36k [+0.83k .. +4.02k; 4-wk +1.17k .. +3.58k]; HOLD +1.98k [+0.54k .. +3.52k]. Stack mean L6M 43.49k -> 45.86k, SD 42.85k -> 43.07k, maxDD 21.12k -> 21.12k, Sharpe 7.32 -> 7.68; worst-20-weeks (PRE+X') -981.18k -> -980.39k.
- controls: random-day placebo (real times) rank 0.12 (PRE+X') / 0.96 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.68 / 0.97 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.779; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.19; days affected 39% (sel.) / 50% (L6M).
- latency (trigger-to-order delay): 0 s -0.55k/+2.36k, 1 s -0.55k/+2.36k, 3 s -0.55k/+2.36k (PRE+X' / L6M, $/wk). Thresholds x0.5 -0.56k/+2.42k, x0.75 -0.52k/+2.51k, x1.25 -0.53k/+2.27k, x1.5 -0.68k/+1.91k (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) -0.55k / +2.36k / +1.98k; stress add-slip 0.45 -0.54k / +2.25k / +1.88k; live-cal join stop 2.45 -0.51k / +2.58k / +2.17k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -1.19k, 2024Q3 -3.15k, 2024Q4 +1.70k, 2025Q1 +0.76k, 2025Q2 -3.08k, 2025Q3 +1.09k, 2025Q4 +3.26k, 2026Q1 +1.04k; positive in 5 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon +0.03k|+0.73k, Tue -0.14k|-0.12k, Wed +0.18k|+0.58k, Thu -0.52k|-0.07k, Fri -0.11k|+1.32k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +0.21k/+0.00k/-0.79k; chop/mid/trend: +0.14k/-0.03k/-0.69k.
- per book $/wk (L6M; per planned lot in brackets): K6 +0.39k (+0.19k), P6 +2.05k (+0.29k), U6 +0.00k (+0.00k), H6 +0.00k (+0.00k), M6 +0.00k (+0.00k), A6 +0.00k (+0.00k).
- on the stack as it is (second base): PRE+X' -0.30k, L6M +0.53k (MDE 1.55k), HOLD +0.55k.

**stack timeif K6 T=12:00 X=regardless LR** (group G2_timeif, cell 72) - tier **DEAD**
- PRE+X' -0.53k/wk [95% CI weeks -1.83k .. +0.65k; 4-week blocks -1.89k .. +0.75k]; L6M +2.43k [-0.03k .. +4.97k; 4-wk +0.20k .. +4.71k]; HOLD +2.00k [-0.39k .. +4.30k]. Stack mean L6M 43.49k -> 45.93k, SD 42.85k -> 44.52k, maxDD 21.12k -> 24.79k, Sharpe 7.32 -> 7.44; worst-20-weeks (PRE+X') -981.18k -> -980.77k.
- controls: random-day placebo (real times) rank 0.43 (PRE+X') / 0.70 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.86 / 0.98 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.779; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.17; days affected 91% (sel.) / 90% (L6M).
- latency (trigger-to-order delay): 0 s -0.53k/+2.43k, 1 s -0.53k/+2.43k, 3 s -0.53k/+2.43k (PRE+X' / L6M, $/wk). Thresholds x0.5 n/a, x0.75 n/a, x1.25 n/a, x1.5 n/a (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) -0.53k / +2.43k / +2.00k; stress add-slip 0.45 -0.52k / +2.46k / +2.02k; live-cal join stop 2.45 -0.40k / +2.68k / +2.22k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -3.66k, 2024Q3 -0.45k, 2024Q4 +0.81k, 2025Q1 +2.10k, 2025Q2 -2.26k, 2025Q3 +0.73k, 2025Q4 +4.95k, 2026Q1 -2.12k; positive in 4 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon -0.20k|+0.68k, Tue -0.29k|-0.46k, Wed +0.32k|+0.88k, Thu -0.60k|+0.57k, Fri +0.23k|+0.83k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +0.59k/-0.05k/-1.11k; chop/mid/trend: +0.60k/-0.04k/-1.13k.
- per book $/wk (L6M; per planned lot in brackets): K6 +0.01k (+0.00k), P6 +2.50k (+0.36k), U6 +0.00k (+0.00k), H6 +0.00k (+0.00k), M6 +0.00k (+0.00k), A6 +0.00k (+0.00k).
- on the stack as it is (second base): PRE+X' -0.65k, L6M +0.06k (MDE 1.77k), HOLD +0.08k.

**stack timeif K6 T=12:00 X=0 LR dow=(4,)** (group G2_timeif, cell 82) - tier **DEAD**
- PRE+X' -0.07k/wk [95% CI weeks -0.65k .. +0.41k; 4-week blocks -0.78k .. +0.53k]; L6M +1.38k [+0.32k .. +2.75k; 4-wk +0.28k .. +2.97k]; HOLD +1.20k [+0.29k .. +2.35k]. Stack mean L6M 43.49k -> 44.87k, SD 42.85k -> 43.62k, maxDD 21.12k -> 21.12k, Sharpe 7.32 -> 7.42; worst-20-weeks (PRE+X') -981.18k -> -986.66k.
- controls: random-day placebo (real times) rank 0.43 (PRE+X') / 0.99 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.59 / 0.98 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.779; Romano-Wolf survivor False; correlation of the weekly delta with the stack 0.04; days affected 9% (sel.) / 10% (L6M).
- latency (trigger-to-order delay): 0 s -0.07k/+1.38k, 1 s -0.07k/+1.38k, 3 s -0.07k/+1.38k (PRE+X' / L6M, $/wk). Thresholds x0.5 n/a, x0.75 n/a, x1.25 n/a, x1.5 n/a (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) -0.07k / +1.38k / +1.20k; stress add-slip 0.45 -0.07k / +1.38k / +1.21k; live-cal join stop 2.45 -0.06k / +1.33k / +1.17k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -0.23k, 2024Q3 -0.10k, 2024Q4 +1.18k, 2025Q1 +0.94k, 2025Q2 -1.16k, 2025Q3 +0.74k, 2025Q4 +2.13k, 2026Q1 +0.39k; positive in 5 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon +0.00k|+0.00k, Tue +0.00k|+0.00k, Wed +0.00k|+0.00k, Thu +0.00k|+0.00k, Fri -0.07k|+1.42k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +0.11k/-0.20k/+0.03k; chop/mid/trend: +0.06k/+0.00k/-0.14k.
- per book $/wk (L6M; per planned lot in brackets): K6 +0.34k (+0.17k), P6 +1.07k (+0.15k), U6 +0.00k (+0.00k), H6 +0.00k (+0.00k), M6 +0.00k (+0.00k), A6 +0.00k (+0.00k).
- on the stack as it is (second base): PRE+X' -0.18k, L6M +0.33k (MDE 0.47k), HOLD +0.29k.

**stack timeif K6 T=14:00 X=0 LR** (group G2_timeif, cell 160) - tier **DEAD**
- PRE+X' -0.17k/wk [95% CI weeks -0.48k .. +0.12k; 4-week blocks -0.49k .. +0.12k]; L6M +0.12k [-0.33k .. +0.53k; 4-wk -0.23k .. +0.46k]; HOLD +0.18k [-0.26k .. +0.60k]. Stack mean L6M 43.49k -> 43.61k, SD 42.85k -> 42.61k, maxDD 21.12k -> 22.34k, Sharpe 7.32 -> 7.38; worst-20-weeks (PRE+X') -981.18k -> -981.58k.
- controls: random-day placebo (real times) rank 0.07 (PRE+X') / 0.73 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.74 / 0.79 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.779; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.12; days affected 37% (sel.) / 44% (L6M).
- latency (trigger-to-order delay): 0 s -0.17k/+0.12k, 1 s -0.17k/+0.12k, 3 s -0.17k/+0.12k (PRE+X' / L6M, $/wk). Thresholds x0.5 n/a, x0.75 n/a, x1.25 n/a, x1.5 n/a (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) -0.17k / +0.12k / +0.18k; stress add-slip 0.45 -0.17k / +0.12k / +0.18k; live-cal join stop 2.45 -0.14k / +0.08k / +0.15k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -0.71k, 2024Q3 -0.24k, 2024Q4 +0.15k, 2025Q1 +0.37k, 2025Q2 -0.43k, 2025Q3 +0.50k, 2025Q4 +0.12k, 2026Q1 -0.44k; positive in 4 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon -0.07k|+0.07k, Tue +0.08k|-0.00k, Wed -0.00k|-0.03k, Thu -0.13k|-0.09k, Fri -0.05k|+0.18k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +0.01k/+0.01k/-0.19k; chop/mid/trend: -0.02k/+0.02k/-0.17k.
- per book $/wk (L6M; per planned lot in brackets): K6 +0.12k (+0.06k), P6 +0.00k (+0.00k), U6 +0.00k (+0.00k), H6 +0.00k (+0.00k), M6 +0.00k (+0.00k), A6 +0.00k (+0.00k).
- on the stack as it is (second base): PRE+X' -0.07k, L6M -0.00k (MDE 0.44k), HOLD +0.08k.

**book timeif own T=14:00 X=0 LR** (group G2_timeif, cell 187) - tier **CANDIDATE-RECENT**
- PRE+X' +0.11k/wk [95% CI weeks -0.26k .. +0.49k; 4-week blocks -0.23k .. +0.48k]; L6M +0.06k [-0.43k .. +0.58k; 4-wk -0.35k .. +0.58k]; HOLD +0.09k [-0.39k .. +0.55k]. Stack mean L6M 43.49k -> 43.56k, SD 42.85k -> 42.55k, maxDD 21.12k -> 22.34k, Sharpe 7.32 -> 7.38; worst-20-weeks (PRE+X') -981.18k -> -981.19k.
- controls: random-day placebo (real times) rank n/a (PRE+X') / n/a (L6M); random-time placebo (uniform 09:30-14:00) rank n/a / n/a (200 draws each; n/a = per-book cell, not run); RC p of the group 0.779; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.07; days affected 44% (sel.) / 49% (L6M).
- latency (trigger-to-order delay): 0 s +0.11k/+0.06k, 1 s +0.11k/+0.06k, 3 s +0.11k/+0.06k (PRE+X' / L6M, $/wk). Thresholds x0.5 n/a, x0.75 n/a, x1.25 n/a, x1.5 n/a (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) +0.11k / +0.06k / +0.09k; stress add-slip 0.45 +0.11k / +0.07k / +0.09k; live-cal join stop 2.45 +0.13k / +0.08k / +0.10k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -1.00k, 2024Q3 +0.89k, 2024Q4 -0.04k, 2025Q1 +0.32k, 2025Q2 +0.28k, 2025Q3 +0.41k, 2025Q4 -0.11k, 2026Q1 -0.19k; positive in 4 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon -0.07k|-0.13k, Tue +0.12k|+0.04k, Wed +0.15k|+0.06k, Thu -0.13k|-0.09k, Fri +0.04k|+0.18k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +0.10k/+0.10k/-0.09k; chop/mid/trend: +0.08k/+0.09k/-0.05k.
- per book $/wk (L6M; per planned lot in brackets): K6 +0.07k (+0.03k), P6 +0.00k (+0.00k), U6 +0.00k (+0.00k), H6 +0.00k (+0.00k), M6 +0.00k (+0.00k), A6 +0.00k (+0.00k).
- on the stack as it is (second base): PRE+X' +0.00k, L6M -0.14k (MDE 0.50k), HOLD -0.12k.

**stack timeif K6 T=13:00 X=regardless FL** (group G2_timeif, cell 145) - tier **LEAD**
- PRE+X' +0.85k/wk [95% CI weeks -1.57k .. +3.46k; 4-week blocks -1.29k .. +2.87k]; L6M -2.05k [-6.03k .. +1.54k; 4-wk -4.93k .. +1.00k]; HOLD -0.78k [-5.05k .. +3.34k]. Stack mean L6M 43.49k -> 41.45k, SD 42.85k -> 42.13k, maxDD 21.12k -> 20.50k, Sharpe 7.32 -> 7.09; worst-20-weeks (PRE+X') -981.18k -> -916.81k.
- controls: random-day placebo (real times) rank 0.61 (PRE+X') / 0.34 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.95 / 0.92 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.779; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.30; days affected 80% (sel.) / 77% (L6M).
- latency (trigger-to-order delay): 0 s +0.85k/-2.05k, 1 s +0.83k/-2.11k, 3 s +0.81k/-2.20k (PRE+X' / L6M, $/wk). Thresholds x0.5 n/a, x0.75 n/a, x1.25 n/a, x1.5 n/a (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) +0.85k / -2.05k / -0.78k; stress add-slip 0.45 +0.88k / -2.01k / -0.74k; live-cal join stop 2.45 +1.05k / -1.85k / -0.60k.
- drift by quarter ($/wk delta, last 8): 2024Q2 +0.87k, 2024Q3 -1.67k, 2024Q4 +2.34k, 2025Q1 -1.79k, 2025Q2 +2.85k, 2025Q3 -0.53k, 2025Q4 -1.79k, 2026Q1 -0.19k; positive in 3 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon +0.12k|+0.28k, Tue -0.40k|-1.31k, Wed +1.63k|-0.93k, Thu -0.71k|+1.05k, Fri +0.24k|-1.20k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +1.63k/+1.36k/-2.08k; chop/mid/trend: +2.03k/+1.71k/-2.84k.
- per book $/wk (L6M; per planned lot in brackets): K6 +0.26k (+0.13k), P6 -1.86k (-0.27k), U6 +0.00k (+0.00k), H6 -0.65k (-0.16k), M6 +0.14k (+0.07k), A6 +0.00k (+0.00k).
- on the stack as it is (second base): PRE+X' -0.75k, L6M -2.23k (MDE 5.43k), HOLD -1.56k.

## 3.3 G3 day profit trail

Cells: 72. Top 5 by PRE+X' delta (selection windows only; the recent windows were NOT computed for cells outside the shortlist):

| cell | days fired | dPRE | dX' | dPRE+X' | MDE | mean kept | lambda | forgone/avoided $/wk |
|---|---|---|---|---|---|---|---|---|
| stack trail Rs A=1 B=0.3 meas=R FL | 15% | +1.66k | +0.41k | +1.20k | 2.92k | 106% | 0.99 | -8.57k / +9.76k |
| stack trail Rs A=1 B=0.2 meas=R FL | 17% | +1.30k | +0.84k | +1.13k | 3.12k | 106% | 1.00 | -9.96k / +11.09k |
| book trail own A=2 B=0.5 meas=R FL | 13% | +0.34k | -0.02k | +0.21k | 0.42k | 101% | 1.00 | -0.63k / +0.83k |
| book trail own A=2.3 B=0.5 meas=R FL | 7% | +0.22k | -0.00k | +0.14k | 0.35k | 101% | 1.00 | -0.60k / +0.74k |
| book trail own A=3 B=1 meas=R FL | 2% | +0.16k | +0.03k | +0.11k | 0.17k | 101% | 1.00 | -0.25k / +0.36k |

Bottom 3:

| cell | days fired | dPRE | dX' | dPRE+X' | MDE |
|---|---|---|---|---|---|
| stack trail K6 A=2 B=0.5 meas=RO FL | 82% | -16.42k | +1.45k | -9.81k | 12.52k |
| stack trail K6 A=2 B=1.5 meas=RO FL | 80% | -15.44k | -0.14k | -9.78k | 12.60k |
| stack trail K6 A=2 B=1 meas=RO FL | 81% | -16.04k | +1.01k | -9.73k | 12.51k |

Shortlists (PRE+X' selection per sub-group) + prereg canon cells, ONE recent look - D6 composite:

- G3_trail_book: [21, 19, 3] (LEAD-set)
- G3_trail_stack: [32, 31] (LEAD-set)
- canon: [50]

| id | cell | days fired (sel.) | dPRE | dX' | dPRE+X' (MDE) | dL3M | dL6M (MDE) | dHOLD | L6M mean kept | lambda=SD_base/SD_rule | equal-risk d (PRE+X') | L6M forgone / avoided $/wk | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 3 | book trail own A=2 B=1 meas=R FL | 8% | +0.13k | +0.03k | +0.09k (0.32k) | -0.53k | -1.01k (1.50k) | -0.89k | 98% | 1.00 | +0.10k | -2.03k / +1.02k | LEAD |
| 19 | book trail own A=3 B=0.5 meas=R FL | 3% | +0.15k | +0.03k | +0.10k (0.16k) | -0.27k | -0.42k (0.73k) | -0.37k | 99% | 1.00 | +0.06k | -1.35k / +0.93k | LEAD |
| 21 | book trail own A=3 B=1 meas=R FL | 2% | +0.16k | +0.03k | +0.11k (0.17k) | -0.54k | -0.64k (0.87k) | -0.56k | 99% | 1.00 | +0.07k | -1.22k / +0.57k | LEAD |
| 31 | stack trail Rs A=1 B=0.2 meas=R FL | 17% | +1.30k | +0.84k | +1.13k (3.12k) | -0.82k | -4.04k (9.01k) | -4.02k | 91% | 1.00 | +1.17k | -26.53k / +22.49k | LEAD |
| 32 | stack trail Rs A=1 B=0.3 meas=R FL | 15% | +1.66k | +0.41k | +1.20k (2.92k) | -0.90k | -4.81k (9.06k) | -4.69k | 89% | 0.99 | +1.01k | -24.86k / +20.05k | LEAD |
| 50 | stack trail K6 A=2.5 B=1 meas=RO FL | 77% | -15.23k | +0.99k | -9.23k (12.24k) | -23.55k | -29.84k (19.91k) | -27.34k | 31% | 2.20 | +2.07k | -149.27k / +119.43k | DEAD |

Same cells on the stack as it is (second base):

| id | cell | days fired (sel.) | dPRE | dX' | dPRE+X' (MDE) | dL3M | dL6M (MDE) | dHOLD | L6M mean kept | lambda=SD_base/SD_rule | equal-risk d (PRE+X') | L6M forgone / avoided $/wk | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 3 | book trail own A=2 B=1 meas=R FL | 16% | +0.01k | +0.03k | +0.02k (0.87k) | -1.56k | -1.30k (4.71k) | -1.03k | 94% | 1.02 | +0.21k | -5.42k / +4.12k |  |
| 19 | book trail own A=3 B=0.5 meas=R FL | 7% | -0.34k | +0.04k | -0.20k (0.73k) | +0.40k | -0.49k (3.30k) | -0.42k | 98% | 1.02 | -0.03k | -3.54k / +3.06k |  |
| 21 | book trail own A=3 B=1 meas=R FL | 7% | -0.38k | +0.04k | -0.22k (0.73k) | +0.40k | -0.40k (3.15k) | -0.35k | 98% | 1.02 | -0.03k | -3.46k / +3.06k |  |
| 31 | stack trail Rs A=1 B=0.2 meas=R FL | 16% | +0.76k | +0.17k | +0.54k (2.02k) | +0.96k | -0.53k (7.87k) | -1.18k | 98% | 1.01 | +0.63k | -16.68k / +16.15k |  |
| 32 | stack trail Rs A=1 B=0.3 meas=R FL | 15% | +0.13k | +0.14k | +0.13k (1.98k) | -0.07k | -0.86k (7.37k) | -1.47k | 96% | 1.02 | +0.35k | -15.02k / +14.16k |  |
| 50 | stack trail K6 A=2.5 B=1 meas=RO FL | 76% | -12.75k | +5.22k | -6.11k (10.85k) | -18.14k | -21.52k (18.66k) | -23.92k | 1% | 1.78 | -2.69k | -127.30k / +105.78k |  |

Detail for the canon cells and the best looked-at cell of the group:

**stack trail K6 A=2.5 B=1 meas=RO FL** (group G3_trail, cell 50) - tier **DEAD**
- PRE+X' -9.23k/wk [95% CI weeks -17.51k .. -0.47k; 4-week blocks -19.26k .. -0.22k]; L6M -29.84k [-43.74k .. -16.04k; 4-wk -38.42k .. -20.66k]; HOLD -27.34k [-42.47k .. -12.03k]. Stack mean L6M 43.49k -> 13.65k, SD 42.85k -> 20.83k, maxDD 21.12k -> 55.41k, Sharpe 7.32 -> 4.73; worst-20-weeks (PRE+X') -981.18k -> -584.43k.
- controls: random-day placebo (real times) rank 0.53 (PRE+X') / 0.05 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.00 / 0.00 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.785; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.89; days affected 77% (sel.) / 85% (L6M).
- latency (trigger-to-order delay): 0 s -9.23k/-29.84k, 1 s -9.05k/-29.80k, 3 s -9.14k/-29.82k (PRE+X' / L6M, $/wk). Thresholds x0.5 -10.90k/-36.95k, x0.75 -9.90k/-30.06k, x1.25 -5.95k/-28.73k, x1.5 -4.09k/-26.61k (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) -9.23k / -29.84k / -27.34k; stress add-slip 0.45 -9.08k / -29.36k / -26.76k; live-cal join stop 2.45 -7.84k / -27.64k / -25.31k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -4.25k, 2024Q3 -23.75k, 2024Q4 -8.90k, 2025Q1 -28.42k, 2025Q2 -24.39k, 2025Q3 -24.37k, 2025Q4 -31.82k, 2026Q1 -16.67k; positive in 0 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon -2.07k|-15.06k, Tue -2.72k|-6.60k, Wed -1.36k|-2.90k, Thu -1.87k|+1.59k, Fri -1.36k|-7.76k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +10.56k/+2.62k/-22.75k; chop/mid/trend: +7.85k/+0.46k/-17.88k.
- per book $/wk (L6M; per planned lot in brackets): K6 -3.21k (-1.61k), P6 -18.54k (-2.65k), U6 -0.96k (-0.24k), H6 -5.62k (-1.40k), M6 -0.63k (-0.31k), A6 -1.78k (-1.78k).
- on the stack as it is (second base): PRE+X' -6.11k, L6M -21.52k (MDE 18.66k), HOLD -23.92k.

**book trail own A=3 B=1 meas=R FL** (group G3_trail, cell 21) - tier **LEAD**
- PRE+X' +0.11k/wk [95% CI weeks +0.01k .. +0.24k; 4-week blocks +0.01k .. +0.27k]; L6M -0.64k [-1.30k .. -0.13k; 4-wk -1.17k .. -0.15k]; HOLD -0.56k [-1.14k .. -0.12k]. Stack mean L6M 43.49k -> 42.85k, SD 42.85k -> 42.88k, maxDD 21.12k -> 21.12k, Sharpe 7.32 -> 7.21; worst-20-weeks (PRE+X') -981.18k -> -981.18k.
- controls: random-day placebo (real times) rank n/a (PRE+X') / n/a (L6M); random-time placebo (uniform 09:30-14:00) rank n/a / n/a (200 draws each; n/a = per-book cell, not run); RC p of the group 0.785; Romano-Wolf survivor False; correlation of the weekly delta with the stack 0.16; days affected 2% (sel.) / 7% (L6M).
- latency (trigger-to-order delay): 0 s +0.11k/-0.64k, 1 s +0.11k/-0.64k, 3 s +0.11k/-0.64k (PRE+X' / L6M, $/wk). Thresholds x0.5 +0.74k/-1.10k, x0.75 +0.12k/-0.97k, x1.25 -0.03k/+0.00k, x1.5 +0.00k/+0.00k (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) +0.11k / -0.64k / -0.56k; stress add-slip 0.45 +0.11k / -0.64k / -0.56k; live-cal join stop 2.45 +0.11k / -0.44k / -0.39k.
- drift by quarter ($/wk delta, last 8): 2024Q2 +0.00k, 2024Q3 +0.00k, 2024Q4 +0.02k, 2025Q1 +0.64k, 2025Q2 +0.32k, 2025Q3 -0.34k, 2025Q4 -0.50k, 2026Q1 -1.50k; positive in 3 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon +0.00k|-0.14k, Tue -0.07k|-0.52k, Wed +0.03k|+0.00k, Thu +0.08k|+0.00k, Fri +0.07k|+0.00k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +0.00k/+0.00k/+0.11k; chop/mid/trend: +0.02k/+0.12k/-0.03k.
- per book $/wk (L6M; per planned lot in brackets): K6 -0.66k (-0.33k), P6 +0.00k (+0.00k), U6 +0.00k (+0.00k), H6 +0.00k (+0.00k), M6 +0.00k (+0.00k), A6 +0.00k (+0.00k).
- on the stack as it is (second base): PRE+X' -0.22k, L6M -0.40k (MDE 3.15k), HOLD -0.35k.

**stack trail Rs A=1 B=0.3 meas=R FL** (group G3_trail, cell 32) - tier **LEAD**
- PRE+X' +1.20k/wk [95% CI weeks -0.76k .. +3.34k; 4-week blocks -0.80k .. +3.58k]; L6M -4.81k [-11.37k .. +1.16k; 4-wk -11.83k .. +3.15k]; HOLD -4.69k [-10.38k .. +0.71k]. Stack mean L6M 43.49k -> 38.68k, SD 42.85k -> 42.48k, maxDD 21.12k -> 39.52k, Sharpe 7.32 -> 6.57; worst-20-weeks (PRE+X') -981.18k -> -953.32k.
- controls: random-day placebo (real times) rank 0.94 (PRE+X') / 0.21 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.96 / 0.01 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.785; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.07; days affected 15% (sel.) / 31% (L6M).
- latency (trigger-to-order delay): 0 s +1.20k/-4.81k, 1 s +1.18k/-4.92k, 3 s +1.19k/-4.90k (PRE+X' / L6M, $/wk). Thresholds x0.5 -3.33k/-7.42k, x0.75 -0.52k/-6.00k, x1.25 +0.20k/-1.63k, x1.5 -0.55k/+0.74k (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) +1.20k / -4.81k / -4.69k; stress add-slip 0.45 +1.22k / -4.76k / -4.65k; live-cal join stop 2.45 +1.37k / -4.40k / -4.33k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -0.95k, 2024Q3 +0.07k, 2024Q4 -2.94k, 2025Q1 +1.64k, 2025Q2 +10.85k, 2025Q3 -4.25k, 2025Q4 -1.26k, 2026Q1 -15.30k; positive in 3 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon +0.50k|-2.02k, Tue +0.32k|-1.00k, Wed +0.23k|+0.22k, Thu -0.13k|+0.76k, Fri +0.30k|-2.92k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): -0.01k/+0.49k/+0.73k; chop/mid/trend: +0.76k/+1.13k/-0.67k.
- per book $/wk (L6M; per planned lot in brackets): K6 +0.01k (+0.00k), P6 -2.33k (-0.33k), U6 -1.04k (-0.26k), H6 -0.40k (-0.10k), M6 -1.15k (-0.58k), A6 -0.04k (-0.04k).
- on the stack as it is (second base): PRE+X' +0.13k, L6M -0.86k (MDE 7.37k), HOLD -1.47k.

## 3.4 G4 quit after N winners / N trades / first loser after +X

Cells: 52. Top 5 by PRE+X' delta (selection windows only; the recent windows were NOT computed for cells outside the shortlist):

| cell | days fired | dPRE | dX' | dPRE+X' | MDE | mean kept | lambda | forgone/avoided $/wk |
|---|---|---|---|---|---|---|---|---|
| book flx own X=2 LR | 27% | +1.07k | -0.17k | +0.62k | 1.20k | 103% | 1.01 | -1.82k / +2.44k |
| book flx own X=2 FL | 27% | +1.07k | -0.17k | +0.62k | 1.20k | 103% | 1.01 | -1.82k / +2.44k |
| book flx own X=3 LR | 8% | +0.35k | -0.02k | +0.21k | 0.68k | 101% | 1.01 | -0.80k / +1.02k |
| book flx own X=3 FL | 8% | +0.35k | -0.02k | +0.21k | 0.68k | 101% | 1.01 | -0.80k / +1.02k |
| book ntr own N=6 LR | 32% | +0.30k | +0.03k | +0.20k | 2.68k | 101% | 1.04 | -7.00k / +7.20k |

Bottom 3:

| cell | days fired | dPRE | dX' | dPRE+X' | MDE |
|---|---|---|---|---|---|
| stack ntr N=6 LR | 91% | -15.46k | -6.01k | -11.97k | 9.78k |
| stack ntr N=6 FL | 91% | -14.66k | -3.79k | -10.64k | 11.50k |
| stack nwin N=3 LR | 85% | -14.62k | -3.10k | -10.36k | 10.21k |

Shortlists (PRE+X' selection per sub-group) + prereg canon cells, ONE recent look - D6 composite:

- G4_count_book: [14, 48] (LEAD-set)
- G4_count_stack: [47, 45, 51] (none with PRE>=0&X>=0 (top by PRE+X shown, weak/DEAD))
- canon: [1, 5, 17]

| id | cell | days fired (sel.) | dPRE | dX' | dPRE+X' (MDE) | dL3M | dL6M (MDE) | dHOLD | L6M mean kept | lambda=SD_base/SD_rule | equal-risk d (PRE+X') | L6M forgone / avoided $/wk | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | stack nwin N=3 LR | 85% | -14.62k | -3.10k | -10.36k (10.21k) | -29.54k | -25.33k (18.71k) | -23.20k | 42% | 1.36 | -7.34k | -113.07k / +87.74k | DEAD |
| 5 | stack ntr N=8 LR | 81% | -12.22k | -1.26k | -8.17k (9.19k) | -17.37k | -15.57k (17.54k) | -13.82k | 64% | 1.23 | -5.77k | -98.25k / +82.69k | DEAD |
| 14 | book ntr own N=6 LR | 32% | +0.30k | +0.03k | +0.20k (2.68k) | -10.91k | -6.29k (6.81k) | -5.39k | 86% | 1.04 | +1.03k | -20.95k / +14.66k | LEAD |
| 17 | stack flx K6 X=2 LR | 78% | -10.29k | -2.43k | -7.38k (8.70k) | -19.94k | -12.82k (15.46k) | -10.93k | 71% | 1.24 | -4.70k | -91.40k / +78.58k | DEAD |
| 45 | stack flx K6 X=3 FL | 70% | -3.14k | +1.01k | -1.61k (8.67k) | -13.48k | -9.10k (13.82k) | -7.09k | 79% | 1.20 | +1.76k | -84.33k / +75.23k | DEAD |
| 47 | stack flx K6 X=4 FL | 64% | -4.01k | +2.49k | -1.61k (8.14k) | -12.87k | -9.87k (11.60k) | -7.93k | 77% | 1.18 | +1.53k | -76.40k / +66.52k | DEAD |
| 48 | book flx own X=4 FL | 2% | +0.31k | +0.00k | +0.19k (0.57k) | +0.35k | -0.01k (0.79k) | -0.01k | 100% | 1.01 | +0.32k | -0.32k / +0.31k | LEAD |
| 51 | stack flx Rs X=1 FL | 31% | -3.36k | +1.05k | -1.73k (6.18k) | -0.51k | -3.12k (11.83k) | -3.60k | 93% | 1.09 | -0.12k | -39.67k / +36.55k | DEAD |

Same cells on the stack as it is (second base):

| id | cell | days fired (sel.) | dPRE | dX' | dPRE+X' (MDE) | dL3M | dL6M (MDE) | dHOLD | L6M mean kept | lambda=SD_base/SD_rule | equal-risk d (PRE+X') | L6M forgone / avoided $/wk | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | stack nwin N=3 LR | 90% | -8.01k | +2.32k | -4.19k (8.55k) | -19.89k | -20.08k (19.03k) | -21.40k | 8% | 1.32 | -2.15k | -96.57k / +76.49k |  |
| 5 | stack ntr N=8 LR | 94% | -8.71k | -0.41k | -5.64k (8.08k) | -11.77k | -12.07k (14.63k) | -11.88k | 44% | 1.21 | -4.64k | -89.91k / +77.84k |  |
| 14 | book ntr own N=6 LR | 30% | -0.61k | -0.38k | -0.53k (1.95k) | -1.65k | -0.33k (6.24k) | -0.01k | 98% | 1.03 | -0.23k | -10.80k / +10.47k |  |
| 17 | stack flx K6 X=2 LR | 78% | -5.64k | +0.25k | -3.46k (8.17k) | -0.43k | -0.72k (11.87k) | -1.22k | 97% | 1.23 | -1.85k | -77.22k / +76.50k |  |
| 45 | stack flx K6 X=3 FL | 70% | -4.21k | +0.74k | -2.38k (7.91k) | -2.26k | -3.50k (12.30k) | -6.19k | 84% | 1.26 | -0.30k | -77.79k / +74.30k |  |
| 47 | stack flx K6 X=4 FL | 62% | -3.18k | +3.32k | -0.78k (6.75k) | +2.47k | +2.10k (13.57k) | -1.42k | 110% | 1.25 | +1.65k | -63.94k / +66.04k |  |
| 48 | book flx own X=4 FL | 7% | -0.40k | +0.04k | -0.24k (0.72k) | +0.40k | -0.40k (3.32k) | -0.35k | 98% | 1.02 | -0.07k | -3.37k / +2.97k |  |
| 51 | stack flx Rs X=1 FL | 30% | -2.95k | +2.51k | -0.93k (4.19k) | -1.65k | -2.58k (10.50k) | -4.31k | 88% | 1.11 | +0.09k | -28.25k / +25.67k |  |

Detail for the canon cells and the best looked-at cell of the group:

**stack nwin N=3 LR** (group G4_count, cell 1) - tier **DEAD**
- PRE+X' -10.36k/wk [95% CI weeks -17.27k .. -3.21k; 4-week blocks -18.91k .. -2.40k]; L6M -25.33k [-38.66k .. -12.65k; 4-wk -37.43k .. -13.87k]; HOLD -23.20k [-35.63k .. -11.39k]. Stack mean L6M 43.49k -> 18.16k, SD 42.85k -> 30.49k, maxDD 21.12k -> 57.61k, Sharpe 7.32 -> 4.30; worst-20-weeks (PRE+X') -981.18k -> -903.80k.
- controls: random-day placebo (real times) rank 0.03 (PRE+X') / 0.01 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.00 / 0.00 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.852; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.69; days affected 85% (sel.) / 93% (L6M).
- latency (trigger-to-order delay): 0 s -10.36k/-25.33k, 1 s -10.48k/-25.33k, 3 s -10.46k/-25.33k (PRE+X' / L6M, $/wk). Thresholds x0.5 -9.84k/-32.58k, x0.75 -9.84k/-32.58k, x1.25 -9.35k/-13.61k, x1.5 -9.35k/-13.61k (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) -10.36k / -25.33k / -23.20k; stress add-slip 0.45 -10.21k / -24.92k / -22.84k; live-cal join stop 2.45 -9.32k / -24.09k / -22.08k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -17.27k, 2024Q3 -30.00k, 2024Q4 -5.01k, 2025Q1 -23.93k, 2025Q2 -6.93k, 2025Q3 -13.32k, 2025Q4 -36.46k, 2026Q1 -24.22k; positive in 0 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon -2.05k|-8.35k, Tue -1.90k|-9.75k, Wed -1.59k|-2.00k, Thu -3.34k|+1.86k, Fri -1.64k|-7.84k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +5.16k/+5.07k/-20.27k; chop/mid/trend: +6.10k/+0.30k/-16.45k.
- per book $/wk (L6M; per planned lot in brackets): K6 -3.16k (-1.58k), P6 -15.57k (-2.22k), U6 -0.43k (-0.11k), H6 -5.79k (-1.45k), M6 -0.03k (-0.01k), A6 -1.09k (-1.09k).
- on the stack as it is (second base): PRE+X' -4.19k, L6M -20.08k (MDE 19.03k), HOLD -21.40k.

**stack ntr N=8 LR** (group G4_count, cell 5) - tier **DEAD**
- PRE+X' -8.17k/wk [95% CI weeks -14.48k .. -1.60k; 4-week blocks -14.99k .. -1.60k]; L6M -15.57k [-27.59k .. -3.36k; 4-wk -26.63k .. -3.57k]; HOLD -13.82k [-25.23k .. -2.02k]. Stack mean L6M 43.49k -> 27.93k, SD 42.85k -> 33.38k, maxDD 21.12k -> 27.10k, Sharpe 7.32 -> 6.03; worst-20-weeks (PRE+X') -981.18k -> -895.69k.
- controls: random-day placebo (real times) rank 0.12 (PRE+X') / 0.22 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.00 / 0.00 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.852; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.60; days affected 81% (sel.) / 93% (L6M).
- latency (trigger-to-order delay): 0 s -8.17k/-15.57k, 1 s -8.17k/-15.57k, 3 s -8.17k/-15.57k (PRE+X' / L6M, $/wk). Thresholds x0.5 -14.18k/-34.62k, x0.75 -11.97k/-23.74k, x1.25 -5.15k/-11.38k, x1.5 -3.75k/-10.67k (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) -8.17k / -15.57k / -13.82k; stress add-slip 0.45 -8.04k / -15.18k / -13.47k; live-cal join stop 2.45 -7.31k / -14.45k / -12.72k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -15.14k, 2024Q3 -27.77k, 2024Q4 -4.06k, 2025Q1 -14.32k, 2025Q2 -7.28k, 2025Q3 -4.22k, 2025Q4 -25.30k, 2026Q1 -15.27k; positive in 0 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon -0.67k|-5.58k, Tue -2.30k|-7.73k, Wed -1.31k|-1.29k, Thu -2.09k|+4.66k, Fri -1.92k|-6.08k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +2.74k/+4.09k/-14.95k; chop/mid/trend: +4.63k/-0.23k/-12.52k.
- per book $/wk (L6M; per planned lot in brackets): K6 -2.05k (-1.02k), P6 -8.97k (-1.28k), U6 +0.29k (+0.07k), H6 -4.06k (-1.01k), M6 -0.68k (-0.34k), A6 -0.56k (-0.56k).
- on the stack as it is (second base): PRE+X' -5.64k, L6M -12.07k (MDE 14.63k), HOLD -11.88k.

**stack flx K6 X=2 LR** (group G4_count, cell 17) - tier **DEAD**
- PRE+X' -7.38k/wk [95% CI weeks -13.12k .. -1.34k; 4-week blocks -14.20k .. -0.58k]; L6M -12.82k [-23.91k .. -2.89k; 4-wk -23.20k .. -3.01k]; HOLD -10.93k [-22.17k .. +0.10k]. Stack mean L6M 43.49k -> 30.68k, SD 42.85k -> 38.76k, maxDD 21.12k -> 41.21k, Sharpe 7.32 -> 5.71; worst-20-weeks (PRE+X') -981.18k -> -903.15k.
- controls: random-day placebo (real times) rank 0.30 (PRE+X') / 0.45 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.00 / 0.00 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.852; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.60; days affected 78% (sel.) / 85% (L6M).
- latency (trigger-to-order delay): 0 s -7.38k/-12.82k, 1 s -7.39k/-12.99k, 3 s -7.40k/-12.99k (PRE+X' / L6M, $/wk). Thresholds x0.5 -10.10k/-20.33k, x0.75 -7.06k/-12.40k, x1.25 -5.44k/-12.01k, x1.5 -3.99k/-11.83k (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) -7.38k / -12.82k / -10.93k; stress add-slip 0.45 -7.25k / -12.44k / -10.59k; live-cal join stop 2.45 -6.49k / -11.76k / -9.93k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -7.48k, 2024Q3 -18.28k, 2024Q4 -5.91k, 2025Q1 -7.22k, 2025Q2 -16.55k, 2025Q3 +2.75k, 2025Q4 -23.88k, 2026Q1 -13.43k; positive in 1 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon +0.09k|-6.09k, Tue -3.99k|+0.48k, Wed -1.39k|-2.81k, Thu -0.52k|+0.62k, Fri -1.69k|-5.40k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +2.58k/+3.33k/-13.36k; chop/mid/trend: +4.25k/+1.30k/-13.00k.
- per book $/wk (L6M; per planned lot in brackets): K6 -1.20k (-0.60k), P6 -8.87k (-1.27k), U6 -0.08k (-0.02k), H6 -1.55k (-0.39k), M6 -1.05k (-0.52k), A6 -0.45k (-0.45k).
- on the stack as it is (second base): PRE+X' -3.46k, L6M -0.72k (MDE 11.87k), HOLD -1.22k.

**book ntr own N=6 LR** (group G4_count, cell 14) - tier **LEAD**
- PRE+X' +0.20k/wk [95% CI weeks -1.58k .. +2.15k; 4-week blocks -1.76k .. +2.32k]; L6M -6.29k [-11.27k .. -1.91k; 4-wk -11.42k .. -2.50k]; HOLD -5.39k [-9.92k .. -1.46k]. Stack mean L6M 43.49k -> 37.20k, SD 42.85k -> 41.17k, maxDD 21.12k -> 25.11k, Sharpe 7.32 -> 6.52; worst-20-weeks (PRE+X') -981.18k -> -970.08k.
- controls: random-day placebo (real times) rank n/a (PRE+X') / n/a (L6M); random-time placebo (uniform 09:30-14:00) rank n/a / n/a (200 draws each; n/a = per-book cell, not run); RC p of the group 0.852; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.30; days affected 32% (sel.) / 51% (L6M).
- latency (trigger-to-order delay): 0 s +0.20k/-6.29k, 1 s +0.20k/-6.29k, 3 s +0.20k/-6.29k (PRE+X' / L6M, $/wk). Thresholds x0.5 -4.49k/-11.52k, x0.75 -2.65k/-9.60k, x1.25 +0.31k/-2.29k, x1.5 +0.06k/-1.69k (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) +0.20k / -6.29k / -5.39k; stress add-slip 0.45 +0.19k / -6.29k / -5.39k; live-cal join stop 2.45 +0.31k / -6.48k / -5.55k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -2.50k, 2024Q3 -2.39k, 2024Q4 +3.98k, 2025Q1 +4.53k, 2025Q2 -1.63k, 2025Q3 -0.30k, 2025Q4 -10.00k, 2026Q1 -8.82k; positive in 2 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon -0.36k|-2.07k, Tue -0.12k|-1.07k, Wed +0.30k|-1.02k, Thu +0.26k|+0.88k, Fri +0.11k|-3.20k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +0.01k/+0.34k/-0.14k; chop/mid/trend: +0.07k/+0.99k/-0.85k.
- per book $/wk (L6M; per planned lot in brackets): K6 -1.09k (-0.54k), P6 -4.41k (-0.63k), U6 +0.00k (+0.00k), H6 -0.07k (-0.02k), M6 -0.91k (-0.45k), A6 +0.00k (+0.00k).
- on the stack as it is (second base): PRE+X' -0.53k, L6M -0.33k (MDE 6.24k), HOLD -0.01k.

**stack flx K6 X=4 FL** (group G4_count, cell 47) - tier **DEAD**
- PRE+X' -1.61k/wk [95% CI weeks -7.30k .. +4.37k; 4-week blocks -7.98k .. +4.41k]; L6M -9.87k [-17.79k .. -1.79k; 4-wk -16.98k .. -1.99k]; HOLD -7.93k [-16.80k .. +0.99k]. Stack mean L6M 43.49k -> 33.62k, SD 42.85k -> 38.55k, maxDD 21.12k -> 26.99k, Sharpe 7.32 -> 6.29; worst-20-weeks (PRE+X') -981.18k -> -902.70k.
- controls: random-day placebo (real times) rank 0.91 (PRE+X') / 0.61 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.47 / 0.01 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.852; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.55; days affected 64% (sel.) / 73% (L6M).
- latency (trigger-to-order delay): 0 s -1.61k/-9.87k, 1 s -1.68k/-10.28k, 3 s -1.89k/-10.36k (PRE+X' / L6M, $/wk). Thresholds x0.5 -4.71k/-10.19k, x0.75 -1.61k/-9.10k, x1.25 -2.44k/-8.11k, x1.5 -1.76k/-8.07k (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) -1.61k / -9.87k / -7.93k; stress add-slip 0.45 -1.48k / -9.52k / -7.61k; live-cal join stop 2.45 -0.55k / -8.87k / -6.99k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -10.19k, 2024Q3 -21.19k, 2024Q4 +13.32k, 2025Q1 +0.71k, 2025Q2 -0.17k, 2025Q3 -1.60k, 2025Q4 -13.19k, 2026Q1 -9.23k; positive in 2 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon +2.52k|-4.46k, Tue -3.18k|-1.25k, Wed -0.07k|-2.26k, Thu -0.16k|+1.21k, Fri -0.74k|-3.40k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +3.61k/+2.84k/-8.20k; chop/mid/trend: +3.87k/+3.21k/-8.83k.
- per book $/wk (L6M; per planned lot in brackets): K6 -0.97k (-0.48k), P6 -7.48k (-1.07k), U6 -0.86k (-0.22k), H6 -0.23k (-0.06k), M6 -0.77k (-0.38k), A6 +0.15k (+0.15k).
- on the stack as it is (second base): PRE+X' -0.78k, L6M +2.10k (MDE 13.57k), HOLD -1.42k.

## 3.5 G5 quit on regime (chop) and trend-only

Cells: 36. Top 5 by PRE+X' delta (selection windows only; the recent windows were NOT computed for cells outside the shortlist):

| cell | days fired | dPRE | dX' | dPRE+X' | MDE | mean kept | lambda | forgone/avoided $/wk |
|---|---|---|---|---|---|---|---|---|
| stack timeif K6 T=12:00 X=regardless LR regime=('12:00', 'er_trend') pol=trend_o | 62% | +0.85k | +0.44k | +0.70k | 1.11k | 104% | 1.00 | -2.58k / +3.28k |
| stack timeif K6 T=12:00 X=regardless LR regime=('12:00', 'ci_chop') pol=quit_if_ | 30% | +0.34k | +0.75k | +0.49k | 0.78k | 103% | 1.01 | -1.09k / +1.58k |
| book timeif own T=12:00 X=regardless LR regime=('12:00', 'ci_chop') pol=quit_if_ | 30% | +0.34k | +0.75k | +0.49k | 0.78k | 103% | 1.01 | -1.09k / +1.58k |
| stack timeif K6 T=12:00 X=regardless LR regime=('12:00', 'er_chop') pol=quit_if_ | 29% | +0.36k | +0.64k | +0.46k | 0.73k | 102% | 1.00 | -1.17k / +1.63k |
| book timeif own T=12:00 X=regardless LR regime=('12:00', 'er_chop') pol=quit_if_ | 29% | +0.36k | +0.64k | +0.46k | 0.73k | 102% | 1.00 | -1.17k / +1.63k |

Bottom 3:

| cell | days fired | dPRE | dX' | dPRE+X' | MDE |
|---|---|---|---|---|---|
| stack timeif K6 T=11:00 X=regardless LR regime=('prev', 'prev_high') pol=trend_o | 67% | -3.54k | +1.37k | -1.73k | 3.92k |
| stack timeif K6 T=11:00 X=regardless LR regime=('11:00', 'ci_trend') pol=trend_o | 66% | -1.76k | -1.06k | -1.50k | 3.21k |
| stack timeif K6 T=11:00 X=regardless LR regime=('11:00', 'ci_chop') pol=quit_if_ | 32% | -1.11k | -0.78k | -0.99k | 2.16k |

Shortlists (PRE+X' selection per sub-group) + prereg canon cells, ONE recent look - D6 composite:

- G5_regime_book: [33, 32, 34] (LEAD-set)
- G5_regime_stack: [9, 10, 8] (LEAD-set)
- canon: [8, 9]

| id | cell | days fired (sel.) | dPRE | dX' | dPRE+X' (MDE) | dL3M | dL6M (MDE) | dHOLD | L6M mean kept | lambda=SD_base/SD_rule | equal-risk d (PRE+X') | L6M forgone / avoided $/wk | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 8 | stack timeif K6 T=12:00 X=regardless LR regime=('12:00', 'er_chop') pol=quit_if_ | 29% | +0.36k | +0.64k | +0.46k (0.73k) | +0.56k | +0.56k (1.14k) | +0.51k | 101% | 1.00 | +0.47k | -0.85k / +1.42k | CANDIDATE-RECENT |
| 9 | stack timeif K6 T=12:00 X=regardless LR regime=('12:00', 'er_trend') pol=trend_o | 62% | +0.85k | +0.44k | +0.70k (1.11k) | -0.02k | -0.16k (2.18k) | -0.09k | 100% | 1.00 | +0.70k | -3.35k / +3.18k | LEAD |
| 10 | stack timeif K6 T=12:00 X=regardless LR regime=('12:00', 'ci_chop') pol=quit_if_ | 30% | +0.34k | +0.75k | +0.49k (0.78k) | +0.99k | +0.34k (2.70k) | +0.08k | 101% | 1.01 | +0.62k | -1.52k / +1.87k | CANDIDATE-RECENT |
| 32 | book timeif own T=12:00 X=regardless LR regime=('12:00', 'er_chop') pol=quit_if_ | 29% | +0.36k | +0.64k | +0.46k (0.73k) | +0.56k | +0.56k (1.14k) | +0.51k | 101% | 1.00 | +0.47k | -0.85k / +1.42k | CANDIDATE-RECENT |
| 33 | book timeif own T=12:00 X=regardless LR regime=('12:00', 'ci_chop') pol=quit_if_ | 30% | +0.34k | +0.75k | +0.49k (0.78k) | +0.99k | +0.34k (2.70k) | +0.08k | 101% | 1.01 | +0.62k | -1.52k / +1.87k | CANDIDATE-RECENT |
| 34 | book timeif own T=14:00 X=regardless LR regime=('14:00', 'er_chop') pol=quit_if_ | 24% | +0.12k | +0.15k | +0.13k (0.37k) | -0.04k | +0.08k (0.33k) | +0.01k | 100% | 1.00 | +0.12k | -0.20k / +0.28k | CANDIDATE-RECENT |

Same cells on the stack as it is (second base):

| id | cell | days fired (sel.) | dPRE | dX' | dPRE+X' (MDE) | dL3M | dL6M (MDE) | dHOLD | L6M mean kept | lambda=SD_base/SD_rule | equal-risk d (PRE+X') | L6M forgone / avoided $/wk | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 8 | stack timeif K6 T=12:00 X=regardless LR regime=('12:00', 'er_chop') pol=quit_if_ | 27% | -0.40k | -0.04k | -0.27k (0.52k) | +0.22k | -0.03k (0.71k) | -0.03k | 100% | 1.00 | -0.29k | -0.43k / +0.40k |  |
| 9 | stack timeif K6 T=12:00 X=regardless LR regime=('12:00', 'er_trend') pol=trend_o | 58% | -0.65k | +0.20k | -0.34k (0.76k) | +0.49k | -0.01k (1.06k) | +0.00k | 100% | 0.99 | -0.41k | -1.07k / +1.06k |  |
| 10 | stack timeif K6 T=12:00 X=regardless LR regime=('12:00', 'ci_chop') pol=quit_if_ | 28% | -0.42k | +0.34k | -0.14k (0.55k) | +0.22k | -0.00k (0.92k) | -0.06k | 100% | 1.00 | -0.15k | -0.78k / +0.78k |  |
| 32 | book timeif own T=12:00 X=regardless LR regime=('12:00', 'er_chop') pol=quit_if_ | 27% | -0.40k | -0.04k | -0.27k (0.52k) | +0.22k | -0.03k (0.71k) | -0.03k | 100% | 1.00 | -0.29k | -0.43k / +0.40k |  |
| 33 | book timeif own T=12:00 X=regardless LR regime=('12:00', 'ci_chop') pol=quit_if_ | 28% | -0.42k | +0.34k | -0.14k (0.55k) | +0.22k | -0.00k (0.92k) | -0.06k | 100% | 1.00 | -0.15k | -0.78k / +0.78k |  |
| 34 | book timeif own T=14:00 X=regardless LR regime=('14:00', 'er_chop') pol=quit_if_ | 22% | -0.04k | +0.18k | +0.04k (0.20k) | +0.00k | +0.21k (0.41k) | +0.11k | 101% | 1.00 | +0.04k | +0.00k / +0.21k |  |

Detail for the canon cells and the best looked-at cell of the group:

**stack timeif K6 T=12:00 X=regardless LR regime=('12:00', 'er_chop') pol=quit_if_chop** (group G5_regime, cell 8) - tier **CANDIDATE-RECENT**
- PRE+X' +0.46k/wk [95% CI weeks -0.03k .. +0.99k; 4-week blocks -0.02k .. +0.97k]; L6M +0.56k [-0.20k .. +1.38k; 4-wk -0.21k .. +1.36k]; HOLD +0.51k [-0.18k .. +1.20k]. Stack mean L6M 43.49k -> 44.06k, SD 42.85k -> 43.29k, maxDD 21.12k -> 21.12k, Sharpe 7.32 -> 7.34; worst-20-weeks (PRE+X') -981.18k -> -967.47k.
- controls: random-day placebo (real times) rank 0.98 (PRE+X') / 0.48 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.92 / 0.86 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.710; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.04; days affected 29% (sel.) / 23% (L6M).
- latency (trigger-to-order delay): 0 s +0.46k/+0.56k, 1 s +0.46k/+0.56k, 3 s +0.46k/+0.56k (PRE+X' / L6M, $/wk). Thresholds x0.5 n/a, x0.75 n/a, x1.25 n/a, x1.5 n/a (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) +0.46k / +0.56k / +0.51k; stress add-slip 0.45 +0.46k / +0.57k / +0.51k; live-cal join stop 2.45 +0.49k / +0.58k / +0.52k.
- drift by quarter ($/wk delta, last 8): 2024Q2 +0.18k, 2024Q3 +0.40k, 2024Q4 -0.01k, 2025Q1 +1.08k, 2025Q2 +1.07k, 2025Q3 +0.57k, 2025Q4 +0.25k, 2026Q1 +1.20k; positive in 7 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon +0.02k|+0.20k, Tue +0.01k|-0.24k, Wed -0.07k|+0.13k, Thu +0.09k|+0.58k, Fri +0.40k|-0.10k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +0.22k/+0.07k/+0.18k; chop/mid/trend: +0.36k/+0.17k/-0.07k.
- per book $/wk (L6M; per planned lot in brackets): K6 +0.11k (+0.06k), P6 +0.47k (+0.07k), U6 +0.00k (+0.00k), H6 +0.00k (+0.00k), M6 +0.00k (+0.00k), A6 +0.00k (+0.00k).
- on the stack as it is (second base): PRE+X' -0.27k, L6M -0.03k (MDE 0.71k), HOLD -0.03k.

**stack timeif K6 T=12:00 X=regardless LR regime=('12:00', 'er_trend') pol=trend_only neg=True** (group G5_regime, cell 9) - tier **LEAD**
- PRE+X' +0.70k/wk [95% CI weeks -0.06k .. +1.45k; 4-week blocks -0.07k .. +1.49k]; L6M -0.16k [-1.67k .. +1.35k; 4-wk -1.68k .. +1.40k]; HOLD -0.09k [-1.39k .. +1.22k]. Stack mean L6M 43.49k -> 43.33k, SD 42.85k -> 43.00k, maxDD 21.12k -> 24.79k, Sharpe 7.32 -> 7.27; worst-20-weeks (PRE+X') -981.18k -> -968.42k.
- controls: random-day placebo (real times) rank 1.00 (PRE+X') / 0.03 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.95 / 0.81 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.710; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.05; days affected 62% (sel.) / 50% (L6M).
- latency (trigger-to-order delay): 0 s -1.19k/+2.59k, 1 s -1.19k/+2.59k, 3 s -1.19k/+2.59k (PRE+X' / L6M, $/wk). Thresholds x0.5 n/a, x0.75 n/a, x1.25 n/a, x1.5 n/a (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) -1.19k / +2.59k / +2.09k; stress add-slip 0.45 -1.18k / +2.60k / +2.09k; live-cal join stop 2.45 -1.13k / +2.66k / +2.15k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -0.59k, 2024Q3 +2.13k, 2024Q4 +0.44k, 2025Q1 +2.21k, 2025Q2 +1.15k, 2025Q3 +0.58k, 2025Q4 -0.14k, 2026Q1 -2.50k; positive in 5 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon -0.07k|+0.47k, Tue +0.18k|-0.84k, Wed +0.24k|+0.05k, Thu -0.02k|-0.00k, Fri +0.38k|+0.15k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +0.57k/+0.13k/-0.02k; chop/mid/trend: +0.70k/+0.29k/-0.31k.
- per book $/wk (L6M; per planned lot in brackets): K6 -0.61k (-0.31k), P6 +0.44k (+0.06k), U6 +0.00k (+0.00k), H6 +0.00k (+0.00k), M6 +0.00k (+0.00k), A6 +0.00k (+0.00k).
- on the stack as it is (second base): PRE+X' -0.34k, L6M -0.01k (MDE 1.06k), HOLD +0.00k.

**book timeif own T=12:00 X=regardless LR regime=('12:00', 'ci_chop') pol=quit_if_chop** (group G5_regime, cell 33) - tier **CANDIDATE-RECENT**
- PRE+X' +0.49k/wk [95% CI weeks -0.07k .. +1.04k; 4-week blocks -0.02k .. +1.01k]; L6M +0.34k [-1.03k .. +2.49k; 4-wk -0.70k .. +1.89k]; HOLD +0.08k [-1.23k .. +2.05k]. Stack mean L6M 43.49k -> 43.84k, SD 42.85k -> 45.32k, maxDD 21.12k -> 22.35k, Sharpe 7.32 -> 6.98; worst-20-weeks (PRE+X') -981.18k -> -958.44k.
- controls: random-day placebo (real times) rank n/a (PRE+X') / n/a (L6M); random-time placebo (uniform 09:30-14:00) rank n/a / n/a (200 draws each; n/a = per-book cell, not run); RC p of the group 0.710; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.14; days affected 30% (sel.) / 29% (L6M).
- latency (trigger-to-order delay): 0 s +0.49k/+0.34k, 1 s +0.49k/+0.34k, 3 s +0.49k/+0.34k (PRE+X' / L6M, $/wk). Thresholds x0.5 n/a, x0.75 n/a, x1.25 n/a, x1.5 n/a (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) +0.49k / +0.34k / +0.08k; stress add-slip 0.45 +0.49k / +0.35k / +0.08k; live-cal join stop 2.45 +0.51k / +0.55k / +0.25k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -0.82k, 2024Q3 -0.05k, 2024Q4 +1.17k, 2025Q1 +1.13k, 2025Q2 +0.20k, 2025Q3 -0.51k, 2025Q4 +1.29k, 2026Q1 -1.43k; positive in 4 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon -0.06k|+0.10k, Tue +0.12k|-0.72k, Wed +0.23k|-0.03k, Thu -0.04k|+0.54k, Fri +0.24k|+0.46k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +0.43k/+0.19k/-0.12k; chop/mid/trend: +0.46k/+0.15k/-0.10k.
- per book $/wk (L6M; per planned lot in brackets): K6 -0.74k (-0.37k), P6 +1.09k (+0.16k), U6 +0.00k (+0.00k), H6 +0.00k (+0.00k), M6 +0.00k (+0.00k), A6 +0.00k (+0.00k).
- on the stack as it is (second base): PRE+X' -0.14k, L6M -0.00k (MDE 0.92k), HOLD -0.06k.

## 3.6 G6 resume at the next session boundary

Cells: 148. Top 5 by PRE+X' delta (selection windows only; the recent windows were NOT computed for cells outside the shortlist):

| cell | days fired | dPRE | dX' | dPRE+X' | MDE | mean kept | lambda | forgone/avoided $/wk |
|---|---|---|---|---|---|---|---|---|
| stack timeif K6 T=13:00 X=regardless FL resume=15:00 | 80% | +0.14k | +2.07k | +0.85k | 3.49k | 105% | 1.05 | -10.05k / +10.90k |
| stack timeif K6 T=13:00 X=1 FL resume=15:00 | 37% | -0.38k | +1.26k | +0.23k | 2.25k | 101% | 1.01 | -4.89k / +5.12k |
| stack timeif Rs T=13:00 X=0.25 FL resume=15:00 | 34% | -0.31k | +1.08k | +0.21k | 2.19k | 101% | 1.01 | -4.62k / +4.82k |
| stack timeif Rs T=13:00 X=0.5 FL resume=15:00 | 28% | -0.20k | +0.69k | +0.13k | 2.00k | 101% | 1.01 | -3.58k / +3.71k |
| stack timeif K6 T=13:00 X=2 FL resume=15:00 | 35% | -0.54k | +1.19k | +0.10k | 2.22k | 101% | 1.01 | -4.77k / +4.87k |

Bottom 3:

| cell | days fired | dPRE | dX' | dPRE+X' | MDE |
|---|---|---|---|---|---|
| stack plus K6 X=1 meas=RO FL resume=15:00 | 91% | -18.77k | -2.42k | -12.73k | 12.58k |
| stack plus K6 X=1 meas=RO FL resume=12:00 | 91% | -18.65k | -2.54k | -12.70k | 12.37k |
| stack plus K6 X=1 meas=RO LR resume=15:00 | 91% | -16.67k | -2.53k | -11.44k | 12.15k |

Shortlists (PRE+X' selection per sub-group) + prereg canon cells, ONE recent look - D6 composite:

- G6_resume_stack: [105] (LEAD-set)
- canon: [4]

| id | cell | days fired (sel.) | dPRE | dX' | dPRE+X' (MDE) | dL3M | dL6M (MDE) | dHOLD | L6M mean kept | lambda=SD_base/SD_rule | equal-risk d (PRE+X') | L6M forgone / avoided $/wk | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | stack plus K6 X=2 meas=RO LR resume=12:00 | 82% | -11.47k | -1.04k | -7.61k (11.27k) | -31.58k | -29.24k (19.06k) | -26.31k | 33% | 1.63 | -0.63k | -126.18k / +96.94k | DEAD |
| 105 | stack timeif K6 T=13:00 X=regardless FL resume=15:00 | 80% | +0.14k | +2.07k | +0.85k (3.49k) | +0.33k | -2.05k (5.56k) | -0.78k | 95% | 1.05 | +1.80k | -9.89k / +7.84k | LEAD |

Same cells on the stack as it is (second base):

| id | cell | days fired (sel.) | dPRE | dX' | dPRE+X' (MDE) | dL3M | dL6M (MDE) | dHOLD | L6M mean kept | lambda=SD_base/SD_rule | equal-risk d (PRE+X') | L6M forgone / avoided $/wk | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | stack plus K6 X=2 meas=RO LR resume=12:00 | 81% | -9.01k | +6.06k | -3.43k (10.46k) | -15.33k | -16.36k (16.41k) | -17.44k | 25% | 1.44 | -0.36k | -110.66k / +94.31k |  |
| 105 | stack timeif K6 T=13:00 X=regardless FL resume=15:00 | 66% | -0.81k | -0.64k | -0.75k (3.29k) | -0.56k | -2.23k (5.43k) | -1.56k | 90% | 1.03 | -0.45k | -7.48k / +5.25k |  |

Detail for the canon cells and the best looked-at cell of the group:

**stack plus K6 X=2 meas=RO LR resume=12:00** (group G6_resume, cell 4) - tier **DEAD**
- PRE+X' -7.61k/wk [95% CI weeks -15.13k .. +0.59k; 4-week blocks -16.21k .. +0.67k]; L6M -29.24k [-42.91k .. -16.45k; 4-wk -39.35k .. -20.13k]; HOLD -26.31k [-40.21k .. -12.39k]. Stack mean L6M 43.49k -> 14.25k, SD 42.85k -> 27.28k, maxDD 21.12k -> 33.30k, Sharpe 7.32 -> 3.77; worst-20-weeks (PRE+X') -981.18k -> -695.91k.
- controls: random-day placebo (real times) rank 0.80 (PRE+X') / 0.07 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.00 / 0.00 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.901; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.80; days affected 82% (sel.) / 88% (L6M).
- latency (trigger-to-order delay): 0 s -7.61k/-29.24k, 1 s -7.65k/-29.24k, 3 s -7.65k/-29.24k (PRE+X' / L6M, $/wk). Thresholds x0.5 -11.40k/-34.06k, x0.75 -8.39k/-31.15k, x1.25 -5.22k/-29.02k, x1.5 -4.73k/-28.27k (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) -7.61k / -29.24k / -26.31k; stress add-slip 0.45 -7.43k / -28.82k / -25.93k; live-cal join stop 2.45 -6.41k / -27.98k / -25.10k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -0.11k, 2024Q3 -16.23k, 2024Q4 -8.51k, 2025Q1 -26.38k, 2025Q2 -14.32k, 2025Q3 -16.64k, 2025Q4 -37.41k, 2026Q1 -28.24k; positive in 0 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon -1.36k|-13.06k, Tue -2.02k|-7.29k, Wed -1.58k|-3.01k, Thu -0.98k|-1.76k, Fri -1.79k|-4.98k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +6.04k/+5.56k/-19.28k; chop/mid/trend: +8.06k/-0.32k/-15.44k.
- per book $/wk (L6M; per planned lot in brackets): K6 -3.32k (-1.66k), P6 -19.14k (-2.73k), U6 +0.18k (+0.05k), H6 -6.46k (-1.61k), M6 -0.30k (-0.15k), A6 -1.07k (-1.07k).
- on the stack as it is (second base): PRE+X' -3.43k, L6M -16.36k (MDE 16.41k), HOLD -17.44k.

**stack timeif K6 T=13:00 X=regardless FL resume=15:00** (group G6_resume, cell 105) - tier **LEAD**
- PRE+X' +0.85k/wk [95% CI weeks -1.57k .. +3.46k; 4-week blocks -1.29k .. +2.87k]; L6M -2.05k [-6.03k .. +1.54k; 4-wk -4.93k .. +1.00k]; HOLD -0.78k [-5.05k .. +3.34k]. Stack mean L6M 43.49k -> 41.45k, SD 42.85k -> 42.13k, maxDD 21.12k -> 20.50k, Sharpe 7.32 -> 7.09; worst-20-weeks (PRE+X') -981.18k -> -916.81k.
- controls: random-day placebo (real times) rank 0.62 (PRE+X') / 0.40 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.97 / 0.93 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.901; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.30; days affected 80% (sel.) / 77% (L6M).
- latency (trigger-to-order delay): 0 s +0.85k/-2.05k, 1 s +0.83k/-2.11k, 3 s +0.81k/-2.20k (PRE+X' / L6M, $/wk). Thresholds x0.5 n/a, x0.75 n/a, x1.25 n/a, x1.5 n/a (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) +0.85k / -2.05k / -0.78k; stress add-slip 0.45 +0.88k / -2.01k / -0.74k; live-cal join stop 2.45 +1.05k / -1.85k / -0.60k.
- drift by quarter ($/wk delta, last 8): 2024Q2 +0.87k, 2024Q3 -1.67k, 2024Q4 +2.34k, 2025Q1 -1.79k, 2025Q2 +2.85k, 2025Q3 -0.53k, 2025Q4 -1.79k, 2026Q1 -0.19k; positive in 3 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon +0.12k|+0.28k, Tue -0.40k|-1.31k, Wed +1.63k|-0.93k, Thu -0.71k|+1.05k, Fri +0.24k|-1.20k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +1.63k/+1.36k/-2.08k; chop/mid/trend: +2.03k/+1.71k/-2.84k.
- per book $/wk (L6M; per planned lot in brackets): K6 +0.26k (+0.13k), P6 -1.86k (-0.27k), U6 +0.00k (+0.00k), H6 -0.65k (-0.16k), M6 +0.14k (+0.07k), A6 +0.00k (+0.00k).
- on the stack as it is (second base): PRE+X' -0.75k, L6M -2.23k (MDE 5.43k), HOLD -1.56k.

## 3.7 G7 size down / size up through the engine multiplier

Cells: 62. Top 5 by PRE+X' delta (selection windows only; the recent windows were NOT computed for cells outside the shortlist):

| cell | days fired | dPRE | dX' | dPRE+X' | MDE | mean kept | lambda | forgone/avoided $/wk |
|---|---|---|---|---|---|---|---|---|
| stack loss K6 X=1 LR size=2.0 int=True | 85% | +12.26k | +3.08k | +8.87k | 10.46k | 147% | 0.60 | -78.12k / +86.98k |
| stack loss K6 X=2 LR size=2.0 int=True | 75% | +9.62k | +5.61k | +8.14k | 9.19k | 144% | 0.66 | -63.03k / +71.17k |
| stack loss Rs X=0.25 LR size=2.0 int=True | 69% | +7.75k | +6.74k | +7.38k | 8.78k | 140% | 0.68 | -58.01k / +65.39k |
| stack loss K6 X=3 LR size=2.0 int=True | 66% | +5.37k | +8.40k | +6.49k | 8.96k | 135% | 0.68 | -53.36k / +59.85k |
| stack loss K6 X=1 LR size=1.5 int=True | 85% | +7.65k | +1.10k | +5.23k | 6.17k | 128% | 0.73 | -48.89k / +54.12k |

Bottom 3:

| cell | days fired | dPRE | dX' | dPRE+X' | MDE |
|---|---|---|---|---|---|
| stack plus K6 X=1 meas=RO LR size=0.33 int=False | 91% | -11.06k | -1.65k | -7.58k | 8.13k |
| stack plus K6 X=1 meas=RO LR size=0.33 int=True | 91% | -9.34k | -2.64k | -6.87k | 7.71k |
| stack plus K6 X=1 meas=RO LR size=0.5 int=False | 91% | -8.15k | -1.20k | -5.58k | 6.07k |

Shortlists (PRE+X' selection per sub-group) + prereg canon cells, ONE recent look - D6 composite:

- G7_size_down: [16, 24, 25] (none with PRE>=0&X>=0 (top by PRE+X shown, weak/DEAD))
- G7_size_up: [57, 58, 60] (LEAD-set)
- canon: [2]

| id | cell | days fired (sel.) | dPRE | dX' | dPRE+X' (MDE) | dL3M | dL6M (MDE) | dHOLD | L6M mean kept | lambda=SD_base/SD_rule | equal-risk d (PRE+X') | L6M forgone / avoided $/wk | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2 | stack plus K6 X=2 meas=RO LR size=0.5 int=True | 82% | -4.15k | -1.10k | -3.02k (4.95k) | -13.07k | -11.38k (7.59k) | -10.07k | 74% | 1.38 | +2.89k | -50.59k / +39.22k | DEAD |
| 16 | stack timeif Rs T=11:00 X=0.5 LR size=0.5 int=True | 29% | -0.68k | +1.07k | -0.03k (1.31k) | +0.34k | -0.83k (1.98k) | -0.60k | 98% | 1.01 | +0.17k | -3.36k / +2.53k | DEAD |
| 24 | stack timeif K6 T=14:00 X=2 LR size=0.5 int=True | 30% | -0.02k | -0.12k | -0.05k (0.12k) | -0.05k | +0.02k (0.18k) | +0.05k | 100% | 1.00 | -0.04k | -0.09k / +0.11k | DEAD |
| 25 | stack timeif Rs T=14:00 X=0.5 LR size=0.5 int=True | 24% | -0.04k | -0.09k | -0.06k (0.12k) | -0.09k | -0.04k (0.12k) | -0.01k | 100% | 1.00 | -0.05k | -0.09k / +0.04k | DEAD |
| 57 | stack loss K6 X=1 LR size=2.0 int=True | 85% | +12.26k | +3.08k | +8.87k (10.46k) | +13.50k | +21.63k (23.32k) | +20.20k | 150% | 0.60 | -2.13k | -109.22k / +130.85k | weak (PRE+X>=0, one selection window negative) |
| 58 | stack loss K6 X=2 LR size=2.0 int=True | 75% | +9.62k | +5.61k | +8.14k (9.19k) | +14.22k | +19.71k (20.85k) | +18.17k | 145% | 0.66 | -1.01k | -88.51k / +108.22k | weak (PRE+X>=0, one selection window negative) |
| 60 | stack loss Rs X=0.25 LR size=2.0 int=True | 69% | +7.75k | +6.74k | +7.38k (8.78k) | +14.17k | +17.18k (18.30k) | +14.96k | 140% | 0.68 | -1.06k | -80.51k / +97.69k | weak (PRE+X>=0, one selection window negative) |

Same cells on the stack as it is (second base):

| id | cell | days fired (sel.) | dPRE | dX' | dPRE+X' (MDE) | dL3M | dL6M (MDE) | dHOLD | L6M mean kept | lambda=SD_base/SD_rule | equal-risk d (PRE+X') | L6M forgone / avoided $/wk | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2 | stack plus K6 X=2 meas=RO LR size=0.5 int=True | 81% | -4.50k | +2.64k | -1.86k (4.62k) | -6.26k | -7.34k (7.55k) | -7.88k | 66% | 1.33 | +0.94k | -51.42k / +44.09k |  |
| 16 | stack timeif Rs T=11:00 X=0.5 LR size=0.5 int=True | 30% | -0.13k | +0.46k | +0.09k (1.00k) | +1.17k | +0.64k (2.10k) | +0.42k | 103% | 1.01 | +0.22k | -2.51k / +3.15k |  |
| 24 | stack timeif K6 T=14:00 X=2 LR size=0.5 int=True | 23% | -0.01k | -0.09k | -0.04k (0.12k) | +0.02k | -0.00k (0.22k) | +0.04k | 100% | 1.00 | -0.05k | -0.13k / +0.13k |  |
| 25 | stack timeif Rs T=14:00 X=0.5 LR size=0.5 int=True | 17% | +0.01k | -0.07k | -0.02k (0.11k) | +0.02k | -0.00k (0.22k) | +0.04k | 100% | 1.00 | -0.03k | -0.13k / +0.13k |  |
| 57 | stack loss K6 X=1 LR size=2.0 int=True | 90% | +6.23k | +2.41k | +4.81k (9.87k) | +26.85k | +22.22k (21.15k) | +18.69k | 202% | 0.61 | -1.22k | -107.63k / +129.85k |  |
| 58 | stack loss K6 X=2 LR size=2.0 int=True | 80% | +7.16k | +4.45k | +6.16k (9.12k) | +23.64k | +23.96k (23.08k) | +20.03k | 210% | 0.63 | -0.01k | -92.37k / +116.33k |  |
| 60 | stack loss Rs X=0.25 LR size=2.0 int=True | 75% | +8.75k | +9.00k | +8.84k (8.74k) | +14.39k | +16.81k (19.13k) | +13.01k | 177% | 0.65 | +1.99k | -87.57k / +104.38k |  |

Detail for the canon cells and the best looked-at cell of the group:

**stack plus K6 X=2 meas=RO LR size=0.5 int=True** (group G7_size, cell 2) - tier **DEAD**
- PRE+X' -3.02k/wk [95% CI weeks -6.34k .. +0.51k; 4-week blocks -6.76k .. +0.56k]; L6M -11.38k [-16.81k .. -6.37k; 4-wk -15.47k .. -7.52k]; HOLD -10.07k [-15.68k .. -4.15k]. Stack mean L6M 43.49k -> 32.12k, SD 42.85k -> 32.74k, maxDD 21.12k -> 13.37k, Sharpe 7.32 -> 7.07; worst-20-weeks (PRE+X') -981.18k -> -698.15k.
- controls: random-day placebo (real times) rank 0.71 (PRE+X') / 0.16 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.00 / 0.00 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.024; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.80; days affected 82% (sel.) / 88% (L6M).
- latency (trigger-to-order delay): 0 s -3.02k/-11.38k, 1 s -3.04k/-11.38k, 3 s -3.04k/-11.38k (PRE+X' / L6M, $/wk). Thresholds x0.5 -4.54k/-13.40k, x0.75 -3.29k/-12.30k, x1.25 -1.99k/-11.36k, x1.5 -1.51k/-11.01k (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) -3.02k / -11.38k / -10.07k; stress add-slip 0.45 -2.96k / -11.26k / -9.97k; live-cal join stop 2.45 -2.61k / -10.87k / -9.60k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -0.63k, 2024Q3 -7.13k, 2024Q4 +0.87k, 2025Q1 -9.24k, 2025Q2 -6.93k, 2025Q3 -5.73k, 2025Q4 -14.50k, 2026Q1 -12.01k; positive in 1 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon -0.73k|-5.23k, Tue -0.73k|-3.45k, Wed -0.67k|-0.86k, Thu -0.57k|-0.55k, Fri -0.36k|-1.62k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +2.31k/+2.32k/-7.73k; chop/mid/trend: +3.07k/-0.19k/-5.97k.
- per book $/wk (L6M; per planned lot in brackets): K6 -0.97k (-0.48k), P6 -7.56k (-1.08k), U6 +0.09k (+0.02k), H6 -2.78k (-0.69k), M6 +0.27k (+0.14k), A6 -0.77k (-0.77k).
- on the stack as it is (second base): PRE+X' -1.86k, L6M -7.34k (MDE 7.55k), HOLD -7.88k.

**stack timeif Rs T=11:00 X=0.5 LR size=0.5 int=True** (group G7_size, cell 16) - tier **DEAD**
- PRE+X' -0.03k/wk [95% CI weeks -0.88k .. +0.85k; 4-week blocks -1.00k .. +0.91k]; L6M -0.83k [-2.26k .. +0.52k; 4-wk -1.96k .. +0.28k]; HOLD -0.60k [-2.18k .. +0.93k]. Stack mean L6M 43.49k -> 42.67k, SD 42.85k -> 41.91k, maxDD 21.12k -> 21.12k, Sharpe 7.32 -> 7.34; worst-20-weeks (PRE+X') -981.18k -> -983.06k.
- controls: random-day placebo (real times) rank 0.57 (PRE+X') / 0.36 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.79 / 0.26 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.024; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.16; days affected 29% (sel.) / 42% (L6M).
- latency (trigger-to-order delay): 0 s -0.03k/-0.83k, 1 s -0.03k/-0.83k, 3 s -0.03k/-0.83k (PRE+X' / L6M, $/wk). Thresholds x0.5 -0.30k/-0.48k, x0.75 -0.10k/-0.67k, x1.25 -0.04k/-0.79k, x1.5 -0.11k/-0.47k (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) -0.03k / -0.83k / -0.60k; stress add-slip 0.45 +0.05k / -0.82k / -0.59k; live-cal join stop 2.45 +0.10k / -0.85k / -0.62k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -0.70k, 2024Q3 -4.14k, 2024Q4 +2.20k, 2025Q1 +1.57k, 2025Q2 -1.97k, 2025Q3 -0.36k, 2025Q4 -1.47k, 2026Q1 +0.60k; positive in 3 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon +0.18k|-0.25k, Tue -0.02k|-0.27k, Wed +0.01k|+0.09k, Thu -0.29k|+0.08k, Fri +0.09k|-0.51k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +0.18k/+0.57k/-0.72k; chop/mid/trend: +0.38k/+0.36k/-0.70k.
- per book $/wk (L6M; per planned lot in brackets): K6 +0.00k (+0.00k), P6 -1.01k (-0.14k), U6 +0.00k (+0.00k), H6 +0.00k (+0.00k), M6 +0.16k (+0.08k), A6 +0.00k (+0.00k).
- on the stack as it is (second base): PRE+X' +0.09k, L6M +0.64k (MDE 2.10k), HOLD +0.42k.

**stack loss K6 X=1 LR size=2.0 int=True** (group G7_size, cell 57) - tier **weak (PRE+X>=0, one selection window negative)**
- PRE+X' +8.87k/wk [95% CI weeks +1.40k .. +15.45k; 4-week blocks +0.62k .. +18.13k]; L6M +21.63k [+6.01k .. +37.46k; 4-wk +6.96k .. +36.10k]; HOLD +20.20k [+5.53k .. +35.90k]. Stack mean L6M 43.49k -> 65.13k, SD 42.85k -> 78.97k, maxDD 21.12k -> 47.29k, Sharpe 7.32 -> 5.95; worst-20-weeks (PRE+X') -981.18k -> -1704.19k.
- controls: random-day placebo (real times) rank 0.63 (PRE+X') / 0.50 (L6M); random-time placebo (uniform 09:30-14:00) rank 1.00 / 1.00 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.024; Romano-Wolf survivor False; correlation of the weekly delta with the stack 0.65; days affected 85% (sel.) / 85% (L6M).
- latency (trigger-to-order delay): 0 s +8.87k/+21.63k, 1 s +8.87k/+21.63k, 3 s +8.87k/+21.63k (PRE+X' / L6M, $/wk). Thresholds x0.5 +10.97k/+28.04k, x0.75 +8.25k/+23.76k, x1.25 +8.61k/+19.78k, x1.5 +8.70k/+23.13k (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) +8.87k / +21.63k / +20.20k; stress add-slip 0.45 +8.64k / +21.82k / +20.34k; live-cal join stop 2.45 +7.13k / +20.91k / +19.41k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -1.80k, 2024Q3 +22.91k, 2024Q4 +9.54k, 2025Q1 +13.21k, 2025Q2 +32.13k, 2025Q3 +10.67k, 2025Q4 +28.96k, 2026Q1 +20.40k; positive in 7 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon +2.81k|+16.41k, Tue +3.55k|+1.83k, Wed +1.20k|+0.44k, Thu +1.51k|-0.15k, Fri -0.07k|+3.74k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): -7.00k/-2.27k/+18.54k; chop/mid/trend: -5.95k/+0.54k/+14.68k.
- per book $/wk (L6M; per planned lot in brackets): K6 +3.07k (+1.53k), P6 +11.50k (+1.64k), U6 -1.71k (-0.43k), H6 +7.89k (+1.97k), M6 +0.57k (+0.29k), A6 +0.95k (+0.95k).
- on the stack as it is (second base): PRE+X' +4.81k, L6M +22.22k (MDE 21.15k), HOLD +18.69k.

## 3.8 G8 combinations

Cells: 91. Top 5 by PRE+X' delta (selection windows only; the recent windows were NOT computed for cells outside the shortlist):

| cell | days fired | dPRE | dX' | dPRE+X' | MDE | mean kept | lambda | forgone/avoided $/wk |
|---|---|---|---|---|---|---|---|---|
| stack timeif K6 T=12:00 X=0 LR regime=('12:00', 'er_chop') | 14% | +0.29k | +0.55k | +0.38k | 0.49k | 102% | 1.00 | -0.50k / +0.89k |
| stack timeif K6 T=12:00 X=2 LR regime=('12:00', 'er_chop') | 10% | +0.25k | +0.41k | +0.31k | 0.42k | 102% | 1.00 | -0.40k / +0.71k |
| stack timeif K6 T=12:00 X=0 LR regime=('12:00', 'ci_chop') | 16% | +0.07k | +0.70k | +0.30k | 0.54k | 102% | 1.00 | -0.70k / +1.00k |
| stack timeif K6 T=12:00 X=2 LR regime=('12:00', 'ci_chop') | 13% | +0.04k | +0.71k | +0.29k | 0.49k | 102% | 1.00 | -0.58k / +0.87k |
| stack timeif Rs T=12:00 X=0.5 LR regime=('12:00', 'er_chop') | 6% | +0.23k | +0.29k | +0.25k | 0.35k | 101% | 1.00 | -0.25k / +0.50k |

Bottom 3:

| cell | days fired | dPRE | dX' | dPRE+X' | MDE |
|---|---|---|---|---|---|
| stack combo K6 LR subs=[{'kind': 'nwin', 'N': 3}, {'kind': 'timeif', 'T': '13:00 | 86% | -14.62k | -3.16k | -10.38k | 10.21k |
| stack combo K6 LR subs=[{'kind': 'nwin', 'N': 3}, {'kind': 'timeif', 'T': '12:00 | 85% | -14.62k | -2.79k | -10.25k | 10.22k |
| stack combo K6 LR subs=[{'kind': 'nwin', 'N': 4}, {'kind': 'timeif', 'T': '13:00 | 80% | -13.37k | -2.66k | -9.41k | 9.86k |

Shortlists (PRE+X' selection per sub-group) + prereg canon cells, ONE recent look - D6 composite:

- G8_combo_stack: [1, 10, 2] (LEAD-set)
- canon: [0]

| id | cell | days fired (sel.) | dPRE | dX' | dPRE+X' (MDE) | dL3M | dL6M (MDE) | dHOLD | L6M mean kept | lambda=SD_base/SD_rule | equal-risk d (PRE+X') | L6M forgone / avoided $/wk | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0 | stack timeif K6 T=12:00 X=0 LR | 49% | -0.56k | -0.18k | -0.42k (1.50k) | +3.96k | +2.99k (3.09k) | +2.53k | 107% | 1.02 | -0.09k | -3.12k / +6.11k | DEAD |
| 1 | stack timeif K6 T=12:00 X=0 LR regime=('12:00', 'er_chop') | 14% | +0.29k | +0.55k | +0.38k (0.49k) | +0.31k | +0.64k (1.25k) | +0.53k | 101% | 1.00 | +0.38k | -0.52k / +1.16k | CANDIDATE-RECENT |
| 2 | stack timeif K6 T=12:00 X=0 LR regime=('12:00', 'ci_chop') | 16% | +0.07k | +0.70k | +0.30k (0.54k) | +1.51k | +0.90k (2.63k) | +0.64k | 102% | 1.00 | +0.40k | -0.88k / +1.78k | CANDIDATE-RECENT |
| 10 | stack timeif K6 T=12:00 X=2 LR regime=('12:00', 'er_chop') | 10% | +0.25k | +0.41k | +0.31k (0.42k) | +0.49k | +0.42k (0.86k) | +0.35k | 101% | 1.00 | +0.29k | -0.37k / +0.79k | CANDIDATE-RECENT |

Same cells on the stack as it is (second base):

| id | cell | days fired (sel.) | dPRE | dX' | dPRE+X' (MDE) | dL3M | dL6M (MDE) | dHOLD | L6M mean kept | lambda=SD_base/SD_rule | equal-risk d (PRE+X') | L6M forgone / avoided $/wk | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0 | stack timeif K6 T=12:00 X=0 LR | 45% | -0.48k | +0.15k | -0.25k (0.69k) | +1.00k | +0.44k (1.56k) | +0.47k | 102% | 1.00 | -0.29k | -1.16k / +1.61k |  |
| 1 | stack timeif K6 T=12:00 X=0 LR regime=('12:00', 'er_chop') | 13% | -0.12k | +0.24k | +0.01k (0.38k) | +0.22k | +0.05k (0.68k) | +0.04k | 100% | 1.00 | -0.02k | -0.26k / +0.31k |  |
| 2 | stack timeif K6 T=12:00 X=0 LR regime=('12:00', 'ci_chop') | 14% | -0.34k | +0.17k | -0.15k (0.41k) | +0.22k | +0.22k (0.92k) | +0.20k | 101% | 1.00 | -0.16k | -0.44k / +0.66k |  |
| 10 | stack timeif K6 T=12:00 X=2 LR regime=('12:00', 'er_chop') | 10% | -0.12k | +0.13k | -0.03k (0.35k) | +0.22k | +0.14k (0.63k) | +0.12k | 101% | 1.00 | -0.05k | -0.17k / +0.31k |  |

Detail for the canon cells and the best looked-at cell of the group:

**stack timeif K6 T=12:00 X=0 LR** (group G8_combo, cell 0) - tier **DEAD**
- PRE+X' -0.42k/wk [95% CI weeks -1.52k .. +0.54k; 4-week blocks -1.56k .. +0.67k]; L6M +2.99k [+0.98k .. +5.11k; 4-wk +1.33k .. +4.62k]; HOLD +2.53k [+0.71k .. +4.50k]. Stack mean L6M 43.49k -> 46.49k, SD 42.85k -> 43.95k, maxDD 21.12k -> 23.56k, Sharpe 7.32 -> 7.63; worst-20-weeks (PRE+X') -981.18k -> -980.19k.
- controls: random-day placebo (real times) rank 0.32 (PRE+X') / 0.99 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.71 / 1.00 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.757; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.21; days affected 49% (sel.) / 58% (L6M).
- latency (trigger-to-order delay): 0 s -0.42k/+2.99k, 1 s -0.42k/+2.99k, 3 s -0.42k/+2.99k (PRE+X' / L6M, $/wk). Thresholds x0.5 n/a, x0.75 n/a, x1.25 n/a, x1.5 n/a (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) -0.42k / +2.99k / +2.53k; stress add-slip 0.45 -0.39k / +3.01k / +2.55k; live-cal join stop 2.45 -0.35k / +3.19k / +2.71k.
- drift by quarter ($/wk delta, last 8): 2024Q2 -0.60k, 2024Q3 -3.45k, 2024Q4 +1.51k, 2025Q1 +0.99k, 2025Q2 -2.70k, 2025Q3 +1.62k, 2025Q4 +4.14k, 2026Q1 +1.04k; positive in 5 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon -0.01k|+0.84k, Tue -0.09k|-0.23k, Wed +0.16k|+0.22k, Thu -0.38k|+0.80k, Fri -0.12k|+1.46k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +0.29k/+0.14k/-0.88k; chop/mid/trend: +0.32k/-0.09k/-0.69k.
- per book $/wk (L6M; per planned lot in brackets): K6 +0.48k (+0.24k), P6 +2.60k (+0.37k), U6 +0.00k (+0.00k), H6 +0.00k (+0.00k), M6 +0.00k (+0.00k), A6 +0.00k (+0.00k).
- on the stack as it is (second base): PRE+X' -0.25k, L6M +0.44k (MDE 1.56k), HOLD +0.47k.

**stack timeif K6 T=12:00 X=0 LR regime=('12:00', 'er_chop')** (group G8_combo, cell 1) - tier **CANDIDATE-RECENT**
- PRE+X' +0.38k/wk [95% CI weeks +0.04k .. +0.74k; 4-week blocks +0.04k .. +0.75k]; L6M +0.64k [-0.17k .. +1.61k; 4-wk -0.23k .. +1.66k]; HOLD +0.53k [-0.15k .. +1.34k]. Stack mean L6M 43.49k -> 44.13k, SD 42.85k -> 43.17k, maxDD 21.12k -> 21.12k, Sharpe 7.32 -> 7.37; worst-20-weeks (PRE+X') -981.18k -> -975.56k.
- controls: random-day placebo (real times) rank 0.99 (PRE+X') / 0.74 (L6M); random-time placebo (uniform 09:30-14:00) rank 0.88 / 0.83 (200 draws each; n/a = per-book cell, not run); RC p of the group 0.757; Romano-Wolf survivor False; correlation of the weekly delta with the stack -0.01; days affected 14% (sel.) / 14% (L6M).
- latency (trigger-to-order delay): 0 s +0.38k/+0.64k, 1 s +0.38k/+0.64k, 3 s +0.38k/+0.64k (PRE+X' / L6M, $/wk). Thresholds x0.5 n/a, x0.75 n/a, x1.25 n/a, x1.5 n/a (PRE+X' / L6M).
- fill bases side by side (delta vs each base, PRE+X' / L6M / HOLD): model add-slip 0.25 (headline) +0.38k / +0.64k / +0.53k; stress add-slip 0.45 +0.38k / +0.64k / +0.54k; live-cal join stop 2.45 +0.40k / +0.65k / +0.55k.
- drift by quarter ($/wk delta, last 8): 2024Q2 +0.45k, 2024Q3 -0.07k, 2024Q4 +0.47k, 2025Q1 +0.54k, 2025Q2 +0.44k, 2025Q3 +1.02k, 2025Q4 -0.14k, 2026Q1 +1.20k; positive in 6 of 8.
- day-of-week split ($/wk, PRE+X' | L6M): Mon +0.01k|+0.36k, Tue +0.09k|-0.24k, Wed +0.03k|+0.00k, Thu +0.02k|+0.54k, Fri +0.23k|-0.00k. Regime split by same-day vol tercile (low/mid/high, PRE+X'): +0.13k/+0.12k/+0.14k; chop/mid/trend: +0.18k/+0.23k/-0.02k.
- per book $/wk (L6M; per planned lot in brackets): K6 +0.36k (+0.18k), P6 +0.29k (+0.04k), U6 +0.00k (+0.00k), H6 +0.00k (+0.00k), M6 +0.00k (+0.00k), A6 +0.00k (+0.00k).
- on the stack as it is (second base): PRE+X' +0.01k, L6M +0.05k (MDE 0.68k), HOLD +0.04k.


## 5. G9 learned policy (walk-forward; all 108 cells reported, no selection)

Targets and features as in prereg B; first test week 2023-07-03; 3-month rolling refit every week (roll3m) and anchored expanding (anch); HGB = gradient boosted trees depth 2, ridge = benchmark. Cells show delta vs the D6 composite, $k/wk, as PRE+X' / L6M / HOLD (stack, exact overlay; quit = no entries after T; size = x0.5 integer; three = x0.5 below -theta, quit below -(theta+1) K6-R).

| T | model | window | rank IC PRE+X / L6M / HOLD | quit th=0 | quit th=0.5 | quit th=1 | size th=0 | size th=0.5 | size th=1 | three th=0 | three th=0.5 | three th=1 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 10:30 | hgb | roll3m | IC -0.002 / -0.097 / -0.081 | -2.14/-3.16/-3.03 | -1.55/-2.85/-2.56 | -1.58/-1.68/-1.49 | -0.67/-1.31/-1.25 | -0.48/-1.16/-1.10 | -0.55/-0.75/-0.75 | -1.69/-2.24/-2.00 | -1.33/-2.24/-1.99 | -1.30/-1.55/-1.60 |
| 10:30 | hgb | anch | IC 0.019 / -0.114 / -0.046 | -1.66/-5.71/-4.36 | -1.59/-3.05/-2.95 | -2.11/-1.90/-1.95 | -0.69/-2.11/-1.44 | -0.67/-1.10/-1.12 | -0.83/-0.69/-0.76 | -1.96/-3.32/-2.63 | -1.48/-1.94/-2.06 | -1.31/-1.78/-1.92 |
| 10:30 | ridge | roll3m | IC 0.061 / -0.034 / -0.035 | +0.10/-2.11/-2.54 | -0.24/-1.00/-1.48 | -0.36/-0.81/-1.18 | +0.28/-1.04/-1.19 | +0.12/-0.48/-0.73 | +0.08/-0.23/-0.39 | -0.18/-1.62/-1.98 | -0.66/-1.19/-1.60 | -1.14/-0.44/-0.82 |
| 10:30 | ridge | anch | IC 0.073 / 0.020 / -0.014 | -0.70/-2.76/-3.10 | +0.22/-0.99/-1.42 | -0.66/-0.19/-0.55 | -0.31/-0.94/-1.20 | +0.08/-0.45/-0.65 | -0.30/-0.09/-0.26 | -0.68/-1.05/-1.49 | +0.25/-0.25/-0.39 | -0.17/+0.08/-0.04 |
| 12:00 | hgb | roll3m | IC -0.007 / -0.056 / -0.034 | -0.21/+1.52/+1.18 | -0.11/+1.61/+1.34 | +0.05/+1.51/+1.32 | +0.00/+0.60/+0.46 | -0.02/+0.60/+0.52 | +0.04/+0.53/+0.46 | +0.02/+1.59/+1.33 | +0.16/+0.64/+0.55 | +0.18/+0.84/+0.73 |
| 12:00 | hgb | anch | IC 0.009 / 0.001 / 0.017 | -0.67/+0.75/+0.51 | -0.38/+0.02/-0.09 | +0.09/-0.31/-0.41 | -0.19/+0.38/+0.29 | -0.11/-0.02/-0.06 | +0.10/-0.03/-0.08 | -0.20/+0.10/-0.05 | +0.02/-0.15/-0.17 | +0.18/-0.12/-0.16 |
| 12:00 | ridge | roll3m | IC 0.007 / 0.051 / 0.082 | -0.42/+0.42/+0.13 | -0.52/+0.36/+0.14 | -0.32/+0.50/+0.26 | -0.09/+0.13/+0.05 | -0.16/+0.11/+0.04 | -0.10/+0.19/+0.11 | -0.31/+0.44/+0.19 | -0.14/+0.66/+0.52 | -0.07/+0.75/+0.60 |
| 12:00 | ridge | anch | IC 0.040 / 0.058 / 0.085 | +0.04/+0.32/+0.10 | +0.20/+0.73/+0.48 | +0.03/+0.42/+0.35 | +0.01/+0.08/+0.03 | +0.09/+0.33/+0.22 | +0.03/+0.23/+0.19 | +0.01/+0.28/+0.18 | +0.16/+0.33/+0.22 | +0.14/+0.23/+0.19 |
| 14:00 | hgb | roll3m | IC -0.013 / -0.178 / -0.145 | +0.13/-0.08/-0.11 | -0.01/-0.17/-0.19 | -0.05/-0.05/-0.08 | +0.07/+0.00/+0.00 | +0.01/-0.04/-0.04 | -0.01/+0.00/+0.00 | +0.03/-0.05/-0.08 | -0.00/-0.00/-0.00 | -0.02/+0.00/+0.00 |
| 14:00 | hgb | anch | IC 0.107 / -0.006 / 0.015 | +0.01/-0.25/-0.13 | +0.02/+0.09/+0.08 | +0.04/+0.09/+0.08 | +0.01/-0.02/+0.02 | +0.01/+0.04/+0.04 | +0.01/+0.04/+0.04 | +0.04/+0.02/+0.05 | +0.00/+0.04/+0.04 | +0.01/+0.04/+0.04 |
| 14:00 | ridge | roll3m | IC 0.041 / -0.163 / -0.149 | +0.11/+0.05/+0.01 | +0.00/+0.02/-0.02 | -0.11/+0.00/+0.00 | +0.05/+0.00/+0.00 | +0.02/+0.00/+0.00 | -0.04/+0.00/+0.00 | -0.02/+0.00/+0.00 | +0.03/-0.09/-0.08 | -0.04/+0.00/+0.00 |
| 14:00 | ridge | anch | IC 0.075 / 0.140 / 0.087 | +0.12/-0.24/-0.26 | -0.03/+0.00/+0.00 | +0.06/+0.00/+0.00 | +0.06/-0.07/-0.07 | -0.01/+0.00/+0.00 | +0.01/+0.00/+0.00 | +0.10/-0.07/-0.07 | -0.01/+0.00/+0.00 | +0.01/+0.00/+0.00 |

Of 108 cells, 50 have a positive PRE+X' delta, 50 a positive L6M delta, 26 positive on PRE+X', L6M and HOLD together; the best by PRE+X' is ('10:30', 'ridge', 'roll3m', 'size', 0.0) (PRE+X' +0.28k, L6M -1.04k, HOLD -1.19k; MDE PRE+X' 1.75k). The largest |delta| of any cell is +2.14k/wk against a stack mean of ~40k/wk: the learned policy is a null.

Shuffled-label placebo (training labels permuted across days, same chain, quit theta=0.5 K6-R, rolling 3 months; 100 draws): rank of the real delta among the placebo deltas (fraction of placebo draws below the real one) PRE+X' / L6M / HOLD:

| T | model | real delta PRE+X / L6M / HOLD | placebo mean | rank PRE+X | rank L6M | rank HOLD |
|---|---|---|---|---|---|---|
| 10:30 | hgb | -1.55k / -2.85k / -2.56k | -1.87k / -3.04k / -3.01k | 0.62 | 0.56 | 0.62 |
| 10:30 | ridge | -0.24k / -1.00k / -1.48k | -1.72k / -2.94k / -2.88k | 0.89 | 0.82 | 0.76 |
| 12:00 | hgb | -0.11k / +1.61k / +1.34k | -0.33k / +0.54k / +0.45k | 0.78 | 0.96 | 0.94 |
| 12:00 | ridge | -0.52k / +0.36k / +0.14k | -0.29k / +0.84k / +0.72k | 0.20 | 0.25 | 0.16 |
| 14:00 | hgb | -0.01k / -0.17k / -0.19k | -0.02k / +0.03k / +0.04k | 0.52 | 0.04 | 0.03 |
| 14:00 | ridge | +0.00k / +0.02k / -0.02k | -0.03k / +0.05k / +0.06k | 0.62 | 0.43 | 0.31 |

Extracted rules (depth-2 tree on PRE+X' days predicting the afternoon, in K6-R / $):

T=10:30: unconditional afternoon mean PRE+X' +0.44k, L6M +2.69k.
```
|--- ci14 <= 26.26
|   |--- prevpnl <= -5.66
|   |   |--- value: [8592.74]
|   |--- prevpnl >  -5.66
|   |   |--- value: [1211.97]
|--- ci14 >  26.26
|   |--- open <= 7.50
|   |   |--- value: [3.88]
|   |--- open >  7.50
|   |   |--- value: [-5358.13]
```
Leaves (prediction, PRE+X' n, PRE+X' mean, L6M n, L6M mean): -5.36k, 72, -5.36k, 10, +0.11k; +0.00k, 278, +0.00k, 69, +1.27k; +1.21k, 156, +1.21k, 40, +4.72k; +8.59k, 51, +8.59k, 10, +6.94k

T=12:00: unconditional afternoon mean PRE+X' -0.11k, L6M +0.41k.
```
|--- gb <= 7.94
|   |--- ci14 <= 37.50
|   |   |--- value: [1604.94]
|   |--- ci14 >  37.50
|   |   |--- value: [-1401.03]
|--- gb >  7.94
|   |--- open <= 5.50
|   |   |--- value: [-435.74]
|   |--- open >  5.50
|   |   |--- value: [-4052.68]
```
Leaves (prediction, PRE+X' n, PRE+X' mean, L6M n, L6M mean): -4.05k, 50, -4.05k, 16, +6.91k; -1.40k, 132, -1.40k, 35, -0.79k; -0.44k, 135, -0.44k, 38, -1.03k; +1.60k, 240, +1.60k, 40, +0.23k

T=14:00: unconditional afternoon mean PRE+X' -0.08k, L6M +0.31k.
```
|--- fhr <= 47.38
|   |--- value: [1899.88]
|--- fhr >  47.38
|   |--- fhr <= 72.12
|   |   |--- value: [-1318.34]
|   |--- fhr >  72.12
|   |   |--- value: [11.63]
```
Leaves (prediction, PRE+X' n, PRE+X' mean, L6M n, L6M mean): -1.32k, 96, -1.32k, 13, +1.51k; +0.01k, 419, +0.01k, 112, +0.12k; +1.90k, 42, +1.90k, 4, +1.83k

Best 1- and 2-feature distillation (fit on PRE+X' days, target = minus afternoon, one look at L6M):

T=10:30:

| k | rule (fires where the afternoon is worst) | fit mean of -afternoon | fit n | L6M mean of -afternoon | L6M n |
|---|---|---|---|---|---|
| 1 | open > 5 | +1.59k | 181 | -3.38k | 40 |
| 2 | open > 5 AND fhr < 82.75 | +4.98k | 85 | -1.08k | 12 |

T=12:00:

| k | rule (fires where the afternoon is worst) | fit mean of -afternoon | fit n | L6M mean of -afternoon | L6M n |
|---|---|---|---|---|---|
| 1 | gb > 7.988 | +1.41k | 184 | -1.32k | 54 |
| 2 | ci14 > 38.45 AND prevrng < 171.2 | +4.57k | 36 | -4.16k | 6 |

T=14:00:

| k | rule (fires where the afternoon is worst) | fit mean of -afternoon | fit n | L6M mean of -afternoon | L6M n |
|---|---|---|---|---|---|
| 1 | nwin < 6 | +0.38k | 273 | -1.37k | 31 |
| 2 | wtd < -6.384 AND ci14 > 37.88 | +1.92k | 38 | +0.44k | 6 |

Ridge standardised coefficients (anchored refit at each quarter start), top 3 by |coef| per quarter, T=12:00:

| refit date | top features (coef, $ per 1 SD) |
|---|---|
| 2023-07-01 | fhr +2802, ci14 -2764, tsince +2719 |
| 2023-10-01 | fhr +2183, tsince +2081, ntr +1522 |
| 2024-01-01 | fhr +2007, ci14 -1799, wtd -1124 |
| 2024-04-01 | ntr +1191, wtd -1188, ci14 -1183 |
| 2024-07-01 | fhr +743, gb -691, tsince +628 |
| 2024-10-01 | gb -720, tsince +569, nwin +455 |
| 2025-01-01 | tsince +814, gb -715, peak -436 |
| 2025-04-01 | tsince +882, gb -540, wtd -452 |
| 2025-07-01 | tsince +810, gb -512, nwin +323 |
| 2025-10-01 | tsince +968, gb -624, open +410 |
| 2026-01-01 | tsince +925, open +736, gb -436 |

## 6. Chop-day check of the afternoon give-back (causal tags at T)

| T | tag (tercile cuts PRE+X) | window | tercile (ER20 low = chop; CI14 high = chop) | days | afternoon mean (all) | %neg | days up>=2R | afternoon mean | %neg |
|---|---|---|---|---|---|---|---|---|---|
| 12:00 | 5m ER20 | PRE+X | low | 186 | -0.72k | 52% | 64 | -2.03k | 58% |
| 12:00 | 5m ER20 | PRE+X | mid | 185 | -0.10k | 47% | 85 | +1.09k | 44% |
| 12:00 | 5m ER20 | PRE+X | high | 186 | +0.49k | 44% | 90 | +0.69k | 42% |
| 12:00 | 5m ER20 | L6M | low | 34 | +0.87k | 53% | 17 | -0.32k | 53% |
| 12:00 | 5m ER20 | L6M | mid | 38 | -0.43k | 50% | 23 | -2.17k | 57% |
| 12:00 | 5m ER20 | L6M | high | 57 | +0.70k | 49% | 29 | -1.31k | 55% |
| 12:00 | Choppiness-14 | PRE+X | low | 186 | +0.41k | 48% | 87 | +1.13k | 48% |
| 12:00 | Choppiness-14 | PRE+X | mid | 185 | +0.28k | 41% | 67 | +0.63k | 37% |
| 12:00 | Choppiness-14 | PRE+X | high | 186 | -1.01k | 53% | 85 | -1.36k | 53% |
| 12:00 | Choppiness-14 | L6M | low | 47 | -0.57k | 53% | 25 | -2.32k | 60% |
| 12:00 | Choppiness-14 | L6M | mid | 39 | +1.46k | 54% | 20 | +0.57k | 50% |
| 12:00 | Choppiness-14 | L6M | high | 43 | +0.53k | 44% | 24 | -1.95k | 54% |
| 14:00 | 5m ER20 | PRE+X | low | 186 | -0.28k | 42% | 71 | +0.56k | 39% |
| 14:00 | 5m ER20 | PRE+X | mid | 185 | -0.04k | 39% | 86 | +0.06k | 35% |
| 14:00 | 5m ER20 | PRE+X | high | 186 | +0.10k | 32% | 78 | +0.19k | 33% |
| 14:00 | 5m ER20 | L6M | low | 45 | -0.23k | 47% | 24 | -0.42k | 42% |
| 14:00 | 5m ER20 | L6M | mid | 49 | +0.82k | 27% | 30 | +0.82k | 30% |
| 14:00 | 5m ER20 | L6M | high | 35 | +0.29k | 34% | 19 | +0.63k | 32% |
| 14:00 | Choppiness-14 | PRE+X | low | 186 | +0.13k | 33% | 93 | +0.14k | 34% |
| 14:00 | Choppiness-14 | PRE+X | mid | 185 | -0.06k | 35% | 61 | -0.02k | 41% |
| 14:00 | Choppiness-14 | PRE+X | high | 186 | -0.29k | 46% | 81 | +0.59k | 33% |
| 14:00 | Choppiness-14 | L6M | low | 29 | +0.03k | 34% | 17 | +0.52k | 24% |
| 14:00 | Choppiness-14 | L6M | mid | 48 | +0.77k | 25% | 28 | +1.18k | 25% |
| 14:00 | Choppiness-14 | L6M | high | 52 | +0.04k | 46% | 28 | -0.55k | 50% |
