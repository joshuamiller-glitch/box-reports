# DS3_EXIT_N_FLOW - flow-gated LOSS cuts (E2c) and flow-gated TAKES (E2d), basis N (S4b, 14:14Z 2026-11-02)
POST-HOC, no PASS claim, Shadow only. Prereg l2vast/ds3/prereg/EXITN_E2CD_prereg.md sha256 8faba0d541d1e83f51dd5681bff0bd948672036eb44349db1ce353a2941f038b (+ amendment 17:12Z in DECISIONS.md: the pulled-mult loss grid is S4a's, E2c reduced to delta-turn and large-print gates). Base V13T_LIVE lock none (xcost 0.80, stop 2.45), inject kind cut / take (market at the path price), flow arrays /mnt/l2/l2vast/ds3_flow1s/.
## Plain sentences
* **Flow-gated loss cuts (20 cells: adverse A = 20/25/30/35/40 pts AND delta-turn against or a tier-2 large print against, ADD to the base TH-L2 cut or REPLACE it): 0 eligible.** The large-print-against cut ADDED to the base cut is the least harmful (mean change -0.4k to +0.3k/wk, inside MDE; X' maxDD +16..+39% but HOLD ~0% and PRE -5..-10%, MID -6..-26%): it moves the X' episode only. The delta-turn gate fires on 26k-38k rows and costs -2k to -6k/wk; REPLACING the live cut by any of these gates is worse than the live cut. Best score +0.099 (LP A30 ADD).
* **Flow-gated takes (18 cells: pct 0.3/0.5/0.7 AND delta-turn / large print / own-support pulled / iceberg against): 0 eligible**, best HOLD mean change -0.58k/wk (large-print-against at pct 0.7, 8,243 rows), every other cell -3k to -13k/wk. On basis N an early market exit at 0.80 pt gives up more than the flow signal saves, even when gated by order flow.
## E2c loss cuts, top 10 by S
| cell | rows | S | elig | cut HOLD / PRE / X' / L6M / MID | mean d HOLD / PRE $k/wk (MDE) |
|---|---|---|---|---|---|
| L_LP_30_ADD | 15599 | +0.099 | n | +4% / -8% / +34% / +4% / -19% | +0.0 / -0.6 (0.9) |
| L_LP_40_ADD | 11101 | +0.057 | n | -0% / -5% / +24% / -0% / -6% | -0.4 / +0.3 (1.4) |
| L_LP_35_ADD | 13408 | +0.051 | n | +0% / -7% / +16% / +0% / -6% | -0.4 / +0.6 (0.9) |
| L_LP_25_ADD | 17726 | +0.047 | n | +2% / -10% / +29% / +9% / -26% | +0.3 / -0.7 (1.9) |
| L_LP_20_ADD | 19964 | +0.038 | n | +7% / -8% / +39% / +7% / -25% | -0.2 / -1.2 (4.2) |
| L_DT_25_ADD | 38300 | +0.001 | n | -15% / +28% / +6% / -15% / -50% | -6.5 / -4.5 (6.8) |
| L_DT_40_ADD | 26132 | -0.002 | n | +0% / -7% / -2% / +0% / -3% | +0.2 / -0.8 (0.8) |
| L_DT_30_ADD | 34732 | -0.007 | n | +1% / +4% / -9% / +1% / -12% | -2.0 / -3.1 (3.2) |
| L_DT_35_ADD | 30849 | -0.036 | n | -11% / -5% / -7% / -11% / -21% | -0.4 / -1.3 (1.2) |
| L_DT_20_ADD | 41918 | -0.114 | n | -41% / +20% / -15% / -24% / -181% | -13.3 / -6.2 (12.1) |
## E2d takes, top 8 by S
| cell | rows | S | elig | cut HOLD / PRE / X' / L6M / MID | mean d HOLD / PRE $k/wk (MDE) |
|---|---|---|---|---|---|
| T_DT0_0.7_0 | 35384 | +0.066 | n | +16% / +21% / +28% / +25% / -3% | -6.7 / -4.0 (11.7) |
| T_PS50_0.7_0 | 36988 | +0.003 | n | +25% / +11% / +5% / +25% / -10% | -4.4 / -5.0 (12.4) |
| T_DT0_0.5_0 | 42483 | -0.003 | n | +21% / +1% / +30% / +32% / -82% | -12.9 / -9.7 (12.6) |
| T_LP0_0.5_0 | 14422 | -0.015 | n | +12% / -13% / +12% / +12% / -35% | -3.0 / -1.1 (6.2) |
| T_IC100_0.5_0 | 39192 | -0.017 | n | -43% / +16% / +30% / -43% / -131% | -13.1 / -7.8 (11.1) |
| T_IC300_0.7_0 | 19888 | -0.022 | n | -10% / +0% / -4% / -10% / -11% | -2.9 / -1.0 (4.3) |
| T_LP0_0.7_0 | 8243 | -0.030 | n | +6% / -3% / -3% / +6% / -16% | -0.6 / -0.6 (3.6) |
| T_IC300_0.5_0 | 24038 | -0.065 | n | +0% / -2% / -34% / +10% / -19% | -3.7 / -5.8 (4.9) |
Pulled-mult-gated loss cuts and ungated cuts/book-flip/time-stop/blackouts: S4a (DS3_EXIT_N_LOSS.md). Ledger: 38 cells appended (programs EXITN_E2C / EXITN_E2D). Cubes /mnt/l2/l2vast/ds3_zones3_new/e2/cubes_cd, table e2cd_table.pkl, code zones3/s4b/e2cd.py.

## Correction (REPLACE mode)
The first REPLACE run (th_loss off) was invalid: with th_loss off the engine does not merge injected exits (the 10 REPLACE cells came out identical); those ledger rows (program EXITN_E2C, cell ids without '|v2') are invalid. Corrected REPLACE = the base TH-L2 cut moved to 55 pts (a near no-op, the stop is ~60) with the gated cut injected, ledger ids '...|v2'. Result: 0 of 10 eligible; the large-print-against cut at A 20 (19,964 rows) scores S +0.21 only through HOLD +17% / X' +43% / L6M +20% while PRE -35% and MID -185% (the live cut is needed in PRE/MID), mean -1.4k/wk HOLD; every delta-turn REPLACE cell has HOLD maxDD -23% to -63% (worse) and mean -4k to -14k/wk. Replacing the live pulled/adverse cut with an order-flow-gated cut is therefore worse than keeping it; the ADD results above are unchanged (valid).
