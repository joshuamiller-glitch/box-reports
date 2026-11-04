# RECON_PAUSE: why the pause-30 cell differed between ZL-2 ($1,469k / HOLD maxDD $62.4k) and Z3 ($1,613k / $84.6k), and the restated pause rows

Author ZL-2, 2026-11-04 (copy: Z3 a3fd82672e72ada3e). Measurement; no PASS; nothing live. Code l2vast/ds3/code/dis_x/rp_lib.py (parametrised pause emulation), rp_exp.py (one-at-a-time toggles), rp_front.py (corrected rerun), rp_diag.py (cut-set overlap); Z3's code l2vast/ds3/code/dis_bd/bd_cell.py. Cell tested: PE weight 0.5, net-lot cap 12, pause 30 minutes, loss gate 1R, TH on, engine base V0 (as run).

## Answer
The two emulations differ in ONE thing that matters: the clock. Z3 measures the 30 minutes in real seconds (SS[kin] > SS[tx] and <= SS[tx] + 1,800). My mask measured them in path-index units (kin index > tx and <= tx + 1,800), and the 1-second path contains only seconds with prints (about 1,430 path indices per real hour overall), so 1,800 indices are 60 real minutes in Asia (median over 10,128 cuts), 48 in London, 30 in the NY sessions: my pause was about twice as long in the sessions that carry the PE book. With Z3's clock the cell is $1,624k / HOLD maxDD $84.5k / 2026 maxDD $31.1k (Z3: $1,613k / $84.55k / $31.12k); with my clock and Z3's cut set it is $1,457k / $60.0k / $22.5k. The cut set (Z3 box-side exits vs the stored TH-L2 fire stream vs fires confirmed by the engine exit) changes the total by 0.4% and the HOLD maxDD by under $3.2k and does not matter. All pause-15 and pause-30 rows of DS3_RISK_FRONTIER, DS3_GATES and DS3_SLOT_CHANNEL are restated below.

## 1. The two definitions, precisely
| item | ZL-2 (v1, v2 frontier, DS3_SLOT_CHANNEL, DS3_GATES) | Z3 (DS3_FRONTIER_XCHECK) |
|---|---|---|
| cut set | taken trades of the previous pass whose d-row has a TH-L2 fire in out/dis_ba/bundle/ai_cuts.pkl (d7lib._exits_l2sl(30,5,30,0), first fire per trade), whether or not the engine's exit coincided with the fire (4.7% did not: 247 exit earlier, 331 later) | taken trades with R['ty0']==2 and R['kx0'] < R['kflat'] (box-side exit before the session flat); lock flattens not targeted |
| cut time | the fire second index kx (path index) | the actual exit second SS[tx] |
| clock for the N minutes | path-INDEX units: entries with kin in (kx, kx + 60 N] | REAL seconds: entries with SS[kin] in (SS[tx], SS[tx] + 60 N] |
| scope | same book, either side | same book, either side |
| action | skip via extra_skip (no delay) | skip via extra_skip |
| rows paused | every library row of the book in the window (taken or not) | every live signal row of the book in the window |
| add leg | the skipped entry has no legs; the cut closes the position and cancels the resting add (engine rule); a cut of the add leg alone is not a separate event | same |
| iteration with the cap | pause mask rebuilt from the previous pass's trades every pass, cap pass on the same run; stops when no taken row changes lots and the mask is unchanged | the same (cap via run_stack with the pause OR-ed into extra_skip each pass), up to 8 passes |
| lock governor | gov_mer = ER multiplier alone (unchanged by weight, cap, pause) | same |

## 2. One-at-a-time toggles on the pause-30 cell (PE x0.5, cap 12, 1R; total $k / HOLD maxDD / 2026 maxDD / PRE maxDD; converged in 7-10 passes)
| run | cut set | clock | scope | total | HOLD dd | 2026 dd | PRE dd | masked rows |
|---|---|---|---|---|---|---|---|---|
| Z3 reproduced | box-side exits (Z3) | real seconds | book | 1,613 | 84.5 | 31.1 | 52.1 | 2,118 |
| ZL-2 reproduced | table fires | path index | book | 1,469 | 63.1 | 22.5 | 48.9 | 3,203 |
| toggle: cut set only (Z3 -> table fires) | table fires | real seconds | book | 1,618 | 87.7 | 31.1 | 51.0 | 2,182 |
| toggle: cut set only (Z3 -> fires confirmed by the engine exit) | confirmed fires | real seconds | book | 1,624 | 84.5 | 31.1 | 52.1 | 2,034 |
| toggle: clock only (Z3 -> path index) | box-side exits (Z3) | path index | book | 1,457 | 60.0 | 22.5 | 47.8 | 3,135 |
| both ZL-2 choices except cut-set confirmation | confirmed fires | path index | book | 1,470 | 59.2 | 22.5 | 45.8 | 3,045 |
| toggle: scope (confirmed fires, real seconds) book -> all books | confirmed fires | real seconds | ALL books | 1,349 | 77.4 | 25.0 | 48.5 | 7,625 |
Cut-set overlap (taken trades 19,523 in the PE x0.5 gate-1R run): Z3's set 10,980, table fires 11,126, confirmed fires 10,561; Z3 and confirmed fires share 10,561, Z3 and table fires 10,947; engine-early exits (tx earlier than the library exit) are only 58. So Z3's "box-side exits" and the TH-L2 fire stream are the same population within 5%. The gap of $144k in total and $21k in HOLD maxDD is the clock (-$156k and -$24.5k when Z3's set is run on the index clock).

## 3. Which definition matches the intended rule
Intended rule (DS3_SLOT_CHANNEL.md and the lead): "no re-entry for N minutes after a TH cut on the same book". Minutes are clock minutes, so the real-seconds clock (Z3's) is the correct one; same book, either side, skip (not delay), from the cut exit second. For the cut set I use cuts the engine actually made (a TH-L2 fire at the exit second, "confirmed fires": 10,561 trades); Z3's set differs by 4%. Lock flattens, stops, targets and session flats are not cuts in either definition. I withdraw the index-clock results.

## 4. Restated pause rows (real clock, confirmed fires; everything else as in the frontier; all cells converged in 5-10 passes; engine as run V0)
DS3_RISK_FRONTIER pause cells, mean over the 60 cells at each pause (old index clock -> real clock): pause 15: mean $12.66k -> $13.42k per week, worst-of maxDD $96.7k -> $88.2k; pause 30: $11.68k -> $12.75k, worst-of $94.7k -> $102.8k. The 30-minute pause cells that looked like drawdown-cutters (HOLD maxDD $62k) are not: with the real clock HOLD maxDD gets WORSE than the pause-0 cell ($66.6k -> $84.5k in the cell tested); the 15-minute pause is mildly useful. Selected cells (mean $k/wk, HOLD maxDD $k, 2026 maxDD $k):
| cell | old (index clock) | restated (real clock) |
|---|---|---|
| w1.00 no cap, gate 2R, pause 15 | 16.20, 124.7, 60.1 | 17.44, 116.9, 59.9 |
| w1.00 no cap, gate 2R, pause 30 | 14.91, 128.2, 38.4 | 16.58, 131.0, 46.6 |
| w1.00 no cap, gate 1R, pause 15 | 14.27, 129.6, 40.7 | 15.32, 126.0, 39.3 |
| w1.00 no cap, gate 1R, pause 30 | 13.61, 112.0, 30.6 | 14.62, 126.6, 40.5 |
| w0.50 cap 12, gate 1R, pause 30 | 10.42, 62.4, 22.5 | 11.76, 84.5, 31.1 |
Frontier membership (V0 base, real clock): 18 cells (was 14): ten pause-15 cells join (for example w1.00 no cap gate 2R pause 15: mean $17.44k, worst-of maxDD $116.9k, $54 of weekly mean lost per $1k of maxDD removed, cheaper than any cap-only cell), six pause-0 cells drop out (w0.75 cap10/cap12 gate 2R, w0.75 cap12 gate 1R, w1.00 cap10/12/14 gate 2R: now dominated by the pause-15 cells), and every pause-30 cell stays off. The frontier extremes (PE weight 0.5, cap 8, gate 1R, pause 0) are unchanged. New CSV (do not overwrite): l2vast/ds3/out/dis_ba/DS3_RISK_FRONTIER_v3.csv (92 cells; the first CSV and the v2 CSV are unchanged). The V2 (live-window) frontier is in DS3_RISK_FRONTIER_W3_livewindows_v3.csv.
Real-clock pause rows for DS3_GATES and DS3_SLOT_CHANNEL (TH on, w1.00, no cap, V0 base; total $k / ALL mean $k per week / 2026 maxDD / HOLD maxDD): gate 2R: pause 15 2,469 / 17.44 / 60 / 117; pause 30 2,327 / 16.58 / 47 / 131; pause 60 2,075 / 15.12 / 47 / 128. Gate 1R: 2,126 / 15.32 / 39 / 126; 2,020 / 14.62 / 40 / 127; 1,926 / 14.24 / 46 / 117. Gate 1.5R: 2,387 / 16.79 / 58 / 116; 2,324 / 16.44 / 56 / 131; 2,049 / 14.82 / 56 / 135. Gate 3R: 2,398 / 17.08 / 52 / 130; 2,254 / 16.33 / 48 / 138; 2,066 / 15.13 / 48 / 138. Gate off: 2,388 / 17.01 / 52 / 132; 2,262 / 16.36 / 48 / 138; 2,063 / 15.11 / 48 / 138 (no cap, pause 0 live: 2,520 / 17.72 / 63 / 122). Reading: with the real clock a re-entry pause after a cut still lowers the mean in every setting, still does not reduce the HOLD drawdown (117k-138k vs 122k), and lowers the 2026 drawdown only at 1R and at the 30- and 60-minute settings; the earlier claim that a 30-60 minute pause cuts the HOLD drawdown ("pause 30-60 gives 33k-30k 2026 maxDD") is withdrawn for the 2R gate (real clock 2026 maxDD 47k).
Time stops (DS3_SLOT_CHANNEL (b)) used the same index clock (kin + 60 N); rebuilt with real seconds: conditional totals $1.24M (20 min), $1.63M (30), $1.26M (45), $1.61M (60) (old $1.40M, 1.49M, 1.78M, 1.89M), unconditional $-0.2M to $0.4M, cut ON plus conditional stop $1.96M (30) and $2.01M (60); still all below the cut ($2.52M) and TH-off ($2.24M); conclusion unchanged.

## 5. Open points
* The cap loop and the lock governor are shared with Z3's path (engine kernels), so this reconciles the two pause definitions, not the engine itself.
* Pause rows are single-path in-sample; pause 15 on the frontier is a one-path observation (mean cost $0.3k per week for $5k of HOLD maxDD in the live-weights cell).
