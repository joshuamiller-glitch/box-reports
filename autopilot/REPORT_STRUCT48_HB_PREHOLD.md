# STRUCT48 HB - handoff book: PRE-HOLDOUT TEXT (RESEARCH V2 addendum)
Written BEFORE the holdout look. Prereg l2vast/struct48/prereg/HB_prereg.md sha256 ac398dcc5472910477495467c39be06ba230bb49b58f38494e648c8e3bef177e (frozen in autopilot/DECISIONS.md before any scored cell; 28 cells appended to ledger/trials.jsonl).
Everything below is WF-PRE (2024-02..2025-06, 912 stop-out events) and IS (2023-02..2024-01, 512 events). The holdout (2025-07+, 1,044 events) and L8W are NOT read: no number in this text was computed on a holdout day (the engine run covers the whole tape, the scoring slices WF-PRE/IS only).
Research only; no execution-server / chart / live change; no credentials; no download; UNTOUCHED not read.

## What was tested
A book that is flat until an ST or HM stop-out of a D2 trade that Set A actually took, then (a) reverses at the stop fill, (b) goes to the session VWAP, (c) re-enters toward the opening range / prior-day value area, (d) re-takes the original direction on a re-break of the stopped level. Unit = stop-out event (912 in WF-PRE); paired difference vs 'do nothing after the stop'; trade-block bootstrap, blocks = label-day x session; chain rule = one position per event, closed at the next stop-out in the session; fills on the 1-s tape with stop-join 1.01 pt, market 0.995 pt, $4.84 RT/contract. Live stop exits are ~2.01 pts worse than nominal (replay 0.52); SENS2 re-runs everything with every stop-order fill 2.0 pts worse (columns SENS2). Details in the prereg.

## Main table (WF-PRE)
Score window WF-PRE. Paired effect = mean over ALL stop-out events (0 for no-trade events) of book pts net of fills and commission; $ at the cell's lots; $/wk = window sum / weeks. Full-seq = Set A + book through the locked sequence, week-block CI; d = vs Set A.

| cell | n events | trades (skipped by filter) | paired effect pts/event [95% CI] | $/event | $/wk | MDE pts (80%) | effect >= MDE | placebo | neighbours | full-seq d mean $/wk [CI] | d SD | d maxDD | 2x d $/wk | SENS2 paired pts | SENS2 d $/wk | year-share | DSR | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HB_REV_s20_r1.0_L4 | 912 | 691 (196) | -1.96 [-3.16, -0.72] | -156 | -1,902 | 1.70 | Y | 0.05 | Y | -592 [-4,573, +3,159] | +1,477 | +79,794 | -3,169 | -4.17 | -314 | - | 0.150 | DEAD* |
| HB_REV_s20_r1.0_L7 | 912 | 691 (196) | -1.96 [-3.16, -0.72] | -274 | -3,329 | 1.70 | Y | 0.05 | Y | +34 [-5,037, +4,942] | +3,856 | +64,350 | -3,365 | -4.17 | -2,006 | 61.80 | 0.153 | DEAD* |
| HB_REV_s20_r1.5_L4 | 912 | 691 (196) | -2.58 [-4.11, -1.12] | -206 | -2,507 | 2.03 | Y | 0.01 | Y | +1,877 [-3,360, +6,988] | +4,434 | +44,180 | -4,105 | -5.05 | -2,096 | 1.27 | 0.191 | DEAD* |
| HB_REV_s20_r1.5_L7 | 912 | 691 (196) | -2.58 [-4.11, -1.12] | -361 | -4,387 | 2.03 | Y | 0.01 | Y | +268 [-5,393, +6,039] | +4,093 | +29,286 | -5,646 | -5.05 | -5,998 | 1.02 | 0.157 | DEAD* |
| HB_REV_s30_r1.0_L4 | 912 | 691 (196) | -2.51 [-4.24, -0.83] | -201 | -2,446 | 2.37 | Y | 0.02 | Y | -949 [-4,549, +2,003] | +964 | +41,752 | -2,205 | -4.91 | -848 | - | 0.145 | DEAD* |
| HB_REV_s30_r1.0_L7 | 912 | 691 (196) | -2.51 [-4.24, -0.83] | -352 | -4,281 | 2.37 | Y | 0.02 | Y | +624 [-5,340, +7,120] | +4,710 | +32,781 | -8,695 | -4.91 | -3,776 | 1.51 | 0.161 | DEAD* |
| HB_REV_s30_r1.5_L4 | 912 | 691 (196) | -2.98 [-4.80, -1.16] | -239 | -2,903 | 2.66 | Y | 0.01 | Y | -2,733 [-7,435, +1,686] | -1,824 | +41,595 | -6,476 | -5.00 | -4,785 | - | 0.119 | DEAD* |
| HB_REV_s30_r1.5_L7 | 912 | 691 (196) | -2.98 [-4.80, -1.16] | -418 | -5,081 | 2.66 | Y | 0.01 | Y | -3,407 [-9,863, +2,817] | +183 | -2,419 | -13,387 | -5.00 | -7,685 | - | 0.101 | DEAD* |
| HB_REV_s40_r1.0_L4 | 912 | 691 (196) | -2.18 [-4.35, -0.06] | -175 | -2,123 | 3.09 | N | 0.10 | Y | -2,575 [-6,369, +1,150] | +633 | +29,020 | -1,720 | -4.51 | -2,510 | - | 0.115 | DEAD* |
| HB_REV_s40_r1.0_L7 | 912 | 691 (196) | -2.18 [-4.35, -0.06] | -305 | -3,715 | 3.09 | N | 0.10 | Y | -2,342 [-9,513, +5,050] | +2,824 | -12,410 | -1,589 | -4.51 | -4,554 | - | 0.111 | DEAD* |
| HB_REV_s40_r1.5_L4 | 912 | 691 (196) | -2.92 [-5.25, -0.55] | -234 | -2,843 | 3.46 | N | 0.02 | Y | -5,174 [-10,747, +528] | -1,153 | +31,254 | -4,409 | -5.15 | -6,534 | - | 0.079 | DEAD* |
| HB_REV_s40_r1.5_L7 | 912 | 691 (196) | -2.92 [-5.25, -0.55] | -409 | -4,975 | 3.46 | N | 0.02 | Y | -3,807 [-11,002, +3,865] | +1,813 | +65,952 | -8,648 | -5.15 | -9,563 | - | 0.091 | DEAD* |
| HB_VWAP_k1.5_L4 | 912 | 604 (190) | -0.34 [-2.52, +1.81] | -27 | -331 | 3.16 | N | 0.89 | Y | +3,194 [-6,066, +13,467] | -1,775 | +29,829 | -4,971 | -0.63 | +3,074 | 0.66 | 0.258 | DEAD* |
| HB_VWAP_k1.5_L7 | 912 | 604 (190) | -0.34 [-2.52, +1.81] | -48 | -578 | 3.16 | N | 0.89 | Y | +4,292 [-6,318, +16,202] | -2,275 | +28,837 | -3,286 | -0.63 | +4,245 | 0.73 | 0.294 | DEAD* |
| HB_VWAP_k1.25_L4_NB (NB) | 912 | 604 (190) | -0.20 [-2.32, +1.94] | -16 | -192 | 3.10 | N | 0.91 | - | +3,523 [-5,318, +13,778] | -1,737 | +45,105 | -4,552 | -0.54 | +3,342 | 0.53 | 0.267 | DEAD* |
| HB_VWAP_k2.0_L4_NB (NB) | 912 | 604 (190) | -0.83 [-3.14, +1.63] | -66 | -803 | 3.46 | N | 0.77 | - | +1,275 [-8,110, +11,702] | -4,769 | +19,396 | -4,139 | -1.05 | +1,127 | 1.69 | 0.225 | DEAD* |
| HB_OR_s30_L4 | 912 | 130 (74) | +0.90 [+0.03, +1.84] | +72 | +878 | 1.33 | N | 1.00 | Y | +4,171 [-462, +11,224] | +1,063 | -31,600 | -1,811 | +0.81 | +4,110 | 0.62 | 0.266 | DEAD* |
| HB_OR_s30_L7 | 912 | 130 (74) | +0.90 [+0.03, +1.84] | +126 | +1,537 | 1.33 | N | 1.00 | Y | +3,097 [-2,940, +10,761] | +2,102 | +18,208 | 181 | +0.81 | +3,024 | 0.51 | 0.231 | DEAD* |
| HB_OR_s20_L4_NB (NB) | 912 | 130 (74) | +0.50 [-0.12, +1.17] | +40 | +485 | 0.94 | N | 1.00 | - | +1,167 [-1,059, +4,996] | +2,868 | -1,005 | -277 | +0.38 | +1,073 | 1.11 | 0.179 | DEAD* |
| HB_OR_s40_L4_NB (NB) | 912 | 130 (74) | +1.00 [-0.02, +2.16] | +80 | +973 | 1.56 | N | 0.99 | - | +3,055 [-2,822, +11,137] | +2,559 | +24,429 | -126 | +0.92 | +2,894 | 0.53 | 0.228 | DEAD* |
| HB_PV_s30_L4 | 912 | 77 (34) | -0.11 [-0.77, +0.50] | -9 | -111 | 0.92 | N | 0.28 | Y | +503 [-324, +1,537] | +225 | -32,412 | -1,331 | -0.20 | +443 | 0.74 | 0.177 | DEAD* |
| HB_PV_s30_L7 | 912 | 77 (34) | -0.11 [-0.77, +0.50] | -16 | -193 | 0.92 | N | 0.28 | Y | +21 [-3,744, +3,156] | -1,329 | -27,464 | -2,754 | -0.20 | -69 | 61.13 | 0.173 | DEAD* |
| HB_PV_s20_L4_NB (NB) | 912 | 77 (34) | -0.04 [-0.51, +0.46] | -3 | -36 | 0.70 | N | 0.47 | - | +476 [-237, +1,457] | +416 | -30,858 | -2,484 | -0.13 | +408 | 0.89 | 0.176 | DEAD* |
| HB_PV_s40_L4_NB (NB) | 912 | 77 (34) | -0.43 [-1.28, +0.41] | -34 | -414 | 1.20 | N | 0.18 | - | -782 [-4,109, +1,598] | -826 | -32,267 | -858 | -0.51 | -843 | - | 0.153 | DEAD* |
| HB_REB_w15_L4 | 912 | 395 (155) | -0.03 [-2.42, +2.48] | -2 | -29 | 3.65 | N | 0.66 | Y | -3,507 [-11,003, +2,821] | +2,624 | +263,499 | -7,766 | -1.02 | -4,200 | - | 0.095 | DEAD* |
| HB_REB_w15_L7 | 912 | 395 (155) | -0.03 [-2.42, +2.48] | -4 | -50 | 3.65 | N | 0.66 | Y | -4,609 [-14,540, +5,036] | +2,868 | +415,714 | -11,769 | -1.02 | -7,725 | - | 0.080 | DEAD* |
| HB_REB_w30_L4 | 912 | 426 (178) | -0.46 [-2.90, +2.19] | -36 | -443 | 3.74 | N | 0.58 | Y | -4,522 [-11,694, +1,541] | +1,810 | +256,705 | -5,510 | -1.51 | -5,452 | - | 0.083 | DEAD* |
| HB_REB_w30_L7 | 912 | 426 (178) | -0.46 [-2.90, +2.19] | -64 | -776 | 3.74 | N | 0.58 | Y | -4,439 [-14,485, +5,067] | +2,272 | +403,742 | -9,823 | -1.51 | -7,588 | - | 0.083 | DEAD* |

Columns: MDE = minimum detectable paired effect (80% power) from the bootstrap SE of that cell; 'effect >= MDE' = the observed effect is outside what the test could not see. Placebo = share of 500 random-time event sets (same size and session mix, same bracket) whose mean pts/event is BELOW the cell's; a value near 0 means random times do better than stop-outs (after-a-stop-out timing HURTS), near 1 means stop-out timing helps. Year-share is meaningless when the total gain is about 0 (values > 1 or '-' are not informative). DSR = deflated Sharpe on the cumulative ledger (28,502 trials), weekly full-sequence series. A '*' on a verdict marks provisional: the holdout sign is not yet known.

## Gross edge, trade mix and interaction (WF-PRE)
| cell | gross pts/event at ZERO cost (thr=join=market=commission=0) | net paired pts/event | mean net pts per trade (before commission) | trades | exit share stop / target / closed at next stop-out / session end | book's own weekly mean $ (additive) | lock-feedback shift of the full-sequence weekly mean $ | SD of weekly (full-seq minus additive) $ | additive maxDD diff $ | share of book rows blocked by locks |
|---|---|---|---|---|---|---|---|---|---|---|
| HB_REV_s20_r1.0_L4 | -0.52 | -1.96 | -2.3 | 691 | 0.51 / 0.42 / 0.04 / 0.03 | -1,902 | +1,310 | 16,496 | +48,071 | 0.036 |
| HB_REV_s20_r1.0_L7 | -0.52 | -1.96 | -2.3 | 691 | 0.51 / 0.42 / 0.04 / 0.03 | -3,329 | +3,363 | 21,782 | +84,125 | 0.045 |
| HB_REV_s20_r1.5_L4 | -0.65 | -2.58 | -3.2 | 691 | 0.60 / 0.30 / 0.04 / 0.06 | -2,507 | +4,384 | 22,734 | +45,155 | 0.039 |
| HB_REV_s20_r1.5_L7 | -0.65 | -2.58 | -3.2 | 691 | 0.60 / 0.30 / 0.04 / 0.06 | -4,387 | +4,654 | 26,634 | +79,022 | 0.054 |
| HB_REV_s30_r1.0_L4 | -0.69 | -2.51 | -3.1 | 691 | 0.48 / 0.38 / 0.05 / 0.09 | -2,446 | +1,497 | 13,596 | +50,767 | 0.051 |
| HB_REV_s30_r1.0_L7 | -0.69 | -2.51 | -3.1 | 691 | 0.48 / 0.38 / 0.05 / 0.09 | -4,281 | +4,905 | 28,355 | +88,842 | 0.070 |
| HB_REV_s30_r1.5_L4 | -1.40 | -2.98 | -3.7 | 691 | 0.54 / 0.27 / 0.05 / 0.13 | -2,903 | +170 | 22,030 | +39,910 | 0.048 |
| HB_REV_s30_r1.5_L7 | -1.40 | -2.98 | -3.7 | 691 | 0.54 / 0.27 / 0.05 / 0.13 | -5,081 | +1,674 | 28,659 | +69,843 | 0.065 |
| HB_REV_s40_r1.0_L4 | -0.67 | -2.18 | -2.6 | 691 | 0.43 / 0.36 / 0.06 / 0.15 | -2,123 | -452 | 17,105 | +23,242 | 0.050 |
| HB_REV_s40_r1.0_L7 | -0.67 | -2.18 | -2.6 | 691 | 0.43 / 0.36 / 0.06 / 0.15 | -3,715 | +1,372 | 31,710 | +40,674 | 0.076 |
| HB_REV_s40_r1.5_L4 | -1.38 | -2.92 | -3.6 | 691 | 0.46 / 0.24 / 0.09 / 0.21 | -2,843 | -2,331 | 26,790 | +29,767 | 0.061 |
| HB_REV_s40_r1.5_L7 | -1.38 | -2.92 | -3.6 | 691 | 0.46 / 0.24 / 0.09 / 0.21 | -4,975 | +1,168 | 34,282 | +52,093 | 0.083 |
| HB_VWAP_k1.5_L4 | +0.83 | -0.34 | -0.3 | 604 | 0.22 / 0.40 / 0.24 / 0.14 | -331 | +3,525 | 37,661 | -12,848 | 0.050 |
| HB_VWAP_k1.5_L7 | +0.83 | -0.34 | -0.3 | 604 | 0.22 / 0.40 / 0.24 / 0.14 | -578 | +4,871 | 40,611 | +7,414 | 0.079 |
| HB_VWAP_k1.25_L4_NB | +1.15 | -0.20 | -0.1 | 604 | 0.25 / 0.39 / 0.23 / 0.13 | -192 | +3,715 | 37,371 | +962 | 0.056 |
| HB_VWAP_k2.0_L4_NB | +0.37 | -0.83 | -1.0 | 604 | 0.17 / 0.41 / 0.26 / 0.16 | -803 | +2,078 | 37,391 | -4,277 | 0.063 |
| HB_OR_s30_L4 | +1.13 | +0.90 | +6.6 | 130 | 0.32 / 0.39 / 0.11 / 0.18 | +878 | +3,293 | 26,615 | -15,531 | 0.063 |
| HB_OR_s30_L7 | +1.13 | +0.90 | +6.6 | 130 | 0.32 / 0.39 / 0.11 / 0.18 | +1,537 | +1,560 | 28,859 | -27,179 | 0.089 |
| HB_OR_s20_L4_NB | +0.83 | +0.50 | +3.7 | 130 | 0.43 / 0.45 / 0.06 / 0.06 | +485 | +683 | 14,495 | -8,987 | 0.063 |
| HB_OR_s40_L4_NB | +1.36 | +1.00 | +7.3 | 130 | 0.27 / 0.31 / 0.17 / 0.25 | +973 | +2,082 | 28,870 | -15,553 | 0.092 |
| HB_PV_s30_L4 | -0.02 | -0.11 | -1.1 | 77 | 0.51 / 0.34 / 0.06 / 0.09 | -111 | +614 | 3,428 | -15,086 | 0.134 |
| HB_PV_s30_L7 | -0.02 | -0.11 | -1.1 | 77 | 0.51 / 0.34 / 0.06 / 0.09 | -193 | +215 | 15,047 | -18,706 | 0.143 |
| HB_PV_s20_L4_NB | +0.07 | -0.04 | -0.2 | 77 | 0.56 / 0.38 / 0.04 / 0.03 | -36 | +512 | 3,390 | -2,125 | 0.129 |
| HB_PV_s40_L4_NB | -0.22 | -0.43 | -4.8 | 77 | 0.51 / 0.29 / 0.08 / 0.13 | -414 | -368 | 13,184 | -9,186 | 0.143 |
| HB_REB_w15_L4 | +0.95 | -0.03 | +0.2 | 395 | 0.28 / 0.17 / 0.30 / 0.25 | -29 | -3,478 | 29,042 | -2,468 | 0.062 |
| HB_REB_w15_L7 | +0.95 | -0.03 | +0.2 | 395 | 0.28 / 0.17 / 0.30 / 0.25 | -50 | -4,559 | 38,215 | +51,167 | 0.076 |
| HB_REB_w30_L4 | +0.57 | -0.46 | -0.7 | 426 | 0.28 / 0.17 / 0.30 / 0.24 | -443 | -4,079 | 28,126 | -5,369 | 0.067 |
| HB_REB_w30_L7 | +0.57 | -0.46 | -0.7 | 426 | 0.28 / 0.17 / 0.30 / 0.24 | -776 | -3,663 | 38,493 | +44,375 | 0.081 |

The full-sequence column is NOT a clean measure of the book: the book's P&L enters the day-cap / give-back / week-floor locks and shifts which D2 trades survive, which moves the weekly mean by a few $k either way and the maxDD by tens of $k, irrespective of the book's own edge (compare the 'lock-feedback shift' and its weekly SD against the additive columns). The paired per-event test is the decision basis (V2 s2b); the full-sequence maxDD is reported as the directive requires and flagged as lock-chaos dominated.

## Long / short, ST / HM and session decomposition (WF-PRE, contribution in pts per ALL events; book trade side = long/short)
| cell | long: trades / contrib pts per event / mean pts per trade | short: trades / contrib pts per event / mean pts per trade | ST: trades / contrib pts per event / mean pts per trade | HM: trades / contrib pts per event / mean pts per trade | ASIA: trades / contrib pts per event / mean pts per trade | LONDON: trades / contrib pts per event / mean pts per trade | NY: trades / contrib pts per event / mean pts per trade | after_long_stop: trades / contrib pts per event / mean pts per trade | after_short_stop: trades / contrib pts per event / mean pts per trade |
|---|---|---|---|---|---|---|---|---|---|
| HB_REV_s20_r1.0_L7 | 345 / -0.78 / -2.1 | 346 / -1.18 / -3.1 | 382 / -1.43 / -3.4 | 309 / -0.52 / -1.5 | 163 / -0.23 / -1.3 | 259 / -0.68 / -2.4 | 269 / -1.04 / -3.5 | 346 / -1.18 / -3.1 | 345 / -0.78 / -2.1 |
| HB_REV_s20_r1.5_L7 | 345 / -0.89 / -2.4 | 346 / -1.69 / -4.4 | 382 / -1.89 / -4.5 | 309 / -0.69 / -2.0 | 163 / -0.26 / -1.5 | 259 / -1.06 / -3.7 | 269 / -1.26 / -4.3 | 346 / -1.69 / -4.4 | 345 / -0.89 / -2.4 |
| HB_REV_s30_r1.0_L7 | 345 / -0.81 / -2.1 | 346 / -1.71 / -4.5 | 382 / -1.93 / -4.6 | 309 / -0.58 / -1.7 | 163 / -0.13 / -0.7 | 259 / -1.07 / -3.8 | 269 / -1.31 / -4.5 | 346 / -1.71 / -4.5 | 345 / -0.81 / -2.1 |
| HB_REV_s30_r1.5_L7 | 345 / -0.65 / -1.7 | 346 / -2.33 / -6.1 | 382 / -2.23 / -5.3 | 309 / -0.76 / -2.2 | 163 / -0.08 / -0.4 | 259 / -1.23 / -4.3 | 269 / -1.68 / -5.7 | 346 / -2.33 / -6.1 | 345 / -0.65 / -1.7 |
| HB_REV_s40_r1.0_L7 | 345 / -0.27 / -0.7 | 346 / -1.91 / -5.0 | 382 / -1.18 / -2.8 | 309 / -1.01 / -3.0 | 163 / +0.37 / +2.1 | 259 / -1.32 / -4.7 | 269 / -1.23 / -4.2 | 346 / -1.91 / -5.0 | 345 / -0.27 / -0.7 |
| HB_REV_s40_r1.5_L7 | 345 / -0.88 / -2.3 | 346 / -2.04 / -5.4 | 382 / -2.26 / -5.4 | 309 / -0.66 / -2.0 | 163 / +0.28 / +1.6 | 259 / -2.13 / -7.5 | 269 / -1.08 / -3.6 | 346 / -2.04 / -5.4 | 345 / -0.88 / -2.3 |
| HB_VWAP_k1.5_L7 | 313 / -0.37 / -1.1 | 291 / +0.03 / +0.1 | 317 / +0.50 / +1.5 | 287 / -0.84 / -2.7 | 137 / -0.63 / -4.2 | 239 / +0.23 / +0.9 | 228 / +0.06 / +0.2 | 298 / +0.08 / +0.2 | 306 / -0.42 / -1.3 |
| HB_OR_s30_L7 | 55 / +0.73 / +12.0 | 75 / +0.18 / +2.2 | 64 / +0.46 / +6.5 | 66 / +0.44 / +6.1 | 34 / +0.17 / +4.6 | 48 / +0.33 / +6.2 | 48 / +0.40 / +7.6 | 58 / +0.93 / +14.7 | 72 / -0.03 / -0.4 |
| HB_PV_s30_L7 | 39 / +0.04 / +0.9 | 38 / -0.15 / -3.7 | 41 / -0.06 / -1.2 | 36 / -0.06 / -1.5 | 5 / -0.01 / -0.9 | 23 / -0.19 / -7.6 | 49 / +0.08 / +1.5 | 46 / -0.27 / -5.4 | 31 / +0.16 / +4.7 |
| HB_REB_w15_L7 | 182 / -0.24 / -1.2 | 213 / +0.21 / +0.9 | 214 / -0.06 / -0.3 | 181 / +0.03 / +0.2 | 85 / +0.15 / +1.6 | 145 / -1.04 / -6.6 | 165 / +0.86 / +4.8 | 182 / -0.24 / -1.2 | 213 / +0.21 / +0.9 |
| HB_REB_w30_L7 | 195 / -0.62 / -2.9 | 231 / +0.17 / +0.7 | 225 / +0.16 / +0.7 | 201 / -0.62 / -2.8 | 90 / +0.20 / +2.0 | 156 / -1.20 / -7.0 | 180 / +0.55 / +2.8 | 195 / -0.62 / -2.9 | 231 / +0.17 / +0.7 |

(lots-7 cells shown; lots-4 cells have identical points.)

## Look-ahead audit (hb_audit.py, truncation invariance)
300 sampled WF-PRE/IS events x 11 rules, cuts 2 s..3 h and (second pass) 2 s..25 min after the stop fill, all 1-s data, bars, prefix sums and the next-stop time after the cut replaced by NaN or noise: REV, VWAP, ZONE OR, ZONE PV, REBREAK w15, REBREAK w30 = 0 mismatches in both passes; planted look-ahead controls flagged (hindsight reversal 7 and 21, future-bar VWAP 1 and 2, hindsight re-break 5 and 15 mismatches; the planted 'OR with future bars' control never entered before its cut, i.e. it was not exercised). Files: hb/out/HB_audit.json, HB_audit_short.json.

## Pre-holdout status per cell
Cells that could still be CANDIDATE/PASS if the holdout sign agrees: HB_OR_s30_L7.
All other cells are DEAD irrespective of the holdout (they fail mean-up and/or the placebo and/or neighbours already on WF-PRE).

## Pre-holdout reading (WF-PRE only)
1. (a) Reversing at the stop: all 12 cells are negative on the paired test (-2.0 to -3.0 pts/event, i.e. -$156 to -$418 per stop-out event, -$1.9k to -$5.1k per week standalone); 9 of 12 have a CI excluding zero on the negative side and the placebo rank is 0.01-0.10, so stop-out timing is WORSE than random timing for this entry. Even at ZERO cost the gross edge is negative (-0.5 to -1.4 pts/event): the stop-run does not continue, if anything it gives back. Detectable effect for these cells is 1.7-3.5 pts/event: the negative effects of the S20/S30 cells are larger than that, the S40 R1.0 cell (-2.2 vs MDE 3.1) and S40 R1.5 are at the edge.
2. (b) VWAP reversion: net -0.2 to -0.8 pts/event (MDE 3.1-3.5), gross +0.4 to +1.2 at zero cost: the whole gross edge is eaten by fills; CI includes zero, placebo 0.77-0.91. Null with MDE ~3.2 pts/event: a +2 pts/event effect could not have been seen reliably.
3. (c) Zones: opening range re-entry +0.5 to +1.0 pts/event (130 trades in 912 events; 36% of triggers are removed by the opposite-side filter), placebo 0.99-1.00, neighbours agree in sign, CI of the s30 cell [+0.03, +1.84] just excludes zero but the effect (0.9) is below the cell's MDE (1.3): suggestive, not established; the gain is concentrated in re-entries after LONG stops (long book trades +12 pts/trade, 55 trades). Prior-value re-entry: zero (-0.1 pts/event, placebo 0.18-0.47).
4. (d) Re-break in the original direction: zero (-0.03 and -0.46 pts/event, MDE 3.7): gross +0.6 to +1.0 at zero cost, eaten by fills; null with MDE 3.7 pts/event.
5. Full-sequence maxDD and weekly means are dominated by lock feedback (book P&L shifts D2's lock states): weekly SD of the interaction $3k-$38k and maxDD moves of tens of $k with no relation to the book's edge; they cannot confirm or refute a 1-2 pt/event effect.
6. The only cell that can still reach CANDIDATE in this window if the holdout sign agrees is HB_OR_s30_L7 (its lots-4 twin fails 2x-cost sign / year share via the lock-chaos full-sequence series).
