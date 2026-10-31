# DS3_TREND_2 - PLAN36 section 3, TREND second pass: 5-min ER(20) as a SIZER (agent T2, 2026-10-30T23:47Z; INTERIM 1, part (d) pending)

Prereg `l2vast/ds3/out/trend2/T2_prereg.json` sha256 df4dad1f414bed7e8e5323bbf00bb11aae171165974312c30ea85c151c413f20 (52 sizer cells + 5 regime-switch thresholds + 4 walk-forward chains, logged in DECISIONS.md before any statistic); PRE+X' selection file `selection_SEL.csv` sha256 3d7b9b0c...1839 (logged before the recent windows were read). Code `l2vast/ds3/code/trend2/`, outputs `l2vast/ds3/out/trend2/`. Research only; UNTOUCHED never read (every frame capped at label day 20260206; the 1-min bar file was read with a `ld<=20260206` parquet filter). Own masks: X' 20230401-20240131, PRE 20240201-20250630, HOLD 20250701-20260206, L6M 20250801-20260206, L3M 20251106-20260206 (view), 2026 = 20260101-20260206 (5 real weeks, sign only). Data: the TG-1 trend store (44,370 signals, ENG6 = 29,800); ER(10/20/50) on 3m/5m/15m rebuilt with the TG-1 bar code and checked equal to the store's `5m.er*` to 0.0 on every signal.

## PAGE 1 - THE ANSWER (a null on the stack, a clean positive on the trades)

1. **Sizing keeps the volume and the trade-level gain is real; the lock-engine stack does not show it.** Sizing ENG6 lots by the 5-min ER(20) at the signal (x1.5 at ER>=t, x0.5 below, equal-risk normalised on PRE+X' lots) keeps all 237 trades/week and lifts the equal-risk P&L per planned lot in **every window for every threshold 0.20-0.40** (ER>=0.3: L3M +1.39, L6M +1.40 [MDE 1.15], HOLD +1.35, PRE +0.52, X' +0.04, 2026 +1.50 pts per lot; per contract of final lots the same +/-0.01, because final lots are 1.0 on average). The shuffled-ER placebo (500 draws, within book x month) ranks the real sizer **1/301 in L3M, L6M, HOLD and PRE but 119/301 in X'** (ER>=0.3): the effect is a PRE-onward, mostly 2025-26 effect, not a 2023 one.
2. **On the exact lock-engine stack the same rule is INSIDE the MDE in every window and negative in PRE.** ER>=0.3, equal-risk, 70/30 N base: stack d = +35.5k L3M, **+13.3k L6M (MDE 41k)**, +14.6k HOLD, **-10.9k PRE (MDE 29k)**, +7.5k X', +51k 2026, **-0.1k over the whole 2023-04..2026-02 (MDE 18.9k)** per week at research lots (live lots: divide by 2.35, i.e. L6M +5.7k/wk). Market-M base: L6M +9.5k, PRE -5.6k, ALL +2.2k. Across the 10 F1 cells the PRE stack delta is negative in 10 of 10 (-1.2k..-13.2k), the all-window delta -4.3k..+5.3k. The placebo for the stack delta (100 shuffled-ER draws): rank 2/101 in L6M, 47/101 in PRE.
3. **Why: the lock engine's day/week governors are denominated in base-lot R.** sl_lib BASE = day entry test +5R/-2R, day give-back arm (2R keep 50%), week floor 12R, with R = planned lots x stop x $20, NOT rescaled by a sizer. Up-sizing a trend day trips those governors earlier and clips exactly the upside the sizer creates: a **uniform x1.5 on ENG6 returns -4.7k/wk in L6M and -3.1k in PRE instead of the linear +36k/+30k** (x0.5 is linear, -25k/-30k). With the governors switched OFF in both base and sized runs the same sizer is **positive in every window: L6M +44.2k (MDE 41.7k), HOLD +42.1k (38.1k), PRE +15.7k (26.3k), X' +1.4k, 2026 +54k, all-window +17.4k (MDE 18.1k)** and the two bases computed (f73 N, market-M) agree (tables below). So the stack verdict depends on one thing the box cannot see: **do D6's day-arm / week-floor thresholds use the planned lots or the sized lots?** (question in MORNING.md). If planned lots (as in this engine), ER sizing is a shadow-only lead; if the sized lots, it is the +17k/wk (live +7k) all-window line with a worse worst-20 week (ungoverned base is not what runs live).
4. **5-min specific, level not state.** 3-min ER: PRE lift ~0 (-0.18..+0.03), X' -0.05..+0.36, L6M +0.5..+1.3; 15-min: negative in L6M, only PRE positive; ER10 positive in L6M (+0.8..+1.45) but PRE/X' about 0; ER50 was the PRE+X' winner (t 3.3) and is flat in L6M (+0.15), shuffled-ER rank **85/301**: the textbook case of a selection that does not carry forward. Signed ER times side (F4 `er20s_sided`, x1.5 when the ER-signed trend is with the trade, x0.5 against) is the most sign-consistent family (positive in all 30 cell-windows) but small (+0.4..+0.6 L6M, MDE 0.5). The ER-state (improving vs fading 5 / 15 min earlier) adds nothing stable: ER>=0.3 and improving beats fading by +6.5 pts/lot in L6M at 5 min but -0.5 in PRE and +1.8 in X', and not at all at 15 min (6.75 vs 6.53).
5. **Where it lives: Asia.** ER>=0.3 minus ER<0.3 spread, f73 N per planned lot, L6M: Asia +10.6, NY-AM +4.6, NY-PM +3.5, London +2.2, pre-market -1.1 (PRE: Asia +2.3, NY-AM +6.1, London -2.7). Applying the sizer in Asia only gives +26.4k/wk L6M on the governed stack (MDE 37k), -3.9k PRE; NY-AM only: -1.3k L6M, +7.1k PRE: no session is stable in sign.
6. **The 30% add pays more in trend in the recent windows only** (add-leg proxy, spread hi-lo: L6M +1.46 per planned lot, HOLD +1.38, PRE +0.62, X' -0.15; Asia +3.3 L6M / +0.7 PRE). The add fills in 92-94% of signals in every ER bucket (fill rate does not depend on trend), so the sizer cannot be built on fill probability.
7. **Regime-switch sizing is not better than the plain trend sizer.** Polarity fixed on PRE+X': only HM prefers chop (SEL spread -1.6/lot; ST, KB, PE, SM, WT, MV, PB, DN, MA prefer trend); the "fade" book is therefore HM only and reversing it costs L6M (HM's L6M spread is +4.9): equal-risk lift L6M +1.07 (vs +1.40 uniform), stack +7.9k L6M / -1.3k PRE. The chosen polarity beats 95% of all 64 polarity assignments in L6M (98% in PRE+X'), shuffled-ER rank 2/301.
8. **Walk-forward chain of the threshold** (monthly re-fit, fit only on trades closed before the re-fit, 3/6/12-month rolling and anchored, grid 0.15-0.45, sizing OFF if the best fit lift <= 0): equal-risk lift L6M +0.91..+1.22, PRE +0.26..+0.58, X' +0.46..+0.61 per planned lot (shuffled-ER chain rank 100/100 in L6M, 93/100 PRE); stack (governed) L6M -10.8k..+6.3k, PRE -8k..-18k, all-window -5k..-9k: the chain is worse than the fixed 0.3 on the stack. **Last re-fit (data to 2026-02-06, applies to Feb 2026): anchored 0.45 (grid edge), roll-12 0.30, roll-6 0.40, roll-3 0.40.** The thresholds wander 0.20-0.45 month to month (std 0.06-0.09), which is the honest forward statement: any value 0.30-0.40 is equivalent.
9. **Tier.** The ER(20) 5-min sizer is a **post-hoc-named LEAD / CANDIDATE-RECENT (ER>=0.3 was named after TG-1 looked at L6M/HOLD)**; PRE+X'-selected alternatives (ER50>=0.4) fail the recent look. Failed gates: stack PRE < 0 (governed), cumulative multiplicity (program RC p 0.024 over its 54 cells, Sidak against 2.46 M cumulative cells = 1.0), PBO 0.81, X' placebo not distinguished, stack effect inside MDE in every window. **PASS: none. Recommendation: SHADOW (paper-trade the 1.5/0.5 lot multiplier), not ON**; see the D6 line below. (d) ER x sub-minute confirmation is **pending** (CF-SUBMIN S2 look is 34/67 done, `out/confirm2` is still empty); it will be added in the next update.

## D6 mapping and dollars (Sunday-brief rows)

| rule | D6 vocabulary (group / property / value) | per planned lot (equal risk) L6M / PRE | stack d $/wk research lots L6M / PRE / all (governed) | at live lots (/2.35) | tier |
|---|---|---|---|---|---|
| ER20 5m sizer, ENG6 | `entry book ST,HM,WT,KB,SM,PE regime trend(ER20, 5m) >= 0.3 -> take \| lotmult 1.5; below 0.3 -> lotmult 0.5` (the equal-risk version is 1.68 / 0.56: the 1.5/0.5 pair has mean lot factor 0.87-0.89 in recent windows, i.e. it also cuts total risk 11%) | +1.40 / +0.52 | unscaled +18.6k / -7.4k / +2.3k; equal-risk +13.3k / -10.9k / -0.1k | unscaled +7.9k / -3.1k / +1.0k wk | LEAD (post-hoc named), SHADOW |
| same, governors scaled with sized lots (question) | same | same | +44.2k / +15.7k / +17.4k (equal risk, governors off in base and sized) | +18.8k / +6.7k / +7.4k | (upper bound, not the engine as live) |
| walk-forward threshold chain | same property, value re-fitted monthly (last: 0.30-0.40) | +0.9..+1.2 / +0.3..+0.6 | -10.8k..+6.3k / -8k..-18k / -5k..-9k | | CANDIDATE-RECENT (no stack gain) |

Trades per week: 237 (unchanged by construction). Mean lot factor of the 1.5/0.5 sizer: 0.87 (SEL), 0.89 (L6M).

## Quant-layer one-page header (equal-risk planned-lot gain per ENG6 trade; x = (m-1)*pnl on the 70/30 N base; capacity not measurable here because every entry is the same fill with +/-50% lots; promote_ok is False for every row, as it must be)

| cell | pts_per_contract | ci_lo | ci_hi | L3M | L6M | HOLD | PRE | Xp | trades_per_week | fire_rate | n_cells | rc_p_program | rw_survives | dsr | pbo | placebo_rank | neighbourhood_mean | breakeven_slip | capacity_contracts | top5_share | stack_corr | regime | drift_sign_count | promote_ok | stack_d_L6M | stack_d_PRE | stack_d_ALL |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| T2 F1 5m ER20>=0.3 sizer 2L (post-hoc-named) | 1.291 | 0.467 | 2.034 | 1.320 | 1.291 | 1.254 | 0.493 | 0.059 | 237.000 | 1.000 | 54 | 0.024 | Y | 0.707 | 0.806 | 1/301 | 1.235 | 2.423 | not measured (lots +-50% on the same entries) | 1.613 | -0.132 | ER-high (trend) bars; positive in asia/nyam/nypm L6M | 10/12 | False | 13309.170 | -10895.344 | -126.682 |
| T2 F1 5m ER20>=0.25 sizer 2L | 1.218 | 0.287 | 2.082 | 1.274 | 1.218 | 1.125 | 0.529 | 0.205 | 237.000 | 1.000 | 54 | 0.024 | Y | 0.743 | 0.806 | 1/301 | 1.064 | 2.405 | not measured (lots +-50% on the same entries) | 1.314 | -0.133 | ER-high (trend) bars; positive in asia/nyam/nypm L6M | 10/12 | False | 10642.999 | -4306.064 | 3915.070 |
| T2 F1 5m ER20 0.3 3L | 0.944 | 0.178 | 1.706 | 0.968 | 0.944 | 0.851 | 0.486 | 0.248 | 237.000 | 1.000 | 54 | 0.024 | Y | 0.782 | 0.806 | 1/301 | nan | 2.313 | not measured (lots +-50% on the same entries) | 1.671 | -0.155 | ER-high (trend) bars; positive in asia/nyam/nypm L6M | 10/12 | False | 14131.391 | -1198.178 | 5080.898 |
| T2 SEL-top F3 5m ER50>=0.4 2L | 0.116 | -0.593 | 0.763 | 0.448 | 0.116 | 0.028 | 0.747 | 0.830 | 237.000 | 1.000 | 54 | 0.024 | Y | 0.780 | 0.806 | 85/301 | nan | 0.662 | not measured (lots +-50% on the same entries) | 20.295 | -0.182 | ER-high (trend) bars; positive in asia/nyam/nypm L6M | 10/12 | False | 52.496 | -9272.178 | -3639.344 |
| T2 SEL-best F4 ER20>=0.2 & slope-with | 0.682 | -0.113 | 1.460 | 0.636 | 0.682 | 0.558 | 0.561 | 0.476 | 237.000 | 1.000 | 54 | 0.024 | Y | 0.770 | 0.806 | 2/301 | nan | 1.539 | not measured (lots +-50% on the same entries) | 2.378 | -0.130 | ER-high (trend) bars; positive in asia/nyam/nypm L6M | 11/12 | False | 5955.274 | -3022.807 | 3191.661 |
| T2 SEL-best F5 persist lag900 t.25 | 0.990 | 0.187 | 1.746 | 1.147 | 0.990 | 0.951 | 0.591 | 0.309 | 237.000 | 1.000 | 54 | 0.024 | Y | 0.877 | 0.806 | 3/301 | nan | 2.551 | not measured (lots +-50% on the same entries) | 1.601 | -0.179 | ER-high (trend) bars; positive in asia/nyam/nypm L6M | 11/12 | False | 6819.030 | -5543.754 | 1970.935 |
| T2 E regime-switch t=.3 (HM reversed) | 0.985 | 0.172 | 1.725 | 1.114 | 0.985 | 0.985 | 0.656 | 0.036 | 237.000 | 1.000 | 54 | 0.024 | Y | 0.869 | 0.806 | 2/301 | nan | 1.866 | not measured (lots +-50% on the same entries) | 1.947 | nan | ER-high (trend) bars; positive in asia/nyam/nypm L6M | 10/12 | False | 7922.992 | -1325.209 | 2039.218 |
| T2 F WF roll6 chain | 1.072 | 0.100 | 2.059 | 1.203 | 1.072 | 0.897 | 0.284 | 0.459 | 237.000 | 1.000 | 54 | 0.024 | N | 0.480 | 0.806 | 1/301 | nan | 2.390 | not measured (lots +-50% on the same entries) | 3.095 | nan | ER-high (trend) bars; positive in asia/nyam/nypm L6M | 9/12 | False | 5564.823 | -17872.921 | -7956.101 |

Notes on the columns: `pts_per_contract` is the L6M mean over ALL ENG6 trades (untouched trades count 0) with a week-block bootstrap CI; `rc_p_program` is White RC over the 54-cell program on the all-window daily deltas (0.024; Sidak against the 2.46 M cumulative cells = 1.0); `rw_survives` Romano-Wolf stepdown (23 of 54 cells survive within the program: the cells are near-duplicates of one effect, so program-level survival is not independent evidence); `top5_share` > 1 means the 5% best trades earn more than the whole net gain (big offsetting losses); `stack_corr` = correlation of the weekly delta with the weekly base stack (all-window, governed). `placebo_rank` = rank of the real equal-risk lift among 300 shuffled-ER draws (L6M).

## (a) THE SIZER GRID

All numbers: ENG6, 70/30 N base, equal-risk (multiplier rescaled by a PRE+X'-fixed constant so Sum lots is unchanged), pts per planned lot; `unscaled L6M` = Sum (m-1)*pnl / N without re-normalising; `lotfac` = lot-weighted mean multiplier in L6M; `plc rank` = fraction of 500 shuffled-ER draws (within book x month) below the real value (1.00 = real beats all); `plc p95` = the 95th percentile of the draws.

#### F1 5m ER20 sizer

| cell | hi-share | lotfac L6M | SEL t | rm L3M | rm L6M | rm HOLD | rm PRE | rm X' | rm 2026 | MDE L6M | pc L6M | unscaled L6M | plc rank L6M | plc p95 L6M | plc rank SEL |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F1|5m.er20|t=0.25|2L | 0.49 | 0.97 | 1.86 | 1.33 | 1.30 | 1.19 | 0.56 | 0.18 | 1.67 | 1.30 | 1.30 | 1.17 | 1.00 | 0.63 | 0.99 |
| F1|5m.er20|t=0.25|3L | 0.49 | 1.07 | 1.48 | 0.85 | 0.71 | 0.64 | 0.32 | 0.14 | 0.86 | 0.99 | 0.71 | 0.93 | 0.99 | 0.40 | 0.96 |
| F1|5m.er20|t=0.2|2L | 0.59 | 1.07 | 2.37 | 0.71 | 0.73 | 0.58 | 0.50 | 0.38 | 0.43 | 1.20 | 0.72 | 0.93 | 0.99 | 0.53 | 1.00 |
| F1|5m.er20|t=0.2|3L | 0.59 | 1.18 | 1.94 | 0.46 | 0.42 | 0.36 | 0.29 | 0.30 | 0.48 | 0.86 | 0.42 | 0.93 | 0.97 | 0.36 | 0.99 |
| F1|5m.er20|t=0.35|2L | 0.30 | 0.79 | 1.58 | 1.32 | 1.17 | 1.13 | 0.47 | 0.31 | 1.00 | 1.20 | 1.17 | 0.41 | 0.99 | 0.74 | 0.97 |
| F1|5m.er20|t=0.35|3L | 0.30 | 0.88 | 1.85 | 1.32 | 1.24 | 1.16 | 0.52 | 0.24 | 1.37 | 1.15 | 1.24 | 0.79 | 1.00 | 0.61 | 1.00 |
| F1|5m.er20|t=0.3|2L | 0.39 | 0.87 | 1.51 | 1.39 | 1.40 | 1.35 | 0.52 | 0.04 | 1.50 | 1.15 | 1.40 | 0.89 | 1.00 | 0.68 | 0.97 |
| F1|5m.er20|t=0.3|3L | 0.39 | 0.97 | 2.15 | 1.02 | 1.03 | 0.92 | 0.51 | 0.22 | 0.91 | 1.12 | 1.03 | 0.91 | 1.00 | 0.55 | 1.00 |
| F1|5m.er20|t=0.4|2L | 0.23 | 0.71 | 1.87 | 1.65 | 1.34 | 1.35 | 0.53 | 0.51 | 1.18 | 1.42 | 1.34 | 0.25 | 1.00 | 0.65 | 1.00 |
| F1|5m.er20|t=0.4|3L | 0.23 | 0.79 | 1.79 | 1.51 | 1.37 | 1.35 | 0.52 | 0.25 | 1.36 | 1.10 | 1.37 | 0.57 | 1.00 | 0.64 | 0.99 |

### ER on 3m / 15m (2L)

#### F2 3m/15m ER20

| cell | hi-share | lotfac L6M | SEL t | rm L3M | rm L6M | rm HOLD | rm PRE | rm X' | rm 2026 | MDE L6M | pc L6M | unscaled L6M | plc rank L6M | plc p95 L6M | plc rank SEL |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F2|15m.er20|t=0.25|2L | 0.45 | 0.97 | -0.12 | -0.17 | 0.11 | 0.24 | 0.09 | -0.36 | -1.21 | 1.34 | 0.11 | 0.02 | 0.53 | 0.61 | 0.45 |
| F2|15m.er20|t=0.2|2L | 0.55 | 1.06 | -0.06 | 0.25 | 0.21 | 0.24 | 0.05 | -0.19 | -0.53 | 1.05 | 0.21 | 0.36 | 0.72 | 0.60 | 0.52 |
| F2|15m.er20|t=0.35|2L | 0.28 | 0.81 | 1.30 | -0.66 | -0.19 | -0.06 | 0.77 | -0.39 | -2.22 | 1.30 | -0.19 | -0.62 | 0.34 | 0.60 | 0.98 |
| F2|15m.er20|t=0.3|2L | 0.36 | 0.88 | 1.03 | -0.24 | -0.00 | 0.07 | 0.59 | -0.35 | -1.86 | 1.38 | -0.00 | -0.29 | 0.44 | 0.63 | 0.94 |
| F2|15m.er20|t=0.4|2L | 0.21 | 0.73 | 2.15 | -0.37 | -0.23 | -0.10 | 1.08 | -0.14 | -1.47 | 1.47 | -0.23 | -0.83 | 0.29 | 0.64 | 1.00 |
| F2|3m.er20|t=0.25|2L | 0.52 | 0.99 | 0.28 | 0.16 | 0.53 | 0.58 | 0.03 | 0.17 | 0.93 | 1.30 | 0.52 | 0.49 | 0.92 | 0.61 | 0.56 |
| F2|3m.er20|t=0.2|2L | 0.62 | 1.09 | -0.13 | 0.65 | 0.78 | 0.79 | -0.01 | -0.05 | 1.32 | 0.90 | 0.78 | 1.06 | 0.99 | 0.50 | 0.39 |
| F2|3m.er20|t=0.35|2L | 0.33 | 0.79 | -0.03 | 0.41 | 1.10 | 0.97 | -0.03 | 0.09 | 1.25 | 1.62 | 1.10 | 0.37 | 0.99 | 0.71 | 0.42 |
| F2|3m.er20|t=0.3|2L | 0.42 | 0.88 | -0.35 | -0.03 | 0.86 | 0.84 | -0.18 | 0.20 | 1.02 | 1.69 | 0.86 | 0.47 | 0.99 | 0.60 | 0.27 |
| F2|3m.er20|t=0.4|2L | 0.24 | 0.72 | -0.15 | 1.08 | 1.26 | 1.12 | -0.18 | 0.36 | 1.88 | 1.38 | 1.26 | 0.21 | 1.00 | 0.62 | 0.36 |

#### F3 ER10/ER50 5m

| cell | hi-share | lotfac L6M | SEL t | rm L3M | rm L6M | rm HOLD | rm PRE | rm X' | rm 2026 | MDE L6M | pc L6M | unscaled L6M | plc rank L6M | plc p95 L6M | plc rank SEL |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F3|5m.er10|t=0.25|2L | 0.63 | 1.12 | -1.30 | 0.77 | 0.86 | 0.64 | -0.18 | -0.29 | 0.96 | 0.71 | 0.87 | 1.27 | 1.00 | 0.47 | 0.05 |
| F3|5m.er10|t=0.2|2L | 0.71 | 1.20 | -0.56 | 0.76 | 0.84 | 0.61 | 0.07 | -0.52 | 1.02 | 0.57 | 0.84 | 1.49 | 1.00 | 0.44 | 0.25 |
| F3|5m.er10|t=0.35|2L | 0.49 | 0.96 | 0.16 | 0.72 | 0.99 | 0.81 | 0.07 | -0.04 | 0.64 | 1.14 | 0.99 | 0.86 | 1.00 | 0.59 | 0.50 |
| F3|5m.er10|t=0.3|2L | 0.56 | 1.04 | -0.34 | 0.96 | 0.89 | 0.69 | -0.05 | -0.10 | 0.59 | 0.81 | 0.89 | 1.02 | 1.00 | 0.52 | 0.26 |
| F3|5m.er10|t=0.4|2L | 0.42 | 0.89 | 0.84 | 1.15 | 1.45 | 1.18 | 0.19 | 0.25 | 1.29 | 1.14 | 1.45 | 1.04 | 1.00 | 0.73 | 0.81 |
| F3|5m.er50|t=0.25|2L | 0.23 | 0.73 | 2.16 | 0.48 | 0.63 | 0.64 | 0.87 | 0.24 | -0.52 | 1.71 | 0.64 | -0.18 | 0.93 | 0.68 | 1.00 |
| F3|5m.er50|t=0.2|2L | 0.34 | 0.85 | 1.50 | 0.06 | 0.21 | 0.31 | 0.64 | 0.09 | -0.84 | 1.36 | 0.21 | -0.18 | 0.62 | 0.71 | 1.00 |
| F3|5m.er50|t=0.35|2L | 0.09 | 0.58 | 2.84 | 0.82 | 0.28 | 0.27 | 0.86 | 0.68 | 0.19 | 1.17 | 0.28 | -0.86 | 0.77 | 0.57 | 1.00 |
| F3|5m.er50|t=0.3|2L | 0.15 | 0.64 | 2.41 | 1.07 | 0.34 | 0.30 | 0.89 | 0.45 | 0.86 | 1.40 | 0.34 | -0.66 | 0.73 | 0.76 | 1.00 |
| F3|5m.er50|t=0.4|2L | 0.05 | 0.55 | 3.28 | 0.45 | 0.15 | 0.06 | 0.76 | 0.81 | 0.22 | 0.95 | 0.15 | -1.03 | 0.68 | 0.45 | 1.00 |

### ER with direction (F4: `slope_with` = x1.5 only if ER>=t AND the 20-bar regression slope is with the trade side, x1.0 if against, x0.5 below; `er20s_sided` = signed ER times side: >=t x1.5, <=-t x0.5)

#### F4 ER + direction

| cell | hi-share | lotfac L6M | SEL t | rm L3M | rm L6M | rm HOLD | rm PRE | rm X' | rm 2026 | MDE L6M | pc L6M | unscaled L6M | plc rank L6M | plc p95 L6M | plc rank SEL |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F4|er20+slope_with|t=0.2 | 0.53 | 1.04 | 2.61 | 0.67 | 0.75 | 0.61 | 0.58 | 0.45 | 0.63 | 1.17 | 0.74 | 0.87 | 0.99 | 0.51 | 1.00 |
| F4|er20+slope_with|t=0.25 | 0.45 | 0.95 | 1.95 | 1.32 | 1.31 | 1.20 | 0.57 | 0.29 | 1.88 | 1.34 | 1.31 | 1.12 | 1.00 | 0.54 | 1.00 |
| F4|er20+slope_with|t=0.3 | 0.37 | 0.86 | 1.63 | 1.40 | 1.42 | 1.36 | 0.52 | 0.18 | 1.69 | 1.18 | 1.42 | 0.88 | 1.00 | 0.65 | 0.99 |
| F4|er20+slope_with|t=0.35 | 0.29 | 0.78 | 1.70 | 1.39 | 1.21 | 1.17 | 0.46 | 0.47 | 1.13 | 1.23 | 1.21 | 0.42 | 1.00 | 0.68 | 0.99 |
| F4|er20+slope_with|t=0.4 | 0.22 | 0.71 | 2.00 | 1.70 | 1.38 | 1.39 | 0.51 | 0.67 | 1.30 | 1.40 | 1.38 | 0.27 | 1.00 | 0.71 | 1.00 |
| F4|er20s_sided|t=0.2 | 0.54 | 1.24 | 2.37 | 0.31 | 0.37 | 0.33 | 0.30 | 0.21 | 0.49 | 0.57 | 0.37 | 1.04 | 0.99 | 0.28 | 1.00 |
| F4|er20s_sided|t=0.25 | 0.45 | 1.20 | 1.60 | 0.57 | 0.54 | 0.48 | 0.22 | 0.17 | 0.95 | 0.59 | 0.54 | 1.15 | 1.00 | 0.27 | 1.00 |
| F4|er20s_sided|t=0.3 | 0.37 | 1.17 | 1.64 | 0.53 | 0.54 | 0.52 | 0.18 | 0.21 | 0.74 | 0.50 | 0.54 | 1.04 | 1.00 | 0.26 | 0.99 |
| F4|er20s_sided|t=0.35 | 0.29 | 1.13 | 1.84 | 0.57 | 0.47 | 0.45 | 0.14 | 0.31 | 0.52 | 0.49 | 0.47 | 0.85 | 1.00 | 0.25 | 1.00 |
| F4|er20s_sided|t=0.4 | 0.22 | 1.10 | 2.23 | 0.59 | 0.48 | 0.48 | 0.14 | 0.36 | 0.53 | 0.46 | 0.48 | 0.77 | 1.00 | 0.21 | 1.00 |

#### F5 ER state vs earlier

| cell | hi-share | lotfac L6M | SEL t | rm L3M | rm L6M | rm HOLD | rm PRE | rm X' | rm 2026 | MDE L6M | pc L6M | unscaled L6M | plc rank L6M | plc p95 L6M | plc rank SEL |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F5|persist|lag=300|t=0.25 | 0.41 | 0.96 | 1.94 | 0.95 | 1.06 | 0.98 | 0.50 | 0.26 | 1.26 | 1.27 | 1.06 | 0.93 | 1.00 | 0.62 | 0.99 |
| F5|persist|lag=300|t=0.3 | 0.32 | 0.87 | 1.77 | 1.04 | 1.08 | 1.02 | 0.55 | 0.07 | 1.27 | 1.21 | 1.08 | 0.62 | 1.00 | 0.55 | 1.00 |
| F5|persist|lag=300|t=0.35 | 0.24 | 0.79 | 1.70 | 1.07 | 0.89 | 0.86 | 0.50 | 0.28 | 0.87 | 1.22 | 0.88 | 0.18 | 0.98 | 0.60 | 0.99 |
| F5|persist|lag=900|t=0.25 | 0.37 | 0.97 | 2.46 | 1.18 | 1.05 | 1.00 | 0.62 | 0.28 | 1.23 | 1.14 | 1.04 | 0.95 | 1.00 | 0.49 | 1.00 |
| F5|persist|lag=900|t=0.3 | 0.28 | 0.88 | 1.93 | 1.21 | 1.10 | 1.08 | 0.56 | 0.18 | 1.63 | 1.00 | 1.10 | 0.67 | 1.00 | 0.56 | 1.00 |
| F5|persist|lag=900|t=0.35 | 0.21 | 0.79 | 1.64 | 1.35 | 1.02 | 0.95 | 0.50 | 0.14 | 1.76 | 1.01 | 1.01 | 0.30 | 0.99 | 0.64 | 0.99 |
| F5|state_delta|lag=300|t=0.25 | 0.49 | 0.99 | 1.90 | 1.75 | 1.69 | 1.51 | 0.54 | 0.32 | 2.00 | 1.34 | 1.69 | 1.65 | 1.00 | 0.68 | 0.99 |
| F5|state_delta|lag=300|t=0.3 | 0.39 | 0.89 | 1.62 | 1.76 | 1.76 | 1.65 | 0.52 | 0.16 | 1.73 | 1.24 | 1.76 | 1.31 | 1.00 | 0.72 | 0.96 |
| F5|state_delta|lag=300|t=0.35 | 0.30 | 0.81 | 1.79 | 1.67 | 1.48 | 1.38 | 0.50 | 0.50 | 1.28 | 1.38 | 1.48 | 0.74 | 1.00 | 0.81 | 0.98 |
| F5|state_delta|lag=900|t=0.25 | 0.49 | 0.99 | 1.52 | 1.63 | 1.55 | 1.42 | 0.43 | 0.34 | 1.84 | 1.44 | 1.55 | 1.50 | 1.00 | 0.54 | 0.97 |
| F5|state_delta|lag=900|t=0.3 | 0.39 | 0.89 | 1.23 | 1.68 | 1.60 | 1.54 | 0.38 | 0.21 | 1.73 | 1.34 | 1.60 | 1.15 | 1.00 | 0.78 | 0.94 |
| F5|state_delta|lag=900|t=0.35 | 0.30 | 0.81 | 1.18 | 1.68 | 1.42 | 1.38 | 0.29 | 0.53 | 1.26 | 1.38 | 1.42 | 0.67 | 1.00 | 0.75 | 0.95 |

F1-F3 and F5 rows are in `out/trend2/tables.md` (F3 = ER10/ER50, F5 = ER state vs 5/15 min earlier).

### The ER state vs 5 / 15 minutes earlier (improving / fading is the change of ER(20) of more than 0.05)

#### ER state vs 5 min earlier: mean f73 N pts per planned lot (ENG6)

| er | state | L3M | L6M | HOLD | PRE | X' | 2026 | n L6M | n PRE | n X' |
|---|---|---|---|---|---|---|---|---|---|---|
| ER<.3 | fading(d<-.05) | -2.90 | 0.83 | 0.29 | -0.10 | -1.34 | -0.02 | 1215.00 | 2984.00 | 944.00 |
| ER<.3 | flat | -3.13 | -0.60 | -0.60 | 1.72 | 1.19 | -3.02 | 2069.00 | 5042.00 | 1693.00 |
| ER<.3 | improving(d>+.05) | 4.26 | 2.67 | 1.67 | -0.17 | 1.30 | 9.53 | 911.00 | 2225.00 | 740.00 |
| ER>=.3 | fading(d<-.05) | 0.05 | 3.07 | 3.79 | 2.94 | -0.08 | 6.54 | 450.00 | 1114.00 | 430.00 |
| ER>=.3 | flat | 4.19 | 4.07 | 3.08 | 2.81 | 0.25 | 6.73 | 1159.00 | 3091.00 | 1264.00 |
| ER>=.3 | improving(d>+.05) | 5.17 | 9.56 | 8.83 | 2.45 | 1.73 | 5.88 | 832.00 | 2160.00 | 782.00 |

#### ER state vs 15 min earlier: mean f73 N pts per planned lot (ENG6)

| er | state | L3M | L6M | HOLD | PRE | X' | 2026 | n L6M | n PRE | n X' |
|---|---|---|---|---|---|---|---|---|---|---|
| ER<.3 | fading(d<-.05) | -2.27 | -0.64 | -0.81 | 2.36 | -1.16 | -1.75 | 1747.00 | 4253.00 | 1437.00 |
| ER<.3 | flat | -2.30 | 1.10 | 0.68 | -0.44 | 2.57 | 1.91 | 1499.00 | 3665.00 | 1180.00 |
| ER<.3 | improving(d>+.05) | 1.52 | 1.77 | 1.05 | -0.19 | 0.48 | 3.40 | 949.00 | 2333.00 | 760.00 |
| ER>=.3 | fading(d<-.05) | 0.69 | 6.53 | 5.23 | 4.23 | 0.55 | 3.92 | 640.00 | 1665.00 | 678.00 |
| ER>=.3 | flat | 6.07 | 3.70 | 3.84 | 2.56 | -1.79 | 9.77 | 749.00 | 1858.00 | 714.00 |
| ER>=.3 | improving(d>+.05) | 3.95 | 6.75 | 6.06 | 1.92 | 2.33 | 5.24 | 1052.00 | 2842.00 | 1084.00 |

## Lock-engine stack lines (F1 grid)

#### F1 stack (base f73_N; $/wk at research lots, divide by 2.35 for live lots)

| cell | frame | L3M | L6M | HOLD | PRE | X' | 2026 | ALL | MDE L6M | sd L6M (base 139698) | maxDD ALL (base 610249) | w20 ALL (base -164897) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F1|5m.er20|t=0.25|2L | rm | 23130 | 10643 | 11844 | -4306 | 11984 | 36288 | 3915 | 41915 | 142923 | 556383 | -188858 |
| F1|5m.er20|t=0.25|2L | unscaled | 24488 | 12421 | 13390 | -3672 | 11561 | 34557 | 4441 | 42093 | 141862 | 548787 | -185370 |
| F1|5m.er20|t=0.25|2L | uniform_unscaled | -274 | -2121 | -2079 | 183 | -374 | 1317 | -465 | 6753 | 141864 | 621634 | -166044 |
| F1|5m.er20|t=0.25|3L | rm | 27033 | 8884 | 6917 | -8687 | 8813 | 33934 | -285 | 40740 | 134656 | 605987 | -185261 |
| F1|5m.er20|t=0.25|3L | unscaled | 15746 | -6790 | -4785 | -4294 | 11143 | 25359 | 102 | 42119 | 134902 | 613711 | -190293 |
| F1|5m.er20|t=0.25|3L | uniform_unscaled | -6701 | 403 | -1517 | -1610 | 1967 | -5725 | -556 | 10525 | 151349 | 678533 | -183253 |
| F1|5m.er20|t=0.2|2L | rm | 9476 | -2618 | -5726 | -5307 | 7220 | 36346 | -1769 | 38275 | 135637 | 656875 | -193361 |
| F1|5m.er20|t=0.2|2L | unscaled | 12384 | -4279 | -4365 | -1129 | 10592 | 26692 | 1622 | 35262 | 131164 | 622163 | -184013 |
| F1|5m.er20|t=0.2|2L | uniform_unscaled | -7728 | -837 | -2639 | -769 | 1944 | -8104 | -380 | 9887 | 150116 | 679082 | -182920 |
| F1|5m.er20|t=0.2|3L | rm | 19035 | -2566 | -3237 | -4874 | 3619 | 21652 | -2080 | 32299 | 130184 | 618187 | -184731 |
| F1|5m.er20|t=0.2|3L | unscaled | 3412 | -11535 | -10623 | 1133 | 11865 | 21212 | 1793 | 35316 | 134348 | 681741 | -189727 |
| F1|5m.er20|t=0.2|3L | uniform_unscaled | -14119 | -6333 | -6485 | 858 | 4892 | -10154 | 484 | 19571 | 155033 | 695225 | -188206 |
| F1|5m.er20|t=0.35|2L | rm | 32451 | 18501 | 15262 | -8478 | 15461 | 58188 | 3576 | 49543 | 157189 | 540854 | -188117 |
| F1|5m.er20|t=0.35|2L | unscaled | 30559 | 11053 | 10180 | -7540 | 5589 | 47086 | 42 | 41112 | 134899 | 488286 | -171375 |
| F1|5m.er20|t=0.35|2L | uniform_unscaled | -410 | -985 | -923 | -9348 | -2540 | 26571 | -5654 | 23452 | 124268 | 493653 | -148322 |
| F1|5m.er20|t=0.35|3L | rm | 34762 | 15189 | 13353 | -2705 | 12759 | 48096 | 5274 | 48366 | 146953 | 549503 | -183520 |
| F1|5m.er20|t=0.35|3L | unscaled | 41623 | 22588 | 19580 | -4556 | 10081 | 51326 | 4889 | 43087 | 134892 | 527806 | -177551 |
| F1|5m.er20|t=0.35|3L | uniform_unscaled | 5843 | 7339 | 4530 | -6603 | -612 | 32180 | -2532 | 22784 | 142033 | 570627 | -164843 |
| F1|5m.er20|t=0.3|2L | rm | 35547 | 13309 | 14605 | -10895 | 7520 | 51211 | -127 | 41473 | 129909 | 529364 | -188571 |
| F1|5m.er20|t=0.3|2L | unscaled | 42840 | 18649 | 18736 | -7381 | 6687 | 48766 | 2283 | 41634 | 124277 | 469771 | -180280 |
| F1|5m.er20|t=0.3|2L | uniform_unscaled | 5776 | 7815 | 4955 | -6846 | -329 | 32035 | -2479 | 22886 | 142661 | 569319 | -164465 |
| F1|5m.er20|t=0.3|3L | rm | 42855 | 14131 | 12362 | -1198 | 10257 | 58693 | 5081 | 38930 | 131890 | 561236 | -182653 |
| F1|5m.er20|t=0.3|3L | unscaled | 43725 | 16897 | 14800 | -2150 | 10816 | 59062 | 5290 | 38694 | 131150 | 555979 | -181882 |
| F1|5m.er20|t=0.3|3L | uniform_unscaled | -2354 | -3316 | -3134 | 500 | -507 | -3801 | -571 | 4984 | 140635 | 624334 | -165804 |
| F1|5m.er20|t=0.4|2L | rm | 31071 | 8069 | 7901 | -13166 | 2259 | 29054 | -4263 | 49785 | 129192 | 562640 | -186997 |
| F1|5m.er20|t=0.4|2L | unscaled | 38247 | 10238 | 9657 | -14884 | 1244 | 53060 | -5051 | 48050 | 129598 | 489670 | -171938 |
| F1|5m.er20|t=0.4|2L | uniform_unscaled | -4998 | -11154 | -10054 | -16707 | -5464 | 18087 | -12182 | 25398 | 113872 | 458710 | -137392 |
| F1|5m.er20|t=0.4|3L | rm | 45724 | 22495 | 17754 | -6113 | 12940 | 64407 | 4557 | 48421 | 138847 | 526626 | -190752 |
| F1|5m.er20|t=0.4|3L | unscaled | 39693 | 19762 | 18249 | -9965 | 3569 | 52109 | -43 | 43244 | 133080 | 458611 | -173026 |
| F1|5m.er20|t=0.4|3L | uniform_unscaled | 645 | -244 | -287 | -9182 | -2520 | 29058 | -5428 | 24612 | 123985 | 496697 | -147857 |

#### F1 stack (base mkt_M; $/wk at research lots, divide by 2.35 for live lots)

| cell | frame | L3M | L6M | HOLD | PRE | X' | 2026 | ALL | MDE L6M | sd L6M (base 134756) | maxDD ALL (base 696240) | w20 ALL (base -192985) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F1|5m.er20|t=0.25|2L | rm | 39724 | 23905 | 21800 | 2331 | 13551 | 36158 | 9857 | 47702 | 129128 | 727769 | -204422 |
| F1|5m.er20|t=0.25|2L | unscaled | 41295 | 25063 | 24017 | 990 | 13280 | 42708 | 9578 | 48448 | 129372 | 728642 | -204029 |
| F1|5m.er20|t=0.25|2L | uniform_unscaled | -30 | 137 | 229 | -349 | 490 | -112 | 18 | 2601 | 133731 | 686650 | -190619 |
| F1|5m.er20|t=0.25|3L | rm | 31084 | 14255 | 11980 | -12009 | 8666 | 27743 | -913 | 43147 | 131210 | 818036 | -212879 |
| F1|5m.er20|t=0.25|3L | unscaled | 19582 | -2395 | -3720 | -2154 | 13602 | 15524 | 2134 | 46914 | 125503 | 806924 | -223067 |
| F1|5m.er20|t=0.25|3L | uniform_unscaled | 351 | 4082 | 2615 | -2337 | 3727 | -116 | 486 | 13083 | 137638 | 757475 | -199803 |
| F1|5m.er20|t=0.2|2L | rm | 22004 | 9528 | 5377 | -9619 | 10631 | 25334 | -547 | 39278 | 126596 | 797334 | -211151 |
| F1|5m.er20|t=0.2|2L | unscaled | 30206 | 8006 | 5453 | -3277 | 10078 | 42428 | 2498 | 42958 | 131569 | 784816 | -209052 |
| F1|5m.er20|t=0.2|2L | uniform_unscaled | 360 | 4049 | 2595 | -2924 | 3812 | -96 | 211 | 13059 | 137506 | 756685 | -199551 |
| F1|5m.er20|t=0.2|3L | rm | 35906 | 10747 | 8304 | -10528 | 1920 | 30285 | -2949 | 36207 | 125007 | 743199 | -204317 |
| F1|5m.er20|t=0.2|3L | unscaled | 22427 | -7405 | -9676 | -1090 | 15864 | 39887 | 2058 | 43511 | 134807 | 882298 | -231872 |
| F1|5m.er20|t=0.2|3L | uniform_unscaled | -8306 | -934 | -3483 | -4062 | 2654 | -18073 | -2009 | 16668 | 144550 | 813455 | -216679 |
| F1|5m.er20|t=0.35|2L | rm | 38027 | 14312 | 11466 | -11789 | 14735 | 58253 | 879 | 51768 | 141314 | 694804 | -214849 |
| F1|5m.er20|t=0.35|2L | unscaled | 33636 | 14296 | 13662 | -9922 | 11081 | 39084 | 1212 | 44742 | 129477 | 612011 | -186806 |
| F1|5m.er20|t=0.35|2L | uniform_unscaled | -1530 | -4621 | -5493 | -11253 | -144 | 17047 | -6887 | 23492 | 111804 | 651061 | -180655 |
| F1|5m.er20|t=0.35|3L | rm | 49637 | 26503 | 22295 | -4590 | 16927 | 46919 | 7476 | 46967 | 138388 | 691145 | -214053 |
| F1|5m.er20|t=0.35|3L | unscaled | 47067 | 27367 | 24444 | -4789 | 14633 | 39448 | 7160 | 40993 | 123054 | 663071 | -193182 |
| F1|5m.er20|t=0.35|3L | uniform_unscaled | -8514 | -2540 | -4832 | -5198 | 1549 | 11179 | -3197 | 20230 | 129768 | 722227 | -192236 |
| F1|5m.er20|t=0.3|2L | rm | 38885 | 9479 | 9392 | -5595 | 10198 | 38167 | 2212 | 46846 | 129228 | 657962 | -218838 |
| F1|5m.er20|t=0.3|2L | unscaled | 43464 | 17149 | 17554 | -2191 | 9499 | 37231 | 5472 | 44936 | 121783 | 599300 | -196447 |
| F1|5m.er20|t=0.3|2L | uniform_unscaled | -8845 | -2744 | -4988 | -5133 | 1395 | 10246 | -3243 | 21094 | 127805 | 720666 | -191562 |
| F1|5m.er20|t=0.3|3L | rm | 42612 | 13636 | 10706 | -2775 | 14622 | 36502 | 5220 | 39613 | 120442 | 708776 | -202811 |
| F1|5m.er20|t=0.3|3L | unscaled | 41225 | 12691 | 10177 | -2832 | 13513 | 34301 | 4751 | 40843 | 118161 | 702136 | -201555 |
| F1|5m.er20|t=0.3|3L | uniform_unscaled | -323 | 138 | 194 | -744 | 41 | -197 | -321 | 2549 | 134377 | 689780 | -190679 |
| F1|5m.er20|t=0.4|2L | rm | 43307 | 15167 | 13246 | -19236 | 4038 | 77324 | -5645 | 50692 | 120814 | 683076 | -203688 |
| F1|5m.er20|t=0.4|2L | unscaled | 42666 | 16760 | 16637 | -15265 | 3513 | 51799 | -3073 | 45224 | 117133 | 590214 | -189418 |
| F1|5m.er20|t=0.4|2L | uniform_unscaled | 4680 | -5755 | -5462 | -13085 | -809 | 26197 | -7998 | 29541 | 97815 | 598088 | -165408 |
| F1|5m.er20|t=0.4|3L | rm | 41068 | 20264 | 15413 | -11389 | 11469 | 44299 | 964 | 50376 | 130639 | 686018 | -218324 |
| F1|5m.er20|t=0.4|3L | unscaled | 45863 | 25767 | 24470 | -10235 | 7680 | 58480 | 2371 | 46425 | 121757 | 572928 | -187269 |
| F1|5m.er20|t=0.4|3L | uniform_unscaled | -2049 | -4461 | -5412 | -10612 | -520 | 17036 | -6657 | 22525 | 112973 | 655167 | -180717 |

Reading: `rm` = equal-risk sizer; `unscaled` = the 1.5/0.5 pair as is; `uniform_unscaled` = every ENG6 lot times the same L6M mean lot factor (the lot-factor-matched uniform scaling line). **Sizing alpha = unscaled minus uniform_unscaled** (e.g. t=0.3 2L: L6M +10.8k, HOLD +13.8k, PRE -0.5k, X' +7.0k on f73 N). The raw `unscaled` delta contains the mere effect of running 11-27% fewer or more lots on a positive-mean base (STRUCTURE): a rule with lot factor <1 loses base P&L by construction, one with >1 gains it; the equal-risk and the alpha lines remove that.

### Governors ON (engine as scored everywhere) vs OFF - stack d $/wk research lots, equal-risk sizers plus the uniform multipliers as the linearity check

f73 N base:

| governors | cell | L3M | L6M | HOLD | PRE | X' | 2026 | ALL | mde_L6M | mde_ALL | base_L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| on | uniform1.5 | -14989 | -4675 | -3455 | -3067 | 13995 | -17373 | 1847 | 40204 | 16805 | 72135 |
| on | uniform0.5 | -2036 | -25199 | -22920 | -29827 | -12426 | 24451 | -23605 | 42001 | 16597 | 72135 |
| on | F1|5m.er20|t=0.25|2L | 23130 | 10643 | 11844 | -4306 | 11984 | 36288 | 3915 | 41915 | 17398 | 72135 |
| on | F1|5m.er20|t=0.3|2L | 35547 | 13309 | 14605 | -10895 | 7520 | 51211 | -127 | 41473 | 18932 | 72135 |
| on | F1|5m.er20|t=0.3|3L | 42855 | 14131 | 12362 | -1198 | 10257 | 58693 | 5081 | 38930 | 17173 | 72135 |
| on | F1|5m.er20|t=0.35|2L | 32451 | 18501 | 15262 | -8478 | 15461 | 58188 | 3576 | 49543 | 19949 | 72135 |
| on | F1|5m.er20|t=0.4|2L | 31071 | 8069 | 7901 | -13166 | 2259 | 29054 | -4263 | 49785 | 19974 | 72135 |
| on | F4|er20+slope_with|t=0.3 | 43511 | 21551 | 22481 | -5668 | 9844 | 58305 | 4882 | 41444 | 19118 | 72135 |
| on | F5|state_delta|lag=300|t=0.25 | 47229 | 24121 | 21034 | -10719 | 16095 | 54578 | 3875 | 46918 | 19214 | 72135 |
| on | F5|persist|lag=900|t=0.25 | 13476 | 6819 | 6914 | -5544 | 11095 | 21836 | 1971 | 42297 | 16482 | 72135 |
| off | uniform1.5 | 18023 | 49283 | 38874 | 25658 | 6211 | 67762 | 23098 | 55460 | 20639 | 98567 |
| off | uniform0.5 | -18023 | -49283 | -38874 | -25658 | -6211 | -67762 | -23098 | 55460 | 20639 | 98567 |
| off | F1|5m.er20|t=0.25|2L | 54085 | 42302 | 38773 | 16089 | 3974 | 64805 | 17599 | 47248 | 17974 | 98567 |
| off | F1|5m.er20|t=0.3|2L | 52166 | 44208 | 42101 | 15709 | 1422 | 54476 | 17369 | 41703 | 18092 | 98567 |
| off | F1|5m.er20|t=0.3|3L | 40302 | 31418 | 27727 | 15106 | 4629 | 31521 | 14925 | 40519 | 15028 | 98567 |
| off | F1|5m.er20|t=0.35|2L | 50815 | 37203 | 35120 | 15497 | 9287 | 36959 | 18086 | 44788 | 19046 | 98567 |
| off | F1|5m.er20|t=0.4|2L | 63852 | 44354 | 42564 | 15335 | 13164 | 44656 | 20747 | 53622 | 21071 | 98567 |
| off | F4|er20+slope_with|t=0.3 | 52879 | 45705 | 42985 | 15828 | 3761 | 62124 | 18309 | 42386 | 18527 | 98567 |
| off | F5|state_delta|lag=300|t=0.25 | 70698 | 56012 | 49448 | 16379 | 6246 | 77999 | 20708 | 50419 | 19252 | 98567 |
| off | F5|persist|lag=900|t=0.25 | 48043 | 33864 | 32016 | 18008 | 5420 | 45872 | 17541 | 40924 | 15698 | 98567 |

market-M base:

| governors | cell | L3M | L6M | HOLD | PRE | X' | 2026 | ALL | mde_L6M | mde_ALL | base_L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| on | uniform1.5 | -6597 | -2603 | -11129 | -2230 | 5726 | -8083 | -1822 | 39978 | 16805 | 18815 |
| on | uniform0.5 | 13243 | -7899 | -5083 | -19913 | -4717 | 41831 | -12508 | 42422 | 15875 | 18815 |
| on | F1|5m.er20|t=0.25|2L | 39724 | 23905 | 21800 | 2331 | 13551 | 36158 | 9857 | 47702 | 17165 | 18815 |
| on | F1|5m.er20|t=0.3|2L | 38885 | 9479 | 9392 | -5595 | 10198 | 38167 | 2212 | 46846 | 17351 | 18815 |
| on | F1|5m.er20|t=0.3|3L | 42612 | 13636 | 10706 | -2775 | 14622 | 36502 | 5220 | 39613 | 15068 | 18815 |
| on | F1|5m.er20|t=0.35|2L | 38027 | 14312 | 11466 | -11789 | 14735 | 58253 | 879 | 51768 | 18592 | 18815 |
| on | F1|5m.er20|t=0.4|2L | 43307 | 15167 | 13246 | -19236 | 4038 | 77324 | -5645 | 50692 | 19115 | 18815 |
| on | F4|er20+slope_with|t=0.3 | 46542 | 16353 | 15259 | -4145 | 13448 | 50213 | 5162 | 48051 | 17655 | 18815 |
| on | F5|state_delta|lag=300|t=0.25 | 53473 | 28914 | 24179 | -971 | 16045 | 37011 | 9442 | 51749 | 18402 | 18815 |
| on | F5|persist|lag=900|t=0.25 | 22050 | 9849 | 7816 | -2335 | 14280 | 29803 | 4720 | 42375 | 15134 | 18815 |
| off | uniform1.5 | -23454 | 8518 | -672 | 1431 | 714 | 24981 | 787 | 53337 | 20347 | 17035 |
| off | uniform0.5 | 23454 | -8518 | 672 | -1431 | -714 | -24981 | -787 | 53337 | 20347 | 17035 |
| off | F1|5m.er20|t=0.25|2L | 54396 | 41580 | 39141 | 15571 | 4986 | 63338 | 17716 | 48045 | 17601 | 17035 |
| off | F1|5m.er20|t=0.3|2L | 56086 | 46544 | 44868 | 15685 | 2676 | 57229 | 18321 | 41210 | 17865 | 17035 |
| off | F1|5m.er20|t=0.3|3L | 41597 | 32284 | 29528 | 14409 | 5565 | 31369 | 15238 | 41086 | 14834 | 17035 |
| off | F1|5m.er20|t=0.35|2L | 56236 | 40869 | 38862 | 15099 | 10403 | 41063 | 19018 | 43375 | 18468 | 17035 |
| off | F1|5m.er20|t=0.4|2L | 67976 | 47214 | 45626 | 14726 | 14051 | 48069 | 21361 | 51320 | 20414 | 17035 |
| off | F4|er20+slope_with|t=0.3 | 56289 | 47580 | 45292 | 15432 | 5008 | 63958 | 18974 | 41899 | 18308 | 17035 |
| off | F5|state_delta|lag=300|t=0.25 | 69162 | 54498 | 48852 | 15719 | 7367 | 72523 | 20579 | 51501 | 18808 | 17035 |
| off | F5|persist|lag=900|t=0.25 | 49610 | 34485 | 33487 | 18201 | 5882 | 48476 | 18090 | 40886 | 15609 | 17035 |

Note `uniform1.5` ON is -4.7k in L6M and `uniform0.5` is -25k: the engine is linear in size only for down-sizing. OFF both are +/-49k (linear: 0.5 x the ungoverned base stack 98.6k).

## (b) ER x SESSION

##### ER bucket x session = ALL: f73 N pts per planned lot

| bucket | L6M | HOLD | PRE | X' | n L6M |
|---|---|---|---|---|---|
| -1-0.2 | 0.67 | 0.59 | 0.24 | -0.53 | 2890 |
| 0.2-0.3 | 0.19 | -0.86 | 1.93 | 2.56 | 1305 |
| 0.3-0.4 | 4.13 | 3.31 | 1.97 | -1.42 | 1028 |
| 0.4-9 | 6.93 | 6.52 | 3.27 | 2.10 | 1413 |

##### ER bucket x session = asia: f73 N pts per planned lot

| bucket | L6M | HOLD | PRE | X' | n L6M |
|---|---|---|---|---|---|
| -1-0.2 | -2.36 | -3.00 | 3.50 | -0.33 | 728 |
| 0.2-0.3 | 1.81 | 0.22 | 0.19 | -0.35 | 358 |
| 0.3-0.4 | 7.17 | 7.07 | -3.12 | 1.08 | 275 |
| 0.4-9 | 11.14 | 10.13 | 10.14 | -0.08 | 440 |

##### ER bucket x session = london: f73 N pts per planned lot

| bucket | L6M | HOLD | PRE | X' | n L6M |
|---|---|---|---|---|---|
| -1-0.2 | 3.72 | 3.54 | -1.20 | 0.35 | 504 |
| 0.2-0.3 | 2.19 | 2.07 | 5.62 | 6.75 | 316 |
| 0.3-0.4 | 1.92 | 1.47 | 5.05 | 1.64 | 239 |
| 0.4-9 | 7.74 | 7.91 | -6.59 | 3.66 | 325 |

##### ER bucket x session = nyam: f73 N pts per planned lot

| bucket | L6M | HOLD | PRE | X' | n L6M |
|---|---|---|---|---|---|
| -1-0.2 | 1.82 | 3.00 | 0.44 | 1.48 | 953 |
| 0.2-0.3 | -2.30 | -2.69 | 3.34 | 3.43 | 352 |
| 0.3-0.4 | -0.39 | -0.64 | 5.72 | -1.74 | 243 |
| 0.4-9 | 9.09 | 7.94 | 8.49 | 1.02 | 368 |

##### ER bucket x session = nypm: f73 N pts per planned lot

| bucket | L6M | HOLD | PRE | X' | n L6M |
|---|---|---|---|---|---|
| -1-0.2 | -1.10 | -1.71 | -0.54 | -4.20 | 565 |
| 0.2-0.3 | 0.89 | -0.45 | -2.77 | -1.16 | 213 |
| 0.3-0.4 | 9.25 | 6.69 | 2.81 | -4.41 | 203 |
| 0.4-9 | -3.14 | -1.54 | 0.50 | 4.62 | 209 |

##### ER bucket x session = pre: f73 N pts per planned lot

| bucket | L6M | HOLD | PRE | X' | n L6M |
|---|---|---|---|---|---|
| -1-0.2 | 4.66 | 1.92 | -5.85 | -2.31 | 132 |
| 0.2-0.3 | -7.12 | -11.80 | 5.33 | 11.22 | 66 |
| 0.3-0.4 | 0.50 | -0.40 | -3.17 | -9.82 | 68 |
| 0.4-9 | -1.16 | -4.43 | -1.78 | 0.39 | 65 |

#### ER(>=.3) minus ER(<.3) spread by session (f73 N pts per planned lot)

| sess | L3M | L6M | HOLD | PRE | X' | 2026 | SE L6M | SE PRE |
|---|---|---|---|---|---|---|---|---|
| ALL | 5.20 | 5.23 | 5.02 | 1.93 | 0.15 | 5.60 | 1.90 | 1.22 |
| asia | 12.67 | 10.60 | 10.93 | 2.30 | 0.74 | 9.39 | 3.20 | 2.63 |
| london | -0.53 | 2.15 | 2.18 | -2.70 | -0.09 | 0.47 | 3.81 | 2.86 |
| nyam | 5.41 | 4.61 | 3.03 | 6.10 | -2.13 | 4.29 | 3.68 | 2.57 |
| nypm | 4.62 | 3.52 | 3.88 | 2.81 | 4.00 | 15.49 | 3.45 | 2.55 |
| pre | -10.80 | -1.05 | 0.19 | -0.06 | -6.54 | -12.44 | 9.25 | 4.86 |

Sizer applied inside one session only (ER>=0.3, 2L, equal risk within the session, stack effect of changing that session only):

#### ER>=.3 2L sizer applied in ONE session only: equal-risk planned-lot lift (f73_N)

| sess | L3M | L6M | HOLD | PRE | X' | 2026 |
|---|---|---|---|---|---|---|
| asia | 0.91 | 0.75 | 0.78 | 0.15 | 0.05 | 0.73 |
| london | -0.05 | 0.10 | 0.10 | -0.15 | 0.02 | 0.07 |
| nyam | 0.41 | 0.35 | 0.23 | 0.42 | -0.17 | 0.30 |
| nypm | 0.23 | 0.18 | 0.20 | 0.16 | 0.22 | 0.65 |
| pre | -0.14 | -0.01 | 0.01 | 0.00 | -0.11 | -0.13 |

#### same, lock-engine stack d $/wk research lots (f73_N)

| sess | L3M | L6M | HOLD | PRE | X' | 2026 | MDE L6M |
|---|---|---|---|---|---|---|---|
| asia | 34239 | 26424 | 26943 | -3916 | 1891 | 69668 | 37193 |
| london | 6661 | 1703 | -559 | -16849 | 1419 | 6543 | 24131 |
| nyam | 3083 | -1332 | -3620 | 7087 | 2081 | -6320 | 19379 |
| nypm | 6752 | 3712 | 1492 | -173 | 4225 | 5293 | 7226 |
| pre | 3412 | 3711 | 3550 | -1509 | 2073 | 5684 | 11509 |

#### ER>=.3 2L sizer applied in ONE session only: equal-risk planned-lot lift (mkt_M)

| sess | L3M | L6M | HOLD | PRE | X' | 2026 |
|---|---|---|---|---|---|---|
| asia | 0.89 | 0.71 | 0.75 | 0.15 | 0.06 | 0.67 |
| london | -0.04 | 0.09 | 0.09 | -0.11 | 0.06 | 0.10 |
| nyam | 0.40 | 0.36 | 0.26 | 0.39 | -0.15 | 0.31 |
| nypm | 0.23 | 0.19 | 0.20 | 0.16 | 0.21 | 0.65 |
| pre | -0.11 | 0.01 | 0.03 | 0.00 | -0.09 | -0.12 |

#### same, lock-engine stack d $/wk research lots (mkt_M)

| sess | L3M | L6M | HOLD | PRE | X' | 2026 | MDE L6M |
|---|---|---|---|---|---|---|---|
| asia | 33024 | 28025 | 26165 | -1862 | 4255 | 56346 | 41230 |
| london | 7236 | 1003 | -308 | -10089 | 1503 | -2299 | 25155 |
| nyam | -2642 | -6988 | -7222 | 5461 | 2386 | -16319 | 20124 |
| nypm | 3838 | 1575 | 1187 | 385 | 4235 | 3481 | 7875 |
| pre | 160 | 1307 | 1139 | 103 | 1612 | 2694 | 7643 |

## (c) ER x THE 70/30 SPLIT

`split_minus_mkt` = f73 N minus market-at-signal N per planned lot (the whole split effect: dip fill, target re-base, lots); `add_contrib` = f73 N - 0.7 x mkt N (proxy of the 30% add's own contribution incl. the target re-base: labelled APPROXIMATE, the engine cannot isolate the add leg); `addfill` = share of signals with final lots > 0.75.

#### split x ER: spread (hi minus lo) of split_minus_mkt

| sess | L3M | L6M | HOLD | PRE | X' | 2026 |
|---|---|---|---|---|---|---|
| ALL | -0.181 | -0.158 | -0.186 | 0.053 | -0.272 | -0.123 |
| asia | -0.138 | 0.165 | 0.117 | 0.015 | -0.174 | 0.445 |
| london | -0.235 | 0.061 | 0.075 | -0.437 | -0.828 | -0.609 |
| nyam | -0.025 | -0.295 | -0.408 | 0.493 | -0.196 | -0.301 |
| nypm | -0.130 | -0.383 | -0.373 | 0.064 | 0.181 | -0.593 |
| pre | -1.520 | -1.432 | -1.185 | 0.123 | -1.054 | 0.092 |

#### split x ER: spread (hi minus lo) of add_contrib

| sess | L3M | L6M | HOLD | PRE | X' | 2026 |
|---|---|---|---|---|---|---|
| ALL | 1.434 | 1.459 | 1.377 | 0.617 | -0.146 | 1.595 |
| asia | 3.704 | 3.294 | 3.361 | 0.700 | 0.100 | 3.128 |
| london | -0.322 | 0.687 | 0.707 | -1.115 | -0.608 | -0.285 |
| nyam | 1.604 | 1.178 | 0.625 | 2.174 | -0.776 | 1.075 |
| nypm | 1.296 | 0.788 | 0.904 | 0.887 | 1.328 | 4.231 |
| pre | -4.304 | -1.317 | -0.772 | 0.069 | -2.700 | -3.669 |

#### split x ER: spread (hi minus lo) of addfill

| sess | L3M | L6M | HOLD | PRE | X' | 2026 |
|---|---|---|---|---|---|---|
| ALL | 0.006 | 0.013 | 0.013 | 0.000 | 0.015 | 0.013 |
| asia | -0.002 | 0.000 | 0.008 | -0.000 | 0.031 | 0.007 |
| london | 0.005 | 0.017 | 0.016 | -0.010 | 0.014 | -0.000 |
| nyam | 0.018 | 0.019 | 0.014 | 0.011 | 0.012 | 0.029 |
| nypm | -0.009 | 0.013 | 0.010 | 0.002 | 0.018 | 0.014 |
| pre | 0.015 | 0.006 | 0.010 | -0.013 | -0.025 | 0.013 |

#### add-leg-only sizer proxy (approximate, STRUCTURE): scale the 30% add x1.5 / x0.5 by ER

| t | L3M | L6M | HOLD | PRE | X' | 2026 | SEL |
|---|---|---|---|---|---|---|---|
| 0.25 | 0.395 | 0.387 | 0.341 | 0.181 | 0.010 | 0.523 | 0.133 |
| 0.30 | 0.356 | 0.345 | 0.323 | 0.148 | -0.031 | 0.391 | 0.098 |
| 0.35 | 0.287 | 0.232 | 0.216 | 0.131 | 0.054 | 0.211 | 0.108 |

The add-leg-only sizer proxy (scale only the add x1.5 / x0.5 by ER, risk matched on add lots; STRUCTURE-labelled because the proxy assumes a separable add leg): L6M +0.35, HOLD +0.32, PRE +0.15, X' -0.03 pts per planned lot at t=0.3.

## per book (which books carry it)

#### per book: f73 N mean at ER>=.3 minus ER<.3 (pts per planned lot)

| book | L3M | L6M | HOLD | PRE | X' | 2026 | SEL | n_hi L6M |
|---|---|---|---|---|---|---|---|---|
| DN | 5.24 | 3.20 | 2.76 | 0.86 | 1.79 | -2.01 | 1.12 | 301 |
| HM | 3.25 | 4.86 | 4.12 | -2.33 | 0.35 | -0.20 | -1.60 | 345 |
| KB | 8.29 | 8.23 | 8.27 | 1.12 | 2.36 | 8.91 | 1.33 | 448 |
| MA | 1.60 | -0.97 | -1.26 | -1.67 | 7.30 | -10.61 | 1.16 | 156 |
| MV | 0.86 | 0.19 | -0.16 | 1.26 | 7.28 | 3.71 | 2.72 | 460 |
| PB | -4.94 | 1.23 | 1.29 | 2.53 | -2.29 | -0.98 | 1.29 | 375 |
| PE | 5.32 | 5.58 | 4.40 | 4.32 | -2.08 | 3.72 | 2.74 | 485 |
| SM | -3.06 | 3.35 | 4.23 | 0.18 | 1.90 | 6.06 | 0.73 | 152 |
| ST | 8.57 | 6.02 | 6.78 | 5.11 | 0.95 | 13.20 | 4.02 | 473 |
| WT | 2.95 | 2.58 | 2.08 | 0.98 | -1.25 | 2.19 | 0.37 | 538 |

#### per book equal-risk lift of the ER>=.3 2L sizer (pts per planned lot, f73 N)

| book | L3M | L6M | HOLD | PRE | X' | 2026 | SEL | MDE L6M |
|---|---|---|---|---|---|---|---|---|
| DN | 1.38 | 0.84 | 0.73 | 0.23 | 0.47 | -0.50 | 0.29 | 2.31 |
| HM | 0.87 | 1.30 | 1.10 | -0.62 | 0.09 | -0.05 | -0.43 | 2.60 |
| KB | 2.21 | 2.20 | 2.21 | 0.30 | 0.63 | 2.36 | 0.36 | 2.18 |
| MA | 0.43 | -0.26 | -0.34 | -0.45 | 1.96 | -2.84 | 0.31 | 4.66 |
| MV | 0.23 | 0.05 | -0.04 | 0.33 | 1.92 | 0.98 | 0.72 | 2.28 |
| PB | -1.31 | 0.32 | 0.34 | 0.67 | -0.59 | -0.26 | 0.34 | 2.33 |
| PE | 1.42 | 1.49 | 1.17 | 1.14 | -0.54 | 0.99 | 0.72 | 2.54 |
| SM | -0.76 | 0.85 | 1.07 | 0.04 | 0.46 | 1.29 | 0.18 | 4.92 |
| ST | 2.30 | 1.61 | 1.82 | 1.37 | 0.25 | 3.54 | 1.07 | 2.50 |
| WT | 0.78 | 0.68 | 0.55 | 0.26 | -0.33 | 0.58 | 0.10 | 1.35 |

## (e) THE REGIME-SWITCH STACK WITH SIZING (volume kept)

Polarity from PRE+X' only (spread of f73 N at ER>=0.3 vs <0.3): HM = fade (-1.6), all others trend. Trend books x1.5 in trend / x0.5 in chop, fade books the reverse; threshold column t.

#### regime-switch sizing ENG6 (polarity from PRE+X: HM reversed): equal-risk planned-lot lift (f73_N)

| t | L3M | L6M | HOLD | PRE | X' | 2026 |
|---|---|---|---|---|---|---|
| 0.20 | 0.54 | 0.68 | 0.57 | 0.57 | 0.45 | 0.82 |
| 0.25 | 1.19 | 1.07 | 0.96 | 0.79 | 0.20 | 1.53 |
| 0.30 | 1.17 | 1.07 | 1.05 | 0.68 | 0.02 | 1.54 |
| 0.35 | 0.76 | 0.79 | 0.79 | 0.48 | 0.05 | 0.95 |
| 0.40 | 1.34 | 0.96 | 0.99 | 0.53 | 0.05 | 1.32 |

regime-switch stack d $/wk equal-risk (f73_N)

| t | L3M | L6M | HOLD | PRE | X' | 2026 | MDE L6M |
|---|---|---|---|---|---|---|---|
| 0.20 | 9460 | -7025 | -5467 | -3383 | 4107 | 42383 | 37891 |
| 0.25 | 26515 | 2147 | 4185 | 1801 | 6409 | 26267 | 41432 |
| 0.30 | 37584 | 7923 | 11332 | -1325 | 923 | 59475 | 42559 |
| 0.35 | 9247 | -5760 | -2992 | -4940 | 628 | 47158 | 36693 |
| 0.40 | 36892 | 7670 | 8735 | -7435 | -852 | 60709 | 48318 |

regime-switch stack d $/wk unscaled (f73_N)

| t | L3M | L6M | HOLD | PRE | X' | 2026 |
|---|---|---|---|---|---|---|
| 0.20 | 6358 | -4713 | -2468 | -5536 | 4242 | 27261 |
| 0.25 | 27613 | 2350 | 4359 | 1418 | 6024 | 25052 |
| 0.30 | 43249 | 9931 | 12615 | -1143 | 2625 | 47170 |
| 0.35 | 14906 | -6518 | -2932 | -8463 | -648 | 40252 |
| 0.40 | 31366 | -3236 | 876 | -17323 | -7735 | 50670 |

#### regime-switch sizing ENG6 (polarity from PRE+X: HM reversed): equal-risk planned-lot lift (mkt_M)

| t | L3M | L6M | HOLD | PRE | X' | 2026 |
|---|---|---|---|---|---|---|
| 0.20 | 0.49 | 0.64 | 0.54 | 0.50 | 0.47 | 0.68 |
| 0.25 | 1.14 | 1.04 | 0.93 | 0.73 | 0.21 | 1.37 |
| 0.30 | 1.17 | 1.09 | 1.06 | 0.64 | 0.04 | 1.47 |
| 0.35 | 0.82 | 0.87 | 0.85 | 0.45 | 0.06 | 0.96 |
| 0.40 | 1.42 | 1.04 | 1.07 | 0.47 | 0.06 | 1.41 |

regime-switch stack d $/wk equal-risk (mkt_M)

| t | L3M | L6M | HOLD | PRE | X' | 2026 | MDE L6M |
|---|---|---|---|---|---|---|---|
| 0.20 | 20606 | 7212 | 6785 | -8789 | 7340 | 44292 | 36549 |
| 0.25 | 40670 | 14967 | 14577 | 4844 | 9893 | 40721 | 48754 |
| 0.30 | 35561 | -723 | 956 | -1056 | 3976 | 37136 | 44290 |
| 0.35 | 15232 | -856 | -828 | -16147 | 1028 | 42800 | 39796 |
| 0.40 | 48761 | 11871 | 11934 | -15145 | -5610 | 79695 | 43120 |

regime-switch stack d $/wk unscaled (mkt_M)

| t | L3M | L6M | HOLD | PRE | X' | 2026 |
|---|---|---|---|---|---|---|
| 0.20 | 25394 | 5772 | 6081 | -1632 | 6607 | 50903 |
| 0.25 | 41007 | 14238 | 13985 | 5111 | 9567 | 41464 |
| 0.30 | 33675 | -651 | 2661 | 1850 | 4739 | 42881 |
| 0.35 | 15546 | -7755 | -4631 | -10257 | 1514 | 33884 |
| 0.40 | 36740 | 1112 | 3683 | -18027 | -7667 | 54610 |

#### regime-switch sizing ALL10 (incl. MV PB DN MA; trade level only)

| t | L3M | L6M | HOLD | PRE | X' | 2026 |
|---|---|---|---|---|---|---|
| 0.20 | 0.67 | 0.76 | 0.64 | 0.49 | 0.45 | 0.71 |
| 0.25 | 1.23 | 1.05 | 0.92 | 0.61 | 0.39 | 1.42 |
| 0.30 | 0.84 | 0.83 | 0.79 | 0.55 | 0.31 | 1.09 |
| 0.35 | 0.61 | 0.66 | 0.68 | 0.43 | 0.41 | 0.61 |
| 0.40 | 1.03 | 0.94 | 0.98 | 0.47 | 0.28 | 0.89 |

placebo of the regime-switch at t=.3: rank of the chosen polarity among all 64 polarity assignments / among 300 shuffled-ER draws

| kind | SEL | L6M | HOLD | PRE | X | L3M | Y26 |
|---|---|---|---|---|---|---|---|
| real lift | 0.49 | 1.07 | 1.05 | 0.68 | 0.02 | 1.17 | 1.54 |
| rank among 64 polarities | 0.98 | 0.95 | 0.95 | 0.98 | 0.52 | 0.94 | 0.98 |
| rank among shuffled-ER (300) | 1.00 | 1.00 | 1.00 | 1.00 | 0.55 | 0.99 | 0.97 |

Governors ON vs OFF for the regime-switch, the walk-forward chains and the session-limited sizers (stack d $/wk research lots; sd / worst-20 week of the sized stack beside the base's, all-window):

f73 N:

| governors | cell | L3M | L6M | HOLD | PRE | X' | 2026 | ALL | mde_L6M | sd_ALL | sd_base_ALL | w20_ALL | w20_base_ALL |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| on | ER.3 only in asia | 34239 | 26424 | 26943 | -3916 | 1891 | 69668 | 4374 | 37193 | 149760 | 137451 | -182915 | -164897 |
| on | ER.3 only in london | 6661 | 1703 | -559 | -16849 | 1419 | 6543 | -8182 | 24131 | 137922 | 137451 | -179985 | -164897 |
| on | ER.3 only in nyam | 3083 | -1332 | -3620 | 7087 | 2081 | -6320 | 3404 | 19379 | 136179 | 137451 | -163898 | -164897 |
| on | F1|5m.er20|t=0.25|2L | 23130 | 10643 | 11844 | -4306 | 11984 | 36288 | 3915 | 41915 | 147904 | 137451 | -188858 | -164897 |
| on | F1|5m.er20|t=0.3|2L | 35547 | 13309 | 14605 | -10895 | 7520 | 51211 | -127 | 41473 | 150724 | 137451 | -188571 | -164897 |
| on | WF anch | 21458 | 415 | -2831 | -18303 | 2392 | 34580 | -9114 | 50343 | 151964 | 137451 | -196001 | -164897 |
| on | WF roll12 | 29571 | 6293 | 6339 | -16909 | 2392 | 47172 | -6443 | 49233 | 145998 | 137451 | -184100 | -164897 |
| on | WF roll3 | 17224 | -10757 | -5740 | -8397 | 267 | 33025 | -5380 | 46035 | 141334 | 137451 | -174187 | -164897 |
| on | WF roll6 | 38546 | 5565 | 3039 | -17873 | 1313 | 50125 | -7956 | 50248 | 144788 | 137451 | -188133 | -164897 |
| on | regime t=0.25 | 26515 | 2147 | 4185 | 1801 | 6409 | 26267 | 3698 | 41432 | 138218 | 137451 | -163428 | -164897 |
| on | regime t=0.3 | 37584 | 7923 | 11332 | -1325 | 923 | 59475 | 2039 | 42559 | 147414 | 137451 | -178764 | -164897 |
| on | regime t=0.35 | 9247 | -5760 | -2992 | -4940 | 628 | 47158 | -2944 | 36693 | 151509 | 137451 | -195436 | -164897 |
| off | ER.3 only in asia | 36003 | 25744 | 26033 | 5166 | 1252 | 31560 | 8561 | 24570 | 192075 | 179951 | -232290 | -230328 |
| off | ER.3 only in london | -6050 | 1719 | 2229 | -4001 | 848 | -213 | -1284 | 16912 | 185354 | 179951 | -248558 | -230328 |
| off | ER.3 only in nyam | 19994 | 12308 | 8040 | 12713 | -3219 | 14552 | 7175 | 25155 | 193378 | 179951 | -240806 | -230328 |
| off | F1|5m.er20|t=0.25|2L | 54085 | 42302 | 38773 | 16089 | 3974 | 64805 | 17599 | 47248 | 207044 | 179951 | -247756 | -230328 |
| off | F1|5m.er20|t=0.3|2L | 52166 | 44208 | 42101 | 15709 | 1422 | 54476 | 17369 | 41703 | 210227 | 179951 | -254116 | -230328 |
| off | WF anch | 47504 | 43960 | 42852 | 12016 | 13136 | 45018 | 19131 | 46881 | 220789 | 179951 | -253961 | -230328 |
| off | WF roll12 | 44040 | 42201 | 40655 | 7960 | 13136 | 59712 | 16617 | 47160 | 221993 | 179951 | -260179 | -230328 |
| off | WF roll3 | 43819 | 33922 | 33059 | 18583 | 11686 | 42273 | 19905 | 51855 | 206199 | 179951 | -234950 | -230328 |
| off | WF roll6 | 46948 | 38470 | 31266 | 7498 | 9353 | 42938 | 13251 | 49987 | 208268 | 179951 | -254886 | -230328 |
| off | regime t=0.25 | 46900 | 32856 | 29421 | 26728 | 4427 | 55359 | 21080 | 41737 | 199510 | 179951 | -234350 | -230328 |
| off | regime t=0.3 | 41268 | 30811 | 30688 | 23625 | 916 | 55206 | 18753 | 42088 | 204178 | 179951 | -232711 | -230328 |
| off | regime t=0.35 | 21980 | 21566 | 21897 | 17341 | 2314 | 32597 | 14114 | 37121 | 207705 | 179951 | -249860 | -230328 |

market-M:

| governors | cell | L3M | L6M | HOLD | PRE | X' | 2026 | ALL | mde_L6M | sd_ALL | sd_base_ALL | w20_ALL | w20_base_ALL |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| on | ER.3 only in asia | 33024 | 28025 | 26165 | -1862 | 4255 | 56346 | 5939 | 41230 | 143879 | 131257 | -209391 | -192985 |
| on | ER.3 only in london | 7236 | 1003 | -308 | -10089 | 1503 | -2299 | -4701 | 25155 | 135163 | 131257 | -197850 | -192985 |
| on | ER.3 only in nyam | -2642 | -6988 | -7222 | 5461 | 2386 | -16319 | 1902 | 20124 | 131004 | 131257 | -194036 | -192985 |
| on | F1|5m.er20|t=0.25|2L | 39724 | 23905 | 21800 | 2331 | 13551 | 36158 | 9857 | 47702 | 144285 | 131257 | -204422 | -192985 |
| on | F1|5m.er20|t=0.3|2L | 38885 | 9479 | 9392 | -5595 | 10198 | 38167 | 2212 | 46846 | 144721 | 131257 | -218838 | -192985 |
| on | WF anch | 19144 | 5095 | 1678 | -23106 | 4204 | 45742 | -10029 | 51964 | 146749 | 131257 | -222850 | -192985 |
| on | WF roll12 | 23710 | 7382 | 6381 | -20284 | 4204 | 37552 | -7598 | 50535 | 141897 | 131257 | -206452 | -192985 |
| on | WF roll3 | 33584 | -1919 | -654 | -9276 | 934 | 32570 | -4534 | 48262 | 137108 | 131257 | -197750 | -192985 |
| on | WF roll6 | 50337 | 11505 | 7496 | -19666 | 1830 | 72637 | -7749 | 52642 | 140915 | 131257 | -207150 | -192985 |
| on | regime t=0.25 | 40670 | 14967 | 14577 | 4844 | 9893 | 40721 | 8490 | 48754 | 137054 | 131257 | -193155 | -192985 |
| on | regime t=0.3 | 35561 | -723 | 956 | -1056 | 3976 | 37136 | 848 | 44290 | 141038 | 131257 | -199192 | -192985 |
| on | regime t=0.35 | 15232 | -856 | -828 | -16147 | 1028 | 42800 | -8002 | 39796 | 146900 | 131257 | -218585 | -192985 |
| off | ER.3 only in asia | 35797 | 24943 | 25449 | 4710 | 1346 | 28833 | 8234 | 24024 | 187667 | 177407 | -296938 | -293058 |
| off | ER.3 only in london | -3518 | 2367 | 2802 | -2839 | 1439 | 3169 | -402 | 15740 | 184589 | 177407 | -315126 | -293058 |
| off | ER.3 only in nyam | 19774 | 12979 | 9179 | 11679 | -2616 | 15373 | 7078 | 24768 | 188821 | 177407 | -296429 | -293058 |
| off | F1|5m.er20|t=0.25|2L | 54396 | 41580 | 39141 | 15571 | 4986 | 63338 | 17716 | 48045 | 202076 | 177407 | -301447 | -293058 |
| off | F1|5m.er20|t=0.3|2L | 56086 | 46544 | 44868 | 15685 | 2676 | 57229 | 18321 | 41210 | 205925 | 177407 | -308397 | -293058 |
| off | WF anch | 49838 | 44952 | 43842 | 11555 | 13084 | 43915 | 19096 | 45269 | 215168 | 177407 | -313911 | -293058 |
| off | WF roll12 | 45087 | 42558 | 41470 | 6527 | 13084 | 59802 | 16055 | 46388 | 216849 | 177407 | -324564 | -293058 |
| off | WF roll3 | 43134 | 34163 | 33882 | 16882 | 11756 | 42514 | 19246 | 51580 | 200850 | 177407 | -293217 | -293058 |
| off | WF roll6 | 48848 | 39333 | 33151 | 6935 | 9341 | 45423 | 13369 | 48186 | 203560 | 177407 | -317260 | -293058 |
| off | regime t=0.25 | 46951 | 32867 | 29382 | 24608 | 4308 | 52196 | 19969 | 42246 | 191175 | 177407 | -289864 | -293058 |
| off | regime t=0.3 | 43852 | 33330 | 32499 | 22053 | 642 | 55516 | 18269 | 41792 | 196369 | 177407 | -284415 | -293058 |
| off | regime t=0.35 | 25830 | 25033 | 24424 | 15624 | 1572 | 35021 | 13574 | 37139 | 201108 | 177407 | -296632 | -293058 |

## (f) WALK-FORWARD CHAIN OF THE THRESHOLD

#### walk-forward chain of the threshold: equal-risk planned-lot lift (f73_N)

| chain | L3M | L6M | HOLD | PRE | X' | 2026 | SEL |
|---|---|---|---|---|---|---|---|
| anch | 1.15 | 1.22 | 1.29 | 0.34 | 0.61 | 1.20 | 0.41 |
| roll12 | 0.96 | 1.11 | 1.15 | 0.26 | 0.61 | 1.49 | 0.35 |
| roll3 | 1.03 | 0.91 | 0.91 | 0.58 | 0.61 | 1.04 | 0.59 |
| roll6 | 1.21 | 1.07 | 0.90 | 0.28 | 0.46 | 1.10 | 0.33 |

chain stack d $/wk equal-risk (f73_N)

| chain | L3M | L6M | HOLD | PRE | X' | 2026 | MDE L6M |
|---|---|---|---|---|---|---|---|
| anch | 21458 | 415 | -2831 | -18303 | 2392 | 34580 | 50343 |
| roll12 | 29571 | 6293 | 6339 | -16909 | 2392 | 47172 | 49233 |
| roll3 | 17224 | -10757 | -5740 | -8397 | 267 | 33025 | 46035 |
| roll6 | 38546 | 5565 | 3039 | -17873 | 1313 | 50125 | 50248 |

#### walk-forward chain of the threshold: equal-risk planned-lot lift (mkt_M)

| chain | L3M | L6M | HOLD | PRE | X' | 2026 | SEL |
|---|---|---|---|---|---|---|---|
| anch | 1.18 | 1.24 | 1.30 | 0.33 | 0.61 | 1.14 | 0.40 |
| roll12 | 0.97 | 1.12 | 1.17 | 0.22 | 0.61 | 1.46 | 0.33 |
| roll3 | 1.01 | 0.92 | 0.93 | 0.53 | 0.62 | 1.01 | 0.55 |
| roll6 | 1.23 | 1.09 | 0.94 | 0.27 | 0.47 | 1.15 | 0.32 |

chain stack d $/wk equal-risk (mkt_M)

| chain | L3M | L6M | HOLD | PRE | X' | 2026 | MDE L6M |
|---|---|---|---|---|---|---|---|
| anch | 19144 | 5095 | 1678 | -23106 | 4204 | 45742 | 51964 |
| roll12 | 23710 | 7382 | 6381 | -20284 | 4204 | 37552 | 50535 |
| roll3 | 33584 | -1919 | -654 | -9276 | 934 | 32570 | 48262 |
| roll6 | 50337 | 11505 | 7496 | -19666 | 1830 | 72637 | 52642 |

placebo of the roll6 chain: shuffled-ER chain (100 draws)

| kind | SEL | L6M | HOLD | PRE | X | L3M | Y26 |
|---|---|---|---|---|---|---|---|
| real | 0.33 | 1.07 | 0.90 | 0.28 | 0.46 | 1.21 | 1.10 |
| placebo mean | 0.01 | -0.02 | 0.00 | 0.00 | 0.01 | -0.08 | -0.12 |
| rank | 0.98 | 1.00 | 1.00 | 0.93 | 0.90 | 0.99 | 0.97 |

#### chain thresholds by month (NaN = sizing off) - last 14 months; the last row is the last re-fit

| month | anch | roll12 | roll3 | roll6 |
|---|---|---|---|---|
| 202501.00 | 0.45 | 0.40 | 0.40 | 0.40 |
| 202502.00 | 0.45 | 0.40 | 0.20 | 0.40 |
| 202503.00 | 0.45 | 0.40 | 0.20 | 0.40 |
| 202504.00 | 0.45 | 0.40 | 0.20 | 0.20 |
| 202505.00 | 0.45 | 0.40 | 0.45 | 0.20 |
| 202506.00 | 0.45 | 0.45 | 0.45 | 0.45 |
| 202507.00 | 0.45 | 0.40 | 0.30 | 0.20 |
| 202508.00 | 0.45 | 0.45 | 0.30 | 0.45 |
| 202509.00 | 0.45 | 0.45 | 0.30 | 0.30 |
| 202510.00 | 0.45 | 0.45 | 0.45 | 0.45 |
| 202511.00 | 0.45 | 0.45 | 0.25 | 0.30 |
| 202512.00 | 0.45 | 0.25 | 0.25 | 0.30 |
| 202601.00 | 0.45 | 0.30 | 0.30 | 0.40 |
| 202602.00 | 0.45 | 0.30 | 0.40 | 0.40 |

## (d) ER x SUB-MINUTE CONFIRMATION - PENDING

C2's `out/confirm2` is empty; CF-SUBMIN's S2 recent look (`out/confirm/submin/look/*.pkl`, per-trade `dx` = confirmed cell minus floor for all 44,370 signals) is 34/67 done. When it finishes this section will give, for the selected PE / KB (and the other ENG6) cells: mean dx at ER>=0.3 vs <0.3 per window, the confirmed-cell outcome sized by the ER sizer (equal risk), and the stack line. Not done yet; no number is claimed.

## Method notes and defects

* Sizer cells never skip: m is 0.5 / 1.0 / 1.5 on every ENG6 signal; NaN ER (warm-up) = 1.0. Equal-risk constant = Sum lots / Sum (m x lots) on PRE+X' (fixed), so no look at the recent windows enters the normalisation. The chain uses the per-month version (causal by construction).
* Stack lines use the TG-1 `Stack` wrapper over `de_engine.run_rows` (busy rule per book, ST10 HM10 WT7 KB5.2 SM7.4 PE5.6 research lots, BASE governors). Admitted rows only are 18,386 of 29,800 ENG6 signals on f73 N; the lock-admitted, research-lots-weighted trade-level lift of the same sizer is +1.34 L6M / +0.62 PRE / -0.11 X' (`adm_lift.parquet`), so the lock/weights do not explain the PRE stack gap; the governors do (OFF: +15.7k PRE).
* The shuffled-ER placebo permutes the multiplier within book x month among ENG6 trades (same marginal, same fire rate); the stack placebo uses 100 draws. The lot-factor-matched uniform line is the `uniform_unscaled` frame.
* Multiplicity honest count: 52 sizer cells x 4-5 bases, 10 regime cells (5 thresholds x ENG6/ALL10), 4 chains, 15 session-limited, 3 add-leg proxies = 84 cells appended to UF_TRIALS (side `plan36_trend2`) and to DEAD_CELLS (52 sizer specs, program PLAN36_T2); the 924,611-cell TG-1 program also scored tercile 0.5/1/1.5 sizers on ER and every other trend measure (565 selected sizers: mean L6M risk-matched lift +0.04); the directive-named ER20 5-min thresholds are the same family as TG-1's lead, so this pass is a unit/sizing re-read, not independent evidence.
* RECENT_WINS rows: `l2vast/ds3/out/recent_wins/trend2.csv` (49 L6M-positive view rows). Files: `score_trade.parquet`, `score_stack_{f73_N,mkt_M,f73_M}.parquet`, `gov.parquet`, `gov2.parquet`, `regime*.parquet`, `wf_*.parquet`, `qv_header.parquet`, `bsplit.parquet`, `state_table.parquet`, `tables.md`, `tables2.md`.
