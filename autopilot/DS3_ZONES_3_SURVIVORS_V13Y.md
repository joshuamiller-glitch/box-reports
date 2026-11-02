# DS3_ZONES_3_SURVIVORS_V13Y - what survives, all programs, against the V13Y noise band (Z3, 2026-11-02 ~11:40Z; refresh for 18:00Z). Research, Shadow, no PASS claims.
## Bottom line
**Nothing survives.** Of every zone cell evaluated on the fixed base V13Y, the cells that clear the phase-averaged noise band in L6M AND (PRE or X') are all lot-volume cuts or fragile: the S5 density masks and SWG|f3L flag 25-75% of rows (VOLUME), sopen40 (the only band + no-harm passer on the 2%/5% band) fails the size-matched null and the equal-risk check, ARR iplFVG and DEV fail PRE/MID. No Z3 action cell, no mean-type lead (BT, LP) and no combination (B10) passes. The shipped layer itself is not distinguishable from a random same-size half-lot layer in L6M/HOLD, and a monthly-refit zone file does not beat the fixed layer.
Band used: V13Y phase-averaged (K = 9) noise band, flip-5% row (DS3_ZONES_3_NOISE.md): lock-off L6M 20%, PRE 17%, X' 23%; lock 12R L6M 24%, PRE 13%, X' 15% (flip-2%: lock-off 16/11/16, 12R 12/13/10). For masks of ~55% of rows the 2%/5% band is the WRONG null: the size-matched null (random 55% half layer) has a 95th percentile |cut| of 61% (L6M), 57% (PRE), 46% (X'), and a mean cut of +33% in L6M.
## Table A - cells re-evaluated phase-averaged (K = 5-9 lock-reset phases) on V13Y, both frames. Columns: PA cut L6M / PRE / X' (+ = smaller maxDD vs shipped); band L6M / PRE / X' (flip-5%); band pass = L6M above band AND (PRE or X' above band); placebo = matched-row random half layer rank (share beaten) L6M/PRE/X' (n draws); carrying week = the V13Y L6M episode 2026-W27 to W38 (trough W32/W38) for every L6M/HOLD cut, W34-W40 (PRE 2024-W34..W51) for PRE (DS3_ZONES_EPISODES_V13Y.md)
| cell | family | owner | frame | PA cut L6M / PRE / X' % | band % | band pass | placebo rank | label |
|---|---|---|---|---|---|---|---|---|
| S5 sopen40 half | S5 density | S5 | lock-off | +52 / +15 / +24 | 20 / 17 / 23 | YES | 0.90/0.90/0.65 (n=20) | VOLUME / EQUAL-RISK-HARM (size-matched null: inside band; PRE/MID worse at equal risk) |
| S5 open20 half | S5 density | S5 | lock-off | +52 / +22 / +11 | 20 / 17 / 23 | YES | 0.85/0.60/0.25 (n=20) | VOLUME |
| S5 nA60>=1 skip | S5 density | S5 | lock-off | +43 / -26 / +13 | 20 / 17 / 23 | no | nan | VOLUME (PRE -26%) |
| S5 openA40 half | S5 density | S5 | lock-off | +38 / +27 / +40 | 20 / 17 / 23 | YES | 0.40/0.90/0.85 (n=20) | VOLUME |
| S5 rho60>=2 skip | S5 density | S5 | lock-off | +50 / +2 / +34 | 20 / 17 / 23 | YES | nan | VOLUME ONE-WEEK (placebo n/a) |
| S4A DEV|day_L|so_far D40 half | S4A streams | S4a | lock-off | +61 / -54 / +18 | 20 / 17 / 23 | no | nan | FRAGILE (PRE and MID negative in lock-off) |
| S4A DEV|on_L|so_far D20 half | S4A streams | S4a | lock-off | +54 / -26 / +16 | 20 / 17 / 23 | no | nan | FRAGILE (PRE and MID negative in lock-off) |
| S4A SWG|f3L|15s D40 half | S4A streams | S4a | lock-off | +46 / +15 / +27 | 20 / 17 / 23 | YES | 0.80/0.95/0.80 (n=20) | VOLUME / FRAGILE (equal-risk PRE worse) |
| S4A ARR|iplFVG|15s D20 skip | S4A streams | S4a | lock-off | +51 / -78 / +25 | 20 / 17 / 23 | YES | nan | FRAGILE (PRE -78% lock-off) |
| S4A ARR|iplFVG|15s D40 half | S4A streams | S4a | lock-off | +34 / -45 / +26 | 20 / 17 / 23 | YES | nan | FRAGILE (PRE -45% lock-off) |
| S4A FIB|ret50|1h D40 skip | S4A streams | S4a | lock-off | +20 / -5 / +5 | 20 / 17 / 23 | no | nan | NOISE |
| S4A MAS|bb_mid|4h D20 skip | S4A streams | S4a | lock-off | +17 / +3 / +8 | 20 / 17 / 23 | no | 1.00/0.85/0.75 (n=20) | NOISE (L6M below band) |
| S5 sopen40 half | S5 density | S5 | lock 12R | +35 / +10 / +28 | 24 / 13 / 14 | YES | 1.00/0.65/0.55 (n=20) | VOLUME / EQUAL-RISK-HARM (size-matched null: inside band; PRE/MID worse at equal risk) |
| S5 open20 half | S5 density | S5 | lock 12R | +45 / +34 / +40 | 24 / 13 / 14 | YES | 0.90/0.65/0.40 (n=20) | VOLUME |
| S5 nA60>=1 skip | S5 density | S5 | lock 12R | +24 / +21 / +25 | 24 / 13 / 14 | no | nan | VOLUME (PRE -26%) |
| S5 openA40 half | S5 density | S5 | lock 12R | +17 / +29 / +43 | 24 / 13 / 14 | no | 0.35/0.75/0.80 (n=20) | VOLUME |
| S5 rho60>=2 skip | S5 density | S5 | lock 12R | +28 / +3 / +19 | 24 / 13 / 14 | YES | nan | VOLUME ONE-WEEK (placebo n/a) |
| S4A DEV|day_L|so_far D40 half | S4A streams | S4a | lock 12R | +46 / -19 / +37 | 24 / 13 / 14 | YES | nan | FRAGILE (PRE and MID negative in lock-off) |
| S4A DEV|on_L|so_far D20 half | S4A streams | S4a | lock 12R | +14 / -3 / +19 | 24 / 13 / 14 | no | nan | FRAGILE (PRE and MID negative in lock-off) |
| S4A SWG|f3L|15s D40 half | S4A streams | S4a | lock 12R | +33 / +11 / +41 | 24 / 13 / 14 | YES | 0.90/0.45/1.00 (n=20) | VOLUME / FRAGILE (equal-risk PRE worse) |
| S4A ARR|iplFVG|15s D20 skip | S4A streams | S4a | lock 12R | +22 / -30 / +31 | 24 / 13 / 14 | no | nan | FRAGILE (PRE -78% lock-off) |
| S4A ARR|iplFVG|15s D40 half | S4A streams | S4a | lock 12R | +22 / +2 / +36 | 24 / 13 / 14 | no | nan | FRAGILE (PRE -45% lock-off) |
| S4A FIB|ret50|1h D40 skip | S4A streams | S4a | lock 12R | -26 / -1 / +16 | 24 / 13 / 14 | no | nan | NOISE |
| S4A MAS|bb_mid|4h D20 skip | S4A streams | S4a | lock 12R | +0 / +8 / +3 | 24 / 13 / 14 | no | 0.60/0.90/0.80 (n=20) | NOISE (L6M below band) |
| Z3 ALL7 skip | Z3 action table | Z3 | lock-off | -10 / -1 / +10 | 20 / 17 / 23 | no | nan | NOISE |
| Z3 ALL7 rt | Z3 action table | Z3 | lock-off | +4 / -41 / -51 | 20 / 17 / 23 | no | nan | NOISE |
| Z3 OTE705 skip | Z3 action table | Z3 | lock-off | -6 / -0 / +12 | 20 / 17 / 23 | no | nan | NOISE |
| Z3 kijun1h wt | Z3 action table | Z3 | lock-off | +4 / -4 / +7 | 20 / 17 / 23 | no | nan | NOISE |
| Z3 camH3 wt | Z3 action table | Z3 | lock-off | -6 / +2 / +8 | 20 / 17 / 23 | no | nan | NOISE |
| Z3 bar4hmid wt | Z3 action table | Z3 | lock-off | +3 / -1 / -1 | 20 / 17 / 23 | no | nan | NOISE |
| Z3 O62_30 d5 | Z3 action table | Z3 | lock-off | +23 / -3 / +6 | 20 / 17 / 23 | no | nan | (recent windows only), MID -48% |
| Z3 ALL7 skip | Z3 action table | Z3 | lock 12R | -1 / -13 / +27 | 24 / 13 / 14 | no | nan | NOISE |
| Z3 ALL7 rt | Z3 action table | Z3 | lock 12R | +23 / -3 / -25 | 24 / 13 / 14 | no | nan | NOISE |
| Z3 OTE705 skip | Z3 action table | Z3 | lock 12R | +1 / +6 / +17 | 24 / 13 / 14 | no | nan | NOISE |
| Z3 kijun1h wt | Z3 action table | Z3 | lock 12R | -1 / +4 / +5 | 24 / 13 / 14 | no | nan | NOISE |
| Z3 camH3 wt | Z3 action table | Z3 | lock 12R | -4 / +2 / +1 | 24 / 13 / 14 | no | nan | NOISE |
| Z3 bar4hmid wt | Z3 action table | Z3 | lock 12R | +5 / -1 / +4 | 24 / 13 / 14 | no | nan | NOISE |
| Z3 O62_30 d5 | Z3 action table | Z3 | lock 12R | +21 / +2 / -0 | 24 / 13 / 14 | no | nan | (recent windows only), MID -48% |

## Table B - mean-type leads on smooth measures (lock-off, PA K = 9; see DS3_ZONES_3_PHASE_AVG.md section 3)
| cell | owner | maxDD cut L6M / PRE / X' | ulcer L6M / PRE / X' ($k) | mean L6M ($k/wk) | label |
|---|---|---|---|---|---|
| BT swing flip skip (F10 4h D40) | ZL-1 | -12 / +3 / -11% | +4.3 / -1.2 / +0.8 | +1.8 | MEAN-ONLY (risk measures worse); 12R worse |
| LP A40 TLP p25 4h skip | ZL-2 | +19 / +9 / +4% (below band 20/17/23) | -11.5 / -6.2 / +4.8 (band 9-12 / 6-9 / 4-6) | +3.2 | smooth-measure LEAD-weak, LOCK-OFF ONLY (12R flat), MID -18% |
| BT+LP union skip | ZL-1 + ZL-2 | +10 / +14 / -1% | -8.0 / -8.1 / +3.1 | +4.9 | mean + ulcer, no maxDD band pass; equal-risk lot scale 1.00 |
| S5 sopen40 half (size-matched check) | S5 | +53 / +15 / +24% (size-matched null mean +33 / -4 / +14%, p95 61 / 57 / 46%) | n/a | -7.4 | VOLUME + EQUAL-RISK-HARM: equal-risk PRE maxDD +23%, MID +50%, PRE mean -52% |
## Table C - single-path scoring in the program master table (autopilot/ZONES3_MASTER_TABLE.csv)
V13Y rows (cells scored on the fixed base, single-path cut vs single-path band): 
| program | frame | cells | band pass |
|---|---|---|---|
| S4A streams | lock12 | 24 | 0 |
| S4A streams | lockoff | 24 | 2 |
| S5 density | lock12 | 33 | 0 |
| S5 density | lockoff | 33 | 4 |
| Z3 action table | lock12 | 91 | 0 |
| Z3 action table | lockoff | 91 | 0 |
Rows still on the V13X DEFECT BASE (need a V13Y re-run before any conclusion): 
| program | frame | cells | band pass (defect base) |
|---|---|---|---|
| S4A streams | lock12 | 48 | 2 |
| S4A streams | lockoff | 48 | 12 |
| S5 density | lock12 | 34 | 0 |
| S5 density | lockoff | 34 | 5 |
| Z3 action table | lock12 | 101 | 0 |
| Z3 action table | lockoff | 101 | 0 |
| ZL3 L2/tape zones | lockoff | 418 | 56 |
Z3 action table on V13Y (my 91 cells x 2 frames, single-path band): 0 of 182 pass in either frame (survivors_z3.csv). Combinations B10 on V13Y: none. Walk-forward on V13Y: no refit chain beats the fixed layer.
## What would count as a survivor, and what is missing
A survivor needs: PA cut above the PA band in L6M and PRE or X' (same sign); no-harm (PRE and MID not worse than -band); matched-volume/size-matched placebo >= 0.95 in those windows; equal-risk maxDD/Calmar not worse than shipped; carrying episode dropped with the cut kept; D +-25/50% sign stability. No cell has all six. Still to do before 18:00Z: S4A/ZL3 cells on V13Y with PA K = 9 (their 56 + 12 defect-base band passers), placebo ranks at >= 100 draws for the PA tables above (n = 20 now), and the 12R phase-averaged placebo for the S4A leads without placebo (DEV, ARR iplFVG, FIB ret50, nA60, rho60).

## Table D - ZL-3 cells re-evaluated phase-averaged (K = 9 lock-reset phases, phase_lib) on V13Y, both frames (appended by ZL-3). Masks: the cells' own V13Y masks (skip / half; G1 = skip + full lot for unconfirmed within the D20 set). PA cut = + smaller maxDD vs the shipped V13Y layer; band = V13Y PA flip-5% band; band pass = L6M above band AND (PRE or X') above band; the matched-volume placebo for the one band-passer is the size-matched null in Table A (the 40,617-row SET8 rule is S5's sopen family). 13 of the 56 defect-base band passers (the distinct cell families) were re-run; the rest are variants of these cells (D, tolerance, tier, book/session slices).
| cell | family | owner | frame | PA cut L6M / PRE / X' % | band % | band pass | placebo rank | label |
|---|---|---|---|---|---|---|---|---|
| F1 TAPEALL >=5 zones half | ZL3 density | ZL-3 | lock-off | -11 / +5 / -17 | 20 / 17 / 23 | no | not run (size-matched null not built) | below band |
| F1 TAPEALL >=5 zones half | ZL3 density | ZL-3 | lock 12R | +5 / -8 / +22 | 24 / 13 / 14 | no | not run (size-matched null not built) | below band |
| F2 TPF hvn1 sw1h D20 skip | ZL3 tape | ZL-3 | lock-off | -2 / -3 / -6 | 20 / 17 / 23 | no | not run (size-matched null not built) | below band |
| F2 TPF hvn1 sw1h D20 skip | ZL3 tape | ZL-3 | lock 12R | -0 / -6 / +13 | 24 / 13 / 14 | no | not run (size-matched null not built) | below band |
| F3 TLQ SES asia D20 skip | ZL3 tape | ZL-3 | lock-off | +10 / +5 / +20 | 20 / 17 / 23 | no | not run (size-matched null not built) | below band |
| F3 TLQ SES asia D20 skip | ZL3 tape | ZL-3 | lock 12R | +5 / +5 / +8 | 24 / 13 / 14 | no | not run (size-matched null not built) | below band |
| F4 TCD divbull D20 skip | ZL3 tape | ZL-3 | lock-off | -0 / -9 / -18 | 20 / 17 / 23 | no | not run (size-matched null not built) | below band |
| F4 TCD divbull D20 skip | ZL3 tape | ZL-3 | lock 12R | -4 / +3 / +11 | 24 / 13 / 14 | no | not run (size-matched null not built) | below band |
| FVG 15m 24h D40 skip | ZL3 B3 FVG | ZL-3 | lock-off | -5 / -10 / -5 | 20 / 17 / 23 | no | not run (size-matched null not built) | below band |
| FVG 15m 24h D40 skip | ZL3 B3 FVG | ZL-3 | lock 12R | -17 / -15 / +16 | 24 / 13 / 14 | no | not run (size-matched null not built) | below band |
| FVG 5m 4h D30 skip | ZL3 B3 FVG | ZL-3 | lock-off | -3 / -18 / -5 | 20 / 17 / 23 | no | not run (size-matched null not built) | below band |
| FVG 5m 4h D30 skip | ZL3 B3 FVG | ZL-3 | lock 12R | -15 / -5 / -13 | 24 / 13 / 14 | no | not run (size-matched null not built) | below band |
| FVG 5m 4h D60 skip | ZL3 B3 FVG | ZL-3 | lock-off | -23 / -15 / +2 | 20 / 17 / 23 | no | not run (size-matched null not built) | below band |
| FVG 5m 4h D60 skip | ZL3 B3 FVG | ZL-3 | lock 12R | -22 / -3 / -6 | 24 / 13 / 14 | no | not run (size-matched null not built) | below band |
| G1 TVP-confirmed skip, unconfirmed full | ZL3 conf/weak | ZL-3 | lock-off | +47 / -10 / -10 | 20 / 17 / 23 | no | not run (size-matched null not built) | below band |
| G1 TVP-confirmed skip, unconfirmed full | ZL3 conf/weak | ZL-3 | lock 12R | +11 / +3 / +6 | 24 / 13 / 14 | no | not run (size-matched null not built) | below band |
| G2 TVP-confirmed skip Dl60 | ZL3 conf/weak | ZL-3 | lock-off | +43 / -12 / +6 | 20 / 17 / 23 | no | not run (size-matched null not built) | below band |
| G2 TVP-confirmed skip Dl60 | ZL3 conf/weak | ZL-3 | lock 12R | +4 / +18 / +40 | 24 / 13 / 14 | no | not run (size-matched null not built) | below band |
| PUL k3 4h D20 skip (ZL-1) | ZL1 book | ZL-3 | lock-off | +7 / -4 / +0 | 20 / 17 / 23 | no | not run (size-matched null not built) | below band |
| PUL k3 4h D20 skip (ZL-1) | ZL1 book | ZL-3 | lock 12R | +9 / +8 / +5 | 24 / 13 / 14 | no | not run (size-matched null not built) | below band |
| SET8 open space (no set line within 40) skip | ZL3 density | ZL-3 | lock-off | +68 / -33 / +28 | 20 / 17 / 23 | YES | not run (size-matched null not built) | VOLUME (40,617 rows; MID -239) |
| SET8 open space (no set line within 40) skip | ZL3 density | ZL-3 | lock 12R | +45 / -14 / +51 | 24 / 13 / 14 | YES | not run (size-matched null not built) | VOLUME (40,617 rows; MID -105) |
| SET8 open space half | ZL3 density | ZL-3 | lock-off | +38 / +28 / +39 | 20 / 17 / 23 | YES | not run (size-matched null not built) | VOLUME |
| SET8 open space half | ZL3 density | ZL-3 | lock 12R | +23 / +27 / +42 | 24 / 13 / 14 | no | not run (size-matched null not built) | below band |
| TAPEALL ratio<=0.5 half | ZL3 density | ZL-3 | lock-off | +31 / +16 / +3 | 20 / 17 / 23 | no | not run (size-matched null not built) | below band |
| TAPEALL ratio<=0.5 half | ZL3 density | ZL-3 | lock 12R | +3 / +7 / +4 | 24 / 13 / 14 | no | not run (size-matched null not built) | below band |

Result: of 13 cells x 2 frames only the SET8 'open space' rule passes the band (skip in both frames, half in lock-off), and it touches 40,617 of 88,490 rows (VOLUME: skip MID -239% lock-off, PRE -33%, mean -20.3k/wk); G2, G1, F1-F4, FVG, PUL k3 and the density halves are below the band or fail PRE in at least one frame. No ZL-3 survivor.
