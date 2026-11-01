# DS3_BETTER_S7 - T-BETTER section 7: per-book SESSION re-selection and the 14:40-15:00 close (fade book + K7 NY-PM block). RANKING, POST-HOC, nothing here is a PASS, Shadow only

Capped 20260206, UNTOUCHED never read, no post-cap file opened. Prereg `l2vast/ds3/prereg/BETTER_S7_prereg.md` sha256 `a420d2b618d3e303a1955b5140e8fa2b9d579f2732d80398938db675f23a0bb5` (logged in DECISIONS.md before any S7 statistic; dead_lookup NOT FOUND for the session-table, the 15:55 close-fade and the NYPM block on the composite; prior art HEDGE1 `hs_stackfade` / `hs_uncond`, flat 15:50 / 16:00, noted). Code `l2vast/ds3/code/better_s7/`, outputs `l2vast/ds3/out/better/s7/` (sweep_off_*.pkl 384 daily series, a_cells_off.csv, close_scored.pkl, blk_scored_off.pkl, tables_all.md).
**BASE USED = the INTERIM base** (one-convention Sunday composite at live lots, 70/30 dip 3, PE 45-s NY, zone skip D 20, Asia cut 50%, ER(20) sizer all books with running-max locks, parity stop, slip +0.25, combined week lock OFF headline, 12R(K6) as sensitivity on finalists). Tie-out exact: live composite L6M +41.1k/wk, maxDD 22.9k, PRE maxDD 241.2k, ALL worst-20 -1,098k (DS3_ONE_CONVENTION / DS3_LOTS_DD). It lacks the D7-only pieces (TH-L2 exits, signal-state rules, X1-X5, OTE-62 B73, Native stops); the same scripts are re-run on `d7lib` (section D) and must be re-run on `out/d7base/` when BASE-1 delivers (one command, section F). Units $k per week; windows L3M 14 wk / L6M 28 / HOLD 32 / PRE 75 / X' 44 / ALL 149; PX = PRE+X' (the selection window). MDE = 2.8 x SE of the paired weekly delta, `*` / NO = beyond MDE. S/T/N = STRICT / TOLERANT (literal T-SIXTY addendum, `ddr_lib.tiers`) / NOW-ONLY; TOL-B / TOL-nc beside (post-hoc, never TOLERANT). dCalmar is Calmar (mean / weekly-cumulative maxDD) after minus before; because Calmar is scale-free it IS the Calmar change at equal risk; the equal-risk MEAN column is the mean change when the new stack's lots are scaled so ALL worst-20 matches the base (engine lot table re-run where no `~`, linear on the daily series where `~`).

## Page 1

**Plain sentence.** On the interim base, re-picking which sessions each book trades does not carry out of sample: the PX-selected (honest) session sets lose in L6M for 4 of the 6 books (K6, P6, H6, A6; the P6 pick is beyond its MDE), and a monthly walk-forward re-selection (trailing 6 months or expanding, score the next 3 months, 2024-26) ends below the live table in 10 of 12 book-by-window runs; only U6 and M6 with the expanding window are above live (forward 29.7 and 30.5 vs live 28.8, both inside their MDE, 3-month hit rates 0.62 and 0.88). The recent-window ranking (post-hoc) finds large Calmar gains that are real arithmetic but do not hold in PRE: the top one, M6 London+NY-AM -> London+Pre-open+NY-PM, moves the L6M maxDD from 22.9k to 10.6k at an unchanged mean (+0.5, MDE 4.5; dCalmar +2.13, beats 100% of the best-of-64 chance null) but that cut is two weeks (2025-10-20 and 2026-01-19, where M6's NY-AM trades lost about 12k each), PRE is -1.6, so it is NOW-ONLY (TOL-B yes, TOL-nc no). The sets that pass the literal TOLERANT gate are 40 of 371 distinct cells and are all U6 (12) or M6 (28): they pass because they ADD lots to two positive books, not because they swap risk; the cleanest are U6 add NY-AM at 4 lots (L6M +1.5 (4.7), HOLD +2.4, PRE +0.1, X' +1.2, maxDD 22.9 -> 22.6, ALL worst-20 -1,098 -> -1,041, dCalmar +0.08, equal-risk +3.8 linear / +2.5 engine for the +Pre variant) and M6 drop London / add NY-PM (AM+PM at 2 lots: L6M +0.4 (4.8), maxDD 22.9 -> 15.4, dCalmar +0.90, PRE +0.7, X' +0.0, STRICT+TOLERANT+NOW, equal-risk ~ +2.9), the best joint line is U6 +Pre+NY-AM with M6 AM+PM (drop London, add NY-PM): L6M +2.6 (MDE 6.3), L6M maxDD 22.9 -> 15.6 (-32%), PRE maxDD 241 -> 206 (-15%), X' 121 -> 91 (-25%), ALL worst-20 -1,098 -> -994 (+9%), dCalmar +1.00, STRICT+TOLERANT+NOW, and it stays STN under the 12R combined lock (+1.2 (6.0); there dCalmar -0.03); with M6 +Asia+NY-PM instead of the AM+PM set: +4.9 (7.0), L6M maxDD 24.6, ALL worst-20 -1,043, also STN (joint table). M6 AM+PM ALONE deepens the PRE maxDD (241 -> 257), so the line is a U6+M6 pair, picked post-hoc from 371 cells (best-of-N null p = 1.00 on L6M for M6, 0.89 for U6) and not confirmed by the walk-forward except with the expanding window; under the 12R lock U6 alone falls to S-N. The 14:40-15:00 close does not give a book or a block that clears: the unconditional fade of the late-afternoon move is -2.3 pts per trade net (1,037 trades) and adds maxDD; the fade of the stack's own 14:40-15:00 signals (60 trades in 3 years; the 29 short-side ones average +22.6 pts) adds +8.1k to the ALL worst-20 (0.7% of 1,098k) at 3 lots with maxDD unchanged, but one episode carries all of it (leave-one-episode-out min -0.5k, 13 of 14 episodes keep it) and it beats the random-sign placebo at 0.84 (bar 0.95); the K7 NY-PM block 14:40-15:00 is a no-op at live lots (only K6 has NY-PM lots; L6M +0.003k, MDE 0.8; ALL maxDD 0; worst-20 +0.8k; placebo rank 0.51 on Calmar). **On the BASE-1 engine (BASE-noTH, section D) the same picture:** walk-forward 10 of 12 below live (U6 and M6 expanding the exceptions), TOLERANT cells only U6 / M6 / one H6 NY-PM add (10 of 342), the block -0.2k L6M and not NOW-ONLY, the stack-fade short side +2.5k on the ALL worst-20; the literal TH-L2-on draft is a different, much worse stack and should not be used to pick.

### Ranked table (post-hoc, ranked by L6M Calmar change at equal risk; sel. column: H = the PX-selected honest pick of its book, P = the L6M-best pick, T = best literal-TOLERANT pick; every pick shown is the fewest-session variant of its identical-result group)

| rank | family | what | sel. | L6M mean base->new $k/wk (MDE) | in MDE | L6M maxDD $k | ALL worst-20 $k | equal-risk mean L6M $k | dCalmar L6M | dCalmar PX | placebo | S/T/N | TOL-B/TOL-nc | HOLD / PRE / X' mean d $k | LOEO | D7 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | SESSION | M6 sessions Lo+AM -> Lo+Pre+PM | P | 41.1 -> 41.6 (4.5) | yes | 22.9 -> 10.6 | -1098.1 -> -1034.5 | -2.2 | +2.13 | -0.006 | same-size sets (n=20): Calmar rank 0.95, maxDD rank 0.95; best-of-64 null pct 1.00 | --N | 1/0 | +0.6 / -1.6 / +0.3 |  | D7: per-book session lot row (panel/lot table) (adds a session) |
| 2 | SESSION | M6 sessions Lo+AM -> AM+PM | T | 41.1 -> 41.6 (4.8) | yes | 22.9 -> 15.4 | -1098.1 -> -1036.8 | +2.9~ | +0.90 | -0.003 | same-size sets (n=14): Calmar rank 0.71, maxDD rank 0.71; best-of-64 null pct 1.00 | STN | 1/1 | +0.5 / +0.7 / +0.0 |  | D7: per-book session lot row (panel/lot table) (drops a session) |
| 3 | SESSION | K6 sessions As+Lo+AM+PM -> Lo+Pre+AM+Cl | P | 41.1 -> 39.4 (5.4) | yes | 22.9 -> 18.2 | -1098.1 -> -1097.0 | -1.7 | +0.37 | +0.004 | same-size sets (n=14): Calmar rank 0.93, maxDD rank 0.93; best-of-64 null pct 1.00 | --- | 0/0 | -1.4 / -2.3 / -0.1 |  | D7: per-book session lot row (panel/lot table) (drops a session) |
| 4 | SESSION | H6 sessions As+AM -> As+Pre+AM | P | 41.1 -> 41.5 (1.4) | yes | 22.9 -> 21.4 | -1098.1 -> -1110.3 | -0.5 | +0.15 | -0.005 | same-size sets (n=20): Calmar rank 0.95, maxDD rank 0.95; best-of-64 null pct 0.98 | --- | 0/0 | +0.1 / -0.7 / -0.0 |  | D7: per-book session lot row (panel/lot table) (adds a session) |
| 5 | SESSION | U6 sessions As+Lo -> As+Pre+AM | PT | 41.1 -> 43.3 (4.5) | yes | 22.9 -> 22.6 | -1098.1 -> -1039.5 | +2.5 | +0.12 | +0.026 | same-size sets (n=20): Calmar rank 0.95, maxDD rank 0.85; best-of-64 null pct 0.89 | STN | 1/1 | +3.3 / +0.2 / +1.1 |  | D7: per-book session lot row (panel/lot table) (adds a session) |
| 6 | SESSION | U6 sessions As+Lo -> As+Pre+AM+Cl | H | 41.1 -> 42.8 (4.7) | yes | 22.9 -> 22.6 | -1098.1 -> -1037.0 | +2.0 | +0.09 | +0.027 | same-size sets (n=15): Calmar rank 0.93, maxDD rank 0.93; best-of-64 null pct 0.89 | STN | 1/1 | +2.5 / +0.4 / +1.1 |  | D7: per-book session lot row (panel/lot table) (adds a session) |
| 7 | SESSION | A6 sessions As -> As+AM | P | 41.1 -> 39.9 (2.4) | yes | 22.9 -> 21.6 | -1098.1 -> -1119.4 | -2.6 | +0.05 | -0.002 | same-size sets (n=15): Calmar rank 0.93, maxDD rank 0.93; best-of-64 null pct 0.85 | --- | 0/0 | -0.9 / +0.5 / -0.4 |  | D7: per-book session lot row (panel/lot table) (adds a session) |
| 8 | CLOSE | close-fade UNCOND BOTH stop40 3 lots (M) |  | 41.1 -> 43.1 (3.1) | yes | 22.9 -> 23.9 | -1098.1 -> -1098.8 | +1.9~ | +0.01 | -0.006 | time dd 0.37/w20 0.86; sign 0.17/0.68 | --N | 1/0 | +1.3 / -0.5 / -0.2 | 5/14 ep>0, min -9.0k | D7: NEW 1-min close book (NT8 strategy, flat 15:55) |
| 9 | NYPM-BLOCK | K7 NY-PM block 1450-1500 (all books = K6 at live lots) |  | 41.1 -> 41.2 (0.6) | yes | 22.9 -> 22.9 | -1098.1 -> -1096.7 | +0.1~ | +0.00 | -0.001 | n/a (edge sens.) | --N | 1/0 | +0.1 / -0.1 / -0.1 |  | D7: entry-time block flag NYPM_END_BLOCK (shadow rule exists) |
| 10 | CLOSE | close-fade STACK BOTH stop40 3 lots (M) |  | 41.1 -> 41.2 (0.9) | yes | 22.9 -> 22.9 | -1098.1 -> -1091.7 | +0.3~ | +0.00 | -0.000 | time dd 0.56/w20 0.89; sign 0.00/0.81 | --N | 1/0 | -0.0 / -0.2 / +0.1 | 13/14 ep>0, min -2.8k | D7: NEW 1-min close book (NT8 strategy, flat 15:55) |
| 11 | CLOSE | close-fade STACK SHORT stop0 3 lots (M) |  | 41.1 -> 41.2 (0.1) | yes | 22.9 -> 22.9 | -1098.1 -> -1090.0 | +0.3~ | +0.00 | +0.001 | time dd 0.36/w20 0.96; sign 0.00/0.84 | --- | 0/0 | +0.0 / +0.3 / +0.4 | 13/14 ep>0, min -0.5k | D7: NEW 1-min close book (NT8 strategy, flat 15:55) |
| 12 | NYPM-BLOCK | K7 NY-PM block 1440-1500 (all books = K6 at live lots) |  | 41.1 -> 41.1 (0.8) | yes | 22.9 -> 22.9 | -1098.1 -> -1097.3 | +0.0~ | +0.00 | -0.000 | random 20-min: dCal rank 0.51, ALLdd 0.24, w20 0.62 | --N | 0/0 | -0.0 / -0.2 / +0.2 |  | D7: entry-time block flag NYPM_END_BLOCK (shadow rule exists) |
| 13 | SESSION | P6 sessions As+Lo+AM -> As+Lo+AM+Cl | P | 41.1 -> 41.1 (0.0) | yes | 22.9 -> 22.9 | -1098.1 -> -1093.2 | +0.2 | +0.00 | +0.000 | same-size sets (n=15): Calmar rank 0.93, maxDD rank 0.93; best-of-64 null pct 0.00 | --- | 0/0 | +0.0 / -0.0 / +0.2 |  | D7: per-book session lot row (panel/lot table) (adds a session) |
| 14 | CLOSE | close-fade STACK BOTH stop0 3 lots (M) |  | 41.1 -> 41.1 (1.3) | yes | 22.9 -> 22.9 | -1098.1 -> -1089.0 | +0.3~ | -0.00 | +0.001 | time dd 0.52/w20 0.93; sign 0.00/0.89 | --- | 0/0 | +0.1 / +0.2 / +0.1 | 13/14 ep>0, min -0.0k | D7: NEW 1-min close book (NT8 strategy, flat 15:55) |
| 15 | CLOSE | close-fade STACK SHORT stop40 3 lots (M) |  | 41.1 -> 41.1 (0.3) | yes | 22.9 -> 22.9 | -1098.1 -> -1090.0 | +0.3~ | -0.00 | +0.001 | time dd 0.39/w20 0.95; sign 0.00/0.84 | --- | 0/0 | -0.0 / +0.0 / +0.4 | 13/14 ep>0, min -0.5k | D7: NEW 1-min close book (NT8 strategy, flat 15:55) |
| 16 | NYPM-BLOCK | K7 NY-PM block 1440-1450 (all books = K6 at live lots) |  | 41.1 -> 41.1 (0.6) | yes | 22.9 -> 22.9 | -1098.1 -> -1098.6 | -0.1~ | -0.00 | +0.000 | n/a (edge sens.) | --- | 0/0 | -0.1 / -0.1 / +0.3 |  | D7: entry-time block flag NYPM_END_BLOCK (shadow rule exists) |
| 17 | NYPM-BLOCK | K7 NY-PM block 1430-1500 (all books = K6 at live lots) |  | 41.1 -> 40.9 (0.7) | yes | 22.9 -> 22.9 | -1098.1 -> -1096.0 | -0.2~ | -0.01 | +0.001 | n/a (edge sens.) | --- | 0/0 | -0.2 / -0.1 / +0.3 |  | D7: entry-time block flag NYPM_END_BLOCK (shadow rule exists) |
| 18 | NYPM-BLOCK | K7 NY-PM block 1430-1450 (all books = K6 at live lots) |  | 41.1 -> 40.8 (0.5) | yes | 22.9 -> 22.9 | -1098.1 -> -1097.2 | -0.3~ | -0.02 | +0.002 | n/a (edge sens.) | --- | 0/0 | -0.2 / +0.0 / +0.4 |  | D7: entry-time block flag NYPM_END_BLOCK (shadow rule exists) |
| 19 | SESSION | M6 sessions Lo+AM -> As+Lo+AM+PM | H | 41.1 -> 43.8 (5.8) | yes | 22.9 -> 24.9 | -1098.1 -> -1103.8 | +2.2 | -0.03 | +0.016 | same-size sets (n=15): Calmar rank 0.33, maxDD rank 0.33; best-of-64 null pct 1.00 | STN | 1/1 | +2.4 / +3.0 / +1.1 |  | D7: per-book session lot row (panel/lot table) (adds a session) |
| 20 | CLOSE | close-fade UNCOND SHORT stop40 3 lots (M) |  | 41.1 -> 42.5 (2.7) | yes | 22.9 -> 24.4 | -1098.1 -> -1099.4 | +1.3~ | -0.05 | -0.005 | time dd 0.15/w20 0.81; sign 0.01/0.86 | --N | 1/0 | +1.2 / -0.2 / +0.5 | 3/14 ep>0, min -11.0k | D7: NEW 1-min close book (NT8 strategy, flat 15:55) |
| 21 | CLOSE | close-fade UNCOND BOTH stop0 3 lots (M) |  | 41.1 -> 41.5 (3.5) | yes | 22.9 -> 25.7 | -1098.1 -> -1113.2 | -0.2~ | -0.18 | -0.007 | time dd 0.23/w20 0.73; sign 0.07/0.60 | --N | 1/1 | +0.1 / +0.6 / -0.4 | 0/14 ep>0, min -27.3k | D7: NEW 1-min close book (NT8 strategy, flat 15:55) |
| 22 | CLOSE | close-fade UNCOND SHORT stop0 3 lots (M) |  | 41.1 -> 41.7 (3.0) | yes | 22.9 -> 26.1 | -1098.1 -> -1087.3 | +1.0~ | -0.20 | -0.004 | time dd 0.15/w20 0.89; sign 0.02/0.94 | S-N | 1/1 | +0.5 / +0.3 / +0.6 | 14/14 ep>0, min +0.0k | D7: NEW 1-min close book (NT8 strategy, flat 15:55) |
| 23 | SESSION | A6 sessions As -> As+PM | H | 41.1 -> 41.0 (1.7) | yes | 22.9 -> 25.8 | -1098.1 -> -1105.2 | -0.6 | -0.21 | +0.003 | same-size sets (n=15): Calmar rank 0.67, maxDD rank 0.67; best-of-64 null pct 0.85 | --- | 0/0 | -0.3 / +0.2 / -0.1 |  | D7: per-book session lot row (panel/lot table) (adds a session) |
| 24 | SESSION | K6 sessions As+Lo+AM+PM -> As+AM | H | 41.1 -> 37.9 (4.1) | yes | 22.9 -> 25.2 | -1098.1 -> -1028.9 | -4.8 | -0.29 | +0.013 | same-size sets (n=15): Calmar rank 0.67, maxDD rank 0.60; best-of-64 null pct 1.00 | --- | 0/0 | -2.8 / +0.6 / -0.0 |  | D7: per-book session lot row (panel/lot table) (drops a session) |
| 25 | SESSION | P6 sessions As+Lo+AM -> As | H | 41.1 -> 28.0 (12.7) | NO* | 22.9 -> 32.1 | -1098.1 -> -822.2 | -4.7 | -0.93 | +0.045 | same-size sets (n=6): Calmar rank 0.83, maxDD rank 0.83; best-of-64 null pct 0.00 | --- | 0/0 | -13.5 / -5.4 / -4.1 |  | D7: per-book session lot row (panel/lot table) (drops a session) |
| 26 | SESSION | H6 sessions As+AM -> Lo | H | 41.1 -> 33.3 (8.4) | yes | 22.9 -> 40.8 | -1098.1 -> -1054.4 | -9.2 | -0.98 | +0.018 | same-size sets (n=6): Calmar rank 0.00, maxDD rank 0.00; best-of-64 null pct 0.98 | --- | 0/0 | -7.2 / -0.8 / +1.2 |  | D7: per-book session lot row (panel/lot table) (drops a session) |

The sessions part of this table is 13 rows of the 384 cells (the six honest picks, the six L6M-best picks, the best TOLERANT picks); the other 371 are in `a_cells_off.csv` with every column. Close-book rows are 3 lots with measured fills (LIVE-CAL beside in section B); NYPM-BLOCK rows: scopes all-books, K6-only and A6+K6 give the SAME result at live lots (K6 is the only book with NY-PM lots; A6 is Asia-only), so one row per window.

### Honest ranking (selected on PX = PRE+X' only, judged on L6M and HOLD; the pick is the rank-1 line of each family)

Sessions (one pick per book, selected on PX Calmar subject to PX mean >= base - MDE, shown ranked by PX dCalmar; the judgement columns are L6M dCalmar, the L6M mean and HOLD):

| rank | family | what | sel. | L6M mean base->new $k/wk (MDE) | in MDE | L6M maxDD $k | ALL worst-20 $k | equal-risk mean L6M $k | dCalmar L6M | dCalmar PX | placebo | S/T/N | TOL-B/TOL-nc | HOLD / PRE / X' mean d $k | LOEO | D7 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | SESSION | P6 sessions As+Lo+AM -> As | H | 41.1 -> 28.0 (12.7) | NO* | 22.9 -> 32.1 | -1098.1 -> -822.2 | -4.7 | -0.93 | +0.045 | same-size sets (n=6): Calmar rank 0.83, maxDD rank 0.83; best-of-64 null pct 0.00 | --- | 0/0 | -13.5 / -5.4 / -4.1 |  | D7: per-book session lot row (panel/lot table) (drops a session) |
| 2 | SESSION | U6 sessions As+Lo -> As+Pre+AM+Cl | H | 41.1 -> 42.8 (4.7) | yes | 22.9 -> 22.6 | -1098.1 -> -1037.0 | +2.0 | +0.09 | +0.027 | same-size sets (n=15): Calmar rank 0.93, maxDD rank 0.93; best-of-64 null pct 0.89 | STN | 1/1 | +2.5 / +0.4 / +1.1 |  | D7: per-book session lot row (panel/lot table) (adds a session) |
| 3 | SESSION | H6 sessions As+AM -> Lo | H | 41.1 -> 33.3 (8.4) | yes | 22.9 -> 40.8 | -1098.1 -> -1054.4 | -9.2 | -0.98 | +0.018 | same-size sets (n=6): Calmar rank 0.00, maxDD rank 0.00; best-of-64 null pct 0.98 | --- | 0/0 | -7.2 / -0.8 / +1.2 |  | D7: per-book session lot row (panel/lot table) (drops a session) |
| 4 | SESSION | M6 sessions Lo+AM -> As+Lo+AM+PM | H | 41.1 -> 43.8 (5.8) | yes | 22.9 -> 24.9 | -1098.1 -> -1103.8 | +2.2 | -0.03 | +0.016 | same-size sets (n=15): Calmar rank 0.33, maxDD rank 0.33; best-of-64 null pct 1.00 | STN | 1/1 | +2.4 / +3.0 / +1.1 |  | D7: per-book session lot row (panel/lot table) (adds a session) |
| 5 | SESSION | K6 sessions As+Lo+AM+PM -> As+AM | H | 41.1 -> 37.9 (4.1) | yes | 22.9 -> 25.2 | -1098.1 -> -1028.9 | -4.8 | -0.29 | +0.013 | same-size sets (n=15): Calmar rank 0.67, maxDD rank 0.60; best-of-64 null pct 1.00 | --- | 0/0 | -2.8 / +0.6 / -0.0 |  | D7: per-book session lot row (panel/lot table) (drops a session) |
| 6 | SESSION | A6 sessions As -> As+PM | H | 41.1 -> 41.0 (1.7) | yes | 22.9 -> 25.8 | -1098.1 -> -1105.2 | -0.6 | -0.21 | +0.003 | same-size sets (n=15): Calmar rank 0.67, maxDD rank 0.67; best-of-64 null pct 0.85 | --- | 0/0 | -0.3 / +0.2 / -0.1 |  | D7: per-book session lot row (panel/lot table) (adds a session) |

Close book (8 cells, PX score at 3 lots, measured fills):

| PX rank | cell | PX score (mean of maxDD cut %, worst-20 cut %) | PX own mean ok | L6M dCal (judge) | HOLD mean d $k | S/T/N |
|---|---|---|---|---|---|---|
| 1 | STACK|BOTH|stop0 | +0.0038 | yes | -0.001 | +0.1 | --- |
| 2 | STACK|SHORT|stop40 | +0.0037 | yes | -0.002 | -0.0 | --- |
| 3 | STACK|SHORT|stop0 | +0.0037 | yes | +0.001 | +0.0 | --- |
| 4 | STACK|BOTH|stop40 | +0.0024 | yes | +0.003 | -0.0 | --N |
| 5 | UNCOND|BOTH|stop40 | -0.0313 | yes | +0.008 | +1.3 | --N |
| 6 | UNCOND|SHORT|stop0 | -0.0379 | yes | -0.202 | +0.5 | S-N |
| 7 | UNCOND|SHORT|stop40 | -0.0411 | yes | -0.052 | +1.2 | --N |
| 8 | UNCOND|BOTH|stop0 | -0.0648 | yes | -0.181 | +0.1 | --N |

K7 block windows (PX dCalmar):

| PX rank | window | PX dCalmar | L6M dCalmar (judge) | HOLD mean d $k |
|---|---|---|---|---|
| 1 | 1430-1450 | +0.0018 | -0.016 | -0.2 |
| 2 | 1430-1500 | +0.0013 | -0.012 | -0.2 |
| 3 | 1440-1450 | +0.0002 | -0.004 | -0.1 |
| 4 | 1440-1500 | -0.0003 | +0.000 | -0.0 |
| 5 | 1450-1500 | -0.0005 | +0.004 | +0.1 |

Honest reading: the PX-selected session sets keep L6M Calmar only for U6 (+0.09) and M6 (-0.03, i.e. flat); K6 (-0.29), P6 (-0.93), H6 (-0.98), A6 (-0.21) lose it, because PX Calmar is one 241k PRE drawdown episode and the sets that avoid it (P6 Asia only, H6 London) give up the recent months. The close-book and block honest picks have no L6M edge either (dCalmar -0.001, -0.016).


### RISK-KEEP labels (standing order: maxDD cut >= 20% in L6M with the mean inside MDE; placebo = same-size random sets; PRE / X' agree = both >= 20%)

* M6 AM+PM (drop London, add NY-PM): L6M maxDD 22.9 -> 15.4 (-33%), mean +0.4 (4.8): meets the L6M definition; same-size placebo rank 0.71 (below the 0.95 bar), PRE maxDD gets WORSE (241 -> 257): **RISK-KEEP (L6M only), does not beat the placebo, PRE disagrees**.
* M6 London+Pre+NY-PM: -54% (22.9 -> 10.6), mean +0.5 (4.5), same-size rank 0.95, best-of-64 null 1.00, PRE mean -1.6: **RISK-KEEP (L6M only), carried by two weeks, PRE disagrees on the mean**.
* U6 +Pre+NY-AM with M6 AM+PM (pair): L6M maxDD -32% (22.9 -> 15.6), PRE -15%, X' -25%, mean +2.6 (6.3): **L6M RISK-KEEP; PRE misses the 20% bar (-15%), X' agrees; STRICT+TOLERANT**; it adds U6 lots (equal-risk ~ +1 to +2.5), not a pure risk swap.
* K6 London+Pre+NY-AM(+Close): L6M maxDD -21%, mean -1.7 (inside 5.4), PRE -2.3 (fails TOLERANT), ALL worst-20 unchanged: volume effect (it drops Asia and NY-PM lots).
* Close book / NY-PM block: none cuts a maxDD (STACK short-side: 0.0 on L6M / PRE; +8.1k on the ALL worst-20 only).

## A. Per-book SESSION re-selection (384 cells: 6 books x 64 session subsets, lot per ON session = its live lot or the book's smallest live lot)

Cell definition (prereg): a subset of {Asia, London, Pre-open, NY-AM, NY-PM, Close} ON for one book, all others at live lots; sessions with no live lot get the book's smallest live session lot (K6 2, P6 7, U6 4, H6 2, M6 2, A6 1); the engine (running-max locks, ER sizer, PE, zone skip, Asia cut, per-book locks) runs on the whole stack. 7 of the 378 non-live cells are identical to another (the Close and Pre-open sessions have few trades); the tables show the fewest-session variant. Of the 371 distinct cells: STRICT 34 / TOLERANT 40 / NOW-ONLY 95 / TOL-B 74 / TOL-nc 51; by book TOLERANT: M6 28, U6 12, K6 0, P6 0, H6 0, A6 0 (STRICT: M6 26, U6 8). Live lots: K6 2 Asia/London/NY-AM/NY-PM; P6 7 Asia/London/NY-AM; U6 4 Asia/London; H6 4 Asia / 2 NY-AM; M6 2 London/NY-AM; A6 1 Asia.

### A1. Per book: current table, honest (PX-selected) top 3 and L6M-best top 3 (dedup), L6M Calmar, PX Calmar, equal-risk mean (~ linear), tiers

**K6: live = As+Lo+AM+PM (2 Asia/London/NY-AM/NY-PM)**

| set | kind | L6M mean d (MDE) | L6M maxDD | L6M Calmar (live 1.80) | PX Calmar (live 0.073) | ALL worst-20 | HOLD / PRE / X' mean d | eq-risk L6M (~) | S/T/N | TOL-B/TOL-nc |
|---|---|---|---|---|---|---|---|---|---|---|
| As+AM | honest | -3.2 (4.1) | 25.2 | 1.50 | 0.086 | -1028.9 | -2.8 / +0.6 / -0.0 | -0.7 | --- | 0/0 |
| As+Pre+AM | honest | -3.5 (4.2) | 22.8 | 1.65 | 0.085 | -1053.5 | -3.4 / +0.6 / -0.1 | -1.9 | --- | 0/0 |
| As+AM+Cl | honest | -3.3 (4.1) | 25.2 | 1.50 | 0.085 | -1034.0 | -2.8 / +0.5 / -0.0 | -0.9 | --- | 0/0 |
| Lo+Pre+AM+Cl | post | -1.7 (5.4) | 18.2 | 2.17 | 0.077 | -1097.0 | -1.4 / -2.3 / -0.1 | -1.7 | --- | 0/0 |
| Lo+Pre+AM | post | -1.7 (5.4) | 18.2 | 2.17 | 0.077 | -1089.8 | -1.4 / -2.2 / -0.1 | -1.4 | --- | 0/0 |
| Lo+AM+Cl | post | -1.7 (5.1) | 19.4 | 2.04 | 0.077 | -1078.2 | -1.1 / -2.4 / +0.1 | -1.0 | --- | 0/0 |

**P6: live = As+Lo+AM (7 Asia/London/NY-AM)**

| set | kind | L6M mean d (MDE) | L6M maxDD | L6M Calmar (live 1.80) | PX Calmar (live 0.073) | ALL worst-20 | HOLD / PRE / X' mean d | eq-risk L6M (~) | S/T/N | TOL-B/TOL-nc |
|---|---|---|---|---|---|---|---|---|---|---|
| As | honest | -13.2 (12.7) | 32.1 | 0.87 | 0.118 | -822.2 | -13.5 / -5.4 / -4.1 | -3.8 | --- | 0/0 |
| As+Cl | honest | -13.2 (12.7) | 32.1 | 0.87 | 0.118 | -827.2 | -13.5 / -5.5 / -3.9 | -4.0 | --- | 0/0 |
| As+Pre | honest | -13.3 (14.5) | 55.4 | 0.50 | 0.103 | -919.5 | -14.7 / -6.4 / -4.7 | -7.9 | --- | 0/0 |
| As+Lo+AM+Cl | post | +0.0 (0.0) | 22.9 | 1.80 | 0.074 | -1093.2 | +0.0 / -0.0 / +0.2 | +0.2 | --- | 0/0 |
| As+Lo+AM+PM+Cl | post | -1.2 (4.7) | 27.5 | 1.45 | 0.078 | -1219.7 | -1.1 / +0.7 / -0.7 | -5.2 | --- | 0/0 |
| As+Lo+AM+PM | post | -1.2 (4.7) | 27.5 | 1.45 | 0.078 | -1219.7 | -1.1 / +0.6 / -0.7 | -5.2 | --- | 0/0 |

**U6: live = As+Lo (4 Asia/London)**

| set | kind | L6M mean d (MDE) | L6M maxDD | L6M Calmar (live 1.80) | PX Calmar (live 0.073) | ALL worst-20 | HOLD / PRE / X' mean d | eq-risk L6M (~) | S/T/N | TOL-B/TOL-nc |
|---|---|---|---|---|---|---|---|---|---|---|
| As+Pre+AM+Cl | honest | +1.7 (4.7) | 22.6 | 1.89 | 0.100 | -1037.0 | +2.5 / +0.4 / +1.1 | +4.2 | STN | 1/1 |
| As+Pre+AM | honest | +2.2 (4.5) | 22.6 | 1.91 | 0.100 | -1039.5 | +3.3 / +0.2 / +1.1 | +4.6 | STN | 1/1 |
| As+AM+Cl | honest | +1.0 (4.9) | 22.6 | 1.86 | 0.098 | -1038.9 | +1.7 / +0.3 / +1.2 | +3.4 | STN | 1/1 |
| As+Pre+AM | post | +2.2 (4.5) | 22.6 | 1.91 | 0.100 | -1039.5 | +3.3 / +0.2 / +1.1 | +4.6 | STN | 1/1 |
| As+Pre+AM+Cl | post | +1.7 (4.7) | 22.6 | 1.89 | 0.100 | -1037.0 | +2.5 / +0.4 / +1.1 | +4.2 | STN | 1/1 |
| As+AM | post | +1.5 (4.7) | 22.6 | 1.88 | 0.097 | -1041.4 | +2.4 / +0.1 / +1.2 | +3.8 | STN | 1/1 |

**H6: live = As+AM (4 Asia / 2 NY-AM)**

| set | kind | L6M mean d (MDE) | L6M maxDD | L6M Calmar (live 1.80) | PX Calmar (live 0.073) | ALL worst-20 | HOLD / PRE / X' mean d | eq-risk L6M (~) | S/T/N | TOL-B/TOL-nc |
|---|---|---|---|---|---|---|---|---|---|---|
| Lo | honest | -7.8 (8.4) | 40.8 | 0.82 | 0.091 | -1054.4 | -7.2 / -0.8 / +1.2 | -6.4 | --- | 0/0 |
| Lo+Cl | honest | -7.8 (8.4) | 40.8 | 0.82 | 0.091 | -1054.4 | -7.2 / -0.8 / +1.2 | -6.4 | --- | 0/0 |
| Lo+AM | honest | -5.3 (7.1) | 31.5 | 1.13 | 0.089 | -1066.2 | -5.3 / +0.2 / +0.6 | -4.3 | --- | 0/0 |
| As+Pre+AM | post | +0.4 (1.4) | 21.4 | 1.94 | 0.069 | -1110.3 | +0.1 / -0.7 / -0.0 | -0.1 | --- | 0/0 |
| As+Pre+AM+Cl | post | +0.4 (1.4) | 21.4 | 1.94 | 0.069 | -1110.3 | +0.1 / -0.7 / -0.0 | -0.1 | --- | 0/0 |
| As+AM+Cl | post | +0.0 (0.0) | 22.9 | 1.80 | 0.073 | -1098.1 | -0.0 / -0.0 / +0.0 | +0.0 | --- | 0/0 |

**M6: live = Lo+AM (2 London/NY-AM)**

| set | kind | L6M mean d (MDE) | L6M maxDD | L6M Calmar (live 1.80) | PX Calmar (live 0.073) | ALL worst-20 | HOLD / PRE / X' mean d | eq-risk L6M (~) | S/T/N | TOL-B/TOL-nc |
|---|---|---|---|---|---|---|---|---|---|---|
| As+Lo+AM+PM | honest | +2.7 (5.8) | 24.9 | 1.76 | 0.089 | -1103.8 | +2.4 / +3.0 / +1.1 | +2.5 | STN | 1/1 |
| As+Lo+AM+Cl | honest | +2.1 (4.6) | 33.7 | 1.28 | 0.088 | -1103.7 | +1.8 / +2.6 / +1.1 | +1.9 | STN | 1/1 |
| As+Lo+AM | honest | +2.1 (4.6) | 33.7 | 1.28 | 0.088 | -1103.7 | +1.8 / +2.6 / +1.1 | +1.9 | STN | 1/1 |
| Lo+Pre+PM | post | +0.5 (4.5) | 10.6 | 3.93 | 0.067 | -1034.5 | +0.6 / -1.6 / +0.3 | +3.1 | --N | 1/0 |
| Lo+Pre+PM+Cl | post | +0.5 (4.5) | 10.6 | 3.93 | 0.069 | -1034.5 | +0.6 / -1.5 / +0.3 | +3.1 | --N | 1/0 |
| Lo+PM+Cl | post | +0.3 (4.1) | 13.0 | 3.19 | 0.071 | -1024.0 | +0.8 / -1.8 / +0.4 | +3.3 | --N | 0/0 |

**A6: live = As (1 Asia)**

| set | kind | L6M mean d (MDE) | L6M maxDD | L6M Calmar (live 1.80) | PX Calmar (live 0.073) | ALL worst-20 | HOLD / PRE / X' mean d | eq-risk L6M (~) | S/T/N | TOL-B/TOL-nc |
|---|---|---|---|---|---|---|---|---|---|---|
| As+PM | honest | -0.2 (1.7) | 25.8 | 1.59 | 0.077 | -1105.2 | -0.3 / +0.2 / -0.1 | -0.4 | --- | 0/0 |
| As+PM+Cl | honest | -0.3 (1.7) | 25.8 | 1.58 | 0.075 | -1108.1 | -0.4 / -0.1 / -0.0 | -0.6 | --- | 0/0 |
| As+AM | honest | -1.3 (2.4) | 21.6 | 1.85 | 0.071 | -1119.4 | -0.9 / +0.5 / -0.4 | -2.0 | --- | 0/0 |
| As+AM | post | -1.3 (2.4) | 21.6 | 1.85 | 0.071 | -1119.4 | -0.9 / +0.5 / -0.4 | -2.0 | --- | 0/0 |
| As+AM+Cl | post | -1.4 (2.4) | 21.6 | 1.84 | 0.070 | -1123.9 | -1.0 / +0.2 / -0.7 | -2.3 | --- | 0/0 |
| As+Pre+AM+PM | post | -0.9 (2.9) | 21.9 | 1.84 | 0.063 | -1139.9 | -0.8 / -0.6 / -0.4 | -2.4 | --- | 0/0 |

### A2. Best-of-N chance null (is the L6M best-of-64 gain more than selection on a 28-week window finds anywhere in PRE+X'?)

| book | L6M best-of-64 dCalmar (mean-constrained) | null (all 28-wk windows of PX): median | p95 | real percentile in null |
|---|---|---|---|---|
| K6 | +0.369 | +0.017 | +0.195 | 1.00 |
| P6 | +0.000 | +0.105 | +0.421 | 0.00 |
| U6 | +0.117 | +0.040 | +0.124 | 0.89 |
| H6 | +0.146 | +0.049 | +0.126 | 0.98 |
| M6 | +2.133 | +0.036 | +0.187 | 1.00 |
| A6 | +0.048 | +0.013 | +0.063 | 0.85 |

Reading: K6, M6, H6 beat 98-100% of the in-window best-of-64 gains (so the L6M-best pick is not just "best of 64"), U6 0.89 and A6 0.85 do not; P6's live table is already the best (no alternative improves it). Beating the best-of-N null on L6M says nothing about PRE (K6 L6M-best is -2.3 in PRE, M6 L6M-best -1.6). Placebo (random session assignment of the same count, enumerated exactly, in the placebo column of the ranked table): for post-hoc picks the same-size rank is about 1 - 1/n by construction; for the honest and TOLERANT picks it is informative: U6 0.93-0.95 (among the best of their size), M6 AM+PM 0.71, M6 honest 0.33, K6 0.67, A6 0.67, P6 0.83, H6 0.00.

### A3. Walk-forward: does session re-selection carry? (select per book on the trailing 6 months or the expanding window to month M subject to mean >= live - MDE, maximise Calmar; score months M+1..M+3; 3-month steps 2024-01..2025-10, 8 segments chained; other books live; full-week series, so the chained live line is the same for every book)

| book | selection window | segments changed vs live | chained fwd mean live -> selected $k/wk (MDE) | fwd maxDD live -> sel | fwd Calmar live -> sel | hit rate (mean up) 3-mo segs | monthly hit (n changed) |
|---|---|---|---|---|---|---|---|
| K6 | roll6 | 8/8 | 28.8 -> 27.5 (2.1) | 241.2 -> 210.1 | 0.119 -> 0.131 | 0.12 | 0.23 (22/22) |
| K6 | expand | 8/8 | 28.8 -> 28.2 (2.5) | 241.2 -> 210.1 | 0.119 -> 0.134 | 0.12 | 0.32 (22/22) |
| P6 | roll6 | 8/8 | 28.8 -> 17.7 (8.8) | 241.2 -> 176.1 | 0.119 -> 0.100 | 0.12 | 0.14 (22/22) |
| P6 | expand | 8/8 | 28.8 -> 21.6 (7.7) | 241.2 -> 195.9 | 0.119 -> 0.110 | 0.25 | 0.32 (22/22) |
| U6 | roll6 | 8/8 | 28.8 -> 27.8 (2.9) | 241.2 -> 284.3 | 0.119 -> 0.098 | 0.38 | 0.45 (22/22) |
| U6 | expand | 8/8 | 28.8 -> 29.7 (3.1) | 241.2 -> 224.8 | 0.119 -> 0.132 | 0.62 | 0.77 (22/22) |
| H6 | roll6 | 7/8 | 28.8 -> 26.1 (3.2) | 241.2 -> 214.0 | 0.119 -> 0.122 | 0.29 | 0.24 (21/22) |
| H6 | expand | 8/8 | 28.8 -> 26.2 (3.7) | 241.2 -> 195.4 | 0.119 -> 0.134 | 0.25 | 0.32 (22/22) |
| M6 | roll6 | 8/8 | 28.8 -> 28.6 (3.0) | 241.2 -> 265.2 | 0.119 -> 0.108 | 0.38 | 0.41 (22/22) |
| M6 | expand | 8/8 | 28.8 -> 30.5 (2.8) | 241.2 -> 247.1 | 0.119 -> 0.123 | 0.88 | 0.82 (22/22) |
| A6 | roll6 | 8/8 | 28.8 -> 27.8 (1.4) | 241.2 -> 255.5 | 0.119 -> 0.109 | 0.12 | 0.27 (22/22) |
| A6 | expand | 7/8 | 28.8 -> 28.2 (0.9) | 241.2 -> 255.5 | 0.119 -> 0.111 | 0.00 | 0.26 (19/22) |
| ALL SIX (additive) | roll6 | - | 28.8 -> 11.6 (11.5) | 241.2 -> 115.1 | 0.119 -> 0.101 | | |
| ALL SIX (additive) | expand | - | 28.8 -> 20.7 (10.2) | 241.2 -> 145.8 | 0.119 -> 0.142 | | |

Reading: the selected session table is changed in nearly every segment (7-8 of 8) and the forward mean is below live in 10 of the 12 book-by-window runs (P6 -11.1 / -7.2, K6 -1.3 / -0.6, A6 -1.0 / -0.5, H6 -2.7 / -2.5, U6 roll6 -1.0, M6 roll6 -0.2); the forward maxDD is lower in 7 of 12 and higher in 5 (U6 roll6 284 vs 241, M6 265 / 247, A6 256). Hit rates (share of changed 3-month segments with a forward mean above live) are 0.00-0.38 except U6 expanding (0.62 / monthly 0.77) and M6 expanding (0.88 / monthly 0.82), the two books whose additions are what the TOLERANT cells are. Pooled over all six re-selected at once (additive approximation): roll6 11.6 vs 28.8, expanding 20.7 vs 28.8, with the forward maxDD cut to 115 / 146 from 241 (the one PRE episode again). Verdict: re-selecting sessions every quarter does not beat the live table; the exception is an expanding-window preference for "more lots on U6 / M6".

### A4. Finalists under the 12R(K6) combined week lock (vs live under 12R)

| book | set | pick kind | L6M mean d vs live (12R) | L6M maxDD live-12R -> set-12R | PRE maxDD | X' maxDD | dCalmar L6M (12R) | S/T/N (12R) |
|---|---|---|---|---|---|---|---|---|
| A6 | As+AM | post | -1.1 (1.9) | 26.6 -> 32.9 | 232.6 -> 230.2 | 119.6 -> 141.1 | -0.27 | --- |
| A6 | As+AM+Cl | runner-up | -1.3 (1.8) | 26.6 -> 32.9 | 232.6 -> 230.2 | 119.6 -> 141.1 | -0.27 | --- |
| A6 | As+PM | honest | -0.2 (1.6) | 26.6 -> 24.3 | 232.6 -> 252.7 | 119.6 -> 120.3 | +0.11 | --- |
| A6 | As+PM+Cl | runner-up | -0.3 (1.5) | 26.6 -> 24.3 | 232.6 -> 252.7 | 119.6 -> 113.5 | +0.11 | --- |
| A6 | As+Pre+AM+PM | runner-up | -1.0 (3.2) | 26.6 -> 42.9 | 232.6 -> 247.5 | 119.6 -> 143.4 | -0.48 | --- |
| H6 | As+AM+Cl | runner-up | +0.0 (0.0) | 26.6 -> 26.6 | 232.6 -> 232.6 | 119.6 -> 119.6 | +0.00 | --- |
| H6 | As+Pre+AM | post | +0.2 (0.9) | 26.6 -> 26.6 | 232.6 -> 236.3 | 119.6 -> 118.8 | +0.01 | --- |
| H6 | As+Pre+AM+Cl | runner-up | +0.2 (0.9) | 26.6 -> 26.6 | 232.6 -> 236.3 | 119.6 -> 118.8 | +0.01 | --- |
| H6 | Lo | honest | -5.4 (20.5) | 26.6 -> 51.7 | 232.6 -> 149.5 | 119.6 -> 119.6 | -0.69 | --- |
| H6 | Lo+Cl | runner-up | -5.4 (20.5) | 26.6 -> 51.7 | 232.6 -> 149.5 | 119.6 -> 119.6 | -0.69 | --- |
| H6 | Lo+AM | runner-up | -4.8 (20.7) | 26.6 -> 51.7 | 232.6 -> 242.0 | 119.6 -> 124.5 | -0.68 | --- |
| K6 | As+AM | honest | -2.6 (3.8) | 26.6 -> 32.6 | 232.6 -> 182.5 | 119.6 -> 158.0 | -0.30 | --- |
| K6 | As+AM+Cl | runner-up | -2.7 (3.9) | 26.6 -> 32.6 | 232.6 -> 181.3 | 119.6 -> 157.9 | -0.30 | --- |
| K6 | As+Pre+AM | runner-up | -2.7 (3.9) | 26.6 -> 34.9 | 232.6 -> 178.4 | 119.6 -> 164.5 | -0.36 | --- |
| K6 | Lo+AM+Cl | runner-up | -9.7 (23.3) | 26.6 -> 58.2 | 232.6 -> 346.3 | 119.6 -> 116.5 | -0.82 | --- |
| K6 | Lo+Pre+AM | runner-up | -9.4 (23.3) | 26.6 -> 58.5 | 232.6 -> 334.5 | 119.6 -> 125.5 | -0.82 | --- |
| K6 | Lo+Pre+AM+Cl | post | -9.4 (23.3) | 26.6 -> 58.5 | 232.6 -> 334.5 | 119.6 -> 125.5 | -0.82 | --- |
| M6 | As+Lo+AM | runner-up | -0.4 (7.1) | 26.6 -> 43.6 | 232.6 -> 231.5 | 119.6 -> 145.6 | -0.48 | --- |
| M6 | As+Lo+AM+Cl | runner-up | -0.4 (7.1) | 26.6 -> 43.6 | 232.6 -> 231.5 | 119.6 -> 145.6 | -0.48 | --- |
| M6 | As+Lo+AM+PM | honest | -0.1 (7.4) | 26.6 -> 43.6 | 232.6 -> 231.4 | 119.6 -> 146.5 | -0.47 | --- |
| M6 | Lo+PM+Cl | runner-up | +4.9 (11.3) | 26.6 -> 25.9 | 232.6 -> 230.8 | 119.6 -> 144.4 | +0.22 | --N |
| M6 | Lo+Pre+PM | post | +4.3 (11.4) | 26.6 -> 43.2 | 232.6 -> 236.5 | 119.6 -> 146.4 | -0.37 | S-N |
| M6 | Lo+Pre+PM+Cl | runner-up | +4.3 (11.4) | 26.6 -> 43.2 | 232.6 -> 236.5 | 119.6 -> 146.4 | -0.37 | S-N |
| P6 | As | honest | -7.9 (12.6) | 26.6 -> 17.0 | 232.6 -> 102.9 | 119.6 -> 142.9 | +0.22 | --- |
| P6 | As+Cl | runner-up | -7.9 (12.6) | 26.6 -> 17.0 | 232.6 -> 102.9 | 119.6 -> 142.9 | +0.22 | --- |
| P6 | As+Lo+AM+Cl | post | +0.0 (0.0) | 26.6 -> 26.6 | 232.6 -> 232.6 | 119.6 -> 119.6 | +0.00 | --- |
| P6 | As+Lo+AM+PM | runner-up | -1.9 (3.8) | 26.6 -> 32.5 | 232.6 -> 236.6 | 119.6 -> 145.3 | -0.28 | --- |
| P6 | As+Lo+AM+PM+Cl | runner-up | -1.9 (3.8) | 26.6 -> 32.5 | 232.6 -> 236.6 | 119.6 -> 145.3 | -0.28 | --- |
| P6 | As+Pre | runner-up | -6.4 (12.6) | 26.6 -> 53.0 | 232.6 -> 135.2 | 119.6 -> 127.1 | -0.72 | --- |
| U6 | As+AM | runner-up | +0.7 (4.3) | 26.6 -> 32.1 | 232.6 -> 133.0 | 119.6 -> 163.3 | -0.19 | -TN |
| U6 | As+AM+Cl | runner-up | +0.4 (4.5) | 26.6 -> 32.1 | 232.6 -> 133.0 | 119.6 -> 163.3 | -0.19 | -TN |
| U6 | As+Pre+AM | post | +1.4 (4.4) | 26.6 -> 32.1 | 232.6 -> 133.0 | 119.6 -> 143.5 | -0.16 | S-N |
| U6 | As+Pre+AM+Cl | honest | +1.1 (4.6) | 26.6 -> 32.1 | 232.6 -> 133.0 | 119.6 -> 143.5 | -0.17 | --N |

### A5. Joint runs (all the picks together in one engine run, interaction included)

| joint set | lock | L6M mean (d, MDE) | L6M maxDD | PRE maxDD | X' maxDD | ALL worst-20 | dCalmar L6M | dCalmar PX | S/T/N |
|---|---|---|---|---|---|---|---|---|---|
| honest_all = K6 As+AM, P6 As, U6 As+Pre+AM+Cl, H6 Lo, M6 As+Lo+AM+PM+Cl, A6 As+PM | off | 21.6 (-19.5, 14.2) | 22.9 -> 52.5 | 241.2 -> 65.9 | 120.5 -> 72.7 | -1098.1 -> -748.0 | -1.38 | +0.1430 | --- |
| honest_all = K6 As+AM, P6 As, U6 As+Pre+AM+Cl, H6 Lo, M6 As+Lo+AM+PM+Cl, A6 As+PM | 12R | 17.2 (-15.1, 21.9) | 26.6 -> 43.5 | 232.6 -> 98.6 | 119.6 -> 82.0 | -688.5 -> -516.7 | -0.82 | +0.0639 | --- |
| post_all = K6 Lo+Pre+AM+Cl, P6 As+Lo+AM+Cl, U6 As+Pre+AM, H6 As+Pre+AM, M6 Lo+Pre+PM, A6 As+AM | off | 41.2 (+0.1, 10.6) | 22.9 -> 56.2 | 241.2 -> 177.9 | 120.5 -> 104.5 | -1098.1 -> -1037.8 | -1.06 | +0.0147 | --- |
| post_all = K6 Lo+Pre+AM+Cl, P6 As+Lo+AM+Cl, U6 As+Pre+AM, H6 As+Pre+AM, M6 Lo+Pre+PM, A6 As+AM | 12R | 32.8 (+0.5, 18.7) | 26.6 -> 57.2 | 232.6 -> 168.3 | 119.6 -> 158.2 | -688.5 -> -727.2 | -0.64 | -0.0165 | --- |
| tol_pair = U6 As+Pre+AM, M6 As+Lo+AM+PM | off | 46.0 (+4.9, 7.0) | 22.9 -> 24.6 | 241.2 -> 173.8 | 120.5 -> 115.9 | -1098.1 -> -1042.6 | +0.07 | +0.0447 | STN |
| tol_pair = U6 As+Pre+AM, M6 As+Lo+AM+PM | 12R | 33.6 (+1.3, 8.4) | 26.6 -> 27.5 | 232.6 -> 121.6 | 119.6 -> 149.5 | -688.5 -> -717.8 | +0.01 | +0.0497 | STN |
| tol_pair_nopre = U6 As+AM, M6 As+Lo+AM+PM | off | 45.3 (+4.2, 6.8) | 22.9 -> 24.6 | 241.2 -> 173.7 | 120.5 -> 110.8 | -1098.1 -> -1043.4 | +0.05 | +0.0447 | STN |
| tol_pair_nopre = U6 As+AM, M6 As+Lo+AM+PM | 12R | 32.9 (+0.6, 8.3) | 26.6 -> 27.5 | 232.6 -> 121.4 | 119.6 -> 168.9 | -688.5 -> -722.1 | -0.02 | +0.0344 | STN |
| M6only | off | 43.8 (+2.7, 5.8) | 22.9 -> 24.9 | 241.2 -> 224.6 | 120.5 -> 133.2 | -1098.1 -> -1103.8 | -0.03 | +0.0157 | STN |
| M6only | 12R | 32.2 (-0.1, 7.4) | 26.6 -> 43.6 | 232.6 -> 231.4 | 119.6 -> 146.5 | -688.5 -> -697.7 | -0.47 | +0.0074 | --- |
| U6only | off | 42.6 (+1.5, 4.7) | 22.9 -> 22.6 | 241.2 -> 187.0 | 120.5 -> 100.3 | -1098.1 -> -1041.4 | +0.09 | +0.0241 | STN |
| U6only | 12R | 33.0 (+0.7, 4.3) | 26.6 -> 32.1 | 232.6 -> 133.0 | 119.6 -> 163.3 | -688.5 -> -722.6 | -0.19 | +0.0251 | -TN |
| tol_pair_M6AMPM = U6 As+Pre+AM, M6 AM+PM | off | 43.7 (+2.6, 6.3) | 22.9 -> 15.6 | 241.2 -> 206.0 | 120.5 -> 91.0 | -1098.1 -> -994.0 | +1.00 | +0.0174 | STN |
| tol_pair_M6AMPM = U6 As+Pre+AM, M6 AM+PM | 12R | 33.4 (+1.2, 6.0) | 26.6 -> 28.4 | 232.6 -> 157.1 | 119.6 -> 140.0 | -688.5 -> -710.8 | -0.03 | +0.0320 | STN |
| tol_pair_M6AMPM_nopre = U6 As+AM, M6 AM+PM | off | 43.1 (+1.9, 6.0) | 22.9 -> 15.6 | 241.2 -> 205.9 | 120.5 -> 85.9 | -1098.1 -> -993.5 | +0.96 | +0.0174 | STN |
| tol_pair_M6AMPM_nopre = U6 As+AM, M6 AM+PM | 12R | 32.8 (+0.5, 5.4) | 26.6 -> 27.7 | 232.6 -> 157.1 | 119.6 -> 175.0 | -688.5 -> -724.9 | -0.03 | +0.0238 | -TN |
| M6AMPMonly = M6 AM+PM | off | 41.6 (+0.4, 4.8) | 22.9 -> 15.4 | 241.2 -> 256.8 | 120.5 -> 105.9 | -1098.1 -> -1036.8 | +0.90 | -0.0027 | STN |
| M6AMPMonly = M6 AM+PM | 12R | 32.1 (-0.1, 4.4) | 26.6 -> 23.9 | 232.6 -> 241.6 | 119.6 -> 124.3 | -688.5 -> -708.4 | +0.13 | +0.0004 | --- |

The "all six" joint lines are what happens if every book takes its honest (or L6M-best) pick at once: honest_all -19.5 mean (MDE 14.2) and L6M maxDD 22.9 -> 52.5 (worse), post_all +0.1 mean but maxDD 22.9 -> 56.2: the interaction of the running-max locks and the lock engine makes the per-book gains non-additive and the joint swap strictly worse than live on L6M. The TOLERANT pair (U6 + NY-AM, M6 drop London / NY-PM or +Asia +NY-PM) is the only joint that holds (STN off and under 12R). Caveat: M6 and U6 are the two smallest-risk books that are positive in every window, so any added lot passes; the equal-risk column is the fair comparison, and it is +2.5 to +4.2 (inside MDE) not a drawdown cut.

## B. The 14:40-15:00 drift as a close book (1-min bars, real fills; 8 cells x 2 fills x 1/2/3 lots)

Cells (prereg): signal UNCOND (fade the sign of the 14:40 open -> 14:59 close move) or STACK (opposite of the net side x lots of the composite's taken signals fired 14:40:00-15:00:00, 60 days in 3 years); side BOTH or SHORT-ONLY; stop none or 40 pts; entry at the 15:00 bar open, flat at the 15:55 close; M = measured fills (market +0.25, stop cost 1.28, exit slip 0.25), LC = LIVE-CAL (+0.50, target needs +1 tick through, stop cost 2.45, slip 0.50); NQ $20/pt, fee $4.84 RT per contract. The STACK signals are the composite's (not the D7 base's).

### B1. Detail at 3 lots (hedge value = change in the stack when added; own mean per lot-week; correlation; placebos 200 draws random-timing and random-sign; leave-one-episode-out on the stack's 14 worst-20 episodes; stationary-bootstrap 95% CI)

| cell | fills | n trades | pts/trade | own mean $k/wk per lot: L6M (MDE) / PRE / X' / ALL | corr to stack ALL / PX / in worst-20 | 3 lots: dmaxDD L6M / PRE / X' / ALL $k | 3 lots: d worst-20 PRE / X' / ALL $k | 1 / 2 lots ALL w20 d | placebo rank (time; sign): dd ALL / w20 ALL / dd L6M | LOEO w20-gain per episode | boot 95% CI own mean $/wk; w20 excess over constant $k | S/T/N (3 lots) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| UNCOND|BOTH|stop0 | M | 1037 | -2.34 | +113 (1166) / +200 / -137 / +68 | +0.15 / +0.16 / +0.25 | +2.8 / +27.4 / +3.5 / +27.4 | -26.9 / -33.4 / -15.1 | +6.8 / +0.2 | 0.23/0.73/0.63; 0.07/0.60/0.73 | min -27.3 / med -16.2 / max -10.9 (0/14>0) | [-385, +602]; [-69.2, +26.2] | --N |
| UNCOND|BOTH|stop0 | LC | 1037 | -2.84 | +68 (1166) / +153 / -184 / +20 | +0.15 / +0.16 / +0.25 | +2.9 / +28.4 / +4.6 / +28.4 | -29.7 / -36.2 / -18.0 | +5.8 / -1.8 | 0.20/0.74/0.65; 0.08/0.60/0.70 | min -30.3 / med -19.1 / max -13.8 (0/14>0) | [-432, +555]; [-69.3, +26.2] | --N |
| UNCOND|BOTH|stop40 | M | 1037 | -1.42 | +657 (1037) / -151 / -60 / -2 | +0.09 / +0.07 / +0.17 | +1.0 / +15.5 / -3.2 / +15.5 | -5.9 / -26.8 / -0.8 | +3.1 / +2.1 | 0.37/0.86/0.72; 0.17/0.68/0.61 | min -9.0 / med -2.5 / max +6.0 (5/14>0) | [-334, +355]; [-36.9, +30.6] | --N |
| UNCOND|BOTH|stop40 | LC | 1037 | -2.36 | +484 (1048) / -222 / -121 / -90 | +0.08 / +0.07 / +0.17 | +1.2 / +17.1 / -1.9 / +17.1 | -10.2 / -30.8 / -5.0 | +1.7 / -0.7 | 0.32/0.90/0.74; 0.17/0.71/0.61 | min -13.3 / med -6.6 / max +1.9 (1/14>0) | [-423, +250]; [-36.0, +31.1] | --N |
| UNCOND|SHORT|stop0 | M | 559 | -0.53 | +185 (989) / +97 / +213 / +149 | +0.11 / +0.14 / +0.38 | +3.3 / +19.4 / -1.2 / +19.4 | -8.3 / +9.0 / +10.8 | +5.0 / +9.4 | 0.15/0.89/0.46; 0.02/0.94/0.63 | min +0.0 / med +8.2 / max +13.3 (14/14>0) | [-110, +450]; [-31.0, +31.0] | S-N |
| UNCOND|SHORT|stop0 | LC | 559 | -1.03 | +159 (990) / +73 / +185 / +124 | +0.11 / +0.14 / +0.38 | +3.3 / +19.9 / -0.5 / +19.9 | -9.8 / +7.4 / +9.3 | +4.5 / +8.4 | 0.17/0.86/0.48; 0.03/0.96/0.58 | min -1.5 / med +6.7 / max +11.7 (13/14>0) | [-138, +425]; [-31.0, +31.0] | S-N |
| UNCOND|SHORT|stop40 | M | 559 | -0.10 | +460 (899) / -65 / +158 / +103 | +0.11 / +0.13 / +0.31 | +1.5 / +18.2 / -2.2 / +18.2 | -12.2 / +1.2 / -1.3 | +1.1 / +1.6 | 0.15/0.81/0.61; 0.01/0.86/0.43 | min -11.0 / med -3.3 / max +3.2 (3/14>0) | [-118, +344]; [-36.7, +18.3] | --N |
| UNCOND|SHORT|stop40 | LC | 559 | -0.84 | +416 (897) / -99 / +123 / +67 | +0.10 / +0.13 / +0.31 | +1.6 / +18.9 / -1.3 / +18.9 | -14.4 / -0.9 / -3.4 | +0.4 / +0.3 | 0.15/0.79/0.60; 0.02/0.88/0.41 | min -13.1 / med -5.5 / max +1.0 (1/14>0) | [-153, +306]; [-36.4, +18.3] | --N |
| STACK|BOTH|stop0 | M | 60 | +6.05 | -9 (421) / +63 / +34 / +47 | +0.01 / -0.02 / +0.18 | +0.0 / +0.0 / -0.4 / +0.0 | +3.0 / -5.3 / +9.1 | +3.6 / +7.2 | 0.52/0.93/0.23; 0.00/0.89/0.00 | min -0.0 / med +8.4 / max +10.1 (13/14>0) | [-47, +141]; [-6.6, +21.8] | --- |
| STACK|BOTH|stop0 | LC | 60 | +5.55 | -12 (421) / +60 / +29 / +43 | +0.01 / -0.02 / +0.18 | +0.0 / +0.0 / -0.3 / +0.0 | +2.8 / -5.6 / +8.8 | +3.5 / +7.0 | 0.51/0.92/0.24; 0.00/0.88/0.00 | min -0.3 / med +8.1 / max +9.8 (13/14>0) | [-51, +137]; [-6.5, +21.7] | --- |
| STACK|BOTH|stop40 | M | 60 | -1.47 | +22 (298) / -54 / +46 / -14 | -0.00 / +0.02 / +0.22 | +0.0 / +0.0 / -0.4 / +0.0 | +0.2 / -6.0 / +6.3 | +2.6 / +5.3 | 0.56/0.89/0.31; 0.00/0.81/0.00 | min -2.8 / med +5.6 / max +10.2 (13/14>0) | [-96, +68]; [-6.8, +23.0] | --N |
| STACK|BOTH|stop40 | LC | 60 | -2.23 | +16 (300) / -59 / +39 / -20 | -0.01 / +0.01 / +0.22 | +0.0 / +0.0 / -0.3 / +0.0 | -0.1 / -6.6 / +6.0 | +2.5 / +5.1 | 0.57/0.90/0.31; 0.00/0.81/0.00 | min -3.1 / med +5.2 / max +9.8 (13/14>0) | [-103, +62]; [-6.7, +23.0] | --N |
| STACK|SHORT|stop0 | M | 29 | +22.59 | +8 (46) / +88 / +136 / +87 | +0.05 / +0.07 / +0.15 | +0.0 / +0.0 / -0.4 / +0.0 | +0.3 / +6.5 / +8.1 | +2.7 / +5.4 | 0.36/0.96/0.14; 0.00/0.84/0.00 | min -0.5 / med +8.1 / max +9.2 (13/14>0) | [+22, +164]; [-8.6, +18.5] | --- |
| STACK|SHORT|stop0 | LC | 29 | +22.09 | +7 (45) / +86 / +133 / +85 | +0.05 / +0.07 / +0.15 | +0.0 / +0.0 / -0.3 / +0.0 | +0.2 / +6.3 / +7.9 | +2.6 / +5.3 | 0.39/0.94/0.17; 0.00/0.80/0.00 | min -0.7 / med +7.9 / max +9.0 (13/14>0) | [+20, +162]; [-8.6, +18.4] | --- |
| STACK|SHORT|stop40 | M | 29 | +10.50 | -15 (94) / +14 / +117 / +40 | +0.04 / +0.05 / +0.15 | +0.0 / +0.0 / -0.4 / +0.0 | +0.3 / +4.0 / +8.1 | +2.7 / +5.4 | 0.39/0.95/0.17; 0.00/0.84/0.00 | min -0.5 / med +8.1 / max +9.2 (13/14>0) | [-30, +115]; [-5.5, +20.9] | --- |
| STACK|SHORT|stop40 | LC | 29 | +9.84 | -16 (96) / +12 / +113 / +37 | +0.04 / +0.05 / +0.15 | +0.0 / +0.0 / -0.3 / +0.0 | +0.2 / +3.7 / +7.9 | +2.6 / +5.3 | 0.40/0.95/0.20; 0.00/0.80/0.00 | min -0.7 / med +7.9 / max +9.0 (13/14>0) | [-33, +113]; [-5.5, +20.9] | --- |

### B2. 1 / 2 / 3 lots (M fills; LC fills differ by less than 5% of every number in B1)

| cell (M fills) | lots | L6M stack mean d (MDE) | maxDD L6M / PRE / X' / ALL d $k | worst-20 PRE / X' / ALL d $k | dSD ALL | dCalmar ALL | S/T/N |
|---|---|---|---|---|---|---|---|
| STACK|SHORT|stop0 | 1 | +0.0 (0.0) | +0.0 / +0.0 / -0.1 / +0.0 | +0.1 / +2.2 / +2.7 | +0.0 | +0.0004 | --- |
| STACK|SHORT|stop0 | 2 | +0.0 (0.1) | +0.0 / +0.0 / -0.3 / +0.0 | +0.2 / +4.3 / +5.4 | +0.1 | +0.0007 | --- |
| STACK|SHORT|stop0 | 3 | +0.0 (0.1) | +0.0 / +0.0 / -0.4 / +0.0 | +0.3 / +6.5 / +8.1 | +0.1 | +0.0011 | --- |
| STACK|BOTH|stop0 | 1 | -0.0 (0.4) | +0.0 / +0.0 / -0.1 / +0.0 | +1.0 / -1.8 / +3.6 | +0.0 | +0.0002 | --- |
| STACK|BOTH|stop0 | 2 | -0.0 (0.8) | +0.0 / +0.0 / -0.3 / +0.0 | +2.0 / -3.5 / +7.2 | +0.0 | +0.0004 | --- |
| STACK|BOTH|stop0 | 3 | -0.0 (1.3) | +0.0 / +0.0 / -0.4 / +0.0 | +3.0 / -5.3 / +9.1 | +0.1 | +0.0006 | --- |
| UNCOND|SHORT|stop0 | 1 | +0.2 (1.0) | +1.1 / +6.5 / -0.4 / +6.5 | -1.8 / +5.3 / +5.0 | +0.2 | -0.0018 | S-N |
| UNCOND|SHORT|stop0 | 2 | +0.4 (2.0) | +2.2 / +12.9 / -0.8 / +12.9 | -3.6 / +8.0 / +9.4 | +0.5 | -0.0035 | S-N |
| UNCOND|SHORT|stop0 | 3 | +0.6 (3.0) | +3.3 / +19.4 / -1.2 / +19.4 | -8.3 / +9.0 / +10.8 | +0.8 | -0.0052 | S-N |

Reading. (1) The unconditional fade has no edge: -2.34 pts per trade net (-1.42 with the 40-pt stop), own mean about 0 per lot-week (MDE 0.4-1.2k), and added at 3 lots it makes the stack's ALL maxDD worse by +27k (both sides, no stop; PRE) and its worst-20 worse (-15k); the short-only half is neutral in mean (-0.53 pts per trade, own L6M +185/wk) and is S-N across windows at 3 lots (+0.6k L6M), but ALL maxDD +19.4k worse and a hedge claim fails (random-sign rank on ALL worst-20 0.94, on ALL maxDD 0.02). (2) The stack-fade is a different animal: the stack's own 14:40-15:00 signals are followed by an adverse move (+6.05 pts per trade faded, +22.6 for the 29 short-side), 1/2/3 lots add +2.7 / +5.4 / +8.1k to the ALL worst-20 with maxDD unchanged and L6M +0.0k: the hedge value is real in sign and small in size (0.7% of the 1,098k tail), the own mean CI for the short-side cell is [+22, +164] $/lot-week (excludes 0) but its worst-20 excess over a constant weekly add is [-8.6, +18.5]k (includes 0); weekly correlation to the stack +0.05 (+0.15 inside the stack's worst-20 weeks: no negative correlation); leave-one-episode-out: 13 of 14 episodes keep the gain, deleting the one that carries it leaves -0.5k, i.e. one episode; random-timing placebo ranks 0.96 on ALL worst-20 (bar 0.95) but 0.36 on ALL maxDD, random-sign 0.84 / 0.00. (3) STRICT / TOLERANT / NOW-ONLY on the stack mean at 3 lots: all STACK cells are mean-neutral (+0.0 L6M), none S/T; UNCOND short-only stop-none is S-N (no TOLERANT: PRE worst-20 deeper). (4) Honest ranking (PX): STACK both-sides no stop first, L6M dCalmar -0.001 - no recent edge. The 95th percentile of the placebo ALL worst-20 gain is 7.4-27.2k (random-timing) and 5.0-27.6k (random-sign) across the 8 cells; the STACK short-side cell's real +8.1k is just above its random-timing 7.9k and below its random-sign 9.5k, UNCOND short-only +10.8k is below both (27.2k, 10.9k): with 8 cells examined, one exceedance of a 95% bar is expected by chance. Net: a +8k tail improvement from one episode; no book is recommended. If D7 wants a shadow log: the STACK short-side rule (fade the book's own late signals) needs only the 14:40-15:00 signal flag and a 15:00 market order flat at 15:55.

## C. K7 NY-PM block 14:40-15:00 on top of the composite (engine, signal-second mask; open trades continue; a blocked signal is a skipped trade)

| window (scope: all = K6 = A6+K6 at live lots, identical) | signals blocked (all rows incl. non-live) | L6M mean d (MDE) | L6M maxDD d | PRE / X' maxDD d | worst-20 ALL d | HOLD / PRE / X' mean d | LOEO dW20 min / med / max $k | boot CI mean d $/wk; maxDD cut ALL $k | S/T/N | TOL-B/TOL-nc |
|---|---|---|---|---|---|---|---|---|---|---|
| 1440-1500 | 1246 | +0.0 (0.8) | +0.0 | +0.0 / -1.1 | +0.8 | -0.0 / -0.2 / +0.2 | -2.0 / -0.1 / +1.2 | [-246, +121]; [-2.9, +4.1] | --N | 0/0 |
| 1430-1500 | 1919 | -0.3 (0.7) | +0.0 | -3.9 / -5.7 | +2.1 | -0.2 / -0.1 / +0.3 | -0.2 / +1.4 / +3.0 | [-271, +228]; [-4.9, +9.7] | --- | 0/0 |
| 1440-1450 | 579 | -0.1 (0.6) | +0.0 | +0.0 / -0.8 | -0.6 | -0.1 / -0.1 / +0.3 | -1.4 / -0.6 / +0.8 | [-143, +209]; [-1.4, +3.8] | --- | 0/0 |
| 1450-1500 | 667 | +0.1 (0.6) | +0.0 | +0.0 / -0.2 | +1.4 | +0.1 / -0.1 / -0.1 | -1.4 / +0.4 / +1.7 | [-224, +49]; [-3.8, +2.0] | --N | 1/0 |
| 1430-1450 | 1252 | -0.4 (0.5) | +0.0 | -3.9 / -5.5 | +0.9 | -0.2 / +0.0 / +0.4 | -1.8 / +1.2 / +2.6 | [-185, +323]; [-3.9, +10.2] | --- | 0/0 |

200 random 20-min windows starting 12:00-14:40 ET (scope all books): the named 14:40-15:00 block's dCalmar L6M beats 0.51 of the draws, ALL maxDD 0.24, ALL worst-20 0.62, L6M mean 0.53 (K6 scope: 0.42 / 0.25 / 0.65 / 0.46); placebo medians (dMaxDD L6M, dW20 ALL, dMaxDD ALL, dCal L6M, dMean L6M): [0.0, -739.0, -1951.0, -0.0, -29.0]

Reading: at live lots the block can only touch K6 (2 lots NY-PM; P6 / U6 / H6 / M6 do not trade NY-PM, A6 is Asia only), 115 K6 signals in 3 years (about 0.7 per week); L6M +0.003k (MDE 0.8), PRE -0.25k, X' +0.22k, HOLD -0.0, ALL maxDD change 0 and worst-20 +0.8k (0.07% of the tail), NOW-ONLY (L3M and L6M positive by +0.0), leave-one-episode-out -2.0 to +1.2k, bootstrap CI of the mean change [-246, +121] $/wk. Against 200 random 20-minute NY-PM windows the named window is at the median (Calmar 0.51, worst-20 0.62, ALL maxDD 0.24). Edges (14:30, 14:50) move L6M by -0.4 to +0.1k, all inside MDE; 14:30-15:00 improves the PRE / X' maxDD by 3.9 / 5.7k (and costs -0.3k L6M; no placebo was run for the edge windows). The earlier register line (NYPM_END_SKIP, K6 -240/wk L6M at live lots with its own convention) agrees with "about zero, a hair negative". The K6 signals fired in the window earned +8.3 pts per signal in L6M (NYPM_END_SKIP table), so blocking removes winners; the books whose 14:40-15:00 signals are the losers (P6 -16.7, U6 -10.4, H6 -8.6 pts per signal) do not trade NY-PM at live lots. If D7 hosts X1-X5 (alt-bar cells with NY-PM entries) or other NY-PM books the block must be re-scored on them: that is the D7 re-run.

## D. On the BASE-1 engine (d7lib; BASE-1 had not delivered out/d7base/ results at 15:30Z; two passes on its engine, both labelled)

d7lib.py was edited at 15:12:16Z and then raised `NameError: _l2sl_shifted` for any run with the TH-L2 loss cut on, so: D1 = BASE-noTH (d7lib.BASE with th_loss and th_profit off, a variant BASE-1's own README offers; L6M 48.9k, maxDD 29.9k, PRE maxDD 244.5k, ALL worst-20 -1,262k) run today; D2 = the literal draft with TH-L2 on, run with the 15:11Z version before the break (L6M 18.2k, maxDD 84.8k: TH-L2 loss cut alone takes the composite to 20.8k / 76.7k and the profit path rule to 28.9k / 34.4k, X1-X5 add +3.6k, Native +1.3k, OTE-62 B73 +1.7k, sig_pe +2.2k; the D2 numbers are not the ones to pick from until BASE-1 settles the TH-L2 mapping). **Reading across the three bases (interim composite, D1, D2): (i)** the walk-forward verdict is the same: session re-selection loses to the live table in 10 of 12 book-by-window runs on D1 as on the interim base, the two exceptions again U6 and M6 with the expanding window (D1 forward 31.0 and 31.4 vs live 30.7, inside MDE); pooled over all six books the expanding re-selection is 27.7 vs 30.7 (roll6 16.8 vs 30.7). **(ii)** What survives the literal TOLERANT gate is again U6 and M6 additions, plus one H6 NY-PM add on D1: D1 has 10 TOLERANT cells of 342 (U6 6 (+NY-AM variants): L6M +0.0 to +1.7 (MDE 3.0-5.0), PRE +0.1 to +0.8, X' +0.9 to +1.3; H6 1: +NY-PM, L6M +1.5 (2.3), PRE +0.0, X' -0.3; M6 3: NY-AM+NY-PM L6M +0.1 (4.7), PRE +0.4, X' +0.1, maxDD 29.9 -> 26.8; London+NY-AM+NY-PM +0.6 (2.5)); D2 has 52 (M6 39, U6 11, P6 2). K6, P6 and A6 have no TOLERANT alternative on D1. **(iii)** The L6M-best picks again cut the L6M maxDD at no mean cost and fail PRE: D1 K6 drop NY-AM (As+Lo+PM+Cl) maxDD 29.9 -> 19.3, Calmar 1.64 -> 2.52, mean -0.2 (3.1), PRE -1.8; D1 U6 +NY-AM+NY-PM (As+Lo+AM+PM) Calmar 2.61, maxDD 19.3, mean +1.3 (4.6), --N only. The best-of-64 null is beaten for K6, U6, H6, M6 on D1 (pct 1.00) and not for P6 (0.66) or A6 (0.91). **(iv)** K7 NY-PM block on D1 (scope all books = K6 = A6+K6): 14:40-15:00 L6M -0.2k (MDE 0.4), L6M maxDD -0.2k, PRE maxDD +0.0 / X' +0.2, ALL worst-20 -0.8k (slightly worse), NOT even NOW-ONLY; placebo ranks 0.43 (Calmar) / 0.51 (worst-20) of 200 random 20-minute windows: a no-op or a hair negative on D7 as on the composite. **(v)** Close book on the D1 stack (table below): the stack-fade short side adds +2.5k to the ALL worst-20 (interim +8.1k) at 3 lots with maxDD unchanged and L6M +0.0k - weaker on D7 than on the composite; the unconditional short-only fade is STN on the mean at 3 lots but worsens the ALL maxDD by +19.4k (dCalmar L6M -0.147).

#### D1. BASE-noTH (d7lib.BASE with th_loss and th_profit off; BASE-1 README offers this variant) - the pass to read

**Engine** `d7lib` (BASE-noTH: d7lib.BASE with th_loss and th_profit off): d7lib.BASE (six core books at live lots plus X1-X5 at 2 lots, total series incl. X; signal-state rules A, Native stops, OTE-62 B73 D 30, lock off) with the overrides named in the label. BASE LINE: L6M mean 48.9k, maxDD 29.9k, PRE maxDD 244.5k, ALL worst-20 -1261.9k. (The interim composite was 41.1 / 22.9 / 241.2 / -1,098.) Same 384 cells, same prereg.

| book | live set | pick | set | L6M mean d (MDE) | L6M maxDD | L6M Calmar (live 1.64) | PX Calmar (live 0.069) | ALL worst-20 | HOLD / PRE / X' mean d | S/T/N | TOL-B/TOL-nc |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K6 | As+Lo+AM+PM | honest | As+AM | -3.8 (2.9) | 33.3 | 1.36 | 0.078 | -1209.2 | -3.4 / -0.2 / +0.0 | --- | 0/0 |
| K6 | As+Lo+AM+PM | post | As+Lo+PM+Cl | -0.2 (3.1) | 19.3 | 2.52 | 0.059 | -1290.1 | -0.3 / -1.8 / -0.1 | --- | 0/0 |
| P6 | As+Lo+AM | honest | As+AM+Cl | -3.7 (13.2) | 48.3 | 0.94 | 0.090 | -1078.9 | -4.1 / +1.3 / +0.9 | --- | 0/0 |
| P6 | As+Lo+AM | post | As+PM | -7.8 (17.9) | 23.3 | 1.77 | 0.064 | -1081.8 | -9.4 / -4.3 / -2.1 | --- | 0/0 |
| U6 | As+Lo | honest | As+AM+Cl | +0.7 (5.0) | 32.8 | 1.51 | 0.090 | -1148.1 | +1.5 / +0.1 / +1.2 | STN | 1/1 |
| U6 | As+Lo | post | As+Lo+AM+PM | +1.3 (4.6) | 19.3 | 2.61 | 0.070 | -1243.9 | +2.4 / +0.4 / -0.5 | --N | 1/1 |
| H6 | As+AM | honest | Lo+PM | -5.0 (7.7) | 34.0 | 1.29 | 0.104 | -1166.3 | -3.9 / +0.9 / +0.9 | --- | 0/0 |
| H6 | As+AM | post | As+Lo+AM | -0.5 (2.6) | 25.4 | 1.91 | 0.076 | -1300.4 | -0.6 / +0.4 / +0.3 | --- | 0/0 |
| M6 | Lo+AM | honest | As+Lo+AM+PM | +3.2 (6.0) | 32.9 | 1.58 | 0.085 | -1312.5 | +2.5 / +2.0 / +1.1 | S-N | 1/1 |
| M6 | Lo+AM | post | Lo+Pre+AM+Cl | +0.2 (1.8) | 26.1 | 1.88 | 0.069 | -1281.4 | -0.2 / +0.1 / -0.3 | --N | 1/1 |
| A6 | As | honest | As+PM | -0.1 (1.8) | 29.0 | 1.68 | 0.072 | -1275.6 | -0.3 / +0.3 / -0.1 | --- | 0/0 |
| A6 | As | post | As+PM | -0.1 (1.8) | 29.0 | 1.68 | 0.072 | -1275.6 | -0.3 / +0.3 / -0.1 | --- | 0/0 |

Distinct non-live cells 342: STRICT 25 / TOLERANT 10 / NOW-ONLY 83 / TOL-B 66 / TOL-nc 35; TOLERANT by book: K6 0, P6 0, U6 6, H6 1, M6 3, A6 0.

Best-of-64 null (L6M best dCalmar vs the in-window null over PX): K6 +0.883 (null p50 +0.018, p95 +0.049, pct 1.00); P6 +0.129 (null p50 +0.096, p95 +0.292, pct 0.66); U6 +0.972 (null p50 +0.034, p95 +0.046, pct 1.00); H6 +0.269 (null p50 +0.044, p95 +0.061, pct 1.00); M6 +0.239 (null p50 +0.025, p95 +0.059, pct 1.00); A6 +0.044 (null p50 +0.010, p95 +0.048, pct 0.91).

Walk-forward (forward 3-month mean, chained, live -> selected, $k/wk (MDE); hit rate): K6 roll6: 30.7 -> 29.4 (2.0), hit 0.14; K6 expand: 30.7 -> 29.0 (2.4), hit 0.25; P6 roll6: 30.7 -> 22.3 (9.0), hit 0.12; P6 expand: 30.7 -> 30.3 (7.3), hit 0.38; U6 roll6: 30.7 -> 30.2 (2.8), hit 0.38; U6 expand: 30.7 -> 31.0 (3.1), hit 0.50; H6 roll6: 30.7 -> 29.2 (3.5), hit 0.50; H6 expand: 30.7 -> 29.4 (3.4), hit 0.50; M6 roll6: 30.7 -> 29.8 (3.1), hit 0.25; M6 expand: 30.7 -> 31.4 (3.2), hit 0.62; A6 roll6: 30.7 -> 29.7 (1.6), hit 0.25; A6 expand: 30.7 -> 30.3 (1.4), hit 0.38; pooled: roll6 30.7 -> 16.8; expand 30.7 -> 27.7.

K7 NY-PM block on the D7 engine (extra_skip on the signal second; scope all books - the K6 and A6+K6 scopes are identical row for row):

| window | scope | blocked rows | L6M mean d (MDE) | L6M maxDD d | PRE / X' maxDD d | worst-20 ALL d | HOLD / PRE / X' mean d | dCalmar L6M / PX | S/T/N |
|---|---|---|---|---|---|---|---|---|---|
| 1440-1500 | ALL | 1246 | -0.2 (0.4) | -0.2 | +0.0 / +0.2 | -0.8 | -0.3 / -0.2 / +0.2 | +0.005 / -0.0002 | --- |
| 1430-1500 | ALL | 1919 | -0.3 (0.6) | -0.2 | -3.8 / -4.4 | -1.9 | -0.3 / +0.0 / +0.3 | +0.001 / +0.0015 | --- |
| 1440-1450 | ALL | 579 | -0.2 (0.4) | +0.0 | +0.0 / +1.7 | -0.1 | -0.1 / -0.1 / +0.2 | -0.005 / +0.0001 | --- |
| 1450-1500 | ALL | 667 | -0.1 (0.1) | -0.2 | +0.0 / -1.5 | -0.7 | -0.1 / -0.1 / -0.1 | +0.010 / -0.0004 | --- |
| 1430-1450 | ALL | 1252 | -0.3 (0.5) | +0.0 | -3.8 / -2.9 | -1.2 | -0.1 / +0.1 / +0.3 | -0.009 / +0.0019 | --- |

Random 20-min window placebo (200, all books): named block beats Calmar 0.43, ALL maxDD 0.24, ALL worst-20 0.51, L6M mean 0.30.

Close book on the D7 stack (3 lots, measured fills; STACK signals are the composite's):

| cell | pts/trade | own mean $/lot-wk L6M (MDE) / PRE / X' | 3 lots: d maxDD L6M / PRE / X' / ALL $k | d worst-20 PRE / X' / ALL $k | dCalmar L6M / PX | S/T/N |
|---|---|---|---|---|---|---|
| UNCOND|BOTH|stop0 | -2.34 | +113 (1166) / +200 / -137 | +5.8 / +27.4 / -4.8 / +27.4 | -6.5 / -35.0 / +1.6 | -0.257 / -0.0061 | --N |
| UNCOND|BOTH|stop40 | -1.42 | +657 (1037) / -151 / -60 | +3.5 / +15.5 / -13.0 / +15.5 | -29.6 / -21.6 / -24.2 | -0.114 / -0.0055 | --N |
| UNCOND|SHORT|stop0 | -0.53 | +185 (989) / +97 / +213 | +3.3 / +19.4 / -7.9 / +19.4 | +0.4 / +7.0 / +5.4 | -0.147 / -0.0035 | STN |
| UNCOND|SHORT|stop40 | -0.10 | +460 (899) / -65 / +158 | +2.3 / +18.2 / -8.9 / +18.2 | -19.8 / +8.6 / -3.0 | -0.073 / -0.0046 | --N |
| STACK|BOTH|stop0 | +6.05 | -9 (421) / +63 / +34 | +0.3 / +0.0 / -4.1 / +0.0 | +7.4 / +10.0 / +3.4 | -0.017 / +0.0006 | --- |
| STACK|BOTH|stop40 | -1.47 | +22 (298) / -54 / +46 | +0.3 / +0.0 / -4.1 / +0.0 | -14.9 / +5.9 / +0.5 | -0.014 / -0.0002 | --N |
| STACK|SHORT|stop0 | +22.59 | +8 (46) / +88 / +136 | +0.0 / +0.0 / -1.8 / +0.0 | +7.5 / +13.7 / +2.5 | +0.001 / +0.0013 | --- |
| STACK|SHORT|stop40 | +10.50 | -15 (94) / +14 / +117 | +0.0 / +0.0 / -1.8 / +0.0 | -7.5 / +11.2 / +2.4 | -0.002 / +0.0006 | --- |

#### D2. d7lib.BASE literal draft (TH-L2 on) - 15:11Z version

**Engine** `d7lib` (d7lib.BASE literal draft, TH-L2 on, 15:11Z version): d7lib.BASE (six core books at live lots plus X1-X5 at 2 lots, total series incl. X; signal-state rules A, Native stops, OTE-62 B73 D 30, lock off) with the overrides named in the label. BASE LINE: L6M mean 18.2k, maxDD 84.8k, PRE maxDD 190.7k, ALL worst-20 -957.5k. (The interim composite was 41.1 / 22.9 / 241.2 / -1,098.) Same 384 cells, same prereg.

| book | live set | pick | set | L6M mean d (MDE) | L6M maxDD | L6M Calmar (live 0.21) | PX Calmar (live 0.057) | ALL worst-20 | HOLD / PRE / X' mean d | S/T/N | TOL-B/TOL-nc |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K6 | As+Lo+AM+PM | honest | As+AM | -1.6 (2.1) | 80.6 | 0.21 | 0.063 | -921.6 | -1.4 / -0.1 / +0.5 | --- | 0/0 |
| K6 | As+Lo+AM+PM | post | As+Lo+AM+Cl | -0.1 (1.3) | 78.8 | 0.23 | 0.059 | -940.1 | -0.0 / -0.3 / +0.1 | --- | 0/0 |
| P6 | As+Lo+AM | honest | As+AM+PM | -0.3 (10.2) | 56.9 | 0.31 | 0.126 | -764.9 | -1.0 / +3.0 / +3.3 | --- | 0/0 |
| P6 | As+Lo+AM | post | AM+PM | -3.3 (18.9) | 24.8 | 0.60 | 0.090 | -702.7 | -3.2 / -1.5 / +2.4 | --- | 0/0 |
| U6 | As+Lo | honest | As+AM+PM+Cl | -0.2 (5.4) | 91.3 | 0.20 | 0.072 | -925.6 | +1.1 / +0.7 / +0.6 | --- | 0/0 |
| U6 | As+Lo | post | As+Lo+Pre+AM | +0.9 (3.6) | 84.8 | 0.23 | 0.061 | -962.9 | +1.6 / +0.4 / +1.1 | S-N | 1/1 |
| H6 | As+AM | honest | Lo+PM | -3.5 (4.8) | 102.3 | 0.14 | 0.070 | -963.2 | -2.9 / +1.2 / -0.5 | --- | 0/0 |
| H6 | As+AM | post | As+AM+PM | +0.8 (1.6) | 87.2 | 0.22 | 0.057 | -967.4 | +0.7 / +0.1 / -0.0 | --- | 0/0 |
| M6 | Lo+AM | honest | As+Pre+AM+Cl | +3.1 (5.2) | 48.9 | 0.44 | 0.068 | -899.9 | +2.1 / +2.4 / -0.1 | -TN | 1/1 |
| M6 | Lo+AM | post | As+Pre | +4.5 (5.9) | 48.5 | 0.47 | 0.063 | -853.8 | +3.2 / +1.3 / -0.8 | -TN | 1/1 |
| A6 | As | honest | As+Lo+PM | -0.8 (2.1) | 84.8 | 0.21 | 0.061 | -953.5 | -1.0 / +0.4 / +0.2 | --- | 0/0 |
| A6 | As | post | PM | -2.3 (3.6) | 69.4 | 0.23 | 0.048 | -936.6 | -2.0 / -2.0 / -1.1 | --- | 0/0 |

Distinct non-live cells 347: STRICT 33 / TOLERANT 52 / NOW-ONLY 84 / TOL-B 80 / TOL-nc 68; TOLERANT by book: K6 0, P6 2, U6 11, H6 0, M6 39, A6 0.

Best-of-64 null (L6M best dCalmar vs the in-window null over PX): K6 +0.014 (null p50 +0.010, p95 +0.025, pct 0.78); P6 +0.387 (null p50 +0.189, p95 +0.430, pct 0.90); U6 +0.011 (null p50 +0.023, p95 +0.074, pct 0.20); H6 +0.003 (null p50 +0.016, p95 +0.040, pct 0.01); M6 +0.253 (null p50 +0.017, p95 +0.061, pct 1.00); A6 +0.014 (null p50 +0.009, p95 +0.021, pct 0.73).

Walk-forward (forward 3-month mean, chained, live -> selected, $k/wk (MDE); hit rate): K6 roll6: 16.6 -> 15.3 (1.3), hit 0.25; K6 expand: 16.6 -> 15.8 (1.5), hit 0.38; P6 roll6: 16.6 -> 13.9 (7.7), hit 0.38; P6 expand: 16.6 -> 16.3 (6.6), hit 0.50; U6 roll6: 16.6 -> 16.4 (2.2), hit 0.50; U6 expand: 16.6 -> 17.3 (2.5), hit 0.50; H6 roll6: 16.6 -> 15.9 (2.5), hit 0.50; H6 expand: 16.6 -> 15.9 (2.1), hit 0.50; M6 roll6: 16.6 -> 17.3 (2.1), hit 0.88; M6 expand: 16.6 -> 18.6 (2.2), hit 0.88; A6 roll6: 16.6 -> 15.9 (1.4), hit 0.29; A6 expand: 16.6 -> 16.1 (1.4), hit 0.12; pooled: roll6 16.6 -> 11.9; expand 16.6 -> 17.2.

(NY-PM block on the D7 engine not available: [Errno 2] No such file or directory: 'l2vast/ds3/out/better/s7/blkD7draft_scored.pkl')

Close book on the D7 stack (3 lots, measured fills; STACK signals are the composite's):

| cell | pts/trade | own mean $/lot-wk L6M (MDE) / PRE / X' | 3 lots: d maxDD L6M / PRE / X' / ALL $k | d worst-20 PRE / X' / ALL $k | dCalmar L6M / PX | S/T/N |
|---|---|---|---|---|---|---|
| UNCOND|BOTH|stop0 | -2.34 | +113 (1166) / +200 / -137 | -2.0 / +22.7 / -3.2 / +22.7 | +2.7 / -20.0 / +11.3 | +0.009 / -0.0050 | -TN |
| UNCOND|BOTH|stop40 | -1.42 | +657 (1037) / -151 / -60 | -9.0 / +16.0 / -5.1 / +16.0 | -8.4 / -5.5 / +4.7 | +0.052 / -0.0061 | --N |
| UNCOND|SHORT|stop0 | -0.53 | +185 (989) / +97 / +213 | +0.4 / +12.0 / -6.7 / +12.0 | -0.4 / +8.6 / -1.7 | +0.005 / -0.0013 | S-N |
| UNCOND|SHORT|stop40 | -0.10 | +460 (899) / -65 / +158 | -3.6 / +13.3 / -9.8 / +13.3 | -12.9 / +9.7 / -1.3 | +0.027 / -0.0035 | --N |
| STACK|BOTH|stop0 | +6.05 | -9 (421) / +63 / +34 | +0.0 / +0.0 / -4.4 / +0.0 | +3.8 / +10.6 / +1.5 | -0.000 / +0.0008 | --- |
| STACK|BOTH|stop40 | -1.47 | +22 (298) / -54 / +46 | +0.0 / +0.0 / -4.4 / +0.0 | -4.3 / +8.4 / -3.5 | +0.001 / -0.0003 | --N |
| STACK|SHORT|stop0 | +22.59 | +8 (46) / +88 / +136 | +0.0 / +0.0 / -7.2 / +0.0 | +1.1 / +13.8 / +0.6 | +0.000 / +0.0017 | --- |
| STACK|SHORT|stop40 | +10.50 | -15 (94) / +14 / +117 | +0.0 / +0.0 / -7.2 / +0.0 | -4.1 / +13.3 / +0.1 | -0.001 / +0.0008 | --- |

## E. Caveats

(1) L6M is 28 weeks and its maxDD is two weeks (2025-10-20, 2026-01-19), so any L6M maxDD cut that touches those weeks (M6 NY-AM, K6 London/NY-AM) is a two-week result. (2) PX Calmar is dominated by one 241k PRE episode (75 weeks), so the honest ranking is a ranking by "avoid that episode". (3) The U6 / M6 TOLERANT cells add lots; equal-risk is the fair column; M6's NY-PM and Asia sessions are positive in every window but tiny (MDE 5-6k). (4) Equal-risk is linear on the daily series for the sweep (`~`; A1 columns), engine-rerun (lot table x c matching ALL worst-20, interpolated between three c values) for the finalists (page 1, no `~`); integer half-up lots make the engine version coarse for 2-lot books: M6 London+Pre+NY-PM is -2.2 by engine and +3.1 linear, M6 AM+PM +2.9 linear, U6 As+Pre+AM +2.5 engine / +4.6 linear - read the equal-risk mean as a range, the dCalmar column does not depend on it. (5) The block uses the engine's zone-skip semantics: a blocked signal does not feed the running-max SizeMult of its book (the D6 rule would count it); K6 is the only book affected, so the difference is bounded by K6's 115 signals. (6) The close-book STACK signals are the composite's, entry time proxy = the engine entry time of taken rows within 14:40-15:00 ET; the D7 base will differ. (7) Dedup: identical-result groups (sets differing only by an unused Pre-open / Close session) are shown by their fewest-session member. (8) No PASS claim. Shadow only.

## F. Re-run on the delivered D7 base

`python3 -I l2vast/ds3/code/better_s7/sweep_d7.py <shard> 3 <tag>` (3 shards; writes sweepD7<tag>_off_*.pkl), `nypm_block_d7.py <shard> 3 <tag>`, then `a_score_d7.py <tag>` and `d7_section.py <tag>`; `write_md.py` assembles this file. dead cells: `append_dead.py` (program BETTERS7) after scoring.

## CHECKPOINT: OLD CAP interim (cap 20260206; windows L3M/L6M/HOLD/PRE/X'). Written on the lead's T-RECENT-REDO order; nothing deleted

Built and scored (old cap): (a) 384-cell session sweep on the interim one-convention base (lock off) plus 12R finalists, equal-risk engine reruns, joint runs, walk-forward, best-of-64 null; (b)(i) close book 8 cells x M/LC x 1/2/3 lots with placebos, LOEO, bootstrap; (b)(ii) K7 NY-PM block 5 windows x 3 scopes + 200 random-window placebo. Same three on d7lib: BASE-noTH (D1) and literal draft (D2, 15:11Z version); the K7 block on D2 was NOT run (d7lib broke at 15:12Z). Dead cells: 407 appended (program BETTERS7I); D1 append (program BETTERS7D1) NOT done (append_dead_d1.py has an indentation error at the nypm loop, fix then run).
Entry points (l2vast/ds3/code/better_s7/): bs7_lib.py (6-session custom lot hook), sweep_a.py / sweep_d7.py (env D7OV json overrides), a_score.py <lock> [prefix], a_final.py, joint*.py, close_book.py + close_score.py [tag], nypm_block.py / nypm_block_d7.py, blk_score*.py, report.py, d7_section.py, write_md.py (assembles this file from out/better/s7/doc_template.md), append_dead.py. Prereg l2vast/ds3/prereg/BETTER_S7_prereg.md sha256 a420d2b618d3e303a1955b5140e8fa2b9d579f2732d80398938db675f23a0bb5.
Outputs: l2vast/ds3/out/better/s7/ (sweep_off_*.pkl, sweepD7noTH_off_*.pkl, sweepD7draft_off_*.pkl, a_cells_*.csv, a_*.pkl, close_scored*.pkl, blk*_scored*.pkl, tables_all.md, d7_section_*.md).
To redo on the new cap: change the window table and cap in wlib.py (WINS, PX) and the data cap in the base engines, then rerun sweep_a/sweep_d7 -> a_score -> a_final -> joint -> close_book/close_score -> nypm_block* -> report -> write_md. All numbers above are OLD CAP.
