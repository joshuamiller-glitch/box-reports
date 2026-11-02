# DS3_ZONES_3_ZL1_SUMMARY - ZL-1 program summary (order-book, liquidity-pool, profile-level and flip streams), written 2026-11-02 for the 18:00Z refresh
Base for every final label: D7 V13Y (v1.3 EXACT + the add-fill fix), new windows, lock=None headline (lock=12R beside it where stated). Everything post-hoc, Shadow only, no PASS claim. Earlier V13X/assumed-base numbers are superseded; where a label changed it says so.
Scale: 213 POI-format streams built on the 1-s L2 table / path (2023-02..2026-10-30, new cap), 818 distinct cells appended to DEAD_CELLS (program ZL1) plus about 400 unappended screens, placebo runs, definition grids and variants (144-config plateau, 29-variant definition map, 16 flip families, 10 size-up cells): about 1,100 scored cells in all. n used for best-of-N: 834 (818 + 16 flip families) before the size-up family.

| family | streams / events | what was tested | V13Y result | FINAL LABEL |
|--|--|--|--|--|
| ABS absorption (gate k5N10 and 9 grid points) | 30 streams; gate def 0.3 events/day, k1N10 6.8/day | AHEAD/BEHIND/AT, D 10-60, skip/half, descriptive reaction | descriptive reaction at chance (best k2N10 0.504 vs 0.478, one of many); cells cut < 2% | DEAD |
| ICE iceberg (>= 2 refills at a price) | 12 streams; events fell 10x from 2023-24 to 2026 | same | no cut in any window | DEAD |
| DEF book-defended walls | 18 streams | same | react worse than random levels (rank .98-1.0); no cut | DEAD |
| PUL pulled walls (k2/k3/k4/k5) | 12+ streams; events rose 5x | k3 4h D20 skip was the only V13X lead (PRE/X' only, LOCK-ONLY L6M) | V13Y: lock12 L3M -8 L6M +1 PRE +6; lock None L6M -6 MID -27 PRE -6; no parameter plateau (k2 harmful, k4 L6M-only) | DEAD (V13X LEAD(weak) withdrawn) |
| SWP sweep-and-reclaim levels and extremes (prior-day, session, swing) | 36 streams | same, plus failed-breakdown view | stop-extremes react worse than random; swing D60 candidate (assumed base) flips on V13X | DEAD |
| LQP unswept liquidity (swing/equal H/L 15m-4h) | 13 streams, 31,214 levels | same incl. sweep-then-reverse size-up | best min(L6M,PRE,X') 8% | DEAD |
| NPD naked prior-day POC/VAH/VAL (tape, 1/2 pt) | 6 streams, 926 levels each | same, both lock frames | L6M 0-4%, PRE <= 5% | DEAD |
| RXL reaction levels (density bands, composite HVN/LVN) | 8 streams | same | volume effects; LVN-20d half D40 lock-dependent (X' -32% with 12R, MID -12%) | DEAD / VOLUME (FRAGILE) |
| Mancini failed breakdown / back-test | S4b's 24 streams (cited) + my SWP/BT views | same | S median +0.01, best +0.20 | DEAD |
| L2 zone confirms a price line | PUL/SWP/ICE/DEF x 8 coded lines | confirm-skip, undo-HALF on unconfirmed lines | confirm-skip ~0; undoing the HALF is 12-40% worse | DEAD |
| LNC/OPN2/PWM/VWB (lunch, opens, prior week/month, VWAP bands) | 24 streams built | scored by Z1 (none a lead); my flip view below | see flip families | DEAD (Z1) |
| Flip families (16 other level families, prereg 607cc2e6...) | day/session/week/month levels, round 50, shipped lines, VWAP, equal H/L | skip when a fresh flip level lies ahead | none passes; shipped 8 lines -61k, VWAP Asia -149k, VWAP London -118k are negative | DEAD |
| Size-up of the winner families (prereg 25827761...) | 10 cells | x1.5 lots / restore full lots | gains positive but placebo ranks 0.04-0.7, per-year signs flip | VOLUME / DEAD |
| **BT swing flip (5-min fractal swing broken by >= 10 pts, 4 h, ahead within 40 pts)** | 18 BT + 36 BTC streams; 26.5 flagged taken trades/month | row-level saved dollars, placebos, null, walk-forward, exits, variants, phases | see below | **LEAD, mean-type (not a drawdown cut), not RISK-KEEP** |

## BT swing flip on V13Y (lock None, row-level saved $k = minus the flagged taken trades' net; details autopilot/DS3_BT_SWING_FLIP_CANDIDATE.md, DS3_ZONES_3_B5_MANCINI.md)
* Flagged taken trades lose money: HOLD -$209 per trade vs +$182 for the rest (hit 37-40% vs 47%). Saved dollars: L3M +30, L6M +70, HOLD +75, MID +18, PRE +103, X' +50; 200-draw row placebo ranks L6M .005-.025, HOLD .005-.035, PRE .03-.08, X' .055-.27, MID .20.
* Per year 2023 +57, 2024 +29, 2025 +28, 2026 +89 (4/4); quarters 11/14. Best-of-N null: beats all 1,980 same-density null families on min(L6M,HOLD,PRE,X') (50k vs null max 17k; lock 12R 66k vs 15k).
* Walk-forward 2024-01..2026-10 (definition chosen on trailing months): +54k (12 m) / +51k (6 m) vs random config +33k / +21k; lock12R +134k / +180k.
* Exit-set robustness: the edge persists and grows without the TH-L2 loss cut / take lines (L6M +169k, HOLD +197k), and across take thresholds x0.5..x1.5: a property of the zone; the live exits dilute it.
* Definition map: 5-min plateau 3-10 min (1m $55/trade, 1h dead); both sides carry (longs 130k, shorts 70k); a bar close works as well as a print; waiting for a retest kills it; 4 h validity is an optimum; no freshness limit works as well; reach 40-60.
* NOT a drawdown cut: phase-averaged maxDD cut +12% L3M, +25% MID but -10% L6M, -10% HOLD, +3% PRE, -11% X'; the engine dollars are positive in 5/5 lock phases (lock None).
* Caveats: 86% of flagged trades exit early (552 of 584 losers before the library stop); effect absent over 2023-04..07 (before the L2-based events; -15.9k on 69 trades); 2025 weak; PRE/X' ranks not significant; 40% of candidate rows already in the shipped zone layer (BT minus layer saves 66k L6M); overlap with large prints 10%.
* Forward: Shadow spec and CSV in FORWARD_SHADOW_ZONES_SPEC.md; check script l2vast/ds3/code/zones3/bt_forward_check.py (13/26-week read, SPRT); clock from 2026-11-02.
* Open: S4b clean-room reproduction of the mask (definition pinning in progress), V13Y noise band for the maxDD columns.
