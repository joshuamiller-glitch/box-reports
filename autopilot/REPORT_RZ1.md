# REPORT RZ1 - structural-level limit-order retrace on ES, RTY, YM, GC, CL, ZN, 6E

RZ1 structural-level limit-order retrace (FVG / displacement 50% retrace) on ES, RTY, YM, GC, CL, ZN, 6E.


| instrument | selected cell | eligible cells | verdict | gates | additive 20% clean/H1/H2 | standalone Sharpe | clean+H1+H2 trades | ERA | own-null rank |
|---|---|---|---|---|---|---|---|---|---|
| ES | setup=FVG, tf=15, thr=0.25 | 8 | NO | 1/7 | +0.11/-0.14/+0.46 | 1.14 | 2913 | positive pre-2023 | 1.00 |
| RTY | setup=FVG, tf=15, thr=0.5 | 8 | NO | 2/7 | +0.26/+0.05/-0.16 | 1.14 | 2038 | positive pre-2023 | 1.00 |
| YM | setup=FVG, tf=30, thr=0.25 | 8 | NO | 4/7 | +0.19/-0.31/+0.81 | 1.19 | 1806 | positive pre-2023 | 1.00 |
| GC | setup=FVG, tf=15, thr=0.25 | 8 | FOUND-PENDING-REPLICATION | 7/7 | +0.46/+0.75/+0.36 | 2.61 | 3228 | positive pre-2023 | 1.00 |
| CL | setup=FVG, tf=15, thr=0.25 | 8 | FOUND-PENDING-REPLICATION | 7/7 | +0.41/+0.36/+0.52 | 2.34 | 2992 | positive pre-2023 | 1.00 |
| ZN | setup=FVG, tf=15, thr=0.25 | 5 | NO | 4/7 | +0.07/+0.00/+0.04 | 0.62 | 59 | positive pre-2023 | 1.00 |
| 6E | setup=FVG, tf=15, thr=0.25 | 8 | NO | 2/7 | +0.12/-0.15/+0.07 | 0.70 | 2277 | gross-positive, cost-negative pre-2023 | 1.00 |

Per-instrument full reports: REPORT_RZ1_<SYM>.md (gates, insurance set, plateau, ERA decomposition, range-tercile table). Reading: the FVG/displacement retrace edge on NQ is reported by the ICT worker (REPORT_ICT.md); this is the same mechanics on other instruments with a 30-tick stop floor.

DONE RZ1