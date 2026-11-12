# F2_HYPOTHESIS_LOG (W-FD2, T-FEEDS F3-F6) - append only, one line per hypothesis, so nothing is run twice
- 2026-11-12 F3-H0: Cboe Open-Close 10-min as customer-vs-MM positioning flag - NOT TESTABLE (no data owned; price unpublished; sample file only) - status: quoted, waiting on user/sales quote.
- 2026-11-12 F4-H0: economic surprise (actual-consensus) first 1-30 min rules - NOT TESTABLE with consensus (owned DISCOVER_CALENDAR.csv has 0 consensus cells; 270 actual+prior cells: CLAIMS 186, NFP 42, CPI 42 from ALFRED first prints) - status: prior-change surprise is the only owned variant; scheduled.
- 2026-11-12 F5-H0: IB internals - NOT TESTABLE on the box (no IB access).
- 2026-11-12 F4-H1 (run): actual-prior and actual-trailing-3-mean surprise z vs 08:30 ET release windows on exact trade lists (JN05W2, NOCUT 8 months, LPB_BASE): entries in 1/5/10/30 min windows = 0 trades by design (pre session lots 0, 09:00-09:59 blocked); open-at-release post-release pnl: 60 cells, 3 at p<=0.05 (chance 3), all LPB_BASE - NULL at chance level.
- 2026-11-12 F4-H2: price-shock (NQ 1-min 08:30 move >= 1.5x median) selection of the same events: same result, NULL.
- 2026-11-12 F4-H3 (queued): trade-with-the-surprise needs a pre-open entry window (not in current books) - not testable on exact lists.
- 2026-11-12 F4-H4: free consensus sources checked (TE guest discontinued, FMP needs key, FF mirror this-week only/429, FRED none) - forward recorder started.
- 2026-11-12 F3-H1: sample loader/features built (cboe_oc.py); scoring waits for history.
- 2026-11-12 F5-H1: IB probe script written for the user; no box access.
