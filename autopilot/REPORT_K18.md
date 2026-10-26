# REPORT K18 - TARGET SCALED BY LAST-30-MIN REALISED VOL, STOP FIXED, live pair
**Verdict: NO. FOUND 0. All 8 target-scaling cells lose 0.85-1.9 weekly Sharpe on clean; selected p=1.0 clip [0.75,1.33] wider-when-vol-high: uplift -0.849 clean / -1.436 H1 / -2.122 H2 (needed +0.10 each); all-in -1.220; bootstrap CI [-1.86, -0.63] (entirely negative). Mean-neutral variant K18b also all negative (best clean -0.75)**

## Set-up and fill model
- Feature: rv30 = RMS of the 1-minute close changes over the 30 bars ending at the signal bar (changes across session breaks set to 0); ref = median of the 30-minute-sampled rv30 over the trailing 920 samples (about 20 trading days), shifted one sample; r = rv30/ref (median 1.55 at the pair's entries: quantiles 5/25/50/75/95 = 0.53/0.97/1.55/2.54/4.78). Target = 60 x clip(r^(sg p), lo, hi) rounded to 0.25; stop fixed 60; fixed lots.
- Replay: all 13,089 pair rows from their actual market fill on 1-second bars (ap_g11_c_core.rs, stop before target in the same second); control (60/60) reproduces the live rows (0 differ) and the account 1.46/2.83/2.30; rows closed externally (41%) keep their external exit. 1 tick/side + $34.88 per 8 lots; 2x slippage SLIP_PT 1.0.
- Grid (8): p {0.5,1.0} x clip {N=[0.75,1.33], W=[0.5,2.0]} x sg {+1 wider target when vol high, -1 control}. Selection clean-only. Null: r permuted across rows within book x year-month, whole grid, 100 draws, linear net swap, best-of statistic. Plateau: p x0.75/x1.25, clip half-width x0.75/x1.25.
- Variant K18b (pre-registered before it ran, reason stated in PREREG: the median ratio at entries is 1.55 so the MEAN target moved to 69-87 or 50-54 pts): r' = r / median of r over the previous 500 rows. Mean target then 61-68 pts. Selected (0.5, 'W', -1): -0.753/-1.818/-0.898, all-in -0.925, bootstrap CI [-1.52,-0.34], plateau 0.00, null all-in rank 0.07; every K18b cell is negative on clean (best -0.75). Disclosure: both tables print all spans for every cell.

## Grid, uplift per cell (weekly Sharpe vs the live pair; all spans printed for transparency, only the clean-selected cell was read for H1/H2)
| cell | clean | H1 | H2 | all-in | trades / mean target / stop% / tgt% |
|---|---|---|---|---|---|
| (0.5, 'N', 1) | -0.922 | -1.105 | -1.493 | -1.041 | 6932 / 69 / 24 / 34 |
| (0.5, 'N', -1) | -1.344 | -0.700 | -1.331 | -1.205 | 7096 / 54 / 20 / 38 |
| (0.5, 'W', 1) | -0.976 | -0.795 | -1.814 | -1.098 | 6753 / 78 / 26 / 31 |
| (0.5, 'W', -1) | -1.503 | -0.840 | -1.356 | -1.326 | 7126 / 51 / 19 / 39 |
| (1.0, 'N', 1) **(selected)** | -0.849 | -1.436 | -2.122 | -1.220 | 6815 / 70 / 24 / 33 |
| (1.0, 'N', -1) | -1.451 | -1.479 | -1.910 | -1.536 | 7061 / 54 / 20 / 38 |
| (1.0, 'W', 1) | -1.134 | -1.067 | -1.799 | -1.236 | 6555 / 87 / 27 / 29 |
| (1.0, 'W', -1) | -1.886 | -2.245 | -3.460 | -2.295 | 6766 / 50 / 19 / 40 |

## Result for the carried cell: (1.0, 'N', 1)
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 0.61 | -0.849 | -0.689 |
| H1 | 2.83 | 1.39 | -1.436 | -0.918 |
| H2 | 2.30 | 0.17 | -2.122 | -2.183 |
| all | 1.86 | 0.64 | -1.220 | -1.032 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank): clean -0.849 vs -0.073 / 0.00; H1 -1.436 vs +0.395 / 0.00; H2 -2.122 vs +0.059 / 0.00; all -1.220 vs -0.087 / 0.00
- bootstrap 90% CI of all-in uplift: [-1.857, -0.634]
- plateau: 0.00 of 4 neighbours keep >= 75% of the all-in uplift; neighbours: p x0.75 -1.142; p x1.25 -1.224; clip half-width x0.75 -1.156; clip half-width x1.25 -1.157
- alternating-month split (pre-registered): select (1.0, 'N', 1) (-0.617) reads -0.984 on the other half; select (1.0, 'N', 1) (-0.984) reads -0.617 on the other half
- H0 (2023-02-10..07-31) uplift: -0.810; replications counted (alt-month, H0): 0 of 2 needed (newest live weeks and ES/RTY not available / not applicable for this pair-row family)
- worst-week (candidate vs pair): clean -81.9k vs -81.9k; H1 -79.9k vs -78.3k; H2 -81.0k vs -82.5k; all -81.9k vs -82.5k; weekly corr with pair 0.787 (pair change, no hedge claim; worst-decile corr n/a)

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 0.61 | 0.97 | 1.35 | -79.7k | -78.9k | 406k | -81.9k | 46.7 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 1.39 | 2.61 | 1.85 | -79.0k | -78.7k | 201k | -79.9k | 46.4 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 cand | 0.17 | 0.31 | 0.17 | -79.8k | -79.1k | 399k | -81.0k | 58.3 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all cand | 0.64 | 1.07 | 2.26 | -79.7k | -79.0k | 438k | -81.9k | 49.4 |

## Reading
Scaling only the target with recent realised vol destroys the live edge in every direction, including the mean-neutral K18b: the pair's 60/60 bracket is pinned (D2 E6, G11-C, K12). Making the target larger when vol is high (sg=+1) moves 3-6 points of target-hit share into stop-outs (stop share rises 20->24-27% while target share falls 35->29-34%); making it smaller when vol is high (sg=-1) trades winners for earlier, smaller wins. Even the permuted-r null is about as bad (mean -0.27 clean in K18, -0.71 in K18b), meaning the cost is in perturbing the target per trade, not in the sign of the vol signal. Constant-risk framing is identical to the pair-change framing here (stop and lots unchanged).

## Executability / era / replication
NT8: a per-entry target computed from the last 30 one-minute closes would be strategy-side code (a rolling RMS and a median reference), straightforward; not recommended. Era: pair rows start 2023-02; pre-2023 n/a (ERA flag n/a); H0 reported above. Replication not met (H0 and alternating-month negative). Mechanism: depends on intraday vol clustering, not on current structure. Files: code/census/night_ins/ap_k18.py (K18VAR=b for K18b), ap_k18_rep.py, ap_k_lib.py; outputs/autopilot/k18/, k18b/.

DONE K18
