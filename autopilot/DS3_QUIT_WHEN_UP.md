# DS3_QUIT_WHEN_UP - RHQ follow-up section 8 (2026-10-31)

**INTERPRETATION IS THE LEAD'S, NOT THE USER'S.** The user's original text for this program never reached the lead (no directive text exists in the logs); the lead supplied the interpretation below. If the user re-pastes the original text, this report is superseded and the cells are re-run with the same machinery (code `l2vast/ds3/code/rhq/`, outputs `l2vast/ds3/out/rhq/`).

Research only; no live/execution/chart change. UNTOUCHED (label day > 20260206) never read. Windows: L3M 20251106.. (view), L6M 20250801.., HOLD 20250701.., PRE 20240201..20250630, X' 20230401..20240131, all capped 20260206. Base = the stack as it is = 70/30 split (S73) on the exact per-book lock engine (day entry test +5R/-2R, day arm 2R keep 50%, week floor 12R in planned-lot R; R = lots x 60 x $20), six engine books ST HM WT KB SM PE, N basis (M and LIVE-CAL beside for the cells that got the recent look). $ shown at research lots (ST10 HM10 WT7 KB5.2 SM7.4 PE5.6) AND at LIVE lots (mapping stated: ST=U6 4 Asia/London; HM=H6 4 Asia / 2 NY-AM; KB=K6 2; SM=M6 2 London/NY-AM; PE=P6 7 Asia/London/NY-AM; WT not live = research/2.35 = 3; pre-market counted with NY-AM and close with NY-PM; per-row live/research scaling of the research-lot outcome, locks evaluated at research lots). Prereg autopilot/RHQ_QUIT_WHEN_UP_prereg.md sha256 dbc0fc90ddf7482bdf2066e03732d568e5caff12694f445e90cda69608ba0d73 (sha256 in DECISIONS.md before any cell was scored). Multiplicity and the cumulative count are in the QUANT block. UF_TRIALS side=rhq_*. 

Lead's interpretation: QUIT-WHEN-UP = stop trading (or halve) after the day (or session / week) is up X R or $Y: book-level engine variants (day +1/2/3/4/6R entry test vs the base +5R, skip or halve; give-back arm 1.5/3/4R, keep .25/.75, arm OFF, 'continue at 50% after the arm' vs the base 'arm 2R keep 50%') and stack-level quits in R (12,000 per R at research lots) and in $ at LIVE lots ($1k / 2k / 4k / 6k), day / session / week, quit (x0) or halve (x0.5). 50 cells (+1 identity control).

## 1. Page 1 - the answer: quitting when up loses; the existing '+5R / arm 2R keep 50%' governors are not beaten

1. **1 of 50 cells carried on PRE and X'** (stack session P&L >= +1R: quit the rest of the session), and it **fails its recent look badly**: d vs the stack L3M -34.9k, L6M -25.2k, HOLD -23.4k per week, PRE -5.3k, X' +0.6k (live lots -17.7k / -12.3k / -10.8k / -1.2k / +3.3k); excess over the lot-factor line -32.1k / -16.1k / -15.9k / +2.5k / +2.0k. A textbook case of PRE+X' selection not carrying forward (placebo rank of its excess 0.04 L3M, 0.41 L6M, 0.32 HOLD, 0.97 PRE, 0.85 X').
2. **The prereg-named canon cells:** stack day P&L >= +2R quit: L3M -40.6k, L6M -44.7k, HOLD -45.0k, PRE -30.6k, X' -8.8k per week (live lots -18.5k / -17.1k / -18.1k / -10.7k / +0.6k); SD falls 136k -> 103k (L6M) but the equal-risk delta (c on worst-20 PRE u HOLD) is -37.8k in L6M, and it is worse than the lot-factor line in every window (-16.1k L6M). Book day entry test +3R (base +5R), skip: -14.2k / -12.3k / -12.3k / -12.5k / -1.1k. 'Continue at x0.5 after the arm' instead of flatten-and-quit (day arm 2R): L3M +6.6k, L6M +3.0k, HOLD +3.3k, PRE +2.6k, X' -2.4k (all inside the MDE 4-20k; live lots +4.9k / +2.9k / +3.1k / -1.0k / +0.3k), at lot factor 1.09-1.34 (it re-admits 30-34 trades/wk): excess over the lot-factor line -3.9k / -17.2k / -12.4k / -11.6k / -4.0k, equal-risk delta +5.5k / +0.8k / +1.4k / +0.8k / -2.8k. Not carried (PRE excess < 0, X' d < 0). Tier: DEAD / STRUCTURE, no LEAD.
3. **Against the existing day arm (2R keep 50%) and the +5R test, from the PRE/X' screen (50 cells; recent look only for the 4 above):** lowering the book entry-test win level below 5R (1, 2, 3, 4R) loses in PRE for both skip and halve (-30.9k .. -3.8k per week), the +6R / OFF variants are +1.3k..+2.9k in PRE and -0.4k in X' (immaterial). Every arm variant flips sign between PRE and X' (PRE / X' d per week: arm 1.5R -10.5k / +2.5k; 3R +6.2k / -8.4k; 4R +5.5k / -10.4k; OFF +1.0k / -10.6k; keep .25 +0.2k / -8.5k; keep .75 -16.4k / +4.7k), so none beats 'arm 2R keep 50%' consistently: the base is not improved by the variants. Stack quits in $ at live lots (quit): PRE d -21.8k..-25.7k per week (research-lot units), halve -6.0k..-10.5k; the quit cells have positive excess over the lot-factor line in BOTH PRE (+5.3k..+13.0k) and X' (+3.2k..+7.9k) because the first trades of a day (before the threshold) earn more per lot than the rest, but they fail the equal-risk gate in PRE (-4.0k..-13.2k: worst-20 falls less than lots) and were therefore not carried.
4. **Why:** the trades a quit removes are better than average. The stack +2R quit drops 46 trades/wk in L6M worth +43.3k/wk ($934 per trade vs $614 for the average stack trade) and 53 trades/wk in PRE worth +30.1k/wk ($568 vs $478): after the day is up, the remaining trades are above-average (trend days continue). Quitting converts that into a smaller mean with a proportionally smaller SD (STRUCTURE).
5. **Sized-lot R governors:** identical for the quit cells (the day's largest multiplier is 1 before the quit), so the sized-lot table repeats the planned-lot numbers. **QUANT:** White RC p 0.96 / 0.95, Romano-Wolf none, PBO 0.00 (the ranking of cells is stable: quit variants are consistently the worst), DSR 0.00, minimum backtest length for 50 trials 5.2 years.
6. **For the Sunday brief:** keep the D6 locks as coded (+5R / -2R day entry tests, arm 2R keep 50%, week floor 12R); do not add a stack-level quit-when-up. Questions (MORNING.md): re-paste the original QUIT-WHEN-UP text if it meant a $-based stop at live lots only for specific books.

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
| QW_arm1.0_cont0.5 | 1.23 | -9,226 (19,915) | -23,334 | 8,632 | -3,161 | 1.09 | 1,808 (17,477) | 241 | 8,602 | 0.00 |  |  |
| QW_stack_sess+1R_halve | 1.00 | -1,687 (17,534) | -1,969 | 5,053 | -1,628 | 0.98 | -225 (12,597) | 181 | 1,790 | 34.17 |  |  |
| QW_stack_day+$4000live_halve | 0.93 | -6,022 (19,514) | -1,448 | 8,312 | -1,544 | 0.87 | -5,191 (15,072) | -2,766 | -1,849 | 91.59 |  |  |
| QW_stack_sess+1R_quit | 0.87 | -5,254 (28,412) | 2,481 | 2,298 | -1,167 | 0.93 | 646 (21,561) | 2,000 | 3,162 | 0.00 | Y | Y |
| QW_stack_day+$1000live_quit | 0.41 | -23,648 (36,795) | 13,048 | -4,503 | -6,705 | 0.53 | -774 (35,147) | 7,716 | 7,966 | 0.00 |  |  |
| QW_stack_sess+2R_halve | 1.01 | -1,740 (15,052) | -2,225 | 1,485 | -730 | 0.99 | -239 (8,685) | 28 | 725 | 21.17 |  |  |
| QW_arm1.5_keep0.5 | 0.84 | -10,542 (18,290) | -861 | -3,641 | -1,665 | 0.92 | 2,462 (13,019) | 3,891 | 5,242 | 0.00 |  |  |
| QW_book_up6R_skip | 1.01 | 2,933 (4,572) | 2,070 | 2,081 | 983 | 1.00 | -374 (1,675) | -400 | -608 | 0.00 |  |  |
| QW_stack_sess+3R_halve | 1.01 | -1,389 (11,518) | -1,825 | -199 | -1,867 | 0.99 | 733 (5,745) | 871 | 1,106 | 13.08 |  |  |
| QW_stack_day+$2000live_halve | 0.92 | -10,007 (18,720) | -5,364 | 648 | -3,429 | 0.85 | -2,921 (17,228) | -188 | 222 | 101.17 |  |  |
| QW_stack_day+$6000live_halve | 0.92 | -8,187 (18,344) | -3,411 | 1,970 | -2,281 | 0.88 | -4,470 (14,654) | -2,235 | -1,869 | 85.80 |  |  |
| QW_book_up6R_halve | 1.04 | 1,440 (5,706) | -866 | 607 | 259 | 1.00 | -374 (1,675) | -400 | -608 | 0.00 |  |  |
| QW_book_up_off | 1.03 | 1,277 (6,439) | -844 | 447 | -121 | 1.00 | -374 (1,675) | -400 | -608 | 0.00 |  |  |
| QW_arm2.0_cont0.5 | 1.23 | 2,555 (8,846) | -11,553 | 1,316 | -1,043 | 1.09 | -2,386 (4,139) | -3,952 | -2,690 | 0.00 |  | Y |
| QW_stack_day+$1000live_halve | 0.92 | -10,535 (19,452) | -5,437 | 443 | -3,324 | 0.84 | -4,897 (17,661) | -1,990 | -2,049 | 103.92 |  |  |
| QW_stack_day+$4000live_quit | 0.48 | -21,816 (34,165) | 10,425 | -4,047 | -6,211 | 0.61 | -3,934 (30,089) | 3,217 | 2,404 | 0.00 |  |  |
| QW_stack_wk+12R_halve | 0.98 | -3,785 (10,594) | -2,651 | -3,785 | -1,772 | 0.98 | 1,514 (4,134) | 1,797 | 1,514 | 36.24 |  |  |
| QW_stack_day+1R_halve | 0.93 | -9,242 (19,312) | -4,752 | -29 | -2,467 | 0.88 | -5,369 (16,439) | -3,161 | -3,121 | 84.85 |  |  |
| QW_stack_wk+8R_halve | 0.97 | -2,546 (13,533) | -422 | -2,386 | -557 | 0.96 | -1,312 (6,871) | -568 | -1,266 | 61.25 |  |  |
| QW_stack_day+3R_halve | 0.97 | -7,092 (13,686) | -4,975 | -3,620 | -4,125 | 0.94 | -1,325 (12,301) | -175 | -255 | 53.44 |  |  |
| QW_stack_sess+2R_quit | 0.93 | -8,937 (21,915) | -4,424 | -6,228 | -2,347 | 0.96 | 636 (14,387) | 1,375 | 1,601 | 0.00 |  |  |
| QW_stack_day+2R_halve | 0.95 | -5,539 (16,802) | -2,204 | -1,574 | -1,983 | 0.91 | -4,173 (14,795) | -2,511 | -3,185 | 70.05 |  |  |
| QW_book_up4R_halve | 1.04 | -3,789 (5,337) | -6,479 | -4,240 | -1,097 | 1.00 | -538 (2,136) | -564 | -675 | 0.00 |  |  |
| QW_stack_sess+3R_quit | 0.96 | -6,727 (18,418) | -4,238 | -6,676 | -3,901 | 0.98 | 1,097 (10,682) | 1,432 | 1,115 | 0.00 |  |  |
| QW_stack_day+$2000live_quit | 0.43 | -25,666 (35,596) | 9,722 | -12,092 | -7,509 | 0.55 | -262 (33,181) | 7,921 | 6,474 | 0.00 |  |  |
| QW_stack_day+$6000live_quit | 0.51 | -25,170 (33,845) | 5,308 | -13,211 | -7,249 | 0.63 | 494 (30,207) | 7,276 | 6,593 | 0.00 |  |  |
| QW_arm3.0_keep0.5 | 1.15 | 6,198 (14,885) | -3,319 | 1,643 | 189 | 1.07 | -8,352 (8,311) | -9,695 | -9,012 | 0.00 |  |  |
| QW_stack_day+6R_halve | 0.99 | -7,110 (9,950) | -6,232 | -6,766 | -2,297 | 0.98 | -851 (5,528) | -509 | -741 | 20.91 |  |  |
| QW_book_up3R_halve | 1.06 | -7,465 (7,023) | -10,915 | -6,401 | -2,507 | 1.00 | -2,386 (3,404) | -2,448 | -2,076 | 0.00 |  |  |
| QW_book_up4R_skip | 0.98 | -7,055 (5,469) | -5,558 | -7,329 | -2,594 | 0.99 | -1,081 (2,665) | -940 | -1,167 | 0.00 |  |  |
| QW_stack_wk+12R_quit | 0.78 | -11,196 (16,790) | 2,238 | -11,196 | -3,153 | 0.93 | 1,743 (8,651) | 2,934 | 1,743 | 0.00 |  |  |
| QW_arm3.0_cont0.5 | 1.23 | 4,583 (16,573) | -9,525 | -1,054 | -1,120 | 1.09 | -8,456 (8,946) | -10,023 | -9,284 | 0.00 |  |  |
| QW_arm2_keep0.75 | 0.92 | -16,427 (15,200) | -11,753 | -15,671 | -4,343 | 0.97 | 4,733 (12,174) | 5,365 | 5,115 | 0.00 |  |  |
| QW_stack_day+4R_halve | 0.98 | -8,547 (10,558) | -7,136 | -7,707 | -3,038 | 0.96 | -3,097 (9,839) | -2,357 | -2,859 | 39.59 |  |  |
| QW_book_up2R_halve | 1.13 | -5,995 (10,141) | -14,315 | -5,769 | -2,496 | 1.04 | -5,352 (7,443) | -6,043 | -5,300 | 0.00 |  |  |
| QW_book_up3R_skip | 0.92 | -12,540 (10,805) | -7,890 | -10,651 | -4,500 | 0.97 | -1,096 (7,477) | -464 | -440 | 0.00 |  | Y |
| QW_arm4.0_keep0.5 | 1.21 | 5,473 (18,171) | -7,348 | -1,257 | -1,267 | 1.09 | -10,396 (10,201) | -11,960 | -11,177 | 0.00 |  |  |
| QW_arm2_keep0.25 | 1.09 | 172 (10,200) | -5,511 | -3,569 | -502 | 1.05 | -8,462 (8,234) | -9,324 | -9,050 | 0.00 |  |  |
| QW_stack_wk+8R_quit | 0.65 | -16,674 (25,625) | 4,962 | -16,375 | -4,819 | 0.82 | 3,567 (20,821) | 6,833 | 3,711 | 0.00 |  |  |
| QW_stack_day+3R_quit | 0.69 | -23,951 (27,227) | -4,559 | -17,265 | -8,516 | 0.80 | 1,028 (20,558) | 4,594 | 4,422 | 0.00 |  |  |
| QW_book_up1R_halve | 1.24 | -15,423 (15,404) | -29,966 | -8,903 | -4,847 | 1.08 | -8,617 (14,706) | -10,113 | -7,270 | 0.00 |  |  |
| QW_arm_off | 1.23 | 982 (19,088) | -13,125 | -5,562 | -2,848 | 1.09 | -10,637 (10,349) | -12,204 | -11,425 | 0.00 |  |  |
| QW_stack_day+4R_quit | 0.78 | -21,701 (23,478) | -8,199 | -20,221 | -7,513 | 0.87 | 1,074 (18,102) | 3,378 | 1,786 | 0.00 |  |  |
| QW_book_up2R_skip | 0.84 | -19,922 (16,954) | -10,144 | -19,015 | -6,182 | 0.89 | -219 (14,776) | 1,731 | 170 | 0.00 |  |  |
| QW_stack_wk+4R_halve | 0.93 | -18,219 (13,607) | -13,935 | -18,179 | -6,649 | 0.89 | -2,279 (12,975) | -260 | -2,264 | 85.60 |  |  |
| QW_stack_day+6R_quit | 0.89 | -22,450 (18,619) | -15,669 | -21,618 | -7,756 | 0.94 | 323 (10,749) | 1,371 | 715 | 0.00 |  |  |
| QW_stack_wk+4R_quit | 0.49 | -39,278 (29,152) | -7,948 | -37,500 | -12,444 | 0.59 | 11,730 (33,076) | 19,252 | 14,090 | 0.00 |  |  |
| QW_stack_day+1R_quit | 0.50 | -30,359 (34,125) | 378 | -21,093 | -9,442 | 0.63 | -6,997 (32,639) | -256 | -3,698 | 0.00 |  |  |
| QW_book_up1R_skip | 0.53 | -30,904 (30,670) | -1,768 | -22,087 | -7,606 | 0.64 | -10,042 (29,367) | -3,409 | -7,714 | 0.00 |  |  |
| QW_stack_day+2R_quit | 0.59 | -30,597 (31,122) | -5,256 | -24,779 | -10,680 | 0.71 | -8,822 (26,568) | -3,624 | -7,074 | 0.00 |  | Y |

### The single recent look: stack weekly mean / SD / maxDD / worst-20 weeks, recent-first, rule vs the stack as it is
Columns: stack $/wk base -> rule; SD; maxDD; worst-20 sum (sum of the worst min(20, weeks) weeks; L3M has 14 and L6M 28 weeks, so those two are not comparable with the 75-week PRE) (research lots); d = rule - stack with MDE (2.8 SE of the paired weekly delta); lam; uniform = lam x stack mean; excess = rule - uniform; eqWF = equal-risk delta with c solving worst-20 over WF (PRE u HOLD) equal to the stack (c shown); trades/wk; LIVE-lot $/wk d.

#### QW_stack_sess+1R_quit  (stack realised session P&L >= +1R: quit the rest of the session)  engine fires (day arm / week floor, all windows, per book ST HM WT KB SM PE)=[(143, 0), (116, 0), (195, 0), (152, 0), (28, 0), (156, 0)], entry-test resumes=0, stage resumes day/week=0/0, iterations to a stable traded set=5
| window | mean | SD | maxDD | worst-20 | d (MDE) | lam | uniform line | excess | eqWF | trades/wk | LIVE d |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 31,261 -> -3,592 | 130,314 -> 93,509 | 318,846 -> 485,683 | 437,655 -> -50,284 | -34,853 (80,461) | 0.91 | 28,491 | -32,082 | -35,484 (c 1.18) | 126.71 -> 116.07 | -17,650 |
| L6M | 79,055 -> 53,842 | 136,536 -> 122,765 | 318,846 -> 485,683 | 332,332 -> -103,343 | -25,213 (44,159) | 0.89 | 69,987 | -16,145 | -15,747 (c 1.18) | 128.71 -> 114.36 | -12,283 |
| HOLD | 66,693 -> 43,306 | 169,113 -> 156,799 | 624,547 -> 609,904 | -630,207 -> -984,242 | -23,387 (38,803) | 0.89 | 59,249 | -15,943 | -15,774 (c 1.18) | 127.41 -> 113.62 | -10,769 |
| PRE | 61,831 -> 56,577 | 138,576 -> 127,391 | 614,903 -> 471,764 | -2,304,704 -> -1,770,825 | -5,254 (28,412) | 0.87 | 54,096 | 2,481 | 4,693 (c 1.18) | 129.47 -> 113.64 | -1,167 |
| X' | 18,206 -> 18,852 | 101,638 -> 103,673 | 469,146 -> 494,094 | -1,392,026 -> -1,429,366 | 646 (21,561) | 0.93 | 16,852 | 2,000 | 3,960 (c 1.18) | 105.86 -> 97.84 | 3,314 |

#### QW_arm2.0_cont0.5  (day arm 2.0R: instead of flatten-and-quit, the open position runs and later entries at 50%)  engine fires (day arm / week floor, all windows, per book ST HM WT KB SM PE)=[(191, 0), (161, 0), (233, 0), (185, 0), (35, 0), (198, 0)], entry-test resumes=0, stage resumes day/week=0/0, iterations to a stable traded set=1
| window | mean | SD | maxDD | worst-20 | d (MDE) | lam | uniform line | excess | eqWF | trades/wk | LIVE d |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 31,261 -> 37,824 | 130,314 -> 140,884 | 318,846 -> 396,655 | 437,655 -> 529,532 | 6,563 (20,422) | 1.34 | 41,751 | -3,927 | 5,532 (c 0.97) | 126.71 -> 171.00 | 4,938 |
| L6M | 79,055 -> 82,068 | 136,536 -> 140,931 | 318,846 -> 396,655 | 332,332 -> 323,063 | 3,013 (12,214) | 1.26 | 99,278 | -17,209 | 778 (c 0.97) | 128.71 -> 163.18 | 2,894 |
| HOLD | 66,693 -> 70,038 | 169,113 -> 174,428 | 624,547 -> 624,224 | -630,207 -> -661,200 | 3,345 (11,011) | 1.24 | 82,398 | -12,360 | 1,437 (c 0.97) | 127.41 -> 158.97 | 3,147 |
| PRE | 61,831 -> 64,385 | 138,576 -> 146,375 | 614,903 -> 553,304 | -2,304,704 -> -2,381,507 | 2,555 (8,846) | 1.23 | 75,938 | -11,553 | 801 (c 0.97) | 129.47 -> 159.60 | -1,043 |
| X' | 18,206 -> 15,820 | 101,638 -> 101,110 | 469,146 -> 464,064 | -1,392,026 -> -1,434,361 | -2,386 (4,139) | 1.09 | 19,772 | -3,952 | -2,817 (c 0.97) | 105.86 -> 114.91 | 252 |

#### QW_book_up3R_skip  (book day entry test +3R: no new entries (base is +5R))  engine fires (day arm / week floor, all windows, per book ST HM WT KB SM PE)=[(164, 0), (134, 0), (190, 0), (154, 0), (35, 0), (166, 0)], entry-test resumes=0, stage resumes day/week=0/0, iterations to a stable traded set=1
| window | mean | SD | maxDD | worst-20 | d (MDE) | lam | uniform line | excess | eqWF | trades/wk | LIVE d |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 31,261 -> 17,081 | 130,314 -> 116,949 | 318,846 -> 309,506 | 437,655 -> 239,137 | -14,180 (22,299) | 0.92 | 28,627 | -11,546 | -13,569 (c 1.04) | 126.71 -> 116.07 | -7,013 |
| L6M | 79,055 -> 66,739 | 136,536 -> 124,194 | 318,846 -> 309,506 | 332,332 -> 244,779 | -12,316 (15,474) | 0.92 | 72,431 | -5,692 | -9,927 (c 1.04) | 128.71 -> 117.71 | -4,349 |
| HOLD | 66,693 -> 54,359 | 169,113 -> 156,139 | 624,547 -> 618,338 | -630,207 -> -717,377 | -12,334 (13,858) | 0.92 | 61,376 | -7,017 | -10,389 (c 1.04) | 127.41 -> 117.03 | -3,877 |
| PRE | 61,831 -> 49,291 | 138,576 -> 123,718 | 614,903 -> 675,042 | -2,304,704 -> -2,118,332 | -12,540 (10,805) | 0.92 | 57,181 | -7,890 | -10,776 (c 1.04) | 129.47 -> 119.64 | -4,500 |
| X' | 18,206 -> 17,110 | 101,638 -> 96,969 | 469,146 -> 489,301 | -1,392,026 -> -1,364,538 | -1,096 (7,477) | 0.97 | 17,574 | -464 | -484 (c 1.04) | 105.86 -> 102.23 | 1,754 |

#### QW_stack_day+2R_quit  (stack realised day P&L >= +2R (12,000 per R, research lots): quit the rest of the day)  engine fires (day arm / week floor, all windows, per book ST HM WT KB SM PE)=[(40, 0), (32, 0), (64, 0), (48, 0), (14, 0), (51, 0)], entry-test resumes=0, stage resumes day/week=0/0, iterations to a stable traded set=4
| window | mean | SD | maxDD | worst-20 | d (MDE) | lam | uniform line | excess | eqWF | trades/wk | LIVE d |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 31,261 -> -9,303 | 130,314 -> 101,843 | 318,846 -> 350,170 | 437,655 -> -130,249 | -40,565 (68,306) | 0.67 | 21,006 | -30,309 | -42,429 (c 1.20) | 126.71 -> 85.64 | -18,537 |
| L6M | 79,055 -> 34,384 | 136,536 -> 103,104 | 318,846 -> 350,170 | 332,332 -> -121,344 | -44,671 (50,198) | 0.64 | 50,471 | -16,087 | -37,782 (c 1.20) | 128.71 -> 82.61 | -17,063 |
| HOLD | 66,693 -> 21,671 | 169,113 -> 126,351 | 624,547 -> 555,426 | -630,207 -> -875,201 | -45,023 (49,121) | 0.65 | 43,248 | -21,577 | -40,681 (c 1.20) | 127.41 -> 82.97 | -18,101 |
| PRE | 61,831 -> 31,234 | 138,576 -> 93,139 | 614,903 -> 432,349 | -2,304,704 -> -1,668,168 | -30,597 (31,122) | 0.59 | 36,490 | -5,256 | -24,338 (c 1.20) | 129.47 -> 76.88 | -10,680 |
| X' | 18,206 -> 9,384 | 101,638 -> 89,306 | 469,146 -> 491,117 | -1,392,026 -> -1,376,167 | -8,822 (26,568) | 0.71 | 13,008 | -3,624 | -6,942 (c 1.20) | 105.86 -> 75.77 | 614 |

### Re-entry / opportunity decomposition ($/wk research lots): same trades (sizing / flatten effect on trades taken in both worlds) | admitted only in the rule world ("re-entry in") | dropped by the rule world ("out") | flagged (reduced) trades: P&L at full size and as sized
| cell | win | same trades | re-entry in | out | in trades/wk | out trades/wk | flagged/wk | flagged P&L full size | flagged P&L as sized |
|---|---|---|---|---|---|---|---|---|---|
| QW_stack_sess+1R_quit | L6M | -1,675 | 17,283 | -40,821 | 16.39 | 30.75 | 0.00 | 0 | 0 |
| QW_stack_sess+1R_quit | HOLD | -1,039 | 14,594 | -36,943 | 14.81 | 28.59 | 0.00 | 0 | 0 |
| QW_stack_sess+1R_quit | PRE | -343 | 5,907 | -10,818 | 16.56 | 32.39 | 0.00 | 0 | 0 |
| QW_stack_sess+1R_quit | X' | -1,611 | 930 | 1,328 | 2.98 | 11.00 | 0.00 | 0 | 0 |
| QW_arm2.0_cont0.5 | L6M | 0 | 3,013 | -0 | 34.46 | 0.00 | 0.00 | 0 | 0 |
| QW_arm2.0_cont0.5 | HOLD | 0 | 3,345 | -0 | 31.56 | 0.00 | 0.00 | 0 | 0 |
| QW_arm2.0_cont0.5 | PRE | 0 | 2,555 | -0 | 30.13 | 0.00 | 0.00 | 0 | 0 |
| QW_arm2.0_cont0.5 | X' | 0 | -2,386 | -0 | 9.05 | 0.00 | 0.00 | 0 | 0 |
| QW_book_up3R_skip | L6M | 0 | 0 | -12,316 | 0.00 | 11.00 | 0.00 | 0 | 0 |
| QW_book_up3R_skip | HOLD | 0 | 0 | -12,334 | 0.00 | 10.38 | 0.00 | 0 | 0 |
| QW_book_up3R_skip | PRE | 0 | 0 | -12,540 | 0.00 | 9.83 | 0.00 | 0 | 0 |
| QW_book_up3R_skip | X' | 0 | 0 | -1,096 | 0.00 | 3.64 | 0.00 | 0 | 0 |
| QW_stack_day+2R_quit | L6M | -235 | -1,118 | -43,317 | 0.29 | 46.39 | 0.00 | 0 | 0 |
| QW_stack_day+2R_quit | HOLD | -206 | -979 | -43,838 | 0.25 | 44.69 | 0.00 | 0 | 0 |
| QW_stack_day+2R_quit | PRE | -103 | -414 | -30,080 | 0.39 | 52.97 | 0.00 | 0 | 0 |
| QW_stack_day+2R_quit | X' | -270 | 262 | -8,815 | 0.43 | 30.52 | 0.00 | 0 | 0 |

### Placebos at the same fire rate (100 random suppressions with the same count per book x session stratum and the same factor values): rank of the real cell among the draws (1.00 = real beats all); excess = after the lot-factor line
| cell | L3M excess/d rank | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| QW_stack_sess+1R_quit | 0.04 / 0.04 (placebo mean excess -9,798) | 0.41 / 0.31 (placebo mean excess -12,929) | 0.32 / 0.28 (placebo mean excess -11,890) | 0.97 / 0.93 (placebo mean excess -7,035) | 0.85 / 0.89 (placebo mean excess -3,630) |
| QW_arm2.0_cont0.5 | n/a (the rule only re-admits trades; no suppression to randomise) | n/a (the rule only re-admits trades; no suppression to randomise) | n/a (the rule only re-admits trades; no suppression to randomise) | n/a (the rule only re-admits trades; no suppression to randomise) | n/a (the rule only re-admits trades; no suppression to randomise) |
| QW_book_up3R_skip | 0.04 / 0.03 (placebo mean excess 1,674) | 0.23 / 0.11 (placebo mean excess -1,442) | 0.15 / 0.06 (placebo mean excess -1,834) | 0.00 / 0.00 (placebo mean excess -965) | 0.75 / 0.76 (placebo mean excess -2,810) |
| QW_stack_day+2R_quit | 0.00 / 0.00 (placebo mean excess 3,792) | 0.19 / 0.01 (placebo mean excess -7,579) | 0.09 / 0.00 (placebo mean excess -8,522) | 0.56 / 0.05 (placebo mean excess -6,488) | 0.74 / 0.74 (placebo mean excess -8,377) |

### Other fill bases (selected cells re-run; d vs the stack on the same basis, research $/wk; excess in brackets)
| cell | basis | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| QW_stack_sess+1R_quit | N | -34,853 (-32,082) | -25,213 (-16,145) | -23,387 (-15,943) | -5,254 (2,481) | 646 (2,000) |
| QW_stack_sess+1R_quit | M | -26,471 (-28,438) | -25,966 (-22,261) | -23,679 (-21,421) | -4,048 (402) | 2,636 (3,224) |
| QW_stack_sess+1R_quit | LIVE-CAL | -28,049 (-26,743) | -22,654 (-15,329) | -21,146 (-15,317) | -4,967 (1,168) | 1,147 (1,851) |
| QW_arm2.0_cont0.5 | N | 6,563 (-3,927) | 3,013 (-17,209) | 3,345 (-12,360) | 2,555 (-11,553) | -2,386 (-3,952) |
| QW_arm2.0_cont0.5 | M | 1,500 (6,381) | -395 (-7,498) | 401 (-3,655) | -763 (-7,925) | -3,109 (-3,763) |
| QW_arm2.0_cont0.5 | LIVE-CAL | 6,303 (1,260) | 3,205 (-13,507) | 3,474 (-9,081) | 983 (-10,353) | -2,635 (-3,454) |
| QW_book_up3R_skip | N | -14,180 (-11,546) | -12,316 (-5,692) | -12,334 (-7,017) | -12,540 (-7,890) | -1,096 (-464) |
| QW_book_up3R_skip | M | 1,498 (420) | -1,851 (-129) | -2,247 (-1,240) | -9,448 (-7,718) | -359 (-211) |
| QW_book_up3R_skip | LIVE-CAL | -9,421 (-8,242) | -9,025 (-3,898) | -9,460 (-5,459) | -12,279 (-8,662) | -674 (-348) |
| QW_stack_day+2R_quit | N | -40,565 (-30,309) | -44,671 (-16,087) | -45,023 (-21,577) | -30,597 (-5,256) | -8,822 (-3,624) |
| QW_stack_day+2R_quit | M | -5,282 (-11,106) | -17,955 (-6,357) | -19,871 (-12,760) | -16,103 (-1,759) | -4,836 (-2,643) |
| QW_stack_day+2R_quit | LIVE-CAL | -31,591 (-26,656) | -37,460 (-13,940) | -38,483 (-19,816) | -25,576 (-5,559) | -6,376 (-3,710) |

### Sized-lot R governors (day entry test, day arm and week floor thresholds multiplied by the day's / week's largest multiplier of the book; the user's ER-sizer convention) vs the planned-lot base used above. d vs the stack as it is, research $/wk (excess in brackets); planned-lot row repeated
| cell | governors | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| QW_stack_sess+1R_quit | planned-lot R | -34,853 (-32,082) | -25,213 (-16,145) | -23,387 (-15,943) | -5,254 (2,481) | 646 (2,000) |
| QW_stack_sess+1R_quit | sized-lot R | -34,853 (-32,082) | -25,213 (-16,145) | -23,387 (-15,943) | -5,254 (2,481) | 646 (2,000) |
| QW_stack_day+2R_quit | planned-lot R | -40,565 (-30,309) | -44,671 (-16,087) | -45,023 (-21,577) | -30,597 (-5,256) | -8,822 (-3,624) |
| QW_stack_day+2R_quit | sized-lot R | -40,565 (-30,309) | -44,671 (-16,087) | -45,023 (-21,577) | -30,597 (-5,256) | -8,822 (-3,624) |

### Per-session split of the delta (entry session of the affected row; $/wk, research lots | LIVE lots), L6M and PRE
| cell | win | asia (res / live) | london (res / live) | pre (res / live) | nyam (res / live) | nypm (res / live) | close (res / live) |
|---|---|---|---|---|---|---|---|
| QW_stack_sess+1R_quit | L6M | -22,013 / -11,865 | -14,522 / -5,374 | 2,749 / 888 | 2,803 / 2,750 | 5,813 / 1,319 | -43 / -0 |
| QW_stack_sess+1R_quit | PRE | -153 / -166 | 225 / 1,072 | 2,006 / -313 | -6,858 / -1,922 | -413 / 183 | -60 / -23 |
| QW_arm2.0_cont0.5 | L6M | -1,416 / -920 | -1,021 / 261 | 1,139 / 186 | 2,191 / 2,683 | 2,018 / 734 | 103 / -50 |
| QW_arm2.0_cont0.5 | PRE | 253 / -393 | -1,533 / -581 | 201 / -366 | 3,243 / 311 | 513 / 6 | -123 / -19 |
| QW_book_up3R_skip | L6M | -2,070 / -851 | -5,592 / -2,018 | 145 / -991 | -653 / 634 | -4,145 / -1,124 | -0 / -0 |
| QW_book_up3R_skip | PRE | -589 / -584 | -1,726 / -557 | -381 / -5 | -8,077 / -3,125 | -1,889 / -239 | 122 / 10 |
| QW_stack_day+2R_quit | L6M | -20,697 / -10,290 | -14,450 / -5,860 | 3,940 / -400 | -11,938 / -880 | -1,650 / 339 | 124 / 27 |
| QW_stack_day+2R_quit | PRE | -905 / -1,105 | -5,203 / -1,546 | -1,948 / -1,183 | -17,932 / -6,457 | -4,694 / -432 | 85 / 43 |

### QUANT-LAYER columns (program: 50 cells, cumulative with earlier programs 2890654)
White RC p (best cell, PRE u X' weeks / selection frame) = 0.96 (studentised 0.45); over all weeks to 2026-02-06 = 0.95 (studentised 0.53); Romano-Wolf survivors: selection frame none, all weeks none; PBO (CSCV, S=10, daily deltas) = 0.00; minimum backtest length for 50 trials at annual SR 1 = 5.2 years.

| cell | d L6M [week-block 95% CI] | d L3M / L6M / HOLD / PRE / X' | trades/wk | RW p (sel / all) | DSR (sel / all / cumulative) | NW t (L6M / all) | longest losing-delta run (wks) | top-5% share of gain (L6M) | corr(d, stack) L6M / all | quarters d>0 | marginal worst-20 (WF) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| QW_stack_sess+1R_quit | -25,213 [-51,612, 5,576] | -34,853 / -25,213 / -23,387 / -5,254 / 646 | 114.36 | 1.00 / 1.00 | 0.00 / 0.00 / 0.00 | -1.94 / -1.31 | 7 | n/a (net loss) | -0.46 / -0.39 | 4/12 | 465,043 |
| QW_arm2.0_cont0.5 | 3,013 [-6,286, 13,376] | 6,563 / 3,013 / 3,345 / 2,555 / -2,386 | 163.18 | 0.97 / 0.94 | 0.01 / 0.01 / 0.00 | 0.64 / 0.72 | 6 | 16.44 | 0.11 / 0.17 | 5/12 | -87,102 |
| QW_book_up3R_skip | -12,316 [-19,324, -4,748] | -14,180 / -12,316 / -12,334 / -12,540 / -1,096 | 117.71 | 1.00 / 1.00 | 0.00 / 0.00 / 0.00 | -3.37 / -3.80 | 7 | n/a (net loss) | -0.51 / -0.52 | 1/12 | 107,469 |
| QW_stack_day+2R_quit | -44,671 [-68,966, -23,690] | -40,565 / -44,671 / -45,023 / -30,597 / -8,822 | 82.61 | 1.00 / 1.00 | 0.00 / 0.00 / 0.00 | -3.83 / -4.40 | 9 | n/a (net loss) | -0.66 / -0.69 | 1/12 | 519,183 |

Breakeven slippage / capacity: not applicable for sizing, skipping and halt rules that change no fill, price or level: they add or remove whole planned trades (lot factor lam <= ~1.36 of the planned lots, never above the planned lot per trade except where lam>1 comes from re-admitted trades); costs per lot are unchanged. Latency: decisions use closed trades only (causal), so a 1-3 s delay does not alter them.



## Code / outputs
`l2vast/ds3/code/rhq/`; `l2vast/ds3/out/rhq/qw_*`. Prereg sha256 dbc0fc90ddf7482bdf2066e03732d568e5caff12694f445e90cda69608ba0d73.
