# WHAT_MOVES_NQ: of all the feeds on the box, what moves NQ, and what moves BEFORE NQ (W-DYNL). DISCOVERY, NOT A RESULT
Generated 2026-11-27T18:16:25Z. Order: Josh 17:51Z 27 Nov ("what moves NQ and what moves before NQ moves"). Searching is right here; nothing below is a design: the only use is WHICH FEEDS SIT ON WHICH SCREEN IN WHICH SESSION. Code code/th_dynl/wm_run.py, wm_agg.py, wm_turns.py, wm_turn_agg.py, wm_page.py; raw counts /mnt/l2/l2vast/_dynexit/wm/ (server C).

## ANSWER FIRST
1. MOVES WITH NQ (same moment): ES carries NQ: correlation of its move with NQ over the same 1 s / 5 s / 60 s is about 0.74-0.89 / 0.82-0.94 / 0.88-0.95 depending on session (R2 55-90%); RTY and YM next (0.58-0.83); then NQ's own order book/flow (MBO adds l3_add 0.6-0.78 at 1 s, 10-level nq10_add, trade flow nq10_ofi, fills). Bonds, FX, crude, gold, Nikkei, megacaps, QQQ/SPY and the UW feeds co-move far less at these horizons (table 3).
2. MOVES BEFORE NQ: mostly it does not, and where it does the move that follows is tiny. Of 306 feed x session x variant judged rows only 1 are STEADY LEADERS (listed in table 5); the rest are SOMETIMES or NEVER. The one robust second-scale lead is ES over the last second, with NQ not yet moved: it is right 52-53% of the time vs a 49-50% matched null, but NQ moves only about 0.01 bp (0.03 pt) after it: real in the statistics, not tradable as a signal.
3. TURNS: see table 6: which feeds turned before NQ turned (descriptive, hindsight-defined turn, linear drift removed, null with the same direction mix).
4. STABILITY: the study is built on the worry that everything changes: every row has its judge-set (last 40% of the feed months, never used to pick the setting), each year, last 3 and last 6 months, and a label. A feed is a candidate for a screen's vote ONLY if STEADY. Count of everything examined: 358 (feed, window, horizon) cells x 4 sessions x 2 variants; BH q=10% over the 306 judged rows.

## 1. Method (all causal; DISCOVERY)
- Grid: NQ mid per second (age_ feed), 46 months 2023-02..2026-11. Feed x_w(t) = its move over the last w seconds (price feeds: return in bp; order-flow feeds: net sum over w; level feeds: mean over w; UW cumulative feeds: change over w), scaled by its own rolling std over the previous 3600 s (ending at t-1). FIRE when |x|/sigma >= 2. NQ-FLAT variant: additionally NQ's own move over the same w is < 0.5 of its sigma, i.e. the lead is not just NQ moving first.
- Outcome: NQ mid return over the next h = w seconds (and 300 s), HIT = same sign as the feed (sign of the feed fixed on its first 60% of months from the same-moment covariance: e.g. ZN, 6J, dollar, UW tide, book imbalance come out negative). Fires thinned by a refractory period of max(w,h) so outcomes do not overlap. 1-minute feeds (xmkt 12 instruments, megacaps, QQQ/SPY/IWM/DIA, TICK, UW 1-min) are evaluated at their own update times with w, h = 1/5/15/60 min.
- NULL (matched base rate): the same fires, scored against NQ outcomes taken 30-120 min later (two random shifts per month): same fire process, same sign, same volatility regime. Edge = hit rate - null hit rate.
- Selection: per feed, session and variant the (w, h) with the best edge z on the FIT months (first 60% of the feed's months) is chosen, then judged ONCE on the last 40%; BH over all judged rows.
- Sessions (ET of the fire time): Asia 18:00-03:00, London 03:00-08:30, NY AM 08:30-12:00, NY PM 12:00-16:00.
- Labels: STEADY LEADER = judge edge >= 1.0 pp, BH q <= 0.10, positive in >= 75% of the years with >= 200 fires AND at least 3 such years, positive in the last 3 AND last 6 months. NOTE: the NQ own book/flow features (nq10_, l3sec_, liq10_) hold Asia and London hours only for 2026 (earlier years only have the NY hours), so in those sessions they can at most be SOMETIMES; UW, megacaps and QQQ/SPY start 2024-10 (3 calendar years). SOMETIMES = positive on the judge set and (q <= 0.10 or positive in the last 6 months). NEVER otherwise.
- Size of the move: "follow" = mean NQ move in the feed's direction after a fire, in bp (1 bp = about 2.7 NQ points).

## 2. Coverage (months per feed, native resolution)
| feed | months | native resolution |
|---|---|---|
| l3_add | 44 | 1 s |
| l3_fill | 44 | 1 s |
| l3_pull | 44 | 1 s |
| l3_wall120 | 44 | 1 s |
| l3_wall30 | 44 | 1 s |
| liq10_imb | 46 | 1 s |
| liq10_wall | 46 | 1 s |
| m_6B | 45 | 1 min |
| m_6C | 45 | 1 min |
| m_6E | 46 | 1 min |
| m_6J | 46 | 1 min |
| m_AAPL | 26 | 1 min |
| m_AMZN | 26 | 1 min |
| m_CL | 46 | 1 min |
| m_DIA | 26 | 1 min |
| m_ES | 46 | 1 min |
| m_GC | 46 | 1 min |
| m_GOOGL | 26 | 1 min |
| m_IWM | 26 | 1 min |
| m_META | 26 | 1 min |
| m_MSFT | 26 | 1 min |
| m_NKD | 46 | 1 min |
| m_NVDA | 26 | 1 min |
| m_QQQ | 26 | 1 min |
| m_RTY | 46 | 1 min |
| m_SPY | 26 | 1 min |
| m_TSLA | 26 | 1 min |
| m_YM | 46 | 1 min |
| m_ZB | 46 | 1 min |
| m_ZN | 46 | 1 min |
| m_bk7 | 26 | 1 min |
| m_breadth_hl | 26 | 1 min |
| m_cap | 26 | 1 min |
| m_dollar | 46 | 1 min |
| m_eq | 26 | 1 min |
| m_tick | 44 | 1 min |
| m_tick_lvl | 44 | 1 min |
| nq10_add | 45 | 1 s |
| nq10_big | 45 | 1 s |
| nq10_imb5 | 45 | 1 s |
| nq10_ofi | 45 | 1 s |
| nq10_pull | 45 | 1 s |
| nq10_trd | 45 | 1 s |
| nq_self | 46 | 1 s |
| px_6B | 45 | 1 s |
| px_6C | 45 | 1 s |
| px_6E | 46 | 1 s |
| px_6J | 46 | 1 s |
| px_CL | 45 | 1 s |
| px_ES | 39 | 1 s |
| px_GC | 45 | 1 s |
| px_NKD | 46 | 1 s |
| px_RTY | 39 | 1 s |
| px_YM | 46 | 1 s |
| px_ZB | 46 | 1 s |
| px_ZN | 45 | 1 s |
| uw_gam_NDX | 26 | 1 min |
| uw_gam_QQQ | 26 | 1 min |
| uw_gam_SPX | 26 | 1 min |
| uw_gamdir_NDX | 26 | 1 min |
| uw_np_QQQ | 26 | 1 min |
| uw_np_SPY | 26 | 1 min |
| uw_tide | 26 | 1 min |
| uw_tide_QQQ | 26 | 1 min |
| uw_tide_SPY | 26 | 1 min |

## 3. Moves WITH NQ at the same moment (correlation with NQ over the same window; R2 = share of NQ move explained)
**Asia**

| window | top feeds (corr) |
|---|---|
| 1 s | px_ES 0.74, l3_add 0.61, px_RTY 0.58, nq10_add 0.51, nq10_ofi 0.46, l3_fill 0.46, nq10_trd 0.41, nq10_pull 0.29 |
| 5 s | px_ES 0.82, px_RTY 0.67, l3_add 0.56, nq10_ofi 0.50, l3_fill 0.50, nq10_add 0.46, nq10_trd 0.44, nq10_pull 0.17 |
| 1 min | px_ES 0.88, m_ES 0.82, px_RTY 0.76, m_RTY 0.69, m_YM 0.69, l3_fill 0.58, nq10_ofi 0.58, l3_add 0.46 |
| 300 s | px_ES 0.92, m_ES 0.89, px_RTY 0.82, m_YM 0.78, m_RTY 0.78, px_YM 0.68, nq10_ofi 0.60, l3_fill 0.59 |

**London**

| window | top feeds (corr) |
|---|---|
| 1 s | px_ES 0.84, l3_add 0.72, px_RTY 0.67, nq10_add 0.64, nq10_ofi 0.49, l3_fill 0.49, nq10_trd 0.45, nq10_pull 0.43 |
| 5 s | px_ES 0.91, px_RTY 0.72, l3_add 0.67, nq10_add 0.55, nq10_ofi 0.52, l3_fill 0.52, nq10_trd 0.47, nq10_pull 0.31 |
| 1 min | px_ES 0.94, m_ES 0.92, px_RTY 0.75, m_YM 0.73, m_RTY 0.73, nq10_ofi 0.60, l3_fill 0.59, m_NKD 0.54 |
| 300 s | px_ES 0.94, m_ES 0.93, px_RTY 0.76, m_YM 0.75, m_RTY 0.75, px_YM 0.67, m_NKD 0.66, nq10_ofi 0.64 |

**NY AM**

| window | top feeds (corr) |
|---|---|
| 1 s | px_ES 0.87, l3_add 0.78, nq10_add 0.68, px_RTY 0.58, l3_fill 0.51, nq10_ofi 0.51, nq10_pull 0.48, nq10_trd 0.47 |
| 5 s | px_ES 0.90, l3_add 0.74, px_RTY 0.60, l3_fill 0.60, nq10_ofi 0.60, nq10_add 0.54, nq10_trd 0.53, l3_pull -0.38 |
| 1 min | px_ES 0.92, m_ES 0.91, nq10_ofi 0.70, l3_fill 0.70, m_NKD 0.63, m_RTY 0.62, px_RTY 0.62, m_YM 0.60 |
| 300 s | px_ES 0.92, m_ES 0.92, m_NKD 0.73, nq10_ofi 0.70, l3_fill 0.69, px_NKD 0.68, px_RTY 0.64, m_RTY 0.63 |

**NY PM**

| window | top feeds (corr) |
|---|---|
| 1 s | px_ES 0.89, l3_add 0.78, px_RTY 0.74, nq10_add 0.71, nq10_pull 0.52, nq10_ofi 0.49, l3_fill 0.48, nq10_trd 0.45 |
| 5 s | px_ES 0.94, px_RTY 0.77, l3_add 0.72, nq10_add 0.58, nq10_ofi 0.56, l3_fill 0.56, nq10_trd 0.49, nq10_pull 0.40 |
| 1 min | px_ES 0.95, m_ES 0.95, m_YM 0.83, px_RTY 0.80, m_RTY 0.79, nq10_ofi 0.65, l3_fill 0.64, m_NKD 0.63 |
| 300 s | px_ES 0.96, m_ES 0.96, m_YM 0.84, px_RTY 0.81, m_RTY 0.81, m_NKD 0.76, px_YM 0.75, px_NKD 0.74 |

(1-minute feeds appear at 60 s and 300 s rows; minute-bar feeds cannot be measured at 1 s or 5 s.)

## 4. Moves BEFORE NQ: all feeds, by session (variant NQ-FLAT = NQ has not moved yet; the setting chosen on the fit months, judged on the last 40%)
### Asia

| feed | native | window / horizon | fires per month | hit | null | edge pp | z | q | follow bp (pts) | by year (pp) | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| px_RTY | 1 s | 1 s / 1 s | 4104 | 0.520 | 0.494 | +2.5 | +2.4 | 0.43 | +0.01 (+0.04) | 23- 24- 25- 26+2 | +1.5 | +2.0 | SOMETIMES |
| l3_add | 1 s | 1 s / 1 s | 1708 | 0.508 | 0.491 | +1.7 | +1.3 | 0.92 | +0.01 (+0.02) | 23- 24- 25- 26+2 | +1.1 | +1.1 | SOMETIMES |
| px_GC | 1 s | 15 s / 15 s | 1964 | 0.502 | 0.494 | +0.9 | +0.8 | 0.98 | +0.02 (+0.05) | 23- 24-1 25- 26+1 | -0.6 | +0.4 | SOMETIMES |
| nq10_pull | 1 s | 1 s / 1 s | 3443 | 0.502 | 0.496 | +0.6 | +0.8 | 0.98 | -0.00 (-0.01) | 23- 24- 25+7 26-0 | +3.5 | +0.3 | SOMETIMES |
| px_6E | 1 s | 5 s / 5 s | 3562 | 0.504 | 0.501 | +0.3 | +0.3 | 0.98 | +0.01 (+0.02) | 23- 24- 25- 26+0 | -0.9 | -0.1 | NEVER |
| l3_wall120 | 1 s | 15 s / 15 s | 7851 | 0.503 | 0.501 | +0.2 | +0.3 | 0.98 | +0.00 (+0.01) | 23- 24-9 25+2 26+0 | +0.4 | +0.0 | SOMETIMES |
| px_CL | 1 s | 5 s / 5 s | 5011 | 0.498 | 0.500 | -0.2 | -0.2 | 1.00 | -0.01 (-0.03) | 23- 24+3 25- 26-0 | -0.5 | +0.0 | NEVER |
| px_ZN | 1 s | 1 s / 1 s | 3110 | 0.499 | 0.503 | -0.4 | -0.3 | 1.00 | +0.00 (+0.00) | 23- 24+1 25- 26-1 | -0.0 | -0.9 | NEVER |
| l3_wall30 | 1 s | 5 s / 5 s | 10620 | 0.500 | 0.503 | -0.4 | -0.6 | 1.00 | -0.00 (-0.01) | 23- 24+1 25- 26-1 | +1.6 | -0.4 | NEVER |
| liq10_wall | 1 s | 1 s / 1 s | 15146 | 0.487 | 0.503 | -1.6 | -3.2 | 1.00 | -0.00 (-0.01) | 23- 24- 25-11 26-2 | -1.4 | -1.5 | NEVER |
| liq10_imb | 1 s | 1 s / 1 s | 12576 | 0.469 | 0.499 | -3.0 | -5.6 | 1.00 | -0.01 (-0.04) | 23- 24-4 25- 26-3 | -2.5 | -2.1 | NEVER |
| nq10_imb5 | 1 s | 1 s / 1 s | 22400 | 0.474 | 0.497 | -2.2 | -9.8 | 1.00 | -0.01 (-0.03) | 23- 24-11 25-5 26-1 | -0.5 | -0.9 | NEVER |

### London

| feed | native | window / horizon | fires per month | hit | null | edge pp | z | q | follow bp (pts) | by year (pp) | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| px_YM | 1 s | 1 s / 300 s | 239 | 0.504 | 0.486 | +1.9 | +0.9 | 0.98 | -0.05 (-0.13) | 23- 24- 25+9 26+1 | +4.6 | +2.6 | SOMETIMES |
| nq10_big | 1 s | 15 s / 15 s | 95 | 0.490 | 0.457 | +3.4 | +0.9 | 0.98 | -0.09 (-0.23) | 23- 24- 25+3 26+3 | +6.7 | +0.2 | SOMETIMES |
| l3_wall30 | 1 s | 5 s / 300 s | 119 | 0.503 | 0.479 | +2.4 | +0.8 | 0.98 | +0.24 (+0.66) | 23- 24- 25+19 26+1 | +1.3 | +1.0 | SOMETIMES |
| nq10_imb5 | 1 s | 5 s / 300 s | 232 | 0.503 | 0.491 | +1.2 | +0.6 | 0.98 | -0.02 (-0.05) | 23- 24- 25+1 26+1 | -0.4 | +0.0 | SOMETIMES |
| px_ES | 1 s | 1 s / 1 s | 1339 | 0.534 | 0.514 | +2.0 | +0.5 | 0.98 | +0.02 (+0.04) | 23- 24+5 25- 26-0 | -2.5 | -0.3 | NEVER |
| liq10_wall | 1 s | 15 s / 15 s | 1277 | 0.504 | 0.498 | +0.6 | +0.4 | 0.98 | +0.02 (+0.05) | 23+9 24- 25+4 26-0 | -1.3 | +0.3 | SOMETIMES |
| uw_gam_SPX | 1 min | 1 min / 1 min | 124 | 0.532 | 0.518 | +1.5 | +0.3 | 0.98 | +0.14 (+0.38) | 24- 25-6 26+1 | -3.0 | -0.1 | NEVER |
| px_ZN | 1 s | 5 s / 300 s | 228 | 0.506 | 0.502 | +0.5 | +0.2 | 0.98 | +0.25 (+0.68) | 23+13 24- 25+2 26+0 | +0.8 | +1.9 | SOMETIMES |
| px_6C | 1 s | 5 s / 300 s | 222 | 0.508 | 0.506 | +0.2 | +0.1 | 0.98 | -0.08 (-0.20) | 23- 24- 25+2 26-0 | +2.4 | +2.7 | SOMETIMES |
| l3_wall120 | 1 s | 1 min / 300 s | 146 | 0.518 | 0.516 | +0.2 | +0.1 | 0.98 | +0.16 (+0.42) | 23- 24- 25-1 26+1 | +0.7 | +1.2 | SOMETIMES |
| nq10_trd | 1 s | 1 min / 300 s | 79 | 0.511 | 0.510 | +0.1 | +0.0 | 1.00 | +0.25 (+0.67) | 23- 24- 25+4 26+1 | +8.2 | +6.0 | SOMETIMES |
| l3_add | 1 s | 1 s / 1 s | 932 | 0.494 | 0.496 | -0.2 | -0.1 | 1.00 | -0.00 (-0.01) | 23- 24- 25-2 26+1 | +2.8 | +1.7 | NEVER |
| px_RTY | 1 s | 15 s / 15 s | 558 | 0.491 | 0.498 | -0.6 | -0.3 | 1.00 | +0.01 (+0.04) | 23- 24+5 25+7 26-0 | -1.0 | +0.4 | NEVER |
| l3_fill | 1 s | 1 s / 300 s | 183 | 0.503 | 0.509 | -0.6 | -0.3 | 1.00 | -0.08 (-0.21) | 23- 24- 25-0 26-0 | +2.0 | +0.9 | NEVER |
| nq10_add | 1 s | 5 s / 5 s | 1796 | 0.498 | 0.502 | -0.4 | -0.3 | 1.00 | +0.00 (+0.00) | 23+7 24- 25-2 26+0 | +0.1 | +1.0 | NEVER |
| px_6J | 1 s | 5 s / 300 s | 247 | 0.493 | 0.500 | -0.7 | -0.3 | 1.00 | -0.13 (-0.36) | 23- 24- 25+4 26-1 | -2.3 | -0.4 | NEVER |
| px_NKD | 1 s | 15 s / 15 s | 620 | 0.492 | 0.499 | -0.7 | -0.4 | 1.00 | -0.01 (-0.02) | 23+5 24- 25+5 26-1 | -3.0 | -3.0 | NEVER |
| liq10_imb | 1 s | 15 s / 300 s | 154 | 0.512 | 0.522 | -1.1 | -0.4 | 1.00 | +0.20 (+0.54) | 23- 24- 25+6 26-2 | -4.1 | -4.6 | NEVER |
| px_6E | 1 s | 15 s / 15 s | 1300 | 0.498 | 0.507 | -0.9 | -0.6 | 1.00 | +0.00 (+0.00) | 23+4 24- 25+4 26-1 | -0.6 | -1.1 | NEVER |
| px_6B | 1 s | 5 s / 300 s | 222 | 0.510 | 0.527 | -1.7 | -0.7 | 1.00 | +0.31 (+0.84) | 23+6 24- 25+1 26-1 | -0.9 | -0.3 | NEVER |
| l3_pull | 1 s | 1 min / 300 s | 108 | 0.503 | 0.527 | -2.3 | -0.7 | 1.00 | +0.13 (+0.36) | 23- 24- 25+4 26-2 | -4.5 | -1.0 | NEVER |
| px_GC | 1 s | 1 s / 300 s | 247 | 0.492 | 0.510 | -1.8 | -0.8 | 1.00 | -0.10 (-0.26) | 23- 24- 25+2 26-2 | -1.2 | -1.5 | NEVER |
| nq10_ofi | 1 s | 5 s / 5 s | 1162 | 0.504 | 0.518 | -1.5 | -1.0 | 1.00 | -0.00 (-0.00) | 23+5 24- 25+2 26-2 | -1.5 | -1.7 | NEVER |
| px_ZB | 1 s | 5 s / 5 s | 1679 | 0.493 | 0.504 | -1.1 | -1.0 | 1.00 | -0.01 (-0.01) | 23+4 24- 25-2 26-1 | -1.3 | -0.5 | NEVER |
| nq10_pull | 1 s | 1 min / 300 s | 97 | 0.501 | 0.537 | -3.5 | -1.0 | 1.00 | +0.01 (+0.01) | 23- 24- 25+5 26-4 | -7.0 | -5.1 | NEVER |

### NY AM

| feed | native | window / horizon | fires per month | hit | null | edge pp | z | q | follow bp (pts) | by year (pp) | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| px_ES | 1 s | 1 s / 1 s | 464 | 0.524 | 0.497 | +2.7 | +2.8 | 0.34 | +0.00 (+0.00) | 23+4 24+3 25+3 26+2 | +1.5 | +2.9 | SOMETIMES |
| l3_fill | 1 s | 1 min / 300 s | 120 | 0.523 | 0.488 | +3.5 | +2.3 | 0.45 | +0.42 (+1.13) | 23+2 24+1 25+5 26+3 | +6.1 | +2.3 | SOMETIMES |
| nq10_imb5 | 1 s | 5 s / 300 s | 532 | 0.516 | 0.503 | +1.3 | +1.8 | 0.72 | +0.38 (+1.03) | 23+2 24+0 25+2 26+1 | +0.0 | +0.5 | SOMETIMES |
| l3_add | 1 s | 1 s / 1 s | 534 | 0.514 | 0.500 | +1.4 | +1.8 | 0.72 | +0.01 (+0.03) | 23+2 24+3 25+1 26+1 | +1.1 | +1.9 | SOMETIMES |
| l3_wall30 | 1 s | 1 min / 300 s | 180 | 0.518 | 0.496 | +2.2 | +1.7 | 0.73 | +0.36 (+0.97) | 23-1 24+0 25+2 26+2 | +3.3 | +4.7 | SOMETIMES |
| nq10_ofi | 1 s | 1 min / 300 s | 120 | 0.522 | 0.499 | +2.4 | +1.5 | 0.88 | +0.50 (+1.36) | 23+3 24+1 25+3 26+1 | +3.7 | +2.1 | SOMETIMES |
| px_6C | 1 s | 1 s / 1 s | 1557 | 0.502 | 0.498 | +0.5 | +1.0 | 0.98 | +0.00 (+0.01) | 23+1 24+1 25+1 26+0 | +0.9 | -0.4 | NEVER |
| uw_np_SPY | 1 min | 300 s / 300 s | 128 | 0.507 | 0.488 | +2.0 | +1.0 | 0.98 | +0.42 (+1.13) | 24-1 25+2 26+1 | -0.3 | +0.0 | NEVER |
| liq10_imb | 1 s | 1 min / 1 min | 340 | 0.512 | 0.503 | +0.9 | +1.0 | 0.98 | +0.07 (+0.18) | 23+1 24+1 25+1 26+0 | -1.0 | +0.9 | SOMETIMES |
| px_NKD | 1 s | 1 s / 1 s | 984 | 0.503 | 0.499 | +0.5 | +0.8 | 0.98 | +0.00 (+0.01) | 23-0 24+1 25+2 26+0 | +1.4 | +1.2 | SOMETIMES |
| nq10_trd | 1 s | 300 s / 300 s | 104 | 0.511 | 0.499 | +1.2 | +0.7 | 0.98 | +0.27 (+0.72) | 23+2 24+3 25+3 26+0 | -0.8 | +0.2 | SOMETIMES |
| uw_np_QQQ | 1 min | 300 s / 300 s | 131 | 0.506 | 0.493 | +1.4 | +0.7 | 0.98 | +0.08 (+0.22) | 24-4 25+2 26+2 | +2.1 | +0.3 | SOMETIMES |
| nq10_pull | 1 s | 15 s / 300 s | 350 | 0.515 | 0.509 | +0.6 | +0.6 | 0.98 | +0.49 (+1.34) | 23+1 24-0 25+2 26+1 | +2.9 | +2.1 | SOMETIMES |
| uw_tide_QQQ | 1 min | 1 min / 1 min | 98 | 0.505 | 0.492 | +1.3 | +0.6 | 0.98 | +0.03 (+0.09) | 24+0 25+0 26+1 | -2.2 | -1.6 | NEVER |
| px_CL | 1 s | 15 s / 300 s | 433 | 0.501 | 0.497 | +0.4 | +0.5 | 0.98 | +0.01 (+0.02) | 23-0 24-0 25-0 26+1 | +3.9 | +1.7 | SOMETIMES |
| uw_tide | 1 min | 300 s / 300 s | 59 | 0.492 | 0.479 | +1.3 | +0.4 | 0.98 | -0.20 (-0.55) | 24- 25-0 26+0 | +2.6 | +3.0 | SOMETIMES |
| l3_wall120 | 1 s | 1 s / 300 s | 322 | 0.501 | 0.497 | +0.4 | +0.4 | 0.98 | -0.07 (-0.20) | 23+0 24+1 25-0 26+1 | -2.0 | +0.7 | SOMETIMES |
| px_ZB | 1 s | 1 min / 1 min | 199 | 0.491 | 0.488 | +0.3 | +0.2 | 0.98 | -0.07 (-0.20) | 23+3 24+2 25+1 26-0 | -1.1 | +0.3 | SOMETIMES |
| liq10_wall | 1 s | 15 s / 300 s | 385 | 0.511 | 0.510 | +0.2 | +0.2 | 0.98 | +0.14 (+0.37) | 23+2 24-0 25+0 26+0 | -0.9 | +0.8 | SOMETIMES |
| uw_gam_NDX | 1 min | 300 s / 300 s | 63 | 0.514 | 0.509 | +0.5 | +0.2 | 0.98 | +0.21 (+0.56) | 24- 25+1 26+1 | +0.8 | +1.5 | SOMETIMES |
| px_RTY | 1 s | 15 s / 300 s | 254 | 0.499 | 0.496 | +0.2 | +0.2 | 0.98 | -0.20 (-0.55) | 23+1 24+2 25+0 26+1 | +0.4 | +1.9 | SOMETIMES |
| uw_gamdir_NDX | 1 min | 300 s / 300 s | 80 | 0.497 | 0.494 | +0.3 | +0.1 | 0.98 | +0.17 (+0.45) | 24+4 25+1 26-0 | -2.1 | -2.2 | NEVER |
| uw_tide_SPY | 1 min | 300 s / 300 s | 53 | 0.516 | 0.515 | +0.1 | +0.0 | 1.00 | +0.95 (+2.57) | 24- 25+4 26-1 | +3.6 | +0.2 | SOMETIMES |
| l3_pull | 1 s | 1 s / 1 s | 1433 | 0.500 | 0.500 | +0.0 | +0.0 | 1.00 | +0.00 (+0.01) | 23+1 24+0 25+1 26-0 | -0.3 | -0.1 | NEVER |
| px_6B | 1 s | 1 s / 1 s | 1646 | 0.501 | 0.501 | -0.0 | -0.0 | 1.00 | -0.00 (-0.00) | 23+0 24+1 25+0 26-0 | +0.6 | -0.3 | NEVER |

### NY PM

| feed | native | window / horizon | fires per month | hit | null | edge pp | z | q | follow bp (pts) | by year (pp) | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| px_ES | 1 s | 1 s / 1 s | 570 | 0.530 | 0.493 | +3.7 | +3.5 | 0.07 | +0.01 (+0.02) | 23+4 24+1 25+3 26+4 | +6.5 | +5.4 | STEADY LEADER |
| px_6B | 1 s | 1 s / 1 s | 1407 | 0.506 | 0.496 | +0.9 | +1.9 | 0.72 | +0.01 (+0.02) | 23+1 24+1 25+1 26+1 | -0.6 | +1.2 | SOMETIMES |
| nq10_pull | 1 s | 5 s / 300 s | 454 | 0.516 | 0.501 | +1.5 | +1.7 | 0.73 | +0.08 (+0.22) | 23+3 24+1 25+2 26+1 | -1.7 | +0.5 | SOMETIMES |
| nq10_imb5 | 1 s | 1 s / 300 s | 811 | 0.502 | 0.493 | +0.9 | +1.4 | 0.92 | +0.09 (+0.25) | 23+1 24+0 25+1 26+1 | +1.1 | +1.5 | SOMETIMES |
| l3_wall30 | 1 s | 1 min / 1 min | 636 | 0.509 | 0.500 | +0.9 | +1.2 | 0.95 | +0.02 (+0.05) | 23-0 24+1 25+1 26+0 | +1.1 | +1.1 | SOMETIMES |
| px_ZN | 1 s | 15 s / 300 s | 266 | 0.514 | 0.501 | +1.3 | +1.1 | 0.98 | +0.30 (+0.82) | 23-1 24+2 25+0 26+1 | +5.0 | +3.0 | SOMETIMES |
| nq10_big | 1 s | 300 s / 300 s | 107 | 0.514 | 0.497 | +1.7 | +0.9 | 0.98 | +0.00 (+0.01) | 23+6 24-1 25+3 26-1 | -5.6 | -0.8 | NEVER |
| uw_np_SPY | 1 min | 1 min / 300 s | 166 | 0.523 | 0.506 | +1.7 | +0.9 | 0.98 | +0.32 (+0.87) | 24-0 25+1 26+1 | -0.1 | +3.4 | SOMETIMES |
| px_6J | 1 s | 1 min / 1 min | 201 | 0.513 | 0.502 | +1.1 | +0.9 | 0.98 | +0.03 (+0.08) | 23+2 24-0 25+1 26+1 | +4.3 | +2.2 | SOMETIMES |
| liq10_wall | 1 s | 300 s / 300 s | 156 | 0.509 | 0.497 | +1.2 | +0.8 | 0.98 | +0.22 (+0.59) | 23-1 24+2 25+1 26+3 | +1.0 | +4.0 | SOMETIMES |
| px_ZB | 1 s | 1 min / 1 min | 166 | 0.503 | 0.491 | +1.2 | +0.8 | 0.98 | +0.05 (+0.14) | 23-0 24+1 25+1 26+1 | +0.2 | -0.0 | NEVER |
| nq10_trd | 1 s | 1 min / 300 s | 211 | 0.505 | 0.502 | +0.3 | +0.2 | 0.98 | +0.02 (+0.04) | 23-3 24+1 25+0 26+2 | +6.8 | +2.2 | SOMETIMES |
| uw_tide | 1 min | 1 min / 300 s | 203 | 0.508 | 0.504 | +0.4 | +0.2 | 0.98 | +0.08 (+0.21) | 24+4 25-1 26+0 | -0.9 | -0.2 | NEVER |
| uw_gamdir_NDX | 1 min | 300 s / 300 s | 148 | 0.506 | 0.502 | +0.4 | +0.2 | 0.98 | -0.07 (-0.19) | 24-2 25+2 26+1 | -2.1 | -0.8 | NEVER |
| uw_tide_QQQ | 1 min | 1 min / 300 s | 206 | 0.505 | 0.502 | +0.3 | +0.2 | 0.98 | +0.18 (+0.47) | 24-1 25+1 26+0 | +1.9 | +1.2 | SOMETIMES |
| nq10_add | 1 s | 1 s / 1 s | 934 | 0.502 | 0.501 | +0.1 | +0.1 | 0.98 | +0.01 (+0.02) | 23+2 24+1 25-0 26+0 | +0.4 | -0.1 | NEVER |
| px_YM | 1 s | 1 s / 1 s | 1834 | 0.501 | 0.501 | -0.0 | -0.0 | 1.00 | -0.01 (-0.02) | 23-1 24+0 25+0 26+1 | -0.1 | +1.1 | NEVER |
| l3_add | 1 s | 15 s / 15 s | 543 | 0.498 | 0.499 | -0.1 | -0.1 | 1.00 | -0.01 (-0.02) | 23+2 24-0 25+0 26-0 | -0.8 | -1.8 | NEVER |
| uw_gam_SPX | 1 min | 300 s / 300 s | 125 | 0.501 | 0.503 | -0.2 | -0.1 | 1.00 | +0.20 (+0.54) | 24-0 25+2 26-1 | +0.3 | +1.2 | NEVER |
| px_GC | 1 s | 5 s / 300 s | 653 | 0.499 | 0.500 | -0.1 | -0.1 | 1.00 | +0.02 (+0.04) | 23-1 24+1 25+0 26-1 | +0.7 | -0.5 | NEVER |
| uw_gam_QQQ | 1 min | 300 s / 300 s | 143 | 0.482 | 0.484 | -0.2 | -0.1 | 1.00 | -0.24 (-0.66) | 24+5 25+1 26-0 | -4.3 | +0.6 | NEVER |
| px_6C | 1 s | 1 s / 1 s | 1356 | 0.503 | 0.504 | -0.1 | -0.1 | 1.00 | +0.01 (+0.02) | 23+0 24-0 25+0 26+0 | -0.3 | +0.3 | NEVER |
| px_RTY | 1 s | 5 s / 300 s | 403 | 0.492 | 0.493 | -0.2 | -0.2 | 1.00 | +0.04 (+0.12) | 23+2 24+1 25-2 26+1 | +0.8 | +2.8 | NEVER |
| liq10_imb | 1 s | 15 s / 300 s | 512 | 0.500 | 0.502 | -0.2 | -0.2 | 1.00 | -0.10 (-0.27) | 23+1 24+0 25-0 26+1 | +2.9 | +2.2 | NEVER |
| px_6E | 1 s | 1 s / 1 s | 1715 | 0.503 | 0.504 | -0.1 | -0.2 | 1.00 | +0.00 (+0.00) | 23+0 24+1 25+0 26-0 | -0.7 | -1.1 | NEVER |

(top 25 per session by judge z; full table in agg1.json. Note: "follow" in pts = bp x 2.7.)

## 5. The five steadiest leaders per session (score = 2 x share of years positive + last-3M positive + last-6M positive + judge z/5; either variant, judge edge > 0)
**Asia**

| rank | feed | variant | window / horizon | edge pp | follow bp | by year | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|
| 1 | l3_wall120 | all | 15 s / 15 s | +1.4 | +0.00 | 23- 24+4 25+2 26+1 | +0.8 | +1.2 | SOMETIMES |
| 2 | px_RTY | nqflat | 1 s / 1 s | +2.5 | +0.01 | 23- 24- 25- 26+2 | +1.5 | +2.0 | SOMETIMES |
| 3 | l3_add | nqflat | 1 s / 1 s | +1.7 | +0.01 | 23- 24- 25- 26+2 | +1.1 | +1.1 | SOMETIMES |
| 4 | px_6E | all | 5 s / 5 s | +0.6 | +0.01 | 23- 24- 25- 26+1 | +1.7 | +0.2 | SOMETIMES |
| 5 | px_YM | all | 5 s / 5 s | +0.4 | +0.02 | 23- 24+1 25- 26+0 | +0.3 | +0.2 | SOMETIMES |

**London**

| rank | feed | variant | window / horizon | edge pp | follow bp | by year | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|
| 1 | px_NKD | all | 5 s / 300 s | +4.1 | +0.26 | 23+10 24- 25+6 26+4 | +2.4 | +4.1 | SOMETIMES |
| 2 | m_META | all | 1 min / 1 min | +6.5 | +0.07 | 24- 25+10 26+7 | +2.9 | +5.9 | SOMETIMES |
| 3 | l3_pull | all | 1 s / 1 s | +0.6 | +0.00 | 23+2 24+3 25+1 26+0 | +1.1 | +0.4 | SOMETIMES |
| 4 | l3_add | all | 15 s / 300 s | +3.0 | +0.28 | 23- 24- 25+7 26+3 | +4.1 | +5.1 | SOMETIMES |
| 5 | nq10_ofi | all | 5 s / 300 s | +3.0 | +0.21 | 23+2 24- 25+6 26+2 | +1.1 | +2.0 | SOMETIMES |

**NY AM**

| rank | feed | variant | window / horizon | edge pp | follow bp | by year | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|
| 1 | px_ES | nqflat | 1 s / 1 s | +2.7 | +0.00 | 23+4 24+3 25+3 26+2 | +1.5 | +2.9 | SOMETIMES |
| 2 | liq10_imb | all | 1 s / 300 s | +1.6 | +0.13 | 23+0 24+0 25+1 26+1 | +0.6 | +0.7 | SOMETIMES |
| 3 | l3_fill | nqflat | 1 min / 300 s | +3.5 | +0.42 | 23+2 24+1 25+5 26+3 | +6.1 | +2.3 | SOMETIMES |
| 4 | m_NKD | all | 15 min / 15 min | +4.5 | +1.74 | 23+1 24+4 25+2 26+5 | +5.5 | +5.4 | SOMETIMES |
| 5 | nq10_imb5 | nqflat | 5 s / 300 s | +1.3 | +0.38 | 23+2 24+0 25+2 26+1 | +0.0 | +0.5 | SOMETIMES |

**NY PM**

| rank | feed | variant | window / horizon | edge pp | follow bp | by year | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|
| 1 | px_ES | nqflat | 1 s / 1 s | +3.7 | +0.01 | 23+4 24+1 25+3 26+4 | +6.5 | +5.4 | STEADY LEADER |
| 2 | px_6C | all | 1 s / 1 s | +0.9 | +0.01 | 23+0 24+1 25+1 26+1 | +0.4 | +1.0 | SOMETIMES |
| 3 | px_6E | all | 1 s / 1 s | +0.7 | +0.00 | 23+0 24+1 25+1 26+1 | +0.4 | +0.4 | SOMETIMES |
| 4 | nq10_imb5 | nqflat | 1 s / 300 s | +0.9 | +0.09 | 23+1 24+0 25+1 26+1 | +1.1 | +1.5 | SOMETIMES |
| 5 | uw_tide_QQQ | all | 1 min / 300 s | +1.5 | +0.32 | 24+4 25+4 26+1 | +5.2 | +1.8 | SOMETIMES |

STEADY LEADERS (all sessions, both variants): px_ES NY PM nqflat (1 s/1 s)

## 6. NQ TURNS: which feeds turned first (descriptive; hindsight-defined turn)
Run = NQ moved >= 3 sigma over 300 s; turn = the extreme found in the next 300 s that NQ then retraces by >= 40% of the run (about 101 turns per month). Lead = time of the feed's own extreme minus the NQ extreme, in seconds, window drift removed; negative = feed turned BEFORE NQ. "Early" = lead <= -5 s (<= -60 s for minute feeds). Null = random windows with the same direction mix (what chance and noise give).
**Asia**

| feed | turns (judge) | median lead s (null) | early share | null | diff pp | z | by year (pp) | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|---|
| liq10_wall | 413 | -83 (-10) | 0.688 | 0.513 | +17.5 | +3.8 | 23- 24- 25- 26+16 | +17 | +17 | SOMETIMES |
| nq10_pull | 362 | -60 (+20) | 0.622 | 0.461 | +16.1 | +3.2 | 23- 24- 25- 26+17 | +27 | +19 | SOMETIMES |
| px_CL | 362 | -23 (+35) | 0.519 | 0.425 | +9.5 | +1.8 | 23- 24- 25- 26+9 | +17 | +10 | SOMETIMES |
| px_ZN | 360 | -48 (-9) | 0.606 | 0.514 | +9.2 | +1.7 | 23- 24- 25- 26+7 | +11 | +0 | SOMETIMES |
| px_YM | 413 | +3 (+26) | 0.429 | 0.367 | +6.2 | +1.3 | 23- 24- 25- 26+6 | -13 | +6 | NEVER |
| liq10_imb | 413 | -63 (-44) | 0.620 | 0.570 | +5.0 | +1.1 | 23- 24- 25- 26+4 | +7 | +3 | NEVER |
| px_NKD | 411 | +10 (+41) | 0.397 | 0.347 | +5.0 | +1.1 | 23- 24- 25- 26+6 | +7 | +9 | NEVER |
| l3_fill | 403 | -1 (+1) | 0.432 | 0.384 | +4.8 | +1.0 | 23- 24- 25- 26+4 | +3 | +1 | NEVER |
| nq10_ofi | 362 | -1 (+0) | 0.423 | 0.380 | +4.2 | +0.8 | 23- 24- 25- 26+5 | - | +1 | NEVER |
| m_6C | 366 | -18 (+3) | 0.423 | 0.386 | +3.8 | +0.7 | 23- 24- 25- 26+4 | +24 | +18 | NEVER |

**London**

| feed | turns (judge) | median lead s (null) | early share | null | diff pp | z | by year (pp) | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|---|
| uw_gam_SPX | 140 | +17 (+114) | 0.379 | 0.186 | +19.3 | +2.7 | 24- 25- 26+19 | - | +24 | SOMETIMES |
| l3_fill | 411 | -3 (+0) | 0.472 | 0.343 | +12.9 | +2.4 | 23- 24- 25- 26+15 | - | +19 | SOMETIMES |
| px_ZN | 386 | -18 (+17) | 0.565 | 0.429 | +13.6 | +2.3 | 23- 24- 25- 26+11 | - | +10 | SOMETIMES |
| m_6J | 418 | -34 (+28) | 0.435 | 0.324 | +11.2 | +2.1 | 23- 24- 25- 26+12 | +16 | +13 | SOMETIMES |
| liq10_wall | 418 | -50 (-10) | 0.620 | 0.517 | +10.3 | +2.0 | 23- 24- 25- 26+8 | +8 | +8 | SOMETIMES |
| nq10_pull | 384 | -34 (-1) | 0.602 | 0.479 | +12.2 | +1.9 | 23- 24- 25- 26+12 | - | +15 | SOMETIMES |
| px_6J | 418 | -31 (+32) | 0.550 | 0.452 | +9.9 | +1.7 | 23- 24- 25- 26+9 | -6 | +6 | SOMETIMES |
| nq10_ofi | 384 | -2 (+0) | 0.471 | 0.375 | +9.6 | +1.7 | 23- 24- 25- 26+9 | - | +7 | SOMETIMES |
| liq10_imb | 418 | -59 (-2) | 0.586 | 0.495 | +9.1 | +1.7 | 23- 24- 25- 26+8 | +10 | +7 | SOMETIMES |
| nq10_imb5 | 384 | -58 (+4) | 0.586 | 0.487 | +9.9 | +1.6 | 23- 24- 25- 26+14 | - | +15 | SOMETIMES |

**NY AM**

| feed | turns (judge) | median lead s (null) | early share | null | diff pp | z | by year (pp) | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|---|
| liq10_wall | 763 | -67 (-16) | 0.641 | 0.534 | +10.6 | +3.1 | 23+3 24+1 25+15 26+7 | -9 | +10 | SOMETIMES |
| l3_fill | 756 | +0 (+1) | 0.413 | 0.321 | +9.2 | +2.9 | 23+1 24+7 25+7 26+6 | +13 | +8 | SOMETIMES |
| nq10_trd | 768 | -4 (+0) | 0.499 | 0.419 | +8.0 | +2.4 | 23+4 24-0 25+4 26+8 | +19 | +12 | SOMETIMES |
| nq10_ofi | 768 | +0 (+0) | 0.405 | 0.348 | +5.7 | +1.7 | 23-2 24+3 25+9 26-0 | +11 | +5 | SOMETIMES |
| l3_wall30 | 756 | -16 (-1) | 0.542 | 0.488 | +5.4 | +1.6 | 23+9 24+1 25+2 26+8 | +13 | +13 | SOMETIMES |
| px_ES | 716 | +0 (+0) | 0.318 | 0.272 | +4.7 | +1.5 | 23+8 24+0 25+9 26+4 | +16 | +6 | NEVER |
| nq10_pull | 768 | -22 (-8) | 0.553 | 0.507 | +4.7 | +1.4 | 23-6 24-5 25+7 26-1 | -13 | -1 | NEVER |
| nq10_big | 646 | -10 (-2) | 0.536 | 0.487 | +4.9 | +1.2 | 23+3 24+3 25+2 26+6 | +9 | +5 | NEVER |
| m_AMZN | 399 | +88 (+96) | 0.276 | 0.260 | +1.6 | +0.4 | 24+1 25-8 26+1 | +8 | +4 | NEVER |
| nq10_imb5 | 768 | -32 (-18) | 0.544 | 0.530 | +1.4 | +0.4 | 23+4 24+8 25+1 26+3 | -0 | +1 | NEVER |

**NY PM**

| feed | turns (judge) | median lead s (null) | early share | null | diff pp | z | by year (pp) | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|---|
| nq10_ofi | 632 | -1 (+0) | 0.418 | 0.338 | +7.9 | +2.6 | 23+6 24+4 25+11 26+7 | +17 | +11 | SOMETIMES |
| l3_wall120 | 611 | +13 (+31) | 0.462 | 0.383 | +7.9 | +2.5 | 23+4 24+1 25+7 26+9 | +14 | +11 | SOMETIMES |
| nq10_pull | 632 | -20 (-4) | 0.573 | 0.500 | +7.3 | +2.3 | 23-3 24+5 25+1 26+12 | +19 | +15 | SOMETIMES |
| px_CL | 635 | -18 (+22) | 0.517 | 0.451 | +6.5 | +2.0 | 23+5 24-3 25-1 26+15 | +15 | +17 | SOMETIMES |
| liq10_wall | 618 | -48 (-20) | 0.594 | 0.548 | +4.6 | +1.5 | 23+5 24+8 25+11 26+2 | +17 | +7 | NEVER |
| uw_tide_SPY | 317 | -64 (-43) | 0.511 | 0.456 | +5.5 | +1.3 | 24+10 25+8 26+5 | -0 | +4 | NEVER |
| nq10_add | 632 | +0 (+3) | 0.399 | 0.360 | +3.9 | +1.2 | 23+9 24-6 25+3 26+3 | +5 | +11 | NEVER |
| m_ZN | 615 | -73 (-58) | 0.530 | 0.499 | +3.1 | +1.0 | 23-12 24+1 25-4 26+4 | +11 | +4 | NEVER |
| nq10_trd | 632 | -3 (-1) | 0.487 | 0.456 | +3.1 | +1.0 | 23+6 24+6 25+4 26+4 | -5 | +2 | NEVER |
| l3_fill | 611 | -1 (+0) | 0.414 | 0.384 | +3.0 | +1.0 | 23+7 24+6 25+6 26+3 | +2 | -2 | NEVER |

## 7. What could NOT be measured at fine resolution (data shopping list for Josh; no quote, nothing bought)
- Held only as 1-minute bars (no second-level lead can be tested): the seven megacaps (NVDA MSFT AAPL AMZN META GOOGL TSLA), QQQ SPY IWM DIA, NYSE TICK, UW spot gamma / tide / net premium (one-minute updates at best). Their history starts 2024-10 (megacaps, ETFs, UW), NYSE TICK 2023-04. Price feeds YM, NKD, ZB, 6E, 6J, 6B, 6C, CL, GC, ZN are second-level prints with staleness (age_ columns).
- Not on the box at all: market internals other than NYSE TICK (NYSE/Nasdaq A/D, TRIN, VOLD, Nasdaq TICK), VIX / VXN / VIX futures term, 6A, HG (copper), BTC/MBT beyond a few spot files, megacap tick/L1 data, options trade flow by strike at second resolution before 18 Nov, SPX/NQ options order flow ticks. These are the places where a faster feed could plausibly lead NQ and where nothing can be tested today.

## 8. Caveats
- Statistics at 1-5 s are about information speed, not trading edge: follow moves of 0.01-0.1 bp are far below a tick. A lead has to survive fees and fill delay of the engine (LAT 0.5-1.0 s) to matter; this page does not claim it does.
- Index prices, bond/FX/crude mids and book features are second-resolution from the L2/L3 tapes with their own staleness (age_ columns); prices older than 60 s are dropped. Feeds with 1-minute updates (UW, TICK, stocks) are tested only at 1-60 min horizons and say nothing about seconds.
- Same-moment correlation is not causation: ES co-moves because it is the same equity index; it is the best NOW-read of NQ but NQ often leads ES in ticks (see 1 s rows).
- Overlap and multiple testing: refractory thinning removes overlapping outcomes inside a feed, not across feeds (the feeds are strongly correlated); BH uses the judged rows only, so read the q column with that in mind.
