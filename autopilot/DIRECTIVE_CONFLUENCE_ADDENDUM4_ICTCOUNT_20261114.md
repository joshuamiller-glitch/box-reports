ADDENDUM 4 (user) to T-CONFLUENCE — ICT-STYLE CANDLE COUNT (7-13-21 TIME SEQUENCE). Research only. Save verbatim as DIRECTIVE_CONFLUENCE_ADDENDUM4_ICTCOUNT_20261114.md, log within 15 minutes. Part of BLOCK 6 (counting). Source: a public thread the user supplied; rules as stated there, coded mechanically. Write the exact coding in CONFLUENCE_DEFS.md with worked examples from our own NQ data BEFORE scoring.

THE COUNT, as stated:
R1. Anchor = the highest high or lowest low. Code three anchor definitions and score each: (a) the extreme of the last 20 / 40 / 60 bars of that timeframe (the thread's 20-40-60 look-back); (b) the last confirmed swing extreme (causal pivot, known only after its right-side bars close) at 3 / 5 / 10 bars each side; (c) the session / week / month extreme. A new extreme beyond the anchor resets the count to that bar.
R2. From a low, count only up-closed candles; from a high, only down-closed candles.
R3. Do not count an inside candle: a candle that takes out neither the high nor the low of the previous candle.
R4. Consolidations are skipped: the count starts from the extreme that leads to the break. Code as: when the last N bars sit inside a range narrower than k x ATR, the anchor moves to the range's extreme on the side opposite the eventual break (N = 8 / 12 / 20, k = 1 / 1.5). Also score the version WITHOUT R4, since R4 is the most subjective rule.
Key counts: 7-8, 12-13, 20-21, 33-34, 40-42. Timeframes: daily and weekly (as context for the day, since the user trades intraday), and 240 / 60 / 15 / 5 / 3-min for intraday use.

STEP A — MEASURE, NO TRADING. Is there anything at these counts?
1. For every count 1..60 on each timeframe and each anchor definition: the rate of (i) a retracement of at least 0.5 / 1 ATR starting at that count, (ii) a swing extreme that holds for the next 5 / 10 / 20 counted candles, (iii) a failed breakout of the prior swing (turtle soup) at that count. Plot the rate by count.
2. The claim is clusters at 7-8, 12-13, 20-21, 33-34, 40-42. Test each key count against its neighbours (two counts either side), against the smooth trend of the curve (longer runs are rarer and end more often anyway: fit that and test the EXCESS at the key counts), and against the same count from RANDOM anchors.
3. Do the specific rules matter: the same curves with all candles counted (no R2), with inside candles counted (no R3), with and without R4. If the plain count gives the same curve, the special rules add nothing.
4. Multi-timeframe: rate when two or three timeframes sit at a key count at once versus one.
5. Ignore the thread's "time distortion" clause: a miss is a miss.
Report per timeframe and per session, recent windows first, then the full history (daily and weekly counts can use the longest NQ history on the box).

STEP B — AS CONFLUENCE CONDITIONS in the entry table (every D7 signal, 43 months), for each timeframe and anchor version:
- the current count; at a key count yes / no; which key count;
- with-the-trend conditions: count at 7-8 or 33-34 and the signal is in the direction of the counted move after a retracement;
- exhaustion conditions: count at 12-13, 20-21 or 40-42 and the signal is WITH the counted move (candidate veto) or AGAINST it (candidate go);
- number of timeframes at a key count; daily and weekly count state as day context;
- counted candles since the anchor versus all candles since the anchor (how "distorted" the leg is).
These go through steps 3-5 of the parent order like every other condition, and into the redundancy clustering with the other counting schools and with plain "bars since swing" and "leg extension in ATR". If the count is only a proxy for how extended the move is, the clustering will show it.

STEP C — AS BOOKS, through the exact-engine injection hook, intraday only, flat by session end:
1. CONTINUATION BOOK: count reaches 7-8 (and separately 33-34) on the 15- or 60-min; enter with the counted move on a retrace into the most recent fair value gap or order block formed inside the leg (code both: 3-candle gap; last opposite candle before the impulse); stop beyond the gap / block or the retracement low; target the leg's extreme and 1R / 1.5R / 2R; time stop.
2. EXHAUSTION BOOK (turtle soup): count at 12-13, 20-21 or 40-42; price takes out the prior swing extreme and closes back inside within 1-3 bars; fade it; stop beyond the sweep extreme; targets as above.
3. Each on 5 / 15 / 60-min counts, with and without the higher timeframe at a key count, long and short separately, session by session. Grid kept small (the thread's own counts, not a search over counts).
4. CONTROL BOOKS: the same entries at the neighbouring counts (5-6, 9-11, 15-18, 24-30) and from random anchors. The real book must beat those, not just beat zero.

RULES as in the parent order: session by session; recent windows from today first; a lead must hold in recent AND older windows; drawdown first; measured fills; exact placebos; matched-count control for every filter; walk-forward. The key counts come from the thread and are fixed in advance: do NOT tune them. If other counts turn out better, report that as a separate, searched result with its own controls.

REPORT. Section "ICT count" in DS3_CONFLUENCE_ITEMS.md (Step A curves and Step B table) and in DS3_CONFLUENCE.md (books). Plain one-line verdict: is there an excess at the named counts, yes or no, on which timeframes, and by how much over the neighbours. Step A within 6 hours.
