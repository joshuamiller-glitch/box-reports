# DS3_L2_UF_ENTRY_C4 - L2-UNTIL-FOUND cycle 4, ENTRY: per-book x per-session policy, session-relative L2 add gates, ES/RTY divergence modifier (agent UF-ENTRY, 2026-10-30)
Research only; UNTOUCHED never read. Prereg autopilot/UF_ENTRY_C4_prereg.md sha256 39c8d4da4c5fdfd2453b4126c2ddbcada2794522db964edbc1cd80f5c13b331e (DECISIONS.md, before any cell statistic); 107 cells, spec sha256 68748c2b13b729a63e121b5aa67ba1a1c34edd51c7425d309b2ac7278597077f; PRE+X' selection out/uf/entry_c4/pre_sel.json (copy autopilot/UF_ENTRY_C4_PRESEL.json) sha256 79deef98252f96b69cdf455ff4aa1ba33fd18bbc2df8a476bb3ccc0244bed8de logged before the one recent look. Masks, EQR frame, bases (N primary, L = LIVE-CAL, M), +pt = extra cost per remainder fill (charged to the cell AND the reference), MDE80 in parentheses as in cycles 1-3. References S (70/30 split), C (F.9/X8/no gate), market; every cell is scored vs all three. dead_lookup: 0 EXACT/NEAR; nearest = L2SE 'bookxsessionPRE-selected' policy row.
Look-ahead: no day-level feature (session tag known at entry; minute-of-day medians from prior <= 6 months; divergence uses 5-min returns to the signal second). sig_st1_age / sig_hma_sp (cycle-1 G11) are bar-state columns from abr_build.py covered by the ABR leak_test (noise-after-cut, 0 mismatches in 46,364 checks, DS3_CAUSAL_TIMES.md l.117) but not listed row by row there: treated as causal 'by test, not by row'.

## 0a. PER-CONTRACT RESTATEMENT (user addendum 2026-10-30: primary number = pts per trade per contract, size-independent; structure is not edge)
Trade level, 6 engine books, one row per taken signal (no lock engine, no equal-risk factor), book bracket as taken (60/60; WT stop 45), pts per trade per CONTRACT OF FINAL POSITION (net pts / total lots), $ per trade at 1 lot = 20 x pts, 95% CI = day-block bootstrap, MDE = 2.8 SE. N = no target-fill correction, L = LIVE-CAL, M = measured with the target correction. Recent windows first.
| arm | basis | 2026 (~5 wk) | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|
| MARKET (1 lot, book bracket 60/60) | N | +2.94 [-1.34,+7.22] (MDE 6.11; $+59/trade at 1 lot; n=1529) | +2.39 [+0.24,+4.54] (MDE 3.07; $+48/trade at 1 lot; n=6636) | +1.90 [-0.18,+3.98] (MDE 2.97; $+38/trade at 1 lot; n=7331) | +1.48 [-0.02,+2.97] (MDE 2.13; $+30/trade at 1 lot; n=16616) | +0.70 [-1.21,+2.60] (MDE 2.73; $+14/trade at 1 lot; n=5853) |
| 70/30 split S per contract of final position | N | +4.33 [+0.07,+8.58] (MDE 6.08; $+87/trade at 1 lot; n=1529) | +3.63 [+1.51,+5.75] (MDE 3.02; $+73/trade at 1 lot; n=6636) | +3.17 [+1.09,+5.25] (MDE 2.97; $+63/trade at 1 lot; n=7331) | +2.73 [+1.20,+4.26] (MDE 2.19; $+55/trade at 1 lot; n=16616) | +1.62 [-0.34,+3.59] (MDE 2.80; $+32/trade at 1 lot; n=5853) |
| base C (F.9 dip8) per contract of final position | N | +3.79 [-0.55,+8.14] (MDE 6.20; $+76/trade at 1 lot; n=1529) | +3.22 [+1.03,+5.41] (MDE 3.13; $+64/trade at 1 lot; n=6636) | +2.74 [+0.51,+4.98] (MDE 3.19; $+55/trade at 1 lot; n=7331) | +2.34 [+0.87,+3.80] (MDE 2.09; $+47/trade at 1 lot; n=16616) | +1.39 [-0.61,+3.40] (MDE 2.86; $+28/trade at 1 lot; n=5853) |
| MARKET (1 lot, book bracket 60/60) | L | +2.31 [-2.11,+6.72] (MDE 6.31; $+46/trade at 1 lot; n=1529) | +1.76 [-0.43,+3.95] (MDE 3.13; $+35/trade at 1 lot; n=6636) | +1.27 [-0.85,+3.39] (MDE 3.03; $+25/trade at 1 lot; n=7331) | +0.83 [-0.62,+2.29] (MDE 2.08; $+17/trade at 1 lot; n=16616) | +0.09 [-1.94,+2.11] (MDE 2.89; $+2/trade at 1 lot; n=5853) |
| 70/30 split S per contract of final position | L | +3.70 [-0.61,+8.02] (MDE 6.16; $+74/trade at 1 lot; n=1529) | +3.01 [+0.78,+5.24] (MDE 3.19; $+60/trade at 1 lot; n=6636) | +2.55 [+0.46,+4.63] (MDE 2.98; $+51/trade at 1 lot; n=7331) | +2.10 [+0.61,+3.59] (MDE 2.13; $+42/trade at 1 lot; n=16616) | +1.02 [-1.03,+3.06] (MDE 2.92; $+20/trade at 1 lot; n=5853) |
| base C (F.9 dip8) per contract of final position | L | +3.17 [-1.30,+7.64] (MDE 6.39; $+63/trade at 1 lot; n=1529) | +2.60 [+0.37,+4.82] (MDE 3.18; $+52/trade at 1 lot; n=6636) | +2.12 [-0.01,+4.24] (MDE 3.03; $+42/trade at 1 lot; n=7331) | +1.70 [+0.17,+3.23] (MDE 2.18; $+34/trade at 1 lot; n=16616) | +0.79 [-1.28,+2.85] (MDE 2.95; $+16/trade at 1 lot; n=5853) |
| MARKET (1 lot, book bracket 60/60) | M | +0.60 [-3.61,+4.81] (MDE 6.01; $+12/trade at 1 lot; n=1529) | +0.15 [-1.96,+2.27] (MDE 3.02; $+3/trade at 1 lot; n=6636) | -0.30 [-2.33,+1.73] (MDE 2.90; $-6/trade at 1 lot; n=7331) | +0.05 [-1.46,+1.56] (MDE 2.16; $+1/trade at 1 lot; n=16616) | +0.01 [-2.04,+2.05] (MDE 2.92; $+0/trade at 1 lot; n=5853) |
| 70/30 split S per contract of final position | M | +1.96 [-2.20,+6.11] (MDE 5.94; $+39/trade at 1 lot; n=1529) | +1.37 [-0.72,+3.46] (MDE 2.99; $+27/trade at 1 lot; n=6636) | +0.94 [-1.16,+3.04] (MDE 3.00; $+19/trade at 1 lot; n=7331) | +1.29 [-0.16,+2.74] (MDE 2.08; $+26/trade at 1 lot; n=16616) | +0.93 [-1.09,+2.94] (MDE 2.88; $+19/trade at 1 lot; n=5853) |
| base C (F.9 dip8) per contract of final position | M | +1.44 [-2.73,+5.61] (MDE 5.95; $+29/trade at 1 lot; n=1529) | +0.97 [-1.15,+3.09] (MDE 3.03; $+19/trade at 1 lot; n=6636) | +0.52 [-1.51,+2.56] (MDE 2.91; $+10/trade at 1 lot; n=7331) | +0.90 [-0.56,+2.36] (MDE 2.09; $+18/trade at 1 lot; n=16616) | +0.70 [-1.26,+2.66] (MDE 2.80; $+14/trade at 1 lot; n=5853) |

**Plain reading.** (i) The market arm at 1 lot and a fixed bracket is +2.4 pts/trade on N but +0.15 (L6M), -0.30 (HOLD) on M and +1.8 / +1.3 on LIVE-CAL: the N-basis level is the target-fill basis (gain from the fill-basis correction), not book information. (ii) The 70/30 split and base C earn MORE per contract of final position than market entry on the same signals; this is STRUCTURE, not L2 edge: a lower average entry, a target re-based on the average (closer) and a stop kept at the original level (farther from the average) change the bracket geometry. Paired per-contract deltas (N):
| paired delta per contract of final position (same signals) | ref | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|
| 70/30 split S per contract of final position | market | +1.39 [+0.99,+1.78] (MDE 0.57) | +1.24 [+1.03,+1.45] (MDE 0.30) | +1.27 [+1.08,+1.46] (MDE 0.27) | +1.26 [+1.14,+1.38] (MDE 0.17) | +0.93 [+0.76,+1.10] (MDE 0.24) |
| base C (F.9 dip8) per contract of final position | market | +0.85 [+0.52,+1.19] (MDE 0.47) | +0.83 [+0.68,+0.98] (MDE 0.22) | +0.84 [+0.69,+0.99] (MDE 0.22) | +0.86 [+0.76,+0.96] (MDE 0.14) | +0.70 [+0.57,+0.82] (MDE 0.18) |
| UF4|R|F0.7|X3|rel-any per contract of final position | split S | +0.29 [-0.14,+0.72] (MDE 0.62) | +0.25 [+0.10,+0.39] (MDE 0.20) | +0.26 [+0.12,+0.40] (MDE 0.20) | +0.31 [+0.23,+0.39] (MDE 0.12) | +0.17 [+0.06,+0.29] (MDE 0.17) |
| UF4|R|F0.9|X8|rel-any per contract of final position | split S | -0.38 [-0.72,-0.05] (MDE 0.48) | -0.27 [-0.40,-0.14] (MDE 0.19) | -0.29 [-0.41,-0.17] (MDE 0.17) | -0.26 [-0.34,-0.17] (MDE 0.12) | -0.14 [-0.29,+0.01] (MDE 0.22) |
| UF4|P|S|6m|ce1|fbC per contract of final position | split S | +0.18 [-0.26,+0.61] (MDE 0.62) | +0.12 [-0.05,+0.30] (MDE 0.25) | +0.05 [-0.12,+0.21] (MDE 0.24) | -0.35 [-0.46,-0.25] (MDE 0.15) | +0.10 [-0.08,+0.28] (MDE 0.25) |

(iii) The size-only cells have no per-contract content: the ES/RTY divergence modifier (half size on 20% of trades) leaves every traded contract's result unchanged; its stack gain is a re-weighting. The only per-contract question is whether the flagged trades are worse, and they are not reliably:
| D-cell information test (base C per contract, flagged top-20% NQ-ahead minus rest) | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| UF4|D|div_esrty|C|half flagged(top20% NQ-ahead) minus rest, base C per contract | -2.95 [-12.62,+6.71] (MDE 13.81; flagged +1.44 vs rest +4.39) | -2.34 [-6.95,+2.27] (MDE 6.59; flagged +1.28 vs rest +3.62) | -2.07 [-6.48,+2.34] (MDE 6.30; flagged +1.02 vs rest +3.09) | +0.53 [-1.96,+3.01] (MDE 3.55; flagged +2.76 vs rest +2.23) | -0.37 [-6.17,+5.44] (MDE 8.29; flagged +1.07 vs rest +1.43) |
| UF4|D|div_es|C|half flagged(top20% NQ-ahead) minus rest, base C per contract | +0.95 [-11.15,+13.05] (MDE 17.28; flagged +4.56 vs rest +3.61) | -2.29 [-7.69,+3.11] (MDE 7.71; flagged +1.30 vs rest +3.59) | -1.94 [-6.69,+2.81] (MDE 6.79; flagged +1.11 vs rest +3.05) | +0.60 [-2.04,+3.23] (MDE 3.76; flagged +2.81 vs rest +2.22) | -1.18 [-6.41,+4.04] (MDE 7.47; flagged +0.35 vs rest +1.53) |

(iv) Per-contract information in the add gate (the one L2 element in the split): the real gate vs a random gate at the same add rate (P1) and vs the book shuffled within day (P2), 20 draws each, per contract of final position (an add is ~30% of the position at F .7, ~10% at F .9, so per ADDED contract multiply by ~3 / ~10):
| add gate (per contract of final position, N) | placebo | window | real | placebo mean (sd) | gap (pts/contract) | rank |
|--|--|--|--|--|--|--|
| S abs 1of8 (F.7 X3) | P1 | L6M | 3.631 | 3.626 (0.031) | +0.005 | 0.55 |
| S abs 1of8 (F.7 X3) | P1 | HOLD | 3.170 | 3.148 (0.035) | +0.022 | 0.80 |
| S abs 1of8 (F.7 X3) | P1 | PRE | 2.734 | 2.700 (0.015) | +0.035 | 1.00 |
| S abs 1of8 (F.7 X3) | P1 | X | 1.623 | 1.599 (0.018) | +0.024 | 0.90 |
| S abs 1of8 (F.7 X3) | P2 | L6M | 3.631 | 3.574 (0.022) | +0.057 | 1.00 |
| S abs 1of8 (F.7 X3) | P2 | HOLD | 3.170 | 3.102 (0.020) | +0.068 | 1.00 |
| S abs 1of8 (F.7 X3) | P2 | PRE | 2.734 | 2.668 (0.018) | +0.067 | 1.00 |
| S abs 1of8 (F.7 X3) | P2 | X | 1.623 | 1.578 (0.021) | +0.045 | 1.00 |
| S rel any-of-8 (F.7 X3) | P1 | L6M | 3.876 | 3.938 (0.050) | -0.062 | 0.10 |
| S rel any-of-8 (F.7 X3) | P1 | HOLD | 3.428 | 3.447 (0.056) | -0.019 | 0.50 |
| S rel any-of-8 (F.7 X3) | P1 | PRE | 3.044 | 3.011 (0.024) | +0.032 | 0.85 |
| S rel any-of-8 (F.7 X3) | P1 | X | 1.797 | 1.760 (0.039) | +0.037 | 0.95 |
| S rel any-of-8 (F.7 X3) | P2 | L6M | 3.876 | 3.792 (0.040) | +0.084 | 1.00 |
| S rel any-of-8 (F.7 X3) | P2 | HOLD | 3.428 | 3.317 (0.039) | +0.111 | 1.00 |
| S rel any-of-8 (F.7 X3) | P2 | PRE | 3.044 | 2.905 (0.032) | +0.139 | 1.00 |
| S rel any-of-8 (F.7 X3) | P2 | X | 1.797 | 1.734 (0.041) | +0.063 | 0.90 |
| C+gate abs 1of8 (F.9 X8) | P1 | L6M | 3.238 | 3.271 (0.013) | -0.033 | 0.00 |
| C+gate abs 1of8 (F.9 X8) | P1 | HOLD | 2.761 | 2.790 (0.012) | -0.029 | 0.00 |
| C+gate abs 1of8 (F.9 X8) | P1 | PRE | 2.386 | 2.372 (0.011) | +0.014 | 0.95 |
| C+gate abs 1of8 (F.9 X8) | P1 | X | 1.403 | 1.396 (0.011) | +0.007 | 0.65 |
| C+gate abs 1of8 (F.9 X8) | P2 | L6M | 3.238 | 3.255 (0.013) | -0.017 | 0.10 |
| C+gate abs 1of8 (F.9 X8) | P2 | HOLD | 2.761 | 2.776 (0.012) | -0.015 | 0.15 |
| C+gate abs 1of8 (F.9 X8) | P2 | PRE | 2.386 | 2.360 (0.007) | +0.026 | 1.00 |
| C+gate abs 1of8 (F.9 X8) | P2 | X | 1.403 | 1.382 (0.012) | +0.022 | 0.95 |
| C+gate rel any-of-8 (F.9 X8) | P1 | L6M | 3.361 | 3.367 (0.023) | -0.006 | 0.50 |
| C+gate rel any-of-8 (F.9 X8) | P1 | HOLD | 2.878 | 2.881 (0.021) | -0.003 | 0.50 |
| C+gate rel any-of-8 (F.9 X8) | P1 | PRE | 2.478 | 2.475 (0.018) | +0.003 | 0.70 |
| C+gate rel any-of-8 (F.9 X8) | P1 | X | 1.480 | 1.451 (0.021) | +0.029 | 0.90 |
| C+gate rel any-of-8 (F.9 X8) | P2 | L6M | 3.361 | 3.340 (0.017) | +0.021 | 0.85 |
| C+gate rel any-of-8 (F.9 X8) | P2 | HOLD | 2.878 | 2.860 (0.016) | +0.019 | 0.85 |
| C+gate rel any-of-8 (F.9 X8) | P2 | PRE | 2.478 | 2.451 (0.020) | +0.027 | 0.90 |
| C+gate rel any-of-8 (F.9 X8) | P2 | X | 1.480 | 1.448 (0.024) | +0.032 | 0.85 |

The absolute gate on the split beats the shuffled book by +0.057 / +0.068 / +0.067 / +0.045 pts per contract (L6M / HOLD / PRE / X', rank 1.00) = about $1.2-1.4 per trade at 1 lot; against a random gate at the same rate it beats by only +0.005 (L6M, rank 0.55) to +0.035 (PRE). The session-relative gate: +0.084 / +0.111 / +0.139 / +0.063 vs the shuffled book (rank 1.00 / 1.00 / 1.00 / 0.90), +-0.06 vs a random gate (not above placebo). On base C the gate is not above the random gate (gap <= +0.03). A measured acting cost of about 0.25 pt per added fill (about 0.08 pt per final contract at F .7) is larger than the L6M gap vs a random gate and about equal to the gap vs the shuffled book: **not enough to trade on**. The per-contract structure gain of the split (+1.2 pts) is 20x the information in its gate.
**Verdict for cycle 4 per contract: every cell is structure-only.** (P) per-book x per-session policy: per contract of final position the chosen configs differ from the fallback by -0.35..+0.18 pts (the 6-month cell: +0.12 L6M, +0.05 HOLD, -0.35 PRE vs S), i.e. choosing among structures; (R) session-relative gate vs the absolute split: +0.25 pts per contract [+0.10, +0.39] in L6M, +0.26 HOLD, +0.31 PRE, +0.18 X' (MDE 0.12-0.20), but its placebo gap vs a random gate at the same rate is -0.06..+0.04 (rank 0.10-0.95): the gain is the lower add rate (fewer, deeper adds on a different mix), i.e. structure; (D) size-only. No cycle-4 cell is an information finding. The honest information statement for the entry gate is the P2 line above (+0.06-0.14 pts per contract vs the shuffled book), which is below the measured cost of acting.

## 0. Plain verdict (stack frame, secondary after the addendum)
* **No parameterisation, session-relative gate or modifier clears the floor with a size above its MDE.** RC over 107 cells (centred weekly deltas, 2000 draws), N: vs split L6M max t 1.96, p 0.539, cum-adj p 1.000 (best UF4|D|div_esrty|S|half); HOLD max t 1.69, p 0.691, cum-adj p 1.000 (best UF4|D|div_esrty|S|half); PRE max t 2.26, p 0.260, cum-adj p 1.000 (best UF4|PS|BS|SELfit|ce0|fbS); vs C L6M max t 1.65, p 0.656, cum-adj p 1.000 (best UF4|R|F0.9|X8|rel-DLTr05). N_cum = 147,250 = 147,143 stored (UF_TRIALS) + 107: cumulative-adjusted p = 1.0 everywhere vs a base.
* **PRE-selected cell `UF4|D|div_esrty|C|half`** (ES/RTY price divergence modifier on base C: half size when the NQ 5-min return, in the trade direction, is >= the 80th SEL percentile ahead of the mean of ES and RTY, i.e. NQ ran ahead of the other indices; threshold 5.46 bp; 20% of trades). One of two cells eligible vs split, vs C and vs market at +1 pt on PRE and X'. N, +0 pt, equal risk: vs C 2026 -3.7k, L6M +11.7k (MDE 24.9k), HOLD +8.6k, PRE +4.9k, X' +2.6k; vs split +7.1k / +13.7k (MDE 26.3k) / +7.9k / +6.3k / +9.6k (positive in all five windows); vs market L6M +37.1k, HOLD +31.1k, PRE +14.4k, X' +13.5k. The MDE (25-26k) is twice the effect: the half size on 20% of trades cuts exposure and the equal-risk factor rescales the whole stack (c* 1.10-1.13), so the number is noisy. Costs +1/+2 pt per remainder fill leave it unchanged vs C (L6M +11.7k, +11.7k) because it removes remainder fills only where it halves them.
* Tier: **BEST-AVAILABLE-NEGATIVE with a forward-watch LEAD flag**. Single tests: t vs C L6M 1.31, HOLD 1.06, PRE 1.25; vs split L6M 1.45; CI(PRE) vs C [-2.7k, +12.8k] and vs split [-3.5k, +16.1k] include 0; 2026 vs C -3.7k; year share of the delta vs C 0.73 (2025 carries, 2026 negative); RC p 0.5-0.7, cumulative 1.0. Placebo vs C: random subset at the same rate rank 1.00 / 0.85 / 0.85 / 1.00 (L6M/HOLD/PRE/X'), divergence shuffled within day 1.00 / 1.00 / 0.90 / 0.90: it passes >= 0.95 in L6M (both) and HOLD (shuffled) but not in PRE; not a PASS. The ES-only twin `div_es|C|half` is ~0 (L6M +0.8k vs C): the RTY leg carries the effect, one more reason to treat it as a lead, not a rule.
* **(P) per-book x per-session parameterisation: no.** 36 walk-forward cells vs C (N, +0 pt): mean L6M -2.7k, HOLD -0.8k, PRE -2.2k, X' -6.4k; share >= 0 vs the split: L6M 28%, HOLD 36%, PRE 28%. Windows 3 / 6 / 12 months and aggregation (book x session / session / book) do not change the sign; the best cells are within +-1.5k of the fallback (and the session-only 12m cell is -7k). The SEL-fit static cells are positive in SEL by construction (book x session +5.0k L6M, +5.5k HOLD, +6.1k PRE vs C at ce 0) but flip to -1.6k L6M at +1 pt: choosing among 18 configs per cell fits noise. The plateau in (F, X) has no session structure the data can pick causally.
* **(R) session-relative L2 add gates: the same as the absolute gate, not better.** Relative 'any of 8' vs the absolute 1-of-8 gate on the split's own settings (F .7, X 3): delta vs the absolute split L6M +0.8k (MDE 8.3k), HOLD +0.8k, PRE -4.1k, X' +1.1k, 2026 +7.1k: equal within MDE, PRE negative. The book-shuffle placebo ranks the relative gate 0.95 / 1.00 / 0.50 / 1.00 (L6M / HOLD / PRE / X'): informative recently, as the absolute gate, but its PRE information is lost; random gate at the same rate ranks 0.75 / 0.80 / 0.60 / 1.00. Single relative classes are -8k..-11k (too rare); 'two of 8' worse; adding the session-relative depth condition (thick >= 1.0 or not thin > 0.7 of rel_tot8 / session median) gives +3.4k L6M +0.7k HOLD -1.5k PRE (mean of 8 cells vs the split), inside MDE. On base C the gate is worth nothing either way (rank 0.40-0.60). 
* (D) ES/RTY divergence family (8 cells): means vs the split are ~0 (L6M +1.8k, HOLD -1.4k, PRE -0.7k, X' +4.4k); the selected `div_esrty|C|half` is the one cell with a consistent positive sign vs C and vs the split (the ES-only twin and the 'up when NQ lags' cells are ~0 or negative), i.e. a single-cell lead among 8, not a family effect.
* Floor unchanged after four cycles (~1,300 cells): the 70/30 split and its cost-robust form C remain the ENTRY best.

## 1. SETTINGS TABLE (recent windows first)
| row | basis | +pt/fill | ref | 2026 (~5 wk) | L6M | HOLD | PRE | X' | c* |
|--|--|--|--|--|--|--|--|--|--|
| C + half size when NQ ahead of ES/RTY (PRE-selected) | N | 0 | vs split | +7.1k (42.4k) | +13.7k (26.3k) | +7.9k (24.4k) | +6.3k (14.5k) | +9.6k (11.6k) | 1.134 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | N | 0 | vs C | -3.7k (62.4k) | +11.7k (24.9k) | +8.6k (22.6k) | +4.9k (11.1k) | +2.6k (7.8k) | 1.104 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | N | 0 | vs market | +28.0k (75.4k) | +37.1k (30.3k) | +31.1k (28.0k) | +14.4k (15.8k) | +13.5k (12.8k) | 1.206 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | N | 1 | vs split | +7.7k (44.2k) | +23.6k (27.6k) | +17.2k (25.7k) | +12.2k (15.2k) | +13.0k (11.6k) | 1.159 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | N | 1 | vs C | -3.8k (62.6k) | +11.7k (25.0k) | +8.9k (22.5k) | +5.0k (11.1k) | +2.5k (7.8k) | 1.106 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | N | 1 | vs market | +26.2k (74.6k) | +34.4k (29.8k) | +28.8k (27.3k) | +11.7k (15.5k) | +11.1k (12.2k) | 1.193 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | N | 2 | vs split | +13.6k (40.1k) | +30.3k (30.2k) | +23.5k (28.0k) | +16.9k (15.2k) | +16.2k (12.2k) | 1.192 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | N | 2 | vs C | -2.9k (66.2k) | +11.7k (25.0k) | +8.8k (22.5k) | +4.3k (11.2k) | +2.5k (7.6k) | 1.105 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | N | 2 | vs market | +23.9k (74.3k) | +31.9k (29.6k) | +26.5k (27.0k) | +8.1k (15.6k) | +9.4k (12.0k) | 1.181 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | L | 0 | vs split | +5.2k (39.6k) | +16.1k (25.3k) | +10.3k (23.7k) | +3.6k (14.8k) | +7.7k (11.9k) | 1.123 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | L | 0 | vs C | +0.5k (84.1k) | +12.8k (27.2k) | +9.1k (24.6k) | +3.3k (11.0k) | +2.4k (7.8k) | 1.104 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | L | 0 | vs market | +21.5k (72.9k) | +35.7k (30.3k) | +29.7k (27.7k) | +10.3k (15.4k) | +11.1k (12.8k) | 1.184 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | L | 1 | vs split | +6.4k (43.1k) | +22.7k (27.7k) | +16.5k (25.8k) | +6.7k (15.4k) | +10.3k (11.5k) | 1.147 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | L | 1 | vs C | +4.4k (78.0k) | +13.2k (26.4k) | +9.7k (23.9k) | +3.0k (11.0k) | +2.2k (7.7k) | 1.102 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | L | 1 | vs market | +19.4k (71.8k) | +32.4k (29.5k) | +27.1k (26.7k) | +5.8k (15.1k) | +8.7k (12.1k) | 1.163 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | L | 2 | vs split | +7.9k (42.7k) | +28.0k (29.1k) | +21.7k (26.8k) | +11.9k (16.1k) | +13.3k (12.0k) | 1.178 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | L | 2 | vs C | +12.0k (66.0k) | +16.1k (25.2k) | +12.3k (22.9k) | +3.1k (11.1k) | +2.1k (7.6k) | 1.103 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | L | 2 | vs market | +18.1k (70.3k) | +30.0k (28.9k) | +24.9k (26.2k) | +3.3k (15.0k) | +7.1k (12.0k) | 1.152 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | M | 0 | vs split | -10.7k (58.8k) | +12.1k (25.1k) | +7.4k (22.9k) | +0.9k (15.2k) | +6.8k (10.1k) | 1.095 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | M | 0 | vs C | +4.3k (62.7k) | +10.2k (23.4k) | +7.6k (21.3k) | -0.1k (11.1k) | +1.1k (7.1k) | 1.048 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | M | 0 | vs market | +8.8k (74.2k) | +25.5k (28.1k) | +19.1k (26.3k) | +8.7k (15.5k) | +9.7k (11.2k) | 1.098 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | M | 1 | vs split | -10.3k (50.5k) | +14.9k (26.0k) | +10.0k (23.8k) | +7.0k (15.3k) | +9.1k (10.3k) | 1.123 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | M | 1 | vs C | +5.7k (60.6k) | +8.9k (23.4k) | +6.6k (21.4k) | -1.0k (11.0k) | +0.9k (7.1k) | 1.044 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | M | 1 | vs market | +8.6k (71.5k) | +21.7k (28.1k) | +15.6k (26.2k) | +5.6k (14.8k) | +8.1k (11.1k) | 1.087 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | M | 2 | vs split | -5.8k (54.5k) | +18.6k (28.1k) | +13.4k (26.0k) | +14.6k (14.7k) | +12.9k (10.9k) | 1.157 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | M | 2 | vs C | +3.5k (63.2k) | +9.3k (23.7k) | +7.2k (21.4k) | -1.2k (11.1k) | +0.9k (7.0k) | 1.041 |
| C + half size when NQ ahead of ES/RTY (PRE-selected) | M | 2 | vs market | +7.2k (71.2k) | +19.7k (27.8k) | +13.8k (25.9k) | +4.1k (14.6k) | +6.5k (11.1k) | 1.078 |
| split with session-relative any-of-8 gate | N | 0 | vs split | +7.1k (30.1k) | +0.8k (8.3k) | +0.8k (7.3k) | -4.1k (6.9k) | +1.1k (4.8k) | 1.017 |
| split with session-relative any-of-8 gate | N | 0 | vs C | -3.7k (10.1k) | -0.9k (11.7k) | +1.6k (11.3k) | -5.2k (9.0k) | -5.6k (8.5k) | 0.990 |
| split with session-relative any-of-8 gate | N | 0 | vs market | +28.0k (37.0k) | +23.4k (16.1k) | +23.5k (15.6k) | +3.3k (12.1k) | +4.5k (9.8k) | 1.082 |
| split with session-relative any-of-8 gate | N | 1 | vs split | +6.4k (23.6k) | +3.3k (9.1k) | +3.1k (8.0k) | -3.5k (6.4k) | +1.2k (4.8k) | 1.008 |
| split with session-relative any-of-8 gate | N | 1 | vs C | -5.0k (11.4k) | -7.6k (11.5k) | -4.6k (11.9k) | -9.9k (9.3k) | -8.7k (8.5k) | 0.961 |
| split with session-relative any-of-8 gate | N | 1 | vs market | +24.8k (30.2k) | +13.5k (15.3k) | +14.3k (14.3k) | -4.4k (11.6k) | -0.9k (9.4k) | 1.037 |
| split with session-relative any-of-8 gate | N | 2 | vs split | +10.0k (28.5k) | +2.9k (10.2k) | +3.0k (9.1k) | -5.6k (5.9k) | +0.9k (4.1k) | 1.000 |
| split with session-relative any-of-8 gate | N | 2 | vs C | -6.2k (19.0k) | -13.8k (13.2k) | -10.2k (14.1k) | -16.5k (9.1k) | -11.7k (8.8k) | 0.927 |
| split with session-relative any-of-8 gate | N | 2 | vs market | +20.3k (21.8k) | +4.6k (16.0k) | +6.1k (14.6k) | -14.2k (11.8k) | -5.8k (9.3k) | 0.990 |
| split with session-relative any-of-8 gate | L | 0 | vs split | +11.4k (28.9k) | +3.2k (9.1k) | +3.0k (8.0k) | -5.4k (6.4k) | +0.8k (5.0k) | 0.993 |
| split with session-relative any-of-8 gate | L | 0 | vs C | +6.6k (22.0k) | +0.1k (10.9k) | +1.9k (10.4k) | -5.5k (8.6k) | -4.4k (8.5k) | 0.976 |
| split with session-relative any-of-8 gate | L | 0 | vs market | +28.0k (33.3k) | +22.1k (15.5k) | +22.0k (14.6k) | +0.8k (10.7k) | +3.8k (9.5k) | 1.047 |
| split with session-relative any-of-8 gate | L | 1 | vs split | +9.9k (27.7k) | +2.9k (11.2k) | +2.7k (9.9k) | -5.7k (6.2k) | +0.5k (4.6k) | 0.992 |
| split with session-relative any-of-8 gate | L | 1 | vs C | +7.8k (18.5k) | -5.8k (13.0k) | -3.6k (12.7k) | -8.9k (8.2k) | -7.2k (8.7k) | 0.953 |
| split with session-relative any-of-8 gate | L | 1 | vs market | +23.1k (25.3k) | +12.4k (15.8k) | +13.1k (14.4k) | -6.7k (11.1k) | -1.2k (9.3k) | 1.005 |
| split with session-relative any-of-8 gate | L | 2 | vs split | +5.6k (22.7k) | +2.1k (9.1k) | +2.3k (8.4k) | -6.9k (5.9k) | +1.0k (4.2k) | 0.990 |
| split with session-relative any-of-8 gate | L | 2 | vs C | +9.8k (17.9k) | -8.1k (11.7k) | -5.8k (12.2k) | -14.5k (8.1k) | -9.4k (8.7k) | 0.927 |
| split with session-relative any-of-8 gate | L | 2 | vs market | +15.8k (21.0k) | +4.7k (15.3k) | +6.0k (13.9k) | -15.0k (10.9k) | -4.9k (9.4k) | 0.968 |
| split with session-relative any-of-8 gate | M | 0 | vs split | +3.7k (19.6k) | +0.8k (8.1k) | +0.4k (7.2k) | -0.5k (4.8k) | +1.9k (4.3k) | 1.013 |
| split with session-relative any-of-8 gate | M | 0 | vs C | +18.1k (23.7k) | -0.6k (13.7k) | +0.9k (13.8k) | -1.4k (8.9k) | -3.6k (8.4k) | 0.969 |
| split with session-relative any-of-8 gate | M | 0 | vs market | +23.3k (34.7k) | +14.2k (15.9k) | +12.0k (15.4k) | +7.3k (11.6k) | +4.7k (8.9k) | 1.016 |
| split with session-relative any-of-8 gate | M | 1 | vs split | -0.3k (19.6k) | +0.3k (7.9k) | -0.4k (7.1k) | -1.0k (4.9k) | +1.1k (4.6k) | 1.018 |
| split with session-relative any-of-8 gate | M | 1 | vs C | +15.0k (22.6k) | -4.6k (13.9k) | -3.1k (14.5k) | -8.5k (8.2k) | -6.5k (8.1k) | 0.946 |
| split with session-relative any-of-8 gate | M | 1 | vs market | +18.2k (32.3k) | +7.6k (14.7k) | +5.5k (14.8k) | -2.1k (10.7k) | +0.3k (9.1k) | 0.986 |
| split with session-relative any-of-8 gate | M | 2 | vs split | -0.4k (21.1k) | +0.1k (8.5k) | -1.3k (7.7k) | +1.7k (5.3k) | +1.0k (4.7k) | 1.031 |
| split with session-relative any-of-8 gate | M | 2 | vs C | +8.4k (17.4k) | -7.3k (13.3k) | -6.0k (14.0k) | -12.8k (8.3k) | -9.8k (8.5k) | 0.928 |
| split with session-relative any-of-8 gate | M | 2 | vs market | +12.2k (29.7k) | +2.5k (13.7k) | +0.2k (14.4k) | -7.9k (11.1k) | -4.5k (9.4k) | 0.960 |

### References
| row | basis | +pt/fill | ref | 2026 (~5 wk) | L6M | HOLD | PRE | X' | c* |
|--|--|--|--|--|--|--|--|--|--|
| split vs market | N | 0 | +20.5k (43.8k) | +22.6k (16.4k) | +22.6k (16.0k) | +7.7k (11.4k) | +3.3k (8.8k) | 1.064 |
| C vs market | N | 0 | +32.1k (41.5k) | +24.4k (15.1k) | +21.7k (17.0k) | +9.0k (10.6k) | +10.7k (9.5k) | 1.093 |
| C vs split | N | 0 | +10.9k (29.9k) | +1.6k (14.4k) | -0.8k (13.5k) | +1.2k (9.1k) | +6.9k (8.8k) | 1.027 |
| split vs market | N | 1 | +18.2k (39.5k) | +10.1k (15.5k) | +11.1k (14.8k) | -0.8k (11.4k) | -2.2k (8.7k) | 1.029 |
| C vs market | N | 1 | +30.2k (39.4k) | +21.7k (14.5k) | +19.2k (16.1k) | +6.4k (10.3k) | +8.5k (9.3k) | 1.079 |
| C vs split | N | 1 | +11.7k (26.2k) | +11.3k (12.0k) | +7.9k (12.5k) | +6.9k (9.7k) | +10.4k (9.3k) | 1.049 |
| split vs market | N | 2 | +10.4k (39.1k) | +1.8k (16.1k) | +3.1k (14.8k) | -8.6k (11.9k) | -6.7k (8.6k) | 0.991 |
| C vs market | N | 2 | +27.0k (37.4k) | +19.4k (14.2k) | +17.1k (15.5k) | +3.5k (10.2k) | +6.7k (9.3k) | 1.068 |
| C vs split | N | 2 | +16.7k (35.4k) | +17.8k (14.5k) | +14.0k (14.5k) | +12.2k (10.0k) | +13.5k (9.7k) | 1.078 |
| split vs market | L | 0 | +16.0k (44.4k) | +18.7k (15.9k) | +18.9k (15.5k) | +6.5k (11.9k) | +3.0k (8.8k) | 1.054 |
| C vs market | L | 0 | +21.0k (40.8k) | +22.0k (15.2k) | +20.0k (15.8k) | +6.7k (10.5k) | +8.5k (9.3k) | 1.072 |
| C vs split | L | 0 | +4.7k (47.6k) | +3.1k (13.1k) | +1.1k (12.1k) | +0.2k (8.8k) | +5.3k (8.6k) | 1.017 |
| split vs market | L | 1 | +13.0k (39.9k) | +9.4k (15.5k) | +10.4k (14.6k) | -1.0k (11.4k) | -1.7k (8.6k) | 1.014 |
| C vs market | L | 1 | +14.8k (31.7k) | +18.5k (14.1k) | +16.8k (14.4k) | +2.7k (10.3k) | +6.4k (9.1k) | 1.055 |
| C vs split | L | 1 | +1.8k (42.2k) | +8.9k (13.3k) | +6.4k (12.8k) | +3.6k (9.4k) | +7.9k (8.8k) | 1.041 |
| split vs market | L | 2 | +10.3k (36.4k) | +2.7k (16.1k) | +3.7k (14.6k) | -8.3k (11.2k) | -5.9k (8.7k) | 0.978 |
| C vs market | L | 2 | +5.6k (32.0k) | +13.2k (14.6k) | +12.1k (14.5k) | +0.1k (10.2k) | +4.9k (9.1k) | 1.044 |
| C vs split | L | 2 | -4.9k (34.8k) | +10.8k (13.0k) | +8.6k (12.3k) | +8.5k (9.8k) | +11.0k (9.2k) | 1.068 |
| split vs market | M | 0 | +19.5k (41.7k) | +13.4k (14.5k) | +11.6k (14.0k) | +7.8k (11.3k) | +2.8k (8.4k) | 1.003 |
| C vs market | M | 0 | +4.3k (35.4k) | +14.9k (17.0k) | +11.1k (16.4k) | +8.8k (11.6k) | +8.5k (9.4k) | 1.048 |
| C vs split | M | 0 | -15.2k (25.7k) | +1.5k (15.2k) | -0.6k (14.6k) | +1.0k (9.6k) | +5.7k (8.8k) | 1.045 |
| split vs market | M | 1 | +18.5k (44.1k) | +7.3k (14.5k) | +5.9k (14.2k) | -1.2k (11.5k) | -0.7k (8.5k) | 0.968 |
| C vs market | M | 1 | +2.7k (34.7k) | +12.4k (16.6k) | +8.7k (16.0k) | +6.7k (11.1k) | +7.1k (9.4k) | 1.042 |
| C vs split | M | 1 | -16.4k (34.0k) | +5.3k (17.1k) | +2.9k (16.8k) | +8.1k (10.1k) | +8.1k (8.9k) | 1.076 |
| split vs market | M | 2 | +12.6k (42.7k) | +2.4k (13.7k) | +1.3k (14.1k) | -9.5k (11.7k) | -5.5k (9.2k) | 0.931 |
| C vs market | M | 2 | +3.6k (34.6k) | +10.1k (16.4k) | +6.3k (15.7k) | +5.3k (10.9k) | +5.6k (9.4k) | 1.035 |
| C vs split | M | 2 | -9.7k (32.2k) | +8.3k (17.5k) | +5.4k (17.7k) | +15.9k (11.1k) | +11.9k (9.9k) | 1.112 |

## 2. Family map (means, N, +0 pt, equal risk)
vs the split:
| family | n | 2026 | L6M | HOLD | PRE | X' | share>=0 L6M/HOLD/PRE/X' |
|--|--|--|--|--|--|--|--|
| D_div | 8 | +5.4k | +1.8k | -1.4k | -0.7k | +4.4k | 0.50/0.25/0.50/0.88 |
| P_static | 12 | +13.6k | +0.1k | -1.0k | +1.5k | +3.8k | 0.33/0.42/0.67/1.00 |
| P_wf | 36 | +8.5k | -1.2k | -1.7k | -1.0k | +0.4k | 0.28/0.36/0.28/0.58 |
| R_control | 3 | +11.0k | +1.3k | -0.4k | -0.6k | +2.2k | 0.67/0.33/0.67/0.67 |
| R_depth | 8 | +11.0k | +3.4k | +0.7k | -1.5k | -0.1k | 0.75/0.62/0.38/0.38 |
| R_gate | 8 | +13.8k | +0.9k | -1.2k | -1.9k | +2.2k | 0.75/0.25/0.50/1.00 |
| R_single | 32 | +15.6k | -8.1k | -10.3k | -10.8k | -0.6k | 0.25/0.12/0.22/0.47 |

vs C:
| family | n | 2026 | L6M | HOLD | PRE | X' | share>=0 L6M/HOLD/PRE/X' |
|--|--|--|--|--|--|--|--|
| D_div | 8 | -5.4k | +0.1k | -0.6k | -1.9k | -2.4k | 0.50/0.38/0.50/0.25 |
| P_static | 12 | +2.6k | -1.5k | -0.1k | +0.2k | -3.1k | 0.17/0.50/0.50/0.00 |
| P_wf | 36 | -2.3k | -2.7k | -0.8k | -2.2k | -6.4k | 0.25/0.42/0.17/0.03 |
| R_control | 3 | +0.1k | -0.3k | +0.4k | -1.8k | -4.6k | 0.33/0.33/0.33/0.00 |
| R_depth | 8 | +0.1k | +1.8k | +1.6k | -2.7k | -6.8k | 0.75/0.62/0.25/0.00 |
| R_gate | 8 | +2.8k | -0.7k | -0.3k | -3.1k | -4.5k | 0.50/0.50/0.12/0.00 |
| R_single | 32 | +4.5k | -9.4k | -9.2k | -11.7k | -7.3k | 0.19/0.22/0.16/0.00 |

### (P) walk-forward policies vs C, means by aggregation and refit window (36 cells)
| aggregation | window | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|
| B | 12m | +6.3k | -1.0k | +0.7k | -0.7k | -7.9k |
| B | 3m | -9.2k | -4.5k | -0.5k | -3.6k | -7.9k |
| B | 6m | +4.1k | -1.2k | +1.5k | +0.1k | -7.8k |
| BS | 12m | -10.5k | -0.0k | +1.0k | -1.8k | -6.7k |
| BS | 3m | -14.2k | -1.8k | +1.0k | -2.6k | -7.2k |
| BS | 6m | +1.8k | -4.1k | -1.0k | -1.7k | -6.1k |
| S | 12m | -4.1k | -7.4k | -7.1k | -5.7k | -4.5k |
| S | 3m | -4.4k | -2.9k | -2.3k | -1.4k | -5.9k |
| S | 6m | +9.3k | -1.6k | -0.7k | -2.0k | -3.3k |

| static SEL-fit cell (in-sample on SEL) | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| UF4|PS|BS|SELfit|ce0|fbS | +8.3k | +5.0k | +5.5k | +6.1k | -2.3k |
| UF4|PS|BS|SELfit|ce0|fbC | +8.3k | +5.0k | +5.8k | +6.1k | -2.3k |
| UF4|PS|BS|SELfit|ce1|fbS | +7.4k | -1.6k | +0.8k | +1.3k | -4.2k |
| UF4|PS|BS|SELfit|ce1|fbC | +7.4k | -1.6k | +1.1k | +1.3k | -4.2k |
| UF4|PS|S|SELfit|ce0|fbS | -4.4k | -1.9k | -2.6k | -2.9k | -4.3k |
| UF4|PS|S|SELfit|ce0|fbC | -4.4k | -1.9k | -2.3k | -2.9k | -4.3k |
| UF4|PS|S|SELfit|ce1|fbS | -3.0k | -5.9k | -5.4k | -3.3k | -1.1k |
| UF4|PS|S|SELfit|ce1|fbC | -3.0k | -5.9k | -5.1k | -3.3k | -1.1k |
| UF4|PS|B|SELfit|ce0|fbS | +6.6k | -1.8k | +1.6k | -1.0k | -1.7k |
| UF4|PS|B|SELfit|ce0|fbC | +6.6k | -1.8k | +1.6k | -1.0k | -1.7k |
| UF4|PS|B|SELfit|ce1|fbS | +1.0k | -3.1k | -1.3k | +1.2k | -4.8k |
| UF4|PS|B|SELfit|ce1|fbC | +1.0k | -3.1k | -1.3k | +1.2k | -4.8k |

### (R) session-relative gates vs the split (N, +0 pt)
| cid | cell | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|
| 48 | UF4|R|F0.7|X3|rel-any | +7.1k (30.1k) | +0.8k (8.3k) | +0.8k (7.3k) | -4.1k (6.9k) | +1.1k (4.8k) |
| 49 | UF4|R|F0.7|X3|rel-two | +10.5k (40.8k) | +0.3k (13.0k) | -1.5k (11.8k) | -4.1k (8.7k) | +0.4k (5.8k) |
| 58 | UF4|R|F0.7|X3|rel-any+thick1.0-sess | -1.7k (10.9k) | +5.4k (13.8k) | +4.4k (12.2k) | -5.1k (9.7k) | -4.4k (8.3k) |
| 59 | UF4|R|F0.7|X3|rel-any+notthin0.7-sess | +10.3k (29.8k) | +4.7k (14.5k) | +4.2k (12.7k) | -2.0k (7.7k) | +0.2k (5.2k) |
| 60 | UF4|R|F0.7|X5|rel-any | +12.5k (23.7k) | +4.1k (9.6k) | +2.3k (8.8k) | -4.9k (9.1k) | +0.9k (9.3k) |
| 61 | UF4|R|F0.7|X5|rel-two | +16.7k (19.9k) | +2.0k (15.3k) | -0.6k (14.1k) | -7.9k (11.1k) | +3.0k (9.7k) |
| 70 | UF4|R|F0.7|X5|rel-any+thick1.0-sess | +10.9k (29.8k) | +5.7k (21.0k) | +1.9k (19.4k) | -7.0k (11.9k) | -1.1k (12.7k) |
| 71 | UF4|R|F0.7|X5|rel-any+notthin0.7-sess | +24.1k (27.4k) | +7.0k (18.2k) | +4.7k (16.2k) | -3.4k (9.6k) | -0.5k (10.0k) |
| 72 | UF4|RC|F0.7|X5|abs-1of8-control | +14.7k (19.3k) | +3.7k (11.1k) | +2.7k (9.8k) | -4.1k (7.7k) | +0.6k (9.3k) |
| 73 | UF4|R|F0.9|X8|rel-any | +18.5k (31.1k) | +2.5k (13.9k) | -0.7k (13.0k) | +0.9k (8.8k) | +5.8k (9.6k) |
| 74 | UF4|R|F0.9|X8|rel-two | +24.4k (45.8k) | +2.3k (16.6k) | -1.2k (15.4k) | +0.8k (9.0k) | +4.3k (10.1k) |
| 83 | UF4|R|F0.9|X8|rel-any+thick1.0-sess | +12.6k (28.0k) | +5.9k (15.2k) | +0.7k (14.9k) | +1.5k (12.0k) | +3.0k (10.8k) |
| 84 | UF4|R|F0.9|X8|rel-any+notthin0.7-sess | +17.7k (34.3k) | +1.9k (14.3k) | -1.1k (13.1k) | +0.3k (8.6k) | +4.7k (9.2k) |
| 85 | UF4|RC|F0.9|X8|abs-1of8-control | +11.0k (29.1k) | +1.6k (14.1k) | -1.2k (13.4k) | +0.7k (9.1k) | +6.0k (9.0k) |
| 86 | UF4|R|F0.9|X5|rel-any | +8.0k (26.5k) | -3.2k (12.7k) | -5.2k (11.7k) | +3.8k (8.1k) | +0.8k (7.7k) |
| 87 | UF4|R|F0.9|X5|rel-two | +12.6k (26.6k) | -1.3k (12.7k) | -3.5k (11.5k) | +0.1k (9.3k) | +1.7k (7.9k) |
| 96 | UF4|R|F0.9|X5|rel-any+thick1.0-sess | +8.1k (22.7k) | -0.2k (12.5k) | -4.0k (12.4k) | -1.3k (10.2k) | -2.3k (9.7k) |
| 97 | UF4|R|F0.9|X5|rel-any+notthin0.7-sess | +6.3k (29.7k) | -2.9k (12.8k) | -4.9k (11.8k) | +4.7k (8.4k) | -0.4k (7.9k) |
| 98 | UF4|RC|F0.9|X5|abs-1of8-control | +7.5k (16.7k) | -1.4k (10.0k) | -2.8k (9.4k) | +1.6k (7.8k) | -0.1k (7.4k) |

### (D) divergence modifier cells (vs split and vs C)
| cid | cell | ref | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|--|
| 99 | UF4|D|div_es|S|half | vs | +16.1k (26.3k) | +2.9k (20.7k) | -0.4k (19.6k) | +1.3k (10.3k) | +1.1k (7.6k) |
| 99 | UF4|D|div_es|S|half | vc | +5.1k (47.6k) | +1.2k (24.1k) | +0.5k (23.0k) | +0.1k (13.2k) | -5.7k (12.6k) |
| 100 | UF4|D|div_es|S|up | vs | -10.6k (47.8k) | -10.1k (15.8k) | -8.5k (14.5k) | -7.8k (14.3k) | -2.6k (6.5k) |
| 100 | UF4|D|div_es|S|up | vc | -20.9k (47.6k) | -11.4k (19.3k) | -7.5k (18.0k) | -8.7k (14.0k) | -9.3k (11.0k) |
| 101 | UF4|D|div_es|C|half | vs | +8.5k (19.5k) | +2.4k (20.2k) | -2.8k (19.6k) | +1.3k (12.4k) | +6.5k (9.9k) |
| 101 | UF4|D|div_es|C|half | vc | -2.3k (38.6k) | +0.8k (19.4k) | -1.9k (18.7k) | +0.1k (9.7k) | -0.4k (7.3k) |
| 102 | UF4|D|div_es|C|up | vs | -7.1k (44.4k) | -4.7k (22.0k) | -6.4k (20.2k) | -5.4k (15.5k) | +6.7k (11.5k) |
| 102 | UF4|D|div_es|C|up | vc | -17.5k (31.1k) | -6.1k (16.5k) | -5.3k (15.1k) | -6.4k (12.9k) | -0.2k (8.2k) |
| 103 | UF4|D|div_esrty|S|half | vs | +29.0k (38.0k) | +16.7k (23.8k) | +13.1k (21.7k) | +5.1k (11.3k) | +1.8k (8.3k) |
| 103 | UF4|D|div_esrty|S|half | vc | +17.6k (52.0k) | +14.6k (25.4k) | +13.6k (23.2k) | +3.8k (13.7k) | -5.0k (12.5k) |
| 104 | UF4|D|div_esrty|S|up | vs | +1.5k (19.2k) | -3.2k (10.1k) | -5.6k (11.0k) | -6.0k (13.7k) | +2.3k (6.5k) |
| 104 | UF4|D|div_esrty|S|up | vc | -9.2k (41.0k) | -4.7k (13.3k) | -4.6k (14.4k) | -7.0k (13.7k) | -4.4k (10.7k) |
| 105 | UF4|D|div_esrty|C|half | vs | +7.1k (42.4k) | +13.7k (26.3k) | +7.9k (24.4k) | +6.3k (14.5k) | +9.6k (11.6k) |
| 105 | UF4|D|div_esrty|C|half | vc | -3.7k (62.4k) | +11.7k (24.9k) | +8.6k (22.6k) | +4.9k (11.1k) | +2.6k (7.8k) |
| 106 | UF4|D|div_esrty|C|up | vs | -1.4k (25.8k) | -3.6k (16.8k) | -9.0k (16.5k) | -0.7k (15.9k) | +9.7k (12.0k) |
| 106 | UF4|D|div_esrty|C|up | vc | -12.0k (34.9k) | -5.1k (13.1k) | -7.9k (13.7k) | -1.8k (12.3k) | +2.7k (7.4k) |

## 3. Placebo, RC, gates
| cell | placebo (20 draws) | ref | L6M | HOLD | PRE | X' | 2026 |
|--|--|--|--|--|--|--|--|
| UF4|P|S|6m|ce1|fbC | P1 random assignment / random gate / random subset at the same rate: rank | vc | 0.75 | 0.75 | 0.55 | 0.90 | 0.70 |
| UF4|P|S|6m|ce1|fbC | P1 random assignment / random gate / random subset at the same rate: rank | vs | 0.75 | 0.75 | 0.55 | 0.90 | 0.70 |
| UF4|R|F0.7|X3|rel-any | P1 random assignment / random gate / random subset at the same rate: rank | vc | 0.75 | 0.80 | 0.60 | 1.00 | 0.75 |
| UF4|R|F0.7|X3|rel-any | P1 random assignment / random gate / random subset at the same rate: rank | vs | 0.75 | 0.80 | 0.60 | 1.00 | 0.75 |
| UF4|R|F0.7|X3|rel-any | P2 book bits / feature shuffled within day: rank | vc | 0.95 | 1.00 | 0.50 | 1.00 | 0.95 |
| UF4|R|F0.7|X3|rel-any | P2 book bits / feature shuffled within day: rank | vs | 0.95 | 1.00 | 0.50 | 1.00 | 0.95 |
| UF4|R|F0.9|X8|rel-any | P1 random assignment / random gate / random subset at the same rate: rank | vc | 0.45 | 0.50 | 0.60 | 0.45 | 0.35 |
| UF4|R|F0.9|X8|rel-any | P1 random assignment / random gate / random subset at the same rate: rank | vs | 0.45 | 0.50 | 0.60 | 0.45 | 0.35 |
| UF4|R|F0.9|X8|rel-any | P2 book bits / feature shuffled within day: rank | vc | 0.50 | 0.60 | 0.60 | 0.40 | 0.45 |
| UF4|R|F0.9|X8|rel-any | P2 book bits / feature shuffled within day: rank | vs | 0.50 | 0.60 | 0.60 | 0.40 | 0.45 |
| UF4|R|F0.9|X8|rel-IMBFr2 | P1 random assignment / random gate / random subset at the same rate: rank | vc | 0.70 | 0.60 | 1.00 | 0.75 | 0.30 |
| UF4|R|F0.9|X8|rel-IMBFr2 | P1 random assignment / random gate / random subset at the same rate: rank | vs | 0.70 | 0.60 | 1.00 | 0.75 | 0.30 |
| UF4|R|F0.9|X8|rel-IMBFr2 | P2 book bits / feature shuffled within day: rank | vc | 0.75 | 0.55 | 1.00 | 0.85 | 0.20 |
| UF4|R|F0.9|X8|rel-IMBFr2 | P2 book bits / feature shuffled within day: rank | vs | 0.75 | 0.55 | 1.00 | 0.85 | 0.20 |
| UF4|R|F0.9|X8|rel-any+notthin0.7-sess | P1 random assignment / random gate / random subset at the same rate: rank | vc | 0.55 | 0.65 | 0.60 | 0.10 | 0.45 |
| UF4|R|F0.9|X8|rel-any+notthin0.7-sess | P1 random assignment / random gate / random subset at the same rate: rank | vs | 0.55 | 0.65 | 0.60 | 0.10 | 0.45 |
| UF4|R|F0.9|X8|rel-any+notthin0.7-sess | P2 book bits / feature shuffled within day: rank | vc | 0.70 | 0.70 | 0.35 | 0.15 | 0.35 |
| UF4|R|F0.9|X8|rel-any+notthin0.7-sess | P2 book bits / feature shuffled within day: rank | vs | 0.70 | 0.70 | 0.35 | 0.15 | 0.35 |
| UF4|D|div_es|C|half | P1 random assignment / random gate / random subset at the same rate: rank | vc | 0.90 | 0.70 | 0.90 | 0.65 | 0.55 |
| UF4|D|div_es|C|half | P1 random assignment / random gate / random subset at the same rate: rank | vs | 0.90 | 0.70 | 0.90 | 0.65 | 0.55 |
| UF4|D|div_es|C|half | P2 book bits / feature shuffled within day: rank | vc | 0.65 | 0.50 | 0.80 | 0.75 | 0.30 |
| UF4|D|div_es|C|half | P2 book bits / feature shuffled within day: rank | vs | 0.65 | 0.50 | 0.80 | 0.75 | 0.30 |
| UF4|D|div_esrty|C|half | P1 random assignment / random gate / random subset at the same rate: rank | vc | 1.00 | 0.85 | 0.85 | 1.00 | 0.35 |
| UF4|D|div_esrty|C|half | P1 random assignment / random gate / random subset at the same rate: rank | vs | 1.00 | 0.85 | 0.85 | 1.00 | 0.35 |
| UF4|D|div_esrty|C|half | P2 book bits / feature shuffled within day: rank | vc | 1.00 | 1.00 | 0.90 | 0.90 | 0.30 |
| UF4|D|div_esrty|C|half | P2 book bits / feature shuffled within day: rank | vs | 1.00 | 1.00 | 0.90 | 0.90 | 0.30 |

* RC over 107 cells: vs split N L6M max t 1.96, p 0.539, cum-adj p 1.000 (best UF4|D|div_esrty|S|half); HOLD max t 1.69, p 0.691, cum-adj p 1.000 (best UF4|D|div_esrty|S|half); PRE max t 2.26, p 0.260, cum-adj p 1.000 (best UF4|PS|BS|SELfit|ce0|fbS); vs C N L6M max t 1.65, p 0.656, cum-adj p 1.000 (best UF4|R|F0.9|X8|rel-DLTr05); HOLD max t 1.81, p 0.557, cum-adj p 1.000 (best UF4|PS|BS|SELfit|ce0|fbC); M L6M vs split max t 2.26, p 0.328, cum-adj p 1.000 (best UF4|RC|F0.7|X5|abs-1of8-control); LIVE-CAL L6M vs split max t 2.04, p 0.491, cum-adj p 1.000 (best UF4|RC|F0.7|X5|abs-1of8-control); vs market (claim of the bases): N L6M max t 5.56, p 0.001, cum-adj p 0.748 (best UF4|PS|BS|SELfit|ce0|fbS) - the best 'vs market' cell is a SEL-fit static policy (in-sample by construction).
* Gates for the selected cell vs C / vs split: holdout_sign yes/yes; SPAN2 yes/yes; CI(PRE lo>0) no/no; maxDD(engine, HOLD) 691k vs C 685k (fail) / 710k vs split 625k (fail); year_share 0.73 / 0.42; RC fail; placebo partial.
* D6 session cells (row attribution, N, c=1, $k/wk, no per-cell MDE; MV has no lock-engine book, so its London / NY-AM cells are not attributable here), selected cell vs C:
| D6 session cell | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| KB asia | -2.2k | -0.3k | -0.2k | +0.9k | -0.0k |
| PE london | -1.1k | +0.3k | +0.0k | -0.6k | +0.0k |
| HM asia | -2.5k | -0.2k | -0.4k | -0.6k | -0.4k |
| HM nyam | +5.1k | -0.5k | -0.9k | +0.5k | +1.2k |
| SM asia | +0.0k | -0.0k | -0.1k | -0.4k | -0.1k |
| SM london | +0.0k | +0.3k | +0.3k | -0.1k | +0.0k |
| ST asia | +12.6k | +2.2k | +3.4k | -1.0k | -0.2k |
| WT london | +1.0k | +0.0k | -0.2k | +0.3k | +0.1k |

  and vs the split:
| D6 session cell | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| KB asia | -0.7k | +0.1k | +0.2k | +0.9k | -0.1k |
| PE london | +0.3k | +1.0k | +0.8k | -0.7k | +0.3k |
| HM asia | +0.2k | +1.1k | +0.7k | -0.2k | -1.7k |
| HM nyam | +4.7k | -0.1k | -0.6k | -0.7k | +1.2k |
| SM asia | -0.1k | -0.3k | -1.0k | -0.1k | +0.4k |
| SM london | +0.1k | +0.3k | +0.4k | -0.4k | +0.1k |
| ST asia | +13.6k | +2.9k | +3.0k | +0.7k | +0.4k |
| WT london | -0.0k | -1.4k | -1.3k | -0.3k | +0.9k |

  The session-relative any-gate split (cid 48) vs the absolute split:
| D6 session cell | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| KB asia | -1.6k | -0.2k | -0.2k | -0.1k | +0.1k |
| PE london | +0.8k | +0.4k | +0.3k | -0.4k | +0.2k |
| HM asia | +0.1k | -0.7k | -0.7k | +0.1k | -0.4k |
| HM nyam | -0.1k | -1.9k | -1.7k | -0.7k | +0.2k |
| SM asia | -0.9k | -0.4k | -0.3k | -0.0k | +0.3k |
| SM london | +0.1k | -0.2k | -0.2k | -0.2k | -0.1k |
| ST asia | -0.7k | -0.4k | -0.2k | +1.0k | -0.3k |
| WT london | +0.2k | +0.3k | +0.3k | -0.6k | -0.1k |

## 4. What was learned
1. Session structure in (F, X, gate) is not recoverable causally: 36 walk-forward policy cells average -1 to -3k vs the fallback; per-session fits are noise on 100-3,000 trades per cell.
2. Session-relative thresholds (same-minute medians) leave the L2 add gate where it was: equal to the absolute gate within MDE, informative recently (book-shuffle rank 0.95-1.00 in L6M / HOLD), with PRE information lost; they do not rescue Asia / London specifically (see the session attribution of cell 48).
3. The only positive sign among the cycle's cells is the NQ-ahead-of-ES/RTY half-size modifier on C (+11.7k L6M, +8.6k HOLD, +4.9k PRE, +2.6k X' vs C; negative in 2026; MDE 25k): a forward-watch lead with the RTY leg doing the work, not significant.
4. Floor unchanged after four cycles.
## 5. Caveats
2026 ~5 weeks. c* on WF (EQR), SEL-only for selection; static policy cells are in-sample on SEL and excluded from selection. Session-relative multipliers were fixed after looking at fire rates only (first try discarded on rates, no outcome seen). MBO order lifetimes and queue position remain not run. Placebo draws 20. The hazard of choosing among 18 configs per cell is the reason policy cells are scored vs the fallback, not vs market.
## 6. Files
code l2vast/ds3/code/uf/ufe4_bits.py (session-relative bits), ufe4_div.py, ufe4_cells.py, ufe4_run.py, ufe4_stageA.py, ufe4_stageB.py, ufe4_plac.py, ufe4_gates.py, ufe4_report.py; outputs l2vast/ds3/out/uf/entry_c4/ (BL2/BS2/REL_s, D/SW, pre_sel.json, stageB_*, gates.pkl, placebo_*.pkl); cells l2vast/ds3/prereg/UF_ENTRY_C4_cells.csv.
