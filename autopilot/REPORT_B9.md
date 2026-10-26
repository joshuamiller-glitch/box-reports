# REPORT B9 - cross-instrument trend confirmation (ES/RTY) as sizing of the live pair

**Verdict: NO (0 FOUND, 0 LEAD).** Best of 12 registered sizing cells on clean (('T3', (12,), 'A', (0.75, 1.25))) changes weekly Sharpe by -0.27 on clean (H1 -0.53, H2 -0.60) against the +0.10 gate; the headline T1/A 50/150 is -0.52 clean. All 12 cells are negative on clean (range -0.86..-0.27).

Reading: the real uplift sits inside the matched random-size null (ranks 0.36-0.87 on clean/H1/H2; null median is itself -0.2 to -1.4 because random 0.5-1.5x sizing adds weekly variance with no information), so the ES/RTY agreement carries no usable information for the pair's entries; the 150% size on 'all agree' entries is just extra risk (mean multiplier 1.29), and constant-risk versions are also negative on clean.

## Setup
Pre-registered in PREREG_AUTOPILOT.md ('B9') before the first run. Sizing multiplier on new pair entries from the 5-min trend of NQ, ES, RTY at the last completed 5-min bar (T1 EMA9/21, T2 MACD 12/26, T3 12-bar return); scheme A (ES/RTY disagree -> low; NQ=ES=RTY -> high), scheme B (side-aware); multipliers (0.5,1.5) and (0.75,1.25). 12 cells. Engine: b11_nt8 `Cfg.sizefn` on the corrected live rows, so day/week locks, per-book rules and P&L scale natively (no approximation). Baseline B.Cfg(wk_floor=8,wk_loss_pb=None), clean process (asserted no b10_core). Fill model: live rows unchanged, 1 tick/side + $34.88 commission scaled with the multiplier; 2x slippage tested. Data: databento 1-min NQ/ES/RTY exist only from 2023-02 (pair window); no parameters fitted, so the whole window is out of sample for the definitions; selection among 12 cells on clean only.

## Stage 1: 12 cells, clean only (selection)
| cell | mean multiplier | clean Sharpe uplift |
|---|---|---|
| T1 (9, 21) A (0.5, 1.5) | 1.291 | -0.519 |
| T1 (9, 21) A (0.75, 1.25) | 1.146 | -0.553 |
| T1 (9, 21) B (0.5, 1.5) | 1.292 | -0.279 |
| T1 (9, 21) B (0.75, 1.25) | 1.146 | -0.430 |
| T2 (12, 26) A (0.5, 1.5) | 1.285 | -0.864 |
| T2 (12, 26) A (0.75, 1.25) | 1.142 | -0.462 |
| T2 (12, 26) B (0.5, 1.5) | 1.293 | -0.319 |
| T2 (12, 26) B (0.75, 1.25) | 1.146 | -0.501 |
| T3 (12,) A (0.5, 1.5) | 1.270 | -0.593 |
| T3 (12,) A (0.75, 1.25) | 1.135 | -0.272 |
| T3 (12,) B (0.5, 1.5) | 1.237 | -0.704 |
| T3 (12,) B (0.75, 1.25) | 1.118 | -0.273 |

Baseline clean weekly Sharpe 1.46.

## Cell ('T1', (9, 21), 'A', (0.5, 1.5)) (HEADLINE)
| span | uplift | net % | worst-week chg % | boot 5% | boot 95% | null p50 | null p95 | rank | 2x-slip uplift | constant-risk (mean mult 1) uplift |
|---|---|---|---|---|---|---|---|---|---|---|
| clean | -0.519 | -27.0 | -2.4 | -1.165 | +0.120 | -0.497 | +0.110 | 0.48 | -0.334 | -0.655 |
| H1 | -0.160 | +16.5 | -0.5 | -2.066 | +1.540 | -0.874 | +0.263 | 0.87 | -0.539 | +0.343 |
| H2 | -1.098 | -43.2 | +2.8 | -2.884 | +0.563 | -1.391 | -0.230 | 0.67 | -1.643 | +0.368 |
| all | -0.583 | -21.9 | -1.6 | -1.185 | -0.019 | -0.736 | -0.255 | 0.73 | -0.646 | -0.273 |

Mean multiplier 1.291. vs B.Cfg(): clean -0.417, H1 +1.107, H2 -0.547, all -0.222.
Plateau neighbours (uplift clean/H1/H2): (7, 16) (0.5, 1.5): -0.519/-0.715/-0.651; (11, 26) (0.5, 1.5): -0.854/-1.831/-1.012; (9, 21) (0.375, 1.625): -0.835/-0.341/-1.889; (9, 21) (0.625, 1.375): -0.356/-0.589/-0.715
Plateau neighbours keeping >=75% of uplift on all spans: 0/4.

## Cell ('T3', (12,), 'A', (0.75, 1.25)) (SELECTED)
| span | uplift | net % | worst-week chg % | boot 5% | boot 95% | null p50 | null p95 | rank | 2x-slip uplift | constant-risk (mean mult 1) uplift |
|---|---|---|---|---|---|---|---|---|---|---|
| clean | -0.272 | -11.3 | -6.9 | -0.797 | +0.210 | -0.216 | +0.123 | 0.40 | +0.053 | -0.239 |
| H1 | -0.533 | +1.1 | +0.7 | -2.214 | +0.815 | -0.329 | +0.675 | 0.36 | -0.994 | -0.384 |
| H2 | -0.599 | -14.1 | +4.9 | -2.037 | +0.689 | -0.760 | +0.247 | 0.60 | -0.699 | +0.095 |
| all | -0.363 | -9.4 | -6.1 | -0.870 | +0.103 | -0.327 | +0.001 | 0.45 | -0.259 | -0.140 |

Mean multiplier 1.135. vs B.Cfg(): clean -0.339, H1 -0.152, H2 -0.611, all -0.360.
Plateau neighbours (uplift clean/H1/H2): (9,) (0.75, 1.25): -0.383/+0.124/-0.089; (15,) (0.75, 1.25): -0.211/-1.337/-0.577; (12,) (0.625, 1.375): -0.287/-1.459/-1.606; (12,) (0.875, 1.125): -0.077/-0.632/-0.684
Plateau neighbours keeping >=75% of uplift on all spans: 0/4.

## Gate checklist (selected cell)
- Sharpe uplift >=0.10 clean/H1/H2: FAIL
- worst week not worse: FAIL
- random-size null p95: FAIL
- bootstrap lower>0: FAIL
- plateau: FAIL
- 2x slippage: FAIL

## Executability and limits
Sizing by 0.5/1.5 would need ES and RTY 5-min data in the NT8 strategy (multi-instrument data series, supported in NT8; Rithmic provides both), and 150% size means 12 NQ contracts per book vs the 8 base (margin up to 1.5x on those entries; intraday NQ margin at NTB is not changed by this study). The multiplier mean exceeds 1 in scheme A (about 1.29) so risk rises; constant-risk renormalised versions are reported alongside. Limits: only 3.7 years of ES/RTY data exist locally (pair window), no long-history development possible; signals use back-adjusted closes; slippage 1 tick/side not calibrated to live fills.

Runtime: stage 1 (60 account runs) 2.3 min, stage 2 (500-draw nulls per cell) see b9/s2.log; 5 workers.

DONE B9
