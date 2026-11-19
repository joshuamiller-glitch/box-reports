# NEW_BOOK_BEATS_LIVE_ASIA - does a new book beat the live Asia book(s) in the exact engine? (W-ASIA, order 0400Z), refreshed 2026-11-19 07:30Z

**vs TODAY's stack (JL3, today's DAY-DONE); Asia is decided FIRST; label BETTER = calibration pending, NOT calibrated.** Asia rule (higher bar, order 1731Z / 0210Z item 4): a REPLACE row (new book ON, the named live Asia book's Asia entries OFF) beats that live book only if on BOTH L6M and L3M the stack ulcer is LOWER (drawdown first) AND mean $/wk is not lower AND worst week and max drawdown are not worse; then prior years (no RED = >30% worse; AMBER shown), persistence > 0.60, 30 date-shift controls, calibration. du = d stack ulcer (negative = better), dm = d mean $/wk (base lots, $4.84 RT).

**Counts:** Asia cells with any engine row 210; cells with a finished REPLACE verdict (L6M+L3M landed) 88; cells that beat at least one live Asia book on L6M+L3M under the Asia rule (BETTER, calibration pending) 3 (under the looser NY rule 9); ADD rows finished 205.

| live Asia book replaced | cells finished | beat it | pending |
|---|---|---|---|
| K7 | 16 | 0 | 1 |
| P7 | 11 | 0 | 4 |
| A7 | 88 | 3 | 21 |
| H7 | 16 | 0 | 3 |
| U7 | 13 | 0 | 6 |

## Engine throughput and queue (Asia sets TL3_ASI_*)
Asia set-months landed: last 1 h 2186, last 3 h 4451; Asia queue lines pending (not DONE): 32095.

## Proof that Asia sets are launched ahead of NY AM
- QUEUES.txt order on server 2 dispatcher: _asi position 4, _nye/pending_l 11, _nye/pending_w , _lon 12 (lower = earlier).
- PRIORITY.txt admission order (TP admit, all hosts): NT > ASI > NYL > NYR > NYF > FR > NYE > NYW > LON > ME
- box1 running engine sets by tag: 32 TL3_NYE_      12 TL3_LON_      12 TL3_ASI_
- server2 running engine sets by tag: 34 TL3_ASI_
- A running engine sets by tag: 190 TL3_ASI_
- B running engine sets by tag: 196 TL3_ASI_

## Best five rows (drawdown first: most negative L6M du among cells with a finished REPLACE row)
| cell | ADD | REPLACE K7 | REPLACE P7 | REPLACE A7 | REPLACE H7 | REPLACE U7 | controls |
|---|---|---|---|---|---|---|---|
| AB6 trb_240 / levels_fib15.break_native {"n": 3, "k": 0.5} / plain60/60 / both | no (L6M du +335 dm +1217 | L3M du +511 dm -702) | no (L6M du +2242 dm -2808 | L3M du +3964 dm -6870) | not run | no (L6M du +49 dm +370 | L3M du +377 dm -199) | no (L6M du -296 dm -526 | L3M du -327 dm -1249) | no (L6M du -1396 dm -146 | L3M du -2236 dm -914) | 0 of 30 |
| Lda55d973 vol_750 / momentum_stoch.zone_break_native {"len": 9, "lvl": 80} / plain60/60 / long | yes (L6M du -1672 dm +2260 | L3M du -2265 dm +1965) | not run | not run | yes (L6M du -1222 dm +911 | L3M du -1416 dm +2143) | not run | not run | 0 of 30 |
| Leee81e35 vol_750 / bands_atrchan.break_ext {"n": 20, "atr": 14, "k": 2.0} / asym15u/30u / long | no (L6M du +1888 dm -1084 | L3M du -1129 dm -101) | not run | not run | no (L6M du -992 dm +1085 | L3M du -895 dm +1573) | not run | not run | 0 of 30 |
| L3ee2d289 vsess_50 / momentum_mvote.v3of5_native {"scale": 1.0, "thr": 0.25} / plain60/60 / long | no (L6M du +953 dm +862 | L3M du +1594 dm +907 RED Y2025) | no (L6M du +964 dm -2275 | L3M du +1442 dm -3776) | no (L6M du +5444 dm -8546 | L3M du +7875 dm -6391) | no (L6M du -307 dm +633 | L3M du -414 dm +2184) | no (L6M du -728 dm -61 | L3M du -811 dm +1385) | pending | 0 of 30 |
| L5c9e11b3 vol_750 / momentum_mvote.v3of5 {"scale": 0.25, "thr": 0.25} / plain60/60 / long | no (L6M du -815 dm +2152 | L3M du -1706 dm +3570) | not run | not run | yes (L6M du -603 dm +1062 | L3M du -1151 dm +3460) | not run | not run | 0 of 30 |

## Cells that beat a live Asia book (Asia rule, yes), drawdown first
| cell | ADD | REPLACE K7 | REPLACE P7 | REPLACE A7 | REPLACE H7 | REPLACE U7 | prior years run | controls |
|---|---|---|---|---|---|---|---|---|
| Lda55d973 vol_750 / momentum_stoch.zone_break_native {"len": 9, "lvl": 80} / plain60/60 / long | yes (L6M du -1672 dm +2260 | L3M du -2265 dm +1965) | not run | not run | yes (L6M du -1222 dm +911 | L3M du -1416 dm +2143) | not run | not run | K7:0,P7:0,A7:0,H7:0,U7:0 | 0 of 30 |
| L5c9e11b3 vol_750 / momentum_mvote.v3of5 {"scale": 0.25, "thr": 0.25} / plain60/60 / long | no (L6M du -815 dm +2152 | L3M du -1706 dm +3570) | not run | not run | yes (L6M du -603 dm +1062 | L3M du -1151 dm +3460) | not run | not run | K7:0,P7:0,A7:0,H7:0,U7:0 | 0 of 30 |
| Ledfbf4d2 vol_350 / bands_bollinger.break_native {"clk": 20, "k": 1.5} / plain60/60 / long | no (L6M du -813 dm +880 | L3M du -949 dm +64) | not run | not run | yes (L6M du -459 dm +384 | L3M du -548 dm +1331) | not run | not run | K7:0,P7:0,A7:0,H7:0,U7:0 | 0 of 30 |

## D8 gate (orders 0213Z, 0228Z)
Nothing enters D8 without the EXIT RUN (68 recipes) on its own entries. Candidates are appended to autopilot/D8_CANDIDATES.txt (append-only, session Asia). Engine cost after the exit screen for the 3 Asia cell(s) that beat a live book today: about 5169 set-months (prior years + 30 controls + layers/exit rows ~1,723 per candidate).

All other cells: see /mnt/l2/l2vast/_asi_lad/beats_rows.csv (verdict per live book: no / pending). Asia ladder state: `python3 code/th_asia/asia_ladder.py status`.

