# DS3_INST_E_DD - INSTITUTIONAL section E, cash-market lead (QQQ + 10 NDX leaders, 1-minute bars): re-read under DRAWDOWN FIRST (F1, overnight order, written 2026-11-01 00:00Z)

DATA. On disk: 1-minute Nasdaq bars QQQ + 10 NDX leaders 2022-26 (no NBBO/quotes). 396 grid cells re-run on the composite; tied to stored res_grid.npz. Quote context: P-E2 1-second bars $70.54, P-E1 mbp-1 one month $33.52 (unchanged, nothing bought).

**Prereg** `prereg/F1_INSTDD_prereg.md` sha256 `b177b68129c4bf2e492749bdf8ac98d8f1da9bac3c6c7dc4bc5957806d03ae98`; stage-1 selection `out/inst_dd/stage1_selection.json` sha256 `8ce67ccbbedfc6a5810d8ac8d1d8710a45b1b17084b618b4f17cb5854f802763` logged in DECISIONS.md before the recent look. Capped 20260206; UNTOUCHED never read. Frames: Sunday composite (headline) and as-is stack, live lots (K6 2 / P6 7 / U6 4 / H6 4-2 / M6 2 / A6 1), one-convention engine (dd_lib/lib3, unchanged).
**Coverage.** 396 cells swept in this group; 0 carried on PRE and X' (composite maxDD cut >= 20% in BOTH and mean not beyond -MDE in both); 0 distinct fire vectors; 0 looked at once in L3M/L6M/HOLD/ALL (cap 40 by min(PRE cut, X' cut)); 0 more carry in the as-is frame only (not looked at).
**Family-wise.** 396 cells swept; program placebo false-carry rate of the PRE+X' criterion for same-volume random skips/size-cuts in this group: 0/150 draws = 0.0% (15 sampled cells x 10 draws; mean volume cut 4%), i.e. about 0 chance carries expected of 396 swept vs 0 observed. Bonferroni placebo p = min(1, placebo rank p x distinct carried).

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
| qqq_sided_15>=1.199|skip|PE | skip | +1% | +10% | +11% | 273 (2,835) | 204 (2,391) | -5% | +6% |
| qqq_sided_15>=1.199|skip|PULL | skip | +1% | +10% | +11% | 273 (2,835) | 204 (2,391) | -5% | +6% |
| qqq_sided_5<=0.6125|skip|PE | skip | +8% | +30% | +6% | -2,703 (5,352) | -1,072 (6,755) | -19% | -3% |
| qqq_sided_5<=0.6125|skip|PULL | skip | +8% | +30% | +6% | -2,703 (5,352) | -1,072 (6,755) | -19% | -3% |
| cash_lead_5<=0.4622|skip|PE | skip | +8% | +31% | +5% | -3,855 (5,387) | -1,870 (7,146) | -4% | -6% |
| cash_lead_5<=0.4622|skip|PULL | skip | +8% | +31% | +5% | -3,855 (5,387) | -1,870 (7,146) | -4% | -6% |
| qqq_sided_15>=1.199|half|PULL | mult | +1% | +5% | +6% | 253 (2,053) | 186 (1,058) | -7% | +7% |
| qqq_sided_15>=1.199|half|PE | mult | +1% | +5% | +6% | 253 (2,053) | 186 (1,058) | -7% | +7% |

### Reading

E (cash-market lead): 396 cells swept, 0 cut the composite maxDD >= 20% in BOTH PRE and X-prime with the mean inside its MDE; none carried, so no recent window was opened and nothing is RISK-KEEP.

The 1-minute cash-lead states are INST-E NULL on the mean and also on drawdown: no cell cuts the composite maxDD >= 20% in both PRE and X-prime.

### Notes
- Counts: STRICT/TOLERANT(literal)/NOW-ONLY over the looked cells: see Reading; TOL-B and TOL-nc are post-hoc, beside.
- dead_lookup (run before scoring): every cell here exists in the ledger under INST_D 1,044 / INST_E 396 / INST3C 701 / INST3F 134 / INSTG 36 / INST_H 16 (scored on the mean, 'EXACT' by name); this program re-prices them on drawdown. The new H4 (12) and H5 (4) cells and the engine-route H2 bracket rows have 0 hits. Appended after scoring with append_cells (program F1DD, tier PRICED), never rebuilt.
- Coverage gaps (not stack rules, not re-priced here): 8 NQ/ES pair-book cells (C), 24 close-window class books (F; C1 builds the close-fade sleeve), the stored INST-D/E s2 series (neighbours, shifted-state and random placebos, not scored cells).
- Single-week caveat: the composite L6M maxDD (22.9k) is one week (2026-01-19); the as-is L6M maxDD is the same week. L3M/L6M/HOLD have fewer than 20 losing weeks, so worst-20 is shown for PRE, X-prime, ALL only.
- Deviation from the prereg count: H4 has 12 cells, not 14 (counting error); swept total 2,311.
- Top-N by in-sample drawdown (the 40 cap in C) is post-hoc; nothing promoted; Shadow only.
- Code l2vast/ds3/code/inst_dd/, results l2vast/ds3/out/inst_dd/ (stage1_table.csv, stage2a_table.csv, final_rows.csv, summary.json), rows out/recent_wins/inst_dd.csv.
