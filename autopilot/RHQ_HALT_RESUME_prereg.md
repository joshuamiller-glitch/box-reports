# RHQ HALT-RESUME - prereg (2026-10-31)

HALT-RESUME = the engine's per-book day entry test (-2R / +5R realised), day give-back arm (2R keep 50%) and week floor (12R) halt trading for the rest of the day / week; the cells test RESUME rules (next session; T minutes; next day; Thursday; virtual-equity conditions with the shadow P&L of the halted signals) at size rf 0.5 or 1.

Mechanism: a halt discards the signals after the lock; if halts are mostly noise-triggered (day-type mean reversion of the lock state) later sessions are still positive expectancy and a half-size resume recovers part. Predicted sign if real: positive delta in PRE and X' with the lot-factor-matched line also positive; null otherwise.

Common frame (all three programs, one prereg each; this file is sha256-hashed into DECISIONS.md BEFORE any cell is scored; hash line carries this file's sha):
* INTERPRETATION IS THE LEAD'S, not the user's: the user's original texts for RISK-OFF / HALT-RESUME / QUIT-WHEN-UP never reached the lead. To be superseded if the user re-pastes them; each report says so on page 1.
* Base = the stack as it is: 70/30 split (S73) on the exact per-book lock engine (day entry test +5R/-2R, day arm 2R keep 50%, week floor 12R, R = planned lots x 60 x $20), six engine books ST HM WT KB SM PE, N basis (no target-fill correction; M and LIVE-CAL beside for the selected cells), research lots ST10 HM10 WT7 KB5.2 SM7.4 PE5.6, and the same $ at LIVE lots (U6=ST 4 Asia/London, H6=HM 4 Asia/2 NY-AM, K6=KB 2, M6=SM 2 London/NY-AM, P6=PE 7 Asia/London/NY-AM, WT not live = research/2.35 = 3; 'pre' counted with NY-AM, 'close' with NY-PM; per-row live/research scaling of the research-lot outcome, locks evaluated at research lots).
* Governors stay in PLANNED-lot R (the sl_lib convention). The sized-lot variant (thresholds x the largest multiplier of the day/week) equals the planned-lot one for any rule that only sizes DOWN (the largest multiplier is 1); cells with explicit sized_gov=True are listed where relevant (HALT-RESUME).
* Windows: L3M 20251106..20260206 (view), L6M 20250801.., HOLD 20250701.., PRE 20240201..20250630, X' 20230401..20240131, all capped 20260206; UNTOUCHED never read.
* SELECTION on PRE and X' ONLY: a cell is carried if its excess over the lot-factor-matched uniform scaling line is >= 0 in BOTH PRE and X' AND its equal-risk delta (lot factor c solving worst-20-weeks over PRE u X' equal to the stack's) is >= 0 in BOTH; carried cells are ranked by the sum of the PRE and X' equal-risk deltas and the top 8 (all if fewer) plus the cells marked CANON below get the ONE recent look (L3M/L6M/HOLD; M and LIVE bases, placebos, QUANT columns). Cells not carried show PRE and X' only. The selection list is hashed and logged before the recent columns are opened.
* Reported per window (recent-first L3M, L6M, HOLD, PRE, X'): stack weekly mean / SD / maxDD / worst-20-weeks (sum of the 20 worst weeks) rule vs the stack as it is, paired delta with MDE (2.8 x SE), lot factor, uniform-scaling line, excess, equal-risk delta, trades/week, $/wk at research and LIVE lots, re-entry decomposition (same trades / admitted only in the rule world / dropped), P&L of the flagged (reduced or resumed) trades at full size.
* Equal-risk frame = STRUCTURE label: a rule that merely lowers risk is not edge; the lot-factor-matched uniform scaling line (lambda x the stack, lambda = rule lots / base lots on the window) is shown for every row.
* Placebos (selected cells): 100 random rules at the same fire rate (same count of flagged trades per book x session stratum, same factor values); rank of the real excess among draws. HALT-RESUME: random-resume-timing placebo (30 seeds).
* QUANT columns via qv: White RC and Romano-Wolf over the program's cells (daily deltas, 5-day blocks) on the selection frame (PRE u X') and on all weeks, DSR with the program's cell count and the cumulative count, PBO (CSCV), block-bootstrap CI of the weekly delta, Newey-West t, longest losing run, top-5% share, stack correlation, marginal worst-20.
* Tiers: LEAD = excess >= 0 and delta >= 0 in L3M/L6M/HOLD/PRE/X' but fails RC/RW/DSR; CANDIDATE-RECENT = LEAD with placebo rank >= 0.90; PASS needs RC/RW/DSR and independent forward evidence; else DEAD / STRUCTURE (a gain explained by the uniform line). Gates never softened.
* Multiplicity = the cell count stated below (plus every variant added later, logged as an addendum). dead_lookup before scoring, append_cells after; UF_TRIALS side=rhq_<program>.

Cell count: 27 (including the identity control and, for HALT-RESUME, 2 placebo kinds).

## Cell list (name | mode/spec | CANON = named a priori for the recent look)
* HR_ctrl_identity | engine | spec_diff={} | measure=res |  | no resume: the stack as it is
* HR_dayL_sess_rf0.5 | engine | spec_diff={'res_day': {'kind': 'session', 'rf': 0.5, 'types': 'L'}} | measure=res |  | day -2R entry-test halt, resume: L_sess_rf0.5
* HR_dayL_sess_rf1 | engine | spec_diff={'res_day': {'kind': 'session', 'rf': 1.0, 'types': 'L'}} | measure=res |  | day -2R entry-test halt, resume: L_sess_rf1
* HR_dayL_min60_rf0.5 | engine | spec_diff={'res_day': {'kind': 'min', 'T': 60, 'rf': 0.5, 'types': 'L'}} | measure=res |  | day -2R entry-test halt, resume: L_min60_rf0.5
* HR_dayL_min120_rf0.5 | engine | spec_diff={'res_day': {'kind': 'min', 'T': 120, 'rf': 0.5, 'types': 'L'}} | measure=res |  | day -2R entry-test halt, resume: L_min120_rf0.5
* HR_dayL_virt1R_rf0.5 | engine | spec_diff={'res_day': {'kind': 'virt', 'vthr': 1.0, 'rf': 0.5, 'types': 'L'}} | measure=res |  | day -2R entry-test halt, resume: L_virt1R_rf0.5
* HR_dayL_sess_rf0.5_x2 | engine | spec_diff={'res_day': {'kind': 'session', 'rf': 0.5, 'types': 'L', 'nres': 2}} | measure=res |  | day -2R entry-test halt, resume: L_sess_rf0.5_x2
* HR_dayW_sess_rf0.5 | engine | spec_diff={'res_day': {'kind': 'session', 'rf': 0.5, 'types': 'W'}} | measure=res |  | day +5R entry-test halt, resume: W_sess_rf0.5
* HR_dayW_sess_rf1 | engine | spec_diff={'res_day': {'kind': 'session', 'rf': 1.0, 'types': 'W'}} | measure=res |  | day +5R entry-test halt, resume: W_sess_rf1
* HR_armA_sess_rf0.5 | engine | spec_diff={'res_arm': {'kind': 'session', 'rf': 0.5}} | measure=res |  | day give-back arm halt, resume: A_sess_rf0.5
* HR_armA_sess_rf1 | engine | spec_diff={'res_arm': {'kind': 'session', 'rf': 1.0}} | measure=res |  | day give-back arm halt, resume: A_sess_rf1
* HR_armA_min60_rf0.5 | engine | spec_diff={'res_arm': {'kind': 'min', 'T': 60, 'rf': 0.5}} | measure=res |  | day give-back arm halt, resume: A_min60_rf0.5
* HR_armA_virtarm_rf0.5 | engine | spec_diff={'res_arm': {'kind': 'virt', 'vmode': 'arm', 'vthr': 0, 'rf': 0.5}} | measure=res |  | day give-back arm halt, resume: A_virtarm_rf0.5
* HR_armA_virtarm_rf1 | engine | spec_diff={'res_arm': {'kind': 'virt', 'vmode': 'arm', 'vthr': 0, 'rf': 1.0}} | measure=res |  | day give-back arm halt, resume: A_virtarm_rf1
* HR_wkF_sess_rf0.5 | engine | spec_diff={'res_wk': {'kind': 'session', 'rf': 0.5}} | measure=res |  | week floor halt, resume: F_sess_rf0.5
* HR_wkF_day_rf0.5 | engine | spec_diff={'res_wk': {'kind': 'day', 'rf': 0.5}} | measure=res |  | week floor halt, resume: F_day_rf0.5
* HR_wkF_thu_rf0.5 | engine | spec_diff={'res_wk': {'kind': 'thu', 'rf': 0.5}} | measure=res |  | week floor halt, resume: F_thu_rf0.5
* HR_wkF_thu_rf1 | engine | spec_diff={'res_wk': {'kind': 'thu', 'rf': 1.0}} | measure=res |  | week floor halt, resume: F_thu_rf1
* HR_wkF_virt4R_rf0.5 | engine | spec_diff={'res_wk': {'kind': 'virt', 'vthr': 4.0, 'rf': 0.5}} | measure=res |  | week floor halt, resume: F_virt4R_rf0.5
* HR_wkF_thuvirt4R_rf0.5 | engine | spec_diff={'res_wk': {'kind': 'thuvirt', 'vthr': 4.0, 'rf': 0.5}} | measure=res | CANON | week floor halt, resume: F_thuvirt4R_rf0.5
* HR_wkF_virt8R_rf0.5 | engine | spec_diff={'res_wk': {'kind': 'virt', 'vthr': 8.0, 'rf': 0.5}} | measure=res |  | week floor halt, resume: F_virt8R_rf0.5
* HR_wkF_virt0R_rf0.5 | engine | spec_diff={'res_wk': {'kind': 'virt', 'vthr': 0.0, 'rf': 0.5}} | measure=res |  | week floor halt, resume: F_virt0R_rf0.5
* HR_all_sess_rf0.5 | engine | spec_diff={'res_day': {'kind': 'session', 'rf': 0.5}, 'res_arm': {'kind': 'session', 'rf': 0.5}, 'res_wk': {'kind': 'session', 'rf': 0.5}} | measure=res | CANON | every halt resumes at the next session at half size
* HR_all_sess_rf0.5_sizedgov | engine | spec_diff={'sized_gov': True, 'res_day': {'kind': 'session', 'rf': 0.5}, 'res_arm': {'kind': 'session', 'rf': 0.5}, 'res_wk': {'kind': 'session', 'rf': 0.5}} | measure=res |  | same, governors scaled by the resume factor in the resumed segment (sized-lot R variant)
* HR_dayL_sess_rf0.5_sizedgov | engine | spec_diff={'sized_gov': True, 'res_day': {'kind': 'session', 'rf': 0.5, 'types': 'L'}} | measure=res |  | day -2R halt resume next session half, sized-lot governors
* HR_plc_dayL_rand_rf0.5 | engine | spec_diff={'res_day': {'kind': 'rand', 'rf': 0.5, 'types': 'L', 'prand': 0.3}} | measure=res |  | PLACEBO: day -2R halt resume at a random later row (p=.3 per row), rf .5
* HR_plc_wk_rand_rf0.5 | engine | spec_diff={'res_wk': {'kind': 'rand', 'rf': 0.5}} | measure=res |  | PLACEBO: week floor halt resume at a random later row, rf .5
