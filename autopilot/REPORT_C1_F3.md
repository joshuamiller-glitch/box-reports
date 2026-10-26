# REPORT C1-F3 — term-structure carry and cross-sectional momentum (daily, 26 CME outrights)
Registered in PREREG_AUTOPILOT.md (cycle 1) before the run. **Result: FOUND 0, LEAD 0, NO 40 of 40 additive cells. Nothing here raises the pair's Sharpe; the carry signal is the only thing with a hedge-like pattern and it does not pay.**

## What was run
- **Data:** Databento GLBX.MDP3 ohlcv-1d continuous .v.0 / .v.1 for the 26 outrights (2013-01..2026-10-14; ZC and some grains start later), back-adjusted additively with the T4-A loader (`t4_a_core.py`), roll costs = one extra round trip per contract held through a roll.
- **Carry:** ln(F_v0 / F_v1) from same-day RAW closes, annualised by the calendar spacing between the v.0 contract's tenure start and the next contract's tenure start (proxy for expiry spacing: no definition schema on the box). Used only on days where v.1's instrument_id equals the contract v.0 rolls into next (valid deferred contract); 21-day mean. Valid share: ES 94%, CL 92%, GC 80%, ZN 70%, ZC 71%. Positive = backwardation = long.
- **Momentum:** vol-normalised (t-statistic) return from t-L to t-21 days (skips the last month), L = 126 (6 mo) or 252 (12 mo).
- **Books (10, as registered):** carry-CS (long top quintile, short bottom quintile of 26), carry-TS (sign of own carry), mom6-CS, mom12-CS, both = rank average of carry and mom12; each rebalanced weekly (W) or monthly (M) at the last close of the period, acting from the next open. Each market sized to $7,000 ATR20 risk (1% of $700k), fractional contracts. Needs >= 18 valid markets, else flat.
- **Costs:** 1 tick/side + per-product commission (T4-A table) + roll cost. Margins: metals 9% of notional (unverified; T4-A), others fixed approximations (unverified).
- **Pair baseline:** B.Cfg(wk_floor=8, wk_loss_pb=None) (1.46/2.83/2.30), computed in a clean process via `t3_score.py`; robustness vs B.Cfg() (1.35/1.65/2.26) in section 4. Sleeves are scaled to the pair's weekly volatility (same convention as T4 A / T3). Selection rule: best CLEAN standalone Sharpe = **both(carry+mom12)-CS|W**; all 10 are reported.
- **Gating null:** each book's own timing-destroyed null — each market's target series circularly shifted by an independent random offset (60..n-60) and re-priced (200 draws), compared on standalone weekly Sharpe in the pair window 2023-08..2026-10 and on 2013-2026. The circular-shift null of the weekly P&L (reported; a gate only for hedge claims, wd corr < 0) is in `F3_scored.csv`.

## 1. Standalone (weekly Sharpe)
| book | trades in pair window | clean | H1 | H2 | pair-window Sharpe | own-null p95 (pair window) | 2013-2026 Sharpe | null p95 (full) | small-sample |
|---|---|---|---|---|---|---|---|---|---|
| carry-CS|W | 108 | -0.09 | -1.29 | -0.04 | -0.30 | 0.76 | 0.04 | 0.47 | no |
| carry-TS|W | 94 | -0.07 | -2.45 | -0.28 | -0.43 | 0.43 | -0.06 | 0.44 | **YES** |
| mom6-CS|W | 348 | -1.36 | 1.68 | 1.61 | -0.32 | 1.14 | -0.04 | 0.73 | no |
| mom12-CS|W | 278 | -0.07 | 1.82 | 0.95 | 0.50 | 1.19 | 0.53 | 0.84 | no |
| both(carry+mom12)-CS|W **(clean-selected)** | 264 | 0.18 | -0.74 | -0.61 | -0.12 | 0.94 | 0.45 | 0.76 | no |
| carry-CS|M | 72 | 0.11 | -2.20 | 0.42 | -0.20 | 0.77 | 0.30 | 0.51 | **YES** |
| carry-TS|M | 74 | -0.03 | -2.16 | 0.43 | -0.27 | 0.41 | 0.10 | 0.45 | **YES** |
| mom6-CS|M | 164 | -1.71 | 2.39 | -0.13 | -0.77 | 1.12 | -0.11 | 0.75 | no |
| mom12-CS|M | 117 | -0.34 | 1.79 | 1.12 | 0.31 | 1.22 | 0.69 | 0.84 | no |
| both(carry+mom12)-CS|M | 131 | -0.05 | 0.06 | 0.95 | 0.16 | 1.04 | 0.78 | 0.77 | no |

## 2. Additive at 20% of pair risk (change in weekly Sharpe vs the pair)
| book | clean dSharpe | H1 | H2 | all-in | worst week chg % | bootstrap 5th pct | shift-null rank | wd corr | wd sleeve mean $/wk | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|
| carry-CS|W | -0.01 | -0.26 | -0.04 | -0.05 | +18 | -0.25 | 0.94 | -0.17 | 30,981 | NO | G3 per-span +0.10/worst week; G4 own null p95 + bootstrap; G4h shift null (hedge claim); G5 plateau/2x slip |
| carry-TS|W | -0.05 | -0.54 | -0.06 | -0.12 | +32 | -0.31 | 0.40 | -0.08 | 253 | NO | G3 per-span +0.10/worst week; G4 own null p95 + bootstrap; G4h shift null (hedge claim); G5 plateau/2x slip |
| mom6-CS|W | -0.31 | 0.21 | 0.20 | -0.12 | +30 | -0.31 | 0.21 | 0.03 | -10,783 | NO | G3 per-span +0.10/worst week; G4 own null p95 + bootstrap; G5 plateau/2x slip |
| mom12-CS|W | -0.04 | 0.20 | 0.18 | 0.05 | +32 | -0.13 | 0.35 | 0.13 | -6,033 | NO | G3 per-span +0.10/worst week; G4 own null p95 + bootstrap; G5 plateau/2x slip |
| both(carry+mom12)-CS|W | 0.02 | -0.31 | -0.06 | -0.04 | +14 | -0.23 | 0.80 | 0.06 | 17,269 | NO | G3 per-span +0.10/worst week; G4 own null p95 + bootstrap; G5 plateau/2x slip |
| carry-CS|M | 0.01 | -0.53 | 0.05 | -0.05 | +17 | -0.25 | 0.80 | -0.12 | 25,624 | NO | G3 per-span +0.10/worst week; G4 own null p95 + bootstrap; G4h shift null (hedge claim); G5 plateau/2x slip |
| carry-TS|M | -0.04 | -0.54 | 0.05 | -0.09 | +31 | -0.28 | 0.42 | -0.06 | 2,918 | NO | G3 per-span +0.10/worst week; G4 own null p95 + bootstrap; G4h shift null (hedge claim); G5 plateau/2x slip |
| mom6-CS|M | -0.38 | 0.35 | -0.10 | -0.21 | +17 | -0.40 | 0.16 | -0.11 | -13,494 | NO | G3 per-span +0.10/worst week; G4 own null p95 + bootstrap; G4h shift null (hedge claim); G5 plateau/2x slip |
| mom12-CS|M | -0.09 | 0.21 | 0.13 | 0.01 | +34 | -0.17 | 0.24 | 0.20 | -17,367 | NO | G3 per-span +0.10/worst week; G4 own null p95 + bootstrap; G5 plateau/2x slip |
| both(carry+mom12)-CS|M | -0.03 | -0.17 | 0.17 | 0.01 | +12 | -0.18 | 0.68 | 0.09 | 10,730 | NO | G3 per-span +0.10/worst week; G4 own null p95 + bootstrap; G5 plateau/2x slip |

Other shares (10/30/50%) are in `F3_scored.csv` and `F3_verdicts.csv`; the pattern is the same.

## 3. Constant-risk (total 16 contracts-eq; pair shrinks) at 10% and 30%
| book | share | all-in net chg % | worst week impr % | CVaR5 impr % | max DD impr % | INSURANCE |
|---|---|---|---|---|---|---|
| carry-CS|W | 10% | -12 | +4 | +8 | +16 | no |
| carry-CS|W | 30% | -35 | -2 | +16 | +23 | no |
| carry-TS|W | 10% | -12 | -3 | +5 | +11 | no |
| carry-TS|W | 30% | -37 | -23 | +10 | +32 | no |
| mom6-CS|W | 10% | -12 | -4 | +4 | +4 | no |
| mom6-CS|W | 30% | -35 | -18 | +4 | +9 | no |
| mom12-CS|W | 10% | -7 | -6 | +4 | +6 | no |
| mom12-CS|W | 30% | -22 | -19 | +5 | -6 | no |
| both(carry+mom12)-CS|W | 10% | -11 | +3 | +8 | +5 | no |
| both(carry+mom12)-CS|W | 30% | -32 | +3 | +12 | +13 | no |
| carry-CS|M | 10% | -11 | +4 | +7 | +17 | no |
| carry-CS|M | 30% | -33 | -1 | +17 | +21 | no |
| carry-TS|M | 10% | -11 | -3 | +6 | +11 | no |
| carry-TS|M | 30% | -34 | -22 | +12 | +32 | no |
| mom6-CS|M | 10% | -14 | +2 | +4 | +1 | no |
| mom6-CS|M | 30% | -42 | -13 | +2 | +3 | no |
| mom12-CS|M | 10% | -8 | -7 | +2 | +4 | no |
| mom12-CS|M | 30% | -25 | -22 | +3 | -6 | no |
| both(carry+mom12)-CS|M | 10% | -9 | +6 | +7 | +8 | no |
| both(carry+mom12)-CS|M | 30% | -27 | +3 | +12 | +16 | no |

## 4. Robustness against the other pair definition
| book | vs live config (clean/H1/H2) | vs B.Cfg() (clean/H1/H2) |
|---|---|---|
| carry-CS|W | -0.01 / -0.26 / -0.04 | -0.02 / -0.20 / -0.04 |
| carry-TS|W | -0.05 / -0.54 / -0.06 | -0.04 / -0.42 / -0.06 |
| mom6-CS|W | -0.31 / 0.21 / 0.20 | -0.31 / 0.22 / 0.18 |
| mom12-CS|W | -0.04 / 0.20 / 0.18 | -0.04 / 0.25 / 0.16 |
| both(carry+mom12)-CS|W | 0.02 / -0.31 / -0.06 | 0.02 / -0.18 / -0.07 |
| carry-CS|M | 0.01 / -0.53 / 0.05 | 0.00 / -0.41 / 0.07 |
| carry-TS|M | -0.04 / -0.54 / 0.05 | -0.03 / -0.41 / 0.05 |
| mom6-CS|M | -0.38 / 0.35 / -0.10 | -0.38 / 0.31 / -0.12 |
| mom12-CS|M | -0.09 / 0.21 / 0.13 | -0.09 / 0.25 / 0.13 |
| both(carry+mom12)-CS|M | -0.03 / -0.17 / 0.17 | -0.03 / -0.05 / 0.20 |

## 5. Plateau and 2x slippage (additive 20%, change in all-in Sharpe uplift)
Plateau variants (carry smoothing 16/26 days, momentum lookback x0.75 / x1.25) are in `F3_plateau.csv`; 2x slippage in `F3_slip2.csv`. Summary:
- Base all-in uplifts are -0.21..+0.05 (best: mom12-CS|W +0.05; clean -0.04, H1 +0.20, H2 +0.18; mom12-CS|M and both-CS|M +0.01), so there is no uplift to hold on a plateau. The four mom12 neighbours (W and M) range -0.07..+0.12 all-in and their clean uplift is negative in 3 of 4.
- At 2x slippage every book's uplift is within +-0.03 of its 1-tick value (mom12-CS|W standalone pair-window Sharpe falls to 0.43; carry books are negative standalone at 2x).

## 6. Reading
- **Carry has no edge in this window** (standalone Sharpe -0.09..+0.11 on clean, negative in H1 for every carry book). Its 2013-2026 Sharpe is -0.06..+0.30 (carry-CS|M best, 0.30), below the own-null p95 of 0.44-0.51 for the full sample.
- **The hedge pattern is real but unpaid:** the carry-CS books have worst-decile correlation -0.12..-0.17 and the sleeve earned about +$26k..+$31k a week (pair-vol scaled) in the pair's 17 worst weeks. But the all-in Sharpe change is -0.05 and H1 is -0.26..-0.53, so the P&L given up elsewhere outweighs it. Shift-null ranks are 0.80-0.94, below 0.95 (gate for hedge claims).
- **Momentum:** only the 12-month versions are positive (2013-2026 Sharpe 0.53/0.69, H1/H2 positive, clean negative); they fail the own-null p95 on the pair window (1.19-1.22) and have positive worst-decile correlation +0.13..+0.20 (they lose when the pair loses). mom6-CS is the worst book (clean Sharpe -1.4..-1.7).
- **Constant-risk:** see section 3; no INSURANCE cell clears worst-week or CVaR5 >= 20% at <= 5% net cost with clean and H1 not worse (count of INSURANCE rows: 0 of 40).
- **Small-sample:** the books trade 72-348 times in the pair window (two carry-TS books and carry-CS|M have fewer than 100: flagged); the 2013-2026 Sharpe is reported beside each.
- **Executability:** all 26 products are CME Group futures (CME/CBOT/NYMEX/COMEX), so executable at NinjaTrader Brokerage via Rithmic is assumed Y from general knowledge (not verified per product). Fractional contract counts would have to be rounded; at the pair-vol scale (~1.5x the $7k-risk book) the both(carry+mom12)-CS|W sleeve at 20% share needs about $80,964 average margin (assumptions above). Not worth specifying: nothing passes.
- **Fill model/slippage:** daily bars, market-on-open fills at the next open (T4-A convention), 1 tick/side, no queue model; the weekly/monthly rebalance is not netted against the pair's lots.
- **Caveats:** carry uses a spacing proxy and the v.1-validity flag (uses the ex-post roll sequence to label which contract is deferred, not prices); sleeve scaling uses the full-span weekly volatility ratio, as in T3/T4; UNTOUCHED not read.

Runtime: 157 s compute on 4 workers (10 books, 2,000 null draws, 24 plateau variants, 10 2x-slippage runs).

DONE C1_F3
