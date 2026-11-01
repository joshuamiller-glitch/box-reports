# DS3_DATA_REDO - data rebuild to the cap 2026-10-31 (REDO-1, T-RECENT-REDO), 2026-11-01

Research only; no purchases, no downloads; originals untouched, every new file next to the old one (`*_redo`, symlink views). Log: DECISIONS.md. Sub-reports: DS3_DATA_REDO_BARS.md, _T1.md, _T2.md, _T3A.md (when written), _T3B.md. Code `l2vast/ds3/code/cap/`.

## PAGE 1

**Verdict.** The NQ composite path is rebuilt through label day 20261030 (last trading day; Sat 10-31 has no session) from the de-duplicated tape, append-only, and every old day reproduces: trade rows of 12 books, trade_index (69,660 trades, 47,131 old identical), lock-engine inputs, bar store (164 series), tick-bar library, 1-s path, aux bars, L2 gates/dp10s/ldp10s. BASE-1's D7 engine and the one-convention engine run to 20261030 (935 label days, 15 s/run) via `code/cap/engine_redo/redo_boot.py`; 19 stored checks tie to 0.0000 $/day on the 745 old days. NOT possible without purchases (not synthesised): any instrument other than NQ/ES/RTY below the 1-min level, and ohlcv-1m of the 23 other instruments after 2026-10-16; O6 stops at 20261023; VIX after 2026-10-16.

### A. The date-axis parameter (single config)
`out/cap/CAP.json`: cap 20261031 (last trading label day on disk Fri 20261030; Sat 10-31 has no session), OLD CAP 20260206. Helper `l2vast/ds3/code/cap/windows.py` (`import windows as W`): `W.CAP, W.WINDOWS, W.ORDER, W.mask / slice_daily / slice_weekly / split_daily / weekly / stats / mde / dmde / table / old_windows`.

| window | from | to | note |
|---|---|---|---|
| L1M | 2026-10-01 | 2026-10-31 | VIEW only (no selection) |
| L2M | 2026-09-01 | 2026-10-31 | VIEW only |
| L3M | 2026-08-01 | 2026-10-31 | |
| L6M | 2026-05-01 | 2026-10-31 | |
| HOLD | 2025-11-01 | 2026-10-31 | |
| MID | 2026-02-07 | 2026-04-30 | between the old cap and L6M |
| PRE | 2024-02-01 | 2025-06-30 | unchanged |
| X' | 2023-04-01 | 2024-01-31 | unchanged |
OLD windows kept for 'old L3M (to Feb-06)' columns: L3M_old 2025-11-06..2026-02-06, L6M_old 2025-08-01..2026-02-06, HOLD_old 2025-07-01..2026-02-06. MDE = 2.8 x SE of the weekly mean (level) or of the paired weekly delta (== d7lib.mde / dmde); weekly = ISO week of the label day (== dd_lib.wk).


### B. Tie-out table
| layer | new file | old part vs stored | new days check |
|---|---|---|---|
| tape de-dup (cap 202610) | out/tape_dedup/{NQ,ES,RTY}/2026-03, 2026-08, 2026-10__ext_20261024_20261030 + *_dropin_redo | block rule, head == window element-wise (9 files) | dedup tape volume / L2 1-min = 1.0000 on all 33 post-cap files (2 ES files off by 1 contract) and on 190/190 days; originals ratio 1.0017/1.0018/1.0065 |
| 1-s path ds3_g2_redo | /mnt/l2/l2vast/ds3_g2_redo | 13 arrays + 4 event lists: old prefix bit-identical | 46,674,871 s, to 20261030 |
| volume | out/redo/volume_tieout.csv | - | bars2 1-min/1-s = L2 on 184 days; 6 roll days (0317-18, 0616-17, 0915-16) differ by construction (library holds both contracts, L2 front only) |
| aux 1-min bars | ds3_thp_redo/aux/aux_bar.npz | 34 columns bit-identical on 1,059,591 old bars | volume from L2 ext parts included (an earlier zero-volume file was replaced; kept as aux_bar_noext_volbug.npz) |
| day labels | out/redo/dv2a/day_labels.parquet | identical except October month-end flags; VIX NaN after 2026-10-16 (stale > 5 d); FOMC 2026-10-28 added | - |
| trade rows ST HM KB SM WT PB7 PE PB DN CR MV MA | out/redo/rows/*_redo.parquet | identical prefix, all columns, 0 straddlers | independent 30-day numpy scan on SH/SL/SC: entry/type/exit 100% (CR exit price 97/121 as in the old file); PE entry vs ohlcv-1m open 457/460 |
| O6 (3 T-OPEN cells) | O6_trades_redo.parquet | rows to 0206 equal survivors_for_A exactly | PARTIAL to 20261023 (harness inputs end there) |
| trade_index | out/thp_redo/trade_index.parquet (59 cols) | 47,131 old tids identical | 69,660 trades |
| THP dp tables / tstats | /mnt/l2/l2vast/ds3_thp_redo/data, aux/tstats | old months reproduced | all months 202304..202610 |
| L2 feature tables | /mnt/l2/l2vast/ds3_l2feat_redo/{dp10s,ldp10s,gates} | 202602 old tids bit-identical | to 202610; dp1m/ldp1m, t2/t3/t4/vpin: see T3A report (not needed by the composite) |
| bar store 164 series | out/bars_store_redo | 3,936/3,936 clean old month files bit-identical; 11 defective months = TAPE-2 | tc/1m volume vs library 0.9973-1.0000; bpm frozen at the old-window value |
| tick-bar library 44 types | out/bars_redo | 0 mismatching rows on 769 non-defective old days | volume = tape = L2 on 970/970 days |
| lock-engine inputs | out/dipentry_redo, trendgate_redo, eint1dd_redo, l2set_redo, ds3_l2set_redo, poi_store_redo (8 streams), confirm_redo, thp_redo c3 cache, tape_rescore_redo (X1-X5) | old rows identical (trades_arm 63 cols except opp_s of 33 rows = real extension) | engine: 6 core books exact; X3/X4/X5 differ on 6 cells (max $3,050/day) only on days of the 11 defective-tape months, as expected |
| engines | out/redo/engine/d7_base_literal_redo.npz | 19 checks max abs diff 0.0000 $/day | 190 new days finite, no all-zero book/session, 38 weeks, total +$670,521 (D7 base) |

### C. The one-table state of the data, 2026-02-07 .. 2026-10-31
Cells: P all days present; `17P 4M` counts (P present, p partial, M missing, d duplicated-hour defect). Zero-signal days of a book show as M in 'trade library' rows (no trade, not a data gap). Reference calendar = 190 trading label days.

| layer | inst | Feb(07+) | Mar | Apr | May | Jun | Jul | Aug | Sep | Oct(-30) | last day present | missing days / note |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| tape (original files) | NQ | P | 21P 1d | P | P | P | P | 20P 1d | P | 21P 1d | 20261030 | d: 20260302, 20260803, 20261026 |
| tape (de-duplicated, out/tape_dedup) | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| tape (original files) | ES | P | 21P 1d | P | P | P | P | 20P 1d | P | 21P 1d | 20261030 | d: 20260302, 20260803, 20261026 |
| tape (de-duplicated, out/tape_dedup) | ES | P | P | P | P | P | P | P | P | P | 20261030 |  |
| tape (original files) | RTY | P | 21P 1d | P | P | P | P | 20P 1d | P | 21P 1d | 20261030 | d: 20260302, 20260803, 20261026 |
| tape (de-duplicated, out/tape_dedup) | RTY | P | P | P | P | P | P | P | P | P | 20261030 |  |
| L2 table 1-min (tables/<S>/1min) | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| L2 table 1-s (tables/<S>/1s) | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| L2 table 100ms (tables/<S>/100ms) | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| L2 table sweeps (tables/<S>/sweeps) | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| L2 table vpin (tables/<S>/vpin) | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| L2 table events_L13 (tables/<S>/events_L13) | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| L2 table 1-min (tables/<S>/1min) | ES | P | P | P | P | P | P | P | P | P | 20261030 |  |
| L2 table 1-s (tables/<S>/1s) | ES | P | P | P | P | P | P | P | P | P | 20261030 |  |
| L2 table 100ms (tables/<S>/100ms) | ES | P | P | P | P | P | P | P | P | P | 20261030 |  |
| L2 table sweeps (tables/<S>/sweeps) | ES | P | P | P | P | P | P | P | P | P | 20261030 |  |
| L2 table vpin (tables/<S>/vpin) | ES | P | P | P | P | P | P | P | P | P | 20261030 |  |
| L2 table events_L13 (tables/<S>/events_L13) | ES | P | P | P | P | P | P | P | P | P | 20261030 |  |
| L2 table 1-min (tables/<S>/1min) | RTY | P | P | P | P | P | P | P | P | P | 20261030 |  |
| L2 table 1-s (tables/<S>/1s) | RTY | P | P | P | P | P | P | P | P | P | 20261030 |  |
| L2 table 100ms (tables/<S>/100ms) | RTY | P | P | P | P | P | P | P | P | P | 20261030 |  |
| L2 table sweeps (tables/<S>/sweeps) | RTY | P | P | P | P | P | P | P | P | P | 20261030 |  |
| L2 table vpin (tables/<S>/vpin) | RTY | P | P | P | P | P | P | P | P | P | 20261030 |  |
| L2 table events_L13 (tables/<S>/events_L13) | RTY | P | P | P | P | P | P | P | P | P | 20261030 |  |
| mbp-10 raw files (raw/<S>) | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| mbp-10 raw files (raw/<S>) | ES | P | P | P | P | P | P | P | P | P | 20261030 |  |
| mbp-10 raw files (raw/<S>) | RTY | P | P | P | P | P | P | P | P | P | 20261030 |  |
| 1-min series (data/databento/<S>/series_<S>.npz, back-adjusted) | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| 1-min series (data/databento/<S>/series_<S>.npz, back-adjusted) | ES | P | P | P | P | P | P | P | P | P | 20261030 |  |
| 1-min series (data/databento/<S>/series_<S>.npz, back-adjusted) | RTY | P | P | 21P 1p | P | 21P 1p | P | 20P 1p | 20P 2p | P | 20261030 | p: 20260403, 20260615, 20260828, 20260907, 20260914 |
| 1-min series (data/databento/<S>/series_<S>.npz, back-adjusted) | CL | P | P | 21P 1M | P | P | P | P | P | 9P 13M | 20261013 | M: 20260403, 20261014-20261030 |
| 1-min series (data/databento/<S>/series_<S>.npz, back-adjusted) | GC | P | P | 21P 1M | P | P | P | P | P | 9P 13M | 20261013 | M: 20260403, 20261014-20261030 |
| 1-min series (data/databento/<S>/series_<S>.npz, back-adjusted) | ZN | P | P | P | P | P | P | P | P | 9P 13M | 20261013 | M: 20261014-20261030 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | 6A | P | P | P | P | P | P | P | P | 12P 10M | 20261016 | M: 20261019-20261030 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | 6B | P | P | P | P | 21P 1p | P | P | P | 12P 10M | 20261016 | M: 20261019-20261030; p: 20260612 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | 6C | P | P | 21P 1p | P | P | P | P | P | 12P 10M | 20261016 | M: 20261019-20261030; p: 20260403 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | 6E | P | P | P | P | P | P | P | P | 12P 10M | 20261016 | M: 20261019-20261030 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | 6J | P | P | P | P | P | P | P | P | 12P 10M | 20261016 | M: 20261019-20261030 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | CL | P | P | 21P 1M | P | P | P | P | P | 12P 10M | 20261016 | M: 20260403, 20261019-20261030 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | ES | P | P | P | P | P | P | P | P | 21P 1p | 20261030 | p: 20261019 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | GC | P | P | 21P 1M | P | P | 22P 1p | P | P | 12P 10M | 20261016 | M: 20260403, 20261019-20261030; p: 20260730 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | HE | 14P 1M | P | 21P 1M | 20P 1M | 21P 1M | 22P 1M | P | 21P 1M | 12P 10M | 20261016 | M: 20260216, 20260403, 20260525, 20260619, 20260703, 20260907, 20261019-20261030 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | HG | P | P | 21P 1M | P | P | P | P | P | 12P 10M | 20261016 | M: 20260403, 20261019-20261030 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | HO | P | P | 21P 1M | P | P | P | P | P | 12P 10M | 20261016 | M: 20260403, 20261019-20261030 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | LE | 14P 1M | P | 21P 1M | 20P 1M | 21P 1M | 22P 1M | P | 21P 1M | 12P 10M | 20261016 | M: 20260216, 20260403, 20260525, 20260619, 20260703, 20260907, 20261019-20261030 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | NG | P | P | 21P 1M | P | P | P | P | P | 12P 10M | 20261016 | M: 20260403, 20261019-20261030 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | NKD | P | 21P 1p | 21P 1p | P | 21P 1p | P | P | 21P 1p | 12P 10M | 20261016 | M: 20261019-20261030; p: 20260312, 20260403, 20260611, 20260910 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | NQ | P | P | P | P | P | P | P | P | 21P 1p | 20261030 | p: 20261019 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | PL | P | P | 21P 1M | P | P | P | P | P | 12P 10M | 20261016 | M: 20260403, 20261019-20261030 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | RB | P | P | 21P 1M | P | P | P | P | P | 12P 10M | 20261016 | M: 20260403, 20261019-20261030 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | RTY | P | P | P | P | P | P | P | P | 21P 1p | 20261030 | p: 20261019 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | SI | 14P 1p | P | 20P 1p 1M | P | P | P | 20P 1p | P | 12P 10M | 20261016 | M: 20260403, 20261019-20261030; p: 20260226, 20260429, 20260828 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | YM | P | P | P | P | P | P | P | P | 12P 10M | 20261016 | M: 20261019-20261030 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | ZB | P | P | 21P 1p | P | P | P | P | P | 12P 10M | 20261016 | M: 20261019-20261030; p: 20260403 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | ZC | 14P 1M | P | 21P 1M | 20P 1M | 20P 1p 1M | 22P 1M | P | 21P 1M | 12P 10M | 20261016 | M: 20260216, 20260403, 20260525, 20260619, 20260703, 20260907, 20261019-20261030; p: 20260630 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | ZF | P | P | 21P 1p | P | P | P | P | P | 12P 10M | 20261016 | M: 20261019-20261030; p: 20260403 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | ZN | P | P | P | P | P | P | P | P | 12P 10M | 20261016 | M: 20261019-20261030 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | ZS | 14P 1M | P | 21P 1M | 20P 1M | 21P 1M | 22P 1M | P | 21P 1M | 12P 10M | 20261016 | M: 20260216, 20260403, 20260525, 20260619, 20260703, 20260907, 20261019-20261030 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | ZT | P | P | 21P 1p | P | P | P | P | P | 12P 10M | 20261016 | M: 20261019-20261030; p: 20260403 |
| ohlcv-1m continuous (data/autopilot/ohlcv1m/<S>_2026) | ZW | 14P 1M | P | 21P 1M | 20P 1M | 21P 1M | 22P 1M | P | 21P 1M | 12P 10M | 20261016 | M: 20260216, 20260403, 20260525, 20260619, 20260703, 20260907, 20261019-20261030 |
| 1-s path array ds2 (pairP2/ds2_SS/SC/K0/K1; NQ back-adj.) | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| 1-s path array ds3_g2 (SS/SH/SL/SC; THP/bars store path) | NQ | P | P | P | P | P | P | P | P | 17P 5M | 20261023 | M: 20261026-20261030 |
| 1-s/1-min day files data/bars2 (capped copy: 1-s+1-min day files) | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| 1-s/1-min day files h2root/bars2 (1-s+1-min day files) | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| aux 1-min bars (ds3_thp/aux/aux_bar.npz) | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| bar store 164 series (out/bars_store), series tc/1m | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| bar store rebuilt from de-dup tape (out/bars_store_dedup, 11 old months only) | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| tick-bar library out/bars (time_1m; 44 types; built on ORIGINAL tape via E1 cache) | NQ | P | 21P 1d | P | P | P | P | 20P 1d | P | 17P 5M | 20261023 | M: 20261026-20261030; d: 20260302, 20260803 |
| L2 entry-side gates 1-s (ds3_l2feat/gates) | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| trade library THP trade_index, book KB = K6 | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| trade library THP trade_index, book PE = P6 | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| trade library THP trade_index, book SM = U6 | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| trade library THP trade_index, book HM = H6 | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| trade library THP trade_index, book MV = M6 | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| trade library THP trade_index, book PB = A6(lib PB) | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| trade library THP trade_index, book ST = S6 | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| trade library THP trade_index, book WT = W6 | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| trade library THP trade_index, book DN = N6 | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| trade library THP trade_index, book MA = MA6 | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| trade library THP trade_index, book CR = C6 | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| trade library A6 = PB7 rows (sundaydecision/pb7_rows) | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| trade library O6 | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| lock engine input dipentry/trades_arm.parquet (lock-engine trade table) | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| L2 feature table dp1m (ds3_l2feat; trade decision grid, book ST) | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| L2 feature table dp10s (ds3_l2feat; trade decision grid, book ST) | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| L2 feature table ldp1m (ds3_l2feat; trade decision grid, book ST) | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| L2 feature table ldp10s (ds3_l2feat; trade decision grid, book ST) | NQ | M | M | M | M | M | M | M | M | M |  | M: ALL 190 |
| REDO 1-s path ds3_g2_redo | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| REDO aux 1-min bars (ds3_thp_redo/aux) | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| REDO bar store 164 series (bars_store_redo), series tc/1m | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| REDO tick-bar library (bars_redo, 44 types; de-dup tape) | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| REDO trade library trade_index_redo, book KB = K6 | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| REDO trade library trade_index_redo, book PE = P6 | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| REDO trade library trade_index_redo, book SM = U6 | NQ | P | P | P | P | 21P 1M | 22P 1M | 20P 1M | 21P 1M | 20P 2M | 20261030 | M: 20260615, 20260701, 20260818, 20260921, 20261006, 20261022 |
| REDO trade library trade_index_redo, book HM = H6 | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| REDO trade library trade_index_redo, book MV = M6 | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| REDO trade library trade_index_redo, book PB = A6(lib PB) | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| REDO trade library trade_index_redo, book ST = S6 | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| REDO trade library trade_index_redo, book WT = W6 | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| REDO trade library trade_index_redo, book DN = N6 | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| REDO trade library trade_index_redo, book MA = MA6 | NQ | P | P | P | P | 21P 1M | P | P | P | P | 20261030 | M: 20260615 |
| REDO trade library trade_index_redo, book CR = C6 | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| REDO trade library A6 = PB7 rows (pb7_rows_redo) | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| REDO trade library O6 (3 T-OPEN cells; harness ends 20261023) | NQ | P | 20P 2M | 21P 1M | 19P 2M | P | P | P | 21P 1M | 17P 5M | 20261023 | M: 20260324, 20260330, 20260403, 20260513-20260514, 20260903, 20261026-20261030 |
| REDO lock engine input trades_arm_redo | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| REDO D7 engine cube (11 books x 6 sessions, d7_base_literal_redo) | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| REDO L2 feature table dp10s (ds3_l2feat_redo, book ST) | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| REDO L2 feature table ldp10s (ds3_l2feat_redo, book ST) | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |
| REDO L2 gates 1-s (ds3_l2feat_redo/gates) | NQ | P | P | P | P | P | P | P | P | P | 20261030 |  |

Notes: (1) d = ORIGINAL tape files; use the de-duplicated row. (2) NQ/ES/RTY are the only instruments with tape/mbp-10/L2; every other instrument (YM, ZN, GC, CL, 6E, 6J, 6B, 6C and the rest) has ohlcv-1m only, ending 2026-10-16 (10 trading days missing, not bought, not synthesised); NQ 1-s arrays only; ES/RTY have no 1-s path array. (3) Redo rows of the old layers (before the 'REDO' rows) still end at their old caps: use the REDO rows.

## STORED DERIVED PRODUCTS THAT STILL END AT 2026-02-06 (owners must extend; builder entry points)
| product | where | how to extend |
|---|---|---|
| all windows/ledger date logic | any script with 20260206/202602 literals (718 files in ds3/code) | import cap/windows.py; use `*_redo` inputs |
| ledger rows / RECENT_WINS / streams (43,660 series) | out/recent_wins, ledger | code/recent_wins/compile_recent_wins.py, recentedge*/re6_*.py on the redo trade tables; per-trade vectors from out/thp_redo/trade_index + dp tables |
| POI streams (681 non-SET8 + rsim) | out/poi_store/streams, rsim | code/poi/poi_build_streams.py, poi_build_feats.py (SET8 only done: engine_redo/redo_gen_poi.py) |
| ABR feature store | out/abr | code/abr/abr_build.py (thp_* copies in abr/); use thp_redo/trade_index and ds3_thp_redo data |
| EINT1 features | out/eint1, eint1dd | code/eint1/ei_feat.py (masks done: engine_redo/redo_masks.py); order-flow chart_5m columns need flow_1m |
| SIXTY streams | out/sixty, sixty2 | code/sixty/ s*_ scripts over the redo cube/series |
| DEAD_CELLS programs' per-trade vectors (BARS-CAND, GRID, ICT, BAR-ENG, CF-BARS) | out/bars_cand*, bars_eng, ... | their harnesses read bars_store / bars: point at out/bars_store_redo and out/bars_redo; reps re-scored by their owners |
| ZL / ZONES order-book streams | out/zl, zones* | code/zones*/ with L2 tables incl. tables/NQ/<tbl>/2026-10__ext_*.parquet |
| LGB entry prediction, l2set joint streams, poi rsim | out/l2set/entry, joint | NaN/copied beyond old cap (unused by D7) |
| forward-weekly extension procedure | RUNBOOK_WEEKLY_EXTENSION.md | add: run cap/tape_dedup_redo.py on each new month/ext file BEFORE any use (2026-11 starts Sunday, DST: Sunday open 23:00Z); then the extend commands in DS3_DATA_REDO_T3B.md / _BARS.md / _T1.md / _T2.md |

## Caveats
Month-keyed L2 readers must also read `2026-10__ext_*` parts. FOMC list in dv2a_labels has a missing comma (2024-11-07 and 2025-01-29 merge into one invalid date): kept so that old labels reproduce; flag for owners. bar-store `bpm` frozen at the old window (full-window bpm would change g in 86/164 series). Roll days 6 new: vol_ok False. Weekly D7 stats windows inside d7lib/dd_lib keep OLD definitions: apply windows.py to the daily series.
