# DS3_FEEDS_F2 - T-FEEDS items F3 (Cboe Open-Close), F4 (economic surprise), F5 (IB internals), F6 (FlashAlpha / SqueezeMetrics quote-only)
Updated by W-FD2 2026-11-12 ~21:10Z (update 2; next refresh every 4 h). Shadow only; no PASS claims; nothing bought.

## NEEDS USER (quotes / account actions only the user or lead can do)
1. **Cboe DataShop sales quote**: Open-Close 10-minute history, C1 (SPX, SPXW, NDX) from 2011-01-03 + BZX/C2/EDGX (SPY, QQQ) from 2019-03-01, 12 months and 3.5 years (2023-04..). List price of the live feed per SEC filings is $2,000-3,000/month; history priced ad hoc. The free sample file is already downloaded (below), so loader and features are ready.
2. **Economic consensus with history to 2023-04**: no free historical consensus exists on the net (checked, below). Ask TradingEconomics (guest key discontinued; subscription needed) or Benzinga for a one-month trial/sample with Forecast/Consensus + Actual + Previous + release timestamps; or give a free FMP key (financialmodelingprep.com free tier, account action) for a coverage test.
3. **IB**: run `python3 code/th_feeds/ib_probe.py` on a machine with TWS/IB Gateway + NYSE market-data entitlement and send the printed output (bars returned per symbol/bar size), or tell us there is no IB account. Recorder design: code/th_feeds/IB_RECORDER_DESIGN.md.

## F4 result 1 - owned-data screen: NULL at chance level (details autopilot/DS3_FEEDS_F2_F4.md, code/th_feeds/f4_screen.py, data /mnt/l2/l2vast/_feeds/f4_screen.csv)
- 270 events (CLAIMS 186, NFP 42, CPI 42; 08:30 ET; PRE 171, GAP 24, HOLD 37, L6M 38 by date). Surprise = actual - prior and actual - trailing-3-print mean (poor-man consensus), expanding-std z; price shock = |NQ 1-min open->close at 08:30| (1.5x median = big).
- **Structural fact first: the exact trade lists contain ZERO entries in the 30 minutes after an 08:30 release** (JN05W2, JN05W2_NOCUT, LPB_BASE: all window sums 0.0): the 'pre' session (08:30-09:29) has lots 0 for every book and 09:00-09:59 is blocked. So 'stand aside', 'skip entries' and 'trade with the surprise' have nothing to act on in the current books; trading with the surprise would need a NEW pre-open entry window/book, which is not testable on these trade lists.
- The only exposure is positions OPEN at the release (opened in London). First-order 'flatten at 08:29:59' = pnl from release to exit measured on the same NQ 1-min series: tested 60 cells (3 bases x 4 selections x 5 periods): 3 have placebo p<=0.05 (about 3 expected by chance), all on LPB_BASE (the older base without the survivors' layers), none on JN05W2 and none on JN05W2_NOCUT (NOCUT has only 8 of 43 months so far, partial). Signs differ across bases (LPB_BASE open positions lose after releases: -23k vs placebo +53k, p 0.08; JN05W2: -83k vs placebo -96k; NOCUT +11k vs -1k).
- Verdict: **null / chance level**; no rule recommended. To revisit when JN05W2_NOCUT has 43 months, and with real consensus.

## F4 result 2 - free consensus sources (checked 2026-11-12)
- FRED/ALFRED: release dates and vintage actuals only, no consensus (fredgraph.csv works without a key for current vintages).
- TradingEconomics: guest key discontinued ("guest account has been discontinued"); needs a paid plan.
- Financial Modeling Prep: free tier needs an API key (account action); coverage of historical consensus not verified.
- ForexFactory mirror JSON (nfs.faireconomy.media/ff_calendar_thisweek.json): THIS WEEK only (title, country, date with offset, impact, forecast, previous; rate-limited, HTTP 429 after a few calls); unofficial. **Forward recorder started** (code/th_feeds/ff_calendar_rec.py, nohup, pid in forward_register/ff_calendar/rec.pid, one GET per 10 min, writes only on change) to build our own forecast/actual history from now on at zero cost.
- Alpaca/Benzinga: HTTP 401 without key (W-TL3).
- Conclusion: there is no free historical consensus back to 2023; a paid trial or the forward recorder (months to accumulate) are the only routes.

## F3 - Cboe Open-Close: loader and features READY on the free sample
- Sample downloaded from the public product page (no purchase): /mnt/l2/l2vast/_feeds/cboe_sample/Cboe_OpenClose_2026-09-30_15_20_1.csv.gz (123,022 rows, 88 columns; one 10-min interval 15:20 ET; underlyings include SPX 9,418 rows, SPY, QQQ, XSP, RUT and single names; NDX had no rows in this interval) and the v1.8 10-minute spec PDF (same dir; no pdftotext on the box, read by the user or load later).
- Fields: trade_datetime, underlying, option_symbol (root SPX/SPXW/...), expiration_date, strike_price, call_or_put, days_to_expire, then _qty (trades) and _vol (contracts) for firm / bd / mm / cust_{lt_100,100_199,gt_199} / procust_{same} x open/close x buy/sell, trading_dt, trading_segment.
- Loader + features: code/th_feeds/cboe_oc.py (cust_net_c/p, cust_dir, cust_big_dir (>199 lots), procust_dir, mm_net_c/p, open_frac, zdte_frac, cumulative/diff/flip). Smoke test on the sample: SPX 15:20 interval gross 3.34M contracts, customer net calls +19.5k, net puts +44.4k (cust_dir -0.007), MM net calls -24.4k, puts -62.0k, 0DTE share 75%; SPY gross 0.71M, QQQ 0.67M.
- Observation: the 0DTE share is 66-75% and the customer net direction is tiny relative to gross (|cust_dir| <= 0.02), so a positioning flag will need cumulative intraday sums and extremes, not single-interval levels.
- Comparison with Unusual Whales: pending W-UW's pull (DS3_UW.md): UW's net premium / Market Tide are premium-weighted and market-wide; Cboe open-close is contracts by participant type per root; they overlap on customer-vs-MM flow but only Cboe separates size bands and open/close. Compare once both exist for the same dates (needs the paid history).
- No scoring possible on one interval; scoring waits for history.

## F5 - IB internals: probe script written for the user
code/th_feeds/ib_probe.py (reqHistoricalData TRADES/MIDPOINT, 2D 1-min / 1W 5-min / 1Y 1-day bars + a 5 s live tick for TICK-NYSE, TRIN-NYSE, AD-NYSE, VOL-NYSE; paced 15 s; prints status/size/first-last only), recorder design in code/th_feeds/IB_RECORDER_DESIGN.md (IB Gateway + IBC, NYSE entitlement, 1 Hz x 4 symbols, RTH only). Stopping there as ordered.

## F6 - FlashAlpha / SqueezeMetrics: quote only, not bought; decide after the UW verdict.

## Running (nohup)
- ff_calendar_rec.py (free forward consensus recorder, pid in forward_register/ff_calendar/rec.pid).
- Next hypotheses (log: autopilot/F2_HYPOTHESIS_LOG.md): re-run f4_screen.py when JN05W2_NOCUT reaches 43 months; F4 on ES/RTY-open positions is not applicable; F3 scoring on arrival of history.
