# REPORT RU10 - RU10 displacement continuation confirmed by a same-direction displacement (range >= 1 ATR) in the partner market

RU10: see PREREG_AUTOPILOT.md BATCH RU.


| market | selected cell | eligible | verdict | gates | additive 20% clean/H1/H2 | clean Sh | trades | ERA | own-null rank |
|---|---|---|---|---|---|---|---|---|---|
| GCxSI | nb=1, conf=1, sess=ALL, ent=mkt, k=1.5, tf=30, S=1.0, R=2.0, partner=SI | 8 | NO | 1/7 | +0.06/+0.17/-0.13 | 0.71 | 1916 | gross-positive, cost-negative pre-2023 | 0.97 |
| SIxGC | nb=1, conf=1, sess=ALL, ent=stop, k=2.0, tf=15, S=1.0, R=2.0, partner=GC | 8 | NO | 2/7 | -0.16/+0.06/+0.09 | -0.55 | 1426 | negative pre-2023 | 0.98 |
| CLxHO | nb=1, conf=1, sess=ALL, ent=mkt, k=1.5, tf=30, S=1.0, R=2.0, partner=HO | 8 | NO | 1/7 | -0.05/-0.69/-0.21 | -0.07 | 2362 | negative pre-2023 | 0.82 |
| HOxCL | nb=1, conf=1, sess=ALL, ent=stop, k=2.0, tf=15, S=1.0, R=2.0, partner=CL | 8 | NO | 3/7 | +0.09/-0.12/+0.19 | 0.87 | 2060 | gross-positive, cost-negative pre-2023 | 0.99 |
| RBxCL | nb=1, conf=1, sess=ALL, ent=mkt, k=2.0, tf=30, S=1.0, R=2.0, partner=CL | 8 | NO | 2/7 | -0.00/-0.18/-0.14 | -0.03 | 1239 | negative pre-2023 | 0.41 |
| NGxCL | nb=1, conf=1, sess=ALL, ent=mkt, k=2.0, tf=30, S=1.0, R=2.0, partner=CL | 8 | NO | 2/7 | +0.13/+0.01/-0.13 | 0.59 | 677 | negative pre-2023 | 0.97 |

Per-market reports: REPORT_RU10_<MKT>.md.

DONE RU10