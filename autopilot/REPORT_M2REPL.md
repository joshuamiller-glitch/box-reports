# REPORT M2-REPL - independent replication of the six METHOD-2 single-family passers (pre-registered in PREREG_AUTOPILOT.md BLOCK 'M2-REPL' before any cell below was read)

## 1. Same-bet map (OOS correlation, METHOD-2 12/3/3 tilt OOS series)

| | BM13_NQ | BM11_NQ | BM12_NQ | BM8_RTY | Q37_RTY | BI8_YM |
|---|---|---|---|---|---|---|
| BM13_NQ | 1 | 0.54 | 0.61 | 0.03 | 0.03 | -0.04 |
| BM11_NQ | 0.54 | 1 | 0.81 | 0.00 | 0.03 | 0.01 |
| BM12_NQ | 0.61 | 0.81 | 1 | 0.05 | 0.00 | -0.08 |
| BM8_RTY | 0.03 | 0.00 | 0.05 | 1 | 0.06 | -0.01 |
| Q37_RTY | 0.03 | 0.03 | 0.00 | 0.06 | 1 | 0.04 |
| BI8_YM | -0.04 | 0.01 | -0.08 | -0.01 | 0.04 | 1 |

**Four independent bets:** (1) BM13_NQ + BM11_NQ + BM12_NQ = one late-day NQ fade of the move away from a reference price (weekly corr 0.53 / 0.58 / 0.81); (2) BM8_RTY; (3) Q37_RTY; (4) BI8_YM (|corr| < 0.2 with every other passer).

## 2. R2: shifted-clock / parameter families (METHOD-2 harness exactly as the parents; pass = gates a-d AND OOS Sharpe >= 0.5 x parent)

| family | cells | OOS Sharpe (parent) | null rank | boot lo | half 1 / half 2 net | gates a/b/c/d | OOS corr with parent | replication |
|---|---|---|---|---|---|---|---|---|
| BM12S_NQ | 24 | 0.89 (1.28) | 0.930 | +0.002 | 26.5 / 5.2 | 1011 | 0.88 | **FAIL** |
| BM13S_NQ | 12 | 1.12 (1.77) | 0.970 | +0.060 | 44.0 / 12.3 | 1111 | 0.59 | **PASS** |
| BM8S_RTY | 12 | 1.07 (1.32) | 0.955 | +0.013 | 11.6 / 18.6 | 1111 | 0.63 | **PASS** |
| BI8S_YM | 18 | -0.39 (1.10) | 0.370 | -0.842 | -36.3 / 5.7 | 0 | 0.05 | **FAIL** |
| Q37S_RTY | 16 | 1.00 (1.24) | 0.945 | -0.015 | 9.5 / 21.7 | 1001 | 0.56 | **FAIL** |

Reading: BM13S (entry 15:10 / 15:30, vwap references) and BM8S (up-day-fraction lookbacks 7/15/30 on RTY) replicate; BM12S (the 12-cell parent grid at shifted clocks) narrowly fails (null rank 0.93 < 0.95, OOS Sharpe 0.89 = 70% of the parent); Q37S narrowly fails (null rank 0.945, bootstrap lower bound -0.015); BI8S fails clearly (OOS Sharpe -0.39: the YM range-shock drift does not survive different range multiples). The S families share the sample window with their parents and are correlated with them (0.59 / 0.63 / 0.88 / 0.56 / 0.05), so these are robustness-to-parameter tests, not new calendar time; chance expectation for five S families was 0.09 passes (about 1.7% each), so two passes are above chance, but both are weaker than their parents (1.12 vs 1.77, 1.07 vs 1.32).

Sibling evidence already read (not independent): BM13 on ES/RTY/YM -0.55/-0.20/-0.61, BM12 +0.32/+0.53/+0.35, BM11 ES +0.24 RTY -0.18 YM -0.87, BM8 ES -0.85 NQ -0.50 YM +0.58, Q37 ES -0.42 NQ -1.30, BI8 ES +0.19 NQ +0.39 RTY +0.48: the NQ-only late-day reversion does not transfer to the other indices (BM13), while BM12 and BI8 show weak same-sign results.

## 3. R1 forward test (the only genuinely independent read)

Weights frozen (outputs/methods2/repl/M2-REPL_weights_<family>.csv; cells with positive tilt weight: BM13 4 of 6, BM11 3 of 8, BM12 8 of 12, BM8 5 of 12, Q37 4 of 8, BI8 6 of 12). Evaluator: code/census/night_ins/ap_m2_repl_forward.py (rebuilds the matrices to the latest data, applies the frozen weights to the weeks after 2026-10-16, applies the registered decision rule: PASS at 52 weeks z >= 1.64 and net > 0, early PASS at 26 weeks z >= 2.33, KILL at 26 weeks z <= -1.0), log outputs/methods2/repl/M2-REPL_forward_log.csv. At write time there are 0 forward weeks.

DONE M2-REPL (pre-registration, R2 and R1 set-up)
