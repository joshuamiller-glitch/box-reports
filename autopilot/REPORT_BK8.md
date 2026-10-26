# REPORT BK8 - LATE-DAY FADE TO THE 0DTE PIN, standalone NQ sleeve (BACKLOG2 #55; D03 x M1/M3, H3)
**Verdict: NO. FOUND 0. Selected (870, 0.25, 2.0) (clean standalone weekly Sharpe among 8 cells, >= 60 clean trades): standalone Sharpe clean 0.58 / H1 1.26 / H2 -1.28 / all-in 0.51; additive uplift at 20% of pair risk +0.09 / +0.12 / -0.04 (needed +0.10 each), all-in +0.06; bootstrap 90% CI [-0.10, +0.24]; own random-date null p95 on standalone clean Sharpe +1.01 (real rank 0.83); plateau 0.50.** Pre-registered in PREREG_AUTOPILOT.md / PREREG_BK.md before the first scored run.

## Mechanism (one sentence) and set-up
- Mechanism: 0DTE hedging and pinning pull the index toward the largest-volume strike in the last two hours, so a stretched price relative to the pin mean-reverts to it before the close.
- Rule: at 14:30 ET each RTH day, pin = strike with the largest cumulative 0DTE (NDXP) traded size through the last completed 30-min slot among strikes within 100 pts of the NDXP forward (PREREG amendment 1); distance D = pin - price (K - Fp); if |D| >= 0.25 x ADR20 (previous 20 sessions' RTH high-low mean) fade toward the pin: long if D > 0, short if D < 0; target = pin level (limit, needs 1 tick trade-through), stop = 2.0 x threshold from the entry, time exit 15:55 ET open; one trade per day; fill: next 1-minute open + 1 tick adverse, stop-market with 1 tick slippage, $4.36 per contract round trip; sized so a full stop = $9,600 (library standard; contracts = 9,600/(stop pts x $20)). Same-bar stop and target resolves to the stop (conservative).
- Data: OPRA NDXP trades (30-min strike tables) 2022-03..2026-10-16 (data/autopilot/opt0dte); NQ 1-minute harness series. Price distance is measured against the NDX-equivalent forward, so the NQ-NDX basis cancels.
- Additive framing: pair (ST+HM, B.Cfg(wk_floor=8,wk_loss_pb=None), clean process, clean 1.46 / H1 2.83) plus share x scale x sleeve, scale chosen so the sleeve's clean weekly sd equals the pair's (share = fraction of pair risk). Baseline reproduced. small-sample flag: no (256 trades 2023-02..2026-10; 160 clean).

## Grid (selection on clean standalone weekly Sharpe, trades >= 60)
| cell (T min ET, x in ADR, k) | clean standalone Sharpe | clean trades |
|---|---|---|
| (840, 0.15, 1.0) | -1.10 | 275 |
| (840, 0.15, 2.0) | -0.51 | 275 |
| (840, 0.25, 1.0) | -0.76 | 158 |
| (840, 0.25, 2.0) | +0.04 | 158 |
| (870, 0.15, 1.0) | +0.43 | 277 |
| (870, 0.15, 2.0) | +0.13 | 277 |
| (870, 0.25, 1.0) | +0.29 | 160 |
| (870, 0.25, 2.0) **(selected)** | +0.58 | 160 |

## Result for the carried cell
| span | pair Sharpe | sleeve standalone Sharpe | pair + 20% sleeve | uplift @20% | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 0.58 | 1.55 | +0.087 | +0.074 |
| H1 | 2.83 | 1.26 | 2.95 | +0.121 | +0.110 |
| H2 | 2.48 | -1.28 | 2.44 | -0.043 | -0.044 |
| all | 1.90 | 0.51 | 1.96 | +0.065 | +0.054 |

Uplift by share (clean/H1/H2/all-in): 10% +0.05/+0.07/-0.02/+0.04; 20% +0.09/+0.12/-0.04/+0.06; 30% +0.11/+0.15/-0.07/+0.07; 50% +0.11/+0.14/-0.13/+0.06

## Gate checklist
- uplift>=0.10 clean/H1/H2 at 20% share: FAIL
- worst week of combination not worse than pair by more than share x |pair worst|: FAIL
- own timing-destroyed null p95 on standalone Sharpe (clean and all-in): FAIL
- bootstrap 90% CI of all-in additive uplift > 0: FAIL
- plateau >= 75% of neighbours keep >= 75% of uplift: FAIL
- 2x slippage uplift >= +0.10 each span: FAIL
- worst-decile corr with pair <= +0.30: PASS
- own null (200 random-date reassignments of the same direction/distance/stop triples): standalone clean Sharpe p95 +1.01 vs real +0.58 (rank 0.83); all-in p95 +0.64 vs real +0.51 (rank 0.92); additive-uplift null p95 clean/H1/H2/all +0.17/+0.35/+0.33/+0.08
- plateau neighbours (all-in uplift @20%): x*0.75 +0.08; x*1.25 +0.05; k*0.75 +0.02; k*1.25 +0.08; T-15 -0.02; T+15 +0.16 -> 50% keep >= 75% of +0.06
- worst week: combination all-in -102.1k vs pair -82.5k (share 20%); weekly corr sleeve-pair -0.02, worst-decile corr -0.05 (hedge claim not made, shift null reported-only and not run)

## Replication leg
- H0 2023-02-10..07-31 (59 trades): standalone Sharpe -0.97, additive uplift -0.31 -> does not hold.
- Alternating months: select (840, 0.25, 2.0) (-0.079) reads +0.014; select (870, 0.15, 2.0) (+0.295) reads -0.311 -> does not hold.
- Cross-instrument ES (SPX/SPXW tables): not run - the NQ cell fails the Sharpe gate on H2 / null; to be run if the cell is revisited. Newest live weeks (2026-10-09..16): report-only, see library series.
- Replications counted: 0 of 2 required. ERA FLAG: not testable (0DTE flow data from 2022; the pair has no pre-2023 rows); cost decomposition: not meaningful without a pre-2022 sample; cost per trade 1 tick/side entry and exit + $4.36 per contract round trip (about 1.5% of a full-stop risk of $9,600 at the mean stop).

## Insurance metrics (weekly, USD; sleeve20 = the 20% sleeve alone)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.55 | 2.94 | 4.97 | -87.4k | -82.9k | 289k | -102.1k | 47.6 |
| clean sleeve20 | 0.58 | 0.85 | 0.71 | -26.4k | -22.0k | 148k | -39.0k | 32.4 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 2.95 | 6.83 | 4.23 | -61.3k | -60.1k | 152k | -64.6k | 39.3 |
| H1 sleeve20 | 1.26 | 1.96 | 1.71 | -20.9k | -17.4k | 28k | -26.6k | 25.0 |
| H2 pair | 2.48 | 5.08 | 3.77 | -81.1k | -79.2k | 217k | -82.5k | 41.7 |
| H2 cand | 2.44 | 4.94 | 3.73 | -81.1k | -78.1k | 213k | -82.5k | 41.7 |
| H2 sleeve20 | -1.28 | -1.34 | -0.93 | -13.9k | -8.9k | 27k | -19.5k | 8.3 |
| all pair | 1.90 | 3.71 | 9.79 | -79.2k | -78.2k | 280k | -82.5k | 42.3 |
| all cand | 1.96 | 3.86 | 9.95 | -85.1k | -80.5k | 289k | -102.1k | 45.2 |
| all sleeve20 | 0.51 | 0.74 | 0.87 | -24.7k | -20.4k | 148k | -39.0k | 25.6 |

## Sized dollars
- Standard size ($9,600 per full stop): worst single day $-9,655; worst trade-day $-9,655; at the 20% share (x2.02) worst day $-19,536. Mean stop 109.9 pts -> about 4.5 NQ contracts per standard-size trade.

## Causality check
- Pin from slots completed before the entry minute and Fp from records in the five minutes before it (same function as BK7, whose poison test (8 rows, tables truncated at the entry) passed); ADR20 is the mean of the previous 20 sessions; entry at the next bar open; target level from the close of the bar before entry. No H1/H2 information entered selection.

## Executability
A spec exists (pin from a real-time NDXP strike-volume table), but NDXP trades are OPRA data: not available through Rithmic/NinjaTrader Brokerage; an external options tape and a file/socket bridge into NT8 would be required. Margin: standard 8-contract-equivalent NQ intraday margin for the 2-hour hold.

## Reading
The sleeve's clean standalone Sharpe (+0.58) is the maximum of eight cells; the same rule beats a random-date null of its own structure at rank 0.83, and on H2 its additive contribution is -0.04. Gates failed: uplift>=0.10 clean/H1/H2 at 20% share, worst week of combination not worse than pair by more than share x |pair worst|, own timing-destroyed null p95 on standalone Sharpe (clean and all-in), bootstrap 90% CI of all-in additive uplift > 0, plateau >= 75% of neighbours keep >= 75% of uplift, 2x slippage uplift >= +0.10 each span.

Files: code/census/night_ins/ap_bk8.py, ap_bk8_rep.py; outputs/autopilot/bk/bk8/.

DONE BK8
