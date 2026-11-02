# DS3_ZONES_3_L2_TAPE_LP_AGAINST_NFIX - flag #2 (natural mask, 2,081 rows) re-scored on V13Y vs V13Y+nfix vs nfix with take lines off (ZL-2, 2026-11-02; Shadow only)
Why: BASE-4 found take-line deltas credited ~3.39 pts/lot on engine basis N (nfix=True fixes it; V13Z base coming). Bases: A = V13Y; B = V13Y + nfix; C = nfix with take lines off (ov nfix=True, lines='empty'). Saved $k = minus realised net of flagged taken rows (row-level, engine record). Files: ds3_zl/v13z_row_net_{nfix,nfixnotake}_{nolock,12R}.pkl, lp_natural_saved_V13Y_vs_nfix.csv, lp_null_{V13Y,nfix,nfixnotake}_natural.csv.

## 1. Saved dollars (n = taken flagged rows)
| base | lock | n | L6M | HOLD | PRE | X' | ALL | 2023 | 2024 | 2025 | 2026 |
|--|--|--|--|--|--|--|--|--|--|--|--|
| A V13Y | none | 538 | 43.0 | 60.7 | 95.8 | 1.3 | 136.8 | 6.5 | 54.3 | 24.1 | 52.0 |
| A V13Y | 12R | 354 | 16.2 | 27.8 | 91.6 | 14.2 | 123.7 | 20.0 | 49.5 | 28.7 | 25.5 |
| B +nfix | none | 540 | 45.5 | 65.6 | 100.1 | -9.8 | 137.8 | -5.0 | 57.4 | 30.6 | 54.9 |
| B +nfix | 12R | 332 | 16.5 | 33.5 | 72.9 | 15.4 | 119.9 | 20.8 | 36.0 | 37.5 | 25.6 |
| C nfix, no take | none | 513 | 9.8 | 2.7 | 75.0 | -13.5 | 64.1 | -4.4 | 20.6 | 49.7 | -1.8 |
| C nfix, no take | 12R | 301 | -6.2 | -35.9 | 118.2 | 6.2 | 101.1 | 14.7 | 61.4 | 49.1 | -24.1 |
Base total $k (lock none): A 2,563 / B 1,663 / C 3,496 (take lines hurt once the basis is fixed, as BASE-4 found).

## 2. 2,001-family null (same natural scan inside every family; thinned to 2,081 rows)
| base | lock | real min3 / min4 | p(min3) pooled | p(min4) pooled | shuffled-day p(min3) |
|--|--|--|--|--|--|
| A | none | 43.0 / 1.3 | 0.036 | 0.181 | 0.099 |
| A | 12R | 16.2 / 14.2 | 0.194 | 0.079 | 0.402 |
| B | none | 45.5 / -9.8 | 0.039 | 0.315 | 0.109 |
| B | 12R | 16.5 / 15.4 | 0.221 | 0.097 | 0.448 |
| C | none | 2.7 / -13.5 | 0.217 | 0.254 | 0.426 |
| C | 12R | -35.9 / -35.9 | 0.650 | 0.578 | 0.922 |

## 3. Phase-averaged maxDD cut (9 lock-reset phases, lock none; base for the cut = the same config without the flag). Z3 band (V13Y, flip 2%): L6M 15.5, HOLD 13.3, MID 26.8, PRE 11.5, X' 14.1
| base | L6M | HOLD | MID | PRE | X' |
|--|--|--|--|--|--|
| A V13Y | +12.4 | +9.9 | -16.1 | +2.5 | -13.7 |
| B +nfix | +7.1 | +7.1 | -1.6 | +0.6 | -7.3 |
| C nfix no take | -2.3 | -1.7 | +6.8 | +4.3 | -16.3 |
The V13Y band is not recomputed for nfix; the cut is below the V13Y band in every base.

## Reading
Flag #2's saved dollars survive the nfix correction (B ~ A: 137.8 vs 136.8k ALL, X' now -10) but are almost entirely a take-line interaction on the shipped base: with the take lines off (C, lock none) L6M/HOLD fall to +9.8 / +2.7 (null p 0.22) and in 12R go negative (L6M -6, HOLD -36). PRE stays positive in all bases (+75..+118). The drawdown band fails in all bases. Label: LEAD-weak -> DOWNGRADE to NOISE-LEANING / Shadow only on the corrected base (positive PRE only; recent windows depend on the artefact-laden take lines). No PASS.

## Other results (same order)
LP_FLIP (pre-registered, sha256 3de31519...e8 in DECISIONS.md 10:16Z; the "just-broken print level" test is that cell, already done): DEAD, V13Y lock none L6M +71 / HOLD +111 / PRE -232 / X' +7 $k, per year 2023 +23 / 2024 -172 / 2025 -152 / 2026 +108; overlap with BT 5m swing flip (D40 mask, 3,027 rows): 1,109 shared of 13,610 (Jaccard 0.07, 8% of the LP_FLIP mask); LP_AGAINST natural vs BT: 186 shared (Jaccard 0.04).
Chains refreshed (new files, V13Y engine, monthly, ZL-2 dir): chain_V13Y_LP_AGAINST_NATURAL_25_4h_D40_{nolock,12R}.csv (engine delta total +89.5k / +288.9k vs row-level 137/124k: lock and sizing re-optimisation) and chain_V13Y_LP_FLIP_25_D40_{nolock,12R}.csv (-198.4k / +300.4k).
