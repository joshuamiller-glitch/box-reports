# P7 (PE) ASIA RISK CONTROL on V13T_LIVE (BASE-4, 2026-11-02T13:37Z)

Prereg: l2vast/ds3/prereg/P7_ASIA_RISK_prereg.md (sha256 7e6eecd7e44503a9784dbd6ddf5e9b71096a67826be908d0471a7f5f0fda9e2b in DECISIONS.md; the prereg text says "11 cells" but lists 9 cells + base). Base V13T_LIVE lock none; episodes lookup DS3_ZONES_EPISODES_V13Y.md. Cell: mean $k/wk / maxDD $k (cut vs base, positive = shallower) / equal-risk mean (x worst-20-ALL base / variant, linear). Post-hoc; no PASS.

## 1. Family, lock none (phase 0)
| cell | F9 | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|
| base | 33.7 / DD 150.7 (+0%) / ER 33.7 | 14.7 / DD 94.0 (+0%) / ER 14.7 | 36.7 / DD 150.7 (+0%) / ER 36.7 | 30.4 / DD 150.7 (+0%) / ER 30.4 | 24.0 / DD 43.7 (+0%) / ER 24.0 | 17.3 / DD 166.2 (+0%) / ER 17.3 | 4.8 / DD 92.5 (+0%) / ER 4.8 |
| C75 | 29.3 / DD 133.6 (+11%) / ER 31.6 | 11.3 / DD 104.7 (-11%) / ER 12.2 | 31.1 / DD 133.6 (+11%) / ER 33.5 | 28.3 / DD 133.6 (+11%) / ER 30.5 | 22.9 / DD 42.1 (+4%) / ER 24.6 | 14.5 / DD 163.0 (+2%) / ER 15.6 | 4.9 / DD 62.3 (+33%) / ER 5.3 |
| C50 | 25.8 / DD 160.7 (-7%) / ER 28.6 | 6.1 / DD 142.9 (-52%) / ER 6.8 | 26.9 / DD 160.7 (-7%) / ER 29.9 | 25.1 / DD 160.7 (-7%) / ER 27.8 | 20.9 / DD 40.5 (+7%) / ER 23.2 | 13.5 / DD 142.0 (+15%) / ER 15.0 | 1.3 / DD 94.2 (-2%) / ER 1.4 |
| G1 | 28.7 / DD 172.1 (-14%) / ER 28.6 | 11.4 / DD 97.1 (-3%) / ER 11.4 | 31.2 / DD 172.1 (-14%) / ER 31.2 | 25.9 / DD 172.1 (-14%) / ER 25.9 | 20.6 / DD 44.0 (-1%) / ER 20.6 | 17.0 / DD 158.3 (+5%) / ER 17.0 | 5.3 / DD 94.8 (-3%) / ER 5.2 |
| G2 | 32.5 / DD 148.2 (+2%) / ER 32.4 | 13.8 / DD 94.0 (+0%) / ER 13.7 | 36.0 / DD 148.2 (+2%) / ER 35.9 | 29.6 / DD 148.2 (+2%) / ER 29.6 | 22.0 / DD 43.7 (+0%) / ER 22.0 | 17.1 / DD 166.5 (-0%) / ER 17.1 | 4.8 / DD 92.5 (+0%) / ER 4.8 |
| G3 | 24.1 / DD 205.2 (-36%) / ER 24.8 | 8.4 / DD 115.4 (-23%) / ER 8.7 | 24.0 / DD 205.2 (-36%) / ER 24.7 | 22.0 / DD 205.2 (-36%) / ER 22.6 | 22.4 / DD 42.8 (+2%) / ER 23.1 | 16.6 / DD 155.3 (+7%) / ER 17.1 | 5.0 / DD 87.9 (+5%) / ER 5.2 |
| F4 | 32.6 / DD 182.3 (-21%) / ER 34.3 | 14.1 / DD 81.7 (+13%) / ER 14.8 | 35.3 / DD 182.3 (-21%) / ER 37.1 | 30.2 / DD 182.3 (-21%) / ER 31.7 | 23.8 / DD 43.6 (+0%) / ER 25.0 | 16.1 / DD 166.2 (+0%) / ER 16.9 | 3.9 / DD 96.5 (-4%) / ER 4.1 |
| F6 | 32.4 / DD 194.4 (-29%) / ER 32.0 | 14.2 / DD 94.0 (+0%) / ER 14.0 | 34.9 / DD 194.4 (-29%) / ER 34.5 | 29.6 / DD 194.4 (-29%) / ER 29.3 | 24.0 / DD 43.7 (+0%) / ER 23.7 | 16.9 / DD 166.2 (+0%) / ER 16.7 | 4.5 / DD 91.0 (+2%) / ER 4.5 |
| L2 | 27.5 / DD 164.5 (-9%) / ER 26.9 | 14.5 / DD 78.1 (+17%) / ER 14.2 | 31.6 / DD 164.5 (-9%) / ER 30.9 | 27.6 / DD 164.5 (-9%) / ER 26.9 | 16.1 / DD 75.5 (-73%) / ER 15.8 | 15.8 / DD 188.9 (-14%) / ER 15.5 | 4.9 / DD 72.6 (+21%) / ER 4.7 |
| L3 | 32.8 / DD 116.5 (+23%) / ER 32.8 | 14.7 / DD 111.6 (-19%) / ER 14.7 | 36.6 / DD 116.5 (+23%) / ER 36.5 | 30.3 / DD 134.2 (+11%) / ER 30.3 | 21.5 / DD 48.6 (-11%) / ER 21.5 | 16.4 / DD 170.7 (-3%) / ER 16.4 | 6.0 / DD 77.7 (+16%) / ER 6.0 |


## 2. (a) Phase-averaged maxDD cut (K=9 lock-reset phases) vs Z3 band
| cell | band row | L6M | PRE | X' | HOLD | MID | rule (a) |
|---|---|---|---|---|---|---|---|
| C75 | flip 5% | +11% [+5,+22] (band 20%) | +0% [-4,+4] (band 17%) | +20% [+15,+33] (band 23%) | +11% [+5,+22] (band 19%) | +13% [-4,+46] (band 37%) | no |
| C50 | flip 5% | +7% [-7,+17] (band 20%) | -36% [-65,+15] (band 17%) | +19% [-2,+36] (band 23%) | +7% [-7,+17] (band 19%) | +2% [-54,+65] (band 37%) | no |
| G1 | flip 5% | -10% [-16,+0] (band 20%) | +8% [+5,+12] (band 17%) | -0% [-6,+3] (band 23%) | -10% [-16,+0] (band 19%) | -46% [-152,-1] (band 37%) | no |
| G2 | flip 5% | +1% [+1,+2] (band 20%) | -0% [-0,+0] (band 17%) | +0% [+0,+0] (band 23%) | +1% [+1,+2] (band 19%) | -12% [-54,+0] (band 37%) | no |
| G3 | flip 5% | -23% [-36,-11] (band 20%) | +9% [+3,+15] (band 17%) | +3% [+1,+5] (band 23%) | -23% [-36,-11] (band 19%) | -36% [-134,+2] (band 37%) | no |
| F4 | flip 5% | -5% [-21,+2] (band 20%) | +0% [-0,+1] (band 17%) | +1% [-4,+8] (band 23%) | -5% [-21,+2] (band 19%) | +0% [+0,+1] (band 37%) | no |
| F6 | flip 5% | -9% [-29,+0] (band 20%) | -0% [-0,+0] (band 17%) | +0% [-10,+8] (band 23%) | -9% [-29,+0] (band 19%) | +0% [-0,+1] (band 37%) | no |
| L2 | flip 2% | -5% [-13,+2] (band 16%) | -6% [-17,+7] (band 11%) | +17% [+11,+26] (band 16%) | -5% [-13,+2] (band 14%) | -52% [-166,-2] (band 26%) | no |
| L3 | flip 2% | +22% [+11,+34] (band 16%) | -7% [-8,-3] (band 11%) | +9% [-3,+19] (band 16%) | +17% [+11,+34] (band 14%) | -18% [-56,-6] (band 26%) | no |


## 3. (b) Equal-risk mean delta vs base ($k/wk; need >= -0.5 MDE)
| cell | L6M | PRE | X' | rule (b) |
|---|---|---|---|---|
| C75 | -3.3 (MDE 6.8) | -1.7 (MDE 3.4) | +0.5 (MDE 2.9) | MET |
| C50 | -6.8 (MDE 9.4) | -2.3 (MDE 4.6) | -3.4 (MDE 5.6) | no |
| G1 | -5.6 (MDE 6.4) | -0.3 (MDE 3.3) | +0.4 (MDE 1.4) | no |
| G2 | -0.9 (MDE 3.1) | -0.2 (MDE 0.4) | -0.0 (MDE 0.0) | no |
| G3 | -12.0 (MDE 10.3) | -0.2 (MDE 4.0) | +0.4 (MDE 1.6) | no |
| F4 | +0.3 (MDE 4.4) | -0.4 (MDE 2.3) | -0.7 (MDE 1.8) | MET |
| F6 | -2.3 (MDE 2.9) | -0.6 (MDE 1.4) | -0.3 (MDE 1.3) | no |
| L2 | -5.9 (MDE 11.0) | -1.8 (MDE 3.5) | -0.1 (MDE 3.0) | no |
| L3 | -0.2 (MDE 5.7) | -0.9 (MDE 2.0) | +1.2 (MDE 2.1) | MET |


## 4. (c) Two-episode rule: episodes = top-3 base drawdown episodes of F9, PRE, X' (peak-week..recovery-week; episode-local maxDD with vs without): F9 W202628-W202639 depth 151k; F9 W202643-W202644 depth 94k; F9 W202607-W202609 depth 44k; PRE W202434-W202448 depth 166k; PRE W202505-W202519 depth 165k; PRE W202412-W202422 depth 86k; X' W202341-W202404 depth 92k; X' W202332-W202339 depth 66k; X' W202314-W202317 depth 46k
| cell | episodes with a shallower drawdown | rule (c) |
|---|---|---|
| C75 | 8 of 9 | MET |
| C50 | 6 of 9 | MET |
| G1 | 3 of 9 | MET |
| G2 | 1 of 9 | no |
| G3 | 6 of 9 | MET |
| F4 | 4 of 9 | MET |
| F6 | 1 of 9 | no |
| L2 | 6 of 9 | MET |
| L3 | 4 of 9 | MET |


## 5. (e) Purged walk-forward (monthly choice among base + 9 cells by trailing-12m Calmar, series splicing): eval 2024-01..2026-10: base mean 22.9k maxDD 166k worst-20 -1048k; WF mean 20.4k maxDD 196k worst-20 -1098k; equal-risk WF mean 19.5k; choices {'C75': 10, 'L3': 5, 'L2': 2, 'G1': 1, 'G3': 10, 'F4': 6}. Rule (e): NOT met.


## 6. Survivors of (a)-(c): none. Placebos (d) run for survivors only.
