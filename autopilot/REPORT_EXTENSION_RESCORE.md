# REPORT_EXTENSION_RESCORE (addendum to REPORT_EXTENSION_20261017, written 2026-10-17)
**Verdict: registry extended to 12 leads (K4 family = one signal); hard-coded 20261013 ends patched in 54 scripts with backups; additive gate-3 re-score on the longer H2 (36 weeks, to 10-16) changes NO verdict for the 12 registry leads. Q5/Q5ENS and the weekend-gap fades are NOT in the registry yet (daily-bar inputs missing, see 1). The full multi-gate pipelines (nulls, plateau, bootstrap) were NOT rerun.**

## 1. Refresh functions / FORWARD.md registry (forward/refresh_*.py, all definitions untouched)
| lead | refresh script | reproduction check against the stored series | 3 post-freeze days (10-14..16), weekly 90% interval |
|---|---|---|---|
| RW12P | refresh_rw12p.py (ap_r_fams.R12 cell 0) | recomputed 2023-W31..2026-W41 mean weekly uplift x scale = $3,361 = stored mu_unshrunk | $0 flat, -$2,347 .. +$11,038 |
| RX5 | refresh_rx5.py (ap_rx_fams.RX5, 5 seeds) | $2,766 = stored | $0 flat, -$456 .. +$8,557 |
| RW5 | refresh_rw5.py (selected cell K4_a0.25_both_sg+1 of ap_r_pair R5) | live-pair and RW5-pair daily series equal the stored R5_res.pkl (all but the last 3 days) | +$1,070 pair-side, -$22,529 .. +$46,280 |
| L93 GC fade 108-cell ensemble | refresh_l93.py (ap_l93.grid through ap_b_base.run_cell; old part of the dump identical to dump_GC.pkl) | identical on all days before 10-12; prediction frozen now with the registry recipe (ap_ext_pred_l93.py): $4,836/wk at 20% of pair SD, CI of mean $2,097 .. $7,860 | +$23,222, -$16,783 .. +$37,679 (in band) |
K4v2 + RW12P + RX5 + RW5 are ONE signal (PRED_EXTRA note); K4v2/RX5/RW12P are flat for the week (no trade since 09-24/09-11), RW5 only re-sizes pair flips. K4 signal on Fri 10-16: ES p 0.596 (long open into 10-19). Promotion rules are the same mechanical rule as PRED.json (stored in PRED_EXTRA.json; backups .bak_pre_*). ap_forward_score.py now merges PRED_EXTRA.json (backup ap_forward_score.py.bak_pre_ext20261017b). FORWARD.md lists 12 leads.
**Not added (data, not code):** Q5/Q5ENS and the gap fades (Z3/W6/T1b) run in the daily-bar framework (ap_b2356_core / t4 daily_outrights `.v.0` and `.v.1` ohlcv-1d, last bar 2026-10-14). Daily bars for 10-15/10-16 are not on the box; rebuilding them from 1-minute data would change the definition. The purchase would cost $0.0015 (26 symbols, v.0 + v.1, 10-14..10-16); NOT bought (no-purchase instruction). Once the daily files are extended, Q5ENS (ap_q5ens_run recipe) and Z3/W6 (ap_y_run cells) each need a small refresh_*.py; the gap-fade Monday trades of 10-12 and the monthly Q5 rebalance contribute nothing before then. N3 needs VX curve data; BTC WT needs the crypto 1-min file; MBO has no data after 2026-02-06.

## 2. Hard-coded end dates
- 54 scripts with a literal 20261013 end/span were patched to 20261016 (list with line counts: outputs/autopilot/EXTENSION_PATCH_LOG_20261017.txt; originals in code/census/_bak_hc20261013_ext/); ap_i_common.END, SPANS/SP/WIN lists, K4v2/K4P/E7/R12P scorers included. All 54 compile.
- 35 scripts asserted `abs(H2 - 2.30) < 0.01` on the pair baseline; that assertion was removed (clean 1.46 and H1 2.83 assertions kept), logged in the same file.
- Left alone on purpose: ap_ext_*, ap_fv_live (FREEZE), ap_pa3_watch / ap_pz5_forward (pre-registered watermarks), night_b10 history, report/doc generators (prose), ap_c6_n2_gen (string template for 2017-22).
- Re-run policy: the full gate pipelines were not rerun (hours of nulls per lead; the 12 registry leads' series are what the longer H2 touches). They will pick up the new end automatically when next run.

## 3. Additive re-score on H2 to 2026-10-16 (forward/RESCORE_H2_20261016.csv; uplift of weekly Sharpe vs the live pair at 10/20/30/50% of pair risk, pair-side leads at live size)
Pair H2 weekly Sharpe 2.48 (36 weeks) vs 2.39 on the old span. Gate 3 (+0.10 on clean, H1 AND H2): **all 12 leads pass at every share on the old and the new H2; 0 flips.** Selected rows (uplift clean / H1 / H2 old span -> H2 new span):
| lead | share | clean | H1 | H2 old -> new |
|---|---|---|---|---|
| WT-10 | 20% | +0.37 | +0.42 | +0.277 -> +0.278 |
| K4v2 | 20% | +0.18 | +0.39 | +0.195 -> +0.196 |
| RX5 | 20% | +0.28 | +0.20 | +0.329 -> +0.331 |
| RW12P | 20% | +0.26 | +0.65 | +0.399 -> +0.400 |
| RW5 (pair-side) | live | +0.25 | +1.06 | +0.621 -> +0.629 |
| H11-B | live | +0.20 | +0.47 | +0.193 -> +0.197 |
| PERS30 | live | +0.72 | +0.77 | +0.412 -> +0.793 (one strong week: +$62.5k) |
| ES dip | 20% | +0.27 | +1.05 | +0.252 -> +0.254 |
| FVG P1 | 20% | +0.44 | +0.44 | +0.599 -> +0.590 |
| FVG E1 | 20% | +0.65 | +1.00 | +0.866 -> +0.894 |
| FVG IMP3 | 20% | +0.80 | +0.99 | +1.416 -> +1.473 |
| L93 GC fade | 20% | +0.21 | +0.95 | +0.844 -> +0.916 |
Worst-week gate (combined worst week vs pair worst week -$82,524, over 2023-08..2026-10-16): all pass except **L93 at 30% (+30.1% vs 30%) and 50% (+54.5% vs 50%)** (same borderline as before; 10/20% pass). The pair's own worst week is unchanged by the extension. No LEAD/FOUND-PENDING verdict changes. Not re-scored (no refresh function, listed in section 1): Q5/Q5ENS, weekend-gap fades, N3, J4 (no event), BTC WT, MBO, and the remaining CANDIDATES.md leads that live only in the library (series end 10-13/10-14).

## 4. Update (coordinator authorised the daily-bar buy)
- Bought ohlcv-1d `.v.0` and `.v.1`, 26 outrights, 10-12..10-16 ($0.0026, SPEND.json family EXTENSION_2026-10-17, logged first); overlap bars identical; merged into data/t4 (backups data/t4/_bak_20261017; code ap_ext_daily.py). Daily axis now ends 2026-10-16.
- New refresh_b2356.py (Q5ENS, Z3FADE, W6FADE, T1B): the unmodified ap_y_run / ap_t30_run cell runners; each lead's cells reproduce the stored stage-1 pickles exactly (max diff 0.0) before the series is written. Predictions frozen by the registry recipe (ap_ext_pred_b2356.py): Q5ENS $809/wk (CI -617..2,244), Z3FADE $1,699 (-55..3,615), W6FADE $1,938 (51..4,085), T1B $1,641 (-324..3,978); promotion N 78 weeks.
- 3 post-freeze days: Q5ENS $0 (monthly book, no exits), Z3FADE +$4,571 (band -8,070..+15,041), W6FADE $0, T1B $0 (no Monday event). FORWARD.md now lists 16 leads.
- Registry gap that remains: N3 (VX curve), BTC WT (crypto 1-min), MBO (no data), J4 (no event).

## 5. BTC WT (crypto extension)
- Bought CME BTC.v.0 and ETH.v.0 ohlcv-1m continuous, 10-14..10-16T21:30, $0.0232 (quote < $15 cap, SPEND.json family EXTENSION_2026-10-17, logged before buying; reproduction of cell 89 checked before buying). Merged into data/t4/crypto_1m__*_v_0.dbn.zst (overlap identical); b/series_BTC/ETH rebuilt.
- refresh_btcwt.py (B1 cell 89 = 10-min WT ATR20 x3.0 EMA100, ATR(14)x3 trail, equal R) reproduces b1_co/real_BTC.pkl on every stored day up to 10-13 (max diff 0.0035, float32; the stored 10-15 label was a partial day). Prediction frozen with the registry recipe: $3,477/wk (CI $1,974..4,988), shrink 0 (one of 113 passing cells, no selection-aware null).
- **First BTC WT live result: -$25,805 over 10-14..10-16 (-$48.8k on 10-14, -$4.4k, -$9.9k) against a weekly 90% interval of -$12,956 .. +$15,914: BELOW the band (cum band lower -$16,356).** Flagged in FORWARD.md; the kill-watch rule needs >= 6 weeks, so no action, but this is the only lead outside its interval. FORWARD.md lists 17 leads.

## 6. Batch-3 LEADs added (not counted; no purchases)
refresh_cells.py reproduces each stored real_<SYM>.pkl cell (max diff <= 0.0004 on all stored days; only the partial 10-14 day differs): SW4 RTY cell 39, SW20 RTY cell 17, Q12 NQ boll(20,2.5) against h120, Q20 RTY priorclose(0,0.75) against h240. Predictions (20% of pair SD, no shrink, N = 78 weeks): SW4 $3,160/wk (CI 1,315..5,010; ERA-NEGATIVE pre-2023, Sharpe -0.63: the effect exists only since 2023-08), SW20 $2,096 (511..3,656), Q12 $1,505 (-265..3,275), Q20 $2,159 (459..3,941).
3 post-freeze days: SW4 +$9,412, SW20 +$4,058, Q12 -$3,226 (all in band); **Q20 -$21,229 vs weekly interval -12,236..+15,949: below band** (cum band lower -15,751; kill watch needs >= 6 weeks). FORWARD.md lists 21 leads (labels carry LEAD / not counted). Out of band now: BTC WT and Q20.

## 7. FVG IMP3-VC (volume clock) added to the registry (FVG family, counted once; no purchases)
- refresh_fvc.py reruns the unmodified ap_fv17_audit pipeline for VC k1 m1.125 / f0.5 / lat0 on all raw NQ trade files (10 min): 73,233 orders = stored; daily series equals the stored fv17_audit.pkl series exactly (max diff 0.0) and the FV17 library book to 0.008 (float32); fill 79.3%, net R/trade +0.2069 as in REPORT_ICT s23.
- Frozen prediction (standard recipe, R-sized, scale 0.101 so the clean weekly SD is 20% of the pair, NO shrink: no selection-aware null exists for the VC cell): $15,924/wk (CI $14,057..17,906), Sharpe uplift +1.62, weekly 90% -$2,144..+$35,439; trade rule: predicted fill 79.3%, net R/trade +0.207 (SD 1.46), CUSUM k 0.118 / h 54.8, stop if fill < 60% over >= 300 orders; promotion N = 13 weeks, z >= 1.28.
- 10-14..10-16 (scored, post-freeze): +$20,598 vs weekly band -$1,661..+$27,451 (in band); 383 orders, fill 80% (79%), 87 trades, net R/trade +0.248 (0.207), CUSUM 1.5 / 54.8: OK. Full week 10-12..10-16 (information): +$31,813; daily at 20% size +$7.8k, +$3.4k, +$6.5k, +$4.6k, +$9.5k; fills 77%, 71%, 79%, 84%, 76%. FORWARD.md lists 22 leads.

## 8. BM1 added (LEAD, not counted; no purchases)
BM1 = NQ 15:20 ET fade of a >= 0.4 ADR20 move from the prior RTH close, flat 15:55 (ap_bm_1 cell 1 of bm1_co, reported as 'NQ 3'); refresh_cells.py BM1 reproduces the stored real_NQ.pkl series (max diff 0.0001, all stored days). Labelled LEAD / not counted; ERA-NEGATIVE (2013-22 Sharpe -1.48); post-hoc sign (opposite to the registered LETF direction); one observation with BJ2 (same late-day reversal). Frozen prediction (20% of pair risk, scale 8.97 x native, no shrink): $2,746/wk (CI $988..4,589), weekly 90% as in FORWARD.md, promotion N = 78 weeks. 10-14..10-16: +$1,760 (band -$11,574..+$20,669, in band); full week 10-12..10-16 +$5,802 (daily +$4,042, $0, +$1,934, $0, -$174). FORWARD.md lists 23 leads.

## 9. REGIME (tracked factor) and Q34 ES 1 (no purchases)
- REGIME: new FORWARD.md section 'Tracked factor' (not a trade, no promotion/kill rule): rolling-63-day gross Sharpe of the ALL intraday extension-fade factor (forward/series/REGIME_live.csv, refresh_regime.py now called by --refresh); flag when the weekly close is below -1.10 on two consecutive weeks; expectation positive gross (median since 2023-01 +0.93). 2026-10-16: +0.77; last six weekly closes +3.45, +3.37, +1.67, +1.26, +1.45, +0.77; no flag. (Median over the whole 2013+ history is +0.35; the +0.93 is the 2023+ window.)
- Q34 ES 1 (ES Globex-return reversal at the 09:30 ET open, hold 180 min, cell index 1 of b/q34_co): refresh_cells.py Q34 reproduces the stored real_ES.pkl series (max diff 0.0004, every stored day). LEAD, not counted; ERA-negative (pre-2023 Sharpe -0.63); replication 1 of 4. Frozen prediction (20% of pair risk, no shrink, N = 78 weeks): $2,316/wk (CI $543..4,039). 10-14..10-16: +$6,990 (band -$15,713..+$19,744, in band); full week 10-12..10-16 +$5,024 (daily -$1,616, -$350, -$12,242, +$6,643, +$12,589). FORWARD.md lists 24 leads + REGIME.

DONE EXTENSION_RESCORE
