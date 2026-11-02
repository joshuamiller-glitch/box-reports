
## OLD CAP interim (checkpoint, Z2, wall ~15:50Z 2026-11-01) - data cap 2026-02-06, windows L3M/L6M/HOLD/PRE/X'; superseded by T-RECENT-REDO, workers stopped
Base: interim one-convention composite via drawdown/dd_lib (oc_lib unchanged); zone mask rebuilt from per-line store features ties x['zone'][20] (9,642 fires); L6M maxDD 22.9k, Calmar L6M 1.80 / PRE 0.096 / X' 0.066. Not the D7 base (BASE-1 pending).
Prereg: l2vast/ds3/prereg/ZONES3_S2_prereg.md sha256 4fef9568f04020637a3fce9c7c5dba7565b3cd68631a963e838947135805b016 (in DECISIONS.md). dead_lookup: out/zones3/s2/dead_lookup.txt. append_cells NOT yet done (nothing final).
BUILT (code l2vast/ds3/code/zones3/s2/): z2lib.py (line masks D/freshness/age/confluence/session, scoring, placebo mask builder), gen_jobs.py, worker.py (resumable; `python3 -I worker.py <s1|sess|null|gen> <shard> 3 [tag]`), gen_null.py, an1/an2/an3/an4/an5/an6/an8.py (scoring, picks, neighbours, leave-one-episode-out, composites, equal-risk, placebo ranks, null summary, session picks), rep1.py, mkrep1.py.
SCORED (old cap): stage 1 complete: 3,033 nominal per-line cells (1,417 distinct masks) incl. 144 stacked-POI cells -> out/zones3/s2/s1_scored.pkl/.csv.gz, picks_s1.json, table_picks_s1.md, picks_diag_s1.pkl; job files jobs_gen_comp/plc.pkl generated (not run). Stage 2 (per-session) ~80% done (res_sess_*.pkl partial, resumable). Null (30 shuffled-label replicates), 200-draw placebos, equal-risk runs, composites: NOT run.
Interim (old cap, no placebo/null, all mean deltas inside MDE): 43% of changed cells have positive honest score, 20% positive post-hoc score. Best honest: camH3 40pts fw8 (+0.30 but L6M Calmar -26%), OTE705 60pts fw4 (Calmar +11/+27/+11/+33% L6M/HOLD/PRE/X'). Post-hoc: OTE705 75%tgt fw1 solo (L6M maxDD 22.9->17.7k), PDmid 40pts age 1-4h solo (STRICT). Honest and post-hoc picks disagree for 7 of 8 lines. LEAD labels only.
RESUME: update windows/cap in dd_lib/z2lib (WINS, MAT), rerun gen_jobs.py, workers s1 -> sess -> gen comp/er1/er2/plc -> null, then an1,an3,an4,an5,an6,an8, mkrep1.py. Re-run on out/d7base when BASE-1 delivers.

## NEW CAP interim 17:3xZ (Z2, cap 2026-10-31, windows L1M|L2M|L3M|L6M|HOLD|MID|PRE|X'); workers killed, stopped for the ledger re-score
Prereg addendum: l2vast/ds3/prereg/ZONES3_S2_REDO_prereg.md (sha256 in DECISIONS.md). Engine: one-convention composite via redo_boot (interim base; D7 base check not run). Tie-out: rebuilt 8-line mask == engine zone[20] (12,174 fires). Lines: poi_store_redo (8 streams; uncoded VAH/LVN1/HVN0 unavailable after 2026-02-06, so STK uses C8 only).
RAN: stage 1 complete (2,241 nominal per-line + STK cells, 1,198 distinct masks, ~2.8 s/run): out/zones3/s2/redo/s1_scored.pkl, picks_s1.json, table_picks_s1.md, picks_diag_s1.pkl (neighbour stability + LOEO), with OLD CAP S_hon/S_post as separate columns. Stage 2 (per-session) ~25% done (redo/res_sess_*.pkl partial, resumable). Job files for composites and 8,400 placebo draws generated (redo/jobs_gen_comp.pkl, jobs_gen_plc.pkl, cells_comp.pkl). NOT run: composites, equal-risk, null (15 shuffled replicates), placebos, session picks.
PARTIAL (no placebo/null yet, all mean deltas inside MDE, LEAD labels): honest picks (selected on PRE+X') mostly fail on the new L6M/HOLD: OTE705 60pts fw4 Calmar gain L6M -24% / HOLD -21% (was +11/+27% on the old cap); camH3 40pts fw8 L6M -2%, MID +104%; kijun1h 60pts a1-4 -21%/-19%. Holding on the new windows: CRT4h 30pts fw1 solo (L6M +11%, HOLD +13%, MID +14%, PRE +6%, X' +22%; neighbours 3/3 same sign, LOEO worst +0.14) and post-hoc CRT4h 30pts fw2 any (L6M +18%, HOLD +20%; STRICT/TOL, neighbours 4/4). No cell is RISK-KEEP on the new L6M. Shipped composite L6M maxDD 247.7k (Oct-26 week), so single-line changes move it little.
ENTRY POINTS (code l2vast/ds3/code/zones3/s2/): z2lib_redo.py, gen_jobs_redo.py, worker_redo.py (`python3 -I worker_redo.py <s1|sess|null|gen> <shard> 3 [tag]`, resumable), an1..an8_redo.py, mkrep1_redo.py, drive.sh (chain: wait sess -> gen comp -> er1 -> er2 -> session picks/comp -> null -> placebos; restart sess workers first, then `nohup ./drive.sh &`).


## s2 INTERIM (Z2, wall ~23:55Z 2026-11-01) - D / freshness / age / confluence per line, NEW windows, base D7 v1.1 sweep (zones HALF, lock 12R, U7 off) with v1.2 (U7) and v1.3 re-runs of every finalist. POST-HOC, LEAD labels, no PASS
Prereg autopilot-logged: ZONES3_S2_V12_prereg.md sha256 8c35b106a572fb057257c036b12c96d19e1adc0cefb48d863d3670889567842f (before scoring). Code l2vast/ds3/code/zones3/s2/, data l2vast/ds3/out/zones3/s2/v12/ (table_final_r2.md = the table below, s1_scored.csv.gz = all cells, candidate_grid_for_Z3.csv = grid for the walk-forward). Memory limited the run to 2 workers of ~10 GB (engine needs more than 6 GB).
**Bases (mean $k/wk / maxDD $k / Calmar):** v1.1 ship L6M 30.5/135.9/0.22, HOLD 26.1/135.9/0.19, MID 19.1/42.6/0.45, PRE 9.9/126.5/0.08, X' -4.5/233.9/-0.02, L1M 21.9/26.3. v1.2 (U7) L6M 26.0/127.8/0.20, MID 11.3/92.1, PRE 13.2/113.8. v1.3 L6M 21.3/94.1/0.23, HOLD 23.5/94.1/0.25, MID 19.7/43.1, PRE 2.9/175.1. The sweep is on v1.1 (2.3 s/run vs 12.6 s for v1.2); picks/composites are re-run on v1.2 and v1.3 and scored against their own shipped layer (last two columns).
**Cells swept:** stage 1 = 1,970 nominal per-line cells (7 lines x 9 D x 10 freshness/age types x confluence any/stk/solo + OFF + 72 stacked-POI) = 1,192 distinct masks run; D +-25/50% sensitivity 56 runs; v1.2/v1.3/lock-off re-runs of 20 finalists each. OTE-62 is not in the HALF mask (it is the B73 D30 row); its B73 distance sweep is in out as res_gen_ote62. Uncoded profile lines are not in this grid (poi_store_redo holds them; not yet added). Stage 2 per-session, the shuffled-label null (20 replicates) and the 200-draw placebos (3 kinds) are running: ranks in the table carry their draw count n; n below 50 is not a rank.
**Plain reading so far:** (1) 37% of changed cells have a positive honest score (selected on PRE+X'), 44% a positive post-hoc score; only 20 cells are STRICT, 29 TOLERANT, 546 NOW-ONLY (TOL-B 415, TOL-nc 278), 2 meet the L6M RISK-KEEP rule: a single cell is not evidence until the null lands. (2) Lines are not alike: camH3, CRT4h and OTE705 respond systematically (91%, 78%, 81% of their cells have positive post-hoc score: the shipped D20-fresh setting is not the recent optimum for them), KCup4h/OTE79/kijun1h respond little. (3) Best honest pick (camH3 20pts touched solo, S_hon +0.39, PRE Calmar +80%) fails the recent windows (L6M -17%, HOLD -10%); honest and post-hoc picks disagree on every line except CRT4h (60pts fresh solo: L6M +11%, HOLD +6%, PRE +6%, X' +7%, MID -38%; TOLERANT; 7/7 months of L6M keep a positive cut; D +-25/50% ROBUST-D; v1.3 +11%/+1%). (4) The composite of post-hoc picks C_post cuts L6M maxDD 135.9 -> 112.3k (-17%, below the 20% RISK-KEEP bar), Calmar +40% L6M / +24% HOLD but -59% MID, 0% PRE; on v1.3 +94% L6M and -17% HOLD: base-dependent, so LEAD only. (5) No cut is labelled ONE-WEEK on L6M (dropping the week 2026-09-07 that carries the shipped L6M maxDD leaves the sign), none has a placebo-beating rank yet. All mean deltas are inside their MDE.
| cell | own score | maxDD $k L6M / HOLD / MID / PRE / X' | Calmar gain L6M / HOLD / MID / PRE / X' | mean d L6M (MDE) | S/T/N | label | equal-risk mean d L6M | ONE-WEEK (cut w/o ship ddweek) | LOMO pos, min | boot 5-95 | D +-25/50 | placebo rank L6M cut cnt / vol / sday | v1.2 Calmar gain L6M / HOLD | v1.3 Calmar gain L6M / HOLD | vol tercile mean d low / mid / high |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PICK_hon|kijun1h | +0.112 | 139.9 / 139.9 / 42.6 / 111.5 / 217.5 | -5% / -4% / -1% / +24% / -1% | -0.6 (1.0) | -/-/- | no | -0.8 | no (-4%; wk 202637) | 0/7, -0.07 | -0.15..+0.00 | MIXED-D | 1.00 / 1.00 / 0.25 (n=3) | -4% / -5% | +13% / +3% | +0.3 / +1.0 / -0.0 |
| PICK_post|kijun1h | +0.155 | 126.8 / 126.8 / 44.1 / 127.1 / 230.9 | +18% / +13% / -9% / -3% / -1% | +3.1 (10.6) | -/-/N | no | -0.2 | no (+17%; wk 202637) | 6/7, -0.18 | -0.15..+0.43 | ROBUST-D | 0.25 / 0.25 / 0.25 (n=3) | +12% / +4% | +16% / +6% | +1.8 / -0.3 / -0.3 |
| PICK_hon|PDmid | +0.192 | 151.1 / 151.1 / 43.4 / 100.4 / 217.5 | -15% / -11% / +7% / +38% / +0% | -1.6 (5.0) | -/-/- | no | -1.7 | no (-13%; wk 202637) | 0/7, -0.26 | -0.31..+0.00 | MIXED-D | 1.00 / 1.00 / 1.00 (n=3) | -17% / -6% | +32% / +30% | +0.1 / +0.8 / +0.3 |
| PICK_post|PDmid | +0.080 | 127.5 / 127.5 / 44.1 / 105.6 / 216.0 | +7% / +9% / -0% / +30% / -1% | +0.0 (2.6) | -/-/- | no | +0.1 | no (+14%; wk 202637) | 6/7, -0.19 | -0.14..+0.24 | ROBUST-D | 0.50 / 0.25 / 0.25 (n=3) | -8% / +8% | +31% / +25% | +0.5 / +0.7 / +0.6 |
| PICK_hon|CRT4h | +0.067 | 125.3 / 125.3 / 52.1 / 122.8 / 291.5 | +11% / +6% / -38% / +6% / +7% | +0.7 (1.4) | -/T/N | no | +0.9 | no (+8%; wk 202637) | 7/7, +0.04 | +0.01..+0.11 | ROBUST-D | 0.50 / 0.25 / 0.50 (n=3) | +38% / +39% | +11% / +1% | -0.1 / -0.5 / -0.6 |
| PICK_post|CRT4h | +0.086 | 125.3 / 125.3 / 52.1 / 122.8 / 291.5 | +11% / +6% / -38% / +6% / +7% | +0.7 (1.4) | -/T/N | no | +0.9 | no (+8%; wk 202637) | 7/7, +0.04 | +0.01..+0.11 | ROBUST-D | 0.50 / 0.25 / 0.50 (n=3) | +38% / +39% | +11% / +1% | -0.1 / -0.5 / -0.6 |
| PICK_hon|KCup4h | +0.085 | 139.1 / 139.1 / 42.6 / 121.6 / 268.0 | -5% / +2% / +5% / +10% / +7% | -0.8 (1.0) | -/-/- | no | -0.6 | no (-3%; wk 202637) | 0/7, -0.06 | -0.14..+0.00 | ROBUST-D | 1.00 / 1.00 / 0.75 (n=3) | +1% / +10% | -4% / -4% | +1.2 / -0.3 / +0.2 |
| PICK_post|KCup4h | +0.023 | 135.9 / 135.9 / 42.6 / 125.4 / 237.4 | -1% / +5% / +2% / +6% / +4% | -0.2 (0.5) | -/-/- | no | -0.3 | no (+0%; wk 202637) | 0/7, +0.00 | -0.01..+0.00 | MIXED-D | 0.75 / 1.00 / 0.75 (n=3) | +4% / +12% | -0% / -0% | +1.4 / +0.2 / +0.1 |
| PICK_hon|camH3 | +0.392 | 145.4 / 145.4 / 44.0 / 94.0 / 231.7 | -17% / -10% / +4% / +80% / -2% | -3.4 (8.2) | -/-/- | no | -3.6 | no (-8%; wk 202637) | 0/7, -0.39 | -1.14..-0.01 | ROBUST-D | 1.00 / 0.75 / 1.00 (n=3) | -17% / -3% | -10% / -5% | +2.3 / +0.9 / +0.4 |
| PICK_post|camH3 | +0.077 | 124.5 / 124.5 / 66.2 / 99.9 / 292.5 | +12% / +3% / -58% / +42% / +6% | +0.8 (1.5) | -/T/N | no | +0.9 | no (+9%; wk 202637) | 7/7, +0.06 | +0.00..+0.19 | ROBUST-D | 0.75 / 0.25 / 0.50 (n=3) | +12% / +15% | +13% / +11% | +0.7 / +0.4 / -2.0 |
| PICK_hon|OTE705 | +0.050 | 131.9 / 131.9 / 46.8 / 123.8 / 283.6 | +6% / +2% / -17% / +4% / +6% | +0.9 (2.1) | -/-/N | no | +0.9 | no (+3%; wk 202637) | 6/7, -0.04 | -0.04..+0.26 | ROBUST-D | 0.75 / 0.50 / 0.25 (n=3) | -4% / -0% | +37% / +23% | -0.1 / -0.6 / -0.2 |
| PICK_post|OTE705 | +0.020 | 130.8 / 130.8 / 47.0 / 126.9 / 254.1 | +4% / -0% / -17% / +2% / +1% | +0.1 (2.3) | -/T/N | no | +0.6 | no (+4%; wk 202637) | 6/7, -0.02 | -0.02..+0.21 | ROBUST-D | 0.25 / 0.67 / 0.67 (n=3) | +54% / +39% | +54% / -7% | +0.1 / -0.3 / -1.2 |
| PICK_hon|OTE79 | +0.009 | 139.8 / 139.8 / 43.8 / 122.0 / 191.0 | -4% / -1% / -28% / +5% / -4% | -0.5 (1.2) | -/-/- | no | -0.6 | no (-3%; wk 202637) | 0/7, -0.07 | -0.05..+0.00 | FRAGILE | 1.00 / 0.67 / 0.67 (n=2) | -2% / +1% | +1% / -4% | +2.4 / +0.1 / -1.9 |
| PICK_post|OTE79 | +0.007 | 135.9 / 135.9 / 42.6 / 126.5 / 232.3 | +1% / +0% / -1% / -2% / -0% | +0.4 (0.8) | -/-/N | no | -4.4 | no (+0%; wk 202637) | 0/7, +0.00 | +0.00..+0.00 | FRAGILE | 0.67 / 0.33 / 0.33 (n=2) | +1% / +0% | +2% / -0% | +0.0 / -0.1 / -0.1 |
| PICK_hon|STK | +0.032 | 141.3 / 141.3 / 43.5 / 161.1 / 220.1 | -6% / -2% / +6% / -5% / +11% | -0.6 (4.9) | -/-/- | no | -5.3 | no (-3%; wk 202637) | 0/7, -0.10 | -0.12..+0.01 | n/a | 0.67 / 0.67 / 0.33 (n=2) | -8% / +8% | +38% / +9% | +2.9 / +0.2 / +0.2 |
| PICK_post|STK | +0.043 | 139.4 / 139.4 / 43.0 / 163.5 / 256.7 | -1% / +10% / +10% / -19% / +10% | +0.5 (4.4) | -/-/- | no | -4.4 | no (-12%; wk 202637) | 1/7, -0.13 | -0.31..+0.08 | n/a | 1.00 / 0.67 / 1.00 (n=2) | -17% / -2% | +26% / +3% | +5.5 / -0.9 / -1.3 |
| C_hon | +0.247 | 151.7 / 151.7 / 45.3 / 110.9 / 171.7 | -25% / -14% / -14% / +42% / +7% | -5.1 (10.5) | -/-/- | no | -4.9 | no (-14%; wk 202637) | 1/7, -0.39 | -1.24..+0.13 | n/a | 0.67 / 1.00 / 0.67 (n=2) | -18% / +3% | +10% / -3% | +5.3 / -1.3 / -0.6 |
| C_hon+STK | +0.032 | 141.3 / 141.3 / 43.5 / 161.1 / 220.1 | -6% / -2% / +6% / -5% / +11% | -0.6 (4.9) | -/-/- | no | -5.3 | no (-3%; wk 202637) | 0/7, -0.10 | -0.12..+0.01 | n/a | 0.67 / 0.67 / 1.00 (n=2) | -8% / +8% | +38% / +9% | +2.9 / +0.2 / +0.2 |
| C_post | +0.320 | 112.3 / 112.3 / 63.6 / 132.8 / 302.8 | +40% / +24% / -59% / +0% / +12% | +4.9 (10.3) | -/-/N | no | +4.3 | no (+17%; wk 202637) | 7/7, +0.09 | +0.01..+0.34 | n/a | 0.33 / 0.33 / 0.33 (n=2) | +53% / +59% | +94% / -17% | +3.6 / +0.2 / -4.4 |
| C_post+STK | +0.043 | 139.4 / 139.4 / 43.0 / 163.5 / 256.7 | -1% / +10% / +10% / -19% / +10% | +0.5 (4.4) | -/-/- | no | -4.4 | no (-12%; wk 202637) | 1/7, -0.13 | -0.31..+0.08 | n/a | 1.00 / 0.67 / 1.00 (n=2) | -17% / -2% | +26% / +3% | +5.5 / -0.9 / -1.3 |
(Columns: cell = PICK_hon|post|line from the honest (PRE+X') or post-hoc (L6M+HOLD, TOLERANT-gated when a TOLERANT cell exists) ranking, C_* = composite of all picks with positive own score; STK picks use mode ONLY, so C_*+STK equals the STK pick. Placebo ranks are shares of draws with an L6M maxDD cut at least as large (small = good). Vol tercile = weeks split by the shipped layer's within-week SD of daily P&L (volatility-regime proxy). Line parameter variants (swing strength, profile bin) do not exist for the 7 coded lines in poi_store_redo; stated as not done.)


## s2 UPDATE (Z2, wall ~00:35Z 2026-11-02): placebos (n=43 draws per kind) on the key cells; same base layout as the interim above
**Placebo verdict (L6M maxDD cut rank; share of random draws at least as good; 5% would be a beat):** no pick beats its placebos. CRT4h 60pts fresh solo 0.34 / 0.16 / 0.45 (random-level same-count / same-volume / shuffled-day line sets); camH3 75%tgt age>4h solo 0.18 / 0.18 / 0.23; kijun1h 15pts touched 0.23 / 0.23 / 0.14; OTE705 60pts fw2 0.51 / 0.44 / 0.63; composite C_post 0.34 / 0.27 / 0.23; C_hon (honest picks together) 0.86 / 0.91 / 0.86, i.e. worse than random. The only rank at or below 5% is a PRE cut (camH3 post-hoc pick, same-volume 0.02, PRE) while its X' cut ranks 0.95-1.00 (worse than random). So: every setting in the table is a LEAD of the weakest kind; none is RISK-KEEP; none is distinguishable from changing the layer at random with the same count or volume. Reading for Z3 and the policy file: keep the shipped D20 fresh for all seven half-lines unless a better test appears; CRT4h at a long D (60 pts) is the one line where the honest and post-hoc rankings and the D +-25/50% check agree, but it does not beat the placebo.
The null (best-of-N chance) and per-session stage are running (8 shuffled replicates; sess resumable). Placebo draws are capped at 43 per kind (rank resolution about 0.02).
| cell | own score | maxDD $k L6M / HOLD / MID / PRE / X' | Calmar gain L6M / HOLD / MID / PRE / X' | mean d L6M (MDE) | S/T/N | label | equal-risk mean d L6M | ONE-WEEK (cut w/o ship ddweek) | LOMO pos, min | boot 5-95 | D +-25/50 | placebo rank L6M cut cnt / vol / sday | v1.2 Calmar gain L6M / HOLD | v1.3 Calmar gain L6M / HOLD | vol tercile mean d low / mid / high |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PICK_hon|kijun1h | +0.112 | 139.9 / 139.9 / 42.6 / 111.5 / 217.5 | -5% / -4% / -1% / +24% / -1% | -0.6 (1.0) | -/-/- | no | -0.8 | no (-4%; wk 202637) | 0/7, -0.07 | -0.15..+0.00 | MIXED-D | 1.00 / 1.00 / 0.25 (n=3) | -4% / -5% | +13% / +3% | +0.3 / +1.0 / -0.0 |
| PICK_post|kijun1h | +0.155 | 126.8 / 126.8 / 44.1 / 127.1 / 230.9 | +18% / +13% / -9% / -3% / -1% | +3.1 (10.6) | -/-/N | no | -0.2 | no (+17%; wk 202637) | 6/7, -0.18 | -0.15..+0.43 | ROBUST-D | 0.23 / 0.23 / 0.14 (n=43) | +12% / +4% | +16% / +6% | +1.8 / -0.3 / -0.3 |
| PICK_hon|PDmid | +0.192 | 151.1 / 151.1 / 43.4 / 100.4 / 217.5 | -15% / -11% / +7% / +38% / +0% | -1.6 (5.0) | -/-/- | no | -1.7 | no (-13%; wk 202637) | 0/7, -0.26 | -0.31..+0.00 | MIXED-D | 1.00 / 1.00 / 1.00 (n=3) | -17% / -6% | +32% / +30% | +0.1 / +0.8 / +0.3 |
| PICK_post|PDmid | +0.080 | 127.5 / 127.5 / 44.1 / 105.6 / 216.0 | +7% / +9% / -0% / +30% / -1% | +0.0 (2.6) | -/-/- | no | +0.1 | no (+14%; wk 202637) | 6/7, -0.19 | -0.14..+0.24 | ROBUST-D | 0.50 / 0.25 / 0.25 (n=3) | -8% / +8% | +31% / +25% | +0.5 / +0.7 / +0.6 |
| PICK_hon|CRT4h | +0.067 | 125.3 / 125.3 / 52.1 / 122.8 / 291.5 | +11% / +6% / -38% / +6% / +7% | +0.7 (1.4) | -/T/N | no | +0.9 | no (+8%; wk 202637) | 7/7, +0.04 | +0.01..+0.11 | ROBUST-D | 0.34 / 0.16 / 0.45 (n=43) | +38% / +39% | +11% / +1% | -0.1 / -0.5 / -0.6 |
| PICK_post|CRT4h | +0.086 | 125.3 / 125.3 / 52.1 / 122.8 / 291.5 | +11% / +6% / -38% / +6% / +7% | +0.7 (1.4) | -/T/N | no | +0.9 | no (+8%; wk 202637) | 7/7, +0.04 | +0.01..+0.11 | ROBUST-D | 0.34 / 0.16 / 0.45 (n=43) | +38% / +39% | +11% / +1% | -0.1 / -0.5 / -0.6 |
| PICK_hon|KCup4h | +0.085 | 139.1 / 139.1 / 42.6 / 121.6 / 268.0 | -5% / +2% / +5% / +10% / +7% | -0.8 (1.0) | -/-/- | no | -0.6 | no (-3%; wk 202637) | 0/7, -0.06 | -0.14..+0.00 | ROBUST-D | 1.00 / 1.00 / 0.75 (n=3) | +1% / +10% | -4% / -4% | +1.2 / -0.3 / +0.2 |
| PICK_post|KCup4h | +0.023 | 135.9 / 135.9 / 42.6 / 125.4 / 237.4 | -1% / +5% / +2% / +6% / +4% | -0.2 (0.5) | -/-/- | no | -0.3 | no (+0%; wk 202637) | 0/7, +0.00 | -0.01..+0.00 | MIXED-D | 0.75 / 1.00 / 0.75 (n=3) | +4% / +12% | -0% / -0% | +1.4 / +0.2 / +0.1 |
| PICK_hon|camH3 | +0.392 | 145.4 / 145.4 / 44.0 / 94.0 / 231.7 | -17% / -10% / +4% / +80% / -2% | -3.4 (8.2) | -/-/- | no | -3.6 | no (-8%; wk 202637) | 0/7, -0.39 | -1.14..-0.01 | ROBUST-D | 1.00 / 0.75 / 1.00 (n=3) | -17% / -3% | -10% / -5% | +2.3 / +0.9 / +0.4 |
| PICK_post|camH3 | +0.077 | 124.5 / 124.5 / 66.2 / 99.9 / 292.5 | +12% / +3% / -58% / +42% / +6% | +0.8 (1.5) | -/T/N | no | +0.9 | no (+9%; wk 202637) | 7/7, +0.06 | +0.00..+0.19 | ROBUST-D | 0.18 / 0.18 / 0.23 (n=43) | +12% / +15% | +13% / +11% | +0.7 / +0.4 / -2.0 |
| PICK_hon|OTE705 | +0.050 | 131.9 / 131.9 / 46.8 / 123.8 / 283.6 | +6% / +2% / -17% / +4% / +6% | +0.9 (2.1) | -/-/N | no | +0.9 | no (+3%; wk 202637) | 6/7, -0.04 | -0.04..+0.26 | ROBUST-D | 0.75 / 0.50 / 0.25 (n=3) | -4% / -0% | +37% / +23% | -0.1 / -0.6 / -0.2 |
| PICK_post|OTE705 | +0.020 | 130.8 / 130.8 / 47.0 / 126.9 / 254.1 | +4% / -0% / -17% / +2% / +1% | +0.1 (2.3) | -/T/N | no | +0.6 | no (+4%; wk 202637) | 6/7, -0.02 | -0.02..+0.21 | ROBUST-D | 0.51 / 0.44 / 0.63 (n=42) | +54% / +39% | +54% / -7% | +0.1 / -0.3 / -1.2 |
| PICK_hon|OTE79 | +0.009 | 139.8 / 139.8 / 43.8 / 122.0 / 191.0 | -4% / -1% / -28% / +5% / -4% | -0.5 (1.2) | -/-/- | no | -0.6 | no (-3%; wk 202637) | 0/7, -0.07 | -0.05..+0.00 | FRAGILE | 1.00 / 0.67 / 0.67 (n=2) | -2% / +1% | +1% / -4% | +2.4 / +0.1 / -1.9 |
| PICK_post|OTE79 | +0.007 | 135.9 / 135.9 / 42.6 / 126.5 / 232.3 | +1% / +0% / -1% / -2% / -0% | +0.4 (0.8) | -/-/N | no | -4.4 | no (+0%; wk 202637) | 0/7, +0.00 | +0.00..+0.00 | FRAGILE | 0.67 / 0.33 / 0.33 (n=2) | +1% / +0% | +2% / -0% | +0.0 / -0.1 / -0.1 |
| PICK_hon|STK | +0.032 | 141.3 / 141.3 / 43.5 / 161.1 / 220.1 | -6% / -2% / +6% / -5% / +11% | -0.6 (4.9) | -/-/- | no | -5.3 | no (-3%; wk 202637) | 0/7, -0.10 | -0.12..+0.01 | n/a | 0.67 / 0.67 / 0.33 (n=2) | -8% / +8% | +38% / +9% | +2.9 / +0.2 / +0.2 |
| PICK_post|STK | +0.043 | 139.4 / 139.4 / 43.0 / 163.5 / 256.7 | -1% / +10% / +10% / -19% / +10% | +0.5 (4.4) | -/-/- | no | -4.4 | no (-12%; wk 202637) | 1/7, -0.13 | -0.31..+0.08 | n/a | 1.00 / 0.67 / 1.00 (n=2) | -17% / -2% | +26% / +3% | +5.5 / -0.9 / -1.3 |
| C_hon | +0.247 | 151.7 / 151.7 / 45.3 / 110.9 / 171.7 | -25% / -14% / -14% / +42% / +7% | -5.1 (10.5) | -/-/- | no | -4.9 | no (-14%; wk 202637) | 1/7, -0.39 | -1.24..+0.13 | n/a | 0.86 / 0.91 / 0.86 (n=43) | -18% / +3% | +10% / -3% | +5.3 / -1.3 / -0.6 |
| C_hon+STK | +0.032 | 141.3 / 141.3 / 43.5 / 161.1 / 220.1 | -6% / -2% / +6% / -5% / +11% | -0.6 (4.9) | -/-/- | no | -5.3 | no (-3%; wk 202637) | 0/7, -0.10 | -0.12..+0.01 | n/a | 0.67 / 0.67 / 1.00 (n=2) | -8% / +8% | +38% / +9% | +2.9 / +0.2 / +0.2 |
| C_post | +0.320 | 112.3 / 112.3 / 63.6 / 132.8 / 302.8 | +40% / +24% / -59% / +0% / +12% | +4.9 (10.3) | -/-/N | no | +4.3 | no (+17%; wk 202637) | 7/7, +0.09 | +0.01..+0.34 | n/a | 0.34 / 0.27 / 0.23 (n=43) | +53% / +59% | +94% / -17% | +3.6 / +0.2 / -4.4 |
| C_post+STK | +0.043 | 139.4 / 139.4 / 43.0 / 163.5 / 256.7 | -1% / +10% / +10% / -19% / +10% | +0.5 (4.4) | -/-/- | no | -4.4 | no (-12%; wk 202637) | 1/7, -0.13 | -0.31..+0.08 | n/a | 1.00 / 0.67 / 1.00 (n=2) | -17% / -2% | +26% / +3% | +5.5 / -0.9 / -1.3 |

## s2 FINAL-FOR-NOW (Z2, 2026-11-02 ~01:40Z): best-of-N chance null and verdict
**Best-of-N chance null (6 shuffled-label replicates complete of 8 planned; 238-cell reduced grid per replicate = 7 lines x 9 D x {fresh, touched, any, fw2}; real reduced grid beside):** max honest score (S_hon) in shuffled worlds 0.11 / 0.17 / 0.15 / 0.17 / 0.21 / 0.40 vs real 0.38 (full grid 0.39): the real maximum beats 5 of 6 nulls (not significant at 6 replicates; the 0.40 replicate shows chance alone reaches it). Max post-hoc score (S_post) null 0.23-0.55 vs real 0.33 (below the null median); max S_post among TOLERANT cells null 0.02-0.46 vs real 0.07-0.09. Cells passing the gates: real 2 STRICT / 6 TOLERANT / 68 NOW-ONLY of 238, null 12-27 / 18-51 / 62-99: the real lines pass the gates LESS often than shuffled lines. So the grid contains no signal beyond chance at this resolution; the table of picks is a ranking of noise-level differences. Ranked by what each ranking honestly says: CRT4h 60pts fresh solo (only agreement of the two rankings, ROBUST-D, 7/7 months), camH3 75%tgt age>4h solo, kijun1h 15pts touched, PDmid 15pts touched, OTE705 60pts fw2 solo; all LEAD-weak, none beats its three placebos, none is RISK-KEEP, base-dependent (v1.1 / v1.2 / v1.3 disagree in sign for several).
**Not done / resumable:** per-session stage (res_sess partial, `worker_v12.py sess`), 200 placebo draws (43 done), 2 more null replicates, uncoded profile lines in the grid, D7 v1.3 sweep (finalists re-run on v1.3 only), OTE-62 B73 D sweep scored but not tabulated (res_gen_ote62). Grid file for Z3: out/zones3/s2/v12/candidate_grid_for_Z3.csv. Entry: code/zones3/s2/{z2lib_v12,worker_v12,rep_final,rob,an*_v12}.py, drivers drive2-5.sh. DEAD_CELLS appended (program ZONES3_S2, 1,933 cells; never rebuilt).


## s2 on D7 v1.3 (Z2, wall ~02:05Z 2026-11-02) - finalists, per-session stage, profile lines, OTE-62 D sweep, robustness; POST-HOC, LEAD, no PASS
Base v1.3 (profit side = gated take lines U6/P6, best-effort; U7 on) shipped layer L6M 21.3k/wk, maxDD 94.1k; screening frame U7 off: L6M 27.3k, maxDD 107.3k. Finalists = the post-hoc picks of the v1.1 sweep (CRT4h 60pts fresh solo is the honest+post-hoc agreement). Code rep13.py, rep13b.py; data v12/table_rep13_a1.md, table_rep13b_b2.md.
**CRT4h 60pts fresh solo on v1.3 with U7 on (item 6):** L6M maxDD 94.1 -> 89.1k (-5%, below the 20% RISK-KEEP bar), L6M Calmar +11%, HOLD +1%, PRE +38%, X' +6%, **MID -58% (MID maxDD 43.1 -> 69.9k; mean change in MID -6.2k/wk, MDE 16.2: inside MDE but the drawdown is 62% deeper)**. It is not ONE-WEEK: dropping the week that carries the shipped L6M maxDD (ISO 2026-W38 on v1.3 U7) leaves a +6% cut; leave-one-week-out over the 27 L6M weeks keeps the cut positive in 27/27 (min +0.02, W38 +0.06); only 5/7 L6M months keep a positive cut; month-block bootstrap 5-95% of the cut -0.00..+0.27. Mean change L6M +1.2k (MDE 1.9). Placebo ranks on 100+ draws: see the placebo table below (filled as draws complete). The gain is carried by Asia (per book x session table: P6 Asia -7.7k L6M maxDD, -22.4k PRE; MID worsens in P6 Asia/London/NY-AM +12.6/+4.9/+7.0k).
**Per-session (item 1):** Asia is where the CRT4h line acts: 11 STRICT / 11 TOLERANT / 17 NOW-ONLY of 36 settings, best honest 60pts fresh (L6M +7%, PRE +39%), removing the line in Asia gives L6M +9% / PRE +14%; London, NY-AM, NY-PM cells are flat (0-2 TOLERANT). camH3: Asia PRE +52% when the line is removed there but L6M +1%; kijun1h removed in Asia: L6M +12% but PRE -66% (not a lead); PDmid: nothing in Asia, NY-AM has 8 TOLERANT cells at tiny size. A zone layer whose only live line is CRT4h-in-Asia is a different product from the shipped all-session layer (Asia carries the stack in 2026), consistent with the order's warning. LEAD pending placebo for the Asia-only cell.
**Profile lines added to the half mask (item 3, poi_store_redo streams):** HVN0 1h-swing: best honest 60pts fw2 (PRE +82%, X' +13%, L6M -1%), best post-hoc 30pts fw2 (L6M +2%, HOLD +1%), 2 STRICT of 36; LVN1 1h-swing: 94% of settings have positive honest score but L6M/HOLD gains are +2%; VAH 15m-swing: honest-only (PRE +86% at 20pts touched), L6M -7%, no post-hoc cell. Their honest and post-hoc scores disagree; no lead. **OTE-62 B73 D sweep:** shorter than D30 is worse (D10/15/20 L6M -24..-28%, PRE -9..-26% with U7 off); D40/60 improve L6M +11/+14% and HOLD +10/+15% but PRE -12/-7%: the shipped D30 is a local optimum on the honest windows, longer D is a recent-only effect (FRAGILE). With U7 on D40: L6M +8%, MID -15%, PRE -4%. **Line parameter variants (swing strength 2/3, profile bin 1/2 pt, anchor shifts): NOT DONE** - the poi_store_redo streams have one fixed definition per line; building variants is a profile-engine task (named gap). **Decision delay 1-s/3-s: N/A for skip/half** (the decision is taken at the signal second; it matters for B73/WT/re-target, which s2 does not sweep). **FRAGILE rule:** a cell is FRAGILE when at most 1 of the 4 D +-25/+-50% neighbours keeps a positive own score (computed on the v1.1 sweep: camH3 20pts-touched honest pick ROBUST-D, OTE79 picks FRAGILE; CRT4h/camH3/kijun1h/PDmid post-hoc picks ROBUST-D, but D=60 is the ladder end for CRT4h).

### v1.3 U7 OFF (screening frame): shipped layer L6M maxDD 107.3k mean 27.3k; MID 67.0k; PRE 192.4k

| finalist | maxDD $k L6M / HOLD / MID / PRE / X' | Calmar gain L6M / HOLD / MID / PRE / X' | mean d L6M (MDE) | mean d MID (MDE) | S/T/N | ONE-WEEK (cut w/o maxDD week) | leave-one-week-out L6M cut: min, #weeks cut<=0, W38 | LOMO | boot 5-95 | vol tercile mean d low/mid/high | equal-risk |
|---|---|---|---|---|---|---|---|---|---|---|---|
| CRT4h60 | 100.5 / 100.5 / 66.1 / 197.8 / 256.4 | +10% / +8% / +2% / +32% / +1% | +0.7 (1.0) | +0.0 (2.9) | -/T/N | no (+10%; wk 202637) | min +0.03, 0/27, W38 +0.06 | 7/7 months >0, min +0.01 | +0.01..+0.10 | +0.6/+0.5/+0.2 | n/a (see er) |
| camH3 | 98.1 / 98.1 / 67.8 / 193.2 / 331.8 | +11% / +8% / -3% / +16% / +30% | +0.3 (2.3) | -0.2 (2.7) | -/-/N | no (+4%; wk 202637) | min +0.00, 0/27, W38 +0.09 | 6/7 months >0, min +0.00 | +0.00..+0.19 | -0.5/-0.7/-1.3 | n/a (see er) |
| kijun1h | 102.3 / 102.3 / 70.1 / 214.6 / 270.4 | +14% / +10% / -6% / -6% / +1% | +2.4 (10.4) | -0.2 (2.5) | -/-/N | no (+4%; wk 202637) | min -0.01, 2/27, W38 +0.05 | 6/7 months >0, min +0.00 | -0.09..+0.33 | +1.6/+0.2/-0.6 | n/a (see er) |
| PDmid | 105.9 / 105.9 / 66.2 / 186.7 / 254.0 | +2% / +4% / +1% / +10% / +1% | +0.1 (1.8) | +0.0 (2.7) | -/-/- | no (+10%; wk 202637) | min -0.05, 3/27, W38 +0.01 | 5/7 months >0, min -0.00 | -0.10..+0.11 | -0.6/+1.1/+0.2 | n/a (see er) |

### v1.3 U7 ON (finalist frame): shipped layer L6M maxDD 94.1k mean 21.3k; MID 43.1k; PRE 175.1k

| finalist | maxDD $k L6M / HOLD / MID / PRE / X' | Calmar gain L6M / HOLD / MID / PRE / X' | mean d L6M (MDE) | mean d MID (MDE) | S/T/N | ONE-WEEK (cut w/o maxDD week) | leave-one-week-out L6M cut: min, #weeks cut<=0, W38 | LOMO | boot 5-95 | vol tercile mean d low/mid/high | equal-risk |
|---|---|---|---|---|---|---|---|---|---|---|---|
| CRT4h60 | 89.1 / 89.1 / 69.9 / 173.5 / 281.5 | +11% / +1% / -58% / +38% / +6% | +1.2 (1.9) | -6.2 (16.2) | -/T/N | no (+6%; wk 202638) | min +0.02, 0/27, W38 +0.06 | 5/7 months >0, min -0.01 | -0.00..+0.27 | +0.6/-0.2/-0.7 | n/a (see er) |
| camH3 | 84.1 / 84.1 / 43.1 / 179.2 / 305.3 | +13% / +11% / +0% / -6% / +32% | +0.1 (2.3) | +0.0 (2.6) | -/-/N | no (+9%; wk 202638) | min +0.00, 1/27, W38 +0.09 | 6/7 months >0, min +0.00 | +0.00..+0.21 | -0.0/-1.8/-1.1 | n/a (see er) |
| kijun1h | 89.1 / 89.1 / 47.0 / 195.4 / 257.3 | +16% / +6% / -29% / -6% / +2% | +2.1 (8.7) | -4.4 (12.0) | -/T/N | no (+4%; wk 202638) | min -0.00, 1/27, W38 +0.04 | 6/7 months >0, min +0.00 | -0.01..+0.29 | +1.6/-0.1/-1.5 | n/a (see er) |
| PDmid | 75.7 / 75.7 / 44.1 / 177.6 / 249.9 | +31% / +25% / -21% / +24% / +3% | +1.2 (3.1) | -3.7 (13.1) | -/-/N | no (+13%; wk 202638) | min -0.01, 1/27, W38 +0.13 | 5/7 months >0, min -0.03 | -0.03..+0.42 | -0.2/+1.0/-0.2 | n/a (see er) |

### CRT4h 60pts fresh solo, v1.3 U7 on: per book x session, change in maxDD and mean ($k, cell minus shipped; negative maxDD change = shallower)

| book | session | dDD L6M | dDD MID | dDD PRE | dDD X' | dmean L6M | dmean MID | dmean PRE | dmean X' |
|---|---|---|---|---|---|---|---|---|---|
| K6 | asia | +2.1 | +0.4 | +0.5 | -7.4 | +0.10 | -0.05 | +0.00 | +0.17 |
| K6 | london | +0.0 | -1.2 | -0.8 | +2.5 | +0.29 | +0.10 | +0.02 | -0.04 |
| K6 | nyam | +0.0 | +0.0 | +0.3 | -0.5 | +0.16 | -0.02 | +0.13 | -0.01 |
| K6 | nypm | +1.9 | -2.4 | -1.7 | +0.0 | -0.10 | +0.16 | +0.06 | +0.00 |
| P6 | asia | -7.7 | +12.6 | -22.4 | +0.9 | +0.70 | -0.98 | +0.38 | -0.00 |
| P6 | london | +0.0 | +4.9 | +2.6 | +0.5 | -0.11 | -3.36 | -0.02 | -0.01 |
| P6 | nyam | +0.0 | +7.0 | +0.0 | +0.0 | +0.00 | -0.58 | +0.41 | -0.73 |
| U6 | asia | -1.1 | -3.5 | +2.6 | +0.0 | -0.09 | +0.56 | -0.06 | -0.01 |
| U6 | london | +0.0 | +2.8 | +0.2 | -0.1 | +0.09 | -0.69 | +0.04 | -0.03 |
| H6 | asia | -3.0 | +3.3 | -8.3 | +9.3 | +0.02 | -0.97 | +0.12 | -0.23 |
| H6 | nyam | +0.2 | +0.4 | +3.6 | +2.3 | +0.03 | +0.12 | -0.05 | -0.10 |
| M6 | london | +0.0 | +3.5 | -0.2 | +1.2 | +0.14 | -0.36 | -0.01 | -0.03 |
| M6 | nyam | +0.4 | +5.8 | +0.0 | +4.8 | -0.01 | -0.34 | +0.08 | -0.11 |
| A6 | asia | +1.1 | -1.4 | +0.0 | -2.0 | -0.04 | +0.27 | -0.02 | +0.06 |

### s2 per-session stage on D7 v1.3 (U7 off, screening), 4 lines x 4 sessions, 36 settings + OFF each; shipped = D20 fresh in every session

| line | session | cells | share S_hon>0 | share S_post>0 | best honest (S_hon) | best post-hoc TOL-gated (S_post) | OFF (line removed in this session): Calmar gain L6M / PRE | n STRICT/TOL/NOW |
|---|---|---|---|---|---|---|---|---|
| CRT4h | asia | 36 | 0.53 | 0.69 | 60pts|fresh (+0.187; L6M +7%, PRE +39%) | 60pts|fw2 (+0.205) | +9% / +14% | 11/11/17 |
| CRT4h | london | 36 | 0.22 | 0.25 | 40pts|touched (+0.009; L6M -3%, PRE +3%) | 60pts|fresh (+0.016) | -3% / -1% | 0/2/8 |
| CRT4h | nyam | 36 | 0.25 | 0.28 | 40pts|touched (+0.115; L6M +0%, PRE +23%) | no TOL cell | +0% / -0% | 0/0/9 |
| CRT4h | nypm | 36 | 0.31 | 0.00 | 60pts|fresh (+0.001; L6M +0%, PRE +1%) | no TOL cell | +0% / +0% | 0/0/2 |
| PDmid | asia | 36 | 0.31 | 0.39 | 75%tgt|touched (+0.061; L6M -7%, PRE +11%) | no TOL cell | +5% / -6% | 0/0/0 |
| PDmid | london | 36 | 0.69 | 0.11 | 30pts|fresh (+0.189; L6M -4%, PRE +38%) | no TOL cell | +0% / +1% | 0/0/0 |
| PDmid | nyam | 36 | 0.56 | 0.56 | 10pts|touched (+0.090; L6M -1%, PRE +16%) | 75%tgt|fresh (+0.010) | -1% / +0% | 7/8/11 |
| PDmid | nypm | 36 | 0.00 | 0.25 | 10pts|fresh (+0.000; L6M +0%, PRE +0%) | no TOL cell | +0% / +0% | 0/0/0 |
| camH3 | asia | 36 | 0.94 | 0.58 | 60pts|fresh (+0.306; L6M -2%, PRE +31%) | no TOL cell | +1% / +52% | 0/0/19 |
| camH3 | london | 36 | 0.19 | 0.72 | 20pts|touched (+0.071; L6M -2%, PRE +17%) | 30pts|touched (+0.048) | +0% / +0% | 6/6/19 |
| camH3 | nyam | 36 | 0.31 | 0.00 | 10pts|fw2 (+0.026; L6M +0%, PRE +5%) | no TOL cell | +0% / +5% | 0/0/6 |
| camH3 | nypm | 36 | 0.56 | 0.00 | 60pts|touched (+0.016; L6M +0%, PRE +3%) | 30pts|touched (-0.000) | +0% / +0% | 0/5/5 |
| kijun1h | asia | 36 | 0.00 | 0.58 | 20pts|fresh (+0.000; L6M +0%, PRE +0%) | no TOL cell | +12% / -66% | 0/0/24 |
| kijun1h | london | 36 | 0.69 | 0.53 | 60pts|fresh (+0.225; L6M +3%, PRE +36%) | 60pts|fresh (+0.023) | +2% / +11% | 0/3/9 |
| kijun1h | nyam | 36 | 0.25 | 0.25 | 30pts|touched (+0.061; L6M -1%, PRE +11%) | no TOL cell | -2% / -1% | 0/0/0 |
| kijun1h | nypm | 36 | 0.25 | 0.08 | 15pts|touched (+0.002; L6M +0%, PRE +0%) | no TOL cell | +0% / +0% | 0/0/3 |

### the three profile lines ADDED to the half mask (v1.3, U7 off); shipped layer has them off

| line | cells | share S_hon>0 | share S_post>0 | best honest | best post-hoc (TOL gate if any) | STRICT/TOL/NOW |
|---|---|---|---|---|---|---|
| HVN0_1hs | 36 | 0.56 | 0.39 | 60pts|fw2 (+0.472; L6M -1%, PRE +82%, X' +13%) | 30pts|fw2 (+0.013; L6M +2%, HOLD +1%) | 2/4/9 |
| LVN1_1hs | 36 | 0.94 | 0.36 | 75%tgt|fw2 (+0.148; L6M -4%, PRE +19%, X' +11%) | 10pts|fresh (+0.015; L6M +2%, HOLD +2%) | 0/3/3 |
| VAH15s | 36 | 0.25 | 0.00 | 20pts|touched (+0.433; L6M -7%, PRE +86%, X' +0%) | 10pts|fw2 (-0.020; L6M -3%, HOLD -1%) | 0/0/0 |

### OTE-62 B73 distance sweep (v1.3), Calmar gain vs the D30 shipped B73

| ote62_D | frame | maxDD L6M / MID / PRE $k | Calmar gain L6M / HOLD / MID / PRE / X' |
|---|---|---|---|
| 10 | U7 off | 123.3 / 67.7 / 231.2 | -24% / -22% / -10% / -23% / +10% |
| 15 | U7 off | 123.4 / 66.0 / 212.9 | -26% / -22% / +5% / -9% / +10% |
| 20 | U7 off | 126.1 / 66.0 / 216.1 | -28% / -23% / +4% / -26% / +10% |
| 30 | U7 off | 107.3 / 67.0 / 192.4 | +0% / +0% / +0% / +0% / +0% |
| 40 | U7 off | 101.8 / 69.9 / 206.4 | +11% / +10% / -2% / -12% / -3% |
| 60 | U7 off | 99.1 / 74.1 / 202.1 | +14% / +15% / -2% / -7% / +0% |
| 20 | U7 on | 92.6 / 43.4 / 190.0 | +4% / +2% / +1% / -16% / +8% |
| 30 | U7 on | 94.1 / 43.1 / 175.1 | +0% / +0% / +0% / +0% / +0% |
| 40 | U7 on | 90.9 / 49.7 / 181.0 | +8% / +7% / -15% / -4% / -4% |

### placebo ranks on v1.3 (share of draws with an L6M / MID / PRE / X' maxDD cut at least as large; small = good); CRT4h on U7 ON vs its U7-on shipped layer, others U7 off

| finalist | kind | n | L6M cut (cell) | rank L6M | rank HOLD | rank MID | rank PRE | rank X' | rank Calmar L6M |
|---|---|---|---|---|---|---|---|---|---|


## s2 on v1.3: placebo ranks, interim at ~02:40Z (Z2)
CRT4h 60pts fresh solo with U7 ON, v1.3 (n about 67 draws per kind so far; the run continues to 120, then the Asia-only CRT4h cell and 2 more null replicates). **It does not beat any placebo on the L6M cut (ranks 0.32-0.60) and its MID cut ranks 0.85-0.99, i.e. worse than random; only the shuffled-day PRE rank (0.07) is near a beat.** With the MID maxDD +62% (Calmar -58%) the cell is a recent-window, Asia-carried, placebo-indistinguishable LEAD, not a RISK-KEEP. Reading for the policy file: keep the shipped D20 fresh; if the user wants one change to test forward, it is CRT4h in Asia only (per-session table) and it must pass its own placebo first (job queued: res_gen_plc13b).
### placebo ranks on v1.3 (share of draws with an L6M / MID / PRE / X' maxDD cut at least as large; small = good); CRT4h on U7 ON vs its U7-on shipped layer, others U7 off

| finalist | kind | n | L6M cut (cell) | rank L6M | rank HOLD | rank MID | rank PRE | rank X' | rank Calmar L6M |
|---|---|---|---|---|---|---|---|---|---|
| CRT4h60 | cnt | 67 | +5% | 0.60 | 0.60 | 0.94 | 0.31 | 0.93 | 0.54 |
| CRT4h60 | vol | 67 | +5% | 0.32 | 0.32 | 0.99 | 0.28 | 0.96 | 0.34 |
| CRT4h60 | sday | 66 | +5% | 0.57 | 0.55 | 0.85 | 0.07 | 0.72 | 0.49 |

## BASE LABEL (Z2, 2026-11-02 ~02:50Z): every s2 row above is on the ASSUMED base
All tables in the sections "s2 INTERIM", "s2 UPDATE", "s2 FINAL-FOR-NOW", "s2 on D7 v1.3" and "placebo ranks, interim" are on the ASSUMED base (D7 v1.1 sweep; v1.2 = U7 on all books both sides; v1.3-assumed = + U6/P6 take lines on rel_tot8), not the EXACT D7 v1.3 given by the user at 02:45Z. They are valid evidence about the assumed base only. Queued placebos finish on it; no new large grid is started on it. When BASE-4 announces V13X (d7_v13x.py) the finalists (CRT4h 60 fresh solo, CRT4h Asia-only, camH3, kijun1h, PDmid post-hoc picks) are re-run there and those rows become the headline; cut flips are reported as base-dependence.


## s2 HEADLINE on D7 v1.3 EXACT (V13X) - finalists (Z2, ~03:25Z 2026-11-02). Old rows above = ASSUMED base
Finalists are the picks made on the assumed v1.1 sweep; the full screen is re-run on V13X (s1x, then re-picks) and appended below when done. BASE-DEPENDENCE: CRT4h 60 fresh solo flips from assumed-v1.3 (L6M maxDD -5%, MID maxDD +62%, Calmar MID -58%) to V13X (L6M maxDD -8%, HOLD -15%, MID -15% with Calmar MID +104%, PRE -4%): the exact take lines remove the MID damage; kijun1h flips the other way (MID Calmar -76%). All inside MDE, STRICT/TOLERANT pass for CRT4h60 and CRT4h-Asia-only; placebo ranks pending.

### D7 v1.3 EXACT (V13X, lock 12R): shipped layer L6M 22.4k/wk maxDD 73.9k; HOLD maxDD 119.2k; MID maxDD 78.5k; PRE maxDD 252.4k

| finalist | maxDD $k L6M / HOLD / MID / PRE / X' | Calmar gain L6M / HOLD / MID / PRE / X' | mean d L6M (MDE) | mean d MID (MDE) | S/T/N | ONE-WEEK (cut w/o maxDD week) | leave-one-week-out L6M cut: min, #weeks <=0 | LOMO | boot 5-95 | vol tercile mean d low/mid/high |
|---|---|---|---|---|---|---|---|---|---|---|
| CRT4h60 | 67.9 / 101.8 / 66.7 / 242.3 / 167.1 | +9% / +22% / +104% / +17% / +0% | +0.1 (1.3) | +3.9 (5.6) | S/T/N | no (+11%; wk 202637) | min +0.03, 0/27 | 7/7 months >0, min +0.01 | -0.00..+0.11 | +0.2/+0.9/+0.2 |
| camH3 | 68.4 / 113.5 / 77.7 / 230.1 / 268.9 | +6% / +3% / +10% / -9% / +0% | -0.3 (2.8) | +0.5 (2.9) | -/-/- | no (+4%; wk 202637) | min +0.00, 1/27 | 5/7 months >0, min +0.00 | +0.00..+0.17 | +0.3/-0.7/-2.3 |
| kijun1h | 68.6 / 126.1 / 81.5 / 220.8 / 197.8 | +12% / -7% / -76% / +27% / -0% | +0.9 (5.7) | -4.0 (10.8) | -/-/N | no (+4%; wk 202637) | min +0.02, 0/27 | 5/7 months >0, min +0.00 | -0.01..+0.28 | +0.5/+0.7/-2.2 |
| PDmid | 64.4 / 116.0 / 77.9 / 223.5 / 226.8 | +18% / +7% / +2% / +65% / +0% | +0.6 (2.1) | +0.1 (1.5) | -/-/- | no (+11%; wk 202637) | min +0.03, 0/27 | 5/7 months >0, min +0.00 | -0.01..+0.11 | +1.0/+0.8/+0.2 |
| CRT4h60asia | 68.1 / 116.4 / 73.4 / 242.3 / 160.5 | +9% / +6% / +59% / +15% / +0% | +0.1 (1.1) | +2.6 (5.1) | S/T/N | no (+11%; wk 202637) | min -0.00, 1/27 | 7/7 months >0, min +0.01 | -0.00..+0.11 | +0.2/+0.8/+0.1 |
| OTE705 | 65.0 / 122.3 / 75.8 / 254.3 / 176.8 | +16% / -8% / +11% / -13% / -0% | +0.4 (2.3) | +0.4 (1.5) | -/-/- | no (+16%; wk 202637) | min +0.03, 0/27 | 5/7 months >0, min +0.00 | -0.18..+0.16 | -0.3/-0.9/-0.7 |

#### CRT4h60 on V13X: per book x session, change in maxDD and mean ($k, cell minus shipped; negative maxDD change = shallower)

| book | session | dDD L6M | dDD MID | dDD PRE | dDD X' | dmean L6M | dmean MID | dmean PRE | dmean X' |
|---|---|---|---|---|---|---|---|---|---|
| K6 | asia | +0.2 | -4.9 | +4.9 | -0.8 | +0.11 | +0.38 | -0.12 | +0.02 |
| K6 | london | +0.0 | -8.7 | -9.4 | +0.3 | -0.04 | +0.73 | +0.16 | +0.06 |
| K6 | nyam | +2.7 | +0.0 | -0.0 | +0.0 | -0.23 | -0.02 | +0.01 | -0.06 |
| K6 | nypm | -2.4 | -0.2 | -3.6 | +0.0 | +0.09 | +0.02 | -0.01 | +0.07 |
| P6 | asia | -2.9 | +0.0 | +3.9 | -1.0 | -0.07 | -0.02 | +0.21 | -0.11 |
| P6 | london | +0.6 | +0.6 | -6.7 | -10.8 | -0.11 | -0.08 | +0.20 | +0.31 |
| P6 | nyam | +0.0 | +0.0 | -9.6 | +2.1 | +0.00 | +0.00 | +0.18 | +0.02 |
| U6 | asia | -2.7 | -2.0 | +3.6 | +0.0 | +0.23 | +0.39 | -0.06 | -0.01 |
| U6 | london | +0.0 | -3.2 | -2.2 | +3.7 | +0.03 | +0.27 | +0.07 | -0.12 |
| H6 | asia | -3.0 | +0.1 | +11.4 | -0.7 | +0.15 | +1.42 | -0.15 | -0.01 |
| H6 | nyam | +2.2 | +0.7 | -2.5 | +0.6 | -0.11 | -0.14 | +0.03 | -0.13 |
| M6 | london | +0.0 | -0.6 | +2.9 | -0.7 | +0.00 | +0.58 | +0.00 | +0.09 |
| M6 | nyam | +0.0 | -1.0 | +0.0 | +0.0 | +0.00 | +0.49 | +0.04 | -0.00 |
| A6 | asia | -2.1 | +0.0 | +1.2 | +0.0 | +0.08 | -0.11 | -0.09 | +0.03 |

#### CRT4h60asia on V13X: per book x session, change in maxDD and mean ($k, cell minus shipped; negative maxDD change = shallower)

| book | session | dDD L6M | dDD MID | dDD PRE | dDD X' | dmean L6M | dmean MID | dmean PRE | dmean X' |
|---|---|---|---|---|---|---|---|---|---|
| K6 | asia | +0.2 | -4.7 | +4.9 | -0.8 | +0.11 | +0.10 | -0.12 | +0.02 |
| K6 | london | +0.0 | -7.9 | -8.6 | -0.1 | +0.00 | +0.66 | +0.14 | +0.05 |
| K6 | nyam | +3.7 | +0.0 | -0.0 | +0.0 | -0.27 | -0.02 | +0.02 | -0.02 |
| K6 | nypm | -3.1 | +0.6 | -2.9 | +0.0 | +0.11 | -0.05 | -0.02 | +0.07 |
| P6 | asia | -2.9 | +0.0 | +5.4 | -1.0 | -0.07 | +0.32 | +0.19 | -0.11 |
| P6 | london | +0.0 | +0.0 | -6.9 | -10.1 | -0.11 | +0.00 | +0.19 | +0.29 |
| P6 | nyam | +0.0 | +0.0 | -9.6 | +0.0 | +0.00 | +0.00 | +0.19 | +0.07 |
| U6 | asia | -2.7 | -2.0 | +3.6 | +0.0 | +0.23 | +0.43 | -0.06 | -0.02 |
| U6 | london | +0.0 | -1.2 | -3.5 | +3.8 | +0.00 | +0.10 | +0.05 | -0.13 |
| H6 | asia | -3.0 | +1.7 | +11.7 | -0.7 | +0.15 | +1.28 | -0.16 | -0.01 |
| H6 | nyam | +2.2 | +1.5 | -2.5 | +0.0 | -0.11 | -0.21 | +0.03 | -0.03 |
| M6 | london | +0.0 | +0.0 | +2.9 | -0.6 | +0.00 | +0.00 | +0.00 | +0.09 |
| A6 | asia | -2.1 | +0.0 | +1.2 | +0.1 | +0.08 | -0.11 | -0.09 | +0.02 |

#### placebo ranks on V13X (share of draws with an L6M / MID / PRE / X' maxDD cut at least as large; small = good)

| finalist | kind | n | L6M cut (cell) | rank L6M | rank HOLD | rank MID | rank PRE | rank X' | rank Calmar L6M |
|---|---|---|---|---|---|---|---|---|---|


## s2 HEADLINE: full screen re-run on D7 v1.3 EXACT (V13X, lock 12R), ~04:20Z 2026-11-02 (picks re-made on the exact base)
Same 1,192-mask grid (7 lines x 9 D x 10 freshness/age types x confluence any/stk/solo + OFF + stacked rule), 2.3-4 s/run. **On the exact base CRT4h is the line that carries the layer, in every window:** honest pick CRT4h 30pts fresh solo (Calmar gain L6M +1%, HOLD +17%, MID +43%, PRE +33%, X' flat; 4/4 neighbours same sign, leave-one-episode-out min +0.08) and post-hoc pick CRT4h 60pts fresh solo (L6M +9%, HOLD +22%, MID +104%, PRE +17%; STRICT, TOLERANT, NOW-ONLY; L6M maxDD 73.9 -> 67.9k, HOLD 119.2 -> 101.8k, MID 78.5 -> 66.7k; neighbours 3/3; LOEO min +0.09). On the assumed base the same cells read L6M -5% / MID +62% maxDD (cut flips = base dependence, reported). Nine cells meet the literal L6M RISK-KEEP rule (e.g. OTE705 60pts fw2 any: L6M maxDD 73.9 -> 58.1k, -21%, but HOLD -6%, PRE +4%, LOEO min -0.13): L6M-only, not a lead. Gate counts (1,933 changed cells): STRICT 22, TOLERANT 41, NOW-ONLY 448 (TOL-B 281, TOL-nc 86); positive honest score 45%, positive post-hoc score 57%. Other lines: camH3, PDmid, kijun1h, OTE79, KCup4h picks disagree between honest and post-hoc rankings (cells that help PRE hurt HOLD/L6M or the reverse); the stacked rule ONLY mode (60pts) helps L6M/HOLD (+17%/+48%) and hurts PRE (-47%). Placebos (200 draws x 3 kinds, 6 finalists) and the V13X null are queued behind this; table below.
V13X full screen: 1933 changed distinct-key cells; S_hon>0 0.45, S_post>0 0.57; STRICT 22, TOL 41, NOW 448, TOL-B 281, TOL-nc 86, RISK-KEEP(L6M rule) 9

| line | pick | cell | maxDD $k L6M / HOLD / MID / PRE / X' | Calmar gain L6M / HOLD / MID / PRE / X' | mean d L6M (MDE) | S/T/N | RK | neighbours n, mean S, same sign | LOEO worst S (episode) |
|---|---|---|---|---|---|---|---|---|---|
| CRT4h | HONEST | CRT4h|30pts|fresh|solo | 72.9 / 104.2 / 75.2 / 219.0 / 172.1 | +1% / +17% / +43% / +33% / +0% | -0.1 (0.5) | -/-/- | no | 4, +0.10, 4/4 | +0.08 (202435-202516) |
| CRT4h | POST-HOC | CRT4h|60pts|fresh|solo | 67.9 / 101.8 / 66.7 / 242.3 / 167.1 | +9% / +22% / +104% / +17% / +0% | +0.1 (1.3) | S/T/N | no | 3, +0.15, 3/3 | +0.09 (202604-202613) |
| KCup4h | HONEST | KCup4h|75%tgt|fw2|any | 77.6 / 84.2 / 78.5 / 198.3 / 190.6 | -10% / +42% / -6% / +76% / +0% | -1.2 (1.6) | -/-/- | no | 3, +0.30, 3/3 | +0.01 (202435-202516) |
| KCup4h | POST-HOC (ungated) | KCup4h|30pts|fw2|any | 77.6 / 84.2 / 78.5 / 196.3 / 186.3 | -7% / +56% / +44% / +64% / +0% | -0.5 (0.7) | -/-/- | no | 4, +0.09, 2/4 | -0.05 (202604-202613) |
| OTE705 | HONEST | OTE705|40pts|touched|solo | 69.7 / 128.5 / 83.9 / 231.9 / 166.2 | -7% / -16% / -11% / +15% / +0% | -2.7 (9.4) | -/-/- | no | 3, +0.02, 2/3 | -0.03 (202435-202516) |
| OTE705 | POST-HOC | OTE705|60pts|fw2|any | 58.1 / 121.6 / 75.1 / 248.7 / 169.4 | +31% / -6% / +16% / +4% / +0% | +0.8 (2.3) | -/T/N | yes | 3, +0.07, 3/3 | -0.13 (202628-202637) |
| OTE79 | HONEST | OTE79|20pts|fw1|any | 72.6 / 123.0 / 82.3 / 217.1 / 171.8 | +2% / -2% / +33% / +21% / +0% | -0.0 (0.6) | -/-/- | no | 3, -0.03, 1/3 | -0.02 (202435-202516) |
| OTE79 | POST-HOC (ungated) | OTE79|75%tgt|a1-4|any | 66.4 / 66.4 / 62.4 / 284.2 / 166.2 | +11% / +98% / +47% / -43% / +0% | -0.0 (1.2) | -/-/- | no | 3, +0.01, 2/3 | +0.11 (202604-202613) |
| PDmid | HONEST | PDmid|30pts|touched|any | 67.8 / 113.4 / 74.7 / 224.7 / 217.8 | +10% / +7% / -1% / +67% / +0% | +0.2 (2.4) | -/-/- | no | 3, +0.25, 3/3 | -0.01 (202435-202516) |
| PDmid | POST-HOC (ungated) | PDmid|75%tgt|fw4|stk | 73.1 / 76.8 / 73.8 / 287.3 / 209.1 | +5% / +76% / +21% / -37% / +0% | +0.9 (2.2) | -/-/- | no | 3, +0.16, 3/3 | +0.05 (202604-202613) |
| STK | HONEST | STK|C8|clu3|fresh|30pts|add | 73.9 / 119.2 / 78.5 / 251.9 / 173.7 | +0% / +0% / -1% / +1% / +0% | +0.0 (0.0) | -/-/- | no | 4, -0.02, 1/4 | +0.00 (202435-202516) |
| STK | POST-HOC (ungated) | STK|C8|stk2|fresh|60pts|only | 66.9 / 88.9 / 88.9 / 294.6 / 178.2 | +17% / +48% / +43% / -47% / -12% | +1.4 (3.8) | -/-/- | no | 3, +0.27, 3/3 | +0.17 (202604-202613) |
| camH3 | HONEST | camH3|60pts|touched|solo | 97.9 / 112.8 / 62.8 / 195.2 / 172.1 | -31% / +7% / +86% / +116% / -20% | -1.9 (3.4) | -/-/- | no | 2, +0.28, 2/2 | +0.02 (202435-202516) |
| camH3 | POST-HOC (ungated) | camH3|60pts|fresh|solo | 67.4 / 77.9 / 55.3 / 200.6 / 245.7 | +7% / +51% / +63% / +35% / -0% | -0.6 (3.2) | -/-/- | no | 3, +0.18, 3/3 | +0.05 (202604-202613) |
| kijun1h | HONEST | kijun1h|10pts|touched|stk | 71.8 / 124.8 / 80.8 / 218.4 / 203.0 | +1% / -6% / -5% / +47% / +0% | -0.5 (1.5) | -/-/- | no | 2, +0.05, 1/2 | +0.02 (202435-202516) |
| kijun1h | POST-HOC | kijun1h|60pts|fresh|solo | 71.7 / 112.6 / 78.3 / 217.1 / 151.7 | +10% / +2% / +1% / +29% / -4% | +1.5 (4.9) | -/T/N | no | 3, +0.01, 2/3 | +0.01 (202628-202637) |


## s2 LOCK-OFF FRAME (V13X, lock=None = per-book locks only) = HEADLINE until the user confirms the combined 12R lock (Z2, ~05:00Z)
Per the lead's rule every finalist is scored in both frames; a cut present only with lock=12 is LOCK-ONLY. In the lock-off frame the shipped layer reads L6M 26.9k/wk, maxDD 132.6k (HOLD 132.6k, MID 62.6k, PRE 178.4k). **CRT4h 60pts fresh solo: L6M maxDD 132.6 -> 127.2k (-4%), HOLD 132.6 -> 130.2k, MID 62.6 -> 56.4k (Calmar +38%), PRE 178.4 -> 203.5k (Calmar -16%), X' -6%; only NOW-ONLY (fails TOLERANT on PRE), cut +2% without the maxDD week (W34), 6/7 months, bootstrap -0.12..+0.11: the lock=12 headline (STRICT, L6M -8%, HOLD -15%, MID -15%) is largely LOCK-ONLY.** Others lock-off: PDmid post-hoc pick L6M Calmar +17%, HOLD +11%, X' +62%, PRE +2% (not TOL, 6/7 months); kijun1h L6M +10%; camH3 ~flat; OTE705 L6M -9% (the lock=12 RISK-KEEP is LOCK-ONLY). The full lock-off screen (1,192 masks) is running; its re-picks replace the picks above when done.

### D7 v1.3 EXACT (V13X, lock=None: per-book locks only) - HEADLINE FRAME: shipped layer L6M 26.9k/wk maxDD 132.6k; HOLD maxDD 132.6k; MID maxDD 62.6k; PRE maxDD 178.4k

| finalist | maxDD $k L6M / HOLD / MID / PRE / X' | Calmar gain L6M / HOLD / MID / PRE / X' | mean d L6M (MDE) | mean d MID (MDE) | S/T/N | ONE-WEEK (cut w/o maxDD week) | leave-one-week-out L6M cut: min, #weeks <=0 | LOMO | boot 5-95 | vol tercile mean d low/mid/high |
|---|---|---|---|---|---|---|---|---|---|---|
| CRT4h60 | 127.2 / 130.2 / 56.4 / 203.5 / 137.4 | +6% / +4% / +38% / -16% / -6% | +0.4 (2.0) | +2.6 (6.8) | -/-/N | no (+2%; wk 202634) | min -0.04, 1/27 | 6/7 months >0, min -0.04 | -0.12..+0.11 | +0.3/+0.5/-0.8 |
| camH3 | 125.3 / 129.5 / 61.9 / 170.0 / 158.7 | +3% / -1% / -1% / +1% / +23% | -0.7 (3.0) | -0.2 (2.4) | -/-/- | no (+1%; wk 202634) | min +0.01, 0/27 | 7/7 months >0, min +0.01 | -0.07..+0.07 | -0.6/+0.1/-1.5 |
| kijun1h | 117.3 / 123.7 / 69.0 / 174.8 / 142.2 | +10% / +4% / -9% / -0% / -18% | -0.8 (3.5) | +0.0 (2.5) | -/-/- | no (+9%; wk 202634) | min +0.01, 0/27 | 7/7 months >0, min +0.07 | +0.00..+0.12 | +0.2/-0.1/-0.6 |
| PDmid | 116.3 / 122.9 / 66.0 / 176.9 / 150.4 | +17% / +11% / -5% / +2% / +62% | +0.8 (3.2) | +0.1 (2.7) | -/-/- | no (+14%; wk 202634) | min -0.00, 1/27 | 6/7 months >0, min -0.03 | -0.05..+0.22 | -0.1/+0.1/-0.2 |
| CRT4h60asia | 127.6 / 131.3 / 58.2 / 200.6 / 132.6 | +6% / +4% / +22% / -14% / -16% | +0.5 (1.8) | +1.5 (6.1) | -/-/N | no (+3%; wk 202634) | min -0.03, 2/27 | 6/7 months >0, min -0.03 | -0.05..+0.04 | +0.4/+0.5/-0.7 |
| OTE705 | 143.2 / 143.2 / 65.3 / 178.1 / 156.3 | -9% / -11% / +5% / +0% / +80% | -0.5 (3.2) | +1.0 (2.6) | -/-/- | no (-12%; wk 202634) | min -0.19, 26/27 | 1/7 months >0, min -0.19 | -0.23..+0.13 | -0.4/-0.6/-1.0 |

#### CRT4h60 on V13X: per book x session, change in maxDD and mean ($k, cell minus shipped; negative maxDD change = shallower)

| book | session | dDD L6M | dDD MID | dDD PRE | dDD X' | dmean L6M | dmean MID | dmean PRE | dmean X' |
|---|---|---|---|---|---|---|---|---|---|
| K6 | asia | -1.2 | -0.7 | +6.1 | -2.8 | +0.15 | -0.04 | -0.20 | +0.06 |
| K6 | london | -0.0 | -2.1 | +3.9 | +0.5 | -0.05 | +0.29 | -0.05 | -0.02 |
| K6 | nyam | +3.4 | -0.9 | +1.1 | +0.0 | -0.25 | +0.07 | +0.01 | -0.03 |
| K6 | nypm | -1.2 | +1.6 | +4.3 | +0.0 | +0.04 | -0.09 | -0.15 | +0.00 |
| P6 | asia | -5.2 | +0.7 | -7.4 | +3.8 | +0.00 | +1.02 | +0.22 | +0.47 |
| P6 | london | +1.5 | +0.0 | +5.7 | +3.0 | +0.13 | -0.30 | +0.04 | -0.07 |
| P6 | nyam | +0.0 | +12.9 | +0.5 | +0.0 | +0.00 | -1.08 | -0.09 | -0.34 |
| U6 | asia | -2.0 | -3.1 | +0.0 | +0.3 | +0.26 | +0.53 | -0.11 | -0.02 |
| U6 | london | +0.0 | -1.3 | +1.6 | +0.0 | +0.03 | +0.17 | +0.02 | +0.00 |
| H6 | asia | -1.8 | +3.1 | -1.9 | -1.6 | +0.03 | +1.15 | -0.06 | +0.06 |
| H6 | nyam | +1.9 | +2.3 | -0.4 | +0.2 | -0.09 | -0.18 | -0.01 | -0.04 |
| M6 | london | +0.0 | -0.6 | -0.8 | +0.0 | +0.01 | +0.58 | +0.01 | +0.00 |
| M6 | nyam | +0.0 | -0.9 | +0.0 | +0.0 | +0.00 | +0.40 | +0.02 | -0.00 |
| A6 | asia | -1.9 | +0.0 | +0.0 | +0.0 | +0.12 | +0.10 | -0.03 | -0.03 |

#### CRT4h60asia on V13X: per book x session, change in maxDD and mean ($k, cell minus shipped; negative maxDD change = shallower)

| book | session | dDD L6M | dDD MID | dDD PRE | dDD X' | dmean L6M | dmean MID | dmean PRE | dmean X' |
|---|---|---|---|---|---|---|---|---|---|
| K6 | asia | -1.2 | -0.7 | +6.2 | -2.8 | +0.15 | -0.04 | -0.20 | +0.06 |
| K6 | london | +0.0 | -1.4 | +1.6 | +0.0 | -0.01 | +0.23 | -0.02 | +0.00 |
| K6 | nyam | +4.4 | -1.5 | +1.8 | +0.0 | -0.29 | +0.12 | +0.01 | +0.00 |
| K6 | nypm | -1.8 | +2.4 | +1.2 | +0.0 | +0.07 | -0.20 | -0.11 | +0.00 |
| P6 | asia | -5.2 | +0.7 | -7.4 | +3.8 | +0.00 | +1.02 | +0.22 | +0.47 |
| P6 | london | +2.9 | +0.0 | +4.5 | +3.0 | +0.30 | -0.10 | +0.03 | -0.07 |
| P6 | nyam | +0.0 | +12.9 | +0.0 | +0.0 | +0.00 | -1.08 | -0.02 | -0.32 |
| U6 | asia | -2.0 | -3.1 | +0.0 | +0.3 | +0.26 | +0.53 | -0.11 | -0.02 |
| H6 | asia | -1.8 | +3.1 | -1.9 | -1.6 | +0.03 | +1.15 | -0.06 | +0.06 |
| H6 | nyam | +1.9 | +2.7 | -0.4 | +0.0 | -0.09 | -0.25 | -0.01 | +0.05 |
| A6 | asia | -1.9 | +0.0 | +0.0 | +0.0 | +0.12 | +0.10 | -0.03 | -0.03 |

#### placebo ranks on V13X (share of draws with an L6M / MID / PRE / X' maxDD cut at least as large; small = good)

| finalist | kind | n | L6M cut (cell) | rank L6M | rank HOLD | rank MID | rank PRE | rank X' | rank Calmar L6M |
|---|---|---|---|---|---|---|---|---|---|


## s2 HEADLINE FRAME: full screen on V13X with lock=None (per-book locks only), ~05:20Z 2026-11-02
The 1,192-mask grid re-run with the combined 12R lock removed. Counts (1,933 changed cells): STRICT 46, TOLERANT 110, NOW-ONLY 663 (TOL-B 492, TOL-nc 143); positive honest score 47%, positive post-hoc score 35%; **0 cells meet the L6M RISK-KEEP rule** (the 9 of the lock=12 frame were LOCK-ONLY). Picks (labelled LEAD, placebos queued): CRT4h 30pts fw2 solo (post-hoc; STRICT: L6M +8%, HOLD +9%, MID +6%, PRE +4%, X' -29%; L6M maxDD 132.6 -> 124.3k = -6%; 4/4 neighbours), camH3 40pts fw8 any (post-hoc; STRICT: L6M +9%, MID +39%, X' -26%; maxDD 132.6 -> 123.1k), PDmid 20pts touched solo (TOL: L6M +14%, HOLD +14%, X' +45%, PRE +5%), PDmid 30pts touched stacked (honest; L6M +13%). The honest and post-hoc picks again disagree for CRT4h/KCup4h/OTE705/OTE79/kijun1h; the lock=12 favourite CRT4h 60pts fresh solo is NOW-ONLY here. All inside MDE; maxDD cuts at most 6-10%.
V13X lock=None full screen: 1933 changed distinct-key cells; S_hon>0 0.47, S_post>0 0.35; STRICT 46, TOL 110, NOW 663, TOL-B 492, TOL-nc 143, RISK-KEEP(L6M rule) 0

| line | pick | cell | maxDD $k L6M / HOLD / MID / PRE / X' | Calmar gain L6M / HOLD / MID / PRE / X' | mean d L6M (MDE) | S/T/N | RK | neighbours n, mean S, same sign | LOEO worst S (episode) |
|---|---|---|---|---|---|---|---|---|---|
| CRT4h | HONEST | CRT4h|75%tgt|touched|solo | 152.4 / 152.4 / 74.5 / 194.7 / 161.7 | -15% / -12% / -11% / -17% / +84% | -0.7 (3.2) | -/-/- | no | 2, +0.11, 1/2 | -0.49 (202314-202337) |
| CRT4h | POST-HOC | CRT4h|30pts|fw2|solo | 124.3 / 124.3 / 66.7 / 178.0 / 134.3 | +8% / +9% / +6% / +4% / -29% | +0.3 (1.0) | S/T/N | no | 4, +0.06, 4/4 | +0.02 (202628-202634) |
| KCup4h | HONEST | KCup4h|40pts|a1-4|any | 135.9 / 135.9 / 58.5 / 182.9 / 134.8 | -4% / -2% / +10% / -1% / +36% | -0.4 (1.0) | -/-/- | no | 4, +0.03, 4/4 | -0.21 (202314-202337) |
| KCup4h | POST-HOC (ungated) | KCup4h|60pts|fresh|stk | 131.9 / 131.9 / 62.6 / 179.4 / 132.4 | -0% / +1% / -2% / -1% / +5% | -0.2 (0.5) | -/-/- | no | 3, +0.00, 2/3 | -0.03 (202628-202634) |
| OTE705 | HONEST | OTE705|40pts|fw2|solo | 141.8 / 141.8 / 63.7 / 160.4 / 160.3 | -7% / -8% / -1% / +16% / +87% | -0.2 (3.3) | -/-/- | no | 4, +0.38, 4/4 | -0.03 (202314-202337) |
| OTE705 | POST-HOC (ungated) | OTE705|30pts|a1-4|solo | 126.7 / 126.7 / 66.0 / 182.0 / 133.6 | +7% / +7% / -3% / -5% / -12% | +0.5 (1.6) | -/-/N | no | 4, -0.02, 2/4 | +0.03 (202628-202634) |
| OTE79 | HONEST | OTE79|40pts|fw2|any | 138.3 / 138.3 / 61.3 / 177.6 / 150.4 | -6% / -6% / -4% / +4% / +91% | -0.5 (1.7) | -/-/- | no | 4, +0.27, 3/4 | -0.10 (202314-202337) |
| OTE79 | POST-HOC | OTE79|20pts|fw2|any | 132.6 / 132.6 / 62.6 / 178.4 / 136.0 | +1% / +0% / +0% / +0% / +1% | +0.2 (0.5) | -/T/N | no | 4, -0.03, 1/4 | +0.00 (202606-202607) |
| PDmid | HONEST | PDmid|30pts|touched|stk | 117.9 / 122.9 / 63.8 / 176.7 / 154.4 | +13% / +7% / -11% / +3% / +71% | +0.0 (2.9) | -/-/- | no | 3, +0.33, 3/3 | +0.04 (202314-202337) |
| PDmid | POST-HOC | PDmid|20pts|touched|solo | 123.3 / 123.3 / 65.5 / 173.1 / 140.5 | +14% / +14% / +3% / +5% / +45% | +1.5 (2.6) | -/T/N | no | 3, +0.04, 2/3 | +0.07 (202628-202634) |
| STK | HONEST | STK|C8|stk2|fresh|40pts|add | 144.8 / 144.8 / 69.1 / 187.0 / 127.7 | -12% / -5% / -2% / -5% / +34% | -1.0 (1.8) | -/-/- | no | 4, +0.02, 3/4 | +0.07 (202314-202337) |
| STK | POST-HOC (ungated) | STK|C8|clu3|fresh|30pts|only | 136.8 / 136.8 / 84.3 / 211.8 / 144.3 | +4% / +4% / -16% / -28% / -86% | +1.8 (3.9) | -/-/- | no | 4, -0.01, 3/4 | +0.02 (202606-202607) |
| camH3 | HONEST | camH3|40pts|fw4|stk | 127.4 / 127.4 / 61.4 / 180.2 / 149.9 | +5% / +7% / +10% / -1% / +62% | +0.3 (0.8) | -/-/N | no | 4, +0.15, 4/4 | +0.06 (202314-202337) |
| camH3 | POST-HOC | camH3|40pts|fw8|any | 123.1 / 123.1 / 46.4 / 181.2 / 123.6 | +9% / +11% / +39% / +2% / -26% | +0.3 (1.5) | S/T/N | no | 4, +0.06, 4/4 | +0.04 (202628-202634) |
| kijun1h | HONEST | kijun1h|60pts|fw1|solo | 123.6 / 123.6 / 63.9 / 183.7 / 147.2 | +8% / +6% / -2% / -6% / +85% | +0.2 (2.8) | -/-/N | no | 2, +0.19, 2/2 | -0.11 (202314-202337) |
| kijun1h | POST-HOC | kijun1h|60pts|a1-4|stk | 135.3 / 135.3 / 68.5 / 170.0 / 138.3 | -1% / +2% / -1% / +7% / -39% | +0.3 (1.1) | S/T/N | no | 3, -0.02, 1/3 | -0.01 (202606-202607) |


## s2 CORRECTION and CORRECTED headline (Z2, ~05:50Z 2026-11-02)
**DEFECT FOUND AND FIXED:** the relative Calmar gain (c_cell / c_ship - 1) was inverted when the shipped Calmar was negative and exploded when it was near zero. This hit the X' component of the HONEST score S_hon (and the displayed X' Calmar-gain column) in every frame where the X' shipped mean is <= 0: D7 v1.1 / v1.2 / v1.3-assumed / V13X (X' mean about -4k/wk); the one-convention frames (X' mean +8k) and the L6M, HOLD, MID, PRE columns were not affected, nor were maxDD cuts, tiers, RISK-KEEP, placebo ranks, S_post. Fixed definition: dcal = (c_cell - c_ship) / max(|c_ship|, 0.05). All honest picks and 'X'' Calmar gain' entries printed above for those frames are superseded by the tables in this section; the honest ranking in the earlier sections should be disregarded.
**Corrected lock=None (headline) picks:** the honest and post-hoc rankings now agree on CRT4h 30pts fw2 solo (fresh within 2 h, no other set line within 5 pts): STRICT, L6M maxDD 132.6 -> 124.3k (-6%), Calmar gain L6M +8%, HOLD +9%, MID +6%, PRE +4%, X' +5%, mean +0.3k/wk (MDE 1.0), 4/4 neighbours, LOEO worst +0.04; second agreement camH3 40pts fw8 any (post-hoc STRICT: L6M +9%, HOLD +11%, MID +39%, PRE +2%, X' +5%; the honest pick is the 75%tgt neighbour). kijun1h 60pts a1-4 (honest, S/T/N) and PDmid 75%tgt age>4h solo (honest, S/T/N: PRE +9%) are small. Share of cells with positive honest score falls from 47% to 20% (the inverted X' term inflated it), positive post-hoc 35%. Placebos for these cells are queued (lock-off frame).
V13X lock=None full screen: 1933 changed distinct-key cells; S_hon>0 0.20, S_post>0 0.35; STRICT 46, TOL 110, NOW 663, TOL-B 492, TOL-nc 143, RISK-KEEP(L6M rule) 0

| line | pick | cell | maxDD $k L6M / HOLD / MID / PRE / X' | Calmar gain L6M / HOLD / MID / PRE / X' | mean d L6M (MDE) | S/T/N | RK | neighbours n, mean S, same sign | LOEO worst S (episode) |
|---|---|---|---|---|---|---|---|---|---|
| CRT4h | HONEST | CRT4h|30pts|fw2|solo | 124.3 / 124.3 / 66.7 / 178.0 / 134.3 | +8% / +9% / +6% / +4% / +5% | +0.3 (1.0) | S/T/N | no | 4, +0.03, 4/4 | +0.04 (202506-202516) |
| CRT4h | POST-HOC | CRT4h|30pts|fw2|solo | 124.3 / 124.3 / 66.7 / 178.0 / 134.3 | +8% / +9% / +6% / +4% / +5% | +0.3 (1.0) | S/T/N | no | 4, +0.06, 4/4 | +0.02 (202628-202634) |
| KCup4h | HONEST | KCup4h|15pts|fresh|solo | 132.6 / 132.6 / 62.6 / 176.9 / 128.2 | -0% / -0% / -3% / +2% / +1% | -0.0 (0.3) | -/-/- | no | 4, +0.01, 3/4 | -0.01 (202314-202337) |
| KCup4h | POST-HOC (ungated) | KCup4h|60pts|fresh|stk | 131.9 / 131.9 / 62.6 / 179.4 / 132.4 | -0% / +1% / -2% / -1% / -1% | -0.2 (0.5) | -/-/- | no | 3, +0.00, 2/3 | -0.03 (202628-202634) |
| OTE705 | HONEST | OTE705|60pts|a1-4|any | 125.5 / 125.5 / 67.6 / 139.4 / 134.2 | +7% / +5% / -3% / +34% / +1% | +0.3 (1.9) | -/-/- | no | 3, -0.01, 1/3 | +0.07 (202506-202516) |
| OTE705 | POST-HOC (ungated) | OTE705|30pts|a1-4|solo | 126.7 / 126.7 / 66.0 / 182.0 / 133.6 | +7% / +7% / -3% / -5% / +2% | +0.5 (1.6) | -/-/N | no | 4, -0.02, 2/4 | +0.03 (202628-202634) |
| OTE79 | HONEST | OTE79|75%tgt|a1-4|solo | 138.3 / 138.3 / 63.6 / 182.0 / 132.5 | -5% / -4% / -3% / -1% / +2% | -0.4 (1.1) | -/-/- | no | 3, -0.06, 0/3 | -0.02 (202314-202337) |
| OTE79 | POST-HOC | OTE79|20pts|fw2|any | 132.6 / 132.6 / 62.6 / 178.4 / 136.0 | +1% / +0% / +0% / +0% / -0% | +0.2 (0.5) | -/T/N | no | 4, -0.03, 1/4 | +0.00 (202606-202607) |
| PDmid | HONEST | PDmid|75%tgt|a>4|solo | 133.9 / 133.9 / 62.4 / 170.8 / 130.3 | +2% / +0% / +1% / +9% / +5% | +0.7 (2.4) | S/T/N | no | 2, +0.01, 1/2 | +0.04 (202506-202516) |
| PDmid | POST-HOC | PDmid|20pts|touched|solo | 123.3 / 123.3 / 65.5 / 173.1 / 140.5 | +14% / +14% / +3% / +5% / -8% | +1.5 (2.6) | -/T/N | no | 3, +0.04, 2/3 | +0.07 (202628-202634) |
| STK | HONEST | STK|C8|clu3|fresh|75%tgt|add | 132.6 / 132.6 / 62.6 / 178.4 / 130.1 | +0% / +0% / -1% / +2% / +1% | +0.0 (0.0) | -/-/- | no | 3, -0.02, 2/3 | +0.01 (202435-202445) |
| STK | POST-HOC (ungated) | STK|C8|clu3|fresh|30pts|only | 136.8 / 136.8 / 84.3 / 211.8 / 144.3 | +4% / +4% / -16% / -28% / +16% | +1.8 (3.9) | -/-/- | no | 4, -0.01, 3/4 | +0.02 (202606-202607) |
| camH3 | HONEST | camH3|75%tgt|fw8|solo | 123.4 / 123.4 / 46.4 / 181.1 / 116.9 | +8% / +9% / +42% / +3% / +5% | +0.0 (2.7) | -/-/- | no | 3, +0.00, 2/3 | -0.12 (202314-202337) |
| camH3 | POST-HOC | camH3|40pts|fw8|any | 123.1 / 123.1 / 46.4 / 181.2 / 123.6 | +9% / +11% / +39% / +2% / +5% | +0.3 (1.5) | S/T/N | no | 4, +0.06, 4/4 | +0.04 (202628-202634) |
| kijun1h | HONEST | kijun1h|60pts|a1-4|any | 135.3 / 135.3 / 68.5 / 165.7 / 136.5 | -1% / +3% / -1% / +10% / +11% | +0.2 (1.1) | S/T/N | no | 3, +0.00, 2/3 | +0.07 (202506-202516) |
| kijun1h | POST-HOC | kijun1h|60pts|a1-4|stk | 135.3 / 135.3 / 68.5 / 170.0 / 138.3 | -1% / +2% / -1% / +7% / +7% | +0.3 (1.1) | S/T/N | no | 3, -0.02, 1/3 | -0.01 (202606-202607) |

## s2 B2 round numbers, profile lines and B3 unfilled levels as ADDED lines (lock=None, corrected score)
B2 (00/50/25 handles, 100s separate, price-scaled, fresh = untouched since the day start): no honest lead (best honest scores <= +0.14; most 0 or negative). The recent-window scores are large (post-hoc up to L6M +91%, maxDD cut up to 48%) but they come with PRE Calmar -27 to -62% and a much larger halved volume: each added handle line half-sizes 10-25% of the signals, so these are VOLUME effects until a same-volume placebo says otherwise (queued). Profile lines vah/lvn1/hvn0: honest scores positive for VAH15 and LVN1 on the old inverted X' term only; after the fix no STRICT/TOLERANT cell (0/0/0 and 0/0/9). B3 (unfilled FVG 5m/15m/1h, Globex-open gap, RTH gap; 180 cells) pending. NOTE: naked prior-day POC/VAH/VAL, NY lunch, Globex open print, session VWAP bands, weekly/monthly open and prior week/month H/L are ZL-1's streams (NPD, LNC, OPN2, VWB, PWM) per its message; not built here.

### B2 round numbers (R100 = x100 levels, R50 = 50 mod 100, R25 = 25/75, A50/A25 = all multiples, SC* = price-scaled spacing); fresh = untouched since the day start (V13X lock=None, ADDED to the half mask; 216 cells)

| stream | cells | S_hon>0 | S_post>0 | best honest (cell: S, L6M/HOLD/MID/PRE/X' Calmar gain) | best post-hoc, TOL-gated if any | STRICT/TOL/NOW | max L6M maxDD cut | volume (kept trades) of best honest |
|---|---|---|---|---|---|---|---|---|
| A25 | 27 | 0.04 | 0.78 | 10pts|touched: +0.071, +26% / -7% / -25% / -23% / +37% | 20pts|fresh (ungated): +0.268, +39% / +14% / +31% / -27% / -10% | 0/0/6 | +36% | n/a |
| A50 | 27 | 0.00 | 0.70 | 40pts|fresh: -0.037, +24% / +2% / -10% / -36% / +28% | 75%tgt|fresh (ungated): +0.266, +32% / +21% / +22% / -56% / +20% | 0/0/6 | +42% | n/a |
| R100 | 27 | 0.00 | 0.63 | 10pts|touched: -0.057, +3% / +4% / +47% / -32% / +21% | 60pts|fresh (ungated): +0.308, +68% / -7% / +8% / -57% / -24% | 0/0/5 | +47% | n/a |
| R25 | 27 | 0.22 | 0.78 | 10pts|touched: +0.075, -25% / -19% / -17% / +1% / +14% | 75%tgt|fresh (ungated): +0.767, +91% / +62% / -28% / -62% / -12% | 0/0/2 | +48% | n/a |
| R50 | 27 | 0.48 | 0.48 | 75%tgt|touched: +0.142, -15% / -18% / -32% / +30% / -2% | 75%tgt|fresh (ungated): +0.471, +57% / +37% / +2% / -18% / +27% | 0/0/4 | +41% | n/a |
| SC100 | 27 | 0.00 | 0.52 | 10pts|touched: -0.030, -16% / -13% / +28% / -33% / +27% | 20pts|fresh (ungated): +0.128, +8% / +18% / +45% / +1% / -17% | 0/0/4 | +10% | n/a |
| SC25 | 27 | 0.04 | 0.78 | 10pts|touched: +0.071, +40% / -3% / -25% / -23% / +37% | 40pts|fresh (ungated): +0.306, +31% / +30% / -55% / -31% / -18% | 0/0/0 | +37% | n/a |
| SC50 | 27 | 0.00 | 0.52 | 10pts|touched: -0.009, -17% / -12% / +25% / -28% / +26% | 75%tgt|fresh (ungated): +0.240, +34% / +14% / +52% / -56% / -11% | 0/0/6 | +39% | n/a |

### profile lines vah sw15 / lvn1 sw1h / hvn0 sw1h (V13X lock=None, ADDED to the half mask; 108 cells)

| stream | cells | S_hon>0 | S_post>0 | best honest (cell: S, L6M/HOLD/MID/PRE/X' Calmar gain) | best post-hoc, TOL-gated if any | STRICT/TOL/NOW | max L6M maxDD cut | volume (kept trades) of best honest |
|---|---|---|---|---|---|---|---|---|
| HVN0_1hs | 36 | 0.42 | 0.25 | 30pts|fw2: +0.040, -2% / -2% / -11% / +8% / -1% | 40pts|touched (ungated): +0.062, +7% / +5% / -7% / -7% / +2% | 0/0/9 | +4% | n/a |
| LVN1_1hs | 36 | 0.44 | 0.08 | 60pts|fresh: +0.064, -25% / -21% / +8% / +20% / -7% | 10pts|fw2 (ungated): +0.009, +1% / +1% / -0% / -1% / -2% | 0/0/0 | +0% | n/a |
| VAH15s | 36 | 0.33 | 0.50 | 10pts|fresh: +0.035, -1% / +0% / +8% / +10% / -3% | 30pts|fresh (ungated): +0.064, +10% / +2% / +2% / +11% / -13% | 0/0/0 | +10% | n/a |

(b3xl0: not complete: need at least one array to stack)


## s2 PLACEBOS in the headline frame (V13X lock=None), interim n=36 draws per kind (Z2, ~06:00Z 2026-11-02; target 150, queue running)
Share of placebo draws with an L6M/HOLD/MID/PRE/X' maxDD cut at least as large as the cell's (5% would be a beat; the resolution at n=36 is 0.03). No finalist beats any of its three placebos (random-level same-count, same-volume random half, shuffled-day line sets) on the L6M cut: CRT4h 60pts fresh solo 0.24-0.42, CRT4h-Asia-only 0.30-0.46, CRT4h 30pts fw2 solo (the corrected honest+post-hoc agreement) 0.16-0.24, camH3 40pts fw8 any 0.19-0.22 (MID rank 0.03-0.05 and X' 0.03: its MID/X' cuts are the placebo-beating part), PDmid 20pts touched solo 0.16-0.24, PDmid 30pts touched stacked 0.11-0.14. Labels: CRT4h 30pts fw2 solo = LEAD (STRICT, 4/4 neighbours, inside MDE, no placebo beat yet); camH3 40pts fw8 any = LEAD with MID/X' placebo ranks <= 0.05 (watch); the rest LEAD-weak / VOLUME-like.
| finalist (lock=None) | kind | n | L6M cut (cell) | rank L6M | rank HOLD | rank MID | rank PRE | rank X' | rank Calmar L6M | rank S_post | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| CRT4h60 | cnt | 37 | +4% | 0.42 | 0.50 | 0.24 | 0.84 | 0.50 | 0.34 | 0.37 | no placebo beat |
| CRT4h60 | vol | 37 | +4% | 0.24 | 0.26 | 0.13 | 0.92 | 0.74 | 0.24 | 0.21 | no placebo beat |
| CRT4h60 | sday | 36 | +4% | 0.24 | 0.27 | 0.14 | 0.57 | 0.22 | 0.16 | 0.22 | no placebo beat |
| CRT4h60asia | cnt | 36 | +4% | 0.46 | 0.57 | 0.14 | 0.84 | 0.41 | 0.35 | 0.43 | no placebo beat |
| CRT4h60asia | vol | 36 | +4% | 0.38 | 0.46 | 0.19 | 0.97 | 0.41 | 0.27 | 0.22 | no placebo beat |
| CRT4h60asia | sday | 36 | +4% | 0.30 | 0.30 | 0.16 | 0.49 | 0.08 | 0.24 | 0.22 | no placebo beat |
| CRT4h30fw2solo | cnt | 36 | +6% | 0.19 | 0.16 | 0.78 | 0.43 | 0.30 | 0.22 | 0.14 | no placebo beat |
| CRT4h30fw2solo | vol | 36 | +6% | 0.16 | 0.16 | 0.84 | 0.35 | 0.41 | 0.19 | 0.16 | no placebo beat |
| CRT4h30fw2solo | sday | 36 | +6% | 0.24 | 0.14 | 0.41 | 0.11 | 0.08 | 0.22 | 0.19 | no placebo beat |
| camH3_40fw8any | cnt | 36 | +7% | 0.22 | 0.14 | 0.05 | 0.35 | 0.14 | 0.22 | 0.22 | no placebo beat |
| camH3_40fw8any | vol | 36 | +7% | 0.19 | 0.11 | 0.03 | 0.49 | 0.11 | 0.19 | 0.16 | no placebo beat |
| camH3_40fw8any | sday | 36 | +7% | 0.22 | 0.14 | 0.05 | 0.59 | 0.03 | 0.19 | 0.14 | no placebo beat |
| PDmid_20touchedsolo | cnt | 36 | +7% | 0.24 | 0.22 | 0.81 | 0.30 | 0.68 | 0.11 | 0.05 | no placebo beat |
| PDmid_20touchedsolo | vol | 36 | +7% | 0.22 | 0.11 | 0.78 | 0.27 | 0.73 | 0.11 | 0.11 | no placebo beat |
| PDmid_20touchedsolo | sday | 36 | +7% | 0.16 | 0.11 | 0.84 | 0.32 | 0.19 | 0.16 | 0.16 | no placebo beat |
| PDmid_30touchedstk | cnt | 36 | +11% | 0.14 | 0.11 | 0.62 | 0.43 | 1.00 | 0.16 | 0.16 | no placebo beat |
| PDmid_30touchedstk | vol | 36 | +11% | 0.11 | 0.11 | 0.62 | 0.35 | 0.95 | 0.14 | 0.14 | no placebo beat |
| PDmid_30touchedstk | sday | 36 | +11% | 0.14 | 0.16 | 0.59 | 0.57 | 0.76 | 0.27 | 0.27 | no placebo beat |


## s2 per-session stage and B3 cells in the headline frame (V13X lock=None, corrected score), ~06:25Z 2026-11-02
Per-session (4 lines x 4 sessions, line setting changed in that session only, 36 settings each): **CRT4h acts in Asia** (11 STRICT / 7 TOLERANT / 22 NOW-ONLY of 36 settings; best 40pts fw2 L6M +9% HOLD +10% PRE +5%) and nowhere else; camH3 acts in London (5/5/18; 60pts touched L6M +16%, HOLD +14%, MID +25%); kijun1h in London (0 STRICT, 12 TOL, 29 NOW; tiny gains); PDmid nothing. Asia carries the stack in 2026, so a CRT4h-Asia-only line is the natural small product; its placebo is the CRT4h60asia row above (no beat at n=36). Per-session cells have NOT been put through a session-level best-of-N null.
| line | session | cells | S_hon>0 | S_post>0 | best honest (S; L6M/HOLD/MID/PRE/X' Calmar gain) | best post-hoc (TOL gate if any) | STRICT/TOL/NOW |
|---|---|---|---|---|---|---|---|
| CRT4h | asia | 36 | 0.28 | 0.75 | 40pts|fw2: +0.040; +9% / +10% / +0% / +5% / +3% | 75%tgt|fw2: +0.097; +9% / +10% / +1% / -8% / +3% | 11/7/22 |
| CRT4h | london | 36 | 0.81 | 0.50 | 75%tgt|touched: +0.042; -2% / -0% / +14% / +3% / +5% | 60pts|fresh: +0.018; +2% / +2% / +6% / +1% / -0% | 0/2/8 |
| CRT4h | nyam | 36 | 0.17 | 0.61 | 30pts|fresh: +0.003; +0% / +0% / +0% / +1% / -0% | 20pts|touched (ungated): +0.003; +0% / +0% / +2% / -3% / -3% | 0/0/9 |
| CRT4h | nypm | 36 | 0.19 | 0.53 | 60pts|fw2: +0.001; +0% / +0% / +0% / +0% / +0% | 60pts|touched (ungated): +0.002; +0% / +0% / +0% / -0% / -0% | 0/0/3 |
| PDmid | asia | 36 | 0.67 | 0.28 | 10pts|fresh: +0.021; +2% / +1% / -2% / +4% / +0% | 15pts|touched (ungated): +0.116; +14% / +10% / -3% / +6% / -2% | 0/0/3 |
| PDmid | london | 36 | 0.11 | 0.22 | 40pts|fresh: +0.003; -1% / -0% / -2% / -2% / +2% | 20pts|touched (ungated): +0.066; +6% / +7% / +1% / -4% / -9% | 0/0/1 |
| PDmid | nyam | 36 | 0.58 | 0.39 | 30pts|touched: +0.022; -0% / +0% / -4% / +2% / +3% | 40pts|fresh (ungated): +0.018; +2% / +2% / +0% / -1% / +1% | 0/0/10 |
| PDmid | nypm | 36 | 0.36 | 0.25 | 60pts|touched: +0.010; +0% / +0% / +0% / +2% / -0% | 60pts|touched: +0.002; +0% / +0% / +0% / +2% / -0% | 0/1/1 |
| camH3 | asia | 36 | 0.56 | 0.42 | 15pts|touched: +0.019; -10% / -8% / +2% / +8% / -4% | 60pts|fw2 (ungated): +0.061; +6% / +6% / +6% / +3% / -4% | 0/0/15 |
| camH3 | london | 36 | 0.28 | 0.72 | 60pts|touched: +0.032; +16% / +14% / +25% / +2% / +4% | 60pts|touched: +0.153; +16% / +14% / +25% / +2% / +4% | 5/5/18 |
| camH3 | nyam | 36 | 0.44 | 0.19 | 10pts|fw2: +0.017; -0% / -0% / +0% / -1% / +4% | 60pts|fresh (ungated): +0.031; +3% / +3% / +0% / +0% / -0% | 0/0/0 |
| camH3 | nypm | 36 | 0.31 | 0.28 | 30pts|touched: +0.008; -1% / -1% / -0% / +1% / +0% | 30pts|fresh (ungated): +0.000; +0% / +0% / +0% / +0% / +0% | 0/0/0 |
| kijun1h | asia | 36 | 0.61 | 0.33 | 40pts|touched: +0.041; +1% / +3% / -26% / +7% / +1% | 15pts|touched (ungated): +0.047; +5% / +4% / -9% / +5% / +1% | 0/0/6 |
| kijun1h | london | 36 | 0.25 | 0.81 | 10pts|fresh: +0.025; +1% / +0% / -12% / +5% / +0% | 75%tgt|fresh: +0.016; +1% / +2% / +7% / -1% / -4% | 0/12/29 |
| kijun1h | nyam | 36 | 0.25 | 0.25 | 10pts|fresh: +0.007; -2% / -2% / +0% / -2% / +3% | 75%tgt|fresh (ungated): +0.005; +1% / +0% / +1% / -3% / +1% | 0/0/5 |
| kijun1h | nypm | 36 | 0.42 | 0.58 | 60pts|fresh: +0.009; +0% / +0% / +2% / +1% / +1% | 60pts|fresh: +0.001; +0% / +0% / +2% / +1% / +1% | 3/3/21 |

B3 (my cut; ZL-3 also owns B3 scoring): unfilled FVG 5m/15m/1h, Globex-open gap, RTH gap as ADDED lines: no STRICT cell; FVG15 and FVG1H have recent-only gains (L6M +15..+17%, MID -18% / +163% unstable), FVG5 honest score positive with MID -40%; NDOG/RTHG are sparse (95 / 9 trades within 20 pts). No lead.
### B3 unfilled FVG 5m/15m/1h and Globex-open / RTH gap edges (V13X lock=None, ADDED to the half mask; 180 cells)

| stream | cells | S_hon>0 | S_post>0 | best honest (cell: S, L6M/HOLD/MID/PRE/X' Calmar gain) | best post-hoc, TOL-gated if any | STRICT/TOL/NOW | max L6M maxDD cut | volume (kept trades) of best honest |
|---|---|---|---|---|---|---|---|---|
| FVG15 | 36 | 0.00 | 0.53 | 60pts|fw2: -0.028, +17% / +19% / -18% / +2% / -7% | 75%tgt|fw2: +0.167, +15% / +18% / -18% / +0% / -7% | 0/3/6 | +17% | n/a |
| FVG1H | 36 | 0.06 | 0.33 | 60pts|fresh: +0.016, -4% / -5% / -7% / +0% / +3% | 40pts|touched (ungated): +0.180, +10% / +26% / +163% / -21% / +3% | 0/0/0 | +18% | n/a |
| FVG5 | 36 | 0.94 | 0.14 | 30pts|fw2: +0.138, +4% / -3% / -40% / +20% / +8% | 40pts|fw2: +0.007, +7% / -5% / -44% / +10% / +8% | 0/7/8 | +11% | n/a |
| NDOG | 36 | 0.03 | 0.69 | 60pts|fw2: +0.000, +0% / +0% / +0% / +1% / -1% | 30pts|fresh: +0.004, +0% / +0% / +0% / +2% / -2% | 0/18/24 | +0% | n/a |
| RTHG | 36 | 0.25 | 0.14 | 20pts|touched: +0.180, -5% / +3% / +16% / +48% / -12% | 40pts|touched (ungated): +0.022, -2% / +7% / +39% / +33% / -10% | 0/0/2 | +14% | n/a |


## s2 FINAL (Z2, ~07:15Z 2026-11-02): V13X lock=None placebos at n=133-139 draws per kind (first 6 cells), n=60 for the 4 extra honest cells (queue still filling to 100)
**Verdict, headline frame (lock=None, corrected score):** no finalist beats its three placebos (random-level same-count, same-volume random half, shuffled-day line sets) on the L6M maxDD cut. Closest: CRT4h 30pts fw2 solo (the corrected honest+post-hoc agreement, STRICT, 4/4 neighbours, 43-month chain delta +75.5k lock-none / +101.9k lock-12, leave-one-month-out min +60.6k / +62.3k, P(delta>0) 1.00 / 0.99, best month 20% / 39%: NOT one-month) has L6M-cut ranks 0.09-0.14, HOLD 0.07-0.11, S_post 0.08-0.10, X' 0.04 (sday): the strongest LEAD but not a placebo beat. camH3 40pts fw8 any: L6M ranks 0.19-0.25 but MID cut ranks 0.01 / 0.01 / 0.05 and X' 0.01-0.20 (placebo-beating on MID and X' only); its lock-12 monthly chain is ONE-MONTH (best month 137%, LOMO min -32.7k) so it is a lock-none-only lead. PDmid 20pts touched solo beats the cnt and vol placebos on S_post (0.04) but not on the L6M cut (0.16-0.17) nor shuffled-day (0.11). OTE705 60pts a1-4 any: PRE rank 0.02 only. Others no. **Labels: CRT4h 30pts fw2 solo = LEAD (strongest; carried by Asia in the per-session stage; keep forward-shadow only); camH3 40pts fw8 any = LEAD in lock-none only (MID/X' placebo beat; ONE-MONTH in lock-12); PDmid 20pts touched solo = LEAD-weak; CRT4h 60pts fresh solo = LOCK-ONLY in part, no placebo beat; B2 round numbers = VOLUME (recent-only gains, PRE -27..-62%); profile lines and B3 FVG/gap lines = no lead; stacked rule = no lead.** Nothing is RISK-KEEP in the headline frame (L6M maxDD cuts at most 6-11%, inside MDE on the mean). Proposed policy-file row (shadow only, for Z3): CRT4h | 30pts | fresh within 2 h, no other set line within 5 pts | half | all books | Asia; every other line keeps D20 fresh half. Not done: the V13X best-of-N null for the full grid (the earlier 6-replicate null was on the v1.1 assumed base: real best scores fell inside the shuffled range), a same-volume placebo for the B2 cells, line-parameter variants.
| finalist (lock=None) | kind | n | L6M cut (cell) | rank L6M | rank HOLD | rank MID | rank PRE | rank X' | rank Calmar L6M | rank S_post | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| CRT4h60 | cnt | 139 | +4% | 0.34 | 0.36 | 0.17 | 0.84 | 0.64 | 0.26 | 0.23 | no placebo beat |
| CRT4h60 | vol | 134 | +4% | 0.31 | 0.37 | 0.16 | 0.91 | 0.57 | 0.27 | 0.25 | no placebo beat |
| CRT4h60 | sday | 139 | +4% | 0.21 | 0.26 | 0.12 | 0.59 | 0.19 | 0.17 | 0.18 | no placebo beat |
| CRT4h60asia | cnt | 134 | +4% | 0.41 | 0.50 | 0.12 | 0.81 | 0.44 | 0.33 | 0.36 | no placebo beat |
| CRT4h60asia | vol | 139 | +4% | 0.29 | 0.44 | 0.16 | 0.94 | 0.41 | 0.19 | 0.21 | no placebo beat |
| CRT4h60asia | sday | 134 | +4% | 0.28 | 0.31 | 0.14 | 0.56 | 0.07 | 0.19 | 0.21 | no placebo beat |
| CRT4h30fw2solo | cnt | 139 | +6% | 0.12 | 0.11 | 0.86 | 0.39 | 0.35 | 0.13 | 0.08 | no placebo beat |
| CRT4h30fw2solo | vol | 133 | +6% | 0.09 | 0.07 | 0.83 | 0.39 | 0.43 | 0.12 | 0.08 | no placebo beat |
| CRT4h30fw2solo | sday | 139 | +6% | 0.14 | 0.11 | 0.41 | 0.15 | 0.04 | 0.11 | 0.10 | no placebo beat |
| camH3_40fw8any | cnt | 133 | +7% | 0.23 | 0.14 | 0.01 | 0.43 | 0.20 | 0.25 | 0.21 | no placebo beat |
| camH3_40fw8any | vol | 139 | +7% | 0.19 | 0.11 | 0.01 | 0.50 | 0.14 | 0.19 | 0.15 | no placebo beat |
| camH3_40fw8any | sday | 133 | +7% | 0.25 | 0.07 | 0.05 | 0.63 | 0.01 | 0.19 | 0.12 | no placebo beat |
| PDmid_20touchedsolo | cnt | 139 | +7% | 0.16 | 0.11 | 0.81 | 0.21 | 0.66 | 0.06 | 0.04 | beats on S_post |
| PDmid_20touchedsolo | vol | 133 | +7% | 0.17 | 0.09 | 0.72 | 0.25 | 0.67 | 0.10 | 0.04 | beats on S_post |
| PDmid_20touchedsolo | sday | 139 | +7% | 0.17 | 0.09 | 0.82 | 0.36 | 0.24 | 0.16 | 0.11 | no placebo beat |
| PDmid_30touchedstk | cnt | 133 | +11% | 0.06 | 0.07 | 0.57 | 0.43 | 0.99 | 0.09 | 0.10 | no placebo beat |
| PDmid_30touchedstk | vol | 138 | +11% | 0.06 | 0.06 | 0.58 | 0.37 | 0.96 | 0.09 | 0.11 | no placebo beat |
| PDmid_30touchedstk | sday | 133 | +11% | 0.10 | 0.11 | 0.56 | 0.60 | 0.72 | 0.21 | 0.28 | no placebo beat |
| camH3_75fw8solo | cnt | 61 | +7% | 0.26 | 0.18 | 0.02 | 0.40 | 0.13 | 0.24 | 0.21 | no placebo beat |
| camH3_75fw8solo | vol | 61 | +7% | 0.23 | 0.16 | 0.03 | 0.42 | 0.06 | 0.26 | 0.21 | no placebo beat |
| camH3_75fw8solo | sday | 61 | +7% | 0.32 | 0.08 | 0.05 | 0.56 | 0.02 | 0.23 | 0.13 | no placebo beat |
| OTE705_60a14any | cnt | 61 | +5% | 0.24 | 0.21 | 0.71 | 0.02 | 0.40 | 0.19 | 0.24 | no placebo beat |
| OTE705_60a14any | vol | 61 | +5% | 0.26 | 0.16 | 0.66 | 0.02 | 0.34 | 0.24 | 0.21 | no placebo beat |
| OTE705_60a14any | sday | 60 | +5% | 0.15 | 0.11 | 0.69 | 0.02 | 0.51 | 0.13 | 0.15 | no placebo beat |
| kijun1h_60a14any | cnt | 60 | -2% | 0.64 | 0.64 | 0.80 | 0.05 | 0.49 | 0.64 | 0.56 | no placebo beat |
| kijun1h_60a14any | vol | 60 | -2% | 0.57 | 0.56 | 0.85 | 0.07 | 0.30 | 0.57 | 0.41 | no placebo beat |
| kijun1h_60a14any | sday | 60 | -2% | 0.61 | 0.56 | 0.56 | 0.26 | 0.49 | 0.54 | 0.48 | no placebo beat |
| PDmid_75a4solo | cnt | 60 | -1% | 0.64 | 0.64 | 0.33 | 0.08 | 0.28 | 0.38 | 0.44 | no placebo beat |
| PDmid_75a4solo | vol | 60 | -1% | 0.66 | 0.66 | 0.38 | 0.16 | 0.25 | 0.39 | 0.41 | no placebo beat |
| PDmid_75a4solo | sday | 60 | -1% | 0.67 | 0.62 | 0.39 | 0.38 | 0.03 | 0.69 | 0.70 | no placebo beat |

## LIVE definition (Shadow only) of the CRT4h 30pts fw2 solo zone cell, for D7 v1.3 EXACT (Z2, 2026-11-02 ~08:00Z)
Status: strongest LEAD of section 2 (STRICT in V13X lock=None, 4/4 neighbours, 43-month chain +75.5k, not one-month, placebo ranks 0.09-0.14: not at the 5% bar). Shadow log only; nothing is traded or acted on; no PASS.
**Line (CRT 4h midpoint):** at each close of a 4-hour bar (bars anchored at 18:00 ET: 18:00, 22:00, 02:00, 06:00, 10:00, 14:00 ET), line L = (high + low) / 2 of that just-closed bar, built from the 1-s path price frame (back-adjusted at rolls; D7 uses its own chart price frame, same quantity). It exists from the first second after the bar closes (ek) until the next 4h bar closes (a new L replaces it; cap = next close).
**Fresh:** L is fresh while no 1-s bar since ek has traded through it (second range [low, high] containing L; first touch ends freshness); evaluated on state strictly before the signal second.
**Age rule ("fresh within 2 h"):** signal_second - ek <= 7,200 s (the line formed within the last 2 hours; the first half of its 4-hour life).
**Ahead:** L is between the planned entry price E and the target: distance a = (L - E) x side >= 0 and a <= D = 30 pts (and, as for every zone line, a <= target distance). CRT midpoints are neutral lines (count for longs and shorts).
**Solo (confluence):** no other line of the set - MAS ich_kijun 1h, PDX day midpoint, MAS kc_up 4h, PIV cam_H3 RTH, FIB ote62/705/79 up 15m - is fresh, ahead and within D = 30 pts AND within 5 pts of a (|a_other - a| <= 5 pts) at the signal second. (The 3-profile lines are not in the set.)
**Action HALF:** if all of the above hold, the signal's planned lots are multiplied by 0.5 through the ER row multiplier exactly as the shipped zone HALF does (integer half-up, minimum 1 lot, the running-max SizeMult governor keeps the 0.5). This REPLACES the shipped CRT term (shipped: CRT midpoint fresh, any age, any confluence, D = 20): in the cell the CRT line half-sizes only when the three conditions above hold. The other six half-lines keep D20 fresh unchanged; OTE-62 B73 D30 unchanged.
**Scope in the cell tested:** all books and sessions (lock=None headline). The per-session stage found the effect only in Asia (11 STRICT / 7 TOLERANT of 36 settings; London / NY flat), so an Asia-only version is the cleaner product; its placebos (Asia-restricted) are being run.
**Forward shadow log (pointer in FORWARD_SHADOW_ZONES_SPEC.md; fields to add to shadow_zone_flags.csv for rule_id Z2_CRT4h30fw2solo):** signal_id, rule_id, variant=half, D_pts=30, frame=AHEAD, fresh_only=1, crt_line_px, crt_formed_ts_utc (ek), crt_age_s, crt_fresh (0/1), crt_dist_pts, crt_touched_ts_utc, for each of the 7 other set lines: px, fresh, dist_pts (NaN if none ahead within D), n_others_within_5pts, solo (0/1), shipped_crt_flag (D20, fresh, any age), cell_flag, would_action (half lots, min 1), lots_final_if_applied, and at trade close base_pnl_usd and pnl_with_action_usd. Controls: every signal row (flagged or not) so the same-count / same-volume / shuffled-day placebos can be built from the log; per day count of flagged signals; hourly heartbeat (4h bars seen, 1-s rows seen).


## s2 NEXT-STEP RESULTS (Z2, ~08:00Z 2026-11-02): Asia-only cell with Asia-restricted placebos; phase-averaged check
**(2) CRT4h 30pts fw2 solo as an ASIA-ONLY cell (V13X lock=None; the CRT line changed in Asia rows only):** STRICT in all five windows (L6M maxDD 132.6 -> 125.6k, -5%; Calmar gain L6M +7%, HOLD +8%, MID +1%, PRE +3%, X' +5%; mean +0.4k/wk, MDE 0.9k). Lock-12: L6M maxDD -10% (73.9 -> 66.3k), HOLD +2%, MID +48%, PRE +8%, TOL fails HOLD. **ONE-WEEK in the total series:** with the week carrying the shipped L6M maxDD (W34) dropped the cut is -0.4% (the Asia-session series itself: cut +0.0%, W33). Per book in Asia (lock none, change in maxDD $k, L6M / PRE / X'): K6 -0.7 / -0.7 / -1.3; P6 0 / -7.4 / 0 (mean +0.2k PRE, +0.6k X'); U6 -2.8 / 0 / +0.7; H6 -2.8 / +2.3 / -0.4; A6 +2.8 / 0 / 0; M6 none (no Asia lots). Asia-restricted placebos (120 draws per kind; cnt = same count of Asia rows at random levels by book; volA = same planned-lot volume of random Asia rows; sdayA = the CRT line fires taken from other Asia trades of the same stratum):
| kind | n | L6M cut total (cell) | rank L6M | rank HOLD | rank MID | rank PRE | rank X' | rank S_post | Asia-session series: L6M cut (cell) | rank L6M | rank PRE | rank X' | rank HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| cnt | 120 | +5% | 0.15 | 0.14 | 0.89 | 0.40 | 0.32 | 0.14 | +0% | 0.42 | 0.64 | 0.20 | 0.04 |
| volA | 120 | +5% | 0.04 | 0.03 | 0.89 | 0.45 | 0.36 | 0.04 | +0% | 0.51 | 0.72 | 0.20 | 0.01 |
| sdayA | 120 | +5% | 0.35 | 0.29 | 0.38 | 0.10 | 0.05 | 0.22 | +0% | 0.43 | 0.44 | 0.01 | 0.06 |

Carrying week of the shipped L6M maxDD: total series wk 202634, cut with that week dropped -0% (ONE-WEEK); Asia-session series wk 202633, cut +0%, dropped +0% (not one-week).
Flag test (rank <= 0.05 in L6M AND PRE or X' with the carrying week dropped): NOT met. volA gives L6M 0.04, HOLD 0.03, S_post 0.04, but PRE 0.45 / X' 0.36 and the total-series L6M cut is ONE-WEEK; sdayA gives X' 0.05 but L6M 0.35 and PRE 0.10; cnt gives nothing (0.15 / 0.40). The honest reading: the Asia-only version is a volume-sensitive L6M/HOLD effect (random Asia half-sizing of the same volume does almost as well), not a PRE/X' effect.
**(3) Phase-averaged check (Z3 method: 5 lock-reset phases = week key shifted -2..+2 label days; V13X; ship and cell both re-run each phase):**
| lock | cell | phase-avg L6M maxDD cut (range over 5 phases) | phase-avg Calmar gain L6M / HOLD / MID / PRE / X' | phases with L6M cut > 0 | phase-avg ship L6M maxDD (range) | phase-avg cell L6M maxDD |
|---|---|---|---|---|---|---|
| none | CRT4h30fw2solo | +10.5% (+6.3%..+12.4%) | +14% / +16% / +7% / +5% / +3% | 5/5 | 150.0k (132.6..164.0) | 134.0k |
| none | CRT4h30asia | +4.3% (+3.1%..+5.3%) | +6% / +7% / +2% / +4% / +4% | 5/5 | 150.0k (132.6..164.0) | 143.6k |
| none | camH3_40fw8any | +5.2% (+0.6%..+7.2%) | +6% / +8% / +37% / -0% / +5% | 5/5 | 150.0k (132.6..164.0) | 142.2k |
| none | CRT4h60 | +7.3% (+4.1%..+9.6%) | +10% / +10% / +27% / -12% / +0% | 5/5 | 150.0k (132.6..164.0) | 138.9k |
| none | PDmid_20touchedsolo | +4.5% (-1.8%..+7.1%) | +10% / +10% / +0% / +4% / +0% | 4/5 | 150.0k (132.6..164.0) | 143.3k |
| 12 | CRT4h30fw2solo | +16.6% (+6.7%..+38.2%) | +25% / +14% / +14% / +6% / -3% | 5/5 | 103.7k (73.9..139.9) | 87.5k |
| 12 | CRT4h30asia | +8.3% (+0.0%..+25.0%) | +13% / +10% / +18% / +6% / -3% | 4/5 | 103.7k (73.9..139.9) | 96.2k |
| 12 | camH3_40fw8any | +1.9% (-9.6%..+10.5%) | +5% / +14% / +12% / +2% / +5% | 4/5 | 103.7k (73.9..139.9) | 101.4k |
| 12 | CRT4h60 | +4.2% (-19.0%..+13.4%) | +9% / +6% / -6% / +1% / -12% | 4/5 | 103.7k (73.9..139.9) | 98.6k |
| 12 | PDmid_20touchedsolo | +4.7% (+0.6%..+9.1%) | +11% / +14% / +8% / +0% / +6% | 5/5 | 103.7k (73.9..139.9) | 99.0k |

CRT4h 30pts fw2 solo (all sessions) survives every phase: L6M maxDD cut +10.5% (+6.3..+12.4%) lock=None, +16.6% (+6.7..+38.2%) lock=12, 5/5 phases positive in both frames; phase-averaged Calmar gain L6M +14%, HOLD +16%, MID +7%, PRE +5%, X' +3% (lock none). The Asia-only cut is smaller (+4.3%) but 5/5; camH3 40 fw8 +5.2% (5/5) lock none and +1.9% (4/5) lock 12; CRT4h 60pts fresh solo +7.3% / +4.2% (4/5); PDmid 20 touched solo 4/5 and 5/5. Phase noise in the shipped L6M maxDD itself is large (132.6 .. 164.0k), which is why single-phase L6M cuts below about 10% are inside the lock-phase noise.


## s2 B2 round numbers: same-volume placebos (100 draws) for the top 5 cells by post-hoc score (Z2, ~08:00Z 2026-11-02)
The two 'any' rows are the identical mask to the 'fresh' rows (round-number lines are fresh/any-equivalent at these D). **Result: RECENT-ONLY, not a lead.** Against 100 random half-size draws of the same planned-lot volume the L6M maxDD cut ranks 0.07-0.11 (not at the 5% bar), HOLD 0.01-0.05 (beats), S_post 0.02-0.09; but PRE ranks 0.52-0.87 and X' 0.19-0.88 and the PRE Calmar gains are -18% to -62%: the lines help only after 2025-11 and hurt the older windows. They halve 10-25% of signals (R25 75%tgt: L6M maxDD cut +48% but Calmar -62% in PRE). Label: RECENT-ONLY / VOLUME-sensitive; shadow-log candidate only if the user wants a recent-regime test.
| B2 cell (added to the half mask, lock=None) | L6M cut | Calmar gain L6M / HOLD / MID / PRE / X' | n | same-volume placebo rank: L6M cut | HOLD | MID | PRE | X' | S_post | label |
|---|---|---|---|---|---|---|---|---|---|---|
| B2|R25|75%tgt|any | +48% | +91% / +62% / -28% / -62% / -12% | 100 | 0.07 | 0.01 | 0.78 | 0.87 | 0.86 | 0.02 | VOLUME (placebo matches) |
| B2|R25|75%tgt|fresh | +48% | +91% / +62% / -28% / -62% / -12% | 100 | 0.07 | 0.01 | 0.78 | 0.87 | 0.86 | 0.02 | VOLUME (placebo matches) |
| B2|R25|40pts|fresh | +40% | +68% / +38% / -2% / -38% / -17% | 100 | 0.11 | 0.05 | 0.52 | 0.52 | 0.88 | 0.09 | VOLUME (placebo matches) |
| B2|R25|40pts|any | +40% | +68% / +38% / -2% / -38% / -17% | 100 | 0.11 | 0.05 | 0.52 | 0.52 | 0.88 | 0.09 | VOLUME (placebo matches) |
| B2|R50|75%tgt|fresh | +41% | +57% / +37% / +2% / -18% / +27% | 100 | 0.07 | 0.01 | 0.42 | 0.75 | 0.19 | 0.03 | VOLUME (placebo matches) |


## BASE LABEL 2 (Z2, 2026-11-02 ~08:40Z): every V13X row above is on the 'DEFECT BASE (V13X)'
BASE-4 / ZL-3 found that d7lib dropped TH-L2 loss cuts and take-line exits that preceded the resting-add fill (846 rows). V13X = defect base; V13Y = fixed base. All V13X tables in this file (the lock=12 and lock=None screens, the CRT4h 30pts fw2 solo / camH3 / PDmid ranking, the Asia-only cell and its Asia-restricted placebos, the phase-averaged table, the B2 same-volume placebos, the chain CSVs sent to S5) are labelled 'defect base (V13X)'. Leads are being re-run on V13Y, lock=None headline and 12R, then the 1,933-cell screen, then placebos and the null; V13Y rows will be appended below and become the headline. The V13X best-of-N null run was stopped half-way (4 of 8 replicates) for this reason.


## s2 ON D7 V13Y (FIXED BASE) - leads re-run, lock=None HEADLINE and lock=12R (Z2, ~08:55Z 2026-11-02); POST-HOC, LEAD labels, no PASS
Same cells, same masks; only the engine changed (add-fill ordering fix). Placebos/noise band/phase average on V13Y are queued (leads first, then the screen).
**V13X (defect base) -> V13Y change for each lead (L6M maxDD cut, lock=None):** CRT4h 30pts fw2 solo +6% (STRICT) -> -0% (no gate: Calmar gain L6M -0%, HOLD -1%, MID -7%, PRE +3%, X' +8%; the strongest V13X lead DISAPPEARS); CRT4h 30pts fw2 solo Asia-only -> -2%; CRT4h 60pts fresh solo +4% -> +3% and now ONE-WEEK (-4% without the carrying week); camH3 40pts fw8 any +7% (STRICT) -> +8% (STRICT, 6/7 months, leave-one-week-out min +0.03, cut +9% without the carrying week; Calmar L6M +10%, HOLD +2%, MID +1%, PRE +1%, X' +40%) = the only cell that survives the base fix; PDmid 20pts touched solo +7% -> -0%; PDmid 30pts touched stacked +11% -> +6% (weak); OTE705 60pts a1-4 +5% -> -5%; B2 round numbers: R50 75%tgt fresh +41% -> +44% L6M cut with PRE Calmar -11% (VOLUME-type recent effect, LOMO 6/7 but min -0.16, no placebo yet), R25 cells reversed (PRE -38..-55%, MID -31..-49%). Lock=12R on V13Y: nothing is STRICT or TOLERANT; CRT4h30fw2solo and all PDmid/kijun1h/OTE705 cuts are ONE-WEEK (+0% without the carrying week), camH3 40 fw8 -5% (LOCK-ONLY reversal), B2 R25 40pts -17%.
**Reading:** on the fixed base the section-2 candidate set shrinks to camH3 40pts fw8 any (lock=None only; STRICT; maxDD cuts L6M -8%, PRE ~0, X' +40% Calmar; inside MDE; placebo and phase checks pending). The V13X reading 'CRT4h 30pts fw2 solo carries the layer' and its forward-shadow spec were driven by the dropped-exit defect and are withdrawn pending the V13Y screen.

#### V13Y lock=None (HEADLINE): shipped layer L6M 28.8k/wk, maxDD L6M 96.2k, HOLD 103.0k, MID 30.2k, PRE 129.7k, X' 69.7k

| cell | maxDD $k L6M / HOLD / MID / PRE / X' | Calmar gain L6M / HOLD / MID / PRE / X' | maxDD cut L6M | mean d L6M (MDE) | S/T/N | ONE-WEEK (cut w/o carrying week) | LOMO months>0, min | LOEO-week min cut | V13X->V13Y L6M cut | label |
|---|---|---|---|---|---|---|---|---|---|---|
| CRT4h60 | 93.1 / 113.1 / 36.6 / 129.9 / 70.9 | +6% / -7% / -8% / -1% / +2% | +3% | +0.6 (1.7) | -/-/N | ONE-WEEK (-4%) | 5/7, -0.15 | -0.04 | +4% -> +3% | ONE-WEEK |
| CRT4h60asia | 93.5 / 114.2 / 37.8 / 129.3 / 69.8 | +5% / -7% / -14% / -1% / +6% | +3% | +0.7 (1.7) | -/-/N | ONE-WEEK (-3%) | 5/7, -0.15 | -0.03 | +4% -> +3% | ONE-WEEK |
| CRT4h30fw2solo | 96.3 / 105.7 / 34.2 / 130.3 / 70.7 | -0% / -1% / -7% / +3% / +8% | -0% | -0.0 (0.7) | -/-/- | no (+1%) | 2/7, -0.00 | -0.02 | +6% -> -0% | weak |
| camH3_40fw8any | 88.5 / 103.8 / 30.1 / 131.2 / 64.7 | +10% / +2% / +1% / +1% / +40% | +8% | +0.3 (1.5) | S/-/N | no (+9%) | 6/7, +0.00 | +0.03 | +7% -> +8% | LEAD |
| PDmid_20touchedsolo | 96.3 / 103.0 / 33.1 / 131.5 / 70.1 | +3% / +5% / -5% / -2% / +3% | -0% | +0.8 (2.6) | -/-/N | no (+2%) | 1/7, -0.11 | -0.03 | +7% -> -0% | weak |
| PDmid_30touchedstk | 90.0 / 103.0 / 31.3 / 122.1 / 83.5 | +7% / -1% / -13% / +8% / -17% | +6% | +0.1 (2.8) | -/-/- | no (+0%) | 6/7, +0.00 | -0.03 | +11% -> +6% | weak |
| camH3_75fw8solo | 94.1 / 103.8 / 30.1 / 131.2 / 58.1 | +2% / +1% / +3% / +1% / +52% | +2% | -0.1 (2.8) | -/-/- | no (+9%) | 6/7, -0.06 | -0.05 | +7% -> +2% | weak |
| OTE705_60a14any | 100.7 / 100.7 / 35.2 / 124.1 / 65.1 | -4% / +2% / -13% / +4% / +38% | -5% | +0.0 (1.8) | -/-/- | no (-13%) | 0/7, -0.13 | -0.13 | +5% -> -5% | weak |
| kijun1h_60a14any | 98.9 / 98.9 / 31.2 / 139.9 / 77.0 | -2% / +9% / +3% / -8% / +30% | -3% | +0.3 (1.1) | -/-/N | no (-3%) | 0/7, -0.07 | -0.04 | -2% -> -3% | weak |
| PDmid_75a4solo | 101.0 / 101.3 / 29.9 / 126.4 / 64.0 | -3% / +3% / +1% / +6% / +16% | -5% | +0.6 (2.4) | S/T/N | no (-6%) | 0/7, -0.06 | -0.07 | -1% -> -5% | weak |
| CRT4h30asia | 97.6 / 105.7 / 34.1 / 129.3 / 69.2 | -1% / -1% / -7% / +3% / +10% | -2% | +0.1 (0.5) | -/-/- | no (-1%) | 1/7, -0.02 | -0.02 | n/a | weak |
| kijun1h_post | 90.0 / 103.7 / 31.7 / 135.2 / 85.4 | +4% / -3% / -6% / -8% / +10% | +6% | -0.9 (3.2) | -/-/- | no (+3%) | 6/7, +0.00 | -0.04 | n/a | weak |
| OTE705 | 100.3 / 104.4 / 32.8 / 149.2 / 74.1 | -5% / -3% / -1% / -14% / -2% | -4% | -0.2 (3.1) | -/-/- | no (-10%) | 0/7, -0.22 | -0.10 | n/a | weak |
| B2|R25|75%tgt|any | 87.2 / 87.2 / 47.7 / 166.6 / 113.6 | +3% / +7% / -49% / -55% / -54% | +9% | -1.9 (9.7) | -/-/- | no (+35%) | 6/7, -0.21 | -0.39 | n/a | weak |
| B2|R25|75%tgt|fresh | 87.2 / 87.2 / 47.7 / 166.6 / 113.6 | +3% / +7% / -49% / -55% / -54% | +9% | -1.9 (9.7) | -/-/- | no (+35%) | 6/7, -0.21 | -0.39 | n/a | weak |
| B2|R25|40pts|fresh | 103.4 / 103.4 / 39.4 / 143.9 / 108.6 | -12% / -8% / -31% / -38% / -50% | -7% | -1.4 (6.4) | -/-/- | no (+22%) | 1/7, -0.38 | -0.22 | n/a | weak |
| B2|R25|40pts|any | 103.4 / 103.4 / 39.4 / 143.9 / 108.6 | -12% / -8% / -31% / -38% / -50% | -7% | -1.4 (6.4) | -/-/- | no (+22%) | 1/7, -0.38 | -0.22 | n/a | weak |
| B2|R50|75%tgt|fresh | 53.9 / 71.0 / 28.6 / 134.1 / 57.3 | +59% / +39% / +2% / -11% / +59% | +44% | -3.0 (8.8) | -/-/- | no (+41%) | 6/7, -0.16 | +0.21 | n/a | weak |

#### V13Y lock=12R: shipped layer L6M 21.2k/wk, maxDD L6M 52.8k, HOLD 90.4k, MID 52.3k, PRE 282.2k, X' 131.5k

| cell | maxDD $k L6M / HOLD / MID / PRE / X' | Calmar gain L6M / HOLD / MID / PRE / X' | maxDD cut L6M | mean d L6M (MDE) | S/T/N | ONE-WEEK (cut w/o carrying week) | LOMO months>0, min | LOEO-week min cut | V13X->V13Y L6M cut | label |
|---|---|---|---|---|---|---|---|---|---|---|
| CRT4h60 | 51.8 / 96.5 / 43.8 / 279.2 / 128.0 | +9% / +0% / +68% / +4% / -2% | +2% | +1.4 (4.0) | -/-/- | no (+1%) | 7/7, +0.01 | +0.01 | n/a | weak |
| CRT4h60asia | 51.8 / 96.5 / 47.2 / 275.3 / 124.7 | +9% / +1% / +47% / +4% / -1% | +2% | +1.5 (4.0) | -/-/- | no (+1%) | 7/7, +0.01 | -0.01 | n/a | weak |
| CRT4h30fw2solo | 52.7 / 91.0 / 57.6 / 262.7 / 123.8 | -0% / +1% / +8% / +9% / +3% | +0% | -0.1 (0.6) | -/-/- | ONE-WEEK (+0%) | 5/7, +0.00 | +0.00 | n/a | ONE-WEEK |
| camH3_40fw8any | 55.5 / 90.4 / 39.2 / 235.1 / 143.5 | -7% / +5% / +95% / +19% / -10% | -5% | -0.5 (2.0) | -/-/- | no (+0%) | 0/7, -0.05 | -0.05 | n/a | weak |
| PDmid_20touchedsolo | 52.2 / 83.2 / 52.8 / 283.7 / 133.9 | +5% / +16% / +8% / -2% / -9% | +1% | +0.8 (2.4) | -/-/N | ONE-WEEK (+0%) | 5/7, +0.00 | -0.03 | n/a | ONE-WEEK |
| PDmid_30touchedstk | 52.2 / 92.2 / 56.6 / 249.8 / 140.1 | +8% / +3% / -25% / +7% / -12% | +1% | +1.5 (4.5) | -/-/- | ONE-WEEK (+0%) | 5/7, +0.00 | +0.00 | n/a | ONE-WEEK |
| camH3_75fw8solo | 56.8 / 90.4 / 39.2 / 238.1 / 143.7 | -11% / +2% / +97% / +18% / -17% | -8% | -1.0 (2.5) | -/-/- | no (+0%) | 0/7, -0.08 | -0.08 | n/a | weak |
| OTE705_60a14any | 51.7 / 91.3 / 57.3 / 247.1 / 161.1 | +6% / -1% / -24% / +7% / -11% | +2% | +0.7 (1.5) | -/-/- | no (+1%) | 7/7, +0.01 | +0.01 | n/a | weak |
| kijun1h_60a14any | 52.2 / 94.4 / 53.3 / 237.0 / 185.8 | +3% / -3% / -2% / +3% / -14% | +1% | +0.3 (0.9) | -/-/N | ONE-WEEK (+0%) | 5/7, +0.00 | +0.00 | n/a | ONE-WEEK |
| PDmid_75a4solo | 52.2 / 83.5 / 54.6 / 252.3 / 133.3 | +5% / +12% / -3% / +11% / -7% | +1% | +0.7 (2.3) | -/-/- | ONE-WEEK (+0%) | 5/7, +0.00 | +0.00 | n/a | ONE-WEEK |
| CRT4h30asia | 52.7 / 91.0 / 57.7 / 263.4 / 123.8 | +1% / +1% / +6% / +8% / +3% | +0% | +0.1 (0.4) | -/-/- | ONE-WEEK (+0%) | 5/7, +0.00 | +0.00 | n/a | ONE-WEEK |
| kijun1h_post | 52.2 / 97.9 / 54.5 / 192.8 / 129.5 | -3% / -9% / -4% / +23% / -8% | +1% | -0.9 (2.9) | -/-/- | ONE-WEEK (+0%) | 5/7, +0.00 | +0.00 | n/a | ONE-WEEK |
| OTE705 | 52.2 / 94.5 / 54.1 / 253.5 / 170.2 | +2% / -6% / -8% / +7% / -13% | +1% | +0.2 (1.9) | -/-/- | ONE-WEEK (+0%) | 5/7, +0.00 | +0.00 | n/a | ONE-WEEK |
| B2|R25|75%tgt|any | 50.9 / 79.1 / 39.9 / 265.0 / 89.3 | -12% / +17% / +189% / -29% / -7% | +4% | -3.1 (6.4) | -/-/- | no (+2%) | 7/7, +0.04 | +0.02 | n/a | weak |
| B2|R25|75%tgt|fresh | 50.9 / 79.1 / 39.9 / 265.0 / 89.3 | -12% / +17% / +189% / -29% / -7% | +4% | -3.1 (6.4) | -/-/- | no (+2%) | 7/7, +0.04 | +0.02 | n/a | weak |
| B2|R25|40pts|fresh | 61.6 / 79.2 / 61.8 / 223.2 / 132.6 | -23% / +12% / +29% / -9% / -19% | -17% | -2.2 (4.2) | -/-/- | no (-12%) | 2/7, -0.17 | -0.17 | n/a | weak |
| B2|R25|40pts|any | 61.6 / 79.2 / 61.8 / 223.2 / 132.6 | -23% / +12% / +29% / -9% / -19% | -17% | -2.2 (4.2) | -/-/- | no (-12%) | 2/7, -0.17 | -0.17 | n/a | weak |
| B2|R50|75%tgt|fresh | 70.4 / 91.9 / 56.6 / 235.4 / 109.4 | -42% / -14% / +4% / -0% / -4% | -33% | -4.8 (11.1) | -/-/- | no (-35%) | 1/7, -0.52 | -0.35 | n/a | weak |


## s2 V13Y lock=None full screen (1,192 masks / 1,902 changed cells), ~09:35Z 2026-11-02
Gate counts: STRICT 48, TOLERANT 86, NOW-ONLY 662 (TOL-B 596, TOL-nc 120); positive honest score 42%, positive post-hoc 39%; **0 cells meet the L6M RISK-KEEP rule**. Honest and post-hoc rankings agree on no line. Survivors by label: camH3 40pts fw8 any (post-hoc; STRICT is lost in the screen's tier column here because HOLD +2% is positive but PRE/X' small; L6M maxDD 96.2 -> 88.5k, -8%; Calmar +10% L6M, +2% HOLD, +1% MID/PRE, +40% X'; neighbours 3/4 same sign; LOEO worst -0.00) = LEAD-weak; PDmid 40pts fw1 stacked (TOL: L6M +3%, HOLD +14%, PRE +4%, X' -9%) = LEAD-weak; CRT4h 20pts fw1 solo (STRICT/TOL/NOW but L6M +0%, MID -12%) = weak. The V13X leader CRT4h 30pts fw2 solo is the honest pick here with L6M -0%: gone. Placebos (100 draws x 3 kinds, 5 cells), phase averages and the V13Y null are queued after the lock=12R screen.
V13Y l0 full screen: 1902 changed distinct-key cells; S_hon>0 0.42, S_post>0 0.39; STRICT 48, TOL 86, NOW 662, TOL-B 596, TOL-nc 120, RISK-KEEP(L6M rule) 0

| line | pick | cell | maxDD $k L6M / HOLD / MID / PRE / X' | Calmar gain L6M / HOLD / MID / PRE / X' | mean d L6M (MDE) | S/T/N | RK | neighbours n, mean S, same sign | LOEO worst S (episode) |
|---|---|---|---|---|---|---|---|---|---|
| CRT4h | HONEST | CRT4h|30pts|fw2|solo | 96.3 / 105.7 / 34.2 / 130.3 / 70.7 | -0% / -1% / -7% / +3% / +8% | -0.0 (0.7) | -/-/- | no | 4, +0.03, 4/4 | +0.06 (202506-202509) |
| CRT4h | POST-HOC | CRT4h|20pts|fw1|solo | 97.4 / 101.3 / 35.0 / 132.8 / 72.6 | +0% / +4% / -12% / -2% / +3% | +0.4 (0.6) | S/T/N | no | 3, +0.01, 2/3 | -0.00 (202606-202607) |
| KCup4h | HONEST | KCup4h|15pts|fresh|solo | 96.2 / 103.0 / 30.2 / 129.1 / 69.7 | -0% / -0% / -2% / +2% / +3% | -0.0 (0.3) | -/-/- | no | 4, +0.01, 3/4 | +0.02 (202435-202440) |
| KCup4h | POST-HOC (ungated) | KCup4h|20pts|fresh|solo | 96.2 / 103.0 / 30.2 / 129.7 / 69.7 | +0% / +0% / +0% / +0% / +0% | +0.0 (0.0) | -/-/- | no | 4, -0.01, 2/4 | +0.00 (202435-202440) |
| OTE705 | HONEST | OTE705|60pts|a1-4|any | 100.7 / 100.7 / 35.2 / 124.1 / 65.1 | -4% / +2% / -13% / +4% / +38% | +0.0 (1.8) | -/-/- | no | 3, +0.06, 2/3 | +0.18 (202435-202440) |
| OTE705 | POST-HOC (ungated) | OTE705|30pts|a1-4|solo | 96.2 / 98.7 / 33.6 / 127.3 / 64.5 | +2% / +6% / -8% / -2% / +38% | +0.5 (1.4) | -/-/N | no | 4, -0.05, 2/4 | +0.01 (202628-202632) |
| OTE79 | HONEST | OTE79|10pts|touched|any | 111.7 / 111.7 / 29.4 / 136.0 / 56.7 | -17% / -8% / +6% / -7% / +38% | -1.0 (2.6) | -/-/- | no | 2, +0.02, 1/2 | +0.15 (202606-202607) |
| OTE79 | POST-HOC | OTE79|20pts|fw2|any | 96.2 / 103.0 / 30.2 / 129.7 / 66.0 | +1% / +1% / +0% / +0% / +2% | +0.2 (0.5) | -/T/N | no | 4, -0.01, 1/4 | +0.01 (202606-202607) |
| PDmid | HONEST | PDmid|40pts|fresh|any | 99.6 / 99.6 / 35.1 / 136.9 / 56.7 | -7% / +5% / -12% / -8% / +40% | -1.2 (1.9) | -/-/- | no | 4, +0.08, 4/4 | +0.16 (202411-202415) |
| PDmid | POST-HOC | PDmid|40pts|fw1|stk | 96.2 / 96.2 / 30.8 / 125.9 / 78.7 | +3% / +14% / -1% / +4% / -9% | +1.0 (2.2) | -/T/N | no | 3, +0.06, 3/3 | +0.03 (202606-202607) |
| STK | HONEST | STK|C8|stk2|fresh|15pts|only | 128.2 / 128.2 / 39.9 / 151.2 / 69.9 | -22% / -15% / -20% / -22% / +52% | +1.3 (4.1) | -/-/N | no | 4, +0.07, 4/4 | +0.14 (202435-202440) |
| STK | POST-HOC (ungated) | STK|C8|stk2|fresh|75%tgt|add | 96.0 / 96.0 / 37.7 / 137.0 / 63.4 | -2% / +11% / -12% / -9% / +27% | -0.8 (1.5) | -/-/- | no | 3, +0.01, 2/3 | -0.01 (202606-202607) |
| camH3 | HONEST | camH3|75%tgt|fw8|any | 94.1 / 103.8 / 30.1 / 131.2 / 55.4 | +2% / +1% / +3% / +1% / +59% | -0.0 (2.7) | -/-/- | no | 3, +0.13, 3/3 | +0.27 (202435-202440) |
| camH3 | POST-HOC (ungated) | camH3|40pts|fw8|any | 88.5 / 103.8 / 30.1 / 131.2 / 64.7 | +10% / +2% / +1% / +1% / +40% | +0.3 (1.5) | S/-/N | no | 4, +0.01, 3/4 | -0.00 (202628-202632) |
| kijun1h | HONEST | kijun1h|40pts|fw2|stk | 97.0 / 97.0 / 39.0 / 127.0 / 69.5 | -3% / +11% / -15% / +1% / +42% | -0.5 (1.7) | -/-/- | no | 4, +0.19, 4/4 | +0.21 (202411-202415) |
| kijun1h | POST-HOC (ungated) | kijun1h|40pts|a1-4|any | 96.4 / 96.4 / 31.2 / 139.9 / 77.0 | +1% / +12% / +3% / -8% / +21% | +0.3 (1.0) | -/-/N | no | 4, -0.04, 2/4 | +0.01 (202606-202607) |


## s2 V13Y lock=12R full screen (1,933 changed cells), ~10:15Z 2026-11-02
STRICT 61, TOLERANT 137, NOW-ONLY 553 (TOL-B 427, TOL-nc 156); 0 cells meet the L6M RISK-KEEP rule. The 12R-frame post-hoc leader CRT4h 60pts fresh any (L6M maxDD cut +24%, Calmar +24% L6M / +10% HOLD / +68% MID / +3% PRE / +2% X', STRICT, 3/3 neighbours, LOEO min +0.17) has a lock=None L6M cut of about +3% (ONE-WEEK there) => **LOCK-ONLY**, not a lead under the lead's rule. kijun1h 40pts fresh any is S/T/N in the 12R frame (L6M +2%, HOLD +11%, PRE +19%, mean +3.0k, MDE 9.1) with an L6M cut of 0% in the lock-none frame: LOCK-ONLY as well. Candidates present in BOTH frames: camH3 40pts fw8 any (lock none STRICT-ish, lock 12R -5%): not consistent; PDmid 40pts fw1 stacked: lock none TOL, lock 12R mixed. Nothing is a lead in both frames on V13Y.
V13Y l12 full screen: 1933 changed distinct-key cells; S_hon>0 0.38, S_post>0 0.49; STRICT 61, TOL 137, NOW 553, TOL-B 427, TOL-nc 156, RISK-KEEP(L6M rule) 0

| line | pick | cell | maxDD $k L6M / HOLD / MID / PRE / X' | Calmar gain L6M / HOLD / MID / PRE / X' | mean d L6M (MDE) | S/T/N | RK | neighbours n, mean S, same sign | LOEO worst S (episode) |
|---|---|---|---|---|---|---|---|---|---|
| CRT4h | HONEST | CRT4h|15pts|fw2|any | 53.3 / 91.2 / 58.0 / 278.3 / 96.7 | -1% / -0% / -8% / +2% / +12% | +0.1 (0.6) | -/-/- | no | 4, +0.03, 4/4 | +0.03 (202314-202323) |
| CRT4h | POST-HOC | CRT4h|60pts|fresh|any | 51.8 / 96.5 / 43.8 / 276.7 / 128.0 | +24% / +10% / +68% / +3% / +2% | +4.7 (9.1) | S/T/N | no | 3, +0.16, 3/3 | +0.17 (202435-202516) |
| KCup4h | HONEST | KCup4h|60pts|fw1|solo | 53.1 / 90.7 / 52.3 / 194.9 / 138.1 | -1% / +1% / +13% / +34% / -3% | -0.1 (1.0) | -/-/- | no | 2, +0.01, 1/2 | +0.14 (202314-202323) |
| KCup4h | POST-HOC | KCup4h|15pts|fresh|any | 52.8 / 90.4 / 52.3 / 281.3 / 131.5 | +0% / -0% / -5% / +4% / +0% | +0.0 (0.2) | -/T/N | no | 4, -0.00, 3/4 | -0.00 (202548-202550) |
| OTE705 | HONEST | OTE705|75%tgt|fw4|any | 52.2 / 92.4 / 51.2 / 232.4 / 120.3 | +0% / -4% / +2% / +13% / +5% | -0.2 (1.6) | -/-/- | no | 3, +0.05, 2/3 | +0.01 (202435-202516) |
| OTE705 | POST-HOC | OTE705|15pts|fresh|any | 52.8 / 90.7 / 60.9 / 277.1 / 131.2 | +7% / +3% / -24% / +1% / +0% | +1.4 (3.5) | S/T/N | no | 4, +0.04, 3/4 | +0.04 (202604-202608) |
| OTE79 | HONEST | OTE79|60pts|fw2|solo | 52.2 / 101.3 / 53.3 / 266.9 / 131.5 | -2% / -15% / -10% / +3% / -2% | -0.6 (1.7) | -/-/- | no | 3, -0.03, 1/3 | -0.00 (202314-202323) |
| OTE79 | POST-HOC (ungated) | OTE79|60pts|touched|solo | 64.7 / 64.7 / 48.7 / 310.7 / 120.9 | -18% / +53% / +14% / -14% / +1% | +0.1 (5.0) | -/-/- | no | 2, +0.04, 1/2 | -0.10 (202604-202608) |
| PDmid | HONEST | PDmid|75%tgt|fresh|any | 52.9 / 88.1 / 47.7 / 259.0 / 108.0 | -3% / +10% / +28% / +12% / +11% | -0.5 (1.7) | -/-/- | no | 3, +0.06, 3/3 | +0.12 (202604-202608) |
| PDmid | POST-HOC | PDmid|75%tgt|fw1|solo | 55.0 / 83.1 / 52.3 / 280.2 / 132.6 | -2% / +21% / +14% / +0% / -0% | +0.3 (0.8) | -/T/N | no | 2, +0.09, 2/2 | +0.01 (202604-202608) |
| STK | HONEST | STK|C8|clu3|fresh|10pts|only | 51.7 / 120.2 / 77.7 / 279.4 / 67.3 | +12% / -12% / -19% / +8% / +83% | +2.1 (5.2) | -/-/- | no | 3, +0.26, 3/3 | -0.00 (202314-202323) |
| STK | POST-HOC (ungated) | STK|C8|stk2|fresh|60pts|only | 52.1 / 93.4 / 74.3 / 342.9 / 76.9 | +20% / +16% / +14% / -21% / +12% | +3.9 (8.7) | -/-/N | no | 3, +0.15, 3/3 | +0.18 (202604-202608) |
| camH3 | HONEST | camH3|60pts|touched|solo | 87.9 / 107.5 / 56.4 / 184.0 / 149.7 | -38% / -10% / -4% / +36% / -5% | +0.7 (10.2) | -/T/N | no | 2, +0.08, 2/2 | -0.04 (202435-202516) |
| camH3 | POST-HOC | camH3|60pts|touched|any | 88.0 / 107.5 / 56.4 / 185.3 / 149.2 | -37% / -10% / -2% / +35% / -5% | +0.9 (10.4) | -/T/N | no | 2, -0.08, 1/2 | -0.30 (202604-202608) |
| kijun1h | HONEST | kijun1h|40pts|fresh|any | 58.9 / 88.9 / 56.7 / 235.3 / 107.3 | +2% / +11% / -7% / +19% / +7% | +3.0 (9.1) | S/T/N | no | 4, +0.08, 4/4 | +0.10 (202314-202323) |
| kijun1h | POST-HOC | kijun1h|40pts|fw1|solo | 58.0 / 90.0 / 54.1 / 270.0 / 125.7 | +5% / +11% / +1% / +3% / -1% | +3.3 (9.1) | -/T/N | no | 3, +0.03, 2/3 | +0.07 (202604-202608) |


## s2 FINAL ON V13Y (fixed base), lock=None placebos n=100 per kind (Z2, ~11:00Z 2026-11-02)
**Verdict:** on the fixed base nothing in section 2 is a lead in both lock frames and nothing beats its L6M maxDD placebos. camH3 40pts fw8 any: L6M maxDD cut +8% (not ONE-WEEK), ranks 0.15-0.18 on L6M, X' sday 0.05: LEAD-weak, inside MDE. PDmid 40pts fw1 stacked: no maxDD cut (+0%), but HOLD ranks 0.02, PRE 0.05-0.07, S_post 0.01-0.05 against count/volume placebos (Calmar gain through the mean: HOLD +14%): LEAD-weak, mean-side. camH3 75%tgt fw8 any: X' ranks 0.01-0.02 only. CRT4h 30pts fw2 solo (the withdrawn V13X lead): ranks 0.34-0.80, nothing; CRT4h 20pts fw1 solo: nothing. V13X lead withdrawn: its apparent L6M cut and STRICT status came from the dropped-exit defect. Lock-12R-only: CRT4h 60pts fresh any (L6M +24%), kijun1h 40pts fresh any = LOCK-ONLY. B2 round numbers on V13Y: R50 75%tgt L6M cut +44% with PRE Calmar -11% (recent-type volume effect), R25 reversed: no lead. Recommendation for the policy file: keep the shipped D20 fresh half on all seven lines; the only items to carry into a forward shadow are camH3 40pts fw8 any and PDmid 40pts fw1 stacked as LEAD-weak, shadow-only. NOT done on V13Y: best-of-N null (the V13X null was stopped; the grid-level evidence is the gate counts: 48 STRICT / 86 TOLERANT of 1,902 lock-none cells and 61 / 137 of 1,933 lock-12R cells, 0 RISK-KEEP in both), Asia-restricted placebos, phase-averaged check, session-level lock-none stage (all on the V13X defect base only).
| cell (V13Y lock=None) | kind | n | L6M cut | rank L6M | rank HOLD | rank MID | rank PRE | rank X' | rank Calmar L6M | rank S_post | ONE-WEEK | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| camH3_40fw8any | cnt | 100 | +8% | 0.17 | 0.43 | 0.18 | 0.39 | 0.17 | 0.16 | 0.17 | no | no placebo beat |
| camH3_40fw8any | vol | 100 | +8% | 0.18 | 0.40 | 0.25 | 0.36 | 0.18 | 0.15 | 0.13 | no | no placebo beat |
| camH3_40fw8any | sday | 100 | +8% | 0.15 | 0.35 | 0.63 | 0.51 | 0.05 | 0.12 | 0.16 | no | no placebo beat |
| camH3_75fw8any | cnt | 100 | +2% | 0.35 | 0.28 | 0.22 | 0.35 | 0.02 | 0.33 | 0.27 | no | no placebo beat |
| camH3_75fw8any | vol | 100 | +2% | 0.40 | 0.38 | 0.21 | 0.35 | 0.02 | 0.44 | 0.33 | no | no placebo beat |
| camH3_75fw8any | sday | 100 | +2% | 0.29 | 0.35 | 0.64 | 0.42 | 0.01 | 0.24 | 0.26 | no | no placebo beat |
| CRT4h20fw1solo | cnt | 100 | -1% | 0.67 | 0.10 | 0.93 | 0.59 | 0.62 | 0.43 | 0.16 | no | no placebo beat |
| CRT4h20fw1solo | vol | 100 | -1% | 0.66 | 0.12 | 0.94 | 0.67 | 0.75 | 0.52 | 0.21 | no | no placebo beat |
| CRT4h20fw1solo | sday | 100 | -1% | 0.42 | 0.35 | 0.33 | 0.54 | 0.34 | 0.26 | 0.22 | no | no placebo beat |
| PDmid_40fw1stk | cnt | 100 | +0% | 0.55 | 0.02 | 0.60 | 0.07 | 0.96 | 0.27 | 0.05 | no | no placebo beat |
| PDmid_40fw1stk | vol | 100 | +0% | 0.47 | 0.02 | 0.61 | 0.05 | 0.90 | 0.19 | 0.01 | no | no placebo beat |
| PDmid_40fw1stk | sday | 100 | +0% | 0.40 | 0.09 | 0.41 | 0.05 | 0.67 | 0.34 | 0.17 | no | no placebo beat |
| CRT4h30fw2solo | cnt | 100 | -0% | 0.47 | 0.72 | 0.80 | 0.45 | 0.49 | 0.48 | 0.50 | no | no placebo beat |
| CRT4h30fw2solo | vol | 100 | -0% | 0.52 | 0.79 | 0.80 | 0.38 | 0.54 | 0.52 | 0.60 | no | no placebo beat |
| CRT4h30fw2solo | sday | 100 | -0% | 0.34 | 0.53 | 0.25 | 0.13 | 0.24 | 0.31 | 0.32 | no | no placebo beat |
