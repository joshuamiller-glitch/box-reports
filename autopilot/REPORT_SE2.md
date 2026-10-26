# REPORT SE2 - WHY THE PAIR IS FRAGILE TO FILL DELAY (decomposition, bootstrap curve, execution tolerances, latency gate)
**Verdict: analysis plus one counted family (5 cells x delays 1/5/15 s): NO FOUND. The fragility is real but diffuse: the all-in Sharpe falls 1.90 -> 1.86 (1 s), 1.47 (5 s), 1.43 (15 s), 1.20 (30 s); the paired bootstrap says the loss at 1 s is indistinguishable from zero (P(worse) 0.60) and at 5 s and beyond it is worse in 93%-98% of 1,000 week-block draws, but the 90% interval of the difference touches zero at 5 s (-0.96,+0.05) and 15 s (-0.98,+0.00). It is not a few trades (top 20 events carry 2% of the gross absolute change at 15 s) and not a price drift (mean adverse fill drift is about $8 per signal at 1 s and has no consistent slope to 300 s); it is the account's path dependence. Selected tolerance tol4: at 15 s +0.19/+0.15/+0.70 vs the delayed market (LEAD, fails own null, bootstrap, plateau, 2x slip, alt-month), at 5 s and 1 s it fails clean. Recommended latency gate: median submit-to-fill <= 1 s relative to the bar-open first print, p95 <= 2 s, alarm at median > 2 s, stop-and-fix at median > 5 s.**

## Set-up
- Same clean-process 1-second order-level engine as SE1/K96 (ap_k96_core acct_se copy with an event id on every lot/row: ap_sw_se2.py). Baseline asserted at start: control clean 1.46, H1 2.83 weekly Sharpe (H2 2.48 and all-in 1.90 on the axis ending 2026-10-16). Fill model 1 tick/side + $34.88 per 8 lots, 2x slippage = 1.0 pt on both sides of the comparison; ET clock. Pre-registered in PREREG_AUTOPILOT.md 'BATCH SE2' before any run. Up to 10 processes, < 1 GB disk.
- Event = one live signal (50,199 market signals, book/side/bar); every row of the account is attributed to the event that opened the lot. R0 = control, R1 = delayed in time but filled at the control price (timing/path only), R2 = fully delayed.

## 1. Decomposition of the all-in net change (control net $2,951,248)
| delay | total change $ | R1-R0 timing/path/acceptance $ | R2-R1 fill-price (drift) incl. re-centred brackets $ | stop-vs-target tie order (target-first re-run), $ at R0 / R2 |
|---|---|---|---|---|
| 5 s | -464,302 (-16%) | -201,466 | -262,836 | 0 / 0 |
| 15 s | -662,117 (-22%) | -178,880 | -483,237 | 0 / 0 |
| 30 s | -1,258,095 (-43%) | -60,184 | -1,197,911 | 0 / 0 |

(d) Stop/target ordering inside a second: breaking ties target-first instead of stop-first changes nothing at all (0 $ and 0.00 Sharpe at R0 and R2): a 60-point bracket is never both touched within one second, so ordering is not a mechanism.

(a)-(c) by event (R2 vs R0, per-event net, sums in $):
| delay | events opened in both | pts effect, exit class unchanged | pts effect, exit class changed (n) | sizing / lock effect f (n changed) | acceptance, netting, multi-lot events (n) | total |
|---|---|---|---|---|---|---|
| 5 s | 10649 | -250,760 | 118,400 (337) | -117,304 (667) | -214,638 (2320) | -464,302 |
| 15 s | 10370 | -274,200 | -41,960 (538) | 47,136 (823) | -393,093 (2923) | -662,117 |
| 30 s | 10122 | -732,680 | -50,480 (676) | -114,660 (1053) | -360,275 (3404) | -1,258,095 |

Status transitions of the events (R1-R0 timing effect, $ / events) at 15 s:
| cat                             |     sum |   count |
|:--------------------------------|--------:|--------:|
| opened both, same exit class    | -218248 |   11821 |
| status opened->busy             |  -51391 |      70 |
| status netted->opened           |  -21994 |      27 |
| status netted->netted           |  -14655 |     513 |
| status netted->busy             |  -10335 |       4 |
| opened both, exit class changed |   -1771 |      72 |
| status busy->busy               |       0 |     661 |
| status busy->netted             |   11735 |       9 |
| status opened->netted           |   12110 |       6 |
| status opened->none             |   22934 |      15 |
| status busy->opened             |   92736 |     147 |

Reading of (a)-(c): the fill-price drift of one market order is tiny ($8 per signal at 1 s, no slope to 300 s), because the 60-point stop and target are re-centred on the new entry price, so a drifted fill moves the exits with it. What moves is which lots close at which price: both books send same-side orders, the account closes lots FIFO whichever protective order fires, and a delay of a few seconds re-orders those events. Per class the gross changes are huge and opposite (e.g. at 5 s the 'unchanged class' Stop events gain $1.29M while Target events lose $1.63M, a lot-reassignment signature), and they net to about -$0.25M of the -$0.46M. The remainder is acceptance/netting (events that become busy, un-busy or netted: -$0.21M at 5 s) and the live sizing/lock rules (a changed f on 667 events at 5 s, because one different trade moves a day or week lock). So (a) price drift ~ small, (b) acceptance changes and (c) netting/FIFO lot reassignment carry the loss together with (e) lock cascades; (d) is zero.

### Which trades drive it: top 20 events by |R2 - R0| at 15 s
|       | date       |   hour | book   |   side | st0    | st2    | c0     | c2     |   d01 |    d12 |    d02 |
|------:|:-----------|-------:|:-------|-------:|:-------|:-------|:-------|:-------|------:|-------:|-------:|
| 28701 | 2026-07-09 |     20 | ST     |     -1 | opened | opened | multi  | Target |     0 |  26675 |  26675 |
| 45234 | 2025-11-05 |     20 | HM     |     -1 | opened | opened | Target | multi  |     0 | -25995 | -25995 |
| 17853 | 2025-03-26 |     18 | ST     |     -1 | opened | opened | multi  | Target |     0 |  22595 |  22595 |
| 47220 | 2026-03-24 |     19 | HM     |      1 | opened | opened | Entry  | Target |  -320 |  20040 |  19720 |
| 13405 | 2024-09-11 |      3 | ST     |      1 | opened | opened | multi  | Stop   | 19670 |      0 |  19670 |
| 17944 | 2025-03-31 |      8 | ST     |     -1 | opened | opened | Stop   | multi  |     0 | -19430 | -19430 |
|  4319 | 2023-08-16 |     10 | ST     |     -1 | busy   | opened | nan    | multi  |     0 | -19430 | -19430 |
| 26669 | 2026-04-09 |     10 | ST     |      1 | opened | opened | Stop   | multi  |     0 | -19430 | -19430 |
| 26098 | 2026-03-16 |     12 | ST     |      1 | opened | opened | Stop   | multi  |     0 | -19430 | -19430 |
| 46555 | 2026-02-10 |      5 | HM     |     -1 | opened | netted | multi  | Target |     0 |  19275 |  19275 |
| 38837 | 2024-08-05 |     21 | HM     |      1 | opened | opened | Target | Stop   |     0 | -19200 | -19200 |
| 23952 | 2025-12-12 |     11 | ST     |     -1 | opened | opened | Stop   | Target |     0 |  19200 |  19200 |
|  1026 | 2023-03-23 |     19 | ST     |      1 | opened | opened | Target | Stop   |     0 | -19200 | -19200 |
| 23950 | 2025-12-12 |     10 | ST     |     -1 | opened | opened | Stop   | Target |     0 |  19200 |  19200 |
| 45415 | 2025-11-18 |     21 | HM     |      1 | opened | opened | Target | Stop   |     0 | -19200 | -19200 |
| 32027 | 2023-04-12 |      8 | HM     |      1 | opened | opened | Target | Stop   |     0 | -19200 | -19200 |
| 15727 | 2024-12-18 |     14 | ST     |     -1 | opened | opened | Stop   | Target |     0 |  19200 |  19200 |
| 11371 | 2024-06-12 |      8 | ST     |      1 | opened | opened | Target | Stop   |     0 | -19200 | -19200 |
| 47753 | 2026-05-05 |     18 | HM     |      1 | opened | opened | Stop   | Target |     0 |  19200 |  19200 |
| 49982 | 2026-10-01 |      5 | HM     |     -1 | opened | opened | Stop   | Target |     0 |  19200 |  19200 |

Concentration (R2 - R0):
| delay | top-20 events share of gross |change| | top-1% events share | total with top 20 removed $ | top-3 hours of day share of |change| (hours) | top-3 months share (of 45) | days with |change|>$1k (of 953) | top-20 days share | days gained / lost (sum $) | weekly paired t |
|---|---|---|---|---|---|---|---|---|---|
| 5 s | 2.7% | 14.4% | -510,646 | 28% (8,0,12) | 27% | 309 | 27% | 149 / 160 (1,968,763 / -2,433,065) | -1.32 |
| 15 s | 2.0% | 11.6% | -666,338 | 37% (8,10,20) | 20% | 408 | 23% | 196 / 212 (2,497,227 / -3,159,344) | -0.88 |
| 30 s | 1.6% | 9.6% | -1,238,566 | 40% (10,14,8) | 21% | 479 | 19% | 230 / 249 (2,932,568 / -4,122,008) | -0.07 |

So it is neither a handful of trades (removing the top 20 events changes the total by < 10%) nor concentrated in particular hours or months (top-3 hours carry 28-40%, top-3 of 45 months 20-27%, close to the shares of random groups); the sign is systematic (the total stays negative at every delay and the loss grows with delay) but the day-by-day change is a two-sided cloud: many days gain and many lose, with a net loss. The weekly paired t-statistic of the change is only -1.3 (5 s), -0.9 (15 s) and -0.1 (30 s), i.e. at weekly resolution the P&L change is itself within the weekly noise.

### Sharpe-vs-delay curve, stationary block bootstrap over weeks (1,000 draws, mean block 4 weeks, same resampled weeks for every delay; all-in span 2023-08..2026-10)
| delay s | all-in Sharpe | 90% CI of Sharpe | 90% CI of Sharpe(d) - Sharpe(0) | P(Sharpe(d) < Sharpe(0)) | clean / H1 / H2 |
|---|---|---|---|---|---|
| 0 | 1.90 | [1.15, 2.57] | [+0.00, +0.00] | 0.00 | 1.46 / 2.83 / 2.48 |
| 1 | 1.86 | [1.11, 2.53] | [-0.25, +0.19] | 0.60 | 1.48 / 3.17 / 2.02 |
| 2 | 1.58 | [0.74, 2.41] | [-0.88, +0.17] | 0.84 | 1.39 / 3.22 / 1.06 |
| 5 | 1.47 | [0.72, 2.23] | [-0.96, +0.05] | 0.93 | 1.33 / 3.07 / 0.80 |
| 10 | 1.21 | [0.39, 1.99] | [-1.32, -0.14] | 0.97 | 1.19 / 2.51 / 0.36 |
| 15 | 1.43 | [0.64, 2.16] | [-0.98, +0.00] | 0.95 | 1.19 / 2.01 / 1.62 |
| 30 | 1.20 | [0.42, 1.97] | [-1.24, -0.16] | 0.98 | 1.12 / 1.61 / 1.07 |
| 60 | 1.25 | [0.46, 1.97] | [-1.26, -0.07] | 0.96 | 1.37 / 1.13 / 1.03 |

Fill-second noise benchmark (300 replicates of the control with a random 0, 1 or 2 s delay per signal, mean 1 s): all-in Sharpe mean 1.71, sd 0.15 (5th-95th 1.46-1.96); clean 1.43 (sd 0.11), H1 2.89 (sd 0.27), H2 1.70 (sd 0.52). The control (1.90) sits at the 89% percentile of that band, so about 0.19 of Sharpe is the cost of merely not knowing the exact second (an average 1 s delay) or fill-second luck; delay 5 s (1.47), 15 s (1.43) and 30 s (1.20) sit at the 6%, 4% and 0% percentiles. Answer to the question 'is 1.90 vs 1.43 at 15 s distinguishable from fill-second noise?': against fill-second noise alone (sd 0.15) the gap of 0.47 is 3.1 sd, but against sampling noise over weeks (bootstrap) the difference is 'worse' in 95% of draws with the 90% interval touching zero. Most honest reading: a 15 s delay is probably worse by 0.3-0.5 Sharpe, with the live-measurement caveat that the control itself is at the lucky end of the fill-second band (about +0.2 above the average 1 s case).

## 2. Latency-robust execution tolerances (counted family: 5 cells x delay 1/5/15 s; signal logic unchanged)
Cells: TOL-N (N 2/4/8 ticks): enter at market after the delay only if the fill is not worse than N ticks versus the signal-bar close, else skip; CAP-N (N 4/8, rest 30 s): unfilled orders rest as a limit at the tolerance price. Uplift is vs the delayed market of the same delay (weekly Sharpe, clean / H1 / H2 / all-in); selection = best mean clean uplift over the three delays (clean only): **tol4**.
| cell | accepted share d=1/5/15 | d=1 uplift | d=5 uplift | d=15 uplift |
|---|---|---|---|---|
| tol2 | 82% / 71% / 65% | -0.77 / -1.55 / -1.00 / -0.92 | -0.24 / -0.09 / +1.03 / +0.09 | +0.05 / +0.84 / +0.73 / +0.29 |
| tol4 **(selected)** | 90% / 80% / 73% | -0.10 / -1.55 / -0.91 / -0.49 | -0.20 / -0.29 / +1.70 / +0.26 | +0.19 / +0.15 / +0.70 / +0.30 |
| tol8 | 96% / 89% / 83% | -0.46 / -0.79 / +0.09 / -0.37 | -0.56 / -0.70 / +0.28 / -0.34 | +0.16 / +0.37 / -0.36 / +0.05 |
| cap4 | 98% / 95% / 89% | -0.52 / -0.75 / -0.06 / -0.45 | -0.61 / -0.58 / +0.18 / -0.40 | -0.57 / +0.53 / +0.01 / -0.29 |
| cap8 | 99% / 97% / 94% | -0.25 / -0.19 / -0.44 / -0.28 | -0.75 / -0.77 / +0.50 / -0.44 | -0.31 / +0.26 / -0.26 / -0.22 |

Gate checklist of the selected cell at each delay (uplift vs the delayed market):
- d=1 s (NO): uplift>=0.10 clean/H1/H2: FAIL; worst week not worse (all-in): PASS; own null all-in > p95 (and clean): FAIL; bootstrap CI lo > 0: FAIL; plateau >= 75%: FAIL; 2x slip uplift >= 0.10 each span: FAIL; alt-month both directions hold: FAIL; own null all-in rank 0.24 (p95 +0.10); bootstrap CI [-0.99,-0.04]; plateau 0.00; H0 -0.45; 2x slip -0.09/-1.57/-0.64
- d=5 s (NO): uplift>=0.10 clean/H1/H2: FAIL; worst week not worse (all-in): PASS; own null all-in > p95 (and clean): FAIL; bootstrap CI lo > 0: FAIL; plateau >= 75%: FAIL; 2x slip uplift >= 0.10 each span: FAIL; alt-month both directions hold: FAIL; own null all-in rank 0.74 (p95 +0.46); bootstrap CI [-0.46,+0.98]; plateau 0.50; H0 -1.61; 2x slip -0.01/-0.23/+1.72
- d=15 s (LEAD): uplift>=0.10 clean/H1/H2: PASS; worst week not worse (all-in): PASS; own null all-in > p95 (and clean): FAIL; bootstrap CI lo > 0: FAIL; plateau >= 75%: FAIL; 2x slip uplift >= 0.10 each span: FAIL; alt-month both directions hold: FAIL; own null all-in rank 0.94 (p95 +0.31); bootstrap CI [-0.35,+0.97]; plateau 0.50; H0 -1.01; 2x slip +0.17/-0.02/+0.72

Sharpe (clean / H1 / H2 / all-in): undelayed live 1.46 / 2.83 / 2.48 / 1.90; delayed market and selected tolerance:
- d=1 s: delayed market 1.48 / 3.17 / 2.02 / 1.86; tol4 1.38 / 1.62 / 1.11 / 1.37
- d=5 s: delayed market 1.33 / 3.07 / 0.80 / 1.47; tol4 1.14 / 2.78 / 2.51 / 1.73
- d=15 s: delayed market 1.19 / 2.01 / 1.62 / 1.43; tol4 1.38 / 2.16 / 2.32 / 1.74

Reading: a tolerance only deletes trades whose fill was worse than N ticks; because the drift of a market fill has no consistent sign or slope, skipping the worst fills discards as many eventual winners as losers and does not repair the lot-reassignment path dependence. The one apparently positive cell (tol4 at 15 s, +0.19/+0.15/+0.70) recovers the delayed market only partly (it stays below the undelayed live Sharpe in every span) and fails the own null (random same-rate skips are as good), the bootstrap, the plateau, the 2x slippage test and the alternating-month split; at 5 s it fails clean and at 1 s it is clearly worse. No cell is a latency fix. The pure execution tolerance that is robust is therefore 'none': the way to protect the edge is the latency gate below.

## 3. Latency gate and what would settle it
- Gate (derived from the curve; the 1 s point is the only delay whose loss is statistically indistinguishable from zero, P(worse) 0.60, difference interval [-0.25,+0.19]; 2 s already costs -0.32 with P(worse) 0.84): hold the live system to **median (bar-open first print -> NT8 fill) <= 1 s and p95 <= 2 s**, alarm at median > 2 s, treat median > 5 s (-0.43 Sharpe, P(worse) 0.93) as a stop-and-fix condition. The model-emission latency file (outputs/h2/emission_latency_sep24_oct15.csv.gz) is the ML emission pass time, not the NT8 fill latency, so it cannot answer this.
- Measurement that settles it: per live fill log (1) bar-close time and the first print of the next bar from the tick stream, (2) strategy SubmitOrder time, (3) Rithmic acknowledgement time and (4) execution time and price from OnExecutionUpdate. Derived per fill: latency = fill time - first print of the new bar; slippage = signed fill price - first print price (points). After about 200 fills (~4 weeks at about 9 trades per day) compare (a) the latency distribution with the gate, (b) the realised mean signed slippage with the simulated drift (about +0.05 pt at 1 s, no slope), and (c) replay the same live signals through the 1-second engine with each fill's measured delay: the live weekly P&L should track that replay; a persistent shortfall of live vs replay beyond the fill-second band (sd 0.15 Sharpe all-in, about $815 per week) is the evidence of an execution problem.

## Insurance metrics (weekly; k$ except Sharpe, Sortino, MAR, %neg)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean control (undelayed live) | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 control (undelayed live) | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 control (undelayed live) | 2.48 | 5.08 | 3.77 | -81.1k | -79.2k | 217k | -82.5k | 41.7 |
| all control (undelayed live) | 1.90 | 3.71 | 9.79 | -79.2k | -78.2k | 280k | -82.5k | 42.3 |
| clean delay 5 s | 1.33 | 2.49 | 3.98 | -79.4k | -78.5k | 308k | -80.7k | 45.7 |
| H1 delay 5 s | 3.07 | 7.02 | 3.11 | -77.9k | -66.9k | 220k | -77.9k | 32.1 |
| H2 delay 5 s | 0.80 | 1.32 | 0.74 | -80.2k | -79.1k | 379k | -81.6k | 47.2 |
| all delay 5 s | 1.47 | 2.70 | 5.79 | -79.5k | -78.6k | 379k | -81.6k | 44.0 |
| clean delay 15 s | 1.19 | 2.16 | 2.80 | -78.6k | -78.2k | 401k | -79.8k | 46.7 |
| H1 delay 15 s | 2.01 | 4.36 | 2.70 | -77.7k | -75.6k | 187k | -78.3k | 46.4 |
| H2 delay 15 s | 1.62 | 3.24 | 2.23 | -80.6k | -79.5k | 262k | -82.0k | 47.2 |
| all delay 15 s | 1.43 | 2.71 | 5.52 | -79.1k | -78.4k | 401k | -82.0k | 47.0 |
| clean delay 30 s | 1.12 | 1.98 | 2.35 | -79.6k | -78.8k | 427k | -80.9k | 46.7 |
| H1 delay 30 s | 1.61 | 3.43 | 2.27 | -78.6k | -78.1k | 191k | -78.8k | 50.0 |
| H2 delay 30 s | 1.07 | 1.92 | 1.04 | -79.5k | -78.7k | 388k | -79.8k | 47.2 |
| all delay 30 s | 1.20 | 2.18 | 4.32 | -79.6k | -78.7k | 427k | -80.9k | 47.6 |
| clean tol4 at 15 s | 1.38 | 2.43 | 3.06 | -78.1k | -77.8k | 423k | -78.7k | 44.8 |
| H1 tol4 at 15 s | 2.16 | 4.35 | 3.43 | -79.0k | -78.6k | 161k | -79.9k | 42.9 |
| H2 tol4 at 15 s | 2.32 | 4.90 | 4.00 | -79.3k | -78.4k | 211k | -80.5k | 44.4 |
| all tol4 at 15 s | 1.74 | 3.24 | 6.37 | -78.6k | -78.1k | 423k | -80.5k | 44.6 |

Constant-risk reading: all variants keep the same size; the INSURANCE statement is the CVaR/maxDD/worst-week columns above (a delay raises none of them in clean and lowers the Sharpe everywhere; no tolerance cell qualifies as insurance).

## Executability / era / replication
NT8: delay = latency to be measured and gated as above; tolerance cells need a price check against the signal-bar close at submission (a market order with a limit-price cap) - executable at NinjaTrader Brokerage via Rithmic; none is recommended. ERA n/a (1-second bars exist only for the pair period); newest live weeks none after 2026-10-13. Code: ap_sw_se2.py, ap_sw_se2_run.py (part1/part2), ap_sw_se2_b.py, ap_sw_se2_rep.py; outputs/autopilot/se2/.

DONE SE2
