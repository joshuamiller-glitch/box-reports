# D7 V13Z BASE: V13Y (add-fill ordering fixed) + basis-N consistent take deltas (nfix default) - BASE-4, 2026-11-02T11:07Z

**Call:** `import sys; sys.path.insert(0,"l2vast/ds3/code/d7base"); import d7_v13z as V13Z; r = V13Z.run_v13z(ov=None, lock=12|None)`; `ov={"nfix":False}` = V13Y exactly (the M-basis / "live targets really suffer the measured 3.4-pt fill shortfall" scenario; tie-out max|cube diff| 0.0018 $ at lock none and 0.0018 $ at 12R = float32 storage noise); `ov={"b73fix":False}` = V13X. All V13X ov keys unchanged (grid "1sh" = 1-s lines, lines, u7x, extra_skip, lscale...). Scripts that `import use_z` run unmodified code as V13Z. Episodes lookup: DS3_ZONES_EPISODES_V13Y.md (loss cuts only differ by the profit-side basis; re-run code/d7base/episodes.py for the V13Z cubes).

**What nfix changes:** the engine baseline is basis N (target exits carry no limit-fill cost; live: touched targets fill at nominal, T-MISSED 11/11). The take/tighten deltas were measured against pts_lib - fill_cost_pts, crediting every early market exit on a trade that would have hit the target with fill_cost_pts (mean 3.39 pts/lot, 1.0 on stops). nfix subtracts it on target-exit rows. The TH-L2 loss-cut deltas are exit-price differences and unchanged.

## LOCK NONE (headline): mean $k/wk (MDE) / maxDD $k

| row | F9 | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|
| 10-s profit side OFF / V13Z (basis N) | 33.7 (28.6) / DD 132.1 | 12.7 (94.8) / DD 97.7 | 23.4 (65.9) / DD 97.7 | 15.5 (45.8) / DD 97.7 | 37.1 (37.9) / DD 132.1 | 31.2 (23.5) / DD 139.2 | 23.3 (33.0) / DD 51.2 | 17.1 (14.8) / DD 166.3 | 4.7 (12.3) / DD 91.2 |
| 10-s profit side OFF / V13Y (basis M) | 33.7 (28.6) / DD 132.1 | 12.7 (94.8) / DD 97.7 | 23.4 (65.9) / DD 97.7 | 15.5 (45.8) / DD 97.7 | 37.1 (37.9) / DD 132.1 | 31.2 (23.5) / DD 139.2 | 23.3 (33.0) / DD 51.2 | 17.1 (14.8) / DD 166.3 | 4.7 (12.3) / DD 91.2 |
| 10-s five lines ON / V13Z (basis N) | 14.6 (20.6) / DD 182.8 | 11.0 (51.3) / DD 37.6 | 16.6 (39.6) / DD 37.6 | 9.4 (29.9) / DD 51.8 | 16.8 (26.3) / DD 182.8 | 14.9 (18.4) / DD 182.8 | 8.5 (29.1) / DD 50.6 | 8.4 (12.2) / DD 172.9 | 1.2 (10.0) / DD 88.5 |
| 10-s five lines ON / V13Y (basis M) | 25.6 (21.8) / DD 96.2 | 21.4 (53.8) / DD 27.3 | 27.6 (40.8) / DD 27.3 | 19.7 (30.8) / DD 31.1 | 28.8 (27.7) / DD 96.2 | 24.6 (19.2) / DD 103.0 | 16.4 (31.3) / DD 30.2 | 12.1 (12.5) / DD 129.7 | 1.6 (10.3) / DD 69.7 |
| 1-s five lines ON / V13Z (basis N) | 12.1 (21.1) / DD 174.1 | 6.7 (47.0) / DD 37.5 | 12.7 (38.7) / DD 37.5 | 4.8 (30.7) / DD 85.1 | 17.1 (24.8) / DD 174.1 | 11.1 (18.3) / DD 185.9 | -0.2 (36.3) / DD 112.4 | 5.9 (11.7) / DD 223.7 | 2.6 (9.1) / DD 81.7 |
| 1-s five lines ON / V13Y (basis M) | 24.7 (21.7) / DD 80.2 | 18.7 (51.1) / DD 26.5 | 25.0 (40.3) / DD 26.5 | 16.4 (31.6) / DD 53.5 | 30.8 (26.1) / DD 80.2 | 23.1 (18.8) / DD 134.9 | 8.9 (34.6) / DD 63.7 | 10.8 (11.9) / DD 149.5 | 3.6 (9.4) / DD 73.4 |

Five lines ON vs OFF: maxDD CUT (positive = shallower) / d mean $k/wk (MDE):
| grid / base | F9 | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|
| 10-s / V13Z (N) | -38% / -19.1(14.0) | +62% / -1.8(56.2) | +62% / -6.8(35.5) | +47% / -6.1(24.8) | -38% / -20.3(19.0) | -31% / -16.3(11.5) | +1% / -14.8(13.5) | -4% / -8.7(7.5) | +3% / -3.5(7.9) |
| 10-s / V13Y (M) | +27% / -8.1(13.2) | +72% / +8.6(56.1) | +72% / +4.1(33.6) | +68% / +4.2(23.4) | +27% / -8.4(17.9) | +26% / -6.6(10.9) | +41% / -6.9(12.6) | +22% / -5.0(7.4) | +24% / -3.1(8.5) |
| 1-s / V13Z (N) | -32% / -21.7(17.0) | +62% / -6.0(61.9) | +62% / -10.8(40.0) | +13% / -10.7(29.0) | -32% / -20.0(22.2) | -34% / -20.1(13.4) | -120% / -23.5(22.3) | -35% / -11.2(8.0) | +10% / -2.1(7.4) |
| 1-s / V13Y (M) | +39% / -9.0(16.6) | +73% / +5.9(60.6) | +73% / +1.6(37.1) | +45% / +0.9(27.1) | +39% / -6.3(21.6) | +3% / -8.1(13.0) | -24% / -14.4(20.6) | +10% / -6.3(8.0) | +20% / -1.1(7.9) |

## 12R combined lock: mean $k/wk (MDE) / maxDD $k

| row | F9 | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|
| 10-s profit side OFF / V13Z (basis N) | 26.8 (26.8) / DD 150.2 | 20.7 (61.1) / DD 26.3 | 21.8 (51.7) / DD 63.3 | 14.9 (35.7) / DD 65.7 | 29.2 (34.9) / DD 150.2 | 24.5 (21.6) / DD 150.2 | 19.0 (34.8) / DD 43.8 | 8.9 (12.7) / DD 132.4 | -4.6 (7.5) / DD 233.9 |
| 10-s profit side OFF / V13Y (basis M) | 26.8 (26.8) / DD 150.2 | 20.7 (61.1) / DD 26.3 | 21.8 (51.7) / DD 63.3 | 14.9 (35.7) / DD 65.7 | 29.2 (34.9) / DD 150.2 | 24.5 (21.6) / DD 150.2 | 19.0 (34.8) / DD 43.8 | 8.9 (12.7) / DD 132.4 | -4.6 (7.5) / DD 233.9 |
| 10-s five lines ON / V13Z (basis N) | 9.3 (18.4) / DD 117.1 | 3.2 (37.4) / DD 25.2 | 11.7 (36.2) / DD 30.1 | 6.4 (26.2) / DD 51.7 | 12.7 (22.9) / DD 117.1 | 10.2 (16.1) / DD 122.1 | 0.8 (27.9) / DD 70.3 | 3.0 (11.2) / DD 362.9 | -2.5 (7.9) / DD 139.0 |
| 10-s five lines ON / V13Y (basis M) | 17.2 (20.8) / DD 52.8 | 9.9 (43.5) / DD 22.2 | 20.1 (39.4) / DD 22.2 | 13.8 (28.9) / DD 26.5 | 21.2 (25.8) / DD 52.8 | 16.4 (18.0) / DD 90.4 | 6.7 (31.4) / DD 52.3 | 5.9 (11.9) / DD 282.2 | -1.1 (8.2) / DD 131.5 |
| 1-s five lines ON / V13Z (basis N) | 10.5 (18.8) / DD 145.8 | 12.5 (38.4) / DD 19.3 | 12.6 (37.2) / DD 52.5 | 6.2 (27.1) / DD 84.8 | 16.0 (22.2) / DD 145.8 | 9.8 (15.6) / DD 145.8 | -2.5 (31.3) / DD 97.0 | 1.6 (9.9) / DD 353.4 | -1.1 (7.8) / DD 110.6 |
| 1-s five lines ON / V13Y (basis M) | 19.4 (20.9) / DD 80.5 | 18.7 (51.1) / DD 26.5 | 21.3 (42.3) / DD 42.2 | 14.1 (30.8) / DD 53.8 | 25.8 (25.3) / DD 80.5 | 17.4 (17.6) / DD 125.3 | 3.2 (31.7) / DD 72.4 | 4.0 (10.8) / DD 308.9 | -0.7 (8.2) / DD 113.3 |

Five lines ON vs OFF: maxDD CUT (positive = shallower) / d mean $k/wk (MDE):
| grid / base | F9 | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|
| 10-s / V13Z (N) | +22% / -17.5(15.1) | +4% / -17.5(57.1) | +52% / -10.1(41.0) | +21% / -8.5(28.0) | +22% / -16.6(20.2) | +19% / -14.2(11.5) | -60% / -18.2(17.1) | -174% / -5.9(9.2) | +41% / +2.1(7.2) |
| 10-s / V13Y (M) | +65% / -9.6(15.3) | +16% / -10.8(60.9) | +65% / -1.7(42.5) | +60% / -1.1(28.9) | +65% / -8.0(20.3) | +40% / -8.1(11.6) | -19% / -12.4(17.5) | -113% / -3.0(8.7) | +44% / +3.4(7.4) |
| 1-s / V13Z (N) | +3% / -16.3(14.7) | +27% / -8.3(23.6) | +17% / -9.2(27.7) | -29% / -8.7(20.2) | +3% / -13.3(18.4) | +3% / -14.7(11.1) | -121% / -21.6(23.4) | -167% / -7.2(8.6) | +53% / +3.4(7.4) |
| 1-s / V13Y (M) | +46% / -7.4(14.6) | -1% / -2.1(17.0) | +33% / -0.5(25.6) | +18% / -0.8(18.8) | +46% / -3.4(18.2) | +17% / -7.1(10.9) | -65% / -15.8(21.1) | -133% / -4.9(8.7) | +52% / +3.8(7.6) |
