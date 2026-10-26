# PRED FEEDS NEEDED  (PRED-COORD, 2026-10-23)  - NOTHING IS DOWNLOADED. Waiting for the user's written yes/no per feed.
Cost quotes: the coordinator shell has no DATABENTO_API_KEY in its environment, so the free `metadata.get_cost` call could not be made. All $ below are ORDER-OF-MAGNITUDE guesses (unverified, scaled from the $2,024.78 NQ mbp-10 5-yr purchase in DECISIONS.md) and are to be replaced by exact quotes: run `python3 l2vast/pred/feed_cost.py` with the key exported in the env (script calls only metadata.get_cost / get_billable_size / get_record_count, fetches nothing, never prints the key).

## FIRST: what is already on disk (corrects the directive's assumption that Block C/H need feeds for daily data)
- data/databento/B10/fopt_def + fopt_stats: CME futures-options definitions and daily statistics (settlement/OI/volume), 2023-02-01..2026-10-12 -> daily OI-based GEX, put/call OI, walls, max-pain are runnable NOW (Block C-lite, agent predC started). 
- data/databento/B10/opra_spx{ndx,w}_{def,stats}: OPRA SPX/NDX/SPXW definitions + daily stats, 2023-02..2026-10.
- data/gap/vix (VIX, VIX9D, VIX6M, SKEW), data/gap/cot (CFTC COT disagg + legacy zips 2013-2026, no download needed), data/gap/ds50/cboe_putcall_daily.csv, treasury_auctions.csv, data/gap/edgar (filings JSON for top constituents), data/basket (BASKET_ITCH_main, BASKET_EQUS_MINI, BASKET_DBEQ_BASIC: check which tickers/dates before asking for Block D).
So: VIX1D/VIX9D (CBOE, free) and CFTC COT (free): no new fetch needed; VIX1D only if absent from data/gap/vix (that folder has VIX, VIX9D, VIX6M, SKEW; FAILPRED also has f_VIX1D from another source) - Block E/C agents will confirm and re-request only the gap.

## Feed C1 - intraday options flow (Block C, hypothesis: positive dealer gamma -> pinning -> trend trades fail; most likely family to work)
- Dataset/schema: Databento GLBX.MDP3, schema `trades` (and `definition`), parent symbols NQ.OPT and ES.OPT (stype_in=parent). Optional upgrade: schema `cbbo-1s` for NQ.OPT (intraday quotes -> intraday implied vol / delta).
- Range: 2023-02-01 .. 2026-10-23 (the F-R sample). Ask in round 1 for 2024-02-01..2026-10-23 only (WF window) if cost is a concern; training before 2024 is needed (expanding) so full range preferred.
- Approx size/cost: unverified; NQ.OPT+ES.OPT trades ~ tens of GB compressed-equivalent; guess $300-1,500 (trades), cbbo-1s NQ.OPT guess $1,000-4,000. EXACT via feed_cost.py.
- Tests: intraday signed options flow, 0DTE volume share by minute, intraday GEX update (trade-by-trade OI proxy), gamma flip crossing. 
- Justification threshold: only buy if the on-disk daily-OI Block C-lite shows a holdout F-R or G AUC lift >= +0.02 (CIs non-overlapping) over the FAILPRED baseline in a stack, i.e. positive evidence that options positioning carries information at all. Otherwise intraday refinement is unlikely to move AUC from ~0.70 to the 0.72 bar.

## Feed D1 - index internals (Block D)
- Dataset/schema: Databento XNAS.ITCH `trades` (or `mbp-1`/`bbo-1s` if trades-only is not enough for breadth/lead-lag), symbols = top-10 NDX names first (NVDA AAPL MSFT AMZN META GOOGL TSLA AVGO COST NFLX), then top-50. Range 2023-02-01..2026-10-23. Check data/basket first (may already hold part of this).
- Size/cost: unverified; ITCH trades for 10 mega-caps ~ tens of GB; guess $200-800 (10 names), $1,000-4,000 (50). Exact via feed_cost.py.
- Tests: breadth, leadership (VWAP position, OFI, 1-5 s lead-lag vs NQ), dispersion, top-10 correlation to NQ.
- Justification: top-10 first; expand to 50 only if top-10 adds >= +0.02 holdout AUC on top of the stack.

## Feed H1/H4 - economic calendar with consensus/actual, Fed speakers, news (Block H)
- Source is NOT Databento: needs a vendor/free scrape. Request: calendar with release time, consensus, actual, prior, for CPI, NFP, PCE, GDP, ISM, retail sales, FOMC (statement/minutes/speakers), 2023-02..2026-10. Free sources: BLS/BEA/Fed release calendars (times only; consensus requires a vendor, e.g. Trading Economics / Econoday / Bloomberg export). News: headline timestamps (GDELT free; Databento has no news dataset on this plan).
- Cost: free for times and actuals (BLS/BEA/FRED ALFRED vintages); consensus paid vendor ~ $0-500/yr (unverified).
- Tests: surprise magnitude x time-to-release interaction with the +h horizons; event-day failure rate (FAILPRED already has event flags ev_* in ctx; gain must come from consensus/surprise).
- Justification: surprise z-scores must lift holdout AUC >= +0.02 on event sessions in a stack; event-flag-only baseline is already in FAILPRED.

## Status: all four feeds WAITING ON USER YES/NO. No data requested from any vendor.
