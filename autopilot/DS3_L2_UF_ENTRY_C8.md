# DS3_L2_UF_ENTRY_C8 - L2-UNTIL-FOUND cycle 8, ENTRY: cross-day causal-tag lot multiplier on the integer-lot 70/30 (agent UF-ENTRY, 2026-10-31)
Research only; UNTOUCHED never read. Prereg autopilot/UF_ENTRY_C8_prereg.md sha256 aceee96dd2141db901d4b13b8e10dae1955fc736b5892bd0ed5b363630b43359 (before any cycle-8 statistic); 34 cells x 2 governors; PRE+X' selection out/uf/entry_c8/pre_sel.json (copy autopilot/UF_ENTRY_C8_PRESEL.json) sha256 3515bc9928e6ea8802f439da6c0b5725d93e80dc540f16f971dbe9b94ed7e65e logged before the one recent look. Base = the split at INTEGER live lots (K6 2, P6 7, U6 4, H6 4/2 NY-AM, ST 10, WT 7 research) with the cycle-7 MODELLED add slippage (d=2 s, state-dependent) on every add; multiplier m in {0.5,1,1.5} -> L' = round(m L); the split at L' uses add contracts L' - round(0.7 L'). Tags (all causal at the entry second): vol_tag_causal sidecar, prior-day range ratio, prior-day RTH vol ratio, VIX expanding tercile, Globex-gap tercile (sided), prior day trend/other. Units: stack \$/wk at research lots (lock engine; live lots = x live/research per book), c=1 (no equal-risk rescaling: lots are the object), MDE in parentheses. PLAN-R = locks at planned lots (the base); SIZED-R = approximation labelled (daily results stitched from three engine runs with R scaled 0.5 / 1 / 1.5 by the book's largest multiplier of the day, SW from the PLAN-R rows).

## Page 1 - the verdict
1. **No tag-driven lot multiplier is information; they are STRUCTURE (lot dispersion).** Against the lot-factor-matched UNIFORM line (the base scaled by the cell's mean multiplier), the 34 cells average -8.6k L6M / -8.0k HOLD / -9.0k PRE / +0.3k X' per week (plan-R, N) and only 32% / 29% / 21% / 62% are >= 0 in L6M / HOLD / PRE / X'; against the base at c=1 (no scaling) 21% / 15% / 18% / 47% are >= 0. White RC over the 34 cells vs the uniform line: L6M max t 3.22 p 0.106 (best t_vix|P4), HOLD 2.50 p 0.251, PRE 1.36 p 0.749, X' 1.05 p 0.934; cumulative-adjusted p 1.0 (N_cum 2,889,091 + 68).
2. **PRE-selected cell `t_pdr|P4`** (prior-day range ratio in the top tercile -> 0.5x lots; mean multiplier 0.79): vs the uniform line (N, plan-R) 2026 +18.8k, L6M +6.4k (MDE 23k), HOLD +3.9k, PRE +4.1k, X' +2.0k - positive but every number is inside its MDE and the shuffled-tag placebo (tags permuted within the label week, 100 draws) gives a median of the same size: rank L6M 0.45, HOLD 0.56, PRE 0.94, X' 0.90. Against the base itself (no scaling) it LOSES: L6M -8.6k, HOLD -8.6k, PRE -8.4k (lower average lots). Under SIZED-R the vs-uniform sign flips (L6M -4.7k, HOLD -6.8k, PRE +8.6k): the governor choice moves the number by more than the tag does. Tier **BEST-AVAILABLE-NEGATIVE** (structure).
3. **Per planned lot / per contract the tags carry nothing.** The multiplier does not change a contract's result; the lot-weighted mean pts per trade is the information measure:
| lot-weighted pts per trade | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| base (integer live lots, modelled slippage), per planned lot | +2.99 (MDE 5.94) | +2.55 (MDE 3.00) | +2.08 (MDE 2.72) | +1.23 (MDE 2.16) | +0.76 (MDE 2.95) |
| selected multiplier rule, per planned lot (weights = lots) | +2.32 (MDE 6.00) | +2.30 (MDE 3.11) | +1.64 (MDE 2.86) | +1.72 (MDE 2.21) | +1.11 (MDE 2.94) |
| base, per contract of final position | +4.44 (MDE 5.83) | +3.73 (MDE 3.02) | +3.26 (MDE 3.00) | +2.77 (MDE 2.03) | +1.67 (MDE 2.96) |
| selected rule, per contract of final position | +4.09 (MDE 6.34) | +3.48 (MDE 3.01) | +3.04 (MDE 3.11) | +2.55 (MDE 2.11) | +1.59 (MDE 2.99) |

4. The cells with the largest L6M gain vs the uniform line (t_vix hi->0.5x +19k L6M, t_gap, t_vix lo->1.5x) flip across windows (t_vix hi->0.5x: PRE -10k; t_vix lo->1.5x: PRE -20k; t_gap lo->0.5x: PRE +6k but X' -4.5k): looked-data recent-only, the same shape as every earlier recent lead.
5. UF_TRIALS +68 (34 cells x 2 governors); DEAD_CELLS +68 (UFE8).

## 1. All 34 cells (stack \$/wk, N basis; deltas in k\$/wk)
| tag | pattern | mean lot mult | N plan-R vs uniform line L6M / HOLD / PRE / X' | N plan-R vs base L6M / HOLD / PRE / X' | N SIZED-R vs uniform L6M / HOLD / PRE / X' | LIVE-CAL plan-R vs uniform L6M / HOLD |
|--|--|--|--|--|--|--|
| t_vol | P1 | 1.08 | -25.0 / -22.7 / -13.4 / +2.5 | -19.7 / -18.3 / -9.0 / +3.8 | +13.9 / +13.4 / -0.4 / +4.4 | -26.7 / -24.0 |
| t_vol | P2 | 0.92 | -6.2 / -6.1 / -16.8 / +0.5 | -11.4 / -10.5 / -21.2 / -0.9 | -1.5 / -5.0 / +2.5 / -3.4 | -8.7 / -9.3 |
| t_vol | P3 | 1.22 | -31.2 / -26.3 / -12.0 / -1.0 | -15.9 / -13.5 / +0.7 / +2.9 | +2.0 / +2.7 / +4.3 / -0.3 | -28.2 / -23.5 |
| t_vol | P4 | 0.78 | +9.2 / +8.2 / -2.5 / +2.6 | -6.1 / -4.6 / -15.1 / -1.4 | +3.7 / +3.4 / -2.1 / +3.5 | +7.2 / +6.0 |
| t_vol | P5 | 1.14 | -16.2 / -14.3 / -14.3 / -5.2 | -6.3 / -6.0 / -6.0 / -2.6 | -8.3 / -10.7 / +2.5 / -4.9 | -15.3 / -14.1 |
| t_vol | P6 | 0.86 | +3.2 / +2.0 / +0.3 / +3.3 | -6.8 / -6.3 / -8.0 / +0.8 | +3.8 / +4.4 / +1.9 / +4.0 | +0.6 / -0.3 |
| t_pdr | P1 | 1.08 | -19.2 / -16.8 / -10.9 / -6.3 | -13.8 / -12.2 / -6.3 / -4.9 | +17.3 / +18.7 / -16.3 / -8.4 | -16.0 / -13.6 |
| t_pdr | P2 | 0.92 | -12.8 / -10.9 / -12.6 / +6.1 | -18.2 / -15.4 / -17.1 / +4.7 | -10.5 / -12.5 / +9.8 / +14.2 | -16.5 / -14.1 |
| t_pdr | P3 | 1.21 | -25.9 / -22.4 / -10.6 / +2.3 | -10.9 / -9.9 / +1.8 / +6.1 | +10.9 / +12.6 / -12.9 / -2.1 | -20.2 / -17.1 |
| t_pdr | P4 | 0.79 | +6.4 / +3.9 / +4.1 / +2.0 | -8.6 / -8.6 / -8.4 / -1.8 | -4.7 / -6.8 / +8.6 / +6.1 | +3.5 / +1.1 |
| t_pdr | P5 | 1.14 | -19.2 / -14.7 / -16.6 / +4.1 | -9.7 / -6.8 / -8.7 / +6.5 | -5.8 / -5.8 / +1.2 / +8.1 | -20.0 / -15.2 |
| t_pdr | P6 | 0.86 | +6.7 / +5.6 / -0.2 / -8.6 | -2.9 / -2.3 / -8.2 / -11.0 | +6.3 / +6.1 / -3.4 / -6.3 | +4.2 / +3.5 |
| t_rv | P1 | 1.07 | -22.8 / -23.2 / -7.6 / +1.9 | -17.6 / -18.8 / -3.2 / +3.3 | +20.2 / +18.0 / -4.4 / +8.5 | -19.2 / -19.6 |
| t_rv | P2 | 0.93 | -10.3 / -7.5 / -13.0 / +2.8 | -15.5 / -11.9 / -17.4 / +1.4 | -11.6 / -10.3 / -0.0 / -2.8 | -14.4 / -11.2 |
| t_rv | P3 | 1.20 | -24.5 / -22.7 / -8.3 / +0.4 | -10.8 / -11.2 / +3.2 / +3.9 | +17.5 / +16.3 / -5.8 / +6.0 | -19.1 / -17.8 |
| t_rv | P4 | 0.80 | -2.6 / -1.2 / +1.8 / -1.3 | -16.3 / -12.7 / -9.7 / -4.8 | -10.4 / -9.6 / +3.3 / -1.3 | -4.6 / -3.2 |
| t_rv | P5 | 1.12 | -7.7 / -6.3 / -14.8 / +4.0 | +0.8 / +0.8 / -7.7 / +6.2 | -1.2 / -0.7 / -3.3 / -1.5 | -9.7 / -7.7 |
| t_rv | P6 | 0.88 | +1.7 / -0.5 / +0.7 / +1.6 | -6.8 / -7.6 / -6.4 / -0.6 | +2.7 / +1.7 / +1.5 / +2.6 | -0.0 / -1.8 |
| t_vix | P1 | 1.10 | -19.7 / -17.0 / -10.5 / -11.2 | -12.8 / -11.2 / -4.7 / -9.4 | -9.3 / -7.9 / +5.2 / -10.1 | -19.5 / -16.7 |
| t_vix | P2 | 0.90 | +12.0 / +10.3 / -19.8 / +9.1 | +5.1 / +4.5 / -25.6 / +7.4 | +11.8 / +10.0 / -10.7 / +13.3 | +8.5 / +7.0 |
| t_vix | P3 | 1.19 | -21.2 / -18.0 / -12.3 / -3.7 | -7.6 / -6.6 / -1.0 / -0.2 | -12.2 / -10.2 / +3.3 / -5.8 | -19.8 / -16.6 |
| t_vix | P4 | 0.81 | +19.2 / +16.2 / -10.5 / +3.2 | +5.5 / +4.8 / -21.8 / -0.3 | +15.8 / +13.3 / -8.2 / +5.2 | +15.4 / +12.7 |
| t_vix | P5 | 1.10 | -7.1 / -6.0 / -9.4 / +5.9 | -0.4 / -0.4 / -3.8 / +7.6 | -4.1 / -3.3 / -2.6 / +8.1 | -6.9 / -5.7 |
| t_vix | P6 | 0.90 | +1.5 / +1.0 / +1.8 / -7.5 | -5.2 / -4.6 / -3.8 / -9.2 | +2.9 / +2.3 / +1.9 / -4.3 | +0.3 / -0.1 |
| t_gap | P1 | 0.99 | +8.6 / +5.5 / +12.9 / -8.6 | +8.2 / +5.2 / +12.6 / -8.7 | +34.1 / +28.5 / +24.5 / -9.5 | +9.2 / +6.3 |
| t_gap | P2 | 1.01 | -22.6 / -22.5 / -26.7 / +7.9 | -22.2 / -22.1 / -26.4 / +8.0 | -22.7 / -14.3 / -34.1 / +2.3 | -21.9 / -21.9 |
| t_gap | P3 | 1.15 | -20.9 / -20.7 / -3.1 / -4.4 | -10.2 / -11.7 / +5.7 / -1.6 | +11.3 / +9.7 / +16.1 / -8.0 | -20.9 / -20.5 |
| t_gap | P4 | 0.85 | -3.6 / -1.0 / -17.5 / +1.9 | -14.3 / -9.9 / -26.4 / -0.9 | -4.4 / -1.7 / -18.8 / +2.1 | -7.6 / -4.7 |
| t_gap | P5 | 1.16 | -10.2 / -12.0 / -24.3 / +6.1 | +0.9 / -2.7 / -15.1 / +8.9 | -11.6 / -6.6 / -24.2 / -0.3 | -7.3 / -9.3 |
| t_gap | P6 | 0.84 | +13.2 / +11.0 / +6.4 / -4.5 | +2.1 / +1.8 / -2.8 / -7.3 | +12.3 / +10.2 / +5.9 / -4.5 | +8.7 / +6.9 |
| t_dtype | Q1 | 0.93 | -4.5 / -6.0 / -10.5 / -7.2 | -9.3 / -10.0 / -14.5 / -8.5 | +26.7 / +23.1 / -15.5 / -6.0 | -4.9 / -6.3 |
| t_dtype | Q2 | 1.07 | -27.7 / -24.4 / -25.2 / +7.9 | -22.9 / -20.4 / -21.2 / +9.2 | -17.1 / -16.5 / +9.8 / +10.6 | -28.8 / -25.2 |
| t_dtype | Q3 | 1.20 | -13.8 / -13.1 / -10.4 / -0.2 | +0.2 / -1.3 / +1.2 / +3.4 | +15.9 / +13.6 / -9.7 / -1.5 | -10.3 / -9.8 |
| t_dtype | Q4 | 0.80 | +2.5 / +1.5 / -0.7 / +3.3 | -11.5 / -10.3 / -12.4 / -0.3 | -7.5 / -7.6 / +5.4 / +5.0 | +0.2 / -0.7 |

## 2. Placebo (shuffled tags within the label week)
| cell | window | real delta vs uniform line | shuffled-tag placebo median | rank (100 draws) |
|--|--|--|--|--|
| t_pdr|P4 | L6M | +6.4k | +7.4k | 0.45 |
| t_pdr|P4 | HOLD | +3.9k | +3.0k | 0.56 |
| t_pdr|P4 | PRE | +4.1k | -1.2k | 0.94 |
| t_pdr|P4 | X | +2.0k | -2.8k | 0.90 |
| t_vol|P6 | L6M | +3.2k | +3.1k | 0.51 |
| t_vol|P6 | HOLD | +2.0k | +2.6k | 0.43 |
| t_vol|P6 | PRE | +0.3k | +0.4k | 0.49 |
| t_vol|P6 | X | +3.3k | -0.4k | 0.82 |
| t_rv|P6 | L6M | +1.7k | +2.4k | 0.44 |
| t_rv|P6 | HOLD | -0.5k | +0.4k | 0.42 |
| t_rv|P6 | PRE | +0.7k | -0.0k | 0.64 |
| t_rv|P6 | X | +1.6k | -1.8k | 0.95 |

## 3. Selected cell per book (plan-R, N, delta vs the base book P&L, c=1, MDE)
| book | L6M | HOLD | PRE | X' |
|--|--|--|--|--|
| ST | -3.7k (15.7k) | -4.0k (14.1k) | -3.6k (7.2k) | -3.7k (7.2k) |
| HM | +0.9k (10.2k) | +0.7k (8.9k) | -0.2k (6.3k) | +2.6k (7.4k) |
| WT | -1.7k (5.0k) | -1.1k (4.5k) | -1.0k (4.3k) | -1.8k (3.6k) |
| KB | -1.0k (5.6k) | -1.4k (5.3k) | -0.2k (4.9k) | +1.3k (3.0k) |
| SM | -1.8k (5.3k) | -1.7k (4.7k) | -1.9k (3.4k) | -0.3k (3.5k) |
| PE | -1.4k (6.9k) | -1.0k (6.0k) | -1.4k (5.8k) | +0.1k (4.4k) |

## 4. Caveats
Integer rounding of m L (np.round, 3.5 -> 4, 10.5 -> 10) and the extra add slippage at the new lot size (state-dependent model) are in every cell; the uniform line is the naive EQR scaling c*raw - sweep(c) (it scales lots and sweep but not the lock R), so the line itself is optimistic for scale-ups (R fixed) and the comparison is conservative against the rules. SIZED-R is an approximation (stitching), so SIZED-R entries are indicative only. 2026 is ~5 weeks.
## 5. Files
code l2vast/ds3/code/uf/ufe8_lib.py, ufe8_tags.py, ufe8_run.py, ufe8_stageA.py, ufe8_stageB.py, ufe8_report.py; outputs l2vast/ds3/out/uf/entry_c8/.
