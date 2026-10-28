# DS3_OPEN_B2_OR_DRIVE - T-OPEN block (ii): 3.1 opening-range breaks and 3.2 drive continuation (D3O1, 2026-10-28)
Research only; no live/chart/execution-server change, no credentials, no purchases, no deletions. Harness, bases, placebos, gates, audits, control rows: `autopilot/DS3_OPEN_B2_HARNESS.md` and `l2vast/ds3/code/open2/README_OPEN2.md`. Rows: `l2vast/ds3/rows/DS3_TOPEN_B2_{ORbase,ORre,ORcond,DRbase,DRcond}.json`; series for the CANDIDATE cells: `l2vast/ds3/out/SERIES/DS3_TOPEN_B2_<cell>_<M|T>.parquet`; per-variant results `l2vast/ds3/out/topen_b2/grp_*/`.

## 1. Verdict
**3.1 OR breaks: 0 PASS, 0 CANDIDATE of 7,200 scored cells (ORbase 910, ORre 848, ORcond 5,442; 0 PASS / 0 CANDIDATE; ORcond had 2 M-basis-only CANDIDATE labels that are DEAD on basis T). 3.2 Drive continuation: 0 PASS, 10 CANDIDATE of 2,295 scored cells (DRbase 288: 0; DRcond 2,007: 10), all ten in ONE cluster: the 5-minute drive with |move| >= 0.5 x the 20-day median 5-minute opening range, entered at the first pullback (pb1 = first 1-min counter bar close, pb3 = first 3-min counter block close), brackets F45 / F60 / T1030 / T1200 / HOLD / STRAIL / SCALE; each fails ONLY the family-wise best-of-N gate on both bases.** Nothing is recommended for live; the cluster is the object for block (iii) (full target/stop/exit grid) and for forward weeks.

Best-of-N reading: the registered gate (effect vs random clock above the 95th percentile of the per-draw maximum over all registered cells of the family, N_total 7,668 for 3.1 and 2,304 for 3.2) fails for every cell. The null is dominated by small-sample conditioned cells (null p95 about 140 pts vs the cluster's 10-28 pts); by the cell-level bootstrap the cluster has z = 1.9-3.2 (effect vs random clock / bootstrap SE) while a Bonferroni line over about 10,000 cells needs z of about 4.4: consistent with a best-of-N chance finding, not excluded as real. Forward weeks to settle (80% power on the WF stack effect): 117-186 weeks per cell (146-395 on the HOLD effect).

## 2. Scope
Block (ii) screen exactly as the directive: 1-min bars, market entries, the 12-cell bracket core x 2 bases (M mapped conservative / T tape-direct-style), fixed 10 lots, verdict = lower tier of the two bases. Prereg: 416 groups of <= 24 cells (2 variants x 12 brackets), master prereg sha256 per block in DECISIONS.md and `l2vast/ds3/prereg/TOPEN_B2_<block>_hashes.json`; holdout looks logged one per group in `struct48/ledger/holdout_looks.jsonl` (416), trials +9,972 in `trials.jsonl`.
| block | registered (variants x 12) | scored cells (rest = no valid trade, e.g. VWAP target behind a continuation entry) | groups |
|---|---|---|---|
| ORbase (9 OR lengths x 9 break types, one-and-done) | 81 x 12 = 972 | 910 | 41 |
| ORre (first signal + second break after a stop-out) | 72 x 12 = 864 | 848 | 36 |
| ORcond (OR size >=/<= 0.5/1/1.5 x 20-day median) | 486 x 12 = 5,832 | 5,442 | 243 |
| DRbase (D in 1,2,3,5,10,15 x mark/pb1/pb3/hl) | 24 x 12 = 288 | 288 | 12 |
| DRcond (od, mv5/10/15/20, rm0.5/rm1) | 168 x 12 = 2,016 | 2,007 | 84 |
| total | 9,972 | 9,495 | 416 |
Entry types as the directive: OR {30 s, 1, 2, 3, 5, 10, 15, 30, 60 min}; stop-entry at OR H/L +1 tick (kind stp: M fills at level+1 tick = MAPPED-ONLY, T = first print through the level + 1 tick), first 1-min close outside, first 5-min close outside, close outside by 2 / 5 pts, two consecutive closes, retest-and-hold within 5 / 15 min, second break after a failed first; drives {1,2,3,5,10,15} min at the mark / first 1-min pullback / first 3-min pullback / first higher-low; open-drive-only, move >= 5/10/15/20 pts, >= 0.5x/1x the 20-day median 5-min range. Opening-type, gap-class, VIX tercile, day-of-week, release flags, FOMC/opex/month-end and ALL pre-open (09:29 table) features are conditioning COLUMNS in every cell's `cond` table (interaction table with CIs inside each variant pickle); only the size/strength conditions above are filters, each with its own in-regime placebo (c).
Not scored in this block (block (iii)+): full section-4 grid, other bar types, stop-limit/limit/OCO order types, direct L2 replay, footprint/L2 triggers, other instruments, learned classifier.

## 3.Tier counts by block and basis

|                 |   CANDIDATE |   DEAD |
|:----------------|------------:|-------:|
| ('DRbase', 'M') |           1 |    287 |
| ('DRbase', 'T') |           0 |    288 |
| ('DRcond', 'M') |          13 |   1991 |
| ('DRcond', 'T') |          11 |   1996 |
| ('ORbase', 'M') |           0 |    909 |
| ('ORbase', 'T') |           0 |    910 |
| ('ORcond', 'M') |           2 |   5437 |
| ('ORcond', 'T') |           0 |   5440 |
| ('ORre', 'M')   |           0 |    848 |
| ('ORre', 'T')   |           0 |    848 |

## 3.Final verdict (lower tier of M/T) by block

| block   |   CANDIDATE |   DEAD |
|:--------|------------:|-------:|
| DRbase  |           0 |    288 |
| DRcond  |          10 |   1997 |
| ORbase  |           0 |    910 |
| ORcond  |           0 |   5442 |
| ORre    |           0 |    848 |

## 3.Failed-gate counts (basis T)

| failed        |   DRbase |   DRcond |   ORbase |   ORcond |   ORre |
|:--------------|---------:|---------:|---------:|---------:|-------:|
| beats_b       |      272 |     1881 |      891 |     5227 |    821 |
| beats_beta    |      287 |     1952 |      899 |     5423 |    842 |
| beats_c       |        0 |       28 |        0 |       10 |      0 |
| best_of_N     |      284 |     2007 |      896 |     5370 |    821 |
| cost2x_pre    |      103 |      496 |      350 |     2430 |    396 |
| hold          |      190 |     1031 |      785 |     4353 |    757 |
| mean_up       |       55 |      343 |      233 |     1980 |    281 |
| min_n         |       12 |      487 |       20 |     1280 |     47 |
| neighbours    |       89 |      525 |      414 |     3043 |    463 |
| span2         |      111 |      960 |      587 |     3383 |    645 |
| stack_add_pre |      274 |     1850 |      886 |     5321 |    829 |
| year_share    |      229 |     1384 |      858 |     5067 |    815 |


## 4. The CANDIDATE cluster (3.2, 5-minute drive, rm0.5, pullback entry)
Rule: at 09:35 the drive is the sign of close(09:34) - open(09:30); condition |move| >= 0.5 x the 20-day median of the 09:30-09:34 high-low range (same-origin rolling median, as-of prior days); entry (pb1) at the close of the first 1-min bar that closes against the drive (pb3: first 3-min block from 09:35 that closes against it), market at the next second (+1 s on basis T), window to 10:30, one trade per day; brackets as listed. 432 events in 955 days (45% of days; about 174 in the 75-week selection span), 2.3 trades/wk (SCALE 4.6 rows), long/short split 50/50.
### CANDIDATE cells (fail only best_of_N), both bases

| cell | basis | stand-alone PRE / HOLD / 2023 $/wk | trades/wk | win vs req | stack dSh PRE / WF / HOLD | dMean PRE / HOLD / 2023 $/wk | dMaxDD WF | MDE PRE-mean | eff vs random clock pts [CI] rank | eff vs random direction | vs 09:30-un-block dSh / dMean (WF) | vs D3SL-published dSh / dMean |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| DR5m_pb1_rm0.5_F45 | M | 4,233 / 1,786 / 562 | 2.3 | 0.60/0.52 | 0.23 / 0.15 / 0.06 | 4,233 / 1,786 / 562 | -64,874 | 3,368 | 11.3 [4.2,18.0] r1.00 | 10.8 r1.00 | -0.078 / -2,753 | 0.094 / -602 |
| DR5m_pb1_rm0.5_F45 | T | 3,925 / 2,881 / 874 | 2.3 | 0.59/0.50 | 0.21 / 0.16 / 0.11 | 3,925 / 2,881 / 874 | -71,613 | 3,532 | 10.0 [2.4,16.9] r1.00 | 9.6 r1.00 | -0.062 / -2,392 | 0.110 / -240 |
| DR5m_pb1_rm0.5_F60 | M | 4,346 / 2,461 / 1,388 | 2.3 | 0.58/0.52 | 0.21 / 0.18 / 0.14 | 4,346 / 2,461 / 1,388 | -88,874 | 4,264 | 12.9 [3.1,21.7] r1.00 | 11.4 r1.00 | -0.049 / -2,370 | 0.123 / -219 |
| DR5m_pb1_rm0.5_F60 | T | 5,258 / 3,896 / 1,932 | 2.3 | 0.59/0.50 | 0.26 / 0.25 / 0.23 | 5,258 / 3,896 / 1,932 | -95,613 | 4,325 | 13.6 [3.4,23.2] r1.00 | 13.4 r1.00 | 0.020 / -1,202 | 0.192 / 950 |
| DR5m_pb1_rm0.5_SCALE | M | 5,798 / 3,070 / 1,255 | 4.6 | 0.49/0.39 | 0.33 / 0.21 / 0.09 | 5,798 / 3,070 / 1,255 | -68,231 | 3,983 | 13.6 [4.4,21.8] r1.00 | 12.2 r1.00 | -0.016 / -1,312 | 0.156 / 840 |
| DR5m_pb1_rm0.5_SCALE | T | 5,191 / 3,573 / 1,367 | 4.6 | 0.48/0.38 | 0.29 / 0.20 / 0.11 | 5,191 / 3,573 / 1,367 | -71,175 | 4,049 | 12.2 [3.2,20.3] r1.00 | 11.0 r1.00 | -0.022 / -1,392 | 0.150 / 760 |
| DR5m_pb1_rm0.5_STRAIL | M | 6,168 / 4,134 / 2,105 | 2.3 | 0.40/0.31 | 0.34 / 0.24 / 0.14 | 6,168 / 4,134 / 2,105 | -70,148 | 5,396 | 12.9 [3.0,22.0] r1.00 | 11.2 r1.00 | 0.016 / -607 | 0.188 / 1,545 |
| DR5m_pb1_rm0.5_STRAIL | T | 5,455 / 3,900 / 2,037 | 2.3 | 0.40/0.31 | 0.29 / 0.21 / 0.12 | 5,455 / 3,900 / 2,037 | -69,298 | 5,430 | 12.6 [2.8,21.6] r1.00 | 12.0 r1.00 | -0.013 / -1,096 | 0.159 / 1,056 |
| DR5m_pb1_rm0.5_T1030 | M | 6,359 / 4,867 / 709 | 2.3 | 0.47/0.39 | 0.26 / 0.20 / 0.14 | 6,359 / 4,867 / 709 | -60,945 | 6,186 | 14.5 [2.5,26.1] r1.00 | 12.4 r1.00 | -0.024 / -155 | 0.147 / 1,997 |
| DR5m_pb1_rm0.5_T1030 | T | 6,338 / 4,602 / 921 | 2.3 | 0.47/0.39 | 0.26 / 0.20 / 0.13 | 6,338 / 4,602 / 921 | -64,695 | 6,220 | 14.0 [2.1,25.9] r1.00 | 13.9 r1.00 | -0.024 / -293 | 0.148 / 1,859 |
| DR5m_pb1_rm0.5_T1200 | M | 8,922 / 3,617 / 2,096 | 2.3 | 0.46/0.37 | 0.39 / 0.22 / 0.04 | 8,922 / 3,617 / 2,096 | -33,800 | 6,544 | 23.7 [6.5,40.3] r1.00 | 19.1 r1.00 | -0.005 / 600 | 0.167 / 2,751 |
| DR5m_pb1_rm0.5_T1200 | T | 8,680 / 4,016 / 2,673 | 2.3 | 0.46/0.37 | 0.38 / 0.23 / 0.07 | 8,680 / 4,016 / 2,673 | -34,863 | 6,697 | 23.5 [6.2,40.0] r1.00 | 21.1 r1.00 | 0.004 / 664 | 0.176 / 2,815 |
| DR5m_pb3_rm0.5_HOLD | M | 10,145 / 8,828 / 1,535 | 2.3 | 0.45/0.33 | 0.40 / 0.27 / 0.13 | 10,145 / 8,828 / 1,535 | -36,050 | 8,374 | 28.7 [3.6,61.4] r1.00 | 22.8 r1.00 | 0.043 / 3,741 | 0.214 / 5,893 |
| DR5m_pb3_rm0.5_HOLD | T | 9,822 / 8,322 / 2,076 | 2.3 | 0.44/0.33 | 0.37 / 0.24 / 0.11 | 9,822 / 8,322 / 2,076 | -37,563 | 8,451 | 28.4 [3.1,60.9] r1.00 | 23.2 r1.00 | 0.017 / 3,328 | 0.189 / 5,480 |
| DR5m_pb3_rm0.5_STRAIL | M | 4,377 / 4,061 / 867 | 2.3 | 0.40/0.32 | 0.27 / 0.20 / 0.12 | 4,377 / 4,061 / 867 | -42,998 | 4,506 | 10.5 [0.7,19.4] r1.00 | 11.1 r1.00 | -0.029 / -1,588 | 0.143 / 564 |
| DR5m_pb3_rm0.5_STRAIL | T | 4,274 / 3,791 / 838 | 2.3 | 0.39/0.31 | 0.27 / 0.19 / 0.11 | 4,274 / 3,791 / 838 | -41,598 | 4,501 | 10.5 [0.7,19.2] r1.00 | 11.3 r1.00 | -0.037 / -1,771 | 0.135 / 380 |
| DR5m_pb3_rm0.5_T1030 | M | 5,938 / 4,586 / 328 | 2.3 | 0.50/0.42 | 0.31 / 0.20 / 0.10 | 5,938 / 4,586 / 328 | -51,227 | 5,308 | 14.6 [3.1,25.6] r1.00 | 14.0 r1.00 | -0.022 / -512 | 0.150 / 1,640 |
| DR5m_pb3_rm0.5_T1030 | T | 5,770 / 4,579 / 870 | 2.3 | 0.50/0.42 | 0.28 / 0.19 / 0.10 | 5,770 / 4,579 / 870 | -51,045 | 5,372 | 14.8 [3.4,25.6] r1.00 | 14.3 r1.00 | -0.033 / -604 | 0.139 / 1,547 |
| DR5m_pb3_rm0.5_T1200 | M | 8,355 / 5,050 / 876 | 2.3 | 0.47/0.37 | 0.40 / 0.22 / 0.04 | 8,355 / 5,050 / 876 | -20,200 | 6,459 | 19.7 [3.0,35.7] r1.00 | 20.2 r1.00 | -0.005 / 987 | 0.167 / 3,138 |
| DR5m_pb3_rm0.5_T1200 | T | 8,344 / 4,821 / 823 | 2.3 | 0.47/0.37 | 0.39 / 0.21 / 0.03 | 8,344 / 4,821 / 823 | -21,713 | 6,564 | 19.8 [2.9,35.9] r1.00 | 20.9 r1.00 | -0.014 / 871 | 0.158 / 3,023 |


Reading: (i) it passes mean_up, 2x cost, year share <= 60% (best year 2024), the random-clock placebo (CI lower > 0, rank 1.00), the random-direction placebo, the in-regime random-direction placebo (c) (effect +10 to +23 pts, rank 1.00), the stack-add gate in the selection span (d_Sharpe > 0, CI of d_mean lower bound > 0, maxDD better by 20-96k), the neighbour gate (adjacent drive lengths), the HOLD gate (HOLD stack d_Sharpe +0.03 to +0.23, d_mean +1.8k to +8.8k $/wk) and the 2023-04..2024-01 span (+0.3k to +2.7k $/wk, effect vs placebos positive but CI includes 0); (ii) it is ONE idea: pb1 and pb3 trade the same 432 days, daily correlation 0.68, brackets are exits on the same entries; (iii) it is a regime FILTER plus direction: the unconditioned DR5m_pb1 on the same entries is DEAD (F60 T: PRE -888 $/wk, stack d_Sharpe +0.03), the 432 filtered days earn +9.2 pts/trade and the 520 excluded days -7.0; honest-null rule: the placebo (c) (same filtered days, random direction) is beaten, so the direction carries information beyond the regime, but the filter is what turns the cell positive; (iv) ridge, not a spike: D = 5-10 with rm0.5 is positive in all four entry types (median stack d_Sharpe on rm0.5 by drive length and entry type: 1 min -0.01..+0.05, 2 min +0.07..+0.13, 3 min +0.05..+0.12, 5 min +0.07..+0.20, 10 min +0.13..+0.25, 15 min +0.05..+0.08), the stricter threshold rm1 is positive but smaller (fewer than 150 trades), mv5-mv20 move thresholds show the same shape; (v) mirror (fade the same entries): about -5k to -8k $/wk PRE and -4k to -9k HOLD: the continuation side carries the directional information; (vi) year profile: 2023 +0.9k $ per trade for pb1 F60 (-0.1k for pb3) vs +2.7k in 2024 (strongest), 2025-26 positive; VIX top tercile negative (-0.7k per trade over 95 trades), low and mid VIX positive; long and short symmetric; opening type at 09:35: OD +2.6k, OTD +2.1k, ORR +2.9k, OA +0.2k per trade (the 10:00-cut type OTD is +11k and OA -2k, but that label includes bars after the entry, so it is descriptive, not a usable filter); (vii) equal risk vs ST10: DR5m_pb3_rm0.5_HOLD at 16 lots is +15.3k $/wk (M) / +14.5k (T) vs ST10 14.3k at equal weekly SD (delta +1.0k / +0.2k); the F60 / T1200 / SCALE cells are -0.4k to -4.6k vs ST10 at equal risk (not a DEAD criterion by the rules); (viii) executability: NT8 1-minute bars, market entry; the HOLD variant overlaps the live stack's afternoon (concurrency not modelled in this screen: the 50-cap and margin line are block (ix) items); direct replay, capacity at 09:35-09:45 and 10-lot sweep cost are block (iii)+.
Power: weekly stack-mean MDE 3.4k-8.5k $/wk (PRE); the observed WF effects 3.5k-9.2k are of the order of the MDE, hence the 117-186 forward weeks. A null forward result would not be informative inside about 2.5 years of weeks.

## 5.Top 15 cells overall by stack-add Sharpe delta (WF, lower of M/T), regardless of verdict

| # | cell | verdict | failed gates (T) | dSh WF M/T | dMean WF [CI] | dMaxDD WF | MDE | forward weeks to settle | WF stand-alone $/wk | HOLD dSh | 2023 dMean | eff vs rand-clock [CI] r | vs 09:30 un-block dSh / dMean |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | DR10m_pb1_rm0.5_HOLD | DEAD | beats_b, beats_c, beats_beta, stack_add_pre, best_of_N | 0.346 / 0.342 | 9,553 [4,136,15,110] | -28,164 | 8,270 | 106 | 9,553 | 0.366 | 1,018 | 14.9 [-3.3,32.4] r1.00 | 0.117 / 3,709 |
| 2 | DR10m_pb1_rm0.5_T1200 | DEAD | beats_b, beats_beta, stack_add_pre, best_of_N | 0.296 / 0.294 | 7,355 [3,051,11,968] | -16,664 | 6,606 | 115 | 7,355 | 0.281 | 577 | 11.5 [-2.3,23.5] r1.00 | 0.069 / 1,510 |
| 3 | DR10m_pb1_rm1_HOLD | DEAD | beats_b, stack_add_pre, best_of_N | 0.291 / 0.301 | 6,956 [2,919,11,166] | 11,097 | 6,380 | 119 | 6,956 | 0.296 | 2,178 | 16.0 [-9.8,41.5] r1.00 | 0.076 / 1,111 |
| 4 | DR10m_mark_rm0.5_HOLD | DEAD | beats_b, beats_c, beats_beta, stack_add_pre, best_of_N | 0.341 / 0.284 | 8,829 [3,786,14,283] | -19,064 | 7,989 | 116 | 8,829 | 0.335 | 1,088 | 9.0 [-9.2,27.0] r0.94 | 0.059 / 2,985 |
| 5 | DR10m_hl_rm0.5_HOLD | DEAD | beats_b, beats_beta, stack_add_pre, best_of_N | 0.282 / 0.271 | 8,209 [3,134,13,525] | -22,464 | 7,440 | 117 | 8,209 | 0.267 | 3,336 | 17.5 [-1.1,37.8] r1.00 | 0.046 / 2,364 |
| 6 | DR10m_mark_rm1_HOLD | DEAD | beats_b, stack_add_pre, best_of_N | 0.267 / 0.268 | 6,714 [2,898,11,439] | 9,297 | 6,285 | 124 | 6,714 | 0.329 | 3,097 | 9.6 [-17.3,37.3] r0.75 | 0.043 / 870 |
| 7 | DR5m_pb1_rm0.5_HOLD | DEAD | best_of_N | 0.267 / 0.285 | 8,570 [3,378,13,824] | -50,713 | 7,817 | 118 | 8,570 | 0.195 | 2,668 | 20.2 [0.7,39.1] r1.00 | 0.060 / 2,726 |
| 8 | DR10m_pb1_rm1_T1200 | DEAD | beats_b, best_of_N | 0.266 / 0.267 | 5,484 [2,192,8,691] | 2,947 | 5,035 | 120 | 5,484 | 0.255 | 1,159 | 16.8 [-3.4,37.7] r1.00 | 0.042 / -360 |
| 9 | DR10m_pb1_rm0.5_T1030 | DEAD | beats_b, beats_c, beats_beta, stack_add_pre, span2, best_of_N | 0.266 / 0.266 | 6,174 [2,144,10,082] | -55,264 | 5,815 | 126 | 6,174 | 0.328 | -1,349 | 5.4 [-5.0,15.6] r1.00 | 0.041 / 330 |
| 10 | DR10m_pb1_rm1_T1030 | DEAD | beats_b, beats_c, stack_add_pre, span2, best_of_N | 0.260 / 0.255 | 5,430 [2,498,8,547] | -14,703 | 4,593 | 102 | 5,430 | 0.280 | -461 | 13.4 [-2.5,29.5] r1.00 | 0.031 / -414 |
| 11 | DR5m_pb1_mv20_STRAIL | DEAD | beats_b, beats_beta, best_of_N | 0.325 / 0.255 | 5,762 [1,367,10,016] | -40,279 | 6,402 | 175 | 5,762 | 0.241 | 1,706 | 5.4 [-5.2,16.0] r1.00 | 0.030 / -82 |
| 12 | DR10m_hl_rm1_HOLD | DEAD | beats_b, beats_c, stack_add_pre, best_of_N | 0.271 / 0.254 | 6,088 [2,470,10,134] | 17,347 | 5,788 | 128 | 6,088 | 0.212 | 1,830 | 26.1 [-4.4,56.7] r1.00 | 0.029 / 243 |
| 13 | DR2m_pb3_SCALE | DEAD | beats_b, beats_beta, stack_add_pre, span2, best_of_N | 0.256 / 0.254 | 4,949 [1,024,8,826] | -62,619 | 5,586 | 181 | 4,949 | 0.273 | -777 | 3.8 [-1.6,9.1] r0.94 | 0.029 / -895 |
| 14 | OR30s_c2_le1.5_T1200 | DEAD | beats_b, stack_add_pre, hold, best_of_N | 0.320 / 0.253 | 6,497 [564,12,318] | 76,235 | 8,424 | 239 | 6,497 | -0.059 | 1,822 | 11.1 [-0.2,23.1] r1.00 | 0.029 / 653 |
| 15 | DR10m_pb1_rm0.5_CHAND | DEAD | beats_c, beats_beta, stack_add_pre, span2, best_of_N | 0.264 / 0.249 | 4,744 [1,662,7,800] | -53,006 | 4,359 | 120 | 4,744 | 0.253 | -1,338 | 9.4 [1.5,17.3] r1.00 | 0.024 / -1,100 |


Gate legend: * = gate not evaluated because a cheaper gate had already failed (the post-pass placebos were run for the top 15 cells of every block, so most rows show evaluated gates). The top cells are dominated by long-hold brackets (HOLD, T1200, T1030) whose positive stack effect is partly bracket beta: random-direction entries at 09:31 with the same brackets earn +1.2k to +4.2k $/wk in the selection span (control table in DS3_OPEN_B2_HARNESS.md section 3).

## 6. The block question: does an open book beat un-blocking the existing books 09:00-10:00?
Baselines (WF, 142 weeks): live stack $44.9k/wk (entries 09:00-09:59 blocked), the same with 09:30-09:59 un-blocked $50.7k/wk (+5.8k/wk, Sharpe 2.4 -> 2.6, maxDD +23k worse), the D3SL stack as published (09:00-09:59 traded) $48.6k/wk. The existing books' own 09:30-09:59 flips (control row 3.13): PRE +12.1k/wk, WF +6.3k, HOLD -0.06k, 2023 span +0.4k, maxDD +99k worse: the un-block gain is a selection-span effect that is absent in the holdout.
Open books against that: 32 of 9,495 cells have a stack d_Sharpe above the 09:30-09:59 un-block in both bases, 18 of them also a higher d_mean; the ten best are all 10-minute-drive HOLD/T1200/T1030 cells of 3.2 that are DEAD on other gates (best: DR10m_pb1_rm0.5_HOLD, +0.117 d_Sharpe and +3.6k/wk over un-blocking, fails the random-direction and random-clock gates). Among the CANDIDATEs: DR5m_pb3_rm0.5_HOLD beats un-blocking by +3.7k (M) / +3.3k (T) $/wk and +0.04 / +0.02 Sharpe in WF and its maxDD is 36k better where un-blocking is 23k worse; the F60 / F45 / SCALE / STRAIL / T1030 candidates are -0.2k to -2.8k $/wk below un-blocking in mean but have 40-96k better maxDD; DR5m_pb1_rm0.5_T1200 is level with un-blocking in mean (+0.6k) with maxDD 35k better. In the holdout alone un-blocking adds -0.06k/wk while the cluster adds +1.8k to +8.8k/wk. Answer: no open book clears the un-block comparison with a confidence interval (all differences are inside the MDE of 5-8k $/wk); the CANDIDATE cluster is the only family that is not worse than un-blocking in mean and is better in drawdown and in the holdout.

## 7. Structural read
- 3.1 OR breaks: nothing. Over 7,200 OR cells the median stack d_Sharpe is -0.035 (ORbase), -0.069 (ORre), -0.011 (ORcond); only 22-36% of cells raise the stack Sharpe and HOLD standalone is positive in 31-37% of them. The OR cells that look good are the long-hold brackets, i.e. bracket beta (random-direction entries earn as much). In ORbase the longer ORs (10, 15, 30, 60 min) are worse than the short ones (1-3 min median d_Sharpe -0.005..+0.019 vs -0.044..-0.088); the stop-entry (stp) is the least bad entry type (median +0.004) and the 5-min close (c5) the worst (-0.073); retest-and-hold and second-break entries add nothing over the first close; re-entry after a stop-out lowers the result (-0.069 vs -0.035); OR-size conditions do not rescue it (median d_Sharpe -0.002 to -0.032 over the six conditions; ge0.5, le1.5 and le1 have the highest PRE medians and the worst HOLD medians, -0.6k to -0.7k $/wk). Executability of the top OR cells: NT8-bars (stp cells MAPPED-ONLY: the M basis fills at the level +1 tick; the T basis, first print through the level, is the verdict basis and does not rescue them).
- 3.2 drives: continuation after a strong enough drive, with a pullback entry, is the only positive structure: median stack d_Sharpe by condition rm0.5 +0.087, rm1 +0.032, mv20 +0.060, mv15/mv10 +0.027/+0.026, mv5 +0.018, none +0.016, od +0.005 (strict open-drive: too few days); by drive length the 5-10 minute drives are best (median +0.07 to +0.25 on rm0.5), 1 minute and 15 minute drives are weak; pb1 / pb3 entries beat the mark entry (the pullback improves the price without losing the continuation), hl is similar but fires less. Which brackets pay: all 12 brackets are positive in the cluster; target-less long-hold brackets (HOLD, T1200) have the largest dollar effect and the largest bracket beta, the tight fixed brackets F45/F60 and SCALE the smallest effect with the better drawdown and the cleaner placebo ranks; ORX, VWAP and ONHL structural targets add nothing (VWAP is invalid behind most continuation entries: only 352 of 831 variants have any valid VWAP trade).
- Opening types and conditioning: strict open-drive (OD) is too rare to carry a result (1.4-6.8% of days); the continuation cluster earns in OTD and ORR days, little in OA at the 09:35 cut; pre-open features (pre-market drive and 08:30 release direction aligned with the trade, London direction, gap direction, prior-day type, ON range / volume terciles) were tabulated for every cell; none turns an otherwise DEAD cell positive and none changes the cluster's sign; low and mid VIX carry it, high VIX does not (n=95 trades).
- Tape and book: 3.1/3.2 are bar/tape-only in this screen; the T basis (1 s delay, quote fill, stop slip 1 tick, strict targets) differs from M by -0.7k to +0.9k $/wk on the cluster's PRE means with no systematic sign; L2/footprint triggers are block (vi).

### By bracket over all 8,000+ cells (basis T): share of cells with stack dSh>0 (WF), median dSh, share with standalone PRE mean>0, share passing mean_up AND beats random-direction (where evaluated)

| bracket | cells | share dSh>0 | median dSh | share PRE>0 | median PRE $/wk | random-direction control PRE $/wk (T) |
|---|---|---|---|---|---|---|
| F30 | 831 | 0.33 | -0.015 | 0.41 | -120 | -1,460 |
| F45 | 831 | 0.47 | -0.002 | 0.67 | 500 | -231 |
| F60 | 831 | 0.56 | 0.009 | 0.83 | 1,970 | 226 |
| ORX | 831 | 0.33 | -0.028 | 0.60 | 394 | -475 |
| VWAP | 352 | 0.51 | 0.000 | 0.41 | 0 | -397 |
| ONHL | 831 | 0.39 | -0.010 | 0.73 | 533 | 186 |
| T1030 | 831 | 0.44 | -0.004 | 0.74 | 1,158 | 1,172 |
| T1200 | 831 | 0.42 | -0.011 | 0.83 | 2,707 | 3,951 |
| HOLD | 831 | 0.52 | 0.004 | 0.90 | 4,479 | 4,219 |
| STRAIL | 831 | 0.44 | -0.009 | 0.73 | 1,041 | 1,350 |
| CHAND | 831 | 0.31 | -0.025 | 0.58 | 168 | -1,295 |
| SCALE | 831 | 0.52 | 0.002 | 0.74 | 1,031 | 458 |

## 8. Power statement (per family)
3.1: 7,200 cells, weekly stack-mean MDE 5-10k $/wk per cell (80% power, PRE 75 weeks; sd of the weekly difference 15-35k), per-trade effect MDE 6-12 pts; family-wise best-of-N null over N_total 7,668. A null in 3.1 reads: could not have seen a stack gain below about 8k $/wk or about 8 pts per trade vs a random clock for any single OR-break cell, and no cell cleared the family-wise line. 3.2: 2,295 cells, MDE 3-9k $/wk (the filtered cells have fewer trades but lower sd); N_total 2,304. The 10 CANDIDATE cells are inside 1-2.5 MDE of zero in the PRE span and are the one place where the sign, the placebos, the holdout and the 2023 span agree.

## 9. Deviations and disclosures (all of them)
1. Harness bug fixed before any group look: DS2 path vs library space differ on 15 roll days (offset up to 8.5 pts); ORbase first pass (35 variants) abandoned, recomputed (grp_ORbase_v2); no prereg parameter changed. 2. Gate `min_n` (>= 30 PRE trades) added to the verdict code AFTER the ORbase run, when a 5-trade cell passed every other gate (stricter than the prereg; the ORbase pre-texts were rewritten once afterwards, the originals' sha256 are in `holdout_looks.jsonl` and no longer match the files on disk; all later blocks' prereg masters mention the gate). 3. Placebos (a),(c),(d) were run only for cells passing the cheap gates; for the displayed top-15 cells of each block they were run afterwards (`o2_toppost.py`), which cannot change a verdict. 4. The final result files were regenerated twice without new looks (`O2_NOLOG`: plc_extra merged, gate details annotated); no new data was read. 5. The best-of-N gate is the registered raw-effect version; a standardised version (effect / SD of the 16 draw means) was tried as a sensitivity and discarded because the draw SD understates the sampling error of the real mean (z of 5-10 for cells with near-identical draws); the cell-level bootstrap z values quoted above are the sensitivity reported. 6. Development prints before scoring: OR5m_c1 WFPRE numbers (smoke test); the all-window interaction table of one scratch cell (OR5m_c1 M F60, pre-fix pickle); the control tables with HOLD columns; dry-run report files `*_dry*` for 26 ORbase variants (not read; deletion is not permitted). 7. Nothing is DEAD solely for earning less than ST10 at equal lots. 8. M-basis-only CANDIDATE labels (DEAD on T, hence DEAD overall): DR10m_hl_STRAIL, DR10m_hl_rm1_T1200, DR3m_pb1_rm0.5_F30, DR5m_hl_rm0.5_STRAIL, OR1m_c1_ge0.5_STRAIL, OR3m_c1_le1.5_STRAIL. 9. Duplicates: identical daily series are flagged per row (`duplicates`); pb1/pb3 and the brackets of one entry are one idea. 10. Data coverage: tape and bars to 2026-10-23, stack calendar and all scored weeks to 2026-10-16 (WF 142 weeks, HOLD 68 weeks 2025-07..2026-10-16), the L2 raw ends 2026-10-09 (not used here), VIX/forecaster to 2026-10-16. 11. The live stack baseline used here removes 09:00-09:59 entries from the D3SL books (the as-published D3SL stack trades there); both are reported.

## 10. Addendum 2026-10-28: secondary best-of-N column (per-bracket-class null; harness primary unchanged)
Code `o2_classnull.py` (`out/topen_b2/classnull.json`, `classnull_candidates.json`). Classes: fixed {F30,F45,F60,ORX}, struct {VWAP,ONHL}, time {T1030,T1200,HOLD}, trail {STRAIL,CHAND}, scale {SCALE}. Null p95 of the per-draw maximum over the class cells, scaled to the class's share of the registered family (3.1 N_total 7,668, 3.2 2,304). 3.2 class nulls (M / T, pts): fixed 37.5 / 50.6, scale 36.5 / 39.9, trail 51.4 / 51.9, time 131.7 / 131.6, struct 135.7 / 122.3. 3.1: fixed 42.5, scale 30.5, trail 33, time 90-98, struct 52-54.
Re-label of the 10 CANDIDATEs (effect vs random clock, pts, against their class p95): all 20 cell-bases FAIL the secondary column (fixed-class F45/F60 10-14 vs 38-51; scale 12-14 vs 37-40; trail 10.5-13 vs 51-52; time-class T1030/T1200/HOLD 14-29 vs 132). Reading: primary = CANDIDATE (fails only family-wise best-of-N), secondary = FAIL; none of the 10 is promoted. Caveat recorded: the class nulls are driven by the small-sample conditioned cells (n < 150 trades) whose draw dispersion is large, so they are conservative for a 170-trade cell; the cell-level bootstrap z (1.9-3.2 vs about 4.4 for Bonferroni over about 10,000 cells) points the same way.
