# RHQ RISK-OFF - prereg (2026-10-31)

RISK-OFF = after a stop, size down the next trade(s) for a period: per-book (next trade after a stop at f; ladder; last-K trades; T minutes; rest of day / session) and stack-level (>=2 stops in a day across books -> half size for the rest of the day / session / T minutes; same-side; realised day / week P&L rungs). Back to full after a winner (streak variants) or after the period.

Mechanism: stops cluster (regime/day-type persistence); sizing down after a stop should shave loss clusters more than it shaves wins. Predicted sign if real: positive excess over the lot-factor-matched uniform scaling line in PRE and X' and on the stack at equal risk; a rule that only lowers lots has excess = 0 (STRUCTURE).

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

Cell count: 56 (including the identity control and, for HALT-RESUME, 2 placebo kinds).

## Cell list (name | mode/spec | CANON = named a priori for the recent look)
* RO_ctrl_identity | engine | spec_diff={} | measure=res |  | m=1 everywhere: must equal the stack as it is
* RO_book_streak1_f0.5 | sweep mode 1 P=[0.0, 1.0, 0.5, 0.0, 0.0, 0.0] | spec_diff={} | measure=res | CANON | per-book: next trade after N consecutive book stops at f; back to full after a non-stop (winner) trade
* RO_book_streak1_f0.25 | sweep mode 1 P=[0.0, 1.0, 0.25, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | per-book: next trade after N consecutive book stops at f; back to full after a non-stop (winner) trade
* RO_book_streak2_f0.5 | sweep mode 1 P=[0.0, 2.0, 0.5, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | per-book: next trade after N consecutive book stops at f; back to full after a non-stop (winner) trade
* RO_book_streak2_f0.25 | sweep mode 1 P=[0.0, 2.0, 0.25, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | per-book: next trade after N consecutive book stops at f; back to full after a non-stop (winner) trade
* RO_book_ladder_f0.5_fl0.25 | sweep mode 1 P=[0.0, 1.0, 0.5, 0.0, 0.25, 0.0] | spec_diff={} | measure=res |  | per-book anti-martingale ladder 1,.5,.25 per consecutive stop, floor .25, reset after a non-stop
* RO_book_lastK2_f0.5 | sweep mode 2 P=[0.0, 1.0, 0.5, 0.0, 0.0, 2.0] | spec_diff={} | measure=res |  | per-book: a stop among the last 2 closed book trades -> f (releases after 2 trades)
* RO_book_lastK2_f0.25 | sweep mode 2 P=[0.0, 1.0, 0.25, 0.0, 0.0, 2.0] | spec_diff={} | measure=res |  | per-book: a stop among the last 2 closed book trades -> f (releases after 2 trades)
* RO_book_lastK3_f0.5 | sweep mode 2 P=[0.0, 1.0, 0.5, 0.0, 0.0, 3.0] | spec_diff={} | measure=res |  | per-book: a stop among the last 3 closed book trades -> f (releases after 3 trades)
* RO_book_lastK3_f0.25 | sweep mode 2 P=[0.0, 1.0, 0.25, 0.0, 0.0, 3.0] | spec_diff={} | measure=res |  | per-book: a stop among the last 3 closed book trades -> f (releases after 3 trades)
* RO_book_T30_f0.5 | sweep mode 3 P=[0.0, 1.0, 0.5, 30.0, 0.0, 0.0] | spec_diff={} | measure=res |  | per-book: last book stop <= 30 min ago -> f
* RO_book_T30_f0.25 | sweep mode 3 P=[0.0, 1.0, 0.25, 30.0, 0.0, 0.0] | spec_diff={} | measure=res |  | per-book: last book stop <= 30 min ago -> f
* RO_book_T60_f0.5 | sweep mode 3 P=[0.0, 1.0, 0.5, 60.0, 0.0, 0.0] | spec_diff={} | measure=res |  | per-book: last book stop <= 60 min ago -> f
* RO_book_T60_f0.25 | sweep mode 3 P=[0.0, 1.0, 0.25, 60.0, 0.0, 0.0] | spec_diff={} | measure=res |  | per-book: last book stop <= 60 min ago -> f
* RO_book_T120_f0.5 | sweep mode 3 P=[0.0, 1.0, 0.5, 120.0, 0.0, 0.0] | spec_diff={} | measure=res |  | per-book: last book stop <= 120 min ago -> f
* RO_book_T120_f0.25 | sweep mode 3 P=[0.0, 1.0, 0.25, 120.0, 0.0, 0.0] | spec_diff={} | measure=res |  | per-book: last book stop <= 120 min ago -> f
* RO_book_T240_f0.5 | sweep mode 3 P=[0.0, 1.0, 0.5, 240.0, 0.0, 0.0] | spec_diff={} | measure=res |  | per-book: last book stop <= 240 min ago -> f
* RO_book_T240_f0.25 | sweep mode 3 P=[0.0, 1.0, 0.25, 240.0, 0.0, 0.0] | spec_diff={} | measure=res |  | per-book: last book stop <= 240 min ago -> f
* RO_book_day1_f0.5 | sweep mode 4 P=[0.0, 1.0, 0.5, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | per-book: >= 1 book stops today -> f for the rest of the day
* RO_book_sess1_f0.5 | sweep mode 5 P=[0.0, 1.0, 0.5, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | per-book: >= 1 book stops in this session -> f for the rest of the session
* RO_book_day1_f0.25 | sweep mode 4 P=[0.0, 1.0, 0.25, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | per-book: >= 1 book stops today -> f for the rest of the day
* RO_book_sess1_f0.25 | sweep mode 5 P=[0.0, 1.0, 0.25, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | per-book: >= 1 book stops in this session -> f for the rest of the session
* RO_book_day2_f0.5 | sweep mode 4 P=[0.0, 2.0, 0.5, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | per-book: >= 2 book stops today -> f for the rest of the day
* RO_book_sess2_f0.5 | sweep mode 5 P=[0.0, 2.0, 0.5, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | per-book: >= 2 book stops in this session -> f for the rest of the session
* RO_book_day2_f0.25 | sweep mode 4 P=[0.0, 2.0, 0.25, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | per-book: >= 2 book stops today -> f for the rest of the day
* RO_book_sess2_f0.25 | sweep mode 5 P=[0.0, 2.0, 0.25, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | per-book: >= 2 book stops in this session -> f for the rest of the session
* RO_stack_streak2_f0.5 | sweep mode 1 P=[1.0, 2.0, 0.5, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack: 2 consecutive stack stops (any book) -> f until a non-stop closes
* RO_stack_streak2_f0.25 | sweep mode 1 P=[1.0, 2.0, 0.25, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack: 2 consecutive stack stops (any book) -> f until a non-stop closes
* RO_stack_streak3_f0.5 | sweep mode 1 P=[1.0, 3.0, 0.5, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack: 3 consecutive stack stops (any book) -> f until a non-stop closes
* RO_stack_streak3_f0.25 | sweep mode 1 P=[1.0, 3.0, 0.25, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack: 3 consecutive stack stops (any book) -> f until a non-stop closes
* RO_stack_day2_f0.5 | sweep mode 4 P=[1.0, 2.0, 0.5, 0.0, 0.0, 0.0] | spec_diff={} | measure=res | CANON | stack: >= 2 stops today across books -> f for the rest of the day
* RO_stack_day2_f0.25 | sweep mode 4 P=[1.0, 2.0, 0.25, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack: >= 2 stops today across books -> f for the rest of the day
* RO_stack_day3_f0.5 | sweep mode 4 P=[1.0, 3.0, 0.5, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack: >= 3 stops today across books -> f for the rest of the day
* RO_stack_day3_f0.25 | sweep mode 4 P=[1.0, 3.0, 0.25, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack: >= 3 stops today across books -> f for the rest of the day
* RO_stack_day4_f0.5 | sweep mode 4 P=[1.0, 4.0, 0.5, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack: >= 4 stops today across books -> f for the rest of the day
* RO_stack_day4_f0.25 | sweep mode 4 P=[1.0, 4.0, 0.25, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack: >= 4 stops today across books -> f for the rest of the day
* RO_stack_sess2_f0.5 | sweep mode 5 P=[1.0, 2.0, 0.5, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack: >= 2 stops in this session across books -> f for the rest of the session
* RO_stack_sess2_f0.25 | sweep mode 5 P=[1.0, 2.0, 0.25, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack: >= 2 stops in this session across books -> f for the rest of the session
* RO_stack_sess3_f0.5 | sweep mode 5 P=[1.0, 3.0, 0.5, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack: >= 3 stops in this session across books -> f for the rest of the session
* RO_stack_sess3_f0.25 | sweep mode 5 P=[1.0, 3.0, 0.25, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack: >= 3 stops in this session across books -> f for the rest of the session
* RO_stack_T30_N2_f0.5 | sweep mode 3 P=[1.0, 2.0, 0.5, 30.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack: >= 2 stops in the last 30 min -> f
* RO_stack_T30_N2_f0.25 | sweep mode 3 P=[1.0, 2.0, 0.25, 30.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack: >= 2 stops in the last 30 min -> f
* RO_stack_T60_N2_f0.5 | sweep mode 3 P=[1.0, 2.0, 0.5, 60.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack: >= 2 stops in the last 60 min -> f
* RO_stack_T60_N2_f0.25 | sweep mode 3 P=[1.0, 2.0, 0.25, 60.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack: >= 2 stops in the last 60 min -> f
* RO_stack_T120_N2_f0.5 | sweep mode 3 P=[1.0, 2.0, 0.5, 120.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack: >= 2 stops in the last 120 min -> f
* RO_stack_T120_N2_f0.25 | sweep mode 3 P=[1.0, 2.0, 0.25, 120.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack: >= 2 stops in the last 120 min -> f
* RO_side_day2_f0.5 | sweep mode 4 P=[2.0, 2.0, 0.5, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | same-side stack: >= 2 same-side stops today -> f for the rest of the day (applies to same-side entries)
* RO_side_day3_f0.5 | sweep mode 4 P=[2.0, 3.0, 0.5, 0.0, 0.0, 0.0] | spec_diff={} | measure=res |  | same-side stack: >= 3 same-side stops today -> f for the rest of the day (applies to same-side entries)
* RO_side_T60_N2_f0.5 | sweep mode 3 P=[2.0, 2.0, 0.5, 60.0, 0.0, 0.0] | spec_diff={} | measure=res |  | same-side stack: >= 2 same-side stops in 60 min -> f
* RO_stack_dayPL-1R_f0.5 | sweep mode 6 P=[1.0, 0.0, 0.5, 12000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised day P&L <= -1R (R=12,000) -> f for the rest of the day (a half-size rung before the engine -2R book test)
* RO_stack_dayPL-2R_f0.5 | sweep mode 6 P=[1.0, 0.0, 0.5, 24000.0, 0.0, 0.0] | spec_diff={} | measure=res | CANON | stack realised day P&L <= -2R (R=12,000) -> f for the rest of the day (a half-size rung before the engine -2R book test)
* RO_stack_dayPL-3R_f0.5 | sweep mode 6 P=[1.0, 0.0, 0.5, 36000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised day P&L <= -3R (R=12,000) -> f for the rest of the day (a half-size rung before the engine -2R book test)
* RO_book_dayPL-1R_f0.5 | sweep mode 6 P=[0.0, 0.0, 0.5, 12000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | book realised day P&L <= -1R -> f for the rest of the day
* RO_book_dayPL-1.5R_f0.5 | sweep mode 6 P=[0.0, 0.0, 0.5, 18000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | book realised day P&L <= -1.5R -> f for the rest of the day
* RO_stack_weekPL-4R_f0.5 | sweep mode 7 P=[1.0, 0.0, 0.5, 48000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised week P&L <= -4R -> f for the rest of the week
* RO_stack_weekPL-8R_f0.5 | sweep mode 7 P=[1.0, 0.0, 0.5, 96000.0, 0.0, 0.0] | spec_diff={} | measure=res |  | stack realised week P&L <= -8R -> f for the rest of the week
