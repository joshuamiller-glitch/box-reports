# INSTR_SCALING: scaling and cost note for every T-INSTR slice (Z1, 2026-11-03T19:53Z) RESEARCH ONLY, no PASS, Shadow only
Order: USER P2 = T-INSTR (autopilot/DIRECTIVE_P1_P2_20261104.md). Read this before defining any instrument book. Numbers come from the 1-min Databento bars on disk (tc/cache parquet; ATR windows that contain a roll bar are dropped), 5-minute bars, ATR14 = 14-bar mean true range, median over 2023-04-03..2026-10-16 (NQ to 10-30), code l2vast/ds3/code/instr_sc/ (atr.py, sess.py, warm.py, drift.py, scaling.py), tables in l2vast/ds3/out/instr_sc/. Ledger: INSTR_SC.

## Recommendation in six lines
1. Translate EVERY NQ point constant (60/60 stop and target, 10-pt break, 20/25-pt distances, TH-L2 30-pt arm and its 20/40 variants, any other point threshold) by ONE factor f_i = median ATR14(5m)_instrument / median ATR14(5m)_NQ (ATR-ratio scaling), rounded to the nearest tick with a floor of 2 ticks. Keltner/ATR/EMA lengths in bars, ER, R multiples and all percentages stay unchanged. The NQ stop is 60 pt = 4.14 ATR14(5m) overall (1.9 ATR in nyam, 6.9 in asia), so the mapped stop is 4.14 ATR of the instrument at all times of day.
2. PRIMARY f_i = the full-sample ratio in table 1 (it is a unit conversion, not fitted to P&L, but it uses the scoring window); MANDATORY sensitivities: (S1) the warm-up ratio from 2022-06..2023-03 (no look-ahead; table 8); (S2) bps-of-price scaling (f = price_i / price_NQ). Optional: the per-session ratio (table 2) and the stop x0.75 / x1.33 neighbours. A slice whose verdict flips between primary and S1/S2 is FRAGILE.
3. Lots at equal dollar risk: lots_i = NQ risk $ / (mapped stop $ per contract); one NQ lot ($1,200 to the 60-pt stop) = ATR$ ratio lots (table 4: ES 2.05, RTY 3.67, YM 3.19, ZN 9.98, ZB 5.41, 6E 7.82, 6J 9.83, GC 1.36, CL 2.78, NKD 1.95, MBT 23.9). Research with fractional lots (fees x lots); live-form rounding to the nearest integer, min 1, and a participation cap of 1.7% of the instrument's median 5-min volume per entry (the NQ PE 11-lot entry is 1.7% of NQ volume).
4. Costs: BASE market cost = max(ATR-scaled NQ 0.80 pt, 1 tick; thin 2), stop slip = max(ATR-scaled NQ 2.45 pt, 2 ticks; thin 3), fee per FEES.md or the labelled class estimate; STRESS = 2x slippage and 2x fee; LITERAL (harsh bound) = NQ's 3.2 / 9.8 ticks on every instrument.
5. Books run by the NQ ET session tags (asia 18:00-02:00, london 02:00-08:30, pre 08:30-09:30, nyam 09:30-12:00, nypm 12:00-15:00, close 15:00-16:54), no entries 16:55-18:00; the 17:00-18:00 ET break is confirmed in the data of all 13 instruments.
6. Structural warnings the slices must carry: rates (ZN, ZB) map to a 7-8 tick stop where round-trip BASE cost is 43-44% of the stop distance; NKD (12 contracts per 5 min) and MBT/BTC are too thin for the NQ participation cap; the relative volatility of every instrument against NQ drifted by factors 0.4-1.9 between the warm-up and the full sample (table 8), so the mapped stop is not the same number of ATRs in every window.

## 1. Tick, $ per point and volatility; ATR ratio, bps ratio
| instrument | tick | $/pt | $/tick | median price | median ATR14(5m) | ATR in ticks | ATR in $ per contract | ATR in bps | ATR ratio f_atr (vs NQ) | bps ratio f_bps | 5-min volume (median) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ | 0.25 | 20 | 5.00 | 20669 | 14.48 | 57.9 | 290 | 7.01 | 1 | 1 | 647 |
| ES | 0.25 | 50 | 12.50 | 5866.8 | 2.821 | 11.3 | 141 | 4.81 | 0.1948 | 0.2838 | 1175 |
| RTY | 0.1 | 50 | 5.00 | 2208 | 1.579 | 15.8 | 79 | 7.15 | 0.109 | 0.1068 | 152 |
| YM | 1 | 5 | 5.00 | 42532 | 18.14 | 18.1 | 91 | 4.27 | 1.253 | 2.058 | 143 |
| ZN | 0.01562 | 1000 | 15.62 | 110.88 | 0.02902 | 1.9 | 29 | 2.62 | 0.002004 | 0.005364 | 2851 |
| ZB | 0.03125 | 1000 | 31.25 | 116.47 | 0.05357 | 1.7 | 54 | 4.60 | 0.003699 | 0.005635 | 630 |
| 6E | 5e-05 | 1.25e+05 | 6.25 | 1.1037 | 0.0002964 | 5.9 | 37 | 2.69 | 2.047e-05 | 5.34e-05 | 362 |
| 6J | 5e-07 | 1.25e+07 | 6.25 | 0.0066815 | 2.357e-06 | 4.7 | 29 | 3.53 | 1.628e-07 | 3.233e-07 | 325 |
| GC | 0.1 | 100 | 10.00 | 2748.2 | 2.129 | 21.3 | 213 | 7.75 | 0.147 | 0.133 | 365 |
| CL | 0.01 | 1000 | 10.00 | 73.61 | 0.1043 | 10.4 | 104 | 14.17 | 0.007201 | 0.003561 | 355 |
| NKD | 5 | 5 | 25.00 | 38940 | 29.64 | 5.9 | 148 | 7.61 | 2.047 | 1.884 | 12 |
| MBT | 5 | 0.1 | 0.50 | 69680 | 121.1 | 24.2 | 12 | 17.38 | 8.36 | 3.371 | 68 |
Reading: NQ moves 14.5 pt (58 ticks, $290) per 5-min ATR; the same ATR is 11 ticks ($141) in ES, 1.9 ticks ($29) in ZN, 4.7 ticks ($29) in 6J, 24 ticks ($12) in MBT. The ATR ratio and the bps ratio agree for RTY and GC (within 10%), differ by 1.5x for ES, ZB and YM (1.6x), 2.6x for 6E and ZN, 0.5x for 6J, 2.0x for CL and 2.5x for MBT.

### Why the ATR ratio and not bps or tick count
- Tick count (NQ 240 ticks) makes ES a $3,000 stop, ZN $3,750, MBT $120: meaningless risk and no relation to the instrument's own range (the stop would be 25 ATR in ES).
- bps of price (60/20,669 = 29 bp) ties the stop to price level, but volatility per bp differs by instrument and drifts: ZN price 111 gives a 21-tick stop = 11 ATR (almost never hit), CL a 21-tick stop = 2 ATR (hit constantly), MBT 40 ticks = 1.7 ATR. The book's trade statistics (hit rates, durations, TH-L2 cut frequency) are functions of stop / ATR, so the ATR ratio is the mapping that keeps the same logic. bps is kept as a sensitivity because it is the price-level analogue.
- The ATR ratio is NOT free of drift: NQ price rose from 11.9k (warm-up) to 20.7k (full), its point volatility rose with it, while GC and NKD vol rose more and rates/FX/crypto less (table 8). That is why the warm-up ratio is a mandatory sensitivity.

### Session dispersion of the ratio (sensitivity variant)
| instrument | asia | london | pre | nyam | nypm | close | max/min over sessions | overall f_atr |
|---|---|---|---|---|---|---|---|---|
| NQ | 1 | 1 | 1 | 1 | 1 | 1 | 1.00 | 1 |
| ES | 0.1947 | 0.1994 | 0.2053 | 0.185 | 0.2044 | 0.2154 | 1.16 | 0.1948 |
| RTY | 0.1016 | 0.1166 | 0.1283 | 0.1346 | 0.1187 | 0.1137 | 1.32 | 0.109 |
| YM | 1.131 | 1.299 | 1.356 | 1.475 | 1.459 | 1.463 | 1.30 | 1.253 |
| ZN | 0.002305 | 0.002549 | 0.003142 | 0.001651 | 0.001686 | 0.001661 | 1.90 | 0.002004 |
| ZB | 0.003842 | 0.004343 | 0.006016 | 0.003231 | 0.003168 | 0.003093 | 1.94 | 0.003699 |
| 6E | 2.213e-05 | 3.021e-05 | 2.995e-05 | 1.758e-05 | 1.504e-05 | 1.137e-05 | 2.66 | 2.047e-05 |
| 6J | 2.541e-07 | 2.115e-07 | 2.032e-07 | 1.172e-07 | 9.812e-08 | 8.066e-08 | 3.15 | 1.628e-07 |
| GC | 0.1877 | 0.1692 | 0.1985 | 0.1179 | 0.09747 | 0.07296 | 2.72 | 0.147 |
| CL | 0.006311 | 0.009366 | 0.008856 | 0.006571 | 0.006738 | 0.003813 | 2.46 | 0.007201 |
| NKD | 4.139 | 2.054 | 1.476 | 1.241 | 1.194 | 1.173 | 3.53 | 2.047 |
| MBT | 13.03 | 8.369 | 7.604 | 6.766 | 7.375 | 7.076 | 1.93 | 8.36 |
Ratios by NQ session tag differ most for NKD (3.5x between sessions), 6J (3.2x), GC (2.7x), 6E (2.7x), CL (2.5x), ZN/ZB (1.9x); ES, RTY, YM within 1.3x. For those instruments a per-session factor is the second sensitivity; the primary keeps one factor so the instrument book has the same fixed-distance property as the NQ book (60 pt in every session).

### Table 8. ATR-ratio stability
| instrument | f_atr full sample 2023-04..2026-10 (PRIMARY) | f_atr warm-up 2022-06..2023-03 (no look-ahead) | warm-up / full | L12M / full | L6M / full | stop 60 pt in ATR multiples, L12M | in L6M |
|---|---|---|---|---|---|---|---|
| ES | 0.1948 | 0.2634 | 1.35 | 0.88 | 0.78 | 4.7 | 5.3 |
| RTY | 0.109 | 0.1337 | 1.23 | 0.82 | 0.74 | 5.1 | 5.6 |
| YM | 1.253 | 1.823 | 1.46 | 0.86 | 0.78 | 4.8 | 5.3 |
| ZN | 0.002004 | 0.003437 | 1.72 | 0.61 | 0.56 | 6.8 | 7.4 |
| ZB | 0.003699 | 0.006151 | 1.66 | 0.58 | 0.53 | 7.2 | 7.8 |
| 6E | 2.047e-05 | 3.849e-05 | 1.88 | 0.61 | 0.50 | 6.8 | 8.2 |
| 6J | 1.628e-07 | 2.923e-07 | 1.80 | 0.51 | 0.37 | 8.1 | 11.3 |
| GC | 0.147 | 0.09146 | 0.62 | 1.56 | 1.29 | 2.7 | 3.2 |
| CL | 0.007201 | 0.0136 | 1.89 | 1.01 | 1.20 | 4.1 | 3.5 |
| NKD | 2.047 | 1.245 | 0.61 | 1.24 | 1.33 | 3.3 | 3.1 |
| MBT | 8.36 | 3.329 | 0.40 | 0.69 | 0.50 | 6.0 | 8.2 |

Reading: the 60-pt NQ stop equals 4.14 ATR(NQ); in the last 12 months the mapped stop is 6.8 ATR of ZN, 6.8 of 6E, 8.1 of 6J, 2.7 of GC. Slices must quote results in the primary scaling and report S1 and S2 beside it.

## 1b. NQ point constants translated (ATR-ratio, nearest tick, min 2 ticks; units = instrument price units, t = ticks)
| NQ constant (pts) | ES | RTY | YM | ZN | ZB | 6E | 6J | GC | CL | NKD | MBT |
|---|---|---|---|---|---|---|---|---|---|---|---|
| stop / target 60 | 11.75 (47 t) | 6.5 (65 t) | 75 (75 t) | 0.125 (8 t) | 0.2188 (7 t) | 0.00125 (25 t) | 1e-05 (20 t) | 8.8 (88 t) | 0.43 (43 t) | 125 (25 t) | 500 (100 t) |
| TH-L2 arm cut (adverse excursion) 30 | 5.75 (23 t) | 3.3 (33 t) | 38 (38 t) | 0.0625 (4 t) | 0.125 (4 t) | 0.0006 (12 t) | 5e-06 (10 t) | 4.4 (44 t) | 0.22 (22 t) | 60 (12 t) | 250 (50 t) |
| TH-L2 arm 20 / 40 variants 20 | 4 (16 t) | 2.2 (22 t) | 25 (25 t) | 0.04688 (3 t) | 0.0625 (2 t) | 0.0004 (8 t) | 3.5e-06 (7 t) | 2.9 (29 t) | 0.14 (14 t) | 40 (8 t) | 165 (33 t) |
| distance D (zones, OTE) 25 | 4.75 (19 t) | 2.7 (27 t) | 31 (31 t) | 0.04688 (3 t) | 0.09375 (3 t) | 0.0005 (10 t) | 4e-06 (8 t) | 3.7 (37 t) | 0.18 (18 t) | 50 (10 t) | 210 (42 t) |
| break 10 | 2 (8 t) | 1.1 (11 t) | 13 (13 t) | 0.03125 (2 t) | 0.0625 (2 t) | 0.0002 (4 t) | 1.5e-06 (3 t) | 1.5 (15 t) | 0.07 (7 t) | 20 (4 t) | 85 (17 t) |
| 40 40 | 7.75 (31 t) | 4.4 (44 t) | 50 (50 t) | 0.07812 (5 t) | 0.1562 (5 t) | 0.0008 (16 t) | 6.5e-06 (13 t) | 5.9 (59 t) | 0.29 (29 t) | 80 (16 t) | 335 (67 t) |
Stop-per-instrument under the three mappings (equal-risk lots per NQ lot beside):
| instrument | stop ATR-scaled (units / ticks / $ per contract / bps / ATR multiples) | stop bps-scaled (units / ticks / $) | stop tick-literal 240 ticks ($) | equal-risk lots per NQ lot (ATR) | (bps) |
|---|---|---|---|---|---|
| NQ | 60 / 240 / $1200 / 29.0 bp / 4.14 ATR | 60 / 240 / $1200 | $1200 | 1.00 | 1.00 |
| ES | 11.69 / 47 / $584 / 19.9 bp / 4.14 ATR | 17.03 / 68 / $852 | $3000 | 2.05 | 1.41 |
| RTY | 6.54 / 65 / $327 / 29.6 bp / 4.14 ATR | 6.41 / 64 / $320 | $1200 | 3.67 | 3.74 |
| YM | 75.17 / 75 / $376 / 17.7 bp / 4.14 ATR | 123.5 / 123 / $617 | $1200 | 3.19 | 1.94 |
| ZN | 0.1202 / 8 / $120 / 10.8 bp / 4.14 ATR | 0.3219 / 21 / $322 | $3750 | 9.98 | 3.73 |
| ZB | 0.2219 / 7 / $222 / 19.1 bp / 4.14 ATR | 0.3381 / 11 / $338 | $7500 | 5.41 | 3.55 |
| 6E | 0.001228 / 25 / $154 / 11.1 bp / 4.14 ATR | 0.003204 / 64 / $400 | $1500 | 7.82 | 3.00 |
| 6J | 9.766e-06 / 20 / $122 / 14.6 bp / 4.14 ATR | 1.94e-05 / 39 / $242 | $1500 | 9.83 | 4.95 |
| GC | 8.819 / 88 / $882 / 32.1 bp / 4.14 ATR | 7.978 / 80 / $798 | $2400 | 1.36 | 1.50 |
| CL | 0.4321 / 43 / $432 / 58.7 bp / 4.14 ATR | 0.2137 / 21 / $214 | $2400 | 2.78 | 5.62 |
| NKD | 122.8 / 25 / $614 / 31.5 bp / 4.14 ATR | 113 / 23 / $565 | $6000 | 1.95 | 2.12 |
| MBT | 501.6 / 100 / $50 / 72.0 bp / 4.14 ATR | 202.3 / 40 / $20 | $120 | 23.92 | 59.32 |

## 2. Lots at equal dollar risk, notional and liquidity caps
Rule: lots_i = (NQ lots x $1,200) / (mapped stop distance x $/pt of the instrument), where the NQ book lots are the live Q1-A traded lots (PE 11/7/4/2, SM 6, KB 1-2 ...). Because the lock/R convention is dollar-based (R_book $), the daily +-R caps, the week floor and the TH-L2 dollar-based features transfer unchanged when R$ of the instrument book is set equal to the NQ book's R$; the lock R scaling stays 'never scaled under Q1-A'.
| instrument | lots per 1 / 2 / 4 / 7 NQ lots (ATR scaling, fractional) | integer (nearest, min 1) | notional vs NQ at equal risk | participation cap lots (1.7% of median 5-min volume) | verdict |
|---|---|---|---|---|---|
| NQ | 1.00 / 2.00 / 4.00 / 7.00 | 1 / 2 / 4 / 7 | x1.00 | 11.0 | ok |
| ES | 2.05 / 4.11 / 8.21 / 14.37 | 2 / 4 / 8 / 14 | x1.46 | 20.0 | ok |
| RTY | 3.67 / 7.34 / 14.68 / 25.69 | 4 / 7 / 15 / 26 | x0.98 | 2.6 | too thin: cap below the 2-lot book |
| YM | 3.19 / 6.39 / 12.77 / 22.35 | 3 / 6 / 13 / 22 | x1.64 | 2.4 | too thin: cap below the 2-lot book |
| ZN | 9.98 / 19.96 / 39.93 / 69.87 | 10 / 20 / 40 / 70 | x2.68 | 48.5 | cap binds for the 7-lot book |
| ZB | 5.41 / 10.81 / 21.63 / 37.85 | 5 / 11 / 22 / 38 | x1.52 | 10.7 | too thin: cap below the 2-lot book |
| 6E | 7.82 / 15.63 / 31.27 / 54.72 | 8 / 16 / 31 / 55 | x2.61 | 6.2 | too thin: cap below the 2-lot book |
| 6J | 9.83 / 19.66 / 39.32 / 68.81 | 10 / 20 / 39 / 69 | x1.99 | 5.5 | too thin: cap below the 2-lot book |
| GC | 1.36 / 2.72 / 5.44 / 9.53 | 1 / 3 / 5 / 10 | x0.90 | 6.2 | cap binds for the 7-lot book |
| CL | 2.78 / 5.55 / 11.11 / 19.44 | 3 / 6 / 11 / 19 | x0.49 | 6.0 | cap binds for the 7-lot book |
| NKD | 1.95 / 3.91 / 7.82 / 13.68 | 2 / 4 / 8 / 14 | x0.92 | 0.2 | too thin: cap below the 2-lot book |
| MBT | 23.92 / 47.85 / 95.69 / 167.46 | 24 / 48 / 96 / 167 | x0.40 | 1.2 | too thin: cap below the 2-lot book; micro contract 0.1 BTC, fractional |
Reading: caps bind or are impossible for RTY, YM, ZB, 6E, 6J, NKD and MBT at the NQ book sizes; slices on those instruments must either run at a smaller NQ-equivalent size (state it) or report the participation. Notional per equal-risk unit is x2.7 NQ for ZN, x2.6 for 6E and x2.0 for 6J (low volatility per notional dollar), so a margin / leverage cap of x3 NQ notional is the second cap. The 1.7% cap uses the all-hours median 5-min volume (asia hours are thinner), so it is generous.

## 3. Costs
NQ measured costs (V13T_LIVE): market exit 0.80 pt, stop 2.45 pt worse than nominal, targets nominal, fee $4.84 round trip (0.242 pt; FEES.md, NQ exchange fee is a PROXY of ES):
| NQ cost | points | ticks | $ per contract | bps of price (median 20669) | ATR14(5m) multiples (overall 14.48 pt) |
|---|---|---|---|---|---|
| market exit | 0.800 | 3.20 | 16.00 | 0.387 | 0.0552 |
| stop slip (worse than nominal) | 2.450 | 9.80 | 49.00 | 1.185 | 0.1692 |
| fee round trip | 0.242 | 0.97 | 4.84 | 0.117 | 0.0167 |
Assumed instrument costs, three mappings side by side and the BASE rule (ATR-scaled with floors, as the D3CX/T-C convention 1/2 ticks as lower bound):
| instrument | market cost: ATR-scaled ticks | bps-scaled ticks | NQ-literal ticks | BASE (max(ATR, floor 1 tick; thin 2)) ticks / $ | stop slip: ATR-scaled ticks | BASE (floor 2 tick; thin 3) ticks / $ | fee RT $ (grade) | fee in ticks | RT cost of a stopped trade, BASE $ (entry mkt + stop slip + fee) / 2x stress $ / as share of the stop distance $ |
|---|---|---|---|---|---|---|---|---|---|
| NQ | 3.20 | 3.20 | 3.2 | 3.20 / $16.0 | 9.80 | 9.80 / $49.0 | $4.84 (PROXY(ES)) | 0.97 | $70 / $140 / 5.8% |
| ES | 0.62 | 0.91 | 3.2 | 1.00 / $12.5 | 1.91 | 2.00 / $25.0 | $4.84 (NT-published) | 0.39 | $42 / $85 / 7.2% |
| RTY | 0.87 | 0.85 | 3.2 | 1.00 / $5.0 | 2.67 | 2.67 / $13.4 | $4.84 (PROXY(ES)) | 0.97 | $23 / $46 / 7.1% |
| YM | 1.00 | 1.65 | 3.2 | 1.00 / $5.0 | 3.07 | 3.07 / $15.3 | $4.84 (PROXY(ES)) | 0.97 | $25 / $50 / 6.7% |
| ZN | 0.10 | 0.27 | 3.2 | 1.00 / $15.6 | 0.31 | 2.00 / $31.2 | $4.62 (ESTIMATE) | 0.30 | $51 / $103 / 42.8% |
| ZB | 0.09 | 0.14 | 3.2 | 1.00 / $31.2 | 0.29 | 2.00 / $62.5 | $4.62 (ESTIMATE) | 0.15 | $98 / $197 / 44.3% |
| 6E | 0.33 | 0.85 | 3.2 | 1.00 / $6.2 | 1.00 | 2.00 / $12.5 | $5.30 (FEES.md addendum (exch WEAK)) | 0.85 | $24 / $48 / 15.7% |
| 6J | 0.26 | 0.52 | 3.2 | 2.00 / $12.5 | 0.80 | 3.00 / $18.8 | $5.30 (ESTIMATE(6E class)) | 0.85 | $37 / $73 / 29.9% |
| GC | 1.18 | 1.06 | 3.2 | 1.18 / $11.8 | 3.60 | 3.60 / $36.0 | $5.66 (ESTIMATE) | 0.57 | $53 / $107 / 6.1% |
| CL | 0.58 | 0.28 | 3.2 | 1.00 / $10.0 | 1.76 | 2.00 / $20.0 | $5.26 (ESTIMATE) | 0.53 | $35 / $71 / 8.2% |
| NKD | 0.33 | 0.30 | 3.2 | 2.00 / $50.0 | 1.00 | 3.00 / $75.0 | $5.30 (ESTIMATE) | 0.21 | $130 / $261 / 21.2% |
| MBT | 1.34 | 0.54 | 3.2 | 2.00 / $1.0 | 4.10 | 4.10 / $2.0 | $1.56 (ESTIMATE(micro)) | 3.12 | $5 / $9 / 9.2% |
Fees: FEES.md has ES 4.84 (NT-published), NQ 4.84 (PROXY), MES/MNQ/M2K/MYM 1.78, MCL 2.08 (weak), 6E 5.30 (weak exchange fee). All other values above are labelled ESTIMATES built as 2 x (NT commission 0.59 standard / 0.09 micro + exchange+NFA per side + clearing 0.19 + routing 0.25): RTY, YM exchange+NFA taken equal to ES 1.39 (PROXY); ZN, ZB 1.28 (ESTIMATE of the CME interest-rate non-member Globex rate); 6J = 6E class 1.62; GC 1.80 (ESTIMATE, COMEX); CL 1.60 (ESTIMATE; MCL entry in FEES.md is 0.51 for the micro); NKD 1.62 (ESTIMATE); MBT 0.25 (ESTIMATE; micro crypto). None of these exchange fees was verified against a CME schedule or an NT statement in this note (FEES.md flag 1 applies); they move the BASE round trip by under $2 per contract for the standard contracts and are covered by the 2x stress. A real NT confirmation for one round trip per instrument settles them.
Slippage assumptions are NOT measured: no tick or L2 exists for any instrument except NQ (INSTRUMENT_INVENTORY: ES/RTY mbp10 folders hold only manifests). The ATR-scaled NQ costs are below one tick for ES, ZN, ZB, 6E, 6J, CL and the floors then decide; the LITERAL variant (3.2 ticks market / 9.8 ticks stop on every instrument) is a harsh upper bound for deep markets, and the 2x stress of BASE is the middle. Live model (user): signal at the 1-min bar close, first fill about 1 s later, slices every 2 s, stops/targets resting: with 1-min bars use the next bar's open for entry, stops fill at their level (bar open if gapped) plus the stop slip, targets need a 1-tick trade-through, stop first when stop and target are both inside the same bar (conservative).

## 4. Session tables (ET)
NQ tags, used for every instrument by entry minute (ET): asia 18:00-02:00, london 02:00-08:30, pre 08:30-09:30, nyam 09:30-12:00, nypm 12:00-15:00, close 15:00-16:54. Entries 16:55-18:00 are not possible (maintenance break 17:00-18:00 in all 13 instruments' 1-min data, Mon-Thu, 5-min coverage > 50% of days at every other 5-min slot).
| instrument | Globex hours (ET, Sun-Fri) | maintenance break (ET; confirmed in the 1-min data) | home / cash hours (ET; from CME calendars, NOT checked in data) | daily settlement (ET; not checked in data) | NQ session tags that contain the home hours |
|---|---|---|---|---|---|
| NQ, ES, RTY, YM | Sun 18:00 - Fri 17:00 | 17:00-18:00 daily | RTH 09:30-16:00; Tokyo/London overlaps in asia/london tags | 16:00 | nyam 09:30-12:00, nypm 12:00-15:00, close 15:00-16:54 |
| ZN, ZB | same | 17:00-18:00 | rates pit 08:20-15:00 (data releases 08:30, 10:00 ET) | 15:00 | pre 08:30-09:30 (releases), nyam, nypm |
| 6E, 6J | same | 17:00-18:00 | London 03:00-12:00 for 6E; Tokyo 19:00-02:00 ET (EDT 20:00-02:00) for 6J; ECB/BoJ events | 15:00 (CME FX 14:00 CT) | london (6E), asia (6J) |
| GC | same | 17:00-18:00 | COMEX day 08:20-13:30 | 13:30 | pre, nyam |
| CL | same | 17:00-18:00 | NYMEX day 09:00-14:30 (EIA Wednesday 10:30) | 14:30 | nyam, nypm |
| NKD | same | 17:00-18:00 | Osaka/Tokyo cash 20:00-02:15 ET (EDT; 19:00-01:15 EST) | n/a (check) | asia (thin after 02:00: median 12 contracts per 5 min) |
| MBT, BTC | Sun 18:00 - Fri 17:00 | 17:00-18:00 | 24h; CME reference rate 11:00 ET (16:00 London) | 11:00 reference rate (check) | all tags (vol peaks nyam: ATR x1.9 of asia) |
Median ATR14(5m) by NQ session tag (instrument units) is in out/instr_sc/atr14_5m_by_session.csv; ratios to NQ are in table 2. Weekend and early-close days: not modelled (data-gap flat, 30-minute rule as D3CX).

## Reviewer checklist for the other T-INSTR slices (same logic as the NQ books?)
A slice is the same book only if all of the following hold; I will review any slice definition posted to DECISIONS.md / autopilot against it:
1. Signal definition identical in bar units (same bars: 1-min signal evaluation at bar close, 5-min grid for ER/Keltner), indicator lengths unchanged, ER(20) 5-min ladder identical (Q1-A x0.5 below 0.30).
2. Every point constant mapped with the same f_i (primary) and a stated rounding; stop = target = 1R mapping (60/60 -> f x 60); TH-L2 arm 30 -> f x 30.
3. Lots at equal dollar risk from the live Q1-A traded lots (session table x slot x B02 x ER x zone), or an explicitly stated NQ-lot count; no per-instrument lot tuning.
4. Locks in dollar R units equal to the NQ book (per-book R$, +-R daily caps, week floor, give-back arm 2R keep 0.5), lock R never scaled; zones/B1 layers only if the instrument has the inputs (state which are off).
5. Same ET session tags and entry gate; roll bars excluded; additive back-adjustment disclosed.
6. Costs: BASE and 2x stress from this note, fee grade labelled; a slice that cannot clear 2x stress is DEAD, one that clears only the LITERAL-free BASE is labelled COST-FRAGILE.
7. Evaluation: same windows (L3M, L6M, HOLD, MID, PRE, X'), same paired MDE, per-book weekly P&L in the instrument account's dollars AND in NQ-equivalent dollars (lots x pv x price / NQ), carrying episodes dropped, placebos A/B/C, and the primary/S1/S2 scaling variants.
8. Data limits stated: 1-min bars only for all but NQ (no intrabar path): the stop-first rule and the next-bar-open entry are model choices; NKD, MBT, 6J minute coverage thin.
