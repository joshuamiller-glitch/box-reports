
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
