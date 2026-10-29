# DS3_THL_HM_FWD - THL HM forward test: shadow score of the live loss rule L6_a30_r3_w10 against hold-to-stop

Generated 2026-10-29 15:42Z by l2vast/ds3/code/thl_hm/fwd_marks.py (offline; no live, execution-server, chart or register file touched). Fees per FEES.md ($4.84/contract RT = 0.242 pt, same in both arms, cancels in every delta). No account ids.
Prereg l2vast/ds3/prereg/THL_HM_RETEST_prereg.md (with Amendment A1). User decision 2026-10-29: option A - forward only from 2026-11-01, UNTOUCHED stays sealed; **a30_w10 is the sole primary**; a30_w20 (found after the freeze) and the other 7 cells are DESCRIPTIVE.

## 0. Status

**NO FORWARD DATA SCORED YET.** HM trades scored: 0. Status: **INCONCLUSIVE** (Amendment A1: no verdict below 1,000 HM trades). This file is in template state.

## 1. Expected calendar dates of the marks
Start: Sunday 2026-11-01 (first admissible entry 18:00 ET, official week 2026-W45). The user runs a30/3of3/w10 live on ALL D6 books from 2026-10-29; **HM is the book scored** (the A1 test is HM only; the other D6 books are not pooled here).

| HM trades per week | 500 trades | 1,000 trades |
|---|---|---|
| 15 | 2027-06-22 (Tue) | 2028-02-11 (Fri) |
| 18 | 2027-05-14 (Fri) | 2027-11-25 (Thu) |
| 20 (planning case) | 2027-04-25 (Sun) | 2027-10-17 (Sun) |
| 22 | 2027-04-09 (Fri) | 2027-09-15 (Wed) |
| 25 | 2027-03-21 (Sun) | 2027-08-08 (Sun) |

Planning case 20 HM trades per week (research stream 19.6/week; live HMStrat 18 in its first full week). Holidays and early closes push the dates out by days, not weeks. No observed rate yet.
At 1,000 trades the primary has power ~28% at the observed seen-data effect (+1.18 pts) and ~10% at half of it; a CI that includes 0 there is INCONCLUSIVE, not a refutation (n80 is ~4,300 trades). The single fresh look is the 1,000-trade snapshot; the 500 mark is an interim DESCRIPTIVE report and decides nothing.

## 2. Marks

### 500-trade mark
NOT REACHED (scored 0 of 500). Expected 2027-04-25 (Sun) at 20 HM trades per week.

### 1000-trade mark
NOT REACHED (scored 0 of 1000). Expected 2027-10-17 (Sun) at 20 HM trades per week.

## 3. Running view (all admissible HM trades to date; descriptive, re-scored on every run)

No trades yet.

## 4. Method in one paragraph
Both arms are scored from the live entry (time, side, price) on the 1-second NQ path with the THL B machinery (copy of thl_kern.one / thl_lib.price_legs): hold-to-stop = 60-pt stop, 60-pt target, 16:55 ET flat; rule arm = the same entry with L6_a{A}_r3_w{W} (armed at adverse excursion A, 3 of 3 of: >= 4.0 pts adverse over W s, no new extreme for W s with recovery <= 4.0, efficiency < 0.35; market exit at the decision-second close). MEASURED fills: market exit 1 tick adverse, resting stop minus the by-year walk, limit target at touch plus the P9 correction; C = CONSERVATIVE label. The statistic is d_sim = rule minus hold per trade (pts), mean and week-block bootstrap CI (B = 10,000, seed 20261029). Files: l2vast/ds3/code/thl_hm/{fwd_score.py, fwd_score_test.py, fwd_marks.py}; outputs l2vast/ds3/out/thl_hm_fwd/; runbook and data needs autopilot/DS3_THL_HM_FWD_RUNBOOK.md.

## 5. Caveats that stay on every number
* The live rule is on in the account, so exits in the log are already cut: both arms are re-simulated from the entry, the log supplies only entry, the as-traded check and the fired flag.
* Re-entry effect: a live cut frees the book earlier, so some live entries would not exist in the hold-to-stop world (flag overlap, column "M excl. overlap").
* Model rule vs the live DualStrat implementation (exits one second later, queue, partial fills) is covered by C and by the fired-agreement line; the as-traded delta is shown beside the modelled one.
* From 2027 the stop-walk and P9 target tables fall back to the 2026 values and should be re-measured.
* A mark is reported at exactly N trades; the running view is descriptive only.
