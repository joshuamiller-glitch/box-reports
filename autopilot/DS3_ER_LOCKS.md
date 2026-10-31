# DS3_ER_LOCKS - the ER sizer on P6+K6 at persistence-shrunk multipliers under the combined week lock (LK-1, 2026-10-31). POST-HOC pricing of pre-stated variants, nothing here is a PASS

Capped 20260206, UNTOUCHED never read. Units $k per week, delta vs the as-is stack under the same convention, MDE (2.8 x SE of the paired weekly delta) in brackets, `*` = beyond MDE. Windows L3M 14 wk / L6M 28 / HOLD 32 / PRE 75 / X' 44. Prereg `l2vast/ds3/prereg/LK1_ER_LOCKS_prereg.md` sha256 7aa417731fae93aaa1bca7ceddaf9d874f9dd3568415bef5740c7273403721f6 (logged in DECISIONS.md before scoring; dead_lookup NOT FOUND x3 before; cells appended after). Code `l2vast/ds3/code/erlocks/` (run_erlocks.py, tab_erlocks.py; imports oneconv/oc_lib.py unchanged; feed switch is a wrapper in the runner), results `l2vast/ds3/out/erlocks/` (res_0..2.pkl, tables.md, log_*.txt). 140 scenarios, no selection. As-is = oc_res.pkl rows (arm ON) and 4 new arm-OFF reruns.

## Page 1 - ER sizer on P6+K6 at persistence-shrunk multipliers under the combined week lock (one table)

Delta vs the as-is stack on the same convention, $k/wk, MDE (2.8 x SE of paired weekly delta) in brackets, `*` = beyond MDE. Shrunk multiplier m' = 1 + f(m-1) on P6 and K6 (f = 0.03 headline = DS3_PERSISTENCE_SUNDAY ER ledger size; 0.36 = its best-case stratum; 1.0 = unshrunk = the ON-1 row). Day arm ON (D6), slip +0.25, parity stop, K6 70/30, m0 1.0. POST-HOC pricing of pre-stated variants, no PASS.

| convention | variant | L3M | L6M | HOLD | PRE | X' | L6M level |
|---|---|---|---|---|---|---|---|
| C1 no combined lock | ON set (no ER; f=0) | +0.6 (17.0) | +0.5 (9.8) | +0.7 (8.8) | +0.4 (4.1) | +3.3 (4.6) | 22.2 |
| C1 no combined lock | ER P6+K6 f=0.03, feeds running max, int lots | -0.2 (14.7) | +0.1 (8.9) | +0.3 (7.9) | +1.0 (4.0) | +3.2 (4.5) | 21.8 |
| C1 no combined lock | ER P6+K6 f=0.03, feeds running max, fractional lots | -0.3 (16.1) | -0.2 (9.7) | +0.0 (8.8) | +1.2 (3.8) | +3.5 (4.8) | 21.5 |
| C1 no combined lock | ER P6+K6 f=0.03, locks at planned R, int lots | +0.6 (17.0) | +0.5 (9.8) | +0.7 (8.8) | +0.4 (4.1) | +3.3 (4.6) | 22.2 |
| C1 no combined lock | ER P6+K6 f=0.03, locks at planned R, fractional lots | +4.2 (13.3) | +2.1 (8.5) | +1.8 (7.7) | +0.4 (4.3) | +3.2 (4.8) | 23.8 |
| C1 no combined lock | ER P6+K6 f=0.36, feeds running max, int lots | -2.2 (10.2) | +0.9 (7.7) | +0.6 (7.3) | +0.8 (6.5) | +4.5 (7.2) | 22.6 |
| C1 no combined lock | ER P6+K6 f=0.36, locks at planned R, int lots | -2.9 (16.5) | +1.1 (11.1) | +1.3 (9.8) | -0.7 (6.0) | +4.9 (7.1) | 22.9 |
| C1 no combined lock | ER P6+K6 f=1.0, feeds running max, int lots | +8.9 (14.0) | +10.1 (9.6)* | +9.2 (9.5) | +0.9 (9.3) | +4.1 (14.0) | 31.8 |
| C1 no combined lock | ER P6+K6 f=1.0, locks at planned R, int lots | +8.3 (18.6) | +7.6 (12.9) | +6.9 (11.8) | -2.6 (9.5) | +5.8 (12.5) | 29.4 |
| C2 12R | ON set (no ER; f=0) | -3.5 (27.0) | -5.4 (15.8) | -3.2 (14.7) | -8.9 (10.8) | -1.4 (8.7) | 16.3 |
| C2 12R | ER P6+K6 f=0.03, feeds running max, int lots | -4.3 (25.5) | -5.9 (15.2) | -3.3 (14.2) | -8.2 (10.7) | -1.6 (8.7) | 15.9 |
| C2 12R | ER P6+K6 f=0.03, feeds running max, fractional lots | -4.3 (25.7) | -5.7 (15.4) | -3.3 (14.4) | -8.3 (10.8) | -1.4 (8.8) | 16.0 |
| C2 12R | ER P6+K6 f=0.03, locks at planned R, int lots | -3.5 (27.0) | -5.4 (15.8) | -3.2 (14.7) | -8.9 (10.8) | -1.4 (8.7) | 16.3 |
| C2 12R | ER P6+K6 f=0.03, locks at planned R, fractional lots | -3.0 (27.1) | -5.4 (15.9) | -3.2 (14.7) | -7.3 (10.0) | -1.4 (8.8) | 16.3 |
| C2 12R | ER P6+K6 f=0.36, feeds running max, int lots | -9.1 (24.8) | -7.6 (16.1) | -4.5 (15.2) | -4.4 (10.8) | +1.0 (8.8) | 14.2 |
| C2 12R | ER P6+K6 f=0.36, locks at planned R, int lots | -6.8 (27.3) | -4.5 (17.1) | -2.2 (15.7) | -9.3 (11.6) | +0.9 (9.6) | 17.2 |
| C2 12R | ER P6+K6 f=1.0, feeds running max, int lots | +3.6 (23.1) | +1.7 (14.8) | +4.3 (14.1) | -6.2 (12.4) | +1.8 (12.7) | 23.4 |
| C2 12R | ER P6+K6 f=1.0, locks at planned R, int lots | -12.2 (30.5) | -10.1 (20.4) | -6.9 (18.6) | -11.8 (13.2) | +3.6 (12.2) | 11.7 |
| C2 20R | ON set (no ER; f=0) | +3.0 (17.1) | -1.7 (13.3) | -1.0 (12.1) | -4.6 (7.9) | -0.7 (6.4) | 20.0 |
| C2 20R | ER P6+K6 f=0.03, feeds running max, int lots | +2.4 (14.9) | +0.3 (10.0) | +1.1 (9.2) | -4.1 (7.9) | -0.9 (6.3) | 22.1 |
| C2 20R | ER P6+K6 f=0.03, feeds running max, fractional lots | +2.3 (15.3) | +0.1 (10.4) | +0.6 (9.6) | -4.2 (7.9) | -0.5 (6.6) | 21.8 |
| C2 20R | ER P6+K6 f=0.03, locks at planned R, int lots | +3.0 (17.1) | -1.7 (13.3) | -1.0 (12.1) | -4.6 (7.9) | -0.7 (6.4) | 20.0 |
| C2 20R | ER P6+K6 f=0.03, locks at planned R, fractional lots | +4.1 (17.2) | -1.5 (13.4) | -0.7 (12.2) | -4.5 (8.1) | -0.9 (6.6) | 20.2 |
| C2 20R | ER P6+K6 f=0.36, feeds running max, int lots | -0.2 (13.9) | +0.4 (9.8) | +1.4 (9.6) | -5.6 (9.7) | +1.7 (7.2) | 22.1 |
| C2 20R | ER P6+K6 f=0.36, locks at planned R, int lots | -2.7 (19.5) | +0.3 (12.9) | +1.0 (11.7) | -5.8 (9.2) | +0.0 (8.4) | 22.0 |
| C2 20R | ER P6+K6 f=1.0, feeds running max, int lots | +4.4 (27.0) | +3.6 (16.2) | +4.9 (15.1) | -4.5 (11.8) | +3.1 (12.1) | 25.3 |
| C2 20R | ER P6+K6 f=1.0, locks at planned R, int lots | -0.3 (27.7) | +2.4 (17.2) | +3.1 (15.3) | -5.2 (10.1) | +4.5 (12.7) | 24.1 |
| C2 30R | ON set (no ER; f=0) | +0.6 (17.0) | +0.5 (9.8) | +0.7 (8.8) | -0.2 (4.6) | +3.3 (4.6) | 22.2 |
| C2 30R | ER P6+K6 f=0.03, feeds running max, int lots | -0.2 (14.7) | +0.1 (8.9) | +0.3 (7.9) | +0.4 (4.5) | +3.2 (4.5) | 21.8 |
| C2 30R | ER P6+K6 f=0.03, feeds running max, fractional lots | -0.9 (17.6) | -0.5 (10.3) | -0.2 (9.3) | +0.6 (4.4) | +3.5 (4.8) | 21.2 |
| C2 30R | ER P6+K6 f=0.03, locks at planned R, int lots | +0.6 (17.0) | +0.5 (9.8) | +0.7 (8.8) | -0.2 (4.6) | +3.3 (4.6) | 22.2 |
| C2 30R | ER P6+K6 f=0.03, locks at planned R, fractional lots | +4.2 (13.3) | +2.1 (8.5) | +1.8 (7.7) | -0.2 (4.8) | +3.2 (4.8) | 23.8 |
| C2 30R | ER P6+K6 f=0.36, feeds running max, int lots | -2.2 (10.2) | +0.9 (7.7) | +0.7 (7.3) | -3.4 (9.1) | +2.3 (7.9) | 22.6 |
| C2 30R | ER P6+K6 f=0.36, locks at planned R, int lots | -2.9 (16.5) | +1.1 (11.1) | +1.3 (9.8) | -0.5 (6.0) | +4.9 (7.1) | 22.9 |
| C2 30R | ER P6+K6 f=1.0, feeds running max, int lots | +11.2 (16.6) | +9.5 (11.5) | +10.5 (11.0) | -4.5 (12.3) | +4.6 (13.7) | 31.3 |
| C2 30R | ER P6+K6 f=1.0, locks at planned R, int lots | +5.6 (23.2) | +6.3 (14.6) | +5.5 (13.4) | -3.9 (10.5) | +3.7 (13.1) | 28.0 |
| C3 12R | ON set (no ER; f=0) | +4.7 (13.0) | +5.9 (9.7) | +4.9 (8.7) | -0.0 (3.1) | +2.4 (5.2) | 16.3 |
| C3 12R | ER P6+K6 f=0.03, feeds running max, int lots | +4.0 (9.2) | +5.5 (8.6) | +4.9 (7.6) | +0.7 (2.8) | +2.2 (5.1) | 15.9 |
| C3 12R | ER P6+K6 f=0.03, feeds running max, fractional lots | +3.9 (9.8) | +5.7 (8.9) | +4.8 (8.0) | +0.6 (2.9) | +2.4 (5.4) | 16.0 |
| C3 12R | ER P6+K6 f=0.03, locks at planned R, int lots | +4.7 (13.0) | +5.9 (9.7) | +4.9 (8.7) | -0.0 (3.1) | +2.4 (5.2) | 16.3 |
| C3 12R | ER P6+K6 f=0.03, locks at planned R, fractional lots | +5.3 (13.1) | +5.9 (9.9) | +5.0 (8.9) | +1.6 (5.8) | +2.4 (5.4) | 16.3 |
| C3 12R | ER P6+K6 f=0.36, feeds running max, int lots | -0.8 (7.5) | +3.8 (6.7) | +3.7 (6.1) | +4.5 (8.9) | +4.8 (8.4) | 14.2 |
| C3 12R | ER P6+K6 f=0.36, locks at planned R, int lots | +1.4 (14.2) | +6.9 (11.2) | +6.0 (10.0) | -0.4 (5.8) | +4.7 (8.6) | 17.2 |
| C3 12R | ER P6+K6 f=1.0, feeds running max, int lots | +11.8 (22.9) | +13.0 (12.8)* | +12.4 (11.5)* | +2.7 (9.1) | +5.6 (12.0) | 23.4 |
| C3 12R | ER P6+K6 f=1.0, locks at planned R, int lots | -4.0 (21.2) | +1.3 (14.5) | +1.3 (12.6) | -2.8 (10.3) | +7.4 (11.9) | 11.7 |

**Plain sentence.** Priced on the DS3_ONE_CONVENTION engine (A6 = PB7, live lots, running max over taken signals, parity stop, K6 70/30, slip +0.25, m0 1.0), the ER sizer on P6+K6 at the persistence-shrunk multiplier is worth about nothing under every lock setting: with f = 0.03 (the DS3_PERSISTENCE_SUNDAY ledger size for the ER sizer = the 2-3 t-stat sizing-family factor +0.07 over its in-sample keep; the study is DS3_PERSISTENCE.md) the row equals the ON set within 1 (L6M C1 +0.1 vs +0.5; C2 12R -5.9 vs -5.4; C3 12R +5.5 vs +5.9, MDE 9-15) because integer half-up lots do not move (1.5 -> 1.015); the unshrunk sizer (f = 1.0, the ON-1 row) is the only one that adds anything (C1 +10.1 (9.6)*, C3 12R +13.0 (12.8)*), and its C2 value depends on the lock: +1.7 / +3.6 / +9.5 at 12R / 20R / 30R, PRE negative (-4.5 to -6.2) in all three. (b) If the ER multiplier does NOT feed the running max (locks at planned-lot R) the unshrunk sizer is worse under a combined lock (C2 12R -10.1 (20.4) vs +1.7 feeding; paired -11.7 (21.1) L6M) because lots are up to 1.5x against a lock sized at 1.0x; with no lock the two differ by -2.4 (12.0); at f = 0.03 / 0.36 the feed choice is inside noise. (c) Fractional vs integer lots: -2.9 (5.5) L6M at f = 1.0 no lock, -3.6 (11.1) at 12R, inside MDE; at f = 0.03 the fractional rows are dominated by threshold flips (one day, 20260206, supplies +31.9k of the +43.6k L6M difference between the planned-R fractional row and the ON set, so the +1.6 (3.5) there is the engine's noise floor for a 1.5% lot change, not an ER effect). (d) Day arm off vs on: the pure arm effect (off minus on, no lock) is +3.7 (8.5) L6M on the ON set and -0.4 (10.1) at f = 1.0, inside MDE everywhere; the pure 12R combined-lock effect is -5.9 (arm on) / -7.4 (arm off) on the ON set and -8.4 / -9.7 at f = 1.0 (as-is -11.4 / -9.0), so removing the day arm does not absorb the lock cost: the two are separable and the lock costs 6-10k L6M with or without the arm. (e) Risk: f = 0.03 has the ON-set risk line (L6M maxDD 73, worst week -71 unlocked; 12R 59 / -29); f = 1.0 feeding is 75 / -75 unlocked with PRE worst-20 -1009 (as-is -811) and 53 / -44 at 12R (PRE worst-20 -577 vs as-is-locked -585); per book at f = 1.0 P6 carries +6.5 of the +10.1 L6M (K6 +1.7), at f = 0.03 P6 is -1.5 and K6 -0.6. No significance claim on any risk line. ALL POST-HOC pricing of pre-stated variants; no PASS, no tier.

**Caveats.** (1) The shrink factor is applied as m' = 1 + f(m-1) with the governors seeing the unrounded m' (the PS-1 mapping); f = 0.03 is the ledger size, 0.07 the study factor as size, 0.36 the best-case stratum PS-1 flagged as not supported by the sizer's own t (2.5); f = 0 is the ON set. (2) "ER P6+K6 f=0.03, locks at planned R, int lots" is identical to the ON set (0.0 daily difference): the integer rounding removes the sizer, so (a) at the honest size is a statement about the governors only. (3) The day-arm-off as-is is rerun (join 2.45, planned-lot R); C2/C3 rows in Table 3 use the same-arm as-is. (4) Tie-outs: the f = 1.0 / feeding / integer / arm-on rows and the ON rows reproduce the ON-1 runner (onset res_*.pkl) with a max daily difference of 0.0.


## Table 2 - full grid (a)(b)(c): shrink factor x feed x lots, all lock settings, day arm ON

| convention / variant | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| C1 no combined lock: ER P6+K6 f=0.03, feeds running max, int lots | -0.2 (14.7) | +0.1 (8.9) | +0.3 (7.9) | +1.0 (4.0) | +3.2 (4.5) |
| C1 no combined lock: ER P6+K6 f=0.03, feeds running max, fractional lots | -0.3 (16.1) | -0.2 (9.7) | +0.0 (8.8) | +1.2 (3.8) | +3.5 (4.8) |
| C1 no combined lock: ER P6+K6 f=0.03, locks at planned R, int lots | +0.6 (17.0) | +0.5 (9.8) | +0.7 (8.8) | +0.4 (4.1) | +3.3 (4.6) |
| C1 no combined lock: ER P6+K6 f=0.03, locks at planned R, fractional lots | +4.2 (13.3) | +2.1 (8.5) | +1.8 (7.7) | +0.4 (4.3) | +3.2 (4.8) |
| C1 no combined lock: ER P6+K6 f=0.07, feeds running max, int lots | -2.3 (16.3) | -0.4 (9.6) | -0.1 (8.8) | +2.0 (4.3) | +5.7 (5.9) |
| C1 no combined lock: ER P6+K6 f=0.07, feeds running max, fractional lots | -3.5 (16.5) | -0.5 (9.7) | -0.3 (8.8) | +0.5 (4.6) | +4.9 (6.2) |
| C1 no combined lock: ER P6+K6 f=0.07, locks at planned R, int lots | +0.6 (17.0) | +0.5 (9.8) | +0.7 (8.8) | +0.4 (4.1) | +3.3 (4.6) |
| C1 no combined lock: ER P6+K6 f=0.07, locks at planned R, fractional lots | +2.6 (11.7) | +2.0 (8.8) | +2.0 (8.0) | +0.1 (5.1) | +5.4 (5.6) |
| C1 no combined lock: ER P6+K6 f=0.36, feeds running max, int lots | -2.2 (10.2) | +0.9 (7.7) | +0.6 (7.3) | +0.8 (6.5) | +4.5 (7.2) |
| C1 no combined lock: ER P6+K6 f=0.36, feeds running max, fractional lots | +2.3 (9.3) | +3.3 (6.6) | +2.8 (6.2) | +1.0 (6.4) | +4.2 (7.6) |
| C1 no combined lock: ER P6+K6 f=0.36, locks at planned R, int lots | -2.9 (16.5) | +1.1 (11.1) | +1.3 (9.8) | -0.7 (6.0) | +4.9 (7.1) |
| C1 no combined lock: ER P6+K6 f=0.36, locks at planned R, fractional lots | -0.8 (17.9) | +1.7 (11.5) | +1.6 (10.2) | -0.4 (6.1) | +5.3 (7.5) |
| C1 no combined lock: ER P6+K6 f=1.0, feeds running max, int lots | +8.9 (14.0) | +10.1 (9.6)* | +9.2 (9.5) | +0.9 (9.3) | +4.1 (14.0) |
| C1 no combined lock: ER P6+K6 f=1.0, feeds running max, fractional lots | +6.7 (14.0) | +7.2 (10.1) | +6.5 (9.7) | +0.7 (9.8) | +3.2 (12.2) |
| C1 no combined lock: ER P6+K6 f=1.0, locks at planned R, int lots | +8.3 (18.6) | +7.6 (12.9) | +6.9 (11.8) | -2.6 (9.5) | +5.8 (12.5) |
| C1 no combined lock: ER P6+K6 f=1.0, locks at planned R, fractional lots | +8.2 (18.0) | +5.3 (13.1) | +4.7 (11.9) | -1.9 (9.1) | +4.7 (12.2) |
| C2 12R: ER P6+K6 f=0.03, feeds running max, int lots | -4.3 (25.5) | -5.9 (15.2) | -3.3 (14.2) | -8.2 (10.7) | -1.6 (8.7) |
| C2 12R: ER P6+K6 f=0.03, feeds running max, fractional lots | -4.3 (25.7) | -5.7 (15.4) | -3.3 (14.4) | -8.3 (10.8) | -1.4 (8.8) |
| C2 12R: ER P6+K6 f=0.03, locks at planned R, int lots | -3.5 (27.0) | -5.4 (15.8) | -3.2 (14.7) | -8.9 (10.8) | -1.4 (8.7) |
| C2 12R: ER P6+K6 f=0.03, locks at planned R, fractional lots | -3.0 (27.1) | -5.4 (15.9) | -3.2 (14.7) | -7.3 (10.0) | -1.4 (8.8) |
| C2 12R: ER P6+K6 f=0.07, feeds running max, int lots | -7.3 (24.5) | -9.4 (15.8) | -6.5 (14.8) | -7.5 (10.7) | +1.0 (9.0) |
| C2 12R: ER P6+K6 f=0.07, feeds running max, fractional lots | -10.0 (23.9) | -8.2 (14.6) | -5.5 (13.9) | -8.0 (10.9) | -1.4 (9.4) |
| C2 12R: ER P6+K6 f=0.07, locks at planned R, int lots | -3.5 (27.0) | -5.4 (15.8) | -3.2 (14.7) | -8.9 (10.8) | -1.4 (8.7) |
| C2 12R: ER P6+K6 f=0.07, locks at planned R, fractional lots | -3.9 (25.7) | -4.8 (15.9) | -2.6 (14.7) | -8.2 (11.0) | +1.3 (9.2) |
| C2 12R: ER P6+K6 f=0.36, feeds running max, int lots | -9.1 (24.8) | -7.6 (16.1) | -4.5 (15.2) | -4.4 (10.8) | +1.0 (8.8) |
| C2 12R: ER P6+K6 f=0.36, feeds running max, fractional lots | -7.7 (25.2) | -4.5 (14.7) | -2.0 (13.9) | -4.7 (10.6) | +1.2 (9.6) |
| C2 12R: ER P6+K6 f=0.36, locks at planned R, int lots | -6.8 (27.3) | -4.5 (17.1) | -2.2 (15.7) | -9.3 (11.6) | +0.9 (9.6) |
| C2 12R: ER P6+K6 f=0.36, locks at planned R, fractional lots | -4.2 (27.4) | -5.4 (17.6) | -2.9 (16.2) | -9.7 (11.6) | +1.6 (9.8) |
| C2 12R: ER P6+K6 f=1.0, feeds running max, int lots | +3.6 (23.1) | +1.7 (14.8) | +4.3 (14.1) | -6.2 (12.4) | +1.8 (12.7) |
| C2 12R: ER P6+K6 f=1.0, feeds running max, fractional lots | +1.2 (27.8) | -2.0 (16.7) | +0.8 (15.8) | -6.5 (12.9) | +0.4 (12.1) |
| C2 12R: ER P6+K6 f=1.0, locks at planned R, int lots | -12.2 (30.5) | -10.1 (20.4) | -6.9 (18.6) | -11.8 (13.2) | +3.6 (12.2) |
| C2 12R: ER P6+K6 f=1.0, locks at planned R, fractional lots | -4.7 (27.4) | -5.8 (18.5) | -3.4 (16.8) | -10.3 (12.6) | +3.1 (12.1) |
| C2 20R: ER P6+K6 f=0.03, feeds running max, int lots | +2.4 (14.9) | +0.3 (10.0) | +1.1 (9.2) | -4.1 (7.9) | -0.9 (6.3) |
| C2 20R: ER P6+K6 f=0.03, feeds running max, fractional lots | +2.3 (15.3) | +0.1 (10.4) | +0.6 (9.6) | -4.2 (7.9) | -0.5 (6.6) |
| C2 20R: ER P6+K6 f=0.03, locks at planned R, int lots | +3.0 (17.1) | -1.7 (13.3) | -1.0 (12.1) | -4.6 (7.9) | -0.7 (6.4) |
| C2 20R: ER P6+K6 f=0.03, locks at planned R, fractional lots | +4.1 (17.2) | -1.5 (13.4) | -0.7 (12.2) | -4.5 (8.1) | -0.9 (6.6) |
| C2 20R: ER P6+K6 f=0.07, feeds running max, int lots | +1.4 (15.3) | -0.6 (10.4) | +0.3 (9.7) | -4.2 (8.3) | +1.7 (7.9) |
| C2 20R: ER P6+K6 f=0.07, feeds running max, fractional lots | +0.1 (15.9) | -0.7 (10.6) | +0.2 (9.8) | -5.6 (8.6) | -2.3 (9.2) |
| C2 20R: ER P6+K6 f=0.07, locks at planned R, int lots | +3.0 (17.1) | -1.7 (13.3) | -1.0 (12.1) | -4.6 (7.9) | -0.7 (6.4) |
| C2 20R: ER P6+K6 f=0.07, locks at planned R, fractional lots | +3.0 (15.2) | +1.2 (10.9) | +1.6 (10.1) | -4.9 (8.5) | +1.5 (7.4) |
| C2 20R: ER P6+K6 f=0.36, feeds running max, int lots | -0.2 (13.9) | +0.4 (9.8) | +1.4 (9.6) | -5.6 (9.7) | +1.7 (7.2) |
| C2 20R: ER P6+K6 f=0.36, feeds running max, fractional lots | +4.8 (13.0) | +3.1 (9.0) | +3.9 (8.8) | -5.3 (9.3) | +1.1 (7.5) |
| C2 20R: ER P6+K6 f=0.36, locks at planned R, int lots | -2.7 (19.5) | +0.3 (12.9) | +1.0 (11.7) | -5.8 (9.2) | +0.0 (8.4) |
| C2 20R: ER P6+K6 f=0.36, locks at planned R, fractional lots | -3.9 (25.6) | -0.6 (15.2) | +0.3 (13.7) | -6.0 (9.2) | +0.6 (8.6) |
| C2 20R: ER P6+K6 f=1.0, feeds running max, int lots | +4.4 (27.0) | +3.6 (16.2) | +4.9 (15.1) | -4.5 (11.8) | +3.1 (12.1) |
| C2 20R: ER P6+K6 f=1.0, feeds running max, fractional lots | +2.0 (26.6) | -2.3 (17.3) | -0.5 (16.1) | -3.2 (11.7) | +2.1 (10.5) |
| C2 20R: ER P6+K6 f=1.0, locks at planned R, int lots | -0.3 (27.7) | +2.4 (17.2) | +3.1 (15.3) | -5.2 (10.1) | +4.5 (12.7) |
| C2 20R: ER P6+K6 f=1.0, locks at planned R, fractional lots | -0.5 (27.4) | -0.0 (17.1) | +0.8 (15.2) | -4.9 (9.8) | +3.1 (12.5) |
| C2 30R: ER P6+K6 f=0.03, feeds running max, int lots | -0.2 (14.7) | +0.1 (8.9) | +0.3 (7.9) | +0.4 (4.5) | +3.2 (4.5) |
| C2 30R: ER P6+K6 f=0.03, feeds running max, fractional lots | -0.9 (17.6) | -0.5 (10.3) | -0.2 (9.3) | +0.6 (4.4) | +3.5 (4.8) |
| C2 30R: ER P6+K6 f=0.03, locks at planned R, int lots | +0.6 (17.0) | +0.5 (9.8) | +0.7 (8.8) | -0.2 (4.6) | +3.3 (4.6) |
| C2 30R: ER P6+K6 f=0.03, locks at planned R, fractional lots | +4.2 (13.3) | +2.1 (8.5) | +1.8 (7.7) | -0.2 (4.8) | +3.2 (4.8) |
| C2 30R: ER P6+K6 f=0.07, feeds running max, int lots | -2.6 (17.5) | -0.6 (10.1) | -0.8 (9.5) | +0.1 (5.6) | +5.7 (6.0) |
| C2 30R: ER P6+K6 f=0.07, feeds running max, fractional lots | -3.9 (17.8) | -0.7 (10.3) | -0.5 (9.2) | -1.2 (5.8) | +4.9 (6.2) |
| C2 30R: ER P6+K6 f=0.07, locks at planned R, int lots | +0.6 (17.0) | +0.5 (9.8) | +0.7 (8.8) | -0.2 (4.6) | +3.3 (4.6) |
| C2 30R: ER P6+K6 f=0.07, locks at planned R, fractional lots | +2.6 (11.7) | +2.0 (8.8) | +2.0 (8.0) | -0.5 (5.5) | +5.4 (5.6) |
| C2 30R: ER P6+K6 f=0.36, feeds running max, int lots | -2.2 (10.2) | +0.9 (7.7) | +0.7 (7.3) | -3.4 (9.1) | +2.3 (7.9) |
| C2 30R: ER P6+K6 f=0.36, feeds running max, fractional lots | +3.4 (10.5) | +3.8 (7.0) | +3.0 (6.8) | -4.4 (9.7) | +1.2 (8.7) |
| C2 30R: ER P6+K6 f=0.36, locks at planned R, int lots | -2.9 (16.5) | +1.1 (11.1) | +1.3 (9.8) | -0.5 (6.0) | +4.9 (7.1) |
| C2 30R: ER P6+K6 f=0.36, locks at planned R, fractional lots | -0.8 (17.9) | +1.7 (11.5) | +1.6 (10.2) | -0.6 (6.4) | +4.4 (7.1) |
| C2 30R: ER P6+K6 f=1.0, feeds running max, int lots | +11.2 (16.6) | +9.5 (11.5) | +10.5 (11.0) | -4.5 (12.3) | +4.6 (13.7) |
| C2 30R: ER P6+K6 f=1.0, feeds running max, fractional lots | +9.1 (16.6) | +6.6 (12.2) | +7.7 (11.6) | -5.0 (12.6) | +3.5 (12.1) |
| C2 30R: ER P6+K6 f=1.0, locks at planned R, int lots | +5.6 (23.2) | +6.3 (14.6) | +5.5 (13.4) | -3.9 (10.5) | +3.7 (13.1) |
| C2 30R: ER P6+K6 f=1.0, locks at planned R, fractional lots | +8.2 (18.0) | +5.3 (13.1) | +4.5 (12.1) | -2.2 (9.9) | +2.9 (12.7) |
| C3 12R: ER P6+K6 f=0.03, feeds running max, int lots | +4.0 (9.2) | +5.5 (8.6) | +4.9 (7.6) | +0.7 (2.8) | +2.2 (5.1) |
| C3 12R: ER P6+K6 f=0.03, feeds running max, fractional lots | +3.9 (9.8) | +5.7 (8.9) | +4.8 (8.0) | +0.6 (2.9) | +2.4 (5.4) |
| C3 12R: ER P6+K6 f=0.03, locks at planned R, int lots | +4.7 (13.0) | +5.9 (9.7) | +4.9 (8.7) | -0.0 (3.1) | +2.4 (5.2) |
| C3 12R: ER P6+K6 f=0.03, locks at planned R, fractional lots | +5.3 (13.1) | +5.9 (9.9) | +5.0 (8.9) | +1.6 (5.8) | +2.4 (5.4) |
| C3 12R: ER P6+K6 f=0.07, feeds running max, int lots | +0.9 (7.2) | +1.9 (5.8) | +1.7 (5.2) | +1.4 (3.4) | +4.8 (5.2) |
| C3 12R: ER P6+K6 f=0.07, feeds running max, fractional lots | -1.8 (5.2) | +3.2 (8.2) | +2.7 (7.4) | +0.9 (3.2) | +2.4 (6.0) |
| C3 12R: ER P6+K6 f=0.07, locks at planned R, int lots | +4.7 (13.0) | +5.9 (9.7) | +4.9 (8.7) | -0.0 (3.1) | +2.4 (5.2) |
| C3 12R: ER P6+K6 f=0.07, locks at planned R, fractional lots | +4.4 (9.7) | +6.5 (9.5) | +5.6 (8.6) | +0.7 (3.6) | +5.1 (7.9) |
| C3 12R: ER P6+K6 f=0.36, feeds running max, int lots | -0.8 (7.5) | +3.8 (6.7) | +3.7 (6.1) | +4.5 (8.9) | +4.8 (8.4) |
| C3 12R: ER P6+K6 f=0.36, feeds running max, fractional lots | +0.5 (7.1) | +6.9 (8.1) | +6.2 (7.3) | +4.2 (8.7) | +5.0 (9.2) |
| C3 12R: ER P6+K6 f=0.36, locks at planned R, int lots | +1.4 (14.2) | +6.9 (11.2) | +6.0 (10.0) | -0.4 (5.8) | +4.7 (8.6) |
| C3 12R: ER P6+K6 f=0.36, locks at planned R, fractional lots | +4.0 (13.4) | +5.9 (12.4) | +5.2 (10.9) | -0.8 (5.9) | +5.4 (8.7) |
| C3 12R: ER P6+K6 f=1.0, feeds running max, int lots | +11.8 (22.9) | +13.0 (12.8)* | +12.4 (11.5)* | +2.7 (9.1) | +5.6 (12.0) |
| C3 12R: ER P6+K6 f=1.0, feeds running max, fractional lots | +9.5 (13.2) | +9.4 (10.1) | +9.0 (9.3) | +2.4 (10.3) | +4.2 (11.5) |
| C3 12R: ER P6+K6 f=1.0, locks at planned R, int lots | -4.0 (21.2) | +1.3 (14.5) | +1.3 (12.6) | -2.8 (10.3) | +7.4 (11.9) |
| C3 12R: ER P6+K6 f=1.0, locks at planned R, fractional lots | +3.5 (13.9) | +5.6 (10.4) | +4.8 (9.1) | -1.4 (9.3) | +6.9 (11.7) |
| C3 20R: ER P6+K6 f=0.03, feeds running max, int lots | -0.4 (12.4) | +3.3 (10.4) | +3.1 (9.1) | +0.9 (4.0) | +4.0 (5.6) |
| C3 20R: ER P6+K6 f=0.03, feeds running max, fractional lots | -0.5 (12.9) | +3.1 (9.9) | +2.7 (8.9) | +0.7 (4.0) | +4.3 (6.0) |
| C3 20R: ER P6+K6 f=0.03, locks at planned R, int lots | +0.2 (15.1) | +1.2 (8.8) | +1.1 (7.9) | +0.3 (4.1) | +4.1 (5.7) |
| C3 20R: ER P6+K6 f=0.03, locks at planned R, fractional lots | +1.2 (15.3) | +1.5 (9.0) | +1.3 (8.0) | +0.5 (4.4) | +3.9 (5.9) |
| C3 20R: ER P6+K6 f=0.07, feeds running max, int lots | -1.4 (12.7) | +2.3 (10.5) | +2.4 (9.3) | +0.7 (3.7) | +6.5 (6.4)* |
| C3 20R: ER P6+K6 f=0.07, feeds running max, fractional lots | -2.7 (13.3) | +2.3 (10.2) | +2.2 (9.1) | -0.7 (5.2) | +2.5 (8.9) |
| C3 20R: ER P6+K6 f=0.07, locks at planned R, int lots | +0.2 (15.1) | +1.2 (8.8) | +1.1 (7.9) | +0.3 (4.1) | +4.1 (5.7) |
| C3 20R: ER P6+K6 f=0.07, locks at planned R, fractional lots | +0.2 (13.0) | +4.1 (10.5) | +3.7 (9.4) | +0.1 (5.1) | +6.3 (7.4) |
| C3 20R: ER P6+K6 f=0.36, feeds running max, int lots | -3.0 (9.5) | +3.3 (9.7) | +3.5 (8.7) | -0.7 (6.4) | +6.5 (8.8) |
| C3 20R: ER P6+K6 f=0.36, feeds running max, fractional lots | +2.0 (9.1) | +6.1 (8.2) | +6.0 (7.4) | -0.4 (6.1) | +5.9 (9.2) |
| C3 20R: ER P6+K6 f=0.36, locks at planned R, int lots | -5.5 (17.2) | +3.3 (12.9) | +3.1 (11.3) | -0.9 (6.2) | +4.9 (8.5) |
| C3 20R: ER P6+K6 f=0.36, locks at planned R, fractional lots | -6.7 (23.9) | +2.3 (15.3) | +2.4 (13.5) | -1.0 (6.3) | +5.5 (8.7) |
| C3 20R: ER P6+K6 f=1.0, feeds running max, int lots | +1.6 (24.9) | +6.5 (14.2) | +7.0 (12.7) | +0.5 (10.4) | +7.9 (11.7) |
| C3 20R: ER P6+K6 f=1.0, feeds running max, fractional lots | -0.8 (24.1) | +0.6 (15.7) | +1.6 (14.0) | +1.7 (10.0) | +6.9 (10.2) |
| C3 20R: ER P6+K6 f=1.0, locks at planned R, int lots | -3.1 (26.0) | +5.3 (17.7) | +5.2 (15.5) | -0.2 (9.9) | +9.4 (13.9) |
| C3 20R: ER P6+K6 f=1.0, locks at planned R, fractional lots | -3.3 (25.3) | +2.9 (17.7) | +2.8 (15.5) | +0.1 (9.6) | +8.0 (13.8) |
| C3 30R: ER P6+K6 f=0.03, feeds running max, int lots | -1.3 (14.2) | -0.5 (8.8) | -0.4 (7.8) | +2.7 (6.7) | +3.2 (4.5) |
| C3 30R: ER P6+K6 f=0.03, feeds running max, fractional lots | -2.0 (17.0) | -1.1 (10.1) | -0.9 (9.1) | +3.0 (6.6) | +3.5 (4.9) |
| C3 30R: ER P6+K6 f=0.03, locks at planned R, int lots | -0.6 (16.7) | -0.0 (9.7) | +0.0 (8.6) | +2.1 (6.7) | +3.4 (4.6) |
| C3 30R: ER P6+K6 f=0.03, locks at planned R, fractional lots | +3.1 (12.9) | +1.5 (8.3) | +1.1 (7.5) | +2.2 (6.8) | +3.2 (4.8) |
| C3 30R: ER P6+K6 f=0.07, feeds running max, int lots | -3.7 (17.1) | -1.1 (10.0) | -1.4 (9.4) | +2.4 (6.2) | +5.7 (6.0) |
| C3 30R: ER P6+K6 f=0.07, feeds running max, fractional lots | -5.0 (17.4) | -1.2 (10.2) | -1.1 (9.1) | +1.2 (6.3) | +4.9 (6.3) |
| C3 30R: ER P6+K6 f=0.07, locks at planned R, int lots | -0.6 (16.7) | -0.0 (9.7) | +0.0 (8.6) | +2.1 (6.7) | +3.4 (4.6) |
| C3 30R: ER P6+K6 f=0.07, locks at planned R, fractional lots | +1.5 (11.0) | +1.4 (8.6) | +1.4 (7.8) | +1.9 (7.1) | +5.5 (5.7) |
| C3 30R: ER P6+K6 f=0.36, feeds running max, int lots | -3.3 (9.2) | +0.4 (7.5) | +0.0 (7.1) | -1.0 (9.8) | +2.3 (7.9) |
| C3 30R: ER P6+K6 f=0.36, feeds running max, fractional lots | +2.3 (9.3) | +3.3 (6.6) | +2.4 (6.5) | -2.0 (8.7) | +1.2 (8.7) |
| C3 30R: ER P6+K6 f=0.36, locks at planned R, int lots | -4.0 (15.9) | +0.6 (10.9) | +0.6 (9.7) | +1.9 (7.6) | +4.9 (7.2) |
| C3 30R: ER P6+K6 f=0.36, locks at planned R, fractional lots | -1.9 (17.2) | +1.1 (11.3) | +0.9 (10.0) | +1.8 (8.0) | +4.4 (7.1) |
| C3 30R: ER P6+K6 f=1.0, feeds running max, int lots | +10.1 (15.2) | +9.0 (11.0) | +9.9 (10.5) | -2.2 (11.8) | +4.6 (13.7) |
| C3 30R: ER P6+K6 f=1.0, feeds running max, fractional lots | +8.0 (15.1) | +6.1 (11.7) | +7.1 (11.1) | -2.7 (12.2) | +3.6 (12.1) |
| C3 30R: ER P6+K6 f=1.0, locks at planned R, int lots | +4.5 (22.2) | +5.7 (14.2) | +4.8 (13.0) | -1.5 (9.1) | +3.8 (13.1) |
| C3 30R: ER P6+K6 f=1.0, locks at planned R, fractional lots | +7.0 (16.7) | +4.8 (12.6) | +3.9 (11.7) | +0.2 (9.7) | +2.9 (12.7) |

## Table 3 - (d) day arm 2R/50% off vs on, so the lock contribution is separable

Rows = delta vs the as-is with the SAME arm setting (as-is arm-off rerun for the arm-off rows; C2 vs unlocked as-is, C3 vs same-lock as-is). 'pure lock effect' = locked set minus the same set unlocked, same arm (paired). 'pure arm effect' = arm-off minus arm-on, same set and lock (paired). The unlocked arm-off set has no day arm and no combined lock; the book week 12R floor is in every row.

| row | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| ON set (no ER; f=0), arm ON, C1 no combined lock vs as-is (arm ON) | +0.6 (17.0) | +0.5 (9.8) | +0.7 (8.8) | +0.4 (4.1) | +3.3 (4.6) |
| ON set (no ER; f=0), arm ON, C2 12R vs as-is (arm ON) | -3.5 (27.0) | -5.4 (15.8) | -3.2 (14.7) | -8.9 (10.8) | -1.4 (8.7) |
| ON set (no ER; f=0), arm ON, C3 12R vs as-is (arm ON) | +4.7 (13.0) | +5.9 (9.7) | +4.9 (8.7) | -0.0 (3.1) | +2.4 (5.2) |
| ON set (no ER; f=0), arm ON: pure combined-lock effect 12R (paired, same set) | -4.1 (21.9) | -5.9 (12.2) | -3.9 (11.5) | -9.3 (9.9) | -4.8 (7.5) |
| ON set (no ER; f=0), arm OFF, C1 no combined lock vs as-is (arm OFF) | +3.2 (11.0) | +2.3 (5.9) | +2.5 (5.3) | +0.8 (3.7) | +2.3 (4.5) |
| ON set (no ER; f=0), arm OFF, C2 12R vs as-is (arm OFF) | +0.4 (24.2) | -5.0 (14.5) | -2.2 (13.7) | -7.4 (12.1) | -2.3 (8.1) |
| ON set (no ER; f=0), arm OFF, C3 12R vs as-is (arm OFF) | +3.2 (9.9) | +4.0 (6.4) | +4.1 (6.0) | -0.4 (1.8) | +1.2 (5.0) |
| ON set (no ER; f=0), arm OFF: pure combined-lock effect 12R (paired, same set) | -2.8 (19.6) | -7.4 (12.1) | -4.7 (11.7) | -8.2 (11.4) | -4.6 (6.8) |
| ON set (no ER; f=0): pure day-arm effect, no combined lock (arm OFF minus ON) | +4.8 (14.9) | +3.7 (8.5) | +3.7 (7.6) | -3.2 (7.7) | -1.1 (2.4) |
| ON set (no ER; f=0): pure day-arm effect, 12R (arm OFF minus ON) | +6.0 (11.9) | +2.3 (9.0) | +2.9 (8.0) | -2.1 (6.8) | -0.9 (1.5) |
| ER P6+K6 f=0.03, feeds running max, int lots, arm ON, C1 no combined lock vs as-is (arm ON) | -0.2 (14.7) | +0.1 (8.9) | +0.3 (7.9) | +1.0 (4.0) | +3.2 (4.5) |
| ER P6+K6 f=0.03, feeds running max, int lots, arm ON, C2 12R vs as-is (arm ON) | -4.3 (25.5) | -5.9 (15.2) | -3.3 (14.2) | -8.2 (10.7) | -1.6 (8.7) |
| ER P6+K6 f=0.03, feeds running max, int lots, arm ON, C3 12R vs as-is (arm ON) | +4.0 (9.2) | +5.5 (8.6) | +4.9 (7.6) | +0.7 (2.8) | +2.2 (5.1) |
| ER P6+K6 f=0.03, feeds running max, int lots, arm ON: pure combined-lock effect 12R (paired, same set) | -4.1 (22.0) | -5.9 (12.2) | -3.6 (11.6) | -9.2 (9.9) | -4.7 (7.5) |
| ER P6+K6 f=0.03, feeds running max, int lots, arm OFF, C1 no combined lock vs as-is (arm OFF) | +2.6 (9.2) | +1.9 (5.1) | +2.1 (4.6) | +1.1 (3.7) | +2.3 (4.5) |
| ER P6+K6 f=0.03, feeds running max, int lots, arm OFF, C2 12R vs as-is (arm OFF) | -1.5 (23.2) | -6.0 (13.9) | -3.1 (13.4) | -7.3 (12.1) | -2.2 (8.0) |
| ER P6+K6 f=0.03, feeds running max, int lots, arm OFF, C3 12R vs as-is (arm OFF) | +1.3 (6.7) | +3.0 (5.4) | +3.2 (5.1) | -0.3 (1.8) | +1.3 (5.0) |
| ER P6+K6 f=0.03, feeds running max, int lots, arm OFF: pure combined-lock effect 12R (paired, same set) | -4.1 (19.7) | -8.0 (12.0) | -5.3 (11.7) | -8.4 (11.5) | -4.5 (6.7) |
| ER P6+K6 f=0.03, feeds running max, int lots: pure day-arm effect, no combined lock (arm OFF minus ON) | +4.8 (14.7) | +3.8 (8.4) | +3.8 (7.5) | -3.6 (7.4) | -0.9 (2.3) |
| ER P6+K6 f=0.03, feeds running max, int lots: pure day-arm effect, 12R (arm OFF minus ON) | +4.9 (14.1) | +1.7 (9.6) | +2.1 (8.6) | -2.8 (6.5) | -0.7 (1.4) |
| ER P6+K6 f=0.03, feeds running max, fractional lots, arm ON, C1 no combined lock vs as-is (arm ON) | -0.3 (16.1) | -0.2 (9.7) | +0.0 (8.8) | +1.2 (3.8) | +3.5 (4.8) |
| ER P6+K6 f=0.03, feeds running max, fractional lots, arm ON, C2 12R vs as-is (arm ON) | -4.3 (25.7) | -5.7 (15.4) | -3.3 (14.4) | -8.3 (10.8) | -1.4 (8.8) |
| ER P6+K6 f=0.03, feeds running max, fractional lots, arm ON, C3 12R vs as-is (arm ON) | +3.9 (9.8) | +5.7 (8.9) | +4.8 (8.0) | +0.6 (2.9) | +2.4 (5.4) |
| ER P6+K6 f=0.03, feeds running max, fractional lots, arm ON: pure combined-lock effect 12R (paired, same set) | -4.0 (21.7) | -5.5 (11.7) | -3.4 (10.9) | -9.5 (9.8) | -4.9 (7.7) |
| ER P6+K6 f=0.03, feeds running max, fractional lots, arm OFF, C1 no combined lock vs as-is (arm OFF) | +3.0 (10.9) | +1.9 (5.9) | +2.4 (5.4) | +1.2 (3.7) | +2.8 (4.8) |
| ER P6+K6 f=0.03, feeds running max, fractional lots, arm OFF, C2 12R vs as-is (arm OFF) | +0.4 (23.8) | -5.1 (14.3) | -2.2 (13.6) | -7.3 (12.1) | -1.9 (8.2) |
| ER P6+K6 f=0.03, feeds running max, fractional lots, arm OFF, C3 12R vs as-is (arm OFF) | +3.2 (9.0) | +3.9 (6.1) | +4.1 (5.7) | -0.3 (2.0) | +1.6 (5.3) |
| ER P6+K6 f=0.03, feeds running max, fractional lots, arm OFF: pure combined-lock effect 12R (paired, same set) | -2.6 (19.1) | -7.0 (11.5) | -4.6 (11.0) | -8.5 (11.3) | -4.7 (6.9) |
| ER P6+K6 f=0.03, feeds running max, fractional lots: pure day-arm effect, no combined lock (arm OFF minus ON) | +5.4 (13.7) | +4.0 (8.0) | +4.2 (7.2) | -3.6 (7.3) | -0.8 (2.3) |
| ER P6+K6 f=0.03, feeds running max, fractional lots: pure day-arm effect, 12R (arm OFF minus ON) | +6.8 (10.4) | +2.5 (8.8) | +3.0 (7.9) | -2.6 (6.4) | -0.6 (1.4) |
| ER P6+K6 f=0.36, feeds running max, int lots, arm ON, C1 no combined lock vs as-is (arm ON) | -2.2 (10.2) | +0.9 (7.7) | +0.6 (7.3) | +0.8 (6.5) | +4.5 (7.2) |
| ER P6+K6 f=0.36, feeds running max, int lots, arm ON, C2 12R vs as-is (arm ON) | -9.1 (24.8) | -7.6 (16.1) | -4.5 (15.2) | -4.4 (10.8) | +1.0 (8.8) |
| ER P6+K6 f=0.36, feeds running max, int lots, arm ON, C3 12R vs as-is (arm ON) | -0.8 (7.5) | +3.8 (6.7) | +3.7 (6.1) | +4.5 (8.9) | +4.8 (8.4) |
| ER P6+K6 f=0.36, feeds running max, int lots, arm ON: pure combined-lock effect 12R (paired, same set) | -6.8 (20.5) | -8.5 (12.2) | -5.1 (12.2) | -5.2 (7.9) | -3.5 (7.0) |
| ER P6+K6 f=0.36, feeds running max, int lots, arm OFF, C1 no combined lock vs as-is (arm OFF) | -0.2 (11.9) | +1.1 (7.1) | +0.8 (6.7) | +1.7 (6.1) | +4.1 (7.3) |
| ER P6+K6 f=0.36, feeds running max, int lots, arm OFF, C2 12R vs as-is (arm OFF) | -4.8 (23.5) | -5.2 (13.8) | -2.7 (13.4) | -0.2 (10.6) | +0.2 (8.5) |
| ER P6+K6 f=0.36, feeds running max, int lots, arm OFF, C3 12R vs as-is (arm OFF) | -1.9 (7.7) | +3.8 (7.1) | +3.7 (6.4) | +6.8 (8.9) | +3.7 (7.7) |
| ER P6+K6 f=0.36, feeds running max, int lots, arm OFF: pure combined-lock effect 12R (paired, same set) | -4.6 (18.3) | -6.2 (10.5) | -3.5 (11.1) | -1.9 (9.3) | -3.9 (7.4) |
| ER P6+K6 f=0.36, feeds running max, int lots: pure day-arm effect, no combined lock (arm OFF minus ON) | +4.2 (13.1) | +2.0 (7.5) | +2.1 (6.7) | -2.7 (7.4) | -0.5 (2.3) |
| ER P6+K6 f=0.36, feeds running max, int lots: pure day-arm effect, 12R (arm OFF minus ON) | +6.4 (9.7) | +4.3 (10.2) | +3.7 (8.9) | +0.5 (3.7) | -0.8 (4.4) |
| ER P6+K6 f=1.0, feeds running max, int lots, arm ON, C1 no combined lock vs as-is (arm ON) | +8.9 (14.0) | +10.1 (9.6)* | +9.2 (9.5) | +0.9 (9.3) | +4.1 (14.0) |
| ER P6+K6 f=1.0, feeds running max, int lots, arm ON, C2 12R vs as-is (arm ON) | +3.6 (23.1) | +1.7 (14.8) | +4.3 (14.1) | -6.2 (12.4) | +1.8 (12.7) |
| ER P6+K6 f=1.0, feeds running max, int lots, arm ON, C3 12R vs as-is (arm ON) | +11.8 (22.9) | +13.0 (12.8)* | +12.4 (11.5)* | +2.7 (9.1) | +5.6 (12.0) |
| ER P6+K6 f=1.0, feeds running max, int lots, arm ON: pure combined-lock effect 12R (paired, same set) | -5.4 (17.5) | -8.4 (12.0) | -4.9 (12.8) | -7.1 (11.9) | -2.3 (12.8) |
| ER P6+K6 f=1.0, feeds running max, int lots, arm OFF, C1 no combined lock vs as-is (arm OFF) | +7.6 (13.7) | +7.8 (9.7) | +7.4 (9.2) | +2.9 (9.3) | +1.5 (13.4) |
| ER P6+K6 f=1.0, feeds running max, int lots, arm OFF, C2 12R vs as-is (arm OFF) | +2.5 (24.7) | -1.9 (15.2) | +1.2 (14.7) | -2.0 (13.3) | +0.1 (11.8) |
| ER P6+K6 f=1.0, feeds running max, int lots, arm OFF, C3 12R vs as-is (arm OFF) | +5.3 (14.4) | +7.1 (12.9) | +7.5 (11.6) | +5.1 (10.9) | +3.7 (11.7) |
| ER P6+K6 f=1.0, feeds running max, int lots, arm OFF: pure combined-lock effect 12R (paired, same set) | -5.1 (25.3) | -9.7 (16.0) | -6.2 (16.1) | -4.8 (11.7) | -1.4 (12.1) |
| ER P6+K6 f=1.0, feeds running max, int lots: pure day-arm effect, no combined lock (arm OFF minus ON) | +0.8 (18.7) | -0.4 (10.1) | +0.1 (8.9) | -1.7 (7.5) | -2.6 (3.3) |
| ER P6+K6 f=1.0, feeds running max, int lots: pure day-arm effect, 12R (arm OFF minus ON) | +1.0 (20.6) | -1.6 (11.8) | -1.2 (10.4) | +0.6 (5.8) | -1.7 (2.2) |
| ER P6+K6 f=1.0, locks at planned R, int lots, arm ON, C1 no combined lock vs as-is (arm ON) | +8.3 (18.6) | +7.6 (12.9) | +6.9 (11.8) | -2.6 (9.5) | +5.8 (12.5) |
| ER P6+K6 f=1.0, locks at planned R, int lots, arm ON, C2 12R vs as-is (arm ON) | -12.2 (30.5) | -10.1 (20.4) | -6.9 (18.6) | -11.8 (13.2) | +3.6 (12.2) |
| ER P6+K6 f=1.0, locks at planned R, int lots, arm ON, C3 12R vs as-is (arm ON) | -4.0 (21.2) | +1.3 (14.5) | +1.3 (12.6) | -2.8 (10.3) | +7.4 (11.9) |
| ER P6+K6 f=1.0, locks at planned R, int lots, arm ON: pure combined-lock effect 12R (paired, same set) | -20.5 (32.8) | -17.7 (19.1) | -13.8 (17.8) | -9.2 (11.6) | -2.2 (10.0) |
| ER P6+K6 f=1.0, locks at planned R, int lots, arm OFF, C1 no combined lock vs as-is (arm OFF) | +10.9 (12.6) | +9.6 (9.4)* | +9.3 (8.8)* | +1.4 (8.3) | +1.6 (11.7) |
| ER P6+K6 f=1.0, locks at planned R, int lots, arm OFF, C2 12R vs as-is (arm OFF) | -3.3 (30.8) | -8.0 (19.2) | -4.0 (17.9) | -6.8 (13.1) | -3.1 (11.4) |
| ER P6+K6 f=1.0, locks at planned R, int lots, arm OFF, C3 12R vs as-is (arm OFF) | -0.5 (21.5) | +1.0 (15.2) | +2.3 (13.5) | +0.2 (7.1) | +0.4 (10.1) |
| ER P6+K6 f=1.0, locks at planned R, int lots, arm OFF: pure combined-lock effect 12R (paired, same set) | -14.2 (29.6) | -17.6 (19.0) | -13.3 (17.8) | -8.2 (12.2) | -4.8 (11.1) |
| ER P6+K6 f=1.0, locks at planned R, int lots: pure day-arm effect, no combined lock (arm OFF minus ON) | +4.7 (24.4) | +3.9 (13.7) | +4.3 (12.0) | +0.3 (9.1) | -4.3 (5.2) |
| ER P6+K6 f=1.0, locks at planned R, int lots: pure day-arm effect, 12R (arm OFF minus ON) | +11.1 (19.9) | +4.0 (15.8) | +4.7 (13.9) | +1.3 (8.6) | -6.8 (7.4) |
| as-is arm ON: combined-lock effect 12R (paired) | -8.2 (23.6) | -11.4 (14.3) | -8.2 (13.6) | -8.9 (10.4) | -3.8 (8.0) |
| as-is arm OFF: combined-lock effect 12R (paired) | -2.8 (22.1) | -9.0 (13.5) | -6.4 (13.0) | -7.0 (12.0) | -3.5 (7.4) |
| as-is: pure day-arm effect (OFF minus ON, no combined lock) | +2.1 (14.1) | +1.9 (7.8) | +1.9 (6.9) | -3.7 (7.0) | -0.1 (2.3) |
| as-is: pure day-arm effect (OFF minus ON, 12R) | +7.5 (9.3) | +4.3 (11.5) | +3.7 (10.0) | -1.8 (6.1) | +0.2 (1.7) |

## Table 3b - (d) all lock sizes, ON + ER P6+K6 arm OFF vs arm ON (delta vs as-is with the same arm; C2/C3)

| convention / variant | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| C1 no combined lock: ER P6+K6 f=0.03, feeds running max, fractional lots, arm ON | -0.3 (16.1) | -0.2 (9.7) | +0.0 (8.8) | +1.2 (3.8) | +3.5 (4.8) |
| C1 no combined lock: ER P6+K6 f=0.03, feeds running max, fractional lots, arm OFF | +3.0 (10.9) | +1.9 (5.9) | +2.4 (5.4) | +1.2 (3.7) | +2.8 (4.8) |
| C1 no combined lock: ER P6+K6 f=0.36, feeds running max, int lots, arm ON | -2.2 (10.2) | +0.9 (7.7) | +0.6 (7.3) | +0.8 (6.5) | +4.5 (7.2) |
| C1 no combined lock: ER P6+K6 f=0.36, feeds running max, int lots, arm OFF | -0.2 (11.9) | +1.1 (7.1) | +0.8 (6.7) | +1.7 (6.1) | +4.1 (7.3) |
| C1 no combined lock: ER P6+K6 f=1.0, feeds running max, int lots, arm ON | +8.9 (14.0) | +10.1 (9.6)* | +9.2 (9.5) | +0.9 (9.3) | +4.1 (14.0) |
| C1 no combined lock: ER P6+K6 f=1.0, feeds running max, int lots, arm OFF | +7.6 (13.7) | +7.8 (9.7) | +7.4 (9.2) | +2.9 (9.3) | +1.5 (13.4) |
| C2 12R: ER P6+K6 f=0.03, feeds running max, fractional lots, arm ON | -4.3 (25.7) | -5.7 (15.4) | -3.3 (14.4) | -8.3 (10.8) | -1.4 (8.8) |
| C2 12R: ER P6+K6 f=0.03, feeds running max, fractional lots, arm OFF | +0.4 (23.8) | -5.1 (14.3) | -2.2 (13.6) | -7.3 (12.1) | -1.9 (8.2) |
| C2 12R: ER P6+K6 f=0.36, feeds running max, int lots, arm ON | -9.1 (24.8) | -7.6 (16.1) | -4.5 (15.2) | -4.4 (10.8) | +1.0 (8.8) |
| C2 12R: ER P6+K6 f=0.36, feeds running max, int lots, arm OFF | -4.8 (23.5) | -5.2 (13.8) | -2.7 (13.4) | -0.2 (10.6) | +0.2 (8.5) |
| C2 12R: ER P6+K6 f=1.0, feeds running max, int lots, arm ON | +3.6 (23.1) | +1.7 (14.8) | +4.3 (14.1) | -6.2 (12.4) | +1.8 (12.7) |
| C2 12R: ER P6+K6 f=1.0, feeds running max, int lots, arm OFF | +2.5 (24.7) | -1.9 (15.2) | +1.2 (14.7) | -2.0 (13.3) | +0.1 (11.8) |
| C2 20R: ER P6+K6 f=0.03, feeds running max, fractional lots, arm ON | +2.3 (15.3) | +0.1 (10.4) | +0.6 (9.6) | -4.2 (7.9) | -0.5 (6.6) |
| C2 20R: ER P6+K6 f=0.03, feeds running max, fractional lots, arm OFF | +5.1 (14.3) | +1.6 (8.8) | +2.4 (8.3) | -4.0 (8.2) | -1.1 (6.0) |
| C2 20R: ER P6+K6 f=0.36, feeds running max, int lots, arm ON | -0.2 (13.9) | +0.4 (9.8) | +1.4 (9.6) | -5.6 (9.7) | +1.7 (7.2) |
| C2 20R: ER P6+K6 f=0.36, feeds running max, int lots, arm OFF | +0.8 (18.4) | -1.2 (11.6) | +0.3 (11.0) | -4.8 (9.9) | +0.4 (8.9) |
| C2 20R: ER P6+K6 f=1.0, feeds running max, int lots, arm ON | +4.4 (27.0) | +3.6 (16.2) | +4.9 (15.1) | -4.5 (11.8) | +3.1 (12.1) |
| C2 20R: ER P6+K6 f=1.0, feeds running max, int lots, arm OFF | +10.9 (16.4) | +3.6 (12.2) | +5.2 (12.0) | +0.8 (11.9) | +0.9 (11.2) |
| C2 30R: ER P6+K6 f=0.03, feeds running max, fractional lots, arm ON | -0.9 (17.6) | -0.5 (10.3) | -0.2 (9.3) | +0.6 (4.4) | +3.5 (4.8) |
| C2 30R: ER P6+K6 f=0.03, feeds running max, fractional lots, arm OFF | +3.6 (11.5) | +2.2 (6.2) | +2.6 (5.6) | -0.7 (4.3) | +2.8 (4.8) |
| C2 30R: ER P6+K6 f=0.36, feeds running max, int lots, arm ON | -2.2 (10.2) | +0.9 (7.7) | +0.7 (7.3) | -3.4 (9.1) | +2.3 (7.9) |
| C2 30R: ER P6+K6 f=0.36, feeds running max, int lots, arm OFF | +1.3 (13.6) | +1.8 (7.8) | +1.2 (7.4) | -1.6 (8.8) | +1.9 (7.8) |
| C2 30R: ER P6+K6 f=1.0, feeds running max, int lots, arm ON | +11.2 (16.6) | +9.5 (11.5) | +10.5 (11.0) | -4.5 (12.3) | +4.6 (13.7) |
| C2 30R: ER P6+K6 f=1.0, feeds running max, int lots, arm OFF | +10.6 (17.0) | +6.1 (12.6) | +7.9 (11.9) | -3.1 (12.7) | +3.0 (12.5) |
| C3 12R: ER P6+K6 f=0.03, feeds running max, fractional lots, arm ON | +3.9 (9.8) | +5.7 (8.9) | +4.8 (8.0) | +0.6 (2.9) | +2.4 (5.4) |
| C3 12R: ER P6+K6 f=0.03, feeds running max, fractional lots, arm OFF | +3.2 (9.0) | +3.9 (6.1) | +4.1 (5.7) | -0.3 (2.0) | +1.6 (5.3) |
| C3 12R: ER P6+K6 f=0.36, feeds running max, int lots, arm ON | -0.8 (7.5) | +3.8 (6.7) | +3.7 (6.1) | +4.5 (8.9) | +4.8 (8.4) |
| C3 12R: ER P6+K6 f=0.36, feeds running max, int lots, arm OFF | -1.9 (7.7) | +3.8 (7.1) | +3.7 (6.4) | +6.8 (8.9) | +3.7 (7.7) |
| C3 12R: ER P6+K6 f=1.0, feeds running max, int lots, arm ON | +11.8 (22.9) | +13.0 (12.8)* | +12.4 (11.5)* | +2.7 (9.1) | +5.6 (12.0) |
| C3 12R: ER P6+K6 f=1.0, feeds running max, int lots, arm OFF | +5.3 (14.4) | +7.1 (12.9) | +7.5 (11.6) | +5.1 (10.9) | +3.7 (11.7) |
| C3 20R: ER P6+K6 f=0.03, feeds running max, fractional lots, arm ON | -0.5 (12.9) | +3.1 (9.9) | +2.7 (8.9) | +0.7 (4.0) | +4.3 (6.0) |
| C3 20R: ER P6+K6 f=0.03, feeds running max, fractional lots, arm OFF | +1.8 (11.1) | +4.1 (8.7) | +3.9 (7.7) | +1.0 (3.6) | +3.4 (6.0) |
| C3 20R: ER P6+K6 f=0.36, feeds running max, int lots, arm ON | -3.0 (9.5) | +3.3 (9.7) | +3.5 (8.7) | -0.7 (6.4) | +6.5 (8.8) |
| C3 20R: ER P6+K6 f=0.36, feeds running max, int lots, arm OFF | -2.5 (14.4) | +1.3 (11.9) | +1.8 (10.6) | +0.2 (6.0) | +4.9 (10.6) |
| C3 20R: ER P6+K6 f=1.0, feeds running max, int lots, arm ON | +1.6 (24.9) | +6.5 (14.2) | +7.0 (12.7) | +0.5 (10.4) | +7.9 (11.7) |
| C3 20R: ER P6+K6 f=1.0, feeds running max, int lots, arm OFF | +7.6 (12.8) | +6.1 (9.5) | +6.7 (8.7) | +5.7 (9.9) | +5.5 (11.1) |
| C3 30R: ER P6+K6 f=0.03, feeds running max, fractional lots, arm ON | -2.0 (17.0) | -1.1 (10.1) | -0.9 (9.1) | +3.0 (6.6) | +3.5 (4.9) |
| C3 30R: ER P6+K6 f=0.03, feeds running max, fractional lots, arm OFF | +2.0 (10.6) | +1.4 (5.8) | +1.6 (5.2) | +2.1 (6.6) | +3.9 (5.6) |
| C3 30R: ER P6+K6 f=0.36, feeds running max, int lots, arm ON | -3.3 (9.2) | +0.4 (7.5) | +0.0 (7.1) | -1.0 (9.8) | +2.3 (7.9) |
| C3 30R: ER P6+K6 f=0.36, feeds running max, int lots, arm OFF | -0.3 (11.7) | +1.0 (7.1) | +0.2 (6.9) | +1.3 (9.3) | +3.0 (7.6) |
| C3 30R: ER P6+K6 f=1.0, feeds running max, int lots, arm ON | +10.1 (15.2) | +9.0 (11.0) | +9.9 (10.5) | -2.2 (11.8) | +4.6 (13.7) |
| C3 30R: ER P6+K6 f=1.0, feeds running max, int lots, arm OFF | +9.0 (14.7) | +5.3 (11.8) | +6.9 (11.0) | -0.2 (12.0) | +4.1 (12.7) |

## Table 4 - the sizer's own step: ER P6+K6 minus the ON set, paired, same lock (day arm ON)

| lock / variant | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| C1 off: ER P6+K6 f=0.03, feeds running max, int lots minus ON | -0.7 (4.2) | -0.4 (2.1) | -0.4 (2.1) | +0.7 (1.1) | -0.2 (0.5) |
| C1 off: ER P6+K6 f=0.03, feeds running max, fractional lots minus ON | -0.9 (5.3) | -0.7 (2.9) | -0.6 (2.8) | +0.9 (1.3) | +0.2 (1.7) |
| C1 off: ER P6+K6 f=0.03, locks at planned R, int lots minus ON | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) |
| C1 off: ER P6+K6 f=0.03, locks at planned R, fractional lots minus ON | +3.6 (6.4) | +1.6 (3.5) | +1.1 (3.2) | +0.0 (1.2) | -0.2 (0.9) |
| C1 off: ER P6+K6 f=0.07, feeds running max, int lots minus ON | -2.8 (11.0) | -0.9 (6.5) | -0.8 (6.0) | +1.6 (3.0) | +2.4 (3.8) |
| C1 off: ER P6+K6 f=0.07, feeds running max, fractional lots minus ON | -4.0 (13.5) | -1.0 (7.5) | -0.9 (6.7) | +0.1 (2.9) | +1.5 (4.1) |
| C1 off: ER P6+K6 f=0.07, locks at planned R, int lots minus ON | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) |
| C1 off: ER P6+K6 f=0.07, locks at planned R, fractional lots minus ON | +2.1 (6.5) | +1.5 (4.6) | +1.4 (4.2) | -0.3 (2.6) | +2.1 (2.7) |
| C1 off: ER P6+K6 f=0.36, feeds running max, int lots minus ON | -2.8 (15.3) | +0.4 (8.6) | -0.1 (8.0) | +0.4 (6.2) | +1.1 (5.4) |
| C1 off: ER P6+K6 f=0.36, feeds running max, fractional lots minus ON | +1.8 (17.7) | +2.7 (9.4) | +2.2 (8.4) | +0.6 (5.9) | +0.9 (5.7) |
| C1 off: ER P6+K6 f=0.36, locks at planned R, int lots minus ON | -3.5 (13.7) | +0.6 (8.4) | +0.6 (7.4) | -1.0 (3.9) | +1.5 (4.8) |
| C1 off: ER P6+K6 f=0.36, locks at planned R, fractional lots minus ON | -1.3 (14.8) | +1.2 (9.1) | +0.9 (8.1) | -0.7 (4.4) | +1.9 (5.4) |
| C1 off: ER P6+K6 f=1.0, feeds running max, int lots minus ON | +8.4 (21.0) | +9.6 (12.1) | +8.5 (11.5) | +0.5 (9.0) | +0.7 (12.4) |
| C1 off: ER P6+K6 f=1.0, feeds running max, fractional lots minus ON | +6.1 (20.4) | +6.7 (12.5) | +5.8 (11.6) | +0.3 (9.5) | -0.2 (10.7) |
| C1 off: ER P6+K6 f=1.0, locks at planned R, int lots minus ON | +7.7 (14.0) | +7.1 (10.1) | +6.2 (9.5) | -2.9 (7.8) | +2.5 (10.8) |
| C1 off: ER P6+K6 f=1.0, locks at planned R, fractional lots minus ON | +7.6 (13.7) | +4.8 (10.8) | +4.1 (10.0) | -2.2 (7.5) | +1.4 (10.6) |
| C2 12R: ER P6+K6 f=0.03, feeds running max, int lots minus ON | -0.8 (4.2) | -0.4 (2.1) | -0.1 (2.0) | +0.8 (1.3) | -0.2 (0.6) |
| C2 12R: ER P6+K6 f=0.03, feeds running max, fractional lots minus ON | -0.8 (5.0) | -0.2 (2.5) | -0.1 (2.2) | +0.6 (1.1) | +0.1 (1.6) |
| C2 12R: ER P6+K6 f=0.03, locks at planned R, int lots minus ON | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) |
| C2 12R: ER P6+K6 f=0.03, locks at planned R, fractional lots minus ON | +0.5 (1.2) | +0.0 (1.2) | +0.0 (1.1) | +1.6 (4.8) | +0.0 (0.8) |
| C2 12R: ER P6+K6 f=0.07, feeds running max, int lots minus ON | -3.8 (8.3) | -4.0 (7.8) | -3.2 (6.9) | +1.4 (3.7) | +2.4 (3.9) |
| C2 12R: ER P6+K6 f=0.07, feeds running max, fractional lots minus ON | -6.5 (14.1) | -2.8 (7.4) | -2.3 (6.5) | +1.0 (2.0) | +0.0 (3.0) |
| C2 12R: ER P6+K6 f=0.07, locks at planned R, int lots minus ON | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) |
| C2 12R: ER P6+K6 f=0.07, locks at planned R, fractional lots minus ON | -0.3 (4.0) | +0.6 (3.7) | +0.7 (3.3) | +0.7 (1.5) | +2.7 (5.5) |
| C2 12R: ER P6+K6 f=0.36, feeds running max, int lots minus ON | -5.6 (12.3) | -2.1 (10.1) | -1.2 (8.9) | +4.5 (9.0) | +2.4 (7.9) |
| C2 12R: ER P6+K6 f=0.36, feeds running max, fractional lots minus ON | -4.2 (15.8) | +1.0 (9.0) | +1.2 (7.9) | +4.3 (8.8) | +2.6 (7.4) |
| C2 12R: ER P6+K6 f=0.36, locks at planned R, int lots minus ON | -3.3 (10.6) | +1.0 (7.2) | +1.1 (6.3) | -0.3 (5.0) | +2.3 (5.9) |
| C2 12R: ER P6+K6 f=0.36, locks at planned R, fractional lots minus ON | -0.7 (10.6) | +0.0 (9.4) | +0.3 (8.2) | -0.8 (5.3) | +3.0 (6.2) |
| C2 12R: ER P6+K6 f=1.0, feeds running max, int lots minus ON | +7.1 (27.4) | +7.1 (15.6) | +7.5 (13.8) | +2.7 (9.2) | +3.2 (10.7) |
| C2 12R: ER P6+K6 f=1.0, feeds running max, fractional lots minus ON | +4.7 (16.3) | +3.5 (12.3) | +4.0 (11.0) | +2.4 (10.4) | +1.8 (10.3) |
| C2 12R: ER P6+K6 f=1.0, locks at planned R, int lots minus ON | -8.7 (18.3) | -4.6 (14.2) | -3.6 (12.6) | -2.8 (9.7) | +5.0 (9.3) |
| C2 12R: ER P6+K6 f=1.0, locks at planned R, fractional lots minus ON | -1.2 (7.8) | -0.4 (10.4) | -0.1 (9.1) | -1.4 (8.7) | +4.5 (9.3) |
| C2 20R: ER P6+K6 f=0.03, feeds running max, int lots minus ON | -0.6 (4.2) | +2.1 (7.3) | +2.1 (6.4) | +0.5 (1.1) | -0.2 (0.6) |
| C2 20R: ER P6+K6 f=0.03, feeds running max, fractional lots minus ON | -0.7 (5.1) | +1.9 (6.5) | +1.6 (5.7) | +0.4 (1.2) | +0.2 (1.8) |
| C2 20R: ER P6+K6 f=0.03, locks at planned R, int lots minus ON | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) |
| C2 20R: ER P6+K6 f=0.03, locks at planned R, fractional lots minus ON | +1.0 (1.8) | +0.3 (1.4) | +0.3 (1.2) | +0.1 (1.2) | -0.2 (0.9) |
| C2 20R: ER P6+K6 f=0.07, feeds running max, int lots minus ON | -1.6 (11.0) | +1.1 (9.1) | +1.3 (8.0) | +0.4 (3.6) | +2.4 (3.9) |
| C2 20R: ER P6+K6 f=0.07, feeds running max, fractional lots minus ON | -2.9 (13.5) | +1.0 (9.3) | +1.2 (8.1) | -1.0 (3.7) | -1.6 (6.4) |
| C2 20R: ER P6+K6 f=0.07, locks at planned R, int lots minus ON | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) |
| C2 20R: ER P6+K6 f=0.07, locks at planned R, fractional lots minus ON | -0.0 (4.2) | +2.9 (7.0) | +2.6 (6.2) | -0.2 (2.5) | +2.2 (2.7) |
| C2 20R: ER P6+K6 f=0.36, feeds running max, int lots minus ON | -3.2 (14.4) | +2.1 (10.3) | +2.4 (9.1) | -1.0 (7.0) | +2.4 (6.6) |
| C2 20R: ER P6+K6 f=0.36, feeds running max, fractional lots minus ON | +1.8 (16.3) | +4.9 (10.3) | +4.9 (9.0) | -0.7 (6.6) | +1.8 (6.9) |
| C2 20R: ER P6+K6 f=0.36, locks at planned R, int lots minus ON | -5.7 (11.9) | +2.0 (10.2) | +2.0 (8.9) | -1.2 (4.5) | +0.7 (4.1) |
| C2 20R: ER P6+K6 f=0.36, locks at planned R, fractional lots minus ON | -6.9 (20.4) | +1.1 (13.5) | +1.3 (11.8) | -1.3 (4.9) | +1.3 (4.7) |
| C2 20R: ER P6+K6 f=1.0, feeds running max, int lots minus ON | +1.4 (26.0) | +5.3 (14.2) | +5.9 (12.7) | +0.2 (10.7) | +3.8 (10.6) |
| C2 20R: ER P6+K6 f=1.0, feeds running max, fractional lots minus ON | -1.0 (24.8) | -0.6 (15.9) | +0.5 (14.2) | +1.4 (10.4) | +2.8 (9.2) |
| C2 20R: ER P6+K6 f=1.0, locks at planned R, int lots minus ON | -3.3 (21.9) | +4.1 (15.8) | +4.1 (13.9) | -0.6 (8.7) | +5.2 (11.3) |
| C2 20R: ER P6+K6 f=1.0, locks at planned R, fractional lots minus ON | -3.5 (21.3) | +1.7 (16.1) | +1.8 (14.1) | -0.2 (8.6) | +3.8 (11.3) |
| C2 30R: ER P6+K6 f=0.03, feeds running max, int lots minus ON | -0.7 (4.2) | -0.4 (2.1) | -0.4 (2.1) | +0.6 (1.2) | -0.2 (0.5) |
| C2 30R: ER P6+K6 f=0.03, feeds running max, fractional lots minus ON | -1.5 (5.8) | -1.0 (3.1) | -0.9 (2.9) | +0.9 (1.3) | +0.2 (1.7) |
| C2 30R: ER P6+K6 f=0.03, locks at planned R, int lots minus ON | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) |
| C2 30R: ER P6+K6 f=0.03, locks at planned R, fractional lots minus ON | +3.6 (6.4) | +1.6 (3.5) | +1.1 (3.2) | +0.1 (1.2) | -0.2 (0.9) |
| C2 30R: ER P6+K6 f=0.07, feeds running max, int lots minus ON | -3.2 (11.3) | -1.1 (6.6) | -1.5 (6.7) | +0.3 (4.6) | +2.4 (3.8) |
| C2 30R: ER P6+K6 f=0.07, feeds running max, fractional lots minus ON | -4.4 (13.7) | -1.2 (7.6) | -1.2 (6.7) | -0.9 (4.5) | +1.5 (4.1) |
| C2 30R: ER P6+K6 f=0.07, locks at planned R, int lots minus ON | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) |
| C2 30R: ER P6+K6 f=0.07, locks at planned R, fractional lots minus ON | +2.1 (6.5) | +1.5 (4.6) | +1.4 (4.2) | -0.3 (2.6) | +2.1 (2.7) |
| C2 30R: ER P6+K6 f=0.36, feeds running max, int lots minus ON | -2.8 (15.3) | +0.4 (8.6) | -0.0 (8.0) | -3.2 (8.8) | -1.1 (5.9) |
| C2 30R: ER P6+K6 f=0.36, feeds running max, fractional lots minus ON | +2.9 (17.8) | +3.3 (9.5) | +2.4 (8.7) | -4.1 (9.2) | -2.2 (6.7) |
| C2 30R: ER P6+K6 f=0.36, locks at planned R, int lots minus ON | -3.5 (13.7) | +0.6 (8.4) | +0.6 (7.4) | -0.3 (4.3) | +1.5 (4.8) |
| C2 30R: ER P6+K6 f=0.36, locks at planned R, fractional lots minus ON | -1.3 (14.8) | +1.2 (9.1) | +0.9 (8.1) | -0.4 (4.4) | +1.0 (6.2) |
| C2 30R: ER P6+K6 f=1.0, feeds running max, int lots minus ON | +10.7 (21.6) | +9.0 (12.5) | +9.8 (11.6) | -4.3 (12.3) | +1.2 (12.2) |
| C2 30R: ER P6+K6 f=1.0, feeds running max, fractional lots minus ON | +8.5 (21.2) | +6.1 (14.3) | +7.0 (13.1) | -4.8 (12.6) | +0.2 (10.7) |
| C2 30R: ER P6+K6 f=1.0, locks at planned R, int lots minus ON | +5.0 (14.0) | +5.8 (10.1) | +4.8 (9.8) | -3.7 (9.4) | +0.4 (12.0) |
| C2 30R: ER P6+K6 f=1.0, locks at planned R, fractional lots minus ON | +7.6 (13.7) | +4.8 (10.8) | +3.8 (10.2) | -2.0 (8.7) | -0.4 (11.6) |

## Table 5 - (b) and (c) as paired contrasts (day arm ON)

| contrast | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off, f=0.03: NOT feeding running max minus feeding (int lots) | +0.7 (4.2) | +0.4 (2.1) | +0.4 (2.1) | -0.7 (1.1) | +0.2 (0.5) |
| off, f=0.03: fractional minus integer lots (feeding) | -0.2 (2.9) | -0.3 (1.9) | -0.3 (2.0) | +0.2 (0.9) | +0.4 (1.7) |
| off, f=0.36: NOT feeding running max minus feeding (int lots) | -0.7 (17.3) | +0.2 (10.3) | +0.7 (9.2) | -1.5 (7.5) | +0.4 (4.1) |
| off, f=0.36: fractional minus integer lots (feeding) | +4.5 (5.2) | +2.3 (3.5) | +2.2 (3.2) | +0.2 (2.4) | -0.2 (2.3) |
| off, f=1.0: NOT feeding running max minus feeding (int lots) | -0.7 (19.4) | -2.4 (12.0) | -2.3 (10.9) | -3.5 (9.0) | +1.8 (6.9) |
| off, f=1.0: fractional minus integer lots (feeding) | -2.3 (9.6) | -2.9 (5.5) | -2.7 (4.9) | -0.2 (3.2) | -0.9 (4.2) |
| 12R, f=0.03: NOT feeding running max minus feeding (int lots) | +0.8 (4.2) | +0.4 (2.1) | +0.1 (2.0) | -0.8 (1.3) | +0.2 (0.6) |
| 12R, f=0.03: fractional minus integer lots (feeding) | -0.1 (2.4) | +0.2 (1.3) | -0.0 (1.4) | -0.1 (0.9) | +0.2 (1.6) |
| 12R, f=0.36: NOT feeding running max minus feeding (int lots) | +2.3 (14.9) | +3.1 (11.5) | +2.3 (10.1) | -4.9 (10.1) | -0.1 (6.8) |
| 12R, f=0.36: fractional minus integer lots (feeding) | +1.3 (4.9) | +3.1 (7.1) | +2.5 (6.2) | -0.2 (2.0) | +0.2 (4.0) |
| 12R, f=1.0: NOT feeding running max minus feeding (int lots) | -15.8 (36.4) | -11.7 (21.1) | -11.1 (18.5) | -5.5 (11.7) | +1.8 (10.7) |
| 12R, f=1.0: fractional minus integer lots (feeding) | -2.3 (19.9) | -3.6 (11.1) | -3.5 (9.7) | -0.3 (3.7) | -1.3 (2.1) |
| 20R, f=0.03: NOT feeding running max minus feeding (int lots) | +0.6 (4.2) | -2.1 (7.3) | -2.1 (6.4) | -0.5 (1.1) | +0.2 (0.6) |
| 20R, f=0.03: fractional minus integer lots (feeding) | -0.1 (2.6) | -0.2 (1.8) | -0.4 (1.7) | -0.1 (0.7) | +0.4 (1.7) |
| 20R, f=0.36: NOT feeding running max minus feeding (int lots) | -2.5 (17.9) | -0.1 (10.3) | -0.4 (9.1) | -0.2 (8.6) | -1.7 (5.9) |
| 20R, f=0.36: fractional minus integer lots (feeding) | +5.0 (4.8)* | +2.8 (3.3) | +2.5 (3.0) | +0.3 (2.9) | -0.6 (2.5) |
| 20R, f=1.0: NOT feeding running max minus feeding (int lots) | -4.7 (16.0) | -1.2 (11.8) | -1.8 (10.6) | -0.7 (12.7) | +1.5 (10.1) |
| 20R, f=1.0: fractional minus integer lots (feeding) | -2.3 (9.5) | -5.9 (9.3) | -5.4 (8.1) | +1.2 (4.6) | -1.0 (3.5) |
| 30R, f=0.03: NOT feeding running max minus feeding (int lots) | +0.7 (4.2) | +0.4 (2.1) | +0.4 (2.1) | -0.6 (1.2) | +0.2 (0.5) |
| 30R, f=0.03: fractional minus integer lots (feeding) | -0.8 (3.9) | -0.6 (2.3) | -0.5 (2.3) | +0.2 (0.9) | +0.4 (1.7) |
| 30R, f=0.36: NOT feeding running max minus feeding (int lots) | -0.7 (17.3) | +0.2 (10.3) | +0.6 (9.1) | +2.9 (9.8) | +2.6 (4.6) |
| 30R, f=0.36: fractional minus integer lots (feeding) | +5.6 (4.7)* | +2.9 (3.4) | +2.4 (3.1) | -0.9 (4.5) | -1.1 (3.4) |
| 30R, f=1.0: NOT feeding running max minus feeding (int lots) | -5.7 (22.7) | -3.3 (12.6) | -5.0 (11.2) | +0.6 (12.0) | -0.8 (8.7) |
| 30R, f=1.0: fractional minus integer lots (feeding) | -2.1 (9.6) | -2.9 (10.3) | -2.8 (9.0) | -0.5 (3.2) | -1.0 (4.0) |

## Table 6 - levels, $k/wk

| row | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| as-is off (arm ON) | 12.2 | 21.7 | 21.9 | 18.6 | -3.4 |
| off: ON set (no ER; f=0) | 12.7 | 22.2 | 22.5 | 19.0 | -0.1 |
| off: ER P6+K6 f=0.03, feeds running max, int lots | 12.0 | 21.8 | 22.2 | 19.6 | -0.3 |
| off: ER P6+K6 f=0.03, feeds running max, fractional lots | 11.8 | 21.5 | 21.9 | 19.8 | 0.1 |
| off: ER P6+K6 f=0.03, locks at planned R, int lots | 12.7 | 22.2 | 22.5 | 19.0 | -0.1 |
| off: ER P6+K6 f=0.03, locks at planned R, fractional lots | 16.3 | 23.8 | 23.6 | 19.0 | -0.3 |
| off: ER P6+K6 f=0.36, feeds running max, int lots | 9.9 | 22.6 | 22.5 | 19.4 | 1.0 |
| off: ER P6+K6 f=0.36, locks at planned R, int lots | 9.2 | 22.9 | 23.1 | 18.0 | 1.5 |
| off: ER P6+K6 f=1.0, feeds running max, int lots | 21.1 | 31.8 | 31.1 | 19.5 | 0.7 |
| off: ER P6+K6 f=1.0, locks at planned R, int lots | 20.4 | 29.4 | 28.8 | 16.0 | 2.4 |
| as-is 12R (arm ON) | 3.9 | 10.4 | 13.7 | 9.7 | -7.2 |
| 12R: ON set (no ER; f=0) | 8.6 | 16.3 | 18.6 | 9.7 | -4.8 |
| 12R: ER P6+K6 f=0.03, feeds running max, int lots | 7.9 | 15.9 | 18.6 | 10.4 | -5.0 |
| 12R: ER P6+K6 f=0.03, feeds running max, fractional lots | 7.8 | 16.0 | 18.5 | 10.3 | -4.8 |
| 12R: ER P6+K6 f=0.03, locks at planned R, int lots | 8.6 | 16.3 | 18.6 | 9.7 | -4.8 |
| 12R: ER P6+K6 f=0.03, locks at planned R, fractional lots | 9.2 | 16.3 | 18.7 | 11.3 | -4.8 |
| 12R: ER P6+K6 f=0.36, feeds running max, int lots | 3.1 | 14.2 | 17.4 | 14.2 | -2.4 |
| 12R: ER P6+K6 f=0.36, locks at planned R, int lots | 5.4 | 17.2 | 19.7 | 9.3 | -2.5 |
| 12R: ER P6+K6 f=1.0, feeds running max, int lots | 15.7 | 23.4 | 26.1 | 12.4 | -1.7 |
| 12R: ER P6+K6 f=1.0, locks at planned R, int lots | -0.1 | 11.7 | 15.0 | 6.8 | 0.2 |
| as-is 20R (arm ON) | 15.0 | 18.8 | 19.8 | 13.6 | -8.3 |
| 20R: ON set (no ER; f=0) | 15.2 | 20.0 | 20.9 | 14.0 | -4.1 |
| 20R: ER P6+K6 f=0.03, feeds running max, int lots | 14.5 | 22.1 | 23.0 | 14.5 | -4.3 |
| 20R: ER P6+K6 f=0.03, feeds running max, fractional lots | 14.5 | 21.8 | 22.5 | 14.4 | -3.9 |
| 20R: ER P6+K6 f=0.03, locks at planned R, int lots | 15.2 | 20.0 | 20.9 | 14.0 | -4.1 |
| 20R: ER P6+K6 f=0.03, locks at planned R, fractional lots | 16.2 | 20.2 | 21.1 | 14.1 | -4.3 |
| 20R: ER P6+K6 f=0.36, feeds running max, int lots | 12.0 | 22.1 | 23.3 | 13.0 | -1.7 |
| 20R: ER P6+K6 f=0.36, locks at planned R, int lots | 9.4 | 22.0 | 22.9 | 12.8 | -3.4 |
| 20R: ER P6+K6 f=1.0, feeds running max, int lots | 16.5 | 25.3 | 26.8 | 14.2 | -0.4 |
| 20R: ER P6+K6 f=1.0, locks at planned R, int lots | 11.9 | 24.1 | 25.0 | 13.4 | 1.1 |
| as-is 30R (arm ON) | 13.3 | 22.3 | 22.5 | 16.3 | -3.4 |
| 30R: ON set (no ER; f=0) | 12.7 | 22.2 | 22.6 | 18.4 | -0.1 |
| 30R: ER P6+K6 f=0.03, feeds running max, int lots | 12.0 | 21.8 | 22.2 | 19.0 | -0.3 |
| 30R: ER P6+K6 f=0.03, feeds running max, fractional lots | 11.2 | 21.2 | 21.7 | 19.2 | 0.1 |
| 30R: ER P6+K6 f=0.03, locks at planned R, int lots | 12.7 | 22.2 | 22.6 | 18.4 | -0.1 |
| 30R: ER P6+K6 f=0.03, locks at planned R, fractional lots | 16.3 | 23.8 | 23.7 | 18.4 | -0.3 |
| 30R: ER P6+K6 f=0.36, feeds running max, int lots | 9.9 | 22.6 | 22.5 | 15.2 | -1.1 |
| 30R: ER P6+K6 f=0.36, locks at planned R, int lots | 9.2 | 22.9 | 23.1 | 18.1 | 1.5 |
| 30R: ER P6+K6 f=1.0, feeds running max, int lots | 23.4 | 31.3 | 32.4 | 14.1 | 1.2 |
| 30R: ER P6+K6 f=1.0, locks at planned R, int lots | 17.7 | 28.0 | 27.3 | 14.7 | 0.3 |

## Table 7 - (e) risk lines, weekly series: mean / SD / maxDD / worst week / worst-20 sum ($k); day arm ON; as-is carries the same combined lock (C3 partner) in the lock rows

| lock | row | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| off | as-is | 12.2/45.5/88/-88/170 | 21.7/43.9/88/-88/58 | 21.9/53.8/144/-88/-187 | 18.6/50.4/162/-96/-811 | -3.4/29.0/317/-71/-572 |
| off | ON set (no ER; f=0) | 12.7/46.1/73/-71/178 | 22.2/44.0/73/-71/53 | 22.5/52.4/128/-73/-165 | 19.0/47.2/114/-85/-737 | -0.1/28.2/224/-63/-511 |
| off | ER P6+K6 f=0.03, feeds running max, int lots | 12.0/46.7/73/-71/168 | 21.8/44.5/73/-71/32 | 22.2/53.7/137/-73/-194 | 19.6/48.0/114/-85/-733 | -0.3/28.3/233/-63/-517 |
| off | ER P6+K6 f=0.03, feeds running max, fractional lots | 11.8/46.4/77/-68/166 | 21.5/44.4/77/-68/29 | 21.9/52.8/131/-68/-192 | 19.8/47.5/110/-86/-725 | 0.1/28.6/213/-64/-521 |
| off | ER P6+K6 f=0.03, locks at planned R, fractional lots | 16.3/42.6/68/-68/228 | 23.8/42.0/68/-68/90 | 23.6/51.4/137/-73/-137 | 19.0/46.9/117/-86/-736 | -0.3/28.3/215/-64/-513 |
| off | ER P6+K6 f=0.36, feeds running max, int lots | 9.9/40.3/68/-68/139 | 22.6/42.9/68/-68/31 | 22.5/54.0/158/-77/-203 | 19.4/52.3/184/-81/-797 | 1.0/30.2/191/-72/-517 |
| off | ER P6+K6 f=1.0, feeds running max, int lots | 21.1/50.8/75/-75/295 | 31.8/45.0/75/-75/216 | 31.1/57.3/151/-84/-68 | 19.5/57.2/248/-115/-1009 | 0.7/42.2/220/-90/-771 |
| off | ER P6+K6 f=1.0, locks at planned R, int lots | 20.4/42.1/43/-43/286 | 29.4/45.5/43/-43/150 | 28.8/55.9/143/-65/-110 | 16.0/49.5/191/-117/-943 | 2.4/40.6/127/-81/-688 |
| 12R | as-is | 3.9/40.7/105/-30/55 | 10.4/46.0/116/-30/-260 | 13.7/53.4/116/-30/-433 | 9.7/46.9/276/-30/-585 | -7.2/25.5/436/-30/-584 |
| 12R | as-is UNLOCKED (C2 partner) | 12.2/45.5/88/-88/170 | 21.7/43.9/88/-88/58 | 21.9/53.8/144/-88/-187 | 18.6/50.4/162/-96/-811 | -3.4/29.0/317/-71/-572 |
| 12R | ON set (no ER; f=0) | 8.6/40.0/50/-29/121 | 16.3/44.4/59/-29/-114 | 18.6/51.0/87/-29/-286 | 9.7/45.0/271/-31/-589 | -4.8/26.8/351/-30/-584 |
| 12R | ER P6+K6 f=0.03, feeds running max, int lots | 7.9/40.6/64/-29/110 | 15.9/44.8/64/-30/-134 | 18.6/51.9/87/-30/-303 | 10.4/45.6/272/-34/-589 | -5.0/26.8/357/-30/-583 |
| 12R | ER P6+K6 f=0.03, feeds running max, fractional lots | 7.8/40.4/64/-30/110 | 16.0/44.6/64/-30/-124 | 18.5/51.3/86/-30/-293 | 10.3/45.7/263/-31/-588 | -4.8/27.0/346/-30/-584 |
| 12R | ER P6+K6 f=0.03, locks at planned R, fractional lots | 9.2/40.9/50/-29/128 | 16.3/44.8/59/-29/-120 | 18.7/51.3/87/-29/-292 | 11.3/45.4/202/-31/-588 | -4.8/26.6/346/-30/-583 |
| 12R | ER P6+K6 f=0.36, feeds running max, int lots | 3.1/37.7/95/-35/43 | 14.2/46.0/95/-35/-199 | 17.4/53.3/95/-36/-349 | 14.2/50.8/221/-35/-603 | -2.4/28.6/277/-35/-560 |
| 12R | ER P6+K6 f=1.0, feeds running max, int lots | 15.7/50.4/53/-44/220 | 23.4/47.5/53/-44/-20 | 26.1/55.3/73/-44/-208 | 12.4/49.2/298/-45/-577 | -1.7/31.0/174/-44/-450 |
| 12R | ER P6+K6 f=1.0, locks at planned R, int lots | -0.1/33.8/87/-30/-1 | 11.7/47.6/117/-30/-257 | 15.0/55.5/117/-30/-423 | 6.8/42.7/305/-33/-593 | 0.2/34.9/248/-31/-586 |
| 20R | as-is | 15.0/39.7/49/-49/209 | 18.8/44.7/96/-49/-24 | 19.8/53.4/127/-49/-253 | 13.6/51.3/229/-49/-955 | -8.3/31.7/463/-49/-766 |
| 20R | as-is UNLOCKED (C2 partner) | 12.2/45.5/88/-88/170 | 21.7/43.9/88/-88/58 | 21.9/53.8/144/-88/-187 | 18.6/50.4/162/-96/-811 | -3.4/29.0/317/-71/-572 |
| 20R | ON set (no ER; f=0) | 15.2/41.8/48/-48/212 | 20.0/45.1/97/-49/-10 | 20.9/52.6/119/-49/-218 | 14.0/49.0/228/-49/-928 | -4.1/32.0/392/-49/-683 |
| 20R | ER P6+K6 f=0.03, feeds running max, int lots | 14.5/42.3/48/-48/204 | 22.1/43.4/49/-49/40 | 23.0/52.0/119/-49/-169 | 14.5/49.7/229/-49/-930 | -4.3/32.0/401/-49/-691 |
| 20R | ER P6+K6 f=0.03, feeds running max, fractional lots | 14.5/41.9/48/-48/203 | 21.8/43.2/49/-49/38 | 22.5/51.4/121/-49/-173 | 14.4/49.7/231/-51/-938 | -3.9/32.3/380/-49/-693 |
| 20R | ER P6+K6 f=0.03, locks at planned R, fractional lots | 16.2/42.0/48/-48/227 | 20.2/45.2/97/-48/-9 | 21.1/52.7/119/-48/-217 | 14.1/48.5/228/-49/-922 | -4.3/32.0/384/-50/-691 |
| 20R | ER P6+K6 f=0.36, feeds running max, int lots | 12.0/36.6/40/-40/168 | 22.1/42.7/43/-43/16 | 23.3/51.8/117/-57/-177 | 13.0/55.7/301/-57/-949 | -1.7/32.2/281/-57/-639 |
| 20R | ER P6+K6 f=1.0, feeds running max, int lots | 16.5/50.0/63/-50/231 | 25.3/47.0/63/-50/33 | 26.8/56.0/105/-57/-187 | 14.2/52.1/232/-62/-683 | -0.4/35.5/240/-72/-619 |
| 20R | ER P6+K6 f=1.0, locks at planned R, int lots | 11.9/45.6/48/-48/166 | 24.1/49.5/51/-51/3 | 25.0/57.6/117/-51/-209 | 13.4/47.8/212/-50/-963 | 1.1/40.7/172/-50/-740 |
| 30R | as-is | 13.3/43.0/73/-73/186 | 22.3/42.5/73/-73/73 | 22.5/52.6/139/-73/-166 | 16.3/52.1/145/-73/-927 | -3.4/29.0/318/-72/-573 |
| 30R | as-is UNLOCKED (C2 partner) | 12.2/45.5/88/-88/170 | 21.7/43.9/88/-88/58 | 21.9/53.8/144/-88/-187 | 18.6/50.4/162/-96/-811 | -3.4/29.0/317/-71/-572 |
| 30R | ON set (no ER; f=0) | 12.7/46.1/73/-71/178 | 22.2/44.0/73/-71/53 | 22.6/52.4/128/-72/-164 | 18.4/48.1/145/-85/-782 | -0.1/28.2/224/-63/-511 |
| 30R | ER P6+K6 f=0.03, feeds running max, int lots | 12.0/46.7/73/-71/168 | 21.8/44.5/73/-71/32 | 22.2/53.7/137/-73/-195 | 19.0/48.9/144/-85/-781 | -0.3/28.3/233/-63/-517 |
| 30R | ER P6+K6 f=0.03, feeds running max, fractional lots | 11.2/47.5/86/-73/157 | 21.2/45.0/86/-73/20 | 21.7/53.2/131/-73/-200 | 19.2/48.3/140/-85/-769 | 0.1/28.6/213/-64/-521 |
| 30R | ER P6+K6 f=0.03, locks at planned R, fractional lots | 16.3/42.6/68/-68/228 | 23.8/42.0/68/-68/90 | 23.7/51.3/137/-72/-136 | 18.4/47.8/148/-85/-779 | -0.3/28.3/215/-64/-513 |
| 30R | ER P6+K6 f=0.36, feeds running max, int lots | 9.9/40.3/68/-68/139 | 22.6/42.9/68/-68/31 | 22.5/54.0/157/-77/-202 | 15.2/55.7/310/-85/-1011 | -1.1/32.9/237/-72/-613 |
| 30R | ER P6+K6 f=1.0, feeds running max, int lots | 23.4/46.6/52/-36/328 | 31.3/44.4/52/-37/201 | 32.4/53.8/94/-56/-26 | 14.1/55.5/292/-79/-892 | 1.2/39.7/194/-56/-728 |
| 30R | ER P6+K6 f=1.0, locks at planned R, int lots | 17.7/46.8/72/-72/248 | 28.0/48.0/72/-72/112 | 27.3/58.1/151/-73/-156 | 14.7/48.5/145/-78/-960 | 0.3/43.7/184/-78/-781 |

Day arm OFF risk lines (as-is arm OFF same lock):

| lock | row | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| off | as-is arm OFF | 14.3/55.6/95/-95/200 | 23.6/50.8/95/-95/10 | 23.8/59.2/136/-95/-239 | 15.0/55.6/188/-95/-1088 | -3.5/28.5/309/-67/-573 |
| off | ON set (no ER; f=0), arm OFF | 17.5/51.7/84/-84/245 | 26.0/50.2/84/-84/39 | 26.3/57.9/121/-84/-199 | 15.8/53.2/147/-88/-1004 | -1.2/26.8/236/-45/-508 |
| off | ER P6+K6 f=0.03, feeds running max, fractional lots, arm OFF | 17.3/52.9/80/-80/242 | 25.5/50.7/80/-80/18 | 26.2/58.1/115/-80/-208 | 16.2/53.0/139/-84/-991 | -0.7/27.1/213/-46/-511 |
| off | ER P6+K6 f=1.0, feeds running max, int lots, arm OFF | 21.8/59.7/79/-79/306 | 31.5/51.4/79/-79/149 | 31.1/62.6/147/-93/-139 | 17.8/62.8/222/-115/-1153 | -1.9/40.1/264/-88/-756 |
| 12R | as-is arm OFF | 11.4/49.6/94/-29/160 | 14.6/52.4/94/-29/-242 | 17.4/58.5/94/-30/-442 | 7.9/47.4/259/-30/-585 | -7.0/25.8/417/-30/-584 |
| 12R | ON set (no ER; f=0), arm OFF | 14.7/47.4/71/-29/206 | 18.6/52.3/71/-29/-168 | 21.6/57.3/71/-29/-350 | 7.6/46.8/241/-31/-587 | -5.8/26.2/382/-31/-585 |
| 12R | ER P6+K6 f=0.03, feeds running max, fractional lots, arm OFF | 14.7/48.8/74/-29/205 | 18.6/52.8/74/-29/-177 | 21.5/58.0/74/-29/-356 | 7.7/47.1/233/-34/-599 | -5.4/26.4/364/-31/-585 |
| 12R | ER P6+K6 f=1.0, feeds running max, int lots, arm OFF | 16.7/55.4/103/-44/234 | 21.7/51.2/103/-44/-111 | 25.0/59.0/103/-44/-287 | 13.0/53.5/178/-43/-615 | -3.3/29.3/235/-44/-450 |

## Table 8 - (e) per-book contribution: book delta vs the as-is book (unlocked as-is), $k/wk (MDE), day arm ON. Sum of books = the set row of Table 1/2.

**off: ER P6+K6 f=0.03, feeds running max, fractional lots** (vs unlocked as-is)

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K6 | -0.2 (3.2) | -0.6 (2.9) | -0.5 (2.8) | -0.1 (1.5) | +0.3 (1.5) |
| P6 | -2.0 (11.7) | -1.5 (7.0) | -1.4 (6.3) | +1.7 (3.1) | +2.9 (3.2) |
| U6 | +1.0 (2.0) | +1.5 (1.7) | +1.6 (1.6) | -0.1 (0.4) | -0.2 (0.5) |
| H6 | +0.3 (3.5) | -0.1 (2.1) | -0.1 (1.9) | -0.5 (1.6) | +0.4 (2.1) |
| M6 | +0.5 (1.3) | +0.5 (1.3) | +0.4 (1.1) | +0.2 (0.8) | +0.1 (0.6) |
| A6 | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* |
| sum | -0.3 (16.1) | -0.2 (9.7) | +0.0 (8.8) | +1.2 (3.8) | +3.5 (4.8) |

**off: ER P6+K6 f=0.36, feeds running max, int lots** (vs unlocked as-is)

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K6 | -1.8 (6.8) | -1.5 (4.4) | -1.7 (4.1) | -0.0 (2.1) | -0.1 (1.9) |
| P6 | -2.3 (10.7) | +0.5 (6.7) | +0.3 (6.1) | +1.2 (6.4) | +4.3 (6.4) |
| U6 | +1.0 (2.0) | +1.5 (1.7) | +1.6 (1.6) | -0.1 (0.4) | -0.2 (0.5) |
| H6 | +0.3 (3.5) | -0.1 (2.1) | -0.1 (1.9) | -0.5 (1.6) | +0.4 (2.1) |
| M6 | +0.5 (1.3) | +0.5 (1.3) | +0.4 (1.1) | +0.2 (0.8) | +0.1 (0.6) |
| A6 | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* |
| sum | -2.2 (10.2) | +0.9 (7.7) | +0.6 (7.3) | +0.8 (6.5) | +4.5 (7.2) |

**off: ER P6+K6 f=1.0, feeds running max, int lots** (vs unlocked as-is)

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K6 | +3.2 (9.0) | +1.7 (6.3) | +1.5 (5.6) | -0.4 (3.2) | +0.2 (3.2) |
| P6 | +4.0 (16.7) | +6.5 (9.9) | +5.7 (9.3) | +1.6 (8.6) | +3.6 (12.4) |
| U6 | +1.0 (2.0) | +1.5 (1.7) | +1.6 (1.6) | -0.1 (0.4) | -0.2 (0.5) |
| H6 | +0.3 (3.5) | -0.1 (2.1) | -0.1 (1.9) | -0.5 (1.6) | +0.4 (2.1) |
| M6 | +0.5 (1.3) | +0.5 (1.3) | +0.4 (1.1) | +0.2 (0.8) | +0.1 (0.6) |
| A6 | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* |
| sum | +8.9 (14.0) | +10.1 (9.6)* | +9.2 (9.5) | +0.9 (9.3) | +4.1 (14.0) |

**off: ER P6+K6 f=1.0, locks at planned R, int lots** (vs unlocked as-is)

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K6 | +4.8 (5.7) | +1.4 (5.5) | +1.1 (4.9) | -0.4 (2.6) | +0.3 (2.5) |
| P6 | +1.7 (18.9) | +4.4 (12.4) | +3.9 (11.1) | -1.7 (8.1) | +5.2 (10.9) |
| U6 | +1.0 (2.0) | +1.5 (1.7) | +1.6 (1.6) | -0.1 (0.4) | -0.2 (0.5) |
| H6 | +0.3 (3.5) | -0.1 (2.1) | -0.1 (1.9) | -0.5 (1.6) | +0.4 (2.1) |
| M6 | +0.5 (1.3) | +0.5 (1.3) | +0.4 (1.1) | +0.2 (0.8) | +0.1 (0.6) |
| A6 | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* | +0.0 (0.0)* |
| sum | +8.3 (18.6) | +7.6 (12.9) | +6.9 (11.8) | -2.6 (9.5) | +5.8 (12.5) |

**12R: ER P6+K6 f=0.03, feeds running max, fractional lots** (vs unlocked as-is)

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K6 | -0.7 (4.8) | -2.0 (3.6) | -0.7 (3.6) | -1.9 (2.5) | -0.2 (2.2) |
| P6 | -2.9 (13.4) | -2.2 (8.1) | -2.0 (7.6) | -1.7 (6.7) | +0.4 (6.4) |
| U6 | +1.6 (5.0) | +1.1 (3.4) | +0.6 (3.2) | -1.6 (2.7) | -0.7 (1.5) |
| H6 | -1.8 (7.4) | -1.6 (4.2) | -0.9 (3.9) | -1.7 (2.8) | -0.1 (2.6) |
| M6 | -0.3 (2.5) | -0.8 (2.2) | -0.3 (2.3) | -1.1 (1.5) | -0.6 (1.5) |
| A6 | -0.3 (1.2) | -0.1 (0.7) | -0.0 (0.6) | -0.4 (0.6) | -0.1 (0.4) |
| sum | -4.3 (25.7) | -5.7 (15.4) | -3.3 (14.4) | -8.3 (10.8) | -1.4 (8.8) |

**12R: ER P6+K6 f=0.36, feeds running max, int lots** (vs unlocked as-is)

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K6 | -1.3 (6.9) | -2.4 (4.5) | -1.3 (4.3) | -1.6 (2.8) | -0.2 (2.7) |
| P6 | -7.3 (14.6) | -3.9 (9.7) | -3.0 (8.8) | +1.1 (7.8) | +1.5 (7.6) |
| U6 | +2.2 (5.1) | +1.3 (3.7) | +1.0 (3.4) | -1.0 (2.6) | -0.6 (1.4) |
| H6 | -2.5 (7.4) | -1.8 (4.0) | -1.0 (3.7) | -1.8 (2.8) | +0.7 (2.5) |
| M6 | -0.1 (3.0) | -0.8 (2.2) | -0.2 (2.2) | -0.9 (1.6) | -0.4 (1.3) |
| A6 | -0.0 (1.6) | -0.1 (0.8) | +0.1 (0.8) | -0.2 (0.5) | -0.0 (0.4) |
| sum | -9.1 (24.8) | -7.6 (16.1) | -4.5 (15.2) | -4.4 (10.8) | +1.0 (8.8) |

**12R: ER P6+K6 f=1.0, feeds running max, int lots** (vs unlocked as-is)

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K6 | +3.5 (9.4) | -0.4 (6.1) | +0.3 (5.5) | -1.8 (3.1) | +0.3 (3.0) |
| P6 | -1.3 (17.9) | +0.9 (11.1) | +1.9 (10.2) | +0.5 (9.3) | +1.4 (11.5) |
| U6 | +1.9 (5.9) | +1.7 (3.8) | +1.4 (3.5) | -1.4 (2.5) | -0.4 (2.1) |
| H6 | -2.4 (5.8) | -0.9 (3.6) | -0.3 (3.4) | -1.9 (3.1) | +0.5 (3.3) |
| M6 | +1.6 (3.0) | +0.0 (2.3) | +0.5 (2.3) | -1.2 (1.8) | +0.1 (1.6) |
| A6 | +0.2 (1.4) | +0.3 (0.8) | +0.4 (0.8) | -0.4 (0.6) | -0.1 (0.6) |
| sum | +3.6 (23.1) | +1.7 (14.8) | +4.3 (14.1) | -6.2 (12.4) | +1.8 (12.7) |

**12R: ER P6+K6 f=1.0, locks at planned R, int lots** (vs unlocked as-is)

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K6 | +3.1 (6.4) | -1.0 (4.8) | -0.3 (4.5) | -1.7 (2.8) | +0.9 (3.1) |
| P6 | -10.7 (20.9) | -4.1 (14.5) | -3.1 (12.9) | -5.9 (9.7) | +3.0 (10.0) |
| U6 | +1.3 (3.1) | +0.1 (3.5) | -0.1 (3.3) | -1.3 (2.6) | -0.4 (2.0) |
| H6 | -6.4 (11.2) | -4.3 (6.0) | -3.2 (5.6) | -1.9 (3.0) | +0.3 (3.0) |
| M6 | +1.0 (2.9) | -0.4 (2.4) | +0.2 (2.3) | -0.6 (1.5) | -0.2 (1.7) |
| A6 | -0.5 (0.8) | -0.4 (0.6) | -0.3 (0.6) | -0.4 (0.6) | -0.1 (0.4) |
| sum | -12.2 (30.5) | -10.1 (20.4) | -6.9 (18.6) | -11.8 (13.2) | +3.6 (12.2) |

## Table 9 - combined-lock fires (weeks fired / weeks in window; day arm ON)

| lock | row | L3M | L6M | HOLD | PRE | X' | all 149 |
|---|---|---|---|---|---|---|---|
| 12R | as-is | 7/14 | 12/28 | 15/32 | 34/75 | 23/44 | 72 |
| 12R | ON set (no ER; f=0) | 5/14 | 9/28 | 12/32 | 32/75 | 21/44 | 65 |
| 12R | ER P6+K6 f=0.03, feeds running max, int lots | 5/14 | 9/28 | 12/32 | 31/75 | 21/44 | 64 |
| 12R | ER P6+K6 f=0.03, feeds running max, fractional lots | 4/14 | 8/28 | 11/32 | 32/75 | 21/44 | 64 |
| 12R | ER P6+K6 f=0.03, locks at planned R, fractional lots | 5/14 | 9/28 | 12/32 | 31/75 | 21/44 | 64 |
| 12R | ER P6+K6 f=0.36, feeds running max, int lots | 6/14 | 10/28 | 13/32 | 35/75 | 22/44 | 70 |
| 12R | ER P6+K6 f=1.0, feeds running max, int lots | 7/14 | 12/28 | 15/32 | 43/75 | 29/44 | 87 |
| 12R | ER P6+K6 f=1.0, locks at planned R, int lots | 6/14 | 12/28 | 15/32 | 37/75 | 23/44 | 75 |
| 20R | as-is | 1/14 | 3/28 | 5/32 | 19/75 | 11/44 | 35 |
| 20R | ON set (no ER; f=0) | 2/14 | 4/28 | 6/32 | 18/75 | 9/44 | 33 |
| 20R | ER P6+K6 f=0.03, feeds running max, int lots | 2/14 | 3/28 | 5/32 | 18/75 | 9/44 | 32 |
| 20R | ER P6+K6 f=0.03, feeds running max, fractional lots | 2/14 | 3/28 | 5/32 | 18/75 | 9/44 | 32 |
| 20R | ER P6+K6 f=0.03, locks at planned R, fractional lots | 2/14 | 4/28 | 6/32 | 18/75 | 9/44 | 33 |
| 20R | ER P6+K6 f=0.36, feeds running max, int lots | 1/14 | 2/28 | 4/32 | 23/75 | 11/44 | 38 |
| 20R | ER P6+K6 f=1.0, feeds running max, int lots | 5/14 | 8/28 | 11/32 | 32/75 | 21/44 | 64 |
| 20R | ER P6+K6 f=1.0, locks at planned R, int lots | 2/14 | 4/28 | 6/32 | 19/75 | 12/44 | 37 |
| 30R | as-is | 1/14 | 1/28 | 2/32 | 9/75 | 1/44 | 12 |
| 30R | ON set (no ER; f=0) | 0/14 | 0/28 | 1/32 | 5/75 | 0/44 | 6 |
| 30R | ER P6+K6 f=0.03, feeds running max, int lots | 0/14 | 0/28 | 1/32 | 5/75 | 0/44 | 6 |
| 30R | ER P6+K6 f=0.03, feeds running max, fractional lots | 1/14 | 1/28 | 1/32 | 5/75 | 0/44 | 6 |
| 30R | ER P6+K6 f=0.03, locks at planned R, fractional lots | 0/14 | 0/28 | 1/32 | 5/75 | 0/44 | 6 |
| 30R | ER P6+K6 f=0.36, feeds running max, int lots | 0/14 | 0/28 | 1/32 | 11/75 | 3/44 | 15 |
| 30R | ER P6+K6 f=1.0, feeds running max, int lots | 2/14 | 3/28 | 5/32 | 24/75 | 13/44 | 42 |
| 30R | ER P6+K6 f=1.0, locks at planned R, int lots | 1/14 | 1/28 | 2/32 | 9/75 | 5/44 | 16 |
