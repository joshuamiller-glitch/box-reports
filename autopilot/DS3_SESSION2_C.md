# DS3_SESSION2_C - the 2023 problem on the MEASURED survivors (D3SA item C), 2026-10-28
Research only; UNTOUCHED never read. Prereg l2vast/ds3/prereg/SSC_prereg.md sha256 0337ce87165880a29c8579f54ad946830a4dc894549286ddba0322e2f63923db (before any feature or gate was computed). Universe: the 146 MEASURED SESSION-CANDIDATE cell-sessions of the A replay (V0 basis, net pts, session-book lock), 9 clusters; survivors table = best measured-PRE-t cell per cluster. Code l2vast/ds3/code/ssa/ssa_c.py; data out/ssa/c_cells.csv, c_char.csv. Gate cells: F = prior-session range known at the session open, q in {0,33,50,67} percentile of F in PRE, chosen on PRE $/wk only, HOLD one look (logged out/ssa/looks_c.json). F_C = 4 x 146 gate cells; best-of is a label.

## Verdict (plain)
- **2023 is a low-range year and the survivors' sign flip lines up with it.** Median session range in 2023-04..2024-01 vs 2024-26 (pts): NY-AM 133 vs 193, ASIA 51 vs 94, LONDON 75 vs 112; the prior-session range F is 124 vs 197 (median over survivors); volume is not lower in 2023 (255k vs 218k contracts per session, median) and trend efficiency |close-open|/range is the same (0.46 vs 0.47). By the prereg rule (X range or F below 2024-26 and mean pts monotone from F tercile 1 to 3) 109 of 146 survivors are 'volatility-regime' cells; the mean MEASURED pts per trade by F tercile (median over survivors) is T1 +1.3, T2 +2.2, T3 +2.7.
- **But a session-range gate does not fix 2023 without costing 2024-26.** Chosen on PRE, the gate was q=0 (no gate) for 134 of 146 cells; only 12 cells selected a gate, 2 'fix 2023' (ba2/ST_t45_s60 NY-AM, ba3/seq_HM_LONDON_t30_s60 NY-AM, both at q67) and for them the HOLD $/wk falls from +871 / +988 to -107 / -43 (the point-estimate cost is large; by the prereg 'costs 2024-26' test, a drop larger than the HOLD MDE of the $/wk, 0 of 146 are flagged only because the HOLD MDE in $/wk is large; read it as unproven, not as free). Sensitivity (not selection): a gate at the PRE 67th percentile of F turns the 2023 mean positive for 128 of 146 cells (median +14.9 pts) only because it keeps about 2% of 2023 trades (median 4 trades) and the HOLD income of the whole set goes from +95.0k/wk (no gate) to -2.9k/wk. The 33rd/50th percentile gates keep 25%/12.5% of the 2023 trades and are worse in 2023 (median X mean -3.1 / -3.4 pts vs -1.6 ungated) while cutting HOLD $/wk to 64k / 45k.
- So: the 2023 loss is a low-volatility regime effect in the descriptive sense, but a rule that is known at the open and tuned on 2024-25 cannot use it: 2023's ranges sit below the PRE bottom third, so any gate that excludes 2023 also excludes most of the profitable days in 2024-26. 2023 is a regime the sample cannot validate, not one a gate repairs.
- X-span numbers: ungated MEASURED X mean is negative for 114 of the 146 survivors (median -1.61 pts); only ba2/HM_t75_s90 NY-AM (+9.6), SB_HM_st_sig0 NY-AM (+7.7), ba2/KB_t90_s90 NY-AM (+9.1), ba2/SM_t75_sst ASIA (+4.0) and ba2/ST_t120_s50 NY-AM (+3.7) and ba2 IF_5m_tg_pd LONDON (+0.8) of the 9 cluster bests are positive in 2023 (6 of 9; ASIA EM / SS_HM and IF_3m_tg_pd are negative): NY-AM survivors are the ones that did not need a fix.

## Best cell per cluster: ungated vs gate chosen on PRE (X mean pts, n; $/wk with the session-book lock; HOLD MDE in $/wk)
| cell                  | sess   |   q |   x_mean_u |   x_mean_g |   n_x_u |   n_x_g |   pre_dwk_u |   pre_dwk_g |   hold_dwk_u |   hold_dwk_g |   hold_mde_dwk |   x_dwk_u |   x_dwk_g | fixes_2023   | costs_2024_26   |
|:----------------------|:-------|----:|-----------:|-----------:|--------:|--------:|------------:|------------:|-------------:|-------------:|---------------:|----------:|----------:|:-------------|:----------------|
| ba2/HM_t75_s90        | NY-AM  |   0 |        9.6 |        9.6 |     156 |     156 |      1115.1 |      1115.1 |        578.9 |        578.9 |         1875.6 |     667.8 |     667.8 | False        | False           |
| ba2/EM_t60_s40        | ASIA   |   0 |       -2.4 |       -2.4 |     152 |     152 |       491   |       491   |        192.3 |        192.3 |          965.8 |    -164.6 |    -164.6 | False        | False           |
| ba2/SM_t75_sst        | ASIA   |   0 |        4   |        4   |     134 |     134 |       768.5 |       768.5 |        138.8 |        138.8 |         1617.8 |     432.9 |     432.9 | False        | False           |
| SB_HM_st_sig0         | NY-AM  |   0 |        7.7 |        7.7 |      43 |      43 |       477.2 |       477.2 |        -59.2 |        -59.2 |         1946.1 |     258.9 |     258.9 | False        | False           |
| ba2/ST_t120_s50       | NY-AM  |   0 |        3.7 |        3.7 |     203 |     203 |       957.8 |       957.8 |       1039.9 |       1039.9 |         1958.2 |     331.5 |     331.5 | False        | False           |
| ba2/KB_t90_s90        | NY-AM  |   0 |        9.1 |        9.1 |     164 |     164 |      1094.9 |      1094.9 |        287.1 |        287.1 |         2173.9 |     662.7 |     662.7 | False        | False           |
| ba/SS_HM_ASIA_t75_s60 | ASIA   |   0 |       -2.8 |       -2.8 |     237 |     237 |       527.7 |       527.7 |        793.2 |        793.2 |         1432.3 |    -294.8 |    -294.8 | False        | False           |
| IF_3m_tg_pd           | LONDON |   0 |       -3.2 |       -3.2 |     275 |     275 |       866.6 |       866.6 |        603.6 |        603.6 |         5249.6 |   -2152.6 |   -2152.6 | False        | False           |
| IF_5m_tg_pd           | LONDON |   0 |        0.8 |        0.8 |     242 |     242 |      1129.8 |      1129.8 |       1911.9 |       1911.9 |         4210.9 |     437.4 |     437.4 | False        | False           |

## Characterisation (no selection), best cell per cluster
| cell                  | sess   |   range_med_X |   range_med_Y |   vol_med_X |   vol_med_Y |   eff_med_X |   eff_med_Y |   F_med_X |   F_med_Y |   T1 |   T2 |   T3 |   x_mean |   y_mean | vol_regime   |
|:----------------------|:-------|--------------:|--------------:|------------:|------------:|------------:|------------:|----------:|----------:|-----:|-----:|-----:|---------:|---------:|:-------------|
| IF_3m_tg_pd           | LONDON |          74.5 |         111.6 |       55254 |       46042 |         0.5 |         0.4 |      49   |      90   |  0.1 | -1.9 |  1.4 |     -3.5 |      1.4 | True         |
| IF_5m_tg_pd           | LONDON |          74.5 |         111.6 |       55254 |       46042 |         0.5 |         0.4 |      48.8 |      87   |  1.7 | -1.4 |  4.3 |      0.4 |      2.1 | True         |
| SB_HM_st_sig0         | NY-AM  |         133.2 |         192.6 |      254970 |      217683 |         0.5 |         0.5 |     133.8 |     222.5 |  8.3 |  3.1 |  2.5 |      7.7 |      4.2 | False        |
| ba/SS_HM_ASIA_t75_s60 | ASIA   |          51.2 |          93.5 |       28268 |       29570 |         0.5 |         0.5 |     177.8 |     270.5 |  3.7 |  0.5 |  3   |     -3   |      3.6 | False        |
| ba2/EM_t60_s40        | ASIA   |          51.2 |          93.5 |       28268 |       29570 |         0.5 |         0.5 |     176   |     256.5 |  2.9 |  4.1 |  2.7 |     -1.6 |      5.1 | False        |
| ba2/HM_t75_s90        | NY-AM  |         133.2 |         192.6 |      254970 |      217683 |         0.5 |         0.5 |     128.1 |     197.4 | 11.9 |  7.7 |  7   |      9.6 |      8.7 | False        |
| ba2/KB_t90_s90        | NY-AM  |         133.2 |         192.6 |      254970 |      217683 |         0.5 |         0.5 |     133   |     214.2 |  7.5 | 10.7 |  0.1 |      8.5 |      5.6 | False        |
| ba2/SM_t75_sst        | ASIA   |          51.2 |          93.5 |       28268 |       29570 |         0.5 |         0.5 |     178.8 |     242   |  9   |  4.1 |  2.3 |      4.3 |      5.2 | False        |
| ba2/ST_t120_s50       | NY-AM  |         133.2 |         192.6 |      254970 |      217683 |         0.5 |         0.5 |     123.8 |     209.4 |  4.5 |  7   |  3.7 |      3.2 |      5.4 | False        |

## By session (median over the survivors; vol_regime = number of cells flagged)
| sess    |   cells |   range_X |   range_Y |    vol_X |   vol_Y |   eff_X |   eff_Y |   F_X |   F_Y |   T1 |   T3 |   x_mean |   y_mean |   vol_regime |
|:--------|--------:|----------:|----------:|---------:|--------:|--------:|--------:|------:|------:|-----:|-----:|---------:|---------:|-------------:|
| ASIA    |      58 |      51.2 |      93.5 |  28268   |   29570 |     0.5 |     0.5 | 177.4 | 275.5 |  1.3 |  2.6 |     -2   |      2.6 |           51 |
| LONDON  |       4 |      74.5 |     111.6 |  55254   |   46042 |     0.5 |     0.4 |  48.1 |  87.4 | -0.3 |  1.6 |     -1.2 |      0.8 |            4 |
| NY-AM   |      83 |     133.2 |     192.6 | 254970   |  217683 |     0.5 |     0.5 | 122.5 | 189.9 |  1.3 |  3   |     -0.4 |      3.5 |           53 |
| PREOPEN |       1 |      46.5 |      62.2 |  24773.5 |   20555 |     0.4 |     0.4 |  82.5 | 113.2 | -2.1 |  2   |     -1.9 |      0.8 |            1 |

## Gate sensitivity over all 146 survivors (descriptive, not used for selection)
|   q |   median X mean pts |   cells with X mean>0 |   median X trades kept |   sum HOLD $/wk |   sum PRE $/wk |
|----:|--------------------:|----------------------:|-----------------------:|----------------:|---------------:|
|   0 |                -1.6 |                    32 |                    240 |         95037.5 |        62095   |
|  33 |                -3.1 |                    48 |                     60 |         64157.9 |        29974.5 |
|  50 |                -3.4 |                    55 |                     30 |         45086.9 |        17473.5 |
|  67 |                14.9 |                   128 |                      4 |         -2918.7 |        26482.7 |
