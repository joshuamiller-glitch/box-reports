# REPORT EXTENSION_2026-10-17 - weekly rolling-data extension (week ending Fri 2026-10-16)
**Verdict: DONE. Data, pair H2 and the forward test now end 2026-10-16. FORWARD.md has live-week rows (stub week 2026-W42, 3 post-freeze days, f = 0.6). No break: every lead is inside its weekly 90% interval; FVG trade-level flags OK.** Pair clean/H1 weekly Sharpe still 1.46/2.83 (clean process); H2 on the longer span 2.48, all-in 1.90.

## 1. What was on disk, quotes, purchase
- Before: NQ/ES/RTY 1-min series (trades-built, data/databento/<SYM>/series_<SYM>.npz) ended 2026-10-12 23:59 UTC (session label 20261013 was PARTIAL, 2 h); NQ/ES trades to 2026-10-12; yearly continuous ohlcv-1m (data/autopilot/ohlcv1m) to 2026-10-13 23:59 UTC; pair H2 end 2026-10-13 (rows ROWS_corrected_engine.parquet to 2026-10-12 19:36 ET, last day partial).
- What the pair engine consumes: the B8/nt8sim account model on `outputs/b10/h2root` (1-second bars and 100 ms-throttled print stream built from Databento TRADES prints), NOT ohlcv-1s and not ohlcv-1m. So the purchase is trades (NQ for the engine; NQ+ES for PERS30 flow and the FVG tick replay; RTY for completeness of the trades-built series) plus continuous ohlcv-1m for the lead scripts.
- Quotes (metadata.get_cost, 2026-10-13..2026-10-17): NQ trades $2.584, ES trades $2.556, RTY trades $0.543, NQ/ES/RTY ohlcv-1m (parent) $0.026/$0.025/$0.021, ohlcv-1s NQ $0.868 / ES $0.773 / RTY $0.439 (NOT bought: not consumed), 26 outrights + NKD continuous .v.0 ohlcv-1m 2026-10-14..10-17 $0.338. Total bought $6.02 (cap $120). Logged in SPEND.json (family EXTENSION_2026-10-17) BEFORE buying; spent_usd 6,932.13 -> 6,938.15 of $8,000. Databento releases CME data ~8 h after the event, so the buy waited until the Friday close + 8 h (data through 2026-10-16T21:30 UTC, i.e. the complete Friday session).
- Raw files: data/ext_20261017/.

## 2. Files extended (all old parts verified identical before swap; backups kept)
| file | action | check / backup |
|---|---|---|
| data/databento/{NQ,ES,RTY}/trades/GLBX*/glbx-mdp3-20261013-20261016.trades.dbn.zst | new file added in the existing job dirs | - |
| data/databento/{NQ,ES,RTY}/{series_*.npz, contract_minutes_*.parquet, contract_of_day_*.csv, roll_gaps_*.csv} | incremental rebuild (code/census/night_ins/ap_ext_build.py = b7_build post-parse logic, new file parsed only) | old 1.307M/1.307M/1.271M bars identical on every field; +5,400/5,400/5,358 bars; last label 20261016; no new roll; backups data/databento/<SYM>/_bak_20261017/ |
| outputs/b10/ticks2/glbx-mdp3-20261013-20261016.npz | b10_tickdbn2.py | - |
| outputs/b10/h2root/{bars2,ticks_all}/20261013..20261016.npz | ap_ext_h2.py (b10_h2build logic); 20261013 rebuilt whole (was partial); regression: rebuilt 20261008/09/12 byte-equal to the existing files | backup of replaced day-13 files and series caches in h2root/_bak_ext_20261017; series_bars2_{et,utc4}_1.npz caches regenerated on first use |
| code/census/night_ins/ins_env.py | LAST / FULL_END / CEND 20261013 -> 20261016 (H2 end) | ins_env.py.bak_pre_ext20261017 |
| outputs/h2/ROWS_corrected_engine.parquet | regenerated with the unchanged er_gen logic (nt8sim account model) | 13,184 rows (+95); the 13,086 rows before 2026-10-12 17:00 ET are field-identical to the old file; ROWS_corrected_engine.parquet.bak_pre_ext20261017 |
| outputs/autopilot/drivers/min_{NQ,ES}_2023.parquet (PERS30 flow minutes) | new-file reduction appended (ap_ext_drv.py) | row counts equal series bars; .bak_pre_ext20261017 |
| data/autopilot/ohlcv1m/<27 syms>_2026.dbn.zst | valid DBN merge (ap_ext_dbn.py: header + records + merged symbol mappings); verified equal to old+new frames | _bak_20261017/ |
| outputs/autopilot/i/{m1,x}_<26 syms>.npz, c3/h23/series_{NQ,ES}_long.npz, c7/p1/series_{6E,6J,CL,GC,ZB,ZN}.npz, b/series_<19 syms>.npz | rebuilt in staging with the original builder logic, old part identical, swapped | _bak_pre_ext20261017 dirs. RB: a NEW roll on 2026-10-14 shifts the whole back-adjustment by a constant -0.1121; raw prices equal; swapped deliberately |
| data/gap/vix/{VIX,VIX3M,VVIX,VIX9D,VIX6M,SKEW}.csv, data/gap/cot/{fut_fin,com_disagg,deacot}2026.zip | CBOE / CFTC re-download (adds 2026-10-16 VIX family, COT through report date 2026-10-13); old rows identical | _bak_pre_ext20261017 |
| forward/refresh_h11b.py, refresh_pers30.py | the 'H2 == 2.30' assertion replaced by a clean/H1 (1.46/2.83) assertion (H2 now spans to 10-16) | .bak_pre_ext20261017 |
| code/census/night_ins/ap_fv_live.py | coverage rule: a trades file whose last print is at/after 16:50 ET counts that day as complete (was 'back off one day' always; the weekly file ends at the Friday close). No FVG/ICT definition touched | .bak_pre_ext20261017 |
| forward/cache/{i,daily_ES.pkl} | moved to cache/_bak_pre_ext20261017 so the private caches rebuild | - |
Not extended (not in the purchase list): BTC/ETH 1-min (data/t4), VX curve (B10 vx_1d), OPRA/options, mbp-10 (NQ/ES/RTY depth), MBO.

## 3. Pair baseline in a CLEAN process (b10_core never imported; B.Cfg(wk_floor=8, wk_loss_pb=None), 8/8, 1 tick/side + $34.88)
| span | weekly Sharpe | net | maxDD | worst week | weeks | CVaR5 | CVaR10 | Sortino | MAR |
|---|---|---|---|---|---|---|---|---|---|
| clean 2023-08..2025-07 | **1.460** | $1,329,959 | $280,110 | -$81,874 | 105 | -$78,736 | -$78,009 | 2.78 | 4.75 |
| H1 2025-08..2026-02-06 | **2.828** | $593,797 | $151,713 | -$78,287 | 28 | -$77,610 | -$66,030 | 6.09 | 3.91 |
| H2 2026-02-07..2026-10-16 (extended) | **2.484** | $819,748 | $217,425 | -$82,524 | 36 | -$81,089 | -$79,185 | 5.08 | 3.77 |
| all-in 2023-08..2026-10-16 | **1.897** | $2,743,504 | $280,110 | -$82,524 | 168 | -$79,220 | -$78,243 | 3.71 | 9.79 |
- B.Cfg() (default): 1.350 / 1.653 / 2.458 / 1.655. Same H2 span as before (to 10-13) on the new rows: 2.39 (the old 2.30 had a 2-hour 10-13 label day; the complete day is +$10,211).
- Pair daily P&L: 10-12 -$3,344; 10-13 +$10,211; 10-14 +$7,860; 10-15 +$16,436; 10-16 +$6,881. ISO week 2026-W42 (10-12..10-16) **+$38,045**; the three post-freeze days (10-14..16) +$31,177. Preceding weeks W40 -$15,630, W41 -$54,750 (so the last three weeks net -$32k).
- Executability/margin unchanged (live system untouched).

## 4. Forward test (python3 outputs/autopilot/forward/ap_forward_score.py --refresh, then the two refresh scripts and the scorer re-run after the assertion/coverage patches; outputs/FORWARD.md)
All 8 refresh scripts ran (WT10, K4V2, H11B, PERS30, ESDIP, FVG P1/E1/IMP3). FORWARD.md rows now show 0.6 live weeks (stub W42 = 10-14..16). Weekly 90% intervals from PRED.json/PRED_FVG.json (frozen; unchanged).
| lead | new-week P&L (20% sleeve / live pair size) | weekly 90% interval | in band | note |
|---|---|---|---|---|
| WT-10 | -$396 | -$9,983 .. +$12,274 | yes | |
| K4v2 | $0 realised | -$1,041 .. +$7,084 | yes | a signal: ES p=0.596 >= 0.58 on 10-16 (NQ 0.564, RTY 0.578, YM 0.566 below) -> ES long entered 16:16 Fri, exits Mon 10-19: scores next week. VIX/COT refreshed to 10-16 / 10-13 first |
| H11-B halt | $0 | -$882 .. +$15,814 | yes | no 2-stops-in-10-min day |
| PERS30 | +$62,520 | -$68,556 .. +$76,649 | yes (upper half) | uplift = modified pair - live pair, 3 days |
| ES dip-buy | $0, 0 trades | -$2,592 .. +$25,387 | yes | no RSI(2)<5 signal; trade rule counts closed trades (0 of 21) |
| FVG P1 | -$3,101 | -$8,123 .. +$20,894 | yes | 88 orders, fill 72% (pred 73%), 34 trades, -0.062 R/trade (pred +0.079), CUSUM 3.96 / h 82.96 OK |
| FVG E1 | +$10,218 | -$6,573 .. +$24,609 | yes | 276 orders, fill 74% (73%), 111 trades, +0.118 R (pred +0.078), CUSUM 10.2 / 82.3 OK |
| FVG IMP3 | +$16,956 | -$4,891 .. +$28,933 | yes | 146 orders, fill 75% (69%), 48 trades, +0.217 R (pred +0.120), CUSUM 2.09 / 72.0 OK |
Cumulative actual vs cumulative band: all WITHIN BAND; status NOT PROMOTED (needs 13-78 weeks); no KILL WATCH. 0.6 weeks carries essentially no power (z about 0.1 to 1.5).

## 5. Other LEADs (definitions untouched)
| lead | result for the new week | status |
|---|---|---|
| GC ST-flip fade 108-cell ensemble (L93), 20% sleeve at pair-vol-matched size | refreshed with the extended GC series and the unchanged ap_l_cure dump logic (old part identical): 10-12 -$416, 10-13 -$2,908, 10-14 +$10,916, 10-15 +$883, 10-16 +$3,828; post-freeze 3 days +$15,626; full W42 +$12,302 | historical mean +$3,271/wk (block-bootstrap CI of the mean +$1,402 .. +$5,423), weekly 5-95% -$14,616 .. +$32,765: inside |
| K4 family (K4v2; RX5/RW5/RW12P are variants) | see K4v2 above: flat, one open ES signal | RX5/RW5/RW12P have no refresh function (PRED_EXTRA.json only); not rescored |
| ES dip-buy | no trade | scored in FORWARD.md |
| J4 quad-witching close->close | no event (next 2026-12-18; 10-16 is a plain monthly expiry) | 0 by construction |
| Weekend-gap fade (Z3/W6/T1b), Q5/Q5ENS (monthly rebalance), N3 (needs VX curve) | no refresh function; library series end 2026-10-13/14; N3 needs the VX F1/F2 files (not bought); Q5 holds a monthly position | not rescored |
| BTC 10-min WT | crypto 1-min files (data/t4) not part of the GLBX purchase | not rescored |
| MBO seven | series end 2026-02-06 (no MBO beyond) | not applicable |

## 6. Breaks / caveats
- No lead outside its interval; no FVG stop-rule trigger.
- Process breaks fixed: (a) the 'H2 == 2.30' assertions in refresh_h11b/pers30 (would be true only on the old span); (b) the FVG coverage rule backed off one day even when the file ended at the Friday close; (c) hard-coded END/LAST 20261013 constants remain in ~60 older family scripts (ap_i_common.END, SPANS lists, etc.): they still evaluate H2 to 10-13 unless edited; ins_env (pair engine), ins_metrics (H2 to 20261231) and the refresh scripts are updated.
- Freeze-day caveat: the 2026-10-13 label day was frozen when only its first 2 hours existed; the forward test scores only labels after 10-13 (as pre-registered) and the pair/L93 W42 numbers above include 10-12/10-13 for information.
- Peak-week context: VIX +21% on Fri 10-16 (16.46 -> 19.99); the pair made +$6.9k that day.

DONE EXTENSION
