# REPORT RU7 - RU7 displacement continuation with a trailing exit (trail S ATR, no target)

RU7: see PREREG_AUTOPILOT.md BATCH RU.


| market | selected cell | eligible | verdict | gates | additive 20% clean/H1/H2 | clean Sh | trades | ERA | own-null rank |
|---|---|---|---|---|---|---|---|---|---|
| GC | nb=1, conf=0, sess=ALL, ent=mkt, k=2.0, tf=30, S=1.0, R=0.0 | 16 | NO | 2/7 | -0.05/-0.19/-0.05 | -0.05 | 865 | negative pre-2023 | 0.86 |
| CL | nb=1, conf=0, sess=ALL, ent=mkt, k=1.5, tf=30, S=1.5, R=0.0 | 16 | NO | 1/7 | -0.25/-0.73/-0.24 | -1.05 | 2655 | negative pre-2023 | 0.56 |
| SI | nb=1, conf=0, sess=ALL, ent=stop, k=2.0, tf=15, S=1.5, R=0.0 | 16 | NO | 2/7 | -0.08/+0.20/+0.07 | -0.15 | 1538 | negative pre-2023 | 0.98 |
| HO | nb=1, conf=0, sess=ALL, ent=stop, k=2.0, tf=15, S=1.5, R=0.0 | 16 | NO | 3/7 | +0.12/+0.04/+0.24 | 0.94 | 2026 | gross-positive, cost-negative pre-2023 | 0.99 |
| RB | nb=1, conf=0, sess=ALL, ent=stop, k=2.0, tf=15, S=1.5, R=0.0 | 16 | NO | 2/7 | +0.00/-0.31/-0.00 | 0.10 | 1973 | positive pre-2023 | 0.59 |
| NG | nb=1, conf=0, sess=ALL, ent=stop, k=2.0, tf=15, S=1.0, R=0.0 | 16 | NO | 2/7 | +0.01/-0.09/-0.45 | 0.19 | 1629 | negative pre-2023 | 0.97 |
| 6E | nb=1, conf=0, sess=ALL, ent=stop, k=2.0, tf=30, S=1.5, R=0.0 | 16 | NO | 1/7 | -0.26/-0.81/-0.24 | -1.24 | 754 | negative pre-2023 | 0.70 |
| ES | nb=1, conf=0, sess=ALL, ent=mkt, k=2.0, tf=30, S=1.5, R=0.0 | 16 | NO | 2/7 | -0.29/-0.71/-0.37 | -1.08 | 1199 | negative pre-2023 | 0.30 |
| NQ | nb=1, conf=0, sess=ALL, ent=mkt, k=2.0, tf=15, S=1.0, R=0.0 | 16 | NO | 2/7 | +0.26/-0.22/-0.10 | 1.55 | 2082 | negative pre-2023 | 1.00 |

Per-market reports: REPORT_RU7_<MKT>.md.

DONE RU7