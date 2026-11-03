# DISCOVER_REGIME (CAL, 2026-11-04; no new books except the causal switch; ledger DISC_R 12 cells)
Data: 1-min RTH (09:30-16:00 ET) bars NQ (out/def), ES, RTY, YM (tc/cache), 2023-04..2026-10-16, 60-64 days per quarter. Daily rows `l2vast/ds3/out/regime_daily_<inst>.parquet`, quarterly `regime_quarterly.csv`, pre/post `regime_prepost.csv`. Code `l2vast/ds3/code/discover/{regime_diag,regime_prepost,regime_causal,regime_gate}.py`. Change date used: 2025-10-23 = the peak of the cumulative P&L of the 30-min RTH breakout book (the fade book's trough); breakout quarterly P&L was positive through 2025Q2, about flat in Q3-Q4, large negative from 2026Q1.

## 1. What changed in the market (NQ quarterly; ES/RTY/YM in `regime_quarterly.csv`)
ER_1h = efficiency ratio of 09:30-10:30; ac5/ac30 = lag-1 autocorrelation of 5-/30-min log returns inside RTH; VR6 = variance ratio 30-min vs 6 x 5-min; orb_cont_rate = share of 30-min-range first-break days where the price 60 min later is beyond the break close; orb_win25 = hit +0.25% before -0.25% from the break close.
        days  ER_1h  ac5_rth  ac30_rth    VR6  orb_cont_rate  orb_win25  rv_pct  range_atr  open_hr_share  abs_gap_bps
q                                                                                                                     
2023Q1    23  0.133    0.028     0.036  0.950          0.522      0.478   1.118      0.808          0.530       43.393
2023Q2    62  0.145    0.031     0.012  1.048          0.583      0.541   0.801      1.010          0.588       44.847
2023Q3    62  0.124    0.006    -0.024  1.073          0.433      0.459   0.827      1.017          0.623       48.383
2023Q4    62  0.126   -0.013     0.033  0.940          0.484      0.567   0.784      0.965          0.578       39.517
2024Q1    61  0.140   -0.019     0.041  0.955          0.492      0.533   0.696      1.031          0.609       48.663
2024Q2    63  0.137   -0.010     0.080  1.013          0.565      0.567   0.707      1.052          0.562       44.008
2024Q3    63  0.133   -0.042    -0.026  0.965          0.540      0.571   1.009      1.039          0.564       64.897
2024Q4    62  0.166   -0.028     0.055  1.018          0.468      0.492   0.751      1.075          0.666       46.021
2025Q1    60  0.163   -0.044    -0.004  0.969          0.533      0.583   1.045      1.036          0.630       65.190
2025Q2    62  0.134    0.034     0.001  0.969          0.525      0.492   1.235      1.006          0.579       97.011
2025Q3    63  0.145    0.010    -0.070  1.114          0.468      0.458   0.617      1.005          0.658       32.002
2025Q4    62  0.140    0.034     0.013  1.117          0.532      0.424   0.836      1.050          0.612       55.970
2026Q1    61  0.162    0.018     0.005  1.046          0.590      0.407   0.974      1.085          0.678       60.158
2026Q2    62  0.127   -0.008    -0.017  0.932          0.517      0.533   0.959      1.072          0.612       71.318
2026Q3    64  0.142   -0.034     0.011  1.092          0.413      0.371   0.809      0.945          0.713       69.246
2026Q4    12  0.144   -0.028     0.013  0.983          0.727      0.455   0.731      1.194          0.664       64.979

Pre (2023-04..2025-10-23) vs post (2025-10-24..2026-10-16), day-level permutation p (2,000 shuffles):
| metric | NQ pre->post diff (p) | ES | RTY | YM |
|---|---|---|---|---|
| ER_1h | +0.001 (0.915) | +0.001 (0.903) | +0.002 (0.740) | -0.002 (0.783) |
| ER_open2h | -0.001 (0.861) | +0.003 (0.564) | -0.002 (0.699) | -0.006 (0.289) |
| ER_rth | -0.000 (0.983) | -0.001 (0.681) | -0.002 (0.494) | -0.003 (0.413) |
| absgap | +12.663 (0.005) | +1.580 (0.637) | -3.744 (0.407) | +9.242 (0.002) |
| absret | +0.004 (0.942) | -0.054 (0.215) | -0.066 (0.232) | -0.029 (0.477) |
| close_loc | -0.022 (0.335) | -0.036 (0.096) | -0.020 (0.366) | -0.045 (0.036) |
| open_hour_range_share | +0.059 (0.001) | +0.055 (0.001) | -0.004 (0.816) | +0.073 (0.000) |
| orb_cont60 | +0.006 (0.934) | -0.006 (0.884) | +0.011 (0.819) | -0.019 (0.638) |
| orb_ft60 | -3.641 (0.233) | -1.203 (0.576) | +0.438 (0.893) | -0.568 (0.789) |
| orb_win | -0.107 (0.009) | -0.009 (0.880) | -0.013 (0.755) | -0.005 (0.924) |
| range_over_atr14 | -0.004 (0.913) | -0.016 (0.713) | -0.019 (0.569) | -0.014 (0.708) |
| rv_pct | +0.048 (0.109) | -0.020 (0.489) | -0.049 (0.129) | +0.032 (0.149) |

Reading: the classical statistics did not move. Efficiency ratio (opening hour, 2 h, RTH), 5-/30-min autocorrelation, variance ratio, realized vol, range/ATR and the 60-minute ORB continuation rate show no pre/post difference in any of the four contracts (all p >= 0.1). Two things did move: (a) the share of the day's range printed in the first hour rose by 5.5 pts on NQ, 5.5 on ES and 7.3 on YM (p <= 0.001; RTY flat); the rest of the session carries less of the day (consistent with a range-bound NY-AM after the open); (b) NQ-only: the ORB hit rate for a 0.25% move from the break fell 0.107 (p 0.009; 0.55 -> 0.44) and opening gaps are larger (+12.7 bps NQ, +9.2 YM, p <= 0.005; not ES/RTY). The breakout failure is NQ-specific in the P&L-relevant statistic; the larger opening-hour share is market-wide among the large-cap indexes. The regime is real in the P&L but weak in the descriptive statistics: no autocorrelation or efficiency measure would have shown it.

## 2. Causal detection and what the live NY-AM sleeve correlates with
- Detection lag (trading days after the 2025-10-23 peak until the indicator is on for >= 10 of the next 15 days; indicators use strictly prior days): trailing-10 fade P&L > 0: 5 days (but on 45% of pre-change days: it flickers); trailing-20: 10 days (41% pre, 70% post); trailing-40: 29 days (28% pre, 70% post); trailing-10/20/40 ORB hit rate < 0.45: 10 / 14 / 19 days (35% / 22% / 9% on pre-change days, 51% / 46% / 49% after); opening-hour range share above its trailing-250 median: 31-39 days (39-45% pre, 56-63% post); opening-hour ER below its trailing-250 median: 47 / 111 / 157 days (rarely on). The efficiency ratio is too slow and carries no signal; the fast and discriminating indicators are the strategy's own recent P&L and the ORB hit rate.
- Live NY-AM sleeve daily $ (six books, cube session nyam): same-day opening-hour ER +0.26, ORB hit +0.29, open-hour share -0.21 (contemporaneous, not usable); prior-day values have |r| <= 0.06 for ER, close location, gap, realized vol. At the 60-day level the sleeve correlates +0.43 with trailing realized vol (the VIX proxy) and -0.39 with the open-hour share; the bundle's 60-day level correlates -0.65 with the ORB hit rate and +0.41 with the open-hour share. So the sleeve earns when the realized vol is high and the first hour is not dominating the day, which is where the fades lose.

## 3. Causal regime switch on the bundle
Books (2 lots each): overnight-extreme fade at the open (ON_RTH), NY-AM VWAP fade (d10, T120), RTH 09:30 30-min ORB fade (60/60 T240). Switch: trade day t only if the trailing-N-day P&L of the bundle (days < t) > 0 [and optionally trailing-N mean opening-hour ER < trailing-250-day median]; N 10/20/40; bundle-level or per-book switch = 12 configurations. S = mean of the weekly means over L6M, HOLD, MID, PRE, X'.
Plain bundle: L6M +4,540, HOLD +5,065, MID +11,284, PRE -2,422, X' -588 (S 3,576, maxDD L6M 9.9k). Switched (L6M / HOLD / MID / PRE / X'; S): N40 bundle-level no ER: 4,540 / 4,758 / 10,298 / -986 / +354 (S 3,793); N20 bundle: 3,946 / 4,099 / 8,115 / -565 / +430 (S 3,205); N10 bundle: 2,073 / 3,854 / 9,839 / -364 / -898; the per-book switches 2,253..3,710 L6M; every configuration with the ER condition (N10/20/40) is worse (S 660-1,181): the opening-hour efficiency condition removes the gains. Best-of-12 null (200 worlds, circular shift of the regime-on vector): real best S 3,793 vs null median 2,435, p95 3,652, p = 0.005; but the switched bundle's S is only 6% above the plain bundle's 3,576: what the switch does is to cut the 2023-25 losses (PRE -2,422 -> -986, X' -588 -> +354) because the trailing-40 P&L is mostly negative in the old regime, and to stay on in 2026 (L6M unchanged). It costs MID (11,284 -> 10,298).
Gate v2 (ZL-2, placebos 100, n_tested 1,458 = 636 DISC_B/C census + 464 DISC_C + 346 DISC_D + 12 here) on the three switched components (N40): ON_RTH p_book 0.119 (HOLD placebo p 0.01-0.02, PRE p 0.39-0.83), VWAP p_book 0.030 (HOLD p 0.01, stack gain p 0.01-0.03 but L6M stack gain p 0.30-0.48), ORBF p_book 0.861; gate_v1 TOLERANT false for all three, gate_v2a false, gate_v2 false, Bonferroni p = 1.0, addition false. Nothing clears.

## 4. Stack effect of the bundle (Q1-A ts2; harness stack L6M Calmar 0.258, carrying week dropped 0.695, HOLD 0.185 / 0.228, MID 0.282, PRE 0.150)
| bundle scale | L6M Calmar (dropcar) | L6M maxDD | HOLD Calmar (dropcar) | MID | PRE | mean gain L6M / HOLD $/wk |
|---|---|---|---|---|---|---|
| plain 0.25x | 0.305 (0.724) | 92.3k | 0.203 (0.247) | 0.392 | 0.138 | +1,135 / +1,266 |
| plain 0.5x | 0.355 (0.755) | 82.4k | 0.222 (0.268) | 0.552 | 0.128 | +2,270 / +2,533 |
| plain 1.0x | 0.503 (0.818) | 62.7k | 0.239 (0.284) | 1.291 | 0.108 | +4,540 / +5,065 |
| switched N40 0.25x | 0.305 (0.724) | 92.3k | 0.202 (0.247) | 0.387 | 0.147 | +1,135 / +1,190 |
| switched N40 0.5x | 0.355 (0.755) | 82.4k | 0.220 (0.266) | 0.540 | 0.144 | +2,270 / +2,379 |
| switched N40 1.0x | 0.503 (0.818) | 62.7k | 0.237 (0.281) | 1.246 | 0.133 | +4,540 / +4,758 |
Equal risk (largest k with the stack maxDD, HOLD with the carrying weeks dropped, not above the stack's own): plain k = 1.56 -> HOLD stack Calmar 0.228 -> 0.293, mean gain +$7.8k/wk; switched k = 1.56 -> 0.288, +$7.2k/wk. The L6M equal-risk search hits the k = 5 cap (the stack L6M maxDD never exceeds its own up to 5x, mean gain +$20.3k/wk, Calmar 1.58): not a usable lot size (5 x 2 lots per book). PRE: the plain bundle worsens PRE Calmar 0.150 -> 0.108 at 1x; the switched bundle 0.133. The switch's value is the PRE cost, not the 2026 gain.

## Verdict
The regime is a fact in the P&L (the NQ opening-range breakout stopped working in Oct-2025 and the NY-AM fades earn since), not in the standard efficiency/autocorrelation statistics. A causal rule detects it in 5-30 trading days using the books' own trailing P&L (N10-40) or the ORB hit rate, but those same rules are on 28-45% of the days before the change, so the switch is a lag, not a predictor. The switched bundle improves PRE/X' by turning itself off in the old regime, improves nothing in L6M, passes no gate (v1 TOLERANT false, v2 false, Bonferroni 1.0). Label: LEAD-regime bundle (hedge of the stack's NY-AM sleeve, which stalled with the same regime), not cleared.
