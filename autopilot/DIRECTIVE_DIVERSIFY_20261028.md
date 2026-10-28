# DIRECTIVE 2026-10-28 T-DIVERSIFY (intraday) (verbatim from user)

T-DIVERSIFY (intraday) — diversifiers for the live stack on other markets, at each market's own clock (2026-10-28)

Research only. No live, execution-server or chart change. UNTOUCHED never read. No purchase without the user's OK (section 0 lists what to ask for). Redact account ids in anything mirrored. No multi-day holds anywhere in this program: every position is flat by its market's session close (or, in section 2 only, by the next open).

Why this program is different
Everything scored so far is NQ intraday bar patterns, and the cross-instrument work scaled NQ rules down by a range ratio. That tests whether NQ rules port; it does not test whether ES, CL, ZN, GC, 6E, RTY, YM have intraday structure of their own. This program does that, market by market, from each market's own time-of-day behaviour. Evidence standard: a rule is CONFIRMED by holding up across years (every year 2023-2026 positive or within MDE, with the pre-2025 and post-2025 halves both positive), by beating both placebos (random direction same clock; same rule random clock), and by replicating on the market's nearest sibling where one exists (ES<->RTY/YM, ZN<->ZB/ZF, CL<->RB/HO, GC<->SI) when data exists. Preregs small (<= 12 cells per market: one obvious rule per window, no grids). Fees per market from FEES.md where present, WEAK label otherwise, 2x-cost column always. Objective = marginal Sharpe added to the live stack's weekly P&L at fixed risk and P&L in the stack's 20 worst weeks, not standalone return.

0. Data inventory first (report within 1 h, before any scoring)
Per market on disk: symbol, resolution, first/last date, roll method, fee line. Then what a proper intraday program on the other markets would need and the cost: tick/trades for ES, CL, ZN, GC, 6E, RTY, YM (Databento trades schema via the existing key and env var only — never in a file or the chat), and whether mbp-1 (top of book) is worth it for stop-fill realism on each. Score on what exists now; do not wait for purchases.

1. Time-of-day maps per market (the base of everything below)
For each of ES, RTY, YM, CL, ZN, GC, 6E (and NQ as the reference): the average and median signed return, range, and volume per 15-min window across the full session, by year, and by day-type (trend day / range day by the first-hour range vs the 20-day median). Show which windows carry the market's drift, which carry its range expansion, and which are dead. Then the structural events each market has: CL 10:30 ET inventory (Wed) and 14:30 settle; ZN/ZB 08:30 releases, 13:00 auctions, 15:00 close; GC 05:30/10:00 ET London fixes, 13:30 settle; 6E 08:30, 11:00 London close; ES/RTY/YM 09:30 open, 10:00 data, 15:50 MOC imbalance, 16:00. Report the event-window return/range profile around each. This section is descriptive; no cells.

2. One obvious rule per window, per market (<= 12 cells per market)
From section 1, for each window that shows a repeatable profile: the single rule the profile implies (drift window: enter at window open in the drift direction, flat at window end; range-expansion window: break of the pre-window range with a bracket at the market's own median-range multiple; post-event: continuation vs reversal of the first 5-min move after the event). Bracket = 1x / 1.5x the market's median window range, flat at window end at the latest. Per cell: trades/wk, WF/HOLD/by-year mean with CI and MDE, both placebos, 2x cost, sibling replication. Include the overnight-hold cells (buy settle, flat next open; the equity-index overnight premium; and the B3_F19 signals on ES/RTY/YM themselves), as these are the one overnight family the stack already runs.

3. Cross-market intraday signals into NQ and ES (the stack's own markets, new information)
Not new books: filters or entries for the existing clock. (a) Bond-equity: a ZN move > 1x its 30-min median range in the first hour — does the NQ/ES drift that follows pay as a bracket entry? (b) 6E/DXY first-hour direction vs ES. (c) CL shock (> 2x median 5-min range) vs ES in the next 30 min. (d) ES-NQ-RTY relative strength at 10:00: the laggard catching up vs the leader continuing. Each one cell per side. The point: information the NQ books do not have.

4. Volatility-regime gates for the existing books (live-eligible once scored, per the user's rule)
Daily ATR/VIX-tercile and first-hour-range gates applied to the live stack's own entries (ST/HM/WT/KB/SM/PE): trade only / size down in the bottom tercile, size up in the top. Paired by week vs unscaled, exact lock engine, shifted-label placebo, by year. (The DS3_SIZING programs tested vol-scaled lots; this tests on/off gates by regime — report the difference plainly.)

5. Portfolio
For every rule that is CONFIRMED: add it to the live stack at 10%, 20%, 30% of stack risk; report marginal Sharpe, maxDD change, worst-20-weeks P&L, weekly correlation. The solve: the 2-3 rules that give the best stack Sharpe with maxDD not worse. Verdict line names them with weekly $ at the chosen risk and $ in the stack's worst 20 weeks.

6. For anything CONFIRMED: the Sim spec
Instrument, session, signal with its exact times in ET, order type, bracket in ticks, flat rule, lots at $1,000 risk and at the user's lot scale, costs assumed, plain-English paragraph. Codeable in NT8 without reading the study.

Reporting
DS3_DIV_0_INVENTORY.md first (with the purchase list and cost). DS3_DIV_1_MAPS.md (section 1, all markets, with the plots described in words), then DS3_DIV_<market>.md per market (never-empty-handed: top cells regardless of verdict, failed gate, MDE), DS3_DIV_XMKT.md (section 3), DS3_DIV_VOLGATE.md (section 4). MORNING.md every 2 h. DS3_DIV_FINAL.md: one verdict line per market and per cross-market signal. Use all cores; bars-only work should not need the replay memory.
