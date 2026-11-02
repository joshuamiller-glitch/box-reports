# DS3_EXIT_N_AUDIT - independent audit of the T-EXIT-N conclusion (S4b, 2026-11-02, written for the 23:00Z final)
Method: the 10 best exit cells across E1-E4 by (L6M cut + PRE cut) ignoring labels, taken from the family result files (E1 e1_cells.csv, E3 res_*.pkl cubes scored with my scorer, E4 page table), plus the best E4 cell (not in the top 10 by this rule) and my own best E2 cell. Each was recomputed FROM SCRATCH in a fresh process: d7_v13t.run_v13t_live(ov) with the cell's own override (E1: engine th_loss path with the flip combo, as coded by S4a) or ov={'inject': [...]} built from the authors' row kernels (E3 take_rows/take_rows2, E4 build()), plus INDEPENDENT row generation for two E3 cells (my own iceberg-against take kernel, e2cd.sim_take, written without e3lib), and scored with my own scorer (agg.py windows, weekly-cumulative maxDD of the 11-book total; not S5's harness). Code: l2vast/ds3/code/zones3/s4b/audit_cells.py; raw results /mnt/l2/l2vast/ds3_zones3_new/e2/audit_res.pkl.
Base V13T_LIVE recomputed: maxDD $k L6M 150.7 / HOLD 150.7 / MID 43.7 / PRE 166.2 / X' 92.5 (identical with grid 1sh), equal to the E1 reference row and the base used on the E3 and E4 pages.
## 1. Verdict
**The numbers on the family pages reproduce.** All 12 cells that have a page row agree with the recomputation to <= 0.09% of the maxDD (E1 cells exactly; E3 to 0.03-0.09%; E4 to 0.04-0.06%, limited by the 0.1-point rounding of the page cuts). The independent iceberg-against gate kernel reproduces the E3 G14ice cells EXACTLY in all five windows although it flags more library rows (33,659 vs the page's 20,071 fired rows, because it does not restrict to the core-book taken set; the extra rows are never taken, so the engine result is identical: the page 'n' column is not comparable with a raw flagged-row count). No discrepancy above 1%.
## 2. Recomputed table
| family | cell | rows injected / flagged | maxDD $k L6M / HOLD / MID / PRE / X' (recomputed) | page values | max rel diff vs page | cut L6M / PRE | mean change $k/wk L6M / PRE vs base |
|---|---|---|---|---|---|---|---|
| E1 | B flip K2 arm15 | 0 | 111.2 / 111.2 / 41.3 / 128.9 / 117.0 | 111.2 / 111.2 / 41.3 / 128.9 / 117.0 | 0.00% | +26.2% / +22.4% | -11.14 / -8.34 |
| E1 | B flip SWP arm15 | 0 | 107.1 / 121.5 / 76.3 / 114.1 / 110.5 | 107.1 / 121.5 / 76.3 / 114.1 / 110.5 | 0.00% | +28.9% / +31.3% | -15.89 / -7.18 |
| E3 | R3v2|G10delta|a0.3|T20 | 23270 | 52.4 / 173.1 / 118.8 / 205.9 / 185.3 | 52.4 / 173.1 / 118.8 / 205.9 / 185.3 | 0.03% | +65.2% / -23.9% | -3.91 / -10.25 |
| E3 | R3v2|G14ice|a0.3|thr200 | 20071 | 98.1 / 164.9 / 69.2 / 154.9 / 125.0 | 98.1 / 164.9 / 69.2 / 154.9 / 125.0 | 0.06% | +34.9% / +6.8% | +0.88 / -9.28 |
| E3 | R3v2|G14ice|a0.7|thr50 | 22177 | 109.8 / 115.6 / 37.5 / 146.2 / 69.0 | 109.8 / 115.6 / 37.5 / 146.2 / 69.0 | 0.09% | +27.1% / +12.0% | -6.93 / -4.61 |
| E3 | R3v2|G15sweep|a0.7 | 22490 | 113.5 / 113.5 / 48.2 / 145.0 / 68.4 | 113.5 / 113.5 / 48.2 / 145.0 / 68.4 | 0.05% | +24.7% / +12.7% | -6.95 / -5.26 |
| E3 | R3|delta|a0.3|T100 | 13167 | 113.0 / 171.6 / 71.1 / 148.2 / 149.5 | 113.0 / 171.6 / 71.1 / 148.2 / 149.5 | 0.03% | +25.0% / +10.8% | -1.24 / -5.84 |
| E3 | R3|delta|a0.5|T30 | 21295 | 83.9 / 156.5 / 90.2 / 166.3 / 69.8 | 83.9 / 156.5 / 90.2 / 166.3 / 69.8 | 0.05% | +44.4% / -0.1% | -7.30 / -6.95 |
| E3 | R3|pull|a0.5|thr1.0 | 23471 | 91.7 / 111.8 / 73.6 / 151.5 / 71.8 | 91.7 / 111.8 / 73.6 / 151.5 / 71.8 | 0.04% | +39.2% / +8.8% | -10.33 / -9.57 |
| E3 | R3|pull|a0.5|thr1.25 | 21734 | 90.3 / 115.8 / 69.5 / 157.7 / 76.8 | 90.3 / 115.8 / 69.5 / 157.7 / 76.8 | 0.05% | +40.1% / +5.1% | -8.37 / -9.32 |
| E3ind | IND ice a0.3 thr200 (own gate kernel) | 33659 | 98.1 / 164.9 / 69.2 / 154.9 / 125.0 | - | n/a (no page row) | +34.9% / +6.8% | +0.88 / -9.28 |
| E3ind | IND ice a0.7 thr50 (own gate kernel) | 38150 | 109.8 / 115.6 / 37.5 / 146.2 / 69.0 | - | n/a (no page row) | +27.1% / +12.0% | -6.93 / -4.61 |
| E4 | RT100_BTswing_ALL | 1076 | 105.6 / 124.3 / 44.1 / 165.6 / 75.7 | 105.5 / 124.4 / 44.1 / 165.7 / 75.7 | 0.06% | +30.0% / +0.3% | +3.66 / +0.25 |
| E4 | RT70_BTswing_ALL | 1076 | 110.5 / 121.2 / 41.9 / 163.5 / 70.9 | 110.5 / 121.2 / 41.9 / 163.5 / 70.9 | 0.04% | +26.7% / +1.6% | +3.79 / -0.17 |
| E2 | K7TR_P0.7_30_G1 | 1474 | 142.6 / 142.6 / 52.9 / 171.5 / 93.2 | - | n/a (no page row) | +5.4% / -3.2% | -1.47 / -0.11 |
Columns: maxDD of the weekly cumulative total in the window ($k), page values from the family page (E1 e1_cells.csv, E3 DS3_EXIT_N_TAKE.md first block, E4 page cut converted to $k), cut vs the base, mean change vs the base in $k/wk.
## 3. What the recomputed top 10 say about the conclusion
Every one of the 10 largest L6M+PRE cuts is paid for: mean change L6M -1.2 to -16k/wk (only G14ice a0.3 thr200 is +0.9k in L6M and it has PRE -9.3k/wk), and each makes at least one window clearly worse than the base: MID maxDD 76.3 (SWP15), 73.6 (pull a0.5 thr1.0), 118.8 (G10delta a0.3), 90.2 (delta a0.5 T30) vs 43.7; HOLD 173.1 / 171.6 / 164.9 / 156.5 vs 150.7; X' 185.3 / 149.5 / 125.0 vs 92.5 (the delta and ice-200 cells). The largest cut pair in the program (E1 B flip SWP arm15: L6M +28.9%, PRE +31.3%) has MID +75% worse and -16k/wk. So the audit supports the T-EXIT-N conclusion that no exit rule is a lead on basis N: the cuts are real in the recomputation but are volume/cost effects concentrated in single windows, not free drawdown reduction. The E4 re-target cells RT100/RT70_BTswing_ALL are the only ones with positive mean change (+3.7k/wk L6M) and a clean MID/HOLD, but with PRE +0.3%/+1.6% (no PRE protection) and X' strongly different (75.7/70.9 vs 92.5); they are the BT-flip level re-target and are covered by the zone/BT pages.
## 4. Bug scan: th_loss=False with an injected exit
* **The bug:** with th_loss=False the engine does not merge injected exits (V13X _merge13 is only reached through the TH-L2 part list), so a run with th_loss off plus inject silently equals the no-cut base. I hit it myself in E2c REPLACE (first run; corrected with the base cut moved to 55 pts, ledger rows with '|v2'; the earlier EXITN_E2C REPLACE rows are invalid and are said so in DS3_EXIT_N_FLOW.md).
* **Remaining occurrence in code:** zones3_new/s4a/e1_harness.py lines 9 and 25 (S4a addendum-2 harness route: ov['th_loss']=False with the K-table cut set injected). Its results (/mnt/l2/l2vast/ds3_zones3_new/s4a/e1_harness.pkl, e.g. B flip SWP arm30 cut L6M -0.15 with 38,885 'rows') equal the no-cut case and are the 'does not tie out' numbers the E1 page already discloses (page line 128). **Not on any page as a result:** I recomputed the per book x session table of the three near cells with the valid engine path and it matches the page exactly (K7 +0.09|-0.13, P7 +0.02|+0.08, U7 -0.01|+0.09, H7 +0.13|+0.07, asia -0.29|+0.09 for B flip SWP arm30), while the harness cubes give K7 -0.03|-0.20 (different). Recommend: S4a deletes/flags e1_harness.pkl and the REPLACE harness route.
* **Checked and clean:** E1 e1_run.py (engine th_loss path; 'noCut' is a no-inject reference); E1 e1_flow.py (th_loss_arm 1e6 with first_rows patched; its 12 stored cells differ from the no-cut cell: e.g. SWPF 30 L6M/PRE 179.7/155.6 vs no-cut 197.9/282.7 so the injections were applied); E3 e3lib (run_take/run_take2/take_rows: th_loss on); E4 e4_run (th_loss on); E2 (mine, th_loss on); S5 exit_harness._run (th_loss on). Grep over zones3_new, zones3_s5, zones3/s2, zones3/s4b, zones3_s3, zl2: the only inject-with-th_loss-off lines are the two in e1_harness.py.
## 5. Other observations
* E1 cells are engine-path runs (th_loss override with a K-table flip combo through a monkey-patched lc_rows.fire_mask, thr >= 1000 as the combo switch); I reproduced them exactly with a copy of that patch, so their reproducibility depends on that convention (documented in e1_run.py, not in the page).
* The first EXITN_E2/E2B/E2D cubes use the library entry second as the pct reference (entry-fill timing approximated); not part of this audit.
* Not audited: E1 time-stop/blackout cells, E3 zone-as-gate and the five exact lines (they were outside the top 10), placebos and PA-band computations of the families (they use S5's harness).


# EXTENSION (S4b, 17:48Z): the cells left out of the first audit, independent PA9 and a placebo
## 6. E1 time-stop / blackout and E3 exact-line / plain-pct / zone-as-gate cells (12 cells recomputed from scratch)
| family | cell | injected rows | maxDD $k L6M / HOLD / MID / PRE / X' (recomputed) | page values | max rel diff |
|---|---|---|---|---|---|
| E1 | C time-stop 10min | engine ov | 181.0/263.9/147.6/232.3/166.2 | 181.0/263.9/147.6/232.3/166.2 | 0.00% |
| E1 | C time-stop 20min | engine ov | 176.6/218.7/132.7/206.1/239.6 | 176.6/218.7/132.7/206.1/239.6 | 0.00% |
| E1 | C time-stop 30min | engine ov | 183.0/194.3/69.1/354.7/187.1 | 183.0/194.3/69.1/354.7/187.1 | 0.00% |
| E1 | C time-stop 5min | engine ov | 156.7/321.2/166.5/209.8/122.4 | 156.7/321.2/166.5/209.8/122.4 | 0.00% |
| E1 | D blackout assumed 15min | engine ov | 147.2/147.2/45.0/167.5/90.7 | 147.2/147.2/45.0/167.5/90.7 | 0.00% |
| E1 | D blackout assumed 60min | engine ov | 141.3/141.3/46.0/194.5/152.5 | 141.3/141.3/46.0/194.5/152.5 | 0.00% |
| E3 | R1|exact5 | engine ov | 163.8/177.5/107.3/222.9/80.5 | 163.8/177.5/107.3/222.9/80.5 | 0.04% |
| E3 | R2|plain0.5 | engine ov | 97.0/142.4/105.8/186.3/75.2 | 97.0/142.4/105.8/186.3/75.2 | 0.02% |
| E3 | R2|plain0.7 | engine ov | 118.4/118.4/48.0/145.5/64.2 | 118.4/118.4/48.0/145.5/64.2 | 0.08% |
| E3 | R4|zone|ahead0.0 | 8624 | 117.1/117.1/29.5/171.2/129.0 | 117.1/117.1/29.5/171.2/129.0 | 0.04% |
| E3 | R4|zone|ahead1.2 | 3712 | 138.7/138.7/34.2/159.7/112.7 | 138.7/138.7/34.2/159.7/112.7 | 0.12% |
| E3 | R4|zone|ahead1.5 | 1801 | 171.2/171.2/44.2/171.9/115.3 | 171.2/171.2/44.2/171.9/115.3 | 0.06% |
All 12 agree with the family pages to <= 0.12% of the maxDD (E1 cells exactly). Code: zones3/s4b/audit2.py (E1 time-stop kernel copied from e1_run.py, so the row set is S4a's; E3 plain/exact via the lines option, zone via take_rows(4,...)).
## 7. Independent phase-averaged (K = 9) cuts, own code (zones3/s4b/audit3.py: week-key shift of de_engine._ENV['WK'] by -4..+4 for the base and the cell, cut = mean over the 9 shifts of the per-shift maxDD cut)
| cell | my PA9 cut L6M / HOLD / MID / PRE / X' | page (E1 section 4, S5 harness) | max abs diff |
|---|---|---|---|
| B flip SWP arm15 | +0.41 / +0.31 / -1.40 / +0.32 / -0.19 | +0.41 / +0.31 / -1.40 / +0.32 / -0.19 | 0.004 |
| B flip K2 arm15 | +0.35 / +0.35 / -0.43 / +0.23 / -0.33 | +0.35 / +0.35 / -0.43 / +0.23 / -0.33 | 0.005 |
| B flip SWP arm30 | +0.19 / +0.17 / +0.01 / +0.08 / -0.13 | +0.19 / +0.17 / +0.01 / +0.08 / -0.13 | 0.004 |
| B flip ICE arm15 | +0.32 / +0.32 / -0.38 / +0.15 / -0.30 | +0.32 / +0.32 / -0.38 / +0.15 / -0.30 | <= 0.005 (page table value) |
The PA9 machinery used on the E1 page reproduces to the second decimal for all four cells.
## 8. Independent placebo A (100 draws; random cut trades, same count per day, among trades that reach the same adverse threshold, run through the same V13T_LIVE engine path), own draw code
| cell | real cut L6M / PRE / X' (phase 0) | placebo median cut L6M / PRE / X' | share of placebo draws below the real cut L6M / PRE / X' | rank with ties half (S4a's convention) L6M |
|---|---|---|---|---|
| B flip SWP arm30 | +0.207 / +0.093 / -0.070 | +0.207 / +0.119 / +0.110 | 0.00 / 0.00 / 0.00 | 0.50 (page: A 0.50, n 100) |
| B flip SWP arm15 | +0.289 / +0.313 / -0.195 | +0.289 / +0.313 / -0.190 | 0.00 / 0.06 / 0.01 | 0.50 |
| B flip K2 arm15 | +0.262 / +0.224 / -0.265 | +0.262 / +0.225 / -0.257 | 0.00 / 0.42 / 0.01 | 0.50 |
**Finding: placebo A cannot test the L6M cut of the E1 cells.** The median placebo L6M cut equals the real cut to three decimals in all three cells, and the share of draws below the real cut is exactly 0 (all draws tie or exceed). Reason: the L6M (= HOLD) maxDD is carried by one week; on the days of that episode the 'same count per day among trades that reach the arm' draw selects ALL eligible trades (the count equals the pool), so the placebo cut set equals the real one there and reproduces the real L6M cut regardless of the flip flag. The page's 'A 0.50' for SWP arm30 is that tie (rank with ties counted half), not evidence that the flag is no better than random. The same placebo is informative in PRE, and there the cells do NOT beat random cut sets: the real PRE cut is above only 6% of the placebo draws for SWP arm15 and 42% for K2 arm15 (SWP arm30: real +0.093 against a placebo median +0.119, above 0%) and in X' (placebo median close to the real, all negative). So the E1 page's statement that the B-flip cells' L6M cuts are 'ONE-WEEK / not distinguishable from a random cut set' is right, but for a structural reason: a same-day random-trade placebo shares the carrying week with the cell. The same-volume placebo (B) or shuffled-day placebo (C) are the informative ones for the carrying week (SWP arm30: B 0.01, C 0.05 on the page).
## 9. Ledger / flags
S4a confirmed the e1_harness fix (pickle renamed e1_harness_INVALID.pkl, header note in e1_harness.py, E1 page sentence corrected); no note appended by me.
