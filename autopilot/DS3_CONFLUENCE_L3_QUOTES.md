# DS3_CONFLUENCE_L3_QUOTES (W-CF2, 2026-11-14 ~00:10Z). Quotes only, nothing bought by this page.
VERDICT (data ends 2026-11-14): NQ MBO 2023-04..2026-04 is $1,095.50 in three yearly batches (inside the user's $2,500 L3-history authority; the lead's script already submitted 2025-05..2026-04 at $409.65); ES MBO for the same span is $844.71 (quote only, no authority yet); a live L3 feed is roughly $199/month (Databento Standard, no license fees listed) or CME depth entitlement $12-17/month non-pro per exchange via a Rithmic broker, to be confirmed.

Method: Databento metadata.get_cost / get_billable_size, dataset GLBX.MDP3, schema mbo, continuous front month (NQ.v.0, ES.v.0), key read from the environment inside `bash -ic`, never printed. Quotes at 2026-11-14.

| span | NQ $ | NQ GB billable | ES $ | ES GB billable | on the box? |
|--|--|--|--|--|--|
| 2023-04-01..2024-05-01 | 315.00 | 187.9 | 246.29 | 146.9 | no |
| 2024-05-01..2025-05-01 | 370.85 | 221.2 | 292.72 | 174.6 | no |
| 2025-05-01..2026-05-01 | 409.65 | 244.4 | 305.70 | 182.4 | NQ batch submitted by lead (SPEND.json CONFL_MBO_Y2025_05_2026_04); ES no |
| 2026-05-01..2026-11-14 | 249.30 | 196.8 | 138.25 | 108.4 | NQ yes (L3M_PRE, L3M, TAIL); ES no |
| TOTAL not on the box (2023-04..2026-04) | 1,095.50 | 653.5 | 844.71 | 504.0 | |
| TOTAL 2023-04..today | 1,344.80 | 850.3 | 982.96 | 612.4 | |

Disk: about 0.45 of billable on disk (earlier NQ months: 52 GB for ~120 GB billable): NQ remaining about 295 GB, ES the same span about 227 GB.

LIVE L3 FEED (public pages, not binding; confirm with the vendor before any decision):
- Databento Live, GLBX.MDP3 (incl. L3 MBO): Standard plan $199/month, listed with "no license fees"; Plus $1,750/month license fees (annual); Unlimited $4,500/month (annual); usage-based live billed per message plus pass-through license fees. The pricing page does not state clearly which plan carries MBO live: confirm with Databento sales. Source https://databento.com/pricing
- Rithmic / broker route (order-by-order depth is delivered as market-by-order only through Rithmic R|API+ style access, price not published): CME depth (Level 2) non-pro about $12.10-17 per exchange per month, $36.50-48 for the four CME-group bundle, plus a Rithmic connection fee about $25/month per user ID (AMP Futures table effective 2026-06-01; NinjaTrader and a third-party guide agree within a few dollars). Bookmap quotes its own MBO add-on at $39/month per exchange or $101/month for the CME bundle (platform charge, separate). Professional classification would multiply CME fees several times.
- Already on the box: the live MBO recorder (autopilot/DS3_LIVE_MBO.md) shows D7's server can ingest an MBO stream today; whether it is a paid entitlement or a derived feed is not restated here.
- Reading: if the L3 conditions show lift on the months on the box and on the bought NQ history, the live cost is of the order of $200-250/month (Databento Standard) against D7 profits of thousands per week; any L3 condition reaching the build list needs it live.
