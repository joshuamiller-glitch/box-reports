# REPORT C11-DIP-REP2 - replication of the ES dip-buy lead under GATE AMENDMENT 2 (ERA)

**FOUND-PENDING (replicated by 2 of 4 tests, both marginal; live weeks still needed). Not FOUND.** ES RSI(2)<5 & close>SMA200, exit 5 bars, 3xATR20 stop, one pre-selected cell (C11-DIP, selection on clean only). With 2013-22 no longer a gate, the only items that kept it a LEAD were the small-sample flag (23 pair-window trades; flag, not a gate) and the 2013-22 replication (dropped). All seven pair-window gates passed in REPORT_C11_DIP.md (additive 20% uplift +0.27/+1.06/+0.25, own-null p95 2.05 vs 1.22, boot lo +0.20, plateau 7/8, 2x slippage pass, wd corr +0.10, worst week +3.7% vs 20%). Protocol pre-registered in PREREG_AUTOPILOT.md ("C11-DIP REPLICATION UNDER GATE AMENDMENT 2", before running); code code/census/night_ins/ap_c11_rep2.py, data outputs/autopilot/c11/dip_rep2.pkl. Fill model as C11-DIP (entry/exit at the daily close, stop at min(stop, open) minus a tick, 1 tick/side + $4.36 RT).

| test (needs same sign and >= 50% of the ES all-in uplift +0.37) | result | verdict |
|---|---|---|
| (a) live weeks | window 2026-10-14+ is empty | pending |
| (b) H0 2023-02-01..07-31 | only 2 trades; uplift -0.002 (pair Sharpe 0.66 -> 0.66) | NOT held (uninformative) |
| (c) cross-instrument 2023-26: same frozen rule on NQ, RTY, YM, sized to equal dollar ATR risk | NQ +0.20 (22 trades), RTY +0.18 (18), YM +0.14 (21) all-in; equal-weight average +0.19 (>= 50% of +0.37 = 0.18); clean-window uplift of the average only +0.01 (the effect is H1/H2, as for ES) | HELD (marginal: 0.19 vs 0.18 threshold, 3 of 3 signs positive) |
| (d) alternating months in 2023-26, selection among the 64 C11 cells | odd -> even: selects the frozen ES cell itself, even-month uplift +0.39 (= reference); even -> odd: selects ES RSI5/3-bar/stop2, odd-month uplift +0.00 vs ES-frozen-cell reference +0.32; mean +0.20 vs 50% of mean reference (+0.35 x 0.5 = 0.18) | HELD under the pre-registered mean rule (marginal; the even -> odd direction is ~0) |

**ERA FLAG (2013-22, from REPORT_C11_DIP): negative / flat pre-2023** (standalone weekly Sharpe 0.08 on 40 trades, 2013-26 0.80, additive uplift +0.01). Mechanism (one sentence): equity-index dips inside an uptrend recover within a week (liquidity-provision / retail dip-buying) - plausibly dependent on the modern retail/0DTE flow structure; the pre-2023 absence is consistent with that.

Reading: two of four replication tests hold, both by thin margins, and one (H0) is uninformative for lack of trades. By the letter of Amendment 2 it is FOUND-PENDING-REPLICATED; I would not trust it before the live-weeks test: the sleeve has 23 ES trades (84 across four indices) in 3.2 years, the 2024 results come from 9 trades, and the replication hinges on index co-movement (NQ, RTY and YM dip signals are highly correlated with ES's). False-discovery context: 64 cells examined in C11, one chosen on clean.

DONE C11-DIP-REP2
