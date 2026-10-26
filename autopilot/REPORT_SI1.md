# REPORT SI1 - forward distributions for the stated objective (weekly Sharpe, smooth weekly income) on $700k, with shrinkage and margin views
**Verdict (conclusions at the end of the first table block): every sleeve book improves the pair's forward distribution at 100% of its backtest edge, and the improvement in the odds of a $200k drawdown over 52 weeks is large (pair 46% -> 1.7-22% for the sleeve books; pair 6/6 alone 19%); but the improvement is carried by the sleeves' in-sample means, and the break-even shrinkage shows how much of that edge must survive: for the constant-risk 80/20 books it is 0% (VC) and 0% (IMP3); for pair + 20% IMP3 40%; for pair + 20% VC 36%. Pre-registered in PREREG_AUTOPILOT.md ('SI1') before the bootstrap ran. The lead-only books (BM1, Q34 ES1) are sensitivity rows, flagged NOT counted.**

## 0. Set-up (what was and was not done)
- Data: label days 2023-08-01..2026-10-16 = 168 ISO weeks (168 joint weekly vectors); the pair's weekly Sharpe in this window is 1.90 and its best period ever (the bootstrap replays this window: it is not a claim about the pair's long-run distribution; the shrinkage rows are the sensitivity). Series: pair = ap_ict_core PAIR (live 8/8); IMP3 = incumbent tf3 m1.5 and VC = k1 m1.125 on FV18 basis B (+1 s latency, +1.4 ticks extra on every stop exit; conservative), tick-built; BM1 = NQ 15:20 fade; Q34 ES1 = ES overnight-return-sign fade, RTH open + 180 min (library Q34CO/ES_1 rule).
- Scaling conventions (as FV18): 'additive 20%' = pair + 0.2 x sleeve in its R-sized form; constant-risk (CR) a/b = a x pair + b x kappa x sleeve with kappa = clean weekly SD pair / sleeve = 0.81 for IMP3 and 0.50 for VC. NOTE: kappa 0.50 means the R-sized VC sleeve has TWICE the pair's weekly risk, so 'pair + 20% VC' is a ~40%-of-pair-risk addition (and pair + 20% IMP3 ~16%): the additive books are not risk-comparable with the CR books. BM1 and Q34 ES1 enter at 10% of pair risk (x kappa 45.0 and 22.1); VC in the pre-registered lead-only row at raw 10% (= 20% risk), with an equal-risk 10% row added for comparability.
- Bootstrap: moving blocks of 4 weeks with circular wrap, 20,000 draws, common random numbers across books (paired comparison), horizons 13/26/52. P(neg quarter) = share of non-overlapping 13-week segments with negative sum; drawdown = max peak-to-trough of the cumulative path from 0; $280k = 40% of $700k. Pair 6/6 = 0.75 x pair (contract rounding and the R-based locks ignored).

## 1. Forward distributions at 100% of the backtest edge
### 13 weeks
| book | P5 | median | P95 | P(neg quarter) | P(DD>$200k) | P(DD>$300k) | P(DD>$280k) | E[worst wk] | P(>=8/13 pos) |
|---|---|---|---|---|---|---|---|---|---|
| Pair 8/8 (live) | -101k | +204k | +547k | 0.141 | 0.104 | 0.011 | 0.019 | -72k | 0.500 |
| Pair 6/6 (0.75x) | -76k | +153k | +410k | 0.141 | 0.025 | 0.001 | 0.001 | -54k | 0.500 |
| Pair + 20% IMP3 | +5k | +354k | +730k | 0.047 | 0.042 | 0.001 | 0.002 | -72k | 0.711 |
| Pair + 20% VC | +245k | +591k | +1036k | 0.001 | 0.009 | 0.000 | 0.000 | -60k | 0.890 |
| CR 80/20 pair/IMP3 | +6k | +285k | +587k | 0.046 | 0.009 | 0.000 | 0.000 | -57k | 0.711 |
| CR 70/30 pair/IMP3 | +43k | +325k | +628k | 0.026 | 0.002 | 0.000 | 0.000 | -54k | 0.733 |
| CR 80/20 pair/VC | +97k | +357k | +674k | 0.009 | 0.002 | 0.000 | 0.000 | -51k | 0.824 |
| CR 70/30 pair/VC | +186k | +432k | +750k | 0.001 | 0.000 | 0.000 | 0.000 | -42k | 0.897 |
| Pair + 10% VC + 10% BM1 + 10% Q34 ES1 (lead-only) | +104k | +434k | +813k | 0.013 | 0.025 | 0.001 | 0.002 | -66k | 0.810 |
| Same, equal-risk 10% each (VC x kappa) (lead-only) | +19k | +337k | +694k | 0.042 | 0.050 | 0.003 | 0.005 | -69k | 0.723 |
### 26 weeks
| book | P5 | median | P95 | P(neg quarter) | P(DD>$200k) | P(DD>$300k) | P(DD>$280k) | E[worst wk] | P(>=8/13 pos) |
|---|---|---|---|---|---|---|---|---|---|
| Pair 8/8 (live) | -12k | +415k | +885k | 0.136 | 0.244 | 0.043 | 0.062 | -78k | 0.503 |
| Pair 6/6 (0.75x) | -9k | +311k | +664k | 0.136 | 0.079 | 0.006 | 0.010 | -59k | 0.503 |
| Pair + 20% IMP3 | +221k | +709k | +1231k | 0.044 | 0.103 | 0.007 | 0.011 | -82k | 0.712 |
| Pair + 20% VC | +694k | +1195k | +1800k | 0.002 | 0.023 | 0.000 | 0.001 | -72k | 0.893 |
| CR 80/20 pair/IMP3 | +180k | +571k | +990k | 0.044 | 0.028 | 0.001 | 0.002 | -66k | 0.712 |
| CR 70/30 pair/IMP3 | +253k | +650k | +1066k | 0.024 | 0.008 | 0.000 | 0.000 | -63k | 0.731 |
| CR 80/20 pair/VC | +352k | +722k | +1152k | 0.009 | 0.007 | 0.000 | 0.000 | -59k | 0.827 |
| CR 70/30 pair/VC | +518k | +874k | +1306k | 0.001 | 0.001 | 0.000 | 0.000 | -51k | 0.900 |
| Pair + 10% VC + 10% BM1 + 10% Q34 ES1 (lead-only) | +411k | +876k | +1397k | 0.012 | 0.056 | 0.003 | 0.006 | -76k | 0.816 |
| Same, equal-risk 10% each (VC x kappa) (lead-only) | +236k | +679k | +1167k | 0.037 | 0.111 | 0.009 | 0.015 | -78k | 0.726 |
### 52 weeks
| book | P5 | median | P95 | P(neg quarter) | P(DD>$200k) | P(DD>$300k) | P(DD>$280k) | E[worst wk] | P(>=8/13 pos) |
|---|---|---|---|---|---|---|---|---|---|
| Pair 8/8 (live) | +222k | +844k | +1497k | 0.138 | 0.462 | 0.115 | 0.156 | -80k | 0.505 |
| Pair 6/6 (0.75x) | +166k | +633k | +1123k | 0.138 | 0.190 | 0.024 | 0.036 | -60k | 0.505 |
| Pair + 20% IMP3 | +726k | +1425k | +2157k | 0.047 | 0.217 | 0.021 | 0.033 | -89k | 0.711 |
| Pair + 20% VC | +1673k | +2415k | +3246k | 0.001 | 0.049 | 0.000 | 0.002 | -81k | 0.892 |
| CR 80/20 pair/IMP3 | +588k | +1149k | +1737k | 0.046 | 0.068 | 0.003 | 0.006 | -71k | 0.711 |
| CR 70/30 pair/IMP3 | +735k | +1301k | +1893k | 0.027 | 0.021 | 0.001 | 0.001 | -70k | 0.730 |
| CR 80/20 pair/VC | +914k | +1459k | +2055k | 0.010 | 0.017 | 0.000 | 0.001 | -64k | 0.823 |
| CR 70/30 pair/VC | +1236k | +1766k | +2360k | 0.001 | 0.001 | 0.000 | 0.000 | -57k | 0.900 |
| Pair + 10% VC + 10% BM1 + 10% Q34 ES1 (lead-only) | +1087k | +1762k | +2493k | 0.013 | 0.126 | 0.006 | 0.016 | -81k | 0.814 |
| Same, equal-risk 10% each (VC x kappa) (lead-only) | +724k | +1370k | +2051k | 0.040 | 0.234 | 0.025 | 0.041 | -82k | 0.725 |

## 2. Income smoothness (in-sample weekly P&L of each book, the quantity the bootstrap resamples)
| book | in-sample weekly mean | weekly SD | share of weeks < -$25k | worst week | weekly Sharpe |
|---|---|---|---|---|---|
| Pair 8/8 (live) | +16.3k | 62.1k | 25.6% | -83k | 1.90 |
| Pair 6/6 (0.75x) | +12.2k | 46.5k | 22.0% | -62k | 1.90 |
| Pair + 20% IMP3 | +27.5k | 67.6k | 25.0% | -101k | 2.93 |
| Pair + 20% VC | +46.7k | 72.6k | 17.9% | -95k | 4.64 |
| CR 80/20 pair/IMP3 | +22.2k | 54.2k | 22.6% | -81k | 2.95 |
| CR 70/30 pair/IMP3 | +25.1k | 52.6k | 19.6% | -83k | 3.44 |
| CR 80/20 pair/VC | +28.2k | 54.0k | 19.0% | -71k | 3.77 |
| CR 70/30 pair/VC | +34.2k | 51.5k | 14.9% | -68k | 4.78 |
| Pair + 10% VC + 10% BM1 + 10% Q34 ES1 (lead-only) | +34.1k | 65.8k | 19.6% | -90k | 3.73 |
| Same, equal-risk 10% each (VC x kappa) (lead-only) | +26.5k | 63.3k | 21.4% | -90k | 3.01 |

## 3. Shrinkage sensitivity (sleeve edge = lambda x backtest mean; the pair is untouched in the lambda rows)
| book (52 weeks) | edge 100%: median / P(DD>200k) / P(neg q) | 50% | 25% | break-even lambda (26w / 52w) |
|---|---|---|---|---|
| Pair 8/8 (live) | +844k / 0.462 / 0.138 | (pair unshrunk) | | |
| Pair 6/6 (0.75x) | +633k / 0.190 / 0.138 | +633k / 0.190 / 0.138 | +633k / 0.190 / 0.138 | 0% / 0% |
| Pair + 20% IMP3 | +1425k / 0.217 / 0.047 | +1134k / 0.416 / 0.095 | +989k / 0.534 / 0.130 | 41% / 40% |
| Pair + 20% VC | +2415k / 0.049 / 0.001 | +1624k / 0.279 / 0.030 | +1229k / 0.540 / 0.087 | 36% / 36% |
| CR 80/20 pair/IMP3 | +1149k / 0.068 / 0.046 | +912k / 0.197 / 0.095 | +793k / 0.289 / 0.130 | 0% / 0% |
| CR 70/30 pair/IMP3 | +1301k / 0.021 / 0.027 | +946k / 0.153 / 0.088 | +768k / 0.291 / 0.140 | 0% / 0% |
| CR 80/20 pair/VC | +1459k / 0.017 / 0.010 | +1064k / 0.118 / 0.052 | +867k / 0.216 / 0.097 | 0% / 0% |
| CR 70/30 pair/VC | +1766k / 0.001 / 0.001 | +1175k / 0.043 / 0.028 | +879k / 0.157 / 0.086 | 0% / 0% |
| Pair + 10% VC + 10% BM1 + 10% Q34 ES1 (lead-only) | +1762k / 0.126 / 0.013 | +1301k / 0.388 / 0.057 | +1070k / 0.495 / 0.100 | 33% / 33% |
| Same, equal-risk 10% each (VC x kappa) (lead-only) | +1370k / 0.234 / 0.040 | +1106k / 0.377 / 0.082 | +975k / 0.495 / 0.112 | 37% / 37% |

Joint shrink (pair and sleeves both at 50%), 52 weeks:

| book | median | P(DD>200k) | P(neg quarter) | E[worst wk] |
|---|---|---|---|---|
| Pair 8/8 (live) | +420k | 0.783 | 0.303 | -89k |
| Pair 6/6 (0.75x) | +315k | 0.506 | 0.303 | -66k |
| Pair + 20% IMP3 | +709k | 0.739 | 0.215 | -103k |
| Pair + 20% VC | +1200k | 0.553 | 0.092 | -104k |
| CR 80/20 pair/IMP3 | +572k | 0.502 | 0.214 | -82k |
| CR 70/30 pair/IMP3 | +649k | 0.404 | 0.184 | -83k |
| CR 80/20 pair/VC | +725k | 0.330 | 0.144 | -78k |
| CR 70/30 pair/VC | +877k | 0.158 | 0.086 | -74k |
| Pair + 10% VC + 10% BM1 + 10% Q34 ES1 (lead-only) | +876k | 0.606 | 0.150 | -98k |
| Same, equal-risk 10% each (VC x kappa) (lead-only) | +682k | 0.681 | 0.200 | -96k |
- Break-even lambda = the sleeve-edge fraction at which the book's P(DD > $200k) equals the live pair's unshrunk value (0.244 at 26 weeks, 0.462 at 52 weeks; interpolated on a 5% grid). 'never' = the book never reaches the pair's probability even at 100%; 0% = it already beats the pair with a zero-mean sleeve (a pure diversification/volatility effect, since the CR books hold less pair risk).
- Reading: constant-risk 70/30 and 80/20 books reduce the pair's own risk (0.7-0.8 x pair) so they keep a lower drawdown probability than the pair even with zero sleeve edge; the additive books (pair + 20% X) add risk, so they need a positive edge to improve the odds: break-evens in the table.

## 4. Margin and capital view (UNVERIFIED assumptions; day session = 09:30-16:00 ET; peaks from the actual trade intervals)
| book | peak NQ contracts (day / outside 09:30-16:00) | peak ES | margin A (intraday $1.5k NQ, $1.2k ES) peak $ / % of $700k | margin B (exchange-style $20k NQ, $14k ES) peak $ / % of $700k |
|---|---|---|---|---|
| Pair 8/8 (live) | 16.0 / 16.0 (p99 in-market 16.0) | 0.0 | 24k / 3.4% | 320k / 46% |
| Pair 6/6 | 12.0 / 12.0 (p99 in-market 12.0) | 0.0 | 18k / 2.6% | 240k / 34% |
| Pair + 20% IMP3 | 20.8 / 20.8 (p99 in-market 20.8) | 0.0 | 31k / 4.5% | 416k / 59% |
| Pair + 20% VC | 30.4 / 25.6 (p99 in-market 20.8) | 0.0 | 46k / 6.5% | 608k / 87% |
| CR 80/20 pair/IMP3 | 16.7 / 16.7 (p99 in-market 16.7) | 0.0 | 25k / 3.6% | 334k / 48% |
| CR 70/30 pair/IMP3 | 17.1 / 17.1 (p99 in-market 17.1) | 0.0 | 26k / 3.7% | 341k / 49% |
| CR 80/20 pair/VC | 20.0 / 17.6 (p99 in-market 15.2) | 0.0 | 30k / 4.3% | 400k / 57% |
| CR 70/30 pair/VC | 22.0 / 18.4 (p99 in-market 14.8) | 0.0 | 33k / 4.7% | 439k / 63% |
| Pair + 10% VC + 10% BM1 + 10% Q34 ES1 (lead-only) | 25.3 / 20.8 (p99 in-market 18.4) | 2.2 | 41k / 5.8% | 537k / 77% |
| Same, equal-risk 10% each (lead-only) | 22.9 / 18.4 (p99 in-market 17.2) | 2.2 | 37k / 5.3% | 489k / 70% |
- Assumption A is an intraday/day-trade style margin (NinjaTrader Brokerage-type) that applies to all hours if positions are flat before the session end; B is exchange-style maintenance for positions outside the broker's intraday window. All books flatten by 16:55 ET (no position is carried through the 17:00-18:00 break), but about 80% of the pair's in-market minutes are Globex (outside 09:30-16:00), so the broker's treatment of the overnight window decides between A and B. Margin figures are NOT verified with the broker. Peak contracts add the books' peaks (coincident peaks are unlikely but not excluded).
- Capital reading: at B the live pair already uses 46% of $700k at its 16-contract peak; the additive IMP3 / VC books reach 59% / 87%; the CR books 48-63%. A 40%-of-equity drawdown ($280k) plus peak margin B on pair + 20% VC would exceed the account. At A all books use under 7% of the account, so capital is not the constraint, drawdown is.

## 5. Conclusions (how to read these tables)
1. Smooth weekly income: every sleeve book lowers the share of weeks below -$25k (pair 25.6% -> 15-25%) and, at 100% edge, the P(negative quarter) (pair 14% -> 0.1-4.7%), and raises P(>= 8 of 13 positive weeks) from 0.50 to 0.71-0.90.
2. Drawdown insurance: the books that reduce P(DD > $200k) at 52 weeks most are the CR 70/30 books (IMP3 2.1%, VC 0.1%); the pair itself has 46%. Pair 6/6 is the 'size-down' alternative (19.0%): it needs no new sleeve and no edge assumption, and costs 25% of the pair's mean. At 25% edge retention (52 weeks): the additive books are WORSE than the pair on P(DD > $200k) (pair + 20% IMP3 0.53, pair + 20% VC 0.54 vs pair 0.46) with medians still above the pair's ($989k / $1,229k vs $844k); the CR books stay better than the pair (0.16-0.29) but, except CR 70/30 pair/VC (0.157), not better than simply running pair 6/6 (0.19, median $633k); at 50% retention CR 80/20 pair/VC (0.118) and CR 70/30 pair/VC (0.043) beat pair 6/6 on drawdown and on median ($1,064k / $1,175k vs $633k). Joint shrink (pair AND sleeves at 50%) moves everything: the pair alone then has P(DD > $200k) = 0.78 over 52 weeks (median $420k), so the absolute levels in section 1 are best-case; only the ordering between books is robust.
3. Worst-week tail is not improved by additive sleeves (E[worst week] -72k pair -> -81 to -89k) but is improved by CR books (-57k to -71k).
4. Lead-only sensitivity (VC + BM1 + Q34 at 10% each): adds mean and cuts P(neg quarter) to 1-4%, but with the VC at raw 10% it adds 20% risk; with equal risk (10% each) P(DD > $200k) at 52 weeks is 23.4% vs 46% for the pair. Not counted.
5. Caveats: the sample is 168 weeks of the pair's best window; sleeve edges are in-sample after a selection history (the shrinkage tables are the honest read); VC's in-sample weekly mean is very large for an 18,600-trade tick-replay sleeve and rests on basis-B assumptions (fills at touched limits) - its 25% row is the one to trust; margin figures are unverified.

Files: code/census/night_ins/ap_si1_extract.py, ap_si1_b.py, ap_si1_boot.py, ap_si1_margin.py; outputs/autopilot/b/si1_*.

DONE SI1
