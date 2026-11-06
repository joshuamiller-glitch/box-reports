# IDEAS_ROUND2_20261106 - idea round (CHAR-A, lookups only, no compute, no purchase). Shadow only; nothing here is a result.
**Read first.** I read WHAT_IS_DEAD_20261105.md, DS3_FIND_FINAL.md (+ corrections), DS3_INSTR2_FINAL.md, DS3_FIND_DAILY.md, DS3_REPLICATION.md, FADE_NTESTED.md, the DEAD_CELLS ledger program list (422 programs, 2,086,460 rows), and, because the ledger does not hold the September/October autopilot cells, PREREG_AUTOPILOT.md (cycles C1-C11, B2356 batches X/Y/Z/W/V/U/T/S), REPORT_IDEAS50K_N2..N9 (about 50,000 cells: event-time, vol, session legs, roll windows, cross-sectional, pair and calendar spreads, multi-hour indicators, cross-asset lead-lag), REPORT_BASKET.md, DS3_HEDGE_*.md, DS3_STACK_*.md, DS3_FWD_DD.md, EXEC_SUMMARY.md. **Honest premise: this box is close to saturated for strategy search on the data it owns.** Almost every 'structure the box has not examined' that the lead listed has a prior test (table in section 3). The ideas below are therefore either (a) a different STRUCTURE (replication across products of the only tick-scale regularity found), (b) a measurement that changes the cost wall instead of searching, or (c) honest documentation/decision support. I rank them and say which could clear the diversifier bar.
Cost-wall numbers used (all measured/cited): taker round trip ES 1.39 ticks, RTY 2.97, NQ 3.97 (spread + $4.84 fee; DS3_FIND_CHARACTER 1b-a); maker per order ES -0.35, RTY -0.94, NQ -1.73 ticks (1b-d); 1-min proxy round trips ES $42, RTY/YM $20, NQ $45, GC/CL $35, ZN $52, ZB $99 (CHAR room tables); NQ stop-market slips +1.44 pt at 10 lots (DS3_DN_STOPFILL.md). Diversifier bar = tolerant gate + forward-only placebos + family max-stat + own walk-forward + |corr to NQ stack| <= .3 + stack Calmar up carry-dropped.

## 1. The programs (ranked)
### R1. Cross-product replication of the tick-scale prior-day-level touch, on 1-second OHLCV only (GC CL ZN 6J NKD + ES NQ RTY as the bar-based control)
* Data (owned, no purchase): /mnt/l2/l2vast/instr_1s {GC 27.6M, CL 24.4M, ZN 12.7M, ES 41.4M, NQ 46.1M, RTY 24.2M 1-s bars, 2023-02..2026-10-16}; 6J and NKD 1-s tapes ds3/discover_data/*_ohlcv1s_20230401_20261031.dbn.zst (CHAR-C's 1-s block).
* Mechanism: the only tick-scale regularity this project found (first touch of the prior-day high/low continues over 30 s-30 min: ES +2.55 ticks/60 s p_fam .049, RTY pre-market +13 ticks/30 min p_fam .016, NQ NY-AM 30 s) is either structural stop-run/level behaviour (then it should replicate on other deep markets) or an equity-index regime (then it will not). One cheap cross-product test decides which, with the bar-based definition that the planned ohlcv-1s pull can compute forward (WATCH_NQ_PDL_SPEC.md).
* Novelty evidence: prior-day-level books are in the ledger only for NQ/ES/RTY/YM at 1-min (REACTLEVELS 3,120, FADE_LV 1,034, T2F_*; WHAT_IS_DEAD F1/F4) and on L2 for ES/RTY/NQ (T2F*_1B*, 1B_DEEP*); grep of the ledger/pages finds NO 5 s-30 min level-touch cell on GC, CL, ZN, 6J, NKD. CHAR maps (1-min, 0.5A/60 min) show GC/CL levels break through slightly (VW1 47% vs 49%; CL PD|asia bounce 42% vs 47%) and ZN bounces 55-64%: opposite signs at the 1-min scale, so the tick scale is a genuinely open question.
* Cost-wall check: bar data carry no spread, so costs use the instr2_sessions proxies (GC/CL $35, ZN $52, 6J $25, NKD $129.8); on the ES analogue the gross at 60 s was 2.55 ticks against 1.39 ticks cost (room 1.8x); GC ($10/tick) and CL ($10/tick) need >= 3.5 ticks gross, ZN 3.3 ticks of 1/64; unmeasured until step 1. Step 1 (1 hour of compute) is a gross-move table, cost applied only if gross > cost.
* Power: bar-based NQ replay gave 561 events over 3.2 years (about 175 per year, both sides); expect 100-180 per year per product for NY-AM/pre-market windows (to be counted) = 300-550 per product, adequate for a +2-tick/60 s effect (sd about 12 ticks) at t about 3.
* Compute: 1 worker-hour per product with the fixed simulator (instr2_eval_1s.py, bar_s explicit); family = 8 products x 2 sessions x 5 horizons x 2 classes = 160 cells, shuffled-level transplant null B=200.
* Pass bar: p_family <= .05 on the pooled non-index products (GC CL ZN 6J NKD, 5 products, one family), same sign in >= 70% of years, corrected-simulator book net > 0 after proxy cost with placebo p <= .10; otherwise the effect is classified INDEX-REGIME and the three WATCH items stay watch/kill items. Chance of clearing the diversifier bar: low (about 5-10%): even a positive replication gives a small book on thin products (CAP and cost). Value: high (it is the cheapest test that can promote or demote the whole tick-scale WATCH family).

### R2. Measured-cost recalibration of every saved trade frame ('cost-gap map')
* Data: raw mbp-10 ES/RTY/NQ 2023-08+ (raw/ES 185 GB, raw/NQ, raw/RTY), the trade frames in /mnt/l2/l2vast/instr2_trades (stop_px/tgt_px/entry_px/exit_px; 6,704 parquet frames on disk).
* Mechanism: all 1-min books are charged proxy slippage (ES $42 round trip = 0.85 pt incl. stop slip) while the measured taker cost on ES is 1.39 ticks = $17 and the measured NQ 10-lot stop-market slip is +1.44 pt; the proxies are wrong in both directions by order type and size. A measured fill walk per order type (market in, resting target, stop-market) turns every frame's net P&L into a measured one.
* Novelty: DS3_DN_STOPFILL.md did this for the DN book only; no ledger program re-scores T2*/T2F*/FIND* frames at measured fills (ledger program list); my own FINAL page flags the cost-basis mix (Section 4 first bullet) without resolving it.
* Cost-wall check: this IS the cost wall: a cell within +-1 tick of break-even changes sign; cells with gross >> cost do not. Random-side placebos pay the same cost, so family p barely moves; what moves are the absolute gates (tolerant, Calmar).
* Power: all saved trades (tens of thousands). Compute: about 6 worker-hours (book walk per trade, DN_STOPFILL machinery). Pass bar: no strategy is promoted by this alone; deliverable = per-book measured cost vs proxy table and a re-run of the tolerant gate; any cell that then clears the FULL bar is flagged. Chance of a diversifier clearing: about 5%. Value: removes the largest unresolved uncertainty in the cost-walled families.

### R3. Capital, margin and micro-granularity audit of the live stack + the WATCH register (documentation for the user's decisions)
* Data: Q1-A ts2 weekly/daily P&L, saved lots, instr2_sessions caps, S4a's margin proxies (stated assumptions, unverified), the watch specs.
* Mechanism: several items change when contracts are integers (CMD4 rounds from 0.4-0.7 lots to whole contracts and the book changes; the Monday long is $690 per MNQ sd vs $6.9k per NQ; NQ-lot equal-risk for the 30-s book is 14 contracts). A single table of lots, margin, sd, max loss and kill thresholds per item and combined with the stack gives the user what the decisions need.
* Novelty: DS3_FWD_DD.md (stack tail), SIZER_* (lot arms), DS3_STACK_* exist; nothing joins the WATCH items with margin and micro rounding.
* Cost-wall/power: n/a. Compute: lookups plus 1 worker-hour. Pass bar: none (documentation). Chance of discovery: 0%.

### R4. One sequential-evidence plan for all WATCH items (pooled, SPRT-style, pre-registered boundaries)
* Data: the watch specs, their historical sd and event rates (RTY pre-market 8 events/quarter, NQ 30-s 3.3/week, Monday 1/week, CL Donchian 1 episode every few weeks).
* Mechanism: each spec has its own fixed-sample criterion; at event rates of 3-8 per quarter the fixed samples take 4-5 years. Two things shorten that honestly: (a) pooling items that share one hypothesis (index prior-day-level touch on NQ/ES/RTY, Monday on four indices) in a hierarchical test; (b) SPRT/mixture boundaries fixed now.
* Novelty: SPRT appears in FORWARD_SHADOW_ZONES_SPEC.md and DS3_BT_SWING_FLIP_CANDIDATE.md (single items); no pooled plan across the register.
* Compute: lookups. Pass bar: boundaries and expected sample size under H0/H1 tabled. Chance of discovery: 0%; value: decision speed.

### R5. Tick-scale calendar-spread / roll-window microstructure on ES, NQ, RTY (back months are in the 1-s tables)
* Data: tables/<SYM>/1s include the second contract (instr column; used in the front-contract selection); raw mbp-10 all months.
* Mechanism: dislocations of the front-back spread around the quarterly roll (volume migration, wider spreads) mean-revert toward cost of carry at seconds-minutes; market-neutral, so corr to the stack should be about 0.
* Novelty: calendar spreads were tested at 1-minute (N20, 'intraday calendar-spread books from per-contract 1-minute files': 0 passes, DECISIONS 2026-10-19) and the roll window directionally (S9, B-batch); no tick-scale/L2 spread study (N3 listed the NQ second month as unscorable then).
* Cost-wall check: two legs, 2 x 1.39 ticks taker on ES before any spread-order discount; the spread's own tick and depth are unmeasured (step 1 = measure). Prior is low: the spread range around roll is a few ticks.
* Power: 4 rolls a year x 3.2 years = 13 roll windows per product: very low power; non-roll days add little. Compute: 4 worker-hours. Pass bar: family p_family <= .05 and passive-in/market-out net > 0 with >= 300 fills. Chance: about 3%.

### R6. Daily/weekly trend + vol-targeting on the 15 outrights S4a never scored (NG RB HO SI HG PL ZC ZS ZW LE HE ZF ZT 6A 6B 6C)
* Data: ohlcv1m 26 outrights 2013-2026 (owned; 'extra 1-min outrights owned (not requested)', INSTR2_DATA_INVENTORY.md). S4a's T2F_DAILY_* ledger covers 11 instruments only.
* Mechanism: classic cross-asset time-series trend on markets uncorrelated with equity indices; cost small vs multi-day moves (room: a 1-tick cost against a daily ATR of 50-300 ticks).
* Novelty: PARTIAL OVERLAP: IDEAS50K N7 (TREND-GC, RSI), N10 (XS rank books incl. COMM), N13 (NG/CL-neutral ranks), C1-F3 (carry + XS momentum, 26 markets), X1-Z10 (short-horizon on ALL26) touched these markets; daily time-series trend/breakout/MA-cross at multi-month lookbacks on the 15 was not part of S4a's 11. So it is an extension, with multiplicity and prior evidence (carry/XS momentum NO) both against it.
* Power: 13 years x 15 markets; family 15 x 34 (S4a grid) = 510 cells. Compute: 2 worker-hours (S4a code unchanged). Pass bar: S4a's LEAD rule. Chance of clearing: about 5% (S4a on 11: 0 of 408).

### R7. Quote-only: pre-2023 L2 sample for ES/NQ/RTY (information value, needs the user's OK; metadata cost quote only)
* Mechanism: every tick-scale row says 'no pre-2023 evidence'; a 1-month-per-year mbp-10 sample 2018-2022 would give the first out-of-era read of the prior-day-level touch (about 14 events per product-month, so 12+ months are needed for power; a quote decides feasibility).
* Novelty: WHAT_IS_DEAD 'Not run' lists data purchases pending the user's OK; no quote exists for pre-2023 L2.
* Compute: none until bought. Pass bar: effect size and sign consistent with 2023-26 at p <= .10 on >= 150 events. Chance of promoting an item: unknown, depends on price; documentation otherwise.

## 2. Ranking and recommendation
| rank | program | realistic chance to clear the diversifier bar | role |
|--|--|--|--|
| 1 | R1 cross-product replication (1-s OHLCV) | low (5-10%) | decisive and cheap: promotes or demotes the whole tick-scale WATCH family; also yields the bar-based definition for the forward feed |
| 2 | R2 measured-cost recalibration | ~5% | resolves the cost-wall uncertainty behind the 'tolerant' counts; documentation with possible sign flips |
| 3 | R3 capital/margin/micro audit + R4 sequential plan (one deliverable) | 0% | decision support: lots, margin, kill rules, expected time to resolution |
| 4 | R6 extend S4a to the 15 unscored outrights | ~5% | completeness; multiplicity and prior against it |
| 5 | R5 tick-scale calendar spreads | ~3% | low power (13 roll windows) |
| 6 | R7 pre-2023 L2 quote | n/a | information value; needs the user |
**Recommend the top 3: R1, R2, and the R3+R4 document.** Plain verdict: NONE of the seven has a realistic chance (> 15%) of producing a validated diversifier; R1 and R2 can change what the existing WATCH items and cost-walled families mean, R3/R4 are documentation. If the user wants a diversifier hunt rather than a closure, the evidence of this project is that it needs a different data class (non-CME venues, options, a bigger cost-advantage such as maker rebates), none of which is owned.

## 3. Ideas the lead listed that were already tested (do not repeat)
| idea | where it was tested | note |
|--|--|--|
| NQ/ES basis, spreads | Q14 (96 cells, all lose), N15 daily pair spreads (41,370 cells, 0 gate passes), N20 intraday calendar spreads (0 passes), CHAR-B RV pages (ESRTY, ESYM, RTYYM, ZNZB, 6E6J), Z8/DIS-G | tick-scale spread study is the only gap (R5) |
| roll windows | S9 (5 days before roll; ES NQ RTY YM ZN), C9-R1 roll-week avoid filter, N3-ROLL, N20 | directional windows done |
| opening auction / MOC imbalance | not testable: no MOC imbalance feed owned (WHAT_IS_DEAD 'Not run') | needs data |
| end-of-day settle/close at tick scale | 1b-a session and hour cells incl. the 15:00-16:55 close; CL 14:30 settlement and GC fix native books (DS3_INSTR2_NATIVE.md); S7 month-end afternoon; LASTHOUR (N11) | covered; ES close 30-min trend +0.052 (CHAR ES) is a documented map row |
| mean-reverting weekend gap on 24h products | T1/T2/T6 (Monday gap fade, 6 classes), W6/V3/V4, native BTC/MBT Sunday-open gap, NKD, my Monday follow-up | dead/regime |
| MBT/BTC vs NQ lead-lag at seconds | NOT testable: MBT/BTC owned at 1-min only (2022-01+); at 1 minute NQ leads MBT by one bar (+0.02..+0.05, CHAR MBT); DIS-C weekend jump coincident, not predictive | needs 1-s crypto data (purchase) |
| volatility-clustered sizing of the books | B17 (trailing realised-vol sizing), VOLSCALE_DEC, A3SZ, SIZER_* (dozens), E1 vol targeting; INST-4 vol-state regime NULL | dead |
| multi-book risk parity / portfolio construction | U2 inverse-vol book, C1-F2 allocation rule, B19 book tilt, DS3_STACK_* (A..F), DIS-T watch-bundle portfolio, SIZER_Q1A | dead; only the margin/granularity audit (R3) is new |
| MNQ-short hedging overlay in drawdown regimes | B8 conditional hedge (24 cells), HEDGE1/HEDGE-ASM/HEDGE_DEC, DS3_HEDGE_DECISIVE.md | dead |
| daily/multi-day on ZN/GC/CL/6E | S4a T2F_DAILY (408 cells), my T2F_DAILY2, Z1 DAILY4, C1-F3 carry/XS momentum, C7-P1, C10-S1, S3/S4 skew/carry, IDEAS50K N3/N7/N10/N13 | dead / best-of-F |
| lead-lag / cross-asset | DISC_A (768 census tests), N13, N16-N19 (one gate pass N16-F1-RTY, not replicated), V1, W3, W8, S6 | dead |
| event-day books | V2/V8 (FOMC/NFP), Addendum A native (EIA, OPEC, refunding, BoJ), Q10 earnings, DIS-F | dead |
| open-type, semivariance, volume-clock, IB-extension (IDEAS_FV15 I1-I5) | dispatched 2026-10-17 to the FV16 worker (DECISIONS 564); FV15/SX results NO | I3/I5 variants also appear in CHAR maps (IB extension shares, day types) |
