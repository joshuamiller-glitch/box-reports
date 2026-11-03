# DISCOVER_EVENT_BOOKS (T-DISCOVER B event books + C calendar window books, CAL, built 2026-11-03)

Built on the ZL-2 harness (`autopilot/DISCOVER_HARNESS.md`, `book_harness.py`), 1-s NQ path through 2026-10-30, label days 2023-04-03..2026-10-30, windows L1M..X'. Code: `l2vast/ds3/code/discover/{event_books,window_books,targeted_placebo,broad_placebo,analyze,leads_corr}.py`; results `DISCOVER_EVENT_BOOKS.csv` (368 books), `DISCOVER_WINDOW_BOOKS.csv` (268 books), per-year rows and placebo grids in `l2vast/ds3/out/`.

## Spec (all books)
- Entry: market at the 1-s price at T+k minutes (k = 1, 2, 5; "E1/E2/E5" = the close of the 1st/2nd/5th minute after the release second T), using only the information up to that second. First move = price at entry minus the last print before T (T-1 s). Direction: cont (with the first move), fade (against it), and for CPI/NFP `sign` = short when actual > prior, long when actual < prior (prior = previous print, NOT consensus; the census shows the post-release reaction is partly mean reversion of the series; the sign direction was fixed after seeing the census, so it is in-sample as to direction).
- Brackets: 60/60 pts, or stop = 1 x ATR(14) of 5-min bars and target = 1 x ATR (1R-ATR); time stop at T+30 or T+60 min; flat 16:55 (harness). 2 lots. Costs: harness LIVE basis (stops 2.45 worse, market/time/flat exits 0.80, fee 0.242 pt/lot RT).
- Release-minute slippage stress (separate columns, never the base): entry price 1 or 3 pt worse than the 1-s price (columns `slip1_*`, `slip3_*` in the CSV).
- Event types: CPI, NFP, FOMC statement (14:00), FOMC presser (14:30), PPI, PCE, GDP, retail sales, claims, ISM mfg, ISM svc, 3Y/10Y/30Y auctions (13:00) = 14 types; plus FOMC_TREND = entry 14:35 with the move since 14:00, exit by 15:00/16:00 or bracket. Calendar = `DISCOVER_CALENDAR.csv`.
- Gates and marginal value: the harness' (NOW-ONLY / TOLERANT / STRICT; ADDITION = TOLERANT and the Q1-A ts2 stack's Calmar with the carrying week dropped improves). The harness Calmar is mean weekly $ / maxDD of the cumulative weekly $ (not annualised).

## Result in one paragraph
368 event books were scored: 126 pass NOW-ONLY, 53 TOLERANT, 5 STRICT, 39 ADDITION. The same grid run on 30 placebo replicates (same count of events per year at the same clock times on random non-event days, the actual/prior pairs permuted for the sign books) passes TOLERANT 48.1 times per replicate (max 59), ADDITION 36.2 (max 46), NOW-ONLY 117.0. So the gate counts of the real event grid are what random days give: the family as a whole is NOT distinguishable from the placebo. The tolerant gate is easy for sparse books (5-6 trades in L6M, one loser sets the whole maxDD). Calendar window books (268 books, 6 day-sets): 28 TOLERANT, 19 ADDITION against 33.4 / 22.2 per replicate (30 replicates, matched weekday mix): same null result.
No book reaches the confirmed tier. A few individual books beat their own matched placebo draws (table below) but with 5-9 L6M trades each, 636 books tested in total (Bonferroni would need p < 0.0001; 200 draws resolve only 0.005), and 2023 negative in most of them, the honest label is LEAD at best and several are artefacts of 2026 alone.

## Per event type (real grid vs placebo grid)
| event | books | TOLERANT real | TOLERANT placebo mean (max) | ADDITION real | median L6M trades | best L6M book | L6M $/wk |
|---|---|---|---|---|---|---|---|
| AUC10Y | 24 | 6 | 3.0 (max 6) | 3 | 9 | AUC10Y|E5|fade|1R-ATR|T30 | +239 |
| AUC30Y | 24 | 2 | 2.8 (max 7) | 0 | 7 | AUC30Y|E2|fade|1R-ATR|T60 | +139 |
| AUC3Y | 24 | 7 | 2.6 (max 6) | 7 | 6 | AUC3Y|E1|cont|1R-ATR|T60 | +296 |
| CLAIMS | 24 | 0 | 4.6 (max 7) | 0 | 26 | CLAIMS|E2|cont|60/60|T30 | +463 |
| CPI | 36 | 5 | 4.5 (max 8) | 1 | 6 | CPI|E1|fade|60/60|T60 | +350 |
| FOMC_PR | 24 | 0 | 3.2 (max 7) | 0 | 4 | FOMC_PR|E1|fade|1R-ATR|T30 | +203 |
| FOMC_ST | 24 | 2 | 2.5 (max 5) | 2 | 4 | FOMC_ST|E5|cont|1R-ATR|T60 | +258 |
| FOMC_TREND | 8 | 2 | 0.8 (max 3) | 2 | 4 | FOMC_TREND|E35|cont|60/60|T60 | +173 |
| GDP | 24 | 0 | 3.3 (max 6) | 0 | 6 | GDP|E2|cont|60/60|T30 | +194 |
| ISMM | 24 | 5 | 2.9 (max 9) | 5 | 6 | ISMM|E5|fade|60/60|T60 | +443 |
| ISMS | 24 | 8 | 2.9 (max 7) | 6 | 6 | ISMS|E5|fade|1R-ATR|T30 | +237 |
| NFP | 36 | 7 | 4.7 (max 8) | 4 | 6 | NFP|E2|cont|60/60|T60 | +531 |
| PCE | 24 | 5 | 3.1 (max 6) | 5 | 6 | PCE|E2|cont|60/60|T30 | +194 |
| PPI | 24 | 2 | 3.1 (max 6) | 2 | 6 | PPI|E5|cont|60/60|T60 | +294 |
| RETAIL | 24 | 2 | 4.0 (max 7) | 2 | 6 | RETAIL|E5|cont|60/60|T60 | +260 |

## Event-book leads (placebo p_joint_all3 <= 0.005 and p_L6M <= 0.05 over 200 matched-day draws; p_joint = share of draws with L6M, PRE and HOLD means all >= the real book)
| book | trades L6M/HOLD/PRE/X' | mean $/wk L6M | maxDD L6M | Calmar L6M | stack Calmar L6M base -> with | mean HOLD / PRE / X' | L6M mean slip +1 / +3 pt | placebo p L6M / PRE / joint(L6M,PRE,HOLD) | $/trade by year |
|---|---|---|---|---|---|---|---|---|---|
| CPI|E1|fade|60/60|T30 | 6/11/17/10 | +350 | 2,508 | 0.139 | 0.258 -> 0.273 (0.695 -> 0.698 dropcar) | +229 / +61 / -180 | +350 / +350 | 0.000 / 0.035 / 0.000 | 23 -601 / 24 -15 / 25 +182 / 26 +1444 |
| NFP|E2|sign|60/60|T30 | 6/12/17/10 | +383 | 1,622 | 0.236 | 0.258 -> 0.274 (0.695 -> 0.701 dropcar) | +223 / +71 / -86 | +381 / +378 | 0.000 / 0.060 / 0.000 | 23 -144 / 24 -377 / 25 +909 / 26 +957 |
| ISMM|E5|fade|1R-ATR|T30 | 5/11/17/10 | +362 | 0 | nan | 0.258 -> 0.267 (0.695 -> 0.703 dropcar) | +191 / +17 / +155 | +361 / +358 | 0.000 / 0.255 / 0.000 | 23 +653 / 24 -123 / 25 +466 / 26 +821 |
| NFP|E2|cont|60/60|T30 | 6/12/17/10 | +500 | 0 | nan | 0.258 -> 0.275 (0.695 -> 0.704 dropcar) | +296 / +123 / -170 | +498 / +495 | 0.000 / 0.025 / 0.000 | 23 -550 / 24 +361 / 25 -72 / 26 +1763 |
| ISMM|E5|fade|1R-ATR|T60 | 5/11/17/10 | +392 | 0 | nan | 0.258 -> 0.268 (0.695 -> 0.703 dropcar) | +155 / +9 / +155 | +392 / +392 | 0.000 / 0.335 / 0.000 | 23 +653 / 24 -177 / 25 +466 / 26 +613 |
| ISMM|E5|fade|60/60|T60 | 5/11/17/10 | +443 | 0 | nan | 0.258 -> 0.268 (0.695 -> 0.705 dropcar) | +35 / +53 / +183 | +443 / +443 | 0.005 / 0.195 / 0.000 | 23 +627 / 24 +151 / 25 -467 / 26 +758 |
| ISMS|E5|fade|1R-ATR|T30 | 6/11/17/10 | +237 | 2,209 | 0.107 | 0.258 -> 0.270 (0.695 -> 0.698 dropcar) | +210 / +141 / +1 | +237 / +237 | 0.005 / 0.000 / 0.000 | 23 +120 / 24 +589 / 25 +318 / 26 +836 |
| ISMS|E5|fade|1R-ATR|T60 | 6/11/17/10 | +237 | 2,209 | 0.107 | 0.258 -> 0.270 (0.695 -> 0.698 dropcar) | +210 / +141 / +1 | +237 / +237 | 0.010 / 0.005 / 0.000 | 23 +120 / 24 +589 / 25 +318 / 26 +836 |
| ISMM|E5|fade|60/60|T30 | 5/11/17/10 | +378 | 0 | nan | 0.258 -> 0.267 (0.695 -> 0.703 dropcar) | +95 / +53 / +116 | +376 / +373 | 0.010 / 0.125 / 0.005 | 23 +301 / 24 +155 / 25 -17 / 26 +977 |
| FOMC_TREND|E35|cont|60/60|T60 | 4/8/11/7 | +173 | 2,508 | 0.069 | 0.258 -> 0.265 (0.695 -> 0.723 dropcar) | -59 / +95 / -76 | +173 / +173 | 0.015 / 0.005 / 0.000 | 23 -142 / 24 -2 / 25 -59 / 26 -78 |
| AUC3Y|E1|cont|1R-ATR|T60 | 6/12/17/10 | +296 | 1,305 | 0.227 | 0.258 -> 0.266 (0.695 -> 0.701 dropcar) | +206 / +61 / -13 | +294 / +291 | 0.020 / 0.125 / 0.000 | 23 -129 / 24 +49 / 25 +686 / 26 +840 |
| ISMS|E2|fade|1R-ATR|T30 | 6/11/17/10 | +223 | 2,073 | 0.108 | 0.258 -> 0.269 (0.695 -> 0.698 dropcar) | +215 / +15 / -60 | +223 / +223 | 0.025 / 0.395 / 0.000 | 23 -185 / 24 +460 / 25 -646 / 26 +1262 |
| ISMS|E2|fade|1R-ATR|T60 | 6/11/17/10 | +223 | 2,073 | 0.108 | 0.258 -> 0.269 (0.695 -> 0.698 dropcar) | +215 / +15 / -60 | +223 / +223 | 0.030 / 0.370 / 0.000 | 23 -185 / 24 +460 / 25 -646 / 26 +1262 |
| AUC3Y|E1|cont|1R-ATR|T30 | 6/12/17/10 | +247 | 1,305 | 0.190 | 0.258 -> 0.266 (0.695 -> 0.700 dropcar) | +100 / +77 / -19 | +246 / +243 | 0.045 / 0.070 / 0.005 | 23 -156 / 24 +53 / 25 +635 / 26 +461 |
| NFP|E2|sign|60/60|T60 | 6/12/17/10 | +350 | 2,508 | 0.139 | 0.258 -> 0.273 (0.695 -> 0.700 dropcar) | +227 / +56 / -116 | +350 / +350 | 0.050 / 0.235 / 0.000 | 23 -290 / 24 -584 / 25 +926 / 26 +921 |

Reading: all lead books are the same handful of trades seen through different variants (the CPI/NFP/ISM first-5-minute reactions in 2026: 5-6 trades). Their 2023 per-trade means are negative or flat; 2025-26 carry. FOMC_TREND (trend continuation 14:35 to 16:00) is not an edge: HOLD mean -59, yearly per-trade negative every year, despite the 3.0x range excess (the excess is volatility, not direction). Auction books (3Y cont, 10Y fade at T+2) lead on 2025-26 only (2023-24 negative); the 10Y at E1 collapses with 1-3 pt entry slippage (+113 at +1 pt vs +210 base). CPI: 'fade the first move at T+1 minute' (bracket 60/60, T30) leads on 2026 (+1,444 $/trade) but is -601 in 2023; slip +3 pt is the same (the trade list is tiny and the entry is already after the spike).
Marginal value to the stack is small in absolute terms: books earn about +$100-500 per week at 2 lots against a stack maxDD of $104.8k (L6M); the stack L6M maxDD moves by at most -4.8k (CPI fade, NFP/ISM) because the books add profit in a few weeks, not because they hedge the 2026-W29..W39 episode (carrying weeks dropped: Calmar 0.695 -> 0.698..0.709). Correlation to the stack and to each live book is |r| <= 0.17 for every lead (`l2vast/ds3/out/leads_corr.csv`), so they would be diversifiers if real, but too small to matter at 2 lots (they would need 10+ lots, where one 60-pt loser costs $12k+).

## Calendar window books (family C): leads and the broad-day-set results
Window leads among event-day sets (OPEX Friday, roll week, month-end, quarter-end; matched random non-event days, same weekday mix, 200 draws; p_L6M <= 0.15 and p_joint <= 0.005; slip +3 not run for window books):
| book | trades L6M/HOLD/PRE/X' | mean $/wk L6M | maxDD L6M | Calmar L6M | stack Calmar L6M base -> with | mean HOLD / PRE / X' | L6M mean slip +1 / +3 pt | placebo p L6M / PRE / joint(L6M,PRE,HOLD) | $/trade by year |
|---|---|---|---|---|---|---|---|---|---|
| CLK|OPEX_FRI|15:00|short|1R-ATR|look30|T60 | 6/12/17/10 | +242 | 779 | 0.311 | 0.258 -> 0.262 (0.695 -> 0.700 dropcar) | +191 / +33 / +41 | +242 / +nan | 0.000 / 0.465 / 0.000 | 23 +251 / 24 +14 / 25 +133 / 26 +809 |
| CLK|OPEX_FRI|15:00|short|1R-ATR|look30|T180 | 6/12/17/10 | +242 | 779 | 0.311 | 0.258 -> 0.262 (0.695 -> 0.700 dropcar) | +191 / +45 / +31 | +242 / +nan | 0.005 / 0.315 / 0.000 | 23 +251 / 24 -24 / 25 +211 / 26 +809 |
| CLK|QUARTER_END|15:30|cont|1R-ATR|look30|T180 | 4/8/12/6 | +86 | 0 | nan | 0.258 -> 0.258 (0.695 -> 0.698 dropcar) | +43 / +79 / -78 | +86 / +nan | 0.100 / 0.015 / 0.005 | 23 -573 / 24 +180 / 25 +301 / 26 +441 |
| CLK|OPEX_FRI|15:30|short|1R-ATR|look30|T180 | 6/12/17/10 | +74 | 1,632 | 0.045 | 0.258 -> 0.256 (0.695 -> 0.697 dropcar) | -9 / +50 / -14 | +74 / +nan | 0.130 / 0.100 / 0.005 | 23 +26 / 24 +507 / 25 -405 / 26 +140 |
| CLK|OPEX_FRI|10:00|cont|1R-ATR|look30|T60 | 6/12/17/10 | +76 | 5,048 | 0.015 | 0.258 -> 0.262 (0.695 -> 0.692 dropcar) | +33 / +26 / +37 | -78 / +nan | 0.135 / 0.010 / 0.000 | 23 +273 / 24 +319 / 25 -523 / 26 +623 |
| CLK|QUARTER_END|15:30|cont|1R-ATR|look30|T60 | 4/8/12/6 | +86 | 0 | nan | 0.258 -> 0.258 (0.695 -> 0.698 dropcar) | +43 / +79 / -78 | +86 / +nan | 0.140 / 0.035 / 0.005 | 23 -573 / 24 +180 / 25 +301 / 26 +441 |

Broad day-sets (ALL, Mon-Tue, Mon: the placebo days would be the same days, so the harness placebos are used instead: shift5 / side / days ranks = share of 100 draws below the real book on L6M / PRE / HOLD mean):
| book | shift5 L6M/PRE/HOLD | side L6M/PRE/HOLD | days L6M/PRE/HOLD |
|---|---|---|---|
| CLK|MON_TUE|19:00|cont|60/60|look30|T60 | 0.92/0.96/0.98 | 0.82/0.72/0.97 | 0.86/0.66/0.99 |
| ORB|MON_TUE|18:00|brk|60/60|rng30|T120 | 0.79/1.00/0.91 | 0.74/0.93/0.92 | 0.87/0.97/0.97 |
| ORB|MON|18:00|brk|60/60|rng30|T120 | 0.85/1.00/1.00 | 0.94/0.95/0.99 | 0.95/0.97/1.00 |
| CLK|MON_TUE|19:00|cont|60/60|look30|T180 | 0.96/0.78/1.00 | 0.87/0.82/0.98 | 0.89/0.73/1.00 |
| ORB|MON_TUE|18:00|brk|60/60|rng30|T240 | 0.51/0.93/0.88 | 0.68/0.96/0.91 | 0.74/0.98/0.96 |
| ORB|MON|18:00|brk|60/60|rng30|T240 | 0.74/0.98/0.99 | 0.84/0.80/0.97 | 0.91/0.80/1.00 |
| CLK|ALL|15:00|fade|1R-ATR|look60|T60 | 0.72/0.42/0.54 | 0.77/0.84/0.84 | 0.73/0.81/0.79 |
| ORB|ALL|18:00|brk|60/60|rng30|T240 | 0.74/0.46/0.86 | 0.75/0.83/0.74 | 0.79/0.71/0.78 |
| ORB|MON_TUE|18:00|brk|rangeR|rng30|T240 | 0.73/0.69/0.89 | 0.67/0.66/0.80 | 0.79/0.75/0.94 |

Reading: the only broad book with all four years positive per trade is the Mon-Tue 19:00 Asia continuation (enter at 19:00 ET in the direction of the previous 30 minutes' move, bracket 60/60, time stop 180 min): 371 trades, $/trade 2023 +30, 2024 +19, 2025 +179, 2026 +351 (2 lots), but it is a recent-strengthening pattern (PRE rank vs shift/side/days placebos 0.73-0.82, HOLD 0.98-1.0), halves with 1 pt slippage in L6M (577 -> 386), is not TOLERANT under the 1R-ATR bracket, and the stack already makes its best money in exactly that cell (Mon/Tue 19:00-21:00, +370..+700 per trade). The opening-range breakouts (Asia 18:00 Mon / Mon-Tue, 60/60) rank 0.9-1.0 on HOLD and PRE vs placebo but L6M 0.74-0.95; their maxDD (10.0-10.5k L6M, 25.7-34.1k worst-20 in PRE) is 18-20x the weekly mean; the 15:00 settlement-window fade and 16:00 books lose (cont) or are flat (fade). ORB London 02:00/03:00 do not pass; the RTH 09:30 ORB (breakout of the first 30 minutes, 60/60) is strongly negative recently (L6M -2,660/wk, HOLD -1,700) while positive in PRE (+1,594): a regime flip, so its fade (range failure) is the untested mirror (not built here, a post-hoc inversion). The range-as-stop ORB variants have maxDD 19-30k on $400-500/wk.
Settlement window 16:00-17:00: the stack has zero entries there; the clock books at 16:00 (all days) were in the grid but the harness flat time is 16:55, so only 55-minute holds exist; none passed TOLERANT or NOW-ONLY (16 books, L6M -574..+59, HOLD -797..+318; T60 and T180 are identical because the harness flattens at 16:55).

## Multiple-comparison note
636 books were scored (368 event, 268 window), about 1,900 evaluations including slippage, with variants that are near-duplicates of each other (same trades through different time stops). Family-level placebo counts above are the correct reference: the real grids pass the gates at the placebo rate. Per-book placebo p-values use 200 draws (resolution 0.005, one-sided), so a Bonferroni correction over 636 cannot be met by any book. Direction rule `sign` and the choice of CPI/NFP/ISM as the story were taken after the census (in-sample), and L6M is 5-6 events per type.
