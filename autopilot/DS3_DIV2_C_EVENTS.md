# DS3_DIV2_C_EVENTS - scheduled-event intraday books, flat by 15:59 (D3D2C, T-DIVERSIFY-2 section C, 2026-10-28)

Research only; no live / execution / chart change, no download or purchase, UNTOUCHED (trade dates after 2026-02-06) never read (cut is the first statement of the data loader; stack P&L read with a label_day <= 20260206 filter). Code l2vast/ds3/code/dv2c/, outputs l2vast/ds3/out/dv2c/ (calendar_*.csv, sel_results.csv, hold_*.csv, final_results.csv, sel_trades.parquet). Preregs l2vast/ds3/prereg/DV2C_EV_MACRO|EV_FOMC|EV_CAL_prereg.md, master sha256 188f0ee8dc1c9aad8cafa546b85a5b04d54f6e7bf67970494f79566be0a8ec64 (written before any cell was scored; F = 24 / 24 / 12 = 60 cells; ledger +60). One logged HOLD look per group, taken after the SEL results file and pre-holdout text (out/dv2c/SEL_<group>.md) were written.

## 1. Verdict (read this first)

**60 cells: {'DEAD': 57, 'PASS': 1, 'CANDIDATE': 1, 'LEAD': 1}.** These are few-trades-per-year cells (24 CPI/NFP prints a year, 8 FOMC, 52 EIA, 12 month-ends, 12 opex, 4-5 rebalance days): the pooled sample is n = 5-90 trades per cell, and every cell with SEL n < 30 (all FOMC, month-end, opex and rebalance cells) is a LEAD at best by rule. Every mean below is dollars per trade at $1,000 risk (stop distance, or the window-range unit for time-exit rules), fractional lots, D3CX conservative 1-min fills, $4.84 RT (CL/ZN/GC fee grade WEAK, ceiling CANDIDATE), 95% CI over trades, MDE = 2.8 x SE, beside every mean.

**The only cell that clears every prereg gate is M0830_NQ_FADE5_60** (fade the first-5-min move after CPI/NFP 08:30, market at 08:35, stop = target = 1 x the event's as-of median 15-min range, flat at 09:30): SEL n=53, mean $+133/trade (+0.13R) CI [+12, +253], MDE 172, WF +138 (n34), SPAN2 +123 (n19), 2x-cost +127, placebo A rank 0.98, placebo B rank 0.98, HOLD (one look) +134 (n11), by year 2023: n17 +80; 2024: n24 +81; 2025: n12 +310; pooled 2023-02..2026-02-06 n=64, mean $+133 CI [+24, +242], MDE 156. **I do not call it CONFIRMED in the program sense:** (1) the mean (132) is below its own MDE (172): the test could only see an effect of +172 or more; (2) best-of-F: the zero-null test of the best cell of the group is t=2.16, one-sided p=0.018, x F=24 = 0.43 (not significant; the placebo-B rank of 0.977 is not a zero-null test, see section 5); (3) the ES sibling is positive (+76, plA 0.90, plB 0.96) but its CI includes 0 (the prereg G9 only asked for a positive sign; the D3CFA R1 standard, CI lower > 0, is NOT met); the GC copy is +88 (CI includes 0) and the ZN copy is negative (-62); (4) it is not a stack hedge: weekly correlation to the stack +0.09 but it LOSES $949 in the stack's 20 worst weeks (7 trades), and 30 of its 64 trades are on the stack's range days (+$1,790); (5) about 21 trades a year. Reading: a small, plausible 'first-5-min macro overshoot' lead (66% of trades win, 59 of 64 exit on the clock, stop/target rarely touched) that needs a fresh prereg on fresh data (2026-02-07 onward is UNTOUCHED and stays so here) before any build.

Every other family is DEAD or a LEAD, and the stack-relevant answer is plain: **no scheduled-event cell combines n >= 30, a CI above zero and a positive P&L in the stack's 20 worst weeks.** Positive worst-20-week figures exist but sit on 2-7 trades: the FOMC range-break LEADs (NQ/ES +$1.0k to +$2.0k on 2 FOMC trades, SEL n=12-13, below MDE), EIA breaks (+$0.4k..+$2.5k, 19 trades, but negative SEL means), M0830_GC_FADE5 (+$2.7k on 7 trades, DEAD, HOLD -223) and NQ/ES PRE60 (+$175/+$179, 7 trades, CI includes 0). The PASS cell loses $949 in those weeks.

### 1a. Verdict table per event family

| family (instruments) | cells | PASS | CANDIDATE | LEAD | DEAD | what the family says |
|---|---|---|---|---|---|---|
| CPI + NFP 08:30 (NQ, ES, ZN, GC) | 24 | 1 | 1 | 0 | 22 | 24 cells. First-minute range BREAKS lose on every instrument at both brackets (NQ -143..-11, ES -103..+100, ZN -204..-94, GC -275..-109 $/trade; ZN and GC significantly below zero and below the random-sign placebo, i.e. the break is faded by the market, cost-inclusive). FADE5 is the only positive rule (NQ +133, ES +76, GC +88, ZN -62). PRE60 (long, 07:30-08:30) NQ +73 / ES +69 (CI includes 0, plB 0.87/0.85), ZN -36, GC -104 (significant against). |
| FOMC 14:00 statement (NQ, ES, ZN, GC) | 24 | 0 | 0 | 1 | 23 | 24 cells, SEL n = 8-16. NQ/ES range breaks are positive in all 8 cells (+195..+319 $/trade, plB 0.97-1.00, plA 0.84-0.94, HOLD n=4-5 positive) but n=12-13 and CI includes 0: LEADs at most; ES BRK1.5_120 is the only LEAD that survives the core gates. FADE5 and PRE60 are negative on every instrument (ZN/GC PRE60 significant). ZN/GC are n=8-11: nothing. |
| EIA crude Wed 10:30 (CL) | 6 | 0 | 0 | 0 | 6 | 6 cells, SEL n = 84-90 (the best-powered family, MDE 140-260 $). All six are negative or flat (-130..-30), FADE5 -129 (plB 0.04). No edge; the earlier T3.7b4 EIA sleeve on NQ was DEAD too. |
| Month-end 15:00-15:59, direction inverse of month-to-date (NQ, ES) | 2 | 0 | 0 | 0 | 2 | 2 cells, n=28: NQ -259, ES -202 (CI spans zero; HOLD n=7 mixed). Inverse-of-MTD flow is not there; the mirror (follow MTD) is the same trade with the opposite sign and is NOT scored (post-hoc). |
| Opex Friday 14:00 pin fade (NQ, ES) | 2 | 0 | 0 | 0 | 2 | 2 cells, n=5 and 10 (the distance filter leaves few days). Nothing measurable. |
| Rebalance-day MOC continuation (NQ, ES) | 2 | 0 | 0 | 0 | 2 | 2 cells, n=13 each (S&P quarterly + Russell). NQ +233, ES +30, CI spans zero, HOLD n=2. Nothing measurable. |

Not scored (calendar, see section 2): ISM 10:00 and the FOMC press conference 14:30 (volume signature not confirmed); PPI, retail sales, GDP, Treasury 10y/30y auctions, NatGas storage (NEEDS CSV).

### 1b. Prior ledger items cited, not re-run

- DS3_TB8 (D3Q): CPI / NFP / FOMC first-move N-point breakouts on NQ with the DS2 60/60 bracket to 16:55 and their fades, 20 cells, ALL DEAD; n = 20-32 WF trades, per-trade MDE $5.7-7.3k at 10 lots; FOMC fade control +2.6k with n=21 was noise. My M0830/FOMC cells are different objects (first-minute range break with an event-scaled symmetric bracket and a 60/120-min clock exit; fade of the first 5 min with a 1R bracket; pre-event long) and use the dollar-risk unit, but the NQ FOMC break LEADs here sit opposite to TB8's negative FOMC continuation cells (TB8_FOMC_N20 -2.8k): one more reason they stay LEAD.
- LEADERBOARD T3.7b4 EIA_h30 / EIA_h60 (NQ EIA sleeves, DEAD) and T3.6b1 FOMC_P1_x1400 / FOMC_P2_e0930 (NQ FOMC sleeves, DEAD); DS3_TF TF1_FOMC_NY (FOMC-day NY entry block on the proxy trend book, CANDIDATE filter, paired CI includes 0, MDE 48 pts) and TF2_CPI_LON (DEAD). ES TOM / opex positional books: DEAD (DS3_CENSUS T-F row). DS3_DIV_1_MAPS event profiles (EIA, NFP 5-min follow-through +1.4..+3.9 bps, t < 1) were the descriptive basis; no cell here was selected from them.

## 2. The event calendar (RECONSTRUCTED) and its confirmation

**Label: RECONSTRUCTED.** Sources: CPI / NFP / FOMC statement dates = l2vast/standS/event_calendar_core.csv (fetched 2026-09-18 from bls.gov / federalreserve.gov, tier VERIFIED, already used by D3Q TB8 and D3X); FOMC press conference 14:30 = the same FOMC dates; ISM manufacturing = first trading day of the month 10:00 (rule); EIA crude = every Wednesday 10:30 plus the Thursday of a week whose Monday has no bars (holiday shift; rule); opex = third Friday (Thursday if the Friday has no RTH bars); S&P quarterly rebalance = third Friday of Mar/Jun/Sep/Dec; Russell reconstitution = fourth Friday of June; month-end / quarter-end = last trading day with RTH bars. Window 2023-02-01..2026-02-06 (the CSV starts 2023-02).

**Confirmation test (fixed a priori, volume only, no prices):** release-minute ratio = max(v[t0], v[t0+1]) / median(v[t0-30 .. t0-3]) >= 3.0 (>= 2.0 for the presser) and the two minutes before t0 each <= 0.5 x the peak (a step-up exactly at the release, sustained volume afterwards allowed); closing events: the session ran to the 16:00 close (v[15:59] / median(v[15:30..15:49]) >= 2.5; this only rejects early-close / missing-bar days). The same statistic on the same clock on every non-event weekday gives the false-positive rate. Unconfirmed dates are DROPPED per instrument.

| event | clock | instrument | listed | in session | confirmed | confirm rate | median ratio | control false-positive rate (non-event weekdays) |
|---|---|---|---|---|---|---|---|---|
| CPI | 08:30 | ES | 35 | 35 | 35 | 100% | 25.8 | 40.1% (n499) |
| CPI | 08:30 | GC | 35 | 35 | 35 | 100% | 24.2 | 42.5% (n499) |
| CPI | 08:30 | NQ | 35 | 35 | 35 | 100% | 24.8 | 43.5% (n499) |
| CPI | 08:30 | ZN | 35 | 35 | 35 | 100% | 23.2 | 51.9% (n499) |
| EIA | 10:30 | CL | 174 | 169 | 119 | 68% | 4.6 | 7.6% (n499) |
| FOMC | 14:00 | ES | 25 | 25 | 23 | 92% | 8.8 | 6.2% (n499) |
| FOMC | 14:00 | GC | 25 | 25 | 24 | 96% | 19.8 | 5.0% (n499) |
| FOMC | 14:00 | NQ | 25 | 25 | 21 | 84% | 10.9 | 5.2% (n499) |
| FOMC | 14:00 | ZN | 25 | 25 | 23 | 92% | 18.7 | 25.5% (n499) |
| FOMC_PRESS | 14:30 | ES | 25 | 25 | 6 | 24% | 1.6 | 11.4% (n499) |
| FOMC_PRESS | 14:30 | NQ | 25 | 25 | 6 | 24% | 1.5 | 11.4% (n499) |
| ISM | 10:00 | ES | 37 | 37 | 4 | 11% | 1.9 | 3.8% (n499) |
| ISM | 10:00 | NQ | 37 | 37 | 1 | 3% | 1.5 | 2.6% (n499) |
| MONTHEND | close | ES | 37 | 37 | 37 | 100% | 32.5 | 100.0% (n674) |
| MONTHEND | close | NQ | 37 | 37 | 37 | 100% | 12.8 | 99.9% (n674) |
| NFP | 08:30 | ES | 35 | 33 | 33 | 94% | 21.4 | 40.1% (n499) |
| NFP | 08:30 | GC | 35 | 33 | 33 | 94% | 26.1 | 42.5% (n499) |
| NFP | 08:30 | NQ | 35 | 33 | 33 | 94% | 20.8 | 43.5% (n499) |
| NFP | 08:30 | ZN | 35 | 33 | 33 | 94% | 24.0 | 51.9% (n499) |
| OPEX | close | ES | 36 | 36 | 36 | 100% | 20.8 | 100.0% (n674) |
| OPEX | close | NQ | 36 | 36 | 36 | 100% | 10.5 | 99.9% (n674) |
| QTREND | close | ES | 12 | 12 | 12 | 100% | 30.6 | - |
| QTREND | close | NQ | 12 | 12 | 12 | 100% | 12.4 | - |
| REBAL | close | ES | 15 | 15 | 15 | 100% | 22.5 | 100.0% (n674) |
| REBAL | close | NQ | 15 | 15 | 15 | 100% | 10.6 | 99.9% (n674) |

Reading: CPI 35/35, NFP 33/35, FOMC statement 21-24 of 25 are confirmed; the 08:30 control rate of 40-50% is other 08:30 releases (jobless claims every Thursday, PPI, retail sales), so the signature proves that SOME release happened at 08:30, not that it was CPI; the date comes from the verified CSV. EIA crude confirms on CL for 119 of 174 candidate Wednesdays/Thursdays (68%, false-positive 8%): the muted-reaction and holiday-shifted weeks drop out. **ISM 10:00 failed (NQ 1/37, ES 4/37; the 10:00 minute carries no step-up above the opening-hour flow) and the FOMC press conference 14:30 failed (6/25 vs control 11%): neither is scored.** Month-end / opex / rebalance rows only certify that the session ran to the close (MOC-volume concentration, descriptive: calendar_close_conc.csv, NQ event days 2.9-3.5 vs 2.8 control).

**Dates the signature does not confirm (dropped from scoring on that instrument):**
- FOMC: 2024-07-31 [NQ,ES]; 2025-05-07 [NQ,ES,ZN]; 2025-06-18 [NQ]; 2025-07-30 [NQ,ZN,GC]
- NFP: 2023-04-07 [NQ,ES,ZN,GC]; 2025-07-03 [NQ,ES,ZN,GC]   (2023-04-07 Good Friday and 2025-07-03 early close: no RTH session, NFP released into a closed/short equity session)
- EIA crude (55 of 174 dropped, CL): 2023-02-23, 2023-03-01, 2023-03-15, 2023-04-12, 2023-04-26, 2023-05-03, 2023-05-31, 2023-06-01, 2023-06-21, 2023-06-22, 2023-07-05, 2023-07-06, 2023-09-06, 2023-09-07, 2023-10-11, 2023-11-01, 2023-11-08, 2023-12-06, 2023-12-27, 2023-12-28, 2024-01-03, 2024-01-04, 2024-01-17, 2024-01-18, 2024-01-31, 2024-02-21, 2024-02-22, 2024-05-30, 2024-06-19, 2024-07-17, 2024-09-04, 2024-09-05, 2024-10-16, 2024-11-13, 2024-12-25, 2025-01-01, 2025-01-15, 2025-01-22, 2025-01-23, 2025-02-20, 2025-03-05, 2025-04-09, 2025-04-16, 2025-04-23, 2025-05-29, 2025-06-18, 2025-08-06, 2025-09-03, 2025-09-04, 2025-10-15, 2025-11-12, 2026-01-14, 2026-01-21, 2026-01-22, 2026-01-28
- ISM 10:00 (all 37 dates, NQ 36 unconfirmed / ES 33 unconfirmed) and FOMC presser 14:30 (NQ/ES 19 of 25 unconfirmed): whole event types dropped; listing in calendar_confirmation.csv.

**NEEDS (the box cannot assemble these date lists; user supplies a CSV with columns event,date_et,time_et):** PPI (08:30), retail sales (08:30), GDP advance/second/third (08:30), Treasury 10-year and 30-year auctions (13:00; 3-/10-/30-yr dates are not derivable from a fixed rule), NatGas storage Thu 10:30 (rule is simple, but NG is outside the scored instrument set NQ/ES/ZN/CL/GC; NG.npz exists raw, no adjusted series), MSCI semi-annual/quarterly review effective dates (month-end subset only, not separable). Jobless claims (Thursday 08:30) are not asked for and not in the calendar; they remain in the placebo-B pool and in the 08:30 control rate (disclosed).

Event counts used (confirmed, before the 4-event scale warm-up): M0830 68 on every instrument, FOMC NQ 21 / ES 23 / ZN 23 / GC 24, EIA CL 119, month-end 37, opex 36, rebalance 15. SEL (<= 2025-06-30) after warm-up: M0830 40-53, FOMC 8-16, EIA 84-90, ME 28, OPEX 5-10, MOC 13. The scale R (as-of expanding median of the 15-min post-release range) at the end of the sample: NQ CPI/NFP 138 pts, ES 30, ZN 0.65 (41 ticks), GC 19 pts, NQ FOMC 91, ES 25, ZN 0.36, GC 13, CL EIA 0.51 ($0.51).

## 3. Cells, rules and gates (frozen in the prereg; summary)

Per event type 6 cells: BRK1.0_60, BRK1.0_120, BRK1.5_60, BRK1.5_120 (stop-entry one tick beyond the high/low of the release-minute bar, valid bars t0+1..t0+14, OCO, stop = target = k x R, flat at t0+60/120 capped 15:59), FADE5_60 (against the first-5-min move, market at t0+5, 1R bracket, flat t0+60), PRE60 (long, t0-60 to t0-1). Calendar flows: month-end FLOW (side = -sign(price - last prior-month close at 14:59), 15:00-15:59), opex PINFADE (toward the nearest 100 NQ / 25 ES strike at 14:00 if the distance >= the median 14:00-14:14 range; target strike+1 tick, stop equal distance, flat 15:59), rebalance MOCCONT (sign of the 14:59-15:49 move, 15:50-15:59). Gates: G1 SEL n>=30; G2 pooled CI>0; G3 WF and SPAN2 means >0; G4/G5 placebo A (random sign, same bars) and B (same rule, random clock +/-15..150 min on non-event days) ranks >= 0.95 (300 draws); G6 2x-cost mean >0; G7 no year > 60% of the gain; G8 HOLD mean >0; G9 sibling (NQ<->ES) same sign. PASS = G1-G9 and a non-WEAK fee grade; CANDIDATE = mean>0, G3, G6, G8 and both placebo ranks >= 0.90 with another gate failed; LEAD when n<30 is the failed gate; DEAD otherwise. Mechanism and predicted effect per cell: in the three prereg files (predicted net = gross hypothesis minus cost, 0 for breaks/fades, +0.03R for FOMC pre-drift, month-end flow and pin; cost per trade 0.008-0.09R; per-trade MDE 0.35-0.75R from n).

## 4. All 60 cells (nothing hidden; sorted by group; $ per trade at $1,000 risk)

SEL = events to 2025-06-30. CI is the 95% interval of the SEL mean, MDE = 2.8 x SE. WF = 2024-02..2025-06, S2 = 2023-02..2024-01, HOLD = 2025-07..2026-02-06 (one look per group). corr = weekly correlation to the live stack (149 weeks 2023-04..2026-02, mostly zero weeks), W20 = cell $ in the stack's 20 worst weeks of that span (n trades in brackets), LS = cell $ entered in the stack's loss half-hour slots (recomputed on the truncated span: 01:00, 01:30, 03:30, 05:00, 05:30, 08:00, 08:30, 11:30, 14:30, 16:30, 23:30), RD = cell $ on the stack's (ex-post) range days.

| cell | verdict | failed gates | SEL n | mean [CI] | MDE | WF | S2 | 2x | plA | plB | HOLD n / mean | pooled n / mean [CI] / MDE | corr | W20 (n) | LS | RD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M0830_NQ_BRK1.0_60 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,HOLD,sib | 43 | -143 [-285,-2] | 202 | -158 | -118 | -150 | 0.02 | 0.05 | 11 / -69 | 54 / -128 [-251,-5] / 175 | -0.02 | +630 (6) | -6913 | -1145 |
| M0830_NQ_BRK1.0_120 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,HOLD | 43 | -126 [-368,+116] | 346 | -119 | -138 | -132 | 0.19 | 0.06 | 11 / -181 | 54 / -137 [-348,+73] / 301 | +0.06 | -2675 (6) | -7417 | -2185 |
| M0830_NQ_BRK1.5_60 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,HOLD,sib | 43 | -99 [-201,+3] | 146 | -111 | -79 | -104 | 0.03 | 0.11 | 11 / -46 | 54 / -88 [-176,-1] / 125 | -0.02 | +420 (6) | -4772 | -1097 |
| M0830_NQ_BRK1.5_120 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,HOLD | 43 | -11 [-178,+155] | 238 | +30 | -81 | -16 | 0.42 | 0.44 | 11 / -95 | 54 / -28 [-176,+119] / 211 | +0.04 | -184 (6) | -1532 | -1491 |
| M0830_NQ_FADE5_60 | PASS | - | 53 | +133 [+12,+253] | 172 | +138 | +123 | +127 | 0.98 | 0.98 | 11 / +134 | 64 / +133 [+24,+242] / 156 | +0.09 | -949 (7) | +8505 | +1790 |
| M0830_NQ_PRE60 | DEAD | CI,plB | 53 | +73 [-3,+150] | 109 | +89 | +46 | +68 | 0.99 | 0.87 | 11 / +69 | 64 / +73 [+8,+138] / 93 | +0.01 | +175 (7) | +0 | +1187 |
| M0830_ES_BRK1.0_60 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,HOLD,sib | 41 | -103 [-249,+43] | 209 | -99 | -109 | -129 | 0.16 | 0.08 | 10 / -129 | 51 / -108 [-234,+18] / 180 | -0.05 | -691 (7) | -5500 | -1135 |
| M0830_ES_BRK1.0_120 | DEAD | CI,WF/SPAN2,plA,plB,yr,HOLD,sib | 41 | +22 [-221,+265] | 347 | +38 | -6 | +2 | 0.61 | 0.74 | 10 / -322 | 51 / -46 [-266,+175] / 315 | +0.04 | -2556 (7) | -2332 | +2991 |
| M0830_ES_BRK1.5_60 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,HOLD,sib | 41 | -71 [-165,+23] | 134 | -72 | -70 | -89 | 0.10 | 0.10 | 10 / -86 | 51 / -74 [-155,+7] / 116 | -0.04 | -460 (7) | -3770 | -1360 |
| M0830_ES_BRK1.5_120 | DEAD | CI,WF/SPAN2,plA,plB,HOLD,sib | 41 | +100 [-75,+274] | 249 | +168 | -18 | +83 | 0.88 | 0.94 | 10 / -344 | 51 / +13 [-154,+180] / 238 | +0.02 | -1385 (7) | +653 | +1083 |
| M0830_ES_FADE5_60 | CANDIDATE | CI,plA,yr | 53 | +76 [-51,+204] | 183 | +67 | +93 | +58 | 0.90 | 0.96 | 11 / +83 | 64 / +78 [-35,+191] / 162 | +0.13 | -573 (7) | +4967 | -293 |
| M0830_ES_PRE60 | DEAD | CI,plB,yr | 53 | +69 [-15,+153] | 120 | +106 | +3 | +49 | 0.99 | 0.85 | 11 / +12 | 64 / +59 [-13,+132] / 104 | -0.01 | +179 (7) | +0 | +1094 |
| M0830_ZN_BRK1.0_60 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,sib,feeWEAK | 40 | -142 [-241,-42] | 142 | -174 | -66 | -214 | 0.03 | 0.05 | 6 / +28 | 46 / -120 [-216,-23] / 138 | +0.09 | -1407 (5) | -5499 | -3531 |
| M0830_ZN_BRK1.0_120 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,sib,feeWEAK | 40 | -204 [-331,-76] | 182 | -185 | -248 | -279 | 0.00 | 0.00 | 6 / +154 | 46 / -157 [-281,-33] / 178 | +0.08 | -2052 (5) | -7223 | -4453 |
| M0830_ZN_BRK1.5_60 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,sib,feeWEAK | 40 | -94 [-161,-28] | 95 | -116 | -44 | -143 | 0.04 | 0.05 | 6 / +19 | 46 / -80 [-144,-15] / 92 | +0.09 | -938 (5) | -3666 | -2354 |
| M0830_ZN_BRK1.5_120 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,sib,feeWEAK | 40 | -137 [-226,-48] | 127 | -111 | -199 | -185 | 0.01 | 0.01 | 6 / +101 | 46 / -106 [-192,-20] / 123 | +0.09 | -1432 (5) | -4880 | -3365 |
| M0830_ZN_FADE5_60 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,HOLD,sib,feeWEAK | 51 | -62 [-144,+20] | 117 | -60 | -65 | -112 | 0.39 | 0.28 | 11 / -16 | 62 / -54 [-127,+19] / 104 | +0.08 | -858 (7) | -3337 | +592 |
| M0830_ZN_PRE60 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,HOLD,sib,feeWEAK | 53 | -36 [-78,+7] | 61 | -83 | +49 | -86 | 0.76 | 0.74 | 11 / -37 | 64 / -36 [-73,+1] / 53 | +0.03 | -272 (7) | +0 | -1048 |
| M0830_GC_BRK1.0_60 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,sib,feeWEAK | 47 | -197 [-361,-32] | 235 | -246 | -100 | -216 | 0.01 | 0.00 | 10 / +167 | 57 / -133 [-293,+28] / 229 | +0.12 | -2264 (6) | -7572 | -6784 |
| M0830_GC_BRK1.0_120 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,sib,feeWEAK | 47 | -275 [-462,-88] | 267 | -320 | -189 | -291 | 0.00 | 0.00 | 10 / +292 | 57 / -176 [-367,+16] / 274 | +0.20 | -2968 (6) | -10022 | -7220 |
| M0830_GC_BRK1.5_60 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,sib,feeWEAK | 47 | -109 [-217,-0] | 155 | -125 | -78 | -121 | 0.04 | 0.00 | 10 / +169 | 57 / -60 [-168,+48] / 154 | +0.14 | -1402 (6) | -3430 | -2922 |
| M0830_GC_BRK1.5_120 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,sib,feeWEAK | 47 | -164 [-309,-19] | 207 | -183 | -129 | -176 | 0.01 | 0.00 | 10 / +145 | 57 / -110 [-253,+33] / 204 | +0.15 | -2022 (6) | -6266 | -4695 |
| M0830_GC_FADE5_60 | DEAD | CI,plA,yr,HOLD,sib,feeWEAK | 53 | +88 [-55,+231] | 204 | +113 | +44 | +76 | 0.91 | 0.97 | 11 / -223 | 64 / +35 [-106,+176] / 201 | -0.09 | +2748 (7) | +2219 | +1656 |
| M0830_GC_PRE60 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,sib,feeWEAK | 53 | -104 [-186,-21] | 118 | -158 | -5 | -117 | 0.00 | 0.05 | 11 / +283 | 64 / -37 [-122,+48] / 122 | +0.09 | -190 (7) | +0 | -119 |
| FOMC_NQ_BRK1.0_60 | DEAD | n<30,CI,WF/SPAN2,plA | 12 | +315 [-142,+773] | 653 | +562 | -30 | +310 | 0.92 | 1.00 | 4 / +216 | 16 / +291 [-110,+692] / 573 | +0.11 | +1041 (2) | +0 | +5195 |
| FOMC_NQ_BRK1.0_120 | DEAD | n<30,CI,plA | 12 | +319 [-191,+828] | 728 | +523 | +33 | +314 | 0.86 | 0.99 | 4 / +245 | 16 / +300 [-132,+733] / 618 | +0.07 | +1996 (2) | +0 | +5166 |
| FOMC_NQ_BRK1.5_60 | DEAD | n<30,CI,WF/SPAN2,plA | 12 | +241 [-174,+657] | 594 | +428 | -20 | +236 | 0.84 | 0.98 | 4 / +657 | 16 / +345 [+5,+685] / 486 | +0.09 | +1027 (2) | +0 | +4547 |
| FOMC_NQ_BRK1.5_120 | DEAD | n<30,CI,plA | 12 | +274 [-200,+748] | 677 | +461 | +11 | +269 | 0.89 | 0.99 | 4 / +748 | 16 / +392 [+9,+775] / 547 | +0.06 | +1789 (2) | +0 | +4565 |
| FOMC_NQ_FADE5_60 | DEAD | n<30,CI,WF/SPAN2,plA,plB,2x,yr,HOLD,sib | 13 | -81 [-550,+388] | 670 | -127 | -8 | -88 | 0.42 | 0.30 | 4 / -235 | 17 / -118 [-526,+291] / 584 | -0.05 | -1093 (2) | +0 | -1375 |
| FOMC_NQ_PRE60 | DEAD | n<30,CI,WF/SPAN2,plA,plB,2x,yr,sib | 13 | -73 [-210,+64] | 196 | -142 | +38 | -80 | 0.22 | 0.29 | 4 / +105 | 17 / -31 [-182,+121] / 216 | -0.02 | +265 (2) | +0 | +448 |
| FOMC_ES_BRK1.0_60 | DEAD | n<30,CI,WF/SPAN2,plA | 13 | +211 [-257,+679] | 668 | +355 | -19 | +195 | 0.88 | 0.97 | 5 / +375 | 18 / +256 [-137,+650] / 562 | +0.10 | +1069 (2) | +0 | +3182 |
| FOMC_ES_BRK1.0_120 | DEAD | n<30,CI,plA | 13 | +195 [-325,+715] | 743 | +297 | +33 | +182 | 0.90 | 0.97 | 5 / +334 | 18 / +234 [-195,+662] / 612 | +0.06 | +1994 (2) | +0 | +2851 |
| FOMC_ES_BRK1.5_60 | DEAD | n<30,CI,plA | 13 | +244 [-123,+610] | 523 | +292 | +166 | +221 | 0.87 | 1.00 | 5 / +304 | 18 / +260 [-63,+584] / 462 | +0.09 | +1046 (2) | +0 | +2981 |
| FOMC_ES_BRK1.5_120 | LEAD | n<30,CI,plA | 13 | +308 [-123,+740] | 616 | +256 | +392 | +294 | 0.94 | 0.99 | 5 / +266 | 18 / +296 [-68,+661] / 520 | +0.04 | +1697 (2) | +0 | +2442 |
| FOMC_ES_FADE5_60 | DEAD | n<30,CI,WF/SPAN2,plA,plB,2x,yr,HOLD,sib | 14 | -243 [-622,+135] | 541 | -155 | -403 | -263 | 0.13 | 0.02 | 5 / -423 | 19 / -291 [-629,+47] / 483 | -0.09 | -1145 (2) | +0 | -3146 |
| FOMC_ES_PRE60 | DEAD | n<30,CI,WF/SPAN2,plA,plB,2x,yr,sib | 14 | -145 [-270,-20] | 178 | -208 | -31 | -168 | 0.03 | 0.09 | 5 / +4 | 19 / -106 [-227,+16] / 174 | -0.03 | +34 (2) | +0 | -395 |
| FOMC_ZN_BRK1.0_60 | DEAD | n<30,CI,WF/SPAN2,plA,2x,yr,HOLD,sib,feeWEAK | 8 | +59 [-501,+619] | 800 | -11 | +268 | -30 | 0.70 | 1.00 | 3 / -320 | 11 / -45 [-507,+418] / 660 | +0.01 | +144 (2) | +0 | -529 |
| FOMC_ZN_BRK1.0_120 | DEAD | n<30,CI,WF/SPAN2,plA,2x,yr,HOLD,sib,feeWEAK | 8 | +21 [-528,+571] | 786 | -154 | +548 | -67 | 0.61 | 0.99 | 3 / -285 | 11 / -62 [-527,+403] / 664 | +0.02 | +97 (2) | +0 | -1066 |
| FOMC_ZN_BRK1.5_60 | DEAD | n<30,CI,plA,yr,HOLD,sib,feeWEAK | 8 | +97 [-221,+415] | 454 | +92 | +112 | +16 | 0.72 | 1.00 | 3 / -324 | 11 / -18 [-332,+296] / 449 | +0.01 | +96 (2) | +0 | -686 |
| FOMC_ZN_BRK1.5_120 | DEAD | n<30,CI,plA,yr,HOLD,sib,feeWEAK | 8 | +128 [-199,+454] | 467 | +44 | +378 | +47 | 0.74 | 1.00 | 3 / -301 | 11 / +11 [-318,+339] / 469 | +0.02 | +64 (2) | +0 | -1044 |
| FOMC_ZN_FADE5_60 | DEAD | n<30,CI,WF/SPAN2,plA,plB,2x,yr,sib,feeWEAK | 15 | -288 [-547,-28] | 371 | -278 | -306 | -371 | 0.07 | 0.00 | 3 / +19 | 18 / -237 [-503,+30] / 381 | -0.08 | -311 (2) | +0 | -2256 |
| FOMC_ZN_PRE60 | DEAD | n<30,CI,WF/SPAN2,plA,plB,2x,yr,HOLD,sib,feeWEAK | 15 | -126 [-184,-67] | 84 | -144 | -88 | -209 | 0.09 | 0.19 | 4 / -189 | 19 / -139 [-191,-87] / 75 | -0.11 | -219 (2) | +0 | -1208 |
| FOMC_GC_BRK1.0_60 | DEAD | n<30,CI,WF/SPAN2,plA,plB,yr,HOLD,sib,feeWEAK | 11 | +64 [-470,+598] | 763 | -28 | +479 | +47 | 0.58 | 0.89 | 4 / -1020 | 15 / -225 [-686,+236] / 659 | -0.10 | +959 (2) | +0 | -4108 |
| FOMC_GC_BRK1.0_120 | DEAD | n<30,CI,WF/SPAN2,plA,plB,yr,HOLD,sib,feeWEAK | 11 | +84 [-492,+659] | 822 | -61 | +734 | +69 | 0.59 | 0.84 | 4 / -1020 | 15 / -211 [-699,+278] / 698 | -0.11 | +1469 (2) | +0 | -3560 |
| FOMC_GC_BRK1.5_60 | DEAD | n<30,CI,plA,yr,HOLD,sib,feeWEAK | 11 | +158 [-300,+617] | 655 | +85 | +486 | +146 | 0.80 | 1.00 | 4 / -1014 | 15 / -154 [-583,+275] / 613 | -0.07 | +973 (2) | +0 | -3136 |
| FOMC_GC_BRK1.5_120 | DEAD | n<30,CI,WF/SPAN2,plA,plB,yr,HOLD,sib,feeWEAK | 11 | +46 [-501,+593] | 781 | -89 | +656 | +35 | 0.59 | 0.84 | 4 / -1014 | 15 / -236 [-702,+229] / 665 | -0.11 | +1313 (2) | +0 | -3812 |
| FOMC_GC_FADE5_60 | DEAD | n<30,CI,WF/SPAN2,plA,plB,2x,yr,HOLD,sib,feeWEAK | 16 | -207 [-586,+172] | 542 | -195 | -233 | -227 | 0.18 | 0.00 | 4 / -516 | 20 / -269 [-622,+84] / 505 | +0.06 | -1064 (2) | +0 | -1098 |
| FOMC_GC_PRE60 | DEAD | n<30,CI,WF/SPAN2,plA,plB,2x,yr,HOLD,sib,feeWEAK | 16 | -191 [-289,-93] | 140 | -240 | -84 | -212 | 0.00 | 0.05 | 4 / -366 | 20 / -226 [-366,-86] / 200 | -0.03 | -397 (2) | +0 | -2279 |
| EIA_CL_BRK1.0_60 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,sib,feeWEAK | 84 | -90 [-243,+63] | 219 | -12 | -229 | -139 | 0.24 | 0.44 | 24 / +42 | 108 / -60 [-189,+68] / 184 | -0.01 | +949 (19) | +0 | +8 |
| EIA_CL_BRK1.0_120 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,HOLD,sib,feeWEAK | 84 | -100 [-281,+82] | 259 | -85 | -125 | -138 | 0.22 | 0.30 | 24 / -148 | 108 / -110 [-266,+45] / 222 | +0.07 | -1672 (19) | +0 | -2614 |
| EIA_CL_BRK1.5_60 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,sib,feeWEAK | 84 | -30 [-143,+82] | 161 | +29 | -137 | -75 | 0.53 | 0.49 | 24 / +5 | 108 / -23 [-114,+69] / 131 | -0.10 | +2517 (19) | +0 | +689 |
| EIA_CL_BRK1.5_120 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,HOLD,sib,feeWEAK | 84 | -58 [-204,+88] | 209 | -63 | -49 | -100 | 0.38 | 0.26 | 24 / -100 | 108 / -67 [-191,+56] / 176 | -0.01 | +1251 (19) | +0 | -554 |
| EIA_CL_FADE5_60 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,HOLD,sib,feeWEAK | 90 | -129 [-273,+15] | 206 | -239 | +69 | -164 | 0.16 | 0.04 | 25 / -8 | 115 / -103 [-226,+20] / 176 | +0.01 | -2726 (19) | +0 | -5871 |
| EIA_CL_PRE60 | DEAD | CI,WF/SPAN2,plA,plB,2x,yr,HOLD,sib,feeWEAK | 90 | -55 [-165,+55] | 157 | +29 | -207 | -93 | 0.45 | 0.34 | 25 / -0 | 115 / -43 [-134,+48] / 130 | +0.18 | -3229 (19) | +0 | -1680 |
| ME_NQ_FLOW | DEAD | n<30,CI,WF/SPAN2,plA,plB,2x,yr,sib | 28 | -259 [-803,+284] | 776 | -486 | +43 | -271 | 0.17 | 0.19 | 7 / +80 | 35 / -191 [-641,+258] / 642 | +0.07 | -4055 (6) | +0 | -10123 |
| ME_ES_FLOW | DEAD | n<30,CI,WF/SPAN2,plA,plB,2x,yr,HOLD,sib | 28 | -202 [-762,+359] | 801 | -171 | -242 | -239 | 0.33 | 0.31 | 7 / -31 | 35 / -168 [-636,+301] / 669 | +0.10 | -4241 (6) | +0 | -10414 |
| OPEX_NQ_PINFADE | DEAD | n<30,CI,WF/SPAN2,plA,plB,2x,yr | 5 | -107 [-1008,+794] | 1287 | -348 | +254 | -120 | 0.40 | 0.42 | 2 / +792 | 7 / +150 [-557,+857] / 1010 | +0.02 | +0 (0) | +0 | -1504 |
| OPEX_ES_PINFADE | DEAD | n<30,CI,WF/SPAN2,plA,plB,2x,yr,sib | 10 | +34 [-575,+643] | 871 | -188 | +367 | -7 | 0.67 | 0.75 | 5 / +261 | 15 / +110 [-368,+587] / 682 | +0.02 | +1056 (2) | +0 | -2111 |
| MOC_NQ_MOCCONT | DEAD | n<30,CI,plA,plB,yr | 13 | +233 [-283,+750] | 738 | +290 | +143 | +214 | 0.85 | 0.64 | 2 / +52 | 15 / +209 [-241,+660] / 644 | +0.04 | +292 (1) | +0 | -733 |
| MOC_ES_MOCCONT | DEAD | n<30,CI,WF/SPAN2,plA,plB,2x,yr,HOLD | 13 | +30 [-322,+382] | 503 | +133 | -136 | -32 | 0.67 | 0.54 | 2 / -335 | 15 / -19 [-329,+292] / 444 | +0.03 | +128 (1) | +0 | +329 |

By-year SEL means (n, $/trade): 
- M0830_NQ_BRK1.0_60: 2023: n14 -37; 2024: n21 -128; 2025: n8 -368; HOLD n11 -69
- M0830_NQ_BRK1.0_120: 2023: n14 -112; 2024: n21 -140; 2025: n8 -114; HOLD n11 -181
- M0830_NQ_BRK1.5_60: 2023: n14 -25; 2024: n21 -89; 2025: n8 -257; HOLD n11 -46
- M0830_NQ_BRK1.5_120: 2023: n14 -38; 2024: n21 -6; 2025: n8 +23; HOLD n11 -95
- M0830_NQ_FADE5_60: 2023: n17 +80; 2024: n24 +81; 2025: n12 +310; HOLD n11 +134
- M0830_NQ_PRE60: 2023: n17 +37; 2024: n24 +42; 2025: n12 +188; HOLD n11 +69
- M0830_ES_BRK1.0_60: 2023: n13 +2; 2024: n20 -135; 2025: n8 -192; HOLD n10 -129
- M0830_ES_BRK1.0_120: 2023: n13 +45; 2024: n20 +52; 2025: n8 -91; HOLD n10 -322
- M0830_ES_BRK1.5_60: 2023: n13 +1; 2024: n20 -101; 2025: n8 -113; HOLD n10 -86
- M0830_ES_BRK1.5_120: 2023: n13 +39; 2024: n20 +87; 2025: n8 +230; HOLD n10 -344
- M0830_ES_FADE5_60: 2023: n17 +38; 2024: n24 +12; 2025: n12 +260; HOLD n11 +83
- M0830_ES_PRE60: 2023: n17 -3; 2024: n24 +46; 2025: n12 +215; HOLD n11 +12
- M0830_ZN_BRK1.0_60: 2023: n10 +23; 2024: n19 -250; 2025: n11 -105; HOLD n6 +28
- M0830_ZN_BRK1.0_120: 2023: n10 -160; 2024: n19 -333; 2025: n11 -19; HOLD n6 +154
- M0830_ZN_BRK1.5_60: 2023: n10 +15; 2024: n19 -167; 2025: n11 -70; HOLD n6 +19
- M0830_ZN_BRK1.5_120: 2023: n10 -113; 2024: n19 -222; 2025: n11 -13; HOLD n6 +101
- M0830_ZN_FADE5_60: 2023: n17 -82; 2024: n23 -20; 2025: n11 -120; HOLD n11 -16
- M0830_ZN_PRE60: 2023: n17 +57; 2024: n24 -56; 2025: n12 -125; HOLD n11 -37
- M0830_GC_BRK1.0_60: 2023: n14 -29; 2024: n21 -54; 2025: n12 -642; HOLD n10 +167
- M0830_GC_BRK1.0_120: 2023: n14 -125; 2024: n21 -149; 2025: n12 -671; HOLD n10 +292
- M0830_GC_BRK1.5_60: 2023: n14 -19; 2024: n21 -31; 2025: n12 -351; HOLD n10 +169
- M0830_GC_BRK1.5_120: 2023: n14 -62; 2024: n21 -88; 2025: n12 -416; HOLD n10 +145
- M0830_GC_FADE5_60: 2023: n17 +2; 2024: n24 +49; 2025: n12 +288; HOLD n11 -223
- M0830_GC_PRE60: 2023: n17 -24; 2024: n24 -53; 2025: n12 -317; HOLD n11 +283
- FOMC_NQ_BRK1.0_60: 2023: n4 +214; 2024: n6 +156; 2025: n2 +997; HOLD n4 +216
- FOMC_NQ_BRK1.0_120: 2023: n4 +293; 2024: n6 +110; 2025: n2 +997; HOLD n4 +245
- FOMC_NQ_BRK1.5_60: 2023: n4 +226; 2024: n6 +96; 2025: n2 +707; HOLD n4 +657
- FOMC_NQ_BRK1.5_120: 2023: n4 +265; 2024: n6 +129; 2025: n2 +725; HOLD n4 +748
- FOMC_NQ_FADE5_60: 2023: n4 -259; 2024: n7 -1; 2025: n2 -5; HOLD n4 -235
- FOMC_NQ_PRE60: 2023: n4 +19; 2024: n7 -17; 2025: n2 -451; HOLD n4 +105
- FOMC_ES_BRK1.0_60: 2023: n4 +231; 2024: n6 +141; 2025: n3 +323; HOLD n5 +375
- FOMC_ES_BRK1.0_120: 2023: n4 +296; 2024: n6 +64; 2025: n3 +323; HOLD n5 +334
- FOMC_ES_BRK1.5_60: 2023: n4 +238; 2024: n6 +218; 2025: n3 +302; HOLD n5 +304
- FOMC_ES_BRK1.5_120: 2023: n4 +303; 2024: n6 +380; 2025: n3 +173; HOLD n5 +266
- FOMC_ES_FADE5_60: 2023: n4 -505; 2024: n7 -113; 2025: n3 -199; HOLD n5 -423
- FOMC_ES_PRE60: 2023: n4 -38; 2024: n7 -128; 2025: n3 -328; HOLD n5 +4
- FOMC_ZN_BRK1.0_60: 2023: n2 +268; 2024: n4 +25; 2025: n2 -82; HOLD n3 -320
- FOMC_ZN_BRK1.0_120: 2023: n2 +548; 2024: n4 -181; 2025: n2 -100; HOLD n3 -285
- FOMC_ZN_BRK1.5_60: 2023: n2 +112; 2024: n4 +165; 2025: n2 -55; HOLD n3 -324
- FOMC_ZN_BRK1.5_120: 2023: n2 +378; 2024: n4 +100; 2025: n2 -67; HOLD n3 -301
- FOMC_ZN_FADE5_60: 2023: n4 -455; 2024: n8 -174; 2025: n3 -367; HOLD n3 +19
- FOMC_ZN_PRE60: 2023: n4 -60; 2024: n8 -128; 2025: n3 -206; HOLD n4 -189
- FOMC_GC_BRK1.0_60: 2023: n2 +479; 2024: n5 +359; 2025: n4 -511; HOLD n4 -1020
- FOMC_GC_BRK1.0_120: 2023: n2 +734; 2024: n5 +189; 2025: n4 -374; HOLD n4 -1020
- FOMC_GC_BRK1.5_60: 2023: n2 +486; 2024: n5 +372; 2025: n4 -273; HOLD n4 -1014
- FOMC_GC_BRK1.5_120: 2023: n2 +656; 2024: n5 +193; 2025: n4 -442; HOLD n4 -1014
- FOMC_GC_FADE5_60: 2023: n4 -297; 2024: n8 -442; 2025: n4 +354; HOLD n4 -516
- FOMC_GC_PRE60: 2023: n4 -33; 2024: n8 -249; 2025: n4 -234; HOLD n4 -366
- EIA_CL_BRK1.0_60: 2023: n29 -201; 2024: n40 +25; 2025: n15 -180; HOLD n24 +42
- EIA_CL_BRK1.0_120: 2023: n29 -94; 2024: n40 -16; 2025: n15 -334; HOLD n24 -148
- EIA_CL_BRK1.5_60: 2023: n29 -120; 2024: n40 +57; 2025: n15 -91; HOLD n24 +5
- EIA_CL_BRK1.5_120: 2023: n29 -16; 2024: n40 +17; 2025: n15 -339; HOLD n24 -100
- EIA_CL_FADE5_60: 2023: n30 +126; 2024: n42 -295; 2025: n18 -168; HOLD n25 -8
- EIA_CL_PRE60: 2023: n30 -217; 2024: n42 +14; 2025: n18 +55; HOLD n25 -0
- ME_NQ_FLOW: 2023: n11 -196; 2024: n11 -648; 2025: n6 +336; HOLD n7 +80
- ME_ES_FLOW: 2023: n11 -480; 2024: n11 -574; 2025: n6 +989; HOLD n7 -31
- OPEX_NQ_PINFADE: 2023: n2 +254; 2024: n1 +993; 2025: n2 -1018; HOLD n2 +792
- OPEX_ES_PINFADE: 2023: n3 +304; 2024: n6 +81; 2025: n1 -1057; HOLD n5 +261
- MOC_NQ_MOCCONT: 2023: n5 +143; 2024: n5 +626; 2025: n3 -270; HOLD n2 +52
- MOC_ES_MOCCONT: 2023: n5 -136; 2024: n5 +264; 2025: n3 -84; HOLD n2 -335

## 5. Top cells regardless of verdict (failed gate and MDE)

Ranked by pooled mean ($/trade): FOMC_NQ_BRK1.5_120 +392 (n16, MDE 547, DEAD; failed: n<30,CI,plA) | FOMC_NQ_BRK1.5_60 +345 (n16, MDE 486, DEAD; failed: n<30,CI,WF/SPAN2,plA) | FOMC_NQ_BRK1.0_120 +300 (n16, MDE 618, DEAD; failed: n<30,CI,plA) | FOMC_ES_BRK1.5_120 +296 (n18, MDE 520, LEAD; failed: n<30,CI,plA) | FOMC_NQ_BRK1.0_60 +291 (n16, MDE 573, DEAD; failed: n<30,CI,WF/SPAN2,plA) | FOMC_ES_BRK1.5_60 +260 (n18, MDE 462, DEAD; failed: n<30,CI,plA) | FOMC_ES_BRK1.0_60 +256 (n18, MDE 562, DEAD; failed: n<30,CI,WF/SPAN2,plA) | FOMC_ES_BRK1.0_120 +234 (n18, MDE 612, DEAD; failed: n<30,CI,plA) | MOC_NQ_MOCCONT +209 (n15, MDE 644, DEAD; failed: n<30,CI,plA,plB,yr) | OPEX_NQ_PINFADE +150 (n7, MDE 1010, DEAD; failed: n<30,CI,WF/SPAN2,plA,plB,2x,yr)

Best-of-F, zero-null (one-sided t on the SEL trades, p x group F): EV_MACRO M0830_NQ_FADE5_60 t=2.16, p=0.018, x24 = 0.43; EV_FOMC FOMC_ES_BRK1.5_120 t=1.40, p=0.093, x24 = 2.2 (not significant); EV_CAL MOC_NQ_MOCCONT t=0.89, p=0.20, x12 = 2.4. No group has a best cell below Bonferroni 0.05. **Placebo-B caveat:** the random-clock placebo is not centred on zero (a bracket sized to a release, run at a quiet clock, mostly pays cost), so a positive real mean beats it easily; with 5,000 draws (plB_5000.csv) FOMC_ES_BRK1.5_60/_120 have p = 0.001 / 0.0014 and the ZN FOMC break cells p ~ 0 on n=8, yet their CIs include zero. Read placebo B as: better than the same rule at a random time; and the CI/t-test as: better than zero; both are needed and the FOMC breaks pass only the first. Eight correlated FOMC break cells on 12-13 events are one hypothesis, not eight.

## 6. What the event books do for the stack

- The stack's own 08:30 half-hour slot is a net LOSS slot on the truncated span (one of 11 loss slots); the NQ CPI/NFP 5-min fade enters inside it (08:35) and earned +$8.5k pooled at $1,000 risk, weekly correlation +0.09, 63 weeks with a trade out of 149. So the cell is uncorrelated with the stack, but its 20-worst-week P&L is -$949 (7 trades): no worst-week protection. Beside the stack's -$3.53M in those 20 weeks (truncated span) any of these cells at $1,000 risk per trade is a rounding error; scaling to the stack's 20% risk is the job of section H and is not warranted for a cell below its MDE.
- The positive worst-week figures are 2-7 trades deep (section 1); the 19-trade EIA figures belong to cells with negative SEL means. The one number for section C: **$ in the stack's 20 worst weeks for the best cell (M0830_NQ_FADE5_60) = -$949 per $1,000 risk per trade; for the best worst-week figure with a positive SEL mean (FOMC_NQ_BRK1.0_120, LEAD-level) +$1,996 on 2 trades.**
- Month-end flow, opex pin and MOC are small-n nulls (28 / 5-10 / 13 trades): the MDE is 0.5-1.3R per trade, so these are inconclusive, not refuted.

## 7. Calendar caveats and disclosures

1. Calendar is RECONSTRUCTED. Only CPI/NFP/FOMC come from a VERIFIED CSV; ISM, EIA, opex, rebalance, month-end are rules; CPI drops 0%, NFP 6%, FOMC 4-16% (NQ 16%), EIA 32% of dates on the volume test, and the EIA test conditions on the realised release-minute reaction (a muted print is dropped), a mild selection toward bigger-reaction events; for PRE60 cells the confirmation uses volume that is only known after the entry (calendar validity, not look-ahead on direction, but the sample is the confirmed one). Confirmation rates for CPI/NFP/FOMC are 84-100%, so the effect there is small; for EIA (68%) it is not.
2. The first confirmation test used argmax in {t0,t0+1} and wrongly rejected 8 FOMC dates (volume stays high for minutes); fixed to the onset test before any cell was scored. A MOC-volume-magnitude test for close events was written and REJECTED before scoring because it conditions 15:00/15:50 entries on later volume (look-ahead); the descriptive version is kept. Both logged in DECISIONS.
3. After the preregs were written I printed the first six trades of one cell (M0830_NQ_BRK1.0_60) and ran an independent pure-python replay of 53 FADE5 trades (0 mismatches vs the numba engine) before the SEL run; no cell, window, gate or scale was changed after seeing them.
4. G9 (sibling) was written as a sign test only; under the stricter D3CFA R1 standard (sibling CI lower > 0) no cell is sibling-confirmed. Verdict labels follow the frozen prereg; my reading is stricter and is stated in section 1.
5. Placebo A uses a market fill at the bar open, so a stop-entry real trade pays 1 extra tick against its own placebo (conservative for the real cell). Placebo B runs the rule at +/-15..150 min clock shifts on non-event days with the real cell's as-of R, so a bracket sized to a release is wide for a quiet clock (it mostly exits on the clock); that is the definition asked for, and the ranks of the break cells must be read with it (real break cells are far WORSE than placebo-A on NQ/ZN/GC, a reversal signal, not a null).
6. Fees: $4.84 RT for all; ES NT-published, NQ PROXY of ES, CL/ZN/GC WEAK proxy (their ceiling is CANDIDATE). Release-minute spreads and the bar-open stop fills are optimistic; 2x cost is shown. 1-min bars cannot see an intrabar stop-first order.
7. Stack context (weekly corr, worst-20 weeks, loss slots, range days) is recomputed from stack_trades.parquet filtered to label_day <= 20260206 (149 weeks from 2023-04-03); its worst-20 list differs from the audit's published list (which includes weeks to 2026-10). Day type (range/trend) is the audit's ex-post label.
8. Post-hoc observations NOT scored: the 08:30 first-minute break loses on NQ/ZN/GC beyond cost, so its mirror (fade the first-minute break) is a hypothesis for a fresh prereg; the month-end FLOW sign is also negative in SEL. No cell was added or re-signed here.
9. Pooled-all statistics include the HOLD events after the one look; the verdicts use SEL for selection and HOLD only as G8.
