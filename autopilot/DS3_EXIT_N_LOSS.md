# DS3_EXIT_N_LOSS - T-EXIT-N E1, LOSS SIDE (S4a)

STATUS 2026-11-02 17:28Z: first table. Prereg autopilot/ZL_S4A_PREREG_EXIT_N_LOSS.md sha256 1ba0d3c23f262eeec067abc9b9f1dafddd7b938923e9ed5efa49d7f77159254f (DECISIONS.md). POST-HOC, Shadow only, no PASS claim. Base = V13T_LIVE (code/d7base/d7_v13t.py run_v13t_live: take lines empty, lock none = per-book locks, market exits 0.80 pt, stops 2.45 pt worse than nominal, targets at nominal, resting add cancelled on any exit). Reference cell = the SHIPPED TH-L2 loss cut (-30 pts / 5 s / 30x) on this base; every cut below is vs that reference, maxDD of the weekly cumulative total. Reference maxDD $k: L6M 151, HOLD 151, MID 44, PRE 166, X 92; weekly mean $: L6M 36747, HOLD 30405, MID 24008, PRE 17285, X 4801.

## 0. Plain sentences

* The shipped loss cut is a drawdown protector, not a profit tool: removing it makes maxDD worse in every window (L6M -0.31, HOLD -0.31, MID -2.90, PRE -0.70, X' -0.35) while costing only -1728 $/wk of mean (MDE 6929).
* Of 94 alternative cells, 3 lower maxDD AND improve worst-20 in BOTH L6M and PRE on the single path: A arm30 pull50x w10s (cut L6M +0.18, PRE +0.01, X' -0.07, mean -487 $/wk); B flip K2 arm30 (cut L6M +0.04, PRE +0.07, X' -0.10, mean -415 $/wk); B flip SWP arm30 (cut L6M +0.21, PRE +0.09, X' -0.07, mean -450 $/wk). None of them is above the Z3 phase-averaged band in L6M AND (PRE or X') (section 4), so none is a lead.
* TIME-STOPS (no progress at <= 0 after 5/10/20/30 min) are harmful on true fills: mean change -18767 to -13099 $/wk and worse maxDD in nearly every window (they give up trades that come back). The exact U7 blackout (SM only, same side) has zero effect ('never binds'); the all-books both-sides blackout is mixed and costs $/wk.

* FLOW-GATED replacement cuts on the 1-s path (sweep-against and iceberg-ahead, arms 15-40, S4b's flow arrays) are worse than the shipped cut in L6M and HOLD in all 12 cells (best L6M cut -0.14, median -0.32) and cost -14698 to -1078 $/wk: these flags are present on 40,000 of the 88,490 rows, so they are not selective. Delta-turn and large-print-against are S4b's (E2c).

## 1. F-A threshold grid (40 cells): maxDD cut vs the shipped cell, L6M | PRE | X' (single path, lock none)

| arm pts | pulled x | w 5 s: L6M / PRE / X' | w 10 s: L6M / PRE / X' |
|--|--|--|--|
| 20 | 10 | +0.05 / +0.21 / -0.00 | +0.05 / +0.22 / +0.03 |
| 20 | 20 | +0.04 / +0.19 / -0.14 | +0.05 / +0.21 / +0.03 |
| 20 | 30 | -0.02 / +0.21 / -0.18 | +0.05 / +0.18 / -0.04 |
| 20 | 50 | +0.07 / +0.15 / +0.11 | +0.02 / +0.13 / -0.42 |
| 25 | 10 | -0.23 / +0.13 / +0.17 | -0.27 / +0.14 / +0.15 |
| 25 | 20 | -0.13 / +0.11 / +0.00 | -0.28 / +0.13 / +0.09 |
| 25 | 30 | -0.50 / +0.08 / +0.08 | -0.23 / +0.11 / +0.10 |
| 25 | 50 | -0.09 / -0.04 / +0.12 | -0.31 / +0.06 / -0.13 |
| 30 | 10 | +0.03 / +0.09 / -0.10 | +0.04 / +0.09 / -0.05 |
| 30 | 20 | +0.00 / +0.07 / -0.01 | +0.04 / +0.08 / -0.09 |
| 30 | 30 | +0.00 / +0.00 / +0.00 | +0.03 / +0.08 / -0.14 |
| 30 | 50 | +0.37 / -0.27 / +0.15 | +0.18 / +0.01 / -0.07 |
| 35 | 10 | -0.71 / -0.24 / -0.15 | -0.60 / -0.26 / -0.13 |
| 35 | 20 | -0.73 / -0.25 / -0.01 | -0.71 / -0.24 / -0.03 |
| 35 | 30 | -0.70 / -0.19 / +0.21 | -0.71 / -0.24 / -0.10 |
| 35 | 50 | -0.42 / -0.44 / +0.22 | -0.70 / -0.26 / +0.04 |
| 40 | 10 | -0.41 / -0.33 / -0.22 | -0.41 / -0.33 / -0.20 |
| 40 | 20 | -0.43 / -0.30 / -0.07 | -0.41 / -0.33 / -0.10 |
| 40 | 30 | -0.44 / -0.38 / -0.08 | -0.41 / -0.31 / +0.16 |
| 40 | 50 | -0.56 / -0.18 / +0.05 | -0.45 / -0.38 / +0.05 |

## 2. F-B flip-against (30 cells; no pulled gate): cut L6M / PRE / X', mean change $/wk

| combo | arm | cut L6M | HOLD | MID | PRE | X' | w20 change L6M $k | w20 change PRE $k | mean $/wk (MDE) |
|--|--|--|--|--|--|--|--|--|--|
| ICE | 15 | +0.20 | +0.20 | +0.14 | +0.15 | -0.30 | -60 | +252 | -7513 (6694) |
| ICE | 20 | -0.10 | -0.10 | -0.22 | +0.20 | -0.05 | -93 | +164 | -5554 (5604) |
| ICE | 25 | -0.07 | -0.07 | +0.21 | +0.05 | +0.08 | -99 | +92 | -3799 (4321) |
| ICE | 30 | +0.00 | +0.00 | +0.02 | +0.04 | -0.09 | -5 | +28 | -281 (2362) |
| ICE | 35 | -0.52 | -0.52 | +0.18 | -0.22 | +0.01 | -77 | -76 | +1848 (3772) |
| ICE | 40 | -0.47 | -0.47 | -0.76 | -0.33 | -0.11 | -141 | -107 | +1984 (4850) |
| IMB | 15 | +0.31 | +0.08 | -0.33 | -0.21 | -0.42 | -101 | -5 | -4033 (5086) |
| IMB | 20 | -0.35 | -0.35 | -0.26 | -0.08 | -0.84 | -250 | +41 | -2833 (4860) |
| IMB | 25 | -0.32 | -0.32 | -0.23 | -0.24 | -0.98 | -184 | -78 | -1323 (4947) |
| IMB | 30 | -0.45 | -0.45 | -0.59 | -0.42 | -0.71 | -133 | -154 | +458 (5272) |
| IMB | 35 | -0.47 | -0.47 | -0.50 | -0.35 | -1.37 | -210 | -138 | +508 (6215) |
| IMB | 40 | -0.34 | -0.34 | -1.21 | -0.52 | -0.83 | -166 | -166 | +659 (6530) |
| K2 | 15 | +0.26 | +0.26 | +0.06 | +0.22 | -0.26 | -31 | +235 | -7659 (6641) |
| K2 | 20 | +0.13 | -0.11 | -0.23 | +0.18 | +0.01 | -57 | +148 | -5372 (5542) |
| K2 | 25 | -0.12 | -0.12 | +0.12 | +0.04 | +0.14 | -103 | +84 | -3894 (4239) |
| K2 | 30 | +0.04 | +0.04 | +0.06 | +0.07 | -0.10 | +11 | +24 | -415 (2568) |
| K2 | 35 | -0.53 | -0.53 | +0.20 | -0.23 | +0.01 | -86 | -105 | +1192 (4017) |
| K2 | 40 | -0.56 | -0.56 | -0.75 | -0.34 | -0.14 | -150 | -129 | +1633 (4893) |
| SWP | 15 | +0.29 | +0.19 | -0.74 | +0.31 | -0.20 | -112 | +254 | -7945 (7226) |
| SWP | 20 | +0.01 | -0.12 | -0.56 | +0.22 | +0.01 | -83 | +151 | -5487 (6023) |
| SWP | 25 | -0.36 | -0.36 | -0.21 | +0.14 | +0.13 | -192 | +60 | -4633 (4564) |
| SWP | 30 | +0.21 | +0.15 | +0.00 | +0.09 | -0.07 | +17 | +76 | -450 (2284) |
| SWP | 35 | -0.60 | -0.60 | -0.25 | -0.24 | -0.13 | -149 | -71 | -270 (3839) |
| SWP | 40 | -0.44 | -0.44 | -0.07 | -0.33 | -0.20 | -54 | -115 | +2616 (4505) |
| WG | 15 | -0.85 | -0.85 | -2.14 | -0.32 | -0.62 | -279 | -163 | -5275 (6298) |
| WG | 20 | -0.57 | -0.57 | -1.94 | -0.36 | -0.22 | -206 | -172 | -3451 (6092) |
| WG | 25 | -0.23 | -0.42 | -2.20 | -0.37 | -0.38 | -244 | -162 | -3131 (6136) |
| WG | 30 | -0.11 | -0.36 | -2.76 | -0.40 | -0.35 | -158 | -217 | -2453 (6490) |
| WG | 35 | -0.30 | -0.30 | -2.86 | -0.62 | +0.02 | -216 | -256 | -2612 (6933) |
| WG | 40 | -0.31 | -0.31 | -3.09 | -0.58 | +0.01 | -254 | -203 | -1954 (6934) |

## 2b. F-B2 flow-gated cut on the 1-s path (sweep against / iceberg ahead; replaces the shipped cut)

| cell | cut L6M | HOLD | MID | PRE | X' | w20 change L6M $k | w20 change PRE $k | mean $/wk (MDE) |
|--|--|--|--|--|--|--|--|--|
| B2 flow SWPF arm20 | -0.14 | -0.87 | -3.28 | +0.01 | -0.12 | -223 | +195 | -11263 (6855) |
| B2 flow SWPF arm30 | -0.19 | -0.35 | -1.37 | +0.06 | +0.04 | -211 | +22 | -5874 (3791) |
| B2 flow SWPF arm40 | -0.58 | -0.58 | +0.54 | -0.41 | -0.38 | -71 | -205 | -1078 (4412) |
| B2 flow ICEF arm20 | -0.19 | -0.76 | -3.18 | -0.03 | -0.13 | -211 | +187 | -11201 (6749) |
| B2 flow ICEF arm30 | -0.14 | -0.35 | -1.38 | -0.03 | +0.03 | -181 | -1 | -6005 (3732) |
| B2 flow ICEF arm40 | -0.61 | -0.61 | +0.41 | -0.42 | -0.39 | -81 | -208 | -1286 (4458) |
| B2 flow SWPF arm15 | -0.24 | -0.96 | -3.13 | -0.47 | -0.19 | -360 | +167 | -14698 (7850) |
| B2 flow SWPF arm25 | -0.58 | -0.58 | -1.44 | -0.26 | -0.14 | -310 | +80 | -8892 (5315) |
| B2 flow SWPF arm35 | -0.40 | -0.40 | -0.14 | -0.34 | -0.63 | -143 | -93 | -3707 (3516) |
| B2 flow ICEF arm15 | -0.23 | -0.96 | -3.11 | -0.44 | -0.21 | -339 | +183 | -14035 (7876) |
| B2 flow ICEF arm25 | -0.44 | -0.47 | -1.57 | -0.27 | -0.13 | -273 | +84 | -8573 (5335) |
| B2 flow ICEF arm35 | -0.42 | -0.42 | -0.20 | -0.32 | -0.65 | -148 | -92 | -3737 (3484) |

## 3. F-C time-stops and F-D blackouts

| cell | cut L6M | HOLD | MID | PRE | X' | mean $/wk (MDE) |
|--|--|--|--|--|--|--|
| C time-stop 10min | -0.20 | -0.75 | -2.38 | -0.40 | -0.80 | -17398 (8388) |
| C time-stop 30min | -0.21 | -0.29 | -0.58 | -1.13 | -1.02 | -13099 (6800) |
| D blackout exact 30min | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 | +0 (0) |
| D blackout assumed 15min | +0.02 | +0.02 | -0.03 | -0.01 | +0.02 | -425 (963) |
| D blackout assumed 60min | +0.06 | +0.06 | -0.05 | -0.17 | -0.65 | -3463 (3732) |
| C time-stop 5min | -0.04 | -1.13 | -2.81 | -0.26 | -0.32 | -18767 (8908) |
| C time-stop 20min | -0.17 | -0.45 | -2.03 | -0.24 | -1.59 | -14116 (7371) |
| D blackout exact 15min | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 | +0 (0) |
| D blackout exact 60min | -0.02 | -0.02 | +0.00 | +0.00 | +0.00 | -19 (40) |
| D blackout assumed 30min | -0.02 | -0.02 | -0.23 | +0.15 | -0.13 | -1529 (1994) |
| D blackout off 0min | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 | +0 (0) |

## 4. Candidates: phase-averaged (K=9) cuts vs the Z3 V13T PA9 FINAL band (flip-5 values, because every E1 cell acts on far more than 3.5 % of rows: L6M .219, PRE .099, X' .182), dollar no-harm, two-episode

| cell | PA cut L6M | HOLD | MID | PRE | X' | min phase L6M/PRE/X' | band rule | no-harm ($) | two-episode (V13T ref episodes) | placebo ranks (A/B/C, n) |
|--|--|--|--|--|--|--|--|--|--|--|
| A arm30 pull50x w10s | +0.17 | +0.16 | -0.02 | +0.03 | -0.18 | +0.15/+0.01/-0.30 |  | yes | ONE | A 0.39 (n100) |
| B flip K2 arm30 | +0.10 | +0.10 | -0.26 | +0.05 | -0.16 | +0.02/+0.04/-0.19 |  | yes | ONE | A 0.50 (n100) |
| B flip K2 arm20 | +0.21 | +0.11 | -0.77 | +0.26 | -0.07 | +0.13/+0.18/-0.12 |  | yes | OK |  |
| A arm20 pull10x w10s | +0.15 | +0.14 | -1.07 | +0.30 | +0.05 | +0.05/+0.22/-0.09 |  | yes | OK |  |
| B flip IMB arm15 | +0.14 | +0.12 | -0.30 | -0.16 | -0.36 | -0.02/-0.34/-0.57 |  | NO | ONE |  |
| A arm25 pull30x w5s | -0.21 | -0.21 | -0.30 | +0.04 | -0.00 | -0.50/-0.02/-0.12 |  | NO | OK |  |
| B flip SWP arm30 | +0.19 | +0.17 | +0.01 | +0.08 | -0.13 | +0.17/+0.03/-0.15 |  | yes | ONE | A 0.50 (n100), B 0.01 (n100), C 0.05 (n100) |
| A arm30 pull50x w5s | +0.27 | +0.23 | +0.08 | -0.19 | +0.10 | +0.19/-0.27/+0.05 |  | NO | ONE |  |
| B flip SWP arm15 | +0.41 | +0.31 | -1.40 | +0.32 | -0.19 | +0.29/+0.31/-0.32 | YES | NO | OK |  |
| B flip K2 arm15 | +0.35 | +0.35 | -0.43 | +0.23 | -0.33 | +0.26/+0.19/-0.39 | YES | NO | OK |  |
| A arm20 pull50x w5s | +0.15 | +0.14 | -0.81 | +0.12 | +0.05 | +0.07/+0.06/-0.05 |  | yes | OK |  |
| B flip ICE arm15 | +0.32 | +0.32 | -0.38 | +0.15 | -0.30 | +0.20/+0.11/-0.44 | YES | NO | OK |  |

Band rule: PA cut above the band in L6M AND in PRE or X' (flip-5 band of DS3_ZONES_3_NOISE_V13T_FINAL.md). No-harm: no window's PA maxDD increase exceeds max(band x base maxDD, 0.5 x base weekly SD) and the PA mean change over ALL is not below minus the paired MDE. Placebos carry the same cost model (the engine path is identical): A random cut trades same count per day among trades that reach the same adverse threshold; B same total count among such trades; C the per-day counts moved to random other days.


## 5. Equal-risk and book x session for the three near cells (addendum 2; REPLACE-mode alternatives to the shipped cut; own engine path with the K-table cuts, which ties by construction)

Equal-risk = lot scale so ALL worst-20 equals the shipped cell's. The S5 harness route was tried (K-table cut sets injected as 'cut' rows with the shipped cut off) and its output is INVALID: with th_loss off the engine dropped the injected exits in that configuration, so the harness numbers equalled the no-cut base (audit by S4b, DS3_EXIT_N_AUDIT.md section 4); the file is renamed e1_harness_INVALID.pkl and no number of this page comes from it; so the final numbers of these three cells use the engine's own th_loss path and the harness is used only for the cells that are native injections (flow-gated, time).

| cell | lot scale c | equal-risk cut L6M | HOLD | PRE | X' | equal-risk mean change $/wk (ALL) | mean change at c=1 $/wk |
|--|--|--|--|--|--|--|--|
| B flip SWP arm30 | 1.13 | +0.30 | +0.16 | +0.02 | -0.01 | +1729 | -450 |
| A arm30 pull50x w10s | 1.00 | +0.18 | +0.15 | +0.01 | -0.07 | -487 | -487 |
| B flip K2 arm30 | 1.00 | +0.04 | +0.04 | +0.07 | -0.10 | -415 | -415 |
| B flip K2 arm20 | 1.18 | -0.04 | -0.15 | +0.04 | -0.26 | -4196 | -5372 |

**Per book x session maxDD cut of the near cells (HOLD | PRE), cell vs the shipped cell**

| cell | K7 | P7 | U7 | H7 | M7 | A6 | asia | london | pre | nyam | nypm | close |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| B flip SWP arm30 | +0.09\|-0.13 | +0.02\|+0.08 | -0.01\|+0.09 | +0.13\|+0.07 | +0.05\|-0.02 | +0.00\|+0.00 | -0.29\|+0.09 | +0.06\|+0.05 | +0.00\|+0.00 | -0.05\|+0.04 | -0.10\|-0.00 | +0.00\|+0.00 |
| A arm30 pull50x w10s | +0.06\|-0.00 | +0.00\|+0.02 | +0.00\|-0.05 | -0.11\|+0.07 | +0.06\|+0.06 | +0.00\|+0.00 | -0.32\|+0.09 | -0.05\|+0.04 | +0.00\|+0.00 | -0.12\|-0.01 | +0.01\|+0.10 | +0.00\|+0.00 |
| B flip K2 arm30 | +0.01\|+0.08 | +0.12\|-0.04 | +0.02\|-0.02 | +0.08\|+0.42 | +0.13\|-0.07 | +0.00\|+0.00 | -0.36\|-0.08 | +0.17\|-0.10 | +0.00\|+0.00 | -0.06\|+0.07 | -0.34\|+0.12 | +0.00\|+0.00 |
| B flip K2 arm20 | +0.02\|-0.45 | -0.06\|+0.05 | +0.39\|+0.29 | -0.52\|+0.32 | -0.37\|+0.21 | -0.00\|+0.00 | -0.47\|+0.09 | -0.83\|+0.13 | +0.00\|+0.00 | +0.01\|-0.05 | +0.43\|+0.54 | +0.00\|+0.00 |

## 6. Per-book same-side blackout family (hypothetical for K7/P7/H7/M7; live form = U7 same-side 30 min, which never binds), added to the exact U7 rule; vs the live reference

| book | minutes | rows blocked | cut L6M | HOLD | MID | PRE | X' | w20 change L6M / PRE $k | mean $/wk (MDE) |
|--|--|--|--|--|--|--|--|--|--|
| H7 | 15 | 24 | -0.02 | -0.02 | +0.00 | +0.01 | +0.00 | -3 / +3 | -18 (94) |
| H7 | 30 | 41 | -0.09 | -0.09 | +0.00 | +0.01 | +0.00 | -21 / +3 | -154 (304) |
| H7 | 60 | 139 | -0.06 | -0.06 | +0.04 | +0.01 | +0.00 | -25 / -4 | -210 (399) |
| K7 | 15 | 65 | +0.01 | +0.01 | +0.00 | +0.00 | +0.00 | -2 / +0 | -64 (259) |
| K7 | 30 | 244 | +0.00 | +0.00 | +0.00 | +0.00 | +0.03 | -2 / -1 | +59 (427) |
| K7 | 60 | 613 | -0.07 | -0.07 | +0.01 | +0.01 | +0.07 | -36 / +0 | -89 (674) |
| M7 | 15 | 75 | +0.06 | +0.06 | +0.00 | -0.01 | +0.00 | +8 / +0 | +3 (193) |
| M7 | 30 | 166 | +0.07 | +0.07 | +0.00 | +0.01 | +0.00 | +8 / -0 | -8 (233) |
| M7 | 60 | 443 | +0.07 | +0.07 | -0.04 | +0.01 | +0.01 | +11 / +3 | -17 (354) |
| P7 | 15 | 28 | -0.03 | -0.03 | +0.00 | -0.03 | +0.00 | -4 / -24 | -150 (345) |
| P7 | 30 | 125 | +0.17 | +0.14 | +0.00 | -0.01 | +0.00 | +12 / -12 | -325 (1269) |
| P7 | 60 | 416 | +0.27 | +0.19 | +0.12 | -0.03 | -0.17 | -33 / -31 | -818 (1861) |

Reading: no K7/P7/H7/M7 same-side blackout lowers maxDD and worst-20 in both L6M and PRE; P7 60 min gives L6M +0.27 / MID +0.12 but PRE -0.03 and X' -0.17 with worse worst-20; M7 gives +0.06..+0.07 L6M and +$8-11k worst-20 but only 75-443 blocked rows (noise-size).
