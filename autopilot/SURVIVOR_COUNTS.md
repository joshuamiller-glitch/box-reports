# SURVIVOR_COUNTS - rule-based shortlist, no top-N (W-SHORT, order 1845Z), refreshed 2026-11-18 19:08Z

THRESHOLDS (equal risk; stop = clip(bracket multiple x row bar unit, 10, 120), plain 60/60 = 60; R = points / stop): R1 last 26 weeks (L6M) positive; R2 >= 100 trades in L6M; R3 last 13 weeks (L3M) positive; R4 persistence > 0.60 = share of 2-week windows since 2023-10 with positive P&L; R5 prior years 2023 / 24 / 25: R per week more than 30% below the cell's own L6M R per week = RED (shown, NOT delivered as a pick), 15-30% = AMBER (passes, flagged); R6 trust (brute-force tape walk) + look-ahead (6 truncation cuts) + fills >= signal + 1 s = run on every passing cell in phase 2, best first (about 5-20 CPU-s per cell; counts below are BEFORE R6). A cell gets the FIRST rule it fails; every evaluated cell stays on disk with its reason.
W-GRIDOPS: no threshold differs from the 1845Z order. R4 = 0.60 strict (> 0.60). L3M and L6M are on net points after $4.84, equal-risk R has the same sign.

RANKING VARIANTS: bare = the grid result as scored (no account rule). OWN-STOP (cell's own bad-day stop, N = 2 stops, 1.5 / 3 neighbours) and current-stack MASK (JL3 DAY-DONE day state) are W-DAYMASK arrays that exist for only ~1,600-1,800 (row, module) pairs so far (cache_os2 / cache_acct); the full-grid arrays are produced by the phase-1 scoring (GL_OWNSTOP). Until they exist the OWN-STOP / MASK / difference counts cannot be computed: shown as n/a, not zero. The bare counts below are PROVISIONAL (the grid is partitioned over servers and each server sees only its own finished results until W-S3 merges them; counts from server 2 only, data week 189).

FAMILIES: passing cells are linked into one family when they are the same module.variant on an adjacent bar size of the same bar type (grid size neighbours), an adjacent parameter of the same variant (grid parameter neighbours), or the identical parameter with another bracket / side; family = connected component of that graph. Best member (highest min(L6M R/wk, weakest prior-year R/wk)) is run first by the engine, the other members are listed after it with their screen numbers; nothing is dropped.

## Asia
- cells evaluated (server-2 results, data week 189): 4,386,735
- PASS R1-R5, bare: **2,992** cells in **1,890 families** (non-reversal bars 2099, reversal 835, other 58; level / S-D modules 1061)
- PASS on OWN-STOP: n/a (arrays not built for the full grid) | PASS on current-stack MASK: n/a | pass own-stop but not mask / mask but not own-stop: n/a
- FAIL (first rule failed): R1 L6M<=0: 2,375,203; R2 trades<100: 960,658; R3 L3M<=0: 345,052; R4 persistence<=0.60: 622,303; R5 RED prior year (shown, not delivered): 80,527
- AMBER prior year(s) (passing, flagged): 571 | trust fail / look-ahead fail: not run yet (R6 is phase 2; sample audit of 48 shortlisted cells: 47 pass, 1 look-ahead fail)
- on-disk file with every cell and its reason: server 2 /mnt/l2/l2vast/_grid/rule/bare_Asia.parquet (+ pass_bare_Asia.csv = passing cells with family id, family order, rank in family)

## London
- cells evaluated (server-2 results, data week 189): 4,397,570
- PASS R1-R5, bare: **1,035** cells in **808 families** (non-reversal bars 746, reversal 233, other 56; level / S-D modules 349)
- PASS on OWN-STOP: n/a (arrays not built for the full grid) | PASS on current-stack MASK: n/a | pass own-stop but not mask / mask but not own-stop: n/a
- FAIL (first rule failed): R1 L6M<=0: 2,458,413; R2 trades<100: 1,125,318; R3 L3M<=0: 268,528; R4 persistence<=0.60: 498,770; R5 RED prior year (shown, not delivered): 45,506
- AMBER prior year(s) (passing, flagged): 216 | trust fail / look-ahead fail: not run yet (R6 is phase 2; sample audit of 48 shortlisted cells: 47 pass, 1 look-ahead fail)
- on-disk file with every cell and its reason: server 2 /mnt/l2/l2vast/_grid/rule/bare_London.parquet (+ pass_bare_London.csv = passing cells with family id, family order, rank in family)

## NYAM
- cells evaluated (server-2 results, data week 189): 4,828,997
- PASS R1-R5, bare: **9,504** cells in **4,556 families** (non-reversal bars 6560, reversal 2430, other 514; level / S-D modules 5157)
- PASS on OWN-STOP: n/a (arrays not built for the full grid) | PASS on current-stack MASK: n/a | pass own-stop but not mask / mask but not own-stop: n/a
- FAIL (first rule failed): R1 L6M<=0: 2,839,937; R2 trades<100: 755,347; R3 L3M<=0: 367,009; R4 persistence<=0.60: 788,984; R5 RED prior year (shown, not delivered): 68,216
- AMBER prior year(s) (passing, flagged): 1565 | trust fail / look-ahead fail: not run yet (R6 is phase 2; sample audit of 48 shortlisted cells: 47 pass, 1 look-ahead fail)
- on-disk file with every cell and its reason: server 2 /mnt/l2/l2vast/_grid/rule/bare_NYAM.parquet (+ pass_bare_NYAM.csv = passing cells with family id, family order, rank in family)

## NYPM
- cells evaluated (server-2 results, data week 189): 4,842,376
- PASS R1-R5, bare: **531** cells in **396 families** (non-reversal bars 401, reversal 86, other 44; level / S-D modules 112)
- PASS on OWN-STOP: n/a (arrays not built for the full grid) | PASS on current-stack MASK: n/a | pass own-stop but not mask / mask but not own-stop: n/a
- FAIL (first rule failed): R1 L6M<=0: 2,596,024; R2 trades<100: 1,163,063; R3 L3M<=0: 294,813; R4 persistence<=0.60: 773,890; R5 RED prior year (shown, not delivered): 14,055
- AMBER prior year(s) (passing, flagged): 116 | trust fail / look-ahead fail: not run yet (R6 is phase 2; sample audit of 48 shortlisted cells: 47 pass, 1 look-ahead fail)
- on-disk file with every cell and its reason: server 2 /mnt/l2/l2vast/_grid/rule/bare_NYPM.parquet (+ pass_bare_NYPM.csv = passing cells with family id, family order, rank in family)

