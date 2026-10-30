# DS3_BASIS_LIVE - best cell of every closed program on M / N / LIVE-P9 (T-MISSED 1b). All numbers: recomputed, no new look.
Prereg: l2vast/ds3/out/basis_live/PREREG_BASIS_LIVE.md sha256 2349c3d73f97a0e881c57f2695987c806732321ba3f20e45f1a8cce7bacb7f3b (logged in DECISIONS.md before any statistic). Masks own, capped 20260206 (2026=0101..0206, L6M=20250801.., HOLD=20250701.., PRE, X'); WINMASK/vs_lib.WINS unused. No file under data/live and no post-2026-02-06 1-s data was opened.

## Basis LIVE-P9: provenance and its own uncertainty
* M = programs' measured basis (stop 1.01, market 0.995, limit-target correction 1.4/1.5/4.2/4.3 pt for 2023-26). N = M without the target correction.
* LIVE-P9 = M with every stop-class exit charged 2.45 pt worse than nominal (instead of 1.01), target correction kept. LIVE-P9-T0 = same without the target correction (live filled targets sit at nominal, +0.01 pt, n=17, LIVE_RECON DS3 table). LIVE-P9-LO = stop exits +0.68 better (sensitivity).
* Source of 2.45: LIVE_RECON.md, 10-20..23, n=21 stop exits (StopJoin n=8 +0.52 better; StopJoinFallback n=12 -4.46; Rejected n=1 -2.11); SE ~0.75; pre-join-fix. The 10-26..29 files (n=26, +0.68 better) are computed by live_vs_replay_p9.py against a hard-coded 60-pt stop level, not each trade's real stop, so they are not comparable; unresolved from text. Market-class exits (cuts, time, policy) kept at M: no live number published. NOT published at all: fill rate of targets the path touched (so the true target correction live is unknown; that is the M-vs-N question part (a) answers).
* Consequence: the stop cost (LIVE vs M) moves early-exit/cut rules by +0.1..+0.6 pt (stop avoided costs more) and never decides a sign alone; the target correction (M vs N, 1-2 pt on profit-take rules) decides every sign flip below.

## TABLE (pts/trade unless $k/wk; cells M / N / LIVE-P9 / LIVE-P9-T0; HOLD value after the slash; MDE = 2.8 SE)
| Program | Best cell | L6M (n, MDE) | HOLD | Sign depends on basis? |
|---|---|---|---|---|
| L2SET entry ($k/wk) | pooled 70/30 split, dip 3 pt (PRE-selected) | +13.3 / +17.6 / +15.2 / +15.1 (MDE 14.5) | +11.6 / +18.4 / +13.0 / +16.0 (14.0) | No; ~at MDE |
| L2SET joint ($k/wk) | E+P+L PRE-selected | +25.8 / -14.6 / +30.7 / -10.1 (56.3) | +20.5 / -17.2 / +24.2 / -13.9 | YES (target corr via profit leg) |
| L2SET profit stack ($k/wk) | plain 70% take | +29.6 / -9.0 / +31.2 / -7.6 (46.7) | +30.0 / -6.1 / +31.4 / -5.1 | YES |
| L2SET profit | REF take-at-70% pooled | +0.86 / -1.25 / +0.95 / -1.16 (n 9743, 1.08) | +0.94 / -1.13 / +1.03 / -1.04 | YES: +0.86 M vs -1.25 N; LIVE-P9 +0.95 only if the target correction is real live |
| L2SET profit | PRE-selected pooled cell | -0.05 / -0.13 / -0.08 / -0.16 (0.39) | -0.06 / -0.14 / -0.09 / -0.17 | No, negative |
| L2SET loss | PRE-selected A15 cut | -0.30 / -0.61 / -0.05 / -0.36 (1.15) | -0.32 / -0.60 / -0.08 / -0.37 | No, negative |
| L2SET loss | rank-1 looked (A15 z2@5s imb cut) | +0.34 / +0.26 / +0.44 / +0.36 (0.58) | +0.30 / +0.23 / +0.39 / +0.32 | No; looked data, fails stack gates |
| L2ENTRY A | skipTop3_rnd100_ahead (pts/signal) | +0.79 / +0.76 / +0.82 / +0.79 (1.06) | +0.68 / +0.65 / +0.70 / +0.67 | No; stack line -9.9k L6M on M (not rerun) |
| L2ENTRY B | B2_r20_R100 ES London 60/60 (looked, n 31) | +17.86 / +20.72 / +17.39 / +20.26 (27.9) | +21.18 / +24.17 / +20.76 / +23.74 | No; PRE negative |
| DIPENTRY ($k/wk) | rank-1 A1_timer X10 T1800 (looked) | +26.7 / +3.7 / +26.9 / +3.9 (41.7) | +28.5 / +6.8 / +28.7 / +7.0 (38.3) | magnitude (85% is target corr), sign no |
| DIPENTRY | D6-LIVE cell | -57.1 / -111.6 / -51.3 / -105.8 (95.4) | -35.9 / -87.5 / -30.1 / -81.8 | No, negative |
| THP B | F10_m40_r3_t4 (best PRE) | -0.06 / -1.40 / -0.01 / -1.35 (n 6856, 1.49) | +0.03 / -1.28 / +0.08 / -1.23 | zero within MDE |
| THP B | F10_m20_r3_t8 (live JADE) | -0.89 / -2.66 / -0.97 / -2.74 (2.66) | -0.64 / -2.38 / -0.72 / -2.47 | No |
| THP C1 | profit logit 3m tighten | -0.31 / -2.04 / -0.09 / -1.82 (2.23) | +0.04 / -1.69 / +0.28 / -1.44 | HOLD only |
| THP C1 | loss meta GBM 12m | -0.75 / -2.05 / -0.33 / -1.63 (1.48) | -0.51 / -1.81 / -0.09 / -1.38 | No |
| THP C2 | profit qr 6m regime | +0.21 / -0.78 / +0.28 / -0.71 (n 9573, 0.95) | +0.44 / -0.55 / +0.51 / -0.47 | YES |
| THP C2 | loss haz 6m | -0.31 / -0.46 / -0.25 / -0.41 (0.85) | -0.05 / -0.24 / +0.02 / -0.16 | HOLD ~0 |
| THP C3 | profit btab m2 (best PRE) | -0.31 / -0.52 / -0.29 / -0.50 (0.66) | -0.36 / -0.66 / -0.33 / -0.62 | No |
| THP C3 | profit hmm K3 (looked) | +0.30 / -1.13 / +0.51 / -0.92 (1.78) | +0.44 / -0.94 / +0.65 / -0.73 | YES |
| THP C3 | loss ogbm m8 | -1.10 / -1.55 / -0.84 / -1.30 (1.27) | -0.73 / -1.19 / -0.46 / -0.92 | No |
| THL B | L2_x10_t60 pooled cut | -0.65 / -0.90 / -0.55 / -0.80 (1.29) | -0.40 / -0.65 / -0.29 / -0.54 | No |
| THL B | HM L6_a30_r3_w10 (seen-data lead, n 618) | +1.88 / +1.69 / +2.12 / +1.92 (2.98) | +1.82 / +1.64 / +2.05 / +1.87 | No, positive all bases; lead only |
| THL B | L6_a15_r3_w30 live loss rule | -1.58 / -2.40 / -1.29 / -2.12 (2.49) | -1.13 / -1.92 / -0.84 / -1.63 | No |
| THL2 L2H | H7P pct0.7 take (= plain 70%) | +0.90 / -1.20 / +0.99 / -1.12 (1.02) | +0.99 / -1.08 / +1.07 / -1.00 | YES, clearest flip |
| THL2 L2L | loss A30 k3 medlvl (live) | -1.41 / -1.97 / -0.79 / -1.35 (1.77) | -1.04 / -1.59 / -0.43 / -0.97 | No |
| THL2 L2L | profit B20 r1.5 d8 W15 (live) | -0.50 / -0.90 / -0.65 / -1.05 (0.88) | -0.43 / -0.86 / -0.60 / -1.03 | No |
| THL2 L2P | P 3m haz d0.05 (rank-1 looked, fires 1.5%) | +0.12 / +0.09 / +0.13 / +0.10 (0.28) | +0.13 / +0.09 / +0.14 / +0.10 | No, positive all bases, tiny |
| ABR B | fixed abs120 OR none, gain vs 60/60 | +3.95 / +2.76 / +3.90 / +2.71 (n 10252, 10.4) | +3.17 / +1.94 / +3.15 / +1.92 (9.7) | No |
| ABR C1 | gbm EV 12m 1m 0 rp m1 (only CANDIDATE) | +3.17 / +2.11 / +3.01 / +1.95 (4.6) | +2.53 / +1.48 / +2.39 / +1.33 (4.3) | No (PRE +0.56 M, -0.06 N) |
| ABR C2 | session table ew5 weekly (best PRE) | +0.56 / -0.81 / +0.51 / -0.85 (9.6) | +0.57 / -0.73 / +0.54 / -0.75 (8.7) | YES |
| EXP1 | profit chain tighten 6m m0.5 | +0.22 / -0.70 / +0.36 / -0.55 (1.30) | +0.41 / -0.48 / +0.56 / -0.33 (1.22) | YES (if tighten treated stop-class: -0.12 / +0.08) |
| EXP2 | session table by book U3 3m | +0.11 / +0.08 / +0.11 / +0.08 (0.52) | +0.13 / +0.09 / +0.13 / +0.10 (0.47) | No, below MDE |
| CUTWAIT ($/wk) | HM x30 N10 any | not stored | -5,775 M / -2,418 N / ~-3,300 LIVE (approx, lock engine not rerun) | negative HOLD all bases |
| ADDUW ($/wk) | STACK #5 (50% + add at -5) | B2 +6,772 / B1 +4,834 / B0 -14,986 (MDE 18.1k) | +5,924 / +5,020 / -14,235 (16.0k) | YES (LIVE-P9 not computed; B1 includes a stop credit) |
| SIZING REGIME ($k/wk, lot-matched) | B2_STACK 8-wk | +10.5 / = / +9.6 / = (MDE 8.1) | +8.8 / +7.8 (11.8) | No; leverage, DEAD on tail gates |
| SIZING VOLSCALE ($k/wk) | S_V8 8-wk | +9.4 / +8.3 (8.3) | +7.6 / +6.6 (11.0) | No; DEAD |
| SIZING RECENT ($k/wk) | D6 V5 SH6 | -4.3 / -3.3 (37.1) | +1.2 / +2.2 (33.5) | not material |
| STACK F ($k/wk delta) | A06+HM5R+B02 | -12.2 / -9.4 (38.8) | -10.3 / -7.5 (34.7) | No, negative |
| STACK E-corrected ($k/wk) | HM5te REPL, HOLD only | NA | +11.4 D-replay / +3.6 M-mapped / +11.4 LIVE (22.2) | depends on report basis (D vs M), not exit cost |
Not rows (data builds, no cell): THP A, THL A, ABR A. THPC1/C2/C3 = THP C1-C3. For stack-level rows N = M (stored stack basis carries no target correction) and LIVE adjustment is first-order (not a lock re-run). Rows labelled EXPLICITLY looked-data are selected on looked windows.

## Re-labelled: >=0 on LIVE-P9 in both L6M and HOLD (every one is NOT a pass)
* Sign set by the target correction (negative on N / LIVE-P9-T0): take-at-70% (REF, L2H H7P, L2SET profit stack, joint), THP C2 profit qr, THP C3 hmm, ABR C2, EXP1, ADDUW (vs B0).
* Positive on every basis but weak: L2SET entry split (+15.2k L6M, MDE 14.5k, ~1 MDE; CANDIDATE-RECENT, fails placebo/RC), L2ENTRY A skipTop3 (pts/signal, stack line negative), L2ENTRY B / DIPENTRY rank-1 (looked, PRE negative / 85% target corr), THL B HM lead (1 book of 22), L2P haz (1.5% fires), L2SET loss rank-1 (looked, fails stack gates), ABR B / C1 (gain vs 60/60 on its oracle/model; C1 PRE is basis-dependent), EXP2 (+0.1, below MDE 0.5).
* Plain statement of basis dependence: take-at-70% is +0.86 (M) / +0.95 (LIVE-P9) vs -1.25 (N) / -1.16 (LIVE-P9-T0). Which side is true is decided by whether live limit targets are filled when the path touches them, which published text does not give (only 17 filled targets, at nominal).

## Part (a): HELD
Script ready: l2vast/ds3/code/basis_live/live_exit_cal.py (exit classes TARGET/STOP/STOP_FB/STOP_REJ/LOSSCUT/PROFITEXIT/LOCK/FLATTEN/TIME; fill vs 1-s path price at the exit second (last, bid/ask, mid); OLS on stop distance and qty; per-year means; M/N/CONS closest-basis with z and n; target touch-vs-fill rate). Self test (synthetic exits on the 2025-09 path, injected costs recovered exactly at zero noise, within 0.2 at sd 1; classification and guard checks) PASS. It refuses any path under data/live without the confirmation string.
Exact confirmation needed (from MORNING.md): "read live exit fills from 2026-10-28 for cost calibration only (fill price vs path price at the exit second; no strategy scoring, no P&L by cell)". Note the live files also contain 10-20..10-27 trades, also inside the sealed span; the confirmation should say from 2026-10-20 if those are wanted (n=21 stops are from 10-20..23). Run: python3 live_exit_cal.py <live csv> --confirm-sealed-read "read live exit fills from 2026-10-28 for cost calibration only".

## ADDENDUM 2026-10-30: part (a) RUN (user confirmation in DIRECTIVE_L2_UNTIL_FOUND_20261030.md: "read live exit fills from 2026-10-20 for cost calibration only"). Details: LIVE_CAL_SUMMARY.md
Findings: (1) the 2.45-pt figure is reproduced and is the correct one; the +0.68 pools 21 true 60-pt stops (-2.45) with 5 WT_Stop exits against a wrong hard-coded 60-pt level (+13.86 each); (2) stop cost vs nominal matches CONS (2.02) better than M (1.01); against the path price at the exit second, fallbacks are +0.86 (matches M) and joins -0.80: the extra cost is delay; (3) touched targets: 11/11 filled (10 through by >2 ticks, none marginal); consistent with N, M-vs-N for marginal touches undecided; (4) LossExit +0.80 (n=14) matches M.
LIVE-CAL basis = stop 2.45, market M, target correction 0 (point; M's correction as stress) = the LIVE-P9-T0 column of the table above (already recomputed with the exit-cost component only; no new recompute needed). Rows that CHANGE SIGN between LIVE-P9/M and LIVE-CAL (L6M and HOLD, + to -): take-at-70% REF (+0.95/+1.03 -> -1.16/-1.04), THL2 L2H H7P (+0.99/+1.07 -> -1.12/-1.00), L2SET profit stack (+31.2k/+31.4k -> -7.6k/-5.1k), L2SET joint (+30.7k/+24.2k -> -10.1k/-13.9k), L2SET profit rank-1 (+1.11/+1.14 -> -1.00/-0.94), THP C2 profit qr (+0.28/+0.51 -> -0.71/-0.47), THP C3 hmm (+0.51/+0.65 -> -0.92/-0.73), ABR C2 (+0.51/+0.54 -> -0.85/-0.75), EXP1 (+0.36/+0.56 -> -0.55/-0.33), DIPENTRY rank-1 stays positive but 85% smaller (+3.9k/+7.0k, MDE 41.7k/38.3k), ADDUW (B2 positive, T0 not computed). Rows positive on LIVE-CAL in both windows, none a PASS: L2SET entry split (+15.1k/+16.0k, MDE 14.5k/14.0k), L2ENTRY A skipTop3 (+0.79/+0.67 per signal), L2ENTRY B cells (looked), THL B HM lead (+1.92/+1.87), L2P haz (+0.10), L2SET loss rank-1 (+0.36/+0.32, looked), ABR B (+2.71/+1.92), ABR C1 (+1.95/+1.33), EXP2 (+0.08/+0.10, below MDE). Everything else negative. Caveat: the target-correction side rests on 11 touched targets, none marginal; if M's correction is real the take-at-70% family stays positive.
