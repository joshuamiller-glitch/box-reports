# PREREG_REGIME - the 'intraday extension-fade' factor and its structural break (registered 2026-10-18 before any factor was computed)

Question: the index-futures fades found in batches S, BI, BJ, BM, Q (SW4, SW20, Q12, Q20, Q34, BM1, BJ2, BI8) are positive from about 2023 and ~0 or negative before. Is that ONE regime (a common structural break in a fixed-rule factor), when did it start, and what (on-disk data only) drives it?

## 1. The factor (frozen before looking at any component's history)
Per index I in {ES, NQ, RTY, YM}: F_I(day) = equal-weight average of 20 components, each component = the daily after-cost P&L (1 contract, 1 tick/side + $4.36, from the existing runs `outputs/autopilot/b/<fam>_co/real_<I>.pkl`; RTY from 2017-07) of ONE frozen rule cell applied to index I, divided by that component's own full-sample daily standard deviation on I. ALL(day) = mean of the four F_I available that day.
Frozen set (8, cells at their reported selected parameters, applied unchanged to all four indices; the reported selection instrument is in brackets):
 1. SW4 cell 39: RTH open+15m, fade the first-15-minute move when the overnight-range percentile >= 0.67, hold 120 min [RTY]
 2. SW20 cell 17: prior-3-day RTH flow-proxy imbalance |m|>=0.02, fade at the RTH open, flat exit [RTY]
 3. Q12 cell 75: 15-min Bollinger(20,2.5) cross-out, fade, hold 120 min, day [NQ]
 4. Q20 cell 79: 15-min prior-close distance >= 0.75 ADR20, fade, hold 240 min, day [RTY]
 5. Q34 cell 1: Globex return faded from the 09:30 open, hold 180 min [ES]
 6. BM1 cell 1: 15:20 ET fade of a >= 0.4 ADR20 move from the prior RTH close, exit 15:55 [NQ]
 7. BJ2 cell 3: 15:00 ET fade of the prior 60-minute return, exit 15:55 [NQ]
 8. BI8 cell 0: after a prior-day range >= 1.5 x ATR20, LONG, hold 1 day [ES] - NOT a fade (REPORT_BI8B withdrew it as long beta); included because it was named, with the 7-rule sensitivity reported.
Neutral variants (12), drawn by `ap_regime_draw.py` with numpy default_rng(20261018) from the 'against' (fade) cells of each family's grid, one per family, using only grid definitions (no P&L read):
 Q11 cell 73 (15m burst(10,3.0) against, 60m, day); Q12 cell 89 (15m boll(40,2.5) against 60m day); Q13 cell 88 (15m run(5) against 60m all); Q18 cell 42 (5m openDist(1.0) against 120m all); Q19 cell 59 (15m emaz(50,2.0) against 120m day); Q20 cell 9 (5m priorclose(0.5) against 60m day); Q23 cell 17 (settlement drift (15,0.25,0,-1)); Q34 cell 17 (onr (30,0.2,180,-1)); SW4 cell 3 (RTH open+0m ref=on, hi0.67 against 120m); SW20 cell 41 (clv prior3d |m|>=0.02 against flat); BM1 cell 9 (15:30 |px-prior close|>=0.7 ADR against, exit 15:55); BJ2 cell 9 (15:30 prior 60m ret against, exit 15:55).
Where a family has no run on YM, its `real` stage is run on YM (cells unchanged; no re-selection). Sensitivities: frozen-8 only, neutral-12 only, 7 rules without BI8, leave-one-out.

## 2. Descriptive series
Daily factor, monthly factor sum and monthly Sharpe (daily mean/SD within the month x sqrt(252)), rolling 63-day Sharpe, calendar-year Sharpe table 2013-2026-10, cumulative standardised P&L; per index and ALL.

## 3. Structural-break tests (weekly factor sums, ISO weeks)
(a) Mean-shift (Chow-type) Welch t between the weeks before and after each candidate date 2020-03-01, 2022-01-01, 2022-10-01, 2023-01-01; (b) single-break supF scan with 15% trimming (Bai-Perron single-break statistic: maximum over dates of the F for a mean shift) and the maximising date; (c) CUSUM: max |cumulative sum of (x - mean)| / (sd sqrt(n)); (d) the same on the 7-rule and leave-one-out factors.
Null: SIGN-RANDOMISED CONSTRUCTION - 5,000 draws; each draw multiplies each of the 20 components by an independent random sign and recomputes F_I and ALL; p-value = share of draws with |t| (or supF, CUSUM) >= the real value. Interpretation: a small p means the break is common across rules in the SAME direction (aligned), not the arithmetic of 20 noisy series. Second reference null (drift-neutral): 2,000 circular time-shifts of the real demeaned factor (preserves autocorrelation, destroys the break location), compared on supF only.

## 4. Candidate drivers (on-disk data only; coverage stated)
Monthly series: (D1) 0DTE share of NDX option volume (`outputs/autopilot/opt/ndx_vol_daily.parquet` share0; coverage 2019-01..2026-10 only); (D2) VIX level (data/gap/vix/VIX.csv); (D3) vol-of-vol: VVIX level and the monthly SD of daily VIX changes; (D4) ES realised volatility (21-day, annualised, from the 1-minute series); (D5) volume growth: ES front-month volume, 12-month change of the monthly total; (D6) first-hour range fraction: ES RTH range of 09:30-10:30 over the full-session range, monthly mean. Tests: (i) driver break at the same candidate dates (Welch t pre/post); (ii) DRIFT-NEUTRAL association: linearly detrend both the driver and the monthly ALL factor over the common window and take the Pearson correlation; null = 5,000 circular shifts of the driver; Bonferroni threshold 0.05/6 across drivers; also the same on first differences; (iii) within-regime (2023-01..2026-10 only) correlation with the same null; (iv) tercile split of driver months: mean factor in top vs bottom tercile. A driver 'survives' if (ii) p < 0.0083 on both detrended levels and first differences and (iii) p < 0.05 in the same sign.

## 5. Forward implication
If a break date is identified (p < 0.05 against the sign-randomised null at a candidate date or the supF date) and a driver survives, the regime-end observable is stated as: rolling-63-day ALL-factor Sharpe falling below the 5th percentile of its post-break distribution for two consecutive weeks, or the driver crossing back to its pre-break tercile; a tracked daily series `forward/series/REGIME_live.csv` (+ meta) and a refresh script are provided for the extension worker's registry (a tracked rolling factor, not a trade). The existing registry files (ap_forward_score.py, PRED*.json) are not edited by this worker.

## 6. Insurance view (2023-26 only; 2013-22 reported alongside)
The ALL factor (and each F_I) as a sleeve: scaled so its clean weekly SD = share x the pair's clean weekly SD (additive at 10/20/30/50%) and the constant-risk framing (30%); metrics via t3_score.score_one on the pair B.Cfg(wk_floor=8, wk_loss_pb=None) (clean/H1/H2/all-in: weekly Sharpe uplift, worst week, CVaR5, max DD, Sortino, MAR, % negative weeks); 2013-22 flat period: factor standalone weekly Sharpe by year and cumulative $ at the same scale. Sized dollars at 20% share: contracts per component slot per index, worst day, worst week, worst single-component trade. Gates are NOT applied (the factor is a diagnostic of a regime, not a candidate book) but the numbers are stated next to the pair's.

## 7. Reporting
REPORT_REGIME.md with: the factor series tables, break tests with nulls, drivers with coverage and survival, the forward observable, the insurance view, and the list of what is NOT identified. Look-ahead rules: components are the already-run causal cells; drivers are lagged by one month for the association tests (driver month m vs factor month m+0 and m+1 both reported); the factor scaling uses full-sample SD (a research factor, not a trading signal).
