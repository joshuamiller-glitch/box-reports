# REPORT CONTROL - would the gate chain have found ST, HM, WT-10 and the pair? (directive CALIBRATE item 1)

**Short answer.** Run as candidates through the same chain, with a 229-247-cell grid around the live parameters, clean-only selection and H1/H2 read once, the live pair gets the label **LEAD (6 of 7 measured gates; FOUND needs all 7)**: it fails exactly one measured gate, the exact +-25% plateau (60% of neighbours keep 75% of the Sharpe, gate 75%), and passes replication with 2 of 4 (H0 and newest weeks; alternating-month and ES/RTY/YM fail). ST (live) is LEAD (plateau 50%), WT-10 (live) is LEAD (plateau 50%), HM (live) is NO (as a 20% sleeve to ST it adds +0.01 clean). The chain therefore does NOT reject the pair on power grounds on 6 of 7 gates, but it would not have labelled ANY of the four FOUND or FOUND-PENDING: the plateau gate at 75/75 fails for all four, ES/RTY/YM replication and 2013-22 ERA fail for all four, and alternating months fails for all four.

**Caveats (as required).** (1) The pair parameters were chosen on 2023-2026 data, so clean selection around the live cell is in-sample for the live pair and H1/H2 are not virgin for it: the control measures whether the chain passes a book of the pair quality, not whether a search would have found it. (2) Engine: ST, HM and the pair run on the NT8-faithful harness (nt8sim.acct, 1-second bracket path, netting, B11 account rules wk_floor 8); the harness reproduces the live pair exactly from its parameters (clean/H1/H2/all 1.4599/2.8276/2.4840/1.8974 against the asserted 1.46/2.83; 7,361 vs 7,346 trades; daily corr 0.99998). WT runs on the verified WT-10 path (ap_wt_gate / ap_wt_acct; reproduces forward/series/WT10_live.csv). (3) ES/RTY/YM replication and the 2013-22 ERA gate use a 1-minute approximation (ap_ctl_lite.py: same indicator code, bracket scaled by ADR20, stop-first on 1-minute bars, no account locks, no ST/HM netting) because there is no second-resolution data for ES/RTY/YM and none before 2023; the lite NQ pair-window Sharpe is 0.9-1.5 against the harness 1.9-2.0, so those two gates are indicative, not exact. (4) The selection criterion is the clean standalone weekly Sharpe (>= 200 pair-window trades, positive in both clean halves); entry-window variants were only available for ST/HM/PAIR.

## 1. Selection (clean only, 2023-08..2025-07)

| book | cells (eligible) | selected cell | clean Sh | live-cell clean Sh | live cell rank among eligible |
|---|---|---|---|---|---|
| ST | 229 (150) | ST br=60.0 ema=200 mult=2.0 period=120 win=W3 | 1.92 | 1.78 | 3 |
| HM | 229 (138) | HM br=60.0 ema=100 f=17 sl=70 win=W0 | 1.97 | 0.81 | 94 |
| PAIR | 247 (155) | PAIR br=60.0 ema=200 f=20 mult=1.75 period=90 sl=63 win=W0 | 1.82 | 1.46 | 20 |
| WT | 270 (105) | an=10 WT br=60.0 ema=0 exit=X1 m=3.0 tf=10 | 2.17 | 1.99 | 3 |

The chain selected a neighbour of the live cell for ST (window variant W3: entries stop at 14:00), HM (EMA 100, HMA 17/70) and PAIR (ST 90/1.75 with HM 20/63) and an ATR-10 variant of WT. Each book is therefore reported twice: SELECTED (what a search would pass forward) and LIVE (the live cell as a candidate).

## 2. Gate-by-gate: LIVE cell as candidate (pass margin = how far from failing; positive = pass)

| gate | ST (base: live HM) | HM (base: live ST) | WT-10 (base: live pair) | ST+HM pair (empty base) |
|---|---|---|---|---|
| 3 uplift>=+0.10 clean/H1/H2 @20% (pair: standalone Sharpe) | PASS  +0.26/+0.32/+0.28 (margin +0.16) | FAIL  +0.01/+0.17/+0.13 (margin -0.09) | PASS  +0.37/+0.42/+0.28 (margin +0.18) | PASS  +1.46/+2.83/+2.48 (margin +1.36) |
| 3b worst week within share (>= -20%) | PASS  -14.5% (margin +5.51) | PASS  -13.0% (margin +7.00) | PASS  -10.4% (margin +9.58) | PASS  n/a (empty base) |
| 4 own timing-destroyed null p95 (standalone all-in Sharpe, 200 reps) | PASS  real 1.93 vs p95 0.57 (rank 1.00) (margin +1.35) | PASS  real 1.11 vs p95 0.67 (rank 0.99) (margin +0.44) | PASS  real 2.02 vs p95 0.69 (rank 1.00) (margin +1.32) | PASS  real 1.90 vs p95 0.42 (rank 1.00) (margin +1.48) |
| 4b bootstrap 90% CI lower bound > 0 | PASS  [+0.13, +0.44] (margin +0.13) | FAIL  [-0.11, +0.24] (margin -0.11) | PASS  [+0.17, +0.57] (margin +0.17) | PASS  [+1.01, +2.74] (margin +1.01) |
| 5 plateau: >=75% of exact +-25% neighbours keep >=75% of the metric | FAIL  50% of 8 (margin -0.25) | PASS  88% of 8 (margin +0.12) | FAIL  50% of 8 (margin -0.25) | FAIL  60% of 10 (margin -0.15) |
| 5b 2x slippage >= +0.10 each span | PASS  +0.25/+0.30/+0.23 (margin +0.13) | FAIL  -0.03/+0.13/+0.11 (margin -0.13) | PASS  +0.34/+0.41/+0.22 (margin +0.12) | PASS  +0.99/+2.49/+2.37 (margin +0.89) |
| 6 worst-decile corr <= +0.30 | PASS  -0.30 (margin +0.60) | PASS  +0.23 (margin +0.07) | PASS  -0.20 (margin +0.50) | PASS  n/a (empty base) |
| measured gates passed (of 7) | 6/7 | 4/7 | 6/7 | 6/7 |
| replication: H0 standalone weekly Sharpe > 0 (2023-02..07) | PASS +0.47 | FAIL -0.46 | FAIL -0.31 | PASS +0.70 |
| replication: alternating months (read > 0 and >= 50% of selection, both directions) | FAIL sel +0.29 read +0.07; sel +0.39 read +0.09 | FAIL sel +0.19 read +0.03; sel +0.46 read -0.22 | FAIL sel +0.33 read +0.11; sel +0.70 read -0.06 | FAIL sel +2.04 read +0.56; sel +2.20 read +1.25 |
| replication: ES/RTY/YM same cell positive (1-min approximation) | FAIL ES -1.40 RTY -0.46 YM -0.88 (NQ-lite +1.11) | FAIL ES -0.80 RTY -0.95 YM -0.15 (NQ-lite +0.89) | FAIL ES +0.36 RTY -0.03 YM -0.58 (NQ-lite +1.46) | FAIL ES -1.32 RTY -0.81 YM -0.60 (NQ-lite +1.16) |
| replication: newest 4 weeks positive | PASS +46.8k | PASS +25.6k | PASS +5.9k | PASS +101.7k |
| replications passed (of 4; need 2) | 2/4 | 1/4 | 1/4 | 2/4 |
| 2013-22 ERA flag (lite; weekly Sharpe gross / fixed / ADR-scaled cost) | negative pre-2023 (-0.05 / -1.89 / -0.55) | gross-positive, cost-negative pre-2023 (+0.21 / -1.46 / -0.24) | negative pre-2023 (-0.68 / -1.79 / -0.98) | gross-positive, cost-negative pre-2023 (+0.08 / -1.96 / -0.47) |
| executability | executable (NT8 market entry + OCO bracket; own account for WT) | executable (NT8 market entry + OCO bracket; own account for WT) | executable (NT8 market entry + OCO bracket; own account for WT) | executable (live strategy) |
| **label the pipeline would assign** | **LEAD** | **NO** | **LEAD** | **LEAD** |

## 3. Gate-by-gate: SELECTED cell (pass margin = how far from failing; positive = pass)

| gate | ST (base: live HM) | HM (base: live ST) | WT-10 (base: live pair) | ST+HM pair (empty base) |
|---|---|---|---|---|
| 3 uplift>=+0.10 clean/H1/H2 @20% (pair: standalone Sharpe) | PASS  +0.29/+0.37/+0.23 (margin +0.13) | PASS  +0.26/+0.15/+0.36 (margin +0.05) | FAIL  +0.43/+0.24/+0.01 (margin -0.09) | PASS  +1.82/+2.31/+1.73 (margin +1.63) |
| 3b worst week within share (>= -20%) | PASS  -12.9% (margin +7.06) | PASS  -9.6% (margin +10.44) | FAIL  -25.2% (margin -5.22) | PASS  n/a (empty base) |
| 4 own timing-destroyed null p95 (standalone all-in Sharpe, 200 reps) | PASS  real 1.99 vs p95 0.57 (rank 1.00) (margin +1.42) | PASS  real 2.08 vs p95 0.47 (rank 1.00) (margin +1.60) | PASS  real 1.65 vs p95 0.51 (rank 1.00) (margin +1.14) | PASS  real 1.87 vs p95 0.26 (rank 1.00) (margin +1.61) |
| 4b bootstrap 90% CI lower bound > 0 | PASS  [+0.14, +0.45] (margin +0.14) | PASS  [+0.10, +0.43] (margin +0.10) | PASS  [+0.13, +0.52] (margin +0.13) | PASS  [+0.99, +2.71] (margin +0.99) |
| 5 plateau: >=75% of exact +-25% neighbours keep >=75% of the metric | FAIL  50% of 8 (margin -0.25) | FAIL  62% of 8 (margin -0.12) | FAIL  50% of 8 (margin -0.25) | FAIL  70% of 10 (margin -0.05) |
| 5b 2x slippage >= +0.10 each span | PASS  +0.27/+0.34/+0.18 (margin +0.08) | PASS  +0.24/+0.12/+0.32 (margin +0.02) | FAIL  +0.39/+0.21/-0.04 (margin -0.14) | PASS  +1.44/+1.44/+1.52 (margin +1.34) |
| 6 worst-decile corr <= +0.30 | PASS  -0.25 (margin +0.55) | FAIL  +0.38 (margin -0.08) | PASS  -0.17 (margin +0.47) | PASS  n/a (empty base) |
| measured gates passed (of 7) | 6/7 | 5/7 | 3/7 | 6/7 |
| replication: H0 standalone weekly Sharpe > 0 (2023-02..07) | PASS +0.00 | FAIL -3.47 | FAIL -0.49 | FAIL -0.85 |
| replication: alternating months (read > 0 and >= 50% of selection, both directions) | FAIL sel +0.29 read +0.07; sel +0.39 read +0.09 | FAIL sel +0.19 read +0.03; sel +0.46 read -0.22 | FAIL sel +0.33 read +0.11; sel +0.70 read -0.06 | FAIL sel +2.04 read +0.56; sel +2.20 read +1.25 |
| replication: ES/RTY/YM same cell positive (1-min approximation) | FAIL ES -1.40 RTY -0.46 YM -0.88 (NQ-lite +1.11) | FAIL ES +0.08 RTY -1.29 YM -0.18 (NQ-lite +1.04) | FAIL ES -0.24 RTY -0.07 YM -0.25 (NQ-lite +1.31) | FAIL ES -1.28 RTY -0.72 YM -0.35 (NQ-lite +0.98) |
| replication: newest 4 weeks positive | PASS +46.8k | PASS +14.8k | PASS +14.4k | PASS +127.4k |
| replications passed (of 4; need 2) | 2/4 | 1/4 | 1/4 | 1/4 |
| 2013-22 ERA flag (lite; weekly Sharpe gross / fixed / ADR-scaled cost) | negative pre-2023 (-0.05 / -1.89 / -0.55) | gross-positive, cost-negative pre-2023 (+0.39 / -1.23 / -0.05) | gross-positive, cost-negative pre-2023 (+0.11 / -0.97 / -0.18) | gross-positive, cost-negative pre-2023 (+0.12 / -1.89 / -0.43) |
| executability | executable (NT8 market entry + OCO bracket; own account for WT) | executable (NT8 market entry + OCO bracket; own account for WT) | executable (NT8 market entry + OCO bracket; own account for WT) | executable (live strategy) |
| **label the pipeline would assign** | **LEAD** | **LEAD** | **NO** | **LEAD** |

## 4. The live pair: pass margins for item 3 ("the level the pair achieves")

- Gate 3 (standalone, empty base): weekly Sharpe clean/H1/H2/all 1.46/2.83/2.48/1.90: margin over +0.10 is +1.36 at the weakest span (clean).
- Own null: 200 timing-destroyed replicates (same signal counts, random bars, harness + B11 rules), standalone all-in Sharpe p95 0.42, median -0.52; real 1.90, rank 1.00: margin +1.48 Sharpe.
- Bootstrap 90% CI of the all-in Sharpe: [+1.01, +2.74] (lower bound margin +1.01).
- Plateau: 60% of the 10 exact +-25% neighbours keep >= 75% of the Sharpe: FAILS the 75/75 gate by 0.15. Failing neighbours: ST multiplier 2.5 (67%), HM fast 15 (70%), HM slow 69 (61%), bracket 75 pts (39%). Retention of the 10 neighbours: 111%, 94%, 81%, 67%, 70%, 96%, 85%, 61%, 77%, 39% (median 79%, minimum 39%). The level the pair achieves is therefore 60/75 on this definition (6 of 10 neighbours at >= 75%), or 7 of 10 neighbours at >= 70% retention.
- 2x slippage (1 tick/side to 2 ticks/side): standalone Sharpe clean/H1/H2 0.99/2.49/2.37; the clean span loses 0.47 Sharpe (1.46 -> 0.99), margin over +0.10 is +0.89.
- H0 2023-02..07 standalone Sharpe +0.70 (positive, 0.48 of the clean value); newest 4 weeks +$102k at native 8 NQ; alternating months: selection 2.04/2.20, read 0.56/1.25 (one direction below 50% of selection: FAIL); ES/RTY/YM (lite) all negative (-1.3/-0.8/-0.6): FAIL; 2013-22 (lite) gross +0.08, fixed -1.96, scaled -0.47: ERA negative net pre-2023 (cost-negative).
- Worst-decile correlation and worst-week-within-share are not defined against an empty base.

## 5. What the control says about the chain

- Gates the live pair passes with margin: gate 3, own null (rank 1.00, 1.5 Sharpe over p95), bootstrap, 2x slippage, executability, H0 and the newest weeks. Gates it fails at the 75/75 plateau definition and in replication: plateau (60%), alternating months (one direction), ES/RTY/YM, and the 2013-22 ERA. If the chain is applied unchanged, the pair itself is a LEAD, not FOUND-PENDING: every candidate that fails the same gates is therefore "pair-grade" on those gates.
- ST is the strongest sleeve to HM (+0.26/+0.32/+0.28 live; plateau 50%), HM adds nothing to ST at the live cell (clean +0.01; it needs HMA 17/70 EMA 100 to reach +0.26, which then fails worst-decile correlation 0.38 and H0), and WT adds +0.37/+0.42/+0.28 to the pair (plateau 50%, H0 negative). The pair live cell sits at rank 20 of 155 and the HM live cell at rank 94 of 138 on clean standalone Sharpe: the clean-only selection would not have picked the live HM cell.
- Files: outputs/autopilot/control/ (grid_*.pkl, selection_*.csv, stageA.pkl, lite_results.csv, CONTROL_CELLS.json); code ap_ctl_lib.py, ap_ctl_grid.py, ap_ctl_score.py, ap_ctl_lite.py, ap_ctl_lite_run.py; PREREG block CONTROL in PREREG_AUTOPILOT.md.
