# DATA_TODAY_QUOTE (W-DATA, 2026-11-23 17:15Z): data through today, authority, quote, free alternatives
Order: ~/inbox/20261123_1710Z_Josh-data-through-today-and-live-check.md (copy autopilot/DIRECTIVE_DATA_TODAY_20261123_1710Z.md). Research only. NOTHING was bought, pulled or downloaded: only the free read-only metadata endpoints (get_cost, get_dataset_range) were called; the key came from the process environment and was never printed.

## 1. Where the box's data stops
NQ trades / 1-minute / mbp-10 end 2026-11-13 ~22:00Z (raw/NQ_mbp10_extra to 20261113T22; raw/tail_20261114 adds ohlcv-1m/1s for NQ, ES, RTY, YM to 2026-11-14 08:00Z). CL to 11-13 08:59Z, ZB and 6J to 11-10 (intermarket files; the P_TOPUP_20261110 pull stopped at 11-10 08:00Z, the licence limit for historical that day). The gap to bring the box current is td 20261116 (opens Sun 11-15 23:00Z) through today.

## 2. Spend authority already on record, what each covered, and what is left
Ledger: autopilot/SPEND.json: cap_usd 8,000 (BUDGET AMENDMENT 2, 2026-10-16), spent_usd 9,044.82 (the ledger total already EXCEEDS the 8,000 cap by 1,044.82; it includes the order-specific authorities below, which are not separate ledgers). Per-item sum of the 112 items = 7,515.14; NQ mbp-10 job GLBX-20261013-Y3PCQ4MKV3 (2,024.78) is excluded as the A5 session's own budget.
| Authority (record) | Covered | Spent per ledger | Standing daily update? |
|---|---|---|---|
| Weekly L2 extension, 'Q1 YES' 2026-10-20 (~$25/wk), Q9 same day: 'weekly L2 ~$32/wk until the $8,000 cap then STOP + ask' | NQ/ES/RTY mbp-10 weekly | 31.70 + 35.59 + 38.32 (weeks to 10-30), later weeks (raw/NQ_mbp10_extra to 11-13) | The only STANDING allowance, but the ledger is above its $8,000 cap, so by its own wording it says STOP + ask |
| T-NEXT A2 top-up, 2026-11-10 ('quote < $100, buy, log') | 1-minute top-up to 11-10 for every product | 1.01 | One-off (done) |
| MBO pull <= $250, 2026-11-08 (order 1500Z) | one NQZ6 blind-span MBO pull | 15.08 | One-off, 'any further MBO purchase needs the user' |
| T-CROSS / T-SCREENS 'up to $1,000 total', 2026-11-11 | cross-market data | 143.52 + 290.40 (+0.0 T-UWBOOKS) | Order-specific |
| T-TOOLS 'up to $1,500 for this order only', 2026-11-12 | MBO, options, internals | 290.68 + 54.54 + 0.14 (+54.11 user order 11-12 item 3) | Order-specific, 'no recurring subscription' |
| T-CONFLUENCE L3 history 'up to $2,500' | L3 | 1,095.50 | Order-specific |
| W-ND approved 2026-11-16 (one-off list) | ES MBO Aug-Oct, imbalance, VX, NKD/6J/NIY Sep | 77.41 total (NKD/6J/NIY charged $0.00) | One-off |
| Night standing order 2005Z / inbox rule | no spend, no new machine, no purchase | n/a | Refuses spend |
Reading: NO authority on record is a standing daily-update allowance for td 20261116..today (my reading is right). The only recurring one (weekly L2) is tied to the $8,000 cap which the ledger has passed.

## 3. The vendor's quoted cost (free metadata endpoint, 17:11-17:14Z)
Dataset GLBX.MDP3, continuous symbols NQ.v.0 ES.v.0 YM.v.0 6J.v.0 CL.v.0 ZB.v.0 (stype_in continuous). Window 2026-11-13T22:00Z -> vendor range end. Vendor range end at 17:12Z: trades, mbp-1, ohlcv-1m, ohlcv-1s: 2026-11-23T16:50Z; mbp-10 and mbo: 2026-11-23T09:10Z (about 7.7 h lag); ohlcv-1h 16:00Z; ohlcv-1d 11-23T00:00Z. Metadata after 16:30Z is 'not finalized; costs expected over-estimated'.
| Dataset / schema | Window | Quoted cost |
|---|---|---|
| NQ trades | 11-13 22:00Z -> 11-23 16:50Z | $0.00 |
| NQ mbp-1 (L1 book at 1 ms for Lf0346d55, L12842dde) | same | $0.00 |
| NQ mbp-10 (10-level depth for L578701ed) | 11-13 22:00Z -> 11-23 09:10Z | $0.00 |
| NQ mbo | same as mbp-10 | $0.00 |
| NQ ohlcv-1m | -> 16:50Z | $0.00 |
| ES, YM ohlcv-1m (J502 conditions c9, c10) | -> 16:50Z | $0.00 each |
| 6J ohlcv-1m (Lbb254083), CL ohlcv-1m (L19201dfc, Lc78f2492), ZB ohlcv-1m (L74274eca) | -> 16:50Z | $0.00 each |
| Total | | $0.00 |
Why $0.00: Databento prices a recent window at zero. Probe (get_cost, 1 day each): NQ trades are $0.00 on every date tested (2026-05-01 .. 11-10); NQ mbp-10 is $0.00 for 2026-11-01 and 11-10 but $2.08-4.91 per day for 2026-05-01, 09-01, 09-15, 10-01, 10-15 (and $0.00 on 08-01, not understood). So the free window for depth lies somewhere between 10-15 and 11-01 and ROLLS: the days 11-14..11-23 are free today and may stop being free after some weeks. Re-quote immediately before the pull. Same pattern as the earlier records: LCB_MBO_NIGHT get_cost 0.00 and NKD/6J/NIY Sep 'charged $0.00' (SPEND.json, W-ND, 11-16).
## 4. Approval wording
A $0.00 quote is not a spend, so no approval is needed for the pull above if the quote is still $0.00 when it runs (the lead re-quotes, logs the quote in SPEND.json BEFORE downloading, as the pre-purchase logging rule says, and stops if any line is above $0.00). If Josh still wants it explicit, the one sentence is:
'I approve a Databento GLBX.MDP3 pull of NQ trades, mbp-1, mbp-10 and ohlcv-1m, and ES, YM, 6J, CL, ZB ohlcv-1m, for 2026-11-13T22:00Z through the latest released data, for up to $5 in total, and I approve a daily refresh of the same for up to $5 a day.'
(Total quoted $0.00; the $5 cap only covers the quote moving.) The relay's inbox cannot approve spend; this is worded for him to paste at a terminal.
Files to pull (not run): the six symbols x the schemas above; mbp-10/mbo for NQ only; NQ mbp-10 is about 4-5 GB a day.

## 5. Which D8 books can be checked from what
From D8_BUILD_SPEC.md '(e) DATA beyond NQ trades' lines:
| Book | Needs | NT8 NQ tick export alone? |
|---|---|---|
| Asia Lb0e6dfa3, L92a90948 | NQ trades only | YES |
| Asia L6b373671 | NQ trades + 1-minute NQ for prior-day/week lines | YES if the export covers >= 5 sessions (1-minute built from ticks; back-adjusted opens at rolls need care) |
| Asia L385f4f2e.J502 | NQ trades + NQ 1-minute (Fibonacci pivots up to 30 days) + ES and YM 1-minute | NO: ES and YM 1-minute (from NT8/CQG export of ES, YM or Databento) |
| Asia L578701ed (depth) | 10-level depth at each 1-minute bar close | NO: tick export has no depth; needs mbp-10 (Databento) or a recorded CQG depth |
| NY AM L8cfda948 (block prints) | tape with per-record size and aggressor | PARTLY: NT8 shows ~17% more ticks than the tape; needs Databento trades to compare |
| NY AM Lf0346d55 (order flow) | L1 book at 1 ms | NO: mbp-1 (Databento) |
| NY AM L7cc56d99, L8f11883e | NQ trades + 1-minute NQ lines | YES from ticks if multi-session |
| NY AM Lbb254083 | 6J 1-minute closes, 3 days history | NO: 6J (Databento or NT8 export of 6J) |
| London L19201dfc / Lc78f2492 | CL 1-minute closes + 3 days history + roll flag | NO: CL |
| London L74274eca | ZB 1-minute | NO: ZB |
| London L12842dde | level-1 depth | NO: mbp-1 / mbp-10 |
| NY PM (4 books) | W-D8SPEC4 (in progress) | see D8_NYPM_NOTES.md when written |
NT8 export route: Josh's NT8 / CQG export for td 20261110 was a 22 MB text file for ~18 h of NQ ticks, arriving as an inbox file; the same file type for td 20261123 would cover the Asia books (3 of 5 fully, L6b373671 with 5 sessions) and the NQ-only NY AM books; ES, YM, 6J, CL, ZB would need separate small exports of 1-minute bars (NT8 can export them).
Mac: no host named 'mac' resolves from this box and no mount exists; the Mac's files reach the box only as inbox copies (1/minute). I could not read its contents.

## 6. Earliest date td 20261123 can be on the box
Vendor range ends at 17:12Z today: Asia session of td 20261123 (11-22 23:00Z .. 11-23 07:00Z) is fully released for trades, mbp-1, mbp-10, ohlcv-1m NOW. NY AM (14:30-17:00Z): trades/mbp-1/ohlcv-1m complete by ~17:10Z NOW; mbp-10/mbo for NY AM release at ~01:00Z on 11-24. NY PM (17:00-21:00Z) releases ~21:15Z for trades. Option A (Databento, $0.00 quote, lead pulls after re-quote and logging): td 20261123 Asia + NY AM trades/L1 on the box today; NY AM depth 11-24 ~01:00Z; the whole 11-16..11-22 gap today. Option B (NT8 export): the day Josh drops the file; no depth.
