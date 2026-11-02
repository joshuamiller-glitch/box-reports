# SIZER_HARNESS - T-SIZER scoring harness on V13T_LIVE (ZL-2, 2026-11-02; prep, no strategy claims)
Code: l2vast/ds3/code/zones3/sizer/sizer_harness.py (class Harness), test_harness.py (reference + sizer-off + placebos), test_harness2.py (equal-risk scans, walk-forward toy). Cache and results: /mnt/l2/l2vast/ds3_zones3_new/sizer_cache/ (harness_test.json, harness_test2.json, live_p*.npy base cores for the 9 phases, scan_*.pkl, plc_live_*.npy). python3 -I; uses BASE-4's d7_v13t lots-override hook (lots_mult / lots_round / lscale), V13T_LIVE cost model (xcost 0.80, stopcost 2.45, lines empty, lock none, cancel-on-exit).

## API (input = per-signal multiplier array, 88,490 engine d rows, NaN -> 1.0)
| call | output | time |
|--|--|--|
| H.run(m, lscale, phase, lots_round) | daily core $ (935), cube (6 books x 6 sessions x days) | 3-12 s per engine run (first call 12 s incl. load) |
| H.score(m) | per window L6M/HOLD/MID/PRE/X': maxDD, worst-20, ulcer, CVaR5, Calmar, mean, paired MDE, cut vs live ER ladder, cut with the carrying weeks dropped (L6M 2026 W27-38, PRE 2024 W34-51, X' 2023 W21-41), leave-one-episode-out min cut (top-3 base drawdown episodes of each window); lots distribution (mean lots, % at x0.25/.5/.75/1/1.5, max) | 3-6 s |
| H.pa9(m) | mean cut over 9 lock-reset phases per window, SD, carrying-drop cut, pass vs the V13T PA9 band (flip 2% and 5%; band constants BAND2/BAND5 = DS3_ZONES_3_NOISE_V13T.md partial, update when final), no-harm flag | 27-53 s |
| H.lscale_scan(m) / H.equal_risk(m, window) | engine lot search: runs at lscale 0.6..2.0 (11 runs), linear fit of maxDD and mean vs lscale for the cell and for the live ladder; equal-risk mean = cell's fitted mean where its fitted maxDD equals the live ladder's fitted maxDD at lscale 1 (self-check: live vs live returns lscale* 1.000) | 32 s per scan |
| H.placebos(m, kind, n=100, nproc=3) | kind perm (random multipliers, same distribution, permuted within book x session), dayshuf (each day's multiplier sequence from a random other day), ar1 (Gaussian AR(1) with the lag-1 autocorrelation of the real multiplier path per book, quantile-mapped to the same marginal); rank of the real cell on cut and on mean | 114-129 s per 100 draws with 3 workers |
| H.walk_forward(fit, predict, train_months=6/12) | purged walk-forward scaffold: for each month M fit on the trailing window (taken rows, last 2 label days dropped), predict M; returns the OOS multiplier array (engine run afterwards via score/pa9/placebos) | fit/predict 0.2 s + one engine run |
| H.rows() | per-row table for fitting: label day, month, book, session, kin, session lots, zone factor, live multiplier, net $ with sizer-off (lots x1), taken flag | 3 s |
| H.features() / H.ladder(x, thr, hi, lo) | S4b feature table (feat_signal.parquet) aligned to the d rows; binary ladder helper. Check: ladder(er_5m_20 >= 0.30 -> 1.5 else 0.5) equals the live ladder on 99.95% of taken rows | |
Rank convention: rank = share of placebo draws whose cut (or mean) is BELOW the real cell (high = real beats the placebo). Cuts are relative to the live ER ladder run (phase-matched for PA9). Whole test (references, PA9 both, 3 x 100 placebos, equal-risk): 536 s on 3 workers, memory about 10 GB per worker; memory rule applies (up to 3 workers while available >= 30 GB).

## Test results (reference = live ER ladder; V13T_LIVE, lock none, 17,396 taken core-book signals)
| item | live ER(20) ladder | sizer off (x1) |
|--|--|--|
| total $ 2023-04..2026-10 | 3,481k | 2,526k |
| lots: mean / max / % x0.5 / % x1.5 | 3.20 / 11 / 56.2 / 43.8 (the zone half moves some to 0.25 / 0.75 inside the engine) | 3.14 / 7 / x1 100% |
| L6M: maxDD, mean $/wk | 150.7k, 36.7k | 80.5k, 26.2k (cut +46.6%, mean -10.5k/wk, MDE 19.9k) |
| HOLD: maxDD, mean | 150.7k, 30.4k | 192.4k, 21.1k (cut -27.6%) |
| MID: maxDD, mean | 43.7k, 24.0k | 135.4k, 4.0k |
| PRE: maxDD, mean | 166.2k, 17.3k | 119.9k, 13.8k (cut +27.8%) |
| X': maxDD, mean | 92.5k, 4.8k | 119.9k, 4.9k |
| PA9 cut vs live (L6M / HOLD / MID / PRE / X') | 0 (reference) | +51.9 / -12.7 / -360 / +28.5 / -35.8; carrying-drop +10.1 / - / - / +28.1 / +30.7; passes the band rule on L6M+PRE but fails no-harm |
| equal-risk mean at the live ladder's maxDD (fitted), sizer off vs live ladder | L6M 35.9k, HOLD 29.8k, PRE 15.5k, X' 4.8k | L6M 41.1k (lscale* 1.57), HOLD 15.3k (0.70), PRE 17.1k (1.28), X' 3.2k (0.60); MID unreliable (R2 0.26 on the mean fit) |
| placebos of the live ladder (100 draws each: perm / dayshuf / ar1), rank on cut L6M, HOLD, PRE | the live ladder has a deeper L6M maxDD than random multipliers with its distribution (ranks 0.11 / 0.07 / 0.09) and shallower only in HOLD/MID (0.8-0.99); on MEAN dollars it beats random multipliers in L6M 0.93-0.96, HOLD 0.95-0.99, PRE 0.94-0.96, X' 0.41-0.48 | |
Reading (harness validation, not a finding about the sizer): on V13T_LIVE the ER ladder adds about +$950k over the history and +10.5k/wk in L6M but deepens the L6M maxDD from 80k to 151k; at equal fitted maxDD the sizer-off book is better in L6M and PRE and worse in HOLD and X'. The fit noise is real (integer lots): self-check shows raw per-point equal-risk would be off by up to 0.3 lscale, hence the smoothed fits; treat equal-risk means as +-10%.
Toy walk-forward check (per book x session sign of the trailing 12-month mean net -> x1.5/x0.5, 20 placebo draws): mechanics work (lots mean 4.2, ranks printed per window), not a result.

## Known limits
Phase-0 placebos only; the band is the partial V13T PA9; carrying weeks are fixed ranges, leave-one-episode-out uses the base's top-3 drawdown episodes per window; the lscale scan is linear (R2 reported); a vol-tercile / per book x session split is not built into score() (use H.rows() groups and cube); lock 12R per-book frame via H.run(m, lock=12) is reference only. lots_round='sequential' available (BASE-4 open item on live rounding).
