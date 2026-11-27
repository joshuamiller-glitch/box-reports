# WF M11: SIZE BY THE UNUSUAL WHALES RANGE FORECAST (W-WF1112, 2026-11-27 03:04Z)

**PAUSED (LEAD order 0311Z, DIRECTIVE_EXITS_ALL_SERVERS_0311Z.md): M11 is paused until a new order; no further compute; this page is the write-up of what was computed before the pause.**


## ANSWER FIRST
**M11 (size by the UW range forecast) does NOT work as a walk-forward rule. Primary PASS only for S1 Asia (the four-live-mix subject) at the 2-week and 4-week steps; every other session, subject and step FAILS, and the Asia pass is not distinguishable from random half-sizing at the 10% level (p about 0.09-0.11 against a random-half null), before any correction for the number of cells tried.**
- Primary (as ordered): session size FULL when the UW-forecast session range sits in the tercile where the subject earned best per unit drawdown on past data, HALF otherwise; refit of the forecast every 10 trading days, tercile re-chosen at every decision date from past days only.
- The drawdown cut is mostly the half-size effect: the primary runs full size on only 13-49% of days (Asia 36-49%, London 16-23%, NY AM 13-18%, NY PM 37-41%), so income falls 34-52% (Asia 2/4-week excepted: -4%) and fails the "not lower by more than 10%" rule in every session but Asia. A random assignment of the same fraction of half-size days to the same days gives the same share of "good" periods (e.g. All-four S1 2-week: 30/32 real vs 94% mean in the null, p=0.65) and a similar chained drawdown cut.
- UW-specific gain (UW forecast vs the no-UW ATR+IV+weekday benchmark forecast through the same rule): visible in ASIA only. S1 Asia 2-week: UW primary chained out-of-sample max DD -57,585 -> -33,017 with income -4%; benchmark forecast -57,585 -> -48,335 with income -40%. London, NY AM, NY PM: no UW gain (benchmark about equal or better). Forecast quality agrees (out-of-sample R2 of ln session range, benchmark -> UW): Asia 0.278 -> 0.379, London 0.234 -> 0.275, NY AM 0.247 -> 0.270, NY PM 0.282 -> 0.270 (UW does NOT help NY PM).
- Skip-instead-of-half (reference) cuts chained drawdown the most (All-four S1 2-week -215,625 -> -85,661) but costs 73% of income; quintiles -108,737 at -45%: both are just less risk taken.
- Day-type reference (Asia, where the page has a day-type YES: SPY iv_term for crossings): ALL FOUR live Asia books are breakout/follow type (RSI momentum break L385f4f2e, VWAP break L9c2622b0, VWAP-bands break L4aaacdb2, narrow-range structure Lb0e6dfa3), so the page's rule is "full size on forecast trend days (few crossings), half otherwise". That reference row gives S1 Asia 2-week chain -36,923 with income -11%, 4-week -36,923 / -9%, 13-week -36,923 / -7% (5/5 periods good): comparable to the primary, and the fade-type rule (full on chop days) is bad (-76,095, income -39%). NY PM is a mixed book set (L2c6916a5 is a fade book; I did not classify the other three), so both directions are shown as references: fade-direction wins on drawdown (-88,173 -> -36,967 at 2 weeks, income -28%), breakout-direction loses (-97,452).
- Reference rows that also pass (not scored as primaries): S1 Asia skip-instead-of-half at 2 and 4 weeks (income -5%/-7%) and the Asia day-type breakout rule at all steps; a few S2 quintile rows (tiny-income baskets, not meaningful). The reference rows were picked after seeing the primary, so they are context, not candidates.
- Forward periods given by the UW span: forecasts exist from 2025-03-19 (120-day minimum), a decision needs >=60 forecast days, so the first decision is week 116 (2025-06-23): 32 periods at 2 weeks, 16 at 4 weeks, 5 at 13 weeks (Nov 2025 weeks excluded). The programme's "8 of 12" at 13 weeks is unreachable; I applied the same two-thirds rule at every step. With 5 periods nothing at 13 weeks can be called a result.
- No engine rows queued (0 set-months).

## STATUS LINE (UW recorder / plan)
- Live recorder: RUNNING (code/th_uw/uw_live.py, pid 75822, started Nov 18). Its websocket reconnected at 2026-11-27 02:09Z and the server answered every channel join with status ok (join_reply.log), which a lapsed key would normally not do. Newest full live day: 2026-11-25 (1.4 GB); 11-26 (US holiday) and 11-27 hold only join replies so far (pre-open). Errors log: ConnectionClosedError reconnects at 00:45Z and 02:09Z, recovered.
- REST history pulls (the panel behind this work) end 2026-11-12 (552 trading days 2024-10-02..2026-11-12); no pull since, so the forecast cannot be scored beyond that date, and the engine data end 2026-10-30 anyway.
- Plan active: PROBABLY YES (the websocket accepts the token), NOT CONFIRMED: I made NO UW API call, did not log in, renew or buy anything. If LEAD wants a hard yes/no, one read-only status call with the existing key is the only way; I did not make it.

## What was done (exact definitions)
- Forecast: code/wf_m11m12/fc.py imports the DS3_UWREGIME machinery (code/th_uwregime/ur_forecast.py: expanding ridge, min 120 days, refit every 10 trading days = 2 weeks, strictly out of sample). Target = session ln range of NQ (panel T_NQ_<session>_lnrng = ln(1 + range/price)). UW model = strict benchmark (ATR lags, session-range lags, IV level/rank, weekday) + QQQ:iv_term (3 features: term slope, front-end bump, implied move; the "+19 pp over ATR, +10 pp over ATR+IV+DOW" reading for Asia on the page; reproduced: +10.1 pp). No-UW benchmark = the same model without that group.
- Readings and delivery lag (conservative): Asia and London use R0 = prior-close reading (UW minute rows used only from start+180 s, EOD files only from the previous trading day: for Asia, which starts 18:00 ET, the reading is the prior RTH close, so 3 h or more of lag in practice). NY AM (09:30-12:00) uses the 08:30 reading (R1, usable at 08:33), NOT the 09:30 reading (R2 is a reference row: it would be usable only at 09:33, after the first trades). NY PM (12:00-17:00) uses the 10:00 reading (R3). The live websocket delivers in near real time, so this lag is longer than live.
- Rule per decision date d (weeks 26, 28, ... for step 2; every 4; every 13), using only days before the start of week d: terciles of the past forecast values; score of each tercile = past income / max drawdown of the past daily P&L restricted to days in that tercile; the best tercile is FULL size in the coming period, outside it HALF. Days with no forecast = full.
- S1: the four live sets (TL3_SR_AS_STKd8da2eb47b_FSff6_PICKC, TL3_SR_NY_STKd8cd0279ff_FSff6_PICKC, TL3_SR_NP_STKd893133bd8_FSf46_PICKC, TL3_SR_LO_STKd8w42lo_FSffb8_BARE), exact per-trade p484, factor applied to each trade of the day; POST-HOC APPROX (half lots not rounded to integers; stack caps and daily-loss halts not re-run). "All four" = sum of the four treated daily curves.
- S2: Test 5 primary baskets (walk5 rule 5, cells held at the latest 13-week date <= d, same convention as W-WF49's M4), quick screen, weekly resolution (weekly factor from the weekly mean of the daily forecast), $ per 1-lot-per-cell equal-weight basket.
- Good period (2/4-week step): forward max DD shallower, or income higher with DD not deeper; PASS = good in >= 2/3 of periods AND mean income >= 90% of untouched (or income higher in >= 2/3 with DD not deeper). Chained curve = all forward periods concatenated into one curve per variant (max DD of that curve, L3M = weeks 169-181, L6M = weeks 156-181).
- Null: for the primary, 200 draws that permute the day-level factors inside each forward period (same number of half-size days, random days); last column = share of draws with at least as many good periods. Sign-test p and the full numbers are in the scoreboard lines (/mnt/l2/l2vast/_wf/scoreboard_rows.jsonl, method M11, 150 lines, step_weeks 2/4/13).



## Step 2 weeks (32 forward periods), drawdown first

### S1 = four live session mixes (post-hoc approx on exact per-trade results), PRIMARY
| session | version | chained OOS max DD (untouched -> treated) | L3M max DD | L6M max DD | L3M worst week | income change (mean per period) | good periods | verdict | p vs random-half null |
|---|---|---|---|---|---|---|---|---|---|
| Asia | primary | -57,585 -> -33,017 | -21,250 -> -14,428 | -37,750 -> -33,017 | -8,395 -> -8,395 | -3% | 27/32 | PASS | 0.10 |
| London | primary | -127,791 -> -63,895 | -39,760 -> -28,229 | -39,760 -> -28,229 | -20,172 -> -18,284 | -47% | 28/32 | fail | 0.72 |
| NY AM | primary | -163,622 -> -83,497 | -69,974 -> -44,100 | -69,974 -> -44,100 | -35,029 -> -17,515 | -40% | 29/32 | fail | 0.58 |
| NY PM | primary | -88,173 -> -72,831 | -26,269 -> -28,788 | -30,613 -> -28,788 | -18,119 -> -16,302 | -45% | 26/32 | fail | 0.61 |
| All four | primary | -215,625 -> -97,549 | -38,773 -> -35,906 | -76,723 -> -46,710 | -15,957 -> -6,899 | -36% | 30/32 | fail | 0.65 |

### S2 = Test 5 qualifier baskets (quick screen), PRIMARY ($ per 1-lot basket, so incomes are small and noisy)
| session | version | chained OOS max DD (untouched -> treated) | L3M max DD | L6M max DD | L3M worst week | income change (mean per period) | good periods | verdict | p vs random-half null |
|---|---|---|---|---|---|---|---|---|---|
| Asia | primary | -7,083 -> -6,560 | -3,189 -> -2,033 | -3,999 -> -2,771 | -1,920 -> -960 | -44% | 11/32 | fail | 1.00 |
| London | primary | -8,389 -> -5,858 | -5,858 -> -5,858 | -5,858 -> -5,858 | -3,458 -> -3,458 | +80% | 15/32 | fail | 0.20 |
| NY AM | primary | -20,874 -> -10,170 | -4,696 -> -2,348 | -9,115 -> -6,124 | -2,501 -> -1,250 | +31% | 13/32 | fail | 0.54 |
| NY PM | primary | -22,899 -> -17,426 | -5,097 -> -5,030 | -12,126 -> -7,957 | -2,559 -> -2,559 | -185% | 11/32 | fail | 0.94 |
| All four | primary | -34,757 -> -22,601 | -10,529 -> -7,798 | -11,188 -> -7,798 | -5,280 -> -4,521 | -56% | 17/32 | fail | 0.27 |

### Reference rows, S1 (reference; not scored as primary)
| session | version | chained OOS max DD (untouched -> treated) | L3M max DD | L6M max DD | L3M worst week | income change (mean per period) | good periods | verdict | p vs random-half null |
|---|---|---|---|---|---|---|---|---|---|
| Asia | ref bench | -57,585 -> -48,335 | -21,250 -> -18,502 | -37,750 -> -23,953 | -8,395 -> -8,395 | -40% | 27/32 | fail |  |
| Asia | ref skip_outside | -57,585 -> -28,284 | -21,250 -> -21,924 | -37,750 -> -28,284 | -8,395 -> -8,395 | -5% | 25/32 | PASS |  |
| Asia | ref quintile | -57,585 -> -28,792 | -21,250 -> -21,250 | -37,750 -> -21,250 | -8,395 -> -11,618 | -35% | 30/32 | fail |  |
| Asia | ref daytype_brk | -57,585 -> -36,923 | -21,250 -> -16,277 | -37,750 -> -27,051 | -8,395 -> -8,395 | -10% | 23/32 | PASS |  |
| Asia | ref daytype_fade | -57,585 -> -76,095 | -21,250 -> -24,789 | -37,750 -> -40,273 | -8,395 -> -11,125 | -40% | 20/32 | fail |  |
| London | ref bench | -127,791 -> -97,579 | -39,760 -> -28,078 | -39,760 -> -28,078 | -20,172 -> -18,284 | -51% | 27/32 | fail |  |
| London | ref skip_outside | -127,791 -> -59,636 | -39,760 -> -21,873 | -39,760 -> -21,873 | -20,172 -> -16,397 | -93% | 28/32 | fail |  |
| London | ref quintile | -127,791 -> -63,895 | -39,760 -> -30,126 | -39,760 -> -30,126 | -20,172 -> -20,332 | -52% | 26/32 | fail |  |
| NY AM | ref bench | -163,622 -> -81,811 | -69,974 -> -68,133 | -69,974 -> -68,133 | -35,029 -> -26,124 | -34% | 28/32 | fail |  |
| NY AM | ref skip_outside | -163,622 -> -83,497 | -69,974 -> -44,100 | -69,974 -> -44,100 | -35,029 -> -20,161 | -80% | 28/32 | fail |  |
| NY AM | ref quintile | -163,622 -> -89,026 | -69,974 -> -34,987 | -69,974 -> -34,987 | -35,029 -> -17,515 | -46% | 31/32 | fail |  |
| NY AM | ref R2 | -163,622 -> -83,497 | -69,974 -> -34,987 | -69,974 -> -34,987 | -35,029 -> -17,515 | -44% | 29/32 | fail |  |
| NY PM | ref bench | -88,173 -> -55,714 | -26,269 -> -17,859 | -30,613 -> -20,761 | -18,119 -> -16,302 | -47% | 25/32 | fail |  |
| NY PM | ref skip_outside | -88,173 -> -80,357 | -26,269 -> -52,216 | -30,613 -> -70,080 | -18,119 -> -21,586 | -91% | 24/32 | fail |  |
| NY PM | ref quintile | -88,173 -> -58,248 | -26,269 -> -17,066 | -30,613 -> -25,896 | -18,119 -> -15,509 | -45% | 29/32 | fail |  |
| NY PM | ref daytype_brk | -88,173 -> -97,452 | -26,269 -> -35,428 | -30,613 -> -35,428 | -18,119 -> -8,738 | -27% | 15/32 | fail |  |
| NY PM | ref daytype_fade | -88,173 -> -36,967 | -26,269 -> -19,556 | -30,613 -> -25,896 | -18,119 -> -18,441 | -24% | 29/32 | fail |  |
| All four | ref bench | -215,625 -> -127,776 | -38,773 -> -45,839 | -76,723 -> -48,210 | -15,957 -> -8,411 | -39% | 27/32 | fail |  |
| All four | ref skip_outside | -215,625 -> -85,661 | -38,773 -> -41,615 | -76,723 -> -44,308 | -15,957 -> -29,928 | -72% | 28/32 | fail |  |
| All four | ref quintile | -215,625 -> -108,737 | -38,773 -> -25,252 | -76,723 -> -44,583 | -15,957 -> -11,558 | -45% | 32/32 | fail |  |

### Reference rows, S2 (reference)
| session | version | chained OOS max DD (untouched -> treated) | L3M max DD | L6M max DD | L3M worst week | income change (mean per period) | good periods | verdict | p vs random-half null |
|---|---|---|---|---|---|---|---|---|---|
| Asia | ref bench | -7,083 -> -6,560 | -3,189 -> -2,033 | -3,999 -> -2,771 | -1,920 -> -960 | -30% | 11/32 | fail |  |
| Asia | ref skip_outside | -7,083 -> -6,047 | -3,189 -> -1,090 | -3,999 -> -1,544 | -1,920 -> -943 | -87% | 11/32 | fail |  |
| Asia | ref quintile | -7,083 -> -3,542 | -3,189 -> -1,960 | -3,999 -> -3,227 | -1,920 -> -960 | -16% | 14/32 | fail |  |
| Asia | ref daytype_brk | -7,083 -> -4,417 | -3,189 -> -3,189 | -3,999 -> -3,999 | -1,920 -> -1,920 | +9% | 12/32 | fail |  |
| Asia | ref daytype_fade | -7,083 -> -6,208 | -3,189 -> -2,276 | -3,999 -> -2,535 | -1,920 -> -960 | -59% | 5/32 | fail |  |
| London | ref bench | -8,389 -> -5,858 | -5,858 -> -5,858 | -5,858 -> -5,858 | -3,458 -> -3,458 | +58% | 11/32 | fail |  |
| London | ref skip_outside | -8,389 -> -5,858 | -5,858 -> -5,858 | -5,858 -> -5,858 | -3,458 -> -3,458 | +161% | 15/32 | fail |  |
| London | ref quintile | -8,389 -> -3,187 | -5,858 -> -2,929 | -5,858 -> -2,929 | -3,458 -> -1,729 | +102% | 19/32 | fail |  |
| NY AM | ref bench | -20,874 -> -10,437 | -4,696 -> -2,348 | -9,115 -> -4,558 | -2,501 -> -1,250 | +29% | 14/32 | fail |  |
| NY AM | ref skip_outside | -20,874 -> -3,134 | -4,696 -> 0 | -9,115 -> -3,134 | -2,501 -> 0 | +62% | 13/32 | fail |  |
| NY AM | ref quintile | -20,874 -> -10,437 | -4,696 -> -2,348 | -9,115 -> -4,558 | -2,501 -> -1,250 | -25% | 14/32 | fail |  |
| NY AM | ref R2 | -20,874 -> -10,170 | -4,696 -> -2,348 | -9,115 -> -6,124 | -2,501 -> -1,250 | +34% | 13/32 | fail |  |
| NY PM | ref bench | -22,899 -> -14,398 | -5,097 -> -3,716 | -12,126 -> -7,957 | -2,559 -> -1,619 | -95% | 14/32 | fail |  |
| NY PM | ref skip_outside | -22,899 -> -18,682 | -5,097 -> -4,962 | -12,126 -> -8,751 | -2,559 -> -2,559 | -369% | 11/32 | fail |  |
| NY PM | ref quintile | -22,899 -> -13,342 | -5,097 -> -2,110 | -12,126 -> -7,957 | -2,559 -> -1,279 | -28% | 17/32 | fail |  |
| NY PM | ref daytype_brk | -22,899 -> -21,276 | -5,097 -> -4,555 | -12,126 -> -10,503 | -2,559 -> -2,559 | -63% | 5/32 | fail |  |
| NY PM | ref daytype_fade | -22,899 -> -13,337 | -5,097 -> -3,090 | -12,126 -> -7,686 | -2,559 -> -1,279 | +13% | 16/32 | fail |  |
| All four | ref bench | -34,757 -> -20,121 | -10,529 -> -7,871 | -11,188 -> -7,871 | -5,280 -> -4,521 | -29% | 18/32 | fail |  |
| All four | ref skip_outside | -34,757 -> -13,256 | -10,529 -> -5,849 | -11,188 -> -5,849 | -5,280 -> -4,661 | -112% | 15/32 | fail |  |
| All four | ref quintile | -34,757 -> -18,714 | -10,529 -> -4,880 | -11,188 -> -7,694 | -5,280 -> -2,640 | -8% | 18/32 | fail |  |

## Step 4 weeks (16 forward periods), drawdown first

### S1 = four live session mixes (post-hoc approx on exact per-trade results), PRIMARY
| session | version | chained OOS max DD (untouched -> treated) | L3M max DD | L6M max DD | L3M worst week | income change (mean per period) | good periods | verdict | p vs random-half null |
|---|---|---|---|---|---|---|---|---|---|
| Asia | primary | -57,585 -> -39,625 | -21,250 -> -16,724 | -37,750 -> -33,017 | -8,395 -> -8,395 | +0% | 15/16 | PASS | 0.09 |
| London | primary | -127,791 -> -63,895 | -39,760 -> -28,229 | -39,760 -> -28,229 | -20,172 -> -18,284 | -50% | 13/16 | fail | 0.85 |
| NY AM | primary | -163,622 -> -83,497 | -69,974 -> -34,987 | -69,974 -> -34,987 | -35,029 -> -17,515 | -41% | 15/16 | fail | 0.78 |
| NY PM | primary | -88,173 -> -62,926 | -26,269 -> -21,134 | -30,613 -> -21,134 | -18,119 -> -16,302 | -58% | 13/16 | fail | 0.77 |
| All four | primary | -215,625 -> -96,513 | -38,773 -> -26,384 | -76,723 -> -46,710 | -15,957 -> -6,899 | -37% | 16/16 | fail | 0.47 |

### S2 = Test 5 qualifier baskets (quick screen), PRIMARY ($ per 1-lot basket, so incomes are small and noisy)
| session | version | chained OOS max DD (untouched -> treated) | L3M max DD | L6M max DD | L3M worst week | income change (mean per period) | good periods | verdict | p vs random-half null |
|---|---|---|---|---|---|---|---|---|---|
| Asia | primary | -7,083 -> -6,560 | -3,189 -> -2,033 | -3,999 -> -2,771 | -1,920 -> -960 | -44% | 8/16 | fail | 0.85 |
| London | primary | -9,093 -> -5,858 | -5,858 -> -5,858 | -5,858 -> -5,858 | -3,458 -> -3,458 | +61% | 11/16 | PASS | 0.53 |
| NY AM | primary | -21,801 -> -12,912 | -4,696 -> -2,348 | -9,115 -> -6,590 | -2,501 -> -1,250 | +298% | 10/16 | fail | 0.55 |
| NY PM | primary | -22,405 -> -19,118 | -5,097 -> -5,465 | -10,865 -> -8,777 | -2,559 -> -2,559 | -178% | 8/16 | fail | 1.00 |
| All four | primary | -34,285 -> -25,321 | -10,529 -> -8,234 | -10,529 -> -8,234 | -5,280 -> -4,521 | -71% | 11/16 | fail | 0.49 |

### Reference rows, S1 (reference; not scored as primary)
| session | version | chained OOS max DD (untouched -> treated) | L3M max DD | L6M max DD | L3M worst week | income change (mean per period) | good periods | verdict | p vs random-half null |
|---|---|---|---|---|---|---|---|---|---|
| Asia | ref bench | -57,585 -> -39,625 | -21,250 -> -18,502 | -37,750 -> -21,646 | -8,395 -> -4,198 | -38% | 13/16 | fail |  |
| Asia | ref skip_outside | -57,585 -> -39,625 | -21,250 -> -16,724 | -37,750 -> -28,284 | -8,395 -> -8,395 | +0% | 14/16 | PASS |  |
| Asia | ref quintile | -57,585 -> -31,439 | -21,250 -> -22,323 | -37,750 -> -22,323 | -8,395 -> -11,618 | -39% | 14/16 | fail |  |
| Asia | ref daytype_brk | -57,585 -> -36,923 | -21,250 -> -16,277 | -37,750 -> -27,051 | -8,395 -> -8,395 | -7% | 13/16 | PASS |  |
| Asia | ref daytype_fade | -57,585 -> -78,837 | -21,250 -> -24,789 | -37,750 -> -40,273 | -8,395 -> -11,125 | -43% | 13/16 | fail |  |
| London | ref bench | -127,791 -> -103,536 | -39,760 -> -28,078 | -39,760 -> -28,078 | -20,172 -> -18,284 | -52% | 11/16 | fail |  |
| London | ref skip_outside | -127,791 -> -93,652 | -39,760 -> -21,873 | -39,760 -> -21,873 | -20,172 -> -16,397 | -99% | 13/16 | fail |  |
| London | ref quintile | -127,791 -> -63,895 | -39,760 -> -38,041 | -39,760 -> -38,041 | -20,172 -> -16,169 | -52% | 14/16 | fail |  |
| NY AM | ref bench | -163,622 -> -81,811 | -69,974 -> -68,133 | -69,974 -> -68,133 | -35,029 -> -26,124 | -33% | 15/16 | fail |  |
| NY AM | ref skip_outside | -163,622 -> -83,497 | -69,974 -> -20,161 | -69,974 -> -20,161 | -35,029 -> -20,161 | -81% | 15/16 | fail |  |
| NY AM | ref quintile | -163,622 -> -89,026 | -69,974 -> -34,987 | -69,974 -> -34,987 | -35,029 -> -17,515 | -48% | 16/16 | fail |  |
| NY AM | ref R2 | -163,622 -> -81,811 | -69,974 -> -34,987 | -69,974 -> -34,987 | -35,029 -> -17,515 | -41% | 16/16 | fail |  |
| NY PM | ref bench | -88,173 -> -62,380 | -26,269 -> -16,234 | -30,613 -> -20,761 | -18,119 -> -9,060 | -58% | 13/16 | fail |  |
| NY PM | ref skip_outside | -88,173 -> -63,387 | -26,269 -> -44,823 | -30,613 -> -44,823 | -18,119 -> -14,485 | -116% | 12/16 | fail |  |
| NY PM | ref quintile | -88,173 -> -59,407 | -26,269 -> -17,066 | -30,613 -> -25,896 | -18,119 -> -15,509 | -56% | 16/16 | fail |  |
| NY PM | ref daytype_brk | -88,173 -> -97,452 | -26,269 -> -37,648 | -30,613 -> -37,648 | -18,119 -> -8,738 | -40% | 9/16 | fail |  |
| NY PM | ref daytype_fade | -88,173 -> -39,639 | -26,269 -> -19,556 | -30,613 -> -25,896 | -18,119 -> -18,441 | -11% | 16/16 | fail |  |
| All four | ref bench | -215,625 -> -128,701 | -38,773 -> -45,839 | -76,723 -> -48,210 | -15,957 -> -8,411 | -40% | 14/16 | fail |  |
| All four | ref skip_outside | -215,625 -> -103,555 | -38,773 -> -23,705 | -76,723 -> -44,308 | -15,957 -> -14,485 | -75% | 16/16 | fail |  |
| All four | ref quintile | -215,625 -> -107,813 | -38,773 -> -25,252 | -76,723 -> -38,361 | -15,957 -> -11,558 | -48% | 16/16 | fail |  |

### Reference rows, S2 (reference)
| session | version | chained OOS max DD (untouched -> treated) | L3M max DD | L6M max DD | L3M worst week | income change (mean per period) | good periods | verdict | p vs random-half null |
|---|---|---|---|---|---|---|---|---|---|
| Asia | ref bench | -7,083 -> -6,560 | -3,189 -> -2,276 | -3,999 -> -2,771 | -1,920 -> -960 | -39% | 8/16 | fail |  |
| Asia | ref skip_outside | -7,083 -> -6,047 | -3,189 -> -1,090 | -3,999 -> -1,544 | -1,920 -> -943 | -87% | 8/16 | fail |  |
| Asia | ref quintile | -7,083 -> -5,832 | -3,189 -> -1,960 | -3,999 -> -3,227 | -1,920 -> -960 | -10% | 8/16 | fail |  |
| Asia | ref daytype_brk | -7,083 -> -4,417 | -3,189 -> -3,189 | -3,999 -> -3,999 | -1,920 -> -1,920 | +6% | 7/16 | fail |  |
| Asia | ref daytype_fade | -7,083 -> -6,208 | -3,189 -> -2,276 | -3,999 -> -2,276 | -1,920 -> -960 | -56% | 6/16 | fail |  |
| London | ref bench | -9,093 -> -5,858 | -5,858 -> -5,858 | -5,858 -> -5,858 | -3,458 -> -3,458 | +47% | 11/16 | PASS |  |
| London | ref skip_outside | -9,093 -> -5,858 | -5,858 -> -5,858 | -5,858 -> -5,858 | -3,458 -> -3,458 | +123% | 11/16 | PASS |  |
| London | ref quintile | -9,093 -> -4,430 | -5,858 -> -2,929 | -5,858 -> -2,929 | -3,458 -> -1,729 | +68% | 13/16 | PASS |  |
| NY AM | ref bench | -21,801 -> -12,714 | -4,696 -> -2,348 | -9,115 -> -4,558 | -2,501 -> -1,250 | +461% | 12/16 | PASS |  |
| NY AM | ref skip_outside | -21,801 -> -5,226 | -4,696 -> 0 | -9,115 -> -5,226 | -2,501 -> 0 | +595% | 10/16 | fail |  |
| NY AM | ref quintile | -21,801 -> -10,901 | -4,696 -> -2,348 | -9,115 -> -4,558 | -2,501 -> -1,250 | +75% | 11/16 | PASS |  |
| NY AM | ref R2 | -21,801 -> -12,912 | -4,696 -> -2,348 | -9,115 -> -6,590 | -2,501 -> -1,250 | +230% | 10/16 | fail |  |
| NY PM | ref bench | -22,405 -> -16,090 | -5,097 -> -5,030 | -10,865 -> -8,777 | -2,559 -> -2,559 | -136% | 9/16 | fail |  |
| NY PM | ref skip_outside | -22,405 -> -23,432 | -5,097 -> -5,834 | -10,865 -> -12,522 | -2,559 -> -2,559 | -357% | 8/16 | fail |  |
| NY PM | ref quintile | -22,405 -> -14,815 | -5,097 -> -2,110 | -10,865 -> -9,048 | -2,559 -> -1,279 | -52% | 12/16 | fail |  |
| NY PM | ref daytype_brk | -22,405 -> -20,782 | -5,097 -> -4,555 | -10,865 -> -9,242 | -2,559 -> -2,559 | -52% | 5/16 | fail |  |
| NY PM | ref daytype_fade | -22,405 -> -12,826 | -5,097 -> -3,090 | -10,865 -> -7,056 | -2,559 -> -1,279 | +2% | 13/16 | PASS |  |
| All four | ref bench | -34,285 -> -23,015 | -10,529 -> -8,113 | -10,529 -> -8,113 | -5,280 -> -4,521 | -45% | 13/16 | fail |  |
| All four | ref skip_outside | -34,285 -> -20,119 | -10,529 -> -5,939 | -10,529 -> -7,543 | -5,280 -> -4,661 | -142% | 8/16 | fail |  |
| All four | ref quintile | -34,285 -> -23,138 | -10,529 -> -4,880 | -10,529 -> -7,369 | -5,280 -> -2,640 | -5% | 13/16 | PASS |  |

## Step 13 weeks (5 forward periods), drawdown first

### S1 = four live session mixes (post-hoc approx on exact per-trade results), PRIMARY
| session | version | chained OOS max DD (untouched -> treated) | L3M max DD | L6M max DD | L3M worst week | income change (mean per period) | good periods | verdict | p vs random-half null |
|---|---|---|---|---|---|---|---|---|---|
| Asia | primary | -57,585 -> -49,223 | -21,250 -> -18,502 | -37,750 -> -34,869 | -8,395 -> -8,395 | -32% | 5/5 | fail | 0.45 |
| London | primary | -127,791 -> -63,895 | -39,760 -> -30,402 | -39,760 -> -30,402 | -20,172 -> -10,086 | -43% | 4/5 | fail | 0.98 |
| NY AM | primary | -163,622 -> -82,044 | -69,974 -> -34,987 | -69,974 -> -34,987 | -35,029 -> -17,515 | -40% | 5/5 | fail | 0.96 |
| NY PM | primary | -88,173 -> -62,380 | -26,269 -> -28,788 | -30,613 -> -28,788 | -18,119 -> -16,302 | -49% | 3/5 | fail | 0.96 |
| All four | primary | -215,625 -> -116,477 | -38,773 -> -26,384 | -76,723 -> -46,710 | -15,957 -> -6,899 | -41% | 5/5 | fail | 0.94 |

### S2 = Test 5 qualifier baskets (quick screen), PRIMARY ($ per 1-lot basket, so incomes are small and noisy)
| session | version | chained OOS max DD (untouched -> treated) | L3M max DD | L6M max DD | L3M worst week | income change (mean per period) | good periods | verdict | p vs random-half null |
|---|---|---|---|---|---|---|---|---|---|
| Asia | primary | -7,083 -> -7,083 | -3,189 -> -2,276 | -3,999 -> -2,771 | -1,920 -> -960 | -45% | 4/5 | fail | 0.79 |
| London | primary | -6,616 -> -5,869 | -5,858 -> -5,858 | -5,858 -> -5,858 | -3,458 -> -3,458 | +7% | 2/5 | fail | 0.99 |
| NY AM | primary | -22,269 -> -19,740 | -4,696 -> -2,348 | -10,511 -> -8,766 | -2,501 -> -1,250 | -66% | 2/5 | fail | 0.99 |
| NY PM | primary | -23,091 -> -15,032 | -5,097 -> -2,906 | -12,126 -> -9,407 | -2,559 -> -1,279 | -96% | 4/5 | fail | 0.69 |
| All four | primary | -34,757 -> -29,817 | -10,529 -> -7,304 | -11,188 -> -9,530 | -5,280 -> -3,711 | -64% | 5/5 | fail | 0.65 |

### Reference rows, S1 (reference; not scored as primary)
| session | version | chained OOS max DD (untouched -> treated) | L3M max DD | L6M max DD | L3M worst week | income change (mean per period) | good periods | verdict | p vs random-half null |
|---|---|---|---|---|---|---|---|---|---|
| Asia | ref bench | -57,585 -> -28,792 | -21,250 -> -16,724 | -37,750 -> -23,953 | -8,395 -> -8,395 | -52% | 5/5 | fail |  |
| Asia | ref skip_outside | -57,585 -> -40,861 | -21,250 -> -33,055 | -37,750 -> -33,055 | -8,395 -> -14,553 | -65% | 4/5 | fail |  |
| Asia | ref quintile | -57,585 -> -50,530 | -21,250 -> -14,961 | -37,750 -> -21,435 | -8,395 -> -4,256 | -46% | 5/5 | fail |  |
| Asia | ref daytype_brk | -57,585 -> -36,923 | -21,250 -> -16,277 | -37,750 -> -27,051 | -8,395 -> -8,395 | -8% | 5/5 | PASS |  |
| Asia | ref daytype_fade | -57,585 -> -65,848 | -21,250 -> -24,789 | -37,750 -> -40,273 | -8,395 -> -11,125 | -42% | 1/5 | fail |  |
| London | ref bench | -127,791 -> -64,626 | -39,760 -> -21,673 | -39,760 -> -21,673 | -20,172 -> -10,086 | -40% | 4/5 | fail |  |
| London | ref skip_outside | -127,791 -> -45,363 | -39,760 -> -21,873 | -39,760 -> -21,873 | -20,172 -> -21,873 | -86% | 4/5 | fail |  |
| London | ref quintile | -127,791 -> -63,895 | -39,760 -> -36,957 | -39,760 -> -36,957 | -20,172 -> -20,332 | -51% | 4/5 | fail |  |
| NY AM | ref bench | -163,622 -> -81,811 | -69,974 -> -68,133 | -69,974 -> -68,133 | -35,029 -> -26,124 | -35% | 5/5 | fail |  |
| NY AM | ref skip_outside | -163,622 -> -68,332 | -69,974 -> 0 | -69,974 -> 0 | -35,029 -> 0 | -81% | 5/5 | fail |  |
| NY AM | ref quintile | -163,622 -> -89,026 | -69,974 -> -34,987 | -69,974 -> -34,987 | -35,029 -> -17,515 | -52% | 5/5 | fail |  |
| NY AM | ref R2 | -163,622 -> -81,811 | -69,974 -> -34,987 | -69,974 -> -34,987 | -35,029 -> -17,515 | -42% | 5/5 | fail |  |
| NY PM | ref bench | -88,173 -> -54,141 | -26,269 -> -17,859 | -30,613 -> -17,859 | -18,119 -> -16,302 | -40% | 5/5 | fail |  |
| NY PM | ref skip_outside | -88,173 -> -58,724 | -26,269 -> -52,216 | -30,613 -> -58,724 | -18,119 -> -21,586 | -98% | 3/5 | fail |  |
| NY PM | ref quintile | -88,173 -> -59,407 | -26,269 -> -14,650 | -30,613 -> -25,896 | -18,119 -> -9,410 | -39% | 5/5 | fail |  |
| NY PM | ref daytype_brk | -88,173 -> -104,534 | -26,269 -> -35,841 | -30,613 -> -35,841 | -18,119 -> -8,738 | -28% | 1/5 | fail |  |
| NY PM | ref daytype_fade | -88,173 -> -34,657 | -26,269 -> -19,556 | -30,613 -> -25,896 | -18,119 -> -18,441 | -22% | 5/5 | fail |  |
| All four | ref bench | -215,625 -> -107,813 | -38,773 -> -45,839 | -76,723 -> -45,839 | -15,957 -> -30,422 | -39% | 4/5 | fail |  |
| All four | ref skip_outside | -215,625 -> -73,810 | -38,773 -> -29,922 | -76,723 -> -50,937 | -15,957 -> -29,928 | -81% | 5/5 | fail |  |
| All four | ref quintile | -215,625 -> -103,004 | -38,773 -> -25,449 | -76,723 -> -38,361 | -15,957 -> -11,558 | -49% | 5/5 | fail |  |

### Reference rows, S2 (reference)
| session | version | chained OOS max DD (untouched -> treated) | L3M max DD | L6M max DD | L3M worst week | income change (mean per period) | good periods | verdict | p vs random-half null |
|---|---|---|---|---|---|---|---|---|---|
| Asia | ref bench | -7,083 -> -7,083 | -3,189 -> -2,276 | -3,999 -> -2,771 | -1,920 -> -960 | -45% | 4/5 | fail |  |
| Asia | ref skip_outside | -7,083 -> -7,093 | -3,189 -> -1,575 | -3,999 -> -1,575 | -1,920 -> -943 | -90% | 4/5 | fail |  |
| Asia | ref quintile | -7,083 -> -4,270 | -3,189 -> -2,033 | -3,999 -> -2,033 | -1,920 -> -960 | -22% | 5/5 | fail |  |
| Asia | ref daytype_brk | -7,083 -> -4,417 | -3,189 -> -3,189 | -3,999 -> -3,999 | -1,920 -> -1,920 | +7% | 4/5 | PASS |  |
| Asia | ref daytype_fade | -7,083 -> -6,208 | -3,189 -> -2,276 | -3,999 -> -2,276 | -1,920 -> -960 | -57% | 3/5 | fail |  |
| London | ref bench | -6,616 -> -5,858 | -5,858 -> -5,858 | -5,858 -> -5,858 | -3,458 -> -3,458 | +31% | 3/5 | fail |  |
| London | ref skip_outside | -6,616 -> -5,858 | -5,858 -> -5,858 | -5,858 -> -5,858 | -3,458 -> -3,458 | +13% | 2/5 | fail |  |
| London | ref quintile | -6,616 -> -2,929 | -5,858 -> -2,929 | -5,858 -> -2,929 | -3,458 -> -1,729 | +81% | 4/5 | PASS |  |
| NY AM | ref bench | -22,269 -> -18,063 | -4,696 -> -2,348 | -10,511 -> -5,255 | -2,501 -> -1,250 | -8% | 2/5 | fail |  |
| NY AM | ref skip_outside | -22,269 -> -17,210 | -4,696 -> 0 | -10,511 -> -7,021 | -2,501 -> 0 | -131% | 2/5 | fail |  |
| NY AM | ref quintile | -22,269 -> -11,134 | -4,696 -> -2,348 | -10,511 -> -5,255 | -2,501 -> -1,250 | +31% | 5/5 | PASS |  |
| NY AM | ref R2 | -22,269 -> -18,964 | -4,696 -> -2,348 | -10,511 -> -7,990 | -2,501 -> -1,250 | -52% | 2/5 | fail |  |
| NY PM | ref bench | -23,091 -> -15,032 | -5,097 -> -4,739 | -12,126 -> -9,407 | -2,559 -> -2,559 | -74% | 4/5 | fail |  |
| NY PM | ref skip_outside | -23,091 -> -8,339 | -5,097 -> -716 | -12,126 -> -7,004 | -2,559 -> -716 | -192% | 4/5 | fail |  |
| NY PM | ref quintile | -23,091 -> -11,688 | -5,097 -> -2,548 | -12,126 -> -6,063 | -2,559 -> -1,279 | +7% | 4/5 | PASS |  |
| NY PM | ref daytype_brk | -23,091 -> -21,276 | -5,097 -> -4,555 | -12,126 -> -10,503 | -2,559 -> -2,559 | -136% | 3/5 | fail |  |
| NY PM | ref daytype_fade | -23,091 -> -13,838 | -5,097 -> -3,090 | -12,126 -> -7,686 | -2,559 -> -1,279 | +86% | 5/5 | PASS |  |
| All four | ref bench | -34,757 -> -28,787 | -10,529 -> -8,181 | -11,188 -> -8,500 | -5,280 -> -4,521 | -42% | 5/5 | fail |  |
| All four | ref skip_outside | -34,757 -> -27,208 | -10,529 -> -4,230 | -11,188 -> -9,200 | -5,280 -> -3,042 | -127% | 5/5 | fail |  |
| All four | ref quintile | -34,757 -> -16,126 | -10,529 -> -5,130 | -11,188 -> -5,130 | -5,280 -> -2,640 | +5% | 5/5 | PASS |  |

## Honest caveats
- Short span: the UW forecast has only ~17 months of out-of-sample days (2025-03-19..2026-10-30, Nov 2025 excluded), the first 3 months of which are consumed by the 60-day minimum for the tercile choice; five 13-week periods and 16 four-week periods are not enough to separate skill from luck, and the 2-week periods are 32 overlapping-regime samples, not independent ones (a drawdown over one or two weeks is noisy; the chained curve is the steadier number).
- The live books were chosen on the same weeks (in-sample), so every S1 "untouched" curve is the best case; S2 qualifiers are in-sample too.
- The UW input (QQQ:iv_term) was picked on the full-sample page (it is the page's top row), so the UW forecast fit is itself a forking-paths choice; the refit is out of sample, the input choice is not. The page's own family null charged the choice of group/reading, but not this selection of a favourite for sizing.
- The strict benchmark has no macro-event calendar and no VIX (not on the box); iv_term partly carries event risk (FOMC/CPI), so a UW "gain" in Asia/London may be an event-day signal rather than gamma/flow.
- The NY AM and NY PM forecasts are weak on the range target (NY AM lnrng gain is the page's "weak" row, L3M negative; NY PM +/-0), so poor sizing results there are expected.
- Median sizes: S1 half-size is not integer-lot rounded; engine layers (stack caps, daily-loss halts) are not re-run; sizes of 1-lot books cannot be halved live without rounding. S2 income is $ per 1-lot basket and tiny or negative for London and NY PM baskets, so S2 income percentages are meaningless there (PASS rows where the untouched income is below zero are artifacts, flagged in the scoreboard notes).
- Luck accounting: M11 adds 5 sessions x 2 subjects x 3 steps = 30 primary cells (24 excluding "All four"); the S1 Asia 2- and 4-week PASS rows are two of them, p about 0.1 against the random-half null, so after any best-of correction nothing here survives. Nothing is called "works"; if LEAD wants it on the forward register, the candidate is S1 Asia only and it must be forward-tested.
