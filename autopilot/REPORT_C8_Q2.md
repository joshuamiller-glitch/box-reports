# REPORT C8-Q2 — TIME-OF-DAY DRIFT SLEEVES (NQ, ES)

**Verdict: NO. FOUND 0, LEAD 0.** All 160 scored rows (20 selected cells x 4 shares x 2 framings) are NO. Grid registered in `PREREG_AUTOPILOT.md` ('CYCLE 8' + 'C8-Q2 exact cell list') before the first full run. Status `outputs/autopilot/status/C8_Q2.txt`.

## What was run
- 1-minute bars 2013-2026 (`data/autopilot/ohlcv1m`), CME trading day (18:00 ET to 17:00 ET, label = ET date of t+6h), 45 full 30-minute ET buckets (18:00 ... 16:00 start). Entry = open of the bucket's first 1-min bar (within 3 min), exit = open at the next bucket start; both prices must share an instrument_id (roll-safe). Bars missing within 3 minutes drop the day for that bucket.
- 178 cells: variant U (direction = sign of the 2013-2022 mean bucket return, 45/instrument) and variant C (direction = sign of the prior bucket's return x s, s = +1 momentum / -1 reversal fitted on 2013-2022, 44/instrument). Selection on 2013-2022 only: >= 7 of 10 years with positive gross mean in the chosen direction, top 10 per instrument by 2013-2022 NET weekly Sharpe. Qualifying cells: NQ 37, ES 41.
- Costs per round trip: NQ 1 tick/side = 0.50 pt + $4.36 = **0.72 pt**; ES 0.5 tick/side = 0.25 pt + $4.36 = **0.34 pt** (assumed commission). Gross and net both shown (gross Sharpe is also in `cells.pkl`).
- Pair window (clean 2023-08..2025-07, H1, H2) read once, only for the 20 selected cells. Baseline = B.Cfg(wk_floor=8,wk_loss_pb=None) computed in a process that never imported b10_core (clean 1.46 / H1 2.83 / H2 2.30); robustness vs B.Cfg() in `dsh_def` (scores.pkl) gives the same verdict. Sleeve scaled to the pair's clean weekly volatility (t3_score convention).

## The 20 selected cells (gross vs net, then pair window read once)
| sym | var | bucket (ET) | dir | yrs ok /10 | trades 13-22 | gross pts/trade | cost pts/RT | fit net Sh 13-22 | net Sh clean | H1 | H2 | pair win | pair-win null p95 | 2x-slip pair-win | contracts to match pair vol | worst-decile corr |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ | U | 14:30 | +1 | 8 | 2491 | 1.29 | 0.72 | 0.38 | -0.24 | 2.16 | -2.31 | -0.62 | 0.52 | -0.78 | 31 | 0.24 |
| NQ | U | 09:30 | +1 | 8 | 2565 | 1.00 | 0.72 | 0.13 | -0.46 | -0.45 | 0.35 | -0.21 | 0.52 | -0.29 | 17 | 0.40 |
| NQ | C | 14:00 | -1 | 8 | 2452 | 0.85 | 0.72 | 0.09 | -0.38 | 0.77 | 1.08 | 0.15 | 0.52 | -0.04 | 35 | -0.10 |
| NQ | U | 10:30 | -1 | 7 | 2565 | 0.69 | 0.72 | -0.02 | 0.18 | 2.98 | -1.14 | 0.35 | 0.52 | 0.22 | 26 | -0.06 |
| NQ | C | 12:00 | +1 | 7 | 2541 | 0.66 | 0.72 | -0.04 | -0.50 | -1.10 | -0.30 | -0.55 | 0.52 | -0.73 | 33 | -0.58 |
| NQ | C | 10:00 | +1 | 8 | 2550 | 0.63 | 0.72 | -0.05 | -0.16 | 1.95 | -0.46 | 0.07 | 0.52 | -0.04 | 21 | 0.19 |
| NQ | C | 18:30 | -1 | 10 | 2450 | 0.65 | 0.72 | -0.10 | -0.65 | 0.98 | -3.77 | -1.26 | 0.52 | -1.60 | 77 | 0.17 |
| NQ | U | 11:00 | +1 | 7 | 2565 | 0.50 | 0.72 | -0.13 | 0.30 | 0.17 | -0.10 | 0.19 | 0.52 | 0.04 | 27 | 0.29 |
| NQ | U | 00:30 | +1 | 9 | 2536 | 0.62 | 0.72 | -0.15 | -1.22 | -0.60 | -1.50 | -1.20 | 0.52 | -1.63 | 81 | -0.08 |
| NQ | C | 06:00 | -1 | 7 | 2501 | 0.58 | 0.72 | -0.16 | -0.23 | -0.12 | -0.28 | -0.23 | 0.52 | -0.46 | 41 | -0.19 |
| ES | C | 15:30 | +1 | 7 | 2406 | 0.39 | 0.34 | 0.09 | -1.02 | 1.15 | -1.26 | -0.75 | -0.06 | -1.07 | 47 | 0.36 |
| ES | C | 14:00 | -1 | 8 | 2374 | 0.35 | 0.34 | 0.03 | -0.34 | -0.02 | 0.69 | -0.10 | -0.06 | -0.49 | 56 | -0.08 |
| ES | C | 18:30 | -1 | 9 | 2381 | 0.30 | 0.34 | -0.16 | -0.84 | -0.68 | -2.07 | -1.17 | -0.06 | -1.93 | 145 | 0.17 |
| ES | U | 15:30 | -1 | 7 | 2491 | 0.24 | 0.34 | -0.18 | -0.62 | 0.20 | -0.08 | -0.39 | -0.06 | -0.71 | 46 | -0.17 |
| ES | C | 09:30 | -1 | 7 | 2425 | 0.22 | 0.34 | -0.20 | 1.68 | 0.13 | -0.35 | 0.91 | -0.06 | 0.63 | 44 | 0.09 |
| ES | U | 09:30 | +1 | 7 | 2565 | 0.20 | 0.34 | -0.26 | -0.45 | 0.74 | 0.10 | -0.13 | -0.06 | -0.42 | 41 | 0.55 |
| ES | C | 12:00 | +1 | 7 | 2481 | 0.23 | 0.34 | -0.32 | -0.68 | 0.59 | 0.85 | -0.06 | -0.06 | -0.49 | 68 | -0.67 |
| ES | U | 12:30 | +1 | 8 | 2513 | 0.15 | 0.34 | -0.57 | -0.72 | -2.32 | -0.93 | -1.03 | -0.06 | -1.48 | 68 | -0.04 |
| ES | C | 11:30 | -1 | 7 | 2491 | 0.13 | 0.34 | -0.59 | -1.24 | -0.32 | -1.08 | -1.01 | -0.06 | -1.42 | 64 | 0.24 |
| ES | C | 03:00 | -1 | 8 | 2317 | 0.12 | 0.34 | -0.60 | -1.45 | 0.31 | -1.81 | -1.30 | -0.06 | -1.83 | 78 | -0.44 |

Reading: gross edge per trade is 0.1-1.3 pt; the cost is 0.34-0.72 pt per round trip, so net edge is thin or negative even in the fit span. Only 5 of 20 cells have a positive net Sharpe in the pair window (10 positive gross). Mean net Sharpe in the pair window is -0.42; at 2x slippage -0.73. The sleeves need 17-145 contracts to match the pair's volatility, which is not a practical size (margin well above the account).

## Additive uplift vs the pair (all 20 cells)
| share | cells with +0.10 on clean,H1,H2 | clean >=0.10 | H1 >=0.10 | H2 >=0.10 | bootstrap lo>0 | best all-in dSharpe | worst |
|---|---|---|---|---|---|---|---|
| 10% | 0/20 | 1 | 5 | 1 | 0 | +0.064 | -0.176 |
| 20% | 0/20 | 1 | 6 | 3 | 0 | +0.104 | -0.372 |
| 30% | 0/20 | 1 | 6 | 3 | 0 | +0.123 | -0.578 |
| 50% | 0/20 | 1 | 5 | 2 | 0 | +0.114 | -0.972 |

No cell reaches +0.10 on clean, H1 and H2 together at any share; every bootstrap lower bound is <= 0. Constant-risk (30% share): all-in net changes -57% to -14% (limit -5%) and worst week changes -181% to +0% — no INSURANCE. Worst-decile correlation with the pair: -0.67 to +0.55 on 17 weeks (too noisy to call anything a hedge). Plateau (adjacent buckets keep >= 75% of the uplift): 0 of 20 cells.

## Nulls
- Random-bucket null (500 draws, random bucket and direction, net weekly Sharpe p95): 1 of 20 cells beat it in the pair window (the cell is ES C 09:30 (pair-window Sharpe +0.91, 20% additive uplift +0.25 clean, -0.14 H1, -0.14 H2)), and 15 of 20 beat it on 2013-2022 (by construction of the selection). In the pair window the null p95 is +0.52 (NQ) and -0.06 (ES); a cell above the null but with a negative or sub-0.10 uplift is not a candidate.
- False-survivor test (200 timing-destroyed replicates per instrument; per-day random circular rotation of the bucket sequence, whole selection repeated):

| inst | real qualifying | replicate qualifying (mean) | real top-10 mean net Sharpe 13-22 | replicate top-10 mean / p95 | real rank |
|---|---|---|---|---|---|
| NQ | 37 of 89 | 28.3 (p of >= real: 0.040) | -0.004 | -0.048 / +0.052 | 0.745 |
| ES | 41 of 89 | 32.0 (p of >= real: 0.025) | -0.275 | -0.431 / -0.331 | 0.995 |

There are somewhat more year-consistent cells than chance gives (NQ p=0.04, ES p=0.025) — a weak sign of persistent bucket structure in 2013-2022 — but the NQ top 10 is at chance (rank 0.75, below p95) and ES's top-10 average net Sharpe is negative (-0.27); ranking above a worse null that loses to cost is not an edge.

## Why it fails, plainly
Time-of-day drift exists in gross terms (the best NQ cell, 14:30-15:00 long, earns 1.29 pt gross per trade on 2013-2022, Sharpe 0.86 gross) but cost takes more than half of it, it does not persist (that cell: clean -0.24, H1 +2.16, H2 -2.31 net Sharpe) and no cell adds Sharpe to the pair on all three spans.

## Executability, margin, assumptions
- NQ/ES futures: executable at NinjaTrader Brokerage via Rithmic (general knowledge, not checked against the product list). A bucket sleeve is a simple NT8 time-based strategy. Margin assumed ~$22k NQ / ~$15k ES per contract (unverified); at the required 17-145 contracts it is unusable.
- Slippage 1 tick/side NQ, 0.5 ES, commission $4.36/RT assumed (not calibrated to live fills); no netting against the pair's lots; bucket returns use bar opens, so fills inside a bucket's first/last seconds are not modelled.
- Runtime: about 56 s of compute (1 process; the 2 x 200 replicates dominate). Code `ap_c8_q2_core.py`, `ap_c8_q2_run.py`, `ap_c8_q2_rep.py`; data `outputs/autopilot/c8/q2/`.

DONE C8_Q2
