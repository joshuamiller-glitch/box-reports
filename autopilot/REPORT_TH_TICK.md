# REPORT_TH_TICK: Trade Health (lever B) on the NQ trade prints

Code (code/census/night_ins): ap_th_prints_cache.py (prints), ap_th_tick.py (ManageLoss kernel), ap_th_tick_val.py (live-log validation), ap_th_tick_run.py / ap_th_tick_main.py (state-consistent per-book re-runs and tables), ap_th_tick_eval.py / _grid.py (account layer), ap_th_tick_null.py / _nullan.py / _an.py / _rep.py (walk-forward and nulls).
Data: Databento NQ trades 2023-02-01..2026-10-16, 361.3M prints, the session-volume-leader contract per label day (prints cache outputs/autopilot/ddmin/prints, 8.1 GB; disk guard respected, 8 processes).

## 1. Result in five lines
1. The tick-level port passes the bar: on the live log, exit type matches 97.9% and type AND exit time within 2 minutes matches 95.9% (195 ST/HM exits, ComboLock rows excluded). The old 1-second port had 95-96% / 81-84%. TH rows lose the PROVISIONAL label (manifest status OK_TICK).
2. The file cells are uniquely the best fit on ticks: ST 15/3 gives 95.0% (next best cell 85.7%) and HM 10/3 gives 97.4% (next 90.8%) over the full 192-cell grid. This is independent evidence that the chart's TH values equal the file values (the on/off state still differs from the file: HM TH off after 10-09).
3. Lever B grid (off / ST / HM / both x MinPoints {10,15,20,25} x Required {2,3} x window {30,60} s x momentum {4,6,8} x pullback {4,6} x efficiency {0.35,0.5} = 192 TH-on cells per book) is stored for ST and HM: 386 files, outputs/autopilot/ddmin/tables/, manifest_tick.csv.
4. In-sample some cells look good (HM-only best cell: DD $242k to $177k with net +8%), and they beat the random-exit best-of-N null (p about 0.005), so TH exits carry information that random exits do not. But no cell is robust: plateau 0-17% against the 60% bar, span signs are mixed, and the walk-forward fails (section 5).
5. The live-fit cells (ST 15/3, HM 10/3) cost the pair money: both on = net -$1,084k, max DD +$78k, Sharpe -0.66 versus TH off (8/8). TH-off stays the base; lever B is not recommended.

## 2. How the C# is run on prints (state-consistent)
- Cadence: OnMarketData fires on every Last print; AddSample keeps one sample per >= 100 ms (throttled against the last SAMPLE time) and trims to (max window + 5) s on each accepted sample; the shared buffer is warmed from 45 s before the entry. Per print for a book in a trade: if ExitPending, PumpExit (market exit on the first print >= 400 ms after the request, after the cancel is effective); otherwise AdvExt/AdvExtTime update on every strictly worse print, then ManageLoss: eligibility latch, one evaluation per >= 1 s of print time, momentum via PriceAgo on the sample buffer (needs a sample older than the window), stall (print time since the adverse extreme >= window and recovery <= pullback), efficiency via WindowStats on the sample buffer (|last - first| / path < threshold, path from the samples). now = the print time. The adverse extreme, stop and target use every print (not samples).
- Stop = resting stop-market (fills at the print through it), target = resting limit (fills at the level when a print touches it; 1 tick through changes the match by -1 point). Both stay live until the cancel is effective (0-0.3 s tested, insensitive); the market exit fills at the first print after the order delay (0-0.5 s tested, insensitive).
- A TH exit frees the book; the next flip is taken (no suppression), so every cell is a full re-run of the book on the prints, per book. 'both' is the ST cell stream plus the HM cell stream combined by the account layer (lot netting, per-book rules, combined lock). Entries fill at the first print at/after the signal bar's minute start; entry_px in the tables is the engine bar open and exit_px = open + (exit print - entry print), so prices are comparable with the earlier tables. The TH-off control run on the prints (tk_off) reproduces the 1-second base: same exit type on 99.3-99.9%, mean points per trade 2.02 vs 2.06 (ST), pair net $2.68M vs $2.74M over 2023-08..2026-10.

## 3. Validation against the live log (outputs/h2/StratTrades_DualStrat_<acct>.csv)
Replay from each live entry fill (live entry time and price, 60-point stop, 1.0R target), ST TH 15/3 on throughout, HM TH 10/3 until 2026-10-09 14:12 and off after it.
| slice | exits | type and time within 2 min | type only |
|---|---|---|---|
| all (ComboLock excluded) | 195 | 95.9% | 97.9% |
| ST | 119 | 95.0% | 96.6% |
| HM | 76 | 97.4% | 100% |
| Asia (entry 18:00-02:59 ET) | 93 | 94.6% | |
| London (03:00-08:59) | 63 | 98.4% | |
| NY (09:00-15:59) | 39 | 94.9% | |
| close (16:00-17:59) | 0 entries | | |
| exit LossExit | 112 | 98.2% | 100% (112/112) |
| exit Target | 64 | 96.9% | 100% |
| exit Stop | 18 | 83.3% | 83.3% |
| exit SessionFlat | 1 | 0% | |
LossExit exit price minus engine print price: median 0 ticks, 25-75% range -0.75..+1.0 points. Sensitivity (cancel latency 0/0.1/0.3 s x market delay 0/0.1/0.5 s x entry lag 0/0.5 s): 95.9% throughout; target needing 1 tick through: 94.9%.
The 8 misses (4.1%): ST Stop live while the replay fires LossExit (10-11 20:10 and 21:01, Sunday session; 10-15 10:24, 30 s earlier); one live SessionFlat 5 s after a 10-12 18:01 entry (a live first-bar-of-session flatten the C# does by itself, the replay has no counterpart); two Targets that filled later live than the first touch (126 s, 1,764 s: queue position of the resting limit); two HM LossExits 237 s and 3,409 s apart in thin overnight markets.
Diagnosis of the old port's late/early bias: the 1-second rows fired LossExit 5-6 times where live ran to Target/Stop and had 81-84% on timing. On prints only the 3 ST Stops remain and no Target is cut. Cause: 1-second closes lose the intra-second path length (efficiency denominator) and the real 100 ms sample times and the sample-buffer warm-up rule (a window needs a sample at least window seconds old). Latency and target-touch conventions do not matter. Remaining uncertainty: live-side events the log cannot show (clock offset between the PC clock and exchange time, feed gaps, ST TH state around 10-11).

## 4. Lever B effect, TH on at the best in-sample cell vs TH off, with the live account layer
Best cell = lowest max DD among cells with net >= 90% of TH off (in-sample, 2023-08..2026-10, weeks); TH off = the print-method control; deltas versus it.

### 8/8: pair under the live account layer (cap 8R, week floor 8R, give-back 2R/67% from 00:00, per-book +5R/-2R), weeks 2023-08..2026-10
| line | cell | net | d net | max DD | d DD | worst week | d worst | Sharpe | d Sharpe | null rank | plateau (+-1 step) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1-second base (live streams) | - | $2742k | | $245k | | $-83k | | 1.90 | | | |
| TH-off, print-method control | - | $2678k | 0 | $242k | 0 | $-79k | 0 | 1.85 | 0 | | |
| best in-sample cell, TH ST (lowest DD at >=90% net) | tk_m25_r2_w60_mo4_pb4_e0.35 | $2613k | -65k | $224k | -18k | $-80k | -1k | 1.86 | +0.01 | see section 5 | 17% of 6 |
| best in-sample cell, TH HM (lowest DD at >=90% net) | tk_m25_r3_w60_mo6_pb4_e0.5 | $2898k | +220k | $177k | -65k | $-80k | -1k | 1.99 | +0.14 | see section 5 | 0% of 7 |
| best in-sample cell, TH both (lowest DD at >=90% net) | tk_m25_r3_w60_mo8_pb4_e0.35 | $3005k | +327k | $228k | -14k | $-83k | -4k | 1.98 | +0.13 | see section 5 | 0% of 6 |
| ST book alone, best in-sample cell | tk_m15_r3_w30_mo4_pb4_e0.5 | $1085k (off $846k) | +238k | $123k (off $227k) | -105k | $-41k (off $-42k) | | 1.41 (off 1.00) | | not nulled | |
| HM book alone, best in-sample cell | tk_m25_r3_w30_mo6_pb6_e0.35 | $1111k (off $1130k) | -19k | $130k (off $265k) | -135k | $-41k (off $-40k) | | 1.31 (off 1.33) | | not nulled | |

### 6/6: pair under the live account layer (cap 8R, week floor 8R, give-back 2R/67% from 00:00, per-book +5R/-2R), weeks 2023-08..2026-10
| line | cell | net | d net | max DD | d DD | worst week | d worst | Sharpe | d Sharpe | null rank | plateau (+-1 step) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1-second base (live streams) | - | $2057k | | $184k | | $-62k | | 1.90 | | | |
| TH-off, print-method control | - | $2009k | 0 | $182k | 0 | $-60k | 0 | 1.85 | 0 | | |
| best in-sample cell, TH ST (lowest DD at >=90% net) | tk_m25_r2_w60_mo4_pb4_e0.35 | $1960k | -49k | $168k | -14k | $-60k | -0k | 1.86 | +0.01 | see section 5 | 17% of 6 |
| best in-sample cell, TH HM (lowest DD at >=90% net) | tk_m25_r3_w60_mo6_pb4_e0.5 | $2174k | +165k | $133k | -49k | $-60k | -0k | 1.99 | +0.14 | see section 5 | 0% of 7 |
| best in-sample cell, TH both (lowest DD at >=90% net) | tk_m25_r3_w60_mo8_pb4_e0.35 | $2254k | +245k | $171k | -10k | $-62k | -3k | 1.98 | +0.13 | see section 5 | 0% of 6 |
| ST book alone, best in-sample cell | tk_m15_r3_w30_mo4_pb4_e0.5 | $814k (off $635k) | +179k | $92k (off $170k) | -78k | $-31k (off $-31k) | | 1.41 (off 1.00) | | not nulled | |
| HM book alone, best in-sample cell | tk_m25_r3_w30_mo6_pb6_e0.35 | $834k (off $848k) | -14k | $97k (off $198k) | -101k | $-30k (off $-30k) | | 1.31 (off 1.33) | | not nulled | |
The 'book alone' lines run one book alone through the layer with its rules scaled to that book's R, so the combined lock is twice as tight as in the pair; read the ST-only and HM-only pair lines as the per-book effect under the live layer.
Live-fit cells (ST 15/3 and HM 10/3, window 30, momentum 4, pullback 4, efficiency 0.35) versus TH off, pair:
| | net | d net | max DD | d DD | worst week | Sharpe |
|---|---|---|---|---|---|---|
| 8/8 ST TH on | $2,591k | -87k | $472k | +229k | -$88k | 1.72 (-0.13) |
| 8/8 HM TH on | $2,204k | -475k | $230k | -12k | -$79k | 1.56 (-0.29) |
| 8/8 both on | $1,595k | -1,084k | $321k | +78k | -$96k | 1.19 (-0.66) |
| 6/6 ST TH on | $1,944k | -65k | $354k | +172k | -$66k | 1.72 |
| 6/6 HM TH on | $1,653k | -356k | $173k | -9k | -$59k | 1.56 |
| 6/6 both on | $1,196k | -813k | $241k | +59k | -$72k | 1.19 |

## 5. Validity of lever B
- Walk-forward on the cell choice (best cell on the trailing 52 weeks, applied to the next 13, rolled over 11 blocks 2024-02..2026-10; 576 candidates plus TH off):
| criterion | OOS d DD | OOS d net | OOS d Sharpe | share of 200 null worlds doing at least as well (DD / net) |
|---|---|---|---|---|
| lowest DD at >= 90% net | +45.8% worse | -15.8% | -0.31 | 72% / 53% |
| highest net | +51.7% worse | -28.2% | -0.68 | 62% / 77% |
By mode (DD criterion): ST only -45.8% DD (worse) / -18.7% net; HM only -25.3% / -25.4%; both -11.4% / -26.7%. The procedure chose to stay off in 0 of 11 blocks (pair, all modes), i.e. it always found a cell that looked better on the trailing 52 weeks. The walk-forward gain is not positive for any mode and criterion; the one DD improvement ('both', net criterion: DD +1% better) comes with net -17% (null share 4% on DD, 62% on net).
- Random-exit null (200 replicates, random market exits with the empirical TH hold-time distribution, matched to each cell's TH-exit frequency per book, whole pair under the layer): per cell the best in-sample cells beat 99.5-100% of null replicates on DD reduction, so TH exits are more informative than random exits. Best-of-N null on the grid (best feasible DD reduction): observed ST 7.6%, HM 26.8%, both 5.8% versus null mean 0.1%, 1.9%, 0.2% (p = 0.01, 0.005, 0.015). So the in-sample effect is real as an in-sample statement and it does not survive time.
- Plateau (>= 60% of +-1-step neighbours keeping >= 75% of the DD gain at >= 90% net): ST best 17%, HM best 0%, both best 0%. Not met.
- Span signs (clean / H1 / H2 DD change at the best cells): ST best (-18k, -10k, -100k) with net (-415k, -112k, +461k); HM best (-65k, +39k, -101k) with net (+124k, +81k, +16k); both best (-14k, -9k, -55k) with net (+172k, +278k, -124k). The DD reduction is concentrated in H2 and flips sign in H1 for HM.
- No cell meets walk-forward gain > 0 with null rank >= 0.95 and plateau >= 60%: no robust TH cell.

## 6. Hand-back
TH-off remains the base; lever B in DDMIN should use the tick tables (ST_tk_*, HM_tk_*, control tk_off). With the bar met the label is OK_TICK. WT / WT10 TH on prints not run (optional). Files: outputs/autopilot/th_tick_{paths,stats,rep,nullan,wf,null,fit}.pkl.
