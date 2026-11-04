
## DIS-BQ (S4a, 2026-11-04 23:15Z): pre-2023 OUT-OF-SAMPLE of the DIS-B candidates on the owned 1-min NQ history 2013-01..2023-04-02 (prereg autopilot/DIS_BQ_PREREG.md sha256 5af1f45bf097a1614a59cef027817fcddc81b43d4a62951e15fb09b6a261a890; ledger DIS_BQ; $0; research only, no PASS claims)
Protocol = DIS-W (ZL-1): 1-min live fill model on the extended feed (stop-first, 2.45 / 0.80 / 0.242), calibration vs the 1-s harness in 2023-04..2026-10 first (weekly $ correlation >= 0.90 else NO VERDICT), four causal placebos x 100 (P1 side, P2 delay, P3 weekday day, P4 shift5), family max-T over the 157 cells, BH q on the largest placebo p. Verdict rules fixed before the run: SURVIVES = calibrated, OOS mean > 0, q <= 0.10; WEAK = mean > 0 and all four raw p <= 0.10 but q > 0.10; NEGATIVE/NULL; NO VERDICT.
**Headline: of the 14 cells with 1-s placebo p <= 0.10, {'NO VERDICT': 7} (the two already tested elsewhere, P_REL_cont and N_REL_rev, excluded from this tally; 12 of the 157 cells are theirs). All 157 cells: {'NO VERDICT': 127, 'NEGATIVE/NULL': 30}.**
Calibration: 30 of 157 cells reach weekly correlation >= 0.90 between the 1-min pipeline and the 1-s harness (median 0.86).
### The 14 headline cells (1-s placebo p <= 0.10)
| fam                   | shape         |   p1s |   corr |    n |   mean |      t | posy   |   usd_wk |    p1 |    p2 |   p3 |   p4 |   pmaxT1 |   q | verdict       |
|:----------------------|:--------------|------:|-------:|-----:|-------:|-------:|:-------|---------:|------:|------:|-----:|-----:|---------:|----:|:--------------|
| N_REL_rev_m0.5        | mid/1.00/120m | 0.01  |  0.857 |  695 | -1.021 | -0.983 | 1/11   | -304.678 | 0.267 | 0.198 |    1 |    1 |    1     |   1 | NO VERDICT    |
| N_REL_rev_m0.5        | mid/1.00/60m  | 0.01  |  0.862 |  695 | -1.18  | -1.192 | 1/11   | -309.077 | 0.228 | 0.248 |    1 |    1 |    1     |   1 | NO VERDICT    |
| P_REL_cont_m1.0       | r1/1.00/30m   | 0.059 |  0.928 |  809 | -1.343 | -2.467 | 2/11   | -339.085 | 0.406 | 0.396 |    1 |    1 |    1     |   1 | NEGATIVE/NULL |
| N_GAPFILL_t31_g1.0_hi | mid/1.00/60m  | 0.069 |  0.874 |  630 |  1.089 |  0.926 | 6/10   |   69.981 | 0.02  | 0.01  |    1 |    1 |    0.376 |   1 | NO VERDICT    |
| P_REL_cont_m1.0       | r2/1.00/30m   | 0.069 |  0.908 |  809 | -1.074 | -1.532 | 3/11   | -327.496 | 0.257 | 0.099 |    1 |    1 |    1     |   1 | NEGATIVE/NULL |
| N_GAPFILL_t31_g1.0_hi | mid/1.00/120m | 0.069 |  0.858 |  630 |  1.263 |  1.022 | 6/10   |   74.683 | 0.02  | 0.04  |    1 |    1 |    0.277 |   1 | NO VERDICT    |
| N_IMB_rev_th0.1       | mid/0.25/120m | 0.089 |  0.88  |  545 | -0.521 | -0.656 | 2/11   | -140.951 | 0.02  | 0.03  |    1 |    1 |    1     |   1 | NO VERDICT    |
| N_REL_rev_m0.5        | r1/1.00/120m  | 0.099 |  0.885 | 1388 | -1.108 | -1.985 | 2/11   | -397.693 | 0.287 | 0.317 |    1 |    1 |    1     |   1 | NO VERDICT    |
| N_IMB_rev_th0.1       | mid/0.25/60m  | 0.099 |  0.878 |  545 | -0.665 | -0.912 | 2/11   | -143.62  | 0.03  | 0.04  |    1 |    1 |    1     |   1 | NO VERDICT    |
| N_REL_rev_m0.5        | r1/1.00/30m   | 0.099 |  0.886 | 1388 | -1.279 | -2.28  | 2/11   | -410.429 | 0.337 | 0.347 |    1 |    1 |    1     |   1 | NO VERDICT    |
| N_REL_rev_m0.5        | r1/1.00/60m   | 0.099 |  0.885 | 1388 | -1.211 | -2.172 | 2/11   | -410.791 | 0.238 | 0.356 |    1 |    1 |    1     |   1 | NO VERDICT    |
| N_IMB_rev_th0.1       | mid/0.25/30m  | 0.099 |  0.869 |  545 | -0.997 | -1.453 | 2/11   | -186.815 | 0.01  | 0.059 |    1 |    1 |    1     |   1 | NO VERDICT    |
| N_GAPFILL_t31_g0.5_hi | mid/1.00/60m  | 0.099 |  0.874 |  657 |  1.102 |  0.972 | 6/11   |   77     | 0.03  | 0.01  |    1 |    1 |    0.366 |   1 | NO VERDICT    |
| N_GAPFILL_t31_g0.5_hi | mid/1.00/120m | 0.099 |  0.858 |  657 |  1.269 |  1.065 | 5/11   |   81.586 | 0.02  | 0.03  |    1 |    1 |    0.257 |   1 | NO VERDICT    |
### Calibrated cells with the best OOS mean (top 15 of the 157)
| fam                   | shape          |   p1s |   corr |    n |   mean |      t | posy   |   usd_wk |    p1 |    p2 |   p3 |   p4 |   pmaxT1 |   q | verdict       |
|:----------------------|:---------------|------:|-------:|-----:|-------:|-------:|:-------|---------:|------:|------:|-----:|-----:|---------:|----:|:--------------|
| N_GAPFILL_t35_g0.5_hi | mid/1.00/120m  | 0.891 |  0.919 |  498 |  0.675 |  0.437 | 5/11   |  -60.559 | 0.119 | 0.05  |    1 |    1 |    0.604 |   1 | NEGATIVE/NULL |
| N_GAPFILL_t35_g1.0_hi | mid/1.00/120m  | 0.802 |  0.912 |  465 |  0.422 |  0.269 | 5/10   |  -80.347 | 0.208 | 0.069 |    1 |    1 |    0.782 |   1 | NEGATIVE/NULL |
| N_GAPFILL_t35_g0.5_hi | mid/1.00/60m   | 0.891 |  0.909 |  498 | -0.039 | -0.028 | 4/11   | -140.101 | 0.188 | 0.149 |    1 |    1 |    0.99  |   1 | NEGATIVE/NULL |
| N_GAPFILL_t35_g1.0_hi | mid/1.00/60m   | 0.802 |  0.901 |  465 | -0.372 | -0.26  | 4/10   | -168.693 | 0.248 | 0.218 |    1 |    1 |    1     |   1 | NEGATIVE/NULL |
| P_PO_fade             | r1/1.00/30m    | 0.327 |  0.944 |  762 | -0.778 | -3.273 | 2/11   | -152.531 | 0.079 | 0.356 |    1 |    1 |    1     |   1 | NEGATIVE/NULL |
| P_PO_fade             | r1/1.00/120m   | 0.327 |  0.944 |  762 | -0.778 | -3.273 | 2/11   | -152.531 | 0.05  | 0.347 |    1 |    1 |    1     |   1 | NEGATIVE/NULL |
| P_PO_fade             | r1/1.00/60m    | 0.327 |  0.944 |  762 | -0.778 | -3.273 | 2/11   | -152.531 | 0.069 | 0.327 |    1 |    1 |    1     |   1 | NEGATIVE/NULL |
| N_RCL_W10             | vwap/1.00/120m | 0.178 |  0.947 | 1452 | -0.861 | -1.148 | 4/11   | -395.368 | 0.198 | 0.297 |    1 |    1 |    1     |   1 | NEGATIVE/NULL |
| P_PO_fade             | r1/0.25/120m   | 0.505 |  0.9   |  762 | -0.934 | -4.22  | 2/11   | -196.212 | 0.05  | 0.267 |    1 |    1 |    1     |   1 | NEGATIVE/NULL |
| P_PO_fade             | r1/0.25/30m    | 0.505 |  0.9   |  762 | -0.934 | -4.22  | 2/11   | -196.212 | 0.059 | 0.327 |    1 |    1 |    1     |   1 | NEGATIVE/NULL |
| P_PO_fade             | r1/0.25/60m    | 0.505 |  0.9   |  762 | -0.934 | -4.22  | 2/11   | -196.212 | 0.089 | 0.327 |    1 |    1 |    1     |   1 | NEGATIVE/NULL |
| N_PO_fade             | r1/0.25/120m   | 0.822 |  0.913 | 2268 | -0.957 | -2.128 | 2/11   | -460.29  | 0.069 | 0.238 |    1 |    1 |    1     |   1 | NEGATIVE/NULL |
| N_PO_fade             | r1/0.25/60m    | 0.802 |  0.913 | 2268 | -0.982 | -2.189 | 2/11   | -468.016 | 0.119 | 0.208 |    1 |    1 |    1     |   1 | NEGATIVE/NULL |
| P_REL_cont_m1.0       | r2/1.00/30m    | 0.069 |  0.908 |  809 | -1.074 | -1.532 | 3/11   | -327.496 | 0.257 | 0.099 |    1 |    1 |    1     |   1 | NEGATIVE/NULL |
| N_PO_fade             | r1/0.25/30m    | 0.842 |  0.917 | 2268 | -1.091 | -2.516 | 2/11   | -502.745 | 0.228 | 0.327 |    1 |    1 |    1     |   1 | NEGATIVE/NULL |
### Counts
OOS mean > 0: 21 of 157; OOS mean > 0 and calibrated: 2; q <= 0.10: 0; family max-T p (P1) <= 0.10: 0.

**SUPERSEDED: the DIS-BQ block above (23:15Z) was produced with a unit bug in the P3/P4 day-shift placebos (p = 1.00 artefact); P1/P2, calibration and the OOS means were unaffected. The corrected block follows.**

## DIS-BQ (S4a, 2026-11-04 23:18Z): pre-2023 OUT-OF-SAMPLE of the DIS-B candidates on the owned 1-min NQ history 2013-01..2023-04-02 (prereg autopilot/DIS_BQ_PREREG.md sha256 5af1f45bf097a1614a59cef027817fcddc81b43d4a62951e15fb09b6a261a890; ledger DIS_BQ; $0; research only, no PASS claims)
Protocol = DIS-W (ZL-1): 1-min live fill model on the extended feed (stop-first, 2.45 / 0.80 / 0.242), calibration vs the 1-s harness in 2023-04..2026-10 first (weekly $ correlation >= 0.90 else NO VERDICT), four causal placebos x 100 (P1 side, P2 delay, P3 weekday day, P4 shift5), family max-T over the 157 cells, BH q on the largest placebo p. Verdict rules fixed before the run: SURVIVES = calibrated, OOS mean > 0, q <= 0.10; WEAK = mean > 0 and all four raw p <= 0.10 but q > 0.10; NEGATIVE/NULL; NO VERDICT.
**Headline: of the 14 cells with 1-s placebo p <= 0.10, {'NO VERDICT': 7} (the two already tested elsewhere, P_REL_cont and N_REL_rev, excluded from this tally; 12 of the 157 cells are theirs). All 157 cells: {'NO VERDICT': 127, 'NEGATIVE/NULL': 30}.**
Calibration: 30 of 157 cells reach weekly correlation >= 0.90 between the 1-min pipeline and the 1-s harness (median 0.86).
### The 14 headline cells (1-s placebo p <= 0.10)
| fam                   | shape         |   p1s |   corr |    n |   mean |      t | posy   |   usd_wk |    p1 |    p2 |    p3 |    p4 |   pmaxT1 |     q | verdict       |
|:----------------------|:--------------|------:|-------:|-----:|-------:|-------:|:-------|---------:|------:|------:|------:|------:|---------:|------:|:--------------|
| N_REL_rev_m0.5        | mid/1.00/120m | 0.01  |  0.857 |  695 | -1.021 | -0.983 | 1/11   | -304.678 | 0.267 | 0.198 | 0.139 | 0.248 |    1     | 0.636 | NO VERDICT    |
| N_REL_rev_m0.5        | mid/1.00/60m  | 0.01  |  0.862 |  695 | -1.18  | -1.192 | 1/11   | -309.077 | 0.228 | 0.248 | 0.109 | 0.287 |    1     | 0.673 | NO VERDICT    |
| P_REL_cont_m1.0       | r1/1.00/30m   | 0.059 |  0.928 |  809 | -1.343 | -2.467 | 2/11   | -339.085 | 0.406 | 0.396 | 0.287 | 0.485 |    1     | 0.846 | NEGATIVE/NULL |
| N_GAPFILL_t31_g1.0_hi | mid/1.00/60m  | 0.069 |  0.874 |  630 |  1.089 |  0.926 | 6/10   |   69.981 | 0.02  | 0.01  | 0.01  | 0.01  |    0.376 | 0.097 | NO VERDICT    |
| P_REL_cont_m1.0       | r2/1.00/30m   | 0.069 |  0.908 |  809 | -1.074 | -1.532 | 3/11   | -327.496 | 0.257 | 0.099 | 0.079 | 0.109 |    1     | 0.631 | NEGATIVE/NULL |
| N_GAPFILL_t31_g1.0_hi | mid/1.00/120m | 0.069 |  0.858 |  630 |  1.263 |  1.022 | 6/10   |   74.683 | 0.02  | 0.04  | 0.01  | 0.01  |    0.277 | 0.159 | NO VERDICT    |
| N_IMB_rev_th0.1       | mid/0.25/120m | 0.089 |  0.88  |  545 | -0.521 | -0.656 | 2/11   | -140.951 | 0.02  | 0.03  | 0.03  | 0.059 |    1     | 0.227 | NO VERDICT    |
| N_REL_rev_m0.5        | r1/1.00/120m  | 0.099 |  0.885 | 1388 | -1.108 | -1.985 | 2/11   | -397.693 | 0.287 | 0.317 | 0.02  | 0.218 |    1     | 0.675 | NO VERDICT    |
| N_IMB_rev_th0.1       | mid/0.25/60m  | 0.099 |  0.878 |  545 | -0.665 | -0.912 | 2/11   | -143.62  | 0.03  | 0.04  | 0.02  | 0.079 |    1     | 0.296 | NO VERDICT    |
| N_REL_rev_m0.5        | r1/1.00/30m   | 0.099 |  0.886 | 1388 | -1.279 | -2.28  | 2/11   | -410.429 | 0.337 | 0.347 | 0.05  | 0.248 |    1     | 0.68  | NO VERDICT    |
| N_REL_rev_m0.5        | r1/1.00/60m   | 0.099 |  0.885 | 1388 | -1.211 | -2.172 | 2/11   | -410.791 | 0.238 | 0.356 | 0.02  | 0.287 |    1     | 0.682 | NO VERDICT    |
| N_IMB_rev_th0.1       | mid/0.25/30m  | 0.099 |  0.869 |  545 | -0.997 | -1.453 | 2/11   | -186.815 | 0.01  | 0.059 | 0.059 | 0.158 |    1     | 0.478 | NO VERDICT    |
| N_GAPFILL_t31_g0.5_hi | mid/1.00/60m  | 0.099 |  0.874 |  657 |  1.102 |  0.972 | 6/11   |   77     | 0.03  | 0.01  | 0.01  | 0.01  |    0.366 | 0.123 | NO VERDICT    |
| N_GAPFILL_t31_g0.5_hi | mid/1.00/120m | 0.099 |  0.858 |  657 |  1.269 |  1.065 | 5/11   |   81.586 | 0.02  | 0.03  | 0.01  | 0.01  |    0.257 | 0.123 | NO VERDICT    |
### Calibrated cells with the best OOS mean (top 15 of the 157)
| fam                   | shape          |   p1s |   corr |    n |   mean |      t | posy   |   usd_wk |    p1 |    p2 |    p3 |    p4 |   pmaxT1 |     q | verdict       |
|:----------------------|:---------------|------:|-------:|-----:|-------:|-------:|:-------|---------:|------:|------:|------:|------:|---------:|------:|:--------------|
| N_GAPFILL_t35_g0.5_hi | mid/1.00/120m  | 0.891 |  0.919 |  498 |  0.675 |  0.437 | 5/11   |  -60.559 | 0.119 | 0.05  | 0.02  | 0.05  |    0.604 | 0.389 | NEGATIVE/NULL |
| N_GAPFILL_t35_g1.0_hi | mid/1.00/120m  | 0.802 |  0.912 |  465 |  0.422 |  0.269 | 5/10   |  -80.347 | 0.208 | 0.069 | 0.01  | 0.05  |    0.782 | 0.583 | NEGATIVE/NULL |
| N_GAPFILL_t35_g0.5_hi | mid/1.00/60m   | 0.891 |  0.909 |  498 | -0.039 | -0.028 | 4/11   | -140.101 | 0.188 | 0.149 | 0.05  | 0.119 |    0.99  | 0.547 | NEGATIVE/NULL |
| N_GAPFILL_t35_g1.0_hi | mid/1.00/60m   | 0.802 |  0.901 |  465 | -0.372 | -0.26  | 4/10   | -168.693 | 0.248 | 0.218 | 0.109 | 0.218 |    1     | 0.627 | NEGATIVE/NULL |
| P_PO_fade             | r1/1.00/30m    | 0.327 |  0.944 |  762 | -0.778 | -3.273 | 2/11   | -152.531 | 0.079 | 0.356 | 0.02  | 0.05  |    1     | 0.682 | NEGATIVE/NULL |
| P_PO_fade             | r1/1.00/120m   | 0.327 |  0.944 |  762 | -0.778 | -3.273 | 2/11   | -152.531 | 0.05  | 0.347 | 0.01  | 0.119 |    1     | 0.68  | NEGATIVE/NULL |
| P_PO_fade             | r1/1.00/60m    | 0.327 |  0.944 |  762 | -0.778 | -3.273 | 2/11   | -152.531 | 0.069 | 0.327 | 0.02  | 0.079 |    1     | 0.675 | NEGATIVE/NULL |
| N_RCL_W10             | vwap/1.00/120m | 0.178 |  0.947 | 1452 | -0.861 | -1.148 | 4/11   | -395.368 | 0.198 | 0.297 | 0.069 | 0.396 |    1     | 0.732 | NEGATIVE/NULL |
| P_PO_fade             | r1/0.25/120m   | 0.505 |  0.9   |  762 | -0.934 | -4.22  | 2/11   | -196.212 | 0.05  | 0.267 | 0.01  | 0.059 |    1     | 0.636 | NEGATIVE/NULL |
| P_PO_fade             | r1/0.25/30m    | 0.505 |  0.9   |  762 | -0.934 | -4.22  | 2/11   | -196.212 | 0.059 | 0.327 | 0.01  | 0.05  |    1     | 0.675 | NEGATIVE/NULL |
| P_PO_fade             | r1/0.25/60m    | 0.505 |  0.9   |  762 | -0.934 | -4.22  | 2/11   | -196.212 | 0.089 | 0.327 | 0.01  | 0.059 |    1     | 0.675 | NEGATIVE/NULL |
| N_PO_fade             | r1/0.25/120m   | 0.822 |  0.913 | 2268 | -0.957 | -2.128 | 2/11   | -460.29  | 0.069 | 0.238 | 0.02  | 0.188 |    1     | 0.612 | NEGATIVE/NULL |
| N_PO_fade             | r1/0.25/60m    | 0.802 |  0.913 | 2268 | -0.982 | -2.189 | 2/11   | -468.016 | 0.119 | 0.208 | 0.01  | 0.208 |    1     | 0.583 | NEGATIVE/NULL |
| P_REL_cont_m1.0       | r2/1.00/30m    | 0.069 |  0.908 |  809 | -1.074 | -1.532 | 3/11   | -327.496 | 0.257 | 0.099 | 0.079 | 0.109 |    1     | 0.631 | NEGATIVE/NULL |
| N_PO_fade             | r1/0.25/30m    | 0.842 |  0.917 | 2268 | -1.091 | -2.516 | 2/11   | -502.745 | 0.228 | 0.327 | 0.02  | 0.257 |    1     | 0.675 | NEGATIVE/NULL |
### Counts
OOS mean > 0: 21 of 157; OOS mean > 0 and calibrated: 2; q <= 0.10: 32; family max-T p (P1) <= 0.10: 0.
### Reading (S4a, DIS-BQ final; post-hoc, research only)
1. **Verdict tally (prereg rules): SURVIVES 0, WEAK 0, NEGATIVE/NULL 30, NO VERDICT 127 of 157.** Only 30 of 157 cells meet the calibration rule (weekly correlation of the 1-min pipeline with the 1-s harness >= 0.90; median 0.86): the pre-market entries and the NY-AM gap/fade cells depend on the first seconds after the signal, which 1-minute bars approximate poorly. Of the 14 cells with 1-s placebo p <= 0.10: 7 are P_REL_cont / N_REL_rev cells (tested by ZL-1 and BASE-4; P_REL_cont is NEGATIVE here again, -1.1 to -1.3 pt per trade; N_REL_rev is negative -1.0 to -1.2, uncalibrated), and the other 7, all N_GAPFILL (gap fill after a high-pre-market-volume day), are NO VERDICT because their calibration correlation is 0.86-0.87.
2. **Descriptive only (no verdict by rule): the high-PM-volume gap-fill family is the one thing that does not look like the 2026 artefact.** N_GAPFILL_t31 with relvol >= 1 (g 0.5 and 1.0), 1.0 ATR stop, R1 or PM-mid target: OOS mean +0.8 to +1.3 pt per trade (n 630-1,146), 5-6 of 10-11 years positive, week-cluster t only 0.9-1.8, placebo p <= 0.02 on all four placebos (P1-P4), family max-T p (P1) 0.38 and BH q 0.056-0.097. The 16 no-verdict cells with positive OOS mean and q <= 0.10 are all this family (plus two near-zero PMV_rev cells). Calibration weekly correlation 0.82-0.87 (< 0.90), so by the preregistered rule it cannot be called a replication; t_week < 2 and the family max-T p of 0.38 say the OOS evidence is weak even before the calibration question. It is a candidate for a 1-s check if the user buys ohlcv-1s for 2021-2023 (ZL-1's estimate: $97 for 2021-01-01..2023-02-09), not before.
3. **No DIS-B pre-market-entry (P family) cell replicates**: every calibrated P cell is negative or null before 2023.
Files: /mnt/l2/l2vast/ds3_disbq/disbq_table.csv (157 rows), code l2vast/ds3/code/disb/disbq_*.py, ledger DIS_BQ (157 cells).
