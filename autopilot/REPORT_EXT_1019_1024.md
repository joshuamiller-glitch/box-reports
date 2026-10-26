# REPORT EXT 2026-10-19..10-24 - weekly L2 extension (week 202643) and per-trade live join reconciliation

Research only. Nothing in the execution server, chart or live strategy was touched. Databento key was read only inside the subprocess (`bash -ic`, exported by the user's profile), never printed or written. No deletions (every replaced file has a `.bak_*`/`_bak_*` copy).

## 1. Job A - data

### Purchase
| item | value |
|---|---|
| range check | `get_dataset_range('GLBX.MDP3')['end']` = 2026-10-24T19:41:49Z >= requested end 2026-10-24T00:00Z |
| request | mbp-10, `NQ.v.0 / ES.v.0 / RTY.v.0` continuous, 2026-10-19T00:00Z .. 2026-10-24T00:00Z, historical batch, split by day (previous segment ended 2026-10-19T00:00Z) |
| quote (metadata.get_cost, free) | NQ $21.1186, ES $11.3183, RTY $3.1548; total **$35.5917** (cap $40 per week; not exceeded) |
| logged in SPEND.json before submit | item `L2EXT_20261019-20261024` (status planned), backup `SPEND.json.bak_ext1019` |
| jobs | NQ GLBX-20261025-DSDKAWJBDU, ES GLBX-20261025-XNDJDGBCD5, RTY GLBX-20261025-3GRATGHGMJ (ids also in `/mnt/l2/l2vast/meta/ext_20261019_jobs.json`) |
| **cost actually charged** | **$35.5917** (batch charged at submit; the client has no billing endpoint and `list_jobs` shows `cost_usd=None`, so actual = quote, as for the earlier weeks; please compare with the portal usage page once) |
| SPEND.json | spent_usd 7,153.0267 -> **7,188.6184** of 8,000 (811.38 left); L2-extension running total 31.70 + 35.59 = **67.29** of 700 |
| anything else bought | **no** |

### Files and tables
* Raw: `/mnt/l2/l2vast/raw/{NQ,ES,RTY}/ext/GLBX-20261025-*/glbx-mdp3-20261019..20261023.mbp-10.dbn.zst` (NQ 3.4 GB, ES 1.5 GB, RTY 475 MB; no file for the closed Saturday). Contract NQZ6 (261401) / ESZ6 (10252) / RTYZ6 (42012034); no roll in the week.
* Reduced parts (never touching the old ones): `/mnt/l2/l2vast/tables/{NQ,ES,RTY}/{100ms,1s,1min,sweeps,vpin,tape,events_L13,qa}/2026-10__ext_20261019_20261023.parquet`; READY.md lines written (NQ 123,238,814 records, ES 66,048,405, RTY 18,410,067). Span 2026-10-19 00:00 -> 2026-10-23 21:01 UTC. The Sunday 10-18 evening session (22:00-24:00 UTC) lives in the catch-up part `2026-10__ext_20261012_20261018`; the pair is contiguous.
* Verification (`l2v_ext_verify.py`, results appended to `/mnt/l2/l2vast/meta/verify_ext_<SYM>.jsonl`): the paid references (ohlcv-1m, trades) for 10-19..10-23 do not exist on disk (they are the next purchase in the old runbook), so the script's bar/tick comparison is empty for this week. Substitute checks: (a) 1-min volume of the L2 table vs the trades-built series minute by minute (offset -1 min, table label = bar end): 99.99% of minutes equal, volume ratio 0.99998 for NQ, ES and RTY; (b) the L2-derived trade records are byte-equal to the PAID trades file on the previous week (2,059,770 NQ records 10-13..10-16: ts_event, price, size, side, flags, sequence 100% equal; ts_recv/ts_in_delta differ in 27%, unused); (c) anomalies (qa): NQ crossed 299, locked 1, trade-outside-book 28; ES crossed 523, trade-outside-book 1; RTY crossed 10, trade-outside-book 3; max gap 0.75 h (maintenance); no missing day.
* Tape end dates: before: series NQ/ES/RTY ended 2026-10-16 20:59 UTC (label 20261016), nt8sim tape and L2 parts to 10-18. After: **series_{NQ,ES,RTY}.npz end 2026-10-23 20:59 UTC (label 20261023)**, h2root bars2/ticks_all through 20261023, nt8sim tape (`ap_fwd_ab_sets.py --status`) "ends label day 20261023 (2026-10-23 20:59:00 UTC)", L2 parts through 2026-10-23 21:01 UTC.

### Library / series / rows extension (runbook steps 3-6, 15c-15h) - what was done and how
The old runbook buys trades + continuous ohlcv-1m (about $6/week) for steps 1-2. That was **not** authorised here ("do NOT purchase anything else"), so the NQ/ES/RTY trade ticks were **derived from the mbp-10 already paid for** (`outputs/autopilot/ext_1019/l2_to_trades.py`: `action=='T'` records of the front contract written into a trades-schema DBN; file `data/ext_20261024/<SYM>_trades_20261019_20261023.dbn.zst`, copied as `glbx-mdp3-20261018-20261023.trades.dbn.zst` into the existing trades job dirs with a `DERIVED_FROM_L2.txt` note). Front contract only (no NQH7/ESH7 deferred prints), harmless until the Dec roll; the paid file for 10-19..10-23 can replace it later (compare then).
| step | result |
|---|---|
| 3 `ap_ext_build.py` NQ/ES/RTY | old part identical on every field (old_part_identical true); +6,900 / 6,900 / 6,850 bars; no new roll; swapped into `data/databento/<SYM>/` (= `/mnt/l2/rootmoves/data_databento/<SYM>/`), backups `_bak_20261025` |
| 4 ticks2 + `ap_ext_h2.py 20261019` | `outputs/b10/ticks2/glbx-mdp3-20261018-20261023.npz` (2,557,787 prints); h2root bars2/ticks_all 20261019..20261023 built; no roll in window; `series_bars2_*_1.npz` moved to `h2root/_bak_ext_20261025` |
| 5 ins_env + rows | `ins_env.py` LAST/FULL_END/CEND 20261016 -> 20261023 (`.bak_pre_ext20261025`); `ROWS_corrected_engine.parquet` 13,184 -> 13,306 rows (first 13,184 field-identical; `.bak_pre_ext20261025`); `ROWS_bench3.parquet` 14,486 -> 14,620 (prefix identical; backups `pairP/_bak_pre_ext20261025/`); `bench3_run.py` refreshed PAIR_WINDOWED_BENCH3.npz and bench3.out (numbers in bench3.out) |
| 5b | 1-second caches `/mnt/l2/l2vast/pairP2/ds2_{SS,SC,K0,K1}.npy` extended (old prefix identical, backups `_bak_pre_ext20261025/`); without this the F1/firmlib chain raised IndexError once rows were extended |
| 6 `ap_ext_drv` | `drivers/min_{NQ,ES}_2023.parquet` +6,900 rows each (via `ap_ext_drv_1025.py`, `.bak_pre_ext20261025`) |
| 15e S130 | `s130_shadow.py 2026-10__ext_20261019_20261023` ran (10 pre-forward days 10-12..10-23, 0 counted; WAITING 0/26 forward weeks; first forward week W44) |
| 15f DS15 | `ap_shadow_ds15.py` via the chain: WAITING (1/26 forward weeks) |
| 15g Set A vs Set B | `ap_fwd_ab_sets.py`: W43 (info) DONE on the extended tape: A -134,500 (49 trades), B -86,278 (53), live -189,750 (49); W44..W47 PENDING (tape must reach 10-30..11-20) |
| 15h live-arrival daemon (pid 2963506, still running) | chain rerun twice with `ap_live_arrival.py --once`: a ab_sets, b ds15, c F1 (was rc=1 IndexError before 5b; now rc=0), d table3, e live_vs_replay_p9 (tz fixed), f forward register; FORWARD_REGISTER.md and LIVE_RECON.md regenerated |
**Not extended (blocked on purchases/approval, report to owners):** the 26 outrights' daily/1-min, BTC/ETH, VIX/COT downloads (steps 1, 7), continuous ohlcv-1m merge and i/c3/c7/b series (step 6 rest), the 24-lead `ap_forward_score.py --refresh`, the method-2 family matrices and PAPER-ALL league (steps 9, 11, 12), step 8's clean-process pair check. Warning for those owners: `ins_env.LAST/FULL_END/CEND` now say 20261023 while those series still end 2026-10-16; scripts mixing them will see a shorter series than the pair engine. If the ~$6 week buy (trades + ohlcv-1m + outrights) is approved it can be run now (START 2026-10-16T21:30Z for the library files).

## 2. Job B - per-trade live join reconciliation
Full detail, per-attempt table, CIs and unknowns: **`autopilot/JOIN_RECON.md` section 5** (backup of the old file `JOIN_RECON.md.bak_pre_ext1025`). Data: `autopilot/join_recon2/` (`summary.json`, `join_replay_per_attempt.csv`, `entry_slip_per_trade.csv`, `table_final.md`, code `jb_*.py`).
Key numbers (exact 95% CIs):
* Clock: CSV and trace are **Eastern** (UTC = ET + 4 h). `live_vs_replay_p9.py` (tz default) and `ap_forward_register.py` (CSV tz) were off by +1 h; fixed with backups (`*.bak_pre_et_fix_20261025`, `*.bak_pre_et_ext1025`), LIVE_RECON.md regenerated (`LIVE_RECON.md.bak_pre_et_fix_20261025`). The trace stamps run ahead of the exchange by 27 ms (82.3% exact fill-price match on 427 traced entry slices vs 27% uncorrected); strategy CreateOrder follows the tape print through the nominal stop by a median 104 ms.
* **Replay (exec_engine_l2, true trigger, queue rule) fills 11/17 = 0.647 [0.383, 0.858]; live 8/17 = 0.471 [0.230, 0.722]; all-history replay 0.78.** Trade-through rule 9/17 = 0.529 [0.278, 0.770].
* Per-attempt agreement 14/17 = 0.824 [0.566, 0.962]: **11/11 on the attempts with an order trace** [0.715, 1.000] (6 full, 1 partial, 4 none, same in replay); 3/6 on the untraced 10-20 attempts (rows 3, 5, 7: replay fills, live did not; no trace; exact McNemar p = 0.25).
* Conclusion on 0.47 vs 0.78: **mostly composition** (evening 18:00-22:00 mix: live 3/9, replay on the same triggers 5/9; earlier time-of-day reweighting predicted 0.65-0.69, which the replay on the actual triggers reproduces), failures are "price runs away" (zero volume at or through the limit in 3 s for 4 of 5 traced non-fills, adverse extension 4.5-11.0 pts). No engine-vs-live mechanism gap is detectable (exit px live minus replay -0.18 pt, SD 0.96, n = 11). A residual of up to ~30 points of per-attempt fill probability cannot be excluded at n = 17.
* Entry slip (F1 part): live **0.458 pt/lot = 1.83 ticks** [0.98, 2.69 ticks] vs the L2 mid at each slice's order time (ST+HM 14 lots, n = 29), replay of the same slices 0.529 pt (2.12 ticks); traced 21 trades 0.591 vs 0.560; ST 0.34, HM 0.63 pt. Versus the single mid at the trigger minute: -0.41 pt [-2.45, +1.63] (staggered over ~26 s, mostly drift, not a cost).
* The bypassed 10-21 04:34:01 ST event: the join, left resting, would have filled 14/14 at 29845.00 (~0.26 s after create); the Close at 29842.52 cost 2.48 pt = ~$694. Replay of the market Close brackets the live price (29842.29..29842.64 for 31-60 ms arrival).
* **For the user - missing CSV trade:** ST Buy 14, entry 2026-10-21 04:00:00 ET (avg 29905.73), flattened 04:34:01.6 at 29842.52: -63.21 pt, **about -$17.7k (-$17,699 gross, -$17,767 after fees)**; not in `StratTrades_DualStrat2_<acct>.csv`, so W43 live net (-189,750 here; FORWARD_REGISTER) excludes it. Nothing else done about it.
* Unknown: why rows 3/5/7 failed live (no 10-20 trace; row 3 contradicts the 60-pt trigger rule); true queue position/hidden size; join-path latency sub-ms; the strategy's quote source for the limit (equals the touch at create-27 ms in 4/11).
FORWARD_REGISTER.md join-rate/slip rows now show the replay-on-live-triggers row and the entry-slip numbers (via `ap_forward_register.py`, reads `join_recon2/summary.json`); `f1_live.py` writes them into `f1_live.json`.

## 3. Verification checklist
* Tape end dates: series NQ/ES/RTY 2026-10-23 20:59 UTC, nt8sim tape label 20261023, L2 parts 2026-10-23 21:01 UTC, ROWS to 2026-10-23 14:05 ET.
* Old parts identical (series x3, rows x2, ds2 caches, ticks); cost = $35.5917 in SPEND.json; spent 7,188.62 / 8,000.
* Corepool: Job B ran with 4 single-slot workers (`corepool.py run 1 1`; about 13 GB each), no PRED_BLOCK.
* Files changed with backups: see the tables above; nothing deleted.

DONE EXT 1019_1024 (Job A data + library for NQ/ES/RTY; Job B reconciliation). OPEN: outrights/VIX/COT/ohlcv-1m week buy (~$6, needs approval) and refresh of the 24-lead scorer.

## Addendum 2026-10-26 (main's order: ES/RTY tape, Saturday prep)
* ES/RTY (and NQ) 1-min series were already extended to 2026-10-23 20:59 UTC in Job A (verified; FORWARD_REGISTER line 24 reads "Tape ends 2026-10-23"). Added now, derived from the paid mbp-10 (no purchase): `data/autopilot/ohlcv1m/{ES,NQ,RTY}_2026.dbn.zst` merged to 2026-10-23 20:59 (old part identical; backups `ohlcv1m/_bak_20261025/`); `i/m1_,x_{NQ,ES,RTY}.npz`, `c3/h23/series_{NQ,ES}_long.npz`, `b/series_RTY.npz` rebuilt (old part identical, backups `_bak_pre_ext20261025`); forward caches `cache/i`, `cache/daily_ES.pkl` moved to `cache/_bak_pre_ext20261025`. Identity check of the ohlcv derivation on the prior week (ES): 4,020/4,020 bars matched, high/low 100%, open 99.95%, close 99.93%, volume 99.6% of bars, total volume ratio 1.0000 (16 bars = trades straddling a minute boundary). Code `ext_1019/l2_to_ohlcv1m.py`, `merge_ohlcv_1025.py`.
* Saturday 2026-10-31 run is written into `RUNBOOK_WEEKLY_EXTENSION.md` (ADDENDUM, backup `.bak_pre_w202644`) with exact commands; generic driver `ext_1019/ext_week_derive.py`. Not part of it: the ~$6 library buy.
