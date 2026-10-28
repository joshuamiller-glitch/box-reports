# DS3_SESSION2_B_pool_c10s1 - Pool family C10S1 entry-clock re-run and session scoring

Written 2026-10-28T21:12:15Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/pool_c10s1/. Prereg l2vast/ds3/prereg/SB3_pool_c10s1_prereg.md sha256 15652b781ae51db2a6258674be43159faefdf23bc55422400556c55edb5b42db; PREHOLD autopilot/DS3_SESSION2_B_pool_c10s1_PREHOLD.md sha256 634326db71286f25efd8bd5051aa760e9ecfc645914cc2a9834cba9df9194d5b (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run of the original core (run_cell -> trade records: exit bar, net $, entry bar index) for every grid cell of the pool family; entry time = ET minute of the entry bar (HM) on the label-day calendar (label day minus one calendar day for minutes >= 18:00), pnl = net $ per trade as in the pool series (instrument costs, NT8sim fills: MAPPED, not direct), lots = contracts. Side is not carried by the trade record (stored as 0), so the overlap-cluster Jaccard uses entry minute only (clusters are a conservative merge). Cell label column shows the original pool name and pool tier (F-* = failed pooled, T1/T2 = passed pooled). Entries are bar-level market entries; exits opp/trail/time are dynamic, brk is a fixed stop=target bracket (par x BS points).

Reproduction: the daily $ series of every cell equals the stored series (real_*.pkl X) for all days up to 2026-10-13 (rtol 1e-4) and, for C5/C7/C10, the stored 2013-2022 trade count; the stored pickles predate the 2026-10-19 end-of-day fix and the series extension, so the re-run uses ENDI_LEGACY and is compared only up to 2026-10-13 (the window used here ends 2026-02-06). All cells checked, rates in out/sb3/pool_<mod>/repro_*.json.

## 2. Multiplicity and counts
- Cells 4040; F = cells x 7 sessions = **28420**; overlap clusters (Jaccard >= 0.5, PRE entries) **323**, F_eff = **2261**. Independent (cluster x session) PRE tests with n >= 100: 253; PRE-selected cell-sessions 55 = 24 independent (chance at 2.5% one-sided = about 6).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 36, DEAD-IN-HOLD 19; alive cells 29, alive clusters 13. HOLD sign persistence of the selected list: 84%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 205 | 8 | 7 | 4 | 0 | 3 | C10S1_GC_40 | 380 | 436 |
| LONDON | 02:00-08:30 | 381 | 5 | 4 | 4 | 0 | 3 | C10S1_6J_149 | 48.2 | 43.7 |
| PREOPEN | 08:30-09:30 | 8 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 267 | 23 | 6 | 14 | 0 | 6 | C10S1_ES_274 | 415 | 442 |
| NY-PM | 12:00-15:00 | 31 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| CLOSE | 15:00-16:54 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 885 | 19 | 7 | 14 | 0 | 6 | C10S1_ES_78 | 277 | 261 |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C10S1_6J_149 | LONDON | 109 | 1.45 | 48.2 | 43.7 | 3.09 | 0.65 | 55.0 | 21.8 | 18.4 | 38.9 | -28.0 | -20.4 | 38.5 | 29.4 | 38.9 | SESSION-CANDIDATE |  | BOF:not cleared | 8.36 | 51 |
| C10S1_ES_78 | NY | 217 | 2.89 | 277 | 261 | 2.98 | 0.59 | 90.0 | 231 | 170 | 595 | 40.9 | 103 | 234 | 189 | 595 | SESSION-CANDIDATE |  | BOF:not cleared | 120 | 194 |
| C10S1_ES_274 | NY-AM | 113 | 1.51 | 415 | 442 | 2.63 | 0.55 | 50.0 | 365 | 258 | 701 | 123 | 105 | 174 | 565 | 701 | SESSION-CANDIDATE |  | BOF:not cleared | 207 | 163 |
| C10S1_6J_157 | LONDON | 105 | 1.40 | 58.8 | 63.2 | 2.60 | 0.61 | 53.0 | 13.4 | 14.9 | 5.01 | -50.8 | -42.3 | 64.1 | 12.0 | 5.01 | SESSION-CANDIDATE |  | BOF:not cleared | 1.30 | 51 |
| C10S1_ES_77 | NY-AM | 100 | 1.33 | 384 | 425 | 2.53 | 0.59 | 47.0 | 351 | 320 | 564 | 78.4 | 103 | 136 | 575 | 564 | SESSION-CANDIDATE |  | BOF:not cleared | 97.7 | 194 |
| C10S1_ES_78 | NY-AM | 145 | 1.93 | 284 | 316 | 2.52 | 0.59 | 68.0 | 246 | 198 | 603 | 106 | 170 | 156 | 294 | 603 | SESSION-CANDIDATE |  | BOF:not cleared | 120 | 194 |
| C10S1_NQ_47 | NY | 112 | 1.49 | 570 | 639 | 2.49 | 0.49 | 46.0 | 320 | 428 | -399 | 125 | 160 | 193 | 842 | -399 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 384 | 272 |
| C10S1_NQ_45 | NY | 110 | 1.47 | 554 | 622 | 2.49 | 0.49 | 45.0 | 248 | 348 | -399 | 125 | 160 | 206 | 759 | -399 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 249 | 272 |
| C10S1_6J_48 | LONDON | 134 | 1.79 | 29.8 | 33.7 | 2.48 | 0.61 | 56.0 | -10.2 | -11.3 | -6.83 | -35.0 | -24.8 | 18.1 | 9.86 | -6.83 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 5.76 | 80 |
| C10S1_NQ_79 | NY-AM | 118 | 1.57 | 626 | 713 | 2.46 | 0.61 | 39.0 | 464 | 342 | 1294 | 17.5 | -64.8 | 314 | 899 | 1294 | SESSION-CANDIDATE |  | BOF:not cleared | 71.7 | 285 |
| C10S1_GC_40 | ASIA | 176 | 2.35 | 380 | 436 | 2.44 | 0.39 | 61.0 | 394 | 67.5 | 1597 | 1.11 | -14.2 | 315 | 282 | 1597 | SESSION-CANDIDATE |  | BOF:not cleared | 159 | 227 |
| C10S1_ES_76 | NY | 208 | 2.77 | 223 | 256 | 2.43 | 0.57 | 87.0 | 335 | 289 | 595 | 14.3 | 64.0 | 219 | 198 | 595 | SESSION-CANDIDATE |  | BOF:not cleared | 2.87 | 194 |
| C10S1_ES_79 | NY-AM | 107 | 1.43 | 302 | 348 | 2.43 | 0.59 | 46.0 | 215 | 163 | 564 | 125 | 154 | 141 | 360 | 564 | SESSION-CANDIDATE |  | BOF:not cleared | 100 | 194 |
| C10S1_ES_70 | NY | 348 | 4.64 | 112 | 131 | 2.40 | 0.58 | 144 | 29.0 | 29.2 | 27.9 | 38.8 | 45.6 | 113 | 55.0 | 27.9 | SESSION-CANDIDATE |  | BOF:not cleared | 32.7 | 194 |
| C10S1_NQ_68 | NY-AM | 215 | 2.87 | 282 | 330 | 2.39 | 0.60 | 97.0 | -76.2 | -63.4 | -166 | 27.8 | 14.8 | 308 | 52.7 | -166 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 71.1 | 285 |
| C10S1_GC_0 | ASIA | 237 | 3.16 | 221 | 261 | 2.38 | 0.32 | 91.0 | 687 | 166 | 2957 | 69.4 | 79.2 | 166 | 231 | 2957 | SESSION-CANDIDATE |  | BOF:not cleared | 95.2 | 196 |
| C10S1_ES_68 | NY | 345 | 4.60 | 110 | 132 | 2.33 | 0.58 | 143 | 33.1 | 34.1 | 27.9 | 37.1 | 43.6 | 113 | 55.6 | 27.9 | SESSION-CANDIDATE |  | BOF:not cleared | 19.3 | 194 |
| C10S1_ES_54 | NY-AM | 100 | 1.33 | 301 | 363 | 2.32 | 0.58 | 53.0 | 319 | 275 | 507 | -47.8 | 0.28 | -16.2 | 518 | 507 | SESSION-CANDIDATE |  | BOF:not cleared | 140 | 172 |
| C10S1_GC_60 | ASIA | 220 | 2.93 | 264 | 319 | 2.32 | 0.40 | 103 | 837 | 278 | 3156 | -30.6 | -2.95 | 142 | 335 | 3156 | SESSION-CANDIDATE |  | BOF:not cleared | 67.7 | 247 |
| C10S1_NQ_70 | NY-AM | 217 | 2.89 | 277 | 336 | 2.30 | 0.60 | 97.0 | -76.2 | -63.4 | -166 | 8.82 | -5.73 | 308 | 47.9 | -166 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 68.6 | 285 |
| C10S1_GC_340 | ASIA | 101 | 1.35 | 579 | 710 | 2.28 | 0.49 | 40.0 | 286 | 398 | -498 | 216 | 147 | 688 | 399 | -498 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 188 | 219 |
| C10S1_ES_98 | NY | 192 | 2.56 | 256 | 316 | 2.27 | 0.55 | 77.0 | 227 | 189 | 484 | -71.9 | -68.0 | 324 | 129 | 484 | SESSION-CANDIDATE |  | BOF:not cleared | 125 | 195 |
| C10S1_6J_12 | ASIA | 173 | 2.31 | 48.8 | 60.3 | 2.27 | 0.62 | 97.0 | -42.9 | -36.7 | -74.0 | -19.8 | -27.3 | 54.6 | -2.91 | -74.0 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 8.71 | 45 |
| C10S1_NQ_40 | NY-AM | 128 | 1.71 | 866 | 1071 | 2.26 | 0.52 | 60.0 | 578 | 541 | 821 | 349 | 402 | 538 | 950 | 821 | SESSION-CANDIDATE |  | BOF:not cleared | 204 | 272 |
| C10S1_NQ_42 | NY-AM | 128 | 1.71 | 866 | 1071 | 2.26 | 0.52 | 60.0 | 578 | 541 | 821 | 349 | 402 | 538 | 950 | 821 | SESSION-CANDIDATE |  | BOF:not cleared | 293 | 272 |
| C10S1_NQ_77 | NY-AM | 111 | 1.48 | 613 | 758 | 2.26 | 0.61 | 39.0 | 350 | 212 | 1294 | 9.77 | -71.8 | 282 | 836 | 1294 | SESSION-CANDIDATE |  | BOF:not cleared | 66.7 | 285 |
| C10S1_NQ_42 | NY | 209 | 2.79 | 597 | 741 | 2.26 | 0.50 | 87.0 | 423 | 439 | 311 | 188 | 200 | 284 | 832 | 311 | SESSION-CANDIDATE |  | BOF:not cleared | 293 | 272 |
| C10S1_NQ_40 | NY | 209 | 2.79 | 597 | 741 | 2.26 | 0.50 | 87.0 | 423 | 439 | 311 | 188 | 200 | 284 | 832 | 311 | SESSION-CANDIDATE |  | BOF:not cleared | 204 | 272 |
| C10S1_ES_274 | NY | 180 | 2.40 | 319 | 403 | 2.21 | 0.54 | 71.0 | 324 | 220 | 746 | 13.3 | 1.29 | 173 | 403 | 746 | SESSION-CANDIDATE |  | BOF:not cleared | 207 | 163 |
| C10S1_NQ_54 | NY-AM | 117 | 1.56 | 664 | 845 | 2.20 | 0.56 | 58.0 | 197 | 302 | -462 | 130 | 277 | 252 | 740 | -462 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 273 | 272 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C10S1_6J_149 | LONDON | 109 | 1.45 | 48.2 | 43.7 | 3.09 | 0.65 | 55.0 | 21.8 | 18.4 | 38.9 | -28.0 | -20.4 | 38.5 | 29.4 | 38.9 | SESSION-CANDIDATE |  | BOF:not cleared | 8.36 | 51 |
| C10S1_ES_78 | NY | 217 | 2.89 | 277 | 261 | 2.98 | 0.59 | 90.0 | 231 | 170 | 595 | 40.9 | 103 | 234 | 189 | 595 | SESSION-CANDIDATE |  | BOF:not cleared | 120 | 194 |
| C10S1_ES_274 | NY-AM | 113 | 1.51 | 415 | 442 | 2.63 | 0.55 | 50.0 | 365 | 258 | 701 | 123 | 105 | 174 | 565 | 701 | SESSION-CANDIDATE |  | BOF:not cleared | 207 | 163 |
| C10S1_NQ_47 | NY | 112 | 1.49 | 570 | 639 | 2.49 | 0.49 | 46.0 | 320 | 428 | -399 | 125 | 160 | 193 | 842 | -399 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 384 | 272 |
| C10S1_6J_48 | LONDON | 134 | 1.79 | 29.8 | 33.7 | 2.48 | 0.61 | 56.0 | -10.2 | -11.3 | -6.83 | -35.0 | -24.8 | 18.1 | 9.86 | -6.83 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 5.76 | 80 |
| C10S1_NQ_79 | NY-AM | 118 | 1.57 | 626 | 713 | 2.46 | 0.61 | 39.0 | 464 | 342 | 1294 | 17.5 | -64.8 | 314 | 899 | 1294 | SESSION-CANDIDATE |  | BOF:not cleared | 71.7 | 285 |
| C10S1_GC_40 | ASIA | 176 | 2.35 | 380 | 436 | 2.44 | 0.39 | 61.0 | 394 | 67.5 | 1597 | 1.11 | -14.2 | 315 | 282 | 1597 | SESSION-CANDIDATE |  | BOF:not cleared | 159 | 227 |
| C10S1_GC_0 | ASIA | 237 | 3.16 | 221 | 261 | 2.38 | 0.32 | 91.0 | 687 | 166 | 2957 | 69.4 | 79.2 | 166 | 231 | 2957 | SESSION-CANDIDATE |  | BOF:not cleared | 95.2 | 196 |
| C10S1_ES_54 | NY-AM | 100 | 1.33 | 301 | 363 | 2.32 | 0.58 | 53.0 | 319 | 275 | 507 | -47.8 | 0.28 | -16.2 | 518 | 507 | SESSION-CANDIDATE |  | BOF:not cleared | 140 | 172 |
| C10S1_GC_60 | ASIA | 220 | 2.93 | 264 | 319 | 2.32 | 0.40 | 103 | 837 | 278 | 3156 | -30.6 | -2.95 | 142 | 335 | 3156 | SESSION-CANDIDATE |  | BOF:not cleared | 67.7 | 247 |
| C10S1_GC_340 | ASIA | 101 | 1.35 | 579 | 710 | 2.28 | 0.49 | 40.0 | 286 | 398 | -498 | 216 | 147 | 688 | 399 | -498 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 188 | 219 |
| C10S1_ES_98 | NY | 192 | 2.56 | 256 | 316 | 2.27 | 0.55 | 77.0 | 227 | 189 | 484 | -71.9 | -68.0 | 324 | 129 | 484 | SESSION-CANDIDATE |  | BOF:not cleared | 125 | 195 |
| C10S1_6J_12 | ASIA | 173 | 2.31 | 48.8 | 60.3 | 2.27 | 0.62 | 97.0 | -42.9 | -36.7 | -74.0 | -19.8 | -27.3 | 54.6 | -2.91 | -74.0 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 8.71 | 45 |
| C10S1_6J_64 | LONDON | 200 | 2.67 | 43.8 | 58.3 | 2.10 | 0.43 | 90.0 | 30.2 | 18.3 | 95.2 | -32.0 | -30.8 | 65.3 | 2.21 | 95.2 | SESSION-CANDIDATE |  | BOF:not cleared | -1.84 | 103 |
| C10S1_NQ_282 | NY | 129 | 1.72 | 455 | 620 | 2.05 | 0.53 | 65.0 | 846 | 837 | 898 | 234 | 270 | 352 | 710 | 898 | SESSION-CANDIDATE |  | BOF:not cleared | 106 | 264 |
| C10S1_GC_140 | ASIA | 333 | 4.44 | 180 | 246 | 2.05 | 0.35 | 143 | 103 | -58.0 | 1091 | 41.4 | 50.9 | 113 | 104 | 1091 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 63.5 | 201 |
| C10S1_GC_100 | ASIA | 116 | 1.55 | 367 | 509 | 2.02 | 0.45 | 48.0 | 80.0 | -489 | 4061 | 195 | 184 | 383 | -64.7 | 4061 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 137 | 198 |
| C10S1_CL_149 | LONDON | 128 | 1.71 | 60.8 | 87.8 | 1.94 | 0.59 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 20.8 | 112 |
| C10S1_NQ_144 | ASIA | 230 | 3.07 | 308 | 448 | 1.93 | 0.43 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 91.1 | 253 |
| C10S1_NQ_8 | ASIA | 117 | 1.56 | 303 | 444 | 1.91 | 0.61 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -13.5 | 250 |
| C10S1_NQ_240 | NY | 103 | 1.37 | 473 | 730 | 1.81 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 22.8 | 262 |
| C10S1_GC_150 | NY-AM | 100 | 1.33 | 135 | 209 | 1.81 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 72.5 | 202 |
| C10S1_ES_144 | ASIA | 222 | 2.96 | 154 | 240 | 1.80 | 0.40 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 13.0 | 153 |
| C10S1_ES_13 | NY | 112 | 1.49 | 208 | 330 | 1.76 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -8.58 | 150 |
| C10S1_6J_112 | ASIA | 150 | 2.00 | 43.7 | 69.6 | 1.76 | 0.59 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 17.1 | 47 |
| C10S1_6J_88 | LONDON | 125 | 1.67 | 26.9 | 44.8 | 1.68 | 0.58 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -3.02 | 105 |
| C10S1_CL_1 | LONDON | 133 | 1.77 | 117 | 195 | 1.67 | 0.39 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 35.6 | 106 |
| C10S1_ES_150 | NY | 211 | 2.81 | 82.1 | 139 | 1.65 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 60.3 | 154 |
| C10S1_ES_298 | NY | 109 | 1.45 | 213 | 366 | 1.63 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 32.9 | 164 |
| C10S1_6J_200 | LONDON | 109 | 1.45 | 55.0 | 99.4 | 1.55 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 6.53 | 60 |


## 5. Dead pooled, alive in a session
29 cell-sessions (23 cells, 16 independent). Top 30:
| cid | session | n | tpw | mean | mde | t | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | bof_label | label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C10S1_ES_78 | NY | 217 | 2.89 | 277 | 261 | 2.98 | 90.0 | 231 | 170 | 595 | 40.9 | 103 | 234 | 189 | 595 | SESSION-CANDIDATE | BOF:not cleared | C10S1_ES/30_st_10_2_time_8_day_0|F-HOLD (holdout <=0) | 120 | 194 |
| C10S1_ES_274 | NY-AM | 113 | 1.51 | 415 | 442 | 2.63 | 50.0 | 365 | 258 | 701 | 123 | 105 | 174 | 565 | 701 | SESSION-CANDIDATE | BOF:not cleared | C10S1_ES/60_st_10_2_brk_3.0_day_0|F-X (2023-04..2024-01 <=0) | 207 | 163 |
| C10S1_ES_77 | NY-AM | 100 | 1.33 | 384 | 425 | 2.53 | 47.0 | 351 | 320 | 564 | 78.4 | 103 | 136 | 575 | 564 | SESSION-CANDIDATE | BOF:not cleared | C10S1_ES/30_st_10_2_time_8_all_1|F-HOLD (holdout <=0) | 97.7 | 194 |
| C10S1_NQ_79 | NY-AM | 118 | 1.57 | 626 | 713 | 2.46 | 39.0 | 464 | 342 | 1294 | 17.5 | -64.8 | 314 | 899 | 1294 | SESSION-CANDIDATE | BOF:not cleared | C10S1_NQ/30_st_10_2_time_8_day_1|F-HOLD (holdout <=0) | 71.7 | 285 |
| C10S1_GC_0 | ASIA | 237 | 3.16 | 221 | 261 | 2.38 | 91.0 | 687 | 166 | 2957 | 69.4 | 79.2 | 166 | 231 | 2957 | SESSION-CANDIDATE | BOF:not cleared | C10S1_GC/30_ema_9_21_opp_0_all_0|F-X (2023-04..2024-01 <=0) | 95.2 | 196 |
| C10S1_ES_54 | NY-AM | 100 | 1.33 | 301 | 363 | 2.32 | 53.0 | 319 | 275 | 507 | -47.8 | 0.28 | -16.2 | 518 | 507 | SESSION-CANDIDATE | BOF:not cleared | C10S1_ES/30_macd_12_26_brk_3.0_day_0|F-HOLD (holdout <=0) | 140 | 172 |
| C10S1_GC_60 | ASIA | 220 | 2.93 | 264 | 319 | 2.32 | 103 | 837 | 278 | 3156 | -30.6 | -2.95 | 142 | 335 | 3156 | SESSION-CANDIDATE | BOF:not cleared | C10S1_GC/30_st_10_2_opp_0_all_0|F-X (2023-04..2024-01 <=0) | 67.7 | 247 |
| C10S1_ES_98 | NY | 192 | 2.56 | 256 | 316 | 2.27 | 77.0 | 227 | 189 | 484 | -71.9 | -68.0 | 324 | 129 | 484 | SESSION-CANDIDATE | BOF:not cleared | C10S1_ES/30_st_14_3_time_8_day_0|F-HOLD (holdout <=0) | 125 | 195 |
| C10S1_NQ_42 | NY-AM | 128 | 1.71 | 866 | 1071 | 2.26 | 60.0 | 578 | 541 | 821 | 349 | 402 | 538 | 950 | 821 | SESSION-CANDIDATE | BOF:not cleared | C10S1_NQ/30_macd_12_26_opp_0_day_0|F-HOLD (holdout <=0) | 293 | 272 |
| C10S1_NQ_42 | NY | 209 | 2.79 | 597 | 741 | 2.26 | 87.0 | 423 | 439 | 311 | 188 | 200 | 284 | 832 | 311 | SESSION-CANDIDATE | BOF:not cleared | C10S1_NQ/30_macd_12_26_opp_0_day_0|F-HOLD (holdout <=0) | 293 | 272 |
| C10S1_ES_274 | NY | 180 | 2.40 | 319 | 403 | 2.21 | 71.0 | 324 | 220 | 746 | 13.3 | 1.29 | 173 | 403 | 746 | SESSION-CANDIDATE | BOF:not cleared | C10S1_ES/60_st_10_2_brk_3.0_day_0|F-X (2023-04..2024-01 <=0) | 207 | 163 |
| C10S1_ES_54 | NY | 175 | 2.33 | 235 | 308 | 2.14 | 78.0 | 189 | 154 | 377 | -148 | -113 | -10.5 | 395 | 377 | SESSION-CANDIDATE | BOF:not cleared | C10S1_ES/30_macd_12_26_brk_3.0_day_0|F-HOLD (holdout <=0) | 140 | 172 |
| C10S1_6J_64 | LONDON | 200 | 2.67 | 43.8 | 58.3 | 2.10 | 90.0 | 30.2 | 18.3 | 95.2 | -32.0 | -30.8 | 65.3 | 2.21 | 95.2 | SESSION-CANDIDATE | BOF:not cleared | C10S1_6J/30_st_10_2_trail_2.5_all_0|F-HOLD (holdout <=0) | -1.84 | 103 |
| C10S1_ES_98 | NY-AM | 128 | 1.71 | 236 | 314 | 2.10 | 57.0 | 332 | 299 | 484 | 36.8 | 30.7 | 257 | 241 | 484 | SESSION-CANDIDATE | BOF:not cleared | C10S1_ES/30_st_14_3_time_8_day_0|F-HOLD (holdout <=0) | 125 | 195 |
| C10S1_NQ_280 | NY | 129 | 1.72 | 455 | 620 | 2.05 | 65.0 | 846 | 837 | 898 | 234 | 270 | 352 | 710 | 898 | SESSION-CANDIDATE | BOF:not cleared | C10S1_NQ/60_st_14_3_opp_0_all_0|F-HOLD (holdout <=0) | -57.2 | 264 |
| C10S1_6J_5 | LONDON | 100 | 1.33 | 49.9 | 69.6 | 2.01 | 41.0 | 81.3 | 45.5 | 229 | -60.1 | -35.6 | 27.2 | 43.9 | 229 | SESSION-CANDIDATE | BOF:not cleared | C10S1_6J/30_ema_9_21_trail_2.5_all_1|F-HOLD (holdout <=0) | 11.2 | 45 |

