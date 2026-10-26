# REPORT IDEAS-50K N2 / N4 / N6 (a027)

## Counts
| Book | Enumerated | Low activity (<20 days) | Series-deduped | Built cells | Families |
|---|---|---|---|---|---|
| N2 event-time | 35,790 | 9,380 | 318 | 26,092 | 170 |
| N4 volatility | 23,184 | 2,824 | 117 | 20,243 | 132 |
| N6 non-NQ session | 9,900 | 1,040 | 16 | 8,844 | 91 |
| Total | 68,874 | 13,244 | 451 | 55,179 | 393 |

Cell targets (6,000 / 5,000 / 6,000) are exceeded. Grammar, calendars and chance expectations are in PREREG_IDEAS50K.md section 10.

## Calendar provenance and completeness
- OFFICIAL (census calendar.csv): FOMC (30), CPI (44), NFP (43; file ends 2026-09-04), EIA (198).
- RULE-derived, not verified against published release dates: jobless claims, ISM manufacturing and services, Conference Board, opex (monthly and quarterly), equity roll Thursday, BCOM and GSCI roll days, month-end, quarter-end, first business day, pre/post CME holiday. The October 2026 month is incomplete and excluded from month-end.
- Not on disk and therefore not tested: retail sales, PPI, GDP, PCE, FOMC minutes, UMich, JOLTS, durable goods.

## Method
Reconciled NT8-faithful engine (market entry at the next open plus 1 tick, time exit, 1 tick/side plus $4.36). METHOD-2 harness with 12/3/3 tilt. Stage 0 is a vectorised pre-screen: keep a family only if OOS Sharpe > 0.25 and both halves are net positive. Survivors get a sign-flip family null (1000 reps), a bootstrap, and a beta check against the group instruments (beta > 0.15 invalidates the sign-flip null and would require a drift-matched null).

Fix made mid-run: instruments have different day axes (960 / 958 / 932 days). The assembler had used the last file's day axis, so the first scoring pass failed with shape errors. It now reindexes every cell to the union day axis, with zeros on missing days. Counts and hashes are unchanged. Rows were purged and re-registered.

## Results
- 393 families were pre-screened. Median OOS Sharpe was -0.79, which is what costs on unselected books look like. 377 were dropped at the pre-screen and still count toward F.
- 16 survivors were scored with the null. 2 passed gates a-d:
  - N2-ISM_S-RANGE-MET: Sharpe 1.35, null rank 0.995, boot_lo +0.10, halves 1.64 / 1.04, pair corr -0.01. It rests on the RULE-derived ISM services date (third business day), which is unverified.
  - N4-NR7-ENR-c570: Sharpe 1.31, null rank 0.983, boot_lo +0.03, halves 0.01 / 2.23. First half is flat and the bootstrap lower bound is marginal, so I treat it as weak.
- Gate a-d passes: N2 1 and N4 1 in the shared status script. N6 passes 0 against a chance expectation of about 4.6. N2 and N4 are far below their chance expectations (8.5 and 6.6).
- Best-of-F: neither passer reaches the best-of-F >= 0.95 level at F_eff = 594. Null ranks of 0.995 and 0.983 are nowhere near G^F. Neither survives the multiple-testing correction. Both are handed to PAPER-ALL as candidates only, because the directive says to feed any a-d passer.
- The beta check cleared both passers, so the sign-flip null is valid for them. A drift-matched null was not needed.

## Caveats
- RULE calendars are unverified.
- Fixed-side long/short cells carry directional exposure.
- The NFP calendar ends 2026-09-04.
- The sign-flip null is used only where the beta check passed.

Files: outputs/ideas50k/N2N4N6_results.csv, N2N4N6_counts.json, methods2/fam/N{2,4,6}-*.npz, code/census/night_ins/ap_n_*.py.

DONE N2N4N6
