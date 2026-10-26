# FAILPRED PART 1 - where DualStrat2 does not work (session level)
Benchmark: live Set A, corrected P9, 14/14, $4.84 RT. WF-sample = all 2859 sessions 2023-02..2026-10 (descriptive, full sample). Unit = (label day, ENTRY session). R = $16,800 (60 pts x $20 x 14). q25 by type: ASIA -19.8k, LONDON -13.8k, NY -4.4k
**Key facts (read these first).** (1) A session loses (F-A) 37.5% of the time pooled (Asia 45%, London 39%, NY 29%); 21% of sessions lose >= 1R. Failing sessions explain 35% of weekly P&L variance on their own (Asia 22%, London 7%, NY 6%) and every one of the 80 losing weeks has a failing-session sum below zero. (2) A failing session is a STOP-OUT session: 2.1 stops per session vs 0.72 (stop rate 71% vs 22% of trades); entries per session are not higher (1.6/1.4 vs 1.7/1.6). Stopped trades run ~67 pts adverse in both groups, so failing sessions are not worse-stopped, just stopped more. Lock exits are rarer in failing Asia sessions (0.05 vs 0.40 per session): the day locks do not rescue them. (3) Timing: Asia and London losses land in the last hour of the session (59% / 55% of losing P&L), NY losses early (32% in the first hour; first stop at median minute 52 vs 123). (4) Persistence is weak: only London after a failing Asia (45.9% vs 33.5%; F-B 40.6% vs 20.0%); Asia and NY show none; NY after Asia+London both failing 36.6% vs 28.8% base. (5) The two books fail together: both lose in 33% of both-traded sessions, they split in 30%; corr(ST,HM) 0.44. (6) Calendar / overnight context: 7 of 714 cells flag (about 18 would clear the CI rule by chance alone); the strongest are CPI days (London F-A 66%, n=44) and FOMC-day NY F-C 34% (n=29) - small samples, one look each. Pooled rows mix session types (Asia has the highest base rate), so a pooled gap or prior-session bucket can look high purely through the type mix; read the per-type columns.


## 1.1/1.2 Failure definitions: counts, means, variance share, losing weeks
| definition | group | sessions | failing (rate [Wilson 95%]) | mean P&L failing | mean P&L rest | share of weekly variance | losing weeks (of 80) explained alone / with a failing session |
|---|---|---|---|---|---|---|---|
| F-A  P&L<0 | ASIA | 954 | 425 (44.5% [41%,48%]) | -25,972 | 25,995 | 22% | 39 / 80 |
| F-A  P&L<0 | LONDON | 954 | 372 (39.0% [36%,42%]) | -18,930 | 13,629 | 7% | 29 / 77 |
| F-A  P&L<0 | NY | 951 | 274 (28.8% [26%,32%]) | -21,136 | 9,521 | 6% | 26 / 71 |
| F-A  P&L<0 | POOLED | 2859 | 1071 (37.5% [36%,39%]) | -22,289 | 15,732 | 35% | 80 / 80 |
| F-B  bottom quartile | ASIA | 954 | 239 (25.1% [22%,28%]) | -40,251 | 17,249 | 22% | 36 / 76 |
| F-B  bottom quartile | LONDON | 954 | 240 (25.2% [23%,28%]) | -26,683 | 10,215 | 7% | 29 / 71 |
| F-B  bottom quartile | NY | 951 | 238 (25.0% [22%,28%]) | -24,102 | 8,963 | 6% | 26 / 68 |
| F-B  bottom quartile | POOLED | 2859 | 717 (25.1% [24%,27%]) | -30,349 | 12,146 | 35% | 73 / 80 |
| F-C  loss>=1R ($16.8k) | ASIA | 954 | 287 (30.1% [27%,33%]) | -36,422 | 19,739 | 22% | 37 / 79 |
| F-C  loss>=1R ($16.8k) | LONDON | 954 | 176 (18.4% [16%,21%]) | -30,614 | 8,069 | 8% | 26 / 65 |
| F-C  loss>=1R ($16.8k) | NY | 951 | 148 (15.6% [13%,18%]) | -31,950 | 6,704 | 6% | 22 / 56 |
| F-C  loss>=1R ($16.8k) | POOLED | 2859 | 611 (21.4% [20%,23%]) | -33,666 | 11,044 | 36% | 71 / 80 |

Zero-trade sessions: ASIA 59, LONDON 311, NY 461 (P&L 0, never failing). Weekly P&L: mean 22,059, SD 102,178, 80 losing of 193 weeks. "Explained alone" = week loses but would not lose without the failing sessions (W minus failing >= 0); "with" = failing sessions sum < 0 in a losing week.

## 1.3 Anatomy of a failing session (ex post) - failing = F-B; rest = non-failing sessions with trades
| group | kind | n | entries/sess ST | HM | stops/sess | stop rate | MAE pts stopped / other | median min to first stop | share of losing P&L: first hr / middle / last hr | lock exits/sess |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | FAIL (F-B) | 239 | 1.75 | 1.62 | 2.83 | 84% | 65 / 25 | 452 | 2% / 39% / 59% | 0.05 |
| ASIA | rest (with trades) | 656 | 1.67 | 1.55 | 0.76 | 24% | 65 / 27 | 309 | 3% / 58% / 39% | 0.40 |
| LONDON | FAIL (F-B) | 240 | 1.38 | 1.21 | 1.80 | 69% | 68 / 38 | 390 | 1% / 44% / 55% | 0.36 |
| LONDON | rest (with trades) | 403 | 1.56 | 1.47 | 0.62 | 20% | 68 / 29 | 390 | 1% / 52% / 47% | 0.54 |
| NY | FAIL (F-B) | 238 | 1.59 | 1.39 | 1.76 | 59% | 67 / 36 | 52 | 32% / 62% / 6% | 0.45 |
| NY | rest (with trades) | 252 | 2.17 | 1.79 | 0.77 | 20% | 67 / 25 | 123 | 19% / 73% / 9% | 0.44 |
| POOLED | FAIL (F-B) | 717 | 1.57 | 1.41 | 2.13 | 71% | 67 / 34 | 224 | 11% / 47% / 42% | 0.29 |
| POOLED | rest (with trades) | 1311 | 1.73 | 1.57 | 0.72 | 22% | 66 / 27 | 270 | 6% / 60% / 35% | 0.45 |

Persistence (P(fail F-A next | fail now), chain = Asia->London->NY->next Asia; F-B in brackets):
| session | n | base F-A | after failing session F-A [Wilson] | after non-failing | lift | base F-B | after F-B | after non-F-B |
|---|---|---|---|---|---|---|---|---|
| ASIA (prior = previous session in chain) | 953 | 44.6% | 44.0% [38%,50%] (n 275) | 44.8% | 0.99 | 25.1% | 22.6% (n 239) | 25.9% |
| LONDON (prior = previous session in chain) | 954 | 39.0% | 45.9% [41%,51%] (n 425) | 33.5% | 1.18 | 25.2% | 40.6% (n 239) | 20.0% |
| NY (prior = previous session in chain) | 951 | 28.8% | 29.6% [25%,34%] (n 371) | 28.3% | 1.03 | 25.0% | 27.2% (n 239) | 24.3% |
| POOLED (prior = previous session in chain) | 2858 | 37.5% | 39.8% [37%,43%] (n 1071) | 36.1% | 1.06 | 25.1% | 30.1% (n 717) | 23.4% |
- ASIA after previous-day ASIA failed (F-A): 43.3% [39%,48%] vs 45.6% after non-fail (base 44.6%).
- LONDON after previous-day LONDON failed (F-A): 42.3% [37%,47%] vs 36.9% after non-fail (base 39.0%).
- NY after previous-day NY failed (F-A): 29.6% [24%,35%] vs 28.6% after non-fail (base 28.8%).
- Chain within a label day: P(London fail | Asia fail) = 45.9% vs 33.5%; P(NY fail | London fail) = 29.6% vs 28.3%; P(NY fail | Asia&London both fail) = 36.6% (n 194).

Book divergence (sessions where both books traded):
| group | sessions both traded | both lose | both earn | ST loses & HM earns | HM loses & ST earns | corr(ST,HM P&L) | one book loses >=1R while other earns |
|---|---|---|---|---|---|---|---|
| ASIA | 782 | 31% | 44% | 13% | 12% | 0.49 | 13.6% |
| LONDON | 456 | 35% | 30% | 18% | 17% | 0.40 | 16.2% |
| NY | 287 | 36% | 29% | 17% | 18% | 0.38 | 13.9% |
| POOLED | 1525 | 33% | 37% | 15% | 15% | 0.44 | 14.4% |

## 1.4 / 1.5 Calendar and overnight-context failure rates (714 (category x group x definition) cells inspected; flag = rate >= 1.5x base AND Wilson 95% lower bound > base)
**Flagged cells: 7 of 714** (about 18 would be expected by chance on the CI rule alone, before the 1.5x rule).
| variable | category | group | definition | n | fail rate [Wilson] | base | x base |
|---|---|---|---|---|---|---|---|
| CPI day | CPI day | LONDON | FA | 44 | 66% [51%,78%] | 39% | 1.69 |
| CPI day | CPI day | ASIA | FC | 44 | 48% [34%,62%] | 30% | 1.59 |
| CPI day | CPI day | ASIA | FB | 44 | 43% [30%,58%] | 25% | 1.72 |
| CPI day | CPI day | LONDON | FB | 44 | 41% [28%,56%] | 25% | 1.63 |
| FOMC day | FOMC day | NY | FC | 29 | 34% [20%,53%] | 16% | 2.22 |
| prior session result | prior session lost >=1R | LONDON | FC | 287 | 29% [24%,35%] | 18% | 1.59 |
| prior session result | prior session lost | LONDON | FC | 425 | 29% [25%,33%] | 18% | 1.56 |

Pooled F-A rates for every category (base in header; * = flagged on any definition for that group):
| variable | category | ASIA F-A | LONDON F-A | NY F-A | POOLED F-A [Wilson] (n) | pooled F-B | pooled F-C |
|---|---|---|---|---|---|---|---|
| weekday | dow0 | 44% | 32% | 31% | 35% [32%,39%] (570) | 25% | 21% |
| weekday | dow1 | 47% | 44% | 32% | 41% [37%,45%] (576) | 26% | 22% |
| weekday | dow2 | 49% | 42% | 29% | 40% [36%,44%] (570) | 26% | 24% |
| weekday | dow3 | 46% | 35% | 26% | 35% [32%,39%] (572) | 25% | 22% |
| weekday | dow4 | 36% | 43% | 26% | 35% [31%,39%] (571) | 23% | 18% |
| week of month | wom1 | 41% | 37% | 28% | 35% [32%,39%] (649) | 24% | 19% |
| week of month | wom2 | 49% | 41% | 26% | 39% [35%,42%] (671) | 27% | 23% |
| week of month | wom3 | 44% | 40% | 31% | 38% [35%,42%] (663) | 24% | 22% |
| week of month | wom4 | 47% | 39% | 30% | 39% [35%,42%] (651) | 26% | 22% |
| week of month | wom5 | 39% | 35% | 31% | 35% [29%,41%] (225) | 23% | 22% |
| month | month01 | 45% | 49% | 19% | 38% [31%,45%] (194) | 25% | 23% |
| month | month02 | 41% | 45% | 24% | 37% [31%,43%] (225) | 25% | 22% |
| month | month03 | 45% | 37% | 17% | 33% [28%,39%] (258) | 21% | 19% |
| month | month04 | 40% | 46% | 28% | 38% [32%,44%] (253) | 26% | 24% |
| month | month05 | 45% | 31% | 31% | 36% [30%,42%] (267) | 26% | 21% |
| month | month06 | 40% | 41% | 31% | 37% [32%,43%] (255) | 22% | 17% |
| month | month07 | 44% | 33% | 26% | 34% [29%,40%] (270) | 22% | 18% |
| month | month08 | 48% | 39% | 26% | 38% [32%,44%] (261) | 28% | 23% |
| month | month09 | 47% | 40% | 40% | 42% [36%,48%] (258) | 28% | 25% |
| month | month10 | 48% | 36% | 34% | 39% [33%,45%] (240) | 25% | 21% |
| month | month11 | 48% | 29% | 35% | 37% [30%,44%] (189) | 25% | 23% |
| month | month12 | 44% | 43% | 37% | 41% [34%,48%] (189) | 29% | 22% |
| FOMC day | FOMC day | 52% | 45% | 45%* | 47% [37%,58%] (87) | 31% | 28% |
| FOMC day | day before FOMC | 41% | 55% | 24% | 40% [31%,51%] (87) | 20% | 17% |
| FOMC day | day after FOMC | 41% | 28% | 31% | 33% [24%,44%] (87) | 25% | 24% |
| CPI day | CPI day | 57%* | 66%* | 30% | 51% [42%,59%] (132) | 36% | 27% |
| NFP day | NFP day | 23% | 42% | 15% | 27% [20%,35%] (127) | 17% | 13% |
| PCE day | PCE day | 53% | 42% | 28% | 41% [33%,50%] (129) | 26% | 19% |
| opex | opex day | 25% | 48% | 27% | 33% [26%,42%] (132) | 23% | 17% |
| month/quarter end | month end | 44% | 47% | 35% | 42% [34%,50%] (129) | 28% | 26% |
| month/quarter end | quarter end | - | - | - | 50% [36%,64%] (42) | 29% | 26% |
| holiday-adjacent | holiday-adj | - | - | - | 21% [9%,40%] (24) | 8% | 4% |
| short NY day (<15:00) | short NY day | 44% | 29% | 12% | 28% [21%,38%] (102) | 12% | 12% |
| roll week | roll week | 27% | 22% | 20% | 23% [17%,31%] (135) | 16% | 15% |
| any FOMC/CPI/NFP/PCE | any macro | 46% | 49% | 28% | 41% [37%,46%] (472) | 27% | 22% |
| prior session result | prior session lost | 44% | 46%* | 30% | 40% [37%,43%] (1071) | 29% | 25% |
| prior session result | prior session earned | 48% | 37% | 39% | 40% [37%,43%] (957) | 25% | 19% |
| prior session result | prior session lost >=1R | 44% | 49%* | 34% | 43% [39%,47%] (611) | 32% | 27% |
| prior day result | prior day lost | 44% | 39% | 28% | 37% [34%,40%] (1018) | 24% | 21% |
| prior day result | prior day earned | 46% | 41% | 31% | 40% [37%,42%] (1706) | 27% | 23% |
| prior day result | prior day lost >=1R | 45% | 38% | 28% | 37% [34%,40%] (838) | 24% | 20% |
| gap |open-prior close|/ATR20 | gap_abs_atr low | 51% | 39% | 28% | 34% [31%,37%] (939) | 25% | 18% |
| gap |open-prior close|/ATR20 | gap_abs_atr mid | 54% | 38% | 29% | 36% [33%,39%] (937) | 26% | 18% |
| gap |open-prior close|/ATR20 | gap_abs_atr high | 43% | 37% | 34% | 42% [39%,45%] (938) | 24% | 28% |
| overnight/pre-open range vs 20-session median | on_rng_rel low | 44% | 41% | 37% | 41% [38%,44%] (943) | 27% | 22% |
| overnight/pre-open range vs 20-session median | on_rng_rel mid | 46% | 40% | 26% | 37% [34%,40%] (942) | 24% | 21% |
| overnight/pre-open range vs 20-session median | on_rng_rel high | 44% | 35% | 23% | 34% [31%,37%] (943) | 24% | 20% |
| NQ-ES divergence |over window| | on_div_abs low | 51% | 39% | 31% | 39% [36%,42%] (953) | 26% | 20% |
| NQ-ES divergence |over window| | on_div_abs mid | 40% | 43% | 32% | 38% [35%,41%] (952) | 27% | 21% |
| NQ-ES divergence |over window| | on_div_abs high | 45% | 28% | 23% | 35% [32%,39%] (953) | 23% | 22% |
| VIX level | vix low | 46% | 41% | 34% | 40% [37%,44%] (954) | 26% | 21% |
| VIX level | vix mid | 46% | 39% | 29% | 38% [35%,41%] (956) | 26% | 22% |
| VIX level | vix high | 42% | 36% | 23% | 34% [31%,37%] (949) | 22% | 21% |
| VIX3M-VIX (term slope) | term_slope low | 43% | 40% | 24% | 36% [33%,39%] (963) | 25% | 22% |
| VIX3M-VIX (term slope) | term_slope mid | 45% | 38% | 32% | 38% [35%,41%] (959) | 24% | 21% |
| VIX3M-VIX (term slope) | term_slope high | 46% | 39% | 30% | 38% [35%,41%] (935) | 26% | 21% |
| treasury (ZN) move |ret| | on_zn_abs low | 43% | 40% | 35% | 40% [37%,43%] (949) | 26% | 22% |
| treasury (ZN) move |ret| | on_zn_abs mid | 46% | 39% | 27% | 37% [34%,41%] (949) | 26% | 21% |
| treasury (ZN) move |ret| | on_zn_abs high | 45% | 33% | 28% | 35% [32%,38%] (949) | 24% | 22% |
| NQ-ES: NQ outperformed / lagged | NQ>ES | 46% | 38% | 28% | 38% [35%,40%] (1500) | 25% | 21% |
| NQ-ES: NQ outperformed / lagged | NQ<ES | 43% | 40% | 29% | 37% [35%,40%] (1358) | 25% | 21% |

Bases F-A: ASIA 45%, LONDON 39%, NY 29%, POOLED 37%; F-B: ASIA 25%, LONDON 25%, NY 25%, POOLED 25%; F-C: ASIA 30%, LONDON 18%, NY 16%, POOLED 21%