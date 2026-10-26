# DS3 T-BRACKET-PM section G2 - profit-side Trade Health grid (D3TH2, tier 1: ST, HM, KB, SM, EM)
Prereg G2-P1 sha256 9b8f42e50f72ea7f3385181068572f3dfc6c295d90247ccb2a5f2f6a526edf04 (l2vast/ds3/prereg/TH_G2_P1_prereg.md; DECISIONS.md 2026-10-26T18:01Z), 30 cells x 5 entries = 150 cell-entries, all in the ledger (l2vast/struct48/ledger/trials.jsonl). Holdout (2025-07+) looked once for the group after l2vast/ds3/prereg/TH_G2_P1_prehold.md (logged). Rows: l2vast/ds3/rows/DS3_TH_G2.json (= DS3_TBRACKET_G2.json). Code: l2vast/ds3/code/g2/.

## Verdict line
**Profit-side Trade Health: 0 PASS, 0 CANDIDATE, 150 DEAD (150 cell-entries). All 150 cells have a negative WF paired effect (0 of 150 positive; the largest CI upper bound is +1.2 pts); the live STStrat JADE control is negative on all five entries (paired WF ST -1.77, HM -2.18, KB -1.51, SM -3.03, EM -1.19 pts/trade; CI excludes 0 on ST, HM, KB, SM; EM CI [-3.3,+1.1]). Stop-to-breakeven and trail-only variants are also negative. Best cell per entry (min profit 40, the least-cutting setting) is statistically zero-to-negative (best-of-30 null rank ST 0.65, HM 0.35, KB 0.6, SM 0.7, EM 0.25): nothing beats chance. No registration in PAPER-ALL (no PASS/CANDIDATE), no 3x3 widening required.**

## Design and engine (as preregistered)
* Staged fractional design: the full G2 space is 145-153 cells/entry (~750 cell-entries); stage 1 scored 30 cells/entry (control, 10 one-factor moves, 9 two-factor interactions, 3 breakeven, 7 trail-only). Unscored grid cells (min profit x required x trail x scale) are NOT scored; stage 2 (neighbour widening) was not triggered because stage 1 produced no cell with positive WF effect and CI above zero (a 3x3 widening is only required around a PASS). Interaction cells that were not preregistered stay unscored: the grid response is monotone in cut share (below), so unscored cells are expected to lie between the scored ones.
* Screen = MAPPED: 1-s path kernel (base bracket reproduced to the point and exit bar on 100% of base trades, all five entries), STStrat profit-side port (st_th.py semantics) on 1-s rows, live exit model (stop-join 1.01, market 0.995, limit 0) as a delta on the corrected-P9 mapped base, exact lock engine (Set A 14/14 for ST/HM with the other book at base; 10-lot per-book locks for KB/SM/EM). Cut trades free the book, so the cell takes extra entries (counted: n_new_entries; they enter weekly series, not the paired mean).
* Print-level cross-check (ap_thaudit_kern, tick-port flags, prints 2023-02..2026-02) of the control on all five entries and the best cell per entry: tick-level paired effect agrees with the 1-s screen in sign and size (table below). Cut share ST live 72% (tick) vs 71% (1-s). **DIRECT L2 replay (SO2 standard) was NOT run**: it exists only for static OCO brackets, no cell is a PASS/CANDIDATE, and a path-dependent TH exit cannot be represented by it; the print-level kernel is the highest-fidelity engine used. Basis is therefore MAPPED + print-level, and exec_status is NOT DELIVERABLE as a recommendation.
* Windows: selection PRE 2024-02..2025-06; holdout 2025-07+ once; second span 2023-04..2024-01 reported; verdict window WF (PRE + holdout) for the paired test with holdout sign, placebo (random exit timing, same cut share and hold-time distribution, 20 draws, PRE metric), neighbours (adjacent factor levels), maxDD of the full sequence, 2x cost, DSR over the ledger count.

## Named control rows (live STStrat JADE: min profit 20, 3 of 4, trail 8, C1 30s/4, C2 60s/4, C3 60s/0.35, C4 30s/0.55, eval 1 s)
| entry | cut share | would-hit-target share of cut trades | EV per cut (pts) | paired WF pts/trade [CI] | MDE | paired HOLD | print-level paired [CI] | weekly d_mean $/wk (WF) | d_maxDD $ (WF) | 2x paired |
|--|--|--|--|--|--|--|--|--|--|--|
| ST | 0.71 | 0.63 | -2.02 | -1.77 [-2.83,-0.60] | 1.62 | -1.80 | -1.88 [-2.92,-0.83] | -23509 | +205605 | -2.22 |
| HM | 0.72 | 0.63 | -1.83 | -2.18 [-3.46,-0.79] | 1.89 | -2.29 | -1.21 [-2.41,+0.01] | -14645 | +189387 | -2.64 |
| KB | 0.72 | 0.63 | -1.94 | -1.51 [-2.58,-0.38] | 1.57 | -1.23 | -1.31 [-2.37,-0.26] | -12783 | +486264 | -1.95 |
| SM | 0.73 | 0.64 | -2.17 | -3.03 [-5.28,-0.98] | 3.02 | -2.33 | -1.62 [-3.58,+0.24] | -8105 | +101528 | -3.50 |
| EM | 0.74 | 0.63 | -1.81 | -1.19 [-3.34,+1.10] | 3.10 | -1.34 | -1.13 [-2.87,+0.96] | -2183 | +76448 | -1.65 |

Reading: about 72% of trades are cut, 63% of the cut trades would have hit the 60-pt target uncut, and the cut trades keep +15.5 pts on average against +17.4 uncut: the rule gives up ~2 pts per cut. Weekly effect is negative on all five entries; the extra attempts (book freed early) do not repay it, as in the TH audit (REPORT_TH_AUDIT s0b).

## All cells (WF 2024-02+ paired vs own base; MDE = bootstrap MDE at 80% power; every row DEAD)

### ST

| cell | cut share | would-hit-tgt | EV/cut pts | paired WF pts/trade [CI] | MDE | HOLD | SPAN2 | placebo rank | d_mean $/wk | d_maxDD $ | nbrs agree | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| G2_TH_LIVE_JADE_m20_r3_t8_s1 (CONTROL) | 0.71 | 0.63 | -2.02 | -1.77 [-2.83,-0.60] | 1.62 | -1.80 | -1.47 | 0.80 | -23509 | +205605 | False | DEAD |
| G2_m40_r4_t8_s1 | 0.29 | 0.64 | -0.74 | -0.39 [-1.08,+0.32] | 1.03 | -0.20 | -0.12 | 0.80 | -11172 | +204126 | False | DEAD |
| G2_m20_r4_t8_s1 | 0.54 | 0.54 | -1.70 | -0.93 [-1.89,+0.03] | 1.38 | -0.89 | +0.13 | 0.90 | -20400 | +495603 | False | DEAD |
| G2_m20_r4_t12_s1 | 0.54 | 0.54 | -1.74 | -0.94 [-1.85,-0.00] | 1.39 | -0.92 | +0.16 | 1.00 | -21767 | +460308 | False | DEAD |
| G2_m40_r3_t8_s1 | 0.48 | 0.77 | -1.57 | -0.96 [-1.77,-0.19] | 1.13 | -0.74 | -0.23 | 0.65 | -7774 | +58217 | False | DEAD |
| G2_m40_r2_t8_s1 | 0.52 | 0.79 | -1.55 | -0.96 [-1.82,-0.13] | 1.18 | -0.77 | -0.30 | 0.85 | -9232 | +62101 | False | DEAD |
| G2_TRAILONLY_m40_t8 | 0.55 | 0.80 | -1.54 | -1.00 [-1.85,-0.16] | 1.20 | -0.74 | -0.19 | 0.70 | -12868 | +22370 | False | DEAD |
| G2_m30_r3_t4_s1 | 0.61 | 0.70 | -1.22 | -1.02 [-1.96,-0.08] | 1.38 | -0.83 | -0.57 | 0.95 | -18145 | +264736 | False | DEAD |
| G2_m30_r3_t12_s1 | 0.58 | 0.68 | -1.29 | -1.04 [-2.02,-0.15] | 1.35 | -0.82 | -0.38 | 0.70 | -20522 | +305059 | False | DEAD |
| G2_m30_r3_t8_s1 | 0.60 | 0.70 | -1.32 | -1.09 [-2.08,-0.16] | 1.35 | -0.90 | -0.54 | 0.90 | -18749 | +220484 | False | DEAD |
| G2_m10_r4_t8_s1 | 0.67 | 0.49 | -1.46 | -1.16 [-2.27,-0.09] | 1.56 | -1.33 | -0.70 | 1.00 | -22844 | +739778 | False | DEAD |
| G2_TRAILONLY_m30_t8 | 0.66 | 0.72 | -1.50 | -1.29 [-2.35,-0.31] | 1.44 | -1.30 | -0.56 | 0.90 | -18835 | +286527 | False | DEAD |
| G2_BE_p20 | 0.50 | 0.48 | -1.92 | -1.33 [-2.28,-0.36] | 1.45 | -1.34 | -1.26 | 0.75 | -21800 | +330924 | False | DEAD |
| G2_BE_p15 | 0.61 | 0.48 | -1.89 | -1.48 [-2.63,-0.43] | 1.61 | -1.35 | -1.06 | 0.60 | -22055 | +580984 | False | DEAD |
| G2_m20_r2_t4_s1 | 0.74 | 0.64 | -1.86 | -1.52 [-2.65,-0.36] | 1.66 | -1.50 | -1.65 | 0.95 | -20597 | +208143 | False | DEAD |
| G2_m20_r3_t8_s2.0 | 0.69 | 0.62 | -1.88 | -1.64 [-2.67,-0.58] | 1.51 | -1.61 | -1.19 | 0.65 | -20785 | +107180 | False | DEAD |
| G2_m20_r3_t4_s1 | 0.72 | 0.63 | -1.93 | -1.66 [-2.72,-0.47] | 1.62 | -1.65 | -1.54 | 0.75 | -22900 | +308133 | False | DEAD |
| G2_BE_p10 | 0.72 | 0.48 | -1.90 | -1.66 [-2.89,-0.44] | 1.71 | -1.66 | -1.99 | 0.80 | -33926 | +1077110 | False | DEAD |
| G2_TRAILONLY_m20_t4 | 0.75 | 0.65 | -1.91 | -1.69 [-2.82,-0.49] | 1.65 | -1.64 | -1.62 | 0.75 | -20101 | +149064 | False | DEAD |
| G2_m20_r3_t12_s1 | 0.70 | 0.62 | -1.98 | -1.74 [-2.78,-0.74] | 1.52 | -1.65 | -1.41 | 0.45 | -24923 | +115318 | False | DEAD |
| G2_m20_r2_t8_s1 | 0.74 | 0.64 | -1.98 | -1.75 [-2.86,-0.59] | 1.66 | -1.80 | -1.66 | 0.75 | -19803 | +181026 | False | DEAD |
| G2_m20_r2_t8_s2 | 0.73 | 0.64 | -2.11 | -1.82 [-2.95,-0.66] | 1.63 | -1.78 | -1.55 | 0.65 | -21519 | +256712 | False | DEAD |
| G2_m20_r3_t8_s0.5 | 0.72 | 0.63 | -2.08 | -1.86 [-2.96,-0.67] | 1.64 | -1.91 | -1.55 | 0.55 | -21931 | +163582 | False | DEAD |
| G2_TRAILONLY_m20_t12 | 0.73 | 0.63 | -2.04 | -1.92 [-2.98,-0.86] | 1.59 | -1.96 | -1.41 | 0.65 | -22802 | +65101 | False | DEAD |
| G2_TRAILONLY_m20_t8 | 0.75 | 0.65 | -2.09 | -1.95 [-3.09,-0.77] | 1.65 | -1.90 | -1.53 | 0.60 | -20526 | +223919 | False | DEAD |
| G2_m15_r3_t8_s1 | 0.77 | 0.59 | -2.03 | -1.98 [-3.14,-0.87] | 1.65 | -1.98 | -1.67 | 0.60 | -30100 | +346025 | False | DEAD |
| G2_m10_r3_t8_s1 | 0.84 | 0.56 | -2.39 | -2.14 [-3.35,-0.91] | 1.77 | -2.30 | -2.17 | 0.65 | -36709 | +644753 | False | DEAD |
| G2_TRAILONLY_m15_t8 | 0.80 | 0.61 | -2.25 | -2.14 [-3.28,-1.04] | 1.69 | -1.97 | -1.76 | 0.45 | -33748 | +407801 | False | DEAD |
| G2_m10_r2_t8_s1 | 0.85 | 0.56 | -2.40 | -2.27 [-3.54,-1.03] | 1.81 | -2.40 | -2.25 | 0.75 | -34634 | +835579 | False | DEAD |
| G2_TRAILONLY_m10_t8 | 0.86 | 0.57 | -2.48 | -2.36 [-3.63,-1.13] | 1.80 | -2.38 | -2.12 | 0.35 | -36538 | +686318 | False | DEAD |

Best cell G2_m40_r4_t8_s1: best-of-30 random-timing null rank 0.65 (below 0.95: indistinguishable from the best of 30 random-timing draws).

### HM

| cell | cut share | would-hit-tgt | EV/cut pts | paired WF pts/trade [CI] | MDE | HOLD | SPAN2 | placebo rank | d_mean $/wk | d_maxDD $ | nbrs agree | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| G2_TH_LIVE_JADE_m20_r3_t8_s1 (CONTROL) | 0.72 | 0.63 | -1.83 | -2.18 [-3.46,-0.79] | 1.89 | -2.29 | +1.45 | 0.20 | -14645 | +189387 | False | DEAD |
| G2_m40_r4_t8_s1 | 0.30 | 0.65 | -2.80 | -1.09 [-1.91,-0.35] | 1.12 | -1.40 | -0.38 | 0.60 | -11239 | +44270 | False | DEAD |
| G2_BE_p20 | 0.50 | 0.47 | -1.28 | -1.21 [-2.38,-0.06] | 1.65 | -0.87 | +1.25 | 0.30 | -8656 | +139882 | False | DEAD |
| G2_m40_r2_t8_s1 | 0.52 | 0.78 | -1.25 | -1.45 [-2.37,-0.47] | 1.39 | -1.78 | +0.23 | 0.70 | -9602 | +215814 | False | DEAD |
| G2_m40_r3_t8_s1 | 0.49 | 0.77 | -1.51 | -1.46 [-2.37,-0.50] | 1.36 | -1.78 | +0.18 | 0.65 | -12366 | +192789 | False | DEAD |
| G2_m30_r3_t4_s1 | 0.61 | 0.70 | -1.41 | -1.55 [-2.66,-0.37] | 1.64 | -1.78 | -1.03 | 0.75 | -10644 | +135769 | False | DEAD |
| G2_m20_r4_t8_s1 | 0.55 | 0.54 | -1.73 | -1.63 [-2.81,-0.43] | 1.68 | -1.72 | +1.85 | 0.25 | -13135 | +270406 | False | DEAD |
| G2_m30_r3_t8_s1 | 0.61 | 0.70 | -1.62 | -1.65 [-2.80,-0.50] | 1.63 | -1.89 | -0.89 | 0.80 | -13607 | +124060 | False | DEAD |
| G2_m20_r4_t12_s1 | 0.54 | 0.54 | -1.81 | -1.65 [-2.83,-0.44] | 1.68 | -1.74 | +1.83 | 0.30 | -12730 | +271539 | False | DEAD |
| G2_BE_p15 | 0.60 | 0.47 | -1.27 | -1.72 [-3.12,-0.44] | 1.86 | -1.51 | +1.40 | 0.35 | -9407 | -15243 | False | DEAD |
| G2_TRAILONLY_m40_t8 | 0.55 | 0.79 | -1.60 | -1.78 [-2.73,-0.82] | 1.35 | -2.04 | +0.03 | 0.15 | -10530 | +211867 | False | DEAD |
| G2_BE_p10 | 0.71 | 0.47 | -0.96 | -1.83 [-3.32,-0.36] | 2.12 | -1.71 | +0.63 | 0.45 | -7971 | +65156 | False | DEAD |
| G2_m30_r3_t12_s1 | 0.59 | 0.69 | -1.84 | -1.89 [-3.04,-0.80] | 1.62 | -1.95 | -0.24 | 0.40 | -17733 | +198700 | False | DEAD |
| G2_TRAILONLY_m30_t8 | 0.66 | 0.72 | -1.71 | -1.91 [-3.20,-0.82] | 1.69 | -2.11 | -0.79 | 0.55 | -12547 | +133139 | False | DEAD |
| G2_m10_r4_t8_s1 | 0.67 | 0.49 | -1.68 | -1.99 [-3.29,-0.79] | 1.86 | -2.55 | +1.84 | 0.80 | -12266 | +85689 | False | DEAD |
| G2_m20_r3_t8_s2.0 | 0.71 | 0.62 | -1.83 | -2.01 [-3.28,-0.61] | 1.90 | -1.92 | +1.54 | 0.25 | -16927 | +103979 | False | DEAD |
| G2_m20_r2_t8_s2 | 0.74 | 0.63 | -1.79 | -2.03 [-3.34,-0.74] | 1.89 | -2.15 | +0.96 | 0.20 | -15699 | +173178 | False | DEAD |
| G2_m20_r3_t4_s1 | 0.73 | 0.63 | -1.68 | -2.07 [-3.43,-0.72] | 1.88 | -2.18 | +1.33 | 0.35 | -12698 | +94396 | False | DEAD |
| G2_m20_r2_t4_s1 | 0.75 | 0.63 | -1.65 | -2.11 [-3.49,-0.81] | 1.97 | -2.12 | +0.98 | 0.35 | -13689 | +107582 | False | DEAD |
| G2_TRAILONLY_m20_t4 | 0.76 | 0.64 | -1.75 | -2.13 [-3.50,-0.72] | 1.96 | -2.27 | +0.66 | 0.55 | -14135 | +57072 | False | DEAD |
| G2_m20_r3_t8_s0.5 | 0.73 | 0.63 | -1.96 | -2.17 [-3.58,-0.87] | 1.88 | -2.15 | +1.17 | 0.10 | -13458 | +78030 | False | DEAD |
| G2_m20_r3_t12_s1 | 0.71 | 0.62 | -2.02 | -2.22 [-3.49,-1.02] | 1.78 | -2.10 | +1.34 | 0.05 | -19868 | +341706 | False | DEAD |
| G2_m20_r2_t8_s1 | 0.74 | 0.63 | -1.84 | -2.23 [-3.57,-0.96] | 1.89 | -2.25 | +1.06 | 0.25 | -17043 | +201912 | False | DEAD |
| G2_m15_r3_t8_s1 | 0.78 | 0.59 | -1.71 | -2.25 [-3.55,-0.80] | 1.95 | -2.40 | +1.14 | 0.45 | -13146 | +331328 | False | DEAD |
| G2_TRAILONLY_m20_t8 | 0.75 | 0.64 | -1.92 | -2.29 [-3.72,-0.92] | 1.97 | -2.34 | +1.02 | 0.25 | -14172 | +190194 | False | DEAD |
| G2_TRAILONLY_m20_t12 | 0.73 | 0.63 | -2.08 | -2.31 [-3.63,-0.94] | 1.91 | -2.15 | +1.30 | 0.10 | -20685 | +330852 | False | DEAD |
| G2_m10_r3_t8_s1 | 0.84 | 0.55 | -1.76 | -2.35 [-3.87,-0.90] | 2.11 | -2.66 | -0.05 | 0.80 | -12297 | +169848 | False | DEAD |
| G2_TRAILONLY_m15_t8 | 0.81 | 0.60 | -1.99 | -2.54 [-4.00,-1.13] | 2.12 | -2.66 | +0.71 | 0.40 | -16058 | +306292 | False | DEAD |
| G2_m10_r2_t8_s1 | 0.86 | 0.56 | -1.92 | -2.65 [-4.20,-1.13] | 2.14 | -3.00 | -0.66 | 0.50 | -12219 | +14747 | False | DEAD |
| G2_TRAILONLY_m10_t8 | 0.86 | 0.56 | -2.03 | -2.75 [-4.29,-1.22] | 2.14 | -3.13 | -0.64 | 0.55 | -15305 | +117041 | False | DEAD |

Best cell G2_m40_r4_t8_s1: best-of-30 random-timing null rank 0.35 (below 0.95: indistinguishable from the best of 30 random-timing draws).

### KB

| cell | cut share | would-hit-tgt | EV/cut pts | paired WF pts/trade [CI] | MDE | HOLD | SPAN2 | placebo rank | d_mean $/wk | d_maxDD $ | nbrs agree | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| G2_TH_LIVE_JADE_m20_r3_t8_s1 (CONTROL) | 0.72 | 0.63 | -1.94 | -1.51 [-2.58,-0.38] | 1.57 | -1.23 | +0.60 | 1.00 | -12783 | +486264 | False | DEAD |
| G2_m40_r4_t8_s1 | 0.29 | 0.64 | -1.00 | -0.31 [-1.00,+0.38] | 1.00 | +0.17 | -0.44 | 0.65 | -872 | -46900 | False | DEAD |
| G2_m40_r3_t8_s1 | 0.48 | 0.76 | -1.02 | -0.63 [-1.49,+0.09] | 1.11 | -0.42 | -0.32 | 0.90 | -3183 | +70882 | False | DEAD |
| G2_m10_r4_t8_s1 | 0.68 | 0.49 | -1.13 | -0.88 [-1.98,+0.26] | 1.60 | -0.22 | +1.03 | 1.00 | -17444 | +543087 | False | DEAD |
| G2_m40_r2_t8_s1 | 0.52 | 0.78 | -1.35 | -0.89 [-1.69,-0.10] | 1.17 | -0.62 | -0.62 | 0.85 | -5776 | +39800 | False | DEAD |
| G2_m20_r4_t8_s1 | 0.55 | 0.54 | -1.49 | -0.99 [-2.06,+0.02] | 1.46 | -0.47 | +0.87 | 0.80 | -12551 | +512225 | False | DEAD |
| G2_m20_r4_t12_s1 | 0.54 | 0.54 | -1.50 | -1.00 [-1.97,+0.01] | 1.42 | -0.43 | +0.90 | 0.65 | -12434 | +571676 | False | DEAD |
| G2_TRAILONLY_m40_t8 | 0.55 | 0.80 | -1.55 | -1.11 [-1.90,-0.28] | 1.16 | -0.97 | -0.73 | 0.95 | -7442 | +64043 | False | DEAD |
| G2_BE_p15 | 0.60 | 0.48 | -1.57 | -1.12 [-2.21,-0.02] | 1.56 | -0.26 | +0.92 | 0.70 | -21875 | +595579 | False | DEAD |
| G2_BE_p20 | 0.50 | 0.48 | -1.57 | -1.23 [-2.22,-0.32] | 1.41 | -0.34 | +1.39 | 0.25 | -17679 | +281183 | False | DEAD |
| G2_BE_p10 | 0.72 | 0.48 | -1.54 | -1.25 [-2.55,-0.02] | 1.82 | -0.08 | +0.54 | 0.40 | -20115 | +413096 | False | DEAD |
| G2_m20_r3_t8_s2.0 | 0.70 | 0.62 | -1.73 | -1.29 [-2.37,-0.19] | 1.54 | -0.81 | +0.38 | 0.95 | -11929 | +408240 | False | DEAD |
| G2_m30_r3_t4_s1 | 0.61 | 0.71 | -2.08 | -1.34 [-2.38,-0.37] | 1.42 | -1.13 | +0.76 | 0.95 | -11340 | +211157 | False | DEAD |
| G2_m30_r3_t12_s1 | 0.58 | 0.69 | -2.16 | -1.35 [-2.25,-0.37] | 1.34 | -1.16 | +0.66 | 0.90 | -10314 | +178390 | False | DEAD |
| G2_m30_r3_t8_s1 | 0.60 | 0.71 | -2.27 | -1.41 [-2.42,-0.48] | 1.41 | -1.21 | +0.94 | 0.65 | -11207 | +201133 | False | DEAD |
| G2_m20_r3_t4_s1 | 0.72 | 0.63 | -1.88 | -1.45 [-2.60,-0.32] | 1.60 | -1.13 | +0.32 | 1.00 | -12428 | +606275 | False | DEAD |
| G2_m20_r2_t4_s1 | 0.74 | 0.64 | -1.84 | -1.45 [-2.55,-0.31] | 1.56 | -0.97 | -0.26 | 0.90 | -11838 | +57182 | False | DEAD |
| G2_m20_r3_t8_s0.5 | 0.73 | 0.63 | -1.79 | -1.49 [-2.61,-0.40] | 1.56 | -1.15 | +0.36 | 0.95 | -13728 | +400442 | False | DEAD |
| G2_m20_r3_t12_s1 | 0.70 | 0.62 | -2.00 | -1.52 [-2.59,-0.48] | 1.53 | -1.13 | +0.07 | 1.00 | -17572 | +790500 | False | DEAD |
| G2_TRAILONLY_m20_t4 | 0.76 | 0.65 | -1.95 | -1.55 [-2.72,-0.33] | 1.69 | -1.11 | -0.13 | 0.90 | -15429 | +139652 | False | DEAD |
| G2_m20_r2_t8_s1 | 0.74 | 0.64 | -1.96 | -1.55 [-2.67,-0.43] | 1.57 | -1.16 | +0.09 | 1.00 | -14176 | +199800 | False | DEAD |
| G2_m20_r2_t8_s2 | 0.73 | 0.63 | -1.88 | -1.58 [-2.63,-0.51] | 1.53 | -1.16 | +0.03 | 0.90 | -13003 | +268913 | False | DEAD |
| G2_TRAILONLY_m30_t8 | 0.65 | 0.73 | -2.23 | -1.65 [-2.64,-0.59] | 1.47 | -1.43 | +0.82 | 1.00 | -12172 | +152033 | False | DEAD |
| G2_TRAILONLY_m20_t8 | 0.75 | 0.64 | -2.01 | -1.69 [-2.75,-0.56] | 1.62 | -1.30 | +0.09 | 0.90 | -16692 | +300185 | False | DEAD |
| G2_TRAILONLY_m20_t12 | 0.73 | 0.63 | -2.01 | -1.69 [-2.85,-0.60] | 1.61 | -1.33 | -0.16 | 0.90 | -20664 | +678514 | False | DEAD |
| G2_m15_r3_t8_s1 | 0.78 | 0.59 | -2.22 | -1.82 [-3.03,-0.72] | 1.66 | -1.30 | -0.91 | 0.80 | -24647 | +1245579 | False | DEAD |
| G2_m10_r3_t8_s1 | 0.84 | 0.56 | -2.18 | -1.90 [-3.11,-0.67] | 1.74 | -1.04 | -0.70 | 0.90 | -29044 | +1617553 | False | DEAD |
| G2_m10_r2_t8_s1 | 0.85 | 0.56 | -2.36 | -2.06 [-3.31,-0.81] | 1.78 | -1.09 | -0.95 | 0.60 | -32165 | +1951738 | False | DEAD |
| G2_TRAILONLY_m15_t8 | 0.80 | 0.60 | -2.34 | -2.07 [-3.20,-0.86] | 1.67 | -1.36 | -0.79 | 0.50 | -24710 | +1161367 | False | DEAD |
| G2_TRAILONLY_m10_t8 | 0.86 | 0.56 | -2.38 | -2.19 [-3.46,-0.87] | 1.79 | -1.14 | -0.61 | 0.30 | -33328 | +2185285 | False | DEAD |

Best cell G2_m40_r3_t8_s1: best-of-30 random-timing null rank 0.6 (below 0.95: indistinguishable from the best of 30 random-timing draws).

### SM

| cell | cut share | would-hit-tgt | EV/cut pts | paired WF pts/trade [CI] | MDE | HOLD | SPAN2 | placebo rank | d_mean $/wk | d_maxDD $ | nbrs agree | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| G2_TH_LIVE_JADE_m20_r3_t8_s1 (CONTROL) | 0.73 | 0.64 | -2.17 | -3.03 [-5.28,-0.98] | 3.02 | -2.33 | +0.09 | 0.55 | -8105 | +101528 | False | DEAD |
| G2_m40_r4_t8_s1 | 0.31 | 0.64 | -0.53 | -0.34 [-1.71,+0.93] | 1.86 | +0.41 | -0.21 | 0.80 | -1822 | +43820 | False | DEAD |
| G2_m40_r3_t8_s1 | 0.50 | 0.76 | +0.04 | -0.54 [-2.00,+0.97] | 2.15 | +0.05 | +0.20 | 0.95 | -2057 | +5948 | False | DEAD |
| G2_m40_r2_t8_s1 | 0.55 | 0.78 | -0.60 | -1.00 [-2.50,+0.57] | 2.20 | -0.59 | -0.06 | 0.80 | -3284 | +17954 | False | DEAD |
| G2_TRAILONLY_m40_t8 | 0.57 | 0.79 | -0.78 | -1.24 [-2.76,+0.35] | 2.20 | -0.95 | +0.19 | 1.00 | -4366 | +872 | False | DEAD |
| G2_m30_r3_t4_s1 | 0.62 | 0.71 | -1.43 | -1.88 [-3.93,-0.25] | 2.58 | -1.15 | +1.38 | 0.70 | -5102 | +18065 | False | DEAD |
| G2_m30_r3_t12_s1 | 0.59 | 0.70 | -1.63 | -1.89 [-3.94,-0.29] | 2.56 | -0.99 | +1.00 | 0.55 | -5429 | +31338 | False | DEAD |
| G2_m30_r3_t8_s1 | 0.62 | 0.71 | -1.59 | -1.99 [-4.00,-0.34] | 2.57 | -1.27 | +1.06 | 0.65 | -5395 | +24567 | False | DEAD |
| G2_BE_p20 | 0.52 | 0.49 | -3.16 | -2.41 [-4.32,-0.45] | 2.73 | -1.61 | -0.53 | 0.25 | -7150 | +58313 | False | DEAD |
| G2_m20_r4_t12_s1 | 0.54 | 0.56 | -3.37 | -2.44 [-4.29,-0.70] | 2.65 | -1.77 | -0.89 | 0.40 | -7208 | +63797 | False | DEAD |
| G2_m20_r4_t8_s1 | 0.54 | 0.56 | -3.37 | -2.48 [-4.34,-0.71] | 2.66 | -1.71 | -0.84 | 0.30 | -7285 | +63547 | False | DEAD |
| G2_TRAILONLY_m30_t8 | 0.67 | 0.73 | -2.13 | -2.65 [-4.61,-0.99] | 2.61 | -2.10 | +1.21 | 0.55 | -7173 | +29313 | False | DEAD |
| G2_m20_r3_t8_s2.0 | 0.71 | 0.63 | -1.92 | -2.81 [-5.08,-0.81] | 2.99 | -2.02 | +0.17 | 0.50 | -7397 | +93156 | False | DEAD |
| G2_m20_r3_t12_s1 | 0.71 | 0.63 | -2.13 | -2.84 [-5.06,-0.78] | 3.03 | -2.17 | +0.06 | 0.65 | -7735 | +101007 | False | DEAD |
| G2_m20_r3_t4_s1 | 0.73 | 0.64 | -1.92 | -2.90 [-5.16,-0.85] | 3.03 | -2.13 | +0.56 | 0.40 | -7747 | +95827 | False | DEAD |
| G2_m20_r3_t8_s0.5 | 0.73 | 0.64 | -2.07 | -2.99 [-5.27,-0.92] | 3.05 | -2.40 | +0.02 | 0.65 | -7969 | +95749 | False | DEAD |
| G2_TRAILONLY_m20_t12 | 0.74 | 0.64 | -2.34 | -3.16 [-5.48,-1.16] | 3.08 | -2.58 | +0.03 | 0.60 | -8655 | +100140 | False | DEAD |
| G2_BE_p15 | 0.61 | 0.49 | -3.21 | -3.17 [-5.31,-1.13] | 2.97 | -2.28 | -1.23 | 0.05 | -9904 | +168671 | False | DEAD |
| G2_m20_r2_t8_s2 | 0.74 | 0.64 | -2.27 | -3.18 [-5.41,-1.08] | 3.04 | -2.89 | +0.02 | 0.65 | -8566 | +62673 | False | DEAD |
| G2_m20_r2_t4_s1 | 0.75 | 0.65 | -2.18 | -3.23 [-5.53,-1.05] | 3.10 | -2.77 | +0.39 | 0.45 | -8676 | +71310 | False | DEAD |
| G2_m20_r2_t8_s1 | 0.75 | 0.65 | -2.24 | -3.24 [-5.49,-1.15] | 3.08 | -2.86 | +0.22 | 0.50 | -8693 | +78325 | False | DEAD |
| G2_TRAILONLY_m20_t4 | 0.77 | 0.65 | -2.10 | -3.37 [-5.66,-1.25] | 3.11 | -2.53 | +0.60 | 0.30 | -9370 | +150573 | False | DEAD |
| G2_TRAILONLY_m20_t8 | 0.76 | 0.65 | -2.41 | -3.41 [-5.70,-1.35] | 3.08 | -2.67 | +0.10 | 0.30 | -9294 | +137754 | False | DEAD |
| G2_m10_r4_t8_s1 | 0.65 | 0.51 | -3.35 | -3.41 [-5.53,-1.43] | 2.91 | -1.71 | -1.83 | 0.00 | -9984 | +249936 | False | DEAD |
| G2_BE_p10 | 0.71 | 0.49 | -2.51 | -3.43 [-5.72,-1.13] | 3.26 | -1.76 | -1.91 | 0.00 | -10923 | +369442 | False | DEAD |
| G2_m15_r3_t8_s1 | 0.78 | 0.60 | -2.36 | -3.49 [-5.81,-1.39] | 3.20 | -2.98 | -1.29 | 0.40 | -9823 | +132616 | False | DEAD |
| G2_m10_r3_t8_s1 | 0.83 | 0.57 | -2.37 | -4.00 [-6.41,-1.76] | 3.37 | -2.68 | -2.57 | 0.05 | -11219 | +320604 | False | DEAD |
| G2_TRAILONLY_m15_t8 | 0.81 | 0.62 | -2.87 | -4.08 [-6.36,-2.01] | 3.22 | -3.71 | -1.62 | 0.30 | -11446 | +237654 | False | DEAD |
| G2_m10_r2_t8_s1 | 0.85 | 0.57 | -2.60 | -4.34 [-6.73,-2.05] | 3.39 | -3.24 | -2.43 | 0.05 | -12368 | +331557 | False | DEAD |
| G2_TRAILONLY_m10_t8 | 0.85 | 0.57 | -2.93 | -4.68 [-6.99,-2.23] | 3.42 | -3.60 | -2.96 | 0.00 | -13291 | +422300 | False | DEAD |

Best cell G2_m40_r4_t8_s1: best-of-30 random-timing null rank 0.7 (below 0.95: indistinguishable from the best of 30 random-timing draws).

### EM

| cell | cut share | would-hit-tgt | EV/cut pts | paired WF pts/trade [CI] | MDE | HOLD | SPAN2 | placebo rank | d_mean $/wk | d_maxDD $ | nbrs agree | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| G2_TH_LIVE_JADE_m20_r3_t8_s1 (CONTROL) | 0.74 | 0.63 | -1.81 | -1.19 [-3.34,+1.10] | 3.10 | -1.34 | -3.04 | 1.00 | -2183 | +76448 | False | DEAD |
| G2_m40_r2_t8_s1 | 0.54 | 0.78 | -1.13 | -0.65 [-2.18,+0.87] | 2.19 | -0.91 | -1.38 | 0.85 | -161 | +6517 | False | DEAD |
| G2_m40_r3_t8_s1 | 0.51 | 0.77 | -1.33 | -0.69 [-2.19,+0.80] | 2.15 | -0.96 | -1.58 | 0.85 | -58 | -800 | False | DEAD |
| G2_TRAILONLY_m40_t8 | 0.57 | 0.79 | -1.25 | -0.74 [-2.29,+0.77] | 2.24 | -1.00 | -1.30 | 0.85 | -388 | +18014 | False | DEAD |
| G2_m20_r3_t8_s2.0 | 0.72 | 0.62 | -1.75 | -0.97 [-3.12,+1.21] | 3.10 | -1.14 | -2.73 | 1.00 | -1814 | +112052 | False | DEAD |
| G2_m30_r3_t4_s1 | 0.63 | 0.71 | -1.68 | -1.03 [-2.86,+0.73] | 2.62 | -0.74 | -1.25 | 0.50 | -1728 | +84934 | False | DEAD |
| G2_m20_r2_t4_s1 | 0.76 | 0.64 | -1.70 | -1.04 [-3.21,+1.22] | 3.19 | -0.99 | -2.68 | 0.90 | -2219 | +49874 | False | DEAD |
| G2_TRAILONLY_m20_t4 | 0.77 | 0.64 | -1.67 | -1.10 [-3.28,+1.22] | 3.24 | -0.93 | -2.65 | 1.00 | -2536 | +34831 | False | DEAD |
| G2_m20_r2_t8_s1 | 0.76 | 0.64 | -1.77 | -1.12 [-3.33,+1.09] | 3.16 | -1.05 | -2.86 | 0.90 | -2303 | +74838 | False | DEAD |
| G2_m20_r3_t4_s1 | 0.74 | 0.63 | -1.71 | -1.12 [-3.33,+1.11] | 3.11 | -1.30 | -2.71 | 0.95 | -2130 | +71938 | False | DEAD |
| G2_m20_r3_t12_s1 | 0.73 | 0.62 | -2.00 | -1.15 [-3.25,+1.09] | 3.07 | -1.37 | -3.08 | 0.90 | -2360 | +86352 | False | DEAD |
| G2_m20_r3_t8_s0.5 | 0.75 | 0.63 | -1.86 | -1.15 [-3.33,+1.05] | 3.14 | -1.41 | -2.90 | 0.85 | -2444 | +86197 | False | DEAD |
| G2_m40_r4_t8_s1 | 0.32 | 0.65 | -3.64 | -1.17 [-2.54,+0.14] | 1.97 | -1.64 | -1.47 | 0.50 | -1812 | +64676 | False | DEAD |
| G2_m30_r3_t8_s1 | 0.63 | 0.70 | -1.92 | -1.19 [-3.03,+0.54] | 2.61 | -0.85 | -1.41 | 0.55 | -2150 | +89486 | False | DEAD |
| G2_m20_r2_t8_s2 | 0.75 | 0.63 | -1.95 | -1.24 [-3.38,+1.00] | 3.14 | -1.28 | -2.82 | 0.95 | -2554 | +77297 | False | DEAD |
| G2_m30_r3_t12_s1 | 0.61 | 0.69 | -2.20 | -1.36 [-3.25,+0.35] | 2.60 | -0.92 | -1.47 | 0.15 | -2579 | +86509 | False | DEAD |
| G2_TRAILONLY_m20_t8 | 0.77 | 0.64 | -2.01 | -1.39 [-3.67,+0.85] | 3.18 | -1.10 | -2.88 | 0.55 | -2999 | +67641 | False | DEAD |
| G2_BE_p20 | 0.53 | 0.49 | -3.23 | -1.39 [-3.28,+0.52] | 2.78 | -1.31 | -3.78 | 0.55 | -2895 | +69461 | False | DEAD |
| G2_TRAILONLY_m20_t12 | 0.75 | 0.63 | -2.20 | -1.45 [-3.62,+0.80] | 3.14 | -1.39 | -2.92 | 0.85 | -3127 | +65840 | False | DEAD |
| G2_TRAILONLY_m30_t8 | 0.67 | 0.72 | -2.21 | -1.50 [-3.41,+0.31] | 2.69 | -0.98 | -1.49 | 0.25 | -3053 | +95271 | False | DEAD |
| G2_m20_r4_t8_s1 | 0.56 | 0.55 | -3.11 | -1.67 [-3.55,+0.24] | 2.71 | -1.70 | -2.54 | 0.40 | -3404 | +71190 | False | DEAD |
| G2_m20_r4_t12_s1 | 0.56 | 0.55 | -3.10 | -1.70 [-3.59,+0.18] | 2.71 | -1.81 | -2.54 | 0.30 | -3506 | +60791 | False | DEAD |
| G2_BE_p15 | 0.62 | 0.49 | -2.68 | -1.90 [-4.05,+0.12] | 3.08 | -1.76 | -1.96 | 0.35 | -4932 | +101360 | False | DEAD |
| G2_m15_r3_t8_s1 | 0.79 | 0.60 | -1.88 | -1.92 [-4.34,+0.41] | 3.31 | -2.10 | -1.54 | 0.85 | -4787 | +87529 | False | DEAD |
| G2_BE_p10 | 0.73 | 0.49 | -2.37 | -2.24 [-4.58,-0.00] | 3.31 | -2.62 | -1.91 | 0.70 | -6366 | +78579 | False | DEAD |
| G2_TRAILONLY_m15_t8 | 0.82 | 0.60 | -2.26 | -2.39 [-4.83,-0.01] | 3.40 | -2.21 | -1.42 | 0.50 | -6383 | +148544 | False | DEAD |
| G2_m10_r3_t8_s1 | 0.85 | 0.56 | -1.93 | -2.55 [-4.95,-0.07] | 3.49 | -3.01 | -1.08 | 0.85 | -6891 | +80138 | False | DEAD |
| G2_m10_r2_t8_s1 | 0.86 | 0.56 | -2.01 | -2.68 [-5.13,-0.30] | 3.50 | -2.88 | -1.12 | 0.70 | -7482 | +88620 | False | DEAD |
| G2_m10_r4_t8_s1 | 0.67 | 0.51 | -3.98 | -3.03 [-5.08,-0.79] | 3.03 | -3.05 | -2.40 | 0.00 | -8973 | +219875 | False | DEAD |
| G2_TRAILONLY_m10_t8 | 0.87 | 0.57 | -2.37 | -3.16 [-5.72,-0.74] | 3.56 | -3.34 | -1.08 | 0.30 | -8688 | +111756 | False | DEAD |

Best cell G2_m40_r2_t8_s1: best-of-30 random-timing null rank 0.25 (below 0.95: indistinguishable from the best of 30 random-timing draws).

## Factor reading (all entries agree)
* Paired effect rises toward zero monotonically as cut share falls: min profit 40 and 4-of-4 are the least bad; min profit 10 and 2-of-4 the worst. No setting crosses zero: TH "works" only in the limit of never cutting.
* Trail-only variants (no conditions) are no better than the conditioned rule, i.e. the four conditions add no information over the plain trail; stop-to-breakeven at +10/+15/+20 is negative too (more stop-join exits on trades that would have recovered), with maxDD worse in the full sequence at +10 on every entry (ST +$1.08M, KB +$0.41M, SM +$0.37M, EM +$0.08M, HM +$0.07M).
* By session / long-short / quiet-wide: sign negative in every split with enough pairs (full splits in the rows file, paired_by_session, paired_long_short, paired_quiet_wide).

## Print-level cross-check (finalists = control + best cell per entry; prints 2023-02..2026-02; tick-port flags)
| entry | cell | 1-s screen WF pts/trade | print-level pts/trade [CI] | pairs |
|--|--|--|--|--|
| ST | G2_TH_LIVE_JADE_m20_r3_t8_s1 | -1.77 | -1.88 [-2.92,-0.83] | 7211 |
| ST | G2_m40_r4_t8_s1 | -0.39 | -0.42 [-1.08,+0.21] | 7088 |
| ST | G2_TRAILONLY_m20_t8 | -1.95 | -1.73 [-2.81,-0.63] | 7217 |
| HM | G2_TH_LIVE_JADE_m20_r3_t8_s1 | -2.18 | -1.21 [-2.41,+0.01] | 5538 |
| HM | G2_m40_r4_t8_s1 | -1.09 | -0.60 [-1.29,+0.12] | 5549 |
| KB | G2_TH_LIVE_JADE_m20_r3_t8_s1 | -1.51 | -1.31 [-2.37,-0.26] | 7268 |
| KB | G2_m40_r3_t8_s1 | -0.63 | -0.52 [-1.22,+0.31] | 6848 |
| SM | G2_TH_LIVE_JADE_m20_r3_t8_s1 | -3.03 | -1.62 [-3.58,+0.24] | 2155 |
| SM | G2_m40_r4_t8_s1 | -0.34 | -0.15 [-1.37,+1.05] | 2155 |
| EM | G2_TH_LIVE_JADE_m20_r3_t8_s1 | -1.19 | -1.13 [-2.87,+0.96] | 2148 |
| EM | G2_m40_r2_t8_s1 | -0.65 | -0.84 [-2.25,+0.51] | 2144 |

## Equal-risk columns (per user addendum; rows: cell['equal_risk'])
No cell is DEAD for earning less than ST at equal lots; these cells are DEAD because the paired effect vs the entry's own base is negative. For the controls (cell series at base lots; equal-risk lots scaled to ST10 WF weekly SD; sweep cost applied; capacity = lots where mean reaches zero; DS3 marginal Sharpe via ds3_addbook for control and best cell only, which re-reads the holdout and is logged in addbook_looks.jsonl):
| entry | $/wk equal lots | $/wk equal risk | lots at equal risk | capacity lots | DS3 marginal Sharpe (WF) |
|--|--|--|--|--|--|
| ST (JADE live) | 7592 | 4547 | 8.4 | 21.0 | -0.37569439594978693 |
| HM (JADE live) | 16457 | 9219 | 7.8 | 39.0 | -0.1339085915607785 |
| KB (JADE live) | 3419 | 3935 | 11.5 | 18.0 | -0.28263717629110996 |
| SM (JADE live) | 1417 | 560 | 21.3 | 24.0 | -0.3097728085217035 |
| EM (JADE live) | 6018 | 10707 | 23.2 | 78.0 | 0.34861297259947754 |

## MDE statement
Paired MDE (80% power, bootstrap, WF) is 1.6-1.9 pts/trade on ST/HM/KB and 3.0-3.1 on SM/EM. The control effects (-1.2 to -3.0) exceed the MDE only on ST (1.77 vs 1.62) and HM/KB/SM by CI, not on EM; the least-cutting cells (-0.3 to -0.9) are below the MDE, so those are null reads ("could not see an effect smaller than the MDE"), but they are not positive either, and no cell has a positive point estimate or a CI above zero.

## Not done / caveats
* Direct L2 replay of TH exits (see above); G3/G4 combinations with A-D are separate preregs; unscored grid cells; the print archive ends 2026-02-06 so the print-level check excludes 2026-02..10. The 1-s mapping of the conditions (second end, min-path efficiency, second extremes for collapse) is validated against the print kernel at the effect level, not trade-by-trade.
* Nearest scored cells: TH audit profit-side arms and nq7_th_overlay (0/1620 positive): the result replicates them on four additional entries (KB, SM, EM and HM profit-side).
