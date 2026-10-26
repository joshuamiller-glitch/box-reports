# REPORT Q40 - cost decomposition and passive-fill execution test for the gross-positive families (BATCH 5, Part 1)

**Verdict: NO RESCUE. 0 of 144 one-minute passive variants and 0 of 48 tick-replay variants rescue any object.** Passive limit entries at the signal level lower the per-signal net in every object (1-minute replay: mean improvement -$24 to -$55 per signal; NQ tick replay: -$39 to -$134), because the signals that never get filled are the ones that run away immediately and carry most of the profit. The cost problem is real only before 2023 and only for a few objects; for RB, HO, HOQ14 and ESQ20 the 2013-22 gross edge is itself negative, so cost is not the issue there. Pre-registered in PREREG_AUTOPILOT.md ('BATCH 5, Part 1') before any run; no new signal selection (objects are the cells identified in B7, Q2, Q12, Q14, Q1B, Q20, Q29).

## 1. Cost decomposition per round trip (1 contract; slippage 1 tick/side; commission $4.36)
| object | span | trades | gross $/trade | slippage $ (2 sides) | commission $ | net $/trade | cost % of gross | breakeven slip ticks/side |
|---|---|---|---|---|---|---|---|---|
| GCB7 | pre | 2908 | 26.8 | 20.0 | 4.36 | 2.5 | 91 | 1.1 |
| GCB7 | clean | 566 | 156.2 | 20.0 | 4.36 | 131.8 | 16 | 7.6 |
| GCB7 | oos | 348 | 504.9 | 20.0 | 4.36 | 480.6 | 5 | 25.0 |
| RBQ2 | pre | 4849 | -6.3 | 8.4 | 4.36 | -19.0 |  |  |
| RBQ2 | clean | 944 | 66.3 | 8.4 | 4.36 | 53.5 | 19 | 7.4 |
| RBQ2 | oos | 575 | 48.2 | 8.4 | 4.36 | 35.4 | 26 | 5.2 |
| HOQ2 | pre | 4811 | -14.1 | 8.4 | 4.36 | -26.9 |  |  |
| HOQ2 | clean | 955 | 61.1 | 8.4 | 4.36 | 48.4 | 21 | 6.8 |
| HOQ2 | oos | 565 | 90.1 | 8.4 | 4.36 | 77.3 | 14 | 10.2 |
| HOQ14 | pre | 7302 | -1.2 | 8.4 | 4.36 | -13.9 |  |  |
| HOQ14 | clean | 1435 | 50.7 | 8.4 | 4.36 | 38.0 | 25 | 5.5 |
| HOQ14 | oos | 844 | 50.3 | 8.4 | 4.36 | 37.6 | 25 | 5.5 |
| GCQ14 | pre | 3024 | 1.6 | 20.0 | 4.36 | -22.8 | 1,564 | -0.1 |
| GCQ14 | clean | 597 | 100.5 | 20.0 | 4.36 | 76.1 | 24 | 4.8 |
| GCQ14 | oos | 361 | 368.4 | 20.0 | 4.36 | 344.0 | 7 | 18.2 |
| NQQ12 | pre | 2328 | 12.3 | 10.0 | 4.36 | -2.0 | 116 | 0.8 |
| NQQ12 | clean | 471 | 121.2 | 10.0 | 4.36 | 106.8 | 12 | 11.7 |
| NQQ12 | oos | 278 | 184.2 | 10.0 | 4.36 | 169.8 | 8 | 18.0 |
| NQQ1B | pre | 8693 | 13.7 | 10.0 | 4.36 | -0.6 | 105 | 0.9 |
| NQQ1B | clean | 1639 | 94.9 | 10.0 | 4.36 | 80.5 | 15 | 9.1 |
| NQQ1B | oos | 1035 | 65.3 | 10.0 | 4.36 | 50.9 | 22 | 6.1 |
| RTYQ20 | pre | 411 | 56.8 | 10.0 | 4.36 | 42.4 | 25 | 5.2 |
| RTYQ20 | clean | 125 | 151.4 | 10.0 | 4.36 | 137.1 | 9 | 14.7 |
| RTYQ20 | oos | 93 | 119.5 | 10.0 | 4.36 | 105.1 | 12 | 11.5 |
| ESQ20 | pre | 627 | -95.9 | 25.0 | 4.36 | -125.3 |  |  |
| ESQ20 | clean | 116 | 110.1 | 25.0 | 4.36 | 80.8 | 27 | 4.2 |
| ESQ20 | oos | 87 | 240.5 | 25.0 | 4.36 | 211.2 | 12 | 9.4 |
| CLQ29 | pre | 846 | 2.3 | 20.0 | 4.36 | -22.0 | 1,046 | -0.1 |
| CLQ29 | clean | 161 | 83.0 | 20.0 | 4.36 | 58.6 | 29 | 3.9 |
| CLQ29 | oos | 125 | 147.7 | 20.0 | 4.36 | 123.3 | 16 | 7.2 |

Reading: in the clean and H1/H2 windows costs are 5-30% of gross, so execution savings cannot create an edge there; in 2013-22 the cost is 91% of the GC gross ($26.8 gross vs $24.4 cost; breakeven slippage 1.1 ticks per side), exceeds gross for NQ (NQQ12 $12.3 gross vs $14.4 cost, NQQ1B $13.7 vs $14.4), GCQ14 ($1.6 vs $24.4) and CLQ29 ($2.3 vs $24.4), and RB, HO, HOQ14, ESQ20 have negative gross before cost. Other objects: Q25 NG (daily window, 2013-22 gross -$43,980 on 1,549 trades; clean +$16,440 on 300; $24.4 cost per trade, net clean +$9,132); B11 CL OR15 fade (hold to close with 0.2 ADR stop, per trade gross -$33.4 pre-2023, +$65.1 clean, +$105.5 H1+H2 vs $24.4 cost); Q26 momentum (per leg, 14 outrights, 2 legs per group slot): gross +$36 / +$52 / -$54 per leg and cost $122 / $93 / $107 per leg in 2013-22 / clean / H1+H2 for the 10:30 g=2 cell, so even a perfect fill-at-mid would leave it at -$86 / -$41 / -$162 net; passive execution could save at most the entry tick ($50-60 per leg) and was not tested (multi-instrument, trade data on disk only for NQ/ES: data-gated).

## 2. One-minute passive replay (all objects, bars only)
Fill model ('passive fills only'): limit at the signal-row close improved by d ticks (d in {0,1}), placed after a 1-minute latency, working W minutes (W in {5,15}); fill models touch (q0), q50 (touch-only fills kept with probability 0.5 by a deterministic hash; through-fills always), through1 (price trades one tick through); entry at the limit price with no slippage, same absolute time exit as the market version with 1 tick adverse exit slippage, commission as before, unfilled = missed trade, one position at a time on the market timing. 12 variants per object, 12 objects in the family (144 variants); null = 40 timing-destroyed event sets per object through the same machinery.
| object | market net $/signal | mean passive improvement $/signal (12 variants) | best variant | mean fill rate | market net of the UNFILLED signals $/signal | median null p95 of improvement | rescues |
|---|---|---|---|---|---|---|---|
| CLQ29 | 5.5 | -55.1 | -47.3 | 81% | 356 | 5.8 | 0 |
| ESQ20 | -63.1 | -7.8 | 0.1 | 87% | 191 | 14.7 | 0 |
| GCB7 | 61.8 | -43.0 | -37.2 | 83% | 357 | -0.4 | 0 |
| GCQ14 | 19.5 | -33.3 | -23.6 | 84% | 300 | -5.5 | 0 |
| HOQ14 | -0.1 | -28.2 | -26.7 | 85% | 232 | -20.1 | 0 |
| HOQ2 | -6.2 | -33.8 | -29.6 | 85% | 266 | -19.6 | 0 |
| NQQ12 | 29.6 | -67.3 | -62.3 | 87% | 591 | -19.3 | 0 |
| NQQ1B | 12.4 | -24.1 | -21.4 | 87% | 260 | -10.0 | 0 |
| RBQ2 | -6.1 | -29.9 | -26.5 | 85% | 246 | -14.6 | 0 |
| RTYQ20 | 68.8 | -38.4 | -32.7 | 87% | 354 | -0.6 | 0 |

Every object has a negative mean improvement; the only positive single variant is ESQ20 touch d=1 W=15 (+$0.1 per signal against a null p95 of +$20.7). The unfilled signals earn between $230 and $1,420 per signal at market, against $2-30 for the filled ones in the same variants: adverse selection, as in the FVG fill study.

## 3. Tick replay on actual trade prints (NQ and ES; other instruments data-gated)
Fill models through1 / q0 / q50 / q100 (queue ahead = trailing 15-minute volume at the price), latency 1 minute, W in {5,15} minutes, d in {0,1}, market benchmark = first print after placement + 1 tick, exits at the first print at/after the hold with 1 tick adverse; events whose series contract and print contract differ by more than 12 ticks (roll mismatch) are dropped; 16 variants per object; 20 null event sets per object in the same pass.
| object | signals replayed | market net $/signal (first print + 1 tick) | mean passive net | mean improvement | best variant improvement | mean fill | market net of unfilled signals | mean null p95 of improvement |
|---|---|---|---|---|---|---|---|---|
| ESQ20 | 222 | 86.5 | 77.4 | -9.1 | 3.4 | 87% | 209 | 30.6 |
| NQQ12 | 832 | 147.6 | 20.5 | -127.1 | -118.5 | 88% | 1,148 | -13.8 |
| NQQ1B | 3001 | 64.7 | 22.9 | -41.8 | -38.7 | 89% | 447 | -18.6 |

q50 and q100 coincide with through1 because fills come from prints through the limit (queue size does not matter), as found in the FVG study. NQQ12: market $147.6/signal vs passive $14-29; NQQ1B: $64.7 vs $19-26; ESQ20 (222 signals only): improvement -$27 to +$3.4 per signal, inside its null (p95 $18-44). The sleeve uplift at 20% with passive entries is not better than with market entries in any NQ variant on any span (see tick_variants.csv).

## 4. Dollar-sized statements
NQQ12 at 20% share is 2.5 NQ contracts: market per-signal net $147.6 times about 830 signals over 2023-26 is the sleeve's gross benefit; the passive version gives up $120-134 per signal ($100k+ over the window at that size). The worst single trade of NQQ12 is -$15.0k per NQ contract (-$38k at 2.5 contracts); passive entries do not change the exit risk.

## 5. Conclusion
Execution quality cannot rescue the gross-positive, cost-negative families: (i) in the modern window the costs are already small relative to gross, (ii) passive entries on fades and trend flips fill precisely when the trade is least attractive, and (iii) before 2023 the edge is too small or negative. The remaining cost lever would be reducing the exit slippage (market exits at 1 tick), which was not varied.

Code ap_q40_pass.py (1-minute), ap_q41_tick.py (tick replay); data outputs/autopilot/l/q40/ (decomp.csv, passive_variants.csv, tick_variants.csv).

DONE Q40
