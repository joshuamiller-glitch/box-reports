USER ORDER — T-ALPHA: ONE COMBINED FORECAST, MANY MARKETS. 2026-11-15. Research only; nothing on the execution server or any live chart changes. Save verbatim as DIRECTIVE_ALPHA_20261115.md, log within 15 minutes. Queue: second, directly after DIRECTIVE_BASIC_TESTS (and after the live-log item when it arrives), 30% of cores. The user: funds with sub-24-hour holds know market conditions and predict; we have not figured this out, and he will pay for any tool that helps. Change of method: stop asking each condition to pass alone. Combine many weak inputs into ONE forecast, across MANY markets, and size by it.

PART 1 — THE FORECAST (NQ first).
1. Target: NQ return over the next 5 / 15 / 30 / 60 / 120 minutes, and the volatility-scaled version, on a 1-minute grid, every session.
2. Inputs: the whole condition library as graded values (not yes / no), one representative per redundancy cluster to start (about 16,000 clusters -> pick by stability, then widen), plus L2 and the L3 history, intermarket, options, calendar, clock.
3. Models, walk-forward only (train on the past, predict the next 2 weeks, roll through all 43 months): ridge / elastic net; gradient-boosted trees; a small neural net; and the average of the three. Heavy regularisation; no tuning on the test span.
4. Score the FORECAST, not rules: information coefficient (rank correlation of forecast and realised return) per horizon, per session, per year and in the recent months; its stability; decay with horizon; and the same for 200 nonsense inputs run through the identical pipeline. Report what share of the information coefficient survives after removing each block (which data actually carries it: price, L2, L3, intermarket, options).
5. Turn it into trades with costs inside: position proportional to forecast strength, with a no-trade band sized to the measured cost (fees $4.84 round trip, measured slippage), turnover penalty, risk cap. Report gross and net, turnover, average hold, capacity in lots.

PART 2 — USE IT ON D7 (it does not replace the books).
6. As SIZE for every D7 signal: lots scale with the forecast in the trade's direction (exact engine, every signal, no skipping, so no path effect).
7. As the bracket input: forecast return and forecast volatility at the trade horizon set target and stop per trade.
8. As hold / cut and take / hold inside a trade, jointly with the live loss and profit lines.
9. As its own book through the injection hook, flat by session end, and scored for correlation with the live books and for what it does to stack drawdown.

PART 3 — BREADTH (where a small edge becomes a large one).
10. Run PART 1 on every liquid futures market we can get clean intraday data for: ES, RTY, YM, micros, ZN, ZB, ZF, ZT, 6E, 6J, 6B, 6A, 6C, GC, SI, HG, CL, NG, RB, HO, the grains, NKD, BTC and ETH futures. Same pipeline, each market's own inputs plus cross-market inputs.
11. QUOTE the history needed (1-minute and top-of-book for all; depth for the most liquid) from 2023-04, by market. The user has said cost is not the obstacle if it works: quote it clearly and he will decide. Start now with what is on the box (ES, RTY, YM, NKD, 6J, ZN, ZB, 6E, GC, SI, CL).
12. Portfolio: combine the per-market forecasts with risk-parity weights and a correlation-aware cap. Report the information ratio of each market alone and of the portfolio, and how it grows with the number of markets (it should grow roughly with the square root of independent bets; show whether it does).
13. Cross-sectional version: rank the markets against each other each minute and trade the spread between the top and bottom of the ranking (relative value), which removes the common market move.

PART 4 — COSTS AND DATA HYGIENE (the unglamorous half).
14. Per market: measured or estimated cost per round trip in ticks, the forecast horizon at which the edge exceeds twice the cost, and the passive-entry version (rest at the bid / offer, cancel after N seconds) with realistic fill rates.
15. Data audit before any result: roll handling, stale prints, session gaps, timestamp alignment across markets to the second, look-ahead check on every input (shift every input one bar later and confirm the information coefficient does not jump).

CONTROLS. Walk-forward everywhere; the nonsense-input pipeline beside every headline number; cluster-robust errors by day; results by year and for the months since 2026-05; the planted-edge check (add a known 0.02 information coefficient signal and show the pipeline recovers it); capacity and turnover stated. "Nothing" is not a deliverable: report the information coefficient we have, where it comes from, and what would raise it.

EXPECTATION, stated so nobody is misled: a single-market information coefficient of 0.01-0.03 at these horizons is a normal, usable result for this kind of model;
[NOTE (lead): the pasted order ends here, mid-sentence, with a semicolon after "model"; the remainder of the user's sentence did not arrive.]
