# D8_STC_SPEC - the state cut (STC) read from the engine code, its cancel measure, an NT8 definition, and how close it is

Written 2026-11-23 by the STC-spec worker for DIRECTIVE_STC_SPEC_20261123_2005Z.md. Information only: nothing queued, no engine row run, no engine/mf_multi.py edit, no data deleted or written outside this page, the two parity CSV pairs and the scripts. All compute niced, on stored data (`/mnt/l2/l2vast/_th_state/days/*.npz`, stored fit trades in `runs_rf/`), plus ONE raw mbp-10 read (one day, section 4.4). Code paths are under `code/`.

Short answer: STC does not read Databento action codes. It is a one-second snapshot difference of the 10-level book minus the trade volume at that price, so an NT8 strategy can reproduce it. With the aggressor taken from the quote at the trade (NT8 gives bid/ask with every trade), the rebuilt measure matched the stored one exactly (46,148 prints, one day). With only a tick rule it fires on the same second for 197 of 219 STC exits and misses 18 of 219. The thing that breaks it is a clock skew of one second between the depth feed and the trade feed (section 4.3).

---------------------------------------------------------------------------
## 1. THE RULE (read from the code)

Engine class chain actually used by the D8 fits: `th_sz_ijk/state_sizer_ijk.py` (JointRep, hook layers) -> `th_state_s345/state_sizer_b.py:31` SizerRep -> `th_redo/state_base_b.py` StateBaseRep (state_base_b.py differs from state_base.py only at lines 23 and 134: output dir, bar-close mode). The cell for the MF books comes from the hook `th_engfix/ev_panel.py:59-64` (`_cell`: latest `cut_tl` entry with from <= entry time, else the base `by_unit` table, which has no MF tags, so MF books without a `cut_tl` entry have no state cut).

### 1.1 Codes
`th_layers/layer_gen.py:228-229, 249-251`: STC_BASE = {arm 45.0, mult 10.0, win 2, pers 3, newmae 0, var 2}; STC_RANGE = [arm 30 (STC1), arm 60 (STC2), mult 5 (STC3), mult 15 (STC4)], each applied on top of the base.

| code | arm (pts, before lot scaling) | mult | win s | pers s | newmae | var |
|---|---|---|---|---|---|---|
| STC1 | 30 | 10 | 2 | 3 | 0 | 2 |
| STC2 | 60 | 10 | 2 | 3 | 0 | 2 |
| STC3 | 45 | 5 | 2 | 3 | 0 | 2 |
| STC4 | 45 | 15 | 2 | 3 | 0 | 2 |

Picks: NY PM JT9 `TL3_SR_NP_STKd893133bd8_BF2_JT9`: MF3 = STC4, MF4 = STC4. London JT14 `TL3_SR_LO_L19201dfc_R0BRF90_30_BF2_JT14`: MF1 = STC4. Asia JT143 `TL3_SR_AS_STKd8106b26ef_BF2_JT143`: MF2 = STC4, MF3 = STC1. Asia JT19 has no STC in any of its 42 stored months (0 StateCut exits), so it is not part of the test below. (Checked in the set JSONs `/mnt/l2/l2vast/_th_sz/ijk/exact/sets/<pick>.json`, `ev_panel` hook `cut_tl`, and in the stored trades.)

### 1.2 The state per exchange second (the "state tape")
One row per second (`th_state/th_state.py:124-153` `build_day`; the same code for NQ in `th_fd/fd_state.py`): row ts = second + 1 (the END of the second the row describes); book = the book fields of the LAST mbp-10 record whose running-max ts_event second is that second (late records join the running-max second, th_state.py:44); seconds without records carry the previous book. Fields used by STC:
- `mid` = (best bid + best ask) x 0.5 at the row (th_state.py:149), NaN if either side is empty.
- `canc_bid`, `canc_ask` = cancelled size (contracts) per side per second, section 2 (th_state.py:67-102).
- `med` ("MedLevel") = EWMA, alpha = 0.001 per second (th_state.py:10 `ALPHA`, 104-113 `kern_ewma`), of x = (sum of the top-5 bid sizes + sum of the top-5 ask sizes) / 10 (th_state.py:150). It is the average displayed size of a top-5 level, in contracts. x is sampled every row, including seconds with no event. Seeded with the first x of an instrument (and re-seeded at a contract roll, kern_ewma `inst[i] != li`), carried across days (th_state.py:154-157 `med_for`, built with 9 warm-up days, `warm_days=9`).
- There is NO weighting by level in the cancel sum: all 10 levels count equally, in contracts. Only the top-5 levels enter `med`.

### 1.3 The rule (`th_redo/state_base.py:53-64` `advance`, `94-129`)
Per open trade (book with a cut cell), side = +1 long / -1 short, own side = bid for a long (`cum = _cumb`), ask for a short (`_cuma`) (state_base.py:117). The opposite side is not used.
- arm_eff (lines 99-104, var 2): `arm_eff = clip(arm x sqrt(q / 4), 15, 50)` with q = lots of the trade (b.qty, the same number as `lots` in the trade record; validated: 219 / 219 STC exits reproduced). STC4 (arm 45): q 1 -> 22.5 pts, 2 -> 31.8, 4 -> 45, >= 5 -> 50. STC1 (arm 30): q 1 -> 15, 2 -> 21.2, 4 -> 30, 8 -> 42.4.
- Per closed row r (r = 0 at the first row after the entry second): a = side x (mid[r] - entry_px) (entry_px = fill average); ext = min(ext, a) (init 0), last_ext = r where a <= ext (only used when newmae = 1; STC has newmae = 0, so ignored).
- pulled = sum of own-side canc over rows r-1 and r (win = 2 rows: lines 59 `cum[r+1] - cum[max(r+1-w,0)]`). The window is a plain 2-row window; it reaches back before the entry for the first evaluated row.
- ok(r) = (-a >= arm_eff) AND (med[r] > 0) AND (pulled >= mult x med[r]) AND (newmae off or ...). Units: arm in index points, pulled and mult x med in contracts.
- run = run + 1 if ok else 0 (NaN mid resets). FIRE at the first row with run >= pers = 3, i.e. three consecutive seconds with ok. advance returns the row.
- Armed from: `r_e` = first row with ts >= ceil(entry_ns / 1e9) (the row of the entry second); evaluation starts at row r_e + 1, ext starts at 0, last_ext at r_e (lines 111-113). Earliest possible fire = row r_e + 3 (3 evaluated rows), exit one row later: about 4-5 s after entry. No arming delay otherwise.
- Evaluated on rows that are complete: `rmax = searchsorted(ts, (now-1)//1e9, 'right')` (line 115): the engine calls it from `manage_th_l2` on every print of the trade (replica/sim.py:839) and processes every complete closed row not yet seen, so the clock is the closed second, not the print.
- When it fires (lines 119-122, 123-129): decision at the end of row fr; an event `statecut` is pushed for ts[fr+1] x 1e9 (one second later, like CU); price = mid[fr+1] - side x 0.80 pts (COST 0.80, line 22); at that time, if the trade is still open and no exit is pending and no stop triggered, the resting stop and target are dropped and the whole position is exited as `StateCut` (exec_exit). A bracket touch or other exit in between wins (the event no-ops). `done` is latched per trade: one fire per trade. Engine detail: the exit time is max(ts[fr+1], now), so 12 of 219 stored exits are 1-5 s later than ts[fr+1] (207 exactly at ts[fr+1]).
- Order versus other rules: hooks decide in written order; the first one that requests an exit names it (D8_LAYER_KEYS_NYAM.md section 3-4). In the stored fit trades no trade had a true fire in its window other than those exited by StateCut (0 of 5,804 other windows), so STC was never second to another rule in a way that hides a fire.
- Warm-up: the rule itself needs 2 rows of cancel history (3 for the diff: row r-2 book to compute canc of r-1) = at most 3 s before the first evaluated row, which the NT strategy has as soon as the depth feed is running at entry. `med` is the long memory: time constant 1/alpha = 1,000 s; a wrong seed decays to 5 % after 3,000 s and 1 % after 4,600 s. The engine's med is continuous over days (9 warm-up days) and resets only at a roll. For NT: start the EWMA at least ~1 h (best: from the 18:00 ET open, or restore yesterday's last value) before the first session where STC may fire; no STC decision while med is not seeded.

---------------------------------------------------------------------------
## 2. THE CANCEL MEASURE from the raw feed (`th_state/th_state.py:67-102` `kern_cancel`)

It is not built from action codes. Facts:
- Only mbp-10 records are read. The book at the end of each second = the last record of that (running-max) second, any action; the book columns `bid_px_00..09 / bid_sz_00..09 / ask_px_00..09 / ask_sz_00..09` (th_state.py:32, 47-49). Prices are stored in ticks of 0.25.
- Trades = records with action 'T' (code 84, th_state.py:43), (price, size, side) with side 'B' -> +1 (buy aggressor, hits the ask), 'A' -> -1 (sell aggressor, hits the bid), anything else -> 0 (th_state.py:51). Each trade is attributed to the row of its running-max second.
- For row r (second s) and the bid side, for every level j = 0..9 present at s-1 (price p > 0, size s1 > 0): look for price p among the 10 bid levels at s: found -> cur = size there; not found: if the 10th bid at s exists and p < that price (the level was pushed out of the 10-level window because the price moved down) -> the level is IGNORED (counted in `ign_bid`, not a cancel); otherwise cur = 0 (level gone). td = sum of trade sizes in second s with price == p and aggressor == -1 (sell). d = s1 - cur - td; cancelled at the level = max(0, d). canc_bid[r] = sum over levels (contracts). Ask side mirror: window rule p > the 10th ask, trades with aggressor +1.
- What this means for the cases asked: (a) a plain cancel = size drop with no trade; (b) a modify that reduces size = the drop counts; a modify that increases size is ignored (only drops count); a modify that changes price (cancel/replace) = a drop at the old price (full size, minus trades), the new level's increase is ignored; (c) a trade that removes size = its volume at that price (opposite aggressor side) is subtracted from the drop at that level and floored at 0 per level; (d) a level that leaves the 10-level window because the price moved away is ignored; a new level entering the window (an increase) is ignored; (e) adds and cancels at the same price inside one second net out (it is a snapshot difference, there is no event-by-event count); a level traded through and re-added is not seen; (f) rows where either book is missing or the instrument id changed (roll) get 0.
- Cancels of orders outside the 10 levels are not seen. The `have` flag: rows before the first record of a session are 0.
- Units: contracts per second per side. Typical own-side cancel in the tested windows: mean 3.98 contracts per second; typical threshold mult x med = 31-34 contracts for STC4 on 2025-09-17 (med about 2.1-2.2).

---------------------------------------------------------------------------
## 3. NINJATRADER-COMPATIBLE DEFINITION (proposal)

Do exactly the same snapshot difference, from the two NT8 streams, on one second clock.

1. Book: keep a 10-level array per side from OnMarketDepth (position 0-9, Add / Insert / Update / Remove, price, size; shift positions on Insert and Remove as NT8 documents) so that at any moment you hold (price, size) for 10 bid and 10 ask levels. At each second boundary, snapshot it (the state at the last depth event of the second; carry the previous snapshot if no event).
2. Trades: from OnMarketData Last (time, price, size, bid, ask) classify the aggressor at the trade: price >= ask -> buy (+1); price <= bid -> sell (-1); else 0 (unclassified, subtract nothing). Add the size into a per-second map keyed by (price, aggressor). The bid/ask must be the quote at the moment of the trade (the quote that NT delivered just before that Last), not the second-end quote.
3. At each second boundary s (using ONE clock for both streams, see below): for each side and each of the 10 levels in snapshot s-1 with size > 0: find the price in snapshot s; if absent and the 10th level of s exists and the price is worse than it, skip; else cur = size or 0; d = size(s-1) - cur - tradedvolume(s, price, aggressor against that side); canc += max(0, d). That is canc_bid / canc_ask.
4. med: x = (sum of 5 best bid sizes + sum of 5 best ask sizes) / 10 every second; med = med + 0.001 (x - med); seeded at the first x.
5. Rule: section 1.3 on the closed-second tape (mid = (best bid + best ask) / 2 of the snapshot).

Where it must differ from ours and what it costs:
- Aggressor flag: ours is the exchange flag. With the quote at the trade it is identical (4.4: 100.0 % of the volume of 46,148 prints, canc series equal on every row). A tick rule (price up = buy, down = sell, equal = carry; no quotes) agrees on 81.8 % of the volume and gives canc correlation 0.997, 91.9 % of rows exactly equal, sum ratio 0.990 (4.2). A rule against the previous second-end quote is worse (undercounts; 60 of 219 exits missed).
- Clock: ours uses the exchange ts_event (running max). NT8 stamps depth and trades on arrival at the NT machine or with the vendor time. If depth and trades are put into seconds by different clocks or are skewed by one second, STC breaks (4.3). Put both streams through one queue, stamp each event with ONE time (the same call, or event time for both), and cut seconds on that.
- A depth feed that does not deliver 10 levels (or that conflates updates) or that sends level changes with a delay relative to trades changes the diff; not testable on our data. Record raw (section 6) to measure it.
- No intra-second visibility: same as ours (snapshot method), so no difference.
- The rows with no trade-side flag in ours (side 'N') are subtracted by nobody; in NT unclassified (inside the spread) the same.
- Exit: ours is a modelled exit at mid[fr+1] -+ 0.80 pt at ts[fr+1]; live it would be a market order at the next second.

---------------------------------------------------------------------------
## 4. HOW CLOSE IS THE NT-COMPATIBLE VERSION ON OUR OWN DATA

Method (scripts in `code/th_stc_spec/`): stored fit trades of the four picks from `/mnt/l2/l2vast/_th_sz/ijk/exact/runs_rf/<pick>/<ym>/trades.parquet` (42 months 2023-04 .. 2026-10, no 202511), every trade of the STC books (6,023 trades). For each trade: the STC rule of section 1.3 run over the rows from the entry second to the trade's actual exit, on (a) the stored canc arrays (true), (b) a cancel measure rebuilt from the stored 10-level book + stored trades with a different aggressor source. This is a per-trade replay on the realised trade windows, not a full engine re-run with the NT state (a different cut changes the later path; not simulated).

### 4.1 Validation of my replay (not NT)
- Kernel rebuilt with the stored aggressor flag = stored canc arrays: identical in all 6,023 windows.
- True STC fire time vs the engine: 219 of 219 stored StateCut exits reproduced (207 exactly at ts[fire+1], 12 later by 1-5 s because the engine exits at max(ts[fire+1], now)); 0 fires in the 5,804 windows of trades with other exits.

### 4.2 Fire timing vs the true STC (counts over all 6,023 trades; true fires = 219)
"same s" = fire row equal; "<= 2 s" = other row within 2 s; "later/earlier" = more than 2 s apart; "not at all" = true fires, variant does not; "extra" = variant fires, true does not.

| variant | true fires | same s | <= 2 s | > 2 s | not at all | extra |
|---|---|---|---|---|---|---|
| T tick rule (no quotes) | 219 | 197 | 1 | 3 | 18 | 7 |
| A quote rule vs previous second-end quote | 219 | 159 | 0 | 0 | 60 | 0 |
| B quote rule vs current second-end quote | 219 | 81 | 11 | 127 | 0 | 863 |
| Q quote at the trade (4.4, one day, 10 trades, 3 true fires) | 3 | 3 | 0 | 0 | 0 | 0 |

Per pick, variant T (the realistic fallback if only a tick rule is used):

| pick / book | trades | true fires | same s | <= 2 s | > 2 s | not at all | extra |
|---|---|---|---|---|---|---|---|
| NY PM JT9 (MF3 + MF4) | 3,237 | 47 | 35 | 0 | 0 | 12 | 3 |
|  MF3 | 1,254 | 19 | 13 | 0 | 0 | 6 | 1 |
|  MF4 | 1,983 | 28 | 22 | 0 | 0 | 6 | 2 |
| London JT14 (MF1) | 1,331 | 21 | 21 | 0 | 0 | 0 | 0 |
| Asia JT143 (MF2 + MF3) | 1,455 | 151 | 141 | 1 | 3 | 6 | 4 |
|  MF2 | 662 | 7 | 5 | 0 | 0 | 2 | 0 |
|  MF3 | 793 | 144 | 136 | 1 | 3 | 4 | 4 |

Series closeness over the 25.56 M in-trade seconds (own-side canc per second; values in contracts; MAE in contracts and in units of med):

| variant | corr | rows exactly equal | exactly equal when either is > 0 | MAE | MAE / med | sum(variant) / sum(true) |
|---|---|---|---|---|---|---|
| T tick rule | 0.9970 | 91.9 % | 87.9 % | 0.13 | 0.025 | 0.990 |
| A previous-quote rule | 0.9912 | 91.0 % | 86.5 % | 0.24 | 0.043 | 0.941 |
| B current-quote rule | 0.9358 | 79.2 % | 69.0 % | 0.98 | 0.197 | 1.241 |
| price only, no aggressor | 0.9912 | 91.0 % | 86.5 % | 0.24 | 0.043 | 0.941 |
| no trade subtraction at all | 0.9191 | 73.5 % | 61.1 % | 1.34 | 0.262 | 1.336 |

### 4.3 Sensitivity to a clock skew between the depth and the trade streams
Same exact kernel (true aggressor flag) but each second's trades attributed to the second +1 or -1 relative to the book (NY PM + London, 4,568 trades, 68 true fires):
- trades +1 s late: 28 same s, 2 within 2 s, 36 later/earlier, 2 not at all, 628 extra.
- trades -1 s early: 30 same s, 4 within 2 s, 32 later/earlier, 2 not at all, 512 extra.
(Earlier full-pick runs with the price-only rule and +-1 s: 87-101 of 219 same second, 480-754 extra.) A one-second skew between the two streams is the biggest risk of the port, bigger than the choice of the aggressor rule. A skew of a fraction of a second cannot be tested on second snapshots.

### 4.4 Quote-at-trade on raw (one day, the parity day)
Raw `glbx-mdp3-20250916-20250917.mbp-10.dbn.zst` (`/mnt/l2/l2vast/raw/NQ/back/GLBX-20261020-E584SQ3UB8/`), window 2025-09-17 about 17:00-20:00 UTC, 46,148 prints aligned one to one with the stored trades. Aggressor from the top of book of the record just before each trade (price >= ask -> buy, <= bid -> sell): equal to the exchange flag for 100.00 % of the volume (0 opposite, 0 unclassified). The rebuilt canc_bid and canc_ask are equal to the stored arrays on every row (corr 1.0000, MAE 0). Tick rule on the same prints: 81.8 % same, canc corr 0.998, 90.5-91.1 % of rows exact. All 10 NY PM trades of the day (3 StateCut) give the same fire row with the quote-at-trade and the tick rule (3 of 3). Caveat: this uses the previous record's book as the quote at the trade, the best proxy we have for NT's trade bid/ask; NT's own quote timing is not tested.

### 4.5 Reading for the decision
- Port with the quote-at-trade aggressor and one clock: expected to reproduce the box state almost exactly (differences only from feed content/timing).
- If only a tick rule is available: about 90 % of the STC exits fire in the same second, about 8 % are missed, about 3 extra fires per 2,800 non-STC trades in NY PM (7 of 5,804 overall). Misses are mostly NY PM (12 of 47).
- Do not use a second-end quote or a price-only rule: they miss 27 % of the STC exits (A) or fire 863 extra times (B).
- Needs engine rows? Not for this test. An exact engine re-run of the three picks with the NT-compatible state replacing the stored one would be 3 sets x 42 months = 126 (set, month) engine rows (the NY PM row 202610 took 226 s on its own core; about 8 core-hours in total, ETA depends on the queue and is unknown). NOT queued; say if you want it.

---------------------------------------------------------------------------
## 5. PARITY PACK (files in `autopilot/`)

No NY PM or London day in the stored fits has 3 STC exits on a single book; the day with 3 STC exits in the NY PM pick (MF3 + MF4 together) is 2025-09-17 (the only such day); it is not recent. A recent day with 3 exits on one book (Asia JT143 MF3, STC1) is 2026-09-11. Both are delivered.

- `D8_STC_PARITY_NYPM_JT9_20250917_state.csv` (523 rows) + `..._inputs.csv`: 10 NY PM trades of MF3/MF4 on 2025-09-17; the 3 StateCut exits (MF4 entered 18:21:48, exit 18:22:10; MF3 19:00:03 -> 19:03:24; MF4 19:13:18 -> 19:23:39, UTC) with the first 8 evaluated rows and the last 90 rows up to fire + 2; the 7 non-fire trades with the first 8 rows and the 40 rows around the closest approach (min of arm ratio and pulled ratio).
- `D8_STC_PARITY_ASIA_JT143_20260911_state.csv` (390 rows) + `..._inputs.csv`: 5 MF3 trades, 3 StateCut exits (STC1: arm 30 x sqrt(lots/4), mult 10).
- State columns: trade, book, side, lots, entry_utc, entry_px, engine_exit_utc, engine_exit_name, row_end_ts (epoch s, the END of the second the row describes), row_end_utc, mid, unreal_pts, adverse_ext_pts, arm_eff_pts, cancel_own_true, cancel_own_nt_tick (tick-rule rebuild), cancel_other_true, pulled_w2_true, pulled_w2_nt_tick, med_level, thr_mult_x_med, mult, cond_arm, cond_pull_true, cond_pull_nt, run_true, run_nt, fire_true, fire_nt. The exit executes one row later (engine_exit_utc = row_end of the fire row + 1 s, plus up to 5 s engine lag in 12 of 219 cases).
- Inputs columns (same rows): the 10 bid and 10 ask levels (price in points, size) of the row, and the prints of that second as `price:size:aggressor` (aggressor +1 buy, -1 sell, 0 unknown) separated by `;`, so a C# implementation can recompute canc from the book and trades directly.
- Check order for the C#: (1) book + prints -> cancel_own (compare), (2) x and med (compare med_level; needs the seed, section 1.3), (3) pulled over 2 rows and the threshold, (4) unreal and arm_eff, (5) run and fire. Fire row = the first row with run >= 3.

---------------------------------------------------------------------------
## 6. RECORDING FORMAT (NT8 strategy, one CSV per session day, UTC, one row per second)

Per second (from the strategy's one-second clock):
1. `sec_utc_end` (epoch seconds of the END of the second) and ISO UTC; `clock_src` (which time stamp was used, same for depth and trades).
2. `bid0_px, bid0_sz, ask0_px, ask0_sz`, `bid_sum5, ask_sum5` (sum of the 5 best sizes each side), `mid`.
3. `x` = (bid_sum5 + ask_sum5) / 10 and `med_ewma` (alpha 0.001, say how it was seeded) and `med_seed_age_s`.
4. `canc_bid_nt, canc_ask_nt` (section 3 with the quote-at-trade aggressor) and `canc_bid_tick, canc_ask_tick` (tick-rule aggressor, same snapshots) so both rules can be compared with ours.
5. `n_depth_events`, `n_trades`, `buy_vol`, `sell_vol`, `unclassified_vol` (aggressor from the quote), `instrument` (contract month).
6. If a position is open: `book`, `side`, `lots`, `entry_px`, `unreal_pts`, `adverse_ext_pts`, `arm_eff_pts`, `pulled_w2`, `thr`, `cond_arm`, `cond_pull`, `run`, `fire`.
7. Optional second file, RTH windows only because of size: every OnMarketDepth event (arrival UTC with ms, side, position, operation, price, size) and every Last (arrival UTC with ms, price, size, bid, ask). With it the box can rebuild the measure event by event and test the timing question of 4.3.
Comparison after the daily pull: our `days/<label>.npz` for that day gives canc_bid, canc_ask, med, mid, bd5/ad5 (top-5 sums) per second; join on `sec_utc_end` = `ts`; report correlation, exact-equality share, fires same second / within 2 s / missed / extra, and the skew between the two clocks (median delay of trade vs depth per second).

---------------------------------------------------------------------------
## What I could not verify
- Actual NT8 behaviour (callback order, timestamps, depth coverage, conflation, Insert/Remove semantics of the vendor): no NT data was available. The test only has our Databento book, with +-1 s skews as a stand-in.
- The quote-at-trade result is from one day (2025-09-17 NY PM window, 46,148 prints) and uses the previous record's top of book as the quote at the trade.
- The closeness test is a per-trade replay on the realised windows of the stored fit trades, not an engine re-run with the NT state (path effects of a different cut are not simulated). Only first fire per trade is compared.
- Lots: arm_eff uses the trade's final lot count (`lots` = b.qty); validated on all 219 StateCut exits, but a trade whose lots change after arming is not separately checked.
- The live NinjaTrader/C# side (DS7.cs) was not read; this page is the engine rule. The code mapping STC1..4 is from layer_gen.py; the cells in the other D8_LAYER_* pages were read, not recomputed.
- JT19 (Asia) has no STC in the stored months, so nothing was tested for it.

Scripts and intermediate files: `code/th_stc_spec/` (stc_lib.py kernel and rule; run4.py, run4b.py, run4c.py closeness runs; an4b.py tables; rawq.py, rawan.py raw quote-at-trade check; parity.py pack builder). Intermediate pickles in the session scratchpad only.
