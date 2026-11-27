# WHAT_MOVES_NQ: of all the feeds on the box, what moves NQ, and what moves BEFORE NQ (W-DYNL). DISCOVERY, NOT A RESULT
Generated 2026-11-27T18:34:02Z. Order: Josh 17:51Z 27 Nov ("what moves NQ and what moves before NQ moves"). Searching is right here; nothing below is a design: the only use is WHICH FEEDS SIT ON WHICH SCREEN IN WHICH SESSION. Code code/th_dynl/wm_run.py, wm_agg.py, wm_turns.py, wm_turn_agg.py, wm_page.py; raw counts /mnt/l2/l2vast/_dynexit/wm/ (server C).

## ANSWER FIRST
1. MOVES WITH NQ (same moment): ES carries NQ. Correlation of the ES move with the NQ move over the same 1 s / 5 s / 60 s is 0.74-0.89 / 0.82-0.94 / 0.86-0.95 (by session); RTY 0.58-0.74 / 0.60-0.77 / 0.62-0.79; YM at 60 s 0.60-0.83; then NQ's own order book and flow (MBO l3_add 0.61-0.78 at 1 s, nq10 add/ofi, fills). Bonds, FX, crude, gold, Nikkei, megacaps, QQQ/SPY and the UW feeds co-move much less at these horizons (section 3).
2. MOVES BEFORE NQ: there is one steady, repeatable lead and it is tiny. When ES moves >= 2 sigma in the last second while NQ has NOT yet moved, NQ goes the same way in the next second more often than chance: Asia 53.7% vs 50.6% null (+3.2 pp; by year 23+8 24+6 25+6 26+2; label STEADY LEADER); London 53.4% vs 49.9% null (+3.5 pp; by year 23+4 24+5 25+6 26+2; label STEADY LEADER); NY AM 52.4% vs 49.9% null (+2.5 pp; by year 23+2 24+2 25+3 26+2; label STEADY LEADER); NY PM 52.9% vs 50.5% null (+2.4 pp; by year 23+5 24+0 25+2 26+3; label STEADY LEADER). The NQ move that follows is 0.02 bp or less (about 0.05 point): a real information lead, far below one tick, so not a trading signal by itself.
   Beyond ES, 11 of 354 judged rows are STEADY LEADERS (list at the end of section 5); they are almost all 1-second reads (RTY, NQ's own MBO adds/fills and trade flow in Asia, Nikkei 5 s in Asia) with follow moves of 0.00-0.02 bp. At 300 s the feeds with the largest follow moves (UW gamma and tide, stock leaders NVDA/META, NKD) are only SOMETIMES: positive on the judge set but not in every year, and their history starts in 2024-10.
3. TURNS (table 6): turn leads are not 1-second effects. Asia: liq10_wall -44 s (null -22), nq10_imb5 -53 s (null -17), nq10_pull -19 s (null +0); London: liq10_imb -53 s (null -23), liq10_wall -53 s (null -22), nq10_ofi -1 s (null +0), nq10_trd -8 s (null +0); NY AM: no STEADY turn leader; NY PM: no STEADY turn leader
4. STABILITY: every row carries its judge set (last 40% of the feed months, never used to pick the setting), each year, last 3 and last 6 months, and a label. Only STEADY rows are candidates for a screen vote. Everything examined: 358 (feed, window, horizon) cells x 4 sessions x 2 variants; BH q=10% over the 354 judged rows.

## 1. Method (all causal; DISCOVERY)
- Grid: NQ mid per second (age_ feed), 46 months 2023-02..2026-11. Feed x_w(t) = its move over the last w seconds (price feeds: return in bp; order-flow feeds: net sum over w; level feeds: mean over w; UW cumulative feeds: change over w), scaled by its own rolling std over the previous 3600 s (ending at t-1). FIRE when |x|/sigma >= 2. NQ-FLAT variant: additionally NQ's own move over the same w is < 0.5 of its sigma, i.e. the lead is not just NQ moving first.
- Outcome: NQ mid return over the next h = w seconds (and 300 s), HIT = same sign as the feed (sign of the feed fixed on its first 60% of months from the same-moment covariance: e.g. ZN, 6J, dollar, UW tide, book imbalance come out negative). Fires thinned by a refractory period of max(w,h) so outcomes do not overlap. 1-minute feeds (xmkt 12 instruments, megacaps, QQQ/SPY/IWM/DIA, TICK, UW 1-min) are evaluated at their own update times with w, h = 1/5/15/60 min.
- NULL (matched base rate): the same fires, scored against NQ outcomes taken 30-120 min later (two random shifts per month): same fire process, same sign, same volatility regime. Edge = hit rate - null hit rate.
- Selection: per feed, session and variant the (w, h) with the best edge z on the FIT months (first 60% of the feed's months) is chosen, then judged ONCE on the last 40%; BH over all judged rows.
- Sessions (ET of the fire time): Asia 18:00-03:00, London 03:00-08:30, NY AM 08:30-12:00, NY PM 12:00-16:00.
- Labels: STEADY LEADER = judge edge >= 1.0 pp, BH q <= 0.10, positive in >= 75% of the years with >= 200 fires AND at least 3 such years, positive in the last 3 AND last 6 months. NOTE: UW, megacaps and QQQ/SPY start 2024-10 (3 calendar years), so they can reach STEADY only with all three years positive. SOMETIMES = positive on the judge set and (q <= 0.10 or positive in the last 6 months). NEVER otherwise.
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
| 5 s | px_ES 0.82, px_RTY 0.66, l3_add 0.56, nq10_ofi 0.50, l3_fill 0.50, nq10_add 0.46, nq10_trd 0.44, nq10_pull 0.17 |
| 1 min | px_ES 0.86, m_ES 0.83, px_RTY 0.73, m_RTY 0.69, m_YM 0.69, nq10_ofi 0.57, l3_fill 0.57, px_YM 0.57 |
| 300 s | m_ES 0.88, px_ES 0.87, px_RTY 0.76, m_YM 0.75, m_RTY 0.75, px_YM 0.69, nq10_ofi 0.61, l3_fill 0.60 |

**London**

| window | top feeds (corr) |
|---|---|
| 1 s | px_ES 0.84, l3_add 0.72, px_RTY 0.67, nq10_add 0.64, nq10_ofi 0.49, l3_fill 0.49, nq10_trd 0.45, nq10_pull 0.43 |
| 5 s | px_ES 0.91, px_RTY 0.72, l3_add 0.67, nq10_add 0.55, nq10_ofi 0.52, l3_fill 0.52, nq10_trd 0.47, nq10_pull 0.31 |
| 1 min | px_ES 0.94, m_ES 0.93, px_RTY 0.75, m_YM 0.73, m_RTY 0.73, px_YM 0.64, nq10_ofi 0.60, l3_fill 0.59 |
| 300 s | px_ES 0.95, m_ES 0.94, px_RTY 0.76, m_YM 0.75, m_RTY 0.75, px_YM 0.73, px_NKD 0.68, m_NKD 0.65 |

**NY AM**

| window | top feeds (corr) |
|---|---|
| 1 s | px_ES 0.87, l3_add 0.78, nq10_add 0.68, px_RTY 0.58, l3_fill 0.51, nq10_ofi 0.51, nq10_pull 0.48, nq10_trd 0.47 |
| 5 s | px_ES 0.90, l3_add 0.74, px_RTY 0.60, l3_fill 0.60, nq10_ofi 0.60, nq10_add 0.54, nq10_trd 0.53, l3_pull -0.38 |
| 1 min | px_ES 0.92, m_ES 0.91, nq10_ofi 0.69, l3_fill 0.69, m_NKD 0.63, px_RTY 0.62, m_RTY 0.62, m_YM 0.60 |
| 300 s | px_ES 0.92, m_ES 0.92, px_NKD 0.73, m_NKD 0.73, nq10_ofi 0.69, l3_fill 0.68, px_RTY 0.63, m_RTY 0.63 |

**NY PM**

| window | top feeds (corr) |
|---|---|
| 1 s | px_ES 0.89, l3_add 0.78, px_RTY 0.74, nq10_add 0.71, nq10_pull 0.52, nq10_ofi 0.49, l3_fill 0.48, nq10_trd 0.45 |
| 5 s | px_ES 0.94, px_RTY 0.77, l3_add 0.72, nq10_add 0.58, nq10_ofi 0.56, l3_fill 0.56, nq10_trd 0.49, nq10_pull 0.40 |
| 1 min | px_ES 0.95, m_ES 0.95, m_YM 0.83, px_RTY 0.79, m_RTY 0.79, px_YM 0.73, nq10_ofi 0.65, l3_fill 0.65 |
| 300 s | px_ES 0.96, m_ES 0.96, m_YM 0.84, px_YM 0.82, m_RTY 0.81, px_RTY 0.81, px_NKD 0.79, m_NKD 0.76 |

(1-minute feeds appear at 60 s and 300 s rows; minute-bar feeds cannot be measured at 1 s or 5 s.)

## 4. Moves BEFORE NQ: all feeds, by session (variant NQ-FLAT = NQ has not moved yet; the setting chosen on the fit months, judged on the last 40%)
### Asia

| feed | native | window / horizon | fires per month | hit | null | edge pp | z | q | follow bp (pts) | by year (pp) | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| px_RTY | 1 s | 1 s / 1 s | 4430 | 0.521 | 0.497 | +2.4 | +8.2 | 0.00 | +0.02 (+0.04) | 23+7 24+4 25+3 26+2 | +1.4 | +1.4 | STEADY LEADER |
| px_ES | 1 s | 1 s / 1 s | 2226 | 0.537 | 0.506 | +3.2 | +7.8 | 0.00 | +0.02 (+0.05) | 23+8 24+6 25+6 26+2 | +0.9 | +1.2 | STEADY LEADER |
| px_GC | 1 s | 1 s / 1 s | 15511 | 0.510 | 0.501 | +0.9 | +6.2 | 0.00 | +0.01 (+0.02) | 23+2 24+1 25+1 26+1 | -0.2 | +0.2 | SOMETIMES |
| px_NKD | 1 s | 5 s / 5 s | 2203 | 0.514 | 0.497 | +1.7 | +4.7 | 0.00 | +0.03 (+0.07) | 23-0 24+1 25+2 26+2 | +0.9 | +1.9 | STEADY LEADER |
| px_6E | 1 s | 1 s / 1 s | 3161 | 0.511 | 0.498 | +1.3 | +4.0 | 0.00 | +0.01 (+0.02) | 23+2 24+1 25+2 26+1 | -0.4 | +0.0 | SOMETIMES |
| l3_add | 1 s | 1 s / 1 s | 2684 | 0.514 | 0.500 | +1.4 | +4.0 | 0.00 | +0.02 (+0.05) | 23+6 24+4 25+1 26+1 | +0.7 | +0.9 | STEADY LEADER |
| nq10_trd | 1 s | 1 s / 1 s | 3434 | 0.513 | 0.502 | +1.2 | +3.8 | 0.00 | +0.01 (+0.03) | 23+4 24+3 25+1 26+1 | +0.3 | +0.6 | STEADY LEADER |
| nq10_add | 1 s | 1 s / 1 s | 3965 | 0.510 | 0.499 | +1.1 | +3.7 | 0.00 | +0.02 (+0.05) | 23+6 24+4 25+2 26+1 | +0.2 | +0.7 | STEADY LEADER |
| l3_fill | 1 s | 1 s / 1 s | 2883 | 0.513 | 0.500 | +1.2 | +3.6 | 0.00 | +0.01 (+0.02) | 23+4 24+3 25+2 26+1 | +1.6 | +0.3 | STEADY LEADER |
| nq10_pull | 1 s | 1 s / 1 s | 4743 | 0.505 | 0.497 | +0.8 | +3.2 | 0.01 | +0.00 (+0.00) | 23+2 24+1 25+2 26-0 | +0.5 | -0.2 | SOMETIMES |
| nq10_ofi | 1 s | 1 s / 1 s | 2861 | 0.512 | 0.502 | +1.0 | +2.9 | 0.03 | +0.01 (+0.02) | 23+3 24+2 25+1 26+1 | +0.1 | +0.4 | SOMETIMES |
| px_6B | 1 s | 5 s / 5 s | 3602 | 0.506 | 0.500 | +0.6 | +2.1 | 0.19 | +0.01 (+0.03) | 23+1 24+1 25+1 26+1 | -0.3 | +0.1 | SOMETIMES |
| px_6C | 1 s | 5 s / 5 s | 2816 | 0.505 | 0.502 | +0.3 | +1.0 | 0.79 | +0.00 (+0.01) | 23+0 24+1 25+1 26+0 | +0.1 | -0.5 | NEVER |
| px_ZB | 1 s | 1 min / 300 s | 402 | 0.503 | 0.496 | +0.7 | +0.9 | 0.81 | -0.01 (-0.03) | 23-0 24+2 25+1 26+1 | -0.8 | +1.6 | SOMETIMES |
| nq10_imb5 | 1 s | 300 s / 300 s | 381 | 0.494 | 0.487 | +0.7 | +0.8 | 0.83 | -0.14 (-0.38) | 23-0 24+1 25-0 26+2 | +1.0 | +1.4 | SOMETIMES |
| l3_wall30 | 1 s | 300 s / 300 s | 536 | 0.505 | 0.503 | +0.2 | +0.3 | 0.90 | +0.02 (+0.06) | 23-1 24-0 25-0 26+0 | -0.4 | +0.7 | SOMETIMES |
| l3_pull | 1 s | 15 s / 15 s | 2556 | 0.498 | 0.497 | +0.1 | +0.2 | 0.93 | -0.01 (-0.02) | 23+1 24-0 25-0 26+0 | +0.5 | -0.0 | NEVER |
| px_6J | 1 s | 1 min / 1 min | 656 | 0.499 | 0.498 | +0.1 | +0.2 | 0.93 | -0.00 (-0.01) | 23-0 24-0 25+1 26+0 | +0.2 | +0.1 | SOMETIMES |
| px_YM | 1 s | 1 min / 1 min | 604 | 0.501 | 0.499 | +0.1 | +0.2 | 0.94 | +0.02 (+0.06) | 23-1 24+1 25+0 26+1 | +0.2 | +1.2 | SOMETIMES |
| l3_wall120 | 1 s | 15 s / 300 s | 1251 | 0.505 | 0.506 | -0.0 | -0.1 | 0.97 | +0.02 (+0.05) | 23-1 24+0 25-1 26+0 | -0.6 | -0.6 | NEVER |
| px_ZN | 1 s | 1 min / 1 min | 693 | 0.502 | 0.504 | -0.2 | -0.3 | 0.99 | -0.00 (-0.01) | 23+1 24+1 25+0 26+1 | -0.1 | +0.7 | NEVER |
| nq10_big | 1 s | 15 s / 15 s | 119 | 0.492 | 0.499 | -0.7 | -0.5 | 0.99 | +0.03 (+0.08) | 23+1 24+4 25+3 26-2 | -7.1 | -4.7 | NEVER |
| liq10_imb | 1 s | 300 s / 300 s | 306 | 0.492 | 0.497 | -0.5 | -0.5 | 0.99 | -0.04 (-0.11) | 23-2 24-1 25-0 26-0 | +0.6 | +0.8 | NEVER |
| liq10_wall | 1 s | 300 s / 300 s | 274 | 0.491 | 0.503 | -1.3 | -1.2 | 0.99 | +0.01 (+0.02) | 23-2 24+0 25-2 26-0 | -1.2 | -0.3 | NEVER |
| px_CL | 1 s | 15 s / 15 s | 3252 | 0.493 | 0.501 | -0.8 | -2.7 | 1.00 | -0.03 (-0.08) | 23+1 24+0 25-0 26-1 | -0.5 | -0.1 | NEVER |

### London

| feed | native | window / horizon | fires per month | hit | null | edge pp | z | q | follow bp (pts) | by year (pp) | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| px_ES | 1 s | 1 s / 1 s | 1368 | 0.534 | 0.499 | +3.5 | +6.8 | 0.00 | +0.02 (+0.04) | 23+4 24+5 25+6 26+2 | +0.4 | +1.1 | STEADY LEADER |
| px_GC | 1 s | 1 s / 1 s | 10593 | 0.508 | 0.501 | +0.6 | +3.7 | 0.00 | +0.01 (+0.02) | 23+0 24+0 25+0 26+1 | +0.5 | +0.6 | SOMETIMES |
| px_6C | 1 s | 1 s / 1 s | 1691 | 0.512 | 0.501 | +1.1 | +2.5 | 0.09 | +0.01 (+0.03) | 23+0 24+0 25+1 26+1 | -0.5 | +0.2 | SOMETIMES |
| px_6E | 1 s | 1 s / 1 s | 2543 | 0.509 | 0.501 | +0.8 | +2.3 | 0.15 | +0.00 (+0.01) | 23+0 24+1 25+1 26+1 | +0.2 | -0.0 | NEVER |
| px_6B | 1 s | 1 s / 1 s | 2250 | 0.509 | 0.500 | +0.8 | +2.2 | 0.16 | +0.01 (+0.02) | 23+1 24+0 25+1 26+1 | +0.1 | +0.2 | SOMETIMES |
| l3_fill | 1 s | 1 s / 1 s | 1534 | 0.507 | 0.500 | +0.7 | +1.5 | 0.58 | +0.00 (+0.01) | 23+2 24+1 25+0 26+1 | -0.3 | +0.6 | SOMETIMES |
| uw_gam_SPX | 1 min | 1 min / 1 min | 169 | 0.527 | 0.506 | +2.1 | +1.2 | 0.69 | +0.11 (+0.31) | 24+1 25+1 26+2 | +1.4 | +5.0 | SOMETIMES |
| l3_wall120 | 1 s | 300 s / 300 s | 657 | 0.504 | 0.496 | +0.8 | +1.2 | 0.71 | +0.08 (+0.21) | 23-1 24+0 25+0 26+1 | -0.1 | +0.0 | SOMETIMES |
| liq10_imb | 1 s | 15 s / 300 s | 619 | 0.501 | 0.494 | +0.7 | +1.0 | 0.79 | +0.05 (+0.13) | 23+1 24-0 25+1 26+1 | +0.4 | +0.9 | SOMETIMES |
| px_RTY | 1 s | 1 s / 1 s | 3064 | 0.503 | 0.501 | +0.3 | +0.9 | 0.81 | +0.01 (+0.03) | 23+2 24+0 25+1 26+0 | +0.9 | +0.3 | SOMETIMES |
| nq10_trd | 1 s | 1 s / 1 s | 1708 | 0.502 | 0.498 | +0.3 | +0.8 | 0.84 | -0.00 (-0.00) | 23+2 24+1 25+1 26+1 | -0.1 | +0.1 | SOMETIMES |
| liq10_wall | 1 s | 15 s / 300 s | 639 | 0.500 | 0.496 | +0.4 | +0.6 | 0.85 | -0.03 (-0.07) | 23+1 24-1 25+1 26-0 | -1.8 | -0.3 | NEVER |
| nq10_pull | 1 s | 15 s / 15 s | 1370 | 0.502 | 0.499 | +0.2 | +0.5 | 0.85 | +0.02 (+0.05) | 23-0 24+1 25+1 26+0 | +0.7 | +0.3 | SOMETIMES |
| nq10_imb5 | 1 s | 15 s / 300 s | 773 | 0.503 | 0.500 | +0.3 | +0.5 | 0.87 | -0.00 (-0.01) | 23-0 24+1 25+0 26+1 | -0.8 | +0.2 | SOMETIMES |
| nq10_ofi | 1 s | 1 s / 1 s | 1523 | 0.508 | 0.506 | +0.2 | +0.4 | 0.90 | +0.00 (+0.01) | 23+1 24+1 25+0 26+0 | +1.2 | +0.3 | SOMETIMES |
| px_ZB | 1 s | 300 s / 300 s | 170 | 0.491 | 0.487 | +0.4 | +0.3 | 0.90 | +0.07 (+0.19) | 23+1 24+2 25+1 26+0 | +0.9 | -0.2 | NEVER |
| nq10_big | 1 s | 5 s / 5 s | 76 | 0.503 | 0.502 | +0.2 | +0.1 | 0.97 | +0.03 (+0.09) | 23+1 24+2 25+2 26+0 | +4.6 | +1.4 | SOMETIMES |
| px_ZN | 1 s | 300 s / 300 s | 299 | 0.503 | 0.505 | -0.2 | -0.3 | 0.98 | +0.09 (+0.25) | 23+0 24+1 25+2 26-0 | +0.4 | -0.8 | NEVER |
| uw_gam_QQQ | 1 min | 300 s / 300 s | 48 | 0.505 | 0.516 | -1.1 | -0.3 | 0.99 | +0.14 (+0.37) | 24- 25+1 26-3 | -4.0 | +1.7 | NEVER |
| px_NKD | 1 s | 1 s / 1 s | 953 | 0.499 | 0.501 | -0.2 | -0.3 | 0.99 | -0.00 (-0.01) | 23-1 24-0 25+0 26+0 | -0.8 | -0.6 | NEVER |
| px_6J | 1 s | 1 s / 300 s | 970 | 0.498 | 0.501 | -0.3 | -0.5 | 0.99 | -0.05 (-0.14) | 23+1 24+0 25-0 26-0 | -1.1 | -1.3 | NEVER |
| l3_pull | 1 s | 1 s / 1 s | 2406 | 0.497 | 0.499 | -0.2 | -0.6 | 0.99 | -0.00 (-0.01) | 23+1 24+0 25-1 26+0 | -0.2 | +0.1 | NEVER |
| px_YM | 1 s | 5 s / 5 s | 2753 | 0.498 | 0.500 | -0.2 | -0.7 | 0.99 | -0.00 (-0.01) | 23-1 24+1 25+1 26-0 | +0.1 | -1.2 | NEVER |
| px_CL | 1 s | 300 s / 300 s | 224 | 0.490 | 0.499 | -0.8 | -0.7 | 0.99 | -0.28 (-0.76) | 23-1 24-0 25-1 26+0 | +0.4 | +2.1 | NEVER |
| l3_wall30 | 1 s | 5 s / 300 s | 541 | 0.495 | 0.501 | -0.5 | -0.7 | 0.99 | -0.05 (-0.13) | 23-1 24-1 25+0 26-1 | -2.5 | -1.1 | NEVER |

### NY AM

| feed | native | window / horizon | fires per month | hit | null | edge pp | z | q | follow bp (pts) | by year (pp) | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| px_ES | 1 s | 1 s / 1 s | 470 | 0.524 | 0.499 | +2.5 | +3.0 | 0.02 | +0.00 (+0.01) | 23+2 24+2 25+3 26+2 | +1.0 | +2.2 | STEADY LEADER |
| l3_fill | 1 s | 1 min / 300 s | 137 | 0.523 | 0.493 | +2.9 | +2.1 | 0.23 | +0.36 (+0.97) | 23+2 24-2 25+4 26+2 | +8.3 | +2.8 | SOMETIMES |
| l3_add | 1 s | 1 s / 1 s | 539 | 0.513 | 0.501 | +1.2 | +1.7 | 0.46 | +0.01 (+0.03) | 23+3 24+2 25+1 26+0 | +1.1 | +0.3 | SOMETIMES |
| l3_pull | 1 s | 1 s / 1 s | 1443 | 0.500 | 0.494 | +0.6 | +1.3 | 0.69 | +0.00 (+0.01) | 23+1 24+0 25+1 26+0 | +0.7 | +0.2 | SOMETIMES |
| liq10_wall | 1 s | 5 s / 300 s | 573 | 0.511 | 0.502 | +0.8 | +1.2 | 0.69 | +0.19 (+0.51) | 23-0 24-0 25-0 26+2 | +1.9 | +1.1 | SOMETIMES |
| uw_gam_NDX | 1 min | 300 s / 300 s | 64 | 0.515 | 0.485 | +3.0 | +1.1 | 0.78 | +0.21 (+0.57) | 24- 25+1 26+3 | +3.3 | +3.5 | SOMETIMES |
| uw_np_SPY | 1 min | 300 s / 300 s | 128 | 0.507 | 0.489 | +1.8 | +0.9 | 0.81 | +0.41 (+1.12) | 24-3 25+2 26+1 | +0.1 | +0.5 | SOMETIMES |
| nq10_trd | 1 s | 300 s / 300 s | 119 | 0.507 | 0.494 | +1.3 | +0.8 | 0.81 | +0.18 (+0.47) | 23-0 24+4 25+3 26-0 | -4.1 | -0.6 | NEVER |
| px_ZN | 1 s | 1 s / 1 s | 10774 | 0.501 | 0.500 | +0.1 | +0.7 | 0.84 | +0.00 (+0.01) | 23+0 24+0 25+0 26+0 | +0.0 | +0.1 | SOMETIMES |
| px_ZB | 1 s | 5 s / 5 s | 1859 | 0.503 | 0.500 | +0.3 | +0.7 | 0.84 | +0.01 (+0.02) | 23-0 24+1 25+1 26-0 | +0.6 | -0.5 | NEVER |
| nq10_imb5 | 1 s | 15 s / 300 s | 456 | 0.510 | 0.505 | +0.5 | +0.7 | 0.85 | +0.27 (+0.72) | 23+1 24-0 25+1 26+1 | -0.6 | +1.1 | SOMETIMES |
| liq10_imb | 1 s | 1 min / 1 min | 361 | 0.512 | 0.507 | +0.6 | +0.6 | 0.85 | +0.06 (+0.15) | 23+0 24+1 25-0 26+0 | -1.7 | +0.1 | SOMETIMES |
| px_6E | 1 s | 1 s / 1 s | 1706 | 0.500 | 0.497 | +0.2 | +0.6 | 0.85 | -0.00 (-0.00) | 23+1 24+2 25+0 26+0 | +0.4 | -0.3 | NEVER |
| nq10_pull | 1 s | 15 s / 300 s | 391 | 0.512 | 0.508 | +0.4 | +0.5 | 0.85 | +0.42 (+1.14) | 23+1 24+1 25+1 26+1 | +1.8 | +1.6 | SOMETIMES |
| px_6C | 1 s | 1 s / 1 s | 1555 | 0.502 | 0.500 | +0.2 | +0.4 | 0.88 | +0.00 (+0.01) | 23+1 24+0 25+0 26-0 | +0.6 | -1.1 | NEVER |
| px_6B | 1 s | 1 s / 1 s | 1644 | 0.501 | 0.499 | +0.2 | +0.4 | 0.89 | -0.00 (-0.00) | 23+0 24+1 25+0 26+0 | -0.3 | +0.1 | SOMETIMES |
| px_NKD | 1 s | 1 s / 1 s | 985 | 0.503 | 0.501 | +0.2 | +0.4 | 0.90 | +0.00 (+0.00) | 23-0 24+1 25+2 26-1 | +0.3 | -0.4 | NEVER |
| uw_gam_QQQ | 1 min | 1 min / 1 min | 238 | 0.495 | 0.489 | +0.5 | +0.4 | 0.90 | +0.15 (+0.41) | 24-1 25+1 26+0 | +2.2 | +1.2 | SOMETIMES |
| nq10_ofi | 1 s | 300 s / 300 s | 64 | 0.504 | 0.500 | +0.4 | +0.2 | 0.93 | +0.72 (+1.94) | 23+2 24-0 25+4 26-1 | -7.7 | -1.6 | NEVER |
| nq10_big | 1 s | 15 s / 15 s | 413 | 0.499 | 0.498 | +0.1 | +0.1 | 0.97 | -0.03 (-0.09) | 23-1 24+2 25-0 26+0 | +1.1 | -0.0 | NEVER |
| nq10_add | 1 s | 1 s / 1 s | 1689 | 0.502 | 0.502 | -0.0 | -0.0 | 0.97 | +0.01 (+0.02) | 23+2 24+1 25+0 26-0 | +0.6 | +0.3 | NEVER |
| l3_wall30 | 1 s | 15 s / 15 s | 1725 | 0.500 | 0.501 | -0.0 | -0.1 | 0.97 | -0.01 (-0.02) | 23+0 24+0 25-0 26+0 | +0.8 | +0.0 | NEVER |
| uw_tide_SPY | 1 min | 1 min / 300 s | 77 | 0.513 | 0.516 | -0.3 | -0.1 | 0.97 | +0.20 (+0.53) | 24+5 25+0 26-0 | -5.3 | -0.3 | NEVER |
| px_RTY | 1 s | 15 s / 300 s | 295 | 0.497 | 0.499 | -0.3 | -0.2 | 0.98 | -0.21 (-0.56) | 23+0 24+2 25-1 26+0 | +1.0 | +1.6 | NEVER |
| l3_wall120 | 1 s | 1 s / 300 s | 383 | 0.503 | 0.506 | -0.3 | -0.4 | 0.99 | -0.08 (-0.21) | 23+1 24+1 25-1 26-0 | -1.9 | -0.7 | NEVER |

### NY PM

| feed | native | window / horizon | fires per month | hit | null | edge pp | z | q | follow bp (pts) | by year (pp) | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| px_ES | 1 s | 1 s / 1 s | 570 | 0.529 | 0.505 | +2.4 | +2.8 | 0.04 | +0.01 (+0.02) | 23+5 24+0 25+2 26+3 | +4.0 | +2.9 | STEADY LEADER |
| nq10_pull | 1 s | 1 min / 300 s | 274 | 0.521 | 0.494 | +2.6 | +2.5 | 0.08 | +0.22 (+0.58) | 23+1 24+2 25+3 26+3 | -1.0 | +1.5 | SOMETIMES |
| px_6J | 1 s | 300 s / 300 s | 91 | 0.522 | 0.495 | +2.7 | +1.5 | 0.58 | +0.16 (+0.43) | 23+5 24-3 25+2 26+2 | -4.7 | +0.3 | SOMETIMES |
| px_6E | 1 s | 1 s / 1 s | 1715 | 0.503 | 0.497 | +0.6 | +1.4 | 0.61 | +0.00 (+0.00) | 23+1 24+0 25+1 26+1 | -0.3 | +0.0 | SOMETIMES |
| px_6C | 1 s | 1 s / 1 s | 1356 | 0.503 | 0.498 | +0.6 | +1.2 | 0.69 | +0.01 (+0.02) | 23+1 24+0 25+1 26+1 | +0.4 | +0.5 | SOMETIMES |
| px_6B | 1 s | 1 s / 1 s | 1407 | 0.506 | 0.501 | +0.4 | +0.9 | 0.81 | +0.01 (+0.02) | 23+1 24+1 25+1 26+0 | -0.7 | +0.5 | SOMETIMES |
| nq10_big | 1 s | 300 s / 300 s | 108 | 0.515 | 0.500 | +1.4 | +0.9 | 0.81 | +0.02 (+0.05) | 23+2 24+1 25+1 26+2 | +0.2 | -0.1 | NEVER |
| l3_add | 1 s | 1 s / 1 s | 391 | 0.509 | 0.502 | +0.7 | +0.8 | 0.84 | +0.01 (+0.03) | 23+1 24+0 25-1 26+2 | -1.5 | +2.0 | SOMETIMES |
| px_ZN | 1 s | 1 min / 1 min | 602 | 0.508 | 0.504 | +0.4 | +0.6 | 0.85 | +0.05 (+0.15) | 23+0 24+1 25+2 26-1 | -3.1 | -1.6 | NEVER |
| px_CL | 1 s | 1 s / 300 s | 787 | 0.501 | 0.497 | +0.4 | +0.6 | 0.85 | +0.09 (+0.24) | 23+1 24+0 25+1 26-0 | -1.2 | -0.1 | NEVER |
| nq10_imb5 | 1 s | 300 s / 300 s | 226 | 0.502 | 0.496 | +0.7 | +0.6 | 0.85 | -0.01 (-0.03) | 23+2 24+1 25+1 26-0 | -1.7 | +0.0 | SOMETIMES |
| px_GC | 1 s | 1 min / 1 min | 438 | 0.499 | 0.494 | +0.5 | +0.6 | 0.85 | +0.05 (+0.13) | 23-1 24+1 25+1 26+1 | -0.7 | +0.8 | SOMETIMES |
| uw_tide_QQQ | 1 min | 1 min / 300 s | 206 | 0.505 | 0.496 | +0.9 | +0.6 | 0.85 | +0.17 (+0.47) | 24+0 25+1 26+1 | +6.2 | +2.9 | SOMETIMES |
| px_YM | 1 s | 1 min / 1 min | 207 | 0.500 | 0.497 | +0.3 | +0.3 | 0.92 | +0.17 (+0.46) | 23+4 24-1 25+1 26-0 | +1.3 | +0.6 | SOMETIMES |
| uw_gamdir_NDX | 1 min | 300 s / 300 s | 148 | 0.506 | 0.506 | +0.1 | +0.0 | 0.97 | -0.07 (-0.19) | 24-2 25+2 26-0 | -2.3 | +0.3 | SOMETIMES |
| px_NKD | 1 s | 1 min / 1 min | 122 | 0.501 | 0.502 | -0.1 | -0.0 | 0.97 | +0.09 (+0.24) | 23+1 24-0 25-0 26+1 | +0.2 | +2.1 | NEVER |
| l3_wall30 | 1 s | 5 s / 5 s | 5502 | 0.498 | 0.499 | -0.0 | -0.1 | 0.97 | -0.00 (-0.01) | 23+1 24-0 25-0 26-0 | -0.6 | -0.4 | NEVER |
| l3_pull | 1 s | 1 s / 1 s | 1208 | 0.501 | 0.502 | -0.1 | -0.1 | 0.97 | +0.00 (+0.01) | 23-0 24+1 25+0 26+0 | +0.5 | +0.0 | NEVER |
| l3_wall120 | 1 s | 5 s / 5 s | 12909 | 0.499 | 0.499 | -0.0 | -0.1 | 0.97 | -0.00 (-0.01) | 23+0 24+0 25-0 26+0 | -0.4 | -0.3 | NEVER |
| uw_tide_SPY | 1 min | 1 min / 1 min | 278 | 0.500 | 0.502 | -0.2 | -0.2 | 0.97 | +0.16 (+0.43) | 24+2 25-2 26+0 | +1.9 | +0.8 | NEVER |
| uw_gam_SPX | 1 min | 1 min / 300 s | 214 | 0.500 | 0.503 | -0.3 | -0.2 | 0.97 | +0.08 (+0.22) | 24+2 25+2 26-0 | -0.0 | -0.4 | NEVER |
| liq10_wall | 1 s | 15 s / 300 s | 528 | 0.494 | 0.496 | -0.2 | -0.2 | 0.97 | -0.07 (-0.18) | 23+1 24+1 25+1 26+0 | +0.5 | +0.3 | NEVER |
| uw_gam_QQQ | 1 min | 1 min / 1 min | 347 | 0.499 | 0.502 | -0.3 | -0.2 | 0.98 | -0.04 (-0.12) | 24-5 25+1 26+0 | -1.2 | +0.1 | NEVER |
| uw_np_SPY | 1 min | 1 min / 1 min | 278 | 0.501 | 0.505 | -0.4 | -0.3 | 0.99 | +0.15 (+0.39) | 24+1 25+0 26-0 | +2.3 | +0.6 | NEVER |
| uw_tide | 1 min | 300 s / 300 s | 116 | 0.499 | 0.507 | -0.9 | -0.4 | 0.99 | -0.13 (-0.35) | 24+2 25+0 26-0 | +2.0 | +1.1 | NEVER |

(top 25 per session by judge z; full table in agg1.json. Note: "follow" in pts = bp x 2.7.)

## 5. The five steadiest leaders per session (score = 2 x share of years positive + last-3M positive + last-6M positive + judge z/5; either variant, judge edge > 0)
**Asia**

| rank | feed | variant | window / horizon | edge pp | follow bp | by year | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|
| 1 | l3_pull | all | 1 s / 1 s | +0.7 | +0.00 | 23+3 24+2 25+1 26+1 | +0.7 | +0.5 | SOMETIMES |
| 2 | px_ES | nqflat | 1 s / 1 s | +3.2 | +0.02 | 23+8 24+6 25+6 26+2 | +0.9 | +1.2 | STEADY LEADER |
| 3 | px_RTY | nqflat | 1 s / 1 s | +2.4 | +0.02 | 23+7 24+4 25+3 26+2 | +1.4 | +1.4 | STEADY LEADER |
| 4 | l3_add | nqflat | 1 s / 1 s | +1.4 | +0.02 | 23+6 24+4 25+1 26+1 | +0.7 | +0.9 | STEADY LEADER |
| 5 | nq10_trd | nqflat | 1 s / 1 s | +1.2 | +0.01 | 23+4 24+3 25+1 26+1 | +0.3 | +0.6 | STEADY LEADER |

**London**

| rank | feed | variant | window / horizon | edge pp | follow bp | by year | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|
| 1 | px_ES | nqflat | 1 s / 1 s | +3.5 | +0.02 | 23+4 24+5 25+6 26+2 | +0.4 | +1.1 | STEADY LEADER |
| 2 | l3_pull | all | 1 s / 1 s | +0.7 | +0.00 | 23+2 24+1 25+1 26+0 | +0.3 | +0.1 | SOMETIMES |
| 3 | px_GC | nqflat | 1 s / 1 s | +0.6 | +0.01 | 23+0 24+0 25+0 26+1 | +0.5 | +0.6 | SOMETIMES |
| 4 | px_6B | all | 1 s / 1 s | +1.0 | +0.01 | 23+0 24+1 25+2 26+0 | +0.1 | +0.2 | SOMETIMES |
| 5 | m_cap | all | 1 min / 1 min | +6.9 | +0.22 | 24- 25- 26+7 | +3.0 | +2.9 | SOMETIMES |

**NY AM**

| rank | feed | variant | window / horizon | edge pp | follow bp | by year | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|
| 1 | px_ES | nqflat | 1 s / 1 s | +2.5 | +0.00 | 23+2 24+2 25+3 26+2 | +1.0 | +2.2 | STEADY LEADER |
| 2 | l3_add | nqflat | 1 s / 1 s | +1.2 | +0.01 | 23+3 24+2 25+1 26+0 | +1.1 | +0.3 | SOMETIMES |
| 3 | l3_pull | nqflat | 1 s / 1 s | +0.6 | +0.00 | 23+1 24+0 25+1 26+0 | +0.7 | +0.2 | SOMETIMES |
| 4 | px_ZN | all | 1 s / 1 s | +0.1 | +0.00 | 23+0 24+0 25+0 26+0 | +0.2 | +0.1 | SOMETIMES |
| 5 | uw_gam_NDX | nqflat | 300 s / 300 s | +3.0 | +0.21 | 24- 25+1 26+3 | +3.3 | +3.5 | SOMETIMES |

**NY PM**

| rank | feed | variant | window / horizon | edge pp | follow bp | by year | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|
| 1 | px_ES | nqflat | 1 s / 1 s | +2.4 | +0.01 | 23+5 24+0 25+2 26+3 | +4.0 | +2.9 | STEADY LEADER |
| 2 | px_6C | all | 1 s / 1 s | +0.8 | +0.01 | 23+0 24+1 25+1 26+1 | +0.4 | +0.8 | SOMETIMES |
| 3 | uw_tide_SPY | all | 300 s / 300 s | +2.0 | +0.27 | 24+3 25+1 26+2 | +6.9 | +3.1 | SOMETIMES |
| 4 | px_CL | all | 15 s / 15 s | +0.3 | -0.04 | 23+0 24+0 25+0 26+1 | +0.7 | +1.3 | SOMETIMES |
| 5 | m_NVDA | all | 300 s / 300 s | +2.7 | +0.94 | 24- 25+1 26+3 | +1.5 | +4.5 | SOMETIMES |

STEADY LEADERS (all sessions, both variants): l3_add Asia nqflat (1 s/1 s), l3_fill Asia nqflat (1 s/1 s), nq10_add Asia nqflat (1 s/1 s), nq10_trd Asia nqflat (1 s/1 s), px_ES Asia nqflat (1 s/1 s), px_ES London nqflat (1 s/1 s), px_ES NY AM nqflat (1 s/1 s), px_ES NY PM nqflat (1 s/1 s), px_NKD Asia all (5 s/5 s), px_NKD Asia nqflat (5 s/5 s), px_RTY Asia nqflat (1 s/1 s)

## 6. NQ TURNS: which feeds turned first (descriptive; hindsight-defined turn)
Run = NQ moved >= 3 sigma over 300 s; turn = the extreme found in the next 300 s that NQ then retraces by >= 40% of the run (about 241 turns per month). Lead = time of the feed's own extreme minus the NQ extreme, in seconds, window drift removed; negative = feed turned BEFORE NQ. "Early" = lead <= -5 s (<= -60 s for minute feeds). Null = random windows with the same direction mix (what chance and noise give).
**Asia**

| feed | turns (judge) | median lead s (null) | early share | null | diff pp | z | by year (pp) | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|---|
| nq10_pull | 1552 | -19 (+0) | 0.552 | 0.458 | +9.4 | +4.8 | 23-3 24+1 25+10 26+8 | +16 | +13 | STEADY LEADER |
| liq10_wall | 1537 | -44 (-22) | 0.627 | 0.547 | +8.0 | +4.1 | 23+8 24+10 25+7 26+7 | +5 | +9 | STEADY LEADER |
| nq10_imb5 | 1552 | -53 (-17) | 0.614 | 0.539 | +7.5 | +3.9 | 23+8 24+8 25+7 26+5 | +16 | +10 | STEADY LEADER |
| nq10_trd | 1552 | -2 (+0) | 0.454 | 0.402 | +5.2 | +2.7 | 23+1 24+4 25+5 26+7 | +1 | +5 | SOMETIMES |
| liq10_imb | 1537 | -51 (-31) | 0.613 | 0.567 | +4.6 | +2.4 | 23+8 24+9 25+6 26+2 | +0 | -0 | SOMETIMES |
| px_ES | 1439 | +0 (+0) | 0.334 | 0.298 | +3.6 | +2.0 | 23+2 24+3 25+3 26+3 | +2 | +4 | SOMETIMES |
| m_GOOGL | 203 | +0 (+60) | 0.429 | 0.325 | +10.4 | +1.9 | 24- 25+3 26+8 | - | +12 | SOMETIMES |
| m_MSFT | 206 | -5 (+41) | 0.442 | 0.342 | +10.0 | +1.8 | 24- 25+3 26+10 | +16 | +13 | SOMETIMES |
| l3_wall120 | 1519 | +1 (+13) | 0.482 | 0.450 | +3.2 | +1.6 | 23-4 24-0 25+3 26+3 | +1 | +1 | SOMETIMES |
| nq10_big | 337 | -14 (-2) | 0.549 | 0.477 | +7.2 | +1.5 | 23+13 24+8 25+5 26+13 | - | +11 | NEVER |

**London**

| feed | turns (judge) | median lead s (null) | early share | null | diff pp | z | by year (pp) | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|---|
| liq10_wall | 1088 | -53 (-22) | 0.643 | 0.526 | +11.7 | +4.9 | 23+12 24+11 25+15 26+10 | +7 | +10 | STEADY LEADER |
| nq10_trd | 1088 | -8 (+0) | 0.528 | 0.423 | +10.5 | +4.4 | 23+4 24+11 25+14 26+9 | +3 | +8 | STEADY LEADER |
| liq10_imb | 1088 | -53 (-23) | 0.624 | 0.541 | +8.3 | +3.5 | 23+13 24+11 25+13 26+6 | +8 | +3 | STEADY LEADER |
| nq10_ofi | 1088 | -1 (+0) | 0.443 | 0.370 | +7.3 | +3.1 | 23+7 24+6 25+5 26+9 | +19 | +6 | STEADY LEADER |
| nq10_big | 301 | -30 (+0) | 0.631 | 0.476 | +15.5 | +2.8 | 23+24 24+20 25+26 26+6 | - | +2 | SOMETIMES |
| l3_fill | 1079 | -1 (+0) | 0.449 | 0.389 | +6.1 | +2.5 | 23+10 24+8 25+7 26+5 | +8 | +7 | SOMETIMES |
| nq10_imb5 | 1089 | -57 (-34) | 0.626 | 0.568 | +5.8 | +2.5 | 23+10 24+6 25+7 26+2 | -1 | -4 | SOMETIMES |
| nq10_pull | 1089 | -4 (+0) | 0.499 | 0.460 | +3.8 | +1.6 | 23-4 24+1 25+9 26+3 | +6 | +3 | SOMETIMES |
| px_CL | 1086 | -16 (+12) | 0.519 | 0.481 | +3.9 | +1.6 | 23+4 24+1 25-0 26+6 | +5 | +2 | SOMETIMES |
| m_GC | 1081 | -2 (+18) | 0.370 | 0.335 | +3.5 | +1.5 | 23-1 24-9 25+5 26+1 | +16 | +2 | SOMETIMES |

**NY AM**

| feed | turns (judge) | median lead s (null) | early share | null | diff pp | z | by year (pp) | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|---|
| nq10_trd | 822 | -4 (+0) | 0.499 | 0.411 | +8.7 | +3.0 | 23+2 24+2 25+12 26+3 | +11 | +7 | SOMETIMES |
| l3_wall120 | 808 | +4 (+20) | 0.470 | 0.396 | +7.4 | +2.6 | 23+5 24+0 25-2 26+12 | +9 | +7 | SOMETIMES |
| liq10_wall | 815 | -66 (-43) | 0.637 | 0.567 | +7.0 | +2.4 | 23+2 24+6 25+9 26+6 | +16 | +11 | SOMETIMES |
| l3_fill | 808 | +0 (+0) | 0.411 | 0.350 | +6.1 | +2.1 | 23-1 24+1 25+10 26-0 | +19 | +0 | SOMETIMES |
| l3_wall30 | 808 | -14 (+2) | 0.535 | 0.475 | +6.0 | +2.0 | 23+6 24+5 25+1 26+6 | +8 | +7 | SOMETIMES |
| nq10_pull | 822 | -18 (-6) | 0.547 | 0.502 | +4.5 | +1.6 | 23-2 24-5 25+7 26-1 | +1 | +2 | SOMETIMES |
| nq10_big | 663 | -11 (-4) | 0.540 | 0.497 | +4.3 | +1.2 | 23+7 24+5 25+6 26-2 | -13 | -5 | NEVER |
| uw_tide_SPY | 320 | -56 (-34) | 0.494 | 0.440 | +5.4 | +1.1 | 24+19 25+1 26+5 | +0 | +5 | NEVER |
| nq10_ofi | 822 | +0 (+0) | 0.404 | 0.372 | +3.2 | +1.1 | 23-0 24+0 25+5 26-2 | +3 | +3 | NEVER |
| px_YM | 815 | +9 (+29) | 0.426 | 0.395 | +3.1 | +1.1 | 23-0 24+4 25+1 26+4 | +6 | +8 | NEVER |

**NY PM**

| feed | turns (judge) | median lead s (null) | early share | null | diff pp | z | by year (pp) | L3M | L6M | label |
|---|---|---|---|---|---|---|---|---|---|---|
| nq10_trd | 638 | -3 (+0) | 0.486 | 0.412 | +7.4 | +2.5 | 23+9 24+6 25+4 26+7 | +7 | +13 | SOMETIMES |
| liq10_wall | 622 | -48 (-18) | 0.595 | 0.525 | +7.0 | +2.3 | 23-2 24+10 25+11 26+4 | +14 | +8 | SOMETIMES |
| l3_fill | 615 | -1 (+0) | 0.415 | 0.356 | +5.8 | +2.0 | 23+7 24+6 25+12 26+3 | +9 | +6 | SOMETIMES |
| nq10_ofi | 638 | -1 (+0) | 0.417 | 0.368 | +4.9 | +1.7 | 23+10 24+8 25+8 26+5 | +6 | +8 | SOMETIMES |
| uw_tide_SPY | 317 | -64 (-44) | 0.511 | 0.448 | +6.3 | +1.5 | 24-6 25+4 26+6 | +3 | +6 | NEVER |
| uw_tide_QQQ | 317 | -57 (-29) | 0.498 | 0.442 | +5.7 | +1.4 | 24+9 25+4 26+4 | -3 | -0 | NEVER |
| nq10_big | 504 | -6 (+10) | 0.508 | 0.455 | +5.3 | +1.4 | 23+11 24+1 25+7 26+4 | - | +13 | NEVER |
| px_CL | 641 | -16 (+4) | 0.515 | 0.476 | +3.8 | +1.3 | 23-8 24+2 25-2 26+8 | +4 | +3 | NEVER |
| l3_wall30 | 615 | +6 (+15) | 0.468 | 0.441 | +2.8 | +0.9 | 23+5 24+4 25+6 26+2 | +16 | +11 | NEVER |
| m_6J | 620 | -43 (-36) | 0.485 | 0.462 | +2.4 | +0.8 | 23-2 24-1 25-1 26+6 | +2 | +6 | NEVER |

## 7. What could NOT be measured at fine resolution (data shopping list for Josh; no quote, nothing bought)
- Held only as 1-minute bars (no second-level lead can be tested): the seven megacaps (NVDA MSFT AAPL AMZN META GOOGL TSLA), QQQ SPY IWM DIA, NYSE TICK, UW spot gamma / tide / net premium (one-minute updates at best). Their history starts 2024-10 (megacaps, ETFs, UW), NYSE TICK 2023-04. Price feeds YM, NKD, ZB, 6E, 6J, 6B, 6C, CL, GC, ZN are second-level prints with staleness (age_ columns).
- Not on the box at all: market internals other than NYSE TICK (NYSE/Nasdaq A/D, TRIN, VOLD, Nasdaq TICK), VIX / VXN / VIX futures term, 6A, HG (copper), BTC/MBT beyond a few spot files, megacap tick/L1 data, options trade flow by strike at second resolution before 18 Nov, SPX/NQ options order flow ticks. These are the places where a faster feed could plausibly lead NQ and where nothing can be tested today.

## 8. Caveats
- Statistics at 1-5 s are about information speed, not trading edge: follow moves of 0.01-0.1 bp are far below a tick. A lead has to survive fees and fill delay of the engine (LAT 0.5-1.0 s) to matter; this page does not claim it does.
- Index prices, bond/FX/crude mids and book features are second-resolution from the L2/L3 tapes with their own staleness (age_ columns); prices older than 60 s are dropped. Feeds with 1-minute updates (UW, TICK, stocks) are tested only at 1-60 min horizons and say nothing about seconds.
- Same-moment correlation is not causation: ES co-moves because it is the same equity index; it is the best NOW-read of NQ but NQ often leads ES in ticks (see 1 s rows).
- Overlap and multiple testing: refractory thinning removes overlapping outcomes inside a feed, not across feeds (the feeds are strongly correlated); BH uses the judged rows only, so read the q column with that in mind.
