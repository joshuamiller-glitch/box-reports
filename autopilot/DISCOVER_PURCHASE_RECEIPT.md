# DISCOVER_PURCHASE_RECEIPT (2026-11-03) - Databento GLBX.MDP3, LEAN option, user-approved "buy lean option"
Params: dataset GLBX.MDP3, symbols X.v.0, stype_in=continuous, end=2026-11-01 exclusive, get_cost checked immediately before each pull (all within 0.1% of quote). Script: outputs/l2vast/ds3/code/discover/dq_pull.py (key read from env only). Log: /mnt/l2/l2vast/ds3/discover_data/pull_log.json
Dir: /mnt/l2/l2vast/ds3/discover_data/
| item | file | bytes | rows | range (UTC) | get_cost USD |
|---|---|---|---|---|---|
| NKD trades 2023-04-01..2026-10-31 | NKD_trades_20230401_20261031.dbn.zst | 91,288,140 | 3,976,216 | 2023-04-02 22:00 .. 2026-10-30 20:59:30 | 4.9770 |
| NKD ohlcv-1s | NKD_ohlcv1s_20230401_20261031.dbn.zst | 25,775,254 | 2,715,056 | 2023-04-02 22:00 .. 2026-10-30 20:59:30 | 9.9121 |
| 6J ohlcv-1s | 6J_ohlcv1s_20230401_20261031.dbn.zst | 98,157,146 | 12,559,639 | 2023-04-02 22:00 .. 2026-10-30 20:59:56 | 45.8525 |
| top-up 1m NKD | topup_ohlcv1m_NKD_20261013_20261031.dbn.zst | 181,892 | 12,930 | 10-13 .. 10-30 20:59 | 0.0472 |
| top-up 1m 6J | topup_ohlcv1m_6J_... | 230,983 | 18,609 | 10-13 .. 10-30 20:59 | 0.0679 |
| top-up 1m 6E | topup_ohlcv1m_6E_... | 249,713 | 18,921 | same | 0.0691 |
| top-up 1m ZN | topup_ohlcv1m_ZN_... | 210,584 | 18,423 | same | 0.0673 |
| top-up 1m ZB | topup_ohlcv1m_ZB_... | 189,728 | 17,517 | same | 0.0640 |
| top-up 1m MBT | topup_ohlcv1m_MBT_... | 289,156 | 18,469 | 10-13 .. 10-31 23:43 | 0.0674 |
| top-up 1m BTC | topup_ohlcv1m_BTC_... | 208,515 | 14,013 | 10-13 .. 10-31 22:28 | 0.0512 |
| top-up 1m GC | topup_ohlcv1m_GC_... | 338,404 | 19,196 | 10-13 .. 10-30 20:59 | 0.0701 |
| top-up 1m CL | topup_ohlcv1m_CL_... | 306,518 | 19,091 | same | 0.0697 |
TOTAL cost (sum of get_cost) = **$61.315** (approved ~$61.3, cap $65). Billed balance not read from API; sum of get_cost is the figure.
Notes: top-ups were pulled for the full 10-13..10-31 (overlap with disk through ~10-16 is ~3 days, ~$0.1 total; merge dedups). 10-31 is a Saturday so equity/FX/rates end Fri 10-30 20:59 UTC; crypto (BTC/MBT) run to 10-31. Databento flagged 3 degraded days in NKD trades (2024-09-18, 2025-09-17, 2025-09-24, ...). Timestamp convention: ts_event = bar OPEN (1-s bars aggregate exactly to the same-ts 1-m bar, verified NKD and 6J). Loader: outputs/l2vast/ds3/code/discover/load_discover_data.py. Nothing incomplete.
