# REPORT RZ6 - range-forecast conditioning of the ICT E1 FVG sleeve (report only; pre-registered, PREREG_AUTOPILOT.md BATCH RZ)
**Verdict: NO MEASURABLE EFFECT (paired CI includes zero for every cell).**

E1 trade quantity is multiplied by mult (0 = skip, 0.5) when the causal pre-open range-forecast score (ap_rz_range score_early: expanding percentiles of prior-label range/ADR and VIX 252d percentile; the overnight leg is NOT used because E1 orders may be placed before 09:30; deviation from the registered score_full, conservative) at the trade placement label is below thr in {0.5, 0.33}. Sleeves scaled to the pair weekly sd (clean), additive 20%; uplift = weekly Sharpe uplift on the live pair.

|   thr |   mult |   base_clean |   mod_clean |   base_H1 |   mod_H1 |   base_H2 |   mod_H2 |   base_all |   mod_all |   diff_all |   ci_lo |   ci_hi |
|------:|-------:|-------------:|------------:|----------:|---------:|----------:|---------:|-----------:|----------:|-----------:|--------:|--------:|
| 0.500 |  0.000 |        0.697 |       0.523 |     0.604 |    0.421 |     1.243 |    0.784 |      0.823 |     0.574 |     -0.249 |  -0.396 |  -0.106 |
| 0.500 |  0.500 |        0.697 |       0.652 |     0.604 |    0.561 |     1.243 |    1.102 |      0.823 |     0.752 |     -0.072 |  -0.137 |  -0.008 |
| 0.330 |  0.000 |        0.697 |       0.702 |     0.604 |    0.486 |     1.243 |    1.194 |      0.823 |     0.796 |     -0.027 |  -0.119 |   0.065 |
| 0.330 |  0.500 |        0.697 |       0.714 |     0.604 |    0.567 |     1.243 |    1.244 |      0.823 |     0.827 |      0.004 |  -0.037 |   0.046 |

Reading: diff_all = conditioned minus unconditioned all-in additive uplift; ci = paired weekly bootstrap 90% interval (4,000 draws). Report-only; E1 itself is not re-gated here.

Runtime 0.7 min.
DONE RZ6