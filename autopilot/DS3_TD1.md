# DS3_TD1 - ATR-targeted lots per book vs fixed lots (D3SZ, addendum 2 D1, 2026-10-26)
Prereg l2vast/ds3/prereg/D1_prereg.md sha256 0189f259b4cc2d7e4aeecae7c3d92141a024aa57e7fb6d3cf3ba446eb616c3d9 (14 cells, ledger appended, DECISIONS.md). Pre-holdout text DS3_TD1_PREHOLD.md, holdout look logged once (track DS3_TD1). Code l2vast/ds3/code/sz/d1.py (+szlib.py, common.py); rows l2vast/ds3/rows/DS3_TD1.json. Exact 1-s lock engine (asm_lib.run), each book alone with per-book locks whose R follows the row lots (lots x stop x $20); T-J (vol-state sizing from own P&L, DEAD) not repeated: this uses PRICE ATR.
Rule: lots_d = clip(round(nominal x ATRref/ATR20_d), 0.5x..1.5x nominal ["sym"] or 0.5x..1.0x ["cap"]), ATR20 = mean true range of the 20 completed label days before the entry day (NQ pts), ATRref = 230.6 pts (mean over 2023-02..2024-01, fixed). Equivalent to lots = target$/(ATR20 x $20) with target$ = nominal x ATRref x $20.
**Verdict: DEAD, 14/14 cells (0 PASS, 0 CANDIDATE).** WF 142 wk, vs the same book at fixed nominal lots, same locks.
| book | variant | mean lots | WF mean (fixed) | mean ratio | SD ratio | dmaxDD | mean CI | SD-diff CI | holdout (fixed) | placebo rank |
|---|---|---|---|---|---|---|---|---|---|---|
| ST10 | sym | 7.1 | 10,047 (14,350) | 0.70 | 0.70 | -75k | [-8.0k,-1.3k] | [-20.7k,-13.5k] | 10,526 (16,463) | .29 |
| HM10 | sym | 7.0 | 6,594 (10,052) | 0.66 | 0.67 | -86k | [-7.0k,-0.2k] | [-21.1k,-13.8k] | 5,575 (10,598) | .19 |
| WT7 | sym | 5.1 | 872 (1,438) | 0.61 | 0.73 | -32k | [-2.1k,+1.0k] | [-9.0k,-6.2k] | 718 (786) | .33 |
| TE7_kelt3m | sym | 7.1 | 12,096 (16,838) | 0.72 | 0.67 | -82k | [-8.8k,-1.0k] | [-24.0k,-16.0k] | 8,847 (12,773) | .35 |
| TE6_st10m_n7 | sym | 7.2 | 6,044 (9,130) | 0.66 | 0.69 | -36k | [-5.0k,-1.0k] | [-13.4k,-8.8k] | 5,840 (9,423) | .13 |
| TE7_emax5m | sym | 7.2 | 5,322 (7,592) | 0.70 | 0.65 | -80k | [-4.4k,-0.2k] | [-13.3k,-9.6k] | 6,081 (10,120) | .28 |
| TB7_ORBNY | sym | 7.6 | 4,589 (6,074) | 0.76 | 0.64 | -133k | [-4.7k,+1.8k] | [-22.3k,-12.5k] | 2,434 (4,812) | .54 |
(the "cap" variant is within $100/wk of "sym" in every book; all rows in the JSON.)
Reading: SD and maxDD fall significantly (SD ratio 0.64-0.73) but the mean falls by the same fraction (0.61-0.76): mean/SD is unchanged, the V2 sizing criterion needs mean not down, so it fails in 12 of 14 cells on the mean CI. The mean lots are 7.0-7.6, not 10, because WF-era ATR20 (above the 2023-24 reference) pushes lots below nominal: the rule behaves as a proportional de-leveraging (lot ratio ~0.70 equals mean ratio ~0.70), like T-J; the permuted-multiplier placebo (300 day-shuffles of the same multiplier histogram) ranks 0.13-0.54 on mean, i.e. no timing information beyond the average lot level. MDE: weekly mean difference MDE about $3-9k per book (CI half-widths). Nearest scored cell: TJ_w20_f50_STHMWT DEAD (same pattern, mean -11.5%). No registration. Nothing to adopt in T-G3: keep fixed lots.
