# DS3_NEAR_ZONE - T-NEAR-ZONE: "dont be a dick for a tick" (page written Thu Nov 12 09:24:13 AM UTC 2026)

STATUS: Shadow only, post-hoc, no PASS claims (PASS/FAIL below is the trader acceptance test of the order, nothing more). Evidence table: DS3_NEAR_ZONE_TABLE.md (published 19:33Z, before any rule). Prereg NEAR_ZONE_PREREG.md (sha in DECISIONS.md). FIRST-ORDER scores on the LPB_BASE stored 1-s paths (43 months; L6M = 2026-05-12..10-30), slip 1.2 market, fees 4.84/lot, base = live panel rules as in LPB_BASE; exact rows in section 6. P7 is run at 12/7/7 lots (P7x, the users lots) and on the installed 7/4/4 table. Objective: give-back $ removed minus fills clipped $ per week; key = min(L6M, 43 months) net $/wk. Standing trader principle (19:45Z) applied: scorecard items a, b, e below, c and d (re-entry streaks) are untouched by exit-side rules in this first-order frame and are W-Qs tool to confirm.

**Fill models (stated; profit side unmeasured).** market = mid at the next second minus 1.2 pt (central; REDO-R9 low 0.57 / high 1.6 not re-run); resting stop-limit floor (mode=1) = fills at the floor minus 0.25 pt if the 1-s mid did not gap more than 1.5 pt through it, else market at the next second: OPTIMISTIC (no queue / partial-fill loss), so every mode=1, limit and work row is an upper bound and the market rows are the base case; passive limit (bank, work-the-exit) = fills at price minus 0.25 only if a later mid trades through it by one tick within the wait, else market at the end of the wait. Engine market exits are about 0.4 pt cheaper than live (1.2 pt adverse, DS3_DN_STOPFILL); code/th_ptr/market_slip.json is not on the box so REDO-R9 1.2 is used; the profit-side take slip is unmeasured. Floors act on a 1-s mid; a gap inside one second is not seen.

**Placebo / family null.** forward-only time-shift placebo (every cell fires as before but exits a random 10-300 s later, 12 reps); p_plc = share of reps with key >= the cell, p_fam = share of reps where the best cell of the same family reaches it (family g = top-150 combos only, p_fam optimistic there). With 12 reps the smallest p is 0.08: read p <= 0.10 as the floor.

## Summary (plain sentences; FIRST-ORDER, exact pending)

| book | strict trader-PASS rule (v1.7 line or v1.8 description) | net $/wk L6M (all fires) | removed / clipped $/wk L6M (zone) ; removed-clipped ; other saves | clipped fills/wk | trend weeks (5 best L6M) delta $ | live week delta $ (week total) | p_plc / p_fam | verdict |
|---|---|---|---|---|---|---|---|---|
| P7 at 12/7/7 lots | flow pulled_against_mult>=5 arm=0.7 persist=1 dd>=0 | 3,165 | 21,417 / 34,269 ; -12,852 ; 16,017 | 18.7 | -66,777 | -29,838 (103,596) | 0.00 / 1.00 | keeps all 5 best weeks positive; passes only by taking early (arm 0.7) - it clips fills |
| P7 at 7/4/4 lots (installed) | flow pulled_against_mult>=5 arm=0.7 persist=1 dd>=0 | 1,831 | 12,401 / 19,848 ; -7,447 ; 9,278 | 18.7 | -34,383 | -17,199 (103,596) | 0.00 / 1.00 | keeps all 5 best weeks positive; passes only by taking early (arm 0.7) - it clips fills |
| K7 | flow delta_mult>=2 arm=0.8 persist=1 dd>=0 | -776 | 6,916 / 7,692 ; -776 ; 0 | 25.0 | -12,612 | 2,172 (103,596) | 1.00 / 1.00 | keeps all 5 best weeks positive; passes only by taking early (arm 0.7) - it clips fills |
| M7 | flow pulled_mult>=5 arm=0.7 persist=3 dd>=0 | 513 | 3,745 / 5,736 ; -1,991 ; 2,504 | 13.8 | -2,949 | -3,616 (103,596) | 0.17 / 1.00 | keeps all 5 best weeks positive; passes only by taking early (arm 0.7) - it clips fills |
| U7 | flow pulled_mult>=5 arm=0.7 persist=5 dd>=0 | 152 | 3,489 / 5,334 ; -1,845 ; 1,997 | 5.6 | -25,433 | -785 (103,596) | 0.00 / 1.00 | keeps all 5 best weeks positive; passes only by a narrow rule |
| H7 | rev arm=0.8 X=4 N=5 | 152 | 1,444 / 1,293 ; 152 ; 0 | 2.5 | -4,704 | -303 (103,596) | 0.17 / 0.42 | keeps all 5 best weeks positive; passes only by a narrow rule |
| A7 | flow delta_mult>=2 arm=0.8 persist=3 dd>=0 | -446 | 1,140 / 1,585 ; -446 ; -0 | 5.7 | -6,590 | 2,597 (103,596) | 0.33 / 1.00 | keeps all 5 best weeks positive; passes only by a narrow rule |
| O7 | flow pulled_against_mult>=20 arm=0.8 persist=3 dd>=2 | -17 | 137 / 155 ; -17 ; 0 | 0.3 | -1,078 | 0 (103,596) | 0.00 / 1.00 | keeps all 5 best weeks positive; passes only by a narrow rule |

Reading: no rule family removes the give-backs without clipping fills. The strict trader test (nothing that reached 90% closes below 50%, nothing that reached 80% closes at or below breakeven) is only met by rules that fire early and often (arm 0.7); on P7 that removes about 50 L6M give-backs and clips about 450 fills, positive net in L6M only because of other saves (removed minus clipped is negative), and negative net in the oldest window, and for P7, K7, M7, A7 and O7 the family-null p is about 1 (a randomly delayed copy of the same rule family does as well), so those strict-pass finalists are NOT evidence of an edge, they are the price list; only the U7 and H7 combinations separate from the delay placebo (p_fam 0 and 0.4) and they are small books. The honest per-book answer is the first-order frontier in section tables: where net is positive and the stack cut is large (P7 ladders and flow rules), the cost shows in the five best trend weeks.

## Exact status and processes

Exact sets built (private nz_hooks for floor/ladder/rev/bank/work/zone; ptr_hooks grammar lines for flow and plain takes; fill models as above, exact market slip 1.2): 23 sets, 191 of 859 set-months DONE. Identity gate PASSED 22:41Z: PTR_NZ_ID (nz_hooks, no cells) vs LPB_BASE 202610, 769 trades, bit-equal on book/lots/entry/exit/net_fee for ref engine, TP engine and the stored LPB_BASE run (code/th_nz/nz_idtest.py; TP wall 96 s vs old path 159 s, private memory 0.4 GB vs ~10.8 GB per worker per W-T). Chain (pid 2335696, log /mnt/l2/l2vast/_nz/exact_chain.log) now launches workers itself as `TP_ENGINE=1 python3 -I code/th_tp/tp_launch.py sz_exact.py batch SET:ym`, one set per job, max 3 workers, admission via `tp_admit.py request NEARZONE --gate 25` (PRIORITY.txt NEARZONE regex extended with PTR_[A-Z0-9]+_NZ), L6M first then HOLD, PRE. Throughput: see `tp_admit.py rate` (cell-months/hour; before TP this chain had 0 because of the 62 GB gate). Manifest /mnt/l2/l2vast/_nz/exact_manifest.json. Page refresh loop pid 2179089 (every 4 h to 2026-11-12 12:00Z).

## Families h-q (user addendum 21:45Z), first-order, same objective and definitions

Definitions as in the block above: net = removed - clipped + other saves (per week; L6M 24 weeks, 43 months). Extra inputs for these families come from the 1-s state tape: per-second printed high/low (H/LO), resting size at the target level / MedLevel (QM, NaN when the level is beyond the top 10), the 30 min after a Target fill (runner), ATR14 of 1-min mid ranges, levels PDH/PDL/PWH/PWL/ONH/ONL from the real mids, 00/50 levels. Passive limits fill at price minus 0.25 only when a later second printed one tick THROUGH the price (queue-conservative; no partial fills). VWAP+-2 sigma and naked POC levels are NOT scored (no VWAP/profile series on the box). Not done for h-q: the live-week replay and the forward placebo (the live paths carry no print extremes; a time-shifted passive limit has no defined placebo) - read these rows as screens; exact needs engine order-level hooks (v1.8 actions below). Table reading: a row with no (pass) twin means NO cell of that family meets the strict trader test (v90 = 0 and v80 = 0 on L6M) on that book. Runner (n): the extra captured beyond the target on trades that filled is d > 0 on a base fill, so it shows as a NEGATIVE clipped number (a gain), and the strict test cannot improve because the runner does not touch the give-back trades. For m the passive limits at 80-95% of target fill at the limit (nominal), the remainder keeps the live outcome unless re-floored. Family i is scored from the resting size at the target level when it is inside the top 10 (about 70% of seconds).

### h. Touched-not-filled: how often, and what those trades did next (live-rule trades whose price printed the target level or within j ticks and that did not fill)

| book | window | level | trades touched-not-filled | per week | of trades that reached it | closed <= breakeven | $ per week (what they did) | mean $/lot | live exits |
|---|---|---|---|---|---|---|---|---|---|
| A7 | L6M | printed >= target | 0 | 0.00 | 1 | 0 | 0 | 0 | {'StateCut': None, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| A7 | L6M | printed >= T-1 tick | 1 | 0.04 | 23 | 1 | -26 | -627 | {'StateCut': 1.0, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| A7 | L6M | printed >= T-2 ticks | 1 | 0.04 | 40 | 1 | -26 | -627 | {'StateCut': 1.0, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| A7 | 43m | printed >= target | 0 | 0.00 | 2 | 0 | 0 | 0 | {'StateCut': None, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| A7 | 43m | printed >= T-1 tick | 2 | 0.01 | 106 | 2 | -10 | -904 | {'StateCut': 1.0, 'Stop': 1.0, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| A7 | 43m | printed >= T-2 ticks | 3 | 0.02 | 176 | 3 | -12 | -720 | {'StateCut': 1.0, 'Stop': 1.0, 'StackCut': 1.0, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| H7 | L6M | printed >= target | 0 | 0.00 | 1 | 0 | 0 | 0 | {'StateCut': None, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| H7 | L6M | printed >= T-1 tick | 0 | 0.00 | 8 | 0 | 0 | 0 | {'StateCut': None, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| H7 | L6M | printed >= T-2 ticks | 1 | 0.04 | 17 | 1 | -42 | -1036 | {'StateCut': None, 'Stop': None, 'StackCut': 1.0, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| H7 | 43m | printed >= target | 0 | 0.00 | 7 | 0 | 0 | 0 | {'StateCut': None, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| H7 | 43m | printed >= T-1 tick | 2 | 0.01 | 89 | 2 | -13 | -918 | {'StateCut': 1.0, 'Stop': 1.0, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| H7 | 43m | printed >= T-2 ticks | 4 | 0.02 | 155 | 4 | -23 | -890 | {'StateCut': 1.0, 'Stop': 1.0, 'StackCut': 2.0, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| K7 | L6M | printed >= target | 0 | 0.00 | 4 | 0 | 0 | 0 | {'StateCut': None, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| K7 | L6M | printed >= T-1 tick | 2 | 0.08 | 79 | 2 | -84 | -665 | {'StateCut': 1.0, 'Stop': None, 'StackCut': None, 'BookLock': 1.0, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| K7 | L6M | printed >= T-2 ticks | 3 | 0.12 | 148 | 3 | -109 | -649 | {'StateCut': 2.0, 'Stop': None, 'StackCut': None, 'BookLock': 1.0, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| K7 | 43m | printed >= target | 0 | 0.00 | 20 | 0 | 0 | 0 | {'StateCut': None, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| K7 | 43m | printed >= T-1 tick | 10 | 0.05 | 410 | 9 | -48 | -705 | {'StateCut': None, 'Stop': None, 'StackCut': 1.0, 'BookLock': None, 'TimeBlock': 3.0, 'StopJoinFallback': None, 'StopJoin': 4.0} |
| K7 | 43m | printed >= T-2 ticks | 20 | 0.11 | 750 | 15 | -65 | -508 | {'StateCut': None, 'Stop': None, 'StackCut': 2.0, 'BookLock': None, 'TimeBlock': 6.0, 'StopJoinFallback': None, 'StopJoin': 6.0} |
| M7 | L6M | printed >= target | 2 | 0.08 | 8 | 2 | -111 | -677 | {'StateCut': 2.0, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| M7 | L6M | printed >= T-1 tick | 4 | 0.16 | 39 | 4 | -213 | -733 | {'StateCut': 4.0, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| M7 | L6M | printed >= T-2 ticks | 5 | 0.20 | 65 | 5 | -246 | -746 | {'StateCut': 5.0, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| M7 | 43m | printed >= target | 2 | 0.01 | 17 | 2 | -15 | -677 | {'StateCut': 2.0, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| M7 | 43m | printed >= T-1 tick | 6 | 0.03 | 245 | 6 | -37 | -763 | {'StateCut': 6.0, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| M7 | 43m | printed >= T-2 ticks | 12 | 0.06 | 428 | 12 | -75 | -819 | {'StateCut': 10.0, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': 2.0} |
| O7 | L6M | printed >= target | 0 | 0.00 | 0 | 0 | 0 | 0 | {'StateCut': None, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| O7 | L6M | printed >= T-1 tick | 0 | 0.00 | 1 | 0 | 0 | 0 | {'StateCut': None, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| O7 | L6M | printed >= T-2 ticks | 0 | 0.00 | 1 | 0 | 0 | 0 | {'StateCut': None, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| O7 | 43m | printed >= target | 0 | 0.00 | 0 | 0 | 0 | 0 | {'StateCut': None, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| O7 | 43m | printed >= T-1 tick | 0 | 0.00 | 16 | 0 | 0 | 0 | {'StateCut': None, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| O7 | 43m | printed >= T-2 ticks | 1 | 0.01 | 29 | 0 | 5 | 874 | {'StateCut': None, 'Stop': None, 'StackCut': None, 'BookLock': 1.0, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| P7 | L6M | printed >= target | 2 | 0.08 | 49 | 2 | -83 | -449 | {'StateCut': 1.0, 'Stop': None, 'StackCut': None, 'BookLock': 1.0, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| P7 | L6M | printed >= T-1 tick | 2 | 0.08 | 91 | 2 | -83 | -449 | {'StateCut': 1.0, 'Stop': None, 'StackCut': None, 'BookLock': 1.0, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| P7 | L6M | printed >= T-2 ticks | 3 | 0.12 | 134 | 3 | -223 | -584 | {'StateCut': 2.0, 'Stop': None, 'StackCut': None, 'BookLock': 1.0, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| P7 | 43m | printed >= target | 11 | 0.06 | 182 | 11 | -139 | -826 | {'StateCut': 10.0, 'Stop': None, 'StackCut': None, 'BookLock': 1.0, 'TimeBlock': None, 'StopJoinFallback': None, 'StopJoin': None} |
| P7 | 43m | printed >= T-1 tick | 14 | 0.08 | 407 | 14 | -188 | -806 | {'StateCut': 11.0, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': 1.0, 'StopJoin': 1.0} |
| P7 | 43m | printed >= T-2 ticks | 21 | 0.11 | 654 | 20 | -284 | -773 | {'StateCut': 17.0, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': 1.0, 'StopJoinFallback': 1.0, 'StopJoin': None} |
| U7 | L6M | printed >= target | 1 | 0.04 | 7 | 1 | -96 | -1176 | {'StateCut': None, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': 1.0, 'StopJoin': None} |
| U7 | L6M | printed >= T-1 tick | 1 | 0.04 | 19 | 1 | -96 | -1176 | {'StateCut': None, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': 1.0, 'StopJoin': None} |
| U7 | L6M | printed >= T-2 ticks | 1 | 0.04 | 28 | 1 | -96 | -1176 | {'StateCut': None, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': 1.0, 'StopJoin': None} |
| U7 | 43m | printed >= target | 1 | 0.01 | 42 | 1 | -13 | -1176 | {'StateCut': None, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': 1.0, 'StopJoin': None} |
| U7 | 43m | printed >= T-1 tick | 1 | 0.01 | 115 | 1 | -13 | -1176 | {'StateCut': None, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': 1.0, 'StopJoin': None} |
| U7 | 43m | printed >= T-2 ticks | 1 | 0.01 | 181 | 1 | -13 | -1176 | {'StateCut': None, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': None, 'StopJoinFallback': 1.0, 'StopJoin': None} |
| ALLBOOKS | L6M | printed >= target | 5 | 0.20 | 70 | 5 | -290 | -686 | {'StateCut': 3.0, 'Stop': None, 'StackCut': None, 'BookLock': 1.0, 'TimeBlock': None, 'StopJoinFallback': 1.0, 'StopJoin': None} |
| ALLBOOKS | L6M | printed >= T-1 tick | 10 | 0.41 | 260 | 10 | -502 | -697 | {'StateCut': 7.0, 'Stop': None, 'StackCut': None, 'BookLock': 2.0, 'TimeBlock': None, 'StopJoinFallback': 1.0, 'StopJoin': None} |
| ALLBOOKS | L6M | printed >= T-2 ticks | 14 | 0.57 | 433 | 14 | -742 | -733 | {'StateCut': 10.0, 'Stop': None, 'StackCut': None, 'BookLock': 2.0, 'TimeBlock': None, 'StopJoinFallback': 1.0, 'StopJoin': None} |
| ALLBOOKS | 43m | printed >= target | 14 | 0.08 | 270 | 14 | -167 | -830 | {'StateCut': 12.0, 'Stop': None, 'StackCut': None, 'BookLock': 1.0, 'TimeBlock': None, 'StopJoinFallback': 1.0, 'StopJoin': None} |
| ALLBOOKS | 43m | printed >= T-1 tick | 35 | 0.19 | 1388 | 34 | -309 | -792 | {'StateCut': 20.0, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': 3.0, 'StopJoinFallback': None, 'StopJoin': 5.0} |
| ALLBOOKS | 43m | printed >= T-2 ticks | 62 | 0.33 | 2373 | 55 | -466 | -681 | {'StateCut': 31.0, 'Stop': None, 'StackCut': None, 'BookLock': None, 'TimeBlock': 7.0, 'StopJoinFallback': None, 'StopJoin': 9.0} |

Reading: a target that printed (or printed within 1 tick) and did not fill is rare in the stored lists (all books about 0.4 per week at T-1 tick in L6M) but every one of them then closed at or below breakeven (live exits are loss cuts / stops / book locks), about -$700 per lot per case. The live M7 one-tick miss is a real pattern but a small one; the h rules below price how much of it a 0-5 s inside exit recovers and what they cost on trades that would have filled.

### P7 12/7/7

| fam | rule | key | net L6M | removed (zone) | clipped | other | clipped fills/wk | GB/wk before>after | RT/wk before>after | strict test v90/v80 (live rules b90/b80) | stack cut L6M/HOLD/PRE/X' % |
|---|---|---|---|---|---|---|---|---|---|---|---|
| h  | touched-not-filled: printed >= T-4 tick(s), hit inside after 0 s, slip 0.25 | 1530 | 5290 | 4357 | -933 | 0 | 7.3 | 2.0 > 1.7 | 2.0 > 1.6 | 17/40 (24/50) | 16.5/16.2/9.3/-0.7 |
| i  | queue step-in: arm=0.8 queue>=1x Med -> limit T-2 tick | 1061 | 1780 | 602 | -1177 | 0 | 1.6 | 2.0 > 2.0 | 2.0 > 2.0 | 23/49 (24/50) | 7.2/7.2/-0.3/6.7 |
| m  | staggered 1/3 at 0.8, 1/3 at 0.9, 1/3 at 100% floors off/0.9 | 3684 | 8320 | 16345 | 9130 | 1104 | 15.4 | 2.0 > 1.0 | 2.0 > 1.0 | 4/25 (24/50) | 21.5/13.0/26.8/30.7 |
| n  | runner 0.50 of lots, trail pts 25, floor 1 T | 1122 | 3333 | 0 | -3333 | 0 | 19.2 | 2.0 > 2.0 | 2.0 > 2.0 | 24/50 (24/50) | 1.8/1.8/11.1/-4.2 |
| o  | level target all m=0.7: target = level - 2 ticks | 871 | 2993 | 10025 | 7844 | 812 | 7.9 | 2.0 > 1.2 | 2.0 > 1.2 | 14/29 (24/50) | 31.2/7.8/14.7/-4.3 |
| p  | noise floor arm=0.9: ext - 0.75 x ATR14(1m) | 494 | 3123 | 10655 | 7532 | -0 | 6.1 | 2.0 > 1.1 | 2.0 > 1.1 | 2/27 (24/50) | 20.1/4.8/8.6/24.9 |
| q  | arrival: fast<=150s mid slow>600s floors 0.8/0.8/0.8 | 445 | 1010 | 22295 | 21285 | 0 | 15.9 | 2.0 > 0.1 | 2.0 > 0.0 | 3/1 (24/50) | 11.3/3.3/22.3/13.0 |
| j  | move-target to wall-1: arm=0.8 wall_ahead[20]>=3 persist=1 | 2001 | 5365 | 12468 | 7103 | 0 | 14.7 | 2.0 > 1.2 | 2.0 > 1.0 | 10/24 (24/50) | 32.9/17.1/3.6/6.8 |

### P7 7/4/4

| fam | rule | key | net L6M | removed (zone) | clipped | other | clipped fills/wk | GB/wk before>after | RT/wk before>after | strict test v90/v80 (live rules b90/b80) | stack cut L6M/HOLD/PRE/X' % |
|---|---|---|---|---|---|---|---|---|---|---|---|
| h  | touched-not-filled: printed >= T-4 tick(s), hit inside after 0 s, slip 0.25 | 893 | 3069 | 2512 | -557 | 0 | 7.3 | 2.0 > 1.7 | 2.0 > 1.6 | 17/40 (24/50) | 14.9/4.1/10.1/1.4 |
| i  | queue step-in: arm=0.8 queue>=1x Med -> limit T-2 tick | 617 | 1040 | 351 | -688 | 0 | 1.6 | 2.0 > 2.0 | 2.0 > 2.0 | 23/49 (24/50) | 5.9/4.9/2.6/5.6 |
| m  | staggered 1/3 at 0.8, 1/3 at 0.9, 1/3 at 100% floors off/0.9 | 1721 | 4973 | 8395 | 4002 | 580 | 11.6 | 2.0 > 1.3 | 2.0 > 1.2 | 9/30 (24/50) | 18.9/-4.6/17.4/24.1 |
| n  | runner 0.50 of lots, trail pts 25, floor 1 T | 1225 | 2555 | 0 | -2555 | 0 | 16.0 | 2.0 > 2.0 | 2.0 > 2.0 | 24/50 (24/50) | 4.5/5.3/16.4/4.3 |
| o  | level target all m=0.7: target = level - 2 ticks | 510 | 1745 | 5810 | 4538 | 473 | 7.9 | 2.0 > 1.2 | 2.0 > 1.2 | 14/29 (24/50) | 28.5/-2.5/14.3/2.3 |
| p  | noise floor arm=0.9: ext - 0.75 x ATR14(1m) | 289 | 1817 | 6182 | 4365 | 0 | 6.1 | 2.0 > 1.1 | 2.0 > 1.1 | 2/27 (24/50) | 25.6/-4.9/3.9/21.9 |
| q  | arrival: fast<=150s mid slow>600s floors 0.8/0.8/0.8 | 269 | 591 | 12913 | 12321 | 0 | 15.9 | 2.0 > 0.1 | 2.0 > 0.0 | 3/1 (24/50) | 8.2/-6.1/16.3/11.6 |
| j  | move-target to wall-1: arm=0.8 wall_ahead[20]>=3 persist=1 | 1171 | 3134 | 7227 | 4093 | 0 | 14.7 | 2.0 > 1.2 | 2.0 > 1.0 | 10/24 (24/50) | 33.2/4.9/1.4/6.0 |

### K7

| fam | rule | key | net L6M | removed (zone) | clipped | other | clipped fills/wk | GB/wk before>after | RT/wk before>after | strict test v90/v80 (live rules b90/b80) | stack cut L6M/HOLD/PRE/X' % |
|---|---|---|---|---|---|---|---|---|---|---|---|
| h  | touched-not-filled: printed >= T-1 tick(s), hit inside after 0 s, slip 0.25 | -8 | 40 | 219 | 179 | -0 | 2.5 | 3.2 > 3.1 | 3.2 > 3.1 | 34/76 (36/78) | -0.4/-0.2/-0.8/-0.5 |
| i  | queue step-in: arm=0.8 queue>=3x Med -> limit T-2 tick | 0 | 0 | 0 | -0 | 0 | 0.0 | 3.2 > 3.2 | 3.2 > 3.2 | 36/78 (36/78) | 0.0/-0.0/-0.0/0.0 |
| m  | staggered 1/2 at 0.95 + 1/2 at 100% floor-after 0.6 | 89 | 686 | 955 | 269 | 0 | 3.0 | 3.2 > 2.9 | 3.2 > 2.9 | 30/72 (36/78) | -0.5/1.5/-0.6/2.5 |
| n  | runner 0.33 of lots, trail pts 8, floor 1 T | -64 | -64 | 0 | 64 | 0 | 4.9 | 3.2 > 3.2 | 3.2 > 3.2 | 36/78 (36/78) | -0.5/0.0/-0.3/0.1 |
| o  | level target round m=0.9: target = level - 2 ticks | -4 | 15 | 231 | 216 | -0 | 1.9 | 3.2 > 3.1 | 3.2 > 3.1 | 35/76 (36/78) | -0.7/-0.2/1.6/-0.4 |
| p  | noise floor arm=0.9: ext - 3 x ATR14(1m) | -226 | 236 | 1864 | 1627 | 0 | 2.2 | 3.2 > 4.2 | 3.2 > 2.3 | 60/56 (36/78) | -1.1/1.0/-3.3/3.0 |
| q  | arrival: fast<=180s mid slow>300s floors 0.4/0.6/0.4 | -639 | -146 | 5036 | 5182 | 0 | 5.9 | 3.2 > 8.7 | 3.2 > 0.0 | 172/1 (36/78) | 8.5/0.3/10.2/6.6 |
| j  | move-target to wall-1: arm=0.9 wall_ahead[4]>=12 persist=3 | -10 | 245 | 707 | 463 | -0 | 0.9 | 3.2 > 3.3 | 3.2 > 3.0 | 39/73 (36/78) | -0.3/0.9/-1.1/-3.4 |

### M7

| fam | rule | key | net L6M | removed (zone) | clipped | other | clipped fills/wk | GB/wk before>after | RT/wk before>after | strict test v90/v80 (live rules b90/b80) | stack cut L6M/HOLD/PRE/X' % |
|---|---|---|---|---|---|---|---|---|---|---|---|
| h  | touched-not-filled: printed >= T-2 tick(s), hit inside after 0 s, slip 0.25 | 64 | 469 | 611 | 142 | 0 | 2.0 | 1.9 > 1.7 | 1.9 > 1.7 | 19/42 (23/47) | -0.3/1.8/-0.5/-0.9 |
| i  | queue step-in: arm=0.8 queue>=1x Med -> limit T-2 tick | 45 | 285 | 304 | 19 | 0 | 0.9 | 1.9 > 1.8 | 1.9 > 1.8 | 21/45 (23/47) | -0.0/2.0/-0.1/-0.2 |
| m  | staggered 1/2 at 0.95 + 1/2 at 100% floor-after 0.7 | 89 | 700 | 847 | 147 | 0 | 1.5 | 1.9 > 1.7 | 1.9 > 1.7 | 18/41 (23/47) | 4.5/0.0/-1.1/-1.0 |
| n  | runner 0.33 of lots, trail pts 8, floor 1 T | -102 | -102 | 0 | 102 | 0 | 2.3 | 1.9 > 1.9 | 1.9 > 1.9 | 23/47 (23/47) | -0.3/-0.3/-0.5/-0.4 |
| o  | level target round m=0.9: target = level - 2 ticks | 12 | 225 | 287 | 62 | 0 | 0.7 | 1.9 > 1.8 | 1.9 > 1.8 | 20/44 (23/47) | 2.1/-0.5/-0.4/1.0 |
| p  | noise floor arm=0.9: ext - 3 x ATR14(1m) | 40 | 361 | 1202 | 841 | 0 | 1.0 | 1.9 > 2.4 | 1.9 > 1.2 | 34/30 (23/47) | 3.3/-0.4/-2.4/-6.0 |
| q  | arrival: fast<=180s mid slow>300s floors 0.8/0.6/0.4 | -148 | 269 | 3014 | 2745 | 0 | 3.7 | 1.9 > 3.9 | 1.9 > 0.0 | 76/0 (23/47) | 6.8/1.7/-5.5/-7.7 |
| j  | move-target to wall-1: arm=0.9 wall_ahead[20]>=6 persist=3 | 109 | 450 | 810 | 360 | 0 | 1.4 | 1.9 > 1.8 | 1.9 > 1.6 | 20/38 (23/47) | -0.1/-1.1/-4.5/-2.1 |

### U7

| fam | rule | key | net L6M | removed (zone) | clipped | other | clipped fills/wk | GB/wk before>after | RT/wk before>after | strict test v90/v80 (live rules b90/b80) | stack cut L6M/HOLD/PRE/X' % |
|---|---|---|---|---|---|---|---|---|---|---|---|
| h  | touched-not-filled: printed >= T-0 tick(s), hit inside after 0 s, slip 0.25 | 14 | 171 | 191 | 20 | 0 | 0.1 | 0.7 > 0.6 | 0.7 > 0.6 | 3/15 (4/16) | -0.3/-0.4/0.0/0.0 |
| i  | queue step-in: arm=0.8 queue>=30x Med -> limit T-1 tick | 0 | 0 | 0 | -0 | 0 | 0.0 | 0.7 > 0.7 | 0.7 > 0.7 | 4/16 (4/16) | 0.0/0.0/0.0/0.0 |
| m  | staggered 1/2 at 0.75 + 1/2 at 100% floor-after off | 148 | 453 | 1779 | 1918 | 593 | 4.8 | 0.7 > 0.7 | 0.7 > 0.5 | 6/11 (4/16) | 8.7/-0.6/7.0/2.4 |
| m (pass) | staggered 1/2 at 0.75 + 1/2 at 100% floor-after 0.8 | 144 | 591 | 3547 | 4119 | 1163 | 4.8 | 0.7 > 0.0 | 0.7 > 0.0 | 0/0 (4/16) | 16.7/-1.5/13.6/1.1 |
| n  | runner 0.50 of lots, trail xATR 5, floor 1 T | 84 | 174 | 0 | -174 | 0 | 4.9 | 0.7 > 0.7 | 0.7 > 0.7 | 4/16 (4/16) | -0.1/2.0/1.8/0.9 |
| o  | level target all m=0.9: target = level - 2 ticks | 4 | 60 | 200 | 140 | 0 | 0.4 | 0.7 > 0.6 | 0.7 > 0.6 | 3/15 (4/16) | -0.4/-0.3/-0.1/2.4 |
| p  | noise floor arm=0.7: ext - 1 x ATR14(1m) | 2 | 809 | 3168 | 4091 | 1731 | 3.2 | 0.7 > 0.6 | 0.7 > 0.0 | 13/0 (4/16) | 13.2/-11.0/18.7/-2.6 |
| q  | arrival: fast<=150s mid slow>600s floors 0.8/0.6/0.8 | -278 | 417 | 3479 | 3063 | 0 | 4.1 | 0.7 > 0.0 | 0.7 > 0.0 | 1/0 (4/16) | 10.0/0.6/14.5/-3.2 |
| q (pass) | arrival: fast<=150s mid slow>600s floors 0.8/0.8/0.8 | -285 | 354 | 3593 | 3239 | 0 | 4.6 | 0.7 > 0.0 | 0.7 > 0.0 | 0/0 (4/16) | 7.0/0.6/13.1/-3.2 |
| j  | move-target to wall-1: arm=0.8 wall_ahead[20]>=25 persist=3 | 172 | 263 | 236 | -27 | -0 | 0.1 | 0.7 > 0.7 | 0.7 > 0.6 | 4/15 (4/16) | 0.0/-0.4/5.9/-0.1 |

### H7

| fam | rule | key | net L6M | removed (zone) | clipped | other | clipped fills/wk | GB/wk before>after | RT/wk before>after | strict test v90/v80 (live rules b90/b80) | stack cut L6M/HOLD/PRE/X' % |
|---|---|---|---|---|---|---|---|---|---|---|---|
| h  | touched-not-filled: printed >= T-4 tick(s), hit inside after 0 s, slip 0.25 | 55 | 189 | 89 | -100 | -0 | 1.1 | 0.5 > 0.5 | 0.5 > 0.5 | 3/12 (4/13) | 2.6/-0.1/-0.3/-0.7 |
| i  | queue step-in: arm=0.8 queue>=30x Med -> limit T-2 tick | 0 | 0 | 0 | -0 | 0 | 0.0 | 0.5 > 0.5 | 0.5 > 0.5 | 4/13 (4/13) | 0.0/0.0/0.0/0.0 |
| m  | staggered 1/2 at 0.9 + 1/2 at 100% floor-after 0.8 | 122 | 359 | 601 | 242 | 0 | 1.6 | 0.5 > 0.4 | 0.5 > 0.4 | 2/9 (4/13) | -1.6/-0.5/-1.4/3.0 |
| n  | runner 0.50 of lots, trail xATR 1, floor 1 T | 44 | 94 | 0 | -94 | 0 | 1.9 | 0.5 > 0.5 | 0.5 > 0.5 | 4/13 (4/13) | -0.1/-0.1/-0.1/-0.8 |
| o  | level target on m=0.8: target = level - 2 ticks | 44 | 81 | 89 | 8 | 0 | 0.1 | 0.5 > 0.5 | 0.5 > 0.5 | 4/12 (4/13) | 2.7/0.0/0.0/-0.1 |
| p  | noise floor arm=0.9: ext - 3 x ATR14(1m) | 49 | 202 | 242 | 40 | 0 | 0.1 | 0.5 > 0.6 | 0.5 > 0.5 | 5/11 (4/13) | 1.8/0.0/-0.8/0.6 |
| q  | arrival: fast<=120s mid slow>900s floors 0.8/0.8/0.6 | 98 | 106 | 1347 | 1241 | 0 | 2.0 | 0.5 > 0.1 | 0.5 > 0.0 | 3/0 (4/13) | 0.1/2.2/-1.0/11.9 |
| q (pass) | arrival: fast<=150s mid slow>600s floors 0.8/0.8/0.8 | 56 | 188 | 1479 | 1290 | 0 | 3.0 | 0.5 > 0.0 | 0.5 > 0.0 | 0/0 (4/13) | -0.1/1.9/-5.0/13.2 |
| j  | move-target to wall-1: arm=0.9 wall_ahead[12]>=12 persist=1 | 60 | 68 | 193 | 126 | 0 | 0.4 | 0.5 > 0.5 | 0.5 > 0.5 | 4/11 (4/13) | 2.7/0.0/0.0/0.0 |

### A7

| fam | rule | key | net L6M | removed (zone) | clipped | other | clipped fills/wk | GB/wk before>after | RT/wk before>after | strict test v90/v80 (live rules b90/b80) | stack cut L6M/HOLD/PRE/X' % |
|---|---|---|---|---|---|---|---|---|---|---|---|
| h  | touched-not-filled: printed >= T-0 tick(s), hit inside after 1 s, slip 0.25 | 0 | 2 | 0 | -2 | 0 | 0.0 | 0.7 > 0.7 | 0.7 > 0.7 | 4/16 (4/16) | 0.0/0.0/0.0/0.0 |
| i  | queue step-in: arm=0.8 queue>=1x Med -> limit T-1 tick | 0 | 0 | 0 | -0 | 0 | 0.0 | 0.7 > 0.7 | 0.7 > 0.7 | 4/16 (4/16) | 0.0/0.0/0.0/0.0 |
| m  | staggered 1/2 at 0.75 + 1/2 at 100% floor-after off | 0 | 0 | 0 | -0 | 0 | 0.0 | 0.7 > 0.7 | 0.7 > 0.7 | 4/16 (4/16) | 0.0/0.0/0.0/0.0 |
| n  | runner 0.33 of lots, trail pts 8, floor 0.9 T | 0 | 0 | 0 | -0 | 0 | 0.0 | 0.7 > 0.7 | 0.7 > 0.7 | 4/16 (4/16) | 0.0/0.0/0.0/0.0 |
| o  | level target on m=0.9: target = level - 2 ticks | 0 | 0 | 0 | -0 | 0 | 0.0 | 0.7 > 0.7 | 0.7 > 0.7 | 4/16 (4/16) | 0.0/0.0/0.0/0.0 |
| p  | noise floor arm=0.8: ext - 3 x ATR14(1m) | -145 | -145 | 735 | 880 | 0 | 1.3 | 0.7 > 1.4 | 0.7 > 0.1 | 23/3 (4/16) | -2.8/-0.7/0.5/-3.0 |
| p (pass) | noise floor arm=0.8: ext - 0.75 x ATR14(1m) | -539 | -539 | 1076 | 1615 | -0 | 4.7 | 0.7 > 0.0 | 0.7 > 0.0 | 0/0 (4/16) | -3.3/-1.2/-1.3/-1.9 |
| q  | arrival: fast<=150s mid slow>600s floors 0.4/0.8/0.4 | -176 | -176 | 860 | 1036 | 0 | 1.7 | 0.7 > 1.8 | 0.7 > 0.0 | 33/0 (4/16) | -2.5/-1.1/-0.7/-2.7 |
| q (pass) | arrival: fast<=180s mid slow>300s floors 0.6/0.4/0.8 | -417 | -417 | 1156 | 1573 | 0 | 5.6 | 0.7 > 0.0 | 0.7 > 0.0 | 0/0 (4/16) | -3.2/-1.1/-1.3/-1.9 |
| j  | move-target to wall-1: arm=0.8 wall_ahead[4]>=25 persist=3 | 37 | 71 | 126 | 54 | 0 | 0.2 | 0.7 > 0.6 | 0.7 > 0.6 | 4/15 (4/16) | -0.5/0.0/0.0/0.0 |

### O7

| fam | rule | key | net L6M | removed (zone) | clipped | other | clipped fills/wk | GB/wk before>after | RT/wk before>after | strict test v90/v80 (live rules b90/b80) | stack cut L6M/HOLD/PRE/X' % |
|---|---|---|---|---|---|---|---|---|---|---|---|
| h  | touched-not-filled: printed >= T-0 tick(s), hit inside after 0 s, slip 0.25 | 0 | 0 | 0 | -0 | 0 | 0.0 | 0.1 > 0.1 | 0.0 > 0.0 | 2/1 (2/1) | 0.0/0.0/0.0/0.0 |
| i  | queue step-in: arm=0.8 queue>=1x Med -> limit T-1 tick | 0 | 0 | 0 | -0 | 0 | 0.0 | 0.1 > 0.1 | 0.0 > 0.0 | 2/1 (2/1) | 0.0/0.0/0.0/0.0 |
| m  | staggered 1/2 at 0.75 + 1/2 at 100% floor-after off | 0 | 0 | 0 | -0 | 0 | 0.0 | 0.1 > 0.1 | 0.0 > 0.0 | 2/1 (2/1) | 0.0/0.0/0.0/0.0 |
| n  | runner 0.33 of lots, trail pts 8, floor 0.9 T | 0 | 0 | 0 | -0 | 0 | 0.0 | 0.1 > 0.1 | 0.0 > 0.0 | 2/1 (2/1) | 0.0/0.0/0.0/0.0 |
| o  | level target pw m=0.7: target = level - 2 ticks | 0 | 0 | 0 | -0 | 0 | 0.0 | 0.1 > 0.1 | 0.0 > 0.0 | 2/1 (2/1) | 0.0/0.0/0.0/0.0 |
| p  | noise floor arm=0.9: ext - 1.5 x ATR14(1m) | 0 | 0 | 0 | -0 | 0 | 0.0 | 0.1 > 0.1 | 0.0 > 0.0 | 2/1 (2/1) | 0.0/0.0/0.0/0.0 |
| p (pass) | noise floor arm=0.8: ext - 0.75 x ATR14(1m) | -58 | -58 | 91 | 149 | 0 | 0.2 | 0.1 > 0.0 | 0.0 > 0.0 | 0/0 (2/1) | 0.4/0.0/-0.0/-1.1 |
| q  | arrival: fast<=180s mid slow>300s floors 0.4/0.6/0.6 | -52 | -52 | 78 | 130 | 0 | 0.2 | 0.1 > 0.0 | 0.0 > 0.0 | 1/0 (2/1) | 0.2/0.0/-0.0/-0.6 |
| q (pass) | arrival: fast<=180s mid slow>300s floors 0.8/0.6/0.6 | -86 | -86 | 99 | 185 | 0 | 0.3 | 0.1 > 0.0 | 0.0 > 0.0 | 0/0 (2/1) | 0.2/0.0/-0.0/-0.6 |
| j  | move-target to wall-1: arm=0.9 wall_ahead[12]>=6 persist=1 | 21 | 21 | 50 | 29 | -0 | 0.2 | 0.1 > 0.0 | 0.0 > 0.0 | 0/1 (2/1) | 0.8/0.0/-0.1/-0.1 |
| j (pass) | move-target to wall-1: arm=0.8 wall_ahead[12]>=3 persist=1 | -68 | -18 | 161 | 179 | 0 | 0.7 | 0.1 > 0.0 | 0.0 > 0.0 | 0/0 (2/1) | 0.9/0.0/-0.3/-1.9 |

### v1.8 actions and fields named by h-q

- h (touched-not-filled): `touched_not_filled j_ticks N_s inside_slip` action (hit the inside after the target level printed and our limit is unfilled); feature `target_printed`
- i (queue/fill step-in): feature `queue_ahead_mult` (resting size at the target level / MedLevel) + action `move-target T-s_ticks`
- j (front-run the wall): action `move-target wall-1_tick` (limit, no market) + feature `wall_px` (price of the largest level ahead) - first-order proxy: wall assumed at the far edge of wall_ticks
- m (staggered passive targets): action `staggered limits a1:w1,a2:w2,... [refloor f1,f2]` (several resting limits for the lots; each fill re-floors the remainder)
- n (runner): action `runner frac trail X|xATR k floor f` (take 1-frac at the target, trail the rest from the target with a floor at f x target)
- o (level in the last 20%): feature `level_in_zone` (PDH/PDL/PWH/PWL/ONH/ONL/00-50 between m x T and T) + action `move-target level-2_ticks` at entry
- p (noise-scaled floor): feature `atr1m14` (ATR(14) of 1-min bars) + action `floor ext-k*atr` armed at `mfe_pct>=m`
- q (arrival type): feature `secs_to_zone` (seconds from entry to first mfe_pct>=m) + class floors fast/mid/slow

## Engine order hooks: staggered targets (m, extended), move-target (j), touched-not-filled (h) - EXACT (user priority 23:20Z; T-BUILD-ON item 2)\n
**Hooks (code/th_nz/nz_hooks.py, private tree, engine untouched).** Extra resting limits live inside the engine alongside the live target order and are matched on every print by the engine itself (match_resting override): staggered rungs (a1 x T for w1 of the lots, a2 x T for w2, the rest keeps the normal 100% target), move-target (a limit at wall - 1 tick for all remaining lots, wall = largest against-side level within wt ticks and >= k x MedLevel, read from the live book at that second; fires once), touched-not-filled (the target level, or within j ticks, has printed and the target is still unfilled N s later -> engine market exit `NZTNF` through the book), re-floor after rung fills (`NZFloor`, engine exit request, stop options entry / entry+2 / none and a remainder floor), tag gate (fresh = n_sess <= 2 and gap >= 30 min, else rechase; chase_k is NOT used, so rechase here = 3rd+ or inside 30 min only) and session gate. Exit names NZStag1/2, NZMove, NZTNF, NZFloor. Partial fills use the engine exec_exit, so lots, locks, caps, stack cuts and re-entries re-simulate.\n
**Queue / fill model.** Primary (as ordered): an extra passive limit fills at its limit price only when a later print trades THROUGH it by one tick (queue-conservative, no rebate, full order size at the limit). Optimistic bound: touch-fill (a print at the level fills). Engine-native (reported as a calibrated third): the same cumulative-aggressor-volume rule the engine uses for the live target (TARGET_MODE=cumvol: filled when the aggressor volume at or through the level reaches the order size). Touched-not-filled and floors are engine market exits with the engine walk through the book (slip comes from the book, plus the engine latency LAT_FILL). Calibration: the cumvol rule was measured on the 85 live Target exits (84 fit) in the engine build notes (replica/sim.py); I did not re-measure it. One-tick-through is stricter than cumvol for small rungs and looser for the full size, so both are run on the best cell. The live M7 one-tick miss (target printed, unfilled) is exactly the case the through-1-tick rule produces and the touch rule hides: in the stored lists a printed-not-filled target is rare (about 0.4 per week across books at T-1 tick in L6M) and every one of them closed at or below breakeven (table h above). Frozen-week targets: the engine reproduces the live week targets under cumvol per the same notes; no new calibration was possible for staggered rungs because the live system never rested partial targets.\n
### Staggered targets extended: first-order, rungs 2/3 x positions 60-95% x stop after rung 1 (none / entry / entry+2 / floor) x remainder floor (best cell per scope; through-1-tick PRIMARY, touch OPTIMISTIC)\n
Per week; key = min(net L6M, net 43 m); net = removed - clipped + other (definitions above). Tags: fresh / rechase from n_sess and gap only (no chase_k).\n
| book | scope | fill | best cell | key | net L6M | removed | clipped | other | trades |
|---|---|---|---|---|---|---|---|---|---|
| P7x | all | through1 | 3 rungs 1/3 at 0.7, 1/3 at 0.9, 1/3 at 100%, after rung1 stop none, remainder floor 0.9 | 3742 | 8574 | 15878 | 13244 | 5941 | 3937 |
| P7x | all | touch | 3 rungs 1/3 at 0.85, 1/3 at 0.9, 1/3 at 100%, after rung1 stop none, remainder floor 0.9 | 3893 | 9538 | 15826 | 7104 | 815 | 3937 |
| P7x | fresh | through1 | 3 rungs 1/3 at 0.85, 1/3 at 0.9, 1/3 at 100%, after rung1 stop entry+2, remainder floor off | 1033 | 1033 | 2511 | 1478 | 0 | 1789 |
| P7x | fresh | touch | 3 rungs 1/3 at 0.85, 1/3 at 0.9, 1/3 at 100%, after rung1 stop entry+2, remainder floor off | 1083 | 1083 | 2523 | 1440 | -0 | 1789 |
| P7x | rechase | through1 | 3 rungs 1/3 at 0.7, 1/3 at 0.75, 1/3 at 100%, after rung1 stop entry+2, remainder floor 0.9 | 2879 | 8714 | 16196 | 18760 | 11278 | 2148 |
| P7x | rechase | touch | 3 rungs 1/3 at 0.7, 1/3 at 0.75, 1/3 at 100%, after rung1 stop entry+2, remainder floor 0.9 | 2710 | 8440 | 16171 | 19017 | 11286 | 2148 |
| P7x | sess_asia | through1 | 3 rungs 1/3 at 0.8, 1/3 at 0.9, 1/3 at 100%, after rung1 stop none, remainder floor 0.9 | 2778 | 6633 | 11005 | 5412 | 1040 | 1768 |
| P7x | sess_asia | touch | 3 rungs 1/3 at 0.8, 1/3 at 0.9, 1/3 at 100%, after rung1 stop entry+2, remainder floor 0.9 | 2969 | 5423 | 12875 | 8896 | 1445 | 1768 |
| P7x | sess_london | through1 | 3 rungs 1/3 at 0.7, 1/3 at 0.85, 1/3 at 100%, after rung1 stop none, remainder floor 0.9 | 448 | 1265 | 4285 | 4569 | 1548 | 1208 |
| P7x | sess_london | touch | 3 rungs 1/3 at 0.7, 1/3 at 0.85, 1/3 at 100%, after rung1 stop none, remainder floor 0.9 | 452 | 1234 | 4283 | 4596 | 1548 | 1208 |
| P7x | sess_nyam | through1 | 3 rungs 1/3 at 0.6, 1/3 at 0.7, 1/3 at 100%, after rung1 stop entry, remainder floor 0.5 | 1096 | 1111 | 1905 | 1866 | 1072 | 961 |
| P7x | sess_nyam | touch | 3 rungs 1/3 at 0.6, 1/3 at 0.7, 1/3 at 100%, after rung1 stop entry, remainder floor 0.5 | 1075 | 1111 | 1905 | 1866 | 1072 | 961 |
| P7x | sess_nypm | through1 | 2 rungs 1/2 at 0.6, 1/2 at 100%, after rung1 stop none | 0 | 0 | 0 | -0 | 0 | 0 |
| P7x | sess_nypm | touch | 2 rungs 1/2 at 0.6, 1/2 at 100%, after rung1 stop none | 0 | 0 | 0 | -0 | 0 | 0 |
| P7 | all | through1 | 2 rungs 1/2 at 0.7, 1/2 at 100%, after rung1 stop floor 0.7 | 1881 | 3475 | 11674 | 18535 | 10336 | 3937 |
| P7 | all | touch | 2 rungs 1/2 at 0.7, 1/2 at 100%, after rung1 stop floor 0.7 | 1842 | 3306 | 11680 | 18707 | 10332 | 3937 |
| P7 | fresh | through1 | 3 rungs 1/3 at 0.85, 1/3 at 0.9, 1/3 at 100%, after rung1 stop entry, remainder floor off | 425 | 425 | 1097 | 672 | 0 | 1789 |
| P7 | fresh | touch | 3 rungs 1/3 at 0.85, 1/3 at 0.9, 1/3 at 100%, after rung1 stop entry, remainder floor off | 444 | 444 | 1097 | 652 | 0 | 1789 |
| P7 | rechase | through1 | 2 rungs 1/2 at 0.7, 1/2 at 100%, after rung1 stop floor 0.7 | 1562 | 4216 | 9165 | 12779 | 7830 | 2148 |
| P7 | rechase | touch | 2 rungs 1/2 at 0.7, 1/2 at 100%, after rung1 stop floor 0.7 | 1493 | 4093 | 9171 | 12904 | 7827 | 2148 |
| P7 | sess_asia | through1 | 3 rungs 1/3 at 0.8, 1/3 at 0.9, 1/3 at 100%, after rung1 stop none, remainder floor 0.9 | 1543 | 3918 | 6286 | 2949 | 580 | 1768 |
| P7 | sess_asia | touch | 3 rungs 1/3 at 0.8, 1/3 at 0.85, 1/3 at 100%, after rung1 stop entry+2, remainder floor 0.9 | 1646 | 2921 | 8141 | 6032 | 812 | 1768 |
| P7 | sess_london | through1 | 2 rungs 1/2 at 0.9, 1/2 at 100%, after rung1 stop entry | 193 | 193 | 1092 | 899 | 0 | 1208 |
| P7 | sess_london | touch | 2 rungs 1/2 at 0.85, 1/2 at 100%, after rung1 stop none | 199 | 313 | 1208 | 895 | -0 | 1208 |
| P7 | sess_nyam | through1 | 2 rungs 1/2 at 0.7, 1/2 at 100%, after rung1 stop floor 0.5 | 570 | 693 | 1104 | 916 | 505 | 961 |
| P7 | sess_nyam | touch | 2 rungs 1/2 at 0.7, 1/2 at 100%, after rung1 stop floor 0.5 | 568 | 693 | 1104 | 916 | 505 | 961 |
| P7 | sess_nypm | through1 | 2 rungs 1/2 at 0.6, 1/2 at 100%, after rung1 stop none | 0 | 0 | 0 | -0 | 0 | 0 |
| P7 | sess_nypm | touch | 2 rungs 1/2 at 0.6, 1/2 at 100%, after rung1 stop none | 0 | 0 | 0 | -0 | 0 | 0 |
| U7 | all | through1 | 3 rungs 1/3 at 0.75, 1/3 at 0.85, 1/3 at 100%, after rung1 stop entry, remainder floor off | 171 | 334 | 1185 | 1214 | 363 | 1118 |
| U7 | all | touch | 3 rungs 1/3 at 0.75, 1/3 at 0.85, 1/3 at 100%, after rung1 stop entry, remainder floor off | 180 | 325 | 1176 | 1214 | 363 | 1118 |
| U7 | fresh | through1 | 3 rungs 1/3 at 0.75, 1/3 at 0.85, 1/3 at 100%, after rung1 stop entry, remainder floor off | 170 | 493 | 1185 | 1054 | 363 | 1016 |
| U7 | fresh | touch | 3 rungs 1/3 at 0.75, 1/3 at 0.85, 1/3 at 100%, after rung1 stop entry, remainder floor off | 180 | 484 | 1176 | 1054 | 363 | 1016 |
| U7 | rechase | through1 | 2 rungs 1/2 at 0.7, 1/2 at 100%, after rung1 stop entry | 207 | 250 | 412 | 555 | 393 | 102 |
| U7 | rechase | touch | 2 rungs 1/2 at 0.7, 1/2 at 100%, after rung1 stop entry | 207 | 250 | 412 | 555 | 393 | 102 |
| U7 | sess_asia | through1 | 2 rungs 1/2 at 0.7, 1/2 at 100%, after rung1 stop floor 0.7 | 112 | 618 | 1916 | 2907 | 1609 | 567 |
| U7 | sess_asia | touch | 2 rungs 1/2 at 0.7, 1/2 at 100%, after rung1 stop none | 103 | 352 | 966 | 1428 | 814 | 567 |
| U7 | sess_london | through1 | 3 rungs 1/3 at 0.8, 1/3 at 0.9, 1/3 at 100%, after rung1 stop entry, remainder floor off | 206 | 288 | 519 | 231 | 0 | 551 |
| U7 | sess_london | touch | 3 rungs 1/3 at 0.8, 1/3 at 0.9, 1/3 at 100%, after rung1 stop entry, remainder floor off | 228 | 288 | 519 | 231 | 0 | 551 |
| U7 | sess_nyam | through1 | 2 rungs 1/2 at 0.6, 1/2 at 100%, after rung1 stop none | 0 | 0 | 0 | -0 | 0 | 0 |
| U7 | sess_nyam | touch | 2 rungs 1/2 at 0.6, 1/2 at 100%, after rung1 stop none | 0 | 0 | 0 | -0 | 0 | 0 |
| U7 | sess_nypm | through1 | 2 rungs 1/2 at 0.6, 1/2 at 100%, after rung1 stop none | 0 | 0 | 0 | -0 | 0 | 0 |
| U7 | sess_nypm | touch | 2 rungs 1/2 at 0.6, 1/2 at 100%, after rung1 stop none | 0 | 0 | 0 | -0 | 0 | 0 |
| H7 | all | through1 | 3 rungs 1/3 at 0.6, 1/3 at 0.8, 1/3 at 100%, after rung1 stop none, remainder floor 0.7 | 152 | 244 | 413 | 261 | 93 | 881 |
| H7 | all | touch | 3 rungs 1/3 at 0.6, 1/3 at 0.7, 1/3 at 100%, after rung1 stop none, remainder floor 0.7 | 169 | 180 | 399 | 452 | 233 | 881 |
| H7 | fresh | through1 | 2 rungs 1/2 at 0.6, 1/2 at 100%, after rung1 stop floor 0.7 | 258 | 259 | 777 | 1581 | 1062 | 827 |
| H7 | fresh | touch | 2 rungs 1/2 at 0.6, 1/2 at 100%, after rung1 stop floor 0.7 | 258 | 323 | 764 | 1589 | 1148 | 827 |
| H7 | rechase | through1 | 3 rungs 1/3 at 0.9, 1/3 at 0.95, 1/3 at 100%, after rung1 stop entry+2, remainder floor 0.9 | -16 | -16 | 0 | 16 | 0 | 54 |
| H7 | rechase | touch | 3 rungs 1/3 at 0.9, 1/3 at 0.95, 1/3 at 100%, after rung1 stop entry+2, remainder floor 0.9 | -16 | -16 | 0 | 16 | 0 | 54 |
| H7 | sess_asia | through1 | 3 rungs 1/3 at 0.6, 1/3 at 0.8, 1/3 at 100%, after rung1 stop none, remainder floor 0.7 | 152 | 244 | 413 | 261 | 93 | 554 |
| H7 | sess_asia | touch | 3 rungs 1/3 at 0.6, 1/3 at 0.7, 1/3 at 100%, after rung1 stop none, remainder floor 0.7 | 169 | 180 | 399 | 452 | 233 | 554 |
| H7 | sess_london | through1 | 2 rungs 1/2 at 0.6, 1/2 at 100%, after rung1 stop none | 0 | 0 | 0 | -0 | 0 | 0 |
| H7 | sess_london | touch | 2 rungs 1/2 at 0.6, 1/2 at 100%, after rung1 stop none | 0 | 0 | 0 | -0 | 0 | 0 |
| H7 | sess_nyam | through1 | 2 rungs 1/2 at 0.6, 1/2 at 100%, after rung1 stop none | 0 | 0 | 0 | -0 | 0 | 327 |
| H7 | sess_nyam | touch | 2 rungs 1/2 at 0.6, 1/2 at 100%, after rung1 stop none | 0 | 0 | 0 | -0 | 0 | 327 |
| H7 | sess_nypm | through1 | 2 rungs 1/2 at 0.6, 1/2 at 100%, after rung1 stop none | 0 | 0 | 0 | -0 | 0 | 0 |
| H7 | sess_nypm | touch | 2 rungs 1/2 at 0.6, 1/2 at 100%, after rung1 stop none | 0 | 0 | 0 | -0 | 0 | 0 |
| K7 | all | through1 | 2 rungs 1/2 at 0.95, 1/2 at 100%, after rung1 stop floor 0.7 | 86 | 697 | 986 | 289 | 0 | 5627 |
| K7 | all | touch | 2 rungs 1/2 at 0.95, 1/2 at 100%, after rung1 stop floor 0.7 | 95 | 652 | 986 | 334 | 0 | 5627 |
| K7 | fresh | through1 | 2 rungs 1/2 at 0.95, 1/2 at 100%, after rung1 stop floor 0.5 | 12 | 79 | 165 | 85 | 0 | 2186 |
| K7 | fresh | touch | 2 rungs 1/2 at 0.95, 1/2 at 100%, after rung1 stop floor 0.5 | 25 | 74 | 165 | 91 | 0 | 2186 |
| K7 | rechase | through1 | 2 rungs 1/2 at 0.95, 1/2 at 100%, after rung1 stop floor 0.7 | 83 | 632 | 812 | 180 | 0 | 3441 |
| K7 | rechase | touch | 2 rungs 1/2 at 0.95, 1/2 at 100%, after rung1 stop floor 0.7 | 76 | 593 | 812 | 219 | 0 | 3441 |
| K7 | sess_asia | through1 | 3 rungs 1/3 at 0.9, 1/3 at 0.95, 1/3 at 100%, after rung1 stop entry+2, remainder floor 0.9 | 0 | 0 | 0 | -0 | 0 | 1893 |
| K7 | sess_asia | touch | 3 rungs 1/3 at 0.9, 1/3 at 0.95, 1/3 at 100%, after rung1 stop entry+2, remainder floor 0.9 | 0 | 0 | 0 | -0 | 0 | 1893 |
| K7 | sess_london | through1 | 2 rungs 1/2 at 0.95, 1/2 at 100%, after rung1 stop floor 0.7 | 91 | 513 | 664 | 151 | 0 | 1378 |
| K7 | sess_london | touch | 2 rungs 1/2 at 0.95, 1/2 at 100%, after rung1 stop floor 0.7 | 83 | 495 | 664 | 168 | 0 | 1378 |
| K7 | sess_nyam | through1 | 2 rungs 1/2 at 0.6, 1/2 at 100%, after rung1 stop none | 0 | 0 | 0 | -0 | 0 | 1301 |
| K7 | sess_nyam | touch | 2 rungs 1/2 at 0.6, 1/2 at 100%, after rung1 stop none | 0 | 0 | 0 | -0 | 0 | 1301 |
| K7 | sess_nypm | through1 | 2 rungs 1/2 at 0.95, 1/2 at 100%, after rung1 stop floor 0.7 | 52 | 270 | 322 | 52 | 0 | 1055 |
| K7 | sess_nypm | touch | 2 rungs 1/2 at 0.95, 1/2 at 100%, after rung1 stop floor 0.7 | 80 | 267 | 322 | 55 | 0 | 1055 |

### Exact results (stack = all books, daily; vs reference: P7 at 12/7/7 -> PTR_P7_NZX00, all other sets -> LPB_BASE)\n
| set | book | cell | months L6M/HOLD/PRE/Xprime | window | stack maxDD cut % | d mean $/wk | rule exits (n, $) |
|---|---|---|---|---|---|---|---|

### Near-zone scorecard and trader test on the exact sets (W-Q behavior_scorecard.py, mid-path MFE; windows with missing months are skipped and said so)\n
**PTR_P7_NZM1** (hq-M1): 
    PTR_P7_NZM1 L6M (stack, per week): full stops 24.5/wk $-39773; give-backs 8.7/wk (8.3 round-trips) realised $-10172, forgone vs target $27699; same-side losing runs max 12, p95 6, $-51951 lost on 3rd-and-later; no-new-evidence re-entries 38.3/wk $1650; recoveries cut 13.9/wk $47788, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $5024/wk, losers avoided $3376/wk, net +1372 $/wk; pnl $21156/wk.
    PTR_P7_NZM1 HOLD: months missing (6 of 12), window not scored
    PTR_P7_NZM1 PRE: months missing (17 of 17), window not scored
    PTR_P7_NZM1 X': months missing (10 of 10), window not scored

**PTR_P7_NZM2** (hq-M2): 
    PTR_P7_NZM2 L6M (stack, per week): full stops 24.6/wk $-40159; give-backs 7.9/wk (7.7 round-trips) realised $-9076, forgone vs target $22668; same-side losing runs max 12, p95 6, $-52743 lost on 3rd-and-later; no-new-evidence re-entries 39.2/wk $2155; recoveries cut 14.2/wk $50796, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $9172/wk, losers avoided $6816/wk, net -2750 $/wk; pnl $17033/wk.
    PTR_P7_NZM2 HOLD: months missing (6 of 12), window not scored
    PTR_P7_NZM2 PRE: months missing (17 of 17), window not scored
    PTR_P7_NZM2 X': months missing (10 of 10), window not scored

**PTR_P7_NZJ1** (hq-J1): 
    PTR_P7_NZJ1 L6M (stack, per week): full stops 24.4/wk $-39553; give-backs 8.5/wk (7.7 round-trips) realised $-9368, forgone vs target $27156; same-side losing runs max 12, p95 6, $-51401 lost on 3rd-and-later; no-new-evidence re-entries 38.7/wk $546; recoveries cut 14.0/wk $49398, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $7123/wk, losers avoided $5063/wk, net -3692 $/wk; pnl $16092/wk.
    PTR_P7_NZJ1 HOLD: months missing (6 of 12), window not scored
    PTR_P7_NZJ1 PRE: months missing (17 of 17), window not scored
    PTR_P7_NZJ1 X': months missing (10 of 10), window not scored

**PTR_P7_NZJ2** (hq-J2): 
    PTR_P7_NZJ2 L6M (stack, per week): full stops 24.4/wk $-39553; give-backs 8.4/wk (7.7 round-trips) realised $-9454, forgone vs target $27047; same-side losing runs max 12, p95 6, $-51479 lost on 3rd-and-later; no-new-evidence re-entries 38.7/wk $704; recoveries cut 14.0/wk $49398, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $7123/wk, losers avoided $4996/wk, net -3770 $/wk; pnl $16014/wk.
    PTR_P7_NZJ2 HOLD: months missing (6 of 12), window not scored
    PTR_P7_NZJ2 PRE: months missing (17 of 17), window not scored
    PTR_P7_NZJ2 X': months missing (10 of 10), window not scored

**PTR_P7_NZH1** (hq-H1): 
    PTR_P7_NZH1 L6M (stack, per week): full stops 24.5/wk $-40052; give-backs 9.1/wk (9.0 round-trips) realised $-14062, forgone vs target $35186; same-side losing runs max 12, p95 6, $-51512 lost on 3rd-and-later; no-new-evidence re-entries 37.3/wk $-440; recoveries cut 13.7/wk $46863, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $97/wk, losers avoided $275/wk, net -497 $/wk; pnl $19286/wk.
    PTR_P7_NZH1 HOLD: months missing (6 of 12), window not scored
    PTR_P7_NZH1 PRE: months missing (17 of 17), window not scored
    PTR_P7_NZH1 X': months missing (10 of 10), window not scored

**PTR_P7_NZH2** (hq-H2): 
    PTR_P7_NZH2 L6M (stack, per week): full stops 24.5/wk $-40006; give-backs 8.9/wk (8.7 round-trips) realised $-13107, forgone vs target $33401; same-side losing runs max 12, p95 6, $-51180 lost on 3rd-and-later; no-new-evidence re-entries 37.4/wk $-383; recoveries cut 13.6/wk $46749, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $780/wk, losers avoided $888/wk, net -165 $/wk; pnl $19619/wk.
    PTR_P7_NZH2 HOLD: months missing (6 of 12), window not scored
    PTR_P7_NZH2 PRE: months missing (17 of 17), window not scored
    PTR_P7_NZH2 X': months missing (10 of 10), window not scored

**PTR_P7_NZXM1** (hq-M1): 
    PTR_P7_NZXM1 L6M (stack, per week): full stops 24.3/wk $-39780; give-backs 7.7/wk (7.4 round-trips) realised $-9146, forgone vs target $25304; same-side losing runs max 11, p95 6, $-50776 lost on 3rd-and-later; no-new-evidence re-entries 34.2/wk $1440; recoveries cut 12.7/wk $51094, clipped fills 0.0/wk $0; vs PTR_P7_NZX00: winners skipped $8246/wk, losers avoided $4929/wk, net -1638 $/wk; pnl $22283/wk.
    PTR_P7_NZXM1 HOLD: months missing (6 of 12), window not scored
    PTR_P7_NZXM1 PRE: months missing (17 of 17), window not scored
    PTR_P7_NZXM1 X': months missing (10 of 10), window not scored

**PTR_P7_NZXM2** (hq-M2): 
    PTR_P7_NZXM2 L6M (stack, per week): full stops 24.3/wk $-39252; give-backs 7.1/wk (7.0 round-trips) realised $-8082, forgone vs target $20357; same-side losing runs max 11, p95 6, $-49605 lost on 3rd-and-later; no-new-evidence re-entries 34.2/wk $642; recoveries cut 12.9/wk $54399, clipped fills 0.0/wk $0; vs PTR_P7_NZX00: winners skipped $14641/wk, losers avoided $11575/wk, net -5925 $/wk; pnl $17995/wk.
    PTR_P7_NZXM2 HOLD: months missing (6 of 12), window not scored
    PTR_P7_NZXM2 PRE: months missing (17 of 17), window not scored
    PTR_P7_NZXM2 X': months missing (10 of 10), window not scored

**PTR_P7_NZXJ1** (hq-J1): 
    PTR_P7_NZXJ1 L6M (stack, per week): full stops 24.3/wk $-39226; give-backs 7.9/wk (7.5 round-trips) realised $-8461, forgone vs target $25530; same-side losing runs max 11, p95 6, $-50243 lost on 3rd-and-later; no-new-evidence re-entries 34.6/wk $1440; recoveries cut 12.9/wk $52596, clipped fills 0.0/wk $0; vs PTR_P7_NZX00: winners skipped $13027/wk, losers avoided $10188/wk, net -5885 $/wk; pnl $18035/wk.
    PTR_P7_NZXJ1 HOLD: months missing (6 of 12), window not scored
    PTR_P7_NZXJ1 PRE: months missing (17 of 17), window not scored
    PTR_P7_NZXJ1 X': months missing (10 of 10), window not scored

**PTR_P7_NZXJ2** (hq-J2): 
    PTR_P7_NZXJ2 L6M (stack, per week): full stops 24.2/wk $-39093; give-backs 7.9/wk (7.5 round-trips) realised $-8594, forgone vs target $25370; same-side losing runs max 11, p95 6, $-49590 lost on 3rd-and-later; no-new-evidence re-entries 34.3/wk $1766; recoveries cut 12.8/wk $51857, clipped fills 0.0/wk $0; vs PTR_P7_NZX00: winners skipped $12978/wk, losers avoided $10251/wk, net -5658 $/wk; pnl $18262/wk.
    PTR_P7_NZXJ2 HOLD: months missing (6 of 12), window not scored
    PTR_P7_NZXJ2 PRE: months missing (17 of 17), window not scored
    PTR_P7_NZXJ2 X': months missing (10 of 10), window not scored

**PTR_P7_NZXH1** (hq-H1): 
    PTR_P7_NZXH1 L6M (stack, per week): full stops 24.2/wk $-39195; give-backs 8.1/wk (7.9 round-trips) realised $-12103, forgone vs target $32083; same-side losing runs max 11, p95 6, $-50415 lost on 3rd-and-later; no-new-evidence re-entries 33.4/wk $-837; recoveries cut 12.6/wk $49084, clipped fills 0.0/wk $0; vs PTR_P7_NZX00: winners skipped $244/wk, losers avoided $768/wk, net -331 $/wk; pnl $23589/wk.
    PTR_P7_NZXH1 HOLD: months missing (6 of 12), window not scored
    PTR_P7_NZXH1 PRE: months missing (17 of 17), window not scored
    PTR_P7_NZXH1 X': months missing (10 of 10), window not scored

**PTR_P7_NZXH2** (hq-H2): 
    PTR_P7_NZXH2 L6M (stack, per week): full stops 24.3/wk $-39692; give-backs 8.1/wk (7.9 round-trips) realised $-11589, forgone vs target $32019; same-side losing runs max 11, p95 6, $-51273 lost on 3rd-and-later; no-new-evidence re-entries 33.7/wk $-85; recoveries cut 12.7/wk $49731, clipped fills 0.0/wk $0; vs PTR_P7_NZX00: winners skipped $2440/wk, losers avoided $1592/wk, net -298 $/wk; pnl $23622/wk.
    PTR_P7_NZXH2 HOLD: months missing (6 of 12), window not scored
    PTR_P7_NZXH2 PRE: months missing (17 of 17), window not scored
    PTR_P7_NZXH2 X': months missing (10 of 10), window not scored

**PTR_P7_NZE1** (stag-E1): 
    PTR_P7_NZE1 L6M (stack, per week): full stops 24.5/wk $-39773; give-backs 8.7/wk (8.4 round-trips) realised $-10229, forgone vs target $27749; same-side losing runs max 12, p95 6, $-52300 lost on 3rd-and-later; no-new-evidence re-entries 38.6/wk $1745; recoveries cut 13.9/wk $47998, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $5024/wk, losers avoided $3376/wk, net +1057 $/wk; pnl $20841/wk.
    PTR_P7_NZE1 HOLD: months missing (6 of 12), window not scored
    PTR_P7_NZE1 PRE: months missing (17 of 17), window not scored
    PTR_P7_NZE1 X': months missing (10 of 10), window not scored

**PTR_P7_NZE2** (stag-E2): 
    PTR_P7_NZE2 L6M (stack, per week): full stops 24.5/wk $-39773; give-backs 8.7/wk (8.4 round-trips) realised $-10229, forgone vs target $27749; same-side losing runs max 12, p95 6, $-52297 lost on 3rd-and-later; no-new-evidence re-entries 38.6/wk $1722; recoveries cut 13.9/wk $47998, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $5024/wk, losers avoided $3376/wk, net +1111 $/wk; pnl $20895/wk.
    PTR_P7_NZE2 HOLD: months missing (6 of 12), window not scored
    PTR_P7_NZE2 PRE: months missing (17 of 17), window not scored
    PTR_P7_NZE2 X': months missing (10 of 10), window not scored

**PTR_P7_NZE3** (stag-E3): 
    PTR_P7_NZE3 L6M (stack, per week): full stops 24.6/wk $-40159; give-backs 8.1/wk (8.0 round-trips) realised $-10197, forgone vs target $24896; same-side losing runs max 12, p95 6, $-51014 lost on 3rd-and-later; no-new-evidence re-entries 38.7/wk $2003; recoveries cut 14.0/wk $49828, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $4879/wk, losers avoided $4590/wk, net +1343 $/wk; pnl $21127/wk.
    PTR_P7_NZE3 HOLD: months missing (6 of 12), window not scored
    PTR_P7_NZE3 PRE: months missing (17 of 17), window not scored
    PTR_P7_NZE3 X': months missing (10 of 10), window not scored

**PTR_P7_NZXE1** (stag-E1): 
    PTR_P7_NZXE1 L6M (stack, per week): full stops 24.3/wk $-39780; give-backs 7.7/wk (7.4 round-trips) realised $-9034, forgone vs target $25193; same-side losing runs max 11, p95 6, $-52063 lost on 3rd-and-later; no-new-evidence re-entries 34.7/wk $15; recoveries cut 12.9/wk $52868, clipped fills 0.0/wk $0; vs PTR_P7_NZX00: winners skipped $8051/wk, losers avoided $4514/wk, net -3467 $/wk; pnl $20453/wk.
    PTR_P7_NZXE1 HOLD: months missing (6 of 12), window not scored
    PTR_P7_NZXE1 PRE: months missing (17 of 17), window not scored
    PTR_P7_NZXE1 X': months missing (10 of 10), window not scored

**PTR_P7_NZXE2** (stag-E2): 
    PTR_P7_NZXE2 L6M (stack, per week): full stops 24.3/wk $-39592; give-backs 7.7/wk (7.4 round-trips) realised $-9034, forgone vs target $25193; same-side losing runs max 11, p95 6, $-51905 lost on 3rd-and-later; no-new-evidence re-entries 34.7/wk $152; recoveries cut 12.9/wk $51969, clipped fills 0.0/wk $0; vs PTR_P7_NZX00: winners skipped $8051/wk, losers avoided $4644/wk, net -3606 $/wk; pnl $20314/wk.
    PTR_P7_NZXE2 HOLD: months missing (6 of 12), window not scored
    PTR_P7_NZXE2 PRE: months missing (17 of 17), window not scored
    PTR_P7_NZXE2 X': months missing (10 of 10), window not scored

**PTR_P7_NZXE3** (stag-E3): 
    PTR_P7_NZXE3 L6M (stack, per week): full stops 24.3/wk $-39501; give-backs 7.3/wk (7.2 round-trips) realised $-9016, forgone vs target $22388; same-side losing runs max 11, p95 6, $-49509 lost on 3rd-and-later; no-new-evidence re-entries 34.5/wk $1096; recoveries cut 12.9/wk $52918, clipped fills 0.0/wk $0; vs PTR_P7_NZX00: winners skipped $7955/wk, losers avoided $7192/wk, net +358 $/wk; pnl $24278/wk.
    PTR_P7_NZXE3 HOLD: months missing (6 of 12), window not scored
    PTR_P7_NZXE3 PRE: months missing (17 of 17), window not scored
    PTR_P7_NZXE3 X': months missing (10 of 10), window not scored

**PTR_U7_NZU1** (stag-U1): 
    PTR_U7_NZU1 L6M (stack, per week): full stops 24.4/wk $-39476; give-backs 9.1/wk (8.8 round-trips) realised $-12783, forgone vs target $34295; same-side losing runs max 12, p95 6, $-50830 lost on 3rd-and-later; no-new-evidence re-entries 37.3/wk $-420; recoveries cut 13.7/wk $46732, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $0/wk, losers avoided $-0/wk, net -197 $/wk; pnl $19587/wk.
    PTR_U7_NZU1 HOLD: months missing (6 of 12), window not scored
    PTR_U7_NZU1 PRE: months missing (17 of 17), window not scored
    PTR_U7_NZU1 X': months missing (10 of 10), window not scored

**PTR_H7_NZH1S** (stag-H1S): 
    PTR_H7_NZH1S L6M (stack, per week): full stops 24.5/wk $-40052; give-backs 9.0/wk (8.9 round-trips) realised $-13870, forgone vs target $34999; same-side losing runs max 12, p95 6, $-51111 lost on 3rd-and-later; no-new-evidence re-entries 37.2/wk $-325; recoveries cut 13.7/wk $46863, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $0/wk, losers avoided $-0/wk, net +5 $/wk; pnl $19789/wk.
    PTR_H7_NZH1S HOLD: months missing (6 of 12), window not scored
    PTR_H7_NZH1S PRE: months missing (17 of 17), window not scored
    PTR_H7_NZH1S X': months missing (10 of 10), window not scored

**PTR_K7_NZK1** (stag-K1): 
    PTR_K7_NZK1 L6M (stack, per week): full stops 24.5/wk $-40052; give-backs 9.1/wk (9.0 round-trips) realised $-14009, forgone vs target $35376; same-side losing runs max 12, p95 6, $-51344 lost on 3rd-and-later; no-new-evidence re-entries 37.3/wk $-363; recoveries cut 13.7/wk $46863, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $0/wk, losers avoided $-0/wk, net +0 $/wk; pnl $19784/wk.
    PTR_K7_NZK1 HOLD: months missing (6 of 12), window not scored
    PTR_K7_NZK1 PRE: months missing (17 of 17), window not scored
    PTR_K7_NZK1 X': months missing (10 of 10), window not scored

**Definitions (all $ per WEEK of the window unless a sentence says "over the window"; L6M = 24 weeks).** Per trade, d = new P&L under the rule minus the trade P&L under live rules (same lots, fees, slip 1.2 on the rule exit). *net (all fires)* = sum of d over every trade the rule exits = the realised P&L change of the rule. *removed (zone)* = sum of d over fired trades that reached 80% of target and did NOT fill under live rules (the give-back saving; counted only inside the 80% zone). *clipped* = sum of (base - new) over fired trades that DID fill under live rules (fills the rule exited early, cost positive number). *other saves* = d over fired non-fill trades that never reached 80% (e.g. trades armed at 0.7 that later stopped out). Identity: net = removed - clipped + other saves. So removed - clipped can be negative while net is positive because of other saves, and the strict-pass early-take rules (arm 0.7) live on those other saves. In the plain sentences, "removed N give-backs worth $X and clipped M fills worth $Y" are totals OVER THE 24-WEEK WINDOW (zone non-fills / base fills), the per-week figures are those divided by 24.

**Is removed - clipped positive on L6M for any rule?** Yes for many rules in the grid (zone-only give-back saving minus clipped fills): see the removed-clipped column; counts of cells with removed-clipped > 0 on L6M (of 1,231 per book): P7x 541, P7 549, K7 359, M7 648, U7 369, H7 430, A7 32, O7 57; with also positive 43-month net: P7x 456, P7 459, K7 5, M7 179, U7 22, H7 334, A7 5, O7 32. But NO strict trader-pass finalist has removed - clipped > 0 on L6M (P7 12/7/7 pass rule: +21,417 removed vs 34,269 clipped = -12,852/wk; its +3,165/wk net comes from other saves of about +16k/wk). Rules with removed-clipped > 0 are the ones that fail the trader test.

## P7 at 12/7/7 lots

| row | rule | key $/wk | net L6M (all fires) | removed (zone) L6M | clipped L6M | removed-clipped | other saves | clipped fills/wk | GB/wk L6M before>after | RT/wk before>after | stack cut L6M/HOLD/PRE/X' % | p_plc | p_fam |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| REF stand-in | stand-in pct>=0.95 secs_fav>=5 take | 679 | 2,757 | 4,003 | 1,246 | 2,757 | 0 | 8.3 | 2.0 > 1.7 | 2.0 > 1.7 | 11.2/11.2/5.3/-2.1 | - | - |
| best_all | flow pulled_against_mult>=20 arm=0.8 persist=1 dd>=0 | 1,986 | 2,669 | 20,675 | 18,006 | 2,669 | 0 | 13.1 | 2.0 > 1.1 | 2.0 > 0.2 | 11.2/-9.0/21.8/6.7 | 0.00 | 0.00 |
| best_pass | flow pulled_against_mult>=5 arm=0.7 persist=1 dd>=0 | 592 | 3,165 | 21,417 | 34,269 | -12,852 | 16,017 | 18.7 | 2.0 > 0.0 | 2.0 > 0.0 | 44.4/30.0/27.6/36.9 | 0.00 | 1.00 |
| fam_a | ladder m1=0.7 f1=0.65 | .9 f2=0.7 | .95 f3=0.9 mode=1 | 1,609 | 4,235 | 20,545 | 31,637 | -11,092 | 15,327 | 15.3 | 2.0 > 0.1 | 2.0 > 0.0 | 51.9/22.7/32.8/42.7 | 0.00 | 0.00 |
| fam_b | rev arm=0.7 X=8 N=3 | 1,146 | 5,224 | 13,641 | 16,618 | -2,977 | 8,201 | 5.1 | 2.0 > 3.6 | 2.0 > 0.9 | 42.6/7.2/20.5/29.7 | 0.00 | 0.00 |
| fam_e | stall arm=0.9 N=3 ticks=0 work=20s | 1,213 | 4,362 | 11,637 | 7,275 | 4,362 | -0 | 13.8 | 2.0 > 1.2 | 2.0 > 1.1 | 20.0/2.9/16.2/20.0 | 1.00 | 1.00 |
| fam_g | ladder m1=0.7 f1=0.65 | .9 f2=0.7 | .95 f3=0.9 mode=1 + zone arm=.8 N=240 floor 0.8 | 1,638 | 4,542 | 20,661 | 31,446 | -10,785 | 15,327 | 15.4 | 2.0 > 0.1 | 2.0 > 0.0 | 51.9/22.7/33.2/43.1 | 0.00 | 0.00 |

**best_pass_market = flow pulled_against_mult>=5 arm=0.7 persist=1 dd>=0** (family c, v1.7: profit P7 * pct>=0.7 pulled_against_mult>=5 take win=5 persist=1   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 0 (live rules 24); reached 80% closing at or below breakeven: 0 (live rules 50) -> PASS. Frozen live week: 0 / 0 (live rules 1 / 3) -> PASS. In plain words L6M: it removed 50 give-backs worth $523,186 and clipped 457 fills worth $837,138 (all in the 24-week window; per week 21,417 removed, 34,269 clipped). Live week: removed 3 worth $47,686, clipped 27 fills worth $77,524.
- Scorecard (per week; before > after): L6M: full stops 0.6 > 0.5 ($-2,207 > $-1,292), give-backs 2.0 > 0.0 ($-10,194 > $0), round trips 2.0 > 0.0, fills clipped 18.7 ($34,269), net 3,165; HOLD: full stops 0.4 > 0.3 ($-1,543 > $-907), give-backs 2.0 > 0.0 ($-9,503 > $17), round trips 2.0 > 0.0, fills clipped 16.8 ($31,525), net 1,937; PRE: full stops 0.4 > 0.3 ($-1,438 > $-1,143), give-backs 1.5 > 0.0 ($-6,451 > $51), round trips 1.4 > 0.0, fills clipped 10.6 ($19,705), net 849; X': full stops 0.4 > 0.3 ($-1,393 > $-929), give-backs 0.8 > 0.0 ($-3,695 > $9), round trips 0.7 > 0.0, fills clipped 6.9 ($13,702), net -557
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 132,671 (-29,935), wk 202623: 96,586 (33,993), wk 202625: 87,393 (-12,277), wk 202624: 79,831 (-21,272), wk 202639: 77,688 (-37,287). Live week: this books Delta -29,838 on a live total of 103,596 -> week stays positive.

**best_pass = flow pulled_against_mult>=5 arm=0.7 persist=1 dd>=0** (family c, v1.7: profit P7 * pct>=0.7 pulled_against_mult>=5 take win=5 persist=1   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 0 (live rules 24); reached 80% closing at or below breakeven: 0 (live rules 50) -> PASS. Frozen live week: 0 / 0 (live rules 1 / 3) -> PASS. In plain words L6M: it removed 50 give-backs worth $523,186 and clipped 457 fills worth $837,138 (all in the 24-week window; per week 21,417 removed, 34,269 clipped). Live week: removed 3 worth $47,686, clipped 27 fills worth $77,524.
- Scorecard (per week; before > after): L6M: full stops 0.6 > 0.5 ($-2,207 > $-1,292), give-backs 2.0 > 0.0 ($-10,194 > $0), round trips 2.0 > 0.0, fills clipped 18.7 ($34,269), net 3,165; HOLD: full stops 0.4 > 0.3 ($-1,543 > $-907), give-backs 2.0 > 0.0 ($-9,503 > $17), round trips 2.0 > 0.0, fills clipped 16.8 ($31,525), net 1,937; PRE: full stops 0.4 > 0.3 ($-1,438 > $-1,143), give-backs 1.5 > 0.0 ($-6,451 > $51), round trips 1.4 > 0.0, fills clipped 10.6 ($19,705), net 849; X': full stops 0.4 > 0.3 ($-1,393 > $-929), give-backs 0.8 > 0.0 ($-3,695 > $9), round trips 0.7 > 0.0, fills clipped 6.9 ($13,702), net -557
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 132,671 (-29,935), wk 202623: 96,586 (33,993), wk 202625: 87,393 (-12,277), wk 202624: 79,831 (-21,272), wk 202639: 77,688 (-37,287). Live week: this books Delta -29,838 on a live total of 103,596 -> week stays positive.

**best_market = flow pulled_against_mult>=20 arm=0.8 persist=1 dd>=0** (family c, v1.7: profit P7 * pct>=0.8 pulled_against_mult>=20 take win=5 persist=1   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 22 (live rules 24); reached 80% closing at or below breakeven: 5 (live rules 50) -> FAIL. Frozen live week: 4 / 1 (live rules 1 / 3) -> FAIL. In plain words L6M: it removed 49 give-backs worth $505,061 and clipped 321 fills worth $439,855 (all in the 24-week window; per week 20,675 removed, 18,006 clipped). Live week: removed 3 worth $33,118, clipped 19 fills worth $65,879.
- Scorecard (per week; before > after): L6M: full stops 0.6 > 0.5 ($-2,207 > $-1,558), give-backs 2.0 > 1.1 ($-10,194 > $2,122), round trips 2.0 > 0.2, fills clipped 13.1 ($18,006), net 2,669; HOLD: full stops 0.4 > 0.3 ($-1,543 > $-1,035), give-backs 2.0 > 1.2 ($-9,503 > $2,385), round trips 2.0 > 0.2, fills clipped 11.6 ($16,732), net 1,787; PRE: full stops 0.4 > 0.4 ($-1,438 > $-1,204), give-backs 1.5 > 1.2 ($-6,451 > $2,007), round trips 1.4 > 0.2, fills clipped 5.6 ($8,742), net 3,237; X': full stops 0.4 > 0.4 ($-1,393 > $-1,393), give-backs 0.8 > 1.0 ($-3,695 > $1,001), round trips 0.7 > 0.2, fills clipped 1.7 ($3,929), net 697
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 132,671 (-21,789), wk 202623: 96,586 (16,036), wk 202625: 87,393 (-5,680), wk 202624: 79,831 (-4,525), wk 202639: 77,688 (-18,125). Live week: this books Delta -32,760 on a live total of 103,596 -> week stays positive.

**best_all = flow pulled_against_mult>=20 arm=0.8 persist=1 dd>=0** (family c, v1.7: profit P7 * pct>=0.8 pulled_against_mult>=20 take win=5 persist=1   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 22 (live rules 24); reached 80% closing at or below breakeven: 5 (live rules 50) -> FAIL. Frozen live week: 4 / 1 (live rules 1 / 3) -> FAIL. In plain words L6M: it removed 49 give-backs worth $505,061 and clipped 321 fills worth $439,855 (all in the 24-week window; per week 20,675 removed, 18,006 clipped). Live week: removed 3 worth $33,118, clipped 19 fills worth $65,879.
- Scorecard (per week; before > after): L6M: full stops 0.6 > 0.5 ($-2,207 > $-1,558), give-backs 2.0 > 1.1 ($-10,194 > $2,122), round trips 2.0 > 0.2, fills clipped 13.1 ($18,006), net 2,669; HOLD: full stops 0.4 > 0.3 ($-1,543 > $-1,035), give-backs 2.0 > 1.2 ($-9,503 > $2,385), round trips 2.0 > 0.2, fills clipped 11.6 ($16,732), net 1,787; PRE: full stops 0.4 > 0.4 ($-1,438 > $-1,204), give-backs 1.5 > 1.2 ($-6,451 > $2,007), round trips 1.4 > 0.2, fills clipped 5.6 ($8,742), net 3,237; X': full stops 0.4 > 0.4 ($-1,393 > $-1,393), give-backs 0.8 > 1.0 ($-3,695 > $1,001), round trips 0.7 > 0.2, fills clipped 1.7 ($3,929), net 697
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 132,671 (-21,789), wk 202623: 96,586 (16,036), wk 202625: 87,393 (-5,680), wk 202624: 79,831 (-4,525), wk 202639: 77,688 (-18,125). Live week: this books Delta -32,760 on a live total of 103,596 -> week stays positive.

## P7 at 7/4/4 lots (installed)

| row | rule | key $/wk | net L6M (all fires) | removed (zone) L6M | clipped L6M | removed-clipped | other saves | clipped fills/wk | GB/wk L6M before>after | RT/wk before>after | stack cut L6M/HOLD/PRE/X' % | p_plc | p_fam |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| REF stand-in | stand-in pct>=0.95 secs_fav>=5 take | 400 | 1,605 | 2,312 | 707 | 1,605 | 0 | 8.3 | 2.0 > 1.7 | 2.0 > 1.7 | 10.6/3.6/6.2/-0.0 | - | - |
| best_all | flow pulled_against_mult>=20 arm=0.8 persist=1 dd>=0 | 1,159 | 1,567 | 11,979 | 10,412 | 1,567 | 0 | 13.1 | 2.0 > 1.1 | 2.0 > 0.2 | 10.7/-15.8/11.7/5.7 | 0.00 | 0.00 |
| best_pass | flow pulled_against_mult>=5 arm=0.7 persist=1 dd>=0 | 358 | 1,831 | 12,401 | 19,848 | -7,447 | 9,278 | 18.7 | 2.0 > 0.0 | 2.0 > 0.0 | 50.4/15.2/18.0/34.8 | 0.00 | 1.00 |
| fam_a | ladder m1=0.7 f1=0.65 | .9 f2=0.7 | .95 f3=0.9 mode=1 | 943 | 2,447 | 11,897 | 18,328 | -6,431 | 8,879 | 15.3 | 2.0 > 0.1 | 2.0 > 0.0 | 51.1/13.1/21.9/37.7 | 0.00 | 0.00 |
| fam_b | rev arm=0.7 X=8 N=3 | 667 | 3,013 | 7,892 | 9,625 | -1,734 | 4,747 | 5.1 | 2.0 > 3.6 | 2.0 > 0.9 | 49.0/9.1/16.7/26.3 | 0.00 | 0.00 |
| fam_e | stall arm=0.9 N=3 ticks=0 work=20s | 715 | 2,551 | 6,751 | 4,200 | 2,551 | 0 | 13.8 | 2.0 > 1.2 | 2.0 > 1.1 | 22.3/-6.4/8.8/17.7 | 1.00 | 1.00 |
| fam_g | ladder m1=0.7 f1=0.65 | .9 f2=0.7 | .95 f3=0.9 mode=1 + zone arm=.8 N=240 floor 0.8 | 959 | 2,628 | 11,964 | 18,215 | -6,251 | 8,879 | 15.4 | 2.0 > 0.1 | 2.0 > 0.0 | 52.6/13.2/21.9/38.0 | 0.00 | 0.00 |

**best_pass_market = flow pulled_against_mult>=5 arm=0.7 persist=1 dd>=0** (family c, v1.7: profit P7 * pct>=0.7 pulled_against_mult>=5 take win=5 persist=1   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 0 (live rules 24); reached 80% closing at or below breakeven: 0 (live rules 50) -> PASS. Frozen live week: 0 / 0 (live rules 1 / 3) -> PASS. In plain words L6M: it removed 50 give-backs worth $302,940 and clipped 457 fills worth $484,859 (all in the 24-week window; per week 12,401 removed, 19,848 clipped). Live week: removed 3 worth $27,817, clipped 27 fills worth $45,016.
- Scorecard (per week; before > after): L6M: full stops 0.6 > 0.5 ($-1,261 > $-738), give-backs 2.0 > 0.0 ($-5,899 > $0), round trips 2.0 > 0.0, fills clipped 18.7 ($19,848), net 1,831; HOLD: full stops 0.4 > 0.3 ($-882 > $-518), give-backs 2.0 > 0.0 ($-5,496 > $10), round trips 2.0 > 0.0, fills clipped 16.8 ($18,244), net 1,134; PRE: full stops 0.4 > 0.3 ($-828 > $-658), give-backs 1.5 > 0.0 ($-3,728 > $30), round trips 1.4 > 0.0, fills clipped 10.6 ($11,385), net 504; X': full stops 0.4 > 0.3 ($-805 > $-535), give-backs 0.8 > 0.0 ($-2,141 > $5), round trips 0.7 > 0.0, fills clipped 6.9 ($7,904), net -293
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (-17,288), wk 202623: 73,836 (19,886), wk 202625: 59,099 (-7,077), wk 202639: 57,178 (-21,582), wk 202633: 52,499 (-8,322). Live week: this books Delta -17,199 on a live total of 103,596 -> week stays positive.

**best_pass = flow pulled_against_mult>=5 arm=0.7 persist=1 dd>=0** (family c, v1.7: profit P7 * pct>=0.7 pulled_against_mult>=5 take win=5 persist=1   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 0 (live rules 24); reached 80% closing at or below breakeven: 0 (live rules 50) -> PASS. Frozen live week: 0 / 0 (live rules 1 / 3) -> PASS. In plain words L6M: it removed 50 give-backs worth $302,940 and clipped 457 fills worth $484,859 (all in the 24-week window; per week 12,401 removed, 19,848 clipped). Live week: removed 3 worth $27,817, clipped 27 fills worth $45,016.
- Scorecard (per week; before > after): L6M: full stops 0.6 > 0.5 ($-1,261 > $-738), give-backs 2.0 > 0.0 ($-5,899 > $0), round trips 2.0 > 0.0, fills clipped 18.7 ($19,848), net 1,831; HOLD: full stops 0.4 > 0.3 ($-882 > $-518), give-backs 2.0 > 0.0 ($-5,496 > $10), round trips 2.0 > 0.0, fills clipped 16.8 ($18,244), net 1,134; PRE: full stops 0.4 > 0.3 ($-828 > $-658), give-backs 1.5 > 0.0 ($-3,728 > $30), round trips 1.4 > 0.0, fills clipped 10.6 ($11,385), net 504; X': full stops 0.4 > 0.3 ($-805 > $-535), give-backs 0.8 > 0.0 ($-2,141 > $5), round trips 0.7 > 0.0, fills clipped 6.9 ($7,904), net -293
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (-17,288), wk 202623: 73,836 (19,886), wk 202625: 59,099 (-7,077), wk 202639: 57,178 (-21,582), wk 202633: 52,499 (-8,322). Live week: this books Delta -17,199 on a live total of 103,596 -> week stays positive.

**best_market = flow pulled_against_mult>=20 arm=0.8 persist=1 dd>=0** (family c, v1.7: profit P7 * pct>=0.8 pulled_against_mult>=20 take win=5 persist=1   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 22 (live rules 24); reached 80% closing at or below breakeven: 5 (live rules 50) -> FAIL. Frozen live week: 4 / 1 (live rules 1 / 3) -> FAIL. In plain words L6M: it removed 49 give-backs worth $292,637 and clipped 321 fills worth $254,354 (all in the 24-week window; per week 11,979 removed, 10,412 clipped). Live week: removed 3 worth $19,319, clipped 19 fills worth $38,305.
- Scorecard (per week; before > after): L6M: full stops 0.6 > 0.5 ($-1,261 > $-890), give-backs 2.0 > 1.1 ($-5,899 > $1,231), round trips 2.0 > 0.2, fills clipped 13.1 ($10,412), net 1,567; HOLD: full stops 0.4 > 0.3 ($-882 > $-591), give-backs 2.0 > 1.2 ($-5,496 > $1,382), round trips 2.0 > 0.2, fills clipped 11.6 ($9,672), net 1,049; PRE: full stops 0.4 > 0.4 ($-828 > $-693), give-backs 1.5 > 1.2 ($-3,728 > $1,160), round trips 1.4 > 0.2, fills clipped 5.6 ($5,042), net 1,882; X': full stops 0.4 > 0.4 ($-805 > $-805), give-backs 0.8 > 1.0 ($-2,141 > $579), round trips 0.7 > 0.2, fills clipped 1.7 ($2,265), net 415
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (-12,644), wk 202623: 73,836 (9,417), wk 202625: 59,099 (-3,302), wk 202639: 57,178 (-10,462), wk 202633: 52,499 (2,446). Live week: this books Delta -18,986 on a live total of 103,596 -> week stays positive.

**best_all = flow pulled_against_mult>=20 arm=0.8 persist=1 dd>=0** (family c, v1.7: profit P7 * pct>=0.8 pulled_against_mult>=20 take win=5 persist=1   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 22 (live rules 24); reached 80% closing at or below breakeven: 5 (live rules 50) -> FAIL. Frozen live week: 4 / 1 (live rules 1 / 3) -> FAIL. In plain words L6M: it removed 49 give-backs worth $292,637 and clipped 321 fills worth $254,354 (all in the 24-week window; per week 11,979 removed, 10,412 clipped). Live week: removed 3 worth $19,319, clipped 19 fills worth $38,305.
- Scorecard (per week; before > after): L6M: full stops 0.6 > 0.5 ($-1,261 > $-890), give-backs 2.0 > 1.1 ($-5,899 > $1,231), round trips 2.0 > 0.2, fills clipped 13.1 ($10,412), net 1,567; HOLD: full stops 0.4 > 0.3 ($-882 > $-591), give-backs 2.0 > 1.2 ($-5,496 > $1,382), round trips 2.0 > 0.2, fills clipped 11.6 ($9,672), net 1,049; PRE: full stops 0.4 > 0.4 ($-828 > $-693), give-backs 1.5 > 1.2 ($-3,728 > $1,160), round trips 1.4 > 0.2, fills clipped 5.6 ($5,042), net 1,882; X': full stops 0.4 > 0.4 ($-805 > $-805), give-backs 0.8 > 1.0 ($-2,141 > $579), round trips 0.7 > 0.2, fills clipped 1.7 ($2,265), net 415
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (-12,644), wk 202623: 73,836 (9,417), wk 202625: 59,099 (-3,302), wk 202639: 57,178 (-10,462), wk 202633: 52,499 (2,446). Live week: this books Delta -18,986 on a live total of 103,596 -> week stays positive.

## K7

| row | rule | key $/wk | net L6M (all fires) | removed (zone) L6M | clipped L6M | removed-clipped | other saves | clipped fills/wk | GB/wk L6M before>after | RT/wk before>after | stack cut L6M/HOLD/PRE/X' % | p_plc | p_fam |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| REF stand-in | stand-in pct>=0.95 secs_fav>=5 take | -410 | -66 | 1,312 | 1,378 | -66 | 0 | 10.4 | 3.2 > 2.6 | 3.2 > 2.6 | -6.0/-3.8/-3.5/-2.8 | - | - |
| best_all | flow pulled_against_mult>=50 arm=0.9 persist=5 dd>=6 | 5 | 30 | 103 | 73 | 30 | 0 | 0.1 | 3.2 > 3.3 | 3.2 > 3.2 | 0.0/0.0/0.0/0.0 | 1.00 | 1.00 |
| best_pass | flow delta_mult>=2 arm=0.8 persist=1 dd>=0 | -1,113 | -776 | 6,916 | 7,692 | -776 | 0 | 25.0 | 3.2 > 0.0 | 3.2 > 0.0 | 2.3/4.3/-1.0/0.2 | 1.00 | 1.00 |

**best_pass_market = flow delta_mult>=2 arm=0.8 persist=1 dd>=0** (family c, v1.7: profit K7 * pct>=0.8 delta_mult>=2 take win=5 persist=1   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 0 (live rules 36); reached 80% closing at or below breakeven: 0 (live rules 78) -> PASS. Frozen live week: 0 / 0 (live rules 2 / 5) -> PASS. In plain words L6M: it removed 80 give-backs worth $168,945 and clipped 610 fills worth $187,912 (all in the 24-week window; per week 6,916 removed, 7,692 clipped). Live week: removed 6 worth $9,299, clipped 22 fills worth $7,126.
- Scorecard (per week; before > after): L6M: full stops 7.5 > 6.6 ($-10,783 > $-9,273), give-backs 3.2 > 0.0 ($-3,334 > $0), round trips 3.2 > 0.0, fills clipped 25.0 ($7,692), net -776; HOLD: full stops 6.8 > 5.9 ($-9,662 > $-8,392), give-backs 2.6 > 0.1 ($-2,681 > $28), round trips 2.6 > 0.0, fills clipped 21.8 ($6,840), net -1,280; PRE: full stops 5.1 > 4.4 ($-7,114 > $-6,205), give-backs 1.6 > 0.0 ($-1,409 > $18), round trips 1.5 > 0.0, fills clipped 14.5 ($4,446), net -1,282; X': full stops 4.5 > 4.0 ($-6,341 > $-5,578), give-backs 1.0 > 0.0 ($-918 > $18), round trips 0.8 > 0.0, fills clipped 8.9 ($2,663), net -600
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (4,312), wk 202623: 73,836 (-3,916), wk 202625: 59,099 (-1,626), wk 202639: 57,178 (-7,414), wk 202633: 52,499 (-3,968). Live week: this books Delta 2,172 on a live total of 103,596 -> week stays positive.

**best_pass = flow delta_mult>=2 arm=0.8 persist=1 dd>=0** (family c, v1.7: profit K7 * pct>=0.8 delta_mult>=2 take win=5 persist=1   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 0 (live rules 36); reached 80% closing at or below breakeven: 0 (live rules 78) -> PASS. Frozen live week: 0 / 0 (live rules 2 / 5) -> PASS. In plain words L6M: it removed 80 give-backs worth $168,945 and clipped 610 fills worth $187,912 (all in the 24-week window; per week 6,916 removed, 7,692 clipped). Live week: removed 6 worth $9,299, clipped 22 fills worth $7,126.
- Scorecard (per week; before > after): L6M: full stops 7.5 > 6.6 ($-10,783 > $-9,273), give-backs 3.2 > 0.0 ($-3,334 > $0), round trips 3.2 > 0.0, fills clipped 25.0 ($7,692), net -776; HOLD: full stops 6.8 > 5.9 ($-9,662 > $-8,392), give-backs 2.6 > 0.1 ($-2,681 > $28), round trips 2.6 > 0.0, fills clipped 21.8 ($6,840), net -1,280; PRE: full stops 5.1 > 4.4 ($-7,114 > $-6,205), give-backs 1.6 > 0.0 ($-1,409 > $18), round trips 1.5 > 0.0, fills clipped 14.5 ($4,446), net -1,282; X': full stops 4.5 > 4.0 ($-6,341 > $-5,578), give-backs 1.0 > 0.0 ($-918 > $18), round trips 0.8 > 0.0, fills clipped 8.9 ($2,663), net -600
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (4,312), wk 202623: 73,836 (-3,916), wk 202625: 59,099 (-1,626), wk 202639: 57,178 (-7,414), wk 202633: 52,499 (-3,968). Live week: this books Delta 2,172 on a live total of 103,596 -> week stays positive.

**best_market = flow pulled_against_mult>=50 arm=0.9 persist=5 dd>=6** (family c, v1.7: profit K7 * pct>=0.9 pulled_against_mult>=50 dd>=6 take win=5 persist=5   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 38 (live rules 36); reached 80% closing at or below breakeven: 77 (live rules 78) -> FAIL. Frozen live week: 2 / 5 (live rules 2 / 5) -> FAIL. In plain words L6M: it removed 1 give-backs worth $2,515 and clipped 2 fills worth $1,793 (all in the 24-week window; per week 103 removed, 73 clipped). Live week: removed 0 worth $0, clipped 0 fills worth $0.
- Scorecard (per week; before > after): L6M: full stops 7.5 > 7.5 ($-10,783 > $-10,688), give-backs 3.2 > 3.3 ($-3,334 > $-3,206), round trips 3.2 > 3.2, fills clipped 0.1 ($73), net 30; HOLD: full stops 6.8 > 6.7 ($-9,662 > $-9,616), give-backs 2.6 > 2.7 ($-2,681 > $-2,619), round trips 2.6 > 2.6, fills clipped 0.0 ($35), net 14; PRE: full stops 5.1 > 5.1 ($-7,114 > $-7,114), give-backs 1.6 > 1.6 ($-1,409 > $-1,397), round trips 1.5 > 1.5, fills clipped 0.0 ($16), net 7; X': full stops 4.5 > 4.5 ($-6,341 > $-6,341), give-backs 1.0 > 1.0 ($-918 > $-918), round trips 0.8 > 0.8, fills clipped 0.0 ($-0), net 0
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (0), wk 202623: 73,836 (0), wk 202625: 59,099 (0), wk 202639: 57,178 (0), wk 202633: 52,499 (0). Live week: this books Delta 0 on a live total of 103,596 -> week stays positive.

**best_all = flow pulled_against_mult>=50 arm=0.9 persist=5 dd>=6** (family c, v1.7: profit K7 * pct>=0.9 pulled_against_mult>=50 dd>=6 take win=5 persist=5   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 38 (live rules 36); reached 80% closing at or below breakeven: 77 (live rules 78) -> FAIL. Frozen live week: 2 / 5 (live rules 2 / 5) -> FAIL. In plain words L6M: it removed 1 give-backs worth $2,515 and clipped 2 fills worth $1,793 (all in the 24-week window; per week 103 removed, 73 clipped). Live week: removed 0 worth $0, clipped 0 fills worth $0.
- Scorecard (per week; before > after): L6M: full stops 7.5 > 7.5 ($-10,783 > $-10,688), give-backs 3.2 > 3.3 ($-3,334 > $-3,206), round trips 3.2 > 3.2, fills clipped 0.1 ($73), net 30; HOLD: full stops 6.8 > 6.7 ($-9,662 > $-9,616), give-backs 2.6 > 2.7 ($-2,681 > $-2,619), round trips 2.6 > 2.6, fills clipped 0.0 ($35), net 14; PRE: full stops 5.1 > 5.1 ($-7,114 > $-7,114), give-backs 1.6 > 1.6 ($-1,409 > $-1,397), round trips 1.5 > 1.5, fills clipped 0.0 ($16), net 7; X': full stops 4.5 > 4.5 ($-6,341 > $-6,341), give-backs 1.0 > 1.0 ($-918 > $-918), round trips 0.8 > 0.8, fills clipped 0.0 ($-0), net 0
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (0), wk 202623: 73,836 (0), wk 202625: 59,099 (0), wk 202639: 57,178 (0), wk 202633: 52,499 (0). Live week: this books Delta 0 on a live total of 103,596 -> week stays positive.

## M7

| row | rule | key $/wk | net L6M (all fires) | removed (zone) L6M | clipped L6M | removed-clipped | other saves | clipped fills/wk | GB/wk L6M before>after | RT/wk before>after | stack cut L6M/HOLD/PRE/X' % | p_plc | p_fam |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| REF stand-in | stand-in pct>=0.95 secs_fav>=5 take | -134 | 354 | 1,050 | 695 | 354 | 0 | 4.5 | 1.9 > 1.5 | 1.9 > 1.5 | -1.1/0.1/-2.3/-4.5 | - | - |
| best_all | ladder m1=0.7 f1=0.4 | .9 f2=0.7 | .95 f3=0.7 mode=1 + bank arm=0.9 F=0.33 lim lt=1 | floor 0.6 | 137 | 570 | 1,845 | 1,275 | 570 | 0 | 2.9 | 1.9 > 1.1 | 1.9 > 1.0 | 5.2/2.5/-5.1/-4.4 | 0.00 | 0.00 |
| best_market | flow pulled_against_mult>=20 arm=0.9 persist=5 dd>=2 | 93 | 606 | 1,390 | 784 | 606 | -0 | 1.4 | 1.9 > 2.0 | 1.9 > 1.2 | 4.2/1.7/-2.2/-2.5 | 0.58 | 0.75 |
| best_pass | flow pulled_mult>=5 arm=0.7 persist=3 dd>=0 | -371 | 513 | 3,745 | 5,736 | -1,991 | 2,504 | 13.8 | 1.9 > 0.0 | 1.9 > 0.0 | 10.5/2.2/-11.7/-12.9 | 0.17 | 1.00 |
| fam_a | ladder m1=0.7 f1=0.4 | .9 f2=0.7 | .95 f3=0.7 mode=1 | 23 | 795 | 3,186 | 4,372 | -1,186 | 1,981 | 6.0 | 1.9 > 5.2 | 1.9 > 0.0 | 9.9/7.8/-6.0/-2.6 | 0.00 | 0.00 |
| fam_b | rev arm=0.9 X=8 N=30 | 51 | 419 | 1,993 | 1,574 | 419 | -0 | 4.5 | 1.9 > 1.1 | 1.9 > 1.0 | 5.2/1.5/-6.9/-6.1 | 0.25 | 0.67 |
| fam_d | bank arm=0.9 F=0.33 mkt lt=1 | floor 0.6 | 68 | 379 | 1,668 | 1,289 | 379 | 0 | 2.2 | 1.9 > 1.2 | 1.9 > 1.0 | 3.6/3.0/-6.8/-5.2 | 0.42 | 0.83 |

**best_pass_market = flow pulled_mult>=5 arm=0.7 persist=3 dd>=0** (family c, v1.7: profit M7 * pct>=0.7 pulled_mult>=5 take win=5 persist=3   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 0 (live rules 23); reached 80% closing at or below breakeven: 0 (live rules 47) -> PASS. Frozen live week: 0 / 0 (live rules 2 / 2) -> PASS. In plain words L6M: it removed 47 give-backs worth $91,482 and clipped 337 fills worth $140,130 (all in the 24-week window; per week 3,745 removed, 5,736 clipped). Live week: removed 3 worth $2,912, clipped 13 fills worth $6,528.
- Scorecard (per week; before > after): L6M: full stops 1.2 > 0.9 ($-1,555 > $-1,035), give-backs 1.9 > 0.0 ($-1,841 > $0), round trips 1.9 > 0.0, fills clipped 13.8 ($5,736), net 513; HOLD: full stops 1.1 > 0.8 ($-1,469 > $-964), give-backs 1.7 > 0.0 ($-1,667 > $34), round trips 1.7 > 0.0, fills clipped 12.6 ($5,391), net 505; PRE: full stops 1.4 > 1.0 ($-1,923 > $-1,470), give-backs 1.0 > 0.1 ($-928 > $42), round trips 1.0 > 0.0, fills clipped 8.9 ($3,879), net -843; X': full stops 1.8 > 1.3 ($-2,506 > $-1,759), give-backs 0.8 > 0.0 ($-757 > $9), round trips 0.7 > 0.0, fills clipped 6.2 ($2,747), net -114
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (-2,385), wk 202623: 73,836 (3,952), wk 202625: 59,099 (-866), wk 202639: 57,178 (-2,311), wk 202633: 52,499 (-1,340). Live week: this books Delta -3,616 on a live total of 103,596 -> week stays positive.

**best_pass = flow pulled_mult>=5 arm=0.7 persist=3 dd>=0** (family c, v1.7: profit M7 * pct>=0.7 pulled_mult>=5 take win=5 persist=3   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 0 (live rules 23); reached 80% closing at or below breakeven: 0 (live rules 47) -> PASS. Frozen live week: 0 / 0 (live rules 2 / 2) -> PASS. In plain words L6M: it removed 47 give-backs worth $91,482 and clipped 337 fills worth $140,130 (all in the 24-week window; per week 3,745 removed, 5,736 clipped). Live week: removed 3 worth $2,912, clipped 13 fills worth $6,528.
- Scorecard (per week; before > after): L6M: full stops 1.2 > 0.9 ($-1,555 > $-1,035), give-backs 1.9 > 0.0 ($-1,841 > $0), round trips 1.9 > 0.0, fills clipped 13.8 ($5,736), net 513; HOLD: full stops 1.1 > 0.8 ($-1,469 > $-964), give-backs 1.7 > 0.0 ($-1,667 > $34), round trips 1.7 > 0.0, fills clipped 12.6 ($5,391), net 505; PRE: full stops 1.4 > 1.0 ($-1,923 > $-1,470), give-backs 1.0 > 0.1 ($-928 > $42), round trips 1.0 > 0.0, fills clipped 8.9 ($3,879), net -843; X': full stops 1.8 > 1.3 ($-2,506 > $-1,759), give-backs 0.8 > 0.0 ($-757 > $9), round trips 0.7 > 0.0, fills clipped 6.2 ($2,747), net -114
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (-2,385), wk 202623: 73,836 (3,952), wk 202625: 59,099 (-866), wk 202639: 57,178 (-2,311), wk 202633: 52,499 (-1,340). Live week: this books Delta -3,616 on a live total of 103,596 -> week stays positive.

**best_market = flow pulled_against_mult>=20 arm=0.9 persist=5 dd>=2** (family c, v1.7: profit M7 * pct>=0.9 pulled_against_mult>=20 dd>=2 take win=5 persist=5   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 25 (live rules 23); reached 80% closing at or below breakeven: 29 (live rules 47) -> FAIL. Frozen live week: 2 / 0 (live rules 2 / 2) -> FAIL. In plain words L6M: it removed 21 give-backs worth $33,958 and clipped 35 fills worth $19,151 (all in the 24-week window; per week 1,390 removed, 784 clipped). Live week: removed 2 worth $2,375, clipped 2 fills worth $1,155.
- Scorecard (per week; before > after): L6M: full stops 1.2 > 1.2 ($-1,555 > $-1,555), give-backs 1.9 > 2.0 ($-1,841 > $-630), round trips 1.9 > 1.2, fills clipped 1.4 ($784), net 606; HOLD: full stops 1.1 > 1.1 ($-1,469 > $-1,420), give-backs 1.7 > 1.9 ($-1,667 > $-602), round trips 1.7 > 1.1, fills clipped 1.3 ($757), net 434; PRE: full stops 1.4 > 1.4 ($-1,923 > $-1,905), give-backs 1.0 > 1.2 ($-928 > $-530), round trips 1.0 > 0.8, fills clipped 0.7 ($452), net -92; X': full stops 1.8 > 1.7 ($-2,506 > $-2,424), give-backs 0.8 > 0.9 ($-757 > $-547), round trips 0.7 > 0.6, fills clipped 0.2 ($133), net 39
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (1,439), wk 202623: 73,836 (4,643), wk 202625: 59,099 (643), wk 202639: 57,178 (-743), wk 202633: 52,499 (-463). Live week: this books Delta 1,219 on a live total of 103,596 -> week stays positive.

**best_all = ladder m1=0.7 f1=0.4 | .9 f2=0.7 | .95 f3=0.7 mode=1 + bank arm=0.9 F=0.33 lim lt=1 | floor 0.6** (family g, v1.7: not expressible; v1.8 fields: `mfe_pct` arm (running max favourable excursion as a fraction of target, not the current pct) + floor ladder action `floor m1:f1,m2:f2,m3:f3 [stoplimit]`; combination of the above fields (OR of lines; first to fire exits))

- Trader test L6M: trades that reached 90% closing below 50%: 2 (live rules 23); reached 80% closing at or below breakeven: 24 (live rules 47) -> FAIL. Frozen live week: 0 / 0 (live rules 2 / 2) -> PASS. In plain words L6M: it removed 23 give-backs worth $45,077 and clipped 72 fills worth $31,156 (all in the 24-week window; per week 1,845 removed, 1,275 clipped). Live week: removed 2 worth $3,128, clipped 2 fills worth $836.
- Scorecard (per week; before > after): L6M: full stops 1.2 > 1.2 ($-1,555 > $-1,506), give-backs 1.9 > 1.1 ($-1,841 > $-874), round trips 1.9 > 1.0, fills clipped 2.9 ($1,275), net 570; HOLD: full stops 1.1 > 1.0 ($-1,469 > $-1,350), give-backs 1.7 > 0.9 ($-1,667 > $-750), round trips 1.7 > 0.8, fills clipped 2.7 ($1,202), net 540; PRE: full stops 1.4 > 1.3 ($-1,923 > $-1,858), give-backs 1.0 > 0.6 ($-928 > $-507), round trips 1.0 > 0.6, fills clipped 2.0 ($923), net -99; X': full stops 1.8 > 1.7 ($-2,506 > $-2,315), give-backs 0.8 > 0.5 ($-757 > $-343), round trips 0.7 > 0.4, fills clipped 1.2 ($520), net 222
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (1,571), wk 202623: 73,836 (4,768), wk 202625: 59,099 (-474), wk 202639: 57,178 (-839), wk 202633: 52,499 (-737). Live week: this books Delta 2,291 on a live total of 103,596 -> week stays positive.

## U7

| row | rule | key $/wk | net L6M (all fires) | removed (zone) L6M | clipped L6M | removed-clipped | other saves | clipped fills/wk | GB/wk L6M before>after | RT/wk before>after | stack cut L6M/HOLD/PRE/X' % | p_plc | p_fam |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| REF stand-in | stand-in pct>=0.95 secs_fav>=5 take | -362 | -314 | 372 | 686 | -314 | 0 | 2.3 | 0.7 > 0.6 | 0.7 > 0.6 | -3.7/-1.6/-1.5/3.2 | - | - |
| best_all | flow pulled_against_mult>=20 arm=0.7 persist=5 dd>=6 | 158 | 1,583 | 2,561 | 2,129 | 432 | 1,151 | 1.4 | 0.7 > 1.1 | 0.7 > 0.1 | 15.0/-3.8/2.7/-8.3 | 0.92 | 0.92 |
| best_pass | ladder m1=0.7 f1=0.65 | .9 f2=0.8 | .95 f3=0.8 mode=1 + rev arm=0.7 X=8 N=3 + zone arm=.8 N=480 floor 0.5 | 110 | 748 | 3,325 | 4,569 | -1,244 | 1,992 | 4.4 | 0.7 > 0.0 | 0.7 > 0.0 | 15.5/-7.1/16.0/0.5 | 0.00 | 0.00 |
| best_pass_market | flow pulled_mult>=5 arm=0.7 persist=5 dd>=0 | -63 | 152 | 3,489 | 5,334 | -1,845 | 1,997 | 5.6 | 0.7 > 0.0 | 0.7 > 0.0 | 15.4/-2.6/16.3/-2.0 | 0.00 | 1.00 |
| fam_a | ladder m1=0.7 f1=0.65 | .9 f2=0.8 | .95 f3=0.8 mode=1 | 98 | 746 | 3,317 | 4,563 | -1,245 | 1,992 | 4.4 | 0.7 > 0.0 | 0.7 > 0.0 | 15.5/-7.1/15.8/0.4 | 0.00 | 0.00 |
| fam_b | rev arm=0.7 X=15 N=3 | 73 | 294 | 854 | 640 | 214 | 79 | 0.2 | 0.7 > 0.8 | 0.7 > 0.6 | -5.2/-3.7/-0.5/3.3 | 0.25 | 0.75 |
| fam_g | ladder m1=0.7 f1=0.65 | .9 f2=0.8 | .95 f3=0.8 mode=1 + rev arm=0.7 X=8 N=3 | 110 | 748 | 3,325 | 4,569 | -1,244 | 1,992 | 4.4 | 0.7 > 0.0 | 0.7 > 0.0 | 15.5/-7.1/16.0/0.5 | 0.00 | 0.00 |

**best_pass_market = flow pulled_mult>=5 arm=0.7 persist=5 dd>=0** (family c, v1.7: profit U7 * pct>=0.7 pulled_mult>=5 take win=5 persist=5   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 0 (live rules 4); reached 80% closing at or below breakeven: 0 (live rules 16) -> PASS. Frozen live week: 0 / 0 (live rules 0 / 0) -> PASS. In plain words L6M: it removed 16 give-backs worth $85,231 and clipped 137 fills worth $130,297 (all in the 24-week window; per week 3,489 removed, 5,334 clipped). Live week: removed 0 worth $0, clipped 2 fills worth $785.
- Scorecard (per week; before > after): L6M: full stops 2.5 > 1.8 ($-7,644 > $-5,434), give-backs 0.7 > 0.0 ($-1,881 > $0), round trips 0.7 > 0.0, fills clipped 5.6 ($5,334), net 152; HOLD: full stops 2.5 > 1.7 ($-7,473 > $-5,293), give-backs 0.6 > 0.0 ($-1,619 > $35), round trips 0.6 > 0.0, fills clipped 4.8 ($4,542), net 230; PRE: full stops 1.6 > 1.1 ($-5,194 > $-3,543), give-backs 0.3 > 0.0 ($-912 > $22), round trips 0.3 > 0.0, fills clipped 3.4 ($3,107), net 27; X': full stops 1.2 > 0.9 ($-3,971 > $-2,841), give-backs 0.2 > 0.0 ($-274 > $54), round trips 0.1 > 0.0, fills clipped 2.4 ($2,229), net -119
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (-6,601), wk 202623: 73,836 (-7,568), wk 202625: 59,099 (-5,743), wk 202639: 57,178 (-3,642), wk 202633: 52,499 (-1,880). Live week: this books Delta -785 on a live total of 103,596 -> week stays positive.

**best_pass = ladder m1=0.7 f1=0.65 | .9 f2=0.8 | .95 f3=0.8 mode=1 + rev arm=0.7 X=8 N=3 + zone arm=.8 N=480 floor 0.5** (family g, v1.7: not expressible; v1.8 fields: `mfe_pct` arm (running max favourable excursion as a fraction of target, not the current pct) + floor ladder action `floor m1:f1,m2:f2,m3:f3 [stoplimit]`; combination of the above fields (OR of lines; first to fire exits))

- Trader test L6M: trades that reached 90% closing below 50%: 0 (live rules 4); reached 80% closing at or below breakeven: 0 (live rules 16) -> PASS. Frozen live week: 0 / 0 (live rules 0 / 0) -> PASS. In plain words L6M: it removed 16 give-backs worth $81,236 and clipped 108 fills worth $111,624 (all in the 24-week window; per week 3,325 removed, 4,569 clipped). Live week: removed 0 worth $0, clipped 0 fills worth $0.
- Scorecard (per week; before > after): L6M: full stops 2.5 > 1.8 ($-7,644 > $-5,434), give-backs 0.7 > 0.0 ($-1,881 > $0), round trips 0.7 > 0.0, fills clipped 4.4 ($4,569), net 748; HOLD: full stops 2.5 > 1.7 ($-7,473 > $-5,293), give-backs 0.6 > 0.1 ($-1,619 > $71), round trips 0.6 > 0.0, fills clipped 3.9 ($4,129), net 485; PRE: full stops 1.6 > 1.1 ($-5,194 > $-3,543), give-backs 0.3 > 0.0 ($-912 > $14), round trips 0.3 > 0.0, fills clipped 2.9 ($2,842), net 230; X': full stops 1.2 > 0.9 ($-3,971 > $-2,841), give-backs 0.2 > 0.0 ($-274 > $24), round trips 0.1 > 0.0, fills clipped 2.2 ($2,181), net -66
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (-4,360), wk 202623: 73,836 (-7,216), wk 202625: 59,099 (-2,991), wk 202639: 57,178 (-3,907), wk 202633: 52,499 (-452). Live week: this books Delta 0 on a live total of 103,596 -> week stays positive.

**best_market = flow pulled_against_mult>=20 arm=0.7 persist=5 dd>=6** (family c, v1.7: profit U7 * pct>=0.7 pulled_against_mult>=20 dd>=6 take win=5 persist=5   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 17 (live rules 4); reached 80% closing at or below breakeven: 3 (live rules 16) -> FAIL. Frozen live week: 0 / 0 (live rules 0 / 0) -> PASS. In plain words L6M: it removed 16 give-backs worth $62,556 and clipped 33 fills worth $52,014 (all in the 24-week window; per week 2,561 removed, 2,129 clipped). Live week: removed 0 worth $0, clipped 0 fills worth $0.
- Scorecard (per week; before > after): L6M: full stops 2.5 > 1.8 ($-7,644 > $-5,434), give-backs 0.7 > 1.1 ($-1,881 > $793), round trips 0.7 > 0.1, fills clipped 1.4 ($2,129), net 1,583; HOLD: full stops 2.5 > 1.8 ($-7,473 > $-5,412), give-backs 0.6 > 1.0 ($-1,619 > $690), round trips 0.6 > 0.1, fills clipped 1.2 ($1,996), net 1,064; PRE: full stops 1.6 > 1.3 ($-5,194 > $-4,139), give-backs 0.3 > 0.7 ($-912 > $220), round trips 0.3 > 0.2, fills clipped 0.9 ($1,548), net -95; X': full stops 1.2 > 1.1 ($-3,971 > $-3,464), give-backs 0.2 > 0.4 ($-274 > $16), round trips 0.1 > 0.1, fills clipped 0.4 ($655), net -343
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (0), wk 202623: 73,836 (-1,381), wk 202625: 59,099 (0), wk 202639: 57,178 (0), wk 202633: 52,499 (1,532). Live week: this books Delta 0 on a live total of 103,596 -> week stays positive.

**best_all = flow pulled_against_mult>=20 arm=0.7 persist=5 dd>=6** (family c, v1.7: profit U7 * pct>=0.7 pulled_against_mult>=20 dd>=6 take win=5 persist=5   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 17 (live rules 4); reached 80% closing at or below breakeven: 3 (live rules 16) -> FAIL. Frozen live week: 0 / 0 (live rules 0 / 0) -> PASS. In plain words L6M: it removed 16 give-backs worth $62,556 and clipped 33 fills worth $52,014 (all in the 24-week window; per week 2,561 removed, 2,129 clipped). Live week: removed 0 worth $0, clipped 0 fills worth $0.
- Scorecard (per week; before > after): L6M: full stops 2.5 > 1.8 ($-7,644 > $-5,434), give-backs 0.7 > 1.1 ($-1,881 > $793), round trips 0.7 > 0.1, fills clipped 1.4 ($2,129), net 1,583; HOLD: full stops 2.5 > 1.8 ($-7,473 > $-5,412), give-backs 0.6 > 1.0 ($-1,619 > $690), round trips 0.6 > 0.1, fills clipped 1.2 ($1,996), net 1,064; PRE: full stops 1.6 > 1.3 ($-5,194 > $-4,139), give-backs 0.3 > 0.7 ($-912 > $220), round trips 0.3 > 0.2, fills clipped 0.9 ($1,548), net -95; X': full stops 1.2 > 1.1 ($-3,971 > $-3,464), give-backs 0.2 > 0.4 ($-274 > $16), round trips 0.1 > 0.1, fills clipped 0.4 ($655), net -343
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (0), wk 202623: 73,836 (-1,381), wk 202625: 59,099 (0), wk 202639: 57,178 (0), wk 202633: 52,499 (1,532). Live week: this books Delta 0 on a live total of 103,596 -> week stays positive.

## H7

| row | rule | key $/wk | net L6M (all fires) | removed (zone) L6M | clipped L6M | removed-clipped | other saves | clipped fills/wk | GB/wk L6M before>after | RT/wk before>after | stack cut L6M/HOLD/PRE/X' % | p_plc | p_fam |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| REF stand-in | stand-in pct>=0.95 secs_fav>=5 take | -134 | 42 | 89 | 47 | 42 | 0 | 1.4 | 0.5 > 0.5 | 0.5 > 0.5 | 2.0/-0.3/-0.8/-2.3 | - | - |
| best_all | flow pulled_against_mult>=20 arm=0.8 persist=3 dd>=4 | 162 | 169 | 1,081 | 912 | 169 | -0 | 1.4 | 0.5 > 0.7 | 0.5 > 0.0 | 2.7/2.5/-2.3/9.3 | 0.42 | 0.42 |
| best_pass | ladder m1=0.8 f1=0.4 | .9 f2=0.5 | .95 f3=0.7 mode=1 + rev arm=0.8 X=4 N=5 + zone arm=.8 N=240 floor 0.5 | 131 | 152 | 1,444 | 1,293 | 152 | -0 | 2.5 | 0.5 > 0.0 | 0.5 > 0.0 | 1.4/3.4/-3.0/12.3 | 0.17 | 0.42 |
| best_pass_market | rev arm=0.8 X=4 N=5 | 130 | 152 | 1,444 | 1,293 | 152 | -0 | 2.5 | 0.5 > 0.0 | 0.5 > 0.0 | 1.4/3.4/-3.0/11.2 | 0.17 | 0.42 |
| fam_a | ladder m1=0.8 f1=0.4 | .9 f2=0.6 | .95 f3=0.7 mode=1 | 24 | 24 | 1,092 | 1,068 | 24 | -0 | 1.2 | 0.5 > 1.0 | 0.5 > 0.0 | 2.4/3.3/-0.6/13.7 | 0.08 | 0.67 |
| fam_e | stall arm=0.8 N=3 ticks=2 work=20s | 52 | 110 | 1,475 | 1,364 | 110 | 0 | 3.4 | 0.5 > 0.0 | 0.5 > 0.0 | -0.6/1.5/-3.7/13.5 | 1.00 | 1.00 |

**best_pass_market = rev arm=0.8 X=4 N=5** (family b, v1.7: not expressible; v1.8 fields: `retrace>=X within N` feature (max of last N s minus current, pts) armed at `mfe_pct>=m`)

- Trader test L6M: trades that reached 90% closing below 50%: 0 (live rules 4); reached 80% closing at or below breakeven: 0 (live rules 13) -> PASS. Frozen live week: 0 / 0 (live rules 0 / 0) -> PASS. In plain words L6M: it removed 13 give-backs worth $35,284 and clipped 62 fills worth $31,583 (all in the 24-week window; per week 1,444 removed, 1,293 clipped). Live week: removed 0 worth $0, clipped 1 fills worth $303.
- Scorecard (per week; before > after): L6M: full stops 0.8 > 0.6 ($-1,215 > $-1,022), give-backs 0.5 > 0.0 ($-603 > $0), round trips 0.5 > 0.0, fills clipped 2.5 ($1,293), net 152; HOLD: full stops 1.0 > 0.8 ($-1,707 > $-1,478), give-backs 0.4 > 0.0 ($-502 > $11), round trips 0.4 > 0.0, fills clipped 1.9 ($903), net 194; PRE: full stops 0.8 > 0.7 ($-1,731 > $-1,499), give-backs 0.3 > 0.1 ($-416 > $106), round trips 0.3 > 0.0, fills clipped 1.6 ($901), net -100; X': full stops 1.2 > 1.0 ($-2,658 > $-2,084), give-backs 0.4 > 0.3 ($-717 > $184), round trips 0.4 > 0.0, fills clipped 1.2 ($700), net 560
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (1,959), wk 202623: 73,836 (-4,309), wk 202625: 59,099 (-1,631), wk 202639: 57,178 (0), wk 202633: 52,499 (-723). Live week: this books Delta -303 on a live total of 103,596 -> week stays positive.

**best_pass = ladder m1=0.8 f1=0.4 | .9 f2=0.5 | .95 f3=0.7 mode=1 + rev arm=0.8 X=4 N=5 + zone arm=.8 N=240 floor 0.5** (family g, v1.7: not expressible; v1.8 fields: `mfe_pct` arm (running max favourable excursion as a fraction of target, not the current pct) + floor ladder action `floor m1:f1,m2:f2,m3:f3 [stoplimit]`; combination of the above fields (OR of lines; first to fire exits))

- Trader test L6M: trades that reached 90% closing below 50%: 0 (live rules 4); reached 80% closing at or below breakeven: 0 (live rules 13) -> PASS. Frozen live week: 0 / 0 (live rules 0 / 0) -> PASS. In plain words L6M: it removed 13 give-backs worth $35,284 and clipped 62 fills worth $31,583 (all in the 24-week window; per week 1,444 removed, 1,293 clipped). Live week: removed 0 worth $0, clipped 1 fills worth $303.
- Scorecard (per week; before > after): L6M: full stops 0.8 > 0.6 ($-1,215 > $-1,022), give-backs 0.5 > 0.0 ($-603 > $0), round trips 0.5 > 0.0, fills clipped 2.5 ($1,293), net 152; HOLD: full stops 1.0 > 0.8 ($-1,707 > $-1,478), give-backs 0.4 > 0.0 ($-502 > $12), round trips 0.4 > 0.0, fills clipped 2.0 ($917), net 180; PRE: full stops 0.8 > 0.7 ($-1,731 > $-1,499), give-backs 0.3 > 0.2 ($-416 > $203), round trips 0.3 > 0.0, fills clipped 1.7 ($949), net -127; X': full stops 1.2 > 1.0 ($-2,658 > $-2,084), give-backs 0.4 > 0.3 ($-717 > $341), round trips 0.4 > 0.0, fills clipped 1.2 ($722), net 611
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (1,959), wk 202623: 73,836 (-4,309), wk 202625: 59,099 (-1,631), wk 202639: 57,178 (0), wk 202633: 52,499 (-723). Live week: this books Delta -303 on a live total of 103,596 -> week stays positive.

**best_market = flow pulled_against_mult>=20 arm=0.8 persist=3 dd>=4** (family c, v1.7: profit H7 * pct>=0.8 pulled_against_mult>=20 dd>=4 take win=5 persist=3   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 12 (live rules 4); reached 80% closing at or below breakeven: 0 (live rules 13) -> FAIL. Frozen live week: 0 / 0 (live rules 0 / 0) -> PASS. In plain words L6M: it removed 13 give-backs worth $26,414 and clipped 35 fills worth $22,286 (all in the 24-week window; per week 1,081 removed, 912 clipped). Live week: removed 0 worth $0, clipped 0 fills worth $0.
- Scorecard (per week; before > after): L6M: full stops 0.8 > 0.6 ($-1,215 > $-1,022), give-backs 0.5 > 0.7 ($-603 > $411), round trips 0.5 > 0.0, fills clipped 1.4 ($912), net 169; HOLD: full stops 1.0 > 0.8 ($-1,707 > $-1,478), give-backs 0.4 > 0.5 ($-502 > $249), round trips 0.4 > 0.0, fills clipped 1.1 ($661), net 179; PRE: full stops 0.8 > 0.7 ($-1,731 > $-1,520), give-backs 0.3 > 0.4 ($-416 > $89), round trips 0.3 > 0.1, fills clipped 0.7 ($540), net -15; X': full stops 1.2 > 1.1 ($-2,658 > $-2,269), give-backs 0.4 > 0.3 ($-717 > $-81), round trips 0.4 > 0.2, fills clipped 0.2 ($163), net 621
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (1,954), wk 202623: 73,836 (-1,825), wk 202625: 59,099 (-263), wk 202639: 57,178 (0), wk 202633: 52,499 (-690). Live week: this books Delta 0 on a live total of 103,596 -> week stays positive.

**best_all = flow pulled_against_mult>=20 arm=0.8 persist=3 dd>=4** (family c, v1.7: profit H7 * pct>=0.8 pulled_against_mult>=20 dd>=4 take win=5 persist=3   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 12 (live rules 4); reached 80% closing at or below breakeven: 0 (live rules 13) -> FAIL. Frozen live week: 0 / 0 (live rules 0 / 0) -> PASS. In plain words L6M: it removed 13 give-backs worth $26,414 and clipped 35 fills worth $22,286 (all in the 24-week window; per week 1,081 removed, 912 clipped). Live week: removed 0 worth $0, clipped 0 fills worth $0.
- Scorecard (per week; before > after): L6M: full stops 0.8 > 0.6 ($-1,215 > $-1,022), give-backs 0.5 > 0.7 ($-603 > $411), round trips 0.5 > 0.0, fills clipped 1.4 ($912), net 169; HOLD: full stops 1.0 > 0.8 ($-1,707 > $-1,478), give-backs 0.4 > 0.5 ($-502 > $249), round trips 0.4 > 0.0, fills clipped 1.1 ($661), net 179; PRE: full stops 0.8 > 0.7 ($-1,731 > $-1,520), give-backs 0.3 > 0.4 ($-416 > $89), round trips 0.3 > 0.1, fills clipped 0.7 ($540), net -15; X': full stops 1.2 > 1.1 ($-2,658 > $-2,269), give-backs 0.4 > 0.3 ($-717 > $-81), round trips 0.4 > 0.2, fills clipped 0.2 ($163), net 621
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (1,954), wk 202623: 73,836 (-1,825), wk 202625: 59,099 (-263), wk 202639: 57,178 (0), wk 202633: 52,499 (-690). Live week: this books Delta 0 on a live total of 103,596 -> week stays positive.

## A7

| row | rule | key $/wk | net L6M (all fires) | removed (zone) L6M | clipped L6M | removed-clipped | other saves | clipped fills/wk | GB/wk L6M before>after | RT/wk before>after | stack cut L6M/HOLD/PRE/X' % | p_plc | p_fam |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| REF stand-in | stand-in pct>=0.95 secs_fav>=5 take | -166 | -166 | 155 | 321 | -166 | -0 | 2.8 | 0.7 > 0.6 | 0.7 > 0.6 | 0.9/-0.2/-0.6/-1.4 | - | - |
| best_all | flow wall_ahead_mult>=12 arm=0.8 persist=5 dd>=4 | 21 | 117 | 386 | 269 | 117 | -0 | 0.5 | 0.7 > 0.7 | 0.7 > 0.5 | 0.3/-0.5/-1.2/-0.2 | 0.42 | 0.42 |
| best_pass | ladder m1=0.8 f1=0.65 | .9 f2=0.7 | .95 f3=0.9 mode=1 | -347 | -347 | 1,069 | 1,416 | -347 | 0 | 4.1 | 0.7 > 0.0 | 0.7 > 0.0 | -3.1/-1.0/-1.2/-2.3 | 0.00 | 1.00 |
| best_pass_market | flow delta_mult>=2 arm=0.8 persist=3 dd>=0 | -446 | -446 | 1,140 | 1,585 | -446 | -0 | 5.7 | 0.7 > 0.0 | 0.7 > 0.0 | -3.2/-1.1/-1.6/-1.8 | 0.33 | 1.00 |

**best_pass_market = flow delta_mult>=2 arm=0.8 persist=3 dd>=0** (family c, v1.7: profit A7 * pct>=0.8 delta_mult>=2 take win=5 persist=3   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 0 (live rules 4); reached 80% closing at or below breakeven: 0 (live rules 16) -> PASS. Frozen live week: 0 / 0 (live rules 1 / 2) -> PASS. In plain words L6M: it removed 16 give-backs worth $27,842 and clipped 140 fills worth $38,727 (all in the 24-week window; per week 1,140 removed, 1,585 clipped). Live week: removed 3 worth $3,150, clipped 2 fills worth $553.
- Scorecard (per week; before > after): L6M: full stops 2.0 > 1.8 ($-2,418 > $-2,176), give-backs 0.7 > 0.0 ($-567 > $0), round trips 0.7 > 0.0, fills clipped 5.7 ($1,585), net -446; HOLD: full stops 1.6 > 1.5 ($-1,899 > $-1,711), give-backs 0.5 > 0.0 ($-429 > $0), round trips 0.5 > 0.0, fills clipped 4.6 ($1,290), net -401; PRE: full stops 0.7 > 0.6 ($-861 > $-732), give-backs 0.2 > 0.0 ($-216 > $0), round trips 0.2 > 0.0, fills clipped 2.4 ($660), net -253; X': full stops 0.8 > 0.6 ($-900 > $-763), give-backs 0.2 > 0.0 ($-182 > $0), round trips 0.2 > 0.0, fills clipped 1.5 ($401), net -28
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (-1,438), wk 202623: 73,836 (-2,071), wk 202625: 59,099 (-2,749), wk 202639: 57,178 (934), wk 202633: 52,499 (-1,266). Live week: this books Delta 2,597 on a live total of 103,596 -> week stays positive.

**best_pass = ladder m1=0.8 f1=0.65 | .9 f2=0.7 | .95 f3=0.9 mode=1** (family a, v1.7: not expressible; v1.8 fields: `mfe_pct` arm (running max favourable excursion as a fraction of target, not the current pct) + floor ladder action `floor m1:f1,m2:f2,m3:f3 [stoplimit]`)

- Trader test L6M: trades that reached 90% closing below 50%: 0 (live rules 4); reached 80% closing at or below breakeven: 0 (live rules 16) -> PASS. Frozen live week: 0 / 0 (live rules 1 / 2) -> PASS. In plain words L6M: it removed 16 give-backs worth $26,123 and clipped 100 fills worth $34,598 (all in the 24-week window; per week 1,069 removed, 1,416 clipped). Live week: removed 3 worth $2,839, clipped 4 fills worth $1,056.
- Scorecard (per week; before > after): L6M: full stops 2.0 > 1.8 ($-2,418 > $-2,176), give-backs 0.7 > 0.0 ($-567 > $23), round trips 0.7 > 0.0, fills clipped 4.1 ($1,416), net -347; HOLD: full stops 1.6 > 1.5 ($-1,899 > $-1,711), give-backs 0.5 > 0.0 ($-429 > $11), round trips 0.5 > 0.0, fills clipped 3.3 ($1,181), net -350; PRE: full stops 0.7 > 0.6 ($-861 > $-732), give-backs 0.2 > 0.0 ($-216 > $0), round trips 0.2 > 0.0, fills clipped 1.6 ($572), net -179; X': full stops 0.8 > 0.6 ($-900 > $-763), give-backs 0.2 > 0.0 ($-182 > $0), round trips 0.2 > 0.0, fills clipped 1.0 ($365), net -21
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (-1,877), wk 202623: 73,836 (-1,218), wk 202625: 59,099 (-2,692), wk 202639: 57,178 (414), wk 202633: 52,499 (-986). Live week: this books Delta 1,783 on a live total of 103,596 -> week stays positive.

**best_market = flow wall_ahead_mult>=12 arm=0.8 persist=5 dd>=4** (family c, v1.7: profit A7 * pct>=0.8 wall_ahead_mult>=12 dd>=4 take win=8 persist=5 wall_ticks=8   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 7 (live rules 4); reached 80% closing at or below breakeven: 11 (live rules 16) -> FAIL. Frozen live week: 1 / 2 (live rules 1 / 2) -> FAIL. In plain words L6M: it removed 8 give-backs worth $9,433 and clipped 12 fills worth $6,579 (all in the 24-week window; per week 386 removed, 269 clipped). Live week: removed 1 worth $280, clipped 0 fills worth $0.
- Scorecard (per week; before > after): L6M: full stops 2.0 > 2.0 ($-2,418 > $-2,323), give-backs 0.7 > 0.7 ($-567 > $-184), round trips 0.7 > 0.5, fills clipped 0.5 ($269), net 117; HOLD: full stops 1.6 > 1.6 ($-1,899 > $-1,829), give-backs 0.5 > 0.6 ($-429 > $-127), round trips 0.5 > 0.3, fills clipped 0.4 ($248), net 63; PRE: full stops 0.7 > 0.7 ($-861 > $-764), give-backs 0.2 > 0.3 ($-216 > $-31), round trips 0.2 > 0.1, fills clipped 0.4 ($197), net -45; X': full stops 0.8 > 0.6 ($-900 > $-763), give-backs 0.2 > 0.3 ($-182 > $50), round trips 0.2 > 0.0, fills clipped 0.4 ($218), net 39
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (-648), wk 202623: 73,836 (-1,065), wk 202625: 59,099 (0), wk 202639: 57,178 (495), wk 202633: 52,499 (-575). Live week: this books Delta 280 on a live total of 103,596 -> week stays positive.

**best_all = flow wall_ahead_mult>=12 arm=0.8 persist=5 dd>=4** (family c, v1.7: profit A7 * pct>=0.8 wall_ahead_mult>=12 dd>=4 take win=8 persist=5 wall_ticks=8   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 7 (live rules 4); reached 80% closing at or below breakeven: 11 (live rules 16) -> FAIL. Frozen live week: 1 / 2 (live rules 1 / 2) -> FAIL. In plain words L6M: it removed 8 give-backs worth $9,433 and clipped 12 fills worth $6,579 (all in the 24-week window; per week 386 removed, 269 clipped). Live week: removed 1 worth $280, clipped 0 fills worth $0.
- Scorecard (per week; before > after): L6M: full stops 2.0 > 2.0 ($-2,418 > $-2,323), give-backs 0.7 > 0.7 ($-567 > $-184), round trips 0.7 > 0.5, fills clipped 0.5 ($269), net 117; HOLD: full stops 1.6 > 1.6 ($-1,899 > $-1,829), give-backs 0.5 > 0.6 ($-429 > $-127), round trips 0.5 > 0.3, fills clipped 0.4 ($248), net 63; PRE: full stops 0.7 > 0.7 ($-861 > $-764), give-backs 0.2 > 0.3 ($-216 > $-31), round trips 0.2 > 0.1, fills clipped 0.4 ($197), net -45; X': full stops 0.8 > 0.6 ($-900 > $-763), give-backs 0.2 > 0.3 ($-182 > $50), round trips 0.2 > 0.0, fills clipped 0.4 ($218), net 39
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (-648), wk 202623: 73,836 (-1,065), wk 202625: 59,099 (0), wk 202639: 57,178 (495), wk 202633: 52,499 (-575). Live week: this books Delta 280 on a live total of 103,596 -> week stays positive.

## O7

| row | rule | key $/wk | net L6M (all fires) | removed (zone) L6M | clipped L6M | removed-clipped | other saves | clipped fills/wk | GB/wk L6M before>after | RT/wk before>after | stack cut L6M/HOLD/PRE/X' % | p_plc | p_fam |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| REF stand-in | stand-in pct>=0.95 secs_fav>=5 take | -18 | -18 | 0 | 18 | -18 | 0 | 0.1 | 0.1 > 0.1 | 0.0 > 0.0 | 0.0/0.0/0.0/-0.6 | - | - |
| best_all | flow pulled_mult>=30 arm=0.7 persist=5 dd>=0 | 16 | 62 | 72 | 50 | 22 | 40 | 0.0 | 0.1 > 0.1 | 0.0 > 0.0 | 0.0/1.1/0.0/0.0 | 0.58 | 0.67 |
| best_pass | flow pulled_against_mult>=20 arm=0.8 persist=3 dd>=2 | -25 | -17 | 137 | 155 | -17 | 0 | 0.3 | 0.1 > 0.0 | 0.0 > 0.0 | 0.6/0.0/-0.0/0.0 | 0.00 | 1.00 |
| fam_b | rev arm=0.9 X=15 N=5 | 12 | 21 | 21 | -0 | 21 | 0 | 0.0 | 0.1 > 0.1 | 0.0 > 0.0 | 0.0/0.0/0.0/0.0 | 0.08 | 0.42 |
| fam_g | rev arm=0.9 X=15 N=5 + bank arm=0.9 F=0.33 lim lt=1 | floor 0.4 | 12 | 21 | 21 | -0 | 21 | 0 | 0.0 | 0.1 > 0.1 | 0.0 > 0.0 | 0.0/0.0/0.0/0.0 | 0.08 | 0.08 |

**best_pass_market = flow pulled_against_mult>=20 arm=0.8 persist=3 dd>=2** (family c, v1.7: profit O7 * pct>=0.8 pulled_against_mult>=20 dd>=2 take win=5 persist=3   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 0 (live rules 2); reached 80% closing at or below breakeven: 0 (live rules 1) -> PASS. Frozen live week: 0 / 0 (live rules 0 / 0) -> PASS. In plain words L6M: it removed 3 give-backs worth $3,352 and clipped 8 fills worth $3,779 (all in the 24-week window; per week 137 removed, 155 clipped). Live week: removed 0 worth $0, clipped 0 fills worth $0.
- Scorecard (per week; before > after): L6M: full stops 0.3 > 0.3 ($-233 > $-202), give-backs 0.1 > 0.0 ($34 > $0), round trips 0.0 > 0.0, fills clipped 0.3 ($155), net -17; HOLD: full stops 0.3 > 0.3 ($-218 > $-203), give-backs 0.2 > 0.1 ($133 > $50), round trips 0.0 > 0.0, fills clipped 0.3 ($137), net 24; PRE: full stops 0.3 > 0.3 ($-220 > $-199), give-backs 0.2 > 0.1 ($46 > $41), round trips 0.1 > 0.0, fills clipped 0.4 ($194), net -54; X': full stops 0.7 > 0.7 ($-543 > $-543), give-backs 0.2 > 0.1 ($39 > $21), round trips 0.0 > 0.0, fills clipped 0.0 ($28), net -12
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (0), wk 202623: 73,836 (0), wk 202625: 59,099 (0), wk 202639: 57,178 (-1,078), wk 202633: 52,499 (0). Live week: this books Delta 0 on a live total of 103,596 -> week stays positive.

**best_pass = flow pulled_against_mult>=20 arm=0.8 persist=3 dd>=2** (family c, v1.7: profit O7 * pct>=0.8 pulled_against_mult>=20 dd>=2 take win=5 persist=3   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 0 (live rules 2); reached 80% closing at or below breakeven: 0 (live rules 1) -> PASS. Frozen live week: 0 / 0 (live rules 0 / 0) -> PASS. In plain words L6M: it removed 3 give-backs worth $3,352 and clipped 8 fills worth $3,779 (all in the 24-week window; per week 137 removed, 155 clipped). Live week: removed 0 worth $0, clipped 0 fills worth $0.
- Scorecard (per week; before > after): L6M: full stops 0.3 > 0.3 ($-233 > $-202), give-backs 0.1 > 0.0 ($34 > $0), round trips 0.0 > 0.0, fills clipped 0.3 ($155), net -17; HOLD: full stops 0.3 > 0.3 ($-218 > $-203), give-backs 0.2 > 0.1 ($133 > $50), round trips 0.0 > 0.0, fills clipped 0.3 ($137), net 24; PRE: full stops 0.3 > 0.3 ($-220 > $-199), give-backs 0.2 > 0.1 ($46 > $41), round trips 0.1 > 0.0, fills clipped 0.4 ($194), net -54; X': full stops 0.7 > 0.7 ($-543 > $-543), give-backs 0.2 > 0.1 ($39 > $21), round trips 0.0 > 0.0, fills clipped 0.0 ($28), net -12
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (0), wk 202623: 73,836 (0), wk 202625: 59,099 (0), wk 202639: 57,178 (-1,078), wk 202633: 52,499 (0). Live week: this books Delta 0 on a live total of 103,596 -> week stays positive.

**best_market = flow pulled_mult>=30 arm=0.7 persist=5 dd>=0** (family c, v1.7: profit O7 * pct>=0.7 pulled_mult>=30 take win=5 persist=5   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 3 (live rules 2); reached 80% closing at or below breakeven: 0 (live rules 1) -> FAIL. Frozen live week: 0 / 0 (live rules 0 / 0) -> PASS. In plain words L6M: it removed 1 give-backs worth $1,755 and clipped 1 fills worth $1,215 (all in the 24-week window; per week 72 removed, 50 clipped). Live week: removed 0 worth $0, clipped 0 fills worth $0.
- Scorecard (per week; before > after): L6M: full stops 0.3 > 0.3 ($-233 > $-202), give-backs 0.1 > 0.1 ($34 > $90), round trips 0.0 > 0.0, fills clipped 0.0 ($50), net 62; HOLD: full stops 0.3 > 0.3 ($-218 > $-188), give-backs 0.2 > 0.2 ($133 > $144), round trips 0.0 > 0.0, fills clipped 0.0 ($41), net 75; PRE: full stops 0.3 > 0.3 ($-220 > $-210), give-backs 0.2 > 0.2 ($46 > $51), round trips 0.1 > 0.1, fills clipped 0.0 ($24), net -5; X': full stops 0.7 > 0.7 ($-543 > $-543), give-backs 0.2 > 0.2 ($39 > $39), round trips 0.0 > 0.0, fills clipped 0.0 ($-0), net 0
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (0), wk 202623: 73,836 (0), wk 202625: 59,099 (0), wk 202639: 57,178 (0), wk 202633: 52,499 (0). Live week: this books Delta 0 on a live total of 103,596 -> week stays positive.

**best_all = flow pulled_mult>=30 arm=0.7 persist=5 dd>=0** (family c, v1.7: profit O7 * pct>=0.7 pulled_mult>=30 take win=5 persist=5   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 3 (live rules 2); reached 80% closing at or below breakeven: 0 (live rules 1) -> FAIL. Frozen live week: 0 / 0 (live rules 0 / 0) -> PASS. In plain words L6M: it removed 1 give-backs worth $1,755 and clipped 1 fills worth $1,215 (all in the 24-week window; per week 72 removed, 50 clipped). Live week: removed 0 worth $0, clipped 0 fills worth $0.
- Scorecard (per week; before > after): L6M: full stops 0.3 > 0.3 ($-233 > $-202), give-backs 0.1 > 0.1 ($34 > $90), round trips 0.0 > 0.0, fills clipped 0.0 ($50), net 62; HOLD: full stops 0.3 > 0.3 ($-218 > $-188), give-backs 0.2 > 0.2 ($133 > $144), round trips 0.0 > 0.0, fills clipped 0.0 ($41), net 75; PRE: full stops 0.3 > 0.3 ($-220 > $-210), give-backs 0.2 > 0.2 ($46 > $51), round trips 0.1 > 0.1, fills clipped 0.0 ($24), net -5; X': full stops 0.7 > 0.7 ($-543 > $-543), give-backs 0.2 > 0.2 ($39 > $39), round trips 0.0 > 0.0, fills clipped 0.0 ($-0), net 0
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 88,836 (0), wk 202623: 73,836 (0), wk 202625: 59,099 (0), wk 202639: 57,178 (0), wk 202633: 52,499 (0). Live week: this books Delta 0 on a live total of 103,596 -> week stays positive.

## 20 largest give-backs replayed (L6M and frozen live week), best_market finalist per book

### P7x L6M (flow pulled_against_mult>=5 arm=0.7 persist=1 dd>=0): live rules vs finalist

| entry | book | lots | MFE % | live closed % | finalist closed % | note |
|---|---|---|---|---|---|---|
| 08-26 03:03Z | P7 | 12 | 93% | -85% | 68% | rule exit |
| 09-10 05:07Z | P7 | 12 | 96% | -72% | 68% | rule exit |
| 07-28 05:40Z | P7 | 12 | 94% | -71% | 67% | rule exit |
| 10-20 05:16Z | P7 | 12 | 86% | -72% | 73% | rule exit |
| 07-02 22:07Z | P7 | 12 | 80% | -74% | 73% | rule exit |
| 09-11 02:43Z | P7 | 12 | 89% | -50% | 68% | rule exit |
| 06-29 01:23Z | P7 | 12 | 95% | -32% | 67% | rule exit |
| 06-01 00:38Z | P7 | 12 | 91% | -29% | 69% | rule exit |
| 06-19 05:03Z | P7 | 12 | 92% | -27% | 66% | rule exit |
| 05-22 10:05Z | P7 | 7 | 84% | -100% | 70% | rule exit |
| 06-25 10:42Z | P7 | 7 | 92% | -89% | 72% | rule exit |
| 07-24 03:10Z | P7 | 12 | 99% | -3% | 68% | rule exit |
| 07-13 23:23Z | P7 | 6 | 95% | -77% | 67% | rule exit |
| 08-13 14:24Z | P7 | 7 | 96% | -71% | 66% | rule exit |
| 07-02 15:16Z | P7 | 7 | 88% | -78% | 86% | rule exit |
| 07-23 15:25Z | P7 | 7 | 97% | -66% | 68% | rule exit |
| 08-07 01:39Z | P7 | 6 | 93% | -72% | 78% | rule exit |
| 09-08 10:18Z | P7 | 7 | 90% | -71% | 86% | rule exit |
| 06-04 00:40Z | P7 | 6 | 86% | -77% | 72% | rule exit |
| 07-28 02:14Z | P7 | 6 | 95% | -67% | 64% | rule exit |

### P7x live week (flow pulled_against_mult>=5 arm=0.7 persist=1 dd>=0): live rules vs finalist

| entry | book | lots | MFE % | live closed % | finalist closed % | note |
|---|---|---|---|---|---|---|
| 11-03 23:13Z | P7 | 12 | 84% | -77% | 72% | rule exit |
| 11-04 05:53Z | P7 | 12 | 81% | -48% | 62% | rule exit |
| 11-02 23:47Z | P7 | 6 | 91% | -50% | 77% | rule exit |

### P7 L6M (flow pulled_against_mult>=5 arm=0.7 persist=1 dd>=0): live rules vs finalist

| entry | book | lots | MFE % | live closed % | finalist closed % | note |
|---|---|---|---|---|---|---|
| 08-26 03:03Z | P7 | 7 | 93% | -85% | 68% | rule exit |
| 09-10 05:07Z | P7 | 7 | 96% | -72% | 68% | rule exit |
| 07-28 05:40Z | P7 | 7 | 94% | -71% | 67% | rule exit |
| 10-20 05:16Z | P7 | 7 | 86% | -72% | 73% | rule exit |
| 07-02 22:07Z | P7 | 7 | 80% | -74% | 73% | rule exit |
| 09-11 02:43Z | P7 | 7 | 89% | -50% | 68% | rule exit |
| 06-29 01:23Z | P7 | 7 | 95% | -32% | 67% | rule exit |
| 06-01 00:38Z | P7 | 7 | 91% | -29% | 69% | rule exit |
| 06-19 05:03Z | P7 | 7 | 92% | -27% | 66% | rule exit |
| 05-22 10:05Z | P7 | 4 | 84% | -100% | 70% | rule exit |
| 06-25 10:42Z | P7 | 4 | 92% | -89% | 72% | rule exit |
| 07-24 03:10Z | P7 | 7 | 99% | -3% | 68% | rule exit |
| 07-13 23:23Z | P7 | 4 | 95% | -77% | 67% | rule exit |
| 08-13 14:24Z | P7 | 4 | 96% | -71% | 66% | rule exit |
| 07-02 15:16Z | P7 | 4 | 88% | -78% | 86% | rule exit |
| 08-07 01:39Z | P7 | 4 | 93% | -72% | 78% | rule exit |
| 06-04 00:40Z | P7 | 4 | 86% | -77% | 72% | rule exit |
| 07-28 02:14Z | P7 | 4 | 95% | -67% | 64% | rule exit |
| 07-23 15:25Z | P7 | 4 | 97% | -66% | 68% | rule exit |
| 10-19 03:21Z | P7 | 4 | 94% | -69% | 67% | rule exit |

### P7 live week (flow pulled_against_mult>=5 arm=0.7 persist=1 dd>=0): live rules vs finalist

| entry | book | lots | MFE % | live closed % | finalist closed % | note |
|---|---|---|---|---|---|---|
| 11-03 23:13Z | P7 | 7 | 84% | -77% | 72% | rule exit |
| 11-04 05:53Z | P7 | 7 | 81% | -48% | 62% | rule exit |
| 11-02 23:47Z | P7 | 4 | 91% | -50% | 77% | rule exit |

### K7 L6M (flow delta_mult>=2 arm=0.8 persist=1 dd>=0): live rules vs finalist

| entry | book | lots | MFE % | live closed % | finalist closed % | note |
|---|---|---|---|---|---|---|
| 09-18 06:51Z | K7 | 2 | 98% | -101% | 85% | rule exit |
| 06-04 11:36Z | K7 | 2 | 95% | -98% | 83% | rule exit |
| 10-21 16:42Z | K7 | 2 | 95% | -96% | 78% | rule exit |
| 07-27 06:03Z | K7 | 2 | 94% | -97% | 84% | rule exit |
| 07-07 16:45Z | K7 | 2 | 91% | -96% | 73% | rule exit |
| 07-31 05:09Z | K7 | 2 | 87% | -98% | 77% | rule exit |
| 08-26 03:21Z | K7 | 2 | 88% | -96% | 70% | rule exit |
| 08-05 22:24Z | K7 | 2 | 80% | -103% | 73% | rule exit |
| 07-17 10:30Z | K7 | 2 | 86% | -83% | 72% | rule exit |
| 10-08 18:18Z | K7 | 2 | 97% | -71% | 95% | rule exit |
| 07-14 05:45Z | K7 | 2 | 92% | -66% | 83% | rule exit |
| 07-07 06:57Z | K7 | 2 | 89% | -69% | 85% | rule exit |
| 06-22 06:54Z | K7 | 2 | 90% | -66% | 77% | rule exit |
| 10-27 12:18Z | K7 | 2 | 90% | -59% | 82% | rule exit |
| 05-15 17:54Z | K7 | 2 | 81% | -65% | 69% | rule exit |
| 07-13 04:24Z | K7 | 2 | 85% | -39% | 83% | rule exit |
| 06-23 03:33Z | K7 | 2 | 80% | -32% | 75% | rule exit |
| 05-18 18:39Z | K7 | 1 | 84% | -123% | 75% | rule exit |
| 06-11 04:21Z | K7 | 1 | 86% | -115% | 83% | rule exit |
| 05-15 12:27Z | K7 | 1 | 90% | -106% | 82% | rule exit |

### K7 live week (flow delta_mult>=2 arm=0.8 persist=1 dd>=0): live rules vs finalist

| entry | book | lots | MFE % | live closed % | finalist closed % | note |
|---|---|---|---|---|---|---|
| 11-03 23:06Z | K7 | 2 | 88% | -74% | 51% | rule exit |
| 11-05 08:12Z | K7 | 1 | 98% | -58% | 75% | rule exit |
| 11-03 15:57Z | K7 | 1 | 82% | -54% | 61% | rule exit |
| 11-04 19:33Z | K7 | 1 | 83% | -50% | 74% | rule exit |
| 11-05 02:18Z | K7 | 1 | 84% | -48% | 70% | rule exit |
| 11-02 01:09Z | K7 | 1 | 95% | 45% | 81% | rule exit |

### M7 L6M (flow pulled_mult>=5 arm=0.7 persist=3 dd>=0): live rules vs finalist

| entry | book | lots | MFE % | live closed % | finalist closed % | note |
|---|---|---|---|---|---|---|
| 05-22 10:05Z | M7 | 2 | 85% | -100% | 69% | rule exit |
| 07-22 06:46Z | M7 | 2 | 98% | -76% | 82% | rule exit |
| 09-18 06:56Z | M7 | 2 | 98% | -73% | 74% | rule exit |
| 06-04 11:36Z | M7 | 2 | 95% | -65% | 67% | rule exit |
| 06-02 07:33Z | M7 | 2 | 93% | -67% | 66% | rule exit |
| 06-23 06:58Z | M7 | 2 | 98% | -58% | 63% | rule exit |
| 09-08 09:57Z | M7 | 2 | 88% | -65% | 68% | rule exit |
| 07-30 07:29Z | M7 | 2 | 96% | -54% | 71% | rule exit |
| 07-08 06:14Z | M7 | 2 | 86% | -53% | 70% | rule exit |
| 10-28 14:35Z | M7 | 1 | 82% | -129% | 74% | rule exit |
| 10-26 08:40Z | M7 | 1 | 92% | -101% | 64% | rule exit |
| 05-20 15:16Z | M7 | 1 | 90% | -94% | 50% | rule exit |
| 10-21 06:05Z | M7 | 1 | 80% | -100% | 71% | rule exit |
| 09-15 08:30Z | M7 | 1 | 81% | -94% | 69% | rule exit |
| 07-06 14:13Z | M7 | 1 | 86% | -83% | 79% | rule exit |
| 09-30 07:16Z | M7 | 1 | 97% | -72% | 65% | rule exit |
| 10-21 10:02Z | M7 | 1 | 92% | -72% | 63% | rule exit |
| 10-05 08:43Z | M7 | 1 | 85% | -78% | 68% | rule exit |
| 07-14 15:08Z | M7 | 1 | 96% | -67% | 64% | rule exit |
| 06-04 06:10Z | M7 | 1 | 82% | -79% | 77% | rule exit |

### M7 live week (flow pulled_mult>=5 arm=0.7 persist=3 dd>=0): live rules vs finalist

| entry | book | lots | MFE % | live closed % | finalist closed % | note |
|---|---|---|---|---|---|---|
| 11-05 10:08Z | M7 | 1 | 98% | -62% | 63% | rule exit |
| 11-02 15:22Z | M7 | 1 | 95% | -59% | 63% | rule exit |
| 11-02 11:58Z | M7 | 1 | 87% | 70% | 65% | rule exit |

### U7 L6M (flow pulled_mult>=5 arm=0.7 persist=5 dd>=0): live rules vs finalist

| entry | book | lots | MFE % | live closed % | finalist closed % | note |
|---|---|---|---|---|---|---|
| 09-02 09:00Z | U7 | 4 | 83% | -99% | 77% | rule exit |
| 05-27 23:40Z | U7 | 4 | 86% | -95% | 76% | rule exit |
| 06-08 05:40Z | U7 | 4 | 81% | -99% | 67% | rule exit |
| 10-15 23:30Z | U7 | 4 | 94% | -61% | 77% | rule exit |
| 08-04 00:40Z | U7 | 4 | 85% | -59% | 72% | rule exit |
| 05-14 09:30Z | U7 | 4 | 85% | -57% | 67% | rule exit |
| 05-19 07:10Z | U7 | 4 | 82% | -61% | 68% | rule exit |
| 07-31 06:40Z | U7 | 2 | 97% | -106% | 83% | rule exit |
| 07-30 01:30Z | U7 | 2 | 100% | -98% | 71% | rule exit |
| 09-10 01:00Z | U7 | 2 | 82% | -110% | 74% | rule exit |
| 10-19 08:00Z | U7 | 2 | 92% | -100% | 77% | rule exit |
| 07-28 08:30Z | U7 | 2 | 84% | -101% | 65% | rule exit |
| 10-26 10:50Z | U7 | 2 | 85% | -100% | 61% | rule exit |
| 10-20 02:00Z | U7 | 2 | 83% | -92% | 74% | rule exit |
| 08-23 23:30Z | U7 | 2 | 85% | -79% | 71% | rule exit |
| 08-14 00:50Z | U7 | 2 | 82% | -56% | 63% | rule exit |

### U7 live week (flow pulled_mult>=5 arm=0.7 persist=5 dd>=0): live rules vs finalist

| entry | book | lots | MFE % | live closed % | finalist closed % | note |
|---|---|---|---|---|---|---|

### H7 L6M (rev arm=0.8 X=4 N=5): live rules vs finalist

| entry | book | lots | MFE % | live closed % | finalist closed % | note |
|---|---|---|---|---|---|---|
| 10-11 23:25Z | H7 | 4 | 84% | -44% | 72% | rule exit |
| 07-22 22:05Z | H7 | 4 | 84% | -21% | 79% | rule exit |
| 06-12 00:25Z | H7 | 2 | 94% | -59% | 82% | rule exit |
| 06-22 04:10Z | H7 | 2 | 92% | -50% | 68% | rule exit |
| 08-07 03:45Z | H7 | 2 | 84% | -52% | 73% | rule exit |
| 07-28 02:30Z | H7 | 2 | 90% | -38% | 79% | rule exit |
| 06-24 14:20Z | H7 | 1 | 89% | -106% | 76% | rule exit |
| 10-08 14:25Z | H7 | 1 | 86% | -101% | 73% | rule exit |
| 09-04 14:45Z | H7 | 1 | 88% | -98% | 79% | rule exit |
| 08-28 00:20Z | H7 | 1 | 98% | -86% | 64% | rule exit |
| 09-29 15:25Z | H7 | 1 | 92% | -87% | 78% | rule exit |
| 06-25 23:20Z | H7 | 1 | 85% | -54% | 72% | rule exit |
| 05-19 14:20Z | H7 | 1 | 80% | -28% | 68% | rule exit |

### H7 live week (rev arm=0.8 X=4 N=5): live rules vs finalist

| entry | book | lots | MFE % | live closed % | finalist closed % | note |
|---|---|---|---|---|---|---|

### A7 L6M (flow delta_mult>=2 arm=0.8 persist=3 dd>=0): live rules vs finalist

| entry | book | lots | MFE % | live closed % | finalist closed % | note |
|---|---|---|---|---|---|---|
| 06-23 03:24Z | A7 | 1 | 86% | -98% | 75% | rule exit |
| 07-02 01:17Z | A7 | 1 | 85% | -99% | 79% | rule exit |
| 07-28 22:54Z | A7 | 1 | 82% | -100% | 54% | rule exit |
| 10-14 02:00Z | A7 | 1 | 85% | -97% | 76% | rule exit |
| 05-27 23:41Z | A7 | 1 | 81% | -97% | 53% | rule exit |
| 06-24 05:12Z | A7 | 1 | 96% | -81% | 89% | rule exit |
| 06-24 02:51Z | A7 | 1 | 91% | -83% | 78% | rule exit |
| 09-22 00:05Z | A7 | 1 | 85% | -79% | 80% | rule exit |
| 10-20 02:17Z | A7 | 1 | 86% | -77% | 75% | rule exit |
| 08-07 01:48Z | A7 | 1 | 89% | -60% | 77% | rule exit |
| 08-26 02:51Z | A7 | 1 | 95% | -52% | 83% | rule exit |
| 06-11 22:21Z | A7 | 1 | 89% | -57% | 60% | rule exit |
| 05-14 03:31Z | A7 | 1 | 84% | -62% | 71% | rule exit |
| 10-13 02:01Z | A7 | 1 | 83% | -59% | 76% | rule exit |
| 05-13 23:14Z | A7 | 1 | 87% | -37% | 69% | rule exit |
| 05-21 23:16Z | A7 | 1 | 94% | -10% | 75% | rule exit |

### A7 live week (flow delta_mult>=2 arm=0.8 persist=3 dd>=0): live rules vs finalist

| entry | book | lots | MFE % | live closed % | finalist closed % | note |
|---|---|---|---|---|---|---|
| 11-04 03:02Z | A7 | 1 | 84% | -53% | 69% | rule exit |
| 11-02 03:13Z | A7 | 1 | 82% | -33% | 75% | rule exit |
| 11-02 01:12Z | A7 | 1 | 91% | 42% | 75% | rule exit |

### O7 L6M (flow pulled_against_mult>=20 arm=0.8 persist=3 dd>=2): live rules vs finalist

| entry | book | lots | MFE % | live closed % | finalist closed % | note |
|---|---|---|---|---|---|---|
| 07-13 13:45Z | O7 | 1 | 87% | -42% | 71% | rule exit |
| 05-27 13:43Z | O7 | 1 | 93% | 42% | 87% | rule exit |
| 08-26 13:42Z | O7 | 1 | 93% | 48% | 76% | rule exit |

### O7 live week (flow pulled_against_mult>=20 arm=0.8 persist=3 dd>=2): live rules vs finalist

| entry | book | lots | MFE % | live closed % | finalist closed % | note |
|---|---|---|---|---|---|---|
