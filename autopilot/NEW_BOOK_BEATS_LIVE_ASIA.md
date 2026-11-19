# NEW_BOOK_BEATS_LIVE_ASIA - does a new book beat the live Asia book(s) in the exact engine? (W-ASIA, order 0400Z), refreshed 2026-11-19 06:35Z

**vs TODAY's stack (JL3, today's DAY-DONE); Asia is decided FIRST; label BETTER = calibration pending, NOT calibrated.** Asia rule (higher bar, order 1731Z / 0210Z item 4): a REPLACE row (new book ON, the named live Asia book's Asia entries OFF) beats that live book only if on BOTH L6M and L3M the stack ulcer is LOWER (drawdown first) AND mean $/wk is not lower AND worst week and max drawdown are not worse; then prior years (no RED = >30% worse; AMBER shown), persistence > 0.60, 30 date-shift controls, calibration. du = d stack ulcer (negative = better), dm = d mean $/wk (base lots, $4.84 RT).

**Counts:** Asia cells with any engine row 102; cells with a finished REPLACE verdict (L6M+L3M landed) 16; cells that beat at least one live Asia book on L6M+L3M under the Asia rule (BETTER, calibration pending) 0 (under the looser NY rule 1); ADD rows finished 86.

| live Asia book replaced | cells finished | beat it | pending |
|---|---|---|---|
| K7 | 7 | 0 | 0 |
| P7 | 3 | 0 | 0 |
| A7 | 16 | 0 | 0 |
| H7 | 7 | 0 | 0 |
| U7 | 7 | 0 | 0 |

## Engine throughput and queue (Asia sets TL3_ASI_*)
Asia set-months landed: last 1 h 1388, last 3 h 3238; Asia queue lines pending (not DONE): 31620.

## Proof that Asia sets are launched ahead of NY AM
- QUEUES.txt order on server 2 dispatcher: _asi position 4, _nye/pending_l 11, _nye/pending_w , _lon 12 (lower = earlier).
- PRIORITY.txt admission order (TP admit, all hosts): NT > ASI > NYL > NYR > NYF > FR > NYE > NYW > LON > ME
- box1 running engine sets by tag: 32 TL3_NYW_      13 TL3_ASI_      10 TL3_LON_
- server2 running engine sets by tag: 44 TL3_ASI_
- A running engine sets by tag: 166 TL3_ASI_
- B running engine sets by tag: 187 TL3_ASI_

## Best five rows (drawdown first: most negative L6M du among cells with a finished REPLACE row)
| cell | ADD | REPLACE K7 | REPLACE P7 | REPLACE A7 | REPLACE H7 | REPLACE U7 | controls |
|---|---|---|---|---|---|---|---|
| AB6 trb_240 / levels_fib15.break_native {"n": 3, "k": 0.5} / plain60/60 / both | no (L6M du +335 dm +1217 | L3M du +511 dm -702) | no (L6M du +2242 dm -2808 | L3M du +3964 dm -6870) | not run | no (L6M du +49 dm +370 | L3M du +377 dm -199) | no (L6M du -296 dm -526 | L3M du -327 dm -1249) | no (L6M du -1396 dm -146 | L3M du -2236 dm -914) | 0 of 30 |
| AB4 mom_56 / trend_psar.flip {"af0": 0.02, "step": 0.03, "max": 0.2} / plain60/60 / both | no (L6M du -434 dm +1 | L3M du -1849 dm +1732 RED Y2025) | no (L6M du -429 dm -3696 | L3M du -584 dm -4368) | not run | no (L6M du -260 dm -1113 | L3M du -395 dm +1001 RED Y2025) | no (L6M du +1262 dm -1480 | L3M du +2231 dm -199 RED Y2025) | no (L6M du +1051 dm -2795 | L3M du -455 dm -1972) | 0 of 30 |
| L40bde9ea vsess_120 / momentum_mvote.v4of5_native {"scale": 1.0, "thr": 0.25} / plain60/60 / long | no (L6M du +510 dm +746 | L3M du -859 dm +2353) | not run | not run | no (L6M du -398 dm +679 | L3M du -813 dm +3433) | not run | not run | 0 of 30 |
| AB2 drb_400 / structure_orb.orb {"or_min": 5, "buf": 0.0} / plain60/60 / both | no (L6M du +250 dm +387 | L3M du +491 dm +369 RED Y2025) | no (L6M du +2017 dm -4391 | L3M du +3402 dm -6784 RED Y2025) | no (L6M du +6520 dm -10007 | L3M du +9814 dm -8871 RED Y2025,Y2023) | no (L6M du -271 dm -948 | L3M du -376 dm +14 RED Y2025) | no (L6M du -259 dm -648 | L3M du +243 dm -914 RED Y2025,Y2023) | no (L6M du +969 dm -2041 | L3M du +951 dm -1558 RED Y2025) | 0 of 30 |
| AB8 cusum_10 / momentum_cci.brk {"len": 30, "lvl": 200} / plain60/60 / both | no (L6M du +1498 dm -927 | L3M du +1563 dm -2352 RED Y2025) | no (L6M du -246 dm -2813 | L3M du +534 dm -5951) | not run | no (L6M du +1231 dm -600 | L3M du +1724 dm -1051) | no (L6M du -42 dm -1658 | L3M du -211 dm -1226 RED Y2025) | no (L6M du +241 dm -2218 | L3M du -523 dm -4307 RED Y2025) | 0 of 30 |

## Cells that beat a live Asia book (Asia rule, yes), drawdown first
| cell | ADD | REPLACE K7 | REPLACE P7 | REPLACE A7 | REPLACE H7 | REPLACE U7 | prior years run | controls |
|---|---|---|---|---|---|---|---|---|

## D8 gate (orders 0213Z, 0228Z)
Nothing enters D8 without the EXIT RUN (68 recipes) on its own entries. Candidates are appended to autopilot/D8_CANDIDATES.txt (append-only, session Asia). Engine cost after the exit screen for the 0 Asia cell(s) that beat a live book today: about 0 set-months (prior years + 30 controls + layers/exit rows ~1,723 per candidate).

All other cells: see /mnt/l2/l2vast/_asi_lad/beats_rows.csv (verdict per live book: no / pending). Asia ladder state: `python3 code/th_asia/asia_ladder.py status`.

