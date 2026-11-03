# DISCOVER_QUOTES (DQ, 2026-11-03) - Databento GLBX.MDP3 cost quote, METADATA ONLY (nothing bought, nothing downloaded)
Window 2023-04-01..2026-10-31 inclusive (end=2026-11-01 exclusive). Continuous symbology volume-front `X.v.0` (matches the on-disk series; the calendar `X.c.0` front gave misleading tiny counts for GC/6J = thin expiring month, so ignore it). Licence covers all nine; no errors. Scripts: outputs/l2vast/ds3/code/discover/dq_quote.py, dq_quote2.py; raw numbers dq_quote2.json.
Budget: ~$770 left of $8,000. User approval required before any pull.

## KEY FINDING: ohlcv-1m is ALREADY OWNED for every symbol
Do not re-buy 1-min. Only a top-up for 2026-10-13..10-31 is missing for most (ES/RTY already to 10-30).

## Per symbol / schema (full window): records | billable GB | USD
| sym | ohlcv-1m | ohlcv-1s | trades |
|---|---|---|---|
| NKD | 843,636 / 0.047 / $3.08 | 2,715,056 / 0.152 / $9.91 | 3,976,216 / 0.191 / $4.98 |
| 6J | 1,240,479 / 0.069 / $4.53 | 12,559,639 / 0.703 / $45.85 | 33,577,229 / 1.612 / $42.03 |
| 6E | 1,244,580 / 0.070 / $4.54 | 14,452,548 / 0.809 / $52.76 | 41,806,869 / 2.007 / $52.33 |
| ZN | 1,181,086 / 0.066 / $4.31 | 12,171,348 / 0.682 / $44.43 | 89,583,899 / 4.300 / $112.13 |
| ZB | 1,081,027 / 0.061 / $3.95 | 7,167,476 / 0.401 / $26.17 | 41,845,214 / 2.009 / $52.38 |
| MBT | 1,029,981 / 0.058 / $3.76 | 7,559,657 / 0.423 / $27.60 | 18,666,405 / 0.896 / $23.36 |
| BTC | 867,352 / 0.049 / $3.17 | 3,417,270 / 0.191 / $12.48 | 6,116,617 / 0.294 / $7.66 |
| GC | 1,256,178 / 0.070 / $4.59 | 26,790,877 / 1.500 / $97.81 | 89,125,565 / 4.278 / $111.56 |
| CL | 1,250,788 / 0.070 / $4.57 | 23,505,150 / 1.316 / $85.81 | 94,288,037 / 4.526 / $118.02 |
Totals: ohlcv-1m all 9 = $36.49 (already owned); ohlcv-1s all 9 = $402.82 (all but GC/CL = $219.20); trades all 9 = $524.44; trades NKD+6J+ZN = $159.14.
Top-up ohlcv-1m 2026-10-13..10-31, all 9 symbols = $0.57 total (~$0.05-0.07 each).

## tbbo / mbp-1 (NKD, 6J, ZN): time sub-selection IS possible
get_cost accepts intraday start/end, so a pull can be one request per day with a 22:00-12:00 UTC window (covers Asia open 18:00 ET through ~London midday/NY pre-open; DST shifts by 1 h - assumption stated). Quoted a sample week (2026-10-12..19), one day, and 00:00-12:00 UTC of that day, then scaled by ~187 weeks. These are EXTRAPOLATIONS (rough, +/-30%), not exact quotes:
| sym | tbbo full-day est | tbbo Asia+London est | mbp-1 full-day est | mbp-1 Asia+London est |
|---|---|---|---|---|
| NKD | ~$6 | ~$3-4 | ~$49 | ~$27-35 |
| 6J | ~$44 | ~$25-30 | ~$125 | ~$70-85 |
| ZN | ~$236 | ~$70-90 | ~$495 | ~$140-200 |
Sample week exact: NKD tbbo $0.033 (15.7k rec), mbp-1 $0.263 (1.96M rec); 6J tbbo $0.234 (112k), mbp-1 $0.668 (4.98M); ZN tbbo $1.27 (607k), mbp-1 $2.65 (19.8M). Recommendation: NOT needed for a first census (the census is 1/5/15/60 min lead-lag); buy NKD tbbo only if NKD passes.

## ALREADY ON DISK
- ohlcv-1m, all of NKD, 6J, 6E, ZN, ZB, GC, CL, ES, RTY, YM, plus BTC and MBT: volume-front, cached at l2vast/ds3/tc/cache/<SYM>.parquet (6J,6E,ZN,ZB,GC,CL,BTC,ES,RTY,YM: 2013-01..2026-10-16; BTC/MBT from 2022-01-02, MBT to 10-14; RTY from 2017-07) and /mnt/l2/l2vast/ds3/cache_te2/<SYM>.npz (+_adj; inventory.csv; NKD there 2013-01-02..2026-10-16, no NKD parquet in tc/cache). Raw per-year dbn: /mnt/l2/rootmoves/data_autopilot/ohlcv1m/<SYM>_<year>.dbn.zst (2013..2026, to 2026-10-16). BTC/MBT have NO raw dbn files, only the cache arrays.
- ES and RTY 1-min extended to 2026-10-30: <repo>/data/ext_20261026_20261030/{ES,RTY,NQ}_2026_merged.dbn.zst (raw 2023-02..2026-10-12: /mnt/l2/rootmoves/data_databento/{ES,RTY}/ohlcv-1m_full.dbn.zst). YM 1-min ends 2026-10-16.
- Trades (tick) monthly files 2023-02..~2026-10-12: /mnt/l2/rootmoves/data_databento/{ES,RTY,ZN,GC,CL}/trades/*/ (ES, RTY, ZN, GC, CL ALL OWNED; ES/RTY continued weekly in data/ext_2026*). NOT owned: trades for NKD, 6J, 6E, ZB, MBT, BTC, YM. => ZN/GC/CL trades must NOT be re-bought (saves $342).
- ohlcv-1s: no raw ohlcv-1s files for ES/RTY/YM (only NQ 1s feeds in scratch). 1-s for ES/RTY is derivable from the owned tick trades; YM has 1-min only (no trades). No tbbo/mbp-1 for NKD/6J/ZN. mbp-10 only ES/RTY small samples (/mnt/l2/rootmoves/data_databento/mbp10).
- NOTE: ZN/GC/CL/ES/RTY owned trades could replace the ohlcv-1s purchase for those; GC/CL 1s ($98/$86) are not worth buying.

## Options (all nine 1-min series are owned, so A is almost free)
- A: ohlcv-1m all eight (+ZB, BTC/MBT): already owned; buy only top-up 10-13..10-31 = **$0.57**. (Full re-buy would be $36.49 - do not.)
- B: A + ohlcv-1s: for NKD, 6J, 6E, ZN, ZB, MBT, BTC = $219.20 + $0.57 = **$219.8**; all nine incl. GC/CL = $403.4 (over $300 cap, not recommended).
- C: A + trades for NKD, 6J, ZN: ZN trades are already owned, so real cost is NKD $4.98 + 6J $42.03 + $0.57 = **$47.6** (nominal if ZN re-bought: $159.7).
## RECOMMENDED minimal pull (under $300): **~$171**
top-up 1m all 9 ($0.57) + NKD trades ($4.98) + ohlcv-1s for NKD ($9.91), 6J ($45.85), 6E ($52.76), ZN ($44.43), BTC ($12.48) = $170.98. Lean version (census-critical only, ~$60): top-up + NKD trades + NKD 1s + 6J 1s = $61.3. Everything else for the 1/5/15/60-min census already exists locally, and the census could start NOW on owned 1-min with no purchase; buy 1-s only if the 1-min census shows an edge worth refining.
