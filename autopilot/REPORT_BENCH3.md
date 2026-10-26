# REPORT_BENCH3 - live-faithful pair benchmark (trackP, 2026-10-20)
BENCH3 = independent per-book streams (each book one bracket trade at a time, market entry at the next bar open, stop/target/force resolved on the 1-second path as nt8sim.natural_full), NO account netting, NO NT8 orphan protective fills, swallowed entries INCLUDED as real trades, the 09:00-09:58 guard removed (user Q3), new live windows (no entries 18:00-18:05 and 15:00-16:54 ET, label time; the 15:00-18:00 block stays in the signal gate), 14/14 = 1.75 x the 8/8 engine. Rows: outputs/l2vast/pairP/ROWS_bench3.parquet (14,486 rows; ST 8,233, HM 6,253); reference with the old 09:00 guard kept: ROWS_bench3_guard09.parquet (13,208 rows). Builder: pairP/bench3_build.py; scorer pairP/bench3_run.py; series PAIR_WINDOWED_BENCH3.npz (keys new_label__* / new_true__*: flat, corr14/8, slice13_14/8, slice19_14/8); metrics pairP/bench3.out. BENCH2 stays labelled "includes NT8 orphan rows".

## (1) Verification against the live log (2026-10-05..10-16, 196 ST/HM entries; engine row matched = same book and side within 2 minutes)
| engine | rows | live matched by engine | engine rows matched by live |
|---|---|---|---|
| netted + orphans (old ROWS) | 197 | 105 (54%) | 105 (53%) |
| independent streams, old 09:00 guard | 197 | 119 (61%) | 119 (60%) |
| BENCH3 (no guard; live had no 09:00 guard in this span) | 217 | 117 (60%) | 117 (54%) |
By book live ST 120 / HM 76; BENCH3 ST 132 / HM 85. The independent streams reproduce 60-61% vs 54% for the netted rows; the AUDIT2 ceiling for TH-off with no limits is about 60%, since the live chart start times, TH on ST, the per-book limits and the combo lock are not in these streams.

## (2) Metrics, 14/14 (all-in net / maxDD / weekly Sharpe; OOS net; L8W net, label-time blocking)
| benchmark | all-in | maxDD | Sharpe | OOS net | L8W net |
|---|---|---|---|---|---|
| old unwindowed (ROWS, netted+orphans), flat | 4.80M | 490k | 1.90 | 4.59M | +84k |
| BENCH2 flat (new windows) | 5.27M | 448k | 2.17 | 5.13M | -8k |
| BENCH2 corrected | 3.13M | 556k | 1.30 | 3.10M | -60k |
| BENCH3 flat | 5.35M | 399k | 2.11 | 4.90M | +68k |
| BENCH3 corrected | 3.95M | 422k | 1.55 | 3.59M | -37k |
| BENCH3 sliced entries 1.3 / 1.9 t | 4.74M / 4.80M | 406k / 408k | 1.89 / 1.90 | 4.33M / 4.41M | +20k / +13k |
| BENCH3 flat, by true instant | 5.52M | 399k | 2.18 | | |
| BENCH3 corrected, by true instant | 4.09M | 422k | 1.61 | 3.75M | +136k |
8/8: BENCH3 flat 3.06M / 228k / 2.11; corrected 2.52M / 234k / 1.75; sliced 2.72-2.80M / 231-232k / 1.89-1.93 (BENCH2 8/8 flat 3.01M / 256k / 2.17; corrected 2.09M / 297k / 1.49).
Cost-corrected excess: foundB v2 rows carry over to the 11,580 BENCH3 rows that match an old row (book/side/entry time); the rest take the year x RTH/ETH mean. Slicing order (1.3 t vs 1.9 t) flips by about $60k because the day/week locks are path dependent.

## (3) Orphan rows and swallowed entries (old ROWS vs BENCH3, rows by year; HM / ST)
- Swallowed entries = old rows closed by an opposing entry (exit name *_Entry): 2023 79/152, 2024 110/193, 2025 133/220, 2026 133/218 = 1,238 rows. Their entry never opened in the netted engine; in BENCH3 each is a real market entry trade.
- Old rows absent from BENCH3 (orphan protective fills plus path divergences): 1,604 of 13,184: HM 116/146/181/150 and ST 195/284/284/248 for 2023-2026.
- BENCH3 rows absent from the old ROWS: 2,906 (swallowed entries, the 09:00 guard removal and independent-book path differences): HM 226/326/391/419, ST 217/339/452/536.
Rows per year (BENCH3): HM 935/1,377/1,818/2,123, ST 1,094/1,731/2,493/2,915.

## (4) Does the old scoring base change? Unwindowed, live per-book/combo/week rules, 8/8 flat (TH off)
| rows | net | maxDD | Sharpe all (clean / H1 / H2) |
|---|---|---|---|
| old ROWS (netted + orphans, 09:00 guard) | 2.74M | 280k | 1.90 (1.46 / 2.83 / 2.48) |
| independent streams, 09:00 guard kept | 2.85M | 335k | 1.95 (1.61 / 2.61 / 2.38) |
| BENCH3 rows (no guard) | 3.17M | 284k | 2.09 (2.02 / 1.88 / 2.37) |
Netting and orphans alone move net +4%, maxDD +20%, Sharpe +0.05 - not material; removing the 09:00 guard adds more (+16% net, Sharpe 2.09) because those entries are positive in the clean span. The large change is in the clean/H1/H2 profile (H1 2.83 -> 1.88): the old base's H1 strength came partly from orphan rows. Re-base the shadows and P9 on BENCH3; the old base is a reference only.
Caveat: pairs in BENCH3 do not model the broker's real netting of fills (only the book-level virtual accounts), the combo lock and per-book limits sit in the b11 account layer as before; and the exact live chart start times are unknown.
