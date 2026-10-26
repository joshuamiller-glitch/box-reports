# REPORT SD (pre-registered block 'SD' in PREREG_AUTOPILOT.md; no new selection; FOUND 0)

Files: sd/ (dip.log, dip_*.csv, q34_main.log, bm1_main.log, *_surface.csv, *_decomp.csv, x_all.csv, sd3_insurance.csv, sd3_sizing.csv). Code: code/census/night_ins/ap_sd_*.py.
Look-ahead checks: signals at bar close, entry next open (1-min) or next-day (daily dip); VIX terciles use prior-day VIX and cutoffs from pre-2023 data; random-date null uses days with close>SMA200 (same filter) and identical exits; no parameter re-selection anywhere.

## SD-1 ES dip-buy (C11-DIP rsi5/5d/3ATR), identical parameters everywhere
- ES: 2023-26 n=25, win 84%, mean +$4,251/trade (t 4.8); 2013-22 n=40, win 60%, mean +$155 (t 0.19, null-indistinguishable). All 65: win 69%, +$1,730.
- Pair window (23 trades): +$4,603/trade, win 87%. 5,000 drift-matched random-date worlds: null mean win 58%, null mean +$543; p(total)=0, p(mean)=0, p(win)=0.001, p(weekly Sharpe)=0. 2013-26 all: p(mean)=0, p(win)=0.039. 2013-22: p=0.38 (nothing).
- Universe (same rule, daily 16:00 bars): NQ n=71 win 73% +$1,958; RTY n=36 69% +$1,252; YM n=69 62% +$454; positives also SI, HG, NG, CL (small, t<1.2). 23 markets, 8 negative. Equity indices are the only consistently positive group; effect is modern-era (2023-26) in ES.
- Win-rate Beta posterior (prior from universe, 3 prior strengths): 2023-26 mean 0.66-0.76, P(>0.5)=0.995-0.999, 90% CI ~0.56-0.87; all-years 0.64-0.67 (P>0.5 0.998); 2013-22 0.57-0.59 (P>0.5 ~0.90).
- Expectancy posterior (normal-normal, tau grid 0.1/0.3/0.6, ATR units): all-years shrinks from 0.54 to 0.12-0.48 (non-ES prior) or 0.39-0.51 (index-peer prior), P(>0) 0.91-1.0. 2013-22: ~0 (P>0 0.4-0.56 with non-ES prior).
- Minimum extra trades: for "win rate >0.5" verdict, 0 (already P=0.999). For an expectancy verdict at t=2 on the all-years figure: n~46 total, i.e. ~0 more at modern frequency; the open question is era persistence, not sample size: ~6.6 trades/yr, so ~2 more years (13 trades) to confirm modern-era win rate stays >0.6 at P>0.95.
- Verdict: the evidence is stronger than "23 trades" implied for the modern era (beats drift-matched dates, replicates NQ/RTY, directionally YM), but it is a 2023+ regime effect; 2013-22 shows none. Sizing: treat as an insurance/overlay candidate, not FOUND.

## SD-2 Q34 ES1 and BM1 (1 contract; scale = contracts for pair-vol match)
2,000-world side-permutation nulls (long/short counts, clock preserved):
- Q34 ES1: Sharpe clean 1.48 p=0.003; H1 1.57 p=0.074; H2 0.39 p=0.267; all 1.17 p=0.002. Pre-2023 mean -$38/trade (fails the era, ERA flag stays).
- BM1 NQ: clean 1.33 p=0.026; H1 0.78 p=0.321; H2 2.31 p=0.018; all 1.47 p=0.003. Pre-2023 -$83/trade.
Shifted-clock surfaces (+-60 min, hold 60-300 min for Q34; entry 860-980 for BM1): both are ridges, not plateaus. Q34 positive uplift for offsets -45..-30 with holds 180-300 (clean +1.2..1.75) and +60 with hold 120; off -60 and holds 60 or 240+ at some offsets negative. BM1 positive only at the registered entry 920 (clean 1.33) and its neighbours 935/950 are weaker (0.8/0.5, H1/H2 flip); entries <=905 negative. Verdict: BM1 surface is sharp (fails plateau honesty); Q34 is moderately broad on the early side only.
Decompositions (2023-26 mean/trade): Q34 positive Mon +$215 (t2.1), Tue +$139, Thu +$127, Wed -$19, Fri ~0; VIX terciles low +$112 (t2.0), mid +$32, high +$184 -> not regime-dependent, but day-of-week heterogeneity is noise-level. BM1: Mon +$229 (t2.5), Tue +$201, Wed +$140, Thu -$46, Fri +$46; VIX mid +$154 (t2.6), low +$103, high +$18. Pre-2023 both negative in every weekday/tercile (BM1 high VIX -$193, t-4).
Cross-section (identical parameters, no re-selection; x_all.csv): Q34 on 26 outrights/indices: positive uplift only ES (+0.30 clean), NQ (+0.34), RTY (+0.14), YM (+0.18), HO, RB; FX/rates/metals/ags negative (all-sample Sharpe negative for 6A,6B,6C,6E,6J,CL,GC,HE,HG,LE,NG,PL,SI,ZB..ZW). BM1: only NQ is positive (clean 1.33, all 1.47); ES 0.17, RTY 0.36 (clean), YM -0.26, H1/H2 sign flips. Both are equity-index-specific; BM1 is NQ-specific. Daily-bar-compatible variants of these intraday rules are not defined (clock-based), so the cross-section used the 1-min series of each market.

## SD-3 Sizing and insurance (pair vol-matched, clean weekly sigma)
Contracts at 100% pair-vol: Q34 ES 22.1, BM1 NQ 45.0; at 20%: 4.4 ES / 9.0 NQ; equal-risk combo at 20%: 3.0 ES + 6.2 NQ. Weekly corr Q34 vs BM1 = +0.02; worst-decile corr with pair -0.09 / -0.20 / -0.26 (combo).
Additive uplift in weekly Sharpe (clean/H1/H2):
| sleeve | 10% | 20% | 30% | 50% |
| Q34 ES1 | +.16/+.19/+.15 | +.30/+.33/+.26 | +.42/+.42/+.30 | +.59/+.45/+.20 |
| BM1 NQ | +.13/+.22/+.25 | +.23/+.40/+.45 | +.32/+.52/+.61 | +.44/+.55/+.80 |
| Q34+BM1 equal risk | +.20/+.30/+.29 | +.38/+.57/+.53 | +.53/+.78/+.71 | +.77/+1.01/+.89 |
All-in with pair+20%: Sharpe 1.90 -> 2.19 (either), 2.32 (combo). Worst week (all-in): pair -$82.5k -> -$98.7k (Q34), -$94.8k (BM1), -$93.1k (combo); CVaR5 -$79.2k -> -$87.4k / -$85.2k / -$84.7k; max DD $280k -> $291k / $259k / $267k. Constant-risk 30%: net change Q34 -8.5%, BM1 -4.5%, combo +2.2%; worst-week improvement -4.3% / +7.7% / +8.7%; CVaR5 +12 / +15 / +18 (see sd3_insurance.csv for the exact definitions).
So: additive uplift passes +0.10 at 10-50% on clean/H1/H2 for all three, but the pair's absolute worst week gets worse in dollars (bigger book) rather than better; as constant-risk replacement only the combo is roughly neutral on net P&L with better tails. Sized dollars at 20%: Q34 worst day -$45.6k (4.4 ES), BM1 -$45.1k (9 NQ), combo worst day -$34.7k / worst week -$38.4k; worst single trade per 1 contract Q34 -$10.3k, BM1 -$5.8k (at 20% size -$45.6k / -$51.9k).
Gate status: not FOUND. Q34 and BM1 fail ERA (pre-2023 negative), BM1 fails plateau, H1/H2 null p not <0.05 for Q34 H2 and BM1 H1; they remain candidates for a small, live-forward-tested overlay (Q34 watcher stays).
