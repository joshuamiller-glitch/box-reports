# DS3_RECENTS - is "what is working now" used optimally? (T-RECENTS, W-RE)

VERDICT (data ends 2026-11-13; exact-engine weeks to 2026-11-13 (true last day in series; weeks to 2026-11-09 complete Mon-Fri); November exact months only for 7 FW2 sets to 2026-11-11; market-state vector to 2026-11-11; price store daily4 to 2026-10-16; FIRST PASS, first-order composition labelled, no PASS): recency does NOT meet the 60% bar in any family. Of 144 real (family, scope, W, H) persistence cells none has P(next-H positive | positive and top third over W) >= 60% with a CI above the base rate and enough independent observations: the highest are 68% and 63% in stack-level brackets at W 3-6m -> H 3m with 0.5-2.8 effective observations, below or equal to their own shuffled-time placebo (66%, 40%); everything else is 17-53%, within a few points of the base rate. Only 6 of 144 real cells beat shuffled time at p<0.05 (all in cuts, +2..+4 points, P 25-51%) versus 10 of 60 nonsense cells (random skips/half-days) - the same magnitude, so not distinguishable from an artefact of the test. In the 43-month walk-forward the best recency window is the 26-week trailing mean (-$11/wk vs frozen on ~$11.4k/wk, block CI -60..+58 = tie); 2-week and 4-week memory are clearly worse (W4 -$139/wk, CI -192..-73); no cadence, refit scope, selection rule, shrinkage or market-state-similarity selection beats the frozen setting (JN05W2 as run) outside noise, and the only arms above it are drawdown / worst-window / placebo-gated rules that mostly stay frozen (<= +$30/wk). Change-points in market state do not precede changes of the best setting (28% vs 30% chance). Answer by family: cuts, sizing, skips, brackets, confluence = FROZEN current setting, recency is not an input; session books cannot be measured (no 43-month cohort). Shelved recent-only rules: strict reading FAIL for every rule whose older windows are run, tolerant reading PASS only for the U7 time stop B (X' and PRE run, GAP not run); the rest FAIL or are UNRESOLVED (older windows not run). Updated 2026-11-15 19:41 UTC.

Generated 2026-11-15 19:41 UTC. Research only; shadow only. Code outputs/code/th_recents/ (rc_extract, rc_lib, rc_persist, rc_walk, rc_walk_run, rc_regime, rc_gate, rc_state, rc_enddate, rc_page); bulk /mnt/l2/l2vast/_recents/. Basis everywhere: exact-engine stored runs (runs_rf/<set>/<month>/trades.parquet), weekly = Monday-start weeks of the Globex label day, BASE LOTS, engine fee $1.18/ct RT (x1.75 live-size and the $4.84 repricing are NOT applied in the weekly series: multiply dollar figures by 1.75 for live-lot scale; fee repricing moves each rule by (4.84-1.18) x its lot change per week, small vs the effects here). Live caps P7 14,700 = engine 8,400 (live-lot figures = base x1.75). Weekly delta = set minus its own base (JN05W2 for TL3_*/SM_A6; LPB_EMPTY for EC_FLAT*; JN04RM for JN04RM_FLAT*). Sets on other bases (PTR_, BO_, G3_, WL/WG, SB_ ...) are excluded, no like-for-like reference.


## 0. Data ends before today, and the end-date checker

Today is 2026-11-15. Ends found on the box:

| object | ends | note |
|--|--|--|
| exact-engine runs (runs_rf, 2,662 sets) | 202610 (last trading day 2026-10-30) for all but 7 sets | only FW2_JN05W2, _nBR3S, _nC22, _nE1, _nF3, _nFLAT, FW2_LPB_EMPTY have 202611 (trades to 2026-11-11) |
| signal universe (191,520 rows) | 2026-10-30 | W-CF1 asked to extend to today |
| state days (th_state, 1-second NQ) | 2026-11-11 (935 Globex days from 2023-04-03) | weekly state vector in this page uses it |
| REG-ATR / panel_cal | 2026-11-12 | |
| price store daily4 (ES/RTY/YM ...) | 2026-10-16 | W-EV asked to extend through 11-14 |
| prior persistence page DS3_PERSISTENCE | cap 2026-02-06 | superseded by section 1 |

**The windows L1M/L3M/L6M of every page therefore end 2026-10-30 (not today); they cannot be moved to 2026-11-15 without engine months for 202611.** Request logged in MORNING.md to W-EV (extended price store, command) and W-CF1 (universe/logger to today) to schedule the November exact months for the main sets (JN05W2, JN05W2J, JV_A/AB/B/C, EA_A6, LR_LS1/LS125, RA_CAP3/BLKiv, EB_U7F_T15D10, PR_BLK_M30, EC_FLAT40K/A, CF_G P7A sets). This page re-runs from the stored files in minutes once those months land (rc_extract.py then rc_persist/rc_walk_run).

End-date checker: code/th_recents/rc_enddate.py scans autopilot/DS3_*.md and flags verdict lines without a stated data end date; output autopilot/ENDDATE_AUDIT.csv. Result today: 1185 DS3 pages; 248 carry a verdict line in the first 60 lines; **229 of 248 verdict lines state no data end date** (and 937 pages have no verdict line at all). Of the 52 verdict pages touched since 2026-11-14, 19 state an end date. This page's verdict states one.


## 1. Persistence, measured properly (answer first)

Unit = (set, book) [scope 'book', family x book cohorts] or (set, all books) [scope 'ALL', family cohorts]; delta = weekly $ minus the set's own base, 187 weeks 2023-04-03..2026-10-26 (sets with fewer months contribute their available stretch). A setting is SELECTED at origin week i if its trailing-W mean delta > 0 AND it is in the top third of its cohort (family x book) at i (cohort >= 3 live units, trailing window complete, delta not identically 0). Outcome: mean delta over the next H weeks > 0 (W: 2w=2, 1m=4, 3m=13, 6m=26, 12m=52 weeks; H: 2w=2, 1m=4, 3m=13). Cells: P(next-H positive | selected) / base rate P(next-H positive | any eligible unit, same origins) / shuffled-time P (each unit's selection signal circularly shifted by an independent random offset, 100 reps, outcome unshifted: keeps the unit's long-run quality, destroys the recency link). 'p vs shift' = share of shuffled reps >= the real P (small = recency adds information). 95% CI = moving-block bootstrap over origin weeks (block = max(W,H,8)). 'eff n' = origins / max(W,H) = independent observations (overlapping windows). Bar: P >= 60% AND CI low > base AND p vs shift < 0.05.

**Result: 0 of 144 real-family cells pass the 60% bar test.** Highest P cells: brackets/ALL W6m H3m P=68% (base 51%, shuffled 33%, eff n 0.5), brackets/ALL W3m H3m P=63% (base 47%, shuffled 65%, eff n 2.8), skips/ALL W6m H3m P=53% (base 46%, shuffled 56%, eff n 5.8), skips/ALL W12m H1m P=52% (base 46%, shuffled 54%, eff n 2.6), cuts/ALL W1m H2w P=51% (base 47%, shuffled 47%, eff n 44.8), skips/ALL W6m H1m P=51% (base 43%, shuffled 50%, eff n 6.2). The few cells above 60% sit on 3-6 month windows with eff n <= 5 and are at or below their own shuffled placebo.


**Scope 'book'** (cell text = real P / base rate / shuffled P, then p vs shift, all in %):


*brackets* - 120 units

| W \ H | 2w | 1m | 3m |
|--|--|--|--|
| 2w | 42 / 43 / 50 (p 0.99; n_sel 1,500, eff n 42.0) | 44 / 45 / 49 (p 0.90; n_sel 1,426, eff n 20.0) | 43 / 43 / 44 (p 0.55; n_sel 1,146, eff n 4.8) |
| 1m | 39 / 39 / 45 (p 0.93; n_sel 1,656, eff n 20.0) | 42 / 42 / 46 (p 0.81; n_sel 1,574, eff n 19.0) | 42 / 43 / 45 (p 0.60; n_sel 1,263, eff n 4.5) |
| 3m | 31 / 31 / 38 (p 0.88; n_sel 1,566, eff n 4.8) | 34 / 34 / 41 (p 0.85; n_sel 1,480, eff n 4.5) | 48 / 40 / 52 (p 0.69; n_sel 1,107, eff n 3.1) |
| 6m | 28 / 29 / 38 (p 0.76; n_sel 1,062, eff n 1.4) | 31 / 31 / 26 (p 0.35; n_sel 966, eff n 1.2) | 42 / 37 / 50 (p 0.59; n_sel 535, eff n 0.5) |
| 12m | n_sel<30 | n_sel<30 | n_sel<30 |


*confluence* - 841 units

| W \ H | 2w | 1m | 3m |
|--|--|--|--|
| 2w | 38 / 37 / 44 (p 1.00; n_sel 8,115, eff n 92.0) | 41 / 41 / 48 (p 1.00; n_sel 7,809, eff n 45.5) | 43 / 43 / 49 (p 1.00; n_sel 6,475, eff n 13.3) |
| 1m | 34 / 33 / 42 (p 1.00; n_sel 9,846, eff n 45.5) | 39 / 38 / 46 (p 1.00; n_sel 9,474, eff n 45.0) | 42 / 42 / 49 (p 1.00; n_sel 7,823, eff n 13.2) |
| 3m | 29 / 27 / 37 (p 1.00; n_sel 11,204, eff n 13.3) | 35 / 32 / 42 (p 1.00; n_sel 10,692, eff n 13.2) | 42 / 39 / 47 (p 1.00; n_sel 8,540, eff n 12.5) |
| 6m | 27 / 24 / 35 (p 1.00; n_sel 9,184, eff n 6.2) | 31 / 29 / 40 (p 1.00; n_sel 8,610, eff n 6.1) | 38 / 35 / 46 (p 1.00; n_sel 5,978, eff n 5.7) |
| 12m | 29 / 27 / 37 (p 1.00; n_sel 2,826, eff n 2.6) | 34 / 32 / 43 (p 1.00; n_sel 2,750, eff n 2.5) | 44 / 41 / 49 (p 0.96; n_sel 2,446, eff n 2.4) |


*cuts* - 222 units

| W \ H | 2w | 1m | 3m |
|--|--|--|--|
| 2w | 37 / 31 / 43 (p 1.00; n_sel 3,023, eff n 90.0) | 41 / 35 / 44 (p 1.00; n_sel 2,916, eff n 44.5) | 41 / 41 / 41 (p 0.62; n_sel 2,390, eff n 12.8) |
| 1m | 33 / 27 / 37 (p 1.00; n_sel 3,905, eff n 45.0) | 37 / 32 / 39 (p 0.93; n_sel 3,741, eff n 44.2) | 40 / 39 / 41 (p 0.75; n_sel 3,044, eff n 12.8) |
| 3m | 25 / 22 / 26 (p 0.89; n_sel 4,887, eff n 13.5) | 30 / 27 / 30 (p 0.49; n_sel 4,686, eff n 13.3) | 40 / 36 / 38 (p 0.13; n_sel 3,881, eff n 12.5) |
| 6m | 25 / 20 / 22 (p 0.01; n_sel 4,495, eff n 6.2) | 31 / 25 / 27 (p 0.00; n_sel 4,266, eff n 6.2) | 38 / 33 / 38 (p 0.48; n_sel 3,275, eff n 5.8) |
| 12m | 17 / 17 / 17 (p 0.43; n_sel 2,563, eff n 2.6) | 25 / 22 / 28 (p 0.93; n_sel 2,485, eff n 2.6) | 37 / 32 / 45 (p 1.00; n_sel 2,153, eff n 2.4) |


*nonsense_half (NONSENSE control)* - 336 units

| W \ H | 2w | 1m | 3m |
|--|--|--|--|
| 2w | 34 / 34 / 36 (p 1.00; n_sel 13,051, eff n 93.0) | 39 / 39 / 40 (p 1.00; n_sel 12,912, eff n 46.0) | 36 / 37 / 36 (p 0.21; n_sel 12,285, eff n 13.5) |
| 1m | 32 / 32 / 34 (p 1.00; n_sel 16,007, eff n 46.0) | 38 / 38 / 39 (p 1.00; n_sel 15,820, eff n 45.5) | 37 / 37 / 37 (p 0.17; n_sel 15,023, eff n 13.3) |
| 3m | 30 / 30 / 30 (p 0.90; n_sel 17,165, eff n 13.5) | 36 / 36 / 36 (p 0.96; n_sel 16,968, eff n 13.3) | 37 / 37 / 37 (p 0.71; n_sel 16,173, eff n 12.6) |
| 6m | 30 / 30 / 29 (p 0.03; n_sel 14,942, eff n 6.2) | 36 / 36 / 36 (p 0.51; n_sel 14,789, eff n 6.2) | 37 / 36 / 37 (p 0.36; n_sel 14,119, eff n 5.8) |
| 12m | 28 / 30 / 28 (p 0.59; n_sel 10,611, eff n 2.6) | 35 / 35 / 35 (p 0.41; n_sel 10,466, eff n 2.6) | 37 / 35 / 36 (p 0.08; n_sel 9,866, eff n 2.4) |


*nonsense_skip (NONSENSE control)* - 336 units

| W \ H | 2w | 1m | 3m |
|--|--|--|--|
| 2w | 34 / 34 / 37 (p 1.00; n_sel 13,084, eff n 93.0) | 39 / 39 / 40 (p 0.99; n_sel 12,939, eff n 46.0) | 38 / 38 / 37 (p 0.06; n_sel 12,326, eff n 13.5) |
| 1m | 33 / 33 / 34 (p 1.00; n_sel 15,999, eff n 46.0) | 38 / 38 / 39 (p 0.94; n_sel 15,814, eff n 45.5) | 38 / 38 / 38 (p 0.39; n_sel 15,061, eff n 13.3) |
| 3m | 31 / 31 / 31 (p 0.67; n_sel 17,108, eff n 13.5) | 37 / 37 / 37 (p 0.25; n_sel 16,920, eff n 13.3) | 38 / 38 / 38 (p 0.09; n_sel 16,177, eff n 12.6) |
| 6m | 30 / 30 / 29 (p 0.00; n_sel 15,277, eff n 6.2) | 37 / 36 / 35 (p 0.00; n_sel 15,125, eff n 6.2) | 38 / 37 / 37 (p 0.00; n_sel 14,400, eff n 5.8) |
| 12m | 29 / 30 / 28 (p 0.02; n_sel 11,411, eff n 2.6) | 36 / 36 / 34 (p 0.03; n_sel 11,269, eff n 2.6) | 38 / 36 / 35 (p 0.00; n_sel 10,650, eff n 2.4) |


*placebo_exact (NONSENSE control)* - 295 units

| W \ H | 2w | 1m | 3m |
|--|--|--|--|
| 2w | 37 / 38 / 43 (p 1.00; n_sel 3,296, eff n 33.0) | 41 / 41 / 44 (p 0.90; n_sel 3,190, eff n 16.0) | 40 / 40 / 43 (p 0.74; n_sel 2,650, eff n 4.2) |
| 1m | 35 / 36 / 41 (p 0.97; n_sel 3,618, eff n 16.0) | 39 / 40 / 43 (p 0.89; n_sel 3,483, eff n 15.5) | 42 / 40 / 46 (p 0.79; n_sel 2,878, eff n 4.1) |
| 3m | 32 / 34 / 37 (p 0.95; n_sel 3,541, eff n 4.2) | 37 / 38 / 43 (p 0.90; n_sel 3,387, eff n 4.1) | 40 / 39 / 63 (p 0.95; n_sel 2,701, eff n 3.4) |
| 6m | 31 / 32 / 46 (p 0.74; n_sel 2,454, eff n 1.6) | 37 / 35 / 52 (p 0.74; n_sel 2,295, eff n 1.5) | n_sel<30 |
| 12m | n_sel<30 | n_sel<30 | n_sel<30 |


*sizing* - 155 units

| W \ H | 2w | 1m | 3m |
|--|--|--|--|
| 2w | 38 / 36 / 43 (p 1.00; n_sel 1,813, eff n 85.5) | 41 / 40 / 46 (p 0.99; n_sel 1,771, eff n 42.0) | 42 / 43 / 50 (p 1.00; n_sel 1,546, eff n 12.4) |
| 1m | 35 / 33 / 40 (p 1.00; n_sel 2,231, eff n 44.8) | 38 / 37 / 44 (p 1.00; n_sel 2,187, eff n 44.0) | 41 / 42 / 49 (p 1.00; n_sel 1,913, eff n 12.9) |
| 3m | 32 / 29 / 34 (p 0.87; n_sel 2,614, eff n 13.2) | 37 / 34 / 39 (p 0.81; n_sel 2,548, eff n 13.2) | 38 / 40 / 45 (p 1.00; n_sel 2,248, eff n 12.5) |
| 6m | 29 / 27 / 31 (p 0.90; n_sel 2,317, eff n 6.2) | 32 / 32 / 37 (p 0.98; n_sel 2,248, eff n 6.2) | 37 / 38 / 45 (p 1.00; n_sel 1,903, eff n 5.8) |
| 12m | 25 / 26 / 32 (p 0.99; n_sel 1,595, eff n 2.6) | 30 / 32 / 38 (p 1.00; n_sel 1,560, eff n 2.6) | 41 / 42 / 52 (p 1.00; n_sel 1,409, eff n 2.4) |


*skips* - 1329 units

| W \ H | 2w | 1m | 3m |
|--|--|--|--|
| 2w | 40 / 39 / 44 (p 1.00; n_sel 15,730, eff n 82.0) | 44 / 43 / 48 (p 1.00; n_sel 15,034, eff n 40.2) | 47 / 46 / 52 (p 1.00; n_sel 12,330, eff n 11.7) |
| 1m | 37 / 36 / 41 (p 1.00; n_sel 18,380, eff n 45.0) | 42 / 40 / 46 (p 1.00; n_sel 17,603, eff n 44.5) | 47 / 45 / 53 (p 1.00; n_sel 14,574, eff n 13.0) |
| 3m | 33 / 30 / 36 (p 1.00; n_sel 20,290, eff n 13.5) | 38 / 35 / 42 (p 1.00; n_sel 19,393, eff n 13.3) | 44 / 41 / 52 (p 1.00; n_sel 16,031, eff n 12.6) |
| 6m | 32 / 27 / 34 (p 0.97; n_sel 17,156, eff n 6.2) | 37 / 31 / 41 (p 1.00; n_sel 16,288, eff n 6.2) | 42 / 38 / 49 (p 1.00; n_sel 12,639, eff n 5.8) |
| 12m | 29 / 24 / 32 (p 0.96; n_sel 7,465, eff n 2.6) | 36 / 30 / 39 (p 0.81; n_sel 7,136, eff n 2.6) | 44 / 41 / 48 (p 0.85; n_sel 5,665, eff n 2.4) |


**Scope 'ALL'** (cell text = real P / base rate / shuffled P, then p vs shift, all in %):


*brackets* - 18 units

| W \ H | 2w | 1m | 3m |
|--|--|--|--|
| 2w | 38 / 41 / 40 (p 0.60; n_sel 274, eff n 38.5) | 43 / 42 / 39 (p 0.35; n_sel 261, eff n 18.2) | 42 / 40 / 34 (p 0.27; n_sel 208, eff n 4.5) |
| 1m | 39 / 39 / 38 (p 0.46; n_sel 290, eff n 18.5) | 40 / 41 / 39 (p 0.45; n_sel 274, eff n 17.5) | 46 / 42 / 36 (p 0.26; n_sel 214, eff n 4.1) |
| 3m | 40 / 36 / 37 (p 0.37; n_sel 257, eff n 4.5) | 47 / 41 / 43 (p 0.41; n_sel 241, eff n 4.2) | 63 / 47 / 65 (p 0.54; n_sel 172, eff n 2.8) |
| 6m | 42 / 36 / 20 (p 0.19; n_sel 151, eff n 1.2) | 51 / 40 / 50 (p 0.49; n_sel 135, eff n 1.1) | 68 / 51 / 33 (p 0.33; n_sel 75, eff n 0.5) |
| 12m | n_sel<30 | n_sel<30 | n_sel<30 |


*confluence* - 192 units

| W \ H | 2w | 1m | 3m |
|--|--|--|--|
| 2w | 46 / 44 / 47 (p 0.86; n_sel 3,820, eff n 91.0) | 48 / 47 / 49 (p 0.79; n_sel 3,688, eff n 44.8) | 46 / 47 / 50 (p 1.00; n_sel 3,088, eff n 13.0) |
| 1m | 44 / 43 / 46 (p 0.94; n_sel 4,124, eff n 44.8) | 48 / 46 / 49 (p 0.56; n_sel 3,972, eff n 44.0) | 47 / 47 / 50 (p 0.95; n_sel 3,302, eff n 12.7) |
| 3m | 44 / 41 / 45 (p 0.88; n_sel 3,681, eff n 13.2) | 47 / 45 / 47 (p 0.54; n_sel 3,519, eff n 12.9) | 50 / 46 / 48 (p 0.25; n_sel 2,802, eff n 11.8) |
| 6m | 45 / 41 / 45 (p 0.46; n_sel 2,624, eff n 5.7) | 49 / 44 / 46 (p 0.14; n_sel 2,463, eff n 5.5) | 49 / 46 / 48 (p 0.44; n_sel 1,714, eff n 4.9) |
| 12m | 45 / 44 / 47 (p 0.94; n_sel 722, eff n 2.3) | 43 / 45 / 49 (p 0.94; n_sel 700, eff n 2.3) | 37 / 43 / 40 (p 0.66; n_sel 619, eff n 2.1) |


*cuts* - 42 units

| W \ H | 2w | 1m | 3m |
|--|--|--|--|
| 2w | 49 / 48 / 49 (p 0.25; n_sel 1,441, eff n 90.0) | 49 / 48 / 47 (p 0.07; n_sel 1,401, eff n 44.5) | 44 / 43 / 41 (p 0.06; n_sel 1,192, eff n 12.5) |
| 1m | 51 / 47 / 47 (p 0.00; n_sel 1,466, eff n 44.8) | 50 / 47 / 46 (p 0.02; n_sel 1,421, eff n 44.0) | 46 / 44 / 41 (p 0.02; n_sel 1,203, eff n 12.3) |
| 3m | 46 / 46 / 46 (p 0.34; n_sel 1,332, eff n 12.9) | 48 / 46 / 44 (p 0.08; n_sel 1,277, eff n 12.7) | 48 / 43 / 37 (p 0.00; n_sel 1,053, eff n 11.3) |
| 6m | 47 / 46 / 44 (p 0.16; n_sel 1,073, eff n 5.8) | 46 / 45 / 44 (p 0.16; n_sel 1,020, eff n 5.7) | 39 / 39 / 34 (p 0.16; n_sel 796, eff n 5.3) |
| 12m | 34 / 39 / 33 (p 0.40; n_sel 537, eff n 2.5) | 31 / 37 / 31 (p 0.50; n_sel 522, eff n 2.4) | 22 / 32 / 40 (p 1.00; n_sel 439, eff n 2.1) |


*nonsense_half (NONSENSE control)* - 48 units

| W \ H | 2w | 1m | 3m |
|--|--|--|--|
| 2w | 39 / 40 / 39 (p 0.53; n_sel 2,613, eff n 93.0) | 35 / 36 / 36 (p 0.86; n_sel 2,584, eff n 46.0) | 23 / 24 / 24 (p 0.89; n_sel 2,480, eff n 13.5) |
| 1m | 39 / 39 / 39 (p 0.54; n_sel 2,467, eff n 46.0) | 35 / 36 / 36 (p 0.75; n_sel 2,440, eff n 45.5) | 23 / 24 / 24 (p 0.91; n_sel 2,328, eff n 13.3) |
| 3m | 39 / 39 / 39 (p 0.49; n_sel 1,895, eff n 13.5) | 33 / 35 / 36 (p 0.94; n_sel 1,879, eff n 13.3) | 22 / 24 / 24 (p 0.85; n_sel 1,839, eff n 12.6) |
| 6m | 41 / 39 / 39 (p 0.11; n_sel 1,313, eff n 6.0) | 37 / 34 / 35 (p 0.11; n_sel 1,312, eff n 6.0) | 29 / 23 / 23 (p 0.01; n_sel 1,293, eff n 5.8) |
| 12m | 43 / 38 / 39 (p 0.05; n_sel 685, eff n 2.6) | 42 / 33 / 36 (p 0.02; n_sel 685, eff n 2.6) | 34 / 20 / 21 (p 0.00; n_sel 671, eff n 2.4) |


*nonsense_skip (NONSENSE control)* - 48 units

| W \ H | 2w | 1m | 3m |
|--|--|--|--|
| 2w | 41 / 40 / 41 (p 0.35; n_sel 2,633, eff n 93.0) | 37 / 37 / 37 (p 0.46; n_sel 2,603, eff n 46.0) | 27 / 27 / 27 (p 0.72; n_sel 2,494, eff n 13.5) |
| 1m | 40 / 40 / 40 (p 0.81; n_sel 2,469, eff n 46.0) | 36 / 36 / 36 (p 0.61; n_sel 2,440, eff n 45.5) | 26 / 27 / 27 (p 0.88; n_sel 2,341, eff n 13.3) |
| 3m | 40 / 40 / 40 (p 0.69; n_sel 2,022, eff n 13.5) | 35 / 36 / 36 (p 0.79; n_sel 2,008, eff n 13.3) | 26 / 26 / 27 (p 0.60; n_sel 1,966, eff n 12.6) |
| 6m | 41 / 39 / 40 (p 0.45; n_sel 1,463, eff n 6.2) | 37 / 35 / 36 (p 0.33; n_sel 1,458, eff n 6.2) | 28 / 25 / 27 (p 0.37; n_sel 1,440, eff n 5.8) |
| 12m | 39 / 39 / 38 (p 0.25; n_sel 754, eff n 2.5) | 33 / 34 / 31 (p 0.15; n_sel 752, eff n 2.4) | 22 / 24 / 20 (p 0.38; n_sel 749, eff n 2.4) |


*placebo_exact (NONSENSE control)* - 45 units

| W \ H | 2w | 1m | 3m |
|--|--|--|--|
| 2w | 40 / 43 / 44 (p 0.89; n_sel 704, eff n 31.5) | 35 / 38 / 38 (p 0.84; n_sel 694, eff n 15.2) | 24 / 31 / 35 (p 0.94; n_sel 580, eff n 4.0) |
| 1m | 39 / 43 / 44 (p 0.89; n_sel 657, eff n 15.2) | 33 / 37 / 38 (p 0.82; n_sel 645, eff n 14.8) | 23 / 31 / 37 (p 0.95; n_sel 551, eff n 3.9) |
| 3m | 37 / 41 / 45 (p 0.84; n_sel 505, eff n 4.1) | 30 / 36 / 41 (p 0.79; n_sel 501, eff n 3.9) | 22 / 29 / 69 (p 0.88; n_sel 423, eff n 3.2) |
| 6m | 40 / 39 / 66 (p 0.89; n_sel 326, eff n 1.6) | 35 / 30 / 67 (p 0.85; n_sel 311, eff n 1.5) | n_sel<30 |
| 12m | n_sel<30 | n_sel<30 | n_sel<30 |


*sizing* - 23 units

| W \ H | 2w | 1m | 3m |
|--|--|--|--|
| 2w | 44 / 45 / 46 (p 0.83; n_sel 561, eff n 81.5) | 44 / 43 / 47 (p 0.90; n_sel 549, eff n 40.2) | 41 / 43 / 50 (p 0.99; n_sel 492, eff n 11.7) |
| 1m | 44 / 44 / 47 (p 0.75; n_sel 560, eff n 43.0) | 44 / 42 / 46 (p 0.79; n_sel 554, eff n 42.5) | 39 / 43 / 51 (p 1.00; n_sel 494, eff n 12.4) |
| 3m | 42 / 42 / 46 (p 0.92; n_sel 542, eff n 13.0) | 40 / 40 / 45 (p 0.86; n_sel 534, eff n 12.8) | 32 / 40 / 49 (p 1.00; n_sel 479, eff n 12.2) |
| 6m | 42 / 39 / 45 (p 0.90; n_sel 487, eff n 6.2) | 42 / 37 / 43 (p 0.60; n_sel 475, eff n 6.2) | 39 / 39 / 51 (p 0.95; n_sel 409, eff n 5.8) |
| 12m | 43 / 43 / 49 (p 0.91; n_sel 273, eff n 2.5) | 48 / 44 / 48 (p 0.52; n_sel 267, eff n 2.4) | 45 / 45 / 55 (p 0.86; n_sel 246, eff n 2.2) |


*skips* - 214 units

| W \ H | 2w | 1m | 3m |
|--|--|--|--|
| 2w | 45 / 45 / 48 (p 0.99; n_sel 4,133, eff n 90.5) | 46 / 47 / 50 (p 0.98; n_sel 3,961, eff n 44.5) | 48 / 49 / 53 (p 0.98; n_sel 3,305, eff n 13.0) |
| 1m | 45 / 44 / 46 (p 0.84; n_sel 4,390, eff n 45.0) | 48 / 46 / 50 (p 0.95; n_sel 4,215, eff n 44.5) | 49 / 49 / 54 (p 0.99; n_sel 3,505, eff n 13.0) |
| 3m | 45 / 41 / 45 (p 0.50; n_sel 4,044, eff n 13.2) | 48 / 44 / 50 (p 0.86; n_sel 3,882, eff n 13.1) | 50 / 47 / 57 (p 1.00; n_sel 3,225, eff n 12.4) |
| 6m | 46 / 41 / 44 (p 0.07; n_sel 3,233, eff n 6.2) | 51 / 43 / 50 (p 0.30; n_sel 3,080, eff n 6.2) | 53 / 46 / 56 (p 0.77; n_sel 2,442, eff n 5.8) |
| 12m | 47 / 42 / 47 (p 0.48; n_sel 1,354, eff n 2.6) | 52 / 46 / 54 (p 0.61; n_sel 1,297, eff n 2.6) | 50 / 51 / 56 (p 0.64; n_sel 1,046, eff n 2.4) |


How to read the controls: nonsense units (random day skips or random half-size days of 5-30% on JN05W2, 12 seeds each, built from the day tables; plus the exact placebo sets TL3_*_PL11/23/37, *_PB1-3) go through the identical pipeline. They land in the same band as the real families (P 20-43%, base 20-40%) and, like the real cuts, show a few cells with p<0.05 vs shuffled time (8 of 60), so a +2..+4 point lift is the size of the test's own artefact. Next-H dollars of the selected units minus the shuffled-selection units (persist_table.csv: meanF_sel - meanF_shift, $/wk): cuts +70 (book) / +170 (all-books), confluence +73 / +164, nonsense_skip +46 / +343, sizing -44 / -335, skips -59 / -260, brackets -16 / -373: mixed in sign and no larger for real cuts/confluence than for nonsense; none is tested to be nonzero. Persistence of 'what works now' is therefore indistinguishable from the persistence of long-run quality (the shuffled placebo keeps each unit's own level), and where it differs from that it is not robustly positive.
Caveat on the unit: many sets in a family are near copies (parameter variants), so cohort members are strongly dependent; the CI is block bootstrapped over time and 'eff n' is the honest count.

## 2-5. Look-back, cadence, what to refit, how to select (walk-forward through the 43 months, FIRST PASS first-order)

Method. Arena A: every layer cohort (family x book, 27 cohorts: cuts 6, sizing 7, skips 7, confluence 7; brackets and session books have no cohort with a complete 43-month stretch) with candidates = sets that have all 187 weeks plus 'base' (delta 0, JN05W2 as run). Refit every 2 weeks from week 53 (2024-04-01) using only weeks before the refit week; position held until the next refit; realised delta = the chosen candidate's actual weekly delta. Cohort series are MEANed over cohorts (never summed: layers overlap; this is first-order and labelled so). Cells show **mean $/wk vs BASE / max-DD cut % of the stack proxy (JN05W2 + mean delta)**; BASE = 0 / 0 by construction; FROZEN = the long-run pick at the first refit, never updated; LONGRUN = expanding-window best (slow refit); RANDOM = random candidate each refit, 100 draws (mean and 95th percentile of draws). A '+' beats base; to count as information an arm must also beat RANDOM-p95.

**Arena A (43 months, by family; mean $/wk vs base / DD cut %)**

| arm | ALL | cuts | sizing | skips | confluence |
|--|--|--|--|--|--|
| BASE | +0 / +0.0 | +0 / +0.0 | +0 / +0.0 | +0 / +0.0 | +0 / +0.0 |
| FROZEN | -143 / -1.3 | -131 / -2.1 | +14 / -0.1 | -20 / -0.7 | -433 / -3.6 |
| LONGRUN | -44 / +0.9 | -16 / +0.6 | -9 / +0.6 | -15 / -2.0 | -134 / +3.0 |
| FINE-MEAN-W4-c2 | -139 / +0.6 | -117 / +0.7 | -54 / -0.7 | -16 / -0.3 | -368 / +2.1 |
| FINE-MEAN-W13-c2 | -79 / -0.2 | -100 / +1.3 | -20 / -0.9 | -75 / -1.3 | -123 / -1.6 |
| FINE-MEAN-W26-c2 | -11 / +0.8 | -42 / +2.0 | +13 / +0.2 | -1 / -0.4 | -18 / +1.6 |
| FINE-MEAN-W52-c2 | -75 / +0.9 | -15 / +0.8 | -33 / -0.9 | -2 / -0.1 | -242 / +3.0 |
| FINE-EXP-hl2-c2 | -143 / +0.3 | -127 / +1.2 | -13 / -0.7 | -129 / -2.5 | -301 / +1.6 |
| FINE-EXP-hl4-c2 | -80 / +0.2 | -75 / +1.2 | -35 / -0.7 | -96 / -2.0 | -111 / +0.9 |
| FINE-EXP-hl13-c2 | -67 / +0.8 | -31 / +1.0 | -7 / +0.6 | -13 / -0.6 | -211 / +1.3 |
| FINE-EXP-hl26-c2 | -61 / +1.2 | -24 / +0.6 | -0 / +0.6 | -1 / -1.3 | -211 / +3.0 |
| FINE-DD-W26-c2 | +6 / +0.1 | +10 / +0.1 | -5 / +0.0 | +9 / +0.0 | +10 / +0.2 |
| FINE-MED-W26-c2 | -74 / +0.1 | -84 / +0.4 | -67 / +0.9 | -39 / -0.7 | -108 / -0.3 |
| FINE-WORST-W26-c2 | -2 / +0.0 | +0 / +0.0 | -6 / +0.0 | -14 / +0.0 | +12 / +0.0 |
| FINE-PLC-W26-c2 | -8 / -0.0 | -17 / +0.0 | -18 / +0.0 | -13 / -0.1 | +16 / +0.0 |
| RANDOM-mean | -70 / -1.0 | -78 / -0.7 | +3 / -0.6 | -32 / -1.0 | -174 / -2.0 |
| RANDOM-p95 | -22 / +0.5 | -19 / +1.6 | +79 / +1.5 | +40 / +1.7 | -24 / +1.7 |


**By year and since 2026-05 (arena A, all cohorts)**

| arm | mean_43m | ddcut_43m | y2024 | y2025 | y2026 | since_2026_05 | ddcut_since_2026_05 |
|--|--|--|--|--|--|--|--|
| BASE | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 |
| LONGRUN | -44.4 | 0.9 | -40.2 | -44.5 | -48.3 | -58.9 | 1.4 |
| FINE-MEAN-W26-c2 | -11.2 | 0.8 | 23.0 | -21.2 | -30.9 | -73.0 | 2.2 |
| FINE-MEAN-W13-c2 | -78.8 | -0.2 | -24.6 | -75.2 | -133.7 | -125.5 | 0.8 |
| FINE-EXP-hl13-c2 | -66.6 | 0.8 | 22.5 | -80.2 | -133.0 | -189.2 | -1.0 |
| FINE-DD-W26-c2 | 5.9 | 0.1 | -2.7 | 15.4 | 2.4 | -3.5 | 0.0 |
| FINE-PLC-W26-c2 | -7.7 | -0.0 | 14.7 | -19.9 | -13.9 | -34.2 | 0.0 |
| CHOICE3-MEAN-W26-sh50 | -34.3 | 0.6 | -13.4 | -45.6 | -39.9 | -42.5 | 1.2 |
| SIZE-MEAN-W26-sh0 | -33.1 | 1.0 | 2.9 | -71.3 | -20.6 | 2.1 | 1.4 |
| FINE-SIMREC-hl52 | -40.3 | 0.7 | -37.8 | -43.1 | -39.3 | -91.9 | 1.8 |
| RANDOM-mean | -69.8 | -1.0 | -50.5 | -63.6 | -95.1 | -93.8 | 1.3 |
| RANDOM-p95 | -22.1 | 0.5 | 35.7 | 0.2 | 17.9 | 67.0 | 2.5 |


**Paired weekly series vs BASE with block-bootstrap CI (block 8 wk; 135 weeks 2024-04..2026-10 = ~17 independent 8-week blocks)**

| arm | mean_per_wk | ci95_block | verdict |
|--|--|--|--|
| LONGRUN | -44.4 | -100 .. +29 | indistinguishable from base |
| FINE-MEAN-W4-c2 | -139.3 | -192 .. -73 | worse than base |
| FINE-MEAN-W13-c2 | -78.8 | -132 .. +0 | indistinguishable from base |
| FINE-MEAN-W26-c2 | -11.2 | -60 .. +58 | indistinguishable from base |
| FINE-EXP-hl13-c2 | -66.6 | -126 .. +23 | indistinguishable from base |
| FINE-DD-W26-c2 | 5.9 | -5 .. +18 | indistinguishable from base |
| FINE-PLC-W26-c2 | -7.7 | -22 .. +12 | indistinguishable from base |
| FINE-WORST-W26-c2 | -2.1 | -13 .. +8 | indistinguishable from base |
| CHOICE3-MEAN-W26-sh50 | -34.3 | -72 .. +28 | indistinguishable from base |
| SIZE-MEAN-W26-sh0 | -33.1 | -96 .. +51 | indistinguishable from base |
| FINE-SIMREC-hl52 | -40.3 | -101 .. +42 | indistinguishable from base |


**Item 2 - best look-back per family (raw trailing mean selection, biweekly)**

| family | best_lookback | mean | ddcut | longrun_mean | random_p95_mean | beats_random_p95 | beats_base |
|--|--|--|--|--|--|--|--|
| ALL | FINE-MEAN-W26-c2 | -11.2 | 0.8 | -44.4 | -22.1 | yes | no |
| cuts | FINE-MEAN-W52-c2 | -14.9 | 0.8 | -16.0 | -19.0 | yes | no |
| sizing | FINE-MEAN-W26-c2 | 12.8 | 0.2 | -9.0 | 78.9 | no | yes |
| skips | FINE-EXP-hl26-c2 | -1.2 | -1.3 | -14.5 | 39.8 | no | no |
| confluence | FINE-MEAN-W26-c2 | -18.3 | 1.6 | -134.0 | -23.5 | yes | no |

Reading: the 26-week window and the slow half-lives are the least bad (W4 -139, W13 -79, W26 -11, W52 -75; hl2 -143, hl4 -80, hl13 -67, hl26 -61 $/wk), but the profile is not monotone (W52 is worse than W26) and every memory is at or below the frozen setting; only W4 is clearly worse by CI. The stale-selection placebo (signal 12 weeks old) gives W26 -35 (live -11) and W13 -30 (live -79): recent beats stale at W26 and loses to it at W13, i.e. there is no consistent value in the data being recent. Per family the best look-back differs (sizing W26 +13, cuts W52, skips hl26, confluence W26) and none exceeds RANDOM-p95 in sizing/skips; with ~100 arms x 5 families, a handful above a 95th percentile is expected by chance.


**Item 3 - cadence (arena A; c1 weekly, c2 two-weekly, c4 monthly, c13 quarterly, PERF = refit when the held setting's last 4 weeks fall below -1 sd of its own 4-week sums, CP = refit on a state change-point, STALE12 = signal 12 weeks old)**

| arm | ALL | cuts | sizing | skips | confluence |
|--|--|--|--|--|--|
| FINE-MEAN-W13-c1 | -79 / -0.1 | -91 / +1.8 | -17 / -1.4 | -54 / -1.3 | -155 / -1.1 |
| FINE-MEAN-W13-c2 | -79 / -0.2 | -100 / +1.3 | -20 / -0.9 | -75 / -1.3 | -123 / -1.6 |
| FINE-MEAN-W13-c4 | -75 / +0.1 | -93 / +2.0 | -36 / -0.9 | -41 / -1.3 | -131 / -0.8 |
| FINE-MEAN-W13-c13 | -41 / -0.2 | -33 / +0.8 | -65 / +0.6 | +1 / -1.0 | -67 / -0.9 |
| FINE-MEAN-W13-PERF | -13 / +0.2 | -3 / +1.0 | -26 / +0.0 | -4 / -0.1 | -17 / -0.1 |
| FINE-MEAN-W13-CP | -89 / -0.8 | -42 / -0.0 | -42 / +0.1 | -150 / -2.1 | -116 / -2.8 |
| FINE-MEAN-W13-STALE12 | -30 / +0.5 | -74 / +0.8 | -35 / +0.8 | +3 / -0.1 | -22 / +0.2 |
| FINE-MEAN-W26-c1 | -21 / +0.9 | -62 / +1.6 | +4 / +0.7 | +11 / -0.4 | -44 / +1.8 |
| FINE-MEAN-W26-c2 | -11 / +0.8 | -42 / +2.0 | +13 / +0.2 | -1 / -0.4 | -18 / +1.6 |
| FINE-MEAN-W26-c4 | -40 / +0.3 | -74 / +1.3 | -25 / +0.5 | +4 / -0.6 | -70 / +0.1 |
| FINE-MEAN-W26-c13 | -46 / +0.8 | -10 / +1.2 | -31 / -1.5 | +24 / +0.0 | -160 / +3.0 |
| FINE-MEAN-W26-PERF | -38 / +0.6 | -41 / +1.0 | +3 / -2.1 | -11 / -0.2 | -103 / +2.8 |
| FINE-MEAN-W26-CP | -51 / -0.8 | -22 / +0.6 | +6 / -0.3 | +22 / -0.7 | -205 / -2.8 |
| FINE-MEAN-W26-STALE12 | -35 / +1.3 | -26 / +1.2 | +31 / -0.4 | +17 / -0.1 | -163 / +3.0 |

Reading: no cadence is positive vs base for all layers together; the event-driven PERF trigger is the least bad at W13 (-13, because it rarely refits) but not at W26 (-38); quarterly beats weekly at W13 (-41 vs -79) and loses to it at W26 (-46 vs -21): the cadence effect has no consistent sign, which is what noise looks like. The state change-point trigger (CP) is worse than fixed cadence (-89 / -51). Two-weekly, the current practice, is not distinguishable from the others.


**Item 4 - what to refit and shrinkage (W26; shrink = share pulled back to the long-run setting; FINE = whole pool, CHOICE3 = {base, long-run, 2nd}, SIZE = x0.5/1/1.5 on the long-run setting)**

| arm | ALL | cuts | sizing | skips | confluence |
|--|--|--|--|--|--|
| FINE-MEAN-W26-c2 | -11 / +0.8 | -42 / +2.0 | +13 / +0.2 | -1 / -0.4 | -18 / +1.6 |
| FINE-MEAN-W26-sh25 | -20 / +0.9 | -36 / +1.7 | +7 / +0.5 | -5 / -0.8 | -47 / +2.1 |
| FINE-MEAN-W26-sh50 | -28 / +0.9 | -29 / +1.3 | +2 / +0.8 | -8 / -1.2 | -76 / +2.7 |
| FINE-MEAN-W26-sh75 | -36 / +0.9 | -23 / +1.0 | -4 / +0.9 | -11 / -1.6 | -105 / +3.0 |
| CHOICE3-MEAN-W26-sh0 | -24 / +0.3 | -4 / +0.8 | +10 / +0.2 | -16 / -1.3 | -83 / +1.6 |
| CHOICE3-MEAN-W26-sh25 | -29 / +0.5 | -7 / +0.8 | +5 / +0.5 | -16 / -1.4 | -96 / +2.1 |
| CHOICE3-MEAN-W26-sh50 | -34 / +0.6 | -10 / +0.7 | +0 / +0.8 | -16 / -1.6 | -109 / +2.7 |
| CHOICE3-MEAN-W26-sh75 | -39 / +0.8 | -13 / +0.7 | -4 / +0.9 | -15 / -1.8 | -121 / +3.0 |
| CHOICE3-MED-W26-sh0 | -80 / +0.5 | -32 / +0.0 | -45 / +2.2 | -19 / -0.7 | -217 / -0.4 |
| CHOICE3-MED-W26-sh25 | -71 / +0.6 | -28 / +0.2 | -36 / +1.8 | -18 / -1.0 | -197 / +0.6 |
| CHOICE3-MED-W26-sh50 | -62 / +0.7 | -24 / +0.3 | -27 / +1.4 | -17 / -1.4 | -176 / +1.7 |
| CHOICE3-MED-W26-sh75 | -53 / +0.8 | -20 / +0.5 | -18 / +1.0 | -16 / -1.7 | -155 / +2.4 |
| CHOICE3-PLC-W26-sh0 | -0 / -0.0 | -1 / +0.0 | -15 / +0.0 | -13 / -0.1 | +27 / +0.0 |
| CHOICE3-PLC-W26-sh25 | -11 / +0.2 | -5 / +0.2 | -13 / +0.3 | -13 / -0.6 | -13 / +0.9 |
| CHOICE3-PLC-W26-sh50 | -22 / +0.4 | -8 / +0.3 | -12 / +0.7 | -14 / -1.1 | -53 / +1.9 |
| CHOICE3-PLC-W26-sh75 | -33 / +0.7 | -12 / +0.5 | -10 / +0.7 | -14 / -1.6 | -94 / +2.4 |
| SIZE-MEAN-W26-sh0 | -33 / +1.0 | -7 / +1.2 | +26 / +1.4 | -31 / -3.6 | -116 / +3.5 |
| SIZE-MEAN-W26-sh25 | -36 / +1.0 | -9 / +1.0 | +17 / +1.2 | -27 / -3.2 | -121 / +3.5 |
| SIZE-MEAN-W26-sh50 | -39 / +0.9 | -11 / +0.9 | +8 / +1.0 | -23 / -2.8 | -125 / +3.5 |
| SIZE-MEAN-W26-sh75 | -42 / +0.9 | -14 / +0.8 | -0 / +0.8 | -19 / -2.4 | -130 / +3.3 |
| SIZE-MED-W26-sh0 | -90 / +0.8 | -38 / +0.3 | -34 / +1.8 | -44 / -3.6 | -238 / +3.0 |
| SIZE-MED-W26-sh25 | -79 / +0.8 | -32 / +0.4 | -27 / +1.5 | -37 / -3.2 | -212 / +3.2 |
| SIZE-MED-W26-sh50 | -67 / +0.8 | -27 / +0.5 | -21 / +1.2 | -29 / -2.8 | -186 / +3.4 |
| SIZE-MED-W26-sh75 | -56 / +0.9 | -22 / +0.6 | -15 / +0.9 | -22 / -2.4 | -160 / +3.2 |
| SIZE-PLC-W26-sh0 | -20 / +0.4 | -8 / +0.3 | -6 / +0.7 | -16 / -1.2 | -49 / +1.9 |
| SIZE-PLC-W26-sh25 | -26 / +0.5 | -10 / +0.4 | -7 / +0.7 | -15 / -1.4 | -70 / +2.2 |
| SIZE-PLC-W26-sh50 | -32 / +0.7 | -12 / +0.5 | -8 / +0.7 | -15 / -1.6 | -91 / +2.4 |
| SIZE-PLC-W26-sh75 | -38 / +0.8 | -14 / +0.6 | -8 / +0.7 | -15 / -1.8 | -113 / +2.7 |

Reading: at W26 the fine pool (-11) is about as good as the coarse choice of 3 (-24) and the x0.5-1.5 size choice (-33); at W13 the coarse choice (-51) beats fine (-79), so coarse helps where the window is short and noisy and does not where it is long. Shrinkage toward the long-run setting moves the result monotonically toward the long-run pick (LONGRUN -44), i.e. it HURTS at W26 (FINE -11 at 0% to -36 at 75%) because the long-run pick is worse than the recent pick on this pool; for the placebo-gated rule 0% shrink looks best (it simply stays on base). Size multipliers help in the sizing family only (+26 at W26, inside the RANDOM p95 of +79) and cost -31..-116 in skips/confluence. So coarse choices and shrinkage reduce variance but do not create a gain over frozen.


**Item 5 - how to select (same pool; mean / DD / median of 4-week sums / worst 4-week sum / beats-placebo t>1.65)**

| arm | ALL | cuts | sizing | skips | confluence |
|--|--|--|--|--|--|
| FINE-MEAN-W26-c2 | -11 / +0.8 | -42 / +2.0 | +13 / +0.2 | -1 / -0.4 | -18 / +1.6 |
| FINE-DD-W26-c2 | +6 / +0.1 | +10 / +0.1 | -5 / +0.0 | +9 / +0.0 | +10 / +0.2 |
| FINE-MED-W26-c2 | -74 / +0.1 | -84 / +0.4 | -67 / +0.9 | -39 / -0.7 | -108 / -0.3 |
| FINE-WORST-W26-c2 | -2 / +0.0 | +0 / +0.0 | -6 / +0.0 | -14 / +0.0 | +12 / +0.0 |
| FINE-PLC-W26-c2 | -8 / -0.0 | -17 / +0.0 | -18 / +0.0 | -13 / -0.1 | +16 / +0.0 |
| FINE-MEAN-W13-c2 | -79 / -0.2 | -100 / +1.3 | -20 / -0.9 | -75 / -1.3 | -123 / -1.6 |
| FINE-DD-W13-c2 | +4 / +0.3 | +4 / +1.0 | +1 / +0.0 | +6 / +0.0 | +6 / +0.2 |
| FINE-MED-W13-c2 | -102 / -0.2 | -77 / +1.2 | -27 / +0.4 | -18 / -1.1 | -282 / -1.2 |
| FINE-WORST-W13-c2 | -5 / -0.3 | -43 / +0.0 | -23 / +0.0 | +9 / +0.0 | +30 / -1.0 |
| FINE-PLC-W13-c2 | +1 / +0.0 | -17 / +0.0 | -2 / +0.0 | -7 / +0.0 | +27 / +0.0 |

Reading: raw trailing mean at W26 is middling (-11); the median-of-sub-windows rule is clearly worse (-74); drawdown-gated (+6), worst-window (-2) and beats-placebo (-8) rules sit at zero because they mostly revert to the unchanged setting. Ranking on mean for the whole pool: DD (+6) > WORST (-2) > PLC (-8) > MEAN (-11) > MED (-74). None is distinguishable from frozen (paired block CI contains 0), so selection by raw trailing mean is not the cause of the shortfall at W26; no selection beats frozen on this pool.


## 6. 'Now' as market conditions, not the calendar

Weekly state vector (rc_state.py, th_state 1-second NQ mid, 935 days to 2026-11-11): realised volatility (sqrt sum of squared 1-min log returns), range, trend efficiency (|net|/path), chop share (5-min sign reversals), overnight share of range (before 09:30 ET), event load (event_flags n_asia+n_london+n_pre); index correlation was built (10-day NQ vs ES/RTY/YM) but the price store ends 2026-10-16 so it is not used. z-scored on an expanding window. SIM = the K past weeks closest to the last 2 weeks, choose the candidate with the best NEXT-week delta in those weeks; SIMREC = similarity x exponential recency.

| arm | ALL | cuts | sizing | skips | confluence |
|--|--|--|--|--|--|
| FINE-MEAN-W26-c2 | -11 / +0.8 | -42 / +2.0 | +13 / +0.2 | -1 / -0.4 | -18 / +1.6 |
| FINE-EXP-hl13-c2 | -67 / +0.8 | -31 / +1.0 | -7 / +0.6 | -13 / -0.6 | -211 / +1.3 |
| FINE-SIM-K8 | -79 / +0.5 | -97 / -1.1 | -76 / -0.7 | -11 / -0.9 | -136 / +2.6 |
| FINE-SIM-K12 | -84 / -0.4 | -30 / -0.4 | -77 / -2.3 | +5 / -0.9 | -227 / +0.5 |
| FINE-SIM-K20 | -87 / +0.5 | -131 / -0.5 | -47 / -1.4 | +44 / -0.9 | -221 / +3.2 |
| FINE-SIMREC-hl13 | -96 / +0.1 | -60 / +1.3 | -82 / -1.1 | -15 / -1.3 | -222 / +1.3 |
| FINE-SIMREC-hl26 | -67 / +0.4 | -40 / +0.8 | -51 / -1.3 | -18 / -2.0 | -157 / +3.0 |
| FINE-SIMREC-hl52 | -40 / +0.7 | -40 / +0.8 | -64 / -0.3 | +1 / -1.6 | -58 / +3.0 |

Reading: similarity selection (K 8-20 nearest weeks) is worse than calendar-recent W26 for all layers together (-79..-87 vs -11), with a single skips cell above RANDOM-p95 (K20 +44 vs p95 +40; 1 of about 40 similarity cells, chance level); similarity x recency with a 52-week half-life ends at -40 (the long-run pick is -44). No state-conditioned selection beats frozen or the random band.


## 7. Regime-switch detection

A 'switch' = week where the best candidate by trailing-13-week mean changes in a cohort (arena A): 656 switches. Change-point detector = |mean z(rv or eff) of the last 2 weeks - mean of the 8 weeks before| > 1.75 (fires in 20 of 135 weeks). Probability a detector firing occurred in the 4 weeks BEFORE a switch: 28% vs 30% for any week and 30% (p95 36%) for circularly shifted switch dates (p = 0.71). **The market-state change-point does not announce changes in the best setting** (same as chance). The detector-triggered refit (FINE-MEAN-W*-CP) is in the cadence table and is not better than fixed cadence; switches of the trailing-best setting are mostly flips between near-equal candidates.


## 8. THE GATE: shelved recent-only rules, strict vs tolerant (side by side)

Definitions (weekly basis, base lots, stored exact runs; windows by week Monday: L1M 2026-10-05.., L3M 2026-08-03.., L6M 2026-05-04.., HOLD 2025-11-03.., PRE 2024-02-05..2025-06-30, X' 2023-04-03..2024-01-29, GAP 2025-07-07..2025-10-27; all end 2026-10-30).
- STRICT: every older window run (PRE, X', GAP) has delta mean >= 0 and DD cut >= 0, and L3M/L6M/HOLD delta mean > 0.
- TOLERANT (the proposal in the order): each older window DD <= 1.10 x the reference DD and mean >= 0.95 x the reference mean; L3M, L6M and HOLD delta mean > 0 and DD cut > 0; and the recent window beats the placebo p95 (random day skips/half-days of 5-30% on JN05W2 in the same window: mean-delta p95 and DD-cut p95 in gate_band.csv) on mean or DD cut.
- Status is UNRESOLVED when no older window exists for the set yet (cell not run beyond 12-21 months): the box does not guess.
- Persistence = the rule's own weekly delta series: P(next-H mean delta > 0 | trailing-W > 0) vs base rate vs shuffled time (300 circular shifts); bar 60%.

| rule | set | base | dMean L3M/L6M/HOLD $/wk | DD cut% L3M/L6M/HOLD | older windows run | dMean PRE/X'/GAP | DD cut% PRE/X'/GAP | STRICT | TOLERANT |
|--|--|--|--|--|--|--|--|--|--|
| A half-size (SM_A6_halfNP7 = TL3_EA_A6) | TL3_EA_A6 | JN05W2 | -886 / 601 / 635 | 11.8 / 11.8 / 11.6 | X',PRE,GAP | -75 / 243 / -828 | -7.6 / 7.8 / 2.3 | FAIL | FAIL |
| London range LS1 | TL3_LR_LS1 | JN05W2 | 2,878 / 1,765 / 468 | 13.9 / 13.9 / -3.7 | GAP |  /  / -1,634 |  /  / 8.6 | FAIL | FAIL |
| London range LS125 | TL3_LR_LS125 | JN05W2 | 4,022 / 2,402 / 784 | 11.8 / 11.8 / 2.7 | GAP |  /  / -1,113 |  /  / 4.4 | FAIL | FAIL |
| M7 London CAP3 | TL3_RA_CAP3 | JN05W2 | -2,258 / -2,178 / -596 | 3.9 / 3.9 / 6.5 |  |  /  /  |  /  /  | UNRESOLVED (no older window run) | UNRESOLVED (no older window run) |
| M7 London CAP2 | TL3_RA_CAP2 | JN05W2 | -5,112 / -5,269 / -2,863 | -36.9 / -36.9 / 7.5 |  |  /  /  |  /  /  | UNRESOLVED (no older window run) | UNRESOLVED (no older window run) |
| M7 BLKiv | TL3_RA_BLKiv | JN05W2 | -2,958 / -3,666 / -867 | -17.1 / -17.1 / 19.4 |  |  /  /  |  /  /  | UNRESOLVED (no older window run) | UNRESOLVED (no older window run) |
| K7 flat -40 | EC_FLAT40K | LPB_EMPTY | -824 / 218 / 154 | -7.8 / -7.8 / -6.2 | X',PRE | -1,041 / 720 /  | 6.2 / 9.0 /  | FAIL | FAIL |
| A7 flat -40 | EC_FLAT40A | LPB_EMPTY | 2,923 / 661 / -30 | 1.2 / 1.2 / -1.9 | X',PRE | -225 / 381 /  | -2.1 / 5.6 /  | FAIL | FAIL |
| CF P7 Asia all-5 (K) | TL3_CF_G_P7A_V0all5_K | JN05W2 | -4,333 / -8,663 /  | -4.5 / -4.5 /  |  |  /  /  |  /  /  | UNRESOLVED (no older window run) | UNRESOLVED (no older window run) |
| CF P7 Asia all-5 (S15) | (not on box) |  |  /  /  |  /  /  |  |  /  /  |  /  /  | cell not on box (months missing) | cell not on box (months missing) |
| CF P7 Asia all-5 (S2) | TL3_CF_G_P7A_V0all5_S2 | JN05W2 | 1,197 / -3,848 /  | -8.2 / -8.2 /  |  |  /  /  |  /  /  | UNRESOLVED (no older window run) | UNRESOLVED (no older window run) |
| CF K7 Asia V0>=4 (K) | (not on box) |  |  /  /  |  /  /  |  |  /  /  |  /  /  | cell not on box (months missing) | cell not on box (months missing) |
| CF SL2 P7 Asia >=4 (K) | TL3_CF_G_P7A_SL2ge4_K | JN05W2 |  /  /  |  /  /  |  |  /  /  |  /  /  | UNRESOLVED (no older window run) | UNRESOLVED (no older window run) |
| BLK_M30 | TL3_PR_BLK_M30 | JN05W2 | 1,223 / 1,444 / 643 | 15.6 / 15.6 / -9.6 | X',PRE | -284 / -109 /  | 0.5 / -6.5 /  | FAIL | FAIL |
| U7 time stop B (T15D10) | TL3_EB_U7F_T15D10 | JN05W2 | 998 / 916 / 679 | 11.7 / 11.7 / 3.3 | X',PRE | -93 / 249 /  | -1.0 / 18.0 /  | FAIL | PASS on available older windows only: X',PRE |


**Measured persistence of each rule's own weekly delta (W,H in weeks; 4,4 = 1m->1m; 13,13 = 3m->3m; 26,13 = 6m->3m)**

| rule | W | H | n_origins | eff_indep | P next-H pos % | base % | shuffled % | p_vs_shift |
|--|--|--|--|--|--|--|--|--|
| A half-size (SM_A6_halfNP7 = TL3_EA_A6) | 4 | 4 | 182 | 45.5 | 51.6 | 48.9 | 47.5 | 0.2 |
| A half-size (SM_A6_halfNP7 = TL3_EA_A6) | 13 | 13 | 164 | 12.6 | 51.6 | 54.3 | 50.5 | 0.4 |
| A half-size (SM_A6_halfNP7 = TL3_EA_A6) | 26 | 13 | 151 | 5.8 | 57.8 | 56.3 | 52.2 | 0.4 |
| A half-size (SM_A6_halfNP7 = TL3_EA_A6) | 13 | 4 | 173 | 13.3 | 51.0 | 46.8 | 44.9 | 0.2 |
| London range LS1 | 4 | 4 | 64 | 16.0 | 50.0 | 53.1 | 58.2 | 0.6 |
| London range LS1 | 13 | 13 | 46 | 3.5 | 26.7 | 54.3 | 47.7 | 0.7 |
| London range LS1 | 26 | 13 | 33 | 1.3 | 16.7 | 57.6 | 100.0 | 1.0 |
| London range LS1 | 13 | 4 | 55 | 4.2 | 58.3 | 58.2 | 69.1 | 0.6 |
| London range LS125 | 4 | 4 | 62 | 15.5 | 39.3 | 51.6 | 56.6 | 0.8 |
| London range LS125 | 13 | 13 | 44 | 3.4 | 27.3 | 52.3 | 58.2 | 0.8 |
| London range LS125 | 26 | 13 | 31 | 1.2 | 33.3 | 58.1 |  |  |
| London range LS125 | 13 | 4 | 53 | 4.1 | 50.0 | 52.8 | 60.8 | 0.6 |
| M7 London CAP3 | 4 | 4 | 45 | 11.2 | 36.4 | 40.0 | 39.5 | 0.5 |
| M7 London CAP3 | 13 | 13 | 27 | 2.1 | 13.3 | 22.2 |  |  |
| M7 London CAP3 | 13 | 4 | 36 | 2.8 | 33.3 | 38.9 | 32.2 | 0.6 |
| M7 London CAP2 | 4 | 4 | 45 | 11.2 | 30.8 | 20.0 | 16.9 | 0.2 |
| M7 London CAP2 | 13 | 13 | 27 | 2.1 | 0.0 | 0.0 |  |  |
| M7 London CAP2 | 13 | 4 | 36 | 2.8 | 20.0 | 8.3 | 8.2 | 0.0 |
| M7 BLKiv | 4 | 4 | 45 | 11.2 | 30.8 | 22.2 | 21.5 | 0.2 |
| M7 BLKiv | 13 | 13 | 27 | 2.1 | 18.8 | 25.9 |  |  |
| M7 BLKiv | 13 | 4 | 36 | 2.8 | 25.0 | 25.0 | 13.8 | 0.1 |
| K7 flat -40 | 4 | 4 | 159 | 39.8 | 53.7 | 49.1 | 47.6 | 0.2 |
| K7 flat -40 | 13 | 13 | 123 | 9.5 | 40.0 | 43.9 | 40.1 | 0.4 |
| K7 flat -40 | 26 | 13 | 97 | 3.7 | 43.2 | 36.1 | 31.5 | 0.3 |
| K7 flat -40 | 13 | 4 | 141 | 10.8 | 42.0 | 46.1 | 44.6 | 0.6 |
| A7 flat -40 | 4 | 4 | 159 | 39.8 | 54.2 | 46.5 | 44.6 | 0.0 |
| A7 flat -40 | 13 | 13 | 123 | 9.5 | 58.7 | 35.8 | 27.9 | 0.1 |
| A7 flat -40 | 26 | 13 | 97 | 3.7 | 42.2 | 32.0 | 31.9 | 0.3 |
| A7 flat -40 | 13 | 4 | 141 | 10.8 | 66.7 | 48.2 | 44.5 | 0.1 |
| BLK_M30 | 4 | 4 | 170 | 42.5 | 35.4 | 30.0 | 26.4 | 0.2 |
| BLK_M30 | 13 | 13 | 134 | 10.3 | 35.7 | 38.8 | 32.5 | 0.4 |
| BLK_M30 | 26 | 13 | 108 | 4.2 | 40.0 | 40.7 | 36.3 | 0.4 |
| BLK_M30 | 13 | 4 | 152 | 11.7 | 40.4 | 30.9 | 27.2 | 0.0 |
| U7 time stop B (T15D10) | 4 | 4 | 161 | 40.2 | 47.5 | 50.9 | 50.0 | 0.6 |
| U7 time stop B (T15D10) | 13 | 13 | 125 | 9.6 | 52.9 | 52.8 | 51.2 | 0.4 |
| U7 time stop B (T15D10) | 26 | 13 | 99 | 3.8 | 45.5 | 52.5 | 47.8 | 0.5 |
| U7 time stop B (T15D10) | 13 | 4 | 143 | 11.0 | 48.3 | 48.3 | 45.8 | 0.4 |

No gated rule has persistence above 60% with at least 5 independent observations. A7 flat -40 reaches 67% at W13->H4 (base 48%, shuffled 44%, p 0.11, eff n 10.8) and 59% at 3m->3m (base 36%, p 0.10, eff n 9.5), the highest of the set, but both miss the 0.05 bar and its level fails the strict test (L6M +$661, HOLD -$30, PRE -$225, X' +$381 vs LPB_EMPTY; DD cut +1.2/-1.9/-2.1/+5.6%). The half-size rule A is the closest to the user's standard on the DD side (L1M/L3M/L6M/HOLD DD cut 11.6-11.8%, X' +7.8%, GAP +2.3%) but its L3M mean is -$886/wk (L6M +$601, HOLD +$635), PRE DD 7.6% deeper (within the 10% tolerance) and mean in the GAP window -$828/wk (about -8% of the reference: fails the -5% tolerance); its persistence is 52-59% against 49-57% base (p 0.27-0.44): no. The London range rule LS1/LS125 is strongly positive recently (L3M +$2.9k/+$4.0k, L6M +$1.8k/+$2.4k, DD cut 12-14% in L3M/L6M) but the GAP window (2025-07..10, -$1.6k/-$1.1k per week, branch A K7/U7 trades) fails both readings and PRE/X' are not yet run. M7 London caps are unresolved (older windows not run; recent: CAP3 -$2.2k/wk mean, DD cut +3.9%; CAP2/BLKiv negative DD). The recent-only confluence cells exist only for 12 months (L6M/L3M window): P7 Asia all-5 L6M -$8.7k/wk (negative), L3M negative; unresolved/fail. BLK_M30 and the U7 time stop B pass the recent side (L3M/L6M/HOLD positive; BLK_M30 L3M +$1.2k, DD cut 15.6%; U7B L3M +$1.0k, DD cut 11.7%) and the older X'/PRE windows by the tolerant test; the GAP window is not run, so 'PASS on available older windows only'. The U7 time stop B is the only shelved rule that clears the tolerant reading on everything that has been run; its persistence is 44-52% vs base 48-52% (no better than coin), so the case for it rests on the level (positive in X' +$249, PRE -$93, L6M +$916), not on recency.


## 9. The whole method walked forward

Arms: (i) FROZEN long-run = BASE (JN05W2 as run) and LONGRUN (expanding best), (ii) TODAY'S METHOD = rolling 26-week trailing-mean pick, refit every 2 weeks (FINE-MEAN-W26-c2; the W-RF/DS3_REFIT_1122 design in first-order form), (iii) RANDOM = random pick each refit (mean and p95 of 100 draws), BEST COMBINATION from items 2-7 = the arm of the grid with highest mean among those with DD cut >= 0 (reported with its identity: it is a placebo-gated/DD-gated arm that mostly stays frozen).


**Layer cohorts (arena A: 27 family x book cohorts, mean over cohorts)** (mean $/wk vs JN05W2, DD cut of the stack proxy, by year, since 2026-05)

| arm | mean_per_wk | ddcut_pct | y2024 | y2025 | y2026 | since_2026_05 | ddcut_since_2026_05 |
|--|--|--|--|--|--|--|--|
| BASE = frozen JN05W2 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 |
| LONGRUN (expanding best) | -44.4 | 0.9 | -40.2 | -44.5 | -48.3 | -58.9 | 1.4 |
| FROZEN at first refit | -143.1 | -1.3 | -108.8 | -111.6 | -213.1 | -208.8 | 1.8 |
| today's method (trail 26w mean, 2-weekly) | -11.2 | 0.8 | 23.0 | -21.2 | -30.9 | -73.0 | 2.2 |
| RANDOM mean of 100 | -69.8 | -1.0 | -50.5 | -63.6 | -95.1 | -93.8 | 1.3 |
| RANDOM p95 | -22.1 | 0.5 | 35.7 | 0.2 | 17.9 | 67.0 | 2.5 |
| BEST COMBINATION = FINE-DD-W26-c2 | 5.9 | 0.1 | -2.7 | 15.4 | 2.4 | -3.5 | 0.0 |


**WHOLE STACK (arena S: ONE cohort of every complete 43-month full-stack set, delta vs JN05W2; each realised week is an exact-engine week of the chosen set, splice not re-simulated)** (mean $/wk vs JN05W2, DD cut of the stack proxy, by year, since 2026-05)

| arm | mean_per_wk | ddcut_pct | y2024 | y2025 | y2026 | since_2026_05 | ddcut_since_2026_05 |
|--|--|--|--|--|--|--|--|
| BASE = frozen JN05W2 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 |
| LONGRUN (expanding best) | -668.7 | 0.3 | -2,051.7 | -16.6 | -170.9 | 603.8 | 25.0 |
| FROZEN at first refit | -3,060.2 | -27.8 | -2,056.0 | -1,564.9 | -5,802.6 | -5,949.3 | -74.5 |
| today's method (trail 26w mean, 2-weekly) | -971.5 | -1.0 | -110.9 | -1,533.2 | -1,092.9 | -501.9 | 1.1 |
| RANDOM mean of 100 | -639.8 | -12.7 | -464.1 | -466.6 | -1,012.9 | -1,104.5 | -11.3 |
| RANDOM p95 | 254.0 | 3.2 | 769.9 | 835.4 | 903.7 | 1,567.9 | 21.2 |
| BEST COMBINATION = FINE-PLC-W52-c2 | 39.0 | 0.0 | 1.8 | 0.0 | 120.9 | 200.0 | 16.0 |


Reading. Drawdown first: no layer-level arm changes the full-history drawdown of the stack proxy by more than about +-2% (BASE 0; today's method +0.8%; best arm +0.1%); the stack-level cohort swings -28..+25% but those swings come from one or two weeks (the 2026 drawdown week W44 and 2024-25 giveback weeks) and change sign by period (FROZEN-at-first-refit -28% over 43 months, LONGRUN +0.3%). Mean second, layers: today's method (26-week trailing mean, two-weekly) is +$23/wk in 2024, -$21 in 2025, -$31 in 2026 and -$73 per week since 2026-05 against frozen JN05W2 (block CI over 2024-04..2026-10: -60..+58, a tie), better than random picks (-70) and than the long-run pick (-44) but not better than frozen. A setting chosen once on the first 52 weeks (FROZEN at first refit) loses $143/wk afterwards: the pool's in-sample winner does not hold up, which is the cleanest sign that fine selection chases noise. Whole stack (arena S): today's method -$972/wk (-$502 since 2026-05), random -$640, long-run pick -$669 (+$604/wk and DD cut 25% since 2026-05, i.e. it is carried by the recent drawdown weeks and loses -$2.1k/wk in 2024), best gated arm +$39/wk (+$200 since 2026-05, DD cut 16%, which is the PLC rule switching to a single set for a few months). Nothing is consistent across 2024, 2025, 2026 and the months since 2026-05, which is the test of an information source. The weekly splice of the stack-level walk uses exact-engine weeks of the chosen set, positions across a splice are not re-simulated; a TL3_RE exact re-run is not queued because the best combination is the frozen setting (nothing to assemble); /mnt/l2/l2vast/_recents/pending.txt is empty.


## Per-family answer (item "nothing is not a deliverable")

| family | does recency carry information? | answer |
|--|--|--|
| cuts (TL3_PM/LA/EB, EC_FLAT, JN04RM_FLAT) | Weak hint, below the bar: book P 17-41% vs base 17-41%; stack-level 22-51% vs base 32-48%; the only real cells with p<0.05 vs shuffled (6 of 36, +2..+4 points) are here, but nonsense shows the same artefact (8 of 60); walk-forward W26 -42, W52 -15, DD-gated +10 (all inside the random band) | FROZEN current cut settings; no refit on recency |
| sizing (TL3_EA/RA, SM_A6, RC*) | No: book P 25-42% vs base 26-43%, shuffled 31-52%; stack 32-48% vs 37-45%; walk-forward W26 +13 inside RANDOM p95 (+79) | FROZEN lot tables / caps |
| skips (TL3_LR/NT/RU/CH/PR/JV) | No: book 29-47% vs shuffled 32-53%; stack 45-53% vs base 41-51%; walk W26 -1 | FROZEN |
| brackets (TL3_D9/D10/R2/TD) | No: book 28-48%; stack-level 38-68%, the two cells at >= 60% (3m->3m 63%, 6m->3m 68%) have 2.8 and 0.5 independent observations and equal or sit below the shuffled placebo (66% / 40%); no 43-month cohort for the walk | FROZEN |
| session books | not measurable: no session-book cohort with a complete history on JN05W2 base | FROZEN until a 43-month cohort exists |
| confluence conditions (TL3_CF/UW/TK) | No: book 22-42% vs base 23-42%, shuffled 30-46%; stack 36-50% vs base 41-47%; walk W26 -18, placebo-gated +16 (inside band); the recent-only P7-Asia cells are negative at L6M | FROZEN |


## 10. Follow-ups after the first page (2026-11-15 evening)

- **RE4 (W44 artefact?) - NOT supported as stated.** Stack-level arms since 2026-05 stay positive with the W44 week removed (long-run pick +$265/wk vs +$604 with W44, DD cut 28% vs 25%; SIMREC hl52 +$547 vs +$875; CHOICE3-MEAN-W26 +$1,203 vs +$1,506), while 62 of 97 arms are positive with W44 and 52 of 97 without. But over the full 43 months the same arms are negative (long-run pick -$669/wk, SIMREC -$555) and today's method is -$537 since 2026-05 with W44 removed: a 24-week window (about 8 independent blocks) in which a few sets were better is not evidence that choosing by recency helps; the picks that won since 2026-05 lost in 2024-25. (re4.csv)
- **RE5 (cuts lift holds out of sample?) - NOT supported.** Selecting with data to 2024-12 and testing 2025-01..2026-10: stack-level cuts lift vs shuffled time +7.2 points in 2024 and +2.5 in 2025+ (0 of 6 cells p<0.05 in 2025+); book-level cuts +2.6 in 2024, -3.0 in 2025+ (0 of 6). Nonsense with 100 seeds: lift about 0 (-1.5..+0.6). The weak cuts hint disappears out of sample. (re5.csv)
- **Live-cap robustness (cohort rerun with dollars rebuilt from books).** All-books x1.75 and P7 x1.75 with the other books at x1 (stress of the P7 14,700 vs 8,400 cap ratio), stack-level scope, 35 cells each: P changes by -0.02 on average (range -0.12..+0.03); cells >= 60%: 2 and 1 (the same stack-level brackets cells with 0.5-2.8 independent observations, 65% / 59%); cells with p<0.05 vs shuffled: 2 and 2 (cuts, +1..+9 points, P 45-50%). Positivity and ranks are invariant to a uniform x1.75; the only change comes from reweighting books, and it leaves the conclusion unchanged. A cap-binding nonlinearity (lot rounding, day caps) needs the engine and is not simulated. (livecap.csv)
- **RE6 (DD-gated rule out of sample to 11-11) - pending.** Needs the November exact months. W-EV: queue under own tags via `cd outputs/code; python3 -I th_engfix/ev_store_launch.py <driver args>` only after its 'STORE READY' message (store rebuild of 11-12/11-13 in progress); not queued yet. Price store: ES/RTY/YM 1m bars to 11-13 exist in data/ext_20261113 and raw/tail_20261114; daily closes for 10-16..11-10 are still to be built.
- **Tooling.** `stamp_enddate.py` stamps 'data ends YYYY-MM-DD' on a verdict line; `rc_enddate.py` runs hourly (loop pid in /mnt/l2/l2vast/_recents/enddate_loop.pid). The tolerant-pass list (B = U7 time stop B only) is in DS3_V20_BUILD_LIST.md (via W-JV). The CF_G confluence cells were referred to W-CF3 for X'/PRE/GAP/202611.


## Open items, honest limits

- Windows end 2026-10-30; November exact months pending (section 0). Re-run takes minutes after extraction.
- The pool consists of the shelved/tested variants, most of which are worse than base on mean by construction (they are cuts/skips that trade mean for drawdown); so 'the best pick is base' is partly a property of the pool. The test that matters is relative: raw recent-mean selection vs random and vs stale selection, and there it shows no information.
- Arena A has no brackets/session-book cohorts with a complete 43-month stretch; arenas B (since 2025-07) and C (since 2025-11) are in walk_B.csv / walk_C.csv, same conclusion (nothing beats RANDOM-p95 except 1-4 gated arms of <= $61/wk).
- Weekly series mean differs slightly from other pages' window means (week boundaries; Monday-start weeks; DD checks agree with W-EA's A6 table to the decimal: L3M/L6M 11.8%, HOLD 11.6%, PRE -7.6%, X' 7.8%, GAP 2.3%).
- Hypothesis ledger: H0xx-RE1 (no recency information once long-run quality held fixed): SUPPORTED; H0xx-RE2 (slow/coarse/risk-side persists): NOT supported (cuts at W6m-12m->3m reach 37-38% only); H0xx-RE3 (placebo/median selection with 50% shrinkage beats raw mean): PARTLY - placebo/DD/worst gating beat raw mean but only by staying on base.
