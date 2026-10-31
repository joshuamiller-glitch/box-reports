# DS3_L2_UF_LOSS_C8 - L2-UNTIL-FOUND cycle 8, LOSS side: stop placement at structure lines behind the entry vs the fixed stop, risk-matched lots (agent UF-LOSS, 2026-10-31)
Research only. UNTOUCHED never read. Own masks: Y26 = 20260101..0206 (~5 wk), L3M = 20251106.., L6M = 20250801.., HOLD = 20250701.., PRE = 20240201..20250630, X' = 20230401..20240131. Prereg `l2vast/ds3/prereg/UF_LOSS_C8_prereg.md` sha256 1c8409f0ba12f649a7671ceb3325424e6cc0ffbeda27ee20b680568b68c406cd; selection `out/uf/loss8/selection_PRE_X.json` sha256 cba557eafe0207e28142d0cdf3c31f4f2080fb2611c29adc74326f19b083129c (PRE+X' only, basis N; EMPTY carried list). dead_lookup over the 18 specs: 0 hits. Cumulative N = UF_TRIALS total + 18; n_effective 4.3.
## Page 1 - the answer (a null, stated first)
1. **The resting-book version cannot be tested on mbp-10** (10 levels = ~2.5 pts; wall_stop finite in 0.05% of in-trade seconds; a wall 20-80 pts behind the entry is invisible) and the traded-volume node (vp_max_behind40) is not available at the signal second in the cached tables. It is added to the raw-MBO pull list (full-depth resting size at price levels 20-80 pts behind the entry at the signal second).
2. What was tested is price structure: the nearest fresh ZONES-2 SET11 line behind the entry within [dmin, 60] pts + a 2 or 5 pt buffer as the stop (40% of signals have such a line; median changed stop distance 35-42 pts vs the fixed 60 on 60/60 books), target unchanged, MKT base, exact per-book lock engine, risk-matched lots (m = min(3, fixed/d)) or unit lots. The 1-s re-scan reproduces the library exits for 100.0% of rows and the base lock-engine daily series to 7e-12 $.
3. **Nothing is selectable on PRE+X'**: 0 of 8 structural cells has a stack delta >= 0 in both PRE and X' (PRE -18,817..-9,188 $/wk, X' -8,852..+5,732; MDE 20-44k). All 10 fixed-distance references (30..80 pts, STRUCTURE) are also negative in PRE. RC / Romano-Wolf over the 18 on PRE+X' days: p 0.99, studentised 0.99, survivors 0, PBO 0.42, best-cell DSR 0.02. The recent windows below are a labelled VIEW of an empty selection.
4. Recent view (L6M / HOLD, basis N, lock-engine stack): see tables; the permuted-distance placebo (same distance distribution, wrong trades; 100 draws) is the real test and is shown beside. A tighter structural stop with more lots is STRUCTURE unless that placebo is beaten in PRE, X', L6M and HOLD.
**LOSS side closed for stop placement: DEAD (no cell selectable on PRE+X'; resting-wall version needs raw MBO).**
## 1. Structural cells, basis N (stack d $/wk at research lots, MDE in brackets; live lots L6M; per contract = same trades, no lock effects; per planned lot = per contract x m)
| cell | Y26 d$/wk (MDE) | L3M d$/wk (MDE) | L6M d$/wk (MDE) | HOLD d$/wk (MDE) | PRE d$/wk (MDE) | X d$/wk (MDE) | L6M live lots | L6M per contract (MDE) | L6M per planned lot |
|---|---|---|---|---|---|---|---|---|---|
| 11set_behind|dmin=15|buf=2|lots=matched | -29,563 (+128,912) | +10,121 (+72,954) | -9,082 (+49,293) | -8,796 (+43,295) | -18,817 (+32,353) | -7,007 (+43,694) | -1,352 | -0.39 (+1.40) | +0.08 |
| 11set_behind|dmin=15|buf=2|lots=unit | +26,332 (+96,304) | +14,516 (+49,278) | +1,584 (+38,214) | +968 (+34,403) | -16,886 (+24,200) | -7,180 (+28,841) | +1,239 | -0.39 (+1.40) | -0.39 |
| 11set_behind|dmin=15|buf=5|lots=matched | -28,523 (+125,906) | +1,149 (+64,211) | -17,252 (+53,455) | -16,788 (+47,591) | -15,052 (+28,677) | -8,852 (+36,108) | -3,461 | -0.56 (+1.37) | -0.25 |
| 11set_behind|dmin=15|buf=5|lots=unit | +23,113 (+98,417) | +13,966 (+50,431) | +3,020 (+40,928) | +1,000 (+36,358) | -16,906 (+24,087) | -7,133 (+26,047) | +4,164 | -0.56 (+1.37) | -0.56 |
| 11set_behind|dmin=25|buf=2|lots=matched | -26,470 (+113,420) | +11,285 (+63,907) | -7,013 (+48,691) | -3,384 (+43,073) | -9,188 (+26,690) | +3,368 (+32,218) | +4,598 | -0.29 (+1.23) | +0.05 |
| 11set_behind|dmin=25|buf=2|lots=unit | +55,438 (+112,526) | +20,368 (+57,304) | +6,949 (+41,208) | +5,253 (+36,390) | -12,490 (+20,441) | +5,732 (+22,651) | +4,717 | -0.29 (+1.23) | -0.29 |
| 11set_behind|dmin=25|buf=5|lots=matched | -23,247 (+89,545) | +9,347 (+51,873) | -13,467 (+47,110) | -10,734 (+41,927) | -11,142 (+24,509) | -1,350 (+26,108) | +3,812 | -0.34 (+1.19) | -0.12 |
| 11set_behind|dmin=25|buf=5|lots=unit | +41,916 (+108,886) | +20,948 (+52,565) | +8,530 (+40,860) | +5,880 (+35,952) | -11,556 (+20,480) | +4,624 (+20,337) | +7,973 | -0.34 (+1.19) | -0.34 |
## 2. Fixed-distance references (STRUCTURE; same lots rule), basis N
| cell | Y26 d$/wk (MDE) | L3M d$/wk (MDE) | L6M d$/wk (MDE) | HOLD d$/wk (MDE) | PRE d$/wk (MDE) | X d$/wk (MDE) | L6M live lots | L6M per contract (MDE) | L6M per planned lot |
|---|---|---|---|---|---|---|---|---|---|
| fixed|d=30|lots=matched | -5,288 (+98,522) | +6,132 (+85,545) | -34,001 (+70,803) | -22,123 (+65,331) | -30,885 (+42,052) | +14,327 (+48,278) | -4,281 | -1.94 (+2.65) | -0.77 |
| fixed|d=30|lots=unit | -13,272 (+96,662) | -15,012 (+67,626) | -38,578 (+50,763) | -28,959 (+47,109) | -43,083 (+35,078) | +1,140 (+33,670) | -9,980 | -1.94 (+2.65) | -1.94 |
| fixed|d=40|lots=matched | +14,874 (+86,409) | +8,683 (+62,228) | -35,962 (+60,242) | -29,128 (+54,894) | -9,630 (+33,290) | -7,902 (+34,258) | -8,936 | -1.21 (+1.91) | -0.30 |
| fixed|d=40|lots=unit | +27,677 (+78,390) | +3,072 (+48,391) | -11,709 (+37,795) | -6,341 (+33,487) | -23,352 (+26,060) | -10,549 (+25,037) | -2,726 | -1.21 (+1.91) | -1.21 |
| fixed|d=50|lots=matched | +15,106 (+54,325) | +20,313 (+34,638) | +6,683 (+26,390) | +6,576 (+24,085) | -9,144 (+23,602) | +7,994 (+19,853) | +4,456 | +0.07 (+0.96) | +0.52 |
| fixed|d=50|lots=unit | +36,872 (+55,323) | +17,880 (+36,382) | +13,406 (+30,235) | +13,608 (+27,014) | -14,751 (+20,232) | +2,275 (+16,421) | +5,158 | +0.07 (+0.96) | +0.07 |
| fixed|d=70|lots=matched | -10,999 (+125,128) | -7,616 (+64,707) | -13,476 (+37,439) | -8,447 (+35,349) | -15,919 (+21,362) | -17,120 (+25,371) | -8,911 | -0.29 (+1.30) | -0.84 |
| fixed|d=70|lots=unit | -20,770 (+99,936) | -16,971 (+54,799) | -9,367 (+31,282) | -6,270 (+29,410) | -18,996 (+22,314) | -13,878 (+25,304) | -2,737 | -0.29 (+1.30) | -0.29 |
| fixed|d=80|lots=matched | -18,135 (+147,926) | -9,053 (+73,348) | -25,042 (+48,996) | -16,847 (+47,235) | -22,427 (+28,720) | -23,088 (+34,743) | -7,276 | -0.00 (+1.87) | -0.91 |
| fixed|d=80|lots=unit | -6,818 (+148,003) | -14,057 (+74,687) | -10,638 (+46,833) | -6,027 (+44,036) | -19,849 (+28,472) | -23,487 (+34,856) | +3,019 | -0.00 (+1.87) | -0.00 |
## 3. Stop-cost bases: N 1.01 vs NATIVE 1.28 vs LIVE join 2.45 (stack d $/wk research lots)
| structural cell | N L6M / HOLD / PRE / X' | NATIVE 1.28 L6M / HOLD / PRE / X' | LIVE join 2.45 L6M / HOLD / PRE / X' |
|---|---|---|---|
| dmin=15|buf=2|lots=matched | -9,082 / -8,796 / -18,817 / -7,007 | -13,231 / -14,246 / -20,065 / -7,684 | -14,265 / -15,562 / -24,499 / -15,701 |
| dmin=15|buf=2|lots=unit | +1,584 / +968 / -16,886 / -7,180 | +1,306 / +785 / -17,379 / -7,355 | -800 / -2,175 / -18,021 / -11,246 |
| dmin=15|buf=5|lots=matched | -17,252 / -16,788 / -15,052 / -8,852 | -17,872 / -17,507 / -14,904 / -9,616 | -18,452 / -18,953 / -16,710 / -15,526 |
| dmin=15|buf=5|lots=unit | +3,020 / +1,000 / -16,906 / -7,133 | +1,711 / +1,124 / -15,690 / -7,239 | -3,833 / -4,230 / -17,997 / -10,904 |
| dmin=25|buf=2|lots=matched | -7,013 / -3,384 / -9,188 / +3,368 | -8,479 / -4,782 / -10,564 / +3,102 | -10,571 / -7,138 / -12,014 / -1,874 |
| dmin=25|buf=2|lots=unit | +6,949 / +5,253 / -12,490 / +5,732 | +6,161 / +4,270 / -12,760 / +5,491 | +5,481 / +2,673 / -13,106 / +3,585 |
| dmin=25|buf=5|lots=matched | -13,467 / -10,734 / -11,142 / -1,350 | -14,341 / -11,610 / -11,086 / -1,480 | -16,117 / -13,875 / -12,146 / -4,444 |
| dmin=25|buf=5|lots=unit | +8,530 / +5,880 / -11,556 / +4,624 | +6,754 / +5,724 / -10,618 / +4,241 | +3,422 / +2,694 / -13,081 / +1,882 |
A tighter stop is hit more often, so the stop cost bites: the structural cells lose $1-7k more per week at 2.45 than at 1.01 in L6M (e.g. dmin=25 buf=5 unit +8.5k -> +3.4k; dmin=15 buf=2 matched -9.1k -> -14.3k); native 1.28 sits in between.
## 4. Re-entry decomposition (basis N, stack $/wk): same trades / re-entry in / re-entry out
| structural cell | window | same trades | re-entry in | re-entry out | total d$/wk |
|---|---|---|---|---|---|
| dmin=25|buf=2|lots=matched | L6M | -1,515 | -6,002 | +504 | -7,013 |
| dmin=25|buf=2|lots=matched | HOLD | -3,160 | -4,607 | +4,383 | -3,384 |
| dmin=25|buf=2|lots=matched | PRE | -1,987 | +5,776 | -12,976 | -9,188 |
| dmin=25|buf=2|lots=matched | X | +8,282 | +262 | -5,176 | +3,368 |
| dmin=25|buf=2|lots=unit | L6M | -7,850 | +16,907 | -2,108 | +6,949 |
| dmin=25|buf=2|lots=unit | HOLD | -6,068 | +12,341 | -1,021 | +5,253 |
| dmin=25|buf=2|lots=unit | PRE | -6,100 | -5,165 | -1,226 | -12,490 |
| dmin=25|buf=2|lots=unit | X | +5,638 | +1,807 | -1,714 | +5,732 |
| dmin=15|buf=2|lots=matched | L6M | +3,725 | -9,040 | -3,767 | -9,082 |
| dmin=15|buf=2|lots=matched | HOLD | +342 | -8,131 | -1,007 | -8,796 |
| dmin=15|buf=2|lots=matched | PRE | -7,322 | +5,615 | -17,109 | -18,817 |
| dmin=15|buf=2|lots=matched | X | -7,141 | +2,057 | -1,924 | -7,007 |
## 5. Permuted-distance placebo (100 draws, same book and month)
| structural cell | real d$/wk PRE / X' / HOLD / L6M | permuted-distance mean (100 draws) | rank PRE / X' / HOLD / L6M |
|---|---|---|---|
| dmin=15|buf=2|lots=matched | -18,817 / -7,007 / -8,796 / -9,082 | -12,587 / -3,748 / -12,167 / -15,130 | 0.15 / 0.27 / 0.66 / 0.74 |
| dmin=15|buf=2|lots=unit | -16,886 / -7,180 / +968 / +1,584 | -11,798 / -4,762 / +70 / -2,594 | 0.11 / 0.29 / 0.52 / 0.75 |
| dmin=15|buf=5|lots=matched | -15,052 / -8,852 / -16,788 / -17,252 | -10,476 / -1,768 / -8,438 / -11,705 | 0.19 / 0.13 / 0.21 / 0.28 |
| dmin=15|buf=5|lots=unit | -16,906 / -7,133 / +1,000 / +3,020 | -9,477 / -3,809 / +1,253 / -1,085 | 0.02 / 0.24 / 0.47 / 0.72 |
| dmin=25|buf=2|lots=matched | -9,188 / +3,368 / -3,384 / -7,013 | -9,063 / -31 / -3,709 / -6,153 | 0.47 / 0.72 / 0.52 / 0.43 |
| dmin=25|buf=2|lots=unit | -12,490 / +5,732 / +5,253 / +6,949 | -9,015 / -1,875 / +2,844 / +1,328 | 0.22 / 0.96 / 0.59 / 0.82 |
| dmin=25|buf=5|lots=matched | -11,142 / -1,350 / -10,734 / -13,467 | -7,438 / -807 / -2,459 / -4,853 | 0.23 / 0.47 / 0.14 / 0.13 |
| dmin=25|buf=5|lots=unit | -11,556 / +4,624 / +5,880 / +8,530 | -7,338 / -1,943 / +3,249 / +2,006 | 0.15 / 0.94 / 0.68 / 0.88 |
Rank >= 0.9 is reached only by the dmin=25 unit-lot cells in X' (0.96 / 0.94); PRE ranks are 0.15-0.47, HOLD 0.14-0.68, L6M 0.13-0.88: no cell beats the permuted-distance placebo in PRE, X', HOLD and L6M together, so the line distance carries no information beyond the change of distance itself (STRUCTURE).
## 6. Learned / next
1. Stop placement at structure lines behind the entry is STRUCTURE with a negative sign on the selection windows; no cell is selectable. The resting-wall question stays open only for raw MBO.
2. Closing line for the LOSS side: with cycles 1-8 (book triggers, tape/footprint, scale-out, regime walk-forward, stall exits, learned trajectory, stopped-book L2 state, stop placement) the only loss-side signal with a recent sign is the stack-level first-stop cut and its ES-book condition (LEAD, re-entry-dominated, SHADOW).
Files: code/uf8/{cells8,engine8,stageB8,val8}.py; out/uf/loss8/{stageA8.pkl,stageA8_PRE_X.csv,selection_PRE_X.json,stageB8.pkl}; DEAD_CELLS.csv +18 (UFL8).
