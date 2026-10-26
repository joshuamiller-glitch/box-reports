# DS3_TA - T-A survivors re-scored as DS3 books (D3A, 2026-10-26)

Prereg `l2vast/ds3/prereg/T-A_prereg.md` sha256 `09c68b514ee3b5567be78bb05f0a2cee9d8a915d4850816e7311e43c88017be8` (22 cells; DECISIONS.md and ledger/trials.jsonl track DS3_TA appended; cumulative 28,588 before this track's cells were added to the total shown by s48score). Pre-holdout text `autopilot/DS3_TA_PREHOLD.md` (WF-PRE only); the holdout (2025-07+) and the second holdout (2023-04..2024-01) were looked at once together, logged (`holdout_looks.jsonl`, track DS3_TA). Code `l2vast/ds3/code/ta_*.py`; rows `l2vast/ds3/rows/DS3_TA.json`; per-cell daily series (per-lot, aligned to s48score.DAYS) `l2vast/ds3/out/T-A/<cell>.parquet`; raw scores `out/T-A/scores_*.json`, `mapped_wt.json`, `corr_WF_3lots.csv`.

## 0. Answer
**0 PASS, 0 CANDIDATE, 22 DEAD of 22 cells.** Nothing is registered to paper_all (no PASS/CANDIDATE); no 3x3 grid is owed (addendum 2 applies only after a PASS). The DS3 bar is what kills them, not the sign of the P&L: most books are positive at live cost in WF and holdout.
- Dip-buy family (NQ RSI2C, ES RSI2, one-exposure book, IBS, plain RSI2): standalone WF, holdout and 2023-04..2024-01 all positive, marginal Sharpe up in the DS2 pool, corr with DS2 ~0, library placebo 0.99-1.0, identity test 0/312 and 0/301 mismatches (D3X). They fail **trades/wk (0.4-0.9 < 3: forward-unmeasurable)** and the **own-timing shift placebo (0.64-0.92 < 0.95)**: two failures = DEAD under "CANDIDATE = all but one". The one-exposure book (3 NQ + 3 ES per signal) is the best of the survivors: +4,604/wk at 3 lots, CI [2,994, 7,174], 0.92 trades/wk, DSR 0.65 (not corrected-significant). It stays a PAPER-ALL sleeve (already registered `DIPBUY_RSI2_2lot`), not a DS3 book. Even adding IBS + ORB + GSHORT frequencies does not reach 3 trades/wk (~2.5 combined).
- Overnight drift unfiltered (ON_none): scorer reading CANDIDATE (+3,537/wk at 3 lots, 4.67 trades/wk, holdout +, span +, marginal Sharpe +0.14, but placebo 0.92 library / 0.76 shift and CI [-207, 7,530] includes 0). Verdict of record **DEAD**, as the prior record says: 2013-2023 placebo .29-.32, drift-matched .22; the standalone sign is NQ's long bias.
- ORB Asia (s60, s75, 30-min): at 2-4 lots they earn only +480 to +1,130/wk, 0.8 trades/wk, and the 2023-04..2024-01 span is **negative** (-516 to -941/wk at 3 lots). The 0.25 ratio equals 14-17 extra lots (not 2-4).
- WT variants: the library series (fixed 60-60 bracket, 1 tick/side) read CANDIDATE (+4.4-4.9k/wk at 3 lots), but that basis omits the P9 live mapping (about $37 per lot-trade, fitted from library WT7 vs the DS2 WT book, 38 trades/wk). On the live mapped basis all three are DEAD: WT_LIVE (the DS2 WT book itself, per-book locks) +616/wk at 3 lots, CI [-1,360, 2,643], marginal Sharpe down; WThist ATR20/2.0 +183/wk, span -3,985; WThist ATR10 m3 tf10 (assembly top-5 cell) +758/wk, holdout -12, placebo 0.79/0.56. The mapping for tf10 is a haircut estimate, not a P9 re-run; flagged.
- GSHORT_t90: NOT DELIVERABLE standalone (the gate reads DS2's realised 4-week P&L), 0.22 trades/wk, span negative: cannot be PASS.
- S130_ES: NOT DELIVERABLE (L2 depth features at runtime, JOIN limit orders on real L2); no independent holdout (fit window includes it); tier LEAD, best-of-F 0.45. Not scored numerically.
- MBO seven: NOT DELIVERABLE (order-book features + ML inference; stays on the execution server). For the record, composite 1-NQ-per-setup scaled to 3 lots: WF +1,679/wk (CI [402, 3,280]), holdout +630 (holdout ends 2026-02-06, 8 months), span +550, 22 trades/wk, DSR 0.11, placebo 0.97/0.76; two setups have negative holdout.

## 1. Table (WF 2024-02..2026-10, 142 weeks, 3 lots of record; mean for 2/3/4 lots; $ per week)
Columns: cell | NT8 exec | trades/wk | WF mean at 2/3/4 lots | SD (3) | maxDD (3, daily path) | worst week (3) | Sharpe (3) | block-bootstrap CI of mean (3) | holdout mean 2025-07+ at 2/3/4 | 2023-04..2024-01 mean (3) | marginal Sharpe vs DS2 books (3) | placebo library/shift | corr with DS2 | DSR | verdict. WT rows use the mapped live basis.

| cell | exec | tr/wk | WF mean 2/3/4 | SD | maxDD | worst | Sharpe | CI | HOLD 2/3/4 | span23 | marg Sh | plc lib/shift | corr DS2 | DSR | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ_RSI2C_s20 | DEL | 0.49 | 1764 / 2646 / 3528 | 13086 | 149565 | -52155 | 1.46 | [1438,4731] | 2131 / 3196 / 4262 | 341 | 0.170 | 0.99/0.86 | -0.02 | 0.48 | DEAD |
| ES_RSI2_t10 | DEL | 0.42 | 1305 / 1958 / 2610 | 8147 | 65781 | -45592 | 1.73 | [1137,2960] | 1508 / 2263 / 3017 | 629 | 0.115 | 0.99/0.92 | 0.08 | 0.66 | DEAD |
| DIPBUY_ONE | DEL | 0.92 | 3069 / 4604 / 6139 | 19191 | 207130 | -97747 | 1.73 | [2994,7174] | 3639 / 5459 / 7279 | 970 | 0.271 | 1.00/0.86 | 0.02 | 0.65 | DEAD |
| NQ_IBS_t20_n1 | DEL | 0.75 | 2027 / 3040 / 4053 | 18769 | 86554 | -69929 | 1.17 | [1157,5606] | 2627 / 3941 / 5254 | 2418 | 0.210 | 0.99/0.64 | -0.10 | 0.28 | DEAD |
| NQ_RSI2_t10_plain | DEL | 0.49 | 2011 / 3016 / 4021 | 15458 | 100765 | -62429 | 1.41 | [1688,5192] | 2167 / 3251 / 4335 | 341 | 0.188 | 0.99/0.83 | -0.01 | 0.44 | DEAD |
| NQ_ON_none | DEL | 4.67 | 2358 / 3537 / 4716 | 24726 | 254086 | -125203 | 1.03 | [-207,7530] | 3132 / 4698 / 6264 | 1595 | 0.143 | 0.92/0.76 | 0.11 | 0.25 | DEAD |
| GSHORT_t90 | NOT | 0.22 | 324 / 486 / 649 | 4279 | 30298 | -21778 | 0.82 | [-297,1417] | 429 / 644 / 858 | -342 | 0.030 | 0.94/0.83 | 0.02 | 0.14 | DEAD |
| ORB_ASIA_15_s60 | DEL | 0.84 | 481 / 722 / 962 | 4227 | 30431 | -7470 | 1.23 | [37,1363] | 724 / 1086 / 1448 | -516 | 0.032 | 0.93/0.99 | 0.21 | 0.33 | DEAD |
| ORB_ASIA_15_s75 | DEL | 0.84 | 565 / 848 / 1131 | 4956 | 36822 | -9270 | 1.23 | [-10,1605] | 1074 / 1611 / 2149 | -925 | 0.042 | 0.96/1.00 | 0.16 | 0.34 | DEAD |
| ORB_ASIA_30_s60 | DEL | 0.81 | 479 / 719 / 958 | 4443 | 25106 | -11204 | 1.17 | [50,1353] | 797 / 1196 / 1594 | -941 | 0.037 | 0.96/0.97 | 0.14 | 0.29 | DEAD |
| WT_LIVE_ATR20_2.0 | DEL | 38.20 | 411 / 616 / 822 | 11893 | 104917 | -28308 | 0.37 | [-1360,2643] | 225 / 337 / 449 | 554 | -0.075 | 0.39/0.51 | 0.52 | 0.83 | DEAD |
| WThist_ATR20_m2_ema100_tf1 | DEL | 38.20 | 122 / 183 / 244 | 17554 | 166436 | -32402 | 0.08 | [-2899,3131] | 244 / 367 / 489 | -3985 | -0.133 | 0.39/1.00 | 0.49 | 0.69 | DEAD |
| WThist_ATR10_m3_ema0_tf10 | DEL | 12.27 | 505 / 758 / 1011 | 10824 | 99885 | -27467 | 0.51 | [-1066,2487] | -8 / -12 / -16 | 1697 | 0.035 | 0.79/0.56 | 0.03 | 0.46 | DEAD |
| MBO7_composite | NOT | 22.23 | 1119 / 1679 / 2238 | 13939 | 96968 | -65088 | 0.87 | [402,3280] | 420 / 630 / 840 | 550 | 0.111 | 0.97/0.76 | -0.05 | 0.11 | DEAD |
| MBO7_H120000_competing_dir_xgboost_Q725 | NOT | 1.97 | 1316 / 1974 / 2633 | 18956 | 114267 | -96270 | 0.75 | [-239,4425] | 69 / 103 / 138 | 863 | 0.087 | 0.85/0.58 | 0.06 | 0.09 | DEAD |
| MBO7_H250_tb_long_xgboost_Q750 | NOT | 2.78 | 523 / 784 / 1046 | 19836 | 326220 | -74592 | 0.29 | [-1821,3219] | 462 / 692 / 923 | 1439 | 0.038 | 0.80/0.38 | -0.05 | 0.02 | DEAD |
| MBO7_H300000_competing_dir_extratrees_Q575 | NOT | 4.47 | 1071 / 1606 / 2141 | 19050 | 235719 | -78993 | 0.61 | [-1151,4470] | 2486 / 3729 / 4973 | 1278 | 0.120 | 0.92/0.46 | -0.12 | 0.08 | DEAD |
| MBO7_H300000_competing_dir_histgb_Q700 | NOT | 3.19 | 833 / 1249 / 1666 | 9949 | 77565 | -30288 | 0.91 | [-331,2678] | 124 / 186 / 248 | -38 | 0.096 | 0.97/0.74 | -0.12 | 0.15 | DEAD |
| MBO7_H60000_competing_dir_histgb_Q675 | NOT | 1.87 | 1700 / 2550 / 3399 | 19202 | 53529 | -48273 | 0.96 | [-173,6565] | -184 / -277 / -369 | 269 | 0.146 | 0.97/0.59 | -0.01 | 0.07 | DEAD |
| MBO7_H60000_y_exec_best_catboost_Q625 | NOT | 5.23 | 1409 / 2114 / 2818 | 18805 | 226338 | -88362 | 0.81 | [-1119,4968] | -91 / -136 / -182 | 440 | 0.148 | 0.96/0.61 | -0.10 | 0.15 | DEAD |
| MBO7_H60000_y_exec_best_lightgbm_Q700 | NOT | 2.72 | 982 / 1473 / 1964 | 18046 | 145677 | -94380 | 0.59 | [-178,3786] | 76 / 114 / 152 | -398 | 0.070 | 0.83/0.99 | 0.01 | 0.05 | DEAD |

Lots are real contracts (NQ, ES lots; one-exposure book = N NQ + N ES; MBO and library books scale the 8-contract engine by L/8; ORB scales the 14-lot unit). Costs: live (4.84 RT + 1 tick/side for 1-min books; ORB on the 1-s tape at stop-join 1.01 pt; library WT shown at its stored 1 tick/side, then mapped; MBO stored MNQ-equivalent). Win rates and per-trade stats are in the rows file (`win_rate`, `avg_win_per_lot`) only where trade lists exist; WF win rate NQ RSI2C about 59%, ES RSI2 68% (SLEEVE_RSI2_SPEC).

Marginal Sharpe = WF change in annualised weekly Sharpe of the DS2 books (ST10 + HM10 + WT7, per-book locks, D3C `DS2_daily.parquet`) when the book is added; the D3C `pool.parquet` was not yet on disk when scored, so the final within-DS3 leave-one-out is T-G's job using `out/T-A/*.parquet`. Placebo: 500 random books from the 33,849-series library universe scaled to the candidate's weekly SD (marginal-Sharpe gain), and 500 circular shifts of its own series (WF mean); the rank of record is the minimum (stricter than the directive's library-only reading; the library rank alone would give dip-buy 0.99-1.0).

## 2. Power (MDE)
Standalone weekly MDE at 80% power = 2.8 x SD / sqrt(142): at 3 lots about 1.0k/wk (RSI2C), 1.9k (one-exposure), 2.0k (ES+IBS range 1.9-2.4k), 2.9k (ON_none), 0.5k (ORB), 3.3k (WT), 3.3k (MBO7). The dip-buy effects (2-5k at 3 lots) exceed their MDE on WF, but 56-139 trades and DSR 0.1-0.65 (prior 28.5k trials) mean the discovery is not corrected-significant. A forward test needs about 135 weeks to detect the expected mean at 0.5 signals/wk, hence the 3 trades/wk bar.

## 3. Executability (NT8 chart data; identity test = D3X)
- **TA_NQ_RSI2C_s20** (DELIVERABLE): 1-min NQ bars; series of the 15:55:00 ET bar open per label day (ET+6h day); RSI(2) Wilder-style weight 1/2 on those opens; signal RSI2<10 -> market buy at close of the 15:55 bar (~15:56 ET); protective sell stop at entry-2.0*ATR14(daily label-day TR, Wilder, prior completed day); time exit market at 15:56 ET next trading day with a 15:55 bar; roll: skip if a roll falls inside the hold. Session 15:55 ET to 15:56 ET next day. Order types: market, stop-market. Identity: D3X x_validate_rsi2.json 0/312 mismatches.
- **TA_ES_RSI2_t10** (DELIVERABLE): Same rule on 1-min ES bars, no stop; market in at 15:56 ET, market out 15:56 ET next day. Identity: D3X 0/301 mismatches.
- **TA_DIPBUY_ONE** (DELIVERABLE): The two legs above in one strategy (NQ and ES charts, multi-instrument NT8 strategy or two strategies sharing a risk lock); same orders.
- **TA_NQ_IBS_t20_n1** (DELIVERABLE): 1-min NQ bars; IBS=(close-low)/(high-low) of the label-day bar built from 1-min bars to 15:55 ET; IBS<0.20 -> market buy at 15:56 ET, market exit 15:56 ET next day (n1 = 1 day hold). Identity test not yet run (D3X).
- **TA_NQ_RSI2_t10_plain** (DELIVERABLE): As RSI2C without the stop; market in/out at 15:56 ET. Identity not yet run.
- **TA_NQ_ON_none** (DELIVERABLE): 1-min NQ; market buy every trading day at the 15:55 bar close (15:56 ET), market sell at 09:30 ET next session open (Fri -> Mon 09:30 ET not held: library holds to next 09:30); roll-skipped. Identity not yet run.
- **TA_GSHORT_t90** (NOT DELIVERABLE): Rule is RSI2>90 on NQ at 15:55 ET gated on Set A being in a weak trailing 4-week stretch (DS2 realised P&L): a DS3 strategy cannot read DS2's realised P&L in NT8 without cross-strategy shared state. The ungated RSI2>90 short is a different, unscored cell.
- **TA_ORB_ASIA_15_s60** (DELIVERABLE): 1-min (or tick) NQ bars; opening range = first 15 min after the 18:00 ET session open; trade only if OR volume >= 1.5 x its 20-day mean; buy-stop above / sell-short-stop below the OR extreme, one trade per night; OCO bracket stop 60 pts, target 90 pts; window 18:00-02:59 ET entries; flat by 04:30 ET; order types stop-market entry, stop-market stop, limit target. Library engine is 1-s tape (stop-join fills 1.01 pt): NT8 chart data sufficient (tick bars for fills), identity test must be run on 1-s/tick data (D3X pending).
- **TA_ORB_ASIA_15_s75** (DELIVERABLE): As ORB_ASIA_15 with a 75-pt stop, 90-pt target. Identity pending.
- **TA_ORB_ASIA_30_s60** (DELIVERABLE): As ORB_ASIA_15 with a 30-min opening range, 60-pt stop. Identity pending.
- **TA_WT_LIVE_ATR20_2.0** (DELIVERABLE): The chart WTStrat: 1-min NQ bars; Wilder ATR(20) x 2.0 ratchet trail on close, flip on cross; EMA100 filter; bracket stop 45 / target 33.75 (library variant: 60/60 fixed bracket, no Trade Health); flat 16:55 ET. Already live in DualStrat2 (WT7).
- **TA_WThist_ATR20_m2_ema100_tf1** (DELIVERABLE): Same as WT_LIVE on 2013-2026 history, 60-60 bracket.
- **TA_WThist_ATR10_m3_ema0_tf10** (DELIVERABLE): 10-minute NQ time bars; Wilder ATR(10) x 3.0 close-based ratchet-trail flip; no EMA filter; bracket 60/60; flat 16:55 ET; market entry at next bar open, stop and limit exits.
- **TA_MBO7_composite** (NOT DELIVERABLE): MBO order-book features (order-by-order book) plus ML inference at runtime; NT8 has no MBO feed in chart data. Stays on the execution server.
- **TA_MBO7_H120000_competing_dir_xgboost_Q725** (NOT DELIVERABLE): MBO order-book features (order-by-order book) plus ML inference at runtime; NT8 has no MBO feed in chart data. Stays on the execution server.
- **TA_MBO7_H250_tb_long_xgboost_Q750** (NOT DELIVERABLE): MBO order-book features (order-by-order book) plus ML inference at runtime; NT8 has no MBO feed in chart data. Stays on the execution server.
- **TA_MBO7_H300000_competing_dir_extratrees_Q575** (NOT DELIVERABLE): MBO order-book features (order-by-order book) plus ML inference at runtime; NT8 has no MBO feed in chart data. Stays on the execution server.
- **TA_MBO7_H300000_competing_dir_histgb_Q700** (NOT DELIVERABLE): MBO order-book features (order-by-order book) plus ML inference at runtime; NT8 has no MBO feed in chart data. Stays on the execution server.
- **TA_MBO7_H60000_competing_dir_histgb_Q675** (NOT DELIVERABLE): MBO order-book features (order-by-order book) plus ML inference at runtime; NT8 has no MBO feed in chart data. Stays on the execution server.
- **TA_MBO7_H60000_y_exec_best_catboost_Q625** (NOT DELIVERABLE): MBO order-book features (order-by-order book) plus ML inference at runtime; NT8 has no MBO feed in chart data. Stays on the execution server.
- **TA_MBO7_H60000_y_exec_best_lightgbm_Q700** (NOT DELIVERABLE): MBO order-book features (order-by-order book) plus ML inference at runtime; NT8 has no MBO feed in chart data. Stays on the execution server.
- **TA_S130_ES** (NOT DELIVERABLE): Depth (L2) features at runtime and JOIN limit orders; 29-cell L2-replay book
Identity status: RSI2C_s20 and ES_RSI2_t10 verified (0 mismatches, D3X `x_validate_rsi2.json`). Others pending D3X; ORB must be replayed on 1-s/tick bars.

## 4. Per-cell notes
- TA_NQ_RSI2C_s20: Scorer: fails trades/wk (0.49 < 3: forward-unmeasurable) and timing-shift placebo 0.86 (library placebo 0.99). Strongest family: holdout +, 2023-04..2024-01 +, marginal Sharpe +, corr DS2 ~0, identity test 0/312 mismatches. DEAD by the DS3 bar; keep as PAPER-ALL sleeve (already registered DIPBUY_RSI2_2lot).
- TA_ES_RSI2_t10: Fails trades/wk (0.42) and shift placebo 0.92 (<0.95). Identity 0/301 mismatches.
- TA_DIPBUY_ONE: NQ+ES one exposure (leg corr 0.61): 0.92 trades/wk, shift placebo 0.86. Best low-frequency book; DEAD by the DS3 bar on measurability + placebo. Already forward-registered as DIPBUY_RSI2_2lot.
- TA_NQ_IBS_t20_n1: Fails trades/wk (0.75) and shift placebo 0.64.
- TA_NQ_RSI2_t10_plain: Fails trades/wk (0.49) and shift placebo 0.83 (corr 0.95 with RSI2C: same exposure).
- TA_NQ_ON_none: Scorer reading CANDIDATE (only placebo 0.76 shift / 0.92 library fails). VERDICT OF RECORD DEAD: prior 2013-2023 placebo .29-.32 and drift-matched .22 (NQ long bias) - the mechanism-matched placebo fails; CI of WF mean includes 0. Re-scored honestly as a DS3 candidate: standalone numbers are positive only because NQ drifts up.
- TA_GSHORT_t90: NOT DELIVERABLE standalone (gate = DS2 realised P&L), 0.22 trades/wk (31-44 trades), 2023-04..2024-01 negative, CI includes 0.
- TA_ORB_ASIA_15_s60: 0.84 trades/wk, 2023-04..2024-01 negative (-516/wk at 3 lots), library placebo 0.93. At ratio 0.25 the sleeve was ~17 lots; at 2-4 lots it earns a few hundred $/wk, lot-limited.
- TA_ORB_ASIA_15_s75: 0.84 trades/wk, 2023-04..2024-01 negative; corr 0.87 with the s60 stop variant (one exposure).
- TA_ORB_ASIA_30_s60: 0.81 trades/wk, 2023-04..2024-01 negative.
- TA_WT_LIVE_ATR20_2.0: Library (fixed 60-60 bracket, 1 tick/side) reads CANDIDATE, but that basis omits the P9 live mapping (~$37 per lot-trade x 38 trades/wk). On the live mapped basis (DS2 WT book, per-book locks): WF +616/wk at 3 lots, CI [-1360, 2643], marginal Sharpe down, placebo 0.39/0.51 -> DEAD.
- TA_WThist_ATR20_m2_ema100_tf1: Same signal family, long history: library basis CANDIDATE, mapped basis +183/wk, 2023-04..2024-01 -3,985/wk, marginal Sharpe down -> DEAD.
- TA_WThist_ATR10_m3_ema0_tf10: Assembly top-5 cell. Library basis CANDIDATE (hold +1,450, span +2,733); mapped (12.3 trades/wk x $37/lot-trade haircut): WF +758, hold -12, placebo 0.79/0.56, CI [-1066, 2487] -> DEAD. Identity test not run.
- TA_MBO7_composite: MBO: NOT DELIVERABLE (MBO feed + ML inference); stays on execution server. See MBO7 paper-soak.
- TA_MBO7_H120000_competing_dir_xgboost_Q725: MBO: NOT DELIVERABLE (MBO feed + ML inference); stays on execution server. See MBO7 paper-soak.
- TA_MBO7_H250_tb_long_xgboost_Q750: MBO: NOT DELIVERABLE (MBO feed + ML inference); stays on execution server. See MBO7 paper-soak.
- TA_MBO7_H300000_competing_dir_extratrees_Q575: MBO: NOT DELIVERABLE (MBO feed + ML inference); stays on execution server. See MBO7 paper-soak.
- TA_MBO7_H300000_competing_dir_histgb_Q700: MBO: NOT DELIVERABLE (MBO feed + ML inference); stays on execution server. See MBO7 paper-soak.
- TA_MBO7_H60000_competing_dir_histgb_Q675: MBO: NOT DELIVERABLE (MBO feed + ML inference); stays on execution server. See MBO7 paper-soak.
- TA_MBO7_H60000_y_exec_best_catboost_Q625: MBO: NOT DELIVERABLE (MBO feed + ML inference); stays on execution server. See MBO7 paper-soak.
- TA_MBO7_H60000_y_exec_best_lightgbm_Q700: MBO: NOT DELIVERABLE (MBO feed + ML inference); stays on execution server. See MBO7 paper-soak.
- TA_S130_ES: No chart-data rule exists; frozen fit window 2025-08..2026-07 covers the holdout so no independent holdout; tier LEAD not confirmed (best-of-F 0.45). Not scored numerically.

## 5. Caveats and looks
- One look at holdout and 2023-04..2024-01 together (logged). The second-holdout span for sleeve-export series (RSI2 etc.) lies inside the T3 IS window (2023-02..2024-01) that T3 scored at 'IS' level but never used for selection; for WT/MBO library series it was never scored.
- WT mapped haircut for the two non-DS2 WT cells is an estimate ($37/lot-trade, 12.3 trades/wk for tf10 from the stored trade list); a P9 1-s re-run of WThist ATR10/tf10 would settle it. Library WT numbers should not be read as live expectations.
- Reported size-of-record is 3 lots; 2 and 4 lots scale linearly (per-book locks are not re-run at 2-4 lots, linear scaling only).
- The directive criterion 'marginal Sharpe up within DS3' is evaluated against the DS2 books pending the D3C pool.
- Cells run: 22 (ledger appended). Sizes are variants, not cells.
