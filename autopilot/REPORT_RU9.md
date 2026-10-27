# REPORT RU9 - RU9 multi-bar continuation (nb consecutive same-direction bars, net >= k ATR), market entry

RU9: see PREREG_AUTOPILOT.md BATCH RU.


| market | selected cell | eligible | verdict | gates | additive 20% clean/H1/H2 | clean Sh | trades | ERA | own-null rank |
|---|---|---|---|---|---|---|---|---|---|
| GC | nb=3, conf=0, sess=ALL, ent=mkt, k=1.5, tf=15, S=1.0, R=2.0 | 8 | NO | 0/7 | -0.03/-0.64/-0.12 | 0.14 | 4303 | negative pre-2023 | 0.91 |
| CL | nb=2, conf=0, sess=ALL, ent=mkt, k=2.5, tf=30, S=1.0, R=2.0 | 8 | NO | 1/7 | -0.09/-0.34/-0.09 | -0.29 | 571 | positive pre-2023 | 0.55 |
| SI | nb=2, conf=0, sess=ALL, ent=mkt, k=1.5, tf=15, S=1.0, R=2.0 | 8 | NO | 2/7 | -0.20/+0.26/-0.47 | -0.79 | 3740 | negative pre-2023 | 0.97 |
| HO | nb=2, conf=0, sess=ALL, ent=mkt, k=2.5, tf=30, S=1.0, R=2.0 | 8 | NO | 2/7 | +0.09/+0.19/+0.10 | 0.51 | 748 | positive pre-2023 | 0.97 |
| RB | nb=2, conf=0, sess=ALL, ent=mkt, k=2.5, tf=30, S=1.0, R=2.0 | 8 | NO | 1/7 | +0.06/-0.39/+0.04 | 0.39 | 676 | negative pre-2023 | 0.81 |
| NG | nb=2, conf=0, sess=ALL, ent=mkt, k=2.5, tf=30, S=1.0, R=2.0 | 8 | NO | 3/7 | +0.29/-0.03/-0.22 | 1.46 | 683 | gross-positive, cost-negative pre-2023 | 0.97 |
| 6E | nb=2, conf=0, sess=ALL, ent=mkt, k=2.5, tf=15, S=1.0, R=2.0 | 8 | NO | 1/7 | -0.18/-0.04/-0.21 | -0.80 | 783 | negative pre-2023 | 0.54 |
| ES | nb=2, conf=0, sess=ALL, ent=mkt, k=2.5, tf=30, S=1.0, R=2.0 | 8 | NO | 2/7 | -0.12/+0.15/-0.01 | -0.05 | 615 | positive pre-2023 | 0.98 |
| NQ | nb=2, conf=0, sess=ALL, ent=mkt, k=2.5, tf=30, S=1.0, R=2.0 | 8 | NO | 3/7 | +0.16/+0.16/-0.25 | 1.39 | 670 | positive pre-2023 | 0.98 |

Per-market reports: REPORT_RU9_<MKT>.md.

DONE RU9