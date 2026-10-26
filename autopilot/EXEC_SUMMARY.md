# EXEC SUMMARY — read on a phone

## ANSWER (P1 cost decomposition, 10-16): the 2013-22 failure is a loss of GROSS edge, not cost eating an old edge
Before any cost the pair's gross move per trade over 2013-22 is +0.0003 R (price-scaled bracket, 16,127 trades, t 0.04) or -0.016 R (live fixed 60 pts, t -1.9); in 2023-26 it is +0.036 R (t 3.0) / +0.057 R (t 4.9). Fixed-dollar costs deepen the early loss (0.05-0.08 R/trade in 2013-16 because the tick was 0.83 bp of price and the bracket only 36-54 ticks; ~0.00-0.01 R in 2024-26), but price-scaled costs alone would leave 2013-22 at about -0.01 R/trade. Structural series (RTH share, MNQ share, volume, NQ options share) do not track the pair's rolling gross Sharpe (|r| <= 0.20; 0DTE split pending). Detail: outputs/autopilot/REPORT_P1_DECOMP.md. Under Gate Amendment 2 (ERA) 2013-22 is reported, not gating.

## !! KEY FINDING (added 2026-10-15 22:25Z, C3-H2)
**The live pair has no edge on NQ 2013-2022.** Frozen live rules on 10 years of untouched 1-minute NQ bars: net -$2.2M, weekly Sharpe -0.78, 7 of 10 years lose; it earns only in 2024-2026 (Sharpe 1.7-2.3), 2023 ~flat. Parameters were chosen on 2023-2026, so this is a true out-of-sample failure, not just a bull-market effect (NQ rose in 2013, 2016-17, 2019-21 and the pair lost). Caveats: the 1-minute engine matches the 1-second engine on 90% of entries (weekly corr 0.88, net within ~+-12% by span), so read the dollars loosely; the sign is unambiguous. Read: the pair's edge is regime-dependent. Consider sizing/monitoring accordingly (EXEC_SUMMARY sizing table, HM early-warning table in outputs/d3/REPORT_D3_S3.md). The 5-minute NQ trend family also has no edge in 2013-2022 and is ruled out as a find.
**Scaled-bracket check (P1, 10-16):** I re-ran 2013-2026 with the bracket scaled to price (60 x price/20,000), to the 20-day range, and to ATR120. It does not rescue 2013-22: gross (no-cost) weekly Sharpe is +0.06 / +0.05 / -0.28 (about zero), with costs -1.4 / -1.6 / -2.0, with costs scaled to the bracket -0.4 / -0.3 / -0.8. The edge is 2023+ only, and scaling lowers it there (1.25 vs 1.78). So **no edge 2013-22 holds under scaled brackets**; the failure was not the unscaled bracket. Detail: outputs/autopilot/REPORT_P1.md.
**Why? (C8-Q1, 23:30Z):** none of 21 market-structure statistics (variance ratios, autocorrelation, trend-day share, vol, ADR, volume, flip run lengths) tracks the pair's yearly Sharpe; 2023-26 looks like a draw from the 2013-22 distribution on 19 of 21, yet the pair does not. Most economical reading: the parameters are period-specific. A regime switch on observables (C6-N1) also fails. Options/0DTE positioning can't be tested (no data on the box).
Written 2026-10-15 21:55Z, after D3. Autopilot clock started 21:52Z (ends 2026-10-17 21:52Z).

## 1. The live configuration (corrected NT8-faithful engine)
ST + HM, 8/8 NQ contracts, per-book 5R/-2R daily rule, combined day lock (cap 8R, arm 2R, give back 67%, from 00:00), combined week floor -8R, per-book week rule OFF, TH off, EMA200 filters on both books, 1 tick/side + $34.88 commission. R = $9,600/book. $700k account.

| span | net | weekly Sharpe | max DD | worst week |
|---|---|---|---|---|
| clean 2023-08..2025-07 | $1.33M | 1.46 | $280k (40%) | -$82k |
| H1 2025-08..2026-02-06 | $594k | 2.83 | $152k (22%) | -$78k |
| H2 2026-02-07..10-13 | $761k | 2.30 | $217k (31%) | -$83k |
| all-in (2023-08..10-13) | $2.69M | 1.86 | $280k (40%) | -$83k |

(The pair quoted as 1.35/1.65/2.26 is a different config: per-book -6R week rule on, no combined floor. Both are in DECISIONS.md. $2.81M elsewhere = same series from 2023-02-10.)

## 2. Sizing (contracts per book; linear)
| size | all-in net | max DD | worst week |
|---|---|---|---|
| 4/4 | $1.34M | $140k (20%) | -$41k |
| 6/6 | $2.01M | $210k (30%) | -$62k |
| 8/8 | $2.69M | $280k (40%) | -$83k |
| 10/10 | $3.36M | $350k (50%) | -$103k |
| 12/12 | $4.03M | $420k (60%) | -$124k |

12-month block bootstrap at 8/8: median net $861k, 1% chance of a losing year, **70% chance max DD > 30%, 29% chance > 40%**; median recovery 60 trading days (p90 121). Largest size with P(DD>40%) <= 10%: **6/6**; for 30%: **4/4**. Locks off: 79% chance DD > 40%. Live 8/8 is above both limits.
Slippage: still profitable at 3 ticks/side (net $1.48M, Sharpe 1.02).

## 3. What D3 says about the live cell
- Plateau: only 3% of 404 joint neighbours keep >=90% of net on clean, H1 and H2 together. Live is a good cell, not the centre of a broad plateau (27th of 405 on Sharpe).
- Re-fitting every 13/26 weeks does not beat leaving it alone (same as picking a random neighbour). Don't adopt.
- Day lock: +$149k clean, **-$422k H1**, +$176k H2. H1 had more high-range trend days (51% of lock days) where the lock flattened winners. Nothing known at the lock minute predicts the bad days.
- HM carries ~90% of net in H1 and H2 (44% in clean). ST is the weak book now (26-wk Sharpe ~0.1 in H2).
- HM early warning: 8-week Sharpe below its 10th percentile fired 2026-09-06 with 72% of the loss already booked (~1.2 false alarms a year). One event only.
- Levers (all-in): +5 pts win rate = +190% net; -10% avg loss = +93%; +10% avg win = +106%; 1 tick better fills = +19%. Half-size Globex = -40%. Random 10% fewer trades = -13%.
- EMA200 filters carry the pair: ST off = -93% net, HM off = -22%. Leave at 200.

## 4. Tested since B3 and ruled out (one line each; detail in LEDGER.md)
- Trade Health overlays (NQ7, B3-TH, B8): negative or neutral. Equity-curve rules (B9): none beat plain.
- 4th-engine searches B4/B4b/B5 (MR, fades, 5/15-min): 0 survivors. B6 chop gating: 0 of 12. B7 cross-instrument: 0.
- B10 sleeves (26 tracks): void — judged against the retired 2.74 baseline; re-scored in T3.
- Insurance grid, VOLSCALE brackets/entries, B11 Tracks 1-7, caps, netting variants, HM variants/anchors, entry scaling, week-floor neighbourhood: nothing survived the null; day lock and week floor are the only insurance-type items that hold.
- D1 (8 diversification families: timeframe, parameter, book split, instrument, MBO, session, staggered, optimizer): 0 survivors.
- D2 (E1-E8: vol targeting, tilts, phase bars, soft locks, execution, brackets, streaks, adaptive thresholds): 0 survivors; E9 re-verified 37 candidates on the live config: none verifies. COMBINED_BEST = live unchanged.
- T3: all 8,054 old sleeve series re-scored; session-structure engines (312 cells): 0; ST/HM on ES/RTY/GC/CL/ZN: 0 (ES loses at 1 tick; GC flips sign with slippage); Track L short-VX: no (not executable at NT Brokerage; CFE needs IBKR); bar-feature ML: NO (looks like a timing-destroyed model).
- T4: daily trend book (26 markets, 368 cells): 0, no edge in the pair window; equity dip/calendar sleeves: 0 FOUND (ES dip-buy = lead, 28 trades); flip-failure fade: loses in the pair's bad weeks; more session structure (276 cells): 0; RangeBreak port: 0; CME crypto: BTC wide-bracket lead.
- V5: the 11 five-minute books and their ensemble: all LEADS, none FOUND (fail 2x slippage, plateau, pre-2023 holdout; clean-only selection shows no excess over null).

## 5. The two rules that went live and why
I cannot identify them: the repo records the live rules only as the baseline, not why each was adopted (LEDGER.md notes this). Measured effects: day lock = +clean, -H1, +H2 (insurance-flagged, cost ~3% of net, DD -14% to -53% by span); combined week floor = modest INSURANCE, effect mostly one H1 week. If you tell me which two you mean, I'll add the reasoning.

## 6. FOUND / LEADS (autopilot, updated 2026-10-16 00:25Z; 10 cycles, ~35 families)
**FOUND: 0.** Every family that looked promising died on a gate:
- 5-min NQ trend ensemble: negative corr with the pair but no edge 2013-22, fails 2x slippage/plateau -> ruled out.
- RTY bar-ML cell: fails out of sample 2017-22 -> ruled out.
- ES/YM dip-buy (28-47 trades; amended survivor) and MBO seven (no H2): still leads, both thin.
- BTC wide-bracket ST/HM (T4 E): lead only (share-dependent, Rithmic crypto unconfirmed).
- Autopilot cycles 1-10 (carry/momentum, index spreads, cross-asset filters, vol-regime switch, exit management, meta-labeling, event days, calendar sleeves, intraday momentum, long-history-selected intraday on 14 instruments at 5-/15-/30-/60-/240-min, regime switch, calendar avoid-filters, time-of-day): all NO.
Pattern: rules selected on 2013-22 (NQ/ES/CL) show real in-sample structure but do not add to the pair in 2023-26; cost kills 5-min on everything but NQ; no observable explains the pair's era.

## 7. Open items
- **A5 L2:** NQ mbp-10 job (A5 session, $2,025) still "processing"; ES and RTY mbp-10 jobs submitted 10-15 ($1,851). L2 round runs when files land.
- **MBO 2026 series:** the 3-year file ends 2026-02-06, so no H2; need 2026 trades to judge MBO.
- **Latency:** real gate admits 97-100% overall, but slow setups admit only ~13% in their worst ET hour — check those hours live.
- **Live-fills file** (slippage calibration) still not received; everything is 1 tick/side.
- **Margins** (GC ~ $37k, crypto 25%) are unverified; confirm with NinjaTrader. Whether Rithmic offers CME crypto micros: unconfirmed.
- **Data spend:** autopilot $1,851 committed + ~$380 1-min bars in progress of $3,000; T4 ~$12 of $150.
