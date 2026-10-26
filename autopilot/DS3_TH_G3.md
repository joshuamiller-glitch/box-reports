# DS3_TH_G3 - T-BRACKET-PM section G3: new Trade Health mechanisms (D3TH3, 2026-10-26, tier 1: ST, HM, KB, SM, EM)

**Verdict: G3: 0 PASS, 0 CANDIDATE, 138 DEAD of 138 rows (30 configs x 5 entries with OPP combinations that do not exist dropped, + 5 live-control rows). No row clears the paired CI. Two LEADs (not CANDIDATE, not registered): HM exits on a flip of a faster book (OPP_EM +0.41 pts/trade, OPP_SM +0.28, both holdout-positive, CI includes 0, MDE 0.6; see section 5). The live TH-loss rule (named control) is negative on every entry. Tape cuts, vol-collapse and session-end tightening do nothing useful; the re-entry rule has no gain.**

Research only; no live recommendation. Preregs `l2vast/ds3/prereg/THG3_A.md` (14 configs, sha256 `d76b52c9119f73c47aefbd8103c6e508221a73eed3406ec826794bbc7a4c8816`) and `THG3_B.md` (16 configs, sha256 `c9e71ffa4d356543cd6fa81358d43fd35a5b10f40bcd9b7ec6a555e6d9d0cd6d`), frozen in `autopilot/DECISIONS.md` before any scoring; ledger +70 and +85 (cumulative corrected trials after: 41,288; the ledger lines are in `l2vast/struct48/ledger/trials.jsonl`, tracks DS3_THG3_A / DS3_THG3_B). Rows `l2vast/ds3/rows/DS3_TH_G3.json` (cell ids `G3_<cell>__<entry>`, with `entry`, `paired`, `equal_risk` blocks); code `l2vast/ds3/code/g3/` (g3k.py kernel, g3score.py, g3seq.py, g3cells.py); pre-holdout text `l2vast/ds3/out/g3/PREHOLD.md` (logged via log_holdout_look track DS3_THG3, ONE look for all rows); PRE table `out/g3/PRE_TABLE.txt`.

## 1. Design (what was run)
* Entries and base: ST10/HM10 (live rows, 8,309 / 6,311 trades), KB = TE7_kelt3m_n14_m1.0 (8,593), SM = TE6_st10m_n7_m3.0 (2,397), EM = TE7_emax5m_f30_s50 (2,335); base bracket 60/60, 1R, flat 16:55, mapped basis. The kernel re-simulates every base trade on the 1-s path and reproduces exit class, exit bar and points of all 28,000 base trades 100%, so a rule changes a trade only when it fires. Each cell is paired on identical entries against its own base; session-block bootstrap (1,000 draws; blocks = label day x session).
* Pricing: paired diff on a changed trade = (pts_new - cost_new) - (pts_base - cost_base) with live exit costs stop-join 1.01 pt, resting target 0, market 0.995 pt. (A first draft charged the cut leg the year x exit-type mapped P9 correction, which carries a +4.5 pt stop-join benefit in 2025-26; that was dropped before any prereg cell was scored and is disclosed in PREHOLD.md.) The cut exit fills at the close of the next traded second.
* Cells (prereg): IMB aggressor imbalance AGAINST >= {60,70}% over {30,60} s x gate {after 60 s hold, only after 10 pts adverse} (8); ABS absorption (flow WITH the position >= 60% of >= 8 contracts/s, no price progress) x {30,60} s x gate (4); DIV delta divergence (>= 4 pts progress while >= 55% of volume against, in profit >= 10) x {30,60} s (2); VOLCOL vol-collapse (60-s range < f x mean 1-min range of the prior 30 bars, f {0.25,0.4}, after {10,20} min) (4); OPP faster-book opposite-signal exit (KB, SM, EM, ANY; faster than ST/HM = KB/SM/EM, than SM = KB/EM, than EM = KB) (4); SESSEND stop tightened from 60 to {30,45} in the last 30 min of Asia (03:00) / London (09:30) / NY (16:55) (6); REENTRY cooldown {10,30} min after a TH cut (2, sequence level). Live control G3_TH_LIVE_ST = the 15 pts / 3-of-3 / 30 s TH-loss rule applied to each entry.
* Staging: stage 1 PRE (2024-02..2025-06) only; then the single holdout + 2023-04..2024-01 look for all rows (no selection on holdout); direct L2 replay for rows meeting the PRE rule (mean > 0 and placebo >= 0.90) and then holdout-positive.
* Placebo = random exit timing, same cut count, time-in-trade fractions drawn from the cell's own cuts (300 draws, WF window); the best-of-N null (max over the 26-28 cells of the same entry, same draw index) is in each row (`placebo_best_of_n`). No cell reached CANDIDATE, so DSR was not needed for a verdict; the LEAD rows' best-of-N ranks are quoted in section 5.
* Truncation-invariance audit (`out/g3/trunc_audit.json`): 300 sampled cut decisions per mechanism with every row from the exit row on replaced by noise: decisions unchanged in all four tape/vol mechanisms (bad = [0, 0, 0, 0]). Tape coverage 96.7% of 1-s rows; rows only exist for traded seconds, so a quiet second is evaluated at the next traded second (NT8 evaluates per tick, a superset).
* Executability: tape cuts (IMB, ABS, DIV) need the aggressor side of each print: execution-server-only (EXEC_SERVER_PREFERRED; NT8 can classify from Last vs bid/ask at tick time but tick ordering differs from the server tape). VOLCOL, OPP, SESSEND are price/time-only (NT8 feasible; OPP needs the faster book's signal inside the same strategy). Every row carries `exec_status`.

## 2. Honest effects and MDE (per mechanism, WF, all entries)
Predicted effects were ~0 (PRED block B tape AUC 0.50-0.54) and below the MDE; the rows confirm it. Median bootstrap MDE per row (80% power): tape/OPP/VOLCOL rows 1.2-1.8 pts/trade (ST/KB about 1.0, SM/EM about 2.2; the cut share is 20-90%), SESSEND 0.19 (1-4% cuts). A null here reads "could not have seen less than that".

| grp     |   rows |   median_eff |   best |   worst |   positive |   median_MDE |   median_cut_share |   median_would_hit |
|:--------|-------:|-------------:|-------:|--------:|-----------:|-------------:|-------------------:|-------------------:|
| ABS     |     20 |       -0.831 | -0.412 |  -1.508 |          0 |        1.344 |              0.344 |              0.486 |
| DIV     |     10 |       -0.778 |  0.154 |  -1.526 |          1 |        1.237 |              0.363 |              0.675 |
| IMB     |     40 |       -1.429 | -0.46  |  -2.819 |          0 |        1.8   |              0.675 |              0.402 |
| OPP     |     13 |       -0.937 |  0.415 |  -2.023 |          2 |        1.316 |              0.446 |              0.318 |
| SESSEND |     30 |        0.002 |  0.092 |  -0.5   |         16 |        0.187 |              0.019 |              0.117 |
| VOLCOL  |     20 |       -1.363 | -0.75  |  -2.64  |          0 |        1.497 |              0.479 |              0.468 |

Base outcome mix (WF): 50% target / 46% stop / 3% time at every entry. The cuts' would-hit-target share is 0.40 (IMB) - 0.49 (ABS) - 0.67 (DIV: in-profit trades) against 0.50 base, i.e. tape imbalance carries a thin 0-10 point separation, far from the 40+ points a market-exit cost of 1 pt plus the lost 60-pt target upside needs. This replicates PRED block B's AUC 0.50-0.54 on the exit side.

## 3. Named control: live TH-loss-on-ST on every entry (paired, WF)
| entry | paired pts/trade [CI] | MDE | HOLD | 2023-04..24-01 | cut share | EV per cut | would-hit-target | placebo rank | d mean $/wk | d maxDD $ |
|--|--|--|--|--|--|--|--|--|--|--|
| ST | -0.97 [-1.95, -0.07] | 1.35 | -0.37 | -0.08 | 61% | -1.16 | 0.29 | 0.81 | -11,224 | +279,991 |
| HM | -1.28 [-2.42, -0.13] | 1.68 | -2.03 | -0.22 | 62% | -1.66 | 0.29 | 0.88 | -8,108 | -53,665 |
| KB | -0.91 [-1.95, 0.05] | 1.40 | -0.54 | -0.32 | 62% | -1.26 | 0.29 | 0.86 | -10,020 | -15,415 |
| SM | -1.34 [-3.27, 0.44] | 2.73 | -0.25 | -0.20 | 61% | -1.37 | 0.29 | 0.93 | -4,539 | +33,933 |
| EM | -1.79 [-3.77, 0.05] | 2.77 | -1.91 | -0.90 | 61% | -1.94 | 0.29 | 0.55 | -4,501 | -28,257 |

The rule fires on 61% of trades in the backtest (every trade that goes 15 pts adverse and then looks choppy) and costs 0.9-1.8 pts/trade on every entry, negative in WF, holdout and the 2023 span, consistent with G1 (autopilot/DS3_TH_G1.md). The forward replay's +5.6 pts per cut (n=50, CI -11.8..+22.3, REPORT_FORWARD_TH) is inside the backtest per-cut CI; per-cut here is -1.2 to -1.9 pts and the forward sample's 24-point MDE could not distinguish them.

## 4. Top 20 per entry family (control row first)
Columns: paired pts/trade [CI], MDE, HOLD, 2023-04..24-01, cuts, P&L of cut trades vs the uncut counterfactual (points, mapped-free), would-hit-target share, EV per cut, trades/wk, weekly mean/SD/maxDD (family at 14 lots ST/HM, 10 lots KB/SM/EM, per-book locks), d vs base mean/maxDD, 2x cost, long/short, by session, quiet/wide, placebo rank, neighbours, verdict. Every one of the 138 rows is in the rows file.

### ST: top 20 of 28 cells by WF paired effect (control row first)

| cell | entry | WF paired pts/trade [CI] | MDE | HOLD | 2023-04..24-01 | cuts (share) | P&L cut / uncut pts | would-hit-target | EV per cut | trades/wk | weekly mean/SD/maxDD $ (10-14 lots) | d mean / d maxDD $ | 2x cost | long/short | Asia/London/NY | quiet/wide | placebo rank | nbrs | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| TH_LIVE_ST | ST | -0.969 [-1.95, -0.07] | 1.35 | -0.372 | -0.081 | 4232 (61%) | -22.7 / -21.5 | 0.29 | -1.16 | 75.4 | 19,878 / 103,551 / 729,118 | -11,224 / +279,991 | -1.14 | -0.56/-1.33 | -1.28/-0.77/-0.91 | -1.98/-0.12 | 0.81 |  | DEAD |
| SESSEND_LONDON_x45 | ST | 0.027 [-0.11, 0.15] | 0.19 | 0.068 | -0.098 | 147 (2%) | -43.1 / -43.5 | 0.11 | 0.43 | 75.4 | 33,102 / 106,310 / 440,727 | +2,000 / -8,400 | 0.02 | 0.03/0.02 | 0.04/0.06/0.00 | -0.00/0.05 | 0.79 | False | DEAD |
| SESSEND_NY_x30 | ST | 0.013 [-0.01, 0.03] | 0.03 | -0.000 | -0.053 | 48 (1%) | -35.7 / -36.6 | 0.00 | 0.88 | 75.4 | 31,158 / 107,298 / 450,820 | +57 / +1,693 | 0.01 | 0.02/0.00 | 0.00/0.01/0.02 | 0.02/0.01 | 0.79 | True | DEAD |
| SESSEND_NY_x45 | ST | 0.002 [-0.01, 0.01] | 0.02 | -0.008 | -0.023 | 17 (0%) | -46.9 / -47.0 | 0.00 | 0.03 | 75.4 | 31,146 / 107,273 / 449,127 | +45 / +0 | 0.00 | 0.02/-0.01 | 0.00/0.01/0.00 | 0.01/-0.01 | 0.62 | True | DEAD |
| OPP_EM | ST | -0.015 [-0.37, 0.31] | 0.50 | 0.308 | -0.195 | 651 (12%) | -22.3 / -22.2 | 0.28 | -0.15 | 75.4 | 26,137 / 110,681 / 542,240 | -4,964 / +93,113 | -0.04 | -0.06/0.02 | -0.12/0.59/-0.31 | -0.06/0.02 | 0.82 | True | DEAD |
| SESSEND_ASIA_x45 | ST | -0.036 [-0.15, 0.07] | 0.16 | -0.030 | -0.073 | 93 (1%) | -43.7 / -41.3 | 0.14 | -2.39 | 75.4 | 30,953 / 107,671 / 439,677 | -149 / -9,450 | -0.04 | -0.00/-0.06 | -0.02/-0.11/0.00 | -0.13/0.04 | 0.40 | True | DEAD |
| OPP_SM | ST | -0.089 [-0.44, 0.24] | 0.49 | 0.138 | -0.106 | 612 (11%) | -25.1 / -24.8 | 0.27 | -0.34 | 75.4 | 30,978 / 108,201 / 488,961 | -123 / +39,834 | -0.11 | -0.00/-0.16 | 0.16/-0.43/-0.03 | -0.17/-0.02 | 0.68 | True | DEAD |
| SESSEND_ASIA_x30 | ST | -0.192 [-0.40, -0.00] | 0.29 | -0.105 | -0.479 | 184 (3%) | -32.9 / -25.3 | 0.28 | -7.58 | 75.4 | 30,951 / 107,646 / 404,305 | -150 / -44,822 | -0.20 | -0.29/-0.11 | -0.57/-0.17/0.00 | -0.44/0.01 | 0.10 | True | DEAD |
| SESSEND_LONDON_x30 | ST | -0.246 [-0.51, -0.01] | 0.36 | -0.090 | 0.302 | 280 (4%) | -31.2 / -26.9 | 0.26 | -4.28 | 75.4 | 31,566 / 107,347 / 437,577 | +465 / -11,550 | -0.26 | -0.25/-0.24 | 0.06/-0.96/0.00 | -0.41/-0.10 | 0.02 | False | DEAD |
| ABS_w60_g1 | ST | -0.412 [-0.90, 0.07] | 0.70 | -0.114 | -1.141 | 1078 (18%) | -0.3 / 2.4 | 0.45 | -2.70 | 75.4 | 29,558 / 102,208 / 459,877 | -1,544 / +10,751 | -0.48 | -0.22/-0.58 | -0.07/-0.24/-0.70 | -0.96/0.04 | 0.29 | True | DEAD |
| IMB_t70_w60_g0 | ST | -0.629 [-1.30, 0.10] | 0.96 | -0.515 | -0.670 | 1995 (31%) | -10.2 / -8.1 | 0.39 | -2.11 | 75.4 | 30,631 / 99,356 / 480,842 | -471 / +31,715 | -0.73 | -0.90/-0.39 | -1.36/-0.70/-0.19 | -1.47/0.08 | 0.38 | True | DEAD |
| IMB_t70_w60_g1 | ST | -0.638 [-1.27, 0.02] | 0.88 | -0.436 | -0.334 | 1788 (27%) | -15.4 / -13.3 | 0.34 | -2.15 | 75.4 | 29,500 / 98,967 / 447,977 | -1,601 / -1,149 | -0.72 | -0.82/-0.48 | -1.02/-0.99/-0.23 | -1.45/0.04 | 0.30 | True | DEAD |
| ABS_w60_g0 | ST | -0.661 [-1.20, -0.11] | 0.77 | -0.320 | -1.565 | 1308 (23%) | 3.7 / 7.2 | 0.50 | -3.48 | 75.4 | 26,088 / 104,552 / 430,424 | -5,013 / -18,703 | -0.75 | -0.66/-0.66 | -0.36/-0.27/-1.05 | -1.29/-0.13 | 0.14 | True | DEAD |
| VOLCOL_f25_h20 | ST | -0.750 [-1.38, -0.14] | 0.91 | -0.515 | -1.224 | 1962 (30%) | -1.3 / 1.1 | 0.45 | -2.43 | 75.4 | 21,927 / 104,452 / 597,670 | -9,174 / +148,543 | -0.88 | -0.67/-0.82 | -2.14/-0.22/-0.30 | -1.24/-0.34 | 0.28 | True | DEAD |
| DIV_w60 | ST | -0.806 [-1.47, -0.12] | 0.97 | -0.511 | -0.661 | 2007 (30%) | 23.2 / 25.7 | 0.68 | -2.44 | 75.4 | 26,060 / 103,130 / 680,869 | -5,041 / +231,742 | -1.00 | -0.13/-1.40 | -1.12/-0.91/-0.58 | -1.14/-0.53 | 0.20 | True | DEAD |
| ABS_w30_g1 | ST | -0.847 [-1.63, -0.06] | 1.12 | -0.632 | -1.514 | 2682 (42%) | -1.5 / 0.5 | 0.47 | -2.06 | 75.4 | 32,220 / 107,216 / 501,651 | +1,119 / +52,524 | -1.03 | -0.80/-0.89 | -0.56/-0.31/-1.31 | -1.48/-0.32 | 0.38 | True | DEAD |
| IMB_t70_w30_g1 | ST | -0.873 [-1.78, -0.00] | 1.29 | -0.773 | -1.002 | 3573 (53%) | -11.6 / -9.9 | 0.38 | -1.74 | 75.4 | 18,890 / 89,601 / 566,891 | -12,211 / +117,764 | -1.06 | -0.13/-1.52 | -1.18/-1.34/-0.44 | -2.01/0.08 | 0.77 | True | DEAD |
| DIV_w30 | ST | -0.876 [-1.69, -0.03] | 1.17 | -0.891 | -0.687 | 3014 (43%) | 22.6 / 24.4 | 0.68 | -1.84 | 75.4 | 23,216 / 99,345 / 634,098 | -7,885 / +184,971 | -1.17 | -0.39/-1.30 | -0.98/-0.76/-0.89 | -0.60/-1.11 | 0.48 | True | DEAD |
| VOLCOL_f25_h10 | ST | -0.906 [-1.54, -0.27] | 0.92 | -0.529 | -1.118 | 2051 (31%) | -1.3 / 1.4 | 0.45 | -2.74 | 75.4 | 17,575 / 102,215 / 622,423 | -13,527 / +173,296 | -1.04 | -0.85/-0.95 | -2.39/-0.59/-0.28 | -1.51/-0.40 | 0.14 | True | DEAD |
| OPP_KB | ST | -1.178 [-1.94, -0.44] | 1.08 | -0.711 | -1.325 | 2867 (44%) | -19.1 / -16.7 | 0.32 | -2.48 | 75.4 | 18,872 / 101,352 / 592,650 | -12,229 / +143,523 | -1.30 | -1.34/-1.04 | -1.66/-1.29/-0.85 | -2.82/0.20 | 0.12 | True | DEAD |
| OPP_ANY | ST | -1.199 [-1.97, -0.44] | 1.09 | -0.713 | -1.352 | 2875 (45%) | -19.1 / -16.6 | 0.32 | -2.54 | 75.4 | 18,853 / 101,309 / 590,340 | -12,248 / +141,213 | -1.32 | -1.39/-1.04 | -1.68/-1.31/-0.88 | -2.78/0.12 | 0.10 | True | DEAD |

### HM: top 20 of 28 cells by WF paired effect (control row first)

| cell | entry | WF paired pts/trade [CI] | MDE | HOLD | 2023-04..24-01 | cuts (share) | P&L cut / uncut pts | would-hit-target | EV per cut | trades/wk | weekly mean/SD/maxDD $ (10-14 lots) | d mean / d maxDD $ | 2x cost | long/short | Asia/London/NY | quiet/wide | placebo rank | nbrs | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| TH_LIVE_ST | HM | -1.275 [-2.42, -0.13] | 1.68 | -2.034 | -0.217 | 3185 (62%) | -22.6 / -20.9 | 0.29 | -1.66 | 75.4 | 22,993 / 99,368 / 395,462 | -8,108 / -53,665 | -1.45 | -0.63/-1.95 | -1.48/-0.89/-1.40 | -1.67/-0.93 | 0.88 |  | DEAD |
| OPP_EM | HM | 0.415 [-0.02, 0.86] | 0.64 | 0.449 | 0.059 | 556 (13%) | -20.5 / -23.2 | 0.27 | 2.70 | 75.4 | 38,170 / 108,153 / 363,701 | +7,069 / -85,425 | 0.39 | 0.44/0.39 | 1.08/0.24/0.07 | 0.92/-0.02 | 1.00 | False | DEAD |
| OPP_SM | HM | 0.280 [-0.13, 0.74] | 0.59 | 0.293 | -0.155 | 516 (13%) | -22.5 / -24.4 | 0.27 | 1.87 | 75.4 | 34,025 / 105,236 / 367,544 | +2,923 / -81,583 | 0.26 | 0.45/0.10 | 1.11/-0.26/0.06 | 0.68/-0.06 | 1.00 | False | DEAD |
| SESSEND_LONDON_x45 | HM | 0.092 [-0.04, 0.22] | 0.18 | 0.031 | 0.156 | 110 (2%) | -43.3 / -46.6 | 0.09 | 3.33 | 75.4 | 31,988 / 107,804 / 435,375 | +887 / -13,752 | 0.09 | 0.07/0.11 | 0.07/0.25/0.00 | 0.11/0.08 | 0.97 | False | DEAD |
| SESSEND_ASIA_x45 | HM | 0.014 [-0.10, 0.11] | 0.16 | -0.006 | 0.014 | 65 (1%) | -43.8 / -45.1 | 0.10 | 1.25 | 75.4 | 32,473 / 107,630 / 443,037 | +1,372 / -6,090 | 0.01 | 0.06/-0.03 | 0.02/0.03/0.00 | -0.02/0.05 | 0.71 | False | DEAD |
| SESSEND_NY_x30 | HM | 0.013 [-0.01, 0.03] | 0.03 | 0.020 | 0.035 | 40 (1%) | -35.9 / -37.4 | 0.00 | 1.46 | 75.4 | 31,113 / 107,203 / 448,855 | +12 / -272 | 0.01 | 0.02/0.00 | -0.00/0.00/0.03 | 0.03/-0.00 | 0.76 | True | DEAD |
| SESSEND_NY_x45 | HM | 0.003 [-0.01, 0.02] | 0.02 | 0.011 | 0.006 | 19 (0%) | -47.0 / -47.9 | 0.00 | 0.88 | 75.4 | 31,079 / 107,293 / 451,161 | -22 / +2,034 | 0.00 | 0.01/-0.00 | 0.00/0.00/0.01 | 0.01/-0.01 | 0.63 | True | DEAD |
| SESSEND_ASIA_x30 | HM | -0.034 [-0.26, 0.16] | 0.30 | -0.115 | 0.020 | 131 (3%) | -32.8 / -32.8 | 0.21 | -0.08 | 75.4 | 32,773 / 108,937 / 414,685 | +1,672 / -34,442 | -0.04 | -0.02/-0.04 | -0.08/-0.03/0.00 | -0.19/0.10 | 0.61 | False | DEAD |
| SESSEND_LONDON_x30 | HM | -0.353 [-0.64, -0.04] | 0.43 | -0.491 | 0.134 | 211 (4%) | -31.8 / -24.5 | 0.28 | -7.29 | 75.4 | 30,141 / 106,856 / 417,665 | -960 / -31,462 | -0.37 | -0.22/-0.50 | -0.22/-1.02/0.00 | -0.68/-0.08 | 0.01 | False | DEAD |
| IMB_t70_w60_g1 | HM | -0.460 [-1.27, 0.31] | 1.12 | -0.630 | -0.120 | 1525 (32%) | -14.7 / -13.4 | 0.34 | -1.23 | 75.4 | 30,005 / 108,893 / 469,540 | -1,096 / +20,413 | -0.56 | -0.28/-0.65 | -0.56/-0.65/-0.26 | -1.11/0.09 | 0.80 | True | DEAD |
| ABS_w60_g1 | HM | -0.556 [-1.15, 0.05] | 0.84 | -0.837 | -0.572 | 935 (21%) | 0.8 / 3.0 | 0.45 | -2.15 | 75.4 | 27,782 / 106,414 / 385,652 | -3,320 / -63,475 | -0.64 | 0.09/-1.24 | -0.39/-0.20/-0.91 | -0.47/-0.63 | 0.36 | True | DEAD |
| IMB_t70_w60_g0 | HM | -0.568 [-1.40, 0.23] | 1.17 | -0.879 | -0.419 | 1699 (36%) | -9.2 / -7.9 | 0.39 | -1.37 | 75.4 | 28,544 / 108,869 / 483,276 | -2,557 / +34,149 | -0.69 | -0.32/-0.83 | -0.90/-0.85/-0.16 | -1.22/-0.01 | 0.84 | True | DEAD |
| DIV_w60 | HM | -0.750 [-1.49, -0.00] | 1.08 | -0.343 | 1.030 | 1525 (31%) | 23.5 / 25.3 | 0.67 | -1.80 | 75.4 | 23,975 / 104,528 / 567,910 | -7,126 / +118,783 | -0.95 | -0.47/-1.05 | -0.79/-0.22/-1.08 | -1.13/-0.43 | 0.51 | True | DEAD |
| IMB_t70_w30_g1 | HM | -0.865 [-1.95, 0.23] | 1.60 | -1.011 | -0.404 | 2911 (58%) | -10.9 / -9.6 | 0.38 | -1.30 | 75.4 | 21,885 / 100,229 / 358,608 | -9,216 / -90,519 | -1.08 | -0.19/-1.58 | -1.40/-1.35/-0.17 | -1.43/-0.38 | 0.98 | True | DEAD |
| ABS_w60_g0 | HM | -0.870 [-1.45, -0.24] | 0.91 | -0.884 | -0.671 | 1158 (27%) | 4.9 / 7.9 | 0.50 | -3.04 | 75.4 | 29,155 / 106,005 / 366,110 | -1,946 / -83,017 | -0.98 | -0.48/-1.28 | -0.94/-0.50/-1.06 | -0.91/-0.84 | 0.21 | True | DEAD |
| OPP_KB | HM | -0.899 [-1.83, 0.01] | 1.32 | -0.633 | -0.604 | 2295 (48%) | -17.8 / -16.1 | 0.32 | -1.62 | 75.4 | 23,817 / 99,877 / 495,033 | -7,284 / +45,906 | -1.03 | -1.09/-0.70 | -2.01/-0.53/-0.37 | -1.59/-0.31 | 0.77 | False | DEAD |
| OPP_ANY | HM | -0.937 [-1.89, -0.03] | 1.32 | -0.607 | -0.537 | 2301 (48%) | -17.8 / -16.1 | 0.32 | -1.66 | 75.4 | 23,651 / 99,354 / 499,780 | -7,450 / +50,653 | -1.07 | -1.11/-0.75 | -2.05/-0.63/-0.37 | -1.64/-0.34 | 0.72 | False | DEAD |
| VOLCOL_f25_h20 | HM | -0.995 [-1.82, -0.19] | 1.16 | -0.980 | -1.301 | 1636 (34%) | -0.1 / 2.8 | 0.46 | -2.90 | 75.4 | 15,395 / 101,022 / 552,160 | -15,706 / +103,033 | -1.14 | -0.75/-1.25 | -3.36/-0.08/0.03 | -1.51/-0.55 | 0.36 | True | DEAD |
| ABS_w30_g1 | HM | -1.023 [-1.93, -0.01] | 1.39 | -1.471 | 0.434 | 2178 (46%) | -1.3 / 0.4 | 0.46 | -1.69 | 75.4 | 29,075 / 111,349 / 426,764 | -2,027 / -22,363 | -1.22 | -0.46/-1.62 | -0.95/-0.74/-1.26 | -1.08/-0.97 | 0.60 | True | DEAD |
| VOLCOL_f25_h10 | HM | -1.229 [-2.04, -0.43] | 1.18 | -1.335 | -1.121 | 1707 (35%) | -0.4 / 2.9 | 0.46 | -3.27 | 75.4 | 14,554 / 102,892 / 567,593 | -16,547 / +118,466 | -1.38 | -1.04/-1.42 | -3.68/-0.44/-0.06 | -1.69/-0.84 | 0.20 | True | DEAD |
| IMB_t70_w30_g0 | HM | -1.272 [-2.44, -0.06] | 1.72 | -1.586 | -0.771 | 3371 (67%) | -4.0 / -2.3 | 0.44 | -1.74 | 75.4 | 18,712 / 100,687 / 530,676 | -12,389 / +81,549 | -1.56 | -0.53/-2.05 | -3.28/-0.87/-0.16 | -2.09/-0.57 | 0.97 | True | DEAD |

### KB: top 20 of 24 cells by WF paired effect (control row first)

| cell | entry | WF paired pts/trade [CI] | MDE | HOLD | 2023-04..24-01 | cuts (share) | P&L cut / uncut pts | would-hit-target | EV per cut | trades/wk | weekly mean/SD/maxDD $ (10-14 lots) | d mean / d maxDD $ | 2x cost | long/short | Asia/London/NY | quiet/wide | placebo rank | nbrs | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| TH_LIVE_ST | KB | -0.912 [-1.95, 0.05] | 1.40 | -0.543 | -0.320 | 4481 (62%) | -22.7 / -21.4 | 0.29 | -1.26 | 44.3 | 6,182 / 48,727 / 362,277 | -10,020 / -15,415 | -1.08 | -0.20/-1.67 | -1.97/-1.15/-0.16 | -1.17/-0.69 | 0.86 |  | DEAD |
| SESSEND_NY_x45 | KB | 0.008 [-0.00, 0.02] | 0.02 | 0.009 | -0.010 | 18 (0%) | -46.7 / -49.0 | 0.00 | 2.35 | 44.3 | 16,270 / 59,331 / 377,692 | +69 / +0 | 0.01 | 0.02/-0.00 | 0.00/0.00/0.02 | 0.02/-0.00 | 0.77 | True | DEAD |
| SESSEND_NY_x30 | KB | 0.006 [-0.01, 0.03] | 0.03 | 0.006 | -0.049 | 49 (1%) | -36.6 / -36.9 | 0.00 | 0.32 | 44.3 | 16,252 / 59,380 / 377,692 | +50 / +0 | 0.01 | 0.01/-0.00 | 0.00/-0.00/0.01 | 0.02/-0.01 | 0.70 | True | DEAD |
| SESSEND_LONDON_x45 | KB | -0.010 [-0.15, 0.11] | 0.19 | -0.005 | -0.089 | 152 (2%) | -43.3 / -43.2 | 0.12 | -0.12 | 44.3 | 16,662 / 60,403 / 377,692 | +460 / +0 | -0.01 | 0.09/-0.11 | -0.03/-0.01/0.00 | 0.12/-0.12 | 0.61 | True | DEAD |
| SESSEND_ASIA_x45 | KB | -0.061 [-0.19, 0.05] | 0.16 | -0.031 | -0.166 | 87 (1%) | -43.6 / -37.7 | 0.17 | -5.90 | 44.3 | 15,407 / 58,657 / 370,192 | -794 / -7,500 | -0.06 | 0.02/-0.15 | 0.00/-0.23/0.00 | -0.09/-0.04 | 0.14 | True | DEAD |
| SESSEND_ASIA_x30 | KB | -0.072 [-0.25, 0.11] | 0.25 | -0.118 | 0.015 | 166 (3%) | -32.1 / -29.1 | 0.24 | -3.01 | 44.3 | 15,867 / 58,579 / 377,474 | -335 / -218 | -0.08 | 0.05/-0.20 | 0.02/-0.30/0.00 | -0.01/-0.12 | 0.34 | True | DEAD |
| SESSEND_LONDON_x30 | KB | -0.274 [-0.53, -0.05] | 0.35 | -0.367 | -0.261 | 277 (4%) | -31.2 / -25.4 | 0.27 | -5.88 | 44.3 | 15,784 / 59,235 / 377,692 | -418 / +0 | -0.29 | -0.19/-0.37 | 0.04/-1.10/0.00 | -0.27/-0.27 | 0.03 | True | DEAD |
| IMB_t70_w60_g1 | KB | -0.626 [-1.23, 0.02] | 0.88 | -0.425 | 0.215 | 1841 (28%) | -14.4 / -12.7 | 0.34 | -1.67 | 44.3 | 11,133 / 54,735 / 522,276 | -5,068 / +144,584 | -0.71 | -0.42/-0.85 | -0.91/-1.05/-0.22 | -1.09/-0.24 | 0.25 | True | DEAD |
| ABS_w30_g1 | KB | -0.650 [-1.49, 0.15] | 1.18 | -0.546 | -0.605 | 2946 (44%) | -2.0 / -0.5 | 0.45 | -1.53 | 44.3 | 13,844 / 50,070 / 290,919 | -2,358 / -86,773 | -0.84 | -0.26/-1.06 | -1.10/-1.22/-0.07 | -1.31/-0.09 | 0.69 | True | DEAD |
| ABS_w60_g1 | KB | -0.675 [-1.15, -0.15] | 0.71 | -0.741 | -1.010 | 1287 (21%) | -0.0 / 3.5 | 0.46 | -3.49 | 44.3 | 10,126 / 52,760 / 362,696 | -6,075 / -14,996 | -0.76 | -0.23/-1.15 | -0.41/-0.91/-0.70 | -1.23/-0.21 | 0.06 | True | DEAD |
| ABS_w60_g0 | KB | -0.816 [-1.36, -0.25] | 0.79 | -0.788 | -1.172 | 1526 (25%) | 3.5 / 7.0 | 0.50 | -3.59 | 44.3 | 8,125 / 52,549 / 348,196 | -8,077 / -29,496 | -0.92 | -0.42/-1.23 | -0.49/-0.61/-1.12 | -1.18/-0.51 | 0.07 | True | DEAD |
| DIV_w30 | KB | -0.849 [-1.66, -0.08] | 1.13 | -0.662 | 0.382 | 3088 (43%) | 21.9 / 23.6 | 0.67 | -1.70 | 44.3 | 4,792 / 46,313 / 396,853 | -11,410 / +19,161 | -1.14 | -0.60/-1.11 | -0.88/-0.55/-1.00 | -0.67/-1.00 | 0.46 | True | DEAD |
| DIV_w60 | KB | -0.877 [-1.56, -0.26] | 0.87 | -0.894 | 0.045 | 2047 (30%) | 22.9 / 25.5 | 0.68 | -2.63 | 44.3 | 8,043 / 53,493 / 375,821 | -8,159 / -1,871 | -1.07 | -0.63/-1.14 | -0.92/-0.95/-0.81 | -1.18/-0.62 | 0.11 | True | DEAD |
| IMB_t70_w60_g0 | KB | -0.924 [-1.58, -0.26] | 0.95 | -0.685 | -0.461 | 2085 (32%) | -9.4 / -6.8 | 0.40 | -2.58 | 44.3 | 6,490 / 54,437 / 689,685 | -9,711 / +311,993 | -1.04 | -0.76/-1.10 | -1.74/-1.20/-0.29 | -1.47/-0.47 | 0.09 | True | DEAD |
| VOLCOL_f25_h20 | KB | -1.079 [-1.70, -0.40] | 0.97 | -0.606 | -0.116 | 2062 (31%) | -1.3 / 1.4 | 0.45 | -2.76 | 44.3 | 5,904 / 53,583 / 582,467 | -10,297 / +204,775 | -1.21 | -1.46/-0.68 | -2.55/-0.91/-0.31 | -1.86/-0.42 | 0.06 | True | DEAD |
| IMB_t70_w30_g1 | KB | -1.079 [-2.04, -0.19] | 1.30 | -1.187 | 0.267 | 3776 (54%) | -11.6 / -10.0 | 0.38 | -1.53 | 44.3 | 6,657 / 52,255 / 609,571 | -9,544 / +231,879 | -1.27 | -0.84/-1.34 | -1.35/-2.15/-0.32 | -1.38/-0.82 | 0.54 | True | DEAD |
| ABS_w30_g0 | KB | -1.155 [-2.08, -0.21] | 1.31 | -0.592 | -1.312 | 3563 (54%) | 3.5 / 5.7 | 0.51 | -2.24 | 44.3 | 7,917 / 45,038 / 273,967 | -8,285 / -103,725 | -1.41 | -0.98/-1.34 | -1.60/-1.24/-0.85 | -1.73/-0.67 | 0.33 | True | DEAD |
| IMB_t60_w60_g1 | KB | -1.178 [-2.27, -0.21] | 1.49 | -0.735 | -0.262 | 4583 (66%) | -12.5 / -11.0 | 0.37 | -1.52 | 44.3 | 3,147 / 44,804 / 577,791 | -13,055 / +200,099 | -1.41 | -0.93/-1.44 | -2.15/-1.58/-0.39 | -2.17/-0.35 | 0.65 | True | DEAD |
| VOLCOL_f25_h10 | KB | -1.256 [-1.93, -0.56] | 1.00 | -0.867 | -0.042 | 2154 (32%) | -1.6 / 1.6 | 0.45 | -3.14 | 44.3 | 4,036 / 50,141 / 566,870 | -12,166 / +189,178 | -1.39 | -1.67/-0.81 | -2.68/-1.50/-0.29 | -2.04/-0.59 | 0.01 | True | DEAD |
| VOLCOL_f40_h10 | KB | -1.302 [-2.26, -0.33] | 1.40 | -1.008 | -0.477 | 4322 (62%) | -0.8 / 1.0 | 0.47 | -1.88 | 44.3 | 1,291 / 45,877 / 721,863 | -14,910 / +344,171 | -1.58 | -1.14/-1.48 | -2.57/-1.56/-0.42 | -2.11/-0.62 | 0.45 | True | DEAD |
| VOLCOL_f40_h20 | KB | -1.367 [-2.31, -0.53] | 1.32 | -1.154 | -0.440 | 3832 (56%) | -1.1 / 1.0 | 0.47 | -2.18 | 44.3 | 474 / 47,024 / 729,307 | -15,728 / +351,615 | -1.62 | -1.11/-1.64 | -2.60/-1.24/-0.72 | -2.01/-0.83 | 0.20 | True | DEAD |

### SM: top 20 of 27 cells by WF paired effect (control row first)

| cell | entry | WF paired pts/trade [CI] | MDE | HOLD | 2023-04..24-01 | cuts (share) | P&L cut / uncut pts | would-hit-target | EV per cut | trades/wk | weekly mean/SD/maxDD $ (10-14 lots) | d mean / d maxDD $ | 2x cost | long/short | Asia/London/NY | quiet/wide | placebo rank | nbrs | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| TH_LIVE_ST | SM | -1.342 [-3.27, 0.44] | 2.73 | -0.246 | -0.195 | 1126 (61%) | -22.6 / -21.2 | 0.29 | -1.37 | 12.4 | 4,982 / 28,597 / 226,050 | -4,539 / +33,933 | -1.52 | -1.84/-0.86 | -1.54/-2.59/0.19 | -1.08/-1.55 | 0.93 |  | DEAD |
| SESSEND_ASIA_x45 | SM | 0.041 [-0.13, 0.19] | 0.23 | -0.097 | 0.014 | 22 (1%) | -43.7 / -46.4 | 0.10 | 2.64 | 12.4 | 9,628 / 35,486 / 192,117 | +107 / -0 | 0.04 | -0.10/0.18 | -0.05/0.16/0.00 | 0.00/0.07 | 0.72 | False | DEAD |
| SESSEND_NY_x45 | SM | 0.008 [0.00, 0.02] | 0.02 | 0.000 | 0.012 | 1 (0%) | -47.2 / -52.0 | 0.00 | 4.85 | 12.4 | 9,543 / 35,887 / 192,117 | +21 / -0 | 0.01 | 0.02/0.00 | 0.00/0.00/0.02 | 0.00/0.01 | - | True | DEAD |
| SESSEND_NY_x30 | SM | 0.004 [-0.02, 0.03] | 0.04 | -0.015 | 0.034 | 4 (1%) | -38.7 / -40.8 | 0.00 | 2.15 | 12.4 | 9,553 / 35,886 / 192,117 | +31 / +0 | 0.00 | 0.02/-0.01 | 0.00/0.00/0.01 | 0.00/0.01 | 0.58 | True | DEAD |
| SESSEND_LONDON_x45 | SM | -0.206 [-0.63, 0.15] | 0.57 | -0.150 | 0.373 | 65 (3%) | -43.4 / -40.6 | 0.14 | -2.84 | 12.4 | 8,973 / 35,889 / 202,038 | -549 / +9,921 | -0.21 | -0.20/-0.21 | -0.19/-0.41/0.00 | -0.21/-0.20 | 0.22 | True | DEAD |
| SESSEND_LONDON_x30 | SM | -0.256 [-0.91, 0.32] | 0.85 | -0.130 | 0.732 | 103 (6%) | -31.8 / -31.0 | 0.22 | -0.72 | 12.4 | 8,694 / 35,460 / 200,200 | -828 / +8,083 | -0.27 | -0.12/-0.39 | -0.27/-0.48/0.00 | -0.45/-0.10 | 0.36 | True | DEAD |
| SESSEND_ASIA_x30 | SM | -0.367 [-0.83, 0.09] | 0.67 | -0.573 | 0.618 | 62 (3%) | -32.2 / -25.9 | 0.26 | -6.28 | 12.4 | 8,364 / 34,370 / 182,317 | -1,158 / -9,800 | -0.38 | -0.56/-0.18 | -1.09/-0.10/0.00 | -0.52/-0.25 | 0.13 | False | DEAD |
| ABS_w60_g1 | SM | -0.458 [-1.41, 0.51] | 1.38 | -0.082 | 0.628 | 285 (20%) | 0.5 / 1.0 | 0.45 | -0.52 | 12.4 | 8,347 / 35,407 / 192,662 | -1,174 / +545 | -0.53 | -0.35/-0.56 | -0.26/0.13/-1.27 | -0.47/-0.45 | 0.64 | True | DEAD |
| DIV_w30 | SM | -0.521 [-2.17, 1.00] | 2.24 | -0.248 | 0.736 | 778 (44%) | 23.2 / 23.0 | 0.67 | 0.12 | 12.4 | 7,763 / 32,332 / 176,141 | -1,758 / -15,976 | -0.81 | -1.79/0.70 | 0.97/-0.41/-1.99 | 0.54/-1.37 | 0.97 | True | DEAD |
| OPP_EM | SM | -0.548 [-1.56, 0.37] | 1.38 | 0.117 | -0.292 | 296 (20%) | -22.7 / -20.5 | 0.29 | -2.15 | 12.4 | 7,561 / 33,770 / 191,855 | -1,961 / -262 | -0.59 | -0.94/-0.17 | -1.58/-0.09/-0.11 | -0.49/-0.60 | 0.52 | True | DEAD |
| DIV_w60 | SM | -0.584 [-1.83, 0.59] | 1.76 | 0.200 | 0.308 | 505 (29%) | 23.6 / 24.3 | 0.68 | -0.73 | 12.4 | 7,301 / 35,749 / 220,840 | -2,221 / +28,723 | -0.77 | -1.12/-0.07 | -0.54/-0.78/-0.42 | -0.15/-0.93 | 0.79 | True | DEAD |
| ABS_w60_g0 | SM | -0.737 [-1.86, 0.36] | 1.53 | 0.003 | -0.588 | 367 (25%) | 4.9 / 7.3 | 0.51 | -2.40 | 12.4 | 8,083 / 34,269 / 195,057 | -1,438 / +2,940 | -0.84 | -0.79/-0.68 | -0.75/-0.10/-1.42 | -0.91/-0.60 | 0.50 | True | DEAD |
| IMB_t70_w30_g0 | SM | -0.849 [-2.99, 1.13] | 2.95 | 0.358 | -2.666 | 1244 (70%) | -3.5 / -2.2 | 0.45 | -1.31 | 12.4 | 6,131 / 26,188 / 144,162 | -3,390 / -47,955 | -1.15 | -1.10/-0.61 | -2.98/0.28/-0.14 | 0.70/-2.09 | 1.00 | True | DEAD |
| IMB_t70_w60_g1 | SM | -1.099 [-2.50, 0.12] | 1.91 | -0.423 | 0.416 | 578 (34%) | -14.4 / -12.6 | 0.36 | -1.85 | 12.4 | 6,931 / 31,168 / 138,588 | -2,591 / -53,529 | -1.21 | -2.42/0.18 | -2.74/-0.74/0.01 | -0.44/-1.63 | 0.57 | True | DEAD |
| IMB_t70_w30_g1 | SM | -1.205 [-3.26, 0.68] | 2.72 | -0.212 | -0.533 | 1076 (60%) | -10.7 / -9.3 | 0.39 | -1.33 | 12.4 | 5,783 / 28,683 / 170,823 | -3,739 / -21,294 | -1.43 | -1.57/-0.85 | -3.07/-0.89/0.14 | -0.53/-1.74 | 0.95 | True | DEAD |
| VOLCOL_f25_h20 | SM | -1.306 [-2.75, 0.20] | 2.11 | -0.730 | -1.678 | 654 (37%) | -1.9 / 1.3 | 0.46 | -3.21 | 12.4 | 5,988 / 28,525 / 218,525 | -3,534 / +26,408 | -1.47 | -2.21/-0.44 | -3.87/-0.04/-0.35 | -0.80/-1.71 | 0.55 | True | DEAD |
| ABS_w30_g1 | SM | -1.320 [-2.95, 0.24] | 2.29 | 0.088 | -1.240 | 754 (46%) | -1.1 / 1.4 | 0.48 | -2.46 | 12.4 | 6,027 / 32,945 / 243,899 | -3,494 / +51,782 | -1.52 | -1.37/-1.27 | -1.66/-1.16/-1.18 | -0.93/-1.63 | 0.63 | True | DEAD |
| VOLCOL_f25_h10 | SM | -1.359 [-2.86, 0.18] | 2.18 | -0.810 | -1.758 | 679 (39%) | -1.9 / 1.5 | 0.46 | -3.35 | 12.4 | 5,446 / 28,029 / 223,175 | -4,076 / +31,058 | -1.53 | -2.41/-0.34 | -3.65/-0.43/-0.29 | -0.96/-1.68 | 0.56 | True | DEAD |
| IMB_t70_w60_g0 | SM | -1.364 [-2.99, -0.02] | 2.13 | -0.414 | -1.402 | 682 (41%) | -8.4 / -5.8 | 0.42 | -2.65 | 12.4 | 6,116 / 30,454 / 165,134 | -3,405 / -26,983 | -1.52 | -2.74/-0.04 | -3.55/-0.50/-0.32 | -0.94/-1.70 | 0.53 | True | DEAD |
| ABS_w30_g0 | SM | -1.508 [-3.27, 0.16] | 2.48 | 0.183 | -2.246 | 908 (55%) | 5.0 / 7.8 | 0.54 | -2.81 | 12.4 | 5,552 / 31,442 / 235,327 | -3,969 / +43,210 | -1.77 | -2.21/-0.83 | -1.89/-1.51/-1.16 | -1.41/-1.59 | 0.71 | True | DEAD |
| OPP_ANY | SM | -1.797 [-3.44, -0.16] | 2.35 | -0.679 | -1.297 | 871 (51%) | -14.9 / -12.1 | 0.36 | -2.79 | 12.4 | 4,756 / 28,670 / 314,735 | -4,765 / +122,618 | -1.96 | -1.61/-1.98 | -2.79/-1.72/-0.98 | -2.02/-1.62 | 0.53 | True | DEAD |

### EM: top 20 of 26 cells by WF paired effect (control row first)

| cell | entry | WF paired pts/trade [CI] | MDE | HOLD | 2023-04..24-01 | cuts (share) | P&L cut / uncut pts | would-hit-target | EV per cut | trades/wk | weekly mean/SD/maxDD $ (10-14 lots) | d mean / d maxDD $ | 2x cost | long/short | Asia/London/NY | quiet/wide | placebo rank | nbrs | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| TH_LIVE_ST | EM | -1.792 [-3.77, 0.05] | 2.77 | -1.908 | -0.897 | 1107 (61%) | -22.6 / -20.7 | 0.29 | -1.94 | 12.0 | 3,700 / 27,763 / 144,302 | -4,501 / -28,257 | -1.97 | -0.24/-3.24 | -0.49/-4.55/-0.37 | -2.66/-1.07 | 0.55 |  | DEAD |
| DIV_w30 | EM | 0.154 [-1.33, 1.71] | 2.17 | -0.373 | -1.403 | 744 (42%) | 23.8 / 23.8 | 0.67 | -0.01 | 12.0 | 9,149 / 29,288 / 141,542 | +948 / -31,017 | -0.12 | -0.03/0.32 | 1.06/0.34/-0.86 | 0.48/-0.12 | 0.97 | False | DEAD |
| SESSEND_ASIA_x45 | EM | 0.088 [-0.12, 0.24] | 0.25 | 0.048 | 0.029 | 29 (2%) | -43.7 / -48.8 | 0.07 | 5.06 | 12.0 | 8,427 / 34,226 / 166,559 | +226 / -6,000 | 0.09 | 0.06/0.11 | 0.15/0.13/0.00 | 0.09/0.09 | 0.85 | True | DEAD |
| SESSEND_ASIA_x30 | EM | 0.062 [-0.37, 0.49] | 0.60 | -0.149 | -0.072 | 72 (4%) | -32.4 / -33.9 | 0.20 | 1.45 | 12.0 | 8,158 / 33,515 / 146,945 | -43 / -25,615 | 0.05 | -0.26/0.36 | -0.09/0.27/0.00 | 0.26/-0.11 | 0.77 | True | DEAD |
| SESSEND_NY_x30 | EM | 0.031 [0.00, 0.07] | 0.05 | 0.017 | -0.111 | 9 (1%) | -35.8 / -36.3 | 0.00 | 0.51 | 12.0 | 8,286 / 34,238 / 172,559 | +84 / +0 | 0.03 | 0.05/0.01 | 0.00/0.00/0.09 | 0.05/0.02 | 0.79 | True | DEAD |
| SESSEND_NY_x45 | EM | 0.012 [-0.00, 0.03] | 0.02 | 0.005 | 0.019 | 4 (0%) | -46.8 / -51.1 | 0.00 | 4.31 | 12.0 | 8,232 / 34,229 / 172,559 | +31 / +0 | 0.01 | 0.02/0.00 | 0.00/0.00/0.04 | 0.02/0.00 | 0.69 | True | DEAD |
| SESSEND_LONDON_x45 | EM | -0.331 [-0.77, 0.06] | 0.59 | -0.259 | -0.322 | 59 (3%) | -44.0 / -35.7 | 0.19 | -8.27 | 12.0 | 7,294 / 34,786 / 166,559 | -907 / -6,000 | -0.34 | -0.05/-0.59 | -0.03/-0.97/0.00 | -0.80/0.06 | 0.05 | True | DEAD |
| DIV_w60 | EM | -0.445 [-1.56, 0.72] | 1.65 | -0.351 | -0.357 | 456 (27%) | 23.6 / 24.8 | 0.66 | -1.17 | 12.0 | 6,780 / 28,948 / 142,161 | -1,422 / -30,398 | -0.61 | -1.00/0.07 | 0.36/-1.99/0.28 | -0.67/-0.26 | 0.69 | False | DEAD |
| ABS_w60_g1 | EM | -0.493 [-1.54, 0.53] | 1.46 | -0.275 | -2.517 | 303 (21%) | 1.2 / 4.8 | 0.46 | -3.66 | 12.0 | 6,981 / 32,237 / 154,272 | -1,221 / -18,288 | -0.57 | -0.41/-0.57 | 0.08/-0.30/-1.21 | -0.57/-0.42 | 0.49 | True | DEAD |
| SESSEND_LONDON_x30 | EM | -0.500 [-1.06, 0.07] | 0.79 | -0.780 | -0.591 | 92 (6%) | -32.8 / -24.4 | 0.28 | -8.48 | 12.0 | 6,769 / 33,652 / 160,559 | -1,432 / -12,000 | -0.52 | -0.25/-0.73 | 0.04/-1.55/0.00 | -0.98/-0.10 | 0.04 | True | DEAD |
| ABS_w60_g0 | EM | -0.550 [-1.63, 0.64] | 1.66 | -0.332 | -3.156 | 382 (26%) | 5.3 / 9.0 | 0.51 | -3.70 | 12.0 | 7,352 / 32,211 / 150,622 | -849 / -21,938 | -0.66 | -0.43/-0.66 | 0.06/-0.10/-1.53 | -0.14/-0.89 | 0.61 | True | DEAD |
| IMB_t70_w60_g1 | EM | -0.752 [-1.98, 0.62] | 1.97 | 0.098 | -1.891 | 602 (36%) | -14.6 / -12.5 | 0.35 | -2.13 | 12.0 | 6,576 / 28,488 / 138,964 | -1,626 / -33,596 | -0.87 | -0.54/-0.95 | -1.68/-0.33/-0.29 | -1.49/-0.14 | 0.60 | True | DEAD |
| IMB_t70_w60_g0 | EM | -0.755 [-2.11, 0.81] | 2.11 | -0.169 | -3.609 | 675 (42%) | -9.3 / -6.7 | 0.40 | -2.56 | 12.0 | 6,913 / 28,054 / 133,796 | -1,289 / -38,763 | -0.90 | -0.74/-0.77 | -2.04/0.39/-0.65 | -1.31/-0.30 | 0.72 | True | DEAD |
| ABS_w30_g1 | EM | -1.125 [-2.73, 0.47] | 2.32 | -0.219 | -2.064 | 746 (46%) | -0.9 / 1.3 | 0.46 | -2.24 | 12.0 | 4,883 / 28,346 / 143,789 | -3,318 / -28,770 | -1.32 | -0.61/-1.61 | 0.52/-2.77/-1.08 | -1.69/-0.65 | 0.58 | True | DEAD |
| IMB_t70_w30_g0 | EM | -1.242 [-3.22, 0.92] | 2.99 | -2.114 | -2.104 | 1250 (72%) | -4.0 / -2.3 | 0.44 | -1.72 | 12.0 | 4,984 / 23,292 / 208,153 | -3,217 / +35,594 | -1.54 | -1.73/-0.79 | -2.63/-1.22/0.03 | -2.84/0.09 | 0.93 | True | DEAD |
| ABS_w30_g0 | EM | -1.312 [-3.04, 0.51] | 2.61 | -0.511 | -3.603 | 914 (56%) | 5.2 / 7.7 | 0.52 | -2.50 | 12.0 | 4,751 / 27,631 / 154,148 | -3,450 / -18,412 | -1.58 | -0.65/-1.93 | 0.17/-2.43/-1.62 | -2.10/-0.66 | 0.66 | True | DEAD |
| VOLCOL_f25_h20 | EM | -1.337 [-2.87, 0.34] | 2.24 | -1.425 | -1.118 | 680 (40%) | -0.7 / 1.9 | 0.46 | -2.64 | 12.0 | 5,091 / 29,071 / 243,328 | -3,110 / +70,768 | -1.51 | -1.81/-0.89 | -3.24/-0.99/0.10 | -1.77/-0.98 | 0.38 | True | DEAD |
| IMB_t70_w30_g1 | EM | -1.445 [-3.27, 0.57] | 2.78 | -2.093 | -1.140 | 1108 (63%) | -10.9 / -8.9 | 0.38 | -1.97 | 12.0 | 4,203 / 25,720 / 224,782 | -3,998 / +52,222 | -1.68 | -1.73/-1.18 | -2.13/-2.52/0.22 | -3.41/0.18 | 0.75 | True | DEAD |
| VOLCOL_f25_h10 | EM | -1.583 [-3.25, 0.04] | 2.32 | -1.844 | -1.227 | 710 (41%) | -0.7 / 2.4 | 0.46 | -3.02 | 12.0 | 4,734 / 28,625 / 246,777 | -3,467 / +74,218 | -1.77 | -2.24/-0.97 | -3.65/-1.31/0.08 | -2.36/-0.94 | 0.31 | True | DEAD |
| VOLCOL_f40_h20 | EM | -1.638 [-3.74, 0.50] | 3.05 | -1.952 | -3.395 | 1152 (66%) | -0.8 / 1.7 | 0.48 | -2.50 | 12.0 | 4,257 / 23,828 / 194,752 | -3,944 / +22,193 | -1.94 | -1.00/-2.24 | -2.64/-0.43/-1.85 | -2.36/-1.04 | 0.74 | True | DEAD |
| IMB_t60_w30_g0 | EM | -1.968 [-4.30, 0.44] | 3.45 | -2.389 | -2.601 | 1646 (93%) | -1.2 / 0.7 | 0.48 | -1.86 | 12.0 | 3,007 / 17,137 / 139,706 | -5,194 / -32,853 | -2.40 | -1.98/-1.96 | -1.95/-3.18/-0.84 | -2.87/-1.22 | 1.00 | True | DEAD |


## 5. The two leads: HM exits on a faster-book flip
HM OPP_EM (HM position closed at market when the 5-min EMA 30/50 cross signals the opposite side): WF +0.415 pts/trade [-0.02, +0.86] (MDE 0.64), PRE +0.37, HOLD +0.449, 2023-04..24-01 +0.059; long +0.44 / short +0.39; 848 cuts (13.4% of HM trades), cuts would have hit target 27% (base 50%): the flip really does identify a worse-than-average continuation; EV per cut +2.70 pts; d vs base +$7.1k/wk (14-lot HM family, weekly SD basis), maxDD -$85k; placebo rank vs same-count random timing 1.00 and vs the best-of-28 null 0.993; 2x cost +0.44. OPP_SM on HM: +0.28 [-0.13, +0.74], HOLD +0.29, span -0.16 (CI includes 0), d +$2.9k/wk, maxDD -$82k, rank vs best-of-28 0.983. Why DEAD: the paired CI includes 0 (MDE 0.6, so the effect is about 0.65 x MDE) and the neighbours OPP_KB (3-min Keltner flips, -0.90) and OPP_ANY (-0.94) are negative, so `neighbours_agree` fails: two conditions, not one. Classified LEAD (a one-sentence mechanism, five consistent windows, passes the placebo, fails the CI and one neighbour). The same exits on ST are ~0 (OPP_SM -0.09, OPP_EM -0.02, MDE 0.5), on SM -0.55 (OPP_EM), and the KB flips are negative everywhere (-0.9 HM, -1.2 ST, -1.8 SM, -2.0 EM). Not registered in PAPER-ALL (V2: only CANDIDATE/PASS). Next test that would resolve it: pool HM OPP_EM/SM across a second window (needs 2.5x the pairs) - a 2026-11+ forward look.

## 5b. Direct L2 replay (SO2 standard, status at report time)
Rows prepared for the PRE-rule candidates that were also WF/holdout-positive or near it (HM OPP_EM 848 cuts, HM OPP_SM 799, HM SESSEND_LONDON_x45 136; EM DIV_w30 and SM SESSEND_ASIA_x45 were prepared and dropped from the run after their WF/holdout signs failed): for each cut trade the base (uncut) trade and the same trade with a market flatten at decision + 400 ms are replayed on the real mbp-10 book (exec_engine_l2, prop queue model, EM and 2-s slice arms, XJ3 stop-join on stops). Driver `l2vast/ds3/code/g3/serial.py` (one worker at a time, MemAvailable >= 36 GB gate; the first launch with two workers was cut to one by me within 2 minutes when available memory fell to 14 GB), outputs `/mnt/l2/l2vast/ds3_g3/K<cell>_{B,C}/`, aggregator `direct_cmp.py`. The box is oversubscribed (load ~40; a monthly worker takes > 70 min): **at report time month 2026-07 is still running, so no direct number exists yet; this section is PENDING.** The DEAD/LEAD verdicts are screen-basis (MAPPED, live cost deltas) and are flagged as such in every row (`exec_status`). Nothing here depends on the direct replay except confirming the 0.995-pt market-exit cost assumed for the cut leg; a 1-pt error in that cost moves the HM OPP_EM effect by 0.13 pts/trade (13% cut share x 1 pt) and would not change the verdict.

## 6. Re-entry after a TH cut (sequence level, per-trade knock-on included)
A cut frees the book, so later raw signals that were blocked by the busy gate are taken: with the live control the sequence grows from 8,593 to 13,372 KB trades (+6,139 new, 1,360 base entries displaced) and from 14,620 to 21,872 on ST+HM; the new trades earn +0.6 to +0.8 pts each (mapped), i.e. nearly nothing, so the knock-on does not rescue the cut. 'ON' = the live behaviour (re-enter on the next signal); 'OFF' = same-direction signals within r min of a cut are skipped.

| cell | family | seq trades | new (knock-on) | dropped | knock-on mean P/trade | WF d mean $/wk | d SD | d maxDD | HOLD d mean |
|--|--|--|--|--|--|--|--|--|--|
| TH_LIVE_seq_on | A | 21872 | 8484 | 1232 | 0.77 | -12,509 | -7,979 | +157,374 | -11,486 |
| TH_LIVE_seq_cool10 | A | 20552 | 7437 | 1505 | 0.61 | -14,625 | -7,525 | +72,770 | -9,664 |
| TH_LIVE_seq_cool30 | A | 18771 | 6408 | 2257 | 0.39 | -19,346 | -12,819 | +102,196 | -17,354 |
| TH_LIVE_seq_on | KB | 13372 | 6139 | 1360 | 0.60 | -7,217 | -9,832 | -24,626 | +1,565 |
| TH_LIVE_seq_cool10 | KB | 12765 | 5639 | 1467 | 0.68 | -5,413 | -11,697 | -63,977 | +32 |
| TH_LIVE_seq_cool30 | KB | 11724 | 4925 | 1794 | 0.75 | -6,220 | -12,408 | +18,619 | +1,710 |
| TH_LIVE_seq_on | SM | 2681 | 293 | 9 | -0.96 | -4,601 | -5,782 | +17,057 | -2,039 |
| TH_LIVE_seq_cool10 | SM | 2681 | 293 | 9 | -0.96 | -4,601 | -5,782 | +17,057 | -2,039 |
| TH_LIVE_seq_cool30 | SM | 2674 | 288 | 11 | -1.74 | -4,926 | -5,858 | +34,978 | -2,203 |
| TH_LIVE_seq_on | EM | 2809 | 482 | 8 | -0.66 | -4,703 | -4,129 | +47,015 | -5,529 |
| TH_LIVE_seq_cool10 | EM | 2809 | 482 | 8 | -0.67 | -4,703 | -4,129 | +47,015 | -5,529 |
| TH_LIVE_seq_cool30 | EM | 2799 | 473 | 9 | -0.71 | -4,689 | -4,220 | +47,015 | -5,630 |
| DIV_w30_seq_on | EM | 2462 | 134 | 7 | 2.91 | +1,506 | -3,404 | -28,352 | +115 |
| DIV_w30_seq_cool10 | EM | 2443 | 121 | 13 | 3.82 | +1,456 | -3,416 | -24,884 | +106 |
| DIV_w30_seq_cool30 | EM | 2439 | 120 | 16 | 4.98 | +1,566 | -3,174 | -24,884 | +51 |
| NONE_seq | EM | 2335 | 0 | 0 | - | +0 | +0 | +0 | +0 |

Reading (WF d vs the no-TH base): no re-entry setting turns the live cut positive. ST+HM: ON -$12.5k/wk, OFF10 -$14.6k, OFF30 -$19.3k (maxDD +$157k / +$73k / +$102k worse than base); KB: ON -$7.2k, OFF10 -$5.4k (the least bad, maxDD -$64k), OFF30 -$6.2k; so cooling down trims exposure, not edge; SM/EM never signal within 10 min of a cut (r=10 identical to ON). For the one cut rule that was not negative (EM DIV_w30, not significant), re-entry on/off changes nothing (+$1.5k/wk either way).

## 7. Group findings
* **Tape imbalance (IMB, 40 rows), absorption (ABS, 20), delta divergence (DIV, 10)**: 0 of 70 rows have a positive significant effect (best EM DIV_w30 +0.15, CI -1.3..+1.7, holdout -0.37, span -1.40). The thresholds as prescribed are met on 20-92% of trades (cut share median 0.68 for IMB), so they are effectively time exits that pay 1 pt and forfeit the target 40-67% of the time. Higher thresholds / the loss gate reduce the share (IMB t70 w60 g1: 27%) but also stay negative (-0.9..-1.9). MDE 1.0-2.3.
* **VOLCOL (20 rows)**: negative on every entry (-0.75..-2.64): dead markets in the trade are not a sign of failing trades, and exits there pay the cost with no information.
* **OPP (13 rows)**: only the HM leads above; KB-flips and ANY are negative.
* **SESSEND (30 rows)**: 16 of 30 nominally positive but all within +/-0.1 pt (median +0.002), MDE 0.19: no detectable effect; the NY window (16:25-16:55) triggers on <1% of trades because the flatten arrives first, Asia/London 1-5%. London x30 is negative on all five entries (-0.25..-0.50, MDE 0.35-0.85), i.e. tightening before the London open is at best a mild cost.
* **REENTRY**: section 6.

## 8. Equal-risk / marginal-Sharpe columns (user addendum)
These cells never add risk per trade (exits only, never more lots), so equal-lots and equal-risk comparisons are the cell against its own base: rows carry `equal_risk` (pnl_wk_equal_lots, pnl_wk_equal_risk scaled by base SD / cell SD, lots_equal_risk, capacity_lots_zero_mean = None, ds3_marginal_sharpe = None with the reason). The shared helper equal_risk.py re-reads the holdout through ds3_addbook, so it was not run on rows that are not candidate books. No row is DEAD for earning less than ST at equal lots; every verdict is the paired test against the cell's own base.

## 9. Registrations and next steps
No PASS or CANDIDATE: nothing registered in `paper_all/ds3_THG3_*`. LEAD tier: HM OPP_EM, HM OPP_SM (`G3_OPP_EM__HM`, `G3_OPP_SM__HM`). No 3x3 widening (no PASS). G4 combination inputs from G3: none beyond the two HM leads; tape/vol-collapse/session-end/REENTRY should not enter the fractional factorial.
