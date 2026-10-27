# DS3 T-ICT progress (D3IC) - paused 2026-10-27 on lead order (priority list); resume exactly as below

## Frozen / hashed (logged in autopilot/DECISIONS.md, files l2vast/ds3/prereg/IC_IC1..IC6.md + .sha256)
IC1 af2f78c8..., IC2 afe1b5e7..., IC3 83e2ef0c..., IC4 d9277d23..., IC5 53ada1d3..., IC6 b19846bb... (172 cells; ledger +172 -> 51174).
Code: l2vast/ds3/code/ic/ (ic_lib, ic_kern, ic_fam, ic_mtf, ic_cells, ic_run, ic_prereg, ic_counts, ic_trunc, ic_pre, ic_final, ic_report[draft]). Out: l2vast/ds3/out/IC/.

## Done
- All 172 cells scored MAPPED (0 errors, 9 DEAD too-few-trades): out/IC/res_IC1..IC6.json (+_daily.parquet, trades_*.parquet).
- Audits: truncation-invariance 164 cells / 2,411,968 setups / 0 mismatches (out/IC/trunc_audit.json); runner identity vs te_core.gen_entries 21,768 trades and vs sf_lib runner 52k market trades, 0 mismatches (out/IC/identity_audit.json).
- PRE text + the ONE logged holdout look for DS3_TICT done (autopilot/DS3_TICT_PREHOLD.md). ic_final.py TICT run: rows l2vast/ds3/rows/DS3_TICT.json, out/IC/final_df_TICT.pkl, equal_risk_TICT.json, SERIES + paper_all registered for PASS/CANDIDATE (ds3_<cell>.json), addbook looks logged.
- Strict verdict (standard gates + added CONS gate): 1 PASS (IF_5m_tg_pd), 8 CANDIDATE (FV_15m_ea/ec/ed, IF_3m_tg_pd, IF_5m_tg_sess, BK_5m_ec, BK_5m_ea_tg_sess, BK_5m_ea_tf60). Standard MAPPED-only verdict would be 1 PASS / 37 CANDIDATE: the P9 mapping credits stop exits +2.6..+4.2 pts (2025-26), inflating small-stop cells (e.g. IF_15s_eb PRE $49k/wk mapped vs -$17.7k CONS).
- Rubric: A+ is very rare (3m: 10-25 setups; 15 s: ~670); A+ vs B: 29 cells with enough A+, A+>B in 12, CI above 0 in 1, below 0 in 6 -> A+ does not beat B. A- vs B ~ coin flip (57/113 positive). Delivery flag is true for most setups on fine bars.

## NOT done (resume here)
1. IC7 (post-look follow-up, defined in ic_cells.py, prereg text added to ic_prereg.py HEADS['IC7'], counts computed in out/IC/cell_counts.json) is NOT yet hashed/scored: controls (mirror/shift60) for the 9 survivors, shift180 for IF_5m_tg_pd/IF_5m_tg_sess, 3x3 widening around the PASS (cells tf 3/5/15 x size 2/4/8, tgt pd) + 2 stop neighbours = 29 cells. Steps: `python3 ic_prereg.py IC7` (logs sha) -> add 'IC7' to ic_run chain (`corepool run 4 1 -- python3 ic_run.py IC7 24`) -> a second logged read (DS3_TICT_IC7) -> report separately (post-look cells cannot add to the family count). The PASS has no mirror/shift control yet: do not treat it as a result before IC7.
2. ic_report.py is a draft (leaderboard table only): write autopilot/DS3_TICT.md (leaderboard, rubric section, column splits from grades/cols in final_df, controls, disclosures), verdict line, DECISIONS hand-back.
3. Direct L2 (ic_direct.py): only for market-entry (mode c) finalists with positive paired CI; none identified yet (only FV_15m_ec is market among survivors; its paired-vs-ST not yet checked). Not started; no replay launched.
## Disclosures so far
Two cells smoke-tested before preregs (logged); stop-credit artifact discovered pre-scoring -> CONS gate added; accidental overwrite of out/SF/identity_audit.json restored (logged). Trend-beta caveat: PASS uses prior-day H/L target (mean ~314 pts, win 12% at R 10).
