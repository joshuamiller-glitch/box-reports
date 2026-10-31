# DS3_HALT_RESUME - RHQ follow-up section 8 (2026-10-31)

**INTERPRETATION IS THE LEAD'S, NOT THE USER'S.** The user's original text for this program never reached the lead (no directive text exists in the logs); the lead supplied the interpretation below. If the user re-pastes the original text, this report is superseded and the cells are re-run with the same machinery (code `l2vast/ds3/code/rhq/`, outputs `l2vast/ds3/out/rhq/`).

Research only; no live/execution/chart change. UNTOUCHED (label day > 20260206) never read. Windows: L3M 20251106.. (view), L6M 20250801.., HOLD 20250701.., PRE 20240201..20250630, X' 20230401..20240131, all capped 20260206. Base = the stack as it is = 70/30 split (S73) on the exact per-book lock engine (day entry test +5R/-2R, day arm 2R keep 50%, week floor 12R in planned-lot R; R = lots x 60 x $20), six engine books ST HM WT KB SM PE, N basis (M and LIVE-CAL beside for the cells that got the recent look). $ shown at research lots (ST10 HM10 WT7 KB5.2 SM7.4 PE5.6) AND at LIVE lots (mapping stated: ST=U6 4 Asia/London; HM=H6 4 Asia / 2 NY-AM; KB=K6 2; SM=M6 2 London/NY-AM; PE=P6 7 Asia/London/NY-AM; WT not live = research/2.35 = 3; pre-market counted with NY-AM and close with NY-PM; per-row live/research scaling of the research-lot outcome, locks evaluated at research lots). Prereg autopilot/RHQ_HALT_RESUME_prereg.md sha256 0fa0cd635870969ab4ce7f7ad13011a77a2485987c682001d78ce77a8c12f526 and the addendum autopilot/RHQ_HALT_RESUME_ADDENDUM_prereg.md sha256 986c01d2ebac91e85c7bfb854d17f83268dbcef6af15b0d523066842db4626e4 (sha256 in DECISIONS.md before any cell was scored). Multiplicity and the cumulative count are in the QUANT block. UF_TRIALS side=rhq_*. 

Lead's interpretation: HALT-RESUME = the engine's per-book day entry test (-2R / +5R realised), day give-back arm (2R keep 50%) and week floor (12R) stop trading for the rest of the day / week; the cells test RESUME rules: next session; T minutes; next day; Thursday; virtual-equity conditions (the halted signals' shadow P&L brings the day/week back to the arm level / -4R / -8R / 0R), at size x0.5 or x1, 'sized-lot' governors in the resumed segment, and a random-resume-timing placebo. Main program 24 cells (+1 control); addendum 14 cells (+2 controls) after the 12R week floor was found inert.

## 1. Page 1 - the answer: NULL at the live governors; the only thing that 'works' is not halting

1. **The 12R week floor never fires on the six-book S73 stack: 0 fires in 149 weeks x 6 books** (10R: 4 fires, 8R: 21, 6R: 77, 5R: 131, 4R: 225 over the six books). So 'resume after the week floor halt / Thursday at 50% when the week is back to -4R' (backlog idea #49) is identical to the stack as it is: all 8 week-floor cells of the main program (and the week random-resume placebo) give exactly 0 in every window. If D6's week floor is wired at the STACK level or at a smaller R this changes; the research lock engine (per book) cannot show it. Day halts are common (day arm: 191 / 161 / 233 / 185 / 35 / 198 book-days fire in ST / HM / WT / KB / SM / PE out of 737; the entry-test halts resume 658 times in the all-halts cell).
2. **Main program (24 cells): 0 carried on PRE and X'.** Excess over the lot-factor line > 0 in PRE for 1 cell and in X' for 7, never both. The canon day-lock rule 'every halt resumes at the next session at x0.5' (HR_all_sess_rf0.5) re-admits ~60 trades/wk (lot factor 1.07 X' .. 1.64 L3M; 1.45 in L6M): d vs the stack L3M -0.6k, L6M +4.2k (MDE 26.9k), HOLD +2.7k, PRE -2.1k, X' +0.7k per week (live lots +0.1k / +0.1k / -0.4k / -1.4k / +1.5k) - all inside the MDE - but the excess over the lot-factor line is -20.5k / -31.3k / -25.1k / -24.3k / -0.5k: the signals after a lock are worse than the average trade (STRUCTURE: it is more lots at lower quality), and at equal risk the delta is -3.2k / -2.9k / -3.3k / -7.2k / -0.9k. The random-resume-timing placebo (30 seeds) ranks its excess 0.50 (L3M) / 0.87 (L6M) / 0.83 (HOLD) / 1.00 (PRE) / 0.97 (X') - a random resume time is worse than the next-session rule - but the absolute excess stays hugely negative (placebo mean -34k in L6M). Tier: DEAD / STRUCTURE.
3. **Addendum (tighter floors 6R and 4R so that the floor fires): the resume rules DO beat 'stay halted' at the same floor - but the tighter floor itself loses to the stack as it is.** Vs the SAME floor without resume: 7 of 14 cells carried (excess and equal-risk >= 0 in PRE and X'): e.g. 6R floor, resume Thursday at x1: d +4.2k L3M, +2.4k L6M, -1.0k HOLD, +5.0k PRE, +1.4k X' (live lots +3.4k / +1.9k / +0.5k / +2.0k / -0.0k); 4R floor, resume Thursday at x1: -1.8k / +2.8k / -2.0k / +8.0k / +6.5k. Vs the stack as it is (12R floor, never fires): 6R/Thursday x1 +1.9k / +1.6k / +2.1k / -0.3k / +0.7k (MDE 1.4-2.5k, i.e. noise) and 4R/Thursday x1 +0.8k / -2.7k / -0.1k / -3.5k / -1.9k. The controls (floor only, no resume, vs the stack, PRE / X' only): 6R floor -5.3k / -0.8k, 4R floor -11.6k / -8.4k per week (excess -3.1k / -0.4k and -2.8k / -6.6k). So resume recovers part of what a tight floor throws away; nothing beats leaving the floor at 12R. Among the 7 cells that got the recent look none is >= 0 in all five windows on BOTH d and excess (the 6R virtual-equity cells are >= 0 on d in all five windows but at $0.1-0.7k/wk, MDE 0.5-3k, and excess is slightly negative in L6M/HOLD). Placebo ranks vs random resume timing: 0.83-0.97 in L3M and L6M, 0.57-1.00 in HOLD, 0.97-1.00 in PRE. Tier: LEAD-at-best for 'resume Thursday at x1 after a 6R floor' versus staying halted only; CANDIDATE-RECENT not reached (fails HOLD); no change to D6 follows.
4. **Sized-lot R governors (the stage thresholds of the resumed segment multiplied by the resume factor 0.5):** HR_all_sess_rf0.5_sizedgov gives PRE -0.6k / X' +0.9k per week vs -2.1k / +0.7k planned-lot (excess -21.7k / -0.3k vs -24.3k / -0.5k): same conclusion. HR_dayL_sess_rf0.5_sizedgov is identical to its planned-lot twin because the day entry-test loop is not rescaled (only the arm and week-floor stages are); this is a limitation of the sized variant, not a finding. The sized variant was a screen cell, not looked at in the recent windows (not carried).
5. **QUANT:** main program: White RC p 0.23, Romano-Wolf none, PBO 0.25. Addendum: RC p 0.02 on the selection frame (PRE u X', where the cells were selected) and 0.05 over all weeks, Romano-Wolf survivors in the selection frame HRX_floor4_sess_rf0.5 and HRX_floor4_day_rf0.5, none over all weeks, PBO 0.77; the comparator is the same tight floor, so this measures 'resume vs halted', not 'vs the stack'.
6. **For the Sunday brief:** keep the lock engine as it is. No resume rule is supported at the 12R week floor (it never binds); if D6's floor is tighter in R terms than the research per-book floor, a Thursday / next-session resume at x1 (not x0.5) is the better of the resume variants but does not beat having no floor. The day-lock resume (next session x0.5 or x1) loses against the lot-factor line.

Questions for the user (MORNING.md): (a) is D6's week floor 12R per book in planned-lot R (as in the research engine, where it never fires) or at the stack level / smaller? (b) re-paste the original HALT-RESUME text if it meant something else.

### The stack as it is (S73 70/30 split, six engine books, lock engine day +5R/-2R, arm 2R keep 50%, week floor 12R; N basis; research lots and LIVE lots)
| window | weeks | mean $/wk | SD | maxDD | worst-20 sum | trades/wk | LIVE-lot mean $/wk |
|---|---|---|---|---|---|---|---|
| L3M | 14 | 31,261 | 130,314 | 318,846 | 437,655 | 126.71 | 15,161 |
| L6M | 28 | 79,055 | 136,536 | 318,846 | 332,332 | 128.71 | 29,957 |
| HOLD | 32 | 66,693 | 169,113 | 624,547 | -630,207 | 127.41 | 26,161 |
| PRE | 75 | 61,831 | 138,576 | 614,903 | -2,304,704 | 129.47 | 22,902 |
| X' | 44 | 18,206 | 101,638 | 469,146 | -1,392,026 | 105.86 | 3,430 |

### Screen: every cell, PRE and X' only (selection frame; recent columns are shown only for the cells in the next section)
lam = rule lots / stack lots; excess = rule mean - lam x stack mean (the lot-factor-matched uniform scaling line; STRUCTURE if <= 0); eq = equal-risk delta (lot factor c solving worst-20 over PRE u X' equal to the stack, c x rule - stack), research-lot $/wk.

| cell | lam PRE | d PRE (MDE) | excess PRE | eq PRE | LIVE d PRE | lam X' | d X' (MDE) | excess X' | eq X' | flagged/wk PRE | carried | recent look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HR_armA_virtarm_rf1 | 1.10 | 7,544 (12,118) | 1,301 | 5,288 | 392 | 1.02 | -2,310 (5,850) | -2,704 | -2,827 | 0.00 |  |  |
| HR_armA_sess_rf1 | 1.11 | 5,155 (10,411) | -1,376 | 2,976 | 1,315 | 1.02 | -328 (3,649) | -641 | -909 | 0.00 |  |  |
| HR_wkF_thu_rf1 | 1.00 | 0 (0) | 0 | 0 | 0 | 1.00 | 0 (0) | 0 | 0 | 0.00 |  |  |
| HR_wkF_virt4R_rf0.5 | 1.00 | 0 (0) | 0 | 0 | 0 | 1.00 | 0 (0) | 0 | 0 | 0.00 |  |  |
| HR_wkF_day_rf0.5 | 1.00 | 0 (0) | 0 | 0 | 0 | 1.00 | 0 (0) | 0 | 0 | 0.00 |  |  |
| HR_wkF_sess_rf0.5 | 1.00 | 0 (0) | 0 | 0 | 0 | 1.00 | 0 (0) | 0 | 0 | 0.00 |  |  |
| HR_wkF_thuvirt4R_rf0.5 | 1.00 | 0 (0) | 0 | 0 | 0 | 1.00 | 0 (0) | 0 | 0 | 0.00 |  | Y |
| HR_wkF_thu_rf0.5 | 1.00 | 0 (0) | 0 | 0 | 0 | 1.00 | 0 (0) | 0 | 0 | 0.00 |  |  |
| HR_wkF_virt0R_rf0.5 | 1.00 | 0 (0) | 0 | 0 | 0 | 1.00 | 0 (0) | 0 | 0 | 0.00 |  |  |
| HR_wkF_virt8R_rf0.5 | 1.00 | 0 (0) | 0 | 0 | 0 | 1.00 | 0 (0) | 0 | 0 | 0.00 |  |  |
| HR_dayW_sess_rf0.5 | 1.02 | -544 (2,492) | -1,642 | -544 | -445 | 1.00 | 0 (0) | 0 | 0 | 0.00 |  |  |
| HR_armA_virtarm_rf0.5 | 1.12 | 1,580 (5,322) | -5,695 | 756 | -516 | 1.02 | -1,155 (2,925) | -1,549 | -1,376 | 0.00 |  |  |
| HR_dayW_sess_rf1 | 1.01 | -637 (4,092) | -1,423 | -637 | -817 | 1.00 | 0 (0) | 0 | 0 | 0.00 |  |  |
| HR_armA_min60_rf0.5 | 1.19 | 1,691 (8,129) | -9,976 | 763 | -920 | 1.06 | -1,242 (3,591) | -2,303 | -1,490 | 0.00 |  |  |
| HR_dayL_sess_rf1 | 1.15 | -3,546 (12,867) | -12,815 | -3,743 | -1,062 | 1.05 | 2,563 (8,507) | 1,690 | 2,493 | 0.00 |  |  |
| HR_armA_sess_rf0.5 | 1.12 | 1,040 (5,719) | -6,551 | -543 | -262 | 1.02 | -359 (1,725) | -683 | -808 | 0.00 |  |  |
| HR_dayL_sess_rf0.5_x2 | 1.19 | -1,949 (6,403) | -13,899 | -2,537 | -737 | 1.05 | 1,103 (4,481) | 173 | 913 | 0.00 |  |  |
| HR_all_sess_rf0.5_sizedgov | 1.34 | -639 (8,588) | -21,725 | -2,450 | -453 | 1.07 | 939 (4,834) | -303 | 372 | 0.00 |  |  |
| HR_dayL_sess_rf0.5_sizedgov | 1.19 | -2,448 (6,574) | -14,283 | -3,032 | -808 | 1.05 | 1,103 (4,481) | 173 | 913 | 0.00 |  |  |
| HR_dayL_sess_rf0.5 | 1.19 | -2,448 (6,574) | -14,283 | -3,032 | -808 | 1.05 | 1,103 (4,481) | 173 | 913 | 0.00 |  |  |
| HR_all_sess_rf0.5 | 1.36 | -2,055 (9,066) | -24,307 | -4,226 | -1,369 | 1.07 | 744 (4,892) | -509 | 56 | 0.00 |  | Y |
| HR_dayL_virt1R_rf0.5 | 1.08 | -4,245 (5,293) | -9,473 | -6,292 | -1,439 | 1.03 | 1,219 (2,199) | 719 | 528 | 0.00 |  |  |
| HR_dayL_min60_rf0.5 | 1.26 | -8,246 (7,844) | -24,569 | -9,474 | -2,213 | 1.10 | 3,781 (5,635) | 1,937 | 3,277 | 0.00 |  |  |
| HR_dayL_min120_rf0.5 | 1.24 | -8,263 (7,721) | -22,869 | -10,549 | -2,378 | 1.08 | 2,132 (4,943) | 628 | 1,265 | 0.00 |  |  |

### The single recent look: stack weekly mean / SD / maxDD / worst-20 weeks, recent-first, rule vs the stack as it is
Columns: stack $/wk base -> rule; SD; maxDD; worst-20 sum (sum of the worst min(20, weeks) weeks; L3M has 14 and L6M 28 weeks, so those two are not comparable with the 75-week PRE) (research lots); d = rule - stack with MDE (2.8 SE of the paired weekly delta); lam; uniform = lam x stack mean; excess = rule - uniform; eqWF = equal-risk delta with c solving worst-20 over WF (PRE u HOLD) equal to the stack (c shown); trades/wk; LIVE-lot $/wk d.

#### HR_wkF_thuvirt4R_rf0.5  (week floor halt, resume: F_thuvirt4R_rf0.5)  engine fires (day arm / week floor, all windows, per book ST HM WT KB SM PE)=[(191, 0), (161, 0), (233, 0), (185, 0), (35, 0), (198, 0)], entry-test resumes=0, stage resumes day/week=0/0, iterations to a stable traded set=1
| window | mean | SD | maxDD | worst-20 | d (MDE) | lam | uniform line | excess | eqWF | trades/wk | LIVE d |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 31,261 -> 31,261 | 130,314 -> 130,314 | 318,846 -> 318,846 | 437,655 -> 437,655 | 0 (0) | 1.00 | 31,261 | 0 | 0 (c 1.00) | 126.71 -> 126.71 | 0 |
| L6M | 79,055 -> 79,055 | 136,536 -> 136,536 | 318,846 -> 318,846 | 332,332 -> 332,332 | 0 (0) | 1.00 | 79,055 | 0 | 0 (c 1.00) | 128.71 -> 128.71 | 0 |
| HOLD | 66,693 -> 66,693 | 169,113 -> 169,113 | 624,547 -> 624,547 | -630,207 -> -630,207 | 0 (0) | 1.00 | 66,693 | 0 | 0 (c 1.00) | 127.41 -> 127.41 | 0 |
| PRE | 61,831 -> 61,831 | 138,576 -> 138,576 | 614,903 -> 614,903 | -2,304,704 -> -2,304,704 | 0 (0) | 1.00 | 61,831 | 0 | 0 (c 1.00) | 129.47 -> 129.47 | 0 |
| X' | 18,206 -> 18,206 | 101,638 -> 101,638 | 469,146 -> 469,146 | -1,392,026 -> -1,392,026 | 0 (0) | 1.00 | 18,206 | 0 | 0 (c 1.00) | 105.86 -> 105.86 | 0 |

#### HR_all_sess_rf0.5  (every halt resumes at the next session at half size)  engine fires (day arm / week floor, all windows, per book ST HM WT KB SM PE)=[(192, 2), (161, 0), (233, 1), (185, 0), (35, 0), (198, 0)], entry-test resumes=658, stage resumes day/week=355/1, iterations to a stable traded set=1
| window | mean | SD | maxDD | worst-20 | d (MDE) | lam | uniform line | excess | eqWF | trades/wk | LIVE d |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 31,261 -> 30,661 | 130,314 -> 157,177 | 318,846 -> 576,925 | 437,655 -> 429,249 | -600 (50,942) | 1.64 | 51,155 | -20,494 | -3,235 (c 0.91) | 126.71 -> 210.71 | 104 |
| L6M | 79,055 -> 83,293 | 136,536 -> 155,142 | 318,846 -> 576,925 | 332,332 -> 223,258 | 4,237 (26,863) | 1.45 | 114,633 | -31,340 | -2,920 (c 0.91) | 128.71 -> 188.39 | 88 |
| HOLD | 66,693 -> 69,387 | 169,113 -> 186,460 | 624,547 -> 673,800 | -630,207 -> -855,201 | 2,694 (23,746) | 1.42 | 94,500 | -25,113 | -3,269 (c 0.91) | 127.41 -> 182.38 | -351 |
| PRE | 61,831 -> 59,775 | 138,576 -> 143,513 | 614,903 -> 561,756 | -2,304,704 -> -2,449,291 | -2,055 (9,066) | 1.36 | 84,083 | -24,307 | -7,192 (c 0.91) | 129.47 -> 177.57 | -1,369 |
| X' | 18,206 -> 18,949 | 101,638 -> 100,193 | 469,146 -> 474,031 | -1,392,026 -> -1,371,099 | 744 (4,892) | 1.07 | 19,459 | -509 | -884 (c 0.91) | 105.86 -> 113.16 | 1,470 |

### Re-entry / opportunity decomposition ($/wk research lots): same trades (sizing / flatten effect on trades taken in both worlds) | admitted only in the rule world ("re-entry in") | dropped by the rule world ("out") | flagged (reduced) trades: P&L at full size and as sized
| cell | win | same trades | re-entry in | out | in trades/wk | out trades/wk | flagged/wk | flagged P&L full size | flagged P&L as sized |
|---|---|---|---|---|---|---|---|---|---|
| HR_wkF_thuvirt4R_rf0.5 | L6M | 0 | 0 | -0 | 0.00 | 0.00 | 0.00 | 0 | 0 |
| HR_wkF_thuvirt4R_rf0.5 | HOLD | 0 | 0 | -0 | 0.00 | 0.00 | 0.00 | 0 | 0 |
| HR_wkF_thuvirt4R_rf0.5 | PRE | 0 | 0 | -0 | 0.00 | 0.00 | 0.00 | 0 | 0 |
| HR_wkF_thuvirt4R_rf0.5 | X' | 0 | 0 | -0 | 0.00 | 0.00 | 0.00 | 0 | 0 |
| HR_all_sess_rf0.5 | L6M | 0 | 4,237 | -0 | 59.68 | 0.00 | 0.00 | 0 | 0 |
| HR_all_sess_rf0.5 | HOLD | 171 | 2,523 | -0 | 54.97 | 0.00 | 0.00 | 0 | 0 |
| HR_all_sess_rf0.5 | PRE | 0 | -2,055 | -0 | 48.11 | 0.00 | 0.00 | 0 | 0 |
| HR_all_sess_rf0.5 | X' | 0 | 744 | -0 | 7.30 | 0.00 | 0.00 | 0 | 0 |

### Placebos at the same fire rate (random resume timing, 30 seeds): rank of the real cell among the draws (1.00 = real beats all); excess = after the lot-factor line
| cell | L3M excess/d rank | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| HR_wkF_thuvirt4R_rf0.5 | n/a (the rule only re-admits trades; no suppression to randomise) | n/a (the rule only re-admits trades; no suppression to randomise) | n/a (the rule only re-admits trades; no suppression to randomise) | n/a (the rule only re-admits trades; no suppression to randomise) | n/a (the rule only re-admits trades; no suppression to randomise) |
| HR_all_sess_rf0.5 | 0.50 / 0.50 (placebo mean excess -20,827) | 0.87 / 0.53 (placebo mean excess -34,060) | 0.83 / 0.57 (placebo mean excess -27,072) | 1.00 / 0.90 (placebo mean excess -28,030) | 0.97 / 0.67 (placebo mean excess -1,932) |

### Other fill bases (selected cells re-run; d vs the stack on the same basis, research $/wk; excess in brackets)
| cell | basis | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| HR_wkF_thuvirt4R_rf0.5 | N | 0 (0) | 0 (0) | 0 (0) | 0 (0) | 0 (0) |
| HR_wkF_thuvirt4R_rf0.5 | M | 0 (0) | 0 (0) | 0 (0) | 0 (0) | 0 (0) |
| HR_wkF_thuvirt4R_rf0.5 | LIVE-CAL | 0 (0) | 0 (0) | 0 (0) | 0 (0) | 0 (0) |
| HR_all_sess_rf0.5 | N | -600 (-20,494) | 4,237 (-31,340) | 2,694 (-25,113) | -2,055 (-24,307) | 744 (-509) |
| HR_all_sess_rf0.5 | M | -13,199 (-3,670) | -4,219 (-17,164) | -4,717 (-12,223) | -7,955 (-19,776) | 303 (-215) |
| HR_all_sess_rf0.5 | LIVE-CAL | -3,214 (-12,625) | 2,151 (-26,919) | 624 (-21,377) | -4,985 (-23,027) | 623 (-18) |

### Per-session split of the delta (entry session of the affected row; $/wk, research lots | LIVE lots), L6M and PRE
| cell | win | asia (res / live) | london (res / live) | pre (res / live) | nyam (res / live) | nypm (res / live) | close (res / live) |
|---|---|---|---|---|---|---|---|
| HR_wkF_thuvirt4R_rf0.5 | L6M | -0 / -0 | -0 / -0 | -0 / -0 | -0 / 0 | -0 / 0 | -0 / -0 |
| HR_wkF_thuvirt4R_rf0.5 | PRE | -0 / -0 | -0 / -0 | -0 / -0 | -0 / -0 | -0 / -0 | 0 / -0 |
| HR_all_sess_rf0.5 | L6M | -0 / -0 | 1,417 / 682 | 2,439 / 622 | 2,311 / -1,425 | -2,134 / 222 | 204 / -13 |
| HR_all_sess_rf0.5 | PRE | -0 / -0 | -1,295 / -1,104 | -615 / -583 | 3,079 / 483 | -3,134 / -147 | -89 / -19 |

### QUANT-LAYER columns (program: 24 cells, cumulative with earlier programs 2890336)
White RC p (best cell, PRE u X' weeks / selection frame) = 0.23 (studentised 0.41); over all weeks to 2026-02-06 = 0.23 (studentised 0.32); Romano-Wolf survivors: selection frame none, all weeks none; PBO (CSCV, S=10, daily deltas) = 0.25; minimum backtest length for 24 trials at annual SR 1 = 3.9 years.

| cell | d L6M [week-block 95% CI] | d L3M / L6M / HOLD / PRE / X' | trades/wk | RW p (sel / all) | DSR (sel / all / cumulative) | NW t (L6M / all) | longest losing-delta run (wks) | top-5% share of gain (L6M) | corr(d, stack) L6M / all | quarters d>0 | marginal worst-20 (WF) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| HR_wkF_thuvirt4R_rf0.5 | 0 [0, 0] | 0 / 0 / 0 / 0 / 0 | 128.71 | 1.00 / 1.00 | nan / nan / nan | 0.00 / 0.00 | 0 | n/a (net loss) | nan / nan | 0/12 | 0 |
| HR_all_sess_rf0.5 | 4,237 [-18,940, 22,627] | -600 / 4,237 / 2,694 / -2,055 / 744 | 188.39 | 0.96 / 0.91 | 0.01 / 0.02 / 0.00 | 0.40 / -0.09 | 7 | 14.68 | 0.21 / 0.12 | 6/12 | -292,402 |

Breakeven slippage / capacity: not applicable for sizing, skipping and halt rules that change no fill, price or level: they add or remove whole planned trades (lot factor lam <= ~1.36 of the planned lots, never above the planned lot per trade except where lam>1 comes from re-admitted trades); costs per lot are unchanged. Latency: decisions use closed trades only (causal), so a 1-3 s delay does not alter them.



# Addendum: tighter week floors (6R / 4R)
### The stack as it is (S73 70/30 split, six engine books, lock engine day +5R/-2R, arm 2R keep 50%, week floor 12R; N basis; research lots and LIVE lots)
| window | weeks | mean $/wk | SD | maxDD | worst-20 sum | trades/wk | LIVE-lot mean $/wk |
|---|---|---|---|---|---|---|---|
| L3M | 14 | 31,261 | 130,314 | 318,846 | 437,655 | 126.71 | 15,161 |
| L6M | 28 | 79,055 | 136,536 | 318,846 | 332,332 | 128.71 | 29,957 |
| HOLD | 32 | 66,693 | 169,113 | 624,547 | -630,207 | 127.41 | 26,161 |
| PRE | 75 | 61,831 | 138,576 | 614,903 | -2,304,704 | 129.47 | 22,902 |
| X' | 44 | 18,206 | 101,638 | 469,146 | -1,392,026 | 105.86 | 3,430 |

### Screen: every cell, PRE and X' only (selection frame; recent columns are shown only for the cells in the next section)
lam = rule lots / stack lots; excess = rule mean - lam x stack mean (the lot-factor-matched uniform scaling line; STRUCTURE if <= 0); eq = equal-risk delta (lot factor c solving worst-20 over PRE u X' equal to the stack, c x rule - stack), research-lot $/wk.

| cell | lam PRE | d PRE (MDE) | excess PRE | eq PRE | LIVE d PRE | lam X' | d X' (MDE) | excess X' | eq X' | flagged/wk PRE | carried | recent look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HRX_floor4_thu_rf1 | 1.12 | 8,012 (13,693) | 1,913 | 9,061 | 3,737 | 1.09 | 6,542 (11,358) | 5,667 | 6,836 | 0.00 | Y | Y |
| HRX_floor4_sess_rf0.5 | 1.16 | 6,536 (7,432) | -1,420 | 7,427 | 3,353 | 1.10 | 2,788 (5,444) | 1,790 | 2,985 | 0.00 |  |  |
| HRX_floor6_thu_rf1 | 1.04 | 4,964 (7,016) | 2,949 | 7,749 | 1,971 | 1.02 | 1,421 (2,961) | 1,117 | 2,275 | 0.00 | Y | Y |
| HRX_floor4_thu_rf0.5 | 1.12 | 3,957 (6,863) | -2,170 | 5,937 | 1,845 | 1.09 | 3,193 (5,723) | 2,316 | 3,668 | 0.00 |  |  |
| HRX_floor4_day_rf0.5 | 1.15 | 6,027 (7,055) | -1,402 | 6,464 | 3,076 | 1.09 | 2,648 (5,008) | 1,778 | 2,744 | 0.00 |  |  |
| HRX_floor4_virt4R_rf0.5 | 1.13 | 4,940 (7,071) | -1,538 | 4,777 | 2,146 | 1.07 | 1,502 (4,488) | 768 | 1,469 | 0.00 |  |  |
| HRX_floor6_day_rf0.5 | 1.03 | 2,316 (3,079) | 724 | 4,348 | 1,015 | 1.01 | 895 (1,828) | 673 | 1,528 | 0.00 | Y | Y |
| HRX_floor6_thu_rf0.5 | 1.04 | 2,482 (3,508) | 467 | 4,347 | 985 | 1.02 | 711 (1,481) | 406 | 1,284 | 0.00 | Y | Y |
| HRX_floor4_thuvirt4R_rf0.5 | 1.09 | 2,620 (5,568) | -1,828 | 3,840 | 869 | 1.06 | 1,229 (4,980) | 667 | 1,484 | 0.00 |  |  |
| HRX_floor6_sess_rf0.5 | 1.03 | 2,225 (3,558) | 315 | 3,809 | 952 | 1.02 | 868 (1,598) | 592 | 1,361 | 0.00 | Y | Y |
| HRX_floor4_virt0R_rf0.5 | 1.03 | 616 (2,925) | -1,118 | 1,284 | -343 | 1.01 | 458 (1,474) | 361 | 593 | 0.00 |  |  |
| HRX_floor6_virt4R_rf0.5 | 1.01 | 731 (1,638) | 68 | 987 | 187 | 1.00 | 101 (503) | 65 | 179 | 0.00 | Y | Y |
| HRX_floor6_thuvirt4R_rf0.5 | 1.01 | 731 (1,638) | 113 | 987 | 187 | 1.00 | 101 (503) | 65 | 179 | 0.00 | Y | Y |
| HRX_floor6_virt0R_rf0.5 | 1.00 | -36 (259) | -65 | -153 | 18 | 1.00 | 0 (0) | 0 | -36 | 0.00 |  |  |

### The single recent look: stack weekly mean / SD / maxDD / worst-20 weeks, recent-first, rule vs the stack as it is
Columns: stack $/wk base -> rule; SD; maxDD; worst-20 sum (sum of the worst min(20, weeks) weeks; L3M has 14 and L6M 28 weeks, so those two are not comparable with the 75-week PRE) (research lots); d = rule - stack with MDE (2.8 SE of the paired weekly delta); lam; uniform = lam x stack mean; excess = rule - uniform; eqWF = equal-risk delta with c solving worst-20 over WF (PRE u HOLD) equal to the stack (c shown); trades/wk; LIVE-lot $/wk d.

#### HRX_floor4_thu_rf1  (week floor 4R, resume thu_rf1 (vs same floor no resume))  engine fires (day arm / week floor, all windows, per book ST HM WT KB SM PE)=[(191, 42), (161, 40), (233, 49), (185, 42), (35, 19), (198, 33)], entry-test resumes=0, stage resumes day/week=0/207, iterations to a stable traded set=1
| window | mean | SD | maxDD | worst-20 | d (MDE) | lam | uniform line | excess | eqWF | trades/wk | LIVE d |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 33,853 -> 32,050 | 118,465 -> 127,166 | 328,378 -> 331,050 | 473,944 -> 448,694 | -1,804 (27,211) | 1.08 | 36,419 | -4,369 | -4,172 (c 0.93) | 116.36 -> 125.50 | -1,873 |
| L6M | 73,645 -> 76,402 | 129,483 -> 138,196 | 328,378 -> 331,050 | 256,888 -> 263,565 | 2,757 (19,169) | 1.06 | 78,394 | -1,992 | -2,889 (c 0.93) | 118.89 -> 126.93 | -28 |
| HOLD | 68,570 -> 66,562 | 149,520 -> 163,669 | 380,429 -> 527,046 | -452,114 -> -589,006 | -2,009 (19,182) | 1.07 | 73,221 | -6,659 | -6,927 (c 0.93) | 116.75 -> 125.03 | -1,417 |
| PRE | 50,272 -> 58,284 | 133,847 -> 133,933 | 597,890 -> 549,913 | -2,329,324 -> -2,171,600 | 8,012 (13,693) | 1.12 | 56,371 | 1,913 | 3,705 (c 0.93) | 111.19 -> 124.53 | 3,737 |
| X' | 9,799 -> 16,342 | 93,635 -> 97,859 | 582,490 -> 464,511 | -1,453,269 -> -1,374,442 | 6,542 (11,358) | 1.09 | 10,675 | 5,667 | 5,335 (c 0.93) | 95.14 -> 103.77 | 482 |

vs the stack as it is (12R floor), research $/wk: L3M 788 (MDE 9,762); L6M -2,653 (MDE 7,148); HOLD -131 (MDE 8,926); PRE -3,547 (MDE 9,514); X' -1,864 (MDE 7,296)

#### HRX_floor6_thu_rf1  (week floor 6R, resume thu_rf1 (vs same floor no resume))  engine fires (day arm / week floor, all windows, per book ST HM WT KB SM PE)=[(191, 14), (161, 14), (233, 17), (185, 16), (35, 3), (198, 13)], entry-test resumes=0, stage resumes day/week=0/68, iterations to a stable traded set=1
| window | mean | SD | maxDD | worst-20 | d (MDE) | lam | uniform line | excess | eqWF | trades/wk | LIVE d |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 28,963 -> 33,154 | 128,436 -> 128,078 | 318,846 -> 318,846 | 405,481 -> 464,156 | 4,191 (17,621) | 1.02 | 29,649 | 3,505 | 4,287 (c 1.00) | 123.57 -> 126.71 | 3,427 |
| L6M | 78,267 -> 80,666 | 136,060 -> 134,408 | 318,846 -> 318,846 | 310,252 -> 377,430 | 2,399 (8,807) | 1.01 | 79,396 | 1,270 | 2,633 (c 1.00) | 126.57 -> 128.57 | 1,851 |
| HOLD | 69,819 -> 68,798 | 160,812 -> 166,277 | 504,643 -> 602,274 | -530,162 -> -562,836 | -1,021 (11,705) | 1.02 | 71,171 | -2,373 | -822 (c 1.00) | 124.78 -> 127.25 | 532 |
| PRE | 56,564 -> 61,527 | 141,411 -> 138,735 | 558,233 -> 605,845 | -2,486,551 -> -2,318,419 | 4,964 (7,016) | 1.04 | 58,579 | 2,949 | 5,142 (c 1.00) | 124.99 -> 129.31 | 1,971 |
| X' | 17,447 -> 18,868 | 101,877 -> 100,620 | 467,576 -> 462,757 | -1,407,784 -> -1,369,285 | 1,421 (2,961) | 1.02 | 17,751 | 1,117 | 1,476 (c 1.00) | 103.86 -> 105.84 | -43 |

vs the stack as it is (12R floor), research $/wk: L3M 1,893 (MDE 2,490); L6M 1,611 (MDE 1,837); HOLD 2,105 (MDE 2,056); PRE -303 (MDE 1,365); X' 662 (MDE 1,745)

#### HRX_floor6_day_rf0.5  (week floor 6R, resume day_rf0.5 (vs same floor no resume))  engine fires (day arm / week floor, all windows, per book ST HM WT KB SM PE)=[(191, 14), (161, 14), (233, 17), (185, 16), (35, 3), (198, 13)], entry-test resumes=0, stage resumes day/week=0/50, iterations to a stable traded set=1
| window | mean | SD | maxDD | worst-20 | d (MDE) | lam | uniform line | excess | eqWF | trades/wk | LIVE d |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 28,963 -> 29,838 | 128,436 -> 128,134 | 318,846 -> 318,846 | 405,481 -> 417,731 | 875 (5,024) | 1.02 | 29,562 | 276 | 1,224 (c 1.01) | 123.57 -> 126.21 | 188 |
| L6M | 78,267 -> 78,625 | 136,060 -> 135,762 | 318,846 -> 318,846 | 310,252 -> 320,291 | 359 (2,490) | 1.01 | 79,136 | -511 | 1,278 (c 1.01) | 126.57 -> 128.07 | 64 |
| HOLD | 69,819 -> 68,972 | 160,812 -> 162,694 | 504,643 -> 540,689 | -530,162 -> -557,280 | -847 (3,450) | 1.01 | 70,801 | -1,829 | -41 (c 1.01) | 124.78 -> 126.56 | -384 |
| PRE | 56,564 -> 58,880 | 141,411 -> 139,814 | 558,233 -> 568,811 | -2,486,551 -> -2,396,715 | 2,316 (3,079) | 1.03 | 58,156 | 724 | 3,005 (c 1.01) | 124.99 -> 128.39 | 1,015 |
| X' | 17,447 -> 18,341 | 101,877 -> 100,653 | 467,576 -> 475,686 | -1,407,784 -> -1,381,537 | 895 (1,828) | 1.01 | 17,668 | 673 | 1,109 (c 1.01) | 103.86 -> 105.23 | 220 |

vs the stack as it is (12R floor), research $/wk: L3M -1,423 (MDE 12,793); L6M -430 (MDE 6,343); HOLD 2,279 (MDE 9,282); PRE -2,950 (MDE 4,965); X' 136 (MDE 1,913)

#### HRX_floor6_thu_rf0.5  (week floor 6R, resume thu_rf0.5 (vs same floor no resume))  engine fires (day arm / week floor, all windows, per book ST HM WT KB SM PE)=[(191, 14), (161, 14), (233, 17), (185, 16), (35, 3), (198, 13)], entry-test resumes=0, stage resumes day/week=0/68, iterations to a stable traded set=1
| window | mean | SD | maxDD | worst-20 | d (MDE) | lam | uniform line | excess | eqWF | trades/wk | LIVE d |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 28,963 -> 31,058 | 128,436 -> 127,716 | 318,846 -> 318,846 | 405,481 -> 434,819 | 2,096 (8,811) | 1.02 | 29,649 | 1,409 | 2,405 (c 1.01) | 123.57 -> 126.71 | 1,714 |
| L6M | 78,267 -> 79,466 | 136,060 -> 134,981 | 318,846 -> 318,846 | 310,252 -> 343,841 | 1,200 (4,404) | 1.01 | 79,396 | 70 | 1,992 (c 1.01) | 126.57 -> 128.57 | 925 |
| HOLD | 69,819 -> 69,309 | 160,812 -> 163,139 | 504,643 -> 553,458 | -530,162 -> -546,499 | -511 (5,853) | 1.02 | 71,171 | -1,862 | 181 (c 1.01) | 124.78 -> 127.25 | 266 |
| PRE | 56,564 -> 59,046 | 141,411 -> 139,659 | 558,233 -> 576,578 | -2,486,551 -> -2,398,055 | 2,482 (3,508) | 1.04 | 58,579 | 467 | 3,071 (c 1.01) | 124.99 -> 129.31 | 985 |
| X' | 17,447 -> 18,157 | 101,877 -> 101,190 | 467,576 -> 465,167 | -1,407,784 -> -1,387,971 | 711 (1,481) | 1.02 | 17,751 | 406 | 892 (c 1.01) | 103.86 -> 105.84 | -22 |

vs the stack as it is (12R floor), research $/wk: L3M -203 (MDE 8,823); L6M 411 (MDE 4,446); HOLD 2,616 (MDE 6,869); PRE -2,785 (MDE 4,200); X' -48 (MDE 1,395)

#### HRX_floor6_sess_rf0.5  (week floor 6R, resume sess_rf0.5 (vs same floor no resume))  engine fires (day arm / week floor, all windows, per book ST HM WT KB SM PE)=[(191, 14), (161, 14), (233, 17), (185, 16), (35, 3), (198, 13)], entry-test resumes=0, stage resumes day/week=0/63, iterations to a stable traded set=1
| window | mean | SD | maxDD | worst-20 | d (MDE) | lam | uniform line | excess | eqWF | trades/wk | LIVE d |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 28,963 -> 31,061 | 128,436 -> 127,308 | 318,846 -> 318,846 | 405,481 -> 434,855 | 2,098 (8,103) | 1.02 | 29,625 | 1,437 | 2,396 (c 1.01) | 123.57 -> 126.57 | 1,717 |
| L6M | 78,267 -> 79,153 | 136,060 -> 134,947 | 318,846 -> 318,846 | 310,252 -> 335,084 | 887 (4,142) | 1.01 | 79,404 | -250 | 1,646 (c 1.01) | 126.57 -> 128.61 | 802 |
| HOLD | 69,819 -> 69,560 | 160,812 -> 162,129 | 504,643 -> 536,671 | -530,162 -> -538,469 | -260 (4,952) | 1.02 | 71,106 | -1,546 | 407 (c 1.01) | 124.78 -> 127.16 | 288 |
| PRE | 56,564 -> 58,788 | 141,411 -> 140,260 | 558,233 -> 579,991 | -2,486,551 -> -2,417,310 | 2,225 (3,558) | 1.03 | 58,474 | 315 | 2,788 (c 1.01) | 124.99 -> 129.13 | 952 |
| X' | 17,447 -> 18,314 | 101,877 -> 100,957 | 467,576 -> 469,531 | -1,407,784 -> -1,381,901 | 868 (1,598) | 1.02 | 17,722 | 592 | 1,043 (c 1.01) | 103.86 -> 105.64 | 249 |

vs the stack as it is (12R floor), research $/wk: L3M -200 (MDE 9,681); L6M 98 (MDE 4,773); HOLD 2,867 (MDE 7,908); PRE -3,042 (MDE 4,349); X' 109 (MDE 1,561)

#### HRX_floor6_virt4R_rf0.5  (week floor 6R, resume virt4R_rf0.5 (vs same floor no resume))  engine fires (day arm / week floor, all windows, per book ST HM WT KB SM PE)=[(191, 14), (161, 14), (233, 17), (185, 16), (35, 3), (198, 13)], entry-test resumes=0, stage resumes day/week=0/27, iterations to a stable traded set=1
| window | mean | SD | maxDD | worst-20 | d (MDE) | lam | uniform line | excess | eqWF | trades/wk | LIVE d |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 28,963 -> 29,713 | 128,436 -> 127,460 | 318,846 -> 318,846 | 405,481 -> 415,984 | 750 (3,025) | 1.01 | 29,313 | 400 | 781 (c 1.00) | 123.57 -> 124.86 | 760 |
| L6M | 78,267 -> 78,645 | 136,060 -> 135,472 | 318,846 -> 318,846 | 310,252 -> 320,838 | 378 (1,498) | 1.01 | 78,771 | -126 | 458 (c 1.00) | 126.57 -> 127.29 | 381 |
| HOLD | 69,819 -> 69,959 | 160,812 -> 160,640 | 504,643 -> 510,770 | -530,162 -> -525,704 | 139 (1,426) | 1.01 | 70,242 | -283 | 211 (c 1.00) | 124.78 -> 125.44 | 295 |
| PRE | 56,564 -> 57,295 | 141,411 -> 141,328 | 558,233 -> 558,233 | -2,486,551 -> -2,468,483 | 731 (1,638) | 1.01 | 57,227 | 68 | 790 (c 1.00) | 124.99 -> 126.48 | 187 |
| X' | 17,447 -> 17,548 | 101,877 -> 101,539 | 467,576 -> 467,576 | -1,407,784 -> -1,402,756 | 101 (503) | 1.00 | 17,483 | 65 | 119 (c 1.00) | 103.86 -> 104.09 | -48 |

vs the stack as it is (12R floor), research $/wk: L3M -1,548 (MDE 14,939); L6M -411 (MDE 7,418); HOLD 3,266 (MDE 12,050); PRE -4,536 (MDE 6,735); X' -658 (MDE 2,267)

#### HRX_floor6_thuvirt4R_rf0.5  (week floor 6R, resume thuvirt4R_rf0.5 (vs same floor no resume))  engine fires (day arm / week floor, all windows, per book ST HM WT KB SM PE)=[(191, 14), (161, 14), (233, 17), (185, 16), (35, 3), (198, 13)], entry-test resumes=0, stage resumes day/week=0/27, iterations to a stable traded set=1
| window | mean | SD | maxDD | worst-20 | d (MDE) | lam | uniform line | excess | eqWF | trades/wk | LIVE d |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 28,963 -> 29,713 | 128,436 -> 127,460 | 318,846 -> 318,846 | 405,481 -> 415,984 | 750 (3,025) | 1.01 | 29,313 | 400 | 781 (c 1.00) | 123.57 -> 124.86 | 760 |
| L6M | 78,267 -> 78,645 | 136,060 -> 135,472 | 318,846 -> 318,846 | 310,252 -> 320,838 | 378 (1,498) | 1.01 | 78,771 | -126 | 458 (c 1.00) | 126.57 -> 127.29 | 381 |
| HOLD | 69,819 -> 69,959 | 160,812 -> 160,640 | 504,643 -> 510,770 | -530,162 -> -525,704 | 139 (1,426) | 1.01 | 70,242 | -283 | 211 (c 1.00) | 124.78 -> 125.44 | 295 |
| PRE | 56,564 -> 57,295 | 141,411 -> 141,328 | 558,233 -> 558,233 | -2,486,551 -> -2,468,483 | 731 (1,638) | 1.01 | 57,182 | 113 | 790 (c 1.00) | 124.99 -> 126.37 | 187 |
| X' | 17,447 -> 17,548 | 101,877 -> 101,539 | 467,576 -> 467,576 | -1,407,784 -> -1,402,756 | 101 (503) | 1.00 | 17,483 | 65 | 119 (c 1.00) | 103.86 -> 104.09 | -48 |

vs the stack as it is (12R floor), research $/wk: L3M -1,548 (MDE 14,939); L6M -411 (MDE 7,418); HOLD 3,266 (MDE 12,050); PRE -4,536 (MDE 6,735); X' -658 (MDE 2,267)

### Re-entry / opportunity decomposition ($/wk research lots): same trades (sizing / flatten effect on trades taken in both worlds) | admitted only in the rule world ("re-entry in") | dropped by the rule world ("out") | flagged (reduced) trades: P&L at full size and as sized
| cell | win | same trades | re-entry in | out | in trades/wk | out trades/wk | flagged/wk | flagged P&L full size | flagged P&L as sized |
|---|---|---|---|---|---|---|---|---|---|
| HRX_floor4_thu_rf1 | L6M | 0 | 2,757 | -0 | 8.04 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor4_thu_rf1 | HOLD | 0 | -2,009 | -0 | 8.28 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor4_thu_rf1 | PRE | 0 | 8,012 | -0 | 13.35 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor4_thu_rf1 | X' | 0 | 6,542 | -0 | 8.64 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_thu_rf1 | L6M | 0 | 2,399 | -0 | 2.00 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_thu_rf1 | HOLD | 0 | -1,021 | -0 | 2.47 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_thu_rf1 | PRE | 0 | 4,964 | -0 | 4.32 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_thu_rf1 | X' | 0 | 1,421 | -0 | 1.98 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_day_rf0.5 | L6M | 0 | 359 | -0 | 1.50 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_day_rf0.5 | HOLD | 0 | -847 | -0 | 1.78 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_day_rf0.5 | PRE | 0 | 2,316 | -0 | 3.40 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_day_rf0.5 | X' | 0 | 895 | -0 | 1.36 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_thu_rf0.5 | L6M | 0 | 1,200 | -0 | 2.00 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_thu_rf0.5 | HOLD | 0 | -511 | -0 | 2.47 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_thu_rf0.5 | PRE | 0 | 2,482 | -0 | 4.32 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_thu_rf0.5 | X' | 0 | 711 | -0 | 1.98 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_sess_rf0.5 | L6M | 0 | 887 | -0 | 2.04 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_sess_rf0.5 | HOLD | 0 | -260 | -0 | 2.38 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_sess_rf0.5 | PRE | 0 | 2,225 | -0 | 4.15 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_sess_rf0.5 | X' | 0 | 868 | -0 | 1.77 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_virt4R_rf0.5 | L6M | 0 | 378 | -0 | 0.71 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_virt4R_rf0.5 | HOLD | 0 | 139 | -0 | 0.66 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_virt4R_rf0.5 | PRE | 0 | 731 | -0 | 1.49 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_virt4R_rf0.5 | X' | 0 | 101 | -0 | 0.23 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_thuvirt4R_rf0.5 | L6M | 0 | 378 | -0 | 0.71 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_thuvirt4R_rf0.5 | HOLD | 0 | 139 | -0 | 0.66 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_thuvirt4R_rf0.5 | PRE | 0 | 731 | -0 | 1.39 | 0.00 | 0.00 | 0 | 0 |
| HRX_floor6_thuvirt4R_rf0.5 | X' | 0 | 101 | -0 | 0.23 | 0.00 | 0.00 | 0 | 0 |

### Placebos at the same fire rate (random resume timing, 30 seeds): rank of the real cell among the draws (1.00 = real beats all); excess = after the lot-factor line
| cell | L3M excess/d rank | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| HRX_floor4_thu_rf1 | 0.93 / 0.93 (placebo mean excess -7,470) | 0.93 / 0.97 (placebo mean excess -4,320) | 0.60 / 0.90 (placebo mean excess -7,244) | 1.00 / 1.00 (placebo mean excess -1,303) | 1.00 / 1.00 (placebo mean excess 800) |
| HRX_floor6_thu_rf1 | 0.97 / 0.97 (placebo mean excess -570) | 0.97 / 0.97 (placebo mean excess -929) | 0.80 / 0.93 (placebo mean excess -3,262) | 1.00 / 1.00 (placebo mean excess -12) | 0.80 / 0.83 (placebo mean excess 619) |
| HRX_floor6_day_rf0.5 | 0.87 / 0.87 (placebo mean excess -468) | 0.83 / 0.87 (placebo mean excess -782) | 0.60 / 0.77 (placebo mean excess -2,021) | 1.00 / 1.00 (placebo mean excess -584) | 1.00 / 1.00 (placebo mean excess 218) |
| HRX_floor6_thu_rf0.5 | 0.97 / 0.97 (placebo mean excess -468) | 0.97 / 0.97 (placebo mean excess -782) | 0.57 / 0.93 (placebo mean excess -2,021) | 1.00 / 1.00 (placebo mean excess -584) | 0.73 / 0.83 (placebo mean excess 218) |
| HRX_floor6_sess_rf0.5 | 0.97 / 0.97 (placebo mean excess -468) | 0.97 / 0.97 (placebo mean excess -782) | 0.83 / 0.97 (placebo mean excess -2,021) | 0.97 / 1.00 (placebo mean excess -584) | 0.97 / 1.00 (placebo mean excess 218) |
| HRX_floor6_virt4R_rf0.5 | 0.87 / 0.87 (placebo mean excess -468) | 0.97 / 0.87 (placebo mean excess -782) | 1.00 / 1.00 (placebo mean excess -2,021) | 0.97 / 0.63 (placebo mean excess -584) | 0.23 / 0.17 (placebo mean excess 218) |
| HRX_floor6_thuvirt4R_rf0.5 | 0.87 / 0.87 (placebo mean excess -468) | 0.97 / 0.87 (placebo mean excess -782) | 1.00 / 1.00 (placebo mean excess -2,021) | 0.97 / 0.63 (placebo mean excess -584) | 0.23 / 0.17 (placebo mean excess 218) |

### Other fill bases (selected cells re-run; d vs the stack on the same basis, research $/wk; excess in brackets)
| cell | basis | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| HRX_floor4_thu_rf1 | N | -1,804 (-4,369) | 2,757 (-1,992) | -2,009 (-6,659) | 8,012 (1,913) | 6,542 (5,667) |
| HRX_floor4_thu_rf1 | M | -10,406 (-9,845) | -5,433 (-8,128) | -9,560 (-11,967) | 5,602 (1,716) | 5,984 (5,928) |
| HRX_floor4_thu_rf1 | LIVE-CAL | -2,441 (-3,975) | 2,049 (-2,054) | -1,898 (-5,943) | 5,820 (458) | 5,715 (5,487) |
| HRX_floor6_thu_rf1 | N | 4,191 (3,505) | 2,399 (1,270) | -1,021 (-2,373) | 4,964 (2,949) | 1,421 (1,117) |
| HRX_floor6_thu_rf1 | M | 369 (907) | -272 (-973) | -3,656 (-4,308) | 4,175 (2,832) | 1,598 (1,458) |
| HRX_floor6_thu_rf1 | LIVE-CAL | 3,559 (3,209) | 1,624 (609) | -2,211 (-3,403) | 4,559 (2,559) | 1,199 (1,000) |
| HRX_floor6_day_rf0.5 | N | 875 (276) | 359 (-511) | -847 (-1,829) | 2,316 (724) | 895 (673) |
| HRX_floor6_day_rf0.5 | M | 1,054 (1,426) | 439 (6) | -804 (-1,207) | 1,644 (573) | 684 (587) |
| HRX_floor6_day_rf0.5 | LIVE-CAL | 752 (464) | 291 (-434) | -1,478 (-2,347) | 1,797 (263) | 235 (95) |
| HRX_floor6_thu_rf0.5 | N | 2,096 (1,409) | 1,200 (70) | -511 (-1,862) | 2,482 (467) | 711 (406) |
| HRX_floor6_thu_rf0.5 | M | 185 (723) | -136 (-838) | -1,828 (-2,480) | 2,087 (745) | 799 (659) |
| HRX_floor6_thu_rf0.5 | LIVE-CAL | 1,780 (1,429) | 812 (-203) | -1,105 (-2,298) | 2,279 (280) | 599 (400) |
| HRX_floor6_sess_rf0.5 | N | 2,098 (1,437) | 887 (-250) | -260 (-1,546) | 2,225 (315) | 868 (592) |
| HRX_floor6_sess_rf0.5 | M | 607 (1,097) | -17 (-672) | -1,199 (-1,793) | 1,734 (440) | 731 (606) |
| HRX_floor6_sess_rf0.5 | LIVE-CAL | 1,723 (1,400) | 686 (-276) | -816 (-1,928) | 1,895 (-16) | 299 (125) |
| HRX_floor6_virt4R_rf0.5 | N | 750 (400) | 378 (-126) | 139 (-283) | 731 (68) | 101 (65) |
| HRX_floor6_virt4R_rf0.5 | M | -248 (-56) | -304 (-538) | -458 (-626) | 529 (37) | 69 (53) |
| HRX_floor6_virt4R_rf0.5 | LIVE-CAL | 981 (802) | 412 (-17) | 164 (-190) | 229 (-682) | 145 (124) |
| HRX_floor6_thuvirt4R_rf0.5 | N | 750 (400) | 378 (-126) | 139 (-283) | 731 (113) | 101 (65) |
| HRX_floor6_thuvirt4R_rf0.5 | M | -248 (-56) | -304 (-538) | -458 (-626) | 731 (348) | 69 (53) |
| HRX_floor6_thuvirt4R_rf0.5 | LIVE-CAL | 981 (802) | 412 (-17) | 164 (-190) | 411 (-332) | 145 (124) |

### Per-session split of the delta (entry session of the affected row; $/wk, research lots | LIVE lots), L6M and PRE
| cell | win | asia (res / live) | london (res / live) | pre (res / live) | nyam (res / live) | nypm (res / live) | close (res / live) |
|---|---|---|---|---|---|---|---|
| HRX_floor4_thu_rf1 | L6M | 698 / -891 | 3,057 / 1,536 | -1,920 / -816 | 2,156 / 494 | -1,234 / -351 | -0 / -0 |
| HRX_floor4_thu_rf1 | PRE | 2,486 / 1,502 | 2,430 / 673 | 509 / 232 | 1,042 / 844 | 1,641 / 486 | -96 / -0 |
| HRX_floor6_thu_rf1 | L6M | 1,570 / 625 | 906 / 390 | -455 / -175 | 775 / 1,169 | -397 / -158 | -0 / -0 |
| HRX_floor6_thu_rf1 | PRE | 1,568 / 698 | 2,046 / 676 | 325 / 11 | 978 / 544 | 46 / 42 | 0 / -0 |
| HRX_floor6_day_rf0.5 | L6M | 701 / 278 | 361 / 56 | -228 / -88 | -360 / -139 | -116 / -44 | -0 / -0 |
| HRX_floor6_day_rf0.5 | PRE | 749 / 295 | 1,191 / 405 | 92 / 51 | 250 / 231 | 34 / 34 | 0 / -0 |
| HRX_floor6_thu_rf0.5 | L6M | 785 / 312 | 453 / 195 | -228 / -88 | 388 / 584 | -198 / -79 | -0 / -0 |
| HRX_floor6_thu_rf0.5 | PRE | 784 / 349 | 1,023 / 338 | 162 / 6 | 489 / 272 | 23 / 21 | 0 / -0 |
| HRX_floor6_sess_rf0.5 | L6M | 701 / 278 | 338 / 151 | -228 / -88 | 274 / 541 | -198 / -79 | -0 / -0 |
| HRX_floor6_sess_rf0.5 | PRE | 749 / 295 | 1,014 / 373 | 152 / 38 | 344 / 244 | -35 / 2 | 0 / -0 |
| HRX_floor6_virt4R_rf0.5 | L6M | -71 / -28 | 215 / -0 | -114 / -44 | 432 / 489 | -85 / -35 | -0 / -0 |
| HRX_floor6_virt4R_rf0.5 | PRE | 5 / -47 | 822 / 230 | -1 / -17 | 105 / -13 | -200 / 33 | 0 / -0 |
| HRX_floor6_thuvirt4R_rf0.5 | L6M | -71 / -28 | 215 / -0 | -114 / -44 | 432 / 489 | -85 / -35 | -0 / -0 |
| HRX_floor6_thuvirt4R_rf0.5 | PRE | -92 / -88 | 822 / 230 | -1 / -17 | 191 / 24 | -189 / 38 | 0 / -0 |

### QUANT-LAYER columns (program: 14 cells, cumulative with earlier programs 2890206)
White RC p (best cell, PRE u X' weeks / selection frame) = 0.02 (studentised 0.02); over all weeks to 2026-02-06 = 0.05 (studentised 0.07); Romano-Wolf survivors: selection frame ['HRX_floor4_sess_rf0.5', 'HRX_floor4_day_rf0.5'], all weeks none; PBO (CSCV, S=10, daily deltas) = 0.77; minimum backtest length for 14 trials at annual SR 1 = 3.0 years.

| cell | d L6M [week-block 95% CI] | d L3M / L6M / HOLD / PRE / X' | trades/wk | RW p (sel / all) | DSR (sel / all / cumulative) | NW t (L6M / all) | longest losing-delta run (wks) | top-5% share of gain (L6M) | corr(d, stack) L6M / all | quarters d>0 | marginal worst-20 (WF) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| HRX_floor4_thu_rf1 | 2,757 [-7,782, 12,512] | -1,804 / 2,757 / -2,009 / 8,012 / 6,542 | 126.93 | 0.06 / 0.19 | 0.90 / 0.72 / 0.02 | 0.52 / 2.00 | 4 | 11.65 | 0.34 / 0.23 | 8/12 | -500,866 |
| HRX_floor6_thu_rf1 | 2,399 [-1,051, 7,239] | 4,191 / 2,399 / -1,021 / 4,964 / 1,421 | 128.57 | 0.06 / 0.20 | 0.93 / 0.69 / 0.02 | 1.09 / 1.48 | 2 | 3.68 | -0.04 / 0.07 | 7/12 | -145,019 |
| HRX_floor6_day_rf0.5 | 359 [-612, 1,452] | 875 / 359 / -847 / 2,316 / 895 | 128.07 | 0.05 / 0.15 | 0.98 / 0.80 / 0.02 | 0.71 / 1.50 | 3 | 9.07 | 0.03 / 0.03 | 7/12 | -36,130 |
| HRX_floor6_thu_rf0.5 | 1,200 [-525, 3,619] | 2,096 / 1,200 / -511 / 2,482 / 711 | 128.57 | 0.06 / 0.20 | 0.93 / 0.69 / 0.02 | 1.09 / 1.48 | 2 | 3.68 | -0.04 / 0.07 | 7/12 | -47,710 |
| HRX_floor6_sess_rf0.5 | 887 [-909, 3,223] | 2,098 / 887 / -260 / 2,225 / 868 | 128.61 | 0.08 / 0.20 | 0.88 / 0.70 / 0.02 | 0.84 / 1.47 | 2 | 4.87 | -0.05 / 0.06 | 8/12 | -42,508 |
| HRX_floor6_virt4R_rf0.5 | 378 [-408, 1,539] | 750 / 378 / 139 / 731 / 101 | 127.29 | 0.27 / 0.30 | 0.60 / 0.54 / 0.01 | 0.74 / 1.07 | 1 | 5.05 | -0.11 / 0.03 | 5/12 | -26,684 |
| HRX_floor6_thuvirt4R_rf0.5 | 378 [-408, 1,539] | 750 / 378 / 139 / 731 / 101 | 127.29 | 0.27 / 0.30 | 0.60 / 0.54 / 0.01 | 0.74 / 1.07 | 1 | 5.05 | -0.11 / 0.03 | 5/12 | -26,684 |

Breakeven slippage / capacity: not applicable for sizing, skipping and halt rules that change no fill, price or level: they add or remove whole planned trades (lot factor lam <= ~1.36 of the planned lots, never above the planned lot per trade except where lam>1 comes from re-admitted trades); costs per lot are unchanged. Latency: decisions use closed trades only (causal), so a 1-3 s delay does not alter them.



## Code / outputs
`l2vast/ds3/code/rhq/`; `l2vast/ds3/out/rhq/hr_*`, `hrx_*`. Prereg sha256 0fa0cd635870969ab4ce7f7ad13011a77a2485987c682001d78ce77a8c12f526, addendum 986c01d2ebac91e85c7bfb854d17f83268dbcef6af15b0d523066842db4626e4.
