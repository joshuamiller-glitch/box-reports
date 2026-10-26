# REPORT RZ2 - structural-level limit-order retrace on BTC, ETH

RZ2 the same limit-order retrace mechanics on CME BTC and ETH futures.


| instrument | selected cell | eligible cells | verdict | gates | additive 20% clean/H1/H2 | standalone Sharpe | clean+H1+H2 trades | ERA | own-null rank |
|---|---|---|---|---|---|---|---|---|---|
| BTC | setup=FVG, tf=15, thr=0.25 | 8 | LEAD | 5/7 | +0.37/+0.30/+0.08 | 1.73 | 3816 | positive pre-2023 | 1.00 |
| ETH | setup=FVG, tf=15, thr=0.25 | 8 | NO | 4/7 | +0.36/+0.45/+0.07 | 1.72 | 3878 | positive pre-2023 | 1.00 |

Per-instrument full reports: REPORT_RZ2_<SYM>.md (gates, insurance set, plateau, ERA decomposition, range-tercile table). Reading: the FVG/displacement retrace edge on NQ is reported by the ICT worker (REPORT_ICT.md); this is the same mechanics on other instruments with a 30-tick stop floor.

DONE RZ2