# SHADOW_READINESS - readiness check of the five SHADOW-2 lines and the Monday table (DIS-AY, CAL, 2026-11-04)
Research-side check only; nothing live; no PASS claims. Code `l2vast/ds3/code/discover/{dias_shadow_readiness.py, dias_shadow_readiness2.py}` (both import the existing `zones3/shadow2/` modules unchanged); outputs `/mnt/l2/l2vast/ds3_base4/shadow_ready/` (readiness.json, readiness2_tables.txt, stream_signals.pkl, registers, monday_dry.txt). 6 workers, whole check about 1 minute.

## 0. Verdict
The five streaming books (`shadow2_books.py`, fed one closed 1-minute bar at a time, no later bar visible) reproduce the research trade lists with **diff 0 for the last two research weeks (label days 2026-10-19..2026-10-30) on all five lines** (row counts, sides, stops, targets, time stops, lots, and the 1-s outcomes in the weekly runner), and the signals up to a cut-off are **unchanged when the feed is truncated at that cut-off** (no look-ahead). Three operational gaps found between the streaming books and the Monday table (section 4), none in the books themselves: (G1) the register has no `day_complete` and the runner does not drop early-close / holiday signals, (G2) the unified Monday runner passes no tape to any Shadow runner, (G3) the weekly-feed tape that `hm_feed.py` writes cannot be read by the Shadow runners (`high/low` vs `hi/lo`).

## 1. Last two research weeks: streaming signals vs the research trade lists
Feed: 1,320,115 one-minute bars (Q13, DIS-K: `nq_min.npz`) / 1,311,620 (DIS-B, DIS-E, DIS-C: `ds3_fade/minute.parquet`; DIS-E also the table RF), 2023-02 .. 2026-10-30; each bar is given to the book only after it closes. Research lists built by the research code (`verify_shadow2.research`). Window = label days 2026-10-19..2026-10-30.
| line | week 1 (10-19..10-23) stream / research | week 2 (10-26..10-30) stream / research | matched on (sec, side) | max field diff (stop, tgt, tstop, lots) | only stream / only research | `day_complete=False` in window |
|--|--|--|--|--|--|--|
| Q13GAP_T1 | 3 / 3 | 3 / 3 | 6 of 6 | 0.0 | 0 / 0 | 0 |
| DISK_BO_CH | 5 / 5 | 2 / 2 | 7 of 7 | 0.0 | 0 / 0 | 0 |
| DISB_PREL | 0 / 0 | 1 / 1 | 1 of 1 | 0.0 | 0 / 0 | 0 |
| DISE_PDF | 1 / 1 | 3 / 3 | 4 of 4 | 0.0 | 0 / 0 | 0 |
| DISC_SUN30 | 1 / 1 | 1 / 1 | 2 of 2 | 0.0 | 0 / 0 | 0 |
(DIS-C counts the Sunday 18:30 signal under the following Monday label day.) The streaming ATR equals the feed ATR to 0.0 on every line (whole history).
**Causal check (no look-ahead):** each line replayed three times, on the full feed, on the feed cut at 2026-10-23 17:30 ET (end of week 1) and on the feed cut at 2026-10-16 17:30 ET. Signals with time up to each cut: Q13 280 / 277, DIS-K 292 / 287, DIS-B 388 / 388, DIS-E 322 / 321, DIS-C 188 / 187 in the full and the truncated run; **symmetric difference 0 and max field difference 0.0 in all ten comparisons**. A signal therefore never depends on a bar after its own decision time.
**Whole history (2023-04-03 on), for context:** every research row is matched (0 missing) on all five lines; streaming extras: Q13 8, DIS-K 12, DIS-B 1, DIS-E 0, DIS-C 0, all flagged `day_complete=False` by the book (section 2).

## 2. Early closes and holidays (`day_complete`)
- The books flag `day_complete` only at the NEXT rollover (the research day filter needs end-of-day facts: Q13 >= 300 RTH bars ending 15:59; DIS-K a full 5-minute bucket set and >= 20,000 seconds with prints; DIS-B >= 300 pre-market bars and the 09:30 bar). At the signal time the book cannot know; it logs the signal and, later, the flag.
- Extras by day (all `day_complete=False`): Q13 20230529, 20230703, 20240219, 20240619, 20241224, 20250120, 20250703, 20250704 (all on the CME holiday / early-close calendar); DIS-K 10 of 12 on calendar days (20230529, 20230619, 20240115, 20240219, 20240703, 20240704, 20241224, ...) plus 20231211 and 20260615, which are NOT calendar days (fewer than 20,000 seconds with prints: needs D7's per-minute `nsec`); DIS-B 20230407 (Good Friday). DIS-E and DIS-C have no extras; they do trade on calendar days and the research keeps them (6 DIS-E and 16 DIS-C streamed signals fall on calendar holidays / early closes and match research rows).
- **Windows with early closes** (register written from the streaming signals, weekly runner replay on the 1-s path, vs the research list after the one-position rule):
| window | raw register (all streamed signals) | calendar exclusion (Q13, DIS-K, DIS-B on EARLY_CLOSE/HOLIDAY days) | exclusion by the book's own `day_complete` flag |
|--|--|--|--|
| 2024-12-23..2025-01-03 (Christmas Eve 12-24) | Q13 3 vs research 2 (runner -181.4 pt vs -155.8), DIS-K 6 vs 5 (-40.8 vs -84.9), others equal | equal on all five lines | equal on all five lines |
| 2025-06-30..2025-07-07 (Jul 3 early close, Jul 4) | Q13 5 vs 3 (-41.6 vs -35.9), others equal | Q13 equal, **DIS-B 3 vs research 4 (over-excluded: a valid research pre-market signal on a calendar day), net 15.4 vs -13.7** | equal on all five lines |
| 2026-10-19..2026-10-30 (no early close) | equal | - | equal |
**Conclusion:** the flag from the book is the correct filter (diff 0 in every window); a blanket calendar list is wrong for DIS-B (and for DIS-E / DIS-C, which keep holiday signals). The runner today applies neither (G1).
- Forward calendar for the D7 owner (DISCOVER_CALENDAR.csv, rule-derived, verify against CME): 2026-11-26 13:00 Thanksgiving halt; 2026-11-27 13:15; 2026-12-24 13:15; 2026-12-25 closed; 2027-01-01 closed; 2027-01-18 MLK 13:00; 2027-02-15 Presidents Day 13:00; 2027-03-26 Good Friday closed.

## 3. Register round trip, weekly runner and the Monday table
- The streamed signals of the last two weeks were written with `shadow_register.log_signal(**shadow2_books.log_args(sig))` (the same writer D7 uses) into a temporary register and read back by `shadow2_weekly.py` with a 1-s tape: **runner trades 6 / 7 / 1 / 4 / 2 = research rows after the one-position rule, net points equal to 0.01 on every line (193.85, 51.71, 32.28, 272.97, 100.59)**; verdict rows `EARLY (keep logging)` for all five, SPRT LLR 0.18 / 0.06 / 0.05 / 0.29 / 0.14 (bounds ±2.20), weeks-to-decision as in SHADOW_PACK_2.
- **Monday table:** `monday_all.py --dry --force` with `MONDAY_FR` pointing at that register runs all seven runners with rc=0, but the five SHADOW-2 rows read `no data yet / no signals logged since the start` although 20 signals are in the register (G2). The same runner called with `--tape` prints the five populated rows (`shadow2_runner_with_tape.txt`).

## 4. Gaps between the streaming books and the Monday table (decisions for BASE-4 / ZL-1; nothing changed here)
| id | finding | evidence | proposed fix (owner) |
|--|--|--|--|
| G1 | the register has no `day_complete`; `shadow_register.log_signal` does not carry it and `shadow2_weekly.py` has no early-close / holiday exclusion although SHADOW_PACK_2 section 7.3 says the runner drops them | raw register overcounts on early-close windows (above) | write a sidecar `<LINE>_daycomplete.csv` (label_day, day_complete 0/1) at each rollover and drop signals with day_complete = 0 in `shadow2_weekly.run` (ZL-1). Not a calendar list |
| G2 | `monday_all.py` calls no Shadow runner with `--tape`; `fade_forward_weekly.load_path(None)` returns the history-only path (ends 2026-10-30), so live signals get no outcome and the rows stay "no data yet" | section 3 | add `--tape {FR}tape.csv` to the `s2` entry in runners.json once the tape exists, and give the built-in jobs (BT, NYAM, fade, sizer) the same argument or make `load_path(None)` use `<FR>tape.csv` when present (BASE-4 owns `monday_all.py`; I did not touch it) |
| G3 | `hm_feed.py` writes the register tape as `sec, high, low, close`; `fade_forward_weekly.load_path` and `nyam_forward_weekly.load_harness` read `sec, hi, lo, close`. Reproduced: a tape in the hm_feed format raises `AttributeError: 'DataFrame' object has no attribute 'hi'` | tape_hmfeed_format.csv vs tape_runner_format.csv | rename `high/low` to `hi/lo` in `load_path` / `load_harness` (or write both from hm_feed). The live monitor now accepts all three layouts |
| G4 | DIS-K day validity needs D7's per-minute `nsec` (seconds with prints); without it 2023-12-11 and 2026-06-15 differ (2 of the 12 DIS-K extras are not calendar days) | whole-history table | D7 logs `nsec` per minute or the day flag is finalised from the 1-s tape in the runner |
| G5 | DIS-E needs D7's refill-failure count RF; this check used the table RF (`dise_minute.parquet`), so the 4 window rows prove the logic, not D7's RF | SHADOW_PACK_2 section 7.1 | first live weeks: compare D7 RF with the table RF on an overlap day |

## 5. Exact commands
Replay check (research side, about 1 minute, 6 workers):
```
cd l2vast/ds3/code/discover
python3 dias_shadow_readiness.py 6      # streaming replays, causal truncation, diff vs research, whole-history day_complete table -> /mnt/l2/l2vast/ds3_base4/shadow_ready/readiness.json
python3 dias_shadow_readiness2.py       # register round trip, weekly runner with a 1-s tape, early-close windows (raw / calendar / flag), Monday table dry run
python3 l2vast/ds3/code/zones3/shadow2/verify_shadow2.py [LINE ...]   # the original whole-history diff (SHADOW_PACK_2 section 3)
```
D7 integration (per closed 1-minute bar, in this order; `x` is the context object of the line, `FB.Ctx()` for Q13 / DIS-K and `SB.CtxG()` for DIS-B / DIS-E / DIS-C):
```
import shadow2_books as SB, fade_books as FB, shadow_register as SR     # code/zones3/shadow2, fade_shadow, discover
x.on_bar(minute_index, o, h, l, c, v)                                    # minute_index = epoch seconds // 60 of the bar start
for sig in book.on_bar(x[, RF_for_this_minute]):                          # RF only for DISE_PDF and DISK_BO_CH (None-safe 0 otherwise)
    SR.log_signal('forward_register/shadow2', **SB.log_args(sig), by='D7_shadow')
# at the end of each label day: book._finalize() / book._final() (day_complete), and write the sidecar flag (G1)
```
Weekly (what the Monday runner should execute for this plugin once G1-G3 are closed):
```
python3 -I l2vast/ds3/code/zones3/shadow2/shadow2_weekly.py --regdir forward_register/shadow2 --start 2026-11-04 --tape forward_register/tape.csv
MONDAY_FR=forward_register/ python3 -I .../zones3/standing/monday_all.py --dry --force      # dry run of the whole Monday table, writes nothing
```
Tape format for every runner: csv/parquet with columns `sec, hi, lo, close` (one row per second with prints, contract frame), until G3 is fixed.
