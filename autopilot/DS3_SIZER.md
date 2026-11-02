
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
