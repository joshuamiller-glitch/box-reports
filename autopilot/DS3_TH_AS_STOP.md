# DS3_TH_AS_STOP - can the TH-L2 -30 cut be a resting stop? (DIS-BB), BASE-4, 2026-11-04T22:53Z

Research only, nothing live, no PASS, no engine edits. Scope note l2vast/ds3/prereg/DISBB_scope.md sha256 833bc47c14ffa6ec1cfc6ea2365ec9bd34c6ed51a7e0704c7161f5861fcc5133 (DECISIONS.md; logged after two disclosed feasibility runs and before the grid was read). Engine: ZL-2's DIS-AB ts2 reference (all switches ON, locks re-run) through the existing hooks `bracket=(stop_array, target_array)` (exact kernel re-run), `stopcost`, `th_loss`, `th_loss_mult` (0 = arm only) and the DIS-AX patch points; tie-out: TH-on reproduces $2,520,149.07, TH-off $2,243,132.77. Code l2vast/ds3/code/disbb/ (bb_lib, bb_run, bb_run2, bb_an, bb_an2, bb_doc); data /mnt/l2/l2vast/ds3_base4/bb_*.pkl, bb_tab2.csv.

## Answer for the user
**As the engine models it, the -30 part of TH-L2 cannot be replaced by a resting 30-point stop: it keeps almost none of the gain and deepens the drawdown.** With every stop paying the same cost c, a 30-point stop (target 60) gains +1880 / +2060 / -36 $/week post-cap at stop cost 0.80 / 1.28 / 2.45 against TH off at the same cost (the box-side cut at the 0.80 frame: +12368 / +14597 / +18076; arm-only cut +10923 / +13151 / +16630), and changes the 2023-26 result by -7616 / -7945 / -9129 $/week (TH cut: -786 / +108 / +2029). The break-even stop cost for the post-cap gain is 2.43 pt; over 2023-26 there is no cost at or above 0.80 at which the stop beats TH off. The stack's HOLD maxDD goes from $85551 (TH off, c = 1.28) / $121322 (TH on) to $208388 with the 30-point stop (PRE improves: $75185 vs $149595 off; L6M $67985 vs $85551). Tighter (25) is worse, looser (35, 40) is less bad (40: post-cap +7347 at c = 1.28, 2023-26 -3976, HOLD maxDD $106927) but never positive over 2023-26. Targets of 30 or 45 with the 30-point stop are much worse (30/30: -23280 post-cap).
**What the liquidity condition adds after costs:** the full rule minus arm-only at equal cost is +1445 / +1446 / +1447 $/week post-cap and +1802 / +1801 / +1772 over 2023-26 at stop cost 0.80 / 1.28 / 2.45 and extra cut slippage 0 (about +1.4k to +1.5k post-cap at +1 and +2 pts as well). That is about 8% of the post-cap gain but nearly all of the 2023-26 gain (arm-only +257 vs full +2029 at c = 2.45): the pulled-support condition is what keeps the cut from being a net loss over the long history, and it cannot be expressed as a resting order. **Why the frames differ:** the engine's TH exit fills at the 1-second tape price of the trigger second (adverse >= 30 and, for the full rule, pulled support >= 30x) plus the 0.80 market frame, evaluated on stored per-second features, once per trade; a resting stop-market fills when price TOUCHES the level (any intra-second wick), at the level plus gap and slippage, which the bracket-override kernel prices at the nominal level plus the stop-cost frame c (0.80 / native 1.28 / join 2.45) on EVERY stop exit, including the 60-point stops of the baseline. Candidate explanations of the gap (NOT separated with the existing hooks; at the same cost 0.80 the 30-point stop earns +28093 post-cap against +37136 for the arm-only cut): (1) the stop is hit by intra-second wicks that the per-second cut may ignore (touch vs close triggering, UNVERIFIED), (2) the cut pays its cost only on trades that go on to be cut, the stop on all stop-outs, (3) the stop also stops the add-on lots and the PE-confirmation rows that the cut table does not cover. Which of (1)-(3) carries the gap is open (missing hooks below).

## 0. dead_lookup (before the grid)
No DEAD_CELLS row sets a 30-point stop on the six live books in the exact engine with locks re-run. Neighbours (not repeated): EXITN_E1 (83 loss-side cut cells, DS3_EXIT_N_LOSS.md), EXITN_E2/E2B (tighten-trail, DS3_EXIT_N_TIGHTEN_SCALE.md), SIXTY1/SIXTY1B (60-point bracket portfolio, DS3_SIXTY.md), L2EB (30/30 on L2 entry cells, DS3_L2ENTRY_B.md), BARSCAND (20/60 on bar types), DS3_TH_OOS.md line 44 (arm-only +16.6k post-cap, reproduced here as +16630 at the 2.45 frame).

## 1. Main table: weekly P&L and gain vs TH off at the same stop cost c (post-cap 2026-02-07..; 2023-26; carrying weeks dropped), full-stack maxDD
Frames: c is the stop-exit cost of EVERY stop (60-point and 30-point); the box-side cut costs 0.80 + s (s = extra cut slippage). TH off baseline P&L post-cap / 2023-26: c = 0.80 $26213 / $18735, 1.28 $23912 / $17781, 2.45 $20250 / $15688 per week.
| stop cost c | configuration | post-cap $/wk | gain vs TH off | 2023-26 $/wk | gain vs TH off | maxDD L6M | HOLD | PRE |
|--|--|--|--|--|--|--|--|--|
| 0.80 | TH off, stop 60 | +26213 | +0 | +18735 | +0 | +83527 | +83527 | +141816 |
| 0.80 | TH on full, cut +0 | +38582 | +12368 | +17950 | -786 | +62211 | +121033 | +73070 |
| 0.80 | TH on full, cut +1 | +33406 | +7193 | +15083 | -3652 | +68141 | +135370 | +81384 |
| 0.80 | TH on full, cut +2 | +28265 | +2052 | +12189 | -6546 | +74698 | +160384 | +89697 |
| 0.80 | TH arm-only, cut +0 | +37136 | +10923 | +16147 | -2588 | +61758 | +118045 | +72188 |
| 0.80 | TH arm-only, +1 | +31873 | +5659 | +13112 | -5623 | +67688 | +127372 | +77207 |
| 0.80 | TH arm-only, +2 | +26778 | +564 | +10623 | -8112 | +74246 | +156757 | +84467 |
| 0.80 | TH off, stop 30 / target 60 | +28093 | +1880 | +11119 | -7616 | +64923 | +193699 | +57724 |
| 0.80 | stop 25 / target 60 | +18999 | -7215 | +7299 | -11436 | +49135 | +200843 | +98564 |
| 0.80 | stop 35 / target 60 | +28181 | +1967 | +12809 | -5926 | +76835 | +179124 | +60995 |
| 0.80 | stop 40 / target 60 | +33225 | +7012 | +14971 | -3765 | +82963 | +91306 | +84242 |
| 0.80 | stop 30 / target 45 | +15193 | -11021 | +5307 | -13428 | +47015 | +247137 | +145366 |
| 0.80 | stop 30 / target 30 | +2632 | -23582 | -110 | -18845 | +62664 | +244080 | +271473 |
| 1.28 | TH off, stop 60 | +23912 | +0 | +17781 | +0 | +85551 | +85551 | +149595 |
| 1.28 | TH on full, cut +0 | +38509 | +14597 | +17890 | +108 | +62317 | +121322 | +73648 |
| 1.28 | TH on full, cut +1 | +33334 | +9422 | +15013 | -2769 | +68237 | +135658 | +81962 |
| 1.28 | TH on full, cut +2 | +28193 | +4281 | +12119 | -5663 | +74794 | +160672 | +90275 |
| 1.28 | TH arm-only, cut +0 | +37063 | +13151 | +16089 | -1692 | +61864 | +118333 | +72541 |
| 1.28 | TH arm-only, +1 | +31801 | +7888 | +13052 | -4729 | +67784 | +127661 | +77560 |
| 1.28 | TH arm-only, +2 | +26705 | +2793 | +10564 | -7217 | +74342 | +157112 | +84877 |
| 1.28 | TH off, stop 30 / target 60 | +25972 | +2060 | +9836 | -7945 | +67985 | +208388 | +75185 |
| 1.28 | stop 25 / target 60 | +16100 | -7812 | +5743 | -12039 | +52536 | +218133 | +130788 |
| 1.28 | stop 35 / target 60 | +26405 | +2492 | +11692 | -6090 | +77532 | +194402 | +66330 |
| 1.28 | stop 40 / target 60 | +31259 | +7347 | +13806 | -3976 | +85608 | +106927 | +89919 |
| 1.28 | stop 30 / target 45 | +13219 | -10693 | +4153 | -13629 | +49842 | +264883 | +179139 |
| 1.28 | stop 30 / target 30 | +632 | -23280 | -1241 | -19022 | +78634 | +273988 | +308597 |
| 2.45 | TH off, stop 60 | +20250 | +0 | +15688 | +0 | +90456 | +91353 | +174642 |
| 2.45 | TH on full, cut +0 | +38327 | +18076 | +17716 | +2029 | +62576 | +122025 | +75057 |
| 2.45 | TH on full, cut +1 | +33152 | +12902 | +14837 | -851 | +68471 | +136361 | +83371 |
| 2.45 | TH on full, cut +2 | +28011 | +7761 | +11943 | -3745 | +75028 | +161375 | +91684 |
| 2.45 | TH arm-only, cut +0 | +36880 | +16630 | +15944 | +257 | +62123 | +119036 | +73401 |
| 2.45 | TH arm-only, +1 | +31619 | +11368 | +12905 | -2783 | +68018 | +128364 | +78420 |
| 2.45 | TH arm-only, +2 | +26524 | +6273 | +10413 | -5275 | +74576 | +157979 | +85878 |
| 2.45 | TH off, stop 30 / target 60 | +20214 | -36 | +6559 | -9129 | +72667 | +252365 | +157849 |
| 2.45 | stop 25 / target 60 | +8914 | -11336 | +1968 | -13720 | +68218 | +270492 | +229593 |
| 2.45 | stop 35 / target 60 | +21221 | +971 | +8650 | -7037 | +84114 | +235888 | +82997 |
| 2.45 | stop 40 / target 60 | +26071 | +5821 | +10904 | -4784 | +92095 | +147012 | +103317 |
| 2.45 | stop 30 / target 45 | +7367 | -12884 | +1012 | -14676 | +67640 | +307133 | +281064 |
| 2.45 | stop 30 / target 30 | -3993 | -24244 | -3902 | -19590 | +108010 | +343413 | +460965 |

## 2. Break-even stop cost (stop 30 / target 60 vs TH off at the same cost; interpolation on c = 0.80, 1.28, 2.45, 3.5, 5.0)
| c | post-cap gain | 2023-26 gain |
|--|--|--|
| 0.80 | +1880 | -7616 |
| 1.28 | +2060 | -7945 |
| 2.45 | -36 | -9129 |
| 3.50 | -2313 | -10146 |
| 5.00 | -6461 | -12048 |
Break-even: post-cap 2.43 pt (so a native stop at 1.28 is inside it, a join at 2.45 is at it); 2023-26: none at c >= 0.80 (the gain is negative at every cost tested, slope about -0.9k/week per point).

## 3. By book (cube books; gain vs TH off at the same cost; post-cap / 2023-26 $/week)
| configuration | KB | PE | SM | HM | MV | PB |
|--|--|--|--|--|--|--|
| THfull+0 at c = 1.28 | +1503 / -190 | +10154 / +911 | +935 / +102 | +1912 / -229 | +256 / -499 | -163 / +13 |
| S30T60 at c = 1.28 | -393 / -1315 | +3328 / -3631 | +131 / -660 | -499 / -1159 | -1488 / -1076 | +980 / -104 |
| S30T60 at c = 2.45 | -1266 / -1636 | +2719 / -4117 | -78 / -752 | -776 / -1294 | -1749 / -1218 | +1112 / -111 |
| S40T60 at c = 1.28 | -18 / -493 | +7195 / -1475 | +1008 / -513 | +201 / -452 | -1196 / -945 | +158 / -97 |
One engine book at a time with the 30-point stop (stop 30 / target 60; gain vs TH off; post-cap / 2023-26 $/week; c = 1.28 and 2.45):
| engine book | c = 1.28 | c = 2.45 |
|--|--|--|
| HM | +2547 / -862 | +2928 / -1033 |
| KB | -356 / -1859 | -983 / -2103 |
| SM | +1236 / -455 | +1559 / -416 |
| PE | +4857 / -3622 | +4446 / -4209 |
| MV | -1501 / -1079 | -1763 / -1222 |
| PB | +1241 / -97 | +894 / -139 |
(ST rows are identical to TH off: the engine book ST is not among the traded rows of the six cube books.) PE is the only book where a 30-point stop earns post-cap (+4.9k at c = 1.28, +4.4k at 2.45) and it loses 3.6-4.2k over 2023-26; HM +2.5k post-cap and -0.9k over 2023-26; KB and MV lose in both.

## 4. Missing hooks (nothing edited)
* A touch-vs-close trigger switch for the cut (to separate wick stop-outs from the cost difference). * A per-row stop COST (the stop-cost frame is one global number; the bracket hook cannot give the 30-point stop a different cost from the 60-point stop). * Stop override for the add-on lots / PE-confirmation rows separately from the base lots. * A resting-stop gap model (the kernel prices a stop at the nominal level plus a constant). * A measured native-stop cost (FORWARD_STOP_AB.md: 1.28 pt from 8 stops; the live A/B has not run). * The lock R units under a bracket override: I read them as book-level constants (R_K6), i.e. not scaled with the stop, UNVERIFIED.

## Limits
* Native stop cost 1.28 rests on 8 stops (FORWARD_STOP_AB.md); the TH exit cost 0.80 has no measured fill (DS3_TH_COST.md). * Post-cap is 25 weeks of one regime. * The kernel re-run changes every row, not only the rows the cut would have fired on. * The comparison "TH exit vs stop" is about the engine frames; a live resting order would also depend on the broker's stop-market behaviour in a fast book, which is not modelled.
