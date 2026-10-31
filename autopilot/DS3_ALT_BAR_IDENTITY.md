
# DS3 ALT-BAR IDENTITY - NT8 identity material for the five alt-bar cells (D7 Shadow from Sunday)
Sections: ALT-A (this block, first): L02766, L01501, L01610. ALT-B sections (L01490, L02783) follow below the line `ALT-B sections`. Agent ALT-A, 2026-10-31. Masks capped at label day 20260206 (the tape was read with ts < 2026-02-06 23:00Z only; UNTOUCHED never decoded). No new strategy, no new selection, no new scored statistic: the registered windows are re-computed from the same library code (`l2vast/ds3/code/bars_cand` + `bars_eng` harness, bar store) and tie out exactly to REPS_TIERED (n and mean in L3M, L6M, HOLD, PRE for all three cells). Code `autopilot/alt_bar_identity/code_altA/` (td.py = independent tape derivation, td_run.py, cmp3.py, lib_sig.py, lib2.py, final.py), CSVs `autopilot/alt_bar_identity/<cell>_signals_last10d.csv`.

## SUMMARY - the five alt-bar cells in one table (ALT-A + ALT-B; per contract, net M points, window ends 20260206)
**Plain statement: after PAIRFIX most of the paired wins against the 1-min engine were within noise (43 of 48 rows have neither the day-summed nor the trade-weighted HOLD CI excluding 0; for all five cells below both HOLD CIs include 0, and every HOLD result is inside its MDE). None is promoted; all five fail the cumulative-multiplicity gate G6. They run in Shadow only (D7), as identity tests of the bar builds and as a forward window, not as sized books.**
| | L02766 | L01501 | L01610 | L01490 | L02783 |
|---|---|---|---|---|---|
| bar / engine | 5-min time, SuperTrend(10 five-min bars, 3.5) | Heikin-Ashi 3-min, EMA30 x EMA50 (bars) | Range 8 pt, 3 per group, Keltner EMA14 ATR10 x1.0 | Volume 500, EMA30 x EMA50 (bars) | 2-min store bars grouped 2 = 4-min bars, EMA30 x EMA50 |
| session, bracket (target/stop) | NY-AM, 60/60 | NY-AM, 50/60 | Pre-open, 50/75 | London, 40/75 | London, 60/60 |
| tier (after PAIRFIX) | LEAD | LEAD | CANDIDATE-RECENT | LEAD (was CANDIDATE-RECENT) | LEAD |
| L3M n (tr/wk), M | 51 (3.92), +11.00 | 43 (3.31), +5.80 | 40 (3.08), +2.90 | 52 (4.00), +11.88 | 51 (3.92), +9.72 |
| L6M n (tr/wk), M | 113 (4.22), +5.47 | 92 (3.43), +5.34 | 68 (2.54), +0.76 | 94 (3.51), +5.78 | 87 (3.25), +9.59 |
| HOLD n (tr/wk), M | 124 (3.95), +6.60 | 106 (3.38), +3.76 | 74 (2.36), +1.10 | 108 (3.44), +4.46 | 102 (3.25), +10.62 |
| MDE HOLD (pts) | 14.6 | 14.7 | 19.4 | 13.3 | 15.0 |
| HOLD D / TW vs native 1-min, same bracket | +3.4 / +3.8 | +0.8 / +0.4 | +5.7 / +15.4 | +0.3 / -0.3 | +4.4 / +6.6 |
| HOLD D CI ; TW CI | [-5.4,+12.1] ; [-9.3,+16.3] | [-7.2,+8.1] ; [-13.0,+12.8] | [-2.0,+13.1] ; [-4.2,+33.3] | [-6.7,+6.5] ; [-10.9,+9.2] | [-2.1,+11.7] ; [-4.1,+18.9] |
| L6M / L3M D | +5.1 / +11.3 | +3.8 / -0.0 | +6.0 / +4.4 | +1.2 / +3.3 | +4.3 / +4.5 |
| tape re-derivation, last 10 days, in-session signals exact second+price | 5/5 | 2/2 | 49/53 (4 misses all on defect day 0202) | 20/20 | 24/24 |
| library trades reproduced | last 10 d, all sessions: 35/36 | last 10 d: 37/39 | last 10 d: 231/256 (225/225 off 0202) | all history, London: 535/541 (531/531 off defect days) | all history, London: 425/428 (420/422 off defect days) |
| HOLD n, M if only armed in the cell window (session-only) | 148, +3.73 | 118, +4.06 | 175, -6.24 | 135, +1.36 | 150, +2.16 |
Units: M x $20 = $ per contract per trade (costs inside); trades/week = n / (trading days/5); live lots for these books are not set. Read with the one-position rule (ALT-A 0 item 3, ALT-B 3): the edges as registered need the engine running all sessions as a ghost. Open items for the D7 owner: (1) the replayed-hour tape defect on 11 label days (rebuild the store from the de-duplicated tape?), (2) which Shadow mode (24-hour engine with session slice vs armed-only-in-window), (3) L02783 is a 4-minute chart, not 6- or 5-minute, (4) PAIRFIX wave-1 PRE/X' D values are 2x (ALT-B 4 item 12).

## ALT-A 0. Headline and consolidated identity table (ALT-A cells)
1. **All three cells re-derive from the raw tape with an independent implementation** (own bar builder, own indicators, own 1-second exit simulator; only the per-day back-adjust constant is taken from the library). Last 10 trading days (label days 20260126-20260206): signals at the exact second AND price: L02766 49 of 50 library signals (98%), L01501 53 of 55 (96%), L01610 1,295 of 1,421 (91%; **1,278 of 1,279 = 99.9% on the nine days other than 20260202**). Library trades reproduced (same signal, side, exit type, exit second): L02766 35 of 36, L01501 37 of 39, L01610 231 of 256 (**225 of 225 on the nine clean days**). In the cell's own session: L02766 5 of 5 signals and 5 of 5 trades; L01501 2 of 2 and 2 of 2; L01610 pre-open 49 of 53 signals (the 4 misses and 3 extra tape signals are all on 20260202) and 6 of 6 trades.
2. **The one mismatch day is a LIBRARY defect, not a tape/rule ambiguity.** 11 of the 36 monthly tape files (2023-04, 2023-07, 2023-10, 2024-06, 2024-09, 2024-12, 2025-02, 2025-03, 2025-06, 2025-11, 2026-02) contain the first 1-2 hours of the month duplicated at the top of the file, so the timestamp steps backwards once (2026-02: row 12,510). The bar store was built from the un-deduplicated file: on the first label day of each of those months (20230403, 20230703, 20231002, 20240603, 20240902, 20241202, 20250203, 20250303, 20250602, 20251103, **20260202**) the store replays the first hour once more (every bar type incl. time bars; `ts0` non-monotone; 20260202 has 3,667 range-8 bars vs 3,300 true, 480 3-min bars vs 460). For 20260202 the library signals in the first hours (and for range bars the whole day, because the 3-bar grouping is phase-locked to the day's first range bar) are wrong; the CSVs carry the tape-derived (de-duplicated) signals as `tape_only` and flag the corrupt library rows `lib_only` (`identity_target` = 0). Effect on registered statistics: 1 trade of 113 (L02766 L6M), 1 of 92, 1 of 68 sit on those days (e.g. L01610 HOLD +1.10 -> +2.16 without them): immaterial. Fix = de-duplicate then rebuild the store (not done; no live consequence). ALT-B met the same file (ALT-B section 1.3).
3. **Biggest trap for the Shadow build: the one-position rule runs across ALL sessions in the library.** The cell is the session slice of an engine that runs 18:00-15:15 ET with one position at a time (bracket exits only, flat 16:55). A NY-AM / pre-open signal is skipped if an Asia/London/earlier position is still open. A build that is only armed inside the cell's window (flat at the start of the window) takes extra signals and the numbers change: **L01610 pre-open HOLD +1.10 pts/trade (n 74) in the library vs -6.24 (n 175) session-only; L3M +2.90 vs -11.62; L02766 NY-AM HOLD +6.60 (124) vs +3.73 (148); L01501 NY-AM HOLD +3.76 (106) vs +4.06 (118).** Decide which one D7 shadows before comparing timestamps with trades (signals are identical either way; taken/not-taken is not).
4. **Spec wording that does not say what was scored** (details in each section): L02766 "ATR period 10" is 10 FIVE-minute bars (Wilder ATR, hl2 bands, final-band rules), not the 10-minute TE6 base; L01501 needs no Heikin-Ashi object at all (the EMA input is the HA close = OHLC4 of the real 3-min bar); L01610 "3-minute-equivalent grouping" is **3 consecutive 8-point range bars counted from the first range bar of each label day**, not 3 minutes and not a 24-point range chart.
5. Tiers after PAIRFIX (unchanged by this work): L02766 NY-AM 5-min = LEAD; L01501 HA-3m NY-AM = LEAD; L01610 range-8 pre-open = CANDIDATE-RECENT. All HOLD CIs of D and TW include 0, all HOLD results are inside their MDE, all fail G6; shadow only, none promoted.

| | L02766 | L01501 | L01610 |
|---|---|---|---|
| bar / engine | 5-min time bars; SuperTrend(ATR 10 bars, x3.5) flip | Heikin-Ashi 3-min time bars; EMA30 x EMA50 of HA close cross (bars) | Range 8-pt bars grouped by 3 per label day; Keltner EMA14, ATR10 x1.0 close-break |
| entry session (ET), bracket | NY-AM 09:30-12:00, 60 / 60 | NY-AM 09:30-12:00, target 50 / stop 60 | Pre-open 08:30-09:30, target 50 / stop 75 |
| tier (PAIRFIX) | LEAD (G6; G4 n/a) | LEAD (G6; G4 n/a) | CANDIDATE-RECENT (G6) |
| L3M n (tr/wk), M pts/contract | 51 (3.92), +11.00 | 43 (3.31), +5.80 | 40 (3.08), +2.90 |
| L6M n (tr/wk), M | 113 (4.22), +5.47 | 92 (3.43), +5.34 | 68 (2.54), +0.76 |
| HOLD n (tr/wk), M | 124 (3.95), +6.60 | 106 (3.38), +3.76 | 74 (2.36), +1.10 |
| MDE L3M / L6M / HOLD (pts) | 21.0 / 15.5 / 14.6 | 24.0 / 16.2 / 14.7 | 23.6 / 20.4 / 19.4 |
| HOLD D / TW vs native 1-min (95% CI) | +3.4 [-5.4,+12.1] / +3.8 [-9.3,+16.3] | +0.8 [-7.2,+8.1] / +0.4 [-13.0,+12.8] | +5.7 [-2.0,+13.1] / +15.4 [-4.2,+33.3] |
| L6M / L3M D | +5.1 / +11.3 | +3.8 / -0.0 | +6.0 / +4.4 |
| signals last 10 d (all sessions / in session) | 51 rows (50 lib) / 5 | 57 rows (55 lib) / 2 | 1,531 rows (1,421 lib) / 56 |
| tape re-derivation: signals exact second+price | 49/50 | 53/55 | 1,295/1,421 (1,278/1,279 off 20260202) |
| tape re-derivation: library trades reproduced | 35/36 | 37/39 | 231/256 (225/225 off 20260202) |
| session-only run HOLD n, M | 148, +3.73 | 118, +4.06 | 175, -6.24 |

Units: M = measured net points per contract (costs in section 0.2), x $20 = dollars per contract (1 NQ); lots are not part of any of the three specs (the numbers are per contract; D7 shadow = 1 lot). Trades/week = n / (trading days in window / 5): L3M 65 days, L6M 134, HOLD 157.

## ALT-A 0.2 Common engine rules (all three cells; code `bars_cand/bc_lib.py` run_br/sim2/prep, `bars_eng/be_lib.py`)
* **Data and coordinates.** Trade prints of the NQ contract with the day's volume (instrument_id 42002475 = the March-2026 contract in this window; the library rolled 2025-09-17 and 2025-12-16 on the label day shown, back-adjusted constant 811.75 pts for 20251216-20260206, 1047.75 before it, 1286.75 before 20250917). Library coordinate = raw price + constant. The CSV gives both (`signal_price_lib`, `signal_price_raw`). No roll falls in the last 10 days; an unadjusted merged chart would see a 236-pt jump at 2025-12-16 (239 at 2025-09-17).
* **Label day** = CME trade date: 18:00 ET of the previous calendar day to 17:59:59 ET (Sunday 18:00 opens Monday's label day). 10 label days = 20260126 ... 20260206 (CSV `label_day`; the Sunday-evening hours of 2026-01-25 and 2026-02-01 belong to 20260126 / 20260202).
* **Decision and fill.** A signal exists when the signal bar has closed. Library signal instant = (the first trade-second at or after the bucket end minus 1 s) + 1 s: for time bars that is exactly the bar end t1 when any trade printed in the last second of the bucket and t1+1 s (or later in a quiet market) otherwise (30% of the 5-min and 20% of the 3-min signals in the last 10 days); for range bars it is the second after the completing print. **The NT8 identity key is Time[0] of the signal bar** (bar end for time bars, time of the completing trade for range bars): CSV column `nt8_bar_time_ET`; `lib_signal_instant_ET` is the library convention. Entry is a market order at the signal instant; modelled fill = last trade price of the decision second +/- 1 tick against (long +0.25, short -0.25), booked in the next trade-second (`est_fill_*`).
* **Bracket.** Stop and target are fixed distances from the modelled fill. Per trade-second path: stop is checked from the fill second, target from the second after; both in one second = stop wins; exits at the exact level (no gap-through); time exit at the last trade-second before 16:55:00 ET. No reversal, no trailing, no break-even, no EMA/ST exit.
* **One position, across all sessions.** A signal arriving while a position is open is ignored (either direction). Entry only when the signal instant is within 18:00-15:15 ET (15:15-18:00 ignored). Sessions by the ET clock of the signal instant: Asia 18:00-02:00, London 02:00-08:30, Pre-open 08:30-09:30, NY-AM 09:30-12:00, NY-PM 12:00-15:00, Close 15:00-18:00. The cell is scored on the trades of its session only; the busy rule runs on the whole 24-hour stream.
* **Costs of M**: fee 0.242 pt round trip; stop exit 1.01 pt worse than the level; time exit 0.995 pt; target exit haircut 1.4 / 1.5 / 4.2 / 4.3 pt for 2023 / 2024 / 2025 / 2026. N = target exits free of the haircut; P9 = stop cost 2.45. These are model costs on resting stop/target exits; a live market-order entry also pays real slippage (not in M).

## ALT-A 1. L02766 - 5-minute time bars, SuperTrend(10, 3.5), NY-AM, 60 / 60 (tier LEAD)
### 1.1 Exact bar-build rule and engine
Source: ledger candidate L02766 `TE6_st10m_n10_m3.5`, scored as bar `tc/5m`, variant D (parameters counted in the bars), session NY-AM, bracket 60 / 60. The native 1-min control is the same SuperTrend run on 10-minute bars (1-min library bars grouped by 10, ATR 10 of 10-min bars), same bracket, same days.
* **Bars.** 300-second time buckets aligned to the clock (bucket start = multiple of 300 s on the UTC epoch = a multiple of 5 minutes on the ET clock; the first bar of a label day is 18:00-18:05 ET). A trade belongs to the bucket of its timestamp second (floor), bar O = first trade, H/L = extremes, C = last trade of the bucket. **No phantom bars**: a bucket without trades produces no bar (halt, Sunday gap); the recursion simply continues with the next bar and its true range uses the previous bar's close across the gap. Bars never span the 18:00 ET label-day change; the last bucket of a day is dropped if the day ended inside it. The series is one continuous sequence across days and weekends (no reset at any session open).
* **Indicator = SuperTrend as in `sd_state.supertrend_te` (not NT8's stock or any third-party SuperTrend; build it from these formulas).** ATR = Wilder: ATR[0] = H0 - L0 of the first bar, ATR[i] = (ATR[i-1] x 9 + TR[i]) / 10 with TR = max(H-L, |H - Cprev|, |L - Cprev|) - no SMA seeding. hl2 = (H+L)/2, basic upper = hl2 + 3.5 x ATR, basic lower = hl2 - 3.5 x ATR. Final upper[i] = basic upper[i] if (basic upper[i] < final upper[i-1] or C[i-1] > final upper[i-1]) else final upper[i-1]; final lower[i] = basic lower[i] if (basic lower[i] > final lower[i-1] or C[i-1] < final lower[i-1]) else final lower[i-1]. Direction starts +1; if dir = +1 and C[i] < final lower[i] then dir = -1; if dir = -1 and C[i] > final upper[i] then dir = +1. (Comparisons use the CURRENT bar's final band, the previous bar's close in the ratchet.)
* **Signal.** Each direction change on a closed bar is a signal in the new direction (flip entries, both ways: dir -1 -> +1 = LONG, +1 -> -1 = SHORT), evaluated on every bar of the 24-hour sequence; only entries are session-filtered. First bar of the series has no signal.
* **Entry/exit.** common rules above; bracket 60 pt stop / 60 pt target from the fill; session NY-AM = signal instant 09:30:00 <= t < 12:00:00 ET; 1 contract.
* **Warm-up.** Results are identical to the full-history library from one prior label day of history (tested: tape builds that start at 20260123, 0122, 0120, 0116, 0105, 20251201 and 20251103 - 1 to about 55 prior label days - give identical signal lists; a build that starts at 20260126 itself loses 1-2 signals); preload >= 5 days.

### 1.2 Signals, last 10 trading days
`autopilot/alt_bar_identity/L02766_signals_last10d.csv` (51 rows = 50 library signals + 1 tape-only; every flip, all sessions; columns in 1.4). In the cell's session (NY-AM), 5 signals, all `both`, all taken by the library and by a session-only run:
| ET bar time (NT8 Time[0]) | side | signal price raw | est. fill raw | status | exit |
|---|---|---|---|---|---|
| 2026-01-27 09:55:00 | LONG | 26037.25 | 26037.50 | both; taken yes | target +55.5 |
| 2026-01-30 11:25:00 | SHORT | 25765.00 | 25764.75 | both; taken yes | stop -61.3 |
| 2026-02-05 09:50:00 | LONG | 24926.00 | 24926.25 | both; taken yes | stop -61.3 |
| 2026-02-05 10:15:00 | SHORT | 24559.75 | 24559.50 | both; taken yes | stop -61.3 |
| 2026-02-06 09:40:00 | LONG | 24911.75 | 24912.00 | both; taken yes | stop -61.3 |
Signal price here is the 5-min bar close (raw contract coordinates). All-session list: of the 50 identity-target signals 6 fall outside the 18:00-15:15 entry window, 9 are skipped as busy and 35 are taken (plus the 1 library-only row, also taken); the CSV marks `entry_window_ok`, `taken_library_allsession`, `taken_session_only`.

### 1.3 Verification: independent tape re-derivation vs library
| scope (20260126-20260206) | library | tape | exact-second + price match | notes |
|---|---|---|---|---|
| all-session signals | 50 | 50 | 49 (98%) | 1 library-only (20260127 18:25:01 ET LONG; the tape flips at 19:20): near-threshold - the tape ATR is 14.19 vs 13.85, so the upper band sits 1.2 pts higher and the 26706.25 close does not clear it; cause = print-second placement (below) |
| library trades (all sessions, with busy rule) | 36 | 36 | 35 (97%) entry second, side, exit type, exit second all equal | the 36th is the same flip |
| NY-AM signals ; trades | 5 ; 5 | 5 ; 5 | 5 of 5 ; 5 of 5 | |
Why the residual: the library places each trade in a 1-second grid by cumulative-volume matching (a print may land one second later than its exchange timestamp), so bar closes can differ by one tick near bucket edges; ATR carries that tick-noise and a band-hugging close can flip. Over 20251103-20260206 (348 library flips) 9 are not reproduced at the same second by the tape version (2.6%): 4 in the roll week (20251217; the tape's max-volume contract rule picks a different instrument for 20251216), 1 on the replayed-hour day 20251103, and 4 near-threshold flips (20251111, 20251209, 20260116, 20260127). An NT8 build on its own feed will show the same kind of 2-3% of near-threshold flips; **a flip within about 1 pt of the band is not an identity failure.**

### 1.4 CSV columns (all three cells, same layout)
`nt8_bar_time_ET/UTC` (Time[0]: bar end for time bars, completing-trade second for range bars), `lib_signal_instant_ET`, `lib_signal_epoch_utc`, `side`, `bar_first_print_or_start_ET`, `signal_price_lib/raw` (value the indicator saw: for L01501 the HA close), `real_bar_close_raw` (L01501 only), `est_fill_lib/raw`, `contract_id`, `session`, `in_cell_session`, `entry_window_ok`, `source` (both / lib_only / tape_only), `tape_signal_price_lib`, `taken_library_allsession`, `taken_session_only`, `exit_type`, `exit_time_ET`, `gross_pts`, `net_M_pts`, `identity_target` (1 = what a correct NT8 build should print: both + tape_only), `note`.

### 1.5 L3M / L6M / HOLD per contract, trades per week, PAIRFIX D and TW (NY-AM, 60/60)
Control = native 1-min engine (SuperTrend 10 / 3.5 on 10-min bars grouped from 1-min), same bracket, same session, same days. D = mean over all days of (cell day-sum - control day-sum), TW = pts/trade difference, 5-day block-bootstrap CIs (DS3_PAIRFIX).
| window | n (trades/wk) | cell M pts/contract [95% CI] ($/contract) | MDE (2.8 SE) | control M (n) | D = cell-ctl pts/contract/day [CI] | TW = pts/trade [CI] | session-only run: n, M |
|---|---|---|---|---|---|---|---|
| L3M 20251106- | 51 (3.92) | +11.00 [-3.71, +25.71] ($+220) | 21.0 | -4.29 (41) | +11.34 [-1.13, +23.08] | +15.29 [-0.65, +31.66] | 55, +7.27 |
| L6M 20250801- | 113 (4.22) | +5.47 [-5.35, +16.29] ($+109) | 15.5 | -0.79 (85) | +5.12 [-4.80, +15.21] | +6.26 [-6.83, +18.90] | 125, +3.09 |
| HOLD 20250701- | 124 (3.95) | +6.60 [-3.59, +16.78] ($+132) | 14.6 | +2.84 (99) | +3.42 [-5.44, +12.10] | +3.76 [-9.34, +16.28] | 148, +3.73 |
| PRE 20240201-20250630 | 270 (3.71) | +8.10 [+1.36, +14.85] ($+162) | 9.6 | +2.00 (424) | +9.69 [-1.13, +20.43] | +6.11 [-2.10, +13.92] | 330, +7.93 |
| X' 20230401-20240131 | 236 | +4.15 | | -3.33 (222) | +8.15 [-3.36, +19.86] | +7.48 [-3.38, +18.59] | |
Reading: positive in every window and direction-consistent (D and TW > 0 in PRE, X', HOLD, L6M, L3M), no CI excludes 0, HOLD +6.6 inside MDE 14.6. HOLD win rate 57%, target 56% / stop 40% / time 3%, long share 44%.
Sessions in which the engine trades (all sessions run; only NY-AM is the registered/tiered cell; the other rows are the same engine's slice, **not selected, not claimed**, shown because the busy rule couples them):
| entry session (ET) | L6M n / M | HOLD n / M | L3M n / M |
|---|---|---|---|
| Asia 18:00-02:00 | 146 / -1.9 | 169 / -2.4 | 80 / -4.0 |
| London 02:00-08:30 | 116 / +1.0 | 131 / +1.9 | 69 / +6.4 |
| Pre-open 08:30-09:30 | 21 / -11.2 | 23 / -15.5 | 11 / -8.2 |
| NY-AM 09:30-12:00 **<- the cell** | 113 / +5.5 | 124 / +6.6 | 51 / +11.0 |
| NY-PM 12:00-15:00 | 48 / -2.2 | 53 / -3.5 | 27 / +0.8 |
| Close 15:00-15:15 (entry cut at 15:15) | 9 / +11.4 | 11 / +11.8 | 4 / +9.6 |

## ALT-A 2. L01501 - Heikin-Ashi 3-minute bars, EMA30 x EMA50 cross (periods in bars), NY-AM, target 50 / stop 60 (tier LEAD)
### 2.1 Exact bar-build rule and engine
Source: `ba2/EM_t50_s60` (BA bracket-assign rows2), scored on `ha/3m`, variant D, NY-AM, target 50 / stop 60 (note the order: target first). Control = EMA30/50 cross on 5-minute bars grouped from 1-min bars (the native EM engine), same 50/60 bracket.
* **Underlying bars.** 180-second time buckets, clock-aligned exactly like section 1 (18:00-18:03, 18:03-18:06, ...; no phantom bars; no reset at session open; label-day last bucket dropped if incomplete).
* **Heikin-Ashi.** haC = (O+H+L+C)/4 of the real 3-min bar; haO[0] = (O0 + C0)/2 of the first bar of the series, haO[i] = (haO[i-1] + haC[i-1])/2; haH = max(H, haO, haC); haL = min(L, haO, haC); carried across days (the store seeds at the start of each month's build, 5 warm days, irrelevant). **Only haC enters the signal**, so the seed and haO/haH/haL are irrelevant: **the NT8 object is EMAs of OHLC4 (= (O+H+L+C)/4) of a 3-minute time chart; no HeikenAshi bar type or indicator is needed.** If a HeikenAshi series is used anyway, the EMAs must read its close (haC), never the real close.
* **Indicator.** EMA(30) and EMA(50) of haC, alpha = 2/(n+1), first value = first haC of the series (NT8 EMA seeding), recursion over every 3-min bar, carried across days/weekends. Periods are counted in 3-minute bars (D), i.e. 90 and 150 minutes, not in 5-minute-equivalent bars.
* **Signal.** s = sign(EMA30 - EMA50); at each bar close a change of s between consecutive bars with both signs non-zero is a cross: s -1 -> +1 = LONG, +1 -> -1 = SHORT (an exact tie suppresses the cross). All sessions evaluated, entries session-filtered.
* **Entry/exit.** common rules; target 50 pt, stop 60 pt from the fill; NY-AM = signal instant 09:30:00 <= t < 12:00:00 ET; 1 contract.
* **Warm-up.** Identical from one prior label day (tested as for L02766: same lists from 1 to ~55 prior label days); preload >= 5 days.

### 2.2 Signals, last 10 trading days
`autopilot/alt_bar_identity/L01501_signals_last10d.csv` (57 rows = 55 library + 2 tape-only). NY-AM signals (2, both `both`, both taken): signal price is the HA close, `real_bar_close_raw` the true 3-min close; est. fill is the trade price.
| ET bar time (NT8 Time[0]) | side | signal price raw | est. fill raw | status | exit |
|---|---|---|---|---|---|
| 2026-01-27 10:06:00 | LONG | 26042.88 | 26024.25 | both; taken yes | target +45.5 |
| 2026-01-30 11:21:00 | SHORT | 25791.94 | 25788.00 | both; taken yes | stop -61.3 |

### 2.3 Verification: independent tape re-derivation vs library
| scope (20260126-20260206) | library | tape | exact-second + price match | notes |
|---|---|---|---|---|
| all-session signals | 55 | 55 | 53 (96%) | the 2 library-only and 2 tape-only rows are all on 20260202 (first 3 hours): the library's EMA state is corrupted by the replayed first hour of that label day (section 0.2); the tape-derived rows are the true ones |
| library trades | 39 | 39 | 37 (95%); 36 of 36 on the nine clean days | |
| NY-AM signals ; trades | 2 ; 2 | 2 ; 2 | 2 of 2 ; 2 of 2 | |
Exit seconds equal on every matched trade (difference 0 s); fills within 0.5 pt.

### 2.4 L3M / L6M / HOLD per contract, trades per week, PAIRFIX D and TW (NY-AM, 50/60)
| window | n (trades/wk) | cell M pts/contract [95% CI] ($/contract) | MDE (2.8 SE) | control M (n) | D = cell-ctl pts/contract/day [CI] | TW = pts/trade [CI] | session-only run: n, M |
|---|---|---|---|---|---|---|---|
| L3M 20251106- | 43 (3.31) | +5.80 [-10.99, +22.58] ($+116) | 24.0 | +7.17 (35) | -0.03 [-14.33, +14.28] | -1.37 [-25.62, +21.90] | 45, +6.58 |
| L6M 20250801- | 92 (3.43) | +5.34 [-6.02, +16.69] ($+107) | 16.2 | -0.23 (69) | +3.78 [-4.19, +11.60] | +5.57 [-7.10, +18.14] | 101, +4.31 |
| HOLD 20250701- | 106 (3.38) | +3.76 [-6.53, +14.04] ($+75) | 14.7 | +3.35 (80) | +0.83 [-7.19, +8.09] | +0.41 [-13.02, +12.76] | 118, +4.06 |
| PRE 20240201-20250630 | 257 (3.53) | +0.81 [-5.86, +7.48] ($+16) | 9.5 | +6.52 (376) | -5.59 [-15.46, +4.07] | -5.71 [-13.58, +2.39] | 290, +2.97 |
| X' 20230401-20240131 | 226 | -0.04 | | +3.83 (180) | -3.31 [-12.39, +6.68] | -3.87 [-14.16, +7.08] | |
Reading: the cell is positive in HOLD/L6M/L3M but its PRE and X' were ~0 (+0.8, -0.04) and the unconditional difference vs the 1-min control is nil in HOLD (D +0.8, TW +0.4) and L3M (-0.03 / -1.4). 2026 YTD (Y26, 16 trades) is -7.9. Inside MDE everywhere. HOLD win rate 60%, target 59% / stop 37% / time 4%.
Sessions in which the engine trades (same caveat as section 1.5; the registered cell is NY-AM only):
| entry session (ET) | L6M n / M | HOLD n / M | L3M n / M |
|---|---|---|---|
| Asia 18:00-02:00 | 152 / -1.5 | 177 / -3.9 | 79 / -1.7 |
| London 02:00-08:30 | 123 / +1.4 | 136 / +1.7 | 70 / +1.3 |
| Pre-open 08:30-09:30 | 22 / -7.9 | 23 / -10.2 | 10 / -7.9 |
| NY-AM 09:30-12:00 **<- the cell** | 92 / +5.3 | 106 / +3.8 | 43 / +5.8 |
| NY-PM 12:00-15:00 | 69 / -1.8 | 78 / -3.3 | 42 / -5.9 |
| Close 15:00-15:15 (entry cut at 15:15) | 4 / -17.0 | 7 / -5.4 | 0 |

## ALT-A 3. L01610 - Range 8-pt bars (3 per group), Keltner(EMA14, ATR10 x 1.0), Pre-open 08:30-09:30, target 50 / stop 75 (tier CANDIDATE-RECENT)
### 3.1 Exact bar-build rule and engine
Source: `ba2/KB_t50_s75` (BA bracket-assign rows2; its native ledger alive session is ASIA - the tiered bar row is the PRE-OPEN session of `range/8`, variant G), bracket target 50 / stop 75. Control = the native KB engine (Keltner EMA14, ATR10 x 1.0 on 3-minute bars grouped from 1-min), same bracket, same session.
* **Range bar (library SPEC `range(R)`), built from the print stream in order.** R = 8.00 pt = 32 ticks. A bar opens at the first print after the previous bar closed (or the first print of the label day); O = that print. Track H and L over all prints of the bar. **The bar closes on the print that makes H - L >= 32 ticks; that print stays in the bar (overshoot allowed: the bar's range can be 8.25 pt or more; its C = that print).** The next print opens the next bar at its own price (it can be several ticks away from the previous close). **No phantom bars**: a price jump of several ranges in one print makes one bar (0.14% of HOLD bars are >= 16 pt; max 76 pt), nothing is inserted. The range counter restarts at each label day (18:00 ET) and the unfinished range bar at the end of the day is discarded. Every trade print counts (size irrelevant, no aggressor filter, no minimum). In HOLD: mean 1,717 bars/day; 71% of bars have range exactly 8.00, 29% exceed it (4% by >= 1 pt); 27% open more than 1 tick from the prior close.
* **Grouping (variant G) = 3 consecutive range bars, counted per label day.** g = round(3 minutes x 1.0793 realised range bars per minute) = 3, a fixed constant. Group k of a label day = range bars 3k-2, 3k-1, 3k counted from the first range bar of that label day; group O = O of its first bar, H = max H, L = min L, C = C of its third bar; **the group completes on the completing print of its third range bar**. If the day ends with 1-2 range bars, they form a short last group that is kept as a bar for the EMA/ATR recursion but never signals. (Not 3 minutes, not a 24-pt range chart: both give different bars.) The count restarts at each label day, so a single extra or missing range bar early in a day phase-shifts every later group of that day.
* **Indicator (on the group series, carried across days).** mid = EMA(14) of group C (first value = first C); ATR = Wilder(10) of the groups (ATR[0] = H0 - L0, then (ATR x 9 + TR)/10, TR with the previous group's close); upper = mid + 1.0 x ATR, lower = mid - 1.0 x ATR, both computed with the current group's EMA/ATR (no shift).
* **Signal.** LONG on the group close when C > upper and the previous group's C was not above the previous upper (first break); SHORT when C < lower and the previous group was not below its lower. Re-arms when the close is back inside/outside. There is no exit on the opposite band.
* **Entry/exit.** common rules; target 50 pt, stop 75 pt from the fill; **pre-open = signal instant 08:30:00 <= t < 09:30:00 ET**; 1 contract. The library engine runs the whole 24-hour stream with one position (see 0 item 3).
* **Warm-up.** Identical from one prior label day; preload >= 5 days of ticks.

### 3.2 Signals, last 10 trading days
`autopilot/alt_bar_identity/L01610_signals_last10d.csv`: 1,531 rows (1,421 library signals + 110 tape-only; 56 in the pre-open window: 49 `both`, 4 `lib_only`, 3 `tape_only`; 6 taken by the all-session engine, 15 by a session-only run). Per label day (both / lib_only / tape_only): 20260126 51/0/0, 0127 36/0/0, 0128 76/0/0, 0129 120/0/0, 0130 182/0/0, **0202 17/125/109 (replayed-hour day)**, 0203 114/0/0, 0204 235/0/0, 0205 284/1/1, 0206 180/0/0. Pre-open signals per day: 3, 1, 2, 4, 6, 7, 4, 4, 19 (0205), 6. The pre-open rows are in the CSV (`in_cell_session` = 1); on 20260202 the four library rows are artefacts and the three tape rows (08:34:28 SHORT, 08:52:39 LONG, 09:15:00 LONG) are the identity target.

### 3.3 Verification: independent tape re-derivation vs library
| scope (20260126-20260206) | library | tape | exact-second + price match | notes |
|---|---|---|---|---|
| all-session signals, 9 clean days | 1,279 | 1,279 | 1,278 (99.9%) | the single miss, 20260205 07:54:01 ET, is a one-tick bar-boundary difference |
| all-session signals, incl. 20260202 | 1,421 | 1,403 | 1,295 (91.1%) | 20260202: library 142 signals vs tape 126, only 17 in common (library bars replay the first hour) |
| library trades, 9 clean days | 225 | 225 | 225 (100%) entry second, side, exit type, exit second | |
| pre-open signals ; trades, 9 clean days | 49 ; 6 | 49 ; 6 | 49 of 49 ; 6 of 6 | |
The exactness (99.9% of 1,279 signals at the same second and price) shows the range-bar rule, the 3-bar grouping and the Keltner recursion are specified completely. Sensitivity: the grouping is phase-locked to the day's first range bar, so one wrong trade print before the first bar of a day (a different tick feed, a dropped opening auction print) changes every group of that day - that is the failure mode of 20260202 and the main risk for an NT8 build on a different tick feed.

### 3.4 L3M / L6M / HOLD per contract, trades per week, PAIRFIX D and TW (pre-open, 50/75)
| window | n (trades/wk) | cell M pts/contract [95% CI] ($/contract) | MDE (2.8 SE) | control M (n) | D = cell-ctl pts/contract/day [CI] | TW = pts/trade [CI] | session-only run: n, M |
|---|---|---|---|---|---|---|---|
| L3M 20251106- | 40 (3.08) | +2.90 [-13.58, +19.38] ($+58) | 23.5 | -5.55 (31) | +4.43 [-9.41, +17.54] | +8.45 [-17.12, +33.68] | 89, -11.62 |
| L6M 20250801- | 68 (2.54) | +0.76 [-13.49, +15.01] ($+15) | 20.4 | -14.21 (53) | +6.01 [-2.74, +14.97] | +14.97 [-4.87, +35.09] | 158, -5.15 |
| HOLD 20250701- | 74 (2.36) | +1.10 [-12.50, +14.70] ($+22) | 19.4 | -14.29 (57) | +5.71 [-1.96, +13.08] | +15.39 [-4.18, +33.31] | 175, -6.24 |
| PRE 20240201-20250630 | 306 (4.20) | +0.14 [-6.02, +6.31] ($+3) | 8.8 | -12.86 (344) | +12.40 [+1.89, +23.40] | +13.01 [+4.24, +21.73] | 492, -2.78 |
| X' 20230401-20240131 | 142 | +0.61 | | -5.36 (116) | +3.36 [-8.34, +14.80] | +5.97 [-13.55, +23.65] | |
Reading: absolute M is ~0 in every window (+0.14 PRE, +1.10 HOLD, +0.76 L6M, +2.90 L3M, -8.6 in 2026 YTD n 18); the positive D and TW come from the CONTROL collapsing (native 1-min Keltner pre-open: -14.3 in HOLD, -12.9 in PRE), so there is no earning cell here. PRE keeps both CIs (D +12.4 [+1.9,+23.4], TW +13.0 [+4.2,+21.7]) but PRE was the selection window. HOLD CIs include 0; MDE 19.4. HOLD target 64% / stop 36% / time 0%, long share 55%.
Sessions in which the same engine trades (24-hour stream, pre-open is the only registered/tiered row; others not claimed):
| entry session (ET) | L6M n / M | HOLD n / M | L3M n / M |
|---|---|---|---|
| Asia 18:00-02:00 | 338 / -5.0 | 369 / -6.4 | 212 / -8.0 |
| London 02:00-08:30 | 247 / -1.8 | 266 / -2.4 | 153 / -3.0 |
| Pre-open 08:30-09:30 **<- the cell** | 68 / +0.8 | 74 / +1.1 | 40 / +2.9 |
| NY-AM 09:30-12:00 | 713 / +0.1 | 766 / +0.0 | 458 / -1.1 |
| NY-PM 12:00-15:00 | 330 / +1.7 | 353 / +0.9 | 200 / +0.3 |
| Close 15:00-15:15 (entry cut at 15:15) | 16 / +13.5 | 17 / +15.4 | 10 / +14.0 |
**Session-only caveat (large):** if the build is armed only in 08:30-09:30 and flat at 08:30, it takes 175 trades in HOLD (library 74) with mean -6.24 (L3M -11.62 on 89, L6M -5.15 on 158, PRE -2.78 on 492). The library's pre-open slice is, in effect, the pre-open signals that find the engine flat after Asia/London; its small positive mean does not carry to a pre-open-only engine.

## ALT-A 4. Ambiguities in the spec (DS3_BARS_ALL_CANDIDATES section 4) that would make an NT8 build differ
1. **Busy rule across sessions** (section 0 item 3): taken/not-taken differs materially between "24-hour engine, session slice" and "armed only in the window". Signals do not differ. L01610 is the extreme (n 74 vs 175, +1.1 vs -6.2).
2. **Range-bar close rule.** Library: the completing print stays in the bar (28.6% of HOLD bars exceed 8.00 pt, 4% by >= 1 pt, max 76 pt; 26.6% of bars open > 1 tick from the prior close). NT8's stock Range bar type is understood to cap bars at the range and open the next bar one tick beyond (to be verified on a chart; not testable on this box). With a stock Range-8 chart the bar sequence and therefore the 3-bar groups differ from the first overshoot of the day on, and L01610 will not reproduce. Use a custom bars type or OnMarketData tick replay implementing the rule in 3.1; test on 20260203-20260206 against the CSV (99.9%).
3. **3-bar grouping (G)**: group size 3 is a constant from the average 1.0793 bars/min over 2023-26 (not adaptive); counter restarts at 18:00 ET label day start; a short last group of the day stays in the EMA/ATR recursion; the spec text "3-minute-equivalent" suggests a time grouping.
4. **Time-bar signal timestamp**: Time[0] (bar end) vs the library instant (+0 or +1 s or more after a quiet last second); NT8 OnBarClose evaluates at the first tick of the next bucket. Use Time[0] and the price for the identity test; do not require the library's second.
5. **Bucket membership at the boundary**: library places trades in a 1-s grid by cumulative-volume matching; NT8 uses exchange/feed millisecond time. About 2-3% of near-threshold SuperTrend/EMA crosses flip on that tick noise; test on count and price within a tick, not 100%.
6. **SuperTrend definition**: custom (Wilder ATR seeded with H-L, final-band ratchet with previous-close tests, flip on current close vs current final band); NT8 has no stock SuperTrend and common ports differ (ATR SMA seeding, median price, band ratchet or not, flip test).
7. **ATR/EMA seeds and history**: library seeds at the first bar of 2023-04 and runs continuously across days; results are identical after one day of history, but NT8 must not reset indicators at session start/"Break at EOD" in a way that restarts the series (the bars may break at 18:00 ET; the recursion must not).
8. **Heikin-Ashi**: not needed for L01501 (OHLC4 EMA input); do not use the HA open/high/low or a different EMA input.
9. **Day boundary**: 18:00 ET (not the calendar day); range count and range-bar state restart there; CME maintenance hour 17:00-18:00 has (almost) no prints; label-day last range bar discarded.
10. **Rollover**: the library series is back-adjusted continuous (offsets 811.75 / 1047.75 / 1286.75); a chart on unadjusted merged data jumps 236 pts at the Dec roll (239 at Sep) and distorts ATR/bands for roughly 50 bars. No roll in the last 10 days or before the June 2026 roll in the capped window; live NT8 needs back-adjusted data or a one-day blind spot at each roll.
11. **Library defect on 11 label days** (section 0 item 2): do not use `lib_only` rows on 20260202 as the identity target; the shipped CSVs use `identity_target`.
12. **Lots and cost model**: none of the three specs states lots; all numbers are per contract. Entries are modelled as market at last price +/- 1 tick (no queue, no latency); exits as resting levels with the haircut of section 0.2; a live fill will be worse by the real entry slippage.
13. **Bracket order of the label** 'tNN_sNN': L01501 `t50_s60` = target 50 / stop 60 (not stop 50); L01610 `t50_s75` = target 50 / stop 75 (stop is the wide side).
14. **Session of the bar row vs the ledger cell**: L01610's native alive session is Asia; the tiered bar row is pre-open (one of 25,380 cells scored; the registered cell lists were not changed).

---

---
# ALT-B sections: L01490 (Volume-500, EMA 30/50, London) and L02783 (2-min G-grouped EMA 30/50, London) - NT8 identity material (agent ALT-B, 2026-10-31)

Files: signal CSVs `autopilot/alt_bar_identity/L01490_signals_last10d.csv` and `L02783_signals_last10d.csv`; code `autopilot/alt_bar_identity/code/` (ind.py = independent tape derivation, cmp/final/stats/csvs/tradeid/grp/busy/lonly/post = comparison and tables), numbers `autopilot/alt_bar_identity/data/*.json|csv`. Masks capped at label day 20260206 (flat 17:00 ET; the tape was read with ts <= 2026-02-06 22:00Z only; nothing after it was read, UNTOUCHED never decoded). No new strategy, no new selection, no new scored statistic beyond re-computing the registered cells' windows. "Library" = the BARS-CAND harness (`bars_cand/bc_lib.py` on the BAR-STORE, `be_lib.sim`), which produced the tier tables; I reproduced its HOLD/L6M/L3M/PRE/X' n and means to the digit (L01490 London 108/94/52 trades, +4.463/+5.779/+11.879; L02783 London 102/87/51, +10.622/+9.588/+9.725).

## ALT-B 0. Headline (read this first)
1. **Both cells re-derive from the raw tape.** An independent re-implementation (tape prints -> bars -> EMA30/50 -> cross -> same entry filter -> the same 1-second exit simulator) reproduces the library London trades: L01490 541 library trades vs 539 tape, **entry-second match 98.9% (all-history), 99.1% HOLD (107/108), 100% L3M (52/52); on the label days without the library's replayed-hour defect (ALT-A 0.2) 100%: 531/531 London trades, 106/106 in HOLD**; exit second equal and per-trade points correlation 1.000 on every matched trade. L02783 428 vs 429, **99.3% all-history (99.5% off the 11 defect days), 100% HOLD (102/102), 100% L3M (51/51)**. Over all sessions: signals 99.5% (L01490, 11,418/11,475 at the exact second; 99.9% = 11,328/11,339 off the 11 defect days) and 98.3% (L02783, 3,529/3,591; 98.7% off the defect days, the rest are boundary-print assignments, see 2.4). In the last 10 trading days **every London signal of both cells matches at the exact second, and the price matches to the tick** (20/20 L01490, 24/24 L02783); over all sessions 193/196 (L01490) and 53/55 (L02783), the misses being Asia signals on the Sunday-evening label day 20260202 and one NY-PM +/-1 s.
2. **L02783 spec as written is wrong.** "5-minute-equivalent grouping, rounded to 3 bars of 2m" is NOT what was scored. The scored cell groups 2 bars (g = round(5 x 0.49998) = round(2.4999) = 2): **EMA(30)/EMA(50) on 4-MINUTE bars (epoch buckets ending at ET minute = 0 mod 4)**, 2-min store bars merged pairwise. The 3-bar (6-minute) reading reproduces **0 of 428** library London trades; no plain EMA period on 2-min bars reproduces it (EMA 60/100 every 2-min bar: 41% of the trades, 35/102 in HOLD; EMA 75/125: 1%; EMA 30/50 direct: 0). The exact NT8 object is a 4-minute chart (or a 2-min chart where the EMA recursion is updated only on every second bar, at the :00/:04/:08... boundaries). Details in ALT-B 2.
3. **Biggest identity trap, both cells: the one-position rule runs across ALL sessions.** The library runs the engine 18:00-15:15 ET with one position at a time; the London cell is the London slice of that stream. A London signal is skipped when an ASIA (or earlier London) position is still open: in HOLD 46 of the 100 skipped L01490 London signals (and 95 of 143 for L02783) were blocked by an Asia trade carried into London. **An NT8 build that trades London only (flat at 02:00) takes those extra signals, and the numbers change**: L01490 London-only engine HOLD +1.36 pts/trade (n 135) vs +4.46 (n 108); L6M +1.54 vs +5.78; L3M +9.54 vs +11.88. L02783 London-only HOLD +2.16 (n 150) vs +10.62 (n 102); L6M +0.72 vs +9.59; L3M +3.63 vs +9.72. The CSV marks both: `status` (all-session engine, the identity test) and `london_only_engine_takes`. To run the identity test, the NT8 Shadow must keep the all-session virtual position (Asia entries 18:00-02:00 as ghost trades), otherwise it will not match; and the edge as registered depends on it (see ALT-B 5).
4. Tier after PAIRFIX: L01490 volume-500 London = **LEAD** (was CANDIDATE-RECENT; HOLD D +0.3, TW -0.3, fails the unconditional G3); L02783 2-min-G London = **LEAD** (HOLD D +4.4 [-2.1,+11.7], TW +6.6 [-4.1,+18.9]; CI includes 0). Both fail G6 (multiplicity) and G4 is not testable for the clock bar. Shadow only.

## ALT-B 1. L01490 - Volume-500 bars, EMA 30/50, London, target 40 / stop 75

### 1.1 Exact bar-build and engine rule (NT8-implementable)
Source: the registered ledger cell `ba2/EM_t40_s75` (family BA bracket-assign rows2), evaluated on `vol/500` with variant D (periods counted in bars), session London, bracket target 40 pt / stop 75 pt from the fill.
* **Prints.** Every trade print (one tape row = one print, size `sz` contracts, no aggressor filter; the 'N'-side opening/auction prints count) of the contract the library uses for the CME label day (the contract with the day's volume; instrument id in the day file). Label day = 18:00 ET (previous calendar day) to 17:00 ET; the maintenance hour has no prints. Prices are the BACK-ADJUSTED continuous series (library coordinate = raw contract price + a per-contract constant; the raw price is in the CSV column `signal_price_raw_contract`). EMA crosses are invariant to the constant, but not to a roll inside the series (see 6).
* **Volume counting rule.** Accumulator starts at 0 at the FIRST print of each label day (18:00 ET, Sunday 18:00 for Monday). Each print adds its whole size. When accumulator >= 500 on a print, **that print belongs wholly to the bar and closes it (no splitting; the overshoot is discarded, not carried)**, the accumulator resets to 0 and the NEXT print opens the next bar. A print that takes the sum from 499 to 520 therefore makes a 520-lot bar. Bar volume: median 500, mean 501.07, max 1,443; 34.7% of bars exceed 500 (single large prints). **The counter does not run across the 18:00 ET label-day boundary; the unfinished last bar of a day (before 17:00) is dropped and never closes.** About 1,134 bars per label day (82 to 2,342), 823,029 bars from 2023-04-03 to 2026-02-06.
* **Bar fields.** O = first print, H/L = extremes of all prints in the bar, C = last (completing) print.
* **EMA.** EMA(n) of the bar CLOSE, alpha = 2/(n+1), first value = the first close of the series (NT8's EMA seeding, `EMA[0] = input[0]`), then `EMA[i] = alpha*C[i] + (1-alpha)*EMA[i-1]`, **carried across label days and weekends, never reset at the session open**. The library series starts 2023-04-03; any seed older than ~1 day is irrelevant at float precision (EMA50 decay 0.96 per bar x 1,100 bars/day), so an NT8 chart needs >= 2 label days of history, not the full seed.
* **Signal.** At bar close: `s = sign(EMA30 - EMA50)`. A cross is a change of `s` between consecutive bars with both signs non-zero: LONG when s goes -1 -> +1, SHORT when +1 -> -1 (an exact tie, s = 0, suppresses the cross; irrelevant in practice). First bar of a label day compares against the last bar of the previous day. Signal time = the completing print. Signal price = the bar close (CSV: library coordinate and raw contract price, plus EMA30/EMA50 values).
* **Decision second and fill (engine's convention).** D = the 1-second library bar containing the completing print (equals the tape second `ts // 1e9` of the print in 99.5% of all signals; +/-1 s in the rest). The order is modelled as a market order at the END of second D: **fill price = last print of second D +/- 1 tick adverse (buy +0.25, sell -0.25)** (CSV `model_fill_px`; this can differ from the signal-bar close by a few ticks because later prints in the same second count). Fill is booked in the next print second.
* **Entry gate.** Entry time (= D + 1 s, ET) must be within 18:00-15:15 ET (the 15:15-18:00 window is excluded) and inside the cell session: **London = 02:00:00 <= time < 08:30:00 ET**. Signals on partial bars are dropped (not relevant for volume bars).
* **One position (the busy rule).** Only one position per engine at a time, **across all sessions and across both signal directions**; a signal while a position is open is ignored (no reverse, no add, no EMA-cross exit). The engine is run on all sessions (Asia, London, pre-open, NY-AM, NY-PM) and the cell is the London slice (see 0.3).
* **Bracket.** Target = fill +40 pt (long) / -40 pt (short); stop = fill -75 / +75 pt. Evaluated on the 1-second high/low path from the fill second: **stop checked from the fill second, target checked from the second after the fill; if both are touched in the same second the stop wins**; exits book at the stop/target level. **Flat at 16:55:00 ET** of the label day (time exit at the last second before 16:55). 1 contract per signal (per-contract points; the live lot is the book's setting).
* **Cost basis of 'M' (headline)**: stop exit -1.01 pt, time exit -0.995 pt, target exit -(1.4/1.5/4.2/4.3 pt for 2023/2024/2025/2026), fee -0.242 pt per round trip; N = same without the target-slip term (target filled at the limit price), P9 = stress stop cost 2.45 pt.

### 1.2 Last 10 trading days (label days 20260126-20260206) - signal list
CSV `autopilot/alt_bar_identity/L01490_signals_last10d.csv` (196 rows = all EMA30/50 crosses, all sessions: 90 taken, 78 skipped_busy, 28 outside the 18:00-15:15 entry window). Columns (same convention as ALT-A: `source` = both / lib_only / tape_only, `identity_target` = 1 for both and tape_only, 0 for lib_only; 4 extra rows on defect day 20260202: L01490 2 lib_only + 2 tape_only, L02783 2 lib_only): label_day, side, decision_second_ET / UTC (the library second D), completing_print_time_ET_ms_tape (tape timestamp of the completing print, millisecond), session, status, signal_price_close (library coordinate) and raw contract, ema30, ema50, model_fill_px, exit second/type, gross and net points, the independently re-derived second and price (`tape_rederived_*`, `tape_minus_library_s`), `blocked_by` (the open trade that blocked a skipped signal), `cell_in_scope` (London) and `london_only_engine_takes`.
London signals (cell in scope), 20 of them, 11 taken by the all-session engine:
| day | ET second | side | price (lib) | status |
|---|---|---|---|---|
| 01-26 | 04:48:18 | short | 26420.00 | taken (stop) |
| 01-26 | 07:08:31 | long | 26523.25 | taken (target) |
| 01-28 | 04:32:17 | short | 27065.50 | taken (target) |
| 01-28 | 05:35:34 / 07:36:25 / 08:05:24 / 08:09:56 | long / short / long / short | 27109.25 / 27086.75 / 27107.75 / 27100.25 | skipped (busy: the 04:32:17 short) |
| 01-29 | 05:58:45 | short | 27001.75 | taken |
| 01-30 | 05:51:00 | long | 26591.50 | taken |
| 02-02 | 02:30:34 | long | 26116.50 | taken |
| 02-03 | 06:09:01 | short | 26763.25 | taken |
| 02-03 | 07:50:34 | long | 26804.25 | skipped (busy) |
| 02-04 | 03:58:13 / 05:56:39 | short / long | 26229.25 / 26265.75 | taken |
| 02-04 | 07:51:52 | short | 26221.00 | skipped (busy) |
| 02-05 | 04:05:25 / 05:14:48 | short / long | 25806.00 / 25889.50 | taken |
| 02-05 | 06:10:29 / 06:22:53 / 06:30:51 | short / long / short | 25845.50 / 25867.00 / 25831.50 | skipped (busy) |
(20260127 has no London signal; 01-28 times shown to the second; full detail incl. exits in the CSV.) Times are America/New_York.

### 1.3 Verification: tape re-derivation vs library
Independent code `code/ind.py` (own volume segmentation, own EMA, own label-day assignment, own contract choice = max-volume instrument per label day (0 mismatches vs the library's instrument on 726 days); shares only the per-day back-adjust offset table of the bar-store meta and the 1-s exit path/simulator).
| scope | library trades | tape trades | exact entry-second+side match | within 1 s / 5 s | exit second equal (matched) | per-trade pts corr |
|---|---|---|---|---|---|---|
| all sessions, 2023-04..2026-02 | 4,342 | 4,338 | 99.24% | 99.42% / 99.56% | 100% | 1.000 |
| London, all history | 541 | 539 | 98.89% | 99.08% / 99.26% | 100% | 1.000 |
| London HOLD (20250701-) | 108 | 108 | 99.07% (107/108) | 99.07% | 100% | 1.000 |
| London L3M | 52 | 52 | 100% | 100% | 100% | 1.000 |
All-session signals (before the busy rule): 11,475 tape vs 11,477 library, 11,418 at the exact second (99.5%).
Causes of the 0.5%: (a) the **library defect found by ALT-A (ALT-A 0 item 2)**: 11 of the 36 monthly tape files carry the first 1-2 hours of the month duplicated at the top (timestamp steps backwards once, 2026-02: row 12,510) and the bar store replays that hour on the first label day of the month (20230403, 20230703, 20231002, 20240603, 20240902, 20241202, 20250203, 20250303, 20250602, 20251103, 20260202). It moves the volume-bar phase of the whole day (the counter runs over the replayed prints; 584 lots at 18:00:00.000 are counted at a different position). All 11 days are flagged `vol_ok False` in the store meta (11 further `vol_ok False` days are roll/after-holiday days with a smaller tape-vs-library volume difference and no signal difference found). Removing the 11 days: **London trades 531/531 identical (100%), HOLD 106/106, signals 11,328/11,339 (99.9%)**; the single London HOLD miss (2 events, 20251103 04:09:30/04:09:40) is on a defect day; 2 Asia signals on label day 20260202 (the day starting Sunday 2026-02-01 18:00 ET) differ in time (tape 18:46:40 long, 20:22:40 short vs library 18:58:57, 20:30:17) - **no London signal of that day is affected (all match to the second)**; (b) +/-1 s between the tape second and the library's cumulative-volume-matched second (e.g. 2025-04-19 09:45:17 vs :18). Three roll days (20250617, 20250917, 20251216) have no bars in the store (the library instrument has < 100 prints that day), so neither side has trades on them.

### 1.4 L3M / L6M / HOLD per contract, trades per week, PAIRFIX D and TW (London, 40/75)
Trades/week = n / (trading days / 5). 'M' = per-contract net points (x $20 = $ per contract; costs inside). Control = native 1-min engine (EM, library 1-min grouped to 5-min bars, EMA30/50), same bracket 40/75, same London session, same days.
| window | n (trades/wk) | cell M [95% CI] | MDE | control M (n, tr/wk) | D (cell-ctl, pts/contract/day) [CI] | TW (pts/trade) [CI] |
|---|---|---|---|---|---|---|
| L3M 20251106- | 52 (4.00) | +11.88 [-0.41, +24.17] | 17.6 | +8.79 (46, 3.54) | +3.28 [-10.95, +15.17] | +3.09 [-14.57, +20.92] |
| L6M 20250801- | 94 (3.51) | +5.78 [-3.99, +15.55] | 14.0 | +4.73 (80, 2.99) | +1.23 [-6.52, +8.17] | +1.05 [-10.35, +11.73] |
| HOLD 20250701- | 108 (3.44) | +4.46 [-4.81, +13.74] | 13.3 | +4.77 (91, 2.90) | +0.31 [-6.70, +6.51] | -0.30 [-10.94, +9.24] |
| PRE 20240201-20250630 | 316 (4.34) | +0.57 [-5.09, +6.23] | 8.1 | -4.09 (246, 3.38) | +3.26 [-0.91, +7.48] | +4.67 [-0.99, +10.74] |
| X' 20230401-20240131 | 117 (2.77) | +0.73 [-8.63, +10.09] | 13.4 | -2.68 (86, 2.04) | +1.50 [-2.88, +5.67] | +3.41 [-5.97, +13.15] |
HOLD: win rate 72%, targets 71% / stops 28% / flat 1%, long share 48%; N basis +7.47, P9 stress +4.06. Dollars per contract: HOLD +4.46 pt x 3.44 trades/wk = +15.3 pt/wk = about +$307/contract/week (CI includes 0); L3M +$950. The D and TW CIs include 0 in every window. Tier LEAD (G3u failed: HOLD TW -0.3 <= 0; G6 fails). The cell beats a 1-min control that is itself +4.8 in HOLD: the gain over the 1-min engine is nil in HOLD.
Sessions: only London is registered for this bar. The same ledger cell on 2-minute bars in NY-AM (L01490 tc/2m NY-AM) was demoted LEAD -> DEAD by PAIRFIX; other sessions of vol/500 are not claimed.

## ALT-B 2. L02783 - 2-minute bars, EMA 30/50 G-grouped, London, 60/60

### 2.1 What "G" actually is (the answer to 'express it as an exact EMA period on 2-min bars')
Registered cell: `xte TE7_emax5m_f30_s50` (EMA30 x EMA50 cross natively on 5-minute bars), re-derived on the 2-minute store bars with variant G = `g = max(1, round(minutes x bars_per_minute))` = round(5 x 0.499980) = round(2.4999) = **2** (and Python's round-half-even would also give 2 at exactly 2.5). So **the scored object is EMA(30)/EMA(50) of the CLOSE of 4-MINUTE bars built from consecutive pairs of 2-min bars**. It cannot be written as a plain EMA period on every 2-min bar: the recursion alpha = 2/31 and 2/51 is applied once per 4 minutes. NT8-exact forms: (i) a 4-minute time chart, EMA(30) and EMA(50) of Close; or (ii) a 2-min chart with a manual recursion updated only on the second bar of each 4-min bucket. Equivalences tested against the library London trades (428 trades, same side and same decision second):
| variant | London trades | HOLD n / M | L3M M | library trades reproduced (all / HOLD) |
|---|---|---|---|---|
| A. scored: 4-min epoch buckets (g=2), EMA30/50 | 428 | 102 / +10.62 | +9.72 | 428/428 (100%) / 102/102 |
| B. spec text: 3 bars (6-min buckets), EMA30/50 | 383 | 84 / +9.20 | +8.81 | 0 / 0 |
| C. 2-min bars, EMA 60/100 every bar | 417 | 96 / +11.45 | +9.73 | 176 (41%) / 35 |
| D. 2-min bars, EMA 75/125 every bar (period x2.5) | 406 | 96 / +1.81 | +0.71 | 5 (1%) / 0 |
| E. 2-min bars, EMA 30/50 direct | 550 | 150 / -2.89 | -0.53 | 0 / 0 |
| F. native 5-min (1-min grouped by 5), EMA 30/50 = the 1-min control | 410 | 98 / +4.04 | +4.14 | 1 / 0 |
So the identity target is the 4-minute chart; the half-life of the filters is 4 x 30 and 4 x 50 minutes, not the 5-minute native 150 / 250 (the cell is NOT the registered native 5-min engine). Variant C looks similar in HOLD average but is a different signal set; do not use it for the identity test.

### 2.2 Exact bar-build rule (NT8)
* **Underlying bars.** 2-minute time bars from the print stream, epoch-aligned buckets `floor(print_second / 120)` (UTC epoch; every ET offset and the 18:00 ET label-day start are multiples of 2 and of 4 minutes, so buckets end at ET :00, :02, :04 ... with no DST shift). A bucket exists only if at least one print falls in it (empty minutes produce no bar and no EMA step). O/H/L/C = first/high/low/last print of the bucket.
* **4-minute bars (the G grouping).** Two consecutive epoch 2-min buckets form one group: bucket pairs `floor(print_second / 240)` (group ends at ET mm = 0 mod 4, e.g. 04:52:00). O = first print of the group, H/L extremes, C = last print. A group is marked partial (its signal is suppressed, but the bar still enters the EMA) only when its second 2-min half has no prints; the day's last group is dropped if the day ended before the group end. The grouping does not cross the 18:00 ET label-day start.
* **EMA / cross / seed / carry.** As L01490 (alpha 2/(n+1), seed = first close, carried over days; cross = sign flip of EMA30-EMA50), applied to the 4-minute closes.
* **Decision second.** The 4-min bar [t0, t1) is known at the first print second >= t1 - 1 (i.e. the last second of the bar, or the first later print second if that second had no print: the CSV `decision_second_ET` is usually hh:mm:59 or hh:mm:00-03). Signal price = last print in the bucket = the bar close (NT8 closes a time bar on the first tick of the next bucket; the identity test should compare the bar-close price and the bucket end `bar_end_ET`, not the NT8 callback timestamp; a bar whose last second has no print is known later in both worlds).
* **Fill, session, gates, one position, bracket, flat time, cost basis**: identical to L01490 except **bracket 60 pt target / 60 pt stop**. Session London = entry time 02:00 <= t < 08:30 ET.

### 2.3 Last 10 trading days - signals
CSV `autopilot/alt_bar_identity/L02783_signals_last10d.csv` (55 rows = all 4-min EMA30/50 crosses incl. other sessions: 32 taken, 14 skipped_busy, 9 outside the entry window). London in scope = 24 signals, 13 taken, 11 skipped by the all-session busy rule; all 24 match the tape re-derivation at the exact second and tick.
| day | ET second | side | price (lib) | status |
|---|---|---|---|---|
| 01-26 | 04:51:59 / 07:16:01 | short / long | 26401.00 / 26515.50 | taken |
| 01-27 | 03:48:01 | short | 26792.50 | taken |
| 01-27 | 05:48:00 | long | 26813.00 | skipped (busy) |
| 01-28 | 04:43:59 | short | 27082.25 | taken |
| 01-28 | 05:00:00, 05:03:59, 05:07:59, 07:51:59, 07:56:00, 07:59:59 | long, short, long, short, long, short | 27096.25, 27091.00, 27097.25, 27097.75, 27112.00, 27092.75 | skipped (busy) |
| 01-29 | 05:08:00 | short | 27022.75 | taken |
| 01-30 | 06:15:59 | long | 26616.75 | taken |
| 02-02 | 03:11:59 | long | 26191.25 | taken |
| 02-03 | 04:31:59 | short | 26783.00 | taken |
| 02-03 | 07:51:59 | long | 26795.25 | skipped (busy) |
| 02-04 | 04:00:00, 06:15:59 | short, long | 26238.25, 26263.25 | taken |
| 02-04 | 07:48:00 | short | 26232.25 | skipped (busy) |
| 02-05 | 04:19:59, 04:32:00, 04:52:00 | short, long, short | 25812.25, 25904.25, 25848.75 | taken |
| 02-05 | 05:15:59, 06:03:59 | long, short | 25892.25, 25824.75 | skipped (busy) |
Signals inside a trade's life are ignored, so the entry list is the sparse one (the full cross list is in the CSV).

### 2.4 Verification
| scope | library trades | tape trades | exact entry-second+side | exit second equal | pts corr |
|---|---|---|---|---|---|
| all sessions | 1,899 | 1,899 | 98.0% | 100% | 1.000 |
| London, all history | 428 | 429 | 99.3% | 100% | 1.000 |
| London HOLD | 102 | 102 | 100% | 100% | 1.000 |
| London L3M | 51 | 51 | 100% | 100% | 1.000 |
All-session signals: 3,591 tape vs 3,594 library, 3,529 identical (98.3%). Residual 1.7% (1.3% on the clean days): a print near a 4-minute boundary assigned to the next library second by the cumulative-volume matching (a bar close differs by one print -> the cross moves one 4-min bar, 4 minutes later or earlier; tolerance 5 s does not recover it) - **an NT8 build timestamped by the exchange/tape clock should be expected to disagree with the library on about 1-2% of signals in this way, not 0%**; in the last 10 days there is no disagreement in London (53 of 55 all-session crosses match at the second and the tick; the 2 misses are Asia signals on the Sunday-evening label day 20260202).

### 2.5 L3M / L6M / HOLD per contract, trades/week, PAIRFIX D and TW (London, 60/60)
| window | n (trades/wk) | cell M [95% CI] | MDE | control M (n, tr/wk) | D [CI] | TW [CI] |
|---|---|---|---|---|---|---|
| L3M | 51 (3.92) | +9.72 [-4.81, +24.26] | 20.8 | +4.14 (50, 3.85) | +4.45 [-6.78, +18.15] | +5.59 [-9.37, +26.82] |
| L6M | 87 (3.25) | +9.59 [-1.83, +21.00] | 16.3 | +3.03 (85, 3.17) | +4.31 [-3.34, +12.63] | +6.56 [-6.13, +21.82] |
| HOLD | 102 (3.25) | +10.62 [+0.13, +21.11] | 15.0 | +4.04 (98, 3.12) | +4.38 [-2.11, +11.65] | +6.59 [-4.14, +18.93] |
| PRE | 256 (3.52) | +2.39 [-4.94, +9.72] | 10.5 | -0.84 (239, 3.28) | +2.23 [-3.26, +7.43] | +3.23 [-4.62, +11.05] |
| X' | 70 (1.66) | +7.39 [-6.18, +20.96] | 19.4 | +5.22 (73, 1.73) | +0.65 [-2.58, +3.88] | +2.17 [-7.55, +12.13] |
HOLD: win rate 62%, targets 61% / stops 38% / flat 1%; N basis +13.19, P9 stress +10.07. HOLD +10.62 pt x 3.25/wk = +34.5 pt/wk = about +$690/contract/week; the HOLD absolute CI just clears 0 (+0.13) and the paired-vs-1-min D/TW do not. Tier LEAD (HOLD CI includes 0, all recent paired CIs include 0). MDE ~15 pts in HOLD: a difference of +4.4 to +6.6 is 0.3-0.45 of MDE.

## ALT-B 3. Which London entries survive if NT8 trades London only (the ambiguity that moves the result)
Skipped-by-busy counts (London entry-window signals, all-session engine):
| cell | window | London signals | taken | skipped (busy) | blocked by an Asia trade | blocked by an earlier London trade |
|---|---|---|---|---|---|---|
| L01490 | HOLD | 208 | 108 | 100 | 46 | 54 |
| L01490 | L3M | 99 | 52 | 47 | 13 | 34 |
| L02783 | HOLD | 245 | 102 | 143 | 95 | 48 |
| L02783 | L3M | 107 | 51 | 56 | 33 | 23 |
Performance of the London-only engine (flat at 02:00, same rules otherwise): L01490 L3M +9.54 (n 57, 4.4/wk) / L6M +1.54 (116) / HOLD +1.36 [-7.39, +10.12] (135, 4.3/wk); L02783 L3M +3.63 (66, 5.1/wk) / L6M +0.72 (129) / HOLD +2.16 [-6.87, +11.20] (150, 4.8/wk). The Asia-blocked London signals are the weaker ones: the registered numbers rely on an Asia position being open. **State this in the Shadow setup: either run the engine all-session as a ghost (the identity test) or accept the London-only numbers (which are noise).**

## ALT-B 4. Ambiguities in the NT8 specs that would make a build differ (all verified against the harness unless stated)
1. **L02783 grouping**: spec says "rounded to 3 bars of 2m"; scored = 2 bars (4-min). See ALT-B 2.1. Any 6-min build reproduces 0% of the trades.
2. **One-position rule across sessions** (ALT-B 3). The spec lines "London 02:00-08:30 ET" do not say the engine also runs 18:00-02:00 and that a still-open Asia trade blocks London.
3. **No exit on opposite cross / no reverse**: signals while in a position are ignored; the position leaves only by stop, target or 16:55 flat. 48% (L01490: 100 of 208) and 58% (L02783: 143 of 245) of the London signals in HOLD are such ignored crosses.
4. **Volume-bar counting**: whole-print (no split), overshoot discarded, counter restarts at the 18:00 ET first print of each label day, last unfinished bar never closes, 'N'-side opening prints counted, aggressor ignored, ticks (prints) not "trades by order". If the NT8 volume bar counts prints differently (merges fills of one aggressor order, or splits a large print across bars and carries the remainder - verify what the NT8 Volume bar type does on your feed), the bar phase of the whole day moves and every signal time after that differs. For the identity test confirm the volume-bar build **does not split** and includes every print from 18:00:00.000.
5. **Session start / replayed-hour defect**: on 11 label days (the first label day of 11 months, incl. 20260202 in the last-10 window) the library replays the first 1-2 hours (ALT-A 0 item 2), which moves the volume-500 phase of the whole day and the 4-min bars of the first hours. A de-duplicated tape is the right definition; CSV rows on 20260202 are flagged (`lib_only` rows are not identity targets; London signals of that day are unaffected). Fix = de-duplicate and rebuild the store (not done).
6. **Back-adjusted vs unadjusted prices**: library prices = raw + per-contract offset; EMA crosses are invariant to the constant but NOT across a roll inside the EMA memory. NT8 on a single contract (or merge-adjusted) series may differ around roll weeks (quarterly, 3 roll days are missing from the library: 20250617, 20250917, 20251216).
7. **Decision second vs NT8 bar-close event**: the harness decides at the library second of the completing print (volume) or the last second of the bucket (time bars: first print second >= t1-1) and fills at the close of that second +/- 1 tick; NT8 would act on the completing print (volume) or the first tick of the next bucket (time). Use signal time/price (bar close) for identity, not fills.
8. **Fill model**: the harness fill is end-of-second last print +/- 1 tick; target never filled in the fill second; stop wins ties; stop/time/target slippage and the fee are post-hoc cost terms in 'M' (target cost 4.3 pt in 2026 is a flat model term, not an order-type simulation).
9. **EMA seed / warm-up**: first value = first close; no bar-count threshold before the first cross (the library emits a cross as soon as the sign flips, including in the first bars); in NT8 `BarsRequiredToTrade` must be set low enough, but any seed >= ~2 days gives identical crosses.
10. **Entry window 18:00-15:15 ET** and the 16:55 flat are in label-day ET clock (DST handled by the ET conversion); the London cell clock is entry time (D + 1 s), not bar open time.
11. **Lots**: per-contract numbers only; the live lot for a new book is not set (an assumption of the stack tables).
12. **Measuring statistic**: PAIRFIX's PRE and X' D values for wave-1 rows are 2x the true value (the S and L daily tables both contain PRE/X' days and were concatenated; n_cell is exactly 2 x n_P on all 25 wave-1 rows; HOLD/L6M/L3M are single-counted and correct, TW is a ratio and unaffected). My PRE D for L01490 is +3.26 (PAIRFIX +6.53), X' +1.50 (+2.99); L02783 PRE +2.23 (+4.47), X' +0.65 (+1.29). The selection windows are not affected in sign, only in D magnitude/SE; the HOLD-based tier changes stand. Flagging for the PAIRFIX owner.

## ALT-B 5. One-line status
L01490 Volume-500 London: LEAD, Shadow only; HOLD +4.46 (CI includes 0), gain over 1-min control +0.3 (D) / -0.3 (TW); identity data ready (CSV, 20/20 London signals reproduced at the second). L02783 2-min-G (= 4-min EMA30/50) London: LEAD, Shadow only; HOLD +10.62 (CI +0.13..+21.1) but +4.4 over the 1-min control (CI includes 0); build it as a 4-min chart with the all-session ghost position. Both: the London-only version has no edge in L6M/HOLD.
