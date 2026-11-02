# DS3_SIZER_Q3 - best-of-52 null, ADDK placebo, walk-forward on the cell choice, monthly stability (ZL-2, 2026-11-02T21:49Z; analysis only, the user decides)
Prereg SIZER_Q3_PREREG.md sha256 2b74e897d39e57249cac201430479a99d35ab99a46cbe0f0a468ea05bea88657 (DECISIONS.md, before any Q3 statistic). Frame: T-SIZER ts base (V13T_LIVE costs, sequential rounding, lock R scaled only when mult > 1, A06 not modelled). Reference L = live ladder.

**HEADLINE.** (1) The Q2 result is what chance produces: in 100 shuffled-day worlds (ER unrelated to outcomes, same 52 cells rebuilt, scored against the world's own ladder) the best cell's min(L6M-dropped cut, PRE cut) among mean-tolerant cells reaches the real 43.4% (W_5m_30_A) in 7% of worlds, the best x1.5-keeping cell reaches the real 19.2% (T_0.25_0.60) in 68%, and 18 or more cells are flagged in 66% of worlds (median 25 flagged in the null vs 18 real). The x1.5-keeping cells (the question asked) are not distinguishable from what chance produces; only the size-down-only family (W_*_A, no x1.5 at all) is somewhat unusual (S1 p = 0.07) and that is a plain less-size effect (Q1 placebo cut ranks 0.00-0.06). 

## 1. Best-of-52 null (100 shuffled-day worlds)
| statistic | real | null median | null p90 | null max | share of worlds >= real |
|--|--|--|--|--|--|
| S1 best min(cut L6M-dropped, cut PRE), all mean-tolerant cells | 43.4 | 26.4 | 41.8 | 53.3 | 0.07 |
| S2 same, cells keeping a x1.5 | 19.2 | 23.7 | 34.1 | 41.2 | 0.68 |
| S3 number of flagged cells | 18.0 | 25.0 | 42.1 | 49.0 | 0.66 |
Best x1.5-keeping cell in the null worlds (most frequent): CAPB_2 15, T_0.30_0.60 9, MAXL_6 9, W_5m_30_live 8, T_0.25_0.60 8; its mean cost in L6M-dropped / PRE (median $k/wk): -5.6 / -1.7 (real T_0.25_0.60: -13.4 / -4.2).

## 2. Placebo for the ADDK cells (100 draws: add multipliers permuted within book x session, same distribution; rank = share of draws below the real cell)
| cell | real: L6M cut / d mean | PRE cut / d mean | rank cut L6M | rank mean L6M | rank cut PRE | rank mean PRE | draws median (L6M cut, d mean, PRE cut, d mean) |
|--|--|--|--|--|--|--|--|
| ADDK_ALL | +38.6% / -3.2k | +11.0% / -2.2k | 1.00 | 0.09 | 0.97 | 0.02 | 5.4 / -1.5 / 7.3 / -1.1 |
| ADDK_PE | +26.2% / -2.6k | +3.1% / -3.0k | 1.00 | 0.12 | 0.46 | 0.00 | -4.7 / -1.0 / 3.4 / -1.1 |

## 3. Purged walk-forward on the CHOICE (top 6 Q2 cells by the rank key + L; trailing 12 months, last 2 label days purged; months 2024-01..2026-10; assembled OOS multiplier run exactly on the engine)
Candidates: W_5m_30_A, W_3m_20_A, W_3m_14_A, T_0.25_0.60, W_5m_30_live, T_0.30_0.60. Months each cell was chosen: W_5m_30_A 17, T_0.30_0.60 11, W_3m_20_A 4, L 2. Static choice made on 2023-04..2023-12 only: W_3m_20_A.
| window (W29-W39 dropped where 2026) | WF cut vs L | WF mean vs L (MDE) | static cut | static mean vs L (MDE) |
|--|--|--|--|--|
| PRE | +32.8% (maxDD 107.9k vs L 160.7k) | -5.9k (6.9k) | +32.8% | -6.9k (8.5k) |
| L6M | +17.4% (maxDD 76.9k vs L 93.1k) | -10.7k (14.5k) | +35.1% | -28.4k (30.1k) |
| HOLD | -7.6% (maxDD 140.3k vs L 130.4k) | -8.9k (8.8k) | -11.6% | -14.9k (13.8k) |
| F9 | +15.5% (maxDD 78.6k vs L 93.1k) | -9.1k (10.0k) | +15.4% | -20.8k (19.1k) |
| X' (mostly in-sample for the first months) | +0.0% | -1.6k (2.9k) | | |
| MID (mostly in-sample for the first months) | -72.8% | -6.3k (12.1k) | | |
Reading: walk-forward selection mostly picks the size-down cells (A-type) and gives the same trade as in-sample: a shallower PRE/L6M maxDD for a lower mean; it does not find a cell that keeps the mean.

## 4a. Monthly stability: months where the cell beats the ladder on mean and on the month's maxDD (delta mean $k, delta maxDD $k, positive = better)
| cell | window | months | beats on mean | beats on maxDD | beats on both | sum d mean $k | best month share of sum |
|--|--|--|--|--|--|--|--|
| T_0.25_0.60 | PRE | 17 | 6 | 15 | 6 | -317.2 | 19% |
| T_0.25_0.60 | X' | 10 | 4 | 10 | 4 | +1.9 | 29% |
| T_0.25_0.60 | L6M | 6 | 2 | 5 | 2 | -154.6 | 45% |
| T_0.25_0.60 | HOLD | 12 | 3 | 10 | 3 | -250.0 | 28% |
| T_0.30_0.60 | PRE | 17 | 6 | 16 | 6 | -309.3 | 22% |
| T_0.30_0.60 | X' | 10 | 4 | 10 | 4 | -39.7 | 24% |
| T_0.30_0.60 | L6M | 6 | 2 | 6 | 2 | -180.3 | 40% |
| T_0.30_0.60 | HOLD | 12 | 3 | 12 | 3 | -294.1 | 29% |
| K_PE | PRE | 17 | 6 | 16 | 6 | -121.0 | 18% |
| K_PE | X' | 10 | 3 | 10 | 3 | -48.7 | 32% |
| K_PE | L6M | 6 | 2 | 6 | 2 | -105.2 | 60% |
| K_PE | HOLD | 12 | 3 | 11 | 3 | -230.1 | 31% |
| PE_S_asia | PRE | 17 | 3 | 15 | 3 | -174.8 | 19% |
| PE_S_asia | X' | 10 | 6 | 10 | 6 | -2.3 | 27% |
| PE_S_asia | L6M | 6 | 3 | 5 | 3 | -32.4 | 25% |
| PE_S_asia | HOLD | 12 | 7 | 10 | 6 | -25.0 | 18% |

## 4b. Exact lot scan (engine runs at lscale 0.80..1.60 step 0.05; W29-W39 dropped in L6M/HOLD): cell's mean at the ladder's maxDD (average of the engine points whose maxDD is within +-7.5% of the ladder's maxDD at lscale 1.00; n points shown)
| cell | L6M-dropped: ladder mean / cell mean at equal maxDD (n) | PRE: ladder mean / cell mean (n) | HOLD-dropped (n) |
|--|--|--|--|
| T_0.25_0.60 | 64.6k / 55.1k (2) | 16.4k / 20.9k (4) | 39.7k / 35.9k (2) |
| T_0.30_0.60 | 64.6k / 52.3k (2) | 16.4k / 18.1k (4) | 39.7k / no point in band (0) |
| K_PE | 64.6k / 70.1k (3) | 16.4k / 18.1k (3) | 39.7k / 34.0k (3) |
| PE_S_asia | 64.6k / 58.1k (6) | 16.4k / no point in band (0) | 39.7k / 53.3k (4) |

## 5. FLAG check (strict: same-or-better mean than the ladder in BOTH L6M with W29-W39 dropped AND PRE, and shallower maxDD in both)
Cells with mean >= ladder in L6M-dropped and PRE: none. Cells with mean >= ladder in L6M-dropped alone: S_AL, PE_S_AL (PRE mean cost -3.3k / -2.5k). => NO strict flag. The Q2 flags remain size effects (section 1).


## 6. Plain sentences
(1) Best-of-52: the x1.5-keeping Q2 flags (19.2% min-cut, 18 flagged cells) are typical of shuffled-day worlds (68% / 66% of worlds do at least as well; 25 flagged cells in the median world), so they are size effects, not ER skill; the size-down-only family reaches its 43.4% in 7% of worlds. (2) ADDK: holding the add at x1 size on high-ER rows cuts L6M maxDD more than any random permutation of the same add multipliers (rank 1.00 and PRE 0.97 for ADDK_ALL) but it costs more mean than random permutations (mean rank 0.09 L6M, 0.02 PRE): it removes add size from the trades that earn the most, so its drawdown benefit is real but expensive; ADDK_PE has L6M cut rank 1.00 and PRE 0.46, mean rank 0.12 / 0.00. (3) Walk-forward on the choice picks mostly the size-down cells and in the fully out-of-sample PRE window gives -32.8% maxDD for -5.9k/wk (MDE 6.9k), L6M-dropped -17.4% for -10.7k/wk, HOLD -7.6% (worse) for -8.9k/wk: the same trade as in-sample, no cell that keeps the mean. (4) K_PE is the best of the x1.5-keeping cells at equal risk (exact scan: L6M-dropped 70.1k vs ladder 64.6k, PRE 18.1k vs 16.4k, but HOLD-dropped 34.0k vs 39.7k, n 3 points per window) yet it beats the ladder on mean in only 6 of 17 PRE months and 2 of 6 L6M months and one month gives 60% of its L6M gain; T_0.25_0.60 (3-tier b=.60) beats the ladder on maxDD in 15 of 17 PRE months (size) and on mean in 6 (sum -317k); PE_S_asia has no exact point in the PRE band. No cell passes the strict FLAG test; nothing is a PASS and the user decides.
