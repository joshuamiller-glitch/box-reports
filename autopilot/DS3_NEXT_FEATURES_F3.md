# DS3_NEXT_FEATURES_F3 - T-NEXT-FEATURES items 3 (hold-or-take by location) and 4 (flat cut by context). W-F3. Shadow only, no PASS claim.
Updated 2026-11-12 18:26Z. Directive autopilot/DIRECTIVE_T_NEXT_FEATURES_20261112.md; prereg autopilot/NEXTF3_PREREG.md (sha in DECISIONS.md). BASE = JN05W2 (LPB panel + F3 + E1 + C22 + BR3S + FLAT45K, exact 43 months, W-J). Item-4 sets keep FLAT45K on K7 unless the cell says replace. Exact sets run one per job (jn05_run2.py, TP engine, tag NEXTF); months done: NC_U7_T10_15F 0/43, NC_U7_T20_15F 0/43, NC_U7_T20_15A 0/43, NC_K7_T20_20RC 0/43, NC_K7_F55_45 0/43, NC_A7_T10_10F 0/43, NC_M7_T10_10A 0/43, NH_P7_A9_N20 0/43, NH_P7_B9_X10N30 0/43, NH_U7_B7_X20N60 0/43, NH_M7_C9_F2 0/43, NH_M7_B9_X10N60 0/43

Reading rule: exact is the verdict; first-order (FO sections) only chose the cells. Mean columns: mean_all (all weeks) vs ref; dmean carry-dropped is not used here. R-vs-dollar note: both items are location rules (points / fractions of target / minutes), independent of lot size, so they transfer unchanged to the user's x1.75 lots; only the dollar P&L scales.

## 0. Identity checks (hook with no rules == JN05W2 on 202610)
```
(not yet)
(not yet)
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

### K7: bi-weekly WF re-pick OOS total $-39240 over 161 weeks (positive weeks 27%); most picked: off x22, B+C rev(0.7,15pt,30s)+floor(0.5,0.2) x8, B rev arm=0.8 X=20pt N=60s x8

| cell | fires | clipped fills | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | clip $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|
| (no cell positive on L6M, HOLD and 3.5-year total) |||||||||||

### U7: bi-weekly WF re-pick OOS total $-73885 over 161 weeks (positive weeks 26%); most picked: off x6, B rev arm=0.6 X=6pt N=60s x6, B rev arm=0.8 X=30pt N=30s x5

| cell | fires | clipped fills | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | clip $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|
| B rev arm=0.7 X=30pt N=120s | 146 | 68 | 953 | 631 | 145 | -68 | -1132 | 0.5 | -0.4 | 1733 |
| B rev arm=0.7 X=20pt N=60s | 227 | 132 | 618 | 439 | 117 | 95 | -1342 | 6.3 | -2.5 | 2704 |
| B rev arm=0.8 X=30pt N=120s | 94 | 47 | 474 | 383 | 179 | -178 | -993 | -7.4 | -5.2 | 1290 |
| B rev arm=0.7 X=20pt N=120s | 299 | 191 | 1250 | 784 | -150 | -66 | -995 | 12.9 | -3.7 | 2933 |

### A7: bi-weekly WF re-pick OOS total $-45348 over 161 weeks (positive weeks 13%); most picked: B rev arm=0.6 X=30pt N=120s x9, B rev arm=0.8 X=30pt N=60s x8, off x7

| cell | fires | clipped fills | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | clip $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|
| (no cell positive on L6M, HOLD and 3.5-year total) |||||||||||

### M7: bi-weekly WF re-pick OOS total $-27545 over 161 weeks (positive weeks 34%); most picked: off x9, C floor m=0.9 f=0.5 x7, B rev arm=0.7 X=15pt N=120s x4

| cell | fires | clipped fills | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | clip $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|
| C floor m=0.9 f=0.2 | 177 | 79 | 360 | 209 | -35 | 238 | 14 | 3.4 | 1.2 | 775 |
| C floor m=0.9 f=0.7 | 461 | 360 | 467 | 439 | -160 | 180 | -159 | 5.0 | 2.4 | 1340 |
| C floor m=0.9 f=0.6 | 351 | 251 | 377 | 346 | -108 | 155 | -112 | 3.6 | 3.0 | 1281 |
| C floor m=0.9 f=0.5 | 284 | 186 | 339 | 285 | -76 | 221 | -269 | 4.0 | 2.5 | 1215 |
| B rev arm=0.9 X=15pt N=60s | 335 | 238 | 302 | 328 | -138 | 134 | 51 | 5.1 | 2.7 | 1323 |

### P7: bi-weekly WF re-pick OOS total $-221135 over 161 weeks (positive weeks 33%); most picked: B rev arm=0.6 X=30pt N=60s x6, A stall arm=0.7 N=160s x6, B rev arm=0.9 X=30pt N=30s x5

| cell | fires | clipped fills | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | clip $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|
| A stall arm=0.9 N=10s | 1508 | 1390 | 2793 | 1236 | 281 | -69 | -568 | 26.0 | -2.1 | 3853 |
| B rev arm=0.9 X=10pt N=30s | 545 | 428 | 1652 | 589 | 479 | 258 | -31 | 26.6 | -5.4 | 3984 |
| A+B stall(0.9,20s)+rev(0.9,10pt,60s) | 1355 | 1237 | 2206 | 871 | 225 | -77 | -813 | 24.7 | -6.4 | 4310 |
| A+C stall(0.9,20s)+floor(0.9,0.2) | 1349 | 1231 | 2168 | 877 | 174 | -66 | -789 | 24.8 | -5.1 | 4260 |
| A stall arm=0.9 N=20s | 1349 | 1231 | 2168 | 877 | 174 | -66 | -789 | 24.8 | -5.1 | 4260 |

### H7: bi-weekly WF re-pick OOS total $-19789 over 161 weeks (positive weeks 23%); most picked: B rev arm=0.9 X=15pt N=120s x7, B rev arm=0.9 X=20pt N=120s x6, B rev arm=0.6 X=15pt N=60s x6

| cell | fires | clipped fills | net/wk L6M | HOLD | PRE | X' | GAP | DD cut L6M | HOLD | clip $/wk L6M |
|--|--|--|--|--|--|--|--|--|--|--|
| B+C rev(0.9,20pt,120s)+floor(0.8,0.2) | 144 | 80 | 103 | 153 | -65 | 499 | 6 | 0.7 | 2.7 | 754 |
| C floor m=0.8 f=0.7 | 337 | 272 | 93 | 51 | -138 | 642 | 123 | 1.2 | 3.2 | 1282 |
| B rev arm=0.8 X=6pt N=30s | 382 | 317 | 172 | 157 | -153 | 422 | 193 | 1.9 | 3.9 | 1276 |
| C floor m=0.8 f=0.2 | 126 | 62 | 24 | 52 | -127 | 492 | 24 | 0.7 | 2.7 | 747 |
| B rev arm=0.8 X=6pt N=60s | 409 | 344 | 179 | 101 | -199 | 545 | 101 | 1.9 | 4.0 | 1257 |

