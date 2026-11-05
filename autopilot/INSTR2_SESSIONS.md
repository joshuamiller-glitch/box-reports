# INSTR2_SESSIONS - session tables for T-INSTR-2 (Z2, 2026-11-05). Measurement only; no PASS; nothing live; no purchase.
Scope note l2vast/ds3/prereg/INSTR2_SESSIONS_scope.md sha256 2185a5c1426b7b8a32685e2d017b99d22c835a7ca33f9290ab5f07be22b956be (DECISIONS.md, before any number). Machine-readable: l2vast/ds3/code/instr2/instr2_sessions.json (keys: instruments.<SYM>.sessions / own_liquid_hours_et / extended_hours_et_10pct_of_peak / session_landmarks_et / flat_1655 / tick_value_usd / fee_rt_usd / bucket30_median5vol). Code l2vast/ds3/code/instr2/sessions_build.py, sessions_md.py. Registered: T2_SESSIONS_NTESTED 72 descriptive cells (13 instruments x 6 sessions).
**Clock and data.** America/New_York wall clock from the tz database (DST aware; every number is by ET minute-of-day, not UTC). Sessions = the NQ-analogue clock used by BookHarness.session_of: asia 18:00-02:00, london 02:00-08:30, pre 08:30-09:30, nyam 09:30-12:00, nypm 12:00-15:00, close 15:00-16:55. Data: /mnt/l2/l2vast/ds3/cache_te2/<SYM>.npz 1-minute continuous front month, profile window = last 24 months 2024-10-17..2026-10-16 (the cache ends 2026-10-16; the 10-13..10-31 top-ups in discover_data are not in it); days kept if >= 60% of the median bar count and >= 40% of the median daily volume (holidays / early closes dropped). Volume = contracts in the cache v. ES / RTY / YM are listed with their own numbers but use NQ's clock (the volume profile of all four is the US equity day).
**Rules.** Participation cap = 1.7% of the median 5-minute volume (contracts per 5-minute bar, median over every (day, 5-min bucket) cell of the session incl. empty buckets). LIQUID = volume per hour >= 25% of the instrument's best session-hour AND cap >= 1 contract per 5 min; THIN = >= 10% and cap >= 1; else ILLIQUID. 'rel-only' = the same without the cap condition. ATR14(5m) = Wilder ATR of ET-aligned 5-minute bars (a bar after a gap > 30 minutes uses its own high-low), median over the bars of the session, shown in points, ticks, and $ per lot.
## Plain sentences
* **NQ / ES / RTY / YM:** liquid only 09:30-16:00 ET (nyam, nypm, close; pre is thin for NQ/ES and liquid for RTY/YM); asia and london are illiquid or thin and should not be tested as stand-alone sessions for ES/RTY/YM beyond what NQ does. 16:55 flat is thin-close (post-16:00 volume is about 8-12% of the open hours' per-minute volume).
* **GC:** liquid nearly around the clock except the close (asia and london LIQUID, the COMEX open 08:20 gives the pre/nyam peak, close THIN); the whole 18:00-15:00 clock is testable, but the dollar cap is only 4.6 contracts per 5 min in asia.
* **CL:** liquid from london 03:00 to 15:00 (pit open 09:00 peak), asia and close not; test london / pre / nyam / nypm.
* **ZN / ZB:** liquid 07:00-17:00 with the peak at the 08:20-08:30 release; asia is ILLIQUID by hour-share; the 16:55 flat is COMPATIBLE (volume per minute 28-30% of the liquid hours even at 16:30-16:55).
* **6E:** liquid 02:00-15:30 (London open 02:00 is the landmark); asia thin; close thin; 6J: liquid in every session by hour-share (Tokyo evening 19:00-22:30 and 01:00-16:00).
* **BTC (standard, 5 BTC):** cap < 1 contract per 5 min in EVERY session (0.14-0.9): the 1.7% participation cap cannot be met at 1 lot; relative hours liquid 08:30-16:00 ET. **MBT (micro):** cap 1.3-7.4 contracts per 5 min, LIQUID pre/nyam/nypm/close, THIN asia/london: the tradable crypto leg.
* **NKD:** cap < 1 contract per 5 min in every session (0.12-0.37): NKD cannot meet the 1.7% cap at 1 lot; relative hours liquid in all sessions (flat profile), nyam highest.
## 1. Instrument specification (tick value, fees, slippage proxies)
| instr | $/point | tick (points) | tick value $ | fee RT $/contract | fee source | slippage ticks market / stop (te2 proxy) | profile window | days kept |
|--|--|--|--|--|--|--|--|--|
| NQ | 20 | 0.25 | 5 | 4.84 | FEES.md (NQ exchange fee = ES proxy) | 4 / 4 | 2024-10-17..2026-10-16 | 487 |
| ES | 50 | 0.25 | 12.5 | 4.84 | FEES.md | 1 / 2 | 2024-10-17..2026-10-16 | 489 |
| RTY | 50 | 0.1 | 5 | 4.84 | PROXY-STD (te2_lib; not in FEES.md) | 1 / 2 | 2024-10-17..2026-10-16 | 484 |
| YM | 5 | 1 | 5 | 4.84 | PROXY-STD (te2_lib; not in FEES.md) | 1 / 2 | 2024-10-17..2026-10-16 | 485 |
| GC | 100 | 0.1 | 10 | 4.84 | PROXY-STD (te2_lib; not in FEES.md) | 1 / 2 | 2024-10-17..2026-10-16 | 492 |
| CL | 1000 | 0.01 | 10 | 4.84 | PROXY-STD (te2_lib; not in FEES.md) | 1 / 2 | 2024-10-17..2026-10-15 | 487 |
| ZN | 1000 | 0.015625 | 15.625 | 4.84 | PROXY-STD (te2_lib; not in FEES.md) | 1 / 2 | 2024-10-17..2026-10-16 | 485 |
| ZB | 1000 | 0.03125 | 31.25 | 4.84 | PROXY-STD (te2_lib; not in FEES.md) | 1 / 2 | 2024-10-17..2026-10-16 | 485 |
| 6E | 125000 | 5e-05 | 6.25 | 5.30 | FEES.md 6E addendum (exchange+NFA weak/third-party) | 1 / 2 | 2024-10-17..2026-10-16 | 500 |
| 6J | 1.25e+07 | 5e-07 | 6.25 | 4.84 | PROXY-STD (te2_lib; not in FEES.md) | 1 / 2 | 2024-10-17..2026-10-16 | 503 |
| BTC | 5 | 5 | 25 | 4.84 | PROXY-STD (te2_lib; not in FEES.md) | 2 / 3 | 2024-10-17..2026-10-16 | 482 |
| MBT | 0.1 | 5 | 0.5 | 1.78 | PROXY-MICRO (FEES.md MES value; not CME-published here) | 2 / 3 | 2024-10-17..2026-10-14 | 479 |
| NKD | 5 | 5 | 25 | 4.84 | PROXY-STD (te2_lib; not in FEES.md) | 2 / 3 | 2024-10-17..2026-10-16 | 495 |

Fee labels: FEES.md lists ES 4.84 (NT-published), NQ 4.84 (PROXY ES), MES / MNQ / M2K / MYM 1.78, MCL 2.08 and the 6E addendum 5.30 (exchange+NFA weak). GC, CL, ZN, ZB, 6J, NKD, BTC, RTY, YM are not in FEES.md: the te2_lib standard proxy $4.84 per contract RT is used and LABELLED PROXY (real CME metals / energy / rates / yen fees differ; owners must not claim a fee edge); MBT uses the micro proxy $1.78. Slippage ticks are the te2_lib INSTR values (proxy, not measured).

## 2. Session tables (rows = NQ-analogue sessions; liquid class by the cap rule / rel-only; cap in contracts per 5-minute bar)

### NQ  ($20/pt, tick 0.25 = $5)
| session | ET | share of daily volume | rel. volume/hour | median 5-min volume | cap (1.7%) | class | class rel-only | ATR14(5m) ticks | ATR14(5m) $/lot | class prior window (2022-06..2024-10) |
|--|--|--|--|--|--|--|--|--|--|--|
| asia | 18:00-02:00 | 7.3% | 0.06 | 340.0 | 5.78 | ILLIQUID | ILLIQUID | 45.26 | 226.28 | ILLIQUID |
| london | 02:00-08:30 | 9.2% | 0.09 | 530.0 | 9.01 | ILLIQUID | ILLIQUID | 62.0 | 309.98 | ILLIQUID |
| pre | 08:30-09:30 | 3.7% | 0.23 | 1460.0 | 24.82 | THIN | THIN | 80.97 | 404.83 | LIQUID |
| nyam | 09:30-12:00 | 39.9% | 1.00 | 6427.5 | 109.27 | LIQUID | LIQUID | 146.42 | 732.08 | LIQUID |
| nypm | 12:00-15:00 | 23.7% | 0.49 | 3270.0 | 55.59 | LIQUID | LIQUID | 117.51 | 587.55 | LIQUID |
| close | 15:00-16:55 | 14.1% | 0.46 | 2498.0 | 42.47 | LIQUID | LIQUID | 96.13 | 480.63 | LIQUID |
### ES  ($50/pt, tick 0.25 = $12.5)
| session | ET | share of daily volume | rel. volume/hour | median 5-min volume | cap (1.7%) | class | class rel-only | ATR14(5m) ticks | ATR14(5m) $/lot | class prior window (2022-06..2024-10) |
|--|--|--|--|--|--|--|--|--|--|--|
| asia | 18:00-02:00 | 4.2% | 0.03 | 478.0 | 8.13 | ILLIQUID | ILLIQUID | 8.4 | 104.97 | ILLIQUID |
| london | 02:00-08:30 | 6.9% | 0.07 | 1002.0 | 17.03 | ILLIQUID | ILLIQUID | 11.54 | 144.2 | ILLIQUID |
| pre | 08:30-09:30 | 3.1% | 0.20 | 3048.5 | 51.82 | THIN | THIN | 15.51 | 193.93 | THIN |
| nyam | 09:30-12:00 | 38.8% | 1.00 | 15847.0 | 269.40 | LIQUID | LIQUID | 26.16 | 327.0 | LIQUID |
| nypm | 12:00-15:00 | 24.9% | 0.54 | 8572.0 | 145.72 | LIQUID | LIQUID | 22.92 | 286.44 | LIQUID |
| close | 15:00-16:55 | 19.8% | 0.66 | 7134.0 | 121.28 | LIQUID | LIQUID | 19.8 | 247.45 | LIQUID |
### RTY  ($50/pt, tick 0.1 = $5)
| session | ET | share of daily volume | rel. volume/hour | median 5-min volume | cap (1.7%) | class | class rel-only | ATR14(5m) ticks | ATR14(5m) $/lot | class prior window (2022-06..2024-10) |
|--|--|--|--|--|--|--|--|--|--|--|
| asia | 18:00-02:00 | 3.7% | 0.03 | 46.0 | 0.78 | ILLIQUID | ILLIQUID | 9.92 | 49.6 | ILLIQUID |
| london | 02:00-08:30 | 7.5% | 0.07 | 123.0 | 2.09 | ILLIQUID | ILLIQUID | 15.04 | 75.19 | ILLIQUID |
| pre | 08:30-09:30 | 3.9% | 0.26 | 475.0 | 8.08 | LIQUID | LIQUID | 21.57 | 107.85 | LIQUID |
| nyam | 09:30-12:00 | 39.3% | 1.00 | 1841.0 | 31.30 | LIQUID | LIQUID | 41.54 | 207.68 | LIQUID |
| nypm | 12:00-15:00 | 20.6% | 0.44 | 860.0 | 14.62 | LIQUID | LIQUID | 32.14 | 160.71 | LIQUID |
| close | 15:00-16:55 | 22.2% | 0.74 | 883.0 | 15.01 | LIQUID | LIQUID | 25.43 | 127.14 | LIQUID |
### YM  ($5/pt, tick 1 = $5)
| session | ET | share of daily volume | rel. volume/hour | median 5-min volume | cap (1.7%) | class | class rel-only | ATR14(5m) ticks | ATR14(5m) $/lot | class prior window (2022-06..2024-10) |
|--|--|--|--|--|--|--|--|--|--|--|
| asia | 18:00-02:00 | 6.1% | 0.05 | 46.0 | 0.78 | ILLIQUID | ILLIQUID | 11.53 | 57.66 | ILLIQUID |
| london | 02:00-08:30 | 12.6% | 0.12 | 115.0 | 1.96 | THIN | THIN | 18.36 | 91.79 | THIN |
| pre | 08:30-09:30 | 4.5% | 0.28 | 279.0 | 4.74 | LIQUID | LIQUID | 26.38 | 131.91 | LIQUID |
| nyam | 09:30-12:00 | 40.6% | 1.00 | 1022.0 | 17.37 | LIQUID | LIQUID | 50.13 | 250.65 | LIQUID |
| nypm | 12:00-15:00 | 19.6% | 0.41 | 459.0 | 7.80 | LIQUID | LIQUID | 40.43 | 202.15 | LIQUID |
| close | 15:00-16:55 | 14.0% | 0.46 | 367.0 | 6.24 | LIQUID | LIQUID | 32.87 | 164.35 | LIQUID |
### GC  ($100/pt, tick 0.1 = $10)
| session | ET | share of daily volume | rel. volume/hour | median 5-min volume | cap (1.7%) | class | class rel-only | ATR14(5m) ticks | ATR14(5m) $/lot | class prior window (2022-06..2024-10) |
|--|--|--|--|--|--|--|--|--|--|--|
| asia | 18:00-02:00 | 21.7% | 0.26 | 272.0 | 4.62 | LIQUID | LIQUID | 30.16 | 301.6 | THIN |
| london | 02:00-08:30 | 25.7% | 0.41 | 422.0 | 7.17 | LIQUID | LIQUID | 35.13 | 351.32 | LIQUID |
| pre | 08:30-09:30 | 8.2% | 0.90 | 991.5 | 16.86 | LIQUID | LIQUID | 45.57 | 455.71 | LIQUID |
| nyam | 09:30-12:00 | 23.7% | 1.00 | 1077.0 | 18.31 | LIQUID | LIQUID | 57.19 | 571.89 | LIQUID |
| nypm | 12:00-15:00 | 12.6% | 0.44 | 455.0 | 7.74 | LIQUID | LIQUID | 39.89 | 398.89 | LIQUID |
| close | 15:00-16:55 | 4.2% | 0.22 | 237.5 | 4.04 | THIN | THIN | 29.85 | 298.5 | THIN |
### CL  ($1000/pt, tick 0.01 = $10)
| session | ET | share of daily volume | rel. volume/hour | median 5-min volume | cap (1.7%) | class | class rel-only | ATR14(5m) ticks | ATR14(5m) $/lot | class prior window (2022-06..2024-10) |
|--|--|--|--|--|--|--|--|--|--|--|
| asia | 18:00-02:00 | 8.0% | 0.09 | 106.0 | 1.80 | ILLIQUID | ILLIQUID | 5.43 | 54.28 | ILLIQUID |
| london | 02:00-08:30 | 23.8% | 0.33 | 429.0 | 7.29 | LIQUID | LIQUID | 10.96 | 109.61 | LIQUID |
| pre | 08:30-09:30 | 8.8% | 0.80 | 1088.5 | 18.50 | LIQUID | LIQUID | 13.61 | 136.11 | LIQUID |
| nyam | 09:30-12:00 | 27.6% | 1.00 | 1358.0 | 23.09 | LIQUID | LIQUID | 17.26 | 172.56 | LIQUID |
| nypm | 12:00-15:00 | 24.3% | 0.72 | 872.0 | 14.82 | LIQUID | LIQUID | 14.62 | 146.21 | LIQUID |
| close | 15:00-16:55 | 3.9% | 0.18 | 246.0 | 4.18 | THIN | THIN | 9.28 | 92.76 | THIN |
### ZN  ($1000/pt, tick 0.015625 = $15.625)
| session | ET | share of daily volume | rel. volume/hour | median 5-min volume | cap (1.7%) | class | class rel-only | ATR14(5m) ticks | ATR14(5m) $/lot | class prior window (2022-06..2024-10) |
|--|--|--|--|--|--|--|--|--|--|--|
| asia | 18:00-02:00 | 6.1% | 0.07 | 736.0 | 12.51 | ILLIQUID | ILLIQUID | 1.12 | 17.57 | ILLIQUID |
| london | 02:00-08:30 | 20.6% | 0.28 | 3361.0 | 57.14 | LIQUID | LIQUID | 1.78 | 27.83 | LIQUID |
| pre | 08:30-09:30 | 10.5% | 1.00 | 13611.5 | 231.40 | LIQUID | LIQUID | 2.79 | 43.65 | LIQUID |
| nyam | 09:30-12:00 | 25.8% | 0.94 | 12802.0 | 217.63 | LIQUID | LIQUID | 3.06 | 47.87 | LIQUID |
| nypm | 12:00-15:00 | 20.9% | 0.65 | 7897.0 | 134.25 | LIQUID | LIQUID | 2.48 | 38.77 | LIQUID |
| close | 15:00-16:55 | 10.7% | 0.51 | 6223.0 | 105.79 | LIQUID | LIQUID | 2.08 | 32.49 | LIQUID |
### ZB  ($1000/pt, tick 0.03125 = $31.25)
| session | ET | share of daily volume | rel. volume/hour | median 5-min volume | cap (1.7%) | class | class rel-only | ATR14(5m) ticks | ATR14(5m) $/lot | class prior window (2022-06..2024-10) |
|--|--|--|--|--|--|--|--|--|--|--|
| asia | 18:00-02:00 | 5.3% | 0.06 | 149.0 | 2.53 | ILLIQUID | ILLIQUID | 0.92 | 28.8 | ILLIQUID |
| london | 02:00-08:30 | 19.3% | 0.26 | 701.0 | 11.92 | LIQUID | LIQUID | 1.54 | 48.19 | THIN |
| pre | 08:30-09:30 | 10.6% | 1.00 | 3293.5 | 55.99 | LIQUID | LIQUID | 2.59 | 81.05 | LIQUID |
| nyam | 09:30-12:00 | 26.0% | 0.93 | 3095.5 | 52.62 | LIQUID | LIQUID | 2.87 | 89.83 | LIQUID |
| nypm | 12:00-15:00 | 21.3% | 0.67 | 1981.0 | 33.68 | LIQUID | LIQUID | 2.29 | 71.63 | LIQUID |
| close | 15:00-16:55 | 13.1% | 0.61 | 1646.0 | 27.98 | LIQUID | LIQUID | 1.92 | 60.09 | LIQUID |
### 6E  ($125000/pt, tick 5e-05 = $6.25)
| session | ET | share of daily volume | rel. volume/hour | median 5-min volume | cap (1.7%) | class | class rel-only | ATR14(5m) ticks | ATR14(5m) $/lot | class prior window (2022-06..2024-10) |
|--|--|--|--|--|--|--|--|--|--|--|
| asia | 18:00-02:00 | 10.0% | 0.12 | 122.0 | 2.07 | THIN | THIN | 4.01 | 25.08 | THIN |
| london | 02:00-08:30 | 32.0% | 0.44 | 507.0 | 8.62 | LIQUID | LIQUID | 7.31 | 45.69 | LIQUID |
| pre | 08:30-09:30 | 8.3% | 0.82 | 978.0 | 16.63 | LIQUID | LIQUID | 9.49 | 59.33 | LIQUID |
| nyam | 09:30-12:00 | 26.1% | 1.00 | 1129.0 | 19.19 | LIQUID | LIQUID | 10.79 | 67.45 | LIQUID |
| nypm | 12:00-15:00 | 13.6% | 0.43 | 477.0 | 8.11 | LIQUID | LIQUID | 8.08 | 50.52 | LIQUID |
| close | 15:00-16:55 | 4.6% | 0.23 | 224.0 | 3.81 | THIN | THIN | 5.46 | 34.15 | THIN |
### 6J  ($1.25e+07/pt, tick 5e-07 = $6.25)
| session | ET | share of daily volume | rel. volume/hour | median 5-min volume | cap (1.7%) | class | class rel-only | ATR14(5m) ticks | ATR14(5m) $/lot | class prior window (2022-06..2024-10) |
|--|--|--|--|--|--|--|--|--|--|--|
| asia | 18:00-02:00 | 23.6% | 0.35 | 237.0 | 4.03 | LIQUID | LIQUID | 4.24 | 26.51 | LIQUID |
| london | 02:00-08:30 | 25.4% | 0.46 | 332.0 | 5.64 | LIQUID | LIQUID | 4.97 | 31.07 | LIQUID |
| pre | 08:30-09:30 | 6.8% | 0.82 | 639.0 | 10.86 | LIQUID | LIQUID | 5.85 | 36.53 | LIQUID |
| nyam | 09:30-12:00 | 21.1% | 1.00 | 749.5 | 12.74 | LIQUID | LIQUID | 6.68 | 41.77 | LIQUID |
| nypm | 12:00-15:00 | 12.4% | 0.49 | 338.0 | 5.75 | LIQUID | LIQUID | 4.81 | 30.07 | LIQUID |
| close | 15:00-16:55 | 4.6% | 0.29 | 194.0 | 3.30 | LIQUID | LIQUID | 3.6 | 22.47 | THIN |
### BTC  ($5/pt, tick 5 = $25)
| session | ET | share of daily volume | rel. volume/hour | median 5-min volume | cap (1.7%) | class | class rel-only | ATR14(5m) ticks | ATR14(5m) $/lot | class prior window (2022-06..2024-10) |
|--|--|--|--|--|--|--|--|--|--|--|
| asia | 18:00-02:00 | 16.1% | 0.19 | 8.0 | 0.14 | ILLIQUID | THIN | 21.24 | 530.88 | ILLIQUID |
| london | 02:00-08:30 | 15.8% | 0.22 | 10.0 | 0.17 | ILLIQUID | THIN | 20.76 | 518.99 | ILLIQUID |
| pre | 08:30-09:30 | 4.3% | 0.43 | 22.0 | 0.37 | ILLIQUID | LIQUID | 25.43 | 635.72 | ILLIQUID |
| nyam | 09:30-12:00 | 26.2% | 1.00 | 53.0 | 0.90 | ILLIQUID | LIQUID | 45.06 | 1126.59 | ILLIQUID |
| nypm | 12:00-15:00 | 17.8% | 0.57 | 30.0 | 0.51 | ILLIQUID | LIQUID | 39.64 | 991.1 | ILLIQUID |
| close | 15:00-16:55 | 13.0% | 0.61 | 24.0 | 0.41 | ILLIQUID | LIQUID | 33.43 | 835.72 | ILLIQUID |
### MBT  ($0.1/pt, tick 5 = $0.5)
| session | ET | share of daily volume | rel. volume/hour | median 5-min volume | cap (1.7%) | class | class rel-only | ATR14(5m) ticks | ATR14(5m) $/lot | class prior window (2022-06..2024-10) |
|--|--|--|--|--|--|--|--|--|--|--|
| asia | 18:00-02:00 | 19.5% | 0.23 | 84.0 | 1.43 | THIN | THIN | 25.53 | 12.76 | ILLIQUID |
| london | 02:00-08:30 | 15.1% | 0.21 | 76.0 | 1.29 | THIN | THIN | 24.2 | 12.1 | ILLIQUID |
| pre | 08:30-09:30 | 5.0% | 0.48 | 205.0 | 3.49 | LIQUID | LIQUID | 29.26 | 14.63 | ILLIQUID |
| nyam | 09:30-12:00 | 27.2% | 1.00 | 436.0 | 7.41 | LIQUID | LIQUID | 48.9 | 24.45 | LIQUID |
| nypm | 12:00-15:00 | 16.3% | 0.52 | 216.0 | 3.67 | LIQUID | LIQUID | 43.33 | 21.67 | ILLIQUID |
| close | 15:00-16:55 | 10.2% | 0.51 | 203.0 | 3.45 | LIQUID | LIQUID | 36.68 | 18.34 | ILLIQUID |
### NKD  ($5/pt, tick 5 = $25)
| session | ET | share of daily volume | rel. volume/hour | median 5-min volume | cap (1.7%) | class | class rel-only | ATR14(5m) ticks | ATR14(5m) $/lot | class prior window (2022-06..2024-10) |
|--|--|--|--|--|--|--|--|--|--|--|
| asia | 18:00-02:00 | 30.5% | 0.46 | 8.0 | 0.14 | ILLIQUID | LIQUID | 8.25 | 206.36 | ILLIQUID |
| london | 02:00-08:30 | 22.5% | 0.42 | 8.0 | 0.14 | ILLIQUID | LIQUID | 6.87 | 171.71 | ILLIQUID |
| pre | 08:30-09:30 | 4.1% | 0.51 | 11.0 | 0.19 | ILLIQUID | LIQUID | 6.56 | 164.11 | ILLIQUID |
| nyam | 09:30-12:00 | 20.8% | 1.00 | 22.0 | 0.37 | ILLIQUID | LIQUID | 9.99 | 249.7 | ILLIQUID |
| nypm | 12:00-15:00 | 10.0% | 0.43 | 8.0 | 0.14 | ILLIQUID | LIQUID | 7.76 | 193.99 | ILLIQUID |
| close | 15:00-16:55 | 6.5% | 0.42 | 7.0 | 0.12 | ILLIQUID | LIQUID | 6.2 | 154.95 | ILLIQUID |

## 3. Own liquid hours from the 30-minute volume profile (ET, clock order from 18:00)
| instr | liquid hours (>= 25% of peak 30-min bucket) | extended hours (>= 10% of peak) | landmarks (volume jumps > 2x, >= 15% of peak) | peak 30-min bucket |
|--|--|--|--|--|
| NQ | 09:30-16:00 | 08:30-16:30 | 09:30 | 09:30 (median 5-min vol 10528.5) |
| ES | 09:30-16:00 | 08:30-16:30 | 09:30 | 09:30 (median 5-min vol 23230.5) |
| RTY | 09:30-13:00, 15:00-16:00 | 08:30-16:30 | 09:30 | 09:30 (median 5-min vol 3538.5) |
| YM | 09:30-12:30, 15:30-16:00 | 08:30-16:30 | 09:30 | 09:30 (median 5-min vol 1975.0) |
| GC | 20:00-20:30, 21:00-22:00, 02:00-02:30, 03:00-04:30, 05:00-06:00, 07:00-14:00 | 18:00-16:30 | none | 09:30 (median 5-min vol 1499.0) |
| CL | 03:00-15:00 | 20:00-20:30, 21:00-22:00, 02:00-17:00 | none | 09:30 (median 5-min vol 1461.0) |
| ZN | 03:00-03:30, 07:00-17:00 | 02:00-17:00 | none | 09:30 (median 5-min vol 15147.0) |
| ZB | 07:00-17:00 | 02:00-17:00 | 08:00 | 09:30 (median 5-min vol 3620.5) |
| 6E | 02:00-15:30 | 20:00-22:00, 01:00-16:30 | 02:00 | 10:30 (median 5-min vol 1322.5) |
| 6J | 19:00-22:30, 01:00-16:00 | 18:00-17:00 | none | 10:30 (median 5-min vol 877.0) |
| BTC | 08:30-16:00 | 18:00-23:30, 01:00-01:30, 02:00-17:00 | 09:30 | 09:30 (median 5-min vol 76.0) |
| MBT | 09:00-16:00 | 18:00-23:00, 03:00-03:30, 04:00-04:30, 07:00-17:00 | 09:30 | 09:30 (median 5-min vol 749.5) |
| NKD | 19:00-22:30, 02:00-04:30, 08:00-13:30, 15:30-16:00 | 18:00-17:00 | 09:30, 15:30 | 09:30 (median 5-min vol 36.0) |

## 4. 16:55 ET flat compatibility
| instr | share of days with bars 16:55-16:59 | volume/min 16:30-16:55 vs liquid-session minute | volume share 16:55-17:00 | verdict |
|--|--|--|--|--|
| NQ | 99.4% | 0.08 | 0.11% | THIN-CLOSE |
| ES | 99.4% | 0.08 | 0.12% | THIN-CLOSE |
| RTY | 99.6% | 0.12 | 0.21% | THIN-CLOSE |
| YM | 99.4% | 0.08 | 0.11% | THIN-CLOSE |
| GC | 97.8% | 0.12 | 0.13% | THIN-CLOSE |
| CL | 98.4% | 0.12 | 0.13% | THIN-CLOSE |
| ZN | 99.6% | 0.28 | 0.30% | COMPATIBLE |
| ZB | 99.4% | 0.30 | 0.30% | COMPATIBLE |
| 6E | 99.4% | 0.10 | 0.15% | THIN-CLOSE |
| 6J | 99.2% | 0.14 | 0.11% | THIN-CLOSE |
| BTC | 98.5% | 0.15 | 0.14% | THIN-CLOSE |
| MBT | 99.8% | 0.23 | 0.27% | THIN-CLOSE |
| NKD | 97.6% | 0.15 | 0.19% | THIN-CLOSE |

Reading: every instrument trades through 16:59 ET (bars on >= 97% of days), so the 16:55 flat is executable everywhere; it is COMPATIBLE (late volume per minute >= 25% of the liquid hours) only for ZN and ZB; for the equity indices, GC, CL, 6E, 6J, MBT, BTC and NKD the 16:30-16:55 volume per minute is 8-23% of the liquid-session level (THIN-CLOSE): the flat is possible but costs more than at the open hours (use the instrument's stop-slippage x1.5 as a stress). For 24-hour style markets (6E, 6J, GC, BTC, MBT, NKD, CL) 16:55 falls mid-day of the liquid clock; positions opened in asia / london are flat by 16:55 anyway.

## 5. Candidate session clocks for the owners' per-session tables (recent windows first, as RECENTS)
| instr | sessions to test (LIQUID/THIN, in clock order) | notes |
|--|--|--|
| NQ | nyam, nypm, close (pre thin; asia / london only for the six live books) |  |
| ES | nyam, nypm, close (pre thin; NQ clock) |  |
| RTY | pre, nyam, nypm, close (NQ clock) |  |
| YM | pre, nyam, nypm, close (NQ clock) |  |
| GC | asia, london, pre, nyam, nypm, close | COMEX open 08:20 (inside pre) is the volume peak; consider splitting pre into 08:20-09:30 |
| CL | london, pre, nyam, nypm, close | pit open 09:00 inside pre/nyam; asia ILLIQUID |
| ZN | london, pre, nyam, nypm, close | release 08:30 inside pre; close session liquid (rates trade to 16:00 cash close then thin) |
| ZB | london, pre, nyam, nypm, close | release 08:30 inside pre; close session liquid (rates trade to 16:00 cash close then thin) |
| 6E | asia, london, pre, nyam, nypm, close | London open 02:00 landmark; close thin |
| 6J | asia, london, pre, nyam, nypm, close | Tokyo evening 19:00-22:30 plus London; flat profile |
| BTC | asia, london, pre, nyam, nypm, close | cap < 1 contract per 5 min in every session: cannot trade 1 lot within 1.7% (BTC: use MBT; NKD: report as cap-infeasible unless the owner uses a larger cap); sessions listed by relative volume only |
| MBT | asia, london, pre, nyam, nypm, close | micro: asia / london THIN |
| NKD | asia, london, pre, nyam, nypm, close | cap < 1 contract per 5 min in every session: cannot trade 1 lot within 1.7% (BTC: use MBT; NKD: report as cap-infeasible unless the owner uses a larger cap); sessions listed by relative volume only |

Stability: the 'class prior window' column compares with 2022-06..2024-10; where it differs from the current class the session boundary of liquidity moved (BTC/MBT exist only from 2022-01). The cache is front-month continuous; roll days are inside the volume (not removed).

## 6. How to use
Per-session tables for T-INSTR-2 should use these ET sessions with their own LIQUID/THIN lists; lots cap = floor(cap_per5min) lots per 5-minute bar of participation (the 1.7% rule) in addition to the equal-$-risk lots; $ risk per lot in ATR terms = atr14_5m_usd above (typical stop 2-6 x that). Fees are proxies except where labelled. No PASS; nothing live.

## 7. Finalist re-run engine (Z2) - request interface
`l2vast/ds3/code/instr2/tick_rerun.py` (self-test passes: random-side entries on ES / RTY / ZN / GC / CL give net per trade near minus the cost proxy, no systematic gain). Interface: `TR.rerun(sym, trades)` with `trades` = DataFrame(sec = epoch of the 1-min bar close B, side +-1, stop_pts, tgt_pts (NaN = none), lots, optional tstop_s) for sym in ES, RTY, ZN, GC, CL (and NQ) on the tick-built 1-s paths /mnt/l2/l2vast/instr_1s (seconds with prints, to 2026-10-16). Live fill model: first fill at the last print <= B + 1 s, 1 lot every 2 s, resting stop / target on the first fill, stop +s ticks and market +m ticks adverse (te2_lib proxy values), fee from instr2_sessions.json (FEES.md where listed, else labelled proxy), flat 16:55 ET (DST aware), no overlap per list. Returns `R.trades` (net_pts, usd, etype, session, ld) and `R.daily` (label-day $); `TR.weekly(R, lo, hi)` gives weekly $ for a window. Owners: append requests to autopilot/INSTR2_RERUN_REQUESTS.md (">>") with the trade-list path; Z2 returns the 16-column rows within the hour. YM has no ticks; NKD / 6J have 1-s bars from the lean purchase (not in instr_1s) and NKD trades.

## 8. Evaluator-ready keys (added 2026-11-05 for instr2_eval.py)
instr2_sessions.json instruments.<SYM> now also carries: `session_def` ({session: [start_min_ET, end_min_ET]}, all six NQ-analogue sessions; asia wraps midnight [1080, 120]) and `session_def_liquid` (the sessions to test: LIQUID/THIN by the cap rule, relative-volume classes for BTC / NKD), `max_lots_per_5min` (floor of the 1.7% cap per session, for `max_lots`), and `cost_pts` {fee_pts, market_entry_slip_pts, stop_exit_slip_pts, market_exit_slip_pts, rt_market_in_market_out, rt_market_in_stop_out} (use rt_market_in_stop_out as the conservative `cost_pts`; slippage ticks are te2_lib PROXIES). Example: `S = json.load(open('.../instr2_sessions.json'))['instruments']['GC']; E.evaluate(tr, ..., session_def={k: tuple(v) for k, v in S['session_def_liquid'].items()})`.
