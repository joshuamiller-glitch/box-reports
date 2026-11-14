USER ORDER — T-RANGE2: BUILD A BETTER RANGE FORECAST THAN UW. 2026-11-14. Research only; nothing on the execution server or any live chart changes. No spend without a quote and the user's OK. Save verbatim, log within 15 minutes. Runs beside T-CHOP at up to 20% of cores; its output feeds the bracket-scaling dials (dial 9) and the chop call.

WHY. In DS3_UWREGIME / DS3_RANGEUSE the UW range forecast is almost entirely the IV term group; the full UW model is not better than ATR + IV term. The useful thing is the options market's expected move. UW reads it indirectly (QQQ / NDX, US hours only, prior close for Asia and London). Build the direct version and see if it beats UW.

BUILD, all causal, each available at the session's own start and updated intraday:
1. NQ and ES OPTIONS ON CME (data already on the box via Databento; pull any missing days and quote the cost first): at-the-money straddle price of the nearest expiry and the next one -> implied move for the rest of today and for tomorrow, in NQ points; refreshed at 18:00, 02:00, 08:30, 09:30, 10:00 ET and every 30 min; plus implied move minus the move already made today, and the forward implied move between the two expiries (what the market expects from the NEXT session alone, which isolates event days).
2. REALIZED-VOLATILITY MODEL on our own NQ bars: HAR-type model (yesterday, last 5 days, last 22 days of realized range / realized variance, per session), with the overnight and prior-session terms, refit walk-forward. This is the benchmark to beat, replacing plain ATR.
3. Cboe short-dated vol indexes (one-day, nine-day, VXN), free daily history, as extra inputs.
4. Event calendar flags already on the box.
5. COMBINED model: 2 + 1 + 3 + 4.

COMPARE, per session (asia, london, pre, nyam, nypm, last 90 min), out of sample, walk-forward, L3M and L6M from today first then older: R2 and rank accuracy (share of days where big / normal / small was called right) for: ATR only; HAR; HAR + CME implied move; the combined model; the UW (b) and (c) models. Report the gain of each over HAR, with shifted-day placebos. State plainly, per session: does the direct CME version beat UW, match it, or lose. Asia and London matter most: UW is stale there and CME options are live.

THEN re-run the best dials with the winning forecast in place of UW: dial 9 (whole bracket at constant R), the one-sided nearer target, and the London range-used-up rule. Same rules, gate and placebos as the parent orders.

OUTSIDE VENDORS, QUOTE ONLY: say what ORATS and ThetaData would add that the CME build cannot (longer history, forward vol, event-stripped vol), and what each costs. Do not buy.

DELIVERABLE. DS3_RANGE2.md, plain verdict at the top: the best range forecaster per session, how much better than UW, and whether the UW subscription is still needed for it. First page (HAR benchmark + CME implied move coverage and first comparison) within 4 hours.
