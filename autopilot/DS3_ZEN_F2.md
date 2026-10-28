# DS3_ZEN_F2 - reaction triggers vs the touch (D3ZF2, 2026-10-28)

**Verdict.** No reaction trigger beats the plain touch: 0 of 4,224 screened cells pass the screen gates together (19 pass G1 only, 0 of them have mean net > 0; best PRE effect vs matched random-in-regime +4.7 pts/trade at n=108 against MDE80 6.8, white reality-check adjusted p 0.94 at N=4,224), the top 30 go to ONE holdout look with **0 of 30 positive-and-significant in HOLD (G6), 0 pass best-of-N (G8), 0 pass G9**; on identical touches every trigger does WORSE than the T0 limit (paired mean -2 to -20 pts), and the unpaired all-touch difference vs T0 is +/-0.7 pts on average, inside its MDE (2-4 pts).

## 1 Counts (descriptive, unscored)
Screen window PRE 2024-02-01..2025-06-30 (75 weeks), PRIMARY 10:00-14:00 entries. Raw touches of the 1-min EMA200 (tol 5) in regime R1 over 2023-02..2025-06 ETH sample: 19,066; trigger fire counts out of those: T1 18,207, T2 4,377, T3 6,377, T4a 5,976, T4b 3,697, T5 14,163, T6 14,549, T7a 1,760, T7b 3,520, T8a 7,152, T8b 11,990, T9a 11,184, T9b 7,618 (before window and bracket filters). T1 fires on 95% of touches (the hold candle is almost always satisfied), so T1 is effectively "market on the touch bar close"; T1+T9a == T9a and T8b+T1 == T8b exactly (duplicate cells, counted once in the top 30). Median PRE trades per cell: T0 about 1,030, T1 1,050, T2 500, T3 380, T4a 370, T4b 250, T5a 800, T5b 600, T6 810, T7a 130, T7b 260, T8a 220, T8b 570, T9a 550, T9b 340; 4,170 of 4,224 cells have n >= 100.

## 2 Grid and screened N
Prereg l2vast/ds3/prereg/ZEN_F2_A_prereg.md sha256 a24a19b587d312b243cbb38999f3f65f4cf6028ff6c12611f606d588c3439809. 12 entry sets (R1/R3/R8 x L1@2, L1@5, L2 EMA40@5, L4 VWAP@5) x 14 triggers x 8 reference brackets x 2 flat = 2,688; two-trigger combos of the top 4 triggers (by paired diff vs T0a: T2, T8b, T1, T9a; 6 pairs, none skipped by the same-family rule) 6 x 12 x 8 x 2 = 1,152; T0a/T0b controls 384. **Screened N = 4,224 (all scored; none skipped)** (plan 3,840 + 384 controls). Program N 291,130. Bracket skips (MODEL/ATR with no swing or stop outside 2-60 pt) are counted per cell in f2_PRE_all_metrics.csv (`skipped`). Holdout: top 30 by PRE matched effect, n >= 100, exact duplicate trade lists once (11 duplicates skipped inside the first 45 ranks). Looks logged: out/zen/f2/looks.jsonl (D3ZF2_HOLD, D3ZF2_X), PREHOLD sha 70f95635f6d4f45e5c1f5be1f22dc3c42a8753cdcb61556dc3437cb93f24c673.

## 3 The central comparison, by trigger (PRE, cells with n >= 100, mean over the 192 cells per trigger variant; combos 96-192)

|trigger|paired vs T0a on identical touches (pts)|unpaired all-touch diff vs T0a (pts)|# cells with its CI lower > 0|effect vs matched random-in-regime|effect vs plain random-in-regime|
|---|---|---|---|---|---|
|T1|-5.06|-0.40|14|-0.41|-0.47|
|T1+T9a|-5.84|0.06|9|0.31|-0.05|
|T2|-4.80|-0.57|8|-0.96|-0.68|
|T2+T1|-5.76|-0.59|2|-0.82|-0.71|
|T2+T8b|-5.31|0.33|19|-0.22|0.23|
|T2+T9a|-7.25|0.67|16|0.27|0.57|
|T3|-8.82|-0.42|6|-0.16|-0.55|
|T4a|-14.65|-0.08|5|-0.79|-0.21|
|T4b|-13.61|0.69|12|0.24|0.59|
|T5a|-9.80|0.13|18|0.05|0.04|
|T5b|-9.21|-0.86|0|-0.13|-0.96|
|T6|-8.61|-0.12|12|-0.11|-0.22|
|T7a|-16.77|-0.33|8|-1.59|-0.38|
|T7b|-13.66|-0.65|1|-0.92|-0.75|
|T8a|-6.57|-0.46|0|0.03|-0.51|
|T8b|-4.92|0.14|17|0.03|0.04|
|T8b+T1|-4.92|0.14|17|0.03|0.04|
|T8b+T9a|-5.80|0.26|20|0.30|0.13|
|T9a|-5.84|0.06|9|0.31|-0.05|
|T9b|-6.28|-0.05|9|-0.08|-0.17|
|T0a (control)| - | - | - |-0.41|-0.08|

Reading: the PAIRED difference is hindsight-conditioned against the trigger: a trigger fires only on touches that later bounced, and T0 (resting limit) is credited with those same touches from its earlier, better fill - so paired values are very negative by construction (this is the cost of waiting, not proof the reaction is useless). The decision-relevant comparison for a trader is the UNPAIRED all-touch difference (trigger trades vs T0 on all touches, same bracket and flat; post-hoc, not in the prereg, labelled as such): mean about 0 (-0.9 to +0.7 pts), its week-block CI lower bound is positive in some cells (202 of 3786) which is what chance gives at ~5% per cell and ~2-4 pts MDE. Under the prereg rule (paired CI lower > 0 and mean >= MDE) no trigger adds anything. Against matched random-in-regime (same reaction pattern at a displaced level) the mean effect is within +-1 pt for every trigger, i.e. the level adds nothing detectable over the reaction pattern, and the reaction pattern adds nothing over the touch.

## 4 Top 10 cells by PRE effect vs matched random-in-regime (regardless of verdict)
Columns: n PRE; net1 pts/trade (10-lot $ = x200); win vs cost-adjusted break-even (BE); matched RIR effect (CI via zen_lib.vs_placebo 2000 week-block draws; MDE80); plain RIR effect; trades/wk; HOLD and X (one look each); forward weeks for 80%% power (PRE weeks x (MDE/effect)^2); failed screen gates; later gates.

|#|cell|n|net1|win/BE|RIR matched eff [CI] (MDE80)|RIR plain|tr/wk|HOLD n, net1, eff [CI lo]|X n, net1, eff|fwd wk|failed gates (screen) / holdout|
|---|---|---|---|---|---|---|---|---|---|---|---|
|1|R8_L1_t2|T2+T9a|F20_30|f840|108|2.89 ($578)|0.676/0.634|4.69 [0.0, 9.4] (6.7)|4.44|1.4|29, 0.91, 2.90 [-4.4]|55, -3.34, -4.17|159|G1(eff 4.69, CI lo -0.18, rank 1.00);G2(eff_dir 1.95, rank 0.87);G5(n 108, eff 4.69 vs MDE 6.82) / G6 fail (HOLD eff 2.9, CI lo -4.4); G7 fail; G8 fail (p 0.94); G9 fail; G10 not run|
|2|R8_L1_t2|T2+T9a|F20_30|f955|108|2.87 ($574)|0.685/0.633|4.57 [-0.2, 9.5] (6.9)|4.37|1.4|29, -0.44, 1.50 [-7.8]|55, -3.14, -3.93|178|G1(eff 4.57, CI lo -0.52, rank 1.00);G2(eff_dir 2.08, rank 0.88);G5(n 108, eff 4.57 vs MDE 7.05) / G6 fail (HOLD eff 1.5, CI lo -7.8); G7 fail; G8 fail (p 0.95); G9 fail; G10 not run|
|3|R1_L1_t2|T9a|R40_40|f955|388|1.67 ($334)|0.534/0.518|4.04 [0.0, 7.7] (5.6)|2.52|5.2|135, -3.85, -2.67 [-8.8]|201, -0.84, 1.89|141|G3(net1 1.67, net2 -0.33);G5(n 388, eff 4.04 vs MDE 5.53) / G6 fail (HOLD eff -2.7, CI lo -8.8); G8 fail (p 0.98); G9 fail; G10 not run|
|4|R1_L1_t2|T1+T9a|R40_40|f840|388|1.36 ($272)|0.526/0.519|3.97 [-0.2, 7.7] (5.7)|2.26|5.2|135, -4.15, -2.86 [-8.9]|201, 1.48, 3.62|148|G2(eff_dir 2.94, rank 0.93);G3(net1 1.36, net2 -0.62);G5(n 388, eff 3.97 vs MDE 5.58) / G6 fail (HOLD eff -2.9, CI lo -8.9); G8 fail (p 0.99); G9 fail; G10 not run|
|5|R1_L1_t5|T8a|R40_40|f955|244|0.55 ($111)|0.520/0.519|3.94 [-0.3, 8.1] (5.8)|1.56|3.3|83, -0.31, -0.69 [-9.2]|135, 1.35, 5.25|180|G1(eff 3.94, CI lo -0.29, rank 0.99);G2(eff_dir 2.71, rank 0.85);G3(net1 0.55, net2 -1.49);G5(n 244, eff 3.94 vs MDE 6.10) / G6 fail (HOLD eff -0.7, CI lo -9.2); G8 fail (p 0.99); G9 fail; G10 not run|
|6|R8_L1_t2|T2+T9a|F20_60|f840|108|1.80 ($359)|0.722/0.775|3.92 [-1.3, 8.8] (7.3)|3.14|1.4|28, -0.78, 3.38 [-6.6]|55, -3.20, -5.04|266|G1(eff 3.92, CI lo -1.43, rank 0.96);G2(eff_dir 1.31, rank 0.76);G3(net1 1.80, net2 -0.67);G4(win 0.722 vs BE 0.775);G5(n 108, eff 3.92 vs MDE 7.39) / G6 fail (HOLD eff 3.4, CI lo -6.6); G7 fail; G8 fail (p 0.99); G9 fail; G10 not run|
|7|R3_L1_t2|T9a|R40_40|f840|338|1.22 ($244)|0.524/0.519|3.79 [-0.3, 7.5] (5.6)|1.98|4.5|116, -3.99, -3.73 [-9.3]|184, 1.55, 3.66|163|G2(eff_dir 2.80, rank 0.94);G3(net1 1.22, net2 -0.76);G5(n 338, eff 3.79 vs MDE 5.59) / G6 fail (HOLD eff -3.7, CI lo -9.3); G8 fail (p 0.99); G9 fail; G10 not run|
|8|R1_L1_t5|T8a|R40_40|f840|244|0.66 ($133)|0.516/0.520|3.78 [-0.4, 7.6] (5.8)|1.61|3.3|83, -0.37, -0.63 [-7.6]|135, 1.63, 3.64|188|G1(eff 3.78, CI lo -0.40, rank 0.99);G2(eff_dir 2.50, rank 0.85);G3(net1 0.66, net2 -1.36);G4(win 0.516 vs BE 0.520);G5(n 244, eff 3.78 vs MDE 6.00) / G6 fail (HOLD eff -0.6, CI lo -7.6); G8 fail (p 0.99); G9 fail; G10 not run|
|9|R1_L4_t5|T9b|F20_60|f955|342|1.51 ($302)|0.775/0.777|3.74 [-0.0, 7.1] (5.2)|3.33|4.6|103, -3.63, -1.36 [-8.3]|192, -1.39, -0.20|145|G1(eff 3.74, CI lo -0.08, rank 0.99);G2(eff_dir 1.53, rank 0.90);G3(net1 1.51, net2 -1.16);G4(win 0.775 vs BE 0.777);G5(n 342, eff 3.74 vs MDE 5.20) / G6 fail (HOLD eff -1.4, CI lo -8.3); G7 fail; G8 fail (p 0.99); G9 fail; G10 not run|
|10|R8_L1_t2|T2+T9a|F20_40|f840|108|2.12 ($425)|0.704/0.697|3.69 [-1.4, 8.4] (7.1)|3.47|1.4|29, 0.28, 2.50 [-6.1]|55, -2.61, -3.85|289|G1(eff 3.69, CI lo -1.43, rank 0.97);G2(eff_dir 1.80, rank 0.84);G3(net1 2.12, net2 -0.28);G5(n 108, eff 3.69 vs MDE 7.25) / G6 fail (HOLD eff 2.5, CI lo -6.1); G7 fail; G8 fail (p 0.99); G9 fail; G10 not run|

Every top-10 cell is inside its MDE (effect < MDE80) and the HOLD effects are scattered around zero (30-cell HOLD mean effect -0.22 pts; mean HOLD net1 -1.44).

## 5 Top 30 through the holdout stage
|#|cell|PRE n/net1/eff|HOLD n/net1/eff/CI lo/MDE|X n/net1/eff|paired vs T0a PRE/HOLD|unpaired vs T0a PRE/HOLD|year eff 2024/25/26|G6|G7|G8 p|G9|
|---|---|---|---|---|---|---|---|---|---|---|---|
|1|R8_L1_t2|T2+T9a|F20_30|f840|108/2.89/4.69|29/0.91/2.90/-4.4/10.4|55/-3.34/-4.17|-4.2/-6.9|4.46/3.13|4.8/4.7/-7.1|N|N|0.94|N|
|2|R8_L1_t2|T2+T9a|F20_30|f955|108/2.87/4.57|29/-0.44/1.50/-7.8/12.7|55/-3.14/-3.93|-5.1/-9.2|4.51/1.45|4.3/5.2/-14.7|N|N|0.95|N|
|3|R1_L1_t2|T9a|R40_40|f955|388/1.67/4.04|135/-3.85/-2.67/-8.8/8.7|201/-0.84/1.89|-6.3/-5.8|3.04/-3.51|4.2/1.2/-11.2|N|Y|0.98|N|
|4|R1_L1_t2|T1+T9a|R40_40|f840|388/1.36/3.97|135/-4.15/-2.86/-8.9/8.6|201/1.48/3.62|-5.7/-5.3|2.37/-3.97|4.6/0.7/-11.4|N|Y|0.99|N|
|5|R1_L1_t5|T8a|R40_40|f955|244/0.55/3.94|83/-0.31/-0.69/-9.2/12.1|135/1.35/5.25|-7.3/-4.4|1.83/0.10|4.2/1.7/0.1|N|Y|0.99|N|
|6|R8_L1_t2|T2+T9a|F20_60|f840|108/1.80/3.92|28/-0.78/3.38/-6.6/13.6|55/-3.20/-5.04|-6.7/-10.3|3.72/2.85|5.8/2.3/-13.6|N|N|0.99|N|
|7|R3_L1_t2|T9a|R40_40|f840|338/1.22/3.79|116/-3.99/-3.73/-9.3/7.9|184/1.55/3.66|-6.3/-5.6|2.08/-3.59|3.9/0.7/-11.4|N|Y|0.99|N|
|8|R1_L1_t5|T8a|R40_40|f840|244/0.66/3.78|83/-0.37/-0.63/-7.6/10.6|135/1.63/3.64|-7.6/-4.9|1.63/0.47|4.6/1.0/-0.2|N|Y|0.99|N|
|9|R1_L4_t5|T9b|F20_60|f955|342/1.51/3.74|103/-3.63/-1.36/-8.3/9.7|192/-1.39/-0.20|-5.7/-6.1|1.76/-1.18|3.1/2.8/-11.2|N|N|0.99|N|
|10|R8_L1_t2|T2+T9a|F20_40|f840|108/2.12/3.69|29/0.28/2.50/-6.1/11.7|55/-2.61/-3.85|-4.1/-6.7|3.63/2.78|4.4/3.7/-13.6|N|N|0.99|N|
|11|R1_L4_t5|T9b|F30_60|f955|305/0.52/3.52|102/0.36/1.62/-6.1/11.1|170/-0.69/1.08|-7.2/-2.8|-0.35/2.22|1.6/5.4/-9.0|N|Y|1.00|N|
|12|R8_L1_t2|T1+T9a|R40_40|f955|188/1.08/3.51|71/-3.42/-3.35/-11.3/11.7|119/0.15/2.30|-7.2/-6.3|1.75/-4.46|3.9/0.4/-14.5|N|Y|1.00|N|
|13|R8_L1_t2|T2+T9a|F20_40|f955|108/2.05/3.51|29/-1.97/0.08/-11.8/16.4|55/-4.30/-5.27|-5.3/-7.5|3.86/-0.10|4.0/2.8/-14.9|N|N|1.00|N|
|14|R8_L1_t2|T9a|R40_40|f840|188/0.92/3.42|71/-3.18/-3.12/-10.1/10.2|119/2.03/3.81|-5.6/-5.1|1.34/-4.07|4.1/0.4/-15.7|N|Y|1.00|N|
|15|R3_L1_t5|T8a|R40_40|f840|236/-0.04/3.35|82/-0.81/-1.62/-8.8/10.8|130/0.87/3.53|-8.2/-4.9|0.53/-0.56|4.3/0.1/0.0|N|Y|1.00|N|
|16|R3_L4_t5|T3|F30_60|f840|308/1.20/3.35|110/-5.26/-3.57/-9.2/7.9|161/-3.75/-2.79|-10.9/-8.4|0.68/-2.35|2.8/1.0/-8.0|N|N|1.00|N|
|17|R3_L1_t2|T1+T9a|R40_40|f955|338/1.00/3.33|116/-3.76/-3.53/-9.6/8.6|184/-0.44/2.21|-7.1/-6.4|2.00/-3.58|2.9/1.1/-10.0|N|Y|1.00|N|
|18|R3_L1_t5|T8a|R40_40|f955|236/-0.36/3.32|82/-0.75/-1.72/-10.3/12.3|130/0.31/5.03|-7.9/-4.4|0.35/-1.00|3.6/0.7/0.3|N|Y|1.00|N|
|19|R8_L1_t2|T2+T9a|F30_60|f840|105/0.38/3.24|27/3.69/6.89/-4.4/15.9|55/-0.73/-1.52|-10.4/-4.9|1.17/4.72|6.3/2.0/-13.4|N|N|1.00|N|
|20|R8_L4_t5|T2+T8b|F30_60|f840|257/1.61/3.19|83/1.50/1.12/-6.7/11.0|110/-4.41/-3.11|-11.8/-7.5|1.09/4.40|-0.1/4.7/15.2|N|N|1.00|N|
|21|R8_L1_t2|T1+T9a|F30_60|f840|195/1.48/3.10|72/-4.14/-3.87/-11.4/11.0|123/2.19/4.49|-5.4/-4.8|2.27/-3.11|4.0/-0.1/-19.3|N|Y|1.00|N|
|22|R1_L2_t5|T7a|F30_60|f955|199/1.71/3.08|85/0.01/4.99/-11.1/21.9|93/-4.98/-16.90|-20.1/-18.1|2.59/0.11|4.6/2.2/4.4|N|N|1.00|N|
|23|R3_L4_t5|T9b|F20_60|f955|324/1.09/3.08|92/-2.32/-0.66/-7.8/10.0|182/-0.74/0.68|-5.5/-5.1|1.60/0.40|1.5/3.9/-13.6|N|Y|1.00|N|
|24|R1_L4_t5|T9b|F20_60|f840|342/1.07/3.02|103/-3.76/-0.90/-6.5/7.8|192/-2.41/-1.15|-6.2/-6.6|1.38/-0.76|2.7/2.0/-6.3|N|N|1.00|N|
|25|R8_L1_t2|T8b+T9a|F20_30|f840|118/0.74/2.93|49/-5.14/-3.85/-9.8/8.3|72/-3.45/-3.43|-2.7/-3.8|2.30/-2.92|1.4/2.5/-17.9|N|N|1.00|N|
|26|R1_L1_t2|T8a|R40_40|f955|205/0.66/2.91|69/-1.30/0.09/-9.6/14.1|108/-4.26/-0.53|-5.5/-5.3|2.03/-0.97|1.1/3.6/-3.4|N|N|1.00|N|
|27|R1_L1_t2|T8a|R40_40|f840|205/0.52/2.85|69/-1.24/-0.54/-9.1/12.2|108/-2.78/-0.51|-6.0/-5.6|1.52/-1.06|2.0/2.2/-2.1|N|N|1.00|N|
|28|R1_L4_t5|T9b|R40_40|f840|300/0.62/2.77|96/3.48/5.04/-1.2/9.2|174/-1.71/-0.75|-8.2/-1.9|1.22/5.62|1.7/5.6/-2.3|N|N|1.00|N|
|29|R3_L4_t5|T2+T8b|F20_60|f840|289/0.92/2.76|91/1.39/1.82/-4.1/8.3|130/-2.77/-1.38|-8.1/-4.4|1.42/4.96|0.2/4.4/10.0|N|N|1.00|N|
|30|R8_L4_t5|T8a|R40_40|f955|187/0.38/2.75|60/-0.26/0.22/-8.8/13.2|103/2.67/1.34|-9.8/-11.8|0.97/0.98|5.2/-0.3/1.7|N|Y|1.00|N|

Gate counts over the 30: G6 0, G7 14, G8 0, G9 0, G10 not run. Nothing is a CANDIDATE; no LEAD (no cell clears G6).

## 6 By window (top 30, PRE, placebo inside each window; descriptive, the screen was PRIMARY only)
|window|median n|mean net1|mean effect vs matched RIR|
|---|---|---|---|
|09:30-10:00|72|-10.75|-8.58|
|10-11|49|-1.33|-0.43|
|11-12|59|2.61|5.01|
|12-13|68|0.25|1.24|
|13-14|72|0.72|5.38|
|14:00-15:30|84|1.31|4.11|
|RTH-pooled|367|0.55|2.73|

09:30-10:00 is strongly negative (open volatility), later windows are mildly positive in effect only because the placebo is worse; a best-window claim would add 8 x 30 = 240 to N and none is made. Per-cell rows: out/zen/f2/f2_top30_bywindow.csv.

## 7 By year, half-year, long/short (top 10; WF = PRE+HOLD)
By year the matched effect is positive in 2024 and 2025 for most cells and strongly negative in 2026 (Jan-Feb 6, small n) - see year columns in section 5. Half-year and side tables per cell are in out/zen/f2/f2_top30_extra.json. Top 10 summary:

- R8_L1_t2|T2+T9a|F20_30|f840: half-year [2024H1 n40 0.3, 2024H2 n38 6.8, 2025H1 n30 1.4, 2025H2 n23 3.0, 2026H1 n6 -7.2]; side [long n87 2.2, short n50 3.0]
- R8_L1_t2|T2+T9a|F20_30|f955: half-year [2024H1 n40 0.6, 2024H2 n38 6.7, 2025H1 n30 1.0, 2025H2 n23 3.4, 2026H1 n6 -15.0]; side [long n87 1.8, short n50 2.9]
- R1_L1_t2|T9a|R40_40|f955: half-year [2024H1 n124 0.5, 2024H2 n139 6.3, 2025H1 n125 -2.3, 2025H2 n111 -2.8, 2026H1 n24 -8.7]; side [long n278 -2.4, short n245 3.2]
- R1_L1_t2|T1+T9a|R40_40|f840: half-year [2024H1 n124 -1.1, 2024H2 n139 6.8, 2025H1 n125 -2.3, 2025H2 n111 -3.4, 2026H1 n24 -7.6]; side [long n278 -1.5, short n245 1.5]
- R1_L1_t5|T8a|R40_40|f955: half-year [2024H1 n74 0.6, 2024H2 n81 2.6, 2025H1 n89 -1.4, 2025H2 n73 -0.0, 2026H1 n10 -2.4]; side [long n212 -1.9, short n115 4.4]
- R8_L1_t2|T2+T9a|F20_60|f840: half-year [2024H1 n40 0.2, 2024H2 n38 8.2, 2025H1 n30 -4.1, 2025H2 n23 1.7, 2026H1 n5 -12.0]; side [long n86 0.9, short n50 1.9]
- R3_L1_t2|T9a|R40_40|f840: half-year [2024H1 n109 -0.5, 2024H2 n122 5.0, 2025H1 n107 -1.3, 2025H2 n93 -3.2, 2026H1 n23 -7.1]; side [long n237 -2.1, short n217 2.0]
- R1_L1_t5|T8a|R40_40|f840: half-year [2024H1 n74 1.6, 2024H2 n81 2.0, 2025H1 n89 -1.3, 2025H2 n73 -0.4, 2026H1 n10 -0.5]; side [long n212 -0.4, short n115 1.9]
- R1_L4_t5|T9b|F20_60|f955: half-year [2024H1 n118 2.1, 2024H2 n110 1.9, 2025H1 n114 0.6, 2025H2 n93 -3.2, 2026H1 n10 -7.3]; side [long n232 0.1, short n213 0.6]
- R8_L1_t2|T2+T9a|F20_40|f840: half-year [2024H1 n40 -0.9, 2024H2 n38 6.5, 2025H1 n30 0.6, 2025H2 n23 3.1, 2026H1 n6 -10.5]; side [long n87 1.0, short n50 3.0]

## 8 MDE, best-of-N, random-in-regime
Per-cell MDE80 in PRE: median 3.2 pts (n about 300); prior formula 2.8*45*sqrt(1.3/n) gives 5-8 at n 100-400. Largest PRE effect +4.7 never exceeds its MDE (G5 passes in 0 cells). Reality check (week-block bootstrap of the matched effect over all 4,224 cells with n >= 30, unstudentized): smallest adjusted p 0.936. Random-in-regime column: matched and plain on every row (f2_PRE_all_metrics.csv). Random direction (G2) passes 100+ cells but those are mostly T0 / T7a cells whose edge is a negative-expectation market.

## 9 Deviations and disclosures
- Matched placebo = same detector on pseudo-touches of a line displaced 10/20/40 pt to the trend side (my reading of "same trigger requirement at the random minute"); it contains some deep-pullback pseudo-touches near the real level. Take-rate clipped at 1 in some T7a/T8a/T4 cells (clip flag in the CSV).
- Paired-vs-T0 is hindsight-conditioned (section 3). The unpaired all-touch difference vs T0a and its CI were added post hoc, labelled; they do not enter N or the gates.
- Top-4 rule produced T2, T8b, T1, T9a; T1 fires on 95% of touches so T1+X combos duplicate X (T1+T9a == T9a, T8b+T1 == T8b); duplicates counted in N, once in the top 30.
- T2 uses a close-break, not a stop-entry. Random-direction placebo for limit cells uses market entry at the fill bar.
- First run of f2_hold.py crashed in the library comparison (variable name clash: cell key `win` overwritten by the win rate) after the HOLD/X cell runs and before any table was written; fixed (window passed explicitly) and rerun with the same code and cells; one look per window, looks.jsonl written once.
- Library caution from D3ZF1 (zen_struct grid_eval fill_mode=1): F2 does NOT use grid_eval; every cell, including limit-entry cells (T0, T5b), runs through Z.simulate(fill_mode=1), so the bug does not apply.
- G10 (direct 1-s/L2 replay) NOT run; PRE re-run on the full context reproduces the PRE-only screen exactly (identity test passed). Screen is on the mapped conservative basis. Data cut ld <= 20260206; UNTOUCHED never read. HOLD/X read once for 30 cells, after the logged PREHOLD hash.
- Entries and exits only at 1-min bars; costs net1 (1x), net2 (2x): only the two n=108 R8_L1_t2 T2+T9a 20/30 cells keep net2 > 0 in PRE (+0.57, +0.56 pts) and both are negative-or-flat in HOLD (+0.91 / -0.44 net1) and negative in X (-3.3 / -3.1).

## 10 Files
autopilot/DS3_ZEN_F2_PREHOLD.md; l2vast/ds3/prereg/ZEN_F2_A_prereg.md(.sha256); code l2vast/ds3/code/zen/f2/{zen_f2,f2_metrics,f2_stageA,f2_stageB,f2_screen,f2_hold,f2_test}.py; PRE tables l2vast/ds3/out/zen/f2/{f2_PRE_all_metrics.csv,f2_PRE_stage1_metrics.csv,f2_top30_PRE.csv,f2_top30_full.csv,f2_top30_bywindow.csv,f2_top30_extra.json,f2_grid_stage1.csv,looks.jsonl,f2_test.log}.

**Do reaction triggers add anything over a touch? No: no trigger (T1-T9 or any pair) beats the touch (T0) by more than its MDE on identical touches, none beats random-in-regime with the same trigger requirement, and none survives the holdout.**

DONE F2
