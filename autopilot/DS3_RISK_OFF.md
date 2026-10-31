# DS3_RISK_OFF - RHQ follow-up section 8 (2026-10-31)

**INTERPRETATION IS THE LEAD'S, NOT THE USER'S.** The user's original text for this program never reached the lead (no directive text exists in the logs); the lead supplied the interpretation below. If the user re-pastes the original text, this report is superseded and the cells are re-run with the same machinery (code `l2vast/ds3/code/rhq/`, outputs `l2vast/ds3/out/rhq/`).

Research only; no live/execution/chart change. UNTOUCHED (label day > 20260206) never read. Windows: L3M 20251106.. (view), L6M 20250801.., HOLD 20250701.., PRE 20240201..20250630, X' 20230401..20240131, all capped 20260206. Base = the stack as it is = 70/30 split (S73) on the exact per-book lock engine (day entry test +5R/-2R, day arm 2R keep 50%, week floor 12R in planned-lot R; R = lots x 60 x $20), six engine books ST HM WT KB SM PE, N basis (M and LIVE-CAL beside for the cells that got the recent look). $ shown at research lots (ST10 HM10 WT7 KB5.2 SM7.4 PE5.6) AND at LIVE lots (mapping stated: ST=U6 4 Asia/London; HM=H6 4 Asia / 2 NY-AM; KB=K6 2; SM=M6 2 London/NY-AM; PE=P6 7 Asia/London/NY-AM; WT not live = research/2.35 = 3; pre-market counted with NY-AM and close with NY-PM; per-row live/research scaling of the research-lot outcome, locks evaluated at research lots). Prereg autopilot/RHQ_RISK_OFF_prereg.md sha256 92da77d19a4d6d5a933478a7d4680a6274094947147cff990499f689b9c01194 (sha256 in DECISIONS.md before any cell was scored). Multiplicity and the cumulative count are in the QUANT block. UF_TRIALS side=rhq_*. 

Lead's interpretation: RISK-OFF = after a stop, size down the next trade(s) for a period, per book (next trade after a stop at x0.5 / x0.25; ladder 1/.5/.25; a stop among the last K trades; T minutes; rest of day / session) and at stack level (>= 2 stops in the day across books -> half size for the rest of the day / session / T minutes; same-side; realised day / week P&L rungs), back to full after a winner or after the period. 55 cells (+1 identity control); selection on PRE and X' only; ONE recent look at the carried cells plus the 3 cells named CANON in the prereg.

## 1. Page 1 - the answer: NULL (every size-down-after-a-stop rule loses to plain uniform scaling)

1. **0 of 55 cells carried on PRE and X'** (carried = excess over the lot-factor-matched uniform scaling line >= 0 AND equal-risk delta >= 0 in BOTH windows). Excess > 0 in PRE for 1 cell and in X' for 2, never the same cell; equal-risk delta > 0 in both windows for 2 cells (the per-book 'two stops in the session' cells at +0.0..+2.5k, i.e. noise), neither with excess > 0 in both. Because nothing was carried, the single recent look went only to the 3 prereg-named CANON cells (per-book 'next trade after a stop at x0.5', stack 'two stops in a day -> x0.5 for the rest of the day', stack 'day P&L <= -2R -> x0.5').
2. **The CANON cells are negative against the stack as it is in every window, at research and at live lots** (d = rule - stack, $/wk research; MDE in the table): book streak-1 x0.5: L3M -17.3k, L6M -9.1k, HOLD -8.7k, PRE -13.3k, X' -5.0k (live lots -6.7k / -2.6k / -0.7k / -7.2k / -1.5k); stack day P&L <= -2R x0.5: -23.2k / -20.3k / -14.9k / -11.3k / -4.8k (live -3.8k / -6.0k / -3.1k / -3.0k / -1.6k); stack two-stops-a-day x0.5: -13.7k / -24.0k / -20.7k / -24.3k / -13.6k (live -5.1k / -6.8k / -5.6k / -8.0k / -2.7k). Against the lot-factor-matched line (STRUCTURE) the sign is the same (L6M excess -8.8k / -19.3k / -14.6k), and at equal risk (c on worst-20 over PRE u HOLD) -3.3k / -17.6k / -7.4k in L6M. SD and maxDD fall (e.g. two-stops-a-day: SD 136k -> 109k, L6M) but by less than the mean they cost; that is what 'lowers risk' means, not edge.
3. **Why: trades after a stop are not worse than other trades.** The flagged (reduced) trades of the book streak-1 rule earn +22.4k/wk at full size in L6M (+15.9k HOLD, +15.9k PRE, +15.6k X'; 64 trades/wk): positive in every window, so halving them removes P&L (-6.2k per week 'same trades' effect in L6M). Lot factor stays 0.9-1.0 because a half-size loss uses less of the day's planned-lot R budget, so the engine's day/arm tests admit 24-56 extra trades per week in L6M (the decomposition table); those re-entered trades are not the source of a gain either (re-entry in: +1.1k / -2.3k / -0.8k / +3.4k per week L6M / HOLD / PRE / X').
4. **Placebo (100 random suppressions with the same count per book x session stratum and the same factor values).** The book streak-1 rule is indistinguishable from random down-sizing (rank of its excess 0.72 L6M, 0.70 HOLD, 0.69 PRE, 0.50 X'; 0.21 L3M): 'after a stop' carries no information about the next trade. The stack day P&L -2R rung is WORSE than random in L3M/L6M/HOLD (rank 0.00 / 0.00 / 0.04); two-stops-a-day L6M 0.15, PRE 0.24.
5. **Governors in sized-lot R (the user's ER-sizer convention, thresholds x the day's/week's largest multiplier)** change nothing material for rules that only size down: canon L6M d -8.9k / -20.3k / -26.1k vs -9.1k / -20.3k / -24.0k planned-lot (table 'Sized-lot R governors').
6. **QUANT:** White RC p 0.99 (selection frame) / 1.00 (all weeks), Romano-Wolf survivors none, DSR 0.00, PBO 0.23, minimum backtest length for 55 trials 5.3 years (> the 3-year sample): consistent with a null. Other bases (M, LIVE-CAL): same signs in all windows (table).
7. **For the Sunday brief:** do NOT add a size-down-after-stop rule to D6 (stack or per-book); the D6 lock engine already ends a bad day (day -2R book test), and a half-size rung before it removes positive trades. Tier: all cells DEAD / STRUCTURE (no LEAD, no CANDIDATE-RECENT). RECENT_WINS: none promoted.

Questions for the user (MORNING.md): none. If the original RISK-OFF text meant something else (e.g. risk-off = the market-state 'risk-off' regime from the cross-asset work, or a time-of-day rule), re-paste it.

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
| RO_book_sess2_f0.25 | 1.00 | 638 (5,313) | 520 | 2,457 | -108 | 1.00 | -393 (2,803) | -339 | 125 | 4.55 |  |  |
| RO_book_sess2_f0.5 | 1.01 | -508 (4,108) | -877 | 610 | -260 | 1.00 | -308 (1,862) | -277 | 18 | 4.28 |  |  |
| RO_book_day2_f0.5 | 0.94 | -5,413 (8,839) | -1,647 | -1,123 | -1,521 | 0.94 | -1,320 (8,260) | -212 | -36 | 46.97 |  |  |
| RO_book_dayPL-1.5R_f0.5 | 1.00 | -1,247 (2,553) | -1,072 | -1,538 | -212 | 1.00 | 267 (964) | 291 | 179 | 0.20 |  |  |
| RO_stack_weekPL-4R_f0.5 | 0.94 | -6,295 (11,250) | -2,500 | 2,713 | -2,320 | 0.92 | -6,731 (12,833) | -5,296 | -4,870 | 48.79 |  |  |
| RO_stack_weekPL-8R_f0.5 | 0.96 | -4,112 (8,258) | -1,933 | -1,980 | -1,866 | 0.98 | -1,301 (6,609) | -897 | -677 | 22.24 |  |  |
| RO_stack_sess2_f0.5 | 1.00 | -9,861 (16,129) | -9,736 | -2,325 | -4,030 | 0.97 | -3,037 (13,009) | -2,579 | -837 | 43.17 |  |  |
| RO_side_T60_N2_f0.5 | 1.01 | -2,682 (8,643) | -3,306 | -2,870 | -2,344 | 0.99 | -531 (4,301) | -340 | -587 | 9.53 |  |  |
| RO_book_T30_f0.5 | 0.99 | -6,348 (12,498) | -5,861 | -1,324 | -2,286 | 0.97 | -4,023 (13,581) | -3,439 | -2,739 | 27.32 |  |  |
| RO_stack_sess3_f0.5 | 1.01 | -9,393 (13,974) | -10,055 | -4,318 | -3,384 | 0.99 | -1,851 (9,353) | -1,615 | -268 | 27.39 |  |  |
| RO_book_dayPL-1R_f0.5 | 0.99 | -6,715 (8,826) | -6,334 | -2,411 | -1,541 | 0.98 | -3,474 (9,545) | -3,111 | -2,323 | 13.31 |  |  |
| RO_book_T240_f0.5 | 0.91 | -14,048 (15,762) | -8,693 | -4,207 | -4,165 | 0.86 | -4,893 (16,726) | -2,410 | -2,151 | 89.16 |  |  |
| RO_book_day2_f0.25 | 0.86 | -8,693 (11,662) | -264 | -3,795 | -2,410 | 0.90 | -4,240 (12,248) | -2,353 | -2,952 | 53.72 |  |  |
| RO_book_sess1_f0.5 | 1.01 | -8,534 (13,050) | -9,098 | -6,336 | -4,210 | 0.98 | -2,346 (10,955) | -1,978 | -1,692 | 35.07 |  |  |
| RO_stack_dayPL-3R_f0.5 | 0.97 | -6,952 (7,833) | -4,933 | -5,393 | -1,498 | 0.97 | -3,381 (10,525) | -2,789 | -2,959 | 22.69 |  |  |
| RO_book_day1_f0.5 | 0.87 | -15,350 (16,634) | -7,600 | -3,853 | -4,817 | 0.83 | -7,998 (16,313) | -4,827 | -5,473 | 110.20 |  |  |
| RO_side_day3_f0.5 | 0.91 | -12,854 (13,523) | -7,285 | -9,638 | -4,530 | 0.91 | -2,235 (14,778) | -525 | -1,186 | 64.19 |  |  |
| RO_book_streak1_f0.5 | 0.95 | -13,287 (19,895) | -10,317 | -7,447 | -7,159 | 0.90 | -5,023 (15,106) | -3,232 | -3,437 | 64.13 |  | Y |
| RO_stack_streak2_f0.25 | 0.94 | -14,034 (17,800) | -10,455 | -5,367 | -3,706 | 0.90 | -7,532 (22,221) | -5,720 | -5,596 | 37.68 |  |  |
| RO_stack_streak3_f0.5 | 1.01 | -12,781 (13,914) | -13,149 | -9,121 | -4,275 | 0.97 | -3,035 (14,334) | -2,443 | -1,903 | 22.97 |  |  |
| RO_stack_T30_N2_f0.5 | 1.00 | -9,700 (12,946) | -9,421 | -5,263 | -2,923 | 0.96 | -6,756 (14,008) | -6,002 | -5,781 | 26.60 |  |  |
| RO_side_day2_f0.5 | 0.90 | -16,098 (14,176) | -9,628 | -11,698 | -4,690 | 0.88 | -1,771 (14,932) | 370 | -190 | 81.72 |  |  |
| RO_stack_dayPL-1R_f0.5 | 0.94 | -15,542 (13,585) | -11,860 | -8,609 | -3,813 | 0.92 | -5,679 (14,663) | -4,132 | -3,803 | 54.69 |  |  |
| RO_book_streak2_f0.5 | 1.00 | -8,245 (12,663) | -8,379 | -6,444 | -1,449 | 0.96 | -6,868 (9,986) | -6,162 | -6,487 | 23.79 |  |  |
| RO_book_T120_f0.5 | 0.94 | -11,881 (14,489) | -8,324 | -7,440 | -3,334 | 0.91 | -6,659 (17,277) | -5,055 | -5,632 | 62.88 |  |  |
| RO_book_T30_f0.25 | 0.97 | -8,443 (18,146) | -6,294 | -4,590 | -2,798 | 0.93 | -9,350 (19,053) | -8,087 | -8,711 | 28.97 |  |  |
| RO_stack_dayPL-2R_f0.5 | 0.96 | -11,333 (11,963) | -8,777 | -9,549 | -3,045 | 0.94 | -4,766 (13,895) | -3,723 | -4,291 | 37.85 |  | Y |
| RO_stack_streak3_f0.25 | 0.98 | -9,083 (18,186) | -7,723 | -6,237 | -2,796 | 0.93 | -8,803 (18,391) | -7,597 | -8,296 | 24.61 |  |  |
| RO_stack_streak2_f0.5 | 0.99 | -17,570 (14,612) | -16,976 | -12,633 | -6,255 | 0.95 | -3,805 (16,519) | -2,936 | -2,198 | 35.71 |  |  |
| RO_stack_T60_N2_f0.5 | 0.97 | -10,555 (16,716) | -8,626 | -5,445 | -4,166 | 0.92 | -10,628 (14,587) | -9,117 | -9,873 | 50.92 |  |  |
| RO_stack_sess2_f0.25 | 0.95 | -15,175 (22,584) | -12,085 | -11,007 | -5,727 | 0.94 | -5,657 (17,511) | -4,621 | -4,536 | 48.17 |  |  |
| RO_book_sess1_f0.25 | 0.97 | -11,408 (18,854) | -9,566 | -10,387 | -4,935 | 0.95 | -5,450 (13,143) | -4,612 | -5,191 | 36.65 |  |  |
| RO_stack_day4_f0.5 | 0.86 | -18,095 (17,855) | -9,672 | -9,004 | -4,888 | 0.82 | -8,734 (17,273) | -5,500 | -6,766 | 101.60 |  |  |
| RO_stack_sess3_f0.25 | 0.98 | -14,719 (19,474) | -13,377 | -12,969 | -4,592 | 0.97 | -4,456 (12,088) | -3,902 | -3,946 | 29.84 |  |  |
| RO_book_day1_f0.25 | 0.70 | -19,829 (21,416) | -1,298 | -5,499 | -5,412 | 0.68 | -13,477 (23,723) | -7,651 | -11,863 | 129.08 |  |  |
| RO_stack_T30_N2_f0.25 | 0.97 | -12,133 (16,844) | -10,018 | -6,249 | -3,050 | 0.91 | -12,314 (21,011) | -10,730 | -11,617 | 28.05 |  |  |
| RO_book_lastK3_f0.5 | 0.84 | -19,318 (21,595) | -9,306 | -3,916 | -7,530 | 0.72 | -15,781 (22,086) | -10,740 | -14,902 | 143.80 |  |  |
| RO_book_streak2_f0.25 | 0.98 | -9,107 (14,537) | -7,825 | -7,497 | -1,012 | 0.93 | -11,712 (11,903) | -10,362 | -11,514 | 24.71 |  |  |
| RO_book_T240_f0.25 | 0.78 | -21,835 (21,171) | -7,989 | -10,307 | -5,662 | 0.74 | -10,923 (23,501) | -6,174 | -8,824 | 105.57 |  |  |
| RO_book_T60_f0.5 | 0.97 | -9,910 (16,035) | -7,954 | -9,214 | -3,544 | 0.94 | -10,160 (15,865) | -8,992 | -10,052 | 44.05 |  |  |
| RO_stack_day4_f0.25 | 0.70 | -23,949 (23,294) | -5,392 | -12,702 | -6,578 | 0.69 | -11,009 (26,316) | -5,337 | -8,873 | 118.07 |  |  |
| RO_book_lastK2_f0.5 | 0.89 | -16,120 (19,152) | -9,428 | -7,919 | -5,375 | 0.79 | -14,451 (20,486) | -10,712 | -13,778 | 113.65 |  |  |
| RO_book_ladder_f0.5_fl0.25 | 0.93 | -17,885 (22,127) | -13,748 | -13,922 | -6,085 | 0.87 | -8,825 (17,809) | -6,464 | -7,979 | 67.43 |  |  |
| RO_stack_T120_N2_f0.5 | 0.92 | -18,823 (16,618) | -14,018 | -12,356 | -6,590 | 0.87 | -10,860 (18,165) | -8,476 | -9,756 | 82.72 |  |  |
| RO_stack_day3_f0.5 | 0.85 | -25,639 (20,329) | -16,347 | -13,849 | -8,274 | 0.79 | -11,491 (18,576) | -7,735 | -9,304 | 117.08 |  |  |
| RO_book_T120_f0.25 | 0.86 | -16,379 (19,471) | -7,923 | -12,361 | -4,645 | 0.83 | -12,556 (23,619) | -9,390 | -12,056 | 72.21 |  |  |
| RO_stack_day2_f0.5 | 0.84 | -24,285 (20,432) | -14,636 | -12,362 | -8,021 | 0.77 | -13,600 (20,125) | -9,482 | -12,138 | 131.65 |  | Y |
| RO_stack_T60_N2_f0.25 | 0.90 | -16,489 (21,899) | -10,061 | -11,704 | -4,833 | 0.84 | -14,352 (21,524) | -11,423 | -13,945 | 57.55 |  |  |
| RO_book_T60_f0.25 | 0.92 | -12,625 (20,272) | -7,465 | -11,981 | -3,569 | 0.88 | -14,544 (21,733) | -12,359 | -14,496 | 48.56 |  |  |
| RO_book_streak1_f0.25 | 0.87 | -23,323 (24,095) | -15,544 | -20,052 | -6,769 | 0.81 | -8,552 (22,357) | -5,073 | -7,732 | 69.03 |  |  |
| RO_stack_T120_N2_f0.25 | 0.79 | -23,634 (25,767) | -10,578 | -15,992 | -8,825 | 0.75 | -16,195 (25,325) | -11,608 | -15,793 | 97.15 |  |  |
| RO_stack_day3_f0.25 | 0.66 | -33,962 (26,755) | -13,123 | -21,016 | -10,550 | 0.63 | -14,544 (27,804) | -7,885 | -12,843 | 137.08 |  |  |
| RO_book_lastK2_f0.25 | 0.73 | -26,886 (26,546) | -10,112 | -17,795 | -9,241 | 0.62 | -18,706 (27,848) | -11,808 | -18,837 | 126.44 |  |  |
| RO_stack_day2_f0.25 | 0.63 | -34,190 (27,472) | -11,450 | -19,434 | -10,475 | 0.59 | -18,250 (29,263) | -10,830 | -18,274 | 153.60 |  |  |
| RO_book_lastK3_f0.25 | 0.61 | -33,882 (28,506) | -9,921 | -17,121 | -12,065 | 0.50 | -20,930 (29,125) | -11,756 | -22,564 | 163.16 |  |  |

### The single recent look: stack weekly mean / SD / maxDD / worst-20 weeks, recent-first, rule vs the stack as it is
Columns: stack $/wk base -> rule; SD; maxDD; worst-20 sum (sum of the worst min(20, weeks) weeks; L3M has 14 and L6M 28 weeks, so those two are not comparable with the 75-week PRE) (research lots); d = rule - stack with MDE (2.8 SE of the paired weekly delta); lam; uniform = lam x stack mean; excess = rule - uniform; eqWF = equal-risk delta with c solving worst-20 over WF (PRE u HOLD) equal to the stack (c shown); trades/wk; LIVE-lot $/wk d.

#### RO_book_streak1_f0.5  (per-book: next trade after N consecutive book stops at f; back to full after a non-stop (winner) trade)  engine fires (day arm / week floor, all windows, per book ST HM WT KB SM PE)=[(159, 0), (143, 0), (188, 0), (163, 0), (30, 0), (158, 0)], entry-test resumes=0, stage resumes day/week=0/0, iterations to a stable traded set=6
| window | mean | SD | maxDD | worst-20 | d (MDE) | lam | uniform line | excess | eqWF | trades/wk | LIVE d |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 31,261 -> 13,921 | 130,314 -> 127,841 | 318,846 -> 395,480 | 437,655 -> 194,890 | -17,340 (24,115) | 1.04 | 32,552 | -18,631 | -16,184 (c 1.08) | 126.71 -> 169.57 | -6,717 |
| L6M | 79,055 -> 69,906 | 136,536 -> 134,477 | 318,846 -> 395,480 | 332,332 -> 147,176 | -9,149 (22,502) | 0.99 | 78,659 | -8,753 | -3,343 (c 1.08) | 128.71 -> 160.82 | -2,591 |
| HOLD | 66,693 -> 57,975 | 169,113 -> 156,301 | 624,547 -> 557,534 | -630,207 -> -722,427 | -8,718 (21,866) | 0.99 | 65,948 | -7,973 | -3,903 (c 1.08) | 127.41 -> 158.72 | -734 |
| PRE | 61,831 -> 48,543 | 138,576 -> 132,259 | 614,903 -> 368,208 | -2,304,704 -> -2,188,253 | -13,287 (19,895) | 0.95 | 58,860 | -10,317 | -9,256 (c 1.08) | 129.47 -> 155.68 | -7,159 |
| X' | 18,206 -> 13,182 | 101,638 -> 84,977 | 469,146 -> 424,339 | -1,392,026 -> -1,214,275 | -5,023 (15,106) | 0.90 | 16,414 | -3,232 | -3,929 (c 1.08) | 105.86 -> 119.50 | -1,501 |

#### RO_stack_dayPL-2R_f0.5  (stack realised day P&L <= -2R (R=12,000) -> f for the rest of the day (a half-size rung before the engine -2R book test))  engine fires (day arm / week floor, all windows, per book ST HM WT KB SM PE)=[(181, 0), (144, 0), (204, 0), (158, 0), (19, 0), (182, 0)], entry-test resumes=0, stage resumes day/week=0/0, iterations to a stable traded set=4
| window | mean | SD | maxDD | worst-20 | d (MDE) | lam | uniform line | excess | eqWF | trades/wk | LIVE d |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 31,261 -> 8,103 | 130,314 -> 123,254 | 318,846 -> 369,986 | 437,655 -> 113,442 | -23,158 (33,053) | 1.01 | 31,444 | -23,341 | -22,790 (c 1.05) | 126.71 -> 157.14 | -3,756 |
| L6M | 79,055 -> 58,787 | 136,536 -> 137,148 | 318,846 -> 369,986 | 332,332 -> -139,378 | -20,269 (20,924) | 0.99 | 78,118 | -19,331 | -17,599 (c 1.05) | 128.71 -> 150.79 | -5,992 |
| HOLD | 66,693 -> 51,815 | 169,113 -> 163,055 | 624,547 -> 531,775 | -630,207 -> -952,409 | -14,878 (19,857) | 0.99 | 65,833 | -14,018 | -12,525 (c 1.05) | 127.41 -> 148.84 | -3,071 |
| PRE | 61,831 -> 50,498 | 138,576 -> 137,623 | 614,903 -> 445,861 | -2,304,704 -> -2,331,580 | -11,333 (11,963) | 0.96 | 59,274 | -8,777 | -9,040 (c 1.05) | 129.47 -> 143.08 | -3,045 |
| X' | 18,206 -> 13,440 | 101,638 -> 97,447 | 469,146 -> 430,541 | -1,392,026 -> -1,431,049 | -4,766 (13,895) | 0.94 | 17,163 | -3,723 | -4,155 (c 1.05) | 105.86 -> 110.98 | -1,595 |

#### RO_stack_day2_f0.5  (stack: >= 2 stops today across books -> f for the rest of the day)  engine fires (day arm / week floor, all windows, per book ST HM WT KB SM PE)=[(84, 0), (62, 0), (112, 0), (72, 0), (0, 0), (94, 0)], entry-test resumes=0, stage resumes day/week=0/0, iterations to a stable traded set=2
| window | mean | SD | maxDD | worst-20 | d (MDE) | lam | uniform line | excess | eqWF | trades/wk | LIVE d |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 31,261 -> 17,538 | 130,314 -> 92,795 | 318,846 -> 309,149 | 437,655 -> 245,532 | -13,723 (54,932) | 0.93 | 29,217 | -11,679 | -8,458 (c 1.30) | 126.71 -> 201.79 | -5,128 |
| L6M | 79,055 -> 55,105 | 136,536 -> 109,259 | 318,846 -> 309,149 | 332,332 -> 43,263 | -23,950 (34,145) | 0.88 | 69,727 | -14,622 | -7,407 (c 1.30) | 128.71 -> 185.00 | -6,833 |
| HOLD | 66,693 -> 46,015 | 169,113 -> 136,835 | 624,547 -> 522,575 | -630,207 -> -722,723 | -20,678 (31,480) | 0.88 | 58,461 | -12,445 | -6,864 (c 1.30) | 127.41 -> 180.03 | -5,583 |
| PRE | 61,831 -> 37,545 | 138,576 -> 113,212 | 614,903 -> 347,126 | -2,304,704 -> -1,930,254 | -24,285 (20,432) | 0.84 | 52,182 | -14,636 | -13,014 (c 1.30) | 129.47 -> 175.57 | -8,021 |
| X' | 18,206 -> 4,605 | 101,638 -> 71,692 | 469,146 -> 418,895 | -1,392,026 -> -1,151,411 | -13,600 (20,125) | 0.77 | 14,087 | -9,482 | -12,218 (c 1.30) | 105.86 -> 122.95 | -2,703 |

### Re-entry / opportunity decomposition ($/wk research lots): same trades (sizing / flatten effect on trades taken in both worlds) | admitted only in the rule world ("re-entry in") | dropped by the rule world ("out") | flagged (reduced) trades: P&L at full size and as sized
| cell | win | same trades | re-entry in | out | in trades/wk | out trades/wk | flagged/wk | flagged P&L full size | flagged P&L as sized |
|---|---|---|---|---|---|---|---|---|---|
| RO_book_streak1_f0.5 | L6M | -6,181 | 1,108 | -4,075 | 35.57 | 3.46 | 64.36 | 22,385 | 11,193 |
| RO_book_streak1_f0.5 | HOLD | -3,115 | -2,280 | -3,324 | 34.41 | 3.09 | 64.16 | 15,862 | 7,931 |
| RO_book_streak1_f0.5 | PRE | -8,876 | -835 | -3,575 | 29.96 | 3.75 | 64.13 | 15,870 | 7,935 |
| RO_book_streak1_f0.5 | X' | -8,299 | 3,449 | -173 | 14.43 | 0.80 | 48.00 | 15,597 | 7,798 |
| RO_stack_dayPL-2R_f0.5 | L6M | -17,222 | -3,033 | -14 | 23.64 | 1.57 | 46.61 | 33,688 | 16,844 |
| RO_stack_dayPL-2R_f0.5 | HOLD | -12,303 | -2,766 | 191 | 22.84 | 1.41 | 45.44 | 25,158 | 12,579 |
| RO_stack_dayPL-2R_f0.5 | PRE | -5,843 | -6,198 | 708 | 14.19 | 0.57 | 37.85 | 4,022 | 2,011 |
| RO_stack_dayPL-2R_f0.5 | X' | -6,706 | 1,935 | 6 | 5.14 | 0.02 | 22.48 | 12,538 | 6,269 |
| RO_stack_day2_f0.5 | L6M | -30,336 | 6,386 | -0 | 56.29 | 0.00 | 141.18 | 69,640 | 34,820 |
| RO_stack_day2_f0.5 | HOLD | -24,995 | 4,317 | -0 | 52.62 | 0.00 | 135.06 | 55,802 | 27,901 |
| RO_stack_day2_f0.5 | PRE | -21,279 | -3,006 | -0 | 46.11 | 0.00 | 131.65 | 29,888 | 14,944 |
| RO_stack_day2_f0.5 | X' | -13,956 | 356 | -0 | 17.09 | 0.00 | 82.23 | 17,234 | 8,617 |

### Placebos at the same fire rate (100 random suppressions with the same count per book x session stratum and the same factor values): rank of the real cell among the draws (1.00 = real beats all); excess = after the lot-factor line
| cell | L3M excess/d rank | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| RO_book_streak1_f0.5 | 0.21 / 0.20 (placebo mean excess -9,695) | 0.72 / 0.64 (placebo mean excess -13,665) | 0.70 / 0.63 (placebo mean excess -12,240) | 0.69 / 0.54 (placebo mean excess -12,346) | 0.50 / 0.51 (placebo mean excess -3,905) |
| RO_stack_dayPL-2R_f0.5 | 0.00 / 0.00 (placebo mean excess -480) | 0.00 / 0.00 (placebo mean excess -3,232) | 0.04 / 0.04 (placebo mean excess -3,570) | 0.30 / 0.15 (placebo mean excess -6,562) | 0.38 / 0.38 (placebo mean excess -3,024) |
| RO_stack_day2_f0.5 | 0.00 / 0.00 (placebo mean excess 3,497) | 0.15 / 0.01 (placebo mean excess -9,091) | 0.24 / 0.03 (placebo mean excess -9,027) | 0.24 / 0.03 (placebo mean excess -12,263) | 0.32 / 0.25 (placebo mean excess -7,885) |

### Other fill bases (selected cells re-run; d vs the stack on the same basis, research $/wk; excess in brackets)
| cell | basis | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| RO_book_streak1_f0.5 | N | -17,340 (-18,631) | -9,149 (-8,753) | -8,718 (-7,973) | -13,287 (-10,317) | -5,023 (-3,232) |
| RO_book_streak1_f0.5 | M | -5,227 (-5,128) | -7,050 (-6,448) | -6,430 (-5,923) | -11,863 (-9,718) | -5,035 (-4,228) |
| RO_book_streak1_f0.5 | LIVE-CAL | -12,725 (-13,080) | -5,931 (-5,265) | -5,829 (-4,996) | -13,922 (-11,504) | -5,035 (-4,090) |
| RO_stack_dayPL-2R_f0.5 | N | -23,158 (-23,341) | -20,269 (-19,331) | -14,878 (-14,018) | -11,333 (-8,777) | -4,766 (-3,723) |
| RO_stack_dayPL-2R_f0.5 | M | -13,403 (-14,101) | -16,715 (-15,385) | -10,962 (-10,158) | -8,368 (-6,415) | -6,105 (-5,611) |
| RO_stack_dayPL-2R_f0.5 | LIVE-CAL | -22,309 (-21,891) | -20,514 (-18,584) | -14,735 (-13,223) | -11,567 (-9,273) | -5,860 (-5,268) |
| RO_stack_day2_f0.5 | N | -13,723 (-11,679) | -23,950 (-14,622) | -20,678 (-12,445) | -24,285 (-14,636) | -13,600 (-9,482) |
| RO_stack_day2_f0.5 | M | -3,641 (-5,504) | -13,744 (-9,070) | -9,950 (-6,925) | -19,013 (-13,067) | -11,980 (-10,141) |
| RO_stack_day2_f0.5 | LIVE-CAL | -9,570 (-8,475) | -20,375 (-12,403) | -17,401 (-10,632) | -21,908 (-14,139) | -12,129 (-9,986) |

### Sized-lot R governors (day entry test, day arm and week floor thresholds multiplied by the day's / week's largest multiplier of the book; the user's ER-sizer convention) vs the planned-lot base used above. d vs the stack as it is, research $/wk (excess in brackets); planned-lot row repeated
| cell | governors | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| RO_book_streak1_f0.5 | planned-lot R | -17,340 (-18,631) | -9,149 (-8,753) | -8,718 (-7,973) | -13,287 (-10,317) | -5,023 (-3,232) |
| RO_book_streak1_f0.5 | sized-lot R | -12,791 (-11,803) | -8,874 (-4,594) | -7,461 (-3,421) | -11,786 (-6,453) | -5,481 (-3,249) |
| RO_stack_dayPL-2R_f0.5 | planned-lot R | -23,158 (-23,341) | -20,269 (-19,331) | -14,878 (-14,018) | -11,333 (-8,777) | -4,766 (-3,723) |
| RO_stack_dayPL-2R_f0.5 | sized-lot R | -22,591 (-22,616) | -20,309 (-19,152) | -14,913 (-13,890) | -11,242 (-8,542) | -4,766 (-3,723) |
| RO_stack_day2_f0.5 | planned-lot R | -13,723 (-11,679) | -23,950 (-14,622) | -20,678 (-12,445) | -24,285 (-14,636) | -13,600 (-9,482) |
| RO_stack_day2_f0.5 | sized-lot R | -14,299 (-11,423) | -26,103 (-15,299) | -22,561 (-13,230) | -23,783 (-13,531) | -13,616 (-9,495) |

### Per-session split of the delta (entry session of the affected row; $/wk, research lots | LIVE lots), L6M and PRE
| cell | win | asia (res / live) | london (res / live) | pre (res / live) | nyam (res / live) | nypm (res / live) | close (res / live) |
|---|---|---|---|---|---|---|---|
| RO_book_streak1_f0.5 | L6M | -1,008 / 833 | -4,759 / -1,770 | 3,984 / 452 | -5,485 / -1,718 | -1,653 / -300 | -228 / -88 |
| RO_book_streak1_f0.5 | PRE | -4,854 / -1,971 | -4,031 / -2,763 | -631 / -794 | -4,275 / -1,385 | 793 / -202 | -289 / -43 |
| RO_stack_dayPL-2R_f0.5 | L6M | -6,379 / -2,325 | -8,108 / -3,310 | -616 / -914 | 927 / 783 | -6,209 / -226 | 117 / -0 |
| RO_stack_dayPL-2R_f0.5 | PRE | -1,903 / -595 | -706 / 194 | -3,005 / -837 | -5,088 / -1,624 | -509 / -189 | -122 / 5 |
| RO_stack_day2_f0.5 | L6M | -8,309 / -3,510 | -9,044 / -4,553 | 5,330 / 477 | -6,777 / 612 | -5,105 / 140 | -46 / 1 |
| RO_stack_day2_f0.5 | PRE | -3,620 / -1,480 | -5,308 / -1,311 | -2,045 / -1,014 | -10,654 / -4,023 | -2,215 / -167 | -443 / -27 |

### QUANT-LAYER columns (program: 55 cells, cumulative with earlier programs 2889751)
White RC p (best cell, PRE u X' weeks / selection frame) = 0.99 (studentised 0.99); over all weeks to 2026-02-06 = 1.00 (studentised 1.00); Romano-Wolf survivors: selection frame none, all weeks none; PBO (CSCV, S=10, daily deltas) = 0.23; minimum backtest length for 55 trials at annual SR 1 = 5.3 years.

| cell | d L6M [week-block 95% CI] | d L3M / L6M / HOLD / PRE / X' | trades/wk | RW p (sel / all) | DSR (sel / all / cumulative) | NW t (L6M / all) | longest losing-delta run (wks) | top-5% share of gain (L6M) | corr(d, stack) L6M / all | quarters d>0 | marginal worst-20 (WF) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| RO_book_streak1_f0.5 | -9,149 [-26,134, 6,188] | -17,340 / -9,149 / -8,718 / -13,287 / -5,023 | 160.82 | 1.00 / 1.00 | 0.00 / 0.00 / 0.00 | -1.08 / -2.34 | 12 | n/a (net loss) | -0.20 / -0.38 | 6/12 | 238,519 |
| RO_stack_dayPL-2R_f0.5 | -20,269 [-28,340, -11,059] | -23,158 / -20,269 / -14,878 / -11,333 / -4,766 | 150.79 | 1.00 / 1.00 | 0.00 / 0.00 / 0.00 | -4.11 / -3.07 | 6 | n/a (net loss) | -0.13 / -0.23 | 3/12 | 135,126 |
| RO_stack_day2_f0.5 | -23,950 [-38,510, -4,934] | -13,723 / -23,950 / -20,678 / -24,285 / -13,600 | 185.00 | 1.00 / 1.00 | 0.00 / 0.00 / 0.00 | -2.62 / -3.87 | 9 | n/a (net loss) | -0.62 / -0.64 | 3/12 | 718,153 |

Breakeven slippage / capacity: not applicable for sizing, skipping and halt rules that change no fill, price or level: they add or remove whole planned trades (lot factor lam <= ~1.36 of the planned lots, never above the planned lot per trade except where lam>1 comes from re-admitted trades); costs per lot are unchanged. Latency: decisions use closed trades only (causal), so a 1-3 s delay does not alter them.



## Code / outputs
`l2vast/ds3/code/rhq/` (rhq_lib.py engine + sweep, rhq_cells.py cell lists, rhq_run.py stage 1 + selection, rhq_look.py placebos / bases / QUANT / sized-lot, rhq_report.py tables); `l2vast/ds3/out/rhq/ro_*` (stage1.pkl all cells, selection json + PRE/X' csv, placebo, bases, quant, body.md). Prereg sha256 92da77d19a4d6d5a933478a7d4680a6274094947147cff990499f689b9c01194; selection sha in DECISIONS.md.
