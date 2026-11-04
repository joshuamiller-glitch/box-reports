# DS3_PB_ASIA - reconcile PB asia (DIS-AD), BASE-4, 2026-11-04T21:58Z

Scope note l2vast/ds3/prereg/DISAD_scope.md sha256 9ce7146c0e0893c0a8de0470a01b61330fecee0c51c5e83e92fce87ccd0a3044 (DECISIONS.md, before any number). Descriptive, no PASS, nothing live, forward-safe placebos only (delay >= 5 min = the shift5 logic, or a side-independent random-time unconditional drift). Code l2vast/ds3/code/disad/ (ad_o1, ad_an1, ad_o2, ad_an2, ad_doc); data /mnt/l2/l2vast/ds3_base4/ad_*.pkl.

## Verdict (which of (i)-(iii) is the artefact)
**(ii) is the artefact, in its reading; (i) and (iii) are real but are statements about different windows and different objects.** (ii) "PB asia sits below its causal drift" is a statement about the L6M / HOLD windows (May-Oct 2026 and Nov 2025-Oct 2026) in which PB timing was worse than a delayed entry; it does not mean PB has no directional edge: the benchmark used there (the same trades delayed 5..120 min, same side) is NOT drift - it keeps the signal's side and day selection, so it measures only ENTRY TIMING. Decomposed (1-min V2 object, pts/trade at the 2023-26 price scale), PB post-2023 = unconditional side drift -1.22 + side/day information +4.20 + timing +1.00 = +3.98 net; the timing term is +2.69 in 2023-25 and -1.79 in 2026 (1-s object: +4.49 in 2024, +1.65 in 2025, -1.59 in 2023 and -1.41 in 2026). The DIS-M window values (L6M real +12 vs +532 delayed, X3 60/60 replica) therefore describe 2026 only; over 2023-26 as a whole the excess over the delayed entry is +1.00 pts/trade and over the side-independent drift +5.19. (i) is not an artefact of costs: PB's gross pts per trade are -0.69 pre-2023 (SE +1.15) and +5.01 post-2023 (SE +1.85); but it is a 2023-25 phenomenon (2023-25 net +7.45, 2026 net -1.76) and 45% of its post-2023 weekly P&L sits in the best five weeks (the other weeks still average $255/wk against $449/wk with them). (iii) "A7 adds about +254 $/wk (L6M)" is the LIVE-exit object in the weakest window: O3 live L6M +222 $/wk, HOLD +357, PRE +1048, MID -136 against the X3 60/60 replica L6M +12, HOLD +213, PRE +988, MID +458 - the live Trade-Health exits recover about +$200/wk in L6M and lose about $600/wk in MID versus the plain 60/60 exit, so (iii) vs (ii) is an exit-object difference, not a contradiction of sign in the same object.

**Is PB's pre-2023 negativity cost or signal?** Mostly cost under the V2 percent convention, partly signal: gross (zero-cost) pts per trade pre-2023 = -0.69 (SE +1.15, 2,705 trades), cost = +1.43, net = -2.12. With costs held at 2023-26 POINT levels (tick-floor, not scaled down by price) net is -4.78. The signal is slightly negative or flat before 2023 (gross -0.69; after-entry move to the session end -5.37 pts, 47% of trades positive) and clearly positive 2023-25 (gross +8.23); the pre-2023 net deficit is about two-thirds cost (V2) or about 85% cost (tick-floor), and the cost per trade is 1.0-1.5 pts in every year (2.9 in 2013).

## 1. Pre / post decomposition, Asia cells (O1: 1-min V2 object, pts per trade at the 2023-26 price scale; post = 2023-04-03..2026-10-30)
| book | period | n | net | gross | cost | net with tick-floor costs | P1c (delayed, same side) | D (unconditional side drift, trade-weighted) | S = P1c - D | T = net - P1c | H60 (hold 60 min) | E = net - H60 | net long / short | D long / short | after-entry move to 02:00 (side-signed), % positive |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| PB | pre 2013-2023Q1 | 2705 | -2.12 | -0.69 | +1.43 | -4.78 | -1.94 | -0.73 | -1.21 | -0.19 | -1.39 | -0.73 | +1.10 / -6.25 | +3.16 / -5.70 | -5.37, 47% |
| PB | post 2023-26 | 1034 | +3.98 | +5.01 | +1.04 | +4.16 | +2.98 | -1.22 | +4.20 | +1.00 | -0.24 | +4.21 | +5.66 / +1.95 | +0.14 / -2.85 | +5.47, 54% |
| PB | 2023-25 | 644 | +7.45 | +8.23 | +0.78 | +7.38 | +4.77 | -1.01 | +5.77 | +2.69 | +0.17 | +7.28 | +8.17 / +6.48 | +0.93 / -3.62 | +8.40, 55% |
| PB | 2026 | 390 | -1.76 | -0.30 | +1.46 | -1.16 | +0.02 | -1.37 | +1.40 | -1.79 | -1.02 | -0.74 | +0.89 / -4.42 | -1.12 / -1.62 | +0.62, 53% |
| SM | pre 2013-2023Q1 | 1774 | -0.99 | +0.23 | +1.22 | -4.36 | -1.08 | -1.21 | +0.13 | +0.09 | -0.35 | -0.65 | +1.95 / -4.12 | +2.10 / -4.71 | +0.14, 46% |
| SM | post 2023-26 | 669 | +3.11 | +3.88 | +0.77 | +3.14 | +1.21 | -1.42 | +2.64 | +1.90 | -0.56 | +3.67 | +4.58 / +1.63 | -0.68 / -2.17 | +0.29, 54% |
| SM | 2023-25 | 456 | +4.96 | +5.64 | +0.68 | +4.88 | +4.34 | -1.43 | +5.77 | +0.62 | -0.28 | +5.25 | +5.69 / +4.19 | +0.08 / -3.02 | +2.51, 54% |
| SM | 2026 | 213 | -0.86 | +0.13 | +0.99 | -0.58 | -5.62 | -1.26 | -4.36 | +4.75 | -1.20 | +0.34 | +2.02 / -3.45 | -2.43 / -0.20 | -4.45, 54% |
| KB | pre 2013-2023Q1 | 5557 | -2.13 | -1.04 | +1.09 | -4.57 | -2.58 | -1.29 | -1.29 | +0.46 | -1.21 | -0.92 | +1.68 / -5.90 | +1.95 / -4.50 | -1.68, 47% |
| KB | post 2023-26 | 1957 | +1.62 | +2.44 | +0.82 | +1.68 | +0.62 | -1.34 | +1.96 | +1.00 | -0.76 | +2.38 | +2.74 / +0.45 | -0.31 / -2.41 | +4.12, 51% |
| KB | 2023-25 | 1325 | +1.50 | +2.51 | +1.00 | +1.44 | +1.11 | -1.31 | +2.41 | +0.39 | -1.32 | +2.82 | +2.64 / +0.26 | +0.17 / -2.92 | +5.31, 51% |
| KB | 2026 | 632 | +1.86 | +2.29 | +0.43 | +2.18 | -0.41 | -1.34 | +0.93 | +2.27 | +1.15 | +0.71 | +2.95 / +0.82 | -1.32 / -1.36 | +1.65, 51% |
| PE | pre 2013-2023Q1 | 5310 | -1.42 | -0.25 | +1.17 | -4.05 | -1.07 | -1.14 | +0.07 | -0.34 | -1.53 | +0.11 | +1.38 / -4.45 | +1.99 / -4.53 | -3.42, 47% |
| PE | post 2023-26 | 1898 | +0.88 | +2.06 | +1.19 | +0.95 | +1.33 | -1.39 | +2.73 | -0.46 | -0.53 | +1.41 | +0.74 / +1.02 | -0.30 / -2.48 | +2.63, 50% |
| PE | 2023-25 | 1291 | +0.79 | +2.08 | +1.29 | +0.72 | +1.02 | -1.38 | +2.41 | -0.23 | -0.42 | +1.21 | +0.82 / +0.76 | +0.20 / -2.98 | +3.43, 50% |
| PE | 2026 | 607 | +1.06 | +2.03 | +0.97 | +1.44 | +1.99 | -1.38 | +3.37 | -0.93 | -0.90 | +1.96 | +0.55 / +1.53 | -1.34 / -1.41 | +0.93, 52% |

Reading: D (what a trade of the same side earns at a random Asia time) is about -1 pt for every book and period (long +3/short -6 pre-2023, about -0.3 / -2.5 post: the sides are very asymmetric because NQ drifted up and the 60/60 bracket holds to the 16:55 flat) so drift alone is not the edge; S (the side/day information, measured at delayed entries) carries the post-2023 edge in every book (PB +4.20, SM +2.64, KB +1.96, PE +2.73) and is about zero or negative before; timing T is small (PB +1.00, SM +1.90, KB +1.00, PE -0.46 post). Exit E (bracket vs holding 60 minutes) is where the money is: the signals' 60-minute forward return is about zero (H60 -0.2 to -0.8) while the bracket (target or the 16:55 hold) earns +4.21 (PB) to +3.67 (SM): the edge is directional persistence beyond an hour, not a short-horizon entry edge.

## 2. PB asia by year, 1-min V2 object (2013-2026; 2023 and 2026 partial)
| year | n | net | gross | cost | P1c | D | S | T | H60 | E | net long | net short | D long | D short | after-entry move | $/wk 1 lot |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 2013 | 201 | -8.73 | -5.84 | +2.89 | -11.53 | -1.24 | -10.29 | +2.80 | -1.34 | -7.39 | -6.80 | -11.20 | +5.05 | -9.32 | +24.80 | -662 |
| 2014 | 175 | -0.43 | +0.56 | +0.98 | -4.57 | +0.37 | -4.95 | +4.15 | -0.90 | +0.47 | +10.74 | -15.67 | +7.90 | -9.90 | +28.32 | -28 |
| 2015 | 234 | -1.52 | -0.52 | +1.00 | -1.98 | -0.31 | -1.67 | +0.46 | -1.41 | -0.11 | +1.29 | -5.22 | +4.08 | -6.08 | +70.53 | -134 |
| 2016 | 303 | -0.09 | +0.89 | +0.98 | +2.26 | -0.99 | +3.25 | -2.35 | -0.17 | +0.08 | -1.36 | +1.24 | -0.87 | -1.12 | +85.94 | -11 |
| 2017 | 192 | +5.21 | +6.14 | +0.93 | +4.60 | +1.28 | +3.32 | +0.61 | -1.10 | +6.31 | +15.82 | -9.63 | +12.65 | -14.64 | +25.17 | +385 |
| 2018 | 261 | +0.88 | +2.09 | +1.20 | +2.99 | -0.60 | +3.59 | -2.10 | -1.62 | +2.51 | +1.06 | +0.65 | +3.40 | -6.01 | +55.92 | +87 |
| 2019 | 269 | -6.31 | -5.25 | +1.06 | -7.79 | -0.67 | -7.12 | +1.48 | -1.98 | -4.33 | -1.57 | -12.39 | +1.67 | -3.65 | +49.09 | -641 |
| 2020 | 448 | -4.52 | -2.14 | +2.37 | -3.57 | -0.92 | -2.65 | -0.95 | -2.78 | -1.73 | +1.42 | -12.15 | +3.55 | -6.68 | +108.24 | -764 |
| 2021 | 265 | -1.91 | -0.45 | +1.46 | -1.60 | -0.78 | -0.82 | -0.31 | -0.53 | -1.38 | -0.63 | -4.10 | +0.88 | -3.61 | +56.47 | -195 |
| 2022 | 311 | -3.53 | -2.51 | +1.02 | -1.47 | -1.13 | -0.35 | -2.06 | -1.70 | -1.83 | -6.24 | -0.59 | +0.60 | -3.00 | +104.72 | -423 |
| 2023 | 177 | +4.97 | +5.89 | +0.92 | +4.54 | -1.49 | +6.03 | +0.44 | -2.45 | +7.43 | +8.68 | +1.47 | -1.04 | -1.91 | +45.33 | +339 |
| 2024 | 235 | +6.18 | +7.08 | +0.90 | +4.12 | -0.56 | +4.68 | +2.06 | +1.51 | +4.67 | +3.09 | +11.16 | +1.87 | -4.47 | +73.07 | +548 |
| 2025 | 278 | +10.89 | +11.48 | +0.59 | +6.41 | -0.88 | +7.29 | +4.48 | +0.25 | +10.64 | +14.24 | +6.28 | +1.40 | -4.04 | +72.95 | +1142 |
| 2026 | 390 | -1.76 | -0.30 | +1.46 | +0.02 | -1.37 | +1.40 | -1.79 | -1.02 | -0.74 | +0.89 | -4.42 | -1.12 | -1.62 | +82.91 | -327 |

(the move column of the yearly table is side x the whole Asia session net move, which includes the move before the entry and is mechanically positive for a pullback entry that fires after a move; the pre/post table above uses the post-entry move to 02:00.) Long/short asymmetry: longs earn in every up-Asia year (2014, 2017, 2023-25) and shorts lose in most (2013-2015, 2017, 2019-2022); the short side is the pre-2023 loss (net short -6.25 vs long +1.10 pts) and is where the post-2023 gain is smaller (+1.95 vs +5.66); in 2026 the sides split (long +0.89, short -4.42).

## 3. Top-5-weeks concentration (O1 weekly $ at 1 lot, V2)
| book | window | weeks | total $ | top-5 weeks $ | top-5 share of the total | mean $/wk | mean excluding the top 5 |
|--|--|--|--|--|--|--|--|
| PB | post | 183 | +82218 | +36812 | 45% | +449 | +255 |
| PB | pre | 531 | -114896 | +34303 | n/a (total <= 0) | -216 | -284 |
| PB | whole | 714 | -32678 | +39163 | n/a (total <= 0) | -46 | -101 |
| SM | post | 181 | +41601 | +25098 | 60% | +230 | +94 |
| SM | pre | 527 | -35273 | +25098 | n/a (total <= 0) | -67 | -116 |
| SM | whole | 708 | +6328 | +26294 | 415% | +9 | -28 |
| KB | post | 185 | +63327 | +54546 | 86% | +342 | +49 |
| KB | pre | 535 | -236593 | +57238 | n/a (total <= 0) | -442 | -554 |
| KB | whole | 720 | -173266 | +65381 | n/a (total <= 0) | -241 | -334 |
| PE | post | 185 | +33285 | +49522 | 149% | +180 | -90 |
| PE | pre | 535 | -150648 | +54376 | n/a (total <= 0) | -282 | -387 |
| PE | whole | 720 | -117363 | +57888 | n/a (total <= 0) | -163 | -245 |

PB's best five post-2023 weeks (ISO) are [np.uint32(202519), np.uint32(202505), np.uint32(202638), np.uint32(202432), np.uint32(202526)]; they hold 45% of the post-2023 total; without them PB asia still averages $255/wk (positive), unlike PE (negative without its top 5) - PB is the least top-heavy of the four Asia cells after SM and PB, but 2024-2025 carry it.

## 4. The 1-s objects, 2023-26 (O2 = replica of the live signal rows at X3 60/60 flat, 1 lot, harness; O3 = engine live P&L with live exits and Trade-Health; forward-only shift5 placebo for P1c; side-independent random-time drift for D)
PB asia by year ($ per trade /20 = pts per trade):
| year | O2 n | O2 pts/trade | P1c (shift5) | D | T = O2 - P1c | S = P1c - D | O2 long | O2 short | O3 live trades | O3 live pts/trade | O3 long | O3 short |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 2023 | 123 | +1.02 | +2.61 | -1.12 | -1.59 | +3.73 | +0.56 | +1.50 | 123 | +0.63 | +0.02 | +1.25 |
| 2024 | 224 | +9.65 | +5.16 | -1.02 | +4.49 | +6.18 | +6.32 | +15.10 | 221 | +9.64 | +7.06 | +13.94 |
| 2025 | 299 | +7.28 | +5.62 | -0.87 | +1.65 | +6.50 | +10.09 | +3.35 | 295 | +9.04 | +11.87 | +5.09 |
| 2026 | 523 | +0.29 | +1.70 | -1.53 | -1.41 | +3.23 | +1.43 | -0.78 | 464 | +0.74 | +2.35 | -0.92 |

Windows, weekly $ (PB asia, live lots 1): 
| object | L1M | L3M | L6M | HOLD | MID | PRE | X' |
|--|--|--|--|--|--|--|--|
| O2 replica X3 60/60 (= DIS-M real) | -1665 | -848 | +12 | +213 | +458 | +988 | +227 |
| O2 shift5 delayed, same side | +2565 | +951 | +719 | +468 | +521 | +596 | +292 |
| O3 engine live P&L (live exits, TH) | +12 | -209 | +222 | +357 | -136 | +1048 | +208 |

Same objects for the other Asia cells, window weekly $: 
* SM: O2 real L6M +554 / HOLD +175 / PRE +479, shift5 L6M -406 / HOLD -330 / PRE +310, live O3 L6M +2707 / HOLD +2460 / PRE +1235.
* KB: O2 real L6M +1183 / HOLD +840 / PRE +428, shift5 L6M -199 / HOLD -137 / PRE +376, live O3 L6M +1433 / HOLD +1377 / PRE +772.
* PE: O2 real L6M +1961 / HOLD +1060 / PRE +378, shift5 L6M +896 / HOLD +519 / PRE -12, live O3 L6M +12915 / HOLD +7851 / PRE +4808.

## Reconciliation of the three numbers, side by side
| finding | object | window | number | what it measures |
|--|--|--|--|--|
| (i) ZL-2 PB +3.98 pts/trade, percentile 1.00 | O1 1-min V2, signals not live exits | 2023-04..2026-10 mean | net +3.98 (2023-25 +7.45, 2026 -1.76) | the raw PB entries with a 60/60 percent bracket earn in 2023-25 and not in 2026 |
| (ii) DIS-M PB asia below drift | O2 1-s replica X3 60/60 | L6M +12 vs delayed +532; HOLD +213 vs +359; PRE +988 vs ~+579 (excess +408) | negative excess in L6M / HOLD only | timing of PB entries vs delayed same-side entries (NOT drift), dominated by 2026 |
| (iii) Q11 A7 adds about +254 $/wk | O3 engine live P&L | L6M | +222 $/wk (HOLD +357) | the live-exit PB asia book in the weak 2026 window |

## Limits
* V2 costs are scaled by price, so pre-2023 costs in index points are below the tick; the tick-floor net is reported; no real pre-2023 fill model exists. * D uses random entries with the same 60/60 bracket, held to 16:55; it includes the next-RTH drift (the Asia trade holds past 02:00). * P1c/shift5 delays are same-side; with a trend-pullback signal a delayed entry keeps most of the edge, so T understates the value of the entry and S includes the signal's sense of direction and day. * O2 and O3 are 2023-26 only; the 1-s harness has no 2013-2023 data. * Top-5 weeks use ISO weeks of the label day. * Single-run bootstraps were not repeated; per-year means for draws are means of 100 draws (O1: 100, O2: 100).
