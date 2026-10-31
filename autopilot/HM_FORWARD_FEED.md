# HM_FORWARD_FEED - November-onward data feed for the HM forward test (HMF-1, 2026-10-31; REG-1 update below)

**REG-1 STATUS (2026-10-31, user reply 14:30Z): the weekly NQ.v.0 ohlcv-1s feed (~$1.15/wk) is APPROVED, start Sat 2026-11-07. Raw MBO ($214) is NO.** The exact weekly procedure, a cron-free checklist, the verification and the budget-log step are in section 6 at the end. The text of sections 1-5 is the original HMF-1 plan (kept); where it says "only after the user confirms", the user's 14:30Z reply is that confirmation for the weekly ohlcv-1s pull at a quote <= $2.00; any other schema, symbol or quote above $2.00 still needs a new OK.

Status: PLAN + guarded script + FREE quotes only. Nothing was downloaded or bought. No key, account or credential appears in any file. Data before 2026-11-01 22:00Z (18:00 ET) is never touched by the script (it refuses an earlier start). Sealed UNTOUCHED stays sealed: no paid pull before 2026-11-02, and only after the lead tells you the user confirmed purchase and budget.

## 1. What the HM forward scorer needs
Scorer: l2vast/ds3/code/thl_hm/fwd_score.py (a30_w10 sole primary; reports at 500 and 1,000 HM trades; Monday weekly run). Per the runbook (DS3_THL_HM_FWD_RUNBOOK.md section 3) it needs, for every second with a print from Sunday 18:00 ET to the 16:55 ET flat: NQ front-month OUTRIGHT per-second **high, low, last trade price** (+ a count/volume only to rank contracts), raw (unadjusted) prices, in the tables/NQ/1s layout (ts = END of the second, ns). It reads columns ts, trd_px_hi, trd_px_lo, trd_px_last, instr, trd_n only. **mbp-10 and quotes are not needed. ES is not needed** (HM trades NQ only; the ES leg exists only for the separate S130_ES shadow, which is covered by the already-approved weekly L2 buy).

How the history was pulled (found in RUNBOOK_WEEKLY_EXTENSION.md, SPEND.json, ext_1019/, l2vast/dl.py, l2v_ext_reduce.py):
* Dataset GLBX.MDP3; key from env DATABENTO_API_KEY only.
* Library trades weeks (data/ext_20261017): schema trades, parent NQ.FUT (the runbook step 1), downloaded with get_range(path=...) to data/ext_<date>/NQ_trades_<from>_<to>.dbn.zst; continuous `<SYM>.v.0` for ohlcv-1m / ohlcv-1d.
* L2 weekly extension (approved, about $36/week for NQ+ES+RTY, running total $67.29 of $700): schema mbp-10, continuous NQ.v.0 / ES.v.0 / RTY.v.0, stype_in=continuous, batch jobs split_duration='day', downloaded with batch.download (l2vast/dl.py) to /mnt/l2/l2vast/raw/<SYM>/ext/<JOB>/, reduced by l2v_ext_reduce.py into tables/<SYM>/1s/<YYYY-MM>__ext_<START>_<END>.parquet. tables/NQ/1s is built from that. Window convention: contiguous, START = previous END, END = Saturday 00:00Z; request end must be <= dataset available end (releases about 8 h after the event).
* ohlcv-1s was not used before (the runbook says "skip ohlcv-1s, the engine uses trade ticks"); the 1-s history is built from the mbp-10.

## 2. Free quotes (metadata.get_cost; GLBX.MDP3; nothing bought)
The forward window cannot be quoted yet: the dataset's available end is 2026-10-31T00:00Z (the API returns 422 data_start_after_available_end for 2026-11-01..). So the quotes below are for the last two COMPLETE weeks, which have the same length and volume regime (Sun 22:00Z-Fri 22:00Z style windows); a forward week should land within about +-15%. The script re-quotes the exact window when the data are released.

| window (proxy) | symbol | schema | cost USD | records | GB billable |
|---|---|---|---|---|---|
| 2026-10-25 22:00Z .. 10-30 22:00Z | NQ.v.0 | ohlcv-1s | **1.14** | 311,169 | 0.017 |
| same | NQ.FUT (parent, all contracts) | ohlcv-1s | 1.15 | 316,078 | 0.018 |
| same | NQ.v.0 | trades | 3.40 | 2,713,809 | 0.130 |
| same | NQ.FUT (parent) | trades | 3.41 | 2,720,370 | 0.131 |
| same | NQ.v.0 | mbp-10 | 23.12 | 134.9M | 49.6 |
| same | NQ.FUT (parent) | mbp-10 | 26.57 | 155.0M | 57.1 |
| same | ES.v.0 | ohlcv-1s / trades | 1.03 / 3.44 | 281k / 2.75M | 0.016 / 0.132 |
| 2026-10-19 00:00Z .. 10-24 00:00Z | NQ.v.0 | ohlcv-1s / trades / mbp-10 | 1.11 / 3.18 / 21.12 | 305k / 2.54M / 123M | 0.017 / 0.122 / 45.4 |
| same | ES.v.0 | ohlcv-1s / trades | 1.02 / 3.34 | 280k / 2.67M | 0.016 / 0.128 |

Projection (x about 4.3 weeks/month; x about 50 weeks to the 1,000-trade mark, about Oct 2027):
| feed | per week | per month | to 1,000-trade mark |
|---|---|---|---|
| NQ.v.0 ohlcv-1s (minimum) | $1.1-1.2 | about $5 | about $57 |
| NQ.v.0 trades (tick level; fwd_path_build.py input) | $3.2-3.4 | about $15 | about $170 |
| NQ.v.0 mbp-10 (already inside the approved L2 weekly buy) | $21-23 | about $95 | about $1,100 (cannot be afforded from the ~$811 left) |

**Minimum schema for the HM scorer: ohlcv-1s on NQ.v.0.** Its bar high/low/close are the per-second max/min/last trade price, which is exactly what the scorer reads (trd_px_hi/lo/last). Unverified assumption (to check on the first pulled week, see section 5): ohlcv-1s equals the 1-s table built from mbp-10 trades on hi/lo/last for the same seconds (it should; same venue prints, close = last trade).

## 3. Recommendation
1. The cheapest feed that lets the Monday scorer run: **NQ.v.0 ohlcv-1s, one pull per week, about $1.15/week, 0.017 GB/week**. The pull script converts it to the tables/NQ/1s layout (data_fwd/path/) so `fwd_score.py --path-kind table --path-root .../data_fwd/path/` works unchanged; no change to the scorer.
2. Shadow register offline replays (HM trades re-simulated on the 1-s path with the THL B kernel) need exactly the same hi/lo/last 1-s path; so ohlcv-1s covers them too. Anything that replays order-book events (S130_ES, L2 health rules) needs the mbp-10 that the approved weekly L2 buy ($36/wk) already brings; do not buy it twice.
3. Optional insurance, week 1 only: also pull NQ.v.0 trades for week 1 (about $3.4) to cross-check ohlcv-1s vs trades-derived 1-s (and fall back to fwd_path_build.py if a mismatch appears). Skip if the weekly L2 buy covers week 1 (then compare against its table at no cost).
4. Budget note (for the user; also in MORNING.md): remaining about $811 of $8,000. The approved weekly L2 buy at about $36/week uses it up in about 22 weeks (April 2027), long before the 1,000-trade mark (about Oct 2027). The HM-only ohlcv-1s feed is $57 for the whole forward test, so it is the safe floor that survives if the L2 buy stops. The first pull of the 202644 L2 week (Sat 2026-10-31) is a separate item and is not part of this feed.

## 4. Exact commands (lead; ONLY after the user confirms purchase and budget AND on/after 2026-11-02)
Script: l2vast/ds3/code/hmfwd/pull_nov.py (dry-run default; free quotes only; paid pull needs --execute + the exact confirm string from a fresh dry run + date >= 2026-11-02 + end released + quote <= --max-usd (default 15) + quote <= remaining budget in SPEND.json; start before 2026-11-01T22:00Z is refused; will not overwrite; writes data_fwd/MANIFEST.jsonl with sha256, bytes, quote, records and the path parquet checksum).

Step A, dry run (free), week 1 (Sun 2026-11-01 22:00Z to Sat 2026-11-07 00:00Z; can be run any time after the data are released, i.e. from Sat 2026-11-07 about 08:00Z; an earlier end such as 2026-11-02T22:00Z can be used for a one-day first look, release lag about 8 h):
```
cd l2vast/ds3/code/hmfwd
bash -ic 'python3 -I pull_nov.py --start 2026-11-01T22:00:00Z --end 2026-11-07T00:00:00Z'
```
Prints cost, records, GB, remaining budget and `CONFIRM STRING: PULL-HMFWD NQ.v.0 ohlcv-1s 20261101T2200-20261107T0000 USD<cost>`.

Step B, the pull (after the user's OK; paste the printed string):
```
bash -ic 'python3 -I pull_nov.py --start 2026-11-01T22:00:00Z --end 2026-11-07T00:00:00Z --execute --confirm "PULL-HMFWD NQ.v.0 ohlcv-1s 20261101T2200-20261107T0000 USD<cost>"'
```
Output: l2vast/ds3/data_fwd/NQ_ohlcv-1s_20261101_20261107.dbn.zst, data_fwd/path/2026-11__ext_fwd_20261101_20261107.parquet, MANIFEST.jsonl line. Then log the spend (SPEND.json item HMFWD_20261101-20261107, spent_usd += quote; DECISIONS.md).

Step C, score (Monday): `python3 fwd_score.py --trades <list> --path-kind table --path-root l2vast/ds3/data_fwd/path/` (runbook section 6). If the L2 weekly buy also supplies tables/NQ/1s for the same weeks, use only one path root per run (the scorer picks the most-printed contract and drops duplicate ts, so do not point both).

## 5. Weekly cadence and cost
* Every Saturday at or after 08:00Z (dataset release lag), window = previous END to Saturday 00:00Z of the same week, 7 days contiguous (week n+1 START = week n END; Sunday 22:00Z sessions open the week). Dry run, user's standing OK (or per-pull OK, lead's call), then execute. Monday: score.
* Cost: about $1.15 per week ohlcv-1s (about $5/month, about $57 to the 1,000-trade mark); trades-schema variant `--schema trades` about $3.4/week.
* First-week check (free): the path parquet's hi/lo/last for the week vs the L2-derived tables/NQ/1s part for the same seconds (if the L2 buy ran) or vs the data/ext trades-derived tick path: expect hi/lo/last equal on at least 99.9% of seconds.
* Quarterly roll: v.0 switches contract around 2026-12-15 inside one week; instr changes mid-file. The scorer ranks contracts by trd_n over the whole window, so a roll week must be pulled and scored as one file but check no_path = 0 and the scored trades' contract.
* Weeks with a CME holiday (Thanksgiving 11-26, 12-25, 01-01): no/short session; early_end flagged by the scorer.

## 6. REG-1: the approved weekly procedure (cron-free; the lead runs it by hand, ~5 minutes, every Saturday)
Standing OK: user reply 2026-10-31 14:30Z (NQ.v.0 ohlcv-1s weekly, ~$1.15/wk, from Sat 2026-11-07; raw MBO no). Guard rails stay in the script: dry run by default, floor 2026-11-01T22:00Z, no paid pull before 2026-11-02, end must be released (<= now - 8 h and <= dataset end), quote <= `--max-usd` and <= remaining budget, exact confirm string, never overwrites. Use `--max-usd 2.00` for this standing OK (a quote above it = stop and ask in MORNING.md). The key comes from `bash -ic` (env DATABENTO_API_KEY) only. REG-1 change to the script: the path parquet also carries `trd_px_open` (extra column; fwd_score.py reads named columns so it is unaffected; it allows 45-s bar opens to be rebuilt later).

Windows are contiguous, Sunday 22:00Z to Saturday 00:00Z; the pull is made on the Saturday that ENDS the window, at or after 08:00Z:
| week | START (UTC) | END (UTC) | pull on |
|---|---|---|---|
| 1 | 2026-11-01T22:00:00Z | 2026-11-07T00:00:00Z | Sat 11-07 >= 08:00Z |
| 2 | 2026-11-07T00:00:00Z | 2026-11-14T00:00:00Z | Sat 11-14 |
| 3 | 2026-11-14T00:00:00Z | 2026-11-21T00:00:00Z | Sat 11-21 |
| 4 | 2026-11-21T00:00:00Z | 2026-11-28T00:00:00Z | Sat 11-28 (Thanksgiving 11-26: short week) |
| n | previous END | previous END + 7 d | the Saturday of END |
(Week 1 holds six trading days; the weekend gap between weeks is empty by construction. The 12-15 roll falls inside the week 2026-12-12..12-19: pull and score it as one file.)

**Step 1 - dry run (free).** Replace S/E with the row above:
```
cd l2vast/ds3/code/hmfwd
bash -ic 'python3 -I pull_nov.py --start S --end E --max-usd 2.00'
```
Check: `cost_usd` between 0.9 and 1.5 (week 1: ~1.1-1.3), `records` 250k-330k, `remaining_budget_usd` > 100, `dry_run: true`, the CONFIRM STRING printed. If the quote fails with "not yet released", wait (it is released ~8 h after the event).
**Step 2 - the pull.** Paste the string from the dry run:
```
bash -ic 'python3 -I pull_nov.py --start S --end E --max-usd 2.00 --execute --confirm "PULL-HMFWD NQ.v.0 ohlcv-1s <S>-<E> USD<cost>"'
```
Writes `data_fwd/NQ_ohlcv-1s_<S>_<E>.dbn.zst`, `data_fwd/path/2026-11__ext_fwd_<S>_<E>.parquet` and a `MANIFEST.jsonl` line (sha256, bytes, quote, records, path_rows, path_sha256).
**Step 3 - verify (free, read-only; all of it is one command):**
```
<repo>/.venv/bin/python3 l2vast/ds3/code/shadow/hm_feed.py --verify
```
It re-hashes the dbn and the path parquet against the MANIFEST (sha256), compares the parquet row count with `path_rows`, checks that no window starts before the floor, that the windows are contiguous (week n START = week n-1 END), and prints the continuity with the prior week (hours between the last print of week n-1 and the first print of week n: expect ~2 days across the weekend; flags a gap > 72 h, an overlap, and an instrument change = roll week). Exit code 1 and the word FAIL = do not score from the feed; paste the lines in MORNING.md.
Also by eye: records/rows within +-15% of the previous week (~300k per full week); `quote_usd` equals the dry-run quote; week 1 only: compare hi/lo/last with the L2-derived `tables/NQ/1s` part for the same seconds if the weekly L2 buy ran (expect equal on >= 99.9% of seconds).
**Step 4 - budget log.** `python3 l2vast/ds3/code/hmfwd/log_spend.py` (dry: prints the SPEND.json update and the DECISIONS.md line), then the same with `--apply`; paste the printed DECISIONS.md line into DECISIONS.md. Expected running line: spent_usd + ~1.15 per week, the HM feed total ~$57 to the 1,000-trade mark.
**Step 5 - Monday.** Nothing to do: `run_register.py` (shadow runbook) verifies the same manifest and, when `incoming/tape.csv` is absent, builds the register tape from ALL verified weekly files (one front contract per trade date: the one with the most volume that date). Run `fwd_score.py` for HM as before with `--path-kind table --path-root .../data_fwd/path/`; use only one path root per run.
Failure handling: a skipped Saturday is made up the next Saturday by one pull covering both weeks (window <= 32 days is accepted by the script; START must still equal the last END); a failed verification is never patched by hand - re-pull is refused (no overwrite), so move the bad files to `data_fwd/quarantine/` first and say so in MORNING.md.
