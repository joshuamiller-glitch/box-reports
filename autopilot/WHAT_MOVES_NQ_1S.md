# WHAT_MOVES_NQ_1S: the WHAT_MOVES_NQ method rerun at 1 second with the new feeds. DISCOVERY, NOT A RESULT (PARTIAL)
Generated 2026-11-28T09:54Z. Order: relay directive 0552Z (autopilot/DIRECTIVE_0552Z_what-moves-nq-1s.md). Label: DISCOVERY. It only feeds which feeds sit on which desk seat; nothing here is a trading rule. Old page (not overwritten): autopilot/WHAT_MOVES_NQ.md.

Code: code/th_dynl/wm1s_conv.py (dbn to per-second tables), wm1s_run.py (reuses wm_run.stats_for, same matched null), wm1s_agg.py, wm1s_turns.py, wm1s_turn_agg.py, wm1s_page.py. Monthly counts backed up in /mnt/l2/l2vast/_dynexit/wm1s_backup/.

## ANSWER FIRST
Scope: 18 of 19 months scored so far (2025-10 stage 1 still finishing; turns still running), windows 1/5/15/60/300 s, four sessions, by half-year, BH over ~2,900 grid cells. Everything below is DISCOVERY and only says which feed could sit on which desk seat.

1. MEGACAPS BELOW ONE MINUTE IN NY AM / NY PM: NO. Neither any single megacap (NVDA MSFT AAPL AMZN META GOOGL AVGO TSLA), nor QQQ/SPY, nor the 8-name basket (price or signed trade flow) leads NQ at 1/5/15/60 s in NY AM or NY PM once NQ itself has not moved: best rows are +0.0 to +3.8 pp with z <= 1.0 and BH q = 1.0 (the basket in NY AM: best +2.1 pp at 300 s, z 0.8, and its follow move flips sign by half-year). They move WITH NQ in the same second (megacap/basket correlation with NQ is high at lag 0) and NQ is simply the faster instrument; NQ is the market the megacaps are priced off at this horizon. Only trace: the basket's signed trade flow in London at 1 s (+3.2 pp, z 4.5, q 0.001, but only 11k fires, edge fades by half-year +5.3 / +3.4 / +1.6 / +0.1, follow 0.014 bp): SOMETIMES, not a seat feed.
2. YM, ZB, 6J, NKD IN ASIA AND LONDON: NO. None of the four (price, signed flow, top-of-book imbalance) shows a BH-significant lead in either session: Asia best +0.3 to +0.9 pp (z <= 2.3, q >= 0.68), London best +0.2 to +2.0 pp (z <= 2.0, q = 1.0). What DOES lead, steadily and tiny, in Asia: 6A and 6E (price +1.4 / +1.1 pp at 1 s, z 7.5 / 6.4, positive in all four half-years but shrinking; 6E flow +1.3 pp) and copper HG (+1.0 pp in Asia, +0.9 pp in London at 1 s, q 0.002). Follow move 0.007-0.011 bp (about 0.02-0.03 NQ points): far below a tick. The old reference lead stays the largest: ES moves lead NQ at 1 s by +4.0 pp Asia, +3.3 pp London and +3.3 pp NY PM (NQ-flat, q <= 0.02), RTY +2.3 pp Asia; both fade across half-years (ES Asia +7.5 / +7.1 / +3.9 / +1.9).
3. WHICH LEAD NQ TURNS: turns still running; section 6 fills in when they finish
Plain statement: apart from ES/RTY (already known) and FX/copper in Asia at 1 second, with sub-tick follow moves, NOTHING in these new feeds leads NQ in the matched-null test. The one "result" that looked dramatic (20-37 pp edges, basket 84-87 percent hit) was a one-second timestamp look-ahead and is void. The new feeds' value is as CONFIRMATION/context (they move with NQ), not as early warning.

## 1. Method (identical to WHAT_MOVES_NQ.md unless stated)
- NQ grid: NQ mid per second (the old age_ feed), 18 months 2025-05..2026-11. Feed move over the last w seconds (w = 1/5/15/60/300 s), scaled by its own rolling std over the previous 3600 s; FIRE at >= 2 sigma; NQ-FLAT variant = NQ itself has not moved yet (< 0.5 sigma). Outcome = NQ return over the next h seconds (h = w and 300 s); HIT = same sign as the feed (sign fixed on the first 60% of the months by same-moment covariance); refractory max(w,h). MATCHED NULL = same fires scored against NQ outcomes 30-120 min later. Edge = hit - null.
- Feeds: EQUS.MINI 1-s bars for NVDA MSFT AAPL AMZN META GOOGL AVGO TSLA QQQ SPY (px_), their signed trade flow from EQUS.MINI trades (fl_, dollar-signed), the equal-weight 8-megacap basket (px_BASKET8 = mean 1-s log return, needs >= 3 live names; fl_BASKET8 = summed signed dollar flow), GLBX 1-s bars YM ZB 6E 6J NKD 6A HG (px_), tbbo signed trade size (fl_) and top-of-book size imbalance at the last trade (imb_) for YM ZB 6E 6J NKD. Reference rows ref_px_ES / ref_px_RTY come from the old ES/RTY mid feed. Roll jumps in .v.0 series are removed (|1-s move| > 40 bp futures, > 150 bp stocks set to 0); price forward-filled at most 60 s.
- TIMING FIX (important): Databento bars and trades are stamped at the START of their second. A bar stamped t is complete only at t+1. Unshifted, the feeds correlated with NQ at lag 1 and the first run printed fake 20-37 pp 1-second "leads" (basket 84-87 percent hit): look-ahead of one second. That first run is VOID and was deleted; every feed is now shifted +1 s so a bar is used only once complete (check: after the shift the basket/YM correlate with NQ at lag 0). Residual: a feed bar closing at second t and the NQ mid at second t are the same instant, so "lead" below means the NEXT seconds of NQ.
- DEGRADED DATA: EQUS.MINI days named by the coordinator (2025-05-06, 2025-06-04, 2025-06-16) plus 2025-12-24 (half day, under 50 percent of the median row count) are EXCLUDED from every megacap/QQQ/SPY price and flow row (set to missing). Only these four were identifiable without calling the conditions API; if the conditions API lists more EQUS.MINI days, they are NOT excluded here (the page says so rather than guessing). For GLBX series, days under 50 percent of the median row count (holidays, half days) and 2026-11-01 are excluded.
- Sessions (ET of fire time): Asia 18:00-03:00, London 03:00-08:30, NY AM 08:30-12:00, NY PM 12:00-16:00. Premarket/after-hours stock prints exist (EQUS.MINI) but are thin: megacap rows in Asia/London have few fires per month (column "fires").
- By HALF-YEAR: 2025H1 = May-Jun only, 2025H2, 2026H1, 2026H2 = Jul-Nov (stocks to 2026-10-31, futures to 2026-11-13 where NQ grid exists).
- Selection (table 3): per feed, session, variant the (w,h) with best edge z on the FIT months (first 60 percent of months) is judged ONCE on the last 40 percent; BH q over all judged rows. Labels: STEADY LEADER = judge edge >= 1.0 pp, BH q <= 0.10, positive in >= 75 percent of half-years with >= 200 fires and at least 3 such half-years, positive in L3M and L6M. SOMETIMES = positive on the judge set and (q <= 0.10 or positive in L6M). NEVER otherwise. NOTE: the inherited SOMETIMES rule is loose (it passes anything positive in the last 6 months); rows with q > 0.10 are printed as "SOMETIMES (noise level)" and should be read as NEVER.
- Full grid (table 1/2): every (feed, session, variant, w=h) over the whole window with BH over all 2945 grid cells (10 cells have q <= 0.10 and edge >= 1 pp).

## 2. Table 1: megacaps / basket / QQQ / SPY vs NQ, NY AM and NY PM, horizons up to 60 s (best w=h per row on the whole window; NQ-FLAT variant; ES reference last)
| session | feed | w=h (s) | fires | hit | null | edge pp | z | BH q | by half-year edge pp |
|---|---|---|---|---|---|---|---|---|---|
| NY AM | px_BASKET8 | 15 | 6304 | 0.498 | 0.494 | +0.4 | 0.4 | 1.000 | 25H1 +2.6 / 25H2 +3.4 / 26H1 -1.1 / 26H2 -0.9 |
| NY AM | fl_BASKET8 | 15 | 17195 | 0.501 | 0.499 | +0.2 | 0.3 | 1.000 | 25H1 -1.1 / 25H2 +0.6 / 26H1 +1.3 / 26H2 -1.7 |
| NY AM | px_NVDA | 60 | 2499 | 0.500 | 0.494 | +0.7 | 0.5 | 1.000 | 25H1 +2.4 / 25H2 +0.4 / 26H1 +1.6 / 26H2 -1.7 |
| NY AM | px_MSFT | 60 | 2205 | 0.515 | 0.490 | +2.5 | 1.7 | 1.000 | 25H1 +7.0 / 25H2 +0.5 / 26H1 +3.3 / 26H2 +1.3 |
| NY AM | px_AAPL | 15 | 9659 | 0.501 | 0.499 | +0.2 | 0.2 | 1.000 | 25H1 -0.1 / 25H2 -0.1 / 26H1 +1.0 / 26H2 -0.5 |
| NY AM | px_AMZN | 1 | 45829 | 0.501 | 0.501 | +0.1 | 0.2 | 1.000 | 25H1 +0.3 / 25H2 -0.4 / 26H1 -0.1 / 26H2 +0.7 |
| NY AM | px_META | 5 | 18895 | 0.505 | 0.500 | +0.6 | 1.1 | 1.000 | 25H1 +1.6 / 25H2 +1.2 / 26H1 -0.2 / 26H2 +0.4 |
| NY AM | px_GOOGL | 5 | 17293 | 0.505 | 0.498 | +0.7 | 1.3 | 1.000 | 25H1 +0.2 / 25H2 +1.0 / 26H1 -0.0 / 26H2 +1.5 |
| NY AM | px_AVGO | 15 | 6227 | 0.504 | 0.500 | +0.4 | 0.4 | 1.000 | 25H1 +1.9 / 25H2 -0.3 / 26H1 -0.3 / 26H2 +1.7 |
| NY AM | px_TSLA | 15 | 10291 | 0.510 | 0.498 | +1.1 | 1.6 | 1.000 | 25H1 -0.8 / 25H2 +3.3 / 26H1 +2.2 / 26H2 -2.5 |
| NY AM | px_QQQ | 60 | 368 | 0.516 | 0.478 | +3.8 | 1.0 | 1.000 | 25H1 +1.8 / 25H2 +6.6 / 26H1 -0.6 / 26H2 +7.1 |
| NY AM | px_SPY | 60 | 572 | 0.465 | 0.481 | -1.6 | -0.5 | 1.000 | 25H1 +4.1 / 25H2 -5.8 / 26H1 -2.9 / 26H2 +3.6 |
| NY AM | fl_NVDA | 1 | 25632 | 0.501 | 0.501 | +0.0 | 0.0 | 1.000 | 25H1 -1.5 / 25H2 +0.7 / 26H1 +0.3 / 26H2 -0.6 |
| NY AM | fl_QQQ | 5 | 33567 | 0.506 | 0.502 | +0.4 | 0.9 | 1.000 | 25H1 +0.8 / 25H2 -0.3 / 26H1 +0.5 / 26H2 +0.8 |
| NY AM | fl_SPY | 1 | 37320 | 0.500 | 0.498 | +0.2 | 0.5 | 1.000 | 25H1 +0.2 / 25H2 +1.2 / 26H1 -0.4 / 26H2 -0.7 |
| NY AM | ref_px_ES | 1 | 7412 | 0.522 | 0.499 | +2.3 | 2.7 | 0.477 | 25H1 -1.2 / 25H2 +2.4 / 26H1 +1.4 / 26H2 +3.6 |
| NY PM | px_BASKET8 | 1 | 45634 | 0.499 | 0.499 | +0.0 | 0.1 | 1.000 | 25H1 +1.0 / 25H2 +1.4 / 26H1 -1.0 / 26H2 -0.2 |
| NY PM | fl_BASKET8 | 1 | 42440 | 0.501 | 0.498 | +0.4 | 1.0 | 1.000 | 25H1 -2.3 / 25H2 +0.7 / 26H1 +0.1 / 26H2 +1.3 |
| NY PM | px_NVDA | 1 | 78873 | 0.500 | 0.501 | -0.1 | -0.4 | 1.000 | 25H1 -0.4 / 25H2 +0.3 / 26H1 -0.4 / 26H2 -0.0 |
| NY PM | px_MSFT | 5 | 42672 | 0.503 | 0.498 | +0.5 | 1.4 | 1.000 | 25H1 +1.4 / 25H2 -0.1 / 26H1 +1.2 / 26H2 +0.1 |
| NY PM | px_AAPL | 15 | 19231 | 0.500 | 0.498 | +0.2 | 0.3 | 1.000 | 25H1 +0.8 / 25H2 +0.3 / 26H1 +0.2 / 26H2 -0.1 |
| NY PM | px_AMZN | 15 | 16473 | 0.501 | 0.492 | +0.9 | 1.6 | 1.000 | 25H1 -0.5 / 25H2 +3.1 / 26H1 -0.1 / 26H2 +0.4 |
| NY PM | px_META | 60 | 6000 | 0.511 | 0.500 | +1.1 | 1.2 | 1.000 | 25H1 -0.8 / 25H2 +0.8 / 26H1 -0.3 / 26H2 +3.0 |
| NY PM | px_GOOGL | 1 | 98384 | 0.501 | 0.500 | +0.1 | 0.5 | 1.000 | 25H1 +0.1 / 25H2 +1.0 / 26H1 -0.8 / 26H2 +0.5 |
| NY PM | px_AVGO | 60 | 4841 | 0.512 | 0.501 | +1.1 | 1.0 | 1.000 | 25H1 -0.9 / 25H2 +0.8 / 26H1 +2.2 / 26H2 +0.6 |
| NY PM | px_TSLA | 60 | 5530 | 0.498 | 0.500 | -0.2 | -0.2 | 1.000 | 25H1 -2.2 / 25H2 +1.4 / 26H1 -1.1 / 26H2 +0.0 |
| NY PM | px_QQQ | 60 | 108 | 0.565 | 0.548 | +1.7 | 0.2 | 1.000 | 25H1 na / 25H2 na / 26H1 na / 26H2 +6.0 |
| NY PM | px_SPY | 15 | 3027 | 0.505 | 0.501 | +0.4 | 0.3 | 1.000 | 25H1 -1.0 / 25H2 +2.0 / 26H1 +0.1 / 26H2 -0.3 |
| NY PM | fl_NVDA | 1 | 29068 | 0.499 | 0.499 | +0.1 | 0.1 | 1.000 | 25H1 +0.2 / 25H2 +0.9 / 26H1 -0.3 / 26H2 -0.4 |
| NY PM | fl_QQQ | 5 | 38056 | 0.500 | 0.497 | +0.3 | 0.7 | 1.000 | 25H1 +0.2 / 25H2 +0.7 / 26H1 +1.1 / 26H2 -1.6 |
| NY PM | fl_SPY | 1 | 50721 | 0.503 | 0.501 | +0.2 | 0.5 | 1.000 | 25H1 -0.8 / 25H2 +0.3 / 26H1 +0.1 / 26H2 +0.8 |
| NY PM | ref_px_ES | 1 | 8472 | 0.531 | 0.497 | +3.3 | 3.8 | 0.018 | 25H1 +7.8 / 25H2 +2.9 / 26H1 +2.1 / 26H2 +4.6 |

## 3. Table 2: YM, ZB, 6J, NKD (and 6E 6A HG) vs NQ, Asia and London, horizons up to 300 s (best w=h per row; NQ-FLAT)
| session | feed | w=h (s) | fires | hit | null | edge pp | z | BH q | by half-year edge pp |
|---|---|---|---|---|---|---|---|---|---|
| Asia | px_YM | 1 | 110348 | 0.504 | 0.500 | +0.3 | 1.4 | 1.000 | 25H1 +0.9 / 25H2 +0.8 / 26H1 +0.1 / 26H2 +0.1 |
| Asia | fl_YM | 1 | 94175 | 0.507 | 0.501 | +0.6 | 2.3 | 0.840 | 25H1 +1.3 / 25H2 +1.1 / 26H1 +0.4 / 26H2 +0.2 |
| Asia | imb_YM | 60 | 19808 | 0.503 | 0.496 | +0.7 | 1.4 | 1.000 | 25H1 -0.6 / 25H2 +0.6 / 26H1 +0.8 / 26H2 +1.3 |
| Asia | px_ZB | 1 | 28862 | 0.502 | 0.499 | +0.3 | 0.7 | 1.000 | 25H1 +0.9 / 25H2 +0.2 / 26H1 +0.4 / 26H2 -0.1 |
| Asia | fl_ZB | 300 | 6152 | 0.506 | 0.496 | +0.9 | 1.0 | 1.000 | 25H1 +5.5 / 25H2 +0.5 / 26H1 -1.0 / 26H2 +2.1 |
| Asia | imb_ZB | 60 | 9125 | 0.499 | 0.492 | +0.8 | 1.0 | 1.000 | 25H1 +3.5 / 25H2 -0.4 / 26H1 +0.6 / 26H2 +1.4 |
| Asia | px_6J | 5 | 158064 | 0.499 | 0.500 | -0.0 | -0.3 | 1.000 | 25H1 +0.7 / 25H2 -0.1 / 26H1 -0.3 / 26H2 +0.1 |
| Asia | fl_6J | 15 | 49736 | 0.501 | 0.500 | +0.1 | 0.3 | 1.000 | 25H1 -0.2 / 25H2 -0.3 / 26H1 -0.3 / 26H2 +1.2 |
| Asia | imb_6J | 15 | 10230 | 0.503 | 0.498 | +0.4 | 0.6 | 1.000 | 25H1 -0.3 / 25H2 -1.6 / 26H1 +1.0 / 26H2 +0.8 |
| Asia | px_NKD | 300 | 2045 | 0.499 | 0.491 | +0.8 | 0.5 | 1.000 | 25H1 -0.1 / 25H2 -1.3 / 26H1 +2.8 / 26H2 +1.1 |
| Asia | fl_NKD | 1 | 61895 | 0.506 | 0.502 | +0.3 | 1.0 | 1.000 | 25H1 +0.2 / 25H2 +0.5 / 26H1 +0.0 / 26H2 +0.7 |
| Asia | imb_NKD | 300 | 6201 | 0.500 | 0.496 | +0.3 | 0.4 | 1.000 | 25H1 +1.2 / 25H2 -0.6 / 26H1 +0.5 / 26H2 +0.9 |
| Asia | px_6E | 1 | 183407 | 0.511 | 0.500 | +1.1 | 6.4 | 0.000 | 25H1 +0.4 / 25H2 +2.3 / 26H1 +1.2 / 26H2 +0.3 |
| Asia | px_6A | 1 | 157262 | 0.514 | 0.499 | +1.4 | 7.5 | 0.000 | 25H1 +1.0 / 25H2 +3.1 / 26H1 +1.3 / 26H2 +0.2 |
| Asia | px_HG | 1 | 145547 | 0.508 | 0.498 | +1.0 | 5.1 | 0.000 | 25H1 +0.7 / 25H2 +1.3 / 26H1 +1.1 / 26H2 +0.6 |
| Asia | ref_px_ES | 1 | 36064 | 0.538 | 0.498 | +4.0 | 9.8 | 0.000 | 25H1 +7.5 / 25H2 +7.1 / 26H1 +3.9 / 26H2 +1.9 |
| London | px_YM | 5 | 52594 | 0.498 | 0.500 | -0.2 | -0.7 | 1.000 | 25H1 +0.8 / 25H2 -0.7 / 26H1 -0.4 / 26H2 +0.1 |
| London | fl_YM | 300 | 3482 | 0.511 | 0.490 | +2.0 | 1.7 | 1.000 | 25H1 -3.9 / 25H2 +1.0 / 26H1 +4.0 / 26H2 +2.9 |
| London | imb_YM | 1 | 13359 | 0.499 | 0.497 | +0.2 | 0.3 | 1.000 | 25H1 -0.7 / 25H2 -2.3 / 26H1 +1.3 / 26H2 +0.4 |
| London | px_ZB | 15 | 58836 | 0.501 | 0.498 | +0.3 | 0.9 | 1.000 | 25H1 +0.0 / 25H2 +0.5 / 26H1 +0.5 / 26H2 -0.2 |
| London | fl_ZB | 1 | 39337 | 0.508 | 0.501 | +0.8 | 2.0 | 1.000 | 25H1 +1.4 / 25H2 +2.0 / 26H1 +0.0 / 26H2 +0.0 |
| London | imb_ZB | 5 | 7786 | 0.499 | 0.496 | +0.3 | 0.4 | 1.000 | 25H1 -12.8 / 25H2 +0.7 / 26H1 +1.0 / 26H2 -0.7 |
| London | px_6J | 60 | 11547 | 0.501 | 0.493 | +0.9 | 1.3 | 1.000 | 25H1 -1.8 / 25H2 +1.9 / 26H1 +0.2 / 26H2 +1.7 |
| London | fl_6J | 15 | 26947 | 0.500 | 0.500 | -0.1 | -0.1 | 1.000 | 25H1 +1.4 / 25H2 -1.4 / 26H1 +0.4 / 26H2 +0.1 |
| London | imb_6J | 60 | 9539 | 0.500 | 0.501 | -0.1 | -0.2 | 1.000 | 25H1 +1.6 / 25H2 +0.3 / 26H1 -1.1 / 26H2 -0.3 |
| London | px_NKD | 300 | 765 | 0.507 | 0.488 | +1.9 | 0.7 | 1.000 | 25H1 +5.8 / 25H2 +1.5 / 26H1 -3.1 / 26H2 +7.9 |
| London | fl_NKD | 1 | 30603 | 0.502 | 0.500 | +0.2 | 0.5 | 1.000 | 25H1 +0.7 / 25H2 +0.5 / 26H1 -0.1 / 26H2 +0.3 |
| London | imb_NKD | 15 | 3192 | 0.533 | 0.505 | +2.8 | 2.3 | 0.933 | 25H1 +5.4 / 25H2 +5.3 / 26H1 +3.1 / 26H2 +2.1 |
| London | px_6E | 1 | 216765 | 0.502 | 0.501 | +0.1 | 0.9 | 1.000 | 25H1 -0.9 / 25H2 +1.4 / 26H1 +0.3 / 26H2 -1.1 |
| London | px_6A | 1 | 114623 | 0.505 | 0.501 | +0.5 | 2.1 | 1.000 | 25H1 +0.2 / 25H2 +1.9 / 26H1 +0.4 / 26H2 -1.0 |
| London | px_HG | 1 | 124881 | 0.509 | 0.499 | +0.9 | 4.4 | 0.002 | 25H1 +0.4 / 25H2 +1.2 / 26H1 +1.2 / 26H2 +0.5 |
| London | ref_px_ES | 1 | 21698 | 0.532 | 0.499 | +3.3 | 6.5 | 0.000 | 25H1 +3.5 / 25H2 +6.7 / 26H1 +3.5 / 26H2 +1.1 |

## 4. Table 3: selected on fit, judged once (all feeds, NQ-FLAT variant; rows with a non-NEVER label)
| session | feed | w | h | fires/mo | judge hit | null | edge pp | z | q | follow bp | by half-year edge pp | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | fl_6E | 1 | 1 | 4873 | 0.499 | 0.497 | +0.3 | 0.7 | 1.000 | 0.004 | 25H1 +0.7 / 25H2 +2.2 / 26H1 +1.7 / 26H2 -0.0 | +0.2 | +0.0 | SOMETIMES (noise level, q>0.10) |
| Asia | fl_6J | 5 | 300 | 1283 | 0.505 | 0.501 | +0.3 | 0.5 | 1.000 | -0.001 | 25H1 +1.6 / 25H2 -1.1 / 26H1 +0.8 / 26H2 +0.1 | -0.7 | +0.2 | SOMETIMES (noise level, q>0.10) |
| Asia | fl_AAPL | 5 | 5 | 29 | 0.551 | 0.505 | +4.6 | 0.9 | 1.000 | 0.032 | 25H1 +2.9 / 25H2 +3.7 / 26H1 +7.2 / 26H2 +0.8 | -1.7 | +0.6 | SOMETIMES (noise level, q>0.10) |
| Asia | fl_AMZN | 60 | 300 | 20 | 0.535 | 0.533 | +0.3 | 0.0 | 1.000 | 1.062 | 25H1 +4.6 / 25H2 +5.0 / 26H1 +1.7 / 26H2 +2.0 | +4.9 | +3.3 | SOMETIMES (noise level, q>0.10) |
| Asia | fl_BASKET8 | 1 | 1 | 137 | 0.509 | 0.493 | +1.6 | 0.7 | 1.000 | -0.004 | 25H1 +5.9 / 25H2 +1.3 / 26H1 +1.2 / 26H2 +3.8 | +4.0 | +1.7 | SOMETIMES (noise level, q>0.10) |
| Asia | fl_GOOGL | 1 | 1 | 9 | 0.567 | 0.474 | +9.3 | 1.0 | 1.000 | 0.067 | 25H1 +7.3 / 25H2 +3.0 / 26H1 na / 26H2 +8.5 |  | +8.1 | SOMETIMES (noise level, q>0.10) |
| Asia | fl_MSFT | 1 | 1 | 17 | 0.504 | 0.442 | +6.2 | 0.9 | 1.000 | 0.017 | 25H1 +7.2 / 25H2 +3.3 / 26H1 +6.9 / 26H2 +6.4 |  | +7.8 | SOMETIMES (noise level, q>0.10) |
| Asia | fl_QQQ | 15 | 300 | 35 | 0.541 | 0.529 | +1.2 | 0.3 | 1.000 | 0.388 | 25H1 +10.8 / 25H2 +6.4 / 26H1 -1.1 / 26H2 -1.6 | +1.7 | +0.5 | SOMETIMES (noise level, q>0.10) |
| Asia | fl_SPY | 5 | 5 | 31 | 0.532 | 0.496 | +3.5 | 0.7 | 1.000 | 0.070 | 25H1 +4.8 / 25H2 -2.9 / 26H1 -1.3 / 26H2 +15.1 | +15.7 | +6.3 | SOMETIMES (noise level, q>0.10) |
| Asia | fl_YM | 1 | 1 | 5884 | 0.501 | 0.500 | +0.1 | 0.4 | 1.000 | 0.003 | 25H1 +1.3 / 25H2 +1.1 / 26H1 +0.4 / 26H2 +0.2 | -0.1 | +0.2 | SOMETIMES (noise level, q>0.10) |
| Asia | fl_ZB | 5 | 300 | 943 | 0.511 | 0.501 | +1.0 | 1.1 | 1.000 | 0.202 | 25H1 +3.0 / 25H2 +0.9 / 26H1 +1.0 / 26H2 +0.9 | +0.8 | +1.2 | SOMETIMES (noise level, q>0.10) |
| Asia | imb_ZB | 60 | 60 | 504 | 0.503 | 0.487 | +1.6 | 1.3 | 1.000 | 0.005 | 25H1 +3.5 / 25H2 -0.4 / 26H1 +0.6 / 26H2 +1.4 | +2.0 | +1.4 | SOMETIMES (noise level, q>0.10) |
| Asia | px_6A | 1 | 1 | 6840 | 0.504 | 0.499 | +0.5 | 1.5 | 1.000 | 0.006 | 25H1 +1.0 / 25H2 +3.1 / 26H1 +1.3 / 26H2 +0.2 | +0.4 | +0.4 | SOMETIMES (noise level, q>0.10) |
| Asia | px_6E | 1 | 1 | 8043 | 0.504 | 0.500 | +0.5 | 1.5 | 1.000 | 0.007 | 25H1 +0.4 / 25H2 +2.3 / 26H1 +1.2 / 26H2 +0.3 | -0.1 | +0.3 | SOMETIMES (noise level, q>0.10) |
| Asia | px_HG | 1 | 1 | 7976 | 0.506 | 0.499 | +0.7 | 2.3 | 0.475 | 0.008 | 25H1 +0.7 / 25H2 +1.3 / 26H1 +1.1 / 26H2 +0.6 | +0.4 | +0.7 | SOMETIMES (noise level, q>0.10) |
| Asia | px_NKD | 5 | 300 | 913 | 0.505 | 0.504 | +0.1 | 0.1 | 1.000 | 0.046 | 25H1 +1.0 / 25H2 +1.3 / 26H1 -0.2 / 26H2 +0.1 | -1.5 | +0.2 | SOMETIMES (noise level, q>0.10) |
| Asia | px_NVDA | 15 | 300 | 19 | 0.477 | 0.469 | +0.8 | 0.1 | 1.000 | -0.364 | 25H1 +2.5 / 25H2 +2.9 / 26H1 +2.9 / 26H2 +10.7 |  | +1.8 | SOMETIMES (noise level, q>0.10) |
| Asia | px_YM | 1 | 1 | 7164 | 0.503 | 0.501 | +0.2 | 0.5 | 1.000 | 0.004 | 25H1 +0.9 / 25H2 +0.8 / 26H1 +0.1 / 26H2 +0.1 | -0.4 | +0.2 | SOMETIMES (noise level, q>0.10) |
| Asia | ref_px_ES | 1 | 1 | 2987 | 0.522 | 0.499 | +2.4 | 4.6 | 0.001 | 0.010 | 25H1 +7.5 / 25H2 +7.1 / 26H1 +3.9 / 26H2 +1.9 | +1.9 | +2.0 | STEADY LEADER |
| Asia | ref_px_RTY | 1 | 1 | 5235 | 0.514 | 0.497 | +1.7 | 4.4 | 0.001 | 0.011 | 25H1 +4.0 / 25H2 +3.1 / 26H1 +1.9 / 26H2 +1.6 | +1.5 | +1.7 | STEADY LEADER |
| London | fl_BASKET8 | 1 | 1 | 503 | 0.503 | 0.492 | +1.2 | 0.9 | 1.000 | 0.004 | 25H1 +5.3 / 25H2 +3.4 / 26H1 +1.6 / 26H2 +0.1 | -0.7 | +0.9 | SOMETIMES (noise level, q>0.10) |
| London | fl_GOOGL | 5 | 5 | 97 | 0.501 | 0.483 | +1.9 | 0.7 | 1.000 | 0.015 | 25H1 +5.3 / 25H2 +3.1 / 26H1 +5.3 / 26H2 -0.8 | -1.6 | +2.0 | SOMETIMES (noise level, q>0.10) |
| London | fl_META | 60 | 60 | 90 | 0.519 | 0.508 | +1.1 | 0.4 | 1.000 | 0.035 | 25H1 +2.8 / 25H2 +3.5 / 26H1 +2.4 / 26H2 -0.7 | +1.4 | +0.4 | SOMETIMES (noise level, q>0.10) |
| London | fl_QQQ | 60 | 60 | 434 | 0.500 | 0.499 | +0.1 | 0.1 | 1.000 | -0.026 | 25H1 +6.2 / 25H2 +4.1 / 26H1 +1.3 / 26H2 -0.8 | -0.5 | +1.1 | SOMETIMES (noise level, q>0.10) |
| London | fl_SPY | 15 | 300 | 247 | 0.515 | 0.494 | +2.1 | 1.3 | 1.000 | -0.172 | 25H1 +2.2 / 25H2 +3.3 / 26H1 -1.4 / 26H2 +7.8 | +9.2 | +3.0 | SOMETIMES (noise level, q>0.10) |
| London | imb_6E | 60 | 60 | 596 | 0.497 | 0.493 | +0.4 | 0.4 | 1.000 | 0.031 | 25H1 +1.3 / 25H2 +0.5 / 26H1 +0.5 / 26H2 -0.4 | +0.8 | +0.2 | SOMETIMES (noise level, q>0.10) |
| London | imb_6J | 60 | 300 | 293 | 0.518 | 0.506 | +1.2 | 0.8 | 1.000 | 0.337 | 25H1 -0.0 / 25H2 +3.7 / 26H1 +1.2 / 26H2 +1.6 | +3.4 | +1.7 | SOMETIMES (noise level, q>0.10) |
| London | imb_NKD | 15 | 15 | 263 | 0.533 | 0.509 | +2.4 | 1.5 | 1.000 | 0.077 | 25H1 +5.4 / 25H2 +5.3 / 26H1 +3.1 / 26H2 +2.1 | +2.6 | +2.8 | SOMETIMES (noise level, q>0.10) |
| London | imb_YM | 15 | 300 | 555 | 0.514 | 0.499 | +1.4 | 1.3 | 1.000 | 0.086 | 25H1 +3.0 / 25H2 +0.7 / 26H1 +0.1 / 26H2 +1.3 | +1.3 | +1.3 | SOMETIMES (noise level, q>0.10) |
| London | px_6J | 60 | 60 | 569 | 0.502 | 0.494 | +0.8 | 0.7 | 1.000 | -0.009 | 25H1 -1.8 / 25H2 +1.9 / 26H1 +0.2 / 26H2 +1.7 | +2.3 | +1.1 | SOMETIMES (noise level, q>0.10) |
| London | px_AMZN | 5 | 5 | 17 | 0.525 | 0.517 | +0.8 | 0.1 | 1.000 | -0.013 | 25H1 +1.0 / 25H2 +3.0 / 26H1 +8.2 / 26H2 -1.8 | -4.9 | +1.6 | SOMETIMES (noise level, q>0.10) |
| London | px_AVGO | 15 | 15 | 18 | 0.558 | 0.439 | +11.9 | 1.9 | 0.854 | 0.168 | 25H1 +0.9 / 25H2 +3.5 / 26H1 +15.9 / 26H2 +17.0 |  | +12.0 | SOMETIMES (noise level, q>0.10) |
| London | px_HG | 1 | 1 | 6543 | 0.509 | 0.500 | +0.9 | 2.6 | 0.290 | 0.008 | 25H1 +0.4 / 25H2 +1.2 / 26H1 +1.2 / 26H2 +0.5 | +0.3 | +0.8 | SOMETIMES (noise level, q>0.10) |
| London | px_NKD | 15 | 300 | 384 | 0.516 | 0.501 | +1.5 | 1.1 | 1.000 | 0.159 | 25H1 -2.8 / 25H2 +0.5 / 26H1 +0.6 / 26H2 +1.9 | +1.8 | +2.4 | SOMETIMES (noise level, q>0.10) |
| London | px_TSLA | 1 | 1 | 55 | 0.552 | 0.512 | +4.1 | 1.1 | 1.000 | 0.041 | 25H1 +2.1 / 25H2 +2.6 / 26H1 -0.5 / 26H2 +3.6 | +3.1 | +2.4 | SOMETIMES (noise level, q>0.10) |
| London | ref_px_ES | 1 | 1 | 1758 | 0.514 | 0.498 | +1.6 | 2.4 | 0.379 | 0.009 | 25H1 +3.5 / 25H2 +6.7 / 26H1 +3.5 / 26H2 +1.1 | +0.9 | +1.6 | SOMETIMES (noise level, q>0.10) |
| NY AM | fl_6J | 5 | 5 | 1911 | 0.505 | 0.502 | +0.2 | 0.4 | 1.000 | 0.018 | 25H1 +0.0 / 25H2 +0.8 / 26H1 +0.2 / 26H2 +0.7 | +1.0 | +0.3 | SOMETIMES (noise level, q>0.10) |
| NY AM | fl_AAPL | 5 | 300 | 363 | 0.504 | 0.501 | +0.3 | 0.2 | 1.000 | 0.025 | 25H1 +2.4 / 25H2 +0.5 / 26H1 -1.3 / 26H2 +1.7 | +0.0 | +0.7 | SOMETIMES (noise level, q>0.10) |
| NY AM | fl_AMZN | 5 | 5 | 1162 | 0.515 | 0.499 | +1.6 | 2.0 | 0.854 | 0.014 | 25H1 +0.0 / 25H2 +2.5 / 26H1 +0.8 / 26H2 +2.2 | +2.3 | +2.0 | SOMETIMES (noise level, q>0.10) |
| NY AM | fl_AVGO | 300 | 300 | 130 | 0.485 | 0.483 | +0.2 | 0.1 | 1.000 | -0.247 | 25H1 +6.4 / 25H2 +1.1 / 26H1 +2.0 / 26H2 -0.5 | -0.3 | +0.2 | SOMETIMES (noise level, q>0.10) |
| NY AM | fl_QQQ | 15 | 15 | 1088 | 0.514 | 0.508 | +0.7 | 0.8 | 1.000 | 0.086 | 25H1 +0.6 / 25H2 +0.6 / 26H1 -0.2 / 26H2 +1.3 | +0.9 | +1.2 | SOMETIMES (noise level, q>0.10) |
| NY AM | fl_YM | 5 | 300 | 483 | 0.498 | 0.490 | +0.8 | 0.7 | 1.000 | -0.198 | 25H1 +1.7 / 25H2 +1.6 / 26H1 +0.8 / 26H2 +0.3 | -0.4 | +0.3 | SOMETIMES (noise level, q>0.10) |
| NY AM | fl_ZB | 60 | 60 | 338 | 0.499 | 0.484 | +1.5 | 1.0 | 1.000 | 0.054 | 25H1 +2.6 / 25H2 +2.5 / 26H1 +1.2 / 26H2 +2.4 | +3.7 | +2.0 | SOMETIMES (noise level, q>0.10) |
| NY AM | imb_6E | 5 | 5 | 36 | 0.524 | 0.509 | +1.5 | 0.3 | 1.000 | 0.102 | 25H1 -1.5 / 25H2 +4.8 / 26H1 +1.2 / 26H2 +3.2 |  | +1.5 | SOMETIMES (noise level, q>0.10) |
| NY AM | imb_NKD | 1 | 300 | 77 | 0.506 | 0.475 | +3.1 | 1.0 | 1.000 | -0.535 | 25H1 na / 25H2 na / 26H1 +2.8 / 26H2 +4.3 | +7.5 | +3.1 | SOMETIMES (noise level, q>0.10) |
| NY AM | imb_ZB | 300 | 300 | 124 | 0.502 | 0.476 | +2.7 | 1.1 | 1.000 | 0.163 | 25H1 -1.2 / 25H2 +1.6 / 26H1 +6.1 / 26H2 +1.7 | -0.5 | +2.4 | SOMETIMES (noise level, q>0.10) |
| NY AM | px_6J | 5 | 300 | 532 | 0.506 | 0.503 | +0.3 | 0.3 | 1.000 | 0.136 | 25H1 +1.7 / 25H2 -1.0 / 26H1 +1.2 / 26H2 +0.1 | +1.0 | +0.0 | SOMETIMES (noise level, q>0.10) |
| NY AM | px_AMZN | 5 | 300 | 377 | 0.506 | 0.496 | +1.0 | 0.7 | 1.000 | 0.048 | 25H1 +0.6 / 25H2 +1.2 / 26H1 +2.7 / 26H2 -0.7 | -1.6 | +0.0 | SOMETIMES (noise level, q>0.10) |
| NY AM | px_AVGO | 300 | 300 | 32 | 0.498 | 0.492 | +0.6 | 0.1 | 1.000 | -0.697 | 25H1 +8.5 / 25H2 +10.3 / 26H1 +3.6 / 26H2 +5.9 | +7.7 | +0.6 | SOMETIMES (noise level, q>0.10) |
| NY AM | px_GOOGL | 60 | 300 | 98 | 0.520 | 0.490 | +3.0 | 1.1 | 1.000 | 0.160 | 25H1 +6.2 / 25H2 +6.0 / 26H1 -1.8 / 26H2 +4.2 | +5.4 | +3.1 | SOMETIMES (noise level, q>0.10) |
| NY AM | px_MSFT | 60 | 60 | 143 | 0.505 | 0.487 | +1.8 | 0.8 | 1.000 | 0.130 | 25H1 +7.0 / 25H2 +0.5 / 26H1 +3.3 / 26H2 +1.3 | +0.4 | +1.3 | SOMETIMES (noise level, q>0.10) |
| NY AM | px_NKD | 15 | 300 | 321 | 0.507 | 0.503 | +0.4 | 0.3 | 1.000 | 0.187 | 25H1 -0.3 / 25H2 +1.5 / 26H1 +1.4 / 26H2 +0.6 | +1.0 | +0.7 | SOMETIMES (noise level, q>0.10) |
| NY AM | px_TSLA | 15 | 15 | 538 | 0.501 | 0.501 | +0.0 | 0.0 | 1.000 | 0.070 | 25H1 -0.8 / 25H2 +3.3 / 26H1 +2.2 / 26H2 -2.5 | -4.1 | +0.0 | SOMETIMES (noise level, q>0.10) |
| NY AM | ref_px_ES | 1 | 1 | 515 | 0.523 | 0.491 | +3.3 | 2.7 | 0.277 | 0.007 | 25H1 -1.2 / 25H2 +2.4 / 26H1 +1.4 / 26H2 +3.6 | +2.2 | +3.5 | SOMETIMES (noise level, q>0.10) |
| NY AM | ref_px_RTY | 1 | 300 | 505 | 0.512 | 0.503 | +0.9 | 0.8 | 1.000 | 0.332 | 25H1 -0.2 / 25H2 +0.7 / 26H1 +0.8 / 26H2 +1.7 | +2.6 | +1.0 | SOMETIMES (noise level, q>0.10) |
| NY PM | fl_6E | 1 | 300 | 598 | 0.501 | 0.495 | +0.7 | 0.6 | 1.000 | -0.038 | 25H1 +2.0 / 25H2 -0.2 / 26H1 +1.5 / 26H2 +0.7 | -0.2 | +0.3 | SOMETIMES (noise level, q>0.10) |
| NY PM | fl_6J | 300 | 300 | 129 | 0.503 | 0.490 | +1.3 | 0.5 | 1.000 | -0.220 | 25H1 -1.8 / 25H2 +6.5 / 26H1 -0.3 / 26H2 +2.1 | +5.2 | +1.9 | SOMETIMES (noise level, q>0.10) |
| NY PM | fl_AMZN | 5 | 5 | 1554 | 0.493 | 0.493 | +0.0 | 0.0 | 1.000 | 0.005 | 25H1 -0.9 / 25H2 +0.8 / 26H1 -0.2 / 26H2 +0.8 | +1.5 | +0.2 | SOMETIMES (noise level, q>0.10) |
| NY PM | fl_AVGO | 300 | 300 | 140 | 0.496 | 0.495 | +0.2 | 0.1 | 1.000 | -0.079 | 25H1 +4.1 / 25H2 +1.0 / 26H1 -0.4 / 26H2 +2.8 | +1.4 | +1.1 | SOMETIMES (noise level, q>0.10) |
| NY PM | fl_BASKET8 | 1 | 1 | 2660 | 0.503 | 0.497 | +0.7 | 1.2 | 1.000 | 0.001 | 25H1 -2.3 / 25H2 +0.7 / 26H1 +0.1 / 26H2 +1.3 | +1.4 | +0.7 | SOMETIMES (noise level, q>0.10) |
| NY PM | fl_NKD | 1 | 300 | 465 | 0.503 | 0.493 | +1.0 | 0.8 | 1.000 | -0.065 | 25H1 -2.9 / 25H2 +1.3 / 26H1 +2.6 / 26H2 +0.5 | +2.1 | +0.4 | SOMETIMES (noise level, q>0.10) |
| NY PM | fl_QQQ | 1 | 300 | 652 | 0.503 | 0.493 | +1.0 | 0.9 | 1.000 | 0.201 | 25H1 -1.5 / 25H2 +1.7 / 26H1 +3.1 / 26H2 -0.6 | -0.4 | +1.1 | SOMETIMES (noise level, q>0.10) |
| NY PM | fl_SPY | 1 | 300 | 637 | 0.505 | 0.498 | +0.7 | 0.7 | 1.000 | 0.043 | 25H1 +0.2 / 25H2 -0.1 / 26H1 +1.1 / 26H2 +1.3 | -0.1 | +1.1 | SOMETIMES (noise level, q>0.10) |
| NY PM | fl_YM | 5 | 5 | 1860 | 0.505 | 0.499 | +0.6 | 1.0 | 1.000 | 0.012 | 25H1 +2.0 / 25H2 +1.2 / 26H1 -0.5 / 26H2 +0.9 | +1.0 | +1.0 | SOMETIMES (noise level, q>0.10) |
| NY PM | fl_ZB | 1 | 300 | 535 | 0.491 | 0.486 | +0.5 | 0.4 | 1.000 | 0.007 | 25H1 +5.8 / 25H2 +0.9 / 26H1 +1.1 / 26H2 +0.8 | -1.0 | +0.5 | SOMETIMES (noise level, q>0.10) |
| NY PM | imb_NKD | 5 | 300 | 46 | 0.509 | 0.498 | +1.1 | 0.3 | 1.000 | 0.260 | 25H1 na / 25H2 na / 26H1 +2.6 / 26H2 +0.9 | +3.2 | +0.9 | SOMETIMES (noise level, q>0.10) |
| NY PM | imb_YM | 5 | 5 | 2758 | 0.498 | 0.496 | +0.3 | 0.5 | 1.000 | 0.001 | 25H1 -0.6 / 25H2 +1.5 / 26H1 +0.3 / 26H2 -0.1 | -0.1 | +0.0 | SOMETIMES (noise level, q>0.10) |
| NY PM | px_6J | 5 | 5 | 4228 | 0.502 | 0.500 | +0.2 | 0.5 | 1.000 | 0.001 | 25H1 +0.9 / 25H2 +0.8 / 26H1 +0.6 / 26H2 +0.1 | +0.4 | +0.0 | SOMETIMES (noise level, q>0.10) |
| NY PM | px_AMZN | 15 | 15 | 1208 | 0.498 | 0.494 | +0.4 | 0.5 | 1.000 | 0.015 | 25H1 -0.5 / 25H2 +3.1 / 26H1 -0.1 / 26H2 +0.4 | +0.6 | +0.2 | SOMETIMES (noise level, q>0.10) |
| NY PM | px_AVGO | 60 | 60 | 285 | 0.507 | 0.502 | +0.4 | 0.3 | 1.000 | 0.041 | 25H1 -0.9 / 25H2 +0.8 / 26H1 +2.2 / 26H2 +0.6 | +2.6 | +0.4 | SOMETIMES (noise level, q>0.10) |
| NY PM | px_HG | 60 | 60 | 296 | 0.498 | 0.498 | +0.0 | 0.0 | 1.000 | 0.029 | 25H1 +0.2 / 25H2 +1.3 / 26H1 +0.8 / 26H2 -0.5 | -3.5 | +0.3 | SOMETIMES (noise level, q>0.10) |
| NY PM | px_MSFT | 5 | 5 | 2840 | 0.500 | 0.497 | +0.3 | 0.6 | 1.000 | -0.003 | 25H1 +1.4 / 25H2 -0.1 / 26H1 +1.2 / 26H2 +0.1 | -0.4 | +0.4 | SOMETIMES (noise level, q>0.10) |
| NY PM | px_NKD | 15 | 300 | 293 | 0.508 | 0.501 | +0.7 | 0.4 | 1.000 | 0.146 | 25H1 -1.2 / 25H2 +1.3 / 26H1 +1.5 / 26H2 -0.2 | +1.8 | +0.5 | SOMETIMES (noise level, q>0.10) |
| NY PM | px_QQQ | 1 | 300 | 837 | 0.502 | 0.497 | +0.5 | 0.6 | 1.000 | 0.025 | 25H1 +1.2 / 25H2 +0.5 / 26H1 +0.4 / 26H2 +0.1 | -0.0 | +0.6 | SOMETIMES (noise level, q>0.10) |
| NY PM | px_TSLA | 60 | 300 | 252 | 0.489 | 0.468 | +2.0 | 1.2 | 1.000 | -0.115 | 25H1 -3.1 / 25H2 +4.2 / 26H1 +1.8 / 26H2 +1.2 | +0.9 | +2.7 | SOMETIMES (noise level, q>0.10) |
| NY PM | ref_px_ES | 1 | 1 | 441 | 0.537 | 0.496 | +4.1 | 2.8 | 0.260 | 0.009 | 25H1 +7.8 / 25H2 +2.9 / 26H1 +2.1 / 26H2 +4.6 | +5.0 | +3.8 | SOMETIMES (noise level, q>0.10) |

Counts by label (all variants): Counter({'NEVER': 180, 'SOMETIMES (noise level, q>0.10)': 131, 'STEADY LEADER': 2})

## 5. Same moment (correlation with NQ over the same window; after the +1 s shift)
| session | window | top feeds (corr) |
|---|---|---|
| Asia | 1 s | ref_px_ES 0.77, ref_px_RTY 0.62, px_YM 0.28, fl_YM 0.20, px_SPY 0.10, px_6A 0.10, px_NKD 0.09, px_QQQ 0.08 |
| Asia | 60 s | ref_px_ES 0.85, ref_px_RTY 0.73, px_QQQ 0.73, px_YM 0.68, px_SPY 0.49, px_NKD 0.47, px_MSFT 0.32, px_6A 0.30 |
| London | 1 s | ref_px_ES 0.85, ref_px_RTY 0.70, px_YM 0.37, fl_YM 0.23, px_NKD 0.17, px_SPY 0.16, px_6A 0.16, px_QQQ 0.12 |
| London | 60 s | ref_px_ES 0.94, ref_px_RTY 0.77, px_YM 0.71, px_SPY 0.66, px_QQQ 0.64, px_NKD 0.64, px_BASKET8 0.50, px_NVDA 0.47 |
| NY AM | 1 s | ref_px_ES 0.88, ref_px_RTY 0.61, px_BASKET8 0.52, px_NVDA 0.43, px_SPY 0.42, px_QQQ 0.40, px_YM 0.39, px_TSLA 0.27 |
| NY AM | 60 s | px_QQQ 0.96, ref_px_ES 0.91, px_SPY 0.89, px_BASKET8 0.81, px_NVDA 0.67, px_NKD 0.66, ref_px_RTY 0.63, px_AVGO 0.60 |
| NY PM | 1 s | ref_px_ES 0.90, ref_px_RTY 0.75, px_BASKET8 0.57, px_YM 0.51, px_SPY 0.48, px_NVDA 0.45, px_QQQ 0.41, px_TSLA 0.30 |
| NY PM | 60 s | px_QQQ 0.97, ref_px_ES 0.95, px_SPY 0.93, px_BASKET8 0.89, ref_px_RTY 0.78, px_YM 0.76, px_NVDA 0.74, px_NKD 0.67 |
