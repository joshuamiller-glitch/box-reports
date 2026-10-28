# DS3 T-FOOTPRINT (D3FP): order-flow footprint triggers, confirmations and cluster zones on NQ
Written 2026-10-28T02:10Z. Research only (no live / execution-server / chart change; UNTOUCHED never read; no downloads; no credentials). Directive: DIRECTIVE_FOOTPRINT.md + the cluster-zones addendum (DIRECTIVE_ADDENDA_WASHOUT_ICT_FP.md item 4). Code l2vast/ds3/code/fp/, prereg l2vast/ds3/prereg/FP_*_prereg.md (17 files, sha256 in DECISIONS.md BEFORE scoring), results l2vast/ds3/out/FP/, rows l2vast/ds3/rows/DS3_TFOOTPRINT.json.

## 1. Verdict
**0 PASS, 0 CANDIDATE, 366 DEAD out of 366 registered cells (174 standalone-trigger cells in 6 groups, 192 confirmation cells in 11 groups). Nothing in the footprint family survives the V2 gates on the conservative basis; no spec is written.** Standalone: {'DEAD': 174}; confirmation: {'DEAD': 192}. Ledger +366 trials (preregs appended before any scored cell; see section 8 for the two engineering tests that printed results of two registered cells before their prereg).

Reading in four lines. (1) Standalone footprint triggers lose money net of costs on the conservative basis: across the 168 scorable standalone cells the mean WF per-trade result is -1.90 pts (median -1.83); only 18 cells have a positive WF weekly mean, 3 are positive in PRE, WF and HOLD together, and 1 has a WF weekly CI lower bound above 0 (FP_CZB2_1m_N_KS, +$54/wk at 0.45 trades/wk). (2) The one large PRE winner, FP_UAfade_5m_Z_K60 (resting fade of an unfinished 20-bar extreme at a liquidity zone, PRE +$5.6k/wk, +5.2 pts/trade, all four placebo ranks 1.00 on PRE), reverses in the holdout (WF +$0.5k, HOLD -$5.2k, 2023 span -$5.9k): selection noise. (3) As an entry CONDITION on ST / KB / pullback / SBS (paired lift of kept vs all trades) nothing is stable: 48 of 130 scorable confirmation cells have a positive WF lift, none passes; the closest, CF_ST_AB_1m_k15 (absorption then a break in the entry direction within 15 min before an ST entry, +9.9 pts/trade [+2.8, +16.4], placebo 0.992, HOLD +6.3) fails the 2023 span (-11.0) and best-of-N, and the same family does NOT replicate on HM / SM / EM / the pullback variants / 3-min bars (follow-up groups CF10, CF11). (4) Cluster zones: the flags fire almost only on 1-minute bars (A: 4,904 / 1,786 runs of >=2 / >=3; B: 322 / 77; 3-min 12 / 1; 5-min and tick bars 0-8); the continuation-type B zone on a structure stop (FP_CZB2_1m_N_KS) is the best standalone cell by gates (4 failed) but it is 0.45 trades/wk (173 trades in 3.7 years), its 2023 span is negative and one year carries most of it. A second low-frequency lead, the RESPONSIVE open (cumulative delta against the opening location, fade into value; 259 days), is positive in PRE, WF, HOLD and 2023 on the 1-min K60 cell but is 1.4 trades/wk with a per-trade MDE of about 10 pts against an effect of +1.8: it cannot be established.

## 2. Deliverability and the 1-min bar-proxy identity number
Directive: execution-server unless the 1-min bar-level proxy reproduces >= 90% of the signals. Identity = Jaccard of the signal sets on 1.32M 1-min bars (OHLCV-only proxies P1/P2; out/tape/_proxy_identity.csv, README_TAPELAYER). **Only absorption (strict 56 / loose 5,112 signals) and price BOS (109,866) reproduce at identity 1.00; every other family fails the 0.90 test and needs the execution server / NT8 Volumetric tick-level bid/ask volume.**

| family | tick-built signals | best proxy Jaccard (P1/P2) | bar-proxyable (>=0.90)? | executable from |
|--|--|--|--|--|
| absorption (strict / loose) | 56 / 5,112 | 1.00 / 1.00 | YES | NT8 1-min OHLCV bars |
| price BOS | 109,866 | 1.00 / 1.00 | YES | NT8 1-min OHLCV bars |
| stacked imbalance buy r3 / sell r3 | 110k / 111k | 0.18 / 0.22 | NO | execution server / Volumetric |
| stacked imbalance r4 | 70k | 0.13 / 0.15 | NO | execution server / Volumetric |
| unfinished auction high / low | 192k / 193k | 0.14 / 0.13 | NO | execution server / Volumetric |
| cluster zones (run >= 2) | 8-9k | 0.10 / 0.14 | NO | execution server / Volumetric |
| delta divergence (best dvx60 bar) | 33-39k | 0.55 / 0.63 | NO | execution server / Volumetric |
| CD BOS up / down | 68k / 67k | 0.10 / 0.16 | NO | execution server / Volumetric |
| initiative / responsive open | 11.9k / 7.8k | 0.62 / 0.70 ; 0.46 / 0.52 | NO | execution server / Volumetric |
Only the loose-absorption cells (FP_ABloose_*, CF_*_AB*_*) are bar-reproducible, and they are DEAD. Everything else would need Volumetric bars on the execution server even if it had passed.

## 3. Top 10 regardless of verdict (fewest failed gates, ties by the standardised effect)
Failed-gate codes. Standalone: g1 trades/wk >= 3, g2 PRE>0, g3 WF>0 with CI>0, g4 HOLD>0, g5 2023-span>0, g6a/g7b/g8c/g9d placebo (a) timing-destroyed / (b) same-rule-random-clock / (c) random-in-regime / (d) random-direction bracket beta rank >= .95 (WF per-trade mean), g10x2 2x cost, g11yr single-year share <= 60%, g12nb neighbours, g13mir paired per-trade vs MIRROR CI>0, g14N best-of-N. Confirmation (V2 trade-modifier + D3WO extras): CI paired CI/maxDD, DD, mean, hold, plc90 / plc95 placebo, nb, x2, yr, span2 second-span lift, eqrisk equal-risk dollars, N best-of-N.

| # | cell | kind | effect (WF) | MDE (80%) | z | failed gates | tier |
|--|--|--|--|--|--|--|--|
| 1 | CF_ST_AB_1m_k15 | confirmation | +9.93 lift pts/trade (kept - all, WF) | 9.63 pts | 2.9 | span2,N | DEAD |
| 2 | CF_PB3B_R60_P2_AB13_3m_k15 | confirmation | +12.73 lift pts/trade (kept - all, WF) | 14.98 pts | 2.4 | nb,span2,N | DEAD |
| 3 | CF_HM_AB13_1m_k5 | confirmation | +14.44 lift pts/trade (kept - all, WF) | 18.84 pts | 2.1 | yr,span2,N | DEAD |
| 4 | FP_CZB2_1m_N_KS | standalone | +2.77 pts/trade (WF, CONS) | 3.91 pts | 3.5 | g1,g5,g11yr,g14N | DEAD |
| 5 | CF_KB_AB_1m_k15 | confirmation | +8.41 lift pts/trade (kept - all, WF) | 10.29 pts | 2.3 | nb,yr,eqrisk,N | DEAD |
| 6 | CF_ST_AB_1m_k5 | confirmation | +12.07 lift pts/trade (kept - all, WF) | 19.46 pts | 1.7 | CI,yr,eqrisk,N | DEAD |
| 7 | CF_PB3B_R5_P3_AB13_1m_k15 | confirmation | +8.08 lift pts/trade (kept - all, WF) | 14.34 pts | 1.6 | nb,CI,yr,plc95,N | DEAD |
| 8 | CF_KB_AB_1m_k5 | confirmation | +7.94 lift pts/trade (kept - all, WF) | 16.10 pts | 1.4 | CI,yr,plc95,eqrisk,N | DEAD |
| 9 | CF_ST_SI44_t500_k5 | confirmation | +1.59 lift pts/trade (kept - all, WF) | 3.32 pts | 1.3 | plc90,CI,yr,eqrisk,N | DEAD |
| 10 | CF_PB3D_R3_P2_AB13_1m_k15 | confirmation | +7.93 lift pts/trade (kept - all, WF) | 16.81 pts | 1.3 | CI,yr,plc95,span2,N | DEAD |

Details of the ten (standalone: trades, trades/wk, weekly CONS mean PRE / WF [CI] / HOLD / 2023 span, placebo ranks WF a/b/b2/c/d, paired vs mirror; confirmation: take, n kept, lift PRE / WF [CI] / HOLD / 2023, mirror lift, placebo rank, weekly $ kept-minus-base, maxDD change):

1. **CF_ST_AB_1m_k15**: take 0.030, 227 kept of 7105 WF trades; lift PRE 15.83 / WF +9.93 [2.82, 16.36] / HOLD 6.28 / 2023 span -10.96 pts/trade (MDE 9.63); mirror (no confirmation) lift -0.33, kept-minus-mirror 10.26 (CI low 2.91); win kept 0.595 / all 0.517; placebo rank 0.992 (p95 of the random-removal lift 6.57); weekly $ kept minus base -10,775, maxDD change -191,513; 2x-cost lift 9.94; best-of-N p95 28.04 (per base 20.36); failed: span2,N.
2. **CF_PB3B_R60_P2_AB13_3m_k15**: take 0.018, 108 kept of 5523 WF trades; lift PRE 18.71 / WF +12.73 [1.21, 22.59] / HOLD 8.12 / 2023 span -8.30 pts/trade (MDE 14.98); mirror (no confirmation) lift -0.25, kept-minus-mirror 12.98 (CI low 1.24); win kept 0.620 / all 0.515; placebo rank 0.993 (p95 of the random-removal lift 8.29); weekly $ kept minus base -3,429, maxDD change -450,431; 2x-cost lift 12.34; best-of-N p95 28.04 (per base 18.01); failed: nb,span2,N.
3. **CF_HM_AB13_1m_k5**: take 0.012, 66 kept of 5271 WF trades; lift PRE 6.18 / WF +14.44 [0.90, 27.03] / HOLD 19.77 / 2023 span -24.28 pts/trade (MDE 18.84); mirror (no confirmation) lift -0.18, kept-minus-mirror 14.62 (CI low 0.92); win kept 0.652 / all 0.523; placebo rank 0.980 (p95 of the random-removal lift 11.91); weekly $ kept minus base -8,242, maxDD change -204,163; 2x-cost lift 13.67; best-of-N p95 28.04 (per base 15.71); failed: yr,span2,N.
4. **FP_CZB2_1m_N_KS**: 173 trades (0.4/wk), weekly $ at 10 lots PRE 396 / WF 248 [54, 453] / HOLD 82 / 2023 -1,071; +2.77 pts/trade (MDE 3.91), weekly MDE $282, win 0.500 vs required 0.375 at R 1.67; mapped (credit) WF 297; placebos (a) 1.00 (b) 1.00 (b2 diag.) 1.00 (c)  (d) 1.00; paired vs mirror 5.25 [0.63, 9.99] pts (MDE 6.60, n 62.0); x2 cost WF 94; failed: g1,g5,g11yr,g14N.
5. **CF_KB_AB_1m_k15**: take 0.032, 253 kept of 7339 WF trades; lift PRE 17.87 / WF +8.41 [1.31, 15.69] / HOLD 3.53 / 2023 span 7.32 pts/trade (MDE 10.29); mirror (no confirmation) lift -0.30, kept-minus-mirror 8.71 (CI low 1.35); win kept 0.589 / all 0.514; placebo rank 0.985 (p95 of the random-removal lift 6.15); weekly $ kept minus base -8,311, maxDD change -207,466; 2x-cost lift 8.09; best-of-N p95 28.04 (per base 20.52); failed: nb,yr,eqrisk,N.
6. **CF_ST_AB_1m_k5**: take 0.009, 70 kept of 7105 WF trades; lift PRE 12.33 / WF +12.07 [-1.94, 25.91] / HOLD 11.88 / 2023 span 24.58 pts/trade (MDE 19.46); mirror (no confirmation) lift -0.12, kept-minus-mirror 12.19 (CI low -1.96); win kept 0.614 / all 0.517; placebo rank 0.962 (p95 of the random-removal lift 11.12); weekly $ kept minus base -13,015, maxDD change -225,717; 2x-cost lift 9.00; best-of-N p95 28.04 (per base 20.36); failed: CI,yr,eqrisk,N.
7. **CF_PB3B_R5_P3_AB13_1m_k15**: take 0.022, 119 kept of 4983 WF trades; lift PRE -9.09 / WF +8.08 [-1.87, 18.13] / HOLD 17.82 / 2023 span 18.63 pts/trade (MDE 14.34); mirror (no confirmation) lift -0.20, kept-minus-mirror 8.28 (CI low -1.91); win kept 0.588 / all 0.513; placebo rank 0.942 (p95 of the random-removal lift 8.54); weekly $ kept minus base 866, maxDD change -452,223; 2x-cost lift 7.62; best-of-N p95 28.04 (per base 15.10); failed: nb,CI,yr,plc95,N.
8. **CF_KB_AB_1m_k5**: take 0.013, 104 kept of 7339 WF trades; lift PRE 9.01 / WF +7.94 [-3.61, 19.00] / HOLD 7.63 / 2023 span 13.28 pts/trade (MDE 16.10); mirror (no confirmation) lift -0.11, kept-minus-mirror 8.06 (CI low -3.65); win kept 0.587 / all 0.514; placebo rank 0.917 (p95 of the random-removal lift 9.58); weekly $ kept minus base -9,904, maxDD change -254,732; 2x-cost lift 7.60; best-of-N p95 28.04 (per base 20.52); failed: CI,yr,plc95,eqrisk,N.
9. **CF_ST_SI44_t500_k5**: take 0.248, 1714 kept of 7105 WF trades; lift PRE 2.79 / WF +1.59 [-0.81, 3.85] / HOLD 0.64 / 2023 span 1.30 pts/trade (MDE 3.32); mirror (no confirmation) lift -0.51, kept-minus-mirror 2.09 (CI low -1.08); win kept 0.529 / all 0.517; placebo rank 0.887 (p95 of the random-removal lift 2.07); weekly $ kept minus base -8,147, maxDD change -94,293; 2x-cost lift 1.96; best-of-N p95 28.04 (per base 20.36); failed: plc90,CI,yr,eqrisk,N.
10. **CF_PB3D_R3_P2_AB13_1m_k15**: take 0.023, 85 kept of 3387 WF trades; lift PRE 7.69 / WF +7.93 [-4.24, 19.48] / HOLD 8.58 / 2023 span -10.81 pts/trade (MDE 16.81); mirror (no confirmation) lift -0.20, kept-minus-mirror 8.13 (CI low -4.35); win kept 0.588 / all 0.517; placebo rank 0.905 (p95 of the random-removal lift 10.23); weekly $ kept minus base -1,112, maxDD change -515,135; 2x-cost lift 7.49; best-of-N p95 28.04 (per base 12.98); failed: CI,yr,plc95,span2,N.

## 4. Standalone triggers (174 cells, 6 groups): what each family does
Basis for every number: conservative (CONS: positive stop-exit credit of the corrected-P9 mapping removed), 10 lots, per-book locks, $4.84 RT, flat 16:55. WF = 2024-02..2026-10-16 (142 wk); PRE = 2024-02..2025-06; HOLD = 2025-07..; 2023 span = 2023-04..2024-01. The mapped-with-credit weekly mean is shown only as a reference column in the cell table.

| family | cells | <100 trades | PRE>0 | WF>0 | mean WF pts/trade | median | best | best-of-N null p95 (pts/trade) | per-trade MDE range (WF) |
|--|--|--|--|--|--|--|--|--|--|
| SI stacked imbalance | 60 | 0 | 3 | 5 | -2.35 | -2.10 | +0.62 | 11.06 | 0.55-12.03 |
| UA unfinished auction + revisit | 29 | 0 | 1 | 1 | -2.14 | -2.04 | +0.51 | 11.06 | 0.26-6.23 |
| DD delta divergence | 30 | 0 | 0 | 0 | -2.41 | -2.51 | -0.77 | 11.06 | 0.24-3.56 |
| AB absorption + break | 10 | 2 | 2 | 1 | -1.06 | -1.40 | +1.70 | 11.06 | 1.10-10.72 |
| IR initiative/responsive open | 8 | 0 | 4 | 5 | -0.89 | +0.44 | +1.78 | 11.06 | 4.27-11.38 |
| CD cumulative-delta BOS / price BOS | 25 | 0 | 3 | 3 | -1.01 | -0.99 | +0.31 | 11.06 | 0.47-3.51 |
| CZ cluster zones | 12 | 4 | 2 | 3 | -0.31 | -1.07 | +4.36 | 11.06 | 0.99-22.48 |

Best-of-N (primary): the p95 of the maximum, over N = 366 registered cells, of one placebo-(b) deviation per cell is 11.06 pts/trade (literal, dominated by the thinnest cells) and 3.11 sigma when standardised; per bracket class (secondary column): K60 11.06 pts, KS 2.59 pts. No cell exceeds the primary null; 2 cells exceed their class null (see the cell table, column N-cls).

Bracket classes: K60 (DS2 60/60) 112 cells, 13 with WF>0, mean -2.19 pts/trade; KS (structure stop, 2R) 56 cells, 5 with WF>0, mean -1.31.

Family notes. SI: mean WF pts/trade by context N -1.30, T (trend-aligned) -0.64, TS (after a sweep) -2.35, TZ (at a zone) -4.07; the best cell FP_SI33_5m_T_K60 (+0.61 pts/trade WF, CI of the weekly mean includes 0, HOLD positive) is beaten by the same-rule-random-clock placebo (b) at rank 0.00 (the placebo keeps the event's side inside the same day and therefore carries the day's direction; the diagnostic (b2) is shown beside it); the zone and sweep contexts are thin (4-9 trades/wk) and worse. UA: the fade (limit at the unfinished extreme) and continuation (stop through it) are mirror orders at one level and are equally negative (-1.7 / -1.8 pts/trade); the finished-extreme control is -4.0, so the unfinished flag is worth about 2 pts/trade relative to a finished extreme but still loses net. DD: all 30 cells are negative WF (mean -2.4 pts/trade): fading divergences at swing points or 60-bar extremes loses with a 60-pt stop and with a structure stop. AB: loose absorption then break is about -1 pt/trade; the strict flag has 56 one-minute signals (not scored). IR: 8 cells are 1.3-2.1 trades/wk (402 initiative and 259 responsive days in 3.7 years) so they are under the 3/wk frequency gate by construction; sign is mixed. CD: cumulative-delta BOS -1.0 pt/trade, the price-BOS comparator (bar-proxyable) the same: no cd-specific information. CZ: see section 6.

## 5. Confirmation as a paired entry condition (192 cells, 11 groups)
Base entries: ST10 (direct true P9), KB (TE7_kelt3m_n14_m1.0), PB3B_R5_P1, SBS (S3_B_N12_tf5m rebuilt), plus HM, SM, EM, PB3B_R60_P2, PB3B_R5_P3, PB3D_R3_P2 for the cluster-zone and (follow-up) absorption conditions. 192 cells, 62 with fewer than 30 kept or mirror WF trades (cluster-zone and some absorption conditions), 130 scorable; WF lift > 0 in 48, WF paired CI lower bound > 0 in 4, placebo rank >= 0.95 in 5, HOLD lift > 0 in 58, second-span lift > 0 in 51. Best-of-N null: p95 of the maximum over N = 366 cells of a random-removal lift = 28.04 pts/trade literal (3.66 sigma standardised; per base EM 11.62, HM 15.71, KB 20.52, PB3B_R5_P1 19.36, PB3B_R5_P3 15.10, PB3B_R60_P2 18.01, PB3D_R3_P2 12.98, SBS 18.10, SM 19.04, ST 20.36); the best cell has z = 2.63.

| base | family | cells | scorable | WF lift>0 | mean WF lift | mean take | mean PRE lift | mean HOLD lift | mean 2023 lift | mean mirror lift |
|--|--|--|--|--|--|--|--|--|--|--|
| EM | AB13 | 4 | 1 | 0 | -0.79 | 0.036 | -5.73 | +3.62 | -8.45 | +0.03 |
| EM | CZA | 2 | 0 | | | 0.003 | | | | |
| EM | CZB | 2 | 0 | | | 0.002 | | | | |
| HM | AB13 | 4 | 4 | 3 | +5.61 | 0.016 | +4.46 | +5.94 | +3.08 | -0.10 |
| HM | CZA | 2 | 0 | | | 0.000 | | | | |
| HM | CZB | 2 | 0 | | | 0.000 | | | | |
| KB | AB | 6 | 5 | 4 | +5.86 | 0.014 | +8.08 | +5.05 | +1.12 | -0.09 |
| KB | AB3 | 2 | 2 | 1 | +0.88 | 0.016 | -4.61 | +4.37 | -6.30 | -0.03 |
| KB | CD | 6 | 6 | 3 | -0.22 | 0.423 | -0.75 | +0.09 | -2.66 | +0.27 |
| KB | CZA | 2 | 0 | | | 0.000 | | | | |
| KB | CZB | 2 | 0 | | | 0.000 | | | | |
| KB | DD | 6 | 6 | 2 | +0.54 | 0.031 | +5.54 | -4.56 | -10.45 | +0.01 |
| KB | SI33 | 6 | 6 | 0 | -0.74 | 0.584 | -0.36 | -1.01 | -2.43 | +0.93 |
| KB | SI44 | 6 | 6 | 1 | -2.22 | 0.282 | -0.79 | -3.40 | +1.30 | +0.53 |
| PB3B_R5_P1 | AB | 6 | 4 | 2 | -1.90 | 0.014 | -3.09 | -0.72 | -19.66 | -0.01 |
| PB3B_R5_P1 | AB3 | 2 | 2 | 0 | -4.15 | 0.015 | -9.31 | -2.19 | -38.66 | +0.03 |
| PB3B_R5_P1 | CD | 6 | 6 | 1 | -0.64 | 0.312 | -2.25 | +0.44 | -0.31 | +0.48 |
| PB3B_R5_P1 | CZA | 2 | 0 | | | 0.000 | | | | |
| PB3B_R5_P1 | CZB | 2 | 0 | | | 0.000 | | | | |
| PB3B_R5_P1 | DD | 6 | 5 | 1 | -4.93 | 0.035 | -5.56 | -4.46 | -5.78 | +0.19 |
| PB3B_R5_P1 | SI33 | 6 | 6 | 3 | -0.01 | 0.512 | +0.77 | -0.62 | -1.69 | +0.57 |
| PB3B_R5_P1 | SI44 | 6 | 6 | 1 | -1.09 | 0.226 | -0.05 | -1.91 | +3.13 | +0.39 |
| PB3B_R5_P3 | AB13 | 4 | 3 | 1 | -0.22 | 0.015 | -13.03 | +6.82 | +5.46 | -0.03 |
| PB3B_R5_P3 | CZA | 2 | 0 | | | 0.001 | | | | |
| PB3B_R5_P3 | CZB | 2 | 0 | | | 0.000 | | | | |
| PB3B_R60_P2 | AB13 | 4 | 4 | 2 | +1.37 | 0.014 | +5.08 | -1.46 | -16.94 | -0.01 |
| PB3B_R60_P2 | CZA | 2 | 0 | | | 0.000 | | | | |
| PB3B_R60_P2 | CZB | 2 | 0 | | | 0.000 | | | | |
| PB3D_R3_P2 | AB13 | 4 | 2 | 2 | +5.38 | 0.019 | +8.63 | +3.47 | +12.39 | -0.13 |
| PB3D_R3_P2 | CZA | 2 | 0 | | | 0.004 | | | | |
| PB3D_R3_P2 | CZB | 2 | 0 | | | 0.000 | | | | |
| SBS | AB | 6 | 2 | 0 | -5.89 | 0.035 | -4.67 | -6.60 | -5.15 | +0.17 |
| SBS | AB3 | 2 | 1 | 0 | -5.85 | 0.016 | -9.70 | -2.56 | -7.10 | +0.10 |
| SBS | CD | 6 | 6 | 3 | +0.23 | 0.346 | -0.46 | +0.94 | -2.06 | +0.05 |
| SBS | CZA | 2 | 0 | | | 0.002 | | | | |
| SBS | CZB | 2 | 0 | | | 0.001 | | | | |
| SBS | DD | 6 | 3 | 1 | -4.13 | 0.022 | +2.39 | -13.60 | -0.57 | +0.11 |
| SBS | SI33 | 6 | 6 | 2 | -0.26 | 0.508 | -0.04 | -0.51 | -0.39 | +0.23 |
| SBS | SI44 | 6 | 6 | 2 | +0.30 | 0.218 | -0.88 | +1.47 | +2.34 | +0.03 |
| SM | AB13 | 4 | 3 | 1 | -2.99 | 0.030 | -4.84 | -0.97 | -9.19 | +0.05 |
| SM | CZA | 2 | 0 | | | 0.002 | | | | |
| SM | CZB | 2 | 0 | | | 0.001 | | | | |
| ST | AB | 6 | 4 | 3 | +5.99 | 0.013 | -1.88 | +8.54 | +8.85 | -0.12 |
| ST | AB3 | 2 | 2 | 1 | -5.79 | 0.010 | -4.78 | -6.11 | -30.60 | +0.02 |
| ST | CD | 6 | 6 | 2 | -1.09 | 0.320 | -2.71 | +0.10 | -1.27 | +0.06 |
| ST | CZA | 2 | 0 | | | 0.001 | | | | |
| ST | CZB | 2 | 0 | | | 0.000 | | | | |
| ST | DD | 6 | 5 | 1 | -1.34 | 0.083 | -1.68 | -0.88 | -5.23 | +0.05 |
| ST | SI33 | 6 | 6 | 0 | -0.50 | 0.532 | -1.12 | -0.08 | +1.80 | +0.83 |
| ST | SI44 | 6 | 6 | 5 | +1.28 | 0.246 | +1.75 | +0.92 | +2.28 | -0.30 |

Reading. SI / DD / CD conditions are noise around zero (mean WF lift by family: SI33 -0.4, SI44 -0.4, CD -0.4, DD -2.1 pts/trade; signs flip between bases and between the PRE, HOLD and 2023 windows). The absorption-then-break condition has large lifts on ST (+6) and KB (+6) with take-rates of 1-3% (60-250 kept trades), is negative on PB3B_R5_P1 and SBS, mixed on HM (+14 at k5 on one bar set, +7 at k15), ~0 on SM / EM, and flips sign across the 2023 span; the follow-up groups CF10 / CF11 (written after the looks, flagged FOLLOW-UP) show it does not replicate. Because the condition removes 97-99% of trades the weekly dollars of the kept book are far below the base (the kept book earns $8k-$14k/wk less than the base on ST and KB at 10 lots, $7-9k on PB3B_R5_P1) even where the per-trade lift is positive; the maxDD of the kept book is lower only because it trades 30 times less. Mirror (entries WITHOUT the confirmation): the mean mirror lift is between -0.04 and +0.64 pts/trade per family (largest single cell 2.3), i.e. no 'unconfirmed entries fade' effect.

## 6. Cluster zones (addendum item 4)
Flags: share >= 0.4 of the bar's bid (ask) volume in the lowest/highest 3 traded ticks and that volume >= 0.25 x the mean bar volume; runs of >= 2 / >= 3 consecutive bars. 1-min bars carry almost all the events (A at a 20-bar extreme, long and short: 4,904 events for run>=2 and 1,786 for run>=3; B 'reverse': 322 / 77); on 3-min only 12 / 1 and on 5-min and tick bars 0-8, so the flag rule effectively fires only on 1-minute bars. A = exhaustion (fade at a 20-bar extreme), B = reverse/continuation, both as standalone triggers (cells FP_CZ*), as a condition on ST / KB / PB3B_R5_P1 / SBS (groups CF2/4/6/8) and on HM / SM / EM / three pullback variants (CF9). Take-rates of the condition on the base entries are 0.0-0.4%, i.e. under 30 kept trades in nearly every cell (DEAD too few; see the cell table).

| cell | trades | /wk | PRE wk | WF wk [CI lo] | HOLD | 2023 | pts/trade WF (MDE) | placebo a/b/c/d | failed |
|--|--|--|--|--|--|--|--|--|--|
| FP_CZA2_1m_N_K60 | 600 | 2.4 | -2,159 | -2,292 [-5,209] | -2,403 | -5,443 | -4.75 (8.75) | /// | g1,g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |
| FP_CZA2_1m_N_KS | 1543 | 5.5 | -2,503 | -1,782 [-2,602] | -973 | -4,207 | -1.62 (0.99) | /// | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |
| FP_CZA3_1m_N_K60 | 338 | 1.2 | -3,032 | -836 [-2,922] | 1,562 | -57 | -3.54 (12.49) | /// | g1,g2,g3,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |
| FP_CZA3_1m_N_KS | 635 | 2.1 | -626 | -383 [-867] | -115 | 54 | -0.93 (1.68) | /// | g1,g2,g3,g4,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |
| FP_CZB2_1m_N_K60 | 124 | 0.4 | 790 | 317 [-1,067] | -202 | -1,946 | +4.36 (22.48) | 0.97/0.53//0.75 | g1,g3,g4,g5,g7b,g9d,g11yr,g13mir,g14N |
| FP_CZB2_1m_N_KS | 173 | 0.4 | 396 | 248 [54] | 82 | -1,071 | +2.77 (3.91) | 1.00/1.00//1.00 | g1,g5,g11yr,g14N |
| FP_CZB3_1m_N_K60 | 44 | | | | | | | | too few trades |
| FP_CZB3_1m_N_KS | 50 | | | | | | | | too few trades |
| FP_CZA2_30s_N_K60 | 1439 | 6.9 | -2,514 | -1,660 [-6,507] | -709 | 210 | -1.20 (5.16) | /// | g2,g3,g4,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |
| FP_CZA2_t250_N_K60 | 75 | | | | | | | | too few trades |
| FP_CZB2_30s_N_K60 | 506 | 1.7 | -540 | 823 [-1,203] | 2,293 | 1,572 | +2.41 (10.37) | /// | g1,g2,g3,g6a,g7b,g9d,g11yr,g12nb,g13mir,g14N |
| FP_CZB2_t250_N_K60 | 0 | | | | | | | | too few trades |

The 'A' exhaustion zones (buying at lows) are negative in WF as standalone fades (A2 K60/KS, A3); the 'B' continuation zones are positive in PRE and WF on a structure stop (+2.8 pts/trade WF on FP_CZB2_1m_N_KS) but at 0.45 trades/wk the whole cell is 173 trades, one year carries it and the 2023 span is negative: a low-frequency lead that cannot be established at this sample (per-trade MDE 3.9 pts).

## 7. Placebos and controls (cells with PRE>0 only: 15 standalone cells ran them)
| cell | WF pts/trade | rank (a) timing | (b) same-rule-clock | (b2) rule-side clock [diag.] | (c) in-regime | (d) random-direction beta | paired vs mirror pts [CI lo] | z vs (b) |
|--|--|--|--|--|--|--|--|--|
| FP_UAfade_5m_Z_K60 | +0.51 | 0.85 | 1.00 | 0.88 | 1.00 | 0.88 |  [] | 7.7 |
| FP_CZB2_1m_N_KS | +2.77 | 1.00 | 1.00 | 1.00 |  | 1.00 | 5.25 [0.63] | 3.5 |
| FP_IRresp_1m_N_K60 | +1.78 | 0.75 | 1.00 | 0.57 |  | 0.85 | 7.57 [-7.14] | 2.8 |
| FP_IRini_1m_N_KS | +0.20 | 0.80 | 0.75 | 0.95 |  | 0.82 | 2.34 [-2.74] | 0.5 |
| FP_ABloose_3m_N_KS | -1.33 | 0.53 | 0.45 | 0.60 |  | 0.72 | 0.00 [-2.19] | 0.0 |
| FP_CZB2_1m_N_K60 | +4.36 | 0.97 | 0.53 | 0.78 |  | 0.75 | 11.03 [-19.38] | -0.2 |
| FP_ABloose_3m_N_K60 | -1.46 | 0.57 | 0.35 | 0.62 |  | 0.62 | 2.41 [-5.15] | -0.2 |
| FP_CDnop_5m_N_K60 | +0.18 | 0.97 | 0.30 | 0.97 |  | 1.00 | 6.47 [1.75] | -0.7 |
| FP_CDwithp_1m_N_K60 | -0.36 | 0.95 | 0.05 | 0.97 |  | 1.00 | 4.36 [-0.33] | -1.5 |
| FP_CDpbos_3m_N_K60 | -0.47 | 0.90 | 0.00 | 0.93 |  | 0.93 | 1.57 [-2.69] | -3.3 |
| FP_SI34_5m_TS_K60 | -1.92 | 0.60 | 0.00 | 0.57 | 0.45 | 0.53 | -0.37 [-10.12] | -3.5 |
| FP_IRini_t500_N_K60 | -2.40 | 0.45 | 0.00 | 0.03 |  | 0.55 | -1.01 [-13.65] | -6.0 |
| FP_IRini_1m_N_K60 | -4.44 | 0.33 | 0.00 | 0.03 |  | 0.23 | -5.10 [-17.29] | -9.5 |
| FP_SI33_5m_T_K60 | +0.61 | 1.00 | 0.00 | 0.88 | 0.80 | 1.00 | 4.28 [-0.10] | -15.1 |
| FP_SI33_t500_T_K60 | +0.02 | 0.97 | 0.00 | 0.33 | 0.82 | 1.00 | 2.76 [-1.45] | -17.9 |

Caveat on (b): the preregistered same-rule-random-clock placebo keeps the event's side while moving its time inside the same label day, so it inherits the day's direction (a day-level oracle); for trend-aligned cells it is a very strong control (rank 0.00 for SI33_5m_T) and for resting-order fades of random bar extremes it is a very weak one (rank 1.00 for UAfade because random-bar limit fades lose 12 pts/trade). The diagnostic (b2) re-derives the side from the rule's own side function at the shifted time (trend sign for T contexts, delta sign for continuation families, minus delta sign for reversal families; UA by the position of the close). The gates use (b) as registered. Replacing (b) by (b2) puts three cells above 0.95 on (a), (b2) and (d) (FP_CZB2_1m_N_KS, FP_CDnop_5m_N_K60, FP_CDwithp_1m_N_K60), but all three still fail the weekly gates (WF CI, HOLD / 2023 sign, x2 cost), so no verdict changes.

## 8. CANDIDATE / PASS specs
None. No cell reached PASS or CANDIDATE (CANDIDATE = exactly one failed gate with PRE, HOLD and CONS WF positive; the best cell fails two: CF_ST_AB_1m_k15, second-span lift and best-of-N). The direct L2 replay (corepool) was therefore not run; it would apply only to market-entry candidates, and the resting-order cells (UA) are mapped-only in any case. Nothing was registered in PAPER-ALL.

## 9. Deviations, disclosures and caveats
1. Two engineering tests printed results of registered cells BEFORE their prereg: the first prototype (SI 3/3, 5-min, no context, K60 = FP_SI33_5m_N_K60) printed weekly means of PRE/WF/HOLD/2023 on the mapped and conservative basis, and a second test printed the PRE/WF/HOLD numbers of the structure-bracket zone cell with an EARLIER zone definition (6-pt width, no 5-min L=8 swings; 254 trades, not the registered cell). Both were negative, no cell definition was changed in response; the zone width was widened to 10 pts and L=8 swings added because the event COUNT of the zone context was too small (254 vs 1,593 events), a count-only decision. All later tests used a random keep mask or printed counts only.
2. time_3m tape layer was built by D3FP (fp_build3m.py, the audited tl_pipe code, loaded with a time_ name so no look-ahead tick is appended); it was not separately truncation-audited, and its volume/delta match time_1m on every label day except 42 month-end days (1-2 contracts). tick_500 is not in the D3BX list of separately audited bar types (same code path as tick_250/1000, which are); the preregs say 'audited' for tick_500 which is only true by code-path identity.
3. IR (initiative/responsive) as-of fix: the registered text said 'the last bar completing by 10:00 ET'; for tick bars the last window bar is only known once the next bar completes, so the code uses the first bar completing at/after 10:00 with the state of the last window bar (identical to the registered rule for time bars). A second fix before the final audit (a clamp that could pick a bar before 10:00 in a truncated frame) does not change any full-data event. fp_trunc.py: 540 checks over 5 bar sets x 4 cuts x 13 event families + 14 derived columns, 0 mismatches after the fix (first run: 2 mismatches, both the clamp bug; out/FP/trunc_audit_run1.json). The shared level/sweep/zone arrays (ic_lib) rely on the D3IC audit.
4. Placebo (b) as registered keeps the event side inside the same day (a day-direction oracle); it is the gate (g7). The rule-side diagnostic (b2) was added after seeing the first rank of 0.00 (FP_SI33_5m_T_K60) and does not enter any gate or verdict. Placebo (c) exists only for cells with a context (T/TZ/TS/Z); placebos run only for cells with CONS PRE weekly mean > 0 (15 of 174), the others are DEAD on g2 whatever the placebo (their g6-g9 are listed as failed because missing).
5. Best-of-N is computed two ways: the registered literal form (raw per-trade deviation of placebo (b) / random-removal lift, p95 of the max over N cells; dominated by the thinnest cells: 11.1 pts standalone, 28.0 confirmation) and a standardised form (sigma units: 3.1 standalone, 3.7 confirmation). The gate g14 / best_of_N uses the literal form. Under the standardised form two standalone cells exceed the null (FP_UAfade_5m_Z_K60 z 7.7, measured against placebo (b) = random-bar limit fades that lose 12 pts/trade, i.e. a null that is far too weak for resting fades; FP_CZB2_1m_N_KS z 3.5) and both still fail 8-9 / 4 other gates; the best confirmation cell has z 2.6 < 3.7. The verdict is DEAD under both forms. N is 366 (174 standalone + 192 confirmation); the preregs of CF1-CF8 said 310 and CF9 334.
6. CF10 and CF11 (32 cells, absorption condition on the remaining bases and on 3-min bars) were preregistered AFTER the logged looks of CF1-CF9, in response to the ST/KB absorption lifts they showed; they are a replication on other bases, not an independent holdout, and are flagged FOLLOW-UP in their prereg. 17 holdout looks were logged (one per group, tracks DS3_FP_<group>); all jobs computed every window but the pre-holdout texts printed PRE keys only and were hashed before HOLD / 2023 values were read.
7. Neighbours (g12) are adjacent single-parameter cells inside the registry; cells without any neighbour (UA zone/trend cells, IR, CZ) fail g12 automatically (V2: neighbours_agree needed). Cells with < 100 trades (standalone) or < 30 kept/mirror WF trades (confirmation) are DEAD for too few and listed.
8. Basis: conservative only (positive stop-exit credit removed, negative corrections kept); the mapped-with-credit weekly mean is a reference column. Resting limits fill on a strict trade-through at their price and stops at the stop or the previous 1-s close; no queue position, no partial fills, no direct L2 replay was run. The corrected-P9 correction table was calibrated on 60-pt-stop ST/HM trades and applies to 8-60 pt structure stops only as a conservative bound.
9. Data: 1-s price axis and lock engine end 2026-10-16 (the tape layer runs to 2026-10-23, unused after 10-16); dupwin (doubled-tape Sunday-open) and partial bars removed; first usable day 2023-02-10. SBS base = S3_B_N12_tf5m rebuilt with the D3SF code (3,357 trades); ST base 8,309 trades with direct true-P9 points (rows beyond the P9 file conservative); KB 8,593; PB3B_R5_P1 8,339.
10. Scope choices: stacked-imbalance variants (r,n) in {(3,3),(3,4),(4,3),(4,4)} are not crossed with every bar set and context (FP1 holds (3,3) across all five bar sets x {T,TZ,TS} x {K60,KS}; FP2 the other variants on 1/5-min and 500-tick with TZ/TS on K60 only); delta-divergence variants dvx20 are not scored; IR bar-set variants are near duplicates (same 10:00 decision); the strict absorption flag (56 one-minute signals) is not scored; cluster-zone cells on time_30s and tick_250 are an extension beyond the directive's bar list. 3-min cells use the D3FP-built tape layer.
11. No cell was run on RTY/ES; no paid pull, no download, no deletion; workers capped at 6 via corepool, memory >= 32 GB free at launch; no kills or retries. The leftover file out/FP/trades_T1.parquet is an engineering-test artefact (not a registered cell).

## 10. What would change the answer / next steps
(a) Low-frequency leads need more data than 3.7 years: the responsive open (259 days), CZ-B continuation (173 trades) and the ST/KB absorption-confirmation (60-250 kept trades) have per-trade MDEs of 4-25 pts against effects of 2-12 pts, so they can be neither confirmed nor killed; forward paper on the 1-min proxy-reproducible absorption condition is the only no-cost way to extend the sample (identity 1.00 from OHLCV). (b) Pre-2023 NQ tick/MBO would multiply the sample for every family but is a paid pull: not done. (c) No NEEDS for fee lines (NQ $4.84 RT used).

## Appendix A. Standalone cells (all 174; CONS basis, 10 lots; weekly $ per window; N-cls = exceeds its bracket-class best-of-N null)

| cell | trades | /wk | PRE | WF [CI lo] | HOLD | 2023 | pts/tr WF (MDE) | win/req | pl a/b/c/d | mir eff [lo] | x2 | failed | N-cls |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| FP_SI33_1m_T_K60 | 12003 | 24.6 | -2,891 | 2,321 [-6,901] | 7,953 | 614 | +0.47 (2.67) | 0.51/0.50 | /// | 3.07 [-1.12] | -8,944 | g2,g3,g6a,g7b,g8c,g9d,g10x2,g12nb,g13mir,g14N |  |
| FP_SI33_1m_T_KS | 33145 | 110.0 | -21,534 | -27,627 [-36,442] | -33,850 | -22,046 | -1.26 (0.55) | 0.33/0.36 | /// | -0.16 [-0.81] | -60,826 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_1m_TZ_K60 | 1094 | 5.0 | -2,371 | -2,776 [-6,562] | -3,176 | 10,888 | -2.77 (6.00) | 0.49/0.52 | /// | -1.85 [-9.81] | -5,065 | g2,g3,g4,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_1m_TZ_KS | 1715 | 7.2 | -3,468 | -3,786 [-5,335] | -4,076 | -2,329 | -2.63 (1.44) | 0.30/0.38 | /// | -1.78 [-3.88] | -6,139 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_1m_TS_K60 | 2349 | 11.2 | -5,887 | -7,181 [-13,743] | -8,483 | -2,698 | -3.21 (3.99) | 0.48/0.51 | /// | -1.87 [-7.51] | -12,239 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_1m_TS_KS | 3561 | 18.8 | -8,605 | -9,864 [-13,658] | -11,089 | -5,552 | -2.63 (1.56) | 0.31/0.36 | /// | -1.49 [-3.13] | -16,653 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_3m_T_K60 | 10206 | 24.7 | -3,694 | 1,471 [-7,482] | 7,065 | -2,121 | +0.30 (2.67) | 0.51/0.50 | /// | 2.37 [-2.26] | -12,671 | g2,g3,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_3m_T_KS | 18121 | 68.1 | -12,899 | -9,157 [-17,722] | -4,956 | -11,175 | -0.67 (0.93) | 0.34/0.35 | /// | 0.69 [-0.40] | -33,298 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_3m_TZ_K60 | 998 | 4.7 | -1,183 | -4,847 [-9,449] | -8,758 | 11,042 | -5.14 (6.15) | 0.47/0.51 | /// | -6.54 [-15.59] | -7,079 | g2,g3,g4,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_3m_TZ_KS | 1401 | 6.3 | -2,647 | -3,974 [-5,782] | -5,359 | 870 | -3.17 (1.83) | 0.30/0.39 | /// | -3.28 [-5.68] | -6,064 | g2,g3,g4,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_3m_TS_K60 | 1697 | 8.6 | -6,667 | -2,869 [-7,523] | 1,301 | -1,054 | -1.67 (4.55) | 0.50/0.51 | /// | 0.33 [-6.02] | -7,060 | g2,g3,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_3m_TS_KS | 1940 | 10.3 | -282 | -1,636 [-4,932] | -3,084 | -2,835 | -0.79 (2.51) | 0.34/0.36 | /// | 1.16 [-1.81] | -5,406 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_5m_T_K60 | 9204 | 23.7 | 1,033 | 2,875 [-5,465] | 4,835 | 4,189 | +0.61 (2.72) | 0.51/0.50 | 1.00/0.00/0.80/1.00 | 4.28 [-0.10] | -10,165 | g3,g7b,g8c,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_5m_T_KS | 12869 | 51.9 | -5,929 | -5,612 [-13,328] | -5,187 | -7,827 | -0.54 (1.20) | 0.34/0.35 | /// | 1.01 [-0.27] | -22,041 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_5m_TZ_K60 | 901 | 4.3 | -3,231 | -3,990 [-7,486] | -4,756 | 9,779 | -4.65 (6.45) | 0.47/0.51 | /// | -5.96 [-14.33] | -5,814 | g2,g3,g4,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_5m_TZ_KS | 1217 | 5.6 | -913 | -2,529 [-4,281] | -4,248 | -134 | -2.26 (2.22) | 0.32/0.38 | /// | -2.31 [-5.65] | -4,453 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_5m_TS_K60 | 1238 | 6.6 | -1,562 | 822 [-3,804] | 3,402 | -1,066 | +0.62 (5.19) | 0.52/0.51 | /// | 3.99 [-3.16] | -2,630 | g2,g3,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_5m_TS_KS | 1274 | 6.9 | -2,144 | -2,723 [-5,666] | -3,314 | -3,809 | -1.97 (3.14) | 0.32/0.36 | /// | -2.24 [-5.86] | -5,375 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_t500_T_K60 | 12515 | 24.3 | 255 | 94 [-7,652] | -82 | 2,088 | +0.02 (2.69) | 0.50/0.50 | 0.97/0.00/0.82/1.00 | 2.76 [-1.45] | -12,766 | g3,g4,g7b,g8c,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_t500_T_KS | 34001 | 84.8 | -7,201 | -7,779 [-15,906] | -8,294 | -24,159 | -0.46 (0.76) | 0.34/0.35 | /// | 1.14 [0.16] | -35,789 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g14N |  |
| FP_SI33_t500_TZ_K60 | 1393 | 6.7 | -7,763 | -8,012 [-12,629] | -8,166 | 9,082 | -5.97 (5.14) | 0.46/0.51 | /// | -8.11 [-15.80] | -10,996 | g2,g3,g4,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_t500_TZ_KS | 2022 | 9.8 | -2,315 | -3,869 [-6,202] | -5,502 | -1,049 | -1.97 (1.55) | 0.32/0.37 | /// | -0.41 [-2.51] | -7,305 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_t500_TS_K60 | 2325 | 11.0 | -5,142 | -7,044 [-13,501] | -9,009 | -2,241 | -3.21 (4.03) | 0.49/0.51 | /// | -1.94 [-7.84] | -12,063 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_t500_TS_KS | 3996 | 20.7 | -6,234 | -8,429 [-12,731] | -10,692 | -3,873 | -2.04 (1.51) | 0.33/0.36 | /// | -0.83 [-2.32] | -15,694 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_t1000_T_K60 | 11532 | 25.2 | -9,489 | -9,299 [-18,342] | -8,958 | 1,319 | -1.84 (2.65) | 0.49/0.50 | /// | -2.08 [-6.30] | -19,670 | g2,g3,g4,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_t1000_T_KS | 20259 | 53.4 | -7,746 | -8,061 [-16,307] | -8,287 | -2,843 | -0.76 (1.24) | 0.34/0.35 | /// | 0.69 [-0.78] | -26,282 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_t1000_TZ_K60 | 1139 | 5.6 | -6,622 | -5,679 [-9,994] | -4,570 | 8,314 | -5.10 (5.67) | 0.47/0.52 | /// | -6.89 [-14.49] | -8,419 | g2,g3,g4,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_t1000_TZ_KS | 1464 | 7.1 | -2,916 | -3,587 [-5,916] | -4,264 | 1,191 | -2.54 (2.35) | 0.32/0.37 | /// | -0.55 [-3.42] | -6,120 | g2,g3,g4,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_t1000_TS_K60 | 1861 | 9.2 | -6,855 | -6,665 [-12,122] | -6,362 | -737 | -3.63 (4.39) | 0.48/0.51 | /// | -3.68 [-10.32] | -10,944 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_t1000_TS_KS | 2571 | 13.4 | -5,948 | -6,719 [-10,771] | -7,460 | -2,496 | -2.50 (2.29) | 0.32/0.36 | /// | -0.41 [-3.03] | -11,701 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI34_1m_TZ_K60 | 547 | 2.4 | -1,351 | -1,640 [-4,433] | -1,931 | 8,460 | -3.40 (8.63) | 0.49/0.52 | /// | -3.39 [-15.06] | -2,684 | g1,g2,g3,g4,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI34_1m_TS_K60 | 1455 | 7.3 | -5,198 | -4,125 [-8,861] | -2,899 | -1,353 | -2.83 (4.95) | 0.49/0.51 | /// | -2.54 [-9.59] | -7,453 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI34_5m_TZ_K60 | 459 | 2.1 | -2,051 | -2,615 [-5,458] | -3,191 | 3,889 | -6.11 (9.15) | 0.46/0.51 | /// | -8.52 [-20.16] | -3,577 | g1,g2,g3,g4,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI34_5m_TS_K60 | 660 | 3.6 | 340 | -1,399 [-4,989] | -3,270 | -3,858 | -1.92 (7.03) | 0.50/0.52 | 0.60/0.00/0.45/0.53 | -0.37 [-10.12] | -3,190 | g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI34_t500_TZ_K60 | 778 | 3.8 | -2,647 | -2,731 [-6,134] | -2,782 | 8,850 | -3.57 (6.85) | 0.49/0.52 | /// | -3.73 [-13.33] | -4,516 | g2,g3,g4,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI34_t500_TS_K60 | 1589 | 8.0 | -9,513 | -6,658 [-11,831] | -3,459 | -1,837 | -4.17 (4.73) | 0.48/0.51 | /// | -3.65 [-10.93] | -10,404 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI43_1m_TZ_K60 | 858 | 4.0 | -1,507 | -1,947 [-5,212] | -2,396 | 12,905 | -2.46 (6.74) | 0.49/0.52 | /// | -1.94 [-10.64] | -3,778 | g2,g3,g4,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI43_1m_TS_K60 | 1969 | 9.8 | -5,997 | -6,631 [-13,156] | -7,224 | -3 | -3.39 (4.27) | 0.48/0.51 | /// | -3.20 [-9.11] | -11,855 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI43_5m_TZ_K60 | 673 | 3.1 | -1,854 | -3,368 [-6,486] | -4,964 | 4,669 | -5.37 (7.55) | 0.46/0.51 | /// | -7.34 [-18.57] | -4,799 | g2,g3,g4,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI43_5m_TS_K60 | 945 | 5.2 | -3,464 | -1,296 [-5,608] | 1,079 | -3,427 | -1.26 (5.90) | 0.50/0.51 | /// | 1.29 [-6.27] | -3,843 | g2,g3,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI43_t500_TZ_K60 | 1075 | 5.2 | -5,977 | -7,144 [-11,367] | -8,309 | 13,527 | -6.81 (5.82) | 0.45/0.51 | /// | -9.84 [-17.63] | -9,480 | g2,g3,g4,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI43_t500_TS_K60 | 1995 | 9.6 | -3,590 | -5,709 [-11,292] | -7,929 | 1,292 | -2.96 (4.28) | 0.48/0.51 | /// | -0.86 [-7.40] | -10,247 | g2,g3,g4,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI44_1m_TZ_K60 | 359 | 1.5 | -560 | -635 [-2,835] | -708 | 5,574 | -2.15 (11.02) | 0.49/0.51 | /// | -0.92 [-16.32] | -1,281 | g1,g2,g3,g4,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI44_1m_TS_K60 | 1020 | 5.2 | -2,031 | -2,290 [-6,452] | -2,538 | -3,068 | -2.19 (5.85) | 0.49/0.51 | /// | -0.59 [-8.99] | -4,768 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI44_5m_TZ_K60 | 277 | 1.3 | -669 | -1,209 [-3,429] | -1,780 | 1,807 | -4.83 (12.03) | 0.47/0.52 | /// | -5.88 [-21.76] | -1,783 | g1,g2,g3,g4,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI44_5m_TS_K60 | 416 | 2.3 | -307 | -338 [-3,249] | -366 | -3,140 | -0.74 (8.88) | 0.51/0.51 | /// | 2.51 [-11.57] | -1,458 | g1,g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI44_t500_TZ_K60 | 494 | 2.3 | -2,720 | -2,937 [-6,181] | -3,130 | 7,612 | -6.38 (8.82) | 0.46/0.52 | /// | -9.11 [-20.49] | -3,960 | g1,g2,g3,g4,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI44_t500_TS_K60 | 1200 | 6.1 | -4,559 | -5,039 [-9,103] | -5,487 | 1,454 | -4.13 (5.40) | 0.48/0.51 | /// | -3.58 [-11.65] | -7,985 | g2,g3,g4,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_1m_N_K60 | 13580 | 23.0 | -6,397 | -8,300 [-17,199] | -10,248 | 279 | -1.81 (2.77) | 0.49/0.50 | /// | -1.08 [-5.74] | -20,376 | g2,g3,g4,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_3m_N_K60 | 12258 | 24.9 | -6,374 | -4,548 [-14,102] | -2,498 | -6,118 | -0.91 (2.66) | 0.50/0.50 | /// | 0.72 [-3.43] | -18,632 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_5m_N_K60 | 11196 | 24.2 | -9,216 | -5,470 [-14,334] | -1,319 | -4,869 | -1.13 (2.69) | 0.49/0.50 | /// | 2.66 [-1.83] | -15,994 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_t500_N_K60 | 13781 | 25.3 | -7,550 | -6,548 [-14,979] | -5,364 | -3,675 | -1.29 (2.64) | 0.49/0.50 | /// | 1.39 [-2.84] | -21,039 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_t1000_N_K60 | 13212 | 24.8 | -11,203 | -13,735 [-23,558] | -16,288 | -11,010 | -2.77 (2.67) | 0.48/0.50 | /// | -3.74 [-8.30] | -24,824 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_1m_N_KS | 37604 | 114.0 | -18,478 | -30,723 [-38,259] | -43,588 | -25,339 | -1.35 (0.57) | 0.33/0.36 | /// | -0.29 [-0.93] | -67,077 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_5m_N_KS | 15662 | 53.6 | -3,576 | -2,775 [-11,859] | -1,864 | -4,197 | -0.26 (1.25) | 0.34/0.34 | /// | 1.33 [-0.17] | -23,435 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI33_t500_N_KS | 38190 | 76.6 | -12,073 | -12,855 [-21,103] | -13,520 | -17,828 | -0.84 (0.85) | 0.33/0.35 | /// | 0.74 [-0.33] | -39,921 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI44_1m_T_K60 | 7452 | 23.1 | -2,997 | -1,626 [-10,870] | -112 | -6,397 | -0.35 (2.75) | 0.50/0.51 | /// | 2.89 [-2.04] | -13,514 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI44_1m_T_KS | 13129 | 55.7 | -14,324 | -20,188 [-26,334] | -26,269 | -11,009 | -1.81 (0.94) | 0.33/0.36 | /// | -0.30 [-1.18] | -37,745 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI44_5m_T_K60 | 5150 | 19.7 | -332 | -5,395 [-14,491] | -10,820 | 1,499 | -1.37 (2.99) | 0.49/0.51 | /// | 1.46 [-3.86] | -14,380 | g2,g3,g4,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_SI44_5m_T_KS | 5292 | 26.4 | -10,880 | -6,839 [-13,111] | -2,347 | -7,143 | -1.29 (1.86) | 0.34/0.36 | /// | 0.96 [-0.84] | -16,376 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAfade_1m_N_K60 | 5738 | 20.5 | -4,686 | -8,667 [-16,999] | -12,870 | -8,213 | -2.11 (2.92) | 0.49/0.50 | /// | 1.59 [-2.93] | -19,171 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAfade_1m_N_KS | 15464 | 74.1 | -22,871 | -23,991 [-27,031] | -24,862 | -28,069 | -1.62 (0.26) | 0.32/0.40 | /// | -0.89 [-1.74] | -49,967 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAfade_3m_N_K60 | 3277 | 14.4 | -6,843 | -5,885 [-12,724] | -4,760 | -17,955 | -2.04 (3.50) | 0.49/0.51 | /// | -0.23 [-5.52] | -12,762 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAfade_3m_N_KS | 6246 | 28.3 | -10,180 | -9,428 [-11,047] | -8,473 | -11,257 | -1.66 (0.43) | 0.32/0.39 | /// | -0.28 [-2.15] | -19,215 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAfade_5m_N_K60 | 2334 | 10.6 | -3,769 | -4,602 [-10,787] | -5,441 | -10,528 | -2.17 (4.09) | 0.50/0.52 | /// | 0.62 [-5.38] | -9,504 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAfade_5m_N_KS | 3781 | 16.7 | -5,191 | -5,138 [-6,400] | -5,006 | -6,572 | -1.54 (0.56) | 0.32/0.39 | /// | 0.97 [-1.44] | -10,879 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAfade_t500_N_K60 | 5057 | 18.6 | -6,238 | -8,759 [-16,455] | -11,373 | -13,348 | -2.35 (3.07) | 0.48/0.50 | /// | -0.32 [-5.44] | -17,577 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAfade_t500_N_KS | 12109 | 55.6 | -16,830 | -17,983 [-20,536] | -18,976 | -20,339 | -1.62 (0.31) | 0.32/0.39 | /// | -0.03 [-1.21] | -36,833 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAfade_t1000_N_K60 | 3521 | 14.8 | -4,191 | -6,098 [-13,251] | -8,082 | -6,502 | -2.07 (3.47) | 0.49/0.51 | /// | -0.04 [-5.57] | -13,893 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAfade_t1000_N_KS | 6712 | 30.1 | -9,099 | -9,561 [-11,457] | -9,924 | -14,094 | -1.59 (0.42) | 0.32/0.39 | /// | 0.84 [-0.97] | -19,820 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAcont_1m_N_K60 | 5737 | 20.5 | -6,365 | -10,076 [-17,367] | -13,963 | -2,899 | -2.46 (2.94) | 0.48/0.51 | /// | -1.59 [-6.10] | -21,931 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAcont_1m_N_KS | 11243 | 50.4 | -2,247 | -7,445 [-14,387] | -12,988 | -4,082 | -0.74 (1.01) | 0.34/0.35 | /// | 0.89 [0.06] | -25,640 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g14N |  |
| FP_UAcont_3m_N_K60 | 3275 | 14.4 | -3,540 | -4,681 [-11,773] | -5,854 | 10,193 | -1.63 (3.51) | 0.49/0.51 | /// | 0.23 [-5.07] | -12,119 | g2,g3,g4,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAcont_3m_N_KS | 4103 | 18.3 | -2,171 | -5,242 [-10,695] | -8,504 | -9,414 | -1.43 (2.17) | 0.34/0.36 | /// | 0.28 [-1.32] | -11,720 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAcont_5m_N_K60 | 2334 | 10.6 | -5,777 | -5,112 [-11,147] | -4,315 | 6,734 | -2.40 (4.09) | 0.49/0.51 | /// | -0.62 [-6.32] | -10,321 | g2,g3,g4,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAcont_5m_N_KS | 2370 | 10.1 | -7,799 | -5,165 [-9,200] | -2,227 | -8,373 | -2.56 (3.13) | 0.33/0.37 | /// | -0.97 [-3.39] | -8,757 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAcont_t500_N_K60 | 5051 | 18.8 | -4,065 | -5,649 [-13,254] | -7,289 | 5,522 | -1.50 (3.06) | 0.49/0.51 | /// | 0.32 [-4.29] | -15,940 | g2,g3,g4,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAcont_t500_N_KS | 8684 | 34.4 | -9,912 | -11,269 [-17,915] | -12,581 | -10,471 | -1.64 (1.44) | 0.33/0.36 | /// | 0.03 [-1.12] | -23,537 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAcont_t1000_N_K60 | 3518 | 14.8 | -2,534 | -6,022 [-12,607] | -9,726 | -2,810 | -2.04 (3.47) | 0.49/0.51 | /// | 0.04 [-4.86] | -13,613 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAcont_t1000_N_KS | 4340 | 17.8 | -7,902 | -8,485 [-13,861] | -8,996 | -3,449 | -2.39 (2.56) | 0.33/0.35 | /// | -0.84 [-2.83] | -13,474 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAfinfade_1m_N_K60 | 11710 | 24.1 | -9,584 | -18,802 [-26,488] | -28,550 | -14,046 | -3.90 (2.71) | 0.47/0.50 | /// |  [] | -29,792 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAfinfade_3m_N_K60 | 8850 | 22.3 | -22,029 | -24,954 [-32,962] | -27,770 | 2,764 | -5.59 (2.81) | 0.46/0.51 | /// |  [] | -36,041 | g2,g3,g4,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAfinfade_5m_N_K60 | 7369 | 21.8 | -16,960 | -20,823 [-28,398] | -24,721 | 553 | -4.78 (2.84) | 0.47/0.51 | /// |  [] | -30,369 | g2,g3,g4,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAfinfade_t500_N_K60 | 11200 | 23.9 | -10,267 | -11,617 [-20,135] | -12,916 | -11,486 | -2.43 (2.72) | 0.48/0.51 | /// |  [] | -24,276 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAfinfade_t1000_N_K60 | 9254 | 23.8 | -8,518 | -14,991 [-24,034] | -21,809 | -4,329 | -3.15 (2.73) | 0.48/0.51 | /// |  [] | -27,538 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAfade_1m_Z_K60 | 2037 | 9.3 | -483 | -3,718 [-10,036] | -7,181 | -2,121 | -1.99 (4.33) | 0.50/0.52 | /// |  [] | -8,007 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAfade_5m_Z_K60 | 1058 | 4.6 | 5,640 | 467 [-3,642] | -5,162 | -5,878 | +0.51 (6.23) | 0.52/0.52 | 0.85/1.00/1.00/0.88 |  [] | -1,609 | g3,g4,g5,g6a,g9d,g10x2,g11yr,g12nb,g13mir | Y |
| FP_UAcont_1m_T_K60 | 4040 | 16.9 | -7,960 | -4,193 [-11,945] | -39 | -1,752 | -1.24 (3.23) | 0.50/0.51 | /// |  [] | -12,479 | g2,g3,g4,g5,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_UAcont_5m_T_K60 | 1865 | 8.6 | -6,026 | -3,213 [-9,026] | -109 | 4,490 | -1.87 (4.55) | 0.49/0.51 | /// |  [] | -7,415 | g2,g3,g4,g6a,g7b,g8c,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvs_bar_1m_N_K60 | 9095 | 24.0 | -8,237 | -17,443 [-25,746] | -27,196 | 3,509 | -3.64 (2.71) | 0.47/0.50 | /// | -5.09 [-9.22] | -29,138 | g2,g3,g4,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvs_bar_3m_N_K60 | 6169 | 21.7 | -6,677 | -13,341 [-22,069] | -20,391 | 589 | -3.08 (2.85) | 0.48/0.51 | /// | -2.05 [-6.44] | -25,055 | g2,g3,g4,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvs_bar_5m_N_K60 | 4732 | 19.1 | -11,398 | -14,015 [-22,517] | -16,656 | -3,565 | -3.66 (3.03) | 0.48/0.51 | /// | -4.59 [-8.75] | -23,616 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvs_bar_t500_N_K60 | 8836 | 23.7 | -16,643 | -13,188 [-21,299] | -9,241 | -8,843 | -2.78 (2.72) | 0.48/0.51 | /// | -0.17 [-4.72] | -24,182 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvs_bar_t1000_N_K60 | 6393 | 20.7 | -15,376 | -15,370 [-22,700] | -15,140 | -10,069 | -3.72 (2.91) | 0.47/0.51 | /// | -3.96 [-8.74] | -27,425 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvs_cd_1m_N_K60 | 6706 | 21.7 | -3,876 | -8,003 [-16,574] | -12,373 | -3,306 | -1.84 (2.84) | 0.49/0.51 | /// | 0.72 [-3.83] | -18,204 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvs_cd_3m_N_K60 | 4088 | 17.5 | -2,885 | -7,924 [-15,852] | -13,285 | -16,682 | -2.26 (3.18) | 0.49/0.51 | /// | -1.52 [-6.74] | -17,168 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvs_cd_5m_N_K60 | 2998 | 13.9 | -2,358 | -5,310 [-12,642] | -8,442 | -4,749 | -1.91 (3.56) | 0.49/0.51 | /// | -0.22 [-5.79] | -12,396 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvs_cd_t500_N_K60 | 5804 | 20.1 | -8,567 | -9,908 [-18,258] | -11,223 | -2,134 | -2.46 (2.96) | 0.49/0.51 | /// | -1.89 [-6.55] | -21,326 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvs_cd_t1000_N_K60 | 3740 | 15.6 | -2,949 | -8,057 [-14,464] | -13,491 | 702 | -2.59 (3.36) | 0.49/0.51 | /// | -0.98 [-6.38] | -15,762 | g2,g3,g4,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvx60_bar_1m_N_K60 | 9914 | 22.8 | -11,439 | -19,506 [-28,139] | -27,992 | -5,445 | -4.28 (2.78) | 0.47/0.50 | /// | -3.35 [-7.93] | -29,697 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvx60_bar_3m_N_K60 | 6446 | 21.3 | -5,013 | -14,815 [-23,081] | -25,253 | -1,419 | -3.47 (2.88) | 0.48/0.51 | /// | -2.22 [-6.62] | -25,060 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvx60_bar_5m_N_K60 | 5032 | 19.1 | -7,628 | -13,965 [-21,915] | -20,651 | -9,570 | -3.66 (3.06) | 0.48/0.51 | /// | -4.13 [-8.49] | -23,926 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvx60_bar_t500_N_K60 | 8364 | 21.6 | -10,347 | -12,642 [-20,299] | -14,954 | -8,177 | -2.92 (2.85) | 0.48/0.51 | /// | -4.49 [-9.18] | -22,928 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvx60_bar_t1000_N_K60 | 5565 | 18.3 | -10,207 | -9,613 [-17,522] | -8,828 | -6,389 | -2.63 (3.10) | 0.48/0.51 | /// | -2.55 [-7.91] | -18,617 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvx60_cd_1m_N_K60 | 8682 | 22.7 | -6,538 | -13,905 [-22,699] | -21,711 | -9,745 | -3.06 (2.78) | 0.48/0.51 | /// | -2.17 [-6.55] | -25,285 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvx60_cd_3m_N_K60 | 5398 | 19.4 | -4,235 | -10,780 [-18,913] | -17,739 | -4,531 | -2.77 (3.02) | 0.48/0.51 | /// | -2.47 [-7.33] | -20,210 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvx60_cd_5m_N_K60 | 4078 | 16.6 | -1,471 | -7,892 [-15,493] | -14,757 | -10,829 | -2.38 (3.27) | 0.49/0.51 | /// | -1.13 [-5.98] | -15,656 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvx60_cd_t500_N_K60 | 7571 | 21.2 | -11,920 | -15,494 [-24,730] | -19,154 | -15,074 | -3.65 (2.88) | 0.48/0.51 | /// | -4.50 [-9.21] | -25,253 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvx60_cd_t1000_N_K60 | 4992 | 17.1 | -13,948 | -8,745 [-16,174] | -2,964 | -6,182 | -2.55 (3.20) | 0.48/0.51 | /// | -2.50 [-7.55] | -20,263 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvs_bar_1m_N_KS | 30904 | 136.0 | -25,888 | -34,375 [-42,026] | -43,102 | -28,952 | -1.26 (0.38) | 0.33/0.37 | /// | 0.22 [-0.22] | -75,141 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvs_bar_3m_N_KS | 12023 | 58.1 | -4,372 | -11,054 [-17,760] | -18,156 | -14,612 | -0.95 (0.83) | 0.34/0.36 | /// | 0.33 [-0.48] | -33,440 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvs_bar_5m_N_KS | 7414 | 36.9 | -4,394 | -5,666 [-12,205] | -6,966 | -6,387 | -0.77 (1.19) | 0.34/0.35 | /// | 0.61 [-0.62] | -19,502 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvs_bar_t500_N_KS | 19483 | 70.5 | -15,663 | -16,485 [-22,955] | -17,140 | -21,447 | -1.17 (0.76) | 0.34/0.36 | /// | 0.37 [-0.34] | -41,311 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvs_bar_t1000_N_KS | 9600 | 39.9 | -9,555 | -13,899 [-20,811] | -18,419 | -11,006 | -1.74 (1.28) | 0.33/0.36 | /// | -0.74 [-2.07] | -27,214 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvx60_bar_1m_N_KS | 44476 | 192.2 | -43,227 | -54,975 [-60,707] | -66,948 | -27,635 | -1.43 (0.24) | 0.33/0.39 | /// | -0.41 [-1.10] | -98,838 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvx60_bar_3m_N_KS | 18199 | 86.2 | -21,280 | -26,516 [-32,539] | -31,824 | -11,389 | -1.54 (0.51) | 0.33/0.37 | /// | -0.65 [-2.03] | -55,421 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvx60_bar_5m_N_KS | 11472 | 54.9 | -13,903 | -16,117 [-22,139] | -18,290 | -12,772 | -1.47 (0.77) | 0.33/0.37 | /// | -1.45 [-3.34] | -34,253 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvx60_bar_t500_N_KS | 29765 | 130.5 | -22,784 | -28,430 [-33,870] | -34,154 | -28,256 | -1.09 (0.30) | 0.34/0.38 | /// | 0.72 [-0.21] | -68,747 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_DDdvx60_bar_t1000_N_KS | 16171 | 74.9 | -16,083 | -22,559 [-27,415] | -29,271 | -18,777 | -1.51 (0.47) | 0.34/0.38 | /// | -0.18 [-1.90] | -47,771 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_ABloose_1m_N_K60 | 2269 | 11.4 | -5,131 | -4,276 [-11,395] | -3,285 | -364 | -1.87 (3.97) | 0.50/0.51 | /// | -0.36 [-6.06] | -10,168 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_ABloose_1m_N_KS | 3636 | 20.4 | -1,243 | -3,295 [-6,480] | -5,478 | -3,100 | -0.81 (1.10) | 0.35/0.37 | /// | 0.48 [-0.54] | -11,275 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_ABloose_3m_N_K60 | 1148 | 6.3 | 559 | -1,857 [-6,430] | -4,456 | -831 | -1.46 (5.27) | 0.50/0.51 | 0.57/0.35//0.62 | 2.41 [-5.15] | -5,008 | g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_ABloose_3m_N_KS | 1433 | 8.0 | 15 | -2,135 [-4,846] | -4,440 | -358 | -1.33 (2.73) | 0.34/0.37 | 0.53/0.45//0.72 | 0.00 [-2.19] | -5,244 | g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_ABloose_5m_N_K60 | 592 | 3.5 | -305 | -430 [-3,928] | -559 | 2,169 | -0.61 (6.81) | 0.51/0.51 | /// | 1.91 [-6.98] | -2,257 | g2,g3,g4,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_ABloose_5m_N_KS | 617 | 3.7 | -388 | -1,389 [-3,976] | -2,456 | 1,351 | -1.87 (5.08) | 0.34/0.36 | /// | -1.41 [-5.52] | -3,019 | g2,g3,g4,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_ABloose_t500_N_K60 | 279 | 1.6 | -1,159 | 533 [-1,781] | 2,366 | 2,057 | +1.70 (10.72) | 0.53/0.51 | /// | 9.04 [-7.31] | -418 | g1,g2,g3,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_ABloose_t500_N_KS | 318 | 1.8 | -313 | -791 [-1,891] | -1,299 | -888 | -2.20 (5.28) | 0.32/0.36 | /// | -0.62 [-4.61] | -1,488 | g1,g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_ABloose_t1000_N_K60 | 57 | | | | | | | | | | | too few trades/events (<100) | |
| FP_ABloose_t1000_N_KS | 57 | | | | | | | | | | | too few trades/events (<100) | |
| FP_CZA2_1m_N_K60 | 600 | 2.4 | -2,159 | -2,292 [-5,209] | -2,403 | -5,443 | -4.75 (8.75) | 0.47/0.51 | /// | -6.26 [-18.40] | -3,275 | g1,g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CZA2_1m_N_KS | 1543 | 5.5 | -2,503 | -1,782 [-2,602] | -973 | -4,207 | -1.62 (0.99) | 0.31/0.38 | /// | -0.86 [-2.26] | -3,461 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CZA3_1m_N_K60 | 338 | 1.2 | -3,032 | -836 [-2,922] | 1,562 | -57 | -3.54 (12.49) | 0.49/0.52 | /// | -4.23 [-22.68] | -1,306 | g1,g2,g3,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CZA3_1m_N_KS | 635 | 2.1 | -626 | -383 [-867] | -115 | 54 | -0.93 (1.68) | 0.34/0.38 | /// | -0.80 [-3.11] | -995 | g1,g2,g3,g4,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CZB2_1m_N_K60 | 124 | 0.4 | 790 | 317 [-1,067] | -202 | -1,946 | +4.36 (22.48) | 0.54/0.50 | 0.97/0.53//0.75 | 11.03 [-19.38] | 195 | g1,g3,g4,g5,g7b,g9d,g11yr,g13mir,g14N |  |
| FP_CZB2_1m_N_KS | 173 | 0.4 | 396 | 248 [54] | 82 | -1,071 | +2.77 (3.91) | 0.50/0.37 | 1.00/1.00//1.00 | 5.25 [0.63] | 94 | g1,g5,g11yr,g14N | Y |
| FP_CZB3_1m_N_K60 | 44 | | | | | | | | | | | too few trades/events (<100) | |
| FP_CZB3_1m_N_KS | 50 | | | | | | | | | | | too few trades/events (<100) | |
| FP_IRini_1m_N_K60 | 402 | 2.1 | 1,455 | -1,845 [-4,591] | -5,405 | -3,453 | -4.44 (9.40) | 0.47/0.51 | 0.33/0.00//0.23 | -5.10 [-17.29] | -2,777 | g1,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_IRini_t500_N_K60 | 402 | 2.1 | 1,607 | -1,001 [-3,507] | -3,821 | -2,915 | -2.40 (9.34) | 0.50/0.52 | 0.45/0.00//0.55 | -1.01 [-13.65] | -1,974 | g1,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_IRresp_1m_N_K60 | 259 | 1.4 | 129 | 490 [-1,728] | 874 | 1,201 | +1.78 (11.37) | 0.53/0.51 | 0.75/1.00//0.85 | 7.57 [-7.14] | -226 | g1,g3,g6a,g9d,g10x2,g11yr,g13mir,g14N |  |
| FP_IRresp_t500_N_K60 | 260 | 1.4 | -1,099 | 187 [-1,986] | 1,583 | 989 | +0.68 (11.38) | 0.52/0.52 | /// | 5.39 [-10.86] | -527 | g1,g2,g3,g6a,g7b,g9d,g10x2,g11yr,g13mir,g14N |  |
| FP_IRini_1m_N_KS | 388 | 2.0 | 1,343 | 79 [-1,505] | -1,296 | 917 | +0.20 (5.54) | 0.36/0.36 | 0.80/0.75//0.82 | 2.34 [-2.74] | -680 | g1,g3,g4,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_IRini_t500_N_KS | 400 | 2.1 | -1,335 | -1,895 [-3,153] | -2,476 | -559 | -4.58 (4.27) | 0.25/0.34 | /// | -5.77 [-9.80] | -2,552 | g1,g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_IRresp_1m_N_KS | 252 | 1.3 | -597 | 229 [-982] | 1,124 | 38 | +0.86 (6.22) | 0.36/0.34 | /// | 4.16 [-2.14] | -324 | g1,g2,g3,g6a,g7b,g9d,g10x2,g11yr,g13mir,g14N |  |
| FP_IRresp_t500_N_KS | 257 | 1.4 | -596 | 214 [-939] | 1,091 | 138 | +0.79 (5.54) | 0.36/0.34 | /// | 2.50 [-3.32] | -346 | g1,g2,g3,g6a,g7b,g9d,g10x2,g11yr,g13mir,g14N |  |
| FP_CDall_1m_N_K60 | 11190 | 24.0 | -3,802 | 607 [-8,240] | 5,391 | -7,370 | +0.13 (2.70) | 0.50/0.50 | /// | 4.46 [-0.42] | -11,870 | g2,g3,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CDall_1m_N_KS | 37308 | 132.9 | -28,070 | -32,554 [-40,330] | -36,956 | -19,487 | -1.22 (0.47) | 0.34/0.37 | /// | 0.19 [-0.33] | -67,320 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CDall_3m_N_K60 | 8463 | 24.2 | -4,775 | -1,857 [-11,012] | 1,342 | -3,589 | -0.38 (2.69) | 0.50/0.51 | /// | 4.87 [0.29] | -12,376 | g2,g3,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g14N |  |
| FP_CDall_3m_N_KS | 15910 | 63.5 | -11,524 | -13,188 [-21,748] | -14,806 | -17,948 | -1.04 (0.98) | 0.34/0.36 | /// | 0.30 [-0.62] | -36,176 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CDall_5m_N_K60 | 6934 | 22.3 | -2,106 | -3,132 [-11,726] | -4,202 | -3,148 | -0.70 (2.80) | 0.50/0.50 | /// | 4.01 [-0.61] | -15,552 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CDall_5m_N_KS | 10323 | 44.9 | -3,637 | 2,756 [-4,445] | 9,664 | -17,676 | +0.31 (1.36) | 0.35/0.35 | /// | 2.65 [1.37] | -14,617 | g2,g3,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g14N |  |
| FP_CDall_t500_N_K60 | 10921 | 24.8 | -11,717 | -7,345 [-15,675] | -2,487 | 3,429 | -1.48 (2.66) | 0.49/0.50 | /// | 3.84 [-0.51] | -18,871 | g2,g3,g4,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CDall_t500_N_KS | 24021 | 64.4 | -4,595 | -6,992 [-15,052] | -9,496 | -24,445 | -0.54 (1.00) | 0.34/0.35 | /// | 1.27 [0.40] | -31,483 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g14N |  |
| FP_CDall_t1000_N_K60 | 8880 | 23.0 | -6,629 | -8,122 [-16,622] | -9,627 | -5,769 | -1.76 (2.75) | 0.49/0.50 | /// | 2.21 [-2.37] | -20,856 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CDall_t1000_N_KS | 12807 | 38.3 | -1,668 | -6,490 [-14,865] | -11,638 | -1,825 | -0.85 (1.67) | 0.34/0.35 | /// | 0.51 [-0.87] | -20,558 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CDwithp_1m_N_K60 | 7290 | 23.2 | 648 | -1,648 [-9,885] | -4,120 | -8,215 | -0.36 (2.75) | 0.50/0.51 | 0.95/0.05//1.00 | 4.36 [-0.33] | -13,205 | g3,g4,g5,g7b,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CDwithp_3m_N_K60 | 4203 | 17.6 | -10,774 | -5,472 [-13,395] | 371 | -6,934 | -1.56 (3.17) | 0.50/0.51 | /// | 1.41 [-3.93] | -14,847 | g2,g3,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CDwithp_5m_N_K60 | 3117 | 14.4 | -6,265 | -2,849 [-9,860] | 905 | -8,976 | -0.99 (3.51) | 0.50/0.51 | /// | 1.12 [-3.84] | -10,585 | g2,g3,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CDwithp_t500_N_K60 | 6179 | 20.8 | -711 | -8,194 [-14,977] | -16,209 | -2,481 | -1.97 (2.91) | 0.49/0.50 | /// | 0.53 [-3.89] | -18,554 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CDwithp_t1000_N_K60 | 4021 | 16.7 | -3,654 | -7,420 [-14,486] | -11,406 | -3,067 | -2.23 (3.26) | 0.49/0.51 | /// | 0.40 [-4.46] | -14,346 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CDnop_1m_N_K60 | 10330 | 24.3 | -7,751 | -10,509 [-20,005] | -13,355 | -446 | -2.16 (2.69) | 0.48/0.50 | /// | 0.43 [-4.10] | -21,491 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CDnop_3m_N_K60 | 7509 | 23.5 | -7,946 | -3,414 [-11,221] | 1,561 | -1,975 | -0.73 (2.73) | 0.50/0.50 | /// | 3.31 [-1.41] | -13,822 | g2,g3,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CDnop_5m_N_K60 | 6038 | 21.5 | 4,484 | 773 [-7,604] | -3,273 | 1,042 | +0.18 (2.86) | 0.50/0.50 | 0.97/0.30//1.00 | 6.47 [1.75] | -12,115 | g3,g4,g7b,g10x2,g11yr,g12nb,g14N |  |
| FP_CDnop_t500_N_K60 | 10301 | 24.8 | -9,308 | -6,006 [-14,148] | -2,330 | -8,032 | -1.21 (2.66) | 0.49/0.50 | /// | 3.29 [-0.84] | -18,331 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CDnop_t1000_N_K60 | 8106 | 22.2 | -5,433 | -12,078 [-19,949] | -19,126 | -71 | -2.73 (2.80) | 0.48/0.50 | /// | -0.01 [-4.69] | -23,032 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CDpbos_1m_N_K60 | 10601 | 25.4 | -2,454 | -2,364 [-11,033] | -2,232 | -15,047 | -0.47 (2.63) | 0.50/0.50 | /// | 3.83 [-0.15] | -12,899 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CDpbos_3m_N_K60 | 7809 | 23.9 | 1,566 | -2,228 [-11,014] | -6,320 | -3,170 | -0.47 (2.72) | 0.50/0.51 | 0.90/0.00//0.93 | 1.57 [-2.69] | -15,021 | g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CDpbos_5m_N_K60 | 6379 | 22.3 | -789 | -5,030 [-11,949] | -9,566 | -9,625 | -1.13 (2.82) | 0.49/0.50 | /// | 2.57 [-1.77] | -15,670 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CDpbos_t500_N_K60 | 10255 | 25.2 | -3,205 | -7,826 [-17,297] | -12,735 | 5,842 | -1.55 (2.65) | 0.49/0.51 | /// | 1.09 [-3.18] | -17,304 | g2,g3,g4,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CDpbos_t1000_N_K60 | 7947 | 22.9 | -1,504 | -1,945 [-9,897] | -2,395 | -5,035 | -0.43 (2.77) | 0.50/0.50 | /// | 4.27 [-0.32] | -15,767 | g2,g3,g4,g5,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CZA2_30s_N_K60 | 1439 | 6.9 | -2,514 | -1,660 [-6,507] | -709 | 210 | -1.20 (5.16) | 0.51/0.52 | /// | 1.50 [-5.98] | -4,874 | g2,g3,g4,g6a,g7b,g9d,g10x2,g11yr,g12nb,g13mir,g14N |  |
| FP_CZA2_t250_N_K60 | 75 | | | | | | | | | | | too few trades/events (<100) | |
| FP_CZB2_30s_N_K60 | 506 | 1.7 | -540 | 823 [-1,203] | 2,293 | 1,572 | +2.41 (10.37) | 0.53/0.51 | /// | 7.83 [-6.89] | 79 | g1,g2,g3,g6a,g7b,g9d,g11yr,g12nb,g13mir,g14N |  |
| FP_CZB2_t250_N_K60 | 0 | | | | | | | | | | | too few trades/events (<100) | |

## Appendix B. Confirmation cells (all 192; lift = mean(kept) - mean(all) pts/trade; CI = label-day-block bootstrap; weekly $ = kept book minus base book at 10 lots)

| cell | take | kept | lift PRE | lift WF [CI] (MDE) | HOLD | 2023 | mirror lift | plc | wk $ d | maxDD d | failed |
|--|--|--|--|--|--|--|--|--|--|--|--|
| CF_ST_SI33_1m_k5 | 0.558 | 3940 | -0.78 | -0.49 [-1.77, 0.69] (1.72) | -0.28 | 1.74 | 0.61 | 0.196 | -5,538 | 52,151 | mean,hold,plc90,CI,x2,yr,eqrisk,N |
| CF_ST_SI33_1m_k15 | 0.744 | 5283 | -0.91 | -0.68 [-1.47, 0.05] (1.09) | -0.51 | -0.21 | 1.97 | 0.056 | -4,639 | 73,423 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_ST_SI33_5m_k5 | 0.190 | 1389 | -2.14 | -0.37 [-3.01, 2.17] (3.73) | 0.74 | 5.77 | 0.09 | 0.365 | -12,250 | 90,396 | mean,plc90,CI,x2,yr,eqrisk,N |
| CF_ST_SI33_5m_k15 | 0.447 | 3271 | -1.16 | -0.08 [-1.43, 1.24] (1.93) | 0.66 | 5.04 | 0.07 | 0.433 | -10,262 | 124,730 | mean,plc90,CI,x2,yr,eqrisk,N |
| CF_ST_SI33_t500_k5 | 0.547 | 3878 | -0.55 | -0.85 [-2.00, 0.36] (1.69) | -1.09 | -0.75 | 1.02 | 0.092 | -12,001 | 437,242 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_ST_SI33_t500_k15 | 0.705 | 5052 | -1.17 | -0.50 [-1.34, 0.33] (1.22) | -0.00 | -0.80 | 1.23 | 0.140 | -7,298 | 39,667 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_ST_SI44_1m_k5 | 0.206 | 1440 | 1.95 | +2.11 [-0.44, 4.70] (3.64) | 2.22 | 6.59 | -0.54 | 0.939 | -7,314 | -98,593 | nb,CI,yr,plc95,eqrisk,N |
| CF_ST_SI44_1m_k15 | 0.367 | 2584 | 0.14 | -0.07 [-1.84, 1.66] (2.49) | -0.24 | 1.82 | 0.04 | 0.459 | -10,981 | 110,626 | mean,hold,plc90,nb,CI,yr,eqrisk,N |
| CF_ST_SI44_5m_k5 | 0.061 | 441 | 4.31 | +3.13 [-2.00, 7.88] (7.00) | 2.28 | 3.11 | -0.21 | 0.875 | -11,762 | -101,384 | plc90,CI,yr,eqrisk,N |
| CF_ST_SI44_5m_k15 | 0.170 | 1220 | -0.41 | +0.16 [-2.80, 3.09] (4.21) | 0.56 | 0.49 | -0.03 | 0.531 | -11,242 | 78,877 | plc90,nb,CI,x2,yr,eqrisk,N |
| CF_ST_SI44_t500_k5 | 0.248 | 1714 | 2.79 | +1.59 [-0.81, 3.85] (3.32) | 0.64 | 1.30 | -0.51 | 0.887 | -8,147 | -94,293 | plc90,CI,yr,eqrisk,N |
| CF_ST_SI44_t500_k15 | 0.423 | 2966 | 1.70 | +0.79 [-0.62, 2.26] (2.08) | 0.06 | 0.37 | -0.57 | 0.825 | -7,142 | -16,806 | plc90,CI,yr,eqrisk,N |
| CF_ST_DD_1m_k5 | 0.048 | 363 | 1.69 | -2.58 [-7.88, 3.14] (8.00) | -4.96 | -10.29 | 0.14 | 0.195 | -15,044 | 88,708 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_ST_DD_1m_k15 | 0.120 | 891 | 2.06 | -1.10 [-4.45, 2.52] (4.97) | -3.09 | -8.46 | 0.16 | 0.254 | -14,780 | 279,024 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_ST_DD_5m_k5 | 0.001 | 11 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_ST_DD_5m_k15 | 0.008 | 59 | -14.68 | -2.89 [-19.35, 12.62] (22.60) | 5.77 | -1.17 | 0.02 | 0.329 | -14,564 | -159,680 | mean,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_ST_DD_t500_k5 | 0.082 | 586 | 2.72 | -1.03 [-5.19, 3.52] (6.19) | -3.92 | -3.22 | 0.09 | 0.314 | -13,912 | 51,999 | mean,hold,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_ST_DD_t500_k15 | 0.155 | 1097 | -0.19 | +0.89 [-2.29, 4.06] (4.56) | 1.79 | -3.03 | -0.16 | 0.696 | -9,979 | -20,870 | plc90,nb,CI,yr,span2,eqrisk,N |
| CF_HM_AB13_1m_k5 | 0.012 | 66 | 6.18 | +14.44 [0.90, 27.03] (18.84) | 19.77 | -24.28 | -0.18 | 0.980 | -8,242 | -204,163 | yr,span2,N |
| CF_HM_AB13_1m_k15 | 0.025 | 142 | 4.93 | +7.39 [-2.16, 16.22] (13.27) | 8.53 | -5.86 | -0.20 | 0.941 | -7,864 | -154,046 | nb,CI,yr,plc95,span2,eqrisk,N |
| CF_HM_AB13_3m_k5 | 0.008 | 48 | 7.43 | +1.63 [-14.60, 16.94] (23.26) | -3.25 | 53.55 | -0.02 | 0.584 | -9,522 | -193,071 | hold,plc90,nb,CI,yr,eqrisk,N |
| CF_HM_AB13_3m_k15 | 0.016 | 91 | -0.69 | -1.04 [-13.03, 10.32] (16.80) | -1.30 | -11.09 | 0.02 | 0.457 | -9,627 | -181,315 | mean,hold,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_SM_AB13_1m_k5 | 0.021 | 41 | -4.45 | -5.31 [-22.83, 13.13] (25.88) | -5.84 | -16.85 | 0.12 | 0.291 | -6,083 | -164,111 | mean,hold,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_SM_AB13_1m_k15 | 0.050 | 96 | -1.49 | +0.93 [-10.64, 12.13] (16.11) | 2.87 | 15.13 | -0.05 | 0.584 | -5,511 | -137,763 | plc90,nb,CI,yr,eqrisk,N |
| CF_SM_AB13_3m_k5 | 0.005 | 10 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_SM_AB13_3m_k15 | 0.019 | 38 | -8.59 | -4.58 [-22.87, 13.38] (25.88) | 0.07 | -25.85 | 0.09 | 0.324 | -6,030 | -151,084 | mean,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_EM_AB13_1m_k5 | 0.012 | 24 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_EM_AB13_1m_k15 | 0.036 | 70 | -5.73 | -0.79 [-14.06, 12.03] (18.97) | 3.62 | -8.45 | 0.03 | 0.428 | -3,744 | -162,529 | mean,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_EM_AB13_3m_k5 | 0.006 | 14 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_EM_AB13_3m_k15 | 0.012 | 24 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3B_R60_P2_AB13_1m_k5 | 0.009 | 51 | -12.70 | -9.64 [-23.50, 5.21] (20.41) | -7.78 | -6.97 | 0.09 | 0.116 | -6,003 | -387,699 | mean,hold,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_PB3B_R60_P2_AB13_1m_k15 | 0.026 | 145 | -4.70 | -6.46 [-15.10, 2.47] (12.45) | -7.13 | 8.61 | 0.17 | 0.081 | -6,686 | -238,139 | mean,hold,plc90,nb,CI,x2,yr,eqrisk,N |
| CF_PB3B_R60_P2_AB13_3m_k5 | 0.005 | 32 | 19.01 | +8.84 [-11.10, 27.72] (27.63) | 0.93 | -61.10 | -0.05 | 0.797 | -4,907 | -469,352 | plc90,nb,CI,span2,eqrisk,N |
| CF_PB3B_R60_P2_AB13_3m_k15 | 0.018 | 108 | 18.71 | +12.73 [1.21, 22.59] (14.98) | 8.12 | -8.30 | -0.25 | 0.993 | -3,429 | -450,431 | nb,span2,N |
| CF_PB3B_R5_P3_AB13_1m_k5 | 0.008 | 43 | -29.09 | -6.07 [-22.79, 10.71] (24.57) | 6.28 | -20.97 | 0.05 | 0.278 | -807 | -457,951 | mean,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_PB3B_R5_P3_AB13_1m_k15 | 0.022 | 119 | -9.09 | +8.08 [-1.87, 18.13] (14.34) | 17.82 | 18.63 | -0.20 | 0.942 | 866 | -452,223 | nb,CI,yr,plc95,N |
| CF_PB3B_R5_P3_AB13_3m_k5 | 0.005 | 29 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3B_R5_P3_AB13_3m_k15 | 0.015 | 84 | -0.91 | -2.67 [-14.37, 8.80] (16.68) | -3.63 | 18.73 | 0.05 | 0.346 | -776 | -466,039 | mean,hold,plc90,nb,CI,x2,yr,eqrisk,N |
| CF_PB3D_R3_P2_AB13_1m_k5 | 0.008 | 28 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3D_R3_P2_AB13_1m_k15 | 0.023 | 85 | 7.69 | +7.93 [-4.24, 19.48] (16.81) | 8.58 | -10.81 | -0.20 | 0.905 | -1,112 | -515,135 | CI,yr,plc95,span2,N |
| CF_PB3D_R3_P2_AB13_3m_k5 | 0.005 | 17 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3D_R3_P2_AB13_3m_k15 | 0.015 | 56 | 9.57 | +2.83 [-12.08, 18.15] (21.65) | -1.65 | 35.58 | -0.05 | 0.628 | -1,838 | -456,704 | hold,plc90,CI,yr,eqrisk,N |
| CF_ST_AB3_3m_k5 | 0.005 | 34 | -7.26 | -13.13 [-30.36, 5.58] (25.57) | -15.89 | -34.82 | 0.06 | 0.085 | -14,899 | -108,083 | mean,hold,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_ST_AB3_3m_k15 | 0.016 | 122 | -2.30 | +1.55 [-7.94, 11.21] (14.05) | 3.68 | -26.38 | -0.03 | 0.618 | -13,821 | -150,542 | plc90,nb,CI,yr,span2,eqrisk,N |
| CF_KB_AB3_3m_k5 | 0.010 | 82 | -8.01 | -0.70 [-13.43, 11.58] (17.72) | 3.82 | -21.09 | 0.01 | 0.458 | -11,129 | -196,368 | mean,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_KB_AB3_3m_k15 | 0.022 | 172 | -1.21 | +2.46 [-6.35, 10.45] (11.88) | 4.93 | 8.49 | -0.06 | 0.709 | -10,499 | -158,299 | plc90,nb,CI,yr,eqrisk,N |
| CF_PB3B_R5_P1_AB3_3m_k5 | 0.005 | 43 | -17.16 | -8.06 [-25.23, 9.02] (24.29) | -4.83 | -61.47 | 0.05 | 0.175 | -8,490 | -272,410 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_PB3B_R5_P1_AB3_3m_k15 | 0.024 | 184 | -1.46 | -0.23 [-8.03, 8.14] (11.42) | 0.46 | -15.86 | 0.01 | 0.479 | -8,089 | -214,980 | mean,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_SBS_AB3_3m_k5 | 0.004 | 11 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_SBS_AB3_3m_k15 | 0.016 | 44 | -9.70 | -5.85 [-13.39, 2.91] (11.74) | -2.56 | -7.10 | 0.10 | 0.202 | -3,439 | -357,220 | mean,hold,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_ST_AB_1m_k5 | 0.009 | 70 | 12.33 | +12.07 [-1.94, 25.91] (19.46) | 11.88 | 24.58 | -0.12 | 0.962 | -13,015 | -225,717 | CI,yr,eqrisk,N |
| CF_ST_AB_1m_k15 | 0.030 | 227 | 15.83 | +9.93 [2.82, 16.36] (9.63) | 6.28 | -10.96 | -0.33 | 0.992 | -10,775 | -191,513 | span2,N |
| CF_ST_AB_5m_k5 | 0.003 | 21 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_ST_AB_5m_k15 | 0.008 | 62 | -3.48 | +4.83 [-8.26, 18.26] (19.42) | 9.75 | 2.95 | -0.04 | 0.738 | -13,796 | -184,565 | plc90,nb,CI,yr,eqrisk,N |
| CF_ST_AB_t500_k5 | 0.002 | 10 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_ST_AB_t500_k15 | 0.005 | 34 | -32.19 | -2.85 [-20.74, 14.87] (25.29) | 6.25 | 18.82 | 0.01 | 0.362 | -14,410 | -203,244 | mean,plc90,nb,CI,x2,yr,eqrisk,N |
| CF_ST_CD_1m_k5 | 0.387 | 2761 | -0.52 | -0.40 [-2.07, 1.13] (2.29) | -0.32 | -0.23 | 0.26 | 0.302 | -9,918 | 122,837 | mean,hold,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_ST_CD_1m_k15 | 0.606 | 4304 | -0.23 | +0.39 [-0.73, 1.45] (1.54) | 0.85 | -0.62 | -0.59 | 0.760 | -1,760 | 35,906 | plc90,nb,CI,yr,span2,eqrisk,N |
| CF_ST_CD_5m_k5 | 0.045 | 325 | -8.48 | -4.08 [-9.97, 2.03] (8.73) | -0.92 | -2.43 | 0.20 | 0.096 | -15,454 | 10,107 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_ST_CD_5m_k15 | 0.140 | 1016 | -4.71 | -1.76 [-4.99, 1.60] (4.80) | 0.39 | -3.63 | 0.29 | 0.138 | -14,933 | 115,997 | mean,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_ST_CD_t500_k5 | 0.288 | 2037 | -2.53 | -0.90 [-2.98, 1.14] (2.96) | 0.40 | -1.05 | 0.36 | 0.195 | -14,035 | 121,312 | mean,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_ST_CD_t500_k15 | 0.457 | 3241 | 0.22 | +0.22 [-1.24, 1.69] (2.13) | 0.20 | 0.36 | -0.18 | 0.607 | -9,729 | 155,574 | plc90,nb,CI,yr,eqrisk,N |
| CF_ST_CZA_1m_k5 | 0.000 | 4 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_ST_CZA_1m_k15 | 0.002 | 8 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_ST_CZB_1m_k5 | 0.000 | 0 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_ST_CZB_1m_k15 | 0.000 | 0 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_KB_SI33_1m_k5 | 0.603 | 4370 | -0.47 | -0.30 [-1.36, 0.76] (1.52) | -0.25 | 0.20 | 0.44 | 0.288 | -6,107 | 202,372 | mean,hold,plc90,CI,x2,yr,eqrisk,N |
| CF_KB_SI33_1m_k15 | 0.769 | 5600 | 0.04 | -0.29 [-1.06, 0.40] (1.04) | -0.55 | -0.69 | 0.93 | 0.226 | -5,368 | 434,255 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_KB_SI33_5m_k5 | 0.281 | 2116 | -1.44 | -1.63 [-3.70, 0.40] (2.87) | -1.63 | -9.05 | 0.66 | 0.057 | -12,964 | 269,221 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_KB_SI33_5m_k15 | 0.519 | 3904 | -0.30 | -0.74 [-1.94, 0.43] (1.69) | -0.95 | -3.52 | 0.84 | 0.115 | -12,080 | 445,935 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_KB_SI33_t500_k5 | 0.593 | 4316 | 0.02 | -1.01 [-2.16, 0.05] (1.57) | -1.89 | -0.73 | 1.45 | 0.033 | -11,380 | 603,475 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_KB_SI33_t500_k15 | 0.740 | 5448 | 0.01 | -0.45 [-1.22, 0.29] (1.08) | -0.78 | -0.79 | 1.29 | 0.128 | -10,019 | 770,446 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_KB_SI44_1m_k5 | 0.248 | 1740 | -1.72 | -2.49 [-4.86, -0.09] (3.43) | -3.30 | 0.07 | 0.77 | 0.018 | -15,945 | 804,195 | mean,hold,plc90,CI,x2,yr,eqrisk,N |
| CF_KB_SI44_1m_k15 | 0.395 | 2820 | -0.57 | -1.35 [-2.96, 0.24] (2.36) | -2.05 | -0.80 | 0.84 | 0.047 | -12,662 | 602,120 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_KB_SI44_5m_k5 | 0.101 | 752 | -3.12 | -5.35 [-9.33, -1.51] (5.61) | -6.70 | 4.45 | 0.61 | 0.000 | -16,773 | 608,475 | mean,hold,plc90,CI,x2,yr,eqrisk,N |
| CF_KB_SI44_5m_k15 | 0.195 | 1457 | -2.54 | -3.44 [-5.84, -0.95] (3.47) | -3.98 | 4.95 | 0.85 | 0.001 | -17,409 | 739,827 | mean,hold,plc90,nb,CI,x2,yr,eqrisk,N |
| CF_KB_SI44_t500_k5 | 0.302 | 2109 | 1.52 | -1.12 [-3.29, 1.03] (3.09) | -3.62 | -1.61 | 0.45 | 0.127 | -11,327 | 726,381 | mean,hold,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_KB_SI44_t500_k15 | 0.449 | 3189 | 1.72 | +0.43 [-0.97, 1.75] (2.00) | -0.77 | 0.75 | -0.33 | 0.712 | -9,499 | 629,194 | hold,plc90,nb,CI,yr,eqrisk,N |
| CF_KB_DD_1m_k5 | 0.009 | 67 | 8.62 | +7.99 [-5.15, 21.39] (19.33) | 6.60 | -46.22 | -0.07 | 0.856 | -10,370 | -256,610 | plc90,nb,CI,span2,eqrisk,N |
| CF_KB_DD_1m_k15 | 0.059 | 446 | 4.21 | -0.29 [-5.80, 5.23] (7.70) | -2.93 | -4.39 | 0.02 | 0.455 | -11,119 | 2,981 | mean,hold,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_KB_DD_5m_k5 | 0.007 | 46 | -6.42 | -4.20 [-20.85, 10.89] (22.82) | -2.62 | -35.71 | 0.03 | 0.319 | -11,302 | -210,758 | mean,hold,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_KB_DD_5m_k15 | 0.029 | 207 | 7.56 | -1.34 [-9.19, 6.43] (11.24) | -6.90 | -4.31 | 0.04 | 0.373 | -11,487 | -41,851 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_KB_DD_t500_k5 | 0.010 | 70 | 16.64 | +2.01 [-11.63, 16.03] (20.44) | -17.43 | 19.77 | -0.02 | 0.607 | -10,846 | -161,782 | hold,plc90,nb,CI,yr,eqrisk,N |
| CF_KB_DD_t500_k15 | 0.071 | 525 | 2.62 | -0.91 [-5.88, 3.92] (7.04) | -4.10 | 8.15 | 0.07 | 0.346 | -12,798 | 166,146 | mean,hold,plc90,nb,CI,x2,yr,eqrisk,N |
| CF_KB_AB_1m_k5 | 0.013 | 104 | 9.01 | +7.94 [-3.61, 19.00] (16.10) | 7.63 | 13.28 | -0.11 | 0.917 | -9,904 | -254,732 | CI,yr,plc95,eqrisk,N |
| CF_KB_AB_1m_k15 | 0.032 | 253 | 17.87 | +8.41 [1.31, 15.69] (10.29) | 3.53 | 7.32 | -0.30 | 0.985 | -8,311 | -207,466 | nb,yr,eqrisk,N |
| CF_KB_AB_5m_k5 | 0.006 | 48 | 5.08 | +6.88 [-7.97, 20.95] (20.93) | 8.24 | -15.91 | -0.05 | 0.810 | -10,455 | -257,572 | plc90,nb,CI,span2,eqrisk,N |
| CF_KB_AB_5m_k15 | 0.012 | 94 | -1.76 | -2.56 [-13.71, 8.33] (15.63) | -2.43 | -15.91 | 0.03 | 0.331 | -11,354 | -167,074 | mean,hold,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_KB_AB_t500_k5 | 0.002 | 18 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_KB_AB_t500_k15 | 0.005 | 39 | 10.23 | +8.62 [-6.97, 24.60] (22.84) | 8.27 | 16.83 | -0.05 | 0.825 | -10,558 | -277,821 | plc90,nb,CI,eqrisk,N |
| CF_KB_CD_1m_k5 | 0.516 | 3831 | -0.09 | +0.60 [-0.60, 1.80] (1.72) | 1.09 | -2.40 | -0.65 | 0.820 | -6,195 | 109,070 | plc90,nb,CI,yr,span2,eqrisk,N |
| CF_KB_CD_1m_k15 | 0.759 | 5636 | -0.89 | -0.04 [-0.76, 0.67] (1.01) | 0.58 | 0.46 | 0.13 | 0.433 | -4,351 | 349,980 | mean,plc90,nb,CI,x2,yr,eqrisk,N |
| CF_KB_CD_5m_k5 | 0.104 | 790 | -0.68 | +0.39 [-3.24, 4.18] (5.35) | 1.19 | -9.56 | -0.05 | 0.569 | -11,361 | -55,781 | plc90,nb,CI,yr,span2,eqrisk,N |
| CF_KB_CD_5m_k15 | 0.207 | 1543 | -0.99 | +0.28 [-2.22, 2.64] (3.54) | 1.25 | -0.95 | -0.08 | 0.560 | -10,570 | 54,221 | plc90,nb,CI,yr,span2,eqrisk,N |
| CF_KB_CD_t500_k5 | 0.399 | 2901 | -1.36 | -1.56 [-3.17, 0.08] (2.33) | -1.94 | -2.65 | 1.02 | 0.025 | -13,362 | 667,119 | mean,hold,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_KB_CD_t500_k15 | 0.555 | 4058 | -0.49 | -1.02 [-2.21, 0.11] (1.69) | -1.59 | -0.89 | 1.26 | 0.037 | -7,452 | 172,104 | mean,hold,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_KB_CZA_1m_k5 | 0.000 | 1 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_KB_CZA_1m_k15 | 0.001 | 4 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_KB_CZB_1m_k5 | 0.000 | 0 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_KB_CZB_1m_k15 | 0.000 | 0 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3B_R5_P1_SI33_1m_k5 | 0.462 | 3300 | 1.58 | +0.06 [-1.36, 1.39] (1.95) | -1.07 | -0.04 | -0.05 | 0.552 | -6,704 | 461,216 | hold,plc90,nb,CI,yr,span2,eqrisk,N |
| CF_PB3B_R5_P1_SI33_1m_k15 | 0.740 | 5288 | -0.04 | -0.51 [-1.24, 0.21] (1.04) | -0.88 | -0.19 | 1.48 | 0.102 | -7,387 | 569,644 | mean,hold,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_PB3B_R5_P1_SI33_5m_k5 | 0.176 | 1327 | 1.43 | +1.47 [-1.24, 4.05] (3.80) | 1.52 | -8.34 | -0.34 | 0.857 | -6,573 | 31,555 | plc90,nb,CI,yr,span2,eqrisk,N |
| CF_PB3B_R5_P1_SI33_5m_k15 | 0.504 | 3713 | 1.11 | +1.00 [-0.29, 2.28] (1.84) | 0.93 | -3.95 | -1.09 | 0.932 | -4,251 | -35,974 | nb,CI,yr,plc95,span2,eqrisk,N |
| CF_PB3B_R5_P1_SI33_t500_k5 | 0.468 | 3352 | 1.07 | -1.22 [-2.63, 0.20] (2.06) | -3.09 | 2.03 | 1.09 | 0.063 | -11,006 | 924,683 | mean,hold,plc90,nb,CI,x2,yr,eqrisk,N |
| CF_PB3B_R5_P1_SI33_t500_k15 | 0.722 | 5189 | -0.50 | -0.87 [-1.70, -0.09] (1.12) | -1.16 | 0.33 | 2.34 | 0.023 | -9,745 | 413,346 | mean,hold,plc90,nb,CI,x2,yr,eqrisk,N |
| CF_PB3B_R5_P1_SI44_1m_k5 | 0.164 | 1152 | 1.62 | +0.20 [-2.81, 3.02] (4.19) | -0.89 | 1.22 | -0.04 | 0.579 | -8,978 | 56,281 | hold,plc90,nb,CI,yr,eqrisk,N |
| CF_PB3B_R5_P1_SI44_1m_k15 | 0.355 | 2500 | 0.06 | -1.06 [-2.89, 0.69] (2.54) | -1.97 | -0.78 | 0.57 | 0.140 | -8,814 | 127,989 | mean,hold,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_PB3B_R5_P1_SI44_5m_k5 | 0.049 | 367 | 0.55 | -0.48 [-6.03, 5.17] (7.97) | -1.11 | 17.48 | 0.03 | 0.411 | -8,052 | -126,453 | mean,hold,plc90,nb,CI,x2,yr,eqrisk,N |
| CF_PB3B_R5_P1_SI44_5m_k15 | 0.176 | 1281 | -3.51 | -2.17 [-4.97, 0.70] (4.10) | -1.17 | 1.92 | 0.47 | 0.061 | -12,410 | 516,401 | mean,hold,plc90,CI,x2,yr,eqrisk,N |
| CF_PB3B_R5_P1_SI44_t500_k5 | 0.199 | 1401 | 0.89 | -1.69 [-4.51, 1.09] (4.09) | -3.80 | -1.52 | 0.41 | 0.101 | -11,894 | 747,721 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_PB3B_R5_P1_SI44_t500_k15 | 0.412 | 2889 | 0.08 | -1.34 [-2.92, 0.13] (2.22) | -2.49 | 0.44 | 0.92 | 0.058 | -13,223 | 1,072,949 | mean,hold,plc90,CI,x2,yr,eqrisk,N |
| CF_PB3B_R5_P1_DD_1m_k5 | 0.011 | 84 | 1.05 | +0.62 [-11.41, 12.59] (17.38) | 0.42 | -21.86 | -0.01 | 0.554 | -7,891 | -237,337 | plc90,nb,CI,yr,span2,eqrisk,N |
| CF_PB3B_R5_P1_DD_1m_k15 | 0.061 | 466 | -7.06 | -6.92 [-11.48, -2.24] (6.59) | -6.80 | -4.73 | 0.48 | 0.004 | -12,774 | 388,442 | mean,hold,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_PB3B_R5_P1_DD_5m_k5 | 0.002 | 11 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3B_R5_P1_DD_5m_k15 | 0.006 | 40 | -20.71 | -10.11 [-27.58, 8.03] (25.19) | -1.45 | 9.82 | 0.06 | 0.123 | -8,568 | -201,874 | mean,hold,plc90,CI,x2,yr,eqrisk,N |
| CF_PB3B_R5_P1_DD_t500_k5 | 0.019 | 142 | 0.48 | -4.29 [-14.68, 5.68] (14.43) | -8.47 | -7.59 | 0.09 | 0.181 | -8,874 | -81,981 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_PB3B_R5_P1_DD_t500_k15 | 0.078 | 578 | -1.55 | -3.95 [-8.56, 0.84] (6.63) | -6.00 | -4.52 | 0.35 | 0.057 | -11,022 | 222,895 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_PB3B_R5_P1_AB_1m_k5 | 0.009 | 69 | 0.88 | +1.13 [-11.78, 14.00] (18.49) | 1.31 | -31.73 | -0.01 | 0.563 | -7,923 | -263,345 | plc90,CI,yr,span2,eqrisk,N |
| CF_PB3B_R5_P1_AB_1m_k15 | 0.033 | 255 | 2.97 | +2.86 [-4.23, 9.45] (9.77) | 2.84 | -19.19 | -0.11 | 0.804 | -7,325 | -226,745 | plc90,nb,CI,yr,span2,eqrisk,N |
| CF_PB3B_R5_P1_AB_5m_k5 | 0.003 | 22 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3B_R5_P1_AB_5m_k15 | 0.010 | 78 | -15.36 | -5.41 [-17.39, 7.19] (17.90) | 0.52 | -5.88 | 0.06 | 0.184 | -8,632 | -95,104 | mean,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_PB3B_R5_P1_AB_t500_k5 | 0.002 | 12 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3B_R5_P1_AB_t500_k15 | 0.005 | 36 | -0.85 | -6.16 [-23.05, 11.18] (25.17) | -7.56 | -21.82 | 0.03 | 0.255 | -8,308 | -275,394 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_PB3B_R5_P1_CD_1m_k5 | 0.298 | 2156 | -0.33 | -0.03 [-1.92, 1.92] (2.74) | 0.19 | 2.60 | 0.01 | 0.506 | -7,996 | -53,272 | mean,plc90,CI,x2,yr,eqrisk,N |
| CF_PB3B_R5_P1_CD_1m_k15 | 0.643 | 4647 | -0.74 | -0.63 [-1.58, 0.35] (1.35) | -0.54 | 0.42 | 1.18 | 0.107 | -8,967 | 112,208 | mean,hold,plc90,nb,CI,x2,yr,eqrisk,N |
| CF_PB3B_R5_P1_CD_5m_k5 | 0.039 | 295 | -6.83 | -0.59 [-6.92, 5.60] (8.82) | 3.64 | 2.65 | 0.03 | 0.424 | -8,247 | -136,303 | mean,plc90,nb,CI,x2,yr,eqrisk,N |
| CF_PB3B_R5_P1_CD_5m_k15 | 0.165 | 1219 | -3.36 | +0.48 [-2.41, 3.41] (4.20) | 3.13 | -4.57 | -0.10 | 0.663 | -6,614 | 73,066 | plc90,nb,CI,yr,span2,eqrisk,N |
| CF_PB3B_R5_P1_CD_t500_k5 | 0.235 | 1706 | -1.88 | -1.78 [-4.04, 0.56] (3.29) | -1.73 | -1.84 | 0.56 | 0.074 | -10,547 | 186,251 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_PB3B_R5_P1_CD_t500_k15 | 0.494 | 3491 | -0.34 | -1.27 [-2.65, 0.16] (1.98) | -2.03 | -1.15 | 1.22 | 0.049 | -9,742 | 345,903 | mean,hold,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_PB3B_R5_P1_CZA_1m_k5 | 0.000 | 0 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3B_R5_P1_CZA_1m_k15 | 0.001 | 3 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3B_R5_P1_CZB_1m_k5 | 0.000 | 0 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3B_R5_P1_CZB_1m_k15 | 0.000 | 0 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_SBS_SI33_1m_k5 | 0.406 | 1029 | 0.46 | -0.89 [-2.99, 1.27] (3.07) | -2.27 | -1.27 | 0.60 | 0.226 | -4,269 | 1,405 | mean,hold,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_SBS_SI33_1m_k15 | 0.762 | 1910 | 0.11 | -0.11 [-1.07, 0.80] (1.30) | -0.36 | 0.05 | 0.34 | 0.430 | -1,665 | -26,118 | mean,hold,plc90,nb,CI,x2,yr,eqrisk,N |
| CF_SBS_SI33_5m_k5 | 0.193 | 510 | -1.61 | +0.56 [-3.17, 4.67] (5.78) | 2.66 | 0.35 | -0.14 | 0.641 | -3,197 | -115,419 | plc90,nb,CI,yr,eqrisk,N |
| CF_SBS_SI33_5m_k15 | 0.585 | 1522 | 0.75 | +0.56 [-0.89, 2.08] (2.11) | 0.38 | -0.04 | -0.84 | 0.778 | -1,555 | -134,236 | plc90,nb,CI,yr,span2,eqrisk,N |
| CF_SBS_SI33_t500_k5 | 0.397 | 1009 | 0.20 | -1.52 [-3.64, 0.72] (3.10) | -3.24 | -1.03 | 1.00 | 0.089 | -4,153 | 33,179 | mean,hold,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_SBS_SI33_t500_k15 | 0.704 | 1789 | -0.18 | -0.19 [-1.24, 0.87] (1.48) | -0.20 | -0.43 | 0.44 | 0.399 | -2,315 | -51,868 | mean,hold,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_SBS_SI44_1m_k5 | 0.129 | 317 | -0.52 | -0.87 [-5.80, 4.24] (7.25) | -1.39 | 1.84 | 0.12 | 0.371 | -3,744 | -265,950 | mean,hold,plc90,nb,CI,x2,yr,eqrisk,N |
| CF_SBS_SI44_1m_k15 | 0.358 | 894 | -0.61 | -0.40 [-2.81, 1.99] (3.43) | -0.25 | 0.32 | 0.22 | 0.386 | -3,814 | -149,803 | mean,hold,plc90,nb,CI,x2,yr,eqrisk,N |
| CF_SBS_SI44_5m_k5 | 0.053 | 144 | -1.28 | +2.94 [-5.58, 12.62] (12.90) | 7.92 | 8.17 | -0.18 | 0.773 | -2,984 | -310,665 | plc90,nb,CI,yr,eqrisk,N |
| CF_SBS_SI44_5m_k15 | 0.219 | 580 | -1.14 | +2.86 [-1.16, 7.90] (6.37) | 6.66 | 1.26 | -0.84 | 0.946 | -2,302 | -265,026 | nb,CI,yr,plc95,eqrisk,N |
| CF_SBS_SI44_t500_k5 | 0.166 | 414 | -1.90 | -1.89 [-6.21, 2.27] (6.11) | -2.02 | 1.34 | 0.37 | 0.182 | -3,314 | -247,994 | mean,hold,plc90,nb,CI,x2,yr,eqrisk,N |
| CF_SBS_SI44_t500_k15 | 0.386 | 961 | 0.20 | -0.85 [-3.00, 1.37] (3.18) | -2.10 | 1.11 | 0.51 | 0.264 | -3,077 | -112,587 | mean,hold,plc90,nb,CI,x2,yr,eqrisk,N |
| CF_SBS_DD_1m_k5 | 0.003 | 7 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_SBS_DD_1m_k15 | 0.014 | 38 | 17.10 | +4.17 [-11.48, 23.33] (25.34) | -10.28 | -8.84 | -0.06 | 0.725 | -3,151 | -337,349 | hold,plc90,nb,CI,yr,span2,eqrisk,N |
| CF_SBS_DD_5m_k5 | 0.000 | 0 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_SBS_DD_5m_k15 | 0.003 | 7 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_SBS_DD_t500_k5 | 0.021 | 52 | -9.61 | -10.87 [-19.16, -1.54] (12.84) | -14.46 | 7.96 | 0.23 | 0.022 | -3,568 | -322,079 | mean,hold,plc90,CI,x2,yr,eqrisk,N |
| CF_SBS_DD_t500_k15 | 0.029 | 71 | -0.31 | -5.68 [-15.09, 5.00] (14.78) | -16.06 | -0.82 | 0.16 | 0.139 | -3,449 | -333,090 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_SBS_AB_1m_k5 | 0.016 | 46 | -4.72 | -8.70 [-14.25, -3.21] (8.08) | -11.35 | -9.26 | 0.16 | 0.065 | -3,662 | -326,677 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_SBS_AB_1m_k15 | 0.053 | 142 | -4.63 | -3.09 [-7.94, 1.97] (7.01) | -1.85 | -1.04 | 0.18 | 0.213 | -3,603 | -313,720 | mean,hold,plc90,CI,x2,yr,span2,eqrisk,N |
| CF_SBS_AB_5m_k5 | 0.003 | 8 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_SBS_AB_5m_k15 | 0.010 | 29 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_SBS_AB_t500_k5 | 0.002 | 6 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_SBS_AB_t500_k15 | 0.005 | 15 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_SBS_CD_1m_k5 | 0.240 | 611 | 0.23 | +0.91 [-2.37, 4.09] (4.69) | 1.56 | 0.25 | -0.29 | 0.731 | -2,378 | -228,659 | plc90,nb,CI,yr,eqrisk,N |
| CF_SBS_CD_1m_k15 | 0.762 | 1930 | -0.70 | -0.34 [-1.31, 0.62] (1.38) | 0.01 | -0.11 | 1.06 | 0.269 | -2,434 | -67,033 | mean,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_SBS_CD_5m_k5 | 0.052 | 128 | -0.60 | -1.13 [-7.44, 6.07] (9.71) | -1.55 | -6.82 | 0.06 | 0.412 | -3,369 | -332,441 | mean,hold,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_SBS_CD_5m_k15 | 0.349 | 864 | -0.84 | +0.89 [-1.50, 3.29] (3.41) | 2.53 | -1.36 | -0.45 | 0.745 | -1,911 | -246,247 | plc90,nb,CI,yr,span2,eqrisk,N |
| CF_SBS_CD_t500_k5 | 0.184 | 455 | -0.26 | +1.26 [-3.24, 5.75] (6.45) | 2.96 | -4.24 | -0.27 | 0.744 | -2,397 | -222,073 | plc90,nb,CI,yr,span2,eqrisk,N |
| CF_SBS_CD_t500_k15 | 0.488 | 1196 | -0.61 | -0.21 [-2.02, 1.70] (2.69) | 0.16 | -0.06 | 0.19 | 0.413 | -2,339 | -91,881 | mean,plc90,nb,CI,x2,yr,span2,eqrisk,N |
| CF_SBS_CZA_1m_k5 | 0.001 | 2 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_SBS_CZA_1m_k15 | 0.003 | 5 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_SBS_CZB_1m_k5 | 0.001 | 1 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_SBS_CZB_1m_k15 | 0.002 | 3 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_HM_CZA_1m_k5 | 0.000 | 1 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_HM_CZA_1m_k15 | 0.000 | 1 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_HM_CZB_1m_k5 | 0.000 | 1 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_HM_CZB_1m_k15 | 0.000 | 1 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_SM_CZA_1m_k5 | 0.000 | 0 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_SM_CZA_1m_k15 | 0.003 | 4 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_SM_CZB_1m_k5 | 0.000 | 0 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_SM_CZB_1m_k15 | 0.002 | 1 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_EM_CZA_1m_k5 | 0.001 | 2 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_EM_CZA_1m_k15 | 0.005 | 7 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_EM_CZB_1m_k5 | 0.001 | 0 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_EM_CZB_1m_k15 | 0.003 | 1 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3B_R60_P2_CZA_1m_k5 | 0.000 | 0 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3B_R60_P2_CZA_1m_k15 | 0.001 | 3 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3B_R60_P2_CZB_1m_k5 | 0.000 | 0 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3B_R60_P2_CZB_1m_k15 | 0.000 | 0 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3B_R5_P3_CZA_1m_k5 | 0.001 | 0 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3B_R5_P3_CZA_1m_k15 | 0.002 | 7 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3B_R5_P3_CZB_1m_k5 | 0.000 | 0 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3B_R5_P3_CZB_1m_k15 | 0.000 | 0 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3D_R3_P2_CZA_1m_k5 | 0.002 | 4 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3D_R3_P2_CZA_1m_k15 | 0.005 | 11 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3D_R3_P2_CZB_1m_k5 | 0.000 | 0 | | | | | | | | | under 30 kept/mirror WF trades |
| CF_PB3D_R3_P2_CZB_1m_k15 | 0.000 | 0 | | | | | | | | | under 30 kept/mirror WF trades |

## Files
Prereg: l2vast/ds3/prereg/FP_{FP1..FP6,CF1..CF11}_prereg.md (+ .sha256); pre-holdout texts autopilot/DS3_FP_<group>_PREHOLD.md; results out/FP/res_FP*.json, conf_CF*.json, plc2_*.json, standalone_final_df.pkl, conf_final_df.pkl, trunc_audit.json; rows l2vast/ds3/rows/DS3_TFOOTPRINT.json; code l2vast/ds3/code/fp/ (fp_data, fp_ev, fp_setups, fp_plc, fp_plc2, fp_score, fp_conf, fp_prereg, fp_conf_prereg, fp_pre, fp_conf_pre, fp_final, fp_conf_final, fp_report, fp_trunc, fp_build3m); logs autopilot/d3fp/.
