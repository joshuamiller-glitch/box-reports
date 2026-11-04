# DS3_LIVE_RECON - live vs model reconciliation (DIS-O, CAL, 2026-11-04). Measurement only. No PASS claims. Nothing goes to the box.
Scope note + sha256: l2vast/ds3/prereg/DISO_scope.md (hash in DISO_scope.sha256 and the DECISIONS.md line "DIS-O SCOPE NOTE (CAL)"), logged before any outcome table was read.

## 0. Headline
1. **No fill-level file exists in the research folder.** There is no fills.csv, signals.csv or stops.csv anywhere under outputs/ (FILLS_CSV_SCHEMA.md describes them; the joiner floor refuses real data before 2026-11-01 23:00Z, and no post-floor file has been delivered). forward_register/{bt,fade,nyam,sizer_shadow} are empty (logs only). So the requested slice-level items (1 lot / 2 s slice VWAP entry slippage, touched-but-not-filled targets, time-exit slippage by slice, per-signal-id pairing with the engine, fee per fill vs FEES.md) CANNOT be computed. Nothing was fabricated.
2. What does exist in aggregated form: LIVE_RECON.md per-trade table (61 trades, books ST and HM only, weeks 2026-W43 and W44, one fill row per trade, 14 lots, L2-tape reference), LIVE_STOP_JOIN.md, JOIN_RECON.md, DS3_P3_EXEC.md. Section 2 re-tabulates the 61 trades; it is a 2-week sample.
3. Direction of the evidence: live stop exits (n=21, JoinThenMarket) are on average 1.23 pt/lot worse than the replay expectation (CI [-2.47, -0.09], trade bootstrap), -$6.5k over the two weeks (about -$3.2k/wk at 14 lots) on ST+HM. This is the fill-rate effect (join limit filled only 8 of 21), not a model-engine P&L gap that can be pinned to signals.

## 1. Columns needed for the full reconciliation (to unblock)
- fills.csv: trade_id, book, side, qty, price, time (epoch ms), order_type (entry/stop/target/time/flat/join/fallback), fee_usd, reject, synthetic. One row per FILL (not per trade), so slices are visible.
- signals.csv: signal_id (or trade_id), book, signal bar-close time, signal price, side, lots, stop distance, target distance, assigned arm (A native / B join).
- stops.csv: trade_id, stop arm, stop trigger time, first-fill time, fill price, nominal stop level, join accepted / rejected / filled / fallback flags.
- engine side: sizer_harness rows are keyed (label_day, book, sess); a signal_id or entry minute per engine row is required to pair. The live names ST and HM are engine books ST/HM (assumption stated; pairing by book + entry minute, tolerance 1 bar).
With these the script is a ~1 h job; weekly blocks need >= 8 weeks for a meaningful block-bootstrap CI.

## 2. What the existing aggregated tables show (LIVE_RECON.md rows, 61 trades, 14 lots, ET)
Entry slippage vs L2 mid at trigger (pts, + = adverse; not a 1-lot/2 s VWAP; one fill per trade). Whole sample mean -0.02 (consistent with LIVE_RECON.md). By session (n):
| book | session | n | entry slip pts | summed pnl $ |
|---|---|---|---|---|
| ST | asia | 21 | +0.11 | -54,480 |
| ST | london | 9 | +0.89 | -29,685 |
| ST | pre | 2 | -0.66 | -21,620 |
| ST | nyam | 7 | -1.32 | +3,295 |
| ST | nypm | 4 | -1.98 | -15,590 |
| HM | asia | 13 | +0.75 | -94,685 |
| HM | nyam | 2 | +0.75 | +895 |
| HM | nypm | 3 | -1.43 | -20,330 |
Sessions with n < 10 are not interpretable. Total pnl over the two weeks -$232k (these were loss weeks; this is not a model comparison).

Exit outcomes (n): ST: LossExit 16, Target 9, StopJoinFallback 6, ProfitExit 6, StopJoin 5, ComboLock 1. HM: StopJoinFallback 6, StopJoin 3, Target 3, LossExit 3, Rejected 1, ComboLock 1, ProfitExit 1.

Stop exits vs replay expectation (live minus replay, pts/lot, + = live better), trade bootstrap (NOT block; only 2 weeks):
| book | n | mean live-replay | 95% CI | total $ |
|---|---|---|---|---|
| ST | 11 | -1.29 | [-3.28, +0.38] | -3,683 |
| HM | 10 | -1.17 | [-2.68, +0.30] | -2,771 |
| both | 21 | -1.23 | [-2.47, -0.09] | -6,454 |

Rejected joins and fallbacks as their own outcomes (exit vs nominal stop, pts):
| outcome | n | mean vs nominal |
|---|---|---|
| join filled (ST) | 5 | +0.16 |
| join filled (HM) | 3 | +1.11 |
| join failed -> market (ST) | 6 | -4.68 |
| join failed -> market (HM) | 6 | -4.25 |
| broker-rejected join (HM) | 1 | -2.11 |
Join fill rate 8/21 = 0.38, versus replay 0.57-0.85 by time of day (JOIN_RECON: 0.83-0.85 in 08:00-18:00 ET, 0.57-0.68 overnight). Most attempts were overnight/Asia, which lowers the expectation. Fallbacks ran 2.8-10.0 pts beyond the join limit after the 3 s timer.

Target fill: LIVE_RECON.md DS3 table gives +0.03 pt vs nominal (n=26, books KB/PE/SM) and +0.02 (n=4, KB). Touched-but-not-filled cannot be tested without fills plus the 1-s path at fill level; not done.
Time/loss/profit exits (ST_LossExit 16, ProfitExit 6, ComboLock): no per-exit slippage available beyond the table (exit-vs-nominal is "-" for these); not computable.

Fees: FEES.md standard NQ is $4.84 round trip per contract (= 0.242 pt/lot/fill at $20/pt, matching the schema). At 14 lots and 61 trades the standard fee is about $4.1k over the two weeks, ~$2.1k/wk, ~1.8% of the $232k loss. Whether LIVE_RECON pnl is net of fees is not stated in the table, and fee_usd per fill is absent; realised fee vs standard cannot be tested. FEES.md flags that NQ exchange+NFA is a proxy, so a real NT statement line is needed.

## 3. Model-minus-live $/wk per book and contributors
Not computable per signal (no pairing). Substitutes:
- ST+HM stop channel, live minus replay: -$6.5k over 2 weeks (about -$3.2k/wk at 14 lots), dominated by the 12 failed/rejected joins (mean -4.4 pt vs nominal). Model-minus-live on this channel is therefore about +$3.2k/wk (sign: model better). CI from 21 stops over 2 weeks: wide (see per-trade CI above; a block CI is not possible).
- Entry channel: mean slip ~0 vs L2 mid; no sign of an entry cost gap in this sample.
- Target channel: no gap (+0.02/+0.03 pt).
- Fee channel: not testable.
- Engine-took-but-box-skipped / reverse: not testable (needs signals.csv).

## 4. Comparison with P3 (DS3_P3_EXEC.md)
P3 models native stop worth +$3,097/wk across six books (L_PE 1,711, L_KB 531, L_HM 325, L_MV 256, L_SM 208, L_PB 66), with the paired difference dominated by bracket re-anchoring noise. The live ST/HM shortfall above (about $3.2k/wk) is of similar size but covers two books that P3 values at ~$0.3-0.5k/wk, at 14 lots, over two weeks, so it is not a confirmation: (a) different books and lot size, (b) join arm only, (c) overnight clustering, (d) n=21. The live data are directionally consistent with the premise that join-then-market loses to native when the join fails often, and nothing more.

## 5. Three most important discrepancies
1. Join fill rate 8/21 live vs 0.57-0.85 in replay; failed joins cost 4.2-4.7 pt each vs +0.5 for filled ones. This alone explains the stop gap.
2. Data gap: no fills-level or signals-level file, so slice entry, target touches, time exits, fees and engine pairing are all unmeasured. The existing table is one row per trade and ST/HM only; L_KB/PE/SM/MV/PB live rows are not in it for W43-W44 (KB/PE/SM appear only in the DS3 summary rows).
3. A trade was missing from the live CSV (JOIN_RECON 0.5: ST 10-21 04:00 buy 14 lots, ~-$17.7k) and the clock is ET not CT; any pairing by time must use ET and must reconcile missing rows first. Also, the sample weeks were loss weeks (-$232k), so P&L-level conclusions are confounded.

## 6. FORWARD STOP A/B status (FORWARD_STOP_AB.md)
Assignment: day-of-month parity from 2026-11-02 (odd = A native, even = B join). Target ~200 stops per arm.
| arm | n stops in files so far | note |
|---|---|---|
| A native (odd days) | 0 | no stops.csv delivered; floor 2026-11-01 23:00Z |
| B join (even days) | 0 | same |
Pre-A/B historical context (not arm data): join 2.45 pt/stop n=21 (fill 8/21) vs native 1.28 pt n=8 (LIVE_STOP_JOIN). At current rates (a handful of stops per day) 200 per arm is months away.
