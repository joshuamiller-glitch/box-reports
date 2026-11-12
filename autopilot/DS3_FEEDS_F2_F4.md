# DS3_FEEDS_F2_F4 - F4 owned-data screen (W-FD2), first-order, Shadow only, no PASS claims

Events: 270 (CLAIMS/NFP/CPI 08:30 ET with actual+prior, 2023-04..); consensus unavailable (0 cells); surprise = actual-prior (z_prior) and actual-trailing-3-mean (z_mom, poor-man consensus), expanding-std z. Placebo: same 08:30 clock window on non-event days, 2000 draws per cell (all non-event days; not purely forward). Cells tested: 360; cells with placebo p<=0.05 (obs pnl LOWER than placebo = skipping gains): 3 (expected by chance about 18.0).

Periods: PRE 2023-04..2025-06, GAP 2025-07..10, HOLD 2025-11..2026-04, L6M 2026-05..10 (coarse). Events by period: {'PRE': 171, 'L6M': 38, 'HOLD': 37, 'GAP': 24}

## Cells with p_lower <= 0.05 (observed in-window pnl below placebo)

| cell     | sel     | period   | kind                  |   n_events |   obs_pnl |   placebo_mean |   p_lower |
|:---------|:--------|:---------|:----------------------|-----------:|----------:|---------------:|----------:|
| LPB_BASE | big_mom | PRE      | open_post_release_pnl |         33 |    -56040 |        7920.86 |     0.004 |
| LPB_BASE | all     | PRE      | open_post_release_pnl |        171 |    -70175 |       35819.2  |     0.014 |
| LPB_BASE | big_mom | ALL      | open_post_release_pnl |         60 |    -38795 |       12076.5  |     0.048 |

## Summary by base x selection x kind (ALL periods; obs vs placebo mean, p_lower)

| cell         | sel            | period   | kind                     |   n_events |   obs_pnl |   placebo_mean |   p_lower |
|:-------------|:---------------|:---------|:-------------------------|-----------:|----------:|---------------:|----------:|
| JN05W2       | all            | ALL      | entries_in_window_1m     |        270 |      0    |          0     |     1     |
| JN05W2       | all            | ALL      | entries_in_window_5m     |        270 |      0    |          0     |     1     |
| JN05W2       | all            | ALL      | entries_in_window_10m    |        270 |      0    |          0     |     1     |
| JN05W2       | all            | ALL      | entries_in_window_30m    |        270 |      0    |          0     |     1     |
| JN05W2       | all            | ALL      | open_at_release          |        270 | 204476    |     192949     |     0.568 |
| JN05W2       | big_prior      | ALL      | entries_in_window_1m     |         71 |      0    |          0     |     1     |
| JN05W2       | big_prior      | ALL      | entries_in_window_5m     |         71 |      0    |          0     |     1     |
| JN05W2       | big_prior      | ALL      | entries_in_window_10m    |         71 |      0    |          0     |     1     |
| JN05W2       | big_prior      | ALL      | entries_in_window_30m    |         71 |      0    |          0     |     1     |
| JN05W2       | big_prior      | ALL      | open_at_release          |         71 |  84746.2  |      51643.7   |     0.794 |
| JN05W2       | big_mom        | ALL      | entries_in_window_1m     |         60 |      0    |          0     |     1     |
| JN05W2       | big_mom        | ALL      | entries_in_window_5m     |         60 |      0    |          0     |     1     |
| JN05W2       | big_mom        | ALL      | entries_in_window_10m    |         60 |      0    |          0     |     1     |
| JN05W2       | big_mom        | ALL      | entries_in_window_30m    |         60 |      0    |          0     |     1     |
| JN05W2       | big_mom        | ALL      | open_at_release          |         60 |  67052.4  |      43717.6   |     0.739 |
| JN05W2       | shock_big      | ALL      | entries_in_window_1m     |        109 |      0    |          0     |     1     |
| JN05W2       | shock_big      | ALL      | entries_in_window_5m     |        109 |      0    |          0     |     1     |
| JN05W2       | shock_big      | ALL      | entries_in_window_10m    |        109 |      0    |          0     |     1     |
| JN05W2       | shock_big      | ALL      | entries_in_window_30m    |        109 |      0    |          0     |     1     |
| JN05W2       | shock_big      | ALL      | open_at_release          |        109 |  83916    |      79228.7   |     0.542 |
| JN05W2       | all            | ALL      | open_post_release_pnl    |        270 | -82735    |     -96165.5   |     0.536 |
| JN05W2       | big_prior      | ALL      | open_post_release_pnl    |         71 | -67165    |     -23901.7   |     0.222 |
| JN05W2       | big_mom        | ALL      | open_post_release_pnl    |         60 | -53030    |     -21828.5   |     0.255 |
| JN05W2       | shock_big      | ALL      | open_post_release_pnl    |        109 | -14920    |     -38198.4   |     0.59  |
| JN05W2       | z_prior_signed | ALL      | with_vs_against_mean_pnl |          0 |    nan    |        nan     |   nan     |
| JN05W2       | z_mom_signed   | ALL      | with_vs_against_mean_pnl |          0 |    nan    |        nan     |   nan     |
| JN05W2_NOCUT | all            | ALL      | entries_in_window_1m     |        270 |      0    |          0     |     1     |
| JN05W2_NOCUT | all            | ALL      | entries_in_window_5m     |        270 |      0    |          0     |     1     |
| JN05W2_NOCUT | all            | ALL      | entries_in_window_10m    |        270 |      0    |          0     |     1     |
| JN05W2_NOCUT | all            | ALL      | entries_in_window_30m    |        270 |      0    |          0     |     1     |
| JN05W2_NOCUT | all            | ALL      | open_at_release          |        270 | -26734    |       5183.76  |     0.138 |
| JN05W2_NOCUT | big_prior      | ALL      | entries_in_window_1m     |         71 |      0    |          0     |     1     |
| JN05W2_NOCUT | big_prior      | ALL      | entries_in_window_5m     |         71 |      0    |          0     |     1     |
| JN05W2_NOCUT | big_prior      | ALL      | entries_in_window_10m    |         71 |      0    |          0     |     1     |
| JN05W2_NOCUT | big_prior      | ALL      | entries_in_window_30m    |         71 |      0    |          0     |     1     |
| JN05W2_NOCUT | big_prior      | ALL      | open_at_release          |         71 |  -7256.38 |       1813.55  |     0.309 |
| JN05W2_NOCUT | big_mom        | ALL      | entries_in_window_1m     |         60 |      0    |          0     |     1     |
| JN05W2_NOCUT | big_mom        | ALL      | entries_in_window_5m     |         60 |      0    |          0     |     1     |
| JN05W2_NOCUT | big_mom        | ALL      | entries_in_window_10m    |         60 |      0    |          0     |     1     |
| JN05W2_NOCUT | big_mom        | ALL      | entries_in_window_30m    |         60 |      0    |          0     |     1     |
| JN05W2_NOCUT | big_mom        | ALL      | open_at_release          |         60 | -10986.9  |       1448.56  |     0.226 |
| JN05W2_NOCUT | shock_big      | ALL      | entries_in_window_1m     |        109 |      0    |          0     |     1     |
| JN05W2_NOCUT | shock_big      | ALL      | entries_in_window_5m     |        109 |      0    |          0     |     1     |
| JN05W2_NOCUT | shock_big      | ALL      | entries_in_window_10m    |        109 |      0    |          0     |     1     |
| JN05W2_NOCUT | shock_big      | ALL      | entries_in_window_30m    |        109 |      0    |          0     |     1     |
| JN05W2_NOCUT | shock_big      | ALL      | open_at_release          |        109 | -33275    |       2949.83  |     0.05  |
| JN05W2_NOCUT | all            | ALL      | open_post_release_pnl    |        270 |  10735    |      -1320.82  |     0.716 |
| JN05W2_NOCUT | big_prior      | ALL      | open_post_release_pnl    |         71 |    220    |          0.538 |     0.506 |
| JN05W2_NOCUT | big_mom        | ALL      | open_post_release_pnl    |         60 |   4660    |        184.81  |     0.646 |
| JN05W2_NOCUT | shock_big      | ALL      | open_post_release_pnl    |        109 |   -440    |        -62.515 |     0.484 |
| JN05W2_NOCUT | z_prior_signed | ALL      | with_vs_against_mean_pnl |          0 |    nan    |        nan     |   nan     |
| JN05W2_NOCUT | z_mom_signed   | ALL      | with_vs_against_mean_pnl |          0 |    nan    |        nan     |   nan     |
| LPB_BASE     | all            | ALL      | entries_in_window_1m     |        270 |      0    |          0     |     1     |
| LPB_BASE     | all            | ALL      | entries_in_window_5m     |        270 |      0    |          0     |     1     |
| LPB_BASE     | all            | ALL      | entries_in_window_10m    |        270 |      0    |          0     |     1     |
| LPB_BASE     | all            | ALL      | entries_in_window_30m    |        270 |      0    |          0     |     1     |
| LPB_BASE     | all            | ALL      | open_at_release          |        270 | 155370    |     229964     |     0.132 |
| LPB_BASE     | big_prior      | ALL      | entries_in_window_1m     |         71 |      0    |          0     |     1     |
| LPB_BASE     | big_prior      | ALL      | entries_in_window_5m     |         71 |      0    |          0     |     1     |
| LPB_BASE     | big_prior      | ALL      | entries_in_window_10m    |         71 |      0    |          0     |     1     |
| LPB_BASE     | big_prior      | ALL      | entries_in_window_30m    |         71 |      0    |          0     |     1     |
| LPB_BASE     | big_prior      | ALL      | open_at_release          |         71 |  37076.1  |      59737.2   |     0.298 |
| LPB_BASE     | big_mom        | ALL      | entries_in_window_1m     |         60 |      0    |          0     |     1     |
| LPB_BASE     | big_mom        | ALL      | entries_in_window_5m     |         60 |      0    |          0     |     1     |
| LPB_BASE     | big_mom        | ALL      | entries_in_window_10m    |         60 |      0    |          0     |     1     |
| LPB_BASE     | big_mom        | ALL      | entries_in_window_30m    |         60 |      0    |          0     |     1     |
| LPB_BASE     | big_mom        | ALL      | open_at_release          |         60 |  17602    |      51952.3   |     0.198 |
| LPB_BASE     | shock_big      | ALL      | entries_in_window_1m     |        109 |      0    |          0     |     1     |
| LPB_BASE     | shock_big      | ALL      | entries_in_window_5m     |        109 |      0    |          0     |     1     |
| LPB_BASE     | shock_big      | ALL      | entries_in_window_10m    |        109 |      0    |          0     |     1     |
| LPB_BASE     | shock_big      | ALL      | entries_in_window_30m    |        109 |      0    |          0     |     1     |
| LPB_BASE     | shock_big      | ALL      | open_at_release          |        109 |  46400.5  |      93181.2   |     0.178 |
| LPB_BASE     | all            | ALL      | open_post_release_pnl    |        270 | -23430    |      53386.1   |     0.075 |
| LPB_BASE     | big_prior      | ALL      | open_post_release_pnl    |         71 | -19925    |      14980.3   |     0.15  |
| LPB_BASE     | big_mom        | ALL      | open_post_release_pnl    |         60 | -38795    |      12076.5   |     0.048 |
| LPB_BASE     | shock_big      | ALL      | open_post_release_pnl    |        109 |   5460    |      23444.9   |     0.32  |
| LPB_BASE     | z_prior_signed | ALL      | with_vs_against_mean_pnl |          0 |    nan    |        nan     |   nan     |
| LPB_BASE     | z_mom_signed   | ALL      | with_vs_against_mean_pnl |          0 |    nan    |        nan     |   nan     |

## Per period (cell JN05W2, all-event selection)

| cell   | sel   | period   | kind                  |   n_events |   obs_pnl |   placebo_mean |   p_lower |
|:-------|:------|:---------|:----------------------|-----------:|----------:|---------------:|----------:|
| JN05W2 | all   | ALL      | entries_in_window_1m  |        270 |       0   |           0    |     1     |
| JN05W2 | all   | ALL      | entries_in_window_5m  |        270 |       0   |           0    |     1     |
| JN05W2 | all   | ALL      | entries_in_window_10m |        270 |       0   |           0    |     1     |
| JN05W2 | all   | ALL      | entries_in_window_30m |        270 |       0   |           0    |     1     |
| JN05W2 | all   | ALL      | open_at_release       |        270 |  204476   |      192949    |     0.568 |
| JN05W2 | all   | PRE      | entries_in_window_1m  |        171 |       0   |           0    |     1     |
| JN05W2 | all   | PRE      | entries_in_window_5m  |        171 |       0   |           0    |     1     |
| JN05W2 | all   | PRE      | entries_in_window_10m |        171 |       0   |           0    |     1     |
| JN05W2 | all   | PRE      | entries_in_window_30m |        171 |       0   |           0    |     1     |
| JN05W2 | all   | PRE      | open_at_release       |        171 |  111006   |      122150    |     0.424 |
| JN05W2 | all   | GAP      | entries_in_window_1m  |         24 |       0   |           0    |     1     |
| JN05W2 | all   | GAP      | entries_in_window_5m  |         24 |       0   |           0    |     1     |
| JN05W2 | all   | GAP      | entries_in_window_10m |         24 |       0   |           0    |     1     |
| JN05W2 | all   | GAP      | entries_in_window_30m |         24 |       0   |           0    |     1     |
| JN05W2 | all   | GAP      | open_at_release       |         24 |   27016   |       17233.8  |     0.66  |
| JN05W2 | all   | HOLD     | entries_in_window_1m  |         37 |       0   |           0    |     1     |
| JN05W2 | all   | HOLD     | entries_in_window_5m  |         37 |       0   |           0    |     1     |
| JN05W2 | all   | HOLD     | entries_in_window_10m |         37 |       0   |           0    |     1     |
| JN05W2 | all   | HOLD     | entries_in_window_30m |         37 |       0   |           0    |     1     |
| JN05W2 | all   | HOLD     | open_at_release       |         37 |   61490.4 |       27111.2  |     0.88  |
| JN05W2 | all   | L6M      | entries_in_window_1m  |         38 |       0   |           0    |     1     |
| JN05W2 | all   | L6M      | entries_in_window_5m  |         38 |       0   |           0    |     1     |
| JN05W2 | all   | L6M      | entries_in_window_10m |         38 |       0   |           0    |     1     |
| JN05W2 | all   | L6M      | entries_in_window_30m |         38 |       0   |           0    |     1     |
| JN05W2 | all   | L6M      | open_at_release       |         38 |    4963.4 |       26015.4  |     0.246 |
| JN05W2 | all   | ALL      | open_post_release_pnl |        270 |  -82735   |      -96165.5  |     0.536 |
| JN05W2 | all   | PRE      | open_post_release_pnl |        171 | -120530   |      -58188.7  |     0.234 |
| JN05W2 | all   | GAP      | open_post_release_pnl |         24 |   11200   |       -8420.77 |     0.704 |
| JN05W2 | all   | HOLD     | open_post_release_pnl |         37 |   22370   |      -13303.3  |     0.816 |
| JN05W2 | all   | L6M      | open_post_release_pnl |         38 |    4225   |      -12201.9  |     0.584 |
