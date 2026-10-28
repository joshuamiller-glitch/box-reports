# DS3_SDISC_3 - session structure as the signal (T-SESSION-DISCOVER item 3), agent D3SD34, 2026-10-28
Research only; no live, execution-server or chart change; UNTOUCHED never read. Prereg l2vast/ds3/prereg/SD34_prereg.md sha256 c1e96d730a2d1b2c0bbd39f3bfb08ff0ea921c5a03b98a63b309cc5a491f61e1 (DECISIONS.md, before any P&L). PREHOLD autopilot/DS3_SDISC_34_PREHOLD.md (sha256 85eda956e4183927d7a9619cb1c4d65c2a49543b53a0daaf73876a9b6cacfba5 of out/sd34/PREHOLD.json). One HOLD+X look, logged out/sd34/looks.jsonl. Code l2vast/ds3/code/sd34/, outputs l2vast/ds3/out/sd34/.

## VERDICT
- **480 event sets x 9 brackets = 4,320 cells, 3762 cell-sessions with PRE n >= 100 (F = 3,762); 48 PRE-selected (PRE n>=100, MEAS mean>0, effect CI > 0 vs the random-in-session placebo); 0 clear best-of-F (Bonferroni p x 3,762 < 0.05; best PRE effect t = 3.49).** If the 3,762 cells were independent noise, about 94 (2.5%) would pass the effect-CI gate; 48 pass (45 after removing identical-entry clones), i.e. the PRE gate does not pass more cells than chance would, although the cells are strongly correlated (shared levels, bars, brackets) so this is a rough guide only.
- **HOLD (one look, 78 cell-sessions: 45 PRE-selected + top-10 per session + top-5 gating): 3 SESSION-CANDIDATE, 0 SESSION-PASS** (candidate = PRE-selected, HOLD MEASURED mean > 0, both HOLD halves > 0). Candidates: SOPEN|own|LONDON|EX|k1|1m|40/40 [LONDON]; PRNG|LONDON|NY-AM|BC|p0|1m|60/60 [NY-AM]; PRNG|LONDON|NYKZ|BC|p0|1m|30/60 [NY-AM]. **All 3 have a NEGATIVE 2023-span (X) MEASURED mean and a HOLD MDE of 12 pts or more**: they are leads, not books.
- Of the 45 PRE-selected cells, 38 are negative in HOLD on MEASURED (median HOLD mean -2.55), 4 more are HOLD-positive but fail one HOLD half (NEAR). The decay PRE -> HOLD is the signature of selection on noise plus the MEASURED haircut (stop slip + P9 target correction).
- The only family with a stable PRE-positive shape is **LONDON-range break-and-go at the NY open (PRNG|LONDON, trigger BC = first close beyond the London high/low, entry NY-AM / 08:30-11:00)**: it supplies 10 of the 25 NY-AM PRE-selected rows (all BC; the other 15 are PPOC 12 and PVWAP 3 levels of the London session) and 2 of the 3 candidates, HOLD +1.8 and +3.1 pts/trade on MEASURED, but 2023 span -4.3 and -0.8 and MDE 12-16 pts. The sweep-and-reverse side of the same levels (SR/SRF), the Judas swing (JUD), the first-hour break/fade (FH) and the previous-session VWAP/POC levels do not produce a HOLD survivor.
- Plain line per session: **ASIA** likes nothing (4 PRE-selected, all previous-NY POC: three break/FVG on 30-s, one SRF on 1-min; all negative in HOLD, -2.2 to -5.4); **LONDON** one lead (session-open magnet, 1m, k=1.0 fade, 107 PRE trades) HOLD +0.99 but n=56 and X -9.1; **PRE** (08:30-09:30) nothing (3 selected, HOLD -4.9/-1.2/+0.8); **NY-AM** carries the LONDON-range break-and-go lead; **NY-PM** nothing (3 selected, all negative); **CLOSE** nothing (0 PRE-selected; top-10 regardless are negative in HOLD).
- New session books found (SESSION-CANDIDATE): ASIA 0, LONDON 1, PRE 0, NY-AM 2, NY-PM 0, CLOSE 0. PASS: 0 everywhere.
- Survivors for the replay: out/sd34/survivors_for_A.parquet, 4051 entries in 7 cell-sessions (3 CANDIDATE + 4 NEAR, column tier says which); no cell has stops below 20 pt, so the mapped stop credit that sank the IF/CRT cells (A_D6) is not in play, but the MEASURED target correction (-4.2 / -4.3 pt on every target exit in 2025/2026) is the largest cost and the replay is what settles it.

## 1. Design
- Levels come from the previous session as listed in the prereg (ASIA<-prior NY 09:30-16:54, LONDON<-ASIA, PRE and NY-AM<-LONDON, NY-PM<-NY-AM, CLOSE<-NY-PM); killzone clocks (London 02:00-05:00, NY 08:30-11:00, NY-PM 13:30-16:00, Asia 20:00-00:00) are windows of the same cells; every trade is scored by its ENTRY session (a NY killzone cell has PRE and NY-AM rows). Families: PRNG (previous range high/low, approached from inside), PVWAP, PPOC, FH (first-hour range, entries after minute 60), JUD (Judas: first-30-min move >= 0.25/0.5 x trailing median range, reversal through the open), SOPEN (return to the session open after a 0.5/1.0 x median-range excursion). Triggers SR, BC, BH, BF, SRF as defined in the prereg; brackets 20/20 30/30 40/40 50/50 60/60 20/40 20/60 30/60 40/20; bars 1-min and 30-s.
- Kernel: own numba kernel, verified identical to zen_lib.simulate(fill_mode=0) on 12,000 random entries (max abs difference 0.0 points) at 40/40 and 30/60 long and short; the fill_mode=1 grid is not used. Entry at the next bar open; stop first inside a bar; flat 16:54 ET.
- MEASURED analytic (tier basis): nominal - 1 tick entry - $4.84 - stop-market slip at the lot class (DN_STOPFILL by year x lot factor) + P9 Target correction. NOM = nominal less commission (the stored-like screen basis; these cells have no mapped stop credit). CONS (stress label) = +1 tick entry, 1-tick trade-through targets, stops +2 ticks, no target correction; C2 adds the correction. Lot class here uses floor(1000/(stop*20)); the replay file uses the nearest-grid convention (30-pt stops: 2 lots vs 1 here, a 0.04 pt/trade difference).
- Placebo: random-in-session, exact expectation: the mean MEAS outcome of EVERY candidate bar in the same entry session (and the same window: FH after minute 60, JUD after minute 30, killzone windows as such), same side, same bracket, same period (PRE / HOLD / X), not conditioned on the day. Disclosure: a first draft conditioned the placebo on the same label day; that is biased against fade cells on trend days (SOPEN effects of +16 pts) and was dropped before any selection; the day-conditioned expectation is kept as column ped in the trade table, not used.
- Duplicate entry sets (a killzone window and the session window produce identical PRE entries, e.g. PVWAP|LONDON|NYKZ vs |PRE) are collapsed to the plain session window before ranking. 1-min and 30-s versions of one idea are different cells (different bar paths) and are kept; they are strongly correlated and count as one idea in the cluster sense.

## 2. What each session likes - median PRE effect vs placebo (pts/trade, MEASURED, cells with n >= 100; all 3,762 cell-sessions)
| family trigger | ASIA | LONDON | PRE | NY-AM | NY-PM | CLOSE |
|---|---|---|---|---|---|---|
| FH BC | 1.95 | -1.05 |  | -1.11 | 0.41 | -0.70 |
| FH BF | 1.31 | -1.07 |  | -0.55 | -0.42 | -0.76 |
| FH BH | 0.75 | -2.01 |  | -1.40 | 0.42 | -1.18 |
| FH SR | -1.82 | 1.15 |  | -0.28 | -0.25 | -1.47 |
| FH SRF | -2.15 | -0.88 |  | -0.42 | 0.88 | -4.90 |
| PPOC BC | 0.78 | 0.97 | 0.01 | 1.80 | -0.82 | -0.76 |
| PPOC BF | 0.49 | 0.57 | 0.16 | 0.81 | -0.33 | -0.15 |
| PPOC BH | -0.44 | 0.09 | -0.28 | 0.16 | -1.05 | -1.36 |
| PPOC SR | 0.51 | 0.75 | -1.65 | 0.78 | -0.93 | -0.31 |
| PPOC SRF | -0.01 | 0.00 | -2.96 | 1.34 | -1.85 | -0.58 |
| PRNG BC | 0.15 | -0.12 | 1.24 | 2.85 | 0.07 | -1.59 |
| PRNG BF | 0.23 | 0.23 | 1.70 | 1.02 | -0.19 | -2.28 |
| PRNG BH | 0.44 | -0.36 | 3.32 | 0.21 | 1.90 | -3.50 |
| PRNG SR | -2.07 | 0.21 | -1.53 | -0.05 | 0.59 | -0.01 |
| PRNG SRF | -0.37 | 0.14 | -1.83 | -1.53 | -0.44 | 0.68 |
| PVWAP BC | -0.03 | -0.25 | 0.97 | -0.26 | -0.37 | -0.52 |
| PVWAP BF | -0.15 | -0.55 | 1.32 | 0.20 | -0.33 | -0.73 |
| PVWAP BH | -0.42 | -0.63 | 0.85 | 1.19 | -0.14 | -1.43 |
| PVWAP SR | -0.22 | 1.26 | 1.09 | 0.13 | 0.60 | -0.11 |
| PVWAP SRF | -1.57 | 0.68 | 0.43 | 0.75 | 0.56 | -1.28 |
| SOPEN EX | -0.77 | 0.43 | 2.04 | -2.15 | -2.94 | -0.32 |
| SOPEN EXR | -0.04 | -0.52 | -0.44 | -2.25 | -2.69 | 0.89 |

Positive medians are the SOPEN fades and the sweep-and-reclaim fades (SR/SRF) at the previous-session levels; every break-and-go row (BC/BH/BF) except LONDON-to-NY-AM is at or below zero after the MEASURED costs. Medians are across brackets, bars, windows and levels, so they are not cells.

## 3. PRE selection and the single HOLD look by session
| session | cell-sessions n>=100 | PRE-selected | clear best-of-F | HOLD-looked | CANDIDATE | NEAR |
|---|---|---|---|---|---|---|
| ASIA | 612 | 4 | 0 | 10 | 0 | 0 |
| LONDON | 702 | 10 | 0 | 13 | 1 | 0 |
| PRE | 612 | 6 | 0 | 10 | 0 | 1 |
| NY-AM | 702 | 25 | 0 | 25 | 2 | 3 |
| NY-PM | 702 | 3 | 0 | 10 | 0 | 0 |
| CLOSE | 432 | 0 | 0 | 10 | 0 | 0 |

## 4. Top 10 per session by PRE effect (never empty-handed; regardless of verdict)
Columns: PRE n, PRE MEAS mean, PRE effect vs placebo [CI lo] (MDE80), NOM / MEAS / M0nc (no target correction) / CONS HOLD means, HOLD n, HOLD MEAS [MDE], HOLD halves 2025H2 / 2026, X (2023 span) MEAS, tier, failed gate. Rows in the PREHOLD list only (the top 10 of each session are all in it).

### ASIA
| cell | PRE n | PRE MEAS | PRE eff [lo] (MDE) | PRE sel | HOLD n | HOLD NOM | HOLD MEAS (MDE) | HOLD M0nc | HOLD CONS | 25H2 | 2026 | X MEAS | lots | $/wk HOLD MEAS | tier | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PPOC|prevNY|ASIA|BC|p0|30s|60/60 | 328 | 0.72 | 2.97 [0.82] (3.02) | yes | 172 | 0.69 | -2.20 (4.89) | -0.06 | 0.19 | -2.04 | -3.16 | -2.44 | 0.8 | -196 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PPOC|prevNY|ASIA|BC|p0|30s|20/20 | 328 | -0.94 | 1.22 [0.21] (1.42) | no | 172 | 1.15 | -1.89 (2.24) | 0.37 | 0.44 | -1.92 | -1.69 | -0.49 | 2.5 | -502 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PPOC|prevNY|ASIA|BF|p0|30s|20/20 | 312 | -0.50 | 1.67 [0.25] (1.99) | no | 170 | 1.17 | -1.88 (2.59) | 0.39 | 0.69 | -2.04 | -0.82 | -0.09 | 2.5 | -492 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PPOC|prevNY|ASIA|BF|p0|30s|20/60 | 312 | 2.39 | 4.40 [0.53] (5.43) | yes | 170 | -0.01 | -2.19 (7.72) | -1.12 | -0.64 | -3.32 | 5.04 | -0.90 | 2.5 | -575 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 |
| PPOC|prevNY|ASIA|BC|p0|30s|20/60 | 328 | 1.71 | 3.72 [0.31] (4.79) | yes | 172 | -1.17 | -3.30 (7.38) | -2.30 | -1.80 | -4.49 | 3.98 | -0.81 | 2.5 | -877 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 |
| PPOC|prevNY|ASIA|SRF|p0|1m|20/60 | 246 | 2.23 | 4.21 [0.16] (5.69) | yes | 137 | -3.31 | -5.36 (8.11) | -4.46 | -3.95 | -7.95 | 10.72 | -0.65 | 2.5 | -1134 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 |
| PVWAP|prevNY|AKZ|BC|p0|1m|30/60 | 162 | 2.52 | 4.98 [-0.07] (7.09) | no | 86 | 0.11 | -2.25 (10.21) | -0.82 | -0.47 | -2.99 | 1.01 | 5.44 | 1.7 | -200 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0 |
| PVWAP|prevNY|ASIA|BC|p0|30s|20/60 | 255 | 1.66 | 3.69 [-0.09] (5.32) | no | 131 | 0.52 | -1.68 (6.98) | -0.58 | -0.10 | -2.22 | 0.32 | 0.13 | 2.5 | -339 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0 |
| PVWAP|prevNY|ASIA|BC|p0|30s|30/60 | 255 | 1.93 | 4.16 [-0.13] (6.04) | no | 131 | -2.07 | -4.35 (8.56) | -3.03 | -2.67 | -4.55 | -3.64 | 2.44 | 1.7 | -589 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| FH|own|ASIA|BF|p0|30s|30/60 | 440 | 1.23 | 3.46 [-0.30] (5.29) | no | 213 | 5.67 | 3.12 (8.69) | 4.81 | 5.12 | 1.28 | 13.15 | -0.05 | 1.7 | 686 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate |

### LONDON
| cell | PRE n | PRE MEAS | PRE eff [lo] (MDE) | PRE sel | HOLD n | HOLD NOM | HOLD MEAS (MDE) | HOLD M0nc | HOLD CONS | 25H2 | 2026 | X MEAS | lots | $/wk HOLD MEAS | tier | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PPOC|ASIA|LONDON|SR|p0|1m|40/20 | 441 | 0.74 | 3.41 [1.39] (2.84) | yes | 194 | 1.35 | -2.13 (4.68) | 0.79 | 0.95 | -1.20 | -6.49 | -1.29 | 1.2 | -321 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PPOC|ASIA|LONDON|SR|p0|30s|40/20 | 453 | 0.93 | 3.55 [1.42] (3.00) | yes | 199 | 2.11 | -1.41 (4.74) | 1.57 | 1.72 | -0.71 | -4.82 | -1.76 | 1.2 | -218 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PVWAP|ASIA|LKZ|SRF|p0|30s|40/20 | 350 | 1.04 | 3.55 [1.37] (3.06) | yes | 120 | 0.40 | -3.02 (5.14) | -0.17 | -0.00 | -2.22 | -9.11 | -2.45 | 1.2 | -282 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PVWAP|ASIA|LKZ|SRF|p0|1m|40/20 | 332 | 0.84 | 3.35 [1.21] (3.01) | yes | 102 | 1.71 | -1.78 (5.98) | 1.16 | 1.31 | -1.34 | -5.43 | -3.89 | 1.2 | -141 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PVWAP|ASIA|LONDON|SRF|p0|1m|40/20 | 429 | -0.02 | 2.65 [0.73] (2.70) | no | 154 | 2.74 | -0.82 (4.91) | 2.20 | 2.35 | -0.91 | -0.28 | -2.26 | 1.2 | -98 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PVWAP|ASIA|LKZ|SR|p0|1m|40/20 | 380 | 0.73 | 3.25 [0.76] (3.51) | yes | 125 | 0.71 | -2.73 (5.02) | 0.14 | 0.31 | -3.11 | 0.07 | -3.19 | 1.2 | -265 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 |
| FH|own|LONDON|SR|p0|1m|20/20 | 505 | -0.26 | 2.03 [0.45] (2.23) | no | 207 | -1.50 | -4.34 (4.31) | -2.36 | -2.01 | -5.18 | 0.23 | -2.70 | 2.5 | -1387 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0 |
| PPOC|ASIA|LONDON|BF|p0|30s|60/60 | 486 | 0.32 | 2.73 [0.49] (3.14) | yes | 215 | -0.01 | -2.85 (4.43) | -0.76 | -0.51 | -3.44 | 0.27 | -1.21 | 0.8 | -318 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 |
| PPOC|ASIA|LKZ|SR|p0|30s|40/20 | 360 | 0.47 | 2.94 [0.52] (3.40) | yes | 167 | 2.33 | -1.21 (5.00) | 1.78 | 1.93 | -0.72 | -3.71 | -1.80 | 1.2 | -156 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PPOC|ASIA|LONDON|BC|p0|30s|40/20 | 493 | -0.63 | 2.00 [0.35] (2.32) | no | 217 | 1.37 | -2.12 (3.48) | 0.80 | 0.69 | -2.02 | -2.63 | -1.68 | 1.2 | -357 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |

### PRE
| cell | PRE n | PRE MEAS | PRE eff [lo] (MDE) | PRE sel | HOLD n | HOLD NOM | HOLD MEAS (MDE) | HOLD M0nc | HOLD CONS | 25H2 | 2026 | X MEAS | lots | $/wk HOLD MEAS | tier | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PVWAP|LONDON|PRE|BC|p0|1m|40/20 | 267 | 0.40 | 2.88 [0.52] (3.32) | yes | 128 | -1.56 | -4.88 (5.17) | -2.17 | -1.99 | -4.22 | -8.68 | -3.28 | 1.2 | -485 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PPOC|LONDON|PRE|BC|p0|1m|40/20 | 333 | -0.06 | 2.45 [0.23] (3.12) | no | 132 | 3.39 | -0.21 (3.90) | 2.87 | 3.01 | -0.00 | -1.01 | -1.51 | 1.2 | -22 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PPOC|LONDON|PRE|BF|p0|1m|30/60 | 342 | 2.08 | 4.43 [0.16] (6.00) | yes | 139 | 1.20 | -1.17 (9.90) | 0.29 | 0.63 | -2.13 | 3.17 | -1.14 | 1.7 | -169 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 |
| PVWAP|LONDON|PRE|BC|p0|1m|30/60 | 267 | 1.69 | 3.96 [0.01] (5.55) | yes | 128 | 3.25 | 0.82 (7.76) | 2.37 | 2.69 | 2.48 | -8.69 | -0.58 | 1.7 | 108 | NEAR(half fails) | HOLD 2026 stub<=0 |
| PVWAP|LONDON|PRE|BF|p0|30s|20/20 | 284 | -0.37 | 1.84 [-0.18] (2.84) | no | 133 | 0.21 | -2.76 (3.25) | -0.60 | -0.29 | -2.01 | -6.56 | -0.75 | 2.5 | -567 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PRNG|LONDON|PRE|BH|p0|1m|20/60 | 165 | 2.20 | 4.74 [-0.47] (7.32) | no | 57 | -0.59 | -2.75 (13.10) | -1.71 | -1.22 | -3.18 | 0.32 | -4.34 | 2.5 | -242 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0 |
| PVWAP|LONDON|PRE|BF|p0|30s|40/20 | 284 | -0.18 | 2.27 [-0.27] (3.57) | no | 133 | -1.68 | -4.99 (3.85) | -2.29 | -2.10 | -4.91 | -5.43 | -1.90 | 1.2 | -516 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PPOC|LONDON|PRE|BC|p0|30s|60/60 | 352 | 0.03 | 2.11 [-0.30] (3.38) | no | 148 | 0.93 | -1.90 (5.47) | 0.19 | 0.44 | -1.06 | -5.04 | -1.51 | 0.8 | -146 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PRNG|LONDON|PRE|BH|p0|1m|30/30 | 165 | 1.42 | 4.03 [-0.70] (6.65) | no | 57 | 2.39 | -0.62 (10.40) | 1.67 | 0.85 | 1.43 | -15.31 | -4.07 | 1.7 | -37 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2026 stub<=0 |
| SOPEN|own|PRE|EXR|k0.5|1m|30/60 | 266 | 2.77 | 4.89 [-0.87] (8.11) | no | 107 | -2.48 | -4.75 (9.69) | -3.44 | -3.08 | -4.51 | -6.01 | 1.79 | 1.7 | -525 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |

### NY-AM
| cell | PRE n | PRE MEAS | PRE eff [lo] (MDE) | PRE sel | HOLD n | HOLD NOM | HOLD MEAS (MDE) | HOLD M0nc | HOLD CONS | 25H2 | 2026 | X MEAS | lots | $/wk HOLD MEAS | tier | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PRNG|LONDON|NY-AM|BC|p0|1m|60/60 | 374 | 6.24 | 8.32 [3.57] (6.67) | yes | 174 | 4.71 | 1.77 (11.74) | 4.01 | 4.24 | 0.32 | 9.34 | -4.27 | 0.8 | 160 | SESSION-CANDIDATE | - |
| PRNG|LONDON|NY-AM|BC|p0|1m|50/50 | 374 | 5.08 | 7.20 [3.04] (5.84) | yes | 174 | 2.37 | -0.54 (9.53) | 1.64 | 1.49 | -2.03 | 7.20 | -4.22 | 1.0 | -59 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 |
| PVWAP|LONDON|NYKZ|SRF|p0|1m|60/60 | 198 | 7.84 | 9.92 [3.64] (8.82) | yes | 94 | 1.18 | -1.68 (16.02) | 0.44 | -0.60 | -3.60 | 10.30 | -1.52 | 0.8 | -82 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 |
| PVWAP|LONDON|NYKZ|BF|p0|1m|60/60 | 211 | 7.15 | 9.21 [3.14] (8.53) | yes | 99 | -3.67 | -6.35 (14.19) | -4.44 | -5.39 | -6.56 | -3.16 | -1.09 | 0.8 | -326 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PPOC|LONDON|NY-AM|BC|p0|30s|30/60 | 470 | 2.60 | 4.53 [1.47] (4.30) | yes | 203 | 0.01 | -2.31 (5.07) | -0.92 | -0.57 | -2.76 | 1.01 | -6.39 | 1.7 | -485 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 |
| PRNG|LONDON|NY-AM|BC|p0|1m|30/60 | 374 | 3.69 | 5.64 [1.66] (5.58) | yes | 174 | 3.33 | 0.89 (9.50) | 2.45 | 2.78 | -1.20 | 11.84 | -3.92 | 1.7 | 161 | NEAR(half fails) | HOLD 2025H2<=0 |
| PRNG|LONDON|NY-AM|BC|p0|1m|40/40 | 374 | 2.80 | 4.93 [1.25] (5.16) | yes | 174 | 0.61 | -2.27 (7.75) | -0.13 | 0.12 | -4.20 | 7.80 | -2.81 | 1.2 | -307 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 |
| PRNG|LONDON|NY-AM|BC|p0|30s|40/40 | 386 | 3.03 | 5.14 [1.29] (5.42) | yes | 178 | 0.59 | -2.29 (6.89) | -0.15 | 0.10 | -3.92 | 6.10 | -2.74 | 1.2 | -316 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 |
| PPOC|LONDON|NYKZ|SRF|p0|1m|40/40 | 174 | 4.15 | 6.24 [1.55] (6.59) | yes | 82 | -5.62 | -8.19 (8.30) | -6.44 | -6.15 | -6.57 | -28.72 | -3.52 | 1.2 | -522 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PPOC|LONDON|NYKZ|BC|p0|30s|20/40 | 192 | 2.58 | 4.61 [1.02] (5.04) | yes | 100 | -1.04 | -3.42 (6.03) | -2.07 | -1.63 | -4.31 | 6.78 | -2.01 | 2.5 | -529 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 |

### NY-PM
| cell | PRE n | PRE MEAS | PRE eff [lo] (MDE) | PRE sel | HOLD n | HOLD NOM | HOLD MEAS (MDE) | HOLD M0nc | HOLD CONS | 25H2 | 2026 | X MEAS | lots | $/wk HOLD MEAS | tier | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PPOC|NYAM|NY-PM|SR|p0|30s|40/20 | 348 | 0.55 | 2.89 [0.42] (3.48) | yes | 141 | -0.58 | -3.79 (4.26) | -1.15 | -0.99 | -3.01 | -8.01 | -0.44 | 1.2 | -415 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PRNG|NYAM|NY-PM|SRF|p0|1m|20/20 | 196 | 0.89 | 3.11 [0.34] (3.89) | yes | 76 | 0.28 | -2.70 (7.21) | -0.52 | -0.21 | -3.73 | 4.14 | -1.87 | 2.5 | -316 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 |
| PPOC|NYAM|NY-PM|BH|p0|1m|40/20 | 291 | 0.15 | 2.53 [0.10] (3.40) | yes | 117 | -0.32 | -3.52 (4.66) | -0.88 | -0.76 | -3.67 | -2.72 | -0.39 | 1.2 | -320 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PRNG|NYAM|NY-PM|SR|p0|1m|30/30 | 235 | 1.21 | 3.30 [-0.01] (4.64) | no | 90 | 1.42 | -1.45 (8.52) | 0.71 | 0.95 | -0.85 | -5.74 | -3.86 | 1.7 | -135 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PVWAP|NYAM|NY-PM|SRF|p0|30s|60/60 | 325 | 2.53 | 4.52 [-0.02] (6.37) | no | 105 | -0.85 | -2.90 (11.56) | -1.45 | -1.27 | -1.56 | -11.63 | 1.53 | 0.8 | -158 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PVWAP|NYAM|NY-PM|SR|p0|1m|20/20 | 355 | -0.59 | 1.63 [-0.13] (2.47) | no | 113 | -0.43 | -3.30 (4.52) | -1.25 | -1.28 | -3.88 | 0.46 | -1.32 | 2.5 | -577 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0 |
| PVWAP|NYAM|NY-PM|SR|p0|30s|30/30 | 369 | -0.30 | 1.83 [-0.27] (2.95) | no | 117 | 0.04 | -2.67 (4.91) | -0.68 | -0.44 | -3.43 | 2.51 | -1.98 | 1.7 | -323 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0 |
| PRNG|NYAM|NY-PM|SR|p0|1m|40/20 | 235 | 0.35 | 2.67 [-0.46] (4.40) | no | 90 | 4.06 | 0.45 (7.32) | 3.55 | 3.01 | 0.55 | -0.28 | -1.75 | 1.2 | 32 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD 2026 stub<=0 |
| PRNG|NYAM|NY-PM|SR|p0|1m|20/20 | 235 | -0.21 | 2.00 [-0.36] (3.30) | no | 90 | 1.09 | -1.95 (6.09) | 0.31 | 0.61 | -1.54 | -4.89 | -0.78 | 2.5 | -270 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PVWAP|NYAM|NY-PM|BH|p0|1m|20/40 | 305 | 0.76 | 2.74 [-0.51] (4.58) | no | 112 | 3.67 | 1.13 (7.76) | 2.75 | 3.13 | 1.37 | -0.32 | 2.68 | 2.5 | 196 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD 2026 stub<=0 |

### CLOSE
| cell | PRE n | PRE MEAS | PRE eff [lo] (MDE) | PRE sel | HOLD n | HOLD NOM | HOLD MEAS (MDE) | HOLD M0nc | HOLD CONS | 25H2 | 2026 | X MEAS | lots | $/wk HOLD MEAS | tier | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SOPEN|own|CLOSE|EXR|k0.5|30s|30/30 | 294 | 1.63 | 3.11 [-0.46] (5.01) | no | 117 | -3.47 | -5.64 (7.29) | -4.19 | -3.95 | -5.92 | -4.51 | -1.11 | 1.7 | -682 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| SOPEN|own|CLOSE|EXR|k0.5|30s|30/60 | 294 | 2.72 | 3.71 [-0.76] (6.27) | no | 117 | -4.82 | -6.21 (8.57) | -5.63 | -5.34 | -6.99 | -3.00 | -0.03 | 1.7 | -751 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| SOPEN|own|CLOSE|EXR|k0.5|30s|60/60 | 294 | 3.17 | 4.23 [-0.91] (7.22) | no | 117 | -6.84 | -8.25 (10.39) | -7.42 | -7.25 | -7.79 | -10.16 | 2.85 | 0.8 | -501 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PRNG|NYPM|CLOSE|SRF|p0|30s|40/20 | 165 | 0.98 | 2.47 [-0.83] (4.64) | no | 78 | -1.36 | -4.05 (6.74) | -1.88 | -1.74 | -3.53 | -6.62 | -0.77 | 1.2 | -245 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| SOPEN|own|CLOSE|EXR|k0.5|30s|40/40 | 294 | 1.25 | 2.57 [-1.53] (5.77) | no | 117 | -4.50 | -6.40 (8.05) | -5.17 | -4.96 | -7.14 | -3.36 | 0.16 | 1.2 | -581 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| SOPEN|own|CLOSE|EXR|k0.5|30s|20/40 | 294 | 0.22 | 1.79 [-1.10] (4.07) | no | 117 | -3.89 | -5.70 (5.80) | -4.87 | -4.46 | -5.54 | -6.34 | -1.84 | 2.5 | -1030 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| SOPEN|own|CLOSE|EXR|k0.5|30s|50/50 | 294 | 1.72 | 2.91 [-2.01] (6.92) | no | 117 | -5.90 | -7.45 (9.26) | -6.50 | -6.32 | -7.29 | -8.09 | 2.70 | 1.0 | -542 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PPOC|NYPM|CLOSE|BF|p0|1m|20/60 | 422 | 0.39 | 1.71 [-1.19] (4.07) | no | 161 | 1.51 | -0.19 (6.23) | 0.57 | 0.96 | -3.12 | 13.71 | -2.82 | 2.5 | -48 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0 |
| SOPEN|own|CLOSE|EX|k0.5|1m|50/50 | 292 | 1.48 | 2.71 [-2.02] (6.65) | no | 115 | -7.48 | -9.02 (9.92) | -8.10 | -7.91 | -8.81 | -9.91 | 3.22 | 1.0 | -645 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0;HOLD 2026 stub<=0 |
| PPOC|NYPM|CLOSE|SRF|p0|30s|40/40 | 356 | 0.12 | 1.43 [-1.29] (3.82) | no | 119 | 0.02 | -1.84 (5.77) | -0.53 | -0.38 | -2.32 | 1.22 | -2.19 | 1.2 | -170 | NOT-PRE-SELECTED(top10 label) | PRE CI/mean/n gate;HOLD mean<=0;HOLD 2025H2<=0 |

## 5. The candidates in full (MEASURED unless stated)
- **NEAR(half fails) | PRE | PVWAP|LONDON|PRE|BC|p0|1m|30/60** (lots 1.7 exact at $1,000 risk, 1 contract minimum in practice): PRE 1.69 [eff 3.96, CI lo 0.01, MDE 5.55]; by year 2023(X) -0.58 (n=185) | 2024 4.42 (n=157) | 2025H1 -2.20 (n=110) | 2025H2 2.48 (n=109) | 2026 stub -8.69 (n=19); HOLD NOM 3.25, MEAS 0.82 (MDE 7.76), no-target-correction 2.37, CONS 2.69 (C2 1.14); X CONS -0.09; slippage break-even (uniform extra adverse pts/trade before HOLD MEAS = 0) 0.82; $/wk at the cell lots on HOLD MEASURED 108.
- **NEAR(half fails) | NY-AM | PRNG|LONDON|NY-AM|BC|p0|1m|30/60** (lots 1.7 exact at $1,000 risk, 1 contract minimum in practice): PRE 3.69 [eff 5.64, CI lo 1.66, MDE 5.58]; by year 2023(X) -3.92 (n=234) | 2024 0.92 (n=248) | 2025H1 9.13 (n=126) | 2025H2 -1.20 (n=146) | 2026 stub 11.84 (n=28); HOLD NOM 3.33, MEAS 0.89 (MDE 9.50), no-target-correction 2.45, CONS 2.78 (C2 1.22); X CONS -3.48; slippage break-even (uniform extra adverse pts/trade before HOLD MEAS = 0) 0.89; $/wk at the cell lots on HOLD MEASURED 161.
- **NEAR(half fails) | NY-AM | PRNG|LONDON|NY-AM|BC|p0|30s|60/60** (lots 0.8 exact at $1,000 risk, 1 contract minimum in practice): PRE 3.86 [eff 5.93, CI lo 1.17, MDE 6.69]; by year 2023(X) -2.66 (n=240) | 2024 1.74 (n=256) | 2025H1 8.05 (n=130) | 2025H2 -1.69 (n=149) | 2026 stub 10.92 (n=29); HOLD NOM 3.27, MEAS 0.37 (MDE 9.84), no-target-correction 2.56, CONS 2.79 (C2 0.60); X CONS -2.00; slippage break-even (uniform extra adverse pts/trade before HOLD MEAS = 0) 0.37; $/wk at the cell lots on HOLD MEASURED 34.
- **NEAR(half fails) | NY-AM | PRNG|LONDON|NYKZ|BC|p0|30s|30/60** (lots 1.7 exact at $1,000 risk, 1 contract minimum in practice): PRE 3.98 [eff 5.96, CI lo 0.56, MDE 7.60]; by year 2023(X) -0.57 (n=117) | 2024 1.40 (n=130) | 2025H1 7.98 (n=84) | 2025H2 3.22 (n=93) | 2026 stub -1.16 (n=20); HOLD NOM 4.96, MEAS 2.44 (MDE 11.19), no-target-correction 4.09, CONS 4.41 (C2 2.76); X CONS -0.08; slippage break-even (uniform extra adverse pts/trade before HOLD MEAS = 0) 2.44; $/wk at the cell lots on HOLD MEASURED 285.
- **SESSION-CANDIDATE | LONDON | SOPEN|own|LONDON|EX|k1|1m|40/40** (lots 1.2 exact at $1,000 risk, 1 contract minimum in practice): PRE 5.53 [eff 8.13, CI lo 1.18, MDE 9.77]; by year 2023(X) -9.09 (n=52) | 2024 4.72 (n=69) | 2025H1 7.00 (n=38) | 2025H2 1.16 (n=45) | 2026 stub 0.33 (n=11); HOLD NOM 4.04, MEAS 0.99 (MDE 16.22), no-target-correction 3.34, CONS 3.57 (C2 1.23); X CONS -8.48; slippage break-even (uniform extra adverse pts/trade before HOLD MEAS = 0) 0.99; $/wk at the cell lots on HOLD MEASURED 43.
- **SESSION-CANDIDATE | NY-AM | PRNG|LONDON|NY-AM|BC|p0|1m|60/60** (lots 0.8 exact at $1,000 risk, 1 contract minimum in practice): PRE 6.24 [eff 8.32, CI lo 3.57, MDE 6.67]; by year 2023(X) -4.27 (n=234) | 2024 5.16 (n=248) | 2025H1 8.38 (n=126) | 2025H2 0.32 (n=146) | 2026 stub 9.34 (n=28); HOLD NOM 4.71, MEAS 1.77 (MDE 11.74), no-target-correction 4.01, CONS 4.24 (C2 2.00); X CONS -3.64; slippage break-even (uniform extra adverse pts/trade before HOLD MEAS = 0) 1.77; $/wk at the cell lots on HOLD MEASURED 160.
- **SESSION-CANDIDATE | NY-AM | PRNG|LONDON|NYKZ|BC|p0|1m|30/60** (lots 1.7 exact at $1,000 risk, 1 contract minimum in practice): PRE 4.63 [eff 6.63, CI lo 1.03, MDE 7.87]; by year 2023(X) -0.83 (n=120) | 2024 2.47 (n=132) | 2025H1 8.14 (n=81) | 2025H2 3.03 (n=91) | 2026 stub 3.17 (n=20); HOLD NOM 5.59, MEAS 3.05 (MDE 11.86), no-target-correction 4.73, CONS 5.04 (C2 3.36); X CONS -0.35; slippage break-even (uniform extra adverse pts/trade before HOLD MEAS = 0) 3.05; $/wk at the cell lots on HOLD MEASURED 350.

Honest reading: the HOLD means have MDE of 12-16 pts, so each is a lead whose sign is not established; the X span is negative for all three on MEASURED, the 60/60 bracket candidate lives on 2026 (H26 +9.3 on 28 trades) and on target exits that the P9 correction then taxes. The CONS basis (no correction, +2-tick stops, trade-through targets) is the label column above.

## 6. Specs for the replay survivors (codeable)
- **PRNG|LONDON|NY-AM|BC|1m|60/60 and 30/60**: levels = LONDON session (02:00-08:30 ET) high and low, fixed at 08:30. Window: entries with bucket start 09:30-12:00 ET (NY-AM); the NYKZ variant 08:30-11:00 (its NY-AM rows are the 09:30-11:00 part, its PRE rows are not in the survivor set). Trigger on closed 1-min bars: the first 1-min close above the London high (long) or below the London low (short) after a close on the inside; once per level per day. Entry: market on the next bar open. Bracket: 60 pt stop / 60 pt target (or 30 / 60), OCO, flat 16:54 ET; 1 lot per $1,000 risk. Costs: $4.84 RT plus MEASURED fills. NT8: 1-min time bars only; no sub-minute identity check needed for the 1m cells; the 30-s variant needs the NT8 30-s bar identity check (not verified in repo).
- **SOPEN|own|LONDON|EX|k1|1m|40/40**: session open = open of the 02:00 ET 1-min bar; median range = trailing median of the last 60 London session ranges; on the first closed 1-min bar whose close is >= 1.0 x that median above (below) the open, enter short (long) at the next open; 40/40 bracket; window 02:00-08:30; once per side per day. Lead only (n=56 HOLD).
- **PVWAP|LONDON|PRE|BC|1m|30/60** (NEAR): level = London VWAP (typical-price, volume weighted, 02:00-08:30), first 1-min close through it in 08:30-09:30 in the cross direction, 30 stop / 60 target.

## 7. Multiplicity and power
F = 3,762 cell-sessions (item 3), plus 195 gated/sizing cells in item 4 (DS3_SDISC_4). Best-of-F: best PRE effect one-sided p = 0.00041; Bonferroni threshold 1.3e-5; none clear. The PRE gate (CI > 0) alone passes 48 of 3,762 (1.3% vs 2.5% expected under chance with independent cells; cells are strongly correlated, so the effective number of independent tests is far smaller, 150-300 ideas x sides).
Power: HOLD has ~170 trades per cell at a trade SD of ~40-60 pts; MDE80 is 5-16 pts per trade, larger than any cell mean. Only an effect of that size would show; a +2 pt/trade edge cannot be told from zero in this data. That is the main limit of this program.