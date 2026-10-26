# REPORT_0900_ENTRIES - the pair's 09:00-09:59 ET entries at 14/14 (UNWINDOWED pair, trackP, 2026-10-20)
Basis: trade rows of the unwindowed engine (13,184 trades), blocked by bar-close label time et_in. 114 entries by label, 101 by true entry instant (et_in-60 s); 13 differ. Net is per trade before the day/week lock rules (flat = engine 1 tick/side; cost-corrected = foundB v2 measured excess on entries and market exits at 14 lots). Week ids are ISO weeks of the exit label.

## Table 1 - 09:00-09:59 entries by year and book ($ and trade count)
| year | book | n | flat net | cost-corrected net |
|---|---|---|---|---|
| 2023 | HM | 15 | -32,486 | -33,801 |
| 2023 | ST | 19 | -41,270 | -43,739 |
| 2023 | both | 34 | -73,755 | -77,540 |
| 2024 | HM | 17 | +64,902 | +61,631 |
| 2024 | ST | 12 | +23,628 | +21,586 |
| 2024 | both | 29 | +88,530 | +83,217 |
| 2025 | HM | 15 | +14,904 | +11,241 |
| 2025 | ST | 21 | +47,788 | +43,084 |
| 2025 | both | 36 | +62,693 | +54,325 |
| 2026 | HM | 4 | +25,096 | +23,997 |
| 2026 | ST | 11 | +2,199 | -1,311 |
| 2026 | both | 15 | +27,294 | +22,686 |
| ALL | HM | 51 | +72,417 | +63,068 |
| ALL | ST | 63 | +32,344 | +19,620 |
| ALL | both | 114 | +104,761 | +82,688 |

## Worst single trade and worst week
- Worst single trade: -$28,621 flat / -$28,692 corrected, HM, label day 2023-08-07.
- Worst week contribution: ISO week 202332 (the same trade), -$28,621 flat / -$28,692 corrected; the unwindowed pair's total that week was -$135,048 (flat).

## Last 8 ISO weeks (202635-202642)
| n | book | flat net | corrected net |
|---|---|---|---|
| 4 | HM 1, ST 3 | +25,726 | +24,795 |
All 4 trades are positive (HM +10,229; ST +15,497; smallest trade +$1,619 flat on 2026-10-05). Worst-week contribution is positive (+$7,639 in week 202635, pair total that week -$98,534; corrected +$7,308 in 202641, pair total -$95,813), so there is no negative contribution. The pair's own 8-week total (unwindowed engine, flat) is +$83,725.

## Table 2 - cost of the live 09:00-09:59 block (windowed pair: 18:00-18:05 and 15:00-16:55 blocks on; 09:00 block ON vs OFF), 14/14
| window | metric | 09:00 block ON (live) | 09:00 block OFF |
|---|---|---|---|
| all-in | flat net / maxDD / Sharpe | 5,171,695 / 436,293 / 2.12 | 5,271,008 / 447,548 / 2.17 |
| all-in | corrected net / maxDD / Sharpe | 2,991,710 / 597,262 / 1.24 | 3,133,961 / 555,571 / 1.30 |
| OOS | flat net / maxDD / Sharpe | 4,817,734 / 436,293 / 2.29 | 5,126,238 / 397,354 / 2.46 |
| OOS | corrected net / maxDD / Sharpe | 2,737,807 / 597,262 / 1.31 | 3,100,489 / 555,571 / 1.50 |
| last 8 weeks | flat / corrected net, maxDD | -7,531 / -60,400, DD 342,563 / 362,066 | identical (the OFF window changes nothing) |
So the block costs about $100k (flat) to $142k (corrected) of all-in net, and $300-360k of OOS net, because 09:00 entries also free daily rule budgets. In the cost-corrected series, OFF also has a lower maxDD (556k vs 597k).

Caveats: 114 trades is a small sample; year signs flip (2023 negative, 2024-26 positive); the OOS difference is larger than the sum of the trade P&L because the per-book daily rules interact. Source: outputs/l2vast/pairP/r0900.py.

## UPDATE 2026-10-20 (user answer Q3): the 09:00-09:59 block is REMOVED; live windows are 18:00-18:05 and 15:00-16:54 ET only
The "09:00 block OFF" case of Table 2 is the NEW benchmark (PAIR_WINDOWED_BENCH2): 14/14 flat net $5.27M, maxDD $448k, Sharpe 2.17; corrected $3.13M, $556k, 1.30; OOS flat $5.13M / DD $397k; L8W -$7.5k / DD $343k. By true entry instant (et_in-60 s): 14/14 flat $5.62M / $448k / 2.27, L8W +$106k. 454 entries blocked by label, 480 by true instant, 44 differ. Series: outputs/l2vast/pairP/PAIR_WINDOWED_BENCH2.npz (keys new_label__*, new_true__*, old3_label__*; flat, corr14/8, slice13_14/8, slice19_14/8). The old 3-window bench stays as the reference column (old3_label).
