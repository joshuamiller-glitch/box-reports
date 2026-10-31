# REG1_CHANGES - what REG-1 changed (2026-10-31, after the user's 14:30Z answers)

Nothing deleted: every edited file was copied first to `autopilot/bak_reg1_20261031_1436/` (specs, runbook, schema docs, `pull_nov.py`, `shadow_files.sha256`) and `l2vast/ds3/code/shadow/bak_reg1_20261031_1436/` (all shadow code). Leaderboards: `LEADERBOARD.md.bak_<time>`, `TREND_LEADERBOARD.md.bak_<time>`. No data after 2026-02-06 was read (tests use synthetic inputs and the existing capped 45-s bar store, Jan 2025 only); no credentials; no purchase; the register floor 2026-11-01 18:00 ET is refused by every new tool.

## 1. User answers applied
| answer | change |
|---|---|
| Stop A/B parity = day-of-month (odd = Native A, even = JoinThenMarket B) | `fills_join.ARM_PARITY = 'dom'` (was ordinal); `make_synthetic_log` uses the day; FORWARD_SHADOW_SPEC (R7 row + REG-1 block), FORWARD_STOP_AB.md, FILLS_CSV_SCHEMA.md, D6_LOG_WRITER_SPEC (`arm_assigned`), RUNBOOK. Mon 11-02 is B either way; the two rules differ only across 31 -> 1 (12-31 and 01-01 are both A). |
| PE R1 = research reading once >= 26 pre-bars | already the replay default (`--min-prebars 26`); spec R1 row now says log 26 pre-bars and every bar to exit/flatten (not 40 min); D6 spec C3 marked DECIDED; the SH-1 reading stays as `--spec-first-event` sensitivity. |
| ER lots half-up, min 1 | `d6_state.hyp_lots(...,'half_up')` is now `max(1, floor(x+0.5))` (identical on all D6 lot/mult pairs; the test asserts 1-lot cases); `floor1` kept as a labelled sensitivity; spec + D6 writer spec text updated (`lot_rule = half_up`). |
| Paper-log books YES; A6 = PB7; lots/sessions; SizeMult running max and BookR; split panel setting; slippage labels | spec "REG-1 update" block (overrides older wording), `d6_book_defaults.json` (lots by session), runbook table. |
| Log writer = v2.4 after Sunday | D6_LOG_WRITER_SPEC and runbook say so; register not blocked (item 2). |
| HM weekly ohlcv-1s feed YES from Sat 11-07 | item 3. |
| Leaderboard: keep tier + add capped column | item 4. |

## 2. Output-log route for week 1 (new code, all synthetic-tested; format of the real log still UNKNOWN)
* `shadow/parse_d6_output_log.py` + `d6_output_patterns.json` (edit patterns there only): classes skipped / taken / signal / fill / stop / session / ignore with macros for timestamp, book (alias map: KB=K6 PE=P6 SM=U6 HM=H6 MV=M6 PB7=A6 ST=S6 WT=W6 MA=MA6 CR=C6), side, price, reason; verdict lines are linked to the signal line of the same book within 5 s; unknown-line counters (shape-masked, D6-like unknowns separated); ambiguity counter; lines that mention an account are counted and never copied; real rows before the floor are refused (`--synthetic` marks test rows); `--dry-run` writes nothing; `--strict` exits 3 on any unknown D6-like line, ambiguity, bad timestamp, signal without verdict, pre-floor row, unmapped book. `--emit-register DIR` writes `signals.csv` / `fills.csv` in the register schema (unknown fields blank; stop/target from the log else `d6_book_defaults.json`, where they are still null).
* `shadow/enrich_from_tape.py`: ER(20) 5-min, multipliers, integer hypothetical lots and `second_fire30` from the 1-s tape (unaudited vs D6). `shadow/tape_to_pe45_bars.py`: P6 45-s bars from the tape (h/l/c identical to the research 45-s store on all 39,549 bars of Jan 2025; open comes from the vendor bar). `shadow_score.py`: optional schema columns missing from the file are blank (NO_DATA), new `--no-pe45-audit`. `run_register.py`: fills.csv optional.
* Tests: `test_parse_d6_output_log.py`, `test_enrich_from_tape.py`, `test_hm_feed.py` pass; `test_fills_join`, `test_shadow_score`, `test_replay`, `test_d6_state` re-run after the edits: all pass, 0 FAIL lines (final run 2026-10-31 ~15:15Z).
* Which rules can be scored in week 1 from the Output log (+ the HM 1-s tape): see the table in FORWARD_SHADOW_RUNBOOK.md. Short form: counts for all; R1, R2, R3, R6 as tape-derived (unaudited) fire rates and hypothetical lots; their dollar/ppl deltas need fills.csv; R5 partial; R4, R7, R8, R9 wait (history/fills/ES feed/v2.4).
* Question for the user (MORNING.md): 20-30 sample lines of the real Output log and whether stop/target distances are printed.

## 3. HM weekly feed
* `HM_FORWARD_FEED.md` section 6: exact weekly commands with the window table (Sat 11-07 first), cost/record sanity checks, `--max-usd 2.00` for the standing OK, verification, budget-log step, failure handling.
* `shadow/hm_feed.py --verify`: manifest sha256 of the dbn and the path parquet, row count vs `path_rows`, floor, contiguity (start = previous end), continuity with the prior week (hours between last and first print, gap/overlap/roll flags). `hmfwd/log_spend.py [--apply]`: SPEND.json item `HMFWD_<S>-<E>` + DECISIONS line (dry by default). `hmfwd/pull_nov.py`: only change = the path parquet also has `trd_px_open`.
* `run_register.py` Monday: verifies the manifest, builds `work/tape_hm.csv` (one front contract per trade date) when `incoming/tape.csv` is absent, prints the report (also `work/hm_feed_report.txt`). Not run on real data (none exists yet).

## 4. Leaderboard capped tier
`l2vast/ds3/code/lbcapped/add_capped_col.py` appended a LAST column `capped tier` to every table that has `cell` and `verdict` columns: LEADERBOARD.md (2 tables, 26,269 rows; 1,646 have a capped tier, the rest `-` = not in the capped re-run) and TREND_LEADERBOARD.md (3 tables, 78 rows, all matched). Values come from `out/cappedrerun/*_rescore.csv`, `struct48_leaderboard_capped.csv`, `struct48_dead_upflip_scan.csv`; all 103 rows of `TIER_CHANGES_ALL.csv` are found and agree. Text: the capped tier, `(UP)` / `(DOWN)` when it differs from the original verdict, `n/a (no series)` etc. where the re-run could not tier the row, `(proxy ...)` for XT/CHOP. The original verdict column is untouched; the original text of every row is a prefix of the new row (checked). **The leaderboard files are regenerated by the 2-hourly loop (ds3_lead.py / lb2): re-run `python3 add_capped_col.py` after a regeneration (idempotent, backs up, atomic, aborts if the file changed under it) or have the generator call it.** Parsers that read leaderboard columns by position are unaffected (the column is last).

## 5. Not done / limits
* The real Output-log format is unknown: the grammar was tested only on synthetic lines written from likely formats. Time zone of the log is assumed ET (config `tz`).
* Stop and target distances per book are not known to us (`d6_book_defaults.json` has nulls except ST stop 60): without them R1/R5/R6 replays cannot run on the log route.
* `enrich_from_tape` and the tape-built bars are unaudited against D6 (no D6 values exist in week 1). The R5 lock-engine effect, ES-lead (no ES feed), zone and FVG are not scorable in week 1.
* `LEADERBOARD.md` also shows a DS3 section header text noting it is rewritten every 2 h: the capped column will vanish on the next regeneration until the generator calls the script.
