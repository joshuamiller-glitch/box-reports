# DS3_SIZER_S35: sizer x lock re-tuned together under Q1-A (Z1, 2026-11-03T17:21Z) POST-HOC, no PASS, Shadow only
Prereg l2vast/ds3/prereg/SIZER_S35_Z1_prereg.md sha256 3350d32cbc61980bbb1dbfdb45a50a3a1ed33f1709a625ca6a9fac0c9a6165bd and ADDENDUM 1 (base -> run_v13t_ts2) sha256 a705fccd47936c53c5192ff5c3197775a25c3ca41a3dd74e32fc9eb5ead4b6da, both in DECISIONS.md before scoring; dead_lookup first (no stored Q1-A lock cell); ledger program SIZER_S35 (60 cells) appended after.
Base: run_v13t_ts2 (live lot order, Q1-A ladder ER<0.30 x0.5 else x1.0, zone HALF last, lock R never scaled), PerBook locks, daily +-R caps as live. 60 cells = week floor {6,8,10,12,16R,none} x give-back {none, arm 1.5/2/3R x keep .25/.5/.75}, 9 engine lock-reset phases (-4..+4) for every cell with a floor, scored with the SCORING week key shifted by the same phase (genuine PA9). My series reproduce BASE-4's lock_surf_ts2_Q1A.pkl on all 460 runs (max diff $0.003). A first pass on the old ts base (zone-before-ER, no A06/B02) gave the same conclusions and is a superseded cross-check.

## Answer in one paragraph
Under Q1-A the live lock cell (floor 12R, give-back arm 2R keep 0.5) is NOT beaten on L6M AND PRE with the carrying episode dropped at same-or-better mean: no cell passes the flag rule. Facts: (1) the week floor is inert at 10R and above under Q1-A (floors 10R, 12R, 16R and none give identical series to the dollar for every give-back variant; the 12R floor never binds with Q1-A lots), floor 8R differs by less than $25 and floor 6R is harmful (PRE -5..-12%); the live "12R week floor" is therefore a no-op under Q1-A and the lock decision is only the give-back. (2) Give-back arm 2R keep 0.5 (live) sits at a high-variance point: its neighbours arm 2R keep 0.25 and every arm-3R cell and "no give-back" cut L6M by +19..+20% (PA9) but are WORSE on PRE (-4..-8%), X' (-5..-7%), HOLD and MID: the single-episode pattern (L6M cut falls to +2% with the carrying episode ISO 202630..202637 removed; lot-shuffle placebo rank 0.01 on L6M but 0.81..0.91 on PRE). (3) The one cell that is non-negative on all five windows is arm 2R keep 0.75 (floor none or 8R): PA9 cut L6M +19%, HOLD +2%, MID +1%, PRE +6%, X' +10%; placebo ranks L6M 0.02, PRE 0.16, X' 0.05, HOLD 0.80; but with the carrying episodes dropped its cuts are only +1% (L6M) and +1% (PRE), its PRE mean is -1.6k/wk (paired MDE 2.5k; tolerance -1.3k, so it fails the mean rule), the family-wise best-of-29 null gives rank 0.099 for S1 (mean of PRE and X' cuts) and 0.257 for S2 (min of L6M and PRE cuts): WATCH only, no flag. (4) The BASE-4 observation "give-back arm 2R keep 25% gives L6M 75k" is true (PA9 80k) and is the same L6M-only single-episode pattern. So under size-down-only the live give-back keeps its place: nothing beats it on drawdown with the mean intact on both L6M and PRE.

### 1. Reference: the live lock cell (floor 12R, give-back arm 2R keep 0.5) under Q1-A
| window | weeks | PA9 maxDD | PA9 mean/wk | single-phase maxDD | worst-20 |
|---|---|---|---|---|---|
| L6M | 27 | 101k | 27.5k | 105k | 91.4k |
| HOLD | 52 | 113k | 22.4k | 122k | -389.8k |
| MID | 12 | 58k | 16.0k | 60k | n<20 |
| PRE | 75 | 101k | 13.3k | 88k | -489.6k |
| X' | 44 | 77k | 3.3k | 81k | -303.4k |
Carrying episodes of the reference (dropped from every series for the "dropped" columns): L6M ISO 202630..202637 (depth $105k), PRE ISO 202506..202509 (depth $88k).


### 2. Which cells are actually different under Q1-A
Of the 60 cells only 30 have distinct series (the week floors 10R, 12R, 16R and none give identical results: with Q1-A lots the week floor never binds at 10R or above; floors 6R and 8R bind a little). Floors 10R, 12R, 16R and none give identical series for all ten give-back variants.


### 3. L6M: PA9 maxDD / PA9 mean per week, Q1-A
| floor | no gb | a1.5 k0.25 | a1.5 k0.5 | a1.5 k0.75 | a2 k0.25 | a2 k0.5 | a2 k0.75 | a3 k0.25 | a3 k0.5 | a3 k0.75 |
|---|---|---|---|---|---|---|---|---|---|---|
| floor 6R | 83k / 30.2k | 94k / 27.7k | 118k / 26.1k | 86k / 23.2k | 82k / 29.7k | 102k / 27.2k | 83k / 27.5k | 83k / 30.2k | 83k / 30.5k | 82k / 29.4k |
| floor 8R | 81k / 30.4k | 90k / 28.0k | 113k / 26.4k | 79k / 23.6k | 80k / 30.0k | 101k / 27.5k | 81k / 27.6k | 81k / 30.4k | 81k / 30.8k | 81k / 29.6k |
| floor 10R | 81k / 30.4k | 90k / 28.0k | 113k / 26.5k | 79k / 23.6k | 80k / 30.0k | 101k / 27.5k | 81k / 27.6k | 81k / 30.4k | 81k / 30.8k | 81k / 29.6k |
| floor 12R | 81k / 30.4k | 90k / 28.0k | 113k / 26.5k | 79k / 23.6k | 80k / 30.0k | 101k / 27.5k | 81k / 27.6k | 81k / 30.4k | 81k / 30.8k | 81k / 29.6k |
| floor 16R | 81k / 30.4k | 90k / 28.0k | 113k / 26.5k | 79k / 23.6k | 80k / 30.0k | 101k / 27.5k | 81k / 27.6k | 81k / 30.4k | 81k / 30.8k | 81k / 29.6k |
| floor none | 81k / 30.4k | 90k / 28.0k | 113k / 26.5k | 79k / 23.6k | 80k / 30.0k | 101k / 27.5k | 81k / 27.6k | 81k / 30.4k | 81k / 30.8k | 81k / 29.6k |

### 3. HOLD: PA9 maxDD / PA9 mean per week, Q1-A
| floor | no gb | a1.5 k0.25 | a1.5 k0.5 | a1.5 k0.75 | a2 k0.25 | a2 k0.5 | a2 k0.75 | a3 k0.25 | a3 k0.5 | a3 k0.75 |
|---|---|---|---|---|---|---|---|---|---|---|
| floor 6R | 120k / 24.1k | 108k / 22.6k | 119k / 20.9k | 96k / 19.6k | 117k / 24.0k | 116k / 22.2k | 112k / 22.1k | 120k / 24.1k | 120k / 24.0k | 120k / 23.4k |
| floor 8R | 119k / 24.2k | 107k / 22.8k | 113k / 21.1k | 93k / 19.8k | 116k / 24.2k | 113k / 22.4k | 111k / 22.2k | 119k / 24.2k | 119k / 24.1k | 119k / 23.5k |
| floor 10R | 119k / 24.2k | 107k / 22.7k | 113k / 21.1k | 94k / 19.8k | 116k / 24.2k | 113k / 22.4k | 111k / 22.2k | 119k / 24.2k | 119k / 24.1k | 119k / 23.5k |
| floor 12R | 119k / 24.2k | 107k / 22.7k | 113k / 21.1k | 94k / 19.8k | 116k / 24.2k | 113k / 22.4k | 111k / 22.2k | 119k / 24.2k | 119k / 24.1k | 119k / 23.5k |
| floor 16R | 119k / 24.2k | 107k / 22.7k | 113k / 21.1k | 94k / 19.8k | 116k / 24.2k | 113k / 22.4k | 111k / 22.2k | 119k / 24.2k | 119k / 24.1k | 119k / 23.5k |
| floor none | 119k / 24.2k | 107k / 22.7k | 113k / 21.1k | 94k / 19.8k | 116k / 24.2k | 113k / 22.4k | 111k / 22.2k | 119k / 24.2k | 119k / 24.1k | 119k / 23.5k |

### 3. MID: PA9 maxDD / PA9 mean per week, Q1-A
| floor | no gb | a1.5 k0.25 | a1.5 k0.5 | a1.5 k0.75 | a2 k0.25 | a2 k0.5 | a2 k0.75 | a3 k0.25 | a3 k0.5 | a3 k0.75 |
|---|---|---|---|---|---|---|---|---|---|---|
| floor 6R | 62k / 16.2k | 55k / 15.5k | 51k / 16.2k | 49k / 16.1k | 61k / 16.4k | 60k / 15.8k | 59k / 15.9k | 62k / 16.2k | 62k / 15.0k | 62k / 14.9k |
| floor 8R | 60k / 16.3k | 53k / 15.7k | 49k / 16.4k | 47k / 16.3k | 59k / 16.6k | 58k / 16.0k | 57k / 16.1k | 60k / 16.3k | 60k / 15.1k | 60k / 15.1k |
| floor 10R | 60k / 16.3k | 53k / 15.7k | 49k / 16.4k | 47k / 16.3k | 59k / 16.6k | 58k / 16.0k | 57k / 16.1k | 60k / 16.3k | 60k / 15.1k | 60k / 15.1k |
| floor 12R | 60k / 16.3k | 53k / 15.7k | 49k / 16.4k | 47k / 16.3k | 59k / 16.6k | 58k / 16.0k | 57k / 16.1k | 60k / 16.3k | 60k / 15.1k | 60k / 15.1k |
| floor 16R | 60k / 16.3k | 53k / 15.7k | 49k / 16.4k | 47k / 16.3k | 59k / 16.6k | 58k / 16.0k | 57k / 16.1k | 60k / 16.3k | 60k / 15.1k | 60k / 15.1k |
| floor none | 60k / 16.3k | 53k / 15.7k | 49k / 16.4k | 47k / 16.3k | 59k / 16.6k | 58k / 16.0k | 57k / 16.1k | 60k / 16.3k | 60k / 15.1k | 60k / 15.1k |

### 3. PRE: PA9 maxDD / PA9 mean per week, Q1-A
| floor | no gb | a1.5 k0.25 | a1.5 k0.5 | a1.5 k0.75 | a2 k0.25 | a2 k0.5 | a2 k0.75 | a3 k0.25 | a3 k0.5 | a3 k0.75 |
|---|---|---|---|---|---|---|---|---|---|---|
| floor 6R | 112k / 12.9k | 114k / 11.9k | 118k / 10.6k | 123k / 8.5k | 114k / 13.2k | 106k / 13.2k | 99k / 11.7k | 112k / 12.9k | 111k / 12.8k | 110k / 11.8k |
| floor 8R | 107k / 13.0k | 109k / 12.0k | 113k / 10.6k | 118k / 8.6k | 109k / 13.2k | 101k / 13.3k | 95k / 11.7k | 107k / 13.0k | 107k / 12.9k | 105k / 11.9k |
| floor 10R | 107k / 13.0k | 109k / 12.0k | 113k / 10.7k | 117k / 8.6k | 109k / 13.3k | 101k / 13.3k | 95k / 11.8k | 107k / 13.0k | 107k / 12.9k | 105k / 11.9k |
| floor 12R | 107k / 13.0k | 109k / 12.0k | 113k / 10.7k | 117k / 8.6k | 109k / 13.3k | 101k / 13.3k | 95k / 11.8k | 107k / 13.0k | 107k / 12.9k | 105k / 11.9k |
| floor 16R | 107k / 13.0k | 109k / 12.0k | 113k / 10.7k | 117k / 8.6k | 109k / 13.3k | 101k / 13.3k | 95k / 11.8k | 107k / 13.0k | 107k / 12.9k | 105k / 11.9k |
| floor none | 107k / 13.0k | 109k / 12.0k | 113k / 10.7k | 117k / 8.6k | 109k / 13.3k | 101k / 13.3k | 95k / 11.8k | 107k / 13.0k | 107k / 12.9k | 105k / 11.9k |

### 3. X': PA9 maxDD / PA9 mean per week, Q1-A
| floor | no gb | a1.5 k0.25 | a1.5 k0.5 | a1.5 k0.75 | a2 k0.25 | a2 k0.5 | a2 k0.75 | a3 k0.25 | a3 k0.5 | a3 k0.75 |
|---|---|---|---|---|---|---|---|---|---|---|
| floor 6R | 88k / 3.2k | 102k / 2.9k | 93k / 3.5k | 83k / 4.2k | 88k / 3.2k | 83k / 3.2k | 76k / 3.0k | 88k / 3.2k | 88k / 3.2k | 88k / 3.2k |
| floor 8R | 83k / 3.4k | 97k / 3.0k | 87k / 3.6k | 76k / 4.3k | 83k / 3.4k | 77k / 3.3k | 69k / 3.1k | 83k / 3.4k | 83k / 3.4k | 83k / 3.4k |
| floor 10R | 83k / 3.4k | 97k / 3.0k | 87k / 3.6k | 76k / 4.3k | 83k / 3.4k | 77k / 3.3k | 69k / 3.1k | 83k / 3.4k | 83k / 3.4k | 83k / 3.4k |
| floor 12R | 83k / 3.4k | 97k / 3.0k | 87k / 3.6k | 76k / 4.3k | 83k / 3.4k | 77k / 3.3k | 69k / 3.1k | 83k / 3.4k | 83k / 3.4k | 83k / 3.4k |
| floor 16R | 83k / 3.4k | 97k / 3.0k | 87k / 3.6k | 76k / 4.3k | 83k / 3.4k | 77k / 3.3k | 69k / 3.1k | 83k / 3.4k | 83k / 3.4k | 83k / 3.4k |
| floor none | 83k / 3.4k | 97k / 3.0k | 87k / 3.6k | 76k / 4.3k | 83k / 3.4k | 77k / 3.3k | 69k / 3.1k | 83k / 3.4k | 83k / 3.4k | 83k / 3.4k |

### 4. Cut of every distinct cell vs the live cell (positive = shallower), genuine PA9 (floors 10R, 12R, 16R and none give identical series: shown once as "floor none"; the live cell is floor none / arm 2R keep 0.5)
| cell | PA9 cut L6M | HOLD | MID | PRE | X' | dropped L6M / PRE | mean d L6M / PRE $k (MDE) | strict / tolerant |
|---|---|---|---|---|---|---|---|---|
| floor 6R / no give-back | +18% | -6% | -7% | -11% | -14% | -3% / -11% | +2.7 (4.6) / -0.4 (1.3) | n / Y |
| floor 6R / arm 1.5R keep 0.25 | +7% | +4% | +5% | -12% | -32% | -15% / -5% | +0.2 (5.5) / -1.4 (2.8) | n / Y |
| floor 6R / arm 1.5R keep 0.5 | -18% | -5% | +12% | -17% | -21% | -12% / -0% | -1.4 (4.7) / -2.7 (3.1) | n / n |
| floor 6R / arm 1.5R keep 0.75 | +15% | +16% | +15% | -21% | -7% | -6% / -15% | -4.3 (9.2) / -4.8 (4.2) | n / n |
| floor 6R / arm 2.0R keep 0.25 | +19% | -3% | -6% | -12% | -14% | -3% / -7% | +2.3 (4.3) / -0.1 (1.0) | n / Y |
| floor 6R / arm 2.0R keep 0.5 | -1% | -2% | -3% | -5% | -8% | -5% / +0% | -0.3 (0.2) / -0.1 (0.3) | n / n |
| floor 6R / arm 2.0R keep 0.75 | +18% | +1% | -3% | +2% | +1% | +1% / +1% | +0.0 (4.4) / -1.6 (2.6) | n / n |
| floor 6R / arm 3.0R keep 0.25 | +18% | -6% | -7% | -11% | -14% | -3% / -12% | +2.7 (4.6) / -0.4 (1.3) | n / Y |
| floor 6R / arm 3.0R keep 0.5 | +18% | -6% | -7% | -10% | -14% | -3% / -8% | +3.1 (4.6) / -0.5 (1.1) | n / Y |
| floor 6R / arm 3.0R keep 0.75 | +19% | -6% | -7% | -9% | -14% | +3% / -3% | +2.0 (5.8) / -1.5 (1.9) | n / n |
| floor 8R / no give-back | +19% | -5% | -4% | -6% | -7% | +2% / -10% | +3.0 (4.8) / -0.4 (1.3) | n / Y |
| floor 8R / arm 1.5R keep 0.25 | +11% | +6% | +8% | -8% | -25% | -11% / -5% | +0.6 (5.4) / -1.3 (2.8) | n / Y |
| floor 8R / arm 1.5R keep 0.5 | -12% | +0% | +15% | -12% | -13% | -8% / -0% | -1.0 (4.6) / -2.7 (3.1) | n / n |
| floor 8R / arm 1.5R keep 0.75 | +21% | +18% | +19% | -17% | +1% | -1% / -15% | -3.9 (9.1) / -4.8 (4.2) | n / n |
| floor 8R / arm 2.0R keep 0.25 | +20% | -3% | -2% | -8% | -7% | +2% / -7% | +2.5 (4.5) / -0.1 (1.0) | n / Y |
| floor 8R / arm 2.0R keep 0.5 | +0% | +0% | +0% | +0% | +0% | +0% / +0% | +0.0 (0.0) / -0.0 (0.0) | n / n |
| floor 8R / arm 2.0R keep 0.75 | +19% | +2% | +1% | +6% | +10% | +1% / +1% | +0.2 (4.4) / -1.6 (2.5) | n / n |
| floor 8R / arm 3.0R keep 0.25 | +19% | -5% | -4% | -6% | -7% | +2% / -10% | +3.0 (4.8) / -0.4 (1.3) | n / Y |
| floor 8R / arm 3.0R keep 0.5 | +19% | -5% | -4% | -5% | -7% | +2% / -6% | +3.3 (4.8) / -0.4 (1.1) | n / Y |
| floor 8R / arm 3.0R keep 0.75 | +20% | -5% | -4% | -4% | -7% | +3% / -1% | +2.1 (5.9) / -1.4 (1.8) | n / n |
| floor none / no give-back | +19% | -5% | -4% | -6% | -7% | +2% / -10% | +3.0 (4.8) / -0.3 (1.3) | n / Y |
| floor none / arm 1.5R keep 0.25 | +11% | +6% | +8% | -8% | -25% | -11% / -5% | +0.6 (5.4) / -1.3 (2.8) | n / Y |
| floor none / arm 1.5R keep 0.5 | -12% | +0% | +15% | -12% | -13% | -7% / -0% | -1.0 (4.6) / -2.7 (3.1) | n / n |
| floor none / arm 1.5R keep 0.75 | +21% | +17% | +19% | -16% | +1% | -1% / -15% | -3.9 (9.1) / -4.7 (4.2) | n / n |
| floor none / arm 2.0R keep 0.25 | +20% | -3% | -2% | -8% | -7% | +2% / -7% | +2.5 (4.5) / -0.1 (1.0) | n / Y |
| floor none / arm 2.0R keep 0.5 | +0% | +0% | +0% | +0% | +0% | +0% / +0% | +0.0 (0.0) / +0.0 (0.0) | Y / Y |
| floor none / arm 2.0R keep 0.75 | +19% | +2% | +1% | +6% | +10% | +1% / +1% | +0.2 (4.4) / -1.6 (2.5) | n / n |
| floor none / arm 3.0R keep 0.25 | +19% | -5% | -4% | -6% | -7% | +2% / -10% | +3.0 (4.8) / -0.4 (1.3) | n / Y |
| floor none / arm 3.0R keep 0.5 | +19% | -5% | -4% | -5% | -7% | +2% / -6% | +3.3 (4.8) / -0.4 (1.1) | n / Y |
| floor none / arm 3.0R keep 0.75 | +20% | -5% | -4% | -4% | -7% | +3% / -1% | +2.1 (5.9) / -1.4 (1.8) | n / n |

### 5. Screens
Cells with PA9 cut > 0 on BOTH L6M and PRE (raw): floor 6R / arm 2.0R keep 0.75, floor 8R / arm 2.0R keep 0.75, floor 10R / arm 2.0R keep 0.75.
Cells with cut > 0 on both with the carrying episode dropped: floor 6R / arm 2.0R keep 0.75, floor 8R / arm 2.0R keep 0.75, floor 10R / arm 2.0R keep 0.75.
Of those, STRICT mean (L6M and PRE mean >= live): none; TOLERANT (>= -0.5 MDE): none.


### 6. One-episode warning (reported although the user has decided not to change the give-back)
Columns: the cut with the carrying episode of the reference removed, and the minimum over leaving out each single month of the window (both series). A cut that collapses when the episode or one month is removed is a single-episode result; the no-give-back and keep-0.75 cells are the cases to read this way.| cell | L6M cut | L6M dropped | L6M leave-one-month-out min | PRE cut | PRE dropped | PRE leave-one-month-out min |
|---|---|---|---|---|---|---|
| floor none / no give-back | +19% | +2% | +5% | -6% | -10% | -10% |
| floor none / arm 3.0R keep 0.75 | +20% | +3% | +7% | -4% | -1% | -11% |
| floor none / arm 2.0R keep 0.75 | +19% | +1% | +5% | +6% | +1% | -4% |
| floor 8R / arm 3.0R keep 0.5 | +19% | +2% | +5% | -5% | -6% | -8% |
| floor none / arm 2.0R keep 0.25 | +20% | +2% | +6% | -8% | -7% | -11% |
| floor 6R / no give-back | +18% | -3% | +2% | -11% | -11% | -15% |

### 7. Lot-shuffle placebo (BASE-4 recipe, Q1-A multipliers shuffled within book x session x month; preference over the live cell in the same world; positive = shallower; engine phase 0, PA9 scoring)
| cell | worlds | L6M maxDD | PRE maxDD | X' maxDD | HOLD maxDD |
|---|---|---|---|---|---|
| floor none / no give-back | 100 | real +19.4k vs placebo med -1.0k [-11.5,+5.8] rank 0.01 | real -6.1k vs placebo med -0.0k [-13.2,+5.9] rank 0.90 | real -5.7k vs placebo med +0.0k [-4.0,+7.5] rank 1.00 | real -6.1k vs placebo med -4.5k [-10.1,+6.2] rank 0.72 |
| floor none / arm 1.5R keep 0.25 | 100 | real +10.8k vs placebo med +0.2k [-19.3,+10.5] rank 0.02 | real -7.8k vs placebo med +0.0k [-11.5,+10.3] rank 0.89 | real -19.6k vs placebo med -1.8k [-10.4,+6.3] rank 1.00 | real +6.7k vs placebo med -3.4k [-13.5,+14.1] rank 0.09 |
| floor none / arm 1.5R keep 0.5 | 100 | real -12.4k vs placebo med +1.8k [-11.5,+11.3] rank 0.97 | real -12.2k vs placebo med +0.0k [-8.6,+13.2] rank 0.99 | real -10.0k vs placebo med -1.9k [-8.7,+8.8] rank 0.99 | real +0.3k vs placebo med +2.8k [-15.1,+20.5] rank 0.72 |
| floor none / arm 1.5R keep 0.75 | 100 | real +21.6k vs placebo med +11.0k [-5.3,+27.4] rank 0.07 | real -15.8k vs placebo med -0.4k [-21.6,+20.7] rank 0.90 | real +0.7k vs placebo med +2.4k [-6.2,+17.8] rank 0.65 | real +19.8k vs placebo med +10.0k [-7.2,+33.3] rank 0.19 |
| floor none / arm 2.0R keep 0.25 | 100 | real +20.4k vs placebo med -0.5k [-8.3,+5.8] rank 0.01 | real -7.8k vs placebo med -1.1k [-11.1,+3.6] rank 0.91 | real -5.7k vs placebo med -0.0k [-4.7,+2.7] rank 0.98 | real -3.1k vs placebo med -2.9k [-10.9,+5.5] rank 0.53 |
| floor none / arm 2.0R keep 0.75 | 100 | real +19.3k vs placebo med +5.1k [-8.2,+16.7] rank 0.02 | real +6.5k vs placebo med +0.9k [-23.1,+11.3] rank 0.16 | real +8.0k vs placebo med +1.2k [-3.5,+8.8] rank 0.05 | real +2.7k vs placebo med +5.4k [-1.2,+14.8] rank 0.80 |
| floor none / arm 3.0R keep 0.25 | 100 | real +19.4k vs placebo med -1.2k [-11.5,+5.8] rank 0.01 | real -6.1k vs placebo med -0.4k [-13.2,+4.4] rank 0.88 | real -5.7k vs placebo med +0.0k [-4.0,+7.5] rank 1.00 | real -6.1k vs placebo med -4.3k [-9.9,+6.6] rank 0.76 |
| floor none / arm 3.0R keep 0.5 | 100 | real +19.4k vs placebo med -1.2k [-11.3,+5.8] rank 0.01 | real -5.5k vs placebo med +0.0k [-14.6,+4.4] rank 0.88 | real -5.7k vs placebo med +0.0k [-4.0,+7.5] rank 1.00 | real -6.1k vs placebo med -3.3k [-9.5,+8.3] rank 0.85 |
| floor none / arm 3.0R keep 0.75 | 100 | real +20.2k vs placebo med +0.3k [-9.5,+6.9] rank 0.01 | real -4.3k vs placebo med +0.1k [-15.4,+8.3] rank 0.81 | real -5.7k vs placebo med +0.0k [-4.0,+7.6] rank 1.00 | real -6.1k vs placebo med -1.8k [-8.6,+10.3] rank 0.90 |
| floor 6R / no give-back | 100 | real +17.7k vs placebo med -3.6k [-12.9,+4.3] rank 0.01 | real -7.2k vs placebo med -0.4k [-13.9,+5.8] rank 0.90 | real -5.7k vs placebo med +0.0k [-4.0,+7.9] rank 1.00 | real +0.5k vs placebo med -5.1k [-21.6,+17.6] rank 0.33 |
| floor 6R / arm 1.5R keep 0.25 | 100 | real +7.1k vs placebo med -2.4k [-23.4,+9.1] rank 0.05 | real -8.9k vs placebo med -0.2k [-11.5,+11.4] rank 0.95 | real -19.6k vs placebo med -1.7k [-10.1,+6.3] rank 1.00 | real +10.9k vs placebo med -5.5k [-30.1,+17.5] rank 0.13 |
| floor 6R / arm 1.5R keep 0.5 | 100 | real -14.0k vs placebo med -1.6k [-15.3,+9.9] rank 0.96 | real -13.3k vs placebo med -0.1k [-8.3,+13.4] rank 0.99 | real -10.0k vs placebo med -1.7k [-8.7,+8.9] rank 1.00 | real -1.3k vs placebo med -0.0k [-21.5,+24.9] rank 0.56 |
| floor 6R / arm 1.5R keep 0.75 | 100 | real +18.4k vs placebo med +8.7k [-6.3,+22.0] rank 0.06 | real -19.0k vs placebo med +0.0k [-21.6,+20.7] rank 0.93 | real +0.7k vs placebo med +2.7k [-5.8,+18.3] rank 0.66 | real +23.8k vs placebo med +7.7k [-17.3,+35.5] rank 0.16 |
| floor 6R / arm 2.0R keep 0.25 | 100 | real +18.7k vs placebo med -2.6k [-10.6,+3.7] rank 0.01 | real -8.9k vs placebo med -1.0k [-14.8,+4.0] rank 0.91 | real -5.7k vs placebo med -0.0k [-4.7,+3.1] rank 0.98 | real +2.6k vs placebo med -4.0k [-22.1,+18.2] rank 0.27 |
| floor 6R / arm 2.0R keep 0.5 | 100 | real -0.5k vs placebo med -1.9k [-7.3,-0.2] rank 0.12 | real -1.1k vs placebo med +0.0k [-3.8,+1.6] rank 0.92 | real +0.0k vs placebo med +0.0k [+0.0,+1.4] rank 1.00 | real +3.4k vs placebo med -1.4k [-19.5,+18.9] rank 0.23 |
| floor 6R / arm 2.0R keep 0.75 | 100 | real +18.1k vs placebo med +3.5k [-11.3,+14.9] rank 0.02 | real +5.3k vs placebo med +0.7k [-25.0,+11.7] rank 0.20 | real +8.0k vs placebo med +1.7k [-3.0,+9.1] rank 0.05 | real +6.7k vs placebo med +2.5k [-14.2,+23.5] rank 0.27 |
| floor 6R / arm 3.0R keep 0.25 | 100 | real +17.7k vs placebo med -3.6k [-12.9,+4.3] rank 0.01 | real -7.2k vs placebo med -0.6k [-14.9,+4.6] rank 0.90 | real -5.7k vs placebo med +0.0k [-4.0,+7.9] rank 1.00 | real +0.5k vs placebo med -5.2k [-21.1,+18.0] rank 0.34 |
| floor 6R / arm 3.0R keep 0.5 | 100 | real +17.7k vs placebo med -3.6k [-12.9,+4.3] rank 0.01 | real -6.6k vs placebo med -0.0k [-16.5,+4.7] rank 0.91 | real -5.7k vs placebo med +0.0k [-4.0,+7.9] rank 1.00 | real +0.5k vs placebo med -4.5k [-18.4,+18.7] rank 0.37 |
| floor 6R / arm 3.0R keep 0.75 | 100 | real +19.1k vs placebo med -2.3k [-11.2,+5.8] rank 0.01 | real -5.4k vs placebo med +0.1k [-16.2,+8.3] rank 0.83 | real -5.7k vs placebo med +0.0k [-4.0,+8.0] rank 1.00 | real +0.5k vs placebo med -3.7k [-16.8,+21.5] rank 0.44 |
| floor 8R / no give-back | 100 | real +19.4k vs placebo med -1.4k [-12.7,+5.8] rank 0.01 | real -6.1k vs placebo med -0.0k [-13.2,+5.9] rank 0.90 | real -5.7k vs placebo med +0.0k [-4.0,+7.5] rank 1.00 | real -6.1k vs placebo med -4.3k [-10.9,+6.0] rank 0.72 |
| floor 8R / arm 1.5R keep 0.25 | 100 | real +10.8k vs placebo med +0.2k [-21.0,+10.5] rank 0.02 | real -7.8k vs placebo med +0.0k [-11.5,+10.3] rank 0.89 | real -19.6k vs placebo med -1.8k [-10.4,+6.3] rank 1.00 | real +6.7k vs placebo med -3.3k [-13.5,+14.2] rank 0.10 |
| floor 8R / arm 1.5R keep 0.5 | 100 | real -12.4k vs placebo med +1.4k [-11.7,+11.3] rank 0.97 | real -12.2k vs placebo med +0.0k [-8.6,+13.2] rank 0.99 | real -10.0k vs placebo med -1.9k [-8.7,+8.8] rank 0.99 | real +0.3k vs placebo med +2.9k [-15.1,+21.7] rank 0.73 |
| floor 8R / arm 1.5R keep 0.75 | 100 | real +21.6k vs placebo med +10.5k [-5.3,+27.4] rank 0.07 | real -15.8k vs placebo med -0.4k [-21.6,+20.7] rank 0.90 | real +0.7k vs placebo med +2.4k [-6.2,+17.8] rank 0.65 | real +19.8k vs placebo med +10.1k [-5.8,+33.1] rank 0.21 |
| floor 8R / arm 2.0R keep 0.25 | 100 | real +20.4k vs placebo med -0.5k [-9.6,+5.8] rank 0.01 | real -7.8k vs placebo med -1.1k [-11.1,+3.6] rank 0.91 | real -5.7k vs placebo med -0.0k [-4.7,+2.7] rank 0.98 | real -3.1k vs placebo med -2.9k [-10.9,+6.2] rank 0.52 |
| floor 8R / arm 2.0R keep 0.5 | 100 | real +0.0k vs placebo med +0.0k [-4.6,+0.0] rank 0.90 | real +0.0k vs placebo med +0.0k [+0.0,+0.0] rank 0.98 | real +0.0k vs placebo med +0.0k [+0.0,+0.0] rank 1.00 | real +0.0k vs placebo med +0.0k [-0.2,+5.6] rank 0.97 |
| floor 8R / arm 2.0R keep 0.75 | 100 | real +19.3k vs placebo med +4.6k [-8.5,+16.7] rank 0.02 | real +6.5k vs placebo med +1.0k [-23.3,+11.3] rank 0.16 | real +8.0k vs placebo med +1.2k [-3.5,+8.8] rank 0.05 | real +2.7k vs placebo med +5.5k [-1.2,+14.8] rank 0.81 |
| floor 8R / arm 3.0R keep 0.25 | 100 | real +19.4k vs placebo med -1.4k [-12.7,+5.8] rank 0.01 | real -6.1k vs placebo med -0.4k [-13.2,+4.4] rank 0.88 | real -5.7k vs placebo med +0.0k [-4.0,+7.5] rank 1.00 | real -6.1k vs placebo med -4.1k [-10.9,+6.6] rank 0.76 |
| floor 8R / arm 3.0R keep 0.5 | 100 | real +19.4k vs placebo med -1.4k [-12.7,+5.8] rank 0.01 | real -5.5k vs placebo med +0.0k [-14.7,+4.4] rank 0.88 | real -5.7k vs placebo med +0.0k [-4.0,+7.5] rank 1.00 | real -6.1k vs placebo med -3.0k [-9.9,+8.4] rank 0.85 |
| floor 8R / arm 3.0R keep 0.75 | 100 | real +20.2k vs placebo med +0.0k [-11.6,+6.9] rank 0.01 | real -4.3k vs placebo med +0.1k [-15.4,+8.3] rank 0.81 | real -5.7k vs placebo med +0.0k [-4.0,+7.6] rank 1.00 | real -6.1k vs placebo med -1.7k [-9.5,+10.3] rank 0.90 |
| floor 10R / no give-back | 100 | real +19.4k vs placebo med -1.0k [-11.5,+5.8] rank 0.01 | real -6.1k vs placebo med -0.0k [-13.2,+5.9] rank 0.90 | real -5.7k vs placebo med +0.0k [-4.0,+7.5] rank 1.00 | real -6.1k vs placebo med -4.5k [-10.1,+6.2] rank 0.72 |
| floor 12R / no give-back | 100 | real +19.4k vs placebo med -1.0k [-11.5,+5.8] rank 0.01 | real -6.1k vs placebo med -0.0k [-13.2,+5.9] rank 0.90 | real -5.7k vs placebo med +0.0k [-4.0,+7.5] rank 1.00 | real -6.1k vs placebo med -4.5k [-10.1,+6.2] rank 0.72 |
| floor 12R / arm 3.0R keep 0.5 | 100 | real +19.4k vs placebo med -1.2k [-11.3,+5.8] rank 0.01 | real -5.5k vs placebo med +0.0k [-14.6,+4.4] rank 0.88 | real -5.7k vs placebo med +0.0k [-4.0,+7.5] rank 1.00 | real -6.1k vs placebo med -3.3k [-9.5,+8.3] rank 0.85 |
| floor 16R / no give-back | 100 | real +19.4k vs placebo med -1.0k [-11.5,+5.8] rank 0.01 | real -6.1k vs placebo med -0.0k [-13.2,+5.9] rank 0.90 | real -5.7k vs placebo med +0.0k [-4.0,+7.5] rank 1.00 | real -6.1k vs placebo med -4.5k [-10.1,+6.2] rank 0.72 |

### 8. Family-wise best-of-29 null (cells with distinct series: floors 6R, 8R, none x 10 give-backs, live excluded), 100 lot-shuffle worlds, engine phase 0, PA9 scoring
Real best S1 = mean(PRE cut, X' cut) 0.084 vs null median 0.044 / 95th 0.105 -> rank 0.099; real best S2 = min(L6M cut, PRE cut) 0.064 vs null median 0.028 / 95th 0.128 -> rank 0.257.

Correction (Z1): in the one-paragraph answer, "floor 8R differs by less than $25" holds only for the live give-back; 8R differs from none by small amounts in other give-back variants (see section 4), and floor 6R is worse than none on PRE for most give-backs (-30 -17Correction (Z1): in the one-paragraph answer, "floor 8R differs by less than $25" holds only for the live give-back; 8R differs slightly from none in other give-back variants (section 4), and floor 6R is worse than none on PRE for most give-backs (-3% to -17%) but +2% for arm 2R keep 0.75.
