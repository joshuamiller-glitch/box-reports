## Dial 10: trade-horizon bracket
**VERDICT (plain, not a PASS): 49 of 94 registered cells scored through L3M, 18 through L6M, 0 through HOLD; 0 (cell,scope) leads pass the tolerant gate in every scored window (0 at scope all) - before placebo. Best L3M cell inside the mean gate: M1_75_g10_c1_d10_c15_tb_N (DD +0.1%, -288 $/wk).**

Identity: TL3_D10_M1_50_g00_c1_d10_c20_tb_B 202610 (hook active, g=0): 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL. Prereg autopilot/DIAL10_PREREG.md (sha line in DECISIONS.md 2026-11-14T22:33Z). Order: ADDENDUM_DIAL10_20261114.md. Code code/th_dial10 (d10_core.py features, d10_coef.py coefficient table, d10_hooks.py hook, d10_driver.py). Bulk /mnt/l2/l2vast/_dial10. Tag D10 (quota 3).
**LOT BASIS**: engine dollars are BASE lots (live user lots x1.75, live caps = engine caps x1.75); the engine charges its raw $1.18/contract RT with the engine fills, FEES.md says $4.84 RT. Every $ column is raw $1.18 unless it says $4.84; the $4.84 columns reprice delta mean/wk as net - lots x 3.66 per trade for cell and JN05W2 alike (no rerun) and show the lot change per week.
Definition: at the signal second the hook computes EM = expected NQ range over the book+session holding horizon H (H50 = median, H75 = 75th pct of the book+session holding time, causal) from own 1-min bars (last 15/30/60/120 min range and realised vol, same-clock normal level of the previous 20 sessions, own session level, range used so far, elapsed fraction) with a walk-forward ridge (coefficients refit every 14 days; M2 adds the T-RANGE2 session forecast and calendar flags). r = EM / ref, ref = trailing-120-day median of the fitted EM for that book+session (so k = stop/ref is fitted on earlier data and tracks price/vol level). W = clip(stop x r^g, lo, hi) with dead band |r-1|<=db => W=stop. Version A: target, state-cut arm and ctxcut arms, K7 flat cut, TH-L2 LOSS_MIN and TIGHT_TRAIL, MINDIP add dip, BookLock R from actual lots and the profit-side 30-point tighten threshold all scale with W/stop. Lots: c = constant dollars at the stop (lots x stop/W, increase capped x1.5/x2/x3, wide brackets reduce lots), h = lots follow half the change in W. O7 fixed. Cell name = TL3_D10_<forecast>_<H tag>_g<10g>_c<clip 1=30..100 2=25..120 3=20..150>_d<db %>_<lots><cap x10>_t<target ratio: b book own, 08 10 12 15 x W, m moving>_<half B both N narrow-only W wide-only>.
**The hard-coded 30-point profit-side tighten threshold (sim.py manage_th_l2, `unreal < 30.0`)** is fixed through the hook: while the old-panel profit tighten is on (before 2026-11-02 08:50 ET; none of it in the live panel after that), the hook shows sim an entry reference shifted so that unreal/W-ratio is tested against 30, i.e. the trigger becomes 30 x W/stop points of open profit (tight trail already scaled via TIGHT_TRAIL). Pair cells with `_x30` in the name run the unfixed version. Effect: narrow brackets start the profit tighten earlier (at 30W/stop), wide ones later; it only matters in months before 2026-11-02, never after.

### Holding time per book and session (JN05W2 exact trades, all 43 months, minutes)
| book | session | trades | median | 75th pct | last causal H50 / H75 used |
|---|---|---|---|---|---|
| A7 | asia | 1156 | 144 | 409 | 152 / 423 |
| H7 | asia | 700 | 229 | 511 | 244 / 515 |
| H7 | nyam | 348 | 43 | 117 | 43 / 117 |
| K7 | asia | 2596 | 88 | 270 | 91 / 279 |
| K7 | london | 1781 | 64 | 139 | 64 / 140 |
| K7 | nyam | 1565 | 23 | 64 | 23 / 64 |
| K7 | nypm | 1136 | 42 | 103 | 42 / 103 |
| M7 | london | 2489 | 73 | 172 | 74 / 174 |
| M7 | nyam | 1496 | 22 | 60 | 22 / 60 |
| O7 | nyam | 452 | 14 | 33 | 15 / 33 |
| P7 | asia | 2161 | 96 | 325 | 98 / 332 |
| P7 | london | 1537 | 60 | 136 | 60 / 136 |
| P7 | nyam | 1050 | 24 | 57 | 24 / 57 |
| U7 | asia | 686 | 201 | 456 | 208 / 459 |
| U7 | london | 645 | 109 | 243 | 110 / 244 |

Heavy tail: some holds run for days (stop-less P7/K7 waiting); H is clipped to 5..600 min (median) and 8..900 (75th).

### FORECAST QUALITY TABLE: expected NQ move over the trade horizon, walk-forward (14-day blocks, expanding, min 90 days), R2 / Spearman rank, per session
Target = ln(high-low over the next H minutes / price) at each trade signal second of JN05W2 (H = causal median holding time of that book+session, tag 50; 75th pct tag 75). B0 is the session-start forecast the first Dial 9 used (available since 2025-03-19), B2 the T-RANGE2 v1 session forecast (HAR+CME, from 2023-10), both fed through the same ridge with ln H. Window "since 2025-03" is the like-for-like sample (all models on the same trades); "ALL43" scores M1/B1 on every trade from ~2023-05 (each model only where its input exists, n differs).

**Horizon = median holding time**
| session | window | n (like-for-like) | B0 start fc b (D9) | B2 T-RANGE2 | B1 own sess level | **M1 bars only** | M1 w/o same-clock | M2 +T-RANGE2+cal (file) |
|---|---|---|---|---|---|---|---|---|
| asia | since 2025-03 | 4424 | 0.32 / 0.55 | 0.36 / 0.57 | 0.19 / 0.42 | 0.49 / 0.68 | 0.42 / 0.61 | 0.49 / 0.68 |
| asia | L6M | 2006 | 0.26 / 0.52 | 0.33 / 0.57 | 0.25 / 0.50 | 0.46 / 0.67 | 0.37 / 0.60 | 0.46 / 0.66 |
| asia | L3M | 875 | 0.12 / 0.41 | 0.16 / 0.44 | 0.07 / 0.34 | 0.27 / 0.55 | 0.25 / 0.50 | 0.28 / 0.56 |
| asia | ALL43 (M1/B1) | 7125 | 0.32 / 0.55 | 0.33 / 0.56 | 0.11 / 0.35 | 0.50 / 0.68 | 0.45 / 0.63 | 0.51 / 0.69 |
| london | since 2025-03 | 3535 | 0.19 / 0.46 | 0.28 / 0.55 | 0.08 / 0.34 | 0.45 / 0.67 | 0.36 / 0.60 | 0.46 / 0.68 |
| london | L6M | 1406 | 0.10 / 0.38 | 0.22 / 0.48 | 0.07 / 0.28 | 0.32 / 0.58 | 0.25 / 0.51 | 0.34 / 0.59 |
| london | L3M | 673 | 0.07 / 0.30 | 0.09 / 0.32 | -0.09 / 0.19 | 0.13 / 0.43 | 0.06 / 0.40 | 0.18 / 0.45 |
| london | ALL43 (M1/B1) | 6298 | 0.19 / 0.46 | 0.37 / 0.57 | 0.14 / 0.38 | 0.55 / 0.71 | 0.46 / 0.65 | 0.56 / 0.72 |
| nyam | since 2025-03 | 1955 | 0.16 / 0.43 | 0.24 / 0.51 | 0.01 / 0.22 | 0.50 / 0.71 | 0.50 / 0.71 | 0.51 / 0.71 |
| nyam | L6M | 600 | 0.23 / 0.53 | 0.28 / 0.56 | 0.05 / 0.26 | 0.61 / 0.78 | 0.61 / 0.78 | 0.61 / 0.78 |
| nyam | L3M | 271 | -0.08 / 0.33 | 0.04 / 0.35 | -0.35 / 0.10 | 0.42 / 0.64 | 0.43 / 0.65 | 0.44 / 0.65 |
| nyam | ALL43 (M1/B1) | 4742 | 0.16 / 0.43 | 0.30 / 0.53 | 0.11 / 0.34 | 0.53 / 0.70 | 0.53 / 0.70 | 0.53 / 0.71 |
| nypm | since 2025-03 | 326 | 0.13 / 0.41 | 0.35 / 0.65 | 0.05 / 0.20 | 0.53 / 0.72 | 0.53 / 0.72 | 0.56 / 0.74 |
| nypm | L6M | 150 | 0.20 / 0.51 | 0.37 / 0.69 | 0.08 / 0.26 | 0.61 / 0.79 | 0.61 / 0.79 | 0.64 / 0.80 |
| nypm | L3M | 56 | -0.33 / 0.12 | -0.18 / 0.16 | -0.82 / -0.06 | 0.19 / 0.54 | 0.17 / 0.53 | 0.25 / 0.50 |
| nypm | ALL43 (M1/B1) | 967 | 0.13 / 0.41 | 0.21 / 0.54 | 0.09 / 0.29 | 0.50 / 0.68 | 0.50 / 0.68 | 0.51 / 0.69 |

**Horizon = 75th percentile holding time**
| session | window | n (like-for-like) | B0 start fc b (D9) | B2 T-RANGE2 | B1 own sess level | **M1 bars only** | M1 w/o same-clock | M2 +T-RANGE2+cal (file) |
|---|---|---|---|---|---|---|---|---|
| asia | since 2025-03 | 4424 | 0.30 / 0.54 | 0.35 / 0.54 | 0.14 / 0.36 | 0.44 / 0.65 | 0.36 / 0.58 | 0.45 / 0.66 |
| asia | L6M | 2006 | 0.12 / 0.45 | 0.23 / 0.49 | 0.19 / 0.44 | 0.32 / 0.59 | 0.18 / 0.50 | 0.32 / 0.59 |
| asia | L3M | 875 | -0.11 / 0.27 | -0.01 / 0.31 | -0.07 / 0.21 | 0.05 / 0.40 | -0.02 / 0.39 | 0.06 / 0.41 |
| asia | ALL43 (M1/B1) | 7125 | 0.30 / 0.54 | 0.30 / 0.53 | 0.09 / 0.32 | 0.49 / 0.67 | 0.43 / 0.62 | 0.49 / 0.68 |
| london | since 2025-03 | 3535 | 0.16 / 0.42 | 0.23 / 0.49 | 0.07 / 0.33 | 0.56 / 0.75 | 0.48 / 0.69 | 0.57 / 0.76 |
| london | L6M | 1406 | 0.07 / 0.29 | 0.14 / 0.41 | 0.06 / 0.27 | 0.47 / 0.68 | 0.37 / 0.61 | 0.48 / 0.68 |
| london | L3M | 673 | 0.03 / 0.23 | 0.02 / 0.27 | -0.10 / 0.26 | 0.31 / 0.61 | 0.23 / 0.54 | 0.35 / 0.60 |
| london | ALL43 (M1/B1) | 6297 | 0.16 / 0.42 | 0.31 / 0.52 | 0.12 / 0.34 | 0.59 / 0.76 | 0.53 / 0.72 | 0.61 / 0.77 |
| nyam | since 2025-03 | 1955 | 0.18 / 0.46 | 0.27 / 0.54 | 0.04 / 0.28 | 0.47 / 0.69 | 0.47 / 0.69 | 0.48 / 0.70 |
| nyam | L6M | 600 | 0.22 / 0.51 | 0.26 / 0.55 | 0.09 / 0.33 | 0.55 / 0.74 | 0.55 / 0.74 | 0.54 / 0.73 |
| nyam | L3M | 271 | -0.08 / 0.27 | 0.06 / 0.37 | -0.24 / 0.23 | 0.33 / 0.56 | 0.34 / 0.58 | 0.34 / 0.56 |
| nyam | ALL43 (M1/B1) | 4742 | 0.18 / 0.46 | 0.31 / 0.54 | 0.11 / 0.34 | 0.48 / 0.67 | 0.47 / 0.67 | 0.48 / 0.68 |
| nypm | since 2025-03 | 326 | 0.18 / 0.41 | 0.38 / 0.67 | 0.04 / 0.16 | 0.45 / 0.65 | 0.44 / 0.64 | 0.51 / 0.70 |
| nypm | L6M | 150 | 0.24 / 0.49 | 0.42 / 0.72 | 0.07 / 0.26 | 0.54 / 0.73 | 0.54 / 0.72 | 0.61 / 0.77 |
| nypm | L3M | 56 | -0.81 / 0.15 | -0.52 / 0.07 | -1.58 / -0.18 | -0.56 / 0.30 | -0.64 / 0.28 | -0.40 / 0.25 |
| nypm | ALL43 (M1/B1) | 962 | 0.18 / 0.41 | 0.23 / 0.54 | 0.06 / 0.25 | 0.40 / 0.62 | 0.40 / 0.61 | 0.43 / 0.65 |

Reading: cell = R2 / Spearman. Out-of-sample, no look-ahead (inputs closed bars up to the signal second; training targets ended before the block start). "Bars only" = D7 can compute everything from its own 1-minute bars plus a small coefficient table that is refit every 14 days; M2 needs the T-RANGE2 file and the calendar. Not a PASS claim: a better forecast does not by itself make a better bracket (exact cells below decide).


### Which setting carries it (median over cells, scope all, delta vs JN05W2; DD cut + = smaller drawdown; cells of the plain family only, no book/session restriction)
| group | cells L3M | median DD cut L3M % | median d mean L3M $/wk | median d worst week L3M | median d full stops/wk | L6M median DD cut % / d mean / cells |
|---|---|---|---|---|---|---|
| g=0.5 | 6 | -10.9 | -3267 | -3640 | +1.41 | -10.9 / -4207 / 6 |
| g=1.0 | 29 | -11.1 | -4332 | -2744 | +2.89 | -16.8 / -3587 / 10 |
| g=1.5 | 6 | -27.5 | -9814 | -12670 | +4.03 | -19.5 / -7725 / 1 |
| g=2.0 | 6 | -54.3 | -11675 | -4932 | +4.18 | -97.4 / -6163 / 1 |
| clip=1 | 30 | -13.3 | -3800 | -4502 | +2.85 | -16.8 / -3785 / 10 |
| clip=2 | 10 | -15.7 | -6328 | -4149 | +3.39 | -10.9 / -4193 / 4 |
| clip=3 | 8 | -18.3 | -7847 | -4405 | +3.77 | -12.7 / -4193 / 4 |
| tag=50 | 20 | -17.5 | -5622 | -7032 | +2.74 | -17.5 / -3785 / 10 |
| tag=75 | 28 | -10.1 | -4911 | -2730 | +3.16 | -12.7 / -3950 / 8 |
| db=0 | 3 | -4.2 | -4332 | -1893 | +3.35 | n/a |
| db=10 | 43 | -16.6 | -5256 | -4214 | +3.12 | -14.4 / -3785 / 17 |
| db=20 | 2 | -5.3 | -1959 | -2498 | +2.66 | -18.0 / -3931 / 1 |
| lots=c15 | 3 | -9.1 | -3080 | -945 | +3.12 | -17.1 / -4229 / 1 |
| lots=c20 | 41 | -16.7 | -4911 | -4085 | +3.12 | -14.4 / -3584 / 15 |
| lots=c30 | 2 | -12.3 | -4249 | -8294 | +2.82 | -22.3 / -3785 / 1 |
| lots=h | 2 | -14.4 | -9251 | -6458 | +2.36 | -16.6 / -5544 / 1 |
| tr=08 | 2 | +0.9 | -5800 | +4968 | +2.13 | n/a |
| tr=10 | 1 | -2.3 | -2708 | -945 | +3.12 | n/a |
| tr=12 | 2 | -70.6 | -8601 | -17857 | +3.61 | n/a |
| tr=b | 42 | -16.6 | -5025 | -4470 | +3.12 | -14.4 / -3785 / 18 |
| tr=m | 1 | -0.7 | -3553 | +1066 | +2.82 | n/a |
| half=B | 38 | -16.6 | -5573 | -4470 | +3.12 | -14.4 / -3858 / 16 |
| half=N | 8 | -1.3 | -3468 | +4 | +3.35 | -10.7 / -2669 / 2 |
| half=W | 2 | -14.5 | -1736 | -6492 | -0.38 | n/a |
| fc=M1 | 47 | -14.4 | -4911 | -4085 | +3.12 | -14.4 / -3785 / 18 |
| fc=M2 | 1 | -36.2 | -7967 | -10331 | +2.89 | n/a |

### Per cell, scope all (sorted by L3M drawdown cut; L6M, HOLD, GAP/MID and PRE when present)
| cell | L3M | L6M | HOLD | MID(GAP) | PRE | d mean/wk at $4.84 L3M | at $4.84 L6M |
|---|---|---|---|---|---|---|---|
| M1_75_g10_c1_d20_c20_tb_B | -1154 $/wk, DD +7.5%, ww +7015, stops 12.71(10.35), b5 79%, w2l 2 | n/a | n/a | n/a | n/a | -1457 (lots +83/wk) | n/a |
| M1_75_g10_c1_d10_c20_t08_N | -4047 $/wk, DD +3.0%, ww +9786, stops 12.48(10.35), b5 66%, w2l 2 | n/a | n/a | n/a | n/a | -4529 (lots +132/wk) | n/a |
| M1_75_g10_c1_d10_c15_tb_N | -288 $/wk, DD +0.1%, ww +154, stops 13.85(10.35), b5 74%, w2l 2 | n/a | n/a | n/a | n/a | -620 (lots +91/wk) | n/a |
| M1_75_g10_c1_d10_c20_tb_N | +236 $/wk, DD +0.1%, ww +154, stops 13.85(10.35), b5 75%, w2l 2 | -1949 $/wk, DD +0.1%, ww +154, stops 13.16(10.99), b5 76%, w2l 3 | n/a | n/a | n/a | -126 (lots +99/wk) | -2172 (lots +61/wk) |
| M1_50_g00_c1_d10_c20_tb_B | +0 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +0 (lots +0/wk) | n/a |
| M1_75_g10_c1_d10_c20_tm_N | -3553 $/wk, DD -0.7%, ww +1066, stops 13.16(10.35), b5 79%, w2l 3 | n/a | n/a | n/a | n/a | -3971 (lots +114/wk) | n/a |
| M1_75_g10_c1_d10_c20_t08_B | -7554 $/wk, DD -1.1%, ww +150, stops 12.48(10.35), b5 61%, w2l 3 | n/a | n/a | n/a | n/a | -8006 (lots +123/wk) | n/a |
| M1_75_g10_c1_d00_c20_tb_N | +84 $/wk, DD -1.8%, ww -146, stops 13.85(10.35), b5 71%, w2l 2 | n/a | n/a | n/a | n/a | -280 (lots +99/wk) | n/a |
| M1_75_g10_c1_d10_c20_tb_B | -2708 $/wk, DD -2.3%, ww -945, stops 13.47(10.35), b5 69%, w2l 2 | -1372 $/wk, DD -2.3%, ww -945, stops 11.91(10.99), b5 52%, w2l 2 | n/a | n/a | n/a | -3047 (lots +92/wk) | -1483 (lots +30/wk) |
| M1_75_g10_c1_d10_c30_tb_B | -2708 $/wk, DD -2.3%, ww -945, stops 13.47(10.35), b5 69%, w2l 2 | n/a | n/a | n/a | n/a | -3047 (lots +92/wk) | n/a |
| M1_75_g10_c1_d10_c20_t10_B | -2708 $/wk, DD -2.3%, ww -945, stops 13.47(10.35), b5 69%, w2l 2 | n/a | n/a | n/a | n/a | -3047 (lots +92/wk) | n/a |
| M1_75_g10_c2_d10_c20_tb_B | -4536 $/wk, DD -2.7%, ww -675, stops 13.62(10.35), b5 58%, w2l 2 | -2465 $/wk, DD -2.7%, ww -675, stops 11.79(10.99), b5 44%, w2l 2 | n/a | n/a | n/a | -4867 (lots +90/wk) | -2570 (lots +29/wk) |
| M1_75_g10_c2_d00_c20_tb_B | -4332 $/wk, DD -4.2%, ww -1893, stops 13.70(10.35), b5 53%, w2l 2 | n/a | n/a | n/a | n/a | -4664 (lots +91/wk) | n/a |
| M1_75_g10_c1_d10_c20_tb_W | -885 $/wk, DD -7.3%, ww -2716, stops 10.04(10.35), b5 95%, w2l 0 | n/a | n/a | n/a | n/a | -873 (lots -3/wk) | n/a |
| M1_50_g15_c2_d10_c20_tb_B | -7400 $/wk, DD -7.4%, ww -4214, stops 14.30(10.35), b5 63%, w2l 3 | n/a | n/a | n/a | n/a | -8036 (lots +174/wk) | n/a |
| M1_50_g05_c1_d10_c20_tb_B | -1623 $/wk, DD -7.5%, ww -4085, stops 11.79(10.35), b5 78%, w2l 3 | -3584 $/wk, DD -7.5%, ww -4085, stops 11.07(10.99), b5 87%, w2l 3 | n/a | n/a | n/a | -1835 (lots +58/wk) | -3659 (lots +20/wk) |
| M1_50_g05_c2_d10_c20_tb_B | -1623 $/wk, DD -7.5%, ww -4085, stops 11.79(10.35), b5 78%, w2l 3 | -3555 $/wk, DD -7.5%, ww -4085, stops 11.07(10.99), b5 87%, w2l 3 | n/a | n/a | n/a | -1835 (lots +58/wk) | -3630 (lots +20/wk) |
| M1_50_g05_c3_d10_c20_tb_B | -1623 $/wk, DD -7.5%, ww -4085, stops 11.79(10.35), b5 78%, w2l 3 | -3555 $/wk, DD -7.5%, ww -4085, stops 11.07(10.99), b5 87%, w2l 3 | n/a | n/a | n/a | -1835 (lots +58/wk) | -3630 (lots +20/wk) |
| M1_75_g10_c1_d10_c15_tb_B | -3080 $/wk, DD -9.1%, ww -945, stops 13.47(10.35), b5 69%, w2l 2 | n/a | n/a | n/a | n/a | -3390 (lots +85/wk) | n/a |
| M1_75_g10_c3_d10_c20_tb_B | -5139 $/wk, DD -11.1%, ww -2744, stops 13.62(10.35), b5 58%, w2l 2 | -3069 $/wk, DD -11.1%, ww -2744, stops 11.79(10.99), b5 45%, w2l 2 | n/a | n/a | n/a | -5463 (lots +89/wk) | -3171 (lots +28/wk) |
| M1_75_g10_c1_d10_h_tb_B | -9206 $/wk, DD -12.3%, ww -6131, stops 12.93(10.35), b5 50%, w2l 3 | n/a | n/a | n/a | n/a | -9370 (lots +45/wk) | n/a |
| M1_75_g05_c1_d10_c20_tb_B | -4911 $/wk, DD -14.4%, ww -3194, stops 11.72(10.35), b5 74%, w2l 2 | -4851 $/wk, DD -14.4%, ww -3194, stops 11.49(10.99), b5 67%, w2l 2 | n/a | n/a | n/a | -5065 (lots +42/wk) | -4898 (lots +13/wk) |
| M1_75_g05_c2_d10_c20_tb_B | -4911 $/wk, DD -14.4%, ww -3194, stops 11.72(10.35), b5 74%, w2l 2 | -4831 $/wk, DD -14.4%, ww -3194, stops 11.49(10.99), b5 67%, w2l 2 | n/a | n/a | n/a | -5065 (lots +42/wk) | -4878 (lots +13/wk) |
| M1_75_g05_c3_d10_c20_tb_B | -4911 $/wk, DD -14.4%, ww -3194, stops 11.72(10.35), b5 74%, w2l 2 | -4831 $/wk, DD -14.4%, ww -3194, stops 11.49(10.99), b5 67%, w2l 2 | n/a | n/a | n/a | -5065 (lots +42/wk) | -4878 (lots +13/wk) |
| M1_50_g10_c1_d10_h_tb_B | -9296 $/wk, DD -16.6%, ww -6785, stops 12.48(10.35), b5 48%, w2l 2 | -5544 $/wk, DD -16.6%, ww -6785, stops 11.22(10.99), b5 52%, w2l 2 | n/a | n/a | n/a | -9550 (lots +69/wk) | -5609 (lots +18/wk) |
| M1_50_g15_c1_d10_c20_tb_B | -4393 $/wk, DD -16.7%, ww -7278, stops 14.00(10.35), b5 74%, w2l 3 | n/a | n/a | n/a | n/a | -4996 (lots +165/wk) | n/a |
| M1_50_g10_c2_d10_c20_tb_B | -5256 $/wk, DD -17.1%, ww -12930, stops 13.24(10.35), b5 66%, w2l 2 | n/a | n/a | n/a | n/a | -5741 (lots +133/wk) | n/a |
| M1_50_g10_c3_d10_c20_tb_B | -6442 $/wk, DD -17.1%, ww -12771, stops 13.24(10.35), b5 65%, w2l 2 | n/a | n/a | n/a | n/a | -6924 (lots +132/wk) | n/a |
| M1_50_g10_c1_d10_c15_tb_B | -6183 $/wk, DD -17.1%, ww -12274, stops 12.93(10.35), b5 61%, w2l 2 | -4229 $/wk, DD -17.1%, ww -12274, stops 11.34(10.99), b5 58%, w2l 2 | n/a | n/a | n/a | -6595 (lots +113/wk) | -4383 (lots +42/wk) |
| M1_50_g10_c1_d20_c20_tb_B | -2764 $/wk, DD -18.0%, ww -12011, stops 13.32(10.35), b5 68%, w2l 2 | -3931 $/wk, DD -18.0%, ww -12011, stops 11.49(10.99), b5 67%, w2l 2 | n/a | n/a | n/a | -3214 (lots +123/wk) | -4093 (lots +44/wk) |
| M1_50_g15_c3_d10_c20_tb_B | -9251 $/wk, DD -19.5%, ww -4726, stops 14.61(10.35), b5 55%, w2l 3 | -7725 $/wk, DD -19.5%, ww -4726, stops 12.25(10.99), b5 39%, w2l 3 | n/a | n/a | n/a | -9877 (lots +171/wk) | -7961 (lots +65/wk) |
| M1_50_g10_c1_d10_c20_tb_N | -3382 $/wk, DD -21.5%, ww -15200, stops 13.54(10.35), b5 68%, w2l 2 | -3388 $/wk, DD -21.5%, ww -15200, stops 13.01(10.99), b5 82%, w2l 3 | n/a | n/a | n/a | -3872 (lots +134/wk) | -3677 (lots +79/wk) |
| M1_50_g10_c1_d10_c20_tb_W | -2587 $/wk, DD -21.6%, ww -10267, stops 9.89(10.35), b5 96%, w2l 0 | n/a | n/a | n/a | n/a | -2574 (lots -4/wk) | n/a |
| M1_50_g10_c1_d10_c20_tb_B | -5789 $/wk, DD -22.3%, ww -15643, stops 12.86(10.35), b5 63%, w2l 2 | -3785 $/wk, DD -22.3%, ww -15643, stops 11.26(10.99), b5 61%, w2l 2 | n/a | n/a | n/a | -6262 (lots +129/wk) | -3971 (lots +51/wk) |
| M1_50_g10_c1_d10_c30_tb_B | -5789 $/wk, DD -22.3%, ww -15643, stops 12.86(10.35), b5 63%, w2l 2 | -3785 $/wk, DD -22.3%, ww -15643, stops 11.26(10.99), b5 61%, w2l 2 | n/a | n/a | n/a | -6262 (lots +129/wk) | -3971 (lots +51/wk) |
| M1_50_g10_c1_d10_c20_tb_B_x30 | -5789 $/wk, DD -22.3%, ww -15643, stops 12.86(10.35), b5 63%, w2l 2 | n/a | n/a | n/a | n/a | -6262 (lots +129/wk) | n/a |
| M1_50_g20_c3_d10_c20_tb_B | -13071 $/wk, DD -22.4%, ww +588, stops 16.59(10.35), b5 34%, w2l 4 | n/a | n/a | n/a | n/a | -13840 (lots +210/wk) | n/a |
| M1_50_g10_c1_d00_c20_tb_B | -5454 $/wk, DD -22.5%, ww -15727, stops 12.86(10.35), b5 62%, w2l 2 | n/a | n/a | n/a | n/a | -5919 (lots +127/wk) | n/a |
| M1_75_g15_c3_d10_c20_tb_B | -10376 $/wk, DD -35.5%, ww -21529, stops 15.29(10.35), b5 69%, w2l 3 | n/a | n/a | n/a | n/a | -10917 (lots +148/wk) | n/a |
| M2_75_g10_c1_d10_c20_tb_N | -7967 $/wk, DD -36.2%, ww -10331, stops 13.24(10.35), b5 55%, w2l 2 | n/a | n/a | n/a | n/a | -8358 (lots +107/wk) | n/a |
| M1_75_g15_c2_d10_c20_tb_B | -11877 $/wk, DD -36.6%, ww -20801, stops 14.46(10.35), b5 58%, w2l 3 | n/a | n/a | n/a | n/a | -12385 (lots +139/wk) | n/a |
| M1_75_g20_c1_d10_c20_tb_B | -5693 $/wk, DD -40.1%, ww -4920, stops 13.54(10.35), b5 72%, w2l 2 | n/a | n/a | n/a | n/a | -6280 (lots +160/wk) | n/a |
| M1_50_g20_c2_d10_c20_tb_B | -13270 $/wk, DD -52.1%, ww +1243, stops 14.84(10.35), b5 35%, w2l 4 | n/a | n/a | n/a | n/a | -14014 (lots +203/wk) | n/a |
| M1_75_g15_c1_d10_c20_tb_B | -10644 $/wk, DD -55.7%, ww -18061, stops 13.85(10.35), b5 58%, w2l 3 | n/a | n/a | n/a | n/a | -11127 (lots +132/wk) | n/a |
| M1_50_g20_c1_d10_c20_tb_B | -9929 $/wk, DD -56.4%, ww -4944, stops 14.23(10.35), b5 48%, w2l 3 | n/a | n/a | n/a | n/a | -10609 (lots +186/wk) | n/a |
| M1_75_g10_c2_d10_c20_t12_B | -8839 $/wk, DD -66.0%, ww -17822, stops 13.77(10.35), b5 77%, w2l 2 | n/a | n/a | n/a | n/a | -9085 (lots +67/wk) | n/a |
| M1_75_g10_c1_d10_c20_t12_N | -8364 $/wk, DD -75.2%, ww -17893, stops 14.15(10.35), b5 79%, w2l 2 | n/a | n/a | n/a | n/a | -8627 (lots +72/wk) | n/a |
| M1_75_g20_c2_d10_c20_tb_B | -10279 $/wk, DD -82.0%, ww -7613, stops 13.92(10.35), b5 64%, w2l 2 | -6163 $/wk, DD -97.4%, ww -7613, stops 12.63(10.99), b5 34%, w2l 2 | n/a | n/a | n/a | -10883 (lots +165/wk) | -6413 (lots +68/wk) |
| M1_75_g20_c3_d10_c20_tb_B | -13357 $/wk, DD -82.5%, ww -13297, stops 14.99(10.35), b5 61%, w2l 3 | n/a | n/a | n/a | n/a | -13963 (lots +166/wk) | n/a |

### Narrow-only and wide-only for the leading cells (item 8; same cell, half B / N / W)
| base cell | half | L3M | L6M |
|---|---|---|---|
| M1_75_g10_c1_d20_c20_tb | B | -1154 $/wk, DD +7.5%, ww +7015, stops 12.71(10.35), b5 79%, w2l 2 | n/a |
| M1_50_g00_c1_d10_c20_tb | B | +0 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a |

### Per book and per session (item 2): effect of the best whole-system cell on each book x session, and the best setting per book x session
Slice of the exact trade tables (books interact through day locks and caps, so single-book cells in the next table are the clean test). For every book x session the cell with the largest drawdown cut inside the tolerant mean gate in L3M (and in L6M when scored) is listed; "stays fixed" = no cell cuts drawdown inside the gate there.
| book | session | trades L3M | best cell | L3M | L6M | verdict |
|---|---|---|---|---|---|---|
| A7 | asia | 160 | M1_75_g10_c1_d10_c20_t08_N | +320 $/wk, DD +39.7%, ww +2974, stops 5.25(4.03), b5 6%, w2l 4 | n/a | L3M only |
| H7 | asia | 67 | none inside the gate | | | stays fixed (no cell cuts DD inside the gate) |
| H7 | nyam | 17 | M1_50_g10_c1_d00_c20_tb_B | +218 $/wk, DD +52.0%, ww +525, stops 0.15(0.38), b5 81%, w2l 0 | n/a | L3M only |
| K7 | asia | 333 | none inside the gate | | | stays fixed (no cell cuts DD inside the gate) |
| K7 | london | 210 | M1_75_g10_c1_d10_c20_t12_N | +773 $/wk, DD +24.7%, ww +5048, stops 0.30(0.30), b5 82%, w2l 1 | n/a | L3M only |
| K7 | nyam | 88 | M1_75_g10_c1_d10_c20_t08_N | +1035 $/wk, DD +78.5%, ww +2161, stops 0.00(0.00), b5 39%, w2l 1 | n/a | L3M only |
| K7 | nypm | 56 | none inside the gate | | | stays fixed (no cell cuts DD inside the gate) |
| M7 | london | 248 | M1_50_g15_c2_d10_c20_tb_B | +354 $/wk, DD +10.5%, ww +6438, stops 1.37(0.91), b5 89%, w2l 0 | n/a | L3M only |
| M7 | nyam | 88 | M1_75_g20_c1_d10_c20_tb_B | +242 $/wk, DD +52.6%, ww +1195, stops 0.30(0.23), b5 35%, w2l 0 | n/a | L3M only |
| P7 | asia | 243 | none inside the gate | | | stays fixed (no cell cuts DD inside the gate) |
| P7 | london | 166 | M1_50_g15_c2_d10_c20_tb_B | +619 $/wk, DD +45.5%, ww +3969, stops 0.15(0.08), b5 74%, w2l 1 | n/a | L3M only |
| P7 | nyam | 58 | M1_75_g10_c1_d10_h_tb_B | +1753 $/wk, DD +74.0%, ww +3339, stops 0.08(0.38), b5 38%, w2l 1 | n/a | L3M only |
| U7 | asia | 72 | M1_75_g10_c1_d20_c20_tb_B | +515 $/wk, DD +19.6%, ww +983, stops 1.98(1.83), b5 92%, w2l 2 | n/a | L3M only |
| U7 | london | 49 | none inside the gate | | | stays fixed (no cell cuts DD inside the gate) |

Single-book and book x session cells (wave 3, clean test of item 2; same config as the wave-2 best; vs JN05W2 on the same book/session slice):
| cell | slice | L3M | L6M |
|---|---|---|---|

### Leads (tolerant gate in every scored window incl. L3M and L6M, DD cut > 0 in some window)
| cell | scope | L6M DD cut % | L6M d mean | windows | W44 removed L3M / L6M |
|---|---|---|---|---|---|
| none | | | | | |

### Placebos beside the finalists (forecast shifted 11 / 23 / 37 sessions at the same clock; random other session at the same clock), scope all, L6M (a real lead must beat all of them)
| finalist | real | pl11 | pl23 | pl37 | random |
|---|---|---|---|---|---|
| M1_75_g10_c1_d20_c20_tb_B | -1154 $/wk, DD +7.5%, ww +7015, stops 12.71(10.35), b5 79%, w2l 2 | pending | pending | pending | pending |
| M1_75_g10_c1_d10_c20_t08_N | -4047 $/wk, DD +3.0%, ww +9786, stops 12.48(10.35), b5 66%, w2l 2 | pending | pending | pending | pending |
| M1_75_g10_c1_d10_c15_tb_N | -288 $/wk, DD +0.1%, ww +154, stops 13.85(10.35), b5 74%, w2l 2 | pending | pending | pending | pending |

### Combined with the chop call and the trend-day call (item 7)
| cell | mode | L3M | L6M |
|---|---|---|---|

### FOR THE LIVE BUILD: what D7 needs at the signal second
1. Own 1-minute NQ bars only (closed bars up to the signal second): range and realised vol of the last 15/30/60/120 min; the same offset-into-session range over the previous 20 sessions (median); the range of the previous 5 and 20 sessions of the same session type; range so far in the current session; last close. D7 computes all of these itself from its own bars (preferred). 2. A small coefficient table (per session: 14 weights, mean, sd, intercept for the median-horizon and 75th-pct models) plus per book+session H50/H75 and ref EM, refit every 14 days: a static file pushed from the box every 2 weeks (the only file). 3. Nothing intraday from the box for M1. M2 (T-RANGE2 session forecast + calendar flags) needs the T-RANGE2 file and the event calendar at the session start: ranks below an equal M1 version. 4. The chop-call and trend-day cells additionally need those call files (not computable from D7 bars alone): rank below the bars-only version.

### Reading
Drawdown first; a result needs the gate in recent AND older windows and has to beat the placebos. Cells that cut drawdown only through L3M, or only with full stops up, are not leads. Expected move forecast quality (table above) is a forecasting result scored on all 43 months; the exact cells decide whether it makes a better bracket. No PASS claim.
