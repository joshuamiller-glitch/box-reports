# DD-2 prereg: DS3_DRAWDOWN_SIXTY (post-hoc pricing of the existing SIXTY lists; no new cell, no selection)
Written 2026-10-31 before any scored statistic. Capped 20260206; UNTOUCHED never read. No PASS claim.

Inputs: l2vast/ds3/out/sixty/sixty_list60.csv, sixty_list70.csv (v2), stream_W.npy / stream_meta.csv (stream/2.35 = live $ per week delta on the as-is stack), live_stack_weekly.npy (ONE_CONVENTION ASIS|off), sunday_comp_weekly.npy (COMP|s0.25|k670|off), 149 weeks from 2023-04-03.
Rule series: x_i = size_rec_i * stream_i/2.35 (shrunk size, live lots). Combined = base + x_i (base = stack as-is; second base = Sunday composite; additive, no joint re-run).
Windows: L3M 13 wk, L6M, HOLD, PRE, X' (s0_common masks), ALL 149 wk. Headline windows: ALL, PRE, X' (L3M/L6M/HOLD have <20 losing weeks: shown, not relied on).
Metrics per window: mean, weekly SD, maxDD of weekly cumulative (within window), worst-20 = sum of 20 lowest weeks, Calmar = mean/maxDD, mean/|worst-20|.
Same-lot: change in maxDD and worst-20 (base -> base + x). Equal-risk: scale k = w20(base)/w20(base+x) (only where both worst-20 < 0), mean change = k*mean(base+x) - mean(base).
MDE (ALL) = 2.8 * SD(x)/sqrt(n_weeks). 
Placebo (rules that remove volume): volume cut f = clip(-beta, 0, 0.9), beta = OLS slope of weekly x on weekly base (ALL); f < 0.02 => no volume removed identified, placebo n/a. 200 draws: random skip of days (daily base ASIS|off from oc_res.pkl, each day dropped w.p. f, seed 20261031) and deterministic size cut (1-f); placebo = the better of the two on maxDD cut (95th percentile of skip draws, and f). Rule "beats" if its maxDD cut (ALL) exceeds both.
RISK-KEEP: maxDD cut ALL >= 20% AND dmean >= -MDE AND beats placebo (or placebo n/a flagged). If cut>=20% and mean ok but placebo not beaten: "RISK-KEEP (volume effect)". Else no. PRE and X' maxDD cut sign shown as agreement flags.
Ranking: Calmar (ALL, base+x vs stack as-is) at shrunk size, size_rec>0 only; headline ranking excludes trade-sum streams (M-basis, not lock engine), fill_artefact rows, EQR (stack scaler, not additive); these shown beside. Ledger-only rules (no stream) not rankable: counted. Second rank: Calmar vs Sunday composite; third: $/wk shrunk_live_wk rank, rank-correlation reported.
Top-N (N=5/10/20) portfolios by Calmar rank, additive; plain and one-per-cluster variants.
Columns STRICT / TOLERANT(literal) / NOW-ONLY taken from the list file as is. dead_lookup: n/a (no new spec); DEAD_CELLS: nothing appended.
Code: l2vast/ds3/code/dd2/. Outputs: l2vast/ds3/out/drawdown_sixty/ ; autopilot/DS3_DRAWDOWN_SIXTY.md.
