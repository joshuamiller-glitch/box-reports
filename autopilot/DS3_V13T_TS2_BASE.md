# DS3_V13T_TS2_BASE - run_v13t_ts2: V13T_LIVE with the LIVE lot order (BASE-4, 2026-11-03T14:29Z); table only
**Definition (user answers from DS7.cs, DIRECTIVE_USER_20261103_SIZER_FINISH.md).** Lot order: session-table lots (LN x session share, lot_tables live11) -> A06 slot x0.5 (if the ENTRY ET half-hour is in the book's list) -> B02 x0.5 (K7/P7/H7 = KB/PE/HM, entry 10:30-17:59 ET, quiet-overnight day), both in ONE rounding floor(lots x mult + 0.5), min 1 -> ER ladder Q1-A (ER(20) >= 0.30 x1.0, < 0.30 x0.5, NaN x1; rounded, min 1) -> zone HALF floor(lots x 0.5 + 0.5), min 1 (LAST). Lock R scaled only when mult > 1 (Q1-A has none: the lock R is never scaled; with the old ladder 'L' the mult-1.5 days still scale it). Call: `T.run_v13t_ts2({'ladder': 'Q1A' | 'L' | 'off'})`; flags slot / b02 / zone_last for step tests; `lots_ts2.live_lots(ladder)` gives the integer lots per d row; lots_mult / add_mult / bracket / stack hooks work on ts2 (stack_expo.run_stack(cell, ladder='Q1A'|'L'|'off')).
**A06 lists** (ET half-hour of the entry): P7 (PE) 0330 0500 0830; K7 (KB) 0330 0400 0430 0500 0530 1430 1900 1930 2030 2100; H7 (HM) 0400 0530 0830 1030 1230 1300 1400 1830; U7 (SM) 0200 0830; M7 (MV) and A7 (PB): none; S7 not live. Source: the user's answer from DS7.cs (the directive); the entry time = the signal second (PE: the 45-s confirmation fill second), converted with DST. **B02:** at 10:30 ET the overnight range (18:00 -> 09:30 ET; max of the 1-s highs minus min of the 1-s lows of the continuous path) is compared with the median of the last 20 available overnight ranges: range < 0.85 x median = QUIET for that ET day, not re-evaluated.
**B02 flag verified** against the earlier STK_B label table (stk_b/labels.parquet ON_085, 774 label days to 2026-02-06, built from NQ bars independently of this path): my overnight range equals theirs on all 774 days (correlation 1.000, median ratio 1.000) and the QUIET flag agrees on 99.6% of days (3 of 774 differ; 36.3% vs 35.9% quiet days). 341 of 964 days with a valid overnight window are quiet over the whole history (35%).
## Flag census (live signals, and taken in ts2)
| book | live signals | A06 slot halving | B02 halving | both | taken in ts2: slot / B02 |
|---|---|---|---|---|---|
| PE | 6126 | 261 (4%) | 321 (5%) | 0 | 246 / 184 |
| KB | 8025 | 1462 (18%) | 803 (10%) | 92 | 1364 / 738 |
| HM | 3304 | 445 (13%) | 226 (7%) | 85 | 442 / 226 |
| SM | 1370 | 73 (5%) | 0 (0%) | 0 | 73 / 0 |
| MV | 3674 | 0 (0%) | 0 (0%) | 0 | 0 / 0 |
| PB | 5403 | 0 (0%) | 0 (0%) | 0 | 0 / 0 |

## Mean lots per book x session (all live signals): before = ts (old order, old ladder x0.5/x1.5), then ts2 with the ladder off, then ts2 Q1-A
| book | session | signals | session-table lots | ts (old order, ladder x0.5/x1.5) | ts2 with ladder off | ts2 Q1-A |
|---|---|---|---|---|---|---|
| PE | asia | 2189 | 7.00 | 6.62 | 6.57 | 4.98 |
| PE | london | 1689 | 7.00 | 6.91 | 6.28 | 4.79 |
| PE | nyam | 2248 | 7.00 | 6.41 | 6.44 | 4.66 |
| KB | asia | 2300 | 2.00 | 1.70 | 1.62 | 1.24 |
| KB | london | 1724 | 2.00 | 1.72 | 1.50 | 1.19 |
| KB | nyam | 2356 | 1.00 | 1.30 | 1.00 | 1.00 |
| KB | nypm | 1645 | 2.00 | 1.65 | 1.54 | 1.19 |
| HM | asia | 1818 | 4.00 | 3.14 | 3.42 | 2.36 |
| HM | nyam | 1486 | 1.00 | 1.36 | 1.00 | 1.00 |
| SM | asia | 690 | 4.00 | 3.96 | 3.49 | 2.85 |
| SM | london | 680 | 4.00 | 3.61 | 3.34 | 2.54 |
| MV | london | 1587 | 2.00 | 1.90 | 1.90 | 1.43 |
| MV | nyam | 2087 | 1.00 | 1.34 | 1.00 | 1.00 |
| PB | asia | 5403 | 1.00 | 1.70 | 1.00 | 1.00 |

## Step table: from ts to ts2 (each step cumulative; all T-SIZER base conventions, lock none)
| base | total $ | L6M mean / maxDD | HOLD | MID | PRE | X' | mean lots per taken signal |
|---|---|---|---|---|---|---|---|
| S0 ts (old order: session -> zone -> ER x0.5/x1.5) | 3,630k | 38.5k / 170k | 32.2k / 170k | 23.5k / 45k | 18.0k / 161k | 5.1k / 73k | 3.01 |
| S2 + zone HALF last (ER ladder x0.5/x1.5, no slot, no B02) | 3,650k | 38.5k / 166k | 32.3k / 166k | 23.6k / 45k | 18.1k / 161k | 5.2k / 75k | 3.00 |
| S3 + A06 slot x0.5 | 3,616k | 37.5k / 142k | 31.8k / 142k | 23.7k / 51k | 18.7k / 155k | 4.1k / 76k | 2.90 |
| S4 + B02 x0.5 (single rounding with the slot) | 3,542k | 37.6k / 143k | 31.7k / 143k | 23.7k / 43k | 18.0k / 148k | 4.1k / 97k | 2.87 |
| S5 ts2 = + ER ladder Q1-A (x1.0 / x0.5) | 2,520k | 27.0k / 105k | 22.6k / 122k | 16.9k / 60k | 13.2k / 88k | 3.3k / 81k | 2.14 |
| ref: ts2 with the ER ladder OFF (x1) | 2,557k | 27.0k / 83k | 21.9k / 192k | 5.8k / 128k | 14.2k / 112k | 3.8k / 144k | 2.72 |

**ts vs ts2 (the base delta):**
| window | mean $/wk ts -> ts2 | maxDD ts -> ts2 | worst-20 ts -> ts2 |
|---|---|---|---|
| L6M | 38.5k -> 27.0k (-11.5k) | 170.4k -> 104.8k (-65.6k) | 100k -> 91k |
| HOLD | 32.2k -> 22.6k (-9.6k) | 170.4k -> 122.0k (-48.4k) | -558k -> -390k |
| MID | 23.5k -> 16.9k (-6.6k) | 45.5k -> 59.7k (+14.2k) | -59k -> -64k |
| PRE | 18.0k -> 13.2k (-4.8k) | 160.7k -> 88.2k (-72.5k) | -823k -> -490k |
| X' | 5.1k -> 3.3k (-1.8k) | 72.8k -> 80.8k (+8.0k) | -445k -> -303k |

Whole-history total ts $3,630k -> ts2 $2,520k; mean lots per taken signal 3.01 -> 2.14.
## Tests
- IDENTITY (old order through the ts2 path: ladder L, slot off, B02 off, zone_last off, old governor): max |cube diff| vs run_v13t_ts = 0.0000 $.
- Every live row of the Q1-A run: engine lots (LN x m0) vs lots_ts2.live_lots('Q1A'): 0 mismatches of 27902.
- **W1 slot then B02, ONE rounding (ER ladder off to isolate)**: d-row 8249 (HM, nyam, label 20230428), session-table lots 1: x0.5 slot x0.5 B02 = floor(1 x 0.25 + 0.5) = 1 (two roundings would give 1); engine lots 1 -> **MATCH**
- **W2 ER ladder after the slot (Q1-A, ER 0.08 < 0.30 -> x0.5)**: d-row 34158 (KB, asia), session lots 2 -> slot 1 -> ER 1; engine 1 -> **MATCH**
- **W2b Q1-A ER >= 0.30 -> x1.0 (no boost)**: d-row 34448 (SM, london, ER 0.65), session lots 4 -> slot 2; engine 2 -> **MATCH**
- **W3 zone HALF last (the P7 7 -> 4 -> 2 case)**: d-row 41548 (PE, asia, ER 0.01, zone line active): session lots 7 -> ER x0.5 = floor(3.5+0.5) = 4 -> zone x0.5 = floor(2+0.5) = 2 (the old order gives zone 7 -> 4 -> ER 2.0 -> 2; here also 2); engine 2 -> **MATCH**
- **W3b zone HALF applies to the Q1-A lots**: d-row 40738 (PE, asia, ER 0.37 >= 0.30, zone): 7 x1.0 = 7 -> zone floor(7/2+0.5) = 4; engine 4 -> **MATCH**
- **W4 B02 only (quiet overnight), then ER x0.5**: d-row 30080 (KB, nypm, label 20250805); 2 -> B02 1 -> ER 1; engine 1 -> **MATCH**
- ALL worked rows MATCH.
- Note on W1: on the live session-table lots no row has a slot-then-B02 outcome that differs between ONE rounding and two successive roundings (the lots are 1, 2, 4, 7; e.g. 4 x 0.25 = 1 either way); a hypothetical 5-lot row would give floor(1.25+0.5) = 1 against floor(floor(2.5+0.5)=3 x 0.5 + 0.5) = 2. The single rounding is what the code does.
- HOOKS on ts2 (all at 0.0000 $ against the ts2 base): stack rule off (stack_expo.run_stack({}, 'Q1A')), add_mult = 1, add_only_if all True, bracket NaN arrays; stack_expo.run_stack(cell, ladder='Q1A'|'L'|'off') (cap12 on Q1-A converges in 3 passes); net_other_books('Q1A') saved to ds3_base4/net_other_books_Q1A.npy. The old True / False ladder arguments still mean the old ts base.
- Reading: the order change alone (zone last) is small (L6M maxDD 170k -> 166k); the A06 slot cuts L6M maxDD to 142k at a 1k/wk mean cost; B02 adds little in L6M and hurts X' (73k -> 97k); Q1-A (no x1.5) lowers the mean by about 30% (L6M 37.6k -> 27.0k/wk) and the maxDD to 105k (L6M) / 88k (PRE) while MID (+14k) and X' (+8k) get slightly deeper. Everything in the sizer program is to be re-stated against ts2 / Q1-A.
