# SIZER x LOCK reference table on V13T_LIVE (BASE-4, 2026-11-02T17:46Z)

Prereg: l2vast/ds3/prereg/LOCK_NOISE_prereg.md ADDENDUM 2026-11-02 (sha256 e35144f0...daeda in DECISIONS.md). The 60 live-lock cells (6 week floors x [no give-back + arm 1.5/2/3R x keep 25/50/75%]) at the 9 lock-reset phases (floor-none: phase 0), V13T_LIVE (xcost 0.80, stop cost 2.45, lock none = per-book locks only), sizer ON = the live ER(20) ladder x1.5/x0.5 (existing DS3_LIVE_LOCK_NOISE A set), sizer OFF = lots_mult 1 for every signal (zone HALF factor and integer rounding kept). All numbers are phase averages (PA) of the weekly-cumulative maxDD and the mean $/wk of the window. Table only, no PASS claim, no recommendation.

## 1. Reference cells: PA maxDD (rank among 60, 1 = shallowest) and PA mean (rank, 1 = highest), sizer ON vs OFF
| window | cell | ON maxDD | ON mean | OFF maxDD | OFF mean | maxDD ON-OFF |
|---|---|---|---|---|---|---|
| F9 | LIVE | 172k (rk 40) | 33.7k (rk 28) | 135k (rk 46) | 19.8k (rk 48) | +36k |
| F9 | F10N | 135k (rk 1) | 37.1k (rk 2) | 132k (rk 39) | 26.2k (rk 3) | +3k |
| F9 | F12N | 142k (rk 9) | 36.8k (rk 3) | 135k (rk 50) | 25.9k (rk 7) | +6k |
| F9 | F8N | 138k (rk 4) | 37.1k (rk 1) | 124k (rk 29) | 26.3k (rk 2) | +14k |
| F9 | F12 arm3 .5 | 144k (rk 11) | 35.8k (rk 13) | 139k (rk 52) | 22.3k (rk 36) | +6k |
| F9 | F16N | 154k (rk 24) | 36.5k (rk 4) | 135k (rk 40) | 25.9k (rk 6) | +19k |
| L6M | LIVE | 172k (rk 40) | 36.2k (rk 28) | 82k (rk 38) | 26.1k (rk 47) | +90k |
| L6M | F10N | 135k (rk 1) | 40.0k (rk 1) | 82k (rk 42) | 30.7k (rk 6) | +53k |
| L6M | F12N | 142k (rk 9) | 39.9k (rk 3) | 86k (rk 52) | 30.5k (rk 9) | +56k |
| L6M | F8N | 138k (rk 4) | 39.9k (rk 2) | 83k (rk 44) | 30.4k (rk 11) | +55k |
| L6M | F12 arm3 .5 | 144k (rk 11) | 39.7k (rk 7) | 88k (rk 57) | 26.7k (rk 41) | +56k |
| L6M | F16N | 154k (rk 24) | 39.3k (rk 13) | 87k (rk 55) | 30.6k (rk 8) | +67k |
| HOLD | LIVE | 172k (rk 37) | 30.6k (rk 30) | 192k (rk 34) | 21.0k (rk 48) | -21k |
| HOLD | F10N | 147k (rk 11) | 34.4k (rk 2) | 211k (rk 50) | 26.2k (rk 3) | -64k |
| HOLD | F12N | 156k (rk 20) | 34.3k (rk 4) | 215k (rk 57) | 26.0k (rk 7) | -59k |
| HOLD | F8N | 144k (rk 5) | 34.5k (rk 1) | 202k (rk 40) | 26.3k (rk 2) | -58k |
| HOLD | F12 arm3 .5 | 148k (rk 12) | 33.4k (rk 12) | 214k (rk 51) | 23.4k (rk 34) | -66k |
| HOLD | F16N | 156k (rk 21) | 34.3k (rk 3) | 214k (rk 55) | 26.1k (rk 6) | -58k |
| PRE | LIVE | 168k (rk 22) | 17.1k (rk 12) | 120k (rk 29) | 13.7k (rk 21) | +48k |
| PRE | F10N | 172k (rk 26) | 17.0k (rk 13) | 126k (rk 39) | 14.1k (rk 13) | +46k |
| PRE | F12N | 176k (rk 31) | 16.9k (rk 14) | 115k (rk 15) | 14.3k (rk 9) | +61k |
| PRE | F8N | 187k (rk 49) | 16.3k (rk 23) | 124k (rk 37) | 13.8k (rk 17) | +63k |
| PRE | F12 arm3 .5 | 181k (rk 39) | 16.6k (rk 19) | 122k (rk 36) | 14.4k (rk 3) | +59k |
| PRE | F16N | 179k (rk 36) | 17.5k (rk 6) | 113k (rk 4) | 14.3k (rk 7) | +66k |
| X' | LIVE | 89k (rk 32) | 4.5k (rk 45) | 121k (rk 42) | 4.9k (rk 58) | -32k |
| X' | F10N | 83k (rk 19) | 4.8k (rk 39) | 109k (rk 12) | 5.4k (rk 18) | -26k |
| X' | F12N | 77k (rk 7) | 5.1k (rk 31) | 110k (rk 15) | 5.3k (rk 26) | -33k |
| X' | F8N | 85k (rk 24) | 4.4k (rk 50) | 106k (rk 3) | 5.2k (rk 36) | -21k |
| X' | F12 arm3 .5 | 78k (rk 9) | 5.3k (rk 25) | 115k (rk 26) | 5.3k (rk 22) | -36k |
| X' | F16N | 76k (rk 5) | 5.4k (rk 24) | 110k (rk 13) | 5.3k (rk 24) | -33k |

## 2. How much does the sizer change the lock surface?  Spearman rank correlation over the 60 cells, ON vs OFF
| window | rho maxDD | rho mean | ON-OFF maxDD | shallowest cell ON ; OFF | highest-mean cell ON ; OFF |
|---|---|---|---|---|---|
| F9 | -0.35 | +0.78 | 59 of 60 deeper with sizer ON; median +41k | floor 10R / no give-back (135k) ; OFF: floor 6R / arm 1.5R keep 0.75 (89k) | floor 8R / no give-back (37.1k) ; OFF: floor 6R / no give-back (26.4k) |
| L6M | -0.56 | +0.65 | 60 of 60 deeper with sizer ON; median +90k | floor 10R / no give-back (135k) ; OFF: floor 6R / arm 1.5R keep 0.5 (64k) | floor 10R / no give-back (40.0k) ; OFF: floor none / arm 2.0R keep 0.25 (31.1k) |
| HOLD | -0.60 | +0.82 | 23 of 60 deeper with sizer ON; median -13k | floor 8R / arm 3.0R keep 0.5 (142k) ; OFF: floor 6R / arm 1.5R keep 0.75 (131k) | floor 8R / no give-back (34.5k) ; OFF: floor 6R / no give-back (26.5k) |
| PRE | +0.11 | +0.83 | 58 of 60 deeper with sizer ON; median +55k | floor none / arm 1.5R keep 0.75 (124k) ; OFF: floor 16R / arm 2.0R keep 0.75 (104k) | floor none / arm 2.0R keep 0.5 (17.7k) ; OFF: floor 16R / arm 3.0R keep 0.5 (14.5k) |
| X' | +0.48 | +0.38 | 0 of 60 deeper with sizer ON; median -29k | floor none / no give-back (72k) ; OFF: floor 8R / arm 2.0R keep 0.75 (104k) | floor none / arm 1.5R keep 0.75 (8.0k) ; OFF: floor none / arm 1.5R keep 0.75 (7.6k) |

## 3. F9, sizer OFF: PA maxDD / PA mean per week (rows: week floor; columns: give-back none | arm 1.5R keep .25 .5 .75 | arm 2R .25 .5 .75 | arm 3R .25 .5 .75)
| floor | no gb | a1.5 k0.25 | a1.5 k0.5 | a1.5 k0.75 | a2.0 k0.25 | a2.0 k0.5 | a2.0 k0.75 | a3.0 k0.25 | a3.0 k0.5 | a3.0 k0.75 |
|---|---|---|---|---|---|---|---|---|---|---|
| floor 6R | 107k / 26.4k | 99k / 24.2k | 96k / 19.0k | 89k / 18.8k | 110k / 24.7k | 107k / 20.8k | 101k / 21.4k | 110k / 26.0k | 109k / 23.0k | 106k / 25.0k |
| floor 8R | 124k / 26.3k | 109k / 24.1k | 101k / 18.8k | 91k / 18.6k | 127k / 24.7k | 122k / 20.2k | 115k / 21.2k | 129k / 25.9k | 127k / 22.7k | 124k / 24.7k |
| floor 10R | 132k / 26.2k | 112k / 24.0k | 104k / 18.7k | 93k / 18.6k | 135k / 24.5k | 130k / 20.1k | 123k / 21.0k | 138k / 25.6k | 135k / 22.6k | 132k / 24.6k |
| floor 12R | 135k / 25.9k | 112k / 23.9k | 103k / 18.7k | 91k / 18.6k | 140k / 24.3k | 135k / 19.8k | 128k / 20.8k | 142k / 25.3k | 139k / 22.3k | 135k / 24.3k |
| floor 16R | 135k / 25.9k | 112k / 24.0k | 103k / 18.7k | 91k / 18.6k | 140k / 24.5k | 135k / 19.8k | 128k / 20.8k | 142k / 25.4k | 139k / 22.3k | 135k / 24.3k |
| floor none | 135k / 26.1k | 112k / 24.0k | 103k / 18.7k | 91k / 18.6k | 140k / 24.5k | 135k / 19.9k | 128k / 20.8k | 142k / 25.5k | 139k / 22.3k | 135k / 24.3k |

## 3. F9, sizer ON: PA maxDD / PA mean per week (rows: week floor; columns: give-back none | arm 1.5R keep .25 .5 .75 | arm 2R .25 .5 .75 | arm 3R .25 .5 .75)
| floor | no gb | a1.5 k0.25 | a1.5 k0.5 | a1.5 k0.75 | a2.0 k0.25 | a2.0 k0.5 | a2.0 k0.75 | a3.0 k0.25 | a3.0 k0.5 | a3.0 k0.75 |
|---|---|---|---|---|---|---|---|---|---|---|
| floor 6R | 148k / 35.0k | 167k / 31.1k | 187k / 31.0k | 161k / 27.8k | 163k / 33.6k | 176k / 32.3k | 176k / 31.1k | 149k / 34.6k | 147k / 34.7k | 148k / 32.9k |
| floor 8R | 138k / 37.1k | 172k / 31.6k | 186k / 31.2k | 155k / 28.2k | 162k / 35.0k | 173k / 33.6k | 171k / 32.2k | 137k / 36.5k | 138k / 36.2k | 140k / 34.3k |
| floor 10R | 135k / 37.1k | 177k / 31.7k | 186k / 31.5k | 161k / 28.2k | 165k / 35.1k | 169k / 33.7k | 171k / 32.0k | 136k / 36.5k | 140k / 36.1k | 141k / 34.3k |
| floor 12R | 142k / 36.8k | 181k / 31.9k | 193k / 31.5k | 159k / 28.7k | 169k / 35.1k | 172k / 33.7k | 172k / 32.1k | 143k / 36.1k | 144k / 35.8k | 146k / 34.0k |
| floor 16R | 154k / 36.5k | 191k / 31.7k | 201k / 31.2k | 164k / 28.5k | 179k / 34.8k | 182k / 33.2k | 183k / 31.7k | 153k / 36.0k | 153k / 35.5k | 155k / 33.6k |
| floor none | 147k / 36.3k | 184k / 31.7k | 197k / 31.3k | 151k / 29.0k | 173k / 34.7k | 176k / 33.2k | 177k / 31.7k | 145k / 35.9k | 146k / 35.4k | 149k / 33.6k |

## 3. L6M, sizer OFF: PA maxDD / PA mean per week (rows: week floor; columns: give-back none | arm 1.5R keep .25 .5 .75 | arm 2R .25 .5 .75 | arm 3R .25 .5 .75)
| floor | no gb | a1.5 k0.25 | a1.5 k0.5 | a1.5 k0.75 | a2.0 k0.25 | a2.0 k0.5 | a2.0 k0.75 | a3.0 k0.25 | a3.0 k0.5 | a3.0 k0.75 |
|---|---|---|---|---|---|---|---|---|---|---|
| floor 6R | 78k / 30.3k | 73k / 29.5k | 64k / 22.4k | 64k / 21.6k | 71k / 30.4k | 82k / 26.2k | 77k / 26.9k | 75k / 30.1k | 83k / 26.7k | 80k / 28.7k |
| floor 8R | 83k / 30.4k | 75k / 29.7k | 65k / 22.4k | 67k / 21.5k | 72k / 30.8k | 85k / 26.2k | 80k / 27.0k | 79k / 30.2k | 85k / 26.7k | 84k / 28.8k |
| floor 10R | 82k / 30.7k | 76k / 29.9k | 66k / 22.5k | 69k / 21.6k | 70k / 31.0k | 83k / 26.3k | 76k / 27.1k | 79k / 30.3k | 84k / 27.0k | 82k / 29.0k |
| floor 12R | 86k / 30.5k | 79k / 29.8k | 66k / 22.4k | 69k / 21.5k | 70k / 31.0k | 82k / 26.1k | 76k / 27.0k | 81k / 30.1k | 88k / 26.7k | 86k / 28.7k |
| floor 16R | 87k / 30.6k | 81k / 29.8k | 68k / 22.4k | 70k / 21.6k | 68k / 31.1k | 82k / 26.1k | 76k / 26.9k | 83k / 30.1k | 92k / 26.6k | 87k / 28.7k |
| floor none | 87k / 30.7k | 82k / 29.8k | 68k / 22.4k | 70k / 21.6k | 68k / 31.1k | 81k / 26.2k | 75k / 27.0k | 83k / 30.3k | 93k / 26.7k | 88k / 28.8k |

## 3. L6M, sizer ON: PA maxDD / PA mean per week (rows: week floor; columns: give-back none | arm 1.5R keep .25 .5 .75 | arm 2R .25 .5 .75 | arm 3R .25 .5 .75)
| floor | no gb | a1.5 k0.25 | a1.5 k0.5 | a1.5 k0.75 | a2.0 k0.25 | a2.0 k0.5 | a2.0 k0.75 | a3.0 k0.25 | a3.0 k0.5 | a3.0 k0.75 |
|---|---|---|---|---|---|---|---|---|---|---|
| floor 6R | 148k / 38.9k | 167k / 34.9k | 187k / 33.7k | 161k / 28.5k | 163k / 37.2k | 176k / 35.5k | 176k / 33.0k | 149k / 38.7k | 147k / 39.0k | 148k / 35.9k |
| floor 8R | 138k / 39.9k | 172k / 35.1k | 186k / 34.2k | 155k / 29.0k | 162k / 37.5k | 173k / 36.0k | 171k / 33.6k | 137k / 39.5k | 138k / 39.7k | 140k / 36.3k |
| floor 10R | 135k / 40.0k | 177k / 35.1k | 186k / 34.1k | 161k / 28.8k | 165k / 37.6k | 169k / 36.1k | 171k / 33.5k | 136k / 39.7k | 140k / 39.7k | 141k / 36.4k |
| floor 12R | 142k / 39.9k | 181k / 35.4k | 193k / 34.2k | 159k / 29.3k | 169k / 37.8k | 172k / 36.2k | 172k / 33.8k | 143k / 39.5k | 144k / 39.7k | 146k / 36.3k |
| floor 16R | 154k / 39.3k | 191k / 34.9k | 201k / 33.8k | 164k / 29.1k | 179k / 37.3k | 182k / 35.8k | 183k / 33.3k | 153k / 39.1k | 153k / 39.2k | 155k / 35.8k |
| floor none | 147k / 39.6k | 184k / 35.1k | 197k / 34.0k | 151k / 29.6k | 173k / 37.5k | 176k / 36.0k | 177k / 33.5k | 145k / 39.3k | 146k / 39.5k | 149k / 36.1k |

## 3. HOLD, sizer OFF: PA maxDD / PA mean per week (rows: week floor; columns: give-back none | arm 1.5R keep .25 .5 .75 | arm 2R .25 .5 .75 | arm 3R .25 .5 .75)
| floor | no gb | a1.5 k0.25 | a1.5 k0.5 | a1.5 k0.75 | a2.0 k0.25 | a2.0 k0.5 | a2.0 k0.75 | a3.0 k0.25 | a3.0 k0.5 | a3.0 k0.75 |
|---|---|---|---|---|---|---|---|---|---|---|
| floor 6R | 179k / 26.5k | 161k / 24.5k | 147k / 19.3k | 131k / 17.9k | 169k / 24.9k | 160k / 21.6k | 143k / 22.6k | 180k / 26.1k | 178k / 24.0k | 172k / 25.7k |
| floor 8R | 202k / 26.3k | 176k / 24.3k | 157k / 19.2k | 137k / 17.7k | 191k / 24.8k | 179k / 21.3k | 161k / 22.5k | 205k / 26.0k | 202k / 23.6k | 195k / 25.5k |
| floor 10R | 211k / 26.2k | 180k / 24.3k | 160k / 19.1k | 139k / 17.7k | 200k / 24.7k | 188k / 21.2k | 170k / 22.4k | 214k / 25.8k | 210k / 23.6k | 203k / 25.4k |
| floor 12R | 215k / 26.0k | 180k / 24.2k | 159k / 19.1k | 137k / 17.8k | 204k / 24.6k | 192k / 21.0k | 174k / 22.2k | 218k / 25.6k | 214k / 23.4k | 206k / 25.3k |
| floor 16R | 214k / 26.1k | 180k / 24.3k | 159k / 19.1k | 137k / 17.8k | 204k / 24.7k | 192k / 21.0k | 174k / 22.2k | 218k / 25.6k | 214k / 23.4k | 206k / 25.2k |
| floor none | 214k / 26.2k | 180k / 24.3k | 159k / 19.1k | 137k / 17.8k | 204k / 24.7k | 192k / 21.0k | 174k / 22.2k | 218k / 25.7k | 214k / 23.4k | 206k / 25.2k |

## 3. HOLD, sizer ON: PA maxDD / PA mean per week (rows: week floor; columns: give-back none | arm 1.5R keep .25 .5 .75 | arm 2R .25 .5 .75 | arm 3R .25 .5 .75)
| floor | no gb | a1.5 k0.25 | a1.5 k0.5 | a1.5 k0.75 | a2.0 k0.25 | a2.0 k0.5 | a2.0 k0.75 | a3.0 k0.25 | a3.0 k0.5 | a3.0 k0.75 |
|---|---|---|---|---|---|---|---|---|---|---|
| floor 6R | 167k / 32.6k | 176k / 28.6k | 188k / 27.4k | 173k / 24.4k | 177k / 30.6k | 187k / 29.2k | 185k / 28.7k | 167k / 32.1k | 164k / 32.1k | 163k / 31.0k |
| floor 8R | 144k / 34.5k | 172k / 29.5k | 186k / 28.1k | 157k / 25.2k | 162k / 32.0k | 173k / 30.5k | 171k / 30.0k | 143k / 33.9k | 142k / 33.5k | 142k / 32.5k |
| floor 10R | 147k / 34.4k | 178k / 29.5k | 186k / 28.3k | 161k / 25.3k | 169k / 32.0k | 169k / 30.5k | 171k / 29.8k | 146k / 33.8k | 144k / 33.3k | 143k / 32.3k |
| floor 12R | 156k / 34.3k | 181k / 29.9k | 193k / 28.6k | 159k / 25.8k | 169k / 32.2k | 172k / 30.6k | 172k / 30.1k | 153k / 33.7k | 148k / 33.4k | 146k / 32.3k |
| floor 16R | 156k / 34.3k | 191k / 29.8k | 201k / 28.5k | 164k / 25.8k | 179k / 32.2k | 182k / 30.6k | 183k / 30.0k | 154k / 33.8k | 153k / 33.3k | 155k / 32.3k |
| floor none | 148k / 34.2k | 184k / 29.8k | 197k / 28.6k | 151k / 26.2k | 173k / 32.2k | 176k / 30.6k | 177k / 30.1k | 145k / 33.7k | 146k / 33.3k | 149k / 32.2k |

## 3. PRE, sizer OFF: PA maxDD / PA mean per week (rows: week floor; columns: give-back none | arm 1.5R keep .25 .5 .75 | arm 2R .25 .5 .75 | arm 3R .25 .5 .75)
| floor | no gb | a1.5 k0.25 | a1.5 k0.5 | a1.5 k0.75 | a2.0 k0.25 | a2.0 k0.5 | a2.0 k0.75 | a3.0 k0.25 | a3.0 k0.5 | a3.0 k0.75 |
|---|---|---|---|---|---|---|---|---|---|---|
| floor 6R | 126k / 13.7k | 120k / 12.5k | 116k / 11.2k | 140k / 8.3k | 128k / 12.9k | 127k / 13.5k | 119k / 11.7k | 129k / 13.9k | 131k / 14.1k | 133k / 13.1k |
| floor 8R | 124k / 13.8k | 117k / 12.5k | 117k / 11.2k | 142k / 8.2k | 127k / 12.9k | 126k / 13.6k | 116k / 11.7k | 129k / 14.1k | 130k / 14.1k | 131k / 13.2k |
| floor 10R | 126k / 14.1k | 118k / 12.6k | 117k / 11.3k | 140k / 8.3k | 128k / 12.9k | 126k / 13.5k | 114k / 11.7k | 130k / 14.2k | 130k / 14.3k | 126k / 13.3k |
| floor 12R | 115k / 14.3k | 115k / 12.6k | 114k / 11.3k | 137k / 8.3k | 120k / 13.1k | 120k / 13.7k | 107k / 11.8k | 121k / 14.4k | 122k / 14.4k | 117k / 13.4k |
| floor 16R | 113k / 14.3k | 115k / 12.6k | 114k / 11.3k | 137k / 8.3k | 119k / 13.1k | 120k / 13.7k | 104k / 11.8k | 120k / 14.4k | 121k / 14.5k | 113k / 13.5k |
| floor none | 113k / 14.3k | 115k / 12.6k | 114k / 11.3k | 137k / 8.3k | 119k / 13.1k | 120k / 13.7k | 104k / 11.8k | 120k / 14.4k | 121k / 14.4k | 113k / 13.4k |

## 3. PRE, sizer ON: PA maxDD / PA mean per week (rows: week floor; columns: give-back none | arm 1.5R keep .25 .5 .75 | arm 2R .25 .5 .75 | arm 3R .25 .5 .75)
| floor | no gb | a1.5 k0.25 | a1.5 k0.5 | a1.5 k0.75 | a2.0 k0.25 | a2.0 k0.5 | a2.0 k0.75 | a3.0 k0.25 | a3.0 k0.5 | a3.0 k0.75 |
|---|---|---|---|---|---|---|---|---|---|---|
| floor 6R | 199k / 15.1k | 171k / 13.5k | 157k / 13.2k | 152k / 10.6k | 179k / 15.2k | 163k / 15.4k | 166k / 12.9k | 201k / 15.0k | 209k / 15.0k | 220k / 13.9k |
| floor 8R | 187k / 16.3k | 177k / 14.0k | 153k / 13.9k | 152k / 10.9k | 181k / 16.0k | 167k / 16.5k | 173k / 13.7k | 191k / 16.2k | 191k / 16.2k | 208k / 14.8k |
| floor 10R | 172k / 17.0k | 166k / 14.8k | 145k / 14.6k | 141k / 11.4k | 177k / 16.6k | 166k / 17.1k | 161k / 14.3k | 176k / 16.8k | 177k / 16.7k | 190k / 15.4k |
| floor 12R | 176k / 16.9k | 170k / 14.8k | 145k / 14.6k | 140k / 11.3k | 181k / 16.6k | 168k / 17.1k | 162k / 14.3k | 179k / 16.7k | 181k / 16.6k | 204k / 15.3k |
| floor 16R | 179k / 17.5k | 173k / 15.4k | 133k / 15.2k | 127k / 11.8k | 184k / 17.1k | 171k / 17.6k | 158k / 14.8k | 182k / 17.5k | 184k / 17.4k | 201k / 16.0k |
| floor none | 181k / 17.7k | 174k / 15.6k | 129k / 15.4k | 124k / 11.9k | 187k / 17.2k | 173k / 17.7k | 161k / 14.9k | 185k / 17.7k | 187k / 17.7k | 191k / 16.4k |

## 3. X', sizer OFF: PA maxDD / PA mean per week (rows: week floor; columns: give-back none | arm 1.5R keep .25 .5 .75 | arm 2R .25 .5 .75 | arm 3R .25 .5 .75)
| floor | no gb | a1.5 k0.25 | a1.5 k0.5 | a1.5 k0.75 | a2.0 k0.25 | a2.0 k0.5 | a2.0 k0.75 | a3.0 k0.25 | a3.0 k0.5 | a3.0 k0.75 |
|---|---|---|---|---|---|---|---|---|---|---|
| floor 6R | 118k / 5.1k | 133k / 5.3k | 128k / 6.0k | 118k / 7.2k | 142k / 5.0k | 130k / 4.7k | 117k / 5.0k | 125k / 5.1k | 123k / 5.1k | 122k / 5.0k |
| floor 8R | 106k / 5.2k | 120k / 5.4k | 118k / 6.1k | 104k / 7.4k | 129k / 5.1k | 117k / 4.8k | 104k / 5.1k | 114k / 5.2k | 112k / 5.2k | 111k / 5.1k |
| floor 10R | 109k / 5.4k | 123k / 5.6k | 122k / 6.2k | 108k / 7.6k | 133k / 5.2k | 121k / 4.9k | 107k / 5.3k | 117k / 5.3k | 114k / 5.3k | 113k / 5.2k |
| floor 12R | 110k / 5.3k | 123k / 5.5k | 122k / 6.2k | 108k / 7.5k | 133k / 5.2k | 121k / 4.9k | 107k / 5.3k | 117k / 5.3k | 115k / 5.3k | 114k / 5.2k |
| floor 16R | 110k / 5.3k | 122k / 5.6k | 121k / 6.2k | 107k / 7.6k | 132k / 5.2k | 120k / 4.9k | 106k / 5.3k | 117k / 5.3k | 114k / 5.3k | 114k / 5.2k |
| floor none | 110k / 5.3k | 122k / 5.6k | 121k / 6.2k | 107k / 7.6k | 132k / 5.2k | 120k / 4.9k | 106k / 5.3k | 117k / 5.3k | 114k / 5.3k | 114k / 5.2k |

## 3. X', sizer ON: PA maxDD / PA mean per week (rows: week floor; columns: give-back none | arm 1.5R keep .25 .5 .75 | arm 2R .25 .5 .75 | arm 3R .25 .5 .75)
| floor | no gb | a1.5 k0.25 | a1.5 k0.5 | a1.5 k0.75 | a2.0 k0.25 | a2.0 k0.5 | a2.0 k0.75 | a3.0 k0.25 | a3.0 k0.5 | a3.0 k0.75 |
|---|---|---|---|---|---|---|---|---|---|---|
| floor 6R | 87k / 4.5k | 112k / 4.1k | 112k / 4.1k | 98k / 6.7k | 100k / 4.4k | 100k / 4.0k | 93k / 5.6k | 90k / 4.5k | 90k / 4.5k | 90k / 4.8k |
| floor 8R | 85k / 4.4k | 109k / 4.1k | 109k / 4.0k | 99k / 6.6k | 95k / 4.3k | 98k / 3.8k | 90k / 5.5k | 86k / 4.5k | 86k / 4.6k | 87k / 4.8k |
| floor 10R | 83k / 4.8k | 109k / 4.5k | 112k / 4.2k | 100k / 6.6k | 96k / 4.7k | 99k / 4.1k | 91k / 5.8k | 85k / 4.8k | 85k / 4.9k | 85k / 5.2k |
| floor 12R | 77k / 5.1k | 101k / 4.8k | 105k / 4.6k | 91k / 7.0k | 88k / 5.1k | 89k / 4.5k | 81k / 6.2k | 79k / 5.2k | 78k / 5.3k | 79k / 5.6k |
| floor 16R | 76k / 5.4k | 97k / 5.2k | 100k / 5.0k | 89k / 7.7k | 84k / 5.4k | 82k / 4.9k | 78k / 6.8k | 80k / 5.4k | 80k / 5.5k | 80k / 5.8k |
| floor none | 72k / 5.6k | 93k / 5.5k | 95k / 5.3k | 84k / 8.0k | 81k / 5.7k | 77k / 5.2k | 73k / 7.1k | 77k / 5.7k | 76k / 5.8k | 76k / 6.1k |

## 4. Phase spread of the live cell with the sizer OFF
F9: live cell maxDD over the 9 phases 135-135k (mean 135k); L6M: live cell maxDD over the 9 phases 81-89k (mean 82k); HOLD: live cell maxDD over the 9 phases 192-192k (mean 192k); PRE: live cell maxDD over the 9 phases 120-120k (mean 120k); X': live cell maxDD over the 9 phases 120-124k (mean 121k)
