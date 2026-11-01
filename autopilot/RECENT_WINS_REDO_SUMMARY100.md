# RECENT_WINS_REDO_SUMMARY100 (lead/SUM, 2026-11-01 ~23:00Z) - descriptive VIEW, post-hoc, no PASS claim, append-only

Source: RECENT_WINS_REDO.md rebuilt 22:35Z (dated copy RECENT_WINS_REDO_2026-11-01.md; code l2vast/ds3/code/recent_wins_redo/main report.py -> assemble.py, scored_rows_latest.csv). Supersede rule in assemble.py: D6/T3/TAIL1/D8/D7/T2 > D5S > rest (both for vectors and tie states); NOT_TIED_CLASSIFICATION.csv applied; BARS-ENG 2,765 rows all tied; TAIL-1 thpc2-loss-refit 6 rows all tied. Rebuild gave the same counts as the 22:29Z page (the late T3 EQR-H/EXP2d/EQR-B and D8 THPC3 vectors were already in vec/).

## 1. Coverage and status counts
| item | n |
|---|---|
| old ledger rows | 14,734 |
| re-scored | 14,702 (100.0% of extendable) |
| cannot extend | 32 |
| pending | 0 |
| tied / tied in variant or counterfactual / irreproducible / NOT TIED | 14,165 / 456 / 80 / 1 |
| still on (L3M>0 and L6M>0) | 5,488 |
| FADING / STOPPED | 3,972 / 4,880 |
| other (L3M>0 with L6M<=0) | 362 |
| turned on since Feb, strict (old L3M<=0, new L3M and L6M>0) | 6 (3 L2ENTRY-A double-tercile, 3 UF-LOSS c6) |
| status NEW (May-Jul <=0, Aug-Oct >0) / RISING / STABLE | 3,286 / 1,444 / 1,120 |

## 2. Top 10 by new L3M $ at live lots (13 wk; rows are overlapping variants, not additive; all tied; none irreproducible)
| # | program / cell | book | new L3M $ | old L3M $ | status | D7 v1.2 mapping |
|---|---|---|---|---|---|---|
| 1 | THPC2 profit qr_profit/qr/1w/S1d/none | pooled chain | 2,513,136 | 494,381 | RISING | not a D7 piece (profit-side chain; D7 TH-L2 profit OFF) |
| 2 | EXP1 profit chains v0 all/bookcell/12m/m0.0 | ALL10 profit side | 2,465,535 | 649,518 | RISING | not a D7 piece (profit chain); variant: v0 look-ahead vol key |
| 3 | THPC2 profit qr_profit/qr/1w/Sintra/none | pooled chain | 2,412,031 | 793,564 | RISING | not a D7 piece |
| 4 | EXP1 profit all/bookcell/12m/m0.5 | ALL10 | 2,371,102 | 450,899 | RISING | not a D7 piece; look-ahead vol key variant |
| 5 | L2ENTRY-A skipTop3_pulled_opp10 [ALL] | ALL | 2,333,913 | 284,927 | RISING | not a D7 piece (L2 order-book entry filter, pts/signal; D7 v1.2 has no L2 book entry filter; a skipTop3 filter in the EINT1 style but on an L2 feature, not an EINT1 feature) |
| 6 | EXP1 profit all/bookcell/12m/m1.0 | ALL10 | 2,310,142 | 534,254 | RISING | not a D7 piece; look-ahead vol key variant |
| 7 | THL2 L2H H6P/mfe10/pul500/take | 10 static books pooled | 2,308,117 | 735,551 | RISING | not a D7 piece (L2H profit-take hypothesis; D7 has TH-L2 LOSS 30/5s/30x only, profit OFF) |
| 8 | THPC2 profit qr_profit/qr/1w/Sintra/reg | pooled chain | 2,209,372 | 352,200 | RISING | not a D7 piece |
| 9 | EXP1 profit all/bookcell/6m/m0.0 | ALL10 | 2,185,972 | 276,018 | RISING | not a D7 piece; look-ahead vol key variant |
| 10 | EXP1 profit all/bookcell/6m/m0.5 | ALL10 | 2,174,267 | 272,644 | RISING | not a D7 piece; look-ahead vol key variant |

Ledger rows that DO correspond to D7 v1.2 ON pieces: the 70/30 entry split = 'L2SE entry (THP_POLICY entry)' F=0.7 X=3 N=1 veto v4 per book plus 'SPLIT 70/30' STACK. New vs old L3M $/wk: STACK6 -5,401 vs +10,007 (L3M -$70.2k vs +$130.1k); KB -4,298 vs +2,975; ST -2,700 vs +3,902; HM -178 vs +2,535 (all four changed sign); SM +326 vs +728; WT +2,195 vs +701. The 17 THP_POLICY profit lines are D6 profit rules that D7 v1.2 keeps OFF: 14 still positive on L3M, PB hour_tot_ge1.2 (-1.18 pts vs +0.92) and ST lock5 (-0.42 vs +2.72) flipped negative, ST hour_tot_ge3.0 +0.03 (was +2.59). No ledger row represents the shipped TH-L2 loss composite (30 pts/5 s/30x) one-to-one, nor zones HALF, 12R lock, PE 45-s (the ledger lists CONFIRM-BARS PE 45-s three-bar as SHADOW: 186 rows, 182 positive, 4 CONFIRM-BARS S1 rows negative: KB ha/45s/two, MV tc three_bar a and c1, PE tc three_bar b).

## 3. Sign check on D7 v1.2 pieces (engine runs, V12.run_v12 with the piece toggled; total of 6 core books + X cells, $/week mean over ISO weeks)
Base total per wk: L3M +13,487, L1M +18,375, L6M +26,045, HOLD +21,974, old L3M (2025-11-06..2026-02-06, same new tables) +13,713. Piece effect = base minus piece removed (for OFF/shadow pieces: variant minus base). MDE = 2.8 x SE of the weekly mean total (the engine rows are the total series, not paired deltas, so the MDE is a conservative level MDE). Mean only; drawdown not scored here.
| piece | new L3M (MDE, wk) | old L3M (MDE) | sign | L1M | L6M | HOLD |
|---|---|---|---|---|---|---|
| TH-L2 loss | ON piece: base minus piece removed | -9,172 (MDE 28,700, n13) | -21,539 (MDE 30,525, n14) | same sign | -857 | +3,304 | -3,920 |
| zones HALF vs skip | ON piece: base minus piece removed | -2,353 (MDE 4,510, n13) | +650 (MDE 22,850, n14) | SIGN CHANGE | -4,039 | +216 | +1,199 |
| zones HALF vs no zones | ON piece: base minus piece removed | +3,042 (MDE 5,101, n13) | -4,301 (MDE 20,949, n14) | SIGN CHANGE | -1,567 | +365 | -2,324 |
| 12R lock | ON piece: base minus piece removed | +1,587 (MDE 23,890, n13) | -5,683 (MDE 27,661, n14) | SIGN CHANGE | +9,205 | -8,279 | -7,931 |
| 70/30 split | ON piece: base minus piece removed | -2,635 (MDE 5,164, n13) | +827 (MDE 6,549, n14) | SIGN CHANGE | -1,836 | +1,834 | +1,624 |
| PE 45s NY | ON piece: base minus piece removed | +1,929 (MDE 13,055, n13) | -1,944 (MDE 20,277, n14) | SIGN CHANGE | +1,342 | +4,831 | +1,457 |
| ER(20) | ON piece: base minus piece removed | -3,160 (MDE 25,674, n13) | -4,263 (MDE 25,484, n14) | same sign | +6,740 | +1,447 | +2,453 |
| Asia cut 50% | ON piece: base minus piece removed | -5 (MDE 81, n13) | -574 (MDE 2,638, n14) | same sign | -52 | -111 | +74 |
| Native stop vs join | ON piece: base minus piece removed | +81 (MDE 55, n13) | +116 (MDE 133, n14) | same sign | +80 | +66 | +276 |
| Native stop vs parity | ON piece: base minus piece removed | +51 (MDE 41, n13) | +49 (MDE 78, n14) | same sign | +61 | +18 | +239 |
| NY-AM 1 lot (vs 2) | ON piece: base minus piece removed | +9,857 (MDE 22,157, n13) | -6,211 (MDE 21,682, n14) | SIGN CHANGE | +908 | +2,379 | -250 |
| U7 blackout | ON piece: base minus piece removed | -2,530 (MDE 7,118, n13) | +384 (MDE 5,651, n14) | SIGN CHANGE | -3,539 | -4,481 | -4,158 |
| OTE62 B73 vs skip | ON piece: base minus piece removed | +721 (MDE 5,054, n13) | +1,946 (MDE 5,056, n14) | same sign | -679 | +714 | -457 |
| TH-L2 profit (OFF piece) turned on | SHADOW/OFF piece: effect of turning ON | -3,148 (MDE 17,232, n13) | -4,417 (MDE 19,624, n14) | same sign | -13,359 | +1,961 | -3,034 |
| sig_hm on | SHADOW/OFF piece: effect of turning ON | -1,816 (MDE 4,272, n13) | -2,333 (MDE 6,787, n14) | same sign | -4,187 | -641 | +512 |
| sig_kb on | SHADOW/OFF piece: effect of turning ON | +103 (MDE 4,521, n13) | -295 (MDE 7,469, n14) | SIGN CHANGE | +740 | -370 | +335 |
| sig_pe on | SHADOW/OFF piece: effect of turning ON | -1,508 (MDE 8,702, n13) | +117 (MDE 10,194, n14) | SIGN CHANGE | -3,852 | +1,403 | +106 |
| X1 (2 lots, outside lock) | SHADOW standalone | -535 (MDE 3,418, n13) | +1,603 (MDE 3,941, n14) | SIGN CHANGE | -2,377 | +134 | +466 |
| X2 (2 lots, outside lock) | SHADOW standalone | -2,060 (MDE 4,085, n13) | +712 (MDE 2,694, n14) | SIGN CHANGE | -2,845 | -467 | -157 |
| X3 (2 lots, outside lock) | SHADOW standalone | -456 (MDE 2,655, n13) | +331 (MDE 3,020, n14) | SIGN CHANGE | +821 | -1,077 | -983 |
| X4 (2 lots, outside lock) | SHADOW standalone | -2,195 (MDE 5,582, n13) | +1,765 (MDE 3,375, n14) | SIGN CHANGE | -6,286 | -782 | +103 |
| X5 (2 lots, outside lock) | SHADOW standalone | +1,037 (MDE 4,052, n13) | +1,417 (MDE 3,049, n14) | same sign | -2,026 | +357 | +369 |
| X1-X5 total | SHADOW standalone | -4,209 (MDE 10,087, n13) | +5,828 (MDE 8,201, n14) | SIGN CHANGE | -12,713 | -1,834 | -202 |

Reading: D7 v1.2 ON/shadow pieces that changed sign on L3M new vs old (all inside the MDE, so noise-sized): zones HALF, 12R lock, 70/30 split, PE 45-s NY, NY-AM 1 lot, U7 blackout, X1-X4 (and X1-X5 total), sig_kb, sig_pe. Unchanged: TH-L2 loss (negative in both in this mean view), ER(20), Asia cut, Native stop, OTE-62 B73, sig_hm, TH-L2 profit. Caveats: TH-L2 loss and U7 runs took about 5 s (cached engine path); a negative TH-L2 loss mean effect in both windows is a mean-only reading of a drawdown rule and should be checked with the drawdown-first tables (DS3_REDO_TOP15_D7 base) before any conclusion; the ledger STACK split figure (-5.4k/wk) and the engine split effect (-2.6k/wk) differ because the ledger row is the as-stack frame at D6 lots, the engine row is on the v1.2 base with locks. Sign-check script and arrays: scratchpad sum/signchk.py, an.py, runs.npz (session scratchpad).
