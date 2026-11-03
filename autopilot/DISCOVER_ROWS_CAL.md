# DISCOVER_ROWS_CAL (CAL interim rows, DS3_DISCOVER format, 2026-11-03 ~19:00Z; B event books and C window books)
Format: book | session | mean ($/wk, L6M, 2 lots) | maxDD (L6M weekly-cum, $) | Calmar (L6M, mean/maxDD) | stack Calmar with it (L6M base 0.258; with carrying week dropped base 0.695; HOLD base 0.185) | windows | label.
Measured fills LIVE basis (stops 2.45, market/time/flat 0.80, fee 0.242/lot). Release-minute slippage shown as separate columns in the CSVs (never the base). Stack = Q1-A ts2.
Plain sentence, family B (event books): the first minutes after CPI/NFP/ISM/auction releases carry 2-8x normal range, but entering after the move starts and fading or continuing it does not beat random days at the family level: the real 368-book grid passes the TOLERANT gate 53 times, the same grid on 30 placebo replicates 48 times (max 59).
Plain sentence, family C (calendar windows): of 268 window books the real grid passes TOLERANT 28 times against 33 on the placebo replicates; the stack already earns in Mon-Tue Asia, and the 15:00-17:00 cells that are empty in the stack lose as stand-alone books.

| book | session | mean | maxDD | Calmar | stack Calmar with it | windows | label |
|---|---|---|---|---|---|---|---|
| CPI E1 fade 60/60 T30 (enter T+1m against the first move) | pre (08:30) | +350 | 2,508 | 0.139 | 0.273 (0.698 dropcar; HOLD 0.191) | L6M+ HOLD+ PRE+ X'- ; 6 L6M trades; 2023 -601 / 2026 +1,444 $/trade; placebo p(L6M,PRE,HOLD) 0.000 | LEAD-thin (family at placebo rate) |
| NFP E2 sign 60/60 T30 (short if actual > prior, T+2m; prior is not consensus) | pre (08:30) | +383 | 1,622 | 0.236 | 0.274 (0.701; HOLD 0.183) | L6M+ HOLD+ PRE+ X'- ; 6 L6M trades; 2023-24 negative | LEAD-thin |
| NFP E2 cont 60/60 T30 | pre | +500 | 0 | n/a | 0.275 (0.704; HOLD 0.191) | L6M+ HOLD+ PRE+ X'- ; 6 trades | LEAD-thin |
| ISM mfg E5 fade 60/60 T30 (T+5m) | nyam (10:00) | +378 | 0 | n/a | 0.267 (0.703; HOLD 0.182) | all four windows + ; 5 L6M trades; slip +3: +373 | LEAD-thin |
| ISM svc E5 fade 1R-ATR T30 | nyam | +237 | 2,209 | 0.107 | 0.270 (0.698; HOLD 0.190) | L6M+ HOLD+ PRE+ X'+ ; 6 trades; all four years + per trade | LEAD-thin |
| Auction 3Y E1 cont 1R-ATR T60 | nypm (13:00) | +296 | 1,305 | 0.227 | 0.266 (0.701; HOLD 0.189) | L6M+ HOLD+ PRE+ X'- ; 2023 negative | LEAD-thin |
| FOMC 14:35 trend (cont) 60/60 T60 | nypm | +173 | 2,508 | 0.069 | 0.265 (0.723; HOLD 0.185) | HOLD- (-59), every year per trade negative | no (volatility excess is not direction) |
| Mon-Tue 19:00 Asia continuation (prev 30 min) 60/60 T180 | asia | +577 | 6,642 | 0.087 | 0.264 (0.702; HOLD 0.197) | L6M+ HOLD+ PRE+ X'+ ; 371 trades; $/trade 23 +30, 24 +19, 25 +179, 26 +351; slip +1: 386; placebo ranks (shift5/side/days) L6M 0.96/0.87/0.89, PRE 0.78/0.82/0.73, HOLD 1.0/0.98/1.0 | LEAD (best of C; not confirmed; stack already earns here) |
| Asia 18:00 ORB (30-min range) Mon 60/60 T120 | asia | +562 | 10,500 | 0.054 | 0.261 (0.684; HOLD 0.198) | L6M+ HOLD+ PRE+ X'+ ; 157 trades; ranks PRE/HOLD 0.95-1.0, L6M 0.85-0.95; maxDD 18.7x the weekly mean | LEAD-thin |
| Asia 18:00 ORB Mon-Tue 60/60 T120 | asia | +458 | 10,028 | 0.046 | 0.249 (0.656; HOLD 0.205) | L6M+ HOLD+ PRE+ X'+ ; stack L6M Calmar worse with it | no (deepens L6M maxDD) |
| Opex Friday 15:00 short 1R-ATR T60 | close | +242 | 779 | 0.311 | 0.262 (0.700; HOLD 0.184) | 43 trades, 6 in L6M; PRE placebo p 0.465 | no (6 trades) |
| 16:00 settlement window, any direction (889 trades) | close | -574..+59 | 17-30k | <0 | worse | NOW-ONLY fails for all 16 variants | no |
| RTH 09:30 ORB | nyam | -2,660 | - | - | - | L6M/HOLD strongly negative, PRE +1,594 | no (regime flip; fade mirror untested) |
All other event types (PPI, PCE, GDP, retail, claims, FOMC statement/presser, auction 30Y): no book separates from the placebo; see `DISCOVER_EVENT_BOOKS.csv`.
Claim to carry: nothing here is an ADDITION candidate that survives the family-level placebo. The nearest to a real shape is the Mon-Tue 19:00 Asia continuation (371 trades), but it sits inside the stack's best cell.

## 2026-11-03 ~21:00Z DISC_C validation rows (prereg sha256 3d7cba2b...; details DISCOVER_C_VALIDATION.md; 464 cells in DEAD_CELLS program DISC_C)
| book | session | mean/wk (L6M) | maxDD (L6M) | Calmar | stack Calmar with it (L6M; dropcar; HOLD) | windows | label |
|---|---|---|---|---|---|---|---|
| Mon-Tue 19:00 Asia continuation (look30, 60/60, T180) | asia | +577 | 6.6k | 0.087 | 0.264; 0.702; 0.197 (m=4 equal-risk 0.280; 0.723; 0.235, but PRE Calmar 0.150 -> 0.122) | HOLD +820 MID +960 PRE +104 X' +67; grid 16% positive L6M/HOLD/PRE, spike (19:30 negative, 75/75 negative); family best-of-30 null p 0.45; walk-forward OOS +585/+497/+340/+138 but from other chosen cells; +2 pt slip PRE -79; 99.7% of entries overlap live Asia entries, profit only on trades with the live side | FRAGILE (stack's own exposure) |
| RTH 09:30 breakout FADE (30-min range, 60/60, T240) | nyam | +2,413 | 9.8k | 0.246 | 0.339; 0.796; HOLD 0.177 | L3M +2,594 HOLD +1,367 MID +1,581 PRE -1,975 X' -514; negative every quarter 2023Q2-2025Q4 except 2023Q3, positive each 2026 quarter; corr stack -0.09; slip +3 L6M +1,522; NOW-ONLY yes, TOLERANT no | LEAD-regime (not an addition: HOLD maxDD 122k -> 135k) |
| RTH 09:30 FLIP (trailing-20-day breakout $ > 0 ? breakout : fade) | nyam | +1,220 mean of 12 | | | | HOLD +116 MID -524 PRE -225; best-of-12 null p 0.51 | DEAD (lag rule cannot date the 2025Q3 flip) |
| 15:30 reversal (fade prev 30 min, 60/60, T60) | close | +310 | 13.5k | 0.023 | | HOLD -454 MID -806 PRE +466 | DEAD |
| 15:50 MOC proxy days (month/quarter-end, opex) | close | within +-200 | | | | 28-127 trades per day set | THIN/DEAD |
| Wed 18:00 contrarian (opposite to live entry, 1 lot/row; row stats 60/60 T60, stack columns for 60/60 T120) | asia | +671 | 2.6k | 0.26 | 0.271; HOLD 0.184 (m=1) | HOLD +109 MID -487 PRE -89 X' +168; null p L6M 0.004 PRE 0.024 HOLD 0.26; T120 HOLD -155 | FRAGILE candidate (not a filter) |

## 2026-11-04 ~02:00Z DISC_D rows (prereg sha256 246396723b2f727b084a002289836d3e631a488ece52300fb860a38e9e3ad9c3; DISCOVER_D.md; 344 cells in DEAD_CELLS DISC_D)
| book | session | mean/wk (L6M) | maxDD (L6M) | Calmar | stack Calmar with it (L6M; dropcar; HOLD) | windows | label |
|---|---|---|---|---|---|---|---|
| D4 NY-AM VWAP fade (>=10pt away, close across, fade, 60/60, T120), 1,360 trades | nyam | +1,424 | 15.9k | 0.090 | 0.338; 0.699; 0.256 | HOLD +2,526 MID +6,803 PRE -493 (within -0.5 MDE) X' -135; family-wise p 0.017 (side) / 0.00 (shift); slip +3 L6M -332; overlap 72%; gate_v2 false | LEAD-regime (not cleared) |
| D3 overnight high/low fade at 09:30-10:00 (break+reclaim, 60/60, T60), 525 trades | nyam | +703 | 7.6k | 0.092 | 0.274; 0.713; 0.206 | L3M -135 HOLD +1,172 MID +2,900 PRE +46 X' +61; p side 0.10 / shift 0.00; overlap 37% | LEAD-thin |
| Bundle: ON_RTH fade + VWAP NY-AM fade + 30-min ORB fade (2 lots each) | nyam | +4,540 | 9.9k | 0.46 | at 0.5x: 0.355; 0.755; 0.222 (MID 0.552, PRE 0.128); at 1x: 0.503; 0.818; 0.239 (PRE 0.108) | the books are uncorrelated (0.01-0.21) but one regime: negative/flat 2023-25Q2, positive 2026; hedges the stack NY-AM sleeve (0 in 2026Q1 vs +44..143k/quarter in 2025) | LEAD-regime bundle (PRE cost) |
| D3 Asia-extreme reclaim in London; D3 prior-day extreme | london / nyam | -742 / +166 means | | | | 0 of 72 books positive in L6M, HOLD and MID | DEAD |
| D4 Asia VWAP cross continuation (d0, T120) | asia | +2,762 | 10.6k | 0.26 | | HOLD +2,516 MID +1,008 PRE +204 X' -863; the Mon-Tue-style Asia continuation again; inside D4 family null | FRAGILE |
| D5 ORB range-stop (96) | all | best S +624 | | | | family p 0.68 / 0.77 | DEAD |
| D6 gap-go/fill (80) | nyam | best S +478 | | | | family p 0.73 / 0.77 | DEAD |

## 2026-11-04 ~04:00Z DISC_R regime rows (DISCOVER_REGIME.md; 12 switch cells in DEAD_CELLS DISC_R; n_tested for Bonferroni = 1,458)
| book | session | mean/wk (L6M) | maxDD (L6M) | Calmar | stack Calmar with it (L6M; dropcar; HOLD) | windows | label |
|---|---|---|---|---|---|---|---|
| NY-AM fade bundle (ON_RTH + VWAP + ORB30, 2 lots each), plain | nyam | +4,540 | 9.9k | 0.46 | 0.5x: 0.355; 0.755; 0.222 (1x: 0.503; 0.818; 0.239); equal-risk HOLD k=1.56: 0.228 -> 0.293 | HOLD +5,065 MID +11,284 PRE -2,422 X' -588 | LEAD-regime |
| same, causal switch (trailing-40-day bundle P&L > 0) | nyam | +4,540 | 9.9k | 0.46 | 0.5x: 0.355; 0.755; 0.220 (1x: 0.503; 0.818; 0.237) | HOLD +4,758 MID +10,298 PRE -986 X' +354; best-of-12 null p 0.005 but only +6% S over plain; ER<x condition hurts; gate_v2 false for all 3 components (p_book 0.12 / 0.03 / 0.86), Bonferroni 1.0 | LEAD-regime (not cleared) |
| diagnostic | - | - | - | - | - | no efficiency/autocorr/VR shift; open-hour range share +5.5 (NQ) +5.5 (ES) +7.3 (YM) pts p<=0.001; NQ ORB 0.25% hit rate -0.107 p 0.009; detection lag 5-30 days via own trailing P&L / ORB hit rate; ER too slow (47-157 d) | INFO |

## 2026-11-04 DISC_E rows (prereg sha256 3b553875f812e4bf4e948e4fa7908cbfa1b9992e63b68da6c45409e640032588; DISCOVER_E.md; 412 cells DISC_E; cumulative n_tested 1,870)
| book | session | mean/wk (L6M) | maxDD (L6M) | Calmar | stack Calmar with it (L6M; dropcar; HOLD) | windows | label |
|---|---|---|---|---|---|---|---|
| E1 NY positive-gamma fade at open+30 min (60/60, T60), 667 trades | nyam | +1,283 | 13.0k | 0.099 | 0.302; 0.729; 0.187 | HOLD +987 MID -32 PRE -712 X' +624; family p side 0.95 / shift 0.58; gate v2 p_book 0.41; overlap 67% | DEAD (echo of the 2026 NY-AM regime) |
| E1 Asia negative-gamma momentum R1, h15 | asia | +649 (22 L6M trades) | 6.5k | | | thin | DEAD (thin) |
| E2 ES-lead entry, Asia D10 4bp L1 60/60, 1,369 trades | asia | +318 | 7.6k | 0.042 | 0.304; 0.687; 0.196 | HOLD +385 MID +410 PRE -327; slip +1 pt L6M -309; L2 S -2; family p 0.70 / 0.10; overlap 79% | DEAD (below cost; latency-fragile) |
| E3 L2 entry engine (72 books) | asia/london/nyam | best S -151 | | | | 0 of 72 S>0; p 0.83 / 0.63 | DEAD |
| E4 all-day fade 10:30-13:30 (60/60, T60), 2,625 trades | nyam | +1,147 | 26.0k | 0.044 | 0.358; 0.609; 0.187 | HOLD +1,054 MID +61 PRE -262 X' -495; slip +2 pt L6M -690; p 0.85 / 0.98 | DEAD |
| E4 quiet-day / wide-day flagged books (B02 exact) | nyam | quiet fade -232 / quiet cont -379 | | | | flag adds nothing over all-days | DEAD |
