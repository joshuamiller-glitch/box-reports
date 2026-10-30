# DS3_NO_TRADE_ZONES - T-NO-TRADE-ZONES section B: rules by the POI AHEAD of / BEHIND a signal (skip, size, re-target, wait, split-behind, tighten, size-up), on the market and 70/30 bases
Agent NTZ-1. Research only; no live / execution / chart change; UNTOUCHED never read; masks own, capped 20260206 (2026 = 20260101.., L6M = 20250801.., HOLD = 20250701.., PRE = 20240201..20250630, X' = 20230401..20240131; L3M = 20251106.. is a VIEW column, never used to select). 44,370 capped trades (10 books), measured fills; bases M, N (no target correction), LIVE (= LIVE-P9, stop exits 2.45 pt); entry bases MKT (market at the signal second, 1 lot) and SPL (70/30 plain 3-pt dip split, the L2SE floor via cf_engine). Preregs (sha256 in DECISIONS.md): C map 04fc159a, B rules 8f874dc9 + amendment 1 7fc59ea7 (D-type bug caught before any recent window was read), B2 combos/time 5c5d898c, B3 learned 6c65b470. POI store: l2vast/ds3/out/poi_store/ (689 streams, README with the named gaps); code l2vast/ds3/code/poi/; outputs l2vast/ds3/out/ntz/.
## 0. Verdict in plain words
1. **Nothing passes. 0 PASS of 130,946 cells (127,548 single-POI rule cells, 3,366 combination / time cells, 32 learned-policy cells), x scope pooled + 10 books. No selected cell clears its MDE in both L6M and HOLD; the cumulative reality check (143,584 earlier cells + this program = 274,530) is 1.0 everywhere.** 33 of the 594 PRE u X'-selected single-POI cells (+ 62 combo / time and 1 learned) are CANDIDATE-RECENT (>= 0 in L6M and HOLD on N and per contract, placebo rank >= 0.90, positive in PRE and X'), but all are below their MDE, most fire fewer than 30 times in L6M (18 single-POI cells fire >= 30 times in both L6M and HOLD) and the count is what chance produces: the selected cells average +0.34 / +0.46 pt per signal in PRE / X' (selected on it) and -0.07 / -0.05 in L6M / HOLD (L3M view -0.05); only 43% / 43% are positive in L6M / HOLD.
2. **A POI ahead is not a reason to skip, size down or re-target in this market.** The map (DS3_POI_MAP.md) found no reversal spot distinguishable from noise (best PRE u X' adjusted dP(target) -0.10, z -5.0, against a shuffled-outcome family null whose median best z is -5.1), the first-touch study shows price turning at a POI no more often than at a random level at the same distance, and the rules built on it do not transfer: every rule family is negative on average in L6M, HOLD and L3M (skip -0.21 / -0.17 / -0.17 pt per signal on the market base; re-target -0.15 / -0.10 / -0.07; wait -0.02 / 0.00 / +0.05).
3. **Skipping loses money by construction when the fired signals are not worse than average** (the market base earns about +1.3 to +1.5 pt per signal on N), so the per-signal test is strict; the per-contract number on the kept signals is printed beside it everywhere, and when the two disagree (skip rules show a small positive per-contract delta and a negative per-signal gain) the rule is a lot-weighting effect, not information (CF-A / CF-B lesson: a result is real only if it holds per planned lot, per contract AND on the lock-engine stack).
4. **Re-target / wait / split-behind cells are STRUCTURE** unless they beat the random-level placebo at the same distance distribution; the placebo columns (random fire set with the real distance distribution, and level-permuted among the real fired signals) are printed with every sim cell.
5. **The user's named examples** (section 4 below, every book): skipping PE signals whose target lies beyond an unmitigated 4-h FVG, KB shorts into yesterday's low, SM longs into the weekly high, and the re-target variants: all inside their MDEs and negative per contract in L6M and HOLD except where the cell fires fewer than 10 times.
6. **One pattern is consistent across windows on the per-signal and per-contract units and is reported as a LEAD (forward-watch), not a rule: the HM book into an unmitigated OPPOSING fair value gap on 15m / 1h / 4h within 60 pts** (section 9, post-hoc follow-up of the HM NAMED cell and the HM map entry). HM signals that fire with such a gap between entry and target average -3 to -4 pt per signal while the rest average +2 to +7; skipping them adds +0.65 / +1.01 / +0.97 / +0.89 / +0.59 pt per signal (PRE / X' / HOLD / L6M / L3M, market base N; MDE 1.5-2.9 each, placebo rank 0.96-0.99 in PRE, X', HOLD, L6M; +1.3 to +2.5 pt per contract on the kept signals) and the same rule is NEGATIVE for SM, MA, DN and neutral for the other books, so it is book-specific (the inverse-variance pool of the three independent windows is about +0.74 +- 0.43, z 1.7, before the multiplicity of choosing 1 book of 10 and 1 rule set of 4). **It fails the unit test of the CF lesson**: the exact lock-engine stack delta is -0.5k / +1.1k / +9.1k / +11.5k \$/wk in PRE / X' / HOLD / L6M (MDE 10-17k each; 60% of the L6M delta sits in 3 weeks), so the stack does not see the PRE gain at all. 2026 (49 fires) is flat. Forward test only.

## 1. Accounting by rule family (single-POI cells; gain per signal on basis N in pts, planned-lot unit; selection on PRE u X' only)
Eligible = positive gain in PRE and in X' separately with >= 100 fires on PRE u X'. Selected = top 3 by week-clustered z per (family, scope). Mean columns average the SELECTED cells (594); 'grid' columns are the VIEW-ONLY recent read of EVERY cell of the family (pooled scope, after the look; never used to select). RC p / RW survivors / PBO are over all cells of the family on weekly PRE u X' gains (circular block bootstrap, block 4 weeks, 400 draws); the cumulative Sidak p uses 274,530 cells.

| family (action [base]) | cells | eligible | selected | sel. mean PRE | X' | L6M | HOLD | L3M(view) | share L6M>0 | mean placebo rank L6M | CAND-RECENT | LEAD | grid mean L6M | grid share L6M>0 | eligible cells L6M>0 | RC p | cum. Sidak p | RW survivors | PBO |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 70% now + 30% after trade-through [market] | 5,578 | 610 | 33 | +0.132 | +0.123 | -0.041 | -0.034 | +0.003 | 0.42 | 0.63 | 3 | 11 | -0.050 | 0.20 | 0.33 | 0.99 | 1.00 | 0 | 0.22 |
| re-target, skip if target<20 [market] | 5,578 | 776 | 33 | +0.514 | +0.584 | -0.176 | -0.095 | -0.133 | 0.30 | 0.53 | 0 | 10 | -0.242 | 0.21 | 0.23 | 0.96 | 1.00 | 0 | 0.38 |
| re-target, skip if target<20 [70/30] | 5,578 | 760 | 33 | +0.436 | +0.665 | -0.147 | -0.076 | -0.141 | 0.30 | 0.52 | 1 | 9 | -0.245 | 0.21 | 0.22 | 0.98 | 1.00 | 0 | 0.46 |
| re-target, skip if target<30 [market] | 5,578 | 679 | 33 | +0.468 | +0.606 | -0.148 | -0.108 | -0.151 | 0.39 | 0.56 | 1 | 12 | -0.270 | 0.20 | 0.23 | 0.99 | 1.00 | 0 | 0.38 |
| re-target, skip if target<30 [70/30] | 5,578 | 697 | 33 | +0.438 | +0.638 | -0.145 | -0.119 | -0.110 | 0.42 | 0.58 | 1 | 13 | -0.271 | 0.20 | 0.21 | 1.00 | 1.00 | 0 | 0.46 |
| re-target to POI-2t [market] | 5,578 | 694 | 33 | +0.423 | +0.578 | -0.153 | -0.104 | -0.067 | 0.15 | 0.46 | 0 | 5 | -0.191 | 0.24 | 0.24 | 0.91 | 1.00 | 0 | 0.34 |
| re-target to POI-2t [70/30] | 5,578 | 677 | 33 | +0.416 | +0.591 | -0.193 | -0.108 | -0.087 | 0.15 | 0.46 | 1 | 4 | -0.200 | 0.23 | 0.24 | 0.90 | 1.00 | 0 | 0.40 |
| skip [market] | 12,630 | 1,418 | 33 | +0.502 | +0.668 | -0.213 | -0.171 | -0.171 | 0.36 | 0.51 | 1 | 11 | -0.430 | 0.17 | 0.27 | 0.99 | 1.00 | 0 | 0.38 |
| skip [70/30] | 12,630 | 1,464 | 33 | +0.471 | +0.732 | -0.168 | -0.129 | -0.107 | 0.39 | 0.59 | 2 | 11 | -0.435 | 0.17 | 0.25 | 0.99 | 1.00 | 0 | 0.38 |
| tighten stop beyond POI (risk-matched) [market] | 1,578 | 155 | 33 | +0.134 | +0.362 | +0.016 | +0.016 | +0.007 | 0.55 | 0.63 | 0 | 19 | -0.109 | 0.24 | 0.37 | 0.71 | 1.00 | 0 | 0.36 |
| tighten stop beyond POI (risk-matched) [70/30] | 1,578 | 150 | 33 | +0.133 | +0.294 | -0.014 | -0.008 | +0.000 | 0.48 | 0.62 | 0 | 18 | -0.110 | 0.25 | 0.41 | 0.73 | 1.00 | 0 | 0.45 |
| size 150% (POI behind) [market] | 1,994 | 814 | 33 | +0.426 | +0.369 | +0.214 | +0.172 | +0.091 | 0.82 | 0.55 | 7 | 20 | +0.157 | 0.83 | 0.90 | 0.01 | 1.00 | 0 | 0.81 |
| size 150% (POI behind) [70/30] | 1,994 | 816 | 33 | +0.399 | +0.429 | +0.228 | +0.176 | +0.085 | 0.88 | 0.54 | 4 | 25 | +0.158 | 0.84 | 0.90 | 0.01 | 1.00 | 0 | 0.81 |
| wait for trade-through [market] | 5,578 | 666 | 33 | +0.453 | +0.424 | -0.019 | -0.002 | +0.047 | 0.52 | 0.58 | 6 | 11 | -0.129 | 0.28 | 0.44 | 0.99 | 1.00 | 0 | 0.37 |
| size 50% [market] | 12,630 | 1,418 | 33 | +0.251 | +0.334 | -0.107 | -0.086 | -0.085 | 0.36 | 0.52 | 1 | 11 | -0.215 | 0.17 | 0.27 | 0.99 | 1.00 | 0 | 0.38 |
| size 50% [70/30] | 12,630 | 1,464 | 33 | +0.235 | +0.366 | -0.084 | -0.064 | -0.054 | 0.39 | 0.58 | 2 | 11 | -0.218 | 0.17 | 0.25 | 0.99 | 1.00 | 0 | 0.38 |
| size 67% [market] | 12,630 | 1,418 | 33 | +0.166 | +0.220 | -0.070 | -0.056 | -0.056 | 0.36 | 0.50 | 1 | 11 | -0.142 | 0.17 | 0.27 | 0.99 | 1.00 | 0 | 0.38 |
| size 67% [70/30] | 12,630 | 1,464 | 33 | +0.155 | +0.241 | -0.055 | -0.043 | -0.035 | 0.39 | 0.58 | 2 | 11 | -0.144 | 0.17 | 0.25 | 0.99 | 1.00 | 0 | 0.38 |

Reading: where 'eligible cells L6M>0' is 0.2-0.4 the family has no transfer (a coin would give ~0.5 of a random split of cells with positive total expectation; skip cells need a NEGATIVE-mean fired set to be positive at all). u150 (size 150% when a POI is behind) is positive in 83-90% of cells because the base earns +1.4 pt per signal and scaling any subset up gains; its meaningful columns are the per-contract and the placebo rank (mean 0.54-0.55: no skill beyond scaling).

## 2. The selected cells by family: best 4 by PRE u X' z (pooled scope) and every CANDIDATE-RECENT cell with >= 30 fires in L6M and HOLD
Columns: fires L6M (share of the scope's signals), PRE, X', L3M (view), L6M (MDE = 2.8 clustered SE) = gain per signal on N; HOLD; per contract on the kept signals (rule net / lots - base net / lots) L6M, HOLD; L6M on M / LIVE; placebo rank (random fire set at the same fire rate and strata; sim cells: random fire set with real distances), stack delta $/wk on the exact lock engine (6 books) L6M / HOLD, tier.

### 70% now + 30% after trade-through [market]

| cell | scope | fires L6M | PRE | X' | L3M(view) | L6M (MDE) | HOLD | per contract L6M | per contract HOLD | L6M M/LIVE | placebo rank | stack L6M/HOLD $/wk | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 70% now + 30% after trade-through [market] - AHEAD BKS:sweep:book (unmitigated) within 5pts | ALL | 1947 (20.0%) | +0.054 | +0.009 | +0.034 | +0.020 (0.04) | +0.022 | +0.024 | +0.026 | +0.020/+0.022 | 1.00 | -1174/-773 | CANDIDATE-RECENT |

### re-target, skip if target<20 [market]

| cell | scope | fires L6M | PRE | X' | L3M(view) | L6M (MDE) | HOLD | per contract L6M | per contract HOLD | L6M M/LIVE | placebo rank | stack L6M/HOLD $/wk | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| re-target, skip if target<20 [market] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 64 (0.7%) | +0.103 | +0.150 | -0.128 | -0.052 (0.16) | -0.032 | -0.039 | -0.021 | -0.043/-0.040 | 0.20 | -760/-627 | DEAD |
| re-target, skip if target<20 [market] - AHEAD PIV:cam_L4:rth (unmitigated) within 0.5xATR15 | ALL | 34 (0.3%) | +0.066 | +0.143 | +0.009 | -0.006 (0.09) | -0.015 | +0.002 | -0.009 | -0.001/+0.001 | 0.70 | +2695/+2506 | DEAD |
| re-target, skip if target<20 [market] - AHEAD ARR:BRK:1h (unmitigated) within 1xATR15 | ALL | 153 (1.6%) | +0.078 | +0.312 | -0.128 | -0.011 (0.25) | +0.045 | +0.010 | +0.063 | -0.002/+0.005 | 0.60 | -202/+265 | DEAD |

### re-target, skip if target<20 [70/30]

| cell | scope | fires L6M | PRE | X' | L3M(view) | L6M (MDE) | HOLD | per contract L6M | per contract HOLD | L6M M/LIVE | placebo rank | stack L6M/HOLD $/wk | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| re-target, skip if target<20 [70/30] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 64 (0.7%) | +0.098 | +0.150 | -0.118 | -0.062 (0.14) | -0.041 | -0.048 | -0.029 | -0.051/-0.049 | 0.15 | -1184/-389 | DEAD |
| re-target, skip if target<20 [70/30] - AHEAD PIV:cam_L4:rth (unmitigated) within 0.5xATR15 | ALL | 34 (0.3%) | +0.056 | +0.144 | +0.010 | -0.014 (0.09) | -0.022 | -0.006 | -0.016 | -0.008/-0.007 | 0.55 | +2325/+1881 | DEAD |
| re-target, skip if target<20 [70/30] - AHEAD ARR:BRK:1h (unmitigated) within 1xATR15 | ALL | 153 (1.6%) | +0.067 | +0.296 | -0.135 | -0.030 (0.24) | +0.027 | -0.009 | +0.046 | -0.020/-0.014 | 0.60 | -1758/-569 | DEAD |

### re-target, skip if target<30 [market]

| cell | scope | fires L6M | PRE | X' | L3M(view) | L6M (MDE) | HOLD | per contract L6M | per contract HOLD | L6M M/LIVE | placebo rank | stack L6M/HOLD $/wk | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| re-target, skip if target<30 [market] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 64 (0.7%) | +0.100 | +0.146 | -0.099 | -0.046 (0.16) | -0.026 | -0.028 | -0.012 | -0.032/-0.029 | 0.30 | +189/+203 | DEAD |
| re-target, skip if target<30 [market] - AHEAD PIV:cam_L4:rth (unmitigated) within 0.5xATR15 | ALL | 34 (0.3%) | +0.066 | +0.143 | +0.030 | +0.006 (0.10) | -0.004 | +0.016 | +0.004 | +0.012/+0.014 | 0.90 | +2695/+2506 | LEAD |
| re-target, skip if target<30 [market] - AHEAD PRF:vwap:day (unmitigated) within 10pts | ALL | 197 (2.0%) | +0.144 | +0.138 | +0.103 | -0.002 (0.24) | -0.010 | +0.065 | +0.043 | +0.042/+0.056 | 0.90 | -330/-420 | DEAD |

### re-target, skip if target<30 [70/30]

| cell | scope | fires L6M | PRE | X' | L3M(view) | L6M (MDE) | HOLD | per contract L6M | per contract HOLD | L6M M/LIVE | placebo rank | stack L6M/HOLD $/wk | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| re-target, skip if target<30 [70/30] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 64 (0.7%) | +0.096 | +0.145 | -0.087 | -0.053 (0.14) | -0.033 | -0.035 | -0.018 | -0.039/-0.036 | 0.25 | -1013/-239 | DEAD |
| re-target, skip if target<30 [70/30] - AHEAD PIV:cam_L4:rth (unmitigated) within 0.5xATR15 | ALL | 34 (0.3%) | +0.056 | +0.144 | +0.031 | -0.002 (0.09) | -0.012 | +0.008 | -0.004 | +0.004/+0.006 | 0.60 | +2325/+1881 | DEAD |
| re-target, skip if target<30 [70/30] - AHEAD ARR:BRK:1h (unmitigated) within 15pts | ALL | 45 (0.5%) | +0.048 | +0.202 | -0.053 | +0.020 (0.16) | +0.039 | +0.035 | +0.053 | +0.029/+0.033 | 0.85 | +253/+560 | LEAD |

### re-target to POI-2t [market]

| cell | scope | fires L6M | PRE | X' | L3M(view) | L6M (MDE) | HOLD | per contract L6M | per contract HOLD | L6M M/LIVE | placebo rank | stack L6M/HOLD $/wk | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| re-target to POI-2t [market] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 64 (0.7%) | +0.103 | +0.140 | -0.103 | -0.026 (0.15) | -0.016 | -0.026 | -0.016 | -0.033/-0.031 | 0.35 | -488/+85 | DEAD |
| re-target to POI-2t [market] - AHEAD PIV:cam_L4:rth (unmitigated) within 0.5xATR15 | ALL | 34 (0.3%) | +0.081 | +0.147 | -0.010 | -0.010 (0.09) | -0.015 | -0.010 | -0.015 | -0.013/-0.012 | 0.30 | +2024/+1977 | DEAD |
| re-target to POI-2t [market] - AHEAD PRF:vwap:day (unmitigated) within 5pts | ALL | 73 (0.7%) | +0.062 | +0.136 | +0.062 | +0.013 (0.14) | +0.029 | +0.013 | +0.029 | +0.003/+0.006 | 0.80 | -271/+358 | LEAD |

### re-target to POI-2t [70/30]

| cell | scope | fires L6M | PRE | X' | L3M(view) | L6M (MDE) | HOLD | per contract L6M | per contract HOLD | L6M M/LIVE | placebo rank | stack L6M/HOLD $/wk | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| re-target to POI-2t [70/30] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 64 (0.7%) | +0.095 | +0.134 | -0.098 | -0.037 (0.13) | -0.020 | -0.036 | -0.019 | -0.042/-0.040 | 0.15 | -1381/-457 | DEAD |
| re-target to POI-2t [70/30] - AHEAD PIV:cam_L4:rth (unmitigated) within 0.5xATR15 | ALL | 34 (0.3%) | +0.072 | +0.159 | -0.000 | -0.013 (0.08) | -0.019 | -0.013 | -0.019 | -0.016/-0.015 | 0.35 | +2645/+2222 | DEAD |
| re-target to POI-2t [70/30] - AHEAD PRF:vwap:day (unmitigated) within 5pts | ALL | 73 (0.7%) | +0.053 | +0.133 | +0.062 | +0.012 (0.14) | +0.029 | +0.014 | +0.030 | +0.004/+0.008 | 0.90 | +704/+1207 | LEAD |
| re-target to POI-2t [70/30] - AHEAD ARR:FVG:1h (unmitigated) within 40pts | HM | 56 (6.2%) | +0.410 | +0.867 | +0.638 | +0.322 (1.40) | +0.378 | +0.333 | +0.387 | +0.241/+0.269 | 0.90 | +4429/+3655 | CANDIDATE-RECENT |

### skip [market]

| cell | scope | fires L6M | PRE | X' | L3M(view) | L6M (MDE) | HOLD | per contract L6M | per contract HOLD | L6M M/LIVE | placebo rank | stack L6M/HOLD $/wk | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| skip [market] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 64 (0.7%) | +0.099 | +0.146 | -0.088 | -0.021 (0.16) | -0.007 | +0.001 | +0.010 | -0.006/-0.001 | 0.44 | +582/+439 | DEAD |
| skip [market] - AHEAD PIV:cam_L4:rth (unmitigated) within 0.5xATR15 | ALL | 34 (0.3%) | +0.061 | +0.143 | +0.016 | +0.005 (0.11) | -0.006 | +0.016 | +0.003 | +0.012/+0.014 | 0.67 | +2602/+2424 | LEAD |
| skip [market] - AHEAD PDX:week:H (any) within 10pts | ALL | 83 (0.9%) | +0.122 | +0.095 | +0.028 | +0.011 (0.17) | +0.004 | +0.039 | +0.030 | +0.029/+0.035 | 0.73 | -2483/-2065 | LEAD |

### skip [70/30]

| cell | scope | fires L6M | PRE | X' | L3M(view) | L6M (MDE) | HOLD | per contract L6M | per contract HOLD | L6M M/LIVE | placebo rank | stack L6M/HOLD $/wk | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| skip [70/30] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 64 (0.7%) | +0.097 | +0.145 | -0.074 | -0.027 (0.15) | -0.013 | -0.006 | +0.004 | -0.012/-0.008 | 0.41 | -1013/-349 | DEAD |
| skip [70/30] - AHEAD PDX:week:H (any) within 10pts | ALL | 83 (0.9%) | +0.122 | +0.102 | +0.028 | +0.018 (0.16) | +0.010 | +0.046 | +0.037 | +0.035/+0.041 | 0.78 | -1982/-1865 | LEAD |
| skip [70/30] - AHEAD PIV:cam_L4:rth (unmitigated) within 0.5xATR15 | ALL | 34 (0.3%) | +0.051 | +0.144 | +0.016 | -0.004 (0.10) | -0.014 | +0.008 | -0.005 | +0.004/+0.006 | 0.58 | +1641/+1283 | DEAD |
| skip [70/30] - AHEAD FIB:ret50:15m (any) within 10pts | WT | 81 (4.7%) | +0.253 | +0.444 | +0.039 | +0.234 (0.52) | +0.236 | +0.340 | +0.313 | +0.331/+0.363 | 0.95 | +2284/+2400 | CANDIDATE-RECENT |

### tighten stop beyond POI (risk-matched) [market]

| cell | scope | fires L6M | PRE | X' | L3M(view) | L6M (MDE) | HOLD | per contract L6M | per contract HOLD | L6M M/LIVE | placebo rank | stack L6M/HOLD $/wk | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| tighten stop beyond POI (risk-matched) [market] - BEHIND ARR:FVG_CE:1h (unmitigated) within 1xATR15 | ALL | 539 (5.5%) | +0.033 | +0.063 | +0.032 | +0.032 (0.06) | +0.050 | +0.029 | +0.047 | +0.029/+0.029 | 0.60 | +921/+1576 | LEAD |
| tighten stop beyond POI (risk-matched) [market] - BEHIND PRF:b2:rth (unmitigated) within 0.25xATR15 | ALL | 301 (3.1%) | +0.003 | +0.018 | +0.000 | -0.000 (0.00) | -0.000 | -0.000 | -0.000 | -0.000/-0.000 | 0.70 | -2/-2 | DEAD |
| tighten stop beyond POI (risk-matched) [market] - BEHIND PRF:poc:sw15 (unmitigated) within 15pts | ALL | 176 (1.8%) | +0.028 | +0.044 | +0.015 | -0.012 (0.04) | -0.018 | -0.015 | -0.020 | -0.012/-0.013 | 0.90 | -220/-446 | DEAD |

### tighten stop beyond POI (risk-matched) [70/30]

| cell | scope | fires L6M | PRE | X' | L3M(view) | L6M (MDE) | HOLD | per contract L6M | per contract HOLD | L6M M/LIVE | placebo rank | stack L6M/HOLD $/wk | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| tighten stop beyond POI (risk-matched) [70/30] - BEHIND PRF:b2:rth (unmitigated) within 0.25xATR15 | ALL | 301 (3.1%) | +0.003 | +0.017 | +0.000 | -0.000 (0.00) | -0.000 | -0.000 | -0.000 | -0.000/-0.000 | 0.70 | -2/-3 | DEAD |
| tighten stop beyond POI (risk-matched) [70/30] - BEHIND ARR:FVG_CE:1h (unmitigated) within 1xATR15 | ALL | 539 (5.5%) | +0.033 | +0.064 | +0.033 | +0.033 (0.06) | +0.051 | +0.031 | +0.048 | +0.031/+0.031 | 0.85 | +776/+1230 | LEAD |
| tighten stop beyond POI (risk-matched) [70/30] - BEHIND PRF:poc:sw15 (unmitigated) within 15pts | ALL | 176 (1.8%) | +0.029 | +0.039 | +0.012 | -0.014 (0.04) | -0.020 | -0.017 | -0.023 | -0.014/-0.015 | 0.90 | -229/-460 | DEAD |

### size 150% (POI behind) [market]

| cell | scope | fires L6M | PRE | X' | L3M(view) | L6M (MDE) | HOLD | per contract L6M | per contract HOLD | L6M M/LIVE | placebo rank | stack L6M/HOLD $/wk | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| size 150% (POI behind) [market] - BEHIND ARR:FVG:2m (unmitigated) within 0.25xATR15 | ALL | 691 (7.1%) | +0.132 | +0.091 | +0.103 | +0.051 (0.23) | +0.037 | -0.062 | -0.052 | -0.027/-0.050 | 0.23 | +2740/+2283 | LEAD |
| size 150% (POI behind) [market] - BEHIND RND:x100:raw (unmitigated) within 2pts | ALL | 210 (2.2%) | +0.085 | +0.051 | +0.021 | +0.033 (0.13) | +0.021 | -0.002 | -0.007 | +0.009/+0.002 | 0.56 | +585/+1441 | LEAD |
| size 150% (POI behind) [market] - BEHIND FIB:ret62:5m (unmitigated) within 20pts | ALL | 449 (4.6%) | +0.077 | +0.215 | +0.123 | +0.123 (0.19) | +0.095 | +0.047 | +0.034 | +0.069/+0.055 | 0.77 | -92/-155 | LEAD |
| size 150% (POI behind) [market] - BEHIND ARR:BRK_CE:3m (unmitigated) within 20pts | SM | 44 (14.0%) | +0.995 | +0.844 | +0.684 | +1.297 (1.83) | +1.029 | +1.057 | +0.707 | +1.102/+1.067 | 0.95 | +1789/+1654 | CANDIDATE-RECENT |
| size 150% (POI behind) [market] - BEHIND SWG:f7L:1m (unmitigated) within 5pts | ST | 61 (4.9%) | +0.510 | +0.048 | +0.489 | +0.440 (0.51) | +0.427 | +0.337 | +0.342 | +0.372/+0.360 | 0.95 | +2069/+1981 | CANDIDATE-RECENT |
| size 150% (POI behind) [market] - BEHIND SWG:f3L:2m (unmitigated) within 5pts | ST | 71 (5.7%) | +0.487 | +0.054 | +0.484 | +0.485 (0.57) | +0.511 | +0.364 | +0.410 | +0.408/+0.393 | 0.95 | +2106/+2186 | CANDIDATE-RECENT |

### size 150% (POI behind) [70/30]

| cell | scope | fires L6M | PRE | X' | L3M(view) | L6M (MDE) | HOLD | per contract L6M | per contract HOLD | L6M M/LIVE | placebo rank | stack L6M/HOLD $/wk | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| size 150% (POI behind) [70/30] - BEHIND EQL:EQL_rel:1m (unmitigated) within 10pts | ALL | 502 (5.2%) | +0.161 | +0.198 | -0.021 | +0.014 (0.18) | +0.029 | -0.068 | -0.042 | -0.042/-0.059 | 0.10 | -1970/-126 | LEAD |
| size 150% (POI behind) [70/30] - BEHIND FIB:ret62:5m (unmitigated) within 20pts | ALL | 449 (4.6%) | +0.075 | +0.220 | +0.140 | +0.139 (0.19) | +0.116 | +0.063 | +0.054 | +0.085/+0.072 | 0.82 | +2896/+2696 | LEAD |
| size 150% (POI behind) [70/30] - BEHIND PRF:b2:day (unmitigated) within 1xATR15 | ALL | 2671 (27.4%) | +0.388 | +0.352 | +0.565 | +0.623 (0.72) | +0.544 | +0.155 | +0.166 | +0.316/+0.232 | 0.91 | +11038/+10112 | CANDIDATE-RECENT |
| size 150% (POI behind) [70/30] - BEHIND ARR:BRK_CE:3m (unmitigated) within 20pts | SM | 44 (14.0%) | +0.994 | +0.864 | +0.608 | +1.255 (1.80) | +0.998 | +0.959 | +0.611 | +1.063/+1.028 | 0.93 | +1738/+1476 | CANDIDATE-RECENT |

### wait for trade-through [market]

| cell | scope | fires L6M | PRE | X' | L3M(view) | L6M (MDE) | HOLD | per contract L6M | per contract HOLD | L6M M/LIVE | placebo rank | stack L6M/HOLD $/wk | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| wait for trade-through [market] - AHEAD PRF:hvn1:sw15 (unmitigated) within 40pts | ALL | 391 (4.0%) | +0.202 | +0.133 | -0.114 | -0.014 (0.33) | -0.040 | +0.026 | -0.008 | +0.007/+0.018 | 0.80 | -3872/-5586 | DEAD |
| wait for trade-through [market] - AHEAD BKS:sweep:book (unmitigated) within 2xATR15 | ALL | 1947 (20.0%) | +0.215 | +0.018 | +0.168 | +0.128 (0.18) | +0.122 | +0.144 | +0.135 | +0.132/+0.138 | 1.00 | +2399/+1538 | CANDIDATE-RECENT |
| wait for trade-through [market] - AHEAD MAS:ich_kijun:4h (unmitigated) within 2xATR15 | DN | 31 (4.4%) | +0.559 | +0.352 | +0.876 | +0.560 (1.26) | +0.782 | +0.698 | +0.917 | +0.578/+0.601 | 0.95 | / | CANDIDATE-RECENT |
| wait for trade-through [market] - AHEAD BKS:sweep:book (unmitigated) within 1xATR15 | WT | 324 (19.0%) | +0.252 | +0.135 | -0.005 | +0.087 (0.17) | +0.082 | +0.095 | +0.088 | +0.090/+0.095 | 0.95 | -1204/-1075 | CANDIDATE-RECENT |

### size 50% [market]

| cell | scope | fires L6M | PRE | X' | L3M(view) | L6M (MDE) | HOLD | per contract L6M | per contract HOLD | L6M M/LIVE | placebo rank | stack L6M/HOLD $/wk | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| size 50% [market] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 64 (0.7%) | +0.050 | +0.073 | -0.044 | -0.010 (0.08) | -0.003 | +0.000 | +0.005 | -0.003/-0.001 | 0.49 | -1309/-911 | DEAD |
| size 50% [market] - AHEAD PIV:cam_L4:rth (unmitigated) within 0.5xATR15 | ALL | 34 (0.3%) | +0.031 | +0.072 | +0.008 | +0.002 (0.05) | -0.003 | +0.008 | +0.002 | +0.006/+0.007 | 0.73 | +717/+848 | LEAD |
| size 50% [market] - AHEAD PDX:week:H (any) within 10pts | ALL | 83 (0.9%) | +0.061 | +0.047 | +0.014 | +0.005 (0.09) | +0.002 | +0.019 | +0.015 | +0.015/+0.017 | 0.74 | -1673/-1218 | LEAD |

### size 50% [70/30]

| cell | scope | fires L6M | PRE | X' | L3M(view) | L6M (MDE) | HOLD | per contract L6M | per contract HOLD | L6M M/LIVE | placebo rank | stack L6M/HOLD $/wk | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| size 50% [70/30] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 64 (0.7%) | +0.048 | +0.073 | -0.037 | -0.013 (0.08) | -0.006 | -0.003 | +0.002 | -0.006/-0.004 | 0.44 | -2660/-1890 | DEAD |
| size 50% [70/30] - AHEAD PDX:week:H (any) within 10pts | ALL | 83 (0.9%) | +0.061 | +0.051 | +0.014 | +0.009 (0.08) | +0.005 | +0.023 | +0.018 | +0.018/+0.021 | 0.78 | -661/-548 | LEAD |
| size 50% [70/30] - AHEAD PIV:cam_L4:rth (unmitigated) within 0.5xATR15 | ALL | 34 (0.3%) | +0.026 | +0.072 | +0.008 | -0.002 (0.05) | -0.007 | +0.004 | -0.002 | +0.002/+0.003 | 0.66 | +1196/+970 | DEAD |
| size 50% [70/30] - AHEAD FIB:ret50:15m (any) within 10pts | WT | 81 (4.7%) | +0.126 | +0.222 | +0.020 | +0.117 (0.26) | +0.118 | +0.166 | +0.153 | +0.166/+0.182 | 0.96 | +1474/+1898 | CANDIDATE-RECENT |

### size 67% [market]

| cell | scope | fires L6M | PRE | X' | L3M(view) | L6M (MDE) | HOLD | per contract L6M | per contract HOLD | L6M M/LIVE | placebo rank | stack L6M/HOLD $/wk | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| size 67% [market] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 64 (0.7%) | +0.033 | +0.048 | -0.029 | -0.007 (0.05) | -0.002 | +0.000 | +0.003 | -0.002/-0.000 | 0.48 | -245/-126 | DEAD |
| size 67% [market] - AHEAD PIV:cam_L4:rth (unmitigated) within 0.5xATR15 | ALL | 34 (0.3%) | +0.020 | +0.047 | +0.005 | +0.001 (0.04) | -0.002 | +0.005 | +0.001 | +0.004/+0.005 | 0.69 | +92/+325 | LEAD |
| size 67% [market] - AHEAD PDX:week:H (any) within 10pts | ALL | 83 (0.9%) | +0.040 | +0.031 | +0.009 | +0.004 (0.06) | +0.001 | +0.013 | +0.010 | +0.010/+0.011 | 0.67 | -1101/-830 | LEAD |

### size 67% [70/30]

| cell | scope | fires L6M | PRE | X' | L3M(view) | L6M (MDE) | HOLD | per contract L6M | per contract HOLD | L6M M/LIVE | placebo rank | stack L6M/HOLD $/wk | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| size 67% [70/30] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 64 (0.7%) | +0.032 | +0.048 | -0.024 | -0.009 (0.05) | -0.004 | -0.002 | +0.001 | -0.004/-0.003 | 0.41 | -1453/-1042 | DEAD |
| size 67% [70/30] - AHEAD PDX:week:H (any) within 10pts | ALL | 83 (0.9%) | +0.040 | +0.034 | +0.009 | +0.006 (0.05) | +0.003 | +0.015 | +0.012 | +0.012/+0.014 | 0.76 | -1256/-1185 | LEAD |
| size 67% [70/30] - AHEAD PIV:cam_L4:rth (unmitigated) within 0.5xATR15 | ALL | 34 (0.3%) | +0.017 | +0.047 | +0.005 | -0.001 (0.03) | -0.005 | +0.002 | -0.002 | +0.001/+0.002 | 0.65 | +658/+525 | DEAD |
| size 67% [70/30] - AHEAD FIB:ret50:15m (any) within 10pts | WT | 81 (4.7%) | +0.083 | +0.147 | +0.013 | +0.077 (0.17) | +0.078 | +0.109 | +0.100 | +0.109/+0.120 | 0.95 | +495/+1072 | CANDIDATE-RECENT |

## 3. Per book (scope = that book only; the best PRE u X' cell of each family within the book, and its recent numbers; one verdict per book is in DS3_NO_TRADE_FINAL.md)

| cell | scope | fires L6M | PRE | X' | L3M(view) | L6M (MDE) | HOLD | per contract L6M | per contract HOLD | L6M M/LIVE | placebo rank | stack L6M/HOLD $/wk | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| wait for trade-through [market] - AHEAD FIB:ret62:15m (unmitigated) within 60pts | ST | 52 (4.1%) | +0.651 | +0.305 | +0.039 | +0.012 (0.64) | -0.028 | +0.079 | +0.023 | +0.042/+0.056 | 0.50 | -3511/-3163 | LEAD |
| 70% now + 30% after trade-through [market] - AHEAD FIB:ret62:15m (unmitigated) within 60pts | ST | 52 (4.1%) | +0.150 | +0.115 | -0.001 | -0.036 (0.19) | -0.018 | -0.016 | -0.003 | -0.028/-0.023 | 0.35 | -1406/-1525 | DEAD |
| tighten stop beyond POI (risk-matched) [market] - BEHIND PRF:b2:rth (unmitigated) within 1xATR15 | ST | 190 (15.1%) | +0.065 | +0.180 | +0.000 | +0.038 (0.11) | -0.054 | +0.035 | -0.058 | +0.035/+0.035 | 0.45 | +317/+77 | LEAD |
| size 150% (POI behind) [market] - BEHIND SWG:f7L:1m (unmitigated) within 5pts | ST | 61 (4.9%) | +0.510 | +0.048 | +0.489 | +0.440 (0.51) | +0.427 | +0.337 | +0.342 | +0.372/+0.360 | 0.95 | +2069/+1981 | CANDIDATE-RECENT |
| tighten stop beyond POI (risk-matched) [70/30] - BEHIND PRF:b2:rth (unmitigated) within 1xATR15 | ST | 190 (15.1%) | +0.070 | +0.189 | +0.000 | +0.040 (0.11) | -0.053 | +0.037 | -0.058 | +0.037/+0.037 | 0.25 | +332/+80 | LEAD |
| size 50% [70/30] - AHEAD FIB:OTEzone:15m (unmitigated) within 60pts | ST | 46 (3.7%) | +0.295 | +0.301 | +0.186 | -0.078 (0.49) | -0.026 | +0.002 | +0.038 | -0.036/-0.024 | 0.51 | -2386/-2327 | DEAD |
| size 150% (POI behind) [70/30] - BEHIND ARR:iplFVG:15s (unmitigated) within 0.25xATR15 | HM | 102 (11.2%) | +0.630 | +0.313 | -0.428 | +0.014 (0.78) | +0.069 | -0.218 | -0.114 | -0.097/-0.135 | 0.23 | +666/+1481 | LEAD |
| size 150% (POI behind) [market] - BEHIND ARR:OB_CE:30m (unmitigated) within 1xATR15 | HM | 68 (7.5%) | +0.454 | +0.546 | -0.342 | +0.186 (0.69) | +0.233 | +0.008 | +0.093 | +0.102/+0.079 | 0.58 | -1895/-1683 | LEAD |
| re-target, skip if target<20 [market] - AHEAD PRF:b1:rth (unmitigated) within 0.5xATR15 | HM | 27 (3.0%) | +0.634 | +0.161 | -0.385 | -0.303 (0.65) | -0.160 | -0.219 | -0.078 | -0.275/-0.266 | 0.40 | -228/+116 | DEAD |
| wait for trade-through [market] - AHEAD ARR:BRK:1h (unmitigated) within 1xATR15 | HM | 13 (1.4%) | +0.428 | +0.052 | +0.205 | -0.007 (0.57) | -0.045 | +0.009 | -0.034 | -0.002/+0.001 | 0.50 | -2034/-1862 | DEAD |
| re-target, skip if target<30 [market] - AHEAD PRF:b1:rth (unmitigated) within 0.5xATR15 | HM | 27 (3.0%) | +0.632 | +0.161 | -0.356 | -0.246 (0.74) | -0.109 | -0.134 | -0.007 | -0.204/-0.191 | 0.30 | +67/+374 | DEAD |
| re-target, skip if target<20 [70/30] - AHEAD PRF:b1:rth (unmitigated) within 0.5xATR15 | HM | 27 (3.0%) | +0.575 | +0.186 | -0.372 | -0.299 (0.65) | -0.159 | -0.222 | -0.083 | -0.272/-0.262 | 0.45 | +126/+419 | DEAD |
| tighten stop beyond POI (risk-matched) [market] - BEHIND RND:x50:raw (unmitigated) within 10pts | WT | 349 (20.5%) | +0.090 | +0.026 | -0.147 | -0.049 (0.19) | -0.074 | -0.059 | -0.081 | -0.054/-0.060 | 1.00 | -497/-370 | DEAD |
| tighten stop beyond POI (risk-matched) [70/30] - BEHIND RND:x50:raw (unmitigated) within 10pts | WT | 349 (20.5%) | +0.092 | +0.021 | -0.153 | -0.053 (0.19) | -0.079 | -0.063 | -0.086 | -0.057/-0.064 | 0.95 | -297/-209 | DEAD |
| wait for trade-through [market] - AHEAD BKS:sweep:book (unmitigated) within 2xATR15 | WT | 324 (19.0%) | +0.252 | +0.135 | -0.005 | +0.087 (0.17) | +0.082 | +0.095 | +0.088 | +0.090/+0.095 | 0.90 | -1204/-1075 | CANDIDATE-RECENT |
| re-target, skip if target<30 [market] - AHEAD FIB:ote705_up:15m (unmitigated) within 1xATR15 | WT | 68 (4.0%) | +0.352 | +0.449 | -0.143 | +0.019 (0.41) | +0.080 | +0.089 | +0.133 | +0.108/+0.131 | 0.70 | -1142/-881 | LEAD |
| size 50% [market] - AHEAD FIB:ote705_up:15m (unmitigated) within 20pts | WT | 48 (2.8%) | +0.143 | +0.159 | -0.045 | +0.020 (0.21) | +0.055 | +0.045 | +0.075 | +0.053/+0.062 | 0.75 | -836/-789 | LEAD |
| size 67% [market] - AHEAD FIB:ote705_up:15m (unmitigated) within 20pts | WT | 48 (2.8%) | +0.095 | +0.105 | -0.030 | +0.013 (0.14) | +0.037 | +0.030 | +0.049 | +0.035/+0.041 | 0.73 | -235/-7 | LEAD |
| size 150% (POI behind) [market] - BEHIND EQL:EQH_tight:5m (unmitigated) within 1xATR15 | KB | 28 (2.2%) | +0.137 | +0.403 | +0.160 | +0.267 (0.43) | +0.237 | +0.246 | +0.222 | +0.235/+0.231 | 0.97 | +1421/+935 | CANDIDATE-RECENT |
| size 150% (POI behind) [70/30] - BEHIND EQL:EQH_tight:5m (unmitigated) within 1xATR15 | KB | 28 (2.2%) | +0.140 | +0.377 | +0.152 | +0.255 (0.43) | +0.226 | +0.238 | +0.215 | +0.224/+0.219 | 0.99 | -116/-409 | CANDIDATE-RECENT |
| tighten stop beyond POI (risk-matched) [market] - BEHIND ARR:FVG_CE:10m (unmitigated) within 0.25xATR15 | KB | 46 (3.7%) | +0.074 | +0.321 | -0.167 | -0.075 (0.26) | -0.069 | -0.079 | -0.071 | -0.072/-0.077 | 0.00 | -134/-117 | DEAD |
| tighten stop beyond POI (risk-matched) [70/30] - BEHIND ARR:FVG_CE:10m (unmitigated) within 0.25xATR15 | KB | 46 (3.7%) | +0.070 | +0.344 | -0.169 | -0.077 (0.27) | -0.070 | -0.080 | -0.072 | -0.073/-0.078 | 0.05 | -135/-118 | DEAD |
| wait for trade-through [market] - AHEAD ORB:H:5m (unmitigated) within 1xATR15 | KB | 15 (1.2%) | +0.181 | +0.219 | +0.400 | +0.112 (0.41) | -0.004 | +0.119 | -0.000 | +0.116/+0.120 | 0.75 | +175/+153 | LEAD |
| skip [70/30] - AHEAD FIB:ret62:15m (unmitigated) within 10pts | KB | 27 (2.1%) | +0.162 | +1.091 | +0.423 | +0.248 (0.69) | +0.260 | +0.283 | +0.286 | +0.285/+0.303 | 0.89 | +2095/+2331 | LEAD |
| tighten stop beyond POI (risk-matched) [market] - BEHIND ARR:FVG_CE:30m (unmitigated) within 15pts | SM | 14 (4.5%) | +0.325 | +1.064 | +0.203 | +0.107 (0.30) | +0.093 | +0.103 | +0.087 | +0.100/+0.100 | 0.75 | +165/+145 | LEAD |
| tighten stop beyond POI (risk-matched) [70/30] - BEHIND ARR:FVG_CE:30m (unmitigated) within 15pts | SM | 14 (4.5%) | +0.336 | +1.056 | +0.142 | +0.075 (0.21) | +0.065 | +0.071 | +0.060 | +0.070/+0.070 | 0.85 | +116/+101 | LEAD |
| size 150% (POI behind) [70/30] - BEHIND FIB:pd50:15m (unmitigated) within 10pts | SM | 8 (2.5%) | +0.256 | +0.809 | -0.059 | -0.228 (0.83) | -0.197 | -0.263 | -0.244 | -0.246/-0.258 | 0.20 | -246/-216 | DEAD |
| size 150% (POI behind) [market] - BEHIND FIB:pd50:15m (unmitigated) within 10pts | SM | 8 (2.5%) | +0.259 | +0.800 | -0.004 | -0.202 (0.84) | -0.175 | -0.229 | -0.213 | -0.222/-0.234 | 0.29 | -369/-323 | DEAD |
| re-target, skip if target<30 [70/30] - AHEAD EQL:EQH_tight:1m (unmitigated) within 0.5xATR15 | SM | 17 (5.4%) | +0.847 | +1.825 | -0.314 | -0.976 (2.07) | -1.124 | -0.841 | -0.904 | -0.839/-0.816 | 0.30 | +660/-123 | DEAD |
| re-target, skip if target<30 [market] - AHEAD EQL:EQH_tight:1m (unmitigated) within 0.5xATR15 | SM | 17 (5.4%) | +0.831 | +1.798 | -0.283 | -0.935 (2.05) | -1.134 | -0.854 | -0.976 | -0.801/-0.778 | 0.15 | +678/-178 | DEAD |
| wait for trade-through [market] - AHEAD PRF:lvn0:sw15 (unmitigated) within 60pts | PE | 63 (5.3%) | +0.667 | +0.316 | -0.094 | -0.291 (0.81) | -0.305 | -0.286 | -0.297 | -0.260/-0.249 | 0.20 | -1949/-2013 | DEAD |
| skip [market] - AHEAD PRF:hvn1:sw15 (any) within 40pts | PE | 94 (7.9%) | +0.743 | +0.570 | -0.252 | -0.225 (1.56) | -0.171 | -0.187 | -0.115 | -0.062/-0.012 | 0.33 | -1211/-1213 | DEAD |
| size 50% [market] - AHEAD PRF:hvn1:sw15 (any) within 40pts | PE | 94 (7.9%) | +0.371 | +0.285 | -0.126 | -0.112 (0.78) | -0.085 | -0.090 | -0.055 | -0.031/-0.006 | 0.39 | -2648/-2532 | DEAD |
| size 67% [market] - AHEAD PRF:hvn1:sw15 (any) within 40pts | PE | 94 (7.9%) | +0.245 | +0.188 | -0.083 | -0.074 (0.51) | -0.056 | -0.058 | -0.036 | -0.021/-0.004 | 0.32 | -187/-378 | DEAD |
| size 50% [70/30] - AHEAD PRF:hvn1:sw15 (any) within 40pts | PE | 94 (7.9%) | +0.354 | +0.316 | -0.109 | -0.098 (0.78) | -0.074 | -0.069 | -0.039 | -0.018/+0.008 | 0.41 | -1773/-1376 | DEAD |
| skip [70/30] - AHEAD PRF:hvn1:sw15 (any) within 40pts | PE | 94 (7.9%) | +0.708 | +0.632 | -0.218 | -0.196 (1.56) | -0.149 | -0.143 | -0.081 | -0.036/+0.016 | 0.37 | -2153/-1656 | DEAD |
| re-target, skip if target<20 [market] - AHEAD ARR:iFVG_CE:5m (unmitigated) within 30pts | PB | 89 (10.3%) | +1.208 | +1.429 | -0.687 | -0.724 (1.30) | -0.549 | -0.233 | -0.125 | -0.578/-0.528 | 0.65 | / | DEAD |
| re-target, skip if target<20 [70/30] - AHEAD ARR:iFVG_CE:5m (unmitigated) within 30pts | PB | 89 (10.3%) | +1.253 | +1.263 | -0.536 | -0.599 (1.32) | -0.434 | -0.051 | +0.047 | -0.460/-0.408 | 0.70 | / | DEAD |
| tighten stop beyond POI (risk-matched) [market] - BEHIND ARR:iFVG_CE:10m (unmitigated) within 20pts | PB | 19 (2.2%) | +0.260 | +0.595 | -0.224 | -0.056 (0.62) | +0.046 | -0.122 | -0.021 | -0.056/-0.070 | 0.70 | / | DEAD |
| tighten stop beyond POI (risk-matched) [70/30] - BEHIND ARR:iFVG_CE:10m (unmitigated) within 20pts | PB | 19 (2.2%) | +0.249 | +0.572 | -0.221 | -0.075 (0.61) | +0.010 | -0.153 | -0.067 | -0.074/-0.090 | 0.90 | / | DEAD |
| wait for trade-through [market] - AHEAD FIB:ext200:5m (unmitigated) within 1xATR15 | PB | 17 (2.0%) | +0.513 | +0.493 | -0.479 | -0.223 (1.10) | -0.281 | -0.175 | -0.243 | -0.208/-0.206 | 0.25 | / | DEAD |
| size 67% [market] - AHEAD ARR:iFVG_CE:5m (unmitigated) within 30pts | PB | 89 (10.3%) | +0.371 | +0.517 | -0.271 | -0.281 (0.43) | -0.204 | -0.046 | +0.005 | -0.202/-0.182 | 0.68 | / | DEAD |
| tighten stop beyond POI (risk-matched) [70/30] - BEHIND ARR:iFVG_CE:30m (unmitigated) within 15pts | DN | 22 (3.1%) | +0.155 | +0.128 | +0.000 | +0.000 (0.00) | +0.081 | +0.000 | +0.075 | +0.000/+0.000 | 0.65 | / | LEAD |
| size 150% (POI behind) [market] - BEHIND SWG:f3L:1m (unmitigated) within 5pts | DN | 58 (8.3%) | +0.866 | +0.008 | +0.372 | +0.187 (0.94) | -0.071 | -0.069 | -0.280 | +0.093/+0.066 | 0.21 | / | LEAD |
| tighten stop beyond POI (risk-matched) [market] - BEHIND ARR:iFVG_CE:30m (unmitigated) within 15pts | DN | 22 (3.1%) | +0.155 | +0.170 | +0.000 | +0.000 (0.00) | +0.076 | +0.000 | +0.068 | +0.000/+0.000 | 0.60 | / | LEAD |
| size 150% (POI behind) [70/30] - BEHIND ARR:FVG_CE:10m (unmitigated) within 5pts | DN | 16 (2.3%) | +0.341 | +0.284 | +0.455 | +0.247 (0.54) | +0.182 | +0.183 | +0.135 | +0.214/+0.208 | 0.80 | / | LEAD |
| size 50% [70/30] - AHEAD PRF:lvn1:week (any) within 15pts | DN | 12 (1.7%) | +0.212 | +0.436 | +0.267 | +0.089 (0.35) | +0.041 | +0.136 | +0.076 | +0.102/+0.109 | 0.83 | / | LEAD |
| skip [70/30] - AHEAD PRF:lvn1:week (any) within 15pts | DN | 12 (1.7%) | +0.425 | +0.871 | +0.534 | +0.178 (0.69) | +0.082 | +0.275 | +0.153 | +0.205/+0.217 | 0.84 | / | LEAD |
| size 150% (POI behind) [market] - BEHIND WYK:tr_bottom:15m (unmitigated) within 20pts | MV | 15 (1.3%) | +0.288 | +0.365 | +0.042 | +0.129 (0.33) | +0.091 | +0.113 | +0.078 | +0.110/+0.107 | 0.66 | / | LEAD |
| size 150% (POI behind) [70/30] - BEHIND WYK:tr_bottom:15m (unmitigated) within 20pts | MV | 15 (1.3%) | +0.273 | +0.335 | +0.046 | +0.133 (0.33) | +0.095 | +0.116 | +0.082 | +0.114/+0.111 | 0.68 | / | LEAD |
| tighten stop beyond POI (risk-matched) [market] - BEHIND PRF:b2:week (unmitigated) within 1xATR15 | MV | 133 (11.8%) | +0.068 | +0.335 | +0.000 | +0.052 (0.15) | +0.047 | +0.048 | +0.045 | +0.048/+0.047 | 0.75 | / | LEAD |
| tighten stop beyond POI (risk-matched) [70/30] - BEHIND PRF:b2:week (unmitigated) within 1xATR15 | MV | 133 (11.8%) | +0.071 | +0.335 | +0.000 | +0.056 (0.16) | +0.051 | +0.052 | +0.048 | +0.052/+0.051 | 0.75 | / | LEAD |
| wait for trade-through [market] - AHEAD FIB:ote62_up:15m (unmitigated) within 20pts | MV | 30 (2.7%) | +0.210 | +0.348 | +0.461 | +0.143 (0.52) | +0.266 | +0.158 | +0.280 | +0.147/+0.153 | 0.70 | / | LEAD |
| re-target, skip if target<20 [market] - AHEAD ARR:BRK:1h (unmitigated) within 1xATR15 | MV | 21 (1.9%) | +0.139 | +0.855 | -0.084 | +0.188 (0.58) | +0.152 | +0.207 | +0.168 | +0.191/+0.201 | 1.00 | / | LEAD |
| wait for trade-through [market] - AHEAD ARR:iFVG_CE:2m (unmitigated) within 10pts | MA | 41 (10.1%) | +0.480 | +0.992 | +0.383 | +0.616 (0.90) | +0.602 | +0.707 | +0.679 | +0.616/+0.633 | 0.95 | / | LEAD |
| size 150% (POI behind) [market] - BEHIND ARR:iFVG_CE:1m (unmitigated) within 2pts | MA | 3 (0.7%) | +0.303 | +0.479 | -0.003 | +0.072 (0.36) | +0.061 | +0.046 | +0.044 | +0.061/+0.059 | 0.65 | / | LEAD |
| size 150% (POI behind) [70/30] - BEHIND ARR:iFVG_CE:1m (unmitigated) within 2pts | MA | 3 (0.7%) | +0.304 | +0.473 | -0.002 | +0.074 (0.36) | +0.063 | +0.050 | +0.048 | +0.063/+0.061 | 0.56 | / | LEAD |
| re-target to POI-2t [market] - AHEAD ARR:BRK:1h (unmitigated) within 2xATR15 | MA | 12 (2.9%) | +0.712 | +1.044 | -0.370 | -0.229 (1.11) | +0.050 | -0.229 | +0.050 | -0.250/-0.243 | 0.40 | / | DEAD |
| tighten stop beyond POI (risk-matched) [market] - BEHIND ARR:FVG_CE:30m (unmitigated) within 10pts | MA | 8 (2.0%) | +0.171 | +0.457 | +0.000 | +0.200 (0.43) | +0.218 | +0.177 | +0.167 | +0.186/+0.186 | 0.70 | / | LEAD |
| re-target, skip if target<30 [market] - AHEAD ARR:BRK:1h (unmitigated) within 30pts | MA | 7 (1.7%) | +0.865 | +0.771 | -0.260 | -0.433 (0.90) | -0.113 | -0.322 | -0.011 | -0.382/-0.374 | 0.30 | / | DEAD |

## 4. The user's named examples, every book (NAMED cells, evaluated regardless of selection; D = any POI between entry and target = within 60 pts; unmitigated; scope = that book's signals, both sides)
kept share = share of the book's signals NOT touched by the rule; per contract = rule net per lot minus base net per lot on N, week-block bootstrap 95% CI and MDE (2.8 SD of the bootstrap) in L6M; gain per signal = planned-lot unit, MDE beside. Stack = exact lock engine, \$/wk, L6M (MDE of the weekly delta) - engine books only.

### skip [market]

| book | POI ahead | kept share L6M | fires L6M | per contract L6M [95% CI] (MDE) | gain per signal L6M (MDE) | per contract HOLD | per contract 2026 | L3M(view) | fired mean (base) / kept mean L6M | stack L6M (MDE) |
|--|--|--|--|--|--|--|--|--|--|--|
| ST | ARR:FVG:4h | 94.9% | 64 | +0.596 [-0.087, +1.409] (1.05) | +0.367 (0.86) | +0.565 | -0.728 | -0.065 | -7.20 / +4.49 | +3184 (12166) |
| HM | ARR:FVG:4h | 92.5% | 68 | +0.945 [-0.046, +2.188] (1.64) | +0.520 (1.20) | +0.564 | +0.700 | +0.798 | -6.95 / +5.68 | +10318 (12318) |
| WT | ARR:FVG:4h | 97.0% | 51 | +0.131 [-0.123, +0.412] (0.39) | +0.074 (0.38) | +0.109 | +0.078 | -0.020 | -2.46 / +1.91 | -1135 (5148) |
| KB | ARR:FVG:4h | 94.3% | 72 | -0.434 [-1.025, +0.231] (0.89) | -0.504 (0.84) | -0.516 | -1.529 | -0.720 | +8.80 / +1.22 | +84 (8095) |
| SM | ARR:FVG:4h | 86.3% | 43 | +0.925 [-1.429, +3.563] (3.62) | +0.476 (3.37) | +0.538 | +2.530 | +2.293 | -3.47 / +3.28 | +731 (5340) |
| PE | ARR:FVG:4h | 95.1% | 58 | -0.184 [-0.626, +0.349] (0.73) | -0.207 (0.75) | -0.298 | +0.090 | -0.034 | +4.27 / +0.48 | -1567 (5191) |
| PB | ARR:FVG:4h | 97.5% | 22 | +0.632 [+0.013, +1.373] (0.99) | +0.438 (0.89) | +0.818 | +1.845 | +0.925 | -17.25 / +7.61 |  (nan) |
| DN | ARR:FVG:4h | 92.3% | 54 | -0.449 [-1.245, +0.421] (1.22) | -0.895 (1.26) | -0.618 | -1.853 | -1.130 | +11.62 / +5.79 |  (nan) |
| MV | ARR:FVG:4h | 93.3% | 76 | +0.103 [-0.896, +1.233] (1.53) | -0.057 (1.35) | -0.156 | -1.086 | -0.717 | +0.85 / +2.38 |  (nan) |
| MA | ARR:FVG:4h | 87.2% | 52 | +0.420 [-1.415, +2.215] (2.62) | -0.499 (2.58) | +0.929 | -3.287 | -1.049 | +3.91 / +7.19 |  (nan) |
| ST | PDX:day:L | 96.6% | 43 | -0.004 [-0.583, +0.792] (0.97) | -0.137 (0.86) | +0.002 | -0.019 | -0.328 | +4.00 / +3.89 | -5992 (10069) |
| HM | PDX:day:L | 96.0% | 36 | -0.087 [-0.795, +0.587] (0.96) | -0.271 (0.98) | -0.100 | -0.669 | +0.132 | +6.84 / +4.65 | -3411 (7047) |
| WT | PDX:day:L | 99.1% | 16 | -0.064 [-0.233, +0.121] (0.25) | -0.080 (0.25) | -0.039 | +0.000 | -0.085 | +8.58 / +1.72 | -136 (3326) |
| KB | PDX:day:L | 97.1% | 36 | -0.153 [-0.692, +0.408] (0.79) | -0.196 (0.81) | -0.123 | -0.124 | -0.027 | +6.84 / +1.50 | +1022 (3960) |
| SM | PDX:day:L | 99.0% | 3 | +0.224 [-0.425, +0.897] (1.00) | +0.200 (0.92) | +0.231 | +0.000 | +0.000 | -20.92 / +2.58 | +324 (1942) |
| PE | PDX:day:L | 96.6% | 40 | -0.475 [-1.000, +0.120] (0.85) | -0.482 (0.82) | -0.391 | -0.323 | -0.568 | +14.38 / +0.19 | -677 (5615) |
| PB | PDX:day:L | 97.1% | 25 | -0.026 [-0.499, +0.444] (0.69) | -0.227 (0.71) | -0.036 | +0.133 | +0.077 | +7.86 / +6.96 |  (nan) |
| DN | PDX:day:L | 95.6% | 31 | -0.907 [-1.625, -0.105] (1.13) | -1.143 (1.04) | -0.572 | -1.260 | -0.901 | +25.84 / +5.33 |  (nan) |
| MV | PDX:day:L | 96.0% | 45 | +0.590 [-0.158, +1.445] (1.17) | +0.476 (1.13) | +0.473 | -0.127 | +0.592 | -11.96 / +2.87 |  (nan) |
| MA | PDX:day:L | 98.0% | 8 | +0.151 [-0.708, +1.213] (1.39) | +0.015 (1.31) | +0.305 | +0.000 | -0.149 | -0.75 / +6.92 |  (nan) |
| ST | PDX:day:H | 96.3% | 46 | -0.114 [-0.673, +0.477] (0.84) | -0.253 (0.76) | +0.068 | -0.386 | -0.398 | +6.90 / +3.78 | -4562 (10622) |
| HM | PDX:day:H | 94.9% | 46 | -0.443 [-1.169, +0.215] (1.00) | -0.660 (0.97) | -0.252 | -0.669 | -0.506 | +13.04 / +4.30 | +889 (10631) |
| WT | PDX:day:H | 98.4% | 28 | -0.054 [-0.264, +0.144] (0.30) | -0.082 (0.30) | -0.016 | -0.031 | -0.070 | +5.02 / +1.73 | -1522 (2796) |
| KB | PDX:day:H | 96.0% | 50 | -0.056 [-0.639, +0.587] (0.88) | -0.120 (0.80) | +0.025 | -0.425 | -0.274 | +3.02 / +1.60 | -393 (3880) |
| SM | PDX:day:H | 95.9% | 13 | +0.737 [-1.029, +2.064] (2.17) | +0.609 (2.33) | +0.872 | +1.010 | +0.880 | -14.71 / +3.09 | +444 (2900) |
| PE | PDX:day:H | 96.2% | 45 | -0.642 [-1.246, -0.045] (0.87) | -0.643 (0.81) | -0.769 | -1.151 | -0.830 | +17.06 / +0.02 | -2599 (5951) |
| PB | PDX:day:H | 95.2% | 42 | -0.395 [-1.271, +0.640] (1.34) | -0.715 (1.29) | -0.370 | -0.846 | -1.253 | +14.74 / +6.59 |  (nan) |
| DN | PDX:day:H | 93.2% | 48 | -0.097 [-1.111, +0.880] (1.46) | -0.518 (1.32) | -0.079 | +0.594 | -0.109 | +7.56 / +6.14 |  (nan) |
| MV | PDX:day:H | 95.1% | 55 | +0.239 [-0.550, +1.020] (1.08) | +0.116 (1.01) | +0.511 | +0.342 | +0.212 | -2.39 / +2.52 |  (nan) |
| MA | PDX:day:H | 96.6% | 14 | -1.356 [-2.130, -0.497] (1.18) | -1.543 (1.39) | -1.200 | -1.959 | -1.448 | +44.85 / +5.42 |  (nan) |
| ST | PDX:week:L | 99.3% | 9 | -0.112 [-0.326, +0.147] (0.34) | -0.139 (0.35) | -0.061 | +0.295 | -0.062 | +19.42 / +3.79 | -3357 (8650) |
| HM | PDX:week:L | 99.2% | 7 | -0.293 [-0.561, +0.026] (0.42) | -0.327 (0.45) | -0.271 | +0.072 | -0.328 | +42.47 / +4.45 | -2810 (4471) |
| WT | PDX:week:L | 99.9% | 2 | -0.037 [-0.095, +0.000] (0.07) | -0.039 (0.08) | -0.034 | +0.000 | -0.034 | +33.51 / +1.74 | -430 (880) |
| KB | PDX:week:L | 99.6% | 5 | -0.232 [-0.403, -0.083] (0.25) | -0.238 (0.28) | -0.169 | -0.198 | -0.254 | +59.76 / +1.42 | -648 (2429) |
| SM | PDX:week:L | 99.7% | 1 | -0.183 [-0.630, +0.000] (0.54) | -0.190 (0.51) | -0.155 | -0.880 | -0.353 | +59.76 / +2.17 | -293 (821) |
| PE | PDX:week:L | 99.5% | 6 | -0.095 [-0.347, +0.160] (0.35) | -0.098 (0.34) | -0.086 | -0.227 | -0.091 | +19.42 / +0.57 | -196 (384) |
| PB | PDX:week:L | 99.5% | 4 | +0.036 [-0.193, +0.333] (0.38) | +0.003 (0.40) | +0.096 | +0.345 | +0.031 | -0.75 / +7.02 |  (nan) |
| DN | PDX:week:L | 98.9% | 8 | -0.269 [-0.675, +0.116] (0.57) | -0.337 (0.58) | -0.254 | +0.000 | +0.065 | +29.51 / +5.97 |  (nan) |
| MV | PDX:week:L | 99.6% | 5 | +0.175 [-0.048, +0.396] (0.32) | +0.164 (0.33) | +0.155 | +0.243 | +0.107 | -37.05 / +2.45 |  (nan) |
| MA | PDX:week:L | 99.8% | 1 | -0.131 [-0.408, +0.000] (0.36) | -0.147 (0.40) | -0.115 | +0.000 | -0.235 | +59.76 / +6.64 |  (nan) |
| ST | PDX:week:H | 99.4% | 7 | -0.117 [-0.330, +0.098] (0.30) | -0.138 (0.30) | -0.064 | -0.252 | -0.120 | +24.79 / +3.78 | -282 (1799) |
| HM | PDX:week:H | 99.1% | 8 | +0.003 [-0.298, +0.291] (0.42) | -0.038 (0.41) | -0.062 | -0.264 | +0.061 | +4.35 / +4.74 | -863 (4929) |
| WT | PDX:week:H | 99.9% | 1 | -0.019 [-0.060, +0.000] (0.05) | -0.020 (0.06) | -0.009 | -0.076 | -0.034 | +33.51 / +1.76 | -146 (409) |
| KB | PDX:week:H | 99.4% | 7 | +0.060 [-0.178, +0.350] (0.37) | +0.051 (0.37) | +0.028 | +0.557 | +0.282 | -9.10 / +1.72 | +120 (693) |
| SM | PDX:week:H | 99.4% | 2 | +0.020 [-0.549, +0.586] (0.78) | +0.005 (0.77) | +0.025 | +0.000 | +0.380 | -0.75 / +2.38 | +30 (1246) |
| PE | PDX:week:H | 99.2% | 9 | -0.152 [-0.420, +0.065] (0.32) | -0.156 (0.32) | -0.228 | -0.250 | +0.016 | +20.65 / +0.51 | -552 (1679) |
| PB | PDX:week:H | 99.4% | 5 | -0.166 [-0.435, +0.105] (0.41) | -0.205 (0.43) | -0.270 | -0.846 | -0.332 | +35.56 / +6.82 |  (nan) |
| DN | PDX:week:H | 98.9% | 8 | -0.204 [-0.629, +0.239] (0.61) | -0.273 (0.60) | -0.104 | -0.309 | +0.033 | +23.88 / +6.03 |  (nan) |
| MV | PDX:week:H | 99.3% | 8 | -0.112 [-0.406, +0.152] (0.40) | -0.128 (0.39) | -0.084 | -0.070 | -0.036 | +18.07 / +2.17 |  (nan) |
| MA | PDX:week:H | 99.8% | 1 | +0.168 [+0.000, +0.527] (0.44) | +0.150 (0.42) | +0.141 | +0.000 | +0.323 | -61.25 / +6.94 |  (nan) |

### skip [70/30]

| book | POI ahead | kept share L6M | fires L6M | per contract L6M [95% CI] (MDE) | gain per signal L6M (MDE) | per contract HOLD | per contract 2026 | L3M(view) | fired mean (base) / kept mean L6M | stack L6M (MDE) |
|--|--|--|--|--|--|--|--|--|--|--|
| ST | ARR:FVG:4h | 94.9% | 64 | +0.524 [-0.053, +1.242] (0.93) | +0.277 (0.77) | +0.501 | -0.740 | -0.056 | -5.43 / +4.89 | +2879 (12471) |
| HM | ARR:FVG:4h | 92.5% | 68 | +0.840 [-0.243, +2.189] (1.75) | +0.454 (1.33) | +0.470 | +0.668 | +0.825 | -6.07 / +5.16 | +10740 (12448) |
| WT | ARR:FVG:4h | 97.0% | 51 | +0.092 [-0.175, +0.363] (0.40) | +0.033 (0.39) | +0.071 | +0.089 | -0.019 | -1.10 / +1.96 | -1871 (5515) |
| KB | ARR:FVG:4h | 94.3% | 72 | -0.564 [-1.139, +0.052] (0.82) | -0.608 (0.80) | -0.641 | -1.589 | -0.910 | +10.61 / +0.77 | -2542 (6577) |
| SM | ARR:FVG:4h | 86.3% | 43 | +1.051 [-1.246, +3.725] (3.65) | +0.463 (3.35) | +0.678 | +2.617 | +2.277 | -3.38 / +4.29 | +654 (5333) |
| PE | ARR:FVG:4h | 95.1% | 58 | -0.173 [-0.611, +0.339] (0.73) | -0.204 (0.76) | -0.293 | +0.132 | +0.003 | +4.20 / +0.63 | -1552 (5192) |
| PB | ARR:FVG:4h | 97.5% | 22 | +0.640 [+0.003, +1.388] (1.00) | +0.430 (0.89) | +0.825 | +1.850 | +0.941 | -16.91 / +8.21 |  (nan) |
| DN | ARR:FVG:4h | 92.3% | 54 | -0.488 [-1.290, +0.409] (1.23) | -0.871 (1.28) | -0.617 | -1.878 | -1.196 | +11.31 / +4.97 |  (nan) |
| MV | ARR:FVG:4h | 93.3% | 76 | +0.039 [-0.890, +1.017] (1.38) | -0.117 (1.24) | -0.219 | -1.058 | -0.638 | +1.74 / +2.34 |  (nan) |
| MA | ARR:FVG:4h | 87.2% | 52 | +0.369 [-1.414, +2.204] (2.59) | -0.478 (2.53) | +0.857 | -3.189 | -1.002 | +3.74 / +6.52 |  (nan) |
| ST | PDX:day:L | 96.6% | 43 | -0.033 [-0.613, +0.738] (0.97) | -0.178 (0.88) | -0.024 | +0.097 | -0.240 | +5.20 / +4.33 | -6756 (12092) |
| HM | PDX:day:L | 96.0% | 36 | -0.084 [-0.772, +0.607] (0.94) | -0.252 (0.98) | -0.096 | -0.552 | +0.164 | +6.37 / +4.23 | -4115 (7075) |
| WT | PDX:day:L | 99.1% | 16 | -0.057 [-0.225, +0.129] (0.25) | -0.073 (0.25) | -0.027 | +0.000 | -0.089 | +7.80 / +1.81 | -358 (3361) |
| KB | PDX:day:L | 97.1% | 36 | -0.133 [-0.680, +0.430] (0.78) | -0.167 (0.80) | -0.107 | -0.139 | -0.046 | +5.83 / +1.20 | -956 (3540) |
| SM | PDX:day:L | 99.0% | 3 | +0.229 [-0.418, +0.909] (1.00) | +0.196 (0.92) | +0.240 | +0.000 | +0.000 | -20.56 / +3.47 | +326 (1967) |
| PE | PDX:day:L | 96.6% | 40 | -0.426 [-0.945, +0.140] (0.81) | -0.440 (0.79) | -0.350 | -0.265 | -0.556 | +13.13 / +0.37 | -707 (6408) |
| PB | PDX:day:L | 97.1% | 25 | -0.109 [-0.630, +0.377] (0.74) | -0.320 (0.76) | -0.111 | +0.132 | -0.136 | +11.09 / +7.47 |  (nan) |
| DN | PDX:day:L | 95.6% | 31 | -0.874 [-1.593, -0.097] (1.09) | -1.070 (1.02) | -0.552 | -1.318 | -0.914 | +24.19 / +4.59 |  (nan) |
| MV | PDX:day:L | 96.0% | 45 | +0.620 [-0.114, +1.451] (1.13) | +0.508 (1.11) | +0.496 | -0.141 | +0.568 | -12.78 / +2.92 |  (nan) |
| MA | PDX:day:L | 98.0% | 8 | +0.125 [-0.743, +1.189] (1.41) | -0.003 (1.32) | +0.312 | +0.000 | -0.177 | +0.17 / +6.29 |  (nan) |
| ST | PDX:day:H | 96.3% | 46 | -0.296 [-0.863, +0.259] (0.79) | -0.444 (0.71) | -0.096 | -0.274 | -0.520 | +12.12 / +4.07 | -5641 (10549) |
| HM | PDX:day:H | 94.9% | 46 | -0.392 [-1.076, +0.236] (0.97) | -0.587 (0.94) | -0.201 | -0.550 | -0.460 | +11.59 / +3.93 | -88 (10638) |
| WT | PDX:day:H | 98.4% | 28 | -0.060 [-0.250, +0.113] (0.27) | -0.087 (0.27) | -0.021 | -0.010 | -0.033 | +5.32 / +1.81 | -1460 (2823) |
| KB | PDX:day:H | 96.0% | 50 | -0.001 [-0.535, +0.649] (0.85) | -0.053 (0.78) | +0.049 | -0.320 | -0.221 | +1.33 / +1.33 | -1099 (4042) |
| SM | PDX:day:H | 95.9% | 13 | +0.759 [-0.998, +2.111] (2.18) | +0.595 (2.36) | +0.899 | +1.034 | +0.879 | -14.36 / +4.00 | +427 (2923) |
| PE | PDX:day:H | 96.2% | 45 | -0.597 [-1.172, +0.026] (0.85) | -0.607 (0.80) | -0.733 | -1.090 | -0.766 | +16.09 / +0.20 | -3186 (5798) |
| PB | PDX:day:H | 95.2% | 42 | -0.370 [-1.234, +0.645] (1.32) | -0.724 (1.29) | -0.344 | -0.848 | -1.211 | +14.92 / +7.20 |  (nan) |
| DN | PDX:day:H | 93.2% | 48 | -0.146 [-1.178, +0.844] (1.47) | -0.513 (1.32) | -0.136 | +0.531 | -0.184 | +7.49 / +5.31 |  (nan) |
| MV | PDX:day:H | 95.1% | 55 | +0.246 [-0.520, +1.021] (1.08) | +0.124 (1.01) | +0.529 | +0.378 | +0.208 | -2.55 / +2.54 |  (nan) |
| MA | PDX:day:H | 96.6% | 14 | -1.416 [-2.199, -0.531] (1.22) | -1.574 (1.41) | -1.249 | -2.033 | -1.520 | +45.77 / +4.75 |  (nan) |
| ST | PDX:week:L | 99.3% | 9 | -0.182 [-0.369, +0.049] (0.29) | -0.211 (0.31) | -0.124 | +0.298 | -0.040 | +29.47 / +4.18 | -1474 (7068) |
| HM | PDX:week:L | 99.2% | 7 | -0.283 [-0.559, +0.028] (0.41) | -0.313 (0.45) | -0.261 | +0.145 | -0.307 | +40.63 / +4.04 | -2717 (4639) |
| WT | PDX:week:L | 99.9% | 2 | -0.038 [-0.097, +0.000] (0.07) | -0.040 (0.08) | -0.035 | +0.000 | -0.034 | +34.16 / +1.83 | -299 (581) |
| KB | PDX:week:L | 99.6% | 5 | -0.238 [-0.413, -0.086] (0.25) | -0.242 (0.28) | -0.175 | -0.202 | -0.259 | +60.89 / +1.10 | -1552 (3180) |
| SM | PDX:week:L | 99.7% | 1 | -0.182 [-0.634, +0.000] (0.53) | -0.193 (0.52) | -0.154 | -0.882 | -0.355 | +60.62 / +3.06 | -297 (833) |
| PE | PDX:week:L | 99.5% | 6 | -0.097 [-0.348, +0.159] (0.36) | -0.101 (0.34) | -0.088 | -0.229 | -0.093 | +20.10 / +0.70 | -357 (798) |
| PB | PDX:week:L | 99.5% | 4 | +0.075 [-0.126, +0.346] (0.35) | +0.045 (0.34) | +0.132 | +0.345 | +0.067 | -9.72 / +7.65 |  (nan) |
| DN | PDX:week:L | 98.9% | 8 | -0.237 [-0.651, +0.176] (0.61) | -0.293 (0.61) | -0.225 | +0.000 | +0.146 | +25.64 / +5.23 |  (nan) |
| MV | PDX:week:L | 99.6% | 5 | +0.173 [-0.050, +0.394] (0.32) | +0.163 (0.33) | +0.153 | +0.241 | +0.105 | -36.86 / +2.47 |  (nan) |
| MA | PDX:week:L | 99.8% | 1 | -0.135 [-0.419, +0.000] (0.37) | -0.150 (0.41) | -0.119 | +0.000 | -0.244 | +60.87 / +6.03 |  (nan) |
| ST | PDX:week:H | 99.4% | 7 | -0.119 [-0.329, +0.101] (0.31) | -0.143 (0.31) | -0.065 | -0.258 | -0.123 | +25.64 / +4.24 | -250 (1788) |
| HM | PDX:week:H | 99.1% | 8 | -0.004 [-0.308, +0.284] (0.42) | -0.043 (0.42) | -0.069 | -0.274 | +0.054 | +4.88 / +4.31 | -833 (5054) |
| WT | PDX:week:H | 99.9% | 1 | -0.019 [-0.061, +0.000] (0.05) | -0.020 (0.06) | -0.010 | -0.079 | -0.035 | +34.23 / +1.85 | -149 (418) |
| KB | PDX:week:H | 99.4% | 7 | +0.031 [-0.240, +0.329] (0.40) | +0.023 (0.39) | -0.001 | +0.554 | +0.281 | -4.10 / +1.36 | -139 (318) |
| SM | PDX:week:H | 99.4% | 2 | +0.023 [-0.550, +0.590] (0.78) | +0.002 (0.78) | +0.028 | +0.000 | +0.382 | -0.33 / +3.26 | +26 (1255) |
| PE | PDX:week:H | 99.2% | 9 | -0.183 [-0.461, +0.050] (0.35) | -0.188 (0.35) | -0.257 | -0.257 | +0.012 | +24.93 / +0.62 | -1061 (2128) |
| PB | PDX:week:H | 99.4% | 5 | -0.167 [-0.435, +0.106] (0.41) | -0.210 (0.43) | -0.271 | -0.847 | -0.330 | +36.43 / +7.41 |  (nan) |
| DN | PDX:week:H | 98.9% | 8 | -0.221 [-0.663, +0.231] (0.63) | -0.281 (0.60) | -0.126 | -0.320 | +0.027 | +24.65 / +5.24 |  (nan) |
| MV | PDX:week:H | 99.3% | 8 | -0.100 [-0.392, +0.159] (0.39) | -0.116 (0.38) | -0.060 | -0.075 | -0.038 | +16.35 / +2.20 |  (nan) |
| MA | PDX:week:H | 99.8% | 1 | +0.168 [+0.000, +0.527] (0.44) | +0.151 (0.42) | +0.141 | +0.000 | +0.324 | -61.28 / +6.33 |  (nan) |

### re-target to POI-2t [market]

| book | POI ahead | kept share L6M | fires L6M | per contract L6M [95% CI] (MDE) | gain per signal L6M (MDE) | per contract HOLD | per contract 2026 | L3M(view) | fired mean (base) / kept mean L6M | stack L6M (MDE) |
|--|--|--|--|--|--|--|--|--|--|--|
| ST | ARR:FVG:4h | 94.9% | 64 | -0.145 [-0.563, +0.353] (0.65) | -0.145 (0.66) | -0.088 | -0.839 | -0.412 | -7.20 / +4.49 | -468 (7458) |
| HM | ARR:FVG:4h | 92.5% | 68 | -0.153 [-0.671, +0.404] (0.80) | -0.153 (0.83) | -0.239 | -0.672 | -0.224 | -6.95 / +5.68 | -225 (7704) |
| WT | ARR:FVG:4h | 97.0% | 51 | -0.005 [-0.204, +0.190] (0.27) | -0.005 (0.28) | -0.021 | -0.084 | -0.009 | -2.46 / +1.91 | -2288 (3006) |
| KB | ARR:FVG:4h | 94.3% | 72 | -0.193 [-0.654, +0.266] (0.69) | -0.193 (0.68) | -0.247 | -0.786 | -0.342 | +8.80 / +1.22 | -349 (4403) |
| SM | ARR:FVG:4h | 86.3% | 43 | -0.142 [-1.674, +1.436] (2.19) | -0.142 (2.21) | -0.180 | +1.693 | +1.169 | -3.47 / +3.28 | -438 (3382) |
| PE | ARR:FVG:4h | 95.1% | 58 | -0.340 [-0.624, -0.005] (0.44) | -0.340 (0.46) | -0.397 | -0.409 | -0.399 | +4.27 / +0.48 | -1471 (1641) |
| PB | ARR:FVG:4h | 97.5% | 22 | +0.208 [-0.125, +0.608] (0.53) | +0.208 (0.55) | +0.187 | +0.586 | +0.157 | -17.25 / +7.61 |  (nan) |
| DN | ARR:FVG:4h | 92.3% | 54 | -0.375 [-0.992, +0.238] (0.87) | -0.375 (0.87) | -0.379 | -0.873 | -0.357 | +11.62 / +5.79 |  (nan) |
| MV | ARR:FVG:4h | 93.3% | 76 | -0.243 [-0.863, +0.554] (1.01) | -0.243 (1.03) | -0.276 | -1.086 | -0.613 | +0.85 / +2.38 |  (nan) |
| MA | ARR:FVG:4h | 87.2% | 52 | -0.617 [-1.713, +0.563] (1.69) | -0.617 (1.74) | -0.064 | -2.514 | -1.394 | +3.91 / +7.19 |  (nan) |
| ST | PDX:day:L | 96.6% | 43 | -0.033 [-0.359, +0.385] (0.55) | -0.033 (0.54) | -0.141 | -0.237 | -0.298 | +4.00 / +3.89 | -2028 (4752) |
| HM | PDX:day:L | 96.0% | 36 | -0.340 [-0.716, +0.066] (0.55) | -0.340 (0.57) | -0.369 | -0.586 | -0.092 | +6.84 / +4.65 | -397 (4002) |
| WT | PDX:day:L | 99.1% | 16 | -0.106 [-0.170, -0.052] (0.08) | -0.106 (0.09) | -0.114 | +0.000 | -0.057 | +8.58 / +1.72 | -453 (842) |
| KB | PDX:day:L | 97.1% | 36 | -0.058 [-0.303, +0.204] (0.37) | -0.058 (0.40) | -0.132 | +0.148 | +0.109 | +6.84 / +1.50 | +102 (1654) |
| SM | PDX:day:L | 99.0% | 3 | +0.286 [-0.017, +0.910] (0.82) | +0.286 (0.78) | +0.106 | +0.000 | +0.000 | -20.92 / +2.58 | +746 (2116) |
| PE | PDX:day:L | 96.6% | 40 | -0.202 [-0.511, +0.125] (0.44) | -0.202 (0.48) | -0.232 | -0.295 | -0.380 | +14.38 / +0.19 | -322 (3448) |
| PB | PDX:day:L | 97.1% | 25 | -0.002 [-0.343, +0.391] (0.51) | -0.002 (0.54) | -0.039 | -0.076 | +0.016 | +7.86 / +6.96 |  (nan) |
| DN | PDX:day:L | 95.6% | 31 | -0.401 [-0.928, +0.223] (0.84) | -0.401 (0.85) | -0.234 | -0.738 | -0.588 | +25.84 / +5.33 |  (nan) |
| MV | PDX:day:L | 96.0% | 45 | +0.282 [-0.190, +0.818] (0.73) | +0.282 (0.76) | +0.168 | -0.089 | +0.170 | -11.96 / +2.87 |  (nan) |
| MA | PDX:day:L | 98.0% | 8 | -0.238 [-0.540, -0.024] (0.38) | -0.238 (0.38) | -0.315 | +0.000 | -0.298 | -0.75 / +6.92 |  (nan) |
| ST | PDX:day:H | 96.3% | 46 | +0.145 [-0.352, +0.706] (0.77) | +0.145 (0.79) | +0.189 | +0.056 | +0.173 | +6.90 / +3.78 | -4261 (7522) |
| HM | PDX:day:H | 94.9% | 46 | -0.294 [-0.719, +0.132] (0.63) | -0.294 (0.64) | -0.111 | -0.291 | -0.270 | +13.04 / +4.30 | +3044 (7848) |
| WT | PDX:day:H | 98.4% | 28 | -0.006 [-0.168, +0.202] (0.26) | -0.006 (0.27) | +0.020 | -0.093 | -0.081 | +5.02 / +1.73 | -620 (2763) |
| KB | PDX:day:H | 96.0% | 50 | -0.052 [-0.336, +0.272] (0.44) | -0.052 (0.48) | +0.075 | -0.318 | -0.238 | +3.02 / +1.60 | -1034 (2924) |
| SM | PDX:day:H | 95.9% | 13 | +0.487 [-0.464, +1.439] (1.39) | +0.487 (1.39) | +0.421 | +0.000 | +0.637 | -14.71 / +3.09 | -196 (1511) |
| PE | PDX:day:H | 96.2% | 45 | -0.100 [-0.483, +0.267] (0.53) | -0.100 (0.53) | -0.147 | -0.411 | -0.127 | +17.06 / +0.02 | +1549 (3611) |
| PB | PDX:day:H | 95.2% | 42 | -0.057 [-0.564, +0.544] (0.77) | -0.057 (0.70) | -0.052 | -0.231 | -0.292 | +14.74 / +6.59 |  (nan) |
| DN | PDX:day:H | 93.2% | 48 | -0.125 [-0.794, +0.593] (0.99) | -0.125 (1.02) | -0.168 | +0.613 | -0.048 | +7.56 / +6.14 |  (nan) |
| MV | PDX:day:H | 95.1% | 55 | +0.413 [-0.182, +1.125] (0.94) | +0.413 (0.94) | +0.488 | +0.664 | +0.471 | -2.39 / +2.52 |  (nan) |
| MA | PDX:day:H | 96.6% | 14 | -0.648 [-0.994, -0.299] (0.51) | -0.648 (0.53) | -0.556 | -0.532 | -0.737 | +44.85 / +5.42 |  (nan) |
| ST | PDX:week:L | 99.3% | 9 | -0.052 [-0.227, +0.185] (0.30) | -0.052 (0.32) | -0.047 | -0.087 | -0.156 | +19.42 / +3.79 | -4141 (7112) |
| HM | PDX:week:L | 99.2% | 7 | -0.166 [-0.328, -0.018] (0.22) | -0.166 (0.22) | -0.150 | -0.071 | -0.223 | +42.47 / +4.45 | -744 (1320) |
| WT | PDX:week:L | 99.9% | 2 | -0.013 [-0.033, +0.000] (0.03) | -0.013 (0.03) | -0.012 | +0.000 | -0.012 | +33.51 / +1.74 | -94 (186) |
| KB | PDX:week:L | 99.6% | 5 | -0.078 [-0.153, -0.017] (0.10) | -0.078 (0.10) | -0.071 | -0.048 | -0.079 | +59.76 / +1.42 | +469 (1018) |
| SM | PDX:week:L | 99.7% | 1 | -0.002 [-0.008, +0.000] (0.01) | -0.002 (0.01) | -0.002 | -0.012 | -0.005 | +59.76 / +2.17 | -4 (11) |
| PE | PDX:week:L | 99.5% | 6 | +0.018 [-0.137, +0.227] (0.26) | +0.018 (0.27) | +0.016 | -0.043 | -0.046 | +19.42 / +0.57 | -103 (208) |
| PB | PDX:week:L | 99.5% | 4 | +0.105 [-0.057, +0.388] (0.36) | +0.105 (0.37) | +0.094 | +0.000 | -0.024 | -0.75 / +7.02 |  (nan) |
| DN | PDX:week:L | 98.9% | 8 | -0.146 [-0.272, -0.039] (0.17) | -0.146 (0.18) | -0.130 | +0.000 | -0.088 | +29.51 / +5.97 |  (nan) |
| MV | PDX:week:L | 99.6% | 5 | +0.092 [-0.005, +0.299] (0.25) | +0.092 (0.26) | +0.084 | +0.000 | -0.003 | -37.05 / +2.45 |  (nan) |
| MA | PDX:week:L | 99.8% | 1 | -0.125 [-0.384, +0.000] (0.34) | -0.125 (0.34) | -0.108 | +0.000 | -0.234 | +59.76 / +6.64 |  (nan) |
| ST | PDX:week:H | 99.4% | 7 | -0.011 [-0.127, +0.127] (0.18) | -0.011 (0.18) | -0.010 | +0.061 | +0.024 | +24.79 / +3.78 | -216 (772) |
| HM | PDX:week:H | 99.1% | 8 | -0.052 [-0.212, +0.111] (0.22) | -0.052 (0.22) | -0.066 | -0.103 | +0.048 | +4.35 / +4.74 | -236 (460) |
| WT | PDX:week:H | 99.9% | 1 | -0.003 [-0.010, +0.000] (0.01) | -0.003 (0.01) | -0.011 | -0.013 | -0.006 | +33.51 / +1.76 | -26 (74) |
| KB | PDX:week:H | 99.4% | 7 | +0.092 [-0.027, +0.273] (0.22) | +0.092 (0.21) | +0.101 | +0.447 | +0.177 | -9.10 / +1.72 | -65 (182) |
| SM | PDX:week:H | 99.4% | 2 | -0.119 [-0.384, +0.000] (0.35) | -0.119 (0.33) | -0.103 | +0.000 | +0.000 | -0.75 / +2.38 | -197 (551) |
| PE | PDX:week:H | 99.2% | 9 | -0.035 [-0.166, +0.081] (0.17) | -0.035 (0.16) | -0.064 | -0.158 | +0.001 | +20.65 / +0.51 | -112 (365) |
| PB | PDX:week:H | 99.4% | 5 | -0.058 [-0.138, -0.004] (0.09) | -0.058 (0.10) | -0.093 | -0.163 | -0.066 | +35.56 / +6.82 |  (nan) |
| DN | PDX:week:H | 98.9% | 8 | -0.138 [-0.315, +0.004] (0.24) | -0.138 (0.23) | -0.135 | -0.214 | -0.082 | +23.88 / +6.03 |  (nan) |
| MV | PDX:week:H | 99.3% | 8 | -0.038 [-0.159, +0.120] (0.19) | -0.038 (0.18) | -0.074 | +0.098 | +0.041 | +18.07 / +2.17 |  (nan) |
| MA | PDX:week:H | 99.8% | 1 | +0.000 [+0.000, +0.000] (0.00) | +0.000 (0.00) | +0.000 | +0.000 | +0.000 | -61.25 / +6.94 |  (nan) |

### re-target to POI-2t [70/30]

| book | POI ahead | kept share L6M | fires L6M | per contract L6M [95% CI] (MDE) | gain per signal L6M (MDE) | per contract HOLD | per contract 2026 | L3M(view) | fired mean (base) / kept mean L6M | stack L6M (MDE) |
|--|--|--|--|--|--|--|--|--|--|--|
| ST | ARR:FVG:4h | 94.9% | 64 | -0.250 [-0.641, +0.227] (0.63) | -0.253 (0.64) | -0.188 | -0.907 | -0.424 | -5.43 / +4.89 | -233 (9761) |
| HM | ARR:FVG:4h | 92.5% | 68 | -0.248 [-0.834, +0.394] (0.89) | -0.252 (0.89) | -0.329 | -0.612 | -0.170 | -6.07 / +5.16 | -560 (7687) |
| WT | ARR:FVG:4h | 97.0% | 51 | -0.058 [-0.259, +0.160] (0.29) | -0.058 (0.29) | -0.078 | -0.072 | -0.005 | -1.10 / +1.96 | -1809 (3056) |
| KB | ARR:FVG:4h | 94.3% | 72 | -0.300 [-0.713, +0.152] (0.65) | -0.300 (0.66) | -0.349 | -0.809 | -0.513 | +10.61 / +0.77 | -1372 (2498) |
| SM | ARR:FVG:4h | 86.3% | 43 | -0.197 [-1.706, +1.418] (2.21) | -0.210 (2.23) | -0.229 | +1.707 | +1.123 | -3.38 / +4.29 | -601 (3378) |
| PE | ARR:FVG:4h | 95.1% | 58 | -0.340 [-0.625, -0.016] (0.44) | -0.341 (0.47) | -0.410 | -0.427 | -0.385 | +4.20 / +0.63 | -1847 (2262) |
| PB | ARR:FVG:4h | 97.5% | 22 | +0.207 [-0.128, +0.610] (0.53) | +0.208 (0.56) | +0.186 | +0.582 | +0.156 | -16.91 / +8.21 |  (nan) |
| DN | ARR:FVG:4h | 92.3% | 54 | -0.363 [-0.985, +0.269] (0.89) | -0.366 (0.89) | -0.353 | -0.844 | -0.374 | +11.31 / +4.97 |  (nan) |
| MV | ARR:FVG:4h | 93.3% | 76 | -0.328 [-0.916, +0.448] (0.93) | -0.334 (0.98) | -0.356 | -1.040 | -0.546 | +1.74 / +2.34 |  (nan) |
| MA | ARR:FVG:4h | 87.2% | 52 | -0.639 [-1.775, +0.567] (1.69) | -0.653 (1.73) | -0.119 | -2.504 | -1.353 | +3.74 / +6.52 |  (nan) |
| ST | PDX:day:L | 96.6% | 43 | -0.112 [-0.448, +0.283] (0.53) | -0.115 (0.52) | -0.215 | -0.206 | -0.264 | +5.20 / +4.33 | -417 (5432) |
| HM | PDX:day:L | 96.0% | 36 | -0.335 [-0.717, +0.069] (0.55) | -0.335 (0.57) | -0.366 | -0.541 | -0.073 | +6.37 / +4.23 | -645 (4139) |
| WT | PDX:day:L | 99.1% | 16 | -0.100 [-0.160, -0.047] (0.08) | -0.100 (0.09) | -0.076 | +0.000 | -0.058 | +7.80 / +1.81 | -705 (761) |
| KB | PDX:day:L | 97.1% | 36 | -0.044 [-0.291, +0.214] (0.36) | -0.044 (0.39) | -0.126 | +0.129 | +0.096 | +5.83 / +1.20 | -1654 (4186) |
| SM | PDX:day:L | 99.0% | 3 | +0.287 [-0.017, +0.915] (0.82) | +0.288 (0.78) | +0.105 | +0.000 | +0.000 | -20.56 / +3.47 | +756 (2145) |
| PE | PDX:day:L | 96.6% | 40 | -0.195 [-0.485, +0.116] (0.42) | -0.196 (0.46) | -0.227 | -0.268 | -0.373 | +13.13 / +0.37 | -891 (3486) |
| PB | PDX:day:L | 97.1% | 25 | -0.126 [-0.361, +0.161] (0.36) | -0.126 (0.38) | -0.150 | -0.077 | -0.215 | +11.09 / +7.47 |  (nan) |
| DN | PDX:day:L | 95.6% | 31 | -0.378 [-0.904, +0.233] (0.84) | -0.379 (0.86) | -0.216 | -0.760 | -0.587 | +24.19 / +4.59 |  (nan) |
| MV | PDX:day:L | 96.0% | 45 | +0.293 [-0.167, +0.835] (0.72) | +0.294 (0.75) | +0.172 | -0.090 | +0.157 | -12.78 / +2.92 |  (nan) |
| MA | PDX:day:L | 98.0% | 8 | -0.270 [-0.584, -0.025] (0.42) | -0.273 (0.42) | -0.345 | +0.000 | -0.310 | +0.17 / +6.29 |  (nan) |
| ST | PDX:day:H | 96.3% | 46 | -0.069 [-0.431, +0.332] (0.56) | -0.072 (0.55) | -0.007 | +0.095 | +0.022 | +12.12 / +4.07 | -4779 (6822) |
| HM | PDX:day:H | 94.9% | 46 | -0.275 [-0.705, +0.148] (0.62) | -0.277 (0.63) | -0.094 | -0.279 | -0.257 | +11.59 / +3.93 | +1556 (6327) |
| WT | PDX:day:H | 98.4% | 28 | -0.029 [-0.148, +0.099] (0.17) | -0.028 (0.18) | -0.000 | -0.077 | -0.054 | +5.32 / +1.81 | -368 (2434) |
| KB | PDX:day:H | 96.0% | 50 | -0.023 [-0.322, +0.294] (0.45) | -0.024 (0.49) | +0.075 | -0.265 | -0.203 | +1.33 / +1.33 | -867 (3030) |
| SM | PDX:day:H | 95.9% | 13 | +0.454 [-0.472, +1.336] (1.35) | +0.448 (1.35) | +0.395 | +0.000 | +0.622 | -14.36 / +4.00 | -246 (1478) |
| PE | PDX:day:H | 96.2% | 45 | -0.102 [-0.485, +0.257] (0.53) | -0.103 (0.53) | -0.152 | -0.379 | -0.110 | +16.09 / +0.20 | +864 (3603) |
| PB | PDX:day:H | 95.2% | 42 | +0.021 [-0.535, +0.640] (0.84) | +0.010 (0.75) | +0.010 | -0.285 | -0.312 | +14.92 / +7.20 |  (nan) |
| DN | PDX:day:H | 93.2% | 48 | -0.126 [-0.803, +0.599] (1.01) | -0.133 (1.04) | -0.173 | +0.595 | -0.076 | +7.49 / +5.31 |  (nan) |
| MV | PDX:day:H | 95.1% | 55 | +0.400 [-0.183, +1.106] (0.93) | +0.399 (0.94) | +0.485 | +0.624 | +0.445 | -2.55 / +2.54 |  (nan) |
| MA | PDX:day:H | 96.6% | 14 | -0.663 [-1.014, -0.307] (0.53) | -0.659 (0.53) | -0.569 | -0.549 | -0.756 | +45.77 / +4.75 |  (nan) |
| ST | PDX:week:L | 99.3% | 9 | -0.133 [-0.227, -0.044] (0.14) | -0.133 (0.13) | -0.121 | -0.088 | -0.137 | +29.47 / +4.18 | -2407 (4083) |
| HM | PDX:week:L | 99.2% | 7 | -0.168 [-0.337, -0.012] (0.23) | -0.169 (0.23) | -0.152 | -0.050 | -0.227 | +40.63 / +4.04 | -771 (1307) |
| WT | PDX:week:L | 99.9% | 2 | -0.014 [-0.034, +0.000] (0.03) | -0.013 (0.03) | -0.012 | +0.000 | -0.012 | +34.16 / +1.83 | -115 (223) |
| KB | PDX:week:L | 99.6% | 5 | -0.080 [-0.156, -0.017] (0.10) | -0.079 (0.11) | -0.073 | -0.049 | -0.081 | +60.89 / +1.10 | -481 (2152) |
| SM | PDX:week:L | 99.7% | 1 | -0.002 [-0.008, +0.000] (0.01) | -0.002 (0.01) | -0.002 | -0.012 | -0.005 | +60.62 / +3.06 | -4 (11) |
| PE | PDX:week:L | 99.5% | 6 | +0.017 [-0.139, +0.228] (0.26) | +0.017 (0.28) | +0.016 | -0.043 | -0.047 | +20.10 / +0.70 | -97 (189) |
| PB | PDX:week:L | 99.5% | 4 | +0.113 [-0.040, +0.397] (0.36) | +0.114 (0.37) | +0.102 | +0.000 | -0.017 | -9.72 / +7.65 |  (nan) |
| DN | PDX:week:L | 98.9% | 8 | -0.134 [-0.257, -0.034] (0.16) | -0.133 (0.17) | -0.120 | +0.000 | -0.062 | +25.64 / +5.23 |  (nan) |
| MV | PDX:week:L | 99.6% | 5 | +0.093 [-0.005, +0.300] (0.25) | +0.093 (0.27) | +0.084 | +0.000 | -0.003 | -36.86 / +2.47 |  (nan) |
| MA | PDX:week:L | 99.8% | 1 | -0.128 [-0.394, +0.000] (0.35) | -0.128 (0.35) | -0.110 | +0.000 | -0.240 | +60.87 / +6.03 |  (nan) |
| ST | PDX:week:H | 99.4% | 7 | -0.013 [-0.130, +0.125] (0.18) | -0.013 (0.18) | -0.012 | +0.058 | +0.023 | +25.64 / +4.24 | -146 (692) |
| HM | PDX:week:H | 99.1% | 8 | -0.054 [-0.215, +0.109] (0.22) | -0.054 (0.22) | -0.068 | -0.106 | +0.047 | +4.88 / +4.31 | -241 (469) |
| WT | PDX:week:H | 99.9% | 1 | -0.003 [-0.010, +0.000] (0.01) | -0.003 (0.01) | -0.011 | -0.013 | -0.006 | +34.23 / +1.85 | -27 (75) |
| KB | PDX:week:H | 99.4% | 7 | +0.066 [-0.058, +0.243] (0.22) | +0.066 (0.21) | +0.077 | +0.447 | +0.177 | -4.10 / +1.36 | -55 (155) |
| SM | PDX:week:H | 99.4% | 2 | -0.120 [-0.387, +0.000] (0.35) | -0.120 (0.33) | -0.104 | +0.000 | -0.000 | -0.33 / +3.26 | -200 (559) |
| PE | PDX:week:H | 99.2% | 9 | -0.063 [-0.188, +0.058] (0.17) | -0.063 (0.16) | -0.090 | -0.160 | -0.000 | +24.93 / +0.62 | -202 (286) |
| PB | PDX:week:H | 99.4% | 5 | -0.071 [-0.167, -0.004] (0.12) | -0.073 (0.13) | -0.105 | -0.216 | -0.087 | +36.43 / +7.41 |  (nan) |
| DN | PDX:week:H | 98.9% | 8 | -0.142 [-0.324, +0.001] (0.24) | -0.141 (0.24) | -0.141 | -0.219 | -0.083 | +24.65 / +5.24 |  (nan) |
| MV | PDX:week:H | 99.3% | 8 | -0.037 [-0.161, +0.121] (0.19) | -0.037 (0.18) | -0.060 | +0.096 | +0.040 | +16.35 / +2.20 |  (nan) |
| MA | PDX:week:H | 99.8% | 1 | -0.000 [-0.000, +0.000] (0.00) | -0.000 (0.00) | -0.000 | +0.000 | -0.000 | -61.28 / +6.33 |  (nan) |

### Headline sentences
* Skipping PE signals whose target lies beyond an unmitigated 4-h FVG (market base): keeps 95.1% of the PE signals (L6M, 58 touched) and changes the result by -0.18 pts per contract [95% CI -0.63, +0.35; MDE 0.73] (-0.21 per signal, MDE 0.75); HOLD -0.30; stack -1567 \$/wk (MDE 5191).
* The same on the 70/30 base: keeps 95.1% of the PE signals (L6M, 58 touched) and changes the result by -0.17 pts per contract [95% CI -0.61, +0.34; MDE 0.73] (-0.20 per signal, MDE 0.76); HOLD -0.29; stack -1552 \$/wk (MDE 5192).
* Re-targeting KB signals to just in front of the prior-day low instead of skipping (market base): keeps 97.1% of the KB signals (L6M, 36 touched) and changes the result by -0.06 pts per contract [95% CI -0.30, +0.20; MDE 0.37] (-0.06 per signal, MDE 0.40); HOLD -0.13; stack +102 \$/wk (MDE 1654).
* Skipping KB signals whose target lies beyond the prior-day low: keeps 97.1% of the KB signals (L6M, 36 touched) and changes the result by -0.15 pts per contract [95% CI -0.69, +0.41; MDE 0.79] (-0.20 per signal, MDE 0.81); HOLD -0.12; stack +1022 \$/wk (MDE 3960).
* Skipping SM signals whose target lies beyond the prior-week high: keeps 99.4% of the SM signals (L6M, 2 touched) and changes the result by +0.02 pts per contract [95% CI -0.55, +0.59; MDE 0.78] (+0.00 per signal, MDE 0.77); HOLD +0.02; stack +30 \$/wk (MDE 1246).
* Re-targeting PE signals to just in front of the prior-day low (market base): keeps 96.6% of the PE signals (L6M, 40 touched) and changes the result by -0.20 pts per contract [95% CI -0.51, +0.13; MDE 0.44] (-0.20 per signal, MDE 0.48); HOLD -0.23; stack -322 \$/wk (MDE 3448).

## 5. Combinations (any-of-k POIs ahead within D, weighted POI score, four-legged) and time windows (3,366 cells: skip / size 50 / 67, market and 70/30)
Same protocol (prereg B2). Tier counts over the 522 selected: DEAD 333, LEAD 127, CANDIDATE-RECENT 62. Mean over selected cells by family (PRE / X' / L6M / HOLD / L3M view / placebo rank L6M):

| family | selected | PRE | X' | L6M | HOLD | L3M | placebo rank | CAND-RECENT |
|--|--|--|--|--|--|--|--|--|
| anyk | 198 | +0.155 | +0.432 | -0.078 | -0.050 | -0.079 | 0.48 | 15 |
| fourleg | 27 | +0.133 | +0.333 | -0.258 | -0.204 | -0.210 | 0.67 | 0 |
| time | 117 | +0.067 | +0.170 | -0.012 | -0.051 | -0.069 | 0.58 | 7 |
| wscore | 180 | +0.220 | +0.376 | -0.145 | -0.081 | -0.161 | 0.58 | 40 |

Best 3 by PRE u X' z per family (pooled scope) and every CANDIDATE-RECENT with >= 30 fires in L6M and HOLD:

| mask | action [base] | scope | fires L6M | PRE | X' | L3M | L6M (MDE) | HOLD | per contract L6M | per contract HOLD | placebo | stack L6M/HOLD | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| wscore:D=20:q=0.9 | size 50% [market] | ALL | 536 (5.5%) | +0.200 | +0.269 | -0.203 | -0.177 (0.21) | -0.090 | -0.090 | -0.010 | 0.49 | +6491/+4369 | DEAD |
| wscore:D=20:q=0.9 | size 67% [market] | ALL | 536 (5.5%) | +0.132 | +0.178 | -0.134 | -0.117 (0.14) | -0.059 | -0.059 | -0.007 | 0.52 | +6130/+3778 | DEAD |
| wscore:D=20:q=0.9 | skip [market] | ALL | 536 (5.5%) | +0.401 | +0.539 | -0.407 | -0.354 (0.42) | -0.180 | -0.185 | -0.021 | 0.51 | +2329/+1248 | DEAD |
| anyk:cls=PDX:k=3:D=20 | skip [70/30] | ALL | 25 (0.3%) | +0.011 | +0.245 | -0.057 | -0.086 (0.11) | -0.070 | -0.078 | -0.064 | 0.05 | -1462/-1332 | DEAD |
| anyk:cls=PDX:k=3:D=20 | size 50% [70/30] | ALL | 25 (0.3%) | +0.006 | +0.122 | -0.029 | -0.043 (0.06) | -0.035 | -0.039 | -0.032 | 0.07 | +55/+44 | DEAD |
| anyk:cls=PDX:k=3:D=20 | size 67% [70/30] | ALL | 25 (0.3%) | +0.004 | +0.081 | -0.019 | -0.028 (0.04) | -0.023 | -0.026 | -0.021 | 0.03 | -698/-609 | DEAD |
| time:macro_1350_1410 | skip [70/30] | ALL | 185 (1.9%) | +0.082 | +0.265 | +0.024 | +0.014 (0.30) | +0.013 | +0.078 | +0.063 | 0.72 | +1588/+962 | LEAD |
| time:macro_1350_1410 | size 50% [70/30] | ALL | 185 (1.9%) | +0.041 | +0.132 | +0.012 | +0.007 (0.15) | +0.006 | +0.039 | +0.031 | 0.80 | +651/+357 | LEAD |
| time:macro_1350_1410 | size 67% [70/30] | ALL | 185 (1.9%) | +0.027 | +0.087 | +0.008 | +0.005 (0.10) | +0.004 | +0.025 | +0.020 | 0.74 | +363/+177 | LEAD |
| anyk:cls=PIV:k=5:D=40 | skip [market] | ALL | 157 (1.6%) | +0.024 | +0.842 | +0.103 | +0.054 (0.30) | +0.076 | +0.108 | +0.133 | 0.98 | -1174/-2405 | CANDIDATE-RECENT |
| anyk:cls=PIV:k=5:D=40 | skip [70/30] | ALL | 157 (1.6%) | +0.033 | +0.763 | +0.106 | +0.061 (0.30) | +0.068 | +0.115 | +0.124 | 0.98 | +558/-212 | CANDIDATE-RECENT |
| anyk:cls=PIV:k=5:D=40 | size 50% [market] | ALL | 157 (1.6%) | +0.012 | +0.421 | +0.052 | +0.027 (0.15) | +0.038 | +0.054 | +0.066 | 0.98 | -306/-2340 | CANDIDATE-RECENT |
| anyk:cls=PIV:k=5:D=40 | size 50% [70/30] | ALL | 157 (1.6%) | +0.016 | +0.381 | +0.053 | +0.030 (0.15) | +0.034 | +0.057 | +0.062 | 0.97 | +1969/+791 | CANDIDATE-RECENT |
| anyk:cls=PIV:k=5:D=40 | size 67% [market] | ALL | 157 (1.6%) | +0.008 | +0.278 | +0.034 | +0.018 (0.10) | +0.025 | +0.035 | +0.043 | 0.97 | -1362/-3534 | CANDIDATE-RECENT |
| anyk:cls=PIV:k=5:D=40 | size 67% [70/30] | ALL | 157 (1.6%) | +0.011 | +0.252 | +0.035 | +0.020 (0.10) | +0.022 | +0.037 | +0.040 | 0.96 | +152/-898 | CANDIDATE-RECENT |
| wscore:D=10:q=0.9 | skip [market] | DN | 53 (7.6%) | +0.257 | +0.612 | -0.093 | +0.408 (1.83) | +0.451 | +0.951 | +0.918 | 0.94 | / | CANDIDATE-RECENT |
| wscore:D=10:q=0.9 | size 50% [market] | DN | 53 (7.6%) | +0.128 | +0.306 | -0.046 | +0.204 (0.91) | +0.226 | +0.457 | +0.440 | 0.90 | / | CANDIDATE-RECENT |
| wscore:D=10:q=0.9 | size 50% [70/30] | DN | 53 (7.6%) | +0.159 | +0.335 | -0.039 | +0.213 (0.90) | +0.244 | +0.440 | +0.429 | 0.94 | / | CANDIDATE-RECENT |
| wscore:D=10:q=0.9 | size 67% [market] | DN | 53 (7.6%) | +0.085 | +0.202 | -0.031 | +0.135 (0.60) | +0.149 | +0.298 | +0.286 | 0.94 | / | CANDIDATE-RECENT |
| wscore:D=10:q=0.9 | size 67% [70/30] | DN | 53 (7.6%) | +0.105 | +0.221 | -0.026 | +0.140 (0.59) | +0.161 | +0.286 | +0.279 | 0.93 | / | CANDIDATE-RECENT |
| wscore:D=20:q=0.8 | skip [market] | DN | 110 (15.7%) | +0.331 | +0.816 | -0.957 | +0.545 (2.80) | +0.974 | +1.807 | +2.179 | 0.98 | / | CANDIDATE-RECENT |
| wscore:D=20:q=0.8 | skip [market] | HM | 151 (16.6%) | +0.202 | +0.745 | -0.349 | +0.081 (2.33) | +0.180 | +1.041 | +1.038 | 0.94 | +15245/+13322 | CANDIDATE-RECENT |
| wscore:D=20:q=0.8 | skip [70/30] | DN | 110 (15.7%) | +0.452 | +0.770 | -0.952 | +0.568 (2.80) | +1.010 | +1.711 | +2.084 | 0.98 | / | CANDIDATE-RECENT |
| wscore:D=20:q=0.8 | skip [70/30] | HM | 151 (16.6%) | +0.146 | +0.531 | -0.208 | +0.242 (2.24) | +0.308 | +1.140 | +1.127 | 0.93 | +16220/+14617 | CANDIDATE-RECENT |
| wscore:D=20:q=0.8 | size 50% [market] | DN | 110 (15.7%) | +0.166 | +0.408 | -0.479 | +0.273 (1.40) | +0.487 | +0.827 | +0.989 | 0.98 | / | CANDIDATE-RECENT |
| wscore:D=20:q=0.8 | size 50% [market] | HM | 151 (16.6%) | +0.101 | +0.372 | -0.175 | +0.041 (1.17) | +0.090 | +0.473 | +0.467 | 0.94 | +6827/+5097 | CANDIDATE-RECENT |
| wscore:D=20:q=0.8 | size 50% [70/30] | DN | 110 (15.7%) | +0.226 | +0.385 | -0.476 | +0.284 (1.40) | +0.505 | +0.782 | +0.945 | 0.97 | / | CANDIDATE-RECENT |
| wscore:D=20:q=0.8 | size 50% [70/30] | HM | 151 (16.6%) | +0.073 | +0.266 | -0.104 | +0.121 (1.12) | +0.154 | +0.519 | +0.508 | 0.92 | +7343/+6241 | CANDIDATE-RECENT |
| wscore:D=20:q=0.8 | size 67% [market] | DN | 110 (15.7%) | +0.109 | +0.269 | -0.316 | +0.180 (0.92) | +0.321 | +0.530 | +0.633 | 0.95 | / | CANDIDATE-RECENT |
| wscore:D=20:q=0.8 | size 67% [70/30] | DN | 110 (15.7%) | +0.149 | +0.254 | -0.314 | +0.187 (0.92) | +0.333 | +0.501 | +0.604 | 0.96 | / | CANDIDATE-RECENT |
| wscore:D=20:q=0.8 | size 67% [70/30] | HM | 151 (16.6%) | +0.048 | +0.175 | -0.069 | +0.080 (0.74) | +0.102 | +0.332 | +0.324 | 0.95 | +6656/+5077 | CANDIDATE-RECENT |
| wscore:D=20:q=0.9 | skip [market] | DN | 42 (6.0%) | +0.729 | +1.081 | -0.521 | +0.441 (1.86) | +0.483 | +0.867 | +0.879 | 0.94 | / | CANDIDATE-RECENT |
| wscore:D=20:q=0.9 | skip [70/30] | DN | 42 (6.0%) | +0.817 | +0.999 | -0.555 | +0.414 (1.87) | +0.477 | +0.800 | +0.824 | 0.94 | / | CANDIDATE-RECENT |
| wscore:D=20:q=0.9 | size 50% [market] | DN | 42 (6.0%) | +0.364 | +0.540 | -0.260 | +0.221 (0.93) | +0.242 | +0.420 | +0.424 | 0.94 | / | CANDIDATE-RECENT |
| wscore:D=20:q=0.9 | size 50% [70/30] | DN | 42 (6.0%) | +0.408 | +0.500 | -0.277 | +0.207 (0.93) | +0.239 | +0.387 | +0.398 | 0.92 | / | CANDIDATE-RECENT |
| wscore:D=20:q=0.9 | size 67% [market] | DN | 42 (6.0%) | +0.240 | +0.357 | -0.172 | +0.146 (0.61) | +0.160 | +0.274 | +0.277 | 0.94 | / | CANDIDATE-RECENT |
| wscore:D=20:q=0.9 | size 67% [70/30] | DN | 42 (6.0%) | +0.269 | +0.330 | -0.183 | +0.137 (0.62) | +0.158 | +0.253 | +0.259 | 0.94 | / | CANDIDATE-RECENT |

## 6. Learned walk-forward policy (LightGBM depth 3, monthly refit on trades closed before the refit; prereg B3)
Model quality of P(target) out of sample (AUC; Brier vs the unconditional; top / bottom decile predicted vs realised):

| feature set | window | n | AUC | Brier / uncond. | top decile p / y | bottom decile p / y |
|--|--|--|--|--|--|--|
| S | L3M | 5518 | 0.536 | 0.2481 / 0.2496 | 0.60 / 0.56 | 0.42 / 0.44 |
| S | L6M | 9741 | 0.530 | 0.2485 / 0.2495 | 0.60 / 0.56 | 0.40 / 0.42 |
| S | HOLD | 10803 | 0.539 | 0.2481 / 0.2497 | 0.60 / 0.56 | 0.40 / 0.40 |
| S | PRE | 24644 | 0.544 | 0.2486 / 0.2498 | 0.62 / 0.56 | 0.37 / 0.39 |
| S | X | 6486 | 0.559 | 0.2513 / 0.2503 | 0.64 / 0.54 | 0.27 / 0.35 |
| SB | L3M | 5518 | 0.536 | 0.2478 / 0.2496 | 0.60 / 0.61 | 0.42 / 0.42 |
| SB | L6M | 9741 | 0.531 | 0.2482 / 0.2495 | 0.60 / 0.60 | 0.40 / 0.41 |
| SB | HOLD | 10803 | 0.540 | 0.2478 / 0.2497 | 0.60 / 0.59 | 0.40 / 0.40 |
| SB | PRE | 24644 | 0.539 | 0.2489 / 0.2498 | 0.62 / 0.58 | 0.38 / 0.41 |
| SB | X | 6486 | 0.553 | 0.2511 / 0.2503 | 0.62 / 0.52 | 0.28 / 0.38 |
| P | L3M | 5518 | 0.546 | 0.2474 / 0.2496 | 0.60 / 0.60 | 0.43 / 0.43 |
| P | L6M | 9741 | 0.535 | 0.2481 / 0.2495 | 0.59 / 0.61 | 0.41 / 0.43 |
| P | HOLD | 10803 | 0.541 | 0.2478 / 0.2497 | 0.59 / 0.61 | 0.41 / 0.42 |
| P | PRE | 24644 | 0.540 | 0.2486 / 0.2498 | 0.60 / 0.57 | 0.39 / 0.40 |
| P | X | 6486 | 0.556 | 0.2504 / 0.2503 | 0.63 / 0.56 | 0.30 / 0.39 |
| PB | L3M | 5518 | 0.545 | 0.2475 / 0.2496 | 0.59 / 0.60 | 0.43 / 0.41 |
| PB | L6M | 9741 | 0.536 | 0.2480 / 0.2495 | 0.59 / 0.61 | 0.41 / 0.42 |
| PB | HOLD | 10803 | 0.542 | 0.2477 / 0.2497 | 0.59 / 0.60 | 0.41 / 0.41 |
| PB | PRE | 24644 | 0.538 | 0.2488 / 0.2498 | 0.60 / 0.56 | 0.39 / 0.40 |
| PB | X | 6486 | 0.547 | 0.2516 / 0.2503 | 0.62 / 0.54 | 0.30 / 0.43 |

S = signal quality + session + HTF flags; SB = S + order book at the signal; P = S + POI aggregates; PB = SB + POI aggregates. The POI features add AUC +0.00 to +0.01 at most (P vs S, PB vs SB), inside noise.

POI contribution against the shuffled-POI placebo (10 refits with the POI aggregates permuted across trades within book x session x month; pooled scope, market base, gain per signal N; rank = share of shuffled draws below the real POI gain difference):

| set vs ref | policy | window | gain (set) | gain (ref) | real delta | shuffled mean (sd) | rank |
|--|--|--|--|--|--|--|--|
| P vs S | skip10 | L3M | +0.091 | +0.066 | +0.025 | +0.147 (0.134) | 0.30 |
| P vs S | skip10 | L6M | -0.205 | -0.166 | -0.039 | +0.033 (0.113) | 0.30 |
| P vs S | skip10 | HOLD | -0.094 | -0.011 | -0.083 | +0.058 (0.101) | 0.10 |
| P vs S | skip10 | SEL | +0.017 | -0.023 | +0.040 | -0.007 (0.022) | 1.00 |
| P vs S | skip20 | L3M | -0.108 | +0.015 | -0.123 | +0.069 (0.190) | 0.10 |
| P vs S | skip20 | L6M | -0.897 | -0.639 | -0.259 | +0.147 (0.127) | 0.00 |
| P vs S | skip20 | HOLD | -0.550 | -0.264 | -0.287 | +0.122 (0.148) | 0.00 |
| P vs S | skip20 | SEL | -0.090 | -0.069 | -0.021 | -0.033 (0.025) | 0.60 |
| P vs S | size_dn20 | L3M | -0.054 | +0.008 | -0.061 | +0.035 (0.095) | 0.10 |
| P vs S | size_dn20 | L6M | -0.449 | -0.319 | -0.129 | +0.073 (0.064) | 0.00 |
| P vs S | size_dn20 | HOLD | -0.275 | -0.132 | -0.143 | +0.061 (0.074) | 0.00 |
| P vs S | size_dn20 | SEL | -0.045 | -0.034 | -0.010 | -0.017 (0.013) | 0.60 |
| P vs S | size_ud20 | L3M | -0.155 | -0.010 | -0.145 | +0.127 (0.077) | 0.00 |
| P vs S | size_ud20 | L6M | -0.487 | -0.357 | -0.130 | +0.212 (0.088) | 0.00 |
| P vs S | size_ud20 | HOLD | -0.307 | -0.192 | -0.115 | +0.192 (0.093) | 0.00 |
| P vs S | size_ud20 | SEL | +0.026 | +0.090 | -0.064 | -0.006 (0.044) | 0.10 |
| PB vs SB | skip10 | L3M | +0.030 | +0.359 | -0.329 | -0.110 (0.087) | 0.00 |
| PB vs SB | skip10 | L6M | -0.097 | -0.037 | -0.060 | +0.004 (0.074) | 0.30 |
| PB vs SB | skip10 | HOLD | -0.036 | +0.182 | -0.218 | -0.030 (0.062) | 0.00 |
| PB vs SB | skip10 | SEL | -0.000 | -0.058 | +0.058 | +0.050 (0.041) | 0.40 |
| PB vs SB | skip20 | L3M | +0.101 | +0.071 | +0.030 | +0.032 (0.159) | 0.60 |
| PB vs SB | skip20 | L6M | -0.563 | -0.622 | +0.059 | +0.086 (0.114) | 0.40 |
| PB vs SB | skip20 | HOLD | -0.292 | -0.209 | -0.082 | +0.013 (0.150) | 0.30 |
| PB vs SB | skip20 | SEL | -0.138 | -0.185 | +0.046 | +0.076 (0.073) | 0.30 |
| PB vs SB | size_dn20 | L3M | +0.051 | +0.035 | +0.015 | +0.016 (0.079) | 0.60 |
| PB vs SB | size_dn20 | L6M | -0.282 | -0.311 | +0.030 | +0.043 (0.057) | 0.40 |
| PB vs SB | size_dn20 | HOLD | -0.146 | -0.105 | -0.041 | +0.007 (0.075) | 0.30 |
| PB vs SB | size_dn20 | SEL | -0.069 | -0.092 | +0.023 | +0.038 (0.036) | 0.30 |
| PB vs SB | size_ud20 | L3M | +0.028 | -0.113 | +0.141 | +0.243 (0.114) | 0.30 |
| PB vs SB | size_ud20 | L6M | -0.304 | -0.352 | +0.048 | +0.187 (0.071) | 0.00 |
| PB vs SB | size_ud20 | HOLD | -0.151 | -0.157 | +0.006 | +0.135 (0.083) | 0.00 |
| PB vs SB | size_ud20 | SEL | +0.025 | -0.001 | +0.027 | +0.061 (0.054) | 0.30 |

Selected learned cells (41 = 32 cells x scopes passing the PRE u X' rule); tiers: DEAD 28, LEAD 12, CANDIDATE-RECENT 1; pooled (ALL) scope: no cell is positive in both PRE and X' with a usable fire count except size_ud20 on S/SB (which is the scaling effect: its per-contract delta is negative in L6M and the placebo rank 0.1-0.3). Per-book selected cells:

| cell | scope | fires L6M | PRE | X' | L3M | L6M (MDE) | HOLD | per contract L6M | per contract HOLD | placebo | stack | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| L:S:size_dn20:MKT | HM | 200 (22.0%) | +0.094 | +0.007 | +0.369 | -0.337 (1.43) | -0.039 | +0.207 | +0.440 | 0.40 | -2516/-1866 | DEAD |
| L:PB:size_dn20:MKT | MV | 228 (20.2%) | +0.144 | +0.156 | +0.136 | +0.145 (1.20) | +0.327 | +0.417 | +0.567 | 0.77 | / | LEAD |
| L:S:size_dn20:MKT | MV | 259 (22.9%) | +0.067 | +0.303 | -0.022 | -0.256 (1.18) | -0.032 | +0.006 | +0.176 | 0.29 | / | DEAD |
| L:SB:size_dn20:SPL | MA | 73 (17.9%) | +0.138 | +0.038 | -1.799 | -1.521 (1.39) | -1.088 | -1.070 | -0.651 | 0.18 | / | DEAD |
| L:PB:size_dn20:SPL | MV | 228 (20.2%) | +0.082 | +0.138 | +0.135 | +0.164 (1.16) | +0.347 | +0.437 | +0.586 | 0.74 | / | LEAD |
| L:S:size_dn20:SPL | MV | 259 (22.9%) | +0.014 | +0.247 | -0.027 | -0.243 (1.17) | -0.009 | +0.021 | +0.202 | 0.27 | / | DEAD |
| L:PB:size_dn20:SPL | SM | 54 (17.2%) | +0.042 | +0.124 | -0.512 | -0.086 (2.44) | -0.264 | +0.209 | +0.198 | 0.55 | +964/+408 | DEAD |
| L:SB:size_ud20:MKT | MA | 113 (27.8%) | +0.098 | +0.045 | -2.193 | -1.776 (1.60) | -1.312 | -1.565 | -1.040 | 0.08 | / | DEAD |
| L:S:size_ud20:MKT | MV | 361 (31.9%) | +0.270 | +0.089 | +0.211 | -0.343 (1.27) | -0.111 | -0.198 | +0.015 | 0.12 | / | DEAD |
| L:SB:size_ud20:MKT | PB | 284 (32.8%) | +0.248 | +0.370 | -0.400 | -0.585 (1.50) | -0.395 | -0.031 | +0.176 | 0.09 | / | DEAD |
| L:S:size_ud20:MKT | PB | 270 (31.2%) | +0.056 | +0.388 | +0.244 | -0.463 (1.59) | -0.348 | +0.084 | +0.176 | 0.20 | / | DEAD |
| L:PB:size_ud20:MKT | SM | 81 (25.8%) | +0.421 | +0.247 | -1.094 | -0.062 (2.69) | -0.257 | +0.041 | -0.045 | 0.31 | +532/-108 | DEAD |
| L:PB:size_ud20:MKT | WT | 1490 (87.3%) | +0.355 | +0.322 | +0.779 | +0.738 (1.09) | +0.721 | -0.012 | +0.166 | 0.47 | -5342/-3985 | LEAD |
| L:P:size_ud20:MKT | WT | 1510 (88.5%) | +0.320 | +0.352 | +0.703 | +0.672 (1.14) | +0.650 | -0.063 | +0.110 | 0.34 | -1850/-842 | LEAD |
| L:S:size_ud20:MKT | WT | 1514 (88.7%) | +0.387 | +0.145 | +0.681 | +0.728 (1.11) | +0.517 | -0.032 | +0.012 | 0.49 | -4247/-2683 | LEAD |
| L:SB:size_ud20:SPL | MA | 113 (27.8%) | +0.068 | +0.174 | -2.417 | -1.877 (1.54) | -1.394 | -1.708 | -1.171 | 0.07 | / | DEAD |
| L:S:size_ud20:SPL | MV | 361 (31.9%) | +0.215 | +0.024 | +0.200 | -0.338 (1.27) | -0.094 | -0.192 | +0.033 | 0.16 | / | DEAD |
| L:SB:size_ud20:SPL | PB | 284 (32.8%) | +0.321 | +0.311 | -0.463 | -0.568 (1.51) | -0.393 | +0.030 | +0.234 | 0.11 | / | DEAD |
| L:S:size_ud20:SPL | PB | 270 (31.2%) | +0.173 | +0.306 | +0.157 | -0.511 (1.54) | -0.401 | +0.071 | +0.166 | 0.18 | / | DEAD |
| L:PB:size_ud20:SPL | SM | 81 (25.8%) | +0.423 | +0.142 | -1.131 | -0.056 (2.69) | -0.238 | +0.087 | +0.035 | 0.28 | +414/-73 | DEAD |
| L:PB:size_ud20:SPL | WT | 1490 (87.3%) | +0.373 | +0.245 | +0.664 | +0.693 (1.05) | +0.644 | -0.070 | +0.083 | 0.40 | -4251/-3337 | LEAD |
| L:P:size_ud20:SPL | WT | 1510 (88.5%) | +0.359 | +0.304 | +0.592 | +0.651 (1.09) | +0.595 | -0.105 | +0.043 | 0.32 | -2839/-1662 | LEAD |
| L:S:size_ud20:SPL | WT | 1514 (88.7%) | +0.428 | +0.059 | +0.595 | +0.743 (1.07) | +0.525 | -0.048 | -0.011 | 0.53 | -2644/-1193 | LEAD |
| L:PB:skip10:MKT | DN | 50 (7.1%) | +0.527 | +0.104 | -0.248 | -1.029 (1.55) | -1.260 | -0.629 | -0.914 | 0.21 | / | DEAD |
| L:P:skip10:MKT | DN | 49 (7.0%) | +0.472 | +0.164 | -0.256 | -1.032 (1.58) | -0.983 | -0.640 | -0.622 | 0.21 | / | DEAD |
| L:S:skip10:MKT | DN | 50 (7.1%) | +0.671 | +0.456 | +1.013 | -0.344 (1.66) | -0.379 | +0.108 | +0.002 | 0.74 | / | DEAD |
| L:SB:skip10:MKT | MV | 125 (11.1%) | +0.052 | +0.151 | +1.343 | +0.557 (1.50) | +0.530 | +0.910 | +0.824 | 0.93 | / | CANDIDATE-RECENT |
| L:S:skip10:MKT | MV | 122 (10.8%) | +0.258 | +0.263 | +0.638 | +0.478 (1.26) | +0.517 | +0.811 | +0.791 | 0.81 | / | LEAD |
| L:P:skip10:MKT | SM | 29 (9.2%) | +0.126 | +0.227 | -1.580 | -0.769 (3.28) | -0.759 | -0.607 | -0.454 | 0.17 | -243/-332 | DEAD |
| L:PB:skip10:SPL | DN | 50 (7.1%) | +0.596 | +0.191 | -0.239 | -0.977 (1.55) | -1.182 | -0.637 | -0.908 | 0.25 | / | DEAD |
| L:P:skip10:SPL | DN | 49 (7.0%) | +0.539 | +0.203 | -0.240 | -0.979 (1.56) | -0.926 | -0.646 | -0.636 | 0.17 | / | DEAD |
| L:S:skip10:SPL | DN | 50 (7.1%) | +0.755 | +0.527 | +1.030 | -0.314 (1.62) | -0.314 | +0.082 | +0.006 | 0.65 | / | DEAD |
| L:S:skip10:SPL | MV | 122 (10.8%) | +0.213 | +0.306 | +0.622 | +0.483 (1.26) | +0.525 | +0.813 | +0.795 | 0.83 | / | LEAD |
| L:P:skip10:SPL | SM | 29 (9.2%) | +0.173 | +0.232 | -1.658 | -0.772 (3.30) | -0.771 | -0.518 | -0.364 | 0.20 | -215/-322 | DEAD |
| L:S:skip20:MKT | HM | 200 (22.0%) | +0.188 | +0.013 | +0.738 | -0.675 (2.86) | -0.077 | +0.471 | +1.014 | 0.47 | -258/+1267 | DEAD |
| L:PB:skip20:MKT | MV | 228 (20.2%) | +0.289 | +0.312 | +0.273 | +0.290 (2.40) | +0.655 | +0.939 | +1.305 | 0.76 | / | LEAD |
| L:S:skip20:MKT | MV | 259 (22.9%) | +0.135 | +0.606 | -0.044 | -0.511 (2.36) | -0.065 | +0.014 | +0.410 | 0.20 | / | DEAD |
| L:SB:skip20:SPL | MA | 73 (17.9%) | +0.276 | +0.075 | -3.599 | -3.042 (2.77) | -2.176 | -2.373 | -1.475 | 0.15 | / | DEAD |
| L:PB:skip20:SPL | MV | 228 (20.2%) | +0.164 | +0.275 | +0.270 | +0.329 (2.33) | +0.694 | +0.983 | +1.347 | 0.76 | / | LEAD |
| L:S:skip20:SPL | MV | 259 (22.9%) | +0.029 | +0.495 | -0.055 | -0.487 (2.34) | -0.017 | +0.049 | +0.469 | 0.32 | / | DEAD |
| L:PB:skip20:SPL | SM | 54 (17.2%) | +0.083 | +0.248 | -1.024 | -0.172 (4.88) | -0.528 | +0.461 | +0.443 | 0.45 | +1044/+326 | DEAD |

Would a simpler rule do the same? Best 1- and 2-feature POI-aggregate skip rule fitted on PRE u X' (target = -net N, so firing = skipping), evaluated out of sample:

|   k | rule                                             |   fit_mean |   fit_n |   eval_mean |   eval_n |   n_rules_searched | eval_win   |
|----:|:-------------------------------------------------|-----------:|--------:|------------:|---------:|-------------------:|:-----------|
|   1 | poi_BOS_htf_bh_n > 0                             |      3.042 |    2238 |      -2.522 |      569 |               1180 | L6M        |
|   2 | poi_BOS_htf_bh_n > 0 AND poi_BOS_htf_bh_min < 99 |      3.042 |    2238 |      -2.522 |      569 |               1285 | L6M        |
|   1 | poi_BOS_htf_bh_n > 0                             |      3.042 |    2238 |      -1.03  |      660 |               1180 | HOLD       |
|   2 | poi_BOS_htf_bh_n > 0 AND poi_BOS_htf_bh_min < 99 |      3.042 |    2238 |      -1.03  |      660 |               1285 | HOLD       |
|   1 | poi_BOS_htf_bh_n > 0                             |      3.042 |    2238 |       2.814 |      230 |               1180 | L3M        |
|   2 | poi_BOS_htf_bh_n > 0 AND poi_BOS_htf_bh_min < 99 |      3.042 |    2238 |       2.814 |      230 |               1285 | L3M        |

Feature attribution by quarter (set P; top-5 gain share; the POI features' summed gain share is 0.56-0.71 only because ~200 POI columns share noise splits; the single biggest features are minute-of-day, session, VIX, ATR, book):

|        | 0          | 1            | 2            | 3            | 4                       |
|:-------|:-----------|:-------------|:-------------|:-------------|:------------------------|
| 2023Q3 | vix (0.09) | mod (0.06)   | dow (0.04)   | atr15 (0.03) | poi_PIV_na_ah_n (0.03)  |
| 2023Q4 | vix (0.07) | mod (0.06)   | atr15 (0.05) | sess (0.04)  | poi_SWG_ltf_bh_n (0.04) |
| 2024Q1 | mod (0.07) | atr15 (0.05) | sess (0.05)  | vix (0.05)   | poi_SWG_ltf_bh_n (0.04) |
| 2024Q2 | mod (0.06) | sess (0.06)  | atr15 (0.06) | vix (0.03)   | poi_SWG_ltf_bh_n (0.03) |
| 2024Q3 | mod (0.08) | sess (0.08)  | atr15 (0.06) | book (0.03)  | dow (0.03)              |
| 2024Q4 | mod (0.09) | sess (0.09)  | atr15 (0.06) | dow (0.05)   | book (0.04)             |
| 2025Q1 | mod (0.11) | sess (0.09)  | dow (0.04)   | book (0.04)  | atr15 (0.04)            |
| 2025Q2 | mod (0.10) | sess (0.09)  | vix (0.04)   | book (0.04)  | td (0.03)               |
| 2025Q3 | mod (0.11) | sess (0.10)  | vix (0.05)   | book (0.04)  | atr15 (0.04)            |
| 2025Q4 | mod (0.12) | sess (0.10)  | vix (0.06)   | book (0.04)  | poi_SWG_ltf_bh_n (0.04) |
| 2026Q1 | mod (0.12) | sess (0.11)  | vix (0.05)   | book (0.05)  | td (0.04)               |

## 7. Program-level validity (QUANT-LAYER): White RC / Romano-Wolf / PBO / min backtest length per family, weekly PRE u X' gains of ALL cells

| program   | grp              |   n_cells |   rc_p_best |   rc_p_stud |   n_rw_survivors |   best_t |   pbo |   n_eff |   min_btl_years |   rc_p_cum_sidak |   n_cum |
|:----------|:-----------------|----------:|------------:|------------:|-----------------:|---------:|------:|--------:|----------------:|-----------------:|--------:|
| B         | b73|MKT          |      5578 |       0.992 |       0.845 |                0 |    2.951 | 0.222 |  52.298 |          13.805 |                1 |  274530 |
| B         | rs20|MKT         |      5578 |       0.965 |       0.082 |                0 |    3.924 | 0.385 |  33.013 |          13.805 |                1 |  274530 |
| B         | rs20|SPL         |      5578 |       0.98  |       0.125 |                0 |    3.799 | 0.456 |  33.212 |          13.805 |                1 |  274530 |
| B         | rs30|MKT         |      5578 |       0.988 |       0.085 |                0 |    3.814 | 0.381 |  31.904 |          13.805 |                1 |  274530 |
| B         | rs30|SPL         |      5578 |       1     |       0.137 |                0 |    3.706 | 0.456 |  31.993 |          13.805 |                1 |  274530 |
| B         | rt|MKT           |      5578 |       0.912 |       0.132 |                0 |    3.813 | 0.337 |  36.383 |          13.805 |                1 |  274530 |
| B         | rt|SPL           |      5578 |       0.898 |       0.227 |                0 |    3.647 | 0.397 |  36.537 |          13.805 |                1 |  274530 |
| B         | skip|MKT         |     12630 |       0.992 |       0.175 |                0 |    3.827 | 0.381 |  25.131 |          15.346 |                1 |  274530 |
| B         | skip|SPL         |     12630 |       0.992 |       0.2   |                0 |    3.762 | 0.385 |  25.241 |          15.346 |                1 |  274530 |
| B         | ts|MKT           |      1578 |       0.712 |       0.204 |                0 |    3.246 | 0.361 |  39.304 |          11.442 |                1 |  274530 |
| B         | ts|SPL           |      1578 |       0.73  |       0.239 |                0 |    3.216 | 0.448 |  39.637 |          11.442 |                1 |  274530 |
| B         | u150|MKT         |      1994 |       0.008 |       0.097 |                0 |    3.72  | 0.81  |  20.94  |          11.878 |                1 |  274530 |
| B         | u150|SPL         |      1994 |       0.01  |       0.075 |                0 |    3.75  | 0.806 |  20.996 |          11.878 |                1 |  274530 |
| B         | wt|MKT           |      5578 |       0.992 |       0.421 |                0 |    3.415 | 0.373 |  57.237 |          13.805 |                1 |  274530 |
| B         | z50|MKT          |     12630 |       0.992 |       0.175 |                0 |    3.827 | 0.381 |  25.131 |          15.346 |                1 |  274530 |
| B         | z50|SPL          |     12630 |       0.992 |       0.2   |                0 |    3.762 | 0.385 |  25.241 |          15.346 |                1 |  274530 |
| B         | z67|MKT          |     12630 |       0.992 |       0.175 |                0 |    3.827 | 0.381 |  25.131 |          15.346 |                1 |  274530 |
| B         | z67|SPL          |     12630 |       0.992 |       0.2   |                0 |    3.762 | 0.385 |  25.241 |          15.346 |                1 |  274530 |
| B2        | anyk|skip|MKT    |       526 |       0.882 |       0.793 |                0 |    2.066 | 0.143 |   6.227 |           9.411 |                1 |  274530 |
| B2        | anyk|skip|SPL    |       526 |       0.89  |       0.743 |                0 |    2.168 | 0.139 |   6.303 |           9.411 |                1 |  274530 |
| B2        | anyk|z50|MKT     |       526 |       0.882 |       0.793 |                0 |    2.066 | 0.143 |   6.227 |           9.411 |                1 |  274530 |
| B2        | anyk|z50|SPL     |       526 |       0.89  |       0.743 |                0 |    2.168 | 0.139 |   6.303 |           9.411 |                1 |  274530 |
| B2        | anyk|z67|MKT     |       526 |       0.882 |       0.793 |                0 |    2.066 | 0.143 |   6.227 |           9.411 |                1 |  274530 |
| B2        | anyk|z67|SPL     |       526 |       0.89  |       0.743 |                0 |    2.168 | 0.139 |   6.303 |           9.411 |                1 |  274530 |
| B2        | fourleg|skip|MKT |        12 |       0.798 |       0.803 |                0 |   -0.149 | 0.06  |   1.513 |           2.772 |                1 |  274530 |
| B2        | fourleg|skip|SPL |        12 |       0.828 |       0.853 |                0 |   -0.268 | 0.087 |   1.52  |           2.772 |                1 |  274530 |
| B2        | fourleg|z50|MKT  |        12 |       0.798 |       0.803 |                0 |   -0.149 | 0.06  |   1.513 |           2.772 |                1 |  274530 |
| B2        | fourleg|z50|SPL  |        12 |       0.828 |       0.853 |                0 |   -0.268 | 0.087 |   1.52  |           2.772 |                1 |  274530 |
| B2        | fourleg|z67|MKT  |        12 |       0.798 |       0.803 |                0 |   -0.149 | 0.06  |   1.513 |           2.772 |                1 |  274530 |
| B2        | fourleg|z67|SPL  |        12 |       0.828 |       0.853 |                0 |   -0.268 | 0.087 |   1.52  |           2.772 |                1 |  274530 |
| B2        | time|skip|MKT    |        14 |       0.718 |       0.2   |                0 |    2.055 | 0.206 |   8.709 |           3.022 |                1 |  274530 |
| B2        | time|skip|SPL    |        14 |       0.715 |       0.162 |                0 |    2.174 | 0.218 |   8.771 |           3.022 |                1 |  274530 |
| B2        | time|z50|MKT     |        14 |       0.718 |       0.2   |                0 |    2.055 | 0.206 |   8.709 |           3.022 |                1 |  274530 |
| B2        | time|z50|SPL     |        14 |       0.715 |       0.162 |                0 |    2.174 | 0.218 |   8.771 |           3.022 |                1 |  274530 |
| B2        | time|z67|MKT     |        14 |       0.718 |       0.2   |                0 |    2.055 | 0.206 |   8.709 |           3.022 |                1 |  274530 |
| B2        | time|z67|SPL     |        14 |       0.715 |       0.162 |                0 |    2.174 | 0.218 |   8.771 |           3.022 |                1 |  274530 |
| B2        | wscore|skip|MKT  |         9 |       0.012 |       0.002 |                4 |    4.238 | 0.06  |   2.075 |           2.313 |                1 |  274530 |
| B2        | wscore|skip|SPL  |         9 |       0.02  |       0.002 |                3 |    4.077 | 0.056 |   2.066 |           2.313 |                1 |  274530 |
| B2        | wscore|z50|MKT   |         9 |       0.012 |       0.002 |                4 |    4.238 | 0.06  |   2.075 |           2.313 |                1 |  274530 |
| B2        | wscore|z50|SPL   |         9 |       0.02  |       0.002 |                3 |    4.077 | 0.056 |   2.066 |           2.313 |                1 |  274530 |
| B2        | wscore|z67|MKT   |         9 |       0.012 |       0.002 |                4 |    4.238 | 0.06  |   2.075 |           2.313 |                1 |  274530 |
| B2        | wscore|z67|SPL   |         9 |       0.02  |       0.002 |                3 |    4.077 | 0.056 |   2.066 |           2.313 |                1 |  274530 |

## 8. Detail for the CANDIDATE-RECENT cells that fire >= 30 times in L6M and HOLD, and for the best selected cell of each family (TOP): per-contract CI, MDE, concentration, capacity, drift, sessions, stack MDE
Top5 = share of the gain from the best 5% of fired signals; breakeven = mean gain per fired signal (the slippage per changed order at which the rule's gain is zero); capacity = 25% of the median top-5 resting size on the side the entry trades against at the signal second (contracts; the live book trades 5-10 lots); quarters+ = quarters (of 12) with positive gain per signal.

| src | cell | scope | kept share | fires/wk L6M | per contract L6M [CI] (MDE) | gain/signal L6M (MDE) | HOLD | L3M | top5 share | breakeven pt | capacity | quarters+ | halves L6M (h1/h2) | stack L6M (MDE) / HOLD | stack corr | kind |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| B | re-target to POI-2t [70/30] - AHEAD ARR:FVG:1h (unmitigated) within 40pts | HM | 93.8% | 2.0 | +0.333 [-0.482, +1.379] (1.36) | +0.322 (1.43) | +0.378 | +0.638 | +0.96 | +5.23 | +4.5 | 11/12 | -0.22/+0.87 | +4429 (9101) / +3655 | -0.13 | SEL |
| B | size 150% (POI behind) [market] - BEHIND ARR:BRK_CE:3m (unmitigated) within 20pts | SM | 86.0% | 1.6 | +1.057 [-0.070, +2.170] (1.56) | +1.297 (1.77) | +1.029 | +0.684 | +0.22 | +9.25 | +3.8 | 9/11 | +2.25/+0.34 | +1789 (3110) / +1654 | +0.08 | SEL |
| B | size 150% (POI behind) [70/30] - BEHIND ARR:BRK_CE:3m (unmitigated) within 20pts | SM | 86.0% | 1.6 | +0.959 [-0.161, +2.016] (1.53) | +1.255 (1.75) | +0.998 | +0.608 | +0.23 | +8.96 | +3.8 | 10/11 | +2.25/+0.26 | +1738 (3074) / +1476 | +0.04 | SEL |
| B | size 150% (POI behind) [70/30] - BEHIND PRF:b2:day (unmitigated) within 1xATR15 | ALL | 72.6% | 95.4 | +0.155 [-0.082, +0.448] (0.38) | +0.623 (0.73) | +0.544 | +0.565 | +0.68 | +2.27 | +4.0 | 11/12 | +0.85/+0.39 | +11038 (24744) / +10112 | -0.02 | SEL |
| B | skip [70/30] - AHEAD FIB:ret50:15m (any) within 10pts | WT | 95.3% | 2.9 | +0.340 [-0.050, +0.735] (0.58) | +0.234 (0.53) | +0.236 | +0.039 | +0.58 | +4.93 | +4.0 | 8/12 | +0.45/+0.02 | +2284 (3624) / +2400 | -0.02 | SEL |
| B | wait for trade-through [market] - AHEAD MAS:ich_kijun:4h (unmitigated) within 2xATR15 | DN | 95.6% | 1.1 | +0.698 [-0.173, +1.685] (1.36) | +0.560 (1.33) | +0.782 | +0.876 | +0.31 | +12.66 | +5.5 | 10/12 | -0.28/+1.42 |  (nan) /  |  | SEL |
| B | size 50% [70/30] - AHEAD FIB:ret50:15m (any) within 10pts | WT | 95.3% | 2.9 | +0.166 [-0.024, +0.357] (0.28) | +0.117 (0.26) | +0.118 | +0.020 | +0.58 | +2.46 | +4.0 | 8/12 | +0.23/+0.01 | +1474 (2199) / +1898 | -0.03 | SEL |
| B | size 150% (POI behind) [market] - BEHIND SWG:f7L:1m (unmitigated) within 5pts | ST | 95.1% | 2.2 | +0.337 [+0.010, +0.662] (0.46) | +0.440 (0.53) | +0.427 | +0.489 | +0.22 | +9.05 | +3.8 | 9/12 | +0.46/+0.42 | +2069 (6715) / +1981 | -0.15 | SEL |
| B | size 67% [70/30] - AHEAD FIB:ret50:15m (any) within 10pts | WT | 95.3% | 2.9 | +0.109 [-0.016, +0.233] (0.18) | +0.077 (0.17) | +0.078 | +0.013 | +0.58 | +1.63 | +4.0 | 8/12 | +0.15/+0.01 | +495 (1617) / +1072 | -0.01 | SEL |
| B | size 150% (POI behind) [market] - BEHIND SWG:f3L:2m (unmitigated) within 5pts | ST | 94.3% | 2.5 | +0.364 [-0.010, +0.705] (0.52) | +0.485 (0.60) | +0.511 | +0.484 | +0.20 | +8.57 | +3.8 | 9/12 | +0.65/+0.32 | +2106 (6903) / +2186 | -0.15 | SEL |
| B | wait for trade-through [market] - AHEAD BKS:sweep:book (unmitigated) within 1xATR15 | WT | 81.0% | 11.6 | +0.095 [-0.021, +0.237] (0.19) | +0.087 (0.17) | +0.082 | -0.005 | +2.51 | +0.46 | +3.8 | 10/12 | +0.17/+0.01 | -1204 (3293) / -1075 | +0.00 | SEL |
| B | 70% now + 30% after trade-through [market] - AHEAD BKS:sweep:book (unmitigated) within 5pts | ALL | 80.0% | 69.5 | +0.024 [-0.008, +0.057] (0.04) | +0.020 (0.05) | +0.022 | +0.034 | +4.28 | +0.10 | +3.8 | 11/12 | -0.01/+0.05 | -1174 (4828) / -773 | -0.23 | SEL |
| B | wait for trade-through [market] - AHEAD BKS:sweep:book (unmitigated) within 2xATR15 | ALL | 80.0% | 69.5 | +0.144 [+0.024, +0.267] (0.18) | +0.128 (0.19) | +0.122 | +0.168 | +2.37 | +0.64 | +3.8 | 10/12 | +0.02/+0.24 | +2399 (12846) / +1538 | -0.32 | SEL |
| B | 70% now + 30% after trade-through [market] - AHEAD BKS:sweep:book (unmitigated) within 1xATR15 | ALL | 80.0% | 69.5 | +0.024 [-0.008, +0.057] (0.04) | +0.020 (0.05) | +0.022 | +0.034 | +4.28 | +0.10 | +3.8 | 11/12 | -0.01/+0.05 | -1174 (4828) / -773 | -0.23 | SEL |
| B | wait for trade-through [market] - AHEAD BKS:sweep:book (unmitigated) within 2xATR15 | WT | 81.0% | 11.6 | +0.095 [-0.021, +0.237] (0.19) | +0.087 (0.17) | +0.082 | -0.005 | +2.51 | +0.46 | +3.8 | 10/12 | +0.17/+0.01 | -1204 (3293) / -1075 | +0.00 | SEL |
| B | wait for trade-through [market] - AHEAD BKS:sweep:book (unmitigated) within 3xATR15 | WT | 81.0% | 11.6 | +0.095 [-0.021, +0.237] (0.19) | +0.087 (0.17) | +0.082 | -0.005 | +2.51 | +0.46 | +3.8 | 10/12 | +0.17/+0.01 | -1204 (3293) / -1075 | +0.00 | SEL |
| B | wait for trade-through [market] - AHEAD BKS:sweep:book (unmitigated) within 3xATR15 | ALL | 80.0% | 69.5 | +0.144 [+0.024, +0.267] (0.18) | +0.128 (0.19) | +0.122 | +0.168 | +2.37 | +0.64 | +3.8 | 10/12 | +0.02/+0.24 | +2399 (12846) / +1538 | -0.32 | SEL |
| B | 70% now + 30% after trade-through [market] - AHEAD BKS:sweep:book (unmitigated) within 3xATR15 | ALL | 80.0% | 69.5 | +0.024 [-0.008, +0.057] (0.04) | +0.020 (0.05) | +0.022 | +0.034 | +4.28 | +0.10 | +3.8 | 11/12 | -0.01/+0.05 | -1174 (4828) / -773 | -0.23 | SEL |
| B | re-target, skip if target<20 [market] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 99.3% | 2.3 | -0.039 [-0.169, +0.068] (0.16) | -0.052 (0.15) | -0.032 | -0.128 |  | -7.99 | +4.0 | 10/12 | +0.03/-0.13 | -760 (5791) / -627 | -0.17 | TOP |
| B | skip [market] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 99.3% | 2.3 | +0.001 [-0.131, +0.111] (0.17) | -0.021 (0.16) | -0.007 | -0.088 |  | -3.17 | +4.0 | 9/12 | +0.07/-0.11 | +582 (6466) / +439 | -0.21 | TOP |
| B | size 50% [market] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 99.3% | 2.3 | +0.000 [-0.065, +0.055] (0.08) | -0.010 (0.08) | -0.003 | -0.044 |  | -1.58 | +4.0 | 9/12 | +0.03/-0.06 | -1309 (5051) / -911 | -0.34 | TOP |
| B | size 67% [70/30] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 99.3% | 2.3 | -0.002 [-0.041, +0.030] (0.05) | -0.009 (0.05) | -0.004 | -0.024 |  | -1.35 | +4.0 | 9/12 | +0.01/-0.03 | -1453 (4742) / -1042 | -0.31 | TOP |
| B | size 67% [market] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 99.3% | 2.3 | +0.000 [-0.043, +0.036] (0.06) | -0.007 (0.05) | -0.002 | -0.029 |  | -1.05 | +4.0 | 9/12 | +0.02/-0.04 | -245 (2602) / -126 | -0.41 | TOP |
| B | skip [70/30] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 99.3% | 2.3 | -0.006 [-0.125, +0.090] (0.15) | -0.027 (0.15) | -0.013 | -0.074 |  | -4.09 | +4.0 | 9/12 | +0.04/-0.10 | -1013 (6379) / -349 | -0.20 | TOP |
| B | re-target, skip if target<20 [70/30] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 99.3% | 2.3 | -0.048 [-0.163, +0.041] (0.14) | -0.062 (0.14) | -0.041 | -0.118 |  | -9.37 | +4.0 | 9/12 | -0.00/-0.12 | -1184 (6105) / -389 | -0.22 | TOP |
| B | size 50% [70/30] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 99.3% | 2.3 | -0.003 [-0.062, +0.045] (0.08) | -0.013 (0.07) | -0.006 | -0.037 |  | -2.04 | +4.0 | 9/12 | +0.02/-0.05 | -2660 (7728) / -1890 | -0.30 | TOP |
| B | re-target, skip if target<30 [70/30] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 99.3% | 2.3 | -0.035 [-0.146, +0.064] (0.15) | -0.053 (0.14) | -0.033 | -0.087 |  | -8.08 | +4.0 | 9/12 | +0.01/-0.12 | -1013 (6379) / -239 | -0.20 | TOP |
| B | re-target, skip if target<30 [market] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 99.3% | 2.3 | -0.028 [-0.154, +0.079] (0.17) | -0.046 (0.15) | -0.026 | -0.099 |  | -6.99 | +4.0 | 9/12 | +0.04/-0.13 | +189 (6350) / +203 | -0.19 | TOP |
| B | re-target to POI-2t [market] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 99.3% | 2.3 | -0.026 [-0.142, +0.073] (0.15) | -0.026 (0.14) | -0.016 | -0.103 |  | -3.95 | +4.0 | 10/12 | +0.05/-0.11 | -488 (5489) / +85 | -0.18 | TOP |
| B | re-target to POI-2t [70/30] - AHEAD ARR:BRK:1h (unmitigated) within 0.5xATR15 | ALL | 99.3% | 2.3 | -0.036 [-0.137, +0.045] (0.13) | -0.037 (0.12) | -0.020 | -0.098 |  | -5.63 | +4.0 | 10/12 | +0.03/-0.10 | -1381 (6350) / -457 | -0.20 | TOP |
| B | wait for trade-through [market] - AHEAD PRF:hvn1:sw15 (unmitigated) within 40pts | ALL | 96.0% | 14.0 | +0.026 [-0.214, +0.289] (0.36) | -0.014 (0.32) | -0.040 | -0.114 |  | -0.35 | +4.0 | 6/12 | +0.04/-0.07 | -3872 (17338) / -5586 | -0.12 | TOP |
| B | 70% now + 30% after trade-through [market] - AHEAD BKS:sweep:book (unmitigated) within 3xATR15 | ALL | 80.0% | 69.5 | +0.024 [-0.008, +0.057] (0.04) | +0.020 (0.05) | +0.022 | +0.034 | +4.28 | +0.10 | +3.8 | 11/12 | -0.01/+0.05 | -1174 (4828) / -773 | -0.23 | TOP |
| B | 70% now + 30% after trade-through [market] - AHEAD BKS:sweep:book (unmitigated) within 5pts | ALL | 80.0% | 69.5 | +0.024 [-0.008, +0.057] (0.04) | +0.020 (0.05) | +0.022 | +0.034 | +4.28 | +0.10 | +3.8 | 11/12 | -0.01/+0.05 | -1174 (4828) / -773 | -0.23 | TOP |
| B | size 50% [market] - AHEAD PIV:cam_L4:rth (unmitigated) within 0.5xATR15 | ALL | 99.7% | 1.2 | +0.008 [-0.029, +0.043] (0.05) | +0.002 (0.06) | -0.003 | +0.008 | +2.77 | +0.65 | +5.2 | 9/12 | -0.01/+0.02 | +717 (3130) / +848 | -0.11 | TOP |
| B | skip [market] - AHEAD PIV:cam_L4:rth (unmitigated) within 0.5xATR15 | ALL | 99.7% | 1.2 | +0.016 [-0.058, +0.086] (0.11) | +0.005 (0.11) | -0.006 | +0.016 | +2.77 | +1.30 | +5.2 | 9/12 | -0.03/+0.04 | +2602 (6644) / +2424 | -0.15 | TOP |
| B | re-target, skip if target<30 [market] - AHEAD PIV:cam_L4:rth (unmitigated) within 0.5xATR15 | ALL | 99.7% | 1.2 | +0.016 [-0.049, +0.079] (0.09) | +0.006 (0.10) | -0.004 | +0.030 | +2.88 | +1.86 | +5.2 | 8/12 | -0.04/+0.05 | +2695 (6758) / +2506 | -0.16 | TOP |
| B | re-target to POI-2t [market] - AHEAD PIV:cam_L4:rth (unmitigated) within 0.5xATR15 | ALL | 99.7% | 1.2 | -0.010 [-0.070, +0.054] (0.09) | -0.010 (0.09) | -0.015 | -0.010 |  | -2.83 | +5.2 | 8/12 | -0.01/-0.01 | +2024 (4839) / +1977 | -0.16 | TOP |
| B | size 67% [market] - AHEAD PIV:cam_L4:rth (unmitigated) within 0.5xATR15 | ALL | 99.7% | 1.2 | +0.005 [-0.019, +0.028] (0.04) | +0.001 (0.04) | -0.002 | +0.005 | +2.77 | +0.43 | +5.2 | 9/12 | -0.01/+0.01 | +92 (778) / +325 | -0.02 | TOP |
| B | re-target, skip if target<20 [market] - AHEAD PIV:cam_L4:rth (unmitigated) within 0.5xATR15 | ALL | 99.7% | 1.2 | +0.002 [-0.057, +0.063] (0.09) | -0.006 (0.09) | -0.015 | +0.009 |  | -1.59 | +5.2 | 8/12 | -0.04/+0.03 | +2695 (6758) / +2506 | -0.16 | TOP |
| B | wait for trade-through [market] - AHEAD BKS:sweep:book (unmitigated) within 3xATR15 | ALL | 80.0% | 69.5 | +0.144 [+0.024, +0.267] (0.18) | +0.128 (0.19) | +0.122 | +0.168 | +2.37 | +0.64 | +3.8 | 10/12 | +0.02/+0.24 | +2399 (12846) / +1538 | -0.32 | TOP |
| B | re-target to POI-2t [70/30] - AHEAD PIV:cam_L4:rth (unmitigated) within 0.5xATR15 | ALL | 99.7% | 1.2 | -0.013 [-0.065, +0.052] (0.08) | -0.013 (0.08) | -0.019 | -0.000 |  | -3.84 | +5.2 | 9/12 | -0.03/+0.00 | +2645 (6986) / +2222 | -0.18 | TOP |
| B | tighten stop beyond POI (risk-matched) [70/30] - BEHIND PRF:b2:rth (unmitigated) within 0.25xATR15 | ALL | 96.9% | 10.8 | -0.000 [-0.001, +0.000] (0.00) | -0.000 (0.00) | -0.000 | +0.000 |  | -0.00 | +6.0 | 7/12 | -0.00/+0.00 | -2 (5) / -3 | +0.02 | TOP |
| B | tighten stop beyond POI (risk-matched) [70/30] - BEHIND ARR:FVG_CE:1h (unmitigated) within 1xATR15 | ALL | 94.5% | 19.2 | +0.031 [-0.000, +0.073] (0.06) | +0.033 (0.06) | +0.051 | +0.033 | +1.00 | +0.61 | +4.2 | 12/12 | +0.03/+0.04 | +776 (1760) / +1230 | +0.04 | TOP |
| B | tighten stop beyond POI (risk-matched) [market] - BEHIND ARR:FVG_CE:1h (unmitigated) within 1xATR15 | ALL | 94.5% | 19.2 | +0.029 [-0.000, +0.070] (0.05) | +0.032 (0.06) | +0.050 | +0.032 | +1.00 | +0.57 | +4.2 | 12/12 | +0.03/+0.04 | +921 (2199) / +1576 | +0.00 | TOP |
| B | size 67% [70/30] - AHEAD PDX:week:H (any) within 10pts | ALL | 99.1% | 3.0 | +0.015 [-0.022, +0.061] (0.06) | +0.006 (0.05) | +0.003 | +0.009 | +1.75 | +0.70 | +4.5 | 9/12 | +0.00/+0.01 | -1256 (1587) / -1185 | +0.13 | TOP |
| B | tighten stop beyond POI (risk-matched) [market] - BEHIND PRF:b2:rth (unmitigated) within 0.25xATR15 | ALL | 96.9% | 10.8 | -0.000 [-0.001, +0.000] (0.00) | -0.000 (0.00) | -0.000 | +0.000 |  | -0.00 | +6.0 | 7/12 | -0.00/+0.00 | -2 (5) / -2 | +0.01 | TOP |
| B | skip [70/30] - AHEAD PDX:week:H (any) within 10pts | ALL | 99.1% | 3.0 | +0.046 [-0.067, +0.185] (0.17) | +0.018 (0.16) | +0.010 | +0.028 | +1.75 | +2.11 | +4.5 | 9/12 | +0.00/+0.03 | -1982 (4316) / -1865 | -0.09 | TOP |
| B | size 50% [70/30] - AHEAD PDX:week:H (any) within 10pts | ALL | 99.1% | 3.0 | +0.023 [-0.033, +0.092] (0.09) | +0.009 (0.08) | +0.005 | +0.014 | +1.75 | +1.05 | +4.5 | 9/12 | +0.00/+0.02 | -661 (1959) / -548 | +0.10 | TOP |
| B | size 150% (POI behind) [market] - BEHIND ARR:FVG:2m (unmitigated) within 0.25xATR15 | ALL | 92.9% | 24.7 | -0.062 [-0.184, +0.079] (0.19) | +0.051 (0.25) | +0.037 | +0.103 | +2.10 | +0.72 | +4.2 | 9/12 | +0.02/+0.08 | +2740 (16755) / +2283 | -0.18 | TOP |
| B | re-target, skip if target<30 [70/30] - AHEAD PIV:cam_L4:rth (unmitigated) within 0.5xATR15 | ALL | 99.7% | 1.2 | +0.008 [-0.053, +0.069] (0.09) | -0.002 (0.10) | -0.012 | +0.031 |  | -0.49 | +5.2 | 8/12 | -0.06/+0.06 | +2325 (6853) / +1881 | -0.20 | TOP |
| B | re-target, skip if target<20 [70/30] - AHEAD PIV:cam_L4:rth (unmitigated) within 0.5xATR15 | ALL | 99.7% | 1.2 | -0.006 [-0.061, +0.052] (0.08) | -0.014 (0.09) | -0.022 | +0.010 |  | -3.88 | +5.2 | 8/12 | -0.06/+0.03 | +2325 (6853) / +1881 | -0.20 | TOP |
| B | size 150% (POI behind) [70/30] - BEHIND EQL:EQL_rel:1m (unmitigated) within 10pts | ALL | 94.8% | 17.9 | -0.068 [-0.205, +0.078] (0.21) | +0.014 (0.18) | +0.029 | -0.021 | +5.74 | +0.28 | +4.0 | 9/12 | +0.04/-0.02 | -1970 (9558) / -126 | -0.30 | TOP |
| B | size 150% (POI behind) [market] - BEHIND RND:x100:raw (unmitigated) within 2pts | ALL | 97.8% | 7.5 | -0.002 [-0.102, +0.098] (0.14) | +0.033 (0.13) | +0.021 | +0.021 | +1.02 | +1.53 | +4.0 | 11/12 | +0.02/+0.05 | +585 (7637) / +1441 | +0.11 | TOP |
| B | size 150% (POI behind) [70/30] - BEHIND FIB:ret62:5m (unmitigated) within 20pts | ALL | 95.4% | 16.0 | +0.063 [-0.062, +0.189] (0.17) | +0.139 (0.18) | +0.116 | +0.140 | +0.52 | +3.02 | +3.8 | 11/12 | +0.17/+0.11 | +2896 (9901) / +2696 | -0.01 | TOP |
| C | anyk:cls=PIV:k=5:D=40 / skip [MKT] | ALL | 98.4% | 5.6 | +0.108 [-0.086, +0.324] (0.30) | +0.054 (0.30) | +0.076 | +0.103 | +0.93 | +3.36 | +3.8 | 10/12 | -0.01/+0.12 | -1174 (14448) / -2405 | -0.19 | SEL |
| C | anyk:cls=PIV:k=5:D=40 / z67 [MKT] | ALL | 98.4% | 5.6 | +0.035 [-0.028, +0.106] (0.10) | +0.018 (0.10) | +0.025 | +0.034 | +0.93 | +1.11 | +3.8 | 10/12 | -0.00/+0.04 | -1362 (7644) / -3534 | +0.10 | SEL |
| C | anyk:cls=PIV:k=5:D=40 / z67 [SPL] | ALL | 98.4% | 5.6 | +0.037 [-0.026, +0.107] (0.10) | +0.020 (0.10) | +0.022 | +0.035 | +0.83 | +1.24 | +3.8 | 9/12 | +0.00/+0.04 | +152 (9685) / -898 | +0.13 | SEL |
| C | wscore:D=10:q=0.9 / skip [MKT] | DN | 92.4% | 1.9 | +0.951 [-0.361, +2.547] (2.09) | +0.408 (1.90) | +0.451 | -0.093 | +0.64 | +5.39 | +5.2 | 8/12 | +0.51/+0.30 |  (nan) /  |  | SEL |
| C | wscore:D=10:q=0.9 / z50 [MKT] | DN | 92.4% | 1.9 | +0.457 [-0.175, +1.218] (1.00) | +0.204 (0.95) | +0.226 | -0.046 | +0.64 | +2.70 | +5.2 | 8/12 | +0.26/+0.15 |  (nan) /  |  | SEL |
| C | wscore:D=10:q=0.9 / z50 [SPL] | DN | 92.4% | 1.9 | +0.440 [-0.169, +1.184] (0.98) | +0.213 (0.93) | +0.244 | -0.039 | +0.62 | +2.81 | +5.2 | 10/12 | +0.26/+0.16 |  (nan) /  |  | SEL |
| C | wscore:D=10:q=0.9 / z67 [MKT] | DN | 92.4% | 1.9 | +0.298 [-0.115, +0.792] (0.65) | +0.135 (0.63) | +0.149 | -0.031 | +0.64 | +1.78 | +5.2 | 8/12 | +0.17/+0.10 |  (nan) /  |  | SEL |
| C | wscore:D=10:q=0.9 / z67 [SPL] | DN | 92.4% | 1.9 | +0.286 [-0.110, +0.770] (0.64) | +0.140 (0.61) | +0.161 | -0.026 | +0.62 | +1.86 | +5.2 | 10/12 | +0.17/+0.11 |  (nan) /  |  | SEL |
| C | wscore:D=20:q=0.8 / skip [MKT] | DN | 84.3% | 3.9 | +1.807 [-0.161, +4.192] (3.11) | +0.545 (2.87) | +0.974 | -0.957 | +0.96 | +3.47 | +5.2 | 10/12 | +1.89/-0.83 |  (nan) /  |  | SEL |
| C | anyk:cls=PIV:k=5:D=40 / skip [SPL] | ALL | 98.4% | 5.6 | +0.115 [-0.079, +0.329] (0.29) | +0.061 (0.29) | +0.068 | +0.106 | +0.83 | +3.76 | +3.8 | 9/12 | +0.00/+0.12 | +558 (16194) / -212 | -0.18 | SEL |
| C | wscore:D=20:q=0.8 / skip [SPL] | DN | 84.3% | 3.9 | +1.711 [-0.276, +4.085] (3.10) | +0.568 (2.86) | +1.010 | -0.952 | +0.92 | +3.62 | +5.2 | 9/12 | +1.92/-0.81 |  (nan) /  |  | SEL |
| C | anyk:cls=PIV:k=5:D=40 / z50 [MKT] | ALL | 98.4% | 5.6 | +0.054 [-0.043, +0.160] (0.15) | +0.027 (0.15) | +0.038 | +0.052 | +0.93 | +1.68 | +3.8 | 10/12 | -0.00/+0.06 | -306 (8533) / -2340 | -0.06 | SEL |
| C | wscore:D=20:q=0.8 / z50 [MKT] | DN | 84.3% | 3.9 | +0.827 [-0.073, +1.903] (1.41) | +0.273 (1.43) | +0.487 | -0.479 | +0.96 | +1.74 | +5.2 | 10/12 | +0.95/-0.41 |  (nan) /  |  | SEL |
| C | wscore:D=20:q=0.8 / skip [MKT] | HM | 83.4% | 5.4 | +1.041 [-0.547, +2.623] (2.43) | +0.081 (2.42) | +0.180 | -0.349 | +6.65 | +0.49 | +4.2 | 9/12 | +0.95/-0.81 | +15245 (19707) / +13322 | -0.04 | SEL |
| C | wscore:D=20:q=0.8 / z50 [SPL] | DN | 84.3% | 3.9 | +0.782 [-0.126, +1.849] (1.40) | +0.284 (1.43) | +0.505 | -0.476 | +0.92 | +1.81 | +5.2 | 9/12 | +0.96/-0.41 |  (nan) /  |  | SEL |
| C | anyk:cls=PIV:k=5:D=40 / z50 [SPL] | ALL | 98.4% | 5.6 | +0.057 [-0.039, +0.163] (0.15) | +0.030 (0.15) | +0.034 | +0.053 | +0.83 | +1.88 | +3.8 | 9/12 | +0.00/+0.06 | +1969 (10410) / +791 | +0.04 | SEL |
| C | wscore:D=20:q=0.8 / z67 [MKT] | DN | 84.3% | 3.9 | +0.530 [-0.047, +1.218] (0.90) | +0.180 (0.95) | +0.321 | -0.316 | +0.96 | +1.15 | +5.2 | 10/12 | +0.62/-0.27 |  (nan) /  |  | SEL |
| C | wscore:D=20:q=0.8 / z67 [SPL] | DN | 84.3% | 3.9 | +0.501 [-0.081, +1.183] (0.90) | +0.187 (0.94) | +0.333 | -0.314 | +0.92 | +1.19 | +5.2 | 9/12 | +0.63/-0.27 |  (nan) /  |  | SEL |
| C | wscore:D=20:q=0.8 / skip [SPL] | HM | 83.4% | 5.4 | +1.140 [-0.393, +2.700] (2.36) | +0.242 (2.33) | +0.308 | -0.208 | +2.23 | +1.45 | +4.2 | 9/12 | +1.15/-0.68 | +16220 (18879) / +14617 | -0.01 | SEL |
| C | wscore:D=20:q=0.9 / skip [MKT] | DN | 94.0% | 1.5 | +0.867 [-0.476, +2.316] (1.93) | +0.441 (1.90) | +0.483 | -0.521 | +0.59 | +7.37 | +5.0 | 10/12 | +1.44/-0.58 |  (nan) /  |  | SEL |
| C | wscore:D=20:q=0.9 / skip [SPL] | DN | 94.0% | 1.5 | +0.800 [-0.554, +2.258] (1.94) | +0.414 (1.91) | +0.477 | -0.555 | +0.63 | +6.91 | +5.0 | 9/12 | +1.42/-0.61 |  (nan) /  |  | SEL |
| C | wscore:D=20:q=0.9 / z50 [MKT] | DN | 94.0% | 1.5 | +0.420 [-0.229, +1.120] (0.93) | +0.221 (0.95) | +0.242 | -0.260 | +0.59 | +3.68 | +5.0 | 10/12 | +0.72/-0.29 |  (nan) /  |  | SEL |
| C | wscore:D=20:q=0.8 / z50 [SPL] | HM | 83.4% | 5.4 | +0.519 [-0.179, +1.218] (1.07) | +0.121 (1.17) | +0.154 | -0.104 | +2.23 | +0.73 | +4.2 | 9/12 | +0.57/-0.34 | +7343 (11503) / +6241 | -0.04 | SEL |
| C | wscore:D=20:q=0.9 / z67 [MKT] | DN | 94.0% | 1.5 | +0.274 [-0.150, +0.730] (0.61) | +0.146 (0.63) | +0.160 | -0.172 | +0.59 | +2.43 | +5.0 | 10/12 | +0.48/-0.19 |  (nan) /  |  | SEL |
| C | wscore:D=20:q=0.9 / z50 [SPL] | DN | 94.0% | 1.5 | +0.387 [-0.270, +1.086] (0.94) | +0.207 (0.95) | +0.239 | -0.277 | +0.63 | +3.45 | +5.0 | 9/12 | +0.71/-0.31 |  (nan) /  |  | SEL |
| C | wscore:D=20:q=0.9 / z67 [SPL] | DN | 94.0% | 1.5 | +0.253 [-0.176, +0.709] (0.61) | +0.137 (0.63) | +0.158 | -0.183 | +0.63 | +2.28 | +5.0 | 9/12 | +0.47/-0.20 |  (nan) /  |  | SEL |
| C | wscore:D=20:q=0.8 / z50 [MKT] | HM | 83.4% | 5.4 | +0.473 [-0.250, +1.190] (1.10) | +0.041 (1.21) | +0.090 | -0.175 | +6.65 | +0.24 | +4.2 | 9/12 | +0.48/-0.40 | +6827 (12174) / +5097 | -0.09 | SEL |
| C | wscore:D=20:q=0.8 / z67 [SPL] | HM | 83.4% | 5.4 | +0.332 [-0.115, +0.779] (0.68) | +0.080 (0.77) | +0.102 | -0.069 | +2.23 | +0.48 | +4.2 | 9/12 | +0.38/-0.23 | +6656 (11355) / +5077 | -0.01 | SEL |
| C | wscore:D=20:q=0.9 / z67 [MKT] | ALL | 94.5% | 19.1 | -0.059 [-0.146, +0.033] (0.13) | -0.117 (0.14) | -0.059 | -0.134 |  | -2.12 | +4.0 | 10/12 | -0.10/-0.13 | +6130 (11266) / +3778 | -0.08 | TOP |
| C | wscore:D=20:q=0.9 / z50 [MKT] | ALL | 94.5% | 19.1 | -0.090 [-0.224, +0.050] (0.20) | -0.177 (0.22) | -0.090 | -0.203 |  | -3.21 | +4.0 | 10/12 | -0.16/-0.20 | +6491 (13593) / +4369 | -0.08 | TOP |
| C | wscore:D=20:q=0.9 / skip [MKT] | ALL | 94.5% | 19.1 | -0.185 [-0.461, +0.103] (0.42) | -0.354 (0.43) | -0.180 | -0.407 |  | -6.43 | +4.0 | 10/12 | -0.32/-0.39 | +2329 (20369) / +1248 | -0.37 | TOP |
| C | wscore:D=20:q=0.9 / z67 [SPL] | ALL | 94.5% | 19.1 | -0.046 [-0.131, +0.048] (0.13) | -0.103 (0.14) | -0.052 | -0.119 |  | -1.88 | +4.0 | 10/12 | -0.09/-0.11 | +8040 (11812) / +6923 | +0.00 | TOP |
| C | wscore:D=20:q=0.9 / skip [SPL] | ALL | 94.5% | 19.1 | -0.143 [-0.410, +0.151] (0.42) | -0.314 (0.43) | -0.159 | -0.360 |  | -5.70 | +4.0 | 10/12 | -0.28/-0.34 | +4547 (20597) / +4569 | -0.31 | TOP |
| C | anyk:cls=PDX:k=3:D=20 / skip [SPL] | ALL | 99.7% | 0.9 | -0.078 [-0.160, -0.014] (0.10) | -0.086 (0.11) | -0.070 | -0.057 |  | -33.54 | +3.2 | 5/12 | -0.11/-0.07 | -1462 (4054) / -1332 | -0.21 | TOP |
| C | wscore:D=20:q=0.9 / z50 [SPL] | ALL | 94.5% | 19.1 | -0.070 [-0.200, +0.074] (0.20) | -0.157 (0.21) | -0.079 | -0.180 |  | -2.85 | +4.0 | 10/12 | -0.14/-0.17 | +8438 (13631) / +7786 | -0.15 | TOP |
| C | anyk:cls=PDX:k=3:D=20 / z50 [SPL] | ALL | 99.7% | 0.9 | -0.039 [-0.080, -0.007] (0.05) | -0.043 (0.06) | -0.035 | -0.029 |  | -16.77 | +3.2 | 5/12 | -0.05/-0.03 | +55 (2354) / +44 | -0.13 | TOP |
| C | anyk:cls=PIV:k=5:D=40 / skip [MKT] | ALL | 98.4% | 5.6 | +0.108 [-0.086, +0.324] (0.30) | +0.054 (0.30) | +0.076 | +0.103 | +0.93 | +3.36 | +3.8 | 10/12 | -0.01/+0.12 | -1174 (14448) / -2405 | -0.19 | TOP |
| C | anyk:cls=PDX:k=3:D=20 / z67 [SPL] | ALL | 99.7% | 0.9 | -0.026 [-0.053, -0.005] (0.03) | -0.028 (0.04) | -0.023 | -0.019 |  | -11.07 | +3.2 | 5/12 | -0.03/-0.02 | -698 (1203) / -609 | +0.02 | TOP |
| C | anyk:cls=PIV:k=5:D=40 / z67 [MKT] | ALL | 98.4% | 5.6 | +0.035 [-0.028, +0.106] (0.10) | +0.018 (0.10) | +0.025 | +0.034 | +0.93 | +1.11 | +3.8 | 10/12 | -0.00/+0.04 | -1362 (7644) / -3534 | +0.10 | TOP |
| C | time:macro_1350_1410 / z50 [SPL] | ALL | 98.1% | 6.6 | +0.039 [-0.063, +0.155] (0.17) | +0.007 (0.14) | +0.006 | +0.012 | +4.41 | +0.38 | +6.0 | 9/12 | -0.00/+0.02 | +651 (1972) / +357 | -0.07 | TOP |
| C | anyk:cls=PIV:k=5:D=40 / z50 [MKT] | ALL | 98.4% | 5.6 | +0.054 [-0.043, +0.160] (0.15) | +0.027 (0.15) | +0.038 | +0.052 | +0.93 | +1.68 | +3.8 | 10/12 | -0.00/+0.06 | -306 (8533) / -2340 | -0.06 | TOP |
| C | time:macro_1350_1410 / skip [SPL] | ALL | 98.1% | 6.6 | +0.078 [-0.128, +0.312] (0.34) | +0.014 (0.29) | +0.013 | +0.024 | +4.41 | +0.75 | +6.0 | 9/12 | -0.00/+0.03 | +1588 (3994) / +962 | -0.12 | TOP |
| C | time:macro_1350_1410 / z67 [MKT] | ALL | 98.1% | 6.6 | +0.029 [-0.040, +0.105] (0.11) | +0.008 (0.09) | +0.007 | +0.008 | +2.46 | +0.44 | +6.0 | 9/12 | +0.01/+0.01 | +347 (1361) / +194 | -0.32 | TOP |
| C | time:macro_1350_1410 / z67 [SPL] | ALL | 98.1% | 6.6 | +0.025 [-0.042, +0.102] (0.11) | +0.005 (0.10) | +0.004 | +0.008 | +4.41 | +0.25 | +6.0 | 9/12 | -0.00/+0.01 | +363 (1275) / +177 | -0.05 | TOP |
| C | time:macro_1350_1410 / skip [MKT] | ALL | 98.1% | 6.6 | +0.089 [-0.123, +0.323] (0.33) | +0.026 (0.29) | +0.022 | +0.025 | +2.46 | +1.35 | +6.0 | 9/12 | +0.02/+0.04 | +1195 (3287) / +713 | -0.23 | TOP |
| C | time:macro_1350_1410 / z50 [MKT] | ALL | 98.1% | 6.6 | +0.044 [-0.061, +0.160] (0.16) | +0.013 (0.14) | +0.011 | +0.013 | +2.46 | +0.67 | +6.0 | 9/12 | +0.01/+0.02 | +388 (1948) / +173 | -0.27 | TOP |

Sessions (gain per signal L6M by entry session, with the fires) for the same cells are in out/ntz/detail.parquet (columns sess_<name>_L6M / _fire) and in the look table out/ntz/look/look.parquet (group = asia, london, pre, nyam, nypm, close; every selected cell, windows L3M..X', bases M / N / LIVE).

## 9. POST-HOC follow-up (NOT part of any prereg group; 4 rules x 10 books x 2 bases = 80 cells added to the cumulative count): skip a signal that has an unmitigated OPPOSING fair value gap between entry and target within 60 pts
Motivation: the HM NAMED cell (4h FVG) was positive in every window, and the HM map list ranks the 15m FVG first. Gain per signal on N (planned lot) with the market base; 'fired mean' = mean base net of the skipped signals (pts); MDE = 2.8 clustered SE; placebo = random fire set at the same rate in the same strata (200 draws).

| rule | book | window | fires / signals | gain per signal (MDE) | per contract kept | skipped mean pts | placebo rank | M / LIVE gain | stack delta \$/wk |
|--|--|--|--|--|--|--|--|--|--|
| FVG 15m:1h:4h | DN | HOLD | 190 / 782 | -0.926 (3.16) | +0.370 | +3.8 | 0.62 | -0.385 / -0.227 |  |
| FVG 15m:1h:4h | DN | L3M | 81 / 382 | -2.913 (4.14) | -2.233 | +13.7 | 0.10 | -2.367 / -2.254 |  |
| FVG 15m:1h:4h | DN | L6M | 166 / 701 | -1.058 (3.17) | +0.549 | +4.5 | 0.69 | -0.527 / -0.375 |  |
| FVG 15m:1h:4h | DN | PRE | 384 / 1761 | -1.186 (1.83) | -0.337 | +5.4 | 0.53 | -0.895 / -0.758 |  |
| FVG 15m:1h:4h | DN | X | 200 / 728 | +0.344 (3.06) | +0.639 | -1.3 | 0.68 | +0.525 / +0.705 |  |
| FVG 15m:1h:4h | DN | Y26 | 38 / 146 | -6.436 (5.84) | -3.417 | +24.7 | 0.09 | -5.641 / -5.533 |  |
| FVG 15m:1h:4h | HM | HOLD | 238 / 1008 | +0.973 (2.55) | +2.407 | -4.1 | 0.98 | +1.417 / +1.589 | +9110 |
| FVG 15m:1h:4h | HM | L3M | 108 / 504 | +0.593 (2.87) | +1.525 | -2.8 | 0.84 | +1.023 / +1.180 |  |
| FVG 15m:1h:4h | HM | L6M | 202 / 909 | +0.887 (2.37) | +2.494 | -4.0 | 0.98 | +1.314 / +1.478 | +11499 |
| FVG 15m:1h:4h | HM | PRE | 494 / 2285 | +0.654 (1.53) | +1.326 | -3.0 | 0.99 | +0.909 / +1.065 | -498 |
| FVG 15m:1h:4h | HM | X | 248 / 863 | +1.010 (2.95) | +1.694 | -3.5 | 0.95 | +1.177 / +1.369 | +1119 |
| FVG 15m:1h:4h | HM | Y26 | 49 / 203 | -0.118 (4.87) | +1.898 | +0.5 | 0.81 | +0.412 / +0.582 | +21018 |
| FVG 15m:1h:4h | KB | HOLD | 394 / 1374 | -0.533 (2.57) | -0.336 | +1.9 | 0.48 | +0.069 / +0.258 | +3594 |
| FVG 15m:1h:4h | KB | L3M | 182 / 728 | -0.599 (3.09) | -1.366 | +2.4 | 0.15 | -0.056 / +0.108 |  |
| FVG 15m:1h:4h | KB | L6M | 354 / 1257 | -0.346 (2.56) | +0.168 | +1.2 | 0.67 | +0.249 / +0.439 | +5432 |
| FVG 15m:1h:4h | KB | PRE | 820 / 3093 | -0.274 (1.58) | +0.555 | +1.0 | 0.83 | +0.064 / +0.241 | -2620 |
| FVG 15m:1h:4h | KB | X | 346 / 1033 | +0.886 (2.82) | +0.994 | -2.6 | 0.88 | +1.093 / +1.319 | +240 |
| FVG 15m:1h:4h | KB | Y26 | 76 / 288 | -4.022 (2.43) | -4.423 | +15.2 | 0.04 | -3.320 / -3.190 | +3115 |
| FVG 15m:1h:4h | MA | HOLD | 195 / 474 | -1.830 (3.57) | +0.679 | +4.4 | 0.61 | -0.923 / -0.665 |  |
| FVG 15m:1h:4h | MA | L3M | 60 / 218 | -3.125 (4.63) | -0.981 | +11.4 | 0.67 | -2.424 / -2.265 |  |
| FVG 15m:1h:4h | MA | L6M | 157 / 407 | -2.055 (3.82) | +0.908 | +5.3 | 0.67 | -1.184 / -0.940 |  |
| FVG 15m:1h:4h | MA | PRE | 414 / 1089 | -0.650 (3.49) | +0.530 | +1.7 | 0.73 | -0.203 / +0.044 |  |
| FVG 15m:1h:4h | MA | X | 265 / 520 | -1.205 (4.31) | -0.304 | +2.4 | 0.34 | -0.855 / -0.534 |  |
| FVG 15m:1h:4h | MA | Y26 | 26 / 87 | -5.340 (7.99) | -5.526 | +17.9 | 0.13 | -4.500 / -4.351 |  |
| FVG 15m:1h:4h | MV | HOLD | 275 / 1251 | +0.711 (2.35) | +1.336 | -3.2 | 0.95 | +1.143 / +1.303 |  |
| FVG 15m:1h:4h | MV | L3M | 123 / 652 | -0.011 (2.76) | +0.521 | +0.1 | 0.74 | +0.394 / +0.526 |  |
| FVG 15m:1h:4h | MV | L6M | 240 / 1131 | +0.750 (2.52) | +1.567 | -3.5 | 0.96 | +1.173 / +1.331 |  |
| FVG 15m:1h:4h | MV | PRE | 535 / 2917 | -0.294 (1.34) | +0.141 | +1.6 | 0.69 | -0.050 / +0.071 |  |
| FVG 15m:1h:4h | MV | X | 244 / 999 | +1.238 (2.22) | +0.656 | -5.1 | 0.81 | +1.382 / +1.556 |  |
| FVG 15m:1h:4h | MV | Y26 | 64 / 272 | +0.035 (4.79) | +1.449 | -0.1 | 0.72 | +0.541 / +0.705 |  |
| FVG 15m:1h:4h | PB | HOLD | 101 / 965 | +0.661 (1.67) | +1.382 | -6.3 | 0.98 | +0.849 / +0.927 |  |
| FVG 15m:1h:4h | PB | L3M | 40 / 483 | +0.312 (1.99) | +0.946 | -3.8 | 0.93 | +0.479 / +0.542 |  |
| FVG 15m:1h:4h | PB | L6M | 83 / 866 | +0.033 (1.57) | +0.776 | -0.3 | 0.91 | +0.227 / +0.292 |  |
| FVG 15m:1h:4h | PB | PRE | 231 / 2261 | +0.661 (1.06) | +0.716 | -6.5 | 0.96 | +0.775 / +0.853 |  |
| FVG 15m:1h:4h | PB | X | 152 / 823 | -0.573 (2.55) | -0.301 | +3.1 | 0.33 | -0.455 / -0.348 |  |
| FVG 15m:1h:4h | PB | Y26 | 20 / 195 | +1.318 (1.43) | +2.106 | -12.8 | 0.91 | +1.494 / +1.583 |  |
| FVG 15m:1h:4h | PE | HOLD | 262 / 1311 | -0.403 (1.73) | -0.301 | +2.0 | 0.47 | +0.022 / +0.154 | -848 |
| FVG 15m:1h:4h | PE | L3M | 125 / 711 | -0.226 (1.80) | -0.711 | +1.3 | 0.33 | +0.156 / +0.275 |  |
| FVG 15m:1h:4h | PE | L6M | 231 / 1194 | -0.215 (1.78) | -0.108 | +1.1 | 0.54 | +0.195 / +0.327 | +51 |
| FVG 15m:1h:4h | PE | PRE | 548 / 3049 | +0.198 (1.23) | +0.331 | -1.1 | 0.66 | +0.420 / +0.544 | -102 |
| FVG 15m:1h:4h | PE | X | 250 / 1001 | +0.007 (2.35) | +0.461 | -0.0 | 0.59 | +0.161 / +0.317 | +4390 |
| FVG 15m:1h:4h | PE | Y26 | 55 / 281 | +0.966 (2.42) | +0.283 | -4.9 | 0.64 | +1.348 / +1.492 | +1795 |
| FVG 15m:1h:4h | SM | HOLD | 174 / 363 | -2.381 (4.88) | -1.160 | +5.0 | 0.31 | -1.313 / -1.011 | -1725 |
| FVG 15m:1h:4h | SM | L3M | 59 / 166 | -2.904 (5.95) | -3.671 | +8.2 | 0.20 | -2.086 / -1.886 |  |
| FVG 15m:1h:4h | SM | L6M | 147 / 314 | -2.078 (5.45) | -1.833 | +4.4 | 0.29 | -1.044 / -0.746 | -1094 |
| FVG 15m:1h:4h | SM | PRE | 376 / 904 | -1.106 (3.39) | +0.754 | +2.7 | 0.74 | -0.603 / -0.331 | -1878 |
| FVG 15m:1h:4h | SM | X | 226 / 441 | +0.249 (5.16) | +1.904 | -0.5 | 0.73 | +0.582 / +0.912 | +53 |
| FVG 15m:1h:4h | SM | Y26 | 25 / 65 | -3.871 (9.72) | -4.158 | +10.1 | 0.24 | -2.945 / -2.746 | -1131 |
| FVG 15m:1h:4h | ST | HOLD | 249 / 1382 | +0.025 (1.84) | +0.693 | -0.1 | 0.85 | +0.398 / +0.523 | +964 |
| FVG 15m:1h:4h | ST | L3M | 111 / 720 | -0.288 (1.63) | +0.106 | +1.9 | 0.62 | +0.048 / +0.152 |  |
| FVG 15m:1h:4h | ST | L6M | 220 / 1256 | +0.075 (1.78) | +0.919 | -0.4 | 0.88 | +0.438 / +0.561 | +814 |
| FVG 15m:1h:4h | ST | PRE | 509 / 3020 | -0.140 (1.34) | +0.194 | +0.8 | 0.69 | +0.072 / +0.185 | -3308 |
| FVG 15m:1h:4h | ST | X | 229 / 988 | +0.231 (2.66) | +0.619 | -1.0 | 0.79 | +0.373 / +0.521 | -1875 |
| FVG 15m:1h:4h | ST | Y26 | 50 / 288 | -0.844 (2.95) | +0.476 | +4.9 | 0.65 | -0.440 / -0.330 | +18756 |
| FVG 15m:1h:4h | WT | HOLD | 220 / 1893 | +0.003 (0.66) | +0.160 | -0.0 | 0.76 | +0.286 / +0.356 | +1091 |
| FVG 15m:1h:4h | WT | L3M | 89 / 954 | -0.451 (0.85) | -0.347 | +4.8 | 0.35 | -0.197 / -0.148 |  |
| FVG 15m:1h:4h | WT | L6M | 195 / 1706 | +0.050 (0.70) | +0.287 | -0.4 | 0.88 | +0.328 / +0.398 | +1424 |
| FVG 15m:1h:4h | WT | PRE | 484 / 4265 | -0.017 (0.52) | +0.053 | +0.2 | 0.59 | +0.140 / +0.207 | +1589 |
| FVG 15m:1h:4h | WT | X | 268 / 1527 | -0.010 (1.06) | +0.154 | +0.1 | 0.68 | +0.132 / +0.235 | -1298 |
| FVG 15m:1h:4h | WT | Y26 | 43 / 404 | -0.605 (1.35) | -0.342 | +5.7 | 0.46 | -0.307 / -0.254 | -7451 |

HM only, the four rule variants and both bases (L6M and HOLD):

| rule | base | window | fires | gain per signal (MDE) | per contract kept | skipped mean | placebo rank | stack delta \$/wk |
|--|--|--|--|--|--|--|--|--|
| FVG 15m:1h:4h | market | HOLD | 238 | +0.973 (2.55) | +2.407 | -4.1 | 0.98 | +9110 |
| FVG 15m:1h:4h | market | L6M | 202 | +0.887 (2.37) | +2.494 | -4.0 | 0.98 | +11499 |
| FVG 15m:1h:4h | 70/30 | HOLD | 238 | +0.871 (2.54) | +2.199 | -3.7 | 0.97 | +8491 |
| FVG 15m:1h:4h | 70/30 | L6M | 202 | +0.908 (2.44) | +2.404 | -4.1 | 0.98 | +10720 |
| FVG 4h | market | HOLD | 78 | +0.236 (1.20) | +0.564 | -3.1 | 0.87 | +7148 |
| FVG 4h | market | L6M | 68 | +0.520 (1.21) | +0.945 | -7.0 | 0.96 | +10318 |
| FVG 4h | 70/30 | HOLD | 78 | +0.170 (1.33) | +0.470 | -2.2 | 0.81 | +7492 |
| FVG 4h | 70/30 | L6M | 68 | +0.454 (1.36) | +0.840 | -6.1 | 0.92 | +10740 |
| FVG 1h | market | HOLD | 102 | +0.008 (1.40) | +0.422 | -0.1 | 0.69 | +2691 |
| FVG 1h | market | L6M | 85 | +0.092 (1.43) | +0.591 | -1.0 | 0.80 | +4499 |
| FVG 1h | 70/30 | HOLD | 102 | +0.006 (1.40) | +0.395 | -0.1 | 0.72 | +2505 |
| FVG 1h | 70/30 | L6M | 85 | +0.080 (1.44) | +0.540 | -0.9 | 0.81 | +4212 |
| FVG 15m | market | HOLD | 157 | +0.953 (2.40) | +1.806 | -6.1 | 0.98 | +9001 |
| FVG 15m | market | L6M | 127 | +0.604 (2.34) | +1.471 | -4.3 | 0.96 | +9390 |
| FVG 15m | 70/30 | HOLD | 157 | +0.961 (2.29) | +1.768 | -6.2 | 0.98 | +8551 |
| FVG 15m | 70/30 | L6M | 127 | +0.741 (2.30) | +1.560 | -5.3 | 0.97 | +8769 |

HM neighbourhood (market base, gain per signal N; D = the FVG distance cut, TF sets): the effect is present from D=20 to D=60 in X', PRE and HOLD and disappears at D=10 (a gap closer than 10 pts is part of the entry noise):

|                       |     X |   PRE |   HOLD |   L6M |   L3M |   Y26 |
|:----------------------|------:|------:|-------:|------:|------:|------:|
| ('15m+1h+4h', 10)     |  0.11 |  0.06 |   0.05 |  0.19 | -0.09 |  0.03 |
| ('15m+1h+4h', 20)     |  0.78 |  0.59 |   0.9  |  0.72 |  0.17 |  0.35 |
| ('15m+1h+4h', 30)     |  0.88 |  0.71 |   0.57 |  0.24 | -0.39 |  0.1  |
| ('15m+1h+4h', 40)     |  1.15 |  0.92 |   0.35 |  0.34 | -0.12 |  0.15 |
| ('15m+1h+4h', 50)     |  1.2  |  0.56 |   0.92 |  0.83 |  0.5  |  0.17 |
| ('15m+1h+4h', 60)     |  1.01 |  0.65 |   0.97 |  0.89 |  0.59 | -0.12 |
| ('15m+30m+1h+4h', 10) |  0.6  |  0.12 |   0.06 |  0.2  | -0.09 |  0.33 |
| ('15m+30m+1h+4h', 20) |  1.34 |  0.59 |   0.79 |  0.53 | -0.06 |  0.37 |
| ('15m+30m+1h+4h', 30) |  1.52 |  0.64 |   0.41 | -0.01 | -0.38 |  0.13 |
| ('15m+30m+1h+4h', 40) |  1.19 |  0.91 |   0.12 |  0.01 | -0.23 |  0.17 |
| ('15m+30m+1h+4h', 50) |  1.36 |  0.51 |   0.57 |  0.44 |  0.15 | -0.4  |
| ('15m+30m+1h+4h', 60) |  1.3  |  0.49 |   0.62 |  0.5  |  0.36 | -0.69 |
| ('15m+4h', 10)        | -0.05 |  0.13 |  -0.06 |  0    | -0.46 |  0.02 |
| ('15m+4h', 20)        |  0.12 |  0.69 |   0.72 |  0.6  | -0.08 |  0.35 |
| ('15m+4h', 30)        |  0.34 |  0.78 |   0.74 |  0.49 | -0.29 |  0.08 |
| ('15m+4h', 40)        |  0.61 |  0.88 |   0.59 |  0.65 |  0.21 |  1.01 |
| ('15m+4h', 50)        |  0.88 |  0.58 |   0.93 |  0.83 |  0.36 |  0.44 |
| ('15m+4h', 60)        |  0.33 |  0.78 |   1.11 |  0.98 |  0.61 | -0.15 |
| ('5m+15m+1h+4h', 10)  | -0.24 |  0.07 |  -0.47 | -0.18 | -0.55 | -1.14 |
| ('5m+15m+1h+4h', 20)  |  0.78 |  0.82 |   0.21 |  0.29 | -0.55 | -1.48 |
| ('5m+15m+1h+4h', 30)  |  1.12 |  0.25 |   0.61 |  0.49 | -0.25 | -0.83 |
| ('5m+15m+1h+4h', 40)  |  1.07 |  0.27 |   0.16 |  0.39 | -0.09 | -0.77 |
| ('5m+15m+1h+4h', 50)  |  1.04 | -0.22 |   0.62 |  0.76 |  0.3  | -1.33 |
| ('5m+15m+1h+4h', 60)  |  0.7  |  0    |   0.97 |  1.01 |  0.63 | -1.02 |

Pooled over the three non-overlapping windows X', PRE, HOLD (inverse-variance, 15m+1h+4h, D=60): +0.74 pt per signal, SE about 0.43, z about 1.7 (one book chosen out of 10 and one rule set out of 4 after seeing it: not significant). Predicted effect for a forward test: +0.6 to +0.9 pt per HM signal on the market base (about 22% of HM signals fire the rule), i.e. about +\$3-4k per week at research lots on the planned-lot unit; the exact stack returned -0.5k (PRE), +1.1k (X'), +9.1k (HOLD), +11.5k (L6M) \$/wk with MDE 10-17k: the stack unit disagrees with the planned-lot unit in size and in PRE sign, so the forward register must settle it.

## 10. What was not tested / limits (named, nothing fabricated)
* POI gaps: see code/poi/README.md (Wyckoff AR/SC/LPS/phases, trend lines/channels, measured moves, 1-2-3 / three-push levels, single prints / poor highs-lows / volume-climax bars, composite profiles, absorption price / last sweep level / session book-defended levels, touch counts).
* Book walls: level prices assumed contiguous; the wall distance is (k-1) ticks, visible book 2.5 pts, so book-POI cells only exist for POIs within about 2.5 pts.
* HTF 200-period averages are NaN until enough bars exist (daily EMA/SMA200: from Feb 2024).
* Time POIs: no per-event release calendar in the repo; the trade table's day flags (fomc, nfp, cpi, event) with the standard 08:30 / 10:00 / 14:00 ET times were used; only windows with >= 100 signals exist.
* Tighten-stop (ts) cells use LINE POIs only (zone far edges are not in the feature store); the stop is the POI near edge + 0.5 pt beyond, lots = min(sd/sd', 2) (the engine cap is 2 lots).
* wait / split-behind cells enter at market the second after the trade-through; no limit-queue model; 'shuffled-day POI' is the random-fire-within-strata placebo (identical construction); the placebo draws are 200 (skip / size / size-up) and 20 + 20 (sim cells).
* Smoke test disclosure: a debugging run of poi_look.py printed recent-window rows of 6 already-selected cells before the formal look (no selection changed). Amendment 1 (D-type bug) logged before any recent read.
* The L2SE floor was not moved by any cell (the 70/30 floor remains the reference; stack lines are deltas against it).
