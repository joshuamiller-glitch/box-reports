# FEED_RUNBOOK_20261107 - Saturday 2026-11-07: pull week 1 of the NQ 1-second feed (DIS-BW, CAL; for the user / lead)
Plain-language checklist. Nothing here was run against Databento: the dry run itself calls Databento's free price-quote service, so I checked only what works offline (help text, the refusals, `hm_feed.py --verify` on an empty folder, `log_spend.py` dry, the new `feed_check.py` on last week's real data). No purchase happens unless you add `--execute` plus the confirm string.

## 0. Facts to know first
- **What:** NQ continuous front month, 1-second bars (`NQ.v.0`, `ohlcv-1s`, raw prices, Databento dataset GLBX.MDP3). `v.0` (follows volume) is what every earlier weekly buy used; in November it is the December contract NQZ6. It switches to March (NQH7) around 2026-12-10..15. `NQ.c.0` (calendar roll) would be the same contract until then; do not mix the two. Do not request `NQ.FUT`, `trades` or ES/RTY.
- **Window for week 1:** start **2026-11-01T23:00:00Z** (Sunday 18:00 ET, the Globex open; DST ended that morning, so it is 23:00Z, not 22:00Z), end **2026-11-07T00:00:00Z**. It covers the five trading days Mon 11-02..Fri 11-06 (Sunday evening belongs to Monday). The Friday close (17:00 ET = 22:00Z) leaves two empty hours at the end, which is normal. The script refuses a start before 23:00Z and an end that is less than 8 hours old, so pull on Saturday **at or after 08:00Z**.
- **Cost:** the same window last week bought as one quote of **about $1.14 (311,169 records, about 17 MB)**. Expect $0.9-1.5. Weekly cap in the command: `--max-usd 2.00`.
- **Budget:** the true balance is **$711.74** ($8,000 minus $7,288.26). The script's own guard reads `autopilot/SPEND.json`, which still shows $7,226.94 spent (the $61.315 LEAN purchase was never added), i.e. $773.06. Ask the lead to add that item before the pull so the guard and the log are right; it does not change this pull.
- **Key:** `DATABENTO_API_KEY` comes only from `bash -ic` (your login shell). Never paste, print or save it.

## 1. The pull (three commands; step 2 needs your OK)
```
cd l2vast/ds3/code/hmfwd
# step 1 - dry run (free quote, buys nothing). Prints cost, records, GB, remaining budget and one line "CONFIRM STRING: ..."
bash -ic 'python3 -I pull_nov.py --start 2026-11-01T23:00:00Z --end 2026-11-07T00:00:00Z --max-usd 2.00'
# step 2 - ONLY after your OK, and only with the string printed by step 1 (it embeds window and price), e.g.
bash -ic 'python3 -I pull_nov.py --start 2026-11-01T23:00:00Z --end 2026-11-07T00:00:00Z --max-usd 2.00 --execute --confirm "PULL-HMFWD NQ.v.0 ohlcv-1s 20261101T2300-20261107T0000 USD1.14"'
# step 3 - log the spend (first the dry print, then apply) and paste the printed DECISIONS.md line into autopilot/DECISIONS.md
python3 -I log_spend.py && python3 -I log_spend.py --apply
```
Step 1 must show `dry_run: true`, `cost_usd` 0.9-1.5, `records` 250,000-330,000, `remaining_budget_usd` above 100. It writes `l2vast/ds3/data_fwd/NQ_ohlcv-1s_20261101_20261107.dbn.zst`, `data_fwd/path/2026-11__ext_fwd_20261101_20261107.parquet` and a `MANIFEST.jsonl` line. The script never overwrites a file.

## 2. Checks right after the pull (all free, read-only, no network)
```
cd l2vast/ds3/code/shadow
python3 -I hm_feed.py --verify          # must end without FAIL (checks hashes, row counts, floor, contiguity)
python3 -I hm_feed.py --tape-out forward_register/tape.csv    # columns sec, open, high, low, close, vol
python3 -I ../hmfwd/feed_check.py       # defaults are week 1; prints OK / PROBLEM lines
```
`feed_check.py` expects: first row Sunday 11-01 **23:00:xxZ = 18:00 EST** and last row Friday 11-06 about 21:59:59Z = 16:59 EST (this is the DST check); **zero prints in the ET 17:xx hour** (a nonzero count means the offset is wrong by one hour); five trade dates with 55,000-70,000 seconds each (last week: 61,537 / 58,956 / 57,414 / 66,199 / 67,056; no holiday this week); high >= low and close inside; one instrument id per date, the NQZ6 id **261401** (no roll this week); and the **price continuity** check: first close within 3% of the last owned bar (Fri 10-30 20:59Z close **28,543.00**, same raw frame). Any PROBLEM: do not score from this feed (section 4).

## 3. What to run after
| step | command | expected |
|--|--|--|
| Monday preflight | `bash l2vast/ds3/code/zones3/standing/check_monday_preflight.sh` | tape line OK with a recent last second. **Known false alarm:** the preflight rejects the real header `sec,open,high,low,close,vol` ("unexpected header"); all runners read it fine (tested); BASE-4 was told. The five `live/*.csv` D7 files stay MISSING until the platform logs them |
| HM anchor test (needs the platform's HM fills for 11-02..11-06) | `cd .../code/dsthm && python3 -I hm_anchor_replay.py live --trades <StratTrades_DualStrat2_*.csv> --bars forward_register/tape.csv --since 2026-11-02 --until 2026-11-06` | about 8 decisive entries; verdict A (ET midnight), B (fixed UTC-4) or NOT DECISIVE (HM_VWAP_ANCHOR.md) |
| Monday run | nothing to start: `monday_all.sh` fires Mon 2026-11-09 13:00Z and passes `tape.csv` to the Shadow runners | SHADOW-2 and fade rows show outcomes instead of "no data yet" once the box has logged signals |
| Caches / ledger | none needed for Monday. The December ledger refit and the engine caches still end 2026-10-30; this feed refreshes only the price-only caches (1-s path, 1-min bars) and only through a manual REDO-style append (CACHE_REFRESH_PLAN.md, phase B, owner REDO-1). It does not refresh the L2 caches | no result to expect before the owner runs it |

## 4. If the pull fails or comes back partial
1. **Do not retry `--execute` blindly.** First look at `data_fwd/MANIFEST.jsonl` and `ls -la data_fwd/`: if a line and a file exist the money is spent.
2. "quote failed / not yet released" = too early; wait until the end of the window is 8 hours old. "output exists; never overwrite" = a file is already there; do not delete it.
3. Quote above $2.00 or above the budget = stop and tell the lead in MORNING.md; do not raise `--max-usd` on your own.
4. Partial or failed verification (records under 85% of last week's 311k, last print before Friday 21:59Z, hash mismatch, a PROBLEM line): move the bad files to `data_fwd/quarantine/` (do not patch), post it in MORNING.md and ask the lead; the next Saturday's pull may cover both weeks only if its START still equals the last good END (maximum window 32 days).
5. A skipped Saturday is made up the next Saturday by one pull of both weeks. Weekly cap $2.00; about $5 a month; balance $711.74.

## 5. What NOT to do
- No `--execute` without a fresh dry run and its exact confirm string; never reuse an old string.
- No other symbol, schema or window: not `trades` (about 3x the price), not `NQ.FUT`, not ES/RTY, not mbp-10 or raw MBO ($214, answered NO). The weekly mbp-10 extension (about $38/week), ES/RTY and the cache merges are separate user decisions.
- Do not start before Saturday 08:00Z, do not edit `SPEND.json` by hand (use `log_spend.py`), do not edit or delete anything in `data_fwd/`, do not paste the key anywhere, do not point the scorers at both the feed and the L2 tables for the same weeks.
