# DS3_L2_UF_LOSS_C9 - L2-UNTIL-FOUND cycle 9, LOSS side: the ES-leads-NQ state on OPEN underwater trades as a cut / tighten trigger, with execution delay (agent UF-LOSS, 2026-10-31)
Research only. UNTOUCHED never read (ES tables opened only through 2026-01; ES exists to 2026-01-31, so Y26 = January, sign only; X' here = 2023-08-01..2024-01-31). Own masks: L6M = 20250801.., HOLD = 20250701.., PRE = 20240201..20250630. Prereg `l2vast/ds3/prereg/UF_LOSS_C9_prereg.md` sha256 1105a81659ece88c9455356709a6848ac38f56fb89dbfded08c178cbae7e87fe; selection `out/uf/loss9/selection_PRE_X.json` sha256 600af34f59e4cc8d977bb6d961c581422a0ca670e39da77c3585093c824816e5 (PRE+X' only, basis N per contract, logged before the single recent look). 432 cells; dead_lookup (1 in 8): 0 hits; cumulative N = UF_TRIALS total + 432; n_effective 2.3.
Primary number: N pts per trade per contract (hold-to-bracket base), `mean (MDE) [n fired]`, M and LIVE-CAL beside with the stop-cost credit; selectivity fire < 50% of arm-reaching trades; stack $/wk secondary (live lots K6 2 P6 7 U6 4 H6 4/2).
## Page 1 - the answer
1. **A null.** Pooled selected cell `lag w=30 s th=2 bp A=30 cut delay 0`: N per contract 2026 -0.52, L6M -0.43 (MDE 0.66), HOLD -0.30 (0.61), PRE +0.25 (0.56), X' +0.34 (1.19); fire 20% L6M (38% PRE). Positive in the selection windows, negative in the last 12 months; random cuts at the same rate rank 0.05 / 0.15 (L6M / HOLD), ES shuffled across trades of the day 0.25 / 0.25; ES computed 60 s earlier gives L6M -1.08. Stack (lock engine, research lots) L6M -4,825 (MDE 17,883), HOLD -2,559.
2. **What the ES term adds:** nothing but selectivity. At the same (w, th, A, action, delay) the NQ-own-move trigger (path control) fires on 87% of arm-reaching trades and loses -1.53 per contract in L6M; the ES-alone trigger fires on 81% and loses -0.97; the lag trigger (ES moved against the trade more than NQ) fires on 20% and loses -0.43. Fewer cuts lose less; the lag trigger does not turn positive. Grid medians in section 2.
3. **Delay is not the problem here:** delay 2 s changes the selected cell by 0.02-0.03 pt (L6M -0.45); the failure is regime, not stale feed.
4. Per book (section 1): every cell is negative in L6M/HOLD or inside MDE with few fired trades; KB (24 fired) +0.04 L6M is the only non-negative recent cell, rank random 0.70 / shuffled 0.40; WT (28 fired) -0.02. RC / Romano-Wolf over the 432 on PRE+X' days: p 0.57 (studentised 0.62), 0 survivors. **Tier: BEST-AVAILABLE-NEGATIVE; the loss-side ES-leads-NQ exit is DEAD; the only ES relation on the loss side remains the cycle-7 stopped-book ES imbalance (LEAD, structure-dominated).**
## 1. Selected cells (recent first; per contract N; controls beside)
| group | cell (selected on PRE+X') | fire % L6M | 2026 N/ct | L6M N/ct (MDE) [n fired] | HOLD | PRE | X' | L6M M / LC (credit) | NQ-own control L6M / fire | ES-only control L6M / fire | delay flipped L6M | rank random cuts / shuffled ES (L6M, HOLD) | time-shift 60 s L6M | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | type=lag|w=30|th=2|A=30|delay=0|act=cut | 20 | -0.52 | -0.43 (0.66) [1177] | -0.30 | +0.25 | +0.34 | -0.33 / -0.30 (+0.13) | -1.53 / 87% | -0.97 / 81% | -0.45 | 0.05/0.15, 0.25/0.25 | -1.08 | BEST-AVAILABLE-NEGATIVE |
| ST | type=lag|w=15|th=4|A=20|delay=0|act=t10 | 2 | -0.37 | -0.16 (0.35) [20] | -0.14 | +0.16 | +0.21 | -0.15 / -0.16 (-0.00) | +0.19 / 53% | +0.22 / 33% | -0.16 | 0.15/0.20, 0.50/0.50 | +0.06 | BEST-AVAILABLE-NEGATIVE |
| HM | type=lag|w=60|th=4|A=30|delay=0|act=cut | 4 | -0.19 | -0.50 (0.87) [23] | -0.54 | +0.13 | +0.36 | -0.46 / -0.47 (+0.02) | -1.23 / 82% | -1.24 / 66% | -0.52 | 0.10/0.05, 0.10/0.00 | -0.71 | BEST-AVAILABLE-NEGATIVE |
| WT (non-D6, separate) | type=lag|w=30|th=2|A=30|delay=0|act=cut | 3 | +0.07 | -0.02 (0.24) [28] | -0.00 | +0.17 | +0.40 | -0.01 / +0.00 (+0.02) | -1.12 / 82% | -0.73 / 70% | -0.02 | 0.45/0.40, 0.90/0.85 | -0.58 | BEST-AVAILABLE-NEGATIVE |
| KB | type=lag|w=60|th=4|A=30|delay=2|act=cut | 3 | +0.26 | +0.04 (0.48) [24] | +0.14 | +0.28 | +0.15 | +0.05 / +0.06 (+0.02) | -0.17 / 78% | -0.15 / 66% | +0.04 | 0.70/0.80, 0.40/0.50 | -0.73 | CANDIDATE-RECENT-weak (N>=0, inside MDE, placebo<0.9) |
| SM | type=es|w=15|th=4|A=30|delay=2|act=t10 | 23 | -0.99 | -0.50 (1.69) [44] | -0.72 | +0.35 | +0.58 | -0.46 / -0.47 (+0.03) | -0.92 / 48% | -0.50 / 23% | -0.41 | 0.65/0.70, 0.05/0.05 | -1.20 | BEST-AVAILABLE-NEGATIVE |
| PE | type=lag|w=15|th=4|A=30|delay=0|act=t10 | 2 | +0.00 | -0.01 (0.07) [14] | -0.01 | +0.06 | +0.05 | -0.01 / -0.01 (+0.00) | -0.80 / 48% | -0.28 / 28% | +0.01 | 0.80/0.80, 0.60/0.55 | -0.36 | BEST-AVAILABLE-NEGATIVE |
| PB | type=lag|w=15|th=2|A=30|delay=0|act=t10 | 18 | +0.18 | -0.21 (0.63) [95] | -0.17 | +0.18 | +0.26 | -0.19 / -0.18 (+0.02) | -1.00 / 85% | -0.68 / 74% | -0.21 | 0.75/0.60, 0.40/0.25 | -0.82 | BEST-AVAILABLE-NEGATIVE |
| DN | type=lag|w=60|th=4|A=20|delay=2|act=cut | 8 | -4.58 | -2.51 (1.89) [40] | -1.97 | +0.41 | +0.00 | -2.35 / -2.48 (+0.03) | -2.50 / 80% | -2.13 / 68% | -2.50 | 0.00/0.00, 0.00/0.00 | -2.67 | BEST-AVAILABLE-NEGATIVE |
| MV | type=es|w=15|th=4|A=30|delay=2|act=cut | 27 | -2.76 | -0.83 (1.66) [194] | -0.99 | +0.18 | +0.62 | -0.69 / -0.65 (+0.19) | -1.51 / 46% | -0.83 / 27% | -0.91 | 0.15/0.00, 0.00/0.00 | -1.11 | BEST-AVAILABLE-NEGATIVE |
| MA | type=es|w=15|th=4|A=30|delay=0|act=t10 | 21 | -0.95 | -1.27 (1.97) [50] | -1.51 | +0.19 | +0.43 | -1.20 / -1.24 (+0.03) | -2.86 / 49% | -1.27 / 21% | -0.51 | 0.75/0.60, 0.00/0.00 | -0.44 | BEST-AVAILABLE-NEGATIVE |
## 2. Grid (PRE and X' only, ALL pooled; medians over cells of a (type, w, th) row incl. both arms, 4 actions, 2 delays)
| type   |   w |   th |   cells |   fire_med |   selective |   PRE_N_med |   X_N_med |   PRE_N_max |
|:-------|----:|-----:|--------:|-----------:|------------:|------------:|----------:|------------:|
| es     |  15 |    1 |      16 |      0.941 |           0 |      -0.572 |     0.259 |       0.055 |
| es     |  15 |    2 |      16 |      0.843 |           0 |      -0.172 |     0.103 |       0.132 |
| es     |  15 |    4 |      16 |      0.455 |          16 |      -0.001 |    -0.083 |       0.12  |
| es     |  30 |    1 |      16 |      0.951 |           0 |      -0.609 |     0.228 |       0.029 |
| es     |  30 |    2 |      16 |      0.911 |           0 |      -0.388 |     0.241 |       0.046 |
| es     |  30 |    4 |      16 |      0.647 |           0 |      -0.04  |     0.18  |       0.143 |
| es     |  60 |    1 |      16 |      0.948 |           0 |      -0.617 |     0.256 |       0.025 |
| es     |  60 |    2 |      16 |      0.931 |           0 |      -0.543 |     0.237 |       0.046 |
| es     |  60 |    4 |      16 |      0.781 |           0 |      -0.211 |     0.061 |       0.071 |
| lag    |  15 |    1 |      16 |      0.786 |           0 |      -0.096 |     0.166 |       0.12  |
| lag    |  15 |    2 |      16 |      0.373 |          16 |      -0.065 |    -0.137 |       0.116 |
| lag    |  15 |    4 |      16 |      0.055 |          16 |       0.007 |     0.004 |       0.067 |
| lag    |  30 |    1 |      16 |      0.786 |           0 |      -0.174 |     0.139 |       0.03  |
| lag    |  30 |    2 |      16 |      0.437 |          16 |      -0.01  |     0.06  |       0.248 |
| lag    |  30 |    4 |      16 |      0.075 |          16 |       0.011 |    -0.007 |       0.087 |
| lag    |  60 |    1 |      16 |      0.763 |           0 |      -0.268 |     0.175 |      -0.038 |
| lag    |  60 |    2 |      16 |      0.487 |           8 |       0.009 |     0.05  |       0.117 |
| lag    |  60 |    4 |      16 |      0.103 |          16 |       0.001 |    -0.018 |       0.107 |
| nq     |  15 |    1 |      16 |      0.956 |           0 |      -0.649 |     0.275 |       0.054 |
| nq     |  15 |    2 |      16 |      0.917 |           0 |      -0.389 |     0.247 |      -0.011 |
| nq     |  15 |    4 |      16 |      0.637 |           0 |       0.011 |     0.006 |       0.138 |
| nq     |  30 |    1 |      16 |      0.959 |           0 |      -0.64  |     0.241 |       0.038 |
| nq     |  30 |    2 |      16 |      0.944 |           0 |      -0.565 |     0.258 |       0.042 |
| nq     |  30 |    4 |      16 |      0.799 |           0 |      -0.168 |     0.316 |       0.106 |
| nq     |  60 |    1 |      16 |      0.953 |           0 |      -0.632 |     0.251 |       0.057 |
| nq     |  60 |    2 |      16 |      0.948 |           0 |      -0.631 |     0.195 |       0.034 |
| nq     |  60 |    4 |      16 |      0.883 |           0 |      -0.327 |     0.144 |       0.028 |
By delay (median PRE / X' N per contract):
| type   |   dl |   PRE_N_med |   X_N_med |
|:-------|-----:|------------:|----------:|
| es     |    0 |      -0.287 |     0.206 |
| es     |    2 |      -0.246 |     0.174 |
| lag    |    0 |      -0.01  |     0.026 |
| lag    |    2 |      -0.018 |     0.035 |
| nq     |    0 |      -0.492 |     0.237 |
| nq     |    2 |      -0.449 |     0.219 |
## 3. Stack (exact 6-book lock engine, secondary) and sessions
| stream | 2026 d$/wk (MDE) | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| ALL_sel | -9,796 (24,317) | -4,825 (17,883) | -2,559 (16,053) | -638 (14,444) | -4,043 (12,400) |
| KB_sel | +319 (894) | -307 (1,852) | -40 (1,694) | -570 (1,758) | +12 (3,255) |
| WT_sel | +394 (1,103) | -206 (1,060) | -585 (1,107) | +15 (1,851) | +977 (3,384) |
| COMBO_perbook6 | -4,327 (10,129) | -3,527 (5,369) | -3,768 (5,123) | -384 (4,311) | -781 (6,374) |
Sessions (ENTRY, pooled cell, N per contract, MDE, n fired) L6M: asia +0.27 (0.89, 193), london -1.03 (1.70, 239), pre +1.70 (2.94, 102), nyam -0.85 (1.43, 449), nypm -0.71 (1.34, 191). HM-only: the registered a30_w10 base (static L6(30,10) FULL, unaltered) is N per contract L6M -0.00, HOLD +0.06, PRE +0.20; the HM ES cell (`type=lag|w=60|th=4|A=30|delay=0|act=cut`) is L6M -0.50 (0.87, 23 fired).
## 4. Learned
1. The ES lead does not rescue an open loser: ES moving against the trade by more than NQ in the last 15-60 s is followed by NQ catching down only in the selection windows; in the last 12 months cutting on it loses as much as any other cut.
2. Together with ESLEAD (entry), cycle 7 (stopped-book ES at the first stop) and INFO's map, ES carries no information beyond NQ's own move that survives selection on the loss side.
3. Closing line: the LOSS side of the standing order has no rule >= 0 per contract in the last 6 months and HOLD with placebos beaten after 9 cycles; best-available per cycle is in DS3_L2_UNTIL_FOUND.md; the only structure with a recent sign is the stack-level first-stop cut (re-entry-dominated, SHADOW).
Files: code/uf9/{cells9,engine9,stageB9,stack9}.py; out/uf/loss9/{D9.npz,stageA9.pkl,cells9_PRE_X.csv,selection_PRE_X.json,stageB9.pkl,stack9.json}; DEAD_CELLS.csv +432 (UFL9).
