# ZONES3_MASTER_TABLE - program-wide finalist x frame x noise band x placebo rank x carrying week x label (S5 light-job agent)
Refreshed 2026-11-06 23:21Z. CSV: autopilot/ZONES3_MASTER_TABLE.csv (1212 rows). TRUTH BASE (user answers 2026-11-02): V13T = V13Z with the five take lines OFF, lock none = live per-book lock stack; combined 12R = reference only (rows labelled 'reference, not live'); S5 V13T rows are computed by S5 as V13Z run with lines='empty' (relabel when BASE-4 publishes d7_v13t.py). BASE COLUMN: V13X = DEFECT BASE (add-fill ordering defect, BASE-4), V13Y = fixed base; only S5 rows exist on V13Y so far (others republish). Bases: V13X exact (S5, Z3 s3_v13x), ZL3 lock-off V13X, S4A stage2x_vx (v13_=lock12, nl_=lock-off) and stage2xn_vxn (v13_=lock-off headline, nl_=lock12), mapping CONFIRMED by S4a; S4A pA/pB/pC rank the mean of the L6M/HOLD/PRE/X cuts, not L6M alone, 40 draws. Band: V13X rows = Z3 V13X noise band (interim n~43); V13Y rows = Z3 V13Y SINGLE-PATH (phase 0) band from DS3_ZONES_3_NOISE.md (our cuts are single-path; the phase-averaged band, lock-off flip2/5 L6M 15.5/20 PRE 11.5/16 X' 14/22, applies only to phase-averaged cuts, which only Z3 computes), row by rows changed (S5 from flagged share; others: Z3 1,500 rows -> flip 2/5; S4A/ZL3 use rows/flags as stored x0.3 for live share, flip 5 when unknown); rule: cut > band in L6M AND (PRE or X'). Placebo ranks: S5 from its stored draws (rank = share of draws with cut >= real, 100/kind lock12 for 9 cells, lock-off for 5), S4A from its pA/pB/pC (see above); Z3 and ZL3 tables carry no placebo ranks (labelled 'BAND (placebo not in table)'). Carrying week: S5 only. Labels are mechanical; nothing is a lead without the robustness standard.

## Counts by program and frame

|                                                              |   cells |   band_pass |   volume |   band_placebo |
|:-------------------------------------------------------------|--------:|------------:|---------:|---------------:|
| ('V13T (HEADLINE: V13Z, take OFF)', 'S5 density', 'lock12')  |      33 |           0 |        0 |              0 |
| ('V13T (HEADLINE: V13Z, take OFF)', 'S5 density', 'lockoff') |      33 |           1 |        0 |              1 |
| ('V13X (DEFECT BASE)', 'S4A streams', 'lock12')              |      48 |           2 |        0 |              0 |
| ('V13X (DEFECT BASE)', 'S4A streams', 'lockoff')             |      48 |          12 |        0 |              0 |
| ('V13X (DEFECT BASE)', 'S5 density', 'lock12')               |      34 |           0 |        0 |              0 |
| ('V13X (DEFECT BASE)', 'S5 density', 'lockoff')              |      34 |           5 |        0 |              0 |
| ('V13X (DEFECT BASE)', 'Z3 action table', 'lock12')          |     101 |           0 |        0 |              0 |
| ('V13X (DEFECT BASE)', 'Z3 action table', 'lockoff')         |     101 |           0 |        0 |              0 |
| ('V13X (DEFECT BASE)', 'ZL3 L2/tape zones', 'lockoff')       |     418 |          56 |        0 |              0 |
| ('V13Y', 'S4A streams', 'lock12')                            |      24 |           0 |        0 |              0 |
| ('V13Y', 'S4A streams', 'lockoff')                           |      24 |           2 |        0 |              0 |
| ('V13Y', 'S5 density', 'lock12')                             |      33 |           0 |        0 |              0 |
| ('V13Y', 'S5 density', 'lockoff')                            |      33 |           4 |        4 |              0 |
| ('V13Y', 'Z3 action table', 'lock12')                        |      91 |           0 |        0 |              0 |
| ('V13Y', 'Z3 action table', 'lockoff')                       |      91 |           0 |        0 |              0 |
| ('V13Z (V13Y+nfix)', 'S5 density', 'lock12')                 |      33 |           0 |        0 |              0 |
| ('V13Z (V13Y+nfix)', 'S5 density', 'lockoff')                |      33 |           3 |        3 |              0 |


## Every row that passes the band in a frame (necessary, not sufficient)

| base | program | cell | frame | L6M | HOLD | PRE | X' | mean d L6M (MDE) | band L6M/PRE/X' | placebo B/C/A | carrying week | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V13T (HEADLINE: V13Z, take OFF) | S5 density | open20 half | lockoff | +56% | +38% | +41% | +15% | -18.3k (20.8k) | 27/17/22% | 0.06/0.05/0.05 | 202630 | BAND+PLACEBO |
| V13X (DEFECT BASE) | S4A streams | DEV|day_L|so_far D40 half | lock12 | +50% | +30% | -46% | +34% | n/a | 36/28/29% | n/a/n/a/n/a |  | [reference, not live] [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | S4A streams | ARR|iplFVG|15s D20 skip | lock12 | +36% | +48% | +9% | +32% | n/a | 36/28/29% | 1.00/1.00/1.00 |  | [reference, not live] [defect base] VOLUME |
| V13X (DEFECT BASE) | S4A streams | DEV|day_L|so_far D40 half | lockoff | +69% | +12% | -43% | +33% | n/a | 21/20/29% | 1.00/1.00/1.00 |  | [defect base] VOLUME [src:(L6M/recent only)] |
| V13X (DEFECT BASE) | S4A streams | DEV|on_L|so_far D40 half | lockoff | +67% | +17% | -38% | +40% | n/a | 21/20/29% | 1.00/1.00/1.00 |  | [defect base] VOLUME [src:(L6M/recent only)] |
| V13X (DEFECT BASE) | S4A streams | DEV|on_L|so_far D20 half | lockoff | +64% | +23% | -21% | +32% | n/a | 21/20/29% | 0.01/0.01/0.01 |  | [defect base] BAND+PLACEBO [src:(L6M/recent only)] |
| V13X (DEFECT BASE) | S4A streams | SWG|f3L|15s D20 half | lockoff | +54% | +8% | -51% | +33% | n/a | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | S4A streams | SWG|f3L|15s D40 half | lockoff | +45% | +31% | +6% | +41% | n/a | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | S4A streams | SWG|f3L|15s D40 half | lockoff | +45% | +31% | +6% | +41% | n/a | 21/20/29% | 0.01/0.04/0.01 |  | [defect base] BAND+PLACEBO |
| V13X (DEFECT BASE) | S4A streams | ARR|iplFVG|15s D40 half | lockoff | +31% | +25% | -23% | +34% | n/a | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | S4A streams | ARR|iplFVG|15s D40 half | lockoff | +31% | +25% | -23% | +34% | n/a | 21/20/29% | 0.07/0.24/0.07 |  | [defect base] VOLUME [src:(L6M/recent only)] |
| V13X (DEFECT BASE) | S4A streams | ARR|iplFVG|15s D20 half | lockoff | +30% | +6% | -24% | +38% | n/a | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | S4A streams | ARR|iplFVG|15s D20 half | lockoff | +30% | +6% | -24% | +38% | n/a | 21/20/29% | 1.00/1.00/1.00 |  | [defect base] VOLUME [src:FRAGILE] |
| V13X (DEFECT BASE) | S4A streams | FIB|ret50|1h D40 skip | lockoff | +23% | +23% | -13% | +31% | n/a | 21/20/29% | 1.00/1.00/1.00 |  | [defect base] VOLUME [src:(L6M/recent only)] |
| V13X (DEFECT BASE) | S4A streams | MAS|bb_mid|4h D20 skip | lockoff | +12% | +7% | +7% | +11% | n/a | 10/14/8% | 0.04/0.03/0.03 |  | [defect base] BAND+PLACEBO |
| V13X (DEFECT BASE) | S5 density | sopen40 half | lockoff | +51% | +44% | +22% | +11% | -6.9k (14.0k) | 21/20/29% | 0.09/0.07/0.11 | 202630 | [defect base] VOLUME |
| V13X (DEFECT BASE) | S5 density | open20 half | lockoff | +47% | +47% | +26% | +1% | -12.3k (15.6k) | 21/20/29% | 0.29/0.23/0.23 | 202630 | [defect base] VOLUME |
| V13X (DEFECT BASE) | S5 density | nA60>=1 skip | lockoff | +38% | +27% | -6% | +31% | -7.2k (14.5k) | 21/20/29% | 0.23/0.30/0.35 | 202630 | [defect base] VOLUME |
| V13X (DEFECT BASE) | S5 density | openA40 half | lockoff | +37% | +37% | +36% | +30% | -8.9k (14.0k) | 21/20/29% | 0.52/0.41/0.39 | 202630 | [defect base] VOLUME |
| V13X (DEFECT BASE) | S5 density | rho60>=2 skip | lockoff | +34% | +15% | +9% | +32% | -1.1k (13.2k) | 21/20/29% | 0.23/0.35/0.23 | 202630 | [defect base] VOLUME |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | act=skip|fam=SET8|kind=DENS|rule=near_ge:40|lat0 | lockoff | +70% | +13% | +5% | +48% | -18.2k (26.8k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf3|rule=pol2040|lat0 | lockoff | +67% | +19% | +10% | +64% | -18.9k (22.5k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf18|rule=pol2040|lat0 | lockoff | +66% | +35% | +42% | +53% | -20.3k (23.3k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=exp|rule=skip30|lat0 | lockoff | +62% | +62% | +52% | +51% | -17.8k (20.2k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf29|rule=pol2040|lat0 | lockoff | +61% | +42% | +19% | +50% | -20.4k (22.5k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | act=half|fam=TAPEALL|kind=DENS|rule=nah20:2|lat0 | lockoff | +60% | +36% | +26% | -19% | -1.5k (10.0k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf1|rule=pol2040|lat0 | lockoff | +55% | +32% | -35% | +47% | -21.4k (22.3k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf15|rule=pol2040|lat0 | lockoff | +54% | +3% | -13% | +31% | -19.2k (21.8k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf27|rule=pol2040|lat0 | lockoff | +54% | +49% | +53% | +58% | -22.9k (22.7k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf7|rule=pol2040|lat0 | lockoff | +53% | +37% | -16% | +65% | -20.6k (22.7k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf18|rule=skip20|lat0 | lockoff | +52% | -2% | +20% | +35% | -17.5k (23.3k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf21|rule=pol2040|lat0 | lockoff | +52% | +45% | +21% | +33% | -23.6k (22.1k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf8|rule=pol2040|lat0 | lockoff | +51% | +29% | +11% | +53% | -22.8k (22.0k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf3|rule=skip20|lat0 | lockoff | +51% | +20% | +6% | +56% | -16.9k (20.0k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | Dl=60|conf=skip|fam=TVP|kind=CONF|line=SET|tier=all|tol=10|weak=half|lat0 | lockoff | +49% | +28% | -5% | +36% | -3.6k (10.5k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | Dl=60|conf=skip|fam=TVP|kind=CONF|line=SET|tier=all|weak=half|lat1 | lockoff | +48% | +31% | -4% | +31% | -3.8k (10.3k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | Dl=60|conf=skip|fam=TVP|kind=CONF|line=SET|tier=all|weak=half|lat3 | lockoff | +48% | +31% | -4% | +31% | -3.8k (10.3k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | Dl=60|conf=skip|fam=TVP|kind=CONF|line=SET|tier=all|weak=half|lat0 | lockoff | +47% | +31% | -4% | +32% | -3.8k (10.3k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | Dl=75|conf=skip|fam=TVP|kind=CONF|line=SET|tier=all|weak=half|lat0 | lockoff | +47% | +31% | -4% | +32% | -3.8k (10.3k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | Dl=90|conf=skip|fam=TVP|kind=CONF|line=SET|tier=all|weak=half|lat0 | lockoff | +47% | +31% | -4% | +32% | -3.8k (10.3k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | Dl=60|conf=skip|fam=TVP|kind=CONF|line=SET|tier=all|tol=7.5|weak=half|lat0 | lockoff | +47% | +28% | -4% | +35% | -4.2k (10.5k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf2|rule=pol2040|lat0 | lockoff | +47% | +45% | +30% | +57% | -22.5k (21.4k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=roll|rule=skip30|lat0 | lockoff | +46% | +40% | +36% | +32% | -17.6k (21.8k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf19|rule=pol2040|lat0 | lockoff | +46% | +36% | +5% | +32% | -21.1k (23.9k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf16|rule=pol2040|lat0 | lockoff | +45% | +41% | +33% | +61% | -20.8k (22.1k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf26|rule=pol2040|lat0 | lockoff | +45% | -10% | +12% | +52% | -21.2k (21.8k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | Dl=60|conf=skip|fam=TVP|kind=CONF|line=SET|sess=asia|tier=all|weak=half|lat0 | lockoff | +45% | +31% | -1% | +32% | -1.9k (8.8k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf9|rule=pol2040|lat0 | lockoff | +45% | +22% | +18% | +34% | -21.2k (22.0k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf29|rule=skip20|lat0 | lockoff | +44% | +13% | +5% | +36% | -18.5k (23.2k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf23|rule=pol2040|lat0 | lockoff | +43% | +43% | +27% | +63% | -22.6k (21.0k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | act=half|fam=SET8+L2ALL|kind=DENS|rule=nah20:2|lat0 | lockoff | +43% | +39% | +35% | -22% | -3.9k (10.3k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf16|rule=skip20|lat0 | lockoff | +43% | +42% | +3% | +56% | -17.7k (20.9k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf13|rule=pol2040|lat0 | lockoff | +42% | +42% | +48% | +41% | -22.3k (22.4k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=roll|rule=pol2040|lat0 | lockoff | +42% | +32% | +39% | +53% | -19.6k (20.6k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | Dl=60|conf=skip|fam=TAPEALL|kind=CONF|line=SET|tier=all|weak=half|lat0 | lockoff | +38% | +25% | +4% | +38% | -5.7k (10.9k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | act=skip|fam=TAPEALL|kind=DENS|rule=nah40:1|lat0 | lockoff | +37% | +34% | +37% | +35% | -16.2k (25.2k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | act=half|fam=SET8|kind=DENS|rule=near_ge:40|lat0 | lockoff | +37% | +37% | +36% | +30% | -8.9k (14.0k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | act=skip|fam=TAPEALL|kind=DENS|rule=nah20:2|lat0 | lockoff | +36% | -21% | +31% | -18% | -4.9k (15.0k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf10|rule=pol2040|lat0 | lockoff | +36% | +31% | +33% | +31% | -22.6k (21.9k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf14|rule=pol2040|lat0 | lockoff | +35% | +18% | +43% | +27% | -21.7k (22.1k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf20|rule=pol2040|lat0 | lockoff | +35% | +3% | +35% | +63% | -23.7k (22.7k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | file=treewf_zm_s3.npz|kind=TWF|lat0 | lockoff | +34% | +34% | +56% | +0% | -21.2k (20.4k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf22|rule=pol2040|lat0 | lockoff | +31% | +31% | +27% | +59% | -22.9k (22.0k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | act=half|fam=SET8+L2ALL|kind=DENS|rule=ratio_ge:2|lat0 | lockoff | +30% | +30% | +6% | +29% | -2.6k (10.1k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | act=skip|fam=TAPEALL|kind=DENS|rule=nah40:2|lat0 | lockoff | +29% | +19% | +26% | -30% | -7.9k (20.7k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | Dl=60|conf=skip|fam=TVP|kind=CONF|line=SET|tier=2|weak=half|lat0 | lockoff | +28% | +28% | -5% | +31% | -4.0k (8.7k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | act=skip|fam=SET8+L2ALL|kind=DENS|rule=nah40:1|lat0 | lockoff | +28% | +28% | +39% | +43% | -21.5k (25.8k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | Dl=60|book=P7|conf=skip|fam=TVP|kind=CONF|line=SET|tier=all|weak=half|lat0 | lockoff | +28% | +28% | -11% | +35% | -4.0k (7.0k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=shuf23|rule=skip20|lat0 | lockoff | +26% | +26% | -53% | +41% | -21.2k (19.7k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | act=skip|fam=SET8+L2ALL|kind=DENS|rule=nah20:5|lat0 | lockoff | +26% | +24% | +35% | +49% | -1.6k (8.3k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | act=half|fam=TAPEALL|kind=DENS|rule=ratio_le:0.5|lat0 | lockoff | +25% | +25% | +23% | +20% | -5.6k (6.5k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=exp|rule=pol2040|lat0 | lockoff | +24% | +24% | +28% | +53% | -17.2k (16.6k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | act=half|fam=SET8+L2ALL|kind=DENS|rule=nah20:3|lat0 | lockoff | +23% | +23% | +23% | -7% | -1.4k (7.2k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | act=skip|fam=TAPEALL|kind=DENS|rule=ratio_le:0.5|lat0 | lockoff | +22% | +22% | +40% | -29% | -12.1k (16.4k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | arm=B|kind=LRN|model=exp|rule=skip20|lat0 | lockoff | +21% | +21% | +23% | +40% | -10.2k (12.6k) | 21/20/29% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13X (DEFECT BASE) | ZL3 L2/tape zones | D=20|act=skip|fam=('tape', 'TLQ_SES_asia')|kind=AH|tier=all|var=fresh|lat0 | lockoff | +11% | +5% | +13% | +12% | -0.0k (3.9k) | 10/14/8% | n/a/n/a/n/a |  | [defect base] BAND (placebo not in table) |
| V13Y | S4A streams | SWG|f3L|15s D40 half | lockoff | +44% | +12% | +5% | +29% | n/a | 27/17/22% | n/a/n/a/n/a |  | BAND (placebo not in table) |
| V13Y | S4A streams | SWG|f3L|15s D20 half | lockoff | +44% | +10% | -36% | +26% | n/a | 27/17/22% | n/a/n/a/n/a |  | BAND (placebo not in table) |
| V13Y | S5 density | open60 half | lockoff | +42% | +10% | +4% | +33% | -7.4k (13.8k) | 27/17/22% | 0.28/0.19/0.16 | 202630 | VOLUME |
| V13Y | S5 density | open20 half | lockoff | +41% | +35% | +17% | +9% | -13.2k (14.5k) | 27/17/22% | 0.46/0.38/0.34 | 202630 | VOLUME |
| V13Y | S5 density | rho60>=2 skip | lockoff | +41% | +14% | +1% | +36% | -1.1k (12.7k) | 27/17/22% | 0.15/0.20/0.10 | 202630 | VOLUME ONE-WEEK |
| V13Y | S5 density | openA40 half | lockoff | +35% | +40% | +20% | +41% | -10.4k (12.9k) | 27/17/22% | 0.53/0.38/0.47 | 202630 | VOLUME |
| V13Z (V13Y+nfix) | S5 density | open60 half | lockoff | +39% | +39% | +11% | +45% | -4.1k (12.7k) | 27/17/22% | 0.18/0.11/0.15 | 202630 | VOLUME |
| V13Z (V13Y+nfix) | S5 density | openA40 half | lockoff | +36% | +36% | +3% | +37% | -5.4k (11.7k) | 27/17/22% | 0.58/0.38/0.45 | 202630 | VOLUME |
| V13Z (V13Y+nfix) | S5 density | sA40>=1 skip | lockoff | +34% | +34% | +18% | +14% | -4.3k (14.1k) | 27/17/22% | 0.31/0.40/0.36 | 202630 | VOLUME |

## Per-family summary (band = Z3 band rule; no-harm = SHARED definition: PRE and MID cut not worse than -(flip-2% PA band) (lock-off 11.5% / 26.8%, 12R 13.3% / 26.5%); MID missing = not tested; pass_all = band + no-harm + placebo ranks <= 0.10 where placebo exists). Chance expectation = cells x 0.110, the lock-off band+no-harm pass rate of 200 information-free same-size masks measured by S5 on V13Y (proxy for every family).

| base                            | family                             | frame   |   cells |   band |   band_noharm |   placebo_tested |   pass_all |   chance_expectation_passes | final_label                                 |
|:--------------------------------|:-----------------------------------|:--------|--------:|-------:|--------------:|-----------------:|-----------:|----------------------------:|:--------------------------------------------|
| V13T (HEADLINE: V13Z, take OFF) | S5 cong                            | lock12  |      20 |      0 |             0 |                0 |          0 |                        2.2  | none                                        |
| V13T (HEADLINE: V13Z, take OFF) | S5 cong                            | lockoff |      20 |      0 |             0 |                2 |          0 |                        2.2  | none                                        |
| V13T (HEADLINE: V13Z, take OFF) | S5 nml                             | lock12  |       4 |      0 |             0 |                0 |          0 |                        0.44 | none                                        |
| V13T (HEADLINE: V13Z, take OFF) | S5 nml                             | lockoff |       4 |      0 |             0 |                0 |          0 |                        0.44 | none                                        |
| V13T (HEADLINE: V13Z, take OFF) | S5 open                            | lock12  |       4 |      0 |             0 |                0 |          0 |                        0.44 | none                                        |
| V13T (HEADLINE: V13Z, take OFF) | S5 open                            | lockoff |       4 |      1 |             1 |                4 |          1 |                        0.44 | CANDIDATE(S): 1 (needs full robustness)     |
| V13T (HEADLINE: V13Z, take OFF) | S5 ratio                           | lock12  |       5 |      0 |             0 |                0 |          0 |                        0.55 | none                                        |
| V13T (HEADLINE: V13Z, take OFF) | S5 ratio                           | lockoff |       5 |      0 |             0 |                1 |          0 |                        0.55 | none                                        |
| V13X (DEFECT BASE)              | S4A ARR                            | lock12  |      11 |      1 |             1 |                8 |          0 |                        1.21 | band+no-harm only (placebo untested/failed) |
| V13X (DEFECT BASE)              | S4A ARR                            | lockoff |      11 |      4 |             0 |                3 |          0 |                        1.21 | band only                                   |
| V13X (DEFECT BASE)              | S4A CRT                            | lock12  |       1 |      0 |             0 |                1 |          0 |                        0.11 | none                                        |
| V13X (DEFECT BASE)              | S4A CRT                            | lockoff |       1 |      0 |             0 |                0 |          0 |                        0.11 | none                                        |
| V13X (DEFECT BASE)              | S4A DEV                            | lock12  |      10 |      1 |             0 |                4 |          0 |                        1.1  | band only                                   |
| V13X (DEFECT BASE)              | S4A DEV                            | lockoff |      10 |      3 |             0 |                6 |          0 |                        1.1  | band only                                   |
| V13X (DEFECT BASE)              | S4A EQL                            | lock12  |       2 |      0 |             0 |                0 |          0 |                        0.22 | none                                        |
| V13X (DEFECT BASE)              | S4A EQL                            | lockoff |       2 |      0 |             0 |                2 |          0 |                        0.22 | none                                        |
| V13X (DEFECT BASE)              | S4A FIB                            | lock12  |       8 |      0 |             0 |                3 |          0 |                        0.88 | none                                        |
| V13X (DEFECT BASE)              | S4A FIB                            | lockoff |       8 |      1 |             0 |                5 |          0 |                        0.88 | band only                                   |
| V13X (DEFECT BASE)              | S4A MAS                            | lock12  |       4 |      0 |             0 |                1 |          0 |                        0.44 | none                                        |
| V13X (DEFECT BASE)              | S4A MAS                            | lockoff |       4 |      1 |             1 |                3 |          1 |                        0.44 | CANDIDATE(S): 1 (needs full robustness)     |
| V13X (DEFECT BASE)              | S4A PRF                            | lock12  |       3 |      0 |             0 |                2 |          0 |                        0.33 | none                                        |
| V13X (DEFECT BASE)              | S4A PRF                            | lockoff |       3 |      0 |             0 |                1 |          0 |                        0.33 | none                                        |
| V13X (DEFECT BASE)              | S4A SES                            | lock12  |       2 |      0 |             0 |                0 |          0 |                        0.22 | none                                        |
| V13X (DEFECT BASE)              | S4A SES                            | lockoff |       2 |      0 |             0 |                2 |          0 |                        0.22 | none                                        |
| V13X (DEFECT BASE)              | S4A SWG                            | lock12  |       7 |      0 |             0 |                5 |          0 |                        0.77 | none                                        |
| V13X (DEFECT BASE)              | S4A SWG                            | lockoff |       7 |      3 |             2 |                2 |          1 |                        0.77 | CANDIDATE(S): 1 (needs full robustness)     |
| V13X (DEFECT BASE)              | S5 cong                            | lock12  |      21 |      0 |             0 |                6 |          0 |                        2.31 | none                                        |
| V13X (DEFECT BASE)              | S5 cong                            | lockoff |      21 |      1 |             1 |                4 |          0 |                        2.31 | band+no-harm only (placebo untested/failed) |
| V13X (DEFECT BASE)              | S5 nml                             | lock12  |       4 |      0 |             0 |                0 |          0 |                        0.44 | none                                        |
| V13X (DEFECT BASE)              | S5 nml                             | lockoff |       4 |      0 |             0 |                0 |          0 |                        0.44 | none                                        |
| V13X (DEFECT BASE)              | S5 open                            | lock12  |       4 |      0 |             0 |                1 |          0 |                        0.44 | none                                        |
| V13X (DEFECT BASE)              | S5 open                            | lockoff |       4 |      3 |             3 |                3 |          0 |                        0.44 | band+no-harm only (placebo untested/failed) |
| V13X (DEFECT BASE)              | S5 ratio                           | lock12  |       5 |      0 |             0 |                2 |          0 |                        0.55 | none                                        |
| V13X (DEFECT BASE)              | S5 ratio                           | lockoff |       5 |      1 |             1 |                1 |          0 |                        0.55 | band+no-harm only (placebo untested/failed) |
| V13X (DEFECT BASE)              | Z3 action table                    | lock12  |     101 |      0 |             0 |                0 |          0 |                       11.11 | none                                        |
| V13X (DEFECT BASE)              | Z3 action table                    | lockoff |     101 |      0 |             0 |                0 |          0 |                       11.11 | none                                        |
| V13X (DEFECT BASE)              | ZL3 AH ('tape', 'TCD_divbull')     | lockoff |       1 |      0 |             0 |                0 |          0 |                        0.11 | none                                        |
| V13X (DEFECT BASE)              | ZL3 AH ('tape', 'TLQ_SES_asia')    | lockoff |       1 |      1 |             1 |                0 |          0 |                        0.11 | band+no-harm only (placebo untested/failed) |
| V13X (DEFECT BASE)              | ZL3 AH ('tape', 'TPF_hvn1_sw1h')   | lockoff |       1 |      0 |             0 |                0 |          0 |                        0.11 | none                                        |
| V13X (DEFECT BASE)              | ZL3 CONF ('tape', 'TVP_hvn_day')   | lockoff |       1 |      0 |             0 |                0 |          0 |                        0.11 | none                                        |
| V13X (DEFECT BASE)              | ZL3 CONF ('tape', 'TVP_hvn_sess')  | lockoff |       1 |      0 |             0 |                0 |          0 |                        0.11 | none                                        |
| V13X (DEFECT BASE)              | ZL3 CONF ('tape', 'TVP_lvn_day')   | lockoff |       1 |      0 |             0 |                0 |          0 |                        0.11 | none                                        |
| V13X (DEFECT BASE)              | ZL3 CONF ('tape', 'TVP_lvn_sess')  | lockoff |       1 |      0 |             0 |                0 |          0 |                        0.11 | none                                        |
| V13X (DEFECT BASE)              | ZL3 CONF ('tape', 'TVP_poc_day')   | lockoff |       1 |      0 |             0 |                0 |          0 |                        0.11 | none                                        |
| V13X (DEFECT BASE)              | ZL3 CONF ('tape', 'TVP_poc_sess')  | lockoff |       1 |      0 |             0 |                0 |          0 |                        0.11 | none                                        |
| V13X (DEFECT BASE)              | ZL3 CONF ('tape', 'TVP_void_day')  | lockoff |       1 |      0 |             0 |                0 |          0 |                        0.11 | none                                        |
| V13X (DEFECT BASE)              | ZL3 CONF ('tape', 'TVP_void_sess') | lockoff |       1 |      0 |             0 |                0 |          0 |                        0.11 | none                                        |
| V13X (DEFECT BASE)              | ZL3 CONF TAPEALL                   | lockoff |      29 |      1 |             1 |                0 |          0 |                        3.19 | band+no-harm only (placebo untested/failed) |
| V13X (DEFECT BASE)              | ZL3 CONF TCD                       | lockoff |      29 |      0 |             0 |                0 |          0 |                        3.19 | none                                        |
| V13X (DEFECT BASE)              | ZL3 CONF TCP                       | lockoff |      29 |      0 |             0 |                0 |          0 |                        3.19 | none                                        |
| V13X (DEFECT BASE)              | ZL3 CONF TLP                       | lockoff |      29 |      0 |             0 |                0 |          0 |                        3.19 | none                                        |
| V13X (DEFECT BASE)              | ZL3 CONF TPF                       | lockoff |      29 |      0 |             0 |                0 |          0 |                        3.19 | none                                        |
| V13X (DEFECT BASE)              | ZL3 CONF TVP                       | lockoff |      93 |     10 |            10 |                0 |          0 |                       10.23 | band+no-harm only (placebo untested/failed) |
| V13X (DEFECT BASE)              | ZL3 DENS SET8                      | lockoff |      23 |      2 |             1 |                0 |          0 |                        2.53 | band+no-harm only (placebo untested/failed) |
| V13X (DEFECT BASE)              | ZL3 DENS SET8+L2ALL                | lockoff |      26 |      5 |             5 |                0 |          0 |                        2.86 | band+no-harm only (placebo untested/failed) |
| V13X (DEFECT BASE)              | ZL3 DENS TAPEALL                   | lockoff |      45 |      6 |             5 |                0 |          0 |                        4.95 | band+no-harm only (placebo untested/failed) |
| V13X (DEFECT BASE)              | ZL3 LRN nan                        | lockoff |      68 |     30 |            22 |                0 |          0 |                        7.48 | band+no-harm only (placebo untested/failed) |
| V13X (DEFECT BASE)              | ZL3 TWF nan                        | lockoff |       7 |      1 |             1 |                0 |          0 |                        0.77 | band+no-harm only (placebo untested/failed) |
| V13Y                            | S4A ARR                            | lock12  |       1 |      0 |             0 |                0 |          0 |                        0.11 | none                                        |
| V13Y                            | S4A ARR                            | lockoff |       1 |      0 |             0 |                0 |          0 |                        0.11 | none                                        |
| V13Y                            | S4A DEV                            | lock12  |       2 |      0 |             0 |                0 |          0 |                        0.22 | none                                        |
| V13Y                            | S4A DEV                            | lockoff |       2 |      0 |             0 |                0 |          0 |                        0.22 | none                                        |
| V13Y                            | S4A EQL                            | lock12  |       2 |      0 |             0 |                0 |          0 |                        0.22 | none                                        |
| V13Y                            | S4A EQL                            | lockoff |       2 |      0 |             0 |                0 |          0 |                        0.22 | none                                        |
| V13Y                            | S4A FIB                            | lock12  |       1 |      0 |             0 |                0 |          0 |                        0.11 | none                                        |
| V13Y                            | S4A FIB                            | lockoff |       1 |      0 |             0 |                0 |          0 |                        0.11 | none                                        |
| V13Y                            | S4A MAS                            | lock12  |       6 |      0 |             0 |                0 |          0 |                        0.66 | none                                        |
| V13Y                            | S4A MAS                            | lockoff |       6 |      0 |             0 |                0 |          0 |                        0.66 | none                                        |
| V13Y                            | S4A PIV                            | lock12  |       1 |      0 |             0 |                0 |          0 |                        0.11 | none                                        |
| V13Y                            | S4A PIV                            | lockoff |       1 |      0 |             0 |                0 |          0 |                        0.11 | none                                        |
| V13Y                            | S4A SES                            | lock12  |       5 |      0 |             0 |                0 |          0 |                        0.55 | none                                        |
| V13Y                            | S4A SES                            | lockoff |       5 |      0 |             0 |                0 |          0 |                        0.55 | none                                        |
| V13Y                            | S4A SWG                            | lock12  |       6 |      0 |             0 |                0 |          0 |                        0.66 | none                                        |
| V13Y                            | S4A SWG                            | lockoff |       6 |      2 |             0 |                0 |          0 |                        0.66 | band only                                   |
| V13Y                            | S5 cong                            | lock12  |      20 |      0 |             0 |                2 |          0 |                        2.2  | none                                        |
| V13Y                            | S5 cong                            | lockoff |      20 |      0 |             0 |                4 |          0 |                        2.2  | none                                        |
| V13Y                            | S5 nml                             | lock12  |       4 |      0 |             0 |                0 |          0 |                        0.44 | none                                        |
| V13Y                            | S5 nml                             | lockoff |       4 |      0 |             0 |                0 |          0 |                        0.44 | none                                        |
| V13Y                            | S5 open                            | lock12  |       4 |      0 |             0 |                1 |          0 |                        0.44 | none                                        |
| V13Y                            | S5 open                            | lockoff |       4 |      3 |             3 |                4 |          0 |                        0.44 | band+no-harm only (placebo untested/failed) |
| V13Y                            | S5 ratio                           | lock12  |       5 |      0 |             0 |                0 |          0 |                        0.55 | none                                        |
| V13Y                            | S5 ratio                           | lockoff |       5 |      1 |             1 |                1 |          0 |                        0.55 | band+no-harm only (placebo untested/failed) |
| V13Y                            | Z3 action table                    | lock12  |      91 |      0 |             0 |                0 |          0 |                       10.01 | none                                        |
| V13Y                            | Z3 action table                    | lockoff |      91 |      0 |             0 |                0 |          0 |                       10.01 | none                                        |
| V13Z (V13Y+nfix)                | S5 cong                            | lock12  |      20 |      0 |             0 |                0 |          0 |                        2.2  | none                                        |
| V13Z (V13Y+nfix)                | S5 cong                            | lockoff |      20 |      1 |             1 |                2 |          0 |                        2.2  | band+no-harm only (placebo untested/failed) |
| V13Z (V13Y+nfix)                | S5 nml                             | lock12  |       4 |      0 |             0 |                0 |          0 |                        0.44 | none                                        |
| V13Z (V13Y+nfix)                | S5 nml                             | lockoff |       4 |      0 |             0 |                0 |          0 |                        0.44 | none                                        |
| V13Z (V13Y+nfix)                | S5 open                            | lock12  |       4 |      0 |             0 |                0 |          0 |                        0.44 | none                                        |
| V13Z (V13Y+nfix)                | S5 open                            | lockoff |       4 |      2 |             2 |                4 |          0 |                        0.44 | band+no-harm only (placebo untested/failed) |
| V13Z (V13Y+nfix)                | S5 ratio                           | lock12  |       5 |      0 |             0 |                0 |          0 |                        0.55 | none                                        |
| V13Z (V13Y+nfix)                | S5 ratio                           | lockoff |       5 |      0 |             0 |                1 |          0 |                        0.55 | none                                        |

## What survives, program-wide, by base and frame (cells in this table; owners that have not republished on a base have no rows there)

| base                            | frame   |   cells |   band |   band_noharm |   placebo_tested |   pass_all |
|:--------------------------------|:--------|--------:|-------:|--------------:|-----------------:|-----------:|
| V13T (HEADLINE: V13Z, take OFF) | lock12  |      33 |      0 |             0 |                0 |          0 |
| V13T (HEADLINE: V13Z, take OFF) | lockoff |      33 |      1 |             1 |                7 |          1 |
| V13X (DEFECT BASE)              | lock12  |     183 |      2 |             1 |               33 |          0 |
| V13X (DEFECT BASE)              | lockoff |     601 |     73 |            54 |               32 |          2 |
| V13Y                            | lock12  |     148 |      0 |             0 |                3 |          0 |
| V13Y                            | lockoff |     148 |      6 |             4 |                9 |          0 |
| V13Z (V13Y+nfix)                | lock12  |      33 |      0 |             0 |                0 |          0 |
| V13Z (V13Y+nfix)                | lockoff |      33 |      3 |             3 |                7 |          0 |

## Exit family (T-EXIT-N, base V13T_LIVE) - see autopilot/DS3_EXIT_N.md (integrator) and the family pages DS3_EXIT_N_LOSS / TIGHTEN_SCALE / TAKE / (E4). Cell-level rows are added here when a family publishes the harness record; as of this refresh no exit rule is reported as passing on basis N (THP_POLICY_D7_N.txt is the empty header).
