FIRST LINE: NY AM MF3 (120/120), NY AM MF7 (120/60), NY AM MF4 (90/30), NY AM MF6 (90/30), London MF3 (120/60) MOSTLY DRIFT with a large stop; alternatives: smaller size until managed, or best replacement book for the slot

# Wide-bracket books: edge beyond drift, and edge per unit of risk (W-SUNDAY-WB)

Order: autopilot/DIRECTIVE_1521Z_Josh-wide-bracket-books-edge-per-t.md (Josh: a 120/120 bracket "monkey" works over time because NQ went up). Research only, nothing live touched.

## Data and method (read first)

- Real trades: the EXACT engine trades of the four live mixes (runs_rf, 42 months 202304..202610 without 202511; 35,236 trades). Net = gross - 4.84 x lots. Week = Monday-anchored session week (ET+7h of the exit date, week 0 = 2023-04-03); 186-week base minus the weeks starting in 202511.
- Brackets per trade come from the live event parquets (stop_pts, tgt_pts, exit_ts matched on book, side, signal second; 100 percent matched). Books with a fixed bracket: as in the order; NY MF1 stop 72-120 and NY MF3 stop 45-120 vary per entry (median 120). Asia and NY PM brackets from the same parquets (AS MF1 40/80, MF2 60/60, MF3 45/45, MF4 30/30; NP MF1 30/30, MF2 120/120, MF3 80/40, MF4 60/60).
- DRAWS ARE A REPLAY NULL, NOT LIVE RESULTS. Replay = NQ 1-s tape (/mnt/l2/l2vast/instr_1s/NQ_S{S,O,H,L,C}.npy, tape ends 2026-10-16 20:59 UTC, so the drift check covers the trades up to then: column n cov), entry at the open of the first 1-s bar at/after the drawn second, stop/target in points from that price, stop first if both are inside one bar, no slippage, time exit at the close of the last bar before the event exit time (same session-window end / UWTime flat), fee 4.84 per lot, same lots as the real trade. 200 draws per book (seed 20261127). Overlapping positions are ALLOWED (no one-position-at-a-time).
- Entry window of the draws: per book, uniform random second between the 0.5th and 99.5th percentile of (event exit time - real entry second) of the book itself, on the same session day as the real trade.
- Two nulls. **Drift null (primary, verdict basis)**: per draw each trade keeps its day, lots and bracket but gets a random entry second AND the side labels of the book are randomly permuted (same count long and short), so the draw knows nothing about the direction of the day: it earns the NQ drift of the window, long gaining and short losing when NQ rises. Excess = real net of that side minus the mean over the 200 draws of the net of the trades assigned that side; share beaten = share of draws below the real result. **Same-day same-side timing null (diagnostic)**: side kept with its day, only the entry second randomized; this null lets a draw enter BEFORE the real signal while already knowing the side, so it is biased in favor of the draws and answers only "is the real entry second better than a random second of that day for that side".
- Real result = exact engine trades (includes live exits: BookLock, DayHalt, and for Asia/NY PM the live PolicyTake/PolicyTrail/EarlyCut). The draws use the bare bracket. Column "entries-only" replays the real entry seconds with the same bare bracket on the same tape, so it removes the exit/engine difference (replay of real entries versus draws, both on the same tape).
- Verdict: EDGE BEYOND DRIFT = real beats >= 90 percent of the drift-null draws on EACH side the book trades; TOO FEW TRADES = < 30 covered trades on a traded side; else MOSTLY DRIFT. NY MF6, MF7, MF9 and London MF2 trade the long side only (no short trades); they are judged on the long side alone.
- "Large stop" = stop >= 90 pts. Variance shares use the weekly net of the book against the weekly net of its own session mix (all books of that live set).

## 1. Edge per trade versus risk per trade (live lots, 42 months)

| book | stop/tgt pts | trades | trades/wk | mean lots | avg net/trade | stop $ (median stop x $20 x mean lots) | avg net / stop $ | total net | weekly-variance share | covariance share | weeks positive of last 26 | share of all weeks positive |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NY AM MF1 | 120/120 (stop 72-120) | 1652 | 9.0 | 4.2 | $712 | $9,994 | 7.1% | $1,176,421 | 26% | 35% | 17 | 55% |
| NY AM MF3 | 120/120 (stop 62-120) | 986 | 5.4 | 3.8 | $501 | $9,186 | 5.5% | $493,804 | 10% | 9% | 15 | 59% |
| NY AM MF7 | 120/60 | 885 | 4.8 | 1.3 | $150 | $3,197 | 4.7% | $132,449 | 1% | 3% | 15 | 58% |
| NY AM MF4 | 90/30 | 3296 | 18.0 | 4.0 | $167 | $7,122 | 2.3% | $549,057 | 12% | 20% | 21 | 55% |
| NY AM MF6 | 90/30 | 2933 | 16.0 | 4.1 | $112 | $7,348 | 1.5% | $327,071 | 9% | 13% | 19 | 55% |
| London MF3 | 120/60 | 1866 | 10.2 | 2.0 | $96 | $4,800 | 2.0% | $179,132 | 9% | 13% | 17 | 56% |
| London MF1 | 90/30 | 1130 | 6.2 | 8.0 | $472 | $14,400 | 3.3% | $532,846 | 46% | 52% | 20 | 58% |
| NY AM MF2 | 60/60 | 1988 | 10.9 | 3.9 | $180 | $4,708 | 3.8% | $357,193 | 9% | 11% | 16 | 54% |
| NY AM MF5 | 60/60 | 2604 | 14.2 | 2.3 | $99 | $2,819 | 3.5% | $258,739 | 4% | 6% | 15 | 59% |
| NY AM MF8 | 80/40 | 927 | 5.1 | 1.1 | $97 | $1,771 | 5.5% | $89,744 | 0% | 1% | 18 | 63% |
| NY AM MF9 | 80/40 | 681 | 3.7 | 2.2 | $167 | $3,592 | 4.7% | $113,815 | 1% | 2% | 17 | 57% |
| London MF2 | 45/45 | 3097 | 16.9 | 4.0 | $65 | $3,600 | 1.8% | $201,642 | 29% | 35% | 17 | 58% |
| Asia MF1 | 40/80 | 1963 | 10.7 | 3.2 | $233 | $2,560 | 9.1% | $457,660 | 39% | 49% | 17 | 57% |
| Asia MF2 | 60/60 | 638 | 3.5 | 3.3 | $383 | $4,001 | 9.6% | $244,228 | 9% | 16% | 22 | 57% |
| Asia MF3 | 45/45 | 2602 | 14.2 | 3.7 | $86 | $3,358 | 2.5% | $222,568 | 19% | 30% | 18 | 58% |
| Asia MF4 | 30/30 | 908 | 5.0 | 3.6 | -$10 | $2,189 | -0.5% | -$9,458 | 3% | 5% | 12 | 50% |
| NY PM MF1 | 30/30 | 3553 | 19.4 | 3.2 | $51 | $1,905 | 2.7% | $180,876 | 17% | 19% | 16 | 54% |
| NY PM MF2 | 120/120 | 587 | 3.2 | 3.7 | $860 | $8,905 | 9.7% | $504,879 | 27% | 27% | 18 | 56% |
| NY PM MF3 | 80/40 | 1138 | 6.2 | 3.4 | $343 | $5,466 | 6.3% | $390,397 | 21% | 16% | 18 | 60% |
| NY PM MF4 | 60/60 | 1802 | 9.8 | 3.4 | $29 | $4,109 | 0.7% | $52,962 | 34% | 38% | 14 | 50% |

Reading: avg net/stop $ is the expected return per trade as a fraction of the dollars put at risk on the stop side. Variance share = var(book weekly net) / var(mix weekly net); covariance share = cov(book, mix) / var(mix) (adds up to 100 percent across the books of a mix).

## 2. Drift check by side (200 random-entry draws, same bracket and time exit; replay null)

Values in dollars summed over the covered trades of that side (n cov), net of fees. "draw" = mean of 200 draws. Beat = share of draws the real result beats.

| book | n cov (long / short) | side | real (exact) | draw mean (drift null) | excess | excess per trade | beat, drift null | entries-only replay vs draws (beat) | same-day same-side timing null: excess, beat |
|---|---|---|---|---|---|---|---|---|---|
| NY AM MF1 | 762 / 862 | long | $621,308 | -$172,793 | $794,101 | $1,042 | 100% | 100% | -$275,153, 4% |
| NY AM MF1 | 762 / 862 | short | $532,601 | $171,745 | $360,856 | $419 | 98% | 96% | -$709,762, 0% |
| NY AM MF3 | 485 / 486 | long | $466,419 | $44,855 | $421,564 | $869 | 100% | 100% | $256,421, 99% |
| NY AM MF3 | 485 / 486 | short | $33,852 | -$73,889 | $107,741 | $222 | 83% | 76% | -$47,662, 30% |
| NY AM MF7 | 873 / 0 | long | $125,566 | $345,787 | -$220,220 | -$252 | 0% | 0% | -$226,465, 0% |
| NY AM MF7 | 873 / 0 | short | no trades | | | | | | |
| NY AM MF4 | 1580 / 1668 | long | $289,152 | -$251,933 | $541,085 | $342 | 100% | 100% | -$5,749, 46% |
| NY AM MF4 | 1580 / 1668 | short | $243,830 | $60,818 | $183,012 | $110 | 87% | 90% | -$338,276, 0% |
| NY AM MF6 | 2882 / 0 | long | $303,435 | $664,442 | -$361,007 | -$125 | 4% | 8% | -$369,898, 2% |
| NY AM MF6 | 2882 / 0 | short | no trades | | | | | | |
| London MF3 | 916 / 912 | long | $145,568 | -$86,894 | $232,462 | $254 | 100% | 100% | $124,736, 99% |
| London MF3 | 916 / 912 | short | $31,192 | -$188 | $31,379 | $34 | 66% | 82% | -$74,144, 9% |
| London MF1 | 589 / 521 | long | $334,154 | -$249,575 | $583,729 | $991 | 100% | 100% | $291,479, 97% |
| London MF1 | 589 / 521 | short | $186,607 | -$15,304 | $201,911 | $388 | 91% | 100% | -$111,285, 18% |
| NY AM MF2 | 988 / 968 | long | $221,293 | -$97,289 | $318,582 | $322 | 100% | 100% | $85,173, 76% |
| NY AM MF2 | 988 / 968 | short | $148,935 | $61,862 | $87,073 | $90 | 76% | 76% | -$173,451, 10% |
| NY AM MF5 | 1647 / 907 | long | $169,609 | $29,678 | $139,931 | $85 | 96% | 95% | -$136,238, 6% |
| NY AM MF5 | 1647 / 907 | short | $93,056 | -$40,091 | $133,147 | $147 | 95% | 93% | -$132,944, 3% |
| NY AM MF8 | 452 / 449 | long | $71,265 | $11,994 | $59,271 | $131 | 100% | 100% | $3,956, 55% |
| NY AM MF8 | 452 / 449 | short | $16,765 | -$17,479 | $34,244 | $76 | 95% | 90% | -$24,267, 10% |
| NY AM MF9 | 674 / 0 | long | $106,652 | $277,199 | -$170,546 | -$253 | 0% | 0% | -$166,454, 0% |
| NY AM MF9 | 674 / 0 | short | no trades | | | | | | |
| London MF2 | 3035 / 0 | long | $199,102 | -$414,700 | $613,802 | $202 | 100% | 100% | $632,348, 100% |
| London MF2 | 3035 / 0 | short | no trades | | | | | | |
| Asia MF1 | 990 / 924 | long | $242,771 | -$12,960 | $255,731 | $258 | 100% | 100% | -$46,108, 28% |
| Asia MF1 | 990 / 924 | short | $187,781 | $135,724 | $52,057 | $56 | 72% | 90% | -$249,415, 0% |
| Asia MF2 | 349 / 277 | long | $135,997 | $274 | $135,724 | $389 | 100% | 100% | -$125,029, 1% |
| Asia MF2 | 349 / 277 | short | $98,057 | -$15,401 | $113,458 | $410 | 99% | 100% | -$151,128, 0% |
| Asia MF3 | 1228 / 1293 | long | $102,701 | -$125,583 | $228,284 | $186 | 100% | 100% | -$347,330, 0% |
| Asia MF3 | 1228 / 1293 | short | $94,322 | $83,148 | $11,175 | $9 | 55% | 100% | -$547,051, 0% |
| Asia MF4 | 419 / 468 | long | -$15,849 | -$37,476 | $21,627 | $52 | 73% | 100% | -$236,805, 0% |
| Asia MF4 | 419 / 468 | short | $13,307 | $24,642 | -$11,335 | -$24 | 38% | 98% | -$274,502, 0% |
| NY PM MF1 | 1659 / 1842 | long | $125,956 | -$87,793 | $213,749 | $129 | 100% | 100% | $470,616, 100% |
| NY PM MF1 | 1659 / 1842 | short | $55,165 | $58,578 | -$3,413 | -$2 | 52% | 62% | $244,203, 100% |
| NY PM MF2 | 291 / 289 | long | $233,509 | -$111,775 | $345,285 | $1,187 | 100% | 100% | $262,826, 100% |
| NY PM MF2 | 291 / 289 | short | $241,469 | $97,408 | $144,060 | $498 | 92% | 92% | $77,496, 80% |
| NY PM MF3 | 570 / 555 | long | $192,561 | -$79,492 | $272,052 | $477 | 100% | 99% | $352,631, 100% |
| NY PM MF3 | 570 / 555 | short | $179,060 | $21,900 | $157,159 | $283 | 98% | 96% | $212,699, 100% |
| NY PM MF4 | 1001 / 773 | long | $74,479 | -$129,058 | $203,537 | $203 | 96% | 100% | $155,494, 96% |
| NY PM MF4 | 1001 / 773 | short | -$49,735 | $70,954 | -$120,689 | -$156 | 7% | 12% | -$175,401, 0% |

## 3. Result in NQ down weeks versus up weeks

Week = session week; NQ weekly return = last close minus first open of the continuous 1-s tape in that week (weekend-to-weekend, so a contract roll over the weekend does not count): 74 down weeks, 107 up weeks in the covered span. $ per week, net; draw = mean of the drift-null draws (random entry, random sides) per week of the same weeks.

| book | real $/wk, NQ down weeks | draws $/wk, down weeks | real $/wk, NQ up weeks | draws $/wk, up weeks | trades down / up |
|---|---|---|---|---|---|
| NY AM MF1 | $7,590 | $746 | $5,535 | -$525 | 724 / 900 |
| NY AM MF3 | $3,320 | -$284 | $2,380 | -$75 | 395 / 576 |
| NY AM MF7 | $153 | $1,508 | $1,068 | $2,189 | 310 / 563 |
| NY AM MF4 | $5,661 | -$1,354 | $1,066 | -$850 | 1402 / 1846 |
| NY AM MF6 | -$2,162 | $1,247 | $4,331 | $5,347 | 1196 / 1686 |
| London MF3 | $844 | -$660 | $1,069 | -$357 | 809 / 1019 |
| London MF1 | $3,541 | -$1,453 | $2,418 | -$1,471 | 485 / 625 |
| NY AM MF2 | $2,300 | -$315 | $1,870 | -$114 | 842 / 1114 |
| NY AM MF5 | $824 | -$925 | $1,885 | $543 | 1116 / 1438 |
| NY AM MF8 | $438 | -$22 | $520 | -$36 | 381 / 520 |
| NY AM MF9 | $95 | $1,154 | $931 | $1,793 | 249 / 425 |
| London MF2 | -$4,292 | -$8,979 | $4,829 | $2,334 | 1368 / 1667 |
| Asia MF1 | $2,495 | $663 | $2,298 | $689 | 825 / 1089 |
| Asia MF2 | $1,317 | -$183 | $1,277 | -$15 | 275 / 351 |
| Asia MF3 | $1,044 | -$18 | $1,119 | -$384 | 1097 / 1424 |
| Asia MF4 | $265 | -$28 | -$207 | -$101 | 424 / 463 |
| NY PM MF1 | $1,550 | $52 | $621 | -$309 | 1546 / 1955 |
| NY PM MF2 | $3,348 | -$261 | $2,123 | $46 | 246 / 334 |
| NY PM MF3 | $2,939 | -$428 | $1,440 | -$242 | 464 / 661 |
| NY PM MF4 | -$596 | -$856 | $644 | $49 | 780 / 994 |

## 4. Verdict per book

| book | stop/tgt | avg net/trade | stop $ | avg / stop $ | long: excess, beat | short: excess, beat | down / up weeks $/wk | verdict |
|---|---|---|---|---|---|---|---|---|
| NY AM MF1 | 120/120 (stop 72-120) | $712 | $9,994 | 7.1% | $794,101, 100% | $360,856, 98% | $7,590 / $5,535 | EDGE BEYOND DRIFT |
| NY AM MF3 | 120/120 (stop 62-120) | $501 | $9,186 | 5.5% | $421,564, 100% | $107,741, 83% | $3,320 / $2,380 | MOSTLY DRIFT (LARGE STOP) |
| NY AM MF7 | 120/60 | $150 | $3,197 | 4.7% | -$220,220, 0% | no trades | $153 / $1,068 | MOSTLY DRIFT (LARGE STOP) |
| NY AM MF4 | 90/30 | $167 | $7,122 | 2.3% | $541,085, 100% | $183,012, 87% | $5,661 / $1,066 | MOSTLY DRIFT (LARGE STOP) |
| NY AM MF6 | 90/30 | $112 | $7,348 | 1.5% | -$361,007, 4% | no trades | -$2,162 / $4,331 | MOSTLY DRIFT (LARGE STOP) |
| London MF3 | 120/60 | $96 | $4,800 | 2.0% | $232,462, 100% | $31,379, 66% | $844 / $1,069 | MOSTLY DRIFT (LARGE STOP) |
| London MF1 | 90/30 | $472 | $14,400 | 3.3% | $583,729, 100% | $201,911, 91% | $3,541 / $2,418 | EDGE BEYOND DRIFT |
| NY AM MF2 | 60/60 | $180 | $4,708 | 3.8% | $318,582, 100% | $87,073, 76% | $2,300 / $1,870 | MOSTLY DRIFT |
| NY AM MF5 | 60/60 | $99 | $2,819 | 3.5% | $139,931, 96% | $133,147, 95% | $824 / $1,885 | EDGE BEYOND DRIFT |
| NY AM MF8 | 80/40 | $97 | $1,771 | 5.5% | $59,271, 100% | $34,244, 95% | $438 / $520 | EDGE BEYOND DRIFT |
| NY AM MF9 | 80/40 | $167 | $3,592 | 4.7% | -$170,546, 0% | no trades | $95 / $931 | MOSTLY DRIFT |
| London MF2 | 45/45 | $65 | $3,600 | 1.8% | $613,802, 100% | no trades | -$4,292 / $4,829 | EDGE BEYOND DRIFT |
| Asia MF1 | 40/80 | $233 | $2,560 | 9.1% | $255,731, 100% | $52,057, 72% | $2,495 / $2,298 | MOSTLY DRIFT |
| Asia MF2 | 60/60 | $383 | $4,001 | 9.6% | $135,724, 100% | $113,458, 99% | $1,317 / $1,277 | EDGE BEYOND DRIFT |
| Asia MF3 | 45/45 | $86 | $3,358 | 2.5% | $228,284, 100% | $11,175, 55% | $1,044 / $1,119 | MOSTLY DRIFT |
| Asia MF4 | 30/30 | -$10 | $2,189 | -0.5% | $21,627, 73% | -$11,335, 38% | $265 / -$207 | MOSTLY DRIFT |
| NY PM MF1 | 30/30 | $51 | $1,905 | 2.7% | $213,749, 100% | -$3,413, 52% | $1,550 / $621 | MOSTLY DRIFT |
| NY PM MF2 | 120/120 | $860 | $8,905 | 9.7% | $345,285, 100% | $144,060, 92% | $3,348 / $2,123 | EDGE BEYOND DRIFT |
| NY PM MF3 | 80/40 | $343 | $5,466 | 6.3% | $272,052, 100% | $157,159, 98% | $2,939 / $1,440 | EDGE BEYOND DRIFT |
| NY PM MF4 | 60/60 | $29 | $4,109 | 0.7% | $203,537, 96% | -$120,689, 7% | -$596 / $644 | MOSTLY DRIFT |

### Notes

- NY AM MF3 (120/120 (stop 62-120)): MOSTLY DRIFT, long beat 100%; short beat 83%; LARGE STOP.
- NY AM MF7 (120/60): MOSTLY DRIFT, long beat 0%; LARGE STOP.
- NY AM MF4 (90/30): MOSTLY DRIFT, long beat 100%; short beat 87%; LARGE STOP.
- NY AM MF6 (90/30): MOSTLY DRIFT, long beat 4%; LARGE STOP.
- London MF3 (120/60): MOSTLY DRIFT, long beat 100%; short beat 66%; LARGE STOP.
- NY AM MF2 (60/60): MOSTLY DRIFT, long beat 100%; short beat 76%.
- NY AM MF9 (80/40): MOSTLY DRIFT, long beat 0%.
- Asia MF1 (40/80): MOSTLY DRIFT, long beat 100%; short beat 72%.
- Asia MF3 (45/45): MOSTLY DRIFT, long beat 100%; short beat 55%.
- Asia MF4 (30/30): MOSTLY DRIFT, long beat 73%; short beat 38%.
- NY PM MF1 (30/30): MOSTLY DRIFT, long beat 100%; short beat 52%.
- NY PM MF4 (60/60): MOSTLY DRIFT, long beat 96%; short beat 7%.
- Same-day same-side timing null (diagnostic): the real entry second is worse than a random second of the same day for the same side in most books (see the last column of section 2), i.e. the books carry day-direction information in the side but the entry timing itself does not add over a random second of the same day. That null is biased toward the draws (draws can enter before the signal), so it is a diagnostic and not the verdict basis.
- Asia and NY PM exact results include live exit management (PolicyTake, PolicyTrail, EarlyCut), the draws and the "entries-only replay" use the bare bracket; compare the real column with the entries-only beat column to see how much of the verdict is the exit side.
- Draw results are a replay null on the 1-s tape (no slippage, stop first in a bar, overlaps allowed): they are not live results and carry no quick-screen gains. Files: outputs/sunday_wb/ (prep.py, wb.py, wbk.py, report.py, mk_md.py, wb_table.csv); compute on server C with 6 threads.

## 5. Same entries with the managed exits

PLACEHOLDER: to be filled by W-SUNDAY (same entries, the managed exits being fitted for Sunday and loop C loss side; edge per unit of risk compared with the bare brackets above).
