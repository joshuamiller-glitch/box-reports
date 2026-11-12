# DS3_LIVE_MBO — live MBO recorder (order 2026-11-12 19:45Z) — STOPPED AT STEP 0: MBO NOT ENTITLED
Written 19:45Z by W-LR. Shadow/research only. Key was read only from env DATABENTO_API_KEY (never printed/logged/written).

## Entitlement test (live gateway, GLBX.MDP3, NQ.v.0 continuous, one short session <=10 s at a time, no session left open)
| schema | result |
|---|---|
| **mbo** | **ErrorMsg: "Not authorized for mbo schema"** |
| **mbp-10** | **ErrorMsg: "Not authorized for mbp-10 schema"** |
| mbp-1 | OK (58,698 MBP1 records in a 3-min replay + live) |
| tbbo | OK |
| trades | OK |
| cmbp-1 / cbbo-1s | OK |
| bbo-1s, bbo-1m | OK |
| ohlcv-1s / 1m / 1h / 1d | OK |
| definition, statistics, status | OK |
| imbalance | not supported for this dataset |

So the active live plan entitles top-of-book (L1: mbp-1 / tbbo / bbo / cbbo / cmbp-1), trades, OHLCV, definition, statistics, status for GLBX.MDP3. It does NOT entitle live MBO (L3) or MBP-10 (L2 depth). Per the order I stopped here: no recorder was started, no features, no parity run, nothing written to live_mbo/.
Docs facts (databento.com/docs): Live client supports intraday replay up to 24 h (GLBX.MDP3 mbo/definition can replay the whole weekly session), reconnect_policy='reconnect' = one attempt; Standard plans: 10 simultaneous sessions per dataset per team (the user's "two devices" limit is a licence term, not the API limit); subscription via add_stream writes raw DBN.

## What would unblock the order
Live MBO/MBP-10 needs a higher CME live entitlement (the account's live plan shows L1 only). Historical MBO/MBP-10 purchase (batch) is unaffected and continues (L3M MBO bought by the lead).
## What the entitled schemas could still do (not started; ask the lead)
- record mbp-1 (top of book + every trade, 1 record per book/trade change) live to /mnt/l2/l2vast/live_mbo_l1/ : gives live trades/BBO for parity and lag (ts_recv - ts_event) but NOT depth, so no pulled/MedLevel and no MBO event detectors.
- tbbo/trades parity vs the historical 'trades' for the same session.
Test tool: code/th_livembo/entitle_test.py (one short live session per call).
