# DS3_SIZER_S35B: lock family cells that can bind under Q1-A (Z1, 2026-11-03T18:44Z) POST-HOC, no PASS, Shadow only
Prereg l2vast/ds3/prereg/SIZER_S35B_Z1_prereg.md sha256 09ecf5111249eff06c95c232fd48b6e3fab5b24ac230caa46e595f798dbaaffb in DECISIONS.md before any statistic; dead_lookup first (4 queries, 0 hits); ledger program SIZER_S35B (229 cells) appended after. Base run_v13t_ts2 (Q1-A), cached live lots (live cell reproduces SIZER_S35 / BASE-4 to $0.003), genuine PA9 (9 engine lock-reset phases x matched scoring week key), carrying episodes of the live cell dropped (L6M ISO 202630..202637, PRE 202506..202509), cuts vs the LIVE cell (floor 12R, give-back 2R keep .5, caps +5R/-2R). Labels: RISK-KEEP = positive cuts bought with mean (Calmar below the live cell, i.e. worse than simply trading smaller), ONE-WINDOW, DEAD, CANDIDATE (tolerant mean).

## Answer in one paragraph
Under Q1-A the lock does very little and nothing in these families beats it. (4) The live 12R week floor fires in 0 weeks in every book (it first fires at 6R: 8 book-weeks; 5R 19; 4R 47; 3R 113 over 3.5 years; 7R and above never), so the lock is only the give-back (arm 2R keep 0.5, 138 book-days: KB 45, PE 50, PB 24, MV 12, HM 6, SM 1) and the daily caps (-2R entry test skipped 432 entries, KB 263, PE 72, PB 47, MV 47; +5R skipped 62). Versus no lock at all the live lock cuts HOLD maxDD 139k -> 113k and MID 68k -> 58k, but DEEPENS L6M 84k -> 101k and costs mean (L6M 29.3k -> 27.5k); the caps alone are the useful part (L6M 81k, HOLD 119k, mean 30.4k / 24.2k vs no lock 29.3k / 23.3k), the give-back alone deepens L6M (93k) and cuts mean. (1) Lower R floors 3/4/5R: the cuts are one-window (L6M +17..+26%, PRE -2..-34%); only 4R with give-back none or arm 2R keep .25 keeps the mean (L6M +25/+26%, PRE -2/-4%, dropped L6M +2%) and is ONE-WINDOW. Dollar floors 4k/6k/8k/10k per book per week cut every window (4k: L6M +34%, HOLD +36%, MID +34%, PRE +20..38%, dropped L6M +66% / PRE +39%) but the floor fires in 472 / 325 / 219 / 157 book-weeks and the cost is 55% of the mean (4k: L6M -14.8k of 27.5k, PRE -7.5k of 13.3k, Calmar x0.5-0.77 of live): RISK-KEEP, not better than trading smaller; lot-shuffle ranks for the best three $ cells: L6M 0.04-0.07, PRE 0.15-0.49, X' 0.84-0.93 (wrong side). (2) Daily caps: the win cap does nothing below 5R except at 3R/4R (L6M 0%, PRE +4%), the loss cap 1.5R cuts PRE +6% but L6M -7% with mean -3..-4k, 2.5R cuts L6M +10% (dropped +7..+16%) but PRE -5%; loss caps of 4R and above are inert; no cap pair is positive on both windows with the mean intact (the best, loss 2.5R / win 3R, L6M +10% / PRE 0% with placebo rank 0.06 / 0.32 = ONE-WINDOW). (3) Proportional lock R (NOT live): scaling the R by the Q1-A multiplier or by the actual lots makes the lock far more active (give-back fires 483-1,570 book-days instead of 138, -cap skips 1,420-1,650 instead of 432, the 12R floor fires 1-13 weeks) and is worse: PRE cut -2..-30% for every cell, L6M +17..+38% only for no-give-back / arm 3R / arm 2R keep .25 variants that collapse with the carrying episode dropped (-12..+17%); no cell is positive on both windows with the episode dropped and the mean intact. Conclusion: no flag; the live floor is a no-op, the live give-back and caps are the whole lock, and under size-down-only none of the tested alternatives improves them at the same mean.

### 0. What the lock does at all under Q1-A (ts2): PA9 maxDD / PA9 mean per week, and how often each part fires over the whole history (935 days, 8 books)
| configuration | L6M | HOLD | MID | PRE | X' | weeks floor fired | days give-back fired | entries skipped by +cap | entries skipped by -cap |
|---|---|---|---|---|---|---|---|---|---|
| no lock at all | 84k / 29.3k | 139k / 23.3k | 68k / 15.0k | 112k / 12.3k | 82k / 3.2k | 0 | 0 | 0 | 0 |
| daily caps only (+5R/-2R) | 81k / 30.4k | 119k / 24.2k | 60k / 16.3k | 107k / 13.0k | 83k / 3.4k | 0 | 0 | 62 | 432 |
| give-back only (arm 2R keep .5) | 93k / 26.3k | 132k / 21.5k | 66k / 14.6k | 106k / 12.8k | 77k / 3.1k | 0 | 139 | 0 | 0 |
| week floor only (12R) | 84k / 29.3k | 139k / 23.3k | 68k / 15.0k | 112k / 12.3k | 82k / 3.2k | 0 | 0 | 0 | 0 |
| LIVE: floor 12R + give-back 2R/.5 + caps | 101k / 27.5k | 113k / 22.4k | 58k / 16.0k | 101k / 13.3k | 77k / 3.3k | 0 | 138 | 62 | 432 |

Live cell by book (R dollars per book: PE 8400, HM 4800, SM 4800, KB 2400, MV 2400, PB 1200): HM: floor weeks 0, give-back days 6, +cap skips 0, -cap skips 3; KB: floor weeks 0, give-back days 45, +cap skips 44, -cap skips 263; SM: floor weeks 0, give-back days 1, +cap skips 0, -cap skips 0; PE: floor weeks 0, give-back days 50, +cap skips 17, -cap skips 72; MV: floor weeks 0, give-back days 12, +cap skips 0, -cap skips 47; PB: floor weeks 0, give-back days 24, +cap skips 1, -cap skips 47. The two books ST and WT carry no live signals.

### 1. Lower week floors 3R / 4R / 5R (live lots, caps as live)
| cell | PA9 cut L6M | HOLD | MID | PRE | X' | dropped L6M / PRE | mean d L6M / PRE $k (MDE) | strict / tol | Calmar vs live L6M / PRE | label | weeks floor fired / give-back days / +cap skips / -cap skips |
|---|---|---|---|---|---|---|---|---|---|---|---|
| floor 3R / no give-back / caps +5R -2R | +21% | +20% | -2% | -14% | -9% | +12% / -11% | +1.8 (5.2) / -1.5 (1.9) | n / n | x1.35 / x0.78 | ONE-WINDOW | 111 / 0 / 62 / 432 |
| floor 3R / arm 1.5R keep 0.25 / caps +5R -2R | +19% | +25% | +7% | -11% | -27% | +2% / -10% | -0.1 (5.7) / -2.3 (3.3) | n / n | x1.23 / x0.75 | ONE-WINDOW | 110 / 159 / 62 / 432 |
| floor 3R / arm 1.5R keep 0.5 / caps +5R -2R | -3% | +9% | +16% | -19% | -18% | +3% / -16% | -1.4 (5.4) / -3.6 (3.4) | n / n | x0.92 / x0.62 | DEAD | 110 / 346 / 62 / 432 |
| floor 3R / arm 1.5R keep 0.75 / caps +5R -2R | +21% | +25% | +19% | -34% | -6% | +11% / -25% | -4.4 (9.5) / -5.5 (4.4) | n / n | x1.06 / x0.44 | ONE-WINDOW | 105 / 615 / 62 / 432 |
| floor 3R / arm 2R keep 0.25 / caps +5R -2R | +22% | +22% | +0% | -13% | -9% | +12% / -11% | +1.4 (4.7) / -1.1 (2.0) | n / n | x1.34 / x0.81 | ONE-WINDOW | 113 / 44 / 62 / 432 |
| floor 3R / arm 2R keep 0.5 / caps +5R -2R | +7% | +12% | +7% | -9% | -5% | +10% / -11% | -0.7 (3.4) / -1.1 (1.5) | n / n | x1.05 / x0.84 | ONE-WINDOW | 113 / 138 / 62 / 432 |
| floor 3R / arm 2R keep 0.75 / caps +5R -2R | +20% | +22% | +11% | -7% | +0% | +13% / -12% | -0.6 (5.1) / -2.5 (3.0) | n / n | x1.22 / x0.76 | ONE-WINDOW | 109 / 306 / 62 / 432 |
| floor 3R / arm 3R keep 0.25 / caps +5R -2R | +21% | +20% | -2% | -14% | -9% | +12% / -11% | +1.8 (5.2) / -1.5 (1.9) | n / n | x1.35 / x0.78 | ONE-WINDOW | 111 / 2 / 62 / 432 |
| floor 3R / arm 3R keep 0.5 / caps +5R -2R | +21% | +20% | -2% | -14% | -9% | +12% / -10% | +2.1 (5.2) / -1.5 (1.7) | n / n | x1.36 / x0.78 | ONE-WINDOW | 112 / 17 / 62 / 432 |
| floor 3R / arm 3R keep 0.75 / caps +5R -2R | +22% | +20% | -2% | -24% | -9% | +12% / -10% | +1.0 (6.1) / -2.3 (2.2) | n / n | x1.33 / x0.67 | ONE-WINDOW | 111 / 72 / 62 / 432 |
| floor 4R / no give-back / caps +5R -2R | +25% | +8% | -6% | -2% | -11% | +2% / -5% | +2.8 (5.0) / -0.7 (1.5) | n / Y | x1.46 / x0.93 | ONE-WINDOW | 46 / 0 / 62 / 432 |
| floor 4R / arm 1.5R keep 0.25 / caps +5R -2R | +17% | +14% | +5% | -4% | -29% | -12% / -4% | +0.5 (5.9) / -1.8 (2.9) | n / n | x1.22 / x0.83 | ONE-WINDOW | 48 / 158 / 62 / 432 |
| floor 4R / arm 1.5R keep 0.5 / caps +5R -2R | -12% | +0% | +9% | -8% | -19% | -9% / -2% | -1.0 (5.2) / -2.9 (3.2) | n / n | x0.86 / x0.72 | DEAD | 48 / 346 / 62 / 432 |
| floor 4R / arm 1.5R keep 0.75 / caps +5R -2R | +18% | +23% | +22% | -16% | -5% | -2% / -16% | -4.0 (9.5) / -4.9 (4.2) | n / n | x1.04 / x0.55 | ONE-WINDOW | 46 / 614 / 62 / 432 |
| floor 4R / arm 2R keep 0.25 / caps +5R -2R | +26% | +10% | -4% | -4% | -11% | +2% / -6% | +2.4 (4.7) / -0.4 (1.2) | n / Y | x1.46 / x0.93 | ONE-WINDOW | 47 / 44 / 62 / 432 |
| floor 4R / arm 2R keep 0.5 / caps +5R -2R | +1% | +5% | -1% | +2% | -6% | -0% / -3% | -0.0 (1.0) / -0.4 (0.8) | n / n | x1.01 / x0.99 | ONE-WINDOW | 47 / 138 / 62 / 432 |
| floor 4R / arm 2R keep 0.75 / caps +5R -2R | +23% | +14% | +1% | +7% | +2% | +1% / -1% | +0.1 (4.6) / -1.9 (2.7) | n / n | x1.30 / x0.92 | ONE-WINDOW | 45 / 306 / 62 / 432 |
| floor 4R / arm 3R keep 0.25 / caps +5R -2R | +25% | +8% | -6% | -2% | -11% | +2% / -6% | +2.8 (5.0) / -0.7 (1.5) | n / Y | x1.46 / x0.93 | ONE-WINDOW | 46 / 2 / 62 / 432 |
| floor 4R / arm 3R keep 0.5 / caps +5R -2R | +25% | +8% | -6% | -2% | -11% | +2% / -2% | +3.1 (4.9) / -0.7 (1.3) | n / n | x1.48 / x0.93 | ONE-WINDOW | 46 / 17 / 62 / 432 |
| floor 4R / arm 3R keep 0.75 / caps +5R -2R | +26% | +8% | -6% | -7% | -11% | +2% / -1% | +1.9 (6.1) / -1.6 (1.9) | n / n | x1.44 / x0.82 | ONE-WINDOW | 46 / 72 / 62 / 432 |
| floor 5R / no give-back / caps +5R -2R | +14% | -3% | -10% | -11% | -11% | -5% / -9% | +2.3 (5.0) / -0.5 (1.3) | n / Y | x1.26 / x0.87 | ONE-WINDOW | 21 / 0 / 62 / 432 |
| floor 5R / arm 1.5R keep 0.25 / caps +5R -2R | +4% | +7% | +8% | -12% | -29% | -17% / -7% | -0.1 (6.2) / -1.5 (2.8) | n / n | x1.04 / x0.79 | ONE-WINDOW | 20 / 158 / 62 / 432 |
| floor 5R / arm 1.5R keep 0.5 / caps +5R -2R | -19% | -6% | +14% | -17% | -17% | -14% / -0% | -1.6 (4.4) / -2.8 (3.1) | n / n | x0.79 / x0.68 | DEAD | 17 / 346 / 62 / 432 |
| floor 5R / arm 1.5R keep 0.75 / caps +5R -2R | +13% | +18% | +15% | -25% | -4% | -8% / -15% | -4.5 (9.0) / -4.9 (4.2) | n / n | x0.96 / x0.51 | ONE-WINDOW | 17 / 614 / 62 / 432 |
| floor 5R / arm 2R keep 0.25 / caps +5R -2R | +15% | -1% | -8% | -12% | -11% | -5% / -9% | +1.9 (4.6) / -0.2 (1.0) | n / Y | x1.26 / x0.88 | ONE-WINDOW | 21 / 44 / 62 / 432 |
| floor 5R / arm 2R keep 0.5 / caps +5R -2R | -7% | -1% | -6% | -5% | -4% | -7% / -5% | -0.6 (1.0) / -0.2 (0.2) | n / n | x0.91 / x0.94 | DEAD | 19 / 138 / 62 / 432 |
| floor 5R / arm 2R keep 0.75 / caps +5R -2R | +15% | +3% | -5% | +1% | +5% | -5% / -0% | -0.4 (4.5) / -1.7 (2.6) | n / n | x1.17 / x0.88 | ONE-WINDOW | 20 / 306 / 62 / 432 |
| floor 5R / arm 3R keep 0.25 / caps +5R -2R | +14% | -3% | -10% | -11% | -11% | -5% / -9% | +2.3 (5.0) / -0.5 (1.3) | n / Y | x1.26 / x0.87 | ONE-WINDOW | 21 / 2 / 62 / 432 |
| floor 5R / arm 3R keep 0.5 / caps +5R -2R | +14% | -3% | -10% | -10% | -11% | -5% / -5% | +2.7 (4.9) / -0.5 (1.1) | n / Y | x1.28 / x0.87 | ONE-WINDOW | 21 / 17 / 62 / 432 |
| floor 5R / arm 3R keep 0.75 / caps +5R -2R | +15% | -3% | -10% | -9% | -11% | -4% / -1% | +1.4 (6.1) / -1.5 (1.9) | n / n | x1.24 / x0.82 | ONE-WINDOW | 21 / 72 / 62 / 432 |

### 1b. Week floor in DOLLARS per book per week (4k / 6k / 8k / 10k)
| cell | PA9 cut L6M | HOLD | MID | PRE | X' | dropped L6M / PRE | mean d L6M / PRE $k (MDE) | strict / tol | Calmar vs live L6M / PRE | label | weeks floor fired / give-back days / +cap skips / -cap skips |
|---|---|---|---|---|---|---|---|---|---|---|---|
| floor $4k / no give-back / caps +5R -2R | +34% | +36% | +34% | +23% | +4% | +66% / +39% | -14.8 (17.5) / -7.4 (6.8) | n / n | x0.69 / x0.58 | RISK-KEEP | 472 / 0 / 62 / 432 |
| floor $4k / arm 1.5R keep 0.25 / caps +5R -2R | +31% | +34% | +34% | +32% | +1% | +58% / +39% | -15.4 (17.3) / -8.1 (7.3) | n / n | x0.64 / x0.58 | RISK-KEEP | 471 / 159 / 62 / 432 |
| floor $4k / arm 1.5R keep 0.5 / caps +5R -2R | +26% | +31% | +34% | +32% | +8% | +58% / +32% | -16.9 (18.9) / -8.6 (7.3) | n / n | x0.52 / x0.52 | RISK-KEEP | 473 / 347 / 62 / 432 |
| floor $4k / arm 1.5R keep 0.75 / caps +5R -2R | +36% | +32% | +31% | +9% | +17% | +61% / +23% | -18.8 (20.0) / -9.7 (7.5) | n / n | x0.49 / x0.30 | RISK-KEEP | 473 / 615 / 62 / 432 |
| floor $4k / arm 2R keep 0.25 / caps +5R -2R | +34% | +36% | +33% | +32% | +4% | +67% / +38% | -14.9 (17.5) / -7.1 (6.7) | n / n | x0.70 / x0.69 | RISK-KEEP | 469 / 44 / 62 / 432 |
| floor $4k / arm 2R keep 0.5 / caps +5R -2R | +27% | +31% | +32% | +38% | +4% | +65% / +38% | -15.5 (18.3) / -7.0 (6.7) | n / n | x0.60 / x0.77 | RISK-KEEP | 471 / 139 / 62 / 432 |
| floor $4k / arm 2R keep 0.75 / caps +5R -2R | +34% | +33% | +31% | +34% | +6% | +64% / +35% | -16.4 (18.6) / -8.1 (7.0) | n / n | x0.61 / x0.60 | RISK-KEEP | 468 / 307 / 62 / 432 |
| floor $4k / arm 3R keep 0.25 / caps +5R -2R | +34% | +36% | +34% | +23% | +4% | +66% / +39% | -14.8 (17.5) / -7.4 (6.8) | n / n | x0.69 / x0.58 | RISK-KEEP | 472 / 2 / 62 / 432 |
| floor $4k / arm 3R keep 0.5 / caps +5R -2R | +34% | +36% | +33% | +20% | +4% | +67% / +39% | -14.4 (17.8) / -7.5 (6.8) | n / n | x0.71 / x0.55 | RISK-KEEP | 472 / 17 / 62 / 432 |
| floor $4k / arm 3R keep 0.75 / caps +5R -2R | +34% | +36% | +33% | +18% | +4% | +67% / +39% | -15.2 (18.2) / -7.9 (6.8) | n / n | x0.68 / x0.49 | RISK-KEEP | 473 / 72 / 62 / 432 |
| floor $6k / no give-back / caps +5R -2R | +6% | +17% | +42% | +4% | +15% | +43% / +21% | -12.2 (14.9) / -6.1 (6.2) | n / n | x0.59 / x0.56 | RISK-KEEP | 325 / 0 / 62 / 432 |
| floor $6k / arm 1.5R keep 0.25 / caps +5R -2R | -0% | +11% | +43% | +14% | +13% | +32% / +22% | -13.2 (14.5) / -6.9 (6.6) | n / n | x0.52 / x0.56 | MIXED | 324 / 159 / 62 / 432 |
| floor $6k / arm 1.5R keep 0.5 / caps +5R -2R | -3% | +8% | +45% | +12% | +14% | +35% / +11% | -14.5 (15.4) / -7.5 (6.7) | n / n | x0.46 / x0.50 | MIXED | 323 / 346 / 62 / 432 |
| floor $6k / arm 1.5R keep 0.75 / caps +5R -2R | +11% | +21% | +45% | -7% | +15% | +42% / +9% | -15.2 (16.2) / -8.7 (7.1) | n / n | x0.50 / x0.33 | MIXED | 325 / 615 / 62 / 432 |
| floor $6k / arm 2R keep 0.25 / caps +5R -2R | +7% | +18% | +43% | +14% | +15% | +43% / +21% | -12.7 (15.0) / -5.7 (6.1) | n / n | x0.58 / x0.66 | RISK-KEEP | 324 / 44 / 62 / 432 |
| floor $6k / arm 2R keep 0.5 / caps +5R -2R | -1% | +10% | +45% | +15% | +16% | +47% / +18% | -13.4 (15.6) / -5.6 (6.1) | n / n | x0.51 / x0.68 | MIXED | 326 / 138 / 62 / 432 |
| floor $6k / arm 2R keep 0.75 / caps +5R -2R | +11% | +21% | +45% | +12% | +17% | +48% / +15% | -13.5 (15.5) / -6.8 (6.4) | n / n | x0.57 / x0.56 | RISK-KEEP | 325 / 306 / 62 / 432 |
| floor $6k / arm 3R keep 0.25 / caps +5R -2R | +6% | +17% | +42% | +4% | +15% | +43% / +21% | -12.2 (14.9) / -6.1 (6.2) | n / n | x0.59 / x0.56 | RISK-KEEP | 325 / 2 / 62 / 432 |
| floor $6k / arm 3R keep 0.5 / caps +5R -2R | +6% | +17% | +42% | -0% | +15% | +47% / +16% | -11.8 (15.0) / -6.3 (6.2) | n / n | x0.61 / x0.53 | MIXED | 325 / 17 / 62 / 432 |
| floor $6k / arm 3R keep 0.75 / caps +5R -2R | +7% | +17% | +42% | -3% | +15% | +48% / +18% | -12.7 (15.3) / -6.9 (6.3) | n / n | x0.58 / x0.47 | MIXED | 326 / 72 / 62 / 432 |
| floor $8k / no give-back / caps +5R -2R | -12% | +0% | +28% | +1% | +2% | +30% / +15% | -10.7 (11.6) / -5.2 (5.4) | n / n | x0.54 / x0.61 | MIXED | 219 / 0 / 62 / 432 |
| floor $8k / arm 1.5R keep 0.25 / caps +5R -2R | -21% | -8% | +30% | +14% | -4% | +13% / +16% | -11.2 (11.6) / -5.9 (5.7) | n / n | x0.49 / x0.64 | MIXED | 219 / 159 / 62 / 432 |
| floor $8k / arm 1.5R keep 0.5 / caps +5R -2R | -19% | -6% | +31% | +8% | -0% | +20% / +7% | -11.3 (12.2) / -6.4 (5.9) | n / n | x0.50 / x0.56 | MIXED | 219 / 347 / 62 / 432 |
| floor $8k / arm 1.5R keep 0.75 / caps +5R -2R | -11% | +2% | +31% | -12% | +3% | +29% / +3% | -14.0 (13.4) / -7.8 (6.1) | n / n | x0.44 / x0.37 | DEAD | 221 / 615 / 62 / 432 |
| floor $8k / arm 2R keep 0.25 / caps +5R -2R | -12% | +0% | +28% | +13% | +2% | +28% / +15% | -10.7 (11.7) / -4.9 (5.2) | n / n | x0.54 / x0.73 | MIXED | 219 / 44 / 62 / 432 |
| floor $8k / arm 2R keep 0.5 / caps +5R -2R | -16% | -3% | +30% | +16% | +4% | +34% / +14% | -11.2 (11.5) / -4.6 (5.3) | n / n | x0.51 / x0.78 | MIXED | 217 / 138 / 62 / 432 |
| floor $8k / arm 2R keep 0.75 / caps +5R -2R | -9% | +3% | +30% | +14% | +2% | +33% / +12% | -11.5 (11.8) / -5.9 (5.6) | n / n | x0.53 / x0.65 | MIXED | 216 / 306 / 62 / 432 |
| floor $8k / arm 3R keep 0.25 / caps +5R -2R | -12% | +0% | +28% | +1% | +2% | +30% / +15% | -10.7 (11.6) / -5.2 (5.4) | n / n | x0.54 / x0.61 | MIXED | 219 / 2 / 62 / 432 |
| floor $8k / arm 3R keep 0.5 / caps +5R -2R | -12% | +0% | +28% | -4% | +2% | +34% / +13% | -9.9 (11.6) / -5.4 (5.4) | n / n | x0.57 / x0.57 | DEAD | 219 / 17 / 62 / 432 |
| floor $8k / arm 3R keep 0.75 / caps +5R -2R | -13% | -0% | +28% | -8% | +2% | +35% / +14% | -10.9 (12.0) / -6.0 (5.5) | n / n | x0.53 / x0.51 | DEAD | 220 / 72 / 62 / 432 |
| floor $10k / no give-back / caps +5R -2R | -8% | +4% | +16% | -5% | -7% | +18% / +10% | -6.5 (10.4) / -4.6 (5.0) | n / n | x0.71 / x0.62 | DEAD | 159 / 0 / 62 / 432 |
| floor $10k / arm 1.5R keep 0.25 / caps +5R -2R | -15% | -2% | +17% | +15% | -14% | +5% / +13% | -7.5 (10.3) / -5.3 (5.5) | n / n | x0.63 / x0.71 | MIXED | 157 / 159 / 62 / 432 |
| floor $10k / arm 1.5R keep 0.5 / caps +5R -2R | -11% | +1% | +17% | +7% | -11% | +11% / +7% | -7.9 (11.0) / -6.0 (5.6) | n / n | x0.64 / x0.59 | MIXED | 155 / 348 / 62 / 432 |
| floor $10k / arm 1.5R keep 0.75 / caps +5R -2R | +4% | +15% | +16% | -10% | -6% | +22% / +3% | -11.0 (12.4) / -7.3 (5.9) | n / n | x0.62 / x0.41 | MIXED | 155 / 616 / 62 / 432 |
| floor $10k / arm 2R keep 0.25 / caps +5R -2R | -8% | +4% | +16% | +15% | -7% | +17% / +12% | -6.5 (10.4) / -4.0 (4.9) | n / n | x0.70 / x0.82 | MIXED | 158 / 44 / 62 / 432 |
| floor $10k / arm 2R keep 0.5 / caps +5R -2R | -8% | +4% | +17% | +14% | -6% | +21% / +11% | -7.6 (10.2) / -3.9 (5.0) | n / n | x0.67 / x0.82 | MIXED | 156 / 138 / 62 / 432 |
| floor $10k / arm 2R keep 0.75 / caps +5R -2R | +3% | +14% | +15% | +13% | -9% | +22% / +12% | -7.9 (10.7) / -5.1 (5.4) | n / n | x0.74 / x0.71 | RISK-KEEP | 157 / 306 / 62 / 432 |
| floor $10k / arm 3R keep 0.25 / caps +5R -2R | -8% | +4% | +16% | -5% | -7% | +18% / +10% | -6.5 (10.4) / -4.6 (5.0) | n / n | x0.71 / x0.62 | DEAD | 159 / 2 / 62 / 432 |
| floor $10k / arm 3R keep 0.5 / caps +5R -2R | -7% | +5% | +16% | -8% | -7% | +22% / +7% | -6.0 (10.5) / -4.8 (5.1) | n / n | x0.73 / x0.59 | DEAD | 159 / 17 / 62 / 432 |
| floor $10k / arm 3R keep 0.75 / caps +5R -2R | -5% | +7% | +16% | -13% | -7% | +23% / +8% | -7.2 (10.9) / -5.4 (5.2) | n / n | x0.70 / x0.53 | DEAD | 160 / 72 / 62 / 432 |

### 2. Daily caps swept (live floor and live give-back): PA9 cut L6M / PRE (carrying episodes dropped) and mean change $k/wk, columns = win cap
|  | win cap 3R | win cap 4R | win cap 5R | win cap 6R | win cap 8R | win cap none |
|---|---|---|---|---|---|---|
| loss cap 1.5R | -7% / +6% (drop -0% / -10%) mean -3.2 / -0.9 | -7% / +6% (drop -10% / -10%) mean -3.4 / -0.0 | -7% / +6% (drop -10% / -10%) mean -3.4 / -0.1 | -7% / +6% (drop -10% / -10%) mean -4.1 / -0.2 | -7% / +6% (drop -10% / -10%) mean -4.1 / -0.2 | -7% / +6% (drop -10% / -10%) mean -4.1 / -0.2 |
| loss cap 2R | +0% / +4% (drop +8% / +0%) mean +0.2 / -0.9 | +0% / +4% (drop +0% / +0%) mean +0.0 / +0.0 | +0% / +0% (drop +0% / +0%) mean +0.0 / +0.0 | +0% / +0% (drop +0% / +0%) mean -0.7 / -0.1 | +0% / +0% (drop +0% / +0%) mean -0.7 / -0.2 | +0% / +0% (drop +0% / +0%) mean -0.7 / -0.2 |
| loss cap 2.5R | +10% / -0% (drop +16% / -1%) mean +0.3 / -1.2 | +10% / -1% (drop +7% / -1%) mean +0.0 / -0.3 | +10% / -5% (drop +7% / -1%) mean +0.0 / -0.3 | +10% / -5% (drop +7% / -1%) mean -0.7 / -0.5 | +10% / -5% (drop +7% / -1%) mean -0.7 / -0.5 | +10% / -5% (drop +7% / -1%) mean -0.7 / -0.5 |
| loss cap 3R | +4% / -2% (drop +15% / -1%) mean -0.3 / -1.3 | +4% / -3% (drop +6% / -1%) mean -0.5 / -0.4 | +4% / -7% (drop +6% / -1%) mean -0.5 / -0.5 | +4% / -7% (drop +6% / -1%) mean -1.2 / -0.6 | +4% / -7% (drop +6% / -1%) mean -1.2 / -0.6 | +4% / -7% (drop +6% / -1%) mean -1.2 / -0.6 |
| loss cap 4R | +8% / -0% (drop +14% / -1%) mean -0.2 / -1.2 | +8% / -1% (drop +5% / -1%) mean -0.5 / -0.3 | +8% / -5% (drop +5% / -1%) mean -0.5 / -0.3 | +8% / -5% (drop +5% / -1%) mean -1.2 / -0.4 | +8% / -5% (drop +5% / -1%) mean -1.2 / -0.5 | +8% / -5% (drop +5% / -1%) mean -1.2 / -0.5 |
| loss cap none | +8% / -0% (drop +14% / -1%) mean -0.2 / -1.2 | +8% / -1% (drop +5% / -1%) mean -0.4 / -0.3 | +8% / -5% (drop +5% / -1%) mean -0.4 / -0.3 | +8% / -5% (drop +5% / -1%) mean -1.2 / -0.5 | +8% / -5% (drop +5% / -1%) mean -1.2 / -0.5 | +8% / -5% (drop +5% / -1%) mean -1.2 / -0.5 |

### 3. Lock R scaled proportionally, multiplier = Q1-A ER multiplier alone (0.5 / 1.0) (NOT live): full floor x give-back surface (cuts vs the LIVE cell)
| cell | PA9 cut L6M | HOLD | MID | PRE | X' | dropped L6M / PRE | mean d L6M / PRE $k (MDE) | strict / tol | Calmar vs live L6M / PRE | label | weeks floor fired / give-back days / +cap skips / -cap skips |
|---|---|---|---|---|---|---|---|---|---|---|---|
| [er-scaled R, NOT live] floor 6R / no give-back / caps +5R -2R | +31% | +18% | +9% | -22% | -12% | +16% / -15% | +1.9 (5.6) / -1.5 (1.7) | n / n | x1.54 / x0.72 | ONE-WINDOW | 113 / 0 / 342 / 1651 |
| [er-scaled R, NOT live] floor 6R / arm 1.5R keep 0.25 / caps +5R -2R | +25% | +20% | +15% | -30% | -40% | -1% / -10% | -2.4 (7.7) / -3.2 (3.5) | n / n | x1.22 / x0.59 | ONE-WINDOW | 105 / 709 / 342 / 1651 |
| [er-scaled R, NOT live] floor 6R / arm 1.5R keep 0.5 / caps +5R -2R | +3% | +9% | +22% | -15% | -23% | -1% / -6% | -3.6 (8.5) / -3.8 (3.7) | n / n | x0.89 / x0.62 | ONE-WINDOW | 100 / 1077 / 342 / 1654 |
| [er-scaled R, NOT live] floor 6R / arm 1.5R keep 0.75 / caps +5R -2R | +32% | +31% | +34% | -35% | -13% | +7% / -19% | -5.9 (11.8) / -5.8 (4.6) | n / n | x1.15 / x0.42 | ONE-WINDOW | 102 / 1574 / 342 / 1655 |
| [er-scaled R, NOT live] floor 6R / arm 2R keep 0.25 / caps +5R -2R | +38% | +23% | +16% | -26% | -27% | +10% / -15% | -0.5 (6.4) / -1.4 (2.4) | n / n | x1.57 / x0.71 | ONE-WINDOW | 110 / 351 / 342 / 1651 |
| [er-scaled R, NOT live] floor 6R / arm 2R keep 0.5 / caps +5R -2R | +22% | +18% | +18% | -17% | -20% | +9% / -7% | -3.4 (6.8) / -0.9 (1.8) | n / n | x1.12 / x0.80 | ONE-WINDOW | 108 / 591 / 342 / 1654 |
| [er-scaled R, NOT live] floor 6R / arm 2R keep 0.75 / caps +5R -2R | +34% | +28% | +22% | -12% | -13% | +12% / +2% | -2.9 (8.1) / -2.5 (3.1) | n / n | x1.36 / x0.72 | MIXED | 111 / 1001 / 342 / 1655 |
| [er-scaled R, NOT live] floor 6R / arm 3R keep 0.25 / caps +5R -2R | +31% | +19% | +9% | -22% | -20% | +16% / -17% | +1.8 (5.7) / -1.7 (1.7) | n / n | x1.54 / x0.72 | ONE-WINDOW | 110 / 108 / 342 / 1651 |
| [er-scaled R, NOT live] floor 6R / arm 3R keep 0.5 / caps +5R -2R | +31% | +20% | +11% | -22% | -19% | +16% / -10% | +1.3 (5.6) / -1.9 (1.6) | n / n | x1.52 / x0.71 | ONE-WINDOW | 110 / 195 / 342 / 1651 |
| [er-scaled R, NOT live] floor 6R / arm 3R keep 0.75 / caps +5R -2R | +31% | +25% | +17% | -20% | -18% | +17% / -1% | -0.2 (7.7) / -2.8 (2.2) | n / n | x1.44 / x0.65 | ONE-WINDOW | 111 / 419 / 342 / 1652 |
| [er-scaled R, NOT live] floor 8R / no give-back / caps +5R -2R | +20% | +2% | -5% | -14% | -6% | +5% / -16% | +2.1 (6.2) / -1.0 (1.5) | n / n | x1.35 / x0.81 | ONE-WINDOW | 59 / 0 / 342 / 1650 |
| [er-scaled R, NOT live] floor 8R / arm 1.5R keep 0.25 / caps +5R -2R | +20% | +13% | +16% | -17% | -30% | -14% / -12% | -2.5 (7.4) / -2.7 (3.0) | n / n | x1.13 / x0.68 | ONE-WINDOW | 51 / 708 / 342 / 1650 |
| [er-scaled R, NOT live] floor 8R / arm 1.5R keep 0.5 / caps +5R -2R | -6% | +5% | +26% | -8% | -12% | -10% / -5% | -3.6 (8.5) / -3.4 (3.5) | n / n | x0.82 / x0.69 | DEAD | 47 / 1076 / 342 / 1653 |
| [er-scaled R, NOT live] floor 8R / arm 1.5R keep 0.75 / caps +5R -2R | +28% | +31% | +33% | -19% | +1% | -3% / -22% | -5.8 (11.6) / -5.5 (4.4) | n / n | x1.10 / x0.49 | ONE-WINDOW | 43 / 1573 / 342 / 1654 |
| [er-scaled R, NOT live] floor 8R / arm 2R keep 0.25 / caps +5R -2R | +25% | +8% | +2% | -18% | -17% | -2% / -18% | -0.3 (6.6) / -0.9 (1.5) | n / n | x1.31 / x0.79 | ONE-WINDOW | 58 / 350 / 342 / 1650 |
| [er-scaled R, NOT live] floor 8R / arm 2R keep 0.5 / caps +5R -2R | +7% | +4% | +4% | -8% | -7% | -3% / -11% | -3.3 (5.7) / -0.5 (1.4) | n / n | x0.95 / x0.89 | ONE-WINDOW | 53 / 590 / 342 / 1653 |
| [er-scaled R, NOT live] floor 8R / arm 2R keep 0.75 / caps +5R -2R | +21% | +12% | +7% | -2% | +6% | +1% / -0% | -2.8 (7.4) / -2.1 (2.9) | n / n | x1.14 / x0.82 | ONE-WINDOW | 51 / 1000 / 342 / 1654 |
| [er-scaled R, NOT live] floor 8R / arm 3R keep 0.25 / caps +5R -2R | +21% | +3% | -5% | -16% | -13% | +5% / -19% | +2.0 (6.3) / -1.4 (1.5) | n / n | x1.36 / x0.78 | ONE-WINDOW | 60 / 108 / 342 / 1650 |
| [er-scaled R, NOT live] floor 8R / arm 3R keep 0.5 / caps +5R -2R | +22% | +4% | -4% | -14% | -12% | +6% / -12% | +1.5 (5.9) / -1.5 (1.4) | n / n | x1.35 / x0.78 | ONE-WINDOW | 58 / 195 / 342 / 1650 |
| [er-scaled R, NOT live] floor 8R / arm 3R keep 0.75 / caps +5R -2R | +21% | +8% | +2% | -13% | -11% | +7% / -1% | -0.0 (7.5) / -2.5 (2.1) | n / n | x1.27 / x0.72 | ONE-WINDOW | 58 / 419 / 342 / 1651 |
| [er-scaled R, NOT live] floor 10R / no give-back / caps +5R -2R | +21% | -2% | -9% | -12% | -6% | +2% / -15% | +2.2 (6.4) / -0.9 (1.4) | n / n | x1.37 / x0.83 | ONE-WINDOW | 30 / 0 / 342 / 1650 |
| [er-scaled R, NOT live] floor 10R / arm 1.5R keep 0.25 / caps +5R -2R | +19% | +14% | +17% | -15% | -30% | -16% / -10% | -2.6 (7.4) / -2.4 (3.0) | n / n | x1.11 / x0.72 | ONE-WINDOW | 25 / 708 / 342 / 1650 |
| [er-scaled R, NOT live] floor 10R / arm 1.5R keep 0.5 / caps +5R -2R | -8% | +4% | +26% | -5% | -12% | -14% / -0% | -3.8 (8.4) / -3.3 (3.5) | n / n | x0.80 / x0.71 | DEAD | 22 / 1076 / 342 / 1653 |
| [er-scaled R, NOT live] floor 10R / arm 1.5R keep 0.75 / caps +5R -2R | +27% | +31% | +32% | -17% | +1% | -7% / -22% | -5.9 (11.5) / -5.4 (4.4) | n / n | x1.08 / x0.51 | ONE-WINDOW | 22 / 1573 / 342 / 1654 |
| [er-scaled R, NOT live] floor 10R / arm 2R keep 0.25 / caps +5R -2R | +27% | +4% | -2% | -15% | -18% | -6% / -16% | -0.4 (6.6) / -0.7 (1.4) | n / Y | x1.34 / x0.82 | ONE-WINDOW | 27 / 350 / 342 / 1650 |
| [er-scaled R, NOT live] floor 10R / arm 2R keep 0.5 / caps +5R -2R | +9% | +5% | -1% | -6% | -8% | -5% / -5% | -3.4 (5.6) / -0.4 (1.4) | n / n | x0.96 / x0.91 | ONE-WINDOW | 25 / 589 / 342 / 1653 |
| [er-scaled R, NOT live] floor 10R / arm 2R keep 0.75 / caps +5R -2R | +24% | +8% | +2% | -1% | +5% | -1% / +4% | -2.8 (7.2) / -2.1 (2.9) | n / n | x1.18 / x0.84 | ONE-WINDOW | 24 / 999 / 342 / 1654 |
| [er-scaled R, NOT live] floor 10R / arm 3R keep 0.25 / caps +5R -2R | +22% | -1% | -8% | -13% | -13% | +2% / -18% | +2.0 (6.5) / -1.1 (1.4) | n / n | x1.38 / x0.81 | ONE-WINDOW | 29 / 108 / 342 / 1650 |
| [er-scaled R, NOT live] floor 10R / arm 3R keep 0.5 / caps +5R -2R | +23% | -0% | -8% | -12% | -12% | +2% / -11% | +1.5 (6.2) / -1.4 (1.4) | n / n | x1.36 / x0.80 | ONE-WINDOW | 29 / 194 / 342 / 1650 |
| [er-scaled R, NOT live] floor 10R / arm 3R keep 0.75 / caps +5R -2R | +22% | +4% | -2% | -11% | -12% | +5% / +2% | -0.0 (7.7) / -2.4 (2.1) | n / n | x1.28 / x0.74 | MIXED | 29 / 418 / 342 / 1651 |
| [er-scaled R, NOT live] floor 12R / no give-back / caps +5R -2R | +21% | -0% | -3% | -10% | -3% | +4% / -16% | +2.3 (6.2) / -0.8 (1.4) | n / n | x1.37 / x0.85 | ONE-WINDOW | 15 / 0 / 342 / 1650 |
| [er-scaled R, NOT live] floor 12R / arm 1.5R keep 0.25 / caps +5R -2R | +17% | +14% | +18% | -15% | -26% | -19% / -9% | -2.6 (7.3) / -2.3 (3.0) | n / n | x1.09 / x0.72 | ONE-WINDOW | 11 / 708 / 342 / 1650 |
| [er-scaled R, NOT live] floor 12R / arm 1.5R keep 0.5 / caps +5R -2R | -9% | +3% | +28% | -5% | -7% | -15% / +0% | -3.8 (8.4) / -3.2 (3.5) | n / n | x0.79 / x0.72 | DEAD | 12 / 1077 / 342 / 1653 |
| [er-scaled R, NOT live] floor 12R / arm 1.5R keep 0.75 / caps +5R -2R | +24% | +30% | +35% | -16% | +6% | -8% / -24% | -6.0 (11.5) / -5.3 (4.4) | n / n | x1.02 / x0.52 | ONE-WINDOW | 11 / 1573 / 342 / 1654 |
| [er-scaled R, NOT live] floor 12R / arm 2R keep 0.25 / caps +5R -2R | +25% | +6% | +5% | -13% | -14% | -7% / -14% | -0.4 (6.5) / -0.6 (1.4) | n / Y | x1.31 / x0.84 | ONE-WINDOW | 13 / 350 / 342 / 1650 |
| [er-scaled R, NOT live] floor 12R / arm 2R keep 0.5 / caps +5R -2R | +7% | +6% | +6% | -4% | -3% | -7% / -4% | -3.3 (5.5) / -0.3 (1.4) | n / n | x0.95 / x0.93 | ONE-WINDOW | 13 / 589 / 342 / 1653 |
| [er-scaled R, NOT live] floor 12R / arm 2R keep 0.75 / caps +5R -2R | +20% | +10% | +9% | +1% | +11% | -4% / +4% | -2.9 (7.1) / -2.0 (2.9) | n / n | x1.12 / x0.86 | ONE-WINDOW | 12 / 999 / 342 / 1654 |
| [er-scaled R, NOT live] floor 12R / arm 3R keep 0.25 / caps +5R -2R | +22% | +1% | -3% | -11% | -10% | +3% / -19% | +2.1 (6.3) / -1.0 (1.4) | n / n | x1.38 / x0.83 | ONE-WINDOW | 13 / 108 / 342 / 1650 |
| [er-scaled R, NOT live] floor 12R / arm 3R keep 0.5 / caps +5R -2R | +22% | +1% | -2% | -9% | -9% | +5% / -12% | +1.6 (5.9) / -1.3 (1.3) | n / n | x1.37 / x0.83 | ONE-WINDOW | 13 / 194 / 342 / 1650 |
| [er-scaled R, NOT live] floor 12R / arm 3R keep 0.75 / caps +5R -2R | +19% | +6% | +5% | -9% | -8% | +8% / +2% | +0.0 (7.5) / -2.3 (2.1) | n / n | x1.24 / x0.76 | MIXED | 12 / 418 / 342 / 1651 |
| [er-scaled R, NOT live] floor 16R / no give-back / caps +5R -2R | +21% | -1% | -3% | -5% | -3% | +5% / -16% | +2.2 (6.2) / -0.7 (1.4) | n / n | x1.37 / x0.90 | ONE-WINDOW | 4 / 0 / 342 / 1650 |
| [er-scaled R, NOT live] floor 16R / arm 1.5R keep 0.25 / caps +5R -2R | +16% | +13% | +17% | -10% | -26% | -20% / -9% | -2.8 (7.3) / -2.2 (3.0) | n / n | x1.07 / x0.76 | ONE-WINDOW | 2 / 708 / 342 / 1650 |
| [er-scaled R, NOT live] floor 16R / arm 1.5R keep 0.5 / caps +5R -2R | -12% | +1% | +28% | -1% | -8% | -15% / +0% | -4.0 (8.3) / -3.2 (3.5) | n / n | x0.77 / x0.76 | DEAD | 2 / 1077 / 342 / 1653 |
| [er-scaled R, NOT live] floor 16R / arm 1.5R keep 0.75 / caps +5R -2R | +25% | +30% | +34% | -11% | +6% | -8% / -23% | -6.1 (11.5) / -5.3 (4.4) | n / n | x1.03 / x0.54 | ONE-WINDOW | 2 / 1573 / 342 / 1654 |
| [er-scaled R, NOT live] floor 16R / arm 2R keep 0.25 / caps +5R -2R | +24% | +5% | +4% | -9% | -14% | -8% / -15% | -0.5 (6.4) / -0.5 (1.4) | n / Y | x1.29 / x0.89 | ONE-WINDOW | 3 / 350 / 342 / 1650 |
| [er-scaled R, NOT live] floor 16R / arm 2R keep 0.5 / caps +5R -2R | +6% | +6% | +5% | +1% | -3% | -7% / -5% | -3.5 (5.3) / -0.3 (1.4) | n / n | x0.93 / x0.99 | ONE-WINDOW | 3 / 589 / 342 / 1653 |
| [er-scaled R, NOT live] floor 16R / arm 2R keep 0.75 / caps +5R -2R | +20% | +10% | +8% | +6% | +11% | -4% / +4% | -3.0 (7.1) / -1.9 (2.9) | n / n | x1.12 / x0.91 | ONE-WINDOW | 3 / 999 / 342 / 1654 |
| [er-scaled R, NOT live] floor 16R / arm 3R keep 0.25 / caps +5R -2R | +23% | +0% | -3% | -6% | -10% | +5% / -20% | +2.0 (6.4) / -0.9 (1.4) | n / n | x1.38 / x0.88 | ONE-WINDOW | 4 / 108 / 342 / 1650 |
| [er-scaled R, NOT live] floor 16R / arm 3R keep 0.5 / caps +5R -2R | +23% | +1% | -2% | -5% | -9% | +6% / -12% | +1.5 (5.9) / -1.2 (1.3) | n / n | x1.37 / x0.87 | ONE-WINDOW | 4 / 194 / 342 / 1650 |
| [er-scaled R, NOT live] floor 16R / arm 3R keep 0.75 / caps +5R -2R | +20% | +5% | +4% | -4% | -8% | +8% / +2% | -0.1 (7.5) / -2.2 (2.1) | n / n | x1.25 / x0.80 | MIXED | 4 / 418 / 342 / 1651 |
| [er-scaled R, NOT live] no floor / no give-back / caps +5R -2R | +21% | -1% | -3% | -5% | -4% | +5% / -16% | +2.2 (6.2) / -0.7 (1.4) | n / n | x1.37 / x0.90 | ONE-WINDOW | 0 / 0 / 342 / 1650 |
| [er-scaled R, NOT live] no floor / arm 1.5R keep 0.25 / caps +5R -2R | +15% | +13% | +17% | -9% | -26% | -20% / -9% | -2.8 (7.3) / -2.2 (3.0) | n / n | x1.06 / x0.77 | ONE-WINDOW | 0 / 708 / 342 / 1650 |
| [er-scaled R, NOT live] no floor / arm 1.5R keep 0.5 / caps +5R -2R | -12% | +1% | +28% | +0% | -8% | -15% / +0% | -4.0 (8.3) / -3.1 (3.5) | n / n | x0.76 / x0.77 | ONE-WINDOW | 0 / 1077 / 342 / 1653 |
| [er-scaled R, NOT live] no floor / arm 1.5R keep 0.75 / caps +5R -2R | +25% | +30% | +34% | -10% | +5% | -8% / -22% | -6.1 (11.5) / -5.2 (4.4) | n / n | x1.03 / x0.55 | ONE-WINDOW | 0 / 1573 / 342 / 1654 |
| [er-scaled R, NOT live] no floor / arm 2R keep 0.25 / caps +5R -2R | +24% | +5% | +4% | -8% | -15% | -8% / -15% | -0.5 (6.4) / -0.5 (1.4) | n / Y | x1.29 / x0.89 | ONE-WINDOW | 0 / 350 / 342 / 1650 |
| [er-scaled R, NOT live] no floor / arm 2R keep 0.5 / caps +5R -2R | +6% | +6% | +5% | +1% | -4% | -7% / -5% | -3.5 (5.3) / -0.2 (1.4) | n / n | x0.93 / x0.99 | ONE-WINDOW | 0 / 589 / 342 / 1653 |
| [er-scaled R, NOT live] no floor / arm 2R keep 0.75 / caps +5R -2R | +20% | +10% | +8% | +6% | +10% | -4% / +4% | -3.0 (7.1) / -1.9 (2.9) | n / n | x1.12 / x0.91 | ONE-WINDOW | 0 / 999 / 342 / 1654 |
| [er-scaled R, NOT live] no floor / arm 3R keep 0.25 / caps +5R -2R | +22% | +0% | -3% | -6% | -11% | +5% / -20% | +2.0 (6.4) / -0.9 (1.4) | n / n | x1.38 / x0.88 | ONE-WINDOW | 0 / 108 / 342 / 1650 |
| [er-scaled R, NOT live] no floor / arm 3R keep 0.5 / caps +5R -2R | +23% | +1% | -2% | -4% | -10% | +6% / -12% | +1.5 (5.9) / -1.2 (1.3) | n / n | x1.37 / x0.87 | ONE-WINDOW | 0 / 194 / 342 / 1650 |
| [er-scaled R, NOT live] no floor / arm 3R keep 0.75 / caps +5R -2R | +20% | +5% | +4% | -4% | -9% | +8% / +2% | -0.1 (7.5) / -2.2 (2.1) | n / n | x1.25 / x0.81 | MIXED | 0 / 418 / 342 / 1651 |

### 3. Lock R scaled proportionally, multiplier = actual traded lots / session-table lots (NOT live): full floor x give-back surface (cuts vs the LIVE cell)
| cell | PA9 cut L6M | HOLD | MID | PRE | X' | dropped L6M / PRE | mean d L6M / PRE $k (MDE) | strict / tol | Calmar vs live L6M / PRE | label | weeks floor fired / give-back days / +cap skips / -cap skips |
|---|---|---|---|---|---|---|---|---|---|---|---|
| [act-scaled R, NOT live] floor 6R / no give-back / caps +5R -2R | +18% | +11% | +3% | -25% | -20% | +9% / -17% | +1.2 (5.5) / -2.1 (2.3) | n / n | x1.27 / x0.68 | ONE-WINDOW | 92 / 0 / 321 / 1418 |
| [act-scaled R, NOT live] floor 6R / arm 1.5R keep 0.25 / caps +5R -2R | +12% | +11% | +13% | -25% | -59% | -8% / -19% | -2.8 (7.9) / -3.7 (3.8) | n / n | x1.02 / x0.58 | ONE-WINDOW | 88 / 558 / 321 / 1418 |
| [act-scaled R, NOT live] floor 6R / arm 1.5R keep 0.5 / caps +5R -2R | -18% | -5% | +16% | -10% | -39% | -7% / -12% | -4.3 (9.1) / -4.2 (3.9) | n / n | x0.71 / x0.62 | DEAD | 87 / 890 / 321 / 1421 |
| [act-scaled R, NOT live] floor 6R / arm 1.5R keep 0.75 / caps +5R -2R | -0% | +7% | +17% | -26% | -27% | +0% / -23% | -7.6 (11.7) / -5.9 (4.9) | n / n | x0.72 / x0.44 | DEAD | 81 / 1368 / 321 / 1422 |
| [act-scaled R, NOT live] floor 6R / arm 2R keep 0.25 / caps +5R -2R | +22% | +15% | +9% | -28% | -37% | +4% / -23% | +0.2 (6.2) / -1.9 (2.7) | n / n | x1.29 / x0.67 | ONE-WINDOW | 89 / 276 / 321 / 1418 |
| [act-scaled R, NOT live] floor 6R / arm 2R keep 0.5 / caps +5R -2R | +1% | +4% | +11% | -16% | -31% | +3% / -8% | -3.4 (5.3) / -1.5 (2.1) | n / n | x0.89 / x0.77 | ONE-WINDOW | 89 / 483 / 321 / 1421 |
| [act-scaled R, NOT live] floor 6R / arm 2R keep 0.75 / caps +5R -2R | +18% | +17% | +15% | -10% | -19% | +2% / -2% | -3.2 (7.2) / -3.0 (3.3) | n / n | x1.08 / x0.71 | ONE-WINDOW | 86 / 883 / 321 / 1422 |
| [act-scaled R, NOT live] floor 6R / arm 3R keep 0.25 / caps +5R -2R | +18% | +11% | +4% | -25% | -25% | +9% / -19% | +1.3 (5.6) / -2.2 (2.4) | n / n | x1.27 / x0.67 | ONE-WINDOW | 90 / 84 / 321 / 1418 |
| [act-scaled R, NOT live] floor 6R / arm 3R keep 0.5 / caps +5R -2R | +18% | +13% | +5% | -24% | -25% | +9% / -20% | +0.6 (5.3) / -2.4 (2.6) | n / n | x1.25 / x0.66 | ONE-WINDOW | 90 / 148 / 321 / 1418 |
| [act-scaled R, NOT live] floor 6R / arm 3R keep 0.75 / caps +5R -2R | +19% | +17% | +12% | -24% | -26% | +10% / -17% | -0.7 (7.3) / -3.3 (2.9) | n / n | x1.20 / x0.61 | ONE-WINDOW | 90 / 325 / 321 / 1419 |
| [act-scaled R, NOT live] floor 8R / no give-back / caps +5R -2R | +13% | +3% | -4% | -21% | -14% | +1% / -14% | +1.4 (5.6) / -1.7 (1.7) | n / n | x1.21 / x0.72 | ONE-WINDOW | 39 / 0 / 321 / 1417 |
| [act-scaled R, NOT live] floor 8R / arm 1.5R keep 0.25 / caps +5R -2R | +6% | +4% | +3% | -24% | -50% | -17% / -15% | -2.9 (7.6) / -3.4 (3.4) | n / n | x0.95 / x0.60 | ONE-WINDOW | 30 / 558 / 321 / 1417 |
| [act-scaled R, NOT live] floor 8R / arm 1.5R keep 0.5 / caps +5R -2R | -23% | -9% | +8% | -7% | -33% | -15% / -6% | -4.2 (8.8) / -3.9 (3.5) | n / n | x0.69 / x0.66 | DEAD | 27 / 890 / 321 / 1420 |
| [act-scaled R, NOT live] floor 8R / arm 1.5R keep 0.75 / caps +5R -2R | -3% | +4% | +9% | -16% | -19% | -9% / -22% | -7.5 (11.4) / -5.5 (4.6) | n / n | x0.70 / x0.51 | DEAD | 27 / 1368 / 321 / 1421 |
| [act-scaled R, NOT live] floor 8R / arm 2R keep 0.25 / caps +5R -2R | +16% | +8% | +1% | -24% | -28% | -5% / -14% | +0.3 (6.3) / -1.6 (2.1) | n / n | x1.21 / x0.71 | ONE-WINDOW | 37 / 276 / 321 / 1417 |
| [act-scaled R, NOT live] floor 8R / arm 2R keep 0.5 / caps +5R -2R | -2% | -2% | +4% | -14% | -21% | -7% / -7% | -3.1 (5.1) / -1.2 (1.4) | n / n | x0.87 / x0.80 | DEAD | 35 / 483 / 321 / 1420 |
| [act-scaled R, NOT live] floor 8R / arm 2R keep 0.75 / caps +5R -2R | +12% | +8% | +3% | -7% | -8% | -7% / +1% | -2.9 (7.1) / -2.7 (3.0) | n / n | x1.01 / x0.75 | ONE-WINDOW | 34 / 883 / 321 / 1421 |
| [act-scaled R, NOT live] floor 8R / arm 3R keep 0.25 / caps +5R -2R | +14% | +3% | -4% | -22% | -18% | +1% / -15% | +1.5 (5.8) / -1.9 (1.9) | n / n | x1.22 / x0.70 | ONE-WINDOW | 39 / 84 / 321 / 1417 |
| [act-scaled R, NOT live] floor 8R / arm 3R keep 0.5 / caps +5R -2R | +14% | +5% | -2% | -21% | -17% | +1% / -11% | +0.9 (5.4) / -2.2 (2.1) | n / n | x1.20 / x0.69 | ONE-WINDOW | 39 / 148 / 321 / 1417 |
| [act-scaled R, NOT live] floor 8R / arm 3R keep 0.75 / caps +5R -2R | +14% | +8% | +4% | -22% | -18% | +3% / -6% | -0.5 (7.2) / -3.1 (2.5) | n / n | x1.15 / x0.62 | ONE-WINDOW | 39 / 325 / 321 / 1418 |
| [act-scaled R, NOT live] floor 10R / no give-back / caps +5R -2R | +16% | -3% | -8% | -14% | -9% | -2% / -10% | +1.5 (6.0) / -1.4 (1.3) | n / n | x1.26 / x0.79 | ONE-WINDOW | 8 / 0 / 321 / 1417 |
| [act-scaled R, NOT live] floor 10R / arm 1.5R keep 0.25 / caps +5R -2R | +6% | +2% | +2% | -17% | -47% | -20% / -13% | -3.0 (7.4) / -3.0 (3.5) | n / n | x0.95 / x0.66 | ONE-WINDOW | 6 / 558 / 321 / 1417 |
| [act-scaled R, NOT live] floor 10R / arm 1.5R keep 0.5 / caps +5R -2R | -23% | -10% | +7% | -4% | -28% | -17% / +1% | -4.3 (8.5) / -3.4 (3.5) | n / n | x0.68 / x0.71 | DEAD | 4 / 890 / 321 / 1420 |
| [act-scaled R, NOT live] floor 10R / arm 1.5R keep 0.75 / caps +5R -2R | -3% | +6% | +8% | -12% | -13% | -12% / -19% | -7.6 (11.2) / -5.2 (4.6) | n / n | x0.70 / x0.55 | DEAD | 4 / 1368 / 321 / 1421 |
| [act-scaled R, NOT live] floor 10R / arm 2R keep 0.25 / caps +5R -2R | +19% | +0% | -2% | -18% | -23% | -9% / -10% | +0.2 (6.6) / -1.3 (2.2) | n / n | x1.24 / x0.77 | ONE-WINDOW | 7 / 276 / 321 / 1417 |
| [act-scaled R, NOT live] floor 10R / arm 2R keep 0.5 / caps +5R -2R | -4% | -2% | -0% | -7% | -15% | -10% / -2% | -3.3 (4.6) / -0.9 (1.4) | n / n | x0.85 / x0.87 | DEAD | 6 / 483 / 321 / 1420 |
| [act-scaled R, NOT live] floor 10R / arm 2R keep 0.75 / caps +5R -2R | +12% | +6% | +0% | -1% | -2% | -9% / +5% | -3.1 (6.8) / -2.3 (3.0) | n / n | x1.01 / x0.82 | ONE-WINDOW | 6 / 883 / 321 / 1421 |
| [act-scaled R, NOT live] floor 10R / arm 3R keep 0.25 / caps +5R -2R | +16% | -3% | -8% | -14% | -13% | -2% / -13% | +1.5 (6.2) / -1.5 (1.3) | n / n | x1.26 / x0.78 | ONE-WINDOW | 8 / 84 / 321 / 1417 |
| [act-scaled R, NOT live] floor 10R / arm 3R keep 0.5 / caps +5R -2R | +17% | -1% | -8% | -14% | -13% | -2% / -9% | +0.8 (5.9) / -1.7 (1.3) | n / n | x1.24 / x0.76 | ONE-WINDOW | 8 / 148 / 321 / 1417 |
| [act-scaled R, NOT live] floor 10R / arm 3R keep 0.75 / caps +5R -2R | +17% | +4% | -1% | -14% | -14% | -1% / -5% | -0.5 (7.5) / -2.8 (2.2) | n / n | x1.18 / x0.70 | ONE-WINDOW | 8 / 325 / 321 / 1418 |
| [act-scaled R, NOT live] floor 12R / no give-back / caps +5R -2R | +17% | -2% | -6% | -15% | -8% | -5% / -12% | +1.6 (6.0) / -1.3 (1.3) | n / n | x1.27 / x0.79 | ONE-WINDOW | 2 / 0 / 321 / 1417 |
| [act-scaled R, NOT live] floor 12R / arm 1.5R keep 0.25 / caps +5R -2R | +7% | +2% | +2% | -18% | -45% | -25% / -14% | -3.1 (7.1) / -2.9 (3.5) | n / n | x0.96 / x0.66 | ONE-WINDOW | 2 / 558 / 321 / 1417 |
| [act-scaled R, NOT live] floor 12R / arm 1.5R keep 0.5 / caps +5R -2R | -23% | -9% | +7% | -6% | -27% | -21% / -1% | -4.4 (8.5) / -3.4 (3.5) | n / n | x0.69 / x0.70 | DEAD | 1 / 890 / 321 / 1420 |
| [act-scaled R, NOT live] floor 12R / arm 1.5R keep 0.75 / caps +5R -2R | -2% | +7% | +8% | -14% | -12% | -14% / -21% | -7.6 (11.1) / -5.2 (4.6) | n / n | x0.71 / x0.54 | DEAD | 1 / 1368 / 321 / 1421 |
| [act-scaled R, NOT live] floor 12R / arm 2R keep 0.25 / caps +5R -2R | +18% | +2% | +0% | -18% | -23% | -13% / -12% | +0.2 (6.6) / -1.2 (2.2) | n / n | x1.23 / x0.78 | ONE-WINDOW | 2 / 276 / 321 / 1417 |
| [act-scaled R, NOT live] floor 12R / arm 2R keep 0.5 / caps +5R -2R | -3% | -0% | +2% | -9% | -14% | -13% / -3% | -3.3 (4.7) / -0.8 (1.3) | n / n | x0.86 / x0.86 | DEAD | 1 / 483 / 321 / 1420 |
| [act-scaled R, NOT live] floor 12R / arm 2R keep 0.75 / caps +5R -2R | +11% | +8% | +2% | -2% | -1% | -11% / +3% | -3.1 (6.9) / -2.3 (2.9) | n / n | x1.00 / x0.81 | ONE-WINDOW | 1 / 883 / 321 / 1421 |
| [act-scaled R, NOT live] floor 12R / arm 3R keep 0.25 / caps +5R -2R | +17% | -1% | -6% | -15% | -12% | -5% / -15% | +1.5 (6.2) / -1.4 (1.3) | n / n | x1.27 / x0.77 | ONE-WINDOW | 1 / 84 / 321 / 1417 |
| [act-scaled R, NOT live] floor 12R / arm 3R keep 0.5 / caps +5R -2R | +17% | +0% | -5% | -15% | -12% | -4% / -11% | +0.9 (5.9) / -1.7 (1.2) | n / n | x1.25 / x0.76 | ONE-WINDOW | 1 / 148 / 321 / 1417 |
| [act-scaled R, NOT live] floor 12R / arm 3R keep 0.75 / caps +5R -2R | +17% | +5% | +1% | -15% | -13% | -2% / -6% | -0.5 (7.6) / -2.7 (2.1) | n / n | x1.18 / x0.70 | ONE-WINDOW | 1 / 325 / 321 / 1418 |
| [act-scaled R, NOT live] floor 16R / no give-back / caps +5R -2R | +15% | -4% | -10% | -6% | -8% | -3% / -12% | +1.6 (5.9) / -0.9 (1.3) | n / n | x1.25 / x0.88 | ONE-WINDOW | 0 / 0 / 321 / 1417 |
| [act-scaled R, NOT live] floor 16R / arm 1.5R keep 0.25 / caps +5R -2R | +7% | +3% | +2% | -10% | -45% | -27% / -14% | -3.1 (7.1) / -2.5 (3.1) | n / n | x0.96 / x0.73 | ONE-WINDOW | 0 / 558 / 321 / 1417 |
| [act-scaled R, NOT live] floor 16R / arm 1.5R keep 0.5 / caps +5R -2R | -21% | -8% | +9% | +1% | -27% | -23% / -1% | -4.3 (8.5) / -3.3 (3.5) | n / n | x0.69 / x0.75 | ONE-WINDOW | 0 / 890 / 321 / 1420 |
| [act-scaled R, NOT live] floor 16R / arm 1.5R keep 0.75 / caps +5R -2R | +1% | +9% | +12% | -7% | -12% | -16% / -21% | -7.5 (11.2) / -5.1 (4.6) | n / n | x0.73 / x0.58 | ONE-WINDOW | 0 / 1368 / 321 / 1421 |
| [act-scaled R, NOT live] floor 16R / arm 2R keep 0.25 / caps +5R -2R | +17% | -0% | -3% | -9% | -23% | -14% / -12% | +0.1 (6.6) / -0.7 (1.3) | n / n | x1.22 / x0.87 | ONE-WINDOW | 0 / 276 / 321 / 1417 |
| [act-scaled R, NOT live] floor 16R / arm 2R keep 0.5 / caps +5R -2R | -2% | +1% | -2% | +0% | -14% | -14% / -3% | -3.3 (4.7) / -0.6 (1.3) | n / n | x0.86 / x0.95 | ONE-WINDOW | 0 / 483 / 321 / 1420 |
| [act-scaled R, NOT live] floor 16R / arm 2R keep 0.75 / caps +5R -2R | +13% | +6% | -1% | +7% | -1% | -12% / +3% | -3.0 (6.9) / -2.1 (2.9) | n / n | x1.02 / x0.90 | ONE-WINDOW | 0 / 883 / 321 / 1421 |
| [act-scaled R, NOT live] floor 16R / arm 3R keep 0.25 / caps +5R -2R | +16% | -3% | -9% | -6% | -12% | -3% / -15% | +1.6 (6.1) / -1.0 (1.3) | n / n | x1.25 / x0.87 | ONE-WINDOW | 0 / 84 / 321 / 1417 |
| [act-scaled R, NOT live] floor 16R / arm 3R keep 0.5 / caps +5R -2R | +16% | -1% | -8% | -6% | -12% | -2% / -11% | +0.9 (5.8) / -1.3 (1.2) | n / n | x1.23 / x0.85 | ONE-WINDOW | 0 / 148 / 321 / 1417 |
| [act-scaled R, NOT live] floor 16R / arm 3R keep 0.75 / caps +5R -2R | +16% | +4% | -2% | -5% | -13% | +1% / -6% | -0.4 (7.5) / -2.4 (2.1) | n / n | x1.17 / x0.78 | ONE-WINDOW | 0 / 325 / 321 / 1418 |
| [act-scaled R, NOT live] no floor / no give-back / caps +5R -2R | +17% | -4% | -10% | -6% | -8% | -2% / -12% | +1.7 (5.9) / -0.9 (1.3) | n / n | x1.28 / x0.88 | ONE-WINDOW | 0 / 0 / 321 / 1417 |
| [act-scaled R, NOT live] no floor / arm 1.5R keep 0.25 / caps +5R -2R | +8% | +3% | +2% | -10% | -45% | -27% / -14% | -3.1 (7.1) / -2.5 (3.1) | n / n | x0.97 / x0.73 | ONE-WINDOW | 0 / 558 / 321 / 1417 |
| [act-scaled R, NOT live] no floor / arm 1.5R keep 0.5 / caps +5R -2R | -19% | -6% | +9% | +1% | -27% | -23% / -1% | -4.3 (8.5) / -3.3 (3.5) | n / n | x0.71 / x0.75 | ONE-WINDOW | 0 / 890 / 321 / 1420 |
| [act-scaled R, NOT live] no floor / arm 1.5R keep 0.75 / caps +5R -2R | +4% | +11% | +12% | -7% | -12% | -16% / -21% | -7.4 (11.2) / -5.1 (4.6) | n / n | x0.76 / x0.58 | ONE-WINDOW | 0 / 1368 / 321 / 1421 |
| [act-scaled R, NOT live] no floor / arm 2R keep 0.25 / caps +5R -2R | +18% | -0% | -3% | -9% | -23% | -14% / -12% | +0.2 (6.6) / -0.7 (1.3) | n / n | x1.23 / x0.87 | ONE-WINDOW | 0 / 276 / 321 / 1417 |
| [act-scaled R, NOT live] no floor / arm 2R keep 0.5 / caps +5R -2R | -0% | +2% | -2% | +0% | -14% | -14% / -3% | -3.2 (4.7) / -0.6 (1.3) | n / n | x0.88 / x0.95 | ONE-WINDOW | 0 / 483 / 321 / 1420 |
| [act-scaled R, NOT live] no floor / arm 2R keep 0.75 / caps +5R -2R | +16% | +6% | -1% | +7% | -1% | -12% / +3% | -2.9 (6.9) / -2.1 (2.9) | n / n | x1.06 / x0.90 | ONE-WINDOW | 0 / 883 / 321 / 1421 |
| [act-scaled R, NOT live] no floor / arm 3R keep 0.25 / caps +5R -2R | +17% | -3% | -9% | -6% | -12% | -2% / -15% | +1.6 (6.1) / -1.0 (1.3) | n / n | x1.28 / x0.87 | ONE-WINDOW | 0 / 84 / 321 / 1417 |
| [act-scaled R, NOT live] no floor / arm 3R keep 0.5 / caps +5R -2R | +18% | -1% | -8% | -6% | -12% | -1% / -11% | +1.0 (5.8) / -1.3 (1.2) | n / n | x1.26 / x0.85 | ONE-WINDOW | 0 / 148 / 321 / 1417 |
| [act-scaled R, NOT live] no floor / arm 3R keep 0.75 / caps +5R -2R | +18% | +4% | -2% | -5% | -13% | +2% / -6% | -0.3 (7.5) / -2.4 (2.1) | n / n | x1.20 / x0.78 | ONE-WINDOW | 0 / 325 / 321 / 1418 |

### 4. Screen (cut > 0 on L6M and PRE, raw and with the carrying episodes dropped)
15 of 229 cells pass raw+dropped; with STRICT mean: none; with TOLERANT mean: none.

| cell | PA9 cut L6M | HOLD | MID | PRE | X' | dropped L6M / PRE | mean d L6M / PRE $k (MDE) | strict / tol | Calmar vs live L6M / PRE | label | weeks floor fired / give-back days / +cap skips / -cap skips |
|---|---|---|---|---|---|---|---|---|---|---|---|
| floor $4k / arm 3R keep 0.5 / caps +5R -2R | +34% | +36% | +33% | +20% | +4% | +67% / +39% | -14.4 (17.8) / -7.5 (6.8) | n / n | x0.71 / x0.55 | RISK-KEEP | 472 / 17 / 62 / 432 |
| floor $4k / arm 3R keep 0.75 / caps +5R -2R | +34% | +36% | +33% | +18% | +4% | +67% / +39% | -15.2 (18.2) / -7.9 (6.8) | n / n | x0.68 / x0.49 | RISK-KEEP | 473 / 72 / 62 / 432 |
| floor $4k / arm 2R keep 0.25 / caps +5R -2R | +34% | +36% | +33% | +32% | +4% | +67% / +38% | -14.9 (17.5) / -7.1 (6.7) | n / n | x0.70 / x0.69 | RISK-KEEP | 469 / 44 / 62 / 432 |
| floor $4k / no give-back / caps +5R -2R | +34% | +36% | +34% | +23% | +4% | +66% / +39% | -14.8 (17.5) / -7.4 (6.8) | n / n | x0.69 / x0.58 | RISK-KEEP | 472 / 0 / 62 / 432 |
| floor $4k / arm 3R keep 0.25 / caps +5R -2R | +34% | +36% | +34% | +23% | +4% | +66% / +39% | -14.8 (17.5) / -7.4 (6.8) | n / n | x0.69 / x0.58 | RISK-KEEP | 472 / 2 / 62 / 432 |
| floor $4k / arm 2R keep 0.5 / caps +5R -2R | +27% | +31% | +32% | +38% | +4% | +65% / +38% | -15.5 (18.3) / -7.0 (6.7) | n / n | x0.60 / x0.77 | RISK-KEEP | 471 / 139 / 62 / 432 |
| floor $4k / arm 2R keep 0.75 / caps +5R -2R | +34% | +33% | +31% | +34% | +6% | +64% / +35% | -16.4 (18.6) / -8.1 (7.0) | n / n | x0.61 / x0.60 | RISK-KEEP | 468 / 307 / 62 / 432 |
| floor $4k / arm 1.5R keep 0.25 / caps +5R -2R | +31% | +34% | +34% | +32% | +1% | +58% / +39% | -15.4 (17.3) / -8.1 (7.3) | n / n | x0.64 / x0.58 | RISK-KEEP | 471 / 159 / 62 / 432 |
| floor $4k / arm 1.5R keep 0.5 / caps +5R -2R | +26% | +31% | +34% | +32% | +8% | +58% / +32% | -16.9 (18.9) / -8.6 (7.3) | n / n | x0.52 / x0.52 | RISK-KEEP | 473 / 347 / 62 / 432 |
| floor $4k / arm 1.5R keep 0.75 / caps +5R -2R | +36% | +32% | +31% | +9% | +17% | +61% / +23% | -18.8 (20.0) / -9.7 (7.5) | n / n | x0.49 / x0.30 | RISK-KEEP | 473 / 615 / 62 / 432 |
| floor $6k / arm 2R keep 0.25 / caps +5R -2R | +7% | +18% | +43% | +14% | +15% | +43% / +21% | -12.7 (15.0) / -5.7 (6.1) | n / n | x0.58 / x0.66 | RISK-KEEP | 324 / 44 / 62 / 432 |
| floor $6k / no give-back / caps +5R -2R | +6% | +17% | +42% | +4% | +15% | +43% / +21% | -12.2 (14.9) / -6.1 (6.2) | n / n | x0.59 / x0.56 | RISK-KEEP | 325 / 0 / 62 / 432 |
| floor $6k / arm 3R keep 0.25 / caps +5R -2R | +6% | +17% | +42% | +4% | +15% | +43% / +21% | -12.2 (14.9) / -6.1 (6.2) | n / n | x0.59 / x0.56 | RISK-KEEP | 325 / 2 / 62 / 432 |
| floor $6k / arm 2R keep 0.75 / caps +5R -2R | +11% | +21% | +45% | +12% | +17% | +48% / +15% | -13.5 (15.5) / -6.8 (6.4) | n / n | x0.57 / x0.56 | RISK-KEEP | 325 / 306 / 62 / 432 |
| floor $10k / arm 2R keep 0.75 / caps +5R -2R | +3% | +14% | +15% | +13% | -9% | +22% / +12% | -7.9 (10.7) / -5.1 (5.4) | n / n | x0.74 / x0.71 | RISK-KEEP | 157 / 306 / 62 / 432 |

### 5. Lot-shuffle placebo (100 worlds, preference over the live cell in the same world; positive = shallower; engine phase 0, PA9 scoring)
| cell | worlds | L6M maxDD | PRE maxDD | X' maxDD | HOLD maxDD |
|---|---|---|---|---|---|
| floor $10k / arm 2R keep 0.75 / caps +5R -2R | 100 | real +14.8k vs placebo med -8.7k [-47.5,+18.6] rank 0.07 | real +6.1k vs placebo med +3.5k [-57.9,+43.0] rank 0.49 | real -46.8k vs placebo med -9.0k [-52.6,+34.4] rank 0.93 | real +27.5k vs placebo med +46.5k [-8.4,+90.8] rank 0.74 |
| floor $4k / arm 2R keep 0.5 / caps +5R -2R | 100 | real +25.4k vs placebo med +2.5k [-33.4,+30.3] rank 0.07 | real +36.1k vs placebo med +21.6k [-10.4,+47.1] rank 0.15 | real -21.5k vs placebo med +3.6k [-39.2,+46.6] rank 0.84 | real +38.1k vs placebo med +53.7k [+10.6,+99.8] rank 0.83 |
| floor $6k / arm 2R keep 0.25 / caps +5R -2R | 100 | real +25.4k vs placebo med -11.7k [-56.9,+23.9] rank 0.04 | real +20.2k vs placebo med +11.6k [-42.9,+44.6] rank 0.26 | real -25.8k vs placebo med +1.0k [-44.0,+55.0] rank 0.90 | real +38.1k vs placebo med +43.0k [-7.4,+92.1] rank 0.54 |
| floor 12R / arm 2R keep 0.5 / caps +3R -2.5R | 100 | real +10.4k vs placebo med -1.3k [-8.4,+13.2] rank 0.06 | real -0.5k vs placebo med -1.3k [-13.2,+5.0] rank 0.32 | real +0.4k vs placebo med +0.0k [-9.8,+8.4] rank 0.46 | real -8.2k vs placebo med -1.7k [-14.1,+14.8] rank 0.76 |
| floor 4R / arm 2R keep 0.25 / caps +5R -2R | 100 | real +15.7k vs placebo med -0.3k [-20.0,+9.8] rank 0.02 | real -7.1k vs placebo med -7.4k [-25.0,+7.2] rank 0.49 | real -2.1k vs placebo med +2.6k [-15.5,+12.6] rank 0.86 | real +19.7k vs placebo med +17.1k [-9.2,+40.2] rank 0.45 |

### 6. How often the week floor binds (live give-back and caps kept): weeks in which a book was flattened by the floor, whole history 2023-04..2026-10
| floor | HM | KB | SM | PE | MV | PB | total |
|---|---|---|---|---|---|---|---|
| 3R | 5 | 37 | 4 | 26 | 15 | 26 | 113 |
| 4R | 1 | 21 | 1 | 9 | 5 | 10 | 47 |
| 5R | 0 | 10 | 0 | 3 | 1 | 5 | 19 |
| 6R | 0 | 2 | 0 | 1 | 1 | 4 | 8 |
| 7R | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 8R | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 10R | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 12R | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
Correction (Z1): in the one-paragraph answer, the proportional-lock-R PRE cuts are -2% to -59% except two ER-scaled cells at +1% / +2% (PRE dropped up to +4%); give-back fires are 84-1,574 book-days depending on the cell (about 480-590 for the live give-back); the win cap changes nothing at 5R and above, and at 3R/4R gives PRE +4% with L6M +0%. None of this changes the conclusion.
