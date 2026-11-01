# DS3_INST_G_DD - INSTITUTIONAL section G, order-flow toxicity sizer (VPIN, cancel ratio, OFI, trade-to-book, hidden rate): re-read under DRAWDOWN FIRST (F1, overnight order, written 2026-11-01 00:00Z)

DATA. On disk: mbp-10 10-s buckets; features VPIN-50, cancel ratio, multi-level OFI, trade-to-book, hidden-liquidity rate at the signal second. 36 cells (6 features x 2 quantiles x S1 half / S2 skip / S3 half+x1.5), composite series tie to the stored stageA_all.pkl.

**Prereg** `prereg/F1_INSTDD_prereg.md` sha256 `b177b68129c4bf2e492749bdf8ac98d8f1da9bac3c6c7dc4bc5957806d03ae98`; stage-1 selection `out/inst_dd/stage1_selection.json` sha256 `8ce67ccbbedfc6a5810d8ac8d1d8710a45b1b17084b618b4f17cb5854f802763` logged in DECISIONS.md before the recent look. Capped 20260206; UNTOUCHED never read. Frames: Sunday composite (headline) and as-is stack, live lots (K6 2 / P6 7 / U6 4 / H6 4-2 / M6 2 / A6 1), one-convention engine (dd_lib/lib3, unchanged).
**Coverage.** 36 cells swept in this group; 8 carried on PRE and X' (composite maxDD cut >= 20% in BOTH and mean not beyond -MDE in both); 8 distinct fire vectors; 8 looked at once in L3M/L6M/HOLD/ALL (cap 40 by min(PRE cut, X' cut)); 1 more carry in the as-is frame only (not looked at).
**Family-wise.** 36 cells swept; program placebo false-carry rate of the PRE+X' criterion for same-volume random skips/size-cuts in this group: 13/200 draws = 6.5% (20 sampled cells x 10 draws; mean volume cut 7%), i.e. about 2 chance carries expected of 36 swept vs 8 observed. Bonferroni placebo p = min(1, placebo rank p x distinct carried).

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

### Table 1. Risk at live lots, composite frame, recent-first (maxDD cut = 1 - after/before; negative = deeper)

| cell | session mix of affected live signals | affected live | L3M cut | L6M maxDD before > after (cut) | HOLD cut | PRE cut | X' cut | ALL cut | worst-20 PRE b>a | X' b>a | ALL b>a | SD L6M b>a | Calmar L6M b>a | as-is L6M cut / PRE / X' |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G|T|q0.8|S1 | asia 48%, nyam 25%, london 20% | 8092 | -129% | 22,892 > 40,086 (-75%) | +51% | +41% | +30% | +41% | -875,191 > -783,245 | -419,642 > -421,943 | -1,098,057 > -990,293 | 42,743 > 41,222 | 1.80 > 0.70 | -1% / +20% / +37% |
| G|V|q0.8|S1 | asia 48%, nyam 28%, london 18% | 4930 | -155% | 22,892 > 54,385 (-138%) | +4% | +34% | +23% | +34% | -875,191 > -796,355 | -419,642 > -364,695 | -1,098,057 > -1,025,929 | 42,743 > 41,191 | 1.80 > 0.62 | +16% / +29% / +29% |
| G|H|q0.9|S2 | asia 53%, nyam 24%, london 19% | 2136 | -199% | 22,892 > 63,896 (-179%) | +22% | +38% | +26% | +38% | -875,191 > -815,307 | -419,642 > -429,568 | -1,098,057 > -1,084,137 | 42,743 > 39,230 | 1.80 > 0.56 | -32% / +14% / +15% |
| G|H|q0.8|S2 | asia 51%, nyam 25%, london 19% | 4402 | -200% | 22,892 > 64,189 (-180%) | +34% | +31% | +36% | +31% | -875,191 > -766,738 | -419,642 > -387,309 | -1,098,057 > -981,645 | 42,743 > 42,983 | 1.80 > 0.51 | +5% / +21% / +31% |
| G|T|q0.9|S1 | asia 49%, nyam 24%, london 21% | 5063 | -245% | 22,892 > 73,779 (-222%) | +24% | +34% | +21% | +34% | -875,191 > -815,521 | -419,642 > -417,306 | -1,098,057 > -1,082,536 | 42,743 > 45,043 | 1.80 > 0.39 | +16% / +15% / +12% |
| G|T|q0.9|S3 | asia 48%, nyam 25%, london 21% | 5591 | -250% | 22,892 > 74,831 (-227%) | +23% | +37% | +26% | +37% | -875,191 > -809,910 | -419,642 > -478,766 | -1,098,057 > -1,092,082 | 42,743 > 47,070 | 1.80 > 0.40 | +16% / +15% / +14% |
| G|T|q0.9|S2 | asia 49%, nyam 24%, london 21% | 5063 | -280% | 22,892 > 81,221 (-255%) | +16% | +38% | +44% | +38% | -875,191 > -870,201 | -419,642 > -407,502 | -1,098,057 > -1,171,705 | 42,743 > 49,197 | 1.80 > 0.28 | +19% / +36% / +28% |
| G|T|q0.8|S2 | asia 48%, nyam 25%, london 20% | 8092 | -448% | 22,892 > 115,289 (-404%) | -19% | +32% | +27% | +32% | -875,191 > -758,285 | -419,642 > -472,748 | -1,098,057 > -1,063,033 | 42,743 > 45,037 | 1.80 > 0.16 | -24% / +9% / +52% |

### Table 2. Mean (MDE), equal-risk, placebo, gates, label ($/wk stack change vs the Sunday composite; MDE = 2.8 x SE of the paired weekly delta)

| cell | mean L3M | L6M (MDE) | HOLD | PRE | X' | ALL | equal-risk mean change L6M (c) | PRE | placebo L6M cut p95 / rank p | Bonf p | STRICT | TOL (literal) | NOW-ONLY | TOL-B / TOL-nc | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G|T|q0.8|S1 | -20,027 | -12,878 (12,041) | -10,754 | -6,284 | -881 | -5,733 | -12,083 (1.14) | -4,521 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| G|V|q0.8|S1 | -5,690 | -7,211 (9,424) | -6,253 | -1,677 | -351 | -2,291 | -6,189 (1.13) | -1,173 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| G|H|q0.9|S2 | -8,091 | -5,267 (9,302) | -4,647 | -2,459 | -1,311 | -2,623 | -5,267 (1.00) | -2,459 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| G|H|q0.8|S2 | -3,023 | -8,347 (11,959) | -8,352 | -6,459 | 1,105 | -4,718 | -6,408 (1.12) | -5,741 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| G|T|q0.9|S1 | -15,933 | -12,441 (12,033) | -9,633 | -2,810 | 239 | -3,413 | -12,855 (1.01) | -2,516 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| G|T|q0.9|S3 | -14,955 | -10,962 (12,615) | -8,286 | -2,498 | -738 | -3,255 | -10,962 (1.00) | -2,498 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| G|T|q0.9|S2 | -17,657 | -18,101 (17,453) | -13,575 | -5,578 | 1,148 | -5,384 | -21,834 (0.95) | -7,597 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| G|T|q0.8|S2 | -30,610 | -22,720 (18,590) | -18,299 | -10,026 | -31 | -8,986 | -23,135 (1.09) | -9,776 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |

### Reading

G (order-flow toxicity sizer): 36 cells swept, 8 cut the composite maxDD >= 20% in BOTH PRE and X-prime with the mean inside its MDE; 8 looked at once in L3M/L6M/HOLD/ALL: 0 meet the user's L6M definition (cut >= 20% with the mean inside MDE), median L6M maxDD change +201% (positive = deeper), 8 still cut ALL by >= 20%, STRICT 0 / TOLERANT 0 / NOW-ONLY 0 (TOL-B 0, TOL-nc 0); program placebo false-carry rate 6.5% at a 7% typical volume cut (about 2 chance carries of 36 vs 8 observed).

The toxicity sizers (INST-G: toxicity predicts the size of the move, not the direction of the signal) cut maxDD only in PRE and X-prime and deepen L6M and L3M (median +201%); 8 carry, 0 meet the user's definition.

### Notes
- Counts: STRICT/TOLERANT(literal)/NOW-ONLY over the looked cells: see Reading; TOL-B and TOL-nc are post-hoc, beside.
- dead_lookup (run before scoring): every cell here exists in the ledger under INST_D 1,044 / INST_E 396 / INST3C 701 / INST3F 134 / INSTG 36 / INST_H 16 (scored on the mean, 'EXACT' by name); this program re-prices them on drawdown. The new H4 (12) and H5 (4) cells and the engine-route H2 bracket rows have 0 hits. Appended after scoring with append_cells (program F1DD, tier PRICED), never rebuilt.
- Coverage gaps (not stack rules, not re-priced here): 8 NQ/ES pair-book cells (C), 24 close-window class books (F; C1 builds the close-fade sleeve), the stored INST-D/E s2 series (neighbours, shifted-state and random placebos, not scored cells).
- Single-week caveat: the composite L6M maxDD (22.9k) is one week (2026-01-19); the as-is L6M maxDD is the same week. L3M/L6M/HOLD have fewer than 20 losing weeks, so worst-20 is shown for PRE, X-prime, ALL only.
- Deviation from the prereg count: H4 has 12 cells, not 14 (counting error); swept total 2,311.
- Top-N by in-sample drawdown (the 40 cap in C) is post-hoc; nothing promoted; Shadow only.
- Code l2vast/ds3/code/inst_dd/, results l2vast/ds3/out/inst_dd/ (stage1_table.csv, stage2a_table.csv, final_rows.csv, summary.json), rows out/recent_wins/inst_dd.csv.
