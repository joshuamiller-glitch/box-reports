# RESEARCH_LOG (idea | mechanism | prior | status)
- C1-F1 5-min family cross-instrument | structure effect? | prior 15% | cycle 1
- C1-F2 allocation rule pair vs 5-min ensemble | trailing tilt | 8% | cycle 1
- C1-F3 term-structure carry + XS momentum (daily, 26 mkts) | risk premium | 10% as sleeve | cycle 1
- C1-F4 index relative-value spreads | market-neutral, ~0 corr | 8% | cycle 1
- C1-F5 cross-asset conditioning of pair entries | risk-on/off context | 6% | cycle 1
- C1-F6 VX/vol-regime size switch | regime-dependent edge | 5% | cycle 1
- C1-F7 MBO-recipe ML ES/RTY | replication of NQ NO | 3% | cycle 1
- conditional day lock; GC hedge | ruled out by D3 S2 / V5 P4 | - | not run
- C2-G1 exit management of the pair (breakeven/trail/scale/time stops) | D3 lever ranking | 10% | cycle 2
- C2-G2 meta-labeling of pair entries (GBM walk-forward) | outcome predictable from flip features | 8% | cycle 2
- C2-G3 event-day (FOMC/NFP) breakout sleeve on NQ | pair blind at those times | 6% | cycle 2
- C2-G4 calendar/seasonal sleeves, daily non-index universe | structural seasonal | 5% | cycle 2
- skipped: short-vol options sleeve (positively tied to bad weeks), long-vol hedge (pair's worst weeks are chop not crashes)
- C1-F4 index spreads: ruled out (regime flip; no lead).
- C3-H1 intraday momentum (first-30-min -> last-30-min) | hedger rebalancing | 10% | cycle 3
- C3-H2 live pair on 2013-2022 NQ 1-min (diagnostic holdout) | does the edge pre-date 2023? | n/a | cycle 3
- C3-H3 5-min NQ ensemble on 2013-2022 | does neg. corr/uplift persist out of sample over 10 yrs? | 15% | cycle 3
- C4-K1 let-winners-run (target extension after +40) | runners carry the edge | 8% | cycle 4
- C4-K1 let winners run: ruled out (idea parked: extension + lock retune, needs long-history holdout).
- C1-F6 vol-regime size switch: ruled out.
- C3-H2/H3: pair has no edge 2013-2022 (KEY FINDING); 5-min family ruled out.
- C5-M1 long-history-selected intraday families NQ/ES | regime-robust selection | 8% | cycle 5
- C5-M2 RTY ML cell OOS on 2013-2022 | out-of-sample check of weak lead | 5% | cycle 5
- C1-F5 cross-asset conditioning: ruled out.
- C6-N1 ex-ante regime switch for the pair (fit 2013-2022, read clean/H1/H2) | edge is regime dependent | 10% | cycle 6
- C6-N2 RTY ML OOS (=C5-M2) and C3-H1 RTY rerun | completeness | 5% | cycle 6
- C6-N1 regime switch for pair: ruled out (no observable explains the 2024-26 edge).
- C7-P1 long-history-selected intraday on ZN/ZB/6E/6J/GC/CL | uncorrelated by construction + regime-robust selection | 8% | cycle 7
- C8-Q1 era diagnostic (variance ratios, ACF, trend-day share by year vs pair yearly Sharpe) | what does the edge depend on | n/a
- C8-Q2 time-of-day drift sleeves NQ/ES, long-history selection | persistent intraday seasonality | 5%
- C9-R1 calendar avoid-filters on the pair (release windows, roll week, holidays, month-end, Friday pm), developed on 2013-22 pair trades | abnormal-liquidity trades lose | 8% | cycle 9
- C10-S1 higher-timeframe (30/60/240-min) trend/MR on 7 instruments, long-history selection | cost drag falls with horizon | 8% | cycle 10
## Cycle 11 batch (B-series, 2026-10-16) and pair-side ideas from the H1 autopsy (D3 S2: lock cost is concentrated on trend/high-range days, -$422k in H1, 5 days = 68%; rest_plain after the lock minute was +$55-94k on the worst days; week floor cost clean/H2 recoveries; S5 attribution: hour/dow/side/book buckets not stable across spans, so no time-of-day tilt)
- B12 multi-hour holds of ST/HM flips, no bracket | different exit paradigm, separate book | 5%
- B9 cross-instrument (ES/RTY) trend agreement as pair SIZE 50%/150% | confirmation raises hit rate | 5%
- B8 trailing-P&L-conditioned 5-min ensemble hedge | hedge only when pair is cold | 4%
- C11-DIP ES/YM RSI2 dip-buy single clean-only cell | amended survivor, small sample | 8%
- C11-HM HM health trigger as HM size switch | D3 S3 early warning | 4%
- B14 meta-labeling of pair entries (GBM walk-forward) | outcome predictable from entry features | 6%
- Q-1 (ID B15-LOCKRE) post-lock reduced-size continuation: after the combined day lock fires, run both books at 25%/50% size for the rest of the day instead of flat | H1 autopsy: lock cost = trending rest-of-day; keeps most of the lock's protection | 8%
- Q-2 (B16-WKGRAD) graded week de-risking: size 50% for the rest of the week once week P&L <= -4R (floor at -8R kept) | week floor cuts recoveries; graded step keeps recovery optionality | 6%
- Q-3 (B17-VOLTGT) trailing-realised-vol sizing of the pair: size = clip(target / trailing 4wk daily P&L stdev, 0.6, 1.4), walk-forward, constant mean risk | smooths weekly income directly (the goal), no signal change | 10%
- Q-4 (B18-PRIORDAY) size after prior-day outcome: 75% after a locked +cap day / 125% after a plain loss day, or reverse (sign set on clean) | daily P&L autocorrelation from the lock structure | 5%
- Q-5 (B19-BOOKTILT) dynamic ST/HM weight by trailing-13-week book Sharpe/P&L (tilt 12/4 .. 4/12, walk-forward) | D1 F3 HM-heavy split lead, books' edge alternate (S5: book rho -1 across spans) | 5%
## Ideation batch I1-I10 + B15 (worker I, 2026-10-16). Sources: D3 S5 (hour/dow/side/book not stable across spans; trend-share stable but ex-post), D3 S6 lever table (win rate and avg loss/win move the number most; 1 tick = +0.30), H1 autopsy (lock cost = trending rest-of-day), P1/P1B/P2 (pair and 5-min family have ~zero gross edge before 2023: sleeves must carry their own long-history evidence), CANDIDATES closest misses (ES/YM dip, MBO seven, BTC wide, prior-day break). Selection principle for sleeves: develop on 2013-2022 (strictly before the pair window), read clean/H1/H2 once for ONE cell.
- B15-LOCKRE post-lock reduced-size continuation (Q-1) | after the combined day lock fires, run books at 25%/50% instead of flat | H1 autopsy: lock cost is trending rest-of-day | 8%
- I1 Sunday weekend-gap fade/follow basket (12 futures, 2013-22 selection) | thin Sunday-open liquidity overshoots, closes in hours | structurally uncorrelated with the pair (trades Sunday evening, 1 position/instrument/week) | 5%
- I2 RTH opening-gap fade/follow (ES/NQ/YM/RTY, 2013-22 selection) | overnight gap vs prior close; fill/continuation conditional on size/ADR | only used as pair filters in B10, never as a sleeve | 5%
- I3 pre-FOMC drift (long into 14:00) and post-FOMC/NFP 5-min-move drift (ES+NQ) | published pre-announcement drift; hedger/dealer inventory post release | event days where pair is blind (G3 tested breakout only) | 3% (small-sample by construction)
- I4 volume-surge continuation/reversal, 5-min bars on ES/NQ/YM/RTY | abnormal volume marks information vs liquidity shocks | volume-conditioned, never tested as stand-alone sleeve | 4%
- I5 ES-NQ 1-min lead-lag catch-up | relative-return dislocation closes within minutes | structural microstructure; likely killed by 1-tick costs | 2%
- I6 walk-forward hour/dow/hour x book SIZE tilt of the pair (cut the worst-trailing buckets) | D3 S5 hour buckets: stable? rho -0.10 -> expect no | explicit user example; walk-forward rather than clean-fitted | 2%
- I7 walk-forward side / book x side size tilt (cut buckets with negative trailing mean) | S5: side share flips by span (long carried clean, short carried H2) | explicit user example | 3%
- I8 post-exit re-entry book: after a pair stop-out reverse/re-enter, after a target continue/fade (30/60 bracket or time exit) | lever table: win rate / avg loss; momentum or reversal after a 60-pt move | uses the pair's own stop/target events as the trigger; not in D2 E5/E6 | 4%
- I9 IBS and consecutive-down-days reversal on ES/NQ/YM/RTY daily (2013-22 selection) | short-term reversal different formulation from RSI(2) (C11-DIP) | long-history daily stream | 4%
- I10 prior-week-conditioned pair size (up after loss week / down after win week) | pair weekly lag-1 autocorr -0.15 (B8) | smooths weekly income directly | 3%
- skipped as covered: ZN-range size switch (C1-F5/F6, C6-N1 state variables), dip-buy on YM/RTY/NQ with RSI2 (C11-DIP covers 64 cells), calendar/seasonal (C2-G4, C9-R1), overnight specialists (B10), 5-min trend (V5, C3-H3, P1B), booktilt (Q-5 logged by lead), vol-target sizing (D2 E1).
## Follow-on batch X1-X5 (B2356 worker, 2026-10-16). Sources: closest misses of this worker's B2/B5/B6 (B2-D inside-day / range-percentile 1-day breakouts have a real standalone edge, own-null rank 1.00 in 2013-22 AND the pair window, but Sharpe ~0.6-1.0 and cost-sensitive in low-ATR products; GC Jan-Feb long +0.16 uplift with 3 windows; B6 continuation after >=1.5 ATR days 2013-22 0.44 / pair window 0.30; fades only survive in 2013-22) and D3 S5 attribution (pair P&L = trend days 232% of clean / chop days -97%; trend-share stable across spans; hour/dow/side unstable -> only regime-type, not calendar-type, sleeves). Overlap check vs RESEARCH_LOG/LEDGER: dip-buy RSI2 = C11-DIP (64 cells), IBS reversal = I9, calendar = C2-G4/C9-R1: skipped.
- X1 (B2-X1) cost-screened compression breakout: union of NR7/inside-day/range-pctile<=10% setups, hold 1-2 d, ATR stop 2-3, markets screened EX ANTE by contract-spec cost (2 ticks + commission <= 3% of median 2013-22 ATR20) | B2-D closest miss: the edge is real but diluted by markets where 1 tick is 5-10% of an ATR | 8%
- X2 (B6-X2) range-regime fade: fade 1/3-day |z|>=1.5/2.0 moves only when the instrument's 20-day efficiency ratio <= 0.25/0.35 (chop), hold 1/3, ALL26 or equity indices | S5: the pair loses on chop and earns on trend; a fade that earns only in chop is a hedge candidate; B6 RV survived 2013-22 only | 6%
- X3 (B6-X3) trend-aligned continuation: after a >=1.5/2.0 ATR day in the direction of sign(c-EMA100) (prior-day value), hold 2/3/5 d | B6 CT closest miss (0.44 in 2013-22, 0.30 pair window) + S5 trend-share stable | 6%
- X4 (B5-X4) gold Jan-Feb long replicated on a second instrument (SI, PL; GC_A reference) | GC_A uplift +0.16 / null rank 0.98 in 2013-22: pre-registered second-instrument replication, rule frozen | 4%
- X5 (B6-X5) daily-candle follow-through: body ratio |c-o|/(h-l) >= 0.6/0.8 and range >= 1.0/1.5 ATR20, follow the candle for 1 or 3 days, ALL26 or COM+RATES | S5 trend-day dominance; candle-shape variant of B6 CT (not a re-skin: shape not size) | 5%
## Batch Y1-Y10 (B2356 worker, 2026-10-16, daily + 30-min first). Sources: X1 closest-miss (breakout effect real, pair uplift thin: refine depth of compression and trend alignment), B6/X3/X5 misses (large-move continuation decays), S5 (pair earns on trend days: short-horizon breakout/trend sleeves), cost lessons (30-min fades die to 1-tick costs). Overlap check vs RESEARCH_LOG/LEDGER: IBS/dip-buy (I9, C11-DIP), calendars, 30/60/240 Donchian (C10-S1) skipped.
- Y1 close-streak fade/follow: N=3,4 consecutive same-direction closes, hold 1/3, ALL26 or cost-screened 16 | short-term exhaustion vs momentum in futures | 4%
- Y2 vol-contraction momentum: ATR5/ATR20 <= 0.6/0.8, trade the 20/60-day trend direction, hold 3/5 | quiet trends persist (vol clustering + trend) | 5%
- Y3 52-week-extreme proximity: within 1/2 ATR of the 252-day high/low -> follow, hold 3/5/10 | George-Hwang anchoring, documented in equities, untested in futures here | 5%
- Y4 short Donchian (10/20/40) close breakout, hold 3/5 | breakout continuation at the 1-2 week horizon; between X1 (1 day) and C10-S1 (intraday) | 5%
- Y5 volume-spike follow/fade: volume >= 1.5/2.0 x 20-day mean, direction of the candle, hold 1/3 | information vs liquidity shocks (daily volume never used as a signal) | 5%
- Y6 depth of compression: 2 consecutive inside days / NR4 / NR7 inside day breakouts, 1-day hold, SCR or ALL26 | X1 refinement: deeper compression -> larger expansion | 8%
- Y7 X1 trend-filtered: union-compression breakouts only WITH or only AGAINST the EMA20 trend | X1 refinement: continuation vs reversal breakouts | 6%
- Y8 30-min overreaction (bar z >= 2.5/3.5 ATR14-bars) fade or follow, hold 1/2/4 bars, NQ ES RTY GC CL ZN | microstructure overshoot; likely cost-killed (C8-Q2) | 3%
- Y9 cross-sectional 26-market rank reversal/momentum (long/short 4 by n-day z, n 1/5, hold 1/3/5) | market-neutral structure, different from C1-F3 (carry+12m momentum) | 4%
- Y10 30-min range-expansion bar (range >= 2/3 ATR14-bars, close in extreme 20%) follow/fade, hold 2/4/8 bars | intraday vol-expansion continuation | 3%
## Batch Z1-Z10 (B2356 worker, 2026-10-16). X1/Y6 count as ONE finding. Sources: coordinator request (path-resolved check of X1), X1/Y6 mechanism (compression -> expansion) and the failure pattern of everything else (continuation/fade signals decay after 2022; 30-min fades are cost-dead). Mechanisms chosen to be different from compression where possible.
- Z1 path-resolved 30-min X1: label-day (ET session) setups union/NR4, entry resolved on the 30-min path (true first touch), stop 2/3 ATR, exit at the day's last bar close, NQ ES RTY GC CL (+ZN) | validates or kills the daily both-touch / UTC-day fill assumptions of X1 | prior n/a (robustness; same finding)
- Z2 weekly compression -> daily close breakout of the prior week's range within the next week, hold 3/5 | weekly-scale vol compression | 5%
- Z3 gap-and-go: open outside prior range and candle confirms (follow) or fades, hold 1/3 | gap continuation vs fill | 4%
- Z4 failed breakout (turtle soup): new 10/20-day high intraday that closes back below it -> short (and mirror), hold 1/3/5 | stop-run liquidity grab reversal | 5%
- Z5 outside-day follow/fade by close location (>=0.7 / <=0.3), hold 1/3 | engulfing-bar information | 4%
- Z6 expansion-then-compression: inside day after a wide-range day (>=1.2/1.6 ATR), stop-entry breakout, 1 day | tighter X1 setup (same family) | 6%
- Z7 compression with volume dry-up (volume < 0.7/0.85 x 20d mean) breakout, 1 day | liquidity coil (same family) | 6%
- Z8 daily spreads (ZN/ZB, ZF/ZN, CL/RB, CL/HO, GC/SI, ZC/ZW, ZS/ZC, 6E/6B) z-score fade/follow at |z|>=1.5/2.5, hold 3/5, legs equal ATR risk | relative-value mean reversion/trend in related futures | 4%
- Z9 30-min prior-day high/low break (all days / narrow prior day / wide prior day), ATR stop 1/2, exit at day close, NQ ES RTY GC CL ZN | D2 NQ prior-day-break lead (selected after the fact among 276) generalised to 6 markets with a frozen grid | 6%
- Z10 vol-surge trend: ATR5/ATR20 >= 1.3/1.6 with the 5/20-day trend direction, hold 3/5 | expansion regimes trend (opposite of Y2) | 4%
- Rule (10-16): stop-entry families must be path-resolved (1-min or 30-min), never daily bars.
## Batch W1-W8 (B2356 worker, 2026-10-16). Program rule: stop-entry families only on path-resolved bars. 8 families (not 10: no further non-duplicate mechanism with data on the box passed the overlap check against LEDGER/RESEARCH_LOG). Sources: Z3 gap-fade weak lead (hedge-type, next-open), cross-asset/hedge logic for the equity-long pair, session structure of the 1-min data.
- W1 opening-range breakout, path-resolved 30-min, GC CL ZN NQ ES RTY with frozen per-market OR bars | T3 S3 NQ ORB had H2 negative; non-index + frozen grid | 4%
- W2 session-block momentum/reversal (Asia 18-03, Europe 03-08, US-AM 08-12, US-PM 12-16:30 ET; block return -> next block) | documented intraday momentum across sessions (Gao et al.; hedger rebalancing), here across 6 markets | 4%
- W3 flight-to-quality: after an ES day of z <= -thr (or >= +thr) go long (short) ZN / ZB / GC / 6J next open, hold 1/3 | negative equity correlation sleeve = natural hedge of an equity-long pair | 5%
- W4 weekday x asset-class sleeves with direction signed on 2013-22 (>= 7/10 years), hold 1 day | weekday effects in futures (Monday/Friday); selection on 2013-22 only | 3%
- W5 time-of-day displacement vs prior close: at 09:30/11:00/14:00 ET if (price - prior label-day close)/ATR >= 0.75/1.25 fade or follow to the day's last bar | prior-close magnet vs trend day | 4%
- W6 gap-size-conditioned gap fade (Z3 refinement): gap >= 0.25/0.5/1.0 ATR with confirming candle, fade next open, hold 1/3, SCR or ALL26 | Z3 closest-miss (hedge-type, null rank 0.96) | 8%
- W8 bond-momentum -> equity: sign of ZN L-day return (L 10/20) -> ES NQ RTY next open hold 5, direction both | rates-to-equity lead-lag (cross-asset momentum, Pitkin/Lyall-style) | 4%
## Batch V1-V10 (B2356 worker, 2026-10-16; coordinator asked for >= 10 families, structural ideas allowed). Skipped as duplicates: pair risk switches from ZN range / daily vol (C1-F5/F6, C6-N1 state variables, all NO), cross-sectional carry on micros (= C1-F3 carry on the same 26 markets; micros only change execution). Gap-fade family (Z3/W6) is the only weak lead: V3, V4, V10 refine it with pre-registered regimes.
- V1 30-min lead-lag among NQ/ES/RTY (follower catches up when leader moved > thr ATR14-bars more than follower) | cross-instrument information flow at 30 min (1-min level is cost-dead: I5) | 2%
- V2 event-day drift: FOMC+NFP days (dates: FOMC 2013-22 from memory, NFP by rule, 2023+ verified), long/short ES NQ ZN GC 6E, event day or day-before+event | pre-FOMC/announcement drift (Lucca-Moench) and macro-event risk premia | 3% (small sample: ~20 events/yr)
- V3 gap-fade conditioned on own volatility regime (ATR20 percentile of 252d: low <= 0.33/0.5, high >= 0.5/0.67) | gap fades revert when liquidity is ample (low vol) vs trend when vol is high; fixes H1? | 6%
- V4 gap-fade conditioned on trend (fade with / against the EMA50 trend) | pullback vs reversal gaps | 6%
- V5 equity-index relative strength (ES NQ RTY YM): long strongest / short weakest by n-day z (n 5/20/60), momentum or reversal, hold 5/10 | style/size rotation, market neutral | 4%
- V6 FX cross-sectional (6E 6J 6B 6A 6C): long 2 / short 2 by n-day z (20/60/120), momentum or reversal, hold 5/10 | FX momentum/carry-proxy | 4%
- V7 commodity cross-section (13 commodities): long 3 / short 3 by n-day z (20/60/120), momentum or reversal, hold 5/10 | commodity momentum at short horizons (Miffre-Rallis) | 4%
- V8 post-event continuation/fade: event-day candle z (FOMC+NFP) followed/faded next open for ES NQ ZN GC 6E, hold 1/3 | event under/over-reaction | 3%
- V9 low-vol-regime mean reversion: fade |close-SMA20|/std20 >= 1.5/2.0 only when ATR20 percentile <= 0.33/0.5, hold 3/5 | MR works in quiet regimes (regime-switch: trend vs MR) | 4%
- V10 gap-fade conditioned on the ZN 5-day range regime (macro-uncertainty proxy, percentile of 252d: low <= 0.33/0.5, high >= 0.5/0.67) | cross-asset state to tame H1 failure of the gap fade | 5%
## Batch T1-T6 (B2356 worker, 2026-10-16; from the U3 autopsy: the gap-fade lead is a weekend-gap fade; worker-I's I1 (1-min, entry at 18:01 before confirmation, hold <= 12 h) found NO, so the confirmed-entry / long-hold / breadth-conditioned versions are NOT duplicates). 6 families; the remaining RESEARCH_LOG mechanisms are already run (I1-I10, B-series) or fail the overlap check.
- T1 session-aligned weekend gap (Monday label day vs Friday close), confirm with the first N 30-min bars, then fade or follow to Monday's last bar, 6 markets | thin Sunday liquidity overshoot that confirms then reverts vs persists | 8%
- T2 weekend-gap fade only when few markets gapped together (breadth <= 2/3/4 of the 16 screened) | autopsy: H1 loss came from a common-shock weekend (breadth 9); idiosyncratic gaps revert, common shocks persist | 6%
- T3 weekend-gap FOLLOW when many markets gapped together (breadth >= 4/6/8) | common-shock continuation (mirror of T2) | 5%
- T4 weekend carry: Friday day-return z beyond +-0/0.5/1 ATR followed/faded over the weekend (Friday 16:30 open -> Sunday 18:30 open), 6 markets | weekend risk premium / positioning | 4%
- T5 pre-holiday drift (US exchange holidays inferred from missing weekdays) ES NQ RTY YM, pre-holiday day or pre+post, long | documented pre-holiday effect | 3% (small sample)
- T6 weekend-gap fade by asset class (EQ, MET, EN, RATES, FX, AG) | autopsy: metals/energy carried the H1 loss; class selection on 2013-22 | 4%
## Batch S1-S10 (B2356 worker, 2026-10-16; coordinator: open different areas, no more weekend-fade variants). 10 families; 30-min bars rebuilt from 1-min for 16 outrights (NQ ES RTY YM; ZN ZB; GC SI HG; CL NG RB HO; 6E 6J 6B); HO/RB/NG back-adjusted series go negative (point P&L only, no % returns).
- S1 post-open drift per asset class (path-resolved 30-min): first-bar move at the class open (EQ 09:30, RATES/MET/FX 08:00, EN 09:00 ET) followed or faded for 2h or to the day end | open-auction information vs overshoot | 4%
- S2 Asian-session range -> London-session breakout (path-resolved): range 18:00-03:00 ET, first touch 03:00-09:00 ET, exit 08:00/12:00/day end | session handover breakout (FX, metals, oil, indices) | 5%
- S3 realised-skew reversal (daily): 20/60-day skew of daily changes <= -thr long, >= +thr short, hold 3/5 | lottery/skew preference premium (Amaya et al.) | 4%
- S4 carry momentum (daily): 10/20/40-day change of the v.0/v.1 annualised carry, long top-4 / short bottom-4, hold 5/10 | roll-yield dynamics (term-structure signal changes before price) | 4%
- S5 price-volume divergence (daily): new 20/60-day high on volume below 0.8/1.0 x its 20-day mean -> short (low -> long), hold 3/5 | weak-volume breakouts fail | 4%
- S6 weekend flight-to-quality leg (30-min): ES Friday z beyond +-0.5/1.0 ATR -> ZN/ZB/GC/6J opposite over the weekend | hedge leg for the equity-long pair | 4%
- S7 month-end/quarter-end rebalancing (30-min): last label day of the month, enter 14:00/15:00 ET, fade or follow the month-to-date move (>= 0.5/1.0 ATR*sqrt(21)) in NQ ES RTY to the 16:30 bar | pension/rebalancing flows | 4%
- S8 options-expiry weeks (daily): long ES NQ RTY YM in the opex week / opex Friday / Monday after | dealer gamma pinning, documented opex-week drift | 3%
- S9 roll-week drift (daily): long/short ES NQ RTY YM ZN in the 5 days before the front-contract roll | roll-spread rebalancing | 3%
- S10 Monday->Tuesday reversal/continuation by asset class (daily) | weekday-conditional serial correlation | 3%
- B1 ST/HM/WT 5-30m ATR-trail on ES/RTY/GC/CL/ZN/BTC/ETH | NQ signals on other contracts, ADR-scaled equal R | 3% | cycle 12 (done: BTC WT lead, plateau 0.67; rest NO)
- B4 VWAP/SD-band fade | session-VWAP pull | 3% | cycle 12
- B7 time-exit-only books | signal timing without stop mechanics | 2% | cycle 12
- B10 overnight Asia/London specialists | home-session liquidity pockets | 3% | cycle 12
- B11 ORB / prior-day-level breakouts | level-breakout flow | 3% | cycle 12
- FU1 B1 grid on 10 further outrights (YM, 6E, 6J, 6B, 6A, 6C, ZB, SI, HG, NG) | closest miss: GC/CL/RTY 30m cells near zero; test breadth where structure differs (FX, rates, metals, nat gas) | 3% | cycle 12 follow-up
- FU2 B4/B7/B10/B11 on BTC and ETH | closest miss: the only lead (BTC WT trail) is in a market with large cost-to-range ratio at intraday scale; test whether other rule books also earn there | 5% | cycle 12 follow-up
- FU3 B10 overnight books on FX and rate futures (6E, 6J, 6B, 6A, 6C, ZB, YM) | London/Asia are the home sessions of FX | 4% | cycle 12 follow-up
- FU4 B1 signals at 45/60/90/120-min bars (ES, RTY, GC, CL, ZN, YM, BTC, ETH) | closest miss: cost drag fell monotonically with bar size (ES median selection Sharpe -5.3, -3.7, -2.8, -1.7 for 5/10/15/30 min) | 4% | cycle 12 follow-up
- FU5 B11 level breakouts and B7 time-exit books on YM, ZB, 6E, SI, HG, NG | transplant the instrument-specific session open to new markets | 3% | cycle 12 follow-up
## Batch R1-R10 (B2356 worker, 2026-10-16; coordinator: kurtosis conditioning, longer-exit Asian breakout, intraday versions of daily-only next-open families on the 16 path-resolved markets, 2-4 week macro cross-asset momentum with monthly rebalancing evaluated 2013-2026)
- R1 realised-kurtosis jump-regime reversal (daily): kurtosis of the last 20/60 daily changes >= 3/6 -> fade the last day move, hold 1/3 | jump regimes mean-revert / liquidity-provision premium | 4%
- R2 Asian-range London breakout with LONGER exits (path): exit at the next label day 08:00 or 2 days later, stop opposite / 1 / 2 ATR | S2 closest family but holding through the next sessions | 4%
- R3 30-min failed-breakout (N=20/40 bars) reversal, hold 2/4/8 bars, 16 markets | intraday analogue of Z4 | 3%
- R4 30-min skew reversal (W 40/120 bars), 16 markets | intraday analogue of S3 | 3%
- R5 30-min close-streak fade/follow (N=3/4), 16 markets | intraday analogue of Y1 | 3%
- R6 30-min vol-contraction momentum (ATR5/ATR20 bars <= 0.6/0.8, trend 20/60 bars), 16 markets | intraday analogue of Y2 | 3%
- R7 30-min outside-bar follow/fade by close location, 16 markets | intraday analogue of Z5 | 3%
- R8 30-min bar-gap-and-go/fade (bar open outside prior bar range, confirming candle), 16 markets | intraday analogue of Z3 | 3%
- R9 macro momentum, 2-4 week lookback (10/15/20 days), monthly rebalance (19-day hold), time-series sign or cross-sectional top/bottom, ALL26 or macro12 | standard macro/CTA short-lookback momentum evaluated 2013-2026 | 5%
- R10 same grid, REVERSAL (contrarian) | 1-month reversal in futures (Moskowitz-style short-horizon reversal) | 4%
## Batch Q1-Q10 (B2356 worker, 2026-10-16; coordinator: combined R9 + weekend-fade book allowed, component choices counted). Panel/cross-sectional monthly families on the macro12 and 26-market universes, one book.
- Q1 ONE book: W6_0.25_h1_SCR (weekend fade) + R9_20_XS_MACRO12 + R9_20_XS_ALL26 + V5_5_rev_EQ + ES dip-buy, inverse-vol, own selection-corrected null (5 component choices) | diversifier of the weak leads | 4%
- Q2 asset-class momentum: long the strongest / short the weakest of 6 classes by mean 20/60-day z, monthly, mom or rev | macro class rotation | 3%
- Q3 CTA-style lookbacks 63/126/252 days, monthly rebalance, TS or XS, ALL26 or macro12 | the standard trend premium evaluated 2013-2026 | 5%
- Q4 R9 at WEEKLY rebalance (hold 4 days), L 10/20, mom/rev | R9 closest miss at higher turnover | 4%
- Q5 R9 local grid (macro12 XS monthly): L 15/20/25/30 x breadth k 2/3/4 | tests whether the R9 cell is a plateau or a spike | 4%
- Q6 volatility-compression cross-section: rank ATR5/ATR60, long most compressed, monthly, mom/rev | compression -> expansion cross-section | 3%
- Q7 52-week-high proximity cross-section (George-Hwang XS), monthly or weekly | anchoring, cross-sectional version of Y3 | 4%
- Q8 skew cross-section: long lowest 60/120-day skew, monthly, direction both | skew preference | 3%
- Q9 low-volatility anomaly cross-section: rank ATR20/price, long lowest vol, monthly, direction both | low-vol premium | 3%
- Q10 within-class cross-sectional momentum monthly (EQ, FX, commodities, rates), L 10/20/40 | class-neutral momentum | 4%
## Batch N1-N7 (B2356 worker, 2026-10-16; FIRST BATCH UNDER GATE AMENDMENT 2: selection on CLEAN only, 2013-22 reported as ERA flag). Mechanisms chosen for the modern microstructure (0DTE/closing-auction flows, VIX curve data from 2018, macro event bars).
- N1 cash-close bar: the 15:30-16:00 ET bar move (closing-auction imbalance) followed or faded in the 16:00-16:30 bar, ES NQ RTY YM | MOC imbalance reversal after the cash close | 4%
- N2 event-bar continuation: the 30-min bar of FOMC (14:00), NFP/CPI (08:30) followed or faded to the day end, ES NQ ZN GC 6E | event under/over-reaction (path-resolved) | 4%
- N3 VIX-curve slope: VX F2/F1 - 1 below 0 (backwardation) or below 3% -> long ES/NQ/RTY next open, hold 1/5 (VX data 2018-11+) | stress premium mean reversion (volatility risk premium) | 5%
- N4 risk-driver lead: 5/10-day move of 6J, 6A or HG sets long/short ES+NQ for 5 days (both signs) | carry-unwind / risk-on proxies lead equities | 4%
- N5 copper/gold ratio: 10/20-day change of HG vs GC pct returns -> long ES / short ZN when rising (risk-on) | classic cross-asset risk gauge | 4%
- N6 overnight-range position at the RTH open: first RTH bar close in the top/bottom 15/25% of the 18:00-09:30 range -> follow or fade for 2 h or the day, ES NQ RTY YM | overnight inventory vs RTH acceptance | 4%
- N7 weekly-range position: Friday close in the top/bottom 10/20% of the week's range -> follow or fade next week (5 days), ALL26 or SCR | weekly auction acceptance | 3%
## GAPMAP claim G1-G5 (B2356 worker, 2026-10-16; daily/weekly horizon, standalone/additive/constant-risk cells, data on disk; SEL=clean from the start)
- G1 [D08 x H5,H6 x M1-M3 x NQ ES RTY YM GC CL ZN BTC VX] realised-vol-regime timing: long or short each instrument when its own ATR20 percentile (252d) is low (<= 0.33) or high (>= 0.67) [VX: level percentile], hold 1 or 5 days | vol regime predicts the sign of next-week returns (vol risk premium / leverage effect) | 4%
- G2 [D07 x H5,H6 x M1-M3 x BTC, VX] cross-asset: BTC follows/inverts ES, NQ, GC or 6J 5/10-day moves; VX reacts to ES drawdowns and own momentum | BTC as a risk asset; VX as hedge | 4%
- G3 [D10 x H5,H6 x M1-M3 x GC CL ZN BTC] event-week drift: the week of FOMC / NFP / CPI (Mon open -> Fri close) and the event day, long or short | event-week risk premia in non-equity markets | 3%
- G4 [D06 x H5,H6 x M1-M3 x BTC] BTC calendar: weekday, Friday->Monday weekend, month turn | crypto weekday seasonality (documented in spot) | 3%
- G5 [D11 x H6 x M1-M3 x BTC] BTC weekly price patterns: TS momentum 4/8/13/26 weeks follow/fade, weekly Donchian | crypto momentum at weekly horizon | 4%

## Batch 3 ideas (worker J9P, 2026-10-16 ~19:00Z). Pair-side only (NQ ST+HM, B.Cfg(wk_floor=8)). Sources: LEDGER.md (every directive), D3 S2 (lock cost on trend/high-range days, no lock-minute observable separates it), D3 S5 (hour/dow/side/book not stable across spans; ST decayed to ~10% of H1/H2 P&L while HM carries 90%), D3 S6 lever table (win rate, average loss and win, 1 tick of fill move the number), closest misses (H11-B whipsaw halt, H8-C VX slope, H7-C risk-on/off, H10-A, G6c, K10). Checked against REPORT_*, PREREG batches J0 (stagnation/overnight-carry/stuck-underwater exits), J5W (H11-B variants), J11 (week-floor tighten-only), J6 (bar-phase minute), G8-E (option OI), C2-G1 (max-hold, breakeven, trail, scale-out), C1-F5/G10-3 (macro filters/halts), B9/H7-A/H7-B (ES/RTY agreement/spread), BASKET, OPTIONS/OPT0DTE, B14 (GBM on 36 entry features), D2 E1-E8, G11-A/B/C, H11-A, H0a-d. Ranked by prior; 1-3 were pre-registered and run, 4-10 queued.
1. J9P-A  Own-NQ multi-day return alignment (D11 x M4/M8, H5): is the entry side with or against the 3/10/30/60-session drift of NQ itself; tilt 0.5x counter / 1.5x aligned. Mechanism: breakout/trend systems earn on persistent drift; B9 used ES/RTY 5-min agreement, G11-A/B prior-day position/range, H11-A intraday ER; none used multi-day own-drift alignment. Prior 5%. RUN.
2. J9P-B  Unscheduled jump-shock halt/half (D07/D10 x M7, H1-H2): abnormal 1-min move vs its own same-minute norm (k 8-16 x mean |r|) opens a window of reflexive vol/wide spreads; skip or halve entries in the next 15-60 min. Mechanism: news that no calendar lists; H10 covers only verified FOMC/NFP/CPI rows (33-50), H11-B reacts to the pair's own stops. Prior 3% (broad coverage: 5-17% of entries flagged). RUN.
3. J9P-C  Run-up-into-entry (chase) tilt (D11 x M4/M8, H2): magnitude (not efficiency) of the 10/30/60-min move in the trade direction before entry; tilt 0.5x chase / 1.5x pullback entries. Mechanism: late entries after a run mean-revert into the 60-pt stop; lever table says entry price quality is worth +0.30 Sharpe per tick. Prior 3%. RUN.
4. NKD-state tilt of Globex entries (D07 x M4, H3): sign and size of the Nikkei futures Tokyo-session return in the trade direction as 0.5x/1.5x tilt on 18:00-03:00 ET entries. J10 tested NKD as an NQ standalone lead (NO), not as pair conditioning. Prior 2% (J10 found no lead, so the conditional should be weak). QUEUED.
5. NQ/ES realised-vol ratio (60-min) as NQ-specific-stress tilt (D07/D08 x M8, H2): H7-A used the return spread; the vol ratio detects tech-specific (megacap) stress regimes where NQ trends diverge from the broad index. Prior 3%. QUEUED.
6. Volume-climax exit (D01 x M5, H1-H2): exit an open trade when a 1-min bar volume >= k x same-minute 20-session norm occurs in the trade direction with the trade >= X pts in profit (exhaustion/absorption). H7-B was price-spread, J6c is clock-based, C2-G1 unconditional. Prior 3%. QUEUED.
7. Early adverse excursion exit at 2-5 min (D00 x M5, H1): MAE > X pts in the first 3 minutes (J0-C works at hours, J0-A on stagnation) exits at market; fast adverse impulse = informed flow against. Cost heavy (2 slippage fills on a smaller loss), prior 3%. QUEUED.
8. Sunday-open weekend gap state (D06/D11 x M4, H2): size the first 6 h of each week's entries by the gap vs Friday close, in the trade direction; S5 shows the 18:00 hour is the largest and least stable bucket (clean 38% of net, H1 -24%), W6 weekend-gap fade is a standalone lead. G8-B covered only the RTH overnight gap. Prior 3%. QUEUED.
9. ST/HM bracket asymmetry by multi-day alignment (D11 x M5/M6, H5): target 70 / stop 50 with-trend, 50/70 against; engine-hard (needs the 1-s replay rebuild of rows; G11-C proved the 60/60 is a sharp optimum, so the prior is low). Prior 2%. NOT RUN.
10. K4 daily forecast as direction-alignment tilt for the pair (D12 x M4, H5): K4's walk-forward LightGBM p (a LEAD sleeve) as the alignment feature in idea 1; the per-day p was not saved (K4v2 re-run needed), long-only bull sample. Prior 3%. NOT RUN (cost: model rebuild; revisit if K4v2 confirms).
Tie-break among the 3% ideas (2, 3, 5, 6, 7, 8, 10): independence from tested observables and absence of a data dependency; 5/6/7/8 need new feature builds, 10 a model rebuild, so 2 and 3 were taken.
- L90 composite ES+NQ price path ST/HM executed on ES | cleaner signal path | 4% | NO (REPORT_L90)
- L91 ST/HM/WT on NKD Asia hours | Nikkei lead in its home session | 3% | NO (REPORT_L91)
- L92 BTC wide-trail cure | plateau of the one B1 lead | 15% | NO: ensemble loses H2 (REPORT_L92)
- L93 GC fade neighbourhood ensemble + stop model | cure of B7 GC lead | 15% | STRONG LEAD, replication not met (REPORT_L93)
- L94/L95 | duplicates of T1b/U2 and Q5ENS | skipped
- K82/83/85-89 ML with flow+gamma on pair entries | whipsaw predictable from state | 8% | LEAD-weak, fails null/transfer (REPORT_K)
- K84 GBM direction sleeve NQ/ES with flow | flow predicts short-horizon direction | 4% | NO (REPORT_K84)
- FU1-FU5 (6E/6J/6B/6A/6C/ZB/SI/HG/NG and ETH-only families) CANCELLED: not in GAPMAP; replaced by GAPMAP cells YM+BTC for B1/B4/B7/B10/B11 and the L/K cures.

## Batch 7 ideas (worker ap_py3, 2026-10-17). Pair-side only (NQ ST+HM, B.Cfg(wk_floor=8,wk_loss_pb=None)); built from the nearest misses PX26 (overnight gap/ADR, plateau 1.00 but H2 +0.08), PA5/PX1 (60-min NQ/ES vol ratio, H2 +0.06 then -0.16), PX25 (first-hour range), J6a (entry-minute skip, LEAD: fails own null .88, CI, H0 -0.22) and H11-B (whipsaw halt = late-day truncation). Duplicate check done against LEDGER.md, GAPMAP_UPDATES.md, DECISIONS.md, REPORT_PX26/PX25/PX1/PA5/J6a/J5W/H11_B (no two-feature tilt, no book-split of the minute skip, no afternoon-trigger or next-session halt, no regime-signed gap tilt exists). Every one of the four uses observables already read in a parent report, so H1/H2 (and in PY8 H0/alt-month for the all-book version) are NON-VIRGIN; maximum status is FOUND-PENDING.
1. PY7  Two weak independent signals, each with its own pre-registered sign, combined as a shrunk linear tilt: m = 1 + lam*(z_gap + z_vol)/2, z_gap = clean-frozen rank-z of ALIGN (side x gap/ADR20; aligned with the overnight gap = good, from PX26), z_vol = minus rank-z of the 60-min NQ/ES realised-vol ratio (high NQ-specific vol = bad, from PA5/PX1). Mechanism: two near-independent state variables each carry a small, same-direction-as-registered edge on trend-rule entries (gap acceptance, NQ-only stress); averaging two weak ranks halves the noise variance of a tilt and the shrinkage lam keeps the size range inside +-lam (no single tercile bet, which is what failed plateau). Cells: W {45,60} x lam {0.25,0.5}. Prior 4% (each parent was NO; the combination is a variance-reduction bet, not new information). Controls: gap-only and vol-only at the same lam, flat-size, block-permuted state, selection-corrected null.
2. PY8  Minute-of-hour entry skip x book split: J6a (all-book skip of :00/:15/:30/:45 fills) is a LEAD only on pooled data. Mechanism claims a fill-phase cost (bar-close/algo-clock spike at the fill) that must live in the book whose signal is evaluated at the bar close; if it is a real microstructure cost it is book-specific and phase-specific, if it is noise it will not localise and the +-1-minute shifted windows will do as well. Cells: book {ST,HM} x m {0,0.5} (window b15k1 fixed from J6a), not renormalised (reduce-only), flat-size control = mean multiplier. Specificity gate: +-1-minute shifted windows must keep < 50% of the uplift. Prior 3%. ES/RTY standalone-book leg run for the selected cell.
3. PY9  H11-B x time of day, the other half: H11-B's gain was late-day truncation (random morning break rank .03 on the morning-only control); so test whether the AFTERNOON whipsaw is informative. Trigger: N=2 stop-outs with hold <= X min whose exit falls 12:00-16:59 ET; action HALT or HALF on the rest of the label day (SAME) or also on the next label day's Globex night and morning before 12:00 ET (NEXT). Mechanism: a late-day failure cluster marks a range/auction regime that persists into the next session open (inventory/overnight carry), unlike a morning cluster where the halt only removes the afternoon trend. Null: random afternoon break on the same fired days with the same action and scope (matched truncation, the control that H11-B lacked). Cells: X {10,20} x act {HALT,HALF} x scope {SAME,NEXT}, N=2 fixed. Prior 3%.
4. PY10 PX26 sign-flipped by regime: PX26 ALIGN_TWO/COUNTER_DOWN gains are positive on clean and weakly in H1/H2 but split sign between alternating-month halves (the carried cell was -0.03 held-out), the signature of a sign that depends on the regime. Regime = mean over the previous L sessions of gapadr x (RTH close-open)/ADR (gap continuation score, known at the open); sign>0 keep PX26's sign (aligned with the gap = up-weight), sign<0 flip it. m = 1 + lam*sgn(R_L)*tercile(ALIGN) (+1 top, -1 bottom), renormalised to mean 1. Cells: L {10,20} x lam {0.25,0.5}. Controls: UNFLIPPED and INVERTED at the same cell; gate: flipped must beat unflipped on clean. Prior 3%.
Selection for all four: clean 2023-08..2025-07 only (best clean uplift among 4 cells; 8 for PY9); H1/H2 read once for the carried cell.
- Q1 NQ index rule books (B4/B7/B10/B11 grids) | where the pair earns | 3% | Q1B LEAD (10m ST WITH, 180m), Q1D weak LEAD, Q1A/C NO
- Q2 B7 on metals/energy | GC-fade transplant | 3% | LEAD weak (RB/HO 5m Donchian fade)
- Q3 B1 on metals/energy | NO
- Q4 B4/B10/B11 on metals/energy | Q4C weak LEAD (SI OR15 fade), others NO
- Q5/Q6/Q7 B7/B1/B4+B10+B11 on FX | NO
- Q8 all five grids on ETH | Q8D LEAD (prior-day break WITH trail), others NO
- Q9 rates (B1/B7/B11) | NO
- Q10 grains (B7/B1) | NO
- GC FADE v2 combined battery; K_CURE whipsaw GBM null selection | see REPORT_GC_FADE_V2.md, REPORT_K_CURE.md

## Batch 8 ideas (worker ap_pz2, 2026-10-17). Pair-side only (NQ ST+HM, B.Cfg(wk_floor=8,wk_loss_pb=None)); prefix ap_pz*, outputs autopilot/pz1..pz5, IDs PZ1..PZ5. Duplicate check done against LEDGER.md, GAPMAP_UPDATES.md, DECISIONS.md and REPORT_G*/H*/J*/K*/PA*/PX*/PY*: tested neighbours are PY4/PY5 (per-book percentile tilt on RV20 LEVEL, GAP, VR60), B17 (trailing 4/8-week P&L vol), H8-A (RV20 week floor), G8-C (prior-20-day-range day lock), J9P-A (own multi-day drift ALIGNMENT of the entry side), PY1-3 (VIX/VVIX/SKEW blocks), PX30/PX31 (weekend/monthly XS), H0a (stacking multiplier by direction only), K20/K22/K24/K26 (per-book give-back, sync-whipsaw entry halt, hourly budget, combined open-risk entry block), NETTING (opposite entry nets the open position: live behaviour).
1. PZ1  NQ month-level own-market regime tilt (D08 x H5 x M4/M8). States known before the entry date: TS20 = |20-day log return| / (daily sigma20 * sqrt 20) (trend strength irrespective of direction), DD60 = drawdown of the last RTH close from its 60-day closing high, VT = ln(sigma20/sigma120) (vol compression/expansion). Mechanism: the pair is a pair of fixed-bracket trend rules; a month in which NQ trends persistently or sits in drawdown changes the share of breakouts that extend vs mean-revert, a horizon (20 days, direction-free) that none of the intraday vol states (VR60, GAP) or the entry-side drift alignment (J9P-A) measured. Form: continuous clean-frozen rank-z, m = 1 + sg*lambda*z renormalised to mean 1 (shrinkage lambda in {0.25,0.5} so m within 0.5-1.5), both signs pre-registered because the mechanism does not fix it; flat-size control at the same mean. Prior 3% (PY4 RV20 and B17 found nothing on neighbouring vol states). RUN.
2. PZ2  Partner-event exits (D00 x H2 x M5). When the other book exits a same-direction position while this book's trade is still open, either flatten at the next bar (FLAT) or move the stop to entry (BE). Trigger types: partner STOP (correlated-failure contagion: the shared signal family failed) or partner TARGET (the bracket target is hit: bank vs let run). Mechanism: ST and HM are different signal views of one price path; a stop on one is a measured failure of the move the other is also trading, and a partner target marks the point where the fixed-bracket expectancy of the survivor is most mean-reverting. Not covered: H0a/K26 act on entries, K20/K22 on per-book P&L and entry halts, G0/J0 exits are keyed to the trade's own MFE/age, NETTING flattens only on an OPPOSITE entry (live behaviour). 4 cells = trigger {PSTOP,PWIN} x action {FLAT,BE}. Prior 3%. RUN.
3. PZ3  Partner open-P&L state at entry (D00 x H1-H2 x M4/M7). Same-direction stacked entries (other book open) split by the partner's mark-to-market at the entry bar: underwater <= -theta R (adding to a losing pair) skip/halve, in profit >= +theta R pyramid x1.5; theta in {0.25,0.5} R. Mechanism: stacking is only valuable when the first trade has confirmed; H0a priced stacking regardless of the partner's state (a in {0,0.5,1.5} all NO), K26 blocks on combined open RISK not P&L. 6 cells. Prior 2%. RUN.
4. PZ4  Month-level cross-index state tilt (D07 x H5 x M4/M8). States: DISP20 = |20-day NQ-minus-RTY return| / sigma of the daily spread (leadership/dispersion regime), VNE = ln(sigma20 NQ / sigma20 ES) (NQ-specific stress at a month horizon; PA5/PX1 used 60 minutes), VRN = ln(sigma20 RTY / sigma20 NQ). Same continuous mean-1 form and grid as PZ1. Mechanism: concentration/dispersion regimes (mega-cap-led vs broad) change whether NQ moves are idiosyncratic trend or index beta; E6 dispersion was reported but never used as a size state at this horizon. Prior 2%. RUN.
5. PZ5  Live-weeks forward monitor (D00 x H5 x M7). One script, ap_pz5_forward.py, re-scores every WATCH/LEAD overlay (H11-B N2_X10_HALT, J6a b15k1_m0.0, PA5 L60_TWO_V, PX1 W60_MEAN1, K96b HM stop-entry, PX26 ALIGN_COUNTER_DOWN) on weeks that arrive after the frozen watermark 20261013 and writes outputs/autopilot/watch/FORWARD_OVERLAYS.md; same pre-registered promotion reading as watch_n2x10.py (>= 8 new weeks, new-week uplift >= +0.10, cumulative net difference > 0, worst new week not worse). Not a test cell; no prior. BUILD.
Batch 8 results (ap_pz2, 2026-10-17): PZ1 NO (NQ 20-day regime tilt, +0.06/-0.37/-1.46), PZ2 NO (partner-event exits, -0.11/+0.47/+0.63: reverses clean vs H1/H2, PSTOP cells degenerate FLAT=BE), PZ3 NO (partner open-P&L, -0.12/+0.78/+0.21), PZ4 NO (cross-index month tilt, +0.09/+0.59/+0.47, clean just under +0.10, CI [-0.28,+0.85], plateau 0.25), PZ5 monitor built (watch/FORWARD_OVERLAYS.md). Both PZ2 and PZ4 are clean-weak/H1-H2-strong (the reverse of the usual failure): not selectable on clean; the forward monitor is the only legitimate way to confirm them.

[BK, 2026-10-17] BK1 (SINGLE-NAME SHOCK PAUSE, item 59): NO; clean/H1/H2 +0.11/-0.09/-0.04; prior was <= 3%.

[BK, 2026-10-17] BK8 (late-day fade to the 0DTE pin, item 55): NO; add@20% +0.09/+0.12/-0.04; prior 3%.

[BK, 2026-10-17] BK8 (late-day fade to the 0DTE pin, item 55): NO; add@20% +0.09/+0.12/-0.04; prior 3%.

[BK, 2026-10-17] BK2 (QQQ-vs-NQ BASIS-DRIFT REGIME TILT, item 57): NO; clean/H1/H2 +0.09/-0.37/+0.70; prior was <= 3%.

[BK, 2026-10-17] BK3 (INTRA-NDX DISPERSION, item 58): NO; clean/H1/H2 +0.21/+0.02/-0.18; prior was <= 3%.

[BK, 2026-10-17] BK4 (TOP-10 CONCENTRATION / DISPERSION REGIME TILT, item 60 (+E6)): NO; clean/H1/H2 +0.05/-0.13/-0.79; prior was <= 3%.

[BK, 2026-10-17] BK5 (BREADTH-THRUST DAY LONGER TARGETS, item 61): NO; clean/H1/H2 -0.06/+0.02/-0.09; prior was <= 3%.

[BK, 2026-10-17] BK5 (BREADTH-THRUST DAY LONGER TARGETS, item 61): NO; clean/H1/H2 -0.06/+0.02/-0.09; prior was <= 3%.

[BK, 2026-10-17] BK6 (GEX-SIGN BRACKET SCALING, item 54): NO; clean/H1/H2 +0.29/-0.39/-1.78; prior was <= 3%.

[BK, 2026-10-17] BK7 (0DTE PIN STRIKE AS TARGET CAP, item 49 + 53): NO; clean/H1/H2 -0.12/+0.15/-0.07; prior was <= 3%.

[BK, 2026-10-17] BK9 (0DTE PUT/CALL PREMIUM IMBALANCE ALIGNMENT TILT, item 50): NO; clean/H1/H2 +0.04/+0.11/-0.32; prior was <= 3%.

[BK, 2026-10-17] BK10 (MEGA-CAP EARNINGS NIGHTS: SKIP/HALF GLOBEX ENTRIES, item 76): NO; clean/H1/H2 -0.09/+0.43/-0.02; prior was <= 3%.

[BK, 2026-10-17] BI10 (TIME-SINCE-LAST-FLIP TILT OF THE PAIR, item idea 10): NO; clean/H1/H2 +0.01/-0.55/+0.23; prior was <= 3%.

[BK, 2026-10-17] BI9 (OVERNIGHT VS RTH DECOMPOSITION FILTER OF THE PAIR, item idea 9): NO; clean/H1/H2 +0.25/-0.06/-1.11; prior was <= 3%.

[BI, 2026-10-17] BI1 (same-half-hour return persistence (Heston-Korajczyk-Sadka) (BI batch)): NO; 20 selected cells over 4 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.12

[BI, 2026-10-17] BI2 (overnight/RTH tug-of-war (BI batch)): NO; 9 selected cells over 4 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.17

[BI, 2026-10-17] BI3 (intraday NQ/ES relative-move mean reversion (BI batch)): NO; 20 selected cells over 4 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.26

[BI, 2026-10-17] BI4 (high-volume-day premium (BI batch)): NO; 7 selected cells over 4 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.23

[BI, 2026-10-17] BI5 (prior-week high/low break or rejection (BI batch)): NO; 11 selected cells over 4 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.21

[BI, 2026-10-17] BI6 (daily cross-index lead-lag (BI batch)): NO; 5 selected cells over 4 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.10

[BI, 2026-10-17] BI7 (semi-monthly payday windows (BI batch)): NO; no cell passed the clean selection rule

[BI, 2026-10-17] BI8 (range-shock day next-day drift (BI batch)): NO; 4 selected cells over 4 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.12

[BJ, 2026-10-17] BJ1 (FOMC-cycle weeks (BJ batch)): NO; 4 selected cells over 4 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.05

[BJ, 2026-10-17] BJ2 (power-hour momentum (BJ batch)): LEAD; 11 selected cells over 4 instruments, 1 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.21

[BJ, 2026-10-17] BJ3 (RTH-open magnet fade (BJ batch)): NO; 3 selected cells over 4 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.12

[BJ, 2026-10-17] BJ4 (open location vs prior-day range (BJ batch)): NO; 5 selected cells over 4 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.11

[BJ, 2026-10-17] BJ5 (prior-day close vs RTH VWAP (BJ batch)): NO; 3 selected cells over 4 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.10

[BK, 2026-10-17] BQ1 (CROSS-SECTIONAL DISPERSION / AVERAGE CORRELATION ACROSS 14 OUTRIGHTS: PAIR TILT, item B5-1): NO; clean/H1/H2 +0.05/+0.19/-1.35; prior was <= 3%.

[BK, 2026-10-17] BQ2 (NQ REALISED SKEW / KURTOSIS OF THE PREVIOUS 5 SESSIONS: PAIR TILT, item B5-2): NO; clean/H1/H2 +0.12/-1.01/-0.63; prior was <= 3%.

[BJ, 2026-10-17] BJ6 (VIX-settlement Wednesday (BJ batch)): NO; 14 selected cells over 4 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.14

[BJ, 2026-10-17] BJ7 (lunar cycle (BJ batch)): NO; 3 selected cells over 4 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.04

[BJ, 2026-10-17] BJ8 (month-of-year (Nov-Apr) (BJ batch)): LEAD; 9 selected cells over 4 instruments, 1 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.19

[BJ, 2026-10-17] BJ9 (opening-drive continuation (BJ batch)): NO; 11 selected cells over 4 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.18

[BJ, 2026-10-17] BJ10 (Globex volume share and overnight move (BJ batch)): NO; 3 selected cells over 4 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.05

[BL1, 2026-10-17] drift-matched audit of long/short-biased leads: no status changes of FOUND-PENDING items; 2 leads fail the new null, 2 pass it; Q9 and b2356 daily long-biased families flagged for follow-up.

[BM, 2026-10-17] BM1 (LETF end-of-day rebalancing (BM batch)): LEAD; 16 selected cells over 4 instruments, 1 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.29

[BM, 2026-10-17] BM2 (Amihud illiquidity day (BM batch)): NO; 13 selected cells over 8 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.08

[BM, 2026-10-17] BM3 (Faber SMA timing (BM batch)): NO; 6 selected cells over 8 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.15

[BM, 2026-10-17] BM4 (weekly reversal (BM batch)): NO; 9 selected cells over 8 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.10

[BM, 2026-10-17] BM5 (monthly reversal/continuation at month start (BM batch)): NO; 5 selected cells over 8 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.14

[BM, 2026-10-17] BM6 (ADR exhaustion (BM batch)): LEAD; 13 selected cells over 8 instruments, 2 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.20

[BM, 2026-10-17] BM7 (high/low time order (BM batch)): NO; 2 selected cells over 8 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.06

[BM, 2026-10-17] BM8 (up-day fraction (BM batch)): NO; 11 selected cells over 8 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.15

[BM, 2026-10-17] BM9 (daily z-score reversion (BM batch)): NO; 3 selected cells over 8 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.04

[BM, 2026-10-17] BM10 (overnight persistence (BM batch)): NO; 4 selected cells over 8 instruments, 0 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift -0.03
[BM, 2026-10-17] batch BM done: BM1 NQ late-day reversal is the best new lead (NQ-only, ERA negative, replication fails); FOUND 0.
- Q40 cost decomposition + passive-fill execution test | adverse selection of passive entries | NO rescue (REPORT_Q40)
- BQ1/BQ2 overlays (dispersion/correlation of 14 outrights; NQ skew/kurtosis) | NO
- Q31 weekly TSMOM gated by variance ratio | NO; Q32 morning-range state NO; Q33 intraday TS momentum NO; Q35/Q36/Q37/Q38 NO
- Q34 overnight-to-day: ES/RTY overnight REVERSAL at the US open = STRONG LEAD (replication 1 of 4; ERA negative pre-2023); forward watcher ap_q34_fwd.py every 6 h

[BM, 2026-10-17] BM12 (BM1 reference-price test (BL3)): LEAD; 8 selected cells over 4 instruments, 2 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.29

[BM, 2026-10-17] BM11 (BM1 replication probe on all outrights at shifted clocks (BL3)): LEAD; 17 selected cells over 28 instruments, 1 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.29

[BM, 2026-10-17] BM13 (BM1 reference test, small thresholds for VWAP references (BL3 amendment 1)): LEAD; 10 selected cells over 4 instruments, 2 with uplift>=0.10 on clean/H1/H2 at 20%; best all-in uplift +0.39
