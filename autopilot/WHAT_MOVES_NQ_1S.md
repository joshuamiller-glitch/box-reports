# WHAT_MOVES_NQ_1S: the WHAT_MOVES_NQ method rerun at 1 second with the new feeds. DISCOVERY, NOT A RESULT
Generated 2026-11-28T12:07Z. Order: relay directive 0552Z (autopilot/DIRECTIVE_0552Z_what-moves-nq-1s.md). Label: DISCOVERY. It only feeds which feeds sit on which desk seat; nothing here is a trading rule. Old page (not overwritten): autopilot/WHAT_MOVES_NQ.md.

Code: code/th_dynl/wm1s_conv.py (dbn to per-second tables), wm1s_run.py (reuses wm_run.stats_for, same matched null), wm1s_agg.py, wm1s_turns.py, wm1s_turn_agg.py, wm1s_page.py. Monthly counts backed up in /mnt/l2/l2vast/_dynexit/wm1s_backup/.

## ANSWER FIRST
Scope: all 19 months (2025-05..2026-11) for the lead tests (turns: 19 months, 4,200+ NQ turns), windows 1/5/15/60/300 s, four sessions, by half-year, BH over ~2,900 grid cells. Everything below is DISCOVERY and only says which feed could sit on which desk seat.

1. MEGACAPS BELOW ONE MINUTE IN NY AM / NY PM: NO. Neither any single megacap (NVDA MSFT AAPL AMZN META GOOGL AVGO TSLA), nor QQQ/SPY, nor the 8-name basket (price or signed trade flow) leads NQ at 1/5/15/60 s in NY AM or NY PM once NQ itself has not moved: best rows are +0.0 to +3.8 pp with z <= 1.0 and BH q = 1.0 (the basket in NY AM: best +2.1 pp at 300 s, z 0.8, and its follow move flips sign by half-year). They move WITH NQ in the same second (megacap/basket correlation with NQ is high at lag 0) and NQ is simply the faster instrument; NQ is the market the megacaps are priced off at this horizon. Only trace: the basket's signed trade flow in London at 1 s (+3.2 pp, z 4.5, q 0.001, but only 11k fires, edge fades by half-year +5.3 / +3.4 / +1.6 / +0.1, follow 0.014 bp): SOMETIMES, not a seat feed.
2. YM, ZB, 6J, NKD IN ASIA AND LONDON: NO. None of the four (price, signed flow, top-of-book imbalance) shows a BH-significant lead in either session: Asia best +0.3 to +0.9 pp (z <= 2.3, q >= 0.68), London best +0.2 to +2.0 pp (z <= 2.0, q = 1.0). What DOES lead, steadily and tiny, in Asia: 6A and 6E (price +1.5 / +1.1 pp at 1 s, z 8.2 / 6.5, positive in all four half-years but shrinking; 6E flow +1.3 pp) and copper HG (+1.0 pp in Asia, +0.9 pp in London at 1 s; HG London is the only new feed labelled STEADY LEADER by the selection rule). Follow move 0.007-0.011 bp (about 0.02-0.03 NQ points): far below a tick. The old reference lead stays the largest: ES moves lead NQ at 1 s by +4.0 pp Asia, +3.6 pp London and +3.2 pp NY PM (NQ-flat, q <= 0.02), RTY +2.5 pp Asia; both fade across half-years (ES Asia +7.5 / +6.8 / +3.9 / +1.9).
3. WHICH LEAD NQ TURNS: TURNS (reversals), London only: signed trade flow of NVDA (turns ~38 s before NQ's extreme vs +23 s on random windows; share of turns with the feed >= 5 s earlier +20.1 pp over null, z 3.9; positive in all four half-years +9.0 / +6.2 / +8.1 / +22.8) and TSLA (-14 s vs +43 s null, +19.2 pp, z 3.4, +6.7 / +2.5 / +12.5 / +13.5) carry the label STEADY LEADER; QQQ flow and price, AVGO price, 6E book imbalance and NKD price are SOMETIMES (z 2.6-3.3, one or two half-years flat). NY AM, NY PM and Asia: NO steady turn leader (best NY AM SPY flow z 2.8, NY PM AAPL flow z 2.7, both SOMETIMES, with a negative first half-year). Caveats, plainly: turn study is descriptive (turn time defined with hindsight, no BH; about 146 feed x session rows so 2 labels at z ~3.4-3.9 is only modestly beyond luck); London megacap rows are PRE-MARKET prints (04:00-08:30 ET, thin), and the sparse series are forward/back-filled inside each 600 s window, which can bias a lead; the 'null' medians are positive for these feeds (+23 to +43 s), so the contrast partly reflects the null's lag structure. Treat as a LEAD to test, not a result.
Plain statement: apart from ES/RTY (already known) and FX/copper in Asia at 1 second, with sub-tick follow moves, NOTHING in these new feeds leads NQ in the matched-null test. The one "result" that looked dramatic (20-37 pp edges, basket 84-87 percent hit) was a one-second timestamp look-ahead and is void. The new feeds' value is as CONFIRMATION/context (they move with NQ), not as early warning.

## 1. Method (identical to WHAT_MOVES_NQ.md unless stated)
- NQ grid: NQ mid per second (the old age_ feed), 19 months 2025-05..2026-11. Feed move over the last w seconds (w = 1/5/15/60/300 s), scaled by its own rolling std over the previous 3600 s; FIRE at >= 2 sigma; NQ-FLAT variant = NQ itself has not moved yet (< 0.5 sigma). Outcome = NQ return over the next h seconds (h = w and 300 s); HIT = same sign as the feed (sign fixed on the first 60% of the months by same-moment covariance); refractory max(w,h). MATCHED NULL = same fires scored against NQ outcomes 30-120 min later. Edge = hit - null.
- Feeds: EQUS.MINI 1-s bars for NVDA MSFT AAPL AMZN META GOOGL AVGO TSLA QQQ SPY (px_), their signed trade flow from EQUS.MINI trades (fl_, dollar-signed), the equal-weight 8-megacap basket (px_BASKET8 = mean 1-s log return, needs >= 3 live names; fl_BASKET8 = summed signed dollar flow), GLBX 1-s bars YM ZB 6E 6J NKD 6A HG (px_), tbbo signed trade size (fl_) and top-of-book size imbalance at the last trade (imb_) for YM ZB 6E 6J NKD. Reference rows ref_px_ES / ref_px_RTY come from the old ES/RTY mid feed. Roll jumps in .v.0 series are removed (|1-s move| > 40 bp futures, > 150 bp stocks set to 0); price forward-filled at most 60 s.
- TIMING FIX (important): Databento bars and trades are stamped at the START of their second. A bar stamped t is complete only at t+1. Unshifted, the feeds correlated with NQ at lag 1 and the first run printed fake 20-37 pp 1-second "leads" (basket 84-87 percent hit): look-ahead of one second. That first run is VOID and was deleted; every feed is now shifted +1 s so a bar is used only once complete (check: after the shift the basket/YM correlate with NQ at lag 0). Residual: a feed bar closing at second t and the NQ mid at second t are the same instant, so "lead" below means the NEXT seconds of NQ.
- DEGRADED DATA: EQUS.MINI days named by the coordinator (2025-05-06, 2025-06-04, 2025-06-16) plus 2025-12-24 (half day, under 50 percent of the median row count) are EXCLUDED from every megacap/QQQ/SPY price and flow row (set to missing). Only these four were identifiable without calling the conditions API; if the conditions API lists more EQUS.MINI days, they are NOT excluded here (the page says so rather than guessing). For GLBX series, days under 50 percent of the median row count (holidays, half days) and 2026-11-01 are excluded.
- Sessions (ET of fire time): Asia 18:00-03:00, London 03:00-08:30, NY AM 08:30-12:00, NY PM 12:00-16:00. Premarket/after-hours stock prints exist (EQUS.MINI) but are thin: megacap rows in Asia/London have few fires per month (column "fires").
- By HALF-YEAR: 2025H1 = May-Jun only, 2025H2, 2026H1, 2026H2 = Jul-Nov (stocks to 2026-10-31, futures to 2026-11-13 where NQ grid exists).
- Selection (table 3): per feed, session, variant the (w,h) with best edge z on the FIT months (first 60 percent of months) is judged ONCE on the last 40 percent; BH q over all judged rows. Labels: STEADY LEADER = judge edge >= 1.0 pp, BH q <= 0.10, positive in >= 75 percent of half-years with >= 200 fires and at least 3 such half-years, positive in L3M and L6M. SOMETIMES = positive on the judge set and (q <= 0.10 or positive in L6M). NEVER otherwise. NOTE: the inherited SOMETIMES rule is loose (it passes anything positive in the last 6 months); rows with q > 0.10 are printed as "SOMETIMES (noise level)" and should be read as NEVER.
- Full grid (table 1/2): every (feed, session, variant, w=h) over the whole window with BH over all 2946 grid cells (10 cells have q <= 0.10 and edge >= 1 pp).

## 2. Table 1: megacaps / basket / QQQ / SPY vs NQ, NY AM and NY PM, horizons up to 60 s (best w=h per row on the whole window; NQ-FLAT variant; ES reference last)
| session | feed | w=h (s) | fires | hit | null | edge pp | z | BH q | by half-year edge pp |
|---|---|---|---|---|---|---|---|---|---|
| NY AM | px_BASKET8 | 15 | 6653 | 0.499 | 0.494 | +0.5 | 0.6 | 1.000 | 25H1 +2.6 / 25H2 +3.3 / 26H1 -1.1 / 26H2 -0.9 |
| NY AM | fl_BASKET8 | 15 | 18335 | 0.501 | 0.500 | +0.1 | 0.2 | 1.000 | 25H1 -1.1 / 25H2 +0.4 / 26H1 +1.3 / 26H2 -1.7 |
| NY AM | px_NVDA | 60 | 2676 | 0.502 | 0.498 | +0.4 | 0.3 | 1.000 | 25H1 +2.4 / 25H2 -0.2 / 26H1 +1.6 / 26H2 -1.7 |
| NY AM | px_MSFT | 60 | 2340 | 0.515 | 0.495 | +2.0 | 1.4 | 1.000 | 25H1 +7.0 / 25H2 -0.7 / 26H1 +3.3 / 26H2 +1.3 |
| NY AM | px_AAPL | 15 | 10279 | 0.502 | 0.501 | +0.1 | 0.2 | 1.000 | 25H1 -0.1 / 25H2 -0.2 / 26H1 +1.0 / 26H2 -0.5 |
| NY AM | px_AMZN | 1 | 48813 | 0.501 | 0.501 | +0.0 | 0.1 | 1.000 | 25H1 +0.3 / 25H2 -0.4 / 26H1 -0.1 / 26H2 +0.7 |
| NY AM | px_META | 5 | 20282 | 0.505 | 0.500 | +0.5 | 1.0 | 1.000 | 25H1 +1.6 / 25H2 +0.8 / 26H1 -0.2 / 26H2 +0.4 |
| NY AM | px_GOOGL | 5 | 18469 | 0.508 | 0.498 | +0.9 | 1.8 | 1.000 | 25H1 +0.2 / 25H2 +1.7 / 26H1 -0.0 / 26H2 +1.5 |
| NY AM | px_AVGO | 15 | 6607 | 0.507 | 0.501 | +0.6 | 0.7 | 1.000 | 25H1 +1.9 / 25H2 +0.5 / 26H1 -0.3 / 26H2 +1.7 |
| NY AM | px_TSLA | 15 | 11038 | 0.509 | 0.497 | +1.2 | 1.7 | 1.000 | 25H1 -0.8 / 25H2 +3.1 / 26H1 +2.2 / 26H2 -2.5 |
| NY AM | px_QQQ | 60 | 374 | 0.516 | 0.477 | +3.9 | 1.1 | 1.000 | 25H1 +1.8 / 25H2 +6.7 / 26H1 -0.6 / 26H2 +7.1 |
| NY AM | px_SPY | 60 | 598 | 0.470 | 0.485 | -1.5 | -0.5 | 1.000 | 25H1 +4.1 / 25H2 -5.2 / 26H1 -2.9 / 26H2 +3.6 |
| NY AM | fl_NVDA | 1 | 27287 | 0.502 | 0.502 | +0.0 | 0.0 | 1.000 | 25H1 -1.5 / 25H2 +0.6 / 26H1 +0.3 / 26H2 -0.6 |
| NY AM | fl_QQQ | 15 | 20208 | 0.505 | 0.501 | +0.4 | 0.8 | 1.000 | 25H1 +0.6 / 25H2 +0.3 / 26H1 -0.2 / 26H2 +1.3 |
| NY AM | fl_SPY | 1 | 39740 | 0.500 | 0.499 | +0.1 | 0.3 | 1.000 | 25H1 +0.2 / 25H2 +0.9 / 26H1 -0.4 / 26H2 -0.7 |
| NY AM | ref_px_ES | 1 | 7982 | 0.522 | 0.499 | +2.3 | 2.8 | 0.324 | 25H1 -1.2 / 25H2 +2.5 / 26H1 +1.4 / 26H2 +3.6 |
| NY PM | px_BASKET8 | 1 | 48714 | 0.501 | 0.499 | +0.2 | 0.6 | 1.000 | 25H1 +1.0 / 25H2 +1.7 / 26H1 -1.0 / 26H2 -0.2 |
| NY PM | fl_BASKET8 | 1 | 44908 | 0.502 | 0.498 | +0.4 | 1.0 | 1.000 | 25H1 -2.3 / 25H2 +0.6 / 26H1 +0.1 / 26H2 +1.3 |
| NY PM | px_NVDA | 1 | 83560 | 0.499 | 0.501 | -0.1 | -0.5 | 1.000 | 25H1 -0.4 / 25H2 +0.2 / 26H1 -0.4 / 26H2 -0.0 |
| NY PM | px_MSFT | 5 | 45621 | 0.503 | 0.498 | +0.4 | 1.2 | 1.000 | 25H1 +1.4 / 25H2 -0.2 / 26H1 +1.2 / 26H2 +0.1 |
| NY PM | px_AAPL | 15 | 20350 | 0.499 | 0.498 | +0.0 | 0.1 | 1.000 | 25H1 +0.8 / 25H2 -0.2 / 26H1 +0.2 / 26H2 -0.1 |
| NY PM | px_AMZN | 15 | 17540 | 0.501 | 0.494 | +0.7 | 1.3 | 1.000 | 25H1 -0.5 / 25H2 +2.1 / 26H1 -0.1 / 26H2 +0.4 |
| NY PM | px_META | 60 | 6373 | 0.511 | 0.500 | +1.1 | 1.2 | 1.000 | 25H1 -0.8 / 25H2 +0.9 / 26H1 -0.3 / 26H2 +3.0 |
| NY PM | px_GOOGL | 5 | 44262 | 0.500 | 0.498 | +0.2 | 0.7 | 1.000 | 25H1 +2.5 / 25H2 +0.4 / 26H1 -0.6 / 26H2 +0.3 |
| NY PM | px_AVGO | 60 | 5160 | 0.510 | 0.500 | +1.0 | 1.0 | 1.000 | 25H1 -0.9 / 25H2 +0.6 / 26H1 +2.2 / 26H2 +0.6 |
| NY PM | px_TSLA | 60 | 5914 | 0.499 | 0.501 | -0.1 | -0.1 | 1.000 | 25H1 -2.2 / 25H2 +1.3 / 26H1 -1.1 / 26H2 +0.0 |
| NY PM | px_QQQ | 60 | 111 | 0.568 | 0.542 | +2.6 | 0.4 | 1.000 | 25H1 na / 25H2 na / 26H1 na / 26H2 +6.0 |
| NY PM | px_SPY | 15 | 3264 | 0.505 | 0.501 | +0.4 | 0.3 | 1.000 | 25H1 -1.0 / 25H2 +1.4 / 26H1 +0.1 / 26H2 -0.3 |
| NY PM | fl_NVDA | 1 | 30654 | 0.499 | 0.499 | -0.0 | -0.0 | 1.000 | 25H1 +0.2 / 25H2 +0.5 / 26H1 -0.3 / 26H2 -0.4 |
| NY PM | fl_QQQ | 5 | 40791 | 0.499 | 0.497 | +0.2 | 0.6 | 1.000 | 25H1 +0.2 / 25H2 +0.5 / 26H1 +1.1 / 26H2 -1.6 |
| NY PM | fl_SPY | 1 | 53942 | 0.503 | 0.501 | +0.1 | 0.4 | 1.000 | 25H1 -0.8 / 25H2 +0.2 / 26H1 +0.1 / 26H2 +0.8 |
| NY PM | ref_px_ES | 1 | 9386 | 0.529 | 0.497 | +3.2 | 3.9 | 0.010 | 25H1 +7.8 / 25H2 +2.8 / 26H1 +2.1 / 26H2 +4.6 |

## 3. Table 2: YM, ZB, 6J, NKD (and 6E 6A HG) vs NQ, Asia and London, horizons up to 300 s (best w=h per row; NQ-FLAT)
| session | feed | w=h (s) | fires | hit | null | edge pp | z | BH q | by half-year edge pp |
|---|---|---|---|---|---|---|---|---|---|
| Asia | px_YM | 1 | 116082 | 0.504 | 0.500 | +0.4 | 1.9 | 1.000 | 25H1 +0.9 / 25H2 +1.1 / 26H1 +0.1 / 26H2 +0.1 |
| Asia | fl_YM | 1 | 99139 | 0.507 | 0.501 | +0.7 | 2.7 | 0.444 | 25H1 +1.3 / 25H2 +1.3 / 26H1 +0.4 / 26H2 +0.2 |
| Asia | imb_YM | 60 | 20978 | 0.503 | 0.496 | +0.8 | 1.6 | 1.000 | 25H1 -0.6 / 25H2 +0.8 / 26H1 +0.8 / 26H2 +1.3 |
| Asia | px_ZB | 1 | 30165 | 0.501 | 0.499 | +0.1 | 0.3 | 1.000 | 25H1 +0.9 / 25H2 -0.5 / 26H1 +0.4 / 26H2 -0.1 |
| Asia | fl_ZB | 5 | 45158 | 0.498 | 0.498 | +0.0 | 0.1 | 1.000 | 25H1 +0.4 / 25H2 -0.2 / 26H1 -0.5 / 26H2 +0.9 |
| Asia | imb_ZB | 60 | 9621 | 0.500 | 0.493 | +0.7 | 1.0 | 1.000 | 25H1 +3.5 / 25H2 -0.4 / 26H1 +0.6 / 26H2 +1.4 |
| Asia | px_6J | 5 | 167760 | 0.499 | 0.500 | -0.0 | -0.2 | 1.000 | 25H1 +0.7 / 25H2 +0.0 / 26H1 -0.3 / 26H2 +0.1 |
| Asia | fl_6J | 15 | 52798 | 0.502 | 0.500 | +0.1 | 0.5 | 1.000 | 25H1 -0.2 / 25H2 -0.1 / 26H1 -0.3 / 26H2 +1.2 |
| Asia | imb_6J | 15 | 10626 | 0.502 | 0.499 | +0.3 | 0.5 | 1.000 | 25H1 -0.3 / 25H2 -1.5 / 26H1 +1.0 / 26H2 +0.8 |
| Asia | px_NKD | 300 | 2232 | 0.504 | 0.492 | +1.2 | 0.8 | 1.000 | 25H1 -0.1 / 25H2 +0.2 / 26H1 +2.8 / 26H2 +1.1 |
| Asia | fl_NKD | 1 | 66825 | 0.506 | 0.503 | +0.3 | 0.9 | 1.000 | 25H1 +0.2 / 25H2 +0.3 / 26H1 +0.0 / 26H2 +0.7 |
| Asia | imb_NKD | 1 | 33122 | 0.501 | 0.499 | +0.2 | 0.5 | 1.000 | 25H1 +1.4 / 25H2 +0.9 / 26H1 +0.3 / 26H2 -0.4 |
| Asia | px_6E | 1 | 195046 | 0.511 | 0.500 | +1.1 | 6.5 | 0.000 | 25H1 +0.4 / 25H2 +2.0 / 26H1 +1.2 / 26H2 +0.3 |
| Asia | px_6A | 1 | 166237 | 0.515 | 0.499 | +1.5 | 8.2 | 0.000 | 25H1 +1.0 / 25H2 +3.1 / 26H1 +1.3 / 26H2 +0.2 |
| Asia | px_HG | 1 | 154777 | 0.508 | 0.498 | +1.0 | 5.0 | 0.000 | 25H1 +0.7 / 25H2 +1.1 / 26H1 +1.1 / 26H2 +0.6 |
| Asia | ref_px_ES | 1 | 37669 | 0.539 | 0.499 | +4.0 | 10.2 | 0.000 | 25H1 +7.5 / 25H2 +6.8 / 26H1 +3.9 / 26H2 +1.9 |
| London | px_YM | 300 | 1907 | 0.488 | 0.499 | -1.1 | -0.7 | 1.000 | 25H1 -4.6 / 25H2 +0.7 / 26H1 -2.0 / 26H2 -1.3 |
| London | fl_YM | 300 | 3703 | 0.504 | 0.493 | +1.1 | 1.0 | 1.000 | 25H1 -3.9 / 25H2 -1.5 / 26H1 +4.0 / 26H2 +2.9 |
| London | imb_YM | 5 | 18350 | 0.499 | 0.498 | +0.2 | 0.3 | 1.000 | 25H1 -0.0 / 25H2 -0.4 / 26H1 +0.5 / 26H2 +0.2 |
| London | px_ZB | 15 | 62436 | 0.501 | 0.498 | +0.3 | 1.0 | 1.000 | 25H1 +0.0 / 25H2 +0.5 / 26H1 +0.5 / 26H2 -0.2 |
| London | fl_ZB | 60 | 11842 | 0.495 | 0.488 | +0.6 | 1.0 | 1.000 | 25H1 +1.0 / 25H2 -0.9 / 26H1 +0.5 / 26H2 +2.9 |
| London | imb_ZB | 5 | 8578 | 0.499 | 0.496 | +0.3 | 0.4 | 1.000 | 25H1 -12.8 / 25H2 +0.5 / 26H1 +1.0 / 26H2 -0.7 |
| London | px_6J | 60 | 12253 | 0.502 | 0.493 | +0.9 | 1.4 | 1.000 | 25H1 -1.8 / 25H2 +1.8 / 26H1 +0.2 / 26H2 +1.7 |
| London | fl_6J | 15 | 28562 | 0.501 | 0.500 | +0.1 | 0.2 | 1.000 | 25H1 +1.4 / 25H2 -0.6 / 26H1 +0.4 / 26H2 +0.1 |
| London | imb_6J | 60 | 10243 | 0.500 | 0.500 | -0.0 | -0.0 | 1.000 | 25H1 +1.6 / 25H2 +0.6 / 26H1 -1.1 / 26H2 -0.3 |
| London | px_NKD | 300 | 834 | 0.502 | 0.488 | +1.4 | 0.6 | 1.000 | 25H1 +5.8 / 25H2 +0.2 / 26H1 -3.1 / 26H2 +7.9 |
| London | fl_NKD | 1 | 33051 | 0.502 | 0.499 | +0.3 | 0.7 | 1.000 | 25H1 +0.7 / 25H2 +0.7 / 26H1 -0.1 / 26H2 +0.3 |
| London | imb_NKD | 15 | 3381 | 0.529 | 0.502 | +2.6 | 2.1 | 1.000 | 25H1 +5.4 / 25H2 +1.5 / 26H1 +3.1 / 26H2 +2.1 |
| London | px_6E | 1 | 231807 | 0.503 | 0.500 | +0.2 | 1.6 | 1.000 | 25H1 -0.9 / 25H2 +1.5 / 26H1 +0.3 / 26H2 -1.1 |
| London | px_6A | 1 | 121548 | 0.506 | 0.500 | +0.6 | 2.6 | 0.496 | 25H1 +0.2 / 25H2 +2.0 / 26H1 +0.4 / 26H2 -1.0 |
| London | px_HG | 1 | 133242 | 0.509 | 0.500 | +0.9 | 4.4 | 0.002 | 25H1 +0.4 / 25H2 +1.0 / 26H1 +1.2 / 26H2 +0.5 |
| London | ref_px_ES | 1 | 23008 | 0.534 | 0.499 | +3.6 | 7.2 | 0.000 | 25H1 +3.5 / 25H2 +6.9 / 26H1 +3.5 / 26H2 +1.1 |

## 4. Table 3: selected on fit, judged once (all feeds, NQ-FLAT variant; rows with a non-NEVER label)
| session | feed | w | h | fires/mo | judge hit | null | edge pp | z | q | follow bp | by half-year edge pp | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | fl_6E | 1 | 1 | 4938 | 0.503 | 0.498 | +0.6 | 1.5 | 0.967 | 0.005 | 25H1 +0.7 / 25H2 +2.2 / 26H1 +1.7 / 26H2 -0.0 | +0.2 | +0.0 | SOMETIMES (noise level, q>0.10) |
| Asia | fl_AAPL | 5 | 5 | 29 | 0.551 | 0.505 | +4.6 | 0.9 | 0.967 | 0.032 | 25H1 +2.9 / 25H2 +4.3 / 26H1 +7.2 / 26H2 +0.8 | -1.7 | +0.6 | SOMETIMES (noise level, q>0.10) |
| Asia | fl_AMZN | 60 | 300 | 20 | 0.535 | 0.533 | +0.3 | 0.0 | 1.000 | 1.062 | 25H1 +4.6 / 25H2 +2.5 / 26H1 +1.7 / 26H2 +2.0 | +4.9 | +3.3 | SOMETIMES (noise level, q>0.10) |
| Asia | fl_BASKET8 | 1 | 1 | 137 | 0.509 | 0.493 | +1.6 | 0.7 | 0.967 | -0.004 | 25H1 +5.9 / 25H2 +1.1 / 26H1 +1.2 / 26H2 +3.8 | +4.0 | +1.7 | SOMETIMES (noise level, q>0.10) |
| Asia | fl_GOOGL | 1 | 1 | 9 | 0.567 | 0.474 | +9.3 | 1.0 | 0.967 | 0.067 | 25H1 +7.3 / 25H2 +3.3 / 26H1 na / 26H2 +8.5 |  | +8.1 | SOMETIMES (noise level, q>0.10) |
| Asia | fl_MSFT | 1 | 1 | 17 | 0.504 | 0.442 | +6.2 | 0.9 | 0.967 | 0.017 | 25H1 +7.2 / 25H2 +3.3 / 26H1 +6.9 / 26H2 +6.4 |  | +7.8 | SOMETIMES (noise level, q>0.10) |
| Asia | fl_QQQ | 15 | 300 | 35 | 0.541 | 0.529 | +1.2 | 0.3 | 1.000 | 0.388 | 25H1 +10.8 / 25H2 +6.5 / 26H1 -1.1 / 26H2 -1.6 | +1.7 | +0.5 | SOMETIMES (noise level, q>0.10) |
| Asia | fl_SPY | 5 | 5 | 31 | 0.532 | 0.496 | +3.5 | 0.7 | 0.967 | 0.070 | 25H1 +4.8 / 25H2 -2.9 / 26H1 -1.3 / 26H2 +15.1 | +15.7 | +6.3 | SOMETIMES (noise level, q>0.10) |
| Asia | fl_YM | 1 | 1 | 5843 | 0.502 | 0.501 | +0.2 | 0.4 | 0.991 | 0.003 | 25H1 +1.3 / 25H2 +1.3 / 26H1 +0.4 / 26H2 +0.2 | -0.1 | +0.2 | SOMETIMES (noise level, q>0.10) |
| Asia | fl_ZB | 5 | 5 | 2349 | 0.503 | 0.498 | +0.5 | 1.0 | 0.967 | -0.009 | 25H1 +0.4 / 25H2 -0.2 / 26H1 -0.5 / 26H2 +0.9 | +1.0 | +0.7 | SOMETIMES (noise level, q>0.10) |
| Asia | imb_ZB | 15 | 15 | 512 | 0.505 | 0.496 | +0.8 | 0.7 | 0.967 | 0.021 | 25H1 +1.1 / 25H2 -0.1 / 26H1 -0.8 / 26H2 +2.9 | +2.1 | +1.6 | SOMETIMES (noise level, q>0.10) |
| Asia | px_6A | 1 | 1 | 7112 | 0.506 | 0.498 | +0.8 | 2.6 | 0.204 | 0.008 | 25H1 +1.0 / 25H2 +3.1 / 26H1 +1.3 / 26H2 +0.2 | +0.4 | +0.4 | SOMETIMES (noise level, q>0.10) |
| Asia | px_6E | 1 | 1 | 8172 | 0.507 | 0.500 | +0.7 | 2.4 | 0.270 | 0.008 | 25H1 +0.4 / 25H2 +2.0 / 26H1 +1.2 / 26H2 +0.3 | -0.1 | +0.3 | SOMETIMES (noise level, q>0.10) |
| Asia | px_HG | 1 | 1 | 7892 | 0.507 | 0.498 | +0.9 | 2.9 | 0.139 | 0.009 | 25H1 +0.7 / 25H2 +1.1 / 26H1 +1.1 / 26H2 +0.6 | +0.4 | +0.7 | SOMETIMES (noise level, q>0.10) |
| Asia | px_NKD | 5 | 300 | 932 | 0.507 | 0.502 | +0.5 | 0.6 | 0.967 | 0.020 | 25H1 +1.0 / 25H2 +1.9 / 26H1 -0.2 / 26H2 +0.1 | -1.5 | +0.2 | SOMETIMES (noise level, q>0.10) |
| Asia | px_NVDA | 15 | 300 | 19 | 0.477 | 0.469 | +0.8 | 0.1 | 1.000 | -0.364 | 25H1 +2.5 / 25H2 +4.8 / 26H1 +2.9 / 26H2 +10.7 |  | +1.8 | SOMETIMES (noise level, q>0.10) |
| Asia | px_YM | 1 | 1 | 7075 | 0.501 | 0.501 | +0.1 | 0.2 | 1.000 | 0.003 | 25H1 +0.9 / 25H2 +1.1 / 26H1 +0.1 / 26H2 +0.1 | -0.4 | +0.2 | SOMETIMES (noise level, q>0.10) |
| Asia | ref_px_ES | 1 | 1 | 2987 | 0.522 | 0.499 | +2.4 | 4.6 | 0.001 | 0.010 | 25H1 +7.5 / 25H2 +6.8 / 26H1 +3.9 / 26H2 +1.9 | +1.9 | +2.0 | STEADY LEADER |
| Asia | ref_px_RTY | 1 | 1 | 5235 | 0.514 | 0.497 | +1.7 | 4.4 | 0.001 | 0.011 | 25H1 +4.0 / 25H2 +3.6 / 26H1 +1.9 / 26H2 +1.6 | +1.5 | +1.7 | STEADY LEADER |
| London | fl_BASKET8 | 1 | 1 | 503 | 0.503 | 0.492 | +1.2 | 0.9 | 0.967 | 0.004 | 25H1 +5.3 / 25H2 +3.4 / 26H1 +1.6 / 26H2 +0.1 | -0.7 | +0.9 | SOMETIMES (noise level, q>0.10) |
| London | fl_GOOGL | 5 | 5 | 97 | 0.501 | 0.483 | +1.9 | 0.7 | 0.967 | 0.015 | 25H1 +5.3 / 25H2 +4.0 / 26H1 +5.3 / 26H2 -0.8 | -1.6 | +2.0 | SOMETIMES (noise level, q>0.10) |
| London | fl_META | 5 | 5 | 90 | 0.498 | 0.479 | +1.9 | 0.7 | 0.967 | 0.003 | 25H1 +0.8 / 25H2 +4.9 / 26H1 +1.1 / 26H2 +0.8 | -3.8 | +2.1 | SOMETIMES (noise level, q>0.10) |
| London | fl_QQQ | 60 | 60 | 434 | 0.500 | 0.499 | +0.1 | 0.1 | 1.000 | -0.026 | 25H1 +6.2 / 25H2 +3.2 / 26H1 +1.3 / 26H2 -0.8 | -0.5 | +1.1 | SOMETIMES (noise level, q>0.10) |
| London | fl_SPY | 15 | 300 | 247 | 0.515 | 0.494 | +2.1 | 1.3 | 0.967 | -0.172 | 25H1 +2.2 / 25H2 +3.3 / 26H1 -1.4 / 26H2 +7.8 | +9.2 | +3.0 | SOMETIMES (noise level, q>0.10) |
| London | imb_6E | 60 | 60 | 611 | 0.500 | 0.490 | +1.0 | 0.9 | 0.967 | 0.022 | 25H1 +1.3 / 25H2 +0.6 / 26H1 +0.5 / 26H2 -0.4 | +0.8 | +0.2 | SOMETIMES (noise level, q>0.10) |
| London | imb_6J | 60 | 300 | 301 | 0.521 | 0.503 | +1.8 | 1.3 | 0.967 | 0.324 | 25H1 -0.0 / 25H2 +3.4 / 26H1 +1.2 / 26H2 +1.6 | +3.4 | +1.7 | SOMETIMES (noise level, q>0.10) |
| London | imb_NKD | 15 | 15 | 272 | 0.531 | 0.509 | +2.2 | 1.5 | 0.967 | 0.081 | 25H1 +5.4 / 25H2 +1.5 / 26H1 +3.1 / 26H2 +2.1 | +2.6 | +2.8 | SOMETIMES (noise level, q>0.10) |
| London | imb_YM | 15 | 300 | 564 | 0.508 | 0.498 | +1.0 | 1.0 | 0.967 | 0.027 | 25H1 +3.0 / 25H2 +1.0 / 26H1 +0.1 / 26H2 +1.3 | +1.3 | +1.3 | SOMETIMES (noise level, q>0.10) |
| London | px_6J | 60 | 60 | 566 | 0.504 | 0.492 | +1.1 | 1.1 | 0.967 | -0.015 | 25H1 -1.8 / 25H2 +1.8 / 26H1 +0.2 / 26H2 +1.7 | +2.3 | +1.1 | SOMETIMES (noise level, q>0.10) |
| London | px_AMZN | 5 | 5 | 17 | 0.525 | 0.517 | +0.8 | 0.1 | 1.000 | -0.013 | 25H1 +1.0 / 25H2 +3.1 / 26H1 +8.2 / 26H2 -1.8 | -4.9 | +1.6 | SOMETIMES (noise level, q>0.10) |
| London | px_AVGO | 15 | 15 | 18 | 0.558 | 0.439 | +11.9 | 1.9 | 0.695 | 0.168 | 25H1 +0.9 / 25H2 +3.5 / 26H1 +15.9 / 26H2 +17.0 |  | +12.0 | SOMETIMES (noise level, q>0.10) |
| London | px_HG | 1 | 1 | 6492 | 0.510 | 0.500 | +1.0 | 3.1 | 0.092 | 0.007 | 25H1 +0.4 / 25H2 +1.0 / 26H1 +1.2 / 26H2 +0.5 | +0.3 | +0.8 | STEADY LEADER |
| London | px_NKD | 15 | 300 | 392 | 0.508 | 0.496 | +1.3 | 1.0 | 0.967 | 0.130 | 25H1 -2.8 / 25H2 +1.1 / 26H1 +0.6 / 26H2 +1.9 | +1.8 | +2.4 | SOMETIMES (noise level, q>0.10) |
| London | px_TSLA | 1 | 1 | 55 | 0.552 | 0.512 | +4.1 | 1.1 | 0.967 | 0.041 | 25H1 +2.1 / 25H2 +2.6 / 26H1 -0.5 / 26H2 +3.6 | +3.1 | +2.4 | SOMETIMES (noise level, q>0.10) |
| London | ref_px_ES | 1 | 1 | 1758 | 0.514 | 0.498 | +1.6 | 2.4 | 0.270 | 0.009 | 25H1 +3.5 / 25H2 +6.9 / 26H1 +3.5 / 26H2 +1.1 | +0.9 | +1.6 | SOMETIMES (noise level, q>0.10) |
| NY AM | fl_6J | 5 | 5 | 1949 | 0.502 | 0.502 | +0.0 | 0.1 | 1.000 | 0.009 | 25H1 +0.0 / 25H2 +0.8 / 26H1 +0.2 / 26H2 +0.7 | +1.0 | +0.3 | SOMETIMES (noise level, q>0.10) |
| NY AM | fl_AAPL | 1 | 1 | 1079 | 0.509 | 0.500 | +0.9 | 1.1 | 0.967 | 0.018 | 25H1 -0.6 / 25H2 -0.2 / 26H1 +1.9 / 26H2 +0.3 | -0.6 | +1.1 | SOMETIMES (noise level, q>0.10) |
| NY AM | fl_AMZN | 5 | 5 | 1162 | 0.515 | 0.499 | +1.6 | 2.0 | 0.695 | 0.014 | 25H1 +0.0 / 25H2 +2.0 / 26H1 +0.8 / 26H2 +2.2 | +2.3 | +2.0 | SOMETIMES (noise level, q>0.10) |
| NY AM | fl_AVGO | 300 | 300 | 130 | 0.485 | 0.483 | +0.2 | 0.1 | 1.000 | -0.247 | 25H1 +6.4 / 25H2 +1.4 / 26H1 +2.0 / 26H2 -0.5 | -0.3 | +0.2 | SOMETIMES (noise level, q>0.10) |
| NY AM | fl_YM | 5 | 300 | 485 | 0.503 | 0.490 | +1.3 | 1.2 | 0.967 | -0.187 | 25H1 +1.7 / 25H2 +2.0 / 26H1 +0.8 / 26H2 +0.3 | -0.4 | +0.3 | SOMETIMES (noise level, q>0.10) |
| NY AM | imb_6E | 5 | 5 | 33 | 0.525 | 0.511 | +1.4 | 0.3 | 1.000 | 0.073 | 25H1 -1.5 / 25H2 +4.1 / 26H1 +1.2 / 26H2 +3.2 |  | +1.5 | SOMETIMES (noise level, q>0.10) |
| NY AM | imb_NKD | 5 | 300 | 90 | 0.488 | 0.481 | +0.7 | 0.3 | 1.000 | -0.342 | 25H1 na / 25H2 +11.1 / 26H1 +1.2 / 26H2 +2.3 | +3.2 | +2.5 | SOMETIMES (noise level, q>0.10) |
| NY AM | imb_ZB | 300 | 300 | 125 | 0.507 | 0.474 | +3.4 | 1.5 | 0.967 | 0.180 | 25H1 -1.2 / 25H2 +1.6 / 26H1 +6.1 / 26H2 +1.7 | -0.5 | +2.4 | SOMETIMES (noise level, q>0.10) |
| NY AM | px_AMZN | 5 | 300 | 377 | 0.506 | 0.496 | +1.0 | 0.7 | 0.967 | 0.048 | 25H1 +0.6 / 25H2 +1.7 / 26H1 +2.7 / 26H2 -0.7 | -1.6 | +0.0 | SOMETIMES (noise level, q>0.10) |
| NY AM | px_AVGO | 300 | 300 | 32 | 0.498 | 0.492 | +0.6 | 0.1 | 1.000 | -0.697 | 25H1 +8.5 / 25H2 +9.3 / 26H1 +3.6 / 26H2 +5.9 | +7.7 | +0.6 | SOMETIMES (noise level, q>0.10) |
| NY AM | px_GOOGL | 60 | 300 | 98 | 0.520 | 0.490 | +3.0 | 1.1 | 0.967 | 0.160 | 25H1 +6.2 / 25H2 +5.7 / 26H1 -1.8 / 26H2 +4.2 | +5.4 | +3.1 | SOMETIMES (noise level, q>0.10) |
| NY AM | px_MSFT | 60 | 60 | 143 | 0.505 | 0.487 | +1.8 | 0.8 | 0.967 | 0.130 | 25H1 +7.0 / 25H2 -0.7 / 26H1 +3.3 / 26H2 +1.3 | +0.4 | +1.3 | SOMETIMES (noise level, q>0.10) |
| NY AM | px_NKD | 15 | 300 | 323 | 0.507 | 0.501 | +0.6 | 0.4 | 0.991 | 0.234 | 25H1 -0.3 / 25H2 +1.6 / 26H1 +1.4 / 26H2 +0.6 | +1.0 | +0.7 | SOMETIMES (noise level, q>0.10) |
| NY AM | px_QQQ | 5 | 5 | 1099 | 0.502 | 0.498 | +0.4 | 0.5 | 0.978 | 0.013 | 25H1 +0.8 / 25H2 +0.5 / 26H1 +1.6 / 26H2 -0.2 | +0.4 | +0.2 | SOMETIMES (noise level, q>0.10) |
| NY AM | px_TSLA | 15 | 15 | 538 | 0.501 | 0.501 | +0.0 | 0.0 | 1.000 | 0.070 | 25H1 -0.8 / 25H2 +3.1 / 26H1 +2.2 / 26H2 -2.5 | -4.1 | +0.0 | SOMETIMES (noise level, q>0.10) |
| NY AM | ref_px_ES | 1 | 1 | 515 | 0.523 | 0.491 | +3.3 | 2.7 | 0.184 | 0.007 | 25H1 -1.2 / 25H2 +2.5 / 26H1 +1.4 / 26H2 +3.6 | +2.2 | +3.5 | SOMETIMES (noise level, q>0.10) |
| NY AM | ref_px_RTY | 1 | 300 | 505 | 0.512 | 0.503 | +0.9 | 0.8 | 0.967 | 0.332 | 25H1 -0.2 / 25H2 +1.2 / 26H1 +0.8 / 26H2 +1.7 | +2.6 | +1.0 | SOMETIMES (noise level, q>0.10) |
| NY PM | fl_6E | 1 | 300 | 606 | 0.502 | 0.494 | +0.8 | 0.8 | 0.967 | -0.033 | 25H1 +2.0 / 25H2 -0.6 / 26H1 +1.5 / 26H2 +0.7 | -0.2 | +0.3 | SOMETIMES (noise level, q>0.10) |
| NY PM | fl_6J | 300 | 300 | 132 | 0.501 | 0.493 | +0.8 | 0.4 | 1.000 | -0.227 | 25H1 -1.8 / 25H2 +5.7 / 26H1 -0.3 / 26H2 +2.1 | +5.2 | +1.9 | SOMETIMES (noise level, q>0.10) |
| NY PM | fl_AMZN | 5 | 5 | 1554 | 0.493 | 0.493 | +0.0 | 0.0 | 1.000 | 0.005 | 25H1 -0.9 / 25H2 +0.3 / 26H1 -0.2 / 26H2 +0.8 | +1.5 | +0.2 | SOMETIMES (noise level, q>0.10) |
| NY PM | fl_BASKET8 | 1 | 1 | 2660 | 0.503 | 0.497 | +0.7 | 1.2 | 0.967 | 0.001 | 25H1 -2.3 / 25H2 +0.6 / 26H1 +0.1 / 26H2 +1.3 | +1.4 | +0.7 | SOMETIMES (noise level, q>0.10) |
| NY PM | fl_GOOGL | 5 | 5 | 1326 | 0.503 | 0.498 | +0.5 | 0.6 | 0.967 | -0.012 | 25H1 +0.8 / 25H2 +0.1 / 26H1 +0.4 / 26H2 +0.0 | +1.0 | +0.0 | SOMETIMES (noise level, q>0.10) |
| NY PM | fl_NKD | 1 | 300 | 476 | 0.505 | 0.491 | +1.4 | 1.2 | 0.967 | -0.038 | 25H1 -2.9 / 25H2 +1.2 / 26H1 +2.6 / 26H2 +0.5 | +2.1 | +0.4 | SOMETIMES (noise level, q>0.10) |
| NY PM | fl_QQQ | 1 | 300 | 652 | 0.503 | 0.493 | +1.0 | 0.9 | 0.967 | 0.201 | 25H1 -1.5 / 25H2 +1.2 / 26H1 +3.1 / 26H2 -0.6 | -0.4 | +1.1 | SOMETIMES (noise level, q>0.10) |
| NY PM | fl_SPY | 1 | 300 | 637 | 0.505 | 0.498 | +0.7 | 0.7 | 0.967 | 0.043 | 25H1 +0.2 / 25H2 +1.1 / 26H1 +1.1 / 26H2 +1.3 | -0.1 | +1.1 | SOMETIMES (noise level, q>0.10) |
| NY PM | fl_YM | 5 | 5 | 1843 | 0.504 | 0.500 | +0.4 | 0.7 | 0.967 | 0.011 | 25H1 +2.0 / 25H2 +1.0 / 26H1 -0.5 / 26H2 +0.9 | +1.0 | +1.0 | SOMETIMES (noise level, q>0.10) |
| NY PM | fl_ZB | 15 | 300 | 428 | 0.504 | 0.486 | +1.8 | 1.4 | 0.967 | 0.067 | 25H1 -3.1 / 25H2 +0.3 / 26H1 +1.0 / 26H2 +1.5 | +5.5 | +2.1 | SOMETIMES (noise level, q>0.10) |
| NY PM | imb_6E | 15 | 300 | 79 | 0.528 | 0.493 | +3.5 | 1.2 | 0.967 | 0.844 | 25H1 -0.1 / 25H2 -1.0 / 26H1 +4.3 / 26H2 +0.6 | -0.6 | +1.4 | SOMETIMES (noise level, q>0.10) |
| NY PM | imb_NKD | 5 | 300 | 50 | 0.518 | 0.504 | +1.3 | 0.4 | 1.000 | 0.495 | 25H1 na / 25H2 na / 26H1 +2.6 / 26H2 +0.9 | +3.2 | +0.9 | SOMETIMES (noise level, q>0.10) |
| NY PM | imb_YM | 5 | 5 | 2812 | 0.499 | 0.497 | +0.2 | 0.5 | 0.978 | 0.001 | 25H1 -0.6 / 25H2 +1.6 / 26H1 +0.3 / 26H2 -0.1 | -0.1 | +0.0 | SOMETIMES (noise level, q>0.10) |
| NY PM | px_6J | 5 | 5 | 4314 | 0.503 | 0.500 | +0.3 | 0.8 | 0.967 | 0.002 | 25H1 +0.9 / 25H2 +0.5 / 26H1 +0.6 / 26H2 +0.1 | +0.4 | +0.0 | SOMETIMES (noise level, q>0.10) |
| NY PM | px_AMZN | 15 | 15 | 1208 | 0.498 | 0.494 | +0.4 | 0.5 | 0.981 | 0.015 | 25H1 -0.5 / 25H2 +2.1 / 26H1 -0.1 / 26H2 +0.4 | +0.6 | +0.2 | SOMETIMES (noise level, q>0.10) |
| NY PM | px_AVGO | 60 | 60 | 285 | 0.507 | 0.502 | +0.4 | 0.3 | 1.000 | 0.041 | 25H1 -0.9 / 25H2 +0.6 / 26H1 +2.2 / 26H2 +0.6 | +2.6 | +0.4 | SOMETIMES (noise level, q>0.10) |
| NY PM | px_QQQ | 1 | 300 | 837 | 0.502 | 0.497 | +0.5 | 0.6 | 0.967 | 0.025 | 25H1 +1.2 / 25H2 +0.3 / 26H1 +0.4 / 26H2 +0.1 | -0.0 | +0.6 | SOMETIMES (noise level, q>0.10) |
| NY PM | px_TSLA | 60 | 300 | 252 | 0.489 | 0.468 | +2.0 | 1.2 | 0.967 | -0.115 | 25H1 -3.1 / 25H2 +3.6 / 26H1 +1.8 / 26H2 +1.2 | +0.9 | +2.7 | SOMETIMES (noise level, q>0.10) |
| NY PM | ref_px_ES | 1 | 1 | 441 | 0.537 | 0.496 | +4.1 | 2.8 | 0.156 | 0.009 | 25H1 +7.8 / 25H2 +2.8 / 26H1 +2.1 / 26H2 +4.6 | +5.0 | +3.8 | SOMETIMES (noise level, q>0.10) |

Counts by label (all variants): Counter({'NEVER': 186, 'SOMETIMES (noise level, q>0.10)': 123, 'STEADY LEADER': 3})

## 5. Same moment (correlation with NQ over the same window; after the +1 s shift)
| session | window | top feeds (corr) |
|---|---|---|
| Asia | 1 s | ref_px_ES 0.77, ref_px_RTY 0.62, px_YM 0.28, fl_YM 0.20, px_SPY 0.10, px_NKD 0.09, px_6A 0.09, px_QQQ 0.08 |
| Asia | 60 s | ref_px_ES 0.85, ref_px_RTY 0.74, px_QQQ 0.73, px_YM 0.68, px_SPY 0.49, px_NKD 0.46, px_MSFT 0.30, px_6A 0.29 |
| London | 1 s | ref_px_ES 0.85, ref_px_RTY 0.70, px_YM 0.38, fl_YM 0.23, px_NKD 0.17, px_SPY 0.16, px_6A 0.15, px_QQQ 0.12 |
| London | 60 s | ref_px_ES 0.94, ref_px_RTY 0.77, px_YM 0.71, px_SPY 0.66, px_QQQ 0.64, px_NKD 0.64, px_BASKET8 0.50, px_NVDA 0.47 |
| NY AM | 1 s | ref_px_ES 0.88, ref_px_RTY 0.61, px_BASKET8 0.52, px_NVDA 0.43, px_SPY 0.42, px_QQQ 0.40, px_YM 0.39, px_TSLA 0.27 |
| NY AM | 60 s | px_QQQ 0.96, ref_px_ES 0.91, px_SPY 0.89, px_BASKET8 0.81, px_NVDA 0.67, px_NKD 0.66, ref_px_RTY 0.63, px_AVGO 0.60 |
| NY PM | 1 s | ref_px_ES 0.90, ref_px_RTY 0.75, px_BASKET8 0.57, px_YM 0.52, px_SPY 0.48, px_NVDA 0.45, px_QQQ 0.41, px_TSLA 0.30 |
| NY PM | 60 s | px_QQQ 0.97, ref_px_ES 0.95, px_SPY 0.93, px_BASKET8 0.90, ref_px_RTY 0.78, px_YM 0.77, px_NVDA 0.74, px_NKD 0.67 |

## 6. TURNS (reversals): which feed turned before NQ (lead in seconds, negative = feed first; NQ turn = 3-sigma 300-s run then >= 40 percent give-back; judge = last 40 percent of months; null = random windows)
| session | feed | turns | median lead s | null median s | share >= 5 s early | null share | diff pp | z | by half-year diff pp | label |
|---|---|---|---|---|---|---|---|---|---|---|
| Asia | fl_YM | 613 | -1 | 14 | 0.457 | 0.385 | +7.2 | 2.3 | 25H1 +2.3 / 25H2 +2.9 / 26H1 +5.5 / 26H2 +3.0 | SOMETIMES |
| Asia | imb_NKD | 590 | -10 | 18 | 0.507 | 0.453 | +5.4 | 1.7 | 25H1 -1.0 / 25H2 -1.0 / 26H1 -0.3 / 26H2 +6.4 | SOMETIMES |
| Asia | fl_ZB | 608 | -4 | 14 | 0.498 | 0.448 | +5.0 | 1.6 | 25H1 +7.6 / 25H2 -1.0 / 26H1 +4.1 / 26H2 +2.5 | SOMETIMES |
| Asia | imb_6J | 640 | 0 | 40 | 0.492 | 0.445 | +4.8 | 1.6 | 25H1 +4.0 / 25H2 -2.4 / 26H1 +1.1 / 26H2 +2.0 | SOMETIMES |
| London | fl_NVDA | 268 | -38 | 23 | 0.627 | 0.425 | +20.1 | 3.9 | 25H1 +9.0 / 25H2 +6.2 / 26H1 +8.1 / 26H2 +22.8 | STEADY LEADER |
| London | fl_TSLA | 202 | -14 | 43 | 0.554 | 0.362 | +19.2 | 3.4 | 25H1 +6.7 / 25H2 +2.5 / 26H1 +12.5 / 26H2 +13.5 | STEADY LEADER |
| London | fl_QQQ | 293 | -21 | 29 | 0.567 | 0.406 | +16.0 | 3.3 | 25H1 +1.0 / 25H2 -1.7 / 26H1 +2.1 / 26H2 +21.3 | SOMETIMES |
| London | px_AVGO | 112 | -42 | 20 | 0.616 | 0.388 | +22.8 | 3.0 | 25H1 +20.2 / 25H2 +21.2 / 26H1 +35.1 / 26H2 +13.8 | SOMETIMES |
| London | px_QQQ | 297 | -10 | 4 | 0.556 | 0.420 | +13.5 | 2.8 | 25H1 +1.4 / 25H2 +11.1 / 26H1 +12.4 / 26H2 +13.7 | SOMETIMES |
| London | px_NKD | 406 | -1 | 18 | 0.470 | 0.367 | +10.3 | 2.7 | 25H1 +8.8 / 25H2 +13.3 / 26H1 +12.8 / 26H2 +9.9 | SOMETIMES |
| London | imb_6E | 426 | -43 | 46 | 0.559 | 0.459 | +10.0 | 2.6 | 25H1 +15.0 / 25H2 -0.2 / 26H1 +10.1 / 26H2 +9.2 | SOMETIMES |
| London | fl_META | 83 | -30 | 48 | 0.614 | 0.383 | +23.1 | 2.6 | 25H1 na / 25H2 +1.4 / 26H1 na / 26H2 na | SOMETIMES |
| London | px_NVDA | 275 | -22 | -0 | 0.582 | 0.471 | +11.1 | 2.3 | 25H1 +5.9 / 25H2 +13.9 / 26H1 +16.2 / 26H2 +11.5 | SOMETIMES |
| London | px_AAPL | 115 | -47 | 7 | 0.565 | 0.444 | +12.1 | 1.7 | 25H1 +12.8 / 25H2 +4.7 / 26H1 +12.1 / 26H2 +9.7 | SOMETIMES |
| London | px_BASKET8 | 68 | 4 | 58 | 0.412 | 0.250 | +16.2 | 1.7 | 25H1 +4.9 / 25H2 +4.1 / 26H1 na / 26H2 na | SOMETIMES |
| London | fl_BASKET8 | 309 | -10 | 10 | 0.524 | 0.452 | +7.2 | 1.6 | 25H1 -3.1 / 25H2 +0.8 / 26H1 +0.0 / 26H2 +9.9 | SOMETIMES |
| London | fl_AMZN | 78 | -14 | 26 | 0.526 | 0.385 | +14.1 | 1.6 | 25H1 -10.8 / 25H2 +13.4 / 26H1 +3.3 / 26H2 na | SOMETIMES |
| London | fl_6J | 403 | -21 | 1 | 0.548 | 0.489 | +6.0 | 1.5 | 25H1 +3.4 / 25H2 -1.7 / 26H1 +3.2 / 26H2 +3.5 | SOMETIMES |
| NY AM | fl_SPY | 312 | -10 | 49 | 0.519 | 0.394 | +12.5 | 2.8 | 25H1 -11.9 / 25H2 +8.6 / 26H1 +5.7 / 26H2 +13.5 | SOMETIMES |
| NY AM | imb_YM | 338 | -30 | 40 | 0.527 | 0.412 | +11.4 | 2.4 | 25H1 +8.6 / 25H2 +3.6 / 26H1 +4.6 / 26H2 +14.1 | SOMETIMES |
| NY AM | px_AVGO | 307 | -3 | 2 | 0.495 | 0.414 | +8.1 | 1.7 | 25H1 -11.1 / 25H2 -0.4 / 26H1 +6.8 / 26H2 +4.7 | SOMETIMES |
| NY PM | fl_AAPL | 239 | -20 | 40 | 0.536 | 0.405 | +13.0 | 2.7 | 25H1 -7.3 / 25H2 +2.4 / 26H1 +13.6 / 26H2 +10.9 | SOMETIMES |
| NY PM | fl_AMZN | 238 | -13 | 24 | 0.534 | 0.422 | +11.2 | 2.3 | 25H1 +0.0 / 25H2 +5.0 / 26H1 +8.0 / 26H2 +6.9 | SOMETIMES |
| NY PM | imb_NKD | 247 | -34 | 11 | 0.547 | 0.470 | +7.7 | 1.6 | 25H1 -4.9 / 25H2 -3.2 / 26H1 +8.4 / 26H2 +10.2 | SOMETIMES |

Turns per month (median): see json. Turn statistics are descriptive (turn time defined with hindsight); no multiple-testing control beyond z >= 3 and consistency; treat SOMETIMES as luck-prone.
