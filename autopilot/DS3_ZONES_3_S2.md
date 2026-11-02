
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
