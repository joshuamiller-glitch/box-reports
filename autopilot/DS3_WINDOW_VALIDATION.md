# DS3_WINDOW_VALIDATION - does "run what was positive in the trailing window" persist? (REDO-3, T-RECENT-REDO section 3)

Written 2026-11-01 ~16:15Z. **OLD CAP (stored streams end 2026-02-06; decision months 2024-01..2026-01).** Months up to 2026-10 are added when the stream owners extend (see "Extension" at the end). Prereg `l2vast/ds3/prereg/WINDOWVAL_prereg.md` sha256 `9773742140583565c39a40d74e7f743f2d200f34ac04ce2a62d7c069a9c9f924` (in DECISIONS.md before scoring). No PASS claim anywhere. Code `l2vast/ds3/code/windowval/` (wv0..wv8), outputs `l2vast/ds3/out/windowval/`.

## PAGE 1

### The plain sentences

* **A rule positive in the last 60 days stays positive over the next 30 days 41.4% of the time (noise twins 43.2%; difference -1.8 pts, 95% CI -5.0 to +2.2); cluster-weighted (independent-bets view) 47.9% vs noise 48.8%; picking everything gives 39.1%.** Over the next 90 days 35.2% (noise 39.5%). Its dollars do not persist: the next-30-day result is -0.60 times the trailing magnitude (the sign flips), about -1,496 $/wk per series-month at live lots (pick everything -2,451).
* **The best window for THIS market**, by walk-forward choice (at month M pick the window with the best excess hit rate over months whose outcome had already ended; judge on M): among single windows **180 d** (chosen in 13 of 20 judged months, 30 d in the other 7); among single windows plus the combinations **60 d AND 180 d** (13 of 20); with the tolerant gate **365 d** (18 of 20). The walk-forward-chosen policy hits 42.3% next month (its own noise twin 45.4%, difference -3.0 pts, CI -7.0 to +1.9) - below noise. The in-sample ranking (not a selection, shown only for completeness) puts 365 d first at 46.3% but its noise twin is 46.4%: a slow window is "better" only because it is closer to a series' own long-run sign.
* **Adding the tolerant gate** (literal: trailing-positive AND older halves >= -0.5 MDE, later half > 0, PRE-analogue worst-20 not worse than the stack's) moves the 60 d rule from 41.4% to **44.2%** (noise twin with the same gate 47.0%, difference -2.8 pts, CI -6.5 to +1.8) while keeping about a quarter of the series. The lift is real against picking everything and against a random pick of the same count (the selected set beats all 100 random draws in every row), and it is exactly what a noise twin with the same long-run mean gets too: the gate selects series whose mean is positive, not series whose recent sign carries information. TOL-B and TOL-nc (post-hoc) are beside in Table 2 and say the same.
* **Verdict under the prereg rule: no window beats noise by a clear margin** (no month-block CI of the real-minus-noise difference lies above zero; every pooled point difference is -3 to 0 pts; cluster-weighted -1.6 to -0.5 pts plain, -2.6 to -0.7 gated). **The ledger stays a view.** It is not a selection window. In 2025 the 180 d and 90 d AND 180 d rules did sit about 1 pt above noise and in 2024 they sat about 4 pts below (Table 5): the sign is not stable, which is why the pooled difference is a wash.
* **L1M and L2M (30 d and 60 d analogues) stay VIEW columns.** The method does not support selecting on them: 30 d 42.4% vs noise 42.5%, 60 d 41.4% vs 43.2%; and the two shortest windows have the worst 90-day persistence (36.2% and 35.2% vs 34.4% for everything). In January 2026 (the last month, n small) a series positive over the last 30 d / 60 d was positive next month only 36% of the time against a 42% noise twin.

### Universe (what was swept)

Weekly streams (Monday weeks from 2023-04-03, 149 weeks to 2026-02-02), live-$ units (research streams divided by 2.35, as in SIXTY). **48,565 distinct streamed series** after removing 293 duplicate vectors (raw 48,858): of which **48,236 are the headline universe** (the four full program universes ADDUW 30,114 / EINT2 5,666 / ZONES-2 5,170 / EINT1 2,701 = 43,651 - the user's ~43,660 - plus the RE-2 STACK-2/session/book/sizing bank 294, plus the RE-6 NTE-2 and GOV grids 4,291) and **329 ledger-extra streams (278 stack-level + 51 per-contract trade-sum duplicates of them), which are look-ahead selected (they were put in the ledger because they were positive in L6M to 2026-02-06) and are therefore excluded from every headline number**, shown only as flagged rows in the family table. Per-contract trade-sum streams (51) are hit-rate only, never in $/wk. The ON / SHADOW pieces of the Sunday composite are not separate stored streams (they live inside the cube of the BASE-1 engine, which is rebuilt by REDO-1); they enter this study through RE-2/RE-6 bank rows that apply the same rules to the stack. They join when the extension lands.

**Effective N.** 48,236 series are NOT 48,236 bets: the spectral effective N (participation ratio of the correlation spectrum) is **24.2** (the first component carries 17% of variance; 93 components carry 90%); greedy clustering at rho >= 0.5 gives **2,839 clusters** (ADDUW 30,114 series sit in 123 clusters; EINT2 1,216; EINT1 810; ZONES-2 257; NTE-2 758; GOV 92; bank 16). So the honest independent count lies between 24 (common-factor view) and 2.8 thousand (cluster view). Two protections are built in: (1) the confidence intervals are month-block bootstraps (blocks of 3 months, 2,000 draws) over 25 decision months, which does not count series at all; (2) the "cluster-weighted" column weights each series by 1/(its cluster size). Pooled rates are dominated by ADDUW (62% of series) and are shown because the user's convention counts series; the cluster-weighted rates are the ones to read for evidence.

### ONE TABLE (Table 1; Table 2 is the same with the TOLERANT gate)

Windows are week-approximated: 30 d = 4 weeks, 60 d = 9, 90 d = 13, 180 d = 26, 365 d = 52; next 30 d = next 4 weeks, next 90 d = next 13 weeks; decision date = first Monday of month M; selection uses weeks before it only. A series is eligible for the pool when active (>= 10 non-zero weeks of the last 26) and for an outcome when it has at least one non-zero week in the outcome window (same filter for every row, noise included). Hit = outcome sum > 0. Shrinkage = pooled mean next $/wk divided by pooled mean trailing $/wk over the same selected stack-level series (negative = the sign flipped). $/wk = mean next-30-day $/wk per selected series-month at live lots (stack-level series only; per-contract trade-sum series excluded). Noise twins: 300 month-block permutations of the whole history (one permutation per replicate applied to all series so cross-correlation is kept; same mean and variance per series; persistence destroyed), the whole pipeline re-run on each; "vs noise" = real minus the mean of the twins with the month-block bootstrap CI of the difference. (The prereg said 30 twins; 300 were run, the procedure is unchanged.) Months = decision months with data (365 d starts 2024-04; gated 365 d starts 2024-10).

**Table 1. Trailing-positive, no gate.**

| window | months | hit next 30 d, pooled [95% CI] | cluster-weighted | hit next 90 d | shrinkage 30d / 90d | $/wk per series-month, live | noise twin 30d pooled / cw | vs noise, 30 d (pts) [CI] | by family: 30 d hit / noise twin (ADDUW; EINT2; ZONES-2; NTE2 sizing) |
|---|---|---|---|---|---|---|---|---|---|
| 30 d (L1M analogue, VIEW only) | 25 | 42.4 [38.8, 46.3] | 48.0 | 36.2 | -0.37 / -0.48 | -1,430 | 42.5 / 48.6 | -0.1 [-3.9, +3.7] ; cw -0.6 [-2.3, +1.4] | ADDUW 39/39; EINT2 48/47; NTE2-siz 56/57; ZONES-2 46/47 |
| 60 d (L2M analogue, VIEW only) | 25 | 41.4 [38.3, 45.3] | 47.9 | 35.2 | -0.60 / -0.79 | -1,496 | 43.2 / 48.8 | -1.8 [-5.0, +2.2] ; cw -0.9 [-2.6, +1.0] | ADDUW 37/40; EINT2 48/47; NTE2-siz 55/58; ZONES-2 46/48 |
| 90 d (L3M) | 25 | 41.0 [37.8, 44.6] | 48.1 | 35.9 | -0.86 / -1.00 | -1,629 | 43.7 / 48.9 | -2.8 [-6.2, +1.1] ; cw -0.8 [-2.5, +1.2] | ADDUW 36/40; EINT2 47/47; NTE2-siz 56/58; ZONES-2 46/48 |
| 180 d (L6M) | 25 | 43.0 [39.8, 46.7] | 48.6 | 41.2 | -1.01 / -0.92 | -1,173 | 44.8 / 49.1 | -1.8 [-4.9, +1.7] ; cw -0.5 [-2.4, +1.8] | ADDUW 38/42; EINT2 48/47; NTE2-siz 56/59; ZONES-2 48/49 |
| 365 d | 22 | 46.3 [43.9, 49.2] | 47.9 | 43.3 | -0.87 / -1.04 | -667 | 46.4 / 49.4 | -0.1 [-2.4, +2.8] ; cw -1.6 [-3.1, +0.1] | ADDUW 45/44; EINT2 45/46; NTE2-siz 56/59; ZONES-2 49/49 |
| 90 d AND 180 d (current rule) | 25 | 43.4 [40.3, 46.9] | 48.8 | 41.4 | -0.80 / -0.76 | -1,053 | 45.1 / 49.5 | -1.6 [-4.8, +1.8] ; cw -0.7 [-2.5, +1.5] | ADDUW 39/42; EINT2 48/47; NTE2-siz 56/59; ZONES-2 48/49 |
| 60 d AND 180 d | 25 | 43.9 [40.7, 47.3] | 49.0 | 41.8 | -0.71 / -0.73 | -936 | 45.0 / 49.6 | -1.1 [-4.3, +2.4] ; cw -0.6 [-2.4, +1.5] | ADDUW 39/42; EINT2 48/47; NTE2-siz 57/59; ZONES-2 48/49 |
| 30 d AND 90 d | 25 | 42.2 [39.3, 45.4] | 48.6 | 36.4 | -0.62 / -0.83 | -1,304 | 43.8 / 49.3 | -1.6 [-4.8, +1.8] ; cw -0.7 [-2.4, +1.2] | ADDUW 38/40; EINT2 48/47; NTE2-siz 57/58; ZONES-2 47/48 |
| pick everything (active pool) | 25 | 39.1 [35.6, 43.1] | 46.5 | 34.4 | n/a | -2,451 | 41.7 / 47.6 | -2.7 | ADDUW 36/39; EINT2 47/47; NTE2-siz 53/56; ZONES-2 45/47 |


**Table 2. The same with the TOLERANT gate (literal), TOL-B and TOL-nc (post-hoc) beside.**

| window | months | hit next 30 d, pooled [95% CI] | cluster-weighted | hit next 90 d | shrinkage 30d / 90d | $/wk per series-month, live | noise twin 30d pooled / cw | vs noise, 30 d (pts) [CI] | by family: 30 d hit / noise twin (ADDUW; EINT2; ZONES-2; NTE2 sizing) |
|---|---|---|---|---|---|---|---|---|---|
| 30 d + TOL | 24 | 46.2 [43.0, 50.0] | 48.7 | 40.4 | -0.18 / -0.40 | -551 | 46.4 / 50.4 | -0.2 [-3.3, +3.4] ; cw -1.7 [-3.4, +0.4] | ADDUW 45/44; EINT2 46/47; NTE2-siz 56/59; ZONES-2 47/49 |
| 30 d + TOL-B | 24 | 42.9 [38.9, 47.4] | 47.9 | 36.9 | -0.29 / -0.44 | -1,152 | 44.2 / 49.6 | -1.3 [-5.5, +3.1] ; cw -1.7 [-3.2, +0.1] | ADDUW 41/41; EINT2 46/47; NTE2-siz 55/58; ZONES-2 45/48 |
| 30 d + TOL-nc | 24 | 43.0 [38.9, 47.5] | 48.1 | 36.9 | -0.31 / -0.48 | -1,131 | 43.8 / 49.5 | -0.8 [-5.0, +3.5] ; cw -1.3 [-3.0, +0.7] | ADDUW 41/41; EINT2 46/47; NTE2-siz 55/57; ZONES-2 45/48 |
| 60 d + TOL | 24 | 44.2 [40.3, 49.1] | 48.7 | 39.1 | -0.37 / -0.72 | -794 | 47.0 / 50.6 | -2.8 [-6.5, +1.8] ; cw -1.8 [-3.5, +0.3] | ADDUW 41/44; EINT2 46/47; NTE2-siz 55/59; ZONES-2 47/49 |
| 60 d + TOL-B | 24 | 41.2 [37.9, 45.9] | 48.3 | 36.3 | -0.50 / -0.72 | -1,380 | 45.3 / 49.9 | -4.1 [-7.4, +0.5] ; cw -1.6 [-3.2, +0.3] | ADDUW 38/42; EINT2 46/47; NTE2-siz 55/58; ZONES-2 46/49 |
| 60 d + TOL-nc | 24 | 40.8 [37.1, 45.5] | 48.2 | 35.1 | -0.63 / -0.85 | -1,545 | 44.6 / 49.7 | -3.8 [-7.5, +1.0] ; cw -1.5 [-3.1, +0.4] | ADDUW 38/42; EINT2 47/47; NTE2-siz 54/58; ZONES-2 45/48 |
| 90 d + TOL | 24 | 44.4 [40.9, 48.8] | 48.5 | 40.4 | -0.55 / -0.88 | -912 | 47.5 / 50.7 | -3.1 [-6.3, +1.0] ; cw -2.2 [-4.0, -0.1] | ADDUW 42/45; EINT2 46/47; NTE2-siz 55/59; ZONES-2 47/50 |
| 90 d + TOL-B | 24 | 41.9 [38.7, 45.8] | 48.1 | 38.4 | -0.63 / -0.83 | -1,270 | 46.0 / 50.0 | -4.2 [-7.2, -0.1] ; cw -1.9 [-3.6, +0.0] | ADDUW 39/43; EINT2 46/47; NTE2-siz 54/59; ZONES-2 46/49 |
| 90 d + TOL-nc | 24 | 41.0 [37.4, 45.3] | 47.9 | 36.9 | -0.91 / -1.10 | -1,650 | 45.2 / 49.8 | -4.2 [-7.7, +0.2] ; cw -1.9 [-3.4, +0.0] | ADDUW 38/42; EINT2 46/47; NTE2-siz 54/58; ZONES-2 45/49 |
| 180 d + TOL | 24 | 46.8 [43.9, 50.1] | 48.6 | 46.4 | -0.55 / -0.59 | -546 | 48.3 / 51.0 | -1.5 [-4.4, +1.6] ; cw -2.3 [-4.0, -0.3] | ADDUW 46/46; EINT2 46/46; NTE2-siz 55/60; ZONES-2 48/50 |
| 180 d + TOL-B | 24 | 45.5 [42.3, 49.3] | 48.5 | 45.4 | -0.59 / -0.55 | -707 | 47.4 / 50.4 | -1.9 [-5.0, +1.7] ; cw -1.9 [-3.6, +0.1] | ADDUW 44/45; EINT2 46/46; NTE2-siz 54/59; ZONES-2 48/49 |
| 180 d + TOL-nc | 24 | 43.8 [40.4, 47.8] | 48.2 | 43.8 | -0.85 / -0.72 | -901 | 46.3 / 50.0 | -2.5 [-5.9, +1.4] ; cw -1.8 [-3.4, +0.1] | ADDUW 41/44; EINT2 46/46; NTE2-siz 54/59; ZONES-2 47/49 |
| 365 d + TOL | 18 | 47.0 [42.8, 51.9] | 50.6 | 48.1 | -0.63 / -0.64 | -443 | 49.2 / 51.3 | -2.3 [-6.4, +2.3] ; cw -0.7 [-3.2, +2.1] | ADDUW 44/48; EINT2 46/46; NTE2-siz 58/60; ZONES-2 47/50 |
| 365 d + TOL-B | 18 | 47.0 [42.7, 51.9] | 50.2 | 47.5 | -0.62 / -0.62 | -525 | 48.9 / 50.9 | -1.9 [-6.1, +2.8] ; cw -0.7 [-3.1, +1.9] | ADDUW 45/48; EINT2 47/46; NTE2-siz 57/60; ZONES-2 47/50 |
| 365 d + TOL-nc | 18 | 46.0 [42.6, 50.5] | 49.8 | 45.2 | -0.85 / -0.91 | -653 | 47.8 / 50.4 | -1.8 [-5.3, +2.5] ; cw -0.6 [-2.8, +1.9] | ADDUW 44/46; EINT2 47/46; NTE2-siz 56/59; ZONES-2 47/49 |
| 90 d AND 180 d + TOL | 24 | 47.2 [44.2, 50.4] | 48.8 | 45.9 | -0.43 / -0.55 | -477 | 48.6 / 51.4 | -1.4 [-4.5, +1.8] ; cw -2.6 [-4.6, -0.4] | ADDUW 47/47; EINT2 46/47; NTE2-siz 55/60; ZONES-2 47/50 |
| 90 d AND 180 d + TOL-B | 24 | 45.2 [41.5, 49.0] | 48.5 | 45.1 | -0.52 / -0.50 | -686 | 47.6 / 50.7 | -2.4 [-6.0, +1.4] ; cw -2.2 [-4.1, -0.0] | ADDUW 43/45; EINT2 46/47; NTE2-siz 55/59; ZONES-2 47/49 |
| 90 d AND 180 d + TOL-nc | 24 | 43.5 [39.7, 47.6] | 48.3 | 43.5 | -0.75 / -0.65 | -887 | 46.6 / 50.4 | -3.0 [-6.9, +0.9] ; cw -2.2 [-3.9, -0.1] | ADDUW 41/44; EINT2 47/47; NTE2-siz 54/59; ZONES-2 46/49 |
| 60 d AND 180 d + TOL | 24 | 47.9 [45.0, 50.9] | 49.5 | 46.4 | -0.25 / -0.47 | -277 | 48.5 / 51.5 | -0.6 [-3.7, +2.5] ; cw -2.0 [-3.8, +0.1] | ADDUW 48/46; EINT2 47/47; NTE2-siz 56/60; ZONES-2 47/50 |
| 60 d AND 180 d + TOL-B | 24 | 45.7 [42.2, 49.4] | 49.1 | 45.1 | -0.43 / -0.47 | -566 | 47.5 / 50.8 | -1.8 [-5.4, +2.1] ; cw -1.7 [-3.4, +0.3] | ADDUW 44/45; EINT2 47/47; NTE2-siz 56/59; ZONES-2 47/49 |
| 60 d AND 180 d + TOL-nc | 24 | 43.8 [39.9, 47.8] | 48.8 | 43.1 | -0.67 / -0.65 | -794 | 46.5 / 50.5 | -2.7 [-6.6, +1.3] ; cw -1.6 [-3.3, +0.3] | ADDUW 41/44; EINT2 47/47; NTE2-siz 55/59; ZONES-2 46/49 |
| 30 d AND 90 d + TOL | 24 | 45.9 [43.5, 49.0] | 48.7 | 41.7 | -0.31 / -0.62 | -554 | 47.5 / 51.1 | -1.6 [-4.3, +1.4] ; cw -2.4 [-4.2, -0.4] | ADDUW 44/45; EINT2 46/47; NTE2-siz 56/60; ZONES-2 46/49 |
| 30 d AND 90 d + TOL-B | 24 | 42.4 [39.6, 45.8] | 48.2 | 38.4 | -0.46 / -0.68 | -1,008 | 45.9 / 50.4 | -3.4 [-6.7, -0.0] ; cw -2.1 [-3.9, -0.1] | ADDUW 39/43; EINT2 46/47; NTE2-siz 56/59; ZONES-2 46/49 |
| 30 d AND 90 d + TOL-nc | 24 | 41.9 [38.2, 46.0] | 48.2 | 37.1 | -0.64 / -0.89 | -1,257 | 45.1 / 50.2 | -3.3 [-7.1, +1.0] ; cw -2.0 [-3.8, +0.1] | ADDUW 39/42; EINT2 46/47; NTE2-siz 55/58; ZONES-2 45/48 |

Random same-count control (100 random picks per month and row from the eligible pool, same number of series): the selected sets beat every draw on both horizons - the lift over "pick everything / a random pick" is +2 to +7 pts at 30 d and +1 to +10 at 90 d - but noise twins reproduce or exceed that lift, which is the point of the test.

| set | selected hit 30 d | random same-count mean (100 draws/month) | selected above 100% of draws? | selected 90 d | random 90 d mean |
|---|---|---|---|---|---|
| 30 d (L1M analogue, VIEW only) | 42.4 | 39.0 | yes | 36.2 | 34.1 |
| 60 d (L2M analogue, VIEW only) | 41.4 | 39.1 | yes | 35.2 | 33.3 |
| 90 d (L3M) | 41.0 | 38.9 | yes | 35.9 | 32.9 |
| 180 d (L6M) | 43.0 | 38.5 | yes | 41.2 | 34.1 |
| 365 d | 46.3 | 39.5 | yes | 43.3 | 33.0 |
| 90 d AND 180 d (current rule) | 43.4 | 38.8 | yes | 41.4 | 33.9 |
| 60 d AND 180 d | 43.9 | 38.9 | yes | 41.8 | 34.0 |
| 30 d AND 90 d | 42.2 | 39.0 | yes | 36.4 | 33.4 |

### Walk-forward window choice (no window chosen on the months it is judged on)

At each month M the rule picks, from the candidate set, the row with the largest cluster-weighted excess 30-day hit rate over the pool in decision months whose outcome ended before M (needs 6 such months with >= 200 series-months; judged from 2024-07). Noise twins run the identical walk-forward on their own tables, so the selection bias is inside the comparison.

| candidate set the rule chooses from | months judged | walk-forward hit 30 d | cw | hit 90 d | noise twin 30 d (also walk-forward) | vs noise [CI] | cw vs noise [CI] | 90 d vs noise [CI] | $/wk | windows chosen (months) |
|---|---|---|---|---|---|---|---|---|---|---|
| singles | 20 | 42.3 | 47.6 | 38.0 | 45.4 (sd 2.0) | -3.0 [-7.0, +1.9] | -1.7 [-3.0, -0.2] | -5.1 [-9.9, +0.7] | -1,534 | {'180d|plain': 13, '30d|plain': 7} |
| singles+combos | 20 | 42.4 | 47.7 | 38.5 | 45.4 (sd 1.9) | -3.0 [-7.2, +1.9] | -1.7 [-3.3, -0.0] | -4.6 [-10.7, +1.7] | -1,520 | {'60&180|plain': 13, '30&90|plain': 6, '30d|plain': 1} |
| singles TOL | 20 | 45.9 | 50.0 | 46.3 | 48.7 (sd 2.3) | -2.9 [-6.4, +1.7] | -1.1 [-3.3, +1.1] | -2.4 [-7.0, +2.3] | -656 | {'365d|TOL': 18, '30d|TOL': 2} |
| all plain+TOL | 20 | 42.6 | 49.0 | 40.1 | 48.5 (sd 2.5) | -5.9 [-10.1, +1.1] | -2.2 [-4.4, +0.7] | -8.2 [-16.3, +2.2] | -1,288 | {'365d|TOL': 18, '30d|plain': 1, '30&90|plain': 1} |

### Regime paragraph: is Feb-Oct 2026 like the old L6M (Aug-Jan) or like PRE (2024-25)?

**Neither; if forced, volatility says "PRE and beyond", liquidity says "something new".** Measured now from the raw NQ/ES 1-minute tables on disk through 2026-10-30 (market-level proxies of the recentedge3 regime frame; the 1-minute tables have not yet been tied out by REDO-1): the share of Feb-Oct days in the top vol tercile is 55% vs 41% in PRE and 30% in the old L6M; the daily range is 527 pts vs 357 and 377; the top-10 book is 44 contracts per side vs 64 and 63 (thinnest on record: June-July about 32); spread 2.85 pts vs 2.31 and 2.31. Trend persistence (efficiency ratio 0.076 vs 0.078 / 0.073; trending-day share 30% vs 34% / 31%) and the ES-NQ correlation (0.902 vs 0.910 / 0.914) are the same in all three; 5-minute returns are a little more mean-reverting (autocorrelation -0.019 vs -0.007 / -0.012). Session shares of volume moved to Asia (12.5% vs 7.7% / 8.3%; check for a data-clock artefact before leaning on this one) and away from NY-PM (21.7% vs 24.9% / 24.3%). On the standardised distance over all 17 measures, Feb-Oct is 0.87 SD-units from PRE and 0.90 from the old L6M (month-block bootstrap of the difference -0.24 to +0.35: not separable), the old L6M being the calm half-year (30% of days in the top tercile). In plain words: the year looks like **2024-25 with the volatility turned up and the book thinned out** (June-July 2026 the extreme), not like the quiet Aug-Jan that the old L6M measured. What waits for REDO-1: the signal-level measures of recentedge3 (signal-time ES correlation, session shares of the stack's own signals, fill cost, stop-exit share, MAE/MFE) need the rebuilt trade library; the market-level proxies above do not.

| measure | PRE 2024-02..2025-06 | L6M-old 2025-08..2026-02-06 | Feb-Oct 2026 | (MID Feb-Apr) | (L6M-new May-Oct) | (L1M Oct) |
|---|---|---|---|---|---|---|
| days | 364 | 134 | 190 | 59 | 131 | 22 |
| share of days in the top vol tercile (cut on 2023-04..2025-06) | 41% | 30% | 55% | 61% | 52% | 55% |
| share in the bottom tercile | 31% | 49% | 19% | 17% | 20% | 23% |
| NQ daily realised vol 5m, % | 1.14 | 0.93 | 1.19 | 1.22 | 1.17 | 1.12 |
| NQ daily range, pts | 357 | 377 | 527 | 470 | 553 | 557 |
| trend persistence: efficiency ratio 5m | 0.0776 | 0.0726 | 0.0756 | 0.0773 | 0.0748 | 0.0714 |
| 5m return autocorrelation | -0.0074 | -0.0119 | -0.0195 | -0.0119 | -0.0229 | -0.0256 |
| variance ratio 30m/5m | 0.991 | 1.009 | 0.987 | 0.989 | 0.986 | 0.923 |
| share of trending days (ER top tercile) | 34% | 31% | 30% | 31% | 30% | 27% |
| book depth, contracts (top-10 each side, RTH median of minutes) | 64 | 63 | 44 | 47 | 43 | 47 |
| spread, pts (RTH) | 2.31 | 2.31 | 2.85 | 2.77 | 2.89 | 2.33 |
| ES-NQ 5m return correlation (daily mean) | 0.910 | 0.914 | 0.902 | 0.940 | 0.886 | 0.886 |
| volume share Asia | 7.7% | 8.3% | 12.5% | 11.6% | 12.9% | 12.5% |
| London | 7.7% | 6.5% | 8.0% | 8.7% | 7.7% | 8.0% |
| Pre | 5.7% | 4.8% | 5.4% | 5.8% | 5.1% | 5.0% |
| NY-AM | 39.2% | 42.1% | 38.9% | 37.5% | 39.5% | 38.7% |
| NY-PM | 24.9% | 24.3% | 21.7% | 22.6% | 21.3% | 22.3% |
| Close | 14.7% | 14.0% | 13.5% | 13.7% | 13.5% | 13.5% |

Distance of Feb-Oct 2026 to the two references in monthly-SD units (z, positive = Feb-Oct higher):

| measure | Feb-Oct minus L6M-old (z) | Feb-Oct minus PRE (z) |
|---|---|---|
| rv5 | +0.71 | +0.13 |
| rng | +0.98 | +1.11 |
| vol | +0.29 | -0.21 |
| er5 | +0.26 | -0.18 |
| ac5 | -0.35 | -0.57 |
| vr6 | -0.37 | -0.07 |
| depth | -0.93 | -0.96 |
| spread | +0.81 | +0.81 |
| esnq | -0.44 | -0.26 |
| sh_asia | +1.68 | +1.93 |
| sh_london | +1.58 | +0.36 |
| sh_pre | +0.79 | -0.50 |
| sh_nyam | -1.28 | -0.12 |
| sh_nypm | -1.53 | -1.91 |
| sh_close | -0.49 | -1.23 |
| trend_day | -0.07 | -0.39 |
| vt_high | +0.25 | +0.14 |


## Detail

### Table 3. By family (60 d positive, no gate): hit 30 d vs the family's noise twin

| family | n series-months (60 d positive) | hit 30 d | noise twin | diff | hit 90 d | noise 90 | $/wk per series-month | shrink |
|---|---|---|---|---|---|---|---|---|
| ADDUW sizing | 238,382 | 37.1 | 39.9 | -2.9 | 28.2 | 34.4 | -2171 | -0.72 |
| EINT1 entry filter | 29,223 | 45.6 | 46.9 | -1.3 | 40.6 | 44.9 | -894 | -0.33 |
| EINT2 regime filter | 63,374 | 47.6 | 47.1 | +0.6 | 42.6 | 45.6 | -409 | -0.28 |
| GOV stack | 16,474 | 42.7 | 40.5 | +2.2 | 35.4 | 32.8 | -3254 | -0.46 |
| NTE-2 entry filter | 11,566 | 42.4 | 47.3 | -4.9 | 38.9 | 44.8 | -1442 | -0.67 |
| NTE-2 sizing | 17,669 | 55.3 | 57.7 | -2.4 | 61.6 | 63.0 | 751 | +0.43 |
| STACK-2 cut/cap (bank) | 585 | 29.2 | 21.4 | +7.8 | 0.5 | 8.1 | -21680 | -2.05 |
| ZONES-2 zone entry | 55,150 | 46.3 | 48.0 | -1.7 | 46.2 | 47.6 | -13 | -0.52 |
| bank entry filter | 99 | 12.1 | 22.5 | -10.3 | 0.0 | 9.3 | -30441 | -2.02 |
| bank regime | 71 | 25.4 | 20.3 | +5.0 | 2.8 | 7.3 | -21757 | -1.82 |
| bank sizing | 135 | 25.9 | 20.9 | +5.0 | 0.0 | 7.9 | -21488 | -1.99 |
| ledger extra: EINT1 (SURVIVOR-SELECTED, not evidence) | 214 | 50.0 | 49.5 | +0.5 | 39.8 | 49.9 | -612 | -0.13 |
| ledger extra: EQR (SURVIVOR-SELECTED, not evidence) | 730 | 64.7 | 57.0 | +7.6 | 60.4 | 61.3 | 17745 | +0.55 |
| ledger extra: EXP1 (SURVIVOR-SELECTED, not evidence) | 83 | 65.1 | 64.7 | +0.4 | 52.1 | 67.3 | 9041 | +0.59 |
| ledger extra: L2SP (SURVIVOR-SELECTED, not evidence) | 84 | 77.4 | 62.4 | +15.0 | 70.8 | 71.3 | 46723 | +0.74 |
| ledger extra: META (SURVIVOR-SELECTED, not evidence) | 1,072 | 54.7 | 54.0 | +0.6 | 54.2 | 54.9 | 1273 | +0.12 |
| ledger extra: SPLIT (SURVIVOR-SELECTED, not evidence) | 108 | 57.4 | 53.5 | +3.9 | 66.0 | 58.7 | 885 | +0.06 |
| ledger extra: THL (SURVIVOR-SELECTED, not evidence) | 107 | 61.7 | 58.5 | +3.2 | 61.3 | 59.0 | -220 | -0.02 |
| ledger extra: THPC2 (SURVIVOR-SELECTED, not evidence) | 171 | 62.0 | 60.4 | +1.6 | 63.1 | 66.9 | 47194 | +0.57 |
| ledger extra: UF-ENTRY (SURVIVOR-SELECTED, not evidence) | 1,110 | 79.3 | 74.3 | +5.0 | 85.0 | 85.8 | 18227 | +0.82 |
| ledger extra: UF-LOSS (SURVIVOR-SELECTED, not evidence) | 120 | 66.7 | 68.1 | -1.4 | 58.6 | 67.7 | 7352 | +0.34 |
| per-contract trade-sum: EXP1 (SURVIVOR-SELECTED, not evidence) | 83 | 65.1 | 64.7 | +0.4 | 52.1 | 67.3 | per contract | - |
| per-contract trade-sum: L2SP (SURVIVOR-SELECTED, not evidence) | 84 | 77.4 | 62.4 | +15.0 | 70.8 | 71.3 | per contract | - |
| per-contract trade-sum: THL (SURVIVOR-SELECTED, not evidence) | 107 | 61.7 | 58.5 | +3.2 | 61.3 | 59.0 | per contract | - |
| per-contract trade-sum: THPC2 (SURVIVOR-SELECTED, not evidence) | 171 | 62.0 | 60.4 | +1.6 | 63.1 | 66.9 | per contract | - |
| per-contract trade-sum: UF-LOSS (SURVIVOR-SELECTED, not evidence) | 124 | 67.7 | 68.1 | -0.4 | 58.3 | 67.6 | per contract | - |

Families that sit above their noise twin by a clear margin do exist at the family level (the EQR/UF-ENTRY/L2SP/THPC2 ledger extras at +5 to +15 pts) - but those rows are exactly the look-ahead-selected ledger streams and are not evidence. Among the large headline families (more than 10,000 series-months) none sits above its twin by more than +2.2 pts (GOV) and ADDUW and NTE-2 sit 2 to 5 points below; the three small bank families sit 5 to 8 points above their twins but at 12 to 29% hit rates and about -$21k/wk (n below 600 series-months).

### Table 4. Random same-count and pick-everything controls: see above. Table 5. By year

| set | 2024 hit30 / noise | 2025 hit30 / noise | 2026-01 hit30 / noise (n small) |
|---|---|---|---|
| 30 d (L1M analogue, VIEW only) | 41.4 / 42.3 (n=228,765) | 43.9 / 42.8 (n=219,951) | 36.4 / 42.0 (n=16,823) |
| 60 d (L2M analogue, VIEW only) | 39.8 / 43.0 (n=217,107) | 43.7 / 43.5 (n=200,428) | 36.0 / 42.7 (n=15,193) |
| 90 d (L3M) | 39.4 / 43.6 (n=203,271) | 42.7 / 43.9 (n=196,499) | 40.1 / 43.3 (n=12,433) |
| 180 d (L6M) | 40.1 / 44.6 (n=174,882) | 46.4 / 44.9 (n=162,405) | 40.8 / 44.2 (n=14,171) |
| 365 d | 45.2 / 46.3 (n=125,274) | 47.5 / 46.5 (n=135,182) | 45.2 / 46.3 (n=11,996) |
| 90 d AND 180 d (current rule) | 41.1 / 45.0 (n=125,242) | 46.0 / 45.2 (n=118,464) | 42.2 / 44.3 (n=9,295) |
| 60 d AND 180 d | 41.7 / 44.9 (n=116,265) | 46.6 / 45.2 (n=109,379) | 40.2 / 44.0 (n=9,609) |
| 30 d AND 90 d | 41.5 / 43.7 (n=133,160) | 43.0 / 43.9 (n=127,946) | 40.4 / 42.9 (n=9,083) |
| pick everything | 38.2 / 41.5 (n=575,628) | 40.5 / 41.9 (n=574,917) | 32.6 / 42.4 (n=47,881) |

### What was not done / limits
* The weekly grid approximates 30/60/90/180/365 days (28/63/91/182/364). Daily-resolution streams exist only for the RE-2/RE-6 banks; the 43,651 program series are stored weekly.
* Outcomes require activity in the outcome window (same filter for all rows). A selected rule that stops firing is dropped from both real and twin rows alike.
* The noise twin keeps each series' mean and variance and the cross-section; it does not keep the real series' autocorrelation. A twin that beats the real series (as here) means the real series mean-revert slightly more than their own mean implies; it does not mean selection is harmful.
* 25 months, month-block CI half-width about 3 to 4 pts at 30 d: a true edge below about 4 pts would not be detected. The test says "no edge visible, and the point estimates are on the wrong side of noise"; it cannot prove zero.
* $/wk is an average over series-months, dominated by ADDUW size scaling, not a portfolio return (rules are not additive). Heavy tails: read the sign and hit rates, not the magnitude.
* Streams of ON/SHADOW pieces and the six-book composite are not in this sweep until REDO-1 rebuilds the cube; the 329 ledger-extra streams are survivors and excluded from headlines.
* The TOLERANT gate is applied at the decision date on the same trailing information (older halves are the two halves of the history before M minus max(window, 26) weeks); for 365 d only months from 2024-10 have both halves.

### Extension (months added as streams extend)
Status at write time: REDO-1 delivered `code/cap/windows.py` and `out/cap/CAP.json` (cap 2026-10-31); the weekly streams used here (universe.npz, stream_W, recentedge2 bank, recentedge6 bank6) still end 2026-02-02/06 - their owners have not yet rebuilt them. The regime paragraph above already uses the raw 1-minute tables through 2026-10.
Re-run (≈6 minutes on 3 workers): put the extended stream files where `wv0_build.py` reads them (same layout, more weeks; `daily2weekly` in `code/sixty/s0_common.py` needs NW raised), then `python3 wv0_build.py; python3 wv2_clusters.py; python3 wv3_run.py 300 3; python3 wv4_random.py; python3 wv5_tables.py <T>; python3 wv8_md.py` (T = number of weeks). Months are generated from the week grid, so each new month M (next 30 d needs 4 more weeks, next 90 d needs 13) appears automatically; the OLD-CAP table stays as `*_cap149.*`. Planned label: "NEW CAP" with months 2024-01..2026-10 once the streams reach 2026-10-31, and the old-cap vs new-cap comparison of every row in the same table.

### Files
`out/windowval/`: X_live.npy, universe_meta.csv, stream_inventory.csv, effective_N.json, cluster_label.npy, tables_cap149.pkl (real + 300 twins), sets_summary_cap149.csv, by_family_cap149.csv, by_year_cap149.csv, monthly_cap149.csv, walkforward_cap149.csv, random_cap149.pkl, regime_market_daily.csv, regime_windows.csv, regime_distance.csv, md_*.md.

### Stream inventory (what streamed series exist and their coverage)

| family | kind | series | clusters (rho>=0.5) | median active weeks | first..last week | source | in headline |
|---|---|---|---|---|---|---|---|
| ADDUW sizing | stack | 30,114 | 123 | 149 | 2023-04-03..2026-02-02 | sixty/universe.npz (4 full program universes) | yes |
| EINT1 entry filter | stack | 2,701 | 810 | 149 | 2023-04-03..2026-02-02 | sixty/universe.npz (4 full program universes) | yes |
| EINT2 regime filter | stack | 5,666 | 1216 | 149 | 2023-04-03..2026-02-02 | sixty/universe.npz (4 full program universes) | yes |
| GOV stack | stack | 1,931 | 92 | 149 | 2023-04-03..2026-02-02 | recentedge6/bank6.npz | yes |
| NTE-2 entry filter | stack | 1,149 | 298 | 149 | 2023-04-03..2026-02-02 | recentedge6/bank6.npz | yes |
| NTE-2 sizing | stack | 1,211 | 460 | 149 | 2023-04-03..2026-02-02 | recentedge6/bank6.npz | yes |
| STACK-2 cut/cap (bank) | stack | 194 | 4 | 149 | 2023-04-03..2026-02-02 | recentedge2/bank.npz | yes |
| ZONES-2 zone entry | stack | 5,170 | 257 | 148 | 2023-04-03..2026-02-02 | sixty/universe.npz (4 full program universes) | yes |
| bank entry filter | stack | 32 | 4 | 149 | 2023-04-03..2026-02-02 | recentedge2/bank.npz | yes |
| bank regime | stack | 24 | 4 | 149 | 2023-04-03..2026-02-02 | recentedge2/bank.npz | yes |
| bank sizing | stack | 44 | 4 | 149 | 2023-04-03..2026-02-02 | recentedge2/bank.npz | yes |
| ledger extra: CUTWAIT | stack | 2 | 2 | 95 | 2023-04-03..2026-02-02 | sixty/stream_W + extra_stack/extra_trade (ledger rows, look-ahead selected) | no |
| ledger extra: EINT1 | stack | 19 | 15 | 149 | 2023-04-03..2026-02-02 | sixty/stream_W + extra_stack/extra_trade (ledger rows, look-ahead selected) | no |
| ledger extra: EINT2 | stack | 2 | 2 | 149 | 2023-04-03..2026-02-02 | sixty/stream_W + extra_stack/extra_trade (ledger rows, look-ahead selected) | no |
| ledger extra: EQR | stack | 52 | 12 | 149 | 2023-04-03..2026-02-02 | sixty/stream_W + extra_stack/extra_trade (ledger rows, look-ahead selected) | no |
| ledger extra: EXP1 | stack | 7 | 5 | 126 | 2023-04-03..2026-02-02 | sixty/stream_W + extra_stack/extra_trade (ledger rows, look-ahead selected) | no |
| ledger extra: L2SE | stack | 2 | 1 | 149 | 2023-04-03..2026-02-02 | sixty/stream_W + extra_stack/extra_trade (ledger rows, look-ahead selected) | no |
| ledger extra: L2SP | stack | 6 | 3 | 149 | 2023-04-03..2026-02-02 | sixty/stream_W + extra_stack/extra_trade (ledger rows, look-ahead selected) | no |
| ledger extra: META | stack | 88 | 34 | 116 | 2023-07-03..2026-02-02 | sixty/stream_W + extra_stack/extra_trade (ledger rows, look-ahead selected) | no |
| ledger extra: SPLIT | stack | 8 | 3 | 149 | 2023-04-03..2026-02-02 | sixty/stream_W + extra_stack/extra_trade (ledger rows, look-ahead selected) | no |
| ledger extra: THL | stack | 10 | 5 | 148 | 2023-04-03..2026-02-02 | sixty/stream_W + extra_stack/extra_trade (ledger rows, look-ahead selected) | no |
| ledger extra: THPC2 | stack | 12 | 7 | 124 | 2023-07-03..2026-02-02 | sixty/stream_W + extra_stack/extra_trade (ledger rows, look-ahead selected) | no |
| ledger extra: UF-ENTRY | stack | 56 | 6 | 149 | 2023-04-03..2026-02-02 | sixty/stream_W + extra_stack/extra_trade (ledger rows, look-ahead selected) | no |
| ledger extra: UF-LOSS | stack | 13 | 8 | 66 | 2023-04-10..2026-02-02 | sixty/stream_W + extra_stack/extra_trade (ledger rows, look-ahead selected) | no |
| ledger extra: UF-PROFIT | stack | 1 | 1 | 32 | 2023-08-14..2026-01-12 | sixty/stream_W + extra_stack/extra_trade (ledger rows, look-ahead selected) | no |
| per-contract trade-sum: CUTWAIT | trade_sum | 2 | 2 | 95 | 2023-04-03..2026-02-02 | sixty/stream_W + extra_stack/extra_trade (ledger rows, look-ahead selected) | no |
| per-contract trade-sum: EXP1 | trade_sum | 7 | 5 | 126 | 2023-04-03..2026-02-02 | sixty/stream_W + extra_stack/extra_trade (ledger rows, look-ahead selected) | no |
| per-contract trade-sum: L2SP | trade_sum | 6 | 3 | 149 | 2023-04-03..2026-02-02 | sixty/stream_W + extra_stack/extra_trade (ledger rows, look-ahead selected) | no |
| per-contract trade-sum: THL | trade_sum | 10 | 5 | 148 | 2023-04-03..2026-02-02 | sixty/stream_W + extra_stack/extra_trade (ledger rows, look-ahead selected) | no |
| per-contract trade-sum: THPC2 | trade_sum | 12 | 7 | 124 | 2023-07-03..2026-02-02 | sixty/stream_W + extra_stack/extra_trade (ledger rows, look-ahead selected) | no |
| per-contract trade-sum: UF-LOSS | trade_sum | 14 | 9 | 66 | 2023-04-10..2026-02-02 | sixty/stream_W + extra_stack/extra_trade (ledger rows, look-ahead selected) | no |

