# DS3_TH_FIDELITY - TH-L2 trigger: stored-table reconstruction vs raw mbp-10 as a live process sees it (DIS-BV), BASE-4, 2026-11-05

Research only, $0, no PASS claims, nothing live. Scope note l2vast/ds3/prereg/DISBV_scope.md sha256 42716f5e32d22d0768b219c34e5857dc03d8e7fc0b465bff0c6f219ae10a77b7 and addendum 1 (DISBV_scope_addendum1.md) sha256 ace46b79203ecece0b620da972214dd6983bdf0282d1b589224113a78d4b4133, both logged in DECISIONS.md before any rebuilt feature was computed or compared. Code l2vast/ds3/code/disbv/ (bv_extract, bv_feat, bv_a, bv_b, bv_c, bv_d); bulk /mnt/l2/l2vast/ds3_base4/bv/.

## 1. Answer in four lines
1. **The stored-table reconstruction is faithful.** Rebuilt from raw NQ mbp-10 events (events with ts_event before the evaluation second only), the 5-s pulled-support sum and the behind-side median level reproduce the stored values on 1,960,295 stored decision rows of the 37 sample weeks: p5 identical on 99.9996% of rows, median level identical on 99.9999%, correlation 1.0000, liquidity-condition agreement 100.00% (kappa 1.00); the per-trade cut second, cut price and cut delta are identical for all 10,709 fired trades when the rebuilt features are evaluated on the stored rows (R10 = S to the cent in the engine: $2,520,149.07).
2. **What is NOT stable is the evaluation cadence.** The stored table evaluates the rule on a 10-s decision grid. A live process that evaluates at every second boundary fires a median 7 s earlier (25% of cuts 27 s or more earlier, 75% at most 3 s earlier, 5% quantile -559 s), agrees with the stored cut/no-cut on 96.5% of trades (kappa 0.90), and cuts an extra 497 trades (4.6% of the stored fires) that the grid never cut (consistent with brief excursions below -30 between grid rows; not separately verified).
3. **$ effect (engine, ts2 reference, live lots, x-cost 0.80): the post-cap TH-L2 gain roughly halves under a 1-s evaluation.** Post-cap 25 weeks: TH gain over TH off 18,076/wk with the stored 10-s grid, 9,903/wk with a 1-s evaluation (change -8,173/wk, week-bootstrap 90% interval -12,987 .. -3,670). Pre-cap 12 weeks: 829/wk stored, 282/wk 1-s (change -547/wk, interval -4,152 .. 2,675). The 1-s stack also has a LARGER post-cap maxDD (67,067 vs 62,576 over the 25 sample weeks).
4. **Rule parts.** The liquidity condition (5-s pulled support >= 30x median level) is stable as a number but almost always satisfied once armed: it is true on 24% of armed rows pre-cap and 60% post-cap, and 99.0% of armed trades eventually fire it (full rule fires 10,709 of 10,814 armed trades, stored). The arm at -30 is what moves the money: under the 1-s evaluation the arm-only cut earns about the same as the full rule post-cap (10,121 vs 9,903 TH gain per week) and the liquidity condition adds -219/wk post-cap and 2,952/wk pre-cap (R1 full minus R1 arm-only; negative = it removes).

## 2. Coverage and construction
* Raw store: /mnt/l2/l2vast/raw/NQ monthly mbp-10 dbn.zst 2023-02 .. 2026-10-11 and daily ext files 2026-10-12 .. 2026-10-30. **All 37 sample weeks (12 pre-cap, 25 post-cap) are covered**, single front-contract records per interval; 3 seconds in 3 weeks carry records of two instruments (roll boundary: 202538: 1 s, 202612: 1 s, 202625: 1 s), negligible. Month files with two instruments are sequential, not interleaved.
* The engine reads the REBUILT tables (r2shim redo root: out/l2set_redo/loss/rows.parquet, 23.6M rows 2023-04-02 .. 2026-10-30; 66,156 trades; dense 1-s path files), so a stored-table trigger exists for every post-cap week. (My first scope note said the opposite; addendum 1 corrects it before any comparison.)
* Stored trigger: decision rows every 10 s from entry; fire = unrealised <= -30 AND p5 >= 30 x max(median behind level, 1); p5 = sum of C-action size on the trade-supporting side (any level) over the 1-s bins ending in (T-5, T]; first fire row; exit at the path price of second T, delta = side*(price-E) - 0.995 - base.
* R10: the same two quantities rebuilt from the raw records (C-action size per second on each side; the last consistent snapshot, flag 128, for the 10 behind-side level sizes; no look-ahead: cancels in seconds T-5..T-1, book as of second T-1), evaluated at the stored rows. R1: the same rebuilt features at every integer second from entry+1 to close-1 (live 1-s process), same adverse measure from the 1-s path price at T.
* Sample: 12 pre-cap weeks 202401 202410 202420 202429 202439 202448 202510 202519 202529 202538 202548 202605 (fixed by linspace rule) and all 25 post-cap weeks 202609-202628, 202640-202644; carrying weeks excluded. 14,026 trades. No week failed or was replaced.

## 3. Row-level fidelity (stored decision rows; unrealised <= -30 rows for the liquidity condition)
| set | rows | armed rows | p5 identical | median level identical | liquidity condition true (stored / rebuilt) | agreement |
|--|--|--|--|--|--|--|
| pre-cap 12 wk | 755,561 | 288,632 | 99.9996% | 100.0000% | 24.1% / 24.1% | 100.00% |
| post-cap 25 wk | 1,204,734 | 492,950 | 99.9996% | 99.9999% | 59.5% / 59.5% | 100.00% |
| all | 1,960,295 | 781,582 | 99.9996% | 99.9999% | 46.5% / 46.5% | 100.00% |
Unrealised P&L from the path equals the stored value on 100.00% of rows (max abs difference 0.0000). The few non-identical p5 rows (about 4 per million; cause not investigated) never flip the liquidity condition.

## 4. Trade level (cut vs no cut, cut second, cut delta)
| comparison | rule | fires A | fires B | only A | only B | cut/no-cut agreement | kappa | lag B-A seconds q05 / q25 / q50 / q75 / q95 | same second | cut delta B-A, points per lot summed over common fires |
|--|--|--|--|--|--|--|--|--|--|--|
| S vs R10 | full (arm 30 + liq) | 10,709 | 10,709 | 0 | 0 | 100.0% | 1.000 | 0 / 0 / 0 / 0 / 0 | 100.0% | 0 |
| S vs R1 | full (arm 30 + liq) | 10,709 | 11,206 | 0 | 497 | 96.5% | 0.897 | -559 / -27 / -7 / -3 / 0 | 10.1% | 20,524 |
| S vs R10 | arm-only (adverse >= 30) | 10,814 | 10,814 | 0 | 0 | 100.0% | 1.000 | 0 / 0 / 0 / 0 / 0 | 100.0% | 0 |
| S vs R1 | arm-only (adverse >= 30) | 10,814 | 11,247 | 0 | 433 | 96.9% | 0.908 | -306 / -19 / -7 / -3 / 0 | 10.3% | 17,924 |
S = stored 10-s grid, R10 = rebuilt features on the stored rows, R1 = rebuilt features every second. Negative lag = the live 1-s process fires earlier. Same table by window (pre / post-cap) in /mnt/l2/l2vast/ds3_base4/bv/bv_c.pkl; post-cap S vs R1 full: agreement 96.4%, only-R1 401; pre-cap: 96.6%, only-R1 96.

Where the points go (full rule, points per lot, summed over trades; cut delta = cut P&L minus the original exit P&L):
| window | stored fires, sum | 1-s fires, sum | on the common fires: stored / 1-s | on trades only the 1-s trigger cuts: n, sum (share negative) |
|--|--|--|--|--|
| pre-cap 12 wk | -6,429 | -5,420 | -6,429 / -2,159 | 96, -3,261 (51%) |
| post-cap 25 wk | 8,667 | 4,273 | 8,667 / 24,920 | 401, -20,648 (70%) |
Reading: on the trades both triggers cut, the 1-s trigger fires earlier and that is better (it cuts nearer -30 than the grid row does). It also cuts trades the 10-s grid never saw armed, that is trades that were below -30 only between grid rows; those cuts cost about 51 points per lot each on average post-cap (about 70% of them negative) and more than offset the gain on the common trades. This is consistent with a sampling effect of the stored grid (the grid only cuts trades still below -30 at a grid row), not a reconstruction error; I did not separately trace each of those trades.

## 5. $ effect in the engine (weekly sums; drawdown first)
Engine: ts2 reference, live lots, x-cost 0.80 (the DIS-AX frame); the sample trades' K rows swapped for the rebuilt trigger, all other rows stored. Tie-outs: TH off $2,243,132.77 and stored TH $2,520,149.07 (935 label days), R10 = S to the cent.
| set | n wk | maxDD TH off | maxDD S (stored) | maxDD R1 (1-s) | maxDD S arm-only | maxDD R1 arm-only | sum TH off | sum S | sum R1 | sum S arm-only | sum R1 arm-only |
|--|--|--|--|--|--|--|--|--|--|--|--|
| pre-cap 12 wk | 12 | 16,345 | 7,964 | 5,198 | 8,772 | 5,103 | 389,343 | 399,296 | 392,731 | 393,015 | 357,305 |
| post-cap 25 wk | 25 | 91,353 | 62,576 | 67,067 | 62,123 | 66,898 | 506,259 | 958,165 | 753,830 | 922,000 | 759,295 |
| all 37 wk | 37 | 91,353 | 62,576 | 67,067 | 62,123 | 66,898 | 895,602 | 1,357,461 | 1,146,561 | 1,315,015 | 1,116,600 |
| full history 187 wk | 187 | 222,071 | 122,025 | 138,355 | 119,036 | 133,013 | 2,243,133 | 2,520,149 | 2,309,250 | 2,300,620 | 2,102,204 |
maxDD = maximum drawdown of the weekly-cumulative $ of the listed weeks in calendar order (sample weeks are not contiguous; the 187-week row is the whole history). Carrying weeks are not in the sample rows; the 187-week row includes them as the engine does.

Mean $ per week by window (TH gain = variant minus TH off):
| window | S - off (stored gain) | R1 - off (1-s gain) | R1 - S | Sarm - off | R1arm - off | R1 minus R1arm (liquidity condition, 1-s) | S minus Sarm (liquidity, stored) |
|--|--|--|--|--|--|--|--|
| pre-cap 12 wk | 829 | 282 | -547 | 306 | -2,670 | 2,952 | 523 |
| post-cap 25 wk | 18,076 | 9,903 | -8,173 | 16,630 | 10,121 | -219 | 1,447 |
Week-bootstrap (5,000 draws of the sample weeks) of the mean R1 - S: post-cap -8,173/wk (90% interval -12,987 .. -3,670); pre-cap -547/wk (-4,152 .. 2,675). R1 - S is positive in 7 of 12 pre-cap weeks and 9 of 25 post-cap weeks.
Week-level numbers include engine interactions (week locks, governors, lots re-sizing), so single-week deltas are far larger than the trade-level cut differences; read means and signs, not single weeks. Per-week table: /mnt/l2/l2vast/ds3_base4/bv/bv_d.pkl.

## 6. Stability of the rule parts
* **Stable across constructions (raw vs stored table): both parts.** Same features, same fires, same dollars when evaluated at the same rows.
* **Not stable across cadence (10-s grid vs 1-s): the arm-at-30 crossing, and through it the whole gain.** The arm-only rule alone moves from 16,630 (stored) to 10,121 (1-s) TH gain per post-cap week and from 306 to -2,670 pre-cap; the full rule moves from 18,076 to 9,903 post-cap. Timing: the cut price on common trades is better at 1 s, but trades that only dip through -30 between grid rows are cut at 1 s and recover on the grid.
* **The liquidity condition** adds about 1,447/wk post-cap (stored) and -219/wk (1-s); pre-cap it adds 523/wk (stored) and 2,952/wk (1-s). In the post-cap weeks it is nearly always true once armed, so it is not what selects the cuts there.

## 7. Limits
* Descriptive, no PASS. 37 of 187 weeks; the pre-cap 12 are a fixed-rule sample and the 25 post-cap are all eligible weeks; the post-cap 25 are the same weeks that produced the +18.1k/wk headline.
* R1 evaluates on 1-s closes of the stored 1-s path (last print per second, forward-filled), at the same cost 0.995 market exit; a tick-level or event-driven live trigger would see more brief excursions than R1 and fire on even more of them. The 10-s grid is not a live design choice; if the live process is event-driven the stored-table number overstates the cut's $ gain.
* The rebuilt quantities share the table's definition (C-action size any level; median over 10 behind levels including empties); this tests the table's construction and alignment, not whether the definition is the best proxy for pulled support.
* Latency and cost sensitivity of the cut stay as in DS3_TH_COST.md (DIS-AX); this page changes only the trigger evaluation cadence.
* Engine-level week interactions mean the engine delta (about -$8.2k/wk post-cap) is not the sum of trade-level cut deltas; the trade-level table is the attribution, the engine table is the dollars.
