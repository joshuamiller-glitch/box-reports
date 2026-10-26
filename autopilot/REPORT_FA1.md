# REPORT FA1 - program-wide false-discovery audit (analysis only, no new strategy search)

Written 2026-10-17 by research worker FA. No gate was changed, no cell was re-run for selection, nothing was purchased. Inputs: all 448 test reports in outputs/autopilot/REPORT_*.md (31 diagnostics, assembly, extension and void reports excluded), PREREG_AUTOPILOT.md, GAPMAP.csv, CANDIDATES.md, LEDGER.md (the 10-16 accounting), FORWARD.md, and the 38,377 full-coverage books in outputs/library/. Code: code/census/night_ins/ap_fa1_mc.py, ap_fa_write.py, ap_fa_reports.py; tables: outputs/autopilot/FA1_*.csv.

## 0. Headline (read this first)

1. Gate 3 (uplift >= +0.10 weekly Sharpe on clean AND H1 AND H2 at 20% share) is passed at or below the rate chance alone predicts. Across **2,977 clean-selected cell rows in 83 reports** the cell-level H1+H2 replication rate is **5.1%** against **8.2%** for a zero-edge sleeve (Monte Carlo on the real pair weeks); all-three-span passes are 79 cells (2.7%) against 5.9% expected for a zero-edge cell selected by the SW rule. Mean uplift of the selected cells is **+0.07 clean, -0.17 H1, -0.16 H2**: the clean-span selection does not carry out of sample on average.
2. Over the whole library (**38,377 stored cells, no selection**) **590 cells pass gate 3 mechanically against 557 expected under a sign-flip (zero-edge) null** (1.54% vs 1.45%). The whole excess (+33) sits in the 5-min NQ trend family T3-S1 (182 vs 75) and WT (16 vs 6); most other families are at or below chance.
3. Program-wide, the **expected number of false gate-3 cells is 40 to 163** (central ~100) against **111 observed**. The observed count is inside the chance range. Gate 3 therefore carries almost no evidence; what separates a real lead from a false one is gates 4-6 and out-of-sample live weeks.
4. Expected false **LEAD** (gate 3 + own null + bootstrap) and **FOUND-PENDING** (all seven gates, replication short): see section 5. The range is wide (LEAD 1 to 43, FOUND-PENDING 0.06 to 11) because the dominant uncertainty is how often the timing-destroyed own-null passes a no-edge cell (nominal 5%, realised 15 of 31 = 48% in C7-P1). Observed: 4 distinct FOUND-PENDING signals (ES dip-buy, K4 family, FVG family, SW4 RTY) and 53 to 72 distinct signal clusters among the library books labelled LEAD/FOUND-PENDING (FA2; an upper bound for LEAD in the section-5 sense, because the label includes books such as the W4 Monday drift that fail the own-null or bootstrap gate). **FOUND = 0 is unchanged and is the honest reading: at the lenient end of the chance range every FOUND-PENDING could be a false discovery; only the FVG family has a family-level null (109-cell depth-permutation, p95 2.67 vs real 4.00) that it clears outright.**
5. 133 of 448 test reports (30%) contain none of the calibration keywords (timing-destroyed / replicates / family null / permutation / selection-aware); these are the pair-side modifier and single-carried-cell reports. For them the only calibration is the program-wide Monte Carlo in section 3, not a report-specific one.

## 1. Method and what is counted

* **Unit.** A *cell* is one pre-registered parameter combination whose result was reported. *Screened / read* means a cell whose uplift was read on H1 and H2 after clean-only selection (the report's "selected cells", or 1 for a single carried cell). Gate-3 pass = uplift >= +0.10 on each of clean, H1, H2 at the 20% additive share (or the report's own statement of that count).
* **Counts come from the report text** (verdict line, "N cells", "cells in grid", "N selected cells", GAPMAP notes, cell tables). They are parsed, not curated: 68 reports state no grid size and are counted as 1 cell, so the cell total is a **lower bound**; the SW grid size is the sum of the section-1 table. Pre-autopilot programs (B3-B10, retired 1-s harness, about 163,000 engines) are excluded as void, as in LEDGER.md. D1/D2 (479+542 cells), E9 (37 candidates), T3/T4/V5 (T3-S1 8,054 series) are in LEDGER.md and not re-tallied here.
* **Chance model.** Zero-mean sleeves scaled to 20% of the pair's clean weekly SD, added to the real pair weeks (clean 104, H1 28, H2 35 weeks, Sharpe = mean/SD x sqrt(52)), 200,000 draws (normal; t3 gives the same). Per-cell gate-3 pass: unselected 1.54%; H1 and H2 both >= 0.10: 8.25%; clean-selected by the SW rule (both clean halves positive, top 10 of 48 by clean Sharpe): **5.88% per selected cell**, P(at least one pass in a 48-cell grid) 44% (independent cells) to 21% (common factor rho 0.5). Random day-skip/halve modifiers of the pair: 1.17% unselected, 6.30% H1+H2. The expectation of a count is linear in the number of cells whatever their correlation; correlation only widens the spread.

## 2. Table A - every batch since the autopilot began

| batch | reports | pre-reg cells (parsed) | reports w/o parseable grid | cells read on pair window (screened) | gate-3 passes (cells) | reports with >=1 | E[gate-3] if unselected (1.5%/cell) | E[gate-3] if clean-selected (5.9-8%/cell) | reports with no calibration keywords |
|---|---|---|---|---|---|---|---|---|---|
| 01 SW gap sweeps (SW1-SW30) | 30.0 | 25,584.0 | 0.000 | 1,046.0 | 52.0 | 17.0 | 16.1 | 61.5 | 0.000 |
| 02 ICT study | 1.000 | 4,064.0 | 0.000 | 1.000 | 1.000 | 1.000 | 0.015 | 0.080 | 0.000 |
| 03 Pullback study | 1.000 | 3,280.0 | 0.000 | 1.000 | 1.000 | 1.000 | 0.015 | 0.080 | 0.000 |
| 04 Drivers / basket / options | 4.000 | 1,084.0 | 0.000 | 4.000 | 0.000 | 0.000 | 0.062 | 0.320 | 1.000 |
| 05 B-capacity instrument grids (B1,B4,B7,B10,B11) | 7.000 | 1,368.0 | 0.000 | 246.0 | 12.0 | 5.000 | 3.786 | 14.5 | 0.000 |
| 06 B pair-side rule changes (B8-B19) | 10.0 | 86.0 | 2.000 | 10.0 | 1.000 | 1.000 | 0.154 | 0.800 | 5.000 |
| 07 Cycles C1-C11 | 22.0 | 4,100.0 | 5.000 | 117.0 | 2.000 | 2.000 | 1.801 | 9.360 | 11.0 |
| 08 B2356 worker batches (N,R-Z,B2-B6) | 75.0 | 998.0 | 3.000 | 77.0 | 1.000 | 1.000 | 1.185 | 6.160 | 0.000 |
| 09 Q-series (B2356 Q1-Q25) | 43.0 | 6,593.0 | 2.000 | 847.0 | 13.0 | 11.0 | 13.0 | 49.8 | 3.000 |
| 10 A/D3x/E alt-engine, flow-filter, evidence | 22.0 | 120.0 | 18.0 | 22.0 | 1.000 | 1.000 | 0.339 | 1.760 | 21.0 |
| 11 G (GAPMAP D00-D11 pair conditioning) | 23.0 | 495.0 | 1.000 | 23.0 | 1.000 | 1.000 | 0.354 | 1.840 | 10.0 |
| 12 H (D06-D11 pair mgmt) | 19.0 | 208.0 | 3.000 | 19.0 | 1.000 | 1.000 | 0.292 | 1.520 | 12.0 |
| 13 I (event/flow signals) | 17.0 | 257.0 | 3.000 | 17.0 | 1.000 | 1.000 | 0.262 | 1.360 | 3.000 |
| 14 J (COT, events, pair mgmt) | 28.0 | 379.0 | 3.000 | 28.0 | 4.000 | 4.000 | 0.431 | 2.240 | 15.0 |
| 15 K (GBM, exits, backlog2 B/C/K) | 34.0 | 264.0 | 16.0 | 34.0 | 4.000 | 4.000 | 0.523 | 2.720 | 16.0 |
| 16 L (backlog2 L; GC fade) | 13.0 | 480.0 | 0.000 | 12.0 | 1.000 | 1.000 | 0.185 | 0.960 | 0.000 |
| 17 P/PA/PX/PY/PZ (pair tilts, near-miss cures) | 36.0 | 3,542.0 | 1.000 | 36.0 | 0.000 | 0.000 | 0.554 | 2.880 | 19.0 |
| 18 RU-RZ (K4 deepening, FVG structural) | 55.0 | 553.0 | 10.0 | 55.0 | 22.0 | 22.0 | 0.846 | 4.400 | 17.0 |
| 19 WT / other | 2.000 | 32.0 | 1.000 | 2.000 | 1.000 | 1.000 | 0.031 | 0.160 | 0.000 |
| 20 other | 6.000 | 64.0 | 0.000 | 6.000 | 0.000 | 0.000 | 0.092 | 0.480 | 0.000 |

Totals: 448 reports, 53,551 parsed cells (lower bound), 2,603 cells read on the pair window, 119 report-level gate-3 passes in 75 reports (report-level counts use each report's own LEAD tally where it is the only count; the cell-table count of section 3 is the cleaner figure: 111).

Reading Table A. Group 18 (RU-RZ) is almost one signal repeated: the K4 daily GBM and its variants, the IBS/RSI dip-buy variants (identical +0.19/+1.02/+0.19 triples in I9, RW9, RX2, RX3) and the FVG retrace across markets; its 22 "passes" are about 4 independent signals. Group 09 and 01 are sweeps where passes are near chance. Groups 10-17 are one carried cell per grid.

## 3. Calibration that exists in the data

### 3a. Pooled cell-level out-of-sample replication (2,977 rows, 83 reports, Q18 void excluded)

| statistic | observed | zero-edge expectation |
|---|---|---|
| clean uplift >= +0.10 | 45.5% | selection-driven (not a test) |
| H1 uplift >= +0.10 | 24.1% | 29.8% |
| H2 uplift >= +0.10 | 21.2% | 27.6% |
| H1 and H2 both >= +0.10 | 5.1% | 8.2% |
| all three (gate 3) | 79 cells = 2.7% | 5.9% (SW rule), 1.5% unselected |
| mean uplift clean / H1 / H2 | +0.070 / -0.171 / -0.163 | clean positive by selection; OOS about 0 (a zero-mean sleeve slightly lowers the pair Sharpe) |

Carried single cells (365 reports not in a cell table; 264 with a parseable clean/H1/H2 triple): 32 pass all three (12%), 48 pass H1 and H2 (18%); the 32 collapse to about 13 independent signals (K4 family 11-13 reports, IBS/RSI dip-buy variants 5-6, FVG retrace on GC/CL/basket 3, plus 8 single ideas), about 5% of 264, which is at or below chance (8%).

### 3b. Clean-span structure beyond chance (reports' own timing-destroyed replicates of the whole grid)

330 instrument-grids in 79 reports (SW, Q, B1/B4/B7, K) carry a "p(top)" test (100 timing-destroyed replicates of the whole selection per grid). **69 of 330 (21%) have p(top) <= 0.05 versus 5% expected; 89 (27%) <= 0.10.** The count test p(count) <= 0.05 in 136 of 457 (30%). So the clean span (2023-08..2025-07) does contain more year-consistent structure than random entries produce (about 4x the nominal rate on NQ 11/42, RTY 11/48, BTC 8/42, ES 7/47; ZN 1/45), but that structure is exactly what fails to carry into H1/H2 (3a). Reports overlap (the Q and SW sweeps reuse the same markets), so the grids are not independent.

### 3c. The whole library, mechanical test (no selection, no report involved)

Every stored book with full 2023-08..2026-10 coverage (38,377) was scaled to 20% of the pair's clean weekly SD and scored on the three spans. Observed gate-3 passes **590**; sign-flip null (each week's sign randomised, 20 replicates, same distribution and zero mean) **557**; iid-normal reference rate 1.54%. A mean-kept week shuffle (keeps any edge, destroys the pair relation) would give 3.58% = 1375 cells, i.e. a library of real stable edges would pass more than the observed 1.54%. Largest families (observed vs sign-flip expected): T3S1_G_G_v1 182 vs 75, ICT 56 vs 44, V5P2 23 vs 32, WT432 16 vs 6, C11DIP 16 vs 1, T3S1_L 16 vs 1, T4B 16 vs 2, B1leg_BTC 15 vs 2. Per-family file: FA1_library_gate3_by_family.csv.

### 3d. Report-specific calibrations (where they exist)

| program | calibration in the report | number |
|---|---|---|
| V5-P2 (2,016 5-min cells, top 20) | null gives 1.14 passes per 20 selected; real 1 | P(null >= real) = 0.69 |
| X1-REP (compression breakout) | 210 null replicates of the pipeline | 0 passes (<= 1.4%) |
| T3-S1 (8,054 series) | timing-destroyed books through the same screen | 4 of 5,480 vs 8 of 8,054 real (5.9 expected) |
| C5/C7/C10 L0 year-consistency (12,500+ cells) | replicates per grid | 362 real cells vs 201 expected (NQ 164 vs 85, ES 76 vs 51, CL 65 vs 28); 0 of 113 selected carry into the pair window |
| SW / Q / B1,B4,B7 | p(top) per instrument-grid | 69 of 330 at <= 0.05 (3b) |
| ICT (4,064 cells) | 30 random-level replicates of the grid; SCREEN 439 real vs 261 +- 25 | C2 FVG 122 vs 6.7; expected cells passing SCREEN and both nulls by chance 0.65 (<= 12.9 if dependent); actual 68, 54 in the FVG cluster |
| PULLBACK (3,280 cells, 12 finalists) | gate-3 chance for 12 finalists | 0.33 expected, 0 observed |
| DRIVERS (256 cells) | gate-3-style bar | about 13 into stage 2 by chance; 3 advanced, 2 reversed sign |
| FVG family (FV8) | 109-cell depth-permutation family null | p95 2.67 vs real 4.00 (clears) |
| K4v2 | selection-aware null (100 random-entry replicates of the 32-cell selection) | real best 1.30 vs replicate median 1.22 (beats 55%); RY7 DSR 0.64 (N=145) to 0.99 (N_eff=4) |
| RW12P | selection-aware null | 1.32 vs 1.81 (73% of the clean uplift is selection) |
| WT-10 (432 cells) | family null | 0.32 vs 0.373 (86% selection-explained) |
| ES dip-buy (64 cells) | selection-aware rank | 70% |
| SW4 RTY | timing-destroyed replicates (RTY grid) | p(top) = 0.00, real best 2.165 vs replicate p95 2.116 (marginal) |

Reports **without** a calibration: 133 of 448 (groups 04, 06, 07, 10, 11, 12, 14, 15, 17, 18 are mostly uncalibrated: single carried cells judged only by the shared gate set and, from RX onward, by bootstrap and own-null on the cell). For them the program-wide Monte Carlo is the only available benchmark and it is not report-specific.

## 4. Per-lead false-discovery view (21 FORWARD.md leads, in-sample window 167 weeks)

One-sided z of the frozen (selection-deflated) mean weekly uplift against its block-bootstrap SE, Benjamini-Hochberg q over the 21 leads, and Bonferroni thresholds for the effective numbers of FA2.

| lead | z (block-bootstrap) | one-sided p | BH q (21 leads) |
|---|---|---|---|
| FVG_E1 | 7.091 | 0.000 | 0.000 |
| FVG_IMP3 | 6.534 | 0.000 | 0.000 |
| FVG_P1 | 5.751 | 0.000 | 0.000 |
| RW12P | 3.817 | 0.000 | 0.000 |
| BTCWT | 3.794 | 0.000 | 0.000 |
| ESDIP | 3.750 | 0.000 | 0.000 |
| SW4 | 2.814 | 0.002 | 0.007 |
| L93 | 2.761 | 0.003 | 0.008 |
| RX5 | 2.667 | 0.004 | 0.009 |
| K4V2 | 2.392 | 0.008 | 0.018 |
| WT10 | 2.353 | 0.009 | 0.018 |
| SW20 | 2.192 | 0.014 | 0.025 |
| RW5 | 2.124 | 0.017 | 0.027 |
| Q20 | 2.040 | 0.021 | 0.031 |
| H11B | 1.819 | 0.034 | 0.048 |
| W6FADE | 1.580 | 0.057 | 0.075 |
| Z3FADE | 1.523 | 0.064 | 0.079 |
| Q12 | 1.398 | 0.081 | 0.094 |
| T1B | 1.255 | 0.105 | 0.116 |
| Q5ENS | 0.930 | 0.176 | 0.185 |
| PERS30 | 0.311 | 0.378 | 0.378 |

Bonferroni one-sided p thresholds: 0.05/21 = 2.4e-3 (z >= 2.82); 0.05/14 effective leads = 3.6e-3 (z >= 2.69); 0.05/2,464 trial clusters = 2.0e-5 (z >= 4.1); 0.05/7,912 = 6.3e-6 (z >= 4.3). Against the trial-cluster thresholds **only the three FVG leads clear (z 5.8, 6.5, 7.1)**; the ES dip-buy (z 3.75), BTC WT (3.79) and RW12P (3.82) do not, and everything else needs live weeks. These z are in-sample on the window that includes the selection span (shrunk for WT10/K4/RW12P only), so they are optimistic.

## 5. Program-wide expected false discoveries at the stated gates

Chain: E[gate 3] x P(own null p95 | no edge) x P(bootstrap 90% lower bound > 0 | passes) = E[LEAD]; x P(plateau >= 75% and 2x slippage and worst-decile corr <= +0.30 and NT8 spec | LEAD) = E[FOUND-PENDING]. Inputs: E[gate 3] 40 (unselected cells) to 163 (clean-selected cells) from section 3 (MC rates x 2,603 cells read); P(own null) 5% nominal, 20%, 48% (C7-P1 realised: 15 of 31 selected cells rank >= 0.95); P(bootstrap) 0.55 (half of the gate-3 passers have a positive lower bound); P(rest) 5%, 12%, 25% (V5-P2: 2.8% of 216 neighbours reach +0.10; X1-REP 0 of 210; plateau gate for a no-edge cell is hard but not impossible).

| assumption | g3 chance basis | E gate-3 | E LEAD | E FOUND-PENDING |
|---|---|---|---|---|
| strict (nominal 5% own-null, plateau/2x/replication pass 5%) | unselected 1.5%/cell | 40.1 | 1.102 | 0.055 |
| strict (nominal 5% own-null, plateau/2x/replication pass 5%) | clean-selected 6-8%/cell | 162.9 | 4.480 | 0.224 |
| central (own-null 20%, rest 12%) | unselected 1.5%/cell | 40.1 | 4.407 | 0.529 |
| central (own-null 20%, rest 12%) | clean-selected 6-8%/cell | 162.9 | 17.9 | 2.150 |
| lenient (realised own-null 48%, rest 25%) | unselected 1.5%/cell | 40.1 | 10.6 | 2.644 |
| lenient (realised own-null 48%, rest 25%) | clean-selected 6-8%/cell | 162.9 | 43.0 | 10.8 |

Observed against this: gate-3 cells 111; report-level LEAD labels 65 (K4, dip-buy, FVG and the gap sweeps account for most), registry leads 21 (about 13-14 independent, FA2); FOUND-PENDING-class signals **4** (ES dip-buy C11-DIP, K4 family K4v2/RX7/RY9, FVG family E1/IMP3/P1/RZ9/RZ1, SW4 RTY); FOUND 0.

* **Gate 3: at chance** (111 observed vs 40-163 expected).
* **LEAD: within the lenient chance range, above the strict one** (observed 13-14 independent registry leads, 65 report-level labels vs 1.1-43 expected). The honest statement is that LEAD status alone is not evidence.
* **FOUND-PENDING: 4 signals vs 0.06-10.8 expected** (central 0.5-2.2). P(>= 4 | lambda=0.5) = 0.002; P(>= 4 | lambda=2.2) = 0.18; P(>= 4 | lambda=10.8) > 0.99. So at the nominal null calibration the four are unlikely to be all false; at the realised null calibration they cannot be separated from chance by the gates alone. Family-specific evidence changes this: the FVG family clears a 109-cell depth-permutation family null and has z > 5.7 and DSR ~1.0 for any N (FA2), the ES dip-buy (selection rank 70%, 23 trades), K4 (beats 55% of selection replicates) and SW4 (ERA-negative pre-2023) do not.
* LEDGER.md's 10-16 accounting (E[FOUND-PENDING] about 0.1, upper bound 0.4, L2 6 vs ~10, L3 2 vs ~7) used the lower end of these inputs and ~110 families. It under-counted the cells read (2,603 here, 3,000+ rows including diagnostics) and the realised own-null pass rate. The qualitative conclusion (excess concentrated in 3-4 mechanisms) stands; the quantitative expectations should be read as 0.06-11, not 0.1-0.4.

## 6. Caveats (stated, not softened)

1. Counts are parsed from report text and the two sources disagree in places (report-level LEAD tally vs cell tables); totals are accurate to roughly +-15%, and the cell total is a lower bound.
2. The chance model is zero-edge, independent of the pair, iid weekly. Real nulls have autocorrelation and a common clean-window factor (NQ trend premium, regime), which raises gate-3 chance in correlated families; the program's observed pass rate is below the iid expectation, so the model is not generous to the program.
3. P(own null) is the dominant unknown (5% to 48%). The program has never measured the full-gate pass rate of a no-edge cell directly (only gate 3 in PULLBACK and X1-REP); a direct no-edge calibration of gates 4-7 would pin the FOUND-PENDING expectation down. That is a follow-up, not a new strategy search.
4. Observed LEAD/FOUND-PENDING signals are not independent of the clean-window regime, and H1/H2 are non-virgin for the FVG family. Live weeks (FORWARD.md) remain the only unconditional test.

DONE FA1
