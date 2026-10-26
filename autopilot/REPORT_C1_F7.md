# REPORT C1-F7 — MBO-recipe ML on ES and RTY bar features (autopilot cycle 1)

**Verdict: ES = NO. RTY = NO as a sleeve for the pair, with one standalone curiosity (RTY H240/8 leaves/tau .55) recorded as a weak LEAD. 0 FOUND.** Stated expectation (PREREG_AUTOPILOT.md): NO. FOUND = 0 from this family unless the table shows a cell passing all four gate columns (it does not: ES: 0, RTY: 0 cell-share combinations pass all four).

## What was run
- Frozen T3 S5 recipe (`outputs/t3/PREREG_T3_S5.md`): decision points every 5 min (ET 18:05-15:30, 09:00-09:58 blocked), 22 bar-only features, LightGBM binary classifier (fixed hyper-parameters), H in {60,120,240} x tau in {0.55,0.60,0.65} x leaves in {8,16} = 18 cells all reported, long if p>tau, short if p<1-tau, entry at the next 1-minute open, time exit at t+H or 16:54 ET, one position at a time. Walk-forward 6-month train / 1-month test, first test month 2023-08 (39 test months to 2026-10). Surrogate null: label series circularly shifted by >= 30 whole days, 20 runs per cell; selection-corrected test = best of 18 vs best of 18 per surrogate run.
- **Data:** Databento ohlcv-1m continuous front-by-volume (.v.0), data/autopilot/ohlcv1m. Session day = ET 18:00 -> 16:59, dominant instrument id per session day (roll safety). Span kept identical to T3 S5 (2023-02-09..2026-10-13, 951 session days; 232,406 decision points per instrument); earlier years in the file were NOT used for training, to keep the recipe identical.
- **Differences from T3 S5 (stated):** ES/RTY have no 1-second bars, so the three 1-second-derived features were replaced by 1-minute equivalents over the last 5 bars (realised vol of 1-min closes; tick-rule signed volume at 1-min / total volume; fraction of the last 5 one-minute highs setting a new running high). Prior-session high/low come from the same session-day construction.
- **Costs:** ES $50/pt, 0.5 tick/side (0.25 pt round trip = $12.50) + $4.36/contract commission (assumed, same as NQ); RTY $50/pt, 1 tick/side (0.20 pt round trip = $10) + $4.36 (assumed).
- **Scoring:** `t3_score.py` (pair = B11 Cfg(wk_floor=8,wk_loss_pb=None) computed in a clean process); the sleeve is scaled so its all-in weekly vol equals the pair's (contracts-eq column). Gates per the amended FOUND definition (own surrogate null p95 on standalone Sharpe, bootstrap lower bound, worst-decile correlation <= +0.30, +0.10 on clean/H1/H2).

## ES
| H | leaves | tau | trades | net/yr per contract $ | all-in wkly Sharpe | clean / H1 / H2 Sharpe | surrogate p95 | Sharpe rank | contracts-eq | corr (all / worst-decile) | additive 10% / 50% | const-risk 30% |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 60 | 8 | 0.55 | 12,674 | -47,237 | -1.55 | -1.37 / -2.80 / -0.98 | -0.97 | 50% | 14.4 | -0.06 / +0.28 | NO / NO | NO |
| 60 | 8 | 0.6 | 5,429 | -10,955 | -0.57 | -1.33 / 0.62 / 0.19 | -0.09 | 75% | 22.8 | -0.02 / -0.01 | NO / NO | NO |
| 60 | 8 | 0.65 | 1,344 | -10,910 | -0.92 | -1.73 / -0.36 / 0.90 | 0.59 | 25% | 37.1 | -0.06 / +0.19 | NO / NO | NO |
| 60 | 16 | 0.55 | 14,404 | -58,926 | -1.74 | -1.83 / -2.74 / -0.77 | -1.29 | 65% | 13.0 | -0.19 / -0.24 | NO / NO | NO |
| 60 | 16 | 0.6 | 9,207 | -29,759 | -1.20 | -1.61 / -0.43 / -0.84 | -0.26 | 65% | 17.8 | -0.08 / +0.09 | NO / NO | NO |
| 60 | 16 | 0.65 | 3,813 | -14,411 | -0.91 | -1.87 / 0.09 / 0.86 | 0.24 | 20% | 27.7 | -0.05 / +0.21 | NO / NO | NO |
| 120 | 8 | 0.55 | 7,808 | -43,542 | -1.18 | -1.12 / -2.79 / -0.36 | -0.02 | 20% | 11.9 | -0.12 / -0.08 | NO / NO | NO |
| 120 | 8 | 0.6 | 4,657 | -19,316 | -0.72 | -1.27 / 1.34 / -0.48 | 0.57 | 20% | 16.4 | -0.10 / -0.07 | NO / NO | NO |
| 120 | 8 | 0.65 | 1,809 | 1,096 | 0.07 | -0.84 / 1.55 / 1.38 | 0.59 | 60% | 26.7 | -0.13 / -0.08 | NO / NO | NO |
| 120 | 16 | 0.55 | 8,285 | -49,425 | -1.33 | -1.34 / -2.13 / -0.69 | -0.20 | 15% | 11.9 | -0.03 / -0.30 | NO / NO | NO |
| 120 | 16 | 0.6 | 6,540 | -19,935 | -0.66 | -0.53 / -1.24 / -0.64 | -0.06 | 55% | 14.6 | -0.01 / +0.22 | NO / NO | NO |
| 120 | 16 | 0.65 | 3,764 | -3,872 | -0.16 | -0.71 / 0.53 / 0.98 | 0.21 | 75% | 17.8 | -0.15 / -0.31 | NO / NO | NO |
| 240 | 8 | 0.55 | 4,517 | -1,238 | -0.03 | -0.32 / -0.61 / 1.32 | 0.68 | 75% | 12.2 | -0.14 / +0.18 | NO / NO | NO |
| 240 | 8 | 0.6 | 3,354 | -5,170 | -0.15 | 0.01 / -0.93 / -0.14 | 0.62 | 65% | 12.4 | -0.04 / -0.02 | NO / NO | NO |
| 240 | 8 | 0.65 | 1,791 | 14,408 | 0.43 | -0.14 / 0.81 / 2.93 | 0.60 | 85% | 13.2 | +0.02 / +0.03 | NO / NO | NO |
| 240 | 16 | 0.55 | 4,785 | -8,358 | -0.21 | -0.32 / -0.73 / 0.44 | 0.42 | 60% | 10.9 | -0.06 / -0.07 | NO / NO | NO |
| 240 | 16 | 0.6 | 4,066 | 17,659 | 0.40 | 0.30 / 0.35 / 0.78 | 0.82 | 80% | 10.1 | -0.05 / -0.07 | NO / NO | NO |
| 240 | 16 | 0.65 | 3,004 | -9,054 | -0.26 | -0.45 / -1.14 / 0.80 | 0.38 | 50% | 12.5 | -0.07 / -0.32 | NO / NO | NO |

Primary cell (H120, tau .60, leaves 8): 4,657 trades, net/yr per contract $-19,316, all-in weekly Sharpe -0.72 (clean -1.27 / H1 1.34 / H2 -0.48), rank 20% of its surrogate. Cells with positive all-in net: 3 of 18; cells with negative clean net: 16.
Selection-corrected test (best of 18 real vs best of 18 per surrogate run): best real Sharpe 0.43 vs surrogate-best median 0.44, p95 1.09 (rank 50%); best real net $58,022 vs surrogate-best p95 $130,324 (rank 70%).
FOUND-gate scan (72 cell x share additive combinations): +0.10 Sharpe on clean, H1 and H2: 0; own surrogate null p95 on standalone Sharpe: 0; bootstrap lower bound > 0: 0; worst-decile corr <= +0.30: 72; all four together: 0.

## RTY
| H | leaves | tau | trades | net/yr per contract $ | all-in wkly Sharpe | clean / H1 / H2 Sharpe | surrogate p95 | Sharpe rank | contracts-eq | corr (all / worst-decile) | additive 10% / 50% | const-risk 30% |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 60 | 8 | 0.55 | 12,140 | -52,223 | -2.80 | -3.33 / -1.41 / -2.24 | -1.92 | 40% | 23.6 | -0.11 / -0.59 | NO / NO | NO |
| 60 | 8 | 0.6 | 4,877 | -20,590 | -1.79 | -1.96 / -1.43 / -1.49 | -0.53 | 45% | 38.2 | -0.02 / +0.13 | NO / NO | NO |
| 60 | 8 | 0.65 | 1,359 | -4,931 | -0.91 | -1.47 / -0.84 / 0.34 | 0.18 | 30% | 81.7 | -0.02 / -0.06 | NO / NO | NO |
| 60 | 16 | 0.55 | 14,276 | -63,286 | -2.90 | -2.90 / -3.46 / -2.51 | -1.74 | 35% | 20.2 | -0.06 / -0.45 | NO / NO | NO |
| 60 | 16 | 0.6 | 8,791 | -32,037 | -2.00 | -1.97 / -1.20 / -2.59 | -1.38 | 65% | 27.5 | -0.04 / -0.11 | NO / NO | NO |
| 60 | 16 | 0.65 | 3,596 | -11,808 | -1.29 | -1.55 / -1.04 / -0.76 | -0.02 | 35% | 48.1 | -0.06 / -0.19 | NO / NO | NO |
| 120 | 8 | 0.55 | 7,514 | -21,340 | -1.04 | -1.01 / -2.09 / -0.48 | -0.30 | 65% | 21.4 | -0.03 / +0.05 | NO / NO | NO |
| 120 | 8 | 0.6 | 4,357 | -29,015 | -1.76 | -1.95 / -2.82 / -0.84 | 0.06 | 0% | 26.7 | -0.19 / -0.20 | NO / NO | NO |
| 120 | 8 | 0.65 | 1,711 | -2,036 | -0.22 | -0.82 / -0.75 / 1.72 | -0.04 | 80% | 47.7 | +0.11 / -0.43 | NO / NO | NO |
| 120 | 16 | 0.55 | 8,234 | -42,977 | -1.85 | -2.01 / -4.14 / 0.03 | -0.30 | 5% | 18.9 | -0.02 / -0.21 | NO / NO | NO |
| 120 | 16 | 0.6 | 6,386 | -26,749 | -1.32 | -1.06 / -2.02 / -1.72 | 0.03 | 55% | 21.7 | -0.15 / -0.11 | NO / NO | NO |
| 120 | 16 | 0.65 | 3,673 | -21,520 | -1.74 | -1.53 / -2.34 / -1.84 | 0.00 | 15% | 35.7 | -0.09 / +0.17 | NO / NO | NO |
| 240 | 8 | 0.55 | 4,476 | 14,414 | 0.60 | 0.34 / 0.12 / 1.75 | 0.05 | 100% | 18.4 | -0.09 / -0.40 | NO / NO | NO |
| 240 | 8 | 0.6 | 3,242 | -12,131 | -0.55 | -0.94 / 0.24 / 0.00 | 0.09 | 50% | 20.1 | -0.13 / -0.61 | NO / NO | NO |
| 240 | 8 | 0.65 | 1,731 | -14,863 | -0.96 | -1.41 / -1.02 / 0.35 | 0.55 | 35% | 28.4 | -0.14 / -0.07 | NO / NO | NO |
| 240 | 16 | 0.55 | 4,798 | 10,417 | 0.47 | 0.25 / -0.01 / 1.36 | -0.10 | 100% | 19.8 | -0.02 / -0.28 | NO / NO | NO |
| 240 | 16 | 0.6 | 4,050 | -20,032 | -0.79 | -1.11 / -0.71 / -0.02 | 0.28 | 30% | 17.4 | -0.08 / -0.10 | NO / NO | NO |
| 240 | 16 | 0.65 | 2,972 | -9,134 | -0.43 | -1.19 / 0.53 / 0.92 | 0.19 | 55% | 20.9 | -0.10 / -0.14 | NO / NO | NO |

Primary cell (H120, tau .60, leaves 8): 4,357 trades, net/yr per contract $-29,015, all-in weekly Sharpe -1.76 (clean -1.95 / H1 -2.82 / H2 -0.84), rank 0% of its surrogate. Cells with positive all-in net: 2 of 18; cells with negative clean net: 16.
Selection-corrected test (best of 18 real vs best of 18 per surrogate run): best real Sharpe 0.60 vs surrogate-best median -0.01, p95 0.55 (rank 95%); best real net $47,360 vs surrogate-best p95 $28,456 (rank 100%).
FOUND-gate scan (72 cell x share additive combinations): +0.10 Sharpe on clean, H1 and H2: 0; own surrogate null p95 on standalone Sharpe: 8; bootstrap lower bound > 0: 0; worst-decile corr <= +0.30: 72; all four together: 0.

## FOUND-gate summary
| instrument | combos | +0.10 on all 3 spans | own-null p95 | bootstrap > 0 | worst-decile corr <= 0.30 | all four |
|---|---|---|---|---|---|---|
| ES | 72 | 0 | 0 | 0 | 72 | 0 |
| RTY | 72 | 0 | 8 | 0 | 72 | 0 |

## Reading
**ES: NO, and it looks like what a timing-destroyed model produces.** Only 3 of 18 cells have positive all-in net, 16 of 18 are negative on clean, the best Sharpe is 0.43, no cell passes 85% of its own surrogate, and the selection-corrected ranks are 50% (Sharpe) and 70% (net).

**RTY: no usable sleeve, one cell worth a footnote.** H240 / 8 leaves / tau 0.55 has all-in Sharpe 0.60 (clean 0.34, H1 0.12, H2 1.75), net per year per contract $14.4k, and sits at the 100th percentile of its own surrogate on both Sharpe and net; its sibling (H240 / 16 leaves / tau 0.55) is also at 100%. The selection-corrected test is borderline: real best Sharpe 0.60 vs surrogate-best p95 0.55 (rank 95%, i.e. at the line, not above it) and best net $47k vs surrogate-best p95 $28k (rank 100%). So on RTY the standalone edge is not obviously timing-destroyed noise — unlike NQ and ES — but:
- it does not help the pair: additive uplift on H1 is negative (-0.01 at 10%, -0.33 at 50%), the bootstrap 90% interval at 50% share is [-0.28, +0.57], no cell passes the +0.10 on clean, H1 and H2 together (0 of 72 cell-share combinations), and the constant-risk version costs about 20% of net (limit 5%) for a 5% worst-week and 17% CVaR5 improvement;
- only 2 of 18 cells have positive all-in net (the two H240 / tau .55 siblings) and 16 of 18 are negative on clean, so the family-wide picture is the same as NQ's;
- sizing to the pair's volatility needs about 18 RTY contracts, and the edge is concentrated in H2 (Sharpe 1.75) with H1 about flat.
Its worst-decile correlation with the pair is -0.40 (n = 17 weeks, noisy), i.e. it would be a hedge claim, and the circular-shift null is the applicable gate for that; it does not pass the additive gates anyway. Recorded as a weak LEAD (standalone only); a longer RTY history (the purchased 2017+ bars exist) could test it out of sample before 2023 without touching the frozen recipe — not done here because the recipe and span were frozen to match T3 S5.

## Executability and margin
ES and RTY futures are CME products; executable at NinjaTrader Brokerage via Rithmic (Y, from general knowledge, unverified). The sleeve needs an external model-scoring process or exported signal schedule (new component). Margin not computed: nothing passes.

## Limits
5-minute decision grid; one-minute entry delay; fixed hyper-parameters; 1-minute substitutes for 1-second features (information loss vs NQ); commission assumed; label-shift null preserves day structure; slippage 1 tick/side (RTY) and 0.5 tick/side (ES) placeholders until live fills exist.

DONE C1_F7
