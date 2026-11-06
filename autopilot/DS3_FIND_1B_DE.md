
# DS3_FIND_1B_DE - Step 1b (d)+(e): queue-aware passive entry and measured-cost room at 1 s, ES / RTY / NQ (ZL-2, 2026-11-06T00:46Z)
Prereg: l2vast/ds3/prereg/T_FIND_1B_DE_zl2_prereg.md sha256 6dd03514120a2650d3ca80ebbd8433d8af41a8ca9bb421893cd59e82f4676c86 (shared definitions: T_FIND_TICKMAP_prereg.md sha 081e392b). Data tables/<SYM>/1s 2023-08..2026-10 (no pre-2023 evidence). Truncation test (NQ, 24 cut checks) 0 failures; injected 3-row look-ahead detected (4 of 24; the rest had no trigger in the last 3 s). Measurement only: no tests, no candidates. Per-cell csv: out/find_1b_de/<SYM>_cells.csv (270 cells each). Fee 4.84 per round trip, same proxy for all three; ES tick \$12.50, RTY/NQ \$5.00.

## ES
Median measured spread 1.07 ticks; cells 270 (270 with n >= 500 triggers).
- room (E|move| \$ / round-trip cost \$) > 2 in 43% of cells, > 1 in 64%; market-in/market-out net G > 0 in 0 of 270 cells (best -1.17 ticks); passive net per trigger > 0 in 0 cells, with P(fill) >= 0.2 in 0.
- median room by horizon h: 1s 0.37, 5s 0.92, 15s 1.65, 60s 3.37, 300s 7.52; median P(fill) by h: 5s 0.43, 15s 0.54, 60s 1.00, 300s 1.00

Best 6 cells by passive net per trigger (ticks, after half-spread exit and fee, fills only), n >= 500:

| signal | session | h | n | P(fill) | room | G_mkt net | passive net / trigger | passive net / fill |
|--|--|--|--|--|--|--|--|--|
| imb1 | asia | 1 | 900994 | 0.00 | 0.18 | -1.51 | +0.000 | +nan |
| imb1 | london | 1 | 1008290 | 0.00 | 0.22 | -1.51 | +0.000 | +nan |
| imb1 | pre | 1 | 181282 | 0.00 | 0.31 | -1.46 | +0.000 | +nan |
| imb1 | nyam | 1 | 503779 | 0.00 | 0.55 | -1.43 | +0.000 | +nan |
| imb1 | close | 1 | 309618 | 0.00 | 0.35 | -1.42 | +0.000 | +nan |
| imb1 | nypm | 1 | 565418 | 0.00 | 0.39 | -1.41 | +0.000 | +nan |

Best 4 cells by market G net:

| signal | session | h | n | room | G_mkt net |
|--|--|--|--|--|--|
| imb5_ema10s | close | 300 | 111840 | 6.09 | -1.17 |
| imb5 | close | 300 | 189100 | 8.09 | -1.21 |
| imb5_ema10s | nypm | 300 | 209659 | 7.64 | -1.22 |
| imb10 | close | 300 | 168297 | 7.67 | -1.24 |

## RTY
Median measured spread 2.02 ticks; cells 270 (270 with n >= 500 triggers).
- room (E|move| \$ / round-trip cost \$) > 2 in 37% of cells, > 1 in 59%; market-in/market-out net G > 0 in 0 of 270 cells (best -1.95 ticks); passive net per trigger > 0 in 0 cells, with P(fill) >= 0.2 in 0.
- median room by horizon h: 1s 0.29, 5s 0.71, 15s 1.27, 60s 2.58, 300s 5.76; median P(fill) by h: 5s 0.45, 15s 0.51, 60s 1.00, 300s 1.00

Best 6 cells by passive net per trigger (ticks, after half-spread exit and fee, fills only), n >= 500:

| signal | session | h | n | P(fill) | room | G_mkt net | passive net / trigger | passive net / fill |
|--|--|--|--|--|--|--|--|--|
| imb1 | asia | 1 | 637130 | 0.00 | 0.13 | -3.51 | +0.000 | +nan |
| imb1 | london | 1 | 888964 | 0.00 | 0.16 | -3.31 | +0.000 | +nan |
| swpnet5 | pre | 1 | 61946 | 0.00 | 0.42 | -3.46 | +0.000 | +nan |
| imb1 | pre | 1 | 177102 | 0.00 | 0.25 | -3.12 | +0.000 | +nan |
| imb1 | nyam | 1 | 538780 | 0.00 | 0.47 | -2.67 | +0.000 | +nan |
| imb1 | nypm | 1 | 614217 | 0.00 | 0.30 | -2.56 | +0.000 | +nan |

Best 4 cells by market G net:

| signal | session | h | n | room | G_mkt net |
|--|--|--|--|--|--|
| big2net5 | close | 300 | 21527 | 6.58 | -1.95 |
| big2net5 | close | 60 | 22018 | 3.53 | -2.15 |
| big2net5 | close | 15 | 22063 | 1.88 | -2.37 |
| big2net5 | close | 1 | 22266 | 0.45 | -2.38 |

## NQ
Median measured spread 2.92 ticks; cells 270 (270 with n >= 500 triggers).
- room (E|move| \$ / round-trip cost \$) > 2 in 61% of cells, > 1 in 81%; market-in/market-out net G > 0 in 0 of 270 cells (best -1.18 ticks); passive net per trigger > 0 in 1 cells, with P(fill) >= 0.2 in 1.
- median room by horizon h: 1s 0.72, 5s 1.69, 15s 2.97, 60s 5.95, 300s 13.58; median P(fill) by h: 5s 0.53, 15s 0.53, 60s 1.00, 300s 1.00

Best 6 cells by passive net per trigger (ticks, after half-spread exit and fee, fills only), n >= 500:

| signal | session | h | n | P(fill) | room | G_mkt net | passive net / trigger | passive net / fill |
|--|--|--|--|--|--|--|--|--|
| big2net5 | nyam | 300 | 28244 | 1.00 | 25.05 | -1.18 | +1.347 | +1.35 |
| imb1 | nypm | 1 | 758553 | 0.00 | 0.84 | -3.27 | +0.000 | +nan |
| imb1 | london | 1 | 1644743 | 0.00 | 0.38 | -4.47 | +0.000 | +nan |
| imb1 | pre | 1 | 271518 | 0.00 | 0.57 | -3.97 | +0.000 | +nan |
| imb1 | nyam | 1 | 674718 | 0.00 | 1.23 | -3.51 | +0.000 | +nan |
| imb1 | close | 1 | 434685 | 0.00 | 0.68 | -3.50 | +0.000 | +nan |

Best 4 cells by market G net:

| signal | session | h | n | room | G_mkt net |
|--|--|--|--|--|--|
| big2net5 | nyam | 300 | 28244 | 25.05 | -1.18 |
| big2net5 | nypm | 300 | 17411 | 18.18 | -2.77 |
| big2net5 | nyam | 60 | 28238 | 11.48 | -2.81 |
| ofi5s | close | 300 | 217074 | 17.54 | -3.24 |

## Reading
At 1-s measured spreads, entering and leaving at market gives a negative net on every 1b (a) trigger cell of all three instruments; the room ratio exceeds 2 in many long-horizon cells only because those moves are large relative to cost, but G (the signed continuation) is not large enough to pay the spread and fee. Passive-in/market-out is tested with queue position and adverse selection; the cells above show whether any has positive net with P(fill) >= 0.2. Nothing here is a book candidate: the frozen map -> book rule (p_family <= 0.05 on CHAR-A (a) rows) is CHAR-A's.

## CORRECTION 2026-11-06T00:47Z (ZL-2): the "best by passive net" tables above sorted ties at zero (h = 1 s cells have no passive fills by construction). Corrected: cells with P(fill) > 0 only, plus the NQ cell that is positive.

### ES: best 5 cells by passive net per trigger (P(fill) > 0, n >= 500)

| signal | session | h | n | P(fill) | room | G_mkt net | passive net / trigger | passive net / fill |
|--|--|--|--|--|--|--|--|--|
| imb5_ema10s | close | 300 | 111840 | 1.00 | 6.09 | -1.17 | -0.129 | -0.13 |
| imb5 | close | 300 | 189100 | 1.00 | 8.09 | -1.21 | -0.147 | -0.15 |
| imb10 | close | 300 | 168297 | 1.00 | 7.67 | -1.24 | -0.181 | -0.18 |
| imb5_ema10s | nypm | 300 | 209659 | 1.00 | 7.64 | -1.22 | -0.187 | -0.19 |
| imb10 | nypm | 300 | 312655 | 1.00 | 8.44 | -1.26 | -0.220 | -0.22 |

### RTY: best 5 cells by passive net per trigger (P(fill) > 0, n >= 500)

| signal | session | h | n | P(fill) | room | G_mkt net | passive net / trigger | passive net / fill |
|--|--|--|--|--|--|--|--|--|
| big2net5 | london | 60 | 4302 | 1.00 | 2.42 | -2.98 | -0.521 | -0.52 |
| big2net5 | london | 300 | 4310 | 1.00 | 5.56 | -3.02 | -0.566 | -0.57 |
| imb10 | pre | 300 | 102024 | 1.00 | 6.09 | -2.97 | -0.592 | -0.59 |
| imb5_ema10s | pre | 300 | 66378 | 1.00 | 5.17 | -2.85 | -0.617 | -0.62 |
| big2net5 | close | 300 | 21527 | 1.00 | 6.58 | -1.95 | -0.622 | -0.62 |

### NQ: best 5 cells by passive net per trigger (P(fill) > 0, n >= 500)

| signal | session | h | n | P(fill) | room | G_mkt net | passive net / trigger | passive net / fill |
|--|--|--|--|--|--|--|--|--|
| big2net5 | nyam | 300 | 28244 | 1.00 | 25.05 | -1.18 | +1.347 | +1.35 |
| big2net5 | nyam | 60 | 28238 | 1.00 | 11.48 | -2.81 | -0.289 | -0.29 |
| big2net5 | nypm | 300 | 17411 | 1.00 | 18.18 | -2.77 | -0.435 | -0.43 |
| ofi5s | nyam | 300 | 328878 | 1.00 | 24.76 | -3.27 | -0.728 | -0.73 |
| big2net5 | london | 300 | 7313 | 1.00 | 9.60 | -4.19 | -0.733 | -0.73 |


## CORRECTION 2 2026-11-06T00:47:57Z (ZL-2): BUG FOUND - every P(fill) and passive-net value for h = 60 and 300 s in the tables above (both the original and the first correction) is WRONG: cells that never filled were coded with fill time T+1 = 31 s and counted as filled whenever k < h. The market-in/market-out columns (room, G_mkt net) and all h <= 15 values are unaffected. A fixed run (filled = k < h and k <= T) is being recomputed; its tables will be appended below and replace these values. Original csv kept in out/find_1b_de/_bug_unfilled_as_filled/.
