# DS3 T-STRUCT-FIB (D3SF)
Generated 2026-10-27T11:07:44Z. Research only; no live/execution/chart change. Code l2vast/ds3/code/sf/ (sf_lib.py shared detector + runner, sf_kern.py state machines, sf_fam.py, sf_cells.py, sf_run.py); preregs l2vast/ds3/prereg/SF_SF1.md, SF_SF2.md (sha256 in DECISIONS.md: SF1 96203422219832d5a7bfe1516aeb832512c9b1b07476bad14712b062146de5e9, SF2 df64ad0329147089c54d325c15b4007ac12e3371053e686f556b5fc667ce5bbb); rows l2vast/ds3/rows/DS3_TSF.json; per-cell trades out/SF/trades_*.parquet; holdout look logged for DS3_TSTRUCTFIB (autopilot/DS3_TSTRUCTFIB_PREHOLD.md).

## 1. Verdict
**Struct-fib: 0 PASS, 0 CANDIDATE; best cell SF_runner_tf1m_L3 (highest WF $/wk among cells with >= 3 trades/wk, DEAD: fails WF_CI>0,SPAN2>0,plc>=.95), 8.9 trades/wk, R multiple 5.60, win rate 0.18 vs required 0.15.**
46 cells scored (SF1 30 = 16 L x bars grid + external/internal + sweep/pullback/validity/entry/cancel variations; SF2 16 = stop/target/exceed variations, runner, mirror and time-shift controls). Verdicts (MAPPED, resting limits are mapped-only): {'DEAD': 46}. 9 cells have fewer than 100 trades over 3.7 years (DEAD, too few trades: the sweep -> impulse -> first pullback -> 100% extension -> retrace sequence is rare: 3-min L=3 gives 552 trades = 3.9/wk, 5-min L=5 90, 15-min none) and 29 cells are below 3 trades/wk (LOW-FREQUENCY, which alone fails gate 1).
No cell passes or is a CANDIDATE: every cell fails the WF week-block CI (the weekly mean is never distinguishable from 0 at MDE $8-13k/wk), most also fail the 2023 span and the timing placebo. Where WF/HOLD means are positive (e.g. the 1-min base +$1.3k WF, runner +$2.6k) the placebo rank on PRE is 0.25-0.50 for the 1-min cells, i.e. random entries with the same stop and target distances do as well; the mirror (fade) and the 180-min time-shifted controls are positive in WF (+$7.3k for the 1-min mirror), which shows the 2024-26 sample rewards almost any long-biased small-stop, wide-target bracket (trend beta), so positive raw means here are not evidence of the sequence. Power: per-trade MDE about 3-8 pts (cells with 100-2,200 trades), weekly MDE $8-13k; observed WF means of $0.2-2.6k are far inside it: a null here means 'could not have seen less than about $8k/wk', not 'no effect'.
Required-vs-observed hurdle: the 37 cells with >= 100 trades have a median realised R of 4.4 (261.8% target with a leg-2 stop) and median observed win 19.5% vs required 18.5% (observed minus required: median +1.1 pts, range -5.9 to +4.1 pts): the hit rate sits on the break-even line, a gross edge of about one point of win rate that costs and the weekly noise absorb; the fixed-60-stop control has win 53-55% at R about 1 (WF +$2.2k, tpw 2.8, fails CI and 2023) and the nearer targets (161.8/200) lower the R but not the sign.
Generic structure controls (BOS / CHoCH / HH-HL sequence entries of TREND PRO R1): the 24 TR1E cells are the same machinery already scored (all DEAD but TR1E_retest_15m_c3 CANDIDATE); NOT re-run (duplicates of existing cells); copied into the table below.

## 2. Method and definitions
Full definitions are in the prereg files (sequence, extension anchors, order and exit rules, risk cap, windows, verdict rule). Highlights and disclosures:
- ONE swing detector (fractal L, strict, confirmed at j+L) and ONE runner shared with T-SBS. Truncation-invariance: 207 cells (all of SF and SBS/CRT), data cut at 62%, 618,975 setups compared, mismatches 0 (out/SF/trunc_audit.json). Identity audit of the runner against te_core.gen_entries: 21,768 trades in 3 pullback cells, 0 mismatches in entry/exit minute, exit type and points (out/SF/identity_audit.json).
- Sweep 'external' = below the running 18:00-session low (>= 30 min in), 'internal' otherwise; 'second-pullback origin' is read as the start of the second leg (= first-pullback end). The 100%-extension is Pb + (H1 - S); the limit is X100 - f x (X100 - Pb); the exceed-cancel is measured on seconds after the validity bar. Entries/exits as in the prereg. RISK CAP: setups with stop distance > 60 or < 4 pts are not traded (DS2 stop width) - a design addition, disclosed.
- Mapped pricing charges limit fills the market-entry P9 correction (conservative). Ladder P&L is normalised to the filled size. Locks run at 10 lots whatever the stop width.
- Grid coverage: scored = 16 (L x bars) at the base + one-factor-at-a-time variations; NOT scored: the full cross of sweep x pullback x validity x entry x cancel x exceed x stop x target (about 10^5 cells), ladder/61.8 on other bars, the runner on external sweeps, 15-s/30-s bars (the directive lists {1,3,5,15}-min for this family).
- Placebo: timing-destroyed (same side/hour mix, same stop and target distances), 40 draws, run when PRE > 0. DSR with N = 46 (track) and the ledger total; none of the cells is near significance.
- Holdout: ONE logged look (DS3_TSTRUCTFIB); equal_risk/add_book was called for PASS/CANDIDATE only: none for this track.

## 3. All cells (MAPPED)
| family | cell | signal bar | parent | L | entry | stop | target | tr/wk | win obs vs req @ R (WF) | avg win/loss $ | paired vs baseline sweep pts [CI] | paired vs ST pts [CI] | PRE / WF / HOLD / 2023 $/wk | verdict | placebo PRE | DSR N-track | equal lots $/wk | equal risk $/wk (lots) | capacity lots | DS3 marginal Sharpe WFPRE/WF/HOLD | executability |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| sfib | SF_can60_tf3m_L3 | 3m | - | 3 |  | origin of leg 2 -0 | 261.8% ext | 3.08 | 0.19 vs 0.18 @ R 4.43 | 12,839 / -2,895 |  |  | -274 / 444 / 1,218 / -1,239 | DEAD (PRE>0,WF_CI>0,SPAN2>0,plc>=.95) |  | 0.16 | 500 | -848 (40.7) | 32 |  | NT8 bars |
| sfib | SF_ent618_tf3m_L3 | 3m | - | 3 |  | origin of leg 2 -0 | 261.8% ext | 2.32 LOWFREQ | 0.17 vs 0.13 @ R 6.54 | 14,202 / -2,173 |  |  | 1,607 / 1,482 / 1,325 / -209 | DEAD (tpw>=3,WF_CI>0,SPAN2>0,plc>=.95) | 0.78 | 0.52 | 1,530 | 4,206 (44.4) | 129 |  | NT8 bars |
| sfib | SF_entlad_tf3m_L3 | 3m | - | 3 |  | origin of leg 2 -0 | 261.8% ext | 2.90 LOWFREQ | 0.21 vs 0.16 @ R 5.10 | 12,972 / -2,545 |  |  | 1,035 / 1,855 / 2,720 / -218 | DEAD (tpw>=3,WF_CI>0,SPAN2>0,plc>=.95) | 0.85 | 0.62 | 1,913 | 5,092 (41.1) | 129 |  | NT8 bars |
| sfib | SF_external_tf1m_L3 | 1m | - | 3 |  | origin of leg 2 -0 | 261.8% ext | 1.37 LOWFREQ | 0.16 vs 0.15 @ R 5.71 | 10,270 / -1,799 |  |  | 131 / 150 / 169 / -42 | DEAD (tpw>=3,WF_CI>0,SPAN2>0,plc>=.95) | 0.50 | 0.14 | 189 | -4,031 (89.6) | 28 |  | NT8 bars |
| sfib | SF_external_tf3m_L3 | 3m | - | 3 |  | origin of leg 2 -0 | 261.8% ext | 0.68 LOWFREQ | 0.16 vs 0.15 @ R 5.86 | 15,874 / -2,709 |  |  | 44 / 242 / 453 / -943 | DEAD (tpw>=3,WF_CI>0,SPAN2>0,plc>=.95) | 0.50 | 0.15 | 243 | -254 (76.2) | 67 |  | NT8 bars |
| sfib | SF_g_tf15m_L12 | 15m | - | 12 |  | origin of leg 2 -0 | 261.8% ext |  | under 100 trades (0) |  |  |  |  | DEAD |  |  |  |  |  |  |  |
| sfib | SF_g_tf15m_L3 | 15m | - | 3 |  | origin of leg 2 -0 | 261.8% ext |  | under 100 trades (23) |  |  |  |  | DEAD |  |  |  |  |  |  |  |
| sfib | SF_g_tf15m_L5 | 15m | - | 5 |  | origin of leg 2 -0 | 261.8% ext |  | under 100 trades (5) |  |  |  |  | DEAD |  |  |  |  |  |  |  |
| sfib | SF_g_tf15m_L8 | 15m | - | 8 |  | origin of leg 2 -0 | 261.8% ext |  | under 100 trades (0) |  |  |  |  | DEAD |  |  |  |  |  |  |  |
| sfib | SF_g_tf1m_L12 | 1m | - | 12 |  | origin of leg 2 -0 | 261.8% ext | 1.27 LOWFREQ | 0.18 vs 0.17 @ R 4.81 | 15,063 / -3,133 |  |  | -455 / 211 / 932 / -464 | DEAD (tpw>=3,PRE>0,WF_CI>0,SPAN2>0,plc>=.95) |  | 0.13 | 250 | -855 (57.3) | 36 |  | NT8 bars |
| sfib | SF_g_tf1m_L3 | 1m | - | 3 |  | origin of leg 2 -0 | 261.8% ext | 10.17 | 0.17 vs 0.16 @ R 5.15 | 9,346 / -1,815 |  | 3.7 [-8.1,14.4] (MDE 16.3, n 93) | 670 / 1,281 / 1,928 / -3,216 | DEAD (WF_CI>0,SPAN2>0,plc>=.95) | 0.25 | 0.35 | 1,349 | -2,474 (36.4) | 28 |  | NT8 bars |
| sfib | SF_g_tf1m_L5 | 1m | - | 5 |  | origin of leg 2 -0 | 261.8% ext | 5.19 | 0.18 vs 0.17 @ R 4.78 | 9,926 / -2,076 |  | 9.2 [-5.7,24.6] (MDE 21.7, n 40) | 388 / 641 / 907 / -2,623 | DEAD (WF_CI>0,SPAN2>0,plc>=.95) | 0.40 | 0.22 | 641 | -2,826 (43.8) | 27 |  | NT8 bars |
| sfib | SF_g_tf1m_L8 | 1m | - | 8 |  | origin of leg 2 -0 | 261.8% ext | 2.59 LOWFREQ | 0.19 vs 0.18 @ R 4.43 | 11,257 / -2,539 |  |  | -936 / 377 / 1,800 / 365 | DEAD (tpw>=3,PRE>0,WF_CI>0,plc>=.95) |  | 0.16 | 422 | -1,693 (52.1) | 32 |  | NT8 bars |
| sfib | SF_g_tf3m_L12 | 3m | - | 12 |  | origin of leg 2 -0 | 261.8% ext |  | under 100 trades (26) |  |  |  |  | DEAD |  |  |  |  |  |  |  |
| sfib | SF_g_tf3m_L3 | 3m | - | 3 |  | origin of leg 2 -0 | 261.8% ext | 2.90 LOWFREQ | 0.20 vs 0.18 @ R 4.42 | 12,986 / -2,938 |  |  | 61 / 736 / 1,458 / -762 | DEAD (tpw>=3,WF_CI>0,SPAN2>0,plc>=.95) | 0.40 | 0.22 | 794 | 490 (41.1) | 50 |  | NT8 bars |
| sfib | SF_g_tf3m_L5 | 3m | - | 5 |  | origin of leg 2 -0 | 261.8% ext | 1.36 LOWFREQ | 0.21 vs 0.17 @ R 4.73 | 15,061 / -3,182 |  |  | 148 / 763 / 1,421 / 2,553 | DEAD (tpw>=3,WF_CI>0,plc>=.95) | 0.55 | 0.31 | 769 | 1,946 (55.5) | 109 |  | NT8 bars |
| sfib | SF_g_tf3m_L8 | 3m | - | 8 |  | origin of leg 2 -0 | 261.8% ext |  | under 100 trades (72) |  |  |  |  | DEAD |  |  |  |  |  |  |  |
| sfib | SF_g_tf5m_L12 | 5m | - | 12 |  | origin of leg 2 -0 | 261.8% ext |  | under 100 trades (9) |  |  |  |  | DEAD |  |  |  |  |  |  |  |
| sfib | SF_g_tf5m_L3 | 5m | - | 3 |  | origin of leg 2 -0 | 261.8% ext | 1.43 LOWFREQ | 0.20 vs 0.17 @ R 5.00 | 15,215 / -3,044 |  |  | 59 / 744 / 1,478 / 2,781 | DEAD (tpw>=3,WF_CI>0,plc>=.95) | 0.38 | 0.32 | 749 | 1,702 (57.3) | 100 |  | NT8 bars |
| sfib | SF_g_tf5m_L5 | 5m | - | 5 |  | origin of leg 2 -0 | 261.8% ext |  | under 100 trades (90) |  |  |  |  | DEAD |  |  |  |  |  |  |  |
| sfib | SF_g_tf5m_L8 | 5m | - | 8 |  | origin of leg 2 -0 | 261.8% ext |  | under 100 trades (27) |  |  |  |  | DEAD |  |  |  |  |  |  |  |
| sfib | SF_internal_tf1m_L3 | 1m | - | 3 |  | origin of leg 2 -0 | 261.8% ext | 8.96 | 0.18 vs 0.16 @ R 5.08 | 9,173 / -1,807 |  | 1.7 [-9.7,12.6] (MDE 16.3, n 90) | 461 / 1,089 / 1,756 / -3,169 | DEAD (WF_CI>0,SPAN2>0,plc>=.95) | 0.28 | 0.31 | 1,122 | -2,857 (37.8) | 27 |  | NT8 bars |
| sfib | SF_internal_tf3m_L3 | 3m | - | 3 |  | origin of leg 2 -0 | 261.8% ext | 2.24 LOWFREQ | 0.21 vs 0.20 @ R 4.10 | 12,267 / -2,991 |  |  | -36 / 456 / 984 / 160 | DEAD (tpw>=3,PRE>0,WF_CI>0,plc>=.95) |  | 0.17 | 512 | -233 (44.7) | 41 |  | NT8 bars |
| sfib | SF_ret382_tf3m_L3 | 3m | - | 3 |  | origin of leg 2 -0 | 261.8% ext | 3.25 | 0.20 vs 0.19 @ R 4.25 | 12,835 / -3,022 |  |  | 132 / 598 / 1,097 / -1,389 | DEAD (WF_CI>0,SPAN2>0,plc>=.95) | 0.25 | 0.19 | 655 | -251 (39.4) | 37 |  | NT8 bars |
| sfib | SF_ret618_tf3m_L3 | 3m | - | 3 |  | origin of leg 2 -0 | 261.8% ext | 2.43 LOWFREQ | 0.18 vs 0.18 @ R 4.64 | 13,411 / -2,892 |  |  | -805 / 279 / 1,454 / -16 | DEAD (tpw>=3,PRE>0,WF_CI>0,SPAN2>0,plc>=.95) |  | 0.14 | 314 | -1,472 (46.2) | 27 |  | NT8 bars |
| sfib | SF_sw1t1b_tf3m_L3 | 3m | - | 3 |  | origin of leg 2 -0 | 261.8% ext | 1.73 LOWFREQ | 0.17 vs 0.19 @ R 4.19 | 12,552 / -2,998 |  |  | -321 / -503 / -693 / -707 | DEAD (tpw>=3,PRE>0,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95) |  | 0.03 |  |  |  |  | NT8 bars |
| sfib | SF_sw1t3b_tf3m_L3 | 3m | - | 3 |  | origin of leg 2 -0 | 261.8% ext | 3.01 | 0.20 vs 0.18 @ R 4.44 | 12,683 / -2,856 |  |  | 314 / 540 / 779 / -1,300 | DEAD (WF_CI>0,SPAN2>0,plc>=.95) | 0.55 | 0.19 | 597 | -558 (42.5) | 37 |  | NT8 bars |
| sfib | SF_sw3t1b_tf3m_L3 | 3m | - | 3 |  | origin of leg 2 -0 | 261.8% ext | 1.55 LOWFREQ | 0.17 vs 0.19 @ R 4.18 | 13,303 / -3,179 |  |  | -584 / -534 / -471 / -330 | DEAD (tpw>=3,PRE>0,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95) |  | 0.03 |  |  |  |  | NT8 bars |
| sfib | SF_val120_tf3m_L3 | 3m | - | 3 |  | origin of leg 2 -0 | 261.8% ext | 3.06 | 0.19 vs 0.19 @ R 4.31 | 13,014 / -3,016 |  |  | -478 / -47 / 423 / -1,170 | DEAD (PRE>0,WF_CI>0,SPAN2>0,plc>=.95) |  | 0.09 |  |  |  |  | NT8 bars |
| sfib | SF_val30_tf3m_L3 | 3m | - | 3 |  | origin of leg 2 -0 | 261.8% ext | 2.44 LOWFREQ | 0.19 vs 0.19 @ R 4.36 | 12,323 / -2,824 |  |  | -718 / 311 / 1,425 / -1,471 | DEAD (tpw>=3,PRE>0,WF_CI>0,SPAN2>0,plc>=.95) |  | 0.14 | 366 | -1,238 (46.2) | 30 |  | NT8 bars |
| sfib | SF_buf5_tf1m_L3 | 1m | - | 3 |  | origin of leg 2 -5 | 261.8% ext | 11.17 | 0.26 vs 0.27 @ R 2.72 | 7,400 / -2,723 |  | 0.6 [-9.6,12.3] (MDE 16.2, n 93) | -1,054 / -1,313 / -1,575 / -4,515 | DEAD (PRE>0,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95) |  | 0.01 |  |  |  |  | NT8 bars |
| sfib | SF_buf5_tf3m_L3 | 3m | - | 3 |  | origin of leg 2 -5 | 261.8% ext | 2.90 LOWFREQ | 0.27 vs 0.25 @ R 3.00 | 11,772 / -3,918 |  |  | 228 / 1,028 / 1,882 / -923 | DEAD (tpw>=3,WF_CI>0,SPAN2>0,plc>=.95) | 0.72 | 0.28 | 1,102 | 1,899 (36.4) | 71 |  | NT8 bars |
| mirror | SF_mirror_tf1m_L3 | - | - |  |  | as base | as base | 21.00 | 0.20 vs 0.18 @ R 4.69 | 10,475 / -2,234 |  | 18.7 [10.2,27.4] (MDE 11.9, n 137) | 5,015 / 7,303 / 9,684 / -3,306 | DEAD (SPAN2>0,plc>=.95) | 0.75 | 0.97 | 7,340 | 12,062 (20.6) | 65 |  | NT8 bars |
| mirror | SF_mirror_tf3m_L3 | - | - |  |  | as base | as base | 7.35 | 0.20 vs 0.20 @ R 4.03 | 13,653 / -3,388 |  |  | -2,082 / -350 / 1,537 / -686 | DEAD (PRE>0,WF_CI>0,SPAN2>0,plc>=.95) |  | 0.07 |  |  |  |  | NT8 bars |
| sfib | SF_runner_tf1m_L3 | 1m | - | 3 |  | origin of leg 2 -0 | runner 261.8/423.6 | 8.94 | 0.18 vs 0.15 @ R 5.60 | 10,108 / -1,805 |  | 2.8 [-9.0,13.5] (MDE 16.3, n 90) | 1,479 / 2,615 / 3,811 / -2,839 | DEAD (WF_CI>0,SPAN2>0,plc>=.95) | 0.47 | 0.72 | 2,652 | 3,364 (34.9) | 54 |  | NT8 bars |
| sfib | SF_runner_tf3m_L3 | 3m | - | 3 |  | origin of leg 2 -0 | runner 261.8/423.6 | 2.24 LOWFREQ | 0.21 vs 0.19 @ R 4.34 | 12,968 / -2,991 |  |  | 37 / 784 / 1,585 / 245 | DEAD (tpw>=3,WF_CI>0,plc>=.95) | 0.38 | 0.24 | 843 | 1,280 (42.8) | 71 |  | NT8 bars |
| shift | SF_shift180_tf1m_L3 | - | - |  |  | as base | as base | 19.48 | 0.19 vs 0.17 @ R 4.77 | 9,860 / -2,066 |  | 0.7 [-6.5,8.6] (MDE 10.8, n 191) | 3,015 / 3,710 / 4,412 / -2,382 | DEAD (WF_CI>0,SPAN2>0,plc>=.95) | 0.55 | 0.65 | 3,990 | 5,093 (22.4) | 38 |  | NT8 bars |
| shift | SF_shift60_tf3m_L3 | - | - |  |  | as base | as base | 7.10 | 0.21 vs 0.19 @ R 4.33 | 14,228 / -3,284 |  | 1.5 [-9.5,12.2] (MDE 15.7, n 90) | -340 / 3,119 / 6,834 / -1,705 | DEAD (PRE>0,WF_CI>0,SPAN2>0,plc>=.95) |  | 0.57 | 3,362 | 6,226 (23.2) | 91 |  | NT8 bars |
| sfib | SF_stopf60_tf1m_L3 | 1m | - | 3 |  | fixed 60 | 261.8% ext | 9.50 | 0.55 vs 0.61 @ R 0.63 | 6,911 / -10,911 |  | 4.3 [-4.9,14.9] (MDE 14.1, n 89) | -7,582 / -10,016 / -12,517 / -9,566 | DEAD (PRE>0,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95,x2_WF>0) |  | 0.00 |  |  |  |  | NT8 bars |
| sfib | SF_stopf60_tf3m_L3 | 3m | - | 3 |  | fixed 60 | 261.8% ext | 2.77 LOWFREQ | 0.53 vs 0.49 @ R 1.03 | 10,945 / -10,584 |  |  | 2,070 / 2,156 / 2,219 / -2,836 | DEAD (tpw>=3,WF_CI>0,SPAN2>0,plc>=.95) | 0.90 | 0.43 | 2,329 | 5,176 (26.0) | 166 |  | NT8 bars |
| sfib | SF_tp1618_tf1m_L3 | 1m | - | 3 |  | origin of leg 2 -0 | 161.8% ext | 10.40 | 0.28 vs 0.28 @ R 2.57 | 4,691 / -1,822 |  | 3.5 [-9.1,14.6] (MDE 16.9, n 93) | -1,035 / 93 / 1,317 / -2,147 | DEAD (PRE>0,WF_CI>0,SPAN2>0,plc>=.95) |  | 0.11 | 101 | -12,278 (46.8) | 15 |  | NT8 bars |
| sfib | SF_tp1618_tf3m_L3 | 3m | - | 3 |  | origin of leg 2 -0 | 161.8% ext | 2.92 LOWFREQ | 0.28 vs 0.30 @ R 2.39 | 7,182 / -3,006 |  |  | -161 / -309 / -464 / -1,605 | DEAD (tpw>=3,PRE>0,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95) |  | 0.05 |  |  |  |  | NT8 bars |
| sfib | SF_tp200_tf1m_L3 | 1m | - | 3 |  | origin of leg 2 -0 | 200.0% ext | 10.29 | 0.22 vs 0.22 @ R 3.62 | 6,597 / -1,821 |  | 2.7 [-9.6,13.4] (MDE 16.1, n 93) | -1,136 / 449 / 2,165 / -4,151 | DEAD (PRE>0,WF_CI>0,SPAN2>0,plc>=.95) |  | 0.17 | 539 | -8,161 (42.3) | 19 |  | NT8 bars |
| sfib | SF_tp200_tf3m_L3 | 3m | - | 3 |  | origin of leg 2 -0 | 200.0% ext | 2.91 LOWFREQ | 0.22 vs 0.23 @ R 3.35 | 9,940 / -2,964 |  |  | -353 / -231 / -95 / -1,469 | DEAD (tpw>=3,PRE>0,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95) |  | 0.06 |  |  |  |  | NT8 bars |
| sfib | SF_xex0_tf1m_L3 | 1m | - | 3 |  | origin of leg 2 -0 | 261.8% ext | 3.63 | 0.19 vs 0.17 @ R 5.05 | 9,557 / -1,892 |  | 0.5 [-18.3,19.8] (MDE 26.9, n 31) | 406 / 980 / 1,590 / -643 | DEAD (WF_CI>0,SPAN2>0,plc>=.95) | 0.28 | 0.41 | 1,077 | -172 (55.9) | 55 |  | NT8 bars |
| sfib | SF_xex0_tf3m_L3 | 3m | - | 3 |  | origin of leg 2 -0 | 261.8% ext | 1.41 LOWFREQ | 0.20 vs 0.19 @ R 4.30 | 13,519 / -3,147 |  |  | 589 / 333 / 49 / -722 | DEAD (tpw>=3,WF_CI>0,SPAN2>0,plc>=.95) | 0.65 | 0.18 | 368 | -867 (65.6) | 47 |  | NT8 bars |

## 4. Generic market-structure controls (TREND PRO R1, existing TR1E rows, not re-run)
| cell | verdict | tr/wk | PRE $/wk | WF $/wk | HOLD $/wk | note |
|--|--|--|--|--|--|--|
| TR1E_bos_1m_c2 | DEAD | 30.38 | 7,391 | 5,383 | 3,124 | existing TR1E score (duplicate, not re-run) |
| TR1E_retest_1m_c2 | DEAD | 26.54 | -2,412 | -1,188 | 160 | existing TR1E score (duplicate, not re-run) |
| TR1E_choch_1m_c2 | DEAD | 28.64 | -2,350 | -8,127 | -14,289 | existing TR1E score (duplicate, not re-run) |
| TR1E_bos_1m_c3 | DEAD | 28.52 | 10,277 | 4,399 | -2,055 | existing TR1E score (duplicate, not re-run) |
| TR1E_retest_1m_c3 | DEAD | 24.15 | -3,288 | -904 | 1,699 | existing TR1E score (duplicate, not re-run) |
| TR1E_choch_1m_c3 | DEAD | 27.84 | -1,982 | -6,769 | -11,875 | existing TR1E score (duplicate, not re-run) |
| TR1E_bos_3m_c2 | DEAD | 23.37 | 687 | 9,005 | 17,915 | existing TR1E score (duplicate, not re-run) |
| TR1E_retest_3m_c2 | DEAD | 17.14 | -2,600 | 3,382 | 9,835 | existing TR1E score (duplicate, not re-run) |
| TR1E_choch_3m_c2 | DEAD | 22.23 | -1,846 | -2,868 | -3,937 | existing TR1E score (duplicate, not re-run) |
| TR1E_bos_3m_c3 | DEAD | 21.76 | -2,362 | 6,543 | 16,129 | existing TR1E score (duplicate, not re-run) |
| TR1E_retest_3m_c3 | DEAD | 14.27 | -10,012 | -4,591 | 1,368 | existing TR1E score (duplicate, not re-run) |
| TR1E_choch_3m_c3 | DEAD | 20.17 | 1,402 | 701 | -70 | existing TR1E score (duplicate, not re-run) |
| TR1E_bos_5m_c2 | DEAD | 20.17 | -3,627 | 991 | 5,995 | existing TR1E score (duplicate, not re-run) |
| TR1E_retest_5m_c2 | DEAD | 11.57 | -457 | -813 | -1,189 | existing TR1E score (duplicate, not re-run) |
| TR1E_choch_5m_c2 | DEAD | 18.41 | -812 | -1,591 | -2,414 | existing TR1E score (duplicate, not re-run) |
| TR1E_bos_5m_c3 | DEAD | 18.13 | -2,888 | -2,621 | -2,293 | existing TR1E score (duplicate, not re-run) |
| TR1E_retest_5m_c3 | DEAD | 9.77 | 1,458 | 889 | 258 | existing TR1E score (duplicate, not re-run) |
| TR1E_choch_5m_c3 | DEAD | 16.20 | -2,782 | -219 | 2,569 | existing TR1E score (duplicate, not re-run) |
| TR1E_bos_15m_c2 | DEAD | 10.86 | 5,747 | 4,161 | 2,377 | existing TR1E score (duplicate, not re-run) |
| TR1E_retest_15m_c2 | DEAD | 4.45 | 3,910 | 2,310 | 537 | existing TR1E score (duplicate, not re-run) |
| TR1E_choch_15m_c2 | DEAD | 9.48 | 1,348 | -5,046 | -11,923 | existing TR1E score (duplicate, not re-run) |
| TR1E_bos_15m_c3 | DEAD | 8.82 | 2,427 | 2,686 | 2,928 | existing TR1E score (duplicate, not re-run) |
| TR1E_retest_15m_c3 | CANDIDATE | 3.31 | 2,279 | 1,595 | 828 | existing TR1E score (duplicate, not re-run) |
| TR1E_choch_15m_c3 | DEAD | 7.67 | 964 | -2,846 | -6,946 | existing TR1E score (duplicate, not re-run) |

