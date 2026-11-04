# DS3_GATES: the per-book daily loss / profit gate on the real engine (DIS-AR)

Author ZL-2, 2026-11-04. Scope note l2vast/ds3/prereg/DISAR_scope.md sha256 752aae1cd4a519f6c8e275f03a768fdcbc83dafd3c1d9c17ea9f332442371840 (DECISIONS.md, before any outcome). Measurement; no PASS; nothing live; no new setting is selected. Code l2vast/ds3/code/dis_x/ar_*.py; tables l2vast/ds3/out/dis_ar/ (ar_grid.csv, ar_paired.csv, ar_frontier.csv). Engine V13T ts2 full stack (the live cell reproduces $2,520,149), live lots, live cost frame; period statistics with the corrected carrying weeks dropped (2023 18 weeks, 2024 53, 2025 49, 2026 30, HOLD 38, PRE 71, L6M 16, X' 23, ALL 148).

## Plain sentence
The 2R daily loss gate is a small positive contributor with the TH cut on (+$0.34k/week over no gate over 148 weeks, paired CI of "no gate minus live" -$711 to -$21; it blocks 432 entries, which would have lost $60k; it lowers the HOLD maxDD from $140k to $122k and the worst day from -$44.9k to -$38.1k, and beats 97% of random same-count entry blocks on mean and on HOLD maxDD), its value is regime-dependent (per year vs no gate: 2023 +$0.26k, 2024 +$0.25k, 2025 +$0.02k, 2026 +$1.07k per week), the TH cut makes it bind 72% less (1,556 blocks with TH off, 432 with TH on) so TH plus 2R is slightly better than TH plus 3R, 4R or no gate and clearly better than TH plus 1R or 1.5R on the mean, tighter gates and a re-entry pause buy a smaller recent drawdown (1R: 2026 maxDD $39k, pause 30-60 minutes: $30-33k, versus $63k live) at a lower mean (-$2.2k to -$4.2k per week over the full period), the profit gate (5R, binds 62 times) is immaterial, and no cell in the 36-cell grid beats the live cell on mean and maxDD together over the full period.

## 1. Hooks
| item | hook | status |
|---|---|---|
| per-book daily loss gate (entry skipped when the book's realised P&L that label day, from trades closed before the entry time, is <= -L x R) | OC.CFG['spec']['pb_loss'] (global value for the six books in a run) | exists; per-book different thresholds: no hook (not run); R = book planned risk x the running-max size multiplier |
| per-book daily profit gate | OC.CFG['spec']['pb_win'] | exists |
| TH cut | ov th_loss | exists |
| re-entry pause after a cut | extra_skip emulation (as in DS3_SLOT_CHANNEL) | emulation |
| blocked-entry value | not logged by the engine (only the day of each skip); measured as the trades in the gate-off run (same TH state and profit gate) that are absent from the gated run, valued in the gate-off run | derived |
Dead_lookup (cited): DS3_LOCK_SWEEP.md (week floor x give-back surface; the daily max P/L 5R/2R held fixed there), DS3_SIZER_X_LOCK_V13T.md (60 lock cells, sizer on/off), DS3_LIVE_LOCK_NOISE_V13T.md; the daily gate grid was not run before. In DS3_SLOT_CHANNEL the gate-off diagnostics showed the TH benefit interacts with this gate.

## 2. Grid: loss gate x profit gate, TH ON (live) and TH OFF — ALL window mean $k/wk, maxDD $k, Calmar (profit gate 5R live | 10R | off)
TH ON: L=1R 15.6/84/0.19 | 15.4/84/0.18 | 15.4/84/0.18; 1.5R 16.9/88/0.19 | 16.7/88/0.19 | 16.7/88/0.19; **2R 17.7/75/0.24 (live)** | 17.5/75/0.23 | 17.5/75/0.23; 3R 17.4/75/0.23 | 17.2/75/0.23 | 17.2/75/0.23; 4R 17.4/75/0.23 | 17.2/75/0.23 | 17.2/75/0.23; off 17.4/75/0.23 | 17.2/75/0.23 | 17.2/75/0.23.
TH OFF: L=1R 14.4/160/0.09 | 14.3/157/0.09 | 14.3/157/0.09; 1.5R 16.0/190/0.08 | 15.9/187/0.08 | 15.9/187/0.08; 2R 15.7/175/0.09 | 15.5/172/0.09 | 15.5/172/0.09; 3R 15.9/154/0.10 | 15.7/151/0.10 | 15.7/151/0.10; 4R 15.9/158/0.10 | 15.7/156/0.10 | 15.7/156/0.10; off 15.7/158/0.10 | 15.5/156/0.10 | 15.5/156/0.10.
By year and window (profit gate live), TH ON, mean $k/wk: 
| loss gate | 2023 | 2024 | 2025 | 2026 | HOLD | PRE | L6M | X' | maxDD HOLD / PRE / L6M / X' / 2026 | worst day / week | blocks (loss / profit) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1R | -0.8 | 11.6 | 17.0 | 29.0 | 23.4 | 13.9 | 37.0 | 2.6 | 127 / 84 / 39 / 53 / 39 | -30.2 / -54.0 | 2,973 / 62 |
| 1.5R | -0.6 | 13.1 | 17.7 | 31.5 | 25.5 | 15.0 | 38.5 | 2.7 | 120 / 88 / 63 / 49 / 63 | -34.2 / -63.1 | 1,155 / 62 |
| **2R (live)** | -0.2 | 13.9 | 17.0 | 35.3 | 27.9 | 15.2 | 43.5 | 3.0 | 122 / 75 / 63 / 49 / 63 | -38.1 / -62.6 | 432 / 62 |
| 3R | -0.2 | 13.7 | 16.7 | 34.5 | 27.3 | 14.7 | 42.2 | 3.0 | 130 / 75 / 55 / 49 / 55 | -44.9 / -62.3 | 80 / 65 |
| 4R | -0.5 | 13.6 | 17.0 | 34.3 | 27.0 | 14.9 | 42.0 | 2.8 | 138 / 75 / 55 / 49 / 55 | -44.9 / -62.3 | 12 / 65 |
| off | -0.5 | 13.6 | 17.0 | 34.2 | 26.9 | 14.8 | 42.1 | 2.8 | 140 / 75 / 55 / 49 / 55 | -44.9 / -62.3 | 0 / 65 |
TH OFF, mean $k/wk and maxDD:
| loss gate | 2023 | 2024 | 2025 | 2026 | HOLD | PRE | L6M | X' | maxDD HOLD / PRE / L6M / X' / 2026 | worst day / week | blocks |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1R | 1.4 | 10.0 | 20.8 | 18.8 | 15.1 | 13.8 | 22.3 | 3.4 | 110 / 160 / 50 / 94 / 74 | -34.1 / -64.1 | 5,337 / 125 |
| 1.5R | 0.6 | 11.2 | 21.0 | 24.7 | 20.8 | 14.6 | 29.1 | 3.0 | 85 / 190 / 69 / 86 / 85 | -43.7 / -99.9 | 2,769 / 132 |
| 2R | 0.4 | 11.3 | 21.8 | 21.7 | 19.9 | 14.8 | 23.5 | 2.8 | 91 / 175 / 90 / 81 / 91 | -52.3 / -104.5 | 1,556 / 132 |
| 3R | 0.5 | 12.1 | 21.4 | 21.5 | 19.2 | 14.9 | 25.2 | 2.9 | 124 / 154 / 106 / 81 / 111 | -54.2 / -105.8 | 498 / 132 |
| 4R | 0.5 | 12.1 | 21.5 | 21.5 | 19.0 | 15.1 | 24.6 | 2.9 | 114 / 158 / 93 / 81 / 107 | -59.4 / -112.5 | 165 / 132 |
| off | 0.5 | 11.9 | 21.2 | 21.4 | 18.6 | 14.9 | 25.4 | 2.9 | 138 / 158 / 93 / 81 / 121 | -66.4 / -112.5 | 0 / 132 |
Profit gate (10R vs 5R): ALL mean -0.2k/wk at every loss gate, no maxDD change; at off -0.2k; binds 62 times (TH ON) and 132 (TH OFF). Immaterial.

## 3. Question 1: is the 2R gate a net contributor, is it regime-dependent?
Paired weekly difference to the live cell (TH ON, 2R, 5R; 148 weeks; 95% block-bootstrap CI, block 4): loss gate 1R -$2,150 [-3,973, -503]*; 1.5R -$831 [-2,007, +184]; 3R -$318 [-679, +26]; 4R -$324 [-665, +9]; off -$342 [-711, -21]*; profit gate 10R at 2R -$213 [-575, +63]. TH OFF cells vs the live cell (TH effect included) are all below by $1.7k-$3.4k per week with intervals spanning zero. So against no gate the 2R gate adds about $0.34k a week (about $51k over the period); against a looser gate (3R, 4R) about $0.32k; against tighter gates it gains $0.8k (1.5R) to $2.2k (1R).
Regime: the gate's value versus no gate, TH ON, $k/wk: 2023 +0.26, 2024 +0.25, 2025 +0.02, 2026 +1.07; with TH OFF the gate does not raise the mean in any year (2R vs off: 2023 -0.1, 2024 -0.7, 2025 +0.6, 2026 +0.2) and deepens PRE/ALL maxDD (175 vs 158) while shrinking HOLD (91 vs 138) and the worst week (-104.5 vs -112.5). With TH ON the gate leaves PRE/ALL maxDD unchanged (75) and cuts HOLD maxDD by $18k and the worst day by $6.8k.
Blocked entries (trades in the gate-off run that the gate removes; their value if taken, TH ON): 2R removes 432 trades worth -$60k (2023 5 trades -$7k; 2024 42 trades -$13k, -14.8 points/lot; 2025 106 trades -$1k, +3.1; 2026 279 trades -$38k, -2.9). By book: KB 263 trades -$28k (-4.1 pts/lot), PE 72 trades -$36k (-4.8), MV 47 +$4k, PB 47 +$2k, HM 3 -$2k, SM 0. By session: nypm 133 trades -$24k (-7.4 pts/lot), london 89 -$23k (-1.8), asia 57 -$13k (-2.2), nyam 153 +$1k. TH OFF 2R removes 1,514 trades worth -$11k net (KB 886 -$104k, PE 315 +$43k, MV 228 +$42k, SM 9 +$8k, HM 48 -$8k, PB 28 +$9k; by year 2023 +$29k, 2024 +$35k, 2025 -$61k, 2026 -$15k): without the TH cut the gate blocks about as many good as bad trades; with it, the entries left to block are mostly bad ones. Tighter gates remove good trades: 1R TH ON removes 2,949 trades worth +$298k (2023 +59k, 2024 +105k, 2026 +144k), 1.5R 1,152 trades +$59k.
Placebo (40 random removals of taken trades from the no-gate TH-ON run, counts equal to the real gate: KB 263, PE 72, MV 47, PB 47, HM 3): ALL mean real $17.72k vs placebo mean $17.12k (range $16.59k-$17.84k; 3% of draws at or above real); ALL maxDD real $75k vs placebo $77k (40% at or below); Calmar real 0.236 vs 0.223 (15% at or above); 2026 mean real $35.3k vs $33.8k; HOLD maxDD real $122k vs placebo $137k (3% at or below). The gate beats random blocking on mean and HOLD drawdown, not on the full-period drawdown. Forward-safe (random blocks use no outcome information).

## 4. Question 2: does TH make the gate bind less; TH+2R versus TH+looser
Bind counts, loss gate (TH OFF -> TH ON): 1R 5,337 -> 2,973; 1.5R 2,769 -> 1,155; 2R 1,556 -> 432 (-72%); 3R 498 -> 80; 4R 165 -> 12. With the cut the daily loss rarely reaches 2R, so the gate acts only on the worst days. TH+2R vs TH+3R / 4R / off: mean +0.3k/wk each (above), HOLD maxDD 122 vs 130 / 138 / 140, PRE and ALL maxDD equal (75), worst day -38.1k vs -44.9k; 2026 maxDD slightly worse (63 vs 55). TH+2R vs TH+1.5R: mean +0.8k/wk, ALL maxDD 75 vs 88. TH+2R vs TH+1R: mean +2.1k/wk, ALL maxDD 75 vs 84, but 2026 maxDD 63 vs 39 and L6M maxDD 63 vs 39. So the combination is better than TH plus a looser gate on mean and HOLD drawdown, and TH plus a tighter gate is a trade of mean for recent drawdown.
Rolling-origin (select the cell with the highest training Calmar among the 18 cells per TH state; test vs the live gate): TH ON: train 2023-04..2024-12 -> test 2025-01..2026-10 selects 2R/10R (test 17.5k/122k/0.14 vs live 17.9k/122k/0.15); 2024 test selects 1.5R (13.1k/88k vs 13.8k/75k); 2025 selects 2R/10R (13.7k/88k vs 14.0k/88k); 2026 selects 2R/5R (equal). TH OFF: selects 3R in every split; test mean is below the 2R gate in three of four (15.2k vs 16.5k; 18.1k vs 18.9k; 11.3k vs 13.2k; 2024: 12.1k vs 11.3k above) with a deeper maxDD in 2 (250k vs 222k). No selected cell beat the live gate in test by more than $0.8k a week; the live gate is rolling-origin stable with TH on.

## 5. Question 3: frontier of (mean, maxDD) across gate x TH x pause
ALL window mean $k/wk / maxDD $k | 2026 mean / maxDD | L6M mean / maxDD | HOLD maxDD | PRE maxDD:
| setting | ALL | 2026 | L6M | HOLD dd | PRE dd |
|---|---|---|---|---|---|
| **LIVE: TH ON, 2R, profit 5R** | 17.7 / 75 | 35.3 / 63 | 43.5 / 63 | 122 | 75 |
| TH ON, loss gate off | 17.4 / 75 | 34.2 / 55 | 42.1 / 55 | 140 | 75 |
| TH ON, 3R | 17.4 / 75 | 34.5 / 55 | 42.2 / 55 | 130 | 75 |
| TH ON, 1.5R | 16.9 / 88 | 31.5 / 63 | 38.5 / 63 | 120 | 88 |
| TH ON, 1R | 15.6 / 84 | 29.0 / 39 | 37.0 / 39 | 127 | 84 |
| TH ON, 2R + pause 15 min | 16.4 / 84 | 33.3 / 57 | 41.5 / 57 | 121 | 80 |
| TH ON, 2R + pause 30 min | 14.9 / 87 | 28.2 / 33 | 33.8 / 33 | 134 | 87 |
| TH ON, 2R + pause 60 min | 13.5 / 81 | 19.2 / 30 | 18.5 / 30 | 118 | 81 |
| TH ON, off + pause 60 | 13.5 / 81 | 19.1 / 38 | 18.1 / 38 | 107 | 81 |
| TH OFF, 2R | 15.7 / 175 | 21.7 / 91 | 23.5 / 90 | 91 | 175 |
| TH OFF, 3R | 15.9 / 154 | 21.5 / 111 | 25.2 / 106 | 124 | 154 |
| TH OFF, 1R | 14.4 / 160 | 18.8 / 74 | 22.3 / 50 | 110 | 160 |
| TH OFF, off | 15.7 / 158 | 21.4 / 121 | 25.4 / 93 | 138 | 158 |
Pareto set on (ALL mean, ALL maxDD): the live cell dominates the other 47 cells (36 grid + 12 pause runs) (nothing has both a higher mean and a lower or equal maxDD). The frontier in the recent drawdown is different: on 2026 / L6M maxDD the lowest points are the TH-ON 2R + pause 60 (30k, mean 19.2k), pause 30 (33k, 28.2k), 1R (39k, 29.0k) and the loss-gate-off cells (55k, mean 34-35k, i.e. no worse than live on drawdown and slightly lower mean). Cost of lowering the 2026 maxDD from $63k to $39k / $33k / $30k: mean -$6.3k / -$7.1k / -$16.1k per week in 2026 and -$2.1k / -$2.8k / -$4.2k per week over the full period. The TH-OFF cells are $1.5-4k per week lower in mean and roughly twice as deep over PRE/ALL.

## Limits
* The gate threshold is one global value per run; per-book thresholds and a dollar-based (not R-based) gate are not hooked. R includes the running-max size multiplier, so a gate in R is wider on high-multiplier days.
* The 36-cell grid, the 12 pause cells and the 40 placebo draws are single engine paths; the placebo compares to the no-gate path; CIs are for weekly differences within one path.
* Blocked-entry value uses the gate-off run's trade (displacement effects, e.g. replacement trades after a block, appear as 0 to 45 trades per cell and are not valued separately).
* Calmar uses the weekly-cumulative maxDD; windows with few weeks (2023: 18, L6M: 16) are noisy.

## AMENDMENT 2026-11-04 (ZL-2, appended): pause clock and live-window base
(a) The re-entry pause rows (section 5 and the pause frontier) used a path-index clock (1,800 indices = 60 real minutes in Asia, 48 London, 30 NY). Real-clock rows, TH on, no cap, V0 base (total $k / mean $k per week / 2026 maxDD / HOLD maxDD): gate 2R pause 15 / 30 / 60: 2,469 / 17.44 / 60 / 117; 2,327 / 16.58 / 47 / 131; 2,075 / 15.12 / 47 / 128. Gate 1R: 2,126 / 15.32 / 39 / 126; 2,020 / 14.62 / 40 / 127; 1,926 / 14.24 / 46 / 117. The statement that pauses of 30 and 60 minutes lower the 2026 maxDD to 33k and 30k at 2R is withdrawn (47k). Everything else in the gate grid (pause 0) is unchanged. (b) On the live-window base (DS3_LIVE_WINDOWS_BASE.md, V2: 09:30-09:59 and 18:00-18:04 blocked), TH on: mean $k/wk 1R 14.22, 1.5R 15.76, **2R 16.54**, 3R 16.29, 4R 16.21, off 16.21; HOLD maxDD 104 / 95 / 91 / 98 / 106 / 107; the 2R gate is still best on mean (+0.33k/wk vs off, was +0.34k) and lowers HOLD maxDD by 16k (was 18k); with TH off the 2R gate is -0.58k/wk against no gate (was 0.00). No ranking changes.
