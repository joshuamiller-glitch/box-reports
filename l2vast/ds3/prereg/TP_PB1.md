# PREREG T-PULLBACK group PB1 (V2) - D3PB, DS3 T-PULLBACK, 2026-10-26T16:56:14Z
Research only. Cell = trend regime x pullback level x trigger -> DS2 bracket held FIXED (identical to T-ENTRY: 60-pt stop, 1.0R target, flat 16:55 ET, signal on completed bar i, entry at open of 1-min bar i+1, one open trade per book, signals blocked 15:00-17:59 ET, entry blocks 18:00-18:05 and 15:00-16:54, 10 lots as S10x1 slices with XJ stop-join, per-book locks day -2R/+5R / give-back 2R keep 50% / week floor 12R, R = $12,000, $4.84 RT). Pricing: MAPPED (1-s path-bracket sim firmlib.sim_rrt + year x exit-type corrected-P9 mapping, te_core.gen_entries/run_rows) for every cell, then DIRECT L2 replay (te_direct machinery, S10x1 + XJ3) for every PASS/CANDIDATE and the top 10 by mapped holdout Sharpe (stated in the report).
Definitions (all bar-based, NT8-implementable; k-min aggregates are used only when their bucket is complete at the signal bar; truncation-invariance audit tp_trunc.py: 97 cells, data cut at 62%, 0 mismatches):
- Regimes: ST10 = Supertrend(ATR n=10 Wilder, mult 3.0, median price (H+L)/2) on 10-min bars (the T-ENTRY TE6 centre definition); EMA200 = sign(5-min close - EMA200 of 5-min closes); HMA55 = sign of the 1-bar change of the Hull MA(55) of 5-min closes; PRIORDIR = sign(close - open) of the previous complete 18:00-18:00 session. Direction 0/NaN = no trade. Long in an up regime, short in a down regime; long and short are scored separately and combined.
- Pullback levels: VWAP = session VWAP (reset 18:00, 1-min typical price x volume, includes the signal bar); EMA1 = EMA20 of 1-min closes; EMA5 = EMA20 of 5-min closes; KELT = EMA20 of 5-min typical price (Keltner mid; the ATR bands are not used); FLIP = close of the last 10-min Supertrend flip bar; SWZ = 38.2% retrace of the last confirmed 5-min fractal swing (2-bar fractals confirmed 2 bars later; up-leg = last swing high and the swing low preceding it) with the touch void if price already went beyond the 61.8% retrace. A pullback TOUCH (uptrend) = the bar's low <= level while the previous bar's low was above the previous level (edge); mirrored for shorts. Armed for W = 30 min (bars) after the touch (first touch of each pullback), cancelled if the regime flips.
- Triggers (while armed, evaluated on each completed 1-min bar from the touch bar on): T1 = bullish 1-min bar (close > open) that closes beyond the level in the trend direction (mirrored for shorts); T2 = close beyond the touch bar's extreme (high for long, low for short), strictly after the touch bar; T3 = RSI(2) of 1-min closes (Wilder) < 10 for longs, > 90 for shorts, in the regime direction. One trade per arming.
- Coinciding with earlier work: FLIP x ST10 cells use the same flip price as D3P B1 (a47186c82e55618e5) but without B1's fixed-point retrace and with the 3 triggers; the ST10/EMA* cells are NOT the same rule as B1 (B1 enters on a limit retrace of 10/20/30 pts after a flip; here a touch of a moving average followed by a close back); no rule is re-tested under a new name.
Windows: selection WF-PRE 2024-02..2025-06; holdout 2025-07+ (ONE look for the track, logged via s48score.log_holdout_look after the PRE text is written; books reusing T-ENTRY series have had earlier looks - the T-PULLBACK cells are new series); second holdout 2023-04..2024-01 (looked at together; no parameter is fitted anywhere).
Regime (volatility) columns: P(quiet) from the D3R as-of-session-open LightGBM walk-forward forecaster (l2vast/ds3/out/TA/pquiet_series.parquet; AUC .858; truncation-audited by D3R): predicted-quiet = P >= 0.6, predicted-wide = P < 0.6 (same threshold as D3R TA1), sessions without a forecast are excluded from both columns. The regime columns are computed by splitting the executed trades of the all-sessions book by the entry session (lock engine run once on the whole book; this is a post-hoc split, not a re-run of a gated book).
Columns per cell: trades/wk (cells < 3/wk are flagged LOW-FREQUENCY, never dropped), win rate, avg win/loss, weekly mean/SD, long and short separately, predicted-quiet and predicted-wide, paired vs ST10 (per-trade, nearest same-side ST10 trade within +/-15 min; session-block bootstrap CI and MDE via s48score.paired_score) and per-week difference with week-block CI, corr to ST10/HM10, 2x-cost WF, timing-destroyed placebo (40 draws, same count, side and ET-hour mix).
Verdict (object = signal): (1) trades/wk >= 3, (2) WF-PRE weekly mean > 0 and WF week-block CI excludes 0, (3) holdout weekly mean > 0, (4) second-holdout > 0, (5) placebo rank on PRE >= 0.95, (6) 2x-cost WF > 0. PASS = all; CANDIDATE = all but one; else DEAD. A PASS gets a 3x3 neighbour grid. Best-of-N is reported with N = cells scored in this track (all groups); the ledger gets the cell counts of each group.
Predicted effect: see per cell; every predicted effect is below the MDE, so verdicts rest on sign agreement over the three windows, the placebo and cost stress.
## Cells (JSON)
```json
[
 {
  "cell": "PB_ST10_VWAP_T1",
  "family": "pb",
  "params": {
   "reg": "ST10",
   "pb": "VWAP",
   "trig": "T1",
   "W": 30,
   "second": 0,
   "fade": false
  },
  "flag": "NT8-bars",
  "mechanism": "When the 10-minute Supertrend (ATR10 x 3.0, TE6 definition) is up/down, a first return to session VWAP within 30 min followed by the first 1-minute close back in the trend direction (bullish bar closing beyond the level) resumes the trend into the 60-pt bracket at a better price than a trend-bar entry",
  "predicted_effect": "pullback entries trade a better price than the flip/trend-bar entry, but skip trends that never retrace: +0.0 to +0.5 pt/trade net vs the same-day flip entry; below the paired MDE (3.5-8 pt/trade)",
  "detectable_effect": "MDE at 80% power, 5% two-sided (2.8 x SE): standalone weekly mean ~$11-18k/wk on WF-PRE (75 wk, candidate weekly SD $30-56k at 10 lots), ~$8-13k/wk on WF (143 wk); standalone per-trade ~3 pts (n~2.5k trades); paired vs ST/HM per overlapping trade ~8-14 pts (only ~15-30% of candidate trades overlap an ST/HM trade); paired weekly diff MDE ~$20k/wk. Predicted effect is BELOW MDE: run level = screen (sign + placebo + second holdout), a PASS cannot be established by power alone",
  "object": "signal",
  "nearest_scored_cell": "FAILPRED STEP2 C4/C6/C8 (VWAP scalps) and T-ENTRY TE3 vwb",
  "nearest_result": "DEAD: no gross edge, 75-90% stop-outs; vwb bands DEAD"
 },
 {
  "cell": "PB_ST10_VWAP_T2",
  "family": "pb",
  "params": {
   "reg": "ST10",
   "pb": "VWAP",
   "trig": "T2",
   "W": 30,
   "second": 0,
   "fade": false
  },
  "flag": "NT8-bars",
  "mechanism": "When the 10-minute Supertrend (ATR10 x 3.0, TE6 definition) is up/down, a first return to session VWAP within 30 min followed by a close beyond the pullback bar's extreme resumes the trend into the 60-pt bracket at a better price than a trend-bar entry",
  "predicted_effect": "pullback entries trade a better price than the flip/trend-bar entry, but skip trends that never retrace: +0.0 to +0.5 pt/trade net vs the same-day flip entry; below the paired MDE (3.5-8 pt/trade)",
  "detectable_effect": "MDE at 80% power, 5% two-sided (2.8 x SE): standalone weekly mean ~$11-18k/wk on WF-PRE (75 wk, candidate weekly SD $30-56k at 10 lots), ~$8-13k/wk on WF (143 wk); standalone per-trade ~3 pts (n~2.5k trades); paired vs ST/HM per overlapping trade ~8-14 pts (only ~15-30% of candidate trades overlap an ST/HM trade); paired weekly diff MDE ~$20k/wk. Predicted effect is BELOW MDE: run level = screen (sign + placebo + second holdout), a PASS cannot be established by power alone",
  "object": "signal",
  "nearest_scored_cell": "FAILPRED STEP2 C4/C6/C8 (VWAP scalps) and T-ENTRY TE3 vwb",
  "nearest_result": "DEAD: no gross edge, 75-90% stop-outs; vwb bands DEAD"
 },
 {
  "cell": "PB_ST10_VWAP_T3",
  "family": "pb",
  "params": {
   "reg": "ST10",
   "pb": "VWAP",
   "trig": "T3",
   "W": 30,
   "second": 0,
   "fade": false
  },
  "flag": "NT8-bars",
  "mechanism": "When the 10-minute Supertrend (ATR10 x 3.0, TE6 definition) is up/down, a first return to session VWAP within 30 min followed by 1-minute RSI(2) < 10 (> 90 for shorts) inside the trend resumes the trend into the 60-pt bracket at a better price than a trend-bar entry",
  "predicted_effect": "pullback entries trade a better price than the flip/trend-bar entry, but skip trends that never retrace: +0.0 to +0.5 pt/trade net vs the same-day flip entry; below the paired MDE (3.5-8 pt/trade)",
  "detectable_effect": "MDE at 80% power, 5% two-sided (2.8 x SE): standalone weekly mean ~$11-18k/wk on WF-PRE (75 wk, candidate weekly SD $30-56k at 10 lots), ~$8-13k/wk on WF (143 wk); standalone per-trade ~3 pts (n~2.5k trades); paired vs ST/HM per overlapping trade ~8-14 pts (only ~15-30% of candidate trades overlap an ST/HM trade); paired weekly diff MDE ~$20k/wk. Predicted effect is BELOW MDE: run level = screen (sign + placebo + second holdout), a PASS cannot be established by power alone",
  "object": "signal",
  "nearest_scored_cell": "FAILPRED STEP2 C4/C6/C8 (VWAP scalps) and T-ENTRY TE3 vwb",
  "nearest_result": "DEAD: no gross edge, 75-90% stop-outs; vwb bands DEAD"
 },
 {
  "cell": "PB_ST10_EMA1_T1",
  "family": "pb",
  "params": {
   "reg": "ST10",
   "pb": "EMA1",
   "trig": "T1",
   "W": 30,
   "second": 0,
   "fade": false
  },
  "flag": "NT8-bars",
  "mechanism": "When the 10-minute Supertrend (ATR10 x 3.0, TE6 definition) is up/down, a first return to the 1-minute EMA20 within 30 min followed by the first 1-minute close back in the trend direction (bullish bar closing beyond the level) resumes the trend into the 60-pt bracket at a better price than a trend-bar entry",
  "predicted_effect": "pullback entries trade a better price than the flip/trend-bar entry, but skip trends that never retrace: +0.0 to +0.5 pt/trade net vs the same-day flip entry; below the paired MDE (3.5-8 pt/trade)",
  "detectable_effect": "MDE at 80% power, 5% two-sided (2.8 x SE): standalone weekly mean ~$11-18k/wk on WF-PRE (75 wk, candidate weekly SD $30-56k at 10 lots), ~$8-13k/wk on WF (143 wk); standalone per-trade ~3 pts (n~2.5k trades); paired vs ST/HM per overlapping trade ~8-14 pts (only ~15-30% of candidate trades overlap an ST/HM trade); paired weekly diff MDE ~$20k/wk. Predicted effect is BELOW MDE: run level = screen (sign + placebo + second holdout), a PASS cannot be established by power alone",
  "object": "signal",
  "nearest_scored_cell": "PULLBACK study 2026-10-16 (autopilot/REPORT_PULLBACK.md; 4,775 cells) and T-ENTRY TE6_st10m (flip entry PASS)",
  "nearest_result": "pullback study: 0 of 41 levels respected, finalists decayed; TE6 Supertrend flip entry (no pullback) PASS WF $8.7k/wk"
 },
 {
  "cell": "PB_ST10_EMA1_T2",
  "family": "pb",
  "params": {
   "reg": "ST10",
   "pb": "EMA1",
   "trig": "T2",
   "W": 30,
   "second": 0,
   "fade": false
  },
  "flag": "NT8-bars",
  "mechanism": "When the 10-minute Supertrend (ATR10 x 3.0, TE6 definition) is up/down, a first return to the 1-minute EMA20 within 30 min followed by a close beyond the pullback bar's extreme resumes the trend into the 60-pt bracket at a better price than a trend-bar entry",
  "predicted_effect": "pullback entries trade a better price than the flip/trend-bar entry, but skip trends that never retrace: +0.0 to +0.5 pt/trade net vs the same-day flip entry; below the paired MDE (3.5-8 pt/trade)",
  "detectable_effect": "MDE at 80% power, 5% two-sided (2.8 x SE): standalone weekly mean ~$11-18k/wk on WF-PRE (75 wk, candidate weekly SD $30-56k at 10 lots), ~$8-13k/wk on WF (143 wk); standalone per-trade ~3 pts (n~2.5k trades); paired vs ST/HM per overlapping trade ~8-14 pts (only ~15-30% of candidate trades overlap an ST/HM trade); paired weekly diff MDE ~$20k/wk. Predicted effect is BELOW MDE: run level = screen (sign + placebo + second holdout), a PASS cannot be established by power alone",
  "object": "signal",
  "nearest_scored_cell": "PULLBACK study 2026-10-16 (autopilot/REPORT_PULLBACK.md; 4,775 cells) and T-ENTRY TE6_st10m (flip entry PASS)",
  "nearest_result": "pullback study: 0 of 41 levels respected, finalists decayed; TE6 Supertrend flip entry (no pullback) PASS WF $8.7k/wk"
 },
 {
  "cell": "PB_ST10_EMA1_T3",
  "family": "pb",
  "params": {
   "reg": "ST10",
   "pb": "EMA1",
   "trig": "T3",
   "W": 30,
   "second": 0,
   "fade": false
  },
  "flag": "NT8-bars",
  "mechanism": "When the 10-minute Supertrend (ATR10 x 3.0, TE6 definition) is up/down, a first return to the 1-minute EMA20 within 30 min followed by 1-minute RSI(2) < 10 (> 90 for shorts) inside the trend resumes the trend into the 60-pt bracket at a better price than a trend-bar entry",
  "predicted_effect": "pullback entries trade a better price than the flip/trend-bar entry, but skip trends that never retrace: +0.0 to +0.5 pt/trade net vs the same-day flip entry; below the paired MDE (3.5-8 pt/trade)",
  "detectable_effect": "MDE at 80% power, 5% two-sided (2.8 x SE): standalone weekly mean ~$11-18k/wk on WF-PRE (75 wk, candidate weekly SD $30-56k at 10 lots), ~$8-13k/wk on WF (143 wk); standalone per-trade ~3 pts (n~2.5k trades); paired vs ST/HM per overlapping trade ~8-14 pts (only ~15-30% of candidate trades overlap an ST/HM trade); paired weekly diff MDE ~$20k/wk. Predicted effect is BELOW MDE: run level = screen (sign + placebo + second holdout), a PASS cannot be established by power alone",
  "object": "signal",
  "nearest_scored_cell": "dip-buy sleeves (RSI2 at the close) and TA_NQ_RSI2_t10_plain",
  "nearest_result": "DEAD as DS3 books, 0.4-0.9 trades/wk; here it is intraday and trend-conditioned"
 },
 {
  "cell": "PB_ST10_EMA5_T1",
  "family": "pb",
  "params": {
   "reg": "ST10",
   "pb": "EMA5",
   "trig": "T1",
   "W": 30,
   "second": 0,
   "fade": false
  },
  "flag": "NT8-bars",
  "mechanism": "When the 10-minute Supertrend (ATR10 x 3.0, TE6 definition) is up/down, a first return to the 5-minute EMA20 within 30 min followed by the first 1-minute close back in the trend direction (bullish bar closing beyond the level) resumes the trend into the 60-pt bracket at a better price than a trend-bar entry",
  "predicted_effect": "pullback entries trade a better price than the flip/trend-bar entry, but skip trends that never retrace: +0.0 to +0.5 pt/trade net vs the same-day flip entry; below the paired MDE (3.5-8 pt/trade)",
  "detectable_effect": "MDE at 80% power, 5% two-sided (2.8 x SE): standalone weekly mean ~$11-18k/wk on WF-PRE (75 wk, candidate weekly SD $30-56k at 10 lots), ~$8-13k/wk on WF (143 wk); standalone per-trade ~3 pts (n~2.5k trades); paired vs ST/HM per overlapping trade ~8-14 pts (only ~15-30% of candidate trades overlap an ST/HM trade); paired weekly diff MDE ~$20k/wk. Predicted effect is BELOW MDE: run level = screen (sign + placebo + second holdout), a PASS cannot be established by power alone",
  "object": "signal",
  "nearest_scored_cell": "PULLBACK study 2026-10-16 (autopilot/REPORT_PULLBACK.md; 4,775 cells) and T-ENTRY TE6_st10m (flip entry PASS)",
  "nearest_result": "pullback study: 0 of 41 levels respected, finalists decayed; TE6 Supertrend flip entry (no pullback) PASS WF $8.7k/wk"
 },
 {
  "cell": "PB_ST10_EMA5_T2",
  "family": "pb",
  "params": {
   "reg": "ST10",
   "pb": "EMA5",
   "trig": "T2",
   "W": 30,
   "second": 0,
   "fade": false
  },
  "flag": "NT8-bars",
  "mechanism": "When the 10-minute Supertrend (ATR10 x 3.0, TE6 definition) is up/down, a first return to the 5-minute EMA20 within 30 min followed by a close beyond the pullback bar's extreme resumes the trend into the 60-pt bracket at a better price than a trend-bar entry",
  "predicted_effect": "pullback entries trade a better price than the flip/trend-bar entry, but skip trends that never retrace: +0.0 to +0.5 pt/trade net vs the same-day flip entry; below the paired MDE (3.5-8 pt/trade)",
  "detectable_effect": "MDE at 80% power, 5% two-sided (2.8 x SE): standalone weekly mean ~$11-18k/wk on WF-PRE (75 wk, candidate weekly SD $30-56k at 10 lots), ~$8-13k/wk on WF (143 wk); standalone per-trade ~3 pts (n~2.5k trades); paired vs ST/HM per overlapping trade ~8-14 pts (only ~15-30% of candidate trades overlap an ST/HM trade); paired weekly diff MDE ~$20k/wk. Predicted effect is BELOW MDE: run level = screen (sign + placebo + second holdout), a PASS cannot be established by power alone",
  "object": "signal",
  "nearest_scored_cell": "PULLBACK study 2026-10-16 (autopilot/REPORT_PULLBACK.md; 4,775 cells) and T-ENTRY TE6_st10m (flip entry PASS)",
  "nearest_result": "pullback study: 0 of 41 levels respected, finalists decayed; TE6 Supertrend flip entry (no pullback) PASS WF $8.7k/wk"
 },
 {
  "cell": "PB_ST10_EMA5_T3",
  "family": "pb",
  "params": {
   "reg": "ST10",
   "pb": "EMA5",
   "trig": "T3",
   "W": 30,
   "second": 0,
   "fade": false
  },
  "flag": "NT8-bars",
  "mechanism": "When the 10-minute Supertrend (ATR10 x 3.0, TE6 definition) is up/down, a first return to the 5-minute EMA20 within 30 min followed by 1-minute RSI(2) < 10 (> 90 for shorts) inside the trend resumes the trend into the 60-pt bracket at a better price than a trend-bar entry",
  "predicted_effect": "pullback entries trade a better price than the flip/trend-bar entry, but skip trends that never retrace: +0.0 to +0.5 pt/trade net vs the same-day flip entry; below the paired MDE (3.5-8 pt/trade)",
  "detectable_effect": "MDE at 80% power, 5% two-sided (2.8 x SE): standalone weekly mean ~$11-18k/wk on WF-PRE (75 wk, candidate weekly SD $30-56k at 10 lots), ~$8-13k/wk on WF (143 wk); standalone per-trade ~3 pts (n~2.5k trades); paired vs ST/HM per overlapping trade ~8-14 pts (only ~15-30% of candidate trades overlap an ST/HM trade); paired weekly diff MDE ~$20k/wk. Predicted effect is BELOW MDE: run level = screen (sign + placebo + second holdout), a PASS cannot be established by power alone",
  "object": "signal",
  "nearest_scored_cell": "dip-buy sleeves (RSI2 at the close) and TA_NQ_RSI2_t10_plain",
  "nearest_result": "DEAD as DS3 books, 0.4-0.9 trades/wk; here it is intraday and trend-conditioned"
 },
 {
  "cell": "PB_ST10_KELT_T1",
  "family": "pb",
  "params": {
   "reg": "ST10",
   "pb": "KELT",
   "trig": "T1",
   "W": 30,
   "second": 0,
   "fade": false
  },
  "flag": "NT8-bars",
  "mechanism": "When the 10-minute Supertrend (ATR10 x 3.0, TE6 definition) is up/down, a first return to the Keltner mid (5-min EMA20 of typical price) within 30 min followed by the first 1-minute close back in the trend direction (bullish bar closing beyond the level) resumes the trend into the 60-pt bracket at a better price than a trend-bar entry",
  "predicted_effect": "pullback entries trade a better price than the flip/trend-bar entry, but skip trends that never retrace: +0.0 to +0.5 pt/trade net vs the same-day flip entry; below the paired MDE (3.5-8 pt/trade)",
  "detectable_effect": "MDE at 80% power, 5% two-sided (2.8 x SE): standalone weekly mean ~$11-18k/wk on WF-PRE (75 wk, candidate weekly SD $30-56k at 10 lots), ~$8-13k/wk on WF (143 wk); standalone per-trade ~3 pts (n~2.5k trades); paired vs ST/HM per overlapping trade ~8-14 pts (only ~15-30% of candidate trades overlap an ST/HM trade); paired weekly diff MDE ~$20k/wk. Predicted effect is BELOW MDE: run level = screen (sign + placebo + second holdout), a PASS cannot be established by power alone",
  "object": "signal",
  "nearest_scored_cell": "PULLBACK study 2026-10-16 (autopilot/REPORT_PULLBACK.md; 4,775 cells) and T-ENTRY TE6_st10m (flip entry PASS)",
  "nearest_result": "pullback study: 0 of 41 levels respected, finalists decayed; TE6 Supertrend flip entry (no pullback) PASS WF $8.7k/wk"
 },
 {
  "cell": "PB_ST10_KELT_T2",
  "family": "pb",
  "params": {
   "reg": "ST10",
   "pb": "KELT",
   "trig": "T2",
   "W": 30,
   "second": 0,
   "fade": false
  },
  "flag": "NT8-bars",
  "mechanism": "When the 10-minute Supertrend (ATR10 x 3.0, TE6 definition) is up/down, a first return to the Keltner mid (5-min EMA20 of typical price) within 30 min followed by a close beyond the pullback bar's extreme resumes the trend into the 60-pt bracket at a better price than a trend-bar entry",
  "predicted_effect": "pullback entries trade a better price than the flip/trend-bar entry, but skip trends that never retrace: +0.0 to +0.5 pt/trade net vs the same-day flip entry; below the paired MDE (3.5-8 pt/trade)",
  "detectable_effect": "MDE at 80% power, 5% two-sided (2.8 x SE): standalone weekly mean ~$11-18k/wk on WF-PRE (75 wk, candidate weekly SD $30-56k at 10 lots), ~$8-13k/wk on WF (143 wk); standalone per-trade ~3 pts (n~2.5k trades); paired vs ST/HM per overlapping trade ~8-14 pts (only ~15-30% of candidate trades overlap an ST/HM trade); paired weekly diff MDE ~$20k/wk. Predicted effect is BELOW MDE: run level = screen (sign + placebo + second holdout), a PASS cannot be established by power alone",
  "object": "signal",
  "nearest_scored_cell": "PULLBACK study 2026-10-16 (autopilot/REPORT_PULLBACK.md; 4,775 cells) and T-ENTRY TE6_st10m (flip entry PASS)",
  "nearest_result": "pullback study: 0 of 41 levels respected, finalists decayed; TE6 Supertrend flip entry (no pullback) PASS WF $8.7k/wk"
 },
 {
  "cell": "PB_ST10_KELT_T3",
  "family": "pb",
  "params": {
   "reg": "ST10",
   "pb": "KELT",
   "trig": "T3",
   "W": 30,
   "second": 0,
   "fade": false
  },
  "flag": "NT8-bars",
  "mechanism": "When the 10-minute Supertrend (ATR10 x 3.0, TE6 definition) is up/down, a first return to the Keltner mid (5-min EMA20 of typical price) within 30 min followed by 1-minute RSI(2) < 10 (> 90 for shorts) inside the trend resumes the trend into the 60-pt bracket at a better price than a trend-bar entry",
  "predicted_effect": "pullback entries trade a better price than the flip/trend-bar entry, but skip trends that never retrace: +0.0 to +0.5 pt/trade net vs the same-day flip entry; below the paired MDE (3.5-8 pt/trade)",
  "detectable_effect": "MDE at 80% power, 5% two-sided (2.8 x SE): standalone weekly mean ~$11-18k/wk on WF-PRE (75 wk, candidate weekly SD $30-56k at 10 lots), ~$8-13k/wk on WF (143 wk); standalone per-trade ~3 pts (n~2.5k trades); paired vs ST/HM per overlapping trade ~8-14 pts (only ~15-30% of candidate trades overlap an ST/HM trade); paired weekly diff MDE ~$20k/wk. Predicted effect is BELOW MDE: run level = screen (sign + placebo + second holdout), a PASS cannot be established by power alone",
  "object": "signal",
  "nearest_scored_cell": "dip-buy sleeves (RSI2 at the close) and TA_NQ_RSI2_t10_plain",
  "nearest_result": "DEAD as DS3 books, 0.4-0.9 trades/wk; here it is intraday and trend-conditioned"
 },
 {
  "cell": "PB_ST10_FLIP_T1",
  "family": "pb",
  "params": {
   "reg": "ST10",
   "pb": "FLIP",
   "trig": "T1",
   "W": 30,
   "second": 0,
   "fade": false
  },
  "flag": "NT8-bars",
  "mechanism": "When the 10-minute Supertrend (ATR10 x 3.0, TE6 definition) is up/down, a first return to the last 10-min Supertrend flip level within 30 min followed by the first 1-minute close back in the trend direction (bullish bar closing beyond the level) resumes the trend into the 60-pt bracket at a better price than a trend-bar entry",
  "predicted_effect": "pullback entries trade a better price than the flip/trend-bar entry, but skip trends that never retrace: +0.0 to +0.5 pt/trade net vs the same-day flip entry; below the paired MDE (3.5-8 pt/trade)",
  "detectable_effect": "MDE at 80% power, 5% two-sided (2.8 x SE): standalone weekly mean ~$11-18k/wk on WF-PRE (75 wk, candidate weekly SD $30-56k at 10 lots), ~$8-13k/wk on WF (143 wk); standalone per-trade ~3 pts (n~2.5k trades); paired vs ST/HM per overlapping trade ~8-14 pts (only ~15-30% of candidate trades overlap an ST/HM trade); paired weekly diff MDE ~$20k/wk. Predicted effect is BELOW MDE: run level = screen (sign + placebo + second holdout), a PASS cannot be established by power alone",
  "object": "signal",
  "nearest_scored_cell": "PULLBACK study 2026-10-16 (autopilot/REPORT_PULLBACK.md; 4,775 cells) and T-ENTRY TE6_st10m (flip entry PASS)",
  "nearest_result": "pullback study: 0 of 41 levels respected, finalists decayed; TE6 Supertrend flip entry (no pullback) PASS WF $8.7k/wk"
 },
 {
  "cell": "PB_ST10_FLIP_T2",
  "family": "pb",
  "params": {
   "reg": "ST10",
   "pb": "FLIP",
   "trig": "T2",
   "W": 30,
   "second": 0,
   "fade": false
  },
  "flag": "NT8-bars",
  "mechanism": "When the 10-minute Supertrend (ATR10 x 3.0, TE6 definition) is up/down, a first return to the last 10-min Supertrend flip level within 30 min followed by a close beyond the pullback bar's extreme resumes the trend into the 60-pt bracket at a better price than a trend-bar entry",
  "predicted_effect": "pullback entries trade a better price than the flip/trend-bar entry, but skip trends that never retrace: +0.0 to +0.5 pt/trade net vs the same-day flip entry; below the paired MDE (3.5-8 pt/trade)",
  "detectable_effect": "MDE at 80% power, 5% two-sided (2.8 x SE): standalone weekly mean ~$11-18k/wk on WF-PRE (75 wk, candidate weekly SD $30-56k at 10 lots), ~$8-13k/wk on WF (143 wk); standalone per-trade ~3 pts (n~2.5k trades); paired vs ST/HM per overlapping trade ~8-14 pts (only ~15-30% of candidate trades overlap an ST/HM trade); paired weekly diff MDE ~$20k/wk. Predicted effect is BELOW MDE: run level = screen (sign + placebo + second holdout), a PASS cannot be established by power alone",
  "object": "signal",
  "nearest_scored_cell": "PULLBACK study 2026-10-16 (autopilot/REPORT_PULLBACK.md; 4,775 cells) and T-ENTRY TE6_st10m (flip entry PASS)",
  "nearest_result": "pullback study: 0 of 41 levels respected, finalists decayed; TE6 Supertrend flip entry (no pullback) PASS WF $8.7k/wk"
 },
 {
  "cell": "PB_ST10_FLIP_T3",
  "family": "pb",
  "params": {
   "reg": "ST10",
   "pb": "FLIP",
   "trig": "T3",
   "W": 30,
   "second": 0,
   "fade": false
  },
  "flag": "NT8-bars",
  "mechanism": "When the 10-minute Supertrend (ATR10 x 3.0, TE6 definition) is up/down, a first return to the last 10-min Supertrend flip level within 30 min followed by 1-minute RSI(2) < 10 (> 90 for shorts) inside the trend resumes the trend into the 60-pt bracket at a better price than a trend-bar entry",
  "predicted_effect": "pullback entries trade a better price than the flip/trend-bar entry, but skip trends that never retrace: +0.0 to +0.5 pt/trade net vs the same-day flip entry; below the paired MDE (3.5-8 pt/trade)",
  "detectable_effect": "MDE at 80% power, 5% two-sided (2.8 x SE): standalone weekly mean ~$11-18k/wk on WF-PRE (75 wk, candidate weekly SD $30-56k at 10 lots), ~$8-13k/wk on WF (143 wk); standalone per-trade ~3 pts (n~2.5k trades); paired vs ST/HM per overlapping trade ~8-14 pts (only ~15-30% of candidate trades overlap an ST/HM trade); paired weekly diff MDE ~$20k/wk. Predicted effect is BELOW MDE: run level = screen (sign + placebo + second holdout), a PASS cannot be established by power alone",
  "object": "signal",
  "nearest_scored_cell": "dip-buy sleeves (RSI2 at the close) and TA_NQ_RSI2_t10_plain",
  "nearest_result": "DEAD as DS3 books, 0.4-0.9 trades/wk; here it is intraday and trend-conditioned"
 },
 {
  "cell": "PB_ST10_SWZ_T1",
  "family": "pb",
  "params": {
   "reg": "ST10",
   "pb": "SWZ",
   "trig": "T1",
   "W": 30,
   "second": 0,
   "fade": false
  },
  "flag": "NT8-bars",
  "mechanism": "When the 10-minute Supertrend (ATR10 x 3.0, TE6 definition) is up/down, a first return to the 38-62% retrace zone of the last 5-minute fractal swing within 30 min followed by the first 1-minute close back in the trend direction (bullish bar closing beyond the level) resumes the trend into the 60-pt bracket at a better price than a trend-bar entry",
  "predicted_effect": "pullback entries trade a better price than the flip/trend-bar entry, but skip trends that never retrace: +0.0 to +0.5 pt/trade net vs the same-day flip entry; below the paired MDE (3.5-8 pt/trade)",
  "detectable_effect": "MDE at 80% power, 5% two-sided (2.8 x SE): standalone weekly mean ~$11-18k/wk on WF-PRE (75 wk, candidate weekly SD $30-56k at 10 lots), ~$8-13k/wk on WF (143 wk); standalone per-trade ~3 pts (n~2.5k trades); paired vs ST/HM per overlapping trade ~8-14 pts (only ~15-30% of candidate trades overlap an ST/HM trade); paired weekly diff MDE ~$20k/wk. Predicted effect is BELOW MDE: run level = screen (sign + placebo + second holdout), a PASS cannot be established by power alone",
  "object": "signal",
  "nearest_scored_cell": "PULLBACK study 2026-10-16 (autopilot/REPORT_PULLBACK.md; 4,775 cells) and T-ENTRY TE6_st10m (flip entry PASS)",
  "nearest_result": "pullback study: 0 of 41 levels respected, finalists decayed; TE6 Supertrend flip entry (no pullback) PASS WF $8.7k/wk"
 },
 {
  "cell": "PB_ST10_SWZ_T2",
  "family": "pb",
  "params": {
   "reg": "ST10",
   "pb": "SWZ",
   "trig": "T2",
   "W": 30,
   "second": 0,
   "fade": false
  },
  "flag": "NT8-bars",
  "mechanism": "When the 10-minute Supertrend (ATR10 x 3.0, TE6 definition) is up/down, a first return to the 38-62% retrace zone of the last 5-minute fractal swing within 30 min followed by a close beyond the pullback bar's extreme resumes the trend into the 60-pt bracket at a better price than a trend-bar entry",
  "predicted_effect": "pullback entries trade a better price than the flip/trend-bar entry, but skip trends that never retrace: +0.0 to +0.5 pt/trade net vs the same-day flip entry; below the paired MDE (3.5-8 pt/trade)",
  "detectable_effect": "MDE at 80% power, 5% two-sided (2.8 x SE): standalone weekly mean ~$11-18k/wk on WF-PRE (75 wk, candidate weekly SD $30-56k at 10 lots), ~$8-13k/wk on WF (143 wk); standalone per-trade ~3 pts (n~2.5k trades); paired vs ST/HM per overlapping trade ~8-14 pts (only ~15-30% of candidate trades overlap an ST/HM trade); paired weekly diff MDE ~$20k/wk. Predicted effect is BELOW MDE: run level = screen (sign + placebo + second holdout), a PASS cannot be established by power alone",
  "object": "signal",
  "nearest_scored_cell": "PULLBACK study 2026-10-16 (autopilot/REPORT_PULLBACK.md; 4,775 cells) and T-ENTRY TE6_st10m (flip entry PASS)",
  "nearest_result": "pullback study: 0 of 41 levels respected, finalists decayed; TE6 Supertrend flip entry (no pullback) PASS WF $8.7k/wk"
 },
 {
  "cell": "PB_ST10_SWZ_T3",
  "family": "pb",
  "params": {
   "reg": "ST10",
   "pb": "SWZ",
   "trig": "T3",
   "W": 30,
   "second": 0,
   "fade": false
  },
  "flag": "NT8-bars",
  "mechanism": "When the 10-minute Supertrend (ATR10 x 3.0, TE6 definition) is up/down, a first return to the 38-62% retrace zone of the last 5-minute fractal swing within 30 min followed by 1-minute RSI(2) < 10 (> 90 for shorts) inside the trend resumes the trend into the 60-pt bracket at a better price than a trend-bar entry",
  "predicted_effect": "pullback entries trade a better price than the flip/trend-bar entry, but skip trends that never retrace: +0.0 to +0.5 pt/trade net vs the same-day flip entry; below the paired MDE (3.5-8 pt/trade)",
  "detectable_effect": "MDE at 80% power, 5% two-sided (2.8 x SE): standalone weekly mean ~$11-18k/wk on WF-PRE (75 wk, candidate weekly SD $30-56k at 10 lots), ~$8-13k/wk on WF (143 wk); standalone per-trade ~3 pts (n~2.5k trades); paired vs ST/HM per overlapping trade ~8-14 pts (only ~15-30% of candidate trades overlap an ST/HM trade); paired weekly diff MDE ~$20k/wk. Predicted effect is BELOW MDE: run level = screen (sign + placebo + second holdout), a PASS cannot be established by power alone",
  "object": "signal",
  "nearest_scored_cell": "dip-buy sleeves (RSI2 at the close) and TA_NQ_RSI2_t10_plain",
  "nearest_result": "DEAD as DS3 books, 0.4-0.9 trades/wk; here it is intraday and trend-conditioned"
 }
]
```
