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

### 4b. Update 20:20Z (all FIRST PASS, gross of cost, ridge stand-in unless stated)
More markets (IC 5 / 15 / 30 / 60 min, all sessions, day-clustered t in brackets): GC 0.0214 (10.5) / 0.0092 (3.5) / 0.0018 / -0.0014; YM 0.0210 (10.2) / 0.0080 (2.8) / 0.0057 / -0.0011; SI 0.0416 (19.3) / 0.0217 (8.7) / 0.0164 (4.7) / 0.0208 (4.2); NKD 0.0722 (26.2) / 0.0473 (13.1) / 0.0354 (7.7) / 0.0287 (4.5). CAUTION on NKD (51 pct flat 1-minute bars) and SI: these large ICs are what a stale, non-synchronous price gives against the US index and metals lead: the forecast is partly predicting the next catch-up print, not a move a fill at the last price can capture. They need the tbbo (real quotes) before any weight. ZN ZB 6J CL NQ still running (chains A and B).
Independent confirmation on W-AL1's pipeline (code/th_alpha, ridge, ES, 132 features, inter NQ RTY YM ZN 6E GC CL; code/th_alpha_breadth/run_mkt.py): IC 0.0337 (t 15.6) / 0.0165 (5.9) / 0.0081 (1.9) / 0.0062 (1.1) / 0.0090 (1.1) at 5/15/30/60/120 min; it uses the completed bar T-1, so the 5-minute IC is not an alignment artefact of the stand-in. Planted 0.02 AR(1) edge on that pipeline: the IC gain is only +0.014 / +0.008 / +0.003 / -0.003 / -0.011: a single 0.02 feature among 130 is shrunk away by the ridge at 30 min and above, i.e. the pipeline (ridge, sub-sampled 6, 3-year window) cannot see an IC-0.02 signal beyond 15 minutes. Note for reading every null at 30-120 min. (Also: ic_table must be scored with tcol='ys' for planted runs.)
PORTFOLIO (items 12-13; 7 markets 6E ES GC NKD RTY SI YM; code portfolio.py; GROSS of cost; per-sample P&L = forecast strength x vol-scaled return /overlap; daily IR annualised): at 15 min single-market IR 0.96 (RTY) to 5.18 (NKD), mean 2.67; risk-parity portfolio 5.13, equal weight 4.87. Effective independent bets 6.17 of 7 (strategy-return correlation) and 6.14 (forecast correlation). IR by number of markets (mean of 100 random subsets): 2.67, 3.24, 3.73, 4.27, 4.53, 4.93, 5.13 for 1 to 7 markets, against single-market-mean x sqrt(Neff) = 2.41, 3.38, 4.09, 4.66, 5.16, 5.62, 6.00: it grows roughly with the square root of independent bets, at about 85 percent of the ideal at 7 markets. At 60 min: single mean 0.86, portfolio 1.53 (Neff 5.4). Cross-sectional top-third minus bottom-third spread: daily IR 7.63 at 15 min (6.3 markets ranked, 1,124 days) and 1.70 at 60 min. These gross IRs are NOT tradable numbers: the 15-minute books turn over every 5 minutes and no cost is deducted (cost per round trip is 0.2 to 1.8 bp against a per-trade edge of a fraction of a bp); the net-of-cost portfolio with a no-trade band is the next step.
$0 BAR PULLS DONE (each preceded by get_cost == 0.0, logged in SPEND.json and MORNING.md before download), files in /mnt/l2/l2vast/_alpha_breadth/pulls0 (about 0.1 GB): top-ups 2026-10-16..11-15 for 6A 6B 6C ZF ZT ZC ZS ZW HG PL HO RB NG LE HE and 2026-11-10..11-15 for 6E 6J NKD ZN ZB; full 2023-04..2026-11-15 ohlcv-1m for MES MNQ M2K MYM MCL MGC BTC ETH MBT. RTY 2013-01..2017-07 returned an EMPTY file (232 bytes): RTY.v.0 has no data before 2017-07; the gap cannot be filled with this symbol. The pulled files are not yet merged into the series used by the forecasts.

## D7 books on other markets (addendum B3). BAR-LEVEL REPLICA, NOT the exact engine; FIRST PASS; data to 2026-11-13 (ZN, 6E to 11-10)
Registered first in HYPOTHESIS_LEDGER (AL2-B3a, B3b). Why not the exact engine: it needs bars plus tape; only NQ, ES and RTY have tape on the box, and the engine's entry path for ES/RTY has not been confirmed by W-EV (question sent below). This is therefore the T-INSTR-2 bar-level generator (outputs/l2vast/ds3/code/instr_rf/irf_core.py: K7 Keltner 3m, U7 Supertrend 10m, P7 PB3B, A7 PB7, H7 HM, M7 vote, O7 = A7 code on 09:30-12:00 ET entries; the live O7 spec is not on disk) run by code/th_alpha_breadth/b3.py on 1-minute bars 2023-04-01..2026-11-13.
Rule for brackets: stop = target = 60 pt x ATR5m(market)/ATR5m(NQ), rounded to ticks (min 2 ticks), ATR(14) 5-minute median since 2023-04 in price units: NQ 15.16, ES 2.95 (stop 11.75 pt), RTY 1.63, YM 19.07, GC 2.22, CL 0.107, ZN 0.030, 6E 0.000306. Entry at the next 1-minute open, one trade at a time per book, flat 16:55 ET, signal block 15:00-17:59 ET. Costs: fee per round trip = costs.csv (ES 4.84, 6E 5.30 from FEES.md; the rest ESTIMATE) plus the NQ-measured slippage (stop exit 2.45 pt, market exit 0.80 pt) scaled by the ATR ratio with floors of 2 and 1 tick. Cost per trade in R: NQ 0.023, ES 0.029, GC 0.025, CL 0.036, YM 0.033, RTY 0.035, 6E 0.077, ZN 0.162.
Gross R per trade (t) by book and market:
| book | NQ | ES | RTY | YM | GC | CL | ZN | 6E |
|---|---|---|---|---|---|---|---|---|
| A7 | +0.091 (3.1) | +0.034 (1.0) | -0.009 (-0.3) | +0.015 (0.4) | +0.066 (2.8) | +0.006 (0.2) | -0.022 (-0.7) | -0.011 (-0.4) |
| H7 | +0.044 (3.5) | +0.018 (1.4) | -0.000 (-0.0) | +0.002 (0.1) | +0.028 (2.4) | -0.014 (-1.2) | -0.032 (-2.4) | -0.008 (-0.6) |
| K7 | +0.022 (2.1) | -0.010 (-0.9) | -0.006 (-0.6) | +0.002 (0.2) | +0.007 (0.7) | -0.008 (-0.8) | -0.019 (-1.6) | -0.005 (-0.5) |
| M7 | +0.031 (2.8) | +0.009 (0.8) | +0.005 (0.5) | +0.006 (0.5) | +0.013 (1.2) | +0.004 (0.4) | -0.022 (-1.8) | -0.001 (-0.1) |
| O7 | +0.013 (0.5) | +0.024 (0.9) | +0.014 (0.6) | +0.032 (1.3) | +0.023 (0.8) | +0.015 (0.6) | -0.003 (-0.1) | -0.022 (-0.8) |
| P7 | +0.018 (1.7) | +0.001 (0.1) | +0.006 (0.5) | -0.006 (-0.5) | +0.009 (0.9) | +0.008 (0.8) | -0.018 (-1.5) | -0.004 (-0.3) |
| U7 | +0.049 (2.4) | +0.022 (1.1) | +0.023 (1.1) | -0.012 (-0.6) | +0.012 (0.6) | +0.010 (0.5) | -0.012 (-0.6) | +0.010 (0.5) |

Net R per trade (after fee and slippage):
| book | NQ | ES | RTY | YM | GC | CL | ZN | 6E |
|---|---|---|---|---|---|---|---|---|
| A7 | +0.068 | +0.006 | -0.045 | -0.017 | +0.041 | -0.030 | -0.184 | -0.088 |
| H7 | +0.021 | -0.011 | -0.035 | -0.031 | +0.003 | -0.051 | -0.195 | -0.085 |
| K7 | -0.001 | -0.040 | -0.041 | -0.031 | -0.019 | -0.045 | -0.181 | -0.082 |
| M7 | +0.008 | -0.020 | -0.030 | -0.027 | -0.013 | -0.032 | -0.185 | -0.078 |
| O7 | -0.011 | -0.005 | -0.021 | -0.001 | -0.001 | -0.021 | -0.164 | -0.100 |
| P7 | -0.005 | -0.028 | -0.029 | -0.039 | -0.017 | -0.028 | -0.180 | -0.081 |
| U7 | +0.026 | -0.007 | -0.012 | -0.045 | -0.013 | -0.026 | -0.174 | -0.066 |

Reading: the replica reproduces a small positive gross edge on NQ (all 7 books, t up to 3.5) and a smaller positive gross edge on ES (5 of 7) and GC (all 7, A7 t 2.8, H7 t 2.4, plus 2023-26 was a strong gold uptrend: the books are long-biased trend/pullback logic, so a part of this is market drift, not tested here). RTY, YM, CL are indistinguishable from zero (|t| < 1.3). ZN and 6E are negative, as T-INSTR-2 found. NET of cost NQ is positive in A7 (+0.068 R, t 2.3), U7 (+0.026), H7 (+0.021, t 1.7) and M7 (+0.008); off NQ only GC A7 (+0.041, t 1.7), ES A7 (+0.006, t 0.2) and GC H7 (+0.003) are positive, none of them with |t| > 2; nothing else travels. So: A7 (Asia PB7) is the one book whose edge shows on a second market (GC, ES gross positive too); K7, P7 and M7 do not survive costs anywhere but NQ.
Diversification (proxy, because the NQ stack weekly series is not rebuilt here; NQ = the same replica on 7 books summed, each trade sized to a $3,000 risk, net of cost): NQ replica mean +4.3k per week, max drawdown 684k, worst week -190k. The correlation of each other market's summed-books weekly P&L to the NQ replica is 0.60 ES, 0.29 YM, 0.16 RTY, 0.14 ZN, 0.09 6E, 0.07 GC, -0.05 CL: low (so the diversification is real) but every added market's summed books lose money net, so adding them raises max drawdown (ES 684k -> 2.36M, GC 2.04M, 6E 8.6M, ZN 15.1M). Diversification does not help when the added streams have negative mean. A selected subset (A7 on GC and ES only) was not run through this test yet: that is the next step, with the exact engine for ES (bars + tape) if W-EV confirms a path.

### 4c. Net-of-cost portfolio with a no-trade band (lead order 1; NKD and SI EXCLUDED as stale-print suspects; 5 markets 6E ES GC RTY YM; costs.csv, ESTIMATE-labelled except ES/6E fees; code portfolio_net.py)
Position = forecast strength (clipped at 3 sd, 1x notional at 1 sd), changed only when the target moves more than the band (in forecast sd) from the current position; P&L from the 5-minute forward return; each unit of position change pays half the round-trip cost (fee + assumed half-spread); risk-parity weights on net daily vol. Gross Sharpe falls with the band (15 min: 4.77 at band 0, 1.81 at 2) but NET Sharpe stays negative everywhere: 15 min -10.4 (band 0), -6.4 (1), -3.2 (2); 30 min -8.8, -4.6, -2.1, best -1.2 (band 2.75); 60 min -7.4, -3.0, -0.6 (band 2), -0.27 at band 2.75 (gross 0.74); bands near 3 sd hold no position. Single markets at 60 min with band 2.5-2.75: YM +0.45/+0.52, ES +0.14, GC +0.13 (about zero within noise, t not computed). 6E is the worst drag (turnover 100 units/day at band 0; RT cost 0.8 bp). Verdict: with these forecasts and estimated costs the portfolio is not positive net at 15-60 min; the gross IR in 4b is not tradable.
### Question to W-EV (sent): how to run the exact engine on ES and RTY bars + tape (entry path, the depth-pollution fix) so the A7-on-ES result above can be repeated on the exact engine.

### 4d. POWER QUALIFIER (lead order): what size of edge these tests could and could not see
Forecast pipeline: with the planted 0.02-IC feature in W-AL1's ridge pipeline on ES, the recovered IC gain was +0.014 (5 min), +0.008 (15), +0.003 (30), -0.003 (60) and -0.011 (120): about 70, 40 and 15 percent of the planted 0.02 at 5, 15 and 30 minutes and none from 60 minutes. Therefore the statements 'IC at 30-120 minutes is about zero' and 'net Sharpe <= 0 at every band' mean only that THIS regularised ridge, with 130 features and a 3-year window, cannot show a true IC of 0.02 beyond about 15 minutes; a real 0.01-0.02 edge at 30-120 minutes could be present and invisible. What it could see: IC of 0.01 or more at 5 minutes (ES, SI, NKD, 6E, RTY, YM, GC are all at 0.02-0.07) and roughly 0.02 or more at 15 minutes. The net-of-cost portfolio test inherits this: it can show that the 5-15 minute forecasts do not pay costs (supported: gross 0.7-4.8 Sharpe, net negative), and it cannot rule out a net edge at 30-120 minutes. To fix: a per-horizon (not per-5-minute) fit, fewer features, or W-AL1's GBM/MLP; the planted check must be rerun on each.
Book replica: each B3 cell has 1,000-8,000 trades with a standard deviation of about 1 R per trade, so the standard error of mean R is 0.011-0.03 (the shifted-entry control gives 0.012-0.04, matching). A net edge is visible at 2 sigma only if it is at least about 0.05 R per trade in the A7/O7/U7 cells (n 1,000-2,400; about +$1,000 per week at $3,000 risk per trade) and 0.02-0.03 R in K7/M7/P7/H7 cells (n 6,000-8,000). The off-NQ net results (GC A7 +0.041 R, ES A7 +0.006 R) are below that threshold: 'nothing survives costs off NQ' means no cell shows a net edge above these thresholds; edges of 0.01-0.03 R per trade in the A7/U7 cells could exist and cannot be seen at this sample size (43 months).

### 4e. B3c drift control, B3d A7 with one extra tick, A7 diversification (bar-level replica; code b3b.py; cells /mnt/l2/l2vast/_alpha_breadth/b3/b3c.csv, b3d.csv, b3_div.csv)
B3c (gross R per trade; drift-adjusted = remove the 2023-26 mean price drift per held minute along the trade side; shifted-entry control = same events and sides moved by a random whole number of days, 30 draws): GC A7 0.0656 (t 2.8) -> 0.0612 (t 2.6) drift-adjusted, shifted-entry mean -0.011 (sd 0.025), z 3.0; GC H7 0.0278 -> 0.0268 (t 2.3), z 2.5. So the GC edge is NOT drift (gold drifted only 0.05 pt per hour on a $2.2 ATR scale). ES A7 0.0343 -> 0.0144 (t 0.4), z 1.9; ES H7 0.0183 -> 0.0122 (t 0.95), z 2.4: the ES edge is mostly drift (0.2 pt per hour on a 2.95 ATR scale) and is not significant. NQ A7 0.0907 -> 0.0748 (t 2.6), z 3.2: stands. The shifted-entry control mean is slightly negative (-0.01) in every cell, so the replica has no hidden positive bias. Hypothesis AL2-B3c: supported for ES (drift), NOT supported for GC (not drift).
B3d (A7 is Asia-only, so the session cut is the whole book; by year, net R per trade, t): GC base +0.041 (1.7): 2023 -0.012, 2024 +0.041, 2025 +0.096 (t 2.2), 2026 +0.015; with 1 extra tick per fill (2 ticks round trip): GC +0.018 (t 0.8) [2025 +0.073 (1.7), 2026 -0.008], ES -0.037 (t -1.1), NQ +0.060 (t 2.0). So GC A7 is carried by 2025 and does not survive one more tick of slippage with significance; ES A7 is negative with one more tick. Only NQ A7 remains positive at t 2.0. Capacity: A7 on GC takes about 1,850 trades in 43 months (about 10 per week), 5-50 lots is plausible in the Asia GC book, but the edge at that scale is not distinguishable from zero.
A7 diversification (weekly net P&L at $3,000 risk per trade, correlation of the added stream to the base): added to the NQ all-books replica: A7 GC (corr 0.03) mean +4.3k -> +5.5k per week, max DD 684k -> 689k, worst week -190k -> -180k; A7 ES (corr 0.37) +4.4k, DD 720k; A7 GC+ES +5.6k, DD 725k, worst week -171k. Added to NQ A7 alone: mean 1.3k -> 2.6k per week (GC+ES), max DD 35k -> 121k, worst week -20k -> -37k, because each added stream carries the same $3,000 risk per trade and the GC and ES streams are noisier. Reading: GC A7 is a true low-correlation stream (0.03-0.06 to NQ) that adds mean without adding drawdown to the full NQ replica, but its own net edge is not significant; the A7-only combination shows the diversification gain is smaller than the added variance at this sample size. Not a PASS.
Exact engine on ES (W-EV answer): not feasible today (_hist_replica_ES and _hist_replica_RTY are empty; sim.py hard-codes NQ constants); it needs an ES day-file and state-day build from raw/ES plus a parameterised engine copy. Not requested yet: the replica shows the ES A7 edge is drift and does not survive an extra tick, so the exact-engine build for ES is not justified by this result. GC has no tape on the box at all.
