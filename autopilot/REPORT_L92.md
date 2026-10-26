# REPORT L92 - BTC wide-bracket cure: plateau, 2x slip, replication (BACKLOG2 item 92)

**Verdict: NO (cure fails). FOUND 0, LEAD 0 new.** 54-cell wide-trail BTC WT neighbourhood: ensemble uplift at 20% +0.10 / +0.18 / -0.02 (H2 fails), ETH/ES/RTY replication fails; the original lead remains a plateau-failing LEAD.

Pre-registered in PREREG_AUTOPILOT.md ('BACKLOG2 GROUP L') before the first run. Fill model: signal at bar close, entry next 1-minute open, 1 tick adverse per side (stop-market with slippage; targets none), $4.36 per contract round trip, 2x slippage = 2 ticks; code ap_b_base.py, L92 module, ap_l_cure.py, ap_l_era.py; data outputs/autopilot/l/l92/. Baseline pair B.Cfg(wk_floor=8, wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30). Selection: none (the whole pre-registered neighbourhood is averaged with equal risk; nothing is picked among cells).

IMPORTANT: this neighbourhood is built around a cell whose clean/H1/H2 results are already known (B-family lead). It is therefore a CURE ATTEMPT, not an independent test: the three spans are not untouched for the centre cell. A pass can at most make it a candidate for a rolling-data (new live weeks) read.

## 1. Grid summary
54 cells; uplift >= +0.10 on clean, H1 and H2 together in 6; positive all-in uplift in 54; median uplift clean/H1/H2 0.09 / 0.13 / -0.03; best/worst all-in 0.20 / 0.01.

## 2. Equal-risk ensembles: additive framing and all gates
| ensemble | cells | standalone Sharpe clean / H1 / H2 | OOS (H1+H2) | uplift@10% clean/H1/H2 | uplift@20% | uplift@30% | uplift@50% | boot lo @20% | worst-week chg @20% (%) | timing-destroyed ensemble null p95 (rank) | wd corr | 2x-slip uplift@20% | leave-one-value-out plateau | alt months odd / even | H0 Sharpe |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | 54 | 2.36 / 2.45 / -0.66 | 0.73 | 0.05 / 0.09 / -0.01 | 0.10 / 0.18 / -0.02 | 0.15 / 0.27 / -0.04 | 0.25 / 0.44 / -0.06 | 0.04 | -1.3 | 0.80 (1.00) | -0.25 | 0.07 / 0.16 / -0.05 | 0.91 | 0.04 / 0.11 | 1.76 |
| m3.0 | 18 | 2.72 / 2.89 / 0.24 | 1.38 | 0.08 / 0.12 / 0.01 | 0.15 / 0.23 / 0.02 | 0.23 / 0.34 / 0.03 | 0.37 / 0.57 / 0.04 | 0.08 | -1.9 | 0.85 (1.00) | -0.15 | 0.10 / 0.20 / -0.01 | 0.88 | 0.08 / 0.15 | 1.44 |
| m4.0 | 18 | 1.99 / 2.11 / -1.10 | 0.30 | 0.05 / 0.08 / -0.02 | 0.09 / 0.16 / -0.05 | 0.13 / 0.24 / -0.07 | 0.22 / 0.39 / -0.12 | 0.02 | -1.1 | 0.65 (1.00) | -0.14 | 0.06 / 0.14 / -0.07 | 0.88 | 0.03 / 0.09 | 2.16 |
| m5.0 | 18 | 1.74 / 1.78 / -1.19 | 0.27 | 0.03 / 0.07 / -0.02 | 0.07 / 0.14 / -0.04 | 0.10 / 0.21 / -0.07 | 0.16 / 0.35 / -0.12 | 0.01 | -0.9 | 0.96 (1.00) | -0.39 | 0.05 / 0.13 / -0.06 | 1.00 | 0.01 / 0.08 | 1.44 |

## 3. Constant-risk framing (INSURANCE test: net >= -5% and worst week / CVaR5 improvement >= 20%)
| ensemble | const20 net % | ww impr % | CVaR5 impr % | const30 net % | ww impr % | CVaR5 impr % |
|---|---|---|---|---|---|---|
| ALL | -15.4 | 21.1 | 20.0 | -23.2 | 30.6 | 29.6 |
| m3.0 | -13.1 | 21.7 | 20.4 | -19.6 | 29.3 | 30.1 |
| m4.0 | -16.3 | 20.9 | 19.8 | -24.5 | 29.0 | 29.6 |
| m5.0 | -16.9 | 20.6 | 19.3 | -25.4 | 27.7 | 28.6 |

## 4. Replication (amendment 2)
Alternating months and H0 are in the ensemble table. Cross-instrument (same grid, same ensemble recipe):
| instrument | standalone Sharpe all-in | OOS | uplift clean / H1 / H2 | all-in |
|---|---|---|---|---|
| ETH | 1.50 | 0.84 | 0.09 / 0.17 / -0.05 | 0.07 |
| ES | -0.71 | -1.43 | -0.03 / -0.11 / -0.11 | -0.06 |
| RTY | -0.99 | -1.38 | -0.06 / 0.06 / -0.17 | -0.07 |

## 5. ERA FLAG and cost decomposition
L92 BTC cells 54 pre-2023 weekly Sharpe gross/net/netscaled 2.22 0.98 1.76 | clean 3.13 2.39 2.54 mean per-trade pre-2023 ($ at 1 contract-equivalent) gross/net/netscaled 735.0 332.7 588.1 trades/cell 578 ERA FLAG: positive pre-2023 

## 6. What this says
- **The BTC lead does not have a plateau in the wide-trail direction: it is a peak.** The 54-cell neighbourhood (10/15-minute WT with ATR 15/20/25, mult 2.25/3.0/3.75, ATR trail x3/x4/x5) is strongly profitable in clean and H1 (ensemble standalone Sharpe 2.36 / 2.45) but loses in H2 (-0.66), so the ensemble uplift at 20% is +0.10 / +0.18 / -0.02 (all-in +0.08) and H2 fails at every share (-0.01 to -0.06); only 6 of 54 single cells have +0.10 on all three spans and 8 have +0.10 in H2, with the original cell (10m WT(20,3.0) x3) one of them. Restricting to the narrowest trail (x3) improves it to +0.15 / +0.23 / +0.02, still H2 below +0.10. Wider trails (x4, x5) are worse (H2 -0.05, -0.04; standalone H2 -1.10 and -1.19). The ensemble passes plateau (leave-one-out 0.91), bootstrap lower bound (+0.04), 2x slippage on H1 but fails H2 uplift, the 2x-slippage all-in uplift is +0.05 and out-of-selection Sharpe 0.73.
- Replication: ETH (same cells) +0.09 / +0.17 / -0.05; ES -0.03 / -0.11 / -0.11; RTY -0.06 / +0.06 / -0.17: the BTC trend sleeve is not a general crypto-or-index structure; H0 2023-02..07 standalone ensemble Sharpe +1.76 holds, alternating months odd +0.04 / even +0.11 against +0.08 (both positive; odd below 50%): 1 of 4 clearly, not replicated.
- Reading: B1's BTC 10m WT x3 lead stands as one cell whose H2 uplift (+0.15) is above its neighbours (median H2 uplift of the neighbourhood -0.03); widening the bracket does not cure the plateau failure, it removes the H2 benefit. Verdict: NO for the cure attempt; the original B1 BTC lead remains a LEAD that failed the plateau gate.
- ERA FLAG for the ensemble: positive pre-2023 (BTC futures 2022 only: weekly Sharpe gross 2.22 / net 0.98 / price-scaled 1.76).


DONE L92
