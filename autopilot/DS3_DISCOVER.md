# DS3_DISCOVER — T-DISCOVER ranked candidate books (lead; interim rows appended every ~6 h; post-hoc, Shadow only, nothing is a PASS)
Columns: book | session | mean/wk | maxDD | Calmar (mean wk / maxDD, not annualised) | stack Calmar with it | windows | label.

## 2026-11-03 ~19:40Z — CAL (families B events, C calendar windows), harness bh.evaluate (ZL-2)
GATE WARNING: the harness TOLERANT/ADDITION gate is easy for sparse books (4-9 trades in L6M): the same grids on 30 placebo replicates (random non-event days at the same clock times) pass TOLERANT ~48 times/replicate (event grid 368 books) and ADDITION ~36; real grid: 53 TOLERANT, 39 ADDITION. Real = random. => no event book is an ADDITION; minimum-n and Bonferroni-aware gate to be added.
| book | session | mean/wk | maxDD | Calmar | stack L6M Calmar with it | windows | label |
| Mon-Tue 19:00 Asia continuation (prior 30 min dir, 60/60, T180), 371 trades | Asia | +$577 L6M | $6.6k | ~0.09 | 0.258 -> ~0.27 (est.) | positive per trade all 4 years (+30,+19,+179,+351); placebo ranks HOLD .98-1.0, PRE .73-.82, L6M .87-.96; +1 pt slip -> $386 L6M; 1R-ATR bracket loses | LEAD (not confirmed) |
| CPI E1 fade 60/60 T30 | NY-AM | +$350 L6M | $2.5k | | small | 2023 -601/trade, 2026 +1,444; 5-6 trades | LEAD-thin |
| ISM manufacturing E5 fade | NY-AM | +$378 | | | small | positive all windows; ~5-6 trades | LEAD-thin |
| ISM services E5 fade 1R-ATR | NY-AM | +$237 | | | small | positive all 4 years | LEAD-thin |
| NFP E2 sign / cont | NY-AM | +$383 / +$500 | | | small | 2023-24 negative; direction fixed after census | LEAD-thin |
| Auction 3Y E1 cont 1R-ATR | NY-PM | +$296 | | | small | 2023 negative | LEAD-thin |
| Asia 18:00 ORB Mon, Mon-Tue | Asia | positive all windows | maxDD ~18-20x weekly mean | | Mon-Tue deepens stack L6M maxDD (Calmar .249 vs .258) | PRE/HOLD ranks .95-1.0, L6M .74-.95 | FRAGILE |
| FOMC 14:35 trend continuation | NY-PM | HOLD -59 | | | | negative per trade every year; 3x range after FOMC is volatility, not direction | DEAD |
| 16:00-17:00 settlement window (16 variants) | | L6M -574..+59 | | | | all fail NOW-ONLY | DEAD |
| RTH 09:30 breakout | NY-AM | L6M -2,660 | | | | PRE +1,594: regime flip; fade (mirror) untested | open |
| month-end / quarter-end / opex Friday / roll week | | 4-6 trades in L6M | | | | do not separate from placebo | VOLUME/THIN |
Stack surface (DISCOVER_SURFACE.md): money is Asia/London handoff 19:00-02:00 esp Mon-Tue; ZERO entries after 15:00 (15:00-17:00 empty); 12:00-15:00 and 08:00-09:00 thin; largest negative cell Wed 18:00 (-$320/trade, 502 trades, ~-$160k); L6M late-week 18:00-20:00 negative. Scale note: surface sums to $11.65M vs stack core $2.52M (per-row net $ at live lots incl. non-live books?): ranking usable, absolute scale to be checked.
Plain sentences: B (events): the reaction is in the first minutes (CPI 7.6x, NFP 5.5x normal) but no entry after minute 1 beats random days; the ~5-6 tradable-looking books are the same 5-6 trades through variants (about 636 books tested, none survives Bonferroni). C (calendar): one thin lead (Mon-Tue 19:00 Asia continuation) in the stack's best cell; the empty 15:00-17:00 window has no edge.

## 2026-11-03 ~20:30Z — CAL validation batch (prereg 3d7cba2b..., DISC_C 464 cells; DISCOVER_C_VALIDATION.md)
| book | session | mean/wk | maxDD | stack effect | windows | label |
| Mon-Tue 19:00 Asia continuation | Asia | L6M +577 | 6.6k | L6M Calmar .258 -> .280 at equal risk (4x2 lots), HOLD maxDD -10%, PRE maxDD 88k -> 111k worse | SPIKE not plateau (16% of 360-book grid positive in L6M+HOLD+PRE; 19:30 clock avg -895; 75/75 flips negative); best-of-30 family null: beaten in 45% of 300 worlds (single pre-chosen p .03); +2 pt slip makes PRE/X' negative; 99.7% of entries have a live Asia entry in the previous 60 min (same-way trades +$331 each, against-live trades -$75 each); stack corr .085 | FRAGILE |
| RTH 09:30 30-min-range FADE 60/60 T240 | NY-AM | L6M +2,413, HOLD +1,367, MID +1,581 | L6M 9.8k | L6M Calmar .258 -> .339 (carry-dropped .695 -> .796); HOLD maxDD 122k -> 135k | PRE -1,975, X' -514; negative every quarter 2023Q2..2025Q4 except 2023Q3, positive every 2026 quarter; placebo rank .99-1.0 L6M/HOLD, 0.00 PRE; +3 pt slip L6M still +1,522; corr to stack -.09 | LEAD-REGIME (NOW-ONLY, fails tolerant) |
| causal trailing-20-day flip rule for breakout/fade | | L6M +1,220 | | | PRE -225, best-of-12 null p .51; cannot date the 2025Q3 change | DEAD |
| 15:30 reversal | | | | | one tolerant pass, HOLD -454, MID -806 | DEAD |
| 15:50 MOC-proxy days | | | | | 28-127 trades, no separation; imbalance data not on disk | THIN |
| Wed 18:00 contrarian (opposite side of live entries), 502 live-entry seconds, 1 lot | Asia | L6M +671 (T60) | | | PRE -89, HOLD +109, MID -487; T120 HOLD -155; null of contrarian books on other cells loses (L6M -387): p .004 L6M, .024 PRE, .26 HOLD; 1R-ATR bracket loses | FRAGILE candidate |
Surface scale corrected: $11.65M was a mis-multiplied column; row table sums to $2,526,421 vs stack core $2,520,149 (0.25%), six live books; per-book differs from the engine cube (KB 179k vs 235k, HM 471k vs 398k), daily corr .94.
Net: no addition. Nearest to real: the RTH 09:30 fade as a recent-regime (2026) bet.

## 2026-11-03 ~21:30Z — CAL family D (prereg 246396723b2f..., DISC_D 344 cells; DISCOVER_D.md); nothing clears the bar
| family | books | best S | p side null | p shift null | verdict |
| D3 session extremes | 108 | +977 | .10 | .00 | LEAD-thin (only the overnight high/low fade at 09:30-10:00 lives: 31/36 books positive in L6M, HOLD, MID; Asia-extreme fade in London dead L6M -742; prior-day extreme dead) |
| D4 VWAP + bands | 62 | +2,075 | .017 | .00 | LEAD-regime (NY-AM VWAP fade works, NY-AM continuation loses badly; Asia continuation positive L6M +2,192 avg) |
| D5 ORB, range as stop | 96 | +624 | .68 | .77 | dead |
| D6 gap books | 80 | +478 | .73 | .77 | dead |
| NY-AM VWAP fade d10 T120, 1,360 trades | NY-AM | L6M +1,424 (maxDD 15.9k), HOLD +2,526, MID +6,803, PRE -493, X' -135 | | | 2026-only: $/trade by year +22, -60, 0, +351; +1/+2/+3 pt slip L6M 611/486/-332; stack L6M Calmar .258 -> .338, HOLD .185 -> .256 (carry-dropped .695 -> .699); corr -.05 to stack; 72% of entries follow a live entry within 60 min (rule < 50%); gate_v2 false (p_book .03; Bonferroni over 346 books 1.0) | LEAD-regime, not cleared |
| overnight-extreme fade ON_RTH x0 w60 60/60 T60, 525 trades | NY-AM | L6M +703, L3M -135, HOLD +1,172, MID +2,900, PRE +46 | | | +3 pt slip L6M 336; 37% follow a live entry; fails tolerant on L3M, side null p .10 | LEAD-thin |
BUNDLE (one regime, count as ONE observation): RTH 09:30 ORB fade + NY-AM VWAP fade + overnight-extreme fade: pairwise daily corr .01-.21; negative/flat 2023Q2-2025Q2, positive 2026Q1-Q3; the live stack's NY-AM sleeve made +5.9k..+143k per quarter through 2025Q2 and ~0, +31k, +10k, +0.8k in 2026Q1-Q4: the three books are effectively a HEDGE for it. At 0.5x of the three combined (2 lots each): L6M Calmar .258 -> .355 (maxDD 104.8k -> 82.4k), carry-dropped .695 -> .755, HOLD .185 -> .222, MID .282 -> .552; PRE worsens .150 -> .128. Across the four D families D4 p ~ .07, D3 > .2.
