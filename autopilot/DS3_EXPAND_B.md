VERDICT (plain, 2026-11-15 01:37 UTC): family B is running; 3 of 239 registered cells have at least one scored window. L3M best DD change TL3_EB_U7F_T15D10 11.7% (mean +1244 $/wk). No PASS claim; the parents are reproduced.

# DS3_EXPAND_B - an exit fitted to how each book fails (W-EB, T-EXPAND family B)

Base JN05W2 (all layers on, K7 flat45, state cuts, flat cuts kept), exact engine, measured fills; dollars are engine net_fee (engine fee $1.18/contract; FEES.md standard is $4.84 RT, rule cuts add exits so cost differences are understated, see note). Prereg autopilot/EXPAND_B_PREREG.md. Code code/th_expand_b (eb_hooks.py). Tolerant gate = programme gate (DS3_JOINT_V20): DD cut > -2% and mean change > -3% of reference mean, per window; d_mean_fee484 = mean change re-priced at the FEES.md $4.84 RT per contract; a cell advances to the next window only after passing the previous.

Identity: TL3_EB_ID 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL

## 1. Parent reproduction (same months, same trade list as the JV set)

| cell      | parent   |   month |   n_eb |   n_parent |   net_eb |   net_parent | verdict   |
|:----------|:---------|--------:|-------:|-----------:|---------:|-------------:|:----------|
| TL3_EB_PB | TL3_JV_B |  202605 |    632 |        632 |  72755   |      72755   | IDENTICAL |
| TL3_EB_PB | TL3_JV_B |  202608 |    640 |        640 | 114176   |     114176   | IDENTICAL |
| TL3_EB_PB | TL3_JV_B |  202609 |    637 |        637 | 113894   |     113894   | IDENTICAL |
| TL3_EB_PB | TL3_JV_B |  202610 |    600 |        600 |  36412.6 |      36412.6 | IDENTICAL |
| TL3_EB_PC | TL3_JV_C |  202608 |    623 |        623 |  94698.9 |      94698.9 | IDENTICAL |
| TL3_EB_PC | TL3_JV_C |  202609 |    641 |        641 | 124875   |     124875   | IDENTICAL |
| TL3_EB_PC | TL3_JV_C |  202610 |    604 |        604 |  35360.4 |      35360.4 | IDENTICAL |

## 2. Scored windows (drawdown first), reference JN05W2


### L3M

| cell              | win   |   weeks |    mean |   d_mean |      dd |   dd_ref |   dd_cut |   dd44_cut |   d_mean_fee484 |       ww |   ww_ref |   best5 |   w2l |   nwin |   cuts_wk | gate   |
|:------------------|:------|--------:|--------:|---------:|--------:|---------:|---------:|-----------:|----------------:|---------:|---------:|--------:|------:|-------:|----------:|:-------|
| TL3_EB_U7F_T15D10 | L3M   |      13 | 17258.8 |   1243.6 | 32116.9 |  36370.5 |     11.7 |       -5.2 |          1243.3 | -31571.5 | -36370.5 |     1.1 |     0 |      9 |      52.4 | PASS   |
| TL3_EB_PB         | L3M   |      13 | 17258.8 |   1243.6 | 32116.9 |  36370.5 |     11.7 |       -5.2 |          1243.3 | -31571.5 | -36370.5 |     1.1 |     0 |      9 |      52.4 | PASS   |
| TL3_EB_PC         | L3M   |      13 | 17760.9 |   1745.7 | 35985.2 |  36370.5 |      1.1 |       28.3 |          1713.3 | -35985.2 | -36370.5 |     1.1 |     0 |      9 |      51.4 | PASS   |

## 3. Anatomy (full stops, cost in targets, saved stops) for cells scored on L3M/L6M

| cell              | win   |   weeks | books   |   fs_wk_ref |   fs_usd_wk_ref |   fsB_wk_ref |   fsB_usd_wk_ref |   bookpnl_wk_ref |   fs_wk_cell |   fs_usd_wk_cell |   fsB_wk_cell |   fsB_usd_wk_cell |   bookpnl_wk_cell |   cuts_wk |   cut_ref_target_wk |   cost_targets_usd_wk |   cut_ref_stop_wk |   saved_stops_usd_wk |   cut_ref_statecut_wk |   d_statecut_usd_wk |   d_other_usd_wk |   best5_ref |   best5_cell |
|:------------------|:------|--------:|:--------|------------:|----------------:|-------------:|-----------------:|-----------------:|-------------:|-----------------:|--------------:|------------------:|------------------:|----------:|--------------------:|----------------------:|------------------:|---------------------:|----------------------:|--------------------:|-----------------:|------------:|-------------:|
| TL3_EB_U7F_T15D10 | L3M   |      13 | U7      |       10.46 |        -19607.1 |         3.31 |         -10021.9 |          4823.66 |         9.54 |         -16683.4 |          2.31 |          -7006.6  |           5798.62 |      1.23 |                0.23 |                449.81 |              1    |              1424.77 |                  0    |                0    |                0 |      241079 |       244735 |
| TL3_EB_PB         | L3M   |      13 | U7      |       10.46 |        -19607.1 |         3.31 |         -10021.9 |          4823.66 |         9.54 |         -16683.4 |          2.31 |          -7006.6  |           5798.62 |      1.23 |                0.23 |                449.81 |              1    |              1424.77 |                  0    |                0    |                0 |      241079 |       244735 |
| TL3_EB_PC         | L3M   |      13 | U7      |       10.46 |        -19607.1 |         3.31 |         -10021.9 |          4823.66 |         8.08 |         -12203.5 |          0.69 |          -2310.73 |           6166.67 |      4.54 |                1.23 |               4379.9  |              2.62 |              3253.34 |                  0.69 |              203.98 |                0 |      241079 |       245753 |

## 4. Reference: W-PM exact A7/U7 cells (L3M first rows, from the lead 2026-11-14). W-EB does not duplicate them; TL3_EB_A7*_T10D20 is the clock-minute twin of E_A7_N10X20 (row convention) and is reported beside it.

| cell        |   L3M dmean |   L3M dd% | L3M stops/wk   |   L6M dmean |   L6M dd% | L6M stops/wk   |   L6M ww d$ |   L6M best5 |   L6M w2l |   HOLD dmean |   HOLD dd% | HOLD stops/wk   |   L3M dmean@4.84 |   L6M dmean@4.84 |   HOLD dmean@4.84 |   L6M dd% noW44 |
|:------------|------------:|----------:|:---------------|------------:|----------:|:---------------|------------:|------------:|----------:|-------------:|-----------:|:----------------|-----------------:|-----------------:|------------------:|----------------:|
| E_A7_N10X20 |        2363 |       1   | 10.3>9.6       |        1420 |       1   | 11.0>10.4      |         511 |        1.03 |         0 |          nan |      nan   | nan             |             2353 |             1414 |               nan |             2.1 |
| E_A7_F50    |        1652 |       2.1 | 10.3>6.5       |        1331 |       2.1 | 11.0>7.3       |        1114 |        1.01 |         0 |          494 |        0.6 | 10.7>7.6        |             1642 |             1324 |               493 |             0.4 |
| E_A7_F40    |        2126 |      10.3 | 10.3>6.5       |        1869 |      10.3 | 11.0>7.2       |        5527 |        1.03 |         0 |          nan |      nan   | nan             |             2109 |             1854 |               nan |             5.5 |
