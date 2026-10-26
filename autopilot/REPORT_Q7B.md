# REPORT Q7B - Q7B: B10 grid on FX (6E, 6J, 6B, 6A, 6C)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 0 selected cells (+30 diagnostic) scored on 5 instruments; best non-diagnostic all-in additive uplift at 20% share +nan; best pair-window standalone Sharpe +0.25.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Windows (ET): Asia entries 19:00-01:30 flat 02:00; London entries 02:30-07:30 flat 08:25. Strategies: ST(14,2), EMA 9/21, Donchian 20, window opening-range breakout (first 30 min), VWAP-z 2.0 fade, RSI(14,30) fade. Exits: bracket stop=target or trail at 0.25/0.5 x SR (SR = the window's own 20-day mean range).
- Instruments: 6E, 6J, 6B, 6A, 6C. Grid: 144 cells per instrument = 2 windows x 3 bar sizes x 6 strategies x 4 exits.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 5 per instrument per window (Asia, London separately) by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| 6A    |     144 |        144 |         0 |              -0.359 |                1 |          0 |            6 |
| 6B    |     144 |        143 |         0 |              -0.556 |                1 |          0 |            6 |
| 6C    |     144 |        142 |         0 |              -1.147 |                0 |          0 |            6 |
| 6E    |     144 |        140 |         0 |               0.187 |                1 |          0 |            6 |
| 6J    |     144 |        144 |         0 |              -0.154 |                1 |          0 |            6 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| 6E    |     100 |                    0 |             0.26 |               2 |          1 |                         nan |            0.391 |           0.839 |      nan |         nan |                0.839 |
| 6J    |     100 |                    0 |             0.04 |               1 |          1 |                         nan |            0.594 |           0.861 |      nan |         nan |                0.861 |
| 6B    |     100 |                    0 |             0.01 |               1 |          1 |                         nan |            0.532 |           0.532 |      nan |         nan |                0.532 |
| 6A    |     100 |                    0 |             0    |               0 |          1 |                         nan |          nan     |         nan     |      nan |         nan |              nan     |
| 6C    |     100 |                    0 |             0    |               0 |          1 |                         nan |          nan     |         nan     |      nan |         nan |              nan     |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6E 1 (diag) | asia 30m rsi[14, 30] exit=bracket0.5xSR | 88 | 1 | 0.16 | 1.17 | -0.84 | -2.66 / -0.76 | -0.01 / -0.51 / -0.58 | -0.33 | 0.18 | 0.96 | -0.40 | 0.00 | 144 | diag |
| 6E 2 (diag) | asia 30m rsi[14, 30] exit=trail0.5xSR | 90 | 0 | -0.43 | 0.52 | -1.04 | -2.45 / -0.60 | -0.07 / -0.64 / -0.41 | -0.35 | 0.06 | 0.98 | -0.40 | 0.00 | 148 | diag |
| 6E 3 (diag) | asia 5m vwz[2.0] exit=bracket0.5xSR | 665 | 1 | -0.63 | -0.25 | -1.03 | -1.63 / -1.20 | -0.10 / -0.12 / -0.56 | -0.55 | -0.32 | 1.00 | -0.42 | 0.00 | 1094 | diag |
| 6E 4 (diag) | lon 30m emax[9, 21] exit=bracket0.5xSR | 275 | 1 | 0.19 | -1.52 | 0.25 | 0.67 / -0.20 | -0.00 / 0.04 / 0.09 | -0.11 | -0.02 | 1.00 | -0.16 | 0.33 | 436 | diag |
| 6E 5 (diag) | lon 15m orb[30] exit=bracket0.5xSR | 515 | 1 | -0.25 | -2.00 | -0.95 | -2.13 / 0.36 | -0.13 / -0.32 / -0.48 | -0.39 | 0.18 | 0.64 | -0.42 | 0.00 | 823 | diag |
| 6E 6 (diag) | lon 30m st[14, 2.0] exit=bracket0.5xSR | 363 | 0 | -0.32 | -1.16 | -0.07 | 0.34 / 0.11 | -0.09 / -0.03 / 0.15 | -0.18 | -0.22 | 1.00 | -0.23 | 0.00 | 572 | diag |
| 6J 1 (diag) | asia 15m don[20] exit=bracket0.5xSR | 655 | 1 | -0.46 | -2.67 | -1.07 | -2.86 / -1.59 | -0.12 / -0.38 / -0.33 | -0.42 | -0.03 | 0.97 | -0.38 | 0.00 | 1037 | diag |
| 6J 2 (diag) | asia 30m emax[9, 21] exit=bracket0.5xSR | 240 | 0 | -0.51 | -1.33 | -1.54 | -3.50 / -1.20 | -0.14 / -0.87 / -0.57 | -0.53 | 0.02 | 0.75 | -0.54 | 0.00 | 415 | diag |
| 6J 3 (diag) | asia 30m st[14, 2.0] exit=bracket0.25xSR | 319 | 0 | -0.60 | -1.60 | -1.06 | -2.09 / -2.73 | -0.13 / -0.33 / -0.37 | -0.46 | -0.00 | 1.00 | -0.40 | 0.00 | 512 | diag |
| 6J 4 (diag) | lon 30m don[20] exit=trail0.5xSR | 283 | 1 | -0.15 | -2.26 | -1.47 | -4.11 / -1.47 | -0.08 / -0.57 / -0.88 | -0.54 | 0.40 | 0.91 | -0.51 | 0.00 | 463 | diag |
| 6J 5 (diag) | lon 30m don[20] exit=bracket0.25xSR | 338 | 1 | -0.33 | -2.53 | -1.37 | -3.36 / -2.90 | -0.13 / -0.44 / -0.78 | -0.58 | 0.17 | 1.00 | -0.49 | 0.00 | 542 | diag |
| 6J 6 (diag) | lon 30m don[20] exit=bracket0.5xSR | 301 | 0 | -0.47 | -2.03 | -1.34 | -2.90 / -1.03 | -0.13 / -0.45 / -0.65 | -0.47 | 0.33 | 0.83 | -0.48 | 0.00 | 487 | diag |
| 6B 1 (diag) | asia 30m st[14, 2.0] exit=bracket0.5xSR | 154 | 0 | -0.83 | -2.26 | -1.49 | -2.58 / -2.50 | -0.22 / -1.05 / -0.34 | -0.63 | -0.00 | 1.00 | -0.56 | 0.00 | 290 | diag |
| 6B 2 (diag) | asia 30m st[14, 2.0] exit=bracket0.25xSR | 156 | 0 | -1.15 | -2.74 | -2.33 | -4.09 / -4.92 | -0.30 / -1.14 / -0.90 | -0.88 | 0.08 | 1.00 | -0.78 | 0.00 | 292 | diag |
| 6B 3 (diag) | asia 30m st[14, 2.0] exit=trail0.5xSR | 156 | 0 | -1.64 | -3.05 | -2.30 | -3.28 / -2.60 | -0.36 / -1.29 / -0.51 | -0.88 | -0.08 | 1.00 | -0.74 | 0.00 | 292 | diag |
| 6B 4 (diag) | lon 15m orb[30] exit=bracket0.5xSR | 512 | 1 | -0.56 | -1.52 | -1.49 | -3.06 / -0.62 | -0.16 / -0.86 / -0.58 | -0.61 | -0.02 | 0.76 | -0.56 | 0.00 | 820 | diag |
| 6B 5 (diag) | lon 5m orb[30] exit=bracket0.5xSR | 514 | 1 | -0.61 | -1.19 | -1.21 | -2.23 / -0.67 | -0.19 / -0.57 / -0.45 | -0.56 | -0.25 | 0.91 | -0.51 | 0.00 | 823 | diag |
| 6B 6 (diag) | lon 30m orb[30] exit=bracket0.5xSR | 510 | 1 | -0.62 | -1.46 | -1.16 | -2.09 / -0.18 | -0.17 / -0.70 / -0.31 | -0.55 | 0.00 | 0.83 | -0.48 | 0.00 | 814 | diag |
| 6A 1 (diag) | asia 30m rsi[14, 30] exit=bracket0.25xSR | 184 | 1 | -1.40 | -0.88 | -2.13 | -3.55 / -3.58 | -0.29 / -0.77 / -0.59 | -0.69 | 0.51 | 1.00 | -0.61 | 0.00 | 302 | diag |
| 6A 2 (diag) | asia 30m rsi[14, 30] exit=trail0.5xSR | 172 | 1 | -1.57 | -1.62 | -1.76 | -2.09 / -1.84 | -0.33 / -0.70 / -0.28 | -0.64 | 0.29 | 0.97 | -0.56 | 0.00 | 280 | diag |
| 6A 3 (diag) | asia 30m emax[9, 21] exit=bracket0.5xSR | 269 | 0 | -1.58 | -2.16 | -1.31 | -0.68 / -1.76 | -0.35 / -0.01 / -0.24 | -0.57 | -0.11 | 1.00 | -0.47 | 0.00 | 418 | diag |
| 6A 4 (diag) | lon 30m vwz[2.0] exit=bracket0.5xSR | 203 | 0 | -0.36 | -0.70 | -0.68 | -1.11 / -2.20 | -0.10 / -0.25 / -0.21 | -0.42 | -0.33 | 1.00 | -0.34 | 0.00 | 325 | diag |
| 6A 5 (diag) | lon 30m vwz[2.0] exit=trail0.5xSR | 210 | 1 | -0.48 | -1.91 | -0.58 | -0.58 / -2.71 | -0.12 / -0.28 / -0.13 | -0.47 | -0.31 | 1.00 | -0.34 | 0.00 | 340 | diag |
| 6A 6 (diag) | lon 15m vwz[2.0] exit=bracket0.5xSR | 267 | 0 | -0.57 | -0.62 | -0.54 | -0.37 / -2.24 | -0.15 / -0.06 / -0.08 | -0.42 | -0.27 | 1.00 | -0.31 | 0.00 | 436 | diag |
| 6C 1 (diag) | asia 15m rsi[14, 30] exit=bracket0.5xSR | 167 | 0 | -1.47 | -1.08 | -1.98 | -3.40 / -3.65 | -0.29 / -0.31 / -0.60 | -0.58 | 0.07 | 1.00 | -0.52 | 0.00 | 265 | diag |
| 6C 2 (diag) | asia 15m rsi[14, 30] exit=bracket0.25xSR | 191 | 0 | -1.86 | -2.00 | -2.17 | -2.83 / -7.02 | -0.34 / -0.22 / -0.53 | -0.67 | -0.24 | 1.00 | -0.53 | 0.00 | 302 | diag |
| 6C 3 (diag) | asia 30m rsi[14, 30] exit=bracket0.5xSR | 88 | 0 | -1.94 | -0.97 | -1.99 | -2.13 / -3.10 | -0.39 / -0.42 / -0.29 | -0.54 | 0.03 | 1.00 | -0.55 | 0.00 | 143 | diag |
| 6C 4 (diag) | lon 30m rsi[14, 30] exit=bracket0.25xSR | 122 | 0 | -1.15 | -0.59 | -1.61 | -2.32 / -3.35 | -0.28 / -0.74 / -0.60 | -0.63 | -0.32 | 1.00 | -0.61 | 0.00 | 212 | diag |
| 6C 5 (diag) | lon 30m vwz[2.0] exit=bracket0.5xSR | 253 | 0 | -1.18 | -0.79 | -1.59 | -2.56 / -2.34 | -0.26 / -0.57 / -0.27 | -0.53 | -0.06 | 1.00 | -0.49 | 0.00 | 413 | diag |
| 6C 6 (diag) | lon 30m rsi[14, 30] exit=bracket0.5xSR | 110 | 0 | -1.21 | 0.14 | -1.28 | -1.52 / -1.61 | -0.30 / -0.56 / -0.38 | -0.51 | -0.46 | 0.98 | -0.55 | 0.00 | 190 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 0 |
| diagnostic cells read | 30 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 1 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 23 |
| worst-decile corr <= +0.30 | 27 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6A lon 15m vwz[2.0] exit=bracket0.5xSR (diag) | clean | -0.63 | -0.79 | -154118 | -125273 | 895671 | -203079 | -0.64 | 47.6 | 1.31 | -95722 | 312152 | -113567 |
| 6A lon 15m vwz[2.0] exit=bracket0.5xSR (diag) | H1 | 0.03 | 0.04 | -104916 | -92830 | 226366 | -129556 | 0.03 | 50.0 | 2.77 | -77984 | 138170 | -82969 |
| 6A lon 15m vwz[2.0] exit=bracket0.5xSR (diag) | H2 | -0.72 | -0.86 | -158389 | -107984 | 415329 | -189005 | -0.45 | 47.2 | 2.22 | -97715 | 234267 | -115217 |
| 6A lon 15m vwz[2.0] exit=bracket0.5xSR (diag) | all | -0.54 | -0.69 | -152338 | -120827 | 895671 | -203079 | -0.84 | 47.6 | 1.73 | -95162 | 312152 | -115217 |
| 6B lon 30m orb[30] exit=bracket0.5xSR (diag) | clean | -0.59 | -0.76 | -141082 | -119084 | 1135533 | -194033 | -0.47 | 56.2 | 1.29 | -95628 | 309775 | -109746 |
| 6B lon 30m orb[30] exit=bracket0.5xSR (diag) | H1 | -3.14 | -3.16 | -149462 | -138694 | 853710 | -180109 | -0.96 | 60.7 | 2.13 | -82941 | 203061 | -87780 |
| 6B lon 30m orb[30] exit=bracket0.5xSR (diag) | H2 | -1.17 | -1.43 | -114339 | -108778 | 631504 | -114505 | -0.54 | 50.0 | 1.99 | -99244 | 244891 | -102554 |
| 6B lon 30m orb[30] exit=bracket0.5xSR (diag) | all | -1.16 | -1.40 | -140286 | -124848 | 2060983 | -194033 | -0.82 | 55.4 | 1.57 | -95560 | 309775 | -109746 |
| 6C lon 30m vwz[2.0] exit=bracket0.5xSR (diag) | clean | -1.18 | -1.44 | -146810 | -124317 | 1208159 | -177329 | -0.88 | 56.2 | 1.20 | -98428 | 355320 | -112777 |
| 6C lon 30m vwz[2.0] exit=bracket0.5xSR (diag) | H1 | -3.58 | -3.45 | -106654 | -101422 | 632531 | -120970 | -0.86 | 67.9 | 2.26 | -84939 | 166198 | -89690 |
| 6C lon 30m vwz[2.0] exit=bracket0.5xSR (diag) | H2 | -1.93 | -2.09 | -134056 | -120623 | 655539 | -138168 | -0.73 | 55.6 | 2.02 | -94533 | 220152 | -104780 |
| 6C lon 30m vwz[2.0] exit=bracket0.5xSR (diag) | all | -1.59 | -1.85 | -141930 | -121430 | 2266223 | -177329 | -0.92 | 58.3 | 1.54 | -96912 | 355320 | -112777 |
| 6E lon 30m emax[9, 21] exit=bracket0.5xSR (diag) | clean | 0.05 | 0.07 | -138045 | -116238 | 721890 | -216646 | 0.07 | 47.6 | 1.45 | -90368 | 306085 | -100371 |
| 6E lon 30m emax[9, 21] exit=bracket0.5xSR (diag) | H1 | 0.67 | 1.04 | -83110 | -78528 | 220586 | -83168 | 0.59 | 39.3 | 2.87 | -73976 | 146709 | -74013 |
| 6E lon 30m emax[9, 21] exit=bracket0.5xSR (diag) | H2 | 0.66 | 1.02 | -91546 | -82083 | 262787 | -107914 | 0.63 | 47.2 | 2.38 | -82335 | 220881 | -84757 |
| 6E lon 30m emax[9, 21] exit=bracket0.5xSR (diag) | all | 0.25 | 0.35 | -122935 | -103312 | 791791 | -216646 | 0.43 | 46.4 | 1.88 | -87354 | 306085 | -100371 |
| 6J asia 15m don[20] exit=bracket0.5xSR (diag) | clean | -0.50 | -0.64 | -147588 | -123931 | 640727 | -226593 | -0.71 | 50.5 | 1.34 | -85809 | 272855 | -96734 |
| 6J asia 15m don[20] exit=bracket0.5xSR (diag) | H1 | -3.10 | -3.19 | -72919 | -66563 | 447987 | -79406 | -0.91 | 64.3 | 2.45 | -86687 | 170178 | -87252 |
| 6J asia 15m don[20] exit=bracket0.5xSR (diag) | H2 | -2.66 | -2.67 | -105413 | -91172 | 551667 | -114781 | -0.88 | 58.3 | 1.96 | -80161 | 218698 | -82616 |
| 6J asia 15m don[20] exit=bracket0.5xSR (diag) | all | -1.07 | -1.31 | -134434 | -111260 | 1488665 | -226593 | -0.90 | 54.8 | 1.65 | -85822 | 272855 | -96734 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| 6E lon 30m emax[9, 21] exit=bracket0.5xSR (diag) | -26.2 | -7.3 | 10.9 | 16.1 | -8.1 / 5.0 | 29.8 / 32.7 | NO |
| 6J asia 15m don[20] exit=bracket0.5xSR (diag) | -45.0 | -1.0 | 12.2 | 11.8 | -1.8 / 11.6 | 12.8 / 12.5 | NO |
| 6B lon 30m orb[30] exit=bracket0.5xSR (diag) | -48.9 | -22.1 | -4.4 | -4.6 | -23.0 / -6.5 | 11.8 / 19.7 | NO |
| 6A lon 15m vwz[2.0] exit=bracket0.5xSR (diag) | -38.4 | -35.7 | -2.2 | 12.8 | -36.8 / -4.7 | 19.6 / 29.3 | NO |
| 6C lon 30m vwz[2.0] exit=bracket0.5xSR (diag) | -53.4 | -30.0 | -5.3 | -10.3 | -31.1 / -9.1 | 6.8 / 15.8 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| 6E 1 (diag) asia 30m rsi[14, 30] exit=bracket0.5xSR | positive pre-2023 | 447 | 40.2 | 25.6 | 24.6 | 14.7 | 1.86 / 1.17 / 1.13 | 17.3 / 2.2 |
| 6E 2 (diag) asia 30m rsi[14, 30] exit=trail0.5xSR | positive pre-2023 | 467 | 27.3 | 10.5 | 9.4 | 16.9 | 1.35 / 0.52 / 0.46 | 10.7 / -6.1 |
| 6E 3 (diag) asia 5m vwz[2.0] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 3424 | 12.9 | -2.0 | -3.0 | 14.9 | 1.63 / -0.25 / -0.38 | 10.9 / -3.9 |
| 6E 4 (diag) lon 30m emax[9, 21] exit=bracket0.5xSR | negative pre-2023 | 1447 | -16.4 | -31.9 | -33.1 | 15.5 | -0.79 / -1.52 / -1.58 | 16.1 / 0.8 |
| 6E 5 (diag) lon 15m orb[30] exit=bracket0.5xSR | negative pre-2023 | 2656 | -20.0 | -35.0 | -36.1 | 15.0 | -1.15 / -2.00 / -2.06 | 10.9 / -4.0 |
| 6E 6 (diag) lon 30m st[14, 2.0] exit=bracket0.5xSR | negative pre-2023 | 1783 | -6.6 | -21.8 | -22.8 | 15.2 | -0.35 / -1.16 / -1.21 | 11.1 / -4.0 |
| 6J 1 (diag) asia 15m don[20] exit=bracket0.5xSR | negative pre-2023 | 3187 | -16.0 | -31.3 | -36.3 | 15.4 | -1.38 / -2.67 / -3.08 | 10.4 / -4.7 |
| 6J 2 (diag) asia 30m emax[9, 21] exit=bracket0.5xSR | negative pre-2023 | 1251 | -4.8 | -20.4 | -25.5 | 15.7 | -0.32 / -1.33 / -1.64 | 9.5 / -6.0 |
| 6J 3 (diag) asia 30m st[14, 2.0] exit=bracket0.25xSR | negative pre-2023 | 1359 | -2.8 | -17.2 | -21.7 | 14.4 | -0.27 / -1.60 / -2.00 | 9.5 / -4.7 |
| 6J 4 (diag) lon 30m don[20] exit=trail0.5xSR | negative pre-2023 | 1546 | -21.4 | -38.2 | -43.7 | 16.9 | -1.27 / -2.26 / -2.56 | 14.6 / -2.2 |
| 6J 5 (diag) lon 30m don[20] exit=bracket0.25xSR | negative pre-2023 | 1860 | -11.2 | -25.3 | -29.9 | 14.2 | -1.14 / -2.53 / -2.95 | 11.6 / -2.4 |
| 6J 6 (diag) lon 30m don[20] exit=bracket0.5xSR | negative pre-2023 | 1643 | -19.2 | -34.4 | -39.3 | 15.2 | -1.14 / -2.03 / -2.30 | 9.1 / -6.2 |
| 6B 1 (diag) asia 30m st[14, 2.0] exit=bracket0.5xSR | negative pre-2023 | 693 | -9.8 | -25.4 | -26.4 | 15.6 | -0.92 / -2.26 / -2.33 | 7.9 / -7.3 |
| 6B 2 (diag) asia 30m st[14, 2.0] exit=bracket0.25xSR | negative pre-2023 | 698 | -9.9 | -24.6 | -25.5 | 14.6 | -1.21 / -2.74 / -2.82 | 7.0 / -6.8 |
| 6B 3 (diag) asia 30m st[14, 2.0] exit=trail0.5xSR | negative pre-2023 | 695 | -14.2 | -31.1 | -32.1 | 16.9 | -1.50 / -3.05 / -3.15 | 4.9 / -12.0 |
| 6B 4 (diag) lon 15m orb[30] exit=bracket0.5xSR | negative pre-2023 | 2669 | -3.7 | -18.6 | -19.8 | 14.9 | -0.30 / -1.52 / -1.63 | 10.6 / -4.2 |
| 6B 5 (diag) lon 5m orb[30] exit=bracket0.5xSR | negative pre-2023 | 2680 | -0.0 | -14.7 | -16.0 | 14.7 | 0.01 / -1.19 / -1.29 | 9.9 / -4.7 |
| 6B 6 (diag) lon 30m orb[30] exit=bracket0.5xSR | negative pre-2023 | 2660 | -3.5 | -18.4 | -19.7 | 15.0 | -0.27 / -1.46 / -1.56 | 10.5 / -4.4 |
| 6A 1 (diag) asia 30m rsi[14, 30] exit=bracket0.25xSR | gross-positive, cost-negative pre-2023 | 967 | 10.6 | -9.3 | -12.6 | 19.9 | 1.05 / -0.88 / -1.18 | 7.1 / -12.6 |
| 6A 2 (diag) asia 30m rsi[14, 30] exit=trail0.5xSR | gross-positive, cost-negative pre-2023 | 915 | 0.3 | -24.1 | -28.3 | 24.4 | 0.02 / -1.62 / -1.88 | 3.7 / -20.7 |
| 6A 3 (diag) asia 30m emax[9, 21] exit=bracket0.5xSR | negative pre-2023 | 1371 | -6.1 | -28.5 | -32.4 | 22.4 | -0.49 / -2.16 / -2.42 | 5.8 / -16.6 |
| 6A 4 (diag) lon 30m vwz[2.0] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 1062 | 9.7 | -11.9 | -15.2 | 21.6 | 0.58 / -0.70 / -0.90 | 16.3 / -4.9 |
| 6A 5 (diag) lon 30m vwz[2.0] exit=trail0.5xSR | negative pre-2023 | 1087 | -3.6 | -27.9 | -31.8 | 24.4 | -0.25 / -1.91 / -2.15 | 17.7 / -6.7 |
| 6A 6 (diag) lon 15m vwz[2.0] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 1439 | 12.3 | -9.2 | -12.6 | 21.4 | 0.84 / -0.62 / -0.85 | 14.5 / -6.6 |
| 6C 1 (diag) asia 15m rsi[14, 30] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 786 | 3.7 | -9.4 | -10.4 | 13.0 | 0.44 / -1.08 / -1.19 | 3.7 / -9.5 |
| 6C 2 (diag) asia 15m rsi[14, 30] exit=bracket0.25xSR | gross-positive, cost-negative pre-2023 | 908 | 1.2 | -11.0 | -11.9 | 12.2 | 0.25 / -2.00 / -2.15 | 5.1 / -6.8 |
| 6C 3 (diag) asia 30m rsi[14, 30] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 409 | 1.3 | -11.8 | -12.9 | 13.1 | 0.11 / -0.97 / -1.05 | -2.8 / -16.1 |
| 6C 4 (diag) lon 30m rsi[14, 30] exit=bracket0.25xSR | gross-positive, cost-negative pre-2023 | 769 | 6.8 | -4.9 | -5.9 | 11.7 | 0.85 / -0.59 / -0.71 | 5.3 / -6.4 |
| 6C 5 (diag) lon 30m vwz[2.0] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 1353 | 5.3 | -7.6 | -8.7 | 12.9 | 0.57 / -0.79 / -0.92 | 4.2 / -8.6 |
| 6C 6 (diag) lon 30m rsi[14, 30] exit=bracket0.5xSR | positive pre-2023 | 693 | 14.7 | 2.2 | 1.1 | 12.5 | 0.92 / 0.14 / 0.07 | 2.4 / -10.5 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): 6A: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); 6B: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); 6C: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); 6E: 0 cells pass the clean rule against a replicate mean of 0.3 (p(count) = 1.00); 6J: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- No cell passed the clean rule on any instrument; the pair window was read only for the diagnostic cells.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat. Overnight liquidity (Asia) is thin for ZN/RTY/CL; slippage of 1 tick may be optimistic there.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q7b.py (= ap_b10.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q7b/ (`Q7B_CO_all_selected_scored.csv`).

DONE Q7B
