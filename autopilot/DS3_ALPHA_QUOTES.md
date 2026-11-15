# DS3_ALPHA_QUOTES - Databento QUOTES ONLY (metadata.get_cost), nothing bought
VERDICT (data ends 2026-11-13; plain): ohlcv-1s and ohlcv-1m are $0.00 on the plan for EVERY market and year in the order's list (so 1-minute and 1-second history for all 31 symbols from 2023-04 is free to pull); top-of-book (tbbo) for the liquid set is a few hundred dollars; full-year mbp-10 for everything is about $14.9k and is not recommended. Quote date 2026-11-15; data window quoted 2023-04-01..2026-11-15; box . No purchase made; no pull made (user decides).

Method: Databento Historical metadata.get_cost, dataset GLBX.MDP3, front-month by volume continuous symbol (SYM.v.0), one call per symbol x schema x year (2023 = Apr-Dec). API key from env only, never printed. Raw numbers: /mnt/l2/l2vast/_alpha_breadth/quotes.json (cost, record count, billable bytes per call); code code/th_alpha_breadth/quotes.py.

## Total by symbol and schema, USD, 2023-04-01..2026-11-15 (0.0 = $0.00 on the current plan)
| sym | ohlcv-1s | ohlcv-1m | trades | tbbo | mbp-1 | mbp-10 |
|---|---|---|---|---|---|---|
| 6A | 0.0 | 0.0 | 19.3 | 32.1 | 79.2 | 174.8 |
| 6B | 0.0 | 0.0 | 17.8 | 29.7 | 63.8 | 139.0 |
| 6C | 0.0 | 0.0 | 13.8 | 22.9 | 46.1 | 96.6 |
| 6E | 0.0 | 0.0 | 41.2 | 68.6 | 130.5 | 275.2 |
| 6J | 0.0 | 0.0 | 33.1 | 55.2 | 93.1 | 190.9 |
| BTC | 0.0 | 0.0 | 5.7 | 9.4 | 59.3 | 497.1 |
| CL | 0.0 | 0.0 | 83.2 | 138.6 | 152.9 | 367.1 |
| ES | 0.0 | 0.0 | 352.0 | 586.6 | 570.4 | 1404.8 |
| ETH | 0.0 | 0.0 | 4.3 | 7.1 | 43.0 | 310.4 |
| GC | 0.0 | 0.0 | 79.8 | 133.0 | 115.9 | 396.4 |
| HG | 0.0 | 0.0 | 23.9 | 39.8 | 41.3 | 118.1 |
| HO | 0.0 | 0.0 | 16.4 | 27.4 | 39.8 | 191.7 |
| M2K | 0.0 | 0.0 | 36.8 | 61.3 | 156.1 | 397.8 |
| MBT | 0.0 | 0.0 | 15.3 | 25.6 | 101.5 | 678.3 |
| MCL | 0.0 | 0.0 | 27.9 | 46.6 | 97.0 | 277.4 |
| MES | 0.0 | 0.0 | 249.5 | 415.8 | 542.4 | 1286.2 |
| MGC | 0.0 | 0.0 | 64.0 | 106.6 | 167.2 | 521.8 |
| MNQ | 0.0 | 0.0 | 577.2 | 962.0 | 1357.8 | 3827.9 |
| MYM | 0.0 | 0.0 | 49.0 | 81.6 | 253.7 | 605.0 |
| NG | 0.0 | 0.0 | 37.2 | 62.0 | 38.8 | 129.1 |
| NKD | 0.0 | 0.0 | 3.9 | 6.5 | 25.7 | 70.0 |
| RB | 0.0 | 0.0 | 16.4 | 27.3 | 42.5 | 182.7 |
| RTY | 0.0 | 0.0 | 79.2 | 131.9 | 202.1 | 586.5 |
| SI | 0.0 | 0.0 | 25.9 | 43.1 | 64.0 | 235.4 |
| YM | 0.0 | 0.0 | 68.1 | 113.5 | 212.1 | 518.7 |
| ZB | 0.0 | 0.0 | 39.8 | 66.4 | 103.8 | 220.5 |
| ZC | 0.0 | 0.0 | 13.2 | 22.0 | 15.4 | 36.9 |
| ZF | 0.0 | 0.0 | 66.8 | 111.3 | 158.2 | 363.0 |
| ZN | 0.0 | 0.0 | 81.2 | 135.3 | 182.0 | 424.9 |
| ZS | 0.0 | 0.0 | 19.5 | 32.5 | 26.3 | 66.2 |
| ZT | 0.0 | 0.0 | 31.0 | 51.7 | 92.1 | 270.0 |
| ZW | 0.0 | 0.0 | 11.1 | 18.5 | 14.1 | 37.8 |

Schema totals (all 32 symbols): trades $2204; tbbo $3672; mbp-1 $5288; mbp-10 $14898; ohlcv-1s / ohlcv-1m $0.

## By year, all symbols, USD
| sym | 2023 | 2024 | 2025 | 2026 |
|---|---|---|---|---|
| mbp-1 | 1372.0 | 1937.0 | 1979.0 | 0.0 |
| mbp-10 | 2317.0 | 3524.0 | 4420.0 | 4639.0 |
| ohlcv-1m | 0.0 | 0.0 | 0.0 | 0.0 |
| ohlcv-1s | 0.0 | 0.0 | 0.0 | 0.0 |
| tbbo | 909.0 | 1350.0 | 1412.0 | 0.0 |
| trades | 546.0 | 810.0 | 847.0 | 0.0 |

Reading: trades, tbbo and mbp-1 are $0.00 for 2026 (the plan appears to cover roughly the most recent months of those schemas; the 2025 rows are charged but may be partly inside the free window: quote a 2025-11..2025-12 slice before buying). mbp-10 is charged in every year. 1-second and 1-minute bars are free everywhere.

## Per year for the five markets nearest the recommended set (USD)
| sym | 2023 | 2024 | 2025 | 2026 |
|---|---|---|---|---|
| ('CL', 'mbp-10') | 91.2 | 107.5 | 78.5 | 90.0 |
| ('CL', 'tbbo') | 44.1 | 54.9 | 39.7 | 0.0 |
| ('ES', 'mbp-10') | 246.9 | 350.6 | 427.4 | 379.9 |
| ('ES', 'tbbo') | 155.8 | 206.7 | 224.2 | 0.0 |
| ('GC', 'mbp-10') | 60.1 | 86.6 | 110.0 | 139.7 |
| ('GC', 'tbbo') | 31.2 | 48.7 | 53.1 | 0.0 |
| ('YM', 'mbp-10') | 100.7 | 149.1 | 149.8 | 119.1 |
| ('YM', 'tbbo') | 36.8 | 44.6 | 32.0 | 0.0 |
| ('ZN', 'mbp-10') | 75.3 | 108.6 | 122.3 | 118.8 |
| ('ZN', 'tbbo') | 33.4 | 52.7 | 49.3 | 0.0 |

## RECOMMENDED MINIMAL SET (a recommendation; the user decides, nothing bought)
1. $0.00: pull ohlcv-1m for the 10 missing/short series (see inventory in DS3_ALPHA_BREADTH.md: RTY 2013-01..2017-07 is absent; ZT ZF ZC ZS ZW HG PL HO RB NG LE HE 6A 6B 6C end 2026-10-16, ZN ZB 6E 6J NKD end 2026-11-10: top-ups to today) and for the symbols not on the box at all: MES MNQ M2K MYM MCL MGC BTC ETH (CME crypto futures). All $0.00 per this quote. Also ohlcv-1s for the markets that feed a 1-minute model with sub-minute detail.
2. About $760: tbbo 2023-04..2026-11 for YM ZN ZB 6E 6J GC CL NKD SI (YM 113.5, ZN 135.3, ZB 66.4, 6E 68.6, 6J 55.2, GC 133.0, CL 138.6, NKD 6.5, SI 43.1). tbbo gives the measured half-spread and the quote side for the passive-entry fill study (item 14) and a trade-sign (order-flow) input. ES RTY NQ top-of-book already exist inside the box's mbp-10 replicas, so no tbbo is needed for them.
3. About $456 more if trade-by-trade prints are wanted for the same nine (trades: YM 68.1, ZN 81.2, ZB 39.8, 6E 41.2, 6J 33.1, GC 79.8, CL 83.2, NKD 3.9, SI 25.9). tbbo already carries trade price and size at each trade, so this is optional.
4. Depth (mbp-10) only if the first-pass results say depth matters in NQ (W-AL1's block ablation): the full-history price for the most liquid, 2023-04..2026-11, is ES $1,405, MNQ $3,828 (not recommended), CL $367, GC $396, 6E $275, ZN $425, YM $519, RTY $587; every mbp-10 quote is in the table above. NQ, ES and RTY depth is already on the box.
Recommended spend: $0 for step 1; about $760 for step 2; about $1,216 including step 3.
