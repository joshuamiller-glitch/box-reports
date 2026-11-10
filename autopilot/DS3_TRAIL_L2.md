# DS3_TRAIL_L2 - profit-state engine on the live panel base: per-book profit lines, 2026-11-10 18:29Z (screen + exact so far)

STATUS: Shadow only, post-hoc, no PASS claims, PRE-PROOF. Prereg autopilot/TRAIL_L2_PREREG.md (sha in DECISIONS.md); engine autopilot/PTR_ENGINE_API.md (code/th_ptr). Base = LPB_BASE exact trade list (live panel: P7 day cap 8,400 loss, P7 7/4/4, P7 cut 40/5x/w5/p3), ROLL-fixed engine; the "v2.5 near-target retargets" are not a separate switch in the engine on the box (no spec found) and are NOT in these runs. **Rows are FIRST-ORDER SCREENS (cached 1-s feature paths, slip 1.2 central) unless marked EXACT**; first-order vs exact: about 26-28% of the fires of a line differ between them (SZ-IJK PTR_T1 check: re-entries and path divergence), so first-order winners are screens, exact decides. Equal lots; stack maxDD (all weeks) cuts vs the live panel base, mean change with the carrying week dropped; recents first (L6M / L3M / L1M), rule 2a (floor = 25% of the live PRE mean) via Z.prior_info; market-exit slip cases central 1.2 / low 0.57 / high 1.6 pts (REDO-R9, vs the fill-second mid; decision at the close of second s and exit at row s+1 is the second-delay frame, no extra delay added) and the engine 0.80 for exact continuity.

## 0. Summary: best line per book

| book | best line (basis) | four-window cut (FO: L6M/HOLD/PRE/X') | EXACT cut L6M/L3M/L1M/HOLD/PRE/X', d mean L6M | live week: Targets clipped / cost, give-backs caught / saved | plain sentence |
|---|---|---|---|---|---|
| K7 | `profit K7 * pct>=0.4 dd>=3 lock 0 persist=5` (EXACT L6M (5 of the top-20 exact so far)) | 32/-2/-7/15 | 37/37/13/-/-/-, 1212 | 6/31 clipped (-11209$), 12/13 give-backs caught (10671$), net -1106$ | K7: the book-based protection is `profit K7 * pct>=0.4 dd>=3 lock 0 persist=5`; it keeps 92% of the give-backs (12 of 13 caught) and costs 19% of the fills (6 of 31 live Targets clipped). |
| P7 | `profit P7 * pct>=0.2 pulled_mult>=50 tot_rel_slow>=1.2 take win=15 persist=1` (EXACT L6M (4 of the top-20 exact so far)) | 62/15/-24/1 | 24/24/62/-/-/-, -1376 | 17/28 clipped (-61122$), 4/7 give-backs caught (20155$), net -23843$ | P7: the book-based protection is `profit P7 * pct>=0.2 pulled_mult>=50 tot_rel_slow>=1.2 take win=15 persist=1`; it keeps 57% of the give-backs (4 of 7 caught) and costs 61% of the fills (17 of 28 live Targets clipped). |
| M7 | `profit M7 * pct>=0.2 pulled_mult>=3 take win=5 persist=3 wall_ticks=8` (EXACT L6M (5 of the top-20 exact so far)) | 32/13/-2/-24 | 26/26/3/-/-/-, -781 | 13/13 clipped (-15026$), 4/4 give-backs caught (6159$), net -3055$ | M7: the book-based protection is `profit M7 * pct>=0.2 pulled_mult>=3 take win=5 persist=3 wall_ticks=8`; it keeps 100% of the give-backs (4 of 4 caught) and costs 100% of the fills (13 of 13 live Targets clipped). |
| U7 | `profit U7 * pct>=0.2 dd>=20 lock 10 persist=10` (FIRST-ORDER SCREEN (exact pending; placebo p_own 0.04, family p 0.63, WF2w 16%)) | 17/-4/16/-7 | pending | no live trade of this book with a path (replay n/a) | - |
| H7 | `profit H7 * pct>=0.3 pulled_mult>=20 secs_fav<=0 take win=10 persist=2` (EXACT L6M (5 of the top-20 exact so far)) | 9/-3/-3/0 | 11/11/0/-/-/-, -262 | no live trade of this book with a path (replay n/a) | - |
| A7 | `profit A7 * pct>=0.2 pulled_against_mult>=30 take win=10 persist=5 wall_ticks=8` (EXACT L6M (5 of the top-20 exact so far)) | 10/2/-2/-2 | 15/15/18/-/-/-, 961 | 7/7 clipped (-5046$), 3/4 give-backs caught (3075$), net 1099$ | A7: the book-based protection is `profit A7 * pct>=0.2 pulled_against_mult>=30 take win=10 persist=5 wall_ticks=8`; it keeps 75% of the give-backs (3 of 4 caught) and costs 100% of the fills (7 of 7 live Targets clipped). |
| O7 | `profit O7 * pct>=0.3 delta_mult>=2 take win=10 persist=10 wall_ticks=8` (EXACT L6M (5 of the top-20 exact so far)) | 5/1/-1/3 | 5/5/2/-/-/-, 30 | 1/1 clipped (-176$), 1/1 give-backs caught (1048$), net 872$ | O7: the book-based protection is `profit O7 * pct>=0.3 delta_mult>=2 take win=10 persist=10 wall_ticks=8`; it keeps 100% of the give-backs (1 of 1 caught) and costs 100% of the fills (1 of 1 live Targets clipped). |

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
| K7 | `profit K7 * pct>=0.4 dd>=3 lock 0 persist=5` | dd (points given back from the favourable extreme) as a condition; persist=<s> (consecutive seconds) |
| P7 | `profit P7 * pct>=0.2 pulled_mult>=50 tot_rel_slow>=1.2 take win=15 persist=1` | persist=<s> (consecutive seconds); slow half-hour baseline for tot_rel / ahead_rel; win=<s> (feature window) |
| M7 | `profit M7 * pct>=0.2 pulled_mult>=3 take win=5 persist=3 wall_ticks=8` | persist=<s> (consecutive seconds); win=<s> (feature window) |
| U7 | `profit U7 * pct>=0.2 dd>=20 lock 10 persist=10` | dd (points given back from the favourable extreme) as a condition; persist=<s> (consecutive seconds) |
| H7 | `profit H7 * pct>=0.3 pulled_mult>=20 secs_fav<=0 take win=10 persist=2` | persist=<s> (consecutive seconds); secs_fav (seconds since the FAVOURABLE extreme; v1.5 has secs_ext = adverse); win=<s> (feature window) |
| A7 | `profit A7 * pct>=0.2 pulled_against_mult>=30 take win=10 persist=5 wall_ticks=8` | persist=<s> (consecutive seconds); pulled_against_mult (OTHER side cancelled / MedLevel); win=<s> (feature window) |
| O7 | `profit O7 * pct>=0.3 delta_mult>=2 take win=10 persist=10 wall_ticks=8` | delta_mult (aggressor delta against / MedLevel over win); persist=<s> (consecutive seconds); win=<s> (feature window) |

v1.7 profit state engine (grammar of the order): one evaluation per exchange second on the 1-s top-10 state, decision at the close of second s, market exit at the next print; features pct, secs_fav, pulled_mult, pulled_against_mult, wall_ahead_mult (wall_ticks), ice_against, imb5/imb10, delta_mult, tot_rel, ahead_rel, sweep_against, dd; actions take / tighten X (ratchet in favour only) / lock X / step X / scale F; modifiers win=, persist=; AND / OR between two conditions.

## K7 (5627 trades with a path; no-rule = LPB_BASE reference row: cut 0 by definition)

First-order top-20 by the recents key (mean equal-mean cut on L6M/L3M/L1M), at most 4 per family and a cap per action; exact columns are the stack maxDD cut vs LPB_BASE (engine slip 0.80) where the PTR_ set has run:

| # | line | fires | FO cut L6M/L3M/L1M | FO cut HOLD/PRE/X' | FO d mean L6M / PRE | placebo p / family p / WF2w % | EXACT cut L6M/L3M/L1M/HOLD/PRE/X' | EXACT d mean L6M | rule 2a (FO) |
|---|---|---|---|---|---|---|---|---|---|
| 1 | `profit K7 * pct>=0.4 dd>=3 lock 0 persist=5` | 2060 | 32/32/14 | -2/-7/15 | 1266 / -1147 | 0.74 / 1.00 / 29 | 37/37/13/-/-/- | 1212 | OK-PRIOR |
| 2 | `profit K7 * pct>=0.3 delta_mult>=5 lock 0 win=10 persist=10` | 2115 | 33/33/10 | 5/-2/10 | 1542 / -1045 | 0.41 / 1.00 / 46 | 32/32/-2/-/-/- | -435 | OK-PRIOR |
| 3 | `profit K7 * pct>=0.4 dd>=5 lock 0 persist=5` | 1865 | 34/34/9 | 2/-2/10 | 1213 / -741 | 0.64 / 1.00 / 41 | 35/35/13/-/-/- | 208 | OK-PRIOR |
| 4 | `profit K7 * pct>=0.5 sweep_against>=2 lock 0 win=15 persist=3` | 1847 | 33/33/9 | 0/-6/10 | 1114 / -787 | 0.63 / 1.00 / 33 | 31/31/13/-/-/- | 69 | OK-PRIOR |
| 5 | `profit K7 * pct>=0.5 pulled_against_mult>=3 tighten 30 win=5 persist=3` | 2397 | 32/32/13 | 3/-2/16 | 812 / -1141 | 0.41 / 1.00 / 33 | 30/30/22/-/-/- | 853 | OK-PRIOR |
| 6 | `profit K7 * pct>=0.5 tot_rel_slow>=1.2 tighten 30 persist=1` | 2167 | 35/35/13 | 3/-9/9 | 226 / -1215 | 0.80 / 1.00 / 32 | -/-/-/-/-/- | - | OK-PRIOR |
| 7 | `profit K7 * pct>=0.4 delta_mult>=10 tighten 30 win=15 persist=10` | 1756 | 28/28/12 | -3/1/7 | 1546 / -857 | 0.40 / 1.00 / 32 | -/-/-/-/-/- | - | OK-PRIOR |
| 8 | `profit K7 * pct>=0.6 pulled_against_mult>=10 tighten 30 win=3 persist=2` | 1537 | 29/29/13 | -1/13/6 | 1121 / -477 | 0.03 / 0.56 / 34 | -/-/-/-/-/- | - | OK-PRIOR |
| 9 | `profit K7 * pct>=0.3 delta_mult>=5 tighten 30 win=10 persist=10` | 2605 | 30/30/11 | 7/0/15 | 1172 / -1282 | 0.35 / 1.00 / 61 | -/-/-/-/-/- | - | OK-PRIOR |
| 10 | `profit K7 * pct>=0.5 tot_rel_slow>=1.2 step 20 persist=1` | 2163 | 39/39/8 | 3/-11/12 | -190 / -1278 | 0.85 / 1.00 / 35 | -/-/-/-/-/- | - | OK-PRIOR |
| 11 | `profit K7 * pct>=0.4 dd>=3 step 20 persist=5` | 2584 | 35/35/13 | 1/-5/21 | -133 / -1530 | 0.66 / 1.00 / 39 | -/-/-/-/-/- | - | OK-PRIOR |
| 12 | `profit K7 * pct>=0.4 delta_mult>=5 step 20 win=15 persist=10` | 2201 | 36/36/5 | 2/4/22 | 270 / -1040 | 0.25 / 0.99 / 44 | -/-/-/-/-/- | - | OK-PRIOR |
| 13 | `profit K7 * pct>=0.2 dd>=20 pulled_mult>=20 take win=10 persist=10` | 1668 | 31/31/9 | -1/5/-8 | 366 / -780 | 0.14 / 0.94 / 25 | -/-/-/-/-/- | - | OK-PRIOR |
| 14 | `profit K7 * pct>=0.3 dd>=16 or imb10<=-0.1 take persist=10` | 3757 | 27/27/11 | 7/-12/13 | 586 / -2491 | 0.85 / 1.00 / 42 | -/-/-/-/-/- | - | OK-PRIOR |
| 15 | `profit K7 * pct>=0.2 dd>=20 delta_mult>=2 take win=10 persist=10` | 2306 | 28/28/12 | 5/-1/16 | -100 / -925 | 0.35 / 1.00 / 30 | -/-/-/-/-/- | - | OK-PRIOR |
| 16 | `profit K7 * pct>=0.2 dd>=20 pulled_against_mult>=20 take win=5 persist=2` | 1458 | 28/28/6 | 6/6/0 | 157 / -1123 | 0.12 / 0.85 / 30 | -/-/-/-/-/- | - | OK-PRIOR |
| 17 | `profit K7 * pct>=0.2 dd>=20 sweep_against>=6 take win=8 persist=5` | 2566 | 30/30/6 | 4/9/12 | -456 / -1086 | 0.04 / 0.64 / 34 | -/-/-/-/-/- | - | OK-PRIOR |
| 18 | `profit K7 * pct>=0.2 dd>=20 or imb10<=-0.1 take persist=10` | 4082 | 23/23/13 | 9/-10/8 | 79 / -2308 | 0.55 / 1.00 / 49 | -/-/-/-/-/- | - | OK-PRIOR |
| 19 | `profit K7 * pct>=0.5 dd>=5 scale 0.75 persist=2` | 3844 | 10/10/7 | 1/2/4 | 770 / -278 | 0.67 / 1.00 / 27 | -/-/-/-/-/- | - | OK-PRIOR |
| 20 | `profit K7 * pct>=0.5 pulled_mult>=20 scale 0.75 win=10 persist=5` | 3437 | 10/10/7 | 1/-1/2 | 668 / -132 | 0.59 / 1.00 / 18 | -/-/-/-/-/- | - | OK-PRIOR |

Bi-weekly re-pick WF over the whole stage-1/2/3 cell set of K7 (first-order, slip 1.2): OOS maxDD cut 7.7%, OOS mean delta -2022 $/wk, pick beats live in 57% of 74 refits (the pick switches every refit: it prefers whichever cell removes the most exposure; read the mean delta).

Placebo (random exit at the same pct, same count) and family null over the profit set (SZ-IJK ptr_null): #1 own p 0.74 / family p 1.00; #2 own p 0.41 / family p 1.00; #3 own p 0.64 / family p 1.00; #4 own p 0.63 / family p 1.00; #5 own p 0.41 / family p 1.00

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

Slip sensitivity of the best line `profit K7 * pct>=0.4 dd>=3 lock 0 persist=5` (first-order, stack cut % / d mean $/wk):

| slip pts | cut L6M | cut L3M | cut L1M | cut HOLD | cut PRE | cut X' | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|---|---|
| 0.57 | 33 | 33 | 15 | -1 | -6 | 16 | 1527 | -997 |
| 0.80 | 33 | 33 | 15 | -1 | -7 | 16 | 1432 | -1052 |
| 1.20 | 32 | 32 | 14 | -2 | -7 | 15 | 1266 | -1147 |
| 1.60 | 32 | 32 | 14 | -2 | -8 | 14 | 1101 | -1241 |

By entry session (the same line applied to one session only; stack effect): 

| session | trades | fires | cut L6M | cut PRE | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|
| asia | 1893 | 708 | 14 | -14 | 391 | -463 |
| london | 1378 | 524 | 10 | -2 | -34 | -388 |
| nyam | 1301 | 473 | 1 | 6 | 283 | -320 |
| nypm | 1055 | 355 | 7 | 4 | 107 | -167 |

## P7 (3937 trades with a path; no-rule = LPB_BASE reference row: cut 0 by definition)

First-order top-20 by the recents key (mean equal-mean cut on L6M/L3M/L1M), at most 4 per family and a cap per action; exact columns are the stack maxDD cut vs LPB_BASE (engine slip 0.80) where the PTR_ set has run:

| # | line | fires | FO cut L6M/L3M/L1M | FO cut HOLD/PRE/X' | FO d mean L6M / PRE | placebo p / family p / WF2w % | EXACT cut L6M/L3M/L1M/HOLD/PRE/X' | EXACT d mean L6M | rule 2a (FO) |
|---|---|---|---|---|---|---|---|---|---|
| 1 | `profit P7 * pct>=0.2 pulled_mult>=50 tot_rel_slow>=1.2 take win=15 persist=1` | 994 | 62/62/66 | 15/-24/1 | -374 / -854 | 0.95 / 1.00 / 16 | 24/24/62/-/-/- | -1376 | RECENT-ONLY |
| 2 | `profit P7 * pct>=0.3 pulled_against_mult>=5 tighten 5 win=5 persist=10` | 3217 | 65/65/61 | -6/22/25 | -1172 / -1172 | 0.01 / 0.04 / 58 | 17/17/18/-/-/- | -6486 | OK-PRIOR |
| 3 | `profit P7 * pct>=0.3 pulled_against_mult>=5 step 5 win=5 persist=10` | 3170 | 62/71/62 | -1/19/29 | -1932 / -1189 | 0.01 / 0.19 / 58 | 10/25/17/-/-/- | -6748 | OK-PRIOR |
| 4 | `profit P7 * pct>=0.3 pulled_against_mult>=20 tighten 5 win=8 persist=3` | 2949 | 67/67/54 | 20/15/22 | -1160 / -1011 | 0.04 / 0.63 / 62 | 19/19/15/-/-/- | -6667 | OK-PRIOR |
| 5 | `profit P7 * pct>=0.3 pulled_against_mult>=30 tighten 5 win=15 persist=5` | 2848 | 65/65/55 | 24/22/16 | -741 / -980 | 0.02 / 0.23 / 70 | -/-/-/-/-/- | - | OK-PRIOR |
| 6 | `profit P7 * pct>=0.2 pulled_mult>=50 tighten 8 win=15 persist=2` | 1610 | 64/64/50 | -10/-14/-0 | -331 / -202 | 0.86 / 1.00 / 44 | -/-/-/-/-/- | - | OK-PRIOR |
| 7 | `profit P7 * pct>=0.2 sweep_against>=3 tighten 5 win=3 persist=10` | 2778 | 59/59/50 | 12/12/45 | 989 / -1432 | 0.46 / 1.00 / 58 | -/-/-/-/-/- | - | OK-PRIOR |
| 8 | `profit P7 * pct>=0.3 pulled_mult>=5 secs_fav<=0 take win=3 persist=1` | 2411 | 55/55/59 | 3/-8/42 | 722 / 773 | 0.62 / 1.00 / 39 | -/-/-/-/-/- | - | OK-PRIOR |
| 9 | `profit P7 * pct>=0.2 pulled_mult>=50 dd>=8 take win=15 persist=1` | 1617 | 60/60/64 | -4/-9/-5 | -1691 / -777 | 0.81 / 1.00 / 39 | -/-/-/-/-/- | - | OK-PRIOR |
| 10 | `profit P7 * pct>=0.2 pulled_mult>=50 step 5 win=15 persist=2` | 1618 | 62/62/54 | -12/-14/-2 | -505 / -330 | 0.85 / 1.00 / 44 | -/-/-/-/-/- | - | OK-PRIOR |
| 11 | `profit P7 * pct>=0.2 pulled_mult>=20 step 5 win=3 persist=1` | 1959 | 56/56/71 | 8/7/15 | -1469 / -904 | 0.44 / 1.00 / 58 | -/-/-/-/-/- | - | OK-PRIOR |
| 12 | `profit P7 * pct>=0.2 pulled_mult>=20 sweep_against>=3 take win=3 persist=1` | 1943 | 55/55/69 | 7/4/18 | -909 / -855 | 0.58 / 1.00 / 59 | -/-/-/-/-/- | - | OK-PRIOR |
| 13 | `profit P7 * pct>=0.2 pulled_mult>=20 lock 10 win=5 persist=5` | 1051 | 61/61/43 | 7/3/14 | 1525 / -960 | 0.53 / 1.00 / 54 | -/-/-/-/-/- | - | OK-PRIOR |
| 14 | `profit P7 * pct>=0.3 pulled_against_mult>=20 ice_against>=1 take win=8 persist=2` | 2407 | 57/57/50 | 39/-0/21 | 966 / -464 | 0.41 / 1.00 / 65 | -/-/-/-/-/- | - | OK-PRIOR |
| 15 | `profit P7 * pct>=0.3 pulled_mult>=10 secs_fav<=0 take win=5 persist=1` | 1793 | 62/62/43 | 18/5/10 | 10 / 876 | 0.26 / 1.00 / 41 | -/-/-/-/-/- | - | OK-PRIOR |
| 16 | `profit P7 * pct>=0.2 sweep_against>=2 lock 5 win=2 persist=10` | 1468 | 52/52/43 | -13/0/-4 | 959 / -1343 | 0.57 / 1.00 / 28 | -/-/-/-/-/- | - | OK-PRIOR |
| 17 | `profit P7 * pct>=0.2 sweep_against>=3 lock 5 win=3 persist=10` | 1820 | 46/46/53 | -7/9/28 | 938 / -2072 | 0.36 / 1.00 / 48 | -/-/-/-/-/- | - | OK-PRIOR |
| 18 | `profit P7 * pct>=0.2 sweep_against>=3 lock 10 win=3 persist=10` | 2004 | 52/52/38 | -1/2/38 | 489 / -2205 | 0.57 / 1.00 / 47 | -/-/-/-/-/- | - | OK-PRIOR |
| 19 | `profit P7 * pct>=0.2 dd>=8 scale 0.75 persist=1` | 3373 | 44/44/32 | 17/9/30 | 817 / -881 | 0.65 / 1.00 / 73 | -/-/-/-/-/- | - | OK-PRIOR |
| 20 | `profit P7 * pct>=0.2 delta_mult>=5 scale 0.75 win=3 persist=5` | 1587 | 36/36/32 | 22/11/19 | 2795 / -94 | 0.33 / 1.00 / 61 | -/-/-/-/-/- | - | OK-PRIOR |

Bi-weekly re-pick WF over the whole stage-1/2/3 cell set of P7 (first-order, slip 1.2): OOS maxDD cut 25.5%, OOS mean delta -4453 $/wk, pick beats live in 82% of 74 refits (the pick switches every refit: it prefers whichever cell removes the most exposure; read the mean delta).

Placebo (random exit at the same pct, same count) and family null over the profit set (SZ-IJK ptr_null): #1 own p 0.95 / family p 1.00; #2 own p 0.01 / family p 0.04; #3 own p 0.01 / family p 0.19; #4 own p 0.04 / family p 0.63; #5 own p 0.02 / family p 0.23

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

Slip sensitivity of the best line `profit P7 * pct>=0.2 pulled_mult>=50 tot_rel_slow>=1.2 take win=15 persist=1` (first-order, stack cut % / d mean $/wk):

| slip pts | cut L6M | cut L3M | cut L1M | cut HOLD | cut PRE | cut X' | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|---|---|
| 0.57 | 64 | 64 | 68 | 17 | -23 | 2 | 336 | -694 |
| 0.80 | 63 | 63 | 67 | 16 | -23 | 2 | 77 | -753 |
| 1.20 | 62 | 62 | 66 | 15 | -24 | 1 | -374 | -854 |
| 1.60 | 61 | 61 | 65 | 15 | -24 | 1 | -826 | -956 |

By entry session (the same line applied to one session only; stack effect): 

| session | trades | fires | cut L6M | cut PRE | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|
| asia | 1768 | 460 | 32 | -17 | -485 | -193 |
| london | 1208 | 357 | 8 | -1 | -647 | -417 |
| nyam | 961 | 177 | 10 | -6 | 264 | 343 |

## M7 (3423 trades with a path; no-rule = LPB_BASE reference row: cut 0 by definition)

First-order top-20 by the recents key (mean equal-mean cut on L6M/L3M/L1M), at most 4 per family and a cap per action; exact columns are the stack maxDD cut vs LPB_BASE (engine slip 0.80) where the PTR_ set has run:

| # | line | fires | FO cut L6M/L3M/L1M | FO cut HOLD/PRE/X' | FO d mean L6M / PRE | placebo p / family p / WF2w % | EXACT cut L6M/L3M/L1M/HOLD/PRE/X' | EXACT d mean L6M | rule 2a (FO) |
|---|---|---|---|---|---|---|---|---|---|
| 1 | `profit M7 * pct>=0.2 sweep_against>=3 take win=8 persist=2 wall_ticks=8` | 3349 | 33/33/10 | 17/-2/-24 | -636 / -674 | - / - / - | 25/25/2/-/-/- | -1583 | - |
| 2 | `profit M7 * pct>=0.2 pulled_mult>=3 take win=5 persist=3 wall_ticks=8` | 3320 | 32/32/11 | 13/-2/-24 | -521 / -694 | - / - / - | 26/26/3/-/-/- | -781 | - |
| 3 | `profit M7 * pct>=0.2 pulled_mult>=3 tighten 5 win=5 persist=3 wall_ticks=8` | 3312 | 32/32/12 | 12/-5/-25 | -520 / -760 | - / - / - | 27/27/4/-/-/- | -1318 | - |
| 4 | `profit M7 * pct>=0.2 sweep_against>=4 take win=8 persist=2 wall_ticks=8` | 3323 | 32/32/11 | 17/-1/-23 | -630 / -662 | - / - / - | 25/25/3/-/-/- | -799 | - |
| 5 | `profit M7 * pct>=0.2 pulled_against_mult>=10 take win=5 persist=2 wall_ticks=8` | 3304 | 32/32/10 | 17/-1/-19 | -627 / -630 | - / - / - | 27/27/3/-/-/- | -1420 | - |
| 6 | `profit M7 * pct>=0.2 pulled_against_mult>=20 tighten 5 win=15 persist=2 wall_ticks=8` | 3307 | 31/31/10 | 14/-5/-23 | -656 / -793 | - / - / - | -/-/-/-/-/- | - | - |
| 7 | `profit M7 * pct>=0.2 imb10<=-0.1 tighten 5 win=0 persist=1 wall_ticks=8` | 3347 | 30/30/12 | 16/-3/-25 | -603 / -818 | - / - / - | -/-/-/-/-/- | - | - |
| 8 | `profit M7 * pct>=0.2 imb5<=-0.1 take win=0 persist=2 wall_ticks=8` | 3261 | 30/30/9 | 15/-0/-24 | -614 / -570 | - / - / - | -/-/-/-/-/- | - | - |
| 9 | `profit M7 * pct>=0.6 ice_against>=1 tighten 20 win=30 persist=1 wall_ticks=8` | 1263 | 15/15/8 | 9/-14/-9 | 528 / -1085 | - / - / - | -/-/-/-/-/- | - | - |
| 10 | `profit M7 * pct>=0.5 dd>=3 step 20 win=0 persist=5 wall_ticks=8` | 1250 | 13/13/14 | 9/-2/-15 | 261 / -617 | - / - / - | -/-/-/-/-/- | - | - |
| 11 | `profit M7 * pct>=0.6 ice_against>=1 tighten 20 win=30 persist=2 wall_ticks=8` | 1235 | 15/15/6 | 9/-14/-8 | 396 / -1087 | - / - / - | -/-/-/-/-/- | - | - |
| 12 | `profit M7 * pct>=0.5 dd>=5 take win=0 persist=1 wall_ticks=8` | 2289 | 13/13/12 | 8/5/-20 | 158 / -755 | - / - / - | -/-/-/-/-/- | - | - |
| 13 | `profit M7 * pct>=0.2 imb5<=-0.1 lock 5 win=0 persist=2 wall_ticks=8` | 2588 | 26/26/3 | 14/-3/-27 | -81 / -302 | - / - / - | -/-/-/-/-/- | - | - |
| 14 | `profit M7 * pct>=0.2 imb10<=-0.1 lock 10 win=0 persist=3 wall_ticks=8` | 2604 | 24/24/11 | 12/-2/-24 | 439 / -409 | - / - / - | -/-/-/-/-/- | - | - |
| 15 | `profit M7 * pct>=0.2 ahead_rel_slow>=1.5 lock 10 win=0 persist=1 wall_ticks=8` | 2540 | 22/22/11 | 10/-5/-28 | 201 / -894 | - / - / - | -/-/-/-/-/- | - | - |
| 16 | `profit M7 * pct>=0.2 ahead_rel>=1.5 lock 10 win=0 persist=1 wall_ticks=8` | 2638 | 21/21/13 | 11/-4/-23 | 167 / -800 | - / - / - | -/-/-/-/-/- | - | - |
| 17 | `profit M7 * pct>=0.2 sweep_against>=3 tighten 5 win=8 persist=2 wall_ticks=8` | 3342 | 32/32/10 | 15/-4/-25 | -592 / -779 | - / - / - | -/-/-/-/-/- | - | - |
| 18 | `profit M7 * pct>=0.2 sweep_against>=3 lock 10 win=8 persist=2 wall_ticks=8` | 3013 | 29/29/9 | 14/-2/-24 | -686 / -453 | - / - / - | -/-/-/-/-/- | - | - |
| 19 | `profit M7 * pct>=0.2 pulled_mult>=3 step 5 win=5 persist=3 wall_ticks=8` | 3299 | 31/31/12 | 12/-2/-25 | -741 / -754 | - / - / - | -/-/-/-/-/- | - | - |
| 20 | `profit M7 * pct>=0.2 sweep_against>=4 scale 0.5 win=8 persist=2 wall_ticks=8` | 3323 | 10/10/0 | 8/5/-3 | 77 / 5 | - / - / - | -/-/-/-/-/- | - | - |

Slip sensitivity of the best line `profit M7 * pct>=0.2 pulled_mult>=3 take win=5 persist=3 wall_ticks=8` (first-order, stack cut % / d mean $/wk):

| slip pts | cut L6M | cut L3M | cut L1M | cut HOLD | cut PRE | cut X' | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|---|---|
| 0.57 | 33 | 33 | 12 | 14 | -1 | -22 | -144 | -450 |
| 0.80 | 33 | 33 | 12 | 14 | -1 | -23 | -282 | -539 |
| 1.20 | 32 | 32 | 11 | 13 | -2 | -24 | -521 | -694 |
| 1.60 | 31 | 31 | 10 | 13 | -3 | -26 | -760 | -849 |

By entry session (the same line applied to one session only; stack effect): 

| session | trades | fires | cut L6M | cut PRE | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|
| london | 2058 | 2002 | 25 | -1 | 30 | -394 |
| nyam | 1365 | 1318 | 3 | -1 | -243 | -533 |

## U7 (1118 trades with a path; no-rule = LPB_BASE reference row: cut 0 by definition)

First-order top-20 by the recents key (mean equal-mean cut on L6M/L3M/L1M), at most 4 per family and a cap per action; exact columns are the stack maxDD cut vs LPB_BASE (engine slip 0.80) where the PTR_ set has run:

| # | line | fires | FO cut L6M/L3M/L1M | FO cut HOLD/PRE/X' | FO d mean L6M / PRE | placebo p / family p / WF2w % | EXACT cut L6M/L3M/L1M/HOLD/PRE/X' | EXACT d mean L6M | rule 2a (FO) |
|---|---|---|---|---|---|---|---|---|---|
| 1 | `profit U7 * pct>=0.3 pulled_against_mult>=20 ahead_rel_slow>=1.2 take win=5 persist=3` | 252 | 27/27/25 | -0/4/-10 | 1087 / -260 | 0.27 / 0.99 / 14 | -/-/-/-/-/- | - | OK-PRIOR |
| 2 | `profit U7 * pct>=0.3 pulled_against_mult>=20 tighten 20 win=5 persist=5` | 285 | 26/26/28 | -12/-0/-2 | 723 / -601 | 0.54 / 1.00 / 10 | -/-/-/-/-/- | - | OK-PRIOR |
| 3 | `profit U7 * pct>=0.3 pulled_against_mult>=20 step 5 win=5 persist=5` | 354 | 29/29/29 | -10/-1/-0 | 46 / -461 | 0.67 / 1.00 / 9 | -/-/-/-/-/- | - | OK-PRIOR |
| 4 | `profit U7 * pct>=0.3 pulled_against_mult>=20 take win=5 persist=5` | 375 | 29/29/27 | -10/-1/-0 | 40 / -455 | 0.62 / 1.00 / 10 | -/-/-/-/-/- | - | OK-PRIOR |
| 5 | `profit U7 * pct>=0.3 pulled_against_mult>=20 tighten 8 win=5 persist=5` | 353 | 29/29/27 | -9/-1/-0 | 51 / -484 | 0.52 / 1.00 / 9 | -/-/-/-/-/- | - | OK-PRIOR |
| 6 | `profit U7 * pct>=0.3 delta_mult>=30 step 5 win=15 persist=1` | 369 | 25/25/16 | -9/2/1 | 1694 / -17 | 0.53 / 1.00 / 22 | -/-/-/-/-/- | - | OK-PRIOR |
| 7 | `profit U7 * pct>=0.4 delta_mult>=20 step 5 win=15 persist=5` | 399 | 28/28/10 | -7/5/6 | 1608 / -564 | 0.32 / 1.00 / 25 | -/-/-/-/-/- | - | OK-PRIOR |
| 8 | `profit U7 * pct>=0.3 delta_mult>=30 take win=15 persist=1` | 376 | 23/23/17 | -9/1/2 | 1663 / -2 | 0.54 / 1.00 / 22 | -/-/-/-/-/- | - | OK-PRIOR |
| 9 | `profit U7 * pct>=0.3 delta_mult>=30 tighten 8 win=15 persist=1` | 369 | 25/25/16 | -9/2/1 | 1653 / -14 | 0.55 / 1.00 / 22 | -/-/-/-/-/- | - | OK-PRIOR |
| 10 | `profit U7 * pct>=0.2 pulled_against_mult>=30 imb5<=-0.3 take win=8 persist=1` | 425 | 26/26/25 | -5/1/-3 | 326 / -202 | 0.56 / 1.00 / 16 | -/-/-/-/-/- | - | OK-PRIOR |
| 11 | `profit U7 * pct>=0.3 pulled_against_mult>=20 ahead_rel>=1.2 take win=5 persist=3` | 251 | 25/25/24 | -2/4/-7 | 341 / -253 | 0.30 / 1.00 / 13 | -/-/-/-/-/- | - | OK-PRIOR |
| 12 | `profit U7 * pct>=0.2 pulled_mult>=5 secs_fav<=0 take win=5 persist=3` | 427 | 29/29/26 | -4/9/9 | -999 / -555 | 0.11 / 0.87 / 18 | -/-/-/-/-/- | - | OK-PRIOR |
| 13 | `profit U7 * pct>=0.2 pulled_against_mult>=30 imb5<=-0.3 tighten 16 win=8 persist=1` | 370 | 25/25/19 | -6/1/-3 | 364 / -139 | 0.52 / 1.00 / 18 | -/-/-/-/-/- | - | OK-PRIOR |
| 14 | `profit U7 * pct>=0.4 tot_rel_slow>=1.5 tighten 20 persist=2` | 549 | 23/23/17 | 3/7/1 | 426 / -774 | 0.29 / 0.99 / 34 | -/-/-/-/-/- | - | OK-PRIOR |
| 15 | `profit U7 * pct>=0.2 wall_ahead_mult>=10 lock 10 persist=2 wall_ticks=2` | 289 | 18/18/5 | -10/-2/-17 | 946 / -550 | 0.75 / 1.00 / 8 | -/-/-/-/-/- | - | OK-PRIOR |
| 16 | `profit U7 * pct>=0.2 wall_ahead_mult>=10 lock 0 persist=2 wall_ticks=2` | 244 | 15/15/5 | -13/-2/-25 | 1327 / -545 | 0.66 / 1.00 / 11 | -/-/-/-/-/- | - | OK-PRIOR |
| 17 | `profit U7 * pct>=0.2 dd>=20 lock 10 persist=10` | 423 | 17/17/6 | -4/16/-7 | 824 / -660 | 0.04 / 0.63 / 16 | -/-/-/-/-/- | - | OK-PRIOR |
| 18 | `profit U7 * pct>=0.3 wall_ahead_mult>=10 lock 0 persist=2 wall_ticks=2` | 171 | 15/15/5 | -6/-1/-6 | 1135 / -391 | 0.61 / 1.00 / 9 | -/-/-/-/-/- | - | OK-PRIOR |
| 19 | `profit U7 * pct>=0.6 pulled_mult>=30 scale 0.75 win=8 persist=2` | 298 | 13/13/3 | -6/5/-1 | 803 / -137 | 0.48 / 1.00 / 11 | -/-/-/-/-/- | - | OK-PRIOR |
| 20 | `profit U7 * pct>=0.3 dd>=20 scale 0.75 persist=10` | 457 | 14/14/1 | -7/8/-10 | 788 / -346 | 0.15 / 0.90 / 19 | -/-/-/-/-/- | - | OK-PRIOR |

Placebo (random exit at the same pct, same count) and family null over the profit set (SZ-IJK ptr_null): #1 own p 0.27 / family p 0.99; #2 own p 0.54 / family p 1.00; #3 own p 0.67 / family p 1.00; #4 own p 0.62 / family p 1.00; #5 own p 0.52 / family p 1.00

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

Slip sensitivity of the best line `profit U7 * pct>=0.2 dd>=20 lock 10 persist=10` (first-order, stack cut % / d mean $/wk):

| slip pts | cut L6M | cut L3M | cut L1M | cut HOLD | cut PRE | cut X' | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|---|---|
| 0.57 | 18 | 18 | 6 | -4 | 16 | -7 | 922 | -588 |
| 0.80 | 17 | 17 | 6 | -4 | 16 | -7 | 886 | -614 |
| 1.20 | 17 | 17 | 6 | -4 | 16 | -7 | 824 | -660 |
| 1.60 | 17 | 17 | 6 | -4 | 16 | -8 | 762 | -706 |

By entry session (the same line applied to one session only; stack effect): 

| session | trades | fires | cut L6M | cut PRE | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|
| asia | 567 | 227 | 13 | 2 | 736 | -610 |
| london | 551 | 196 | 4 | 15 | -206 | -146 |

## H7 (881 trades with a path; no-rule = LPB_BASE reference row: cut 0 by definition)

First-order top-20 by the recents key (mean equal-mean cut on L6M/L3M/L1M), at most 4 per family and a cap per action; exact columns are the stack maxDD cut vs LPB_BASE (engine slip 0.80) where the PTR_ set has run:

| # | line | fires | FO cut L6M/L3M/L1M | FO cut HOLD/PRE/X' | FO d mean L6M / PRE | placebo p / family p / WF2w % | EXACT cut L6M/L3M/L1M/HOLD/PRE/X' | EXACT d mean L6M | rule 2a (FO) |
|---|---|---|---|---|---|---|---|---|---|
| 1 | `profit H7 * pct>=0.4 dd>=20 or ice_against>=3 take persist=5` | 463 | 10/10/0 | 3/2/17 | 597 / -394 | 0.04 / 0.38 / 34 | 5/5/0/-/-/- | 367 | OK-PRIOR |
| 2 | `profit H7 * pct>=0.4 dd>=20 or ice_against>=3 tighten 16 persist=5` | 396 | 9/9/0 | 3/2/16 | 516 / -355 | 0.04 / 0.55 / 33 | 4/4/0/-/-/- | 286 | OK-PRIOR |
| 3 | `profit H7 * pct>=0.3 pulled_mult>=20 secs_fav<=0 take win=10 persist=2` | 138 | 9/9/-0 | -3/-3/0 | 228 / -295 | 0.47 / 1.00 / 3 | 11/11/0/-/-/- | -262 | OK-PRIOR |
| 4 | `profit H7 * pct>=0.2 ice_against>=3 or pulled_mult>=30 take win=5 persist=3` | 516 | 7/7/4 | -3/2/11 | 245 / -578 | 0.26 / 1.00 / 23 | 7/7/4/-/-/- | 319 | OK-PRIOR |
| 5 | `profit H7 * pct>=0.5 dd>=16 tighten 20 persist=10` | 219 | 7/7/0 | -1/1/14 | 442 / -324 | 0.14 / 0.85 / 11 | 2/2/0/-/-/- | 189 | OK-PRIOR |
| 6 | `profit H7 * pct>=0.4 sweep_against>=8 tighten 5 win=5 persist=10` | 206 | 9/9/-2 | -1/-5/6 | 233 / -125 | 0.64 / 1.00 / 1 | -/-/-/-/-/- | - | OK-PRIOR |
| 7 | `profit H7 * pct>=0.4 sweep_against>=8 take win=5 persist=10` | 213 | 10/10/-2 | -1/-5/6 | 209 / -153 | 0.66 / 1.00 / 1 | -/-/-/-/-/- | - | OK-PRIOR |
| 8 | `profit H7 * pct>=0.4 sweep_against>=8 tighten 8 win=5 persist=10` | 200 | 9/9/-2 | -1/-5/6 | 222 / -135 | 0.77 / 1.00 / 1 | -/-/-/-/-/- | - | OK-PRIOR |
| 9 | `profit H7 * pct>=0.5 dd>=16 or sweep_against>=8 take win=3 persist=5` | 366 | 8/8/-2 | -2/-3/9 | 363 / -336 | 0.14 / 0.94 / 11 | -/-/-/-/-/- | - | OK-PRIOR |
| 10 | `profit H7 * pct>=0.4 sweep_against>=8 step 5 win=5 persist=10` | 200 | 9/9/-2 | -2/-5/6 | 232 / -126 | 0.75 / 1.00 / 1 | -/-/-/-/-/- | - | OK-PRIOR |
| 11 | `profit H7 * pct>=0.5 ice_against>=1 tighten 8 persist=3` | 585 | 8/8/-1 | 2/-9/6 | 284 / -620 | 0.40 / 1.00 / 32 | -/-/-/-/-/- | - | OK-PRIOR |
| 12 | `profit H7 * pct>=0.5 dd>=16 step 10 persist=10` | 231 | 6/6/0 | -1/1/15 | 408 / -253 | 0.11 / 0.85 / 15 | -/-/-/-/-/- | - | OK-PRIOR |
| 13 | `profit H7 * pct>=0.2 pulled_mult>=30 take win=8 persist=10` | 49 | 4/4/4 | -1/-1/0 | 331 / -133 | 0.52 / 1.00 / 3 | -/-/-/-/-/- | - | OK-PRIOR |
| 14 | `profit H7 * pct>=0.5 ice_against>=1 step 5 persist=3` | 594 | 7/7/-1 | 2/-9/6 | 309 / -649 | 0.36 / 1.00 / 32 | -/-/-/-/-/- | - | OK-PRIOR |
| 15 | `profit H7 * pct>=0.4 delta_mult>=10 lock 10 win=10 persist=10` | 200 | 6/6/0 | 2/-2/2 | 310 / -139 | 0.35 / 1.00 / 25 | -/-/-/-/-/- | - | OK-PRIOR |
| 16 | `profit H7 * pct>=0.4 delta_mult>=10 lock 5 win=10 persist=10` | 182 | 6/6/0 | 2/-3/6 | 265 / -160 | 0.41 / 1.00 / 22 | -/-/-/-/-/- | - | OK-PRIOR |
| 17 | `profit H7 * pct>=0.4 delta_mult>=10 lock 5 win=8 persist=3` | 279 | 10/10/-5 | 1/-1/10 | 107 / -349 | 0.17 / 0.96 / 24 | -/-/-/-/-/- | - | OK-PRIOR |
| 18 | `profit H7 * pct>=0.4 delta_mult>=10 lock 2 win=10 persist=10` | 172 | 6/6/0 | 2/-3/5 | 267 / -62 | 0.56 / 1.00 / 20 | -/-/-/-/-/- | - | OK-PRIOR |
| 19 | `profit H7 * pct>=0.2 pulled_mult>=30 scale 0.5 win=8 persist=10` | 49 | 2/2/2 | 0/0/0 | 125 / -50 | 0.36 / 1.00 / 0 | -/-/-/-/-/- | - | OK-PRIOR |
| 20 | `profit H7 * pct>=0.2 pulled_mult>=30 scale 0.75 win=5 persist=3` | 86 | 2/2/2 | -1/1/0 | 141 / -50 | 0.27 / 1.00 / 3 | -/-/-/-/-/- | - | OK-PRIOR |

Placebo (random exit at the same pct, same count) and family null over the profit set (SZ-IJK ptr_null): #1 own p 0.04 / family p 0.38; #2 own p 0.04 / family p 0.55; #3 own p 0.47 / family p 1.00; #4 own p 0.26 / family p 1.00; #5 own p 0.14 / family p 0.85

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

Slip sensitivity of the best line `profit H7 * pct>=0.3 pulled_mult>=20 secs_fav<=0 take win=10 persist=2` (first-order, stack cut % / d mean $/wk):

| slip pts | cut L6M | cut L3M | cut L1M | cut HOLD | cut PRE | cut X' | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|---|---|
| 0.57 | 10 | 10 | -0 | -3 | -3 | 0 | 274 | -282 |
| 0.80 | 9 | 9 | -0 | -3 | -3 | 0 | 258 | -287 |
| 1.20 | 9 | 9 | -0 | -3 | -3 | 0 | 228 | -295 |
| 1.60 | 9 | 9 | -0 | -3 | -3 | 0 | 199 | -303 |

By entry session (the same line applied to one session only; stack effect): 

| session | trades | fires | cut L6M | cut PRE | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|
| asia | 554 | 74 | 9 | -0 | -84 | -150 |
| nyam | 327 | 64 | 0 | -2 | -274 | -58 |

## A7 (956 trades with a path; no-rule = LPB_BASE reference row: cut 0 by definition)

First-order top-20 by the recents key (mean equal-mean cut on L6M/L3M/L1M), at most 4 per family and a cap per action; exact columns are the stack maxDD cut vs LPB_BASE (engine slip 0.80) where the PTR_ set has run:

| # | line | fires | FO cut L6M/L3M/L1M | FO cut HOLD/PRE/X' | FO d mean L6M / PRE | placebo p / family p / WF2w % | EXACT cut L6M/L3M/L1M/HOLD/PRE/X' | EXACT d mean L6M | rule 2a (FO) |
|---|---|---|---|---|---|---|---|---|---|
| 1 | `profit A7 * pct>=0.3 delta_mult>=2 tighten 5 win=2 persist=2 wall_ticks=8` | 872 | 10/10/4 | 2/2/-4 | -841 / -346 | - / - / - | 5/5/29/-/-/- | 320 | - |
| 2 | `profit A7 * pct>=0.3 pulled_against_mult>=30 or pulled_mult>=20 take win=10 persist=3 wall_ticks=8` | 811 | 10/10/2 | 2/2/-4 | -221 / -122 | - / - / - | 8/8/-1/-/-/- | -878 | - |
| 3 | `profit A7 * pct>=0.2 pulled_against_mult>=30 take win=10 persist=5 wall_ticks=8` | 571 | 10/10/3 | 2/-2/-2 | 206 / -198 | - / - / - | 15/15/18/-/-/- | 961 | - |
| 4 | `profit A7 * pct>=0.3 pulled_mult>=30 sweep_against>=6 take win=15 persist=1 wall_ticks=8` | 760 | 10/10/2 | 4/2/-0 | -237 / -128 | - / - / - | 5/5/18/-/-/- | -624 | - |
| 5 | `profit A7 * pct>=0.2 pulled_against_mult>=50 take win=15 persist=2 wall_ticks=8` | 438 | 10/10/0 | 3/-1/-1 | -289 / -92 | - / - / - | 6/6/20/-/-/- | 369 | - |
| 6 | `profit A7 * pct>=0.3 pulled_mult>=30 take win=15 persist=2 wall_ticks=8` | 772 | 10/10/2 | 4/0/-1 | -308 / -136 | - / - / - | -/-/-/-/-/- | - | - |
| 7 | `profit A7 * pct>=0.3 pulled_mult>=30 take win=15 persist=1 wall_ticks=8` | 784 | 10/10/2 | 4/2/-2 | -234 / -141 | - / - / - | -/-/-/-/-/- | - | - |
| 8 | `profit A7 * pct>=0.2 sweep_against>=6 step 10 win=5 persist=10 wall_ticks=8` | 552 | 9/9/5 | 3/1/-2 | 21 / -261 | - / - / - | -/-/-/-/-/- | - | - |
| 9 | `profit A7 * pct>=0.5 take` | 787 | 6/6/1 | 2/-0/-7 | -43 / -180 | - / - / - | -/-/-/-/-/- | - | - |
| 10 | `profit A7 * pct>=0.5 tighten 5` | 780 | 6/6/1 | 2/0/-6 | -369 / -209 | - / - / - | -/-/-/-/-/- | - | - |
| 11 | `profit A7 * pct>=0.5 wall_ahead_mult>=5 step 10 win=0 persist=3 wall_ticks=4` | 404 | 4/4/-2 | -0/-3/-4 | -629 / -381 | - / - / - | -/-/20/-/-/- | - | - |
| 12 | `profit A7 * pct>=0.5 wall_ahead_mult>=5 tighten 5 win=0 persist=3 wall_ticks=4` | 504 | 4/4/-1 | 0/-3/-4 | -586 / -338 | - / - / - | -/-/21/-/-/- | - | - |
| 13 | `profit A7 * pct>=0.2 sweep_against>=4 take win=8 persist=10 wall_ticks=8` | 912 | 9/9/6 | 3/-0/-1 | -89 / -405 | - / - / - | -/-/22/-/-/- | - | - |
| 14 | `profit A7 * pct>=0.3 delta_mult>=2 take win=5 persist=1 wall_ticks=8` | 893 | 9/9/2 | 3/1/-5 | -97 / -376 | - / - / - | -/-/2/-/-/- | - | - |
| 15 | `profit A7 * pct>=0.4 dd>=5 take win=0 persist=1 wall_ticks=8` | 787 | 6/6/4 | 2/-1/-4 | 49 / -251 | - / - / - | -/-/29/-/-/- | - | - |
| 16 | `profit A7 * pct>=0.4 dd>=5 tighten 5 win=0 persist=1 wall_ticks=8` | 787 | 6/6/4 | 2/-1/-4 | 49 / -251 | - / - / - | -/-/29/-/-/- | - | - |
| 17 | `profit A7 * pct>=0.2 pulled_against_mult>=30 tighten 5 win=10 persist=5 wall_ticks=8` | 564 | 10/10/3 | 2/-2/-2 | 135 / -194 | - / - / - | -/-/-/-/-/- | - | - |
| 18 | `profit A7 * pct>=0.2 sweep_against>=4 lock 10 win=8 persist=10 wall_ticks=8` | 759 | 7/7/7 | 2/-1/1 | -269 / -371 | - / - / - | -/-/-/-/-/- | - | - |
| 19 | `profit A7 * pct>=0.3 delta_mult>=2 step 5 win=2 persist=2 wall_ticks=8` | 867 | 9/9/3 | 2/2/-3 | -888 / -363 | - / - / - | -/-/-/-/-/- | - | - |
| 20 | `profit A7 * pct>=0.3 sweep_against>=6 pulled_mult>=10 take win=3 persist=1 wall_ticks=8` | 832 | 10/10/2 | 2/2/-5 | -206 / -184 | - / - / - | -/-/-/-/-/- | - | - |

Slip sensitivity of the best line `profit A7 * pct>=0.2 pulled_against_mult>=30 take win=10 persist=5 wall_ticks=8` (first-order, stack cut % / d mean $/wk):

| slip pts | cut L6M | cut L3M | cut L1M | cut HOLD | cut PRE | cut X' | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|---|---|
| 0.57 | 10 | 10 | 3 | 2 | -2 | -2 | 313 | -173 |
| 0.80 | 10 | 10 | 3 | 2 | -2 | -2 | 274 | -182 |
| 1.20 | 10 | 10 | 3 | 2 | -2 | -2 | 206 | -198 |
| 1.60 | 10 | 10 | 2 | 2 | -2 | -2 | 138 | -214 |

By entry session (the same line applied to one session only; stack effect): 

| session | trades | fires | cut L6M | cut PRE | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|
| asia | 956 | 571 | 10 | -2 | 206 | -198 |

## O7 (341 trades with a path; no-rule = LPB_BASE reference row: cut 0 by definition)

First-order top-20 by the recents key (mean equal-mean cut on L6M/L3M/L1M), at most 4 per family and a cap per action; exact columns are the stack maxDD cut vs LPB_BASE (engine slip 0.80) where the PTR_ set has run:

| # | line | fires | FO cut L6M/L3M/L1M | FO cut HOLD/PRE/X' | FO d mean L6M / PRE | placebo p / family p / WF2w % | EXACT cut L6M/L3M/L1M/HOLD/PRE/X' | EXACT d mean L6M | rule 2a (FO) |
|---|---|---|---|---|---|---|---|---|---|
| 1 | `profit O7 * pct>=0.3 delta_mult>=2 take win=10 persist=10 wall_ticks=8` | 255 | 5/5/2 | 1/-1/3 | 218 / -459 | - / - / - | 5/5/2/-/-/- | 30 | - |
| 2 | `profit O7 * pct>=0.2 delta_mult>=5 take win=10 persist=10 wall_ticks=8` | 273 | 5/5/2 | 1/-1/5 | 35 / -592 | - / - / - | 5/5/2/-/-/- | 48 | - |
| 3 | `profit O7 * pct>=0.4 imb5<=-0.1 take win=0 persist=2 wall_ticks=8` | 257 | 5/5/0 | 2/1/1 | -98 / -381 | - / - / - | 5/5/0/-/-/- | -99 | - |
| 4 | `profit O7 * pct>=0.3 imb5<=-0.1 take win=0 persist=2 wall_ticks=8` | 282 | 5/5/0 | 3/1/4 | -283 / -469 | - / - / - | 5/5/2/-/-/- | -276 | - |
| 5 | `profit O7 * pct>=0.3 delta_mult>=5 imb5<=-0.1 take win=10 persist=1 wall_ticks=8` | 273 | 4/4/2 | 3/-2/4 | -201 / -497 | - / - / - | 4/4/2/-/-/- | -228 | - |
| 6 | `profit O7 * pct>=0.3 pulled_against_mult>=20 step 10 win=10 persist=5 wall_ticks=8` | 267 | 4/4/2 | 3/-0/3 | 83 / -456 | - / - / - | -/-/-/-/-/- | - | - |
| 7 | `profit O7 * pct>=0.3 imb10<=-0.2 step 10 win=0 persist=1 wall_ticks=8` | 273 | 4/4/2 | 3/1/4 | 7 / -504 | - / - / - | -/-/-/-/-/- | - | - |
| 8 | `profit O7 * pct>=0.2 dd>=12 step 10 win=0 persist=10 wall_ticks=8` | 242 | 4/4/2 | 2/-1/4 | 148 / -411 | - / - / - | -/-/-/-/-/- | - | - |
| 9 | `profit O7 * pct>=0.9 take` | 167 | 1/1/0 | 0/-0/-1 | -84 / -94 | - / - / - | -/-/-/-/-/- | - | - |
| 10 | `profit O7 * pct>=0.7 imb5<=-0.1 or pulled_against_mult>=10 take win=2 persist=3 wall_ticks=8` | 182 | 1/1/0 | 0/-0/0 | -141 / -252 | - / - / - | -/-/-/-/-/- | - | - |
| 11 | `profit O7 * pct>=0.8 take` | 192 | 1/1/0 | 0/-1/-2 | -159 / -146 | - / - / - | -/-/-/-/-/- | - | - |
| 12 | `profit O7 * pct>=0.3 wall_ahead_mult>=5 step 10 win=0 persist=1 wall_ticks=8` | 267 | 4/4/2 | 3/0/4 | 89 / -553 | - / - / - | -/-/-/-/-/- | - | - |
| 13 | `profit O7 * pct>=0.3 wall_ahead_mult>=5 step 10 win=0 persist=1 wall_ticks=20` | 269 | 4/4/2 | 3/-0/4 | 27 / -587 | - / - / - | -/-/-/-/-/- | - | - |
| 14 | `profit O7 * pct>=0.3 pulled_against_mult>=5 step 10 win=3 persist=5 wall_ticks=8` | 262 | 4/4/2 | 3/-0/3 | 49 / -453 | - / - / - | -/-/-/-/-/- | - | - |
| 15 | `profit O7 * pct>=0.4 imb10<=-0.1 step 10 win=0 persist=1 wall_ticks=8` | 254 | 4/4/2 | 2/1/2 | 33 / -395 | - / - / - | -/-/-/-/-/- | - | - |
| 16 | `profit O7 * pct>=0.3 delta_mult>=2 tighten 5 win=10 persist=10 wall_ticks=8` | 254 | 5/5/2 | 2/-1/3 | 213 / -455 | - / - / - | -/-/-/-/-/- | - | - |
| 17 | `profit O7 * pct>=0.2 wall_ahead_mult>=5 lock 10 win=0 persist=1 wall_ticks=4` | 186 | 3/3/1 | 2/-1/6 | 118 / -312 | - / - / - | -/-/-/-/-/- | - | - |
| 18 | `profit O7 * pct>=0.3 delta_mult>=2 step 5 win=10 persist=10 wall_ticks=8` | 253 | 5/5/2 | 2/-1/3 | 196 / -451 | - / - / - | -/-/-/-/-/- | - | - |
| 19 | `profit O7 * pct>=0.2 delta_mult>=2 take win=8 persist=10 wall_ticks=8` | 278 | 5/5/2 | 3/-1/5 | 10 / -608 | - / - / - | -/-/-/-/-/- | - | - |
| 20 | `profit O7 * pct>=0.3 pulled_mult>=30 take win=15 persist=10 wall_ticks=8` | 239 | 4/4/2 | 2/-2/2 | -98 / -400 | - / - / - | -/-/-/-/-/- | - | - |

Slip sensitivity of the best line `profit O7 * pct>=0.3 delta_mult>=2 take win=10 persist=10 wall_ticks=8` (first-order, stack cut % / d mean $/wk):

| slip pts | cut L6M | cut L3M | cut L1M | cut HOLD | cut PRE | cut X' | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|---|---|
| 0.57 | 5 | 5 | 2 | 2 | -1 | 3 | 31 | -442 |
| 0.80 | 5 | 5 | 2 | 1 | -1 | 3 | 26 | -448 |
| 1.20 | 5 | 5 | 2 | 1 | -1 | 3 | 218 | -459 |
| 1.60 | 5 | 5 | 2 | 1 | -1 | 3 | 209 | -469 |

By entry session (the same line applied to one session only; stack effect): 

| session | trades | fires | cut L6M | cut PRE | d mean L6M | d mean PRE |
|---|---|---|---|---|---|---|
| nyam | 341 | 255 | 5 | -1 | 218 | -459 |
