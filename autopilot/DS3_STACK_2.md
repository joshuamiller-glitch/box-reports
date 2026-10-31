# DS3_STACK_2 - PLAN36 section 4: STACK, second pass ("first stop -> cut the rest" and the cap, made robust) - INTERIM (placebos still running)

Research only. No live, execution-server or chart change. UNTOUCHED never read (every frame capped at label day 20260206). Own window masks: 2026 = 0101..0206 (~5 weeks), L6M = 20250801.., L3M = 20251106..20260206 (view), HOLD = 20250701.., PRE = 20240201..20250630, X' = 20230401..20240131. Code `l2vast/ds3/code/stack2/`, outputs `l2vast/ds3/out/stack2/`. Prereg `out/stack2/PREREG_S2.md` (sha 226c78e8...) and the stage-2 addendum `PREREG_S2_stage2.md` (written after the PRE and X' decomposition, before any recent read), selection list sha `93d7e039...` (PRE and X' only) logged in DECISIONS.md before the single recent look (looks.jsonl). Multiplicity: 202 cell-scopes (101 specs x {MKT, S73}); UF_TRIALS side=plan36_stack2.

## 1. Page 1 - the answer (a null with a narrow, recency-only residue)

1. **The pooled "first book stopped -> cut the rest 50%" is NOT robust and is labelled POST-HOC: the premise was chosen after SP-1 looked at L6M / HOLD / L3M.** Its only non-selected evidence is PRE -8.2k (MKT) / -6.5k (S73) and X' +0.7k / -0.4k per week. The simulator reproduces SP-1 to the dollar (MKT P50: L3M +35,745, L6M +22,975, HOLD +19,319, PRE -8,219, X' +676). Nothing is PASS. Program White RC p 0.72 (MKT, 85 cells) / 0.76 (S73, 117 cells); studentised 0.35 / 0.35; PBO 0.12 / 0.10 (PRE and X' weeks, basis N), Romano-Wolf survivors 0 / 0, DSR 0.00-0.03.
2. **The recent gain is mostly NOT the stopped-out trades.** On the lock engine the L6M gain of the pooled cut splits (MKT, $/wk) into same trades +3.4k, entries the lock engine admits only in the rule world ("re-entry in") +17.4k, entries it blocks ("out") +2.2k; in PRE the same trades are -4.4k, re-entry in -2.8k, out -1.0k. The cut changes the day's P&L state, so the day -2R / give-back / week-floor tests admit later library signals that happened to win lately. All of the pooled cut's L6M gain (108%) and 92% of the Asia-stopped cut's (MKT; S73 107%) fall since 2025-10-01 (18.6 of the 27.2 L6M weeks): 2025Q4 +22.8k/wk and 2026Q1 +40.2k/wk for the Asia-stopped MKT cut against a median quarter of about +1k to +6k (quarterly table in section 7). It is a regime read, as in SP-1.
3. **What carries the PRE loss (answer to 4d, PRE and X' only for the diagnosis).** Pre-lock (same trades, $/wk, PRE | X'): cuts when 4 other books are still open -5.1k | -5.5k; cuts when no book is open on the other side -5.1k | -6.0k; stops of NY-AM books -3.5k | -3.9k; WT stops -3.1k | -0.8k (WT is 584 of 1,137 PRE events). Asia-stopped books are +0.7k | -1.1k pre-lock. "Same impulse" (the stop within 10 minutes of the stopped entry) does NOT carry it: 1.8 fires/wk, PRE ~0, L6M +3.8k. Conditions that remove it (selected on PRE+X' only, 1 of 202): stopped book entered in the Asia session; entry-day vol tercile 2; ER20(5m) >= 0.4 at the stopped signal; a book open on the other side; <= 2 other books open (MKT only).
4. **The conditional versions are CANDIDATE-RECENT / LEAD, all inside their MDE, none survives Romano-Wolf or DSR.** Best-supported: the first-stop cut P50 when the stopped book was entered in Asia (18:00-02:00 ET): MKT L3M +17.5k, L6M +20.2k, HOLD +16.5k, 2026 +36.2k, PRE +0.9k, X' +3.7k per week (L6M MDE 26.3k); S73 +11.9k / +13.2k / +11.4k / +42.8k / +2.0k / +2.8k (MDE 23.1k). Measured (M) basis stays >= 0 in all five windows on both bases; live-cal (LIVE) >= 0 except PRE -0.04k (MKT). It fires 5.2 times per week and is 5.2 of the 14.7 events per week of the pooled rule. Placebo (200 random 50% cuts at the same fire rate, same time-since-first-entry, same first-entry-session stratum): MKT pending; S73 pending. 8 of 12 quarters positive (MKT), 7 of 12 (S73). Tier: **CANDIDATE-RECENT (selected on a post-hoc premise)**; SHADOW only.
5. **Caps (4b): all-session same-side caps are dead.** 0 of 32 all-session cells (6/8/10/12 live lots x room/skip x count rule, mapping A) is >= 0 in PRE and X' on either base (PRE -0.4k..-29.6k per week, X' -15.9k..+1.4k). The pre-session (08:30-09:30 ET) cap stays a LEAD only: 19 of 32 pre-session cells are >= 0 in PRE and X' on the x2.35 mapping (MKT 4 of 8, S73 15 of 24; 14 of them also >= 0 in L6M and HOLD), but under the user's example-stack lots the sign is unstable beyond 8 lots (table in section 5), and it is $1-5k per week.
6. **First-target mirror (4c): dead.** Tightening the rest to breakeven (stack average or own entry) after the first target loses -19k..-26k per week in PRE and -6k..-12k in X' on both bases; "MAE+10" loses -14k..-19k in PRE; recent windows are mixed (MAE+10 MKT L6M +9.2k, S73 +3.2k). "Leave" is the base.
7. **"First L2/TH cut counts as a stop" cannot be tested on the research libraries** (no L2-cut exits exist in them: exit_type 2 is the 16:54 ET session flatten, 1,193 of 1,342 such exits, so `stopdef=1` is identical to `stopdef=0` to the dollar). A proxy (the first same-side book whose own unrealised is -20 / -30 / -40 pts is exited at the market, the rest cut 50%) loses -14.5k..-21.2k per week in PRE on MKT and -12k..-24k on S73, and adding the stack cut to the early exit is worse in PRE at 30 and 40 pts on both bases (-2k to -8k). No support for treating a live L2/TH cut as a stop. Question for the user in MORNING.md.
8. **Composition (for the Sunday stack line): the rule does not add on top of an ER sizer.** S73 + an example ER sizer (x0.5 below 0.3, x1.5 at/above 0.4) already lifts L6M from 79k to 91k per week; the Asia-stopped cut then adds only +1.3k L6M, +1.0k HOLD, -1.6k PRE (against +13.2k / +11.4k / +2.0k on the plain S73 base). The three together are not additive: the stack rule and the sizer remove the same bad stack states. API for SP2 is in section 10.

## 2. The one-page QUANT header (basis N; $/wk = stack delta at research lots vs the same base on the lock engine; CI = 4-week-block bootstrap of the weekly delta; per-contract = lot-weighted points; live A = research lots / 2.35 for every book, live B = the user's example stack P6 5, K6 3, M6 3, H6 1 with ST and WT at research/2.35)

Capacity is NOT measured (the mbp-10 depth is not joined to the cut seconds; each event is a 1-lot slice on the live 2-s schedule: a 50% cut of a 5-book stack = ~9 lots = ~18 s). Window "works in" is stated per row. Tier text: LEAD = >= 0 in PRE, X', HOLD, L6M, L3M but fails RC/RW/DSR; CANDIDATE-RECENT = same with the placebo rank >= 0.90 and the premise post-hoc; none PASS.

| cell | base | $/wk [week-block CI] L3M | L6M | HOLD | PRE | X' | 2026 | pts/planned lot L6M | pts/contract (rule vs base) L6M | events/wk | 1 of | RC p | RW | DSR (202) | PBO | placebo rank L6M / PRE / X' | sibling mean PRE+X' | breakeven extra exit cost (pts) | latency 1s / 3s L6M | capacity | top-5% share | corr(Δ,stack) L6M | works in | quarters + | live A L6M / PRE | live B L6M / PRE | eq-risk Δ HOLD / PRE / X' | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| POOLED first-stop cut P50 (post-hoc premise) | MKT | 35,745 [5,614 to 64,655] | 22,975 [2,473 to 44,959] | 19,319 [780 to 40,002] | -8,219 [-17,534 to 1,824] | 676 [-10,959 to 12,441] | 69,066 | 1.20 | 3.75 vs 3.21 | 14.68 | 1 of 202 | 0.72 | N (p 1.00) | 0.000 | 0.12 | n/a | -5,701 | 3.7 | 23,270 / 22,174 | not measured (needs top-5 depth at the cut seconds) |  | -0.22 | all sessions (pooled) | 5/12 | 9,777 / -3,497 | 7,520 / -5,732 | 41,544 / -5,742 / 389 | CANDIDATE-RECENT per SP-1 (post-hoc premise; PRE -8.2k/-6.5k fails; do not run pooled) |
| first-stop cut P50, stopped book in Asia | MKT | 17,464 [12 to 38,455] | 20,243 [5,087 to 37,657] | 16,499 [2,532 to 33,044] | 916 [-5,921 to 8,678] | 3,706 [-3,491 to 11,326] | 36,167 | 1.06 | 3.69 vs 3.21 | 5.24 | 1 of 202 | 0.72 | N (p 0.96) | 0.001 | 0.12 | n/a | -2,464 | 7.8 | 20,510 / 19,839 | not measured (needs top-5 depth at the cut seconds) | 0.21 | -0.26 | stopped book entered 18:00-02:00 ET (Asia) | 8/12 | 8,614 / 390 | 5,561 / -1,458 | 38,294 / 2,850 / 3,455 | LEAD (>=0 in PRE, X', HOLD, L6M, L3M; within MDE; fails RW/DSR) |
| first-stop cut P100, stopped book in Asia | MKT | 11,052 [-19,814 to 42,513] | 12,510 [-8,569 to 34,287] | 9,815 [-8,763 to 30,342] | 1,397 [-9,149 to 12,258] | 2,962 [-9,283 to 14,639] | 36,179 | 0.65 | 3.41 vs 3.21 | 5.07 | 1 of 202 | 0.72 | N (p 0.98) | 0.001 | 0.12 | n/a | -37 | 6.4 | 14,612 / 14,959 | not measured (needs top-5 depth at the cut seconds) | 0.21 | -0.41 | stopped book entered 18:00-02:00 ET (Asia) | 8/12 | 5,323 / 595 | 957 / -783 | 23,876 / 6,364 / 1,646 | LEAD (>=0 in PRE, X', HOLD, L6M, L3M; within MDE; fails RW/DSR) |
| cut P50, entry-day vol tercile >=2 | MKT | 16,350 [6,208 to 26,387] | 12,402 [1,479 to 22,220] | 10,791 [1,143 to 20,335] | 253 [-6,683 to 7,700] | 4,691 [-2,089 to 11,683] | 26,744 | 0.65 | 3.52 vs 3.21 | 6.14 | 1 of 202 | 0.72 | N (p 0.97) | 0.002 | 0.12 | n/a | -2,462 | 2.7 | 12,804 / 11,534 | not measured (needs top-5 depth at the cut seconds) |  | -0.14 | high-vol entry day | 8/12 | 5,277 / 108 | 5,478 / -2,095 | 15,697 / 2,551 / 6,597 | LEAD (>=0 in PRE, X', HOLD, L6M, L3M; within MDE; fails RW/DSR) |
| cut P50, Asia & vol tercile 2 | MKT | 9,806 [-1,251 to 21,001] | 12,351 [3,492 to 22,267] | 10,174 [1,261 to 20,357] | 3,583 [-2,191 to 9,671] | 6,057 [1,207 to 10,892] | 15,556 | 0.64 | 3.52 vs 3.21 | 2.43 | 1 of 202 | 0.72 | N (p 0.35) | 0.031 | 0.12 | n/a | 581 | 5.3 | 13,492 / 12,095 | not measured (needs top-5 depth at the cut seconds) | 0.21 | -0.23 | stopped book entered 18:00-02:00 ET, high-vol entry day (tercile 2) | 11/12 | 5,256 / 1,525 | 4,163 / -323 | 17,452 / 6,086 / 6,923 | LEAD (>=0 in PRE, X', HOLD, L6M, L3M; within MDE; fails RW/DSR) |
| cut P50, <=2 other books open | MKT | 22,343 [2,436 to 44,692] | 11,509 [-1,962 to 28,281] | 11,877 [26 to 26,963] | 2,445 [-2,553 to 7,786] | 1,603 [-3,800 to 7,168] | 45,372 | 0.60 | 3.50 vs 3.21 | 8.02 | 1 of 202 | 0.72 | N (p 0.90) | 0.003 | 0.12 | n/a | 2,541 | 3.3 | 11,496 / 12,756 | not measured (needs top-5 depth at the cut seconds) |  | -0.17 | small stacks (<=2 other books open) | 9/12 | 4,897 / 1,041 | 4,907 / 530 | 22,786 / 2,404 / 1,750 | LEAD (>=0 in PRE, X', HOLD, L6M, L3M; within MDE; fails RW/DSR) |
| cut P50, ER20(5m) >=0.4 at stopped signal | MKT | 7,973 [-242 to 16,008] | 7,428 [2,096 to 12,863] | 5,452 [-410 to 11,374] | 2,740 [-4,682 to 10,718] | 1,859 [-2,970 to 6,775] | 14,606 | 0.39 | 3.43 vs 3.21 | 3.70 | 1 of 202 | 0.72 | N (p 0.94) | 0.004 | 0.12 | n/a | -2,486 | 8.6 | 6,930 / 7,351 | not measured (needs top-5 depth at the cut seconds) | 0.20 | 0.01 | trending 5m (ER20>=0.4) at the stopped signal | 7/12 | 3,161 / 1,166 | 3,476 / 410 | 6,692 / 5,357 / 1,189 | LEAD (>=0 in PRE, X', HOLD, L6M, L3M; within MDE; fails RW/DSR) |
| cut P50, Asia & ER>=0.4 | MKT | 3,456 [-3,302 to 9,795] | 5,011 [-2,260 to 13,933] | 2,810 [-4,563 to 11,209] | 334 [-5,117 to 6,397] | 2,895 [-966 to 6,737] | 8,274 | 0.26 | 3.35 vs 3.21 | 1.27 | 1 of 202 | 0.72 | N (p 0.97) | 0.002 | 0.12 | n/a | 1,653 | -105.1 | 5,014 / 5,223 | not measured (needs top-5 depth at the cut seconds) | 0.19 | 0.01 | stopped book entered 18:00-02:00 ET, 5m ER20>=0.4 | 7/12 | 2,132 / 142 | 2,306 / -359 | 1,823 / -898 / 2,820 | LEAD (>=0 in PRE, X', HOLD, L6M, L3M; within MDE; fails RW/DSR) |
| cut P50, >=1 book open on the other side | MKT | -2,836 [-10,291 to 4,544] | 4,022 [-3,837 to 13,203] | 4,333 [-2,783 to 12,607] | 4,360 [-659 to 9,943] | 4,380 [-2,546 to 12,051] | 5,290 | 0.21 | 3.26 vs 3.21 | 3.23 | 1 of 202 | 0.72 | N (p 0.39) | 0.019 | 0.12 | n/a | 1,424 | 3.5 | 5,463 / 5,213 | not measured (needs top-5 depth at the cut seconds) | 0.20 | 0.00 | mixed stack (a book open on the other side) | 10/12 | 1,712 / 1,855 | -401 / 1,294 | 10,886 / 7,576 / 5,214 | LEAD/weak |
| pre-session cap 8 live lots (skip), open-lots count | MKT | 4,521 [-3,426 to 17,198] | 2,563 [-5,591 to 10,750] | 3,862 [-3,433 to 11,552] | 1,559 [-4,154 to 7,966] | 3,111 [-3,717 to 11,051] | -2,433 | 0.13 | 3.36 vs 3.21 | n/a | 1 of 202 | 0.72 | N (p 0.94) | 0.005 | 0.12 | n/a | -7,925 |  |  | not measured (needs top-5 depth at the cut seconds) |  | -0.16 | pre-session (08:30-09:30 ET) entries only | 7/12 | 1,091 / 663 | 1,169 / 319 | 7,217 / 6,768 / 6,371 | LEAD (>=0 in PRE, X', HOLD, L6M, L3M; within MDE; fails RW/DSR) |
| pre-session cap 10 live lots (skip) | MKT | 5,531 [-1,184 to 16,886] | 2,789 [-2,572 to 9,191] | 2,940 [-1,623 to 8,681] | 1,493 [-3,246 to 6,646] | 1,180 [-3,347 to 5,933] | -639 | 0.15 | 3.37 vs 3.21 | n/a | 1 of 202 | 0.72 | N (p 0.96) | 0.003 | 0.12 | n/a | -7,874 |  |  | not measured (needs top-5 depth at the cut seconds) |  | -0.19 | pre-session (08:30-09:30 ET) entries only | 7/12 | 1,187 / 635 | 1,480 / 783 | 6,378 / 4,953 / 3,002 | LEAD (>=0 in PRE, X', HOLD, L6M, L3M; within MDE; fails RW/DSR) |
| POOLED first-stop cut P50 (post-hoc premise) | S73 | 16,001 [-10,533 to 43,319] | 6,617 [-13,179 to 27,202] | 4,615 [-13,260 to 23,940] | -6,458 [-16,234 to 4,585] | -448 [-12,589 to 12,128] | 49,158 | 0.34 | 3.83 vs 4.10 | 14.60 | 1 of 202 | 0.76 | N (p 1.00) | 0.000 | 0.10 | n/a | -4,923 | 1.4 | 8,708 / 4,295 | not measured (needs top-5 depth at the cut seconds) |  | -0.26 | all sessions (pooled) | 6/12 | 2,816 / -2,748 | 2,863 / -3,896 | 4,741 / -2,087 / -840 | CANDIDATE-RECENT per SP-1 (post-hoc premise; PRE -8.2k/-6.5k fails; do not run pooled) |
| first-stop cut P50, stopped book in Asia | S73 | 11,874 [-8,305 to 37,665] | 13,191 [-4,354 to 32,083] | 11,391 [-3,626 to 29,133] | 2,005 [-5,876 to 10,857] | 2,818 [-4,757 to 10,720] | 42,829 | 0.68 | 4.20 vs 4.10 | 5.21 | 1 of 202 | 0.76 | N (p 0.98) | 0.000 | 0.10 | n/a | -2,510 | 3.5 | 11,854 / 7,910 | not measured (needs top-5 depth at the cut seconds) | 0.20 | -0.34 | stopped book entered 18:00-02:00 ET (Asia) | 7/12 | 5,613 / 853 | 5,368 / -1,261 | 59,492 / 1,372 / 2,007 | LEAD (>=0 in PRE, X', HOLD, L6M, L3M; within MDE; fails RW/DSR) |
| first-stop cut P100, stopped book in Asia | S73 | 14,936 [-14,405 to 46,080] | 11,799 [-11,041 to 35,643] | 9,860 [-10,674 to 31,786] | 5,345 [-3,769 to 15,848] | 2,217 [-8,802 to 12,681] | 48,215 | 0.61 | 4.21 vs 4.10 | 5.10 | 1 of 202 | 0.76 | N (p 0.94) | 0.001 | 0.10 | n/a | 190 | 3.1 | 8,514 / 10,890 | not measured (needs top-5 depth at the cut seconds) | 0.20 | -0.47 | stopped book entered 18:00-02:00 ET (Asia) | 7/12 | 5,021 / 2,274 | 2,116 / 977 | 87,151 / 14,242 / 240 | LEAD (>=0 in PRE, X', HOLD, L6M, L3M; within MDE; fails RW/DSR) |
| cut P50, Asia & vol tercile 2 | S73 | 5,535 [-9,351 to 26,247] | 6,801 [-6,450 to 21,314] | 6,461 [-4,911 to 19,408] | 4,548 [-932 to 10,338] | 4,742 [18 to 9,199] | 28,725 | 0.35 | 4.12 vs 4.10 | 2.40 | 1 of 202 | 0.76 | N (p 0.35) | 0.007 | 0.10 | n/a | 1,715 | 2.1 | 5,415 / 2,904 | not measured (needs top-5 depth at the cut seconds) | 0.21 | -0.33 | stopped book entered 18:00-02:00 ET, high-vol entry day (tercile 2) | 10/12 | 2,894 / 1,935 | 4,811 / 116 | 29,504 / 6,826 / 5,126 | LEAD (>=0 in PRE, X', HOLD, L6M, L3M; within MDE; fails RW/DSR) |
| cut P50, >=1 book open on the other side | S73 | 3,261 [-7,869 to 13,534] | 4,793 [-4,668 to 13,936] | 4,594 [-3,574 to 13,109] | 2,792 [-2,770 to 9,074] | 4,182 [-2,999 to 12,322] | 13,442 | 0.25 | 4.15 vs 4.10 | 3.32 | 1 of 202 | 0.76 | N (p 0.88) | 0.001 | 0.10 | n/a | 448 | 30.5 | 4,699 / 4,509 | not measured (needs top-5 depth at the cut seconds) | 0.20 | 0.08 | mixed stack (a book open on the other side) | 7/12 | 2,039 / 1,188 | -177 / 625 | 12,450 / 4,520 / 5,444 | LEAD (>=0 in PRE, X', HOLD, L6M, L3M; within MDE; fails RW/DSR) |
| cut P50, Asia & ER>=0.4 | S73 | 1,765 [-4,240 to 7,097] | 1,904 [-2,975 to 7,345] | 691 [-4,285 to 6,052] | 3,338 [-1,917 to 9,369] | 2,998 [-1,514 to 7,385] | 7,684 | 0.10 | 4.07 vs 4.10 | 1.30 | 1 of 202 | 0.76 | N (p 0.81) | 0.005 | 0.10 | n/a | 2,184 | 7.7 | 1,850 / 1,974 | not measured (needs top-5 depth at the cut seconds) | 0.19 | -0.04 | stopped book entered 18:00-02:00 ET, 5m ER20>=0.4 | 8/12 | 810 / 1,421 | 460 / 701 | -3,725 / 6,121 / 2,848 | LEAD (>=0 in PRE, X', HOLD, L6M, L3M; within MDE; fails RW/DSR) |
| pre-session cap 8 live (skip), open-lots count | S73 | 1,314 [-8,555 to 15,128] | 2,465 [-4,264 to 9,452] | 2,735 [-3,406 to 9,312] | 2,985 [-1,627 to 8,076] | 1,101 [-3,984 to 6,816] | -6,470 | 0.13 | 4.25 vs 4.10 | n/a | 1 of 202 | 0.76 | N (p 0.93) | 0.001 | 0.10 | n/a | -5,621 |  |  | not measured (needs top-5 depth at the cut seconds) |  | -0.28 | pre-session (08:30-09:30 ET) entries only | 8/12 | 1,049 / 1,270 | 758 / 1,533 | 15,177 / 9,045 / 3,725 | LEAD (>=0 in PRE, X', HOLD, L6M, L3M; within MDE; fails RW/DSR) |
| pre-session cap 8 live (skip), both legs (100%) reserved | S73 | 2,080 [-7,998 to 16,206] | 3,496 [-4,014 to 11,464] | 4,265 [-2,675 to 11,799] | 3,771 [-1,561 to 9,630] | 326 [-5,659 to 6,976] | -4,775 | 0.18 | 4.31 vs 4.10 | n/a | 1 of 202 | 0.76 | N (p 0.94) | 0.001 | 0.10 | n/a | -5,626 |  |  | not measured (needs top-5 depth at the cut seconds) |  | -0.25 | pre-session (08:30-09:30 ET) entries only | 8/12 | 1,488 / 1,605 | 1,082 / 1,220 | 19,270 / 12,577 / 2,505 | LEAD (>=0 in PRE, X', HOLD, L6M, L3M; within MDE; fails RW/DSR) |
| pre-session cap 6 live (skip), 70% leg only | S73 | 931 [-9,143 to 14,744] | 1,286 [-5,909 to 9,039] | 2,318 [-4,294 to 9,384] | 4,276 [-821 to 9,917] | 1,146 [-4,671 to 7,741] | -6,470 | 0.07 | 4.21 vs 4.10 | n/a | 1 of 202 | 0.76 | N (p 0.84) | 0.003 | 0.10 | n/a | -5,639 |  |  | not measured (needs top-5 depth at the cut seconds) |  | -0.36 | pre-session (08:30-09:30 ET) entries only | 8/12 | 547 / 1,820 | 476 / 1,581 | 15,579 / 12,900 / 3,904 | LEAD (>=0 in PRE, X', HOLD, L6M, L3M; within MDE; fails RW/DSR) |
| pre-session cap 8 live (skip), 70% leg only | S73 | 1,075 [-3,983 to 7,263] | 1,184 [-3,052 to 5,430] | 1,540 [-2,288 to 5,657] | 3,771 [184 to 7,594] | 549 [-4,119 to 5,746] | -2,946 | 0.06 | 4.19 vs 4.10 | n/a | 1 of 202 | 0.76 | N (p 0.76) | 0.003 | 0.10 | n/a | -5,627 |  |  | not measured (needs top-5 depth at the cut seconds) |  | -0.31 | pre-session (08:30-09:30 ET) entries only | 8/12 | 504 / 1,605 | -58 / 1,431 | 12,084 / 9,404 / 2,424 | LEAD (>=0 in PRE, X', HOLD, L6M, L3M; within MDE; fails RW/DSR) |

Reading the header: every L6M / HOLD interval contains zero except the MKT Asia and vol-tercile rows; every PRE and X' interval contains zero (the PRE+X' effects are +0.3k..+6k per week against an MDE of 8-13k). The stack line (mean / SD / maxDD / worst-20 weeks, basis N, research lots, recent first):

| cell | base | window | base mean / SD / maxDD / worst-20 | rule mean / SD / maxDD / worst-20 |
|---|---|---|---|---|
| pooled cut P50 | MKT | L3M | 11,050 / 139,632 / 372,191 / 154,698 | 46,795 / 152,692 / 471,709 / 655,126 |
| pooled cut P50 | MKT | L6M | 61,477 / 145,923 / 372,191 / -152,965 | 84,453 / 143,852 / 471,709 / 311,975 |
| pooled cut P50 | MKT | HOLD | 48,332 / 172,952 / 651,457 / -1,094,574 | 67,651 / 178,591 / 707,870 / -823,897 |
| pooled cut P50 | MKT | PRE | 58,040 / 138,689 / 703,664 / -2,417,606 | 49,821 / 133,270 / 667,666 / -2,303,105 |
| pooled cut P50 | MKT | X | 16,045 / 103,650 / 489,904 / -1,457,114 | 16,721 / 104,654 / 426,329 / -1,482,577 |
| Asia-stopped cut P50 | MKT | L3M | 11,050 / 139,632 / 372,191 / 154,698 | 28,514 / 143,297 / 401,864 / 399,194 |
| Asia-stopped cut P50 | MKT | L6M | 61,477 / 145,923 / 372,191 / -152,965 | 81,720 / 141,514 / 401,864 / 238,509 |
| Asia-stopped cut P50 | MKT | HOLD | 48,332 / 172,952 / 651,457 / -1,094,574 | 64,832 / 171,913 / 671,559 / -819,191 |
| Asia-stopped cut P50 | MKT | PRE | 58,040 / 138,689 / 703,664 / -2,417,606 | 58,956 / 139,877 / 710,479 / -2,340,819 |
| Asia-stopped cut P50 | MKT | X | 16,045 / 103,650 / 489,904 / -1,457,114 | 19,752 / 105,789 / 460,335 / -1,475,928 |
| Asia-stopped cut P50 | S73 | L3M | 31,261 / 130,314 / 318,846 / 437,655 | 43,135 / 131,968 / 370,447 / 603,892 |
| Asia-stopped cut P50 | S73 | L6M | 79,055 / 136,536 / 318,846 / 332,332 | 92,246 / 128,640 / 370,447 / 620,116 |
| Asia-stopped cut P50 | S73 | HOLD | 66,693 / 169,113 / 624,547 / -630,207 | 78,084 / 163,136 / 607,751 / -389,975 |
| Asia-stopped cut P50 | S73 | PRE | 61,831 / 138,576 / 614,903 / -2,304,704 | 63,836 / 142,343 / 747,957 / -2,327,806 |
| Asia-stopped cut P50 | S73 | X | 18,206 / 101,638 / 469,146 / -1,392,026 | 21,023 / 106,031 / 449,659 / -1,447,877 |
| opp-book cut P50 | MKT | L3M | 11,050 / 139,632 / 372,191 / 154,698 | 8,214 / 146,805 / 427,175 / 114,993 |
| opp-book cut P50 | MKT | L6M | 61,477 / 145,923 / 372,191 / -152,965 | 65,500 / 148,025 / 427,175 / -80,510 |
| opp-book cut P50 | MKT | HOLD | 48,332 / 172,952 / 651,457 / -1,094,574 | 52,665 / 173,020 / 611,833 / -973,443 |
| opp-book cut P50 | MKT | PRE | 58,040 / 138,689 / 703,664 / -2,417,606 | 62,400 / 142,450 / 555,287 / -2,299,106 |
| opp-book cut P50 | MKT | X | 16,045 / 103,650 / 489,904 / -1,457,114 | 20,425 / 102,359 / 473,754 / -1,399,944 |
| opp-book cut P50 | S73 | L3M | 31,261 / 130,314 / 318,846 / 437,655 | 34,522 / 147,564 / 333,361 / 483,312 |
| opp-book cut P50 | S73 | L6M | 79,055 / 136,536 / 318,846 / 332,332 | 83,848 / 141,971 / 333,361 / 376,553 |
| opp-book cut P50 | S73 | HOLD | 66,693 / 169,113 / 624,547 / -630,207 | 71,287 / 172,025 / 590,154 / -567,652 |
| opp-book cut P50 | S73 | PRE | 61,831 / 138,576 / 614,903 / -2,304,704 | 64,622 / 142,993 / 607,609 / -2,244,670 |
| opp-book cut P50 | S73 | X | 18,206 / 101,638 / 469,146 / -1,392,026 | 22,388 / 101,835 / 462,560 / -1,317,744 |

## 3. (a) First stop -> cut the rest: every variant, recent first (tables: delta $/wk, N basis, research lots; MDE = 2.8 SE of the weekly L6M delta; 'carried' = delta >= 0 in both PRE and X')

Answers in one line each: **cut size** - recent gain peaks at 50% (MKT L6M P25 +11.7k, P50 +23.0k, P75 +13.5k, P100 +10.4k) and PRE gets monotonically worse as P rises (-7.4k, -8.2k, -9.6k, -11.6k). **L2/TH cut counts as a stop** - identical to stop-only (no such exits in the libraries) and the proxy is negative (section 1.7). **Only when >= 2 other books are on** - drops the recent gain (L6M 16.5k vs 23.0k) and keeps the PRE loss (-7.7k): the small-stack events are not the problem, the 4-other-books events are (others <= 3: PRE -2.7k, X' +6.5k, L6M +20.1k; others <= 2: PRE +2.4k, X' +1.6k, L6M +11.5k, MKT only). **Only same-side** - both-sides scope is worse everywhere (PRE -12.3k, X' -4.9k). **Within N minutes of the stopped entry** - the shorter the window, the closer to zero and the fewer the events (5 min: 0.7/wk, 10 min: 1.8/wk, +3.8k L6M, PRE -0.3k; 60 min: 9.8/wk, +17.1k L6M, PRE -11.7k); it behaves as a thinning of the pooled rule, not as a filter that finds the winners. Reference to the stack's first entry gives the same shape. **Re-entry blocked for the rest of the hour** - more recent gain (L6M +27.7k, L3M +53.8k) and a deeper PRE loss (-16.8k, X' -2.4k); blocking 30 minutes is similar. **Re-arm on every stop** - same as first-stop only (the first stop is the whole effect).


#### A1/A3 first-stop cut: P and stop definition, windows (recent-first)

**MKT** (delta stack $/wk at research lots, basis N, vs the same MKT base; MDE = 2.8 SE of the L6M weekly delta; live A = research/2.35, live B = example stack lots; fires/wk = rule events per week)

| cell | carried(PRE&X>=0) | L3M | L6M | HOLD | 2026 | PRE | X' | MDE L6M | live A L6M | live B L6M | live A PRE | fires/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| fs ; P=25 ; stopdef=0 |  | 10,202 | 11,710 | 9,678 | 45,577 | -7,375 | 658 | 19,537 | 4,983 | 1,721 | -3,138 | 14.4 |
| fs ; P=25 ; stopdef=1 |  | 10,202 | 11,710 | 9,678 | 45,577 | -7,375 | 658 | 19,537 | 4,983 | 1,721 | -3,138 | 14.4 |
| fs ; P=50 ; stopdef=0 |  | 35,745 | 22,975 | 19,319 | 69,066 | -8,219 | 676 | 28,540 | 9,777 | 7,520 | -3,497 | 14.7 |
| fs ; P=50 ; stopdef=1 |  | 35,745 | 22,975 | 19,319 | 69,066 | -8,219 | 676 | 28,540 | 9,777 | 7,520 | -3,497 | 14.7 |
| fs ; P=75 ; stopdef=0 |  | 29,608 | 13,481 | 11,437 | 68,595 | -9,609 | -1,022 | 34,051 | 5,737 | 3,333 | -4,089 | 14.5 |
| fs ; P=75 ; stopdef=1 |  | 29,608 | 13,481 | 11,437 | 68,595 | -9,609 | -1,022 | 34,051 | 5,737 | 3,333 | -4,089 | 14.5 |
| fs ; P=100 ; stopdef=0 |  | 26,542 | 10,376 | 7,908 | 70,061 | -11,621 | 1,825 | 44,227 | 4,415 | 944 | -4,945 | 13.5 |
| fs ; P=100 ; stopdef=1 |  | 26,542 | 10,376 | 7,908 | 70,061 | -11,621 | 1,825 | 44,227 | 4,415 | 944 | -4,945 | 13.5 |
| fs ; P=100 ; win=10m ; ref=stoppedEntry |  | -128 | -3,045 | -3,226 | 27,833 | -1,795 | -1,617 | 23,731 | -1,296 | -919 | -764 | 1.8 |
| fs ; P=100 ; win=30m ; ref=stoppedEntry |  | 5,844 | 11,474 | 9,907 | 27,057 | -13,504 | -4,413 | 30,300 | 4,883 | 4,854 | -5,746 | 5.3 |
| fs ; P=100 ; others>=2 |  | 19,908 | 7,496 | 4,915 | 56,324 | -8,531 | 178 | 42,676 | 3,190 | 1,049 | -3,630 | 9.1 |
| fs ; P=25 ; win=10m ; ref=stoppedEntry | Y | -3,281 | -2,195 | -2,747 | 14,399 | 1,356 | 349 | 12,105 | -934 | -542 | 577 | 1.8 |
| fs ; P=25 ; win=30m ; ref=stoppedEntry |  | 2,548 | 5,581 | 2,973 | 23,282 | -6,673 | -437 | 15,213 | 2,375 | 2,518 | -2,840 | 5.7 |
**S73** (delta stack $/wk at research lots, basis N, vs the same S73 base; MDE = 2.8 SE of the L6M weekly delta; live A = research/2.35, live B = example stack lots; fires/wk = rule events per week)

| cell | carried(PRE&X>=0) | L3M | L6M | HOLD | 2026 | PRE | X' | MDE L6M | live A L6M | live B L6M | live A PRE | fires/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| fs ; P=25 ; stopdef=0 |  | 4,526 | 4,072 | 3,138 | 27,300 | -7,192 | 1,197 | 22,218 | 1,733 | 1,779 | -3,061 | 14.4 |
| fs ; P=25 ; stopdef=1 |  | 4,526 | 4,072 | 3,138 | 27,300 | -7,192 | 1,197 | 22,218 | 1,733 | 1,779 | -3,061 | 14.4 |
| fs ; P=50 ; stopdef=0 |  | 16,001 | 6,617 | 4,615 | 49,158 | -6,458 | -448 | 26,834 | 2,816 | 2,863 | -2,748 | 14.6 |
| fs ; P=50 ; stopdef=1 |  | 16,001 | 6,617 | 4,615 | 49,158 | -6,458 | -448 | 26,834 | 2,816 | 2,863 | -2,748 | 14.6 |
| fs ; P=75 ; stopdef=0 |  | 28,946 | 10,392 | 8,026 | 67,052 | -8,109 | -339 | 34,382 | 4,422 | 3,752 | -3,451 | 14.6 |
| fs ; P=75 ; stopdef=1 |  | 28,946 | 10,392 | 8,026 | 67,052 | -8,109 | -339 | 34,382 | 4,422 | 3,752 | -3,451 | 14.6 |
| fs ; P=100 ; stopdef=0 |  | 27,782 | 4,576 | 3,136 | 65,072 | -9,374 | 334 | 42,151 | 1,947 | -925 | -3,989 | 13.5 |
| fs ; P=100 ; stopdef=1 |  | 27,782 | 4,576 | 3,136 | 65,072 | -9,374 | 334 | 42,151 | 1,947 | -925 | -3,989 | 13.5 |
| fs ; P=100 ; win=10m ; ref=stoppedEntry |  | -1,385 | -4,233 | -3,388 | 29,333 | 664 | -1,533 | 26,348 | -1,801 | -937 | 283 | 1.7 |
| fs ; P=100 ; win=30m ; ref=stoppedEntry |  | 5,106 | 8,113 | 6,894 | 30,171 | -11,345 | -5,370 | 31,271 | 3,452 | 3,485 | -4,828 | 5.4 |
| fs ; P=100 ; others>=2 |  | 18,069 | 902 | -857 | 50,853 | -9,202 | -1,132 | 40,535 | 384 | -1,856 | -3,916 | 8.9 |
| fs ; P=25 ; win=10m ; ref=stoppedEntry |  | 1,092 | 1,021 | 742 | 19,817 | 1,955 | -367 | 14,681 | 435 | 1,370 | 832 | 1.8 |
| fs ; P=25 ; win=30m ; ref=stoppedEntry |  | -4,034 | 2,227 | 1,699 | 7,828 | -5,134 | -1,561 | 16,576 | 948 | 2,013 | -2,185 | 5.8 |

#### A2 first-stop cut variants at P=50

**MKT** (delta stack $/wk at research lots, basis N, vs the same MKT base; MDE = 2.8 SE of the L6M weekly delta; live A = research/2.35, live B = example stack lots; fires/wk = rule events per week)

| cell | carried(PRE&X>=0) | L3M | L6M | HOLD | 2026 | PRE | X' | MDE L6M | live A L6M | live B L6M | live A PRE | fires/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| fs ; P=50 ; others>=2 |  | 25,321 | 16,473 | 13,680 | 42,197 | -7,729 | -101 | 26,379 | 7,010 | 5,060 | -3,289 | 10.1 |
| fs ; P=50 ; scope=both |  | 30,992 | 17,676 | 13,343 | 60,468 | -12,300 | -4,920 | 34,809 | 7,522 | 2,765 | -5,234 | 14.7 |
| fs ; P=50 ; win=5m ; ref=stoppedEntry |  | 839 | -744 | -955 | 1,017 | 630 | -318 | 3,658 | -317 | -221 | 268 | 0.7 |
| fs ; P=50 ; win=10m ; ref=stoppedEntry |  | 6,129 | 3,752 | 2,385 | 22,466 | -285 | -488 | 13,543 | 1,596 | 2,382 | -121 | 1.8 |
| fs ; P=50 ; win=20m ; ref=stoppedEntry |  | 9,533 | 5,960 | 4,246 | 29,247 | -4,026 | 168 | 13,699 | 2,536 | 4,583 | -1,713 | 4.0 |
| fs ; P=50 ; win=30m ; ref=stoppedEntry |  | 8,946 | 12,314 | 10,005 | 28,939 | -7,362 | -1,386 | 17,502 | 5,240 | 6,097 | -3,133 | 5.8 |
| fs ; P=50 ; win=60m ; ref=stoppedEntry |  | 14,220 | 17,134 | 13,110 | 37,200 | -11,739 | 2,996 | 22,691 | 7,291 | 6,340 | -4,995 | 9.8 |
| fs ; P=50 ; win=10m ; ref=stackFirstEntry |  | 5,814 | 1,669 | 1,461 | 17,801 | -522 | 413 | 8,947 | 710 | 1,305 | -222 | 0.6 |
| fs ; P=50 ; win=30m ; ref=stackFirstEntry |  | 3,360 | -482 | -845 | 22,469 | -294 | 975 | 14,168 | -205 | 1,181 | -125 | 2.5 |
| fs ; P=50 ; win=60m ; ref=stackFirstEntry |  | 5,706 | 6,739 | 4,968 | 29,690 | -6,200 | 1,490 | 16,939 | 2,868 | 2,964 | -2,638 | 5.5 |
| fs ; P=50 ; block=hour |  | 53,840 | 27,717 | 24,859 | 91,803 | -16,777 | -2,400 | 36,254 | 11,795 | 8,782 | -7,139 | 14.4 |
| fs ; P=50 ; block=1800s |  | 55,888 | 32,371 | 27,513 | 83,054 | -12,517 | -2,656 | 34,360 | 13,775 | 11,853 | -5,327 | 14.6 |
| fs ; P=50 ; rearm=1 |  | 36,856 | 23,844 | 19,483 | 68,770 | -8,160 | -655 | 29,335 | 10,146 | 8,467 | -3,472 | 31.8 |
**S73** (delta stack $/wk at research lots, basis N, vs the same S73 base; MDE = 2.8 SE of the L6M weekly delta; live A = research/2.35, live B = example stack lots; fires/wk = rule events per week)

| cell | carried(PRE&X>=0) | L3M | L6M | HOLD | 2026 | PRE | X' | MDE L6M | live A L6M | live B L6M | live A PRE | fires/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| fs ; P=50 ; others>=2 |  | 5,093 | -73 | -932 | 22,345 | -5,908 | -661 | 23,343 | -31 | -148 | -2,514 | 9.8 |
| fs ; P=50 ; scope=both |  | 14,130 | 4,249 | 1,424 | 47,991 | -11,671 | -5,757 | 31,511 | 1,808 | -460 | -4,966 | 14.6 |
| fs ; P=50 ; win=5m ; ref=stoppedEntry |  | 2,775 | 787 | 372 | 911 | 855 | -638 | 4,644 | 335 | 801 | 364 | 0.6 |
| fs ; P=50 ; win=10m ; ref=stoppedEntry |  | 2,914 | 960 | 845 | 20,227 | 2,067 | -526 | 14,388 | 409 | 1,364 | 880 | 1.8 |
| fs ; P=50 ; win=20m ; ref=stoppedEntry |  | -2,782 | -789 | -1,099 | 16,816 | -1,704 | -1,814 | 17,516 | -336 | 1,715 | -725 | 4.1 |
| fs ; P=50 ; win=30m ; ref=stoppedEntry |  | -1,963 | 4,340 | 4,130 | 15,795 | -7,880 | -2,979 | 19,618 | 1,847 | 3,197 | -3,353 | 5.8 |
| fs ; P=50 ; win=60m ; ref=stoppedEntry |  | -947 | 4,885 | 2,638 | 22,671 | -10,908 | 854 | 24,257 | 2,079 | 2,987 | -4,642 | 9.8 |
| fs ; P=50 ; win=10m ; ref=stackFirstEntry | Y | 2,433 | -366 | -320 | 13,262 | 805 | 460 | 9,980 | -156 | 696 | 343 | 0.6 |
| fs ; P=50 ; win=30m ; ref=stackFirstEntry |  | 1,633 | -1,670 | -714 | 24,192 | -1,812 | 116 | 14,091 | -710 | 997 | -771 | 2.5 |
| fs ; P=50 ; win=60m ; ref=stackFirstEntry |  | 2,976 | 116 | 1,097 | 29,657 | -5,852 | 583 | 18,056 | 50 | 462 | -2,490 | 5.6 |
| fs ; P=50 ; block=hour |  | 44,421 | 18,615 | 16,364 | 78,724 | -12,573 | -1,742 | 35,127 | 7,921 | 7,219 | -5,350 | 14.4 |
| fs ; P=50 ; block=1800s |  | 33,361 | 18,139 | 14,526 | 58,358 | -13,590 | -2,193 | 31,298 | 7,719 | 5,546 | -5,783 | 14.5 |
| fs ; P=50 ; rearm=1 |  | 20,672 | 8,513 | 5,454 | 50,875 | -8,753 | -940 | 27,489 | 3,623 | 3,328 | -3,725 | 31.0 |

#### D first-stop cut P=50 by condition (stopped-row session, ER20 5m, vol tercile)

**MKT** (delta stack $/wk at research lots, basis N, vs the same MKT base; MDE = 2.8 SE of the L6M weekly delta; live A = research/2.35, live B = example stack lots; fires/wk = rule events per week)

| cell | carried(PRE&X>=0) | L3M | L6M | HOLD | 2026 | PRE | X' | MDE L6M | live A L6M | live B L6M | live A PRE | fires/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| fs ; P=50 ; stoppedSession=asia | Y | 17,464 | 20,243 | 16,499 | 36,167 | 916 | 3,706 | 26,285 | 8,614 | 5,561 | 390 | 5.2 |
| fs ; P=50 ; stoppedSession!=asia |  | 10,568 | 6,013 | 4,939 | 19,087 | -9,190 | -2,728 | 17,004 | 2,559 | 1,995 | -3,911 | 8.6 |
| fs ; P=50 ; stoppedSession=london |  | 8,966 | 5,894 | 4,715 | 20,123 | -6,101 | 2,744 | 17,321 | 2,508 | 1,299 | -2,596 | 3.1 |
| fs ; P=50 ; stoppedSession!=london |  | 25,870 | 23,965 | 19,370 | 46,264 | -3,084 | -38 | 27,539 | 10,198 | 7,769 | -1,312 | 11.2 |
| fs ; P=50 ; stoppedSession=pre | Y | 926 | 480 | 1,173 | -4,286 | 510 | 736 | 5,596 | 204 | 54 | 217 | 0.9 |
| fs ; P=50 ; stoppedSession!=pre |  | 35,021 | 22,714 | 18,467 | 70,211 | -8,275 | -123 | 28,606 | 9,665 | 7,213 | -3,521 | 13.6 |
| fs ; P=50 ; stoppedSession=nyam |  | 4,118 | 3,256 | 2,093 | 2,385 | -2,244 | -5,566 | 6,157 | 1,385 | 2,119 | -955 | 2.9 |
| fs ; P=50 ; stoppedSession!=nyam |  | 29,190 | 19,800 | 16,686 | 60,797 | -5,169 | 4,910 | 28,417 | 8,426 | 5,505 | -2,199 | 11.3 |
| fs ; P=50 ; stoppedSession=nypm |  | -1,170 | -1,075 | -1,145 | -622 | -463 | 785 | 2,863 | -457 | -602 | -197 | 1.2 |
| fs ; P=50 ; stoppedSession!=nypm |  | 35,785 | 23,933 | 21,042 | 67,434 | -7,574 | 964 | 27,383 | 10,184 | 8,017 | -3,223 | 13.1 |
| fs ; P=50 ; stoppedSession=close |  | -0 | -0 | -0 | -0 | 58 | -0 | 0 | -0 | -0 | 25 | 0.0 |
| fs ; P=50 ; stoppedSession!=close |  | 35,745 | 22,975 | 19,319 | 69,066 | -8,345 | 676 | 28,540 | 9,777 | 7,520 | -3,551 | 14.7 |
| fs ; P=50 ; er20_5m>=0.2 |  | 21,684 | 14,524 | 13,939 | 44,086 | -7,372 | 267 | 20,244 | 6,180 | 5,849 | -3,137 | 9.4 |
| fs ; P=50 ; er20_5m<0.2 |  | 11,112 | 9,659 | 6,814 | 20,771 | -2,333 | 2,156 | 16,168 | 4,110 | 1,594 | -993 | 4.7 |
| fs ; P=50 ; er20_5m>=0.3 |  | 12,070 | 7,573 | 8,088 | 29,458 | 1,698 | -586 | 17,867 | 3,223 | 2,295 | 723 | 6.7 |
| fs ; P=50 ; er20_5m<0.3 |  | 17,718 | 18,697 | 13,534 | 23,523 | -7,391 | 2,660 | 20,104 | 7,956 | 6,321 | -3,145 | 7.5 |
| fs ; P=50 ; er20_5m>=0.4 | Y | 7,973 | 7,428 | 5,452 | 14,606 | 2,740 | 1,859 | 11,350 | 3,161 | 3,476 | 1,166 | 3.7 |
| fs ; P=50 ; er20_5m<0.4 |  | 25,531 | 18,059 | 15,610 | 43,873 | -10,138 | 1,876 | 26,557 | 7,685 | 6,073 | -4,314 | 10.6 |
| fs ; P=50 ; voltercile>=1 |  | 31,558 | 19,381 | 18,195 | 53,153 | -960 | 2,771 | 25,828 | 8,247 | 7,750 | -408 | 9.9 |
| fs ; P=50 ; voltercile<1 |  | 4,186 | 3,594 | 1,123 | 15,913 | -7,259 | -2,095 | 15,827 | 1,529 | -230 | -3,089 | 4.8 |
| fs ; P=50 ; voltercile>=2 | Y | 16,350 | 12,402 | 10,791 | 26,744 | 253 | 4,691 | 19,511 | 5,277 | 5,478 | 108 | 6.1 |
| fs ; P=50 ; voltercile<2 |  | 19,395 | 10,574 | 8,528 | 42,321 | -8,472 | -4,015 | 22,712 | 4,500 | 2,043 | -3,605 | 8.5 |
**S73** (delta stack $/wk at research lots, basis N, vs the same S73 base; MDE = 2.8 SE of the L6M weekly delta; live A = research/2.35, live B = example stack lots; fires/wk = rule events per week)

| cell | carried(PRE&X>=0) | L3M | L6M | HOLD | 2026 | PRE | X' | MDE L6M | live A L6M | live B L6M | live A PRE | fires/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| fs ; P=50 ; stoppedSession=asia | Y | 11,874 | 13,191 | 11,391 | 42,829 | 2,005 | 2,818 | 23,119 | 5,613 | 5,368 | 853 | 5.2 |
| fs ; P=50 ; stoppedSession!=asia |  | 3,518 | -1,507 | -2,574 | 8,042 | -8,396 | -4,581 | 16,750 | -641 | -1,039 | -3,573 | 8.8 |
| fs ; P=50 ; stoppedSession=london |  | 2,849 | 20 | -871 | 9,014 | -6,347 | 1,951 | 15,901 | 8 | -992 | -2,701 | 3.2 |
| fs ; P=50 ; stoppedSession!=london |  | 18,631 | 14,699 | 12,179 | 47,553 | -915 | -2,847 | 24,769 | 6,255 | 6,568 | -389 | 11.0 |
| fs ; P=50 ; stoppedSession=pre |  | 3,420 | 1,864 | 2,370 | -2,073 | -36 | -68 | 5,731 | 793 | 715 | -15 | 1.0 |
| fs ; P=50 ; stoppedSession!=pre |  | 13,473 | 5,312 | 2,915 | 49,146 | -6,535 | -873 | 27,168 | 2,260 | 2,095 | -2,781 | 13.6 |
| fs ; P=50 ; stoppedSession=nyam |  | -543 | -1,257 | -1,568 | -3,062 | -2,938 | -6,005 | 5,840 | -535 | -361 | -1,250 | 2.9 |
| fs ; P=50 ; stoppedSession!=nyam |  | 10,607 | 4,736 | 3,617 | 45,853 | -4,446 | 3,354 | 25,500 | 2,015 | 1,767 | -1,892 | 11.1 |
| fs ; P=50 ; stoppedSession=nypm |  | -888 | -370 | -726 | 143 | 181 | -575 | 2,312 | -158 | -17 | 77 | 1.1 |
| fs ; P=50 ; stoppedSession!=nypm |  | 16,244 | 6,203 | 5,274 | 46,937 | -6,300 | 837 | 25,209 | 2,640 | 2,390 | -2,681 | 13.1 |
| fs ; P=50 ; stoppedSession=close | Y | -0 | -0 | -0 | -0 | 42 | 0 | 0 | -0 | 0 | 18 | 0.0 |
| fs ; P=50 ; stoppedSession!=close |  | 16,001 | 6,617 | 4,615 | 49,158 | -6,535 | -448 | 26,834 | 2,816 | 2,863 | -2,781 | 14.6 |
| fs ; P=50 ; er20_5m>=0.2 |  | 12,630 | 4,582 | 5,030 | 30,079 | -7,222 | -1,139 | 17,064 | 1,950 | 1,278 | -3,073 | 9.3 |
| fs ; P=50 ; er20_5m<0.2 |  | -5,351 | -2,315 | -3,788 | 4,667 | -3,609 | 845 | 15,985 | -985 | -1,527 | -1,536 | 4.7 |
| fs ; P=50 ; er20_5m>=0.3 |  | 8,435 | 3,147 | 4,183 | 16,704 | 565 | -2,259 | 16,930 | 1,339 | 179 | 240 | 6.6 |
| fs ; P=50 ; er20_5m<0.3 |  | -3,628 | 3,717 | 236 | 12,874 | -6,254 | 1,647 | 20,791 | 1,582 | 2,312 | -2,661 | 7.4 |
| fs ; P=50 ; er20_5m>=0.4 | Y | 107 | 929 | 608 | 8,633 | 3,647 | 889 | 13,701 | 395 | -43 | 1,552 | 3.8 |
| fs ; P=50 ; er20_5m<0.4 |  | 9,111 | 4,625 | 2,988 | 27,405 | -9,827 | 275 | 24,920 | 1,968 | 2,793 | -4,182 | 10.5 |
| fs ; P=50 ; voltercile>=1 |  | 13,694 | 7,102 | 7,765 | 41,461 | -1,648 | 2,582 | 23,572 | 3,022 | 3,966 | -701 | 9.8 |
| fs ; P=50 ; voltercile<1 |  | 2,307 | -485 | -3,049 | 7,696 | -4,811 | -3,030 | 14,807 | -207 | -1,103 | -2,047 | 4.8 |
| fs ; P=50 ; voltercile>=2 |  | 4,518 | 3,518 | 3,543 | 25,069 | -395 | 3,473 | 20,158 | 1,497 | 3,635 | -168 | 6.0 |
| fs ; P=50 ; voltercile<2 |  | 11,483 | 3,099 | 1,174 | 24,088 | -6,063 | -3,920 | 19,699 | 1,319 | -772 | -2,580 | 8.6 |

#### E1-E3 conditions derived from the PRE+X' decomposition

**MKT** (delta stack $/wk at research lots, basis N, vs the same MKT base; MDE = 2.8 SE of the L6M weekly delta; live A = research/2.35, live B = example stack lots; fires/wk = rule events per week)

| cell | carried(PRE&X>=0) | L3M | L6M | HOLD | 2026 | PRE | X' | MDE L6M | live A L6M | live B L6M | live A PRE | fires/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| fs ; P=50 ; others<=2 | Y | 22,343 | 11,509 | 11,877 | 45,372 | 2,445 | 1,603 | 18,965 | 4,897 | 4,907 | 1,041 | 8.0 |
| fs ; P=50 ; others<=3 |  | 27,530 | 20,060 | 18,650 | 43,975 | -2,698 | 6,529 | 22,340 | 8,536 | 6,727 | -1,148 | 11.5 |
| fs ; P=50 ; oppBooks>=1 | Y | -2,836 | 4,022 | 4,333 | 5,290 | 4,360 | 4,380 | 13,064 | 1,712 | -401 | 1,855 | 3.2 |
| fs ; P=50 ; asia&er20_5m>=0.4 | Y | 3,456 | 5,011 | 2,810 | 8,274 | 334 | 2,895 | 12,399 | 2,132 | 2,306 | 142 | 1.3 |
| fs ; P=50 ; asia&voltercile>=2 | Y | 9,806 | 12,351 | 10,174 | 15,556 | 3,583 | 6,057 | 21,628 | 5,256 | 4,163 | 1,525 | 2.4 |
| fs ; P=50 ; er20_5m>=0.4&voltercile>=2 |  | 7,261 | 4,137 | 3,252 | 10,268 | -556 | 621 | 9,272 | 1,760 | 3,103 | -237 | 1.7 |
| fs ; P=50 ; asia&er20_5m>=0.4&voltercile>=2 |  | 3,537 | 1,581 | 786 | 5,254 | -1,084 | 3,425 | 7,396 | 673 | 1,282 | -461 | 0.6 |
| fs ; P=25 ; stoppedSession=asia |  | 5,968 | 12,763 | 10,180 | 38,350 | -2,225 | 3,692 | 19,370 | 5,431 | 3,712 | -947 | 5.2 |
| fs ; P=100 ; stoppedSession=asia | Y | 11,052 | 12,510 | 9,815 | 36,179 | 1,397 | 2,962 | 37,125 | 5,323 | 957 | 595 | 5.1 |
**S73** (delta stack $/wk at research lots, basis N, vs the same S73 base; MDE = 2.8 SE of the L6M weekly delta; live A = research/2.35, live B = example stack lots; fires/wk = rule events per week)

| cell | carried(PRE&X>=0) | L3M | L6M | HOLD | 2026 | PRE | X' | MDE L6M | live A L6M | live B L6M | live A PRE | fires/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| fs ; P=50 ; others<=2 |  | 10,824 | -241 | 507 | 35,245 | 1,561 | -1,816 | 18,412 | -103 | -118 | 664 | 8.2 |
| fs ; P=50 ; others<=3 |  | 14,648 | 6,485 | 6,007 | 40,289 | -1,430 | 4,015 | 20,914 | 2,760 | 2,658 | -609 | 11.6 |
| fs ; P=50 ; oppBooks>=1 | Y | 3,261 | 4,793 | 4,594 | 13,442 | 2,792 | 4,182 | 15,583 | 2,039 | -177 | 1,188 | 3.3 |
| fs ; P=50 ; asia&er20_5m>=0.4 | Y | 1,765 | 1,904 | 691 | 7,684 | 3,338 | 2,998 | 10,214 | 810 | 460 | 1,421 | 1.3 |
| fs ; P=50 ; asia&voltercile>=2 | Y | 5,535 | 6,801 | 6,461 | 28,725 | 4,548 | 4,742 | 19,750 | 2,894 | 4,811 | 1,935 | 2.4 |
| fs ; P=50 ; er20_5m>=0.4&voltercile>=2 |  | 857 | -745 | -126 | 6,884 | 664 | -614 | 9,526 | -317 | 338 | 282 | 1.7 |
| fs ; P=50 ; asia&er20_5m>=0.4&voltercile>=2 | Y | 2,948 | -233 | -215 | 6,947 | 769 | 3,395 | 7,031 | -99 | 255 | 327 | 0.6 |
| fs ; P=25 ; stoppedSession=asia |  | 5,070 | 8,812 | 7,584 | 32,243 | -1,216 | 2,586 | 18,295 | 3,750 | 4,132 | -517 | 5.2 |
| fs ; P=100 ; stoppedSession=asia | Y | 14,936 | 11,799 | 9,860 | 48,215 | 5,345 | 2,217 | 34,495 | 5,021 | 2,116 | 2,274 | 5.1 |

#### E4 L2/TH-cut proxy (adverse pts)

**MKT** (delta stack $/wk at research lots, basis N, vs the same MKT base; MDE = 2.8 SE of the L6M weekly delta; live A = research/2.35, live B = example stack lots; fires/wk = rule events per week)

| cell | carried(PRE&X>=0) | L3M | L6M | HOLD | 2026 | PRE | X' | MDE L6M | live A L6M | live B L6M | live A PRE | fires/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| adverse20pts ; trigger book only (L2/TH-cut proxy control) |  | 37,874 | 2,464 | 2,430 | 66,729 | -16,182 | -12,651 | 37,426 | 1,048 | -1,772 | -6,886 | 36.8 |
| adverse20pts ; then cut rest P=50 (L2/TH-cut counts as a stop, proxy) |  | -4,320 | -27,753 | -18,618 | 54,040 | -14,523 | -17,810 | 43,769 | -11,810 | -14,555 | -6,180 | 15.6 |
| adverse30pts ; trigger book only (L2/TH-cut proxy control) |  | 23,651 | -3,945 | -5,105 | 63,088 | -15,059 | 765 | 31,546 | -1,679 | -3,863 | -6,408 | 30.6 |
| adverse30pts ; then cut rest P=50 (L2/TH-cut counts as a stop, proxy) |  | 29,472 | 376 | 155 | 93,675 | -19,182 | -196 | 48,690 | 160 | -3,778 | -8,162 | 16.8 |
| adverse40pts ; trigger book only (L2/TH-cut proxy control) |  | 787 | -2,803 | -2,873 | 33,604 | -13,805 | -5,771 | 25,672 | -1,193 | -2,222 | -5,874 | 26.2 |
| adverse40pts ; then cut rest P=50 (L2/TH-cut counts as a stop, proxy) |  | 15,259 | -4,708 | -2,950 | 75,775 | -21,221 | -2,118 | 42,006 | -2,003 | -5,535 | -9,030 | 16.5 |
**S73** (delta stack $/wk at research lots, basis N, vs the same S73 base; MDE = 2.8 SE of the L6M weekly delta; live A = research/2.35, live B = example stack lots; fires/wk = rule events per week)

| cell | carried(PRE&X>=0) | L3M | L6M | HOLD | 2026 | PRE | X' | MDE L6M | live A L6M | live B L6M | live A PRE | fires/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| adverse20pts ; trigger book only (L2/TH-cut proxy control) |  | 5,870 | -13,905 | -13,370 | 31,051 | -16,329 | -15,109 | 38,814 | -5,917 | -8,397 | -6,949 | 36.3 |
| adverse20pts ; then cut rest P=50 (L2/TH-cut counts as a stop, proxy) |  | -28,571 | -28,870 | -22,695 | 1,387 | -23,763 | -19,012 | 48,905 | -12,285 | -15,730 | -10,112 | 16.1 |
| adverse30pts ; trigger book only (L2/TH-cut proxy control) |  | 6,655 | -9,268 | -10,075 | 37,760 | -7,419 | -4,742 | 30,407 | -3,944 | -8,193 | -3,157 | 30.1 |
| adverse30pts ; then cut rest P=50 (L2/TH-cut counts as a stop, proxy) |  | 14,752 | -9,022 | -8,885 | 79,963 | -15,388 | -4,646 | 53,436 | -3,839 | -6,944 | -6,548 | 17.0 |
| adverse40pts ; trigger book only (L2/TH-cut proxy control) |  | -14,211 | -12,178 | -13,182 | 13,659 | -10,236 | -6,669 | 22,798 | -5,182 | -5,939 | -4,356 | 25.6 |
| adverse40pts ; then cut rest P=50 (L2/TH-cut counts as a stop, proxy) |  | -7,267 | -16,951 | -14,872 | 48,748 | -12,229 | -3,816 | 40,010 | -7,213 | -6,711 | -5,204 | 16.1 |

#### C first-target mirror

**MKT** (delta stack $/wk at research lots, basis N, vs the same MKT base; MDE = 2.8 SE of the L6M weekly delta; live A = research/2.35, live B = example stack lots; fires/wk = rule events per week)

| cell | carried(PRE&X>=0) | L3M | L6M | HOLD | 2026 | PRE | X' | MDE L6M | live A L6M | live B L6M | live A PRE | fires/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ft ; stackBE ; others>=1 |  | 20,681 | 362 | 756 | 55,379 | -26,345 | -7,026 | 42,323 | 154 | 1,570 | -11,211 | 14.5 |
| ft ; MAE+10 ; others>=1 |  | 14,286 | 9,161 | 8,863 | 44,461 | -15,051 | -5,335 | 34,442 | 3,898 | 4,359 | -6,405 | 13.9 |
| ft ; rowBE ; others>=1 |  | 16,473 | -4,058 | -2,490 | 50,838 | -25,620 | -5,860 | 41,294 | -1,727 | -2,515 | -10,902 | 14.5 |
| ft ; stackBE ; others>=2 |  | 17,390 | 2,089 | 1,083 | 57,421 | -21,966 | -9,391 | 40,265 | 889 | 1,901 | -9,347 | 9.2 |
| ft ; MAE+10 ; others>=2 |  | 4,992 | 7,447 | 6,396 | 40,417 | -13,810 | -4,915 | 31,996 | 3,169 | 2,706 | -5,876 | 9.0 |
| ft ; rowBE ; others>=2 |  | 12,772 | -3,168 | -2,896 | 56,368 | -20,265 | -7,868 | 40,610 | -1,348 | -2,116 | -8,623 | 9.2 |
**S73** (delta stack $/wk at research lots, basis N, vs the same S73 base; MDE = 2.8 SE of the L6M weekly delta; live A = research/2.35, live B = example stack lots; fires/wk = rule events per week)

| cell | carried(PRE&X>=0) | L3M | L6M | HOLD | 2026 | PRE | X' | MDE L6M | live A L6M | live B L6M | live A PRE | fires/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ft ; stackBE ; others>=1 |  | 227 | -5,282 | -7,454 | 28,131 | -25,396 | -9,481 | 33,013 | -2,248 | -830 | -10,807 | 14.7 |
| ft ; MAE+10 ; others>=1 |  | 4,806 | 3,203 | 2,000 | 27,296 | -18,817 | -8,649 | 23,503 | 1,363 | 2,609 | -8,007 | 14.3 |
| ft ; rowBE ; others>=1 |  | 2,055 | -10,770 | -10,768 | 27,206 | -24,722 | -10,195 | 33,374 | -4,583 | -5,772 | -10,520 | 14.7 |
| ft ; stackBE ; others>=2 |  | 1,063 | -2,889 | -5,188 | 19,870 | -21,424 | -10,110 | 35,052 | -1,229 | 212 | -9,116 | 9.3 |
| ft ; MAE+10 ; others>=2 |  | 784 | 1,541 | 972 | 26,642 | -16,892 | -7,391 | 21,093 | 656 | 851 | -7,188 | 9.2 |
| ft ; rowBE ; others>=2 |  | -1,512 | -11,057 | -10,847 | 16,243 | -19,271 | -11,484 | 35,191 | -4,705 | -5,762 | -8,200 | 9.3 |

#### B same-side cap (mapping A: research lots = live x 2.35)

**MKT** (delta stack $/wk at research lots, basis N, vs the same MKT base; MDE = 2.8 SE of the L6M weekly delta; live A = research/2.35, live B = example stack lots; fires/wk = rule events per week)

| cell | carried(PRE&X>=0) | L3M | L6M | HOLD | 2026 | PRE | X' | MDE L6M | live A L6M | live B L6M | live A PRE | fires/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| cap ; live=6 ; x2.35 ; mode=room ; session=all ; count=openAll |  | -1,315 | -23,399 | -18,525 | 23,305 | -22,080 | -5,182 | 59,408 | -9,957 | -12,545 | -9,396 | 0.0 |
| cap ; live=6 ; x2.35 ; mode=room ; session=pre ; count=openAll |  | 4,060 | 2,501 | 3,624 | -6,748 | -217 | 3,458 | 14,050 | 1,064 | 1,285 | -92 | 0.0 |
| cap ; live=6 ; x2.35 ; mode=skip ; session=all ; count=openAll |  | 28,537 | -15,646 | -9,636 | 84,513 | -27,730 | -12,758 | 75,501 | -6,658 | -9,758 | -11,800 | 0.0 |
| cap ; live=6 ; x2.35 ; mode=skip ; session=pre ; count=openAll |  | 10,395 | 5,067 | 6,416 | 1,239 | -2,047 | 2,753 | 15,781 | 2,156 | 3,116 | -871 | 0.0 |
| cap ; live=8 ; x2.35 ; mode=room ; session=all ; count=openAll |  | -23,329 | -23,674 | -20,892 | 8,782 | -22,532 | -6,106 | 47,727 | -10,074 | -14,600 | -9,588 | 0.0 |
| cap ; live=8 ; x2.35 ; mode=room ; session=pre ; count=openAll | Y | 3,067 | 981 | 1,358 | -3,929 | 330 | 3,087 | 11,165 | 417 | 866 | 140 | 0.0 |
| cap ; live=8 ; x2.35 ; mode=skip ; session=all ; count=openAll |  | 4,162 | -20,322 | -16,565 | 33,829 | -28,739 | -4,181 | 57,313 | -8,648 | -11,584 | -12,229 | 0.0 |
| cap ; live=8 ; x2.35 ; mode=skip ; session=pre ; count=openAll | Y | 4,521 | 2,563 | 3,862 | -2,433 | 1,559 | 3,111 | 13,335 | 1,091 | 1,169 | 663 | 0.0 |
| cap ; live=10 ; x2.35 ; mode=room ; session=all ; count=openAll |  | -4,447 | -2,198 | -2,298 | 16,978 | -19,779 | -2,620 | 39,173 | -935 | -6,089 | -8,416 | 0.0 |
| cap ; live=10 ; x2.35 ; mode=room ; session=pre ; count=openAll | Y | 4,282 | 1,961 | 1,950 | -1,513 | 967 | 1,398 | 9,832 | 835 | 1,212 | 411 | 0.0 |
| cap ; live=10 ; x2.35 ; mode=skip ; session=all ; count=openAll |  | -17,831 | -16,322 | -14,979 | 12,941 | -17,624 | -7,975 | 40,821 | -6,945 | -12,684 | -7,500 | 0.0 |
| cap ; live=10 ; x2.35 ; mode=skip ; session=pre ; count=openAll | Y | 5,531 | 2,789 | 2,940 | -639 | 1,493 | 1,180 | 10,605 | 1,187 | 1,480 | 635 | 0.0 |
| cap ; live=12 ; x2.35 ; mode=room ; session=all ; count=openAll |  | -11,316 | -7,085 | -7,627 | 7,665 | -14,802 | -5,891 | 30,086 | -3,015 | -6,817 | -6,299 | 0.0 |
| cap ; live=12 ; x2.35 ; mode=room ; session=pre ; count=openAll |  | 163 | 77 | 88 | -685 | -914 | 690 | 5,501 | 33 | -12 | -389 | 0.0 |
| cap ; live=12 ; x2.35 ; mode=skip ; session=all ; count=openAll |  | 5,156 | -3,235 | -3,480 | 27,172 | -12,547 | -4,942 | 30,065 | -1,376 | -3,956 | -5,339 | 0.0 |
| cap ; live=12 ; x2.35 ; mode=skip ; session=pre ; count=openAll |  | 780 | 597 | 501 | 133 | -182 | -763 | 5,868 | 254 | 84 | -77 | 0.0 |
**S73** (delta stack $/wk at research lots, basis N, vs the same S73 base; MDE = 2.8 SE of the L6M weekly delta; live A = research/2.35, live B = example stack lots; fires/wk = rule events per week)

| cell | carried(PRE&X>=0) | L3M | L6M | HOLD | 2026 | PRE | X' | MDE L6M | live A L6M | live B L6M | live A PRE | fires/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| cap ; live=6 ; x2.35 ; mode=room ; session=all ; count=openAll |  | -18,197 | -28,918 | -26,864 | 15,443 | -23,917 | -6,447 | 49,899 | -12,306 | -17,978 | -10,178 | 0.0 |
| cap ; live=6 ; x2.35 ; mode=room ; session=all ; count=70only |  | -39,797 | -32,945 | -31,881 | -2,036 | -23,588 | -6,581 | 43,330 | -14,019 | -18,105 | -10,038 | 0.0 |
| cap ; live=6 ; x2.35 ; mode=room ; session=all ; count=both100 |  | -25,866 | -36,985 | -33,516 | 16,499 | -23,285 | -7,775 | 56,687 | -15,738 | -18,557 | -9,909 | 0.0 |
| cap ; live=6 ; x2.35 ; mode=room ; session=pre ; count=openAll |  | -3,033 | 755 | 1,520 | -7,349 | 2,970 | -226 | 14,635 | 321 | -95 | 1,264 | 0.0 |
| cap ; live=6 ; x2.35 ; mode=room ; session=pre ; count=70only | Y | 574 | 391 | 493 | -7,066 | 2,543 | 1,097 | 11,155 | 167 | -125 | 1,082 | 0.0 |
| cap ; live=6 ; x2.35 ; mode=room ; session=pre ; count=both100 |  | -1,705 | 1,377 | 2,332 | -4,203 | 3,852 | -139 | 15,885 | 586 | 708 | 1,639 | 0.0 |
| cap ; live=6 ; x2.35 ; mode=skip ; session=all ; count=openAll |  | -30,862 | -42,164 | -35,698 | 11,297 | -28,502 | -6,690 | 61,674 | -17,942 | -18,489 | -12,128 | 0.0 |
| cap ; live=6 ; x2.35 ; mode=skip ; session=all ; count=70only |  | -27,989 | -43,330 | -38,293 | 11,172 | -29,595 | -12,867 | 55,195 | -18,438 | -22,554 | -12,594 | 0.0 |
| cap ; live=6 ; x2.35 ; mode=skip ; session=all ; count=both100 |  | 15,677 | -22,826 | -20,291 | 73,385 | -25,596 | -15,945 | 68,018 | -9,713 | -11,060 | -10,892 | 0.0 |
| cap ; live=6 ; x2.35 ; mode=skip ; session=pre ; count=openAll |  | 711 | 2,954 | 4,404 | -8,538 | 3,069 | -694 | 16,960 | 1,257 | 1,180 | 1,306 | 0.0 |
| cap ; live=6 ; x2.35 ; mode=skip ; session=pre ; count=70only | Y | 931 | 1,286 | 2,318 | -6,470 | 4,276 | 1,146 | 12,922 | 547 | 476 | 1,820 | 0.0 |
| cap ; live=6 ; x2.35 ; mode=skip ; session=pre ; count=both100 |  | 4,416 | 4,800 | 5,949 | 981 | 1,781 | -1,206 | 17,443 | 2,043 | 2,549 | 758 | 0.0 |
| cap ; live=8 ; x2.35 ; mode=room ; session=all ; count=openAll |  | -25,383 | -18,571 | -16,617 | -8,420 | -14,644 | -6,269 | 39,209 | -7,903 | -13,552 | -6,232 | 0.0 |
| cap ; live=8 ; x2.35 ; mode=room ; session=all ; count=70only |  | -32,023 | -16,835 | -16,587 | -1,160 | -11,673 | -3,045 | 33,046 | -7,164 | -10,189 | -4,967 | 0.0 |
| cap ; live=8 ; x2.35 ; mode=room ; session=all ; count=both100 |  | -34,072 | -30,773 | -29,713 | 1,556 | -22,956 | -10,586 | 44,307 | -13,095 | -17,367 | -9,768 | 0.0 |
| cap ; live=8 ; x2.35 ; mode=room ; session=pre ; count=openAll | Y | 1,445 | 2,541 | 2,094 | -7,290 | 1,781 | 1,125 | 11,533 | 1,081 | 775 | 758 | 0.0 |
| cap ; live=8 ; x2.35 ; mode=room ; session=pre ; count=70only | Y | 113 | 1,193 | 1,139 | -3,984 | 2,007 | 992 | 7,473 | 508 | -396 | 854 | 0.0 |
| cap ; live=8 ; x2.35 ; mode=room ; session=pre ; count=both100 | Y | -415 | -474 | -182 | -7,957 | 2,181 | 796 | 11,939 | -202 | -329 | 928 | 0.0 |
| cap ; live=8 ; x2.35 ; mode=skip ; session=all ; count=openAll |  | -33,894 | -30,578 | -29,150 | -5,135 | -27,217 | -11,933 | 43,267 | -13,012 | -18,558 | -11,582 | 0.0 |
| cap ; live=8 ; x2.35 ; mode=skip ; session=all ; count=70only |  | -30,145 | -22,389 | -21,468 | -23,719 | -17,888 | 1,441 | 38,843 | -9,527 | -10,377 | -7,612 | 0.0 |
| cap ; live=8 ; x2.35 ; mode=skip ; session=all ; count=both100 |  | -23,960 | -44,546 | -39,853 | -11,203 | -26,799 | -10,784 | 53,126 | -18,956 | -21,723 | -11,404 | 0.0 |
| cap ; live=8 ; x2.35 ; mode=skip ; session=pre ; count=openAll | Y | 1,314 | 2,465 | 2,735 | -6,470 | 2,985 | 1,101 | 12,325 | 1,049 | 758 | 1,270 | 0.0 |
| cap ; live=8 ; x2.35 ; mode=skip ; session=pre ; count=70only | Y | 1,075 | 1,184 | 1,540 | -2,946 | 3,771 | 549 | 8,450 | 504 | -58 | 1,605 | 0.0 |
| cap ; live=8 ; x2.35 ; mode=skip ; session=pre ; count=both100 | Y | 2,080 | 3,496 | 4,265 | -4,775 | 3,771 | 326 | 13,330 | 1,488 | 1,082 | 1,605 | 0.0 |
| cap ; live=10 ; x2.35 ; mode=room ; session=all ; count=openAll |  | -23,520 | -14,929 | -17,104 | 3,472 | -13,349 | -5,137 | 34,043 | -6,353 | -10,665 | -5,680 | 0.0 |
| cap ; live=10 ; x2.35 ; mode=room ; session=all ; count=70only |  | -11,188 | -9,331 | -9,281 | 9,591 | -3,794 | -4,004 | 17,809 | -3,971 | -6,132 | -1,614 | 0.0 |
| cap ; live=10 ; x2.35 ; mode=room ; session=all ; count=both100 |  | -32,394 | -18,914 | -17,591 | -7,815 | -15,194 | -2,464 | 35,431 | -8,048 | -12,028 | -6,465 | 0.0 |
| cap ; live=10 ; x2.35 ; mode=room ; session=pre ; count=openAll | Y | 619 | 1,977 | 1,829 | -3,705 | 2,724 | 646 | 7,888 | 841 | 8 | 1,159 | 0.0 |
| cap ; live=10 ; x2.35 ; mode=room ; session=pre ; count=70only | Y | -972 | -1,001 | -909 | -137 | 241 | 1,372 | 2,632 | -426 | -661 | 102 | 0.0 |
| cap ; live=10 ; x2.35 ; mode=room ; session=pre ; count=both100 | Y | 1,151 | 1,787 | 1,816 | -4,656 | 2,930 | 1,211 | 9,144 | 760 | 240 | 1,247 | 0.0 |
| cap ; live=10 ; x2.35 ; mode=skip ; session=all ; count=openAll |  | -24,797 | -18,555 | -20,728 | -19,500 | -10,682 | -3,974 | 33,952 | -7,896 | -10,147 | -4,545 | 0.0 |
| cap ; live=10 ; x2.35 ; mode=skip ; session=all ; count=70only |  | -12,761 | -10,766 | -11,144 | 7,505 | -5,266 | -8,246 | 23,803 | -4,581 | -6,894 | -2,241 | 0.0 |
| cap ; live=10 ; x2.35 ; mode=skip ; session=all ; count=both100 |  | -30,436 | -24,844 | -22,887 | -13,726 | -17,193 | -9,875 | 39,776 | -10,572 | -15,309 | -7,316 | 0.0 |
| cap ; live=10 ; x2.35 ; mode=skip ; session=pre ; count=openAll |  | 1,899 | 1,961 | 1,837 | -4,122 | 3,699 | -657 | 9,624 | 834 | 412 | 1,574 | 0.0 |
| cap ; live=10 ; x2.35 ; mode=skip ; session=pre ; count=70only | Y | -749 | -478 | -323 | -383 | 982 | 1,553 | 5,244 | -204 | -654 | 418 | 0.0 |
| cap ; live=10 ; x2.35 ; mode=skip ; session=pre ; count=both100 |  | 3,289 | 2,340 | 2,538 | -3,756 | 2,949 | -1,375 | 10,891 | 996 | 810 | 1,255 | 0.0 |
| cap ; live=12 ; x2.35 ; mode=room ; session=all ; count=openAll |  | -17,565 | -11,848 | -12,960 | -4,529 | -9,304 | -6,471 | 24,147 | -5,042 | -7,823 | -3,959 | 0.0 |
| cap ; live=12 ; x2.35 ; mode=room ; session=all ; count=70only |  | -672 | -1,247 | -917 | 1,297 | -1,214 | -2,143 | 5,189 | -531 | -961 | -516 | 0.0 |
| cap ; live=12 ; x2.35 ; mode=room ; session=all ; count=both100 |  | -25,219 | -15,387 | -16,186 | -765 | -8,343 | -4,991 | 27,285 | -6,548 | -9,974 | -3,550 | 0.0 |
| cap ; live=12 ; x2.35 ; mode=room ; session=pre ; count=openAll | Y | -1,168 | -354 | -238 | -439 | 598 | 801 | 5,010 | -151 | -558 | 254 | 0.0 |
| cap ; live=12 ; x2.35 ; mode=room ; session=pre ; count=70only |  | -0 | -0 | -0 | -0 | -230 | -148 | 0 | -0 | 0 | -98 | 0.0 |
| cap ; live=12 ; x2.35 ; mode=room ; session=pre ; count=both100 | Y | -669 | 341 | 312 | -663 | 791 | 1,006 | 5,484 | 145 | -370 | 337 | 0.0 |
| cap ; live=12 ; x2.35 ; mode=skip ; session=all ; count=openAll |  | -9,395 | -2,243 | -5,845 | 523 | -9,916 | -6,020 | 29,519 | -954 | -3,526 | -4,220 | 0.0 |
| cap ; live=12 ; x2.35 ; mode=skip ; session=all ; count=70only |  | -1,113 | -1,636 | -957 | 3,351 | -362 | -2,221 | 7,455 | -696 | -1,251 | -154 | 0.0 |
| cap ; live=12 ; x2.35 ; mode=skip ; session=all ; count=both100 |  | -2,506 | -5,657 | -7,848 | 9,520 | -11,138 | -6,485 | 27,299 | -2,407 | -3,975 | -4,740 | 0.0 |
| cap ; live=12 ; x2.35 ; mode=skip ; session=pre ; count=openAll | Y | -176 | -57 | -84 | -109 | 1,976 | 860 | 5,453 | -24 | -388 | 841 | 0.0 |
| cap ; live=12 ; x2.35 ; mode=skip ; session=pre ; count=70only |  | -0 | -0 | -0 | -0 | 16 | -47 | 0 | -0 | 0 | 7 | 0.0 |
| cap ; live=12 ; x2.35 ; mode=skip ; session=pre ; count=both100 |  | -19 | 693 | 572 | 257 | 2,097 | -415 | 5,720 | 295 | -84 | 892 | 0.0 |


## 4. (d) Which sub-rule carries the PRE loss: event decomposition of the P50 cut (pre-lock same-trade $ per week; the final lock-engine effect adds the re-entry in/out terms: PRE total -8.2k = pre-lock -5.4k + lock feedback -2.8k)

The diagnosis used PRE and X' only; recent windows are shown beside as the view. MKT:

| split by | level | events PRE | events X' | pre-lock $/wk PRE | pre-lock $/wk X' | pre-lock $/wk L3M | L6M | HOLD |
|---|---|---|---|---|---|---|---|---|
| session | asia | 408 | 162 | 734 | -1,086 | 7,826 | 3,533 | 4,519 |
| session | london | 306 | 102 | -2,424 | 4,071 | 1,146 | -4,784 | -4,298 |
| session | nyam | 236 | 165 | -3,456 | -3,938 | 1,990 | 0 | -805 |
| session | nypm | 105 | 83 | -676 | -577 | 48 | -721 | -1,516 |
| session | pre | 79 | 45 | 318 | 236 | 1,766 | 2,010 | 2,514 |
| session | close | 3 | nan | 127 | nan | nan | nan | nan |
| book | HM | 167 | 54 | -1,071 | 191 | 4,397 | 1,819 | 1,693 |
| book | KB | 103 | 61 | 232 | 947 | 995 | 2,131 | 601 |
| book | PE | 103 | 38 | -1,027 | 60 | -1,410 | 749 | 1,166 |
| book | SM | 81 | 37 | -778 | -989 | 2,082 | -827 | -201 |
| book | ST | 99 | 51 | 387 | -739 | 1,765 | 543 | 634 |
| book | WT | 584 | 316 | -3,120 | -763 | 4,948 | -4,379 | -3,478 |
| nb | 1 | 391 | 133 | -210 | -21 | 700 | 434 | 284 |
| nb | 2 | 281 | 146 | 427 | -470 | 6,392 | 2,436 | 3,712 |
| nb | 3 | 244 | 150 | -510 | 4,701 | 7,081 | 2,278 | 946 |
| nb | 4 | 221 | 128 | -5,083 | -5,503 | -1,398 | -5,112 | -4,527 |
| opp | 0 | 898 | 397 | -5,072 | -6,022 | 8,605 | -3,527 | -3,188 |
| opp | 1 | 115 | 63 | 518 | 2,547 | 1,702 | 3,060 | 3,381 |
| opp | 2 | 124 | 97 | -823 | 2,181 | 2,469 | 503 | 221 |
| er | .2-.3 | 216 | 97 | -3,918 | 200 | 1,873 | 849 | 519 |
| er | .3-.4 | 220 | 118 | -1,814 | -808 | -410 | -3,730 | -2,409 |
| er | <.2 | 383 | 184 | 489 | -401 | 4,432 | 448 | 61 |
| er | >.4 | 318 | 158 | -133 | -285 | 6,881 | 2,470 | 2,243 |
| vol | 0 | 370 | 186 | -1,559 | -3,069 | 5,045 | -1,879 | -2,613 |
| vol | 1 | 316 | 131 | -1,120 | -352 | 4,864 | 900 | 1,518 |
| vol | 2 | 451 | 240 | -2,699 | 2,128 | 2,867 | 1,016 | 1,509 |
| sincestopped | 1-2h | 189 | 129 | 1,152 | -200 | 6,988 | -2,494 | -2,306 |
| sincestopped | 10-30m | 361 | 111 | -2,628 | -2,641 | -1,392 | 1,942 | 2,567 |
| sincestopped | 2-4h | 90 | 106 | 459 | -1,466 | 172 | -468 | -70 |
| sincestopped | 30-60m | 305 | 120 | -3,939 | 2,919 | 3,467 | 1,288 | 0 |
| sincestopped | <10m | 174 | 42 | -320 | 414 | 3,541 | -231 | 171 |
| sincestopped | >4h | 18 | 49 | -101 | -319 | 0 | 0 | 51 |
| sincefirst | 1-2h | 275 | 102 | -888 | -2,003 | 8,126 | 4,287 | 3,840 |
| sincefirst | 15-30m | 134 | 31 | -1,050 | -284 | 965 | 1,065 | 1,486 |
| sincefirst | 2-4h | 235 | 168 | -706 | 2,139 | 1,194 | -6,714 | -6,191 |
| sincefirst | 30-60m | 248 | 74 | -890 | -356 | 1,156 | 2,834 | 2,054 |
| sincefirst | 5-15m | 92 | 9 | -62 | 397 | 428 | -583 | -355 |
| sincefirst | <5m | 28 | 4 | -636 | 266 | -145 | -623 | -545 |
| sincefirst | >4h | 125 | 169 | -1,146 | -1,453 | 1,051 | -230 | 126 |
| stackppl | -20..-5 | 91 | 56 | -50 | -380 | 2,391 | -3,490 | -2,647 |
| stackppl | -40..-20 | 475 | 217 | -4,734 | 48 | 5,478 | 2,289 | 1,094 |
| stackppl | <-40 | 559 | 280 | -329 | -1,050 | 4,907 | 539 | 2,212 |
| stackppl | -5..5 | 9 | 4 | -53 | 88 | nan | 699 | -152 |
| stackppl | 5..20 | 3 | nan | -212 | nan | nan | nan | -94 |

S73:

| split by | level | events PRE | events X' | pre-lock $/wk PRE | pre-lock $/wk X' | pre-lock $/wk L3M | L6M | HOLD |
|---|---|---|---|---|---|---|---|---|
| session | asia | 403 | 163 | 1,022 | -1,070 | 7,885 | 3,307 | 3,682 |
| session | london | 309 | 100 | -3,363 | 4,071 | -690 | -6,644 | -6,001 |
| session | nyam | 243 | 169 | -2,907 | -3,232 | 596 | -491 | -1,539 |
| session | nypm | 104 | 79 | -99 | -955 | -327 | -555 | -1,506 |
| session | pre | 74 | 45 | 414 | 690 | 2,434 | 2,540 | 2,953 |
| session | close | 2 | nan | 77 | nan | nan | nan | nan |
| book | HM | 175 | 53 | -576 | -89 | 4,626 | 1,943 | 1,793 |
| book | KB | 107 | 61 | 77 | 552 | -444 | 1,469 | -182 |
| book | PE | 104 | 40 | -837 | 313 | -2,268 | 153 | 462 |
| book | SM | 79 | 38 | -738 | -1,085 | 2,391 | -514 | 67 |
| book | ST | 102 | 49 | -443 | -587 | 2,504 | 1,069 | 970 |
| book | WT | 568 | 315 | -2,339 | 401 | 3,089 | -5,962 | -5,520 |
| nb | 1 | 397 | 141 | -58 | -558 | 1,156 | 1,159 | 921 |
| nb | 2 | 284 | 146 | 359 | -601 | 3,950 | -346 | 683 |
| nb | 3 | 241 | 153 | -1,578 | 5,232 | 7,914 | 2,410 | 347 |
| nb | 4 | 213 | 116 | -3,579 | -4,567 | -3,122 | -5,066 | -4,364 |
| opp | 0 | 892 | 394 | -4,960 | -4,712 | 6,193 | -5,079 | -5,251 |
| opp | 1 | 121 | 68 | 653 | 2,560 | 1,201 | 2,734 | 3,041 |
| opp | 2 | 122 | 94 | -548 | 1,657 | 2,504 | 502 | -201 |
| er | .2-.3 | 212 | 97 | -3,260 | 593 | 352 | 366 | -102 |
| er | .3-.4 | 226 | 115 | -1,365 | -548 | 90 | -4,104 | -2,948 |
| er | <.2 | 380 | 186 | 541 | -566 | 3,429 | 364 | -598 |
| er | >.4 | 317 | 158 | -771 | 26 | 6,027 | 1,531 | 1,237 |
| vol | 0 | 375 | 187 | -1,249 | -3,762 | 3,533 | -2,811 | -3,834 |
| vol | 1 | 322 | 130 | -890 | 357 | 4,180 | 817 | 1,372 |
| vol | 2 | 438 | 239 | -2,717 | 2,910 | 2,185 | 152 | 51 |
| sincestopped | 1-2h | 189 | 129 | 651 | 1,136 | 6,403 | -2,978 | -2,740 |
| sincestopped | 10-30m | 357 | 112 | -4,592 | -2,844 | -2,603 | 913 | 1,516 |
| sincestopped | 2-4h | 89 | 105 | 490 | -1,535 | 299 | -457 | -94 |
| sincestopped | 30-60m | 311 | 121 | -2,776 | 2,567 | 3,225 | 811 | -1,142 |
| sincestopped | <10m | 171 | 41 | 1,495 | 595 | 2,574 | -132 | 37 |
| sincestopped | >4h | 18 | 48 | -124 | -413 | 0 | 0 | 12 |
| sincefirst | 1-2h | 278 | 105 | 263 | -1,869 | 6,351 | 3,430 | 3,096 |
| sincefirst | 15-30m | 133 | 36 | -1,392 | -331 | -119 | 904 | 1,093 |
| sincefirst | 2-4h | 231 | 163 | -1,386 | 2,401 | 1,189 | -6,254 | -6,617 |
| sincefirst | 30-60m | 254 | 76 | -1,769 | -328 | 2,061 | 2,260 | 1,580 |
| sincefirst | 5-15m | 92 | 9 | 769 | 532 | -616 | -1,617 | -1,374 |
| sincefirst | <5m | 25 | 3 | -51 | 146 | 693 | -95 | -83 |
| sincefirst | >4h | 122 | 164 | -1,290 | -1,048 | 340 | -471 | -108 |
| stackppl | -20..-5 | 92 | 55 | 769 | 1,281 | 1,349 | -4,848 | -3,697 |
| stackppl | -40..-20 | 523 | 233 | -4,218 | -428 | 3,822 | 1,912 | -492 |
| stackppl | <-40 | 508 | 263 | -765 | -971 | 4,727 | 531 | 2,118 |
| stackppl | -5..5 | 9 | 5 | -438 | -377 | nan | 563 | -246 |
| stackppl | 5..20 | 3 | nan | -203 | nan | nan | nan | -94 |

Reading: the loss concentrates where a cut is least intuitive - in big stacks and when every open book is on the same side. Where the stack is mixed (a book open on the other side) the cut is positive in PRE and X' (+0.5k | +2.5k pre-lock for one opposite book). Those two conditions came from this decomposition (stage 2, registered before any recent read), the session / ER / vol conditions from the prereg.

**Placebos (200 draws each, random 50% cuts at the same fire rate and time-since-first-entry, drawn inside the same first-entry-session stratum; rank = share of draws below the real delta):**

* MKT pooled P50: pending; S73 pooled: pending
* MKT Asia-stopped P50: pending; S73: pending; MKT P100 Asia: pending; S73 P100 Asia: pending
* MKT vol tercile 2: pending; MKT Asia & vol 2: pending; S73 Asia & vol 2: pending
* MKT <= 2 other books: pending; MKT ER >= 0.4: pending; S73 Asia & ER >= 0.4: pending
* MKT opposite book >= 1: pending; S73: pending
* Pre-session caps (random skips in the same session at the same affected rate): MKT cap 8 skip pending; MKT cap 10 pending; S73 cap 8 skip pending; S73 cap 8 both-legs pending; S73 cap 6 70% only pending

The placebo draws keep the rate and the timing and drop the information (which book stopped, whether the stop was an Asia stop); a rank near 1.0 means the timing of the real stop carries information; a rank near 0.5 (as the pooled cell in PRE) means the cut is no better than a random cut. Regime split: the vol-tercile and ER rows are the regime variants (table in section 3); session: Asia positive, London / NY-AM negative in PRE.

**Walk-forward re-selection chain (forward-facing answer; closed days only; each quarter from 2024-04 the best of the 'fs' variants by trailing-52-week delta is applied for the next quarter, none if no variant is positive):**

| base   | win                        |   chain_usd_wk |   pooled_P50_usd_wk |   weeks |
|:-------|:---------------------------|---------------:|--------------------:|--------:|
| MKT    | chain_all                  |           5116 |                 110 |      97 |
| MKT    | PRE_part(2024-04..2025-06) |           2151 |               -9318 |      65 |
| MKT    | HOLD                       |          11194 |               19440 |      32 |
| MKT    | L6M                        |          13831 |               23651 |      27 |
| MKT    | L3M                        |          14359 |               37345 |      13 |
| S73    | chain_all                  |           1709 |               -3689 |      97 |
| S73    | PRE_part(2024-04..2025-06) |           4288 |               -7754 |      65 |
| S73    | HOLD                       |          -3578 |                4644 |      32 |
| S73    | L6M                        |          -3637 |                6812 |      27 |
| S73    | L3M                        |          -1713 |               16717 |      13 |

The chain does not reliably beat the pooled rule recently (it lags it in L6M on both bases and loses -3.6k in S73 HOLD / L6M); it beats it in the PRE part (+2.2k vs -9.3k MKT, +4.3k vs -7.8k S73). The last re-fit (as of 2026-02-06) picks "other books <= 3" for MKT and "a book open on the other side" for S73: the chain's choice is not stable across bases, which is the honest summary of how little the conditions are identified. Detail: out/stack2/wf_*.pkl.

## 5. (b) Same-side cap at 6 / 8 / 10 / 12 live lots, with the split (cap on the 70% leg only / on both)

Cap arithmetic: mapping A = research lots x 2.35 (6/8/10/12 live lots = 14.1 / 18.8 / 23.5 / 28.2 research lots on the six books' 45.2 research lots), mapping B = the cap in the user's example book lots (PE 5, KB 3, SM 3, HM 1, ST and WT at research/2.35). Count rules on the 70/30 base: 'openAll' = open lots incl. filled adds (SP-1), '70only' = only the 70% legs counted, 'both100' = 100% of each planned row reserved at entry (the add is then covered by the cap). On the market base the three coincide.

All-session caps (best of room / skip per cell, mapping B shown; mapping A is in the tables of section 3 group B and is also negative in PRE and X' in all 32 cells):

| base | count rule | live cap (example-stack lots) | best of room/skip L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| MKT | openAll | 6 | -22,836 | -15,322 | -30,837 | -6,113 |
| MKT | openAll | 8 | -19,746 | -15,267 | -25,235 | -797 |
| MKT | openAll | 10 | -16,077 | -12,674 | -17,042 | -2,839 |
| MKT | openAll | 12 | -3,030 | -466 | -10,618 | -2,078 |
| S73 | 70only | 6 | -25,455 | -21,959 | -24,156 | -82 |
| S73 | 70only | 8 | -19,059 | -15,525 | -13,502 | -4,120 |
| S73 | 70only | 10 | -6,563 | -5,021 | -5,840 | 561 |
| S73 | 70only | 12 | -204 | -176 | -205 | -3,378 |
| S73 | both100 | 6 | -40,605 | -33,289 | -30,685 | -8,701 |
| S73 | both100 | 8 | -36,499 | -30,302 | -27,714 | -4,501 |
| S73 | both100 | 10 | -25,259 | -22,497 | -14,634 | -6,827 |
| S73 | both100 | 12 | -14,451 | -12,213 | -9,304 | -3,890 |
| S73 | openAll | 6 | -30,330 | -24,886 | -30,979 | -8,886 |
| S73 | openAll | 8 | -22,105 | -21,048 | -25,433 | -2,783 |
| S73 | openAll | 10 | -12,007 | -10,604 | -15,167 | -3,575 |
| S73 | openAll | 12 | 877 | -857 | -9,787 | 1,203 |

Pre-session (08:30-09:30 ET) caps, skip mode, mapping B:

| base | mode | count rule | live cap (example-stack lots) | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| MKT | room | openAll | 6 | 1,713 | -1,718 | 438 | -1,028 | 2,791 |
| MKT | room | openAll | 8 | 1,293 | -2,317 | -546 | 518 | 1,625 |
| MKT | room | openAll | 10 | -404 | -1,800 | -615 | 279 | 1,728 |
| MKT | room | openAll | 12 | -154 | -690 | -399 | 28 | 1,388 |
| MKT | skip | openAll | 6 | 4,106 | 1,068 | 3,092 | -3,198 | 2,170 |
| MKT | skip | openAll | 8 | 3,511 | 1,268 | 2,716 | 1,702 | 607 |
| MKT | skip | openAll | 10 | 1,727 | -2,165 | -381 | 712 | 3,182 |
| MKT | skip | openAll | 12 | 229 | -3,377 | -1,447 | -1,036 | 992 |
| S73 | room | 70only | 6 | -2,560 | -2,007 | -858 | 3,458 | 660 |
| S73 | room | 70only | 8 | -3,782 | -2,001 | -1,546 | 1,390 | 1,746 |
| S73 | room | 70only | 10 | -1,132 | 296 | 293 | 490 | 1,476 |
| S73 | room | 70only | 12 | -125 | -63 | -55 | -166 | -624 |
| S73 | room | both100 | 6 | -3,477 | -1,166 | 621 | 3,192 | -545 |
| S73 | room | both100 | 8 | 837 | -374 | 753 | 4,000 | 106 |
| S73 | room | both100 | 10 | -3,347 | -3,243 | -2,207 | 2,417 | 1,415 |
| S73 | room | both100 | 12 | -1,686 | -292 | -209 | 1,763 | 1,519 |
| S73 | room | openAll | 6 | -3,262 | -854 | 568 | 2,784 | -13 |
| S73 | room | openAll | 8 | -3,810 | -667 | 396 | 3,207 | 1,087 |
| S73 | room | openAll | 10 | -2,881 | -634 | 4 | 2,475 | 1,393 |
| S73 | room | openAll | 12 | -1,609 | 26 | 260 | 1,310 | 588 |
| S73 | skip | 70only | 6 | -1,850 | -422 | 454 | 4,151 | -2,196 |
| S73 | skip | 70only | 8 | -2,403 | -2,968 | -1,649 | 1,620 | 490 |
| S73 | skip | 70only | 10 | -466 | -959 | -588 | 1,719 | 852 |
| S73 | skip | 70only | 12 | -342 | -171 | -150 | -48 | 42 |
| S73 | skip | both100 | 6 | -2,021 | 311 | 2,203 | 340 | -406 |
| S73 | skip | both100 | 8 | 383 | 1,611 | 2,602 | 4,933 | -2,155 |
| S73 | skip | both100 | 10 | -560 | -1,214 | 41 | 3,295 | 419 |
| S73 | skip | both100 | 12 | -740 | -1,858 | -528 | 1,516 | 109 |
| S73 | skip | openAll | 6 | -1,784 | 2,047 | 3,723 | 554 | -73 |
| S73 | skip | openAll | 8 | -2,114 | 703 | 1,438 | 4,486 | 178 |
| S73 | skip | openAll | 10 | -3,030 | -34 | 1,074 | 3,200 | 416 |
| S73 | skip | openAll | 12 | -645 | -123 | 164 | 1,911 | -661 |

Reading: the cap protects nothing in the long run - it removes lots at the average edge of the books (SP-1: equal-risk scaling does as well). The pre-session cap is small (+1k..+5k per week), positive in PRE on most cells on both mappings and mixed in recent windows; with the split the 'both100' reservation (cap covers the add) is no better than counting the 70% only. It stays a LEAD for paper only.

## 6. (c) First-target mirror

Rows in the group C tables of section 3. Result: tightening the remaining stops after the first target (stack-average breakeven, each book's own entry, or MAE+10 beyond the stack's worst excursion) loses in PRE (-14k..-26k) and X' (-5k..-12k) on both bases and is not systematically positive recently (stack BE MKT L6M +0.4k; own-entry BE -4.1k; MAE+10 +9.2k; S73 -5.3k / -10.8k / +3.2k). The winners the first target leaves behind reach their own targets more often than the tightened stops give back. DEAD.

## 7. Drift, units and the live-lot mapping

Quarterly delta ($/wk) of the rule vs its base (basis N):

| quarter | MKT2 | MKT32 | MKT174 | MKT48 | S7372 | S73102 | S73189 | S73191 |
|---|---|---|---|---|---|---|---|---|
| 20232 | 17,653 | 15,547 | 14,682 | 1,570 | 19,733 | 14,747 | 14,550 | 6,397 |
| 20233 | 3,456 | -1,743 | 265 | 6,126 | 1,560 | -1,835 | -481 | 1,381 |
| 20234 | -26,353 | -7,222 | -4,359 | -5,527 | -27,766 | -10,708 | -4,834 | 2,526 |
| 20241 | 6,851 | 7,343 | 7,436 | 19,216 | 6,586 | 10,967 | 11,051 | 13,027 |
| 20242 | -4,104 | 1,242 | 11,241 | -5,028 | -7,071 | -11,589 | 3,530 | -3,533 |
| 20243 | -14,452 | 5,780 | 6,142 | 11,403 | 1,796 | 17,299 | 2,905 | 15,550 |
| 20244 | -1,327 | 6,574 | -3,619 | 1,567 | -1,759 | 5,140 | -6,160 | 7,941 |
| 20251 | -15,801 | -7,813 | 3,798 | -2,761 | -23,515 | -4,741 | -1,127 | -4,631 |
| 20252 | -11,050 | -2,190 | 4,413 | -4,709 | -8,703 | 1,409 | 10,858 | 3,200 |
| 20253 | -5,857 | 724 | 3,407 | -757 | -17,904 | -2,264 | -1,230 | 262 |
| 20254 | 21,297 | 22,836 | 4,693 | 7,334 | 6,748 | 10,411 | 6,258 | 2,343 |
| 20261 | 76,740 | 40,185 | 5,878 | 16,229 | 54,620 | 47,588 | 14,936 | 31,917 |

Columns: MKT2 = pooled P50 (MKT), MKT32 = Asia-stopped P50 (MKT), MKT174 = opposite-book P50 (MKT), MKT48 = ER>=0.4 P50 (MKT), S7372 = pooled (S73), S73102 = Asia-stopped (S73), S73189 = opposite-book (S73), S73191 = Asia & vol 2 (S73). Quarter 20261 = 5 weeks.

Per-book delta by book, per RESEARCH lot (= per live lot of that book, since P&L is linear in the book's lots), $/wk, L6M then PRE:

| rule | window | HM | ST | PE | KB | SM | WT |
|---|---|---|---|---|---|---|---|
| MKT pooled cut P50 | L6M | 1,079 | 951 | 545 | -177 | 202 | -137 |
| MKT pooled cut P50 | PRE | 227 | -510 | -421 | -514 | -85 | 39 |
| MKT Asia-stopped cut P50 | L6M | 1,221 | 659 | 475 | -373 | 186 | -94 |
| MKT Asia-stopped cut P50 | PRE | 351 | -40 | -191 | -262 | -11 | 45 |
| MKT opp-book cut P50 | L6M | 484 | 36 | -201 | -12 | 12 | -13 |
| MKT opp-book cut P50 | PRE | 328 | 7 | 163 | 95 | -40 | -14 |
| MKT pre-session cap 8 (skip) | L6M | -40 | 188 | -52 | 121 | 86 | 15 |
| MKT pre-session cap 8 (skip) | PRE | 139 | 60 | 21 | 58 | -53 | -66 |
| S73 Asia-stopped cut P50 | L6M | 638 | 545 | 856 | -519 | -9 | -96 |
| S73 Asia-stopped cut P50 | PRE | 425 | -55 | -288 | 24 | -22 | -6 |
| S73 opp-book cut P50 | L6M | 498 | 155 | -181 | -152 | 17 | -8 |
| S73 opp-book cut P50 | PRE | 355 | -228 | 142 | 268 | -72 | -19 |
| S73 pre-session cap 8 (skip, 100% reserved) | L6M | 12 | 318 | -187 | 182 | 131 | -98 |
| S73 pre-session cap 8 (skip, 100% reserved) | PRE | 173 | 166 | -27 | 297 | -102 | -36 |

Live-lot mapping: **A** (uniform: live = research / 2.35, i.e. ST 4.3, HM 4.3, WT 3.0, KB 2.2, SM 3.1, PE 2.4 lots) and **B** (the user's example stack, short 12 lots: P6 5 = PE, K6 3 = KB, M6 3 = SM (my reading of "M6"), H6 1 = HM; ST and WT unspecified, set to research/2.35). The first-stop gain sits mostly in HM (+1.2k per HM lot per week L6M for the Asia-stopped MKT cut), ST and PE; KB is negative. With HM at 1 lot (B) the Asia-stopped MKT rule is +5.6k per week L6M (A: +8.6k) and -1.5k in PRE (A: +0.4k). If the live lots are very different the per-book table above gives the number directly. The mapping question stays open for the user.

## 8. Basis and execution sensitivity (candidate rows; N primary)

M (measured fills with target correction) and LIVE-CAL beside N are in `out/stack2/cand_table.csv` (columns M_*, LIVE_*); latency 1 s / 3 s and +1 pt exit cost are in the header row (latency) and cand_table (xc1_*, breakeven). The Asia-stopped cut survives a 3-second decision delay (L6M MKT +19.8k vs +20.2k) and its breakeven extra exit cost is 7.8 pts per lot (MKT, L6M); the pooled cut's is 3.7 pts. Entry-day vol tercile is a research-library tag (not a live feature); ER20(5m) at the stopped signal needs D6 to store the 5-min ER at each book's entry.

## 9. THP stack section (for merge; no edit of THP_POLICY.txt)

Written to `out/stack2/THP_POLICY_stack2_section.txt` and copied here:

```
# === stack === (STACK-2 = PLAN36 section 4, 2026-10-31; for the lead to merge into THP_POLICY.txt; NOTHING here is PASS. Replaces / extends the SP-1 stack section.)
# FORMAT (stack <cond> <action> [param]; conditions are ANDed): D6 computes the stack state from the other books' positions. Features in the SP-1 section: same_side_lots, books_same (OTHER books still open on the stopped book's side), books_opp (books open on the other side), stack_ppl, stack_R, stack_mfe_ppl, first_stop (1 in the second a same-side book is stopped out, first of its episode: reset when the side goes flat).
# NEW features STACK-2 needs: stopped_session = session tag of the STOPPED book's ENTRY (asia 18:00-02:00 ET, london 02:00-08:30, pre 08:30-09:30, nyam 09:30-12:00, nypm 12:00-15:00, close 15:00-15:15); er20_5m_entry = Kaufman ER(20) on 5-min bars at the stopped book's entry bar (stored at entry; same feature as the TG-1 trend row); vol_tercile_day = research tag of the entry day (NOT a live feature; see NEEDS line).
# CUT MECHANICS in the research: market exit of pct% of every other open book on the same side at the close of the next second (+0.995 pt +0.242 fee per lot); not re-entered in the trade. Research lots ST10 HM10 WT7 KB5.2 SM7.4 PE5.6; live lots per book are an OPEN QUESTION (see DS3_STACK_2.md section 7: the gain sits in HM, ST and PE; KB is negative).
# WHY NOT THE POOLED RULE: 'first_stop=1 books_same>=1 cut pct=50' (SP-1) is +23.0k/wk L6M MKT but PRE -8.2k (S73 -6.5k): the PRE loss is cuts with >=4 other books open and cuts with no book open on the other side (pre-lock -5.1k each in PRE, -5.5k / -6.0k in X'), NY-AM and WT stops. Its recent gain is 76% lock-engine re-entries.
# [STACK first_stop cut, stopped book entered in Asia] tier=CANDIDATE-RECENT (selected on PRE+X' among 202 cells on a post-hoc premise; fails Romano-Wolf (p 0.97) and DSR; inside L6M MDE)
# stack effect on N, $/wk at research lots, L3M | L6M | HOLD | PRE | X': MKT +17.5k | +20.2k | +16.5k | +0.9k | +3.7k (MDE L6M 26.3k, 5.2 events/wk); S73 +11.9k | +13.2k | +11.4k | +2.0k | +2.8k (MDE 23.1k). M and LIVE-CAL >= 0 in all windows (LIVE PRE MKT -0.04k). 92% of the L6M gain falls since 2025-10-01. Live $ per week L6M: mapping A (research/2.35) MKT +8.6k, S73 +5.6k; mapping B (P6 5, K6 3, M6 3, H6 1) MKT +5.6k, S73 +5.4k. Placebo and CI in DS3_STACK_2.md.
#! stack first_stop=1 stopped_session=asia books_same>=1 cut pct=50 books=others_same_side
#! stack first_stop=1 stopped_session=asia books_same>=1 cut pct=100 books=others_same_side   # P100 variant: MKT +12.5k L6M PRE +1.4k X' +3.0k; S73 +11.8k PRE +5.3k X' +2.2k
# [STACK first_stop cut, a book open on the other side] tier=LEAD (>= 0 in PRE, X', HOLD, L6M on both bases; L3M MKT -2.8k)
# stack effect on N, $/wk: MKT L3M -2.8k L6M +4.0k HOLD +4.3k PRE +4.4k X' +4.4k (MDE 13.1k; 3.2 events/wk); S73 +3.3k +4.8k +4.6k +2.8k +4.2k (MDE 15.6k). Live A L6M MKT +1.7k.
#! stack first_stop=1 books_opp>=1 books_same>=1 cut pct=50 books=others_same_side
# [STACK first_stop cut, trending at the stopped signal] tier=LEAD (MKT: >= 0 in PRE, X', HOLD, L6M, L3M; S73 PRE +3.6k X' +0.9k L6M +0.9k)
# stack effect on N, $/wk: MKT +8.0k | +7.4k | +5.5k | +2.7k | +1.9k (MDE 11.4k; 3.7 events/wk).
#! stack first_stop=1 er20_5m_entry>=0.4 books_same>=1 cut pct=50 books=others_same_side
# NEEDS: stack first_stop=1 stopped_session=asia vol_tercile_day>=2 books_same>=1 cut pct=50 books=others_same_side   # vol_tercile_day is a research tag (entry-day volatility rank), not a D6 feature; MKT +9.8k | +12.4k | +10.2k | +3.6k | +6.1k, 11 of 12 quarters positive, 2.4 events/wk
# [STACK pre-session cap] tier=LEAD (SP-1 line retained; mapping dependent: positive PRE and X' in 19 of 32 pre-session cells on the x2.35 mapping, unstable under the example-stack lots beyond 8 lots; $1-5k/wk)
#! stack session=pre same_side_lots>=8.1 skip_entry   # 8.1 live lots == 19 research lots on the x2.35 mapping; MKT N +4.5k L3M +2.6k L6M +3.9k HOLD +1.6k PRE +3.1k X'(skip, 8 lots)
# NOT listed (tested in STACK-2, dead or negative in PRE): the pooled first_stop cut at pct 25/50/75/100 (PRE -7.4k..-11.6k MKT); cut both sides; block re-entry for the hour / 30 min (recent +27.7k..+32.4k L6M MKT but PRE -16.8k / -12.5k); window 5-60 min since the stopped entry; all-session same-side caps at 6/8/10/12 live lots (0 of 32 cells >= 0 in PRE and X'); first-target mirror to breakeven / MAE+10 (PRE -14k..-26k); early L2/TH-cut proxy at -20/-30/-40 pts (PRE -12k..-24k).

```

## 10. Module API (for SP2: compose the first-stop rule with the split and the ER sizer for the Sunday stack line)

```python
import sys; sys.path.insert(0,'l2vast/ds3/code/stack2')
import s2_lib as T
T.setup()                                  # once per process; ~2 GB, 2 s. Set OMP/MKL threads=1 before importing numpy (the module does).
Rv = T.rule(event='stop', action='cut', P=0.5, sess_mask=1)   # Asia-stopped first-stop 50% cut (sess_mask bit i = SESSN[i]: asia,london,pre,nyam,nypm,close)
res = T.run('S73', 'N', Rv, m0=sizer)      # base: 'MKT' | 'S73' (the 70/30 PRE-selected split) | 'S:<name>' registered with T.use_split(name, o_N, o_M); basis 'N' | 'M' | 'LIVE'
res['daily'], res['base_daily']            # (6, ND) $ per day per book (order T.BOOKS = ST HM WT KB SM PE, research lots 10/10/7/5.2/7.4/5.6); base_daily includes m0
T.win(res['daily'].sum(0), 'L6M'); T.delta(res, 'L6M')    # window stats (windows Y26 L3M L6M HOLD PRE X WF) and (mean delta $/wk, MDE) vs the same base incl. the sizer
res['events']                              # ledger DataFrame: one row per rule event (book, session, ER/vol cond, nb, lots open, stack ppl, ok flag, pre-lock delta dpre)
T.rule(...)                                # rule parameters: event 'stop'|'target'|'adverse'; action 'cut'|'stackBE'|'mae'|'rowBE'; P; stopdef; min_others; max_others; min_opp; window_min/window_ref; block (-1 hour, >0 s);
                                           # scope; sess_mask; c1/c1thr and c2/c2thr conditions on per-row arrays set by T.setcond(c1, c2) (e.g. T.er_cond(base,basis) for ER20 5m); rearm; lat; xc;
                                           # cap_lots (research lots) / cap_skip / cap_count (0 open lots, 1 70% leg only, 2 100% reserved) / cap_sess  -> the cap runs in the SAME pass as any event rule
```

Composition rules: (1) `m0` is a per-row size multiplier aligned with `T.S.rows(base,basis)['tid']` (build it from tid, e.g. an ER sizer from `T.er_cond`); it is applied before the rule, so the rule sees sized lots and its base_daily is the sized stack; (2) the split is the base: pass `'S73'`, or register another split's `o` array from `lj_core.run_variant` with `T.use_split`; (3) a run takes 3-4 s (event rules with `action='mae'` or `event='adverse'` step every second: 15-45 s); (4) the 3-pass lock-engine feedback is inside `T.run` (res['toggles'] = row toggles per pass); (5) `s2_compose_demo.py` is the worked example and gives the numbers in section 1.8:

| S73 base + ER sizer (x0.5 below 0.3, x1.5 at/above 0.4), plus rule | delta L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| sizer + first-stop P50 asia | 3,713 | 1,318 | 980 | -1,633 | 834 |
| sizer + first-stop P50 asia + pre cap 8 live (x2.35) | 4,170 | 4,017 | 3,906 | -192 | 512 |
| sizer + first-stop P50 oppBooks>=1 | -707 | 1,371 | 32 | 484 | 1,400 |
| sizer only | 0 | 0 | 0 | 0 | 0 |

## 11. Disclosures and limits

* The pooled first-stop premise is post-hoc (SP-1 looked at L6M / HOLD / L3M before it was named a candidate). The stage-2 conditions came from the PRE and X' decomposition (stated, registered before the single recent look). The recent windows were read once for all 202 cells; the later QUANT columns (placebos, M / LIVE, latency, walk-forward, quarterly drift) are evaluations of already-carried cells, not new selections. Selection used PRE and X' only (carry = delta >= 0 in both, per base).
* The libraries contain taken signals only: a cut frees lots that cannot re-enter on an in-trade signal; what the lock engine does after a cut (admitting / blocking later library signals) is the 're-entry' column, and it is the main source of the recent gain. A live system would see the signals that arrived while a book was inside its trade; this program cannot credit the cut with them.
* Stops = rows whose remainder exit is the original stop (exit_type 0). A live L2 / TH cut is not in the libraries (section 1.7). The 'adverse' proxy is a research stand-in, not the live L2 rule.
* ER20(5m) is the 5-minute Kaufman ER at the stopped book's signal (trend store); entry-day vol tercile is the library's vol_tag_entry_day.
* Capacity (top-5 depth at the cut seconds) not measured. Cuts are market exits at the close of the next second +0.995 pt +0.242 fee per lot.
* MDE = 2.8 x SE of the weekly delta over the window. RC / Romano-Wolf / PBO use PRE and X' weeks (4-week blocks, 2,000 draws), DSR trials = 202 (and the UF_TRIALS cumulative count 2.47 million in the cum column of cand_table.csv: with 2.47M cumulative trials no row has a DSR above 0).
* Workers: at most 3 at any time; threads = 1; per-process RSS < 6 GB.
