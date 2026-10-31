# DS3_SPLIT_2 - THE SPLIT, SECOND PASS (PLAN36 section 6; agent SP2; 2026-10-30T23:52Z)

Research only; no live/execution/chart change; UNTOUCHED (label day > 2026-02-06) never read. Prereg `l2vast/ds3/prereg/SPLIT2_prereg.md` sha256 49438b28457fb8871f37c7734b280a86f85ffda23f1838d086114afbc3521b5f (in DECISIONS.md before any SPLIT-2 cell statistic); PRE u X' selection files (hashed in DECISIONS.md before each group's one recent look): `ga_selection_PRE_X.json`, `gd_selection_PRE_X.json`, `ge_selection_PRE_X.json`. Code `l2vast/ds3/code/split2/` (s2k.py kernel, s2lib.py, ga*/gb/gc/gd*/ge_* drivers, rep_*.py, rc_prog*.py, qh*.py, build_*.py), outputs `l2vast/ds3/out/split2/`. Engine: exact lock engine (sl_lib.run_book), six books ST HM WT KB SM PE at research lots ST10 HM10 WT7 KB5.2 SM7.4 PE5.6; own masks capped at 20260206 (L3M 20251106.., L6M 20250801.., HOLD 20250701.., PRE 20240201..20250630, X' 20230401..20240131; 2026 = 20260101..20260206 = 5 weeks, a sign not a size; 'worst-20' over a window with fewer than 20 weeks is the sum of all its weeks). **Kernel validation:** the pooled 70/30@3 cell reproduces lj_kernel.jrun on 44,360 of 44,370 trades and the published stack deltas (+19.5k/+13.3k/+11.6k/+7.6k/+2.8k on M; LIVE-CAL L6M +15.1k); the first-stop + sizer composition reproduces SP-1 exactly (MKT cutRest50: L3M +35.7k, L6M +23.0k, HOLD +19.3k, PRE -8.2k; S73 cutRest50 +16.0k/+6.6k/+4.6k/-6.4k).
Bases: **N** = no target correction (primary; profit-type results must be >= 0 on N), **LC (LIVE-CAL)** = N + stop-class exits 2.45 pt worse than nominal (p_fallback 0.57), **LJ (LIVE-JOIN)** = N + stop-class exits 0.5 pt (stop-join fix assumed), M beside where stated (BASIS definitions as in LIVE_CAL_SUMMARY.md / DS3_BASIS_LIVE.md; no BASIS_DEF.md file exists on disk). $/wk = lock-engine stack at research lots; **at D6 live lots divide by 2.35** (SP-1 mapping; unconfirmed, question in MORNING). MDE = 2.8 x SE of the paired weekly delta, in parentheses. Units on every row: per planned lot, per contract of final lots, lock-engine stack; STRUCTURE = the variant changes lots and must beat its lot-factor-matched uniform scaling line and the random-dip placebo (the mean final lots of every split cell here is 0.997-0.999 per planned lot, so the lot-matched line is the market stack itself; the real test is the placebo).

## 0. Page-1 verdict (plain)
* **A null on every question the section asked of the split, plus two useful measurements.** Nothing in this pass beats the plain 70/30-at-3 split (S73) by more than its MDE, and nothing passes. 296 prereg cells (A 90 trade cells + 8 stack policies, B 48, C 18, D 105, E 27 lines x 3 bases). Program-level White reality check over the 179 stack-level cells *vs the S73 split*: p = 0.93 (PRE u X'), 0.77 (L6M), 0.81 (HOLD), 0 Romano-Wolf survivors. *Vs the market stack* the split family is significant inside the program (studentised p 0.043 PRE u X', 0.002 L6M, 0.003 HOLD; 28 RW survivors in L6M) - that is the already-known split gain, not new; adjusted for the cumulative cell count (2,467,648 cells in UF_TRIALS.json) the p is 1.00.
* **(a) Add size by session / ER state: no gain.** Eight add-fraction policies (A4 = the directive: 50% add in Asia, 30% elsewhere; PRE u X'-selected F by session, by ER state, by session x ER; ER-conditioned 50% / 10% adds; uniform 10% add) are inside the MDE of uniform 70/30 (L6M vs A0: A1 +0.3k, A2 +2.1k, A3 -1.7k, A4 +2.8k, A5 +1.8k, A6 -3.2k, A7 -5.6k; MDE 5-14k), and the two that look best in L6M are PRE-negative (A4 -3.3k (6.6k), A2 -4.4k (7.1k)). The per-session F tables change sign between PRE and L6M. The PRE u X'-selected F by session (more add, F 0.5, in London / NY) earns *less* than uniform 0.7 on the stack in PRE u X' itself (2.7k vs 3.2k per week): the trade-level argmax does not carry to the lock engine. 30% in NY and 50% in Asia (A4) is +2.8k L6M / +2.5k HOLD / -3.3k PRE / +0.5k X' vs uniform: noise.
* **(b) Limit at (signal - X) placed at arming vs market at the touch: market wins.** At 70/30-at-3 the gated market add makes +17.6k L6M; the same dip as a resting limit placed at arming makes +7.3k (touch fill, the optimistic convention), +7.6k (+1 tick through) and +7.2k (+2 ticks through, the regime the live-cal measured: 11/11 touched targets filled when traded through by > 2 ticks) = -10.3k / -10.0k / -10.4k vs the gated market (MDE 9-10k) and -3.5k / -3.2k / -3.5k vs the ungated market. The limit fills 1-2 points more often (94% vs 92-93%) but at an average **0.72 pt worse price** than the market fill of the same trade: the market add waits for a 1-s close X pt away and gets the continuation, the limit fills on every wick including those that bounce, at exactly the level, and gives up the gate. At 90/10-at-8 limit and market are equal (+17.9k vs +17.1k L6M). Section 3.
* **(c) 90/10-at-8 vs 70/30-at-3 on the live-cal basis: equal at the measured cost; 90/10 is the cost-robust cell; the stop-join fix does not matter for the choice.** Paired C90 minus C70 (N, 2.45 stop): L6M +2.0k (12.5k), HOLD +0.2k (11.5k), PRE -0.9k (8.8k), X' +5.0k (8.6k); at the 0.5 stop: L6M +0.4k (13.6k), HOLD -1.8k (12.5k), PRE -0.8k (9.4k), X' +6.8k (9.3k) - all inside MDE. The stop cost moves either cell by < 3k/wk (stack delta vs market at 0.5 / 2.45: C70 L6M +14.4k / +15.1k, C90 +14.8k / +17.1k): the join fix changes no sign and no ranking. What separates them is the remainder fill cost: at +1 pt per remainder lot-fill C70 falls to +6.1k / +8.6k L6M (PRE -1.9k / -1.6k) and at +2 pt to +1.5k / +3.9k (PRE -7.8k / -7.6k) while C90 keeps +13.3k / +14.9k and +11.7k / +10.6k (PRE +1.6k / -0.0k and -0.2k / -2.1k) at the 0.5 / 2.45 stop. Breakeven remainder cost (N): L6M C70 about 2.3 pt, C90 above 2 pt (not reached); in PRE C70 about 0.6 pt and C90 about 1 pt. This is the UFE1 cell (in DEAD_CELLS: flat vs the split at +0 pt); what is new is that the stop-join assumption leaves it unchanged. Both beat the random-dip placebo (adds at random seconds, same time-since-entry distribution, 100 draws) at rank 1.00 in L3M/L6M/HOLD/PRE/X' (2026 0.98 / 0.94). Section 4.
* **(d) Split on the confirmation base: dead.** 35 confirmation definitions (FVG / iFVG / iplFVG / OB / BRK x 15 s ... 5 min; the 15/30/45-s ones are the CF-SUBMIN sub-minute timeframes) x 3 variants (70% at the confirmation print + 30% on the 3-pt dip after it with / without the gate; pure wait). Pooled PRE u X' excess over the lot-matched market: D1 -0.15, D2 -0.15, D3 -0.10 per planned lot vs +0.03 for the signal-anchored split. The 8 PRE u X'-selected cells are -4.8k .. -35.4k vs the market stack in L6M and negative vs S73 in every window; they are positive only in L3M for 2 (FVG-15s pure wait +2.1k, OB-45s +7.5k) and in 2026 (5 weeks) for 6 of 8. Per planned lot the confirmation cells look fine (FVG-15s pure wait +2.50 vs market 2.39 in L6M) because they skip 7-54% of the signals, which lose -9 .. -31 pts each; on the lock engine the skipped trades and the later fills cost dollars (the CF-B / FZ-1 unit lesson again). Time-matched random events beat the real events in L6M in 6 of 8 cells (the real event beats its random-timing mean in 2 of 8 in L6M, 5 of 8 in PRE = the selection window): no information shown. Section 5.
* **(e) The three together (split + first-stop cut50 + ER sizer) on the lock-engine stack: not additive as lots, additive-ish as risk.** Unscaled (N, L6M, vs the stack as it is): first-stop cut50 adds +23.0k, the ER sizer (lots x0.5 below 5-min ER(20) 0.3, x1.0 above; the sizer takes 30% of the lots off: lot factor 0.70) +16.1k, together +15.5k (additive would be +39k); with 90/10-at-8 underneath +23.7k, +20.9k, together +17.2k. The prereg headline S* (C90) + cut50 + ER 0.5/1.0 is **+17.2k (43.9k) L6M, +16.1k (40.0k) HOLD, +44.0k (56.1k) L3M, -14.9k (23.0k) PRE, -0.8k (23.7k) X'** vs the stack as it is at 0.70 of its lots, weekly SD 146k -> 113k, maxDD 372k -> 448k and worst-20 -153k -> 513k in L6M. **At equal risk (lots scaled by one factor c* so the WF worst-20 weeks equal the stack as it is; c* = 1.39; STRUCTURE-labelled, leverage) the same line is +48.2k (47.8k) L6M, +41.5k (43.6k) HOLD, +65.7k (71.4k) L3M, +2.2k (26.7k) PRE, +5.2k (27.0k) X'** (S73 + cut50 + ER: +41.9k (46.7k) / +36.3k (43.0k) / +53.3k (70.9k) / +3.6k (26.7k) / +1.1k (27.0k); 90/10 alone: +24.4k (15.1k) / +21.7k (17.0k) / +19.9k (23.2k) / +8.9k (10.6k) / +10.7k (9.5k); S73 alone +22.6k / +22.6k / +22.2k / +7.7k / +3.3k = the EQR A|H|E|N row); matched on weekly SD instead of worst-20 the headline is +34.4k / +30.2k / +56.0k / -5.4k / +2.5k. So the combination beats the split alone by about +24k L6M / +20k HOLD at equal risk (positive in all five windows on N, LIVE-CAL and LIVE-JOIN) but is inside its MDE except in L6M (PRE/X' MDE 27k; the MDE is as large as the effect) and the equal-risk factor 1.39 is itself a noisy estimate (EQR: factor CIs +-20-30%, equal risk does not transfer out of sample). Components overlap (both de-risk after a loss / in chop) but at equal risk they add partially: cut50 alone +27.3k, sizer alone +33.7k, both +41.9k..+48.2k L6M. The ER information is real inside the composition (shuffled-ER placebo, 40 draws: sizer alone rank 1.00 L6M / HOLD, 0.97 PRE; the sizer on top of C90 + cut50 rank 1.00 L6M / HOLD / PRE) and vs the lot-matched line (market x 0.70) the sizer is positive in all five windows (+41.8k / +35.0k / +30.6k / +6.2k / +4.2k). Section 6 has the Sunday stack line.
* Tiers (V2 gates, none softened): split S73 CANDIDATE-RECENT (unchanged: random-dip placebo rank 1.00, WF block-bootstrap CI of the weekly delta [+2.0k, +14.8k], 12 of 12 quarters positive; fails cumulative RC, DSR 0.04, CI(PRE) includes 0 in the L2SE run); C90 CANDIDATE-RECENT as a rule vs market and BEST-AVAILABLE-NEGATIVE as an improvement over S73 at +0 pt (use it only if the remainder fill cost is believed to exceed ~+0.5 pt); session / ER add-size policies DEAD; limit-at-arming BEST-AVAILABLE-NEGATIVE; confirmation-base split DEAD; first-stop cut50 and ER sizer CANDIDATE-RECENT in their own programs; the three together CANDIDATE-RECENT at equal risk only (STRUCTURE-labelled leverage; unscaled PRE negative -15k; fails cumulative RC; PRE/X' inside MDE). Selection post-hoc status: the A4/A5 policies are the directive's own (pre-specified, not selected); A1-A3, S* and the D picks are PRE u X' selected (honest); no row here is post-hoc selected on L6M/HOLD.

## 1. The base being tested
| cell | window | pts per planned lot (N) | pts per contract of final lots (N) | final lots per planned lot | engine-book signals / wk | add fill rate | per-contract delta vs market |
|--|--|--|--|--|--|--|--|
| market at signal (stack as it is) | L3M | 0.56 | 0.56 | 1.000 | 270 | - | - |
|  | L6M | 2.39 | 2.39 | 1.000 | 237 | - | - |
|  | HOLD | 1.90 | 1.90 | 1.000 | 229 | - | - |
|  | PRE | 1.48 | 1.48 | 1.000 | 222 | - | - |
|  | X' | 0.70 | 0.70 | 1.000 | 133 | - | - |
| 70/30 split, dip 3, 1-of-8 gate, veto v4 (S73) | L3M | 0.46 | 0.46 | 1.000 | 270 | 0.92 | -0.11 |
|  | L6M | 2.46 | 2.46 | 0.999 | 237 | 0.92 | +0.07 |
|  | HOLD | 2.01 | 2.01 | 0.999 | 229 | 0.92 | +0.11 |
|  | PRE | 1.54 | 1.55 | 0.997 | 222 | 0.92 | +0.07 |
|  | X' | 0.59 | 0.60 | 0.992 | 133 | 0.91 | -0.10 |
| 90/10 split, dip 8, no gate, veto v4 (C90) | L3M | 0.53 | 0.53 | 1.000 | 270 | 0.84 | -0.03 |
|  | L6M | 2.39 | 2.39 | 0.999 | 237 | 0.83 | +0.00 |
|  | HOLD | 1.91 | 1.91 | 0.998 | 229 | 0.83 | +0.01 |
|  | PRE | 1.48 | 1.48 | 0.998 | 222 | 0.82 | +0.01 |
|  | X' | 0.63 | 0.63 | 0.991 | 133 | 0.77 | -0.06 |
Per-contract and per-planned-lot numbers are trade-level over all signals of the six engine books (before the lock engine's busy rule; the stack figures below are after it). The split changes lots by only 0.1% on average (final lots 0.997-0.999 per planned lot: 70% at the signal + a risk-capped remainder that fills on 92% / 83% of signals), so most of its gain is *where* the lots are bought, which is what the random-dip placebo tests. **Units disagree in two windows**: the S73 per-contract delta vs the market is -0.11 (L3M) and -0.10 (X') pt while the lock-engine stack is +20.2k and +2.2k per week there; the per-contract numbers are +0.07 / +0.11 / +0.07 in L6M / HOLD / PRE. The stack gain is therefore not a per-trade price effect alone: it comes through the engine (the split changes exit times and which later signals are blocked or re-entered); that mechanism was not isolated here, and it is why every conclusion below is stated on the stack and the per-contract numbers are given beside.

## 2. (a) The add's size by session and by ER state (Group A: 90 trade cells + 8 stack policies; PRE u X' selection file `ga_selection_PRE_X.json`)
ER state = 5-minute Kaufman ER(20) at the signal, >= 0.3 (hi, 39% of engine signals) or < 0.3 (lo) (TG-1 store `5m.er20`, causal). Cells: F in {0.5, 0.6, 0.7, 0.8, 0.9} (slice 1 at the signal; add = 1-F, risk-capped on the original stop, target re-based) x session x ER state, dip 3 pt, S73 gate. Statistic = excess pts per planned lot over the lot-matched market line (mean pts - mean lots x mean market pts; lots ~1 so ~ delta vs market), recent first.

#### Excess per planned lot vs lot-matched market, all ER states

| session | F | L3M | L6M | HOLD | PRE | X' | 2026 |
|--|--|--|--|--|--|--|--|
| ALL sessions | 0.5 | -0.06 | +0.10 | +0.14 | +0.13 | -0.14 | +0.28 |
| ALL sessions | 0.6 | -0.08 | +0.11 | +0.14 | +0.06 | -0.10 | +0.16 |
| ALL sessions | 0.7 | -0.11 | +0.07 | +0.11 | +0.07 | -0.10 | +0.07 |
| ALL sessions | 0.8 | -0.10 | +0.05 | +0.07 | +0.01 | -0.18 | -0.06 |
| ALL sessions | 0.9 | +0.02 | +0.09 | +0.11 | -0.02 | -0.09 | +0.07 |
| asia | 0.5 | +0.49 | +0.21 | +0.30 | -0.37 | +0.39 | +0.82 |
| asia | 0.6 | +0.22 | +0.10 | +0.21 | -0.29 | +0.45 | +0.73 |
| asia | 0.7 | +0.02 | +0.00 | +0.12 | -0.10 | +0.33 | +0.36 |
| asia | 0.8 | +0.10 | +0.06 | +0.11 | -0.09 | +0.07 | +0.36 |
| asia | 0.9 | +0.03 | +0.01 | +0.06 | -0.09 | +0.09 | +0.27 |
| london | 0.5 | -0.05 | +0.01 | +0.03 | +0.66 | -0.65 | +0.20 |
| london | 0.6 | +0.07 | +0.15 | +0.10 | +0.52 | -0.49 | +0.36 |
| london | 0.7 | -0.06 | +0.07 | +0.04 | +0.35 | -0.38 | +0.27 |
| london | 0.8 | -0.09 | -0.09 | -0.10 | +0.10 | -0.36 | +0.05 |
| london | 0.9 | +0.03 | -0.04 | -0.05 | -0.02 | -0.24 | +0.21 |
| nyam | 0.5 | -0.64 | -0.32 | -0.32 | +0.28 | -0.29 | -0.19 |
| nyam | 0.6 | -0.56 | -0.25 | -0.21 | +0.10 | -0.24 | -0.48 |
| nyam | 0.7 | -0.35 | -0.16 | -0.10 | +0.10 | -0.26 | -0.17 |
| nyam | 0.8 | -0.32 | -0.14 | -0.06 | +0.05 | -0.24 | -0.34 |
| nyam | 0.9 | +0.00 | +0.14 | +0.19 | +0.06 | -0.09 | -0.03 |
| nypm | 0.5 | -0.17 | +0.71 | +0.75 | +0.08 | -0.25 | +0.51 |
| nypm | 0.6 | -0.18 | +0.61 | +0.60 | +0.04 | -0.37 | +0.19 |
| nypm | 0.7 | -0.21 | +0.49 | +0.44 | +0.00 | -0.32 | -0.12 |
| nypm | 0.8 | -0.34 | +0.41 | +0.37 | +0.01 | -0.28 | -0.42 |
| nypm | 0.9 | -0.15 | +0.24 | +0.22 | -0.05 | -0.14 | -0.21 |
| pre | 0.5 | +0.64 | +0.12 | +0.25 | +0.00 | +0.21 | -0.56 |
| pre | 0.6 | +0.72 | +0.26 | +0.40 | -0.13 | +0.36 | -0.46 |
| pre | 0.7 | +0.79 | +0.40 | +0.54 | -0.04 | +0.52 | -0.36 |
| pre | 0.8 | +0.87 | +0.30 | +0.24 | +0.04 | +0.01 | -0.26 |
| pre | 0.9 | +0.53 | +0.20 | +0.18 | -0.04 | -0.16 | -0.16 |

#### Excess per planned lot vs lot-matched market, ER >= 0.3

| session | F | L3M | L6M | HOLD | PRE | X' | 2026 |
|--|--|--|--|--|--|--|--|
| ALL sessions | 0.5 | -0.15 | -0.04 | -0.08 | +0.16 | -0.27 | +0.19 |
| ALL sessions | 0.6 | -0.19 | -0.05 | -0.07 | +0.13 | -0.17 | +0.17 |
| ALL sessions | 0.7 | -0.16 | -0.04 | -0.03 | +0.15 | -0.26 | +0.16 |
| ALL sessions | 0.8 | -0.19 | -0.02 | +0.01 | +0.02 | -0.26 | -0.07 |
| ALL sessions | 0.9 | -0.07 | -0.01 | +0.01 | -0.03 | -0.12 | -0.07 |
| asia | 0.5 | +0.52 | +0.35 | +0.30 | -0.31 | +0.36 | +1.13 |
| asia | 0.6 | -0.06 | +0.06 | +0.08 | -0.19 | +0.42 | +0.73 |
| asia | 0.7 | -0.14 | +0.06 | +0.11 | -0.03 | +0.18 | +0.33 |
| asia | 0.8 | +0.07 | +0.22 | +0.29 | -0.01 | +0.01 | +0.57 |
| asia | 0.9 | -0.02 | +0.05 | +0.17 | +0.02 | +0.10 | +0.17 |
| london | 0.5 | -0.10 | +0.13 | +0.10 | +0.05 | -0.97 | +0.43 |
| london | 0.6 | +0.00 | +0.22 | +0.19 | +0.07 | -0.86 | +0.55 |
| london | 0.7 | +0.11 | +0.16 | +0.14 | +0.04 | -0.82 | +0.67 |
| london | 0.8 | -0.21 | +0.03 | +0.03 | -0.15 | -0.55 | -0.26 |
| london | 0.9 | -0.10 | -0.09 | -0.09 | -0.18 | -0.27 | -0.13 |
| nyam | 0.5 | -0.64 | -0.65 | -0.73 | +0.82 | -0.39 | -0.70 |
| nyam | 0.6 | -0.32 | -0.41 | -0.46 | +0.68 | -0.23 | -0.38 |
| nyam | 0.7 | -0.34 | -0.36 | -0.36 | +0.61 | -0.47 | -0.05 |
| nyam | 0.8 | -0.35 | -0.31 | -0.27 | +0.25 | -0.27 | -0.67 |
| nyam | 0.9 | -0.00 | -0.06 | -0.10 | -0.00 | -0.20 | -0.33 |
| nypm | 0.5 | -0.64 | +0.25 | +0.20 | +0.26 | -0.28 | -0.70 |
| nypm | 0.6 | -0.44 | +0.12 | +0.08 | +0.13 | -0.31 | -0.56 |
| nypm | 0.7 | -0.24 | +0.18 | +0.14 | +0.06 | -0.25 | -0.42 |
| nypm | 0.8 | -0.41 | +0.04 | +0.02 | -0.02 | -0.18 | -0.28 |
| nypm | 0.9 | -0.20 | +0.10 | +0.08 | +0.05 | -0.09 | -0.14 |
| pre | 0.5 | +0.01 | -0.64 | -0.58 | +0.13 | +0.14 | +0.27 |
| pre | 0.6 | +0.01 | -0.51 | -0.47 | -0.07 | +0.40 | +0.21 |
| pre | 0.7 | +0.01 | -0.38 | -0.35 | +0.02 | +0.65 | +0.16 |
| pre | 0.8 | +0.00 | -0.26 | -0.23 | +0.11 | -0.52 | +0.11 |
| pre | 0.9 | +0.00 | -0.13 | -0.12 | +0.01 | -0.26 | +0.05 |

#### Excess per planned lot vs lot-matched market, ER < 0.3

| session | F | L3M | L6M | HOLD | PRE | X' | 2026 |
|--|--|--|--|--|--|--|--|
| ALL sessions | 0.5 | -0.01 | +0.16 | +0.26 | +0.11 | -0.05 | +0.32 |
| ALL sessions | 0.6 | -0.02 | +0.19 | +0.26 | +0.01 | -0.05 | +0.14 |
| ALL sessions | 0.7 | -0.08 | +0.13 | +0.19 | +0.02 | +0.02 | +0.02 |
| ALL sessions | 0.8 | -0.05 | +0.08 | +0.10 | +0.01 | -0.12 | -0.06 |
| ALL sessions | 0.9 | +0.06 | +0.14 | +0.17 | -0.02 | -0.06 | +0.15 |
| asia | 0.5 | +0.46 | +0.09 | +0.26 | -0.42 | +0.41 | +0.58 |
| asia | 0.6 | +0.39 | +0.12 | +0.27 | -0.36 | +0.47 | +0.72 |
| asia | 0.7 | +0.13 | -0.05 | +0.10 | -0.16 | +0.43 | +0.37 |
| asia | 0.8 | +0.13 | -0.06 | -0.02 | -0.15 | +0.12 | +0.19 |
| asia | 0.9 | +0.06 | -0.03 | -0.01 | -0.18 | +0.09 | +0.34 |
| london | 0.5 | -0.03 | -0.07 | -0.03 | +1.11 | -0.30 | +0.08 |
| london | 0.6 | +0.10 | +0.09 | +0.04 | +0.84 | -0.10 | +0.25 |
| london | 0.7 | -0.16 | +0.01 | -0.03 | +0.58 | +0.10 | +0.05 |
| london | 0.8 | -0.03 | -0.17 | -0.18 | +0.28 | -0.15 | +0.22 |
| london | 0.9 | +0.10 | -0.01 | -0.02 | +0.10 | -0.20 | +0.39 |
| nyam | 0.5 | -0.63 | -0.17 | -0.12 | +0.02 | -0.24 | +0.05 |
| nyam | 0.6 | -0.66 | -0.17 | -0.09 | -0.18 | -0.25 | -0.52 |
| nyam | 0.7 | -0.35 | -0.07 | +0.03 | -0.13 | -0.14 | -0.22 |
| nyam | 0.8 | -0.31 | -0.06 | +0.04 | -0.04 | -0.22 | -0.19 |
| nyam | 0.9 | +0.01 | +0.23 | +0.33 | +0.09 | -0.03 | +0.11 |
| nypm | 0.5 | +0.08 | +0.94 | +1.03 | -0.02 | -0.24 | +1.21 |
| nypm | 0.6 | -0.04 | +0.86 | +0.86 | -0.01 | -0.42 | +0.62 |
| nypm | 0.7 | -0.20 | +0.65 | +0.59 | -0.03 | -0.38 | +0.04 |
| nypm | 0.8 | -0.31 | +0.61 | +0.55 | +0.03 | -0.36 | -0.54 |
| nypm | 0.9 | -0.13 | +0.32 | +0.29 | -0.10 | -0.18 | -0.27 |
| pre | 0.5 | +1.02 | +0.63 | +0.77 | -0.10 | +0.22 | -0.85 |
| pre | 0.6 | +1.13 | +0.78 | +0.94 | -0.17 | +0.30 | -0.72 |
| pre | 0.7 | +1.24 | +0.93 | +1.11 | -0.09 | +0.38 | -0.58 |
| pre | 0.8 | +1.36 | +0.68 | +0.55 | -0.01 | +0.45 | -0.44 |
| pre | 0.9 | +0.81 | +0.43 | +0.36 | -0.08 | -0.08 | -0.30 |

Sessions: asia, london, pre (08:30-09:30 ET), nyam, nypm, close (close has 38 PRE u X' trades and is not scored by itself). PRE u X' argmax (selection, recent windows not read): {"A1|asia": 0.7, "A1|close": 0.7, "A1|london": 0.5, "A1|nyam": 0.5, "A1|nypm": 0.5, "A1|pre": 0.7, "A2|hi": 0.6, "A2|lo": 0.5, "A3|asia|hi": 0.9, "A3|asia|lo": 0.7, "A3|close|hi": 0.7, "A3|close|lo": 0.7, "A3|london|hi": 0.6, "A3|london|lo": 0.5, "A3|nyam|hi": 0.5, "A3|nyam|lo": 0.9, "A3|nypm|hi": 0.5, "A3|nypm|lo": 0.8, "A3|pre|hi": 0.7, "A3|pre|lo": 0.8}. Standard errors of the paired F-vs-0.7 differences in PRE u X' are 0.04-0.27 pt per planned lot per cell, i.e. most cells are within 1-2 SE of 0.7.

#### Eight policies on the lock engine, stack delta vs the stack as it is ($k/wk, MDE), basis N (LC and LJ in the CSV `rep_A_stack.md`), and vs uniform A0

| policy | basis | vs market L3M | vs market L6M | vs market HOLD | vs market PRE | vs market X' | vs market 2026 | vs A0 L3M | vs A0 L6M | vs A0 HOLD | vs A0 PRE | vs A0 X' |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| A0 uniform F 0.7 (S73, reference) | N | +20.2k (25.2k) | +17.6k (16.6k) | +18.4k (15.3k) | +3.8k (10.7k) | +2.2k (8.4k) | +18.1k (40.6k) | - | - | - | - | - |
|  | LC | +16.1k (24.4k) | +15.1k (15.8k) | +16.0k (14.7k) | +3.8k (11.2k) | +2.5k (8.4k) | +14.6k (40.3k) | - | - | - | - | - |
|  | LJ | +14.7k (30.2k) | +14.4k (18.5k) | +15.6k (16.9k) | +3.8k (10.8k) | +1.9k (8.6k) | +4.8k (55.5k) | - | - | - | - | - |
| A1 F by session (PRE u X' argmax; n<150 -> 0.7) | N | +22.7k (23.2k) | +17.9k (16.1k) | +18.2k (14.8k) | +3.4k (12.8k) | +1.7k (9.8k) | +22.8k (32.6k) | +2.5k (8.7k) | +0.3k (5.5k) | -0.2k (4.9k) | -0.4k (4.9k) | -0.5k (4.3k) |
|  | LC | +22.3k (21.2k) | +18.7k (14.7k) | +18.6k (13.8k) | +3.6k (12.0k) | +1.8k (9.8k) | +20.2k (29.9k) | +6.2k (8.9k) | +3.5k (6.4k) | +2.6k (5.8k) | -0.2k (4.1k) | -0.7k (4.5k) |
|  | LJ | +20.5k (28.4k) | +16.4k (18.0k) | +17.0k (16.4k) | +3.9k (12.6k) | +1.0k (10.1k) | +12.2k (43.9k) | +5.8k (10.7k) | +2.0k (6.5k) | +1.3k (5.9k) | +0.1k (4.7k) | -1.0k (5.5k) |
| A2 F by ER state (PRE u X' argmax) | N | +25.4k (28.7k) | +19.7k (18.2k) | +20.0k (16.4k) | -0.7k (14.1k) | +1.6k (10.5k) | +24.9k (49.1k) | +5.2k (10.6k) | +2.1k (6.4k) | +1.6k (5.7k) | -4.4k (7.1k) | -0.5k (5.5k) |
|  | LC | +24.7k (27.0k) | +20.6k (16.8k) | +20.5k (15.3k) | +1.2k (12.8k) | +1.5k (11.0k) | +27.8k (43.1k) | +8.6k (11.2k) | +5.4k (7.3k) | +4.5k (6.6k) | -2.6k (6.2k) | -1.0k (5.7k) |
|  | LJ | +20.9k (34.3k) | +16.0k (20.8k) | +16.6k (18.7k) | +0.6k (13.1k) | +1.3k (11.1k) | +14.2k (65.6k) | +6.2k (12.7k) | +1.6k (7.7k) | +1.0k (6.9k) | -3.2k (6.6k) | -0.6k (6.6k) |
| A3 F by session x ER (PRE u X' argmax) | N | +17.6k (22.0k) | +15.8k (15.5k) | +17.2k (14.4k) | +1.7k (10.8k) | +0.3k (10.1k) | +26.8k (32.8k) | -2.6k (17.4k) | -1.7k (9.1k) | -1.1k (8.0k) | -2.1k (6.0k) | -1.8k (4.3k) |
|  | LC | +21.3k (21.7k) | +17.3k (15.3k) | +18.2k (14.3k) | +2.3k (10.4k) | -0.2k (10.5k) | +25.6k (30.8k) | +5.2k (16.1k) | +2.2k (8.7k) | +2.3k (7.6k) | -1.5k (5.9k) | -2.7k (4.5k) |
|  | LJ | +16.1k (19.9k) | +15.0k (14.8k) | +16.3k (13.7k) | +2.2k (10.3k) | -0.4k (10.5k) | +19.2k (34.1k) | +1.4k (19.4k) | +0.6k (10.0k) | +0.6k (8.8k) | -1.6k (6.2k) | -2.3k (5.2k) |
| A4 DIRECTIVE: 50% add Asia, 30% elsewhere | N | +25.1k (35.9k) | +20.4k (21.7k) | +20.9k (19.3k) | +0.5k (12.5k) | +2.6k (9.8k) | +28.6k (74.9k) | +4.9k (17.7k) | +2.8k (9.0k) | +2.5k (7.9k) | -3.3k (6.6k) | +0.5k (4.7k) |
|  | LC | +23.0k (36.1k) | +18.9k (21.2k) | +18.9k (18.9k) | -0.1k (11.7k) | +2.5k (10.2k) | +28.2k (71.5k) | +6.9k (17.6k) | +3.7k (9.0k) | +3.0k (8.1k) | -3.9k (6.8k) | +0.1k (4.9k) |
|  | LJ | +19.0k (41.3k) | +17.0k (23.4k) | +17.8k (20.8k) | +1.6k (12.6k) | +1.9k (10.0k) | +14.3k (88.3k) | +4.4k (19.0k) | +2.6k (9.7k) | +2.2k (8.6k) | -2.3k (7.1k) | -0.0k (5.4k) |
| A5 DIRECTIVE-2: 50% add in Asia or ER>=0.3, else 30% | N | +21.8k (36.2k) | +19.4k (21.7k) | +20.3k (19.3k) | -0.3k (12.7k) | +1.6k (11.0k) | +25.6k (73.2k) | +1.6k (18.3k) | +1.8k (9.3k) | +1.9k (8.4k) | -4.1k (7.1k) | -0.6k (5.7k) |
|  | LC | +21.9k (35.3k) | +19.2k (20.7k) | +19.9k (18.6k) | -0.5k (12.0k) | +1.9k (11.1k) | +26.4k (68.9k) | +5.9k (16.4k) | +4.0k (8.4k) | +3.9k (7.7k) | -4.3k (7.5k) | -0.6k (5.9k) |
|  | LJ | +15.3k (41.2k) | +15.2k (23.4k) | +15.3k (21.2k) | +1.0k (13.3k) | +1.6k (11.0k) | +14.1k (87.6k) | +0.6k (19.0k) | +0.7k (9.6k) | -0.3k (10.0k) | -2.8k (8.3k) | -0.3k (5.6k) |
| A6 ER>=0.3 -> 10% add, else 30% | N | +17.7k (20.4k) | +14.4k (16.3k) | +15.2k (15.0k) | +2.0k (9.4k) | +1.5k (8.5k) | +23.2k (35.9k) | -2.5k (16.7k) | -3.2k (9.9k) | -3.2k (8.7k) | -1.8k (4.4k) | -0.7k (2.2k) |
|  | LC | +19.0k (21.3k) | +14.6k (15.8k) | +16.5k (15.3k) | +1.8k (10.5k) | +2.5k (8.4k) | +19.1k (34.5k) | +2.9k (10.6k) | -0.6k (7.2k) | +0.5k (6.9k) | -2.0k (4.7k) | +0.0k (2.4k) |
|  | LJ | +16.6k (26.0k) | +14.2k (18.0k) | +15.0k (16.4k) | +3.1k (9.3k) | +1.3k (8.4k) | +8.9k (44.5k) | +2.0k (7.7k) | -0.2k (6.5k) | -0.6k (5.7k) | -0.8k (4.7k) | -0.6k (2.2k) |
| A7 uniform F 0.9 (10% add) | N | +16.3k (20.1k) | +12.0k (14.4k) | +13.6k (14.0k) | +2.4k (7.2k) | +0.8k (5.7k) | +32.2k (26.6k) | -3.9k (23.5k) | -5.6k (13.9k) | -4.8k (12.7k) | -1.4k (7.9k) | -1.4k (5.7k) |
|  | LC | +13.6k (19.2k) | +11.1k (14.3k) | +12.9k (13.6k) | +3.8k (7.1k) | +0.5k (5.7k) | +23.1k (29.5k) | -2.4k (23.6k) | -4.1k (12.9k) | -3.1k (11.8k) | +0.0k (7.8k) | -1.9k (6.1k) |
|  | LJ | +11.5k (16.8k) | +9.7k (13.0k) | +10.1k (12.2k) | +2.3k (6.8k) | +0.9k (5.8k) | +16.0k (25.7k) | -3.2k (21.4k) | -4.7k (12.9k) | -5.5k (11.5k) | -1.5k (8.2k) | -1.0k (6.0k) |

Reading: every policy is inside its MDE of uniform 0.7 in every window on every basis (largest L6M gain vs A0: A4 +2.8k, MDE 9.0k; LIVE-CAL A2 +5.4k, MDE 7.3k, and PRE -2.6k). The directive's literal question - a 50% add in Asia and 30% in NY - is A4: +20.4k L6M (vs A0 +17.6k), HOLD +20.9k, PRE +0.5k (A0 +3.8k), X' +2.6k (A0 +2.2k): it is the same stack inside noise, and the Asia F=0.5 gain exists in L3M/L6M/HOLD (+0.49 / +0.21 / +0.30 per planned lot vs F=0.7) but is -0.37 in PRE (+0.39 in X'), so Asia has no stable preference. By ER state (F 0.7, excess per planned lot, L3M / L6M / HOLD / PRE / X'): ER >= 0.3 -0.16 / -0.04 / -0.03 / +0.15 / -0.26; ER < 0.3 -0.08 / +0.13 / +0.19 / +0.02 / +0.02; in the low-ER state F 0.5 vs 0.7 is +0.16 / +0.26 in L6M / HOLD but +0.11 in PRE and -0.05 in X'. The add pays when ER is low in 2025-26 and not in trend, but not reliably across years: the T2 add-sizer question (ER x split) gets the same answer here, no stable ER dependence of the add. Random-dip placebo for the S73 reference (100 draws, adds at random seconds, same time-since-entry distribution, N): real vs lot-matched line L6M +17.7k vs placebo mean -13.4k (sd +6.0k), rank 1.00; HOLD rank 1.00, PRE 1.00, X' 1.00, L3M 1.00, 2026 0.98 - the dip, not the add, carries the gain.

## 3. (b) The add as a limit at (signal - X) placed at arming vs a market add at the X-pt touch (Group B: 48 cells; no selection - directive pair; neighbourhood X in {2,3,5,8} x F in {0.7,0.9})
Modes: MG market at the touch with the S73 gate (1 of 8 + veto v4); MV market at the touch, no gate, veto v4 only; MR market, no gate, no veto; LT limit at (signal - X) resting from the signal second (arming), fills when the 1-s low (long) trades <= the level (touch, optimistic); L1 / L2 the same with +1 / +2 ticks of trade-through (L2 is the regime the live-cal evidence supports: 11/11 touched targets filled when traded through by > 2 ticks, marginal touches undecided). The limit is cancelled if the stop level trades first; a market add fills at the close of the decision second + 1 tick in the next second. Stack delta vs the stack as it is ($k/wk, MDE), N basis; LC / LJ L6M beside; fill and cost columns are over the six engine books in L6M.
| cell | mode | N L3M | N L6M | N HOLD | N PRE | N X' | N 2026 | LC L6M | LJ L6M | add fill rate L6M | P(target|add fill) | P(stop|add fill) | limit price advantage vs MV fill (pts; + = limit cheaper) | L6M vs S73 (A0) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| X3 F0.7 | MG | +20.2k (25.2k) | +17.6k (16.6k) | +18.4k (15.3k) | +3.8k (10.7k) | +2.2k (8.4k) | +18.1k (40.6k) | +15.1k | +14.4k | 92.1% | 0.500 | 0.465 | - | - |
|  | MV | +12.3k (16.1k) | +10.7k (12.3k) | +13.0k (12.2k) | +1.6k (10.5k) | +1.7k (8.6k) | +12.0k (28.0k) | +8.7k | +9.9k | 93.0% | 0.503 | 0.462 | - | -6.8k |
|  | MR | +12.2k (16.0k) | +10.7k (12.3k) | +13.0k (12.1k) | +1.5k (10.5k) | +1.8k (8.6k) | +11.9k (27.7k) | +8.6k | +9.8k | 93.1% | 0.503 | 0.462 | - | -6.9k |
|  | LT | +8.4k (16.5k) | +7.3k (13.2k) | +9.2k (12.6k) | +1.8k (9.8k) | +0.9k (8.1k) | +7.8k (29.8k) | +7.4k | +7.1k | 94.3% | 0.508 | 0.457 | -0.72 | -10.3k |
|  | L1 | +10.4k (19.4k) | +7.6k (14.2k) | +9.2k (13.5k) | +0.5k (10.8k) | -0.1k (8.4k) | +15.0k (37.2k) | +7.8k | +6.7k | 93.7% | 0.505 | 0.460 | -0.72 | -10.0k |
|  | L2 | +10.1k (18.1k) | +7.2k (13.8k) | +8.8k (13.1k) | -0.5k (10.6k) | -0.2k (8.7k) | +13.3k (34.4k) | +8.3k | +6.2k | 93.2% | 0.503 | 0.462 | -0.73 | -10.4k |
| X3 F0.9 | MG | +16.3k (20.1k) | +12.0k (14.4k) | +13.6k (14.0k) | +2.4k (7.2k) | +0.8k (5.7k) | +32.2k (26.6k) | +11.1k | +9.7k | 92.1% | 0.496 | 0.469 | - | -5.6k |
|  | MV | +13.4k (17.5k) | +8.9k (12.2k) | +11.0k (12.4k) | +1.9k (7.1k) | +0.9k (6.1k) | +25.3k (30.0k) | +7.8k | +5.3k | 93.0% | 0.500 | 0.465 | - | -8.7k |
|  | MR | +13.4k (17.5k) | +8.9k (12.2k) | +11.0k (12.4k) | +1.7k (7.1k) | +0.9k (6.1k) | +25.2k (30.0k) | +7.8k | +5.3k | 93.1% | 0.500 | 0.465 | - | -8.7k |
|  | LT | +12.2k (16.1k) | +9.2k (11.6k) | +10.9k (11.6k) | +2.6k (7.1k) | +0.7k (5.7k) | +22.6k (27.6k) | +7.5k | +6.9k | 94.3% | 0.506 | 0.459 | -0.72 | -8.4k |
|  | L1 | +15.3k (17.0k) | +10.5k (12.0k) | +11.8k (12.1k) | +2.4k (7.2k) | +0.4k (5.7k) | +30.0k (25.4k) | +8.8k | +8.2k | 93.7% | 0.503 | 0.462 | -0.72 | -7.1k |
|  | L2 | +14.8k (16.7k) | +10.2k (12.0k) | +11.5k (12.0k) | +1.2k (7.4k) | +0.1k (5.7k) | +29.3k (24.7k) | +7.7k | +7.8k | 93.2% | 0.501 | 0.464 | -0.73 | -7.4k |
| X5 F0.7 | MG | +22.4k (24.7k) | +21.5k (16.4k) | +21.3k (15.1k) | -0.3k (10.7k) | +2.8k (12.2k) | +32.9k (39.3k) | +22.0k | +20.5k | 87.9% | 0.484 | 0.481 | - | +3.9k |
|  | MV | +21.4k (21.5k) | +19.2k (16.3k) | +19.1k (15.0k) | +0.8k (11.6k) | +3.5k (11.8k) | +29.4k (43.7k) | +21.7k | +18.3k | 88.8% | 0.488 | 0.478 | - | +1.6k |
|  | MR | +21.4k (21.5k) | +19.2k (16.3k) | +19.1k (15.0k) | +0.8k (11.6k) | +3.6k (11.8k) | +29.5k (43.7k) | +21.7k | +18.3k | 88.8% | 0.488 | 0.478 | - | +1.6k |
|  | LT | +17.3k (22.0k) | +17.9k (18.6k) | +17.4k (16.9k) | -0.3k (11.6k) | +3.2k (12.1k) | +33.0k (36.0k) | +21.6k | +16.0k | 90.0% | 0.493 | 0.473 | -0.71 | +0.3k |
|  | L1 | +14.7k (21.4k) | +14.8k (16.5k) | +14.5k (15.2k) | -2.1k (11.6k) | +2.6k (12.2k) | +22.1k (43.2k) | +17.1k | +14.3k | 89.5% | 0.490 | 0.475 | -0.71 | -2.8k |
|  | L2 | +14.2k (23.0k) | +13.8k (16.8k) | +13.6k (15.5k) | -3.2k (11.0k) | +1.9k (12.2k) | +22.7k (46.2k) | +15.6k | +13.4k | 89.1% | 0.488 | 0.477 | -0.72 | -3.8k |
| X8 F0.7 | MG | +29.6k (32.6k) | +22.3k (24.9k) | +20.4k (22.5k) | -6.2k (14.2k) | +5.3k (14.3k) | +53.9k (40.5k) | +26.4k | +22.2k | 82.2% | 0.458 | 0.507 | - | +4.8k |
|  | MV | +26.8k (38.3k) | +22.6k (25.4k) | +21.8k (22.6k) | -2.6k (13.9k) | +6.4k (13.4k) | +56.9k (42.5k) | +25.5k | +23.3k | 83.1% | 0.463 | 0.503 | - | +5.1k |
|  | MR | +26.8k (38.3k) | +21.7k (25.4k) | +21.0k (22.6k) | -2.5k (13.9k) | +6.4k (13.4k) | +56.9k (42.5k) | +24.6k | +22.4k | 83.1% | 0.463 | 0.503 | - | +4.1k |
|  | LT | +30.2k (31.4k) | +23.5k (20.9k) | +22.9k (18.7k) | -2.0k (12.7k) | +7.9k (12.8k) | +55.0k (42.4k) | +26.5k | +21.3k | 84.4% | 0.469 | 0.497 | -0.70 | +5.9k |
|  | L1 | +28.9k (31.9k) | +22.4k (21.2k) | +21.8k (19.0k) | -3.0k (12.8k) | +6.0k (12.9k) | +53.7k (42.6k) | +25.2k | +20.2k | 83.9% | 0.466 | 0.499 | -0.70 | +4.8k |
|  | L2 | +26.1k (31.4k) | +21.9k (21.9k) | +21.4k (19.5k) | -4.9k (13.1k) | +2.9k (14.2k) | +50.9k (43.1k) | +24.7k | +18.8k | 83.4% | 0.464 | 0.501 | -0.71 | +4.3k |
| X8 F0.9 | MG | +17.3k (20.6k) | +17.3k (13.6k) | +15.6k (13.5k) | +2.9k (9.8k) | +7.7k (9.2k) | +28.0k (26.5k) | +16.9k | +15.2k | 82.2% | 0.449 | 0.515 | - | -0.2k |
|  | MV | +17.2k (18.9k) | +17.1k (12.9k) | +15.8k (12.6k) | +3.2k (9.8k) | +8.4k (9.1k) | +27.7k (26.3k) | +17.1k | +14.8k | 83.1% | 0.454 | 0.510 | - | -0.5k |
|  | MR | +17.2k (18.9k) | +17.1k (12.9k) | +15.8k (12.6k) | +3.2k (9.8k) | +8.0k (8.8k) | +27.7k (26.3k) | +17.1k | +14.8k | 83.1% | 0.454 | 0.510 | - | -0.5k |
|  | LT | +15.1k (18.8k) | +17.9k (13.2k) | +16.4k (12.9k) | +3.8k (9.5k) | +8.0k (8.8k) | +28.2k (25.7k) | +15.6k | +15.7k | 84.4% | 0.461 | 0.503 | -0.70 | +0.3k |
|  | L1 | +14.7k (18.9k) | +17.3k (13.2k) | +16.3k (12.7k) | +3.3k (9.4k) | +7.5k (8.8k) | +27.7k (25.9k) | +15.0k | +15.2k | 83.9% | 0.458 | 0.505 | -0.70 | -0.3k |
|  | L2 | +13.9k (18.4k) | +16.8k (13.1k) | +15.9k (12.6k) | +2.6k (9.5k) | +6.9k (8.8k) | +25.9k (25.6k) | +15.6k | +14.5k | 83.4% | 0.457 | 0.507 | -0.71 | -0.7k |
| X2 F0.7 | MG | +4.3k (16.1k) | +2.0k (12.0k) | +4.1k (11.0k) | +3.0k (9.7k) | -1.3k (7.4k) | -0.9k (20.4k) | +1.7k | +2.9k | 94.0% | 0.505 | 0.460 | - | -15.6k |
|  | MV | +6.9k (17.2k) | +1.8k (12.0k) | +4.2k (11.0k) | +0.5k (8.3k) | -2.4k (7.5k) | +0.9k (23.4k) | +1.4k | +0.3k | 94.7% | 0.508 | 0.457 | - | -15.8k |
|  | MR | +6.9k (17.2k) | +1.8k (12.0k) | +4.2k (11.0k) | +0.5k (8.3k) | -2.7k (7.6k) | +0.9k (23.4k) | +1.4k | +0.3k | 94.7% | 0.508 | 0.457 | - | -15.7k |
|  | LT | +6.2k (15.9k) | +2.2k (14.1k) | +3.3k (13.0k) | +0.8k (7.3k) | -2.0k (7.5k) | +4.8k (15.3k) | +2.1k | -0.0k | 95.9% | 0.514 | 0.452 | -0.72 | -15.4k |
|  | L1 | +5.1k (15.4k) | +0.9k (13.8k) | +2.2k (12.8k) | -0.1k (7.7k) | -2.5k (7.6k) | +2.3k (10.6k) | +1.4k | -1.3k | 95.6% | 0.513 | 0.453 | -0.72 | -16.6k |
|  | L2 | +4.0k (15.7k) | +0.1k (13.9k) | +1.3k (12.8k) | -1.1k (8.0k) | -3.2k (7.4k) | +0.8k (11.0k) | +0.5k | -2.2k | 95.3% | 0.511 | 0.454 | -0.72 | -17.5k |

Fill rate by session at 70/30-at-3 (L6M, six engine books): MG: asia 92%, london 94%, pre 93%, nyam 90%, nypm 94%; LT: asia 93%, london 95%, pre 95%, nyam 94%, nypm 96%; L2: asia 92%, london 94%, pre 95%, nyam 93%, nypm 94%.

Reading: (1) the gate is the information in the 70/30-at-3 split (MG +17.6k vs MV +10.7k L6M; PRE +3.8k vs +1.6k; HOLD +18.4k vs +13.0k; the earlier UF placebo found the same: rank 1.00 against random gates) - a resting limit cannot carry the gate, because the gate is evaluated at the touch second, so it is compared with MV for the price effect and with MG for the real alternative. (2) The limit does not improve price: **conditional on both filling, the limit price is 0.70-0.73 pt worse than the market fill** (a market add triggers only when a 1-s close is already X pt away and fills in the next second, so it is on average beyond the level; the limit fills at exactly the level). It fills more often (+1.5 to +2 points) because wicks that bounce back through the level fill it; those marginal fills do not pay (P(target|fill) 0.51 vs 0.50, P(stop|fill) 0.46, same). (3) Making the fill harder (+1 / +2 ticks of trade-through, the cost-honest conventions) changes L6M by +0.3k / -0.1k at X=3 F=0.7 and PRE by -1.3k / -2.3k; at X=5 F=0.7 L6M -3.1k / -4.1k and PRE -1.8k / -2.9k; at 90/10-at-8 all three conventions are within 1.1k of each other. (4) The touch-filled limit (LT) beats the gated market (MG) in 3 of the 8 (X, F) pairs (X2 F.7, X8 F.7, X8 F.9) by at most 1.2k L6M and loses by 0.5-10.3k in the other 5; none of those differences exceeds its MDE except X3 F.7 (-10.3k vs MDE 9-10k). **Fill-rate answer: 93-95% at X=2-3, 82-84% at X=8; cost answer: the limit is a -0.7 pt price give-up per add lot against a market fill, repaid only by the extra marginal fills, which are not better trades.** None of the 48 cells beats S73 in L6M above its MDE (RC vs S73 p 0.77 L6M, 0 survivors).

## 4. (c) 90/10-at-8 vs 70/30-at-3 on the live-cal basis, stop-join fix assumed (0.5) and not (2.45) (Group C: 18 cells; headline pair pre-specified by the directive, no selection)
C70 = F0.7 X3 S73 gate (1 of 8, veto v4); C90 = F0.9 X8 no gate, veto v4 (UF1|G1|F=0.9|X=8|N=0, already in DEAD_CELLS as flat vs the split at +0 pt; here re-scored for the stop-cost grid). Stack delta vs the stack as it is ($k/wk, MDE), target basis N (stop cost S pts per stop-class lot; S=1.01 is the measured-fill N basis, S=2.45 LIVE-CAL, S=0.5 join fixed, 4.46 = every stop falls back); M (target correction kept) beside for S=1.01 / 2.45.
| cell | target basis | stop cost S | vs market L3M | vs market L6M | vs market HOLD | vs market PRE | vs market X' | vs market 2026 | pts / contract L6M (after costs) | per-contract delta vs market L6M |
|--|--|--|--|--|--|--|--|--|--|--|
| C70 70/30@3 | N | 0.5 | +14.7k (30.2k) | +14.4k (18.5k) | +15.6k (16.9k) | +3.8k (10.8k) | +1.9k (8.6k) | +4.8k (55.5k) | 2.69 | +0.08 |
|  | N | 1.01 | +20.2k (25.2k) | +17.6k (16.6k) | +18.4k (15.3k) | +3.8k (10.7k) | +2.2k (8.4k) | +18.1k (40.6k) | 2.46 | +0.07 |
|  | N | 1.5 | +18.8k (23.1k) | +17.0k (15.9k) | +17.9k (14.8k) | +4.1k (10.8k) | +2.6k (8.6k) | +19.5k (39.1k) | 2.25 | +0.07 |
|  | N | 2.45 | +16.1k (24.4k) | +15.1k (15.8k) | +16.0k (14.7k) | +3.8k (11.2k) | +2.5k (8.4k) | +14.6k (40.3k) | 1.83 | +0.07 |
|  | N | 3.5 | +19.6k (23.4k) | +17.7k (14.4k) | +17.2k (13.8k) | +3.5k (11.3k) | +2.6k (8.3k) | +18.3k (35.8k) | 1.36 | +0.06 |
|  | N | 4.46 | +14.9k (24.2k) | +15.9k (16.6k) | +15.7k (15.6k) | +0.2k (11.4k) | +2.0k (9.0k) | +13.0k (41.5k) | 0.94 | +0.06 |
|  | M | 1.01 | +9.3k (20.2k) | +13.3k (14.5k) | +11.6k (14.0k) | +7.6k (11.2k) | +2.8k (8.4k) | +19.5k (41.7k) | 0.25 | +0.10 |
|  | M | 2.45 | +12.4k (22.1k) | +15.2k (15.2k) | +13.0k (14.6k) | +6.2k (12.4k) | +3.1k (8.2k) | +19.5k (43.0k) | -0.39 | +0.09 |
| C90 90/10@8 | N | 0.5 | +12.7k (19.4k) | +14.8k (13.1k) | +13.8k (12.7k) | +3.0k (9.8k) | +8.7k (9.4k) | +17.4k (32.6k) | 2.62 | +0.00 |
|  | N | 1.01 | +17.2k (18.9k) | +17.1k (12.9k) | +15.8k (12.6k) | +3.2k (9.8k) | +8.4k (9.1k) | +27.7k (26.3k) | 2.39 | +0.00 |
|  | N | 1.5 | +18.3k (19.7k) | +17.5k (13.0k) | +16.1k (12.9k) | +3.8k (9.8k) | +9.0k (9.2k) | +26.7k (26.0k) | 2.17 | -0.00 |
|  | N | 2.45 | +17.8k (20.3k) | +17.1k (13.4k) | +16.1k (12.7k) | +3.0k (9.9k) | +7.5k (9.0k) | +18.8k (29.3k) | 1.76 | -0.00 |
|  | N | 3.5 | +14.1k (15.9k) | +11.2k (9.5k) | +11.8k (8.5k) | +1.4k (9.7k) | +7.0k (7.0k) | +7.3k (11.9k) | 1.29 | -0.01 |
|  | N | 4.46 | +8.7k (15.2k) | +9.2k (10.1k) | +10.0k (9.1k) | -0.0k (10.0k) | +6.7k (7.2k) | +5.9k (9.7k) | 0.87 | -0.01 |
|  | M | 1.01 | +1.0k (20.3k) | +13.3k (15.8k) | +10.2k (14.8k) | +6.9k (11.0k) | +7.9k (9.3k) | +5.0k (34.4k) | 0.17 | +0.02 |
|  | M | 2.45 | +6.1k (20.3k) | +14.8k (15.3k) | +11.3k (14.5k) | +7.5k (10.9k) | +6.6k (9.2k) | +7.0k (34.1k) | -0.46 | +0.01 |

#### Paired C90 minus C70 (N basis; $k/wk, MDE) by stop cost

| stop cost S | L3M | L6M | HOLD | PRE | X' | 2026 |
|--|--|--|--|--|--|--|
| 0.5 | -1.9k (20.6k) | +0.4k (13.6k) | -1.8k (12.5k) | -0.8k (9.4k) | +6.8k (9.3k) | +12.5k (27.9k) |
| 1.01 | -3.0k (19.7k) | -0.5k (13.4k) | -2.6k (12.2k) | -0.6k (9.0k) | +6.2k (8.8k) | +9.6k (25.9k) |
| 1.5 | -0.5k (13.8k) | +0.5k (11.3k) | -1.8k (10.6k) | -0.3k (8.9k) | +6.4k (9.0k) | +7.2k (25.6k) |
| 2.45 | +1.7k (21.1k) | +2.0k (12.5k) | +0.2k (11.5k) | -0.9k (8.8k) | +5.0k (8.6k) | +4.2k (46.2k) |
| 3.5 | -5.5k (18.0k) | -6.5k (11.0k) | -5.5k (11.1k) | -2.1k (9.2k) | +4.4k (5.7k) | -11.1k (34.7k) |
| 4.46 | -6.2k (19.4k) | -6.7k (12.2k) | -5.7k (12.0k) | -0.2k (9.7k) | +4.7k (6.2k) | -7.0k (38.8k) |

#### Remainder fill cost (+ce pt per remainder lot-fill; applied to the cell, not to the market), vs market, N target basis

| cell | stop cost | ce | L3M | L6M | HOLD | PRE | X' | 2026 |
|--|--|--|--|--|--|--|--|--|
| C70 | 0.5 | 0 | +14.7k (30.2k) | +14.4k (18.5k) | +15.6k (16.9k) | +3.8k (10.8k) | +1.9k (8.6k) | +4.8k (55.5k) |
|  | 0.5 | 1 | +4.4k (25.8k) | +6.1k (16.9k) | +7.7k (15.7k) | -1.9k (10.3k) | -2.6k (8.7k) | +3.6k (51.2k) |
|  | 0.5 | 2 | +2.7k (24.0k) | +1.5k (16.3k) | +2.9k (15.1k) | -7.8k (11.7k) | -6.6k (8.6k) | +4.0k (45.6k) |
|  | 2.45 | 0 | +16.1k (24.4k) | +15.1k (15.8k) | +16.0k (14.7k) | +3.8k (11.2k) | +2.5k (8.4k) | +14.6k (40.3k) |
|  | 2.45 | 1 | +10.0k (22.8k) | +8.6k (15.4k) | +9.7k (14.5k) | -1.6k (11.2k) | -1.8k (8.6k) | +12.7k (38.7k) |
|  | 2.45 | 2 | +4.5k (23.5k) | +3.9k (16.0k) | +4.7k (14.8k) | -7.6k (11.4k) | -5.9k (8.6k) | +10.8k (38.1k) |
| C90 | 0.5 | 0 | +12.7k (19.4k) | +14.8k (13.1k) | +13.8k (12.7k) | +3.0k (9.8k) | +8.7k (9.4k) | +17.4k (32.6k) |
|  | 0.5 | 1 | +11.2k (19.4k) | +13.3k (13.1k) | +12.3k (12.7k) | +1.6k (9.8k) | +7.1k (9.3k) | +15.8k (32.6k) |
|  | 0.5 | 2 | +9.9k (19.3k) | +11.7k (13.0k) | +10.7k (12.7k) | -0.2k (9.6k) | +5.3k (9.1k) | +14.5k (32.6k) |
|  | 2.45 | 0 | +17.8k (20.3k) | +17.1k (13.4k) | +16.1k (12.7k) | +3.0k (9.9k) | +7.5k (9.0k) | +18.8k (29.3k) |
|  | 2.45 | 1 | +14.7k (19.5k) | +14.9k (13.1k) | +14.0k (12.4k) | -0.0k (9.9k) | +5.7k (9.0k) | +13.5k (26.4k) |
|  | 2.45 | 2 | +8.0k (19.6k) | +10.6k (14.0k) | +10.0k (13.1k) | -2.1k (9.9k) | +4.4k (9.0k) | +4.9k (27.5k) |

#### Neighbourhood: all 18 cells at the LIVE-CAL stop (2.45), N target basis, vs market

| cell | L3M | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| F0.7 X3 gate | +16.1k (24.4k) | +15.1k (15.8k) | +16.0k (14.7k) | +3.8k (11.2k) | +2.5k (8.4k) |
| F0.7 X3 nogate | +8.8k (17.6k) | +8.7k (13.5k) | +10.5k (12.9k) | +2.7k (9.9k) | +2.1k (8.7k) |
| F0.7 X5 gate | +25.9k (23.4k) | +22.0k (16.7k) | +21.4k (15.4k) | -0.4k (10.6k) | +3.1k (12.2k) |
| F0.7 X5 nogate | +25.3k (20.1k) | +21.7k (15.0k) | +20.9k (14.0k) | -1.0k (11.5k) | +3.3k (11.9k) |
| F0.7 X8 gate | +36.1k (28.9k) | +26.4k (22.8k) | +23.6k (21.0k) | -6.4k (13.1k) | +4.5k (14.7k) |
| F0.7 X8 nogate | +32.5k (34.3k) | +25.5k (23.8k) | +24.0k (21.5k) | -2.8k (12.8k) | +5.5k (13.9k) |
| F0.8 X3 gate | +19.6k (21.0k) | +14.3k (14.2k) | +14.5k (13.2k) | +4.8k (8.6k) | -0.0k (7.4k) |
| F0.8 X3 nogate | +10.8k (16.1k) | +7.4k (11.5k) | +8.7k (11.2k) | +2.9k (8.4k) | +0.4k (7.6k) |
| F0.8 X5 gate | +17.2k (20.9k) | +18.9k (15.9k) | +17.3k (14.7k) | +2.4k (9.6k) | +3.2k (9.7k) |
| F0.8 X5 nogate | +16.6k (19.7k) | +17.5k (14.0k) | +15.9k (13.2k) | +3.7k (9.5k) | +3.9k (9.5k) |
| F0.8 X8 gate | +32.5k (26.9k) | +26.5k (20.0k) | +23.7k (18.7k) | -1.3k (12.1k) | +7.6k (11.6k) |
| F0.8 X8 nogate | +29.2k (26.5k) | +25.1k (18.6k) | +23.3k (17.2k) | -1.1k (11.2k) | +6.8k (11.5k) |
| F0.9 X3 gate | +13.6k (19.2k) | +11.1k (14.3k) | +12.9k (13.6k) | +3.8k (7.1k) | +0.5k (5.7k) |
| F0.9 X3 nogate | +11.6k (17.0k) | +7.8k (11.2k) | +10.1k (11.4k) | +3.5k (6.9k) | +1.0k (6.0k) |
| F0.9 X5 gate | +14.2k (19.3k) | +12.4k (13.7k) | +12.6k (12.5k) | +4.8k (6.9k) | +2.1k (8.1k) |
| F0.9 X5 nogate | +12.9k (17.7k) | +11.2k (12.5k) | +11.3k (11.7k) | +4.9k (7.3k) | +3.3k (7.8k) |
| F0.9 X8 gate | +16.6k (21.0k) | +16.9k (13.8k) | +15.6k (13.3k) | +2.1k (10.0k) | +6.8k (9.1k) |
| F0.9 X8 nogate | +17.8k (20.3k) | +17.1k (13.4k) | +16.1k (12.7k) | +3.0k (9.9k) | +7.5k (9.0k) |

Reading: (1) **the stop-join fix is worth the same to both cells and to the market**: 0.5 vs 2.45 changes the split's delta vs the market by 0.7-2.0k/wk (the market pays the stop cost too; the split carries slightly more lots into stops), never a sign. The extra 1.9 pt per stop is paid by the whole stack, not by the entry choice - the lever is on the execution side (LIVE_STOP_JOIN.md), not in the split. (2) C90 vs C70 is flat at the measured cost: L6M +0.4k / +2.0k, HOLD -1.8k / +0.2k, PRE -0.8k / -0.9k (stop 0.5 / 2.45, MDE 9-13k). (3) The cost-robustness claim holds and is the only separation: at +1 pt per remainder fill the split loses PRE and X' (it is the PRE-selected L2SE cell's known fragility) while C90 stays at +1.6k / 0.0k in PRE and +7.1k / +5.7k in X' (stop 0.5 / 2.45); at +2 pt C70 is +1.5k / +3.9k L6M and C90 +11.7k / +10.6k. (4) The paired difference turns negative only when stops are very expensive (S >= 3.5: C90 -6.5k L6M, MDE 11k - inside noise; the S >= 3.5 columns are also non-monotone for the market and C70 (C70 L6M +17.0k at 1.5, +15.1k at 2.45, +17.7k at 3.5), so read them as noise around a flat line, not as a trend; the mechanism was not isolated). (5) 90/10 uses less of the book: 10% of the lots are tradeable only on the 8-pt dip (fill 83% vs 92%), the D6 change is just split_F 0.9 / dip_X 8 / confirmations_N 0 - no feature D6 does not already compute. (6) Neighbourhood mean (3 neighbours inside the 3x3 grid, LIVE-CAL-free N basis, L6M): C70 +16.8k, C90 +18.4k: the cells sit on a plateau.

#### Random-dip placebo (adds at random seconds; same time-since-entry distribution, permuted within book; 100 draws; stack delta vs the lot-matched line; rank = share of placebo draws below the real cell)

| cell | L3M | L6M | HOLD | PRE | X' | 2026 | placebo mean L6M |
|--|--|--|--|--|--|--|--|
| S73 split (N) | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 0.98 | -13.4k |
| C90 split (N) | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 0.94 | -4.6k |

## 5. (d) The split on the confirmation base: 70% at the confirmation print, 30% on the dip after it (Group D: 105 cells; PRE u X' selection file `gd_selection_PRE_X.json`)
Confirmation = the first same-direction event of a CF-ENG stream (`out/confirm/streams/s1_<fam>_<tf>.parquet`, FVG / iFVG / iplFVG / OB / BRK at 15 s, 30 s, 45 s, 1 m, 2 m, 3 m, 5 m) knowable after the signal and before the held trade's stop/target/arm end; slice 1 (70%, or 100% in D3) is bought at the next print second (close + 1 tick); the 30% add is the same gated / ungated 3-pt dip measured from the confirmation fill; stop at the ORIGINAL level; unconfirmed signals are skipped. D1 gate, D2 no gate, D3 pure wait 100% at the confirmation. Selected on PRE u X' (pooled top 3 + per-book top 1 of 105 by week-clustered t of the excess over the lot-matched market): [["FVG", "2m", "D3"], ["FVG", "2m", "D1"], ["FVG", "2m", "D2"]] and per book {"HM": ["OB", "30s", "D3"], "KB": ["FVG", "15s", "D3"], "PE": ["OB", "45s", "D2"], "SM": ["FVG", "15s", "D3"], "ST": ["OB", "3m", "D3"], "WT": ["iplFVG", "30s", "D3"]}. Reference = D0, the signal-anchored S73.

#### Population (all 35 definitions, mean excess per planned lot over the lot-matched market; kept share L6M) - looked once, not used for selection

| variant | L3M | L6M | HOLD | PRE | X' | 2026 | kept |
|--|--|--|--|--|--|--|--|
| D1 | +0.093 | -0.028 | -0.028 | -0.067 | -0.355 | -0.538 | 70% |
| D2 | +0.063 | -0.036 | -0.034 | -0.060 | -0.345 | -0.625 | 70% |
| D3 | +0.155 | +0.035 | +0.023 | +0.009 | -0.375 | -0.582 | 70% |
| D0 signal-anchored S73 | -0.106 | +0.074 | +0.113 | +0.069 | -0.099 | +0.073 | 100% |

#### The selected cells on the lock engine ($k/wk vs the stack as it is, N; MDE); per planned lot / per contract and kept share in L6M; mean market pts of the skipped signals

| cell (fam_tf_variant) | vs market L3M | vs market L6M | vs market HOLD | vs market PRE | vs market X' | vs market 2026 | vs S73 L6M | vs S73 PRE | L6M pts/planned lot / per contract | kept L6M | skipped signals' market pts | LC L6M | LJ L6M |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| FVG_15s_D3 | +2.1k (40.7k) | -4.8k (32.5k) | -7.3k (28.5k) | -13.8k (19.0k) | +1.2k (19.0k) | +8.1k (60.7k) | -22.4k | -17.6k | 2.50 / 2.67 | 93% | -31.1 | -3.6k | -9.8k |
| FVG_2m_D1 | -11.5k (57.2k) | -11.8k (41.5k) | -4.5k (37.9k) | -14.5k (26.3k) | -14.0k (23.7k) | +14.2k (90.2k) | -29.4k | -18.3k | 1.79 / 2.41 | 76% | -20.3 | -12.3k | -13.7k |
| FVG_2m_D2 | -15.3k (56.1k) | -13.4k (41.3k) | -5.7k (37.8k) | -14.2k (26.5k) | -13.9k (24.3k) | +8.6k (88.2k) | -30.9k | -17.9k | 1.79 / 2.40 | 76% | -20.3 | -13.4k | -15.6k |
| FVG_2m_D3 | -21.7k (66.9k) | -19.0k (45.8k) | -10.9k (41.6k) | -13.4k (27.2k) | -20.5k (24.4k) | +1.8k (105.9k) | -36.6k | -17.2k | 1.72 / 2.26 | 76% | -20.3 | -20.2k | -20.2k |
| OB_30s_D3 | -19.3k (57.1k) | -35.4k (43.7k) | -30.0k (40.3k) | -23.6k (23.5k) | -6.5k (26.5k) | -25.8k (106.8k) | -53.0k | -27.4k | 1.92 / 2.44 | 79% | -16.4 | -34.0k | -36.1k |
| OB_3m_D3 | -23.8k (77.3k) | -32.6k (69.2k) | -23.2k (66.1k) | -13.5k (31.1k) | -25.4k (35.9k) | -41.3k (107.4k) | -50.2k | -17.3k | 1.10 / 2.42 | 46% | -8.7 | -26.1k | -35.8k |
| OB_45s_D2 | +7.5k (62.7k) | -10.9k (46.2k) | -5.5k (42.9k) | -24.8k (26.6k) | -6.7k (27.1k) | +19.3k (114.1k) | -28.5k | -28.6k | 1.95 / 2.75 | 72% | -14.2 | -9.6k | -13.5k |
| iplFVG_30s_D3 | -6.9k (62.3k) | -24.8k (46.7k) | -21.6k (40.9k) | -17.0k (21.3k) | -6.3k (23.6k) | +12.6k (140.4k) | -42.4k | -20.8k | 2.23 / 2.47 | 90% | -24.6 | -31.6k | -24.7k |

#### Controls: stack delta vs the lot-matched line, real event / mean of 5 time-matched random-event draws ($k/wk)

| cell | L6M real / random | HOLD | PRE | X' |
|--|--|--|--|--|
| FVG_15s_D3 | -1.0k / -4.0k | -4.4k / -3.5k | -10.5k / -10.2k | +2.2k / -4.8k |
| FVG_2m_D1 | +2.9k / +4.6k | +6.9k / +4.4k | -1.2k / -10.7k | -10.1k / +1.0k |
| FVG_2m_D2 | +1.2k / +6.0k | +5.6k / +5.4k | -0.9k / -10.5k | -10.0k / +1.1k |
| FVG_2m_D3 | -5.3k / +12.2k | -0.3k / +10.2k | -1.0k / -5.3k | -16.9k / +1.2k |
| OB_30s_D3 | -23.1k / -0.6k | -20.8k / -3.3k | -13.0k / -12.2k | -3.3k / -5.3k |
| OB_3m_D3 | -0.5k / +11.1k | +1.6k / +6.5k | +16.3k / +8.3k | -17.5k / -3.7k |
| OB_45s_D2 | +5.4k / -5.9k | +6.9k / -8.9k | -10.5k / -16.2k | -2.6k / -4.9k |
| iplFVG_30s_D3 | -19.4k / -3.1k | -17.5k / -3.2k | -12.5k / -11.1k | -4.9k / -5.2k |

Reading: the confirmation base is worse than the signal base in every window that matters. The mechanism is the CF-ENG one: waiting skips the signals that run away without confirming (they are the winners as often as the losers on the lock engine), delays the fill of the kept ones, and the dip add measured from a later price is a different, worse trade (D1 -0.15 per planned lot pooled PRE u X' vs +0.03 at the signal). The three best definitions per PRE u X' (FVG 2m, OB 30s/3m/45s, FVG 15s pure wait) do not carry to the recent windows (-4.8k .. -35.4k L6M, PRE -13k .. -25k, and the PRE u X' pick is not the PRE winner of the time-matched random control). Tier: DEAD. The 70/30 split remains a signal-second construction.

## 6. (e) The split with the first-stop rule and the ER sizer on the lock-engine stack = the Sunday stack line (Group E: 27 lines per basis)
Components, all on the SP-1 simulator (`stackpart/sp_sim.py` -> exact per-book lock engine; the S2 stack module `code/stack2/` and T2 sizer `code/trend2/` published scripts but no import API at this writing, so the composition uses SP-1's first-stop rule kind 4 type 2 and a placeholder ER sizer identical in form to T2's F1/2L cells: lots x 0.5 when 5-min ER(20) < 0.3, x 1.0 above ("er_05_10"), or x 1.5 when ER >= 0.45 ("er_05_10_15"); the first-stop rule: at the second a same-side book is stopped, market-exit 50% (or 100%) of the other same-side books next second). Split: MKT (stack as it is) | S73 | C90 (S* = the best of A0-A7 and C90 by PRE u X' week-weighted stack delta, chosen before any recent window: {"A0": 3186, "A1": 2747, "A2": 187, "A3": 1184, "A4": 1274, "A5": 404, "A6": 1821, "A7": 1805, "C90": 5136} -> **C90**). Prereg headline = C90 + cut50 + ER 0.5/1.0.

#### THE SUNDAY STACK LINE, basis N (primary): weekly mean / SD / maxDD / worst-20 ($k, research lots), recent first; delta vs as-is (MDE)

| line | window | mean $k/wk | SD | maxDD | worst-20 (sum) | delta vs as-is (MDE) | delta vs lot-matched line | lot factor vs market |
|--|--|--|--|--|--|--|--|--|
| as it is (market entries, no rule) | L3M | 11.0 | 140 | 372 | 155 | - | - | 1.00 |
|  | L6M | 61.5 | 146 | 372 | -153 | - | - |  |
|  | HOLD | 48.3 | 173 | 651 | -1095 | - | - |  |
|  | PRE | 58.0 | 139 | 704 | -2418 | - | - |  |
|  | X' | 16.0 | 104 | 490 | -1457 | - | - |  |
|  | 2026 | 18.9 | 186 | 346 | 114 | - | - |  |
| 70/30@3 split only | L3M | 31.3 | 130 | 319 | 438 | +20.2k (25.2k) | +20.2k | 1.00 |
|  | L6M | 79.1 | 137 | 319 | 332 | +17.6k (16.6k) | +17.7k |  |
|  | HOLD | 66.7 | 169 | 625 | -630 | +18.4k (15.3k) | +18.4k |  |
|  | PRE | 61.8 | 139 | 617 | -2307 | +3.8k (10.7k) | +3.8k |  |
|  | X' | 18.2 | 102 | 469 | -1392 | +2.2k (8.4k) | +2.2k |  |
|  | 2026 | 37.0 | 185 | 306 | 222 | +18.1k (40.6k) | +18.2k |  |
| 90/10@8 split only | L3M | 28.3 | 143 | 344 | 396 | +17.2k (18.9k) | +17.3k | 1.00 |
|  | L6M | 78.5 | 145 | 344 | 208 | +17.1k (12.9k) | +17.2k |  |
|  | HOLD | 64.1 | 179 | 685 | -810 | +15.8k (12.6k) | +15.8k |  |
|  | PRE | 61.3 | 136 | 576 | -2150 | +3.2k (9.8k) | +3.3k |  |
|  | X' | 24.4 | 99 | 448 | -1245 | +8.4k (9.1k) | +8.4k |  |
|  | 2026 | 46.7 | 197 | 305 | 280 | +27.7k (26.3k) | +27.9k |  |
| first-stop cut50 only | L3M | 46.8 | 153 | 472 | 655 | +35.7k (44.3k) | +35.7k | 1.00 |
|  | L6M | 84.5 | 144 | 472 | 312 | +23.0k (28.5k) | +23.0k |  |
|  | HOLD | 67.7 | 179 | 708 | -824 | +19.3k (26.1k) | +19.3k |  |
|  | PRE | 49.8 | 133 | 668 | -2303 | -8.2k (15.4k) | -8.2k |  |
|  | X' | 16.7 | 105 | 426 | -1483 | +0.7k (17.9k) | +0.7k |  |
|  | 2026 | 88.0 | 170 | 245 | 528 | +69.1k (54.0k) | +69.1k |  |
| ER sizer 0.5/1.0 only | L3M | 49.6 | 133 | 394 | 695 | +38.6k (58.5k) | +41.8k | 0.70 |
|  | L6M | 77.5 | 117 | 394 | 499 | +16.1k (41.7k) | +35.0k |  |
|  | HOLD | 64.2 | 140 | 470 | -339 | +15.9k (38.3k) | +30.6k |  |
|  | PRE | 46.7 | 125 | 388 | -2108 | -11.4k (18.3k) | +6.2k |  |
|  | X' | 15.4 | 91 | 395 | -1237 | -0.6k (21.4k) | +4.2k |  |
|  | 2026 | 84.5 | 153 | 219 | 507 | +65.5k (123.7k) | +71.8k |  |
| S73 + cut50 + ER 0.5/1.0 | L3M | 46.2 | 123 | 485 | 646 | +35.1k (57.9k) | +38.4k | 0.70 |
|  | L6M | 74.2 | 109 | 485 | 515 | +12.7k (44.2k) | +31.7k |  |
|  | HOLD | 60.8 | 134 | 485 | -299 | +12.4k (40.9k) | +27.2k |  |
|  | PRE | 44.3 | 116 | 367 | -1806 | -13.8k (23.0k) | +3.8k |  |
|  | X' | 12.3 | 85 | 381 | -1191 | -3.8k (23.6k) | +1.1k |  |
|  | 2026 | 90.0 | 141 | 232 | 540 | +71.1k (104.9k) | +77.4k |  |
| **C90 + cut50 + ER 0.5/1.0 (prereg headline)** | L3M | 55.1 | 128 | 448 | 771 | +44.0k (56.1k) | +47.3k | 0.70 |
|  | L6M | 78.7 | 113 | 448 | 513 | +17.2k (43.9k) | +36.3k |  |
|  | HOLD | 64.5 | 138 | 494 | -332 | +16.1k (40.0k) | +30.9k |  |
|  | PRE | 43.2 | 116 | 355 | -1799 | -14.9k (23.0k) | +2.8k |  |
|  | X' | 15.2 | 85 | 361 | -1132 | -0.8k (23.7k) | +4.1k |  |
|  | 2026 | 99.3 | 140 | 238 | 596 | +80.4k (98.4k) | +86.7k |  |
| S73 + cut50 + ER 0.5/1/1.5 | L3M | 60.3 | 130 | 406 | 844 | +49.3k (73.2k) | +51.6k | 0.78 |
|  | L6M | 87.3 | 116 | 406 | 666 | +25.9k (55.1k) | +39.9k |  |
|  | HOLD | 73.3 | 141 | 481 | -190 | +25.0k (49.7k) | +35.8k |  |
|  | PRE | 46.6 | 130 | 405 | -2074 | -11.4k (24.8k) | +1.4k |  |
|  | X' | 19.4 | 105 | 374 | -1402 | +3.4k (26.1k) | +6.9k |  |
|  | 2026 | 95.5 | 148 | 249 | 573 | +76.6k (153.6k) | +81.7k |  |
| C90 + cut50 + ER 0.5/1/1.5 | L3M | 73.8 | 132 | 335 | 1033 | +62.7k (67.7k) | +65.0k | 0.78 |
|  | L6M | 96.3 | 119 | 335 | 766 | +34.8k (50.0k) | +48.9k |  |
|  | HOLD | 82.3 | 148 | 504 | -148 | +34.0k (44.4k) | +44.8k |  |
|  | PRE | 52.5 | 133 | 374 | -1988 | -5.6k (25.2k) | +7.2k |  |
|  | X' | 23.4 | 103 | 340 | -1283 | +7.4k (25.5k) | +10.9k |  |
|  | 2026 | 96.9 | 153 | 278 | 581 | +77.9k (138.3k) | +83.1k |  |

#### THE SUNDAY STACK LINE, basis LIVE-CAL (stop 2.45): weekly mean / SD / maxDD / worst-20 ($k, research lots), recent first; delta vs as-is (MDE)

| line | window | mean $k/wk | SD | maxDD | worst-20 (sum) | delta vs as-is (MDE) | delta vs lot-matched line | lot factor vs market |
|--|--|--|--|--|--|--|--|--|
| as it is (market entries, no rule) | L3M | -1.0 | 141 | 417 | -14 | - | - | 1.00 |
|  | L6M | 50.0 | 145 | 417 | -372 | - | - |  |
|  | HOLD | 37.2 | 173 | 684 | -1321 | - | - |  |
|  | PRE | 46.1 | 137 | 778 | -2620 | - | - |  |
|  | X' | 7.0 | 104 | 560 | -1661 | - | - |  |
|  | 2026 | 11.5 | 187 | 371 | 69 | - | - |  |
| 70/30@3 split only | L3M | 15.1 | 135 | 363 | 211 | +16.1k (24.4k) | +16.1k | 1.00 |
|  | L6M | 65.1 | 139 | 363 | 51 | +15.1k (15.8k) | +15.2k |  |
|  | HOLD | 53.2 | 171 | 658 | -927 | +16.0k (14.7k) | +16.0k |  |
|  | PRE | 49.9 | 140 | 707 | -2543 | +3.8k (11.2k) | +3.8k |  |
|  | X' | 9.5 | 103 | 525 | -1599 | +2.5k (8.4k) | +2.5k |  |
|  | 2026 | 26.0 | 192 | 322 | 156 | +14.6k (40.3k) | +14.7k |  |
| 90/10@8 split only | L3M | 16.8 | 145 | 369 | 235 | +17.8k (20.3k) | +17.8k | 1.00 |
|  | L6M | 67.1 | 146 | 369 | -38 | +17.1k (13.4k) | +17.2k |  |
|  | HOLD | 53.3 | 179 | 697 | -1047 | +16.1k (12.7k) | +16.2k |  |
|  | PRE | 49.1 | 136 | 677 | -2403 | +3.0k (9.9k) | +3.0k |  |
|  | X' | 14.5 | 100 | 492 | -1467 | +7.5k (9.0k) | +7.5k |  |
|  | 2026 | 30.2 | 200 | 358 | 181 | +18.8k (29.3k) | +18.9k |  |
| first-stop cut50 only | L3M | 28.6 | 151 | 515 | 400 | +29.6k (41.5k) | +29.6k | 1.00 |
|  | L6M | 70.6 | 143 | 515 | 67 | +20.6k (25.7k) | +20.6k |  |
|  | HOLD | 54.9 | 178 | 731 | -1019 | +17.7k (23.4k) | +17.7k |  |
|  | PRE | 39.8 | 132 | 667 | -2412 | -6.4k (14.0k) | -6.4k |  |
|  | X' | 8.4 | 103 | 497 | -1625 | +1.4k (17.4k) | +1.4k |  |
|  | 2026 | 77.2 | 178 | 272 | 463 | +65.7k (49.2k) | +65.7k |  |
| ER sizer 0.5/1.0 only | L3M | 34.6 | 127 | 428 | 485 | +35.7k (51.8k) | +35.2k | 0.70 |
|  | L6M | 64.0 | 115 | 428 | 275 | +14.0k (39.8k) | +29.4k |  |
|  | HOLD | 51.2 | 138 | 496 | -559 | +14.0k (37.0k) | +25.3k |  |
|  | PRE | 36.9 | 126 | 421 | -2355 | -9.2k (17.8k) | +4.7k |  |
|  | X' | 8.5 | 91 | 437 | -1391 | +1.5k (22.0k) | +3.6k |  |
|  | 2026 | 63.5 | 142 | 232 | 381 | +52.1k (112.4k) | +56.1k |  |
| S73 + cut50 + ER 0.5/1.0 | L3M | 38.9 | 123 | 506 | 545 | +39.9k (56.4k) | +39.5k | 0.70 |
|  | L6M | 66.7 | 109 | 506 | 375 | +16.7k (43.4k) | +32.2k |  |
|  | HOLD | 53.9 | 132 | 506 | -438 | +16.7k (40.4k) | +28.0k |  |
|  | PRE | 36.2 | 117 | 403 | -2029 | -10.0k (22.2k) | +3.9k |  |
|  | X' | 5.2 | 83 | 437 | -1304 | -1.9k (24.0k) | +0.2k |  |
|  | 2026 | 84.1 | 143 | 230 | 505 | +72.7k (105.3k) | +76.8k |  |
| **C90 + cut50 + ER 0.5/1.0 (prereg headline)** | L3M | 43.5 | 127 | 497 | 609 | +44.6k (55.1k) | +44.1k | 0.70 |
|  | L6M | 68.6 | 113 | 497 | 318 | +18.6k (42.5k) | +34.1k |  |
|  | HOLD | 54.9 | 138 | 508 | -517 | +17.7k (39.0k) | +29.0k |  |
|  | PRE | 36.2 | 118 | 376 | -2007 | -10.0k (22.0k) | +4.0k |  |
|  | X' | 9.0 | 85 | 394 | -1258 | +2.0k (24.2k) | +4.1k |  |
|  | 2026 | 91.7 | 142 | 236 | 550 | +80.3k (97.7k) | +84.4k |  |
| S73 + cut50 + ER 0.5/1/1.5 | L3M | 53.0 | 129 | 429 | 742 | +54.1k (70.8k) | +53.7k | 0.78 |
|  | L6M | 80.5 | 115 | 429 | 526 | +30.5k (53.4k) | +42.0k |  |
|  | HOLD | 66.4 | 140 | 503 | -334 | +29.2k (48.4k) | +37.5k |  |
|  | PRE | 37.3 | 130 | 463 | -2303 | -8.8k (25.0k) | +1.2k |  |
|  | X' | 13.3 | 104 | 421 | -1499 | +6.3k (26.5k) | +7.8k |  |
|  | 2026 | 87.7 | 147 | 259 | 526 | +76.2k (144.7k) | +79.8k |  |
| C90 + cut50 + ER 0.5/1/1.5 | L3M | 59.9 | 135 | 370 | 839 | +60.9k (68.0k) | +60.6k | 0.78 |
|  | L6M | 85.8 | 120 | 370 | 523 | +35.8k (49.6k) | +47.3k |  |
|  | HOLD | 72.1 | 149 | 529 | -400 | +34.9k (44.2k) | +43.2k |  |
|  | PRE | 41.4 | 133 | 392 | -2255 | -4.8k (25.0k) | +5.3k |  |
|  | X' | 17.9 | 102 | 384 | -1386 | +10.9k (25.7k) | +12.4k |  |
|  | 2026 | 84.3 | 158 | 288 | 506 | +72.8k (134.4k) | +76.4k |  |

#### THE SUNDAY STACK LINE, basis LIVE-JOIN (stop 0.5): weekly mean / SD / maxDD / worst-20 ($k, research lots), recent first; delta vs as-is (MDE)

| line | window | mean $k/wk | SD | maxDD | worst-20 (sum) | delta vs as-is (MDE) | delta vs lot-matched line | lot factor vs market |
|--|--|--|--|--|--|--|--|--|
| as it is (market entries, no rule) | L3M | 19.0 | 144 | 360 | 266 | - | - | 1.00 |
|  | L6M | 67.1 | 147 | 360 | -45 | - | - |  |
|  | HOLD | 53.7 | 174 | 640 | -984 | - | - |  |
|  | PRE | 61.5 | 138 | 666 | -2333 | - | - |  |
|  | X' | 19.0 | 103 | 470 | -1389 | - | - |  |
|  | 2026 | 33.0 | 193 | 300 | 198 | - | - |  |
| 70/30@3 split only | L3M | 33.7 | 130 | 312 | 471 | +14.7k (30.2k) | +14.7k | 1.00 |
|  | L6M | 81.5 | 137 | 312 | 376 | +14.4k (18.5k) | +14.5k |  |
|  | HOLD | 69.4 | 169 | 613 | -580 | +15.6k (16.9k) | +15.7k |  |
|  | PRE | 65.3 | 138 | 572 | -2228 | +3.8k (10.8k) | +3.9k |  |
|  | X' | 21.0 | 101 | 451 | -1323 | +1.9k (8.6k) | +1.9k |  |
|  | 2026 | 37.8 | 185 | 301 | 227 | +4.8k (55.5k) | +5.0k |  |
| 90/10@8 split only | L3M | 31.7 | 143 | 337 | 444 | +12.7k (19.4k) | +12.8k | 1.00 |
|  | L6M | 81.9 | 145 | 337 | 279 | +14.8k (13.1k) | +15.0k |  |
|  | HOLD | 67.5 | 178 | 672 | -734 | +13.8k (12.7k) | +13.9k |  |
|  | PRE | 64.5 | 136 | 556 | -2076 | +3.0k (9.8k) | +3.1k |  |
|  | X' | 27.8 | 99 | 427 | -1173 | +8.7k (9.4k) | +8.8k |  |
|  | 2026 | 50.3 | 197 | 299 | 302 | +17.4k (32.6k) | +17.5k |  |
| first-stop cut50 only | L3M | 49.0 | 152 | 467 | 686 | +30.0k (44.5k) | +30.0k | 1.00 |
|  | L6M | 87.1 | 144 | 467 | 365 | +20.0k (28.5k) | +20.0k |  |
|  | HOLD | 70.4 | 178 | 697 | -765 | +16.7k (25.9k) | +16.7k |  |
|  | PRE | 54.1 | 134 | 608 | -2222 | -7.4k (15.7k) | -7.4k |  |
|  | X' | 18.9 | 105 | 408 | -1441 | -0.1k (17.8k) | -0.1k |  |
|  | 2026 | 90.2 | 169 | 250 | 541 | +57.3k (61.9k) | +57.3k |  |
| ER sizer 0.5/1.0 only | L3M | 53.1 | 133 | 381 | 744 | +34.1k (61.1k) | +39.8k | 0.70 |
|  | L6M | 80.9 | 117 | 381 | 567 | +13.8k (42.2k) | +34.4k |  |
|  | HOLD | 67.5 | 140 | 460 | -267 | +13.8k (38.8k) | +30.1k |  |
|  | PRE | 50.5 | 125 | 371 | -2002 | -11.0k (18.2k) | +7.7k |  |
|  | X' | 18.1 | 90 | 378 | -1178 | -1.0k (21.4k) | +4.8k |  |
|  | 2026 | 88.4 | 153 | 214 | 530 | +55.4k (134.2k) | +65.9k |  |
| S73 + cut50 + ER 0.5/1.0 | L3M | 48.0 | 124 | 484 | 672 | +29.0k (60.0k) | +34.7k | 0.70 |
|  | L6M | 76.0 | 109 | 484 | 542 | +8.8k (45.3k) | +29.6k |  |
|  | HOLD | 62.6 | 133 | 484 | -269 | +8.9k (41.9k) | +25.3k |  |
|  | PRE | 47.5 | 116 | 356 | -1735 | -14.0k (22.9k) | +4.6k |  |
|  | X' | 14.8 | 84 | 366 | -1127 | -4.3k (23.4k) | +1.5k |  |
|  | 2026 | 93.2 | 141 | 228 | 559 | +60.2k (114.7k) | +70.8k |  |
| **C90 + cut50 + ER 0.5/1.0 (prereg headline)** | L3M | 58.9 | 127 | 436 | 825 | +40.0k (57.2k) | +45.6k | 0.70 |
|  | L6M | 82.1 | 112 | 436 | 576 | +15.0k (44.4k) | +35.8k |  |
|  | HOLD | 67.8 | 138 | 486 | -266 | +14.1k (40.4k) | +30.5k |  |
|  | PRE | 45.8 | 116 | 350 | -1739 | -15.7k (23.1k) | +3.0k |  |
|  | X' | 17.5 | 84 | 349 | -1068 | -1.5k (23.4k) | +4.3k |  |
|  | 2026 | 103.9 | 140 | 234 | 623 | +70.9k (106.1k) | +81.5k |  |
| S73 + cut50 + ER 0.5/1/1.5 | L3M | 63.5 | 129 | 397 | 890 | +44.5k (78.5k) | +48.6k | 0.78 |
|  | L6M | 90.2 | 115 | 397 | 717 | +23.1k (57.2k) | +38.5k |  |
|  | HOLD | 76.8 | 140 | 452 | -113 | +23.1k (51.7k) | +35.1k |  |
|  | PRE | 49.7 | 130 | 388 | -1994 | -11.8k (25.2k) | +1.8k |  |
|  | X' | 22.1 | 104 | 345 | -1315 | +3.1k (25.8k) | +7.3k |  |
|  | 2026 | 99.5 | 145 | 233 | 597 | +66.5k (170.9k) | +74.8k |  |
| C90 + cut50 + ER 0.5/1/1.5 | L3M | 78.0 | 130 | 328 | 1092 | +59.0k (73.4k) | +63.1k | 0.78 |
|  | L6M | 99.8 | 117 | 328 | 843 | +32.7k (52.2k) | +48.0k |  |
|  | HOLD | 86.0 | 147 | 485 | -64 | +32.3k (46.5k) | +44.3k |  |
|  | PRE | 54.6 | 132 | 371 | -1917 | -6.9k (25.3k) | +6.7k |  |
|  | X' | 25.4 | 103 | 333 | -1222 | +6.3k (25.2k) | +10.5k |  |
|  | 2026 | 101.6 | 150 | 262 | 610 | +68.6k (156.0k) | +76.9k |  |

#### THE SUNDAY STACK LINE AT EQUAL RISK (STRUCTURE: every line is scaled by one factor c* so that its worst-20-weeks over WF = PRE u HOLD equals the stack as it is - the EQR frame of DS3_EQUAL_RISK.md, which this reproduces: S73 alone c* 1.06, +22.6k L6M / +22.6k HOLD / +7.7k PRE / +3.3k X'; C90 alone 1.09, +24.4k / +21.7k / +8.9k / +10.7k = the UF-ENTRY C1 row). Delta vs the stack as it is, $k/wk (MDE); WF SD and maxDD of the scaled line vs as-is beside. EQR caveat stands: the factor CI is +-20-30% and equal risk does not transfer out of sample.

| basis | line | c* (w20-matched) | L3M | L6M | HOLD | PRE | X' | 2026 | WF SD scaled / as-is | WF maxDD scaled / as-is | L6M if matched on SD instead |
|--|--|--|--|--|--|--|--|--|--|--|--|
| N | 70/30@3 only | 1.06 | +22.2k (25.0k) | +22.6k (16.4k) | +22.6k (16.0k) | +7.7k (11.4k) | +3.3k (8.8k) | +20.5k (43.8k) | 158k / 150k | 664k / 704k | +18.3k (16.5k) |
|  | 90/10@8 only | 1.09 | +19.9k (23.2k) | +24.4k (15.1k) | +21.7k (17.0k) | +8.9k (10.6k) | +10.7k (9.5k) | +32.1k (41.5k) | 164k / 150k | 748k / 704k | +16.9k (12.9k) |
|  | first-stop cut50 only | 1.05 | +38.1k (47.0k) | +27.3k (29.4k) | +22.8k (27.6k) | -5.7k (15.7k) | +1.5k (18.5k) | +73.6k (52.7k) | 156k / 150k | 744k / 704k | +23.8k (28.7k) |
|  | ER sizer 0.5/1.0 only | 1.23 | +49.9k (67.0k) | +33.7k (43.0k) | +30.5k (38.5k) | -0.7k (20.3k) | +2.9k (23.2k) | +84.8k (130.6k) | 160k / 150k | 577k / 704k | +28.1k (42.1k) |
|  | S73 + cut50 + ER 0.5/1.0 | 1.39 | +53.3k (70.9k) | +41.9k (46.7k) | +36.3k (43.0k) | +3.6k (26.7k) | +1.1k (27.0k) | +106.5k (108.5k) | 169k / 150k | 675k / 704k | +30.3k (44.4k) |
|  | **C90 + cut50 + ER 0.5/1.0 (prereg headline)** | 1.39 | +65.7k (71.4k) | +48.2k (47.8k) | +41.5k (43.6k) | +2.2k (26.7k) | +5.2k (27.0k) | +119.5k (98.8k) | 172k / 150k | 688k / 704k | +34.4k (44.6k) |
|  | C90 + cut50 + ER 0.5/1/1.5 | 1.33 | +86.9k (82.3k) | +66.4k (55.6k) | +61.0k (50.6k) | +11.6k (31.5k) | +15.1k (32.5k) | +109.7k (154.9k) | 185k / 150k | 670k / 704k | +42.5k (50.6k) |
| LC | 70/30@3 only | 1.05 | +16.9k (24.7k) | +18.7k (15.9k) | +18.9k (15.5k) | +6.5k (11.9k) | +3.0k (8.8k) | +16.0k (44.4k) | 158k / 149k | 746k / 778k | +14.8k (15.8k) |
|  | 90/10@8 only | 1.07 | +19.0k (23.5k) | +22.0k (15.2k) | +20.0k (15.8k) | +6.5k (10.5k) | +8.5k (9.3k) | +21.0k (40.7k) | 161k / 149k | 748k / 778k | +16.6k (13.3k) |
|  | first-stop cut50 only | 1.07 | +31.6k (44.9k) | +25.5k (27.0k) | +21.5k (25.7k) | -3.6k (14.3k) | +1.9k (18.2k) | +71.1k (49.7k) | 158k / 149k | 781k / 778k | +21.4k (25.9k) |
|  | ER sizer 0.5/1.0 only | 1.20 | +42.7k (56.6k) | +27.0k (40.2k) | +24.5k (36.1k) | -1.7k (19.6k) | +3.2k (23.5k) | +65.0k (111.1k) | 156k / 149k | 597k / 778k | +23.6k (39.7k) |
|  | S73 + cut50 + ER 0.5/1.0 | 1.38 | +54.8k (68.3k) | +42.3k (46.0k) | +37.3k (41.7k) | +3.9k (26.1k) | +0.1k (26.6k) | +104.9k (109.6k) | 169k / 149k | 700k / 778k | +31.6k (43.6k) |
|  | **C90 + cut50 + ER 0.5/1.0 (prereg headline)** | 1.38 | +61.1k (68.8k) | +44.7k (46.4k) | +38.6k (41.9k) | +3.8k (26.2k) | +5.5k (27.3k) | +115.2k (98.0k) | 172k / 149k | 701k / 778k | +32.1k (43.1k) |
|  | C90 + cut50 + ER 0.5/1/1.5 | 1.31 | +79.3k (82.0k) | +62.1k (55.2k) | +57.0k (50.1k) | +7.9k (30.8k) | +16.4k (31.9k) | +98.6k (150.5k) | 182k / 149k | 692k / 778k | +41.9k (50.3k) |
| LJ | 70/30@3 only | 1.07 | +17.1k (29.6k) | +20.3k (18.4k) | +20.6k (17.7k) | +8.6k (11.6k) | +3.4k (9.1k) | +7.6k (57.2k) | 159k / 150k | 657k / 666k | +15.4k (18.4k) |
|  | 90/10@8 only | 1.09 | +15.7k (22.3k) | +22.5k (15.1k) | +20.1k (16.9k) | +9.0k (10.8k) | +11.4k (9.8k) | +22.1k (42.2k) | 164k / 150k | 735k / 666k | +14.8k (13.1k) |
|  | first-stop cut50 only | 1.05 | +32.6k (46.8k) | +24.6k (29.2k) | +20.4k (27.4k) | -4.6k (16.1k) | +0.9k (18.4k) | +62.1k (59.4k) | 157k / 150k | 734k / 666k | +20.7k (28.5k) |
|  | ER sizer 0.5/1.0 only | 1.24 | +47.0k (69.3k) | +33.4k (43.6k) | +30.2k (38.9k) | +1.3k (20.5k) | +3.4k (23.4k) | +76.9k (140.5k) | 161k / 150k | 571k / 666k | +26.3k (42.5k) |
|  | S73 + cut50 + ER 0.5/1.0 | 1.40 | +48.2k (72.2k) | +39.2k (48.1k) | +33.9k (44.0k) | +4.9k (26.8k) | +1.6k (26.7k) | +97.4k (115.9k) | 170k / 150k | 677k / 666k | +26.7k (45.6k) |
|  | **C90 + cut50 + ER 0.5/1.0 (prereg headline)** | 1.41 | +63.8k (71.1k) | +48.3k (48.3k) | +41.5k (44.1k) | +2.8k (27.2k) | +5.6k (26.8k) | +113.0k (103.3k) | 173k / 150k | 682k / 666k | +33.0k (45.0k) |
|  | C90 + cut50 + ER 0.5/1/1.5 | 1.34 | +85.3k (87.2k) | +66.3k (57.8k) | +61.3k (52.9k) | +11.5k (31.6k) | +14.9k (32.5k) | +102.9k (171.4k) | 185k / 150k | 649k / 666k | +41.2k (52.9k) |

#### Interaction (basis N; $k/wk vs as-is): are the components additive?

| split | window | split alone vs as-is | + first-stop cut50 (incremental to the split) | + ER sizer (incremental) | + both (incremental) | sum of the two increments | interaction (both - sum) |
|--|--|--|--|--|--|--|--|
| MKT | L3M | +0.0k | +35.7k | +38.6k | +44.3k | +74.3k | -30.0k |
|  | L6M | +0.0k | +23.0k | +16.1k | +15.5k | +39.0k | -23.6k |
|  | HOLD | +0.0k | +19.3k | +15.9k | +14.8k | +35.2k | -20.4k |
|  | PRE | +0.0k | -8.2k | -11.4k | -16.1k | -19.6k | +3.5k |
|  | X' | +0.0k | +0.7k | -0.6k | -3.5k | +0.1k | -3.6k |
| S73 | L3M | +20.2k | +16.0k | +13.7k | +14.9k | +29.7k | -14.8k |
|  | L6M | +17.6k | +6.6k | -2.6k | -4.9k | +4.0k | -8.9k |
|  | HOLD | +18.4k | +4.6k | -1.4k | -5.9k | +3.2k | -9.2k |
|  | PRE | +3.8k | -6.4k | -11.9k | -17.6k | -18.2k | +0.7k |
|  | X' | +2.2k | -0.4k | -6.2k | -5.9k | -6.7k | +0.7k |
| C90 | L3M | +17.2k | +20.3k | +23.0k | +26.8k | +43.4k | -16.6k |
|  | L6M | +17.1k | +6.7k | +3.8k | +0.2k | +10.5k | -10.3k |
|  | HOLD | +15.8k | +5.1k | +4.9k | +0.4k | +10.0k | -9.6k |
|  | PRE | +3.2k | -6.6k | -9.2k | -18.1k | -15.8k | -2.3k |
|  | X' | +8.4k | -1.8k | -8.2k | -9.2k | -10.0k | +0.8k |

Reading: unscaled, the increments of cut50 and the ER sizer overlap (both are "be smaller in the bad state"): the interaction is negative in L3M / L6M / HOLD on every split (e.g. S73 L6M: cut50 +6.6k, sizer -2.6k on top of the split, both -4.9k; MKT L6M: +23.0k, +16.1k, both +15.5k). The ER-sized lines run 0.70 of the lots (0.78 with the 1.5x up-size above ER 0.45), so their unscaled delta vs the stack as it is understates them and the raw PRE (-14.9k for the headline) is mostly the 30% of lots removed; against the lot-matched line (market x 0.70) the headline is +47.3k / +36.3k / +30.9k / +2.8k / +4.1k (L3M / L6M / HOLD / PRE / X'), and at equal worst-20 risk +65.7k / +48.2k / +41.5k / +2.2k / +5.2k - positive in all five windows but at MDE size only in L6M (see the table above; on weekly-SD matching PRE is -5.4k). With the 1.5x up-size the line also leans on the regime that paid in 2025-26 (C90 + cut50 + ER 0.5/1/1.5: +34.8k L6M / +34.0k HOLD / -5.6k PRE / +7.4k X' unscaled; equal risk +66.4k / +61.0k / +11.6k / +15.1k): a candidate for the forward register, not for an ON switch.

#### Shuffled-ER placebo for the sizer inside the composition (ER permuted within book x month; 40 draws; sizer increment in $k/wk | rank among the draws)

| increment | L3M | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| ER sizer alone (market stack) | +38.6k | 0.97 | +16.1k | 1.00 | +15.9k | 1.00 | -11.4k | 0.97 | -0.6k | 0.90 |
| ER sizer on top of C90 + cut50 | +6.4k | 0.97 | -6.5k | 1.00 | -4.8k | 1.00 | -11.5k | 1.00 | -7.4k | 0.82 |

## 7. QUANT-LAYER one-page header (headline rows; N basis; stack-level cells: per-contract of final lots exists only for the split rows)
| cell | per contract delta vs market (point: L6M; [95% block-bootstrap CI over weeks, PRE u HOLD]) | stack L3M | L6M | HOLD | PRE | X' | signals / wk (engine) , fills of the add | n_cells | RC p (program) | Romano-Wolf survives | DSR (n_trials 144k) | PBO | placebo rank | neighbourhood mean | breakeven slippage | capacity | top-5%-of-trades share of gain (x total) | stack corr (weekly delta vs stack) | regime it works in | drift: positive quarters 2023Q2-2026Q1 | WF weekly-delta CI (block bootstrap by week) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| S73 split (70/30@3) | +0.07 [-0.04, +0.20] | +20.2k (25.2k) | +17.6k (16.6k) | +18.4k (15.3k) | +3.8k (10.7k) | +2.2k (8.4k) | 237 / 218 | 1 of 296 (179 stack-level) | vs S73 0.77 / vs mkt 0.002 (L6M) | 0 vs S73; 28 vs mkt | 0.04 | NOT RUN | 1.00 (100 random-dip) | +16.8k L6M (3 nbrs) | ce ~2.3 pt L6M / ~0.6 PRE | NOT MEASURED (book depth at the fill seconds) | 10.4x | -0.15 | no session positive in all 4 windows (pre session +0.40/+0.53/-0.06/+0.52 pt per planned lot L6M/HOLD/PRE/X') | 12/12 | [+2.0k, +14.8k] |
| C90 split (90/10@8) | +0.00 [-0.07, +0.09] | +17.2k (18.9k) | +17.1k (12.9k) | +15.8k (12.6k) | +3.2k (9.8k) | +8.4k (9.1k) | 237 / 197 | 1 of 296 (179 stack-level) | vs S73 0.77 / vs mkt 0.002 (L6M) | 0 vs S73; 28 vs mkt | 0.03 | NOT RUN | 1.00 (100 random-dip) | +18.4k L6M (3 nbrs) | ce > 2 pt L6M / ~1 PRE | NOT MEASURED (book depth at the fill seconds) | 85.7x | -0.09 | no session positive in all 4 windows (asia only in X') | 10/12 | [+1.1k, +12.5k] |
| first-stop cut50 (MKT) | - | +35.7k (44.3k) | +23.0k (28.5k) | +19.3k (26.1k) | -8.2k (15.4k) | +0.7k (17.9k) | 237 / 237 | 1 of 296 (179 stack-level) | vs S73 0.77 / vs mkt 0.002 (L6M) | n/a | 0.00 | NOT RUN | random-cut: SP-1 1.00 L3M / 0.56 PRE | n/a | cut: 1.3-3.7 pt (SP-1) | NOT MEASURED (book depth at the fill seconds) | n/a | -0.20 | recent regime (PRE negative unscaled) | 5/12 | [-9.8k, +9.8k] |
| ER sizer 0.5/1.0 (MKT) | - | +38.6k (58.5k) | +16.1k (41.7k) | +15.9k (38.3k) | -11.4k (18.3k) | -0.6k (21.4k) | 237 / 237 | 1 of 296 (179 stack-level) | vs S73 0.77 / vs mkt 0.002 (L6M) | n/a | 0.00 | NOT RUN | ER 1.00 L6M/HOLD (40 shuffled-ER) | n/a | n/a | NOT MEASURED (book depth at the fill seconds) | n/a | -0.51 | recent regime (PRE negative unscaled) | 6/12 | [-15.5k, +9.1k] |
| S73+cut50+ER0.5/1.0 | - | +35.1k (57.9k) | +12.7k (44.2k) | +12.4k (40.9k) | -13.8k (23.0k) | -3.8k (23.6k) | 237 / 237 | 1 of 296 (179 stack-level) | vs S73 0.77 / vs mkt 0.002 (L6M) | n/a | 0.00 | NOT RUN | ER 1.00 L6M/HOLD (40 shuffled-ER) | n/a | n/a | NOT MEASURED (book depth at the fill seconds) | n/a | -0.60 | recent regime (PRE negative unscaled) | 5/12 | [-20.7k, +7.8k] |
| C90+cut50+ER0.5/1.0 (prereg headline) | - | +44.0k (56.1k) | +17.2k (43.9k) | +16.1k (40.0k) | -14.9k (23.0k) | -0.8k (23.7k) | 237 / 237 | 1 of 296 (179 stack-level) | vs S73 0.77 / vs mkt 0.002 (L6M) | n/a | 0.00 | NOT RUN | ER 1.00 L6M/HOLD (40 shuffled-ER) | n/a | n/a | NOT MEASURED (book depth at the fill seconds) | n/a | -0.58 | recent regime (PRE negative unscaled) | 5/12 | [-20.5k, +8.4k] |
| C90+cut50+ER0.5/1/1.5 | - | +62.7k (67.7k) | +34.8k (50.0k) | +34.0k (44.4k) | -5.6k (25.2k) | +7.4k (25.5k) | 237 / 237 | 1 of 296 (179 stack-level) | vs S73 0.77 / vs mkt 0.002 (L6M) | n/a | 0.00 | NOT RUN | ER 1.00 L6M/HOLD (40 shuffled-ER) | n/a | n/a | NOT MEASURED (book depth at the fill seconds) | n/a | -0.41 | recent regime (PRE negative unscaled) | 8/12 | [-9.0k, +21.7k] |

Column notes: DSR is the Bailey-Lopez de Prado deflated Sharpe of the weekly delta series with the cumulative trial count 144,000 (the 143,584 stored cells + this program), so every row is ~0 by construction; PBO (CSCV) was not run for this program (no cell-by-time return matrix with a selection stage beyond the PRE u X' picks); capacity needs top-5 depth at the 70/30 add seconds, not measured; the top-5% share is the share of the gain in the WF window from the best 5% of trades (the split's gain is concentrated: the best 5% of trades are worth 10x the total net gain, i.e. the rest nets out negative - a tail-capture rule, not a steady one).

## 8. D6 mapping, trades/week and $ at live lots (live lots = research / 2.35, SP-1 mapping, unconfirmed)
| rule (D6 group / property / value) | L3M $/wk at live lots (N / LC) | L6M | HOLD | PRE |
|--|--|--|--|--|
| ENTRY split_F 0.7 / dip_X 3 / confirmations_N 1 / veto imb5<=-0.40 (S73, as D6 would run it) | +8.6k / +6.8k | +7.5k / +6.4k | +7.8k / +6.8k | +1.6k / +1.6k |
| ENTRY split_F 0.9 / dip_X 8 / confirmations_N 0 / veto imb5<=-0.40 (C90, cost-robust) | +7.3k / +7.6k | +7.3k / +7.3k | +6.7k / +6.9k | +1.4k / +1.3k |
| STACK first_stop=1 cut pct=50 (SP-1 text; CANDIDATE-RECENT) | +15.2k / +12.6k | +9.8k / +8.8k | +8.2k / +7.5k | -3.5k / -2.7k |
| SIZER 5-min ER(20): lots x0.5 below 0.3 (T2 / TG-1 carrier) | +16.4k / +15.2k | +6.8k / +6.0k | +6.7k / +6.0k | -4.8k / -3.9k |
| S73 + cut50 + ER 0.5/1.0 | +14.9k / +17.0k | +5.4k / +7.1k | +5.3k / +7.1k | -5.9k / -4.2k |
| C90 + cut50 + ER 0.5/1.0 (prereg headline) | +18.7k / +19.0k | +7.3k / +7.9k | +6.9k / +7.5k | -6.3k / -4.2k |

D6 vocabulary used: group 05 (entry) properties split_F, dip_X, confirmations_N, veto, limit_join_s (0 = market on the touch; the limit-at-arming variant has no D6 property and is not recommended); STACK section lines from SP-1 (`stack first_stop=1 books_same>=1 cut pct=50 books=others_same_side`); the ER sizer needs a 5-min Kaufman ER(20) property (3 numbers per signal, computable from the 5-min bar store; listed in DS3_THL2_NEEDS from TG-1). A per-session split_F (the directive's Asia 0.5 / NY 0.7) maps to a D6 session cell property; it is **not recommended** (A4 is noise).

#### Signals per week / adds (engine books, L6M): about 237 signals per week across the six books (237 for S73's add fill rate 92%, 83% for C90); live $ = research / 2.35.

## 9. What this means for the Sunday brief (one table)
| bucket | item | D6 property | evidence (N / LC, research lots, vs stack as it is) | tier | note |
|--|--|--|--|--|--|
| ON (already the base) | 70/30 split, dip 3 pt, 1-of-8, veto | split_F=0.7 dip_X=3 confirmations_N=1 | L6M +17.6k (16.6k) / +15.1k, HOLD +18.4k (15.3k) / +16.0k, PRE +3.8k (10.7k), 12 of 12 quarters + | CANDIDATE-RECENT | random-dip placebo 1.00; cost-fragile (+1 pt per remainder fill removes PRE and X') |
| SHADOW / switch if remainder fill cost > ~0.5 pt | 90/10, dip 8, no gate | split_F=0.9 dip_X=8 confirmations_N=0 | equal to S73 at the measured cost (paired L6M +2.0k, MDE 12.5k); at +1 / +2 pt per remainder fill L6M +14.9k / +10.6k vs S73 +8.6k / +3.9k | CANDIDATE-RECENT (vs market); BEST-AVAILABLE-NEGATIVE vs S73 | only reason to prefer it is the measured remainder fill cost (live fills of the add not yet measured: ask for the add-fill slippage from the 10-20+ live fills) |
| SHADOW | first-stop cut50 on top of the split | stack first_stop=1 cut 50% | S73 + cut50 L6M +6.6k (26.8k), HOLD +4.6k (24.0k), L3M +16.0k (35.1k), PRE -6.4k (16.0k) (SP-1) | CANDIDATE-RECENT | PRE -6k (S73 base); S2 owns the rule decision |
| SHADOW | ER(20) sizer 0.5/1.0 | sizer: 5-min ER20<0.3 lots x0.5 | alone on the market stack L6M +16.1k (41.7k), SD -20%, PRE -11.4k (18.3k) | CANDIDATE-RECENT (T2 / TG-1) | de-risk tool; shuffled-ER placebo 1.00 |
| OFF | per-session / per-ER add fraction; limit-at-arming; split on a confirmation base; all-three-at-once with the 1.5x up-size | - | section 2, 3, 5, 6 | DEAD / BEST-AVAILABLE-NEGATIVE / LEAD | the three components overlap; running all three removes the mean gain of each |

#### Open questions (non-blocking)
1. Live lots per book (SP-1 asked the same): the 2.35 research-to-live factor is an assumption. 2. The remainder (add) fill slippage on live 70/30 fills: that single number decides 70/30@3 vs 90/10@8 (break-even about +1 pt in PRE, +2.3 pt in L6M for 70/30). 3. T2 / S2 import APIs are not yet published; the composition uses SP-1's simulator and a placeholder ER sizer of T2's F1 2L form; rerun the E group with their modules when they publish (the run takes about 9 minutes: `ge_run.py`).

## 10. Bookkeeping
Dead-lookup: UFE1 contains the 90/10@8 cell and its resting variant, L2SE the F/X/N split grid, ADDUW the add structure; the lookup was run after scoring for the directive cells (they are directive-named repeats, flagged `repeat` in the appended rows); new cells here: per-session / per-ER add fraction (90), limit-at-arming with through-ticks (48 incl. neighbours), stop-cost x remainder-cost grid on the C pair (18 cells x 6 stop costs x 3 ce), confirmation-base split (105), composition (27 x 3 bases). Multiplicity: this program 296 cells (honest count incl. every variant added: +8 selection variants, +1 qh/RC run), cumulative 2,467,648. UF_TRIALS side=plan36_split2; DEAD_CELLS appended (program SPLIT2); RECENT_WINS rows `out/recent_wins/SPLIT2.csv`; D6 policy text candidate `out/split2/split2_policy_candidate.txt`; MORNING.md lines at start / interim / end.