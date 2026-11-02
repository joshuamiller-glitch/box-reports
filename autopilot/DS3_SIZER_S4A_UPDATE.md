
## SIZER_S1 update (2026-11-02 20:26Z): ts-base re-screen, exact equal-risk, rank-hysteresis family with a family-wise null, tier carrying, exposure

Prereg: ZL_S4A_PREREG_SIZER_HYST_FAMILY.md (sha256 6da9c8038f47a138ebf47a8e6276e57e24cbe88086ce5c61eaa854d4e492acc3, DECISIONS.md). Base = the current T-SIZER harness (ts mode: V13T_LIVE costs, sequential rounding, lock R scaled only when mult > 1), reference = live binary ER ladder in the same mode; single path (lock-reset phases are identical on this base). IMPORTANT: the section-1 screen of 998 cells above was run on the sequential-without-ts base; the top 100 of it were re-run on the ts base here.

**(0) Base sensitivity.** The ts re-screen of the top 100 keeps 77 cells at mean >= live. The previous lead (ER(20) rank hysteresis 3 tiers) changes from PA9 L6M +.34 / PRE +.19 (sequential base) to single-path L6M +0.31; see (2): on the ts base its PRE cut is about zero. The lead is BASE-SENSITIVE.

**(2) Family of 72 rank-hysteresis settings** (ER window 14/20/30 x expanding/rolling-250 rank x cuts (1/4,3/4) (1/3,2/3) (.4,.6) x margin 0/.03/.05/.10). Eligible cells (mean >= live, no window worse than the PA9 flip-5 band): 5 of 72. Single-path cuts of the best cells:

| cell | cut L6M | HOLD | MID | PRE | X' | drop L6M | drop PRE | mean $/wk | S=(L6M+PRE)/2 | eligible |
|--|--|--|--|--|--|--|--|--|--|--|
| ER20 exp cuts 1/4-3/4 h0.05 | +0.39 | -0.00 | -0.75 | +0.32 | -0.13 | -0.12 | +0.40 | -254 | +0.351 |  |
| ER20 exp cuts 1/3-2/3 h0.1 | +0.47 | +0.11 | -0.37 | +0.21 | +0.04 | +0.02 | +0.21 | +855 | +0.336 |  |
| ER30 exp cuts 1/4-3/4 h0.1 | +0.46 | -0.07 | -1.24 | +0.13 | +0.09 | +0.01 | +0.13 | -2898 | +0.298 |  |
| ER20 exp cuts 1/4-3/4 h0.03 | +0.39 | +0.00 | -0.70 | +0.18 | -0.05 | -0.12 | +0.33 | -1619 | +0.284 |  |
| ER20 roll cuts .4-.6 h0.1 | +0.46 | +0.10 | -0.73 | +0.10 | +0.14 | +0.01 | +0.20 | +1559 | +0.281 |  |
| ER14 exp cuts 1/4-3/4 h0.1 | +0.38 | -0.25 | -1.75 | +0.18 | -0.31 | +0.14 | +0.18 | -3579 | +0.281 |  |
| ER30 exp cuts .4-.6 h0.1 | +0.42 | -0.43 | -1.65 | +0.11 | +0.09 | +0.27 | +0.11 | -283 | +0.269 |  |
| ER30 roll cuts .4-.6 h0.05 | +0.30 | -0.29 | -1.60 | +0.24 | +0.07 | +0.00 | +0.24 | -2500 | +0.267 |  |
| ER20 exp cuts 1/4-3/4 h0.1 | +0.34 | -0.03 | -1.02 | +0.18 | -0.36 | -0.21 | +0.18 | -1344 | +0.260 |  |
| ER20 roll cuts 1/4-3/4 h0.03 | +0.31 | +0.01 | -0.74 | +0.21 | -0.01 | -0.17 | +0.32 | -1882 | +0.259 |  |

Best-of-grid statistic B = max S over eligible cells = +0.142 (B2 = max min(L6M,PRE) = +0.031; unconditioned max S = +0.351). FAMILY-WISE NULL (day-shuffled multiplier worlds, one day-source map per world applied to all 72 cells): 57 complete worlds so far (target 100). Null B: median -9.000, 95th pct -9.000; share of worlds with an eligible cell 0.00. P-value of B = 0.017; of B2 = 0.017; of the unconditioned max S = 0.793; of the best S among no-harm cells WITHOUT the mean gate (real +0.142) = 0.017; null of unconditioned max S: median +0.407, 95th pct +0.506 (n = 57 worlds). Reading: no day-shuffled world has a cell that keeps the mean at or above the live ladder (the shuffle removes the ER signal's contribution to the mean), so the eligibility gate alone separates the real lead from the null; the drawdown cut S by itself is NOT unusual under shuffling (a random multiplier vector with this distribution reaches an S as high as the real best in most worlds).

**(3) Which tier carries the gain (lead ER20 expanding (1/3,2/3) h .05):**

| variant | cut L6M | HOLD | MID | PRE | X' | drop L6M | drop PRE | mean $/wk vs live |
|--|--|--|--|--|--|--|--|--|
| lead x0.5 / x1.0 / x1.5 | +0.31 | +0.19 | -0.11 | -0.02 | -0.03 | -0.02 | +0.31 | +138 |
| x0.5 replaced by x1.0 (1/1/1.5) | +0.22 | -0.14 | -1.38 | +0.10 | -0.32 | -0.05 | +0.10 | +875 |
| x1.5 replaced by x1.0 (0.5/1/1) | +0.53 | +0.22 | -0.25 | +0.47 | +0.06 | +0.20 | +0.47 | -4982 |

Reading: the drawdown gain sits in the x0.5 (down-size) tier and is paid for in mean; the x1.5 tier is what carries the mean.

**(1) Exact equal-risk mean (11-point lscale scan, linear fits; lot scale c at which the cell's fitted maxDD equals the live ladder's) for the lead and the top-30 ts re-screen cells; mean gain = mean at equal risk - live mean (fitted), $/wk:**

| cell | c L6M | gain L6M | c PRE | gain PRE | c X' | gain X' |
|--|--|--|--|--|--|--|
| ('g13', 'ers_30m_20', 1, 'LIN', 'B') | 2.51 | +69190 | 0.96 | +776 | 0.76 | +1049 |
| ('g13', 'ers_30m_20', 1, 'SIG', 'B') | 2.21 | +56233 | 0.94 | +755 | 0.74 | +994 |
| ('g13', 'ers_30m_20', 1, 'L5', 'B') | 1.97 | +40835 | 1.01 | +3671 | 0.66 | +505 |
| ('g13', 'ers_5m_20', 1, 'L5', 'A') | 1.63 | +27030 | 1.17 | +3666 | 0.94 | +503 |
| ('g12', 'er_15m_10', 'L3', 'D') | 1.67 | +23251 | 1.11 | +4183 | 0.92 | +1241 |
| ('g13', 'ers_5m_20', 1, 'LIN', 'B') | 1.38 | +27016 | 0.87 | +65 | 0.89 | +2724 |
| ('g13', 'ers_15m_20', 1, 'L3', 'A') | 1.39 | +23825 | 1.09 | +2621 | 1.00 | +2063 |
| ('g12', 'er_30m_10', 'L5', 'D') | 1.51 | +17768 | 1.19 | +5918 | 0.70 | -980 |
| ('g12', 'er_10m_14', 'L3', 'D') | 1.33 | +14402 | 1.24 | +5919 | 0.81 | -225 |
| ('g12', 'er_1m_100', 'LIN', 'D') | 1.46 | +16509 | 1.13 | +3727 | 0.48 | -2561 |
| ('g12', 'er_1m_100', 'SIG', 'D') | 1.50 | +16100 | 1.13 | +4029 | 0.53 | -2098 |
| ('g13', 'ers_10m_20', 1, 'LIN', 'B') | 1.11 | +12510 | 1.18 | +6992 | 0.83 | -815 |
| ('g12', 'er_10m_14', 'LIN', 'B') | 1.22 | +13434 | 1.14 | +5274 | 0.81 | +317 |
| ('g12', 'er_10m_14', 'SIG', 'B') | 1.21 | +11719 | 1.16 | +5899 | 0.86 | +1012 |
| ('g12', 'er_5m_20', 'LIN', 'D') | 1.36 | +13002 | 1.18 | +4577 | 0.51 | -1993 |
| ('g12', 'er_30m_10', 'L3', 'D') | 1.33 | +11407 | 1.13 | +6024 | 0.61 | -1425 |
| ('g12', 'er_15m_10', 'L5', 'D') | 1.45 | +14220 | 1.06 | +2271 | 0.89 | +1083 |
| ('g12', 'er_10m_10', 'LIN', 'B') | 1.36 | +16130 | 0.91 | -441 | 0.66 | -1385 |
| ('g12', 'er_30m_10', 'LIN', 'B') | 1.15 | +11060 | 1.00 | +4218 | 0.76 | -251 |
| ('g13', 'ers_5m_20', 1, 'L3', 'A') | 1.39 | +14140 | 1.02 | +1038 | 1.10 | +4255 |
| ('g12', 'er_15m_10', 'LIN', 'D') | 1.36 | +12639 | 1.06 | +2357 | 0.62 | -1198 |
| ('g13', 'ers_5m_20', 1, 'L5', 'D') | 1.25 | +8731 | 1.27 | +6065 | 0.81 | +171 |
| ('g13', 'ers_10m_20', 1, 'SIG', 'B') | 1.02 | +8963 | 1.14 | +5344 | 0.85 | -530 |
| ('g13', 'ers_10m_20', 1, 'L3', 'D') | 1.29 | +12701 | 1.01 | +1122 | 0.88 | +978 |
| ('g12', 'er_1m_100', 'L3', 'D') | 1.37 | +11623 | 1.07 | +1588 | 0.77 | +63 |
| ('g14', 'er_5m_20', 'hyst', 'L3') | 1.41 | +11851 | 0.99 | +565 | 1.02 | +1178 |
| LEAD ER20 hysteresis | 1.41 | +11851 | 0.99 | +565 | 1.02 | +1191 |
| ('g12', 'er_1m_100', 'L3', 'A') | 1.25 | +8296 | 1.13 | +2215 | 1.16 | +2532 |
| ('g12', 'er_5m_20', 'L5', 'D') | 1.12 | +5111 | 1.23 | +4659 | 0.78 | -442 |
| ('g12', 'er_10m_20', 'L3', 'D') | 1.20 | +7549 | 1.01 | +894 | 0.86 | +929 |
| ('g14', 'er_5m_14', 'min3', 'L3') | 1.15 | +5510 | 1.05 | -268 | 1.00 | +1668 |

**Exposure (exposure_table):** lead mean lots 3.14 / max 11; live ladder 3.01 / 11. Worst net signed NQ lots across books: lead 28 (20240926), live 28 (20240220); worst stack risk lead $33,600, live $33,600. The lead does not change the worst-case exposure.
