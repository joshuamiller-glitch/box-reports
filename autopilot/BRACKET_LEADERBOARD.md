# BRACKET LEADERBOARD (T-BRACKET-PM, D3BL)
Updated 2026-10-26T20:39Z. Rows files: DS3_TBRACKET_G1.json, DS3_TBRACKET_G2.json, DS3_TBRACKET_G3.json, DS3_TPYRAMID.json

Brackets: 0 PASS, 0 CANDIDATE. Best shape: none. Near-target: not scored, diagnostic ratio n/a. Scale-out: not scored. Pyramiding risk-constant: 215 cells scored, 0 PASS/CANDIDATE (all DEAD). Combined best on n/a: +$n/a/wk, maxDD delta n/a, CI [n/a]. Trade Health: 5088 cells scored, 0 PASS/CANDIDATE (cut EV: see rows).

Scope: tier 1 only (ST, HM, KB, SM, EM); other registry entries paused; sections B and C paused.
## Multiplicity
Cells scored across A-D, E, G: 5303 (per section {'G': 5088, 'D': 215}). Verdicts: {'DEAD': 5303}.
Cells with paired CI lower bound >0: 2; expected by chance at one-sided 2.5% over 5303 cells: 132.6. If observed is near this the best cell is best-of-N noise.
Best-of-N null: each section's best cell is judged against the max of N paired deltas drawn at zero effect (use the per-owner placebo ranks in the rows; a cell with placebo rank <0.95 is not credited).

## PASS / CANDIDATE
| entry | sec | cell | paired pts/trade [CI] | MDE | win req / obs | trades | lots avg / peak | WF mean / SD / maxDD | holdout | placebo | $/wk equal lots | $/wk equal risk | lots equal risk | capacity lots | DS3 marg. Sharpe | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|

## RE-VERDICT list (DEAD only because earnings below ST at equal lots; rescore at equal risk / DS3 marginal Sharpe)
(none)

Equal-risk columns come from l2vast/ds3/code/equal_risk.py (ST10 WF weekly SD reference; sweep cost on extra lots).

## Top 20 per entry family and section (by paired delta)
### EM / D (43 cells)
| entry | sec | cell | paired pts/trade [CI] | MDE | win req / obs | trades | lots avg / peak | WF mean / SD / maxDD | holdout | placebo | $/wk equal lots | $/wk equal risk | lots equal risk | capacity lots | DS3 marg. Sharpe | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| EM | D | PY_EM_D1_N30_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 4,926 | 7,562 | 14.7 | 54 |  | DEAD |
| EM | D | PY_EM_D1_N15_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 3,529 | 4,676 | 13.0 | 35 |  | DEAD |
| EM | D | PY_EM_D1_N45_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 6,614 | 10,751 | 16.2 | 79 |  | DEAD |
| EM | D | PY_EM_D1_PB_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 3,020 | 4,528 | 13.5 | 34 |  | DEAD |
| EM | D | PY_EM_D1_SG_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 7,194 | 12,136 | 16.7 | 111 |  | DEAD |
| EM | D | PY_EM_D1_N30_f100_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | -2,373 | -3,136 | 13.1 |  |  | DEAD |
| EM | D | PY_EM_D1_N30_f50_m2_s15_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 4,926 | 7,562 | 14.7 | 54 |  | DEAD |
| EM | D | PY_EM_D1_N30_f50_m3_s15_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 4,926 | 7,562 | 14.7 | 54 |  | DEAD |
| EM | D | PY_EM_D1_N30_f50_m1_s30_G2 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 6,109 | 8,293 | 13.6 | 64 |  | DEAD |
| EM | D | PY_EM_D1_N30_f50_m1_s30_G3 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 7,689 | 11,419 | 14.9 | 80 |  | DEAD |
| EM | D | PY_EM_D1_N30_f50_m1_s30_G4 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 5,159 | 7,512 | 14.7 | 55 |  | DEAD |
| EM | D | PY_EM_D2_N30_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 3,680 | 5,530 | 19.1 | 38 |  | DEAD |
| EM | D | PY_EM_D2_N20_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 4,764 | 7,487 | 19.9 | 44 |  | DEAD |
| EM | D | PY_EM_D2_PB_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 1,003 | -657 | 20.6 | 20 |  | DEAD |
| EM | D | PY_EM_D2_SG_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 5,219 | 8,748 | 16.6 | 78 |  | DEAD |
| EM | D | PY_EM_D2_N30_f100_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 2,021 | 1,822 | 18.8 | 23 |  | DEAD |
| EM | D | PY_EM_D2_N30_f50_m2_s15_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 3,680 | 5,530 | 19.1 | 38 |  | DEAD |
| EM | D | PY_EM_D2_N30_f50_m1_s30_G3 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 9,240 | 14,024 | 15.6 | 96 |  | DEAD |
| EM | D | PY_EM_D3_N30_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 1,236 | 1,794 | 16.2 | 22 |  | DEAD |
| EM | D | PY_EM_D3_N15_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | -1,746 | -2,722 | 14.1 |  |  | DEAD |

### EM / G (1017 cells)
| entry | sec | cell | paired pts/trade [CI] | MDE | win req / obs | trades | lots avg / peak | WF mean / SD / maxDD | holdout | placebo | $/wk equal lots | $/wk equal risk | lots equal risk | capacity lots | DS3 marg. Sharpe | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| EM | G | G1_0508__EM | 1.4 [0.1,2.6] |  |  /  |  |  /  |  /  /  | 0.75 | 0.99 |  |  |  |  |  | DEAD |
| EM | G | G1_0822__EM | 0.8 [-0.8,2.3] |  |  /  |  |  /  |  /  /  | 0.05 | 0.94 |  |  |  |  |  | DEAD |
| EM | G | G1_0238__EM | 0.7 [-0.5,1.8] |  |  /  |  |  /  |  /  /  | 0.22 | 0.88 |  |  |  |  |  | DEAD |
| EM | G | G1_0579__EM | 0.7 [-1.2,2.4] |  |  /  |  |  /  |  /  /  | -0.21 | 0.95 |  |  |  |  |  | DEAD |
| EM | G | G1_0069__EM | 0.6 [-1.2,2.4] |  |  /  |  |  /  |  /  /  | 0.54 | 0.88 |  |  |  |  |  | DEAD |
| EM | G | G1_0296__EM | 0.6 [-1.3,2.3] |  |  /  |  |  /  |  /  /  | -0.36 | 0.89 |  |  |  |  |  | DEAD |
| EM | G | G1_0376__EM | 0.5 [-1.5,2.3] |  |  /  |  |  /  |  /  /  | -1.85 | 0.92 |  |  |  |  |  | DEAD |
| EM | G | G1_0008__EM | 0.5 [-2.2,3.2] |  |  /  |  |  /  |  /  /  | -3.10 | 0.95 |  |  |  |  |  | DEAD |
| EM | G | G1_0715__EM | 0.4 [-2.0,2.8] |  |  /  |  |  /  |  /  /  | -2.00 | 0.97 |  |  |  |  |  | DEAD |
| EM | G | G1_0658__EM | 0.4 [-1.1,1.9] |  |  /  |  |  /  |  /  /  | 0.33 | 0.86 |  |  |  |  |  | DEAD |
| EM | G | G1_0510__EM | 0.3 [-0.3,0.9] |  |  /  |  |  /  |  /  /  | 0.20 | 0.85 |  |  |  |  |  | DEAD |
| EM | G | G1_0720__EM | 0.2 [-0.9,1.2] |  |  /  |  |  /  |  /  /  | 0.78 | 0.67 |  |  |  |  |  | DEAD |
| EM | G | G1_0940__EM | 0.2 [-2.1,2.3] |  |  /  |  |  /  |  /  /  | -0.23 | 0.79 |  |  |  |  |  | DEAD |
| EM | G | G3_DIV_w30__EM | 0.2 [-1.3,1.7] |  |  /  | 1,811.0 |  /  |  /  /  | -0.37 | 0.97 | 9,149 | 10,691 | 11.7 |  |  | DEAD |
| EM | G | G1_0206__EM | 0.1 [-2.2,2.4] |  |  /  |  |  /  |  /  /  | -0.25 | 0.76 |  |  |  |  |  | DEAD |
| EM | G | G1_0648__EM | 0.1 [-2.0,2.2] |  |  /  |  |  /  |  /  /  | -0.67 | 0.67 |  |  |  |  |  | DEAD |
| EM | G | G1_0954__EM | 0.1 [-1.2,1.3] |  |  /  |  |  /  |  /  /  | 0.53 | 0.74 |  |  |  |  |  | DEAD |
| EM | G | G1_0664__EM | 0.1 [-0.9,1.1] |  |  /  |  |  /  |  /  /  | 0.49 | 0.69 |  |  |  |  |  | DEAD |
| EM | G | G1_0947__EM | 0.1 [-2.2,2.3] |  |  /  |  |  /  |  /  /  | -0.39 | 0.73 |  |  |  |  |  | DEAD |
| EM | G | G3_SESSEND_ASIA_x45__EM | 0.1 [-0.1,0.2] |  |  /  | 1,811.0 |  /  |  /  /  | 0.05 | 0.85 | 8,427 | 8,427 | 10.0 |  |  | DEAD |

### HM / G (1019 cells)
| entry | sec | cell | paired pts/trade [CI] | MDE | win req / obs | trades | lots avg / peak | WF mean / SD / maxDD | holdout | placebo | $/wk equal lots | $/wk equal risk | lots equal risk | capacity lots | DS3 marg. Sharpe | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| HM | G | G1_0069__HM | 1.0 [-0.1,2.2] |  |  /  |  |  /  |  /  /  | -0.05 | 1.00 |  |  |  |  |  | DEAD |
| HM | G | G1_0947__HM | 0.8 [-0.7,2.2] |  |  /  |  |  /  |  /  /  | -0.23 | 1.00 |  |  |  |  |  | DEAD |
| HM | G | G1_0763__HM | 0.8 [-0.7,2.2] |  |  /  |  |  /  |  /  /  | -0.81 | 1.00 |  |  |  |  |  | DEAD |
| HM | G | G1_0708__HM | 0.6 [-1.1,2.3] |  |  /  |  |  /  |  /  /  | -1.21 | 1.00 |  |  |  |  |  | DEAD |
| HM | G | G1_0867__HM | 0.6 [-1.0,2.1] |  |  /  |  |  /  |  /  /  | -0.41 | 1.00 |  |  |  |  |  | DEAD |
| HM | G | G1_0837__HM | 0.6 [-0.8,2.0] |  |  /  |  |  /  |  /  /  | -0.09 | 1.00 |  |  |  |  |  | DEAD |
| HM | G | G1_0814__HM | 0.6 [-0.7,1.8] |  |  /  |  |  /  |  /  /  | -0.72 | 0.99 |  |  |  |  |  | DEAD |
| HM | G | G1_0940__HM | 0.6 [-0.9,2.0] |  |  /  |  |  /  |  /  /  | -0.25 | 1.00 |  |  |  |  |  | DEAD |
| HM | G | G1_0206__HM | 0.6 [-0.9,2.0] |  |  /  |  |  /  |  /  /  | -0.17 | 1.00 |  |  |  |  |  | DEAD |
| HM | G | G1_0535__HM | 0.6 [-0.9,2.0] |  |  /  |  |  /  |  /  /  | -0.47 | 1.00 |  |  |  |  |  | DEAD |
| HM | G | G1_0021__HM | 0.6 [-0.8,1.9] |  |  /  |  |  /  |  /  /  | -0.25 | 1.00 |  |  |  |  |  | DEAD |
| HM | G | G1_0654__HM | 0.6 [-0.6,1.7] |  |  /  |  |  /  |  /  /  | -0.43 | 0.99 |  |  |  |  |  | DEAD |
| HM | G | G1_0956__HM | 0.5 [-1.0,1.9] |  |  /  |  |  /  |  /  /  | -0.49 | 1.00 |  |  |  |  |  | DEAD |
| HM | G | G1_0020__HM | 0.5 [-1.1,2.1] |  |  /  |  |  /  |  /  /  | -0.82 | 1.00 |  |  |  |  |  | DEAD |
| HM | G | G1_0238__HM | 0.5 [-0.3,1.3] |  |  /  |  |  /  |  /  /  | 0.34 | 0.96 |  |  |  |  |  | DEAD |
| HM | G | G1_0508__HM | 0.5 [-0.4,1.3] |  |  /  |  |  /  |  /  /  | 0.03 | 0.95 |  |  |  |  |  | DEAD |
| HM | G | G1_0722__HM | 0.5 [-0.4,1.3] |  |  /  |  |  /  |  /  /  | 0.09 | 0.92 |  |  |  |  |  | DEAD |
| HM | G | G1_0598__HM | 0.5 [-1.0,1.9] |  |  /  |  |  /  |  /  /  | 0.02 | 0.99 |  |  |  |  |  | DEAD |
| HM | G | G1_0316__HM | 0.4 [-1.0,1.9] |  |  /  |  |  /  |  /  /  | -0.47 | 0.99 |  |  |  |  |  | DEAD |
| HM | G | G1_0709__HM | 0.4 [-1.1,1.9] |  |  /  |  |  /  |  /  /  | -0.37 | 1.00 |  |  |  |  |  | DEAD |

### HM10 / D (43 cells)
| entry | sec | cell | paired pts/trade [CI] | MDE | win req / obs | trades | lots avg / peak | WF mean / SD / maxDD | holdout | placebo | $/wk equal lots | $/wk equal risk | lots equal risk | capacity lots | DS3 marg. Sharpe | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| HM10 | D | PY_HM10_D1_N30_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 5,964 | 6,106 | 10.1 | 26 |  | DEAD |
| HM10 | D | PY_HM10_D1_N15_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 2,927 | 2,543 | 9.7 | 19 |  | DEAD |
| HM10 | D | PY_HM10_D1_N45_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 3,820 | 4,212 | 11.0 | 22 |  | DEAD |
| HM10 | D | PY_HM10_D1_PB_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 7,819 | 7,711 | 9.8 | 29 |  | DEAD |
| HM10 | D | PY_HM10_D1_SG_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 7,278 | 7,609 | 10.5 | 30 |  | DEAD |
| HM10 | D | PY_HM10_D1_N30_f100_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | -2,776 | -2,921 | 10.6 |  |  | DEAD |
| HM10 | D | PY_HM10_D1_N30_f50_m2_s15_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 5,964 | 6,106 | 10.1 | 26 |  | DEAD |
| HM10 | D | PY_HM10_D1_N30_f50_m3_s15_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 5,964 | 6,106 | 10.1 | 26 |  | DEAD |
| HM10 | D | PY_HM10_D1_N30_f50_m1_s30_G2 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 7,822 | 7,529 | 9.7 | 31 |  | DEAD |
| HM10 | D | PY_HM10_D1_N30_f50_m1_s30_G3 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 8,771 | 9,398 | 10.4 | 31 |  | DEAD |
| HM10 | D | PY_HM10_D1_N30_f50_m1_s30_G4 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 7,402 | 7,365 | 9.6 | 32 |  | DEAD |
| HM10 | D | PY_HM10_D2_N30_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 4,793 | 5,587 | 10.7 | 23 |  | DEAD |
| HM10 | D | PY_HM10_D2_N20_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 2,597 | 3,560 | 12.1 | 18 |  | DEAD |
| HM10 | D | PY_HM10_D2_PB_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 717 | 989 | 12.0 | 16 |  | DEAD |
| HM10 | D | PY_HM10_D2_SG_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 4,375 | 5,306 | 12.0 | 21 |  | DEAD |
| HM10 | D | PY_HM10_D2_N30_f100_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | -3,460 | -3,224 | 10.6 |  |  | DEAD |
| HM10 | D | PY_HM10_D2_N30_f50_m2_s15_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 4,793 | 5,587 | 10.7 | 23 |  | DEAD |
| HM10 | D | PY_HM10_D2_N30_f50_m1_s30_G3 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 11,627 | 11,934 | 10.1 | 37 |  | DEAD |
| HM10 | D | PY_HM10_D3_N30_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 26 | 129 | 10.7 | 15 |  | DEAD |
| HM10 | D | PY_HM10_D3_N15_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | -2,633 | -2,292 | 10.4 |  |  | DEAD |

### KB / D (43 cells)
| entry | sec | cell | paired pts/trade [CI] | MDE | win req / obs | trades | lots avg / peak | WF mean / SD / maxDD | holdout | placebo | $/wk equal lots | $/wk equal risk | lots equal risk | capacity lots | DS3 marg. Sharpe | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| KB | D | PY_KB_D1_N30_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 14,079 | 12,919 | 9.2 | 35 |  | DEAD |
| KB | D | PY_KB_D1_N15_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 15,502 | 13,762 | 9.1 | 34 |  | DEAD |
| KB | D | PY_KB_D1_N45_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 11,792 | 11,047 | 9.6 | 32 |  | DEAD |
| KB | D | PY_KB_D1_PB_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 10,342 | 8,874 | 8.7 | 27 |  | DEAD |
| KB | D | PY_KB_D1_SG_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 10,221 | 8,642 | 9.0 | 28 |  | DEAD |
| KB | D | PY_KB_D1_N30_f100_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 6,776 | 5,994 | 9.1 | 21 |  | DEAD |
| KB | D | PY_KB_D1_N30_f50_m2_s15_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 14,079 | 12,919 | 9.2 | 35 |  | DEAD |
| KB | D | PY_KB_D1_N30_f50_m3_s15_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 14,079 | 12,919 | 9.2 | 35 |  | DEAD |
| KB | D | PY_KB_D1_N30_f50_m1_s30_G2 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 14,515 | 13,941 | 9.4 | 39 |  | DEAD |
| KB | D | PY_KB_D1_N30_f50_m1_s30_G3 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 10,884 | 10,410 | 9.6 | 27 |  | DEAD |
| KB | D | PY_KB_D1_N30_f50_m1_s30_G4 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 10,877 | 9,862 | 9.1 | 33 |  | DEAD |
| KB | D | PY_KB_D2_N30_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 7,991 | 8,383 | 10.2 | 23 |  | DEAD |
| KB | D | PY_KB_D2_N20_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 5,192 | 5,394 | 10.5 | 19 |  | DEAD |
| KB | D | PY_KB_D2_PB_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 4,403 | 4,736 | 10.7 | 18 |  | DEAD |
| KB | D | PY_KB_D2_SG_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 1,617 | 1,394 | 9.5 | 16 |  | DEAD |
| KB | D | PY_KB_D2_N30_f100_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 1,335 | 1,207 | 10.8 | 15 |  | DEAD |
| KB | D | PY_KB_D2_N30_f50_m2_s15_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 7,991 | 8,383 | 10.2 | 23 |  | DEAD |
| KB | D | PY_KB_D2_N30_f50_m1_s30_G3 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 8,881 | 8,946 | 10.0 | 24 |  | DEAD |
| KB | D | PY_KB_D3_N30_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 9,674 | 9,453 | 10.0 | 26 |  | DEAD |
| KB | D | PY_KB_D3_N15_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 4,038 | 3,258 | 9.4 | 18 |  | DEAD |

### KB / G (1015 cells)
| entry | sec | cell | paired pts/trade [CI] | MDE | win req / obs | trades | lots avg / peak | WF mean / SD / maxDD | holdout | placebo | $/wk equal lots | $/wk equal risk | lots equal risk | capacity lots | DS3 marg. Sharpe | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| KB | G | G1_0527__KB | 0.2 [-0.2,0.5] |  |  /  |  |  /  |  /  /  | -0.06 | 0.90 |  |  |  |  |  | DEAD |
| KB | G | G3_SESSEND_NY_x45__KB | 0.0 [-0.0,0.0] |  |  /  | 7,250.0 |  /  |  /  /  | 0.01 | 0.77 | 16,270 | 16,264 | 10.0 |  |  | DEAD |
| KB | G | G1_0720__KB | 0.0 [-0.6,0.6] |  |  /  |  |  /  |  /  /  | 0.01 | 0.84 |  |  |  |  |  | DEAD |
| KB | G | G3_SESSEND_NY_x30__KB | 0.0 [-0.0,0.0] |  |  /  | 7,250.0 |  /  |  /  /  | 0.01 | 0.70 | 16,252 | 16,232 | 10.0 |  |  | DEAD |
| KB | G | G3_SESSEND_LONDON_x45__KB | -0.0 [-0.2,0.1] |  |  /  | 7,250.0 |  /  |  /  /  | -0.00 | 0.61 | 16,662 | 16,360 | 9.8 |  |  | DEAD |
| KB | G | G1_0508__KB | -0.0 [-0.8,0.7] |  |  /  |  |  /  |  /  /  | -0.04 | 0.93 |  |  |  |  |  | DEAD |
| KB | G | G3_SESSEND_ASIA_x45__KB | -0.1 [-0.2,0.0] |  |  /  | 7,250.0 |  /  |  /  /  | -0.03 | 0.14 | 15,407 | 15,579 | 10.1 |  |  | DEAD |
| KB | G | G3_SESSEND_ASIA_x30__KB | -0.1 [-0.2,0.1] |  |  /  | 7,250.0 |  /  |  /  /  | -0.12 | 0.34 | 15,867 | 16,065 | 10.1 |  |  | DEAD |
| KB | G | G1_0510__KB | -0.1 [-0.5,0.2] |  |  /  |  |  /  |  /  /  | -0.13 | 0.52 |  |  |  |  |  | DEAD |
| KB | G | G1_0390__KB | -0.1 [-1.0,0.7] |  |  /  |  |  /  |  /  /  | -0.16 | 0.88 |  |  |  |  |  | DEAD |
| KB | G | G1_0060__KB | -0.2 [-0.9,0.5] |  |  /  |  |  /  |  /  /  | 0.41 | 0.79 |  |  |  |  |  | DEAD |
| KB | G | G1_0238__KB | -0.2 [-1.0,0.6] |  |  /  |  |  /  |  /  /  | 0.17 | 0.81 |  |  |  |  |  | DEAD |
| KB | G | G1_0658__KB | -0.3 [-1.2,0.6] |  |  /  |  |  /  |  /  /  | -0.26 | 0.83 |  |  |  |  |  | DEAD |
| KB | G | G3_SESSEND_LONDON_x30__KB | -0.3 [-0.5,-0.0] |  |  /  | 7,250.0 |  /  |  /  /  | -0.37 | 0.03 | 15,784 | 15,803 | 10.0 |  |  | DEAD |
| KB | G | G1_0601__KB | -0.3 [-0.8,0.2] |  |  /  |  |  /  |  /  /  | -0.19 | 0.40 |  |  |  |  |  | DEAD |
| KB | G | G1_0569__KB | -0.3 [-1.1,0.5] |  |  /  |  |  /  |  /  /  | -0.08 | 0.74 |  |  |  |  |  | DEAD |
| KB | G | G1_0942__KB | -0.3 [-1.1,0.5] |  |  /  |  |  /  |  /  /  | -0.45 | 0.77 |  |  |  |  |  | DEAD |
| KB | G | G2_m40_r4_t8_s1__KB | -0.3 [-1.0,0.4] |  |  /  | 6,584.0 |  /  |  /  /  |  | 0.65 | 15,329 | 15,574 | 10.2 | 47 |  | DEAD |
| KB | G | G1_0005__KB | -0.4 [-1.5,0.7] |  |  /  |  |  /  |  /  /  | -0.45 | 0.96 |  |  |  |  |  | DEAD |
| KB | G | G1_0579__KB | -0.4 [-1.4,0.7] |  |  /  |  |  /  |  /  /  | -0.13 | 0.89 |  |  |  |  |  | DEAD |

### SM / D (43 cells)
| entry | sec | cell | paired pts/trade [CI] | MDE | win req / obs | trades | lots avg / peak | WF mean / SD / maxDD | holdout | placebo | $/wk equal lots | $/wk equal risk | lots equal risk | capacity lots | DS3 marg. Sharpe | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| SM | D | PY_SM_D1_N30_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 6,296 | 9,800 | 15.1 | 69 |  | DEAD |
| SM | D | PY_SM_D1_N15_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 2,687 | 3,892 | 13.5 | 30 |  | DEAD |
| SM | D | PY_SM_D1_N45_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 5,729 | 8,949 | 15.4 | 66 |  | DEAD |
| SM | D | PY_SM_D1_PB_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 5,708 | 8,282 | 14.0 | 58 |  | DEAD |
| SM | D | PY_SM_D1_SG_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 9,187 | 14,820 | 16.0 | 140 |  | DEAD |
| SM | D | PY_SM_D1_N30_f100_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 1,747 | 2,795 | 13.4 | 23 |  | DEAD |
| SM | D | PY_SM_D1_N30_f50_m2_s15_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 6,296 | 9,800 | 15.1 | 69 |  | DEAD |
| SM | D | PY_SM_D1_N30_f50_m3_s15_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 6,296 | 9,800 | 15.1 | 69 |  | DEAD |
| SM | D | PY_SM_D1_N30_f50_m1_s30_G2 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 4,117 | 6,251 | 14.0 | 45 |  | DEAD |
| SM | D | PY_SM_D1_N30_f50_m1_s30_G3 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 7,958 | 12,160 | 15.7 | 81 |  | DEAD |
| SM | D | PY_SM_D1_N30_f50_m1_s30_G4 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 3,793 | 6,167 | 14.7 | 45 |  | DEAD |
| SM | D | PY_SM_D2_N30_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 2,638 | 3,974 | 17.8 | 31 |  | DEAD |
| SM | D | PY_SM_D2_N20_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 3,977 | 5,532 | 18.4 | 36 |  | DEAD |
| SM | D | PY_SM_D2_PB_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | -492 | -2,856 | 18.9 |  |  | DEAD |
| SM | D | PY_SM_D2_SG_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 7,203 | 11,750 | 16.2 | 108 |  | DEAD |
| SM | D | PY_SM_D2_N30_f100_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 661 | -234 | 18.9 | 19 |  | DEAD |
| SM | D | PY_SM_D2_N30_f50_m2_s15_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 2,638 | 3,974 | 17.8 | 31 |  | DEAD |
| SM | D | PY_SM_D2_N30_f50_m1_s30_G3 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 6,549 | 10,492 | 16.2 | 68 |  | DEAD |
| SM | D | PY_SM_D3_N30_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 2,459 | 3,811 | 15.5 | 29 |  | DEAD |
| SM | D | PY_SM_D3_N15_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | -1,586 | -1,814 | 14.2 |  |  | DEAD |

### SM / G (1018 cells)
| entry | sec | cell | paired pts/trade [CI] | MDE | win req / obs | trades | lots avg / peak | WF mean / SD / maxDD | holdout | placebo | $/wk equal lots | $/wk equal risk | lots equal risk | capacity lots | DS3 marg. Sharpe | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| SM | G | G1_0720__SM | 0.3 [-0.7,1.3] |  |  /  |  |  /  |  /  /  | 0.44 | 0.96 |  |  |  |  |  | DEAD |
| SM | G | G1_0357__SM | 0.3 [-1.5,2.0] |  |  /  |  |  /  |  /  /  | -1.26 | 0.96 |  |  |  |  |  | DEAD |
| SM | G | G1_0238__SM | 0.3 [-0.9,1.5] |  |  /  |  |  /  |  /  /  | 0.25 | 0.97 |  |  |  |  |  | DEAD |
| SM | G | G1_0569__SM | 0.2 [-1.1,1.5] |  |  /  |  |  /  |  /  /  | 0.81 | 0.97 |  |  |  |  |  | DEAD |
| SM | G | G1_0510__SM | 0.1 [-0.5,0.7] |  |  /  |  |  /  |  /  /  | -0.12 | 0.78 |  |  |  |  |  | DEAD |
| SM | G | G1_0945__SM | 0.1 [-2.0,2.3] |  |  /  |  |  /  |  /  /  | 1.00 | 0.99 |  |  |  |  |  | DEAD |
| SM | G | G1_0527__SM | 0.0 [-0.7,0.7] |  |  /  |  |  /  |  /  /  | -0.56 | 0.76 |  |  |  |  |  | DEAD |
| SM | G | G1_0783__SM | 0.0 [-1.9,1.9] |  |  /  |  |  /  |  /  /  | -0.71 | 0.96 |  |  |  |  |  | DEAD |
| SM | G | G3_SESSEND_ASIA_x45__SM | 0.0 [-0.1,0.2] |  |  /  | 1,863.0 |  /  |  /  /  | -0.10 | 0.72 | 9,628 | 9,739 | 10.1 |  |  | DEAD |
| SM | G | G1_0664__SM | 0.0 [-1.1,1.0] |  |  /  |  |  /  |  /  /  | -0.14 | 0.80 |  |  |  |  |  | DEAD |
| SM | G | G3_SESSEND_NY_x45__SM | 0.0 [0.0,0.0] |  |  /  | 1,863.0 |  /  |  /  /  | 0.00 |  | 9,543 | 9,544 | 10.0 |  |  | DEAD |
| SM | G | G3_SESSEND_NY_x30__SM | 0.0 [-0.0,0.0] |  |  /  | 1,863.0 |  /  |  /  /  | -0.01 | 0.58 | 9,553 | 9,554 | 10.0 |  |  | DEAD |
| SM | G | G1_0508__SM | -0.0 [-1.4,1.3] |  |  /  |  |  /  |  /  /  | 0.45 | 0.95 |  |  |  |  |  | DEAD |
| SM | G | G1_0335__SM | -0.0 [-1.7,1.5] |  |  /  |  |  /  |  /  /  | -0.93 | 0.86 |  |  |  |  |  | DEAD |
| SM | G | G1_0451__SM | -0.1 [-1.8,1.6] |  |  /  |  |  /  |  /  /  | -0.03 | 0.91 |  |  |  |  |  | DEAD |
| SM | G | G1_0056__SM | -0.1 [-1.3,1.0] |  |  /  |  |  /  |  /  /  | -0.72 | 0.83 |  |  |  |  |  | DEAD |
| SM | G | G1_0359__SM | -0.1 [-1.5,1.1] |  |  /  |  |  /  |  /  /  | -0.89 | 0.82 |  |  |  |  |  | DEAD |
| SM | G | G1_0601__SM | -0.1 [-1.0,0.7] |  |  /  |  |  /  |  /  /  | 0.18 | 0.67 |  |  |  |  |  | DEAD |
| SM | G | G1_0330__SM | -0.2 [-1.9,1.5] |  |  /  |  |  /  |  /  /  | -1.97 | 0.86 |  |  |  |  |  | DEAD |
| SM | G | G1_0113__SM | -0.2 [-2.1,1.7] |  |  /  |  |  /  |  /  /  | -0.63 | 0.94 |  |  |  |  |  | DEAD |

### ST / G (1019 cells)
| entry | sec | cell | paired pts/trade [CI] | MDE | win req / obs | trades | lots avg / peak | WF mean / SD / maxDD | holdout | placebo | $/wk equal lots | $/wk equal risk | lots equal risk | capacity lots | DS3 marg. Sharpe | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ST | G | G1_0563__ST | 0.1 [-1.0,1.1] |  |  /  |  |  /  |  /  /  | 0.54 | 0.98 |  |  |  |  |  | DEAD |
| ST | G | G3_SESSEND_LONDON_x45__ST | 0.0 [-0.1,0.1] |  |  /  | 7,029.0 |  /  |  /  /  | 0.07 | 0.79 | 33,102 | 33,403 | 14.1 |  |  | DEAD |
| ST | G | G3_SESSEND_NY_x30__ST | 0.0 [-0.0,0.0] |  |  /  | 7,029.0 |  /  |  /  /  | -0.00 | 0.79 | 31,158 | 31,152 | 14.0 |  |  | DEAD |
| ST | G | G3_SESSEND_NY_x45__ST | 0.0 [-0.0,0.0] |  |  /  | 7,029.0 |  /  |  /  /  | -0.01 | 0.62 | 31,146 | 31,147 | 14.0 |  |  | DEAD |
| ST | G | G3_OPP_EM__ST | -0.0 [-0.4,0.3] |  |  /  | 7,029.0 |  /  |  /  /  | 0.31 | 0.82 | 26,137 | 25,334 | 13.6 |  |  | DEAD |
| ST | G | G1_0510__ST | -0.0 [-0.4,0.4] |  |  /  |  |  /  |  /  /  | -0.10 | 0.72 |  |  |  |  |  | DEAD |
| ST | G | G3_SESSEND_ASIA_x45__ST | -0.0 [-0.2,0.1] |  |  /  | 7,029.0 |  /  |  /  /  | -0.03 | 0.40 | 30,953 | 30,839 | 13.9 |  |  | DEAD |
| ST | G | G1_0060__ST | -0.0 [-0.8,0.7] |  |  /  |  |  /  |  /  /  | 0.32 | 0.98 |  |  |  |  |  | DEAD |
| ST | G | G3_OPP_SM__ST | -0.1 [-0.4,0.2] |  |  /  | 7,029.0 |  /  |  /  /  | 0.14 | 0.68 | 30,978 | 30,714 | 13.9 |  |  | DEAD |
| ST | G | G1_0725__ST | -0.1 [-1.2,1.0] |  |  /  |  |  /  |  /  /  | 0.44 | 0.97 |  |  |  |  |  | DEAD |
| ST | G | G1_0238__ST | -0.1 [-0.9,0.6] |  |  /  |  |  /  |  /  /  | 0.15 | 0.97 |  |  |  |  |  | DEAD |
| ST | G | G1_0508__ST | -0.1 [-1.0,0.6] |  |  /  |  |  /  |  /  /  | -0.13 | 0.98 |  |  |  |  |  | DEAD |
| ST | G | G1_0089__ST | -0.1 [-1.3,1.0] |  |  /  |  |  /  |  /  /  | 0.53 | 0.98 |  |  |  |  |  | DEAD |
| ST | G | G1_0720__ST | -0.2 [-0.8,0.5] |  |  /  |  |  /  |  /  /  | 0.38 | 0.85 |  |  |  |  |  | DEAD |
| ST | G | G3_SESSEND_ASIA_x30__ST | -0.2 [-0.4,-0.0] |  |  /  | 7,029.0 |  /  |  /  /  | -0.10 | 0.10 | 30,951 | 30,845 | 14.0 |  |  | DEAD |
| ST | G | G1_0430__ST | -0.2 [-0.9,0.4] |  |  /  |  |  /  |  /  /  | -0.03 | 0.76 |  |  |  |  |  | DEAD |
| ST | G | G1_0069__ST | -0.2 [-1.3,0.8] |  |  /  |  |  /  |  /  /  | 0.29 | 1.00 |  |  |  |  |  | DEAD |
| ST | G | G1_0056__ST | -0.2 [-0.9,0.4] |  |  /  |  |  /  |  /  /  | 0.05 | 0.83 |  |  |  |  |  | DEAD |
| ST | G | G1_0913__ST | -0.2 [-1.6,1.1] |  |  /  |  |  /  |  /  /  | 0.06 | 1.00 |  |  |  |  |  | DEAD |
| ST | G | G1_0148__ST | -0.2 [-1.4,0.9] |  |  /  |  |  /  |  /  /  | 0.18 | 0.97 |  |  |  |  |  | DEAD |

### ST10 / D (43 cells)
| entry | sec | cell | paired pts/trade [CI] | MDE | win req / obs | trades | lots avg / peak | WF mean / SD / maxDD | holdout | placebo | $/wk equal lots | $/wk equal risk | lots equal risk | capacity lots | DS3 marg. Sharpe | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ST10 | D | PY_ST10_D1_N30_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 7,448 | 6,874 | 10.1 | 23 |  | DEAD |
| ST10 | D | PY_ST10_D1_N15_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 3,936 | 3,429 | 10.1 | 18 |  | DEAD |
| ST10 | D | PY_ST10_D1_N45_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 9,559 | 8,728 | 9.6 | 28 |  | DEAD |
| ST10 | D | PY_ST10_D1_PB_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 3,696 | 3,132 | 10.3 | 18 |  | DEAD |
| ST10 | D | PY_ST10_D1_SG_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 9,499 | 8,576 | 9.6 | 28 |  | DEAD |
| ST10 | D | PY_ST10_D1_N30_f100_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 994 | 765 | 10.2 | 15 |  | DEAD |
| ST10 | D | PY_ST10_D1_N30_f50_m2_s15_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 7,448 | 6,874 | 10.1 | 23 |  | DEAD |
| ST10 | D | PY_ST10_D1_N30_f50_m3_s15_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 7,448 | 6,874 | 10.1 | 23 |  | DEAD |
| ST10 | D | PY_ST10_D1_N30_f50_m1_s30_G2 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 2,973 | 2,260 | 9.8 | 18 |  | DEAD |
| ST10 | D | PY_ST10_D1_N30_f50_m1_s30_G3 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 11,119 | 10,835 | 9.4 | 28 |  | DEAD |
| ST10 | D | PY_ST10_D1_N30_f50_m1_s30_G4 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 6,227 | 6,243 | 10.7 | 24 |  | DEAD |
| ST10 | D | PY_ST10_D2_N30_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 1,026 | 1,527 | 9.6 | 16 |  | DEAD |
| ST10 | D | PY_ST10_D2_N20_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | -1,631 | -944 | 9.9 |  |  | DEAD |
| ST10 | D | PY_ST10_D2_PB_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 767 | 1,605 | 9.6 | 16 |  | DEAD |
| ST10 | D | PY_ST10_D2_SG_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 946 | 1,344 | 10.2 | 16 |  | DEAD |
| ST10 | D | PY_ST10_D2_N30_f100_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | -7,651 | -6,890 | 10.1 |  |  | DEAD |
| ST10 | D | PY_ST10_D2_N30_f50_m2_s15_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 1,026 | 1,527 | 9.6 | 16 |  | DEAD |
| ST10 | D | PY_ST10_D2_N30_f50_m1_s30_G3 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 8,475 | 8,549 | 9.1 | 25 |  | DEAD |
| ST10 | D | PY_ST10_D3_N30_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | 4,869 | 5,039 | 10.5 | 20 |  | DEAD |
| ST10 | D | PY_ST10_D3_N15_f50_m1_s30_G1 |  [,] |  |  /  |  |  /  |  /  /  |  |  | -5,027 | -4,599 | 9.5 |  |  | DEAD |

Named control row in every G table: live TH-loss-on-ST configuration (cell id containing TH_LIVE). All cells: l2vast/ds3/rows/ files.
