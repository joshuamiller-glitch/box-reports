# DS3_NEW_DATA_CANDIDATES - seven outside-data candidates: quotes (nothing bought), ranking, test designs, free pilots 5-7 (W-ND)
REFRESH 2026-11-17 (answers the lead's 4-point order; sections 14 below): (a) Kalshi implied-consensus surprise test run: 212 events / 87 release times 2023-04..2026-08, 58 cells, ALL NO-ACTION (flagged trades < 10 in L6M or L3M: the book almost never has a position or a new entry around an 08:30 release now); history-only skip-gain percentile >= 0.90 in 4 of 58 cells (5.8 expected by chance), 0 <= 0.10: chance level. (b) The free Asia / VX sets (Binance perp, Yahoo HSI, CBOE VX settles, owned NKD/6J 1-min) were ALREADY run on the full 2023-04..2026-10 history in pilots 6 and 7 (sections 4, 5b; the September-only runs in sections 11-12 are the paid 1-s data); only HSI (Yahoo, about 2 years) and intraday VIX (DBIX from 2025-12) are shorter and cannot be extended free; the only free extension left is NKD/6J/NIY ohlcv-1s full history (quote $0.00) which is outside the user's approved item, so NOT downloaded. (c) ES order-by-order does NOT reproduce the NQ lead (opposite sign on ES; best-of-12 nonsense bar not beaten) -> do not buy the full history; auction imbalance: no tier possible (no recent action surface). (d) Per-item recommendations in section 14.
UPDATE 2026-11-16 ~23:00Z (user-approved purchases made, first tests run; data ends: ES MBO 2026-10-30, auction imbalance 2026-11-09, Asia 1-s and VX 2026-09-30, trade list 2026-10-30; FIRST PASS, in-sample, path arithmetic on JL2, no engine re-run): BOUGHT $77.41 in total (ES MBO Aug+Sep+Oct 2026 $52.95; auction imbalance 8 megacaps 2023-04..2026-11-10 $6.39 + QQQ $0.80; VX ohlcv-1m 2026-09 $17.27; NKD/6J/NIY bbo-1s + trades 2026-09 $0.00). RESULTS: (1) ES order-by-order at NQ entry seconds does NOT reproduce the NQ lead: frozen arrival-imbalance lead on ES has the OPPOSITE sign (ES60 lo lift -$226/trade, t -2.3; the NQ reading in the same 3 months +$175, t 1.8, same sign as its history); ES-minus-NQ divergence and ES coefficient beside NQ (t -2.35) are nonzero but in the wrong direction for the frozen rule; the one row above the single-test nonsense bar (ES30 hi, +$369, t 3.99, concentrated in Asia and P7) is below the best-of-12 nonsense 99th percentile (4.47) and 3 shifted-session controls reach |t| up to 3.1 on the NQ row; in-trade ES turn cuts make the L3M ulcer worse everywhere except one small NY AM cell (113 cuts, +2.4%, mean +$342); decision rule -> do NOT buy the ES full history ($984.71). (2) Auction imbalance: no tier can be issued (O7 entries L6M 50 / L3M 22; positions open at 15:50 L6M 24 / L3M 9; every cut cell is NO-ACTION or FAIL); 72 real O7 entry cells = 50 FAIL / 22 NO-ACTION, nothing above the nonsense rate; history-only associations (not recent): positions carried through the 09:30 open earn LESS when the opening imbalance is with them (Spearman -0.14, n 974, beats 3 of 3 shifted days and 100% of 200 permutations) but a 09:31 cut does not capture it, and positions held into the close earn LESS when the closing imbalance is against them (+$32 vs +$303 per trade, Spearman +0.16, n 331, PRE windows only): both are watch items, not results. (3) Asia drivers (one month, September): the family is above its nonsense rate for the first time, driven by 6J: in-trade turn against 35% of 31 real cells pass the strict one-month screen vs 8% of 12 nonsense cells (6J trade-aggressor imbalance 5 min, 6J 5-min move, NIY-minus-NKD), entry cells 11% vs 3%; the 6J London move is the same lead found on owned 1-min history in pilot 6; one month cannot settle it; the cheap next step is 6J trades history ($33.13 quoted 2023-04..2026-11), NOT bought, needs your approval. (4) VX one month: at chance (17% of real entry cells vs 25% of nonsense cells pass the loose smoke screen; 0 of 15 in-trade). Earlier verdict (21:35Z, before any purchase) follows. 
VERDICT (data ends 2026-10-31; for the trade list, features to 2026-11-14; FIRST PASS, in-sample, path arithmetic on JL2, no engine re-run): NOTHING WAS BOUGHT; 78 Databento get_cost quotes logged (QUOTES_NEWDATA.csv + MORNING.md). Ranking by novelty against what we own, cost and the evidence that order flow at the entry second is what has worked here: 1 ES order-by-order ($52.95 for 3 months), 2 auction imbalance ($0.17 pilot month for the 8 megacaps + QQQ), 3 megacap tape extension and order-by-order, 4 Asia drivers (free pilot run), 5 macro surprise (free pilot run: almost no action surface left in the current books), 6 VX / VIX tape (free pilot run), 7 dealer-gamma API (no 2023 history for sale). Free pilots 5, 6, 7 on 18,979 JL2 trades: 0 of 364 + 384 + 162 real cells beyond the nonsense rate; the corrected tiers fired on 10 of 384 real Asia-driver cells (2.6%) against 8 of 160 nonsense cells (5.0%), so the family is at chance; the one item worth a second look is the Nikkei 4-hour return against the trade (half size, Asia, bottom 20%: ulcer -14.8% L6M / -18.1% L3M, mean +245 $/wk L6M, but mean -874 HOLD and -784 PRE, bootstrap P(ulcer lower) 0.97), a LEAD at best. Items 1-4 are quotes and designs only.
Header line (desk standard 5): trials counted: pilots 5/6/7 = 162 + 544 + 115 + 524 cells (TRIALS_LEDGER NDP5/NDP6/NDP6C/NDP7 + _COUNT rows); correction: family null from 160+60+160 NONSENSE cells and 3 shifted (11/23/37) + 3 permuted labels + 30 persistent random draws per cell, tiers from cutoffs_ulc.json, no White/SPA/DSR run (first pass; nothing survives to need it); PBO: not applicable (fixed training-quantile thresholds, no fitted choice); numbers shown are in-sample (thresholds from exit days before 2025-11-01, scored on all windows).
Prereg: NEWDATA_PREREG.md (sha256 a72769c25c8ee20aef9c274c9fc5a755fe7d1bf83eb1b0be11a7ebce5dbe5d89, in DECISIONS.md before any scoring). Code: code/th_newdata. Bulk free data: /mnt/l2/l2vast/_newdata. Fees: engine dollars are BASE lots; x1.75 live and the $4.84 RT column are scale factors, not applied.

## 1. The table (Databento quotes by metadata.get_cost, USD; pilot month = 2026-09-01..10-01; FULL = 2023-04-01..2026-11-10; 3-month = 2026-08-01..11-01)
| # | item (what is quoted) | one-month pilot | full 2023-04..now | live cost per month | can D7 compute it live? | expected overlap with what we own |
|---|---|---|---|---|---|---|
| 1 | Megacap cash tape, XNAS.ITCH, 8 names (NVDA MSFT AAPL AMZN GOOGL META AVGO TSLA). trades / bbo-1s / tbbo / mbp-1 / mbo | $5.51 / $1.37 / $9.18 / $13.12 / **$42.15** (mbp-10 $39.39) | $294.68 / $58.70 / $491.14 / $705.06 / **$2,212.25** (cheaper consolidated: EQUS.MINI trades $58.97, bbo-1s $44.84; XNAS.BASIC tcbbo $1,252 from 2024-07) | Databento Standard $199 (CME only listed); live Nasdaq ITCH not confirmed on the public page; "quote not obtained" for a Nasdaq feed into NT8 | yes if a live equity feed exists (NT8 has no ITCH); needs an external process | HIGH for the cheap form: the L6M package (megacaps trades + bbo-1s, 2026-05-01..11-10, $62.5 with QQQ/SMH) is owned and was null (DS3_CROSS: 0 stable cells in entry, loss cut, near-zone; megacaps LAG NQ at 1 s, corr 0.154 vs 0.001). NEW: pre-2026-05 history (bbo-1s about $50, trades about $250 more) and order-by-order (never tried) |
| 2 | Auction imbalance, XNAS.ITCH imbalance schema (8 megacaps + QQQ); also NYSE (XNYS.PILLAR) and SPY on ARCX.PILLAR | **$0.17** (8 megacaps; QQQ $0.02); ALL Nasdaq symbols $227.61; NYSE ALL $24.06; SPY $0.28 | 8 megacaps + QQQ **$7.19**; ALL Nasdaq $8,664.50; NYSE ALL $837.45; SPY $11.82 | not obtained (Nasdaq NOII/closing-cross feed; NT8 does not carry it) | yes at 09:25-09:30 and 15:50-16:00 ET if a feed exists; the windows are short | NONE: never tested; only a calendar flag for auctions exists (UWBOOKS/calendar) |
| 3 | ES order-by-order, GLBX.MDP3 mbo ES.v.0 (NQ.v.0 and RTY.v.0 for reference) | **$23.02** (NQ same month $41.52); 3-month **$52.95**; RTY 3-month $18.87 | **$984.71** (608 GB billable; disk free 216 GB so it must be reduced on server 2 as it lands) | Databento Standard $199/month (CME, no licence fees per the public page); NT8 has depth, not order-by-order | yes via an external Databento live process (same route as any live NQ L3 feed) | MEDIUM: NQ MBO is owned for all 43 months and the L3 arrival-imbalance reading is the strongest single condition found (CF2); ES mbp-10 per-second features are owned and were null/recents-only; ES order-by-order is NEW |
| 4 | Intraday dealer gamma 0DTE. GEXBot Classic $50 / State $150 / Orderflow $250 / Quant $350 (+ Research add-on $50); FlashAlpha Free $0 (5 calls/day) / Basic $79 / Growth $299 (0DTE) / **Alpha $1,499** (historical API) | GEXBot Quant $350 (one month gives 90 days of 1-s snapshots); FlashAlpha Alpha $1,499 | GEXBot: no 2023 history for sale (rolling 90 days only; EOD reports); FlashAlpha Alpha $1,499 for the whole archive (stated "back to 2017", SPX from 2022-01-05, no native futures replay) | GEXBot Quant $350; FlashAlpha Growth $299 | yes by HTTP/WebSocket from an external script | HIGH: UW GEX/greeks, OPRA open interest (NDX/NDXP FULL bought, $251), CME NQ/ES options 2023-04..now, HAR + CME range forecast (T-RANGE2), the QQQ gamma press on the old base. History point-in-time: GEXBot says values are "calculated live on the trading day" (point-in-time, 90 days only); FlashAlpha says its replay has "no lookahead" but its own comparison page says results come from the current engine over archived inputs (not reproducing the live value): treat as NOT point-in-time. SpotGamma: no public API |
| 5 | Macro release surprise. Actual + prior: ALFRED first prints (owned, free). Consensus: Benzinga calendar API (fields actual/consensus/prior; price not public: "quote not obtained"); Trading Economics (official page lists no prices; third-party listings $149-199/month Standard, $299-399 Professional, trial about $49 for a week, 100 requests: unverified) | **$0** (free sources; Kalshi implied expectation from the owned hourly ladder, market-reaction surprise from owned ZN/ES/6E 1-min) | **$0** for actual/prior + market reaction + Kalshi (2022/23-on); consensus feed unknown | $0 for the market-reaction surprise (computed from ZN at the release minute); consensus feed price unknown | yes (reaction measure) | HIGH for the calendar (T-CAL, DS3_FEEDS_F2_F4: actual-prior null at 270 events); NEW only consensus and the reaction measure |
| 6 | Asia drivers. GLBX NKD / 6J / NIY: bbo-1s, trades, tbbo. Hang Seng / China A50: not on Databento (symbols do not resolve; HSI.v.0 MHI CHN A50 MCH all error) | **$0.00** for NKD, 6J, NIY (all schemas, 1 month) | bbo-1s: NKD $38.43 (history already owned $45.52 + L6M), 6J $49.23, NIY $47.35; trades NKD $3.89, 6J $33.13, NIY $10.82; tbbo 6J $55.22; ohlcv-1s $0.00 for all three | CME live: Databento Standard $199 (or the existing NT8 feed for NKD/6J, which D7 already reads) | yes (CME products) | HIGH: 1-min NKD/6J/ZN/YM and 1-s NKD bbo (full) and 6J (L6M) owned; T-CROSS and T-FEEDS found them null as a family, one NKD imbalance lead at the 80% second. NEW: NIY, BTC perp (free), Hang Seng hourly (free, Yahoo) |
| 7 | VX futures (XCBF.PITCH VX.FUT, all expiries) and VIX intraday. DBIX VIX family 1-min owned from 2025-12-07 | ohlcv-1m **$17.27**; ohlcv-1s $45.74; trades $75.87; tbbo $126.45; bbo-1s $191.01 | ohlcv-1m **$912.49**; ohlcv-1s $2,946.93; trades $5,050.01; tbbo $8,416.72; bbo-1s $13,596.03 (L6M ohlcv-1m $123.42) | Cboe live VX not confirmed on the Databento page; free delayed Cboe VIX 1-min JSON exists (cdn.cboe.com delayed quotes, terms apply) | yes (VIX); VX futures need a paid feed | HIGH: Cboe daily VIX/VIX9D/VIX3M/VVIX/SKEW (S1) and DBIX 1-min (S1 intraday) already screened first-order; daily VX settles are free and now owned |

Prices checked 2026-11-16 from vendor public pages (FlashAlpha pricing page; GEXBot prices from FlashAlpha's own comparison article dated 2026-09-09, not from GEXBot; Databento pricing page; Trading Economics/Benzinga via search only). Nothing was signed up for. GEXBot's own site returned no price text (JS page): "quote not obtained" from the vendor itself.

## 2. Ranking (what to quote-approve first)
1. **ES order-by-order, 3 months $52.95** (full $984.71). Same instrument family as the strongest owned condition, same entry seconds, 40 times cheaper to try than an NQ-sized history purchase; the test is binary (does the NQ-validated L3 reading appear on ES at NQ entry seconds and ES-minus-NQ divergence). Decide on the 3-month cut before paying for the full history.
2. **Auction imbalance, 8 megacaps + QQQ + SPY, full history about $19** (7.19 + 11.82 + QQQ). Almost free, zero overlap, short windows that match O7 (opening drive) and the close. ALL Nasdaq symbols ($8,664) is not needed: the index drivers are the megacaps and QQQ.
3. **Megacap tape, extension + order-by-order pilot.** The cheap form is already owned and null (megacaps lag NQ). Only two things are new: the history before 2026-05 (bbo-1s about $50) and order-by-order ($42.15 one month for 8 names, $22.10 for 3). Not a top candidate on the evidence; buy the one-month MBO pilot only if item 1 shows ES order flow adds anything.
4. **Asia drivers**: pilot already run free (section 4); buying NIY/6J 1-s history is $47-49 each but nothing in the pilot says it will add; hold.
5. **Macro surprise**: free; the books almost never hold or open positions around 08:30 releases now (section 5); only consensus costs money and the action surface is the constraint, not the data.
6. **VX / VIX tape**: free daily VX is owned; intraday VX is $912 for 1-min full history; the owned DBIX VIX 1-min (11 months) already answers the intraday question first-order.
7. **Dealer-gamma API**: no 2023-04 history can be bought from GEXBot; FlashAlpha's $1,499 archive is recomputed (not point-in-time) and heavily overlaps UW + OPRA + CME options already owned. Last.

## 3. Test designs (one page each; standard for every test below)
Standard (orders 1954Z/2000Z/2028Z): base = JL2 (TL3_EV_JN05W2JL2, exact-engine trades, 43 months); outcome = trade P&L; primary drawdown statistic = ulcer index (RMS of daily drawdown), max DD, worst week and week-clustered bootstrap (2,000 resamples: P(ulcer lower), P(max DD shallower), P(worst week better), 90% interval of the mean change) beside it; percentile among >= 30 persistent-draw controls (one uniform per book x side x 5-minute bucket, same share per book x session, realised share within 0.05 of the real rule, printed); condition rules get the real rule with the label shifted 11 / 23 / 37 sessions and shuffled labels; NONSENSE items (pure random-walk feeds through the identical grid; calibration: pass rate of nonsense vs real); exit rules get a random exit with the same share cut and the same minutes-since-entry distribution; tiers CONFIRMED / LEAD / FAIL from cutoffs_ulc.json; a planted-edge check before any "nothing passes" (done once for the pipeline, section 6); trial ledger row before running; BH 10% on survivor lists, White RC / Hansen SPA and deflated Sharpe on any best-of-N, PBO (CSCV, 12-16 blocks, 1 purge week) on any fitted choice and walk-forward (trailing 26 weeks, next 2); W44-removed column; data-end stamp on every verdict; FIRST PASS label until the engine-exact controls land. Engine run only for finalists.

**Item 1 megacaps.** Readings at the D7 entry second T and in-trade (each minute until exit, trigger on 1/5 s and 1/5/15/60 s windows): (a) cap-weighted 8-name return over 1/5/15/60 s minus NQ return over the same window (lead / lag, signed with the trade); (b) breadth = how many of 8 are moving with the trade (return > 0 in the trade direction over 5 s / 60 s); (c) aggressor imbalance = signed volume of the megacap prints over 1/5/15 s (trades schema) and top-of-book imbalance (bbo / mbp-1); (d) tape speed = prints per second vs the same minute-of-day trailing median; (e) one stock dragging the index: max of (stock return x cap weight) share of the 8-name move, and the leader/laggard dispersion. Order-by-order (mbo): arrival imbalance of resting orders at the touch and first 5 levels per stock, the same L3 arrival construction used on NQ (one reading, then the NQ-validated form applied unchanged, no refit). Which books/sessions: all 7 books, RTH (09:30-16:00 ET: NY AM / NY PM) and extended hours (London, Asia, pre-market: thin tape, flag as separate cell families, not pooled). Uses: entry skip / half, in-trade cut on turning against, near-zone take (the usage family where NKD lead appeared). Controls as the standard, plus a nonsense stock basket (8 random liquid non-NDX names matched on volume) through the identical readings. Windows: owned L6M first (already null), then the bought history; PRE/X' tolerance as ordered. Kill rule: nothing above the nonsense pass rate in L6M and L3M -> stop before buying order-by-order.

**Item 2 auction imbalance.** Readings: for each of the 8 megacaps + QQQ, from 09:25 ET (opening cross) and 15:50 ET (closing cross): imbalance shares and side, paired shares, indicative clearing price vs reference (far / near price), each as signed value in the trade direction, summed with cap weights (index imbalance) and per stock. Test against O7 (opening drive), all books 09:30-10:00, and NY PM entries into the close (15:50-16:00). Readings are taken at the last imbalance message before T (09:30:00 for O7, the entry second otherwise). Quotes: Nasdaq imbalance $7.19 full for the 8 + $0 for QQQ, SPY $11.82, NYSE all $837 (not needed first). Only 2-3 books trade these windows: sample is small (O7 465 trades in 43 months), so the first read is a mean-R and MAE/MFE table with shifted-day controls, and tiers only where flagged n >= 10 in L6M and L3M (otherwise NO-ACTION is printed, as in the pilots). Nonsense: imbalance of 8 random Nasdaq names.

**Item 3 ES order-by-order.** Pull ES MBO for 2026-08-01..11-01 ($52.95), build the same per-second L3 features used for NQ (CF2 H table: arrival imbalance over 5 / 15 / 60 s, pull and add rates, sweep flags at the touch and 5 levels), reading at each NQ entry second in L3M. Tests: (a) the NQ-validated L3 condition, frozen, evaluated on ES at NQ entry seconds (same sign and threshold rule, no refit); (b) ES-minus-NQ divergence in arrival imbalance; (c) turning against an open trade in ES order flow. Books: all 7, sessions pooled and per session (asia thin). Controls: shifted labels 11/23/37 sessions of the ES feature, ES from a non-adjacent period, nonsense = RTY order flow from the same months (quote $18.87 for 3 months; same code path). Decision rule: ES condition reaches LEAD on L3M without a refit, and the NQ-vs-ES partial association is non-zero -> quote the full history ($984.71) and write the live path; otherwise stop. Walk-forward over the 3 months is only a smoke test; the history is what settles it.

**Item 4 dealer gamma.** Readings at T and in-trade: distance to the largest gamma strike (QQQ/SPX mapped to NQ points) in ATR units, sign of net gamma, flip distance, and the change in the 0DTE profile since the open (net gamma and largest-strike shift per 30 min); used as range / target / exit inputs (near-zone take, target scale, give-back), NOT direction. Data: GEXBot Quant one month (90 days of 1-s history) is the only point-in-time candidate; FlashAlpha Alpha for the 2023-04.. archive but recomputed. Controls: the same readings from the shifted day (11/23/37), from our own computed gamma (OPRA OI + CME options, owned), and the HAR range forecast (T-RANGE2) as the benchmark: the vendor must beat HAR + CME on range R2 out of sample and beat own-computed gamma on the dials, else it is a purchase of something we hold. 90 days cannot prove a mean effect (floor +30% mean for a broad rule on 12 months, DS3_PASS_RULE): the only valid first deliverable is an incubation log.

**Item 5 macro surprise.** Readings: surprise = actual - consensus (consensus: Benzinga/TE if quoted, else Kalshi implied median from the owned strike ladder, else prior / trailing mean) in expanding-std units, and the market-reaction surprise (ZN, ES, NQ, 6E move in the release minute, known at T+61 s, live-computable). Uses: size/stand-down windows around releases by surprise size (08:30 macro, 10:00 ISM, 14:00 FOMC), the first 5 minutes after (10:00 and 14:00 only: the books do not enter 08:30-09:59), positions open at the release (cut / half at T+60 s), and day-state for entries in the next 2 hours. Controls: label shifted 11/23/37 events of the same type, permuted, random events with the same count. Power note: see section 5; without recent events the test is history-only and cannot issue a tier.

**Item 6 Asia drivers.** Readings at T and each minute in-trade: NKD, NIY, 6J (yen strength = risk off), BTC perp 1/5/15/60/240-min return signed with the trade, NKD-minus-NQ lead, BTC taker imbalance and perp premium change, Hang Seng last hourly bar; turning against an open trade = signed 5-min move below the training q (0.01-0.05). Books/sessions: Asia (33k of the 74k HOLD drawdown) and London. Controls as the standard plus the NQ-own-return rule as the "is it just NQ trend" comparison. Result: section 4.

**Item 7 VX / VIX.** Readings: VX moving against NQ's direction at T (VIX/VX 5/15/60-min change signed with the trade), in-trade turn, and VX term slope (VX2/VX1 - 1), VX1-VIX basis, rank-250 forms as a chop/trend-day input for dial 9 / the chop call. Daily forms from the free Cboe per-contract settles (causal: used from 16:30 ET of the settle date); intraday from DBIX 1-min (owned, 2025-12-08..) or VX ohlcv-1m ($17.27 pilot, $123 L6M). Controls as the standard (daily labels shifted 11/23/37 sessions). Result: section 5b.

## 4. Pilot 6 (free): Asia drivers on JL2 (first table; data: NKD/6J 1-min owned, BTCUSDT USD-M perp 1-min + premium index + funding from data.binance.vision, ^HSI hourly from Yahoo)
Sources and terms: data.binance.vision is Binance's public market-data archive (public, no key; Binance terms of use apply); Yahoo chart API ^HSI 1h is for personal/research use, bars as revised (point-in-time caveat; only about 2 years, so older windows are NOT RUN for the Hang Seng rows); all downloads on this box only, no key, no payment.
Entry readings (skip or half the trade when the driver, signed with the trade, is in its bottom 10% / 20% training tail; 24 real features + 8 NONSENSE random-walk feeds x 2 q x 2 actions x 5 subsets):
| family | cells | CONFIRMED | LEAD | NO-ACTION (flag n < 10 in L6M or L3M) | FAIL |
|---|---|---|---|---|---|
| real drivers | 384 | 10 (2.6%) | 6 | 50 | 318 |
| NONSENSE | 160 | 8 (5.0%) | 0 | 14 | 138 |
Reading: the real family does not beat the nonsense pass rate; no cell is a result. Leads, all in-sample (ulcer % = improvement vs JL2, + is better; mean = $/wk change on base lots; bootstrap = P(ulcer lower) L6M):
| cell (skip unless noted) | L6M ulcer / L3M ulcer / HOLD ulcer | L6M max DD | mean L6M / HOLD / PRE | pctile ulcer L6M / L3M | bootstrap P(ulcer lower) | tier |
|---|---|---|---|---|---|---|
| NKD 4-h return against, all books, bottom 20%, half | +13.8 / +13.9 / +1.8 | +0.1 | +118 / -1,163 / -684 | 0.89 / 0.81 | 0.84 | CONFIRMED |
| NKD 4-h return against, Asia, bottom 20%, half | +14.8 / +18.1 / +7.4 | +11.9 | +245 / -874 / -784 | 0.97 / 0.97 | 0.97 | CONFIRMED |
| NKD 1-h return against, Asia, bottom 10%, skip | +15.4 / +19.7 / -2.5 | n/a | -1,355 / n/a / n/a | 0.97 / 0.97 | 0.97 | CONFIRMED |
| BTC perp 5-min return against, all, bottom 20%, half | +11.4 / +16.0 / +4.1 | +9.4 | -1,542 / -1,428 / -435 | 0.89 / 0.94 | 0.98 | CONFIRMED (mean falls in every window) |
| 6J 15-min yen strength, London, bottom 10%, skip | +11.7 / +16.0 / -6.3 | n/a | -123 / n/a / n/a | 1.00 / 1.00 | 0.87 | CONFIRMED (mean percentile 0.50, 560 trades) |
| Hang Seng last hour, London, bottom 20%, skip | +7.0 / +12.7 / +15.7 | n/a | +747 / n/a / n/a | 0.92 / 0.92 | 0.74 | LEAD (X' not run: HSI covers about 2 years) |
Honest reading: (1) the real-feed pass rate is below the nonsense rate, so any one of these is what 1 in 20 random feeds also produces; (2) skip rules that lose mean ($/wk) improve the ulcer partly by removing trades (the random controls remove the same share, so the percentile is the information, but the mean cost is real); (3) the NQ's own 240-min return, skipped the same way, makes the ulcer WORSE (-29% to -66% L6M in all/Asia), so the NKD 4-h lead is not an NQ-trend proxy, which is the only reason it stays on the watch list; (4) it fails in HOLD / PRE mean, so under the user's tolerant rule it is a LEAD at most (recent works, older worse in mean). Not promoted; engine-exact run only if the quote-free NKD bbo history (owned) shows the same in a second look with the family null (it does not require any purchase).
In-trade cut (driver's signed 5-min move against the open trade below the training q 0.01 / 0.02 / 0.05, cut at the next minute on the NQ 1-min path, 1 tick slippage; random exit control = same share cut, same minutes-since-entry): real 55 cells scored (CONFIRMED 0, LEAD 2, NO-ACTION 8), NONSENSE 60 cells (LEAD 2). The two real LEADs are both NKD-minus-NQ 5-min (Asia q 0.01: L6M ulcer +0.4%, bootstrap 0.24, mean pctile 0.79: no ulcer gain; all books q 0.05: L6M ulcer +17.8% but HOLD -8.3%, mean -1,825 $/wk L6M, 26% of trades cut). Cut shares are high (12-46% of trades), because the rule fires at any of 238 minutes: this is a weak form of the idea; a faster-turn definition (1-min / 1-s on NKD bbo-1s, owned) is the next variant, not run.
Planted-edge check (section 6): the pipeline finds a planted 10% / 20% edge, so the null above is not a blind pipeline.

## 5. Pilot 5 (free): macro release surprise (first table) and 5b pilot 7 (VX / VIX)
**Structural fact first.** In the exact JL2 list there are 0 entries in the first 30 minutes after any 08:30 release, 44 entries in the first 5 minutes after all 10:00 and 14:00 releases in 43 months (ISM 16+18, FOMC 10), and almost no position open at an 08:30 release in L6M/L3M (flagged trades in L6M: at most 13 for "open at release" and at most 30 for "entries in the next 2 hours", across all cells including the loose q 0.5; the history is concentrated in PRE: 18-243 flagged trades per cell). So the stand-down / size / first-5-minute tests have no action surface on the recent windows: 150 of 162 cells print NO-ACTION (n < 10 in L6M or L3M). Windows of the history-only read:
| family (162 cells; surprise = |ZN|, |ES|, |NQ|, |6E| release-minute move, or |actual - prior| z; groups 08:30 macro, 10:00 ISM, 14:00 FOMC, CPI+NFP, CLAIMS) | cells | tier LEAD | FAIL | NO-ACTION |
|---|---|---|---|---|
| macro | 162 | 2 (ISM, ES reaction >= median, entries within 2 h: L6M ulcer +1.5%, mean +157 $/wk, 21 flagged L6M trades, 40 events) | 10 | 150 |
History-wide skip-gain percentile (flagged trades' total P&L vs 33 controls: share of controls whose flagged total is higher): 7 of 81 skip cells reach >= 0.90 (about 8 expected by chance), 7 reach <= 0.10; all of the extreme ones are PRE-window (n_PRE 118-159 flagged trades, n_L6M <= 21 (CLAIMS 6E open-at-release: n_L6M 0)). Verdict: chance level on the owned surprise measures (market reaction, actual - prior); consensus (Benzinga / Trading Economics) is a purchase with no action surface to test it on in the recent windows; first 5 minutes after a release cannot be tested (44 trades). Not done: Kalshi implied-median surprise (owned hourly ladder: CPI 2021-, core CPI 2022-, payrolls 2023-, unemployment); stated as the next free step.
**5b Pilot 7 (free): VX term slope / VX1-VIX basis / VIX.** Daily VX1, VX2 from the Cboe CFE per-contract settle files (52 monthly contracts, 2022-07..2026-11-13, free delayed historical, Cboe terms apply; daily only, no intraday VX), prior-session values used from 16:30 ET; intraday VIX/VIX9D/VIX3M/VVIX 1-min owned (DBIX, 2025-12-08..2026-11-09: older windows NOT RUN for the intraday rows).
| family | cells | CONFIRMED | LEAD | NO-ACTION | FAIL |
|---|---|---|---|---|---|
| real (daily VX features high/low tails, rank-250 forms, intraday VIX / VIX9D / VVIX against the trade, 9D/VIX ratio) | 364 | 0 | 8 | 150 | 206 |
| NONSENSE (4 random-walk intraday, 4 random daily) | 160 | 0 | 0 | 10 | 150 |
The 8 LEAD rows are four cells x skip/half. Two daily: VIX close in its lowest 10% of the trailing 250 days, London (skip: L6M ulcer +11.0%, L3M +16.4%, HOLD -3.8%, mean +339 $/wk) and NY AM (L6M ulcer +0.2%, no effect): 552 and 354 flagged trades, tail defined by a trailing percentile; one London cell out of 364, HOLD slightly worse, not a result. Two intraday (NY AM, bottom 10%, from the DBIX series 2025-12-08..; thresholds from 2025-12..2026-04, windows L3M, L6M and HOLD only, GAP/PRE/X' NOT RUN): VVIX 15-min rise against the trade skip: L6M ulcer +3.0%, L3M +4.8%, HOLD -1.0%, mean +251 $/wk, 100th percentile on both (small effect, 3 windows, 6-month threshold sample: LEAD only); VIX 15-min rise against the trade: ulcer slightly WORSE (-0.5%) with mean +427 (a mean-only LEAD, read as FAIL on the primary statistic). The raw daily VX slope and basis rows: no CONFIRMED or LEAD; rank-250 slope-HIGH (steep contango) skip in Asia makes the ulcer worse (-36% to -63%). Intraday VIX family against the trade: 44 cells, 4 LEAD rows (above), 36 FAIL, 4 NO-ACTION. Verdict: VX term slope and VX-VIX basis add nothing beyond the VIX family already owned on JL2; the intraday question is answered first-order by the owned DBIX VIX; the VX futures purchase ($912 full 1-min) is not supported by this pilot.

## 6. Pipeline validation (planted edge, before reading any "nothing passes")
Planted skip: 25% flag share, information d x rank-normal(own trade P&L) + AR(1, 0.7) noise, 20 seeds each, scored through the same tiers against 30 persistent random draws on all six windows: noise (d 0) 0 CONFIRMED / 0 LEAD of 20; d 0.05: 6 CONFIRMED + 7 LEAD (L6M ulcer cut +2.5% on seed 0); d 0.10: 11 CONFIRMED + 8 LEAD (ulcer cut +19.4%, mean +4,109 $/wk); d 0.20: 17 CONFIRMED + 3 LEAD (+40.9%); d 0.40: 20 of 20 CONFIRMED. So an edge that removes 20% or more of the ulcer in L6M is found about 85-100% of the time; one near 2-3% is found about 30%; the pilots' nulls are not a blind pipeline (planted check in code/th_newdata/plant.py, log /mnt/l2/l2vast/_newdata/run/plant.log). Limitation: skips are path arithmetic (no freed-book replacement, no re-entry); the controls are matched in share (printed: persistent random draws in the entry cells match by construction; the in-trade controls were re-drawn until within 0.05, max deviation 0.05).

## 7. What this page did NOT do (honest list; written 21:35Z before any purchase: superseded where sections 8-13 say otherwise)
- Nothing bought; every Databento price is a get_cost quote; vendor prices for GEXBot / Trading Economics / Benzinga are third-party or "not obtained". Live Nasdaq feed prices not obtained. Engine runs for any pilot lead not done (pilots are arithmetic; no lead qualified). No White RC / SPA / DSR / PBO (nothing to correct: no survivor). Kalshi implied-consensus surprise and 1-s NKD turning definitions not run yet. Megacap cash tape and auction imbalance pilots cannot run until the pilot-month files exist (quotes: $1.37-$42.15 and $0.17); they need the user's approval to buy.


## 8. PURCHASES (user approval 11-16; every quote re-run by metadata.get_cost and logged in MORNING.md + SPEND.json BEFORE its download; key only via bash -ic; downloads on this box to /mnt/l2/l2vast/_newdata_dl/, pushed to server 2 /mnt/l2/l2vast/_newdata/, checksum-verified, local copy removed)
| item | dataset / schema / symbols / range | fresh quote USD | earlier quote | actual USD | SPEND.json id |
|---|---|---|---|---|---|
| 1 ES MBO | GLBX.MDP3 mbo ES.v.0 (continuous) 2026-08-01..11-01 (Aug, Sep, Oct; three requests) | 52.95 (whole) = 19.81 + 23.02 + 10.12 | 52.95 | 52.95 | ND_ES_MBO_m08/m09/m10 |
| 2a imbalance 8 megacaps | XNAS.ITCH imbalance NVDA MSFT AAPL AMZN GOOGL META AVGO TSLA 2023-04-01..2026-11-10 | 6.39 | 7.19 (8 + QQQ together) | 6.39 | ND_IMB_8MEGA |
| 2b imbalance QQQ | XNAS.ITCH imbalance QQQ 2023-04-01..2026-11-10 (proceed only if < $20) | 0.80 | 0.02 (pilot month only) | 0.80 | ND_IMB_QQQ |
| 3 VX pilot month | XCBF.PITCH ohlcv-1m VX.FUT (parent) 2026-09-01..10-01 | 17.27 | 17.27 | 17.27 | ND_VX_1M |
| 4 Asia drivers | GLBX.MDP3 bbo-1s and trades for NKD.v.0, 6J.v.0, NIY.v.0, 2026-09-01..10-01 (6 downloads; the schemas the designs need) | 0.00 each | 0.00 | 0.00 | ND_ASIA_* |
TOTAL $77.41 (approved about $78). Not bought: ohlcv-1s full history NKD/6J/NIY (quote $0.00 but outside the approved item), tbbo, megacap tape and gamma feeds (quote only). Global SPEND.json spent_usd raised by 77.41 to 9,044.82 (the old 8,000 cap line was already exceeded before today).
Files (server 2 /mnt/l2/l2vast/_newdata/): asia/ (6 files, 74 MB), imb/ (2 files, 107 MB), vx/ (1 file, 1.3 MB), es_mbo_stage/ (3 monthly dbn.zst files, 13.3 GB); derived per-second ES L3 tables es_mbo_sec/ (78 UTC-day files, same columns as the NQ cf2_mbo tables) and small result tables /mnt/l2/l2vast/_newdata/derived/ (this box). Code: code/th_newdata2 (nd_buy.py, es_mbo_sec.py, es_lib.py, es_run.py, es_cut.py, imb_derive.py, run_imb*.py, asia_derive.py, run_asia.py, run_vx.py, plant_smoke.py, smoke.py, make_report.py). Prereg NEWDATA2_PREREG.md sha256 097871f0786bb0a3da43d438f412cbbb9326ac9a9839f8890a442866a9a9b1fa (DECISIONS.md 21:56Z, before any scoring).
Header line (desk standard 5): trials counted: NDP9 142 rows (ES: 28 entry cells, 38 in-trade cells, 12 + 4 + 47 lift rows), NDP10 298 + 54 exploratory mirror cells, NDP11 339, NDP12 191 (TRIALS_LEDGER NDP9..NDP12 + _COUNT); correction: family null from same-grid NONSENSE cells, 3 shifted (11/23/37 sessions) + 3 permuted labels and 30 persistent random draws per cell, week-clustered bootstrap (2,000), best-of-12 nonsense bar for the ES lift rows, no White/SPA/DSR (nothing survives to need it); PBO not applicable (no fitted choice: frozen NQ rule on ES, outcome-free quantile thresholds elsewhere); in-sample, L3M-only or one-month samples cannot issue a tier (tier_of needs L6M and L3M). Data-end stamp: ES MBO 2026-10-30; imbalance 2026-11-09; Asia/VX 2026-09-30; trade list 2026-10-30. Fees: engine dollars are BASE lots; x1.75 live scale shown on the ES lift table; the $4.84 RT column is a scale factor, not applied. FIRST PASS labels throughout.
Calibration of the one-month / L3M-only screens (plant_smoke.py, planted skip edge d x rank-normal own P&L, 30 seeds, same Scorer): on all L3M trades the pre-registered loose rule ("ulcer or mean percentile >= 0.75, other >= 0.25") passes pure noise 50% of the time and a planted 5% / 10% / 20% / 40% edge 80% / 100% / 100% / 100% (median L3M ulcer cut +24% / +36% / +56% / +72%); the stricter reading (p_ulc >= 0.9, p_mean >= 0.5, week-bootstrap P(ulcer lower) >= 0.8) passes noise 17% and the planted edges 43% / 57% / 93% / 100%. On September-only trades the loose rule passes noise 27% (planted 50% / 87% / 100% / 100%) and the bootstrap leg can never be met on 4 weeks. So a SMOKE-LEAD is NOT a lead; every ES / Asia / VX statement below is read as the real pass rate against the same-grid NONSENSE pass rate.

## 9. ITEM 1 ES ORDER-BY-ORDER (priority 1; L3M-only SMOKE; first deliverable)
Build: the NQ book code (th_confl_cf2/mbo_sec.py, imported unchanged) on the three ES monthly files with state carried across months; first UTC day of a newly seen instrument (the September roll) is NaN until 23:00 UTC; per-second table, same columns; arrival_imb = (own-side adds within 5 ticks of own touch - opposite-side adds)/max(sum, 1) over the 60 (30) complete seconds ending T-1; yes = value <= q20 of the same value over the previous <= 20 trading days (all JL2 entries, >= 150 prior entries; the NQ lead rule frozen, no refit). Same code on NQ (cf2_mbo) for the same trades.
### 8.1 ES arrival-imbalance reading at the NQ entry second (L3M: JL2 trades 2026-08-02..10-30 with a 20-day reference, n = 1,706; $/trade at base lots; x1.75 = live scale; the $4.84 basis changes both groups equally, not applied)
| condition | n flagged | mean $ flagged | mean $ other | lift $/trade (base) | lift x1.75 | week-cluster t | nonsense p99 |t| (single) |
|---|---|---|---|---|---|---|---|
| ES30_lo (frozen NQ lead: <= q20 of prior 20 days) | 329 | 42 | 137 | -96 | -168.0 | -0.89 | 3.03 |
| ES30_hi (mirror: >= q80) | 333 | 416 | 47 | 369 | 646.0 | 3.99 | 3.03 |
| NQ30_lo (frozen NQ lead: <= q20 of prior 20 days) | 352 | 283 | 76 | 207 | 362.0 | 2.07 | 3.03 |
| NQ30_hi (mirror: >= q80) | 344 | 16 | 145 | -129 | -226.0 | -1.04 | 3.03 |
| ES60_lo (frozen NQ lead: <= q20 of prior 20 days) | 309 | -66 | 160 | -226 | -396.0 | -2.27 | 3.03 |
| ES60_hi (mirror: >= q80) | 337 | 269 | 82 | 187 | 327.0 | 1.79 | 3.03 |
| NQ60_lo (frozen NQ lead: <= q20 of prior 20 days) | 335 | 260 | 85 | 175 | 306.0 | 1.83 | 3.03 |
| NQ60_hi (mirror: >= q80) | 344 | 46 | 137 | -91 | -159.0 | -0.65 | 3.03 |
| divergence 60 s: ES_yes & NQ_not | 231 | -103 | 154 | -256 | -448.0 | -2.16 | 3.03 |
| divergence 60 s: ES_not & NQ_yes | 257 | 326 | 82 | 244 | 427.0 | 2.87 | 3.03 |
| divergence 60 s: both yes | 78 | 41 | 123 | -81 | -142.0 | -0.38 | 3.03 |
| divergence 60 s: neither | 1140 | 122 | 112 | 11 | 19.0 | 0.17 | 3.03 |

Partial association (pnl on yes_NQ and yes_ES together, week-clustered): | n | b_NQ | t_NQ | b_ES | t_ES | corr_yes | corr_raw |
|---|---|---|---|---|---|---|
| 1706.0 | 191.0 | 1.93 | -239.0 | -2.35 | 0.066 | 0.165 |

Controls on the headline rows (ES/NQ value from k sessions earlier, circular inside the 63-session window; within-month permutations):
| cond | control | lift | t |
|---|---|---|---|
| ES30_hi | shifted 11 sessions (circular) | -245.0 | -1.97 |
| ES30_hi | shifted 23 sessions (circular) | 21.0 | 0.22 |
| ES30_hi | shifted 37 sessions (circular) | 35.0 | 0.22 |
| ES30_hi | 100 within-month permutations: t 5th/50th/95th pct |  | -1.39,0.16,1.46 |
| ES60_lo | shifted 11 sessions (circular) | -16.0 | -0.17 |
| ES60_lo | shifted 23 sessions (circular) | 102.0 | 0.94 |
| ES60_lo | shifted 37 sessions (circular) | 48.0 | 0.53 |
| ES60_lo | 100 within-month permutations: t 5th/50th/95th pct |  | -1.56,-0.14,2.21 |
| NQ30_lo | shifted 11 sessions (circular) | 181.0 | 1.56 |
| NQ30_lo | shifted 23 sessions (circular) | 181.0 | 3.13 |
| NQ30_lo | shifted 37 sessions (circular) | -18.0 | -0.11 |
| NQ30_lo | 100 within-month permutations: t 5th/50th/95th pct |  | -1.64,0.00,1.59 |
| DIV60 ES_yes&NQ_not | shifted 11 sessions (circular) | -5.0 | -0.04 |
| DIV60 ES_yes&NQ_not | shifted 23 sessions (circular) | 90.0 | 0.73 |
| DIV60 ES_yes&NQ_not | shifted 37 sessions (circular) | 76.0 | 0.61 |
| DIV60 ES_yes&NQ_not | 100 within-month permutations: t 5th/50th/95th pct |  | -2.73,-0.46,1.52 |

### 8.2 Entry cells (ES/NQ reading at the entry second, action on the flagged trades; L3M window only; controls: 3 shifted + 3 permuted labels + 30 persistent random draws, share deviation <= 0.026)
| cell | act | n_flag | share | ulc_cut | dd_cut | d_mean | p_ulc | p_mean | boot_p_ulc | tier_s |
|---|---|---|---|---|---|---|---|---|---|---|
| ES60: act on NOT-yes (value > q20) | half | 1397 | 0.819 | -26.7 | -44.2 | -8498 | 0.0 | 0.03 | 0.64 | SMOKE-FAIL |
| ES60: act on hi (value >= q80) | half | 337 | 0.198 | -49.7 | -53.4 | -3446 | 0.0 | 0.03 | 0.25 | SMOKE-FAIL |
| ES60: act on NOT-yes (value > q20) | skip | 1397 | 0.819 | -181.1 | -105.6 | -16995 | 0.0 | 0.03 | 0.15 | SMOKE-FAIL |
| ES60: act on hi (value >= q80) | skip | 337 | 0.198 | -116.8 | -112.9 | -6892 | 0.0 | 0.03 | 0.1 | SMOKE-FAIL |
| ES30: act on NOT-yes (value > q20) | half | 1377 | 0.807 | -21.7 | -38.6 | -7195 | 0.06 | 0.14 | 0.68 | SMOKE-FAIL |
| ES30: act on hi (value >= q80) | half | 333 | 0.195 | -44.4 | -45.4 | -5264 | 0.0 | 0.0 | 0.59 | SMOKE-FAIL |
| ES30: act on NOT-yes (value > q20) | skip | 1377 | 0.807 | -88.1 | -96.4 | -14391 | 0.08 | 0.14 | 0.21 | SMOKE-FAIL |
| ES30: act on hi (value >= q80) | skip | 333 | 0.195 | -119.5 | -97.0 | -10528 | 0.0 | 0.0 | 0.23 | SMOKE-FAIL |
| NQ60: act on NOT-yes (value > q20) | half | 1371 | 0.804 | 35.6 | 17.6 | -4408 | 0.67 | 0.94 | 0.65 | SMOKE-LEAD |
| NQ60: act on hi (value >= q80) | half | 344 | 0.202 | 6.7 | 1.4 | -608 | 0.67 | 0.83 | 0.53 | SMOKE-LEAD |
| NQ60: act on NOT-yes (value > q20) | skip | 1371 | 0.804 | 44.9 | 20.7 | -8815 | 0.83 | 0.94 | 0.63 | SMOKE-LEAD |
| NQ60: act on hi (value >= q80) | skip | 344 | 0.202 | 6.4 | 2.7 | -1215 | 0.72 | 0.83 | 0.47 | SMOKE-LEAD |
| NQ30: act on NOT-yes (value > q20) | half | 1354 | 0.794 | 43.7 | 46.9 | -3928 | 0.94 | 0.94 | 0.87 | SMOKE-LEAD |
| NQ30: act on hi (value >= q80) | half | 344 | 0.202 | -0.3 | -5.9 | -210 | 0.44 | 0.94 | 0.34 | SMOKE-LEAD |
| NQ30: act on NOT-yes (value > q20) | skip | 1354 | 0.794 | 45.4 | 31.2 | -7856 | 0.89 | 0.94 | 0.87 | SMOKE-LEAD |
| NQ30: act on hi (value >= q80) | skip | 344 | 0.202 | -4.7 | -12.1 | -420 | 0.56 | 0.94 | 0.32 | SMOKE-LEAD |
| DIV60 (ES-NQ): act when ES much worse than NQ (<= q20) | half | 332 | 0.195 | 20.8 | -1.7 | 1130 | 1.0 | 1.0 | 0.6 | SMOKE-LEAD |
| DIV60 (ES-NQ): act when ES much better than NQ (>= q80) | half | 335 | 0.196 | -56.6 | -73.1 | -4418 | 0.0 | 0.0 | 0.0 | SMOKE-FAIL |
| DIV60 (ES-NQ): act when ES much worse than NQ (<= q20) | skip | 332 | 0.195 | 29.2 | -3.4 | 2260 | 1.0 | 1.0 | 0.55 | SMOKE-LEAD |
| DIV60 (ES-NQ): act when ES much better than NQ (>= q80) | skip | 335 | 0.196 | -153.4 | -177.7 | -8836 | 0.0 | 0.0 | 0.0 | SMOKE-FAIL |
| NONSENSE0: act on NOT-yes | half | 1403 | 0.805 | 35.3 | 30.1 | -5476 | 0.67 | 0.69 | 0.81 | SMOKE-FAIL |
| NONSENSE0: act on NOT-yes | skip | 1403 | 0.805 | 44.8 | 39.9 | -10952 | 0.83 | 0.69 | 0.57 | SMOKE-LEAD |
| NONSENSE1: act on NOT-yes | half | 1424 | 0.817 | 24.1 | -3.9 | -7255 | 0.28 | 0.28 | 0.34 | SMOKE-FAIL |
| NONSENSE1: act on NOT-yes | skip | 1424 | 0.817 | 2.6 | -13.0 | -14510 | 0.33 | 0.28 | 0.16 | SMOKE-FAIL |
| NONSENSE2: act on NOT-yes | half | 1388 | 0.797 | 16.8 | 8.1 | -8415 | 0.33 | 0.17 | 0.68 | SMOKE-FAIL |
| NONSENSE2: act on NOT-yes | skip | 1388 | 0.797 | -236.1 | -132.8 | -16830 | 0.06 | 0.17 | 0.08 | SMOKE-FAIL |
| NONSENSE3: act on NOT-yes | half | 1406 | 0.807 | 23.2 | 7.2 | -6069 | 0.28 | 0.58 | 0.48 | SMOKE-FAIL |
| NONSENSE3: act on NOT-yes | skip | 1406 | 0.807 | 1.0 | -29.1 | -12139 | 0.31 | 0.58 | 0.2 | SMOKE-FAIL |

### 8.3 In-trade ES order-flow turn (cut at the next minute on the NQ path; frozen NQ thresholds)
| driver | subset | q | thr | n_cut | share | med_min | L3M_ulc% | L3M_dmean | L3M_pulc | L3M_pmean |
|---|---|---|---|---|---|---|---|---|---|---|
| ES_mkt60(turn against) | all | 0.05 | -0.09 | 1507 | 0.079 | 5 | -14.9 | -15374 | 0.33 | 0.06 |
| ES_mkt60(turn against) | asia | 0.05 | -0.09 | 771 | 0.108 | 4 | -87.9 | -11090 | 0.06 | 0.03 |
| ES_mkt60(turn against) | london | 0.05 | -0.09 | 575 | 0.09 | 6 | 0.0 | -4332 | 0.39 | 0.06 |
| ES_mkt60(turn against) | nyam | 0.05 | -0.09 | 113 | 0.027 | 9 | 2.4 | 342 | 0.85 | 0.94 |
| ES_mkt60(turn against) | all | 0.1 | -0.06 | 1643 | 0.087 | 4 | -43.0 | -16962 | 0.06 | 0.03 |
| ES_mkt60(turn against) | asia | 0.1 | -0.06 | 799 | 0.112 | 3 | -141.5 | -11916 | 0.03 | 0.03 |
| ES_mkt60(turn against) | london | 0.1 | -0.06 | 625 | 0.098 | 4 | -0.2 | -4807 | 0.42 | 0.06 |
| ES_mkt60(turn against) | nyam | 0.1 | -0.06 | 163 | 0.038 | 5 | -1.6 | 162 | 0.09 | 0.79 |
| ES_mkt30(turn against) | all | 0.05 | -0.15 | 1441 | 0.076 | 6 | -24.9 | -15987 | 0.12 | 0.0 |
| ES_mkt30(turn against) | asia | 0.05 | -0.15 | 751 | 0.106 | 5 | -93.9 | -11641 | 0.03 | 0.0 |
| ES_mkt30(turn against) | london | 0.05 | -0.15 | 546 | 0.086 | 7 | -7.1 | -4793 | 0.09 | 0.03 |
| ES_mkt30(turn against) | all | 0.1 | -0.1 | 1602 | 0.084 | 4 | -21.3 | -17202 | 0.15 | 0.03 |
| ES_mkt30(turn against) | asia | 0.1 | -0.1 | 792 | 0.111 | 4 | -120.4 | -12560 | 0.06 | 0.0 |
| ES_mkt30(turn against) | london | 0.1 | -0.1 | 610 | 0.096 | 5 | -8.7 | -4776 | 0.24 | 0.0 |
| ES_mkt30(turn against) | nyam | 0.1 | -0.1 | 148 | 0.035 | 6 | -2.4 | 370 | 0.03 | 0.97 |
| NQ_mkt60(reference, same L3M) | all | 0.05 | -0.09 | 1353 | 0.071 | 8 | -157.7 | -15446 | 0.0 | 0.0 |
| NQ_mkt60(reference, same L3M) | asia | 0.05 | -0.09 | 723 | 0.102 | 7 | -159.5 | -10919 | 0.0 | 0.03 |
| NQ_mkt60(reference, same L3M) | london | 0.05 | -0.09 | 535 | 0.084 | 10 | -13.5 | -3986 | 0.06 | 0.06 |
| NQ_mkt60(reference, same L3M) | all | 0.1 | -0.06 | 1550 | 0.082 | 5 | -116.8 | -15229 | 0.0 | 0.06 |
| NQ_mkt60(reference, same L3M) | asia | 0.1 | -0.06 | 782 | 0.11 | 5 | -165.6 | -10382 | 0.0 | 0.03 |
| NQ_mkt60(reference, same L3M) | london | 0.1 | -0.06 | 579 | 0.091 | 6 | -10.4 | -4326 | 0.09 | 0.03 |
| NQ_mkt60(reference, same L3M) | nyam | 0.1 | -0.06 | 139 | 0.033 | 7 | -1.0 | -77 | 0.03 | 0.24 |
| NONSENSE0 | all | 0.05 | -0.34 | 1355 | 0.071 | 12 | 54.6 | -7127 | 1.0 | 0.09 |
| NONSENSE0 | asia | 0.05 | -0.34 | 675 | 0.095 | 13 | -34.8 | -5789 | 0.06 | 0.09 |
| NONSENSE0 | london | 0.05 | -0.34 | 503 | 0.079 | 13 | 8.0 | -1315 | 0.91 | 0.09 |
| NONSENSE0 | nyam | 0.05 | -0.34 | 130 | 0.031 | 10 | 4.9 | 302 | 0.91 | 0.88 |
| NONSENSE0 | all | 0.1 | -0.27 | 1535 | 0.081 | 7 | 37.4 | -10958 | 1.0 | 0.09 |
| NONSENSE0 | asia | 0.1 | -0.27 | 749 | 0.105 | 8 | -39.8 | -7345 | 0.24 | 0.09 |
| NONSENSE0 | london | 0.1 | -0.27 | 567 | 0.089 | 7 | -20.2 | -4357 | 0.03 | 0.0 |
| NONSENSE0 | nyam | 0.1 | -0.27 | 167 | 0.039 | 5 | 9.8 | 976 | 1.0 | 1.0 |
| NONSENSE1 | all | 0.05 | -0.33 | 1383 | 0.073 | 11 | -36.2 | -11933 | 0.03 | 0.03 |
| NONSENSE1 | asia | 0.05 | -0.33 | 694 | 0.097 | 11 | -65.0 | -8215 | 0.09 | 0.06 |
| NONSENSE1 | london | 0.05 | -0.33 | 512 | 0.08 | 11 | -15.6 | -3788 | 0.0 | 0.0 |
| NONSENSE1 | nyam | 0.05 | -0.33 | 131 | 0.031 | 7 | 9.6 | 87 | 1.0 | 0.73 |
| NONSENSE1 | all | 0.1 | -0.25 | 1579 | 0.083 | 6 | 16.3 | -14373 | 0.94 | 0.09 |
| NONSENSE1 | asia | 0.1 | -0.25 | 764 | 0.107 | 7 | -78.7 | -10678 | 0.06 | 0.06 |
| NONSENSE1 | london | 0.1 | -0.25 | 590 | 0.093 | 6 | -15.9 | -3765 | 0.0 | 0.09 |
| NONSENSE1 | nyam | 0.1 | -0.25 | 170 | 0.04 | 5 | 7.3 | 389 | 0.97 | 0.94 |

### 8.4 Lift by session (0 Asia, 1 London, 3 NY AM, 4 NY PM) and by book (L3M; rows with >= 8 flagged and >= 8 other)
| cond | group | n | n_yes | lift | t |
|---|---|---|---|---|---|
| ES60_lo | session=0 | 783 | 173 | -462 | -2.24 |
| ES60_lo | session=1 | 613 | 98 | -31 | -0.29 |
| ES60_lo | session=3 | 242 | 28 | -44 | -0.26 |
| ES60_lo | session=4 | 68 | 10 | 296 | 0.88 |
| ES60_lo | book=A7 | 146 | 21 | 349 | 1.8 |
| ES60_lo | book=H7 | 76 | 25 | -603 | -1.33 |
| ES60_lo | book=K7 | 661 | 102 | -50 | -0.41 |
| ES60_lo | book=M7 | 296 | 46 | 123 | 0.52 |
| ES60_lo | book=P7 | 399 | 83 | -672 | -1.7 |
| ES60_lo | book=U7 | 108 | 27 | -651 | -1.27 |
| ES30_hi | session=0 | 783 | 206 | 646 | 4.09 |
| ES30_hi | session=1 | 613 | 105 | -89 | -0.46 |
| ES30_hi | session=3 | 242 | 17 | -144 | -0.38 |
| ES30_hi | book=A7 | 146 | 37 | -14 | -0.05 |
| ES30_hi | book=H7 | 76 | 12 | 4 | 0.01 |
| ES30_hi | book=K7 | 661 | 139 | 61 | 0.79 |
| ES30_hi | book=M7 | 296 | 40 | -257 | -0.93 |
| ES30_hi | book=P7 | 399 | 84 | 1038 | 4.01 |
| ES30_hi | book=U7 | 108 | 20 | 1854 | 2.19 |
| NQ60_lo | session=0 | 783 | 170 | 140 | 0.7 |
| NQ60_lo | session=1 | 613 | 129 | 286 | 1.7 |
| NQ60_lo | session=3 | 242 | 29 | -138 | -0.67 |
| NQ60_lo | book=A7 | 146 | 26 | 136 | 0.72 |
| NQ60_lo | book=H7 | 76 | 21 | -125 | -0.28 |
| NQ60_lo | book=K7 | 661 | 113 | -2 | -0.03 |
| NQ60_lo | book=M7 | 296 | 46 | 192 | 0.94 |
| NQ60_lo | book=P7 | 399 | 100 | 236 | 1.13 |
| NQ60_lo | book=U7 | 108 | 20 | 871 | 1.63 |
| NQ30_lo | session=0 | 783 | 180 | 259 | 1.48 |
| NQ30_lo | session=1 | 613 | 135 | 225 | 1.16 |
| NQ30_lo | session=3 | 242 | 30 | -264 | -1.08 |
| NQ30_lo | book=A7 | 146 | 28 | 486 | 1.59 |
| NQ30_lo | book=H7 | 76 | 18 | 863 | 1.87 |
| NQ30_lo | book=K7 | 661 | 127 | 136 | 1.32 |
| NQ30_lo | book=M7 | 296 | 43 | 474 | 3.22 |
| NQ30_lo | book=P7 | 399 | 106 | -318 | -0.98 |
| NQ30_lo | book=U7 | 108 | 22 | 1297 | 2.94 |
| DIV ES_yes&NQ_not | session=0 | 783 | 122 | -487 | -1.92 |
| DIV ES_yes&NQ_not | session=1 | 613 | 77 | -61 | -0.41 |
| DIV ES_yes&NQ_not | session=3 | 242 | 24 | -87 | -0.45 |
| DIV ES_yes&NQ_not | session=4 | 68 | 8 | 267 | 0.89 |
| DIV ES_yes&NQ_not | book=A7 | 146 | 17 | 425 | 2.56 |
| DIV ES_yes&NQ_not | book=H7 | 76 | 15 | -361 | -0.65 |
| DIV ES_yes&NQ_not | book=K7 | 661 | 84 | -20 | -0.21 |
| DIV ES_yes&NQ_not | book=M7 | 296 | 40 | -14 | -0.06 |
| DIV ES_yes&NQ_not | book=P7 | 399 | 53 | -637 | -1.94 |
| DIV ES_yes&NQ_not | book=U7 | 108 | 19 | -1401 | -2.24 |
Reading. (a) The NQ lead keeps its sign on NQ in these three months (NQ60 lo +$175, NQ30 lo +$207, t 1.8 / 2.1, below the single-test bar 3.03) and has the OPPOSITE sign on ES (ES60 lo -$226, t -2.3): the frozen ES rule is SMOKE-FAIL in every entry cell (ulcer -22% to -181% worse than JL2, mean -$3k to -$17k per week on base lots). (b) Divergence: yes_ES & not yes_NQ -$256 (t -2.2), not yes_ES & yes_NQ +$244 (t 2.9); the partial regression gives the ES coefficient beside NQ -$239 (t -2.35) and NQ +$191 (t 1.9), corr of the two yes flags 0.07: ES carries information beyond NQ, but with the sign opposite to the lead; the divergence skip cell "ES much worse than NQ" is a loose SMOKE-LEAD (ulcer +21% / +29% half / skip, mean +$1,130 / +$2,260 per week, percentiles 1.00 / 1.00, week-bootstrap P(ulcer lower) 0.55-0.60 = below the strict 0.8 line); NONSENSE0 reaches the same loose label (1 of 8 nonsense cells). (c) The only row above the single-test nonsense bar is ES30 hi (+$369, t 3.99), concentrated in Asia (+$646, t 4.1) and P7 (+$1,038, t 4.0), thin ES overnight flow, one 3-month sample; it is below the best-of-12 nonsense 99th percentile (4.47) and the circular-shift controls of the same row are -245 / +21 / +35 (t -2.0 / 0.2 / 0.2). (d) In-trade ES order-flow turn (frozen NQ thresholds, q 0.05 / 0.10): ulcer worse in every pooled / Asia / London cell (0% to -141%), the same cut on NQ itself (reference rows) is also worse. Decision rule from the order (ES reaches SMOKE-LEAD in L3M without a refit AND the NQ-vs-ES partial association is nonzero): the frozen ES lead does not (opposite sign); only the divergence cell does, on a rule that passes noise half the time -> STOP, do not quote or buy the ES full history ($984.71, 608 GB billable). Watch only: ES30 hi in Asia / P7 would need its own prereg and a second sample (ES MBO for 2026-11 onward costs about $20 per month).

## 10. ITEM 2 AUCTION IMBALANCE (priority 2; 2023-04..2026-11-09, all windows)
Readings: open = last 'O' message at or before 09:30:00 ET; close = last 'C' message at or before 15:55:00 and 15:59:00 ET (early-close days NaN); 8 megacaps pooled dollars ratio (signed imbalance $ / paired $), breadth (signed name count), QQQ ratio, dollars z vs 20-day median, 8 per-name ratios; signed with the trade; 905 trading days with readings.
### 9.1 Entry cells O7 09:30-10:00 (465 trades; reading = last opening-cross message at or before 09:30:00): real 72 cells: {'FAIL': 50, 'NO-ACTION': 22}; NONSENSE 36 cells: {'NO-ACTION': 20, 'FAIL': 16}.

### 9.2 Mean P&L by signed-reading tercile and shifted-day control ($/trade base lots; signed with the trade: against = bottom tercile of the buy-minus-sell imbalance)
| item | window | n | mean_against | mean_mid | mean_with | n_lo | n_hi | spearman | shifted | pct_abs_rank_vs_200perm | rank_vs_shifted |
|---|---|---|---|---|---|---|---|---|---|---|---|
| O7 entry open:idx_ratio | ALL | 460 | 154 | 171.0 | 276 | 154 | 153 | 0.05 | 0.076,-0.032,-0.031 | 0.72 | 2 |
| O7 entry open:idx_ratio | L6M | 50 | 632 | -170.0 | 138 | 17 | 17 | -0.193 | -0.244,-0.269,-0.263 | 0.81 | 0 |
| O7 entry open:idx_ratio | PRE | 349 | 39 | 278.0 | 176 | 117 | 116 | 0.069 | 0.103,-0.015,0.015 | 0.82 | 2 |
| CARRY open:idx_ratio | ALL | 974 | 462 | 284.0 | -155 | 325 | 325 | -0.137 | -0.092,0.037,-0.062 | 1.0 | 3 |
| CARRY open:idx_ratio | PRE | 902 | 495 | 204.0 | -94 | 302 | 300 | -0.126 | -0.107,0.046,-0.038 | 1.0 | 3 |
| CLOSE c1555:idx_ratio | ALL | 331 | 32 | 120.0 | 303 | 111 | 110 | 0.156 | 0.009,0.029,-0.062 | 0.99 | 3 |
| CLOSE c1555:idx_ratio | PRE | 297 | 49 | 92.0 | 333 | 100 | 99 | 0.174 | 0.011,0.022,-0.088 | 1.0 | 3 |
| O7 entry open:breadth | ALL | 460 | 197 | 142.0 | 268 | 155 | 144 | 0.068 | 0.115,-0.014,0.010 | 0.84 | 2 |
| O7 entry open:breadth | L6M | 50 | 646 | -172.0 | 180 | 18 | 12 | -0.163 | -0.222,-0.176,-0.147 | 0.72 | 1 |
| O7 entry open:breadth | PRE | 349 | 100 | 180.0 | 218 | 120 | 108 | 0.084 | 0.144,-0.009,0.047 | 0.9 | 2 |
| CARRY open:breadth | ALL | 974 | 438 | 189.0 | -139 | 358 | 248 | -0.118 | -0.111,0.028,-0.099 | 1.0 | 3 |
| CARRY open:breadth | PRE | 902 | 397 | 182.0 | -61 | 333 | 218 | -0.098 | -0.123,0.049,-0.090 | 0.99 | 2 |
| CLOSE c1555:breadth | ALL | 331 | 89 | 81.0 | 283 | 120 | 110 | 0.118 | 0.018,0.085,-0.039 | 0.98 | 3 |
| CLOSE c1555:breadth | PRE | 297 | 78 | 79.0 | 324 | 102 | 96 | 0.132 | 0.016,0.082,-0.082 | 0.98 | 3 |
| O7 entry open:qqq_ratio | ALL | 460 | 233 |  | 12 | 392 | 68 | -0.095 | 0.021,0.059,-0.001 | 0.96 | 3 |
| O7 entry open:qqq_ratio | L6M | 50 | 284 |  | -140 | 41 | 9 | -0.06 | 0.185,0.142,-0.122 | 0.3 | 0 |
| O7 entry open:qqq_ratio | PRE | 349 | 189 |  | 17 | 298 | 51 | -0.086 | 0.037,0.004,0.032 | 0.89 | 3 |
| CARRY open:qqq_ratio | ALL | 974 | 221 |  | 35 | 848 | 126 | -0.023 | -0.047,-0.027,-0.040 | 0.47 | 0 |
| CARRY open:qqq_ratio | PRE | 902 | 238 |  | -42 | 787 | 115 | -0.03 | -0.035,-0.009,-0.030 | 0.63 | 2 |
| CLOSE c1555:qqq_ratio | ALL | 331 | 24 | 173.0 | 257 | 111 | 110 | 0.136 | 0.023,-0.033,0.057 | 0.99 | 3 |
| CLOSE c1555:qqq_ratio | PRE | 297 | 46 | 155.0 | 273 | 100 | 99 | 0.141 | 0.030,-0.031,0.048 | 0.97 | 3 |
| O7 entry open:idx_dol_z | ALL | 451 | 149 | 200.0 | 246 | 151 | 150 | 0.038 | 0.087,-0.043,-0.022 | 0.59 | 1 |
| O7 entry open:idx_dol_z | L6M | 50 | 632 | -170.0 | 138 | 17 | 17 | -0.147 | -0.215,-0.255,-0.260 | 0.65 | 0 |
| O7 entry open:idx_dol_z | PRE | 340 | 33 | 301.0 | 147 | 114 | 113 | 0.049 | 0.108,-0.032,0.028 | 0.7 | 2 |
| CARRY open:idx_dol_z | ALL | 959 | 498 | 162.0 | -73 | 320 | 318 | -0.138 | -0.096,0.040,-0.094 | 1.0 | 3 |
| CARRY open:idx_dol_z | PRE | 887 | 496 | 158.0 | -52 | 298 | 296 | -0.127 | -0.113,0.057,-0.069 | 1.0 | 3 |
| CLOSE c1555:idx_dol_z | ALL | 324 | 68 | 135.0 | 238 | 108 | 106 | 0.138 | -0.012,0.067,-0.063 | 0.98 | 3 |
| CLOSE c1555:idx_dol_z | PRE | 290 | 67 | 121.0 | 269 | 97 | 97 | 0.15 | -0.008,0.067,-0.087 | 0.98 | 3 |

### 9.3 Fixed-time cut cells (CARRY: open at 09:30, cut 09:31; CLOSE: open at 15:50, reading 15:55 cut 15:56, reading 15:59 cut 16:00)
| family | kind | tier_s | cells |
|---|---|---|---|
| CARRY | NONSENSE | NO-ACTION | 18 |
| CARRY | real | NO-ACTION | 28 |
| CARRY | real | FAIL | 8 |
| CLOSE_r1555_c1556 | NONSENSE | NO-ACTION | 18 |
| CLOSE_r1555_c1556 | real | NO-ACTION | 36 |
| CLOSE_r1559_c1600 | NONSENSE | NO-ACTION | 18 |
| CLOSE_r1559_c1600 | real | NO-ACTION | 36 |
### 9.4 EXPLORATORY mirror of CARRY (cut when the opening imbalance is WITH the trade; post-hoc)
| kind | tier_s | cells |
|---|---|---|
| NONSENSE | NO-ACTION | 17 |
| NONSENSE | FAIL | 1 |
| real | NO-ACTION | 27 |
| real | FAIL | 9 |
Reading. No tier can be issued: O7 entries 465 (L6M 50, L3M 22), open at 09:30 1,061 (L6M 28, L3M 18), open at 15:50 402 (L6M 24, L3M 9); at q 0.1 - 0.35 the flagged count in L6M or L3M is below 10, so those cells print NO-ACTION (all 108 CLOSE cells, 28 of 36 real CARRY cells); the O7 entry cells FAIL (real 50 FAIL / 22 NO-ACTION; nonsense 16 / 20). History-only associations, none usable now: carried positions at the open earn $462 per trade (n 325) when the opening imbalance is against them vs -$155 (n 325) when it is with them (Spearman -0.137, beats 3 of 3 shifted days and 100% of 200 permutations; PRE window 902 of 974 trades, L6M too few); a cut at 09:31 does not capture it (mirror cells: no ulcer gain, 44 NO-ACTION / 10 FAIL; nonsense 17 / 1); positions held into the close earn +$32 when the closing imbalance is against them vs +$303 with them (n 111 each, Spearman +0.156, 3 of 3 shifted, 99% of permutations; 297 of 331 trades PRE; K7 held to 16:55 mostly). Verdict: no action surface in the recent windows (the book trades the 09:30-10:00 window 50 times in six months and holds into the close about 24 times); keep as an incubation log item for the live auction feed if one is ever licensed (NT8 does not carry it); no further purchase (NYSE, SPY imbalance not needed).

## 11. ITEM 3 ASIA DRIVERS (priority 3; September 2026 only: 1-s NKD / NIY / 6J bbo and trade aggressor flow; L3M-partial SMOKE)
Readings (all at T-1, signed with the trade; 6J and 6J flow sign flipped, yen strength = risk off): 1 / 5 / 15 min mid return of NKD, NIY, 6J; trade-aggressor imbalance (buy minus sell contracts over 1 and 5 min) of NKD, NIY, 6J (B/A side verified: corr with the next-minute mid change +0.2 to +0.4); NIY-minus-NKD 5-min return. Thresholds = quantile of the feature over September entries (outcome-free; in-sample label); in-trade: 5-min move against, cut at the next minute on the NQ path.

### 10.1 Asia 1-s entry cells (September 2026): real 232 cells: smoke-lead 68 (29%), strict (n>=20, p_ulc>=0.9, p_mean>=0.5) 26 (11%); NONSENSE 64 cells: smoke-lead 12 (19%), strict 2 (3%)
| feature | subset | q | act | n_flag | L3M_ulc% | L3M_dmean | L3M_pulc | L3M_pmean |
|---|---|---|---|---|---|---|---|---|
| 6J_r300s | london | 0.2 | skip | 52 | 19.3 | 899 | 1.0 | 1.0 |
| 6J_r900s | london | 0.2 | skip | 53 | 18.6 | 209 | 1.0 | 0.92 |
| 6J_aggr_imb300s | all | 0.2 | skip | 133 | 18.6 | 26 | 1.0 | 0.58 |
| 6J_aggr_imb300s | all | 0.1 | skip | 66 | 17.8 | 1369 | 1.0 | 1.0 |
| 6J_r300s | london | 0.1 | skip | 27 | 15.1 | 1240 | 1.0 | 1.0 |
| 6J_aggr_imb300s | asia | 0.1 | skip | 26 | 14.0 | 107 | 1.0 | 0.69 |
| 6J_r300s | london | 0.2 | half | 52 | 12.3 | 449 | 1.0 | 1.0 |
| 6J_aggr_imb300s | all | 0.2 | half | 133 | 11.9 | 13 | 1.0 | 0.58 |

### 10.2 Asia in-trade 5-min turn against: real 31 cells: smoke-lead 11 (35%), strict (n>=20, p_ulc>=0.9, p_mean>=0.5) 11 (35%); NONSENSE 12 cells: smoke-lead 1 (8%), strict 1 (8%)
| driver | subset | q | n_cut | L3M_ulc% | L3M_dmean | L3M_pulc | L3M_pmean |
|---|---|---|---|---|---|---|---|
| 6J_aggr_imb300 | all | 0.1 | 453 | 24.3 | 553 | 1.0 | 0.82 |
| NIY-NKD_r300 | all | 0.05 | 268 | 23.9 | 331 | 1.0 | 0.88 |
| 6J_aggr_imb300 | all | 0.05 | 353 | 23.5 | 1260 | 1.0 | 0.97 |
| 6J_aggr_imb300 | london | 0.1 | 173 | 21.5 | 121 | 1.0 | 0.67 |
| 6J_r300(yen up=against) | london | 0.1 | 141 | 20.0 | 415 | 1.0 | 0.97 |
| 6J_aggr_imb300 | london | 0.05 | 127 | 20.0 | 234 | 1.0 | 0.82 |
| NKD_aggr_imb300 | london | 0.1 | 167 | 19.4 | 521 | 1.0 | 0.91 |
| NIY-NKD_r300 | asia | 0.05 | 162 | 18.9 | -102 | 1.0 | 0.61 |


Reading. The family is above its same-grid nonsense rate for the first time in this study (in-trade turn 35% real vs 8% nonsense, entry 11% vs 3% on the strict screen), and the strong cells are 6J (aggressor flow 5 min, 5-15 min move), NIY-minus-NKD 5 min and NKD aggressor flow in London; the shares cut are large (up to 453 of the September trades flagged at q 0.1, because the trigger fires at any of 238 minutes) so the mean effects are mixed (-$113 to +$1,260 per week on base lots). One month, 4 weeks of weekly bootstrap, no tier possible. The 6J 15-min London skip is the same lead pilot 6 found on owned 1-min history (mean percentile 0.50 there); the NEW piece is the 6J trade-aggressor flow, which needs trades history: 6J trades 2023-04..2026-11 quoted $33.13 (NKD trades $3.89, NIY trades $10.82). Recommendation for the lead: ask the user for approval to buy 6J trades full history ($33.13) only; NOT bought, no spend beyond the approved $77.41.

## 12. ITEM 4 VX (priority 4; ohlcv-1m, September 2026; L3M-partial SMOKE)
Readings: VX1 / VX2 by volume rank per ET day (spreads excluded), chain-linked VX1 log return 5 / 15 / 60 min (up = against), term slope VX2/VX1 - 1 level and 15 / 60 min change, VX1 minus VIX (owned DBIX 1-min) level and 15-min change; thresholds from September entries (outcome-free).
 VX entry cells (September 2026): real 100 cells: smoke-lead 17 (17%), strict (n>=20, p_ulc>=0.9, p_mean>=0.5) 10 (10%); NONSENSE 64 cells: smoke-lead 16 (25%), strict 12 (19%)
| feature | subset | q | act | n_flag | L3M_ulc% | L3M_dmean | L3M_pulc | L3M_pmean |
|---|---|---|---|---|---|---|---|---|
| VX_slope_chg15m | all | 0.2 | skip | 95 | 17.5 | 1079 | 1.0 | 0.97 |
| VX_slope_chg15m | london | 0.2 | skip | 42 | 10.8 | 265 | 1.0 | 0.78 |
| VX_slope_chg15m | all | 0.2 | half | 95 | 10.4 | 540 | 1.0 | 0.97 |
| VX1_r5m(up=against) | london | 0.1 | skip | 25 | 5.9 | 959 | 0.94 | 1.0 |
| VX_slope_chg15m | london | 0.2 | half | 42 | 5.8 | 132 | 1.0 | 0.78 |
| VX_slope_chg15m | all | 0.1 | skip | 47 | 4.1 | 144 | 0.94 | 0.78 |
| VX_slope_chg15m | all | 0.1 | half | 47 | 3.4 | 72 | 1.0 | 0.78 |
| VX1_r15m(up=against) | nyam | 0.2 | skip | 31 | 3.2 | 233 | 1.0 | 1.0 |

### 12.2 VX in-trade turn: real 15 cells: smoke-lead 1 (7%), strict (n>=20, p_ulc>=0.9, p_mean>=0.5) 0 (0%); NONSENSE 12 cells: smoke-lead 0 (0%), strict 0 (0%)

Reading. Chance level: 17% of real entry cells pass the loose screen against 25% of nonsense cells (strict 10% vs 19%), 0 of 15 in-trade cells pass; the single repeated row (slope change 15 min, skip, all books) is one feature in one month. Verdict: VX 1-min adds nothing to the VIX family already owned; no further VX purchase ($912 full 1-min history not justified).

## 13. What this update did NOT do
Engine-exact runs for any cell (path arithmetic only); White RC / SPA / DSR (no survivor); older windows for ES / Asia / VX (data covers 1-3 months); the full-history ES / 6J-flow tests (not bought); per-name ES order flow beyond the arrival imbalance (cancel-to-trade, spoof, sweep columns exist in the tables but were not tested: not in the prereg); the 6J / NKD 1-s history already owned (L6M 6J bbo-1s, full NKD bbo-1s) was not re-used for the aggressor-flow construction because flow needs trades. Planted-edge check: pipeline check section 6 plus plant_smoke.py above.


## 14. REFRESH 2026-11-17: Kalshi implied-consensus surprise (free pilot 5 step) and one-line recommendations
**Kalshi implied-consensus surprise (data end 2026-08-12 events; trade list to 2026-10-30; FIRST PASS, path arithmetic on JL2).** Events: Kalshi CPI (MoM, YoY, core MoM, core YoY), payrolls and unemployment (U3) ladders from the owned hourly candles (/mnt/l2/l2vast/feeds/kalshi): implied mean from the strike ladder at T-60 min (same ladder code as DS3_FEEDS F2), actual = market expiration value, release = close + 60 s (08:30 ET); surprise = (actual - implied mean) / ladder step and / implied sd, absolute value (212 events, 87 distinct release times, 20 events in L6M). Cells: group (all 08:30, CPI, NFP) x measure (2) x threshold q (0.5 / 0.75 / 0.9 of the training events, before 2025-11-01) x action (open position at the release: skip = cut at release + 60 s on the NQ path, half; new entry within 2 h: skip, half) = 58 cells; controls: label shifted 11/23/37 events, 3 permutations, 30 random event draws of the same count, ulcer-primary tiers from cutoffs_ulc.json, week-clustered bootstrap, same grid as pilot 5.
| family | cells | CONFIRMED | LEAD | NO-ACTION (flag n < 10 in L6M or L3M) | FAIL |
|---|---|---|---|---|---|
| Kalshi surprise | 58 | 0 | 0 | 58 | 0 |
Structural reason (as in section 5): flagged trades per cell are at most 180 over 43 months and almost all PRE (e.g. all-08:30 'open at release' q 0.5: 173 trades, 150 PRE, 5 in L6M, 2 in L3M). History-wide skip-gain percentile (flagged trades' P&L versus 33 random event draws): >= 0.90 in 4 of 58 cells (2 distinct cells x 2 actions; about 5.8 expected by chance), <= 0.10 in 0: chance level. Verdict: Kalshi implied-consensus surprise adds nothing testable; the constraint is the action surface, not the data. Planted-edge check: section 6 (pipeline finds 10% / 20% edges) and plant_smoke.py (section 8); header line (desk standard 5): trials counted 58 (TRIALS_LEDGER NDP5K), correction = same-grid shifted/permuted/random-event controls, no White/SPA/DSR (no survivor), PBO not applicable (fixed training-quantile thresholds), in-sample; data-end stamp 2026-08-12 (events), 2026-10-30 (trades); engine dollars base lots, x1.75 and $4.84 RT not applied.
**One-line recommendation per item.**
| item | recommendation | quoted $ |
|---|---|---|
| 1 ES order-by-order | DO NOT BUY the full history (frozen NQ lead has the opposite sign on ES; best-of-12 nonsense bar not beaten; 3-month pilot already bought $52.95) | full history $984.71 (608 GB billable) |
| 2 Auction imbalance | DO NOT BUY more (no recent action surface; bought 8 megacaps + QQQ for $7.19; NYSE all $837.45, SPY $11.82 not needed) | $0 more |
| 3 Asia drivers | NEEDS YOUR APPROVAL for one cheap follow-up: 6J trades full history (6J aggressor flow / 5-15 min move is the only family above its nonsense rate in the paid September pilot); NKD trades $3.89 and NIY trades $10.82 only if 6J holds; ohlcv-1s history is $0.00 but outside the approved scope | 6J trades $33.13 |
| 4 VX | DO NOT BUY (chance level on one month and on the free daily VX history) | 1-min full history $912.49 |
| 5 Macro surprise (Kalshi / Benzinga / Trading Economics) | DO NOT BUY a consensus feed (Kalshi implied consensus free and untestable: 58 of 58 cells NO-ACTION) | consensus feed price not obtained |
| 6 Megacap tape / order-by-order | DO NOT BUY (cheap form owned and null; ES order flow gave nothing to extend) | MBO 3 names $22.10 / 8 names $42.15 pilot month |
| 7 Dealer-gamma API | DO NOT BUY now (no 2023 history for sale; FlashAlpha $1,499 recomputed, not point-in-time) | $1,499 / GEXBot $350 |
