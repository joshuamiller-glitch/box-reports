# DS3_HALT_FINAL - T-HALT-RESUME verdicts (GOV-1)

Research only; UNTOUCHED never read; full tables in DS3_HALT_RULES.md, base rates in DS3_HALT_MAP.md. Engine and preregs as stated there.

## Plain sentences

* **Halting PE after a rolling-20-trade P&L below -3R and resuming on 2 paper winners keeps 79% of PE's L6M mean and changes the sum of its worst-20 weeks (all history, 149 weeks) from -544k to -472k (-13%)**; the whole-stack delta of that rule (applied to all six books) is -10.5k/wk in L6M (MDE 16.3k), -9.2k HOLD, -0.2k PRE, -0.5k X'; it halts 14% of signals in L6M; the lag: the first 5 trades after a halt average -0.006 R vs the book mean (positive = still good), the first 5 after a resume +0.028 R. Verdict: cost, not saving.
* **Performance-based halts do NOT beat random halts of the same length.** Over 930 performance/equity cells the median P(cell beats random halts) is 0.46 (L6M), 0.50 (HOLD), 0.72 (PRE), 0.14 (X'); only 68 cells reach 0.90 in both L6M and HOLD, about what chance gives. The classic finding holds.
* **The regime halts that work** (positive in L6M and HOLD with P(beat random) >= 0.80 in both): reg_xasset_120/day (+1.3k L6M, +0.4k HOLD, -0.2k PRE, +0.5k X', halts 7%); map_dow/day (+0.6k L6M, +0.4k HOLD, +0.1k PRE, +2.7k X', halts 3%); map_dow/mem (+0.6k L6M, +0.4k HOLD, +0.1k PRE, +2.7k X', halts 3%). All inside MDE: LEAD at best, tier unchanged for the rest.
* **Learned halt/half policy** (walk-forward logistic on perf + regime state): median delta L6M -0.2k / HOLD -0.6k / PRE -2.7k vs the shuffled-label placebo -0.7k / -0.9k / -1.6k; it is not distinguishable from its placebo. Extracted rule in words: none stable enough to state.

## One verdict per book (cells applied to all books; per-book column of the same cell)

| book | cells with per-book delta > 0 in L6M, HOLD, PRE and X' | best cell by L6M (per book) d L6M / HOLD / PRE / X' ($k/wk) | verdict |
|---|---|---|---|
| KB | 34 of 1786 | book/rs10_5/n5: +1.2 / +1.3 / +0.7 / -0.5 | weak: some cells positive but inside noise; no halt |
| PE | 53 of 1786 | book/L:sh2:0.55/mem: +0.9 / +0.8 / -1.9 / +2.1 | weak: some cells positive but inside noise; no halt |
| SM | 127 of 1786 | book/z10_1.0/n3: +1.4 / +1.2 / +0.5 / +0.6 | weak: some cells positive but inside noise; no halt |
| HM | 9 of 1786 | book/reg_xasset_120/rev: +1.3 / +0.8 / +0.2 / +0.5 | no halt; the stack as it is |
| MV | 11 of 1786 | stack/wr20/n3: +1.5 / +1.1 / -0.9 / +1.0 | no halt; the stack as it is |
| PB | 23 of 1786 | book/z20_1.5/n5: +0.4 / +0.4 / -0.2 / +0.0 | weak: some cells positive but inside noise; no halt |

All per-book numbers are inside the per-book noise (a single book moves the stack weekly mean by $0.1-1.5k with MDE $1-3k). Tiers: all performance halts DEAD; regime/calendar cells LEAD at best; learned = placebo.

## THP_POLICY halt section

No halt section proposed. Nothing is >= 0 on the stack mean in all four windows with a delta above its MDE; the carried cells (DS3_HALT_RULES.md section 4) halt 0-9% of signals and gain $0.0-1.2k/wk, indistinguishable from random halts. The reference stays: per-book day locks + per-book week floor (12R) + combined week lock (12R of K6) as measured in DS3_GOVERNOR_FIDELITY.md (the combined lock itself cost 5.8k/wk L6M in the D6-faithful engine: the one halt-like rule that does fire (73 of 149 weeks) and loses).
