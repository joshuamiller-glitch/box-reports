# REDO D4: THL, THP, UF-LOSS, L2SL re-score through label day 20261030

Status: complete for D4's group (2026-11-01). Descriptive only, no PASS claims. Primary basis as in the ledger (THL/THP/L2SL: M, pts per contract; UF-LOSS: N). Windows L1M..L3M, L6M, HOLD, MID, PRE, X' as defined in code/cap/windows.py.

## Coverage (ledger rows)
| Program | Rows | Scored | Tied | Not tied (flagged) |
|---|---|---|---|---|
| THL | 864 | 864 | 727 | 137 (D6_TB4B, redo tick bars; all 137 TIED in the old-trade-list variant) |
| THP | 845 | 845 | 724 | 121 (D6_TB4B; all 121 TIED in the old-trade-list variant) |
| UF-LOSS c1 | 44 | 44 | 44 | 0 |
| UF-LOSS c2 | 4 | 4 | 4 | 0 |
| UF-LOSS c3 | 98 | 98 | 97 | 1 (stored live $ not reproducible, see below) |
| UF-LOSS c4 | 15 | 15 | 15 | 0 |
| UF-LOSS c5 | 43 | 43 | 43 | 0 |
| UF-LOSS c6 | 27 | 27 | 27 | 0 |
| L2SL | 12 | 12 | 12 | 0 |

## Partial rows (delivered, labelled in the `note` and `data_end_ld` columns)
* O6 (40 THL + 1 THP rows, 3 cells): the T-OPEN B2 harness pickles end at label day 20261023 (20261022 for OR15m); 20261026..20261030 does not exist. members_q1 (SSA de-dup) drops 22/616, 6/299, 14/375 harness rows in the old period; the dropped entries are in no other cell's members, so the rule is not reproducible. Label days <= 20260206 are the stored members exactly (rows identical, dM bit-exact, all 41 ledger rows TIED); 20260207..20261023 use ALL harness rows (148/99/90 new, membership unverified, over-count risk about 3.6%). Windows are therefore 'partial: to 20261023'.
* B3_NQ (1 ledger row + 5 non-ledger): the stored B3_F19 leg list runs to 2026-10-14 (227 NQ legs); old 180 trades identical, dM bit-exact, TIED. Window data end 20261014 (legs after 20260206 come from the stored list, signal inputs not re-derived).
* D6_TB4B: redo bars (de-duplicated tape) differ from the old bars in 17 of 843 old trades in 10 old months (stray Sunday hour), 2 of them in the old L3M window. Both variants delivered: `D4__<prog>_windows.csv` (redo) and `D4__<prog>_windows_tb4b_oldprefix.csv` (old stored trade list for ld <= 20260206 + redo trades after; ties). New L3M mean THL -1.996 (redo) vs -1.958 (old list); THP 2.396 vs 2.366.

## Tie-out (done before scoring every stream/cycle)
* THL/THP: every stream's old trades equal the stored trades_<stream>.parquet and every rule dM equals the stored sealed npz (max abs diff 0.0). Stack books ST HM WT KB SM PE: lots and taken trades identical to dv2a/stack_trades through its last day 20261016.
* UF-LOSS c1 (D_main), c3 (D3), c4 (C4), c5 (D5), c6 (D6, D6q): all matrices DM/DL/DN/FI/NZ(/XI/CH) bit-exact on the 44,385 old trades. C6 walk-forward: stored models re-applied to redo rows, P6 predictions bit-exact on all old rows, 3 models re-trained from scratch reproduce the stored predictions bit-exactly. C4 chains extended to monthly refits through 2026-10 (old decisions identical).
* UF-LOSS c2 (D2): 8 F2-footprint cells (arm 40, 8 of 522) differ at ONE old trade (PB 20260202, redo t3_ldp1m footprint bar); no ledger row uses them; 4/4 rows tie.
* UF-LOSS c1 HAZ (D_extra): 12 of 28 cells differ at 6 old trades (Jan-Mar 2024), the first firing row moves around the p threshold, FI identical; logistic refit is not bit-reproducible (cause not isolated). The 3 ledger rows tie to the stored precision. Refits 2026-04, -07, -10 added.
* L2SL: the 12 cells equal the stored D.npy columns bit-exactly; windows and $ tie.
* UF-LOSS c3, row `loss|trig=L6a20w10|gate=reg2|rem=FULL [scope WT]`: pts 0.671, n 69, MDE and L6M/HOLD/PRE/X' tie, but the stored live $ (23,590) is not reproducible (954 WT trades x 0.671 x $20 x 7.0 lots = 89,664). Flagged NOT TIED (stored value inconsistent); the other 97 tie.

## Descriptive (mean pts per contract, old L3M to Feb 06 -> new L3M to Oct 30)
THL 2.43 -> 0.05 (previous batch); THP 2.56 -> 0.98; UF-LOSS c1 0.032 -> 0.003 (24/41 rows L3M>0); c2 0.107 -> -0.158; c3 0.148 -> 0.032 (54/98); c4 0.388 -> 0.161 (9/15); c5 0.049 -> 0.037 (18/43); c6 0.031 -> -0.017 (16/27); L2SL 1.608 -> 0.836 (8/12, all with L6M>0).

## Files
out/recent_wins/redo/{thl,thp,uf_loss,l2sl}/D4__*  (vec parquet, *_windows.csv, *_tie.csv, *_pending.csv). Code: code/recent_wins_redo/D4/ (d4_rules, d4_streams, d4_assemble, d4_uf_*, d4_c6, d4_l2sl, d4_pt, uf/ patched cycle copies). Bulk (D2..D6 matrices, F6, P6, models): /mnt/l2/l2vast/ds3_redo_d4/uf/loss1.
