RESEARCH ORDER (relay, 11-17 07:28Z): after the stage 1 walk-forward. Three jobs, in this order.

Read of 07:15Z accepted: the pooled top-60-per-cell walk-forward shows no at-entry column beyond the shifted-label null. But the at-entry family table on the UNTOUCHED year still shows three small families above their shifted null, and the top-60 pick is dominated by family 1 (1.4 million tests), so those three never got a fair test:
  family 9 trade context (rebuilt causal): 5.81% vs 1.47% (999 tests)
  family 10 TICK internals: 3.11% vs 1.26% (450 tests)
  family 7 UW options positioning: 2.51% vs 1.56% (2,391 tests)

JOB 1 - FAMILY-RESTRICTED WALK-FORWARD (small, do first). For families 9, 10 and 7 separately: choose columns on 2023-04..2025-10 ONLY within that family (top 5 per book x session cell by stable |z|, and also a simple family score = equal-weight sum of the chosen columns' signs), freeze, then report HOLD and L6M untouched: share keeping sign, lift in R, ulcer and mean change of the skip rule and of a half-size rule, against (a) the same procedure on that family's shifted-label columns (11/23/37) and (b) 200 persistent random skips of the same share. Give block-shift permutation p for the family's real stable count on the untouched year (1,000 draws; these families are tiny). State each chosen column in plain words, what feed it needs, and whether D7 can compute it live today (family 9 should be computable from D7's own trade log; TICK needs the NYSE TICK feed; UW needs the UW subscription). Check family 9 once more for leakage: every input must be a trade CLOSED before the signal second, on the RAW chassis (not the JL2 stack).

JOB 2 - CELL TESTS ON THE ENGINE (the raw base table says some cells have no edge). On JL3 (and JL2 for comparison), 43 months, windows L6M / HOLD / GAP / PRE / pooled, ulcer primary, with 30 persistent random-skip controls of the same trade share: "do not trade" each of M7 London, K7 NY AM, P7 London, P7 NY AM, K7 NY PM, K7 London - each alone, the four weakest together, and half-size versions. Report freed-book effects (what the other books do with the freed stack room). This is an engine test, not path arithmetic.

JOB 3 - STAGE 2 PLAN. With no at-entry filter surviving, write five lines in the lead log on what stage 2-4 now are: which inputs a per-book score would be built from (only families that pass JOB 1), and otherwise go straight to stage 3 (exits jointly, on the raw chassis: stop/target/time-stop per book x session chosen walk-forward) and stage 4 (stack rules last, starting from the stage 5 KEEP list). Queue stage 3 raw-chassis exit cells now so server 2 does not wait.

Keep both servers at 100%. Research only.
