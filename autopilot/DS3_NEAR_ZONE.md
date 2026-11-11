# DS3_NEAR_ZONE - T-NEAR-ZONE: "dont be a dick for a tick" (page written Wed Nov 11 08:37:01 PM UTC 2026)

STATUS: Shadow only, post-hoc, no PASS claims (PASS/FAIL below is the trader acceptance test of the order, nothing more). Evidence table: DS3_NEAR_ZONE_TABLE.md (published 19:33Z, before any rule). Prereg NEAR_ZONE_PREREG.md (sha in DECISIONS.md). FIRST-ORDER scores on the LPB_BASE stored 1-s paths (43 months; L6M = 2026-05-12..10-30), slip 1.2 market, fees 4.84/lot, base = live panel rules as in LPB_BASE; exact rows in section 6. P7 is run at 12/7/7 lots (P7x, the users lots) and on the installed 7/4/4 table. Objective: give-back $ removed minus fills clipped $ per week; key = min(L6M, 43 months) net $/wk. Standing trader principle (19:45Z) applied: scorecard items a, b, e below, c and d (re-entry streaks) are untouched by exit-side rules in this first-order frame and are W-Qs tool to confirm.

**Fill models (stated; profit side unmeasured).** market = mid at the next second minus 1.2 pt (central; REDO-R9 low 0.57 / high 1.6 not re-run); resting stop-limit floor (mode=1) = fills at the floor minus 0.25 pt if the 1-s mid did not gap more than 1.5 pt through it, else market at the next second: OPTIMISTIC (no queue / partial-fill loss), so every mode=1, limit and work row is an upper bound and the market rows are the base case; passive limit (bank, work-the-exit) = fills at price minus 0.25 only if a later mid trades through it by one tick within the wait, else market at the end of the wait. Engine market exits are about 0.4 pt cheaper than live (1.2 pt adverse, DS3_DN_STOPFILL); code/th_ptr/market_slip.json is not on the box so REDO-R9 1.2 is used; the profit-side take slip is unmeasured. Floors act on a 1-s mid; a gap inside one second is not seen.

**Placebo / family null.** forward-only time-shift placebo (every cell fires as before but exits a random 10-300 s later, 12 reps); p_plc = share of reps with key >= the cell, p_fam = share of reps where the best cell of the same family reaches it (family g = top-150 combos only, p_fam optimistic there). With 12 reps the smallest p is 0.08: read p <= 0.10 as the floor.

## P7 at 12/7/7 lots

| row | rule | key $/wk | net L6M | removed L6M | clipped L6M | clipped fills/wk | GB/wk L6M before>after | RT/wk before>after | stack cut L6M/HOLD/PRE/X' % | p_plc | p_fam |
|---|---|---|---|---|---|---|---|---|---|---|---|
| REF stand-in | stand-in pct>=0.95 secs_fav>=5 take | 679 | 2,757 | 4,003 | 1,246 | 8.3 | 2.0 > 1.7 | 2.0 > 1.7 | 11.2/11.2/5.3/-2.1 | - | - |
| best_all | flow pulled_against_mult>=20 arm=0.8 persist=1 dd>=0 | 1,986 | 2,669 | 20,675 | 18,006 | 13.1 | 2.0 > 1.1 | 2.0 > 0.2 | 11.2/-9.0/21.8/6.7 | 0.00 | 0.00 |
| fam_a | ladder m1=0.7 f1=0.65 | .9 f2=0.7 | .95 f3=0.9 mode=1 | 1,609 | 4,235 | 20,545 | 31,637 | 15.3 | 2.0 > 0.1 | 2.0 > 0.0 | 51.9/22.7/32.8/42.7 | 0.00 | 0.00 |
| fam_b | rev arm=0.7 X=8 N=3 | 1,146 | 5,224 | 13,641 | 16,618 | 5.1 | 2.0 > 3.6 | 2.0 > 0.9 | 42.6/7.2/20.5/29.7 | 0.00 | 0.00 |
| fam_e | stall arm=0.9 N=3 ticks=0 work=20s | 1,213 | 4,362 | 11,637 | 7,275 | 13.8 | 2.0 > 1.2 | 2.0 > 1.1 | 20.0/2.9/16.2/20.0 | 1.00 | 1.00 |
| fam_g | ladder m1=0.7 f1=0.65 | .9 f2=0.7 | .95 f3=0.9 mode=1 + zone arm=.8 N=240 floor 0.8 | 1,638 | 4,542 | 20,661 | 31,446 | 15.4 | 2.0 > 0.1 | 2.0 > 0.0 | 51.9/22.7/33.2/43.1 | 0.00 | 0.00 |

**best_market = flow pulled_against_mult>=20 arm=0.8 persist=1 dd>=0** (family c, v1.7: profit P7 * pct>=0.8 pulled_against_mult>=20 take win=5 persist=1   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 22 (live rules 24); reached 80% closing at or below breakeven: 5 (live rules 50) -> FAIL. Frozen live week: 4 / 1 (live rules 1 / 3) -> FAIL. In plain words L6M: it removed 49 give-backs worth $505,061 and clipped 321 fills worth $439,855 (all in the 24-week window; per week 20,675 removed, 18,006 clipped). Live week: removed 3 worth $33,118, clipped 19 fills worth $65,879.
- Scorecard (per week; before > after): L6M: full stops 0.6 > 0.5 ($-2,207 > $-1,558), give-backs 2.0 > 1.1 ($-10,194 > $2,122), round trips 2.0 > 0.2, fills clipped 13.1 ($18,006), net 2,669; HOLD: full stops 0.4 > 0.3 ($-1,543 > $-1,035), give-backs 2.0 > 1.2 ($-9,503 > $2,385), round trips 2.0 > 0.2, fills clipped 11.6 ($16,732), net 1,787; PRE: full stops 0.4 > 0.4 ($-1,438 > $-1,204), give-backs 1.5 > 1.2 ($-6,451 > $2,007), round trips 1.4 > 0.2, fills clipped 5.6 ($8,742), net 3,237; X': full stops 0.4 > 0.4 ($-1,393 > $-1,393), give-backs 0.8 > 1.0 ($-3,695 > $1,001), round trips 0.7 > 0.2, fills clipped 1.7 ($3,929), net 697
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 132,671 (-21,789), wk 202623: 96,586 (16,036), wk 202625: 87,393 (-5,680), wk 202624: 79,831 (-4,525), wk 202639: 77,688 (-18,125). Live week: this books Delta -32,760 on a live total of 103,596 -> week stays positive.

**best_all = flow pulled_against_mult>=20 arm=0.8 persist=1 dd>=0** (family c, v1.7: profit P7 * pct>=0.8 pulled_against_mult>=20 take win=5 persist=1   [v1.7 grammar as is]; v1.8 fields: none (v1.7 expresses it))

- Trader test L6M: trades that reached 90% closing below 50%: 22 (live rules 24); reached 80% closing at or below breakeven: 5 (live rules 50) -> FAIL. Frozen live week: 4 / 1 (live rules 1 / 3) -> FAIL. In plain words L6M: it removed 49 give-backs worth $505,061 and clipped 321 fills worth $439,855 (all in the 24-week window; per week 20,675 removed, 18,006 clipped). Live week: removed 3 worth $33,118, clipped 19 fills worth $65,879.
- Scorecard (per week; before > after): L6M: full stops 0.6 > 0.5 ($-2,207 > $-1,558), give-backs 2.0 > 1.1 ($-10,194 > $2,122), round trips 2.0 > 0.2, fills clipped 13.1 ($18,006), net 2,669; HOLD: full stops 0.4 > 0.3 ($-1,543 > $-1,035), give-backs 2.0 > 1.2 ($-9,503 > $2,385), round trips 2.0 > 0.2, fills clipped 11.6 ($16,732), net 1,787; PRE: full stops 0.4 > 0.4 ($-1,438 > $-1,204), give-backs 1.5 > 1.2 ($-6,451 > $2,007), round trips 1.4 > 0.2, fills clipped 5.6 ($8,742), net 3,237; X': full stops 0.4 > 0.4 ($-1,393 > $-1,393), give-backs 0.8 > 1.0 ($-3,695 > $1,001), round trips 0.7 > 0.2, fills clipped 1.7 ($3,929), net 697
- Trend weeks (five best L6M stack weeks, base $ > this book rule delta $): wk 202638: 132,671 (-21,789), wk 202623: 96,586 (16,036), wk 202625: 87,393 (-5,680), wk 202624: 79,831 (-4,525), wk 202639: 77,688 (-18,125). Live week: this books Delta -32,760 on a live total of 103,596 -> week stays positive.

## 20 largest give-backs replayed (L6M and frozen live week), best_market finalist per book

### P7x L6M (flow pulled_against_mult>=20 arm=0.8 persist=1 dd>=0): live rules vs finalist

| entry | book | lots | MFE % | live closed % | finalist closed % | note |
|---|---|---|---|---|---|---|
| 08-26 03:03Z | P7 | 12 | 93% | -85% | 67% | rule exit |
| 09-10 05:07Z | P7 | 12 | 96% | -72% | 62% | rule exit |
| 07-28 05:40Z | P7 | 12 | 94% | -71% | 77% | rule exit |
| 10-20 05:16Z | P7 | 12 | 86% | -72% | 70% | rule exit |
| 07-02 22:07Z | P7 | 12 | 80% | -74% | 67% | rule exit |
| 09-11 02:43Z | P7 | 12 | 89% | -50% | 58% | rule exit |
| 06-29 01:23Z | P7 | 12 | 95% | -32% | 83% | rule exit |
| 06-01 00:38Z | P7 | 12 | 91% | -29% | 81% | rule exit |
| 06-19 05:03Z | P7 | 12 | 92% | -27% | 39% | rule exit |
| 05-22 10:05Z | P7 | 7 | 84% | -100% | 49% | rule exit |
| 06-25 10:42Z | P7 | 7 | 92% | -89% | 82% | rule exit |
| 07-24 03:10Z | P7 | 12 | 99% | -3% | 84% | rule exit |
| 07-13 23:23Z | P7 | 6 | 95% | -77% | 62% | rule exit |
| 08-13 14:24Z | P7 | 7 | 96% | -71% | 87% | rule exit |
| 07-02 15:16Z | P7 | 7 | 88% | -78% | 86% | rule exit |
| 07-23 15:25Z | P7 | 7 | 97% | -66% | 42% | rule exit |
| 08-07 01:39Z | P7 | 6 | 93% | -72% | 87% | rule exit |
| 09-08 10:18Z | P7 | 7 | 90% | -71% | 59% | rule exit |
| 06-04 00:40Z | P7 | 6 | 86% | -77% | 47% | rule exit |
| 07-28 02:14Z | P7 | 6 | 95% | -67% | 86% | rule exit |

### P7x live week (flow pulled_against_mult>=20 arm=0.8 persist=1 dd>=0): live rules vs finalist

| entry | book | lots | MFE % | live closed % | finalist closed % | note |
|---|---|---|---|---|---|---|
| 11-03 23:13Z | P7 | 12 | 84% | -77% | -45% | rule exit |
| 11-04 05:53Z | P7 | 12 | 81% | -48% | 76% | rule exit |
| 11-02 23:47Z | P7 | 6 | 91% | -50% | 80% | rule exit |
