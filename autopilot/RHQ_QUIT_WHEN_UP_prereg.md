# RHQ QUIT-WHEN-UP - prereg (2026-10-31)

QUIT-WHEN-UP = stop (or halve) after the day / session / week is up X R or $Y: book-level engine variants (day +1,2,3,4,6R entry test vs the base +5R, skip or halve; arm 1.5/3/4R, keep .25/.75, arm OFF, 'continue at 50% after the arm' vs the base 'arm 2R keep 50%'), and stack-level quits in R (12,000 per R, research lots) and in $ at LIVE lots (1k/2k/4k/6k), day / session / week, quit (m=0) or halve (m=0.5).

Mechanism: locking a good day protects against give-back; costs the continuation. Winners trend (the stack's L6M gain is trend-day driven), so we predict quits LOSE mean and only reduce SD proportionally (STRUCTURE); a variant that improves equal-risk P&L would be the finding.

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

Cell count: 51 (including the identity control and, for HALT-RESUME, 2 placebo kinds).

## Cell list (name | mode/spec | CANON = named a priori for the recent look)
* QW_ctrl_identity | engine | spec_diff={} | measure=res |  | the stack as it is: day entry test +5R, arm 2R keep 50%, week floor 12R
* QW_book_up_off | engine | spec_diff={'pb_win': None} | measure=res |  | book day entry test +5R switched OFF (arm and floor kept)
* QW_book_up1R_skip | engine | spec_diff={'pb_win': 1.0} | measure=res |  | book day entry test +1R: no new entries (base is +5R)
* QW_book_up1R_halve | engine | spec_diff={'pb_win': 1.0, 'halve_f': 0.5} | measure=res |  | book day +1R: later entries at 50%
* QW_book_up2R_skip | engine | spec_diff={'pb_win': 2.0} | measure=res |  | book day entry test +2R: no new entries (base is +5R)
* QW_book_up2R_halve | engine | spec_diff={'pb_win': 2.0, 'halve_f': 0.5} | measure=res |  | book day +2R: later entries at 50%
* QW_book_up3R_skip | engine | spec_diff={'pb_win': 3.0} | measure=res | CANON | book day entry test +3R: no new entries (base is +5R)
* QW_book_up3R_halve | engine | spec_diff={'pb_win': 3.0, 'halve_f': 0.5} | measure=res |  | book day +3R: later entries at 50%
* QW_book_up4R_skip | engine | spec_diff={'pb_win': 4.0} | measure=res |  | book day entry test +4R: no new entries (base is +5R)
* QW_book_up4R_halve | engine | spec_diff={'pb_win': 4.0, 'halve_f': 0.5} | measure=res |  | book day +4R: later entries at 50%
* QW_book_up6R_skip | engine | spec_diff={'pb_win': 6.0} | measure=res |  | book day entry test +6R: no new entries (base is +5R)
* QW_book_up6R_halve | engine | spec_diff={'pb_win': 6.0, 'halve_f': 0.5} | measure=res |  | book day +6R: later entries at 50%
* QW_arm1.5_keep0.5 | engine | spec_diff={'arm': 1.5} | measure=res |  | day give-back arm at 1.5R keep 50% (base 2R)
* QW_arm3.0_keep0.5 | engine | spec_diff={'arm': 3.0} | measure=res |  | day give-back arm at 3.0R keep 50% (base 2R)
* QW_arm4.0_keep0.5 | engine | spec_diff={'arm': 4.0} | measure=res |  | day give-back arm at 4.0R keep 50% (base 2R)
* QW_arm_off | engine | spec_diff={'arm': None} | measure=res |  | day give-back arm OFF
* QW_arm2_keep0.25 | engine | spec_diff={'keep': 0.25} | measure=res |  | day arm 2R keep 0.25 (base .5)
* QW_arm2_keep0.75 | engine | spec_diff={'keep': 0.75} | measure=res |  | day arm 2R keep 0.75 (base .5)
* QW_arm1.0_cont0.5 | engine | spec_diff={'arm': 1.0, 'arm_cont': 0.5} | measure=res |  | day arm 1.0R: instead of flatten-and-quit, the open position runs and later entries at 50%
* QW_arm2.0_cont0.5 | engine | spec_diff={'arm_cont': 0.5} | measure=res | CANON | day arm 2.0R: instead of flatten-and-quit, the open position runs and later entries at 50%
* QW_arm3.0_cont0.5 | engine | spec_diff={'arm': 3.0, 'arm_cont': 0.5} | measure=res |  | day arm 3.0R: instead of flatten-and-quit, the open position runs and later entries at 50%
* QW_stack_day+1R_quit | sweep mode 10 P=[1.0, 0.0, 0.0, 12000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised day P&L >= +1R (12,000 per R, research lots): quit the rest of the day
* QW_stack_day+1R_halve | sweep mode 10 P=[1.0, 0.0, 0.5, 12000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised day P&L >= +1R (12,000 per R, research lots): halve the rest of the day
* QW_stack_day+2R_quit | sweep mode 10 P=[1.0, 0.0, 0.0, 24000.0, 0.0, 0.0] | spec_diff={} | measure=res | CANON | stack realised day P&L >= +2R (12,000 per R, research lots): quit the rest of the day
* QW_stack_day+2R_halve | sweep mode 10 P=[1.0, 0.0, 0.5, 24000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised day P&L >= +2R (12,000 per R, research lots): halve the rest of the day
* QW_stack_day+3R_quit | sweep mode 10 P=[1.0, 0.0, 0.0, 36000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised day P&L >= +3R (12,000 per R, research lots): quit the rest of the day
* QW_stack_day+3R_halve | sweep mode 10 P=[1.0, 0.0, 0.5, 36000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised day P&L >= +3R (12,000 per R, research lots): halve the rest of the day
* QW_stack_day+4R_quit | sweep mode 10 P=[1.0, 0.0, 0.0, 48000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised day P&L >= +4R (12,000 per R, research lots): quit the rest of the day
* QW_stack_day+4R_halve | sweep mode 10 P=[1.0, 0.0, 0.5, 48000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised day P&L >= +4R (12,000 per R, research lots): halve the rest of the day
* QW_stack_day+6R_quit | sweep mode 10 P=[1.0, 0.0, 0.0, 72000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised day P&L >= +6R (12,000 per R, research lots): quit the rest of the day
* QW_stack_day+6R_halve | sweep mode 10 P=[1.0, 0.0, 0.5, 72000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised day P&L >= +6R (12,000 per R, research lots): halve the rest of the day
* QW_stack_day+$1000live_quit | sweep mode 10 P=[1.0, 0.0, 0.0, 1000.0, 0.0, 0.0] | spec_diff={} | measure=live |  | stack realised day P&L >= +$1000 AT LIVE LOTS: quit the rest of the day
* QW_stack_day+$1000live_halve | sweep mode 10 P=[1.0, 0.0, 0.5, 1000.0, 0.0, 0.0] | spec_diff={} | measure=live |  | stack realised day P&L >= +$1000 AT LIVE LOTS: halve the rest of the day
* QW_stack_day+$2000live_quit | sweep mode 10 P=[1.0, 0.0, 0.0, 2000.0, 0.0, 0.0] | spec_diff={} | measure=live |  | stack realised day P&L >= +$2000 AT LIVE LOTS: quit the rest of the day
* QW_stack_day+$2000live_halve | sweep mode 10 P=[1.0, 0.0, 0.5, 2000.0, 0.0, 0.0] | spec_diff={} | measure=live |  | stack realised day P&L >= +$2000 AT LIVE LOTS: halve the rest of the day
* QW_stack_day+$4000live_quit | sweep mode 10 P=[1.0, 0.0, 0.0, 4000.0, 0.0, 0.0] | spec_diff={} | measure=live |  | stack realised day P&L >= +$4000 AT LIVE LOTS: quit the rest of the day
* QW_stack_day+$4000live_halve | sweep mode 10 P=[1.0, 0.0, 0.5, 4000.0, 0.0, 0.0] | spec_diff={} | measure=live |  | stack realised day P&L >= +$4000 AT LIVE LOTS: halve the rest of the day
* QW_stack_day+$6000live_quit | sweep mode 10 P=[1.0, 0.0, 0.0, 6000.0, 0.0, 0.0] | spec_diff={} | measure=live |  | stack realised day P&L >= +$6000 AT LIVE LOTS: quit the rest of the day
* QW_stack_day+$6000live_halve | sweep mode 10 P=[1.0, 0.0, 0.5, 6000.0, 0.0, 0.0] | spec_diff={} | measure=live |  | stack realised day P&L >= +$6000 AT LIVE LOTS: halve the rest of the day
* QW_stack_sess+1R_quit | sweep mode 11 P=[1.0, 0.0, 0.0, 12000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised session P&L >= +1R: quit the rest of the session
* QW_stack_sess+1R_halve | sweep mode 11 P=[1.0, 0.0, 0.5, 12000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised session P&L >= +1R: halve the rest of the session
* QW_stack_sess+2R_quit | sweep mode 11 P=[1.0, 0.0, 0.0, 24000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised session P&L >= +2R: quit the rest of the session
* QW_stack_sess+2R_halve | sweep mode 11 P=[1.0, 0.0, 0.5, 24000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised session P&L >= +2R: halve the rest of the session
* QW_stack_sess+3R_quit | sweep mode 11 P=[1.0, 0.0, 0.0, 36000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised session P&L >= +3R: quit the rest of the session
* QW_stack_sess+3R_halve | sweep mode 11 P=[1.0, 0.0, 0.5, 36000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised session P&L >= +3R: halve the rest of the session
* QW_stack_wk+4R_quit | sweep mode 12 P=[1.0, 0.0, 0.0, 48000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised week P&L >= +4R: quit the rest of the week
* QW_stack_wk+4R_halve | sweep mode 12 P=[1.0, 0.0, 0.5, 48000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised week P&L >= +4R: halve the rest of the week
* QW_stack_wk+8R_quit | sweep mode 12 P=[1.0, 0.0, 0.0, 96000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised week P&L >= +8R: quit the rest of the week
* QW_stack_wk+8R_halve | sweep mode 12 P=[1.0, 0.0, 0.5, 96000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised week P&L >= +8R: halve the rest of the week
* QW_stack_wk+12R_quit | sweep mode 12 P=[1.0, 0.0, 0.0, 144000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised week P&L >= +12R: quit the rest of the week
* QW_stack_wk+12R_halve | sweep mode 12 P=[1.0, 0.0, 0.5, 144000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised week P&L >= +12R: halve the rest of the week
