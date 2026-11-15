PROVISIONAL: every row below is PROVISIONAL until parity_ok.txt exists (parents PB/PC month-by-month parity with JV_B/JV_C not yet proven).
VERDICT (plain, 2026-11-14 23:37 UTC): family B is running; 0 of 239 registered cells have at least one scored window. No window is complete yet. No PASS claim; the parents are reproduced.

# DS3_EXPAND_B - an exit fitted to how each book fails (W-EB, T-EXPAND family B)

Base JN05W2 (all layers on, K7 flat45, state cuts, flat cuts kept), exact engine, measured fills; dollars are engine net_fee (engine fee $1.18/contract; FEES.md standard is $4.84 RT, rule cuts add exits so cost differences are understated, see note). Prereg autopilot/EXPAND_B_PREREG.md. Code code/th_expand_b (eb_hooks.py). Tolerant gate = programme gate (DS3_JOINT_V20): DD cut > -2% and mean change > -3% of reference mean, per window; d_mean_fee484 = mean change re-priced at the FEES.md $4.84 RT per contract; a cell advances to the next window only after passing the previous.

Identity: TL3_EB_ID 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL

## 1. Parent reproduction (same months, same trade list as the JV set)

| cell      | parent   |   month |   n_eb |   n_parent |   net_eb |   net_parent | verdict   |
|:----------|:---------|--------:|-------:|-----------:|---------:|-------------:|:----------|
| TL3_EB_PB | TL3_JV_B |  202608 |    640 |        640 | 114176   |     114176   | IDENTICAL |
| TL3_EB_PC | TL3_JV_C |  202608 |    623 |        623 |  94698.9 |      94698.9 | IDENTICAL |

## 4. Reference: W-PM exact A7/U7 cells (L3M first rows, from the lead 2026-11-14). W-EB does not duplicate them; TL3_EB_A7*_T10D20 is the clock-minute twin of E_A7_N10X20 (row convention) and is reported beside it.

| cell        |   L3M dmean |   L3M dd% | L3M stops/wk   |   L6M dmean |   L6M dd% | L6M stops/wk   |   L6M ww d$ |   L6M best5 |   L6M w2l |   HOLD dmean |   HOLD dd% |   HOLD stops/wk |   L3M dmean@4.84 |   L6M dmean@4.84 |   HOLD dmean@4.84 |   L6M dd% noW44 |
|:------------|------------:|----------:|:---------------|------------:|----------:|:---------------|------------:|------------:|----------:|-------------:|-----------:|----------------:|-----------------:|-----------------:|------------------:|----------------:|
| E_A7_N10X20 |        2363 |       1   | 10.3>9.6       |         nan |     nan   | nan            |         nan |      nan    |       nan |          nan |        nan |             nan |             2353 |              nan |               nan |           nan   |
| E_A7_F50    |        1652 |       2.1 | 10.3>6.5       |        1331 |       2.1 | 11.0>7.3       |        1114 |        1.01 |         0 |          nan |        nan |             nan |             1642 |             1324 |               nan |             0.4 |
| E_A7_F40    |        2126 |      10.3 | 10.3>6.5       |        1869 |      10.3 | 11.0>7.2       |        5527 |        1.03 |         0 |          nan |        nan |             nan |             2109 |             1854 |               nan |             5.5 |
