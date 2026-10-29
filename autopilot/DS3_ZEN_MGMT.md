# DS3_ZEN_MGMT - ZEN family MGMT (trailing stops, pyramiding, scaling in, complete management), D3ZMG

VERDICT: DEAD (all 54 holdout cells fail >= 5 gates each; no CANDIDATE, no PASS). No management shape is a tested improvement on the plain bracket; see below.

Hashes: prereg ZEN_MGMT 4e9df16c...42d70 (N = 22,020 scored); cell table 33dc630e...2dc; PREHOLD list 1 8ecba920...97f1f; list-2 prereg ZEN_MGMT_list2_prereg.md 269957c4...e03bda (logged in DECISIONS.md before the ranking was read); list 2 cells (out/zen/mgmt/list2_cells.txt) 418e8503...f45f27f. One combined HOLD + X + WF look on the union of 54 cells, logged in out/zen/mgmt/looks.jsonl (track MGMT_HOLD) before any HOLD/X number was read. Code: code/zen/mgmt/{mg_lib,mg_kernel,mg_pre,mg_list2,mg_hold}.py. Per-cell table: out/zen/mgmt/hold_summary.csv (+ hold_rows.pkl, hold_groups.pkl: hour / side / half-year splits).

## PRE screen (22,020 cells, 15,769 with n >= 100)
Gates on n>=100 cells: G1 185, G2 965, G3 1,210, G4 2,382, G5 5, G1m 1,631; G1+G2+G3+G4+G5 together: 0. Paired delta vs the plain bracket on identical entries (n>=100): P1 mean -0.77 pt (50% positive), P2 mean -1.83 (24% positive), P3 -0.19 (58%), P4 -1.39 (14%); 816 cells have a paired CI lower > 0 but they are small-effect P1 / P3 shapes (best +6.3 pt, B10 S60 fix30 trail, effect vs random-in-regime CI lower < 0). Only 7 of 23 plain controls beat random-in-regime.

## Best-of-N reality check (G8), as written in the prereg
- Null INCLUDES the n<100 cells (every cell with n >= 30 scored, N = 22,020): best cell +59.95 (B05 S60 P2 X10 1.5 3 C W, n 77, MDE80 85.1), null median 32.2, p95 55.5, **p = 0.04**. That cell has n < 100 and cannot be sent to the holdout; it is also far inside its own MDE80.
- Excluded version (n >= 100 only, 15,769 cells), printed beside it: best +22.31 (the list-1 #1 cell), null median 23.5, p95 42.9, **p = 0.54**.
- Neither changes the verdict. For the 54 holdout cells the per-cell best-of-N p (centred max null, N = 22,020) is 0.84-1.00 (median 0.99); with the n>=100 null 0.54-1.00. None reaches 0.05. MDE80 of the PRE effects of the 54: 5.0-88.7 pt; of the HOLD effects 5.9-122 pt.

## Holdout results (HOLD 2025-07-01..2026-02-06; X 2023-04-01..2024-01-31; WF 2024-02..2026-02-06)
List 1 (30 near-duplicate S60 pyramid cells, mostly B03/B08, PRE effect +12.7..+22.3): HOLD effect vs random-in-regime positive in 20/30 (mean +5.5 pt vs +15.3 on PRE), CI lower > 0 in 0/30, effect >= MDE80 in 0/30; HOLD paired delta vs plain bracket mean -2.65 pt (positive in 8/30, paired CI lower > 0 in 0). X effect >= 0 in about 2/3; paired delta in X positive in 6/30.
List 2 (30 diversity-capped, one per idea cluster, 6 cells overlap list 1; E1-E5 and B02-B10): PRE effect mean +3.75; HOLD effect positive in 17/30 (mean +1.21), CI lower > 0 in 1/30, effect >= MDE80 in 0/30; HOLD paired delta mean +0.87 pt (17/30 positive, paired CI lower > 0 in 0). WF paired delta positive in 30/30 of list 2 but with CI-wide, carried by 2024-25 PRE-era trades that were also used for selection.
Across all 54: HOLD effect positive 32/54 (chance level); HOLD net1 positive 26/54; per-trade win rate above break-even 13 (list 1) / 17 (list 2); lot-gate G1m on HOLD 9 / 7; G6 1/54, G7 38/54, G8 0/54, G9 8/54.
Only G6 survivor: E5 S60 P2 TCH 1.5 3 B W (list 2): PRE effect +1.79 (CI lo -7.21, rank 0.71, MDE80 13.2), HOLD effect +13.87 (CI lo +0.57, MDE80 19.4, n 310, net +27.9 pt/trade), X effect +1.72 (n 336), WF net +17.9, positive in 3/3 years, max year share 51%; fails G1, G2, G5, G1m, G8 (p 1.00). One CI-lower > 0 among 54 looks is what chance gives (expected ~1.35); forward weeks for 80% power at the HOLD effect ~147 (MDE 19.4 > effect 13.9). Not a candidate; at most a watch item that needs fresh data.
Verdict gate list (every cell DEAD): the most common failed sets are G1,G5,G6,G8,G9 (8 cells) and G1,G5,G1m,G6,G8,G9 (7); the full per-cell failed-gate string is in hold_summary.csv (column failed). G10 (1-s / L2 direct replay) NOT run (no governor allow-list entry; requested in MORNING.md).

## Answer to the question
Entry x management does not beat the plain bracket out of sample. Paired deltas are negative on average in PRE (all four families) and in HOLD for list 1 (-2.65 pt, the selected pyramids shrink from +15 to about +5 vs random and to -2.65 vs plain); list 2's +0.87 is inside noise (no paired CI lower > 0). Pyramids add lots (average 2.6-2.8 units) so lot-matched deltas look better than risk-matched ones (risk-matched positive in 10 of 30 for list 1). Trailing stops and scale-in give no durable gain. Prior position (exits on existing books dead) stands.
Selection caveat: the 10 B-cells were chosen on a max over 47,602 cells (donor effects upward-biased); list 1 is dominated by two entry cells and one management idea, so its effective independent count is small; list 2 was added at the user's request to remove that.
DONE MGMT
