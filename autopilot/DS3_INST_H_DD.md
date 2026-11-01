# DS3_INST_H_DD - INSTITUTIONAL section H, minute-of-day surface (bracket rescale, vol-of-minute lot scaling, wider brackets in high-vol minutes, minute-bucket skip, drift-minute books): re-read under DRAWDOWN FIRST (F1, overnight order, written 2026-10-31 23:59Z)

DATA. On disk: NQ 1-min and 1-s tables, minute-of-day x day-of-week grid (780 label days), walk-forward 6-month 30-min-forward-range surface. Cells: H3 4 minute-bucket skip filters; H4 12 vol-of-minute lot-scaling cells through the engine multiplier route (NEW); H2 6 bracket rescales and H5 4 wider-brackets-in-high-vol-minutes cells through the engine bracket route (Brackets re-plumbing of INST-H2, tie-out at s=1 max diff 0.0); H1 6 walk-forward drift-minute books as ADDITIVE sleeves (5 NQ contracts, 3-s delay, N basis). Surface months start 2023-08, so X-prime is scaled in 2023-08..2024-01 only.

**Prereg** `prereg/F1_INSTDD_prereg.md` sha256 `b177b68129c4bf2e492749bdf8ac98d8f1da9bac3c6c7dc4bc5957806d03ae98`; stage-1 selection `out/inst_dd/stage1_selection.json` sha256 `8ce67ccbbedfc6a5810d8ac8d1d8710a45b1b17084b618b4f17cb5854f802763` logged in DECISIONS.md before the recent look. Capped 20260206; UNTOUCHED never read. Frames: Sunday composite (headline) and as-is stack, live lots (K6 2 / P6 7 / U6 4 / H6 4-2 / M6 2 / A6 1), one-convention engine (dd_lib/lib3, unchanged).
**Coverage.** 32 cells swept in this group; 0 carried on PRE and X' (composite maxDD cut >= 20% in BOTH and mean not beyond -MDE in both); 0 distinct fire vectors; 0 looked at once in L3M/L6M/HOLD/ALL (cap 40 by min(PRE cut, X' cut)); 0 more carry in the as-is frame only (not looked at).
**Family-wise.** 32 cells swept; program placebo false-carry rate of the PRE+X' criterion for same-volume random skips/size-cuts in this group: 6/150 draws = 4.0% (15 sampled cells x 10 draws; mean volume cut 5%), i.e. about 1 chance carries expected of 32 swept vs 0 observed. Bonferroni placebo p = min(1, placebo rank p x distinct carried).

### Baselines (weekly $, label weeks; maxDD of the weekly cumulative)
| window | frame | mean $/wk | SD | maxDD | worst-20 | Calmar | mean/\|worst-20\| |
|---|---|---|---|---|---|---|---|
| L3M | Sunday composite | 34,406 | 44,702 | 21,361 | n/a (<20 loss wks) | 1.611 | nan |
| L3M | as-is stack | 12,153 | 45,510 | 88,039 | n/a (<20 loss wks) | 0.138 | nan |
| L6M | Sunday composite | 41,137 | 42,743 | 22,892 | n/a (<20 loss wks) | 1.797 | nan |
| L6M | as-is stack | 21,715 | 43,891 | 88,039 | n/a (<20 loss wks) | 0.247 | nan |
| HOLD | Sunday composite | 38,574 | 51,791 | 96,995 | n/a (<20 loss wks) | 0.398 | nan |
| HOLD | as-is stack | 21,874 | 53,850 | 144,173 | n/a (<20 loss wks) | 0.152 | nan |
| PRE | Sunday composite | 23,095 | 55,723 | 241,199 | -875,191 | 0.096 | 0.0264 |
| PRE | as-is stack | 18,612 | 50,445 | 161,956 | -810,578 | 0.115 | 0.0230 |
| X' | Sunday composite | 7,955 | 32,632 | 120,500 | -419,642 | 0.066 | 0.0190 |
| X' | as-is stack | -3,410 | 28,974 | 316,507 | -572,111 | -0.011 | -0.0060 |
| ALL | Sunday composite | 22,258 | 50,318 | 241,199 | -1,098,057 | 0.092 | 0.0203 |
| ALL | as-is stack | 13,060 | 47,240 | 316,507 | -1,161,104 | 0.041 | 0.0112 |

### Nothing carried: the best cells on the selection windows only (PRE, X-prime; no recent window opened for them)

| cell | action | vol cut | composite maxDD cut PRE | X' | mean change PRE (MDE) | X' (MDE) | as-is cut PRE | X' |
|---|---|---|---|---|---|---|---|---|
| h2_rescale|what=stop|gamma=1.0 | brk | -2% | +14% | +0% | -8,491 (12,620) | -2,250 (6,804) | -36% | +22% |
| h2_rescale|what=stop|gamma=0.5 | brk | -2% | +5% | +0% | -732 (8,529) | -2,803 (5,912) | -47% | +9% |
| h5_wider_highvol|what=both|gamma=1.0 | brk | +7% | +3% | +0% | -1,866 (9,456) | 3,556 (6,595) | +27% | +1% |
| h3_bucket_wf_skip|bucket=30|scope=book | skip | +10% | +4% | +0% | -2,512 (5,937) | -2,729 (6,085) | -24% | -2% |
| h3_bucket_wf_skip|bucket=15|scope=pooled | skip | +15% | +19% | +0% | -5,269 (9,685) | -3,649 (8,024) | +4% | +3% |
| h3_bucket_wf_skip|bucket=30|scope=pooled | skip | +23% | +48% | +0% | -3,949 (11,124) | -7,127 (7,793) | +18% | +0% |
| h4_cutonly|g=0.5|ALL6 | mult | +5% | +10% | +0% | -2,604 (2,631) | -1,563 (2,406) | -1% | -3% |
| h1_drift_wf|h=30|var=B | add | +0% | +2% | +0% | -20 (1,156) | -24 (695) | +3% | +0% |

### Reading

H (minute-of-day surface): 32 cells swept, 0 cut the composite maxDD >= 20% in BOTH PRE and X-prime with the mean inside its MDE; none carried, so no recent window was opened and nothing is RISK-KEEP.

H1 drift-minute books were priced as ADDITIVE sleeves (5 NQ contracts); none cuts the composite maxDD >= 20% in both selection windows. Brackets (H2 rescale, H5 wider in high-vol minutes) and lot scaling (H4) do not cut the maxDD either; the table above lists the best by selection-window cut.

### All 32 H cells on the selection windows only (composite frame; PRE, X-prime)

| cell | PRE maxDD cut | X' cut | mean change PRE (MDE) | X' (MDE) | as-is PRE / X' cut |
|---|---|---|---|---|---|
| h2_rescale|what=stop|gamma=1.0 | +14% | +0% | -8,491 (12,620) | -2,250 (6,804) | -36% / +22% |
| h2_rescale|what=stop|gamma=0.5 | +5% | +0% | -732 (8,529) | -2,803 (5,912) | -47% / +9% |
| h5_wider_highvol|what=both|gamma=1.0 | +3% | +0% | -1,866 (9,456) | 3,556 (6,595) | +27% / +1% |
| h3_bucket_wf_skip|bucket=30|scope=book | +4% | +0% | -2,512 (5,937) | -2,729 (6,085) | -24% / -2% |
| h3_bucket_wf_skip|bucket=15|scope=pooled | +19% | +0% | -5,269 (9,685) | -3,649 (8,024) | +4% / +3% |
| h3_bucket_wf_skip|bucket=30|scope=pooled | +48% | +0% | -3,949 (11,124) | -7,127 (7,793) | +18% / +0% |
| h4_cutonly|g=0.5|ALL6 | +10% | +0% | -2,604 (2,631) | -1,563 (2,406) | -1% / -3% |
| h1_drift_wf|h=30|var=B | +2% | +0% | -20 (1,156) | -24 (695) | +3% / +0% |
| h1_drift_wf|h=15|var=B | +2% | +0% | 1,085 (1,939) | 226 (994) | +2% / +5% |
| h1_drift_wf|h=30|var=A | +0% | +0% | -43 (299) | 378 (1,243) | +0% / +1% |
| h1_drift_wf|h=15|var=A | +0% | +0% | -124 (798) | 95 (988) | +0% / +1% |
| h4_cutonly|g=1.0|HM | +4% | +0% | -137 (701) | -23 (569) | +1% / +1% |
| h4_cutonly|g=1.0|SM | +1% | +0% | 67 (146) | -27 (77) | +1% / -0% |
| h4_cutonly|g=1.0|PE | +20% | +0% | -1,913 (2,897) | -1,690 (2,944) | +0% / -1% |
| h4_skiptop|q=0.8|ALL6 | +16% | +0% | -6,871 (8,017) | -1,892 (7,407) | -0% / -3% |
| h4_skiptop|q=0.9|ALL6 | +4% | +0% | -3,649 (5,222) | -3,718 (5,890) | -32% / -20% |
| h4_cutonly|g=1.0|ALL6 | +21% | +0% | -3,298 (3,967) | -1,805 (3,880) | +5% / -5% |
| h2_rescale|what=target|gamma=0.5 | +19% | +0% | -4,306 (10,542) | -583 (7,888) | -20% / -2% |
| h5_wider_highvol|what=both|gamma=0.5 | +2% | +0% | -2,151 (6,157) | 2,443 (6,359) | +13% / +1% |
| h4_cutonly|g=1.0|PB | +0% | +0% | 0 (0) | 0 (0) | +0% / +0% |
| h3_bucket_wf_skip|bucket=15|scope=book | +3% | +0% | -2,299 (4,953) | -1,451 (4,563) | +1% / +1% |
| h4_cutonly|g=1.0|KB | -1% | +0% | -672 (745) | -119 (725) | +4% / -1% |
| h4_invvol|g=0.5|ALL6 | +15% | -2% | 2,612 (8,783) | 1,489 (7,495) | -55% / -13% |
| h1_drift_wf|h=5|var=A | -2% | +0% | -194 (1,321) | 161 (831) | -3% / +2% |
| h4_cutonly|g=1.0|MV | -2% | +0% | -643 (903) | 54 (682) | -6% / +3% |
| h1_drift_wf|h=5|var=B | -3% | +0% | -328 (982) | -600 (1,299) | -8% / -6% |
| h2_rescale|what=target|gamma=1.0 | -5% | +0% | -5,644 (12,719) | -1,871 (9,929) | +19% / -9% |
| h5_wider_highvol|what=stop|gamma=0.5 | -14% | +0% | -1,013 (3,847) | 863 (4,610) | -14% / +8% |
| h4_invvol|g=1.0|ALL6 | -21% | -11% | 4,200 (13,175) | 3,189 (11,347) | -8% / -44% |
| h5_wider_highvol|what=stop|gamma=1.0 | -30% | +0% | -2,281 (5,532) | 493 (5,568) | -20% / +2% |
| h2_rescale|what=both|gamma=0.5 | -28% | -32% | -7,486 (13,101) | -4,128 (10,204) | -29% / -2% |
| h2_rescale|what=both|gamma=1.0 | -130% | +0% | -15,722 (18,543) | -2,480 (9,734) | -94% / +6% |

### Notes
- Counts: STRICT/TOLERANT(literal)/NOW-ONLY over the looked cells: see Reading; TOL-B and TOL-nc are post-hoc, beside.
- dead_lookup (run before scoring): every cell here exists in the ledger under INST_D 1,044 / INST_E 396 / INST3C 701 / INST3F 134 / INSTG 36 / INST_H 16 (scored on the mean, 'EXACT' by name); this program re-prices them on drawdown. The new H4 (12) and H5 (4) cells and the engine-route H2 bracket rows have 0 hits. Appended after scoring with append_cells (program F1DD, tier PRICED), never rebuilt.
- Coverage gaps (not stack rules, not re-priced here): 8 NQ/ES pair-book cells (C), 24 close-window class books (F; C1 builds the close-fade sleeve), the stored INST-D/E s2 series (neighbours, shifted-state and random placebos, not scored cells).
- Single-week caveat: the composite L6M maxDD (22.9k) is one week (2026-01-19); the as-is L6M maxDD is the same week. L3M/L6M/HOLD have fewer than 20 losing weeks, so worst-20 is shown for PRE, X-prime, ALL only.
- Deviation from the prereg count: H4 has 12 cells, not 14 (counting error); swept total 2,311.
- Top-N by in-sample drawdown (the 40 cap in C) is post-hoc; nothing promoted; Shadow only.
- Code l2vast/ds3/code/inst_dd/, results l2vast/ds3/out/inst_dd/ (stage1_table.csv, stage2a_table.csv, final_rows.csv, summary.json), rows out/recent_wins/inst_dd.csv.
