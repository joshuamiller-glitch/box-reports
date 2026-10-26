# REPORT BASKET - cash basket (QQQ + top-10 NDX) lead-lag, breadth divergence, basket flow persistence

**Verdict: NO. FOUND 0, LEAD 0.** The cash side does not lead NQ at 1-5 min after cost (best grid cell, clean Sharpe +1.38, falls to -2.37 on H1 and -1.85 on H2; additive uplift at 20% +0.21 / -0.77 / -0.38 on clean / H1 / H2; gross edge across the whole 144-cell grid is a median +0.15 pt per trade in clean against a round-trip cost of 0.72 pt and a median -0.45 pt in H1+H2). Breadth divergence found no cell eligible on clean (0 of 16), and neither the size tilt on the pair's flips (BK3: best uplift +0.02 / +0.01 / -0.16) nor basket flow persistence as a conditioner (BK4: +0.02 / -0.02 / +0.01) approaches +0.10 on all three spans. 194 pre-registered cells over four families (plus 18 report-only), 0 survivors against an expected chance count well below 1 under the gates. Runtime about 2.3 h wall under heavy box load (pair-engine tilts 59 + 35 + 33 min; sleeves 1-2 min); 6-worker pools (the sub-report headers printing "7-worker pool" are a template string, the pools were 6).

Cells closed (GAP MAP): D04 x M1/M2/M3 x H1-H3 x NQ (BK1, BK2), D04 x M4/M8 x H3-H4 x NQ (BK3 breadth tilt, BK4 flow-persistence tilt). Pre-registered in PREREG_AUTOPILOT.md section BASKET before the first analysis run.

## 1. Data, spend, definitions (what was actually bought and used)
- Purchased and logged in SPEND.json (family BASKET) before each buy: XNAS.ITCH ohlcv-1m 2022-01-01..2026-10-14, 17 symbols (AAPL MSFT NVDA AMZN META GOOGL AVGO TSLA COST NFLX QQQ + candidate year-start members PEP ADBE CSCO CMCSA AMD TMUS) $8.46, FB 2022-01..06-12 (pre-rename) $0.05, DBEQ.BASIC (QQQ + ten, 2023-03-28..) $15.39, EQUS.MINI (same) $2.90. **Total $26.80** of the $8,000 cap (the quoted $6.15 was the 11-symbol ITCH list; the wider universe was needed for year-start membership). Files: data/basket/*.dbn.zst.
- ITCH covers Nasdaq-venue prints only: it understates volume (DBEQ.BASIC volume is about 10% and EQUS.MINI about 20% of the ITCH volume on QQQ/AAPL/NVDA, i.e. Nasdaq is the biggest single source here), prices are fine. **XNAS.ITCH does have QQQ prints** (QQQ is Arca-listed but trades on Nasdaq): 99.9% of the 390 RTH minutes per day have a bar (all 17 symbols 99.1-100%), 1,199 days, first RTH minute 100%. 1-min returns correlate 0.98-0.99 with EQUS.MINI and 0.85 with DBEQ.BASIC (sparser). Thin-volume alternatives were therefore not needed; the DBEQ/EQUS files are kept only as the cross-check.
- Cash window 09:30-16:00 ET (390 bars, label = open minute); a missing equity minute = return 0; the bar close is the last Nasdaq print in the minute, which can be a few seconds earlier than NQ's close (stated bias: if anything against detecting a cash lead).
- Top-10 rule: top ten NDX members by market cap at the PRIOR year-end close, fixed for the calendar year, Alphabet counted once (GOOGL). Market caps are approximate (year-end price x shares from public data, my reconstruction; errors move names ranked 8-10 only, e.g. 2022 AVGO/ADBE/NFLX/CSCO are within ~3%). Lists: 2022 AAPL MSFT GOOGL AMZN TSLA META(FB) NVDA AVGO ADBE NFLX; 2023 AAPL MSFT GOOGL AMZN TSLA NVDA META PEP AVGO COST; 2024 AAPL MSFT GOOGL AMZN NVDA META TSLA AVGO COST ADBE; 2025 AAPL NVDA MSFT AMZN GOOGL META TSLA AVGO COST NFLX; 2026 NVDA AAPL MSFT GOOGL AMZN AVGO META TSLA NFLX COST (Walmart's Nasdaq move/NDX entry and PLTR/ASML are post-start events or borderline, deliberately not used).
- Weights: year-start approximate cap weights renormalised in the ten, fixed all year (CAP10); equal weight (EQ10); QQQ's own 1-min return (QQQ, the cleanest basket-implied NQ). The 1-min correlation of CAP10 with NQ is 0.98/0.96/0.94/0.96/0.86 (2022..2026), QQQ 0.994-0.995 every year. The 2026 CAP10 drop reflects dispersion among the ten, not a data error (QQQ unaffected).
- NQ: 1-min bars from the I-series cache (difference-adjusted), costs 1 tick/side + $4.36/contract round trip = 0.72 pt per round trip; 2x slippage = 1.22 pt. Signal at the close of bar m, entry at the NEXT bar open, exit H minutes later at an open; one position at a time. ET clock throughout (UTC minute keys of both feeds converted separately to ET and joined on date and minute; NQ 18:00 label roll irrelevant inside 09:30-16:00).
- Pair for all pair-side tests: B.Cfg(wk_floor=8, wk_loss_pb=None) in a clean process (ap_i_common imports t3_score first), flips from outputs/h2/ROWS_corrected_engine.parquet; clean 1.46 / H1 2.83 / H2 2.30 weekly Sharpe reproduced. 5,761 of 13,089 pair rows enter during the cash session (only those have a basket state; the rest keep multiplier 1).

## 2. (i) Lead-lag: does the cash side lead NQ at 1-5 min? NO.
Descriptive regression (RTH minutes 09:36-15:59, 448,426 observations; future = sum of the next h one-minute returns; full per-year table in basket/diag_leadlag.md / .csv):

| basket   |   h |   corr_B_to_futNQ |   corr_NQ_to_futB |   corr_dev1_futNQ |   corr_dev3_futNQ |   corr_dev5_futNQ |
|:---------|----:|------------------:|------------------:|------------------:|------------------:|------------------:|
| cap10    |   1 |            0.0076 |            0.0125 |            0.0092 |            0.0010 |            0.0011 |
| cap10    |   2 |            0.0046 |            0.0084 |            0.0030 |           -0.0014 |           -0.0014 |
| cap10    |   3 |            0.0011 |            0.0045 |            0.0011 |           -0.0012 |           -0.0021 |
| cap10    |   5 |            0.0018 |            0.0034 |            0.0018 |           -0.0021 |           -0.0034 |
| qqq      |   1 |            0.0073 |            0.0099 |            0.0130 |            0.0033 |            0.0017 |
| qqq      |   2 |            0.0052 |            0.0067 |            0.0060 |            0.0007 |           -0.0024 |
| qqq      |   3 |            0.0013 |            0.0027 |            0.0029 |           -0.0008 |           -0.0046 |
| qqq      |   5 |            0.0017 |            0.0026 |            0.0023 |           -0.0043 |           -0.0075 |
| eq10     |   1 |            0.0096 |            0.0161 |            0.0137 |            0.0029 |            0.0022 |
| eq10     |   2 |            0.0055 |            0.0105 |            0.0052 |           -0.0004 |           -0.0018 |
| eq10     |   3 |            0.0017 |            0.0061 |            0.0025 |           -0.0006 |           -0.0024 |
| eq10     |   5 |            0.0023 |            0.0052 |            0.0030 |           -0.0018 |           -0.0036 |

Reading: all lead-lag correlations are |r| <= 0.013 (R2 about 1e-4). The reverse direction (NQ now -> basket next) is larger than basket -> NQ for every basket and horizon (e.g. QQQ h=1: 0.0099 vs 0.0073; EQ10 h=1: 0.0161 vs 0.0096): NQ, if anything, leads the cash side by a hair at 1 min, and for h >= 2 the 3-5 min divergence terms (dev3, dev5) are zero or slightly negative (no catch-up). Contemporaneous 1-min correlation is 0.94-0.995 (QQQ), so the two are the same asset at this resolution.

Tradable test, 144 pre-registered cells (basket x k x thr x H), all gross-vs-cost numbers per round trip trade at 1 tick/side + commission (cost 0.72 pt), 'gross pts' = mean points per trade before cost, over cells with >= 30 trades:

| family | span | cells | median gross pts | best gross pts | cells with gross > 0.72 | max t-stat |
|---|---|---|---|---|---|---|
| BK1 | y2022 | 144 | +0.25 | +1.90 | 23% | 4.35 |
| BK1 | clean | 144 | +0.15 | +2.04 | 12% | 3.14 |
| BK1 | H1H2 | 144 | -0.45 | +3.77 | 4% | 1.13 |
| BK2 | y2022 | 16 | -1.10 | +2.75 | 25% | 0.87 |
| BK2 | clean | 16 | +0.07 | +1.83 | 19% | 1.99 |
| BK2 | H1H2 | 16 | -0.09 | +1.86 | 19% | 1.27 |

Selection (clean 2023-08..2025-07 only; eligibility = weekly Sharpe > 0 in BOTH clean halves and >= 100 clean trades): 6 of 144 eligible; selected eq10 k=2 thr=3.0 H=3 (clean Sharpe 1.38, halves 0.73 / 1.95, 1,795 trades). The selection-aware null (30 random-entry replicates of the whole grid selection) never produced an eligible cell (every replicate has all cells losing to cost), so the clean selection itself is real in-sample, but out of sample it reverses: standalone Sharpe H1 -2.37, H2 -1.85, all-in +0.09. The gross edge exists only in 2022-2024 small samples and vanishes by 2025-26 (median gross -0.45 pt in H1+H2). **ERA FLAG for BK1: gross-positive, cost-negative pre-2023** (2022 only: gross +0.0002 ADR units per trade, fixed-cost Sharpe -0.99, price-scaled cost -1.29). Full gate table, insurance metric sets and plateau are in appendix A.

## 3. (ii) Breadth divergence (NQ 30-min high/low with fewer than {3,4} of the ten confirming)
### 3a. As a fade entry (BK2, 16 cells): NO, no eligible cell.
No cell has positive weekly Sharpe in both clean halves with >= 60 trades (0 of 16; best clean Sharpe +0.35 with halves -0.29 / +1.23). Pair window not read. The gross-points table (fade direction, no cost) makes the point in points:

| n< | confirm | H | clean trades | clean gross pts/trade | H1+H2 trades | H1+H2 gross pts/trade | 2022 gross pts/trade |
|---|---|---|---|---|---|---|---|
| 3 | near | 10 | 684 | +0.43 | 1235 | +0.35 | +2.68 |
| 3 | near | 20 | 632 | +1.76 | 1041 | -1.47 | +2.75 |
| 3 | near | 30 | 593 | +1.38 | 908 | -2.60 | +2.30 |
| 3 | near | 60 | 515 | -1.55 | 696 | -0.80 | -3.77 |
| 3 | strict | 10 | 4447 | -0.01 | 3521 | -0.03 | -0.89 |
| 3 | strict | 20 | 3522 | -0.18 | 2590 | -0.77 | -1.72 |
| 3 | strict | 30 | 2908 | -0.97 | 2095 | -0.61 | -1.26 |
| 3 | strict | 60 | 1972 | -1.67 | 1345 | +0.09 | -4.67 |
| 4 | near | 10 | 1718 | +0.39 | 2129 | +1.01 | -0.06 |
| 4 | near | 20 | 1498 | +1.83 | 1689 | +0.15 | +1.60 |
| 4 | near | 30 | 1349 | +0.57 | 1406 | -0.88 | -1.16 |
| 4 | near | 60 | 1063 | -3.17 | 984 | +1.86 | -1.04 |
| 4 | strict | 10 | 6192 | +0.16 | 4295 | +0.16 | -0.85 |
| 4 | strict | 20 | 4549 | +0.21 | 3038 | -0.34 | -1.17 |
| 4 | strict | 30 | 3609 | -0.41 | 2367 | -0.16 | -1.22 |
| 4 | strict | 60 | 2295 | -1.44 | 1446 | +1.12 | -1.20 |

Fade pays in some NEAR cells in 2022 and clean (+1.4 to +2.7 pt) but the sign is not stable (H1+H2 -2.6 to +1.9 pt) and STRICT cells (the literal 'new 30-min high on the same minute') are cost-dominated losers. 4,000-6,000 trades in clean for the STRICT definitions show the condition is very frequent (strict confirmation at the exact same minute is rare even in genuine broad rallies: mean confirmers 3.9 of 10 at NQ highs), so 'divergence' as literally specified is not rare or informative.
### 3b. As a size tilt on the pair's flips (BK3, 16 cells): NO.
Carried cell (clean-only selection): thr=4, j=5, cut to x0.5; changes 8.9% of clean entries. Sharpe uplift clean / H1 / H2 / all-in +0.015 / +0.015 / -0.163 / -0.006; matched-permutation null p95 +0.155 (rank 0.46); bootstrap 90% CI [-0.136, +0.127]; plateau 0 of 6; 2x slippage +0.074 / -0.004 / -0.151. The walk-forward (WF) cells changed 0-0.5% of entries (the 'divergent at an extreme' bucket never had 20 exited rows with a negative mean, so the tilt never switched on). Constant-risk framing for the carried cell is in appendix B. Mechanism not supported: six of the eight cut cells on unconfirmed pushes lower clean Sharpe by 0.09-0.14 (the two thr=4, j=5 cut cells are +0.01), i.e. the unconfirmed pushes are not worse flips on average, which is the opposite of the hypothesis.

## 4. (iii) Basket flow persistence as a conditioner of the pair (BK4, 18 cells): NO
Signed basket flow = sum of sign(bar return) x ITCH dollar volume over the ten (signed-bar-volume proxy, Nasdaq-only volume; no aggressor side in ohlcv). Carried cell W=60, q=80, BOTH (cut x0.5 against persistent flow, boost x1.25 with it): changes 7.4% of clean entries; uplift +0.016 / -0.023 / +0.007 / all-in +0.005; null p95 +0.082 (rank 0.77); bootstrap [-0.071, +0.077]; plateau 75% (pass, trivially, with zero uplift); 2x slippage -0.031 / +0.078 / +0.021; constant-risk framing -0.126 / -0.141 / +0.160. Worst-week gate passes only because the tilt is nearly neutral.
**Join with DRIVERS (report-only, BK4N):** DRIVERS' per-minute NQ signed-volume aggregates (outputs/autopilot/drivers/min_NQ_2023.parquet, 2023-02..2026-10) were already available, so the identical 18 cells were also run with NQ's own aggressor-signed flow persistence (all hours, 24h, so 9-55% of entries change): best clean cell W=15 q=67 BOTH +0.148 clean but -0.361 H1 and -0.356 H2; 0/6 gates. Basket flow F30 and NQ flow F30 correlate +0.56 / +0.59 / +0.49 / +0.38 (2023/24/25/26, RTH): the basket flow is a noisier, Nasdaq-only version of the same information and adds nothing the pair can use. (DRIVERS section 5 itself was not yet published at run time; BK4N is an independent computation on the same aggregates, it does not replace it.)

## 5. Gate checklist (headline cell of each family; 7 gates of AUTOPILOT)
| family | 1 prereg | 2 clean-only selection | 3 uplift>=+0.10 clean/H1/H2 (+ worst week) | 4 own null p95 / bootstrap CI>0 | 5 plateau / 2x slip | 6 wd corr<=+0.30 | 7 NT8 spec | verdict |
|---|---|---|---|---|---|---|---|---|
| BK1 lead-lag sleeve (eq10 k2 thr3 H3) | yes | yes | FAIL +0.21/-0.77/-0.38; worst wk +26% vs share 20% FAIL | standalone null PASS (artefact: random entries lose to cost; median -1.41 vs real +0.09) / bootstrap FAIL [-0.236,+0.115] | FAIL 0 of 4 / FAIL | FAIL +0.58 | spec below (not worth coding) | NO |
| BK2 breadth fade sleeve | yes | no eligible cell (0/16) | n/a | n/a | n/a | n/a | spec below | NO |
| BK3 breadth tilt (thr4 j5 cut0.5) | yes | yes | FAIL +0.02/+0.02/-0.16; worst wk PASS | FAIL (p95 +0.155) / FAIL | FAIL 0 of 6 / FAIL | n/a (pair change) | spec below | NO |
| BK4 flow tilt (W60 q80 both) | yes | yes | FAIL +0.02/-0.02/+0.01; worst wk PASS | FAIL (p95 +0.082) / FAIL | PASS (zero uplift) / FAIL | n/a | spec below | NO |
| BK4N NQ own-flow (report only) | yes | yes | FAIL +0.15/-0.36/-0.36 | FAIL / FAIL | FAIL / FAIL | n/a | n/a | NO |
Framings: sleeves additive 10/20/30/50% and constant-risk 10/20/30/50% (BK1 tables, appendix A); pair tilts additive-on-the-pair by construction plus constant-risk renormalisation (appendices B-D). Circular-shift null: reported in the BK1 table (rank 0.11), not gating (no hedge claim). Insurance metric sets (CVaR5/10, maxDD, worst week, Sortino, weekly Sharpe, MAR, % neg weeks, clean / H1 / H2 / all-in) are in the appendices. No INSURANCE/SURVIVES verdict: BK1 constant-risk 20% lowers weekly Sharpe in H1/H2 (1.88/1.82 vs 2.83/2.30) and raises H1 maxDD (182k vs 152k; H2 196k vs 217k is lower but with 0.5 less Sharpe); the BK3/BK4 tilts leave the metric set essentially unchanged.
**Small-sample flag:** none (BK1 2,886 pair-window trades). **ERA flag:** BK1 gross-positive, cost-negative pre-2023 (2022 is the only pre-2023 year bought; ITCH reaches 2018-05 if a longer era read is wanted, about $4 more). BK2/BK3/BK4 not applicable (no selected sleeve / pair tilts; the pair rows begin 2023-02).
**Mechanism sentence and structure dependence:** index arbitrage keeps NQ and the cash index within a few ticks at 1 min, so any cash lead is smaller than 1 tick and is exactly what NQ market makers already trade; it depends on current structure (HFT arbitrage, micros, 0DTE hedging flow) and is not a stable source of edge in 2025-26.

## 6. Fill model, costs, executability
- Fill model: signal at bar-m close, entry at next NQ bar open, exit at the open H min later (bar-open fills, no limit orders, no queue assumptions), 1 tick per side (0.25 pt) + $4.36 per contract round trip for sleeves; 2x slippage = 2 ticks per side; pair tilts use the corrected NT8-faithful engine (1 tick/side + $34.88 per 8-lot round trip; live day/week/lock rules re-simulated with the size multipliers).
- Executability at NinjaTrader Brokerage via Rithmic: the NQ leg is trivially executable, the SIGNAL is not: Rithmic supplies CME futures only, so a basket/breadth signal needs a cash-equity real-time feed (Nasdaq Basic/UTP via Kinetick/IQFeed/Polygon or Databento live) inside the NT8 chart or a sidecar writing a file/socket the strategy reads. In NT8 this is a multi-instrument strategy (AddDataSeries for QQQ + ten on 1-min, Calculate=OnBarClose) with a second data connection; the sub-minute latency would matter for BK1 (signal-to-fill within seconds of the minute close). IBKR could supply both equities and CME futures in one account but is not the production path. None of this is worth building: no cell passes.
- NT8 spec if it had passed (kept for the record): BK1 on NQ 1-min chart, secondary series QQQ 1-min (cash 09:30-16:00 ET): dev_k = sum over last k bars of (QQQ return - NQ return), z = dev_k / (sqrt(k) x mean over prior 20 sessions of the daily sd of the 1-min difference); at bar close, if 09:35 <= time < 15:50 and |z| >= thr and flat, enter market in sign(dev) direction at the next bar open, exit by time at the open H bars later; size = 1 ADR-dollar-of-risk scaled (ADR20 of NQ), margin about $18k-$20k per NQ contract (intraday day-margin lower). BK3/BK4 would be a sizing hook in DualStrat's entry (multiplier from the basket state at the flip minute): not built.
- Margin: NQ initial margin about $18-20k per contract; the sleeves at 10-50% of the pair risk would need 3-16 contract-equivalents at the scaled size (scale factor f = 2.03e5 $/ADR-unit for BK1 to match the pair's clean weekly sigma), which is large relative to the edge; moot.

## 7. Verdict summary and what would change it
- BK1 NO, BK2 NO (no eligible cell), BK3 NO, BK4 NO, BK4N (NQ own flow, report only) NO. FOUND 0, LEAD 0.
- Closest miss: none within reach. The only positive finding is gross: a small catch-up edge (about +1 to +2 pt per trade in the best cells in 2022-2024) that is below the 0.72 pt cost in aggregate and gone in H1/H2.
- What could still be asked: (a) 2018-2021 ITCH bars (about $4) for a longer era flag; (b) the basket's cash opening auction (09:30 print) and the 15:50-16:00 imbalance as event timing for the pair (not in the user's ask, untested, would need ITCH imbalance/NOII data); (c) QQQ options flow as the true cash-side informed-flow source (belongs to OPTIONS).

## Appendices
Appendix A: BK1 full sub-report (sleeve, both framings, insurance sets, plateau, null, 2x slippage, long history). Appendix B: BK3. Appendix C: BK4. Appendix D: BK4N (report only). Source code: code/census/night_ins/ap_basket_{buy,panel,dense,core,sleeve,tilt,nqflow,diag,gross}.py; artefacts: outputs/autopilot/basket/.

### Appendix A - BK1
# REPORT BK1
**Verdict: NO** (1/7 measured gates pass). Selected cell basket=eq10 k=2 thr=3.0 H=3; additive @20% clean/H1/H2 +0.21/-0.76/-0.38; standalone all-in weekly Sharpe 0.09 (2013-26 -0.08, dev 2013-22 -0.99); pair-window trades 2886. Runtime 0.1 min (+selection 0.0 min). 7-worker pool.



## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 144 cells, eligible (>= 100 clean trades): 6. Top cells by clean weekly Sharpe:

| b     |   k |   thr |   H |    n |   sharpe |    shA |   shB |   net |   ypos | eligible   |
|:------|----:|------:|----:|-----:|---------:|-------:|------:|------:|-------:|:-----------|
| eq10  |   2 | 3.000 |   3 | 1795 |    1.383 |  0.727 | 1.947 | 6.212 |      3 | True       |
| cap10 |   5 | 3.000 |   1 | 2006 |    0.801 |  0.525 | 0.990 | 2.445 |      2 | True       |
| qqq   |   3 | 3.000 |   1 |  884 |    0.683 |  0.668 | 0.692 | 1.199 |      2 | True       |
| eq10  |   3 | 2.000 |   3 | 4912 |    0.602 |  0.299 | 0.871 | 4.603 |      1 | True       |
| eq10  |   5 | 3.000 |   1 | 1861 |    0.415 | -0.410 | 0.873 | 1.511 |      1 | False      |
| cap10 |   5 | 3.000 |   3 | 1465 |    0.313 | -0.313 | 0.703 | 1.593 |      2 | False      |
| qqq   |   3 | 3.000 |   2 |  802 |    0.293 |  0.299 | 0.283 | 0.909 |      2 | True       |
| eq10  |   5 | 3.000 |   3 | 1372 |    0.271 | -0.746 | 0.719 | 1.843 |      1 | False      |
| qqq   |   5 | 2.000 |   3 | 2583 |    0.259 | -0.488 | 0.811 | 1.861 |      2 | False      |
| qqq   |   2 | 3.000 |   1 | 1170 |    0.199 | -1.037 | 1.021 | 0.519 |      1 | False      |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.38; replicate best-eligible median -9.00, p95 0.62; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.028e+05)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.113 | -0.382 | -0.188 | -0.021 | +13.1 | [-0.113, +0.069] | 0.11 | NO |
| 20% | add | +0.208 | -0.765 | -0.382 | -0.058 | +26.2 | [-0.236, +0.115] | 0.11 | NO |
| 30% | add | +0.284 | -1.132 | -0.576 | -0.109 | +39.4 | [-0.368, +0.142] | 0.11 | NO |
| 50% | add | +0.385 | -1.786 | -0.954 | -0.234 | +65.6 | [-0.634, +0.151] | 0.11 | NO |
| 10% | const | +0.125 | -0.425 | -0.210 | -0.024 | +3.1 | [-0.126, +0.076] | 0.11 | NO |
| 20% | const | +0.248 | -0.951 | -0.479 | -0.082 | +6.2 | [-0.302, +0.132] | 0.11 | NO |
| 30% | const | +0.356 | -1.567 | -0.822 | -0.186 | +9.4 | [-0.540, +0.153] | 0.11 | NO |
| 50% | const | +0.448 | -2.906 | -1.741 | -0.564 | +27.6 | [-1.212, +0.059] | 0.11 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,259,902, Sharpe 1.38, maxDD 443,515, worst wk -117,530; H1: net -622,773, Sharpe -2.37, maxDD 738,378, worst wk -165,177; H2: net -503,962, Sharpe -1.85, maxDD 743,072, worst wk -150,348; all: net 133,168, Sharpe 0.09, maxDD 1,293,795, worst wk -165,177
Correlation with pair (weekly): clean +0.11, H1 +0.22, H2 +0.17, all +0.11; worst-decile weeks (n=17) corr +0.58, sleeve mean in those weeks $-15,486, positive share 0.35.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.67 | 3.23 | 7.13 | -87,148 | -81,662 | 222,009 | -97,334 | 39.0 |
| clean | add 30% | 1.74 | 3.41 | 7.94 | -91,490 | -84,848 | 215,181 | -105,064 | 37.1 |
| clean | const 20% | 1.71 | 3.32 | 7.79 | -71,455 | -66,511 | 168,974 | -80,959 | 38.1 |
| clean | const 30% | 1.82 | 3.61 | 8.27 | -68,620 | -63,419 | 158,356 | -80,502 | 38.1 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.06 | 3.98 | 2.23 | -92,708 | -77,795 | 210,002 | -99,079 | 46.4 |
| H1 | add 30% | 1.70 | 3.12 | 1.65 | -100,258 | -87,096 | 246,186 | -110,152 | 50.0 |
| H1 | const 20% | 1.88 | 3.53 | 1.92 | -77,186 | -65,461 | 182,475 | -83,692 | 46.4 |
| H1 | const 30% | 1.26 | 2.19 | 1.12 | -76,975 | -70,452 | 204,897 | -87,072 | 50.0 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 1.91 | 3.51 | 2.87 | -97,226 | -90,077 | 230,133 | -104,179 | 41.7 |
| H2 | add 30% | 1.72 | 3.01 | 2.35 | -110,157 | -97,674 | 259,455 | -115,006 | 36.1 |
| H2 | const 20% | 1.82 | 3.25 | 2.60 | -82,953 | -75,100 | 195,835 | -87,674 | 36.1 |
| H2 | const 30% | 1.47 | 2.45 | 1.83 | -88,748 | -75,972 | 208,008 | -90,248 | 36.1 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.80 | 3.41 | 11.55 | -92,010 | -85,025 | 234,746 | -104,179 | 40.5 |
| all | add 30% | 1.75 | 3.27 | 10.12 | -99,581 | -89,679 | 269,174 | -115,006 | 38.7 |
| all | const 20% | 1.77 | 3.34 | 10.79 | -76,637 | -69,788 | 201,568 | -87,674 | 38.7 |
| all | const 30% | 1.67 | 3.08 | 8.75 | -76,521 | -68,201 | 219,407 | -90,248 | 39.3 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.208 / -0.765 / -0.382
- [FAIL] 3 worst week within share: all-in worst week +26.2% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.09 vs p95 -0.49 (rank 1.00)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.236, +0.115]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.077 / -0.879 / -0.455
- [FAIL] 6 worst-decile corr <=+0.30: +0.58
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section BK1); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (2886 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 1033 | +0.0002 | 0.12 |
| fixed | 1033 | -0.0018 | -0.99 |
| scaled | 1033 | -0.0023 | -1.29 |

Plateau neighbours (all-in 20% uplift; selected -0.058):
- {'b': 'eq10', 'k': '2', 'thr': '2.25', 'H': '3'}: -0.501 (trades 6440)
- {'b': 'eq10', 'k': '2', 'thr': '3.75', 'H': '3'}: -0.028 (trades 1411)
- {'b': 'eq10', 'k': '2', 'thr': '3.0', 'H': '2'}: -0.229 (trades 3102)
- {'b': 'eq10', 'k': '2', 'thr': '3.0', 'H': '4'}: -0.045 (trades 2707)

Own random-entry null: 500 draws, standalone all-in Sharpe median -1.41, p95 -0.49, real 0.09. Standalone Sharpe at 2x slippage -0.51.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2022 | 1033 | -2 | -0.99 |
| 2023 | 770 | 1 | 0.30 |
| 2024 | 921 | 3 | 1.67 |
| 2025 | 817 | 1 | 0.37 |
| 2026 | 785 | -3 | -1.98 |


DONE BK1

### Appendix B - BK3
# REPORT BK3

Full clean grid:

|   thr |   j | mode      |   clean_sharpe |   clean_dsharpe |   changed |   clean_net | eligible   |
|------:|----:|:----------|---------------:|----------------:|----------:|------------:|:-----------|
|     3 |   1 | cut0.5    |          1.319 |          -0.141 |     0.030 | 1191251.840 | True       |
|     3 |   1 | cut0      |          1.356 |          -0.104 |     0.047 | 1227472.000 | True       |
|     3 |   1 | wf0.5     |          1.460 |           0.000 |     0.000 | 1329958.720 | False      |
|     3 |   1 | boost1.25 |          1.492 |           0.032 |     0.009 | 1358018.160 | False      |
|     3 |   5 | cut0.5    |          1.361 |          -0.099 |     0.056 | 1240260.640 | True       |
|     3 |   5 | cut0      |          1.324 |          -0.136 |     0.082 | 1225784.320 | True       |
|     3 |   5 | wf0.5     |          1.460 |           0.000 |     0.000 | 1329958.720 | False      |
|     3 |   5 | boost1.25 |          1.470 |           0.010 |     0.015 | 1338300.960 | False      |
|     4 |   1 | cut0.5    |          1.322 |          -0.137 |     0.044 | 1187017.600 | True       |
|     4 |   1 | cut0      |          1.372 |          -0.088 |     0.061 | 1226682.560 | True       |
|     4 |   1 | wf0.5     |          1.460 |           0.000 |     0.000 | 1329958.720 | False      |
|     4 |   1 | boost1.25 |          1.492 |           0.032 |     0.009 | 1358018.160 | False      |
|     4 |   5 | cut0.5    |          1.475 |           0.015 |     0.089 | 1335541.440 | True       |
|     4 |   5 | cut0      |          1.474 |           0.014 |     0.114 | 1351498.880 | True       |
|     4 |   5 | wf0.5     |          1.453 |          -0.007 |     0.005 | 1321165.440 | False      |
|     4 |   5 | boost1.25 |          1.470 |           0.010 |     0.015 | 1338300.960 | False      |

**Verdict: NO** (1/6 measured gates pass; D1-harness class NO). Carried cell thr=4 j=5 mode=cut0.5; all-in Sharpe uplift clean/H1/H2/all +0.02/+0.01/-0.16/-0.01. Runtime 59.0 min, 7-worker pool. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules (per-book 5R/-2R, day lock 8R/2R/67%, week floor -8R, per-book week rule off).



## Clean-only selection grid

|   thr |   j | mode      |   clean_sharpe |   clean_dsharpe |   changed |   clean_net | eligible   |
|------:|----:|:----------|---------------:|----------------:|----------:|------------:|:-----------|
|     3 |   1 | boost1.25 |          1.492 |           0.032 |     0.009 | 1358018.160 | False      |
|     4 |   1 | boost1.25 |          1.492 |           0.032 |     0.009 | 1358018.160 | False      |
|     4 |   5 | cut0.5    |          1.475 |           0.015 |     0.089 | 1335541.440 | True       |
|     4 |   5 | cut0      |          1.474 |           0.014 |     0.114 | 1351498.880 | True       |
|     4 |   5 | boost1.25 |          1.470 |           0.010 |     0.015 | 1338300.960 | False      |
|     3 |   5 | boost1.25 |          1.470 |           0.010 |     0.015 | 1338300.960 | False      |
|     3 |   5 | wf0.5     |          1.460 |           0.000 |     0.000 | 1329958.720 | False      |
|     3 |   1 | wf0.5     |          1.460 |           0.000 |     0.000 | 1329958.720 | False      |
|     4 |   1 | wf0.5     |          1.460 |           0.000 |     0.000 | 1329958.720 | False      |
|     4 |   5 | wf0.5     |          1.453 |          -0.007 |     0.005 | 1321165.440 | False      |
|     4 |   1 | cut0      |          1.372 |          -0.088 |     0.061 | 1226682.560 | True       |
|     3 |   5 | cut0.5    |          1.361 |          -0.099 |     0.056 | 1240260.640 | True       |
|     3 |   1 | cut0      |          1.356 |          -0.104 |     0.047 | 1227472.000 | True       |
|     3 |   5 | cut0      |          1.324 |          -0.136 |     0.082 | 1225784.320 | True       |
|     4 |   1 | cut0.5    |          1.322 |          -0.137 |     0.044 | 1187017.600 | True       |
|     3 |   1 | cut0.5    |          1.319 |          -0.141 |     0.030 | 1191251.840 | True       |

## Carried cell vs baseline pair (clean / H1 / H2 / all-in)

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.48 |
| clean | Sortino | 2.78 | 2.77 |
| clean | MAR | 4.75 | 4.77 |
| clean | net $ | 1,329,958.72 | 1,335,541.44 |
| clean | maxDD $ | 280,109.76 | 280,049.76 |
| clean | worst wk $ | -81,873.92 | -81,873.92 |
| clean | CVaR5 $ | -78,735.52 | -79,147.33 |
| clean | CVaR10 $ | -78,008.81 | -78,214.75 |
| clean | % neg wk | 42.86 | 44.76 |
| H1 | weekly Sharpe | 2.83 | 2.84 |
| H1 | Sortino | 6.09 | 6.84 |
| H1 | MAR | 3.91 | 4.40 |
| H1 | net $ | 593,797.44 | 665,980.32 |
| H1 | maxDD $ | 151,712.64 | 151,422.88 |
| H1 | worst wk $ | -78,287.36 | -76,887.36 |
| H1 | CVaR5 $ | -77,609.92 | -76,852.48 |
| H1 | CVaR10 $ | -66,029.97 | -65,815.95 |
| H1 | % neg wk | 39.29 | 35.71 |
| H2 | weekly Sharpe | 2.30 | 2.13 |
| H2 | Sortino | 4.69 | 4.26 |
| H2 | MAR | 3.50 | 3.26 |
| H2 | net $ | 761,254.40 | 694,610.72 |
| H2 | maxDD $ | 217,425.28 | 212,927.84 |
| H2 | worst wk $ | -82,524.48 | -80,805.44 |
| H2 | CVaR5 $ | -81,088.96 | -80,229.44 |
| H2 | CVaR10 $ | -79,185.12 | -78,845.36 |
| H2 | % neg wk | 44.44 | 41.67 |
| all | weekly Sharpe | 1.86 | 1.85 |
| all | Sortino | 3.63 | 3.63 |
| all | MAR | 9.59 | 9.63 |
| all | net $ | 2,685,010.56 | 2,696,132.48 |
| all | maxDD $ | 280,109.76 | 280,049.76 |
| all | worst wk $ | -82,524.48 | -81,873.92 |
| all | CVaR5 $ | -79,220.34 | -79,235.40 |
| all | CVaR10 $ | -78,243.12 | -78,215.44 |
| all | % neg wk | 42.86 | 42.86 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.015 / +0.015 / -0.163
- [PASS] 3 worst week not worse (all-in): -81,874 vs baseline -82,524
- [FAIL] 4 matched family null p95: real -0.006 vs p95 +0.155 (median +0.002, rank 0.46, n=500)
- [FAIL] 4 bootstrap 90% CI >0: [-0.136, +0.127]
- [FAIL] 5 plateau: 0% of 6 neighbours keep >=75% of uplift
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.074 / -0.004 / -0.151
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md BATCH I); 2 selection on clean only, H1/H2 read once; 6 n/a (pair change, not a hedge claim); 7 see below

Plateau neighbours (all-in uplift):
- {'thr': 3, 'j': 5, 'mode': 'cut0.5'}: -0.085
- {'thr': 5, 'j': 5, 'mode': 'cut0.5'}: -0.015
- {'thr': 4, 'j': 3, 'mode': 'cut0.5'}: -0.010
- {'thr': 4, 'j': 7, 'mode': 'cut0.5'}: +0.012
- {'thr': 4, 'j': 5, 'mode': 'cut0.375'}: +0.059
- {'thr': 4, 'j': 5, 'mode': 'cut0.625'}: +0.042


## Constant-risk framing (multipliers renormalised to clean mean 1; raw clean mean 0.958)
Sharpe uplift clean/H1/H2/all: +0.095 / -0.274 / -0.359 / -0.033. Rows changed (all/clean): 1235/521 of 5761 cash-session rows.

DONE BK3

### Appendix C - BK4
# REPORT BK4

Full clean grid:

|   W |   q | mode        |   clean_sharpe |   clean_dsharpe |   changed |   clean_net | eligible   |
|----:|----:|:------------|---------------:|----------------:|----------:|------------:|:-----------|
|  15 |  67 | cut_against |          1.443 |          -0.016 |     0.019 | 1304288.000 | False      |
|  15 |  67 | boost_with  |          1.262 |          -0.198 |     0.106 | 1190218.240 | True       |
|  15 |  67 | both        |          1.347 |          -0.113 |     0.117 | 1247665.760 | True       |
|  15 |  80 | cut_against |          1.492 |           0.033 |     0.007 | 1355003.360 | False      |
|  15 |  80 | boost_with  |          1.411 |          -0.049 |     0.065 | 1314713.840 | True       |
|  15 |  80 | both        |          1.437 |          -0.023 |     0.072 | 1334233.360 | True       |
|  30 |  67 | cut_against |          1.389 |          -0.071 |     0.013 | 1267637.760 | False      |
|  30 |  67 | boost_with  |          1.388 |          -0.072 |     0.117 | 1301361.200 | True       |
|  30 |  67 | both        |          1.436 |          -0.024 |     0.124 | 1334447.040 | True       |
|  30 |  80 | cut_against |          1.413 |          -0.047 |     0.006 | 1290348.480 | False      |
|  30 |  80 | boost_with  |          1.415 |          -0.044 |     0.083 | 1334352.880 | True       |
|  30 |  80 | both        |          1.394 |          -0.066 |     0.089 | 1315111.600 | True       |
|  60 |  67 | cut_against |          1.467 |           0.007 |     0.006 | 1337088.000 | False      |
|  60 |  67 | boost_with  |          1.324 |          -0.136 |     0.105 | 1232014.480 | True       |
|  60 |  67 | both        |          1.341 |          -0.119 |     0.109 | 1247584.800 | True       |
|  60 |  80 | cut_against |          1.462 |           0.002 |     0.002 | 1333900.800 | False      |
|  60 |  80 | boost_with  |          1.462 |           0.002 |     0.072 | 1351853.200 | True       |
|  60 |  80 | both        |          1.476 |           0.016 |     0.074 | 1367215.280 | True       |

**Verdict: NO** (2/6 measured gates pass; D1-harness class NO). Carried cell W=60 q=80 mode=both; all-in Sharpe uplift clean/H1/H2/all +0.02/-0.02/+0.01/+0.01. Runtime 35.0 min, 7-worker pool. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules (per-book 5R/-2R, day lock 8R/2R/67%, week floor -8R, per-book week rule off).



## Clean-only selection grid

|   W |   q | mode        |   clean_sharpe |   clean_dsharpe |   changed |   clean_net | eligible   |
|----:|----:|:------------|---------------:|----------------:|----------:|------------:|:-----------|
|  15 |  80 | cut_against |          1.492 |           0.033 |     0.007 | 1355003.360 | False      |
|  60 |  80 | both        |          1.476 |           0.016 |     0.074 | 1367215.280 | True       |
|  60 |  67 | cut_against |          1.467 |           0.007 |     0.006 | 1337088.000 | False      |
|  60 |  80 | cut_against |          1.462 |           0.002 |     0.002 | 1333900.800 | False      |
|  60 |  80 | boost_with  |          1.462 |           0.002 |     0.072 | 1351853.200 | True       |
|  15 |  67 | cut_against |          1.443 |          -0.016 |     0.019 | 1304288.000 | False      |
|  15 |  80 | both        |          1.437 |          -0.023 |     0.072 | 1334233.360 | True       |
|  30 |  67 | both        |          1.436 |          -0.024 |     0.124 | 1334447.040 | True       |
|  30 |  80 | boost_with  |          1.415 |          -0.044 |     0.083 | 1334352.880 | True       |
|  30 |  80 | cut_against |          1.413 |          -0.047 |     0.006 | 1290348.480 | False      |
|  15 |  80 | boost_with  |          1.411 |          -0.049 |     0.065 | 1314713.840 | True       |
|  30 |  80 | both        |          1.394 |          -0.066 |     0.089 | 1315111.600 | True       |
|  30 |  67 | cut_against |          1.389 |          -0.071 |     0.013 | 1267637.760 | False      |
|  30 |  67 | boost_with  |          1.388 |          -0.072 |     0.117 | 1301361.200 | True       |
|  15 |  67 | both        |          1.347 |          -0.113 |     0.117 | 1247665.760 | True       |
|  60 |  67 | both        |          1.341 |          -0.119 |     0.109 | 1247584.800 | True       |
|  60 |  67 | boost_with  |          1.324 |          -0.136 |     0.105 | 1232014.480 | True       |
|  15 |  67 | boost_with  |          1.262 |          -0.198 |     0.106 | 1190218.240 | True       |

## Carried cell vs baseline pair (clean / H1 / H2 / all-in)

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.48 |
| clean | Sortino | 2.78 | 2.81 |
| clean | MAR | 4.75 | 4.79 |
| clean | net $ | 1,329,958.72 | 1,367,215.28 |
| clean | maxDD $ | 280,109.76 | 285,342.80 |
| clean | worst wk $ | -81,873.92 | -81,873.92 |
| clean | CVaR5 $ | -78,735.52 | -79,394.99 |
| clean | CVaR10 $ | -78,008.81 | -78,588.97 |
| clean | % neg wk | 42.86 | 42.86 |
| H1 | weekly Sharpe | 2.83 | 2.80 |
| H1 | Sortino | 6.09 | 6.06 |
| H1 | MAR | 3.91 | 3.88 |
| H1 | net $ | 593,797.44 | 591,500.96 |
| H1 | maxDD $ | 151,712.64 | 152,369.84 |
| H1 | worst wk $ | -78,287.36 | -79,361.20 |
| H1 | CVaR5 $ | -77,609.92 | -78,647.36 |
| H1 | CVaR10 $ | -66,029.97 | -67,246.99 |
| H1 | % neg wk | 39.29 | 39.29 |
| H2 | weekly Sharpe | 2.30 | 2.30 |
| H2 | Sortino | 4.69 | 4.71 |
| H2 | MAR | 3.50 | 3.47 |
| H2 | net $ | 761,254.40 | 762,704.88 |
| H2 | maxDD $ | 217,425.28 | 219,854.00 |
| H2 | worst wk $ | -82,524.48 | -80,153.20 |
| H2 | CVaR5 $ | -81,088.96 | -79,903.32 |
| H2 | CVaR10 $ | -79,185.12 | -78,592.30 |
| H2 | % neg wk | 44.44 | 41.67 |
| all | weekly Sharpe | 1.86 | 1.86 |
| all | Sortino | 3.63 | 3.65 |
| all | MAR | 9.59 | 9.54 |
| all | net $ | 2,685,010.56 | 2,721,421.12 |
| all | maxDD $ | 280,109.76 | 285,342.80 |
| all | worst wk $ | -82,524.48 | -81,873.92 |
| all | CVaR5 $ | -79,220.34 | -79,504.20 |
| all | CVaR10 $ | -78,243.12 | -78,607.00 |
| all | % neg wk | 42.86 | 42.26 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.016 / -0.023 / +0.007
- [PASS] 3 worst week not worse (all-in): -81,874 vs baseline -82,524
- [FAIL] 4 matched family null p95: real +0.005 vs p95 +0.082 (median -0.050, rank 0.77, n=500)
- [FAIL] 4 bootstrap 90% CI >0: [-0.071, +0.077]
- [PASS] 5 plateau: 75% of 4 neighbours keep >=75% of uplift
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.031 / +0.078 / +0.021
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md BATCH I); 2 selection on clean only, H1/H2 read once; 6 n/a (pair change, not a hedge claim); 7 see below

Plateau neighbours (all-in uplift):
- {'W': 45, 'q': 80, 'mode': 'both'}: +0.028
- {'W': 75, 'q': 80, 'mode': 'both'}: -0.022
- {'W': 60, 'q': 60, 'mode': 'both'}: +0.007
- {'W': 60, 'q': 99, 'mode': 'both'}: +0.026


## Constant-risk framing (multipliers renormalised to clean mean 1; raw clean mean 1.024)
Sharpe uplift clean/H1/H2/all: -0.126 / -0.141 / +0.160 / -0.063. Rows changed (all/clean): 1249/677 of 5761 cash-session rows.

DONE BK4

### Appendix D - BK4N (report only)
# REPORT BK4N

Full clean grid:

|   W |   q | mode        |   clean_sharpe |   clean_dsharpe |   changed |   clean_net | eligible   |
|----:|----:|:------------|---------------:|----------------:|----------:|------------:|:-----------|
|  15 |  67 | cut_against |          1.430 |          -0.030 |     0.194 | 1295542.240 | True       |
|  15 |  67 | boost_with  |          1.349 |          -0.111 |     0.393 | 1312464.720 | True       |
|  15 |  67 | both        |          1.608 |           0.148 |     0.547 | 1594874.880 | True       |
|  15 |  80 | cut_against |          1.449 |          -0.011 |     0.090 | 1328995.200 | True       |
|  15 |  80 | boost_with  |          1.244 |          -0.216 |     0.252 | 1193996.560 | True       |
|  15 |  80 | both        |          1.394 |          -0.066 |     0.319 | 1325265.920 | True       |
|  30 |  67 | cut_against |          0.969 |          -0.491 |     0.185 |  863079.680 | True       |
|  30 |  67 | boost_with  |          1.252 |          -0.208 |     0.411 | 1240706.480 | True       |
|  30 |  67 | both        |          1.388 |          -0.072 |     0.551 | 1307980.400 | True       |
|  30 |  80 | cut_against |          1.106 |          -0.354 |     0.111 | 1031973.440 | True       |
|  30 |  80 | boost_with  |          1.309 |          -0.151 |     0.273 | 1274358.800 | True       |
|  30 |  80 | both        |          1.283 |          -0.176 |     0.361 | 1255046.000 | True       |
|  60 |  67 | cut_against |          1.303 |          -0.157 |     0.177 | 1191106.720 | True       |
|  60 |  67 | boost_with  |          1.300 |          -0.160 |     0.429 | 1255476.400 | True       |
|  60 |  67 | both        |          1.465 |           0.005 |     0.554 | 1384578.320 | True       |
|  60 |  80 | cut_against |          1.391 |          -0.069 |     0.085 | 1278091.200 | True       |
|  60 |  80 | boost_with  |          1.345 |          -0.114 |     0.271 | 1320099.680 | True       |
|  60 |  80 | both        |          1.380 |          -0.079 |     0.339 | 1341325.920 | True       |

**Verdict: NO** (0/6 measured gates pass; D1-harness class NO). Carried cell W=15 q=67 mode=both; all-in Sharpe uplift clean/H1/H2/all +0.15/-0.36/-0.36/-0.03. Runtime 33.0 min, 7-worker pool. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules (per-book 5R/-2R, day lock 8R/2R/67%, week floor -8R, per-book week rule off).

REPORT-ONLY comparison: identical BK4 cells with NQ own signed-volume (DRIVERS per-minute aggregates vb/vs, 24h) in place of the basket flow.

## Clean-only selection grid

|   W |   q | mode        |   clean_sharpe |   clean_dsharpe |   changed |   clean_net | eligible   |
|----:|----:|:------------|---------------:|----------------:|----------:|------------:|:-----------|
|  15 |  67 | both        |          1.608 |           0.148 |     0.547 | 1594874.880 | True       |
|  60 |  67 | both        |          1.465 |           0.005 |     0.554 | 1384578.320 | True       |
|  15 |  80 | cut_against |          1.449 |          -0.011 |     0.090 | 1328995.200 | True       |
|  15 |  67 | cut_against |          1.430 |          -0.030 |     0.194 | 1295542.240 | True       |
|  15 |  80 | both        |          1.394 |          -0.066 |     0.319 | 1325265.920 | True       |
|  60 |  80 | cut_against |          1.391 |          -0.069 |     0.085 | 1278091.200 | True       |
|  30 |  67 | both        |          1.388 |          -0.072 |     0.551 | 1307980.400 | True       |
|  60 |  80 | both        |          1.380 |          -0.079 |     0.339 | 1341325.920 | True       |
|  15 |  67 | boost_with  |          1.349 |          -0.111 |     0.393 | 1312464.720 | True       |
|  60 |  80 | boost_with  |          1.345 |          -0.114 |     0.271 | 1320099.680 | True       |
|  30 |  80 | boost_with  |          1.309 |          -0.151 |     0.273 | 1274358.800 | True       |
|  60 |  67 | cut_against |          1.303 |          -0.157 |     0.177 | 1191106.720 | True       |
|  60 |  67 | boost_with  |          1.300 |          -0.160 |     0.429 | 1255476.400 | True       |
|  30 |  80 | both        |          1.283 |          -0.176 |     0.361 | 1255046.000 | True       |
|  30 |  67 | boost_with  |          1.252 |          -0.208 |     0.411 | 1240706.480 | True       |
|  15 |  80 | boost_with  |          1.244 |          -0.216 |     0.252 | 1193996.560 | True       |
|  30 |  80 | cut_against |          1.106 |          -0.354 |     0.111 | 1031973.440 | True       |
|  30 |  67 | cut_against |          0.969 |          -0.491 |     0.185 |  863079.680 | True       |

## Carried cell vs baseline pair (clean / H1 / H2 / all-in)

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.61 |
| clean | Sortino | 2.78 | 3.12 |
| clean | MAR | 4.75 | 3.94 |
| clean | net $ | 1,329,958.72 | 1,594,874.88 |
| clean | maxDD $ | 280,109.76 | 404,922.56 |
| clean | worst wk $ | -81,873.92 | -82,605.20 |
| clean | CVaR5 $ | -78,735.52 | -79,785.40 |
| clean | CVaR10 $ | -78,008.81 | -78,770.59 |
| clean | % neg wk | 42.86 | 42.86 |
| H1 | weekly Sharpe | 2.83 | 2.47 |
| H1 | Sortino | 6.09 | 5.29 |
| H1 | MAR | 3.91 | 4.65 |
| H1 | net $ | 593,797.44 | 618,720.40 |
| H1 | maxDD $ | 151,712.64 | 132,990.96 |
| H1 | worst wk $ | -78,287.36 | -78,869.44 |
| H1 | CVaR5 $ | -77,609.92 | -78,430.20 |
| H1 | CVaR10 $ | -66,029.97 | -77,940.05 |
| H1 | % neg wk | 39.29 | 35.71 |
| H2 | weekly Sharpe | 2.30 | 1.94 |
| H2 | Sortino | 4.69 | 3.74 |
| H2 | MAR | 3.50 | 2.33 |
| H2 | net $ | 761,254.40 | 603,564.96 |
| H2 | maxDD $ | 217,425.28 | 259,423.76 |
| H2 | worst wk $ | -82,524.48 | -79,222.72 |
| H2 | CVaR5 $ | -81,088.96 | -79,081.64 |
| H2 | CVaR10 $ | -79,185.12 | -78,551.56 |
| H2 | % neg wk | 44.44 | 36.11 |
| all | weekly Sharpe | 1.86 | 1.83 |
| all | Sortino | 3.63 | 3.57 |
| all | MAR | 9.59 | 6.96 |
| all | net $ | 2,685,010.56 | 2,817,160.24 |
| all | maxDD $ | 280,109.76 | 404,922.56 |
| all | worst wk $ | -82,524.48 | -82,605.20 |
| all | CVaR5 $ | -79,220.34 | -79,622.72 |
| all | CVaR10 $ | -78,243.12 | -78,686.14 |
| all | % neg wk | 42.86 | 40.48 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.148 / -0.361 / -0.356
- [FAIL] 3 worst week not worse (all-in): -82,605 vs baseline -82,524
- [FAIL] 4 matched family null p95: real -0.030 vs p95 +0.143 (median -0.203, rank 0.76, n=500)
- [FAIL] 4 bootstrap 90% CI >0: [-0.523, +0.464]
- [FAIL] 5 plateau: 0% of 4 neighbours keep >=75% of uplift
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.410 / -0.394 / -0.903
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md BATCH I); 2 selection on clean only, H1/H2 read once; 6 n/a (pair change, not a hedge claim); 7 see below

Plateau neighbours (all-in uplift):
- {'W': 11, 'q': 67, 'mode': 'both'}: -0.271
- {'W': 19, 'q': 67, 'mode': 'both'}: +0.035
- {'W': 15, 'q': 50, 'mode': 'both'}: -0.590
- {'W': 15, 'q': 84, 'mode': 'both'}: -0.187


DONE BK4N

Basket-flow vs NQ-flow F30 correlation (RTH minutes): 2023: +0.557; 2024: +0.589; 2025: +0.492; 2026: +0.380


DONE BASKET
