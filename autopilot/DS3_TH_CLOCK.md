# DS3_TH_CLOCK - the TH-L2 evaluation-clock question closed out: stored 10 s vs every second vs every book event (DIS-BY), BASE-4, 2026-11-05

Research only, $0, no PASS claims, nothing live. Scope note l2vast/ds3/prereg/DISBY_scope.md sha256 b2f5e75d4eb0cb897aa0c818add17c92f7ffb409c32c350ac5398d9523d70254 and addendum 1 sha256 8a325da4461939ad66251af525a494b5df5b189fe9add322904af0de9fbd95d6 (DECISIONS.md, before any DIS-BY number; addendum corrects the grid anchor: epoch second divisible by 10, not entry+10k; the first trace run with the wrong grid was discarded). Code l2vast/ds3/code/disby/; data /mnt/l2/l2vast/ds3_base4/bv/. Builds on DIS-BV (DS3_TH_FIDELITY.md): same 37 sample weeks (12 pre-cap, 25 post-cap), same engine frame (ts2 reference, live lots, x-cost 0.80).

## 1. Answer
1. **"Dips below -30 between grid rows" is CONFIRMED for the 401 post-cap trades only the 1-s trigger cuts:** 365 of 401 (91%) had NO stored grid second (epoch second divisible by 10) on a second with adverse >= 30 (class A), the other 36 (9%) had a grid row below -30 but the liquidity condition was false at every such row (class B, liquidity flicker); none (0) had a grid row with both conditions true. The median contiguous time below -30 at the cut was 2 s (75% <= 3 s, 97.5% under 10 s), and the median worst adverse was -32.8 points (75% of the trades never went beyond -31.0).
2. **Event-driven (every raw record, tick/book event) does not change the post-cap picture relative to 1-s; it makes the pre-cap picture worse.** Post-cap TH gain per week (variant minus TH off): stored 10-s 18,076, 1-s 9,903, event-driven 10,734 (event minus 1-s 831, 90% interval -602 .. 2,205). Pre-cap: 829 / 282 / -3,350 (event minus 1-s -3,632, interval -7,904 .. -207). Event-driven cuts a further 211 trades the 1-s trigger does not (all 37 weeks), agreement with 1-s 98.5% (kappa 0.95), with the stored grid 95.0% (kappa 0.85).
3. **Cost interaction (extra slippage per lot on the cut exit):** the post-cap gain falls from 18,076 (stored, +0) to 12,902 at +1 and 7,761 at +2 points; for the 1-s clock 9,903 / 5,155 / 340; for event-driven 10,734 / 6,556 / 1,558. At +2 points the 1-s and event-driven gains are about zero (340 and 1,558 per week). The drawdown benefit does not go away: post-cap 25-week maxDD with TH off is $91,353; with the cut at +2 points it is still $75,028 (stored), $72,089 (1-s), $70,050 (event-driven). The same holds on the V2 live-window base (section 4).
4. **What the live box must log** is in section 6. Until it does, the evaluation clock of the TH-L2 cut in live is unknown and the research number for the cut's dollar gain should be read as the 1-s / event-driven value (about 55-60% of the stored-grid value at zero slippage), not the stored-grid value.

## 2. (1) Trace of the 401 post-cap trades only the 1-s trigger cuts (full rule)
Per trade from the 1-s path: worst adverse, first second below -30, contiguous episodes below -30, the R1 fire second, the stored grid seconds (epoch second divisible by 10) on or inside the episode, the liquidity condition at those grid rows. Table per trade: /mnt/l2/l2vast/ds3_base4/bv/by_trace.parquet.
| class | meaning | n | share | adverse returns above -15 within 60 s of the cut |
|--|--|--|--|--|
| A | no grid second falls on a second with adverse >= 30 (pure between-rows dip) | 365 | 91.0% | 49% |
| B | >= 1 grid second with adverse >= 30, liquidity false at all of them | 36 | 9.0% | 8% |
| C | a grid row had both true and still no stored fire (anomaly) | 0 | 0.0% | - |
Distribution (n = 401): worst adverse median -32.8, 25% quantile -36.2, 75% -31.0, min -57.2 points; seconds below -30 in total: median 3, mean 8.1, max 204; contiguous episode at the fire second: quantiles 5/25/50/75/95% = 1 / 1 / 2 / 3 / 7 s; fire second after entry median 353 s.
Outcome: the cut is on average -51.5 points per lot worse than the original exit (70% of the 401 cuts are negative), and 75% of these trades finished above -30 (median final unrealised 48.8 points before exit cost). So the trades were cut at the bottom of a short wick and then mostly recovered: the reading in DS3_TH_FIDELITY.md is confirmed, not just consistent.

## 3. (2) Event-driven variant from raw mbp-10 and the three clocks
Construction (scope note): evaluated at every raw record of the front contract with state up to and including that record only: last trade print price (raw price plus the per-trade library-minus-raw offset, estimated from the 1-s table vs the engine path, constant on 98.5% of the seconds of a trade; 23 of 18,477 trades had no usable offset and keep their 1-s rows), 5-s cancel sum on the supporting side over (t-5 s, t], median of the 10 behind-side levels from the last consistent snapshot (flag 128) before t, evaluation from entry+1 s to closed-1 s, cut price = trade price at the firing record, market cost 0.995 as in the engine. Same engine injection as DIS-BV (one K row per trade-second: the firing record, else the most adverse record). The EV cut price is a print, not a fill: no spread, no latency.
| window | rule | comparison | fires A | fires B | only B | agreement | kappa | lag B-A, seconds q05 / q25 / q50 / q75 / q95 | same second | cut delta B-A on common fires (pts/lot summed) | cut on only-B fires (pts/lot summed) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| post-cap | full | S vs R1 | 8,567 | 8,968 | 401 | 96.4% | 0.894 | -432 / -24 / -7 / -3 / 0 | 10% | 16,253 | -20,648 |
| post-cap | full | S vs EV | 8,567 | 9,138 | 571 | 94.9% | 0.845 | -660 / -45 / -10 / -5 / 0 | 6% | 25,565 | -31,805 |
| post-cap | full | R1 vs EV | 8,968 | 9,138 | 170 | 98.5% | 0.951 | -124 / -3 / 0 / 0 / 0 | 56% | 10,151 | -11,997 |
| post-cap | arm-only | S vs R1 | 8,609 | 8,978 | 369 | 96.7% | 0.902 | -294 / -18 / -7 / -3 / 0 | 10% | 14,891 | -18,497 |
| post-cap | arm-only | S vs EV | 8,609 | 9,140 | 531 | 95.2% | 0.855 | -519 / -37 / -9 / -4 / 0 | 6% | 24,275 | -29,018 |
| post-cap | arm-only | R1 vs EV | 8,978 | 9,140 | 162 | 98.6% | 0.953 | -107 / -3 / 0 / 0 / 0 | 58% | 10,216 | -11,353 |
| pre-cap | full | S vs R1 | 2,142 | 2,238 | 96 | 96.6% | 0.906 | -1758 / -46 / -8 / -3 / 0 | 10% | 4,270 | -3,261 |
| pre-cap | full | S vs EV | 2,142 | 2,279 | 137 | 95.2% | 0.863 | -2656 / -112 / -15 / -5 / 0 | 5% | 6,539 | -6,034 |
| pre-cap | full | R1 vs EV | 2,238 | 2,279 | 41 | 98.6% | 0.956 | -268 / -4 / 0 / 0 / 0 | 52% | 2,447 | -2,951 |
| pre-cap | arm-only | S vs R1 | 2,205 | 2,269 | 64 | 97.8% | 0.934 | -362 / -22 / -7 / -3 / 0 | 11% | 3,033 | -3,304 |
| pre-cap | arm-only | S vs EV | 2,205 | 2,301 | 96 | 96.6% | 0.899 | -685 / -44 / -10 / -5 / 0 | 6% | 5,082 | -5,909 |
| pre-cap | arm-only | R1 vs EV | 2,269 | 2,301 | 32 | 98.9% | 0.965 | -154 / -3 / 0 / 0 / 0 | 57% | 2,159 | -2,715 |
S = stored 10-s grid, R1 = every second, EV = every record. Negative lag = B fires earlier. Time stamps of EV rows are at one-second resolution (the second containing the record).

Engine (weekly sums of the sample weeks, TH gain = variant minus TH off, $/week; maxDD = weekly-cumulative maxDD of the listed weeks in calendar order; drawdown first):
| window | TH off maxDD | S maxDD | R1 maxDD | EV maxDD | S gain | R1 gain | EV gain | R1 arm-only gain | EV arm-only gain | S arm-only gain |
|--|--|--|--|--|--|--|--|--|--|--|
| post-cap 25 wk | 91,353 | 62,576 | 67,067 | 63,929 | 18,076 | 9,903 | 10,734 | 10,121 | 10,950 | 16,630 |
| pre-cap 12 wk | 16,345 | 7,964 | 5,198 | 9,732 | 829 | 282 | -3,350 | -2,670 | -4,994 | 306 |
Week-bootstrap (5,000 draws) of mean differences, $/week (90% interval): post-cap R1 - S -8,173 (-12,860 .. -3,601), EV - S -7,342 (-12,652 .. -2,231), EV - R1 831 (-602 .. 2,205); pre-cap R1 - S -547 (-4,142 .. 2,632), EV - S -4,179 (-10,372 .. 1,350), EV - R1 -3,632 (-7,904 .. -207).
Reading: going from every second to every record changes the post-cap result by +831/wk (inside noise); both are about 59% of the stored-grid gain. The event-driven clock fires in a different second than the 1-s clock on 45% of the common fires (same second 55%, and almost never later) and adds 211 fires (1.9% of 1-s fires) that are almost all wicks (cut-only-B sum -14,948 points per lot). Pre-cap the extra event-level cuts lose money (EV minus 1-s -3,632/wk, interval excludes zero).

## 4. (3) Evaluation clock x extra slippage on the cut exit (full rule; engine frame x-cost 0.80 plus the extra points per lot)
**Q1-A ts2 reference base (the DIS-AX / DIS-BV frame).** TH gain per week = variant minus TH off on the same base; maxDD of the 25 post-cap sample weeks in brackets (TH off: $91,353 post-cap, $16,345 pre-cap).

Post-cap 25 weeks: $/week (maxDD of the window)
| evaluation clock | +0 pts | +1 pt | +2 pts |
|--|--|--|--|
| stored 10-s grid | 18,076 (62,576) | 12,902 (68,471) | 7,761 (75,028) |
| every second | 9,903 (67,067) | 5,155 (66,637) | 340 (72,089) |
| every book event | 10,734 (63,929) | 6,556 (63,697) | 1,558 (70,050) |

Pre-cap 12 weeks: $/week (maxDD of the window)
| evaluation clock | +0 pts | +1 pt | +2 pts |
|--|--|--|--|
| stored 10-s grid | 829 (7,964) | -1,490 (10,233) | -3,817 (12,501) |
| every second | 282 (5,198) | -2,166 (8,304) | -4,478 (11,410) |
| every book event | -3,350 (9,732) | -5,843 (14,978) | -8,257 (21,878) |

**DIS-BJ V2 live-window base (no new entries 09:00-09:59, 18:00-18:05, 15:00-16:54; ZL-2 naming; ties to DIS-BR: stored TH total $2,455,259.84).** TH gain per week = variant minus TH off on the same base; maxDD of the 25 post-cap sample weeks in brackets (TH off: $94,358 post-cap, $23,893 pre-cap).

Post-cap 25 weeks: $/week (maxDD of the window)
| evaluation clock | +0 pts | +1 pt | +2 pts |
|--|--|--|--|
| stored 10-s grid | 17,647 (59,964) | 13,148 (65,529) | 8,870 (70,829) |
| every second | 9,508 (63,350) | 5,637 (62,610) | 1,078 (67,752) |
| every book event | 10,373 (61,310) | 6,386 (60,041) | 1,683 (66,085) |

Pre-cap 12 weeks: $/week (maxDD of the window)
| evaluation clock | +0 pts | +1 pt | +2 pts |
|--|--|--|--|
| stored 10-s grid | -2,625 (7,643) | -4,690 (9,676) | -6,945 (12,480) |
| every second | -3,338 (7,437) | -5,453 (10,324) | -7,668 (13,210) |
| every book event | -6,649 (10,282) | -8,822 (14,330) | -11,105 (24,027) |

Totals (all 187 history weeks, 2023-26, $): live base TH off 2,243,133; stored 2,520,149 / 1,966,699 / 1,415,798 at +0 / +1 / +2; 1-s 2,309,250 / 1,764,899 / 1,222,344; event 2,286,452 / 1,755,824 / 1,207,443. The engine charges the slippage on every cut, so the full-history totals fall by about $0.5M per extra point for every clock; at +1 point every clock is already at or below TH off over the whole history (see the totals), which is the DIS-AX conclusion restated with the clock axis.

## 5. Stability summary
* Cut and no-cut: the three clocks agree on 95-98.5% of trades; the disagreement is entirely extra cuts at the faster clock (never a trade cut by the grid and not by the faster clocks).
* The money is in the clock, not the reconstruction: post-cap gain 18.1k (grid) -> 9.9k (1 s) -> 10.7k (event) per week; the arm-only versions give 16.6k -> 10.1k -> 10.9k, so the liquidity condition is not what separates the clocks.
* Cost sensitivity is larger than clock sensitivity: +1 point costs 5.2k (grid), 4.7k (1 s), 4.2k (event) per week post-cap.
* Drawdown: the cut reduces the 25-week post-cap maxDD from $91k to $62-67k at zero slippage and to $70-75k at +2 points, for every clock. The maxDD benefit is more robust than the dollar gain.

## 6. (4) What the live box must log to settle the clock
For every TH-L2 trade (not only the fires), from entry until exit:
1. The EVALUATION TIMESTAMPS: the instant of every evaluation of the rule (exchange ts_event of the last record included, receive time, and the box clock), plus the trigger type (timer / book event / trade print). If the box evaluates on a timer, log the timer period and the phase (the stored table uses epoch seconds divisible by 10; a live timer at 1 s or 10 s is distinguishable from an event-driven one by the spacing of evaluation instants).
2. At each evaluation: price used (and its timestamp), adverse in points, the 5-s pulled-support sum, the median behind-side level, the liquidity flag, the decision. One line per evaluation is enough while the trade is within 15 points of or beyond the arm level (adverse >= 15); below that nothing needs logging.
3. The ARM EVENT: the first instant adverse reached 30 and the first instant both conditions were true (these two instants and the evaluation that saw them are what separates the clocks; time below -30 before the cut is 2 s median in the trades in question).
4. The order: send time, acknowledgement, fill time, fill price, size, slippage vs the price used at the decision; and the original exit (stop/target) the trade would have had, with the post-cut path for 60 s (so that dip-and-recover cuts can be counted).
5. Near misses: evaluations with adverse >= 30 and liquidity false, and evaluations where the box was not running (gaps).
Decision rule once logged (descriptive): (i) fraction of live fires on 10-s boundaries (should be ~100% if the box mirrors the table, ~10% if it runs on a 1-s timer, spread over all instants if event-driven); (ii) number of cuts whose time below -30 before the cut was under 10 s and the trade then recovered above -15 within 60 s (the wick cuts, class A); (iii) mean slippage vs the decision price against the +0/+1/+2 axis in section 4. The Monday program can carry these as three counters.

## 7. Limits
* 37 of 187 weeks (12 pre-cap fixed-rule sample, all 25 eligible post-cap weeks); the post-cap 25 are the weeks behind the +18.1k/wk headline.
* EV cut price is the trade print at the firing record: no spread, no queue, no latency (DIS-AX covers 0-3 s latency); it is a bound on what an event-driven box could see, not a fill model. The slippage axis is the only cost handle here.
* Engine week effects (locks, governors, lot rounding) make single-week deltas much larger than trade-level deltas; read means, intervals and signs. Slippage is subtracted per lot from the cut delta as in DIS-AX; the engine frame is x-cost 0.80.
* One event per row second is kept in the K rows for the engine (the firing record, else the most adverse), so trades whose entry is shifted (PE/OTE rows) are re-evaluated from these rows only; the unshifted trades (the large majority) are exact.
* The V2 base here is ZL-2's naming (09:00-09:59 + 18:00-18:05 + 15:00-16:54), identical to the mask called V1 in DS3_LIVE_WINDOWS_XCHECK.md; TH-off on the same base is the reference.
