# DS3_PBX_FINAL - T-PBX: pullback entries x brackets x exits x bars x order types x tape (D3PX, 2026-10-28)

Research output; NOT a live recommendation. All numbers MAPPED conservative basis (nominal 1-s path points + min(P9 exit-type correction, 0), $4.84/contract, sweep surcharge above 14 lots; stop-join credit NOT given) unless the direct-stage section says otherwise. Unit = 10-lot-equivalent pts/trade (pts x lots/10, $200 per pt). Every effect "vs random-in-regime" is the real mean minus the mean of 16 random-in-regime draws with the same bracket, lots and pipeline (placebo (b)); (c) = also inside the ER gate, used for the PRO_ER families in block (i); (a) = timing-destroyed.

## 1. Verdict

**Pullback brackets: does any stop x exit make the pullback entry beat random-in-regime? no robust cell (best of block (i): PBX_PRO_ER5_EMA5_f40_T3, +7.66 pts/trade [-0.97, +16.82], verdict DEAD).**

Cells scored: 332 non-control cells in 5 scoring blocks plus controls (42). PASS: 0. CANDIDATE: 2 (PBX_PB_ST10_SWZ_T3_f60_T3, PBX_PB_ST10_SWZ_T3_f60_SW). All other cells DEAD. Verdict counts by block:

| blk   |   CANDIDATE |   CONTROL (base) |   DEAD |
|:------|------------:|-----------------:|-------:|
| i     |           2 |                6 |    184 |
| ii    |           0 |               28 |     84 |
| iii   |           0 |                4 |     20 |
| iii-b |           0 |                4 |     12 |
| iv    |           0 |                0 |     30 |

Multiplicity: 22 of 332 cells have a paired CI above 0 against their own market/base control; 33 have a CI above 0 vs random-in-regime. Blocks: (i) 192 stop x exit cells on 6 pullback families (autopilot/DS3_TPBX.md); (ii) 112 cells across 14 NT8-native bar types (DS3_TPBX_B2.md); (iii) 24 order-type cells and (iii-b) 16 touch-rule limit cells (DS3_TPBX_B3.md, B3B.md); (iv) 30 tape/footprint trigger cells (DS3_TPBX_B4.md); (v) robustness of the top 3 below.

## 2. Top 10 cells by effect vs random-in-regime, regardless of verdict (failed gate, by how much, MDE, forward weeks)

ER-family cells of blocks (iii)/(iv) are EXCLUDED from this ranking: their random arms were not ER-gated (placebo (c) exists only in block (i)), so their effects (up to +20 pts, all with CIs including 0 or inflated by the gate itself) are artefacts of the placebo, not results; they remain in the block files.

| rank | block | cell | verdict | effect vs random-in-regime [CI] | WF / HOLD / 2023 wk $ (locked) | failed gates, by how much | paired MDE (pts) | forward weeks (rough) |
|---|---|---|---|---|---|---|---|---|
| 1 | i | PBX_PRO_ER5_EMA5_f40_T3 | DEAD | +7.66 [-0.97,+16.82] r1.00 | +7,476 / +8,403 / -2,000 | paired_CI_excludes0&maxDD_not_worse (CI lower +3.24 > 0, so the maxDD-not-worse part failed; MDE 10.83); maxDD_not_worse(full sequence); SPAN2<=0 (2023-span paired -9.26); beats_(b)_CI_includes_0 (CI lower -0.97, needs > 0) | 10.83 | 386 |
| 2 | i | PBX_PRO_ER5_EMA5_f40_SW | DEAD | +5.47 [-0.71,+12.01] r1.00 | +5,292 / +3,956 / -3,100 | paired_CI_excludes0&maxDD_not_worse (paired CI lower -1.30, needs > 0; MDE 6.93); SPAN2<=0 (2023-span paired -8.31); beats_(b)_CI_includes_0 (CI lower -0.71, needs > 0) | 6.93 | 402 |
| 3 | i | PBX_PRO_ER5_EMA5_f60_T2 | DEAD | +5.37 [-1.54,+12.33] r1.00 | +6,161 / +6,323 / +1,148 | neighbours_agree; paired_CI_excludes0&maxDD_not_worse (CI lower +1.06 > 0, so the maxDD-not-worse part failed; MDE 7.31); maxDD_not_worse(full sequence); SPAN2<=0 (2023-span paired -2.72); year_share>60%; beats_(b)_CI_includes_0 (CI lower -1.54, needs > 0) | 7.31 | 480 |
| 4 | iv | PBX4_PBS_f60_T3_STK | DEAD | +5.20 [+2.56,+7.69] r1.00 | +11,056 / +13,693 / +4,447 | neighbours_agree; paired_CI_excludes0&maxDD_not_worse (paired CI lower -2.47, needs > 0; MDE 3.53); SPAN2<=0 (2023-span paired -0.29) | 3.53 | 70 |
| 5 | i | PBX_PRO_ER5_EMA5_pe10_T3 | DEAD | +5.04 [-3.62,+13.54] r0.94 | -2,251 / +2,603 / -3,451 | mean_up (paired effect vs base <= 0); paired_CI_excludes0&maxDD_not_worse (paired CI lower -10.64, needs > 0; MDE 11.89); placebo<0.95; SPAN2<=0 (2023-span paired -8.16); 2x_cost<=0 (2x WF wk -6,685 $); year_share>60%; beats_(b)_CI_includes_0 (CI lower -3.62, needs > 0) | 11.89 | 858 |
| 6 | iv | PBX4_PBS_f60_T3_CLZ | DEAD | +4.96 [-5.26,+14.90] r0.94 | -636 / -455 / +4,617 | mean_up (paired effect vs base <= 0); holdout_sign_agrees (HOLD paired <= 0); neighbours_agree; paired_CI_excludes0&maxDD_not_worse (paired CI lower -3.81, needs > 0; MDE 4.28); placebo<0.95; SPAN2<=0 (2023-span paired -0.75); 2x_cost<=0 (2x WF wk -821 $); beats_(b)_CI_includes_0 (CI lower -5.26, needs > 0) | 4.28 | 1210 |
| 7 | i | PBX_PRO_ER5_EMA5_pe5_SW | DEAD | +4.92 [-4.19,+14.29] r0.75 | -2,321 / +242 / -4,145 | mean_up (paired effect vs base <= 0); placebo>=0.90; paired_CI_excludes0&maxDD_not_worse (paired CI lower -14.93, needs > 0; MDE 11.89); SPAN2<=0 (2023-span paired -16.40); 2x_cost<=0 (2x WF wk -5,188 $); year_share>60%; beats_(b)_CI_includes_0 (CI lower -4.19, needs > 0) | 11.89 | 997 |
| 8 | i | PBX_PRO_ER4_EMA5_pe10_STB | DEAD | +4.83 [-3.70,+14.23] r0.81 | -3,767 / -5,409 / -11,402 | placebo>=0.90; paired_CI_excludes0&maxDD_not_worse (paired CI lower -6.00, needs > 0; MDE 14.40); SPAN2<=0 (2023-span paired -11.35); year_share>60%; beats_(b)_CI_includes_0 (CI lower -3.70, needs > 0) | 14.40 | 1000 |
| 9 | i | PBX_PRO_ER4_EMA5_pe10_FLIP | DEAD | +4.69 [-3.90,+14.50] r0.94 | +302 / -4,037 / -19,251 | paired_CI_excludes0&maxDD_not_worse (paired CI lower -5.88, needs > 0; MDE 15.73); placebo<0.95; SPAN2<=0 (2023-span paired -19.26); beats_(b)_CI_includes_0 (CI lower -3.90, needs > 0) | 15.73 | 1081 |
| 10 | iii | PBX3_PBS_f60_T3_SE | DEAD | +4.58 [+2.37,+6.80] r1.00 | +11,659 / +20,942 / +8,726 | neighbours_agree; paired_CI_excludes0&maxDD_not_worse (paired CI lower -1.41, needs > 0; MDE 2.60); SPAN2<=0 (2023-span paired -0.49) | 2.60 | 72 |

Forward weeks = weeks of forward data for the standard error of the cell's weekly pre-lock effect vs random-in-regime to fall to 1/2.8 of that effect (80% power), scaled from the WF bootstrap; a planning number. At 50k $/wk weekly SD, even the best cells need on the order of a year or more of forward data.

## 3. RECOMMENDED-FOR-SIM

No cell meets the line (best deliverable cell with a positive direct-basis holdout and a non-negative DS3 marginal line).

Blocking gates, with the random-in-regime placebo beside the leads:

- PB_ST10_SWZ_T3 f60 + swing trail (block (i) CANDIDATE, failed beats_(b)_CI_includes_0): effect vs random-in-regime +1.44 [-0.39,+3.18]; DS3 add-one marginal Sharpe negative (WF -0.30, HOLD -0.08); direct-basis section below.
- PB_ST10_SWZ_T3 f60 + 3R target (block (i) CANDIDATE, fails SPAN2): marginal Sharpe WF -0.32, HOLD -0.07.
- Block (iii)/(iv) leads (PBS_f60_T3 stop-entry; PBS_f60_T3 stacked-imbalance trigger) are paired-neutral vs their market control (+0.4 / +0.0 pts per arm), have a negative 2023-span per-arm effect, and the stop-entry is mapped without stop slippage; the stacked-imbalance trigger is execution-server-only.
Forward-register entry: ds3_TPBX_PB_ST10_SWZ_T3_f60_SW (mapped-screen lead only, struct48/paper_all). Provisional spec: DS3_SPEC_PB_ST10_SWZ_T3.md section 1 with the exit of DS3_TPBX.md section "RECOMMENDED-FOR-SIM" (no 1R target, 60-pt initial stop, 1-min fractal-swing trail -5 after +1R); the exit was not independently replayed (identity test pending).

## 4. Structural read: which axis moved the delta

Effect vs random-in-regime, pts/trade (10-lot-equivalent). Paired columns are vs the same entry's market / 60-1R control. ER5 cells excluded from the order-type and tape axes (ungated placebo).

Family (block (i)):

| family | cells | mean paired vs control | mean effect vs random-in-regime +/- 1.96 SE | cells with CI > 0 |
|---|---|---|---|---|
| PB3B_R5_P1 | 31.0 | -1.05 | -0.02 +/- 0.21 | 0.0 |
| PB3B_R5_P2 | 31.0 | -0.57 | +0.74 +/- 0.36 | 6.0 |
| PB3B_R60_P2 | 31.0 | -0.74 | +0.83 +/- 0.37 | 6.0 |
| PB_ST10_SWZ_T3 | 31.0 | -1.61 | +0.52 +/- 0.47 | 2.0 |
| PRO_ER4_EMA5 | 31.0 | -0.01 | +1.62 +/- 0.50 | 0.0 |
| PRO_ER5_EMA5 | 31.0 | -2.61 | +1.11 +/- 1.15 | 0.0 |

Stop (block (i)):

| stop | cells | mean paired vs control | mean effect vs random-in-regime +/- 1.96 SE | cells with CI > 0 |
|---|---|---|---|---|
| f40 | 48.0 | +1.94 | +1.05 +/- 0.50 | 0.0 |
| f60 | 42.0 | +1.74 | +0.68 +/- 0.42 | 2.0 |
| pe10 | 48.0 | -3.37 | +0.83 +/- 0.62 | 12.0 |
| pe5 | 48.0 | -4.35 | +0.64 +/- 0.40 | 0.0 |

Exit (block (i)):

| exit | cells | mean paired vs control | mean effect vs random-in-regime +/- 1.96 SE | cells with CI > 0 |
|---|---|---|---|---|
| CH | 24.0 | -1.13 | +0.91 +/- 0.49 | 2.0 |
| FLIP | 24.0 | +1.63 | +0.38 +/- 0.87 | 2.0 |
| STB | 24.0 | +1.32 | +0.60 +/- 0.72 | 2.0 |
| SW | 24.0 | -1.38 | +1.17 +/- 0.65 | 1.0 |
| T1 | 18.0 | -6.69 | +0.32 +/- 0.74 | 2.0 |
| T2 | 24.0 | -2.60 | +0.65 +/- 0.64 | 0.0 |
| T3 | 24.0 | -0.49 | +1.33 +/- 0.92 | 3.0 |
| TR30 | 24.0 | -0.85 | +0.94 +/- 0.46 | 2.0 |

Bar type (block (ii), 3 brackets x 2 regimes per bar):

| bar | cells | mean paired vs control | mean effect vs random-in-regime +/- 1.96 SE | cells with CI > 0 |
|---|---|---|---|---|
| range_20 | 6.0 | -1.33 | +1.44 +/- 1.04 | 1.0 |
| range_40 | 6.0 | -1.92 | +1.05 +/- 0.63 | 1.0 |
| range_60 | 6.0 | -1.15 | +0.53 +/- 0.82 | 0.0 |
| renko_20 | 6.0 | -1.49 | +1.26 +/- 0.60 | 0.0 |
| renko_40 | 6.0 | +0.15 | +2.25 +/- 0.79 | 1.0 |
| tick_1000 | 6.0 | -0.12 | -0.24 +/- 1.09 | 0.0 |
| tick_2000 | 6.0 | +0.32 | +0.22 +/- 0.92 | 0.0 |
| tick_250 | 6.0 | -1.03 | +0.37 +/- 1.20 | 1.0 |
| tick_500 | 6.0 | -1.02 | +1.64 +/- 1.08 | 1.0 |
| time_15s | 6.0 | -1.43 | +0.88 +/- 0.96 | 1.0 |
| time_1m | 6.0 | -0.60 | +0.25 +/- 0.74 | 0.0 |
| time_30s | 6.0 | -0.99 | +1.19 +/- 1.01 | 2.0 |
| volume_1000 | 6.0 | -0.40 | +1.13 +/- 0.54 | 0.0 |
| volume_2500 | 6.0 | +0.09 | +0.54 +/- 0.86 | 0.0 |

Order type (blocks (iii)+(iii-b), 3 non-ER cells):

| order | cells | mean paired vs control | mean effect vs random-in-regime +/- 1.96 SE | cells with CI > 0 |
|---|---|---|---|---|
| L10 | 3.0 | -1.03 | -0.11 +/- 2.89 | 0.0 |
| L10T | 3.0 | -0.99 | -0.19 +/- 2.99 | 0.0 |
| L30 | 3.0 | -1.05 | -0.08 +/- 2.86 | 0.0 |
| L30T | 3.0 | -0.99 | -0.16 +/- 2.93 | 0.0 |
| LAD | 3.0 | -0.93 | -0.53 +/- 3.15 | 0.0 |
| LADT | 3.0 | -0.86 | -0.63 +/- 3.17 | 0.0 |
| SC | 3.0 | -1.90 | +1.87 +/- 1.15 | 2.0 |
| SE | 3.0 | -0.16 | +1.74 +/- 3.56 | 2.0 |

Tape trigger (block (iv), 2 non-ER families):

| trigger | cells | mean paired vs control | mean effect vs random-in-regime +/- 1.96 SE | cells with CI > 0 |
|---|---|---|---|---|
| ABS | 2.0 | -0.88 | +0.36 +/- 1.75 | 0.0 |
| BOOK | 2.0 | -0.54 | -0.55 +/- 3.00 | 0.0 |
| CDBOS | 2.0 | -0.53 | +1.23 +/- 2.08 | 0.0 |
| CLZ | 2.0 | -1.09 | +3.47 +/- 2.94 | 0.0 |
| DFLIP | 2.0 | +0.25 | +1.87 +/- 1.48 | 1.0 |
| DIV | 2.0 | -0.67 | +0.39 +/- 1.92 | 0.0 |
| LP | 2.0 | -0.59 | +2.05 +/- 4.67 | 1.0 |
| PBOS | 2.0 | -0.67 | +0.64 +/- 0.37 | 0.0 |
| RUN | 2.0 | +0.36 | +1.01 +/- 3.46 | 1.0 |
| STK | 2.0 | -0.39 | +3.15 +/- 4.00 | 1.0 |

Reading: (1) The pullback location itself, measured against random timing inside the same regime, is worth about 0 on the three PB3B families and about +0.5 on PB_ST10_SWZ_T3; the large positive means on the PRO_ER families are removed once the placebo is conditioned on the ER gate (block (i) placebo (c)). (2) Stop: pullback-extreme stops are worse than fixed stops against the 60/1R base (noise stops plus the sweep surcharge at 24-42 lots; 45-80% of their trades exceed the 23-lot line beside DS2) and do not move the effect against the random placebo because the placebo gets the same stop construction. (3) Exit: 1R is the worst exit; runners (3R, flip, Supertrend-band trail) are best; spreads are about one SE. (4) Bar type: no bar type separates from the 1-min baseline; effects are within the MDE. (5) Order type: no limit, ladder, stop-entry or scale-in variant beats the market entry on a per-arm basis with a CI above 0 (adverse selection: limits fill in the pullbacks that continue). (6) Tape: only absorption and price BOS are 1-min-bar proxyable; no tape trigger beats the base trigger per arm. An axis that mattered at all: exit and stop through cost (sweep surcharge, friction), not through the entry location.

## 5. Power statement

Per-trade paired MDE (80% power, bootstrap SE over session blocks), median over the family's 32 block (i) cells, pts/trade 10-lot-equivalent: PB3B_R5_P1 2.8, PB3B_R5_P2 3.1, PB3B_R60_P2 3.2, PB_ST10_SWZ_T3 3.6, PRO_ER4_EMA5 7.2, PRO_ER5_EMA5 10.8. Block (ii) per-bar MDEs are 3.2-6.2; block (iii)/(iv) per-arm MDEs 0.6-5 (1.4-2.9 typical for the PBS and PB3 cells). The smallest effect the design could have seen is therefore about 3-4 pts/trade (about $600-800 per 10-lot trade) per family at one cell; a pullback-location effect below that was not excluded. Weekly MDE at 80% power on 142 WF weeks with SD about 55k $/wk is about 13k $/wk. Honest summary: the design could reject an effect of +4 pts/trade or more per cell; the observed best cells (+2..+5 vs random-in-regime) sit at or below the MDE and are indistinguishable from the best-of-N null (best-of-N rank in the 0.6-0.9 range).

## 6. Block (v): robustness of the top 3 cells overall

Selection rule (fixed before the numbers were read): rank by effect vs random-in-regime over all scored cells; eligible = CI vs (b) lower bound > 0 and locked WF, HOLD and 2023-span weekly means all > 0, not a control, not an ER-family cell of blocks (iii)-(iv) (ungated placebo). All three are DEAD or at best paired-neutral: they are shown to document how they fail, not as candidates.

### PBX4_PBS_f60_T3_STK (block iv, verdict DEAD, failed: neighbours_agree; paired_CI_excludes0&maxDD_not_worse (paired CI lower -2.47, needs > 0; MDE 3.53); SPAN2<=0 (2023-span paired -0.29))

- Trades 2605; effect vs random-in-regime +5.20 [+2.56,+7.69], vs timing-destroyed (a) +5.93; paired vs control +0.02 [-2.47,+2.46].
- Locked weekly $ (mean / SD / maxDD), cost 1x / 1.5x / 2x: WF +11,056 / 52,630 / 257,845; +9,435; +8,509. HOLD +13,693 / +11,361 / +10,535. 2023 span +4,447 / +3,406 / +2,365.
- Day-block bootstrap (WF, 3000 draws) maxDD median [5-95%] and worst 5-day: b=1: 403,035 [251,687, 741,161], worst5d -120,484; b=5: 358,347 [228,869, 635,439], worst5d -110,284; b=10: 308,440 [206,242, 517,466], worst5d -110,284.
- VIX terciles (WF weeks, mean $/wk): low +7,911 (54 wk), mid +13,091 (39 wk), high +12,864 (50 wk).
- Friction sensitivity (pre-lock weekly $ for +0 / 0.5 / 1 / 2 / 3 extra pts RT per contract): +14,551 / +13,058 / +11,565 / +8,579 / +5,593. Direct-replay latency arms (5/50/150 ms) were not run for these cells.
- Long / short mean pts: +3.77 (n 1077) / +6.00 (n 1058). Session (Asia / London / NY): +7.87 (n 605) / +1.14 (n 564) / +5.18 (n 966). Quiet / wide: -0.38 (n 686) / +7.46 (n 1426).
- Counter-trend mirror (same entries, opposite side, same exit): -2.81 pts/trade vs real +4.87.
- Capacity (equal_risk surface): lots_equal_risk 10.854799361282174, pnl_wk_equal_risk 12002.604436224326, capacity_lots_zero_mean 146.0, practical_ceiling_lots 29.0, delta_vs_st_equal_risk -2347.3357720183285.
- Stability surface: neighbouring cells in the same block tables (adjacent stop / exit / bar / order type) are in the block files; the cell is not a stable local maximum (neighbours_agree failed or paired effect not above zero).

### PBX3_PBS_f60_T3_SE (block iii, verdict DEAD, failed: neighbours_agree; paired_CI_excludes0&maxDD_not_worse (paired CI lower -1.41, needs > 0; MDE 2.60); SPAN2<=0 (2023-span paired -0.49))

- Trades 2911; effect vs random-in-regime +4.58 [+2.37,+6.80], vs timing-destroyed (a) +6.39; paired vs control +0.44 [-1.41,+2.22].
- Locked weekly $ (mean / SD / maxDD), cost 1x / 1.5x / 2x: WF +11,659 / 53,604 / 319,095; +10,677; +9,194. HOLD +20,942 / +19,891 / +17,818. 2023 span +8,726 / +7,709 / +6,652.
- Day-block bootstrap (WF, 3000 draws) maxDD median [5-95%] and worst 5-day: b=1: 388,114 [244,593, 703,050], worst5d -120,484; b=5: 363,544 [232,919, 644,752], worst5d -120,484; b=10: 341,960 [223,915, 598,088], worst5d -120,484.
- VIX terciles (WF weeks, mean $/wk): low +15,733 (54 wk), mid +9,459 (39 wk), high +8,976 (50 wk).
- Friction sensitivity (pre-lock weekly $ for +0 / 0.5 / 1 / 2 / 3 extra pts RT per contract): +16,790 / +15,113 / +13,436 / +10,082 / +6,728. Direct-replay latency arms (5/50/150 ms) were not run for these cells.
- Long / short mean pts: +4.74 (n 1206) / +5.27 (n 1192). Session (Asia / London / NY): +3.94 (n 932) / +4.31 (n 568) / +6.56 (n 898). Quiet / wide: +0.67 (n 805) / +7.22 (n 1568).
- Counter-trend mirror (same entries, opposite side, same exit): -2.47 pts/trade vs real +5.01.
- Capacity (equal_risk surface): lots_equal_risk 10.738417005554048, pnl_wk_equal_risk 11930.032089030849, capacity_lots_zero_mean 130.0, practical_ceiling_lots 27.0, delta_vs_st_equal_risk -2419.9081192118065.
- Stability surface: neighbouring cells in the same block tables (adjacent stop / exit / bar / order type) are in the block files; the cell is not a stable local maximum (neighbours_agree failed or paired effect not above zero).

### PBX_PB3B_R60_P2_pe10_FLIP (block i, verdict DEAD, failed: neighbours_agree; paired_CI_excludes0&maxDD_not_worse (paired CI lower -2.46, needs > 0; MDE 8.24); SPAN2<=0 (2023-span paired -4.72); year_share>60%)

- Trades 4492; effect vs random-in-regime +3.80 [+0.61,+6.96], vs timing-destroyed (a) +3.70; paired vs control +2.91 [-2.46,+9.10].
- Locked weekly $ (mean / SD / maxDD), cost 1x / 1.5x / 2x: WF +3,988 / 76,264 / 506,266; -1,268; -4,762. HOLD +7,869 / -455 / -3,132. 2023 span +2,678 / -8,797 / -19,834.
- Day-block bootstrap (WF, 3000 draws) maxDD median [5-95%] and worst 5-day: b=1: 793,999 [448,214, 1,617,768], worst5d -140,399; b=5: 779,218 [432,015, 1,496,533], worst5d -137,796; b=10: 725,704 [416,660, 1,414,562], worst5d -137,796.
- VIX terciles (WF weeks, mean $/wk): low -2,176 (54 wk), mid -6,309 (39 wk), high +18,677 (50 wk).
- Friction sensitivity (pre-lock weekly $ for +0 / 0.5 / 1 / 2 / 3 extra pts RT per contract): +9,631 / +3,970 / -1,690 / -13,011 / -24,332. Direct-replay latency arms (5/50/150 ms) were not run for these cells.
- Long / short mean pts: +1.91 (n 1807) / +1.89 (n 1811). Session (Asia / London / NY): +8.82 (n 1204) / +0.87 (n 1084) / -3.51 (n 1330). Quiet / wide: -0.04 (n 1217) / +3.49 (n 2354).
- Counter-trend mirror (same entries, opposite side, same exit): -0.59 pts/trade vs real +1.90.
- Capacity (equal_risk surface): lots_equal_risk 17.23518099513151, pnl_wk_equal_risk 5464.773248378674, capacity_lots_zero_mean 31.0, practical_ceiling_lots 24.0, delta_vs_st_equal_risk -8885.166959863982.
- Stability surface: neighbouring cells in the same block tables (adjacent stop / exit / bar / order type) are in the block files; the cell is not a stable local maximum (neighbours_agree failed or paired effect not above zero).

## 7. Direct L2 basis (PB_ST10_SWZ_T3 f60 cells)

# DS3_TPBX_DIRECT - direct-L2 basis for the PB_ST10_SWZ_T3 f60 cells (D3PX, PARTIAL: D3XT months 19/45)

Research output. Cells: PBX_PB_ST10_SWZ_T3_f60_{T1 (control), SW, T3} (the two block (i) mapped CANDIDATEs and the 60/1R base). Entries S10x1 gap-2 s and exits XJ touch-join / 10-lot market from D3XT's replay (identical event keys; pbx_dprep: 0 new events; nominal identity of f60_T1 vs D3XT PBS BASE rows: {"n_mine": 6092, "n_d3xt": 6092, "n_matched": 6092, "k_equal": 1.0, "px_equal": 1.0, "reason_equal": 1.0}). Price basis: raw L2 prices with the per-bar real-minus-adjusted offset (dc_asm.adj_arr). 10 lots (fixed 60 stop, $12,000 risk), per-book locks.

| cell | missing entry / exit fills | n pairs WF | direct mean pts/trade WF | paired vs 60/1R direct [CI] WF | HOLD paired | 2023 paired | direct WF wk mean / SD / maxDD | HOLD wk | 2023 wk | 2x wk | mapped (conservative) WF wk mean | direct real minus mapped random-in-regime (b) draws, pts/trade (WF) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PBX_PB_ST10_SWZ_T3_f60_SW | 4363 / 1930 | 5098 | +0.22 | -1.00 [-2.19,+0.24] | -1.95 | -0.83 | -1,247 / 60,332 / 804,503 | -847 | +8,456 | -8,514 | +5,760 | -0.53 |
| PBX_PB_ST10_SWZ_T3_f60_T1 | 4363 / 1512 | 5098 | +1.22 | +0.00 [+0.00,+0.00] | +0.00 | +0.00 | +6,867 / 57,235 / 556,368 | +9,821 | +8,119 | +2,370 | +295 | +1.66 |
| PBX_PB_ST10_SWZ_T3_f60_T3 | 4363 / 2147 | 5098 | +2.83 | +1.61 [-0.86,+4.13] | +0.05 | -1.36 | +4,295 / 61,303 / 719,041 | +9,729 | +7,021 | +2,155 | +6,901 | +2.71 |

Reading notes: (1) the direct real mean includes the XJ stop-join credit and measured friction; the mapped placebo draws carry no join credit, so "direct real minus mapped random-in-regime" favours the real cell; it is shown only to size the gap, not as a placebo test (placebo trades were not replayed). (2) Base-cell sanity: compare the control row (direct f60_T1 WF mean pts/trade) with the mapped control; D3XT's own PBS BASE direct rows are the same trades.


## 8. Deviations and disclosures

- Mapped conservative basis throughout; direct basis only for the PBS f60 cells (section 7). No stop-join credit was given; limit entries got no friction credit; sweep surcharge above 14 lots is primary (10f and cap23 variants in the block files).
- Placebos: 16 draws per type; random-entry stops for pullback-extreme cells use a pseudo-extreme from empirical arm-to-signal durations; random draws have more trades than the real list and are scaled for the weekly comparison; ER gate (c) only in block (i) (ER5/ER4 cells of blocks (iii)/(iv) are ER-ungated); ER gate for arms evaluated at the touch bar (not the signal bar).
- Fill model of blocks (iii)/(iii-b): 1-s path trade-through (pb2_lib rule) / touch rule; windows end with the arm. Cross-check against D3LS (pbx_lsim_check.py, PBS arms, 2024-03): fill share 0.57 (mine) vs 0.73-0.75 (lsim touch/strict/queue, same windows); 35% of arms have no order window under my rule (the arm ended on the touch bar). Queue model not calibrated; stop-entry mapped without stop slippage. Limit fill rates are therefore conservative lower bounds.
- Selection effects: bracket cells in block (ii) were chosen on WF-PRE from block (i); cells of blocks (iii)/(iv) on WF-PRE and block (i) verdicts; the top 3 of block (v) by a rule fixed before the numbers were read. Selection used PRE only; holdout looks: one per prereg group (12 + 4 + 1 + 1 + 1 + 1 groups) plus 2 add-one looks (track D3PX_TPBX).
- A correction was logged: block (i) PBX_PB_ST10_SWZ_T3_f60_SW was first labelled PASS by the mechanical V2 rank gate and re-labelled CANDIDATE (the directive requires beating (b)); DECISIONS.md keeps both lines.
- Not run: real-book queue replay of limit fills (D3LS audit still running), footprint triggers at tick-bar resolution, dollar / UniRenko bars (custom BarsType), second-touch scale-in with a queue model, blocks beyond the 14 NT8-native bars, direct-replay latency arms.
- Files: autopilot/DS3_TPBX.md, DS3_TPBX_B2.md, DS3_TPBX_B3.md, DS3_TPBX_B3B.md, DS3_TPBX_B4.md, DS3_TPBX_DIRECT.md (when scored); rows l2vast/ds3/rows/DS3_TPBX*.json; series l2vast/ds3/out/SERIES/DS3_TPBX_*; paper_all l2vast/struct48/paper_all/ds3_TPBX_*.json; preregs l2vast/ds3/prereg/TPBX*; code l2vast/ds3/code/pbx/.
