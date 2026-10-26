# REPORT FA2 - correlation of the leads and the effective number of independent leads

Written 2026-10-17 by research worker FA. Analysis only: no lead definition, gate or frozen prediction was changed. Code: code/census/night_ins/ap_fa2_build.py, ap_fa2_run.py, ap_fa2_write.py; tables: outputs/autopilot/FA2_*.csv (correlation matrices per span, DSR table, cluster membership).

## 1. Data and method

* **Set A (21 leads).** Every lead in FORWARD.md, daily USD series from outputs/autopilot/forward/series (sleeves in native units, pair-modifiers H11B, PERS30, RW5 as modified-minus-live uplift), summed to the 167 complete ISO weeks 2023-W31..2026-W41 (clean 104 + H1 28 + H2 35). Correlation is scale-free, so the 20% sizing is irrelevant. Weekly Pearson correlation, zero-filled no-trade weeks, no shrinkage.
* **Set B (165 books).** All library books labelled LEAD / FOUND-PENDING (excluding LEAD-weak, LEAD-history, the T4A scan) with full-window coverage, plus the 21 leads (the leads also appear in the library under other names, which is why near-duplicates merge).
* **Set C (trial population).** All 38,377 full-coverage library books (every cell the program stored), used to estimate how many independent trials the search contained.
* **Effective number.** (i) Participation ratio PR = (sum lambda)^2 / sum lambda^2 of the correlation matrix; (ii) Li-Ji and Nyholt Meff; (iii) eigenvalues for 90%/95% of variance; (iv) average-linkage clusters at |rho| >= 0.3 and 0.5 (distance sqrt(0.5(1-rho))); (v) N/(1+(N-1) mean rho). Because T = 167 weeks is short relative to 21 leads, the **noise baseline** (PR of 21 independent series of the same length, 100 draws) is reported: PR of independent noise is 18.8, not 21, so an observed PR below the baseline is the signal. Per-span matrices are given but H1 (28 weeks) and H2 (35) are too short to count anything: their noise PR is 12-13.
* **DSR.** Bailey-Lopez de Prado deflated Sharpe on each lead's own weekly series (T = 167, skew and kurtosis from the series), expected-maximum benchmark SR0 = sqrt(V) x ((1-gamma) Phi^-1(1-1/N) + gamma Phi^-1(1-1/(N e))) with V = 1/T (the sampling variance of a zero-skill Sharpe estimate). The cross-sectional variance of the library's Sharpes (V = 0.0771 weekly, annualised SD 2.00) was also tried and is **degenerate** (it contains the dispersion of true edges, so SR0 reaches 5-8 annualised and every lead gets DSR 0); it is not used.

## 2. Pairwise weekly correlation of the 21 leads (all 167 weeks)

```
|  | WT10 | K4 | H11 | PERS | DIP | P1 | E1 | IMP3 | 12P | RX5 | RW5 | L93 | Q5E | Z3 | W6 | T1B | BTC | SW4 | SW20 | Q12 | Q20 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| WT10 | 1.00 | -0.07 | 0.07 | 0.04 | 0.04 | 0.07 | 0.08 | -0.04 | -0.12 | -0.03 | -0.06 | -0.14 | -0.08 | -0.00 | -0.02 | -0.04 | -0.02 | 0.15 | -0.02 | 0.20 | -0.14 |
| K4 | -0.07 | 1.00 | -0.10 | -0.06 | 0.34 | -0.06 | -0.02 | 0.05 | 0.74 | 0.90 | -0.08 | 0.08 | 0.01 | 0.20 | 0.14 | 0.15 | -0.07 | 0.09 | 0.00 | -0.02 | 0.18 |
| H11 | 0.07 | -0.10 | 1.00 | 0.14 | 0.04 | 0.07 | 0.14 | 0.03 | -0.12 | -0.11 | 0.07 | -0.08 | -0.01 | -0.17 | -0.09 | -0.14 | 0.01 | 0.02 | 0.08 | 0.06 | -0.19 |
| PERS | 0.04 | -0.06 | 0.14 | 1.00 | -0.05 | -0.05 | -0.04 | 0.14 | -0.03 | -0.04 | 0.15 | 0.04 | 0.08 | -0.02 | -0.08 | -0.09 | 0.05 | 0.17 | 0.06 | 0.15 | -0.05 |
| DIP | 0.04 | 0.34 | 0.04 | -0.05 | 1.00 | 0.14 | 0.26 | 0.10 | 0.24 | 0.32 | 0.09 | -0.00 | 0.09 | -0.09 | -0.08 | -0.06 | -0.13 | 0.07 | 0.06 | 0.01 | -0.01 |
| P1 | 0.07 | -0.06 | 0.07 | -0.05 | 0.14 | 1.00 | 0.82 | 0.41 | 0.03 | -0.01 | -0.07 | -0.02 | -0.07 | -0.09 | -0.07 | -0.07 | -0.01 | 0.05 | 0.07 | -0.00 | -0.06 |
| E1 | 0.08 | -0.02 | 0.14 | -0.04 | 0.26 | 0.82 | 1.00 | 0.50 | 0.05 | 0.02 | -0.02 | 0.01 | -0.14 | -0.08 | -0.05 | -0.07 | -0.08 | 0.06 | 0.04 | -0.04 | -0.08 |
| IMP3 | -0.04 | 0.05 | 0.03 | 0.14 | 0.10 | 0.41 | 0.50 | 1.00 | 0.13 | 0.12 | 0.08 | 0.01 | -0.13 | 0.02 | 0.03 | 0.08 | -0.10 | 0.03 | -0.04 | -0.09 | 0.10 |
| 12P | -0.12 | 0.74 | -0.12 | -0.03 | 0.24 | 0.03 | 0.05 | 0.13 | 1.00 | 0.77 | -0.05 | 0.13 | -0.05 | 0.33 | 0.29 | 0.31 | 0.00 | 0.13 | -0.17 | -0.04 | 0.25 |
| RX5 | -0.03 | 0.90 | -0.11 | -0.04 | 0.32 | -0.01 | 0.02 | 0.12 | 0.77 | 1.00 | -0.04 | 0.07 | 0.02 | 0.33 | 0.23 | 0.28 | -0.13 | 0.15 | -0.04 | -0.05 | 0.25 |
| RW5 | -0.06 | -0.08 | 0.07 | 0.15 | 0.09 | -0.07 | -0.02 | 0.08 | -0.05 | -0.04 | 1.00 | -0.10 | -0.01 | 0.06 | 0.03 | 0.02 | 0.03 | 0.08 | -0.01 | -0.03 | -0.00 |
| L93 | -0.14 | 0.08 | -0.08 | 0.04 | -0.00 | -0.02 | 0.01 | 0.01 | 0.13 | 0.07 | -0.10 | 1.00 | 0.01 | -0.05 | -0.06 | -0.01 | -0.08 | 0.06 | -0.03 | -0.08 | 0.21 |
| Q5E | -0.08 | 0.01 | -0.01 | 0.08 | 0.09 | -0.07 | -0.14 | -0.13 | -0.05 | 0.02 | -0.01 | 0.01 | 1.00 | 0.03 | -0.06 | -0.04 | 0.03 | 0.06 | 0.05 | -0.02 | -0.01 |
| Z3 | -0.00 | 0.20 | -0.17 | -0.02 | -0.09 | -0.09 | -0.08 | 0.02 | 0.33 | 0.33 | 0.06 | -0.05 | 0.03 | 1.00 | 0.80 | 0.76 | -0.05 | 0.12 | 0.01 | -0.03 | 0.33 |
| W6 | -0.02 | 0.14 | -0.09 | -0.08 | -0.08 | -0.07 | -0.05 | 0.03 | 0.29 | 0.23 | 0.03 | -0.06 | -0.06 | 0.80 | 1.00 | 0.92 | -0.02 | 0.24 | 0.02 | -0.11 | 0.23 |
| T1B | -0.04 | 0.15 | -0.14 | -0.09 | -0.06 | -0.07 | -0.07 | 0.08 | 0.31 | 0.28 | 0.02 | -0.01 | -0.04 | 0.76 | 0.92 | 1.00 | -0.04 | 0.28 | -0.07 | -0.15 | 0.36 |
| BTC | -0.02 | -0.07 | 0.01 | 0.05 | -0.13 | -0.01 | -0.08 | -0.10 | 0.00 | -0.13 | 0.03 | -0.08 | 0.03 | -0.05 | -0.02 | -0.04 | 1.00 | 0.08 | 0.18 | -0.09 | 0.02 |
| SW4 | 0.15 | 0.09 | 0.02 | 0.17 | 0.07 | 0.05 | 0.06 | 0.03 | 0.13 | 0.15 | 0.08 | 0.06 | 0.06 | 0.12 | 0.24 | 0.28 | 0.08 | 1.00 | -0.09 | 0.17 | 0.11 |
| SW20 | -0.02 | 0.00 | 0.08 | 0.06 | 0.06 | 0.07 | 0.04 | -0.04 | -0.17 | -0.04 | -0.01 | -0.03 | 0.05 | 0.01 | 0.02 | -0.07 | 0.18 | -0.09 | 1.00 | -0.12 | -0.07 |
| Q12 | 0.20 | -0.02 | 0.06 | 0.15 | 0.01 | -0.00 | -0.04 | -0.09 | -0.04 | -0.05 | -0.03 | -0.08 | -0.02 | -0.03 | -0.11 | -0.15 | -0.09 | 0.17 | -0.12 | 1.00 | 0.00 |
| Q20 | -0.14 | 0.18 | -0.19 | -0.05 | -0.01 | -0.06 | -0.08 | 0.10 | 0.25 | 0.25 | -0.00 | 0.21 | -0.01 | 0.33 | 0.23 | 0.36 | 0.02 | 0.11 | -0.07 | 0.00 | 1.00 |
```
(IMP3 = FVG_IMP3, E1 = FVG_E1, P1 = FVG_P1, K4 = K4V2, 12P = RW12P, DIP = ESDIP, BTC = BTCWT, W6/Z3 = gap fades, PERS = PERS30, H11 = H11B, Q5E = Q5ENS.) Mean pairwise rho +0.055, mean |rho| 0.115; **16 of 210 pairs have |rho| >= 0.3 and 28 have |rho| >= 0.2.**

Pairs with |rho| >= 0.2, with the per-span values (clean / H1 / H2):

| lead A | lead B | all 167 wk | clean | H1 | H2 |
|---|---|---|---|---|---|
| W6FADE | T1B | 0.92 | 0.87 | 0.74 | 0.97 |
| K4V2 | RX5 | 0.90 | 0.91 | 0.88 | 0.94 |
| FVG_P1 | FVG_E1 | 0.82 | 0.78 | 0.89 | 0.83 |
| Z3FADE | W6FADE | 0.80 | 0.89 | 0.11 | 0.80 |
| RW12P | RX5 | 0.77 | 0.79 | 0.66 | 0.80 |
| Z3FADE | T1B | 0.76 | 0.84 | -0.20 | 0.80 |
| K4V2 | RW12P | 0.74 | 0.78 | 0.62 | 0.72 |
| FVG_E1 | FVG_IMP3 | 0.50 | 0.34 | 0.65 | 0.56 |
| FVG_P1 | FVG_IMP3 | 0.41 | 0.33 | 0.42 | 0.50 |
| T1B | Q20 | 0.36 | 0.60 | -0.21 | 0.32 |
| K4V2 | ESDIP | 0.34 | 0.45 | 0.07 | 0.18 |
| RX5 | Z3FADE | 0.33 | 0.34 | 0.02 | 0.42 |
| Z3FADE | Q20 | 0.33 | 0.52 | -0.09 | 0.19 |
| RW12P | Z3FADE | 0.33 | 0.39 | -0.11 | 0.36 |
| ESDIP | RX5 | 0.32 | 0.39 | 0.27 | 0.24 |
| RW12P | T1B | 0.31 | 0.50 | -0.12 | 0.20 |
| RW12P | W6FADE | 0.29 | 0.43 | -0.15 | 0.24 |
| T1B | SW4 | 0.28 | 0.22 | -0.05 | 0.39 |
| RX5 | T1B | 0.28 | 0.43 | -0.35 | 0.18 |
| ESDIP | FVG_E1 | 0.26 | 0.15 | 0.55 | 0.15 |
| RW12P | Q20 | 0.25 | 0.40 | -0.03 | 0.02 |
| RX5 | Q20 | 0.25 | 0.33 | 0.10 | 0.09 |
| W6FADE | SW4 | 0.24 | 0.20 | -0.29 | 0.38 |
| ESDIP | RW12P | 0.24 | 0.29 | 0.21 | 0.10 |
| RX5 | W6FADE | 0.23 | 0.35 | -0.38 | 0.19 |
| W6FADE | Q20 | 0.23 | 0.43 | -0.45 | 0.20 |
| L93 | Q20 | 0.21 | 0.35 | 0.19 | 0.15 |
| WT10 | Q12 | 0.20 | 0.19 | 0.36 | 0.12 |

Reading. Three tight blocks: **K4 family** (K4V2-RX5 0.90, RW12P-RX5 0.77, K4V2-RW12P 0.74: one signal), **FVG** (P1-E1 0.82, E1-IMP3 0.50, P1-IMP3 0.41: one mechanism, IMP3 partly distinct), **weekend/overnight gap fades** (W6-T1b 0.92, Z3-W6 0.80, Z3-T1b 0.76: one signal). T1b/Z3/Q20 also load on the K4 family in the clean span (0.3-0.5) but not in H1 (negative), i.e. the clean-span links are regime-driven. Everything else is within +-0.25. Block correlations are stable across spans (K4 0.88-0.94, FVG 0.78-0.89, gap fades 0.74-0.97 except Z3 in H1 where it is 0.11 on 28 weeks).

Correlation with the live pair and inside the pair's worst-decile weeks (the gate-6 quantity):

| lead | own weekly Sharpe (167 wk, ann.) | corr with live pair (weekly) | corr with pair inside the pair's worst-decile weeks (17 wk) |
|---|---|---|---|
| WT10 | 2.03 | 0.00 | -0.20 |
| K4V2 | 1.43 | 0.04 | 0.26 |
| H11B | 0.99 | -0.18 | 0.15 |
| PERS30 | 0.18 | -0.68 | 0.15 |
| ESDIP | 2.06 | 0.05 | 0.10 |
| FVG_P1 | 2.80 | 0.16 | 0.25 |
| FVG_E1 | 4.05 | 0.20 | 0.16 |
| FVG_IMP3 | 4.48 | 0.13 | 0.11 |
| RW12P | 2.02 | 0.03 | -0.07 |
| RX5 | 1.79 | 0.04 | 0.13 |
| RW5 | 1.32 | -0.11 | -0.32 |
| L93 | 1.50 | -0.06 | 0.06 |
| Q5ENS | 0.49 | -0.16 | -0.38 |
| Z3FADE | 0.92 | 0.03 | -0.70 |
| W6FADE | 0.88 | 0.06 | -0.59 |
| T1B | 0.71 | 0.09 | 0.55 |
| BTCWT | 2.11 | -0.06 | -0.31 |
| SW4 | 1.65 | -0.10 | -0.18 |
| SW20 | 1.10 | -0.04 | 0.09 |
| Q12 | 0.77 | -0.22 | 0.15 |
| Q20 | 1.21 | 0.14 | -0.55 |

Only T1b (+0.55) exceeds the gate-6 limit of +0.30; K4V2 (+0.26) and FVG_P1 (+0.25) are close to it. Negative in the pair's worst weeks: Z3 -0.70, W6 -0.59, Q20 -0.55, Q5ENS -0.38, RW5 -0.32, BTCWT -0.31, WT10 -0.20, SW4 -0.18 (hedge-like, but with the weak weekly power of FA3). 17 worst-decile weeks make each of these a coarse estimate (SE about 0.25).

## 3. Effective number of independent leads

**Set A (21 leads)**

| span | weeks | p | PR | noise_PR | LiJi | Nyholt | k90 | k95 | clusters_03 | clusters_05 | mean_rho | mean_abs_rho | lam1 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| all | 167.00 | 21.00 | 12.01 | 18.75 | 17.00 | 20.25 | 14.00 | 16.00 | 14.00 | 16.00 | 0.06 | 0.12 | 3.75 |
| clean | 104.00 | 21.00 | 10.22 | 17.63 | 16.00 | 19.94 | 13.00 | 15.00 | 12.00 | 15.00 | 0.06 | 0.15 | 4.60 |
| H1 | 28.00 | 21.00 | 9.42 | 12.08 | 15.00 | 19.77 | 11.00 | 13.00 | 10.00 | 16.00 | 0.02 | 0.19 | 4.03 |
| H2 | 35.00 | 21.00 | 10.01 | 13.21 | 16.00 | 19.90 | 11.00 | 13.00 | 10.00 | 15.00 | 0.06 | 0.16 | 3.67 |

* Participation ratio **12.0** vs 18.8 for 21 independent series; first eigenvalue 3.75; 14 eigenvalues carry 90% of variance, 16 carry 95%. Li-Ji 17, Nyholt 20.3 (both nearly insensitive here because the eigenvalue spectrum is flat once the three blocks are removed).
* Average-linkage clusters: **14 at |rho| >= 0.3**, 16 at 0.5. Cluster membership:

| cluster (avg-linkage, rho>=0.3) | members |
|---|---|
| 1 | FVG_E1, FVG_IMP3, FVG_P1 |
| 2 | K4V2, RX5, RW12P |
| 3 | ESDIP |
| 4 | W6FADE, T1B, Z3FADE, Q20 |
| 5 | SW4 |
| 6 | L93 |
| 7 | BTCWT |
| 8 | SW20 |
| 9 | Q5ENS |
| 10 | WT10 |
| 11 | Q12 |
| 12 | PERS30 |
| 13 | RW5 |
| 14 | H11B |

* Structural count (what the mechanisms say): K4V2/RX5/RW12P = 1, FVG P1/E1/IMP3 = 1, W6/T1b/Z3 = 1, so 21 - 2 - 2 - 2 = 15; the cluster count is one lower (14) because Q20, the RTY prior-close fade, joins the gap-fade cluster (weekly rho 0.33-0.36 with Z3 and T1b).
* **Best estimate: the 21 leads are 12 (PR) to 14 (clusters) independent bets; 15 by mechanism.** Taking K4-family, FVG and gap-fade as one each, the independent FOUND-PENDING signals are still ESDIP, K4, FVG, SW4 = 4 (they are mutually uncorrelated: all pairwise |rho| <= 0.34).

**Set B (165 LEAD/FOUND-PENDING library books incl. the 21 leads)**

| span | weeks | p | PR | noise_PR | LiJi | Nyholt | k90 | k95 | clusters_03 | clusters_05 | mean_rho | mean_abs_rho | lam1 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| all | 167.00 | 165.00 | 29.99 | 82.97 | 84.00 | 160.50 | 52.00 | 68.00 | 53.00 | 72.00 | 0.03 | 0.10 | 17.23 |
| clean | 104.00 | 165.00 | 25.82 | 63.68 | 76.00 | 159.61 | 43.00 | 55.00 | 52.00 | 74.00 | 0.03 | 0.12 | 18.32 |
| H1 | 28.00 | 165.00 | 14.82 | 23.33 | 41.00 | 154.87 | 19.00 | 22.00 | 28.00 | 58.00 | 0.05 | 0.19 | 24.14 |
| H2 | 35.00 | 165.00 | 16.81 | 28.29 | 46.00 | 156.19 | 21.00 | 26.00 | 30.00 | 57.00 | 0.03 | 0.17 | 22.25 |

PR 30 (noise baseline 83), clusters **53 at rho >= 0.3 / 72 at 0.5**. The 165 books are dominated by variants: W4 Monday-drift 31 books, Q10 / Q5 / Q9 / R9 momentum books 44, S8 opex 12, V5 5-min trend 14. Largest clusters (books, families):

| cl | n | fam |
|---|---|---|
| 46 | 27 | FWD, Q5, Q5ALL, R9ALL |
| 28 | 19 | FV16_VC, FV17, FWD, ICT, ICT_FVG |
| 22 | 12 | V5P1 |
| 18 | 8 | FWD, N3, RY9, W4ALL |
| 12 | 5 | S8ALL, W4ALL |
| 31 | 5 | RW5, RW8, RX10, WT |
| 39 | 4 | Q10, Q10ALL |
| 51 | 4 | T4E |
| 40 | 4 | Q9, Q9ALL, W4ALL |
| 20 | 4 | Q9ALL, W4ALL |
| 13 | 4 | FWD |
| 11 | 4 | S8ALL |

**Set C (all 38,377 stored cells = the trial population).** PR 96 (iid noise PR at this size 165; the first eigenvalue 1,884 is 4.9% of total variance against 262 for iid noise, a common NQ/trend factor, and the next four are 1,219 / 843 / 694 / 640, so the variance is spread over about 100 effective dimensions; PR counts variance concentration, not trials). Leader clustering gives **2,464 clusters at |rho| >= 0.3, 7,912 at 0.5, 17,663 at 0.7** (signed 2,814 / 8,312 / 18,240). At T = 167 the null correlation SD is 0.077, so rho >= 0.3 has a spurious-merge probability of about 1e-4 per comparison; the 0.3-threshold count is therefore a slight under-count and 0.5 is the safer reading.

## 4. Effective independent N for the family-level DSR

Two different questions need two different N.

| question | N to use | basis |
|---|---|---|
| which of the 21 leads is real, given they were the survivors of one another | **12-14** (PR 12.0; clusters 14) | Set A; 15 by mechanism |
| could the program's search have produced a lead with this Sharpe by chance | **2,464 to 7,912** (trial clusters rho >= 0.3 / 0.5); 38,377 if every stored cell were independent (they are not) | Set C; also report with PR=96 as an unrealistically low bound |

Expected best annualised Sharpe from N zero-skill independent weekly trials of 167 weeks (V = 1/T):

| N | expected best annualised weekly Sharpe from N zero-skill trials (V=1/T) |
|---|---|
| 12.00 | 0.93 |
| 14.00 | 0.97 |
| 2,464.00 | 1.95 |
| 7,912.00 | 2.12 |
| 38,377.00 | 2.33 |

DSR (probability the true Sharpe exceeds the best-of-N expectation under zero skill), V = 1/T. A lead's own Sharpe is on its 167-week series (for the pair-modifiers H11B, PERS30, RW5 it is the Sharpe of the uplift stream):

| lead | N=12 (PR of leads) | N=14 (lead clusters) | N=2,464 (trial clusters rho>=0.3) | N=7,912 (trial clusters rho>=0.5) | N=38,377 (all stored cells) |
|---|---|---|---|---|---|
| WT10 | 0.97 | 0.97 | 0.55 | 0.43 | 0.30 |
| K4V2 | 0.90 | 0.88 | 0.09 | 0.04 | 0.01 |
| H11B | 0.55 | 0.52 | 0.02 | 0.01 | 0.00 |
| PERS30 | 0.09 | 0.08 | 0.00 | 0.00 | 0.00 |
| ESDIP | 1.00 | 1.00 | 0.61 | 0.43 | 0.24 |
| FVG_P1 | 1.00 | 1.00 | 0.94 | 0.89 | 0.80 |
| FVG_E1 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 |
| FVG_IMP3 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 |
| RW12P | 1.00 | 1.00 | 0.56 | 0.40 | 0.22 |
| RX5 | 0.99 | 0.99 | 0.32 | 0.18 | 0.07 |
| RW5 | 0.75 | 0.73 | 0.14 | 0.09 | 0.04 |
| L93 | 0.87 | 0.85 | 0.19 | 0.11 | 0.05 |
| Q5ENS | 0.22 | 0.19 | 0.00 | 0.00 | 0.00 |
| Z3FADE | 0.49 | 0.45 | 0.01 | 0.00 | 0.00 |
| W6FADE | 0.45 | 0.41 | 0.00 | 0.00 | 0.00 |
| T1B | 0.28 | 0.24 | 0.00 | 0.00 | 0.00 |
| BTCWT | 0.98 | 0.98 | 0.61 | 0.49 | 0.35 |
| SW4 | 0.93 | 0.92 | 0.27 | 0.17 | 0.08 |
| SW20 | 0.62 | 0.59 | 0.06 | 0.03 | 0.01 |
| Q12 | 0.39 | 0.36 | 0.02 | 0.01 | 0.00 |
| Q20 | 0.71 | 0.69 | 0.07 | 0.03 | 0.01 |

Family-level view (best lead of each family, family counted once):

| family | best_lead | own Sharpe | N=14 (lead clusters) | N=2,464 (trial clusters rho>=0.3) | N=7,912 (trial clusters rho>=0.5) |
|---|---|---|---|---|---|
| FVG (3 leads) | FVG_IMP3 | 4.48 | 1.00 | 1.00 | 1.00 |
| K4 (3 sleeves + RW5 pair-side) | RW12P | 2.02 | 1.00 | 0.56 | 0.40 |
| ES dip-buy | ESDIP | 2.06 | 1.00 | 0.61 | 0.43 |
| BTC trend | BTCWT | 2.11 | 0.98 | 0.61 | 0.49 |
| NQ trend WT-10 | WT10 | 2.03 | 0.97 | 0.55 | 0.43 |

Reading. **Only the FVG family survives deflation for the full search size** (best-of-N benchmark 1.95-2.33 annualised at N = 2,464-38,377 vs own weekly Sharpe 4.0 (E1), 4.5 (IMP3), 2.8 (P1)): FVG_E1 and FVG_IMP3 have DSR 1.00 even at N = 38,377, FVG_P1 0.94 / 0.89 / 0.80 at N = 2,464 / 7,912 / 38,377. Every other lead is at or below 0.61 at N = 2,464 (ESDIP 0.61, BTCWT 0.61, RW12P 0.56, WT10 0.55, RX5 0.32, SW4 0.27, L93 0.19, K4V2 0.09), and H11B, PERS30, the gap fades, Q5ENS and the RTY cells are near 0. At the lead-level N = 12-14 more clear: ESDIP 0.998, BTCWT 0.98, RW12P 0.996, WT10 0.97, RX5 0.99, SW4 0.93, K4V2 0.90, L93 0.87-0.85; those say only that they are the best of 14 independent survivors, not that the search did not manufacture them. This is consistent with RY7 (K4 DSR 0.64 at N = 145 trials, 0.99 at N_eff = 4) and with the FA1 finding that the nominal gates admit a few false leads.

Two limits. (1) The window (167 weeks) contains the clean selection span, so own Sharpes are in-sample for selection; WT10/K4 are not deflated for selection here (FORWARD.md deflates them by 86%/94% of the clean uplift, which would cut their Sharpe materially). (2) Sharpe skew and kurtosis are from 167 weeks; daily-only leads (ESDIP, 76% zero weeks) have non-normal weekly series and the DSR z-score is only a rough guide for them.

## 5. What this means for sizing and for the forward test

* Combining all 21 at equal risk is not 21 independent bets: 12-14. Position-limit and drawdown planning should use that number; the K4 family, the FVG family and the gap-fade family each act as one sleeve.
* The four FOUND-PENDING signals are mutually uncorrelated, so their live outcomes are four independent tests (FA3 gives their timelines), but FVG is the only one with both a family-level null (FA1) and a DSR that survives the search size.
* Nothing here changes a gate or a status. FOUND remains 0.

DONE FA2
