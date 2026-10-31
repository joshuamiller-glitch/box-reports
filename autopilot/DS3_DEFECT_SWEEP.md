# DS3_DEFECT_SWEEP - DS-1: which closed DEAD / LEAD / CANDIDATE verdicts are exposed to the week's defect classes (2026-10-31)

Read-only classification of the 646 DS3_*.md reports (411 result reports, 235 PREHOLD texts that contain PRE only) from report text, code greps under l2vast/ds3/code, and the audit files (MASKAUDIT, LEAKAUDIT, VOLFIX, PAIRFIX, UNIT_AUDIT, SUNDAY_BRIEF_AUDIT, L2_UNTIL_FOUND, KB_REGIME, STACK_E_CORRECTED). Re-reads of stored series only (no simulation of new strategies); masks capped 20260206; UNTOUCHED never read. Scratch code/outputs: l2vast/ds3/out/ds1_sweep/ (pool.py, series_cap.csv, ua_causal.py, fzrerun.py). Two re-runs of existing engines were done (UA-1 vol rows with the causal tag; FZ-1 size rules through the engine multiplier), both minutes.

## PAGE 1

### A. Counts per defect class (reports touched / verdicts that rest on it)
| # | class | reports exposed | verdict could change | status |
|---|---|---|---|---|
| 1 | look-ahead vol tag (vol_tag_entry_day) | 15 (ADAPTIVE_EXP1, L2SET_PROFIT, L2SET_LOSS s7, THP_C1_GBM, THP_C3_ONLINE, SIZING_REGIME A-cells, UF-LOSS C3 v0, DIV2_A_AUDIT/ABR cpi-nfp proxies, ENSEMBLE (3 EXP1 rows), STACK_2, UNIT_AUDIT (2 rows), STACK_PARTIALS/SUNDAY_STACK quant columns, RE-2 monitors) | 1 already corrected (EXP1 profit 3 CANDIDATE -> 0, VOLFIX); 2 live-adjacent rows re-run here (below) | THP_POLICY.txt has no vol token (checked) |
| 2 | unbounded WINMASK/WINS (HOLD 68 wk, WF 142 wk, L8W 100% post-cut) | ~127 DS3 reports + the whole struct48/pair/pred program (MASKAUDIT 4a-4d); the 141 PREHOLD texts are PRE-only (fine) | yes, both directions (section C) | capped reruns not run |
| 3 | per-contract-of-final-lots as sole unit | ~30 (CONFIRM_1_A/1_B/1_ENG, CONFIRM_2, CONFIRM_BARS, CONFIRM_SUBMIN, CONFIRM_COMBOS(_FINAL), FAVORABLE_*, NO_TRADE_*, BARS_*, DECAY_*, L2_UF_ENTRY C4-C6, L2_INFO, TREND_*) | no flip found: every one that claims a lead restates it per planned lot / on the stack and the lead dies there (CF-B OTE, FZ-1); the unit inflates skip/gate rules, so DEADs are robust | CF-COMBO 7 bars leads and CONFIRM_BARS 7 LEADs were not unit-checked (MORNING 605) |
| 4 | paired conditioned on days both traded | wave-1/2 bar tables (BARS_ALL_CANDIDATES, BARS_2, BARS_ALL_ENGINES/BARENG/BARCAND2), ZEN_BARS, SDISC_6B (~8 reports; 48 rows re-read by PAIRFIX) | 10 of 45 rows demoted; paired gains inflated | DEAD rows in these tables not re-read (see re-runs) |
| 5 | duplicated BAR-STORE candles (ha 1m-15m, linreg, hull, momcol, kaseproxy, lb) | CONFIRM_BARS S1/S2 (rescored S1c/S2c: handled), RC-1 (blocked, handled), BARS_ALL_CANDIDATES wave 1: 9 PAIRFIX rows on ha/3m and ha/5m (L02766, L01678, L01654, L01427, L01501, L01537, L01629) built before the 19:14Z fix and NOT re-scored; BAR-ENG uses barlib, not the store (be_lib) so its HA rows are not exposed by this path | direction unknown (wrong recursion + 2-3x rows); all 9 are LEAD with HOLD CI including 0 or already DEAD | rescore needed (cheap) |
| 6 | shuffle_src monotone ro_start | 1 (L2SET_PROFIT G8 placebo ranks: void; l2set_profit/lp_data.py:14 and lp_sweep still carry it; uf_p1_common fixed; l2h/h_score maps rows by tid: fine) | no: TASK A redo; thick-book null stands on N/LIVE levels. Defect DEFLATED the verdict (ranks 0.00) | done |
| 7 | stack_parts WDAY in-place mutation | 1 (STACK_E; STACK_F/FINAL flag it) | yes, deflating: HM3te DEAD -> LEAD, HM5te DEAD -> CANDIDATE (STACK_E_CORRECTED) | done on disk, E text not edited |
| 8 | planned-lot vs sized-lot governors, day-static locks | 8 (SUNDAY_STACK/_2, TREND_2, KB_REGIME, ESLEAD, UNIT_AUDIT, SUNDAY_BRIEF, RISK_OFF/HALT_RESUME/QUIT_WHEN_UP lead-written) | yes: every sizer (ER20 L6M +8.5k planned vs +37.3k sized; PRE -9.2k vs +11.2k) | spec for D6 stated in brief |
| 9 | lock-engine re-entry as same-trade gain | ~15 (STACK_2, STACK_PARTIALS, SPLIT_2, UNIT_AUDIT, ZONES_2/addendum, CUTWAIT, DECAY_*, SUNDAY_*) | gains survive but their dollars are 47-95% re-entry (Asia cut 71%, 8-line skip 85%, KB sizer 88%) | stated on brief page 1 |
| 10 | book-lean direction/sign | 1 (KB_REGIME). Code check: e_feat.py, DS3_L2_FEATURE_DEFS and ls_* sign by side everywhere (+ = supports the trade); the error was only the directive's wording. N1 cell e "OUR-way" lead was a post-hoc polarity flip (best-of-F) | no code change; sign-conditioned lead remains post-hoc | NOT-EXPOSED in code |
| 11 | size rule scored by scaling the pts column (NTE-1 METHOD WARNING) | NO_TRADE_ZONES, NO_TRADE_FINAL (u150/z50/z67 rows via poi_look.rule_o, poi_detail, poi_lookm), FAVORABLE_ZONES/FINAL (fz_stack_more B2 schemes + score sizers, fz_B6_eval), ZONES_2 original table (zl.simulate z50/u150; the ADDENDUM re-ran half size through the engine and found <1k difference), ENSEMBLE (mult rules enter as (m-1)*bb pts), STACK_E MIX legs (scaled daily series). Engine-based (not exposed): TG-1 (tg_stack mult), ES-lead (sz_engine), N1, KBR (kbr_stack), EINT1/EINT2, EQR, STACK_A/C (run_book size), SS-2, UA-1 | see section D | FZ-1 re-run done here |

### B. Rows that could change the Sunday brief (DS3_SUNDAY_BRIEF.md v3)
| brief row | defect exposure | classification | direction / note |
|---|---|---|---|
| A. composite headline +18.5k L6M | classes 8, 9 | EXPOSED-VERDICT-ROBUST for the running-max reading; EXPOSED-COULD-CHANGE if D6 uses planned-lot or base-lot locks (+9.8k / opener-fixed +4.6k) | already hazard 3 on page 1. Pieces are engine-based (class 11 clear) |
| ON 70/30 split dip 3 | 9 (47% gross / 55% net re-entry), 3 not applicable (stack $), 2 clear (SPLIT_2, L2SE capped), 1 clear, 10 clear (veto_imb5 sign is by side) | NOT-EXPOSED to code defects; EXPOSED-VERDICT-ROBUST to re-entry (positive in every convention cell) | live-lot dollars 5.4k vs 7.5k is a unit issue already fixed in v3 |
| K6 add keep/drop | 3 (C9 K6 alone, research lots) | EXPOSED-VERDICT-ROBUST (both inside MDE; coin flip) | none |
| SHADOW ER(20) 5-m sizer | 8, 9 (200% gross), 11 clear (SS-2/UA-1/TG-1 engine mult), shuffled-ER placebo earns +54k so the sizer is mostly lot dispersion (C8) | EXPOSED-VERDICT-COULD-CHANGE | governor can move it either way (-9.2k to +37k); not a code defect |
| SHADOW KB ER>=0.2 sizer | 8 (planned +3.1k vs sized +8.1k), 10 (book-lean skip sign in same report) | EXPOSED-COULD-CHANGE (governor) | upward if D6 uses sized-lot R |
| SHADOW PE 45-s three-bar | 3 (per planned lot reported), 9 (58% gross, 105% net), tc 45-s is a time bar (not in the dup-bar set) | EXPOSED-VERDICT-ROBUST (inside MDE either way) | none |
| SHADOW 8-line zone skip | 9 (85%), selection (lines post-hoc), engine difference +28.3k vs +15.4k (UA-1 point 10) | EXPOSED-VERDICT-COULD-CHANGE | downward (live +6.6k on the addendum engine, +3.9k on UA-1 live engine) |
| SHADOW Asia-stopped cut50 | 9 (71%), NOT vol keyed (class 1 clear) | EXPOSED-VERDICT-ROBUST | pooled version flips sign; Asia version positive in all grid cells |
| SHADOW second-signal skip, HM FVG skip, ES-lead sizers | 9, 8, 11 clear (engine) | EXPOSED-ROBUST (already weak / OFF) | none |
| Stop-join Native | units (research vs live lots) | fixed in v3 (+1.5k live) | none |
| vol-tercile cut rows in UA-1 (not on the brief) | class 1 | EXPOSED-COULD-CHANGE, re-run here (section E1) | recent windows go UP, selection windows go DOWN with the causal tag |
| OFF list: bar types, L2 profit/loss/entry info, POI/zones, brackets, risk-off etc. | 4, 5 (HA rows), 2 (TH_G1-3, TH_LOSS, TPBX etc. uncapped but all negative-signed), 6 | EXPOSED-VERDICT-ROBUST: the defects inflate or add noise; no OFF row's negative sign depends on them. Deflating exceptions are listed in D | none change an OFF |
| Page-1 hazard 1 (persistence 41%) | 1, 5, 4 in the ledger inputs | EXPOSED-ROBUST: look-ahead and paired inflation make edges look MORE persistent, so the null is conservative | none |

### C. Class 2 re-read (window cap), from stored series
* Library pool (31,098 streams, daily_pool_live, exact reproduction of l_HOLD_mean/l_WF_mean to 0.0): re-tiering with HOLD capped 2025-07-01..2026-02-06 (32 wk vs 69) and WF capped (106 vs 143):
  * F-HOLD (holdout <= 0): 19,760 streams; 3,439 (17%) have a POSITIVE capped HOLD mean (the post-cutoff weeks were negative for them: the defect DEFLATED them); 25 reach capped HOLD t>=2; 107 would pass T1-like (X, PRE, capped HOLD > 0, capped WF t>=2).
  * T1 (1,022) -> 591 keep capped WF t>=2; 20 lose HOLD sign; T2 (3,022): 613 lose HOLD sign. All three PRE+X+HOLD+WF-t>=2 survivors 1,030 -> 855.
  * Net: the cap removes more PASS/CANDIDATE rows than it adds, but the DEAD column is not clean: ~3.4k F-HOLD streams flip sign.
* DS3 stored daily series of PASS/CANDIDATE cells (SERIES/, 154 series, same machinery): HOLD>0 147 -> 137; HOLD t>=2 66 -> 46 (33 lose it, 13 gain it); WF t>=2 103 -> 75; 12 HOLD sign flips, 4 WF flips.
  * by program: PRO1 (22): HOLD t>=2 13 -> 7, WF t>=2 16 -> 2; PRO2 (24): 15 -> 10, WF 19 -> 8; TA1 (7): 4 -> 1; TCHOP (13): 5 -> 2; TICT (9): 7 -> 4; TSBS (12): 7 -> 5, HOLD>0 12 -> 8; XT replay variants (14): median WF +4.4k -> -0.1k/wk. Opposite direction: **T-OPEN (20 DR series): HOLD t>=2 1 -> 8, median HOLD +4.0k -> +7.5k/wk** (the uncapped window understated the DR5m cluster; its program-level best-of-N failure is unchanged).
* Live DS2 books (pool rows D000-D009, WF/HOLD $/wk uncapped -> capped): ST10 14.2k/16.2k -> 15.1k/21.3k; HM10 10.0k/10.4k -> 9.3k/8.8k (HOLD t 1.5 -> 0.9); WT7 1.4k/0.8k -> 2.4k/3.2k. The 36 post-cutoff weeks averaged about +11.9k/wk for ST10 and HM10 (pool-implied), about +43.5k/wk for the stack (MASKAUDIT).
* So class 2 is two-directional: PASS/CANDIDATE rows resting on the HOLD CI or the WF CI lose strength (PRO1/PRO2/TA1/TCHOP/XT, struct48 leaderboard rows); DEAD rows decided by a negative HOLD mean on the uncapped window (about 17% of the pool's F-HOLD) and the T-OPEN family are understated.

### D. Negative verdicts that a defect made too pessimistic (deflating list)
1. Uncapped HOLD/WF: 3,439 pool streams (F-HOLD) positive when capped; T-OPEN DR series; WT7 book; none reaches significance after the cap except 25 streams (t>=2), 107 T1-like.
2. stack_parts: STACK_E HM3te, HM5te (DEAD -> LEAD / CANDIDATE, corrected file exists).
3. L2SP placebo (class 6): G8 ranks 0.00 were an artefact; corrected PRE ranks 0.12-1.00.
4. Pts-scaled SIZE rules (class 11), FZ-1 re-run here (E2): half-size and score-sizer lines are too low on the pts route: M0 half_clip02 L6M -4.8k -> +2.4k, HOLD -2.7k -> +3.9k; S73 half_clip02 L6M -2.1k -> +3.2k; W0 half_clip02 -17.3k -> -6.7k. The FZ-1 selected 36 size schemes stay negative on average (-24k -> -17k L6M) with 4-7 individual sign flips. Verdict "no favourable-zone rule above floor" stands; the PE score sizer / half sizers move from negative to small positive (inside MDE, placebo not re-run).
5. Planned-lot R governor: ER20 sizer PRE -9.2k planned vs +11.2k sized; ES N1 sizer reverses the other way (+7.4k planned, -1.1k sized).
6. Directive sign (class 10): the AGAINST book-lean skip was DEAD only because the directive had the polarity backwards; the OUR-way version is a post-hoc best-of-F lead (stack -1.7k).
7. BAR-STORE dup bug: S1/S2 old scores void (rescored S1c/S2c; no PASS). Wave-1 ha rows not rescored.
Inflating defects (the usual direction): class 1 EXP1 (+0.64 PRE -> -0.28), class 4 paired (TB4W 10m +13.4 -> +3.5), unbounded masks on PRO1/PRO2/XT, pts-scaled size-UP rows (NTE-1: uniform x2 pts-scaled L6M +29.9k vs engine -9.8k).

### E. Re-reads done in this sweep
E1. UA-1 vol-keyed cut rows re-run with the causal sidecar tag (S73 ref, N basis, planned lots, $k/wk; 27% of trades change tag): 
| row | lots | L6M orig -> causal (MDE) | HOLD | PRE | X' |
|---|---|---|---|---|---|
| first-stop cut50, entry-day vol tercile 2 | research | +3.5 -> +6.5 (23.6) | +3.5 -> +6.6 | -0.4 -> -5.3 | +3.5 -> -2.3 |
| same | live | +5.4 -> +5.7 (14.4) | +4.9 -> +5.3 | -1.5 -> -2.9 | +2.6 -> -0.6 |
| cut50, Asia & vol tercile 2 | research | +6.8 -> +10.0 (21.4) | +6.5 -> +8.7 | +4.5 -> +1.6 | +4.7 -> +1.4 |
| same | live | +7.7 -> +7.9 (14.1) | +7.2 -> +6.9 | -0.3 -> -1.0 | +3.1 -> +0.2 |
Reading: the leak inflated the selection windows (PRE, X') and slightly deflated the recent ones; with the causal tag the vol-tercile cut is recent-only (negative in PRE and X'), and Asia&vol keeps a positive sign everywhere but is no longer better than plain Asia cut50 (+13.2k L6M). Neither is on the brief. Tier: stays LEAD/CANDIDATE-RECENT inside MDE; the "positive in all five windows" claim for Asia&vol drops to two windows by size.
E2. FZ-1 size rules, pts route vs engine route (cf_engine stack_line vs de_engine.run_rows with mult), 3 bases, 14 cases: see D4. Code l2vast/ds3/out/ds1_sweep/fzrerun.py.
E3. Pool and SERIES cap re-tiering: section C (pool.py, series_cap.csv).

## RE-RUNS RECOMMENDED (cost)
1. MASKFIX + capped rerun of the uncapped SPEC/STACK_D/VOLGATE/PORTFOLIO_SOLVE/CONFIRM_B/LEADERBOARD rows (MASKAUDIT s5). Cost: patch minutes; stored-series programs (SERIES 154, pool 31k) done here in seconds; engine reruns hours. Priority: PRO1/PRO2/TA1/TCHOP/TICT/TSBS/XT PASS/CANDIDATE rows (HOLD t>=2 count falls 66 -> 46), HM10 HOLD CI, LEADERBOARD 18 PASS + 29 CANDIDATE.
2. NTZ-1 / ZONES-2 size-up rows (u150, up multipliers in NO_TRADE_ZONES, NO_TRADE_FINAL, HM/KB/MV/SM "size 150%" CANDIDATE-RECENT/LEAD rows): NTE-1 is re-running with the mult route; mark the NTZ-1 size-UP stack lines as inflated until then. Cost: ~3 min per base via fzrerun.py pattern (same code path as FZ).
3. Wave-1 PAIRFIX rows on ha/3m, ha/5m (9 rows) re-score on the rebuilt store (BARS-CAND-3 does it for new cells): ~1 h, 2 workers.
4. PAIRFIX extension to DEAD rows of the paired tables (conditioning can bias them either way): needs the per-day series of the DEAD cells; ~1-2 h; low priority.
5. ENSEMBLE: flag the 3 EXP1 rows VOID (weights ~0, no effect on headline); its mult rules enter as pts; re-run on the engine mult route only if ENSEMBLE is revived.
6. UA-1 / STACK_2 other vol-conditioned cells (c2='vol' in stack2/s2_stageA.py): same causal swap as E1, ~2 min per group.
7. CF-COMBO and CONFIRM_BARS "7 LEADs": the per-planned-lot / stack unit check still pending (MORNING 605); expected to kill them as it did CF-B OTE.
8. l2set_profit/lp_data.shuffle_src: replace with uf_p1_common.trade_of_row version so nobody reuses it.
