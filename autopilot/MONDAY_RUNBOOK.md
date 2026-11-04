# MONDAY RUNBOOK - what runs on Monday 2026-11-09 13:00Z and how to read it (BASE-4, 2026-11-05)
Plain language. Research-side only: every runner reads logs, nothing here trades, resizes or changes a rule, and no row is a PASS.

## 1. What runs, in what order
The loop `monday_all.sh` (pid 3715292, flock-guarded, next fire 2026-11-09T13:00:00Z, then every Monday) calls `monday_all.py`, which runs these seven jobs one after another and writes ONE block to `autopilot/MORNING.md` (heading "MONDAY ALL (week N since 2026-11-02 ...)", a table `| Shadow line | verdict | read |`, and a "runner status" line with the return code and seconds of each job):
1 BT flip - 2 NY-AM fades bundle - 3 top-3 fade bundle + OR15 - 4 sizer Shadow lines - 5 NYAM monthly regime read (prints a row only on the FIRST Monday of a month: next 2026-12-07) - 6 SHADOW-2 lines (+ pooled sleeve) - 7 LIVE health monitor ("LM"). Detail pages are also refreshed (BT_FORWARD_WEEKLY.md, NYAM_FORWARD_WEEKLY.md, FADE_FORWARD_WEEKLY.md, SIZER_SHADOW_WEEKLY.md). Within a day it runs once (state file `autopilot/monday_all_state.json`). Before Monday: `bash l2vast/ds3/code/zones3/standing/check_monday_preflight.sh` (read-only, section 5).

## 2. What each row means
* **BT flip** - the swing-flip Shadow line (skip an entry when a fresh flip level lies between entry and target within 40 pts). Reads `forward_register/bt/bt_flip_shadow.csv`: flagged signals vs the expected weekly count (band), the P&L gap flagged-minus-rest, "saved $" and its placebo rank. EARLY until week 13.
* **NY-AM fades bundle** - ONRTH / VWAPF / ORBF at 0.5x (1 lot each). Reads `forward_register/nyam/`: P&L per book, one pooled SPRT, a monthly regime read.
* **top-3 fade bundle** (VB2 NYPM T1, PD ASIA T2, VB2 NYAM T3) **and OR15** (optional REGIME line): reads `forward_register/fade/`; per-book P&L, hit rate, SPRT llr.
* **sizer Shadow VT_Q1A and Z3_RVD30** - lines that only record the lot multiplier they WOULD have applied to signals the box already takes (`forward_register/sizer_shadow/`); the row replays realised P&L with the would-be lots. Not traded.
* **NYAM monthly regime read** - a monthly causal regime reading for the fade books; "not the first Monday" on other weeks is normal.
* **SHADOW-2 lines** (Q13, DIS-K, DIS-B P_REL_cont, DIS-E, DIS-C Sunday) - `forward_register/shadow2/<LINE>_signals.csv`, replayed on the weekly 1-second tape with the live fill model, one position per line. **SHADOW-2 SLEEVE (pooled)** - the five lines as one stream: pooled mean with a 90% interval, one SPRT (alpha = beta = .20), z looks at weeks 26 / 52 / 104; the row carries its own operating-characteristics note (SHADOW_OC.md).
* **LM 1-6** (live health monitor): 1 TH-L2 cuts, 2 Concentration (PE share), 3 Execution (stop fills vs model), 4 Regime, 5 Sizer, 6 Shadow lines. Each is a count of metrics with data and a state.

## 3. What the words mean
* **no data yet** - the register for that line is empty or the tape does not cover it. **NO DATA** (LM) - an input file is absent. **TOO FEW** (LM) - below the minimum sample; no reading.
* **EARLY (keep logging)** - before week 13 (BT, NYAM, fade) or week 26 (SHADOW-2, pooled sleeve); **INCONCLUSIVE (keep logging)** - after that week with no decision. Both are the normal state for months.
* **LOOK** (LM) - open the named page and read it; it is not an alarm and not an instruction. **OK** - nothing to read.
* **CONSISTENT (latched wkNN)** / **CONTRADICTED (latched wkNN)** - the first week the rule crossed; it stays shown (with "[now: ...]" if the current state differs). **CONTRADICTED = significantly below H1 (half the research mean), not necessarily losing money.** CONSISTENT promotes nothing.

## 4. What NOT to conclude
* One week of any row says nothing: the per-line SPRT needs 340-1,000 trades per SHADOW-2 line (4-19 years at 1-2 trades a week; SHADOW_OC.md); the pooled sleeve needs about 39 weeks at H1 (21 if the 2026 mean is true) and has a 13% false CONSISTENT rate at zero truth.
* The week-13 z test of the fade and NYAM rows repeats about 90 looks: 23% false CONTRADICTED for the NYAM bundle at the design truth (the row says so). A CONTRADICTED there is not proof of failure.
* Dollars in the table are the live fill model's replay of the logged signals, not the account's P&L. A signal logged before the first tape second has no outcome. Nothing in the table is a reason to change lots, stops or books; decisions are listed in USER_BRIEF_20261105.md.

## 5. Inputs that must exist (pre-flight prints OK / MISSING for each)
* `forward_register/tape.csv` from `hm_feed.py --tape-out` (weekly 1-s feed, starts 2026-11-07; layout sec,high,low,close or sec,hi,lo,close). Without it the NYAM, fade and SHADOW-2 rows stay "no data yet". Override path: env `MONDAY_TAPE`.
* The Shadow registers written by the box: `forward_register/{bt, nyam, fade, shadow2, sizer_shadow}/` (SHADOW_PACK.md, SHADOW_PACK_2.md). SHADOW-2 also reads optional `<LINE>_daycomplete.csv` sidecars (early-close / holiday signals with day_complete = 0 are dropped).
* The D7 logs of D7_LOGGING_REQUEST.md under `forward_register/live/`: `fills.csv`, `signals.csv` (or `signals_joined.csv`), `d6_stops.csv`, `th_cuts.csv`, `control_pnl.csv` (optional `bars_1min.csv`, `weekly_pnl.csv`). Without them the LM rows read NO DATA; that is expected until D7 delivers.
* Today (2026-11-05) pre-flight reports MISSING: shadow2 directory, tape.csv, all five live files - none exists yet.

## 6. If a row says ERROR (or a runner failed: see "runner status")
The cell reads `ERROR rc=...: <last stderr line>`. Re-run ONE runner without writing anything (`--dry`), from `l2vast/ds3/code/zones3` with `python3 -I`, FR = `forward_register/`. Add `--tape FR/tape.csv` only when that file exists (monday_all does the same; the NYAM runner stops with FileNotFoundError if given a missing tape):
* BT: `bt_forward_weekly.py FR/bt/bt_flip_shadow.csv --start 2026-11-02 --dry`
* NYAM: `nyam/nyam_forward_weekly.py --regdir FR/nyam --start 2026-11-04 --tape FR/tape.csv --dry`
* fade: `fade_shadow/fade_forward_weekly.py --regdir FR/fade --start 2026-11-04 --tape FR/tape.csv --dry`
* sizer: `sizer_shadow/sizer_forward_weekly.py --regdir FR/sizer_shadow --start 2026-11-04 --dry`
* SHADOW-2 + sleeve: `shadow2/shadow2_weekly.py --regdir FR/shadow2 --start 2026-11-04 --tape FR/tape.csv --dry` (self-test: `--selftest`)
* LM: `standing/live_monitor.py --regdir FR --tape FR/tape.csv --dry`
* The whole table without writing: `standing/monday_all.py --dry --force`. To re-issue the real block after a fix: `standing/monday_all.py --force` (appends a second block; a re-run on the same day needs `--force`). Tests: `standing/test_g23.py`, `shadow2/test_g1.py`, `shadow2/test_oc_latch.py` (all must print PASS).
The standing code's md5 vs the logged md5s: the last block of the pre-flight (a file "NOT in DECISIONS.md" changed after the last logged change or was never logged). Backups of the recent edits: `*.bak_pre_g23`, `*.bak_pre_oc`, `*.bak_pre_bn` next to each file; ZL-1's G1 backups in /mnt/l2/l2vast/ds3_zl1_s2/backup_g1/.
