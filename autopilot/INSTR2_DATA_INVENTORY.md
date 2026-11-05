# INSTR2 DATA INVENTORY (T-INSTR-2 day-one, CAL, 2026-11-05)
Scope note: l2vast/ds3/prereg/INSTR2_INV_scope.md, sha256 8355c13175acfaebc168fc166451986c97a4d125fad975263182fee88e5b855a (measurement only, read-only, no network, no purchases).
Script: code/instr2/instr2_inventory.py. Table: outputs/out/instr2_inventory.csv (also instr2_inventory_1m.csv).

## 1. Owned 1-min bars (outright, `.v.0` volume-front continuous), files /mnt/l2/rootmoves/data_autopilot/ohlcv1m/<SYM>_<year>.dbn.zst (symlink data/autopilot/ohlcv1m)
Label day = ET date of (wall clock + 6 h). "Missing weekdays" = Mon-Fri label days with no bars (holidays included, so ~45-50 is normal for 13.8 y; RTY 23 over 9.3 y). No duplicate timestamps, zero zero-volume bars in any file.
| Instrument | First bar (UTC) | Last bar (UTC) | Rows | Label days | Median bars/day | Short days (<200 bars) | Roll id-changes | Price range (raw frame) |
|---|---|---|---|---|---|---|---|---|
| ES | 2013-01-02 11:00 | 2026-10-30 20:59 | 4,832,209 | 3560 | 1365 | 2 | 55 | 1438.25 - 7897.5 |
| NQ | 2013-01-02 11:00 | 2026-10-30 20:59 | 4,741,997 | 3560 | 1365 | 2 | 55 | 2686.25 - 31616.5 |
| RTY | 2017-07-09 22:01 | 2026-10-30 20:59 | 3,079,835 | 2407 | 1331 | 1 | 37 | 948.5 - 3079.9 |
| YM | 2013-01-02 11:00 | 2026-10-16 20:59 | 4,710,231 | 3555 | 1360 | 1 | 55 | 13166 - 54884 |
| GC | 2013-01-01 23:00 | 2026-10-16 20:59 | 4,784,485 | 3548 | 1378 | 8 | 69 | 1045.4 - 5586.2 |
| CL | 2013-01-01 23:00 | 2026-10-16 20:59 | 4,787,820 | 3549 | 1375 | 2 | 165 | 6.5 - 130.5 |
| ZN | 2013-01-02 11:00 | 2026-10-16 20:59 | 4,451,650 | 3554 | 1276 | 1 | 55 | 103.89 - 140.75 |
| ZB | 2013-01-02 11:00 | 2026-10-16 20:59 | 4,133,041 | 3554 | 1185 | 2 | 55 | 101.16 - 191.69 |
| 6E | 2013-01-02 11:00 | 2026-10-16 20:59 | 4,730,908 | 3550 | 1352 | 1 | 55 | 0.9592 - 1.3993 |
| 6J | 2013-01-02 11:00 | 2026-10-16 20:59 | 4,715,000 | 3550 | 1353 | 1 | 55 | 0.006123 - 0.01155 |
| NKD | 2013-01-02 11:00 | 2026-10-16 20:59 | 3,284,254 | 3550 | 935 | 9 | 57 | 10390 - 73830 |
| BTC (CME) | 2022-01-02 23:00 | 2026-10-16 21:25 | 1,132,723 | 1279 | 937 | n/a | 57 | 14925 - 127240 (file data/t4/crypto_1m__BTC_v_0.dbn.zst) |
| MBT | 2022-01-02 23:00 | 2026-10-14 23:59 | 1,228,991 | 1278 | 1097 | n/a | 57 | 14935 - 127240 (data/t4/crypto_1m__MBT_v_0.dbn.zst) |
Key facts:
- Only ES, NQ, RTY reach 2026-10-30. YM GC CL ZN ZB 6E 6J NKD end 2026-10-16 (the 10-17..10-30 pull covered the three equity indices only). BTC ends 10-16, MBT 10-14.
- RTY starts 2017-07-09 (10 yearly files, 2017-2026): 9.3 y not 13.8 y. NQ/ES/YM/6E/6J/ZN/ZB/NKD from 2013-01-02; GC/CL from 2013-01-01 23:00 UTC.
- Crypto 1-min starts 2022-01-02: 4.8 y; no 13-year history; BTC trades ~24x5 plus Sunday session (not CME equity hours), so session tables must be separate.
- Short days: 2 (ES NQ) are holiday half-sessions; NKD 9 and GC 8 are holiday/early-close days. Not repaired.
- CL has 165 id changes vs 55 for others: CL `.v.0` volume-front flips between adjacent months more often (and monthly contracts); roll-gap handling matters more for CL (data/databento/CL/roll_gaps_CL.csv).
- Bars in the ET 17:xx hour: ES/NQ/YM/GC/CL 0.2% of bars (holiday/early-close and 2013-era sessions), 6E/6J/ZN/ZB/RTY about 0 (daily maintenance break respected). NKD 0.08%.

## 2. Roll convention and frames
- `.v.0` volume-front continuous (Databento parent->continuous). Raw per-contract frame in ohlcv1m yearly files and out/def parquet (jumps at rolls).
- Back-adjusted additive series in data/databento/<SYM>/series_<SYM>.npz (newest segment raw, offset 0.00; older segments carry offsets, e.g. NQ +292.75 on one roll). Only CL ES GC NQ RTY ZN have series_*.npz, contract_minutes_*.parquet, contract_of_day_*.csv, roll_gaps_*.csv. YM ZB 6E 6J NKD BTC MBT have NO back-adjusted series built: raw frame only; rebuild from instrument_id changes (55-69 rolls) if a path model needs it (cheap, no purchase). Percent-frame convention for 2013-2023.
- Backups: data/databento/{ES,NQ,RTY}/_bak_20261017, _bak_20261025, _bak_20261031.

## 3. Finer data (ticks, 1-s, L2)
| Instrument | 1-s path | Trades (ticks) | mbp-10 / L2 tables | Notes |
|---|---|---|---|---|
| NQ | /mnt/l2/l2vast/instr_1s NQ_S*.npy (6 files, ends 2026-10-16); ds3_g2_redo 1-s path ends 2026-10-30 | data/databento/NQ/trades: 2023-02 .. 2026-10-30 (some months DERIVED_FROM_L2.txt) | tables/NQ/{1min,1s,100ms,100ms_night,sweeps,vpin,events_L13,tape} 2023-02 .. 2026-10 (+ext 10-19..10-30); raw mbp-10 /mnt/l2/l2vast/raw/NQ/{back,ext} | only instrument with full L2 history |
| ES | instr_1s ES_S* ends 2026-10-16 | trades 2023-02 .. 2026-10-30 (derived from L2 parts) | tables/ES 2023-08 .. 2026-10; raw mbp-10 raw/ES | L2 starts 2023-08 |
| RTY | instr_1s RTY_S* ends 2026-10-16 | trades 2023-02 .. 2026-10-30 | tables/RTY 2023-08 .. 2026-10; raw mbp-10 raw/RTY | L2 starts 2023-08 |
| GC CL ZN | instr_1s (6 files each, end 2026-10-16) | trades: 2023-02 (one month) + 2026-10-01..10-12 only | none | ticks are two small windows, not history |
| YM ZB 6E 6J NKD | none | none | none | 1-min only (6E/6J/YM also have daily_outrights only) |
| BTC MBT | none | none | none | 1-min only |
Daily-bar files (data/t4/daily_outrights__*, daily_micros__*): 6A 6B 6C 6E 6J CL ES GC HE HG HO LE M2K M6A M6B M6E MBT MCL MES MET MGC MNQ MYM NG NQ PL RB RTY SI SIL YM ZB ZC ZF ZN ZS ZT ZW (daily only). Micro-scale (MES MNQ M2K MYM MGC MCL M6E MBT) 1-min is NOT separately owned; use the parent outright 1-min with the micro $/pt (same price, 1/10 multiplier); micro liquidity/slippage is a proxy.
Extra 1-min outrights owned (not requested): 6A 6B 6C HE HG HO LE NG PL RB SI ZC ZF ZS ZT ZW (2013-2026).

## 4. Tick size / value and fee line (code/te2_lib.py INSTR; outputs/FEES.md)
| Instrument | $/pt | Tick | Tick $ | Fee line used | Label |
|---|---|---|---|---|---|
| ES | 50 | 0.25 | 12.50 | FEES.md ES: RT $4.34 all-in published NT lifetime | NT-published |
| NQ | 20 | 0.25 | 5.00 | FEES.md NQ standard $4.84 RT = 0.242 pt/lot RT | exchange part PROXY |
| RTY | 50 | 0.10 | 5.00 | no FEES.md line; use M2K/MES-class proxy scaled | PROXY-STD |
| YM | 5 | 1.0 | 5.00 | no FEES.md line | PROXY-STD |
| MES / MNQ / M2K / MYM | 5 / 2 / 5 / 0.5 | .25/.25/.10/1 | 1.25/0.50/0.50/0.50 | FEES.md MES $1.28 RT (NT-published); MNQ M2K PROXY = MES | MES published, rest PROXY |
| GC | 100 | 0.1 | 10.00 | no line | PROXY-STD |
| CL | 1000 | 0.01 | 10.00 | no line (MCL has a PROXY line) | PROXY-STD |
| ZN | 1000 | 1/64 | 15.625 | no line | PROXY-STD |
| ZB | 1000 | 1/32 | 31.25 | no line | PROXY-STD |
| 6E | 125000 | 0.00005 | 6.25 | FEES.md 6E addendum $5.30 RT all-in (commission NT-published; exchange WEAK) + 1 tick/side slippage | exchange part WEAK |
| 6J | 12.5M | 5e-7 | 6.25 | no line | PROXY-STD |
| NKD | 5 | 5 | 25.00 | no line | PROXY-STD |
| MBT | 0.1 | 5.0 | 0.50 | no line | PROXY |
| BTC | 5 | 5 | 25.00 | no line | PROXY |
NKD tick listed per te2_lib (5 index points = $25 per tick on NKD at $5/pt). All PROXY-STD rows must carry the label "proxy fee" in every result row until a statement line exists.

## 5. First/last-bar sanity and DST handling
- First bar of every 2013 file is 2013-01-02 11:00 UTC (06:00 ET) for the Jan-2 start; the first Globex session begins Dec 31 18:00 ET for GC/CL (23:00 UTC), equities/rates/FX start Jan 2. Not a data fault; the 2013 first session is partial.
- Last bar 20:59 UTC on 2026-10-30 (16:59 ET after DST end 11-01 is still EDT: 20:59 UTC = 16:59 EDT); all 10-16 and 10-30 ends are the final RTH-adjacent minute of the Friday session, no truncated last day.
- All timestamps UTC; convert with tz-aware America/New_York (never fixed UTC-4/-5). DST ended 2026-11-01: any file after 10-30 is not yet owned; Globex open moves 22:00Z to 23:00Z.
- No duplicate timestamps; no zero-volume bars; no non-positive prices (min prices above).

## 6. Missing per instrument, and what would need a purchase (NO PURCHASES made; balance $711.74; quotes only if asked)
| Instrument | Missing (research-side, free) | Needs purchase |
|---|---|---|
| ES | none for 1-min; 1-s ends 10-16 | none for 1-min; L2 before 2023-08 would be a purchase |
| NQ | 1-s instr_1s ends 10-16 (ds3_g2_redo has to 10-30) | L2 before 2023-02 |
| RTY | history before 2017-07-09 | NOTHING: quote shows no RTY exists on GLBX.MDP3 before 2017-06 (see DISCOVER_QUOTES_4); 10-31+ |
| YM | 10-17 .. 10-30 1-min; back-adjusted series; 1-s | 1-min 10-17..10-30 (ohlcv-1m, tiny), 1-s/ticks/L2 |
| GC, CL | 10-17 .. 10-30 1-min; ticks only 2023-02 and 2026-10-01..12 | 1-min top-up; trades/L2 history; 1-s |
| ZN, ZB | 10-17 .. 10-30 1-min; ZB no back-adjusted series; ZB no 1-s/ticks | 1-min top-up; ticks/L2 history |
| 6E, 6J | 10-17 .. 10-30 1-min; no back-adjusted series; no 1-s | 1-min top-up; ticks/L2 |
| NKD | 10-17 .. 10-30 1-min; thin overnight bars (median 935/day); no back-adj | 1-min top-up; ticks |
| BTC, MBT | history before 2022-01-02; 10-17 .. 10-30 (BTC), 10-14 .. 10-30 (MBT) | BTC 1-min 2017-12..2021-12 (CME BTC listed 2017-12; MBT listed 2021-05, so MBT has only a 2021 stub before 2022); 1-min top-up |
| MES/MNQ scale | none (parent frame) | none |
Notes: the 10-17..10-30 top-up for the eight non-equity-index instruments is metadata-quote-first; ohlcv-1m for two weeks is the cheapest class of request but I have not asked for a quote. Ticks/L2 for non-NQ instruments are the large costs; the directive's sessions work does not require them if tests use 1-min bars with a 1-tick/side slippage assumption.
## 7. Caveats
- Short-day counts and "missing weekdays" include exchange holidays; the evaluator should key sessions by label day and skip days with <200 bars.
- CL 165 `.v.0` id changes mean the front flips; use roll_gaps_CL.csv/contract_of_day_CL.csv when walking across rolls.
- RTY, YM, 6E etc. raw-frame returns across a roll contain a jump bar; evaluators must mask the roll minute or use series_*.npz where it exists.
