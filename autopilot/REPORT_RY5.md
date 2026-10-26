# REPORT RY5 - K4 probability scaling of the FVG E1 limit-order sleeve (pre-registered, PREREG_AUTOPILOT.md BATCH RY)
**Verdict: NO MEASURABLE EFFECT (paired CI of the all-in additive-uplift difference includes zero for every pre-declared cell).**

E1 = equal-risk tf3+tf5+tf15 FVG pullback members, tick-replay fills, R-sized (ICT worker; ap_fv_e1.trades). Each trade quantity is multiplied by clip(1 + side x sg x a x z, 0.5, 1.5), z = clip((pbar-0.5)/0.1, -1, 1) from the 5-seed K4 ensemble at the previous label of the trade's placement (sg=+1 the K4 hypothesis, sg=-1 control). Sleeves are scaled so the clean weekly sd equals the pair's, additive 20%; uplift = weekly Sharpe uplift on the live pair (library PAIR).

|     a |     sg |   base_clean |   mod_clean |   base_H1 |   mod_H1 |   base_H2 |   mod_H2 |   base_all |   mod_all |   diff_all |   ci_lo |   ci_hi |
|------:|-------:|-------------:|------------:|----------:|---------:|----------:|---------:|-----------:|----------:|-----------:|--------:|--------:|
| 0.250 |  1.000 |        0.697 |       0.706 |     0.604 |    0.656 |     1.243 |    1.219 |      0.823 |     0.831 |      0.008 |  -0.023 |   0.037 |
| 0.250 | -1.000 |        0.697 |       0.673 |     0.604 |    0.538 |     1.243 |    1.237 |      0.823 |     0.796 |     -0.027 |  -0.055 |   0.002 |
| 0.500 |  1.000 |        0.697 |       0.699 |     0.604 |    0.693 |     1.243 |    1.168 |      0.823 |     0.820 |     -0.003 |  -0.065 |   0.052 |
| 0.500 | -1.000 |        0.697 |       0.635 |     0.604 |    0.464 |     1.243 |    1.203 |      0.823 |     0.754 |     -0.069 |  -0.125 |  -0.015 |

Reading: diff_all = modified minus unmodified all-in additive uplift; ci = paired weekly bootstrap 90% interval of that difference (4,000 draws, i.i.d. weeks). This is report-only; E1 itself is FOUND-PENDING under the ICT worker and is not re-gated here.

Runtime 1.7 min.
DONE RY5