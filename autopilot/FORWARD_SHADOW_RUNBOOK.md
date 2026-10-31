# FORWARD_SHADOW_RUNBOOK - starting the shadow register (one page + REG-1 additions; SH-2 2026-10-31, updated by REG-1 after the user's 14:30Z answers)

Rule of the register: shadow rows only observe. Nothing here places, changes or cancels an order. Real rows before **Sun 2026-11-01 18:00 ET (23:00Z)** are refused by every tool. No account numbers or credentials in any file (the joiner drops such columns; the Output-log parser never copies a line that mentions an account).
Folder: `shadow_register/incoming/` (create the same folder on the box that runs D6 and copy files across; code: `l2vast/ds3/code/shadow/`). Pre-REG-1 copies of every file touched: `autopilot/bak_reg1_20261031_1436/`.

## User answers now built in (2026-10-31 14:30Z; D6 v2.3b as coded)
| item | answer | where it lives |
|---|---|---|
| Stop A/B parity | DAY-OF-MONTH of the exchange trade date: odd = Native A, even = JoinThenMarket B (Mon 11-02 even = B) | `fills_join.ARM_PARITY='dom'` |
| PE R1 reading | research reading: a pattern up to 10 min before the signal counts, once >= 26 pre-bars are logged | `replay_offline --min-prebars 26` (default); `--spec-first-event` = sensitivity only |
| ER lots | `Math.Max(1, Floor(lots*mult + 0.5))`, integer version is the headline | `d6_state.hyp_lots(..,'half_up')` |
| Paper-log books | YES (S6 W6 MA6 C6 ...) | log rule, spec section 0 |
| A6 | = PB7 (PbEngine Pb7Rules, 10-min Supertrend regime, ATR0.5 depth level, T1 close-back), NOT PB3B/PB | spec, book map |
| Lots/sessions | K6 2 Asia/London/NY-AM/NY-PM; P6 7 Asia/London/NY-AM; U6 4 Asia/London; H6 4 Asia, 2 NY-AM; M6 2 London/NY-AM; A6 1 Asia; O6 1 | `d6_book_defaults.json` |
| D6 locks | BookR = BASE lots x SizeMult x stop x $20; SizeMult = running max per book per day (reset 18:00 ET); $ day locks x same SizeMult; week lock same BookR | spec (offline lock-engine replays use ss2_lib causal running max) |
| Split | one panel setting (group 05) for all gated books; K6 keeps the split Sunday; D6 ignores THP entry lines (P6 splits 70/30) | spec |
| Slippage labels | model +0.25/lot, stress +0.45 | labels on offline replays |
| Log writer | D6 v2.4 AFTER Sunday; v2.3b prints one Output-log line per signal incl. SKIPPED + reason | week-1 route below |
| HM feed | weekly NQ.v.0 ohlcv-1s ~$1.15/wk YES from Sat 11-07; raw MBO NO | `HM_FORWARD_FEED.md` section 6 |

## Sunday night (before 18:00 ET) - platform owner / D6 owner
1. **D6 v2.3b (Sunday): no structured writer.** Keep the NT8 Output window text of every session (copy/save the whole text each evening to `incoming/d6_output_YYYYMMDD.txt`; no account text needed - lines that mention an account are skipped by the parser). Do not clear the window mid-session. When D6 v2.4 arrives, switch to the CSV writer exactly as `autopilot/D6_LOG_WRITER_SPEC.md` (checklist at its end): append-only `signals.csv`, `pe45_bars.csv`, `stack_events.csv`, `stops_d6.csv`; log EVERY signal of every book, taken or not; blank + reason when a state is not computable, never 0. Shadow code is read-only and fail-open.
2. (v2.4) P6: keep the 45-s bar series (26 bars before each signal, every bar until the live exit or the 16:55 ET flatten, not 40 min). In week 1 the same bars are rebuilt from the HM 1-s feed (below).
3. Stop A/B (R7) from Monday 2026-11-02: order type by trade DATE (odd day-of-month = Native stop-market A, even = JoinThenMarket 3 s B; Mon 11-02 even = B, Tue 11-03 A, ... 11-30 even = B, 12-01 odd = A; 12-31 and 01-01 are both odd = A,A). No other ON-set change in those books during the test (`live_config_ver` changes start a new scoring segment).
4. Nightly exports (below). Test once on Sunday with an empty file set: `python3 run_register.py` must say `MISSING signals.csv`, not crash.

## Every evening (or Monday morning for the weekend) - what to drop where
| file | from | content |
|---|---|---|
| `incoming/d6_output_*.txt` | platform owner (v2.3b, week 1) | the Output-window text, whole sessions |
| `incoming/signals.csv`, `pe45_bars.csv`, `stack_events.csv`, `stops_d6.csv` | D6 v2.4 (append) | schema `autopilot/shadow_log_schema.csv` |
| `incoming/fills.csv` | platform owner | trade_id, book, side, qty, price, time (epoch ms UTC), order_type (+ fee_usd, reject); `autopilot/FILLS_CSV_SCHEMA.md`. Optional in week 1: without it the register runs, live outcomes stay blank and the delta rules are unscored |
| `incoming/tape.csv` | platform owner (optional now) | sec (epoch s UTC), high, low, close, only seconds with a print. **If absent, `run_register.py` builds it from the verified weekly HM ohlcv-1s files** (`data_fwd/MANIFEST.jsonl`); an incoming tape always wins |

## Monday morning - week 1 (Output-log route, v2.3b)
```
cd l2vast/ds3/code/shadow
PY=<repo>/.venv/bin/python3
cat ../../../../shadow_register/incoming/d6_output_*.txt > /tmp/d6_week.txt      # or any scratch path
$PY parse_d6_output_log.py /tmp/d6_week.txt --dry-run --strict --show-unknown 20     # grammar check: must read unknown D6-like 0, ambiguous 0
$PY parse_d6_output_log.py /tmp/d6_week.txt --strict --out ../../../../shadow_register/work/log_parsed --emit-register ../../../../shadow_register/incoming
$PY run_register.py
```
Until the real Output-log lines have been seen, the grammar is a guess (MORNING.md asks for 20-30 sample lines); a dry strict run that fails is the expected first result. `--emit-register` writes `signals.csv` (+ an empty-or-parsed `fills.csv`) in the register schema; stop/target distances come from the log if it prints them, otherwise from `d6_book_defaults.json` (NOT known to us: fill them in, points; rows without them cannot be replayed). `run_register` then (a) joins fills if any, (b) builds the tape from the HM feed, (c) computes ER / hypothetical lots / second_fire30 from the tape (`enrich_from_tape.py`, UNAUDITED vs D6), (d) rebuilds the P6 45-s bars from the tape (`tape_to_pe45_bars.py`, UNAUDITED; 100% h/l/c match to the research bars on Jan 2025 history), (e) replays R1/R5, (f) scores. The audit line for R1 is then `n/a (tape-built)`.
## Monday morning - week 2 onward (v2.4 CSVs) - one command
```
cd l2vast/ds3/code/shadow
<repo>/.venv/bin/python3 run_register.py          # joins fills, replays R1/R5, scores
```
It writes `shadow_register/work/{signals_joined.csv, stops.csv, cf_results.csv, join_report.json, weekly_lines.txt, hm_feed_report.txt, tape_hm.csv, stop_ab_*.csv}` and prints the weekly lines. Paste the printed block into MORNING.md (the HM forward-register slot). HM feed verification (sha256, row counts, continuity) is printed first; a FAIL there means the tape is not used.

## What can be scored from the Output log alone in week 1 (R1-R9)
Output-log signals give: book, time, side, price, taken / SKIPPED + reason (and, if printed, lots, stop and target). Everything else comes from the HM 1-s tape (exists from the Sat 11-07 pull, so the first scored week is read on Mon 11-09) and, for dollars and the live comparison, the fills.
| rule | week 1 from Output log + tape | needs fills (live outcome) | waits for week 2 / v2.4 |
|---|---|---|---|
| R1 PE45 | YES for fire rate, events, hypothetical limit entry (bars rebuilt from the tape, needs P6 stop/tgt) | delta vs the live fill needs fills.csv | audit vs D6's own bars; the first signals after the Sunday open have < 26 pre-bars (`pre_mode=spec`, flagged) |
| R2 KB ER>=.2 / R3 ER>=.3 | YES for ER, fire rate, hypothetical integer lots (ER from tape 5-min closes, unaudited) | ppl delta = (mult-1) x live result: needs fills | `er_mismatch` audit (needs D6's logged ER) |
| R4 8-line zone | NO (lines need history before the floor: 1-h kijun 26 h, 4-h Keltner ~4 days, previous-day mid and RTH Camarilla; the feed starts 11-01 22:00Z) | - | v2.4 rolling file, or the feed after ~2 weeks of warm-up; counts of fresh lines only |
| R5 Asia-stopped cut50 | PARTIAL: hypothetical stop events of TAKEN signals can be replayed from the tape if stop/tgt/lots are known | real stop times and the other books' open lots need fills / stack_events | v2.4 `stack_events`; 76% of the research gain is the lock-engine effect (offline engine, not the weekly line) |
| R6 2nd-signal skip | YES (signals only, outcome of the previous signal from the tape base trade = the research definition) | $ at live lots needs fills | audit vs D6's `second_fire30` |
| R7 stop A/B | NO (arm schedule and any parsed stop lines only) | YES: real stop fills + order types | `stops_d6.csv` run-past-stop |
| R8 ES-lead (paper) | NO | - | ES 1-s feed is not bought (the NQ-only HM feed does not carry it; ES ohlcv-1s would be ~$1.0/wk) or the weekly L2 buy |
| R9 HM FVG | NO (history needed; default OFF) | - | v2.4 daily FVG file |
Counts (signals per book/session, taken vs SKIPPED, top SKIPPED reasons) come from the Output log in week 1 for ALL rules and are the real week-1 deliverable: the check that D6 logs what we think it logs.

## What the Monday scorer prints (first weeks: mostly counts, decisions are not yet allowed)
```
FILLS JOIN: closed N, open N, anomalies N, taken-without-fills N, unmatched fills N, ... stops rows N      <- must read: anomalies 0, unmatched 0
HM FEED week ..: OK rows=.. ; continuity ..; HM FEED: n week file(s), all checks OK
SHADOW REGISTER week 2026-W45 (1 wk, S signals, T taken); audit er_mismatch .., zone_mismatch .., pe45_mismatch ..   <- each must be < 0.005, else that rule's week is void (n/a on the tape route)
SHADOW PE 45s 3-bar: n=.. fire=..% (../wk); +x.xx ppl/sig (se, p); per-contract a->b; stack $/wk live-lots, $/wk research-lots [status; W=1/66]
SHADOW KB ER>=.2 sizer / ER20>=.3 sizer / 8-line zone skip / Asia-stopped cut50 / 2nd-signal skip / ES-lead (paper) / HM FVG skip   (same format)
STOP A/B: A n=.. mean=.. (CI), B n=.. mean=.. (CI), join fill .., rejected .., diff(B-A) .. p .., deviations ..
```
Status words: `TOO EARLY (<13 wk)` for the first 13 weeks on every rule (no harm/futility call before then), then SHADOW / OFF-HARM / OFF-FUTILE / ON-eligible (needs weeks >= W_on, effect >= half the research estimate, Holm p < 0.05, positive stack, fire rate 0.5-2x research, audit < 0.5%). `NO_CF` = tape or bars missing for R1/R5; `NO_DATA` = the field is not logged/derivable yet. A rule line is never turned ON by the tool: ON is the user's decision.
Week 1 sanity checks (these are the real tests of the plumbing): audit mismatches 0; blank rate of ER / zone / PE45 fields small and explained; `deviations 0` in STOP A/B (a deviation = order type does not match the day's arm); join report `taken-without-fills` = 0 once fills exist; fire rates within about 0.5-2x the research (PE ~0.7, zone ~0.12, 2nd-signal ~0.07).

## Open questions
1. ANSWERED (research reading), 2. ANSWERED (day-of-month), 4. ANSWERED (half up, min 1), 3. (fills `side` = the fill's own direction BUY/SELL; a join placed but not filled shows as a `stop_join` row with qty 0): answered "yes" in the user's reply.
5. NEW, in MORNING.md (one question): 20-30 real lines of the D6 v2.3b Output log, plus whether stop/target distances are printed on the signal lines, so the grammar in `d6_output_patterns.json` can be fixed.
