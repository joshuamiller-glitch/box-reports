# REPORT I5J - trade management of the retrace book (IDEAS-5000 family J)
**Verdict: 0 LEAD, 0 FOUND-PENDING, 0 FOUND.** 608 distinct cells scored (4 books x 2 targets (2R, 3R) x 21 management forms x rules; partial-at-1R forms stk2 only; 16 cells identical to E's L0 not double counted). 8 selected, 8 null passes, 3 gate-3 at stage 1 (chance bound <= 0.4); H1/H2 read once for those 3 cells: all fail (uplift H2 -0.18..-0.25, bootstrap lo < 0).
Engine: exec_engine_pp ECONOMICS (exec_engine v1 + same-row price-priority tie-break, see Amendment E-D2 in PREREG_IDEAS5000.md); rules ffw / ooat / nro / stk2 as an explicit factor of every cell; NQ, clean window 2023-08..2025-07 for stage 1 (H1/H2 untouched until stage 3); R-sized USD (9,600 per trade, cap 24 contracts), 1 tick adverse on market entries and stop exits, $4.36 per contract. Registry: outputs/ideas5000/CELLS.csv (latest row per cell_id), TALLY.csv; per-cell tables i5ej_stage1_pp.csv / i5ej_stage3_pp.csv; v1-engine archive i5ej_stage{1,3}_v1engine.csv. Code: code/census/night_ins/ap_i5_ej.py, exec_engine_pp.py.

## Forms scored (all as order programs; management inside exec_engine: be_r, hold, OCO group, two-leg stk2 partial)
| form          |   cells |   median_clean_sharpe |   best_clean_sharpe |   selected |   g3 |
|:--------------|--------:|----------------------:|--------------------:|-----------:|-----:|
| BE0.0_H120    |      32 |                -0.868 |               0.626 |          1 |    1 |
| BE0.0_H15     |      32 |                -2.401 |              -0.773 |          0 |    0 |
| BE0.0_H30     |      32 |                -1.581 |              -0.442 |          0 |    0 |
| BE0.0_H360    |      16 |                -0.849 |               0.684 |          3 |    1 |
| BE0.0_H60     |      32 |                -1.52  |               0.465 |          1 |    0 |
| BE0.5_H120    |      32 |                -2.389 |              -0.567 |          0 |    0 |
| BE0.5_H360    |      32 |                -2.282 |              -0.693 |          0 |    0 |
| BE0.5_H60     |      32 |                -2.498 |              -0.174 |          0 |    0 |
| BE0.75_H120   |      32 |                -1.926 |              -0.27  |          0 |    0 |
| BE0.75_H360   |      32 |                -1.764 |              -0.227 |          0 |    0 |
| BE0.75_H60    |      32 |                -2.151 |              -0.092 |          0 |    0 |
| BE1.0_H120    |      32 |                -1.355 |               0.11  |          0 |    0 |
| BE1.0_H360    |      32 |                -1.306 |               0.129 |          0 |    0 |
| BE1.0_H60     |      32 |                -1.488 |               0.242 |          0 |    0 |
| BE1.25_H120   |      32 |                -1.403 |               0.167 |          0 |    0 |
| BE1.25_H360   |      32 |                -1.33  |               0.149 |          0 |    0 |
| BE1.25_H60    |      32 |                -1.698 |               0.056 |          0 |    0 |
| M1_BE0.0      |      32 |                -0.849 |               0.684 |          3 |    1 |
| M1_BE1.0      |      32 |                -1.374 |               0.129 |          0 |    0 |
| PART0.33_R2.0 |       4 |                -3.007 |              -2.387 |          0 |    0 |
| PART0.33_R3.0 |       4 |                -2.766 |              -2.049 |          0 |    0 |
| PART0.5_R2.0  |       4 |                -3.259 |              -2.814 |          0 |    0 |
| PART0.5_R3.0  |       4 |                -3.092 |              -2.61  |          0 |    0 |

## Not expressible in exec_engine v1, therefore NOT scored (engine extension requested)
Trail to swing, add-on at the second retrace, max 2 or 3 trades per impulse, cool-off after a stop, daily stop in R, break-even after a partial. They need state that survives across orders (per-impulse fill counters, realised-R accounting, a trailing stop callback) which the v1 intent/bracket model does not have.
The corrected engine (price-priority tie-break) was used; with exec_engine v1 the J cells were equally negative (3 of 3 gate-3 cells failed H2 under both engines).
