# DS3_SESSION2_B_pool_c7p1 - Pool family C7P1 entry-clock re-run and session scoring

Written 2026-10-28T21:11:59Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/pool_c7p1/. Prereg l2vast/ds3/prereg/SB3_pool_c7p1_prereg.md sha256 4f11b957612c633e572b80f54be84350b35bfb51f2d628e3a3917df750570de7; PREHOLD autopilot/DS3_SESSION2_B_pool_c7p1_PREHOLD.md sha256 e80a5c62f8843eb1ca88f78f8885119e889cfccdf8fe29444a973fafdaa8c8de (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run of the original core (run_cell -> trade records: exit bar, net $, entry bar index) for every grid cell of the pool family; entry time = ET minute of the entry bar (HM) on the label-day calendar (label day minus one calendar day for minutes >= 18:00), pnl = net $ per trade as in the pool series (instrument costs, NT8sim fills: MAPPED, not direct), lots = contracts. Side is not carried by the trade record (stored as 0), so the overlap-cluster Jaccard uses entry minute only (clusters are a conservative merge). Cell label column shows the original pool name and pool tier (F-* = failed pooled, T1/T2 = passed pooled). Entries are bar-level market entries; exits opp/trail/time are dynamic, brk is a fixed stop=target bracket (par x BS points).

Reproduction: the daily $ series of every cell equals the stored series (real_*.pkl X) for all days up to 2026-10-13 (rtol 1e-4) and, for C5/C7/C10, the stored 2013-2022 trade count; the stored pickles predate the 2026-10-19 end-of-day fix and the series extension, so the re-run uses ENDI_LEGACY and is compared only up to 2026-10-13 (the window used here ends 2026-02-06). All cells checked, rates in out/sb3/pool_<mod>/repro_*.json.

## 2. Multiplicity and counts
- Cells 6720; F = cells x 7 sessions = **47040**; overlap clusters (Jaccard >= 0.5, PRE entries) **702**, F_eff = **4914**. Independent (cluster x session) PRE tests with n >= 100: 3058; PRE-selected cell-sessions 95 = 68 independent (chance at 2.5% one-sided = about 76).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 17, DEAD-IN-HOLD 78; alive cells 17, alive clusters 13. HOLD sign persistence of the selected list: 46%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 2681 | 13 | 9 | 5 | 0 | 3 | C7P1_GC_924 | 376 | 305 |
| LONDON | 02:00-08:30 | 3260 | 17 | 12 | 1 | 0 | 1 | C7P1_6E_449 | 50.6 | 41.8 |
| PREOPEN | 08:30-09:30 | 1891 | 2 | 2 | 1 | 0 | 1 | C7P1_GC_425 | 117 | 154 |
| NY-AM | 09:30-12:00 | 3706 | 39 | 29 | 8 | 0 | 6 | C7P1_6E_108 | 52.0 | 53.7 |
| NY-PM | 12:00-15:00 | 2823 | 4 | 4 | 0 | 0 | 0 | - |  |  |
| CLOSE | 15:00-16:54 | 959 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 5495 | 20 | 12 | 2 | 0 | 2 | C7P1_GC_980 | 111 | 116 |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C7P1_6J_805 | LONDON | 102 | 1.36 | 57.1 | 42.6 | 3.76 | 0.58 | 50.0 | 2.89 | 13.8 | -64.2 | -25.5 | -19.9 | 34.9 | 42.9 | -64.2 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 9.06 | 228 |
| C7P1_GC_924 | ASIA | 272 | 3.63 | 376 | 305 | 3.45 | 0.41 | 97.0 | 210 | 124 | 814 | 20.1 | 33.5 | 210 | 382 | 814 | SESSION-CANDIDATE |  | BOF:not cleared | 126 | 475 |
| C7P1_6E_449 | LONDON | 249 | 3.32 | 50.6 | 41.8 | 3.39 | 0.71 | 85.0 | 17.0 | 19.4 | 5.64 | 2.93 | 6.17 | 13.1 | 74.0 | 5.64 | SESSION-CANDIDATE |  | BOF:not cleared | 7.01 | 68 |
| C7P1_GC_357 | NY-AM | 177 | 2.36 | 218 | 208 | 2.94 | 0.56 | 85.0 | -167 | 3.85 | -801 | 48.5 | 62.9 | 135 | 160 | -801 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2026 stub<=0 or none | BOF:not cleared | -0.77 | 403 |
| C7P1_GC_983 | NY | 217 | 2.89 | 177 | 172 | 2.87 | 0.63 | 93.0 | 1.12 | -201 | 842 | -52.0 | -35.1 | 64.5 | 67.3 | 842 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 95.5 | 365 |
| C7P1_GC_768 | ASIA | 227 | 3.03 | 223 | 220 | 2.84 | 0.59 | 112 | -39.8 | -195 | 826 | 4.71 | -32.2 | 201 | 33.6 | 826 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 64.5 | 464 |
| C7P1_GC_999 | NY | 266 | 3.55 | 94.4 | 93.6 | 2.82 | 0.58 | 122 | -176 | -205 | -36.3 | -36.3 | -20.1 | 34.9 | -26.6 | -36.3 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 34.2 | 365 |
| C7P1_GC_997 | NY | 266 | 3.55 | 94.4 | 93.6 | 2.82 | 0.58 | 122 | -176 | -205 | -36.3 | -36.3 | -20.1 | 34.9 | -26.6 | -36.3 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 1.10 | 363 |
| C7P1_GC_925 | ASIA | 126 | 1.68 | 569 | 565 | 2.82 | 0.45 | 46.0 | 366 | 423 | 51.4 | 64.3 | 95.1 | 273 | 711 | 51.4 | SESSION-CANDIDATE |  | BOF:not cleared | 127 | 475 |
| C7P1_6J_936 | ASIA | 211 | 2.81 | 45.1 | 45.2 | 2.79 | 0.63 | 112 | -6.34 | -4.79 | -13.9 | -9.73 | -1.83 | 6.76 | 41.3 | -13.9 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 10.9 | 238 |
| C7P1_6J_712 | ASIA | 185 | 2.47 | 43.4 | 43.7 | 2.78 | 0.61 | 102 | -41.6 | -26.0 | -114 | -25.6 | -29.0 | 27.0 | 16.8 | -114 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 12.4 | 222 |
| C7P1_6E_210 | NY-AM | 190 | 2.53 | 45.7 | 46.8 | 2.74 | 0.59 | 85.0 | 11.1 | 21.0 | -19.1 | -32.1 | -22.9 | 23.5 | 40.6 | -19.1 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 13.8 | 33 |
| C7P1_6E_108 | NY-AM | 167 | 2.23 | 52.0 | 53.7 | 2.71 | 0.59 | 63.0 | 22.6 | 10.3 | 166 | 20.6 | 23.2 | 20.5 | 61.0 | 166 | SESSION-CANDIDATE |  | BOF:not cleared | -2.66 | 21 |
| C7P1_GC_600 | ASIA | 203 | 2.71 | 259 | 269 | 2.70 | 0.59 | 90.0 | 148 | -149 | 1339 | -20.1 | -38.3 | 62.8 | 233 | 1339 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 55.8 | 452 |
| C7P1_GC_359 | NY-AM | 168 | 2.24 | 207 | 215 | 2.69 | 0.57 | 79.0 | -149 | 59.7 | -1040 | 42.5 | 56.6 | 135 | 173 | -1040 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2026 stub<=0 or none | BOF:not cleared | 34.5 | 404 |
| C7P1_6E_210 | NY | 311 | 4.15 | 29.0 | 30.2 | 2.69 | 0.55 | 150 | -5.79 | 1.34 | -31.1 | -32.5 | -29.7 | 15.9 | 19.0 | -31.1 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2026 stub<=0 or none | BOF:not cleared | 13.8 | 33 |
| C7P1_GC_981 | NY | 205 | 2.73 | 169 | 176 | 2.68 | 0.62 | 87.0 | 72.8 | -133 | 1059 | -62.4 | -43.7 | 56.6 | 91.7 | 1059 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 12.2 | 363 |
| C7P1_GC_980 | NY | 453 | 6.04 | 111 | 116 | 2.66 | 0.58 | 182 | 87.5 | 13.8 | 493 | -53.9 | -50.2 | 63.6 | 91.2 | 493 | SESSION-CANDIDATE |  | BOF:not cleared | -10.9 | 479 |
| C7P1_GC_309 | ASIA | 192 | 2.56 | 344 | 363 | 2.65 | 0.36 | 61.0 | 925 | 629 | 2635 | -30.0 | -38.8 | 209 | 598 | 2635 | SESSION-CANDIDATE |  | BOF:not cleared | 59.2 | 401 |
| C7P1_GC_616 | ASIA | 194 | 2.59 | 379 | 402 | 2.64 | 0.35 | 69.0 | 493 | -46.1 | 2143 | 27.7 | 9.32 | 262 | 301 | 2143 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 193 | 454 |
| C7P1_6E_360 | NY | 375 | 5.00 | 28.5 | 30.3 | 2.63 | 0.53 | 170 | 16.7 | 23.0 | -16.6 | -14.3 | -20.4 | 25.6 | 29.2 | -16.6 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 4.01 | 46 |
| C7P1_GC_980 | NY-AM | 222 | 2.96 | 173 | 188 | 2.57 | 0.60 | 78.0 | -127 | -66.3 | -464 | -70.4 | -60.0 | 91.8 | 116 | -464 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | -10.9 | 479 |
| C7P1_GC_361 | NY-AM | 110 | 1.47 | 322 | 352 | 2.56 | 0.59 | 52.0 | 207 | 177 | 373 | 59.1 | 67.1 | 194 | 330 | 373 | SESSION-CANDIDATE |  | BOF:not cleared | 74.6 | 403 |
| C7P1_GC_620 | LONDON | 143 | 1.91 | 131 | 146 | 2.52 | 0.62 | 55.0 | -62.6 | -20.0 | -607 | 6.01 | -6.05 | 101 | 89.9 | -607 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 25.0 | 454 |
| C7P1_GC_308 | ASIA | 228 | 3.04 | 279 | 314 | 2.48 | 0.34 | 71.0 | 579 | 281 | 2635 | -58.2 | -60.9 | 168 | 384 | 2635 | SESSION-CANDIDATE |  | BOF:not cleared | 61.1 | 401 |
| C7P1_GC_221 | LONDON | 296 | 3.95 | 190 | 214 | 2.48 | 0.52 | 138 | -333 | -253 | -714 | -44.0 | -54.4 | 54.0 | 77.9 | -714 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 42.8 | 391 |
| C7P1_ZB_166 | NY-AM | 103 | 1.37 | 81.2 | 92.5 | 2.46 | 0.58 | 39.0 | -94.1 | -72.5 | -213 | 16.3 | -9.83 | 77.7 | 30.2 | -213 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 1.96 | 506 |
| C7P1_GC_617 | ASIA | 126 | 1.68 | 491 | 569 | 2.42 | 0.37 | 39.0 | 267 | 462 | -385 | 129 | 128 | 314 | 638 | -385 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 193 | 454 |
| C7P1_GC_982 | NY | 501 | 6.68 | 96.1 | 112 | 2.41 | 0.58 | 199 | -7.63 | -107 | 493 | -49.9 | -46.1 | 57.4 | 21.5 | 493 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 34.8 | 364 |
| C7P1_GC_189 | NY-AM | 170 | 2.27 | 178 | 209 | 2.38 | 0.56 | 66.0 | 320 | 548 | -610 | 56.7 | 38.0 | 155 | 373 | -610 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 5.51 | 388 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C7P1_6J_805 | LONDON | 102 | 1.36 | 57.1 | 42.6 | 3.76 | 0.58 | 50.0 | 2.89 | 13.8 | -64.2 | -25.5 | -19.9 | 34.9 | 42.9 | -64.2 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 9.06 | 228 |
| C7P1_GC_924 | ASIA | 272 | 3.63 | 376 | 305 | 3.45 | 0.41 | 97.0 | 210 | 124 | 814 | 20.1 | 33.5 | 210 | 382 | 814 | SESSION-CANDIDATE |  | BOF:not cleared | 126 | 475 |
| C7P1_6E_449 | LONDON | 249 | 3.32 | 50.6 | 41.8 | 3.39 | 0.71 | 85.0 | 17.0 | 19.4 | 5.64 | 2.93 | 6.17 | 13.1 | 74.0 | 5.64 | SESSION-CANDIDATE |  | BOF:not cleared | 7.01 | 68 |
| C7P1_GC_357 | NY-AM | 177 | 2.36 | 218 | 208 | 2.94 | 0.56 | 85.0 | -167 | 3.85 | -801 | 48.5 | 62.9 | 135 | 160 | -801 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2026 stub<=0 or none | BOF:not cleared | -0.77 | 403 |
| C7P1_GC_983 | NY | 217 | 2.89 | 177 | 172 | 2.87 | 0.63 | 93.0 | 1.12 | -201 | 842 | -52.0 | -35.1 | 64.5 | 67.3 | 842 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 95.5 | 365 |
| C7P1_GC_768 | ASIA | 227 | 3.03 | 223 | 220 | 2.84 | 0.59 | 112 | -39.8 | -195 | 826 | 4.71 | -32.2 | 201 | 33.6 | 826 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 64.5 | 464 |
| C7P1_GC_997 | NY | 266 | 3.55 | 94.4 | 93.6 | 2.82 | 0.58 | 122 | -176 | -205 | -36.3 | -36.3 | -20.1 | 34.9 | -26.6 | -36.3 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 1.10 | 363 |
| C7P1_6J_936 | ASIA | 211 | 2.81 | 45.1 | 45.2 | 2.79 | 0.63 | 112 | -6.34 | -4.79 | -13.9 | -9.73 | -1.83 | 6.76 | 41.3 | -13.9 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 10.9 | 238 |
| C7P1_6J_712 | ASIA | 185 | 2.47 | 43.4 | 43.7 | 2.78 | 0.61 | 102 | -41.6 | -26.0 | -114 | -25.6 | -29.0 | 27.0 | 16.8 | -114 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 12.4 | 222 |
| C7P1_6E_210 | NY-AM | 190 | 2.53 | 45.7 | 46.8 | 2.74 | 0.59 | 85.0 | 11.1 | 21.0 | -19.1 | -32.1 | -22.9 | 23.5 | 40.6 | -19.1 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 13.8 | 33 |
| C7P1_6E_108 | NY-AM | 167 | 2.23 | 52.0 | 53.7 | 2.71 | 0.59 | 63.0 | 22.6 | 10.3 | 166 | 20.6 | 23.2 | 20.5 | 61.0 | 166 | SESSION-CANDIDATE |  | BOF:not cleared | -2.66 | 21 |
| C7P1_GC_600 | ASIA | 203 | 2.71 | 259 | 269 | 2.70 | 0.59 | 90.0 | 148 | -149 | 1339 | -20.1 | -38.3 | 62.8 | 233 | 1339 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 55.8 | 452 |
| C7P1_GC_359 | NY-AM | 168 | 2.24 | 207 | 215 | 2.69 | 0.57 | 79.0 | -149 | 59.7 | -1040 | 42.5 | 56.6 | 135 | 173 | -1040 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2026 stub<=0 or none | BOF:not cleared | 34.5 | 404 |
| C7P1_GC_980 | NY | 453 | 6.04 | 111 | 116 | 2.66 | 0.58 | 182 | 87.5 | 13.8 | 493 | -53.9 | -50.2 | 63.6 | 91.2 | 493 | SESSION-CANDIDATE |  | BOF:not cleared | -10.9 | 479 |
| C7P1_GC_309 | ASIA | 192 | 2.56 | 344 | 363 | 2.65 | 0.36 | 61.0 | 925 | 629 | 2635 | -30.0 | -38.8 | 209 | 598 | 2635 | SESSION-CANDIDATE |  | BOF:not cleared | 59.2 | 401 |
| C7P1_GC_616 | ASIA | 194 | 2.59 | 379 | 402 | 2.64 | 0.35 | 69.0 | 493 | -46.1 | 2143 | 27.7 | 9.32 | 262 | 301 | 2143 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 193 | 454 |
| C7P1_6E_360 | NY | 375 | 5.00 | 28.5 | 30.3 | 2.63 | 0.53 | 170 | 16.7 | 23.0 | -16.6 | -14.3 | -20.4 | 25.6 | 29.2 | -16.6 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 4.01 | 46 |
| C7P1_GC_221 | LONDON | 296 | 3.95 | 190 | 214 | 2.48 | 0.52 | 138 | -333 | -253 | -714 | -44.0 | -54.4 | 54.0 | 77.9 | -714 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 42.8 | 391 |
| C7P1_ZB_166 | NY-AM | 103 | 1.37 | 81.2 | 92.5 | 2.46 | 0.58 | 39.0 | -94.1 | -72.5 | -213 | 16.3 | -9.83 | 77.7 | 30.2 | -213 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 1.96 | 506 |
| C7P1_GC_982 | NY | 501 | 6.68 | 96.1 | 112 | 2.41 | 0.58 | 199 | -7.63 | -107 | 493 | -49.9 | -46.1 | 57.4 | 21.5 | 493 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 34.8 | 364 |
| C7P1_GC_189 | NY-AM | 170 | 2.27 | 178 | 209 | 2.38 | 0.56 | 66.0 | 320 | 548 | -610 | 56.7 | 38.0 | 155 | 373 | -610 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 5.51 | 388 |
| C7P1_ZB_52 | NY-AM | 106 | 1.41 | 91.2 | 108 | 2.37 | 0.60 | 37.0 | -54.2 | -21.1 | -157 | 12.3 | -9.17 | 69.3 | 71.6 | -157 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | -31.8 | 517 |
| C7P1_CL_23 | NY-AM | 167 | 2.23 | 110 | 130 | 2.37 | 0.59 | 79.0 | -65.8 | -41.6 | -188 | -145 | -135 | 125 | -3.09 | -188 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 11.2 | 244 |
| C7P1_6J_989 | NY-PM | 132 | 1.76 | 20.6 | 24.4 | 2.37 | 0.58 | 57.0 | -4.12 | -10.0 | 32.0 | 7.42 | 11.8 | 8.14 | 12.2 | 32.0 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | -8.35 | 125 |
| C7P1_6J_991 | NY-PM | 138 | 1.84 | 19.4 | 23.5 | 2.32 | 0.58 | 60.0 | -6.65 | -9.99 | 18.7 | 7.93 | 12.2 | 7.72 | 10.8 | 18.7 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 1.89 | 127 |
| C7P1_6E_26 | LONDON | 108 | 1.44 | 72.9 | 88.5 | 2.31 | 0.58 | 38.0 | -84.3 | -79.9 | -107 | -131 | -128 | 24.3 | 38.0 | -107 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 3.91 | 1 |
| C7P1_GC_1026 | NY-PM | 149 | 1.99 | 127 | 155 | 2.29 | 0.57 | 58.0 | -38.8 | -137 | 337 | -29.2 | -20.9 | 56.2 | 59.9 | 337 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 28.7 | 369 |
| C7P1_GC_1024 | NY-PM | 149 | 1.99 | 127 | 155 | 2.29 | 0.57 | 58.0 | -38.8 | -137 | 337 | -29.2 | -20.9 | 56.2 | 59.9 | 337 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | -6.90 | 367 |
| C7P1_6J_443 | LONDON | 115 | 1.53 | 47.9 | 58.5 | 2.29 | 0.63 | 51.0 | -20.4 | -23.6 | -5.75 | -3.09 | 11.1 | 38.4 | 10.3 | -5.75 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 1.33 | 176 |
| C7P1_CL_259 | NY-AM | 175 | 2.33 | 43.3 | 53.4 | 2.27 | 0.62 | 76.0 | 16.6 | 27.4 | -40.9 | -49.4 | -60.8 | 61.5 | 24.0 | -40.9 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 9.68 | 280 |


## 5. Dead pooled, alive in a session
8 cell-sessions (8 cells, 8 independent). Top 30:
| cid | session | n | tpw | mean | mde | t | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | bof_label | label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C7P1_6E_449 | LONDON | 249 | 3.32 | 50.6 | 41.8 | 3.39 | 85.0 | 17.0 | 19.4 | 5.64 | 2.93 | 6.17 | 13.1 | 74.0 | 5.64 | SESSION-CANDIDATE | BOF:not cleared | C7P1_6E/5_rsi_5_20_opp_0_all_1|F-HOLD (holdout <=0) | 7.01 | 68 |
| C7P1_6E_108 | NY-AM | 167 | 2.23 | 52.0 | 53.7 | 2.71 | 63.0 | 22.6 | 10.3 | 166 | 20.6 | 23.2 | 20.5 | 61.0 | 166 | SESSION-CANDIDATE | BOF:not cleared | C7P1_6E/5_macd_8_17_time_240_all_0|F-HOLD (holdout <=0) | -2.66 | 21 |
| C7P1_GC_980 | NY | 453 | 6.04 | 111 | 116 | 2.66 | 182 | 87.5 | 13.8 | 493 | -53.9 | -50.2 | 63.6 | 91.2 | 493 | SESSION-CANDIDATE | BOF:not cleared | C7P1_GC/15_rsi_2_10_opp_0_all_0|F-HOLD (holdout <=0) | -10.9 | 479 |
| C7P1_GC_97 | NY-AM | 141 | 1.88 | 186 | 235 | 2.21 | 62.0 | 322 | 345 | 243 | -99.2 | -136 | 251 | 206 | 243 | SESSION-CANDIDATE | BOF:not cleared | C7P1_GC/5_macd_8_17_brk_1.5_all_1|F-X (2023-04..2024-01 <=0) | 28.2 | 361 |
| C7P1_6E_24 | NY-AM | 157 | 2.09 | 44.0 | 55.7 | 2.21 | 58.0 | 12.8 | 7.79 | 65.6 | 38.5 | 48.3 | 15.4 | 51.0 | 65.6 | SESSION-CANDIDATE | BOF:not cleared | C7P1_6E/5_ema_9_21_time_240_all_0|F-HOLD (holdout <=0) | 2.13 | 0 |
| C7P1_GC_425 | PREOPEN | 118 | 1.57 | 117 | 154 | 2.13 | 54.0 | 75.9 | 73.2 | 84.3 | -71.1 | -66.8 | 5.89 | 174 | 84.3 | SESSION-CANDIDATE | BOF:not cleared | C7P1_GC/5_rsi_2_10_brk_0.6666666666666666_all_1|F-HOLD (holdout <=0) | -24.2 | 411 |
| C7P1_GC_195 | NY | 229 | 3.05 | 140 | 185 | 2.13 | 107 | 388 | 236 | 912 | -49.5 | -62.0 | 58.1 | 255 | 912 | SESSION-CANDIDATE | BOF:not cleared | C7P1_GC/5_st_10_2_time_240_day_1|F-HOLD (holdout <=0) | 59.7 | 389 |
| C7P1_6E_14 | NY-AM | 203 | 2.71 | 32.5 | 43.6 | 2.08 | 82.0 | 5.53 | 0.59 | 41.1 | 18.6 | 12.3 | 10.1 | 43.4 | 41.1 | SESSION-CANDIDATE | BOF:not cleared | C7P1_6E/5_ema_9_21_brk_1.5_day_0|F-HOLD (holdout <=0) | 12.3 | 1 |

