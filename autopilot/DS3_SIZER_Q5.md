# DS3_SIZER_Q5 - stale-bar / gap-window effect on the ER ladder (ZL-2, 2026-11-02T22:21Z; analysis only, the user decides)
Prereg SIZER_Q5_PREREG.md sha256 37b421cea5c2c08c7e163375697543483b8dc8cc561422568042e0812f827859 (DECISIONS.md, before any Q5 statistic). Frame: T-SIZER ts base (V13T_LIVE costs, sequential rounding, lock R scaled only when mult > 1, A06 not modelled, zone half before ER); reference L = live ladder; ER(20) on 5-min closes from S4b's builder (minutes without a print create no bar).

**HEADLINE.** 773 of 17,396 taken signals (4.4%) use a last closed 5-min bar older than 60 minutes (all of them are older than 5 and 15 minutes too: the stale ones are session-open signals after a maintenance break or weekend, not slightly late ones): HM asia 169, KB asia 402, PB asia 30, PE asia 172; their net is -139$ per trade (-108k total, mean ER 0.23, 29% at x1.5), worse than the other signals. 2667 taken signals (15%) have a 20-bar window spanning a step > 30 min (mostly asia: PE 868, KB 705, HM 653, PB 299, SM 140) and they are the BETTER trades (+265$/trade vs +123$/trade, +708k total). Neutralising them does not help: GAP_NAN L6M maxDD -6.0% (+5.9% dropped), PRE -3.4% at mean -1.9k / -2.0k per week; GAP_HALF +17.5% (+6.2% dropped), PRE -47.9%, mean -4.6k / -4.3k; SESS_ER -9.5% (-24.7% dropped), PRE +15.3%, mean -1.0k / -1.3k. Flags: none.

## 1. Diagnostics (taken signals, lots x1 net table)
| group | n | net $ per trade | net total $k | mean ER | share at x1.5 |
|--|--|--|--|--|--|
| age>5min | 773 | -139 | -108 | 0.23 | 29% |
| age>15min | 773 | -139 | -108 | 0.23 | 29% |
| age>60min | 773 | -139 | -108 | 0.23 | 29% |
| gap-window (step>30min in the 21 closes) | 2667 | +265 | +708 | 0.28 | 41% |
| no gap window | 14729 | +123 | +1818 | 0.29 | 44% |
| session-only ER defined | 12370 | +164 | +2034 | 0.30 | 46% |
| fewer than 10 bars in the current session | 5026 | +98 | +492 | 0.26 | 37% |

By book x session (taken signals): n, stale bar >5 min / >15 min / >60 min, gap-window n and its net $k, signals with fewer than 10 bars in the current session
| book | session | n | age>5m | >15m | >60m | gap-window n | gap-window net $k | <10 session bars |
|--|--|--|--|--|--|--|--|--|
| HM | asia | 1800 | 169 | 169 | 169 | 653 | +153 | 481 |
| HM | nyam | 560 | 0 | 0 | 0 | 1 | -1 | 289 |
| KB | asia | 2211 | 402 | 402 | 402 | 705 | +71 | 868 |
| KB | london | 1342 | 0 | 0 | 0 | 0 | +0 | 155 |
| KB | nyam | 1042 | 0 | 0 | 0 | 0 | +0 | 501 |
| KB | nypm | 810 | 0 | 0 | 0 | 0 | +0 | 269 |
| MV | london | 1538 | 0 | 0 | 0 | 0 | +0 | 187 |
| MV | nyam | 1350 | 0 | 0 | 0 | 0 | +0 | 631 |
| PB | asia | 1103 | 30 | 30 | 30 | 299 | +60 | 223 |
| PE | asia | 2100 | 172 | 172 | 172 | 868 | +358 | 766 |
| PE | london | 1330 | 0 | 0 | 0 | 0 | +0 | 138 |
| PE | nyam | 840 | 0 | 0 | 0 | 1 | +9 | 315 |
| SM | asia | 690 | 0 | 0 | 0 | 140 | +57 | 89 |
| SM | london | 680 | 0 | 0 | 0 | 0 | +0 | 114 |

## 2. Cells vs the live ladder
| cell | definition | mean lots | L6M cut (dropped) | HOLD | MID | PRE | X' | d mean L6M (MDE) | d mean PRE (MDE) | mean ok | FLAG |
|--|--|--|--|--|--|--|--|--|--|--|--|
| GAP_NAN | ER = NaN (x1.0) when the 21-close window spans a step > 30 min | 3.24 | -6.0% (+5.9%) | -6.0% | +38.8% | -3.4% | -12.0% | -1.9k (6.2k) | -2.0k (4.2k) | True |  |
| GAP_HALF | x0.5 on gap-window signals (others as the ladder) | 2.99 | +17.5% (+6.2%) | +17.5% | +43.9% | -47.9% | -26.6% | -4.6k (11.2k) | -4.3k (4.7k) | True |  |
| SESS_ER | ER from the current session's 5-min bars only (>= 10 bars, lookback min(20, bars-1)), else x1.0 | 3.30 | -9.5% (-24.7%) | -9.5% | -7.4% | +15.3% | +18.2% | -1.0k (10.8k) | -1.3k (6.1k) | True |  |

## 3. Equal-risk (exact lot scan, W29-W39 dropped in L6M/HOLD): mean of the cell at the ladder's maxDD (points within +-7.5% of the ladder's maxDD at lscale 1; n)
| cell | L6M-dropped: ladder / cell (n) | PRE: ladder / cell (n) | HOLD-dropped (n) |
|--|--|--|--|
| GAP_NAN | 64.6k / 54.9k (6) | 16.4k / 15.6k (5) | 39.7k / 37.9k (1) |
| GAP_HALF | 64.6k / 52.3k (5) | 16.4k / no point (0) | 39.7k / 48.8k (4) |
| SESS_ER | 64.6k / 56.6k (3) | 16.4k / 17.7k (3) | 39.7k / 40.6k (3) |

## 4. Placebo (100 draws, multipliers permuted within book x session over taken rows; rank = share of draws below the real cell) and exposure
| cell | rank cut L6M | rank mean L6M | rank cut PRE | rank mean PRE | mean lots | max lots | worst net lots (day) | worst stack risk $ (day) |
|--|--|--|--|--|--|--|--|--|
| GAP_NAN | 0.00 | 0.81 | 0.23 | 0.62 | 3.02 | 11 | 28 (20240726) | 33,600 (20230623) |
| GAP_HALF | 0.10 | 0.89 | 0.01 | 0.45 | 2.82 | 11 | 28 (20240726) | 33,600 (20230623) |
| SESS_ER | 0.04 | 0.82 | 0.48 | 0.71 | 3.06 | 11 | 28 (20240726) | 33,600 (20230623) |
| L | - | - | - | - | 3.01 | 11 | 28 (20240220) | 33,600 (20230623) |

Reading: stale bars are a session-open phenomenon in the Asia session (HM, KB, PB, PE); the first signals after a break are sized on an ER from before the break. Those 773 taken signals lose on average, but the gap-window signals as a whole are the profitable ones, so neutralising the ER on gap windows (NaN or x0.5) costs mean without a consistent drawdown gain; the current-session-only ER changes 36k signal multipliers and is judged in section 2-4.
