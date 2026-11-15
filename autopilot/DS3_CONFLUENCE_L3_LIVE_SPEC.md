# DS3_CONFLUENCE_L3_LIVE_SPEC (W-CF2): what D7 would compute live for the first L3 candidate, c_H2_arrival_imb60_lo
VERDICT: the candidate needs live market-by-order (L3) data for NQ and one counter; an L2 depth proxy built from mbp-10 (depth added over the same 60 s) does NOT reproduce it (lift +$12/trade vs +$144, years -116/+86/+10/+9 vs +75/+200/+114/+160), so the live L3 feed is the whole price of this item. Status: table-level lead (W-CF3: passes matched-count tests, 8 variants tried, not pre-registered); engine set TL3_CF_U7 queued; nothing here is a PASS.

## 1. Event stream
CME MDP 3.0 GLBX market-by-order for the front-month NQ contract (Databento live schema `mbo` on GLBX.MDP3, or an equivalent CME L3 feed): one record per order action with action (A add, M modify, C cancel, F fill, T trade, R clear), side (bid/ask), price, size, order_id, ts_recv. Front month = the contract D7 trades (same roll rule as the engine). Today's live plan on the research box covers L1/trades only (DS3_LIVE_MBO.md: no live MBO or MBP-10 entitlement); NT8 depth is aggregated by price level and carries no order ids, so it cannot give this item.

## 2. State kept
- Best bid and best ask in ticks (0.25), updated from the book after every A/M/C/F/R record (order table keyed by order_id: price, size, side). Rules as in code/th_confl_cf2/mbo_sec.py (copied from code/mbo_book): A inserts, C removes size, F reduces the resting order, M replaces price and size, R clears the book, T does not touch the book.
- One counter per side per second: ADD_NEAR_bid[s], ADD_NEAR_ask[s] = number of records with action A (new orders only, not modifies) whose price is within 5 ticks of the best price OF THE SAME SIDE at that instant (before the order is inserted). Order count, not size.

## 3. The value at a signal
For a signal at second T (the engine signal second sig_ts), side s (+1 buy, -1 sell), use the 60 complete seconds [T-60, T-1] (nothing from second T itself):
- own = sum of ADD_NEAR on the trade's own side (bids for a buy), opp = sum on the opposite side (asks for a buy).
- arrival_imb60 = (own - opp) / max(own + opp, 1), range -1..+1.
(Box check on 2026-10-19: own 3,298 and opp 2,283 adds give 0.182; see /mnt/l2/l2vast/_confl/forward_check/c_H2_arrival_imb60_lo.csv.)

## 4. The 20-day trailing normalisation (the yes/no)
- D7 stores arrival_imb60 for EVERY entry signal of every book it sees (taken and skipped, all sessions), keyed by trading day (ld = the engine trading day).
- For a signal on trading day d: take all stored values with trading day in the 20 trading days before d (d excluded); require at least 150 values (otherwise the item is unknown); q20 = numpy-style linear 20th percentile of them. Condition yes = arrival_imb60 <= q20 (about 20% of entries). The mirror item `_hi` uses the 80th percentile with `>`.
- Why: L3 behaviour drifted strongly between 2023 and 2026 (order sizes at the touch fell, cancel-to-trade rose), so fixed thresholds are not comparable across years; the percentile form is.
- Needs a warm-up of 20 trading days of the same L3 series before the first usable day (about 4,000 values, 150 minimum reached within the first day or two).

## 5. How the candidate is used (as tested)
Engine set TL3_CF_U7: SKIP the signal when the condition is NO (about 80% of entries), keep when yes; W-CF3 table: keeping the yes side gives 3,861 taken trades (about 4 a day), $222 vs $106 per trade, max drawdown 42,526 vs 92,243. This is a very strict gate; the engine decides because a skip frees the book. Unknown (feed down, <150 history, gap > 5 s inside the window) must be defined before any build: recommended = unknown counts as NO only if the user wants the strict gate to fail closed; the tested version never had unknowns (all 19,785 taken entries had a value).

## 6. Volume and latency
About 250 records/s average, peaks about 9,000/s; roughly 20 million records per day. Only the book state and two counters per second are needed, no storage of raw records. Staleness budget: the window ends at second T-1, so the value must be ready within about 1 s after the second closes.

## 7. What it costs (public pages, not binding; quotes in DS3_CONFLUENCE_L3_QUOTES.md)
Databento Live Standard $199/month (listed with no license fee; which plan carries live MBO is not stated on the pricing page: confirm with Databento sales before ordering); a Rithmic or CME-direct L3 route is not priced publicly. History already bought (NQ MBO 2023-04..2026-04, $1,095.50) covers the research; ES MBO would be $844.71 if ever wanted.

## 8. Parity test before any build
Run the same record stream live and from the box files for one day; compare the per-second ADD_NEAR counters and the daily arrival_imb60 values; then compare the live yes/no with the forward check file (the box's values for the most recent 10 trading days) for every signal.
