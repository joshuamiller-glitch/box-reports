# DISCOVER_CALENDAR (T-DISCOVER B/C prep, built 2026-11-03)

File: `outputs/autopilot/DISCOVER_CALENDAR.csv` (1274 rows, 2023-04-01..2027-03-31; rows after 2026-11-03 are forward). Columns: date_et,time_et,event_type,description,source,confidence,actual,consensus,prior. Builder: `outputs/l2vast/ds3/code/discover/build_calendar.py` (+ auction json, alfred_cache.json). Rerun is idempotent.

## Counts per event type per year
| event_type | 2023(Apr-) | 2024 | 2025 | 2026 | 2027(-Mar) |
|---|---|---|---|---|---|
| CLAIMS | 39 | 52 | 53 | 52 | 12 |
| CPI | 9 | 12 | 11 | 12 | 3 |
| EARLY_CLOSE | 8 | 10 | 11 | 10 | 2 |
| FOMC_DECISION | 6 | 8 | 8 | 8 | 2 |
| FOMC_MINUTES | 6 | 8 | 9 | 8 | 1 |
| FOMC_PRESSER | 6 | 8 | 8 | 8 | 2 |
| GDP | 9 | 12 | 10 | 13 | 0 |
| HOLIDAY | 1 | 3 | 3 | 2 | 2 |
| ISM_MFG | 9 | 12 | 12 | 12 | 3 |
| ISM_SVC | 9 | 12 | 12 | 12 | 3 |
| MONTH_END | 12 | 16 | 16 | 16 | 4 |
| NFP | 9 | 12 | 11 | 12 | 3 |
| NQ_ROLL_WEEK | 15 | 20 | 20 | 20 | 5 |
| OPEX_MONTHLY | 6 | 8 | 8 | 8 | 2 |
| OPEX_QUARTERLY | 3 | 4 | 4 | 4 | 1 |
| PCE | 9 | 12 | 10 | 13 | 0 |
| PPI | 9 | 12 | 10 | 13 | 3 |
| QUARTER_END | 6 | 8 | 8 | 8 | 2 |
| RETAIL_SALES | 9 | 12 | 11 | 13 | 3 |
| TREASURY_AUCTION_10Y | 13 | 18 | 18 | 15 | 0 |
| TREASURY_AUCTION_20Y | 9 | 12 | 12 | 10 | 0 |
| TREASURY_AUCTION_2Y | 18 | 24 | 24 | 18 | 0 |
| TREASURY_AUCTION_30Y | 10 | 14 | 14 | 12 | 0 |
| TREASURY_AUCTION_3Y | 9 | 12 | 12 | 10 | 0 |
| TREASURY_AUCTION_5Y | 13 | 16 | 16 | 12 | 0 |
| TREASURY_AUCTION_7Y | 9 | 12 | 12 | 9 | 0 |

## Sources and confidence
- source-confirmed (fetched 2026-11-03): FOMC decision dates (federalreserve.gov; 2027 tentative per Fed); CPI, PPI, NFP (bls.gov year schedule pages 2023-2025, 2026 page, release-schedule pages for Oct 2026-2027; all 08:30); retail sales (census.gov indicator calendars 2023-2027, 08:30); PCE and GDP for 2026 only (bea.gov schedule); Treasury 2Y/3Y/5Y/7Y/10Y/20Y/30Y coupon auctions (fiscaldata auctions_query; 13:00 ET; data through 2026-10-22, so the Nov-2026 refunding is not in yet; TIPS returned empty).
- rule-derived: FOMC presser 14:30 (every scheduled meeting) and minutes (decision + 21 d, Wed 14:00); claims dates (every Thu 08:30, Wed if Thu is a holiday; the VALUES are first prints from ALFRED); ISM mfg (1st business day) and services (3rd business day) 10:00; opex monthly (3rd Fri 16:00; Thu if holiday), quarterly (Mar/Jun/Sep/Dec, 09:30 SOQ); month-end/quarter-end = last two NYSE trading days (quarter months use QUARTER_END only, no MONTH_END row); NQ_ROLL_WEEK = the 5 weekdays of the week before the expiry week (roll Thursday = expiry - 8 d, named in description); HOLIDAY and EARLY_CLOSE (CME equity rules).
- Surprise fields: actual/prior = first print from ALFRED vintage on the release date (NFP change in k, prior as revised in that vintage; CPI SA headline m/m % computed from index levels, core m/m in description; claims level). Consensus is blank everywhere (not free). Actuals are blank for rows after 2026-11-03.

## UPDATE 2026-11-03 (second pass)
- PCE and GDP 2023-04..2025-12 now filled from ALFRED vintage days (day on which PCEPI / GDPC1 last values change, filtered: GDPC1 days 17-22 of Jan/Apr/Jul/Oct are non-GDP revisions and dropped). They match the known end-of-month BEA pattern; confidence label 'source-confirmed (ALFRED vintage)'. PCE has no Oct/Nov 2025 row (shutdown; BEA 2026 page shows PCE 2026-01-22). GDP 2025-12-23 = 3Q25 initial (shutdown-delayed). The PCE row for 2025-12-23 is intentionally omitted (ALFRED change there was GDP-driven, not confirmed as a PCE release).
- Early-close/holiday times replaced by what NQ actually did (last 1-min bar in out/def/NQ.parquet, through 2026-10-16): MLK/Presidents/Memorial/Juneteenth/Jul 4/Labor/Thanksgiving halt 13:00 ET; Jul 3, day-after-Thanksgiving, Dec 24 halt 13:15; 2025-01-09 halt 09:30 (mourning day). Good Friday on NFP day (2023-04-07, 2026-04-03) NQ traded an abbreviated session until 09:15 ET, so NFP 08:30 fell inside it (now EARLY_CLOSE 09:15). Good Friday 2024-03-29 and 2025-04-18, Christmas, New Year: no bars. 2027 rows remain rule-derived. CME's own holiday page was not reachable (timeout/third-party only).
- ISM: ismworld.org calendar is behind a login (redirect); only third-party estimates exist (2027), so ISM stays rule-derived (1st / 3rd business day, 10:00). The ISM Services June 2026 print was reported moved by the Jul-3 holiday (a business-day rule that counts Jul 3 as a non-business day is applied: see build_calendar.py FEDHOL).

## Gaps (first pass; PCE/GDP and Good Friday items are now closed, see update)
- PCE and GDP 2023-04..2025-12: not obtained (BEA archive pages not reachable; FRED release pages 404). Not rule-filled on purpose (a wrong day silently dilutes an event book). 2027 PCE/GDP not published yet.
- Retail sales: complete. ISM: rule only, never confirmed against ISM (login wall); ISM actuals not on hand.
- Treasury bills (4/6/8/13/17/26/52 wk) not included; coupon auctions after 2026-10-22 not announced.
- Consensus for everything.
- Claims actuals around the Oct-Nov 2025 shutdown are unreliable (2025-10-16 has no first print).

## Uncertain rows (verify before using)
- Shutdown fall 2025: NFP 2025-11-20 (Sep data, source-confirmed) and 2025-12-16 (Nov data; there was no Oct jobs release); CPI 2025-10-24 and 2025-12-18 (Oct CPI never published, so no 2025-11 CPI row); PPI 2025-11-25 only, no Oct/Dec 2025 PPI rows (BLS page showed them as not listed; the 2026 page shows PPI 2026-01-14 for Nov data, which may carry the Oct data too); retail 2025-10 absent, 2025-11-25 and 2025-12-16 present; Jan/Feb 2026 BLS dates shifted (NFP 2026-02-11, CPI 2026-02-13, PPI 2026-01-30/02-27) as listed on bls.gov.
- 2026-04-03 Good Friday is also NFP day: CME equity may have run an abbreviated session 08:30-09:15 ET (as on 2023-04-07); not verified. 2023-04-07 likewise (Good Friday, NFP).
- 2025-01-09 (Carter day of mourning): EARLY_CLOSE 09:30 is a guess.
- EARLY_CLOSE times are rules (13:00 for MLK/Presidents/Memorial/Juneteenth/Jul 4/Labor/Thanksgiving; 13:15 for day-after-Thanksgiving, Dec 24, Jul 3). Not checked against the CME holiday page (it timed out). The MLK-type days are Globex trading days with no settlement (consistent with the INST work's "MLK Globex holiday sessions").
- Opex 2026-06-18 (Thu; Juneteenth is the 3rd Friday). Opex 2026-04-17 etc. normal.
- 2027 rows (FOMC tentative; CPI/NFP/PPI/retail published by agencies) are forward.

## Days with early close (observed on NQ 1-min bars through 2026-10-16, else CME rule)
- 2023-04-07 09:15 ET: Good Friday: abbreviated CME equity session (trades until 09:15 ET inc [source-confirmed (NQ bars)]
- 2023-05-29 13:00 ET: Memorial Day (NYSE closed; CME equity trades, halts 13:00 ET, no settl [source-confirmed (NQ bars)]
- 2023-06-19 13:00 ET: Juneteenth (NYSE closed; CME equity trades, halts 13:00 ET, no settlem [source-confirmed (NQ bars)]
- 2023-07-03 13:15 ET: Day before Independence Day (CME equity halts 13:15 ET) [source-confirmed (NQ bars)]
- 2023-07-04 13:00 ET: Independence Day (NYSE closed; CME equity trades, halts 13:00 ET, no s [source-confirmed (NQ bars)]
- 2023-09-04 13:00 ET: Labor Day (NYSE closed; CME equity trades, halts 13:00 ET, no settleme [source-confirmed (NQ bars)]
- 2023-11-23 13:00 ET: Thanksgiving (NYSE closed; CME equity halts 13:00 ET) [source-confirmed (NQ bars)]
- 2023-11-24 13:15 ET: Day after Thanksgiving (CME equity halts 13:15 ET) [source-confirmed (NQ bars)]
- 2024-01-15 13:00 ET: MLK Day (NYSE closed; CME equity trades, halts 13:00 ET, no settlement [source-confirmed (NQ bars)]
- 2024-02-19 13:00 ET: Presidents Day (NYSE closed; CME equity trades, halts 13:00 ET, no set [source-confirmed (NQ bars)]
- 2024-05-27 13:00 ET: Memorial Day (NYSE closed; CME equity trades, halts 13:00 ET, no settl [source-confirmed (NQ bars)]
- 2024-06-19 13:00 ET: Juneteenth (NYSE closed; CME equity trades, halts 13:00 ET, no settlem [source-confirmed (NQ bars)]
- 2024-07-03 13:15 ET: Day before Independence Day (CME equity halts 13:15 ET) [source-confirmed (NQ bars)]
- 2024-07-04 13:00 ET: Independence Day (NYSE closed; CME equity trades, halts 13:00 ET, no s [source-confirmed (NQ bars)]
- 2024-09-02 13:00 ET: Labor Day (NYSE closed; CME equity trades, halts 13:00 ET, no settleme [source-confirmed (NQ bars)]
- 2024-11-28 13:00 ET: Thanksgiving (NYSE closed; CME equity halts 13:00 ET) [source-confirmed (NQ bars)]
- 2024-11-29 13:15 ET: Day after Thanksgiving (CME equity halts 13:15 ET) [source-confirmed (NQ bars)]
- 2024-12-24 13:15 ET: Christmas Eve (CME equity halts 13:15 ET) [source-confirmed (NQ bars)]
- 2025-01-09 09:30 ET: National Day of Mourning (Carter): NYSE closed; CME equity hours uncer [source-confirmed (NQ bars)]
- 2025-01-20 13:00 ET: MLK Day (NYSE closed; CME equity trades, halts 13:00 ET, no settlement [source-confirmed (NQ bars)]
- 2025-02-17 13:00 ET: Presidents Day (NYSE closed; CME equity trades, halts 13:00 ET, no set [source-confirmed (NQ bars)]
- 2025-05-26 13:00 ET: Memorial Day (NYSE closed; CME equity trades, halts 13:00 ET, no settl [source-confirmed (NQ bars)]
- 2025-06-19 13:00 ET: Juneteenth (NYSE closed; CME equity trades, halts 13:00 ET, no settlem [source-confirmed (NQ bars)]
- 2025-07-03 13:15 ET: Day before Independence Day (CME equity halts 13:15 ET) [source-confirmed (NQ bars)]
- 2025-07-04 13:00 ET: Independence Day (NYSE closed; CME equity trades, halts 13:00 ET, no s [source-confirmed (NQ bars)]
- 2025-09-01 13:00 ET: Labor Day (NYSE closed; CME equity trades, halts 13:00 ET, no settleme [source-confirmed (NQ bars)]
- 2025-11-27 13:00 ET: Thanksgiving (NYSE closed; CME equity halts 13:00 ET) [source-confirmed (NQ bars)]
- 2025-11-28 13:15 ET: Day after Thanksgiving (CME equity halts 13:15 ET) [source-confirmed (NQ bars)]
- 2025-12-24 13:15 ET: Christmas Eve (CME equity halts 13:15 ET) [source-confirmed (NQ bars)]
- 2026-01-19 13:00 ET: MLK Day (NYSE closed; CME equity trades, halts 13:00 ET, no settlement [source-confirmed (NQ bars)]
- 2026-02-16 13:00 ET: Presidents Day (NYSE closed; CME equity trades, halts 13:00 ET, no set [source-confirmed (NQ bars)]
- 2026-04-03 09:15 ET: Good Friday: abbreviated CME equity session (trades until 09:15 ET inc [source-confirmed (NQ bars)]
- 2026-05-25 13:00 ET: Memorial Day (NYSE closed; CME equity trades, halts 13:00 ET, no settl [source-confirmed (NQ bars)]
- 2026-06-19 13:00 ET: Juneteenth (NYSE closed; CME equity trades, halts 13:00 ET, no settlem [source-confirmed (NQ bars)]
- 2026-07-03 13:00 ET: Independence Day (NYSE closed; CME equity trades, halts 13:00 ET, no s [source-confirmed (NQ bars)]
- 2026-09-07 13:00 ET: Labor Day (NYSE closed; CME equity trades, halts 13:00 ET, no settleme [source-confirmed (NQ bars)]
- 2026-11-26 13:00 ET: Thanksgiving (NYSE closed; CME equity halts 13:00 ET) [rule-derived]
- 2026-11-27 13:15 ET: Day after Thanksgiving (CME equity halts 13:15 ET) [rule-derived]
- 2026-12-24 13:15 ET: Christmas Eve (CME equity halts 13:15 ET) [rule-derived]
- 2027-01-18 13:00 ET: MLK Day (NYSE closed; CME equity trades, halts 13:00 ET, no settlement [rule-derived]
- 2027-02-15 13:00 ET: Presidents Day (NYSE closed; CME equity trades, halts 13:00 ET, no set [rule-derived]

Full closures (HOLIDAY):
- 2023-12-25: Christmas Day: CME equity clos [source-confirmed (NQ bars)]
- 2024-01-01: New Year's Day: CME equity clo [source-confirmed (NQ bars)]
- 2024-03-29: Good Friday: CME equity closed [source-confirmed (NQ bars)]
- 2024-12-25: Christmas Day: CME equity clos [source-confirmed (NQ bars)]
- 2025-01-01: New Year's Day: CME equity clo [source-confirmed (NQ bars)]
- 2025-04-18: Good Friday: CME equity closed [source-confirmed (NQ bars)]
- 2025-12-25: Christmas Day: CME equity clos [source-confirmed (NQ bars)]
- 2026-01-01: New Year's Day: CME equity clo [source-confirmed (NQ bars)]
- 2026-12-25: Christmas Day: CME equity clos [rule-derived]
- 2027-01-01: New Year's Day: CME equity clo [rule-derived]
- 2027-03-26: Good Friday: CME equity closed [rule-derived]

## Reconciliation with the D7 stack's FOMC / blackout
- `l2vast/standS/event_calendar_core.csv` (VERIFIED, fetched 2026-09-18): FOMC, NFP, CPI. Diffs vs this file over 2023-04-01..2026-12-31: FOMC decision dates identical; CPI identical; NFP identical except this file adds 2026-10-02, 2026-11-06, 2026-12-04 (core file stops earlier). No FOMC/CPI/NFP date disagrees.
- Fed-blackout (inst_dd F1/F2: second Saturday before the meeting through the statement day): recomputing with these FOMC dates reproduces the 183 BLACKOUT days in `l2vast/ds3/out/inst/F/F_class_days.csv` exactly (183 of 183, zero only-theirs, zero only-ours; that file's date universe is 2023-04-03..2026-02-06). The 2025-08-22 notation vote is not a meeting and carries no 14:00/14:30 event in either list.
- The core file has no PPI, claims, retail, PCE, GDP, ISM, auctions, opex, roll, holiday rows; this file supplies them.
