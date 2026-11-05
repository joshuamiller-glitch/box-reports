# DS3_INSTR2_ALLINST - all-instrument family null (2026-11-05T20:41Z, ALLINST fork)
Prereg: /mnt/l2/l2vast/ALLINST_PREREG.md sha256 d7912c18 (DECISIONS.md, filed before any statistic). Base: 1-min owned engine, equal-risk lots (RISK/(stop*pv)), fees per FEES.md, window means in $/week as in each cells_all table; forward-only, epoch-second hash worlds.

**Plain sentence: no instrument clears.**

## Tier A - exact joint null (ES, RTY, YM)
All three tables use i2eval.hash_u(entry epoch-second, world w), W=200, statistic zj = min(z_L6M, z_HOLD): the same world index and the same clock across instruments, so the joint max M_joint[w] = max(M_ES, M_RTY, M_YM)[w] is a valid Westfall-Young null over all 1,371,510 eligible cells. Joint null max: median 3.81, p95 4.27 (single-instrument medians 3.57/3.60/3.57). World maxima are nearly uncorrelated across instruments (ES-RTY 0.005, ES-YM -0.09).

| inst | eligible cells | tolerant | best tolerant zj | best tolerant joint family p | cells with joint p <= .10 (all) | BH q <= .10 (tolerant / all) |
|---|---|---|---|---|---|---|
| ES | 456,498 | 8,149 | 3.47 | 0.970 | 6 (non-tolerant, see below) | 0 / 0 |
| RTY | 457,338 | 8,490 | 3.40 | 0.995 | 0 | 0 / 0 |
| YM | 457,674 | 11,605 | 3.36 | 0.995 | 0 | 0 / 0 |
| pooled | 1,371,510 | 28,244 | | | 6 | 0 / 0 |
BH q uses one-sided normal p from zj (approximation, labelled); the family p is the exact one. Pooled table: /mnt/l2/l2vast/allinst_pooled.parquet.

The 6 ES cells with joint p .06-.07 are one pattern: Keltner b3 ema34 atr14 m1.0 contrarian, london session, 30-min time stop (A3/A4/A6, 1.5-2R). Not tolerant: HOLD mean -$170 to -$570/wk, MID/PRE/X'/PRE23 all negative (PRE23 -$4.0k to -$8.5k), persistence 42-50%. L1M/L6M positive only: a NOW-ONLY regime fit, failed gate.

## 13-year check (top-30 tolerant by zj, from the cells_all window columns; the $ at equal-risk lots is approximately scale-free so no separate percent re-scaling was applied - labelled)
| inst | PRE23 mean > 0 | PRE (2024-25) > 0 | X' > 0 | HOLD > 0 | median PRE23 $/wk |
|---|---|---|---|---|---|
| ES | 0/30 | 17/30 | 0/30 | 30/30 | -287 |
| RTY | 2/30 | 7/30 | 3/30 | 30/30 | -94 |
| YM | 0/30 | 10/30 | 9/30 | 30/30 | -300 |
Pre-2023 sign negative for essentially all (>= 50% positive-years criterion fails). Per-year tick/1-s calibration (weekly corr >= .90) was not run by this fork: it is moot because the joint null already rejects; Z2's 13-year check owns the per-year tables.

## Tier B - no per-world artifacts (GC, CL, ZN, ZB, 6E, 6J, MBT/BTCM/BTC, NKD)
No new world draws (different engines/clocks; the artifacts hold only owner finalist nulls). Owner results: GC best p_book 0.05 but family 1.00 (Bonferroni over 132,286 cells); CL 30 finalists p_book 0.13-0.95; 6E no book (winners lost money 2024-25); ZN/ZB/6J/BTC/NKD pages are interim, no verdict yet. A Sidak union over 12 instruments cannot lower any reported family p, so nothing in Tier B clears either; Tier B is NOT a joint-null result and is labelled as such. To make it joint, owners must expose per-world maxima with the same hash_u clock (request logged in MORNING_FLAGS).

## Diversifier-bar verdict
No cell passes tolerant gate + joint family p <= .10 (or q <= .10) + 13-year sign. Walk-forward, corr to NQ stack and Calmar tests not triggered for lack of a candidate. No MORNING alert.
