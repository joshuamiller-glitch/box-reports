# REPORT RW1 - K4 exposure timing vs an equal-exposure buy-and-hold (pre-registered, PREREG_AUTOPILOT.md BATCH R)
**Verdict: FAIL (timing does not beat equal-exposure buy-and-hold on every pre-registered criterion).** All-in weekly Sharpe K4 1.43 vs scaled buy-and-hold 0.69; paired-bootstrap 90% CI of the difference [-0.24, +1.72]; additive 20% uplift K4 +0.203 vs buy-and-hold +0.086.

Buy-and-hold comparator: always long ES, NQ, RTY, YM at the same unit ADR risk, each scaled by the K4 sleeve's own exposure fraction (days in market / eligible days, 2023-08..2026-10): ES 10.4%, NQ 9.5%, RTY 7.0%, YM 6.3%. Daily marks at the 16:16 ET px, no costs on the buy-and-hold leg (favourable to it); both series scaled to the pair clean weekly sd.

| span | K4 Sharpe | scaled B&H Sharpe | K4 additive 20% uplift | B&H additive 20% uplift |
|---|---|---|---|---|
| clean | 1.23 | 0.50 | +0.183 | +0.039 |
| H1 | 2.51 | 1.47 | +0.392 | +0.331 |
| H2 | 1.72 | 0.76 | +0.193 | +0.119 |
| all | 1.43 | 0.69 | +0.203 | +0.086 |

Timing-skill regression (daily, pair window): K4 = alpha + beta x scaled B&H: beta +1.637; alpha weekly Sharpe 1.21, bootstrap 90% CI [+0.42, +1.93].

Reading: the K4 edge is a timing edge if the K4 sleeve beats the scaled buy-and-hold on Sharpe (CI above zero) and on additive uplift in each span; if the buy-and-hold at the same average exposure is as good, the sleeve is just drift.

DONE RW1