# DS3_L2_UF_ENTRY_C11 - L2-UNTIL-FOUND cycle 11, ENTRY: decomposition of the PE NY confirmation gap on one engine (agent UF-ENTRY, 2026-10-31)
Research only; UNTOUCHED never read. Prereg autopilot/UF_ENTRY_C11_prereg.md sha256 50b99ce4c0e546880afb5bf32ebb7a4706c04076f4206a5d3f58e3b903560ff2 (before any cycle-11 statistic); no selection; one look. One engine: the six engine books, PE rows in NY-AM / NY-PM replaced, every other row the plain 70/30 floor, lock engine (c=1, research lots, PLAN-R; no ER multiplier so planned-R and causal running-max governors coincide here), N basis; LIVE-CAL at the end. Units: pts per planned lot (per contract of final position = same since lots entered average 1.00-1.01), $/wk at research lots (PE 5.6; x1.25 for 7 live lots), MDE 2.8 SE of the paired weekly delta.

## Page 1 - what explains the gap
1. **The +0.92 was a mislabelled cell; there is no 2.6-pt split penalty.** CF2's 'a | A70' puts 70% in AT THE SIGNAL whether or not a confirmation arrives and adds only the 30% at the confirmation. The coded spec (no confirmation = no trade; market at the close; then the 70/30 from that entry) scores **+3.29 per planned lot in L6M (+3.20 HOLD, +1.53 PRE, +0.63 X')** vs the pure wait **+3.57 (+3.54, +1.58, +0.81)**: the split costs 0.28 per planned lot, not 2.65. Cycle 10's rows labelled 'Sunday spec as coded' are superseded (erratum in DS3_L2_UF_ENTRY_C10.md).
2. **On the SAME confirmed trades the confirmation loses money; the whole gain is the skipped signals.** L6M: the 352 confirmed trades earn +6.59 per planned lot at the signal (floor) but +2.71 entered at the close (pure wait) and +2.26 coded - waiting costs 3.9-4.3 pts a trade; the 230 UNCONFIRMED signals (34-40% of the signals) lose -14.9 pts per planned lot under the floor and are not traded. Identity: 0.605 x (2.71 - 6.59) + 0.395 x (0 + 14.95) = +3.56 ~ +3.57. PRE: skipped -6.9, X' -6.1: the filter value is much smaller before 2025 (this is the same recent concentration as the LEAD).
3. **Lock engine: only 30% of the signals are tradable rows.** The PE book is already in a position on most signals (busy rule): in L6M the floor keeps 172 of 582 NY signals; the per-planned-lot average over ALL signals is therefore not what the stack sees. Stack delta = trade P&L of the ENGINE-KEPT rows exactly (A0 +3,610 vs +3,569; coded +3,098 vs +2,920 \$/wk in L6M). Decomposition of A0 (L6M, \$/wk): floor-only rows avoided **+2985** (74 rows the floor takes and loses on), variant-only rows admitted (re-entry in) **+1785** (48 rows), shared rows (later entry, worse price) **-1160**. Re-entry in/out, not the average, is where the stack number comes from; in PRE the avoided floor-only rows were small winners (+431 forgone), the admitted rows +393 and the shared rows -587, so the three lines sum to -625.
4. **Lots/volume: nil.** Lots entered per filled trade: pure wait 1.00, coded 1.00-1.01 (the risk-capped add takes the 30% back to ~1 lot), A70 0.90; lots-weighted and per-planned-lot averages coincide to 0.01. The confirmation fires on 61-67% of the signals (352 / 582 L6M); the fewer-trades effect is the skipped-signal term of point 2, not a size effect.
5. **Pure wait vs split for the confirmed PE entries (plain sentence): they are the same trade within noise; code the split if the account wants one rule for all books, code the full-lot market if it wants the simpler one - it does not matter.** Stack, coded minus pure wait ($/wk, paired MDE): L6M -649 (1817), HOLD -763 (1711), PRE -61 (1259), X' +108 (1835), 2026 -43 (981); LIVE-CAL L6M -40 (443). That reproduces SS-2 (coded minus no-split -0.4k L6M, -0.8k HOLD at live lots, paired MDE 1.6-1.9k): the split costs 0.5-0.8k/wk at research lots in L6M / HOLD (all inside about one paired MDE) (a plausible reason, not tested: the confirmed trades have already had their pullback, so the 3-pt dip add on top is less useful). Gated vs ungated dip inside the coded entry: -20 L6M (MDE 194).
6. Governors: this engine carries no ER multiplier, so planned-R and causal running-max are identical here; the ER effect on these rows is the SS-2 V1/V2 comparison (quoted there: removing the ER multiplier on confirmed entries -1.7k L6M, MDE 4.8k).

## 1. Decomposition table
| quantity (PE NY-AM + NY-PM, N, research lots) | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| floor: signals / confirmed / engine-kept rows | 126 / 68 / 35 | 582 / 352 / 172 | 637 / 392 / 196 | 1504 / 947 / 475 | 540 / 458 / 356 |
| A0 pure wait (market at the close): signals / confirmed / engine-kept rows | 126 / 68 / 23 | 582 / 352 / 146 | 637 / 392 / 164 | 1504 / 947 / 393 | 540 / 458 / 309 |
| A0 pure wait (market at the close): per planned lot over ALL signals (delta vs floor) | +5.31 | +3.57 | +3.54 | +1.58 | +0.81 |
| A0 pure wait (market at the close): same CONFIRMED trades, mean pts (floor +6.59 L6M) | +0.78 (floor +1.74) | +2.71 (floor +6.59) | +3.48 (floor +7.02) | +3.29 (floor +4.85) | +4.50 (floor +4.64) |
| A0 pure wait (market at the close): trade-level sum of all rows, $/wk | +12494 | +8300 | +7902 | +3553 | +1114 |
| A0 pure wait (market at the close): trade-level sum of ENGINE-KEPT rows (variant kept minus floor kept), $/wk | +7278 | +3610 | +3388 | -625 | -41 |
| A0 pure wait (market at the close): lock-engine stack delta, $/wk (MDE) | +5665 (17892) | +3569 (7112) | +3272 (6485) | -425 (3491) | -588 (4553) |
| C coded (confirmation then 70/30): signals / confirmed / engine-kept rows | 126 / 68 / 23 | 582 / 352 / 145 | 637 / 392 / 163 | 1504 / 947 / 398 | 540 / 458 / 307 |
| C coded (confirmation then 70/30): per planned lot over ALL signals (delta vs floor) | +5.37 | +3.29 | +3.20 | +1.53 | +0.63 |
| C coded (confirmation then 70/30): same CONFIRMED trades, mean pts (floor +6.59 L6M) | +0.88 (floor +1.74) | +2.26 (floor +6.59) | +2.93 (floor +7.02) | +3.21 (floor +4.85) | +4.29 (floor +4.64) |
| C coded (confirmation then 70/30): trade-level sum of all rows, $/wk | +12626 | +7666 | +7143 | +3438 | +865 |
| C coded (confirmation then 70/30): trade-level sum of ENGINE-KEPT rows (variant kept minus floor kept), $/wk | +7143 | +3098 | +2735 | -1064 | -164 |
| C coded (confirmation then 70/30): lock-engine stack delta, $/wk (MDE) | +5622 (17129) | +2920 (6889) | +2508 (6292) | -486 (3277) | -480 (4811) |
| A70 (CF2 cell, 70% at the signal): signals / confirmed / engine-kept rows | 126 / 68 / 37 | 582 / 352 / 192 | 637 / 392 / 217 | 1504 / 947 / 488 | 540 / 458 / 353 |
| A70 (CF2 cell, 70% at the signal): per planned lot over ALL signals (delta vs floor) | +2.22 | +0.92 | +0.88 | +0.82 | +1.03 |
| A70 (CF2 cell, 70% at the signal): same CONFIRMED trades, mean pts (floor +6.59 L6M) | +1.72 (floor +1.74) | +4.94 (floor +6.59) | +5.42 (floor +7.02) | +4.41 (floor +4.85) | +5.27 (floor +4.64) |
| A70 (CF2 cell, 70% at the signal): trade-level sum of all rows, $/wk | +5219 | +2148 | +1964 | +1851 | +1413 |
| A70 (CF2 cell, 70% at the signal): trade-level sum of ENGINE-KEPT rows (variant kept minus floor kept), $/wk | +3430 | +2365 | +2081 | +74 | +69 |
| A70 (CF2 cell, 70% at the signal): lock-engine stack delta, $/wk (MDE) | +3251 (9363) | +2334 (5399) | +1598 (4824) | -1106 (2434) | -418 (2630) |
| floor: pts per planned lot on the UNCONFIRMED (skipped) signals | -12.67 (n=58) | -14.95 (n=230) | -14.87 (n=245) | -6.93 (n=557) | -6.13 (n=82) |

## 2. Engine-admit decomposition (the stack delta = kept-row P&L)
| engine-admit decomposition ($/wk) | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| A0: floor-only rows avoided (floor kept them, variant did not) - their floor P&L removed | +4563 (n=21) | +2985 (n=74) | +2846 (n=84) | -431 (n=165) | +223 (n=87) |
| A0: variant-only rows admitted (re-entry in) - their variant P&L | +1984 (n=9) | +1785 (n=48) | +1208 (n=52) | +393 (n=83) | -24 (n=40) |
| A0: shared rows (entry at the close vs at the signal) = kept total - the two lines above | +731 | -1160 | -666 | -587 | -239 |
| A0: engine-kept trade sum = stack delta check | +7278 vs +5665 | +3610 vs +3569 | +3388 vs +3272 | -625 vs -425 | -41 vs -588 |
| C coded: floor-only rows avoided (floor kept them, variant did not) - their floor P&L removed | +4563 (n=21) | +2985 (n=74) | +2846 (n=84) | -342 (n=160) | +37 (n=89) |
| C coded: variant-only rows admitted (re-entry in) - their variant P&L | +1722 (n=9) | +1212 (n=47) | +711 (n=51) | -27 (n=83) | -31 (n=40) |
| C coded: shared rows (entry at the close vs at the signal) = kept total - the two lines above | +858 | -1099 | -821 | -695 | -170 |
| C coded: engine-kept trade sum = stack delta check | +7143 vs +5622 | +3098 vs +2920 | +2735 vs +2508 | -1064 vs -486 | -164 vs -480 |
| A70: floor-only rows avoided (floor kept them, variant did not) - their floor P&L removed | +2289 (n=2) | +1920 (n=11) | +1467 (n=12) | -292 (n=34) | -1036 (n=13) |
| A70: variant-only rows admitted (re-entry in) - their variant P&L | -189 (n=4) | +1088 (n=31) | +924 (n=33) | +739 (n=47) | -578 (n=10) |
| A70: shared rows (entry at the close vs at the signal) = kept total - the two lines above | +1330 | -644 | -311 | -373 | +1682 |
| A70: engine-kept trade sum = stack delta check | +3430 vs +3251 | +2365 vs +2334 | +2081 vs +1598 | +74 vs -1106 | +69 vs -418 |

## 3. Coded vs pure wait, paired
| coded minus pure wait | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| stack, N, $/wk (paired MDE) | -43 (981) | -649 (1817) | -763 (1711) | -61 (1259) | +108 (1835) |
| stack, LIVE-CAL | -150 (892) | -40 (443) | -236 (775) | -278 (1102) | +103 (1864) |
| coded gated (1-of-8) minus coded ungated, stack | -2 (32) | -20 (194) | -16 (170) | -112 (204) | -189 (442) |

## 4. LIVE-CAL
| LIVE-CAL stack delta vs floor, $/wk | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| A0 pure wait | +5772 (18392) | +2967 (7055) | +2766 (6433) | -266 (3519) | -832 (4495) |
| C coded | +5622 (17671) | +2928 (6944) | +2530 (6343) | -545 (3274) | -729 (4746) |
| A70 | +3296 (9897) | +2115 (5437) | +1394 (4854) | -1018 (2464) | -411 (2652) |

## 5. Notes
* Coded entry = ufe_kernel utrade with kin' = the confirmation fill sample and E' = its fill price (market close + 1 tick), stop at the ORIGINAL level, target re-based on the average, dip 3 pt from the entry (ungated, as the plain floor; gated beside). * The limit LEAD (cycle 10) is not re-scored here. * 2026 is ~5 weeks.
