# SLEEVE_RSI2_SPEC - DIPBUY_RSI2_2lot (spec for the user's Sim leader; research output, NOT a live change)
Written 2026-10-25 by S48-T3 per user ruling item 5 (RULINGS_2026-10-25.md). Words and parameters only: no code change to any live file, no account numbers, no credentials. One registered PAPER-ALL item with two legs: NQ RSI2C_s20 (leg 1) and ES_RSI2_t10 (leg 2). They are ONE dip-buy exposure (exposure group G1_INDEX_DIP_BUY_CLOSE), not two bets.

## 1. Entry rule (both legs, long only)
- Price series: for each trading day ("label day": ET clock + 6 h, so a day runs 18:00 ET to 17:00 ET; Fri/Sat/Sun roll to Monday) take the OPEN of the 15:55 ET 1-minute bar of the instrument (NQ for leg 1, ES for leg 2). That is one price per day, known at 15:55:00 ET.
- RSI(2) on those daily 15:55 opens: simple two-period smoothing with weight 1/2 (average up-move and average down-move are each updated as (previous + new)/2; the first average is the mean of the first two changes); RSI = 100 - 100/(1 + avgUp/avgDown), 100 if avgDown = 0. The value for day t uses day t's own 15:55 open (the signal is as-of 15:55:00).
- Signal: RSI(2) < 10 (threshold 10 for both legs; neighbours scored 5 and 15). No trend filter in either leg (the SMA200-filtered variant RSI2T is a different cell).
- Order: long market order, entered at the CLOSE of the 15:55 bar, i.e. about 15:56:00 ET. Backtest entry price = that bar's close, cost 1 tick per side adverse plus fees (see 5).
- Name decoding: RSI2_t10 = RSI(2) < 10 (t = threshold), hold 1 trading day. RSI2C_s20 = the RSI2_t10 signal ('C' = catastrophe-stop variant) with a protective stop at entry - 2.0 x ATR14 (s20 = stop multiple 2.0 x 10). ES_RSI2_t10 = the plain RSI2_t10 rule on ES with NO stop (time exit only). The two legs deliberately differ; both are as scored.
- ATR14 for the stop: Wilder ATR(14) of the daily true range on label days, taken from the previous completed label day (typical NQ value ~350 pts, so the stop sits ~700 pts = ~$14,000 per NQ lot below entry). Confirm the exact ATR construction against code/t33lib.py build() before wiring (flagged as an item to verify, not a known mismatch).

## 2. Instruments and contracts
- NQ (E-mini Nasdaq-100, $20/pt, tick 0.25) and ES (E-mini S&P 500, $50/pt, tick 0.25), front (volume-leading) quarterly contract. Backtest data: Databento 1-min continuous .v.0 series (volume roll), additive-adjusted; micros (MNQ/MES) would carry the same signal at 1/10 size: fees per FEES.md (MNQ/MES $1.78 RT proxy) but were not separately scored.
- Hold session: overnight, one full session (from about 15:56 ET to the 15:56 ET close of the next trading day), including the 17:00-18:00 ET halt and the Globex overnight. Friday signals are held over the weekend to Monday 15:56.
- Roll handling: the backtest DROPS any trade whose entry-to-exit span crosses a contract roll (so no roll-gap P&L is in the numbers; knowing the roll date in advance is a mild look-ahead of calendar only). Live rule: trade the contract that is the volume leader at entry and skip a signal if the roll to the next contract happens between entry and exit.

## 3. Lots
- Spec: 2 contracts per leg: 2 NQ + 2 ES per signal day (4 contracts when both legs fire; both legs fire on the same day on 209 of 404 distinct signal days since 2023-02 (52%), weekly correlation of the two leg P&Ls 0.61; the NQ RSI2_t10 and ES_RSI2_t10 pair is 0.73).
- Scaling equivalents (the tested portfolio ratios): ratio 0.25 = SD of the sleeve equals 0.25 x Set A weekly SD = 6.0 NQ lots (RSI2C_s20) or 9.6 ES lots; ratio 0.5 = 12.0 NQ lots or 19.2 ES lots; ratio 1.0 = 24.0 NQ or 38.5 ES lots. So 2 lots is ~0.08x of Set A risk on the NQ leg (about one third of the 0.25x cell); verdicts at 0.25/0.5/1.0 describe much larger sizes than this Sim spec.

## 4. Exit rule
- Time exit: market order at the close of the 15:55 bar (~15:56:00 ET) on the NEXT trading day that has a 15:55 bar (hold = 1 trading day; a Friday entry exits Monday).
- Stop (NQ leg only): resting stop-market sell at entry - 2.0 x ATR14, active from the bar after entry through the exit bar, including the overnight session. Backtest fill = min(bar open, stop - 1.01 pt), i.e. gaps fill at the open. Stopped in 3 of 70 WF NQ trades. The ES leg has no stop; its worst WF trade was -$16.6k per ES contract.
- No target, no trailing, no re-entry the same day, one position per leg (a signal while the leg is already held cannot occur because the hold is one day).

## 5. Fills and costs assumed in the backtest
- Engine: 1-MINUTE bars (not the 1-s tape) for both legs; the NQ leg was also re-scored on the 1-s tape in T3.10b (stop-join 1.01 pt, market 0.995 pt) with the same verdict PASS at 1x, 1.5x, 2x cost. ES has no 1-s tape: conservative model of 4 ticks per side adverse plus $4.84 RT (1x, 1.5x, 2x scaled) still PASS. Limit fills would require trade-through; this sleeve uses market orders, so that rule is not exercised.
- Costs per contract round trip: NQ $14.84 (= $4.84 fee + 1 tick per side = 2 x 0.25 pt x $20); ES $29.84 (= $4.84 + 1 tick per side = 2 x 0.25 pt x $50). 2x cost: 29.68 / 59.68. FEES.md grades the NQ exchange fee as a proxy.

## 6. Position-limit interaction with Set A
- Set A holds at most 14 + 14 = 28 NQ lots (two books). It enters 18:00-14:59 ET and is flat by the 16:55 flatten, so at 15:56 ET it can still be holding. Worst case NQ concurrent = 28 + 2 = 30 contracts (<= 50-contract limit). The ES leg is a different instrument (2 ES). Margin: 2 NQ + 2 ES overnight is additional initial margin; check the Sim account margin model.
- Netting: Set A shorts are NOT netted against this long unless the Sim leader shares an account; run the sleeve in its own account (below).
- Combined-system sequence test (locks, give-back, week floor, 50-contract) is the lead's job and is scored separately; the sleeve has no interaction with the D2 lock engine in the backtest (independent sleeve).

## 7. Backtest expectation (WF = 2024-02..2026-10, 142 weeks; after live cost; 1 contract unit then x2)
| series (2 contracts) | WF mean/wk | SD/wk | maxDD (weekly) | worst week | L8W mean/wk | IS (2023-02..2024-01) mean/wk | HOLD (2025-07+) mean/wk |
|---|---|---|---|---|---|---|---|
| NQ RSI2C_s20 x2 | 1,777 | 8,754 | 44.8k | -34.8k | -2,599 | 351 | 2,163 |
| ES RSI2_t10 x2 | 1,314 | 5,450 | 30.4k | -30.4k | +1,634 | 191 | 1,531 |
| both legs (2 NQ + 2 ES) | 3,091 | 12,837 | 65.2k | -65.2k | -965 | 542 | 3,694 |
- Weekly correlation of the 4-contract sleeve with Set A: -0.00 (WF).
- Per trade (1 contract): NQ leg mean +$1,789, SD $8,798, hit rate 59%, mean 90 pts, worst -$19.9k, best +$42.6k; ES leg mean +$1,545, SD $4,746, hit 68%, mean 31.5 pts, worst -$16.6k, best +$24.3k. At 2 lots double these. Trades: NQ 70 in WF (18/30/22 in 2024/2025/2026 = about 26 a year, 0.49 a week); ES 60 in WF (16/25/19 = about 22 a year, 0.42 a week). THE 56-139 TRADES CAVEAT: the dip-buy family has only 56-139 trades in the 142-week WF window, so the effect is not significant on its own; individual CIs touch zero at ratio 1.0.
- Year shares of WF net (1 contract): NQ 2024 22%, 2025 32%, 2026 (to Oct) 46%; ES 2024 15.1%, 2025 44.6%, 2026 40.1%. Both legs together: 2025+2026 carry about 76% of the 2023-2026 P&L. No single WF year above 60% of a leg's gain (the test limit); NQ 2026 is the nearest (46%).
- Weekly with Set A at tested ratio 0.5: portfolio delta mean +$10,568/wk (NQ leg, CI [2,294, 20,281], placebo 0.978, holdout delta +12,766) and +$12,559/wk (ES leg, CI [3,559, 22,101], placebo 0.990, holdout delta +14,513). MDE (80% power) 12.9k and 13.3k per week: the Set A-relative weekly test has barely enough power for these effects.
- Pre-2024 out-of-sample (NQ RSI2_t10 plain rule 2013-2023): +$163/wk per unit, CI [36, 301], placebo 0.986, 8 of 11 years positive; ES 2013-2023 positive (9/11 years); the exact RSI2C_s20 stop variant was not separately scored pre-2024.

## 8. Placebo, DSR, cost stress, verdict history
- Verdicts: lead leaderboard PASS for both RSI2C_s20 and ES_RSI2_t10 (V2 sleeve criterion: standalone holdout mean > 0, marginal portfolio Sharpe up at the tested ratio, corr <= 0.5). T3.10b robustness: PASS at 1.5x and 2x cost and on the NQ 1-s tape; unchanged at 10,000-draw bootstraps (mean-delta CI excludes 0 at all three ratios; marginal-Sharpe CI includes 0 at 0.5x and 1.0x, excludes 0 at 0.25x).
- Placebo: WF 500-draw rank 0.978 (NQ leg) and 0.990 (ES leg). Fresh-seed pre-2024 ranks: RSI2C_s20 0.932 (5,000 draws 0.917), ES_RSI2_t10 0.944 (5,000 draws 0.962); the other dip-buy variants span 0.904-0.944 (RTY 0.904, 5,000-draw 0.870). Under a min(WF, pre-2024) convention both would read CANDIDATE, not PASS. Rank standard error near 0.95 with 500 draws is about 0.010.
- DSR: well below 0.95 (RSI2_t10 family about 0.10 on the cumulative ~28.5k-trial ledger): the selection history (41+ ideas scored, RSI2 chosen after seeing results) means the discovery is not corrected-significant.
- Cost stress: NQ leg mean at 2x cost 20,962 vs 21,137 per week at ratio 1.0 (costs barely matter for this low-turnover sleeve); ES leg 24,632 vs 25,117.
- The neighbours (RSI thresholds 5 and 15; stop 1.5 and 2.5 x ATR) agree in sign.

## 9. Independent-exposure grouping
G1 index dip-buy at the 15:55 close contains 10 of the 16 PASS/CANDIDATE sleeves (RSI2, RSI2T, IBS, RSI2C, RSI2CC, COMB, ES/RTY/YM variants); within-group correlation up to 0.95. NQ RSI2C_s20 vs ES_RSI2_t10 weekly correlation 0.61 (NQ RSI2_t10 vs ES 0.73): ONE bet, two legs. Correlation with Set A -0.10 to +0.10. Other groups (overnight long, 16:00-18:00 long, ORB Asia, GSHORT) are separate and NOT part of this spec.

## 10. Forward expectation and V2 rules
- Expectation for the 2+2 spec: +$3,091/wk (SD $12,837), about 0.9 signal-days a week -> roughly 20-25 signal days a year; per trade-day about +$3.5k (2 NQ) / +$3.1k (2 ES). Register one PAPER-ALL record 'DIPBUY_RSI2_2lot' with both legs; official weeks W44+.
- V2 rules: PROMOTE = at least 6 weeks live, realised within 1 SD of expected, sign right; RETIRE = at least 8 weeks live and more than 2 SD behind expected. With SD 12,837/wk, 6 weeks have SE 5,240; realised cumulative must be within ~$5k/wk of $3,091 and positive. In 6-8 weeks the sleeve will have about 5-7 trade-days: the forward test is EXTREMELY underpowered (detecting the expected mean at 80% power needs about 135 weeks), so ON TRACK / BEHIND will mostly reflect luck, and a RETIRE call is as noisy as a PROMOTE call. Read the per-trade table, not the z.

## 11. What could kill it
1. It is dip-buying beta: long index overnight. A trending bear market or a vol shock (the lone 10-15 to 10-16 2026 NQ trade lost -$15.3k per lot, -764 pts) loses several trades in a row; 2022 (outside the scored window) is a known weak year for related overnight-long rules. Weekly worst -$65k for the 2+2 spec in WF.
2. Tiny sample: 56-139 trades; the edge is concentrated in a few large winners (best NQ trade +$42.6k per lot; 2025-2026 carries most of the gain). Fresh-seed placebo is 0.917-0.962, DSR small, and the signal was selected after looking at results.
3. Regime: 2024 was weak (NQ 2024 +$27k on 18 trades); the recent 8 weeks are -$1.3k per NQ lot.
4. Fills: the 15:55-15:56 market order and the overnight stop are 1-min assumptions; ES is 1-min only; stop gaps overnight can exceed the 2 x ATR level (stop fills at min(open, stop - 1.01)); Sunday-open and holiday gaps.
5. Holidays and half days: no 15:55 bar on early closes (13:00 ET); the backtest exits on the next day that has a 15:55 bar and has no row for half-day entries; do not trade a half day entry; holding across a holiday is included only when the next trading day has a full session. Rolls: dropped in the backtest; in live, roll week needs the manual skip rule above.
6. Same exposure as Set A shorts at 15:56 is not netted if separate accounts; margin on 4 overnight contracts.
7. Crowding/capacity is irrelevant at 2 lots; capacity at the scored 6-24 NQ lots was not tested.

## 12. How the Sim leader should be wired (description only)
- A separate Sim account and a separate leader configuration from Set A / D2 (so nothing nets against or locks with D2). Two strategy instances, one on NQ (front month) and one on ES (front month), each on a 1-minute chart, session template that includes the Globex overnight and 18:00 ET start.
- At 15:55:00 ET read the 15:55 bar open (last trade at that second); compute RSI(2) on the series of daily 15:55 opens (needs the previous ~30 days of those prints; the strategy keeps its own daily array rather than using chart RSI on 1-min bars, which would differ). If RSI < 10 and the leg is flat and the contract will not roll before tomorrow's exit: submit a market buy of 2 contracts at 15:55:50-15:56:00 ET. For the NQ leg immediately attach a stop-market sell 2 x ATR14(prior day) below the fill price; ES leg has no stop.
- Exit: market sell at 15:55:50-15:56:00 ET on the next trading day with a full session (cancel the NQ stop at the same time). One trade at a time per leg. Log entry/exit time, price, slippage versus the 15:56 bar close, and the RSI value, to the daily live-file push so FORWARD_REGISTER can reconcile per trade. Leader size: 2 + 2 contracts; copy accounts scale linearly. No other parameter is changed.
- Registration: PAPER-ALL record 'DIPBUY_RSI2_2lot', legs NQ_RSI2C_s20 (2 lots) and ES_RSI2_t10 (2 lots), backtest expectation 3,091/wk, SD 12,837/wk, per-trade as in section 7, exposure group G1, tier PASS(lead)/CANDIDATE(min placebo convention).
