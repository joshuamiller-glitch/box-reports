# DS3_DECAY_C_RESCORE - T-SIGNAL-DECAY section C (forecast re-score) and section D (stack) - SD-C, 2026-10-30
Research only. No live, execution-server or chart change. UNTOUCHED never read (every frame capped at label day 20260206; own masks X'=20230401..20240131, PRE=20240201..20250630, HOLD=20250701..20260206, L6M=20250801..20260206, 2026=20260101..20260206, L3M=20251106..20260206 view-only, never used to choose). Prereg l2vast/ds3/prereg/SD_C_prereg.md sha256 4af72ff3871a3d263d13c1be0f44ad50454777f5ee729d653f988c72538591c6 (DECISIONS.md before any cell statistic; 93 cells, list sha b7a93f20...). Selection file out/decay/C/selection_SEL.json sha256 2f7305504300ca217e38c7a8aca9bcb487841299d01e9678958eb3691d66e858 (PRE+X' only, hashed before the single recent look). Amendment A1 (DECISIONS.md): the first stage-A pass resolved "stop to entry" on minute closes, which is optimistic (misses intra-minute touches of entry, so it keeps winners a real stop would cut); replaced by exact 1-s path resolution before any recent statistic; the first selection (sha c743e519...) was discarded.

## Verdict
**No re-scored-forecast exit improves any book. 0 PASS, 0 CANDIDATE-RECENT, 0 CANDIDATE among 93 cells x 13 scopes (1,209 cell-scope rows).** The PRE+X'-selected cell of every book is negative per contract in the last 6 months on N and M (ST is +0.17 on LIVE-P9 but -1.11 on N; CR never fires). White RC over the 93 cells: p 0.36-1.00 per scope (ENG6 0.99, ALL 0.99); Romano-Wolf stepdown on ENG6 and ALL: 0 survivors; PBO 0.0 (nothing is worth anything out of sample, so there is nothing to overfit); no selected cell beats the random-exit control at 0.95 (best: MV 0.81, PE 0.78, ST 0.56). The model does carry information (below); it is worth less than the cost of acting on it.

## What was built
* Panel: every in-trade minute-close row of the THP trees (dp1m + ldp1m), 6.72 M rows, 47,131 trades, 11 books; causal panel columns (path, regime, ATR, VWAP bands, swings, ST1/5/10, ES/RTY, stack, mbp-10 book/tape) + 29 engine-state columns from SD-A's sd_state (KB channel position/edge/inside/mid-lost; ST, ST-fast, SM, PE regime and distance; HMA a-b, slope, x vs VWAP; EMA200 side; 1m/5m/15m adverse-swing distance and CHoCH; signal-bar, 3m break-bar, 5m and PE pullback extreme lost). Bar-close causal; 99.9% of rows matched to a bar.
* Forecast model: LightGBM, depth <= 4 trees (the trees ARE AND-sets), pooled over books with a book code, refit every week (135 refits, 2023-07-10..2026-02-02) on rows of trades CLOSED before the refit with entry in the prior 91 days (<= 250k rows), two heads: (R) E[remaining pts to the bracket exit, N basis, after exit cost], (P) P(target before stop). Placebo twin: the same model on features permuted within book-week.
* Cells (93): R exit when pred_rem < -0.995-m (m 0/1/2/3); P exit when P(target) < 0.5/0.4/0.3; ages 0/5/15 min; always / under water / in profit; action market exit or tighten stop to entry (profit rows; resolved on the 1-s path); A (REPORTED VARIANT ONLY) add one lot when pred_rem > 2/4/6.
* Fills: market exit at the decision second +0.995 pt (M/N); stop-to-entry fills at -1.01 (LIVE-P9 2.45). Bases M, N (primary), LIVE-P9, LIVE-P9-T0. Per contract = mean over ALL trades of the scope (non-fired = 0); day-clustered SE; MDE = 2.8 SE.
* Machine note: the weekly refits ran at load 35-55 (other programs), 2.2 h.

## Result 1 - the PRE+X'-selected cell per scope, one recent look (pts per contract per trade vs hold-to-bracket, N basis unless stated)
| scope | selected cell (PRE+X') | elig | L6M N [CI day] | MDE | HOLD | PRE | X' | L3M (view) | 2026 | fire% L6M | per fired | P(tgt) fired vs all | LIVE-P9 L6M | M L6M | shuffled-feat | rank vs random | qtrs>0 | DSR |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ST | P/m=0.5/age=0/pr/exit | N | -1.11 [-3.088,0.858] | 2.94 | -1.18 | -0.93 | -1.26 | +1.44 | +1.89 | 46.3 | -2.41 | 0.52 vs 0.52 | +0.17 | -0.11 | -3.10 | 0.56 | 2/11 | 2e-10 |
| HM | P/m=0.5/age=15/pr/tighten | Y | -1.55 [-3.557,0.506] | 3.10 | -1.19 | +0.06 | +0.21 | -0.35 | -1.38 | 32.6 | -4.75 | 0.48 vs 0.52 | -1.18 | -0.89 | -1.77 | 0.02 | 4/11 | 2e-09 |
| WT | P/m=0.3/age=5/pr/tighten | N | -0.21 [-0.593,0.174] | 0.58 | -0.49 | +0.05 | -0.07 | +0.15 | -0.22 | 5.2 | -3.99 | 0.53 vs 0.59 | -0.14 | -0.09 | -1.46 | 0.14 | 4/11 | 7e-09 |
| KB | R/m=0/age=15/pr/tighten | N | -3.12 [-5.38,-1.239] | 3.03 | -2.88 | -0.85 | -0.24 | -0.46 | -2.96 | 31.5 | -9.91 | 0.55 vs 0.50 | -2.67 | -2.40 | -3.17 | 0.00 | 3/11 | 3e-17 |
| SM | P/m=0.4/age=15/pr/exit | N | -0.73 [-3.273,1.944] | 3.78 | -1.75 | -0.80 | -0.50 | -0.34 | -1.66 | 16.9 | -4.32 | 0.53 vs 0.51 | -0.27 | -0.35 | -2.27 | 0.40 | 3/11 | 3e-09 |
| PE | P/m=0.3/age=5/pr/tighten | N | -0.16 [-1.072,0.678] | 1.18 | -0.76 | -0.04 | -0.41 | +0.44 | +0.95 | 10.4 | -1.52 | 0.37 vs 0.49 | -0.09 | +0.00 | -3.42 | 0.78 | 5/11 | 6e-08 |
| ENG6 | P/m=0.3/age=15/pr/tighten | N | -0.43 [-1.073,0.132] | 0.83 | -0.68 | -0.33 | -0.33 | +0.26 | -0.27 | 8.4 | -5.15 | 0.41 vs 0.53 | -0.37 | -0.29 | -2.31 | 0.03 | 3/11 | 3e-14 |
| PB | R/m=1/age=15/uw/exit | N | -3.84 [-6.213,-1.562] | 3.21 | -3.72 | +0.09 | -0.30 | -3.43 | -1.78 | 39.8 | -9.64 | 0.43 vs 0.54 | -2.83 | -3.12 | -5.89 | 0.03 | 4/11 | 7e-16 |
| DN | R/m=1/age=15/uw/exit | N | -3.52 [-6.68,-0.606] | 4.20 | -3.06 | +0.04 | -0.12 | -2.49 | -6.03 | 40.8 | -8.64 | 0.42 vs 0.54 | -2.49 | -2.80 | -5.04 | 0.04 | 5/11 | 2e-11 |
| MV | P/m=0.4/age=15/pr/tighten | N | -0.18 [-1.695,1.192] | 2.07 | -0.20 | -0.16 | -0.71 | +0.14 | +0.41 | 17.9 | -0.99 | 0.42 vs 0.51 | -0.01 | +0.14 | -3.43 | 0.81 | 4/11 | 2e-08 |
| MA | P/m=0.4/age=15/pr/exit | N | -4.66 [-7.962,-1.913] | 4.16 | -5.02 | -0.89 | -0.42 | -3.55 | -4.95 | 24.8 | -18.77 | 0.64 vs 0.55 | -3.89 | -3.98 | -4.84 | 0.00 | 1/11 | 2e-17 |
| CR | P/m=0.3/age=0/any/exit | N | +0.00 [0.0,0.0] | 0.00 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 | 0.0 | +nan | nan vs 0.16 | +0.00 | +0.00 | +0.00 | n/a | 0/11 | nan |
| ALL | P/m=0.4/age=15/pr/tighten | N | -0.90 [-1.761,-0.066] | 1.23 | -1.03 | -0.45 | -0.73 | +0.15 | -0.59 | 16.2 | -5.56 | 0.47 vs 0.51 | -0.73 | -0.58 | -2.79 | 0.00 | 1/11 | 2e-17 |

"elig" = N and LIVE-P9 > 0 in PRE and in X' separately with >= 60 / 20 fires; only HM met it (and flips to -1.55 in L6M). The others are the highest min-t cell, labelled NOT-ELIGIBLE. shuffled-feat = the same cell and thresholds with features permuted within book-week (not fire-rate matched). rank vs random = share of 120 random-exit draws (same book fire rate, same time-since-entry distribution) below the cell in L6M; 0.95 required. L3M is a view column, never a selection input: ST +1.44 / PE +0.44 / ENG6 +0.26 over 13 weeks are inside MDE and were negative in HOLD and L6M ("L3M only").
Quarter drift (ENG6 selected cell, N), 2023Q2..2026Q1: -0.53, +0.67, -1.23, -0.69, -0.09, -0.20, -0.64, +0.01, -2.20, +0.11, -0.27 (3 of 11 positive). First vs second half of L6M: -1.50 / +0.27. By entry session (ENG6, L6M): asia -0.03, london +0.09, pre -0.61, NY-AM -0.76, NY-PM -1.03.

## Result 2 - the direct form: "exit when the re-scored forecast turns against the position"
Family R, m=0, age 0, always (exit at market whenever E[remaining] < the exit cost). L6M, N, per book; the saved/forfeited split is in dollars at one contract summed over the window; P(target | the forecast says exit but the trade is held) beside the all-trade rate:

| book | per contract (MDE) | fire rate | per fired | saved $ / forfeited $ | P(target) fired vs all |
|---|---|---|---|---|---|
| ST | -2.38 (3.67) | 64% | -3.72 | +402k / -462k | 0.51 vs 0.52 |
| HM | -4.18 (4.68) | 67% | -6.27 | +287k / -363k | 0.53 vs 0.52 |
| WT | -1.99 (1.69) | 58% | -3.41 | +309k / -377k | 0.60 vs 0.59 |
| KB | -3.10 (4.02) | 69% | -4.52 | +427k / -505k | 0.50 vs 0.50 |
| SM | -1.46 (7.15) | 63% | -2.31 | +99k / -108k | 0.49 vs 0.51 |
| PE | -2.77 (3.30) | 64% | -4.36 | +372k / -438k | 0.51 vs 0.49 |
| ENG6 | -2.69 (2.41) | 64% | -4.22 | +1896k / -2253k | 0.53 vs 0.53 |


The forecast says "exit" on 58-69% of trades, costs 1.5-4.2 pts per contract in L6M, and the trades it exits reach the target as often as those it keeps (0.49-0.60 vs 0.49-0.59): as a binary exit rule it has no timing information. Plain sentence: "when the re-scored forecast turns against ST, exiting at market costs 2.4 pts per contract on 64% of trades in the last 6 months (MDE 3.7); the trades it exits would have reached the target 51% of the time (52% for all)." The same cell restricted to trades under water or in profit, and the P(target) form, are in view_allcells.parquet.

## What information the forecast carries, and why it still loses
* P(target) head: Brier 0.2312 vs 0.2508 for the unconditional base rate (L6M, 1.15 M rows); decile calibration is monotone but over-confident at the ends (predicted 0.13 -> realised 0.22; 0.87 -> 0.77). The model knows something about how the trade ends.
* It does not know what happens next: rank IC of the forecast with the change in unrealised P&L over the next 1/5/15/60 min is -0.001/-0.004/-0.008/-0.005 (shuffled twin -0.001/-0.004/-0.008/-0.010); the day-clustered t of the daily IC is +3.2/+2.9/+2.5/+2.9 although the pooled IC is slightly negative (sign instability). The entry state is already priced in after the first minute; what the forecast knows is the trade's average outcome, which the hold arm earns anyway.
* The real model beats its shuffled twin by +1.5 to +3.3 pts in L6M (ENG6 -0.43 vs -2.31; ST -1.11 vs -3.10; PE -0.16 vs -3.42): the information is real. It loses to hold-to-bracket by 0.2-3 pts after the 0.995-pt exit cost and the winners it forfeits.
* Feature use (gain share, averaged by quarter): regime and stack columns dominate (prior-day range, VIX, ES-NQ correlation, number of other books open, stack day P&L), and the price level px appears from 2025Q1 (a non-stationary level feature: a model weakness, not a signal). Engine-state columns carry only 4-8% of the gain (8% in 2025Q4): the "would this book enter here now" part is small. Top-5 per quarter: out/decay/C/wf_importance.parquet.

## COMBOS addendum: depth-4 surrogate AND-sets (fit on PRE+X' rows only, applied recent)
A depth-4 tree is fitted to each selected cell's decision; leaves with P(fire) > 0.5 are the AND-sets; retained gain = rule delta vs model delta in L6M; best single member = the best one-condition rule chosen on PRE+X'.

| scope | model L6M | AND-set rule L6M | best single member L6M | AND-set vs best member |
|---|---|---|---|---|
| ENG6 | -0.43 (559 fires) | -0.09 (428) | -0.49 (776) [sess_now > 3.5] | rule better in L6M, PRE +0.10 vs member -0.06: not significant |
| ST | -1.11 | -1.06 | +0.04 (141) [mins_to_rel > 902] | the member alone beats the AND-set |
| HM | -1.55 | -1.44 | -1.44 | same as member |
| KB | -3.12 | -1.63 | -1.63 [stk_real_day_pts > 29.4] | same as member |
| SM | -0.73 | +0.77 (56 fires) | +0.67 (60) | +0.10 over the member, 56 trades, PRE -0.37: inside MDE |
| WT, PE | no firing leaf | - | - | - |

Readable examples: ENG6 "in profit (upnl > 0.125) AND session at or after NY-PM AND age > 15 min AND minute-of-day after 14:02 ET" (P(model fires) 0.50: late-day trades held in profit); ST "distance to target <= 1.0 R AND unrealised <= 0.35 R AND 5-m Supertrend distance <= 61"; HM "age > 15 AND stop distance <= 83.6 AND first-hour range available". Caveats: some thresholds are artefacts of the NaN fill (-999 -> "rg_fh_range > -491" means "available") and of the px level. No combination clears "beats its best member in both selection windows AND >= 0 recent AND placebo": 0 of 7.

## Add-on-strength (reported variant only)
Adding one lot when the forecast is strong (pred_rem > +2/+4/+6): per added lot, ENG6 L6M +0.68 (age 0) and +1.14 (age 15), but adding at the same age at EVERY trade earns +1.62 / +2.06 and a random add at the same rate +1.07 / +1.04; the signal-selected adds rank 0.02-0.03 against random in L6M and 0.00 in HOLD (worse than random). ST alone looks good (+2.3 per added lot in L6M) but ranks 0.29-0.50 against random: indistinguishable. The positive adds are the drift of an open position (STRUCTURE: more lots of a trade that on average still earns), not information. out/decay/C/add_variant.csv.

## Section D - combinations on the exact lock engine
6 engine books ST HM WT KB SM PE, l2set ls_engine.cell_daily. Dollars per week, delta vs hold-to-bracket BASE (L6M BASE +18.8k M / +61.5k N); MDE = 2.8 SE of the paired weekly difference. Components, all PRE+X'-selected: INV = SD-A (ST sel#107, KB sel#60; HM/SM/PE: no eligible cell, the headline premise rule is used; WT: SD-A has no WT state); DECAY = SD-B best group per book (G3 flat-line N10 k0.5 in profit for ST/WT/KB/PE, G1 session-end market for HM, G3 N20 under water for SM); RESC = this section's per-book selected cell. JOINT = the earliest exit of the components per trade. "exit-only" = the same exits with the book kept busy to its original exit time (no re-entry); re-entry P&L = stack delta minus exit-only.

| variant | basis | L6M (MDE) | HOLD | PRE | X' | re-entry P&L L6M | exit-only (no re-entry) L6M | extra trades kept |
|---|---|---|---|---|---|---|---|---|
| RESC_perbook | M | -18,831 (44,674) | -19,939 | -7,697 | -7,600 | +7,593 | -26,424 | 2137 |
| RESC_perbook | N | -26,926 (53,026) | -27,215 | -15,646 | -10,652 | +9,929 | -36,855 | 2262 |
| RESC_ENG6pooled | M | -8,652 (23,454) | -13,113 | -8,107 | -3,669 | +2,316 | -10,967 | 508 |
| RESC_ENG6pooled | N | -9,769 (23,806) | -14,728 | -11,088 | -4,898 | +2,331 | -12,100 | 544 |
| DECAY_bestperbook | M | -105 (22,606) | -1,634 | -1,190 | +1,715 | +2,383 | -2,488 | 457 |
| DECAY_bestperbook | N | -2,911 (25,046) | -4,646 | -4,138 | -788 | +2,623 | -5,534 | 491 |
| INV_bestperbook | M | -21,916 (33,573) | -20,892 | -16,527 | -4,651 | +1,728 | -23,643 | 2690 |
| INV_bestperbook | N | -27,242 (34,955) | -26,094 | -22,407 | -8,725 | +3,374 | -30,616 | 2790 |
| JOINT_INV+DECAY+RESC | M | -39,182 (49,615) | -38,319 | -23,010 | -14,297 | +6,627 | -45,809 | 4281 |
| JOINT_INV+DECAY+RESC | N | -52,159 (55,383) | -50,482 | -32,717 | -19,624 | +8,772 | -60,931 | 4472 |
| JOINT_DECAY+RESC | M | -20,122 (45,098) | -21,395 | -12,301 | -9,451 | +8,913 | -29,036 | 2394 |
| JOINT_DECAY+RESC | N | -31,053 (53,707) | -31,444 | -19,950 | -13,639 | +10,418 | -41,470 | 2543 |
| LIVE_PATH_TH_JADE | M | -11,105 (52,663) | -7,296 | -34,528 | -3,427 | +15,519 | -26,624 | 6075 |
| LIVE_PATH_TH_JADE | N | -46,562 (58,932) | -40,614 | -58,964 | -12,306 | +15,474 | -62,035 | 6425 |
| L2HEALTH_loss_PRE | M | -239 (32,664) | -4,331 | +8,534 | +2,232 | -1,246 | +1,006 | 2470 |
| L2HEALTH_loss_PRE | N | +5,873 (39,243) | +3,745 | +9,163 | +1,518 | -521 | +6,394 | 2533 |
| L2HEALTH_p70_take | M | +29,613 (46,673) | +30,017 | -4,139 | +4,466 | +18,696 | +10,916 | 2351 |
| L2HEALTH_p70_take | N | -8,976 (49,986) | -6,147 | -31,698 | -6,148 | +19,813 | -28,789 | 2752 |
| L2HEALTH_loss+p70 | M | +26,052 (57,979) | +22,300 | +5,009 | +10,225 | +20,986 | +5,066 | 4271 |
| L2HEALTH_loss+p70 | N | -15,387 (62,094) | -16,375 | -23,346 | -502 | +19,994 | -35,380 | 4667 |


Reading. (1) Hold-to-bracket beats every combination of invalidation + decay + re-score on M and N in L6M, HOLD and PRE (JOINT -39k M / -52k N per week in L6M; MDE ~50k, so each is inside noise, but the sign is the same in all windows). (2) The live path TH rule (JADE) and the decay cells lose on N; the L2 health rules (loss PRE cells + REF p70 take) are +26k M (p70 take alone +29.6k, reproducing the earlier L2SET profit-stack number) but -15k N: they live on the target-fill correction (STRUCTURE / basis), as the earlier programs found. (3) Re-entry: an early exit frees the book and the engine admits 500-4,500 extra trades; the re-entry P&L is positive (+2k..+21k per week in L6M) but never covers the exit loss itself. (4) Weekly correlation of the delta with the base stack, L6M: RESC -0.59, DECAY -0.38, INV -0.61, JOINT -0.75, JADE -0.81: the exits cut exactly the big winning weeks. (5) EQR frame (STRUCTURE only; worst-20-week sum matched to BASE): see EQR_scale / EQR_L6M_mean_vs_base in stack_D.csv; scale factors 0.2-0.9 on N, still below BASE.

## Quant-layer items (selected rows; nothing is CANDIDATE-RECENT, so the layer is run on the PRE-selected rows)
Done: White RC and Romano-Wolf (ENG6, ALL), PBO, DSR (1e-7..1e-17 at 147,739 trials: negative Sharpe), day- and week-block bootstrap CI per window (extra.json), 120-draw random-exit rank, shuffled-feature twin, neighbour mean (ENG6 -0.67, HM -1.21, PE -0.27, ST -0.89 vs selected -0.43/-1.55/-0.16/-1.11), bases side by side, breakeven cost (negative: no cost level makes it pay), top-5% share (n/a, gain negative), stack correlation, quarter sign count, session slice, calibration and Brier, IC by horizon (minute resolution), depth-4 distillation, capacity (median size at the touch on the exit side 2-3 contracts, 10th percentile 1, liquidity within 4 ticks 16-32 contracts: a 1-lot exit is fine, a 10-lot exit walks the book). NOT done: 1-s/3-s latency re-evaluation, purged / combinatorial-purged CV (the walk-forward with a 3-month closed-trade window is the only validation), anchored/rolling 6- and 12-month windows, 60-s time-shifted-feature placebo, shuffled-day-market placebo, Newey-West. For rules that lose by 1-3 pts these cannot flip the sign.

## Records
UF_TRIALS.json appended (side="decay", SD-C: 93 x 13 = 1,209 cell-scope rows, n_effective ~1.5 per scope). 1,209 rows appended to DEAD_CELLS.csv (program SDC_RESCORE). RECENT_WINS: 270 cell-scope rows positive in L3M written to out/recent_wins/sd_c.csv (none positive in both L6M and HOLD except the add variant, which is STRUCTURE). Questions for the user: none.

## Files
l2vast/ds3/out/decay/C/: panel.parquet, state_feats.parquet, wf_preds.parquet, wf_importance.parquet, cellsA.parquet (PRE+X' only), selection_SEL.json, stageB_selected.csv, view_allcells.parquet, extra.json, rules.json, add_variant.csv, stack_D.csv, headline_exit_by_book.csv, header_extra.json. Code l2vast/ds3/code/decay/sdc_*.py.
