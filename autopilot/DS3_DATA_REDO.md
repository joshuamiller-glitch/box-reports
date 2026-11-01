# DS3_DATA_REDO - data rebuild to the new cap 2026-10-31 (REDO-1, T-RECENT-REDO) - FIRST DELIVERY (2026-11-01 ~16:30Z)

Research only. No purchases, no downloads. Originals untouched; every new file is next to the old one. Log: DECISIONS.md. Code `l2vast/ds3/code/cap/` (windows.py, inventory.py, inv_md.py, tape_dedup_redo.py); outputs `l2vast/ds3/out/cap/` (CAP.json), `out/redo/` (inventory_days.csv, inventory_summary.csv, INVENTORY.md), `out/tape_dedup/` (de-duplicated copies, `*_dropin_redo/`, `manifest_redo_cap202610.csv`).

## PAGE 1

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

### B. The one-table state of the data, 2026-02-07 .. 2026-10-31 (label days; reference calendar = the 190 trading label days 20260209..20261030 of the NQ 1-min series)
Cells: P = every day present; `17P 4M` = counts (P present, p partial, M missing, d duplicated-hour defect). Instruments with tape / mbp-10 / L2 / 1-s on disk: NQ, ES, RTY only (the only ones ever bought at that depth). All other instruments exist as ohlcv-1m continuous only, last bar 2026-10-16 (not purchased since: the weekly ~$6 library buy was not approved). NOT synthesised: the missing cells stay missing.

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


Notes: (1) 'dup-defect' = the stray Sunday first-hour duplication in the ORIGINAL tape files of the months/weeks whose first session opens on the weekend: 2026-03 (label day 20260302), 2026-08 (20260803) and the weekly ext tape 2026-10__ext_20261024_20261030 (20261026), in NQ, ES and RTY; de-duplicated copies are in out/tape_dedup (volume ratio to the L2 1-min table 1.0000 on all 33 files, ES 0.99999996 and 1.00000003 = 1 contract). The 2026-11 monthly file (starts Sunday 2026-11-01) will carry it too. (2) The tick-bar library (out/bars) was built on the ORIGINAL tape (E1 cache), so its 2026-03 and 2026-08 first days are affected and it ends 20261023; the bar store ends 202602. (3) The rows 'ohlcv-1m' for other instruments show the missing 2026-10-17..10-30 (10 trading days) - no purchase, not synthesised. (4) Part 'trade library' / 'lock engine' / 'L2 feature tables' end at the OLD CAP 2026-02-06 by construction (cap guards in the builders); the rebuild plan is below.
