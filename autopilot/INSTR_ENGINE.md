# INSTR_ENGINE - generic-instrument version of the live book engine (BASE-4, T-INSTR / P2, 2026-11-03T20:04Z); research only, nothing here is a result about any instrument's edge
Code `l2vast/ds3/code/instr/instr_engine.py` (python3 -I; imports `bars_eng/be_lib` and `decay/sd_state` UNCHANGED for the signal recursions; tick, $/pt and commission from `te2_lib.INSTR` so the engine and ZL-2's MultiHarness agree). Tie-outs: `ds3_base4/instr_nq_test.py`, `instr_es_proto.py`, `instr_es_recon.py`, `instr_es_worked.py`.
## 1. Interface
```
import sys; sys.path.insert(0,'l2vast/ds3/code/instr'); import instr_engine as IE
B  = IE.load_bars('ES')                         # 1-min back-adjusted continuous bars (cache_te2 <SYM>_adj.npz | instr_rf/<SYM>_1m.npz | NQ aux_bar), label days <= 20260206 (UNTOUCHED never read)
tr = IE.run_book('ES', 'K7', start_ld=20230401, end_ld=20260206, fill='live', path='1m', bracket='z1', cost_basis='z1', B=B)
IE.harness_trades(tr)                           # -> ZL-2 MultiHarness signal list: instrument, sec (= 1-min bar-close boundary), side, stop_pts, tgt_pts, risk_usd, session, tag
IE.daily(tr, col='live', nq_lots=2)             # label-day $ at the NQ-equal $ risk (lots_equiv = NQ lots x 1,200 / (stop pts x $/pt))
```
* **Books** (`IE.BOOKS`): K7 = KB (Keltner 3-min), P7 = PE (pullback to EMA20 in the 5-min Supertrend regime), U7 = SM (10-min Supertrend flip), H7 = HM (HMA-vs-VWAP cross), M7 = MV (momentum vote), S7 = ST, W7 = WT (bracket 0.75 x), A7 = PB7 Asia session only (no busy rule: pass busy=False), O7 = PB restricted to NY-AM (ASSUMPTION: the O7 signal code is not in be_lib; confirm the mapping with the book owner). Signals use the engines' NATIVE frames (variant G: KB 3m, SM 10m, PE regime 5m, PB 10m/5m).
* **Excluded (need NQ-only data, not portable):** the L2SE 70/30 split (L2 veto v4; a single market entry replaces it), TH-L2 cuts and every other L2 exit, the PE 45-s tape-pattern confirmation, zone layers (lines from NQ files), the sizer inputs that need tape features. The ER(20) ladder (5-min closes) and the live lot order are price-only and can be added by the slice from `d7base/lots_ts2.py` logic; not included here.
* **Fill model.** `fill='live'` (user, 2026-11-04): signal at the 1-min close, first fill ~1 s later = close of the decision second + 1 tick adverse (the be_lib MEASURED convention, unit-tested on NQ); stop / target are RESTING orders anchored on the fill price and fill at their level (a target needs the 2nd bar; stop wins a same-bar tie on bar paths); exit at the flat time (`Spec.flat_et`, default 16:55 ET of the label day) at the bar/second close; busy rule one position per book (market books A7: busy=False); entries 18:00-15:15 ET (`Spec.entry_start_et/entry_end_et`); 17:00-18:00 ET break holds for all instruments. `fill='library'` = the NQ library convention, entry price = the OPEN of the next 1-min bar, no tick (verified below). `path='1m'` scans the 1-min bars (non-NQ today); `path='1s'` = the NQ 1-s path (G2 arrays). A tick-built 1-s path for ES etc. does not exist yet (databento 0.86 is installed; ES trades are 6.2 GB dbn.zst; NKD/6J 1-s files are on disk): the loader contract is `Path(SS, SH, SL, SC, res)`.
* **Bracket scaling (Z1 INSTR_SCALING.md).** `bracket='z1'` (default): stop = target = max(2 ticks, nearest tick of 60 pt x f_i), f_i = median ATR14(5m) ratio to NQ (ES .1948 -> 11.75 pt, RTY .109 -> 6.5, YM 1.253 -> 75, ZN .002004 -> 0.125 (8 ticks), ZB -> 0.21875 (7 ticks), 6E -> 0.00125, 6J -> 1.0e-5, GC .147 -> 8.8, CL .007201 -> 0.43, NKD 2.047 -> 125, MBT 8.36 -> 500). Sensitivities: `bracket='z1_warm'` (warm-up ratio 2022-06..2023-03), `'z1_bps'` (bps of price), `'scaled'` (median daily-range ratio), `'nq'` (60/60 as is), or `(sd, td)`.
* **Costs** (NQ-measured defaults, LABELLED): market exit 0.80 pt, stop slip 2.45 pt worse than nominal, targets nominal, fee 0.242 pt = $4.84; library bases stop 1.01 / time 0.995. `cost_basis='z1'` (BASE) = max(NQ pts x f_i, 1 tick market / 2 ticks stop; thin 6J NKD MBT 2/3) and the Z1 fee per instrument; `'z1_stress'` = 2x slippage and 2x fee; `'ticks'` = the NQ-literal 3.2 / 9.8 ticks on every instrument (harsh bound); `'bps'` = same fraction of price. Output columns `lib` (library-style bases) and `live` (stop slip / market exit / fee), both per contract in points, `R = live / stop`.
* **Lots at equal $ risk:** 1 NQ lot = $1,200 to the 60-pt stop; `nq_equal_lots`, `harness_trades` (risk_usd = NQ lots x 1,200) and `daily`. The Z1 participation cap (1.7% of the median 5-min volume per entry) is NOT applied here; apply it to the lots you feed the harness.
* **Data:** `IE.SPECS[sym]` = tick, $/pt, commission RT (te2_lib), flat/entry windows; loaders: `cache_te2/<SYM>_adj.npz` (ES RTY YM GC CL NKD MBT ...; BTC raw), `instr_rf/<SYM>_1m.npz` (ZN ZB 6E 6J, back-adjusted), NQ = aux_bar. Label day rolls at 18:00 ET; bars up to 20260206 only.
## 2. Tie-out on NQ against the library trade lists (d7 library `t`, the rows under the ts2 base), 2023-04-01..2026-02-06, bracket 60/60 from the fill, 1-s path, `fill='library'`
| book | library trades | engine trades | library entries reproduced | exit type agrees | exit second agrees | entry price == library E |
|---|---|---|---|---|---|---|
| KB | 5500 | 5566 | 5500 (100.00%) | 100.00% | 99.98% | 100.0% |
| PE | 5361 | 5435 | 5361 (100.00%) | 100.00% | 100.00% | 100.0% |
| SM | 1708 | 1719 | 1708 (100.00%) | 100.00% | 100.00% | 100.0% |
| HM | 4156 | 4221 | 4145 (99.74%) | 100.00% | 99.98% | 100.0% |
| MV | 5167 | 5259 | 5127 (99.23%) | 100.00% | 100.00% | 100.0% |
| ST | 5390 | 5464 | 5386 (99.93%) | 100.00% | 100.00% | 100.0% |
| WT | 7685 | 7813 | 7684 (99.99%) | 99.99% | 99.99% | 100.0% |
| PB | 17031 | 3425 | 3023 (17.75%) | 99.67% | 73.30% | 18.8% |

Reading: the NQ library's entry price E is the open of the next 1-min bar and its entry second is the first print second at/after the bar-close boundary (this is what `fill='library'` does); with that, every book reproduces 99.2-100% of the library's trades, with the SAME entry price (100% equal to the cent) and the same exit type (100%) and exit second (99.98-100%). It does not reach 100% of rows for HM (11 of 4,156 library rows missing), MV (40 of 5,167), ST (4), WT (1): signal-state differences at a handful of bars; the engine also takes 1-2% MORE trades than the library (KB 5,566 vs 5,500, PE 5,435 vs 5,361) - signals the library did not take (its older entry-window / path-validity rules, not reconstructed). So the tie-out is 0.0000 on the matched entries and exits (price, type, second) and 99.2-100% on the trade set, NOT 100%. A7 (PB7, 17,031 library rows): with busy=False the engine reproduces the library COUNT (17,031) but 13,946 (82%) of the entry keys; the rest are entry seconds that differ (market-book fill timing not reconstructed). `fill='live'` (close of the decision second + 1 tick) differs from the library entry by 0-1 tick by construction: the exit second then agrees on ~70% of trades and the exit type on 99.2-99.6%.
## 3. ES prototype (research screen only; first run of the pipeline, no claim about edge)
ES: 1,304,573 1-min bars 2022-06..2026-02-06; Z1 bracket 11.75 pt, BASE costs 1 tick market / 2 ticks stop, fee $4.84; fill live, path 1m. Mean net points per contract by book (all sessions), `bracket='z1'` then `'nq'` (60/60 unscaled):
| bracket | book | trades | stop=target pts | mean net pts / contract | mean R | win rate | $ per active day, 1 ES lot |
|---|---|---|---|---|---|---|---|
| z1 | K7 | 6058 | 11.75 | -0.438 | -0.0373 | 0.494 | -179.9 |
| z1 | P7 | 5868 | 11.75 | -0.468 | -0.0398 | 0.493 | -186.2 |
| z1 | U7 | 1767 | 11.75 | -0.284 | -0.0241 | 0.498 | -34.7 |
| z1 | H7 | 4459 | 11.75 | -0.128 | -0.0109 | 0.506 | -38.8 |
| z1 | M7 | 5643 | 11.75 | -0.295 | -0.0251 | 0.5 | -113.0 |
| z1 | S7 | 5882 | 11.75 | -0.518 | -0.0441 | 0.491 | -206.7 |
| z1 | W7 | 8202 | 8.81 | -0.47 | -0.0534 | 0.559 | -261.8 |
| z1 | A7 | 3551 | 11.75 | -0.467 | -0.0397 | 0.493 | -160.8 |
| z1 | O7 | 977 | 11.75 | -0.763 | -0.065 | 0.484 | -61.4 |
| nq | K7 | 1007 | 60.0 | 0.593 | 0.0099 | 0.489 | 40.5 |
| nq | P7 | 1011 | 60.0 | -1.378 | -0.023 | 0.494 | -94.5 |
| nq | U7 | 785 | 60.0 | 2.195 | 0.0366 | 0.507 | 119.2 |
| nq | H7 | 979 | 60.0 | -2.095 | -0.0349 | 0.467 | -139.2 |
| nq | M7 | 1018 | 60.0 | -0.143 | -0.0024 | 0.481 | -9.9 |
| nq | S7 | 1012 | 60.0 | -1.644 | -0.0274 | 0.471 | -112.9 |
| nq | W7 | 1427 | 45.0 | -0.194 | -0.0043 | 0.521 | -18.8 |
| nq | A7 | 3551 | 60.0 | -0.929 | -0.0155 | 0.47 | -320.1 |
| nq | O7 | 82 | 60.0 | -0.286 | -0.0048 | 0.537 | -14.6 |
**Worked rows (independent python scan of the ES 1-min bars, no engine code shared):**
- ES K7 label 20240808 long london: signal bar closes 2024-08-08 02:21 ET at 4865.50; fill 4865.75 (close + 1 tick adverse); stop 4854.00 / target 4877.50 (11.75 pt = Z1 f 0.1948 x 60); exit type 0 (0 stop 1 target 2 flat) at bar 03:03 level 4854.00; gross -11.75 pt; independent python scan: fill 4865.75, exit 0 at 4854.00, gross -11.75 -> **MATCH**
- ES K7 label 20240806 short london: signal bar closes 2024-08-06 05:33 ET at 4870.25; fill 4870.00 (close + 1 tick adverse); stop 4881.75 / target 4858.25 (11.75 pt = Z1 f 0.1948 x 60); exit type 0 (0 stop 1 target 2 flat) at bar 06:29 level 4881.75; gross -11.75 pt; independent python scan: fill 4870.00, exit 0 at 4881.75, gross -11.75 -> **MATCH**
- ES K7 label 20240807 long asia: signal bar closes 2024-08-06 20:24 ET at 4889.75; fill 4890.00 (close + 1 tick adverse); stop 4878.25 / target 4901.75 (11.75 pt = Z1 f 0.1948 x 60); exit type 1 (0 stop 1 target 2 flat) at bar 21:22 level 4901.75; gross +11.75 pt; independent python scan: fill 4890.00, exit 1 at 4901.75, gross +11.75 -> **MATCH**
- ES K7 label 20240814 short nyam: signal bar closes 2024-08-14 09:42 ET at 5091.00; fill 5090.75 (close + 1 tick adverse); stop 5102.50 / target 5079.00 (11.75 pt = Z1 f 0.1948 x 60); exit type 1 (0 stop 1 target 2 flat) at bar 10:12 level 5079.00; gross +11.75 pt; independent python scan: fill 5090.75, exit 1 at 5079.00, gross +11.75 -> **MATCH**
- ES K7 label 20231222 long nypm: signal bar closes 2023-12-22 14:48 ET at 4568.75; fill 4569.00 (close + 1 tick adverse); stop 4557.25 / target 4580.75 (11.75 pt = Z1 f 0.1948 x 60); exit type 2 (0 stop 1 target 2 flat) at bar 16:54 level 4563.50; gross -5.50 pt; independent python scan: fill 4569.00, exit 2 at 4563.50, gross -5.50 -> **MATCH**
- ALL worked rows MATCH

## 4. Reconciliation with ZL-2's MultiHarness (ES K7, cost_basis z1, 6,058 engine trades fed through `IE.harness_trades` -> `MultiHarness.simulate`)
5,863 of 6,058 signals survive the harness (its own no-overlap rule uses minute-resolution exits); on those, exit type agrees on 99.0%, net points per trade are identical on 96.2% (|diff| < 0.01), the harness is 0.114 pt lower on average (mean net -0.494 vs -0.380 pt per contract on the surviving rows; median difference 0). Cause: the harness first fill is the OPEN of the bar that starts at B plus m ticks (ES 1) and fills a gapped stop at the bar open; this engine fills at the close of the decision second + 1 tick and a stop at its level. The two models are close (0.1 pt = 1% of the 11.75 pt stop); use MultiHarness for the verdicts and this engine for screening, signal lists and the NQ tie-out.
## 5. Which agent uses what
Z2 ES / RTY / YM; ZL-1 ZN / ZB / 6E / 6J (reads `instr_rf`); S4b GC / CL / BTC / MBT / NKD (reads `cache_te2`; crypto: set `Spec.flat_et/entry_*` yourself); Z1 scaling = section 1; ZL-2 harness = `harness_trades`. Register the number of books tested with `multi_harness.ntested_register`.
## 6. Known limits / open items
1-min exit path off NQ (stop first in a bar: conservative); no L2/tape books; O7 mapping assumed; 1-s ES path and tick builders not built; participation cap not applied; the engine sees NQ-library entry rules only approximately (+1-2% extra trades).

## 7. SECOND PASS (BASE-4, 2026-11-03T20:26Z): real 1-s paths, A7 solved, cross-checks, caps, sensitivities (supersedes the A7 statement and the table of section 2)
### 7.1 NQ tie-out, final (fill='library'; key = library `k_in` + side; research window 2023-04-01..2026-02-06, the end of the NQ aux bars)
| library book | engine book | library trades | engine trades | library trades reproduced (key k_in+side) | share | library missing | engine extra | exit type agrees | exit second agrees | entry price == library E | exit level == library exit_px |
|---|---|---|---|---|---|---|---|---|---|---|---|
| KB | K7 | 5500 | 5566 | 5500 | 100.00% | 0 | 66 | 100.00% | 99.98% | 100.0% | 100.0% |
| PE | P7 | 5361 | 5435 | 5361 | 100.00% | 0 | 74 | 100.00% | 100.00% | 100.0% | 100.0% |
| SM | U7 | 1708 | 1719 | 1708 | 100.00% | 0 | 11 | 100.00% | 100.00% | 100.0% | 100.0% |
| HM | H7 | 4156 | 4221 | 4145 | 99.74% | 11 | 76 | 100.00% | 99.98% | 100.0% | 100.0% |
| MV | M7 | 5167 | 5259 | 5127 | 99.23% | 40 | 132 | 100.00% | 100.00% | 100.0% | 100.0% |
| ST | S7 | 5390 | 5464 | 5386 | 99.93% | 4 | 78 | 100.00% | 100.00% | 100.0% | 100.0% |
| WT | W7 | 7685 | 7813 | 7684 | 99.99% | 1 | 129 | 99.99% | 99.99% | 100.0% | 100.0% |
| PB | A7 | 17031 | 3557 | 3557 | 20.89% | 13474 | 0 | 100.00% | 100.00% | 100.0% | 0.0% |

* A7 = PB7 Asia: the 17,031-row library `PB` book is the PB7 market book in ALL sessions; its entry price is the close of the last print second before the entry second + 1 tick adverse (= `fill='live'`) with NO busy rule: PB7 (all sessions) reproduces 17,031 of 17,031 entries, exit type 100%, exit second 100%, entry price 100%; the earlier 82% was a keying artefact (the library `s_in` of this book is the nominal bar boundary, `k_in` is the first print). The A7 row above is the Asia subset (3,557 library rows, all reproduced). `exit_px == lv` is 0% for A7 only because the library stores the exit level of this book in a different cost convention (E and types match 100%).
* The other books: 99.2-100% of library trades, E equal to the cent, exit type 100%; the engine also takes 1-2% extra trades the library did not (older entry-window / path-validity rules, not reconstructed); a few library rows missing (H7 11, M7 40, S7 4, W7 1). NQ ends 2026-02-06 because the aux bars do (the library path to 2026-10-30 is in another price frame).
### 7.2 Real 1-second paths from the tick trades (`instr_1s.py`, arrays in /mnt/l2/l2vast/instr_1s/)
ES, RTY, ZN, GC, CL built from the monthly Databento trade files (2023-02..2026-10-30; front contract = the iid of the engine's 1-min series, additive back-adjustment of that minute, ticks bucketed by ts_event second; seconds WITH a print only): ES 41.4M seconds, RTY 24.2M, GC 27.6M, CL 24.4M, ZN 12.7M. YM: no ticks on disk. Use `IE.path_1s(sym)` + `run_book(..., path='1s', P=...)`. Validation: the same builder on NQ April 2023 reproduces the library G2 second path: 914,540 common seconds of 914,622, SC equal on 99.79%, SH 99.92%, SL 99.92% after removing a constant frame offset (cache_te2 adj frame vs the G2 frame); within one tick on 99.93-99.98%.
**ES: 1-min path (stop first in a bar) vs the real 1-s path**, 2023-04-01..2026-10-16, fill live, Z1 bracket 11.75 pt, BASE costs:
| book | trades 1-min path | trades 1-s path | common signals | exit type differs | of which stop (1-min) -> target (1-s) | mean net pts/contract 1-min | 1-s | mean diff on common (1s-1m) |
|---|---|---|---|---|---|---|---|---|
| K7 | 8392 | 8395 | 8392 | 0.18% | 0.18% | -0.536 | -0.495 | +0.043 |
| P7 | 8103 | 8104 | 8103 | 0.14% | 0.14% | -0.522 | -0.488 | +0.033 |
| U7 | 2339 | 2339 | 2339 | 0.13% | 0.13% | -0.255 | -0.225 | +0.031 |
| H7 | 6147 | 6148 | 6146 | 0.15% | 0.15% | -0.355 | -0.319 | +0.035 |
| M7 | 7775 | 7776 | 7775 | 0.13% | 0.13% | -0.391 | -0.358 | +0.031 |
| S7 | 8144 | 8146 | 8144 | 0.15% | 0.15% | -0.613 | -0.578 | +0.035 |
| W7 | 11269 | 11276 | 11266 | 0.31% | 0.31% | -0.547 | -0.497 | +0.049 |
| A7 | 5036 | 5036 | 5036 | 0.06% | 0.06% | -0.420 | -0.405 | +0.014 |

Reading: the 1-min path is conservative by 0.03-0.05 pt net per contract (0.3-0.4% of the 11.75 pt stop); 0.06-0.31% of trades change exit type, always stop (1-min) -> target (1-s). **Slice timing on the real path** (`IE.slice_entries`): ES K7 at the equal-risk 4.1 lots, one lot every 2 s: 4.08 of 4.09 lots fill before the exit, average drift of the filled lots -0.03 ticks (p90 +2.3 ticks); an 11-lot order p90 +3.8 ticks.
### 7.3 Cross-checks of the slice owners' independent ports against the engine
**ZL-1 (`instr_rf/irf_core.py`: K7 U7 H7 M7 P7 A7 on 1-min bars), same bars on NQ and ES, signals 2023-04..2026-02-06** ('share of engine' lower than 100% = their 15:00-15:15 ET block):
| instrument | book | engine events | ZL-1 events | common | share of engine | share of ZL-1 |
|---|---|---|---|---|---|---|
| NQ | K7 | 32619 | 32329 | 32329 | 99.11% | 100.00% |
| NQ | U7 | 2412 | 2399 | 2399 | 99.46% | 100.00% |
| NQ | H7 | 15744 | 15558 | 15557 | 98.81% | 99.99% |
| NQ | M7 | 38728 | 38293 | 38293 | 98.88% | 100.00% |
| NQ | P7 | 47733 | 47170 | 47170 | 98.82% | 100.00% |
| NQ | A7 | 3557 | 3566 | 3557 | 100.00% | 99.75% |
| NQ | O7 | 2035 | 2953 | 0 | 0.00% | 0.00% |
| ES | K7 | 34022 | 33715 | 33715 | 99.10% | 100.00% |
| ES | U7 | 2454 | 2442 | 2442 | 99.51% | 100.00% |
| ES | H7 | 16046 | 15850 | 15850 | 98.78% | 100.00% |
| ES | M7 | 39727 | 39285 | 39284 | 98.88% | 100.00% |
| ES | P7 | 43905 | 43334 | 43334 | 98.70% | 100.00% |
| ES | A7 | 3551 | 3558 | 3550 | 99.97% | 99.78% |
| ES | O7 | 2000 | 3324 | 0 | 0.00% | 0.00% |

O7: 0 events in common (theirs = PB7 on NY-AM, engine = PB on NY-AM): not pinned, see 7.4. ZL-1's first trade-count gap (1.6x) was a window difference on their side (reconciled by ZL-1: median ratio 0.986 on the same window). With the same ZN K7 events and the same 8-tick bracket the engine takes 5,744 trades against 5,430 for ZL-1's simulator (+5.8%): the engine allows a target only from the 2nd bar (NQ library convention) and fills at the close of the decision second + 1 tick; ZL-1's simulator allows a target in the entry bar and fills gapped stops at the bar open.
**Z2** (own 1-min simulator + MultiHarness; M7 mapped as EMA30/50 5-min cross): their identity against the NQ library: PB7 98.2%, PB3B 99.2%, Keltner/Supertrend/EMA ~99%; they did not run the engine's code.
**S4b** (`instr_core.py`: K7 U7 H7; bars /mnt/l2/l2vast/ds3_instr/<SYM>_1m.npz own roll adjustment; NQ, GC, CL on disk, ES not built), events 2023-04..2026-02-06, engine window cut at 15:00 like theirs:
| instrument | book | engine events (15:00 cut) | S4b events | common | share of engine | share of S4b | only S4b | only engine |
|---|---|---|---|---|---|---|---|---|
| NQ | K7 | 32269 | 32356 | 32177 | 99.71% | 99.45% | 179 | 92 |
| NQ | U7 | 2386 | 2409 | 2377 | 99.62% | 98.67% | 32 | 9 |
| NQ | H7 | 15551 | 14641 | 14062 | 90.43% | 96.05% | 579 | 1489 |
| GC | K7 | 32739 | 32610 | 32558 | 99.45% | 99.84% | 52 | 181 |
| GC | U7 | 2341 | 2338 | 2330 | 99.53% | 99.66% | 8 | 11 |
| GC | H7 | 15765 | 14864 | 14392 | 91.29% | 96.82% | 472 | 1373 |
| CL | K7 | 34542 | 34264 | 34217 | 99.06% | 99.86% | 47 | 325 |
| CL | U7 | 2747 | 2744 | 2739 | 99.71% | 99.82% | 5 | 8 |
| CL | H7 | 15879 | 14877 | 14381 | 90.57% | 96.67% | 496 | 1498 |

H7 differences explained on NQ: (a) S4b blocks 09:00-09:58 ET (live stack guard): 898 of the 1,489 engine-only H7 events are in that window; with the guard applied to the engine the sets agree on 96.0% each way; (b) the remaining ~4% (591 engine-only, 579 S4b-only) sit in the standard-time months (Nov-Mar) at 23:00-01:00 ET: the NQ library / engine HM resets the VWAP at a FIXED UTC-4 day boundary (00:00 EDT = 23:00 EST), S4b resets at ET midnight with DST: a logic difference in the VWAP reset in winter (the library convention reproduced 99.7% of the NQ HM rows). K7/U7: 99.4-99.9% on both sides.
### 7.4 O7 (pin)
The live O7 spec is not on disk under that name. What exists: the user's tag list ("O7 NY-AM pullback", DIRECTIVE_USER_ANSWERS_20261102.md), a live lot "O6 1" (DIRECTIVE_FOLLOWUP_20261031.md), the T-OPEN opening-drive pullback specs (DS3_SPEC_TOPEN_DR5m_pb1_rm0.5_X40_90_SESSION.md, DR10m_pb1..., DR5m_pb3...: NY-AM, drive of 5 min >= 0.5 x the 20-day median opening range, first 1-min bar closing against the drive, market entry in the drive direction, 40/90 bracket, 16:00 exit) and the O6 opening-book study (DS3_SESSION2_Q_OPEN_BOOK.md: DEAD; its cells are stop-entry breakouts). Best candidate = the T-OPEN drive-pullback cell, which is NOT what either port calls O7 (ZL-1: PB7 NY-AM, engine: PB NY-AM). **Needs the lead to pin O7**; until then O7 results from any slice are APPROXIMATE.
### 7.5 Participation cap and Z1 sensitivities as options
`IE.lots_at_equal_risk(sym, book)` -> equal-$-risk lots, the 1.7%-of-median-5-min-volume cap, whether it binds (ES K7: 4.1 lots vs cap 19, not binding). `IE.run_sensitivities(sym, book, path='1s')` runs bracket {z1, z1_warm, z1_bps} x cost {z1, z1_stress}. ES, all books, real 1-s path, 2023-04..2026-10-16, mean net pts per contract / mean R / $ per active day at the NQ-equal risk:
| book | bracket (stop pts) | z1 cost: mean net pts / mean R / $ per active day | z1_stress |
|---|---|---|---|
| K7 | z1 (11.75) | -0.495 / -0.042 / -925 | -0.844 / -0.072 / -1,579 |
| K7 | z1_warm (15.75) | -0.554 / -0.035 / -538 | -0.970 / -0.062 / -943 |
| K7 | z1_bps (17.00) | -0.583 / -0.034 / -474 | -1.021 / -0.060 / -831 |
| P7 | z1 (11.75) | -0.488 / -0.042 / -3,083 | -0.838 / -0.071 / -5,292 |
| P7 | z1_warm (15.75) | -0.448 / -0.028 / -1,481 | -0.862 / -0.055 / -2,850 |
| P7 | z1_bps (17.00) | -0.659 / -0.039 / -1,836 | -1.098 / -0.065 / -3,060 |
| U7 | z1 (11.75) | -0.225 / -0.019 / -238 | -0.568 / -0.048 / -603 |
| U7 | z1_warm (15.75) | -0.370 / -0.024 / -252 | -0.783 / -0.050 / -533 |
| U7 | z1_bps (17.00) | -0.294 / -0.017 / -176 | -0.725 / -0.043 / -435 |
| H7 | z1 (11.75) | -0.319 / -0.027 / -875 | -0.665 / -0.057 / -1,822 |
| H7 | z1_warm (15.75) | -0.640 / -0.041 / -974 | -1.057 / -0.067 / -1,607 |
| H7 | z1_bps (17.00) | -0.867 / -0.051 / -1,131 | -1.309 / -0.077 / -1,708 |
| M7 | z1 (11.75) | -0.358 / -0.030 / -620 | -0.705 / -0.060 / -1,221 |
| M7 | z1_warm (15.75) | -0.590 / -0.037 / -544 | -1.007 / -0.064 / -929 |
| M7 | z1_bps (17.00) | -0.671 / -0.039 / -520 | -1.111 / -0.065 / -862 |
| S7 | z1 (11.75) | -0.578 / -0.049 / -524 | -0.929 / -0.079 / -843 |
| S7 | z1_warm (15.75) | -0.587 / -0.037 / -279 | -1.004 / -0.064 / -478 |
| S7 | z1_bps (17.00) | -0.805 / -0.047 / -323 | -1.247 / -0.073 / -500 |
| W7 | z1 (8.81) | -0.497 / -0.056 / -832 | -0.814 / -0.092 / -1,363 |
| W7 | z1_warm (11.81) | -0.603 / -0.051 / -563 | -0.982 / -0.083 / -916 |
| W7 | z1_bps (12.75) | -0.696 / -0.055 / -556 | -1.097 / -0.086 / -876 |
| A7 | z1 (11.75) | -0.405 / -0.034 / -313 | -0.753 / -0.064 / -582 |
| A7 | z1_warm (15.75) | -0.820 / -0.052 / -473 | -1.245 / -0.079 / -718 |
| A7 | z1_bps (17.00) | -0.829 / -0.049 / -443 | -1.277 / -0.075 / -683 |

Every cell is negative on ES (both brackets and both cost stresses); the warm-up and bps brackets (15.75 / 17 pt) lose less per R than the primary 11.75 pt for K7, P7, S7, W7 but more for H7 and A7. Research screen only.
