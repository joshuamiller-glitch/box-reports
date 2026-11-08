# TH_STATE_BASE_S1 - engine base v-S1: replica engine (ITER14_PRM) with TH-L2-S as the live L2 cut
**Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book / UNIF); entries not live-matched; per-book procedure fails the out-of-sample walk-forward (DS3_TH_STATE.md section 5)**

Status: S1-COMB 43 months DONE (G recorder ON); S1-UNIF months done: 43/43 (complete); regression below. Private tree: /mnt/l2/l2vast/_th_state/base/ . Seal manifest_after.json sha256 759f2258daac9d28 (unchanged).

## 1. What the base is
- Engine: hist adapter (code/hist_pipe/hist_adapter.py) on the replica (code/th_redo/adapter_replica.py, rules_replica.py, sim.py unchanged), ITER14_PRM + HIST_PRM, 10 warm days, monthly chunks 2023-04..2026-10 (43 months).
- New rule class: code/th_redo/state_base.py (StateBaseRep(RuleReplica3, HistRuleReplica); StateBaseAdapter.run_range(lo, hi, base, record)). Bases: S1-COMB, S1-UNIF, S1-LIVE (live cell on state), references HOLD (old live cut), NOCUT (arm=1e9), PLAIN6060 (rules_replica.PLAIN_6060).
- Old per-print L2 cut REMOVED: ThL2 loss branch + policy loss line neutralised exactly as the stored never-cut run (rule arm=1e9); zero ThL2Cut/PolicyCut exits in every S1 month (checked). Entries, sizes, stops, targets, locks, caps, U7 blackout, ThL2 profit branch and policy profit lines unchanged.
- TH-L2-S evaluated once per exchange second from /mnt/l2/l2vast/_th_state/days (1-s state arrays); decision at the end of second s, market exit at the end of s+1 at mid(s+1) -+ 0.80 pt, bracket touches in (s,s+1] win. Verification of Stage 2 logic (not trusted): the kernel was re-read against the DS3_TH_STATE.md definition (pulled window = rows r-w+1..r of own-side cancels, newMae ties count, persistence = consecutive evaluated rows, arm variants V0/V1/V2 on position lots, evaluation starts at the row after the entry second), checked against an independent pure-python reference on 300 random cases incl. chunked evaluation (selftest: 0 mismatches), and the cell specs rebuilt from loss_finalists.json equal Stage 2 spec_wave2.json. Stated reading: persistence counts consecutive state rows, not wall-clock gaps (no gaps inside a trade in practice).
- Session scope = ENTRY session (by_unit key book_session); the D7 grammar matches the current session (DS3_TH_STATE.md section 2 caveat (d)).

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

## 3. Regression (exact, all columns of the trade list, order-insensitive)
- S1-COMB vs stage2:COMB: 43 months compared, IDENTICAL (all columns); trades 21067 vs 21067, net 2566937.50 vs 2566937.50, state cuts 6694 vs 6694, old ThL2Cut/PolicyCut exits in base 0
- S1-UNIF vs stage2:UNIF: 43 months compared, IDENTICAL (all columns); trades 19746 vs 19746, net 2256283.50 vs 2256283.50, state cuts 3036 vs 3036, old ThL2Cut/PolicyCut exits in base 0

## 4. Window metrics (USD/week, net of the 4.84 fee proxy, carrying week dropped; windows as of 2026-10-31 = STATE-SCORE; delta = base minus reference, same engine)
| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| S1-COMB vs never-cut | +12301 | +11780 | +10145 | +9975 | +7031 | +914 | +2142 | +973 |
| S1-COMB vs never-cut MDE | 17228 | 13411 | 13982 | 10798 | 7518 | 13193 | 4192 | 2986 |
| S1-COMB vs old live-cut HOLD | +2830 | +1247 | +7270 | +7179 | +4360 | -7369 | +8047 | -3294 |
| S1-COMB vs plain 60/60 | +12301 | +11780 | +10145 | +9975 | +7031 | +914 | +2142 | +973 |
| S1-COMB vs plain 60/60 MDE | 17228 | 13411 | 13982 | 10798 | 7518 | 13193 | 4192 | 2986 |
| S1-UNIF vs never-cut | +1194 | -204 | -1877 | -848 | +372 | +3402 | +1082 | +136 |
| S1-UNIF vs never-cut MDE | 12133 | 12560 | 9316 | 7205 | 5730 | 8505 | 3033 | 631 |
| S1-UNIF vs old live-cut HOLD | -8277 | -3075 | -3430 | -3325 | -3959 | -4882 | +5785 | -3357 |
| S1-UNIF vs plain 60/60 | +1194 | -204 | -1877 | -848 | +372 | +3402 | +1082 | +136 |
| S1-UNIF vs plain 60/60 MDE | 12133 | 12560 | 9316 | 7205 | 5730 | 8505 | 3033 | 631 |
| S1-COMB level (weekly net, plain mean, no week dropped) | +5480 | +25303 | +21376 | +26778 | +17513 | +11228 | +13383 | +1552 |
| S1-UNIF level (weekly net) | -5626 | +12838 | +4601 | +13010 | +11805 | +14134 | +13242 | +1649 |
| never-cut level (weekly net) | -6820 | +17939 | +9740 | +15529 | +12323 | +7725 | +11743 | +1353 |
| plain 60/60 level (weekly net, plain mean, no week dropped) | -6820 | +17939 | +9740 | +15529 | +12323 | +7725 | +11743 | +1353 |

Finding: the plain 60/60 run is trade-for-trade IDENTICAL to the stored never-cut run in every month checked (5 of 43 compared; all columns): in the hist replay config (PERIODS off, policy file in force from the start with no live profit lines) the only active TH component was the L2 loss cut, so vs-never-cut and vs-plain-60/60 deltas coincide (the vs-plain MDEs differ only through the month subset).
S1-COMB vs never-cut reproduces DS3_TH_STATE.md section 6 exactly (L1M +12301 ... X' +973). Caveat carried: the COMB gain is below its MDE on L6M and PRE, the per-book procedure fails the out-of-sample walk-forward, so S1-COMB is an in-sample base.

## 5. Files
- code sha256:
  - f269b3bf336db3efa95727857b3dc972c15ee9cff08bddd06d9749535169794e  th_redo/state_base.py
  - b3044d453f23c373046958c74595e20a543671cb751545b94547354c7b324813  th_redo/state_base_regress.py
  - 2774caa91a3d8d70abb08547b4f13cb822e24450733248fe079a03831d8424bc  th_redo/state_base_manifest.py
  - ec4ed9fbd5bb009ee749818f5fc129fd00bb9ab0a20a56c6fca32d4981e6d640  th_redo/adapter_replica.py
  - 4838268b544e24654244d173e72fe87f950fb6a5aefe1797b2e1f63cf63b30e8  th_redo/rules_replica.py
  - ae67737c61be240b8607c9cde44eabae2a1cc1c26b3e51b69d7ec0f90513db38  hist_pipe/hist_adapter.py
  - c7f3e78fa8894f88a0d05129603c41aedc631e941076a789e070bcf7f335cbb3  th_state_score/stage2.py
  - 659c046c506c5ced90457eac2202fd17e1f3823ddc4e05d6329f748684bd0c11  th_state_score/s2eval.py
  - ce68f510167e94fa86e9da28c2d587e393f714f2c99db3e2e64d37c29ef75058  th_state_score/common.py
- trade lists (per month trades.parquet [+ rows.parquet = G feature rows, every 5th wall second per open book, thG_rec format, S1-COMB/S1-UNIF only], DONE json):
  - S1-COMB: 43 months, dir /mnt/l2/l2vast/_th_state/base/S1-COMB/, feature-row files 43, sha-of-shas 5a643457bf9c41e8
  - S1-UNIF: 43 months, dir /mnt/l2/l2vast/_th_state/base/S1-UNIF/, feature-row files 43, sha-of-shas 9885831a363a65bd
  - S1-LIVE: 0 months, dir /mnt/l2/l2vast/_th_state/base/S1-LIVE/, feature-row files 0, sha-of-shas e3b0c44298fc1c14
  - NOCUT: 0 months, dir /mnt/l2/l2vast/_th_state/base/NOCUT/, feature-row files 0, sha-of-shas e3b0c44298fc1c14
  - HOLD: 0 months, dir /mnt/l2/l2vast/_th_state/base/HOLD/, feature-row files 0, sha-of-shas e3b0c44298fc1c14
  - PLAIN6060: 43 months, dir /mnt/l2/l2vast/_th_state/base/PLAIN6060/, feature-row files 0, sha-of-shas 80f7335605765e25
- manifest.json, metrics.json, regress.json, logs/ in /mnt/l2/l2vast/_th_state/base/
- usage: python3 -I code/th_redo/state_base.py run <S1-COMB|S1-UNIF|S1-LIVE|NOCUT|HOLD|PLAIN6060> <yyyymm,..|a-b> <workers> [--norec]; python3 -I code/th_redo/state_base.py selftest
- dead ledger: 11 rows program THS_PREPROOF appended to l2vast/ds3/out/uf/DEAD_CELLS.csv (7 book cells, P7_0, H7_3, UNIF, LIVE; dead_lookup found no prior match; append only).
