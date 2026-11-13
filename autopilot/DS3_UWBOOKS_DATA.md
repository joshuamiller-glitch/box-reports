# DS3_UWBOOKS_DATA - price-data inventory for T-UWBOOKS (W-UB3), written 2026-11-13 ~14:50Z. Span needed: 2024-10-01 .. today (UW 2-year history).
Code: code/th_uwbooks/instruments.py (loader load_path), build_min1.py, build_ym_ser.py. Caches: /mnt/l2/l2vast/uwbooks/min1_<I>.npz, /mnt/l2/l2vast/uwbooks/ser/YM_{mid,hi,lo}.mm.

| instrument | 1-min OHLCV | 1-s | L2 / book | missing for 2024-10-01..today |
|---|---|---|---|---|
| NQ | 2023-02-01 .. 2026-11-10 07:59Z (min1_NQ.npz; _th_sz/bars1m to 10-16 + ext ohlcv-1m dbn) | trade-second bars instr_1s/NQ_S*.npy 2023-02-01..2026-10-16 20:59:59Z; per-second mid _th_fd/ser to 2026-11-05 16:04Z | mbp-10 2023-02..2026-10-30 (raw/NQ), MBO L3M subsets, state days _th_state/days 2023-04-03..2026-11-11 | 1-min 2026-11-10 08:00Z .. today; 1-s 2026-10-17..today (partly covered by ser mid to 11-05) |
| ES | 2023-02-01 .. 2026-11-10 07:59Z | instr_1s/ES_S*.npy to 2026-10-16; ser mid to 2026-10-31 23:59Z | mbp-10 2023-08..2026-10-30; state days 2023-08-01..2026-10-30 | same 1-min tail; 1-s 2026-11-01..today |
| RTY | 2023-02-01 .. 2026-11-10 07:59Z | instr_1s/RTY_S*.npy to 2026-10-16; ser mid to 2026-10-31 | mbp-10 2023-08..2026-10-30 | same as ES |
| YM | 2022-01-02 .. 2026-11-10 07:59Z (_th_fd/core_bars/YM.npz, P1 + top-up) | bbo-1s MID only 2026-05-01..2026-11-10 (_th_cross/sec/bbo_YM_c_0.parquet, 9.07M rows); NO 1-s before 2026-05-01 | none (no YM book) | 1-s 2024-10-01..2026-04-30; 1-min tail from 11-10 08:00Z |
| MNQ MES M2K MYM | NOT ON BOX. Same index as parent, so the parent path is used (path_as); only tick value, point value, fee differ. Micro-specific book/liquidity and slippage are not measurable. | | | no data and no purchase needed for price path |

Notes: continuous .v.0, raw (roll gaps not adjusted). The 1-min panel flag `idio` (own 1-min move > 0.25% while the other three indexes < 0.08%) is a heuristic, mostly real stock-specific jumps, NOT a roll detector; rolls are <= ~8 minutes per year and are not removed. NQ/ES/RTY 1-s bars exist only for seconds that printed (forward-fill with grid=True). YM before 2026-05-01 is 1-min only: in the ser-format file hi/lo are placed at :20/:40 of each minute, so the stop-vs-target order inside one YM minute is unknown (score YM with 1-min bars or treat ties conservatively). The databento licence limit on 2026-11-13 14:10Z reaches today, so the tails below are purchasable.

UW side (/mnt/l2/l2vast/uw, from W-UW2): SPX NDX QQQ SPY spot_1m, spot_strike, spot_exp_strike, oi_strike, gex_levels_oi/vol, greek_exp each 553 files 2024-10-01..2026-11-12; tide 553 files (folder `_`, market-wide); vol_stats SPX NDX QQQ SPY 553 each; dp_levels QQQ SPY + 8 megacaps 260 days (2025-11-14..2026-11-12). Not yet on box (step 3 of this task): IWM, DIA, megacap spot-exposures.

## QUOTES (Databento metadata.get_cost, GLBX.MDP3, 2026-11-13 ~14:40Z; NOTHING BOUGHT; lead decides; remaining overall SPEND.json cap = 8000 - 7871.91 = $128.09, T-CROSS own rule: no buy above $100 without the user)
| item | quote |
|---|---|
| NQ ES RTY YM ohlcv-1m 2026-11-10T08:00 .. 2026-11-13 (1-min tail) | $0.00 as returned (rounded to cents; P_TOPUP 1-min for 12 products earlier cost $1.01) |
| NQ ES RTY ohlcv-1s 2026-10-17 .. 2026-11-13 | $0.00 as returned (rounded; ohlcv-1s NKD was $1.22 for L6M) |
| YM ohlcv-1s 2024-10-01 .. 2026-11-10 | $0.00 as returned (rounded; treat as < $2) |
| YM bbo-1s 2024-10-01 .. 2026-04-30 | $23.63 |
| ES RTY bbo-1s 2026-10-17 .. 2026-11-13 | $0.00 as returned |
Recommendation (ask lead): the 1-min tail and the YM ohlcv-1s 2024-10..2026-04 are the only gaps that matter for the 2-year UW span; both quote at about zero. YM bbo-1s is not needed. Not bought.
