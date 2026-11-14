# DS3_CHOP_BREADTH (W-CH3, STEP 4: outside data, QUOTE ONLY)

**VERDICT: the 7-megacap proxy does NOT forecast CHOP in any usable way, so buying the Nasdaq-100 minute bars is not justified. No purchase made; all calls were $0.00 metadata quotes. Not a PASS.**

## 1. Proxy test (7 megacaps from the UW pull: NVDA AAPL MSFT AMZN META GOOGL TSLA)
Data: UW ohlc1m regular-session closes (2024-10-01..2026-11-12, ~512 days) with NQ/ES/RTY/YM 1m (uwbooks/min1_*.npz). Code: code/th_chop3/b3_panel.py, b3_test.py. Bulk: /mnt/l2/l2vast/_chop/b3/ (panel.pkl, feat.pkl, proxy_results.csv).
Label: W-CH1's file was not yet in /mnt/l2/l2vast/_chop/f1/, so my own label = NQ efficiency ratio of the rest of the session, CHOP = lowest tercile (full sample, scoring only). Sessions tested (UTC-free ET clock; 3 clocks): nyam@30 (features 09:30-10:00, label 10:00-12:00), nypm@0 (features 09:30-12:00, label 12:00-15:00), nypm@30 (features 12:00-12:30, label 12:30-15:00). Asia/london/pre/close NOT tested: the pull has no usable overnight stock data (extended hours thin) and close is a 1 h session. HOLD/PRE/X'/GAP windows not applied (their definitions are outside this part; only the 2024-10+ span exists), so older = everything before L6M.
Proxy features over the feature window: average pairwise correlation of the 7 names (1m returns), cross-sectional return dispersion, up-share (and |up-share-0.5|), NQ minus basket relative strength (abs and signed), basket return.
Benchmarks: ATR (prior 10 same-session ranges), "yesterday was chop" (same session). Controls = those two + NQ own ER and range so far + index-based correlation and dispersion of NQ/ES/RTY/YM (the W-CH1 style inputs). Model: ridge logistic, walk-forward, refit every 14 days, 120-day warm-up. Shifted-day placebos: proxy features misaligned by 2..13 days (past days only), same walk-forward.
Out-of-sample AUC for CHOP (0.5 = nothing). gain = AUC(controls+proxy) - AUC(controls). placebo_frac_ge = share of 12 shifted placebos that did as well.

| key     | win         |   n |   auc_atr |   auc_yday |   auc_ctrl |   auc_ctrl_proxy |   gain |   placebo_frac_ge |
|:--------|:------------|----:|----------:|-----------:|-----------:|-----------------:|-------:|------------------:|
| nyam@30 | L1M         |  23 |     0.618 |      0.263 |      0.605 |            0.697 |  0.092 |             0.333 |
| nyam@30 | L3M         |  65 |     0.334 |      0.373 |      0.606 |            0.619 |  0.013 |             0.333 |
| nyam@30 | L6M         | 127 |     0.445 |      0.441 |      0.563 |            0.561 | -0.002 |             0.333 |
| nyam@30 | OLDER(>L6M) | 260 |     0.515 |      0.489 |      0.512 |            0.475 | -0.037 |             0.833 |
| nyam@30 | ALL_OOS     | 387 |     0.481 |      0.477 |      0.524 |            0.499 | -0.025 |             0.833 |
| nypm@0  | L1M         |  23 |     0.473 |      0.388 |      0.429 |            0.491 |  0.062 |             0.167 |
| nypm@0  | L3M         |  65 |     0.413 |      0.422 |      0.376 |            0.433 |  0.057 |             0     |
| nypm@0  | L6M         | 127 |     0.447 |      0.434 |      0.472 |            0.478 |  0.006 |             0.25  |
| nypm@0  | OLDER(>L6M) | 259 |     0.458 |      0.419 |      0.546 |            0.54  | -0.006 |             0.417 |
| nypm@0  | ALL_OOS     | 386 |     0.447 |      0.42  |      0.544 |            0.533 | -0.01  |             0.167 |
| nypm@30 | L1M         |  23 |     0.422 |      0.373 |      0.461 |            0.49  |  0.029 |             0.333 |
| nypm@30 | L3M         |  65 |     0.459 |      0.508 |      0.525 |            0.568 |  0.042 |             0     |
| nypm@30 | L6M         | 127 |     0.512 |      0.511 |      0.507 |            0.548 |  0.041 |             0.167 |
| nypm@30 | OLDER(>L6M) | 258 |     0.427 |      0.485 |      0.51  |            0.54  |  0.03  |             0.083 |
| nypm@30 | ALL_OOS     | 385 |     0.457 |      0.495 |      0.509 |            0.544 |  0.035 |             0     |

Reading it:
- Every benchmark and the control set sit at AUC 0.43-0.60, i.e. close to a coin flip; ATR and "yesterday was chop" also do not forecast chop here. Windows of 23 (L1M) and 65 (L3M) sessions are far too small for any gap below roughly 0.08 AUC to mean anything.
- nyam@30: proxy gain is positive only in L1M/L3M (+0.09/+0.01), zero in L6M and NEGATIVE in older (-0.04). A lead must hold in recent AND older windows: it does not. The L1M figure is 23 sessions and one in three placebos beat it.
- nypm@0: gain +0.06/+0.06 in L1M/L3M, ~0 afterwards (+0.01 L6M, -0.01 older). Fails the older-window test.
- nypm@30: the only consistent sign (+0.03 to +0.04 in every window, 0 of 12 placebos as good over all OOS, 0 in L3M). Size is tiny: AUC 0.54-0.57, so a call from it would be wrong about as often as right; it does not clear any tolerant gate for a trading action. Noting it as the one thing worth re-looking at if the proxy is ever extended, not as a lead.
- Single-feature AUCs (see proxy_results.csv): megacap dispersion leans toward "less chop" in L1M/L3M (0.28/0.31, nyam@30) but is 0.49 in older sessions; megacap correlation ~0.5 everywhere. Index dispersion (disp4) shows the same recent-only lean.
Plain answer: the proxy does not forecast CHOP. Caveat: 7 names (the largest, most index-driven ones) is a weak stand-in for breadth; a negative result here bounds, but does not completely rule out, a 100-name measure. It does mean no evidence exists to justify the spend.

## 2. Quotes (Databento metadata.get_cost / get_billable_size / get_record_count, schema ohlcv-1m, stype raw_symbol; nothing downloaded or submitted)
Plan: none of the four datasets quoted at $0.00 for ohlcv-1m on this key (all nonzero, so nothing is included free). Dataset coverage: XNAS.ITCH from 2018-05; DBEQ.BASIC and EQUS.MINI from 2023-03-28 (cover 2023-04); XNAS.BASIC only from 2024-07-01 (cannot cover 2023-04..2024-06). EQUS.SUMMARY has only ohlcv-1d (not minute).
Symbols (101 line items, my best list of current Nasdaq-100 line-ups, to be verified against the index file before any purchase; membership changes since 2023-04 such as additions/removals at the December reconstitutions and delisted/renamed names (e.g. ANSS acquired, WBD, ON, GFS, CDW, MDB, TTD, DXCM, BIIB, DDOG, ZS, TEAM, LULU, GEHC) mean a point-in-time 2023-04 list differs; cost moves about $0.2 per name on EQUS.MINI): AAPL MSFT NVDA AMZN AVGO META GOOGL GOOG TSLA COST NFLX PLTR ASML AMD CSCO AZN TMUS LIN PEP ISRG MU QCOM INTU TXN AMAT LRCX ADBE BKNG SHOP PDD KLAC ARM CMCSA HON GILD AMGN ADI APP PANW CRWD VRTX MELI CEG SBUX ADP CDNS MSTR INTC CTAS ORLY MAR SNPS MDLZ CSX ABNB FTNT REGN MNST DASH WDAY PYPL ADSK AEP ROP TTWO CHTR FANG NXPI PCAR IDXX MRVL FAST ROST BKR CPRT PAYX EA KDP EXC XEL VRSK CCEP ODFL CTSH TRI DDOG KHC TEAM LULU GEHC CSGP ON CDW BIIB ANSS WBD TTD MDB GFS DXCM ZS (list order = rough weight order, top 20/30 = first 20/30).

Full 101 names, 2023-04-01..2026-11-14 (USD, records):
| dataset | 2023-04..2023 | 2024 | 2025 | 2026 YTD | total |
|---|---|---|---|---|---|
| EQUS.MINI | 4.40 (7.0M) | 5.96 (9.5M) | 6.08 (9.7M) | 5.25 (8.4M) | **21.69** (34.7M rec, 1.94 GB) |
| XNAS.ITCH | 5.27 (8.4M) | 7.56 (12.1M) | 7.76 (12.4M) | 7.08 (11.3M) | **27.67** (44.2M) (Nasdaq prints only, not consolidated) |
| DBEQ.BASIC | 24.79 (13.6M) | 26.09 (14.3M) | 23.14 (12.7M) | 21.88 (12.0M) | **95.90** (52.5M) |
| XNAS.BASIC (2024-07+) | n/a | 4.32 (H2 only) | 8.79 | 8.24 | 21.35 (partial span only) |
Cheaper subsets, EQUS.MINI, 2023-04..2026-11-14: top 20 = $4.95 (7.9M rec); top 30 = $7.18 (11.5M rec); DBEQ.BASIC top 20 = $24.60, top 30 = $34.71. RTH-only: sample-day windows show 09:30-16:00 is ~92% of the records on EQUS.MINI/DBEQ.BASIC (e.g. 36,945 of 40,224 records), so RTH-only saves under 10 percent (about $2 on EQUS.MINI); not worth the complexity. (Winter sample windows in the log were mis-set to a 1-hour range; only the summer figures are used.)
Cheapest full answer: EQUS.MINI, all 101 names, 2023-04..today, about $21.7 (consolidated feed, includes volume, so up-volume share is possible). Raw quote log: /mnt/l2/l2vast/_chop/b3/quotes.json.

Massive (formerly Polygon.io) Stocks, from the public pricing page only (no signup): Stocks Advanced $199/month ("20+ years of history", real-time, websockets, individual use only; 20 percent off on annual billing). The page shows no minute-aggregate or rate-limit details and only the Advanced plan; I did not verify the lower-tier plans. A one-month Advanced subscription ($199, or about $159/month on annual billing) would fetch 1-minute aggregates for 101 names x 3.6 years via REST; it is 9x the Databento EQUS.MINI quote and a recurring subscription, so Databento is the cheaper route.

What true breadth needs: for each of ~100 names, 09:30-16:00 1m close and volume per day (EQUS.MINI ohlcv-1m is enough, ~35M rows ~ 2 GB). Up-volume share = sum of volume of names with positive return since the clock start over total; breadth = share of names above their session open/VWAP; dispersion = cross-sectional std of cumulative returns; average pairwise correlation = rolling mean of the 100x100 return correlation over 15-30 minute windows (point-in-time membership and corporate-action-adjusted prices needed; weights from a separate source). Tick/uptick-based versions need trades/tbbo, a much larger purchase (not quoted).

## 3. Recommendation (plain words)
The 7-name megacap proxy does not forecast CHOP: it adds nothing over ATR, yesterday's chop and the index-based dispersion/correlation, and the small recent gains disappear in older windows and are matched by shifted-day placebos (only nypm@30 is consistently slightly positive, +0.035 AUC, too small to act on). Buying is therefore not justified by this evidence. If the user wants the full measure anyway, the exact ask would be: Databento EQUS.MINI, ohlcv-1m, the 101 symbols above (verified point-in-time), 2023-04-01..2026-11-14, quoted $21.69. That is cheap enough to be a curiosity purchase, but it should be labelled as untested-hope rather than a proxy-backed lead. No purchase has been made or authorised by me.
