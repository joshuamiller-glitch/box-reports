# DS3_ALPHA_BREADTH - T-ALPHA parts 3 and 4 (W-AL2). FIRST PAGE: inventory, quotes, audit, costs
VERDICT (data ends 2026-11-13; plain): FIRST PASS, no PASS claimed. All 1-minute data for 28 outright futures is on the box and free to top up; costs are the binding constraint: at a usable single-market IC of 0.02 only NQ (about 60 min) and, at 120 min, GC, SI and HO clear 2x the all-in round-trip cost; rates, FX, grains and the other metals/energies need an IC of 0.1 to 1.8 at 5-120 min, i.e. they cannot be traded by crossing the spread at these horizons. Per-market IC is in the section below as it lands.

All numbers here are FIRST PASS and use the 1-minute bar continuous series SYM.v.0 (Databento volume-roll). Code code/th_alpha_breadth (inventory.py, audit1.py, costs.py, quotes.py, forecast.py); bulk /mnt/l2/l2vast/_alpha_breadth. W-AL1's pipeline (code/th_alpha: audit.py, wf.py, score.py) did not exist when this page was written; forecast.py here is a ridge-only stand-in with the same targets and scoring and will be swapped for theirs.

## 1. INVENTORY (what is on the box)
1-minute bars, data/autopilot/ohlcv1m/<SYM>_<year>.dbn.zst, 2013-01..2026-10-16, plus tops-ups data/ext_20261017 (to 10-17), data/ext_20261110 (6E 6J CL ES GC MBT NKD NQ RTY YM ZB ZN to 11-10), data/ext_20261113 and ext_20261113m (NQ ES RTY YM GC SI CL to 11-13). Series are SYM.v.0 (lead-volume continuous), one contract id per bar; the bars-per-day column is minutes with a print per calendar day of data (23-hour sessions; 1,440 is the ceiling).

| sym | start | end | since2304_rows | bars_per_day | n_rolls | gaps_gt10min_in_session | stale5_runs | maxrun_same_close |
|---|---|---|---|---|---|---|---|---|
| 6A | 2013-01-02 | 2026-10-16 | 1219976 | 1103.0 | 14 | 3184 | 2731 | 17 |
| 6B | 2013-01-02 | 2026-10-16 | 1144334 | 1035.0 | 14 | 3827 | 6663 | 28 |
| 6C | 2013-01-02 | 2026-10-16 | 1114243 | 1007.0 | 14 | 4067 | 8559 | 31 |
| 6E | 2013-01-02 | 2026-11-10 | 1253292 | 1112.0 | 14 | 2995 | 2856 | 17 |
| 6J | 2013-01-02 | 2026-11-10 | 1249063 | 1108.0 | 14 | 3076 | 6197 | 25 |
| CL | 2013-01-01 | 2026-11-13 | 1263792 | 1120.0 | 43 | 3108 | 1328 | 16 |
| ES | 2013-01-02 | 2026-11-13 | 1280276 | 1134.0 | 14 | 4878 | 985 | 15 |
| GC | 2013-01-01 | 2026-11-13 | 1269197 | 1125.0 | 17 | 4040 | 184 | 11 |
| HE | 2013-01-02 | 2026-10-16 | 242797 | 273.0 | 29 | 8612 | 301 | 91 |
| HG | 2013-01-01 | 2026-10-16 | 1186182 | 1074.0 | 18 | 4055 | 1149 | 14 |
| HO | 2013-01-01 | 2026-10-16 | 926227 | 839.0 | 55 | 30775 | 9 | 6 |
| LE | 2013-01-02 | 2026-10-16 | 243891 | 274.0 | 35 | 8950 | 67 | 115 |
| MBT | 2026-10-12 | 2026-11-10 | 28812 | 960.0 | 1 | 201 | 1 | 5 |
| NG | 2013-01-01 | 2026-10-16 | 1125259 | 1019.0 | 44 | 8142 | 2995 | 22 |
| NKD | 2013-01-02 | 2026-11-10 | 850893 | 755.0 | 14 | 14645 | 554 | 11 |
| NQ | 2013-01-02 | 2026-11-13 | 1280548 | 1134.0 | 14 | 4995 | 1 | 6 |
| PL | 2013-01-01 | 2026-10-16 | 1102996 | 999.0 | 14 | 11385 | 72 | 8 |
| RB | 2013-01-01 | 2026-10-16 | 911004 | 825.0 | 77 | 35963 | 8 | 8 |
| RTY | 2017-07-09 | 2026-11-13 | 1240674 | 1099.0 | 14 | 4416 | 151 | 15 |
| SI | 2013-01-01 | 2026-11-13 | 1218570 | 1080.0 | 18 | 5416 | 1514 | 15 |
| YM | 2013-01-02 | 2026-11-13 | 1261416 | 1116.0 | 14 | 4993 | 130 | 9 |
| ZB | 2013-01-02 | 2026-11-10 | 1089077 | 966.0 | 14 | 6715 | 27913 | 67 |
| ZC | 2013-01-02 | 2026-10-16 | 726066 | 816.0 | 24 | 10709 | 14238 | 38 |
| ZF | 2013-01-02 | 2026-10-16 | 1121374 | 1014.0 | 14 | 7977 | 24507 | 46 |
| ZN | 2013-01-02 | 2026-11-10 | 1189582 | 1056.0 | 14 | 3965 | 28049 | 66 |
| ZS | 2013-01-02 | 2026-10-16 | 827256 | 930.0 | 17 | 5264 | 5555 | 67 |
| ZT | 2013-01-02 | 2026-10-16 | 1041704 | 942.0 | 14 | 32229 | 27880 | 87 |
| ZW | 2013-01-02 | 2026-10-16 | 736773 | 828.0 | 20 | 10198 | 5649 | 96 |

Gaps and holes (action items):
- RTY starts 2017-07-09: 2013-01..2017-07 is MISSING (T-INSTR-2 quoted it earlier); ohlcv-1m is $0.00 on the plan.
- Ended 2026-10-16 (4 weeks short of today): 6A 6B 6C ZF ZT ZC ZS ZW HG PL HO RB NG LE HE. Ended 2026-11-10: 6E 6J NKD ZN ZB.
- HE, LE, ZC, ZS, ZW have day-session-only bars (about 270 to 930 bars per day).
- Not on the box as 1-minute history: MES MNQ M2K MYM MCL MGC, CME BTC and ETH futures. MBT only 2026-10-12..11-10 (top-up of 30 days). All $0.00 for ohlcv-1m/1s in DS3_ALPHA_QUOTES.md.
- Tape (trades/mbp-10): NQ full (raw/NQ, NQ_mbo 247 GB L3, NQ_mbp10_extra to 11-13); ES and RTY hist replicas (/mnt/l2/l2vast/_hist_replica 42 GB, 970 days 2023-02-01..2026-10-30; _hist_replica_RTY 11 GB, 4 year folders; _hist_replica_ES is empty (4 KB)); raw/ES/back+ext 16 GB. ZN ZB 6E: ohlcv-1m only (25 MB, 2023-04..2026-11 c.0 series, pulled at $0.00); there is NO tbbo/mbp for ZN ZB 6E 6J GC CL YM NKD on the box (data/databento/{CL,GC,ZN} hold bars, trade folders and roll tables only).
- Unusual Whales: /mnt/l2/l2vast/uw/ohlc1m and spot_1m for SPY QQQ IWM DIA GLD SLV USO XLE XOP GDX and megacaps (an ETF-based clue for metals/oil/indices), etf_tide, flow alerts.
- ETH/BTC futures: none on the box beyond MBT 30 days.

## 2. DATA AUDIT (item 15), per market, since 2023-04
Findings:
1. Roll handling: every series has one instrument_id per bar; the bar that changes id carries a spread jump 5x to 140x the normal 1-minute move (columns in audit1.csv: roll_bar_absret_mean_bp vs nonroll). Index/FX/rates roll quarterly (14 rolls), metals mixed (17-18), energies monthly (43 CL, 44 NG, 55 HO, 77 RB). forecast.py zeroes the return on every roll bar (back-adjusted log price) and never builds a target across a roll as a price change.
2. Contamination bug found and fixed: my first inventory pass merged the 1-second tail files (ext_20261113 ohlcv1s) into the 1-minute series, which gave ES/NQ/RTY/CL/GC 2,100 bars per day and 1.1 million non-minute timestamps. Fixed (only ohlcv1m_* files merged); audit rerun shows nonminute_ts = 0 for all 28. Anyone who read the earlier ES/NQ minute counts from a merged file should recheck.
3. Stale prints: a bar with unchanged close for >=5 consecutive minutes is normal in thin markets: ZT 27,880 runs (max 87 min), ZN 28,049, ZB 27,913, ZF 24,507, ES 16,025 (illiquid overnight, max 27), ZW/ZS/ZC 5,500-14,000. These minutes carry zero return and are excluded from targets unless a real bar exists at t and at t+h.
4. Session gaps: gaps over 10 minutes inside a session: 3,000-5,000 for liquid index/FX/metals, 30,000+ for HO, RB, ZT (the product has bars only when it trades). Daily 17:00-18:00 ET halt and weekends excluded by construction; holiday sessions appear as short days (not yet flagged separately).
5. Timestamp alignment to the second: all bar stamps are on the minute (ts_event = bar open, UTC). Cross-market features use the bar that OPENED at or before the decision minute, close known at t+1 min; the grid is the union minute index; no market uses a later bar than another. The sub-minute alignment of top-ups from 1-second files was not tested (ES/NQ/RTY/YM tails exist at both 1m and 1s: next step is to rebuild the minute bar from 1s and compare).
6. Look-ahead test (shift every input one bar later): run per market in forecast.py mode shift1 (inputs one minute stale); results in section 4 when it finishes. A jump in IC would flag a leak; a drop is expected from stale inputs.
7. Duplicates: 0 duplicate timestamps in all series after merge (the top-up overlap days were de-duplicated by timestamp keeping the later file).

## 3. COSTS (item 14), per market, round trip, in ticks and basis points
Fee grades: NT-published = FEES.md (ES 4.84, MES 1.78); 'proxy' = FEES.md proxies; 6E 5.30 from the FEES.md 6E addendum; everything labelled ESTIMATE is NOT measured: it is my reading of NT Lifetime commission 0.59/side + clearing 0.19 + routing 0.25 + a typical CME Globex non-member exchange fee for the product, and must be confirmed from an NT statement line. Half-spread is ASSUMED (0.5 tick for liquid, 1 tick for thin products) because there is no tbbo on the box for any market except ES/NQ/RTY (the tbbo quote is in DS3_ALPHA_QUOTES.md). Crossing both ways pays 2 half-spreads.
Required IC columns: the IC needed for the expected gross P&L per entry (IC x sigma_h x 0.8, Gaussian signal, one round trip per horizon) to equal 2x cost; sigma_h = last-12-month in-session 1-minute vol x sqrt(h) (random-walk scaling, an approximation). The last column is the shortest horizon among 5/15/30/60/120 at which an IC of 0.02 gives 2x cost.

| sym | price | tick_usd | fee_rt | fee_grade | cost_rt_usd | cost_rt_ticks | cost_bp | sig1m_bp | IC_for_2xcost_15m | IC_for_2xcost_60m | IC_for_2xcost_120m | min_h_for_IC0.02 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES | 7396.25 | 12.5 | 4.84 | NT-published | 17.34 | 1.39 | 0.47 | 2.34 | 0.129 | 0.065 | 0.046 | >120 |
| NQ | 28212.5 | 5.0 | 4.84 | proxy ES | 9.84 | 1.97 | 0.17 | 3.44 | 0.033 | 0.016 | 0.012 | 60 |
| RTY | 2799.7 | 5.0 | 4.84 | proxy ES | 9.84 | 1.97 | 0.7 | 3.56 | 0.128 | 0.064 | 0.045 | >120 |
| YM | 50143.0 | 5.0 | 4.84 | proxy ES | 9.84 | 1.97 | 0.39 | 2.33 | 0.109 | 0.054 | 0.038 | >120 |
| ZN | 110.2031 | 15.62 | 4.36 | ESTIMATE | 19.98 | 1.28 | 1.81 | 1.2 | 0.972 | 0.486 | 0.344 | >120 |
| ZB | 112.875 | 31.25 | 4.5 | ESTIMATE | 35.75 | 1.14 | 3.17 | 2.25 | 0.91 | 0.455 | 0.322 | >120 |
| ZF | 107.9609 | 7.81 | 4.2 | ESTIMATE | 12.01 | 1.54 | 1.11 | 0.71 | 1.01 | 0.505 | 0.357 | >120 |
| ZT | 103.5859 | 7.81 | 4.0 | ESTIMATE | 11.81 | 1.51 | 0.57 | 0.34 | 1.091 | 0.545 | 0.386 | >120 |
| 6E | 1.1616 | 6.25 | 5.3 | FEES.md addendum | 11.55 | 1.85 | 0.8 | 1.03 | 0.5 | 0.25 | 0.177 | >120 |
| 6J | 0.0064 | 6.25 | 5.3 | ESTIMATE=6E | 11.55 | 1.85 | 1.45 | 1.36 | 0.691 | 0.346 | 0.244 | >120 |
| 6B | 1.3412 | 6.25 | 5.3 | ESTIMATE=6E | 11.55 | 1.85 | 1.38 | 1.22 | 0.729 | 0.364 | 0.258 | >120 |
| 6A | 0.6998 | 10.0 | 5.3 | ESTIMATE=6E | 15.3 | 1.53 | 2.19 | 1.56 | 0.907 | 0.453 | 0.321 | >120 |
| 6C | 0.7222 | 5.0 | 5.3 | ESTIMATE=6E | 10.3 | 2.06 | 1.43 | 0.89 | 1.031 | 0.515 | 0.364 | >120 |
| GC | 4429.1 | 10.0 | 5.2 | ESTIMATE | 15.2 | 1.52 | 0.34 | 4.86 | 0.046 | 0.023 | 0.016 | 120 |
| SI | 67.56 | 25.0 | 5.2 | ESTIMATE | 30.2 | 1.21 | 0.89 | 11.26 | 0.051 | 0.026 | 0.018 | 120 |
| HG | 6.033 | 12.5 | 5.2 | ESTIMATE | 17.7 | 1.42 | 1.17 | 4.97 | 0.152 | 0.076 | 0.054 | >120 |
| PL | 1831.8 | 5.0 | 5.2 | ESTIMATE | 15.2 | 3.04 | 1.66 | 10.84 | 0.099 | 0.049 | 0.035 | >120 |
| CL | 85.36 | 10.0 | 5.2 | ESTIMATE (MCL 2.08 in FEES.md) | 15.2 | 1.52 | 1.78 | 9.63 | 0.119 | 0.06 | 0.042 | >120 |
| NG | 3.113 | 10.0 | 5.2 | ESTIMATE | 15.2 | 1.52 | 4.88 | 10.15 | 0.31 | 0.155 | 0.11 | >120 |
| RB | 2.966 | 4.2 | 5.2 | ESTIMATE | 13.6 | 3.24 | 1.09 | 8.17 | 0.086 | 0.043 | 0.031 | >120 |
| HO | 3.6057 | 4.2 | 5.2 | ESTIMATE | 13.6 | 3.24 | 0.9 | 10.89 | 0.053 | 0.027 | 0.019 | 120 |
| ZC | 453.75 | 12.5 | 4.6 | ESTIMATE | 17.1 | 1.37 | 7.54 | 5.51 | 0.883 | 0.442 | 0.312 | >120 |
| ZS | 1167.75 | 12.5 | 4.6 | ESTIMATE | 17.1 | 1.37 | 2.93 | 3.54 | 0.534 | 0.267 | 0.189 | >120 |
| ZW | 605.0 | 12.5 | 4.6 | ESTIMATE | 17.1 | 1.37 | 5.65 | 6.34 | 0.575 | 0.288 | 0.203 | >120 |
| LE | 233.35 | 10.0 | 4.8 | ESTIMATE | 24.8 | 2.48 | 2.66 | 5.88 | 0.292 | 0.146 | 0.103 | >120 |
| HE | 88.45 | 10.0 | 4.8 | ESTIMATE | 24.8 | 2.48 | 7.01 | 6.68 | 0.678 | 0.339 | 0.24 | >120 |
| NKD | 60595.0 | 25.0 | 4.84 | ESTIMATE=ES | 54.84 | 2.19 | 1.81 | 6.26 | 0.187 | 0.093 | 0.066 | >120 |
| MBT | 80885.0 | 0.5 | 1.6 | ESTIMATE | 2.6 | 5.2 | 3.21 | 6.69 | 0.31 | 0.155 | 0.11 | >120 |

Reading: a usable single-market IC is 0.01-0.03 (the order's own expectation). Only NQ (60 min), GC/SI/HO (120 min) pass at 0.02 when crossing the spread; ES needs IC 0.065 at 60 min because its tick is large relative to its 1-minute move. The long list with required IC above 0.3 (rates, FX, grains, NG, the micros' cost share is not shown) cannot be traded this way: for those the route is passive entries, longer horizons (daily-plus), or being a portfolio member whose cost is shared.
PASSIVE-ENTRY VERSION: not measured. Assumption set used for sizing only, to be replaced by tbbo/mbp-10 measurement: resting at the bid/offer saves the entry half-spread (0.5-1 tick) but fills only ~35-50% of orders within N=30 s, and filled orders are adversely selected (price moves through about 0.3 tick more often than not). The break-even fill rate and adverse selection can be measured on NQ, ES and RTY from the mbp-10 replicas now; for the other markets they require the tbbo purchase in the quotes page. Not claimed.
SMALL SIZE (addendum A): at 5-50 contracts the order is a few percent of the best-quote size in ES/NQ/ZN/6E/GC/CL (top-of-book sizes in tens to hundreds of contracts), and tens of lots in RTY/NKD/YM/6J; capacity is therefore not the constraint in the liquid markets, cost is. Not yet measured from depth; to be measured on NQ/ES/RTY only.

## 4. PER-MARKET FORECAST (item 16 / part 3 item 10) - status
First-pass ridge, walk-forward (14-day blocks from 2023-04-01, 4-year trailing window, 5-minute sampling, purge = horizon + 5 min, ridge penalty chosen on the last 200 days inside the training window only), features = every core market's return at lags 1/5/15/60/240 min scaled by trailing vol, own vol-ratio, volume z, 15-min range, clock. Running: ES controls (shift1, nonsense, planted), then RTY YM NKD 6J ZN ZB 6E GC SI CL NQ. Table below is updated when each finishes.

### 4a. First per-market IC (ridge stand-in, walk-forward 2023-04..2026-11-13, all sessions; Spearman IC vs raw forward return, t from day-clustered delta-method SE; FIRST PASS, written 19:50Z)
| market | 5 min | 15 min | 30 min | 60 min | 120 min |
|---|---|---|---|---|---|
| ES | 0.0334 (t 16.4) | 0.0127 (4.9) | 0.0068 (1.8) | 0.0044 (0.8) | -0.0003 (0.0) |
| RTY | 0.0225 (10.5) | 0.0058 (2.0) | 0.0035 (0.9) | 0.0007 (0.1) | -0.0092 (-1.2) |
| 6E | 0.0296 (13.8) | 0.0219 (7.9) | 0.0168 (4.4) | 0.0161 (2.9) | 0.0119 (1.6) |
Controls on ES, same pipeline: nonsense inputs (real features rolled by a random whole number of days, i.e. alignment destroyed) give IC 0.002, 0.0015, -0.0037, -0.0025, 0.0049 (all |t|<1.0): the pipeline does not manufacture IC. Inputs one minute stale (shift1): 0.0072, 0.0019, 0.0034, 0.0045, 0.0009: the 5-min ES IC falls from 0.033 to 0.007, so most of it lives inside the last minute (lead-lag and bid-ask effects in the 1-minute bars), is NOT a leak but also NOT a tradeable edge after costs (ES needs IC 0.22 at 5 min). Planted-edge check: a 0.02-correlated signal planted against the 30-min vol-scaled target moved the 30-min IC only from 0.0068 to 0.0124 (recovery about 60 pct when scored against the raw return): the ridge penalty grid (1e3..1e6 on standardised features) plus the raw-vs-scaled return mismatch shrinks it; the stand-in is therefore conservative, and W-AL1's plant()/ic_table in code/th_alpha is the proper check to rerun.
Plain reading so far: equity-index IC beyond 15 minutes is indistinguishable from zero in this first pass (ES, RTY); 6E is the exception with a slowly decaying IC 0.012-0.022 at 15-120 min (t 1.6-7.9), but 6E needs IC 0.18-0.5 to clear 2x cost when crossing the spread (costs table), so the gross edge does not cover costs. Not a PASS. Nothing here is net of cost.
Still running (explicit pids, nice 10, 2 threads each; logs /mnt/l2/l2vast/_alpha_breadth/fc_real_A.log and fc_real_B.log, per-market forecasts saved to fc_<MKT>.npz): chain A YM NKD 6J ZN ZB; chain B GC SI CL NQ. Box load 70 on 32 cores makes each market take about 1 hour. When 5+ fc_*.npz exist run code/th_alpha_breadth/portfolio.py <horizon> for items 12-13 (risk parity, effective independent bets, IR vs number of markets, cross-sectional top-vs-bottom).
NOT DONE YET (honest list): rerun on W-AL1's code/th_alpha pipeline (ridge/GBM/MLP/avg, block ablation) for the same markets; items 12-13 numbers; measured passive-fill study on NQ/ES/RTY mbp-10; holiday/half-day/17:00-18:00 ET halt minute checks; small-size capacity from depth; addendum B3 (D7 books K7 M7 U7 P7 H7 A7 ported to ES RTY YM GC CL ZN 6E; section 'D7 books on other markets'); addendum D hypothesis ledger entries.
