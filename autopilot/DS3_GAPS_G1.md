# DS3_GAPS_G1 - LIVE-vs-ENGINE RULE AUDIT (written 2026-11-12 19:22Z UTC; Shadow only, no PASS claims)

**Live data used:** `StratTrades_DS7_<acct>_BLINDWEEK_reconstructed.csv` only (187 trades, entries 2026-11-01 18:36:00 .. exits 2026-11-05 11:05:34 ET, label days 2026-11-02, 2026-11-03, 2026-11-04, 2026-11-05). **The 11-02..12 live CSVs, the 11-09..12 live cuts and the Monday CSV are NOT on the box**; 11-11/12 rows below rest on the facts the user supplied (autopilot/DS3_P7_CUT_FIDELITY.md, DS3_LIVE_CUT_BUG.md), not on a log. v1.9a source is not on the box (~/DS7.cs is v1.4). Re-run for a new live file: `python3 -I code/th_gaps/rule_audit.py --live PATH --append-morning`.

**Engine:** exact state-base trade lists `FW2_LPB_EMPTY` (live-panel base, no layers) and `FW2_JN05W2` (+ v1.9 layers) month 202611, restricted to entries inside the live window. The engine state days 11-02..11 exist; the engine fires on 11-06..11 are listed in section 6 with no live comparison. Chart/live clock US/Eastern (UTC-5 since 11-01); label day rolls 18:00 ET.

## 1. Exit classes per book: ENGINE vs LIVE in the live window

Live class map: PolicyCut+ThL2Cut = loss cut; PolicyTake = profit take line; ThL2Trail = tighten/trail; BookLock; Stop/StopJoin/StopJoinFallback = stop; Target. Engine: StateCut = loss cut; StackCut; EarlyCut (v1.9 FLAT45K only); no engine take/trail lines exist.

| book | side | cut | take | trail | lock | stackcut | stop | flat | target | total |
|--|--|--|--|--|--|--|--|--|--|--|
| K7 | LIVE | 30 | 0 | 1 | 1 | 0 | 1 | 0 | 31 | 64 |
| K7 | ENGINE | 23 | 0 | 0 | 1 | 0 | 8 | 0 | 36 | 68 |
| P7 | LIVE | 24 | 0 | 0 | 1 | 0 | 0 | 0 | 28 | 53 |
| P7 | ENGINE | 20 | 0 | 0 | 1 | 0 | 0 | 0 | 26 | 47 |
| U7 | LIVE | 3 | 0 | 0 | 0 | 0 | 0 | 0 | 3 | 6 |
| U7 | ENGINE | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 5 | 7 |
| H7 | LIVE | 2 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 3 |
| H7 | ENGINE | 2 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 3 |
| M7 | LIVE | 13 | 1 | 0 | 0 | 0 | 1 | 0 | 13 | 28 |
| M7 | ENGINE | 17 | 0 | 0 | 0 | 0 | 1 | 0 | 14 | 32 |
| A7 | LIVE | 14 | 0 | 1 | 1 | 0 | 0 | 0 | 7 | 23 |
| A7 | ENGINE | 7 | 0 | 0 | 2 | 1 | 0 | 0 | 9 | 19 |
| O7 | LIVE | 2 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 3 |
| O7 | ENGINE | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 2 | 3 |
| X3 | LIVE | 2 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 3 |
| X3 | ENGINE | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| X4 | LIVE | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 2 |
| X4 | ENGINE | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| X5 | LIVE | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 2 |
| X5 | ENGINE | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| ALL | LIVE | 92 | 2 | 2 | 3 | 0 | 2 | 0 | 86 | 187 |
| ALL | ENGINE | 71 | 0 | 0 | 4 | 1 | 10 | 0 | 93 | 179 |

Live other exit names: {}. Live split of the cut class: {'ThL2Cut': 53, 'PolicyCut': 39}.

## 2. Trade pairing (same book, same side, entry within 180 s)

Live trades 187; paired with an engine trade 133; live-only entries 54; engine-only entries (in window) 46.

| book | live | paired | live-only | engine-only |
|--|--|--|--|--|
| K7 | 64 | 54 | 10 | 14 |
| P7 | 53 | 32 | 21 | 15 |
| U7 | 6 | 5 | 1 | 2 |
| H7 | 3 | 3 | 0 | 0 |
| M7 | 28 | 21 | 7 | 11 |
| A7 | 23 | 15 | 8 | 4 |
| O7 | 3 | 3 | 0 | 0 |
| X3 | 3 | 0 | 3 | 0 |
| X4 | 2 | 0 | 2 | 0 |
| X5 | 2 | 0 | 2 | 0 |

## 3. RULE-LEVEL FIRES (engine fires vs live fires per book) and first mismatching trade

| rule | installed live? | book | ENGINE fires | LIVE fires | status | first mismatching trade |
|--|--|--|--|--|--|--|
| loss cut (state/policy line pct<=-0.50, pulled>=30, newMae) | YES (v1.4 policy line + panel ThL2) | K7 | 23 | 30 | both fire | live ThL2Cut (-640$) / engine StopJoin (-1136$) at live entry 2026-11-02 07:54:00 | engine StateCut / live Stop (-1660$) at live entry 2026-11-03 01:48:01 |
| loss cut (state/policy line pct<=-0.50, pulled>=30, newMae) | YES (v1.4 policy line + panel ThL2) | P7 | 20 | 24 | both fire | live ThL2Cut (-2495$) / engine Target (+4795$) at live entry 2026-11-02 20:42:01 | engine StateCut / live Target (+8390$) at live entry 2026-11-04 19:27:00 |
| loss cut (state/policy line pct<=-0.50, pulled>=30, newMae) | YES (v1.4 policy line + panel ThL2) | U7 | 1 | 3 | both fire | live ThL2Cut (-3890$) / engine StopJoinFallback (-4950$) at live entry 2026-11-02 02:40:00 | - |
| loss cut (state/policy line pct<=-0.50, pulled>=30, newMae) | YES (v1.4 policy line + panel ThL2) | H7 | 2 | 2 | both fire | - | - |
| loss cut (state/policy line pct<=-0.50, pulled>=30, newMae) | YES (v1.4 policy line + panel ThL2) | M7 | 17 | 13 | both fire | live ThL2Cut (-650$) / engine StopJoin (-1236$) at live entry 2026-11-04 11:52:00 | engine StateCut / live Stop (-1615$) at live entry 2026-11-03 02:04:00 |
| loss cut (state/policy line pct<=-0.50, pulled>=30, newMae) | YES (v1.4 policy line + panel ThL2) | A7 | 7 | 14 | both fire | live PolicyCut (-655$) / engine Target (+1199$) at live entry 2026-11-03 20:32:00 | - |
| loss cut (state/policy line pct<=-0.50, pulled>=30, newMae) | YES (v1.4 policy line + panel ThL2) | O7 | 1 | 2 | both fire | live PolicyCut (-695$) / engine Target (+1799$) at live entry 2026-11-05 09:42:00 | - |
| loss cut (state/policy line pct<=-0.50, pulled>=30, newMae) | YES (v1.4 policy line + panel ThL2) | X3 | 0 | 2 | live-only (engine does not model) | - |
| loss cut (state/policy line pct<=-0.50, pulled>=30, newMae) | YES (v1.4 policy line + panel ThL2) | X4 | 0 | 1 | live-only (engine does not model) | - |
| loss cut (state/policy line pct<=-0.50, pulled>=30, newMae) | YES (v1.4 policy line + panel ThL2) | X5 | 0 | 1 | live-only (engine does not model) | - |
| profit take lines (PolicyTake: K7 tighten / P7 / H7 / U7 / * take) | YES (08:05-08:15 Mon lines) | M7 | 0 (engine models none) | 1 | live-only (engine does not model) | - |
| profit take lines (PolicyTake: K7 tighten / P7 / H7 / U7 / * take) | YES (08:05-08:15 Mon lines) | X5 | 0 (engine models none) | 1 | live-only (engine does not model) | - |
| tighten / trail (ThL2Trail) | YES (old panel) | K7 | 0 (engine models none) | 1 | live-only (engine does not model) | - |
| tighten / trail (ThL2Trail) | YES (old panel) | A7 | 0 (engine models none) | 1 | live-only (engine does not model) | - |
| BookLock (day cap +5R/-2R, give-back arm +2R keep 50%, week floor -12R) | YES | K7 | 1 | 1 | both fire | - |
| BookLock (day cap +5R/-2R, give-back arm +2R keep 50%, week floor -12R) | YES | P7 | 1 | 1 | both fire | - |
| BookLock (day cap +5R/-2R, give-back arm +2R keep 50%, week floor -12R) | YES | A7 | 2 | 1 | both fire | - |
| StackCut (Asia same-side stack cut 50%) | unknown: live exit name not in file | A7 | 1 | 0 | - | - |
| stop exits (Stop / StopJoin / StopJoinFallback) | YES | K7 | 8 | 1 | both fire | live Stop (-1660$) / engine StateCut (-602$) at live entry 2026-11-03 01:48:01 |
| stop exits (Stop / StopJoin / StopJoinFallback) | YES | U7 | 1 | 0 | - | - |
| stop exits (Stop / StopJoin / StopJoinFallback) | YES | M7 | 1 | 1 | both fire | live Stop (-1615$) / engine StateCut (-690$) at live entry 2026-11-03 02:04:00 |

For the loss cut the "first mismatching trade" cell shows two sides separated by `|`: first trade live cut but engine did not | first trade engine cut but live did not. The live cut that has no engine twin on the same trade is expected where the live book was the polluted ES/RTY-level book (user finding 11-09 14:00Z).


### 3b. Paired trades: loss-cut agreement (same trade, live vs engine)

| book | paired | both cut | LIVE cut, engine no cut | ENGINE cut, live no cut | neither cut | live cut rate | engine cut rate |
|--|--|--|--|--|--|--|--|
| K7 | 54 | 16 | 7 | 2 | 29 | 43% | 33% |
| P7 | 32 | 13 | 3 | 1 | 15 | 50% | 44% |
| U7 | 5 | 1 | 2 | 0 | 2 | 60% | 20% |
| H7 | 3 | 2 | 0 | 0 | 1 | 67% | 67% |
| M7 | 21 | 9 | 1 | 2 | 9 | 48% | 52% |
| A7 | 15 | 6 | 3 | 0 | 6 | 60% | 40% |
| O7 | 3 | 1 | 1 | 0 | 1 | 67% | 33% |

## 4. Entry-side and v1.9 layers: engine fires (trade-set differences in the live window) vs live

Live panel = LPB base (7/4/4 table, P7 cut 40/5x/w5/p3, day caps), so none of LOT / SIGQ / REG / STACK-London-cap (JN04RM rule layers), E1, C22, BR3S, F3, FLAT45K, blackout variants are installed live (v1.9 pending): the LIVE column is 0 by construction and is **not** a capital alarm. The engine fire counts below say how often each v1.9 layer would have acted in the live window (JN05W2 vs its leave-one-out, same window).

| layer | engine trades without the layer but not with (layer removes/changes) | trades only with the layer (layer creates by freeing slots) | engine exits changed to EarlyCut/cut | LIVE | status |
|--|--|--|--|--|--|
| F3 context cut | 25 | 18 | -7 | 0 | not installed live (v1.9 pending) |
| E1 new-evidence rule | 18 | 5 | 0 | 0 | not installed live (v1.9 pending) |
| C22 day count and P&L | 12 | 0 | 2 | 0 | not installed live (v1.9 pending) |
| BR3S breadth skip | 6 | 19 | -8 | 0 | not installed live (v1.9 pending) |
| FLAT45K K7 flat | 11 | 2 | 6 | 0 | not installed live (v1.9 pending) |
| LOT / SIGQ / REG / STACK (JN04RM rule layers) | engine sets FW2_JN05W2 omits JN04 layers by construction; not measured here | | | 0 | not installed (research layers) |
| entry-side live panel (session tables, day caps, blackout, U7 30-min post-cut blackout) | see section 2 live-only / engine-only entries | | | n/a | installed; mismatches are in section 2 |

## 5. 11-11 / 11-12 (facts supplied by the user and replayed by W-R; NO live log on the box)

| date (UTC) | book | rule | engine | live | source | status |
|--|--|--|--|--|--|--|
| 2026-11-12 00:11-02:45Z (11-11 ET evening) | P7 | state cut (pct<=-0.667 pulled_mult>=5 win=5 persist=3), 3 full stops at 6 lots | 3 cuts: 00:16:37Z -46.4 pts, 01:27:29Z -43.1, 02:43:24Z -43.2 (W-R replay; v1.4-literal replica also fires, 3 of 3) | 0 cuts: 3 StopJoin full stops -60.3/-57.2/-55.8 pts | user 18:05Z order + autopilot/DS3_P7_CUT_FIDELITY.md (W-R) | ENGINE FIRES, LIVE NEVER |
| 2026-11-12 11:30:45Z and 12:21:31Z | M7 | state/policy loss cut | unknown: NQ mbp-10 for 11-12 08:00-14:00Z not yet licensed (retry loop) and 11-12 state day not built | 2 cuts fired (-40 pts, -53.6 pts) | user 19:15Z order | live cut fired; engine comparison pending data |
| 2026-11-11 ET | K7, U7, H7, A7 | loss cut | engine fires in section 6 (no live log) | unknown (no live log) | - | UNKNOWN |

K7, U7, H7, A7 loss lines for 11-11/12: no live log and no replay yet -> UNKNOWN (task 4 of the 19:15Z order: per-book v1.4 policy table is in DS3_LIVE_CUT_BUG.md; check against v1.9a when the source arrives).

## 6. Engine fires on days with no live comparison (state days 11-06..11, same sets)

| book | StateCut | Target | StopJoin/Stop | BookLock | StackCut |
|--|--|--|--|--|--|
| K7 | 35 | 24 | 5 | 2 | 0 |
| P7 | 16 | 8 | 0 | 1 | 0 |
| U7 | 6 | 0 | 2 | 0 | 0 |
| H7 | 4 | 2 | 1 | 0 | 0 |
| M7 | 23 | 15 | 0 | 0 | 0 |
| A7 | 7 | 8 | 1 | 0 | 2 |
| O7 | 1 | 2 | 0 | 0 | 0 |

(Engine only; the live side for these days is not on the box.)

## 7. CAPITAL ALARMS (engine fires > 0, live fires = 0, installed rule)

- **P7 STATE LOSS CUT: ENGINE FIRES 3 OF 3, LIVE FIRED 0 ON THE NIGHT OF 11-11 ET (LIVE SHORT 19:11, SHORT 19:58, LONG 21:31 ET; ENTRY 28188.42 / 28211.04 / 28337.50; THREE FULL STOPS AT 6 LOTS; FIRST MISMATCH = SHORT 19:11 ET). LIVE CUT GATE NOT FOUND (v1.9a source not on box)**
