# TH_STATE_BASE_S1B - engine base S1b: replica engine ITER14 + tick bar close with TH-L2-S as the live L2 cut
**Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched; in-sample base; PRE-PROOF**

Status: S1b-COMB 43 months DONE; references with 43 months: NOCUT, HOLD, S1-UNIF, S1-LIVE. Private tree /mnt/l2/l2vast/_th_state/base_b/ (G recorder off). Supersedes S1 (timer close) as base of record (lead decision 2026-11-09); S1 files untouched. Seal manifest_after.json sha256 759f2258daac9d28.

## 1. What the base is
- Engine: S1 (autopilot/TH_STATE_BASE_S1.md section 1) with ONE change: prm BAR_CLOSE='tick' (NT8 closes a time bar on the first tick of the next bar; ENTRY_MATCH.md F1) via code/th_redo/state_base_b.py (new copy). Everything else (state cut, specs, ITER14_PRM, HIST_PRM, 10 warm days, monthly chunks 2023-04..2026-10) as S1.
- Inert in history and not ported: half-even TrendSize rounding (blind-week old panel only), X-book volume/range bar rules (X books off).
- References rebuilt with the same adapter and tick: NOCUT (arm=1e9), PLAIN6060, HOLD (old per-print live cut), S1b-UNIF, S1b-LIVE.

## 2. Per-book policy table (S1-COMB) - ARM pts / MULT / W s / PERS s / newMae / arm variant
| book | ARM | MULT | W | PERS | newMae | variant |
|---|---|---|---|---|---|---|
| K7 | 45 | 10 | 2 | 3 | off | V2 clip(ARM*sqrt(lots/4),15,50) |
| P7 | 45 | 5 | 5 | 10 | off | V0 fixed points |
| M7 | 30 | 10 | 2 | 2 | off | V0 fixed points |
| U7 | 30 | 60 | 15 | 5 | off | V2 clip(ARM*sqrt(lots/4),15,50) |
| A7 | 30 | 60 | 15 | 3 | off | V0 fixed points |
| H7 | 15 | 30 | 10 | 2 | on | V1 clip(ARM*sqrt(4/lots),15,50) |
| O7 | 25 | 20 | 10 | 10 | off | V0 fixed points |
| P7_0 (session override, entry session asia) | 50 | 5 | 3 | 3 | on | V1 clip(ARM*sqrt(4/lots),15,50) |
| H7_3 (session override, entry session nyam) | 35 | 20 | 2 | 1 | off | V2 clip(ARM*sqrt(lots/4),15,50) |

S1-UNIF (one cell for every book): ARM 30 / MULT 10 / W 5 / PERS 10 / newMae on / V0 fixed points. S1-LIVE: 30/30/5/1/newMae on state.

## 3. Regression
- S1B_BAR_CLOSE=timer, month 202304: identical to S1-COMB 202304 (all columns, 246 trades).
- Per-month trade counts / net per base: base_b/<base>/<yyyymm>/trades.parquet; month diff S1b vs S1: base_b/month_diff.csv.

## 4. Window metrics (USD/week, net of the 4.84 fee proxy, carrying week dropped; windows as of 2026-10-31; delta = S1b-COMB minus the like-for-like reference)
| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| S1b-COMB vs never-cut | +9184 | +8476 | +6532 | +7290 | +6246 | +8032 | +1599 | +772 |
| S1b-COMB vs never-cut MDE | +17248 | +12959 | +12896 | +10176 | +6998 | +14081 | +4255 | +2860 |
| S1b-COMB vs HOLD-old-cut | -1881 | -3610 | +1960 | +2912 | +3106 | +4682 | +7426 | -3617 |
| S1b-COMB vs HOLD-old-cut MDE | +10556 | +11634 | +10674 | +12255 | +8660 | +19612 | +5629 | +6162 |
| S1b-COMB vs S1b-UNIF | +10579 | +6437 | +11266 | +9233 | +6104 | +1585 | -914 | +479 |
| S1b-COMB vs S1b-UNIF MDE | +22541 | +19521 | +14996 | +10473 | +8147 | +10593 | +4630 | +2936 |
| S1b-COMB vs S1b-LIVE (live cell on state) | +9436 | +6270 | +8804 | +5914 | +5587 | +5731 | +1526 | +617 |
| S1b-COMB vs S1b-LIVE (live cell on state) MDE | +15537 | +15417 | +12175 | +9903 | +7127 | +14134 | +4191 | +2854 |
| S1b-COMB level (weekly net) | +301 | +11198 | +9891 | +20791 | +14815 | +4801 | +12266 | -529 |
| never-cut level (weekly net) | -8883 | +2722 | -1574 | +10938 | +9758 | +397 | +14046 | -476 |
| HOLD-old-cut level (weekly net) | +2182 | +8162 | +3501 | +15752 | +12905 | +4690 | +5781 | +2822 |
| S1b-UNIF level (weekly net) | -10277 | -2959 | -7313 | +8707 | +10105 | +8002 | +12540 | -123 |
| S1b-LIVE (live cell on state) level (weekly net) | -9135 | -1880 | -4889 | +12008 | +10426 | +3233 | +11466 | -321 |

PLAIN6060 was not rebuilt with tick (lead order: plain 60/60 == never-cut in the months compared; use the NOCUT rows). Delta MDE = 2.8 sd/sqrt(n). Level rows are the same weekly-net convention as the window deltas (carrying week dropped), so they differ from the plain-mean levels printed in TH_STATE_BASE_S1.md.

## 5. Files
- code sha256:
  - c43652542ef6e1f0b2dbe10a754efb4fd52ad64ed93e8fef05c62bca210d7af3  th_redo/state_base_b.py
  - ef51c890b123c0da762551a1aa929e73644ca537802a929c07f09a070c163c09  th_redo/state_base_b_md.py
  - be6c1a516469efea88cdc48f77ebe3a35531bd98f2a279f3a44e020fabc3b5e6  th_redo/s1b_diff.py
  - ec4ed9fbd5bb009ee749818f5fc129fd00bb9ab0a20a56c6fca32d4981e6d640  th_redo/adapter_replica.py
  - 4838268b544e24654244d173e72fe87f950fb6a5aefe1797b2e1f63cf63b30e8  th_redo/rules_replica.py
  - ae67737c61be240b8607c9cde44eabae2a1cc1c26b3e51b69d7ec0f90513db38  hist_pipe/hist_adapter.py
  - 659c046c506c5ced90457eac2202fd17e1f3823ddc4e05d6329f748684bd0c11  th_state_score/s2eval.py
  - ce68f510167e94fa86e9da28c2d587e393f714f2c99db3e2e64d37c29ef75058  th_state_score/common.py
- trade lists (per month trades.parquet):
  - S1-COMB: 43 months, dir /mnt/l2/l2vast/_th_state/base_b/S1-COMB/, sha-of-shas 92003c0965bb4f49
  - NOCUT: 43 months, dir /mnt/l2/l2vast/_th_state/base_b/NOCUT/, sha-of-shas acc8bf2e5172584c
  - PLAIN6060: 18 months, dir /mnt/l2/l2vast/_th_state/base_b/PLAIN6060/, sha-of-shas 89b40d14afd3e46a
  - HOLD: 43 months, dir /mnt/l2/l2vast/_th_state/base_b/HOLD/, sha-of-shas cfa609f6a945b6fa
  - S1-UNIF: 43 months, dir /mnt/l2/l2vast/_th_state/base_b/S1-UNIF/, sha-of-shas a133f6d29ab37eeb
  - S1-LIVE: 43 months, dir /mnt/l2/l2vast/_th_state/base_b/S1-LIVE/, sha-of-shas 23455eccaeddf78e
- usage: S1B_BAR_CLOSE=tick (default) python3 -I code/th_redo/state_base_b.py run <S1-COMB|S1-UNIF|S1-LIVE|NOCUT|HOLD|PLAIN6060> <yyyymm,..|a-b> <workers> --norec
- diff vs S1: B/month_diff.csv, B/window_diff.csv (s1b_diff.py).
