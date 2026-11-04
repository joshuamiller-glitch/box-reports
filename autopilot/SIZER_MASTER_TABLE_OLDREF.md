# SIZER MASTER TABLE, OLD REFERENCE (x1.5 ladder, superseded by SIZER_MASTER_TABLE.md vs Q1-A) (integrator, 2026-11-04 14:36Z)

Post-hoc, Shadow only, no PASS claims. Cuts are fractions of weekly-cumulative maxDD vs the live binary ER ladder (positive = smaller drawdown), all converted from percent where the source used percent. Base column says ts/V13T_LIVE sequential; ledger-only rows (S2, ADD, STRESS) are tagged by their spec text; S3X is PA maxDD in dollars and sits in the ledger only (not a cut). Q1/Q2 exist only as DS3_SIZER_Q1.md/Q2.md prose and are not yet machine-merged. Full table: SIZER_MASTER_TABLE.csv (6454 rows). Missing columns (equal-risk delta, placebo ranks, best-of-N null, worst-day exposure) are filled only where the source file has them; see per-program pages. 'ER sizer off' is never a ranked cell.

## Top 60 by (cut L6M + cut PRE)/2

| program   | cell                                  | base              |   mean_lots |   cut_L6M |   cut_PRE |   cut_HOLD |   cut_MID |   cut_Xp |   drop_L6M |   drop_PRE |   dmean_L6M |   dmean_PRE |   pa9_L6M |   pa9_PRE | label                        |
|:----------|:--------------------------------------|:------------------|------------:|----------:|----------:|-----------:|----------:|---------:|-----------:|-----------:|------------:|------------:|----------:|----------:|:-----------------------------|
| SIZER_S2  | regime_with_5m|d+1|ALONE:LIN          | ts                |     nan     |     0.708 |     0.621 |      0.305 |   nan     |    0.079 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | regime_with_5m|d+1|ALONE:LIN          | ts                |     nan     |     0.708 |     0.621 |      0.305 |   nan     |    0.079 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst1_dir_s|d+1|ALONE:L3               | ts                |     nan     |     0.708 |     0.604 |      0.305 |   nan     |    0.079 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst1_dir_s|d+1|ALONE:D3               | ts                |     nan     |     0.708 |     0.604 |      0.305 |   nan     |    0.079 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | regime_with_5m|d+1|ALONE:D3           | ts                |     nan     |     0.708 |     0.604 |      0.305 |   nan     |    0.079 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | regime_with_5m|d+1|ALONE:L3           | ts                |     nan     |     0.708 |     0.604 |      0.305 |   nan     |    0.079 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | regime_with_5m|d+1|ALONE:D3           | ts                |     nan     |     0.708 |     0.604 |      0.305 |   nan     |    0.079 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | regime_with_5m|d+1|ALONE:L3           | ts                |     nan     |     0.708 |     0.604 |      0.305 |   nan     |    0.079 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst1_dir_s|d+1|ALONE:L3               | ts                |     nan     |     0.708 |     0.604 |      0.305 |   nan     |    0.079 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | regime_with_5m|d+1|ALONE:SIG          | ts                |     nan     |     0.708 |     0.604 |      0.305 |   nan     |    0.079 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst1_dir_s|d+1|ALONE:D3               | ts                |     nan     |     0.708 |     0.604 |      0.305 |   nan     |    0.079 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | regime_with_5m|d+1|ALONE:SIG          | ts                |     nan     |     0.708 |     0.604 |      0.305 |   nan     |    0.079 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | big2_net30_s|d+1|ALONE:D3             | ts                |     nan     |     0.71  |     0.587 |      0.304 |   nan     |    0.072 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | big2_net30_s|d+1|ALONE:D3             | ts                |     nan     |     0.71  |     0.587 |      0.304 |   nan     |    0.072 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | big2_net30_s|d+1|ALONE:LIN            | ts                |     nan     |     0.687 |     0.57  |      0.283 |   nan     |    0.081 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | big2_net30_s|d+1|ALONE:SIG            | ts                |     nan     |     0.687 |     0.57  |      0.283 |   nan     |    0.064 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | big2_net30_s|d+1|ALONE:LIN            | ts                |     nan     |     0.687 |     0.57  |      0.283 |   nan     |    0.081 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | big2_net30_s|d+1|ALONE:SIG            | ts                |     nan     |     0.687 |     0.57  |      0.283 |   nan     |    0.064 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | big2_net30_s|d+1|ALONE:L3             | ts                |     nan     |     0.668 |     0.582 |      0.31  |   nan     |    0.125 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | big2_net30_s|d+1|ALONE:L3             | ts                |     nan     |     0.668 |     0.582 |      0.31  |   nan     |    0.125 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst1_dir_s|d+1|ALONE:SIG              | ts                |     nan     |     0.694 |     0.553 |      0.236 |   nan     |    0.066 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst1_dir_s|d+1|ALONE:LIN              | ts                |     nan     |     0.694 |     0.553 |      0.236 |   nan     |   -0.101 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst1_dir_s|d+1|ALONE:LIN              | ts                |     nan     |     0.694 |     0.553 |      0.236 |   nan     |   -0.101 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst1_dir_s|d+1|ALONE:SIG              | ts                |     nan     |     0.694 |     0.553 |      0.236 |   nan     |    0.066 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst10_dir_s|d+1|ALONE:D3              | ts                |     nan     |     0.652 |     0.579 |      0.314 |   nan     |    0.046 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst10_dir_s|d+1|ALONE:L3              | ts                |     nan     |     0.652 |     0.579 |      0.314 |   nan     |    0.046 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst10_dir_s|d+1|ALONE:L3              | ts                |     nan     |     0.652 |     0.579 |      0.314 |   nan     |    0.046 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst10_dir_s|d+1|ALONE:D3              | ts                |     nan     |     0.652 |     0.579 |      0.314 |   nan     |    0.046 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst10_dir_s|d+1|ALONE:SIG             | ts                |     nan     |     0.641 |     0.575 |      0.321 |   nan     |   -0.053 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst10_dir_s|d+1|ALONE:SIG             | ts                |     nan     |     0.641 |     0.575 |      0.321 |   nan     |   -0.053 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst5_dir_s|d+1|ALONE:D3               | ts                |     nan     |     0.612 |     0.578 |      0.234 |   nan     |    0.091 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst5_dir_s|d+1|ALONE:L3               | ts                |     nan     |     0.612 |     0.578 |      0.234 |   nan     |    0.091 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst5_dir_s|d+1|ALONE:D3               | ts                |     nan     |     0.612 |     0.578 |      0.234 |   nan     |    0.091 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst5_dir_s|d+1|ALONE:L3               | ts                |     nan     |     0.612 |     0.578 |      0.234 |   nan     |    0.091 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | confirm_n5|d+1|ALONE:D3               | ts                |     nan     |     0.652 |     0.529 |      0.229 |   nan     |   -0.027 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | confirm_n5|d+1|ALONE:D3               | ts                |     nan     |     0.652 |     0.529 |      0.229 |   nan     |   -0.027 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst5_dir_s|d+1|ALONE:LIN              | ts                |     nan     |     0.613 |     0.555 |      0.226 |   nan     |   -0.106 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst5_dir_s|d+1|ALONE:SIG              | ts                |     nan     |     0.613 |     0.555 |      0.226 |   nan     |   -0.106 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst5_dir_s|d+1|ALONE:LIN              | ts                |     nan     |     0.613 |     0.555 |      0.226 |   nan     |   -0.106 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst5_dir_s|d+1|ALONE:SIG              | ts                |     nan     |     0.613 |     0.555 |      0.226 |   nan     |   -0.106 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst10_dir_s|d+1|ALONE:LIN             | ts                |     nan     |     0.635 |     0.51  |      0.207 |   nan     |   -0.186 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst10_dir_s|d+1|ALONE:LIN             | ts                |     nan     |     0.635 |     0.51  |      0.207 |   nan     |   -0.186 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S1  | ('g12', 'er_1m_30', 'LIN', 'C')       | V13T_LIVE_seq(ts) |     nan     |     0.638 |     0.498 |      0.254 |    -0.016 |    0.071 |      0.4   |      0.475 |    -15496.4 |    -7100.77 |   nan     |   nan     | COSTS-MEAN(drawdown for P&L) |
| SIZER_S1  | ('g13', 'ers_30m_20', 1, 'LIN', 'C')  | V13T_LIVE_seq(ts) |     nan     |     0.645 |     0.477 |      0.127 |    -0.107 |   -0.468 |      0.596 |      0.454 |    -15312.5 |    -5695.95 |   nan     |   nan     | COSTS-MEAN(drawdown for P&L) |
| SIZER_S1B | E|UNI|M3|uni0.50                      | V13T_LIVE_seq(ts) |       2.028 |     0.628 |     0.492 |      0.265 |    -0.453 |    0.27  |      0.319 |      0.492 |    -16503.3 |    -7503.89 |     0.628 |     0.492 | COSTS-MEAN(drawdown for P&L) |
| SIZER_S1  | ('g12', 'er_10m_10', 'LIN', 'C')      | V13T_LIVE_seq(ts) |     nan     |     0.598 |     0.521 |      0.13  |    -0.04  |   -0.057 |      0.325 |      0.519 |    -11500.1 |    -5839.22 |   nan     |   nan     | COSTS-MEAN(drawdown for P&L) |
| SIZER_S1  | ('g12', 'er_2m_14', 'LIN', 'C')       | V13T_LIVE_seq(ts) |     nan     |     0.626 |     0.484 |      0.176 |    -0.11  |    0.031 |      0.372 |      0.461 |    -15015.8 |    -7425.93 |   nan     |   nan     | COSTS-MEAN(drawdown for P&L) |
| SIZER_S2  | rst10_dist_atr|d-1|ALONE:D3           | ts                |     nan     |     0.617 |     0.479 |     -0.024 |   nan     |    0.003 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | rst10_dist_atr|d-1|ALONE:D3           | ts                |     nan     |     0.617 |     0.479 |     -0.024 |   nan     |    0.003 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | es_corr0_60|d+1|ALONE:D3              | ts                |     nan     |     0.594 |     0.499 |      0.051 |   nan     |   -0.343 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | es_corr0_60|d+1|ALONE:D3              | ts                |     nan     |     0.594 |     0.499 |      0.051 |   nan     |   -0.343 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | tod_rem_range_pts|d-1|ALONE:D3        | ts                |     nan     |     0.628 |     0.464 |      0.252 |   nan     |    0.25  |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | tod_rem_range_pts|d-1|ALONE:D3        | ts                |     nan     |     0.628 |     0.464 |      0.252 |   nan     |    0.25  |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | bk_sess_n_closed|d+1|ALONE:D3         | ts                |     nan     |     0.601 |     0.484 |      0.308 |   nan     |   -0.015 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | bk_sess_n_closed|d+1|ALONE:D3         | ts                |     nan     |     0.601 |     0.484 |      0.308 |   nan     |   -0.015 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S1  | ('g13', 'ers_15m_20', -1, 'LIN', 'C') | V13T_LIVE_seq(ts) |     nan     |     0.621 |     0.459 |      0.041 |    -0.241 |   -0.603 |      0.37  |      0.435 |    -18844.3 |    -8514.3  |   nan     |   nan     | COSTS-MEAN(drawdown for P&L) |
| SIZER_S2  | hurst_60|d-1|ALONE:D3                 | ts                |     nan     |     0.567 |     0.511 |      0.323 |   nan     |   -0.763 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | hurst_60|d-1|ALONE:D3                 | ts                |     nan     |     0.567 |     0.511 |      0.323 |   nan     |   -0.763 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | vr_60|d-1|ALONE:D3                    | ts                |     nan     |     0.567 |     0.511 |      0.323 |   nan     |   -0.763 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |
| SIZER_S2  | vr_60|d-1|ALONE:D3                    | ts                |     nan     |     0.567 |     0.511 |      0.323 |   nan     |   -0.763 |    nan     |    nan     |       nan   |      nan    |   nan     |   nan     | FRAGILE(drop-carry<=0)       |

## Row counts

program
SIZER_ADD             52
SIZER_Q1               2
SIZER_Q2              52
SIZER_S1            1001
SIZER_S1B            616
SIZER_S1B_EQLOTS       4
SIZER_S1B_TS          28
SIZER_S1_EQLOTS       11
SIZER_S1_HYST        174
SIZER_S2            4256
SIZER_S2V             99
SIZER_S2V_HYBRID      28
SIZER_S2V_MEAN        17
SIZER_S3             114
