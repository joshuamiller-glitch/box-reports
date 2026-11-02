> **DEFECT BASE (V13X):** every cut, rank, lead and withdrawal on this page was computed on D7 V13X, which dropped the TH-L2 loss cut and take-line exits that came before the resting add filled (846 rows; BASE-4 fixed it in V13Y). Treat all numbers here as 'defect base (V13X)'; the V13Y re-run of the leads is in progress and will supersede them.

# DS3_ZONES_3_L2_TAPE_POC - the developing day-POC skip (TVP|poc|day, D40) under the robustness standard (ZL-2), V13X EXACT base

Cell `A40__TVP_poc_day__skip`: skip the signal when a FRESH developing Globex-day POC line (running volume POC of the label day so far, 1-pt bins, 15-min clock checkpoints after a 30-min warm-up, a new line only when the POC bin moves >= 2 bins; the last POC of the previous day stays 24 h) lies between entry and target within min(40 pts, target distance). Fires on 1,768 of 88,490 engine rows (2.0%%). Post-hoc, Shadow, no PASS.

## Verdict
* **LEAD at most; not a RISK-KEEP.** With the combined 12R stack lock the maxDD change is -23% F9 / -39% L3M / -19% L6M / -35% HOLD / -33% MID / -31% PRE / -39% X' (mean change inside MDE, STRICT + TOLERANT + NOW-ONLY pass); **with the lock off (per-book locks only) it is +2% / -13% / +2% / +3% / +19% / +4% / -13%: the Feb-Oct cut disappears** (F9, L6M, HOLD, PRE all worse than the base).
* Entry-time causality audit passed (138 of 138 skip decisions reproduced from prints before the entry second; 137/138 line levels; latest print used = entry second - 1).
* Multiplicity: best-of-N over the 580-cell screen with the same-volume placebo null: Sidak p of the best cell 0.24 (this D40 cell 0.52); 24-31 cells have p < 0.05 against 29 expected by chance.
* Definition sensitivity: the F9 (Feb-Oct) cut exists at only 8 of 19 settings (D20/D30, bin 2 pt, warm-up 15/60 min, replacement 1 bin, 25%/50% of target all lose it; D40-D60, 75% of target, bin 3 pt, checkpoint 5/30 min, replacement 3 bins and the session anchor keep it): FRAGILE on F9; the PRE and X' cuts survive nearly every variant. The Feb-Oct gain in $ is carried by two weeks (2026-03-09 and 2026-02-16 = 85% of the F9 delta).

## Lock frames (maxDD change vs the base of each frame)
| frame | base F9 maxDD | F9 | L3M | L6M | HOLD | MID | PRE | X' | STRICT/TOL/NOW |
|---|---|---|---|---|---|---|---|---|---|
| 12R combined lock (V13X headline) | 78.5k | -23% | -39% | -19% | -35% | -33% | -31% | -39% | YYY |
| lock off (per-book locks only) | 132.6k | +2% | -13% | +2% | +3% | +19% | +4% | -13% | --- |

## Definition sensitivity (V13X, lock 12R; maxDD change)
| variant | rows | F9 | L3M | L6M | HOLD | MID | PRE | X' | S/T |
|---|---|---|---|---|---|---|---|---|---|
| D20 | 1106 | -1% | -39% | -22% | -3% | -1% | -13% | -40% | - |-
| D30 | 1481 | -1% | -39% | -22% | -35% | -1% | -11% | -40% | - |-
| D40 (default) | 1768 | -23% | -39% | -19% | -35% | -33% | -31% | -39% | Y |Y
| D50 | 1978 | -23% | -39% | -19% | -35% | -33% | -33% | -38% | Y |Y
| D60 | 2162 | -24% | -39% | -19% | -49% | -33% | -32% | -37% | Y |Y
| 25% of target | 805 | -0% | -23% | -14% | -2% | -0% | -13% | -32% | - |-
| 50% of target | 1389 | -1% | -39% | -22% | -35% | -1% | -11% | -40% | - |-
| 75% of target | 1842 | -23% | -39% | -19% | -35% | -33% | -33% | -36% | Y |Y
| bin 2 pt | 1575 | -4% | +18% | -1% | -5% | -4% | -16% | -20% | - |-
| bin 3 pt | 1511 | -15% | -14% | -9% | -26% | -33% | -17% | -30% | Y |Y
| checkpoint 5 min | 1347 | -15% | -9% | -9% | -20% | -33% | -33% | -20% | - |-
| checkpoint 30 min | 2061 | -31% | -35% | -27% | -21% | -33% | -18% | -39% | Y |-
| warm-up 15 min | 1821 | -2% | -33% | -20% | -35% | -2% | -32% | -66% | - |Y
| warm-up 60 min | 1662 | -2% | -41% | -20% | -35% | -2% | -29% | -37% | Y |Y
| replacement 1 bin | 2060 | +3% | -39% | +9% | -32% | -33% | -29% | -36% | - |-
| replacement 3 bins | 1637 | -11% | -13% | -5% | -35% | -33% | -30% | -38% | Y |Y
| strictly previous second | 1677 | -23% | -39% | -19% | -35% | -33% | -18% | -39% | - |Y
| session-anchored (TVP|poc|sess) | 2495 | -19% | -30% | -14% | -43% | -34% | -37% | -12% | Y |Y
| day + session | 3491 | -21% | -29% | -16% | -43% | -33% | -37% | -10% | Y |Y

F9 cut >= 15% in 8 of 19 settings -> **FRAGILE (works at few settings only)**

## Episode-proofing
| window | key week of the base | cut | cut without the key week | min leave-one-week-out | min leave-one-month-out | bootstrap 90% CI |
|---|---|---|---|---|---|---|
| F9 | 2026-03-23 | -23% | -19% | -14% | -14% | [-54%, +3%] |
| L3M | 2026-09-07 | -39% | -37% | -0% | -0% | [-43%, +6%] |
| L6M | 2026-09-07 | -19% | -17% | +4% | +1% | [-34%, +5%] |
| HOLD | 2026-03-23 | -35% | -18% | -18% | -18% | [-53%, +4%] |
| MID | 2026-03-23 | -33% | -47% | -3% | -33% | [-44%, -27%] |
| PRE | 2025-04-14 | -31% | -26% | -19% | -7% | [-25%, +11%] |
| X' | 2024-01-29 | -39% | -36% | -27% | -23% | [-54%, -0%] |

## What the 1,768 skipped rows are
By book: DN 43, HM 112, KB 176, MA 121, MV 91, PB 244, PBL 183, PE 198, SM 51, ST 220, WT 329. By session: asia 765, close 4, london 386, nyam 348, nypm 195, pre 70. Six core books: 872 rows.
Feb-Oct weekly delta (cell - base): 18 weeks up, 9 down, total +131k; **the two weeks 2026-03-09 (+69k) and 2026-02-16 (+42k) carry 85% of it** (base maxDD week: 2026-03-30).
Per session (F9 delta mean $k/wk; base maxDD -> cell maxDD): asia +0.8 (62k->56k); london +2.4 (105k->104k); nyam +0.3 (38k->22k); nypm -0.0 (36k->37k). Vol terciles T1/T2/T3 (weeks): +9.4 (13) / +0.1 (12) / +0.6 (13).
Per book x session F9 delta ($k): KB-asia +12.6, KB-london +4.8, KB-nyam -5.9, PE-asia +12.3, PE-london +49.0, PE-nyam +21.2, SM-asia -5.9, SM-london +18.8, HM-asia +10.1, MV-london +18.3, MV-nyam -4.4

## Placebos (draws per kind; rank = share of draws with a shallower cut than the real cell is... i.e. real cut beats the draw; 1.00 = best)
| kind | draws | mean cut of the draws F9 | rank F9 | L3M | HOLD | PRE |
|---|---|---|---|---|---|---|
| same-volume random skip | 100 | +12% | 1.00 | 1.00 | 0.95 | 0.98 |
| random rows, same count per day | 100 | +7% | 1.00 | 0.99 | 0.94 | 0.99 |
| shuffled-day counts | 100 | +5% | 1.00 | 1.00 | 0.98 | 0.98 |

Delay 1 s / 3 s: not applicable to a skip decision taken at the signal second (the line state used is already as of the entry second); see the 1-s / 3-s variants in the main page for the other cells. Per-month chain: `chain_A40__TVP_poc_day__skip.csv` in /mnt/l2/l2vast/ds3_zones3_new/ZL-2/.
