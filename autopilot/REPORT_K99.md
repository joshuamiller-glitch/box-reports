# REPORT K99 - INTRADAY TARGET RE-QUOTED TO THE NEAREST SESSION-VWAP BAND, live pair
**Verdict: NO. FOUND 0. All 4 band-step cells lose 1.2-4.5 weekly Sharpe all-in; selected step 0.5 sigma: uplift -1.305 clean / -0.224 H1 / -1.741 H2 (needed +0.10 each); all-in -1.223; bootstrap CI [-1.71, -0.79] (entirely negative). The real bands are less bad than shifted-day bands (all-in rank 1.00) but nowhere near the fixed 60-pt target**

## Set-up and fill model
- VWAP and sigma: the harness daily VWAP used by HM (resets at the UTC-4 day boundary) and the volume-weighted std of the 1-minute close around it. At each minute i from the entry the target is the band level vwap + j*s*sigma (j integer, including the VWAP itself) nearest to entry + side*60, computed from bar i-1 values, distance from the entry clamped to [20,100] pts; stop fixed 60; fixed lots; if s*sigma < 1 tick the target stays at 60.
- Replay: all 13,089 pair rows from their actual market fill on 1-second bars (stop before target in the same second). Control (clamp [60,60]) reproduces the live rows exactly (0 differ) and the account 1.46/2.83/2.30; rows closed externally (41%) keep their external exit. 1 tick/side + $34.88 per 8 lots; 2x slippage SLIP_PT 1.0.
- Grid (4): step s {0.5, 1.0, 1.5, 2.0} sigma. Selection clean-only. Null: band offsets (vwap - close) circularly shifted by a random whole number of 1,380-bar days (100 draws, selected cell, linear net swap). Plateau: s x0.75/x1.25, clamp [15,75] and [25,125].

## Grid, uplift per cell (weekly Sharpe vs the live pair; all spans printed for transparency, only the clean-selected cell was read for H1/H2)
| cell | clean | H1 | H2 | all-in | trades / stop% / target% |
|---|---|---|---|---|---|
| 0.5 **(selected)** | -1.305 | -0.224 | -1.741 | -1.223 | 7209 / 21 / 38 |
| 1.0 | -2.557 | -2.157 | -3.008 | -2.588 | 7427 / 20 / 38 |
| 1.5 | -4.017 | -5.411 | -4.945 | -4.462 | 6993 / 19 / 39 |
| 2.0 | -3.947 | -4.699 | -4.513 | -4.175 | 7061 / 20 / 38 |

## Result for the carried cell: 0.5
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 0.15 | -1.305 | -1.143 |
| H1 | 2.83 | 2.60 | -0.224 | -0.284 |
| H2 | 2.30 | 0.55 | -1.741 | -1.821 |
| all | 1.86 | 0.63 | -1.223 | -1.162 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank): clean -1.305 vs -1.138 / 0.40; H1 -0.224 vs -0.804 / 1.00; H2 -1.741 vs -2.113 / 1.00; all -1.223 vs -1.395 / 1.00
- bootstrap 90% CI of all-in uplift: [-1.710, -0.795]
- plateau: 0.00 of 4 neighbours keep >= 75% of the all-in uplift; neighbours: s x0.75 -0.923; s x1.25 -1.880; clamp [15,75] -1.235; clamp [25,125] -1.236
- alternating-month split (pre-registered): select 0.5 (-1.408) reads -0.999 on the other half; select 0.5 (-0.999) reads -1.408 on the other half
- H0 (2023-02-10..07-31) uplift: -0.631; replications counted (alt-month, H0): 0 of 2 needed (newest live weeks and ES/RTY not available / not applicable for this pair-row family)
- worst-week (candidate vs pair): clean -81.9k vs -81.9k; H1 -81.7k vs -78.3k; H2 -80.4k vs -82.5k; all -81.9k vs -82.5k; weekly corr with pair 0.890 (pair change, no hedge claim; worst-decile corr n/a)

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 0.15 | 0.25 | 0.32 | -79.3k | -78.5k | 436k | -81.9k | 52.4 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 2.60 | 6.05 | 3.91 | -79.3k | -69.8k | 154k | -81.7k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 cand | 0.55 | 0.93 | 0.86 | -80.2k | -79.4k | 216k | -80.4k | 52.8 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all cand | 0.63 | 1.09 | 2.13 | -80.0k | -78.9k | 436k | -81.9k | 50.6 |

## Reading
Re-quoting the target onto VWAP bands changes the target distance of most trades (clamp [20,100]; the band spacing at 0.5 sigma is a few points, so the target is simply the band nearest to +60 and moves with the VWAP all day), and every variant loses far more than any information in the bands can repay: wider spacing is worse (-2.6 at 1 sigma, -4.0 at 1.5-2 sigma) because the nearest band to +60 is then often the VWAP or a band 20 or 100 points away. The negative result matches the pinned 60/60 bracket seen in D2 E6, G11-C, K12 and K18. The shifted-bands null is worse still (mean all-in -1.5), which says the real bands carry a little structure (targets near VWAP bands are hit more often than targets at random distances) but not enough to beat the fixed target.

## Executability / era / replication
NT8: needs a per-bar update of the target order (ChangeOrder) and a session VWAP/sigma, strategy-side; not recommended. Era: pair rows start 2023-02; pre-2023 n/a (ERA flag n/a). Replication not met. Files: code/census/night_ins/ap_k99.py, ap_k99_rep.py, ap_k_lib.py; outputs/autopilot/k99/.

DONE K99
