# HM_VWAP_ANCHOR - which clock resets the live HM VWAP after the DST change? Replay readiness (DIS-BT, CAL, 2026-11-05)
Research only; nothing live; no PASS claims. Code `l2vast/ds3/code/dsthm/{hm_anchor_replay.py, hm_anchor_selftest.py}`; outputs `/mnt/l2/l2vast/ds3_base4/hm_anchor/`. Context: DST_AUDIT_20261105.md finding 5 / question 4.1.

## 0. Answer in short
1. **In EDT the two anchors are identical** (proof below: 0 differing signal bars and identical trade lists in four EDT windows, 2023-2026). **In EST they differ by one hour of VWAP accumulation** (A resets at 00:00 EST = 05:00Z, B at 23:00 EST = 04:00Z), and that changes the HM signal series on every winter day.
2. **Size of the decision, last winter (2025-11-03..2026-03-06, 18 weeks, research replica of HM, 60/60):** 650 trades under A vs 657 under B, **90% share the same entry** (67 trades only under A, 74 only under B, about 7.8 differing entries per week); points A 2,478 vs B 2,898 (A-B -420); at live lots (Asia 4, NY-AM 2) A-B = **-$16,800 over the winter, mean -$933/week, weekly sd $4,739** (t -0.84: no reliable edge for either anchor; every one of the 18 weeks has a different trade list, 10 weeks differ by more than $1,000). Winter 2024-25: 95% same entries, A-B -$7,200 (sd $7,930/week). Winter 2023-24: 99% same, A-B +$2,400. So the anchor choice matters for which trades the book takes (about 10% of entries, rising over the years) more than for the average P&L.
3. **The test on live fills is ready.** One winter week of live HM entries (about 36 trades, about 8 decisive entries) should say which anchor the platform uses; the exact command is in section 4. Until the week exists it was validated on synthetic fills made from each anchor (the live mode names the right one both times).

## 1. Where the HM VWAP reset lives and what was replicated
HM entry (code/census/night_ins/nt8sim.py `hm_variant`): HMA(20) and HMA(55) of x = close - session VWAP; buy = HMA20 crosses above HMA55 with HMA55 rising and close above EMA200 (mirror for sell); entry at the next bar open; 60/60 bracket, 1-s exits, flat per the B8 harness. The session VWAP resets when a key changes: `key = (minute*60 - 4*3600)//86400` ("fixed UTC-4", the research replica of live NT8) or the research harness label day. I added the ET-midnight key (A, tz database) and an ET 18:00 key (C, context only) to a copy of the same function. **Replica check:** `signals(key B)` equals `nt8sim.hm_variant('fixed')` on all 1,320,115 bars (True). Frame: the newest contract segment of the history is the raw frame (offset 0.00 vs `out/def/NQ.parquet`; older segments +292.75), so tape bars after 10-30 (Dec-2026 contract, no roll before ~12-15) join without a shift.

## 2. EDT identity proof (A == B)
| window (EDT) | bars | signal bars differing | trades A / B | identical trade lists | points A / B |
|--|--|--|--|--|--|
| 2023-03-13..2023-11-03 | 232,915 | 0 | 685 / 685 | yes | 209.5 / 209.5 |
| 2024-03-11..2024-11-01 | 231,988 | 0 | 879 / 879 | yes | 2,136.3 / 2,136.3 |
| 2025-03-17..2025-10-31 | 225,118 | 0 | 1,023 / 1,023 | yes | 3,577.5 / 3,577.5 |
| 2026-03-16..2026-10-30 | 226,266 | 0 | 1,617 / 1,617 | yes | 4,997.0 / 4,997.0 |
(The first Monday after the spring change is used as the start; the days around each change differ for a few hours, by construction.)

## 3. Winter weeks, A (ET midnight) vs B (fixed UTC-4) - research replica, last winter
| week | signals A / B | signals differing | trades A / B | same entry | only A / only B | pts A / B | live-lot $ A-B |
|--|--|--|--|--|--|--|--|
| 2025-11-03 | 114 / 117 | 33 | 46 / 48 | 36 | 10 / 12 | 480 / 480 | +7200 |
| 2025-11-10 | 99 / 99 | 20 | 39 / 41 | 32 | 7 / 9 | -35 / -35 | -4800 |
| 2025-11-17 | 109 / 107 | 28 | 66 / 64 | 58 | 8 / 6 | 0 / 0 | +0 |
| 2025-11-24 | 93 / 88 | 17 | 24 / 24 | 21 | 3 / 3 | 70 / 190 | -9600 |
| 2025-12-01 | 98 / 104 | 24 | 27 / 28 | 25 | 2 / 3 | -413 / -473 | +4800 |
| 2025-12-08 | 104 / 107 | 19 | 35 / 35 | 32 | 3 / 3 | -168 / -168 | +0 |
| 2025-12-15 | 102 / 97 | 15 | 33 / 32 | 30 | 3 / 2 | 950 / 890 | +4800 |
| 2025-12-22 | 76 / 75 | 23 | 11 / 11 | 10 | 1 / 1 | -61 / -61 | +0 |
| 2025-12-29 | 76 / 79 | 15 | 17 / 19 | 15 | 2 / 4 | -300 / -180 | -9600 |
| 2026-01-05 | 91 / 92 | 17 | 25 / 25 | 23 | 2 / 2 | 16 / 16 | +0 |
| 2026-01-12 | 94 / 98 | 20 | 32 / 32 | 31 | 1 / 1 | 801 / 801 | +0 |
| 2026-01-19 | 100 / 100 | 26 | 36 / 36 | 35 | 1 / 1 | -294 / -294 | +0 |
| 2026-01-26 | 97 / 97 | 18 | 32 / 32 | 30 | 2 / 2 | 450 / 450 | +0 |
| 2026-02-02 | 103 / 102 | 23 | 52 / 51 | 46 | 6 / 5 | 120 / 300 | -4800 |
| 2026-02-09 | 119 / 116 | 19 | 43 / 43 | 37 | 6 / 6 | 467 / 347 | +4800 |
| 2026-02-16 | 110 / 112 | 28 | 36 / 38 | 33 | 3 / 5 | -240 / -240 | +0 |
| 2026-02-23 | 98 / 101 | 21 | 37 / 37 | 35 | 2 / 2 | -144 / -24 | -4800 |
| 2026-03-02 | 98 / 104 | 20 | 59 / 61 | 54 | 5 / 7 | 780 / 900 | -4800 |

Totals by winter: 2023-24 (18 wk) trades 308 / 309, same entry 99%, live-lot $ A-B +$2,400; 2024-25 (19 wk) 563 / 564, same entry 95%, A-B -$7,200, 13 weeks with a different trade list; 2025-26 (18 wk) 650 / 657, same entry 90%, A-B -$16,800, 18 weeks different. Files: `winter_weekly.csv`, `edt_identity.csv`. Caveats: points come from the B8 harness (8-lot research, 60/60, harness costs); the live-lot dollars apply Asia 4 / NY-AM 2 lots to the entry session and ignore ER sizing, locks, busy rules of the box and the TH-L2 cut; the weekly differences are partly path-dependent (a different entry changes the next busy window).

## 4. Exact commands for the live check (when the week 11-02..11-06 data exist)
1. After the Saturday 2026-11-07 NQ ohlcv-1s pull (manual, guarded; HM_FORWARD_FEED.md) build the register tape, which carries open and volume:
```
cd l2vast/ds3/code/shadow
python3 -I hm_feed.py --verify && python3 -I hm_feed.py --tape-out forward_register/tape.csv
```
2. Put the platform's HM fills for 2026-11-02..11-06 (StratTrades_DualStrat2 style CSV; columns used: strategy, entryName, side, qty, entryTime in ET; the account column is never read) at a path of your choice, then:
```
cd l2vast/ds3/code/dsthm
python3 -I hm_anchor_replay.py live --trades <StratTrades_DualStrat2_*.csv> --bars forward_register/tape.csv --since 2026-11-02 --until 2026-11-06
```
Output: per live HM entry (minute, side) whether a replay signal that enters at that minute exists under A, B, both or neither, the counts, a verdict line, and the list of decisive entries (`/mnt/l2/l2vast/ds3_base4/hm_anchor/live_entries_vs_anchor.csv`). **Decision rule:** decisive entries are those explained by only one anchor (about 8 per winter week: 3.7 A-only, 4.1 B-only on last winter). If the platform uses A, the B-only entries must be absent from the fills (and vice versa); the verdict says A or B when one side has more than twice the other's decisive entries, otherwise NOT DECISIVE yet (add the next week; 'neither' entries are fills the replica does not generate, e.g. a different HM variant, which would be a separate finding).
3. Self-test (no live data needed): `python3 -I hm_anchor_selftest.py` builds synthetic fills from the replay under A and then under B for the week 2025-12-01..12-05 (history cut at 2025-11-28, bars from a hm_feed-layout file) and runs the live mode: synthetic A -> 22 shared entries, **2 only A, 0 only B -> "A (ET midnight)"**; synthetic B -> 22 shared, **0 only A, 3 only B -> "B (fixed UTC-4)"**.
4. If the answer is A (ET midnight), the research replicas listed in DST_AUDIT item 5 (`nt8sim.hm_variant`, B8 harness, the forward scorers that use `-4*3600`) should switch to the tz-aware key for dates from 2026-11-01 (and for the winters of the history, which would change past HM numbers by the amounts above); if B, nothing changes in the replicas and the platform keeps a fixed-offset clock (worth telling the platform owner that it will be 23:00 EST until March 2027).

## 5. Limits
- Needs the week of data (feed + fills); nothing in this file used data after 2026-10-30.
- The replica is the NT8-faithful HM entry; live HM may run other THP/lot rules (not entries) - those do not change entry times except through busy windows.
- Entry matching is by minute and side; fills with split legs use the earliest fill per minute.
