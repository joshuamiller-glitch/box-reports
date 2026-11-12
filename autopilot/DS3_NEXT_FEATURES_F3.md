# DS3_NEXT_FEATURES_F3 - T-NEXT-FEATURES items 3 (hold-or-take by location) and 4 (flat cut by context). W-F3. Shadow only, no PASS claim.
Updated 2026-11-12 19:16Z. Directive autopilot/DIRECTIVE_T_NEXT_FEATURES_20261112.md; prereg autopilot/NEXTF3_PREREG.md (sha in DECISIONS.md). BASE = JN05W2 (LPB panel + F3 + E1 + C22 + BR3S + FLAT45K, exact 43 months, W-J). Item-4 sets keep FLAT45K on K7 unless the cell says replace. Exact sets run one per job (jn05_run2.py, TP engine, tag NEXTF); months done: NC_U7_T10_15F 3/43, NC_U7_T20_15F 3/43, NC_U7_T20_15A 3/43, NC_K7_T20_20RC 3/43, NC_K7_F55_45 3/43, NC_A7_T10_10F 3/43, NC_M7_T10_10A 3/43, NC_K7_T30_10RC 0/43, NH_P7_A9_N20 3/43, NH_P7_B9_X10N30 3/43, NH_U7_B7_X20N60 3/43, NH_M7_C9_F2 3/43, NH_M7_B9_X10N60 2/43, NH_P7_B7_X10N60 0/43, NH_U7_B7_X30N120 0/43

Reading rule: exact is the verdict; first-order (FO sections) only chose the cells. Mean columns: mean_all (all weeks) vs ref; dmean carry-dropped is not used here. R-vs-dollar note: both items are location rules (points / fractions of target / minutes), independent of lot size, so they transfer unchanged to the user's x1.75 lots; only the dollar P&L scales.

## 0. Identity checks (hook with no rules == JN05W2 on 202610)
```
IDENTITY NC_ID trades 598 598 net 25943.82 25943.82 IDENTICAL

IDENTITY NH_ID trades 598 598 net 25943.82 25943.82 IDENTICAL

```

## 1. Trend-week clause FIRST (L6M, exact; sum of the 5 best LPB_BASE weeks, winning weeks turned losing)

(no set has L6M yet)

## 3. First-order screens that chose the cells
anomalous trades excluded 10
## FO-4. Flat cut by context (K7, U7, A7, M7) - first-order on LPB_BASE trades, 1-s paths (slip 1.2; engine uses 0.80, so each fire is ~$8/lot better in exact)

Grid per book: flat level {35,40,45,50,55} separately for FRESH and RECHASE tags (36 combos), lots-group and session splits, time condition nft (still below -X after N min; X 10/20/30, N 5/10/15/20) for all / fresh / rechase. Cells per book: K7 125, U7 115, A7 105, M7 110 (family size). net $/wk, DD cut % on the stack.

### K7: bi-weekly WF re-pick (trailing 26 wk, max net, off if <=0): OOS total $-70202 over 161 weeks (positive weeks 53%); most picked: T:nft10_5m|all x11, G:flat50|L1 x8, T:nft20_10m|rechase x7

| cell | fires | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | PRE | X' | stops saved $/wk L6M | recoveries lost $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| G:flat50|S3 | 504 | 144 | 169 | -2 | -16 | -153 | 1.0 | -0.8 | 0.4 | -4.9 | 239 | 0 |
| T:nft30_5m|rechase | 150 | 72 | 78 | -86 | 59 | 219 | 1.2 | 2.2 | -0.8 | 0.0 | 399 | -400 |
| T:nft30_15m|rechase | 256 | 16 | 33 | -186 | 208 | 317 | 0.1 | 2.1 | 2.1 | 2.2 | 596 | -562 |
| F:fresh=flat55|rechase=off | 281 | 20 | 55 | -13 | 51 | -108 | 0.3 | 0.5 | 0.5 | 1.6 | 58 | 0 |
| G:flat55|S3 | 401 | 12 | 30 | 0 | 16 | -77 | -0.1 | -0.6 | -0.1 | 0.5 | 112 | 0 |
| G:flat45|S3 | 623 | 325 | 171 | -285 | -121 | -143 | 1.5 | -1.1 | 1.4 | -4.8 | 408 | 0 |

### U7: bi-weekly WF re-pick (trailing 26 wk, max net, off if <=0): OOS total $-69491 over 161 weeks (positive weeks 43%); most picked: T:nft10_5m|rechase x11, T:nft10_5m|all x9, G:flat50|S1 x7

| cell | fires | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | PRE | X' | stops saved $/wk L6M | recoveries lost $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| T:nft20_15m|all | 134 | 103 | 280 | 350 | 215 | 19 | -0.7 | -6.8 | 4.8 | 3.9 | 1357 | -1508 |
| T:nft10_20m|fresh | 110 | 644 | 736 | -172 | 282 | 297 | -1.6 | 0.4 | -2.4 | 2.4 | 1119 | -670 |
| T:nft20_15m|fresh | 57 | 481 | 529 | 160 | 60 | 0 | 1.4 | 0.3 | 3.4 | 0.9 | 782 | -397 |
| T:nft10_15m|fresh | 111 | 694 | 611 | -67 | 190 | 76 | -0.7 | 1.4 | 3.4 | 4.8 | 1242 | -651 |
| T:nft20_5m|all | 57 | 305 | 175 | 233 | 0 | 0 | 8.0 | -4.2 | 0.3 | 0.0 | 1098 | -1070 |
| T:nft10_10m|fresh | 92 | 524 | 445 | 72 | -67 | 106 | 0.5 | 1.3 | 0.9 | 2.0 | 1107 | -893 |

### A7: bi-weekly WF re-pick (trailing 26 wk, max net, off if <=0): OOS total $-8311 over 161 weeks (positive weeks 36%); most picked: T:nft30_15m|all x10, T:nft10_20m|all x8, F:fresh=flat50|rechase=flat35 x7

| cell | fires | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | PRE | X' | stops saved $/wk L6M | recoveries lost $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| T:nft20_10m|fresh | 10 | 86 | 55 | 23 | 0 | 0 | 0.0 | 0.0 | 0.7 | 0.0 | 77 | 0 |
| T:nft10_10m|fresh | 28 | 162 | 47 | 20 | 4 | -36 | 0.0 | 0.0 | 0.7 | 0.7 | 148 | 0 |
| T:nft20_5m|fresh | 7 | 102 | 49 | 18 | 0 | 0 | 0.0 | 0.0 | 0.9 | 0.0 | 102 | 0 |
| T:nft20_15m|fresh | 19 | 55 | 58 | 23 | 14 | -101 | 0.0 | 0.8 | 0.5 | 0.0 | 58 | 0 |
| T:nft30_10m|all | 38 | 75 | 68 | -18 | 0 | 28 | 0.1 | 0.7 | 0.6 | 0.0 | 207 | -164 |
| T:nft20_20m|fresh | 22 | 105 | 10 | 25 | 36 | -93 | 0.0 | 1.0 | 0.5 | 1.3 | 97 | 0 |

### M7: bi-weekly WF re-pick (trailing 26 wk, max net, off if <=0): OOS total $1509 over 161 weeks (positive weeks 45%); most picked: F:fresh=flat40|rechase=flat55 x12, T:nft10_15m|fresh x11, T:nft10_15m|all x8

| cell | fires | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | PRE | X' | stops saved $/wk L6M | recoveries lost $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| F:fresh=flat40|rechase=off | 195 | 80 | 32 | 138 | 76 | 68 | -0.5 | 0.0 | 0.0 | -1.5 | 85 | 0 |
| T:nft10_15m|fresh | 96 | 210 | 31 | 54 | 162 | -32 | 2.2 | -1.9 | -0.8 | 2.7 | 61 | -60 |
| F:fresh=flat45|rechase=off | 134 | 40 | 30 | 63 | 92 | 82 | -0.7 | 0.0 | -0.5 | 0.8 | 69 | 0 |
| F:fresh=flat40|rechase=flat55 | 516 | 43 | 4 | 81 | -72 | 129 | -0.3 | 0.2 | 0.5 | -1.7 | 169 | 0 |
| F:fresh=flat50|rechase=off | 100 | 16 | 7 | 36 | 28 | 53 | 0.0 | 0.0 | -0.1 | 0.0 | 37 | 0 |
| F:fresh=flat40|rechase=flat50 | 693 | 35 | 49 | 56 | 28 | -253 | -0.2 | 0.5 | 0.8 | 0.1 | 355 | -91 |

## FO-3. Hold-or-take by location only (K7, U7, A7, M7, P7, H7) - first-order, nz_kern conditions, take = market exit next 1-s mid - 1.2

Cells (223 per book): A stall (arm {.6,.7,.8,.9} x secs since high {10..160}), B reversal (arm x drawdown from high X pts {6..30} over last N s {30,60,120}), C ladder floor (m,f), plus A+B, A+C, B+C combos (<= 3 plain conditions). clip = Target fills taken early ($/wk lost).

### K7: bi-weekly WF re-pick OOS total $-70904 over 161 weeks (positive weeks 17%); most picked: off x39, B rev arm=0.8 X=30pt N=30s x18, B rev arm=0.9 X=15pt N=30s x3

| cell | fires | clipped fills | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | clip $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|
| (no cell positive on L6M, HOLD and 3.5-year total) |||||||||||

### U7: bi-weekly WF re-pick OOS total $-104664 over 161 weeks (positive weeks 26%); most picked: B rev arm=0.6 X=30pt N=120s x9, B rev arm=0.7 X=30pt N=30s x6, off x6

| cell | fires | clipped fills | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | clip $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|
| B rev arm=0.7 X=30pt N=120s | 140 | 65 | 899 | 604 | 115 | -67 | -1091 | 5.2 | -0.5 | 1567 |
| B rev arm=0.7 X=20pt N=60s | 216 | 126 | 539 | 498 | 71 | 88 | -1300 | 5.2 | -3.1 | 2554 |
| B rev arm=0.7 X=20pt N=120s | 290 | 184 | 1152 | 835 | -184 | -73 | -953 | 6.7 | -4.6 | 2794 |
| B rev arm=0.8 X=30pt N=120s | 89 | 45 | 267 | 282 | 149 | -168 | -993 | 0.0 | 2.3 | 1254 |

### A7: bi-weekly WF re-pick OOS total $-35993 over 161 weeks (positive weeks 14%); most picked: B rev arm=0.8 X=30pt N=60s x10, B rev arm=0.6 X=30pt N=30s x9, B rev arm=0.6 X=30pt N=120s x7

| cell | fires | clipped fills | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | clip $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|
| (no cell positive on L6M, HOLD and 3.5-year total) |||||||||||

### M7: bi-weekly WF re-pick OOS total $-56563 over 161 weeks (positive weeks 35%); most picked: off x7, C floor m=0.9 f=0.5 x6, B rev arm=0.7 X=15pt N=30s x5

| cell | fires | clipped fills | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | clip $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|
| C floor m=0.9 f=0.2 | 154 | 70 | 248 | 43 | -30 | 178 | 14 | 2.3 | 0.1 | 532 |
| C floor m=0.9 f=0.5 | 244 | 160 | 209 | 116 | -33 | 153 | -235 | 3.2 | 1.1 | 854 |
| C floor m=0.9 f=0.6 | 302 | 217 | 283 | 192 | -65 | 83 | -165 | 3.6 | 1.5 | 863 |
| B+C rev(0.9,20pt,120s)+floor(0.9,0.5) | 281 | 197 | 208 | 143 | -67 | 121 | -190 | 3.2 | 1.5 | 905 |
| C floor m=0.9 f=0.7 | 403 | 318 | 310 | 250 | -130 | 106 | -213 | 2.8 | 1.8 | 947 |

### P7: bi-weekly WF re-pick OOS total $-124351 over 161 weeks (positive weeks 35%); most picked: B rev arm=0.9 X=10pt N=60s x9, B rev arm=0.8 X=10pt N=60s x7, B rev arm=0.9 X=20pt N=30s x5

| cell | fires | clipped fills | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | clip $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|
| B rev arm=0.7 X=10pt N=60s | 1509 | 1123 | 2375 | 789 | 172 | 131 | -1662 | 3.6 | -4.1 | 15931 |
| B rev arm=0.9 X=30pt N=30s | 28 | 7 | 205 | 206 | 124 | 0 | 5 | 0.0 | 0.0 | 77 |
| B rev arm=0.9 X=30pt N=60s | 59 | 25 | 360 | 176 | 113 | -308 | 73 | 0.0 | -2.5 | 439 |

### H7: bi-weekly WF re-pick OOS total $-28382 over 161 weeks (positive weeks 21%); most picked: B rev arm=0.6 X=20pt N=120s x7, C floor m=0.9 f=0.5 x7, B rev arm=0.6 X=15pt N=60s x6

| cell | fires | clipped fills | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | clip $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|
| B+C rev(0.9,20pt,120s)+floor(0.8,0.2) | 134 | 73 | 214 | 183 | -139 | 534 | 6 | 0.0 | 4.4 | 617 |
| C floor m=0.8 f=0.7 | 312 | 250 | 218 | 83 | -194 | 677 | 145 | -4.6 | 5.1 | 1101 |
| B+C rev(0.9,10pt,60s)+floor(0.8,0.2) | 189 | 128 | 90 | 107 | -147 | 540 | 75 | -1.8 | 3.4 | 789 |
| B+C rev(0.8,30pt,30s)+floor(0.8,0.2) | 119 | 58 | 76 | 70 | -122 | 527 | 24 | 0.0 | 4.4 | 668 |
| C floor m=0.8 f=0.2 | 118 | 57 | 137 | 99 | -144 | 527 | 24 | 0.0 | 4.4 | 607 |

