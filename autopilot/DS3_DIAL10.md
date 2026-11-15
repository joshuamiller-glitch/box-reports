## Dial 10: trade-horizon bracket
**VERDICT (plain, not a PASS): 7 of 35 registered cells scored through L3M, 0 through L6M, 0 through HOLD; 0 (cell,scope) leads pass the tolerant gate in every scored window (0 at scope all) - before placebo. Best L3M cell inside the mean gate: M1_50_g00_c1_d10_c20_tb_B (DD +0.0%, +0 $/wk).**

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
| g=1.5 | 3 | -19.5 | -9251 | -7278 | +3.65 | n/a |
| g=2.0 | 3 | -40.1 | -9929 | -4920 | +3.88 | n/a |
| clip=1 | 5 | -40.1 | -5693 | -4944 | +3.50 | n/a |
| clip=3 | 2 | -21.0 | -11161 | -2069 | +5.25 | n/a |
| tag=50 | 5 | -19.5 | -9251 | -4726 | +3.88 | n/a |
| tag=75 | 2 | -47.9 | -8168 | -11490 | +3.35 | n/a |
| db=10 | 7 | -22.4 | -9251 | -4920 | +3.65 | n/a |
| lots=c20 | 7 | -22.4 | -9251 | -4920 | +3.65 | n/a |
| tr=b | 7 | -22.4 | -9251 | -4920 | +3.65 | n/a |
| half=B | 7 | -22.4 | -9251 | -4920 | +3.65 | n/a |
| fc=M1 | 7 | -22.4 | -9251 | -4920 | +3.65 | n/a |

### Per cell, scope all (sorted by L3M drawdown cut; L6M, HOLD, GAP/MID and PRE when present)
| cell | L3M | L6M | HOLD | MID(GAP) | PRE | d mean/wk at $4.84 L3M | at $4.84 L6M |
|---|---|---|---|---|---|---|---|
| M1_50_g00_c1_d10_c20_tb_B | +0 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +0 (lots +0/wk) | n/a |
| M1_50_g15_c1_d10_c20_tb_B | -4393 $/wk, DD -16.7%, ww -7278, stops 14.00(10.35), b5 74%, w2l 3 | n/a | n/a | n/a | n/a | -4996 (lots +165/wk) | n/a |
| M1_50_g15_c3_d10_c20_tb_B | -9251 $/wk, DD -19.5%, ww -4726, stops 14.61(10.35), b5 55%, w2l 3 | n/a | n/a | n/a | n/a | -9877 (lots +171/wk) | n/a |
| M1_50_g20_c3_d10_c20_tb_B | -13071 $/wk, DD -22.4%, ww +588, stops 16.59(10.35), b5 34%, w2l 4 | n/a | n/a | n/a | n/a | -13840 (lots +210/wk) | n/a |
| M1_75_g20_c1_d10_c20_tb_B | -5693 $/wk, DD -40.1%, ww -4920, stops 13.54(10.35), b5 72%, w2l 2 | n/a | n/a | n/a | n/a | -6280 (lots +160/wk) | n/a |
| M1_75_g15_c1_d10_c20_tb_B | -10644 $/wk, DD -55.7%, ww -18061, stops 13.85(10.35), b5 58%, w2l 3 | n/a | n/a | n/a | n/a | -11127 (lots +132/wk) | n/a |
| M1_50_g20_c1_d10_c20_tb_B | -9929 $/wk, DD -56.4%, ww -4944, stops 14.23(10.35), b5 48%, w2l 3 | n/a | n/a | n/a | n/a | -10609 (lots +186/wk) | n/a |

### Narrow-only and wide-only for the leading cells (item 8; same cell, half B / N / W)
| base cell | half | L3M | L6M |
|---|---|---|---|
| M1_50_g00_c1_d10_c20_tb | B | +0 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a |
| M1_50_g15_c1_d10_c20_tb | B | -4393 $/wk, DD -16.7%, ww -7278, stops 14.00(10.35), b5 74%, w2l 3 | n/a |
| M1_50_g15_c3_d10_c20_tb | B | -9251 $/wk, DD -19.5%, ww -4726, stops 14.61(10.35), b5 55%, w2l 3 | n/a |
| M1_50_g20_c3_d10_c20_tb | B | -13071 $/wk, DD -22.4%, ww +588, stops 16.59(10.35), b5 34%, w2l 4 | n/a |
| M1_75_g20_c1_d10_c20_tb | B | -5693 $/wk, DD -40.1%, ww -4920, stops 13.54(10.35), b5 72%, w2l 2 | n/a |
| M1_75_g15_c1_d10_c20_tb | B | -10644 $/wk, DD -55.7%, ww -18061, stops 13.85(10.35), b5 58%, w2l 3 | n/a |

### Per book and per session (item 2): effect of the best whole-system cell on each book x session, and the best setting per book x session
Slice of the exact trade tables (books interact through day locks and caps, so single-book cells in the next table are the clean test). For every book x session the cell with the largest drawdown cut inside the tolerant mean gate in L3M (and in L6M when scored) is listed; "stays fixed" = no cell cuts drawdown inside the gate there.
| book | session | trades L3M | best cell | L3M | L6M | verdict |
|---|---|---|---|---|---|---|
| A7 | asia | 160 | M1_75_g15_c1_d10_c20_tb_B | +432 $/wk, DD +32.8%, ww +1550, stops 5.71(4.03), b5 46%, w2l 2 | n/a | L3M only |
| H7 | asia | 67 | none inside the gate | | | stays fixed (no cell cuts DD inside the gate) |
| H7 | nyam | 17 | M1_50_g15_c1_d10_c20_tb_B | +63 $/wk, DD +38.1%, ww +458, stops 0.30(0.38), b5 67%, w2l 0 | n/a | L3M only |
| K7 | asia | 333 | none inside the gate | | | stays fixed (no cell cuts DD inside the gate) |
| K7 | london | 210 | none inside the gate | | | stays fixed (no cell cuts DD inside the gate) |
| K7 | nyam | 88 | M1_50_g15_c3_d10_c20_tb_B | +1007 $/wk, DD +67.3%, ww +2237, stops 0.00(0.00), b5 64%, w2l 1 | n/a | L3M only |
| K7 | nypm | 56 | none inside the gate | | | stays fixed (no cell cuts DD inside the gate) |
| M7 | london | 248 | M1_50_g15_c3_d10_c20_tb_B | +153 $/wk, DD +14.2%, ww +6438, stops 1.07(0.91), b5 77%, w2l 0 | n/a | L3M only |
| M7 | nyam | 88 | M1_50_g15_c3_d10_c20_tb_B | +121 $/wk, DD +73.4%, ww +2536, stops 0.38(0.23), b5 53%, w2l 1 | n/a | L3M only |
| P7 | asia | 243 | none inside the gate | | | stays fixed (no cell cuts DD inside the gate) |
| P7 | london | 166 | M1_50_g15_c1_d10_c20_tb_B | +628 $/wk, DD +34.3%, ww +1543, stops 0.15(0.08), b5 80%, w2l 1 | n/a | L3M only |
| P7 | nyam | 58 | none inside the gate | | | stays fixed (no cell cuts DD inside the gate) |
| U7 | asia | 72 | none inside the gate | | | stays fixed (no cell cuts DD inside the gate) |
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
| M1_50_g00_c1_d10_c20_tb_B | +0 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | pending | pending | pending | pending |
| M1_50_g15_c1_d10_c20_tb_B | -4393 $/wk, DD -16.7%, ww -7278, stops 14.00(10.35), b5 74%, w2l 3 | pending | pending | pending | pending |
| M1_50_g15_c3_d10_c20_tb_B | -9251 $/wk, DD -19.5%, ww -4726, stops 14.61(10.35), b5 55%, w2l 3 | pending | pending | pending | pending |

### Combined with the chop call and the trend-day call (item 7)
| cell | mode | L3M | L6M |
|---|---|---|---|

### FOR THE LIVE BUILD: what D7 needs at the signal second
1. Own 1-minute NQ bars only (closed bars up to the signal second): range and realised vol of the last 15/30/60/120 min; the same offset-into-session range over the previous 20 sessions (median); the range of the previous 5 and 20 sessions of the same session type; range so far in the current session; last close. D7 computes all of these itself from its own bars (preferred). 2. A small coefficient table (per session: 14 weights, mean, sd, intercept for the median-horizon and 75th-pct models) plus per book+session H50/H75 and ref EM, refit every 14 days: a static file pushed from the box every 2 weeks (the only file). 3. Nothing intraday from the box for M1. M2 (T-RANGE2 session forecast + calendar flags) needs the T-RANGE2 file and the event calendar at the session start: ranks below an equal M1 version. 4. The chop-call and trend-day cells additionally need those call files (not computable from D7 bars alone): rank below the bars-only version.

### Reading
Drawdown first; a result needs the gate in recent AND older windows and has to beat the placebos. Cells that cut drawdown only through L3M, or only with full stops up, are not leads. Expected move forecast quality (table above) is a forecasting result scored on all 43 months; the exact cells decide whether it makes a better bracket. No PASS claim.
