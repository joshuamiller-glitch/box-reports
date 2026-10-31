# FORWARD_SHADOW_RUNBOOK - starting the shadow register (one page; SH-2, 2026-10-31)

Rule of the register: shadow rows only observe. Nothing here places, changes or cancels an order. Real rows before **Sun 2026-11-01 18:00 ET (23:00Z)** are refused by every tool. No account numbers or credentials in any file (the joiner drops such columns).
Folder: `shadow_register/incoming/` (create the same folder on the box that runs D6 and copy files across; code: `l2vast/ds3/code/shadow/`).

## Sunday night (before 18:00 ET) - platform owner / D6 owner
1. Turn on the D6 shadow log writer exactly as `autopilot/D6_LOG_WRITER_SPEC.md` (checklist at its end): append-only CSVs `signals.csv`, `pe45_bars.csv`, `stack_events.csv`, `stops_d6.csv` (optional but wanted: real trigger time and run-past-stop). Log EVERY signal of every book, taken or not; blank + reason when a state is not computable, never 0. Shadow code is read-only and fail-open (spec section 4).
2. P6 only: from the Sunday open keep the 45-s bar series (26 bars before each signal and every bar until the live exit or the 16:55 ET flatten, not 40 min).
3. Stop A/B (R7) from Monday 2026-11-02: order type by trade date (odd date = Native stop-market A, even = JoinThenMarket 3 s B; Mon 11-02 is even = B). No other ON-set change in those books during the test (`live_config_ver` changes start a new scoring segment).
4. Set up the nightly exports (below). Test once on Sunday with an empty file set: `python3 run_register.py` must say `MISSING signals.csv`, not crash.

## Every evening (or Monday morning for the weekend) - what to drop where
| file | from | content |
|---|---|---|
| `incoming/signals.csv` | D6 (append) | schema `autopilot/shadow_log_schema.csv`, table signals |
| `incoming/pe45_bars.csv`, `stack_events.csv`, `stops_d6.csv` | D6 (append) | tables pe45_bars, stack_events; stops_d6 = signal_id, ts_trigger_ms, stop_level, run_past_stop_pts |
| `incoming/fills.csv` | platform owner | columns trade_id, book, side, qty, price, time (epoch ms UTC), order_type (+ optional fee_usd, reject); one row per fill slice; `autopilot/FILLS_CSV_SCHEMA.md` |
| `incoming/tape.csv` | platform owner | 1-second print tape of the front month: sec (epoch s UTC), high, low, close, only seconds with a print; must reach at least to the 16:55 ET flatten of the last replayed day (else R1/R5 rows are `missing_tape`, excluded, never zero) |

## Monday morning - one command
```
cd l2vast/ds3/code/shadow
<repo>/.venv/bin/python3 run_register.py          # joins fills, replays R1/R5, scores
```
It writes `shadow_register/work/{signals_joined.csv, stops.csv, cf_results.csv, join_report.json, weekly_lines.txt, stop_ab_*.csv}` and prints the weekly lines. Paste the printed block into MORNING.md (the HM forward-register slot).

## What the Monday scorer prints (first weeks: mostly counts, decisions are not yet allowed)
```
FILLS JOIN: closed N, open N, anomalies N, taken-without-fills N, unmatched fills N, ... stops rows N      <- must read: anomalies 0, unmatched 0
SHADOW REGISTER week 2026-W45 (1 wk, S signals, T taken); audit er_mismatch .., zone_mismatch .., pe45_mismatch ..   <- each must be < 0.005, else that rule's week is void
SHADOW PE 45s 3-bar: n=.. fire=..% (../wk); +x.xx ppl/sig (se, p); per-contract a->b; stack $/wk live-lots, $/wk research-lots [status; W=1/66]
SHADOW KB ER>=.2 sizer / ER20>=.3 sizer / 8-line zone skip / Asia-stopped cut50 / 2nd-signal skip / ES-lead (paper) / HM FVG skip   (same format)
STOP A/B: A n=.. mean=.. (CI), B n=.. mean=.. (CI), join fill .., rejected .., diff(B-A) .. p .., deviations ..
```
Status words: `TOO EARLY (<13 wk)` for the first 13 weeks on every rule (no harm/futility call before then), then SHADOW / OFF-HARM / OFF-FUTILE / ON-eligible (needs weeks >= W_on, effect >= half the research estimate, Holm p < 0.05, positive stack, fire rate 0.5-2x research, audit < 0.5%). `NO_CF` = tape or bars missing for R1/R5; `NO_DATA` = the D6 field is not logged yet. A rule line is never turned ON by the tool: ON is the user's decision.
Week 1 sanity checks (these are the real tests of the plumbing): audit mismatches 0; blank rate of ER / zone / PE45 fields small and explained; `deviations 0` in STOP A/B (a deviation = order type does not match the day's arm); join report `taken-without-fills` = 0; fire rates of each rule within about 0.5-2x the research (PE ~0.7, zone ~0.12, 2nd-signal ~0.07).

## Open questions (also in MORNING.md)
1. R1 reading: research limit also takes a three-bar pattern that completed up to 10 min before the signal and is not yet mitigated (19% of PE fills; needs the 26 pre-signal bars) vs the SH-1 wording 'first pattern after the signal only'. Default: research reading when 26 pre-bars are logged.
2. Stop A/B date parity: ordinal parity (odd ordinal = A) vs day-of-month parity; identical on 2026-11-02, differ only across the 31st to the 1st.
3. Fills `side` = the fill's own direction (BUY/SELL), and a join that was placed but not filled shows as a `stop_join` row with qty 0.
4. Integer-lot rounding for the ER sizer (D6 rule) for `hyp_lots_er`.
