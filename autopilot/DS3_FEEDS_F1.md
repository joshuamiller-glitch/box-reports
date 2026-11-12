# DS3_FEEDS_F1 - crypto overnight gauge (F1) and prediction markets (F2)

Written 2026-11-12 20:59Z by W-FD1 (T-FEEDS). Shadow only, free sources only, no PASS claims. First-order screens on the LPB_BASE trade list (20,807 trades 2023-04..2026-10, engine lots); exact runs only for finalists (none yet).

## 0. Data owned
- Binance spot BTCUSDT and ETHUSDT 1-s klines 2023-04..2026-11-11 (free, data.binance.vision): /mnt/l2/l2vast/feeds/crypto/ (+ 1-min arrays BTCUSDT_1m.npz, ETHUSDT_1m.npz, built by code/th_feeds/f1_agg.py).
- Kalshi public API (no key): economics series for CPI / jobs / FOMC (markets + hourly candles whole life + 1-min candles last 6 h before close): /mnt/l2/l2vast/feeds/kalshi/. Polymarket (gamma + clob prices-history): /mnt/l2/l2vast/feeds/polymarket/.

## 1. F1 BTC / ETH as the overnight risk gauge: family null per subset
Cells = 14 features (BTC/ETH return in the trade direction 5/15/60/240 min, taker-flow imbalance 15 min, BTC-ETH spread, ER60, range15 and volume15 relative to the trailing day, shock15 = max 1-min move in 15 min / trailing sigma) x 6 skip thresholds (train quantiles from pre-2025-11 data). Pass = skip effect positive in L6M, HOLD and PRE. Null = 100 within-month permutations of the feature across the subset's trades.

| subset | cells | real pass | null pass mean / p95 | best worst-window gain $/wk | null best p95 | p(best) | user-lot scale |
|--|--|--|--|--|--|--|--|
| P7_asia | 84 | 3 | 0.7 / 2 | +436 | +544 | 0.11 | x1.86 |
| U7_asia | 84 | 0 | 1.5 / 4 | -22 | +235 | 0.73 | x2.50 |
| P7_all | 84 | 1 | 0.7 / 3 | +446 | +550 | 0.11 | x2.63 |
| U7_all | 84 | 2 | 1.5 / 5 | +130 | +347 | 0.34 | x2.65 |
| K7_asia | 84 | 1 | 0.4 / 2 | +136 | +73 | 0.02 | x3.33 |
| ALL_asia | 84 | 0 | 0.0 / 0 | -114 | -28 | 0.10 |  |

Passing cells (skip effect, $/wk at engine lots; negative = loses money):

| subset | feature | q | skipped | L6M | HOLD | GAP | PRE | X' | best-20-wk | worst-20-wk |
|--|--|--|--|--|--|--|--|--|--|--|
| K7_asia | eth_shock15 | 10 | 224 | +401 | +217 | -192 | +136 | -73 | +116 | +792 |
| P7_all | btc_eth_r60_dir | 10 | 413 | +898 | +446 | -1937 | +664 | -376 | -1975 | +4194 |
| P7_asia | btc_eth_r60_dir | 10 | 170 | +879 | +436 | -827 | +443 | -325 | -1083 | +2688 |
| P7_asia | btc_shock15 | 10 | 205 | +919 | +147 | -742 | +250 | -293 | -1847 | +2002 |
| P7_asia | btc_shock15 | 20 | 423 | +1206 | +115 | -170 | +19 | +566 | -3625 | +2937 |
| U7_all | btc_shock15 | 10 | 110 | +284 | +892 | -605 | +130 | -269 | -177 | +1338 |
| U7_all | btc_er60 | 20 | 257 | +792 | +63 | -1201 | +788 | -53 | -1092 | +1499 |

Reading: see section 3.

## 2. Lead / lag, BTC and ETH 1-min returns vs NQ 1-min returns (positive lag = crypto leads NQ), day-block t

| sym | session | window | lag 0 corr | lag +1 corr (t) | lag +3 corr (t) | lag +5 corr (t) | lag -1 corr (t) |
|--|--|--|--|--|--|--|--|
| BTCUSDT | all | HOLD | 0.437 | 0.006 (0.2) | 0.003 (0.4) | -0.004 (-0.0) | 0.023 (5.4) |
| BTCUSDT | all | L6M | 0.415 | 0.004 (-0.1) | -0.001 (-0.6) | -0.002 (-0.6) | 0.022 (6.8) |
| BTCUSDT | all | PRE | 0.318 | 0.010 (2.9) | 0.001 (1.1) | -0.004 (-2.4) | 0.023 (11.4) |
| BTCUSDT | asia | HOLD | 0.329 | 0.014 (0.9) | 0.019 (1.2) | -0.008 (-0.4) | 0.039 (7.4) |
| BTCUSDT | asia | L6M | 0.379 | 0.001 (-0.5) | 0.002 (-0.1) | -0.003 (-0.9) | 0.036 (7.9) |
| BTCUSDT | asia | PRE | 0.161 | 0.005 (2.6) | 0.001 (0.7) | 0.004 (0.6) | 0.014 (6.2) |
| BTCUSDT | london | HOLD | 0.398 | 0.037 (0.7) | -0.002 (-1.3) | 0.000 (-1.3) | 0.035 (5.7) |
| BTCUSDT | london | L6M | 0.373 | 0.001 (-0.2) | -0.006 (-1.7) | 0.002 (-0.2) | 0.037 (7.3) |
| BTCUSDT | london | PRE | 0.210 | 0.007 (0.6) | 0.003 (0.0) | 0.004 (0.4) | 0.023 (5.7) |
| BTCUSDT | nyam | HOLD | 0.546 | -0.016 (-1.7) | 0.002 (-0.0) | -0.014 (-1.1) | 0.020 (1.9) |
| BTCUSDT | nyam | L6M | 0.454 | 0.003 (-1.0) | 0.004 (-0.1) | -0.006 (-1.0) | 0.004 (-0.1) |
| BTCUSDT | nyam | PRE | 0.455 | 0.018 (1.1) | -0.006 (-0.3) | -0.012 (-4.0) | 0.042 (6.1) |
| BTCUSDT | nypm | HOLD | 0.508 | 0.000 (-0.5) | -0.001 (-0.7) | 0.001 (1.0) | 0.002 (0.4) |
| BTCUSDT | nypm | L6M | 0.467 | 0.014 (0.1) | -0.001 (-0.1) | 0.000 (-2.3) | 0.019 (2.7) |
| BTCUSDT | nypm | PRE | 0.396 | -0.003 (-1.1) | 0.004 (-0.9) | -0.006 (-1.5) | 0.016 (6.5) |
| BTCUSDT | pre | HOLD | 0.366 | 0.037 (1.0) | -0.009 (-1.4) | 0.024 (1.3) | 0.049 (2.4) |
| BTCUSDT | pre | L6M | 0.471 | 0.007 (-0.8) | -0.009 (-1.7) | -0.004 (-1.3) | -0.014 (0.4) |
| BTCUSDT | pre | PRE | 0.382 | 0.006 (0.2) | 0.017 (0.4) | -0.006 (0.8) | 0.010 (0.6) |
| ETHUSDT | all | HOLD | 0.436 | 0.009 (0.5) | 0.001 (-0.0) | -0.003 (-0.3) | 0.021 (6.1) |
| ETHUSDT | all | L6M | 0.431 | 0.006 (0.4) | 0.002 (0.2) | -0.001 (-0.2) | 0.015 (4.3) |
| ETHUSDT | all | PRE | 0.294 | 0.009 (3.1) | 0.001 (0.8) | -0.002 (-1.8) | 0.024 (11.3) |
| ETHUSDT | asia | HOLD | 0.344 | 0.015 (1.8) | 0.016 (0.1) | -0.010 (-0.9) | 0.039 (7.1) |
| ETHUSDT | asia | L6M | 0.397 | 0.002 (-0.1) | 0.005 (0.5) | -0.002 (-0.6) | 0.027 (5.1) |
| ETHUSDT | asia | PRE | 0.152 | 0.011 (2.9) | 0.002 (1.5) | 0.003 (0.3) | 0.016 (4.8) |
| ETHUSDT | london | HOLD | 0.412 | 0.039 (0.1) | -0.004 (-0.5) | -0.000 (-0.7) | 0.021 (4.8) |
| ETHUSDT | london | L6M | 0.409 | 0.004 (0.4) | -0.002 (-1.0) | 0.001 (-0.4) | 0.029 (5.4) |
| ETHUSDT | london | PRE | 0.223 | 0.008 (0.4) | -0.001 (-0.3) | 0.003 (0.2) | 0.017 (4.8) |
| ETHUSDT | nyam | HOLD | 0.545 | -0.008 (-1.3) | -0.002 (-0.2) | -0.009 (-1.0) | 0.022 (2.2) |
| ETHUSDT | nyam | L6M | 0.475 | 0.007 (-0.9) | 0.005 (0.0) | -0.005 (-0.7) | 0.001 (-0.9) |
| ETHUSDT | nyam | PRE | 0.444 | 0.015 (0.8) | -0.004 (-0.0) | -0.011 (-3.5) | 0.043 (5.6) |
| ETHUSDT | nypm | HOLD | 0.490 | 0.002 (-1.0) | -0.005 (-2.3) | -0.000 (0.4) | 0.007 (1.4) |
| ETHUSDT | nypm | L6M | 0.473 | 0.014 (-0.4) | 0.001 (0.2) | 0.006 (-1.7) | 0.005 (1.3) |
| ETHUSDT | nypm | PRE | 0.375 | -0.003 (-1.8) | 0.004 (-1.3) | -0.003 (-1.7) | 0.023 (5.8) |
| ETHUSDT | pre | HOLD | 0.372 | 0.031 (1.2) | -0.005 (-0.7) | 0.024 (1.4) | 0.039 (2.1) |
| ETHUSDT | pre | L6M | 0.463 | -0.003 (-0.9) | -0.009 (-1.3) | -0.012 (-1.9) | -0.012 (0.3) |
| ETHUSDT | pre | PRE | 0.359 | 0.008 (0.5) | 0.012 (-0.7) | -0.004 (1.4) | 0.016 (1.1) |

## 4. F2 prediction markets
Kalshi crawl in progress (code/th_feeds/dl_kalshi.py; chain f2_chain.sh runs events -> eval when it finishes). Polymarket price history for Fed / CPI / jobs events: see /mnt/l2/l2vast/feeds/polymarket/.

## 3. Verdicts so far
**F1 (crypto): NULL as a layer; weak, regime-dependent leads only. No exact run warranted yet.**
- Lead/lag: contemporaneous 1-min correlation BTC/ETH vs NQ in Asia is 0.38-0.40 in L6M, 0.33-0.34 in HOLD but only 0.15-0.16 in PRE (2024-01..2025-06): crypto has become a risk-proxy twin of NQ recently. Crypto does NOT lead NQ at +1..+10 min (|corr| <= 0.02, a few |t| 2.5-4 with both signs); NQ leads crypto by one minute (corr +0.036, t 7-8, tiny). So no timing edge; at best a regime/risk co-movement read. Compare NKD: the NKD imbalance lead is also positive only inside 2025-11..2026-10 and reverses in GAP; crypto skip cells show the same pattern.
- Entry skip (H1): every passing P7_asia cell (btc_shock15 q10/q20 = quiet BTC, btc_eth_r60_dir q10) is negative in GAP (-742 to -827 $/wk) and X'; family null not beaten (P7_asia p(best) 0.11, U7_asia 0 passing cells, ALL_asia 0). K7_asia eth_shock15 q10 passes 1 cell with p(best) 0.02 but GAP -192, X' -73 (1 of 6 subsets x 84 cells: chance-level after family correction ~ 0.1).
- Re-entry gate (H3): skipping P7 rechase entries when BTC 15-min taker flow runs AGAINST the trade (btc_tkr15_dir q30, 338 trades): L6M +983, HOLD +786, GAP +641, PRE +335, X' -1,001 $/wk at engine lots; P7_asia only 159 trades: +1,092/+1,167/-68/+119/-768. Pass counts 2 (P7_all) and 1 (P7_asia) vs null mean 1.6 / p95 5: indistinguishable from chance. Candidate to carry to the exact stage only if cheap; it is a rule-2a case (positive in four windows, negative in 2023). ALLbooks rechase: 0 passing cells.
- Not run: H4 near-zone take / H5 loss-cut confirm need the 80%-of-target and -40-pt hit times (not in the trade list): queued for the exact hook stage. Give-back rate vs regime at entry is in h3h4.json (descriptive).


## 5. Hypothesis log
autopilot/F1_HYPOTHESIS_LOG.md (append-only).
