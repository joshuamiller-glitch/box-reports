
## SIZER_S3 (Z3): section 3 - combinations, learned mapping, risk parity, exits, locks (interim 2026-11-02 ~18:10Z)
Shadow only, no PASS claims. Base V13T_LIVE, SEQUENTIAL rounding (user answer from DS7 code), reference = live binary ER(20) 5-min ladder (x1.5 if ER >= 0.30 else x0.5) in sequential mode, phase-matched for PA9; sizer off is not a row. Prereg SIZER_PREREG_DRAFT.md section 3 (hashed in DECISIONS.md 17:49Z). Code l2vast/ds3/code/sizer_s3/ (sizer3.py, run_indep.py, run_pool.py); results out/sizer_s3/. Cut = 1 - maxDD(cell)/maxDD(live ladder); positive = shallower. Band = tl_band_final PA9.

Status: the pool-dependent cells (3.2 combinations 114, 3.3 learned mapping 6 + comparison, 3.6 sizer x lock) wait for the section 1-2 tables of S4a/S4b to fix the pool P8 (rule: S_sel on PRE and X' only). Machinery built and tied out (sequential baseline total $3,475k; rebuilt ladder differs from the engine's by up to $8.8k only because er_5m_20 from the feature parquet differs on 0.03% of rows). Pool-independent cells are done:

### 3.4 Risk parity (lots = target risk $ / (stop pts x $20))
FINDING: the engine library stop distance is a constant 60 pts (45 for WT), so a parity on the stop is the identity (m = 1 everywhere). The ATR stop of the prereg is therefore implemented as ATR14 of the 5-min bars at the signal as the stop proxy: m = clip(t x median over the book's previous 60 days of ATR / ATR_i, 0.5, 2.0), t in {0.75, 1.0, 1.25}; "ER on top" = m x live ER multiplier (cap 0.25-3.0). Rows marked NON-CANDIDATE replace the ER ladder (ER is a KEEP).
| cell | L6M cut | PRE cut | X' cut | MID cut | L6M cut, W27-38 dropped | PRE cut, W34-51 dropped | L6M d mean $/wk (MDE) | PA9 L6M / PRE | mean lots | band / no-harm |
|---|---|---|---|---|---|---|---|---|---|---|
| RP t=0.75, ER on top | +34.0 | -18.2 | -74.4 | +42.0 | +46.4 | -23.4 | -1,196 (15,390) | +43.0 / -30.2 | 3.2 | fail / fail |
| RP t=1.00, ER on top | +23.0 | -36.1 | -88.0 | +20.5 | +29.2 | -42.1 | +10,980 (17,072) | +27.8 / -47.2 | 3.9 | fail / fail |
| RP t=1.25, ER on top | +28.6 | -41.7 | -103.0 | +14.6 | +13.1 | -48.0 | +21,807 (19,623) | +20.9 / -64.7 | 4.5 | fail / fail |
| RP t=0.75 alone (NON-CANDIDATE) | +35.6 | +34.4 | -90.8 | -15.6 | +51.4 | +31.5 | -5,336 (22,623) | +42.9 / +24.6 | 3.3 | pass / fail (X') |
| RP t=1.00 alone (NON-CANDIDATE) | +20.4 | +15.2 | -126.3 | -41.8 | +26.7 | +11.5 | -221 (25,018) | +29.9 / +17.7 | 4.1 | pass / fail (X') |
| RP t=1.25 alone (NON-CANDIDATE) | +3.9 | +4.0 | -164.3 | -76.0 | +2.6 | -0.3 | +6,389 (25,701) | +16.8 / +6.4 | 4.7 | fail / fail |
Reading: ATR risk parity under the ER ladder helps L6M (and MID) but hurts PRE and X' badly: no flag. Alone it cuts L6M and PRE but is not an ER-based sizer, fails no-harm in X' (-91% to -164%), and its mean is not above the ladder in L6M at t=0.75: reported, not ranked.

### 3.5 Sizer on exits: bracket (stop = target = S points) on signals with ER(20) 5-min <= cutoff (live ER sizer unchanged; engine bracket hook, tighter-or-equal only)
| cutoff / S | L6M cut | PRE cut | X' cut | MID cut | L6M d mean (MDE) | PA9 L6M / PRE | band / no-harm |
|---|---|---|---|---|---|---|---|
| 0.10 / 40 | +9.1 | +4.0 | -18.8 | +8.6 | -2,534 (6,578) | +4.5 / +5.3 | fail / pass |
| 0.10 / 45 | -3.9 | +4.5 | -17.5 | +11.9 | -2,547 (6,664) | -2.9 / +2.8 | fail / pass |
| 0.10 / 50 | -11.0 | +1.3 | -12.6 | +11.6 | -1,133 (3,454) | -10.0 / +0.2 | fail / pass |
| 0.15 / 40 | +3.4 | -2.9 | -15.8 | +1.4 | -2,741 (6,155) | -4.1 / -0.9 | fail / pass |
| 0.15 / 45 | -1.1 | -0.2 | -19.7 | +14.5 | -2,283 (6,619) | -8.2 / +1.1 | fail / pass |
| 0.15 / 50 | -1.1 | -1.7 | -16.8 | +14.7 | -2,372 (5,250) | -6.7 / -0.3 | fail / pass |
| 0.20 / 40 | -10.1 | -3.2 | -36.2 | +12.0 | -3,070 (6,440) | -17.9 / -0.4 | fail / fail |
| 0.20 / 45 | -7.3 | +3.5 | -38.5 | +21.2 | -2,201 (7,510) | -14.8 / +6.6 | fail / fail |
| 0.20 / 50 | +10.5 | +5.5 | -17.2 | +20.6 | -1,856 (5,616) | +4.2 / +2.9 | fail / pass |
Reading: all 9 cells are inside the noise band (|PA9| <= 18), none cuts L6M and PRE together above band, the mean falls in every cell (-1.1k to -3.1k/wk, within MDE) and X' is worse by 13-39%: DEAD for maxDD; no flag. Bracket cells use the live ER ladder as given; equal-risk and placebos are not run (no cell passes the band).

### Flags
None. No cell in this interim meets L6M AND PRE with the carrying week dropped at the same-or-better mean in an ER-based sizer.
### Next
3.2 combinations (84 pairs + 30 triples; ER-based ones ranked), 3.3 learned monotone mapping (6 cells, purged walk-forward vs best hand ladder on identical months), 3.6 sizer x lock, placebos (3 x 100) and equal-risk for survivors of the band gate, worst single-day exposure and lots distribution per book x session for every ranked cell (Addendum 2.3). Starting when the section 1-2 tables fix P8.

# T-SIZER SECTION 3 (Z1, ledger program SIZER_S3X): sizer x lock and sizer on exits, ladder ON (KEEP) - 2026-11-02 18:06Z
POST-HOC, no PASS, Shadow only. Prereg SIZER_S3X_Z1_prereg (sha 49666bd6...) in DECISIONS.md. Base V13T_LIVE + HALF layer, live ER ladder ON (binary 0.30 x1.5/x0.5), per-book locks only. "Live" lock cell = floor 12R + give-back arm 2R keep 50% with the LIVE-FAITHFUL R unit (day locks scale only when mult > 1: R x max(1, running-max SizeMult), user answer 2026-11-02). Phase-averaged over 9 lock-reset phases. Ladder OFF is reference only.

## Plain answers
* Best lock cell with the ladder ON (live-faithful R), by PA maxDD: L6M/HOLD and X' floor 10R without give-back (155k, 155k, 72k; mean 39.1k L6M vs 37.5k for the live cell), PRE floor 12R + arm 1.5R keep 0.75 (146k but mean 10.7k vs 17.6k). No cell has lower maxDD and mean >= the live cell in L6M AND PRE together (table below): the live 12R + 2R/50% lock stays the reference; 10R/no-give-back is better in L6M (155 vs 160k, mean +1.6k), HOLD and X' (72 vs 79k, mean +0.9k) but worse in MID and PRE (183 vs 170k).
* Is ER x0.5 making a tighter give-back redundant? Not in the sense of the prereg test (it fails on both sides): with the ladder ON a tighter give-back (arm 1.5R keep .5/.75/.25) vs the same floor without give-back changes PA maxDD L6M +29k/+16k/+21k (worse), PRE -30k/-37k/-9k (better), X' +21k/+16k/+27k (worse) and costs mean 3.5-8.6k/wk in L6M; with the ladder OFF the same give-back lowers L6M maxDD (-19k/-16k/-7k) and X' rises +12k/-2k/+13k, PRE -1k/+21k/0. So the ladder reverses the sign of the give-back effect in L6M (the x1.5 winners are trimmed by the give-back, the x0.5 rows add nothing), tighter give-back is NOT a free complement to the ladder and is not recommended with it on; it is not "redundant" either (it helps PRE), it is harmful in the recent window.
* R-unit convention matters: R scaled by the full running-max SizeMult (engine default, scales down too) vs the live-faithful max(1, .) vs base-lot R changes the live cell by up to +/-12k L6M / 25k PRE maxDD; base-lot R (no scaling) is worse than the live-faithful one in L6M and X' for almost every cell (live cell L6M 160k / mean 37.5k vs 188k / 30.8k).
* Sizer on exits (bracket by ER) on the exact kernel: nothing beyond the band (see SIZER_BRACKET_PREP.md corrected section): the cells beyond the PA9 band are PRE-only with parity lots (ER<=.15 -> 45/45 PRE +22%, ER<=.30 -> 45/45 PRE +13%, ER>.30 -> 75/75 PRE +11%) and all three are chance against 100 draws per kind (PRE ranks 0.33-0.48) and negative in L6M and X'. No winner flagged.

## Table 1: lock cell x R-unit convention, PA maxDD $k / PA mean $k per window
| lock cell | mode | PA maxDD $k / mean $k per window: L6M | HOLD | MID | PRE | X' | n phases |
|---|---|---|---|---|---|---|---|
| floor 12R / arm 2.0R keep 0.50 | ladder ON, live-faithful R | 160 / 37.5 | 160 / 31.7 | 49 / 23.7 | 170 / 17.6 | 79 / 5.1 | 9 |
| floor 12R / arm 2.0R keep 0.50 | ladder ON, engine default R | 172 / 36.2 | 172 / 30.6 | 41 / 25.1 | 168 / 17.1 | 89 / 4.5 | 9 |
| floor 12R / arm 2.0R keep 0.50 | ladder ON, base-lot R | 188 / 30.8 | 188 / 26.0 | 50 / 18.7 | 132 / 12.2 | 160 / 5.2 | 9 |
| floor 12R / arm 2.0R keep 0.50 | ladder OFF | 82 / 26.1 | 192 / 21.0 | 135 / 3.8 | 120 / 13.7 | 121 / 4.9 | 9 |
| floor 10R / no give-back | ladder ON, live-faithful R | 155 / 39.1 | 155 / 34.0 | 59 / 25.6 | 183 / 17.7 | 72 / 6.0 | 9 |
| floor 10R / no give-back | ladder ON, engine default R | 135 / 40.0 | 147 / 34.4 | 42 / 27.3 | 172 / 17.0 | 83 / 4.8 | 9 |
| floor 10R / no give-back | ladder ON, base-lot R | 150 / 35.9 | 150 / 31.9 | 60 / 20.9 | 166 / 15.9 | 114 / 5.5 | 9 |
| floor 10R / no give-back | ladder OFF | 82 / 30.7 | 211 / 26.2 | 132 / 13.7 | 126 / 14.1 | 109 / 5.4 | 9 |
| floor 12R / no give-back | ladder ON, live-faithful R | 155 / 39.1 | 155 / 34.0 | 59 / 25.4 | 183 / 17.7 | 73 / 5.9 | 9 |
| floor 12R / no give-back | ladder ON, engine default R | 142 / 39.9 | 156 / 34.3 | 46 / 26.7 | 176 / 16.9 | 77 / 5.1 | 9 |
| floor 12R / no give-back | ladder ON, base-lot R | 154 / 35.9 | 154 / 31.8 | 62 / 20.7 | 162 / 16.0 | 116 / 5.4 | 9 |
| floor 12R / no give-back | ladder OFF | 86 / 30.5 | 215 / 26.0 | 135 / 13.3 | 115 / 14.3 | 110 / 5.3 | 9 |
| floor 8R / no give-back | ladder ON, live-faithful R | 157 / 39.1 | 157 / 34.1 | 59 / 26.0 | 183 / 17.6 | 76 / 5.8 | 9 |
| floor 8R / no give-back | ladder ON, engine default R | 138 / 39.9 | 144 / 34.5 | 34 / 27.6 | 187 / 16.3 | 85 / 4.4 | 9 |
| floor 8R / no give-back | ladder ON, base-lot R | 145 / 36.1 | 148 / 32.1 | 63 / 21.2 | 166 / 15.9 | 114 / 5.5 | 9 |
| floor 8R / no give-back | ladder OFF | 83 / 30.4 | 202 / 26.3 | 124 / 14.8 | 124 / 13.8 | 106 / 5.2 | 9 |
| floor 12R / arm 1.5R keep 0.25 | ladder ON, live-faithful R | 176 / 37.3 | 176 / 31.5 | 45 / 23.4 | 174 / 15.9 | 99 / 5.5 | 9 |
| floor 12R / arm 1.5R keep 0.25 | ladder ON, engine default R | 181 / 35.4 | 181 / 29.9 | 32 / 21.6 | 170 / 14.8 | 101 / 4.8 | 9 |
| floor 12R / arm 1.5R keep 0.25 | ladder ON, base-lot R | 163 / 30.6 | 163 / 25.2 | 48 / 15.1 | 152 / 11.6 | 133 / 5.0 | 9 |
| floor 12R / arm 1.5R keep 0.25 | ladder OFF | 79 / 29.8 | 180 / 24.2 | 112 / 8.7 | 115 / 12.6 | 123 / 5.5 | 9 |
| floor 12R / arm 1.5R keep 0.50 | ladder ON, live-faithful R | 184 / 35.6 | 184 / 30.1 | 34 / 25.0 | 153 / 15.0 | 94 / 5.4 | 9 |
| floor 12R / arm 1.5R keep 0.50 | ladder ON, engine default R | 193 / 34.2 | 193 / 28.6 | 26 / 22.9 | 145 / 14.6 | 105 / 4.6 | 9 |
| floor 12R / arm 1.5R keep 0.50 | ladder ON, base-lot R | 159 / 28.2 | 159 / 23.3 | 42 / 16.9 | 138 / 10.8 | 137 / 6.0 | 9 |
| floor 12R / arm 1.5R keep 0.50 | ladder OFF | 66 / 22.4 | 159 / 19.1 | 103 / 8.7 | 114 / 11.3 | 122 / 6.2 | 9 |
| floor 12R / arm 1.5R keep 0.75 | ladder ON, live-faithful R | 171 / 30.5 | 171 / 28.1 | 39 / 26.3 | 146 / 10.7 | 89 / 7.5 | 9 |
| floor 12R / arm 1.5R keep 0.75 | ladder ON, engine default R | 159 / 29.3 | 159 / 25.8 | 24 / 25.0 | 140 / 11.3 | 91 / 7.0 | 9 |
| floor 12R / arm 1.5R keep 0.75 | ladder ON, base-lot R | 144 / 21.2 | 144 / 18.0 | 35 / 15.0 | 144 / 7.5 | 124 / 7.9 | 9 |
| floor 12R / arm 1.5R keep 0.75 | ladder OFF | 69 / 21.5 | 137 / 17.8 | 91 / 10.4 | 137 / 8.3 | 108 / 7.5 | 9 |
| floor 12R / arm 3.0R keep 0.50 | ladder ON, live-faithful R | 157 / 39.3 | 157 / 33.2 | 50 / 22.5 | 183 / 18.0 | 76 / 5.9 | 9 |
| floor 12R / arm 3.0R keep 0.50 | ladder ON, engine default R | 144 / 39.7 | 148 / 33.4 | 40 / 24.3 | 181 / 16.6 | 78 / 5.3 | 9 |
| floor 12R / arm 3.0R keep 0.50 | ladder ON, base-lot R | 162 / 34.3 | 162 / 29.5 | 60 / 19.3 | 160 / 15.7 | 113 / 4.8 | 9 |
| floor 12R / arm 3.0R keep 0.50 | ladder OFF | 88 / 26.7 | 214 / 23.4 | 139 / 10.6 | 122 / 14.4 | 115 / 5.3 | 9 |
| floor 6R / arm 1.5R keep 0.75 | ladder ON, live-faithful R | 169 / 30.6 | 169 / 28.0 | 34 / 25.8 | 158 / 10.3 | 94 / 7.5 | 9 |
| floor 6R / arm 1.5R keep 0.75 | ladder ON, engine default R | 161 / 28.5 | 173 / 24.4 | 27 / 23.9 | 152 / 10.6 | 98 / 6.7 | 9 |
| floor 6R / arm 1.5R keep 0.75 | ladder ON, base-lot R | 132 / 21.8 | 132 / 18.5 | 37 / 14.9 | 146 / 7.4 | 122 / 7.8 | 9 |
| floor 6R / arm 1.5R keep 0.75 | ladder OFF | 64 / 21.6 | 131 / 17.9 | 89 / 11.0 | 140 / 8.3 | 118 / 7.2 | 9 |

## Table 2: ranked against the live cell (ladder ON, live-faithful R), same-or-better mean rule
| lock cell (ladder ON, live-faithful R) | PA maxDD change vs the live cell / PA mean change, $k: L6M | HOLD | MID | PRE | X' | windows with lower maxDD AND mean >= live | verdict |
|---|---|---|---|---|---|---|---|
| floor 10R / no give-back | -5 / +1.6 | -5 / +2.3 | +10 / +1.9 | +13 / +0.1 | -7 / +0.9 | L6M, HOLD, X' | mixed |
| floor 12R / no give-back | -5 / +1.6 | -5 / +2.3 | +10 / +1.7 | +13 / +0.1 | -6 / +0.8 | L6M, HOLD, X' | mixed |
| floor 8R / no give-back | -3 / +1.6 | -3 / +2.5 | +11 / +2.3 | +13 / -0.0 | -3 / +0.8 | L6M, HOLD, X' | mixed |
| floor 12R / arm 1.5R keep 0.25 | +16 / -0.2 | +16 / -0.2 | -3 / -0.4 | +4 / -1.6 | +20 / +0.4 | - | no |
| floor 12R / arm 1.5R keep 0.50 | +24 / -1.9 | +24 / -1.6 | -15 / +1.2 | -17 / -2.6 | +15 / +0.3 | MID | mixed |
| floor 12R / arm 1.5R keep 0.75 | +11 / -7.1 | +11 / -3.6 | -10 / +2.6 | -24 / -6.9 | +10 / +2.4 | MID | mixed |
| floor 12R / arm 3.0R keep 0.50 | -3 / +1.8 | -3 / +1.5 | +1 / -1.3 | +13 / +0.4 | -3 / +0.9 | L6M, HOLD, X' | mixed |
| floor 6R / arm 1.5R keep 0.75 | +9 / -6.9 | +9 / -3.7 | -15 / +2.1 | -12 / -7.3 | +15 / +2.4 | MID | mixed |

## Table 3: tighter give-back vs the same floor without give-back
* M1 floor 12R / arm 1.5R keep 0.50 vs 12R no-gb: PA maxDD change L6M +29k PRE -30k X' +21k (mean -3.5 / -2.7 / -0.5)
* M1 floor 12R / arm 1.5R keep 0.75 vs 12R no-gb: PA maxDD change L6M +16k PRE -37k X' +16k (mean -8.6 / -7.0 / +1.6)
* M1 floor 12R / arm 1.5R keep 0.25 vs 12R no-gb: PA maxDD change L6M +21k PRE -9k X' +27k (mean -1.8 / -1.7 / -0.5)
* OFF floor 12R / arm 1.5R keep 0.50 vs 12R no-gb: PA maxDD change L6M -19k PRE -1k X' +12k (mean -8.0 / -3.0 / +0.9)
* OFF floor 12R / arm 1.5R keep 0.75 vs 12R no-gb: PA maxDD change L6M -16k PRE +21k X' -2k (mean -8.9 / -5.9 / +2.3)
* OFF floor 12R / arm 1.5R keep 0.25 vs 12R no-gb: PA maxDD change L6M -7k PRE -0k X' +13k (mean -0.7 / -1.7 / +0.2)

## Table 4: best cell per window
* M1 L6M best PA maxDD: floor 10R / no give-back (155k)
* M1 PRE best PA maxDD: floor 12R / arm 1.5R keep 0.75 (146k)
* M1 X best PA maxDD: floor 10R / no give-back (72k)
* M1 HOLD best PA maxDD: floor 10R / no give-back (155k)
* OFF L6M best PA maxDD: floor 6R / arm 1.5R keep 0.75 (64k)
* OFF PRE best PA maxDD: floor 12R / arm 1.5R keep 0.50 (114k)
* OFF X best PA maxDD: floor 8R / no give-back (106k)
* OFF HOLD best PA maxDD: floor 6R / arm 1.5R keep 0.75 (131k)

## Bracket-by-ER placebos (exact kernel, 100 draws per kind, parity lots)
A1 lotpar (n 100/100/100): PRE cut +22% ranks 0.327/0.386/0.327 ; L6M cut -2% ranks 0.931/0.931/0.921 ; X cut -5% ranks 0.099/0.059/0.149
A2 lotpar (n 100/100/100): PRE cut +13% ranks 0.178/0.198/0.168 ; L6M cut -12% ranks 0.851/0.921/0.901 ; X cut -31% ranks 0.277/0.366/0.267
B1 lotpar (n 100/100/100): PRE cut +11% ranks 0.455/0.465/0.475 ; L6M cut -9% ranks 0.683/0.723/0.693 ; X cut -54% ranks 0.792/0.861/0.762

(Z1 SIZER_S3X correction to the R-unit sentence above: the three R-unit conventions move the cells by up to 20k PA maxDD in L6M and 12k in PRE (live cell L6M 160 / 172 / 188k for live-faithful / engine default / base-lot R; 10R-no-give-back L6M 155 / 135 / 150k), not 12k / 25k.)

## SIZER_S1 (S4a): section 1 - ER sizer pinned down (screen 2026-11-02 18:37Z)

Shadow only, no PASS claims. Base V13T_LIVE, lock none, SEQUENTIAL rounding (user answer from DS7 code); reference = the live binary ER(20) 5-min ladder (x1.5 if ER >= 0.30 else x0.5) as an explicit multiplier; sizer OFF is not a ranked cell (standing rule). Prereg SIZER_PREREG_DRAFT.md section 1 (hashed in DECISIONS.md 17:49Z). Code l2vast/ds3/code/zones3_new/sizer_s4a/ (copy of ZL-2's harness, untouched logic; s1_cells.py, s1_run.py, s1_pa.py, s1_plc.py); per-cell results out/zones3_new/sizer_s1_cells.csv (998 cells) and sizer_s1_pa9.csv; pool file /mnt/l2/l2vast/ds3_sizer/pool_inputs_s1.csv; ledger program SIZER_S1 (998 rows). Cut = 1 - maxDD(cell)/maxDD(live ladder), single path; PA band = Z3 V13T PA9 FINAL flip-5 (L6M .219 HOLD .205 MID .322 PRE .099 X' .182) because every cell changes the multiplier on a large share of signals. Sections 1.5 (per book x session, walk-forward chains), 1.7 and the regime-conditional ladder moved to Z2 (SIZER_S1B); 1.6 lock conventions: engine exposes only the rounding switch and the day-lock scaling is fixed by the user answer, so 1.6 collapses into the sequential headline.

**Tie-outs.** (a) the live ladder rebuilt as an explicit multiplier vector = the reference to 0.0 $; (b) the ladder from feat_signal er_5m_20 differs by +49 $/wk (the 0.03-4.8 % of rows where the parquet ER differs); (c) sizer off (reference only, not a cell): L6M cut +0.49, PRE +0.29, mean -5084 $/wk: the live ladder is a profit sizer that deepens the drawdown relative to off.

### 1. Plain sentences

* Of 998 section-1 cells, 106 keep the mean at or above the live ladder (ALL-window mean change >= 0); 75 of these also cut the L6M maxDD and 50 cut both L6M and PRE; only 9 of those do not worsen another window beyond the PA band (no-harm, single path).
* 10 cells beat the live ladder on L6M AND PRE with the carrying week dropped at mean >= live on the single path; the cells that beat it do so at a deeper maxDD in HOLD, MID or X' (table 3). After the PA9 + no-harm screen none keeps both drops above the band. No FLAG (MORNING_FLAGS.md rule): nothing survives the carrying-week drop in BOTH L6M and PRE with no-harm.
* BEST ER-based cell so far (LEAD, not RISK-KEEP): ER(20) 5-min rank with hysteresis, 3 tiers x0.5/x1/x1.5 (details table 4): PA9 cuts L6M +0.34 HOLD +0.21 MID -0.07 PRE +0.19 X' +0.08, min phase L6M +0.28 PRE +0.15, mean change +462 $/wk vs live; band rule and no-harm pass, but with the carrying episode dropped the L6M cut is -0.09 (ONE-EPISODE in L6M; PRE drop +0.27) and the 100-draw placebos (random multipliers with the same distribution, shuffled-day, AR(1)-matched) are NOT beaten on the cut (table 4).

### 2. Families (median single-path cut vs the live ladder)

| family | cells | median cut L6M | median cut PRE | share mean >= live | share cut L6M>0 and PRE>0 |
|--|--|--|--|--|--|
| 1.2 ER bar x lookback x mapping (714) | 714 | +0.19 | +0.12 | 0.11 | 0.64 |
| 1.3 signed ER (224) | 224 | +0.25 | +0.15 | 0.12 | 0.75 |
| 1.4 reaction speed (60) | 60 | +0.18 | +0.16 | 0.05 | 0.82 |

### 3. Top cells by drawdown (mean >= live), ranked by the mean of the L6M and PRE cuts (single path), with carrying-week drops

| rank | cell | cut L6M | HOLD | MID | PRE | X' | L6M drop | PRE drop | mean change $/wk (MDE) | no-harm (single path) |
|--|--|--|--|--|--|--|--|--|--|--|
| 1 | ('g14', 'er_5m_20', 'hyst', 'L3') | +0.36 | -0.04 | -0.10 | +0.20 | -0.10 | -0.08 | +0.27 | +453 (3454) | yes |
| 2 | ('g13', 'ers_30m_20', 1, 'L5', 'B') | +0.55 | +0.09 | -0.50 | -0.02 | -0.43 | +0.48 | -0.06 | +2083 (6901) | NO |
| 3 | ('g13', 'ers_30m_20', 1, 'LIN', 'B') | +0.55 | -0.17 | -0.70 | -0.01 | -0.27 | +0.24 | -0.06 | +1287 (5928) | NO |
| 4 | ('g13', 'ers_5m_20', 1, 'L5', 'A') | +0.38 | -0.01 | +0.20 | +0.15 | -0.07 | -0.05 | +0.12 | +843 (3251) | yes |
| 5 | ('g13', 'ers_30m_20', 1, 'SIG', 'B') | +0.53 | -0.15 | -0.67 | -0.02 | -0.20 | +0.21 | -0.07 | +2305 (6023) | NO |
| 6 | ('g12', 'er_30m_10', 'L5', 'D') | +0.33 | -0.41 | -1.17 | +0.16 | -0.68 | +0.10 | +0.13 | +300 (4988) | NO |
| 7 | ('g12', 'er_10m_14', 'L3', 'D') | +0.27 | -0.33 | -0.97 | +0.22 | -0.28 | -0.12 | +0.18 | +1003 (4116) | NO |
| 8 | ('g12', 'er_15m_10', 'SIG', 'D') | +0.35 | -0.43 | -1.23 | +0.13 | -0.53 | -0.05 | +0.09 | +478 (4672) | NO |
| 9 | ('g12', 'er_3m_100', 'L3', 'D') | +0.36 | -0.31 | -0.96 | +0.11 | -0.57 | +0.14 | +0.07 | +181 (4872) | NO |
| 10 | ('g13', 'ers_15m_20', 1, 'L3', 'A') | +0.41 | -0.29 | -0.82 | +0.04 | +0.07 | +0.43 | +0.00 | +521 (5232) | NO |
| 11 | ('g12', 'er_1m_100', 'LIN', 'D') | +0.23 | -0.35 | -0.69 | +0.20 | -0.80 | -0.29 | +0.16 | +683 (4577) | NO |
| 12 | ('g13', 'ers_15m_20', 1, 'SIG', 'D') | +0.34 | -0.28 | -0.87 | +0.08 | -0.88 | +0.11 | +0.04 | +83 (5047) | NO |
| 13 | ('g12', 'er_15m_10', 'L3', 'D') | +0.29 | -0.54 | -0.91 | +0.11 | -0.11 | -0.19 | +0.07 | +754 (4674) | NO |
| 14 | ('g12', 'er_2m_50', 'L3', 'A') | +0.21 | -0.05 | -0.13 | +0.19 | +0.21 | -0.28 | +0.27 | +695 (3424) | yes |
| 15 | ('g12', 'er_10m_10', 'SIG', 'D') | +0.24 | -0.50 | -0.90 | +0.16 | -0.90 | -0.15 | +0.12 | +291 (4623) | NO |
| 16 | ('g13', 'ers_30m_20', 1, 'L3', 'D') | +0.46 | -0.32 | -1.22 | -0.07 | -0.82 | +0.10 | -0.12 | +410 (5222) | NO |
| 17 | ('g13', 'ers_5m_20', 1, 'L5', 'D') | +0.15 | -0.27 | -0.43 | +0.23 | -0.31 | -0.30 | +0.20 | +1030 (3569) | NO |
| 18 | ('g12', 'er_10m_14', 'L5', 'D') | +0.26 | -0.36 | -0.85 | +0.10 | -0.37 | -0.03 | +0.06 | +288 (4080) | NO |
| 19 | ('g12', 'er_30m_10', 'LIN', 'B') | +0.16 | +0.16 | -0.25 | +0.19 | -0.35 | +0.26 | +0.16 | +1813 (5935) | NO |
| 20 | ('g12', 'er_1m_100', 'SIG', 'D') | +0.19 | -0.39 | -0.72 | +0.17 | -0.76 | -0.36 | +0.13 | +928 (4201) | NO |

### 4. PA9 of the 19 screen survivors (9 lock-reset phases vs the live ladder at the same phase)

| cell | PA L6M | HOLD | MID | PRE | X' | min phase L6M / PRE | drop L6M | drop PRE | mean $/wk | band rule | no-harm |
|--|--|--|--|--|--|--|--|--|--|--|--|
| ('g13', 'ers_15m_20', 1, 'SIG', 'D') | +0.45 | -0.16 | -2.18 | +0.03 | -0.65 | +0.34 / -0.10 | +0.07 | +0.01 | +65 |  | NO |
| ('g13', 'ers_15m_20', 1, 'L3', 'A') | +0.43 | -0.12 | -1.72 | +0.06 | +0.17 | +0.36 / -0.01 | +0.39 | +0.05 | +491 |  | NO |
| ('g12', 'er_30m_10', 'L5', 'D') | +0.42 | -0.29 | -2.71 | +0.15 | -0.50 | +0.33 / +0.12 | +0.06 | +0.13 | +312 | YES | NO |
| ('g12', 'er_3m_100', 'L3', 'D') | +0.40 | -0.19 | -2.34 | -0.04 | -0.39 | +0.36 / -0.30 | +0.09 | -0.06 | +15 |  | NO |
| ('g13', 'ers_5m_20', 1, 'L5', 'A') | +0.37 | +0.15 | -0.09 | +0.04 | +0.02 | +0.29 / -0.12 | -0.05 | +0.02 | +738 |  | yes |
| ('g14', 'er_5m_20', 'hyst', 'L3') | +0.34 | +0.21 | -0.07 | +0.19 | +0.08 | +0.28 / +0.15 | -0.09 | +0.27 | +462 | YES | yes |
| ('g12', 'er_30m_10', 'L3', 'D') | +0.25 | -0.09 | -2.05 | +0.13 | -0.63 | +0.15 / +0.07 | +0.02 | +0.11 | +581 | YES | NO |
| ('g13', 'ers_5m_20', 1, 'L3', 'A') | +0.24 | +0.17 | +0.08 | +0.06 | +0.14 | +0.18 / -0.03 | -0.24 | +0.06 | +1212 |  | yes |
| ('g12', 'er_2m_50', 'L3', 'A') | +0.22 | +0.08 | -0.55 | +0.16 | +0.27 | +0.17 / +0.11 | -0.30 | +0.26 | +645 | YES | NO |
| ('g12', 'er_1m_100', 'L5', 'B') | +0.22 | +0.20 | +0.08 | -0.15 | +0.16 | +0.06 / -0.34 | -0.37 | -0.03 | +2269 |  | NO |
| ('g12', 'er_30m_10', 'LIN', 'B') | +0.22 | +0.17 | -1.34 | +0.05 | -0.18 | +0.02 / -0.00 | +0.31 | +0.04 | +1747 |  | NO |
| ('g12', 'er_15m_20', 'LIVE', 'A') | +0.18 | +0.14 | -1.44 | -0.00 | -0.02 | +0.11 / -0.13 | +0.21 | -0.02 | +252 |  | NO |
| ('g13', 'ers_10m_20', 1, 'LIN', 'B') | +0.15 | -0.06 | -0.90 | +0.03 | -0.08 | +0.02 / -0.15 | +0.05 | +0.01 | +1308 |  | NO |
| ('g12', 'er_15m_20', 'LIN', 'B') | +0.15 | -0.02 | -1.65 | -0.07 | +0.03 | +0.03 / -0.35 | +0.41 | -0.09 | +2071 |  | NO |
| ('g12', 'er_1m_100', 'L3', 'A') | +0.14 | +0.12 | -0.26 | +0.12 | +0.20 | +0.10 / +0.07 | -0.27 | +0.20 | +918 |  | yes |
| ('g14', 'er_5m_14', 'min3', 'L3') | +0.13 | +0.11 | -0.70 | +0.06 | +0.08 | +0.03 / +0.03 | -0.51 | +0.05 | +750 |  | NO |
| ('g14', 'er_5m_20', 'ema3', 'L3') | +0.13 | +0.08 | -0.20 | -0.01 | +0.05 | +0.06 / -0.06 | -0.03 | -0.03 | +146 |  | yes |
| ('g12', 'er_2m_50', 'LIVE', 'A') | +0.10 | -0.06 | -0.42 | -0.06 | -0.19 | -0.13 / -0.14 | -0.17 | +0.02 | +369 |  | NO |
| ('g12', 'er_10m_30', 'LIN', 'B') | +0.07 | +0.03 | -1.41 | +0.08 | -0.04 | -0.04 / +0.01 | +0.27 | +0.06 | +2063 |  | NO |

**Hysteresis cell: placebos (100 draws each, phase 0, rank = share of placebo draws whose cut is BELOW the real cell, 0.95+ needed) and equal-risk**

| kind | rank cut L6M | HOLD | MID | PRE | X' | rank mean L6M | PRE |
|--|--|--|--|--|--|--|--|
| perm | 0.55 | 0.90 | 0.92 | 0.72 | 0.95 | 0.83 | 0.95 |
| dayshuf | 0.56 | 0.84 | 0.92 | 0.60 | 0.96 | 0.86 | 0.95 |
| ar1 | 0.57 | 0.82 | 0.93 | 0.66 | 0.96 | 0.92 | 0.98 |

Equal-risk (lot scale c so the cell's fitted maxDD equals the live ladder's fitted maxDD): L6M: c=1.45, mean 50586 vs live 36865 $/wk (+13722); PRE: c=1.05, mean 18794 vs live 17205 $/wk (+1590); X': c=0.90, mean 5241 vs live 4680 $/wk (+561).

**Lots distribution of the hysteresis cell**: share of signals at x0.5 36.8 %, x1 31.1 %, x1.5 32.1 % (live ladder: x0.5 56 %, x1.5 44 %); rank defined for 98.8 % of signals (x1.0 elsewhere).

**Definition (hysteresis cell)**: r = causal expanding per-book percentile rank of ER(20) on 5-min closes at the signal (strictly-below share of earlier signals of the book, min 100); per book in signal order the tier is kept unless r < 1/3 - 0.05 (tier 0, x0.5), r >= 2/3 + 0.05 (tier 2, x1.5) or 1/3 + 0.05 <= r < 2/3 - 0.05 (tier 1, x1.0); first signal: plain thresholds 1/3, 2/3. Lots then follow the live sequential rounding. Files: /mnt/l2/l2vast/ds3_sizer/mult_er_5m_20_hyst_L3_A.npy (multiplier per engine row).


## SIZER_S1B (Z2): per book x session, purged walk-forward, reaction speed, interactions, regime-conditional ER ladder (2026-11-02 ~19:20Z)
Prereg `l2vast/ds3/prereg/SIZER_S1B_prereg.md` sha256 c663c52c17541946f1d662e2708b9c32d6104e343b7cdc6be19eb092cfc6acea (in DECISIONS.md before scoring). Code `l2vast/ds3/code/zones3/s1b/` (s1b_lib.py, s1b_cells.py, s1b_run.py, s1b_pa.py, s1b_plc.py, s1b_an.py), data `/mnt/l2/l2vast/ds3_zones3_new/Z2_s1b/` (res_*.pkl, s1b_scored.csv, pa_table.csv, plc_*.pkl). Harness = ZL-2 sizer_harness on V13T_LIVE; **baseline = the live binary ER(20) 5-min ladder (ER >= 0.30 -> x1.5 else x0.5) passed as an explicit multiplier with lots_round = sequential** (user answer); the 'off' column is reference only and is not ranked. Baseline numbers (sequential, lock none): maxDD L6M 170.4k, HOLD 170.4k, MID 45.5k, PRE 160.7k, X' 72.8k; mean lots 3.19 (56% of signals at x0.5, 44% at x1.5). 616 cells scored (552 static per book x session, 2 walk-forward chains, 18 reaction-speed, 4 interaction, 40 regime-conditional). Ranking key = mean of the L6M and PRE maxDD cut vs the live ladder among cells whose mean change is >= 0 in L6M, HOLD and PRE ('same or better mean'); cells that cut maxDD by sizing down (mean lots 2.0-2.7 instead of 3.2) lose mean and are VOLUME. Ledger program SIZER_S1B; S4a ran 1.1-1.4 (rank-based) separately.
### Plain sentences
**1. No ER-based variant in my subsets beats the live ladder on L6M AND PRE with the carrying week dropped AND against its placebos, so nothing is flagged.** Of 616 cells, 94 cut maxDD in both L6M and PRE with the carrying-week-dropped cut positive in both windows and a mean change inside -MDE, but only 16 do so with a mean change >= 0 in L6M, HOLD and PRE; those 16 are dominated by small single-cell changes (PE London, KB Asia). The best clean one is **PE London, threshold 0.25, ladder x0.5 / x1.0 (no size-up)**: L6M cut +25.9% (carrying-week-dropped +5.1%), HOLD +23.2%, MID -3.0%, PRE +11.0% (dropped +11.0%), X' -11.4%; mean change +343 / +377 / -2,469 / +86 / +777 $/wk (L6M / HOLD / MID / PRE / X'); PA9 +25.9% L6M and +11.0% PRE, 9/9 phases, above the PA band (L6M .219, PRE .099); but **its placebos match it: L6M cut rank 0.77-0.80 against random multipliers with the same distribution, shuffled-day multipliers and AR(1) state paths (PRE 0.64-0.82); only the MEAN is better than the placebos (rank 0.03-0.07)** - i.e. less size-up in PE London is not a drawdown signal beyond what random down-sizing of the same size does. Label: LEAD-weak (VOLUME-like on the cut), not RISK-KEEP.
**2. Per book x session.** Share of the 23 variants per book with an L6M cut > 0: KB 76%, HM 43%, PE 40%, SM 20%, PB 11%, MV 10%; sessions with any same-or-better-mean variant: PE asia/london, KB asia/london/nypm, SM london, MV london; none for HM, PB (the table below lists the best same-or-better-mean variant for each of the 24 cells). The books that pay most from the live ladder are therefore those where almost every alternative loses mean (PB, MV); KB and PE are where a different ladder costs nothing.
**3. Purged walk-forward per (book, session) (6 and 12 months -> next month, last 2 label days dropped):** wf6 L6M cut +21.4% but HOLD -29.3%, MID -111%, PRE -5.5%, mean -9.0k/wk L6M; wf12 L6M +34.2%, HOLD -8.7%, MID -93%, PRE -13.5%, mean -4.3k L6M: the fitted tables do not carry out of sample; the live single ladder is better than any trailing-window per-cell choice on PRE/MID/HOLD.
**4. Reaction speed (absolute ER thresholds, ladder 0.5/1.5):** raw / EMA3 / EMA5 / max3 / min3 / hysteresis at 0.25, 0.30, 0.35: no variant improves L6M and PRE together with the mean intact: min3 at 0.30 cuts L6M 36% and PRE 9.5% but loses mean (mean lots 2.8; -2.5k HOLD, -3.5k PRE); EMA5 at 0.30 is +3.9% / +10.8% (L6M / PRE) with mean -271 / -639 (inside noise); raw at 0.25 has +4.6k/wk L6M mean but cuts nothing (-14%). The live raw ER at the last closed bar is not beaten by smoothing.
**5. Interactions:** D2 no-double-halving (zone rows: ER x1.0 instead of x0.5 on low ER): L6M +14.1%, PRE 0.0%, mean -0.8k/-0.6k/+0.3k (L6M/HOLD/PRE) - nothing; D3 sizer outside zone rows only: L6M +24.2%, HOLD +22.1%, PRE +3.5%, mean -0.9k/-1.2k/+0.8k, not two-window; D5/D6 (B02-quiet proxy): -6.6% / -32.1% L6M. A06 slot halving is not in the engine (OPEN).
**6. Regime-conditional ladder (addendum 2.2): the regime fits do not survive the carrying-week drop.** Vol-tag regimes (vol_tag_entry_day, 3-tier x0.5/x1/x1.5, thresholds per regime fitted on PRE + X'): L6M +38.0%, HOLD +34.2%, MID +22.5%, PRE +12.7%, X' -7.7% with mean >= 0 in every window (+673 / +2,244 / +2,184 / +381 / +2,689 $/wk) and PA9 L6M +37.5% / PRE +12.7% (9/9 phases), but the L6M cut with the carrying weeks dropped is -14.4%: the whole L6M gain is the carrying episode. B02-quiet proxy post-hoc (binary): L6M +37.9%, PRE +10.6%, mean +1.9k / +1.1k / +1.0k, carrying drop -14.9%: same. Uniform threshold 0.20 (binary, all regimes): L6M +31.4%, PRE +13.1%, mean +1.0k / +0.7k / +2.8k / +1.3k (L6M / HOLD / PRE / X'), but more size-up (64% of signals x1.5, mean lots 3.9), carrying drop -4.4%, X' maxDD -46%, MID rank 0.01 against placebos only: no. Walk-forward regime choices (6/12 m): wf6 vol-tercile R1 binary +51.9% L6M but PRE -4.7%, mean -1.8k L6M; wf12 R1/M3 +61.5% L6M, +15.5% PRE, but mean -2.1k / -5.2k (VOLUME: mean lots 2.7). No regime-conditional ladder is a RISK-KEEP; the order's 'a 0.30 threshold on a quiet day may not mean what it means on a wild one' is not supported at this sample (regime thresholds move between 0.15 and 0.50 month to month: the choice is unstable).
**7. Lots distributions** are in the tables (mean lots, share at low/high multiplier); the cells with the largest cuts (uni0.45-0.50, R2/M3 posthoc, R3/M3) have mean lots 2.0-2.2 against the live 3.19, i.e. they are smaller books, not better ladders. Worst single-day exposure of the winners was NOT computed here (ZL-2 harness table pending); the PE London x0.5/x1.0 cell lowers the maximum size-up of PE London only.
### Placebos (100 draws per kind, same engine and cost model; rank = share of draws with a cut >= the real cell's; small = real beats the placebo)
| cell | placebo kind | n | rank (share of draws with cut >= real) L6M / HOLD / MID / PRE / X' | rank on mean change L6M / PRE | label |
|---|---|---|---|---|---|
| A|PE|london|t0.25_0.5_1.0 | perm | 100 | 0.80 / 0.13 / 0.06 / 0.82 / 0.05 | 0.03 / 0.17 | no placebo beat |
| A|PE|london|t0.25_0.5_1.0 | dayshuf | 100 | 0.77 / 0.08 / 0.03 / 0.64 / 0.10 | 0.07 / 0.07 | no placebo beat |
| A|PE|london|t0.25_0.5_1.0 | ar1 | 100 | 0.78 / 0.12 / 0.04 / 0.74 / 0.16 | 0.03 / 0.09 | no placebo beat |
| E|UNI|M2|uni0.20 | perm | 100 | 0.53 / 0.09 / 0.01 / 0.28 / 0.18 | 0.26 / 0.08 | no placebo beat |
| E|UNI|M2|uni0.20 | dayshuf | 100 | 0.49 / 0.15 / 0.01 / 0.31 / 0.13 | 0.21 / 0.09 | no placebo beat |
| E|UNI|M2|uni0.20 | ar1 | 100 | 0.39 / 0.07 / 0.01 / 0.24 / 0.16 | 0.19 / 0.14 | no placebo beat |

### Tables (columns: cut % vs live ladder L6M / HOLD / MID / PRE / X'; mean change $/wk; carrying-week-drop cut L6M / PRE; mean lots; % lots at low / high multiplier; same-or-better mean; PA9 mean cut L6M / PRE where run)
### Family A - per book x session static: best same-or-better-mean variant per cell (ranked key: mean of L6M and PRE cut; mean change >= 0 in L6M, HOLD, PRE), all 24 cells

| key | maxDD cut vs live ladder % (L6M / HOLD / MID / PRE / X') | mean change $/wk (same windows) | carrying-week-drop cut L6M / PRE | mean lots (live 3.19) | % lots at low / high | same-or-better mean (L6M, HOLD, PRE) | PA9 mean cut L6M / PRE |
|---|---|---|---|---|---|---|---|
| A|KB|asia|t0.50_0.75_1.25 | +18.2 / +16.4 / -22.7 / +2.4 / -1.0 | +1865 / +598 / +726 / +92 / +159 | +2.9 / +2.4 | 3.25 | 48 / 39 | yes | +18.2 / +2.4 |
| A|KB|london|t0.25_0.5_1.0 | +6.6 / +6.6 / +15.5 / +4.8 / -2.3 | +234 / +28 / +1276 / +324 / -127 | +6.7 / +5.2 | 3.20 | 55 / 41 | yes | +6.6 / +4.8 |
| A|KB|nyam|t0.30_1.0_1.5 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 | +0 / +0 / +0 / +0 / +0 | +0.0 / +0.0 | 3.22 | 52 / 44 | yes | n/a |
| A|KB|nypm|t0.40_0.5_1.0 | +2.7 / +2.7 / +0.3 / +3.4 / +2.1 | +30 / +149 / -341 / +184 / +142 | -2.5 / +3.4 | 3.20 | 57 / 42 | yes | +2.7 / +3.4 |
| A|PE|asia|t0.40_1.0_1.5 | +20.7 / +20.7 / -14.4 / +5.5 / -17.8 | +1931 / +1802 / +558 / +1134 / -1353 | -45.1 / +5.5 | 3.33 | 49 / 42 | yes | +20.7 / +5.5 |
| A|PE|london|t0.20_0.5_1.0 | +34.5 / +10.0 / -3.0 / +7.1 / -11.4 | +1668 / +658 / -3202 / +164 / +871 | +7.0 / +7.1 | 3.12 | 55 / 40 | yes | +34.5 / +7.1 |
| A|PE|nyam|t0.30_1.0_1.5 | +0.0 / +0.0 / -15.9 / -4.2 / -2.4 | +0 / +441 / +702 / +172 / +734 | +0.0 / +12.2 | 3.31 | 53 / 44 | yes | n/a |
| A|PE|nypm|t0.20_0.5_1.5 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 | +0 / +0 / +0 / +0 / +0 | +0.0 / +0.0 | 3.22 | 56 / 44 | yes | n/a |
| SM asia | no variant has mean change >= 0 in L6M, HOLD and PRE (of 23) | | | | | | |
| A|SM|london|t0.20_0.5_1.0 | +6.6 / +6.6 / -10.2 / +0.2 / -3.7 | +278 / +348 / -360 / +192 / +146 | +3.3 / +0.2 | 3.20 | 55 / 42 | yes | +6.6 / +0.2 |
| A|SM|nyam|t0.20_0.5_1.5 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 | +0 / +0 / +0 / +0 / +0 | +0.0 / +0.0 | 3.22 | 56 / 44 | yes | n/a |
| A|SM|nypm|t0.20_0.75_1.25 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 | +0 / +0 / +0 / +0 / +0 | +0.0 / +0.0 | 3.22 | 56 / 44 | yes | n/a |
| A|HM|asia|t0.20_0.5_1.5 | +14.8 / +14.8 / -19.9 / -2.7 / -17.8 | +1777 / +923 / +70 / +648 / -113 | +7.4 / -2.5 | 3.30 | 54 / 46 | yes | n/a |
| A|HM|london|t0.20_0.5_1.5 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 | +0 / +0 / +0 / +0 / +0 | +0.0 / +0.0 | 3.22 | 56 / 44 | yes | n/a |
| A|HM|nyam|t0.30_1.0_1.5 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 | +0 / +0 / +0 / +0 / +0 | +0.0 / +0.0 | 3.22 | 54 / 44 | yes | n/a |
| A|HM|nypm|t0.20_1.0_1.5 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 | +0 / +0 / +0 / +0 / +0 | +0.0 / +0.0 | 3.22 | 56 / 44 | yes | n/a |
| A|MV|asia|t0.20_0.5_1.5 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 | +0 / +0 / +0 / +0 / +0 | +0.0 / +0.0 | 3.22 | 56 / 44 | yes | n/a |
| A|MV|london|t0.50_0.5_1.0 | +3.9 / +3.9 / -22.5 / +5.6 / -10.6 | +246 / +3 / -2929 / +175 / -224 | +3.3 / +10.0 | 3.15 | 59 / 40 | yes | +3.9 / +5.6 |
| A|MV|nyam|t0.30_1.0_1.5 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 | +0 / +0 / +0 / +0 / +0 | +0.0 / +0.0 | 3.22 | 51 / 44 | yes | n/a |
| A|MV|nypm|t0.20_0.5_1.5 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 | +0 / +0 / +0 / +0 / +0 | +0.0 / +0.0 | 3.22 | 56 / 44 | yes | n/a |
| A|PB|asia|t0.30_1.0_1.5 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 | +0 / +0 / +0 / +0 / +0 | +0.0 / +0.0 | 3.22 | 54 / 44 | yes | n/a |
| A|PB|london|t0.20_1.0_1.5 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 | +0 / +0 / +0 / +0 / +0 | +0.0 / +0.0 | 3.22 | 56 / 44 | yes | n/a |
| A|PB|nyam|t0.20_0.5_1.5 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 | +0 / +0 / +0 / +0 / +0 | +0.0 / +0.0 | 3.22 | 56 / 44 | yes | n/a |
| A|PB|nypm|t0.20_0.75_1.25 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 | +0 / +0 / +0 / +0 / +0 | +0.0 / +0.0 | 3.22 | 56 / 44 | yes | n/a |

### Top 15 cells overall with same-or-better mean (all families)

| key | maxDD cut vs live ladder % (L6M / HOLD / MID / PRE / X') | mean change $/wk (same windows) | carrying-week-drop cut L6M / PRE | mean lots (live 3.19) | % lots at low / high | same-or-better mean (L6M, HOLD, PRE) | PA9 mean cut L6M / PRE |
|---|---|---|---|---|---|---|---|
| E|R2|M3|honest | +38.0 / +34.2 / +22.5 / +12.7 / -7.7 | +673 / +2244 / +2184 / +381 / +2689 | -13.6 / +33.2 | 3.06 | 43 / 26 | yes | +37.5 / +12.7 |
| E|R3|M2|posthoc | +37.9 / +8.6 / -65.0 / +10.6 / -86.2 | +1891 / +1127 / -6115 / +963 / +1057 | -13.7 / +10.6 | 4.05 | 29 / 71 | yes | +37.2 / +10.6 |
| E|UNI|M2|uni0.20 | +31.4 / -2.9 / -15.1 / +13.1 / -46.5 | +993 / +753 / +1203 / +2870 / +1295 | -4.4 / +15.7 | 3.86 | 36 / 64 | yes | +31.4 / +13.1 |
| A|PE|london|t0.20_0.5_1.0 | +34.5 / +10.0 / -3.0 / +7.1 / -11.4 | +1668 / +658 / -3202 / +164 / +871 | +7.0 / +7.1 | 3.12 | 55 / 40 | yes | +34.5 / +7.1 |
| A|PE|london|t0.25_0.5_1.0 | +25.9 / +23.2 / -3.0 / +11.0 / -11.4 | +343 / +377 / -2469 / +86 / +777 | +5.1 / +11.0 | 3.10 | 55 / 40 | yes | +25.9 / +11.0 |
| A|PE|asia|t0.40_1.0_1.5 | +20.7 / +20.7 / -14.4 / +5.5 / -17.8 | +1931 / +1802 / +558 / +1134 / -1353 | -45.1 / +5.5 | 3.33 | 49 / 42 | yes | +20.7 / +5.5 |
| A|PE|asia|t0.35_1.0_1.5 | +22.7 / +22.4 / -20.1 / +0.4 / -22.2 | +1530 / +1702 / -652 / +2095 / -1056 | -41.5 / +0.4 | 3.38 | 49 / 43 | yes | +22.7 / +0.4 |
| A|KB|asia|t0.50_0.75_1.25 | +18.2 / +16.4 / -22.7 / +2.4 / -1.0 | +1865 / +598 / +726 / +92 / +159 | +2.9 / +2.4 | 3.25 | 48 / 39 | yes | +18.2 / +2.4 |
| A|KB|asia|t0.40_0.5_1.5 | +16.9 / +16.9 / -4.6 / +3.1 / +4.7 | +507 / +39 / +27 / +157 / -66 | -4.6 / +3.1 | 3.19 | 58 / 42 | yes | +16.9 / +3.1 |
| A|KB|asia|t0.50_1.0_1.5 | +17.5 / +17.3 / -21.9 / +2.0 / +0.6 | +1863 / +690 / +753 / +30 / +154 | +1.6 / +2.0 | 3.25 | 48 / 40 | yes | +17.5 / +2.0 |
| A|PE|asia|t0.25_1.0_1.5 | +16.9 / +16.9 / -39.1 / +2.4 / -35.4 | +2896 / +1665 / -2858 / +1552 / -871 | -38.5 / +2.4 | 3.46 | 49 / 45 | yes | +16.9 / +2.4 |
| A|KB|london|t0.25_0.5_1.0 | +6.6 / +6.6 / +15.5 / +4.8 / -2.3 | +234 / +28 / +1276 / +324 / -127 | +6.7 / +5.2 | 3.20 | 55 / 41 | yes | +6.6 / +4.8 |
| A|PE|asia|t0.30_1.0_1.5 | +10.9 / +10.9 / -24.8 / +0.4 / -21.7 | +2100 / +1424 / -502 / +2089 / -290 | -38.0 / +0.4 | 3.41 | 49 / 44 | yes | +10.9 / +0.4 |
| A|KB|asia|t0.40_0.75_1.25 | +7.9 / +7.9 / -22.7 / +2.8 / -1.8 | +539 / +6 / +8 / +161 / +197 | -3.4 / +2.8 | 3.26 | 48 / 39 | yes | +7.9 / +2.8 |
| A|MV|london|t0.50_0.5_1.0 | +3.9 / +3.9 / -22.5 / +5.6 / -10.6 | +246 / +3 / -2929 / +175 / -224 | +3.3 / +10.0 | 3.15 | 59 / 40 | yes | +3.9 / +5.6 |

### Family B - purged walk-forward per book x session (6 / 12 m)

| key | maxDD cut vs live ladder % (L6M / HOLD / MID / PRE / X') | mean change $/wk (same windows) | carrying-week-drop cut L6M / PRE | mean lots (live 3.19) | % lots at low / high | same-or-better mean (L6M, HOLD, PRE) | PA9 mean cut L6M / PRE |
|---|---|---|---|---|---|---|---|
| B|wf12 | +34.2 / -8.7 / -93.3 / -13.5 / +0.0 | -4269 / -3707 / -3293 / -3618 / +301 | +4.6 / -13.5 | 3.01 | 53 / 33 | within MDE | n/a |
| B|wf6 | +21.4 / -29.3 / -111.1 / -5.5 / +0.0 | -8965 / -7103 / -3882 / -985 / +433 | -23.1 / +3.8 | 3.04 | 54 / 33 | within MDE | n/a |

### Family C - reaction speed (absolute ER thresholds 0.25 / 0.30 / 0.35)

| key | maxDD cut vs live ladder % (L6M / HOLD / MID / PRE / X') | mean change $/wk (same windows) | carrying-week-drop cut L6M / PRE | mean lots (live 3.19) | % lots at low / high | same-or-better mean (L6M, HOLD, PRE) | PA9 mean cut L6M / PRE |
|---|---|---|---|---|---|---|---|
| C|raw|0.25 | -14.1 / -14.1 / +0.8 / -2.7 / -21.2 | +4552 / +3405 / +1512 / +136 / +2066 | -14.8 / +16.4 | 3.53 | 46 / 54 | yes | n/a |
| C|ema3|0.25 | -18.3 / -18.3 / +4.0 / +1.4 / -44.5 | +2449 / +1162 / -2784 / -984 / +637 | +8.8 / +1.4 | 3.47 | 48 / 52 | within MDE | n/a |
| C|ema5|0.25 | -9.0 / -9.0 / -15.9 / +10.6 / -43.0 | +14 / -1111 / -1719 / +2515 / -807 | +5.2 / +10.6 | 3.42 | 50 / 50 | within MDE | n/a |
| C|max3|0.25 | -20.1 / -20.1 / -30.0 / -10.1 / -56.6 | -3689 / +275 / +440 / +172 / +2285 | -23.0 / -10.1 | 3.87 | 35 / 65 | within MDE | n/a |
| C|min3|0.25 | +34.7 / +19.2 / -2.8 / -0.0 / -32.2 | +6230 / +1520 / -2248 / -685 / +13 | +20.4 / +20.2 | 3.11 | 60 / 40 | within MDE | n/a |
| C|hyst|0.25 | -13.4 / -13.4 / +17.2 / +10.4 / -93.7 | +2630 / +2658 / +3616 / +31 / -973 | -1.0 / +11.7 | 3.50 | 48 / 52 | yes | n/a |
| C|raw|0.35 | +19.2 / +19.2 / +8.8 / -16.4 / -5.8 | -4752 / -2871 / -3938 / -2240 / -621 | -1.1 / -3.4 | 2.93 | 65 / 35 | within MDE | n/a |
| C|ema3|0.35 | -2.5 / -2.5 / -31.4 / -5.6 / -18.8 | -6276 / -5333 / -8994 / -1803 / -1357 | +20.8 / +11.9 | 2.85 | 68 / 32 | within MDE | n/a |
| C|ema5|0.35 | +26.9 / +15.7 / -12.9 / +9.9 / -1.1 | -8052 / -5507 / -5148 / -1801 / -312 | -0.8 / +17.3 | 2.78 | 70 / 30 | within MDE | n/a |
| C|max3|0.35 | -1.6 / -1.6 / +10.9 / +0.5 / +13.1 | -1272 / -491 / -1452 / -682 / +557 | +26.4 / +2.5 | 3.25 | 55 / 45 | within MDE | n/a |
| C|min3|0.35 | +29.1 / +16.4 / -20.8 / +16.9 / -7.9 | -6932 / -5138 / -4689 / -2989 / -662 | +31.0 / +16.9 | 2.59 | 77 / 23 | within MDE | n/a |
| C|hyst|0.35 | +17.2 / +17.2 / -11.2 / +1.5 / +11.1 | -4637 / -2808 / -5252 / -2913 / -771 | +22.7 / +1.5 | 2.89 | 67 / 33 | within MDE | n/a |
| C|raw|0.30 | +0.0 / +0.0 / +0.0 / +0.0 / -1.0 | +367 / +316 / +0 / +82 / -310 | +0.0 / +0.0 | 3.22 | 56 / 44 | yes | n/a |
| C|ema3|0.30 | +2.6 / +2.6 / +1.3 / +5.5 / +5.2 | -880 / -1034 / -3117 / +26 / +955 | +15.0 / +8.9 | 3.15 | 58 / 42 | within MDE | n/a |
| C|ema5|0.30 | +3.9 / +3.9 / -36.2 / +10.8 / -19.5 | -271 / -1177 / -6905 / -639 / +20 | +17.7 / +10.8 | 3.08 | 60 / 40 | within MDE | n/a |
| C|max3|0.30 | -10.5 / -10.5 / +17.0 / -3.0 / -75.8 | +2629 / +2275 / +1239 / -493 / -1187 | -14.7 / -3.0 | 3.57 | 45 / 55 | within MDE | n/a |
| C|min3|0.30 | +36.2 / +8.9 / -34.6 / +9.5 / -25.5 | -84 / -2506 / -8933 / -3516 / -785 | +27.8 / +11.2 | 2.83 | 69 / 31 | within MDE | n/a |
| C|hyst|0.30 | -0.5 / -0.5 / +9.2 / +0.3 / -29.0 | +1383 / +1306 / -74 / -1187 / +448 | -6.7 / +9.6 | 3.18 | 57 / 43 | within MDE | n/a |

### Family D - interactions

| key | maxDD cut vs live ladder % (L6M / HOLD / MID / PRE / X') | mean change $/wk (same windows) | carrying-week-drop cut L6M / PRE | mean lots (live 3.19) | % lots at low / high | same-or-better mean (L6M, HOLD, PRE) | PA9 mean cut L6M / PRE |
|---|---|---|---|---|---|---|---|
| D|D2_nodoublehalve | +14.1 / +14.1 / +8.9 / +0.0 / -2.2 | -768 / -589 / -189 / +320 / -240 | -2.7 / +0.0 | 3.28 | 47 / 44 | within MDE | n/a |
| D|D6_quiet_no_sizedown | -32.1 / -32.1 / -40.8 / +0.3 / -27.5 | -1313 / +239 / -1634 / +794 / +175 | +0.1 / +10.9 | 3.44 | 39 / 44 | within MDE | n/a |
| D|D5_quiet_no_sizeup | -6.6 / -6.6 / +33.5 / +4.8 / -39.1 | -894 / +1201 / +627 / -1325 / -22 | +17.7 / +4.8 | 2.99 | 56 / 31 | within MDE | n/a |
| D|D3_outside_zone_only | +24.2 / +22.1 / -9.1 / +3.5 / -14.3 | -910 / -1200 / -1758 / +844 / -31 | -1.4 / +3.5 | 3.22 | 47 / 38 | within MDE | n/a |

### Family E - regime-conditional ladders and uniform controls

| key | maxDD cut vs live ladder % (L6M / HOLD / MID / PRE / X') | mean change $/wk (same windows) | carrying-week-drop cut L6M / PRE | mean lots (live 3.19) | % lots at low / high | same-or-better mean (L6M, HOLD, PRE) | PA9 mean cut L6M / PRE |
|---|---|---|---|---|---|---|---|
| E|R1|M2|wf6 | +51.9 / +40.5 / -36.1 / -4.7 / +0.0 | -1799 / -2323 / -1550 / -415 / +983 | +12.0 / +18.9 | 2.97 | 63 / 37 | within MDE | n/a |
| E|R1|M3|posthoc | +61.5 / +38.5 / +10.5 / +18.1 / +20.8 | -4034 / -2272 / +407 / -3403 / +142 | +29.5 / +21.4 | 2.73 | 53 / 16 | within MDE | +61.5 / +18.1 |
| E|R2|M2|honest | +39.0 / +4.1 / -63.9 / +1.6 / -88.0 | -4967 / -6421 / -9087 / -3700 / -4109 | -11.7 / +3.2 | 3.28 | 54 / 46 | within MDE | n/a |
| E|R2|M2|wf12 | +42.1 / +14.4 / -52.6 / +26.5 / +0.0 | -598 / -3081 / -3980 / -896 / -180 | -6.0 / +36.1 | 3.01 | 62 / 38 | within MDE | n/a |
| E|R2|M3|wf6 | +46.1 / +16.6 / -19.2 / +11.9 / +0.0 | -13886 / -8023 / -4815 / -3270 / +707 | +1.3 / +45.8 | 2.70 | 60 / 20 | within MDE | n/a |
| E|R3|M2|posthoc | +37.9 / +8.6 / -65.0 / +10.6 / -86.2 | +1891 / +1127 / -6115 / +963 / +1057 | -13.7 / +10.6 | 4.05 | 29 / 71 | yes | +37.2 / +10.6 |
| E|R3|M3|honest | +42.7 / +6.9 / -60.7 / +31.5 / +7.5 | -11331 / -9962 / -8506 / -3486 / -1422 | -4.9 / +31.5 | 2.53 | 62 / 11 | NO (volume) | n/a |
| E|R3|M3|wf12 | +38.0 / +14.7 / -60.4 / +10.3 / +0.0 | -4609 / -5506 / -1549 / -4256 / -1045 | +17.1 / +12.0 | 2.68 | 59 / 17 | within MDE | n/a |
| E|UNI|M2|uni0.25 | -14.1 / -14.1 / +0.8 / -2.7 / -21.2 | +4552 / +3405 / +1512 / +136 / +2066 | -14.8 / +16.4 | 3.53 | 46 / 54 | yes | n/a |
| E|UNI|M2|uni0.40 | +33.4 / +31.3 / +12.7 / +3.3 / +18.6 | -4922 / -2921 / -3692 / -2946 / -36 | +16.6 / +24.9 | 2.66 | 74 / 26 | within MDE | n/a |
| E|UNI|M3|uni0.15 | +29.6 / +10.9 / -46.4 / -4.1 / -16.2 | -3527 / -1616 / -2727 / -281 / +1332 | -17.9 / +18.1 | 3.45 | 26 / 35 | within MDE | n/a |
| E|UNI|M3|uni0.30 | +45.6 / +18.2 / -51.0 / +21.4 / +6.0 | -4178 / -3426 / -1075 / -4057 / +60 | +0.4 / +21.4 | 2.66 | 56 / 13 | within MDE | n/a |
| E|UNI|M3|uni0.45 | +58.2 / +21.7 / -44.2 / +48.0 / +4.5 | -11510 / -9754 / -7023 / -6539 / -1636 | +23.5 / +48.2 | 2.14 | 81 / 3 | within MDE | +58.2 / +48.0 |
| E|R1|M2|posthoc | +55.1 / +29.9 / -51.3 / +24.2 / -13.7 | -4884 / -44 / +7328 / -73 / -694 | +17.7 / +26.5 | 3.01 | 60 / 40 | within MDE | +55.1 / +24.2 |
| E|R1|M3|honest | +59.9 / +34.5 / -23.3 / +28.3 / -23.8 | -6700 / -5346 / -2391 / -1103 / -45 | +26.6 / +33.0 | 2.63 | 57 / 15 | within MDE | +59.9 / +28.3 |
| E|R1|M3|wf12 | +61.5 / +22.0 / -43.1 / +15.5 / +0.0 | -2148 / -2690 / -102 / -5237 / +520 | +29.5 / +18.7 | 2.70 | 58 / 18 | within MDE | +61.5 / +15.5 |
| E|R2|M2|wf6 | +54.4 / +12.5 / -26.6 / -1.9 / +0.0 | -738 / -3156 / -1811 / -656 / +452 | +16.5 / +21.4 | 3.03 | 61 / 39 | within MDE | n/a |
| E|R2|M3|posthoc | +54.6 / +25.8 / -43.3 / +50.4 / +10.9 | -14863 / -10949 / -8356 / -7209 / -1223 | +16.8 / +50.4 | 2.10 | 83 / 6 | NO (volume) | +54.6 / +50.4 |
| E|R3|M2|honest | +29.0 / -23.6 / -147.5 / +33.9 / -33.4 | -9756 / -9637 / -5989 / -487 / -952 | -30.0 / +33.9 | 2.72 | 72 / 28 | within MDE | n/a |
| E|R3|M2|wf12 | +31.8 / +2.6 / -88.6 / +14.3 / +0.0 | -942 / -4166 / -3593 / -1544 / -766 | +18.1 / +38.0 | 2.97 | 64 / 36 | within MDE | n/a |
| E|R3|M3|wf6 | +23.5 / +15.4 / -20.9 / +0.1 / +0.0 | -7930 / -3592 / +1856 / -2158 / -919 | +17.1 / +30.8 | 2.75 | 57 / 19 | within MDE | n/a |
| E|UNI|M2|uni0.20 | +31.4 / -2.9 / -15.1 / +13.1 / -46.5 | +993 / +753 / +1203 / +2870 / +1295 | -4.4 / +15.7 | 3.86 | 36 / 64 | yes | +31.4 / +13.1 |
| E|UNI|M2|uni0.35 | +19.2 / +19.2 / +8.8 / -16.4 / -5.8 | -4752 / -2871 / -3938 / -2240 / -621 | -1.1 / -3.4 | 2.93 | 65 / 35 | within MDE | n/a |
| E|UNI|M2|uni0.50 | +50.8 / +14.3 / -71.7 / +38.1 / -4.6 | -11256 / -8446 / -5523 / -6367 / +44 | +9.9 / +38.1 | 2.25 | 87 / 13 | within MDE | +50.8 / +38.1 |
| E|UNI|M3|uni0.25 | +36.5 / +14.1 / -23.0 / +13.5 / +17.3 | -1396 / -801 / +1729 / -2690 / +895 | -16.3 / +24.8 | 2.90 | 46 / 19 | within MDE | n/a |
| E|UNI|M3|uni0.40 | +57.7 / +30.1 / -21.6 / +39.2 / +16.8 | -11132 / -8387 / -6645 / -5255 / -702 | +22.7 / +45.2 | 2.27 | 74 / 5 | within MDE | +57.7 / +39.2 |
| E|R1|M2|honest | +53.3 / +18.1 / -81.7 / +30.6 / -30.7 | -8817 / -5281 / -1674 / -2149 / -1330 | +14.5 / +34.7 | 2.45 | 79 / 21 | within MDE | +53.3 / +30.6 |
| E|R1|M2|wf12 | +57.7 / +13.0 / -80.0 / -6.9 / +0.0 | -2147 / -3440 / -5137 / -3529 / +983 | +31.1 / +33.2 | 2.87 | 66 / 34 | within MDE | n/a |
| E|R1|M3|wf6 | +54.9 / +42.9 / +12.8 / +31.3 / +0.0 | -5666 / -4408 / +948 / -4384 / +313 | +17.4 / +42.3 | 2.68 | 59 / 18 | within MDE | +54.9 / +31.3 |
| E|R2|M2|posthoc | +42.1 / +20.7 / -58.7 / +25.8 / +3.9 | +4481 / +5925 / +1313 / -81 / +5386 | -6.0 / +25.8 | 3.13 | 59 / 41 | within MDE | n/a |
| E|R2|M3|honest | +38.0 / +34.2 / +22.5 / +12.7 / -7.7 | +673 / +2244 / +2184 / +381 / +2689 | -13.6 / +33.2 | 3.06 | 43 / 26 | yes | +37.5 / +12.7 |
| E|R2|M3|wf12 | +44.7 / +14.9 / -24.0 / +19.3 / +0.0 | -12868 / -9548 / -2244 / -2418 / -181 | +8.2 / +28.8 | 2.62 | 63 / 19 | within MDE | n/a |
| E|R3|M2|wf6 | +31.8 / +2.6 / -88.6 / -12.8 / +0.0 | +973 / -1939 / -3683 / +405 / -766 | +18.1 / +15.7 | 3.14 | 59 / 41 | within MDE | n/a |
| E|R3|M3|posthoc | +54.7 / +14.7 / -60.4 / +47.3 / +4.6 | -10771 / -10070 / -8135 / -5737 / -1726 | +17.1 / +50.8 | 2.23 | 76 / 5 | within MDE | +54.7 / +47.3 |
| E|UNI|M2|uni0.15 | +21.7 / -8.9 / -132.7 / +10.4 / -66.1 | -771 / -774 / -9712 / +834 / +1228 | -14.3 / +17.6 | 4.15 | 26 / 74 | within MDE | n/a |
| E|UNI|M2|uni0.30 | +0.0 / +0.0 / +0.0 / +0.0 / -1.0 | +367 / +316 / +0 / +82 / -310 | +0.0 / +0.0 | 3.22 | 56 / 44 | yes | n/a |
| E|UNI|M2|uni0.45 | +51.3 / +16.4 / -40.4 / +23.1 / +26.8 | -6336 / -4930 / -2479 / -5390 / +57 | +10.9 / +29.8 | 2.44 | 81 / 19 | within MDE | +51.3 / +23.1 |
| E|UNI|M3|uni0.20 | +39.8 / +15.3 / -5.7 / +6.6 / +10.3 | -2246 / -1373 / -1235 / -1562 / +435 | -7.4 / +12.0 | 3.16 | 36 / 26 | within MDE | n/a |
| E|UNI|M3|uni0.35 | +49.3 / +19.5 / -34.4 / +29.5 / +2.3 | -7711 / -5980 / -4685 / -4669 / -871 | +7.2 / +35.4 | 2.45 | 65 / 9 | within MDE | +49.3 / +29.5 |
| E|UNI|M3|uni0.50 | +62.8 / +26.5 / -45.3 / +49.2 / +27.0 | -16503 / -12442 / -8806 / -7504 / -1156 | +31.9 / +49.2 | 2.03 | 87 / 2 | NO (volume) | +62.8 / +49.2 |

(Z2 correction to sentence 2 above, same hour: cells with BOTH an L6M and a PRE cut > 0 and mean change >= 0 exist for KB asia/london/nypm (4/4/3 variants), PE asia (4) and london (2), SM london (4), MV london (3) and HM asia (1); none for PB or the other sessions. Cells where the ladder simply changes inside a (book, session) that the live ladder barely uses (PB/MV/HM/SM London-NY-PM rows with 23 'same mean' variants) are cells where the variant changes almost no lots.)

**Baseline reconciliation (Z2, 20:20Z):** my sequential baseline L6M maxDD 170.4k is the T-SIZER live-faithful base run_v13t_ts (sequential rounding AND day/week lock R scaled by max(1, multiplier), i.e. locks do not shrink when the multiplier is 0.5, as the user's DS7 answer says); BASE-4's 158.0k in SIZER_HOOK_TESTS.md is V13T_LIVE with the same explicit live-ladder lots_mult and lots_round='sequential' but the lock R scaled by the full multiplier (also below 1); single rounding gives 150.7k. Same L6M mean (36.7k/wk) in all three; reproduced in one process (direct run_v13t_live sequential 158.0 vs harness run in 'ts' mode 170.4; the ZL-2 harness default HARNESS_MODE='ts' was added at 18:12Z). All SIZER_S1B cells and their baseline use the 'ts' mode, so the cuts are comparable.


## SIZER_S2V (ZL-1): VOL SCALING UNDER THE LIVE ER LADDER (2026-11-02 ~19:15Z; prereg SIZER_S2V_prereg.md sha256 a82a7b26ef15839f68e38816f51da054749a4b4d2e518f94fa241e46ffd28343, logged in DECISIONS.md before scoring; ledger program SIZER_S2V, 99 cells appended; post-hoc, research only, ER ladder is the KEEP reference)
**Design.** m = clip(ER_ladder x f_vol, 0.25, 1.5); ER ladder = live binary (x1.5 if ER(20) 5m >= 0.30 else x0.5); f_vol in [0.5, 1.5] from one of 5 rank features (atr_ratio_5m ATR14/ATR100; rv_ratio_30m; range_so_far_ratio = overnight/day range ratio; dayrange_atrd = daily-ATR position; pk_ratio_20d Parkinson) with maps LIN / SIG / L3 and variants FULL / DOWN-only / UP-only in the vol-scaling direction INV (high vol = smaller) and the mirror DIR (high vol = larger); plus vol-target VT (lots proportional to median ATR / ATR, target multiples 0.75/1.0/1.25, clipped 0.5-1.5). 99 cells. Base V13T_LIVE, ZL-2 harness (ts mode: sequential rounding, same as the live ladder base, base reproduced exactly), lock none, phase 0. Stand-ins: ATR14/20-day median is not built (atr_ratio_5m used); no separate overnight range ratio (range_so_far_ratio). Cap 1.5 means a vol factor cannot push an ER x1.5 trade above 1.5.
**Ranking (prereg).** Eligible = mean >= ladder mean - MDE in L6M and PRE (80 of 99), ranked by mean of the L6M and PRE maxDD cuts. 27 cells exceed the PA9-band (flip 2%) in both L6M and PRE at phase 0; 10 of them are eligible and no-harm (PRE, MID, X' not worse than -band). All 29 finalist cells (top 5 eligible + the 27) got PA9.
| cell (feature / map / variant / direction) | cut L6M | cut PRE | L6M carry-week dropped | PRE dropped | HOLD | MID | X' | PA9 L6M / PRE | mean lots (live 3.01) | total $k vs ladder | placebo rank on cut L6M / PRE (perm, dayshuf, ar1) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| VT 0.75 DOWN (INV) | 38.6 | 27.3 | 48.6 | 24.0 | 38.6 | 53.9 | -17.9 (harm) | 43.5 / 24.1 | 2.31 | -822 | .32 .40 .38 / .46 .45 .33 |
| rv_ratio_30m SIG DOWN (DIR) | 30.2 | 35.2 | 10.4 | 32.8 | 30.2 | 18.4 | 20.4 | 35.5 / 16.1 | 2.35 | -961 | .25 .21 .26 / .24 .18 .30 |
| VT 0.75 FULL (INV) | 38.2 | 23.3 | 47.8 | 19.9 | 38.2 | 53.6 | -20.1 (harm) | 42.7 / 19.8 | 2.35 | -791 | .32 .39 .41 / .41 .33 .30 |
| dayrange_atrd SIG DOWN (DIR) | 17.7 | 43.6 | 18.0 | 41.1 | 17.7 | 54.7 | 13.9 | 38.9 / 17.9 | 2.35 | -994 | .29 .23 .29 / .52 .44 .49 |
| dayrange_atrd SIG FULL (DIR) | 17.6 | 43.1 | 17.9 | 40.6 | 17.6 | 53.4 | 8.0 | 37.6 / 17.4 | 2.37 | -934 | .27 .21 .30 / .52 .43 .45 |
Rank = share of placebo draws (100 each, same multiplier distribution) with a cut BELOW the real cell; 0.9+ would be evidence.
**Findings.**
1. NO vol-scaling cell is selective. Every top cell works by cutting lots (mean lots 2.3-2.4 vs 3.0 for the ladder, total $ down 0.8-1.0M of 3.5M, mean/wk down about 4-14k in L6M, 3-6k in PRE); random multipliers with the same distribution cut the L6M and PRE maxDD as much (placebo ranks 0.2-0.5 on L6M and PRE, i.e. the real cells are NOT better than random). They only beat random on HOLD/MID/X' (0.7-1.0), which are not the key windows.
2. The sign is wrong for volatility scaling: the no-harm winners are the DIR cells (SIZE DOWN when vol/range is LOW, up when high) which are de-risking in quiet markets (where the ladder's x0.5 and x1.5 are least profitable), not the classic INV vol scaling. INV cells with the full map (e.g. dayrange_atrd SIG FULL INV: cut L6M 46.3, PRE 13.9, mean +1.9k L6M, total -207k) cut L6M but fail X' (-48.8) and MID; INV DOWN-only cells cut L6M 30-47% with PRE 8-14% and X' -14 to -40 (harm).
3. Vol-target (VT, lots proportional to median ATR / ATR): VT 1.0 FULL cuts L6M 56.3% / PRE 18.3% / HOLD 55.8% / MID 61.8% at mean -2.2k/wk (L6M) and -4.9k/wk (PRE), total -474k, but X' -29.1 (harm, fails no-harm); VT 1.0 DOWN-only is no-harm (X' -14.3 = at the band edge): cut L6M 47.0, PRE 22.3, total -566k, PA9 43.4 / 15.7. VT 0.75 is the same with fewer lots. The vol-target idea is the only vol factor with both L6M and PRE cuts and MID/HOLD help, at the price of 14-16% of the ladder's total dollars and a harm in X' (2023-04..2024-01).
4. UP-only variants (vol factor can only add size, and cap 1.5 binds on ER x1.5): do nothing useful (L6M cut -20 to +20, PRE cut -3 to +4, total within +-100k).
5. Equal-risk (lot scale search to the ladder's fitted maxDD; extrapolated beyond lscale 2.0 for the L6M figures, treat as +-30%): PRE: all cells' mean at equal risk 15.5-17.1k vs ladder 17.8k (none better); L6M: 43-90k vs 37.6k (but lscale 1.4-2.7, outside the grid for the largest), HOLD 34-50k vs 31.8k (lscale 1.3-2.1). So a vol factor lets the book run more lots per unit of L6M/HOLD drawdown, never in PRE. Mixed, not a result.
6. Exposure (ZL-2 exposure_table): worst-day max net lots 25-29 vs 28 and stack risk $31-35k vs $33.6k for the ladder: the cells do NOT cut the worst-day stacked exposure (it is a multi-book stacking event at 1-lot books and PE 7); only mean lots fall. Lots per book x session (mean lots, ladder / VT0.75 DOWN / rv SIG DOWN DIR / dayrange SIG DOWN DIR): PE london 6.95 / 5.37 / 4.89 / 5.46; PE asia 6.62 / 5.04 / 4.45 / 4.13; PE nyam 6.50 / 3.68 / 6.21 / 6.06; HM asia 3.14 / 2.46 / 2.28 / 2.11; SM asia 3.96 / 3.19 / 2.96 / 2.74; KB asia 1.70 / 1.51 / 1.42 / 1.40; MV london 1.90 / 1.69 / 1.57 / 1.68; PB asia 1.69 / 1.17 / 1.28 / 1.12 (full table zl: ds3_zones3_new/sizer_s2v/lots_by_book_sess.csv, max lots 11 / 6 / 3 / 2 unchanged).
**Reading.** Vol scaling under the ER ladder does not give a selective drawdown cut: it gives the cut a lot reduction gives (placebo rank 0.2-0.5 on L6M and PRE), with the PRE equal-risk mean below the ladder's. The best honest nominee for 'vol scaling under it' is the vol-target DOWN-only cell VT 1.0 (and its 0.75 sibling), not a recommendation: harm in X', -566k total, not above random in L6M/PRE. Best-of-99 applies. Flag: see MORNING_FLAGS.md (formal prereg flag rule is met mechanically by the DIR cells; caveats stated there).
Files: ds3_zones3_new/sizer_s2v/ (s2v_all.csv, s2v_pa9.csv, plc_*.pkl, equal_risk.pkl, exposure.pkl, lots_by_book_sess.csv); code zones3/sizer_s2v/ (s2v.py, s2v_fin.py, s2v_rank.py, s2v_pa.py).

## SIZER_S3X (Z1) - sizer on exits on the T-SIZER base: tighter brackets / earlier cut on ER>=0.30 trades (2026-11-02 19:20Z)
Prereg SIZER_S3X_Z1_addendum2 (logged before the run). Base = run_v13t_ts (V13T_LIVE + live ER ladder, sequential rounding, lock R scaled only when mult > 1, per-book locks) + HALF layer: PA maxDD L3M 105k, L6M 170k, HOLD 170k, MID 45k, PRE 161k, X' 73k; mean L6M 38.5k, PRE 18.0k. Exact bracket kernel (run_v13t_ts({'bracket': ...})), lots not re-scaled, rows ER_5m_20 >= 0.30. Post-hoc, no PASS, Shadow only.

**Answer:** the anatomy points at ER>=0.30 PE trades, but a tighter bracket on them does not lower drawdown at the same mean. PE only (stop 35/45/50 x target 45/60): no cell is beyond the PA9 band in any window; the 45/60 and 50/60 cells are neutral (L6M +1..+3%, PRE +4..+5%, mean ~0) and the x/45 cells make PRE and MID much worse (PRE -92..-141%) and cost 7-9k/wk. All six live books (ER>=0.30 trades): stop 45 / 50 with target 45 cut L6M +39% / +42% (PA +40% / +42%, beyond the band) but PRE -53% / -58%, MID -199% / -158%, mean -9.4 / -8.9k/wk in L6M (MDE 16) and -10.2 / -9.0 in PRE (MDE 6.7, beyond MDE); with the carrying episode (W29-W39) dropped the L6M cut is +10% / +11%: ONE-EPISODE and it fails PRE. No cell cuts L6M AND PRE at mean >= base (the two cells with mean >= base, PE 45/60 and ALL 50/60, are inside the band). No winner flagged.

| scope ER>=0.30 | stop / target | maxDD cut L3M / L6M / HOLD / MID / PRE / X' (phase-avg) | beyond PA9 band | episode dropped L6M / PRE | mean d $k/wk (MDE) L6M / PRE | mean >= base? | worst-20 PRE b>a |
|---|---|---|---|---|---|---|---|
| PE | 35 / 45 | -1% (+2%) / -4% (-4%) / -4% (-5%) / -85% (-52%) / -141% (-141%) / -24% (-8%) | - | -13% / -141% | -9.0 (10.6) / -9.9 (6.7) | no | -823>-901 |
| PE | 35 / 60 | -6% (-5%) / +1% (+0%) / +1% (+0%) / +15% (+14%) / -13% (-13%) / -10% (-12%) | - | -4% / -13% | -0.7 (2.5) / -4.0 (4.2) | no | -823>-824 |
| PE | 45 / 45 | +8% (+10%) / -4% (-5%) / -4% (-5%) / -43% (-19%) / -92% (-79%) / -40% (-20%) | - | +6% / -92% | -7.3 (12.1) / -7.5 (5.6) | no | -823>-869 |
| PE | 45 / 60 | +3% (+1%) / +1% (+0%) / +1% (+0%) / +15% (+10%) / +5% (+4%) / +3% (-7%) | - | -4% / +8% | +0.3 (0.8) / -1.0 (2.4) | yes | -823>-824 |
| PE | 50 / 45 | +8% (+11%) / -1% (-1%) / -1% (-1%) / -65% (-25%) / -97% (-82%) / -59% (-32%) | - | +10% / -97% | -7.1 (12.1) / -7.3 (5.6) | no | -823>-863 |
| PE | 50 / 60 | +2% (+1%) / +3% (+3%) / +3% (+3%) / -7% (+6%) / +4% (+4%) / +6% (+3%) | - | +1% / +9% | +0.8 (0.5) / -1.1 (2.1) | no | -823>-818 |
| ALL | 35 / 45 | +7% (+14%) / +24% (+25%) / -14% (-24%) / -165% (-141%) / -141% (-139%) / -52% (-33%) | L6M | -5% / -141% | -14.3 (16.8) / -14.2 (8.2) | no | -823>-838 |
| ALL | 35 / 60 | +9% (+7%) / +21% (+18%) / +21% (+18%) / +21% (-10%) / -39% (-55%) / -21% (-29%) | - | +7% / -39% | -2.3 (8.1) / -6.8 (5.8) | no | -823>-834 |
| ALL | 45 / 45 | +20% (+25%) / +39% (+40%) / -15% (-27%) / -199% (-156%) / -53% (-43%) / -17% (-9%) | L3M, L6M | +10% / -53% | -9.4 (16.0) / -10.2 (6.7) | no | -823>-799 |
| ALL | 45 / 60 | +9% (+5%) / +11% (+10%) / +11% (+10%) / +26% (-7%) / +1% (+0%) / +4% (-6%) | - | -1% / +12% | +1.2 (3.5) / -1.6 (3.0) | no | -823>-835 |
| ALL | 50 / 45 | +21% (+27%) / +42% (+42%) / -5% (-15%) / -158% (-122%) / -58% (-43%) / -34% (-14%) | L3M, L6M | +11% / -58% | -8.9 (15.7) / -9.0 (6.8) | no | -823>-793 |
| ALL | 50 / 60 | +5% (+3%) / +9% (+8%) / +9% (+8%) / +1% (-1%) / +6% (+5%) / -5% (-10%) | - | +2% / +11% | +0.9 (3.2) / -0.9 (2.3) | yes | -823>-820 |

## SIZER_S1B follow-up (Z2, 2026-11-02 ~19:40Z): exposure, equal-risk, COMBINED KB+PE rule, family-wise null, PA9 CORRECTION

Nothing here is a PASS. Shadow only. B02 remains a PROXY (overnight-range ratio < 0.85 stand-in, not the user's B02). Harness mode is 'ts' (T-SIZER live-faithful sequential rounding + lock scaling mult>1); baseline = live binary .30 ladder in that mode.

### CORRECTION: earlier "PA9" figures for SIZER_S1B cells were single-phase
The V13T engine has lock none, so shifting the engine week key (Harness.run phase=) changes nothing (base_seq phases -4..+4 were identical bar two). Every earlier S1B "PA9 above band" statement in this file/MORNING therefore meant the single phase-0 result and is RELABELLED "single-phase". A genuine PA9 was recomputed by shifting the SCORING week key -4..+4 days on one engine run per cell (code s1b/s1b_pa2.py -> pa2.pkl). Genuine PA9 L6M cut (single in brackets): PE london t0.20 0.5/1.0 35.0 (34.5), t0.25 28.0 (25.9); KB asia t0.50 0.75/1.25 17.3 (18.2), t0.50 1.0/1.5 17.0 (17.5); KB london t0.25 0.5/1.0 6.3 (6.6); SM london 2-6; MV london 1.6-4.1. Results mostly unchanged for the clean cells, but weekly-phase sd of the PE london cut is 4.6 pts and MID/X' PA9 are negative for PE london (MID -1 to -3, X' -14 to -16).

### (2) Exposure and exact equal-risk (16 clean cells + live + C1/C2), expo_table.csv
- Worst single-day exposure is IDENTICAL for live and every cell: max net 28 lots (day 20240220), max stack risk $33,600 (first at 2023-06-23 07:20Z; ties on 20250618, 20250806, 20250623). Size-down cells do not touch the worst day, because it is set by unsized-down stacked signals. Max lots per signal 11 (PE) unchanged. Mean lots/signal: live 3.010; PE london 2.90-2.93; KB asia 3.05; KB london 2.98-3.09; MV london 2.94-2.98; SM london 2.95-2.99; HM asia 3.04; C1 2.961; C2 2.983.
- Lots distribution per book x session (cell KB asia t0.50 0.75/1.25 shown in exposure_table; full per-cell tables in expo.pkl): e.g. PE asia mean 6.6 / max 11, PE london 6.9 / 11, SM asia 4.0 / 6, HM asia 3.1 / 6, KB sessions 1.3-1.9 / 2-3, MV 1.3-1.9 / 2-3. Share of signals at x0.5: ~47-60% in the live ladder (binary lo=.5), x1.5 ~30-43%; C1 moves KB london to 45% x0.5 / 47% x1.0 and PE asia to 62% x1.0.
- Exact equal-risk mean (Harness.equal_risk, lscale fit over 0.6-2.0 grid, reference live fitted maxDD at lscale 1; L6M reference mean 35,875, PRE 15,502). Cell mean at equal risk minus reference, L6M / PRE: PE london t0.20: +11,661 / +3,096 (lscale 1.20, R2 of maxDD fit only 0.86, so noisy); PE london t0.25: +3,286 / +3,434 (R2 0.88); KB asia t0.50: -3,196 / +2,462 and -3,900 / +2,515; KB london (4 cells): -7,919 to -8,854 / +2,297 to +3,061; MV london: -6,366 to -7,000 / +3,016 to +3,347; SM london: -6,351 to -7,431 / +2,352 to +2,409; HM asia: -8,515 / +2,681; C1: +970 / +10,689 (lscale 1.04 / 1.27); C2: +2,645 / +10,094. So after paying for the risk cut in L6M the KB/MV/SM/HM cells LOSE 3-9k mean (they cut by paying mean, i.e. risk-keep style, not free); only PE london (and combos containing it) gain, and those depend on a noisy linear fit (R2 .86-.88). PRE gains are positive for all but PRE is a short window with a thin MDE.

### (3) COMBINED per-book rule (KB asia/london/nypm + PE asia/london; everything else live ladder)
- C1 = PE london t0.25 0.5/1.0, PE asia t0.40 1.0/1.5, KB asia t0.50 0.75/1.25, KB london t0.25 0.5/1.0, KB nypm t0.40 0.5/1.0. C2 = C1 with PE london t0.20.
- Point cuts vs live (L6M / HOLD / MID / PRE / X'): C1 +29.8 / +7.6 / -62.3 / +19.3 / -25.7; C2 +30.8 / +4.6 / -62.3 / +16.3 / -25.7. Genuine PA9: C1 28.4 / 10.5 / -22.7 / 17.9 / -25.3; C2 28.4 / 7.5 / -24.9 / 14.8 / -27.0 (phase sd L6M 13). Carrying-week-drop cut: L6M -30.3 (C1) and -31.1 (C2), PRE +13.3 / +10.1, X' -4.6 / -4.2. Mean vs live: L6M -1,593 (C1; MDE 11,735), PRE +3,065, MID -4,046. The L6M cut is carried by the single carrying week (drops to -30), MID and X' get materially worse (X' -26% = more drawdown than live in the pre-period). Not a ***FLAG***: fails the "L6M and PRE with carrying week dropped" condition (L6M drop negative) and fails no-harm on MID/X'.
- Placebos for C1, 100 draws each (rank = share of placebo draws with a smaller cut than the real combo; high = real beats chance): L6M cut 0.26 (random multipliers same distribution within book x session), 0.13 (shuffled-day multiplier sequence), 0.21 (AR(1)-matched). PRE 0.23 / 0.43 / 0.45. So a random re-assignment of the same multipliers produces equal or larger L6M and PRE cuts in 55-87% of draws: C1 is NOT distinguishable from size-down noise. Mean ranks 0.93-0.99 (the combo loses less mean than random, mild).
- Family-wise null priced for "best 16 of 616" (reduced to the 115 KB/PE cells that compose the combined rule): each null world permutes the ER feature within book x session x side (shuffled multiplier assignment; it keeps the marginals and removes any signal), reruns all 115 KB/PE cells, applies the same clean test (mean >= 0 on L6M/HOLD/PRE, cut > 0 L6M and PRE, carrying-drop > 0 both), picks the best per (book, session) and scores the combined rule. Worlds completed at time of writing: 10 (target >=100 requested; engine throughput ~15 worlds/h with 3 workers, so this is below target and will be updated by an appended line when more finish). Result on 10 worlds: mean clean cells per null world 5.5 (real 8 among the same 115 cells); P(n_clean >= 8) = 0.20; null best single-cell score median 24.0, p90 27.9 vs real best 20.8: P(null best >= real) = 0.60; null combined-rule L6M cut median 37.0, p90 55.9 vs real 29.8: P(null L6M >= real) = 0.60; P(both L6M and PRE >= real) = 0.30. The real result sits inside the null: the 8 clean KB/PE cells and the combined rule are what shuffled sizing produces. Limitation: 10 worlds cannot support a p-value finer than ~0.1; the direction is clear.
- Verdict: LEAD-weak at best for PE london; the combined KB+PE rule is NOT supported (placebo ranks <= 0.45, carrying-week dependent, MID/X' harm, null-typical). The ER sizer stays KEEP; the 'off' reference unchanged.

Files: s1b/s1b_expo.py, s1b_pa2.py, s1b_plc_comb.py, s1b_null.py, s1b_null_an.py; data /mnt/l2/l2vast/ds3_zones3_new/Z2_s1b/{expo.pkl,expo_table.csv,pa2.pkl,plccomb_C1.pkl,null_*.pkl}.


# S4b SECTION 2 (T-SIZER): other state measures as sizers + sizing of the resting 30% add  (written 19:50Z 2026-11-02, first table)
Prereg SIZER_PREREG_DRAFT.md (hashed in DECISIONS.md 17:49Z); add-sizing prereg l2vast/ds3/prereg/SIZER_ADD_S4B_prereg.md sha256 3dd688f209d22d001192dbc3ccd0a1af0deb10721ef12d5a34287b4856260afc (logged before any add statistic). Base = the T-SIZER TS base (run_v13t_ts: V13T_LIVE + live ER ladder, sequential rounding, lock R scaled only when mult > 1, lock none); reference = the live ER ladder (every cut is vs it). USER KEEP DIRECTIVE: the ER sizer is kept; the other features are scored as MODIFIERS (ON TOP of the live ladder, cap 0.25..2.0, or as GATES on its x1.5 / x0.5) and, for completeness, ALONE in its place. Harness: copy of ZL-2's sizer_harness (zones3/s4b/sizer_harness_s2.py, ts mode). Screen = single path (phase 0), then PA9 + 3 placebos x 100 for the best of the family.
## 2.0 Scope
76 features: the 65 non-ER features of ranks_book.parquet + 11 order-flow/confirmation features built here (feat_signal_flow.parquet, ranks_flow.parquet: pulled support 5/10 s and rate, pulled ahead 5/10 s, iceberg with / against the trade (30 s), microprice deviation and 10-s drift, confirmation counts 5/15 min; causal at the signal second, ranks per book as the other ranks). Cells: 76 features x 2 directions x 5 mappings (U3, D3, L3, LIN, SIG; lo/hi pair A = 0.5/1.5) x (alone, on top) = 1,520 cells + 608 gate cells (GU1/GU2: the x1.5 only when the feature rank >= 1/3 or 2/3, GD: the x0.5 cancelled when rank >= 2/3, GUD both) = 2,128 cells on the TS base. NOT scored from the prereg list: the weekday cells and the vol-target cells (definition missing in the draft); the ES-based features are NaN before 2023-08 (multiplier 1 there). Ledger: program SIZER_S2 (2,128 cells), SIZER_ADD (26).
## 2.1 Plain sentences
* **No second feature improves the live ER ladder at the same-or-better mean: of 2,128 cells 404 keep the mean (L6M and HOLD mean change >= 0, PRE >= -0.5 MDE), 59 of those are also no-harm, and 0 pass the V13T PA9 flip-5 band (L6M .219 and PRE .099 or X' .182) together with mean and no-harm.** The band is passed by 757 cells, all of them by lowering lots (they lose 1-20k/wk of mean: VOLUME).
* Best cell that keeps the mean and is no-harm: bars_since_flip_5m (TOP:D3, direction +1): size the live ladder down (x0.5) when the number of 5-min bars since the last EMA20 flip is in the lowest third of the book's history; PA9 cuts L6M +17.9% / HOLD +17.9% / MID -7.1% / PRE +2.4% / X' +22.5%, mean +1.3k/wk L6M; fails the band (L6M .219; PRE .024 < .099), and the placebos do not separate it: cut ranks (high = real beats placebo) perm / day-shuffled / AR(1): L6M 0.20 / 0.18 / 0.22, PRE 0.37 / 0.31 / 0.27, X' 0.98 / 0.99 / 0.97 (only X' beats chance; the mean beats the placebos, 0.95-0.99). Label: NOT A LEAD.
* The largest cuts in the table are volume cells, e.g. rst1_dir_s TOP:L3: L6M +43% PRE +45% with mean -18.7k/wk and mean lots 1.83 against about 3.2 (a degenerate +-1 regime feature halving a third of the signals).
* GATES (a second feature cancelling the ER x0.5 or limiting its x1.5): 608 cells, none beyond the band at the same mean; the best by S is dist_prior_close_atrd_s (GATE:GD).
## 2.2 Top 12 by S = mean(cut PRE, cut X') among cells that keep the mean and are no-harm
| feature | d | map | cut L6M / HOLD / MID / PRE / X' | mean d L6M / HOLD / PRE $k/wk | mean lots | S |
|---|---|---|---|---|---|---|
| bars_since_flip_5m | +1 | TOP:D3 | +18% / +18% / -7% / +2% / +22% | +1.3 / +0.2 / -0.7 | 2.94 | +0.124 |
| dist_prior_close_atrd_s | +1 | GATE:GD | +7% / +7% / -23% / +0% / +7% | +2.8 / +2.1 / +0.7 | 3.35 | +0.035 |
| zone_set8_ahead_atr | -1 | GATE:GD | +2% / +2% / -6% / +0% / +5% | +0.6 / +0.5 / +1.3 | 3.30 | +0.027 |
| pos_in_day_range_s | +1 | GATE:GD | +11% / +11% / -16% / +5% / -2% | +2.6 / +1.4 / +0.4 | 3.39 | +0.011 |
| big2_net30_s | +1 | TOP:U3 | -1% / -1% / -0% / -1% / +4% | +0.2 / +0.1 / +0.2 | 3.25 | +0.011 |
| slope_atr_5m_20 | +1 | GATE:GD | +4% / +4% / -12% / -1% / +2% | +1.6 / +0.7 / +0.1 | 3.29 | +0.008 |
| pulled_ahd10 | +1 | GATE:GD | +31% / +29% / -25% / +2% / -1% | +1.6 / +2.4 / +0.6 | 3.40 | +0.005 |
| zone_set8_ahead_atr | -1 | TOP:U3 | +4% / +4% / -7% / -1% / +1% | +1.4 / +0.9 / +0.7 | 3.30 | +0.004 |
| rst10_dir_s | +1 | TOP:U3 | +0% / +0% / +0% / +0% / +0% | +0.0 / +0.0 / +0.0 | 3.22 | +0.000 |
| rst5_dir_s | -1 | TOP:D3 | +0% / +0% / +0% / +0% / +0% | +0.0 / +0.0 / +0.0 | 3.22 | +0.000 |
| rst10_dir_s | -1 | TOP:D3 | +0% / +0% / +0% / +0% / +0% | +0.0 / +0.0 / +0.0 | 3.22 | +0.000 |
| rst1_dir_s | -1 | GATE:GU1 | +0% / +0% / +0% / +0% / +0% | +0.0 / +0.0 / +0.0 | 3.22 | +0.000 |
## 2.3 Largest drawdown cuts ignoring the mean (volume effects): no-harm cells with L6M > 30% and PRE > 20%
| feature | d | map | cut L6M / HOLD / MID / PRE / X' | mean d L6M / HOLD / PRE $k/wk | mean lots | S |
|---|---|---|---|---|---|---|
| rst1_dir_s | +1 | TOP:D3 | +43% / +43% / +38% / +45% / +32% | -18.7 / -15.0 / -8.8 | 1.83 | +0.384 |
| regime_with_5m | +1 | TOP:D3 | +43% / +43% / +38% / +45% / +32% | -18.7 / -15.0 / -8.8 | 1.83 | +0.384 |
| rst1_dir_s | +1 | TOP:L3 | +43% / +43% / +38% / +45% / +32% | -18.7 / -15.0 / -8.8 | 1.83 | +0.384 |
| regime_with_5m | +1 | TOP:L3 | +43% / +43% / +38% / +45% / +32% | -18.7 / -15.0 / -8.8 | 1.83 | +0.384 |
| big2_net30_s | +1 | TOP:D3 | +42% / +42% / +44% / +43% / +32% | -17.8 / -14.7 / -9.0 | 1.87 | +0.372 |
| big2_net30_s | +1 | TOP:L3 | +42% / +42% / +44% / +41% / +32% | -17.6 / -14.7 / -9.1 | 1.90 | +0.365 |
| rst5_dir_s | +1 | TOP:L3 | +36% / +36% / +39% / +40% / +32% | -16.9 / -14.2 / -8.1 | 1.92 | +0.360 |
| rst5_dir_s | +1 | TOP:D3 | +36% / +36% / +39% / +40% / +32% | -16.9 / -14.2 / -8.1 | 1.92 | +0.360 |
| rst10_dir_s | +1 | TOP:L3 | +40% / +40% / +35% / +40% / +32% | -17.1 / -14.5 / -7.9 | 1.92 | +0.359 |
| rst10_dir_s | +1 | TOP:D3 | +40% / +40% / +35% / +40% / +32% | -17.1 / -14.5 / -7.9 | 1.92 | +0.359 |
## 2.4 Sizing of the resting 30% add (addendum 2 item 1; hook run_v13t_ts add_mult / add_only_if; 25 cells + bound, all vs the TS base)
Plain sentences: the add leg is the stack's main drawdown source: switching it OFF (bound) cuts maxDD L6M +66% / HOLD +45% / PRE +23% / X' +24% but costs -838k over the history (-8.4k/wk L6M): the add earns about what it risks. **No add-sizing rule cuts the drawdown at the same-or-better mean in all windows:** every 'add only when' filter (ER, large print with the trade, delta with the trade, own support not pulled, iceberg with the trade) is a partial add-off (mean -5 to -8.6k/wk, maxDD cuts as the bound, X' flat); every x2 rule (tape-confirmed or an ER ladder on the add) raises the mean (+0.1 to +7.4k/wk L6M) but deepens PRE and/or X' maxDD (x2 if ER >= .30 else x0.5: PRE -28%, X' -41%; x2 if own support not pulled <= 1/3: X' -46%); the combined ER >= .30 and tape cells are the same. Only 'add only if ER >= 0.40' gives cuts in L6M / HOLD / MID / PRE / X' (+29 / +29 / +55 / +5 / +18%) but at mean -4.6k/wk L6M (-278k total): a volume effect (add off for most signals). Exposure sizing (open same-side position) is not exposed by the hook: not scored. The add fill rate is 88% of taken signals and does not move (the dip-3 trigger precedes the hook). Table:
| cell | cut L6M / HOLD / MID / PRE / X' | mean d L6M / HOLD / PRE $k/wk | total P&L change $k | add fills / taken | add lots base->cell | cancelled n / lots | add-leg P&L base->cell | cancelled add P&L |
|---|---|---|---|---|---|---|---|---|
| A_only_er>=0.15 | +8% / +8% / +31% / -6% / +1% | -1.1 / -0.2 / -0.5 | -40 | 18505 of 21024 (88%) | 25915 -> 20479 | 5375 / 5436 | +873k -> +765k | +95k |
| A_only_er>=0.20 | +12% / +12% / +47% / -4% / -0% | -1.5 / -0.0 / -0.9 | -51 | 18548 of 21070 (88%) | 25958 -> 18605 | 7279 / 7353 | +869k -> +809k | +38k |
| A_only_er>=0.30 | +11% / +11% / +55% / -7% / +1% | -0.5 / +0.1 / -0.9 | -27 | 18662 of 21194 (88%) | 26094 -> 14759 | 11203 / 11335 | +888k -> +725k | +154k |
| A_only_er>=0.40 | +29% / +29% / +55% / +5% / +18% | -4.6 / -2.5 / -2.1 | -278 | 18920 of 21462 (88%) | 26406 -> 8739 | 14519 / 17667 | +889k -> +628k | +237k |
| A_ladder_x2_hi_x0.5_lo | -17% / -17% / -73% / -28% / -41% | +7.4 / +4.3 / +4.5 | +715 | 17505 of 19955 (88%) | 24617 -> 36476 | 0 / 0 | +858k -> +1490k | +0k |
| A_only_hi_x1.5 | +4% / +4% / +33% / -6% / -29% | +2.7 / +2.3 / +1.2 | +287 | 18369 of 20880 (88%) | 25711 -> 19927 | 11003 / 11130 | +873k -> +965k | +157k |
| B_x2_if_T1_25 | +0% / +0% / +7% / -1% / -3% | +0.7 / +0.6 / -0.1 | +28 | 18386 of 20898 (88%) | 25794 -> 26329 | 0 / 0 | +863k -> +872k | +0k |
| B_only_if_T1_25 | +65% / +47% / +24% / +23% / +26% | -8.4 / -7.2 / -5.1 | -840 | 19164 of 21724 (88%) | 26695 -> 1146 | 18234 / 25549 | +871k -> -15k | +878k |
| B_x2_if_T1_50 | +3% / +3% / +7% / -0% / +1% | +0.5 / +0.4 / +0.0 | +28 | 18392 of 20903 (88%) | 25800 -> 26028 | 0 / 0 | +860k -> +852k | +0k |
| B_only_if_T1_50 | +67% / +47% / +22% / +23% / +25% | -8.3 / -7.1 / -5.0 | -825 | 19170 of 21729 (88%) | 26702 -> 454 | 18813 / 26248 | +870k -> -17k | +878k |
| B_x2_if_T2a_d2/3 | -18% / -18% / +18% / -12% / -19% | -0.3 / +0.2 / +1.3 | +227 | 18150 of 20646 (88%) | 25473 -> 29104 | 0 / 0 | +859k -> +1064k | +0k |
| B_only_if_T2a_d2/3 | +50% / +50% / +37% / +7% / +14% | -6.8 / -5.7 / -3.6 | -588 | 19062 of 21611 (88%) | 26569 -> 6974 | 13741 / 19595 | +897k -> +234k | +671k |
| B_x2_if_T2b_d1/2 | -16% / -16% / -7% / -29% / -11% | -1.0 / -0.0 / +2.0 | +254 | 17978 of 20462 (88%) | 25247 -> 31802 | 0 / 0 | +907k -> +1220k | +0k |
| B_only_if_T2b_d1/2 | +39% / +39% / +9% / -4% / -2% | -7.5 / -6.3 / -3.8 | -630 | 18900 of 21443 (88%) | 26388 -> 11765 | 10245 / 14623 | +895k -> +246k | +676k |
| B_x2_if_T3a_ps1/3 | +5% / -7% / -48% / +1% / -45% | +4.3 / +3.2 / +1.9 | +427 | 18108 of 20600 (88%) | 25407 -> 30221 | 0 / 0 | +852k -> +1229k | +0k |
| B_only_if_T3a_ps1/3 | +63% / +33% / +7% / +23% / -35% | -5.2 / -4.4 / -4.2 | -581 | 19026 of 21570 (88%) | 26509 -> 7182 | 14311 / 19327 | +891k -> +428k | +408k |
| B_x2_if_T3b_ps1/2 | -34% / -34% / -26% / -10% / -69% | +5.7 / +5.5 / +0.8 | +454 | 17869 of 20342 (88%) | 25076 -> 32970 | 0 / 0 | +817k -> +1329k | +0k |
| B_only_if_T3b_ps1/2 | +61% / +26% / -17% / +16% / -22% | +1.0 / -1.3 / -3.7 | -367 | 18866 of 21404 (88%) | 26332 -> 12124 | 10841 / 14208 | +864k -> +627k | +192k |
| B_x2_if_T4_ice2/3 | +7% / +7% / -2% / -6% / -4% | -0.6 / +1.0 / +2.4 | +274 | 18224 of 20729 (88%) | 25578 -> 28645 | 0 / 0 | +871k -> +1058k | +0k |
| B_only_if_T4_ice2/3 | +62% / +42% / +20% / +26% / +19% | -8.6 / -6.3 / -2.7 | -647 | 19043 of 21595 (88%) | 26563 -> 6613 | 13607 / 19950 | +879k -> +236k | +650k |
| C_er>=.30_x2_if_T1_25 | +13% / +13% / +62% / -8% / -14% | +0.0 / +0.6 / -0.9 | -2 | 18651 of 21183 (88%) | 26080 -> 15205 | 11196 / 11328 | +885k -> +727k | +153k |
| C_er>=.30_x2_if_T2a_d2/3 | +3% / +3% / +29% / -17% / -29% | +0.1 / +0.9 / +0.8 | +241 | 18421 of 20942 (88%) | 25789 -> 17606 | 11032 / 11164 | +879k -> +944k | +150k |
| C_er>=.30_x2_if_T3a_ps1/3 | +18% / +18% / +21% / -22% / -17% | +4.6 / +4.4 / -0.2 | +333 | 18444 of 20960 (88%) | 25822 -> 18619 | 11053 / 11180 | +887k -> +1004k | +156k |
| D_vol_off_if_atr_rk>=2/3 | +2% / +2% / -5% / -13% / -5% | -1.3 / -1.2 / -2.9 | -275 | 18505 of 21018 (88%) | 25924 -> 19926 | 4957 / 5998 | +851k -> +527k | +309k |
| D_vol_x0.5/x1.5 | -15% / -15% / -21% / -1% / -14% | +2.8 / +0.9 / +0.2 | +120 | 18283 of 20782 (88%) | 25620 -> 28178 | 0 / 0 | +895k -> +955k | +0k |
| BOUND_add_off | +66% / +45% / +20% / +23% / +24% | -8.4 / -7.3 / -4.8 | -838 | 19174 of 21733 (88%) | 26708 -> 0 | 19174 / 26708 | +876k -> -13k | +876k |
## 2.5 Files
pool_inputs_s2.csv for Z3: /mnt/l2/l2vast/ds3_sizer/pool_inputs_s2.csv (2,128 cells; equal-risk cuts by the linear lot-scale approximation, p1_exp = 7-volume-level x 10-draw permutation calibration); cells /mnt/l2/l2vast/ds3_zones3_new/sizer_s2ts/ (res.pkl, res_gate.pkl, table.pkl), add cells /mnt/l2/l2vast/ds3_zones3_new/sizer_add/res.pkl; code l2vast/ds3/code/zones3/s4b/ (sizer_s2.py, sizer_s2g.py, sizer_s2_an.py, sizer_s2_pool.py, sizer_s2_top.py, addm.py, sizer_s2_doc.py); features l2vast/ds3/code/d7base/build_sizer_feats_flow.py.

## SIZER_S3X (Z1) - LOT-SCALED TH-L2 loss cut on top of the live ER ladder (2026-11-02 19:56Z)
Prereg SIZER_S3X_Z1_addendum3 (sha cad3249d...) logged before the run. Hook: per-row arm array for the L2SL cut (per-arm fire tables merged per row; shifted-entry rows re-evaluated with the same per-row arm), the TH-L2 loss cut keeps its trigger (adverse excursion in points from entry AND pulled-support multiple 30x over 5 s) but the adverse threshold in points is per trade, arm = round(clip(3500 / (lots x 20), 20, 40)) with lots = the traded lots of that trade (sequential rounding: session lots -> zone HALF rounded -> x ER ladder 0.5/1.5 rounded, min 1): lots 1-4 -> 40 pts, 5 -> 35, 6 -> 29, 7 -> 25, 8 -> 22, 9+ -> 20; all six live books, all trades, ER ladder and everything else unchanged; base = run_v13t_ts + HALF layer (V13T_LIVE costs, per-book locks, lock R scaled only when mult > 1). X = $3,000 / 3,500 / 4,200 / 5,000 (4,200 = 7 lots x 30 pts x $20), scopes PE only / all six books, rows ER>=0.30 only / all. Post-hoc, no PASS, Shadow only.

**Answer:** the only family that survives is X=$3,500 on ALL six books and ALL rows: lot-scaled arm. Full windows: L6M +4.6% (PA +5%, below the .219 band), HOLD +5%, PRE +7.3% (PA +11%, beyond the .099 band), X' +13.4%, but MID -16% and L3M -8%. With the carrying episodes (W29-W39 in L6M, the PRE episode) dropped: L6M +27.5% and PRE +31.7%; mean change -3.1k/wk L6M (MDE 13.8) and -1.9k PRE (MDE 7.4), i.e. mean within the MDE (kept >= base within 0.5 MDE). Placebos (100 draws each; A = the same arms PERMUTED within book x session: keeps the arm distribution, destroys the lot dependence; B = iid arms from the marginal; C = shuffled-day arms): PRE ranks 0.020 / 0.010 / 0.010 (episode dropped 0.010 / 0.010 / 0.010), X' 0.020 / 0.010 / 0.010, L6M with the episode dropped 0.059 / 0.010 / 0.050, full-window L6M 0.277 / 0.020 / 0.149: the PRE and X' effect is the lot dependence, not a generic arm change. It is a LEAD, not RISK-KEEP (full-window L6M cut below the band, MID and L3M worse, one carrying episode in L6M). Decomposition (X=3500, all books): tighten-only (arm = min(30, scaled)) gives L6M -21% (ep. dropped +22%), PRE +9% (+26%), X' -11%; loosen-only (max(30, scaled)) gives MID +92% and PRE +1%; constant arm 40 or 25 on all rows are much worse (arm 40: L6M -39%, PRE -44%; arm 25: L6M -17%, PRE -4%): the benefit needs the lot scaling (tighter for 7+ lot PE/U7 trades, looser for 1-4 lot books). Caution: 87% of rows get arm 40 (looser than the present 30), i.e. for K7/M7/A6/H7 the cut is relaxed; that is a policy change of the loss protection, not only a PE fix. The PE-only and ER>=0.30 variants do not help (PE only X=3000-4200: L6M -14..-26%, PRE +8..+9%; ER>=.30 rows alone L6M -2..+3%).

### Exposure table (X=3500, all books)
```
X=3500 rows 27902; arm != 30 on 100.0% of rows; arm 20: 8.4%, 21-29: 4.7%, 31-39: 0.0%, 40: 86.8%
      rows  mean_lots  max_lots  mean_arm  tighter_than_30  looser_than_30
book                                                                      
HM    3304        2.3       6.0      38.2             16.6            83.4
KB    8025        1.6       3.0      40.0              0.0           100.0
MV    3674        1.6       3.0      40.0              0.0           100.0
PB    5403        1.7       2.0      40.0              0.0           100.0
PE    6126        6.6      11.0      32.0             41.4            58.6
SM    1370        3.8       6.0      35.2             43.5            56.5
```

### Cells (maxDD cut vs the T-SIZER base; PA = phase-averaged; band = Z3 PA9 flip-5)
| scope | rows | X $ | maxDD cut L3M / L6M / HOLD / MID / PRE / X' (phase-avg) | beyond PA9 band | episode dropped L6M / PRE | mean d $k/wk (MDE) L6M / PRE | mean >= base (within 0.5 MDE) | worst-20 PRE b>a |
|---|---|---|---|---|---|---|---|---|
| PE | ER>=.30 | 3000 | -9% (+1%) / -21% (-6%) / -21% (-6%) / -4% (+10%) / +9% (+5%) / +3% (+4%) | - | +20% / +25% | -2.4 (12.9) / -3.7 (6.5) | no | -823>-788 |
| PE | ER>=.30 | 3500 | -12% (-1%) / -23% (-8%) / -23% (-8%) / -4% (+9%) / +9% (+4%) / +3% (+7%) | - | +20% / +24% | -2.6 (13.0) / -3.9 (6.5) | no | -823>-782 |
| PE | ER>=.30 | 4200 | -17% (-5%) / -26% (-11%) / -26% (-11%) / -4% (+9%) / +8% (+6%) / +1% (+4%) | - | +20% / +23% | -2.9 (12.9) / -4.1 (6.4) | no | -823>-798 |
| PE | ER>=.30 | 5000 | -56% (-37%) / -37% (-23%) / -37% (-23%) / -0% (+6%) / -1% (+1%) / -10% (-7%) | - | +12% / +23% | -3.7 (11.2) / -3.0 (5.3) | no | -823>-845 |
| PE | all | 3000 | +2% (+12%) / -14% (-7%) / -14% (-7%) / -22% (+10%) / +9% (+8%) / +4% (+2%) | - | +14% / +24% | -2.5 (12.2) / -3.2 (6.5) | no | -823>-809 |
| PE | all | 3500 | -8% (+5%) / -13% (-5%) / -13% (-5%) / -27% (+14%) / +8% (+6%) / +8% (+6%) | - | +21% / +21% | -1.8 (11.6) / -2.8 (6.6) | yes | -823>-795 |
| PE | all | 4200 | -14% (+0%) / -17% (-8%) / -17% (-8%) / -27% (+14%) / +8% (+7%) / +5% (+4%) | - | +21% / +21% | -2.1 (11.5) / -3.0 (6.5) | yes | -823>-809 |
| PE | all | 5000 | -55% (-34%) / -41% (-34%) / -41% (-34%) / -5% (+22%) / -1% (-0%) / -3% (-7%) | - | -5% / +21% | -6.2 (11.1) / -2.1 (5.4) | no | -823>-854 |
| ALL | ER>=.30 | 3000 | +14% (+11%) / +3% (+12%) / +3% (+12%) / -34% (-27%) / +10% (+7%) / -10% (+6%) | - | +30% / +31% | -6.3 (15.5) / -3.6 (7.1) | no | -823>-764 |
| ALL | ER>=.30 | 3500 | +1% (-0%) / -2% (+8%) / -2% (+8%) / -18% (-19%) / +8% (+10%) / -12% (+2%) | PRE | +21% / +28% | -3.4 (13.6) / -3.4 (7.0) | yes | -823>-784 |
| ALL | ER>=.30 | 4200 | -12% (-10%) / -15% (-1%) / -15% (-1%) / -9% (+4%) / +9% (+8%) / -18% (-5%) | - | +11% / +24% | -3.1 (14.0) / -3.2 (7.0) | yes | -823>-828 |
| ALL | ER>=.30 | 5000 | -46% (-35%) / -21% (-6%) / -21% (-6%) / +31% (+13%) / -5% (+0%) / +0% (-4%) | - | +7% / +18% | -3.7 (14.4) / -1.6 (5.6) | yes | -823>-880 |
| ALL | all | 3000 | +13% (+11%) / +7% (+6%) / +7% (+6%) / -23% (-7%) / +9% (+8%) / +2% (+5%) | - | +29% / +24% | -7.0 (16.8) / -2.6 (7.4) | yes | -823>-797 |
| ALL | all | 3500 | -8% (-5%) / +5% (+5%) / +5% (+5%) / -16% (-11%) / +7% (+11%) / +13% (+12%) | PRE | +27% / +32% | -3.1 (13.8) / -1.9 (7.4) | yes | -823>-806 |
| ALL | all | 4200 | -22% (-15%) / -9% (-4%) / -9% (-4%) / +15% (+27%) / +7% (+10%) / +4% (+1%) | PRE | +18% / +28% | -2.8 (13.3) / -1.7 (7.4) | yes | -823>-839 |
| ALL | all | 5000 | -58% (-42%) / -29% (-23%) / -29% (-23%) / +82% (+44%) / -6% (-3%) / -19% (-19%) | MID | -5% / +23% | -6.7 (14.9) / -0.2 (6.2) | yes | -823>-896 |

### Placebo ranks for the two cells that qualified (A permuted / B iid / C shuffled-day)
```
ALLall3500 L6M cut +4.6% ranks A(permuted arms)/B(iid marginal)/C(shuffled day) 0.277/0.020/0.149
ALLall3500 L6M (episode dropped) cut +27.5% ranks A(permuted arms)/B(iid marginal)/C(shuffled day) 0.059/0.010/0.050
ALLall3500 PRE cut +7.3% ranks A(permuted arms)/B(iid marginal)/C(shuffled day) 0.020/0.010/0.010
ALLall3500 PRE (episode dropped) cut +31.7% ranks A(permuted arms)/B(iid marginal)/C(shuffled day) 0.010/0.010/0.010
ALLall3500 X cut +13.4% ranks A(permuted arms)/B(iid marginal)/C(shuffled day) 0.020/0.010/0.010
ALLhi3500 L6M cut -1.6% ranks A(permuted arms)/B(iid marginal)/C(shuffled day) 0.436/0.287/0.535
ALLhi3500 L6M (episode dropped) cut +21.5% ranks A(permuted arms)/B(iid marginal)/C(shuffled day) 0.238/0.079/0.248
ALLhi3500 PRE cut +8.0% ranks A(permuted arms)/B(iid marginal)/C(shuffled day) 0.396/0.010/0.436
ALLhi3500 PRE (episode dropped) cut +27.5% ranks A(permuted arms)/B(iid marginal)/C(shuffled day) 0.356/0.010/0.218
ALLhi3500 X cut -11.9% ranks A(permuted arms)/B(iid marginal)/C(shuffled day) 0.851/0.089/0.594
```

(Z1 correction to the SIZER_S3X lot-scaled-cut paragraph above: PE-only cells X=3000-4200 give L6M -13..-26% (PRE +8..+9%); the ER>=0.30-rows-only family over all books gives L6M +3% (X=3000), -2% (3500), -15% (4200), -21% (5000), and PRE +8..+10% for X=3000-4200.)


# S4b SECTION 2 - ADDENDA (written 20:25Z): weekday cells, exposure-aware add, size-matched add-off placebos
## 2.6 Weekday cells (live ER ladder x f(weekday of the label day), cap 0.25..2.0; 20 cells: one weekday x0.75 / x1.25, and x0.75 on each 2-day set; TS base, single path, PA9 for the top 3)
| cell | cut L6M / HOLD / MID / PRE / X' | mean d L6M / HOLD / PRE $k/wk | mean lots | mean_ok | no-harm | band5 |
|---|---|---|---|---|---|---|
| WDSET_Thu+Fri_x0.75 | +23% / +20% / -42% / +15% / +17% | -2.7 / -2.6 / -1.7 | 2.92 | n | n | Y |
| WDSET_Mon+Fri_x0.75 | +1% / +1% / -20% / +12% / +17% | -5.0 / -5.0 / -2.0 | 2.92 | n | Y | n |
| WDSET_Mon+Thu_x0.75 | +13% / +13% / -18% / +9% / +14% | -2.6 / -3.7 / -2.7 | 2.91 | n | Y | n |
| WDSET_Tue+Fri_x0.75 | -4% / -4% / -15% / +9% / +10% | -6.9 / -4.2 / -1.0 | 2.92 | n | Y | n |
| WD_Thu_x0.75 | +17% / +17% / -20% / +8% / +10% | -0.2 / -0.6 / -1.2 | 3.07 | n | Y | n |
| WDSET_Wed+Fri_x0.75 | +30% / +27% / +3% / +13% / +5% | -1.9 / -1.3 / -1.3 | 2.93 | n | Y | Y |
| WD_Fri_x0.75 | +5% / +5% / -22% / +6% / +9% | -2.5 / -1.9 / -0.5 | 3.08 | n | Y | n |
| WDSET_Mon+Tue_x0.75 | -14% / -14% / +10% / +9% / +7% | -6.8 / -5.3 / -2.0 | 2.91 | n | Y | n |
| WDSET_Wed+Thu_x0.75 | +42% / +31% / +5% / +12% / +3% | +0.5 / -0.0 / -2.0 | 2.93 | n | Y | Y |
| WDSET_Tue+Thu_x0.75 | +8% / +8% / -13% / +12% / -1% | -4.5 / -2.9 / -1.8 | 2.91 | n | Y | n |
| WD_Mon_x0.75 | -4% / -4% / +2% / +4% / +7% | -2.4 / -3.0 / -1.5 | 3.06 | n | Y | n |
| WDSET_Mon+Wed_x0.75 | +20% / +20% / +27% / +8% / -2% | -1.8 / -2.4 / -2.3 | 2.92 | n | Y | n |
| WD_Wed_x0.75 | +24% / +24% / +25% / +6% / -8% | +0.6 / +0.6 / -0.8 | 3.08 | Y | Y | n |
| WD_Mon_x1.25 | -4% / -4% / -19% / -3% / -3% | +2.4 / +2.3 / +0.8 | 3.35 | Y | Y | n |
| WD_Thu_x1.25 | -6% / -6% / +2% / -7% / -1% | +0.4 / +1.5 / +0.5 | 3.34 | Y | Y | n |
| WD_Wed_x1.25 | -3% / -3% / -14% / -5% / -3% | +0.3 / +0.4 / +0.3 | 3.33 | Y | Y | n |
| WD_Tue_x0.75 | -9% / -9% / +7% / +3% / -12% | -4.4 / -2.2 / -0.5 | 3.06 | n | Y | n |
| WD_Tue_x1.25 | +19% / +19% / +5% / -4% / -7% | +3.8 / +1.9 / +0.7 | 3.34 | Y | Y | n |
| WD_Fri_x1.25 | -18% / -18% / +12% / -9% / -9% | +1.3 / +1.8 / -0.2 | 3.33 | Y | Y | n |
| WDSET_Tue+Wed_x0.75 | +15% / +15% / +32% / +10% / -33% | -3.7 / -1.6 / -1.3 | 2.92 | n | n | n |
**Plain sentence:** no weekday rule is a lead. The only cell that passes the phase-averaged band AND no-harm is x0.75 on Wednesday+Thursday (PA9 cuts L6M +41.7% / HOLD +30.9% / MID +4.5% / PRE +11.8% / X' +3.4%, carrying-week-dropped L6M +16.8% / PRE +15.6%; mean +0.5k/wk L6M, +0.0 HOLD, -2.0k/wk PRE): its cut ranks against the three placebo kinds (share of 100 placebos below the real cut, perm / day-shuffled / AR(1)) are L6M 0.37 / 0.28 / 0.38 and PRE 0.23 / 0.28 / 0.28, i.e. random multipliers with the same distribution cut as much or more (HOLD 0.93 / 0.90 / 0.97, X' 0.98 / 0.92 / 0.99): VOLUME, and the choice of the pair is one of 10 pairs looked at. x0.75 on Thu+Fri passes the band but harms MID (-42%). Single-day cells: x0.75 on Wednesday cuts L6M +24% / MID +25% with PRE +6.5%, X' -8.3% (fails the band). Size-up days (x1.25) all deepen at least one window.
## 2.7 Exposure-aware add (add_only_if the other books' same-side net open lots at the signal second < N; array net_other_books_ts from BASE-4's stack hook)
| cell | cut L6M / HOLD / MID / PRE / X' | mean d L6M / HOLD / PRE $k/wk |
|---|---|---|
| E_add_only_if_netother<10 | +5% / +5% / +20% / +6% / +1% | -3.4 / -2.7 / -1.2 |
| E_add_only_if_netother<8 | +18% / +18% / +18% / +9% / +1% | -2.7 / -2.5 / -1.9 |
| E_add_only_if_netother<6 | +10% / +10% / +30% / +11% / -7% | -3.8 / -2.7 / -1.9 |
| E_add_only_if_netother<12 | +6% / +6% / +12% / +5% / -1% | -2.0 / -2.2 / -1.1 |
## 2.8 Size-matched add-off placebos (add_only_if cells vs 100 random add-offs with the same cancelled share per book x session; rank = share of placebo draws below the real cell, high = real beats chance)
| real cell (add only when ...) | real cut L6M / HOLD / PRE / X' | real mean d L6M | placebo median cut L6M / HOLD / PRE / X' | share of 100 placebos BELOW the real cut L6M / HOLD / PRE / X' | share below on the mean L6M / PRE | placebo median mean d L6M |
|---|---|---|---|---|---|---|
| A_only_er>=0.30 | +11% / +11% / -7% / +1% | -0.5 | +42% / +33% / +11% / +11% | 0.02 / 0.02 / 0.05 / 0.26 | 1.00 / 1.00 | -5.2 |
| A_only_er>=0.40 | +29% / +29% / +5% / +18% | -4.6 | +54% / +38% / +16% / +12% | 0.02 / 0.09 / 0.13 / 0.69 | 0.83 / 1.00 | -6.6 |
| B_only_if_T1_25 | +65% / +47% / +23% / +26% | -8.4 | +65% / +44% / +23% / +23% | 0.56 / 0.88 / 0.52 / 0.69 | 0.50 / 0.02 | -8.4 |
| B_only_if_T2a_d2/3 | +50% / +50% / +7% / +14% | -6.8 | +55% / +41% / +18% / +13% | 0.22 / 0.96 / 0.07 / 0.56 | 0.62 / 0.25 | -7.4 |
| B_only_if_T3a_ps1/3 | +63% / +33% / +23% / -35% | -5.2 | +50% / +37% / +14% / -2% | 1.00 / 0.32 / 0.94 / 0.02 | 0.43 / 0.52 | -5.0 |
| B_only_if_T4_ice2/3 | +62% / +42% / +26% / +19% | -8.6 | +60% / +43% / +21% / +13% | 0.66 / 0.39 / 0.86 / 0.87 | 0.36 / 0.32 | -8.2 |
**Plain sentence 2.7:** the exposure-aware add (cancel the add when the other books already hold >= N same-side net lots, N = 6 / 8 / 10 / 12 cancels 22 / 16 / 13 / 10 % of live adds) cuts maxDD modestly (N<8: L6M +18%, MID +18%, PRE +9%, X' +1%; N<6: L6M +10%, MID +30%, PRE +11%, X' -7%) but costs mean in every window (-2.0 to -3.8k/wk L6M, -1.1 to -1.9k/wk PRE): no cell keeps the mean; X' is not helped. Not a lead.
**Plain sentence 2.8:** the size-matched add-off placebos show the 'add only when' cells are VOLUME, and some are worse than chance: 'add only if ER >= 0.30' cuts L6M +11% while a random add-off with the same cancelled share cuts +42% (median) and loses 5.2k/wk against -0.5k/wk for the real rule (the ER filter removes adds that earn less than average to the benefit of the mean, but not the drawdown); 'add only if ER >= 0.40' (L6M +29%, PRE +5%, X' +18%, -4.6k/wk) is at or below its placebo in every window (share of placebos below 0.02 / 0.09 / 0.13 / 0.69); the tape-confirmation filters T1 (large print with the trade) and T4 (iceberg with the trade) sit exactly on their placebo medians (shares 0.56 / 0.88 / 0.52 / 0.69 and 0.66 / 0.39 / 0.86 / 0.87), i.e. no information beyond the lower add volume; T3a (own support not pulled) beats its placebo in L6M and PRE (1.00 / 0.94) but loses X' (-35%, share 0.02). The add is a drawdown source of about the right size, and no feature tells which adds to drop.


## SIZER_S2V FOLLOW-UP (ZL-1, 2026-11-02 ~20:30Z): vol-target placebos, and the hybrid 'vol cap on the ER x1.5 side' (prereg SIZER_S2V_HYBRID_prereg.md sha256 d52cb5d375fd089c87df49921e336f79a91a01c8ed21a3bd9ba43ecfc6f4a653, logged before scoring; post-hoc, research only)
### A. Placebos (3 kinds x 100 draws), equal-risk, exposure for the three vol-target cells not in the first top 5
| cell | cut L6M / PRE (phase 0) | PA9 L6M / PRE (X') | placebo rank on CUT L6M (perm, dayshuf, ar1) | on CUT PRE | on MEAN L6M | equal-risk mean L6M / PRE / HOLD (ladder 37.6 / 17.8 / 31.8) | worst-day net lots / stack risk / mean lots (ladder 28 / $33.6k / 3.01) |
|--|--|--|--|--|--|--|--|
| VT 1.0 DOWN-only | 47.0 / 22.3 | 43.4 / 15.7 (-14.4) | .39 .48 .44 | .42 .32 .29 | .92 .93 .95 | 58.7 (lscale 1.78) / 15.5 / 43.6 | 28 / $33.6k / 2.55 |
| VT 1.0 FULL | 56.3 / 18.3 | 58.9 / 16.1 (-27.6, harm) | .86 .89 .81 | .40 .37 .38 | .90 .93 .97 | 89.6 (2.62, extrapolated) / 16.1 / 44.9 | 29 / $34.8k / 2.64 |
| VT 0.75 FULL | 38.2 / 23.3 | 42.7 / 19.8 (-29.8, harm) | .32 .39 .41 | .41 .33 .30 | .81 .84 .89 | 81.4 (2.72, extrapolated) / 16.1 / 49.5 | 29 / $34.8k / 2.35 |
Reading: VT 1.0 FULL is the one vol-target cell whose L6M cut beats random multipliers of the same distribution (rank 0.81-0.89) and whose L6M dollars beat random (0.90-0.97); its PRE cut does not (0.37-0.40, i.e. random does as well), it harms X' (-27.6 PA9) and the PRE equal-risk mean (16.1k) is below the ladder (17.8k). The other two are lot reductions (L6M cut ranks 0.3-0.5). None reduces worst-day exposure (net lots 28-29, stack risk $33.6-34.8k).
### B. Hybrid: vol as a CAP only on the ER x1.5 side (28 cells)
m = ER where ER is x0.5 (untouched); where ER x1.5: 1.5 if quiet else X in {1.0, 0.75}. Quiet = ATR below its expanding same-book median x th (VT; th 0.8-1.25; th 1.0 = 'x1.5 only when ATR is below its median') or rank of atr_ratio_5m / rv_ratio_30m / dayrange_atrd < q (0.33/0.5/0.67). Eligible 24-28 cells; best by key (mean of L6M and PRE cuts):
| cell | cut L6M / PRE | carry-week dropped L6M / PRE | HOLD / MID / X' | mean vs ladder L6M / PRE (MDE) | total $k vs ladder | mean lots | PA9 L6M / PRE / X' | placebo cut rank L6M (perm, dayshuf, ar1) | PRE | equal-risk PRE / HOLD |
|--|--|--|--|--|--|--|--|--|--|--|
| VT th=1.1, X=0.75 | 61.4 / 36.6 | 35.1 / 33.9 | 24.4 / 18.7 / -43.3 | -4.6k (15.1) / -4.7k (6.3) | -716 | 2.60 | 64.2 / 33.5 / -45.4 | .83 .93 .80 | .56 .62 .57 | 18.3 / 39.2 |
| VT th=1.0, X=0.75 | 60.1 / 26.8 | 52.9 / 30.5 | 26.3 / 17.2 / -46.7 | -4.5k (14.2) / -4.5k (5.6) | -608 | 2.70 | 63.0 / 23.3 / -48.8 | .86 .88 .79 | .37 .39 .34 | 17.5 / 42.7 |
| VT th=1.25, X=0.75 | 39.9 / 39.0 | 35.1 / 36.3 | 18.2 / 4.1 / -31.1 | -9.7k (16.2) / -4.8k (6.6) | -828 | 2.50 | 44.3 / 36.0 / -33.0 | .31 .42 .30 | .55 .56 .58 | 18.9 / 31.5 |
Others of interest: VT th=1.0 X=1.0 ('x1.5 only when ATR below median, else x1.0'): cut 35.5 / 20.4, carry-dropped 40.2 / 20.8, HOLD 27.7, MID 15.2, X' -35.2, mean -2.2k / -3.0k, total -369k, lots 2.8. The rank-feature caps (atr_ratio, rv_ratio, dayrange) are weaker or negative on L6M (atr_ratio q .5: -19 / +11).
**EVERY one of the 28 hybrid cells harms X' (-31 to -67%, 2023-04..2024-01): the cap removes x1.5 trades that paid in 2023-24 in high-vol conditions, so no hybrid cell is no-harm (S2 undefined).** The cut in L6M and PRE is real in sign but costs 0.4-0.8M of total dollars and 0.3-0.4 lots per signal.
**Own best-of-N null (28 cells, 65 draws; condition inputs permuted jointly within book x session).** Real best eligible key 49.0; null S1 mean 37.8, p95 47.5, max 51.8; rank p = 0.030 ((1+1)/(1+65): one draw >= real). The null is built from the same cells, so it already contains the lot reduction effect, and still the best real cell sits at the p95 edge. Null draws find a no-harm eligible cell in 75% of draws (real: none), so 'no-harm' is NOT a property the real hybrid has. Reading: moderate, one-sided signal that quiet-vol timing of the x1.5 side helps L6M/PRE drawdown (L6M placebo ranks 0.8-0.93 for th 1.0 / 1.1, PRE 0.34-0.62: not above random in PRE), but it fails X' every time and best-of-28 x best-of-99 multiplicity applies. Not flagged; not a recommendation. If the user wants it as a SHADOW/forward line: 'x1.5 only when ATR14(5m) <= 1.1 x expanding same-book median ATR at the signal, else x0.75 (not x1.0)'.
Files: ds3_zones3_new/sizer_s2v/ (hyb_real.csv, hyb_null_*.csv, hybpa9_*, hybplc_*, hybeq_*, hybex_*, plc_VT_*, equal_risk2.pkl, exposure2.pkl); code zones3/sizer_s2v/ (s2v_fin2.py, s2v_hyb.py, s2v_hybfin.py).

## SIZER_S3 (Z3) - report 1 (2026-11-02 ~21:00Z): 3.2 combinations, 3.3 learned mapping
Shadow only, no PASS claims. V13T_LIVE, sequential rounding, reference = live binary 0.30 ER ladder (same mode, phase-matched); ER sizer is a KEEP (off not ranked). Pool P8 built by the fixed rule (S_sel on PRE and X' only) from pool_inputs_s1.csv (998 cells) + pool_inputs_s2.csv (1,520 parseable of 2,128; gate cells excluded: no rebuildable multiplier): er_1m_100 (L5 B), ers_5m_20 (L3 B), er_2m_50 (L3 A), dist_ema20_5m_atr (L3 A; the only section-2 cell), er_3m_20_min3, ers_3m_20, er_10m_20_max3, er_5m_20_hyst (S4a reaction-speed multiplier vectors). Caveat: S_sel inputs are S4a/S4b single-path PROXY equal-risk cuts with a rough random-multiplier curve (R2 0.36-0.40), so P8 is a proxy ranking. Files: out/sizer_s3/{pool_p8_v2.csv,comb_all.csv,pa9_*.csv,plc_*.json,learned_*.csv,expo_book_sess.csv}; code code/sizer_s3/.

### 3.2 Combinations (114 cells: 84 pairs of P8, 30 triples of the top 5, x PROD / MEAN / MINDOWN)
Non-ER combinations ride on top of the live ER ladder (KEEP rule). All 114 cells have an L6M mean change inside the paired MDE (MDE 15-20k/wk); 30 pass the single-path band rule; 3 also have L6M and PRE cuts above zero with the carrying weeks dropped. PA9 + equal-risk for these 3, and placebos (PA3 = shifts -4/0/4, 100 draws x perm/dayshuf/ar1) for the top 2:
| cell | single-path L6M / PRE / X' / MID | carrying dropped L6M / PRE | PA9 L6M / PRE / X' / MID | L6M d mean (MDE) | equal-risk mean L6M (live 37.6k) / PRE (live 17.8k) | placebo ranks L6M / PRE / X' (perm, dayshuf, ar1) | label |
|---|---|---|---|---|---|---|---|
| er_3m_20_min3 + er_10m_20_max3 MINDOWN | +36.0 / +17.7 / +12.7 / -8.5 | +9.0 / +14.1 | +41.8 / +17.0 / +22.9 / -84.8 | -1.4k (19.5k) | 53.2k / 16.4k | .48 .48 .49 / .51 .43 .43 / .99 .98 1.00 | LEAD at best (MID no-harm fails; L6M, PRE not distinguishable from random multipliers) |
| er_2m_50 + er_10m_20_max3 MEAN | +22.3 / +25.9 / +13.1 / -28.5 | +5.6 / +22.6 | +28.9 / +25.2 / +23.3 / -118.8 | -3.5k (15.8k) | 41.7k / 22.2k | .29 .31 .40 / .68 .73 .73 / 1.00 1.00 1.00 | LEAD at best (MID fails) |
| ers_3m_20 + er_10m_20_max3 MINDOWN | +19.6 / +10.3 / +32.4 / -17.3 | +13.1 / +6.3 | +26.9 / +9.4 / +40.3 / -99.7 | -3.4k (20.4k) | 45.3k / 17.3k | not run | LEAD (MID fails) |
Reading: the best ER x ER pairs cut L6M, PRE and X' versus the live ladder at an equal-or-better equal-risk mean, with the carrying weeks dropped, but (i) MID (2026-02..04, base maxDD 43.7k) gets 85-119% worse in PA9, which breaks the no-harm rule, and (ii) in L6M and PRE the cut is no better than random multipliers with the same distribution (ranks 0.29-0.73); only X' ranks 0.98-1.00. A NOMINAL FLAG (the user's standing rule: L6M and PRE with the carrying week dropped) is written to MORNING_FLAGS.md with the exact definition; the label is LEAD, not RISK-KEEP. No triple is better than the best pair. The other 111 cells: none passes both the carrying-drop and mean gates.
Lots distribution (taken signals, sequential rounding): live ladder mean lots 3.22, max 11; pair MINDOWN 3.09, max 11; pair MEAN 3.32, max 11. Worst single day gross lots (sum of taken-signal lots over the label day, not simultaneous net): live 189 lots (2026-10-01, gross stop-risk $226.8k at 60 pts), MINDOWN pair 186 (2026-05-15, $223.2k), MEAN pair 197 (2025-04-04, $236.4k); 95th percentile day 120 / 113 / 128 lots. Per book x session lots table: out/sizer_s3/expo_book_sess.csv.

### 3.3 Learned monotone mapping (<=6 leaves, 3 seeds, purged walk-forward, causal rank features)
HistGradientBoosting (6 leaves, depth 3, lr 0.05, 100 iterations, monotone constraints from the pool direction, 80% bagging), target R per planned lot, inputs = pool ER and dist_ema20 ranks + book/session dummies; trained on the trailing 12 months ending 5 label days before each month 2024-01..2026-10; multiplier = L3(A) or LIN(A) of the causal per-book expanding rank of the out-of-sample prediction (>=100 earlier OOS predictions, else 1.0). Months before 2024-01 use the hand ladder in both arms, so X' is the same in both and is NOT out-of-sample for the learned arm. Hand ladder compared = pool rank 1 (er_1m_100 L5 B) on the same months.
| cell | L6M / PRE / MID (single path) | carrying dropped L6M / PRE | PA9 L6M / PRE / MID | L6M d mean | mean lots |
|---|---|---|---|---|---|
| HAND er_1m_100 L5 B | +12.3 / -29.4 / +25.8 | -42.2 / -8.7 | +19.3 / -30.6 / -26.4 | +6.0k | 3.6 |
| learned seed0 L3 | +34.0 / +21.6 / -33.2 | -6.5 / +32.7 | +39.7 / +20.9 / -126.9 | -1.2k | 3.4 |
| learned seed0 LIN | +41.1 / +28.9 / -33.2 | +2.6 / +32.2 | +46.5 / +28.3 / -126.8 | -3.0k | 3.2 |
| learned seed1 L3 | +20.6 / +12.9 / -34.6 | -11.6 / +9.1 | +27.8 / +12.1 / -129.2 | -3.3k | 3.4 |
| learned seed1 LIN | +36.7 / +30.2 / -48.8 | -6.4 / +28.0 | +42.5 / +29.5 / -153.4 | -4.0k | 3.2 |
| learned seed2 L3 | +30.0 / +29.5 / -29.8 | -13.6 / +26.4 | +36.4 / +28.9 / -121.0 | -2.0k | 3.3 |
| learned seed2 LIN | +34.0 / +30.6 / -33.5 | -4.3 / +27.5 | +40.0 / +30.0 / -127.3 | -2.0k | 3.2 |
Reading: the learned mapping beats the (poor) hand ladder on L6M and PRE in all 6 cells and the PRE cut is stable across seeds (+13 to +31 single path), but the L6M cut depends on the carrying weeks (5 of 6 cells are negative once they are dropped; seed0 LIN +2.6 is inside noise), MID is 30-50% worse in single path and 121-153% in PA9, and it is judged against the weak hand ladder, not against the live ladder as a rival model (against the live ladder every row above is the cut). NOT flagged: only seed0 LIN meets the L6M-and-PRE carrying-drop test (by +2.6) and it fails MID no-harm. Walk-forward verdict: a refitted learned mapping does not give a robust L6M gain over fixed ladders; it trades MID for PRE.

### Not done in this report
3.6 sizer x lock (the engine does not expose R-from-base-lots vs R-from-sized-lots; waiting for BASE-4's live-faithful lock option, then the ranked cells are rerun); placebos for the learned cells and the third pair; per-book/vol-tercile split tables for the ranked cells (harness split option). 3.4 risk parity and 3.5 brackets: see the interim section above (no flags).

## SIZER_S3X (Z1) - STRESS of the lot-scaled TH-L2 cut (2026-11-02 21:06Z)
Prereg SIZER_S3X_Z1_addendum4 (sha ce70e27f...) logged before the run. Cell = arm_i = round(clip(X/(lots_i x $20), lo, hi)) pts on all six live books, all rows; real cell X=3500, clip 20..40; base = T-SIZER base (run_v13t_ts + HALF layer). Post-hoc, no PASS, Shadow only.

**Answer: the flag STANDS as a LEAD with five qualifiers; it is not RISK-KEEP.**
1. Best-of-16 null (100 worlds with shuffled-day lot assignments): the real best of the 16-cell grid beats every null world except ties at the floor: S1 (mean of PRE and X' PA cut) real 0.116 vs null best-of-16 median -0.088 / 95th 0.037 / max 0.069, rank 0.010; S2 (min of the episode-dropped L6M and PRE cuts) real 0.297 vs null median 0.024 / 95th 0.106, rank 0.010. The lot dependence is real; it is not search luck.
2. Choice stability FAILS: the purged walk-forward on (X, clip) (trailing 12 m Calmar at trailing mean >= base) picks eight different configs in 34 months and the chain is worse than the base in L6M/HOLD (maxDD -4% cut = deeper, mean 32.0k vs 38.5k) and only +7% in PRE; the fixed X=3500 clip 20..40 is L6M +4%, PRE +11% but mean 35.4k vs 38.5k. So X and the clip are not fittable out of sample; the evidence is for the mechanism, not a tuned number.
3. NEVER-LOOSER (arm = min(30, .), only 7+ lot trades get tighter): keeps the carrying-episode-dropped benefit (X=3500: L6M +22%, PRE +26% dropped) but the full-window cuts shrink (L6M -6%, PRE +5%, X' +3%, MID -7%) and the mean cost rises in PRE (-4.1k/wk vs MDE 6.6). The loosen half is what lifts PRE/X' from +5/+3 to +11/+12 (and costs MID); the tighten half carries the episode-dropped L6M/PRE gain.
4. Frames agree: V13T2 (kfix) PRE +8% / X' +7% (episode dropped L6M +16%, PRE +31%); single rounding PRE +11% / X' +14% (episode dropped +27% / +33%).
5. Stability: the cell loses money in the recent window and in PRE: monthly P&L difference vs base positive in 24 of 43 months, sums L6M -84k, PRE -140k, X' +94k, MID +83k (worst month 202505 -177k). Per book it is a PE (7-11 lot) effect: PE alone L6M -5%, PRE +6%, X' +6%, MID +14%, mean -1.8 / -2.8k/wk; the other books are +-4%.
6. Lots basis matters decisively: with BASE lots (no ER x1.5/x0.5) the same rule does NOT work (X=3500: L6M -11%, PRE -14%, X' -15%, episode dropped -1% / +5%); the cut works only when keyed to the ACTUAL traded lots that include the x1.5 inflation, i.e. it is exactly a protection for the x1.5 big-lot trades.
Flag rule of the prereg: beats on PRE and L6M with the carrying week dropped (+27.5% / +31.7%), mean >= base within 0.5 MDE (-3.1k vs MDE 13.8; -1.9k vs 7.4), null rank 0.010 <= 0.10, frames agree in sign on PRE and X': all met, so the flag stays; withdrawn items: none; qualifiers 2, 5 and the full-window L6M cut +4.6% (below the .219 band) keep it a LEAD.

### (1) Best-of-N null
Worlds complete: 100. Score S1 = mean(PA PRE cut, PA X' cut): real best of 16 = 0.116, null best-of-16 median -0.088 / 95th 0.037 / max 0.069 -> rank 0.010. Score S2 = min(L6M cut, PRE cut) with carrying episodes dropped: real best 0.297, null best median 0.024 / 95th 0.106 -> rank 0.010. The real cell ALL/all/3500 (S1 0.116, S2 0.275) vs its own shuffled-lots cell: S1 rank 0.010, S2 rank 0.010.

### (2) Purged walk-forward and never-looser variants
| series | maxDD $k L6M / HOLD / MID / PRE (X' = base before 2024-01 for the chain) | mean $k/wk L6M / HOLD / MID / PRE | worst-20 PRE |
|---|---|---|---|
| base (no lot-scaled cut) | 170 / 170 / 45 / 161 | 38.5 / 32.2 / 23.5 / 18.0 | -823 |
| fixed X=3500 clip 20..40 | 163 / 163 / 53 / 149 | 35.4 / 31.4 / 27.0 / 16.2 | -806 |
| walk-forward chain (trailing 12 m Calmar at mean >= base) | 177 / 177 / 45 / 150 | 32.0 / 29.6 / 30.3 / 15.3 | -867 |

Chosen config counts over 34 months: (3500, 20, 50, False) x7, None x6, (3000, 15, 40, False) x4, (5000, 20, 50, False) x4, (5000, 20, 40, False) x4, (3000, 20, 50, False) x3, (3500, 15, 40, False) x2, (3500, 20, 40, False) x2, (4200, 20, 30, False) x2. Chain cut vs base: L6M -4%, HOLD -4%, MID +0%, PRE +7%.

| config | maxDD cut L6M / HOLD / MID / PRE / X' (PA) | episode dropped L6M / PRE | mean d L6M / PRE $k/wk (MDE) |
|---|---|---|---|
| X=3000 clip 20..40 | +6% / +6% / -7% / +8% / +5% | +29% / +24% | -7.0 (16.8) / -2.6 (7.4) |
| X=3000 clip 20..30 | -1% / -1% / -11% / +2% / +3% | +30% / +29% | -5.7 (15.4) / -4.2 (6.8) |
| X=3000 clip 15..40 | +33% / +33% / -6% / -5% / +25% | +38% / +2% | -8.6 (20.5) / -4.1 (8.5) |
| X=3000 clip 20..50 | +8% / +8% / -10% / +13% / -4% | +17% / +21% | -7.6 (18.4) / -1.4 (7.6) |
| X=3000 clip 20..30 NEVER-LOOSER min(30,.) | -1% / -1% / -11% / +2% / +3% | +30% / +29% | -5.7 (15.4) / -4.2 (6.8) |
| X=3500 clip 20..40 | +5% / +5% / -11% / +11% / +12% | +27% / +32% | -3.1 (13.8) / -1.9 (7.4) |
| X=3500 clip 20..30 | -6% / -6% / -7% / +5% / +3% | +22% / +26% | -2.8 (13.3) / -4.1 (6.6) |
| X=3500 clip 15..40 | +23% / +23% / -5% / +17% / +19% | +43% / +32% | -3.4 (16.2) / -3.5 (8.3) |
| X=3500 clip 20..50 | +0% / +0% / -8% / +19% / -2% | -6% / +37% | -5.8 (15.3) / -1.3 (7.6) |
| X=3500 clip 20..30 NEVER-LOOSER min(30,.) | -6% / -6% / -7% / +5% / +3% | +22% / +26% | -2.8 (13.3) / -4.1 (6.6) |
| X=4200 clip 20..40 | -4% / -4% / +27% / +10% / +1% | +18% / +28% | -2.8 (13.3) / -1.7 (7.4) |
| X=4200 clip 20..30 | -8% / -8% / +9% / +4% / +5% | +20% / +24% | -2.5 (12.9) / -3.9 (6.5) |
| X=4200 clip 15..40 | +6% / +6% / +32% / +10% / +2% | +19% / +31% | -3.1 (14.9) / -1.1 (7.4) |
| X=4200 clip 20..50 | -21% / -21% / +20% / +11% / -17% | +14% / +32% | -5.0 (13.5) / -1.6 (7.9) |
| X=4200 clip 20..30 NEVER-LOOSER min(30,.) | -8% / -8% / +9% / +4% / +5% | +20% / +24% | -2.5 (12.9) / -3.9 (6.5) |
| X=5000 clip 20..40 | -23% / -23% / +44% / -3% / -19% | -5% / +23% | -6.7 (14.9) / -0.2 (6.2) |
| X=5000 clip 20..30 | -18% / -18% / +7% / +0% / -4% | +12% / +25% | -3.5 (11.5) / -2.8 (5.4) |
| X=5000 clip 15..40 | -23% / -23% / +44% / -3% / -19% | -5% / +23% | -6.7 (14.9) / -0.2 (6.2) |
| X=5000 clip 20..50 | -36% / -36% / +26% / +7% / -32% | +19% / +23% | -7.7 (14.6) / -0.0 (6.2) |
| X=5000 clip 20..30 NEVER-LOOSER min(30,.) | -18% / -18% / +7% / +0% / -4% | +12% / +25% | -3.5 (11.5) / -2.8 (5.4) |

### (3) Frames
| frame | cell | maxDD cut vs the frame's own base: L6M / HOLD / MID / PRE / X' (PA) | episode dropped L6M / PRE | mean d L6M / PRE $k/wk (MDE) |
|---|---|---|---|---|
| V13T2 (kfix) | lot-scaled 3500 clip 20..40 | +10% / +10% / -7% / +8% / +7% | +16% / +31% | -3.2 (13.2) / -2.0 (7.0) |
| V13T2 (kfix) | never looser min(30,.) | -1% / -1% / -24% / -0% / +7% | +26% / +28% | -1.8 (12.3) / -4.0 (6.3) |
| single rounding | lot-scaled 3500 clip 20..40 | +0% / +0% / -10% / +11% / +14% | +27% / +33% | -3.1 (13.1) / -2.0 (7.2) |
| single rounding | never looser min(30,.) | -7% / -7% / -7% / +5% / +10% | +22% / +25% | -2.9 (13.3) / -4.1 (6.6) |

### (4) Monthly stability and per-book
Monthly P&L difference cell - base (X=3500, clip 20..40, all books): positive in 24 of 43 months; sum by window: L6M -84k, PRE -140k, X' +94k, MID +83k.
Months with the largest negative difference: 202505 -177k, 202606 -110k, 202506 -46k, 202509 -42k, 202603 -38k; largest positive: 202602 +97k, 202609 +54k, 202502 +51k, 202311 +48k, 202310 +38k.

Per book (the real cell applied to ONE book at a time; full-stack PA cut vs base):

| book | cut L6M / HOLD / MID / PRE / X' | mean d L6M / PRE $k/wk |
|---|---|---|
| KB | +3% / +3% / +2% / -2% / -3% | +0.1 / +0.5 |
| PE | -5% / -5% / +14% / +6% / +6% | -1.8 / -2.8 |
| SM | +3% / +3% / -12% / -1% / +2% | +1.0 / -0.2 |
| HM | -1% / -1% / +3% / +4% / -2% | -1.8 / +0.5 |
| MV | +4% / +4% / -3% / +1% / +3% | -0.7 / +0.2 |
| PB | +0% / +0% / +0% / +0% / +0% | +0.0 / +0.0 |

### (5) Lots basis
| lots basis | variant | maxDD cut L6M / HOLD / MID / PRE / X' (PA) | episode dropped L6M / PRE | mean d L6M / PRE $k/wk (MDE) |
|---|---|---|---|---|
| base lots (no ER multiplier), clip 20..40 | X=3000 | -3% / -3% / +20% / -6% / -9% | +19% / +12% | -6.4 (18.3) / -4.2 (6.4) |
| base lots, never looser min(30,.) | X=3000 | -4% / -4% / +4% / -13% / -3% | +18% / +10% | -6.8 (14.2) / -5.6 (6.2) |
| base lots (no ER multiplier), clip 20..40 | X=3500 | -11% / -11% / +21% / -14% / -15% | -1% / +5% | -6.4 (15.8) / -2.5 (5.1) |
| base lots, never looser min(30,.) | X=3500 | -10% / -10% / +7% / -12% / -1% | -0% / +4% | -6.0 (11.5) / -4.1 (4.6) |
| base lots (no ER multiplier), clip 20..40 | X=4200 | +4% / +4% / +1% / -4% / -8% | -0% / +1% | -0.4 (7.4) / +1.6 (3.4) |
| base lots, never looser min(30,.) | X=4200 | +0% / +0% / +0% / +0% / +0% | +0% / +0% | +0.0 (0.0) / +0.0 (0.0) |
| base lots (no ER multiplier), clip 20..40 | X=5000 | -7% / -7% / +9% / -16% / -19% | -36% / -28% | -0.8 (17.1) / +3.3 (6.6) |
| base lots, never looser min(30,.) | X=5000 | +0% / +0% / +0% / +0% / +0% | +0% / +0% | +0.0 (0.0) / +0.0 (0.0) |
| ER-multiplied lots (the flagged cell) | X=3500 | +5% / +5% / -11% / +11% / +12% | +27% / +32% | |


## SIZER_S2V_MEAN (ZL-1, 2026-11-02 ~22:15Z): mean-keeping quiet-vol cap on the ER x1.5 side (prereg SIZER_S2V_MEAN_prereg.md sha256 b0aea82d8874fe1b4d571a8d56a583ad26d580323cf081473fad43a8e3adf8ee, logged before scoring; post-hoc, research only; ladder = KEEP)
Cap allows ER x1.5 when ATR14(5m) <= a x its expanding same-book median (a = 0.9 ... 2.0), else X (1.0 or 0.75); ER x0.5 rows untouched. 17 cells: F1 PE-only (10), F2 mild all-books X=1.0 (3: a 1.25/1.5/2.0), F3 compensation (4). Strict mean-keeping = mean >= ladder in L6M, PRE and HOLD.
### Real cells (phase 0 vs the live ladder; cuts %, mean k$/wk vs ladder, total $k)
| cell | cut L6M / PRE | carry-dropped L6M / PRE | HOLD / MID / X' | d mean L6M / PRE / HOLD | d total k | max mult | no-harm |
|--|--|--|--|--|--|--|--|
| PE a=0.9 X=1.0 | 23.9 / 12.5 | -8.8 / 22.5 | 23.9 / 37.2 / -16.3 | 0.0 / -2.7 / +0.7 | -225 | 1.5 | no |
| PE a=1.0 X=1.0 | 21.1 / 9.3 | 11.1 / 22.3 | 21.1 / 34.3 / -21.8 | +0.6 / -2.1 / +1.6 | -154 | 1.5 | no |
| PE a=1.25 X=1.0 | 12.4 / 8.8 | 2.0 / 15.7 | 12.4 / 41.9 / -16.1 | +3.9 / -1.5 / +3.2 | -8 | 1.5 | no (X') |
| PE a=1.5 X=1.0 | 23.7 / 8.8 | -0.6 / 13.6 | 23.7 / 41.9 / -8.2 | +2.9 / -0.9 / +2.5 | +23 | 1.5 | yes (X' -8.2) |
| PE a=2.0 X=1.0 | -6.3 / 6.3 | 3.8 / 2.1 | -6.3 / 28.9 / +1.4 | +0.2 / +0.1 / +0.8 | +34 | 1.5 | yes |
| PE a=1.0 X=0.75 | 49.0 / 11.9 | 16.7 / 15.8 | 41.7 / 35.5 / -32.3 | -0.9 / -3.8 / +0.4 | -350 | 1.5 | no |
| PE a=0.9 X=0.75 | 39.5 / 16.7 | -1.7 / 32.7 | 39.5 / 39.8 / -24.1 | -1.2 / -4.4 / -0.6 | -441 | 1.5 | no |
| ALL a=1.25 X=1.0 | 15.5 / 13.4 | 20.2 / 17.4 | 15.5 / 33.9 / -27.9 | +1.9 / -2.2 / +0.9 | -180 | 1.5 | no |
| ALL a=1.5 X=1.0 | 28.0 / 9.4 | 13.0 / 12.9 | 21.8 / 30.5 / -17.5 | +2.0 / -1.5 / +1.1 | -90 | 1.5 | no |
| ALL a=2.0 X=1.0 | -3.8 / 6.3 | 8.6 / 2.2 | -3.8 / 23.3 / +1.4 | +0.8 / -0.3 / +0.6 | -5 | 1.5 | yes |
(all 17 cells: ds3_zones3_new/sizer_s2v/mean_real.csv; MDE L6M about 13-16k/wk, PRE about 5-6k/wk, so all mean changes are inside the noise.)
**(1) PE-only:** the mean is kept (L6M +0.0 to +3.9k/wk, HOLD +0.4 to +3.2k, total -225k to +34k) and the PRE cut is small (9-17%; carry-dropped PRE 13-33%), L6M cut 12-49% but with the carrying week dropped it collapses to -9..+17%, i.e. it is carried by one week for PE. No cell is strict mean-keeping with a cut: PRE mean is -1 to -4k/wk for every cell that cuts PRE by more than 8%. The no-harm cells are the ones that barely cap (a=1.5 X=1.0: L6M 23.7 carry-dropped -0.6, PRE 8.8; a=2.0: L6M -6.3). X' is harmed (-8 to -32%) by every PE-only cell with a <= 1.5 (least: a=1.5 X=1.0 at -8.2).
**(2) Compensation (withheld lots added to quiet x1.5 trades, cap 1.75):** mean improves (CPE a=1.25: L6M +6.2k/wk, HOLD +5.2k, total +180k; CALL a=1.25: +5.7k, +4.2k, +101k) with L6M cut 21%, PRE cut about 0 or negative, X' -21 to -52. **Exposure FAILS for all four:** worst-day net lots 29-32 and stack risk $34.8-38.4k vs 28 / $33.6k for the ladder, max lots 12 vs 11 (mean lots 2.8-3.0). By the stated rule they are not eligible; PA9 / placebos for CALL a=1.0: PA9 40.1 / 1.2 (L6M / PRE), placebo cut ranks L6M .36-.39, PRE .19-.28.
**(3) Milder cap, all books X=1.0:** a=1.25 cut 15.5 / 13.4 (carry-dropped 20.2 / 17.4), X' -27.9; a=1.5 cut 28.0 / 9.4, X' -17.5, mean +2.0k/-1.5k, total -90k; a=2.0 nothing (-3.8 / 6.3). The mean cost falls to 5-180k but the cut falls with it, and X' stays harmed.
**Finalists (top 3 eligible by key, PA9, 3 placebos x100, equal-risk):**
| cell | PA9 L6M / PRE / X' | carry-dropped PA9 L6M / PRE | placebo rank on CUT L6M (perm, dayshuf, ar1) | PRE | on MEAN L6M | equal-risk mean L6M / PRE / HOLD (ladder 37.6 / 17.8 / 31.8) |
|--|--|--|--|--|--|--|
| PE a=1.0 X=0.75 | 52.7 / 7.6 / -34.2 (fails band PRE 7.8) | 15.9 / 15.4 | .67 .68 .63 | .10 .20 .10 | .98 .86 .95 | 72.9 / 14.8 / 63.5 |
| PE a=0.9 X=0.75 | 43.9 / 12.6 / -25.9 | -2.7 / 32.4 | .38 .47 .45 | .10 .24 .15 | .98 .83 .95 | 69.6 / 14.7 / 58.1 |
| CALL a=1.0 X=1.0 (exposure-failed) | 40.1 / 1.2 / -53.9 | 40.1 / 10.9 | .37 .39 .36 | .28 .23 .19 | .81 .82 .88 | 58.1 / 15.9 / 46.9 |
The PRE cuts of PE-only caps rank 0.1-0.2 against random multipliers (random does better on PRE), and the PRE equal-risk mean (14.7-15.9k) is below the ladder's 17.8k; HOLD equal-risk is high (46-64k vs 31.8k) with lscale about 1.6-2.05. The L6M cut is not above random for PE a=0.9 (rank .38-.47) and only moderately for PE a=1.0 (.63-.68). MEAN dollars rank .81-.98 vs random (the cap keeps dollars).
**Family best-of-N null (13 cells F1+F2, 42 draws, joint permutation of the ATR ratio within book x session):** real best eligible key 30.4 (PE a=1.0 X=0.75) vs null mean 19.5, p95 31.1, max 33.2, p = 0.093; strict mean-keeping best key -0.01 (PE a=2.0) vs null (only 9 of 42 draws had any strict mean-keeping cell) mean 4.3, p 0.8. So no hybrid PE/mild cap is above the family's chance level once mean-keeping is required.
### (4) X' harm: is it the 2023-24 high-vol regime where x1.5 paid? (ladder x1.5 taken trades; mean $/trade at actual lots by label year x ATR tercile of the expanding per-book rank of atr14_5m; T0 quiet, T2 volatile)
| year | ALL books T0 / T1 / T2 ($/trade; n) | PE only T0 / T1 / T2 |
|--|--|--|
| 2023 (Apr-Dec) | 253 / -214 / 182 (401/281/245) | 554 / -1,209 / 480 (100/64/58) |
| 2024 | 414 / 79 / 820 (631/649/536) | 933 / -530 / 2,258 (172/146/125) |
| 2025 | 612 / 353 / 337 (727/814/706) | 1,129 / 993 / 2,077 (235/217/151) |
| 2026 | 266 / 590 / 239 (480/1,078/921) | 175 / 1,446 / 41 (168/273/149) |
X' window (2023-04..2024-01) ladder x1.5 trades, all books: T0 331 $/trade (n 474, +157k), T1 36 (326, +12k), T2 83 (271, +23k); PE only: T0 554 (118, +65k), T1 -566 (70, -40k), T2 57 (64, +4k). The rest (2024-02..2026-10): ALL T0 441 / T1 362 / T2 430; PE T0 799 / T1 786 / T2 **1,494** (n 557/630/419). Reading: the hypothesis is only half right. In X' the volatile (T1+T2) x1.5 trades earned little ($36-83/trade, +35k total) versus quiet ones ($331), so a cap removes trades that paid little there; but the harm to X' maxDD comes from the PATH (withheld lots no longer offset the losing stretch, and X' base maxDD is small, 92k), and over 2024-26 the volatile PE x1.5 trades are the BEST ($1,494 vs $799 quiet; 2024 T2 $2,258, 2025 T2 $2,077), 2026 the worst ($41). So the quiet-vol rule cuts PE's best trades in two of three recent years; it only pays in 2026. The ATR tercile is not a stable separator of x1.5 quality: sign changes by year (PE T1 negative in 2023-24, positive 2025-26). x0.5 trades: X' T0 52 / T1 137 / T2 -21 $/trade (n 495/337/438), rest 106 / 21 / 37.
**Flag:** none. No cell beats the ladder on L6M and PRE with the carrying week dropped, is no-harm, AND is strict mean-keeping (the only strict cell is a=2.0 PE, which does nothing). The nearest candidates: PE a=1.5 X=1.0 (mean +2.9k L6M, +2.5k HOLD, -0.9k PRE, total +23k; cut 23.7 / 8.8 with carry-dropped -0.6 / 13.6, X' -8.2): not flaggable (L6M carry-dropped negative). Best-of-17 here, best-of-99 and best-of-28 earlier.
Files: ds3_zones3_new/sizer_s2v/ (mean_real.csv, mean_null_*.csv, meanpa9_*, meanplc_*, meaneq_*, mean_exposure.pkl, regime_all.csv, regime_pe.csv); code zones3/sizer_s2v/ (s2v_mean.py, s2v_regime.py).


## SIZER_S3X_STRESS addendum 5: rule-shaped lot-bucket TH-L2 arms (2026-11-02T21:15Z) POST-HOC, no PASS, Shadow only
Prereg l2vast/ds3/prereg/SIZER_S3X_Z1_addendum5_prereg.md sha256 478d7a47...cd0 (DECISIONS.md 21:07Z), 8 fixed cells, no fitted parameter. Base = run_v13t_ts + HALF layer. Ledger: 48 stress+rule cells appended to the dead-cells ledger under SIZER_S3X_STRESS after dead_lookup (0 prior rows).
Fact that changes the reading: in the live ladder the PE book trades only 2, 4, 6 and 11 lots (390 / 3198 / 181 / 2357 rows); 7-10 lots never occur. So "lots >= 7" = exactly the 11-lot rows (ER >= 0.30 x full size) and "5-7" = the 6-lot rows; SM trades 1, 2, 3, 6 lots.
| cell | maxDD cut PA L6M / HOLD / MID / PRE / X' | PA9 band L6M/HOLD/MID/PRE/X | episode dropped L6M / PRE | S1 | mean d L6M / PRE $k/wk (MDE) | P&L total d $k |
|---|---|---|---|---|---|---|
| PE-R1 | -32% / -32% / +31% / -8% / +8% | .165/.205/.322/.099/.182 | -5% / +10% | 0.003 | -4.7 (9.0) / -1.8 (4.4) | -141 |
| PE-R1n | -6% / -6% / +10% / -6% / +6% | .165/.205/.322/.099/.182 | +8% / +16% | 0.001 | -1.6 (10.2) / -2.6 (4.5) | -244 |
| PE-R2 | -22% / -22% / +27% / -4% / -5% | .165/.205/.322/.099/.182 | -2% / +16% | -0.042 | -6.8 (11.2) / -2.8 (6.2) | -303 |
| PE-R2n | -23% / -23% / +10% / -9% / -2% | .165/.205/.322/.099/.182 | +15% / +16% | -0.055 | -4.7 (12.8) / -3.7 (6.2) | -474 |
| U7-R1 | +2% / +1% / -7% / -7% / -3% | .165/.205/.322/.099/.182 | +5% / -5% | -0.049 | +1.9 (4.2) / -0.5 (1.7) | +3 |
| U7-R2 | +2% / +2% / +1% / -1% / +2% | .165/.205/.322/.099/.182 | -2% / +1% | 0.003 | +0.6 (1.4) / -0.0 (0.5) | +79 |
| PEU7-R1 | -31% / -31% / +36% / -15% / +2% | .165/.205/.322/.099/.182 | -1% / +6% | -0.065 | -2.9 (11.1) / -2.3 (4.8) | -138 |
| PEU7-R2 | -20% / -20% / +32% / -5% / -4% | .165/.205/.322/.099/.182 | -3% / +15% | -0.041 | -6.2 (11.1) / -2.8 (6.3) | -225 |

Reading (positive = smaller drawdown; PA9 band in the second column): no rule-shaped cell cuts the phase-averaged drawdown on PRE or X' (PA PRE -4% to -15%, X' -5% to +8%, all inside or on the wrong side of the band), L6M PA is worse (-20% to -32%) for every PE cell, S1 (mean PA PRE, PA X') is about 0. The episode-dropped cuts are positive for PE-R1n (+8% L6M / +16% PRE) and PE-R2n (+15% / +16%), but each loses $244k / $474k of total P&L, mean changes are inside the MDE and PA PRE is negative, so they do not meet the "PA PRE cut > 0" reading of the prereg qualifier. Placebos A/B/C and the best-of-8 null were therefore NOT run (no cell qualified on PA); if the lead reads the qualifier as the episode-dropped cut only, PE-R1n and PE-R2n need the placebos and I will run them. U7 cells do nothing (|cut| <= 7%, P&L +3k / +79k). Verdict: the dollar-formula LEAD does not reduce to a simple lots rule; the rule shapes are DEAD for the drawdown objective, the flag text for the lot-scaled cut is unchanged (LEAD with qualifiers). Why: the formula arm for 11 lots is 3500/(11*20) = 16 -> clipped to 20, tighter than 22/25, and for 4 lots it is 40 (rule-shaped R1 gives 40 for <=6 too) but the 2- and 6-lot rows get 40 and 29 in the formula versus 40 and 40/30 here.

### PE mechanics by lots bucket (item 3)
Arms constant per PE row (25 / 30 / 40); rows = PE rows where the TH-L2 trigger changes the exit versus the library exit (stored cut delta in points x lots x $20; includes profitable trades cut early, not only losers). Exit-at-cut loss = -(arm + 0.80 xcost) x lots x $20 (a trade that is cut exactly at the arm):
| lots | PE trades | cut trades arm 25 / 30 / 40 | mean cut delta pts vs library exit 25 / 30 / 40 | mean $ per cut trade 25 / 30 / 40 | total $ delta 25 / 30 / 40 | 25 minus 30 $ total | 40 minus 30 $ total | exit-at-cut loss -(arm+0.8)*lots*20 at 25 / 30 / 40 |
|---|---|---|---|---|---|---|---|---|
| 1-4 | 3588 | 2345 / 2190 / 1876 | -1.0 / -0.6 / 0.7 | -84 / -39 / +66 | -196660 / -84743 / +123390 | -111917 | +208133 | -1952 / -2330 / -3087 |
| 5-6 | 181 | 121 / 118 / 106 | 17.4 / 14.7 / 12.3 | +2084 / +1766 / +1479 | +252164 / +208375 / +156731 | +43789 | -51643 | -3096 / -3696 / -4896 |
| 11 | 2357 | 1506 / 1391 / 1226 | -1.9 / -0.5 / -1.0 | -412 / -106 / -228 | -620552 / -146930 / -279840 | -473622 | -132910 | -5676 / -6776 / -8976 |
| 1-99 | 6126 | 3972 / 3699 / 3208 | -0.8 / -0.1 / 0.4 | -142 / -6 / +0 | -565049 / -23299 / +281 | -541749 | +23581 | -3419 / -4081 / -5406 |

Exit-at-cut loss by lots (analytic, $ per cut trade at arm 25 / 30 / 40): 7 lots -3612 / -4312 / -5712; 9 lots -4644 / -5544 / -7344; 11 lots -5676 / -6776 / -8976 (7 and 9 lots do not occur in live PE; only 11 does). Tightening 30 -> 25 saves $700 per cut 7-lot trade, $900 at 9, $1,100 at 11, but at 11 lots arm 25 changes 115 more rows than arm 30 and the net total over all 11-lot rows is $474k worse than arm 30 (arm 40 is $133k worse): trades cut at 25 that would have recovered cost more than the saved loss. At 4 lots the picture reverses (arm 40 is +$208k better than 30, arm 25 -$112k), at 6 lots arm 25 is +$44k and arm 40 -$52k. That is the whole mechanism: large-lot rows prefer a tight arm only for drawdown containment, not for P&L.

## SIZER_S1 update (2026-11-02 21:30Z): ts-base re-screen, exact equal-risk, rank-hysteresis family with a family-wise null, tier carrying, exposure

Prereg: ZL_S4A_PREREG_SIZER_HYST_FAMILY.md (sha256 6da9c8038f47a138ebf47a8e6276e57e24cbe88086ce5c61eaa854d4e492acc3, DECISIONS.md). Base = the current T-SIZER harness (ts mode: V13T_LIVE costs, sequential rounding, lock R scaled only when mult > 1), reference = live binary ER ladder in the same mode; single path (lock-reset phases are identical on this base). IMPORTANT: the section-1 screen of 998 cells above was run on the sequential-without-ts base; the top 100 of it were re-run on the ts base here.

**(0) Base sensitivity.** The ts re-screen of the top 100 keeps 77 cells at mean >= live. The previous lead (ER(20) rank hysteresis 3 tiers) changes from PA9 L6M +.34 / PRE +.19 (sequential base) to single-path L6M +0.31; see (2): on the ts base its PRE cut is about zero. The lead is BASE-SENSITIVE.

**(2) Family of 72 rank-hysteresis settings** (ER window 14/20/30 x expanding/rolling-250 rank x cuts (1/4,3/4) (1/3,2/3) (.4,.6) x margin 0/.03/.05/.10). Eligible cells (mean >= live, no window worse than the PA9 flip-5 band): 5 of 72. Single-path cuts of the best cells:

| cell | cut L6M | HOLD | MID | PRE | X' | drop L6M | drop PRE | mean $/wk | S=(L6M+PRE)/2 | eligible |
|--|--|--|--|--|--|--|--|--|--|--|
| ER20 exp cuts 1/4-3/4 h0.05 | +0.39 | -0.00 | -0.75 | +0.32 | -0.13 | -0.12 | +0.40 | -254 | +0.351 |  |
| ER20 exp cuts 1/3-2/3 h0.1 | +0.47 | +0.11 | -0.37 | +0.21 | +0.04 | +0.02 | +0.21 | +855 | +0.336 |  |
| ER30 exp cuts 1/4-3/4 h0.1 | +0.46 | -0.07 | -1.24 | +0.13 | +0.09 | +0.01 | +0.13 | -2898 | +0.298 |  |
| ER20 exp cuts 1/4-3/4 h0.03 | +0.39 | +0.00 | -0.70 | +0.18 | -0.05 | -0.12 | +0.33 | -1619 | +0.284 |  |
| ER20 roll cuts .4-.6 h0.1 | +0.46 | +0.10 | -0.73 | +0.10 | +0.14 | +0.01 | +0.20 | +1559 | +0.281 |  |
| ER14 exp cuts 1/4-3/4 h0.1 | +0.38 | -0.25 | -1.75 | +0.18 | -0.31 | +0.14 | +0.18 | -3579 | +0.281 |  |
| ER30 exp cuts .4-.6 h0.1 | +0.42 | -0.43 | -1.65 | +0.11 | +0.09 | +0.27 | +0.11 | -283 | +0.269 |  |
| ER30 roll cuts .4-.6 h0.05 | +0.30 | -0.29 | -1.60 | +0.24 | +0.07 | +0.00 | +0.24 | -2500 | +0.267 |  |
| ER20 exp cuts 1/4-3/4 h0.1 | +0.34 | -0.03 | -1.02 | +0.18 | -0.36 | -0.21 | +0.18 | -1344 | +0.260 |  |
| ER20 roll cuts 1/4-3/4 h0.03 | +0.31 | +0.01 | -0.74 | +0.21 | -0.01 | -0.17 | +0.32 | -1882 | +0.259 |  |

Best-of-grid statistic B = max S over eligible cells = +0.142 (B2 = max min(L6M,PRE) = +0.031; unconditioned max S = +0.351). FAMILY-WISE NULL (day-shuffled multiplier worlds, one day-source map per world applied to all 72 cells): 100 complete worlds so far (target 100). Null B: median -9.000, 95th pct -9.000; share of worlds with an eligible cell 0.00. P-value of B = 0.010; of B2 = 0.010; of the unconditioned max S = 0.812; of the best S among no-harm cells WITHOUT the mean gate (real +0.142) = 0.040; null of unconditioned max S: median +0.409, 95th pct +0.501 (n = 100 worlds). Reading: no day-shuffled world has a cell that keeps the mean at or above the live ladder (the shuffle removes the ER signal's contribution to the mean), so the eligibility gate alone separates the real lead from the null; the drawdown cut S by itself is NOT unusual under shuffling (a random multiplier vector with this distribution reaches an S as high as the real best in most worlds).

**(3) Which tier carries the gain (lead ER20 expanding (1/3,2/3) h .05):**

| variant | cut L6M | HOLD | MID | PRE | X' | drop L6M | drop PRE | mean $/wk vs live |
|--|--|--|--|--|--|--|--|--|
| lead x0.5 / x1.0 / x1.5 | +0.31 | +0.19 | -0.11 | -0.02 | -0.03 | -0.02 | +0.31 | +138 |
| x0.5 replaced by x1.0 (1/1/1.5) | +0.22 | -0.14 | -1.38 | +0.10 | -0.32 | -0.05 | +0.10 | +875 |
| x1.5 replaced by x1.0 (0.5/1/1) | +0.53 | +0.22 | -0.25 | +0.47 | +0.06 | +0.20 | +0.47 | -4982 |

Reading: the drawdown gain sits in the x0.5 (down-size) tier and is paid for in mean; the x1.5 tier is what carries the mean.

**(1) Exact equal-risk mean (11-point lscale scan, linear fits; lot scale c at which the cell's fitted maxDD equals the live ladder's) for the lead and the top-30 ts re-screen cells; mean gain = mean at equal risk - live mean (fitted), $/wk:**

| cell | c L6M | gain L6M | c PRE | gain PRE | c X' | gain X' |
|--|--|--|--|--|--|--|
| ('g13', 'ers_30m_20', 1, 'LIN', 'B') | 2.51 | +69190 | 0.96 | +776 | 0.76 | +1049 |
| ('g13', 'ers_30m_20', 1, 'SIG', 'B') | 2.21 | +56233 | 0.94 | +755 | 0.74 | +994 |
| ('g13', 'ers_30m_20', 1, 'L5', 'B') | 1.97 | +40835 | 1.01 | +3671 | 0.66 | +505 |
| ('g13', 'ers_5m_20', 1, 'L5', 'A') | 1.63 | +27030 | 1.17 | +3666 | 0.94 | +503 |
| ('g12', 'er_15m_10', 'L3', 'D') | 1.67 | +23251 | 1.11 | +4183 | 0.92 | +1241 |
| ('g13', 'ers_5m_20', 1, 'LIN', 'B') | 1.38 | +27016 | 0.87 | +65 | 0.89 | +2724 |
| ('g13', 'ers_15m_20', 1, 'L3', 'A') | 1.39 | +23825 | 1.09 | +2621 | 1.00 | +2063 |
| ('g12', 'er_30m_10', 'L5', 'D') | 1.51 | +17768 | 1.19 | +5918 | 0.70 | -980 |
| ('g12', 'er_10m_14', 'L3', 'D') | 1.33 | +14402 | 1.24 | +5919 | 0.81 | -225 |
| ('g12', 'er_1m_100', 'LIN', 'D') | 1.46 | +16509 | 1.13 | +3727 | 0.48 | -2561 |
| ('g12', 'er_1m_100', 'SIG', 'D') | 1.50 | +16100 | 1.13 | +4029 | 0.53 | -2098 |
| ('g13', 'ers_10m_20', 1, 'LIN', 'B') | 1.11 | +12510 | 1.18 | +6992 | 0.83 | -815 |
| ('g12', 'er_10m_14', 'LIN', 'B') | 1.22 | +13434 | 1.14 | +5274 | 0.81 | +317 |
| ('g12', 'er_10m_14', 'SIG', 'B') | 1.21 | +11719 | 1.16 | +5899 | 0.86 | +1012 |
| ('g12', 'er_5m_20', 'LIN', 'D') | 1.36 | +13002 | 1.18 | +4577 | 0.51 | -1993 |
| ('g12', 'er_30m_10', 'L3', 'D') | 1.33 | +11407 | 1.13 | +6024 | 0.61 | -1425 |
| ('g12', 'er_15m_10', 'L5', 'D') | 1.45 | +14220 | 1.06 | +2271 | 0.89 | +1083 |
| ('g12', 'er_10m_10', 'LIN', 'B') | 1.36 | +16130 | 0.91 | -441 | 0.66 | -1385 |
| ('g12', 'er_30m_10', 'LIN', 'B') | 1.15 | +11060 | 1.00 | +4218 | 0.76 | -251 |
| ('g13', 'ers_5m_20', 1, 'L3', 'A') | 1.39 | +14140 | 1.02 | +1038 | 1.10 | +4255 |
| ('g12', 'er_15m_10', 'LIN', 'D') | 1.36 | +12639 | 1.06 | +2357 | 0.62 | -1198 |
| ('g13', 'ers_5m_20', 1, 'L5', 'D') | 1.25 | +8731 | 1.27 | +6065 | 0.81 | +171 |
| ('g13', 'ers_10m_20', 1, 'SIG', 'B') | 1.02 | +8963 | 1.14 | +5344 | 0.85 | -530 |
| ('g13', 'ers_10m_20', 1, 'L3', 'D') | 1.29 | +12701 | 1.01 | +1122 | 0.88 | +978 |
| ('g12', 'er_1m_100', 'L3', 'D') | 1.37 | +11623 | 1.07 | +1588 | 0.77 | +63 |
| ('g14', 'er_5m_20', 'hyst', 'L3') | 1.41 | +11851 | 0.99 | +565 | 1.02 | +1178 |
| LEAD ER20 hysteresis | 1.41 | +11851 | 0.99 | +565 | 1.02 | +1191 |
| ('g12', 'er_1m_100', 'L3', 'A') | 1.25 | +8296 | 1.13 | +2215 | 1.16 | +2532 |
| ('g12', 'er_5m_20', 'L5', 'D') | 1.12 | +5111 | 1.23 | +4659 | 0.78 | -442 |
| ('g12', 'er_10m_20', 'L3', 'D') | 1.20 | +7549 | 1.01 | +894 | 0.86 | +929 |
| ('g14', 'er_5m_14', 'min3', 'L3') | 1.15 | +5510 | 1.05 | -268 | 1.00 | +1668 |

**Exposure (exposure_table):** lead mean lots 3.14 / max 11; live ladder 3.01 / 11. Worst net signed NQ lots across books: lead 28 (20240926), live 28 (20240220); worst stack risk lead $33,600, live $33,600. The lead does not change the worst-case exposure.


## SIZER_S3X_STRESS addendum 6: what the lot-scaled formula really does (2026-11-02T21:47Z) POST-HOC, no PASS, Shadow only
Prereg l2vast/ds3/prereg/SIZER_S3X_Z1_addendum6_prereg.md sha256 3bbd38ba9643ae7b977d29632c4dd5dbe05a9317eb0484829731846e718307d2 (DECISIONS.md before scoring). Positive = smaller drawdown vs the T-SIZER base (run_v13t_ts + HALF), live arm 30 elsewhere. Formula F arms: lots 1-4 -> 40, lots 6 -> 29, lots 11 -> 20 (all books; the 11-lot rows are PE only). Check: rule cell T (40/29/20 by those buckets) reproduces F exactly (max daily diff 0.00).
Formula cell F (ALL, ER-multiplied lots, X=3500)
| cell | PA cut L6M / HOLD / MID / PRE / X' | episode dropped L6M / PRE | S1 | mean d L6M / PRE $k/wk (MDE) | P&L d $k |
|---|---|---|---|---|---|
| F full | +5% / +5% / -11% / +11% / +12% | +27% / +32% | 0.116 | -3.1 (13.8) / -1.9 (7.4) | -60 |
| F only at lots=1 (arm 40) | +8% / +8% / +8% / -2% / -9% | -6% / +1% | -0.055 | +0.6 (2.8) / -0.2 (1.4) | -13 |
| F only at lots=2 (arm 40) | -4% / -4% / +10% / +2% / +3% | +5% / -1% | 0.022 | -0.7 (2.4) / +0.9 (1.4) | +99 |
| F only at lots=3 (arm 40) | +9% / +9% / -8% / -1% / +3% | +2% / +6% | 0.011 | +0.1 (4.8) / +0.4 (2.1) | +125 |
| F only at lots=4 (arm 40) | -10% / -10% / +35% / -2% / -0% | -17% / -4% | -0.010 | -2.8 (5.2) / +0.6 (2.2) | +117 |
| F only at lots=6 (arm 29) | +2% / +2% / -19% / +1% / -0% | +2% / +1% | 0.004 | -0.3 (1.7) / -0.2 (0.7) | -45 |
| F only at lots=11 (arm 20) | -8% / -8% / +9% / +4% / +5% | +20% / +24% | 0.044 | -2.5 (12.9) / -3.9 (6.5) | -488 |
| I40 | -3% / -3% / +31% / +0% / -4% | -12% / +6% | -0.017 | -3.8 (8.3) / +1.7 (3.6) | +319 |
| I29 | +2% / +2% / -19% / +1% / -0% | +2% / +1% | 0.004 | -0.3 (1.7) / -0.2 (0.7) | -45 |
| I20 | -8% / -8% / +9% / +4% / +5% | +20% / +24% | 0.044 | -2.5 (12.9) / -3.9 (6.5) | -488 |
| P4029 | +0% / +0% / +18% / +1% / -2% | -10% / +8% | -0.001 | -4.1 (8.4) / +1.6 (3.6) | +274 |
| P4020 | +2% / +2% / +12% / +10% / +7% | +25% / +30% | 0.085 | -2.7 (13.3) / -1.7 (7.3) | -15 |
| P2920 | -6% / -6% / -7% / +5% / +3% | +22% / +26% | 0.040 | -2.8 (13.3) / -4.1 (6.6) | -533 |
| T | +5% / +5% / -11% / +11% / +12% | +27% / +32% | 0.116 | -3.1 (13.8) / -1.9 (7.4) | -60 |
| I40pe | -10% / -10% / +33% / -1% / -1% | -17% / -3% | -0.010 | -2.8 (5.5) / +0.5 (2.2) | +115 |
| I29pe | +0% / +0% / +0% / +0% / -2% | +0% / +0% | -0.008 | +0.1 (0.1) / +0.1 (0.1) | +4 |
| I20pe | -8% / -8% / +9% / +4% / +5% | +20% / +24% | 0.044 | -2.5 (12.9) / -3.9 (6.5) | -488 |
check T == F: max abs daily diff 0.00
| cell | kind (n) | rank PA PRE | rank PA X' | rank L6M-dropped | rank PRE-dropped |
|---|---|---|---|---|---|
| PE-R1n (real -6% / +6% / +8% / +16%) | A (100) | 0.515 | 0.188 | 0.010 | 0.010 |
| PE-R1n (real -6% / +6% / +8% / +16%) | B (100) | 0.465 | 0.139 | 0.010 | 0.010 |
| PE-R1n (real -6% / +6% / +8% / +16%) | C (100) | 0.574 | 0.257 | 0.020 | 0.010 |
| PE-R2n (real -9% / -2% / +15% / +16%) | A (100) | 0.564 | 0.594 | 0.010 | 0.059 |
| PE-R2n (real -9% / -2% / +15% / +16%) | B (100) | 0.525 | 0.594 | 0.010 | 0.030 |
| PE-R2n (real -9% / -2% / +15% / +16%) | C (100) | 0.554 | 0.683 | 0.020 | 0.099 |
| cell | kind (n) | rank PA PRE | rank PA X' | rank L6M-dropped | rank PRE-dropped |
|---|---|---|---|---|---|
| P4020 (real +10% / +7% / +25% / +30%) | A (100) | 0.010 | 0.020 | 0.139 | 0.020 |
| P4020 (real +10% / +7% / +25% / +30%) | B (100) | 0.010 | 0.010 | 0.010 | 0.010 |
| P4020 (real +10% / +7% / +25% / +30%) | C (100) | 0.010 | 0.010 | 0.040 | 0.010 |
| I20 (real +4% / +5% / +20% / +24%) | A (100) | 1.000 | 1.000 | 1.000 | 1.000 |
| I20 (real +4% / +5% / +20% / +24%) | B (100) | 1.000 | 1.000 | 1.000 | 1.000 |
| I20 (real +4% / +5% / +20% / +24%) | C (100) | 0.208 | 0.386 | 0.020 | 0.040 |

Note: for single-valued cells (I20) placebos A (permute) and B (iid from marginal) are degenerate (every draw equals the cell, rank 1.000); only kind C is informative there. Extra placebos for P4020 and I20 were run because both had PA PRE and X' cuts > 0 (prereg item C).

Frames for P4020 (arm 40 at lots <= 4 plus arm 20 at 11 lots), each vs its own base: V13T2 kfix PA cut L6M/HOLD/MID/PRE/X' +8/+8/+15/+7/+1%, dropped L6M/PRE +14/+30%, mean d -2.9k (MDE 12.6) / -1.9k (7.0), P&L -5k; single rounding +1/+1/+13/+11/+11%, dropped +25/+32%, mean -2.4k (12.7) / -1.7k (7.3), P&L -6k.

### What the formula really does (one paragraph)
The formula is two opposite moves that happen to net to about zero P&L. (1) It tightens the 11-lot PE rows (ER >= 0.30 on the biggest PE size) from arm 30 to arm 20: this alone (I20) gives PA PRE +4%, X' +5%, episode-dropped L6M +20% / PRE +24%, but costs $488k of total P&L (mean -2.5k/-3.9k per week, inside the MDE); it is the part that buys the carrying-episode drawdown cut and it is the same mechanism as the dead fixed arm 25 (which cost $474k). (2) It loosens all rows of 1-4 lots (all six books; PE 2- and 4-lot rows, KB/MV/PB/HM/SM 1-3) from 30 to 40: this alone (I40) cuts no drawdown (PA PRE 0%, X' -4%) but earns +$319k, i.e. it pays for the tightening. The 29 at 6 lots is nearly irrelevant (I29: PA PRE +1%, X' 0%, P&L -$45k, almost all HM/SM rows; PE-only I29 does nothing). The two big parts are not additive: I40+I20 (P4020) gives PA PRE +10%, X' +7%, dropped +25%/+30% at -$15k P&L, vs the sum of singles of PA PRE +4%; adding the 29 at 6 lots (the full formula F) adds PA PRE +1 point and X' +5 points for -$45k. P4020 beats all three placebos on PA PRE, PA X' and the dropped cuts (ranks 0.010-0.04, except A on L6M-dropped 0.139); I20 alone is only informative against C (ranks 0.21/0.39 on PA, 0.02/0.04 on dropped), i.e. its PA gain is chance level and its dropped-episode gain is real but expensive. The fixed rules PE-R1n (25 at 11 lots) and PE-R2n (22 at 11 lots) are the same tightening without the loosened small-lot rows: they beat all three placebos on the episode-dropped cuts (ranks 0.010-0.099) but are at chance on PA PRE/X' (ranks 0.14-0.68) and lose $244k/$474k, which is why they die. So the contradiction resolves as: the fixed rule died because it only had the costly half; the formula's PRE/X' result needs both halves, and the loosening at 1-4 lots is what makes the tightening affordable. Caveats: P4020 is selected after seeing the decomposition (best of 7 isolating cells, not adjusted in the null), PA L6M is only +2% (below the PA9 band .165), kfix X' is +1%, the loosening depends on lots 1-4 being 90%+ of the trade count, and the walk-forward on X/clip from the stress test is unchanged (formula parameters still unstable).


## SIZER_S3X_STRESS addendum 7: pricing the selection of P4020, out-of-time, neighbours (2026-11-02T22:01Z) POST-HOC, no PASS, Shadow only
Prereg l2vast/ds3/prereg/SIZER_S3X_Z1_addendum7_prereg.md sha256 e410702e84b0dc732b66adfc9fe9ea77e1f0287f3d62fa03b10045562d7e81d7 (DECISIONS.md before scoring). Spec: autopilot/SIZER_LOT_ARM_SPEC.md.
(1) Selection-aware null, 100 shuffled-day worlds, whole procedure repeated (best of 16 grid cells by S1 -> decomposition into arm-value groups -> every pair, 4.7 pairs per world on average -> max over pairs). Real: best grid cell by S1 is the formula cell (X=3500, ALL, no ER filter), its pairs P4029 -0.001, P4020 0.085, P2920 0.040 -> real M1 = S1(P4020) = 0.085, M2 = S2(P4020) = 0.251. Null M1 (S1 = mean of PA PRE and PA X' cuts): median 0.007, 95th 0.090, max 0.101 -> rank 0.119. Null M2 (S2 = min of L6M and PRE cuts with carrying episodes dropped): median 0.055, 95th 0.146, max 0.181 -> rank 0.010. So after pricing the selection the PA score is NOT below the 0.10 rank used in the flag rule (0.119), and the episode-dropped score still is (0.010).
(2) Rolling out-of-time (nothing fitted; weekly-cumulative maxDD restarted at each period start, ISO weeks, base vs P4020):
| period | days | base maxDD $ | P4020 maxDD $ | d maxDD $ | d % | d P&L $ | days with a change |
|---|---|---|---|---|---|---|---|
| 2023 | 195 | 72805 | 67051 | -5754 | -7.9% | +80697 | 190 |
| 2024 | 262 | 155639 | 150300 | -5339 | -3.4% | +10833 | 255 |
| 2025 | 261 | 160713 | 111996 | -48718 | -30.3% | -135300 | 258 |
| 2026 | 217 | 170420 | 166273 | -4147 | -2.4% | +28962 | 216 |
| --- quarters --- | | | | | | | |
| 2023Q2 | 65 | 49771 | 67051 | +17281 | +34.7% | +5985 | 64 |
| 2023Q3 | 65 | 66067 | 58383 | -7684 | -11.6% | -15068 | 64 |
| 2023Q4 | 65 | 72805 | 41339 | -31467 | -43.2% | +89780 | 62 |
| 2024Q1 | 65 | 62500 | 74257 | +11757 | +18.8% | +29608 | 63 |
| 2024Q2 | 65 | 84950 | 84806 | -144 | -0.2% | -40542 | 61 |
| 2024Q3 | 66 | 155639 | 150300 | -5339 | -3.4% | +16129 | 66 |
| 2024Q4 | 66 | 27007 | 33696 | +6689 | +24.8% | +5639 | 65 |
| 2025Q1 | 64 | 160713 | 111996 | -48718 | -30.3% | +64793 | 63 |
| 2025Q2 | 65 | 85440 | 74564 | -10877 | -12.7% | -194428 | 64 |
| 2025Q3 | 66 | 92770 | 97014 | +4244 | +4.6% | -6266 | 66 |
| 2025Q4 | 66 | 46313 | 37133 | -9180 | -19.8% | +601 | 65 |
| 2026Q1 | 64 | 130381 | 60740 | -69641 | -53.4% | +81414 | 63 |
| 2026Q2 | 65 | 36551 | 36349 | -202 | -0.6% | -108954 | 65 |
| 2026Q3 | 66 | 170420 | 166273 | -4147 | -2.4% | +31584 | 66 |
| 2026Q4 | 22 | 93094 | 69702 | -23392 | -25.1% | +24918 | 22 |
| --- halves --- | | | | | | | |
| first half to 20250115 | 468 | 155639 | 150300 | -5339 | -3.4% | +135653 | 455 |
| second half from 20250116 | 467 | 170420 | 166273 | -4147 | -2.4% | -150461 | 464 |
| all | 935 | 170420 | 166273 | -4147 | -2.4% | -14808 | 919 |
Reading: the drawdown improvement is not stable by calendar: yearly maxDD changes -7.9 / -3.4 / -30.3 / -2.4% (2023..2026), quarterly it is worse in 2023Q2 (+35%), 2024Q1 (+19%), 2024Q4 (+25%), 2025Q3 (+5%) and better in 8 of the 15 quarters; the whole-period ISO maxDD change is only -2.4% ($170,420 -> $166,273). P&L: +$136k in the first half (to 2025-01-15), -$150k in the second half, -$15k overall (2025Q2 -$194k, 2026Q2 -$109k, 2023Q4 +$90k, 2026Q1 +$81k). The two halves have maxDD -3.4% / -2.4%, i.e. the cut is small in both and carried by a few quarters (2025Q1, 2026Q1, 2023Q4).
(3) Neighbours (arm at lots <= 4 x arm at 11 lots; 6-lot rows live 30; P4020 = 40/20):
| arm lots<=4 | arm 11 lots | PA cut L6M / HOLD / MID / PRE / X' | episode dropped L6M / PRE | S1 | mean d L6M / PRE $k/wk (MDE) | P&L d $k |
|---|---|---|---|---|---|---|
| 35 | 18 | +11% / +11% / +2% / +11% / +10% | +16% / +29% | 0.110 | -2.1 (16.4) / -2.9 (7.0) | -320 |
| 35 | 20 | -1% / -1% / -1% / +7% / +6% | +14% / +22% | 0.067 | -2.0 (13.4) / -3.2 (6.7) | -353 |
| 35 | 22 | -18% / -18% / +9% / +1% / -3% | +9% / +17% | -0.012 | -5.6 (13.6) / -3.1 (6.5) | -373 |
| 35 | 25 | -7% / -7% / +9% / -8% / +1% | +6% / +13% | -0.036 | -2.9 (10.5) / -2.0 (5.0) | -163 |
| 40 | 18 | +18% / +18% / +19% / +13% / +10% | +28% / +36% | 0.119 | -2.3 (15.8) / -1.2 (7.7) | +23 |
| 40 | 20 | +2% / +2% / +12% / +10% / +7% | +25% / +30% | 0.085 | -2.7 (13.3) / -1.7 (7.3) | -15 |
| 40 | 22 | -14% / -14% / +29% / +3% / -5% | +3% / +25% | -0.007 | -7.7 (13.0) / -1.6 (7.0) | -99 |
| 40 | 25 | -18% / -18% / +31% / -5% / -2% | -1% / +22% | -0.036 | -5.5 (10.6) / -0.3 (5.6) | +119 |
| 45 | 18 | +20% / +20% / +14% / +20% / +1% | -10% / +43% | 0.109 | -3.6 (15.6) / -1.4 (8.1) | -45 |
| 45 | 20 | -2% / -2% / +18% / +16% / -8% | -12% / +36% | 0.043 | -4.9 (12.8) / -1.9 (7.7) | -118 |
| 45 | 22 | -15% / -15% / +27% / +11% / -6% | -17% / +30% | 0.023 | -8.2 (12.3) / -1.6 (7.3) | -122 |
| 45 | 25 | -20% / -20% / +27% / +2% / -25% | -21% / +28% | -0.116 | -5.7 (10.7) / -0.5 (6.0) | +91 |
Reading: not a symmetric plateau. In the 11-lot arm it is a ramp: 18 is as good or better than 20 on PA PRE/X' (40/18: +13%/+10%, dropped +28/+36%, P&L +$23k), 22 and 25 lose the PA gain (PA L6M -14..-18%) and keep only the PRE episode-dropped cut. In the lots<=4 arm 35, 40, 45 all keep PRE (+7..+20%) but 35 costs more P&L (-$320k..-$373k at 11-lot arm 18-22 versus -$15k..+$23k for 40), 45 flips L6M-dropped to -10..-21%. The cell is on a ramp whose good side is a tighter 11-lot arm (18-20) with the 40 at small lots; it is not robust to a looser 11-lot arm.
Verdict: the flag stays LEAD with qualifiers but is downgraded: selection-aware null rank on the PA score 0.119 (> 0.10), out-of-time quarterly improvement unstable (8 of 15 quarters), neighbours a ramp. The episode-dropped score (rank 0.010) remains.

- 2026-11-02T22:01Z Z1 CORRECTION to the line above and DS3_SIZER.md addendum 7: P4020 quarterly maxDD is better than base in 11 of 15 quarters (worse in 4: 2023Q2 +35%, 2024Q1 +19%, 2024Q4 +25%, 2025Q3 +5%), NOT 8 of 15. The out-of-time reading is therefore: mostly positive by quarter, but small overall (-2.4% whole period) and carried by 2023Q4, 2025Q1, 2026Q1; P&L swings +136k / -150k between halves. Downgrade rests on selection-aware PA rank 0.119 and the ramp neighbours.

### SIZER_S1B family-wise null UPDATE (Z2, 22:10Z): 62 worlds (target 100 NOT reached; 3 engine workers, ~12-20 worlds/h)
Worlds = ER permuted within book x session x side (115 KB/PE cells rerun per world, same clean test). Real: 8 clean KB/PE cells, best single-cell score 20.8, C1 cuts L6M 29.8 / PRE 19.3. Null: mean clean cells 4.35, P(n_clean >= 8) = 0.145, P(>=1 clean) = 0.89; null best-cell score median 21.6, p90 32.2, P(>= real 20.8) = 0.45; null combined-rule (55 worlds with a rule) L6M cut median 30.8 / p90 55.1, PRE median 16.6 / p90 26.6; P(L6M >= 29.8) = 0.45, P(L6M and PRE both >= real) = 0.32. Family-wise p about 0.15-0.45 on every statistic: the clean cells and the combined KB+PE rule are indistinguishable from a signal-free sizer. Conclusion stands: combined rule not supported, ER sizer KEEP, nothing is a PASS, B02 still a PROXY. Limitation: 62 (not 100) worlds, null restricted to the 115 KB/PE cells (not all 616), permuted-ER rather than literal shuffled-day multiplier worlds (day-shuffled and AR(1) placebos for C1 were run separately at 100 draws each, ranks .13-.45).

## PA9 phase audit across sizer programs + S1B ledger append (Z2, 2026-11-02 ~23:45Z)
Test (code s1b/pa_verify.py): one cell (PE london t0.25 0.5/1.0) run at engine phases 0,1,2,3,4,-3 through each program's own harness; compare daily cores to phase 0.
- ts mode (run_v13t_ts; lock none, lock R scaled only upward): engine phase is a NO-OP (max core diff 0 $ for 4 of 6 phases, 1,249 $ at phases 2/-3 = one leg). Weekly maxDD under the SAME core but a shifted SCORING week key varies strongly (L6M 113k..136k over s=0..4), so a real PA9 needs the scoring shift (s1b_pa2.py).
- single mode (run_v13t_live / V13T_LIVE, lock reset on week key): engine phase is real, period 5 (phases -4..+4 give 5 distinct runs; 1 and -4, 2 and -3 etc. identical), core diffs 27-32k $.
Verdict per program (what the PA9 column in each report is):
- S1 (S4a, sizer_harness_s4a, run_v13t_live): REAL lock-reset PA9 (5 distinct phases, each counted ~twice).
- S2 (S4b, sizer_harness_s2 default HARNESS_MODE ts, S.H.pa9): NOT real; the PA9 columns (e.g. in the DS3_SIZER.md S4b section, top_pa9) equal the phase-0 result. top_pa9.pkl in sizer_s2ts is also an empty file (0 bytes).
- S2V (ZL-1, sizer_s2v harness, default ts): NOT real; all 29 pa9_*.pkl have SD 0.0 on every window (and presumably hybpa9_/meanpa9_ likewise).
- Q1 (ZL-2): s2 stage in ts mode has SD 0 and the report says so ("moot on this base"); the real lock-reset PA9 is the s2s stage in single mode (SD 3-7 L6M), already used in section 9. OK.
- Q2/Q3/Q4 (ZL-2): placebos at phases=(0,) and no PA9 claim; nothing to correct.
- S1B (Z2): was not real, corrected above (scoring-shift PA9 in pa2.pkl).
Note the two PA9 notions are different: single-mode PA9 = lock-reset phase (a real mechanism, engine lock), ts-mode scoring-shift PA9 = weekly bucket phase. Owners of S2 and S2V should either relabel their PA9 columns "single-phase (phase 0)" or recompute with the scoring-week-key shift (F.WK = WK0[clip(arange(ND)+s)], s=-4..4 on one engine run; see s1b/s1b_pa2.py).
Ledger: SIZER_S1B appended to DEAD_CELLS.csv after dead_lookup (6 representative specs, 0 hits, log out/zones3/s2/s1b_deadlookup.log): 616 cells + C1/C2 = 618 rows (program SIZER_S1B, side sizing, tier SCORED; val_L6M/HOLD/PRE/X = single-phase cut %, val_other = MID; genuine PA9 in `extra` for the 40 screened cells and C1/C2). B02-related cells (E|R3, fam E) carry the PROXY label in the report, key names only.


## CORRECTION BLOCK (ZL-1, 2026-11-03 ~00:30Z): GENUINE PA9 for SIZER_S2V, SIZER_S2V_HYBRID and SIZER_S2V_MEAN (replaces the 'PA9' columns above)
Cause (Z2 audit): on the ts base the engine week key does nothing, so the 29 + 3 + 3 harness `pa9_*`/`hybpa9_*`/`meanpa9_*` results equalled phase 0 (SD 0.0 on every window). The statements 'N cells beat the PA9 band', every 'PA9' column and every 'passes PA9/no-harm' above are therefore SINGLE-PHASE band comparisons. Recomputed here as in s1b_pa2.py: one engine run per cell (phase 0, ts base, sequential rounding), SCORING week key shifted -4..+4 (index shift, clipped), mean cut over the 9 shifts vs the live ladder shifted the same way; band = V13T PA9 band, flip 2% (L6M 18.8, HOLD 18.2, MID 21.2, PRE 7.8, X' 14.5), flip 5% (21.9 / 20.5 / 32.2 / 9.9 / 18.2); pass2 = L6M > band and (PRE > band or X' > band); no-harm = PA9 PRE, MID, X' not below -band2; carry-dropped = PA9 with the carrying weeks dropped (L6M 2026 W27-38, PRE 2024 W34-51). Cells: 29 S2V finalists, all 28 HYBRID, all 17 MEAN. File: ds3_zones3_new/sizer_s2v/patrue_all.csv (+ patrue_*.pkl; SD and positive-shift counts per window); code zones3/sizer_s2v/s2v_patrue.py, s2v_patrue_an.py. The placebo ranks above are PHASE-0 placebos (the harness placebos default phases=(0,)) and are unchanged; they are not affected by this bug.
**Counts, corrected.** S2V (29 finalists): 9 beat the band in L6M and PRE (was 27 of the 99 at phase 0, all inside the 29); 9 pass2; 19 no-harm; 8 both-band and no-harm (was 10 eligible + both + no-harm at phase 0). HYBRID (28): 13 pass2, 10 no-harm, 4 both-band and no-harm. MEAN (17): 2 pass2, 13 no-harm, 1 both-band and no-harm. SD across the 9 shifts is 1-11 points (L6M), so the earlier 'SD 0.0' was spurious; all cells have the cut positive in 9 of 9 shifts (L6M and PRE) except as listed in the csv.
**S2V rows that change (phase-0 -> genuine PA9; L6M / PRE / MID / X'):**
| cell | phase-0 (old 'PA9') | genuine PA9 | pass2 old -> new | no-harm old -> new |
|--|--|--|--|--|
| VT 0.75 FULL (INV) | 42.7 / 19.8 / 31.0 / -29.8 | 35.1 / 30.5 / 41.4 / -0.9 (carry-dropped 45.8 / 20.0) | T -> T | F -> **T** |
| VT 0.75 DOWN (INV) | 43.5 / 24.1 / 31.4 / -26.5 | 35.6 / 32.5 / 40.7 / -5.2 (45.8 / 24.1) | T -> T | F -> **T** |
| VT 1.0 DOWN (INV) | 43.4 / 15.7 / 16.2 / -14.4 | 28.9 / 19.8 / 17.8 / -6.2 (34.0 / 15.7) | T -> T | T -> T |
| VT 1.0 FULL (INV) | 58.9 / 16.1 / 28.5 / -27.6 | 39.9 / 22.2 / 21.6 / -15.5 (33.6 / 13.0) | T -> T | F -> F (X' -15.5 vs -14.5) |
| rv_ratio_30m SIG DOWN DIR (the 'flag' cell) | 35.5 / 16.1 / 14.5 / 18.4 | 20.9 / 11.7 / 18.1 / 23.4 (carry-dropped **5.5 / 4.8**) | T -> T | T -> T |
| dayrange_atrd SIG DOWN DIR | 38.9 / 17.9 / -5.1 / 18.1 | 29.1 / 21.5 / 14.0 / 27.5 (12.1 / 24.2) | T -> T | T -> T |
| atr_ratio_5m SIG DOWN DIR | 49.3 / 16.0 / 35.8 / 16.7 | 29.3 / 19.8 / 25.7 / 22.6 (20.9 / 12.7) | T -> T | T -> T |
| atr_ratio_5m LIN FULL DIR / LIN DOWN DIR | 39.3 / 13.9 and 39.3 / 11.7 | 18.6 / 16.5 and 18.6 / 17.5 | T -> **F** (L6M 18.6 < 18.8) | T -> T |
| atr_ratio_5m L3 FULL DIR | 45.6 / 9.0 / 21.3 / 19.0 | 15.0 / 15.3 | T -> **F** | T -> T |
| rv_ratio_30m LIN DOWN DIR, LIN FULL DIR, SIG FULL DIR | 23.8, 23.3, 32.7 (L6M) | 9.2, 8.4, 17.7 | T -> **F** (all three) | T -> T |
| dayrange_atrd SIG DOWN INV, SIG FULL INV; range_so_far_ratio SIG DOWN INV | L6M 28.4 / 32.2 / 26.6 | 16.3 / 14.8 / 15.6 | T -> **F** | F -> F (X' -17 to -24) |
| rv_ratio_30m L3 FULL INV, SIG FULL INV, SIG DOWN INV, L3 DOWN INV; pk_ratio_20d SIG FULL INV | no-harm F | no-harm **T** (X' -14.2 .. +4.8 with L6M 8-15, pass2 F) | F -> F | F -> **T** |
All 17 rows with a changed pass2 or no-harm flag are in patrue_all.csv (old_* columns). Reading: the genuine PA9 lowers most L6M cuts (the phase-0 L6M cut was carried by one alignment of the week key), lifts the X' value of the vol-target cells (-26..-30 -> -1..-6, so they are no longer 'harm' in X'), and keeps the DIR cells passing but with a much thinner carry-dropped cut (rv_ratio_30m SIG DOWN DIR: 5.5 / 4.8).
**HYBRID (x1.5 quiet-vol cap, all books) genuine PA9, top rows:** VT th=1.0 X=0.75: 45.2 / 25.1 / MID 11.9 / X' -21.9 (was 63.0 / 23.3 / -48.8), pass2 T, no-harm F; th=1.1 X=0.75: 44.3 / 32.9 / 14.6 / -21.2 (was 64.2 / 33.5 / -45.4), no-harm F; th=1.25 X=0.75: 29.2 / 31.8 / 17.1 / **-13.5** (was 44.3 / 36.0 / -33.0), pass2 T, **no-harm T (X' -13.5 vs -14.5)**, carry-dropped 29.3 / 21.1; th=1.1 X=1.0: 36.4 / 25.1 / 9.4 / -13.9, no-harm T (carry-dropped 18.4 / 14.8); th=1.0 X=1.0: 29.0 / 20.1 / 7.9 / -13.7, no-harm T (35.6 / 11.3); rv_ratio_30m q .33 X=1.0: 32.0 / 22.1 / 5.8 / -10.0, no-harm T. So the statement 'EVERY hybrid cell harms X' is a phase-0 statement: at genuine PA9 four hybrid cells are no-harm (X' -10 to -14, at the band edge). They are still lot reductions (total -353k to -828k, mean lots 2.5-2.8; phase-0 placebo ranks L6M .30-.93, PRE .34-.62 as reported) and still fail the same-or-better-mean standard.
**MEAN (PE-only / mild / compensation) genuine PA9:** PE a=1.0 X=0.75: 32.9 / 11.6 / 20.3 / -14.9 (was 52.7 / 7.6 / -34.2; now passes PRE band, no-harm F by 0.4); PE a=0.9 X=0.75: 30.0 / 17.9 / 22.8 / -10.5, pass2 T, no-harm T, but carry-dropped L6M **-8.5** (so not 'beats with carrying week dropped'), PRE mean -4.4k/wk; CALL a=1.0 (exposure-failed): 28.2 / 6.8 / 8.1 / -26.7, pass2 F. The other MEAN cells have L6M PA9 <= 16.6 (fail the band). Conclusions of the MEAN section (no strict mean-keeping cut) are unchanged.
**FLAGS, re-judged (prereg rule: beats the ladder on L6M and PRE with the carrying week dropped, no-harm at PA9, eligible on mean; cells are NOT mean-keeping: mean lots 2.3-2.5, total -0.8 to -1.0M):** still met by rv_ratio_30m SIG DOWN DIR (weaker: carry-dropped PA9 5.5 / 4.8 instead of 'cut 10.4 / 32.8'), dayrange_atrd SIG DOWN/FULL DIR, atr_ratio_5m SIG DOWN/FULL DIR; NEWLY met by the vol-target cells VT 0.75 DOWN / FULL (PA9 35.6 / 32.5 / 40.7 / -5.2 and 35.1 / 30.5 / 41.4 / -0.9; carry-dropped 45.8 / 24.1 and 45.8 / 20.0; total -822k / -791k; phase-0 placebo ranks L6M .32-.41 and PRE .30-.46, i.e. a lot reduction) and by VT 1.0 DOWN (28.9 / 19.8 / 17.8 / -6.2; carry-dropped 34.0 / 15.7). The old statement that the vol-target FULL cells fail no-harm is a phase-0 result. MORNING_FLAGS.md gets a corrected line; the formal flag is still caveated (lot cut, placebo ranks, equal-risk PRE mean below the ladder 14.8-16.1k vs 17.8k, best-of-99).

# S4b SECTION 2 - PA9 CORRECTION (genuine phase-averaged cuts; written 22:45Z)
Z2's audit is right: on the TS base the engine week-key phase does nothing, so the harness `pa9` / 'PA9' columns in section 2 above (2.1, the top-6 table and the placebo ranks) equal the phase-0 single path. Genuine PA9 now: one engine run per cell (stored cores), the SCORING week key shifted -4..+4 label days (template zones3/s1b/s1b_pa2.py), cut = mean over the 9 shifts of the per-shift maxDD cut vs the TS reference at the same shift; the equal-risk cuts use the lot factor c of each shift; applied to ALL 2,148 section-2 cells (2,128 + 20 weekday), the 26 add cells and the 4 exposure cells (code zones3/s4b/pa9_fix.py, pa9_pool.py, pa9_plc.py). Band = V13T PA9 flip-5 (L6M .219, HOLD .205, MID .322, PRE .099, X' .182); no-harm = PRE >= -.099, MID >= -.322, X' >= -.182.
## Re-judged with genuine PA9
* **Cells: 2,148; beyond the band 651; band + no-harm 213; band + no-harm + mean kept (L6M and HOLD mean change >= 0): 1.** The one cell is the GATE `pulled_ahd10` direction -1 'GU1' (the live x1.5 is kept only where the 10-s pulled-liquidity-ahead mult is NOT in its top third... i.e. 1 - rank >= 1/3): PA9 cuts L6M +32.9% / HOLD +23.6% / MID +2.9% / PRE +10.8% / X' -13.8%, mean +0.8k/wk L6M, -2.4k/wk PRE; carrying-week and phase SD 2.3%; placebos (3 kinds x 100, PA9-scored, share of placebos below the real cut; high = real beats): L6M 0.39 / 0.35 / 0.29, PRE 0.53 / 0.50 / 0.53, X' 0.87 / 0.85 / 0.83 (the means beat the placebos 0.98-1.00): the cut is at chance level. NOT A LEAD.
* **Weekday x0.75 on Wed+Thu:** PA9 L6M +39.9 / HOLD +31.1 / MID +6.3 / PRE +13.5 / X' +8.1 (band and no-harm pass; mean +0.5k L6M, -2.0k PRE): placebo ranks of the cut perm / day-shuffled / AR(1): L6M 0.42 / 0.39 / 0.40, PRE 0.48 / 0.54 / 0.52, HOLD 0.98 / 0.93 / 0.97, X' 1.00 / 0.97 / 1.00: at chance in L6M and PRE (the HOLD and X' ranks are carried by the same 2-3 episodes). Thu+Fri x0.75 passes band and no-harm under PA9 too (MID -14%, mean -2.8k/wk L6M: mean fails). VOLUME / not a lead.
* **bars_since_flip_5m D3 (the best mean-keeping cell of 2.1):** PA9 L6M +11.0 / HOLD +8.9 / MID -6.8 / PRE +0.5 / X' +18.1 (the earlier +17.9 / +17.9 / -7.1 / +2.4 / +22.5 were phase 0): fails the band by a wider margin.
* **Add cells (genuine PA9):** add OFF (bound) L6M +60.0 / HOLD +45.4 / MID +22.6 / PRE +28.4 / X' +28.6 with mean -8.6k/wk (volume); 'add only when' T1/T2a/T3a/T4/ER >= .40 pass the band by cancelling adds (mean -4.7 to -8.8k/wk L6M); T3b (own support pulled <= 1/2) +50 / +31 / +2 / +17.5 / +3 with mean +1.0k/wk L6M, -3.7k PRE; every x2 rule fails band or no-harm (e.g. x2 if ER >= .30 else x0.5: L6M -17, MID -70, PRE -32, X' -25); exposure N<8: L6M +17.3 / MID +3.9 / PRE +5.9 / X' -4.4, mean -2.8k. No add cell keeps the mean and passes the band except 'T3b only' whose X' is +3% and PRE mean -3.7k; the size-matched placebos of 2.8 stand (single path).
## Files
pool_inputs_s2.csv REWRITTEN: cut_pre_eqrisk / cut_xp_eqrisk are now PA9-averaged equal-risk cuts (X' for xp), p1_exp_* from a PA9-scored calibration (7 volume levels x 10 permutation draws, cores re-run), noharm_flag from the PA9 judgement, new columns pa9_cut_L6M, pa9_cut_PRE, pa9_cut_X, pa9_band5, pa9_mean_ok, eqrisk_method = pa9_scoring_weekkey_shift; the previous single-path file is kept as pool_inputs_s2_singlepath.csv. PA9 tables: /mnt/l2/l2vast/ds3_zones3_new/sizer_s2ts/pa9_all.pkl, pa9_table.pkl, pa9_add.pkl, plc_pa9.pkl.


# S4b: FULL TREATMENT of the one cell that passes PA9 band + no-harm + mean (gate pulled_ahd10 d-1 GU1) - written 23:15Z
## 1. Verdict: it does NOT survive with the carrying week dropped; not flagged
* **Genuine PA9 (scoring week key shifted -4..+4):** L6M +32.9% / PRE +10.8% / X' -13.8%. **With the carrying episode dropped (harness CAR weeks on each shifted key): L6M +15.3% (band .219), PRE +6.6% (band .099), X' +14.0%**: both required windows fall below the band, i.e. the cut is carried by the L6M and PRE worst episode (ONE-EPISODE).
* **Equal-risk (engine lot scale):** L6M lscale 1.19, mean at equal risk 45.8k/wk vs the reference's fitted 35.9k (+10.0k/wk; the maxDD fit has R2 0.87, noisy); PRE lscale 1.09, 16.9k vs 15.5k/wk (+1.4k). The up-size cancelled by the gate removes risk faster than it removes mean in the recent windows.
* **Mean:** +0.8k/wk L6M, but over the whole history the cell minus reference sums to -229k (-1.2k/wk): the monthly table (section 4) shows 18 of 43 months positive. Placebo cut ranks at chance (L6M 0.29-0.39, PRE 0.50-0.53; previous section).
* **Family-wise (section 3): 1 of 2,128 is what the null gives.**
## 2. The rule in plain language (live-computable)
* For a signal of book B at the signal second: ER(20) 5-min as live. **If ER >= 0.30 (the live x1.5 up-size) AND the 10-second pulled-liquidity-ahead multiple is in the top third of book B's own history, use x1.0 instead of x1.5** (the x0.5 branch is unchanged; the zone half, integer lots and locks as live).
* Pulled-liquidity-ahead multiple (10 s) = (size cancelled at levels 1-10 of the AHEAD side in the last 10 seconds, summed from the 1-s L2 table rows with second <= signal second: for a LONG the ask side sz_can_a1 + sz_can_a23 + sz_can_a410, for a SHORT the bid side sz_can_b*) / (median of the 10 displayed level sizes of that same side at the signal second). Array: /mnt/l2/l2vast/ds3_flow1s/pulled_ask10 (long) / pulled_bid10 (short).
* Rank r = (number of EARLIER signals of the same book with a valid multiple strictly below this signal's) / (number of earlier valid signals of the book); defined once the book has >= 100 earlier signals (else the gate does nothing). The gate fires when r > 2/3 (direction -1 of the grid cell: r' = 1 - r < 1/3).
* It touches 2,172 of 17,396 taken signals with live lots (12.5%). By book x session (touched share of the taken signals): HM nyam 30.7%, PE nyam 30.2%, KB nyam 26.1%, MV nyam 26.0%, PB asia 25.5%, KB nypm 15.9%, SM london 11.5%, SM asia 8.1%, and 4.6-7.1% in the other asia/london cells. The gate is mostly a NY-AM rule: the multiple is very large at the open (hundreds of cancelled lots against a 3-5 lot median level), so the per-book rank puts NY-AM signals in the top third.
* Lots distribution of the cell (taken signals), by book x session:
| book | session | n taken | mean lots | max lots | x0.25 | x0.5 | x0.75 | x1 | x1.5 (share %) |
|---|---|---|---|---|---|---|---|---|---|
| HM | asia | 1815 | 3.03 | 6 | 13.3 | 50.1 | 6.5 | 5.4 | 24.7 |
| HM | nyam | 1435 | 1.06 | 2 | 7.2 | 57.6 | 0.8 | 29.1 | 5.2 |
| KB | asia | 2293 | 1.66 | 3 | 14.0 | 48.1 | 6.0 | 4.3 | 27.6 |
| KB | london | 1660 | 1.68 | 3 | 9.1 | 52.5 | 4.2 | 5.1 | 29.2 |
| KB | nyam | 1882 | 1.07 | 2 | 8.4 | 60.0 | 0.8 | 24.6 | 6.1 |
| KB | nypm | 1361 | 1.50 | 3 | 8.7 | 57.5 | 1.8 | 15.9 | 16.2 |
| MV | london | 1576 | 1.84 | 3 | 6.0 | 47.2 | 3.7 | 6.1 | 36.9 |
| MV | nyam | 1947 | 1.08 | 2 | 6.8 | 59.7 | 0.8 | 25.2 | 7.4 |
| PB | asia | 1108 | 1.44 | 2 | 4.2 | 28.7 | 9.3 | 23.5 | 34.4 |
| PE | asia | 2177 | 6.37 | 11 | 9.0 | 47.4 | 5.1 | 5.9 | 32.5 |
| PE | london | 1606 | 6.65 | 11 | 6.6 | 47.5 | 2.2 | 7.8 | 35.8 |
| PE | nyam | 920 | 5.32 | 11 | 5.1 | 57.6 | 0.7 | 28.9 | 7.7 |
| SM | asia | 690 | 3.81 | 6 | 7.1 | 29.1 | 17.5 | 7.2 | 39.0 |
| SM | london | 680 | 3.39 | 6 | 12.8 | 36.3 | 10.1 | 10.7 | 30.0 |
Worst single-day exposure of the cell: max net lots 28 (stack risk $33.6k) on 2026-09-18, 2025-10-14 and 2025-08-06 (day table in /mnt/l2/l2vast/ds3_zones3_new/sizer_s2ts/gate_full.pkl, 'exposure'['days']).
* Worked rows (touched signals; the multiple and the rank are recomputed here from the raw L2 table rows and from the book's earlier signals and reproduce the stored arrays to 1e-7; the first touched row of each book after 2026-01-01, plus the first touched long):
| tid | book | session | day | side | ER(20) 5m | ladder | pulled-ahead 10 s mult | earlier signals of the book / strictly below | rank r | rank in file | session lots | lots live -> gated |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4005220 | KB | nyam | 20260102 | -1 | 0.396 | x1.5 | 557.3 | 5219 / 4874 | 0.9339 | 0.9339 | 1 | 2 -> 1 |
| 6005089 | PE | nyam | 20260102 | -1 | 0.475 | x1.5 | 255.4 | 5089 / 4027 | 0.7913 | 0.7913 | 7 | 11 -> 7 |
| 5001692 | SM | asia | 20260130 | -1 | 0.597 | x1.5 | 160.3 | 1692 / 1232 | 0.7281 | 0.7281 | 4 | 6 -> 4 |
| 2003957 | HM | nyam | 20260102 | -1 | 0.352 | x1.5 | 748.0 | 3957 / 3860 | 0.9755 | 0.9755 | 1 | 2 -> 1 |
| 9004911 | MV | nyam | 20260102 | -1 | 0.396 | x1.5 | 337.2 | 4901 / 4082 | 0.8329 | 0.8329 | 1 | 2 -> 1 |
| 2003961 | HM | asia | 20260105 | +1 | 0.381 | x1.5 | 170.5 | 3961 / 2916 | 0.7362 | 0.7362 | 4 | 6 -> 4 |
Raw check of the multiple for the five shorts (cancelled size in the last 10 s on the bid side / median bid level): KB 1672/3.0 = 557.3, PE 1277/5.0 = 255.4, SM 481/3.0 = 160.3, HM 2244/3.0 = 748.0, MV 1349/4.0 = 337.25. Sized lots with the gate: the x1.5 (rounded) becomes the session lots (e.g. PE 7 lots x1.5 -> 11 becomes 7).
## 3. Family-wise null: does any cell pass band + no-harm + mean by chance?
Shuffled-day multiplier worlds: 1,500 draws, each = a random cell of the 2,128-cell grid with its multiplier vector moved to other days (harness 'dayshuf'), engine run, genuine PA9 judged with the same rules. Null rates per draw: band 38.5% (577), band and no-harm 3.5% (53), band and mean kept 0.33% (5), noharm and mean kept 0.07% (1), **all three 0 of 1,500** (rule-of-3 upper bound 0.20% per cell). Real grid: band 30.4% (648), band and no-harm 9.9% (210), band and mean kept 1.1% (24), all three **1 of 2,128**. Chaining the null stages (P(band and mean kept) x P(no-harm | band) = 0.0033 x 0.092 = 0.0003) the expected number of triple-passing cells in 2,128 is about 0.65 (P(at least one) = 48%); at the 95% upper bound 4.3. **One passing cell is at chance; it is not evidence of a signal.** The real grid does have more cells with band and no-harm (9.9% vs 3.5%) and with band and mean kept (1.1% vs 0.33%) than the shuffled-day worlds, which is the volume/time-of-day structure of the features (cells that size down in the weak periods), not a surviving rule.
## 4. Monthly stability (cell minus reference total, $k per month; touched taken signals per month)
| month | 202304 | 202305 | 202306 | 202307 | 202308 | 202309 | 202310 | 202311 | 202312 | 202401 | 202402 | 202403 | 202404 | 202405 | 202406 | 202407 | 202408 | 202409 | 202410 | 202411 | 202412 | 202501 | 202502 | 202503 | 202504 | 202505 | 202506 | 202507 | 202508 | 202509 | 202510 | 202511 | 202512 | 202601 | 202602 | 202603 | 202604 | 202605 | 202606 | 202607 | 202608 | 202609 | 202610 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| cell minus reference, $k | +0 | +2 | -29 | +36 | -40 | -6 | -1 | -2 | +2 | +7 | +2 | -25 | -19 | -16 | -4 | -61 | -19 | +13 | +8 | -3 | -31 | -24 | +14 | +39 | -20 | -51 | +20 | -17 | -2 | -12 | -24 | +24 | +9 | -19 | +27 | -12 | -16 | +12 | -66 | +67 | +11 | -5 | +3 |
| touched taken signals | 0 | 26 | 40 | 26 | 48 | 22 | 37 | 20 | 19 | 19 | 27 | 27 | 47 | 19 | 16 | 67 | 66 | 53 | 52 | 41 | 30 | 46 | 53 | 52 | 136 | 54 | 38 | 24 | 32 | 19 | 60 | 74 | 44 | 52 | 61 | 134 | 81 | 84 | 129 | 85 | 46 | 75 | 91 |
18 of 43 months positive; best +67k (2026-07), worst -66k (2026-06), -61k (2024-07), -51k (2025-05), -40k (2023-08): the L6M gain is two offsetting months (2026-06 / 2026-07) around a rule that costs money in most other months. NOT A LEAD, no flag.

## SIZER_S3 (Z3) - report 2 (2026-11-03 ~14:30Z): section 3 re-run against Q1-A
Shadow only, no PASS claims. REFERENCE = Q1-A (live since 2026-11-02 19:30Z): ER(20) 5-min < 0.30 -> x0.5, else x1.0, sequential rounding, V13T_LIVE ts base (ts2 rerun of the ranked cells pending BASE-4). Q1-A on this base: L6M maxDD 110.6k, mean 27.6k/wk; HOLD 117.3k / 23.7k; MID 58.2k / 17.8k; PRE 94.8k / 13.0k; X' 60.1k / 3.9k. Cut = 1 - maxDD(cell)/maxDD(Q1-A); mean tolerance = paired MDE; band = tl_band_final PA9. Pool P8 (pool_p8_q1a.csv = built from pool_inputs_s1.csv + pool_inputs_s2.csv by the fixed rule): er_1m_100 (L5 B), ers_5m_20 (L3 B), er_2m_50 (L3 A), fd_katz_5m_20 (D3 A, d-1), es_lead1_60 (SIG A, d-1), ahead_rel (SIG A, d-1), pk_ratio_20d (D3 A, d-1), tot_rel (LIN A, d-1). Caveat: pool_inputs_s1.csv is still the single-path proxy file (unchanged since 2026-11-02 18:54Z); only s2 is PA9.
PHASE NOTE: under Q1-A (every multiplier <= 1) the base and the cells are identical across the 9 lock-reset phases (checked: max |daily difference| = 0.0 $ between phases 0, +2, -3), so PA9 = the single path for every cell below; the band is still the flip-noise band.
Results (files: out/sizer_s3/comb_q1a_all.csv, learnedq_*.csv, indepq_*.csv; ledger program SIZER_S3, 138 cells appended after dead_lookup, 0 duplicates):
* 3.2 COMBINATIONS (114 cells: 84 pairs + 30 triples of the top 5, x PROD / MEAN / MINDOWN; non-ER members ride on Q1-A): 0 of 114 pass the band rule vs Q1-A; the best L6M cut is +1.6% (er_1m_100 + ahead_rel MEAN, PRE -33.6%); 84 cells keep the L6M mean at or above Q1-A, none improves L6M and PRE together. 9 cells have positive L6M and PRE cuts only after dropping the carrying week (all non-ER features on Q1-A: es_lead1_60 + tot_rel MINDOWN L6M raw -32.7, dropped +29.3; PRE +19.9): the raw L6M cut is negative, so they are noise, not leads. NO FLAG.
* 3.3 LEARNED MONOTONE MAPPING (6 leaves, depth 3, 3 seeds, purged walk-forward 2024-01..2026-10, trailing 12 months, 5-day purge; months before 2024 = Q1-A so X' = 0): L3/LIN with the down-only pair (0.5-1.0) and L3 with 0.5-1.5. L6M / PRE / MID cuts vs Q1-A: seed0 L3(C) +4.2 / -16.6 / -35.3, LIN(C) +36.2 / +1.3 / -37.2; seed1 L3(C) +6.6 / -12.9 / -29.9, LIN(C) +10.8 / +6.1 / -28.1; seed2 L3(C) +27.2 / +4.3 / -37.0, LIN(C) +30.3 / +7.2 / -21.1 (the only cell that passes no-harm); the 0.5-1.5 L3(A) cells are worse than Q1-A in PRE and MID (-17 to -42, -46 to -91). With the carrying week dropped L6M falls to -9.8..+8.9. None clears the band in L6M and PRE with the mean intact; the learned mapping does not beat Q1-A. NO FLAG.
* 3.4 RISK PARITY (ATR14 5-min as the stop PROXY, because the engine stop is a constant 60 pts): on top of Q1-A t=0.75 L6M +51.2, PRE -33.8, X' -70.5; t=1.00 +25.0 / -57.9 / -110; t=1.25 +15.4 / -81.2 / -120; the cells that replace the ladder are worse. All fail PRE/X' no-harm. NO FLAG.
* 3.5 SIZER ON EXITS (bracket stop=target=S on ER<=cutoff, Q1-A unchanged): 9 cells, L6M cuts -30.1 to +0.8, PRE -16.4 to +5.4, mean -1.9k to -3.4k/wk: inside the band, none flagged. DEAD for maxDD.
* 3.6 sizer x lock under Q1-A: the day lock R scales only when mult > 1, which Q1-A never has, so the lock surface is unchanged by Q1-A by construction; the lock re-tune (12R floor / 2R-50% give-back) is for BASE-4's lock grid. Not run here.
Plain sentence: no combination, learned mapping, risk-parity or exit-bracket cell beats Q1-A on L6M and PRE with the carrying week dropped, placebo-clean; stay on Q1-A. Still open: exposure table (SIZER_EXPOSURE.md) and the add-sizing cells (waiting for the ts2 base and BASE-4's add hook), top-20 restatement of sections 1-2 (owners S4a/S4b), rerun of the ranked cells on ts2.

## SIZER_S3 (Z3) - report 3 (2026-11-03 ~15:50Z): section 3 on the ts2 base (live lot order) vs Q1-A
Shadow only, no PASS claims. Base = BASE-4 run_v13t_ts2 (session -> A06 slot -> B02 -> ER -> zone HALF last; lock R scaled only when mult > 1); my harness (code/sizer_s3/sizer3_ts2.py, S3H2) puts each cell's multiplier vector in the ER slot and reproduces the ts2 Q1-A default to 0.0 $. REFERENCE = Q1-A on ts2: L6M maxDD 104.8k / mean 27.0k; HOLD 122.0k / 22.6k; MID 59.7k / 16.9k; PRE 88.2k / 13.2k; X' 80.8k / 3.3k; mean lots 2.31, all multipliers <= 1 (phase-invariant). Same pool P8 (pool_p8_q1a.csv), same cells as report 2; files out/sizer_s3/ts2/; ledger program SIZER_S3 +138 ts2 cells (dead_lookup first, 0 dups).
* 3.2 COMBINATIONS (114): 0 pass the band rule, 0 have L6M and PRE both positive vs Q1-A; best L6M +11.4% (er_1m_100 + tot_rel MEAN: PRE -27.2, X' -56.7, MID -41.0); 9 cells positive in L6M and PRE only after dropping the carrying week (raw L6M negative). NO FLAG.
* 3.3 LEARNED MAPPING (3 seeds x L3(C)/LIN(C)/L3(A)): L6M cuts +24 to +42 (down-only pair), PRE -12 to +18, MID -21 to -46 (all fail MID no-harm), L6M with the carrying weeks dropped -15..+9 (seed2 LIN(C): L6M +29.6 / PRE +17.8 / MID -22.9, dropped L6M -0.3); the 0.5-1.5 cells are worse than Q1-A. Does not beat Q1-A. NO FLAG.
* 3.4 RISK PARITY on top of Q1-A (ATR14 5-min stop PROXY): L6M +45.4 / +30.6 / +31.5 (t = 0.75 / 1.0 / 1.25) but PRE -33 / -44 / -71 and X' -44 / -64 / -89: fails. 3.5 brackets on ER<=cutoff: 9 cells inside the band (L6M -32 to +4.6), mean -2.5k to -4.5k/wk, DEAD for maxDD. NO FLAG.
Plain sentence (section 3): on the live-order base no combination, learned mapping, risk-parity or exit-bracket cell beats Q1-A on L6M and PRE with the carrying week dropped; stay on Q1-A. The earlier ts results (report 2) agree.
