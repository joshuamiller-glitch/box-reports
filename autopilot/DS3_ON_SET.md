# DS3_ON_SET - the proposed Sunday ON set priced on the DS3_ONE_CONVENTION engine (ON-1, 2026-10-31). POST-HOC, nothing here is a PASS

Capped 20260206, UNTOUCHED never read. Response to DS3_SUNDAY_BRIEF_AUDIT_v6 finding 3. Units $k per week, delta vs the as-is stack under the same convention, MDE (2.8 x SE of the paired weekly delta) in brackets, `*` = beyond MDE. Windows L3M 14 wk / L6M 28 / HOLD 32 / PRE 75 / X' 44. Brief not edited. Code `l2vast/ds3/code/onset/` (run_onset.py, tab_onset.py; imports oneconv/oc_lib.py unchanged), results `l2vast/ds3/out/onset/` (res_0..2.pkl, tables.md, log_*.txt). Tie-out: the six-piece composite rerun with the onset runner reproduces oc_res.pkl (L6M level 41137); six-piece parity rows are the oc_res.pkl rows; the as-is rows are oc_res.pkl. Single set of runs: 140 new scenarios (3 sets x K6 split/market x parity/join 2.45 x lock off/12/20/30 x m0 1.0/0.5 x slip +0.25/+0.45; six-piece parity reused).

## Page 1 - the proposed ON set, priced on the ONE_CONVENTION engine (recent first)

Table 1. Delta vs the as-is stack, $k/wk, MDE (2.8 x SE of the paired weekly delta) in brackets, `*` = beyond MDE. Headline: slip +0.25, A/B parity stop, D6 locks (day entry +5R/-2R, day arm 2R/50%, book week floor 12R), m0 1.0. C1 = no combined lock vs unlocked as-is; C2 = composite with combined F x R_K6 lock vs UNLOCKED as-is; C3 = same lock on both. Last column = L6M level of the row ($k/wk; as-is unlocked 21.7, 12R-locked as-is 10.4). POST-HOC.

| set | convention | L3M | L6M | HOLD | PRE | X' | L6M level |
|---|---|---|---|---|---|---|---|
| ON set, K6 split | C1 no combined lock | +0.6 (17.0) | +0.5 (9.8) | +0.7 (8.8) | +0.4 (4.1) | +3.3 (4.6) | 22.2 |
| ON set, K6 split | C2 12R | -3.5 (27.0) | -5.4 (15.8) | -3.2 (14.7) | -8.9 (10.8) | -1.4 (8.7) | 16.3 |
| ON set, K6 split | C2 20R | +3.0 (17.1) | -1.7 (13.3) | -1.0 (12.1) | -4.6 (7.9) | -0.7 (6.4) | 20.0 |
| ON set, K6 split | C2 30R | +0.6 (17.0) | +0.5 (9.8) | +0.7 (8.8) | -0.2 (4.6) | +3.3 (4.6) | 22.2 |
| ON set, K6 split | C3 12R like-for-like | +4.7 (13.0) | +5.9 (9.7) | +4.9 (8.7) | -0.0 (3.1) | +2.4 (5.2) | 16.3 |
| ON set, K6 market | C1 no combined lock | +1.9 (15.0) | +1.8 (8.5) | +1.5 (7.7) | +0.8 (3.7) | +3.2 (3.7) | 23.5 |
| ON set, K6 market | C2 12R | -3.4 (26.7) | -4.7 (15.5) | -2.8 (14.4) | -8.5 (10.7) | -1.6 (8.6) | 17.0 |
| ON set, K6 market | C2 20R | +3.4 (16.6) | -0.7 (12.8) | -0.4 (11.7) | -3.5 (7.8) | -0.9 (6.1) | 21.0 |
| ON set, K6 market | C2 30R | +1.9 (15.0) | +1.8 (8.5) | +1.5 (7.7) | -0.3 (3.7) | +2.4 (3.2) | 23.5 |
| ON set, K6 market | C3 12R like-for-like | +4.8 (12.2) | +6.6 (8.9) | +5.4 (8.2) | +0.4 (2.7) | +2.2 (4.7) | 17.0 |
| ON + ER sizer P6+K6, K6 split | C1 no combined lock | +8.9 (14.0) | +10.1 (9.6)* | +9.2 (9.5) | +0.9 (9.3) | +4.1 (14.0) | 31.8 |
| ON + ER sizer P6+K6, K6 split | C2 12R | +3.6 (23.1) | +1.7 (14.8) | +4.3 (14.1) | -6.2 (12.4) | +1.8 (12.7) | 23.4 |
| ON + ER sizer P6+K6, K6 split | C2 20R | +4.4 (27.0) | +3.6 (16.2) | +4.9 (15.1) | -4.5 (11.8) | +3.1 (12.1) | 25.3 |
| ON + ER sizer P6+K6, K6 split | C2 30R | +11.2 (16.6) | +9.5 (11.5) | +10.5 (11.0) | -4.5 (12.3) | +4.6 (13.7) | 31.3 |
| ON + ER sizer P6+K6, K6 split | C3 12R like-for-like | +11.8 (22.9) | +13.0 (12.8)* | +12.4 (11.5)* | +2.7 (9.1) | +5.6 (12.0) | 23.4 |
| ON + ER sizer P6+K6, K6 market | C1 no combined lock | +8.3 (13.7) | +10.4 (9.0)* | +9.6 (8.9)* | +0.8 (9.3) | +4.2 (13.7) | 32.1 |
| ON + ER sizer P6+K6, K6 market | C2 12R | +5.0 (22.2) | +3.2 (14.3) | +5.7 (13.6) | -7.5 (12.5) | -0.5 (12.0) | 24.9 |
| ON + ER sizer P6+K6, K6 market | C2 20R | +4.4 (26.6) | +4.6 (15.9) | +6.0 (14.8) | -4.8 (11.4) | +3.2 (11.8) | 26.3 |
| ON + ER sizer P6+K6, K6 market | C2 30R | +11.2 (16.5) | +10.2 (11.0) | +11.2 (10.5)* | -5.1 (12.4) | +4.6 (13.6) | 31.9 |
| ON + ER sizer P6+K6, K6 market | C3 12R like-for-like | +13.2 (22.5) | +14.6 (12.3)* | +13.9 (11.1)* | +1.4 (9.2) | +3.3 (10.5) | 24.9 |
| six-piece composite, K6 split | C1 no combined lock | +22.3 (22.3) | +19.4 (17.5)* | +16.7 (17.3) | +4.5 (13.2) | +11.4 (14.0) | 41.1 |
| six-piece composite, K6 split | C2 12R | +16.9 (27.4) | +10.6 (26.5) | +9.5 (26.7) | -3.5 (15.3) | +4.5 (14.1) | 32.3 |
| six-piece composite, K6 split | C2 20R | +11.6 (34.3) | +13.1 (21.9) | +10.1 (23.3) | -2.7 (15.3) | +6.7 (15.2) | 34.8 |
| six-piece composite, K6 split | C2 30R | +19.4 (24.9) | +16.6 (18.9) | +14.4 (18.2) | -2.5 (14.9) | +10.1 (14.4) | 38.4 |
| six-piece composite, K6 split | C3 12R like-for-like | +25.1 (21.2)* | +21.9 (27.3) | +17.7 (27.2) | +5.4 (11.9) | +8.3 (13.8) | 32.3 |
| six-piece composite, K6 market | C1 no combined lock | +20.2 (21.8) | +18.9 (17.1)* | +16.5 (16.9) | +3.9 (13.1) | +11.5 (13.4) | 40.6 |
| six-piece composite, K6 market | C2 12R | +15.5 (27.0) | +10.3 (26.2) | +9.5 (26.5) | -4.3 (15.3) | +5.1 (13.2) | 32.0 |
| six-piece composite, K6 market | C2 20R | +9.5 (33.5) | +12.6 (21.5) | +9.8 (23.0) | -3.6 (15.1) | +6.5 (14.7) | 34.3 |
| six-piece composite, K6 market | C2 30R | +17.4 (24.2) | +16.2 (18.5) | +14.2 (17.8) | -2.9 (14.9) | +10.0 (13.9) | 37.9 |
| six-piece composite, K6 market | C3 12R like-for-like | +23.7 (21.1)* | +21.7 (27.1) | +17.7 (27.1) | +4.7 (11.9) | +8.9 (13.7) | 32.0 |

Sets. ON set = 70/30 split (K6 split or K6 at market, per row), locks at D6 as stated, A/B parity stop; NO ER sizer, NO PE 45-s, NO zone skip, NO Asia cut. ON + ER = ON plus the ER sizer on P6 and K6 only (integer half-up min-1 lots; running-max locks). Six-piece = split + PE 45-s + zone skip + Asia cut + ER sizer on all six books (reuse of DS3_ONE_CONVENTION oc_res.pkl; tie-out: composite C1 L6M level 41.1, re-run exact). Engine: DS3_ONE_CONVENTION (A6 = PB7 Asia 1 lot, live lots K6 2 / P6 7 / U6 4 / H6 4+2 / M6 2 / A6 1, running max over TAKEN signals, session planned-lot BookR, integer half-up, in-engine day-of-month parity stop). Not in any number: NY-PM end skip, D7 filters, O6. Capped 20260206.

**Plain sentence.** On the ONE_CONVENTION engine the proposed ON set (70/30 split, D6 locks, A/B parity stop; no ER sizer, PE 45-s, zone skip or Asia cut) is worth about nothing against the as-is stack: C1 +0.5 (9.8) L6M with K6 split, +1.8 (8.5) with K6 at market, every window inside MDE, and all of it is the Native stop (Native OFF: -0.8 split / +0.4 market). The combined lock turns it negative against an unlocked as-is (C2 12R -5.4 L6M, PRE -8.9; 20R -1.7; 30R no fire in recent windows so = C1); C3 12R +5.9 flatters because the lock hurts the as-is more. Adding the ER sizer on P6+K6 gives C1 +10.1 (9.6)* L6M (HOLD +9.2 inside MDE, PRE +0.9, X' +4.1) but C2 12R only +1.7 (14.8) and PRE -6.2; the sizer's step over the ON set is +9.6 (12.1) L6M, inside MDE. The six-piece composite's +19.4 / +10.6 therefore splits (L6M, C1) as ON +0.5, ER on P6+K6 +9.6, the remaining pieces (PE 45-s, zone skip, Asia cut, ER on the other four books) +9.3 (12.1); the +19.4 headline is not what the ON set earns. Risk: the composite's smoothness (L6M maxDD 23, worst week -23) is not in the ON set (maxDD 73, worst week -71, vs as-is 88 / -88); ON + ER has maxDD 75 and a deeper PRE tail than the as-is (worst-20 -1009 vs -811). K6 market vs split: +1.2 (2.9) ON set, +0.3 (2.8) with the sizer, inside MDE. ALL POST-HOC; the Native-stop "beyond MDE" flags (Table 2) are an engine unit effect (the 1.28 vs 2.45 saving is an input applied to odd days, MDE tiny because the difference is near-deterministic); the live evidence for it is z 1.6, n 21 vs 8.

## Table 2 - Native OFF (stop = join 2.45 on every day) and the stop's own contribution

Delta vs the same as-is (join 2.45). Row "Native contribution" = parity series minus join-2.45 series of the SAME set and lock (paired, MDE as above).

| row | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| ON set, K6 split C1: Native OFF (join 2.45) | -0.8 (17.1) | -0.8 (9.9) | -0.7 (8.8) | -1.0 (4.1) | +2.3 (4.6) |
| ON set, K6 split C1: Native contribution (parity - join) | +1.4 (0.5)* | +1.3 (0.3)* | +1.4 (0.3)* | +1.4 (0.6)* | +1.1 (0.2)* |
| ON set, K6 split C2 12R: Native OFF (join 2.45) | -4.5 (26.8) | -6.4 (15.6) | -4.1 (14.6) | -10.0 (10.7) | -1.9 (8.7) |
| ON set, K6 split C2 12R: Native contribution (parity - join) | +1.0 (0.7)* | +0.9 (0.5)* | +0.9 (0.4)* | +1.1 (1.8) | +0.4 (0.3)* |
| ON set, K6 split C3 12R: Native OFF (join 2.45) | +3.8 (13.1) | +5.0 (9.7) | +4.0 (8.7) | -1.1 (2.4) | +1.9 (5.2) |
| ON set, K6 split C3 12R: Native contribution (parity - join) | +1.0 (0.7)* | +0.9 (0.5)* | +0.9 (0.4)* | +1.1 (1.8) | +0.4 (0.3)* |
| ON set, K6 market C1: Native OFF (join 2.45) | +0.5 (15.2) | +0.4 (8.6) | +0.2 (7.8) | -0.3 (3.6) | +2.1 (3.7) |
| ON set, K6 market C1: Native contribution (parity - join) | +1.4 (0.5)* | +1.3 (0.3)* | +1.4 (0.3)* | +1.1 (0.5)* | +1.1 (0.2)* |
| ON set, K6 market C2 12R: Native OFF (join 2.45) | -4.6 (26.5) | -5.7 (15.3) | -3.8 (14.2) | -9.6 (10.6) | -1.9 (8.5) |
| ON set, K6 market C2 12R: Native contribution (parity - join) | +1.1 (1.3) | +1.0 (0.7)* | +1.0 (0.6)* | +1.1 (1.5) | +0.4 (0.3)* |
| ON set, K6 market C3 12R: Native OFF (join 2.45) | +3.7 (12.3) | +5.6 (8.9) | +4.4 (8.1) | -0.7 (2.2) | +1.9 (4.6) |
| ON set, K6 market C3 12R: Native contribution (parity - join) | +1.1 (1.3) | +1.0 (0.7)* | +1.0 (0.6)* | +1.1 (1.5) | +0.4 (0.3)* |
| ON + ER sizer P6+K6, K6 split C1: Native OFF (join 2.45) | +7.8 (13.9) | +8.9 (9.6) | +7.9 (9.5) | -0.4 (9.3) | +2.6 (14.1) |
| ON + ER sizer P6+K6, K6 split C1: Native contribution (parity - join) | +1.2 (1.9) | +1.2 (1.0)* | +1.3 (0.9)* | +1.3 (0.4)* | +1.5 (0.8)* |
| ON + ER sizer P6+K6, K6 split C2 12R: Native OFF (join 2.45) | +4.5 (22.3) | -0.0 (14.3) | +2.7 (13.9) | -7.7 (12.6) | +1.4 (12.6) |
| ON + ER sizer P6+K6, K6 split C2 12R: Native contribution (parity - join) | -1.0 (4.9) | +1.7 (5.9) | +1.5 (5.1) | +1.5 (2.6) | +0.4 (0.3)* |
| ON + ER sizer P6+K6, K6 split C3 12R: Native OFF (join 2.45) | +12.8 (22.3) | +11.3 (13.1) | +10.9 (11.7) | +1.2 (9.0) | +5.2 (11.9) |
| ON + ER sizer P6+K6, K6 split C3 12R: Native contribution (parity - join) | -1.0 (4.9) | +1.7 (5.9) | +1.5 (5.1) | +1.5 (2.6) | +0.4 (0.3)* |
| ON + ER sizer P6+K6, K6 market C1: Native OFF (join 2.45) | +7.2 (13.7) | +9.0 (8.8)* | +8.2 (8.8) | -0.6 (9.2) | +2.8 (13.8) |
| ON + ER sizer P6+K6, K6 market C1: Native contribution (parity - join) | +1.1 (1.8) | +1.4 (1.3)* | +1.4 (1.1)* | +1.4 (0.4)* | +1.4 (0.8)* |
| ON + ER sizer P6+K6, K6 market C2 12R: Native OFF (join 2.45) | +4.2 (21.8) | +2.2 (13.9) | +4.8 (13.4) | -7.2 (12.3) | -0.9 (12.0) |
| ON + ER sizer P6+K6, K6 market C2 12R: Native contribution (parity - join) | +0.8 (0.7)* | +1.0 (1.0)* | +0.9 (0.9) | -0.2 (1.6) | +0.4 (0.2)* |
| ON + ER sizer P6+K6, K6 market C3 12R: Native OFF (join 2.45) | +12.4 (22.4) | +13.5 (12.2)* | +13.0 (11.0)* | +1.7 (9.2) | +2.9 (10.4) |
| ON + ER sizer P6+K6, K6 market C3 12R: Native contribution (parity - join) | +0.8 (0.7)* | +1.0 (1.0)* | +0.9 (0.9) | -0.2 (1.6) | +0.4 (0.2)* |
| six-piece composite, K6 split C1: Native OFF (join 2.45) | +21.7 (21.9) | +18.5 (17.4)* | +15.7 (17.1) | +3.3 (13.2) | +10.6 (14.0) |
| six-piece composite, K6 split C1: Native contribution (parity - join) | +0.6 (1.7) | +0.9 (0.9)* | +1.0 (0.8)* | +1.2 (0.3)* | +0.8 (0.2)* |
| six-piece composite, K6 split C2 12R: Native OFF (join 2.45) | +16.2 (27.2) | +9.8 (26.3) | +8.7 (26.6) | -4.6 (15.2) | +3.1 (14.0) |
| six-piece composite, K6 split C2 12R: Native contribution (parity - join) | +0.7 (0.6)* | +0.8 (0.4)* | +0.8 (0.4)* | +1.0 (1.0)* | +1.4 (2.7) |
| six-piece composite, K6 split C3 12R: Native OFF (join 2.45) | +24.4 (20.9)* | +21.1 (27.2) | +16.9 (27.1) | +4.4 (12.0) | +6.9 (13.7) |
| six-piece composite, K6 split C3 12R: Native contribution (parity - join) | +0.7 (0.6)* | +0.8 (0.4)* | +0.8 (0.4)* | +1.0 (1.0)* | +1.4 (2.7) |
| six-piece composite, K6 market C1: Native OFF (join 2.45) | +19.6 (21.4) | +18.0 (17.0)* | +15.4 (16.7) | +2.7 (13.1) | +10.7 (13.4) |
| six-piece composite, K6 market C1: Native contribution (parity - join) | +0.6 (1.7) | +0.9 (0.9)* | +1.0 (0.8)* | +1.2 (0.3)* | +0.8 (0.2)* |
| six-piece composite, K6 market C2 12R: Native OFF (join 2.45) | +14.7 (26.8) | +9.5 (26.0) | +8.7 (26.3) | -4.8 (15.2) | +3.8 (13.6) |
| six-piece composite, K6 market C2 12R: Native contribution (parity - join) | +0.8 (0.5)* | +0.9 (0.4)* | +0.8 (0.5)* | +0.6 (0.3)* | +1.3 (2.3) |
| six-piece composite, K6 market C3 12R: Native OFF (join 2.45) | +22.9 (20.8)* | +20.8 (27.0) | +16.8 (26.8) | +4.1 (11.8) | +7.6 (13.3) |
| six-piece composite, K6 market C3 12R: Native contribution (parity - join) | +0.8 (0.5)* | +0.9 (0.4)* | +0.8 (0.5)* | +0.6 (0.3)* | +1.3 (2.3) |

## Table 3 - levels, $k/wk (mean per week), headline slip +0.25

| row | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| as-is unlocked | 12.2 | 21.7 | 21.9 | 18.6 | -3.4 |
| as-is 12R | 3.9 | 10.4 | 13.7 | 9.7 | -7.2 |
| as-is 20R | 15.0 | 18.8 | 19.8 | 13.6 | -8.3 |
| as-is 30R | 13.3 | 22.3 | 22.5 | 16.3 | -3.4 |
| ON set, K6 split, parity, no combined lock | 12.7 | 22.2 | 22.5 | 19.0 | -0.1 |
| ON set, K6 split, parity, 12R | 8.6 | 16.3 | 18.6 | 9.7 | -4.8 |
| ON set, K6 split, parity, 20R | 15.2 | 20.0 | 20.9 | 14.0 | -4.1 |
| ON set, K6 split, parity, 30R | 12.7 | 22.2 | 22.6 | 18.4 | -0.1 |
| ON set, K6 split, Native OFF, no combined lock | 11.3 | 20.9 | 21.2 | 17.6 | -1.1 |
| ON set, K6 market, parity, no combined lock | 14.1 | 23.5 | 23.4 | 19.5 | -0.3 |
| ON set, K6 market, parity, 12R | 8.7 | 17.0 | 19.1 | 10.1 | -5.0 |
| ON set, K6 market, parity, 20R | 15.5 | 21.0 | 21.5 | 15.1 | -4.3 |
| ON set, K6 market, parity, 30R | 14.1 | 23.5 | 23.4 | 18.3 | -1.0 |
| ON set, K6 market, Native OFF, no combined lock | 12.7 | 22.1 | 22.0 | 18.3 | -1.3 |
| ON + ER sizer P6+K6, K6 split, parity, no combined lock | 21.1 | 31.8 | 31.1 | 19.5 | 0.7 |
| ON + ER sizer P6+K6, K6 split, parity, 12R | 15.7 | 23.4 | 26.1 | 12.4 | -1.7 |
| ON + ER sizer P6+K6, K6 split, parity, 20R | 16.5 | 25.3 | 26.8 | 14.2 | -0.4 |
| ON + ER sizer P6+K6, K6 split, parity, 30R | 23.4 | 31.3 | 32.4 | 14.1 | 1.2 |
| ON + ER sizer P6+K6, K6 split, Native OFF, no combined lock | 19.9 | 30.6 | 29.8 | 18.2 | -0.8 |
| ON + ER sizer P6+K6, K6 market, parity, no combined lock | 20.4 | 32.1 | 31.5 | 19.4 | 0.8 |
| ON + ER sizer P6+K6, K6 market, parity, 12R | 17.1 | 24.9 | 27.6 | 11.1 | -3.9 |
| ON + ER sizer P6+K6, K6 market, parity, 20R | 16.6 | 26.3 | 27.9 | 13.8 | -0.2 |
| ON + ER sizer P6+K6, K6 market, parity, 30R | 23.4 | 31.9 | 33.1 | 13.5 | 1.2 |
| ON + ER sizer P6+K6, K6 market, Native OFF, no combined lock | 19.3 | 30.7 | 30.0 | 18.0 | -0.6 |
| six-piece composite, K6 split, parity, no combined lock | 34.4 | 41.1 | 38.6 | 23.1 | 8.0 |
| six-piece composite, K6 split, parity, 12R | 29.0 | 32.3 | 31.4 | 15.1 | 1.0 |
| six-piece composite, K6 split, parity, 20R | 23.8 | 34.8 | 32.0 | 15.9 | 3.3 |
| six-piece composite, K6 split, parity, 30R | 31.6 | 38.4 | 36.3 | 16.1 | 6.7 |
| six-piece composite, K6 split, Native OFF, no combined lock | 33.8 | 40.2 | 37.6 | 21.9 | 7.2 |
| six-piece composite, K6 market, parity, no combined lock | 32.4 | 40.6 | 38.3 | 22.5 | 8.1 |
| six-piece composite, K6 market, parity, 12R | 27.6 | 32.0 | 31.4 | 14.3 | 1.7 |
| six-piece composite, K6 market, parity, 20R | 21.6 | 34.3 | 31.7 | 15.0 | 3.0 |
| six-piece composite, K6 market, parity, 30R | 29.6 | 37.9 | 36.1 | 15.7 | 6.6 |
| six-piece composite, K6 market, Native OFF, no combined lock | 31.8 | 39.7 | 37.3 | 21.3 | 7.3 |

## Table 4 - extra conventions: m0 0.5, stress slip +0.45, 20R/30R like-for-like (C2 vs unlocked as-is; C3 same lock both)

| row | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| ON set, K6 split C2 12R m0 0.5 | -1.2 (26.9) | -3.7 (15.7) | -1.8 (14.5) | -8.7 (10.6) | -2.6 (8.1) |
| ON set, K6 split C2 20R m0 0.5 | -0.1 (21.4) | -2.4 (13.5) | -1.1 (12.4) | -6.9 (9.7) | -0.2 (7.3) |
| ON set, K6 split C2 30R m0 0.5 | +2.6 (18.6) | +0.8 (11.0) | +1.7 (10.4) | -3.9 (7.9) | -0.2 (6.4) |
| ON set, K6 split C3 20R | +0.2 (15.1) | +1.2 (8.8) | +1.1 (7.9) | +0.3 (4.1) | +4.1 (5.7) |
| ON set, K6 split C3 30R | -0.6 (16.7) | -0.0 (9.7) | +0.0 (8.6) | +2.1 (6.7) | +3.4 (4.6) |
| ON set, K6 split stress +0.45 C1 | +0.2 (17.2) | +0.2 (9.9) | +0.3 (8.8) | +0.1 (4.1) | +3.1 (4.6) |
| ON set, K6 split stress +0.45 C2 12R | -3.6 (26.9) | -5.6 (15.8) | -3.4 (14.6) | -9.7 (10.7) | -1.6 (8.7) |
| ON set, K6 split stress +0.45 C2 20R | +2.7 (17.2) | -2.0 (13.3) | -1.3 (12.1) | -4.9 (7.9) | -0.9 (6.4) |
| ON set, K6 split stress +0.45 C2 30R | +0.2 (17.2) | +0.2 (9.9) | +0.4 (8.8) | -0.5 (4.6) | +3.1 (4.6) |
| ON set, K6 market C2 12R m0 0.5 | -1.2 (26.6) | -3.6 (15.4) | -1.8 (14.3) | -6.8 (10.4) | -2.2 (8.4) |
| ON set, K6 market C2 20R m0 0.5 | +0.8 (21.9) | -1.1 (13.4) | -0.2 (12.3) | -5.2 (9.3) | -0.4 (7.1) |
| ON set, K6 market C2 30R m0 0.5 | +3.6 (18.6) | +2.0 (10.6) | +2.5 (10.0) | -3.3 (7.8) | -0.6 (6.0) |
| ON set, K6 market C3 20R | +0.6 (14.6) | +2.2 (7.9) | +1.7 (7.2) | +1.4 (4.2) | +4.0 (5.4) |
| ON set, K6 market C3 30R | +0.8 (14.6) | +1.2 (8.3) | +0.9 (7.5) | +2.0 (6.1) | +2.4 (3.2) |
| ON set, K6 market stress +0.45 C1 | +1.7 (15.2) | +1.5 (8.6) | +1.3 (7.8) | +0.6 (3.7) | +3.0 (3.7) |
| ON set, K6 market stress +0.45 C2 12R | -3.6 (26.7) | -4.9 (15.4) | -3.0 (14.4) | -8.7 (10.7) | -1.6 (8.6) |
| ON set, K6 market stress +0.45 C2 20R | +3.2 (16.7) | -0.9 (12.8) | -0.6 (11.7) | -3.7 (7.8) | -1.1 (6.1) |
| ON set, K6 market stress +0.45 C2 30R | +1.7 (15.2) | +1.5 (8.6) | +1.3 (7.8) | -0.6 (3.7) | +2.2 (3.2) |
| ON + ER sizer P6+K6, K6 split C2 12R m0 0.5 | +3.5 (23.1) | +1.6 (14.8) | +4.3 (14.1) | -8.2 (13.4) | +2.7 (12.4) |
| ON + ER sizer P6+K6, K6 split C2 20R m0 0.5 | +2.6 (27.4) | +2.7 (16.4) | +4.1 (15.2) | -5.0 (11.5) | +2.4 (12.6) |
| ON + ER sizer P6+K6, K6 split C2 30R m0 0.5 | +3.2 (26.8) | +5.5 (15.5) | +7.0 (14.3) | -4.9 (11.8) | +4.0 (13.8) |
| ON + ER sizer P6+K6, K6 split C3 20R | +1.6 (24.9) | +6.5 (14.2) | +7.0 (12.7) | +0.5 (10.4) | +7.9 (11.7) |
| ON + ER sizer P6+K6, K6 split C3 30R | +10.1 (15.2) | +9.0 (11.0) | +9.9 (10.5) | -2.2 (11.8) | +4.6 (13.7) |
| ON + ER sizer P6+K6, K6 split stress +0.45 C1 | +8.5 (13.9) | +9.7 (9.6)* | +8.8 (9.5) | +0.6 (9.3) | +3.5 (14.1) |
| ON + ER sizer P6+K6, K6 split stress +0.45 C2 12R | +5.0 (22.5) | +2.3 (14.5) | +4.8 (13.9) | -6.7 (12.4) | +1.7 (12.6) |
| ON + ER sizer P6+K6, K6 split stress +0.45 C2 20R | +4.0 (27.0) | +3.2 (16.2) | +4.6 (15.1) | -4.6 (11.8) | +2.9 (12.1) |
| ON + ER sizer P6+K6, K6 split stress +0.45 C2 30R | +10.6 (16.7) | +9.0 (11.5) | +10.0 (11.0) | -4.7 (12.3) | +4.3 (13.7) |
| ON + ER sizer P6+K6, K6 market C2 12R m0 0.5 | +5.0 (22.2) | +3.2 (14.3) | +5.7 (13.6) | -9.2 (13.4) | +0.5 (11.8) |
| ON + ER sizer P6+K6, K6 market C2 20R m0 0.5 | +2.2 (26.8) | +3.5 (16.0) | +5.0 (14.9) | -4.7 (11.6) | +2.1 (12.5) |
| ON + ER sizer P6+K6, K6 market C2 30R m0 0.5 | +5.0 (26.1) | +7.1 (14.8) | +8.4 (13.7) | -5.5 (11.9) | +4.2 (13.8) |
| ON + ER sizer P6+K6, K6 market C3 20R | +1.6 (24.5) | +7.6 (13.9) | +8.0 (12.4) | +0.2 (10.2) | +8.1 (11.3) |
| ON + ER sizer P6+K6, K6 market C3 30R | +10.1 (15.0) | +9.6 (10.5) | +10.5 (10.0)* | -2.7 (11.9) | +4.7 (13.6) |
| ON + ER sizer P6+K6, K6 market stress +0.45 C1 | +7.9 (13.6) | +10.0 (8.9)* | +9.3 (8.9)* | +0.6 (9.3) | +3.7 (13.8) |
| ON + ER sizer P6+K6, K6 market stress +0.45 C2 12R | +4.8 (22.1) | +3.0 (14.2) | +5.5 (13.6) | -7.5 (12.5) | -0.6 (12.0) |
| ON + ER sizer P6+K6, K6 market stress +0.45 C2 20R | +4.1 (26.5) | +4.3 (15.8) | +5.7 (14.7) | -5.5 (11.6) | +3.1 (11.8) |
| ON + ER sizer P6+K6, K6 market stress +0.45 C2 30R | +10.9 (16.5) | +9.9 (11.0) | +10.9 (10.5)* | -5.2 (12.4) | +4.5 (13.6) |
| six-piece composite, K6 split C2 12R m0 0.5 | +16.8 (27.4) | +10.8 (26.4) | +10.2 (26.2) | -7.7 (15.2) | +5.4 (13.6) |
| six-piece composite, K6 split C2 20R m0 0.5 | +11.3 (34.0) | +13.0 (21.8) | +10.0 (23.2) | -2.7 (15.6) | +6.3 (14.8) |
| six-piece composite, K6 split C2 30R m0 0.5 | +12.4 (35.1) | +13.1 (22.4) | +12.3 (21.1) | -1.8 (14.7) | +10.0 (14.4) |
| six-piece composite, K6 split C3 20R | +8.8 (32.4) | +16.1 (24.4) | +12.2 (24.8) | +2.2 (14.9) | +11.6 (15.4) |
| six-piece composite, K6 split C3 30R | +18.3 (23.8) | +16.1 (18.6) | +13.8 (17.9) | -0.1 (14.5) | +10.2 (14.4) |
| six-piece composite, K6 split stress +0.45 C1 | +21.9 (22.2) | +18.9 (17.3)* | +16.3 (17.1) | +4.1 (13.2) | +11.1 (14.0) |
| six-piece composite, K6 split stress +0.45 C2 12R | +16.6 (27.4) | +10.2 (26.3) | +9.2 (26.6) | -3.7 (15.3) | +4.3 (14.1) |
| six-piece composite, K6 split stress +0.45 C2 20R | +11.3 (34.2) | +12.7 (21.7) | +9.8 (23.2) | -3.0 (15.3) | +6.5 (15.2) |
| six-piece composite, K6 split stress +0.45 C2 30R | +19.0 (24.8) | +16.2 (18.7) | +14.0 (18.1) | -2.7 (14.9) | +9.9 (14.4) |
| six-piece composite, K6 market C2 12R m0 0.5 | +15.5 (27.0) | +10.6 (26.1) | +10.2 (26.0) | -8.5 (15.1) | +6.1 (12.7) |
| six-piece composite, K6 market C2 20R m0 0.5 | +9.7 (33.7) | +12.6 (21.6) | +9.9 (23.0) | -3.1 (15.5) | +6.0 (14.3) |
| six-piece composite, K6 market C2 30R m0 0.5 | +10.3 (34.3) | +12.6 (22.0) | +11.1 (20.6) | -2.2 (14.7) | +10.0 (13.8) |
| six-piece composite, K6 market C3 20R | +6.7 (31.8) | +15.5 (24.1) | +11.8 (24.6) | +1.3 (14.9) | +11.3 (14.9) |
| six-piece composite, K6 market C3 30R | +16.3 (23.2) | +15.6 (18.2) | +13.6 (17.5) | -0.6 (14.4) | +10.1 (13.9) |
| six-piece composite, K6 market stress +0.45 C1 | +20.0 (21.8) | +18.5 (16.9)* | +16.1 (16.7) | +3.6 (13.1) | +11.3 (13.4) |
| six-piece composite, K6 market stress +0.45 C2 12R | +15.3 (26.9) | +10.0 (26.0) | +9.2 (26.4) | -4.4 (15.3) | +5.0 (13.2) |
| six-piece composite, K6 market stress +0.45 C2 20R | +12.1 (28.2) | +13.6 (19.4) | +10.7 (21.6) | -3.8 (15.1) | +6.3 (14.7) |
| six-piece composite, K6 market stress +0.45 C2 30R | +17.1 (24.2) | +15.7 (18.3) | +13.8 (17.7) | -3.1 (14.8) | +9.9 (13.8) |

## Table 5 - risk lines, weekly series: mean / SD / maxDD / worst week / worst-20 sum ($k), composite and as-is with the SAME combined lock (m0 1.0, slip +0.25, parity stop)

| lock | row | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| off | as-is | 12.2/45.5/88/-88/170 | 21.7/43.9/88/-88/58 | 21.9/53.8/144/-88/-187 | 18.6/50.4/162/-96/-811 | -3.4/29.0/317/-71/-572 |
| off | ON set, K6 split | 12.7/46.1/73/-71/178 | 22.2/44.0/73/-71/53 | 22.5/52.4/128/-73/-165 | 19.0/47.2/114/-85/-737 | -0.1/28.2/224/-63/-511 |
| off | ON set, K6 market | 14.1/43.4/69/-69/197 | 23.5/44.3/69/-69/69 | 23.4/52.2/129/-71/-149 | 19.5/47.0/122/-83/-734 | -0.3/28.5/231/-55/-519 |
| off | ON + ER sizer P6+K6, K6 split | 21.1/50.8/75/-75/295 | 31.8/45.0/75/-75/216 | 31.1/57.3/151/-84/-68 | 19.5/57.2/248/-115/-1009 | 0.7/42.2/220/-90/-771 |
| off | ON + ER sizer P6+K6, K6 market | 20.4/51.6/86/-86/286 | 32.1/46.5/86/-86/216 | 31.5/58.5/151/-86/-58 | 19.4/57.3/244/-114/-1016 | 0.8/42.4/213/-88/-770 |
| off | six-piece composite, K6 split | 34.4/44.7/21/-21/482 | 41.1/42.7/23/-23/371 | 38.6/51.8/97/-68/136 | 23.1/55.7/241/-120/-875 | 8.0/32.6/121/-66/-420 |
| off | six-piece composite, K6 market | 32.4/45.3/27/-27/454 | 40.6/42.5/27/-27/372 | 38.3/51.9/95/-67/136 | 22.5/55.6/240/-116/-878 | 8.1/32.1/114/-66/-407 |
| 12R | as-is | 3.9/40.7/105/-30/55 | 10.4/46.0/116/-30/-260 | 13.7/53.4/116/-30/-433 | 9.7/46.9/276/-30/-585 | -7.2/25.5/436/-30/-584 |
| 12R | ON set, K6 split | 8.6/40.0/50/-29/121 | 16.3/44.4/59/-29/-114 | 18.6/51.0/87/-29/-286 | 9.7/45.0/271/-31/-589 | -4.8/26.8/351/-30/-584 |
| 12R | ON set, K6 market | 8.7/39.2/48/-29/122 | 17.0/45.8/59/-29/-113 | 19.1/51.6/87/-29/-284 | 10.1/45.2/259/-31/-586 | -5.0/27.0/353/-30/-584 |
| 12R | ON + ER sizer P6+K6, K6 split | 15.7/50.4/53/-44/220 | 23.4/47.5/53/-44/-20 | 26.1/55.3/73/-44/-208 | 12.4/49.2/298/-45/-577 | -1.7/31.0/174/-44/-450 |
| 12R | ON + ER sizer P6+K6, K6 market | 17.1/48.1/43/-43/240 | 24.9/47.4/47/-43/15 | 27.6/55.5/73/-44/-178 | 11.1/49.5/358/-45/-629 | -3.9/30.0/269/-44/-453 |
| 12R | six-piece composite, K6 split | 29.0/48.4/27/-27/406 | 32.3/45.2/27/-27/181 | 31.4/48.9/35/-27/-6 | 15.1/49.8/233/-46/-608 | 1.0/30.1/120/-45/-468 |
| 12R | six-piece composite, K6 market | 27.6/47.9/26/-26/387 | 32.0/44.9/26/-26/184 | 31.4/49.2/37/-26/-11 | 14.3/49.4/229/-46/-615 | 1.7/29.9/119/-43/-467 |
| 20R | as-is | 15.0/39.7/49/-49/209 | 18.8/44.7/96/-49/-24 | 19.8/53.4/127/-49/-253 | 13.6/51.3/229/-49/-955 | -8.3/31.7/463/-49/-766 |
| 20R | ON set, K6 split | 15.2/41.8/48/-48/212 | 20.0/45.1/97/-49/-10 | 20.9/52.6/119/-49/-218 | 14.0/49.0/228/-49/-928 | -4.1/32.0/392/-49/-683 |
| 20R | ON set, K6 market | 15.5/40.6/48/-48/217 | 21.0/46.2/98/-49/-1 | 21.5/53.1/122/-49/-211 | 15.1/48.4/232/-49/-896 | -4.3/32.3/400/-48/-689 |
| 20R | ON + ER sizer P6+K6, K6 split | 16.5/50.0/63/-50/231 | 25.3/47.0/63/-50/33 | 26.8/56.0/105/-57/-187 | 14.2/52.1/232/-62/-683 | -0.4/35.5/240/-72/-619 |
| 20R | ON + ER sizer P6+K6, K6 market | 16.6/49.0/54/-49/232 | 26.3/47.7/54/-49/54 | 27.9/56.7/105/-56/-170 | 13.8/51.9/251/-62/-673 | -0.2/35.5/232/-72/-611 |
| 20R | six-piece composite, K6 split | 23.8/54.7/64/-64/333 | 34.8/50.0/64/-64/195 | 32.0/55.1/65/-64/-60 | 15.9/53.3/190/-72/-754 | 3.3/32.6/133/-58/-537 |
| 20R | six-piece composite, K6 market | 21.6/54.6/63/-63/303 | 34.3/49.7/63/-63/194 | 31.7/55.4/67/-63/-63 | 15.0/53.2/225/-73/-776 | 3.0/32.3/135/-58/-538 |
| 30R | as-is | 13.3/43.0/73/-73/186 | 22.3/42.5/73/-73/73 | 22.5/52.6/139/-73/-166 | 16.3/52.1/145/-73/-927 | -3.4/29.0/318/-72/-573 |
| 30R | ON set, K6 split | 12.7/46.1/73/-71/178 | 22.2/44.0/73/-71/53 | 22.6/52.4/128/-72/-164 | 18.4/48.1/145/-85/-782 | -0.1/28.2/224/-63/-511 |
| 30R | ON set, K6 market | 14.1/43.4/69/-69/197 | 23.5/44.3/69/-69/69 | 23.4/52.2/131/-72/-150 | 18.3/48.7/200/-75/-822 | -1.0/30.0/266/-72/-554 |
| 30R | ON + ER sizer P6+K6, K6 split | 23.4/46.6/52/-36/328 | 31.3/44.4/52/-37/201 | 32.4/53.8/94/-56/-26 | 14.1/55.5/292/-79/-892 | 1.2/39.7/194/-56/-728 |
| 30R | ON + ER sizer P6+K6, K6 market | 23.4/45.8/54/-36/327 | 31.9/44.9/54/-37/211 | 33.1/54.5/94/-55/-7 | 13.5/55.6/297/-79/-887 | 1.2/40.2/190/-55/-731 |
| 30R | six-piece composite, K6 split | 31.6/48.0/37/-37/442 | 38.4/46.4/37/-37/293 | 36.3/54.1/92/-68/64 | 16.1/55.0/208/-92/-888 | 6.7/33.3/133/-58/-474 |
| 30R | six-piece composite, K6 market | 29.6/48.4/36/-36/414 | 37.9/46.1/36/-36/295 | 36.1/54.1/90/-66/65 | 15.7/54.5/210/-90/-887 | 6.6/32.9/136/-58/-471 |

Native OFF (join 2.45), no combined lock and 12R:

| lock | row | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| off | ON set, K6 split Native OFF | 11.3/46.5/78/-74/159 | 20.9/44.2/78/-74/25 | 21.2/52.7/134/-75/-195 | 17.6/47.7/122/-86/-784 | -1.1/28.3/246/-65/-534 |
| off | ON set, K6 market Native OFF | 12.7/43.7/71/-71/178 | 22.1/44.4/71/-71/41 | 22.0/52.4/135/-73/-178 | 18.3/47.6/131/-84/-770 | -1.3/28.6/252/-57/-541 |
| off | ON + ER sizer P6+K6, K6 split Native OFF | 19.9/51.1/78/-78/279 | 30.6/45.0/78/-78/194 | 29.8/57.4/157/-86/-93 | 18.2/57.4/257/-117/-1042 | -0.8/42.8/256/-93/-810 |
| off | ON + ER sizer P6+K6, K6 market Native OFF | 19.3/51.8/89/-89/270 | 30.7/46.4/89/-89/189 | 30.0/58.6/156/-89/-87 | 18.0/57.5/255/-115/-1049 | -0.6/43.0/248/-90/-807 |
| off | six-piece composite, K6 split Native OFF | 33.8/44.4/24/-24/473 | 40.2/42.4/24/-24/357 | 37.6/51.6/103/-69/118 | 21.9/55.8/250/-121/-903 | 7.2/32.7/125/-66/-436 |
| off | six-piece composite, K6 market Native OFF | 31.8/45.0/29/-29/445 | 39.7/42.2/29/-29/357 | 37.3/51.8/101/-68/118 | 21.3/55.6/249/-118/-905 | 7.3/32.0/118/-67/-424 |
| 12R | ON set, K6 split Native OFF | 7.7/39.9/52/-30/108 | 15.3/44.1/58/-30/-130 | 17.7/50.7/88/-30/-301 | 8.6/44.9/279/-31/-589 | -5.3/26.4/363/-30/-580 |
| 12R | ON set, K6 market Native OFF | 7.6/39.2/50/-29/106 | 16.0/45.6/58/-29/-132 | 18.1/51.3/88/-30/-301 | 9.0/45.1/270/-31/-587 | -5.4/26.6/365/-29/-580 |
| 12R | ON + ER sizer P6+K6, K6 split Native OFF | 16.7/48.3/44/-44/234 | 21.7/46.4/48/-44/-55 | 24.6/54.5/73/-44/-241 | 10.9/49.1/376/-44/-586 | -2.0/30.7/181/-44/-452 |
| 12R | ON + ER sizer P6+K6, K6 market Native OFF | 16.4/47.5/43/-43/229 | 23.9/46.7/47/-43/-1 | 26.7/54.9/73/-43/-185 | 11.4/48.6/332/-45/-584 | -4.3/29.8/280/-44/-458 |
| 12R | six-piece composite, K6 split Native OFF | 28.3/48.0/27/-27/396 | 31.5/44.8/27/-27/167 | 30.6/48.5/35/-27/-20 | 14.1/49.8/247/-47/-631 | -0.3/29.6/152/-45/-471 |
| 12R | six-piece composite, K6 market Native OFF | 26.8/47.6/27/-27/376 | 31.2/44.5/27/-27/169 | 30.6/48.8/35/-27/-23 | 13.8/49.1/229/-47/-624 | 0.4/29.5/122/-44/-469 |

## Table 6 - per-book contribution at live lots: book delta vs the as-is book, $k/wk (MDE of the book delta), no combined lock (C1), parity stop. Sum of books = the C1 row of Table 1.

**ON set, K6 split**

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K6 | -1.1 (3.2) | -1.0 (2.8) | -0.7 (2.6) | -0.4 (1.2) | +0.3 (1.4) |
| P6 | -0.1 (12.9) | -0.3 (7.3) | -0.7 (6.5) | +1.2 (3.1) | +2.7 (2.9) |
| U6 | +1.0 (2.0) | +1.5 (1.7) | +1.6 (1.6) | -0.1 (0.4) | -0.2 (0.5) |
| H6 | +0.3 (3.5) | -0.1 (2.1) | -0.1 (1.9) | -0.5 (1.6) | +0.4 (2.1) |
| M6 | +0.5 (1.3) | +0.5 (1.3) | +0.4 (1.1) | +0.2 (0.8) | +0.1 (0.6) |
| A6 | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* |
| sum | +0.6 (17.0) | +0.5 (9.8) | +0.7 (8.8) | +0.4 (4.1) | +3.3 (4.6) |

**ON set, K6 market**

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K6 | +0.2 (0.1)* | +0.2 (0.1)* | +0.2 (0.1)* | +0.0 (0.3) | +0.1 (0.0)* |
| P6 | -0.1 (12.9) | -0.3 (7.3) | -0.7 (6.5) | +1.2 (3.1) | +2.7 (2.9) |
| U6 | +1.0 (2.0) | +1.5 (1.7) | +1.6 (1.6) | -0.1 (0.4) | -0.2 (0.5) |
| H6 | +0.3 (3.5) | -0.1 (2.1) | -0.1 (1.9) | -0.5 (1.6) | +0.4 (2.1) |
| M6 | +0.5 (1.3) | +0.5 (1.3) | +0.4 (1.1) | +0.2 (0.8) | +0.1 (0.6) |
| A6 | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* |
| sum | +1.9 (15.0) | +1.8 (8.5) | +1.5 (7.7) | +0.8 (3.7) | +3.2 (3.7) |

**ON + ER sizer P6+K6, K6 split**

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K6 | +3.2 (9.0) | +1.7 (6.3) | +1.5 (5.6) | -0.4 (3.2) | +0.2 (3.2) |
| P6 | +4.0 (16.7) | +6.5 (9.9) | +5.7 (9.3) | +1.6 (8.6) | +3.6 (12.4) |
| U6 | +1.0 (2.0) | +1.5 (1.7) | +1.6 (1.6) | -0.1 (0.4) | -0.2 (0.5) |
| H6 | +0.3 (3.5) | -0.1 (2.1) | -0.1 (1.9) | -0.5 (1.6) | +0.4 (2.1) |
| M6 | +0.5 (1.3) | +0.5 (1.3) | +0.4 (1.1) | +0.2 (0.8) | +0.1 (0.6) |
| A6 | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* |
| sum | +8.9 (14.0) | +10.1 (9.6)* | +9.2 (9.5) | +0.9 (9.3) | +4.1 (14.0) |

**ON + ER sizer P6+K6, K6 market**

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K6 | +2.5 (8.8) | +2.0 (5.3) | +1.9 (4.7) | -0.5 (3.1) | +0.3 (3.0) |
| P6 | +4.0 (16.7) | +6.5 (9.9) | +5.7 (9.3) | +1.6 (8.6) | +3.6 (12.4) |
| U6 | +1.0 (2.0) | +1.5 (1.7) | +1.6 (1.6) | -0.1 (0.4) | -0.2 (0.5) |
| H6 | +0.3 (3.5) | -0.1 (2.1) | -0.1 (1.9) | -0.5 (1.6) | +0.4 (2.1) |
| M6 | +0.5 (1.3) | +0.5 (1.3) | +0.4 (1.1) | +0.2 (0.8) | +0.1 (0.6) |
| A6 | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* |
| sum | +8.3 (13.7) | +10.4 (9.0)* | +9.6 (8.9)* | +0.8 (9.3) | +4.2 (13.7) |

**six-piece composite, K6 split**

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K6 | +5.1 (7.5) | +2.0 (5.6) | +1.6 (5.0) | -0.3 (3.1) | +0.8 (3.6) |
| P6 | +16.1 (22.1) | +15.3 (15.1)* | +13.1 (14.5) | +5.4 (9.9) | +7.1 (11.1) |
| U6 | -2.1 (7.7) | -1.2 (5.2) | -1.0 (5.1) | -0.3 (3.1) | +1.5 (3.5) |
| H6 | +2.8 (6.6) | +2.9 (6.2) | +2.6 (5.6) | -0.7 (4.1) | +0.5 (3.5) |
| M6 | -0.3 (4.3) | -0.5 (2.9) | -0.6 (2.7) | +0.0 (1.9) | +1.0 (2.0) |
| A6 | +0.8 (1.9) | +0.9 (1.5) | +0.9 (1.3) | +0.4 (0.7) | +0.4 (0.8) |
| sum | +22.3 (22.3) | +19.4 (17.5)* | +16.7 (17.3) | +4.5 (13.2) | +11.4 (14.0) |

**six-piece composite, K6 market**

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K6 | +3.1 (7.0) | +1.5 (4.8) | +1.3 (4.4) | -0.9 (3.0) | +0.9 (3.2) |
| P6 | +16.1 (22.1) | +15.3 (15.1)* | +13.1 (14.5) | +5.4 (9.9) | +7.1 (11.1) |
| U6 | -2.1 (7.7) | -1.2 (5.2) | -0.9 (5.1) | -0.3 (3.1) | +1.5 (3.5) |
| H6 | +2.8 (6.6) | +2.9 (6.2) | +2.6 (5.6) | -0.7 (4.1) | +0.5 (3.5) |
| M6 | -0.3 (4.3) | -0.5 (2.9) | -0.6 (2.7) | +0.0 (1.9) | +1.0 (2.0) |
| A6 | +0.8 (1.9) | +0.9 (1.5) | +0.9 (1.3) | +0.4 (0.7) | +0.4 (0.8) |
| sum | +20.2 (21.8) | +18.9 (17.1)* | +16.5 (16.9) | +3.9 (13.1) | +11.5 (13.4) |

Per-book at the 12R combined lock (C2: locked ON set book vs the unlocked as-is book), parity, slip +0.25:

**ON set, K6 split 12R**

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K6 | -1.7 (4.8) | -2.6 (3.5) | -1.2 (3.6) | -2.0 (2.5) | -0.1 (2.3) |
| P6 | -1.5 (15.6) | -1.7 (9.0) | -1.7 (8.3) | -2.0 (6.5) | +0.3 (6.4) |
| U6 | +1.7 (5.1) | +1.1 (3.4) | +0.5 (3.3) | -1.6 (2.6) | -0.9 (1.6) |
| H6 | -1.5 (7.3) | -1.5 (4.2) | -0.8 (3.8) | -1.8 (2.9) | +0.1 (2.6) |
| M6 | -0.2 (2.6) | -0.8 (2.2) | -0.1 (2.3) | -1.1 (1.5) | -0.7 (1.5) |
| A6 | -0.3 (1.3) | -0.1 (0.7) | -0.0 (0.6) | -0.4 (0.6) | -0.1 (0.4) |
| sum | -3.5 (27.0) | -5.4 (15.8) | -3.2 (14.7) | -8.9 (10.8) | -1.4 (8.7) |

**ON set, K6 market 12R**

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K6 | -1.1 (4.2) | -1.5 (2.5) | -0.4 (2.8) | -1.7 (2.2) | -0.4 (1.8) |
| P6 | -1.7 (15.5) | -1.8 (9.0) | -1.8 (8.2) | -1.9 (6.6) | +0.3 (6.4) |
| U6 | +1.6 (5.1) | +1.1 (3.4) | +0.5 (3.2) | -1.7 (2.6) | -0.6 (1.5) |
| H6 | -1.8 (7.4) | -1.6 (4.2) | -0.9 (3.9) | -1.7 (2.8) | -0.1 (2.6) |
| M6 | -0.2 (2.3) | -0.8 (2.2) | -0.2 (2.2) | -1.1 (1.5) | -0.6 (1.5) |
| A6 | -0.3 (1.3) | -0.1 (0.7) | -0.0 (0.7) | -0.4 (0.6) | -0.1 (0.4) |
| sum | -3.4 (26.7) | -4.7 (15.5) | -2.8 (14.4) | -8.5 (10.7) | -1.6 (8.6) |

**ON + ER sizer P6+K6, K6 split 12R**

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K6 | +3.5 (9.4) | -0.4 (6.1) | +0.3 (5.5) | -1.8 (3.1) | +0.3 (3.0) |
| P6 | -1.3 (17.9) | +0.9 (11.1) | +1.9 (10.2) | +0.5 (9.3) | +1.4 (11.5) |
| U6 | +1.9 (5.9) | +1.7 (3.8) | +1.4 (3.5) | -1.4 (2.5) | -0.4 (2.1) |
| H6 | -2.4 (5.8) | -0.9 (3.6) | -0.3 (3.4) | -1.9 (3.1) | +0.5 (3.3) |
| M6 | +1.6 (3.0) | +0.0 (2.3) | +0.5 (2.3) | -1.2 (1.8) | +0.1 (1.6) |
| A6 | +0.2 (1.4) | +0.3 (0.8) | +0.4 (0.8) | -0.4 (0.6) | -0.1 (0.6) |
| sum | +3.6 (23.1) | +1.7 (14.8) | +4.3 (14.1) | -6.2 (12.4) | +1.8 (12.7) |

## Table 7 - step between sets (paired, same stop and lock): what each added block is worth

| row | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| ER sizer on P6+K6 added to ON (K6 split, no combined lock) | +8.4 (21.0) | +9.6 (12.1) | +8.5 (11.5) | +0.5 (9.0) | +0.7 (12.4) |
| remaining pieces (PE 45-s, zone skip, Asia cut, ER sizer on U6 H6 M6 A6) added to ON+ER (K6 split, no combined lock) | +13.3 (16.9) | +9.3 (12.1) | +7.5 (12.5) | +3.6 (11.5) | +7.3 (11.4) |
| six-piece minus ON (K6 split, no combined lock) | +21.7 (22.6) | +18.9 (17.4)* | +16.0 (17.1) | +4.1 (12.9) | +8.0 (12.7) |
| ER sizer on P6+K6 added to ON (K6 market, no combined lock) | +6.4 (18.9) | +8.6 (11.3) | +8.1 (10.9) | -0.1 (9.1) | +1.1 (12.5) |
| remaining pieces (PE 45-s, zone skip, Asia cut, ER sizer on U6 H6 M6 A6) added to ON+ER (K6 market, no combined lock) | +12.0 (17.6) | +8.5 (12.5) | +6.9 (12.8) | +3.1 (11.5) | +7.3 (11.4) |
| six-piece minus ON (K6 market, no combined lock) | +18.3 (21.1) | +17.1 (17.3) | +14.9 (17.0) | +3.1 (12.8) | +8.3 (12.4) |
| K6 market minus K6 split, ON set (no combined lock) | +1.4 (3.2) | +1.2 (2.9) | +0.9 (2.6) | +0.5 (1.3) | -0.2 (1.4) |
| K6 market minus K6 split, ON + ER (no combined lock) | -0.7 (3.4) | +0.3 (2.8) | +0.4 (2.5) | -0.1 (1.1) | +0.2 (1.0) |
| ER sizer on P6+K6 added to ON (K6 split, 12R) | +7.1 (27.4) | +7.1 (15.6) | +7.5 (13.8) | +2.7 (9.2) | +3.2 (10.7) |
| remaining pieces (PE 45-s, zone skip, Asia cut, ER sizer on U6 H6 M6 A6) added to ON+ER (K6 split, 12R) | +13.3 (19.5) | +8.9 (23.3) | +5.3 (24.8) | +2.7 (10.6) | +2.7 (10.6) |
| six-piece minus ON (K6 split, 12R) | +20.4 (21.6) | +16.0 (25.6) | +12.8 (25.9) | +5.4 (12.2) | +5.9 (13.1) |
| ER sizer on P6+K6 added to ON (K6 market, 12R) | +8.4 (24.8) | +7.9 (14.6) | +8.5 (13.1) | +1.0 (9.5) | +1.0 (10.7) |
| remaining pieces (PE 45-s, zone skip, Asia cut, ER sizer on U6 H6 M6 A6) added to ON+ER (K6 market, 12R) | +10.5 (16.2) | +7.1 (23.5) | +3.8 (24.8) | +3.2 (11.0) | +5.6 (11.7) |
| six-piece minus ON (K6 market, 12R) | +18.9 (21.4) | +15.1 (26.7) | +12.3 (26.6) | +4.2 (12.2) | +6.6 (13.2) |
| K6 market minus K6 split, ON set (12R) | +0.1 (2.2) | +0.7 (2.5) | +0.4 (2.3) | +0.4 (1.0) | -0.1 (0.9) |
| K6 market minus K6 split, ON + ER (12R) | +1.4 (5.0) | +1.5 (3.1) | +1.5 (2.8) | -1.3 (2.0) | -2.3 (5.1) |

## Table 8 - combined-lock fires (weeks fired / weeks in window; slip +0.25, parity, m0 1.0)

| lock | row | L3M | L6M | HOLD | PRE | X' | all 149 |
|---|---|---|---|---|---|---|---|
| 12R | as-is | 7/14 | 12/28 | 15/32 | 34/75 | 23/44 | 72 |
| 12R | ON set, K6 split | 5/14 | 9/28 | 12/32 | 32/75 | 21/44 | 65 |
| 12R | ON set, K6 market | 5/14 | 9/28 | 12/32 | 32/75 | 21/44 | 65 |
| 12R | ON + ER sizer P6+K6, K6 split | 7/14 | 12/28 | 15/32 | 43/75 | 29/44 | 87 |
| 12R | ON + ER sizer P6+K6, K6 market | 7/14 | 12/28 | 15/32 | 44/75 | 31/44 | 90 |
| 12R | six-piece composite, K6 split | 4/14 | 8/28 | 10/32 | 38/75 | 23/44 | 71 |
| 12R | six-piece composite, K6 market | 4/14 | 8/28 | 10/32 | 39/75 | 23/44 | 72 |
| 20R | as-is | 1/14 | 3/28 | 5/32 | 19/75 | 11/44 | 35 |
| 20R | ON set, K6 split | 2/14 | 4/28 | 6/32 | 18/75 | 9/44 | 33 |
| 20R | ON set, K6 market | 2/14 | 4/28 | 6/32 | 17/75 | 9/44 | 32 |
| 20R | ON + ER sizer P6+K6, K6 split | 5/14 | 8/28 | 11/32 | 32/75 | 21/44 | 64 |
| 20R | ON + ER sizer P6+K6, K6 market | 5/14 | 8/28 | 11/32 | 33/75 | 21/44 | 65 |
| 20R | six-piece composite, K6 split | 3/14 | 5/28 | 7/32 | 28/75 | 13/44 | 48 |
| 20R | six-piece composite, K6 market | 3/14 | 5/28 | 7/32 | 28/75 | 13/44 | 48 |
| 30R | as-is | 1/14 | 1/28 | 2/32 | 9/75 | 1/44 | 12 |
| 30R | ON set, K6 split | 0/14 | 0/28 | 1/32 | 5/75 | 0/44 | 6 |
| 30R | ON set, K6 market | 0/14 | 0/28 | 1/32 | 6/75 | 1/44 | 8 |
| 30R | ON + ER sizer P6+K6, K6 split | 2/14 | 3/28 | 5/32 | 24/75 | 13/44 | 42 |
| 30R | ON + ER sizer P6+K6, K6 market | 3/14 | 4/28 | 6/32 | 25/75 | 13/44 | 44 |
| 30R | six-piece composite, K6 split | 1/14 | 2/28 | 3/32 | 21/75 | 8/44 | 32 |
| 30R | six-piece composite, K6 market | 1/14 | 2/28 | 3/32 | 21/75 | 8/44 | 32 |

## Where / caveats
Conventions as in DS3_ONE_CONVENTION (A6 = PB7 Asia 1 lot, live lots, running max over taken signals, session planned-lot BookR, integer half-up min-1, in-engine parity stop odd Native 1.28 / even join 2.45, slip +0.25 / +0.45, combined lock F x R_K6 with R_K6 = 2 lots x K6 SizeMult x 60 x 20, m0 1.0 / 0.5). Per-book locks = D6 BASE (entry test +5R/-2R, day arm 2R/50%, book week floor 12R). ON set has no ER sizer so SizeMult is 1 and the locks sit at planned-lot R; ON + ER applies the sizer only to P6 and K6 (A6, U6, H6, M6 unsized). A6 is market in every set and is identical to the as-is except for the stop parity (book delta 0.0). Unknowns still open: combined-lock multiple F, m0, lock basis (MTM), O6 missing, NY-PM skip and D7 filters excluded. The Native contribution rows are an engine unit effect, not an independent estimate. Everything is post-hoc.
