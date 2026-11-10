# DS3_TRAIL_L2 - profit-state engine on the live panel base: per-book profit lines, 2026-11-10 20:41Z (screen + exact so far)

STATUS: Shadow only, post-hoc, no PASS claims, PRE-PROOF. Prereg autopilot/TRAIL_L2_PREREG.md (sha in DECISIONS.md); engine autopilot/PTR_ENGINE_API.md (code/th_ptr). Base = LPB_BASE exact trade list (live panel: P7 day cap 8,400 loss, P7 7/4/4, P7 cut 40/5x/w5/p3), ROLL-fixed engine; the "v2.5 near-target retargets" are not a separate switch in the engine on the box (no spec found) and are NOT in these runs. **Rows are FIRST-ORDER SCREENS (cached 1-s feature paths, slip 1.2 central) unless marked EXACT**; first-order vs exact: about 26-28% of the fires of a line differ between them (SZ-IJK PTR_T1 check: re-entries and path divergence), so first-order winners are screens, exact decides. Equal lots; stack maxDD (all weeks) cuts vs the live panel base, mean change with the carrying week dropped; recents first (L6M / L3M / L1M), rule 2a (floor = 25% of the live PRE mean) via Z.prior_info; market-exit slip cases central 1.2 / low 0.57 / high 1.6 pts (REDO-R9, vs the fill-second mid; decision at the close of second s and exit at row s+1 is the second-delay frame, no extra delay added) and the engine 0.80 for exact continuity.

## 0. Summary: best line per book

| book | best line (basis) | four-window cut (FO: L6M/HOLD/PRE/X') | EXACT cut L6M/L3M/L1M/HOLD/PRE/X', d mean L6M | live week: Targets clipped / cost, give-backs caught / saved | plain sentence |
|---|---|---|---|---|---|
| K7 | `profit K7 * pct>=0.5 pulled_against_mult>=3 tighten 30 win=5 persist=3` (EXACT L6M (7 of the top-20 exact so far)) (HOLD exact pending) | 32/3/-2/16 | 30/30/22/-/-/-, 853 (stack scope) | 11/31 clipped (-11221$), 12/13 give-backs caught (13384$), net 1904$ | K7: the book-based protection is `profit K7 * pct>=0.5 pulled_against_mult>=3 tighten 30 win=5 persist=3`; it keeps 92% of the give-backs (12 of 13 caught) and costs 35% of the fills (11 of 31 live Targets clipped) (HOLD exact pending). |
| P7 | `profit P7 * pct>=0.3 pulled_against_mult>=30 tighten 5 win=15 persist=5` (EXACT L6M (10 of the top-20 exact so far)) (HOLD exact pending) | 65/24/22/16 | 33/33/22/-/-/-, -3133 (stack scope) | 27/28 clipped (-108419$), 6/7 give-backs caught (38416$), net -55616$ | P7: the book-based protection is `profit P7 * pct>=0.3 pulled_against_mult>=30 tighten 5 win=15 persist=5`; it keeps 86% of the give-backs (6 of 7 caught) and costs 96% of the fills (27 of 28 live Targets clipped) (HOLD exact pending). |
| M7 | `profit M7 * pct>=0.2 pulled_mult>=3 take win=5 persist=3 wall_ticks=8` (EXACT L6M (6 of the top-20 exact so far)) | 32/13/-2/-24 | 26/26/3/10/-/-, -781 (stack scope) | 13/13 clipped (-15026$), 4/4 give-backs caught (6159$), net -3055$ | M7: the book-based protection is `profit M7 * pct>=0.2 pulled_mult>=3 take win=5 persist=3 wall_ticks=8`; it keeps 100% of the give-backs (4 of 4 caught) and costs 100% of the fills (13 of 13 live Targets clipped). |
| U7 | `profit U7 * pct>=0.5 pulled_mult>=3 secs_fav<=2 take win=15 persist=10 wall_ticks=8` (EXACT L6M (9 of the top-20 exact so far)) (HOLD exact pending) | 29/-4/10/3 | 33/33/6/-/-/-, 845 (stack scope) | 2/3 clipped (-937$), 0/0 give-backs caught (0$), net -937$ | U7: the book-based protection is `profit U7 * pct>=0.5 pulled_mult>=3 secs_fav<=2 take win=15 persist=10 wall_ticks=8`; it keeps 0% of the give-backs (0 of 0 caught) and costs 67% of the fills (2 of 3 live Targets clipped) (HOLD exact pending). |
| H7 | `profit H7 * pct>=0.2 ice_against>=3 or pulled_mult>=30 take win=5 persist=3` (EXACT L6M (6 of the top-20 exact so far)) (HOLD exact pending) | 7/-3/2/11 | 7/7/4/-/-/-, 319 (stack scope) | 1/1 clipped (-652$), 0/2 give-backs caught (0$), net -652$ | H7: the book-based protection is `profit H7 * pct>=0.2 ice_against>=3 or pulled_mult>=30 take win=5 persist=3`; it keeps 0% of the give-backs (0 of 2 caught) and costs 100% of the fills (1 of 1 live Targets clipped) (HOLD exact pending). |
| A7 | `profit A7 * pct>=0.2 pulled_against_mult>=30 take win=10 persist=5 wall_ticks=8` (EXACT L6M (11 of the top-20 exact so far)) (HOLD exact pending) | 10/2/-2/-2 | 15/15/18/-/-/-, 961 (stack scope) | 7/7 clipped (-5046$), 3/4 give-backs caught (3075$), net 1099$ | A7: the book-based protection is `profit A7 * pct>=0.2 pulled_against_mult>=30 take win=10 persist=5 wall_ticks=8`; it keeps 75% of the give-backs (3 of 4 caught) and costs 100% of the fills (7 of 7 live Targets clipped) (HOLD exact pending). |
| O7 | `profit O7 * pct>=0.3 delta_mult>=2 take win=10 persist=10 wall_ticks=8` (EXACT L6M (6 of the top-20 exact so far)) | 5/1/-1/3 | 5/5/2/1/-/-, 30 (stack scope) | 1/1 clipped (-176$), 1/1 give-backs caught (1048$), net 872$ | O7: the book-based protection is `profit O7 * pct>=0.3 delta_mult>=2 take win=10 persist=10 wall_ticks=8`; it keeps 100% of the give-backs (1 of 1 caught) and costs 100% of the fills (1 of 1 live Targets clipped). |

## 0a. First profit-rule candidate: PTR_K7_01 `profit K7 * pct>=0.4 dd>=3 lock 0 persist=5` (exact rows complete so far)

Exact queue status (SZ-CORE, 19:15Z): priority sets ETA about 21:05Z (404 cell-months/h, 229 of 975 done at 19:15Z); the FINAL publishes the exact rows completed so far, flagged. Windows below are listed only when every month of the window has run.

| scope | window | months | maxDD cut vs LPB_BASE % | equal-mean cut % | d mean $/wk | maxDD cell / base | worst-20 cell / base |
|---|---|---|---|---|---|---|---|
| book K7 | HOLD | 26 | -85.7 | -91.3 | -1019 | 78085 / 42052 | -154825 / -131260 |
| book K7 | L1M | 26 | 100.0 | 100.0 | 5299 | 0 / 3940 | 23794 / 18535 |
| book K7 | L3M | 26 | 38.3 | 36.5 | 1099 | 11674 / 18932 | 64955 / 36865 |
| book K7 | L6M | 26 | 18.1 | 15.6 | -98 | 28261 / 34505 | 9485 / -20408 |
| stack ALL | HOLD | 26 | -10.1 | -3.1 | -1000 | 86796 / 78842 | -370416 / -377467 |
| stack ALL | L1M | 26 | 12.9 | 18.4 | 5109 | 44645 / 51253 | 6321 / 1363 |
| stack ALL | L3M | 26 | 36.9 | 40.9 | 1448 | 48719 / 77224 | 187302 / 155437 |
| stack ALL | L6M | 26 | 36.9 | 40.9 | 1212 | 48719 / 77224 | 116208 / 102384 |

Placebo (random exit at the same pct and count, B=200) and family null: see the K7 section; the K7 candidate line fires on about 37% of K7 trades with a break-even lock, so a random exit at the same pct is a strong comparator (own p is high); the exact mean gain is the point, the drawdown cut is shared with random locks.


## 0c. What LPB_BASE runs on the profit side (from the engine config, state_base_b._prm: PERIODS=False) and the reference rows

- **(a) State-armed tighten / take lines: NONE ON, for any book.** The engine profit branch (th_profit_on) needs PERIODS and a date before 2026-11-02 08:50 ET, so it is off in every S1b / LPB month; the policy-file profit lines exist only for the blind-week dates and never touch the 43 historic months; the old per-print loss line is neutralised (arm 1e9) and replaced by the state loss cut.
- **(b) Near-target retarget: the engine has no v2.5 / near-target switch** (no such code in replica/sim.py); the only retarget in it is the NTZ layer (zone lines, action Half), which is a lot / entry layer, not a profit rule. The live v2.5 retargets are therefore NOT in LPB_BASE nor in these runs.
- **(c) Native bracket only:** 60-pt limit target (O7 90) with touch fill, the per-book BookLock give-back lock (arm 2R, keep 50%, week floor), StackCut, TimeBlock flatten, the P7 day cap 8,400 loss. Reference rows: **no profit rule = LPB_BASE** (cut 0 by definition) and the old gated take lines of the blind week re-expressed in the grammar (first-order, slip 1.2; R13 REF_LINES, win=5 persist=1):

| line (old gated take, Mon 08:05-08:15) | fires | cut L6M/L3M/L1M | cut HOLD/PRE/X' | d mean L6M / PRE |
|---|---|---|---|---|
| `profit K7 * pct>=0.7 tot_rel>=1.2 tighten 30 win=5 persist=1` | 1230 | 11/11/-3 | -5/11/7 | -21 / -442 |
| `profit P7 * pct>=0.5 ahead_rel>=1.5 take win=5 persist=1` | 2722 | 11/11/-14 | 12/24/36 | -2969 / -616 |
| `profit H7 * pct>=0.3 ahead_rel>=1.5 take win=5 persist=1` | 771 | 4/4/-9 | 4/-16/9 | -897 / -1035 |
| `profit U7 * pct>=0.17 tot_rel>=1.5 take win=5 persist=1` | 1022 | 9/9/19 | -10/6/-2 | -1951 / -1835 |
| `profit K7 * pct>=0.7 ahead_rel>=1.2 take win=5 persist=1` | 3471 | 1/1/12 | 3/-4/7 | -736 / -1530 |
| `profit M7 * pct>=0.7 ahead_rel>=1.2 take win=5 persist=1` | 1990 | -1/-1/14 | 1/-11/-12 | -416 / -922 |
| `profit P7 * pct>=0.7 ahead_rel>=1.2 take win=5 persist=1` | 2423 | 34/34/0 | 9/14/26 | -1599 / 228 |


## 0b. Policy lines (D7 grammar) and what v1.5 lacks (for v1.7)

| book | line | fields v1.5 lacks |
|---|---|---|
| K7 | `profit K7 * pct>=0.5 pulled_against_mult>=3 tighten 30 win=5 persist=3` | persist=<s> (consecutive seconds); pulled_against_mult (OTHER side cancelled / MedLevel); tighten latched trail semantics (ratchet in favour only) - check v1.5 tighten; win=<s> (feature window) |
| P7 | `profit P7 * pct>=0.3 pulled_against_mult>=30 tighten 5 win=15 persist=5` | persist=<s> (consecutive seconds); pulled_against_mult (OTHER side cancelled / MedLevel); tighten latched trail semantics (ratchet in favour only) - check v1.5 tighten; win=<s> (feature window) |
| M7 | `profit M7 * pct>=0.2 pulled_mult>=3 take win=5 persist=3 wall_ticks=8` | persist=<s> (consecutive seconds); win=<s> (feature window) |
| U7 | `profit U7 * pct>=0.5 pulled_mult>=3 secs_fav<=2 take win=15 persist=10 wall_ticks=8` | persist=<s> (consecutive seconds); secs_fav (seconds since the FAVOURABLE extreme; v1.5 has secs_ext = adverse); win=<s> (feature window) |
| H7 | `profit H7 * pct>=0.2 ice_against>=3 or pulled_mult>=30 take win=5 persist=3` | OR between two conditions; persist=<s> (consecutive seconds); win=<s> (feature window) |
| A7 | `profit A7 * pct>=0.2 pulled_against_mult>=30 take win=10 persist=5 wall_ticks=8` | persist=<s> (consecutive seconds); pulled_against_mult (OTHER side cancelled / MedLevel); win=<s> (feature window) |
| O7 | `profit O7 * pct>=0.3 delta_mult>=2 take win=10 persist=10 wall_ticks=8` | delta_mult (aggressor delta against / MedLevel over win); persist=<s> (consecutive seconds); win=<s> (feature window) |

v1.7 profit state engine (grammar of the order): one evaluation per exchange second on the 1-s top-10 state, decision at the close of second s, market exit at the next print; features pct, secs_fav, pulled_mult, pulled_against_mult, wall_ahead_mult (wall_ticks), ice_against, imb5/imb10, delta_mult, tot_rel, ahead_rel, sweep_against, dd; actions take / tighten X (ratchet in favour only) / lock X / step X / scale F; modifiers win=, persist=; AND / OR between two conditions.

## K7 (5627 trades with a path; no-rule = LPB_BASE reference row: cut 0 by definition)

First-order top-20 by the recents key (mean equal-mean cut on L6M/L3M/L1M), at most 4 per family and a cap per action; exact columns are the stack maxDD cut vs LPB_BASE (engine slip 0.80) where the PTR_ set has run:

| # | line | fires | FO cut L6M/L3M/L1M | FO cut HOLD/PRE/X' | FO d mean L6M / PRE | placebo p / family p / WF2w % | EXACT cut L6M/L3M/L1M/HOLD/PRE/X' | EXACT d mean L6M | rule 2a (FO) |
|---|---|---|---|---|---|---|---|---|---|
| K7_01 | `profit K7 * pct>=0.4 dd>=3 lock 0 persist=5` | 2060 | 32/32/14 | -2/-7/15 | 1266 / -1147 | 0.74 / 1.00 / 29 | 37/37/13/-10/-/- | 1212 | OK-PRIOR |
| K7_02 | `profit K7 * pct>=0.3 delta_mult>=5 lock 0 win=10 persist=10` | 2115 | 33/33/10 | 5/-2/10 | 1542 / -1045 | 0.41 / 1.00 / 46 | 32/32/-2/-5/-/- | -435 | OK-PRIOR |
| K7_03 | `profit K7 * pct>=0.4 dd>=5 lock 0 persist=5` | 1865 | 34/34/9 | 2/-2/10 | 1213 / -741 | 0.64 / 1.00 / 41 | 35/35/13/-/-/- | 208 | OK-PRIOR |
| K7_04 | `profit K7 * pct>=0.5 sweep_against>=2 lock 0 win=15 persist=3` | 1847 | 33/33/9 | 0/-6/10 | 1114 / -787 | 0.63 / 1.00 / 33 | 31/31/13/-/-/- | 69 | OK-PRIOR |
| K7_05 | `profit K7 * pct>=0.5 pulled_against_mult>=3 tighten 30 win=5 persist=3` | 2397 | 32/32/13 | 3/-2/16 | 812 / -1141 | 0.41 / 1.00 / 33 | 30/30/22/-/-/- | 853 | OK-PRIOR |
| K7_06 | `profit K7 * pct>=0.5 tot_rel_slow>=1.2 tighten 30 persist=1` | 2167 | 35/35/13 | 3/-9/9 | 226 / -1215 | 0.80 / 1.00 / 32 | -/-/21/-/-/- | - | OK-PRIOR |
| K7_07 | `profit K7 * pct>=0.4 delta_mult>=10 tighten 30 win=15 persist=10` | 1756 | 28/28/12 | -3/1/7 | 1546 / -857 | 0.40 / 1.00 / 32 | -/-/15/-/-/- | - | OK-PRIOR |
| K7_08 | `profit K7 * pct>=0.6 pulled_against_mult>=10 tighten 30 win=3 persist=2` | 1537 | 29/29/13 | -1/13/6 | 1121 / -477 | 0.03 / 0.56 / 34 | -/-/16/-/-/- | - | OK-PRIOR |
| K7_09 | `profit K7 * pct>=0.3 delta_mult>=5 tighten 30 win=10 persist=10` | 2605 | 30/30/11 | 7/0/15 | 1172 / -1282 | 0.35 / 1.00 / 61 | -/-/18/-/-/- | - | OK-PRIOR |
| K7_10 | `profit K7 * pct>=0.5 tot_rel_slow>=1.2 step 20 persist=1` | 2163 | 39/39/8 | 3/-11/12 | -190 / -1278 | 0.85 / 1.00 / 35 | -/-/11/-/-/- | - | OK-PRIOR |
| K7_S01 | `profit K7 * pct>=0.5 pulled_mult>=20 lock 0 win=15 persist=10` | 1387 | 32/32/8 | -2/6/-3 | 975 / -491 | - / - / - | -/-/-/-/-/- | - | nan |
| K7_S02 | `profit K7 * pct>=0.6 pulled_against_mult>=10 lock 5 win=3 persist=2` | 1141 | 27/27/10 | 1/6/3 | 1254 / -327 | - / - / - | -/-/-/-/-/- | - | nan |
| K7_11 | `profit K7 * pct>=0.4 dd>=3 step 20 persist=5` | 2584 | 35/35/13 | 1/-5/21 | -133 / -1530 | 0.66 / 1.00 / 39 | -/-/14/-/-/- | - | OK-PRIOR |
| K7_S03 | `profit K7 * pct>=0.5 pulled_mult>=20 lock 0 win=8 persist=3` | 1221 | 31/31/10 | -1/11/-6 | 801 / -381 | - / - / - | -/-/-/-/-/- | - | nan |
| K7_12 | `profit K7 * pct>=0.4 delta_mult>=5 step 20 win=15 persist=10` | 2201 | 36/36/5 | 2/4/22 | 270 / -1040 | 0.25 / 0.99 / 44 | -/-/11/-/-/- | - | OK-PRIOR |
| K7_S04 | `profit K7 * pct>=0.5 dd>=5 lock 0 persist=10` | 1236 | 29/29/9 | -0/7/-6 | 1174 / -389 | - / - / - | -/-/-/-/-/- | - | nan |
| K7_S05 | `profit K7 * pct>=0.5 pulled_mult>=30 lock 0 win=15 persist=2` | 1339 | 31/31/7 | -0/3/-6 | 758 / -392 | - / - / - | -/-/-/-/-/- | - | nan |
| K7_S06 | `profit K7 * pct>=0.5 pulled_mult>=10 lock 0 win=2 persist=2` | 1091 | 27/27/7 | -2/14/1 | 1550 / -386 | - / - / - | -/-/-/-/-/- | - | nan |
| K7_S07 | `profit K7 * pct>=0.5 pulled_mult>=20 lock 0 win=8 persist=2` | 1313 | 31/31/8 | -0/2/-7 | 600 / -483 | - / - / - | -/-/-/-/-/- | - | nan |
| K7_D01 | `profit K7 * pct>=0.5 delta_mult>=2 adapt 32 p=0.5 lo=0.5 hi=2 tag=f win=10 persist=10` | 2344 | 28/28/13 | 4/-0/8 | 755 / -1068 | - / - / - | -/-/-/-/-/- | - | nan |
| K7_D02 | `profit K7 * pct>=0.5 delta_mult>=2 adapt 32 p=0.5 lo=0.5 hi=2 tag=s win=10 persist=10` | 2343 | 28/28/13 | 4/-0/8 | 755 / -1068 | - / - / - | -/-/-/-/-/- | - | nan |
| K7_S08 | `profit K7 * pct>=0.6 pulled_against_mult>=10 lock 10 win=3 persist=2` | 1270 | 25/25/13 | -1/7/4 | 1049 / -416 | - / - / - | -/-/-/-/-/- | - | nan |
| K7_13 | `profit K7 * pct>=0.2 dd>=20 pulled_mult>=20 take win=10 persist=10` | 1668 | 31/31/9 | -1/5/-8 | 366 / -780 | 0.14 / 0.94 / 25 | -/-/18/-/-/- | - | OK-PRIOR |
| K7_D03 | `profit K7 * pct>=0.2 dd>=20 adapt 32 p=0.5 lo=0.5 hi=2 tag=s persist=10` | 2397 | 35/35/7 | 5/7/18 | -199 / -1028 | - / - / - | -/-/-/-/-/- | - | nan |
| K7_D04 | `profit K7 * pct>=0.2 dd>=20 adapt 32 p=0.5 lo=0.5 hi=2 tag=f persist=10` | 2397 | 35/35/6 | 5/7/18 | -208 / -1028 | - / - / - | -/-/-/-/-/- | - | nan |
| K7_14 | `profit K7 * pct>=0.3 dd>=16 or imb10<=-0.1 take persist=10` | 3757 | 27/27/11 | 7/-12/13 | 586 / -2491 | 0.85 / 1.00 / 42 | -/-/16/-/-/- | - | OK-PRIOR |
| K7_D05 | `profit K7 * pct>=0.4 delta_mult>=5 adapt 32 p=0.5 lo=0.5 hi=2 tag=s win=15 persist=10` | 2727 | 28/28/8 | 6/6/23 | 505 / -1155 | - / - / - | -/-/-/-/-/- | - | nan |
| K7_15 | `profit K7 * pct>=0.2 dd>=20 delta_mult>=2 take win=10 persist=10` | 2306 | 28/28/12 | 5/-1/16 | -100 / -925 | 0.35 / 1.00 / 30 | -/-/19/-/-/- | - | OK-PRIOR |
| K7_16 | `profit K7 * pct>=0.2 dd>=20 pulled_against_mult>=20 take win=5 persist=2` | 1458 | 28/28/6 | 6/6/0 | 157 / -1123 | 0.12 / 0.85 / 30 | -/-/23/-/-/- | - | OK-PRIOR |
| K7_17 | `profit K7 * pct>=0.2 dd>=20 sweep_against>=6 take win=8 persist=5` | 2566 | 30/30/6 | 4/9/12 | -456 / -1086 | 0.04 / 0.64 / 34 | -/-/1/-/-/- | - | OK-PRIOR |

Bi-weekly re-pick WF over the whole stage-1/2/3 cell set of K7 (first-order, slip 1.2): OOS maxDD cut 7.7%, OOS mean delta -2022 $/wk, pick beats live in 57% of 74 refits (the pick switches every refit: it prefers whichever cell removes the most exposure; read the mean delta).

Placebo (random exit at the same pct, same count) and family null over the profit set (SZ-IJK ptr_null): #1 own p 0.74 / family p 1.00; #2 own p 0.41 / family p 1.00; #3 own p 0.64 / family p 1.00; #4 own p 0.63 / family p 1.00; #5 own p 0.41 / family p 1.00

Family null over the WHOLE profit set of K7 (SZ-IJK, stage 1+2 cells with >= 20 fires, B=100, slip 1.2, bucketed placebo = approximation): 468 of 16170 cells have family p < .05 (2.9%; around 5% is what the null alone gives); cells with own p < .05: 618 (expected by chance 808); the best single lines reach the B=100 floor (p about 0.01), use for ranking only.

Selective lines (fire on <= 25% of the book trades, sets PTR_K7_S01..S08; first-order slip 1.2 / exact where complete):

| # | line | fires | FO cut L6M/L3M/L1M | FO cut HOLD/PRE/X' | FO d mean L6M / PRE | EXACT cut L6M/L3M/L1M |
|---|---|---|---|---|---|---|
| 1 | `profit K7 * pct>=0.5 pulled_mult>=20 lock 0 win=15 persist=10` | 1387 | 32/32/8 | -2/6/-3 | 975 / -491 | -/-/- |
| 2 | `profit K7 * pct>=0.6 pulled_against_mult>=10 lock 5 win=3 persist=2` | 1141 | 27/27/10 | 1/6/3 | 1254 / -327 | -/-/- |
| 3 | `profit K7 * pct>=0.5 pulled_mult>=20 lock 0 win=8 persist=3` | 1221 | 31/31/10 | -1/11/-6 | 801 / -381 | -/-/- |
| 4 | `profit K7 * pct>=0.5 dd>=5 lock 0 persist=10` | 1236 | 29/29/9 | -0/7/-6 | 1174 / -389 | -/-/- |
| 5 | `profit K7 * pct>=0.5 pulled_mult>=30 lock 0 win=15 persist=2` | 1339 | 31/31/7 | -0/3/-6 | 758 / -392 | -/-/- |
| 6 | `profit K7 * pct>=0.5 pulled_mult>=10 lock 0 win=2 persist=2` | 1091 | 27/27/7 | -2/14/1 | 1550 / -386 | -/-/- |
| 7 | `profit K7 * pct>=0.5 pulled_mult>=20 lock 0 win=8 persist=2` | 1313 | 31/31/8 | -0/2/-7 | 600 / -483 | -/-/- |
| 8 | `profit K7 * pct>=0.6 pulled_against_mult>=10 lock 10 win=3 persist=2` | 1270 | 25/25/13 | -1/7/4 | 1049 / -416 | -/-/- |

Best cell per action type (stage 2/3, first-order, by the recents key):

| action | feature / cell | fires | cut L6M/L3M/L1M | cut PRE | d mean L6M |
|---|---|---|---|---|---|
| take | dd+pulled_mult arm 0.2 thr 20.0 win 0 P 10 X 0 F 0.0 | 1668 | 31/31/9 | 5 | 366 |
| tighten | pulled_against_mult arm 0.5 thr 3.0 win 5 P 3 X 30 F 0.0 | 2397 | 32/32/13 | -2 | 812 |
| lock | dd arm 0.4 thr 3.0 win 0 P 5 X 0 F 0.0 | 2060 | 32/32/14 | -7 | 1266 |
| step | tot_rel_slow arm 0.5 thr 1.2 win 0 P 1 X 20 F 0.0 | 2163 | 39/39/8 | -11 | -190 |
| scale | dd arm 0.5 thr 5.0 win 0 P 2 X 0 F 0.75 | 3844 | 10/10/7 | 2 | 770 |
| adaptive tighten | delta_mult|adapt_s_g0.5 arm 0.5 thr 2.0 win 10 P 10 X 32 F 0.5 | 2343 | 28/28/13 | -0 | 755 |

Loss-cut mirror (pulled_mult at a new favourable extreme, secs_fav<=0): best arm 0.3 x pulled_mult>=10.0 win 5 persist 1: fires 2507, cut L6M/L3M/L1M 28/28/-2, PRE 0, d mean L6M -38.

Slip sensitivity of the best line `profit K7 * pct>=0.5 pulled_against_mult>=3 tighten 30 win=5 persist=3` (first-order, stack cut % / d mean $/wk):

| slip pts | cut L6M | cut L3M | cut L1M | cut HOLD | cut PRE | cut X' | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|---|---|
| 0.57 | 33 | 33 | 13 | 4 | -1 | 17 | 220 | -968 |
| 0.80 | 33 | 33 | 13 | 4 | -2 | 16 | 107 | -1031 |
| 1.20 | 32 | 32 | 13 | 3 | -2 | 16 | 812 | -1141 |
| 1.60 | 31 | 31 | 12 | 3 | -3 | 15 | 618 | -1251 |

By window (best line, slip 1.2, first-order): L1M cut 13 / d mean 3888; L3M cut 32 / d mean 1323; L6M cut 32 / d mean 812; HOLD cut 3 / d mean -969; PRE cut -2 / d mean -1141; X' cut 16 / d mean 27. The held-out live week (11-01..05) sits inside L1M, a trending week: P7 carried about $159k of Targets that week, so any rule that exits winners early pays for itself only in the choppy weeks of the history; the single-week replay (REDO-R13: autopilot/R13_TRAIL_LIVE_REPLAY_BOOKS.md) and the 43-month first-order table are different regimes and are both shown, not averaged.

By entry session (the same line applied to one session only; stack effect): 

| session | trades | fires | cut L6M | cut PRE | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|
| asia | 1893 | 816 | 15 | -9 | 297 | -352 |
| london | 1378 | 614 | 6 | 1 | 274 | -384 |
| nyam | 1301 | 550 | 1 | 8 | 315 | -382 |
| nypm | 1055 | 417 | 10 | -2 | -519 | -308 |

## P7 (3937 trades with a path; no-rule = LPB_BASE reference row: cut 0 by definition)

First-order top-20 by the recents key (mean equal-mean cut on L6M/L3M/L1M), at most 4 per family and a cap per action; exact columns are the stack maxDD cut vs LPB_BASE (engine slip 0.80) where the PTR_ set has run:

| # | line | fires | FO cut L6M/L3M/L1M | FO cut HOLD/PRE/X' | FO d mean L6M / PRE | placebo p / family p / WF2w % | EXACT cut L6M/L3M/L1M/HOLD/PRE/X' | EXACT d mean L6M | rule 2a (FO) |
|---|---|---|---|---|---|---|---|---|---|
| P7_PC01 | `profit P7 * pct>=0.2 pulled_mult>=30 secs_fav<=5 take win=15 persist=2 wall_ticks=8` | 2031 | 66/71/60 | 1/41/15 | 1271 / -392 | - / - / - | 12/12/32/-30/-/- | -3927 | nan |
| P7_PC02 | `profit P7 * pct>=0.2 pulled_mult>=30 secs_fav<=5 take win=15 persist=3 wall_ticks=8` | 1785 | 67/67/50 | 10/48/12 | 1574 / 42 | - / - / - | -0/-0/35/-27/-/- | -2757 | nan |
| P7_PC03 | `profit P7 * pct>=0.2 pulled_mult>=20 secs_fav<=5 take win=8 persist=2 wall_ticks=8` | 1979 | 65/65/48 | -15/18/16 | 1762 / 353 | - / - / - | 3/3/45/-/-/- | -6615 | nan |
| P7_PC04 | `profit P7 * pct>=0.2 pulled_mult>=30 secs_fav<=2 take win=15 persist=1 wall_ticks=8` | 1937 | 63/63/47 | 21/37/14 | 2048 / 753 | - / - / - | 17/17/43/-/-/- | -3588 | nan |
| P7_01 | `profit P7 * pct>=0.2 pulled_mult>=50 tot_rel_slow>=1.2 take win=15 persist=1` | 994 | 62/62/66 | 15/-24/1 | -374 / -854 | 0.95 / 1.00 / 16 | 24/24/62/-17/-/- | -1376 | RECENT-ONLY |
| P7_02 | `profit P7 * pct>=0.3 pulled_against_mult>=5 tighten 5 win=5 persist=10` | 3217 | 65/65/61 | -6/22/25 | -1172 / -1172 | 0.01 / 0.04 / 58 | 17/17/18/-17/-/- | -6486 | OK-PRIOR |
| P7_PC06 | `profit P7 * pct>=0.2 pulled_mult>=20 secs_fav<=5 take win=8 persist=3 wall_ticks=8` | 1582 | 60/60/51 | -11/12/20 | 1562 / 1001 | - / - / - | -/-/-/-/-/- | - | nan |
| P7_03 | `profit P7 * pct>=0.3 pulled_against_mult>=5 step 5 win=5 persist=10` | 3170 | 62/71/62 | -1/19/29 | -1932 / -1189 | 0.01 / 0.19 / 58 | 10/25/17/-/-/- | -6748 | OK-PRIOR |
| P7_04 | `profit P7 * pct>=0.3 pulled_against_mult>=20 tighten 5 win=8 persist=3` | 2949 | 67/67/54 | 20/15/22 | -1160 / -1011 | 0.04 / 0.63 / 62 | 19/19/15/-/-/- | -6667 | OK-PRIOR |
| P7_PC05 | `profit P7 * pct>=0.3 pulled_mult>=10 secs_fav<=2 take win=5 persist=2 wall_ticks=8` | 2202 | 58/58/66 | 23/15/-1 | -353 / 500 | - / - / - | -4/-4/25/-/-/- | -6676 | nan |
| P7_05 | `profit P7 * pct>=0.3 pulled_against_mult>=30 tighten 5 win=15 persist=5` | 2848 | 65/65/55 | 24/22/16 | -741 / -980 | 0.02 / 0.23 / 70 | 33/33/22/-/-/- | -3133 | OK-PRIOR |
| P7_06 | `profit P7 * pct>=0.2 pulled_mult>=50 tighten 8 win=15 persist=2` | 1610 | 64/64/50 | -10/-14/-0 | -331 / -202 | 0.86 / 1.00 / 44 | -/-/-/-/-/- | - | OK-PRIOR |
| P7_07 | `profit P7 * pct>=0.2 sweep_against>=3 tighten 5 win=3 persist=10` | 2778 | 59/59/50 | 12/12/45 | 989 / -1432 | 0.46 / 1.00 / 58 | -/-/-/-/-/- | - | OK-PRIOR |
| P7_PC07 | `profit P7 * pct>=0.2 pulled_mult>=20 secs_fav<=5 take win=8 persist=1 wall_ticks=8` | 2383 | 62/62/42 | -10/12/21 | 1261 / -431 | - / - / - | -/-/-/-/-/- | - | nan |
| P7_D01 | `profit P7 * pct>=0.3 pulled_against_mult>=5 adapt 8 p=0.5 lo=0.5 hi=2 tag=f win=5 persist=10` | 3200 | 63/63/60 | -5/28/26 | -1520 / -1107 | - / - / - | -/-/-/-/-/- | - | nan |
| P7_D02 | `profit P7 * pct>=0.3 pulled_against_mult>=5 adapt 8 p=0.5 lo=0.5 hi=2 tag=s win=5 persist=10` | 3200 | 63/63/60 | -5/28/26 | -1520 / -1109 | - / - / - | -/-/-/-/-/- | - | nan |
| P7_08 | `profit P7 * pct>=0.3 pulled_mult>=5 secs_fav<=0 take win=3 persist=1` | 2411 | 55/55/59 | 3/-8/42 | 722 / 773 | 0.62 / 1.00 / 39 | -/-/-/-/-/- | - | OK-PRIOR |
| P7_09 | `profit P7 * pct>=0.2 pulled_mult>=50 dd>=8 take win=15 persist=1` | 1617 | 60/60/64 | -4/-9/-5 | -1691 / -777 | 0.81 / 1.00 / 39 | -/-/-/-/-/- | - | OK-PRIOR |
| P7_10 | `profit P7 * pct>=0.2 pulled_mult>=50 step 5 win=15 persist=2` | 1618 | 62/62/54 | -12/-14/-2 | -505 / -330 | 0.85 / 1.00 / 44 | -/-/-/-/-/- | - | OK-PRIOR |
| P7_D04 | `profit P7 * pct>=0.2 sweep_against>=3 adapt 8 p=1 lo=0.25 hi=4 tag=f win=3 persist=10` | 2778 | 59/59/50 | 11/14/45 | 860 / -1422 | - / - / - | -/-/-/-/-/- | - | nan |
| P7_D03 | `profit P7 * pct>=0.2 sweep_against>=3 adapt 8 p=1 lo=0.25 hi=4 tag=s win=3 persist=10` | 2778 | 59/59/50 | 11/14/45 | 860 / -1422 | - / - / - | -/-/-/-/-/- | - | nan |
| P7_11 | `profit P7 * pct>=0.2 pulled_mult>=20 step 5 win=3 persist=1` | 1959 | 56/56/71 | 8/7/15 | -1469 / -904 | 0.44 / 1.00 / 58 | -/-/-/-/-/- | - | OK-PRIOR |
| P7_12 | `profit P7 * pct>=0.2 pulled_mult>=20 sweep_against>=3 take win=3 persist=1` | 1943 | 55/55/69 | 7/4/18 | -909 / -855 | 0.58 / 1.00 / 59 | -/-/-/-/-/- | - | OK-PRIOR |
| P7_13 | `profit P7 * pct>=0.2 pulled_mult>=20 lock 10 win=5 persist=5` | 1051 | 61/61/43 | 7/3/14 | 1525 / -960 | 0.53 / 1.00 / 54 | -/-/-/-/-/- | - | OK-PRIOR |
| P7_D05 | `profit P7 * pct>=0.3 pulled_against_mult>=20 adapt 8 p=1 lo=0.25 hi=4 tag=f win=5 persist=1` | 2663 | 63/63/48 | 25/6/18 | -61 / -2108 | - / - / - | -/-/-/-/-/- | - | nan |
| P7_14 | `profit P7 * pct>=0.3 pulled_against_mult>=20 ice_against>=1 take win=8 persist=2` | 2407 | 57/57/50 | 39/-0/21 | 966 / -464 | 0.41 / 1.00 / 65 | -/-/-/-/-/- | - | OK-PRIOR |
| P7_PC17 | `profit P7 * pct>=0.2 pulled_mult>=20 secs_fav<=5 take win=5 persist=1 wall_ticks=8` | 1732 | 57/57/35 | -12/13/23 | 2756 / 271 | - / - / - | -/-/-/-/-/- | - | nan |
| P7_PC08 | `profit P7 * pct>=0.3 pulled_mult>=20 secs_fav<=5 take win=10 persist=3 wall_ticks=8` | 1911 | 62/62/42 | -0/25/9 | 343 / 132 | - / - / - | -/-/-/-/-/- | - | nan |
| P7_15 | `profit P7 * pct>=0.3 pulled_mult>=10 secs_fav<=0 take win=5 persist=1` | 1793 | 62/62/43 | 18/5/10 | 10 / 876 | 0.26 / 1.00 / 41 | -/-/-/-/-/- | - | OK-PRIOR |
| P7_PC10 | `profit P7 * pct>=0.3 pulled_mult>=10 secs_fav<=5 take win=5 persist=2 wall_ticks=8` | 3030 | 58/58/49 | 33/14/3 | -409 / -363 | - / - / - | -/-/-/-/-/- | - | nan |

Bi-weekly re-pick WF over the whole stage-1/2/3 cell set of P7 (first-order, slip 1.2): OOS maxDD cut 25.5%, OOS mean delta -4453 $/wk, pick beats live in 82% of 74 refits (the pick switches every refit: it prefers whichever cell removes the most exposure; read the mean delta).

Placebo (random exit at the same pct, same count) and family null over the profit set (SZ-IJK ptr_null): #1 own p 0.95 / family p 1.00; #2 own p 0.01 / family p 0.04; #3 own p 0.01 / family p 0.19; #4 own p 0.04 / family p 0.63; #5 own p 0.02 / family p 0.23

Family null over the WHOLE profit set of P7 (SZ-IJK, stage 1+2 cells with >= 20 fires, B=100, slip 1.2, bucketed placebo = approximation): 681 of 16140 cells have family p < .05 (4.2%; around 5% is what the null alone gives); cells with own p < .05: 986 (expected by chance 807); the best single lines reach the B=100 floor (p about 0.01), use for ranking only.

Selective lines (fire on <= 25% of the book trades, sets PTR_P7_S01..S08; first-order slip 1.2 / exact where complete):

| # | line | fires | FO cut L6M/L3M/L1M | FO cut HOLD/PRE/X' | FO d mean L6M / PRE | EXACT cut L6M/L3M/L1M |
|---|---|---|---|---|---|---|
| 1 | `profit P7 * pct>=0.3 pulled_against_mult>=50 tighten 40 win=15 persist=1` | 963 | 50/50/27 | -32/-19/-8 | 4261 / -418 | -/-/- |
| 2 | `profit P7 * pct>=0.2 pulled_mult>=30 lock 5 win=8 persist=5` | 879 | 48/48/41 | -22/-25/-3 | 2798 / -151 | -/-/- |
| 3 | `profit P7 * pct>=0.5 pulled_mult>=50 step 10 win=15 persist=1` | 879 | 53/53/44 | -1/7/8 | 1396 / 134 | -/-/- |
| 4 | `profit P7 * pct>=0.3 pulled_against_mult>=50 lock 0 win=15 persist=1` | 953 | 47/47/31 | -31/-18/-12 | 3586 / -499 | -/-/- |
| 5 | `profit P7 * pct>=0.5 pulled_mult>=50 tighten 12 win=15 persist=1` | 964 | 54/54/35 | 1/10/10 | 1221 / 81 | -/-/- |
| 6 | `profit P7 * pct>=0.5 pulled_mult>=50 tighten 20 win=15 persist=1` | 761 | 48/54/37 | 0/4/10 | 1355 / 268 | -/-/- |
| 7 | `profit P7 * pct>=0.2 pulled_mult>=30 lock 0 win=8 persist=5` | 800 | 42/42/37 | -18/-9/-4 | 3133 / 160 | -/-/- |
| 8 | `profit P7 * pct>=0.2 pulled_mult>=30 lock 2 win=8 persist=5` | 834 | 42/42/40 | -15/-22/-4 | 2900 / -186 | -/-/- |

Best cell per action type (stage 2/3, first-order, by the recents key):

| action | feature / cell | fires | cut L6M/L3M/L1M | cut PRE | d mean L6M |
|---|---|---|---|---|---|
| take | pulled_mult+tot_rel_slow arm 0.2 thr 50.0 win 15 P 1 X 0 F 0.0 | 994 | 62/62/66 | -24 | -374 |
| tighten | pulled_mult+delta_mult arm 0.2 thr 20.0 win 3 P 1 X 16 F 0.0 | 1475 | 55/55/74 | 12 | -26 |
| lock | pulled_mult arm 0.2 thr 20.0 win 5 P 5 X 10 F 0.0 | 1051 | 61/61/43 | 3 | 1525 |
| step | pulled_against_mult arm 0.3 thr 5.0 win 5 P 10 X 5 F 0.0 | 3170 | 62/71/62 | 19 | -1932 |
| scale | pulled_against_mult arm 0.2 thr 50.0 win 15 P 1 X 0 F 0.75 | 1955 | 52/52/28 | 20 | 2330 |
| adaptive tighten | pulled_against_mult|adapt_f_g0.5 arm 0.3 thr 5.0 win 5 P 10 X 8 F 0.5 | 3200 | 63/63/60 | 28 | -1520 |

Loss-cut mirror (pulled_mult at a new favourable extreme, secs_fav<=0): best arm 0.3 x pulled_mult>=5.0 win 3 persist 1: fires 2411, cut L6M/L3M/L1M 55/55/59, PRE -8, d mean L6M 722.

Slip sensitivity of the best line `profit P7 * pct>=0.3 pulled_against_mult>=30 tighten 5 win=15 persist=5` (first-order, stack cut % / d mean $/wk):

| slip pts | cut L6M | cut L3M | cut L1M | cut HOLD | cut PRE | cut X' | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|---|---|
| 0.57 | 69 | 69 | 57 | 27 | 24 | 19 | 447 | -402 |
| 0.80 | 67 | 67 | 56 | 26 | 23 | 18 | 13 | -613 |
| 1.20 | 65 | 65 | 55 | 24 | 22 | 16 | -741 | -980 |
| 1.60 | 62 | 62 | 53 | 20 | 20 | 15 | -1495 | -1347 |

By window (best line, slip 1.2, first-order): L1M cut 55 / d mean 5900; L3M cut 65 / d mean 5325; L6M cut 65 / d mean -741; HOLD cut 24 / d mean -3439; PRE cut 22 / d mean -980; X' cut 16 / d mean 516. The held-out live week (11-01..05) sits inside L1M, a trending week: P7 carried about $159k of Targets that week, so any rule that exits winners early pays for itself only in the choppy weeks of the history; the single-week replay (REDO-R13: autopilot/R13_TRAIL_LIVE_REPLAY_BOOKS.md) and the 43-month first-order table are different regimes and are both shown, not averaged.

By entry session (the same line applied to one session only; stack effect): 

| session | trades | fires | cut L6M | cut PRE | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|
| asia | 1768 | 1250 | 24 | 16 | -1923 | -683 |
| london | 1208 | 918 | 19 | 5 | 93 | -336 |
| nyam | 961 | 680 | 17 | -7 | 952 | -480 |

## M7 (3423 trades with a path; no-rule = LPB_BASE reference row: cut 0 by definition)

First-order top-20 by the recents key (mean equal-mean cut on L6M/L3M/L1M), at most 4 per family and a cap per action; exact columns are the stack maxDD cut vs LPB_BASE (engine slip 0.80) where the PTR_ set has run:

| # | line | fires | FO cut L6M/L3M/L1M | FO cut HOLD/PRE/X' | FO d mean L6M / PRE | placebo p / family p / WF2w % | EXACT cut L6M/L3M/L1M/HOLD/PRE/X' | EXACT d mean L6M | rule 2a (FO) |
|---|---|---|---|---|---|---|---|---|---|
| M7_PC01 | `profit M7 * pct>=0.2 pulled_mult>=3 secs_fav<=10 take win=5 persist=3 wall_ticks=8` | 3304 | 32/32/11 | 13/-4/-24 | -486 / -709 | - / - / - | -/-/-/-/-/- | - | nan |
| M7_03 | `profit M7 * pct>=0.2 pulled_mult>=3 tighten 5 win=5 persist=3 wall_ticks=8` | 3312 | 32/32/12 | 12/-5/-25 | -520 / -760 | 0.97 / 1.00 / 37 | 27/27/4/-/-/- | -1318 | OK-PRIOR |
| M7_02 | `profit M7 * pct>=0.2 pulled_mult>=3 take win=5 persist=3 wall_ticks=8` | 3320 | 32/32/11 | 13/-2/-24 | -521 / -694 | 0.71 / 1.00 / 39 | 26/26/3/10/-/- | -781 | OK-PRIOR |
| M7_01 | `profit M7 * pct>=0.2 sweep_against>=3 take win=8 persist=2 wall_ticks=8` | 3349 | 33/33/10 | 17/-2/-24 | -636 / -674 | 0.66 / 1.00 / 41 | 25/25/2/14/-/- | -1583 | OK-PRIOR |
| M7_PC02 | `profit M7 * pct>=0.2 pulled_mult>=3 secs_fav<=5 take win=5 persist=3 wall_ticks=8` | 3292 | 31/31/11 | 13/-3/-26 | -480 / -670 | - / - / - | -/-/-/-/-/- | - | nan |
| M7_PC05 | `profit M7 * pct>=0.2 pulled_mult>=10 secs_fav<=5 take win=5 persist=1 wall_ticks=8` | 3064 | 30/30/13 | 20/-4/-12 | -454 / -755 | - / - / - | -/-/-/-/-/- | - | nan |
| M7_04 | `profit M7 * pct>=0.2 sweep_against>=4 take win=8 persist=2 wall_ticks=8` | 3323 | 32/32/11 | 17/-1/-23 | -630 / -662 | 0.42 / 1.00 / 41 | 25/25/3/-/-/- | -799 | OK-PRIOR |
| M7_17 | `profit M7 * pct>=0.2 sweep_against>=3 tighten 5 win=8 persist=2 wall_ticks=8` | 3342 | 32/32/10 | 15/-4/-25 | -592 / -779 | 0.89 / 1.00 / 38 | -/-/-/-/-/- | - | OK-PRIOR |
| M7_05 | `profit M7 * pct>=0.2 pulled_against_mult>=10 take win=5 persist=2 wall_ticks=8` | 3304 | 32/32/10 | 17/-1/-19 | -627 / -630 | 0.42 / 1.00 / 35 | 27/27/3/-/-/- | -1420 | OK-PRIOR |
| M7_06 | `profit M7 * pct>=0.2 pulled_against_mult>=20 tighten 5 win=15 persist=2 wall_ticks=8` | 3307 | 31/31/10 | 14/-5/-23 | -656 / -793 | 0.96 / 1.00 / 34 | -/-/8/-/-/- | - | OK-PRIOR |
| M7_07 | `profit M7 * pct>=0.2 imb10<=-0.1 tighten 5 win=0 persist=1 wall_ticks=8` | 3347 | 30/30/12 | 16/-3/-25 | -603 / -818 | 0.79 / 1.00 / 43 | -/-/9/-/-/- | - | OK-PRIOR |
| M7_14 | `profit M7 * pct>=0.2 imb10<=-0.1 lock 10 win=0 persist=3 wall_ticks=8` | 2604 | 24/24/11 | 12/-2/-24 | 439 / -409 | 0.57 / 1.00 / 30 | -/-/-/-/-/- | - | OK-PRIOR |
| M7_PC10 | `profit M7 * pct>=0.2 pulled_mult>=10 secs_fav<=5 take win=8 persist=2 wall_ticks=8` | 3132 | 30/30/10 | 18/-1/-12 | -535 / -748 | - / - / - | -/-/-/-/-/- | - | nan |
| M7_19 | `profit M7 * pct>=0.2 pulled_mult>=3 step 5 win=5 persist=3 wall_ticks=8` | 3299 | 31/31/12 | 12/-2/-25 | -741 / -754 | 0.57 / 1.00 / 34 | -/-/-/-/-/- | - | OK-PRIOR |
| M7_PC09 | `profit M7 * pct>=0.2 pulled_mult>=3 secs_fav<=5 take win=3 persist=1 wall_ticks=8` | 3359 | 30/30/12 | 20/-3/-25 | -607 / -707 | - / - / - | -/-/-/-/-/- | - | nan |
| M7_PC07 | `profit M7 * pct>=0.2 pulled_mult>=3 secs_fav<=10 take win=3 persist=1 wall_ticks=8` | 3368 | 30/30/12 | 20/-3/-25 | -615 / -700 | - / - / - | -/-/-/-/-/- | - | nan |
| M7_PC04 | `profit M7 * pct>=0.2 pulled_mult>=5 secs_fav<=2 take win=5 persist=1 wall_ticks=8` | 3301 | 30/30/12 | 20/-6/-21 | -646 / -715 | - / - / - | -/-/-/-/-/- | - | nan |
| M7_PC03 | `profit M7 * pct>=0.2 pulled_mult>=3 secs_fav<=10 take win=5 persist=2 wall_ticks=8` | 3344 | 31/31/10 | 17/-1/-24 | -666 / -653 | - / - / - | -/-/-/-/-/- | - | nan |
| M7_PC16 | `profit M7 * pct>=0.2 pulled_mult>=3 secs_fav<=2 take win=2 persist=1 wall_ticks=8` | 3300 | 30/30/11 | 20/-5/-25 | -548 / -695 | - / - / - | -/-/-/-/-/- | - | nan |
| M7_PC06 | `profit M7 * pct>=0.2 pulled_mult>=3 secs_fav<=2 take win=3 persist=1 wall_ticks=8` | 3335 | 30/30/11 | 20/-4/-25 | -613 / -718 | - / - / - | -/-/-/-/-/- | - | nan |
| M7_PC12 | `profit M7 * pct>=0.2 pulled_mult>=5 secs_fav<=10 take win=8 persist=3 wall_ticks=8` | 3311 | 30/30/11 | 15/-4/-23 | -595 / -694 | - / - / - | -/-/-/-/-/- | - | nan |
| M7_PC08 | `profit M7 * pct>=0.2 pulled_mult>=10 secs_fav<=10 take win=15 persist=3 wall_ticks=8` | 3300 | 30/30/11 | 15/-4/-23 | -638 / -755 | - / - / - | -/-/-/-/-/- | - | nan |
| M7_PC11 | `profit M7 * pct>=0.2 pulled_mult>=5 secs_fav<=10 take win=10 persist=3 wall_ticks=8` | 3328 | 30/30/11 | 15/-2/-24 | -643 / -615 | - / - / - | -/-/-/-/-/- | - | nan |
| M7_PC13 | `profit M7 * pct>=0.2 pulled_mult>=10 secs_fav<=10 take win=8 persist=2 wall_ticks=8` | 3223 | 30/30/10 | 17/-3/-20 | -628 / -845 | - / - / - | -/-/-/-/-/- | - | nan |
| M7_PC14 | `profit M7 * pct>=0.2 pulled_mult>=3 secs_fav<=10 take win=15 persist=3 wall_ticks=8` | 3342 | 30/30/11 | 15/-2/-24 | -659 / -616 | - / - / - | -/-/-/-/-/- | - | nan |
| M7_PC15 | `profit M7 * pct>=0.2 pulled_mult>=5 secs_fav<=10 take win=15 persist=3 wall_ticks=8` | 3339 | 30/30/11 | 15/-2/-25 | -659 / -602 | - / - / - | -/-/-/-/-/- | - | nan |
| M7_PC17 | `profit M7 * pct>=0.2 pulled_mult>=3 secs_fav<=10 take win=10 persist=3 wall_ticks=8` | 3340 | 30/30/11 | 15/-2/-25 | -654 / -596 | - / - / - | -/-/-/-/-/- | - | nan |
| M7_PC19 | `profit M7 * pct>=0.2 pulled_mult>=3 secs_fav<=10 take win=8 persist=3 wall_ticks=8` | 3334 | 30/30/11 | 15/-2/-25 | -663 / -632 | - / - / - | -/-/-/-/-/- | - | nan |
| M7_08 | `profit M7 * pct>=0.2 imb5<=-0.1 take win=0 persist=2 wall_ticks=8` | 3261 | 30/30/9 | 15/-0/-24 | -614 / -570 | 0.34 / 1.00 / 39 | -/-/2/-/-/- | - | OK-PRIOR |
| M7_PC18 | `profit M7 * pct>=0.2 pulled_mult>=10 secs_fav<=5 take win=15 persist=2 wall_ticks=8` | 3326 | 30/30/10 | 17/-2/-21 | -811 / -771 | - / - / - | -/-/-/-/-/- | - | nan |

Placebo (random exit at the same pct, same count) and family null over the profit set (SZ-IJK ptr_null): #1 own p 0.66 / family p 1.00; #2 own p 0.71 / family p 1.00; #3 own p 0.97 / family p 1.00; #4 own p 0.42 / family p 1.00; #5 own p 0.42 / family p 1.00

Family null over the WHOLE profit set of M7 (SZ-IJK, stage 1+2 cells with >= 20 fires, B=100, slip 1.2, bucketed placebo = approximation): 63 of 7213 cells have family p < .05 (0.9%; around 5% is what the null alone gives); cells with own p < .05: 188 (expected by chance 361); the best single lines reach the B=100 floor (p about 0.01), use for ranking only.

Slip sensitivity of the best line `profit M7 * pct>=0.2 pulled_mult>=3 take win=5 persist=3 wall_ticks=8` (first-order, stack cut % / d mean $/wk):

| slip pts | cut L6M | cut L3M | cut L1M | cut HOLD | cut PRE | cut X' | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|---|---|
| 0.57 | 33 | 33 | 12 | 14 | -1 | -22 | -144 | -450 |
| 0.80 | 33 | 33 | 12 | 14 | -1 | -23 | -282 | -539 |
| 1.20 | 32 | 32 | 11 | 13 | -2 | -24 | -521 | -694 |
| 1.60 | 31 | 31 | 10 | 13 | -3 | -26 | -760 | -849 |

By window (best line, slip 1.2, first-order): L1M cut 11 / d mean 3133; L3M cut 32 / d mean 1333; L6M cut 32 / d mean -521; HOLD cut 13 / d mean -297; PRE cut -2 / d mean -694; X' cut -24 / d mean -304. The held-out live week (11-01..05) sits inside L1M, a trending week: P7 carried about $159k of Targets that week, so any rule that exits winners early pays for itself only in the choppy weeks of the history; the single-week replay (REDO-R13: autopilot/R13_TRAIL_LIVE_REPLAY_BOOKS.md) and the 43-month first-order table are different regimes and are both shown, not averaged.

By entry session (the same line applied to one session only; stack effect): 

| session | trades | fires | cut L6M | cut PRE | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|
| london | 2058 | 2002 | 25 | -1 | 30 | -394 |
| nyam | 1365 | 1318 | 3 | -1 | -243 | -533 |

## U7 (1118 trades with a path; no-rule = LPB_BASE reference row: cut 0 by definition)

First-order top-20 by the recents key (mean equal-mean cut on L6M/L3M/L1M), at most 4 per family and a cap per action; exact columns are the stack maxDD cut vs LPB_BASE (engine slip 0.80) where the PTR_ set has run:

| # | line | fires | FO cut L6M/L3M/L1M | FO cut HOLD/PRE/X' | FO d mean L6M / PRE | placebo p / family p / WF2w % | EXACT cut L6M/L3M/L1M/HOLD/PRE/X' | EXACT d mean L6M | rule 2a (FO) |
|---|---|---|---|---|---|---|---|---|---|
| U7_01 | `profit U7 * pct>=0.3 pulled_against_mult>=20 ahead_rel_slow>=1.2 take win=5 persist=3` | 252 | 27/27/25 | -0/4/-10 | 1087 / -260 | 0.27 / 0.99 / 14 | 17/17/25/-1/-/- | 585 | OK-PRIOR |
| U7_02 | `profit U7 * pct>=0.3 pulled_against_mult>=20 tighten 20 win=5 persist=5` | 285 | 26/26/28 | -12/-0/-2 | 723 / -601 | 0.54 / 1.00 / 10 | 16/16/28/-12/-/- | 389 | OK-PRIOR |
| U7_03 | `profit U7 * pct>=0.3 pulled_against_mult>=20 step 5 win=5 persist=5` | 354 | 29/29/29 | -10/-1/-0 | 46 / -461 | 0.67 / 1.00 / 9 | 16/16/29/-/-/- | -374 | OK-PRIOR |
| U7_04 | `profit U7 * pct>=0.3 pulled_against_mult>=20 take win=5 persist=5` | 375 | 29/29/27 | -10/-1/-0 | 40 / -455 | 0.62 / 1.00 / 10 | 16/16/28/-/-/- | -435 | OK-PRIOR |
| U7_05 | `profit U7 * pct>=0.3 pulled_against_mult>=20 tighten 8 win=5 persist=5` | 353 | 29/29/27 | -9/-1/-0 | 51 / -484 | 0.52 / 1.00 / 9 | 17/17/27/-/-/- | -369 | OK-PRIOR |
| U7_06 | `profit U7 * pct>=0.3 delta_mult>=30 step 5 win=15 persist=1` | 369 | 25/25/16 | -9/2/1 | 1694 / -17 | 0.53 / 1.00 / 22 | -/-/-/-/-/- | - | OK-PRIOR |
| U7_07 | `profit U7 * pct>=0.4 delta_mult>=20 step 5 win=15 persist=5` | 399 | 28/28/10 | -7/5/6 | 1608 / -564 | 0.32 / 1.00 / 25 | -/-/-/-/-/- | - | OK-PRIOR |
| U7_08 | `profit U7 * pct>=0.3 delta_mult>=30 take win=15 persist=1` | 376 | 23/23/17 | -9/1/2 | 1663 / -2 | 0.54 / 1.00 / 22 | -/-/-/-/-/- | - | OK-PRIOR |
| U7_09 | `profit U7 * pct>=0.3 delta_mult>=30 tighten 8 win=15 persist=1` | 369 | 25/25/16 | -9/2/1 | 1653 / -14 | 0.55 / 1.00 / 22 | -/-/-/-/-/- | - | OK-PRIOR |
| U7_S01 | `profit U7 * pct>=0.4 delta_mult>=20 tighten 30 win=15 persist=5` | 257 | 25/25/15 | -0/4/-0 | 1617 / -689 | - / - / - | 9/9/15/-/-/- | 1074 | nan |
| U7_10 | `profit U7 * pct>=0.2 pulled_against_mult>=30 imb5<=-0.3 take win=8 persist=1` | 425 | 26/26/25 | -5/1/-3 | 326 / -202 | 0.56 / 1.00 / 16 | -/-/-/-/-/- | - | OK-PRIOR |
| U7_S02 | `profit U7 * pct>=0.4 delta_mult>=30 step 5 win=15 persist=1` | 311 | 24/24/16 | -5/2/0 | 1195 / -65 | - / - / - | -/-/-/-/-/- | - | nan |
| U7_PC06 | `profit U7 * pct>=0.5 pulled_mult>=10 secs_fav<=2 take win=15 persist=10 wall_ticks=8` | 331 | 29/29/6 | -4/8/5 | 1324 / 294 | - / - / - | -/-/-/-/-/- | - | nan |
| U7_PC04 | `profit U7 * pct>=0.5 pulled_mult>=5 secs_fav<=2 take win=10 persist=10 wall_ticks=8` | 342 | 29/29/6 | -3/12/3 | 1301 / 108 | - / - / - | -/21/6/-/-/- | - | nan |
| U7_11 | `profit U7 * pct>=0.3 pulled_against_mult>=20 ahead_rel>=1.2 take win=5 persist=3` | 251 | 25/25/24 | -2/4/-7 | 341 / -253 | 0.30 / 1.00 / 13 | -/-/-/-/-/- | - | OK-PRIOR |
| U7_S03 | `profit U7 * pct>=0.5 pulled_against_mult>=50 tighten 30 win=15 persist=1` | 172 | 21/21/10 | -1/1/-4 | 1973 / -104 | - / - / - | -/-/-/-/-/- | - | nan |
| U7_PC01 | `profit U7 * pct>=0.5 pulled_mult>=3 secs_fav<=2 take win=8 persist=10 wall_ticks=8` | 404 | 29/29/6 | -4/11/7 | 1101 / 366 | - / - / - | 33/33/6/-7/-/- | 958 | nan |
| U7_S04 | `profit U7 * pct>=0.5 pulled_against_mult>=50 step 20 win=15 persist=1` | 169 | 21/21/10 | -5/1/-4 | 1875 / -39 | - / - / - | -/-/-/-/-/- | - | nan |
| U7_PC05 | `profit U7 * pct>=0.5 pulled_mult>=5 secs_fav<=2 take win=15 persist=10 wall_ticks=8` | 515 | 29/29/6 | -4/10/8 | 996 / 260 | - / - / - | -/33/6/-/-/- | - | nan |
| U7_PC02 | `profit U7 * pct>=0.5 pulled_mult>=3 secs_fav<=2 take win=10 persist=10 wall_ticks=8` | 487 | 29/29/6 | -4/10/3 | 996 / 463 | - / - / - | 33/33/6/-7/-/- | 845 | nan |
| U7_PC03 | `profit U7 * pct>=0.5 pulled_mult>=3 secs_fav<=2 take win=15 persist=10 wall_ticks=8` | 565 | 29/29/6 | -4/10/3 | 996 / 259 | - / - / - | 33/33/6/-/-/- | 845 | nan |
| U7_12 | `profit U7 * pct>=0.2 pulled_mult>=5 secs_fav<=0 take win=5 persist=3` | 427 | 29/29/26 | -4/9/9 | -999 / -555 | 0.11 / 0.87 / 18 | -/-/-/-/-/- | - | OK-PRIOR |
| U7_13 | `profit U7 * pct>=0.2 pulled_against_mult>=30 imb5<=-0.3 tighten 16 win=8 persist=1` | 370 | 25/25/19 | -6/1/-3 | 364 / -139 | 0.52 / 1.00 / 18 | -/-/-/-/-/- | - | OK-PRIOR |
| U7_S05 | `profit U7 * pct>=0.3 delta_mult>=30 ahead_rel>=1.2 tighten 16 win=15 persist=1` | 160 | 20/20/9 | -1/3/4 | 1471 / -380 | - / - / - | -/-/-/-/-/- | - | nan |
| U7_S06 | `profit U7 * pct>=0.3 pulled_against_mult>=20 ahead_rel_slow>=1.2 tighten 16 win=5 persist=3` | 218 | 21/21/20 | -2/6/-10 | 532 / -485 | - / - / - | -/-/-/-/-/- | - | nan |
| U7_14 | `profit U7 * pct>=0.4 tot_rel_slow>=1.5 tighten 20 persist=2` | 549 | 23/23/17 | 3/7/1 | 426 / -774 | 0.29 / 0.99 / 34 | -/-/-/-/-/- | - | OK-PRIOR |
| U7_PC10 | `profit U7 * pct>=0.5 pulled_mult>=5 secs_fav<=2 take win=8 persist=10 wall_ticks=8` | 247 | 23/23/6 | -3/10/5 | 1342 / 134 | - / - / - | -/-/-/-/-/- | - | nan |
| U7_S07 | `profit U7 * pct>=0.4 tot_rel_slow>=1.5 tighten 30 persist=2` | 450 | 23/23/15 | 3/14/2 | 399 / -360 | - / - / - | -/-/-/-/-/- | - | nan |
| U7_PC13 | `profit U7 * pct>=0.5 pulled_mult>=3 secs_fav<=2 take win=5 persist=10 wall_ticks=8` | 191 | 25/25/-1 | -2/15/2 | 1367 / -42 | - / - / - | -/-/-/-/-/- | - | nan |
| U7_S08 | `profit U7 * pct>=0.5 pulled_mult>=5 secs_fav<=0 take win=5 persist=3` | 288 | 26/26/13 | -3/2/-2 | -62 / -220 | - / - / - | -/-/-/-/-/- | - | nan |

Placebo (random exit at the same pct, same count) and family null over the profit set (SZ-IJK ptr_null): #1 own p 0.27 / family p 0.99; #2 own p 0.54 / family p 1.00; #3 own p 0.67 / family p 1.00; #4 own p 0.62 / family p 1.00; #5 own p 0.52 / family p 1.00

Family null over the WHOLE profit set of U7 (SZ-IJK, stage 1+2 cells with >= 20 fires, B=100, slip 1.2, bucketed placebo = approximation): 253 of 15270 cells have family p < .05 (1.7%; around 5% is what the null alone gives); cells with own p < .05: 660 (expected by chance 764); the best single lines reach the B=100 floor (p about 0.01), use for ranking only.

Best cell per action type (stage 2/3, first-order, by the recents key):

| action | feature / cell | fires | cut L6M/L3M/L1M | cut PRE | d mean L6M |
|---|---|---|---|---|---|
| take | delta_mult+sweep_against arm 0.3 thr 30.0 win 15 P 1 X 0 F 0.0 | 313 | 28/28/17 | -2 | 1730 |
| tighten | pulled_against_mult arm 0.3 thr 20.0 win 5 P 5 X 20 F 0.0 | 285 | 26/26/28 | -0 | 723 |
| lock | delta_mult arm 0.4 thr 20.0 win 15 P 5 X 10 F 0.0 | 211 | 20/20/14 | 3 | 1635 |
| step | pulled_against_mult arm 0.3 thr 20.0 win 5 P 5 X 5 F 0.0 | 354 | 29/29/29 | -1 | 46 |
| scale | pulled_against_mult arm 0.2 thr 30.0 win 8 P 3 X 0 F 0.75 | 548 | 20/20/16 | 1 | 240 |
| adaptive tighten | delta_mult|adapt_f_g1 arm 0.4 thr 20.0 win 15 P 5 X 32 F 1.0 | 364 | 29/29/9 | 4 | 1608 |

Loss-cut mirror (pulled_mult at a new favourable extreme, secs_fav<=0): best arm 0.2 x pulled_mult>=5.0 win 5 persist 3: fires 427, cut L6M/L3M/L1M 29/29/26, PRE 9, d mean L6M -999.

Slip sensitivity of the best line `profit U7 * pct>=0.5 pulled_mult>=3 secs_fav<=2 take win=15 persist=10 wall_ticks=8` (first-order, stack cut % / d mean $/wk):

| slip pts | cut L6M | cut L3M | cut L1M | cut HOLD | cut PRE | cut X' | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|---|---|
| 0.57 | 29 | 29 | 6 | -4 | 10 | 4 | 1136 | 357 |
| 0.80 | 29 | 29 | 6 | -4 | 10 | 4 | 1085 | 321 |
| 1.20 | 29 | 29 | 6 | -4 | 10 | 3 | 996 | 259 |
| 1.60 | 28 | 28 | 6 | -5 | 10 | 3 | 908 | 196 |

By window (best line, slip 1.2, first-order): L1M cut 6 / d mean 1496; L3M cut 29 / d mean 734; L6M cut 29 / d mean 996; HOLD cut -4 / d mean 574; PRE cut 10 / d mean 259; X' cut 3 / d mean -333. The held-out live week (11-01..05) sits inside L1M, a trending week: P7 carried about $159k of Targets that week, so any rule that exits winners early pays for itself only in the choppy weeks of the history; the single-week replay (REDO-R13: autopilot/R13_TRAIL_LIVE_REPLAY_BOOKS.md) and the 43-month first-order table are different regimes and are both shown, not averaged.

By entry session (the same line applied to one session only; stack effect): 

| session | trades | fires | cut L6M | cut PRE | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|
| asia | 567 | 289 | 18 | 1 | 366 | 199 |
| london | 551 | 276 | 11 | 9 | 218 | 159 |

## H7 (881 trades with a path; no-rule = LPB_BASE reference row: cut 0 by definition)

First-order top-20 by the recents key (mean equal-mean cut on L6M/L3M/L1M), at most 4 per family and a cap per action; exact columns are the stack maxDD cut vs LPB_BASE (engine slip 0.80) where the PTR_ set has run:

| # | line | fires | FO cut L6M/L3M/L1M | FO cut HOLD/PRE/X' | FO d mean L6M / PRE | placebo p / family p / WF2w % | EXACT cut L6M/L3M/L1M/HOLD/PRE/X' | EXACT d mean L6M | rule 2a (FO) |
|---|---|---|---|---|---|---|---|---|---|
| H7_01 | `profit H7 * pct>=0.4 dd>=20 or ice_against>=3 take persist=5` | 463 | 10/10/0 | 3/2/17 | 597 / -394 | 0.04 / 0.38 / 34 | 5/5/0/3/-/- | 367 | OK-PRIOR |
| H7_02 | `profit H7 * pct>=0.4 dd>=20 or ice_against>=3 tighten 16 persist=5` | 396 | 9/9/0 | 3/2/16 | 516 / -355 | 0.04 / 0.55 / 33 | 4/4/0/3/-/- | 286 | OK-PRIOR |
| H7_03 | `profit H7 * pct>=0.3 pulled_mult>=20 secs_fav<=0 take win=10 persist=2` | 138 | 9/9/-0 | -3/-3/0 | 228 / -295 | 0.47 / 1.00 / 3 | 11/11/0/-/-/- | -262 | OK-PRIOR |
| H7_04 | `profit H7 * pct>=0.2 ice_against>=3 or pulled_mult>=30 take win=5 persist=3` | 516 | 7/7/4 | -3/2/11 | 245 / -578 | 0.26 / 1.00 / 23 | 7/7/4/-/-/- | 319 | OK-PRIOR |
| H7_05 | `profit H7 * pct>=0.5 dd>=16 tighten 20 persist=10` | 219 | 7/7/0 | -1/1/14 | 442 / -324 | 0.14 / 0.85 / 11 | 2/2/0/-/-/- | 189 | OK-PRIOR |
| H7_06 | `profit H7 * pct>=0.4 sweep_against>=8 tighten 5 win=5 persist=10` | 206 | 9/9/-2 | -1/-5/6 | 233 / -125 | 0.64 / 1.00 / 1 | -/-/-1/-/-/- | - | OK-PRIOR |
| H7_07 | `profit H7 * pct>=0.4 sweep_against>=8 take win=5 persist=10` | 213 | 10/10/-2 | -1/-5/6 | 209 / -153 | 0.66 / 1.00 / 1 | -/-/-1/-/-/- | - | OK-PRIOR |
| H7_08 | `profit H7 * pct>=0.4 sweep_against>=8 tighten 8 win=5 persist=10` | 200 | 9/9/-2 | -1/-5/6 | 222 / -135 | 0.77 / 1.00 / 1 | -/-/-1/-/-/- | - | OK-PRIOR |
| H7_09 | `profit H7 * pct>=0.5 dd>=16 or sweep_against>=8 take win=3 persist=5` | 366 | 8/8/-2 | -2/-3/9 | 363 / -336 | 0.14 / 0.94 / 11 | -/-/-0/-/-/- | - | OK-PRIOR |
| H7_10 | `profit H7 * pct>=0.4 sweep_against>=8 step 5 win=5 persist=10` | 200 | 9/9/-2 | -2/-5/6 | 232 / -126 | 0.75 / 1.00 / 1 | -/-/-1/-/-/- | - | OK-PRIOR |
| H7_11 | `profit H7 * pct>=0.5 ice_against>=1 tighten 8 persist=3` | 585 | 8/8/-1 | 2/-9/6 | 284 / -620 | 0.40 / 1.00 / 32 | -/-/1/-/-/- | - | OK-PRIOR |
| H7_S01 | `profit H7 * pct>=0.5 dd>=16 or sweep_against>=8 tighten 16 win=3 persist=5` | 318 | 6/6/2 | -1/-3/10 | 266 / -393 | - / - / - | 3/3/2/-1/-/- | 115 | nan |
| H7_S02 | `profit H7 * pct>=0.5 dd>=16 tighten 12 persist=10` | 238 | 6/6/0 | -1/1/15 | 414 / -266 | - / - / - | -/-/-/-/-/- | - | nan |
| H7_S03 | `profit H7 * pct>=0.5 dd>=16 tighten 5 persist=10` | 238 | 6/6/0 | -1/1/15 | 414 / -266 | - / - / - | -/-/-/-/-/- | - | nan |
| H7_S04 | `profit H7 * pct>=0.2 ice_against>=3 or pulled_mult>=30 tighten 16 win=5 persist=3` | 458 | 6/6/3 | -3/2/13 | 179 / -362 | - / - / - | -/-/-/-/-/- | - | nan |
| H7_12 | `profit H7 * pct>=0.5 dd>=16 step 10 persist=10` | 231 | 6/6/0 | -1/1/15 | 408 / -253 | 0.11 / 0.85 / 15 | -/-/0/-/-/- | - | OK-PRIOR |
| H7_S05 | `profit H7 * pct>=0.4 delta_mult>=10 tighten 20 win=10 persist=10` | 311 | 8/8/0 | 3/-2/5 | 60 / -264 | - / - / - | -/-/-/-/-/- | - | nan |
| H7_13 | `profit H7 * pct>=0.2 pulled_mult>=30 take win=8 persist=10` | 49 | 4/4/4 | -1/-1/0 | 331 / -133 | 0.52 / 1.00 / 3 | -/-/4/-/-/- | - | OK-PRIOR |
| H7_S06 | `profit H7 * pct>=0.2 pulled_mult>=30 tighten 5 win=8 persist=10` | 49 | 4/4/4 | -1/-1/0 | 327 / -134 | - / - / - | -/-/-/-/-/- | - | nan |
| H7_14 | `profit H7 * pct>=0.5 ice_against>=1 step 5 persist=3` | 594 | 7/7/-1 | 2/-9/6 | 309 / -649 | 0.36 / 1.00 / 32 | -/-/1/-/-/- | - | OK-PRIOR |
| H7_15 | `profit H7 * pct>=0.4 delta_mult>=10 lock 10 win=10 persist=10` | 200 | 6/6/0 | 2/-2/2 | 310 / -139 | 0.35 / 1.00 / 25 | -/-/0/-/-/- | - | OK-PRIOR |
| H7_S07 | `profit H7 * pct>=0.2 pulled_mult>=30 tighten 8 win=8 persist=10` | 48 | 4/4/4 | -1/-1/0 | 308 / -128 | - / - / - | -/-/-/-/-/- | - | nan |
| H7_S08 | `profit H7 * pct>=0.4 ice_against>=3 tighten 8 persist=5` | 329 | 7/7/0 | 0/-1/19 | 225 / -166 | - / - / - | -/-/-/-/-/- | - | nan |
| H7_16 | `profit H7 * pct>=0.4 delta_mult>=10 lock 5 win=10 persist=10` | 182 | 6/6/0 | 2/-3/6 | 265 / -160 | 0.41 / 1.00 / 22 | -/-/0/-/-/- | - | OK-PRIOR |
| H7_17 | `profit H7 * pct>=0.4 delta_mult>=10 lock 5 win=8 persist=3` | 279 | 10/10/-5 | 1/-1/10 | 107 / -349 | 0.17 / 0.96 / 24 | -/-/-2/-/-/- | - | OK-PRIOR |
| H7_PC02 | `profit H7 * pct>=0.4 pulled_mult>=10 secs_fav<=2 take win=3 persist=2 wall_ticks=8` | 185 | 12/12/-5 | 1/-1/-0 | -207 / -112 | - / - / - | -/-/-/-/-/- | - | nan |
| H7_18 | `profit H7 * pct>=0.4 delta_mult>=10 lock 2 win=10 persist=10` | 172 | 6/6/0 | 2/-3/5 | 267 / -62 | 0.56 / 1.00 / 20 | -/-/0/-/-/- | - | OK-PRIOR |
| H7_PC12 | `profit H7 * pct>=0.4 pulled_mult>=5 secs_fav<=2 take win=3 persist=3 wall_ticks=8` | 284 | 8/8/1 | 3/-7/4 | -457 / -460 | - / - / - | -/-/-/-/-/- | - | nan |
| H7_19 | `profit H7 * pct>=0.2 pulled_mult>=30 scale 0.5 win=8 persist=10` | 49 | 2/2/2 | 0/0/0 | 125 / -50 | 0.36 / 1.00 / 0 | -/-/2/-/-/- | - | OK-PRIOR |
| H7_20 | `profit H7 * pct>=0.2 pulled_mult>=30 scale 0.75 win=5 persist=3` | 86 | 2/2/2 | -1/1/0 | 141 / -50 | 0.27 / 1.00 / 3 | -/-/2/-/-/- | - | OK-PRIOR |

Placebo (random exit at the same pct, same count) and family null over the profit set (SZ-IJK ptr_null): #1 own p 0.04 / family p 0.38; #2 own p 0.04 / family p 0.55; #3 own p 0.47 / family p 1.00; #4 own p 0.26 / family p 1.00; #5 own p 0.14 / family p 0.85

Family null over the WHOLE profit set of H7 (SZ-IJK, stage 1+2 cells with >= 20 fires, B=100, slip 1.2, bucketed placebo = approximation): 486 of 13378 cells have family p < .05 (3.6%; around 5% is what the null alone gives); cells with own p < .05: 685 (expected by chance 669); the best single lines reach the B=100 floor (p about 0.01), use for ranking only.

Best cell per action type (stage 2/3, first-order, by the recents key):

| action | feature / cell | fires | cut L6M/L3M/L1M | cut PRE | d mean L6M |
|---|---|---|---|---|---|
| take | dd+ice_against arm 0.4 thr 20.0 win 0 P 5 X 0 F 0.0 | 463 | 10/10/0 | 2 | 597 |
| tighten | dd+ice_against arm 0.4 thr 20.0 win 0 P 5 X 16 F 0.0 | 396 | 9/9/0 | 2 | 516 |
| lock | sweep_against arm 0.5 thr 4.0 win 5 P 10 X 10 F 0.0 | 253 | 5/5/2 | -8 | 428 |
| step | sweep_against arm 0.4 thr 8.0 win 5 P 10 X 5 F 0.0 | 200 | 9/9/-2 | -5 | 232 |
| scale | delta_mult arm 0.4 thr 20.0 win 15 P 1 X 0 F 0.75 | 471 | 3/3/0 | -1 | 213 |
| adaptive tighten | sweep_against|adapt_f_g1 arm 0.4 thr 8.0 win 5 P 10 X 8 F 1.0 | 205 | 9/9/-2 | -5 | 247 |

Loss-cut mirror (pulled_mult at a new favourable extreme, secs_fav<=0): best arm 0.3 x pulled_mult>=20.0 win 10 persist 2: fires 138, cut L6M/L3M/L1M 9/9/-0, PRE -3, d mean L6M 228.

Slip sensitivity of the best line `profit H7 * pct>=0.2 ice_against>=3 or pulled_mult>=30 take win=5 persist=3` (first-order, stack cut % / d mean $/wk):

| slip pts | cut L6M | cut L3M | cut L1M | cut HOLD | cut PRE | cut X' | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|---|---|
| 0.57 | 7 | 7 | 4 | -3 | 2 | 13 | 271 | -524 |
| 0.80 | 7 | 7 | 4 | -3 | 2 | 12 | 261 | -544 |
| 1.20 | 7 | 7 | 4 | -3 | 2 | 11 | 245 | -578 |
| 1.60 | 7 | 7 | 4 | -3 | 2 | 11 | 229 | -612 |

By window (best line, slip 1.2, first-order): L1M cut 4 / d mean -291; L3M cut 7 / d mean 460; L6M cut 7 / d mean 245; HOLD cut -3 / d mean 360; PRE cut 2 / d mean -578; X' cut 11 / d mean -292. The held-out live week (11-01..05) sits inside L1M, a trending week: P7 carried about $159k of Targets that week, so any rule that exits winners early pays for itself only in the choppy weeks of the history; the single-week replay (REDO-R13: autopilot/R13_TRAIL_LIVE_REPLAY_BOOKS.md) and the 43-month first-order table are different regimes and are both shown, not averaged.

By entry session (the same line applied to one session only; stack effect): 

| session | trades | fires | cut L6M | cut PRE | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|
| asia | 554 | 274 | 4 | 2 | 202 | -477 |
| nyam | 327 | 242 | 3 | -1 | -57 | -153 |

## A7 (956 trades with a path; no-rule = LPB_BASE reference row: cut 0 by definition)

First-order top-20 by the recents key (mean equal-mean cut on L6M/L3M/L1M), at most 4 per family and a cap per action; exact columns are the stack maxDD cut vs LPB_BASE (engine slip 0.80) where the PTR_ set has run:

| # | line | fires | FO cut L6M/L3M/L1M | FO cut HOLD/PRE/X' | FO d mean L6M / PRE | placebo p / family p / WF2w % | EXACT cut L6M/L3M/L1M/HOLD/PRE/X' | EXACT d mean L6M | rule 2a (FO) |
|---|---|---|---|---|---|---|---|---|---|
| A7_PC02 | `profit A7 * pct>=0.2 pulled_mult>=20 secs_fav<=10 take win=5 persist=1 wall_ticks=8` | 514 | 12/12/2 | 3/0/0 | 400 / -332 | - / - / - | -/-/-/-/-/- | - | nan |
| A7_PC03 | `profit A7 * pct>=0.3 pulled_mult>=10 secs_fav<=2 take win=5 persist=1 wall_ticks=8` | 711 | 11/11/4 | 3/2/-0 | 124 / -305 | - / - / - | -/-/-/-/-/- | - | nan |
| A7_03 | `profit A7 * pct>=0.2 pulled_against_mult>=30 take win=10 persist=5 wall_ticks=8` | 571 | 10/10/3 | 2/-2/-2 | 206 / -198 | 0.81 / 1.00 / 24 | 15/15/18/-/-/- | 961 | OK-PRIOR |
| A7_PC01 | `profit A7 * pct>=0.3 pulled_mult>=3 secs_fav<=2 take win=5 persist=10 wall_ticks=8` | 256 | 13/13/1 | 2/1/-0 | -67 / -4 | - / - / - | -/-/-/-/-/- | - | nan |
| A7_PC04 | `profit A7 * pct>=0.2 pulled_mult>=10 secs_fav<=10 take win=2 persist=1 wall_ticks=8` | 733 | 11/11/3 | 4/3/-1 | -80 / -253 | - / - / - | -/-/-/-/-/- | - | nan |
| A7_17 | `profit A7 * pct>=0.2 pulled_against_mult>=30 tighten 5 win=10 persist=5 wall_ticks=8` | 564 | 10/10/3 | 2/-2/-2 | 135 / -194 | 0.81 / 1.00 / 25 | -/-/24/-/-/- | - | OK-PRIOR |
| A7_08 | `profit A7 * pct>=0.2 sweep_against>=6 step 10 win=5 persist=10 wall_ticks=8` | 552 | 9/9/5 | 3/1/-2 | 21 / -261 | 0.41 / 1.00 / 27 | 9/9/24/-/-/- | 487 | OK-PRIOR |
| A7_PC07 | `profit A7 * pct>=0.3 pulled_mult>=20 secs_fav<=10 take win=10 persist=2 wall_ticks=8` | 692 | 10/10/3 | 3/1/-4 | -55 / -95 | - / - / - | -/-/-/-/-/- | - | nan |
| A7_PC15 | `profit A7 * pct>=0.2 pulled_mult>=20 secs_fav<=10 take win=8 persist=3 wall_ticks=8` | 619 | 9/9/4 | 4/3/-1 | 19 / -228 | - / - / - | -/-/-/-/-/- | - | nan |
| A7_13 | `profit A7 * pct>=0.2 sweep_against>=4 take win=8 persist=10 wall_ticks=8` | 912 | 9/9/6 | 3/-0/-1 | -89 / -405 | 0.32 / 1.00 / 38 | -/6/22/-/-/- | - | OK-PRIOR |
| A7_PC05 | `profit A7 * pct>=0.2 pulled_mult>=20 secs_fav<=10 take win=8 persist=1 wall_ticks=8` | 709 | 11/11/4 | 4/3/-1 | -231 / -203 | - / - / - | -/-/-/-/-/- | - | nan |
| A7_PC08 | `profit A7 * pct>=0.3 pulled_mult>=5 secs_fav<=2 take win=8 persist=10 wall_ticks=8` | 316 | 12/12/-3 | 2/1/-1 | -10 / -153 | - / - / - | -/-/-/-/-/- | - | nan |
| A7_PC16 | `profit A7 * pct>=0.2 pulled_mult>=10 secs_fav<=10 take win=3 persist=2 wall_ticks=8` | 748 | 9/9/6 | 6/3/-3 | -188 / -215 | - / - / - | -/-/-/-/-/- | - | nan |
| A7_PC19 | `profit A7 * pct>=0.2 pulled_mult>=10 secs_fav<=10 take win=8 persist=10 wall_ticks=8` | 636 | 9/9/4 | 4/1/-3 | -192 / -303 | - / - / - | -/-/-/-/-/- | - | nan |
| A7_02 | `profit A7 * pct>=0.3 pulled_against_mult>=30 or pulled_mult>=20 take win=10 persist=3 wall_ticks=8` | 811 | 10/10/2 | 2/2/-4 | -221 / -122 | 0.08 / 0.73 / 43 | 8/8/-1/2/-/- | -878 | OK-PRIOR |
| A7_14 | `profit A7 * pct>=0.3 delta_mult>=2 take win=5 persist=1 wall_ticks=8` | 893 | 9/9/2 | 3/1/-5 | -97 / -376 | 0.02 / 0.73 / 44 | -/-/2/-/-/- | - | OK-PRIOR |
| A7_20 | `profit A7 * pct>=0.3 sweep_against>=6 pulled_mult>=10 take win=3 persist=1 wall_ticks=8` | 832 | 10/10/2 | 2/2/-5 | -206 / -184 | 0.05 / 0.75 / 43 | -/-/19/-/-/- | - | OK-PRIOR |
| A7_04 | `profit A7 * pct>=0.3 pulled_mult>=30 sweep_against>=6 take win=15 persist=1 wall_ticks=8` | 760 | 10/10/2 | 4/2/-0 | -237 / -128 | 0.14 / 0.91 / 35 | 5/5/18/-/-/- | -624 | OK-PRIOR |
| A7_PC06 | `profit A7 * pct>=0.2 pulled_mult>=20 secs_fav<=10 take win=10 persist=2 wall_ticks=8` | 747 | 10/10/3 | 3/1/-2 | -363 / -223 | - / - / - | -/-/-/-/-/- | - | nan |
| A7_PC11 | `profit A7 * pct>=0.3 pulled_mult>=5 secs_fav<=10 take win=3 persist=3 wall_ticks=8` | 850 | 10/10/2 | 1/1/-4 | -260 / -230 | - / - / - | -/-/-/-/-/- | - | nan |
| A7_PC13 | `profit A7 * pct>=0.3 pulled_mult>=10 secs_fav<=5 take win=5 persist=2 wall_ticks=8` | 787 | 10/10/2 | 1/1/-5 | -245 / -94 | - / - / - | -/-/-/-/-/- | - | nan |
| A7_PC09 | `profit A7 * pct>=0.3 pulled_mult>=3 secs_fav<=5 take win=2 persist=5 wall_ticks=8` | 525 | 11/11/0 | 4/-1/-3 | -233 / -303 | - / - / - | -/-/-/-/-/- | - | nan |
| A7_07 | `profit A7 * pct>=0.3 pulled_mult>=30 take win=15 persist=1 wall_ticks=8` | 784 | 10/10/2 | 4/2/-2 | -234 / -141 | 0.07 / 0.75 / 42 | 7/7/18/-/-/- | -548 | OK-PRIOR |
| A7_PC20 | `profit A7 * pct>=0.3 pulled_mult>=20 secs_fav<=5 take win=15 persist=2 wall_ticks=8` | 734 | 10/10/2 | 3/1/-3 | -232 / -339 | - / - / - | -/-/-/-/-/- | - | nan |
| A7_16 | `profit A7 * pct>=0.4 dd>=5 tighten 5 win=0 persist=1 wall_ticks=8` | 787 | 6/6/4 | 2/-1/-4 | 49 / -251 | 0.92 / 1.00 / 33 | -/-/29/-/-/- | - | OK-PRIOR |
| A7_15 | `profit A7 * pct>=0.4 dd>=5 take win=0 persist=1 wall_ticks=8` | 787 | 6/6/4 | 2/-1/-4 | 49 / -251 | 0.92 / 1.00 / 33 | -/-/29/-/-/- | - | OK-PRIOR |
| A7_PC10 | `profit A7 * pct>=0.2 pulled_mult>=3 secs_fav<=5 take win=2 persist=5 wall_ticks=8` | 574 | 11/11/-1 | 7/-3/-2 | -216 / -304 | - / - / - | -/-/-/-/-/- | - | nan |
| A7_05 | `profit A7 * pct>=0.2 pulled_against_mult>=50 take win=15 persist=2 wall_ticks=8` | 438 | 10/10/0 | 3/-1/-1 | -289 / -92 | 0.68 / 1.00 / 16 | 6/6/20/-/-/- | 369 | OK-PRIOR |
| A7_18 | `profit A7 * pct>=0.2 sweep_against>=4 lock 10 win=8 persist=10 wall_ticks=8` | 759 | 7/7/7 | 2/-1/1 | -269 / -371 | 0.66 / 1.00 / 39 | -/-/23/-/-/- | - | OK-PRIOR |
| A7_S06 | `profit A7 * pct>=0.3 pulled_against_mult>=10 sweep_against>=6 take win=3 persist=3 wall_ticks=8` | 181 | 7/7/3 | 2/-2/-0 | 105 / -86 | - / - / - | -/-/-/-/-/- | - | nan |

Placebo (random exit at the same pct, same count) and family null over the profit set (SZ-IJK ptr_null): #1 own p 0.02 / family p 0.34; #2 own p 0.08 / family p 0.73; #3 own p 0.81 / family p 1.00; #4 own p 0.14 / family p 0.91; #5 own p 0.68 / family p 1.00

Family null over the WHOLE profit set of A7 (SZ-IJK, stage 1+2 cells with >= 20 fires, B=100, slip 1.2, bucketed placebo = approximation): 356 of 6894 cells have family p < .05 (5.2%; around 5% is what the null alone gives); cells with own p < .05: 427 (expected by chance 345); the best single lines reach the B=100 floor (p about 0.01), use for ranking only.

Slip sensitivity of the best line `profit A7 * pct>=0.2 pulled_against_mult>=30 take win=10 persist=5 wall_ticks=8` (first-order, stack cut % / d mean $/wk):

| slip pts | cut L6M | cut L3M | cut L1M | cut HOLD | cut PRE | cut X' | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|---|---|
| 0.57 | 10 | 10 | 3 | 2 | -2 | -2 | 313 | -173 |
| 0.80 | 10 | 10 | 3 | 2 | -2 | -2 | 274 | -182 |
| 1.20 | 10 | 10 | 3 | 2 | -2 | -2 | 206 | -198 |
| 1.60 | 10 | 10 | 2 | 2 | -2 | -2 | 138 | -214 |

By window (best line, slip 1.2, first-order): L1M cut 3 / d mean 467; L3M cut 10 / d mean 244; L6M cut 10 / d mean 206; HOLD cut 2 / d mean -27; PRE cut -2 / d mean -198; X' cut -2 / d mean -56. The held-out live week (11-01..05) sits inside L1M, a trending week: P7 carried about $159k of Targets that week, so any rule that exits winners early pays for itself only in the choppy weeks of the history; the single-week replay (REDO-R13: autopilot/R13_TRAIL_LIVE_REPLAY_BOOKS.md) and the 43-month first-order table are different regimes and are both shown, not averaged.

By entry session (the same line applied to one session only; stack effect): 

| session | trades | fires | cut L6M | cut PRE | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|
| asia | 956 | 571 | 10 | -2 | 206 | -198 |

## O7 (341 trades with a path; no-rule = LPB_BASE reference row: cut 0 by definition)

First-order top-20 by the recents key (mean equal-mean cut on L6M/L3M/L1M), at most 4 per family and a cap per action; exact columns are the stack maxDD cut vs LPB_BASE (engine slip 0.80) where the PTR_ set has run:

| # | line | fires | FO cut L6M/L3M/L1M | FO cut HOLD/PRE/X' | FO d mean L6M / PRE | placebo p / family p / WF2w % | EXACT cut L6M/L3M/L1M/HOLD/PRE/X' | EXACT d mean L6M | rule 2a (FO) |
|---|---|---|---|---|---|---|---|---|---|
| O7_01 | `profit O7 * pct>=0.3 delta_mult>=2 take win=10 persist=10 wall_ticks=8` | 255 | 5/5/2 | 1/-1/3 | 218 / -459 | 0.98 / 1.00 / 19 | 5/5/2/1/-/- | 30 | OK-PRIOR |
| O7_PC02 | `profit O7 * pct>=0.2 pulled_mult>=30 secs_fav<=5 take win=8 persist=2 wall_ticks=8` | 52 | 5/5/0 | 3/-0/0 | 375 / -52 | - / - / - | -/-/-/-/-/- | - | nan |
| O7_16 | `profit O7 * pct>=0.3 delta_mult>=2 tighten 5 win=10 persist=10 wall_ticks=8` | 254 | 5/5/2 | 2/-1/3 | 213 / -455 | 1.00 / 1.00 / 19 | -/-/-/-/-/- | - | OK-PRIOR |
| O7_18 | `profit O7 * pct>=0.3 delta_mult>=2 step 5 win=10 persist=10 wall_ticks=8` | 253 | 5/5/2 | 2/-1/3 | 196 / -451 | 1.00 / 1.00 / 19 | -/-/-/-/-/- | - | OK-PRIOR |
| O7_PC19 | `profit O7 * pct>=0.2 pulled_mult>=30 secs_fav<=5 take win=10 persist=2 wall_ticks=8` | 97 | 4/4/2 | 3/-2/0 | 196 / 6 | - / - / - | -/-/-/-/-/- | - | nan |
| O7_08 | `profit O7 * pct>=0.2 dd>=12 step 10 win=0 persist=10 wall_ticks=8` | 242 | 4/4/2 | 2/-1/4 | 148 / -411 | 1.00 / 1.00 / 15 | -/-/-/-/-/- | - | OK-PRIOR |
| O7_02 | `profit O7 * pct>=0.2 delta_mult>=5 take win=10 persist=10 wall_ticks=8` | 273 | 5/5/2 | 1/-1/5 | 35 / -592 | 1.00 / 1.00 / 13 | 5/5/2/1/-/- | 48 | OK-PRIOR |
| O7_19 | `profit O7 * pct>=0.2 delta_mult>=2 take win=8 persist=10 wall_ticks=8` | 278 | 5/5/2 | 3/-1/5 | 10 / -608 | 1.00 / 1.00 / 9 | -/-/-/-/-/- | - | OK-PRIOR |
| O7_PC11 | `profit O7 * pct>=0.3 pulled_mult>=10 secs_fav<=10 take win=3 persist=3 wall_ticks=8` | 216 | 4/4/2 | 1/0/2 | 81 / -272 | - / - / - | -/-/-/-/-/- | - | nan |
| O7_PC01 | `profit O7 * pct>=0.3 pulled_mult>=10 secs_fav<=5 take win=5 persist=5 wall_ticks=8` | 155 | 4/4/2 | 1/-1/-1 | 38 / -243 | - / - / - | -/-/-/-/-/- | - | nan |
| O7_06 | `profit O7 * pct>=0.3 pulled_against_mult>=20 step 10 win=10 persist=5 wall_ticks=8` | 267 | 4/4/2 | 3/-0/3 | 83 / -456 | 1.00 / 1.00 / 13 | -/-/-/-/-/- | - | OK-PRIOR |
| O7_12 | `profit O7 * pct>=0.3 wall_ahead_mult>=5 step 10 win=0 persist=1 wall_ticks=8` | 267 | 4/4/2 | 3/0/4 | 89 / -553 | 0.98 / 1.00 / 19 | -/-/-/-/-/- | - | OK-PRIOR |
| O7_PC07 | `profit O7 * pct>=0.3 pulled_mult>=20 secs_fav<=2 take win=8 persist=2 wall_ticks=8` | 99 | 4/4/2 | 2/-1/0 | 52 / -62 | - / - / - | -/-/-/-/-/- | - | nan |
| O7_PC10 | `profit O7 * pct>=0.2 pulled_mult>=10 secs_fav<=5 take win=5 persist=5 wall_ticks=8` | 181 | 4/4/2 | 3/0/-2 | 37 / -190 | - / - / - | -/-/-/-/-/- | - | nan |
| O7_14 | `profit O7 * pct>=0.3 pulled_against_mult>=5 step 10 win=3 persist=5 wall_ticks=8` | 262 | 4/4/2 | 3/-0/3 | 49 / -453 | 1.00 / 1.00 / 11 | -/-/-/-/-/- | - | OK-PRIOR |
| O7_PC06 | `profit O7 * pct>=0.3 pulled_mult>=20 secs_fav<=10 take win=10 persist=10 wall_ticks=8` | 93 | 4/4/2 | 2/-1/0 | 11 / -83 | - / - / - | -/-/-/-/-/- | - | nan |
| O7_13 | `profit O7 * pct>=0.3 wall_ahead_mult>=5 step 10 win=0 persist=1 wall_ticks=20` | 269 | 4/4/2 | 3/-0/4 | 27 / -587 | 1.00 / 1.00 / 13 | -/-/-/-/-/- | - | OK-PRIOR |
| O7_15 | `profit O7 * pct>=0.4 imb10<=-0.1 step 10 win=0 persist=1 wall_ticks=8` | 254 | 4/4/2 | 2/1/2 | 33 / -395 | 0.13 / 0.92 / 18 | -/-/-/-/-/- | - | OK-PRIOR |
| O7_07 | `profit O7 * pct>=0.3 imb10<=-0.2 step 10 win=0 persist=1 wall_ticks=8` | 273 | 4/4/2 | 3/1/4 | 7 / -504 | 0.91 / 1.00 / 18 | -/-/-/-/-/- | - | OK-PRIOR |
| O7_PC03 | `profit O7 * pct>=0.3 pulled_mult>=10 secs_fav<=2 take win=8 persist=5 wall_ticks=8` | 153 | 4/4/2 | 3/-1/-1 | -46 / -123 | - / - / - | -/-/-/-/-/- | - | nan |
| O7_PC05 | `profit O7 * pct>=0.3 pulled_mult>=20 secs_fav<=5 take win=8 persist=3 wall_ticks=8` | 136 | 4/4/3 | 2/-1/0 | -68 / -158 | - / - / - | -/-/-/-/-/- | - | nan |
| O7_PC09 | `profit O7 * pct>=0.3 pulled_mult>=20 secs_fav<=2 take win=15 persist=5 wall_ticks=8` | 184 | 4/4/2 | 3/-1/-1 | -46 / -145 | - / - / - | -/-/-/-/-/- | - | nan |
| O7_PC18 | `profit O7 * pct>=0.3 pulled_mult>=5 secs_fav<=2 take win=3 persist=3 wall_ticks=8` | 166 | 4/4/2 | 3/-0/-0 | -64 / -197 | - / - / - | -/-/-/-/-/- | - | nan |
| O7_03 | `profit O7 * pct>=0.4 imb5<=-0.1 take win=0 persist=2 wall_ticks=8` | 257 | 5/5/0 | 2/1/1 | -98 / -381 | 0.94 / 1.00 / 20 | 5/5/0/-/-/- | -99 | OK-PRIOR |
| O7_20 | `profit O7 * pct>=0.3 pulled_mult>=30 take win=15 persist=10 wall_ticks=8` | 239 | 4/4/2 | 2/-2/2 | -98 / -400 | 1.00 / 1.00 / 16 | -/-/-/-/-/- | - | OK-PRIOR |
| O7_PC12 | `profit O7 * pct>=0.3 pulled_mult>=10 secs_fav<=5 take win=3 persist=3 wall_ticks=8` | 184 | 4/4/2 | 1/0/3 | -109 / -275 | - / - / - | -/-/-/-/-/- | - | nan |
| O7_PC08 | `profit O7 * pct>=0.3 pulled_mult>=10 secs_fav<=2 take win=10 persist=5 wall_ticks=8` | 223 | 4/4/2 | 3/-1/1 | -103 / -266 | - / - / - | -/-/-/-/-/- | - | nan |
| O7_PC13 | `profit O7 * pct>=0.4 pulled_mult>=30 secs_fav<=2 take win=15 persist=1 wall_ticks=8` | 150 | 4/4/2 | 2/2/0 | -121 / -136 | - / - / - | -/-/-/-/-/- | - | nan |
| O7_PC15 | `profit O7 * pct>=0.3 pulled_mult>=3 secs_fav<=2 take win=10 persist=5 wall_ticks=8` | 283 | 4/4/2 | 3/1/2 | -108 / -455 | - / - / - | -/-/-/-/-/- | - | nan |
| O7_17 | `profit O7 * pct>=0.2 wall_ahead_mult>=5 lock 10 win=0 persist=1 wall_ticks=4` | 186 | 3/3/1 | 2/-1/6 | 118 / -312 | 0.89 / 1.00 / 22 | -/-/-/-/-/- | - | OK-PRIOR |

Placebo (random exit at the same pct, same count) and family null over the profit set (SZ-IJK ptr_null): #1 own p 0.98 / family p 1.00; #2 own p 1.00 / family p 1.00; #3 own p 0.94 / family p 1.00; #4 own p 0.97 / family p 1.00; #5 own p 1.00 / family p 1.00

Family null over the WHOLE profit set of O7 (SZ-IJK, stage 1+2 cells with >= 20 fires, B=100, slip 1.2, bucketed placebo = approximation): 201 of 5942 cells have family p < .05 (3.4%; around 5% is what the null alone gives); cells with own p < .05: 408 (expected by chance 297); the best single lines reach the B=100 floor (p about 0.01), use for ranking only.

Slip sensitivity of the best line `profit O7 * pct>=0.3 delta_mult>=2 take win=10 persist=10 wall_ticks=8` (first-order, stack cut % / d mean $/wk):

| slip pts | cut L6M | cut L3M | cut L1M | cut HOLD | cut PRE | cut X' | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|---|---|
| 0.57 | 5 | 5 | 2 | 2 | -1 | 3 | 31 | -442 |
| 0.80 | 5 | 5 | 2 | 1 | -1 | 3 | 26 | -448 |
| 1.20 | 5 | 5 | 2 | 1 | -1 | 3 | 218 | -459 |
| 1.60 | 5 | 5 | 2 | 1 | -1 | 3 | 209 | -469 |

By window (best line, slip 1.2, first-order): L1M cut 2 / d mean 408; L3M cut 5 / d mean 447; L6M cut 5 / d mean 218; HOLD cut 1 / d mean -45; PRE cut -1 / d mean -459; X' cut 3 / d mean 4. The held-out live week (11-01..05) sits inside L1M, a trending week: P7 carried about $159k of Targets that week, so any rule that exits winners early pays for itself only in the choppy weeks of the history; the single-week replay (REDO-R13: autopilot/R13_TRAIL_LIVE_REPLAY_BOOKS.md) and the 43-month first-order table are different regimes and are both shown, not averaged.

By entry session (the same line applied to one session only; stack effect): 

| session | trades | fires | cut L6M | cut PRE | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|
| nyam | 341 | 255 | 5 | -1 | 218 | -459 |
