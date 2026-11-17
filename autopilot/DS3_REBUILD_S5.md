# DS3_REBUILD_S5 - T-REBUILD stage 5: leave-one-out audit of every live layer on JL2 (W-S5). REAL NUMBERS, FIRST PASS
VERDICT (data ends 2026-10-30; FIRST PASS 2026-11-17T01:39Z; REAL numbers from the landed engine cells: 30 TL3_RB_S5 sets x 43 months, leave-one-out on JL2, week/day arithmetic, no engine run, ulcer index primary): KEEP (10): L2GATE (ulcer +49.0%, mean -1,716/wk base, P(helps) 1.00); NTZ (ulcer +22.6%, mean -136/wk base, P(helps) 0.97); F3CTXCUT (ulcer +19.3%, mean +325/wk base, P(helps) 0.93); ERLADDER (ulcer +16.4%, mean -1,301/wk base, P(helps) 0.92); STACKCAP (ulcer +14.6%, mean -273/wk base, P(helps) 0.96); CUTLINE_P7 (ulcer +10.2%, mean +621/wk base, P(helps) 0.88); SIGQ (ulcer +6.8%, mean -259/wk base, P(helps) 0.80); BREADTH (ulcer +4.9%, mean +368/wk base, P(helps) 0.88); BLACKOUT (ulcer +2.0%, mean +103/wk base, P(helps) 0.47); CUTLINE_U7 (ulcer +1.8%, mean +172/wk base, P(helps) 0.81). COSTS MONEY (4): LOT (ulcer -0.4%, mean -1,868/wk base, P(helps) 0.59); ADD_P7FLAT42 (ulcer -8.7%, mean -442/wk base, P(helps) 0.09); GIVEBACKLOCK (ulcer +0.5%, mean -371/wk base, P(helps) 0.26); DAYCAPS (ulcer -4.5%, mean -296/wk base, P(helps) 0.08). NOT DISTINGUISHABLE but RECENT-LEANING in L6M (10): A06, ATRSKIP, CUTLINE_H7, CUTLINE_M7, CUTLINE_O7, DAYDONE, GOVERNOR, K7FLAT45, STACKCUT, STATECUT_ALL. NOT DISTINGUISHABLE (6): B02, CUTLINE_A7, CUTLINE_K7, OTE62, P7CONFIRM, REG.

> VALIDATION (desk standard, W-S5, FIRST PASS, written 2026-11-17T01:39Z): trials counted = 30 layer cells (22 layer-off + 7 per-book cut-line-off + 1 add), each reported, no best-of selection (ledger family RB5); correction = Benjamini-Hochberg 10% across the 30 on the ALL43 week-clustered bootstrap (survivors below) plus percentile among 200 matched persistent-draw random-removal controls for skip-type layers and the calibrated ulcer-primary tiers (cutoffs_ulc.json TUNED: conf_hi 0.85, conf_other 0.25, conf_pdd 0.80, conf_old 0.25, lead 0.75/0.25); PBO not applicable (nothing fitted here); numbers are IN-SAMPLE (every layer was fitted or chosen on this same history), NOT walk-forward, NOT untouched. Dollars: engine BASE lots with engine fee $1.18/contract RT; x1.75 = live lots max(1,floor(1.75*base+0.5)) per trade; $4.84 = base lots with the fee repriced (net - 3.66 x lots).

## When the first numbers landed and what is missing
- All 30 TL3_RB_S5_* cells and the 10 TL3_RB_S0_* raw books had landed by 2026-11-16 (S5 cells 43/43 months for 28 sets; the first S5 cell dir was written 2026-11-16 18:47Z, the page is built 2026-11-17 01:39). This is the first page with real stage-5 numbers (the 18:00Z page was design only).
- Months missing: TL3_RB_S5_F3CTXCUT: [202403] (S5), TL3_RB_S0_U7: 202309 (S0). For F3CTXCUT the month 202403 is dropped from BOTH cells (days of that month removed from every X' / ALL43 calendar), so its X' and ALL43 rows are 42 months. 1,289 of 1,290 S5 cell-months done.
- Identity: TL3_EV_LY_ID (JL2 + inert switches) 202610 equals JL2 202610 (642 trades, net 27,487.58, checked); the W2 identity cell was not re-checked here. W-EV had not posted IDENTICAL on a page; if W-EV later reports a mismatch every row below is void.
- Scope check on the base: ATRSKIP is P7-only in the engine too (1,577 of the 1,660 trades it removes are P7; the rest are path effects on other books), as live. STACKCUT leave-one-out uses ev_layers stack_cut=off; JL2 default is Asia-only = live.

## What is NOT modelled (honest list)
- NKD take P7/U7 at 0.80: not in JL2 and not in any S5 cell (no NKD book data on the box) - its value is UNKNOWN here.
- Profit-side lines (K7 delta_mult lock, M7 tot_rel step, U7 delta_mult tighten): absent from JL2 (inert); no leave-one-out exists.
- Session lot tables (they are the entry gate; 0 = no entry): no leave-one-out defined, not run. P7 day cap 8,400 is inside the DAYCAPS cell with the other book day caps (not separable).
- P7 flat -42: live since 11-12, not in JL2: shown as an ADD cell (on = JL2 + flat -42, off = JL2); its sign is opposite to the others in the "cell" sense but the table value is still ON minus OFF.
- Live-vs-engine: ev_layers defaults (NTZ, A06, B02, OTE62, ER ladder, give-back lock, L2 gate, P7 confirmation) are engine layers; the live status of each was not in ANSWER_LIVE_LAYERS_20261116.md, they are listed as engine layers. The engine L2-gate was void live (DS3_ENGINE_VS_LIVE section 14).

## Base used by every comparison
Every stage-5 row compares JL2 = TL3_EV_JN05W2JL2 (layers ON, 18,979 trades, 43 months) with a JL2 copy with ONE layer switched off (leave-one-out), both re-run through the exact engine, so a row includes the freed-book / path effects. Raw S0 (no layers, one book alone) is a different base and is used only in the S0 section at the end. "Value of the layer" = ON minus OFF: ulcer cut by layer (positive = the layer lowers the ulcer index), DD cut, worst-week change and mean change per week (negative mean = the layer costs money). Ulcer index = RMS of the daily drawdown of the cumulative daily P&L in the window (Globex day = exit time ET + 6h). Windows: HOLD = 2025-11..2026-04 (26 weeks), L6M = 2026-05..10, L3M = 2026-08..10, GAP = 2025-07..09, PREUW = 2024-10..2025-06, X' = 2023-04..2024-09, ALL43 = 2023-04..2026-10 (windows overlap: ALL43 contains all others; HOLD+GAP+L6M are not contiguous: 2025-10 sits between GAP and HOLD).

## Table 1 - value of each layer: ulcer cut by layer (%, positive = helps) / change in mean $/wk (BASE lots; ON minus OFF; negative = costs money), per window
Sorted by ALL43 ulcer cut. Verdict rule: KEEP = ALL43 P(layer helps ulcer) >= 0.80, or ALL43 90% interval of the mean change > 0, or tier CONFIRMED/LEAD against matched controls, and not (P(helps ulcer) <= 0.20); COSTS MONEY = ulcer worse with P(helps) <= 0.20, or the 90% interval of the mean change entirely below 0, or P(mean change > 0) <= 0.10 with P(helps ulcer) < 0.80; otherwise NOT DISTINGUISHABLE, with the 80%-power mean floor (2.49 x SE; at the pass-rule calibration ulcer cuts of 5/10/20% were detected 49/72/97% of the time on 12 months, so a small ulcer effect in a 3-6 month window is below the power floor).

| layer | status | verdict | L3M | L6M | HOLD | GAP | PREUW | X' | ALL43 |
|--|--|--|--|--|--|--|--|--|--|
| L2GATE | engine layer (live status not in ANSWER_LIVE_LAYERS) | KEEP (ulcer P=1.00); NOTE live L2 gate was void (DS3_ENGINE_VS_LIVE sec 14): engine value not transferable to live | +70.6% / +4,652 | +72.9% / +2,399 | +52.0% / +320 | +47.1% / -1,707 | -36.1% / -8,500 | +58.9% / -979 | +49.0% / -1,716 |
| NTZ | live (half size within 20 pts) | KEEP (ulcer P=0.97) | +11.9% / +2,097 | +10.0% / +196 | +23.8% / -51 | +2.9% / -2,116 | +8.1% / -2,023 | +33.3% / +981 | +22.6% / -136 |
| F3CTXCUT | engine layer (live status not in ANSWER_LIVE_LAYERS) | KEEP (ulcer P=0.93) | +29.9% / +1,042 | +24.4% / +1,706 | +20.0% / +852 | +6.1% / -1,806 | -58.1% / -1,947 | +35.8% / +1,282 | +19.3% / +325 |
| ERLADDER | engine layer (live status not in ANSWER_LIVE_LAYERS) | KEEP (ulcer P=0.92); costs mean | +21.0% / -4,823 | +38.7% / -2,811 | +26.8% / +773 | +23.7% / -3,524 | -30.3% / -1,905 | +22.6% / -1,098 | +16.4% / -1,301 |
| STACKCAP | live (JN04 cap; JL2 = 6 engine lots = 10 live, London) | KEEP (ulcer P=0.96) | +12.3% / -325 | +9.9% / -437 | +14.1% / -274 | -1.0% / -1,036 | +5.7% / -1,470 | +22.7% / +555 | +14.6% / -273 |
| CUTLINE_P7 | live (loss cut, P7 book line) | KEEP (ulcer P=0.88) | +18.9% / +2,204 | +21.4% / +3,983 | +26.9% / +1,416 | +1.1% / -1,196 | -23.5% / -1,732 | +11.9% / +778 | +10.2% / +621 |
| REG | live (JN04 REG, P7) | NOT DISTINGUISHABLE (ALL43 mean MDE 80% power 613 $/wk base; L6M 2390) | +3.8% / -389 | +9.1% / +671 | +6.4% / -1,095 | +4.9% / +357 | +12.8% / -345 | +11.9% / -224 | +10.1% / -212 |
| SIGQ | live (JN04 SIGQ, P7) | KEEP (ulcer P=0.80) | +13.6% / -278 | +16.9% / -456 | +9.1% / -457 | +6.9% / +123 | +8.9% / -782 | +3.1% / -140 | +6.8% / -259 |
| BREADTH | live (P7 15 min) | KEEP (ulcer P=0.88) | +49.1% / +3,698 | +42.1% / +2,005 | +6.7% / -2 | +0.9% / -1,578 | -7.2% / -693 | +8.1% / +704 | +4.9% / +368 |
| A06 | engine layer (live status not in ANSWER_LIVE_LAYERS) | NOT DISTINGUISHABLE (ALL43 mean MDE 80% power 525 $/wk base; L6M 1985); RECENT-LEANING: L6M ulcer +2.9% P(helps)=0.87, older windows do not carry it | +0.1% / -1,531 | +2.9% / -523 | +7.5% / -309 | -1.4% / -1,290 | +7.5% / +349 | -2.6% / -223 | +3.5% / -262 |
| DAYDONE | live (C22) | NOT DISTINGUISHABLE (ALL43 mean MDE 80% power 657 $/wk base; L6M 2639); RECENT-LEANING: L6M ulcer +33.8% P(helps)=0.91, older windows do not carry it | +40.0% / +3,216 | +33.8% / +2,555 | +15.4% / +624 | +0.4% / -274 | -1.1% / +306 | -3.7% / -191 | +3.5% / +413 |
| ATRSKIP | live (P7, atr_rel>=1.6) | NOT DISTINGUISHABLE (ALL43 mean MDE 80% power 823 $/wk base; L6M 2303); RECENT-LEANING: L6M ulcer +16.1% P(helps)=0.85, older windows do not carry it | +1.0% / -476 | +16.1% / +1,102 | +8.7% / +469 | -2.1% / -2,333 | -25.6% / -827 | +12.7% / -575 | +2.8% / -359 |
| CUTLINE_M7 | live (loss cut, M7 book line) | NOT DISTINGUISHABLE (ALL43 mean MDE 80% power 718 $/wk base; L6M 2059); RECENT-LEANING: L6M ulcer +4.6% P(helps)=0.92, older windows do not carry it | +8.0% / +1,098 | +4.6% / +333 | +10.9% / -393 | -5.0% / -1,792 | -16.0% / -236 | +10.3% / +238 | +2.6% / -68 |
| P7CONFIRM | engine layer (live status not in ANSWER_LIVE_LAYERS) | NOT DISTINGUISHABLE (ALL43 mean MDE 80% power 275 $/wk base; L6M 911) | +1.3% / +53 | +0.7% / +194 | +1.6% / +178 | +7.5% / +251 | +2.2% / -414 | +2.4% / -76 | +2.6% / -41 |
| BLACKOUT | live (P7 30 min) | KEEP (tier CONFIRMED) | +9.9% / +529 | +7.7% / +771 | +6.1% / +89 | -0.0% / -153 | +3.6% / -12 | -1.1% / +23 | +2.0% / +103 |
| CUTLINE_U7 | live (loss cut, U7 book line) | KEEP (ulcer P=0.81) | +7.4% / +1,161 | +7.5% / +1,022 | +6.4% / +420 | +2.1% / -666 | -1.8% / +15 | +1.0% / +17 | +1.8% / +172 |
| GIVEBACKLOCK | engine layer (live status not in ANSWER_LIVE_LAYERS) | COSTS MONEY | +1.3% / -173 | +2.9% / -405 | -4.7% / -1,178 | +0.5% / -372 | +5.2% / +59 | -1.1% / -277 | +0.5% / -371 |
| GOVERNOR | live (WL_E1 new evidence, P7) | NOT DISTINGUISHABLE (ALL43 mean MDE 80% power 233 $/wk base; L6M 1130); RECENT-LEANING: L6M ulcer +6.4% P(helps)=0.80, older windows do not carry it | +2.4% / -230 | +6.4% / +393 | +1.4% / +45 | +0.0% / +0 | -2.3% / -33 | +0.0% / +0 | -0.2% / +55 |
| LOT | live (JN04 LOT, P7) | COSTS MONEY | +14.3% / -440 | +10.9% / -3,596 | -4.2% / -1,540 | -0.4% / -1,655 | +5.3% / -2,400 | -3.2% / -1,462 | -0.4% / -1,868 |
| CUTLINE_O7 | live (loss cut, O7 book line) | NOT DISTINGUISHABLE (ALL43 mean MDE 80% power 91 $/wk base; L6M 70); RECENT-LEANING: L6M ulcer +0.5% P(helps)=0.94, older windows do not carry it | +0.7% / +116 | +0.5% / +91 | +0.1% / -14 | +0.2% / -88 | -1.9% / -38 | +0.4% / -44 | -0.4% / -17 |
| STACKCUT | live (50% Asia-only) | NOT DISTINGUISHABLE (ALL43 mean MDE 80% power 512 $/wk base; L6M 1948); RECENT-LEANING: L6M ulcer +10.7% P(helps)=0.81, older windows do not carry it | +15.8% / -197 | +10.7% / -398 | +1.4% / +543 | +5.8% / -475 | -16.5% / -729 | +6.4% / +90 | -0.4% / -198 |
| B02 | engine layer (live status not in ANSWER_LIVE_LAYERS) | NOT DISTINGUISHABLE (ALL43 mean MDE 80% power 132 $/wk base; L6M 375) | +1.8% / -75 | +1.3% / +34 | -0.1% / -93 | +0.0% / +58 | -1.5% / -314 | -0.1% / +67 | -0.5% / -54 |
| CUTLINE_A7 | live (loss cut, A7 book line) | NOT DISTINGUISHABLE (ALL43 mean MDE 80% power 173 $/wk base; L6M 982) | -8.8% / -418 | +0.4% / +191 | -3.7% / -129 | +0.0% / +105 | -1.6% / -201 | -0.4% / -32 | -1.2% / -35 |
| CUTLINE_H7 | live (loss cut, H7 book line) | NOT DISTINGUISHABLE (ALL43 mean MDE 80% power 425 $/wk base; L6M 1735); RECENT-LEANING: L6M ulcer +11.3% P(helps)=0.94, older windows do not carry it | +11.3% / +418 | +11.3% / +16 | +2.7% / +172 | +8.6% / +556 | -10.6% / -463 | -3.1% / +67 | -2.8% / -34 |
| STATECUT_ALL | live (loss cut, all book cut lines together) | NOT DISTINGUISHABLE (ALL43 mean MDE 80% power 1077 $/wk base; L6M 4191); RECENT-LEANING: L6M ulcer +28.7% P(helps)=1.00, older windows do not carry it | +35.6% / +5,079 | +28.7% / +2,132 | +8.6% / -802 | -5.1% / -2,475 | -44.7% / -267 | +5.6% / -101 | -3.1% / -108 |
| OTE62 | engine layer (live status not in ANSWER_LIVE_LAYERS) | NOT DISTINGUISHABLE (ALL43 mean MDE 80% power 546 $/wk base; L6M 1553) | +2.9% / +912 | +4.7% / +833 | -2.1% / +222 | -0.8% / -139 | -11.3% / +55 | -0.3% / +169 | -3.7% / +311 |
| DAYCAPS | engine layer (live status not in ANSWER_LIVE_LAYERS) | COSTS MONEY (ulcer worse P(helps)=0.08) | -0.5% / -1,475 | +2.3% / -351 | -2.4% / -320 | -0.9% / -403 | -10.5% / -575 | -2.0% / -175 | -4.5% / -296 |
| CUTLINE_K7 | live (loss cut, K7 book line) | NOT DISTINGUISHABLE (ALL43 mean MDE 80% power 614 $/wk base; L6M 2463) | -3.2% / +982 | -1.8% / +401 | +2.8% / -728 | -14.3% / -832 | -12.7% / -45 | -3.4% / -252 | -5.3% / -234 |
| ADD_P7FLAT42 | live since 11-12, NOT in JL2: ADD cell (on = JL2 + flat -42) | COSTS MONEY (ulcer worse P(helps)=0.09) | -20.0% / -1,242 | -12.6% / -669 | +9.4% / +376 | +2.0% / +577 | +13.5% / +289 | -34.4% / -1,135 | -8.7% / -442 |
| K7FLAT45 | live (K7 flat -45) | NOT DISTINGUISHABLE (ALL43 mean MDE 80% power 932 $/wk base; L6M 2609); RECENT-LEANING: L6M ulcer +13.2% P(helps)=0.88, older windows do not carry it | +17.0% / +900 | +13.2% / +1,298 | +13.1% / +105 | -32.4% / -1,224 | -27.8% / -879 | -19.4% / -496 | -12.0% / -272 |

## Headline lists
- KEEP: L2GATE, NTZ, F3CTXCUT, ERLADDER, STACKCAP, CUTLINE_P7, SIGQ, BREADTH, BLACKOUT, CUTLINE_U7
- COSTS MONEY: LOT, ADD_P7FLAT42, GIVEBACKLOCK, DAYCAPS
- NOT DISTINGUISHABLE, recent-leaning: A06, ATRSKIP, CUTLINE_H7, CUTLINE_M7, CUTLINE_O7, DAYDONE, GOVERNOR, K7FLAT45, STACKCUT, STATECUT_ALL
- NOT DISTINGUISHABLE: B02, CUTLINE_A7, CUTLINE_K7, OTE62, P7CONFIRM, REG
- INERT: none
- BH 10% survivors on ALL43 (30 tests): mean change != 0: LOT; ulcer helped: L2GATE.
- Mean floor (80% power, ALL43): A06 525, ADD_P7FLAT42 623, ATRSKIP 823, B02 132, BLACKOUT 500, BREADTH 1,121, CUTLINE_A7 173, CUTLINE_H7 425, CUTLINE_K7 614, CUTLINE_M7 718, CUTLINE_O7 91, CUTLINE_P7 1,345, CUTLINE_U7 320, DAYCAPS 357, DAYDONE 657, ERLADDER 1,881, F3CTXCUT 1,129, GIVEBACKLOCK 394, GOVERNOR 233, K7FLAT45 932, L2GATE 3,600, LOT 966, NTZ 1,129, OTE62 546, P7CONFIRM 275, REG 613, SIGQ 818, STACKCAP 701, STACKCUT 512, STATECUT_ALL 1,077 $/wk base. JL2 earns about 8,796 $/wk base over ALL43.

## Table 2 - matched random-removal controls for skip-type layers (persistent draw, one uniform per 5-minute bucket per book and side, bucket=300 s)
Control = the OFF cell (layer off) with a random set of trades removed in the layer's own book x session scope, same share (realised within 0.05 absolute AND 25% relative, else redrawn, redraws shown), 200 draws; percentile = share of controls the real ON cell beats (higher = better). PATH ARITHMETIC: controls remove trades without the freed-book replacement that the real ON cell contains (conservative for a skip layer, as in DS3_PASS_RULE). Layers that shrink or re-time instead of skip (state cuts, flats, LOT/SIGQ/REG, STACKCUT, locks, NTZ-size etc.) and layers that shift entry time (P7CONFIRM, L2GATE) have NO valid control here: a random-exit control needs engine cells (not run). NTZ and STACKCUT are partly size layers: NTZ treated as skip-type by the code only because its OFF cell has more trades; read its row with care.

| layer (skip-type) | scope (books; sessions 0 asia 1 london 3 nyam 4 nypm) | real share | control share mean (sd) | tol | redraws | valid | pct ulcer L6M / L3M / HOLD / GAP / PREUW / X' | pct mean L6M / L3M / HOLD | pct max DD L6M / L3M / HOLD | P(helps ulcer) L6M / ALL43 | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|
| ATRSKIP | P7; [3, 0, 1] | 0.320 | 0.320 (0.007) | 0.050 | 0 | yes | 0.96 / 0.77 / 0.71 / 0.25 / 0.02 / 0.95 | 1.00 / 0.93 / 0.92 | 0.99 / 0.89 / 0.63 | 0.85 / 0.78 | FAIL |
| BLACKOUT | P7; [1, 0] | 0.086 | 0.085 (0.005) | 0.021 | 0 | yes | 0.96 / 0.91 / 0.79 / 0.38 / 0.43 / 0.54 | 0.99 / 0.88 / 0.79 | 0.99 / 0.99 / 0.77 | 0.82 / 0.47 | CONFIRMED |
| BREADTH | P7; [1, 0] | 0.344 | 0.344 (0.009) | 0.050 | 0 | yes | 0.99 / 0.99 / 0.58 / 0.33 / 0.24 / 0.82 | 1.00 / 1.00 / 0.87 | 0.99 / 0.99 / 0.46 | 0.61 / 0.88 | FAIL |
| DAYCAPS | K7,M7,P7; [1, 4, 3, 0] | 0.021 | 0.021 (0.001) | 0.005 | 0 | yes | 0.76 / 0.49 / 0.38 / 0.28 / 0.07 / 0.42 | 0.52 / 0.07 / 0.43 | 0.62 / 0.60 / 0.46 | 0.61 / 0.08 | FAIL |
| DAYDONE | K7,M7; [3, 1, 4] | 0.121 | 0.122 (0.004) | 0.030 | 0 | yes | 1.00 / 1.00 / 0.93 / 0.22 / 0.38 / 0.42 | 1.00 / 1.00 / 0.74 | 1.00 / 1.00 / 0.99 | 0.91 / 0.66 | FAIL |
| GIVEBACKLOCK | K7; [4, 1, 3, 0] | 0.045 | 0.045 (0.002) | 0.011 | 0 | yes | 0.80 / 0.56 / 0.09 / 0.38 / 0.77 / 0.34 | 0.30 / 0.49 / 0.00 | 0.65 / 0.65 / 0.36 | 0.68 / 0.26 | FAIL |
| GOVERNOR | K7,P7; [0, 1, 4] | 0.006 | 0.006 (0.001) | 0.002 | 2 | yes | 1.00 / 0.89 / 0.69 / 0.43 / 0.17 / 0.56 | 0.99 / 0.30 / 0.59 | 0.96 / 0.96 / 0.48 | 0.80 / 0.49 | FAIL |
| NTZ | K7,M7,P7; [1, 0] | 0.081 | 0.081 (0.003) | 0.020 | 0 | yes | 0.88 / 0.88 / 1.00 / 0.41 / 0.61 / 1.00 | 0.93 / 1.00 / 0.75 | 0.99 / 0.98 / 0.93 | 0.39 / 0.97 | FAIL |
| P7CONFIRM | P7; [3] | 0.956 | - | - | - | INVALID (entry-time shift layer, share 0.96 not a skip) | - | - | - | - | n/a |
| STACKCAP | K7,M7,P7; [1] | 0.101 | 0.101 (0.004) | 0.025 | 0 | yes | 0.84 / 0.78 / 0.99 / 0.26 / 0.46 / 1.00 | 0.28 / 0.41 / 0.46 | 0.92 / 0.91 / 0.90 | 0.79 / 0.96 | FAIL |

## Table 3 - overlap (share of a layer's changed trades that another layer also changes; ALL43, only pairs >= 50%)
Overlap is between changed-trade sets (book, entry second) of two leave-one-out cells; large values mean the two layers act on the same trades, so their leave-one-out values are not additive.

| layer A | changed trades (ALL43) | layer B | share of A's changed trades also changed by B |
|--|--|--|--|
| A06 | 1,136 | L2GATE | 55% |
| ADD_P7FLAT42 | 1,096 | F3CTXCUT | 85% |
| ADD_P7FLAT42 | 1,096 | L2GATE | 71% |
| ATRSKIP | 2,212 | ERLADDER | 92% |
| BLACKOUT | 734 | CUTLINE_P7 | 52% |
| BREADTH | 3,024 | L2GATE | 77% |
| CUTLINE_A7 | 225 | STATECUT_ALL | 90% |
| CUTLINE_H7 | 477 | STATECUT_ALL | 79% |
| CUTLINE_H7 | 477 | L2GATE | 69% |
| CUTLINE_K7 | 2,144 | STATECUT_ALL | 97% |
| CUTLINE_K7 | 2,144 | L2GATE | 54% |
| CUTLINE_M7 | 2,802 | STATECUT_ALL | 97% |
| CUTLINE_M7 | 2,802 | L2GATE | 56% |
| CUTLINE_O7 | 149 | STATECUT_ALL | 100% |
| CUTLINE_P7 | 3,723 | L2GATE | 75% |
| CUTLINE_P7 | 3,723 | F3CTXCUT | 68% |
| CUTLINE_U7 | 260 | STATECUT_ALL | 85% |
| CUTLINE_U7 | 260 | L2GATE | 71% |
| ERLADDER | 8,936 | L2GATE | 74% |
| F3CTXCUT | 3,309 | L2GATE | 78% |
| F3CTXCUT | 3,309 | CUTLINE_P7 | 77% |
| LOT | 2,296 | L2GATE | 88% |
| LOT | 2,296 | ERLADDER | 57% |
| NTZ | 2,998 | L2GATE | 56% |
| OTE62 | 778 | L2GATE | 74% |
| REG | 804 | L2GATE | 85% |
| REG | 804 | ERLADDER | 62% |
| SIGQ | 2,174 | L2GATE | 87% |
| STACKCAP | 1,385 | NTZ | 97% |
| STACKCUT | 1,069 | L2GATE | 71% |
| STATECUT_ALL | 5,567 | L2GATE | 55% |

## Table 4 (43 months) - by book: ulcer cut by layer % / change in mean $/wk base / trades ON minus OFF
Each cell uses the book's own daily path (book-level ulcer); path effects of a layer on other books show up in those books' columns. No bootstrap per book (see the CSV for every number).

| layer | K7 | M7 | U7 | P7 | H7 | A7 | O7 | total |
|--|--|--|--|--|--|--|--|--|
| A06 | +9% / -414 / 210 | -5% / +30 / 10 | +1% / +23 / 1 | +7% / +53 / 9 | -3% / +40 / 1 | +0% / +0 / 0 | +0% / +6 / -2 | +3.5% / -262 / 229 |
| ADD_P7FLAT42 | +2% / +0 / -10 | -7% / -67 / -14 | +1% / +2 / 0 | -14% / -387 / 117 | +1% / +8 / -1 | +0% / +0 / 0 | +0% / +3 / -1 | -8.7% / -442 / 91 |
| ATRSKIP | -4% / +6 / 70 | -15% / -49 / 47 | +0% / +1 / 1 | -13% / -320 / -1229 | -2% / +1 / 2 | +0% / +0 / 0 | -1% / +2 / 5 | +2.8% / -359 / -1104 |
| B02 | +3% / -31 / 1 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / -23 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | -0.5% / -54 / 1 |
| BLACKOUT | -1% / +32 / 26 | +3% / +29 / 18 | -0% / +40 / 0 | -6% / -8 / -83 | +4% / +6 / 1 | +0% / +0 / 0 | -0% / +4 / 2 | +2.0% / +103 / -36 |
| BREADTH | +4% / +167 / 42 | +24% / -91 / 33 | +1% / +29 / 1 | +4% / +301 / -271 | -5% / -19 / 3 | +0% / +0 / 0 | -1% / -17 / 5 | +4.9% / +368 / -187 |
| CUTLINE_A7 | +2% / +45 / -6 | -5% / -21 / -3 | -0% / -70 / -1 | -1% / -18 / -3 | -0% / -7 / 3 | +12% / +35 / 16 | +0% / +0 / 0 | -1.2% / -35 / 6 |
| CUTLINE_H7 | +1% / +13 / -1 | +5% / +20 / -3 | +0% / -37 / 3 | -3% / +1 / 4 | -18% / -16 / 22 | -2% / -14 / -2 | +0% / -1 / 0 | -2.8% / -34 / 23 |
| CUTLINE_K7 | -12% / -246 / 268 | -9% / -32 / -24 | +0% / +12 / -4 | -2% / -15 / -12 | +0% / +22 / 3 | +0% / +0 / 0 | +0% / +26 / 0 | -5.3% / -234 / 231 |
| CUTLINE_M7 | -5% / -12 / -20 | +7% / -112 / 588 | +5% / +51 / -1 | -3% / -21 / -7 | +4% / +52 / -3 | +0% / +0 / 0 | -1% / -27 / 0 | +2.6% / -68 / 557 |
| CUTLINE_O7 | +1% / +6 / 1 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | -17% / -24 / 0 | -0.4% / -17 / 1 |
| CUTLINE_P7 | +5% / +169 / -8 | -2% / -7 / -3 | -2% / -62 / -3 | +40% / +455 / 664 | +4% / +64 / -7 | -5% / +2 / -6 | -1% / +1 / 3 | +10.2% / +621 / 640 |
| CUTLINE_U7 | +1% / +105 / -13 | +4% / +33 / 0 | -1% / +14 / 6 | -0% / +5 / -1 | +0% / +7 / 2 | -0% / -2 / 0 | +0% / +9 / 1 | +1.8% / +172 / -5 |
| DAYCAPS | -8% / -113 / -159 | -19% / -140 / 5 | -1% / -6 / -1 | -1% / -17 / -60 | -3% / -13 / 8 | -1% / -5 / -12 | -1% / -2 / 4 | -4.5% / -296 / -215 |
| DAYDONE | +2% / +256 / -727 | +19% / +170 / -472 | +1% / +90 / -37 | -0% / -35 / -128 | -10% / -77 / -56 | +0% / +0 / 0 | +3% / +8 / -41 | +3.5% / +413 / -1461 |
| ERLADDER | +31% / +28 / 708 | -11% / -271 / 181 | +31% / +149 / 11 | +27% / -775 / -1031 | +11% / -424 / -12 | +0% / +1 / 0 | -0% / -9 / -3 | +16.4% / -1,301 / -146 |
| F3CTXCUT | +1% / +112 / 33 | +4% / +96 / 10 | -1% / -3 / 1 | +37% / +112 / 165 | +3% / +18 / -1 | +0% / +0 / 0 | -1% / -10 / 3 | +19.3% / +325 / 211 |
| GIVEBACKLOCK | -6% / -282 / -346 | -5% / -23 / -20 | +0% / +17 / 0 | -0% / -6 / 0 | +0% / +0 / 0 | +1% / -35 / -15 | -9% / -42 / 2 | +0.5% / -371 / -379 |
| GOVERNOR | +0% / +56 / -3 | -3% / -26 / 6 | +0% / -6 / 0 | -0% / +35 / -29 | +0% / -4 / 1 | +0% / +0 / 0 | +0% / +0 / 0 | -0.2% / +55 / -25 |
| K7FLAT45 | -10% / -486 / 631 | +2% / +79 / -32 | +1% / +33 / -6 | +8% / +13 / -15 | +10% / +34 / -1 | -3% / +37 / -5 | +0% / +17 / -5 | -12.0% / -272 / 567 |
| L2GATE | +26% / +20 / 900 | +5% / +70 / 326 | +29% / -27 / 52 | +68% / -1,369 / 222 | +32% / -402 / -20 | -1% / +20 / -9 | -1% / -28 / -4 | +49.0% / -1,716 / 1467 |
| LOT | +4% / -29 / -11 | +6% / +30 / 9 | -4% / +1 / 5 | +4% / -1,874 / 107 | +4% / +26 / -3 | +0% / +0 / 0 | -1% / -22 / 2 | -0.4% / -1,868 / 109 |
| NTZ | -4% / -46 / 42 | -29% / -302 / -91 | +12% / -91 / -5 | +38% / +201 / 139 | +2% / +93 / 5 | +0% / +0 / 0 | -0% / +10 / 8 | +22.6% / -136 / 98 |
| OTE62 | -1% / +55 / 17 | -11% / -41 / 1 | +2% / +221 / -3 | -3% / +9 / -47 | +2% / +71 / 4 | +0% / +0 / 0 | -0% / -4 / 1 | -3.7% / +311 / -27 |
| P7CONFIRM | +1% / +24 / 2 | -1% / -6 / 1 | +0% / +0 / 0 | -3% / -59 / -73 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +2.6% / -41 / -70 |
| REG | -4% / -51 / -2 | -16% / -63 / -9 | +2% / +67 / 1 | +19% / -167 / 32 | -1% / -11 / -5 | +0% / +0 / 0 | -0% / +13 / 0 | +10.1% / -212 / 17 |
| SIGQ | +2% / +71 / 80 | +9% / +32 / 40 | +3% / -388 / -1 | +5% / +73 / 74 | +1% / -42 / -4 | +0% / +0 / 0 | -0% / -4 / 1 | +6.8% / -259 / 190 |
| STACKCAP | +4% / +103 / 22 | -15% / -243 / -113 | +1% / -95 / -12 | +11% / -51 / -43 | -5% / -6 / 1 | +0% / +0 / 0 | +0% / +20 / 2 | +14.6% / -273 / -143 |
| STACKCUT | +2% / -195 / -5 | +20% / +22 / -16 | +3% / +14 / -1 | +3% / -82 / 17 | +7% / +6 / -2 | +6% / +36 / 3 | +0% / +1 / 0 | -0.4% / -198 / -4 |
| STATECUT_ALL | -11% / -156 / 271 | +5% / -79 / 581 | +3% / -3 / 3 | -7% / -10 / -8 | -16% / +115 / 16 | +12% / +17 / 14 | -17% / +8 / -1 | -3.1% / -108 / 876 |

## Table 4 (L6M) - by book: ulcer cut by layer % / change in mean $/wk base / trades ON minus OFF
Each cell uses the book's own daily path (book-level ulcer); path effects of a layer on other books show up in those books' columns. No bootstrap per book (see the CSV for every number).

| layer | K7 | M7 | U7 | P7 | H7 | A7 | O7 | total |
|--|--|--|--|--|--|--|--|--|
| A06 | +17% / -889 / 67 | +8% / +69 / -5 | +0% / +116 / 0 | -8% / +12 / 4 | +8% / +167 / 1 | +0% / +0 / 0 | +10% / +3 / 0 | +2.9% / -523 / 67 |
| ADD_P7FLAT42 | -9% / -97 / -7 | +12% / +110 / -9 | +4% / +151 / -1 | -7% / -833 / 15 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | -12.6% / -669 / -2 |
| ATRSKIP | +9% / +366 / 24 | +8% / +96 / 20 | -6% / -44 / 1 | -2% / +726 / -135 | +0% / +17 / 2 | +0% / +0 / 0 | -30% / -58 / 2 | +16.1% / +1,102 / -86 |
| B02 | +11% / +23 / 1 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +11 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +1.3% / +34 / 1 |
| BLACKOUT | +6% / +188 / 11 | -15% / +62 / 7 | -5% / +194 / -1 | +13% / +334 / -25 | +0% / -46 / 1 | +0% / +0 / 0 | -2% / +38 / 2 | +7.7% / +771 / -5 |
| BREADTH | +10% / +324 / 19 | -25% / -79 / 9 | +2% / +113 / 0 | +24% / +1,753 / -76 | -0% / -1 / 0 | +0% / +0 / 0 | -31% / -105 / 4 | +42.1% / +2,005 / -44 |
| CUTLINE_A7 | -2% / +191 / 6 | +8% / +40 / -1 | -7% / -301 / 0 | -2% / +96 / 0 | +0% / +3 / 2 | +30% / +163 / 10 | +0% / +0 / 0 | +0.4% / +191 / 17 |
| CUTLINE_H7 | -3% / +105 / 7 | -3% / -74 / -2 | -8% / -226 / 0 | +0% / -203 / 0 | +54% / +432 / 6 | -2% / -18 / 0 | +0% / +0 / 0 | +11.3% / +16 / 11 |
| CUTLINE_K7 | +6% / +164 / 91 | +9% / -0 / -4 | -2% / +91 / -2 | -1% / +15 / -2 | +0% / +62 / 3 | +0% / +0 / 0 | +2% / +68 / 1 | -1.8% / +401 / 87 |
| CUTLINE_M7 | +12% / +251 / -1 | +22% / +218 / 126 | -10% / -218 / 1 | -2% / +44 / -2 | +0% / +68 / 0 | +0% / +0 / 0 | -4% / -29 / 1 | +4.6% / +333 / 125 |
| CUTLINE_O7 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +10% / +91 / 0 | +0.5% / +91 / 0 |
| CUTLINE_P7 | +17% / +723 / 26 | -33% / +144 / 9 | -11% / -159 / 0 | +34% / +3,288 / 158 | +10% / +90 / -1 | -6% / -44 / -2 | -22% / -59 / 2 | +21.4% / +3,983 / 192 |
| CUTLINE_U7 | +4% / +490 / 10 | +4% / +140 / 11 | -2% / +293 / 0 | +4% / +19 / 3 | +6% / +53 / 2 | -1% / -12 / 0 | +3% / +39 / 2 | +7.5% / +1,022 / 28 |
| DAYCAPS | +7% / +223 / -15 | -8% / -139 / 0 | +0% / +0 / 0 | -22% / -323 / -22 | -0% / -43 / 4 | -18% / -40 / -10 | -13% / -28 / 1 | +2.3% / -351 / -42 |
| DAYDONE | +54% / +1,839 / -276 | +25% / +621 / -236 | +5% / +599 / -25 | +5% / -53 / -89 | -26% / -424 / -22 | +0% / +0 / 0 | +31% / -27 / -17 | +33.8% / +2,555 / -665 |
| ERLADDER | +44% / +331 / 286 | -1% / -165 / 31 | +49% / +807 / -5 | -18% / -3,709 / -111 | +58% / -32 / -5 | +0% / +0 / 0 | -4% / -44 / -2 | +38.7% / -2,811 / 194 |
| F3CTXCUT | +27% / +685 / 28 | +1% / +243 / 8 | -9% / -62 / 1 | -3% / +692 / 41 | +10% / +106 / 2 | +0% / +0 / 0 | +2% / +42 / 2 | +24.4% / +1,706 / 82 |
| GIVEBACKLOCK | +3% / -295 / -141 | -0% / -71 / 4 | +0% / +73 / 0 | -2% / -66 / -1 | +0% / +0 / 0 | +11% / -13 / -7 | -1% / -31 / 1 | +2.9% / -405 / -144 |
| GOVERNOR | +5% / +210 / 8 | +10% / +44 / 3 | +0% / +46 / 1 | +5% / +76 / -18 | +0% / +17 / 2 | +0% / +0 / 0 | +0% / +0 / 0 | +6.4% / +393 / -4 |
| K7FLAT45 | +40% / +702 / 129 | +8% / -19 / 2 | -5% / +305 / -5 | +0% / +314 / -5 | -1% / -60 / 0 | +7% / +57 / -2 | -6% / +0 / 0 | +13.2% / +1,298 / 119 |
| L2GATE | +60% / +735 / 379 | +63% / +2,458 / 59 | +46% / +624 / -2 | +70% / -1,376 / 201 | +67% / +236 / -4 | -0% / -29 / 0 | -46% / -249 / 2 | +72.9% / +2,399 / 635 |
| LOT | -9% / +226 / 4 | -1% / +17 / -1 | +1% / +307 / 1 | -6% / -4,141 / 23 | +0% / +46 / 1 | +0% / +0 / 0 | -5% / -51 / 2 | +10.9% / -3,596 / 30 |
| NTZ | +2% / -558 / 16 | -2% / +130 / 7 | -6% / -247 / -1 | +18% / +1,192 / 23 | +3% / -284 / 1 | +0% / +0 / 0 | -3% / -38 / 5 | +10.0% / +196 / 51 |
| OTE62 | -7% / +139 / 18 | -5% / +11 / 9 | -3% / +691 / 0 | -16% / -83 / -3 | +5% / +104 / 2 | +0% / +0 / 0 | -4% / -29 / 1 | +4.7% / +833 / 27 |
| P7CONFIRM | +5% / +91 / 2 | -5% / -44 / 1 | +0% / +0 / 0 | +3% / +147 / -14 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +0.7% / +194 / -11 |
| REG | +0% / -23 / 6 | +1% / +11 / 0 | +1% / +200 / -2 | +1% / +512 / 6 | +0% / +0 / 0 | +0% / +0 / 0 | -15% / -30 / 1 | +9.1% / +671 / 11 |
| SIGQ | +22% / -410 / 53 | -2% / +135 / 14 | +28% / -434 / -3 | -5% / +463 / 32 | +4% / -181 / -1 | +0% / +0 / 0 | -4% / -29 / 1 | +16.9% / -456 / 96 |
| STACKCAP | -1% / -531 / 6 | +9% / +50 / -18 | -5% / -38 / -4 | +1% / +82 / -3 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +9.9% / -437 / -19 |
| STACKCUT | +10% / -401 / -29 | +2% / -106 / -8 | -4% / -78 / -2 | +7% / +292 / 3 | -5% / -183 / 0 | +7% / +78 / 0 | +0% / +0 / 0 | +10.7% / -398 / -36 |
| STATECUT_ALL | +33% / +604 / 105 | +29% / +282 / 127 | -13% / +34 / -2 | +1% / +203 / -2 | +59% / +683 / 4 | +27% / +128 / 10 | +18% / +198 / 3 | +28.7% / +2,132 / 245 |

## Table 4 (HOLD) - by book: ulcer cut by layer % / change in mean $/wk base / trades ON minus OFF
Each cell uses the book's own daily path (book-level ulcer); path effects of a layer on other books show up in those books' columns. No bootstrap per book (see the CSV for every number).

| layer | K7 | M7 | U7 | P7 | H7 | A7 | O7 | total |
|--|--|--|--|--|--|--|--|--|
| A06 | -8% / -642 / 48 | +11% / +220 / 6 | -0% / +198 / 1 | -4% / -65 / 5 | -9% / -41 / 2 | +0% / +0 / 0 | +11% / +22 / -1 | +7.5% / -309 / 61 |
| ADD_P7FLAT42 | -1% / -64 / 6 | -9% / -194 / -1 | +0% / +0 / 0 | +13% / +609 / -1 | +0% / +0 / 0 | +0% / +0 / 0 | +8% / +25 / -1 | +9.4% / +376 / 3 |
| ATRSKIP | -2% / -163 / 16 | -25% / -156 / 13 | +3% / +40 / -1 | -3% / +645 / -200 | +0% / +0 / 0 | +0% / +0 / 0 | +18% / +103 / 2 | +8.7% / +469 / -170 |
| B02 | +0% / -46 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | -0% / -46 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | -0.1% / -93 / 0 |
| BLACKOUT | -3% / -140 / 16 | +0% / +56 / 9 | +0% / +93 / 1 | +9% / +34 / -23 | +3% / +46 / 1 | +0% / +0 / 0 | +0% / +0 / 0 | +6.1% / +89 / 4 |
| BREADTH | +4% / +592 / -7 | -35% / -422 / 8 | -1% / +46 / 1 | +4% / -107 / -65 | -9% / -92 / 0 | +0% / +0 / 0 | -3% / -20 / 1 | +6.7% / -2 / -62 |
| CUTLINE_A7 | +3% / +120 / -11 | -2% / -130 / -4 | -0% / -93 / -1 | -2% / -73 / -3 | -0% / -7 / 0 | +14% / +52 / 4 | +0% / +0 / 0 | -3.7% / -129 / -15 |
| CUTLINE_H7 | -2% / +59 / 0 | +1% / +161 / 5 | +2% / +73 / 2 | +4% / +141 / 1 | -53% / -140 / 6 | -23% / -114 / -1 | +2% / -8 / 0 | +2.7% / +172 / 13 |
| CUTLINE_K7 | -42% / -818 / 45 | +13% / +41 / -7 | +3% / -53 / -2 | +1% / +32 / -7 | -0% / -46 / 1 | +0% / +0 / 0 | +23% / +116 / -1 | +2.8% / -728 / 29 |
| CUTLINE_M7 | -1% / -87 / -4 | -23% / -682 / 125 | +8% / +320 / -1 | +5% / +84 / -2 | +4% / +1 / 2 | +0% / +0 / 0 | -16% / -29 / 1 | +10.9% / -393 / 121 |
| CUTLINE_O7 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | -1% / -14 / 0 | +0.1% / -14 / 0 |
| CUTLINE_P7 | +8% / +318 / -8 | -4% / +342 / 1 | -8% / -131 / 0 | +52% / +688 / 120 | +1% / +53 / 2 | +2% / +72 / 0 | -2% / +75 / 1 | +26.9% / +1,416 / 116 |
| CUTLINE_U7 | +3% / +181 / -7 | -1% / +47 / -4 | -1% / +95 / 0 | +3% / +74 / -3 | +0% / +0 / 0 | +0% / +0 / 0 | +11% / +23 / -1 | +6.4% / +420 / -15 |
| DAYCAPS | +1% / -168 / -10 | -10% / -186 / 16 | -2% / -93 / -1 | +2% / +144 / -13 | -1% / -17 / 1 | +0% / +0 / 0 | +0% / +0 / 0 | -2.4% / -320 / -7 |
| DAYDONE | +21% / +567 / -177 | +16% / +469 / -120 | -8% / -162 / -8 | +4% / -95 / -28 | -13% / -188 / -11 | +0% / +0 / 0 | +35% / +32 / -11 | +15.4% / +624 / -355 |
| ERLADDER | +4% / -1,278 / 142 | -35% / -208 / 25 | +32% / +1,515 / 5 | +54% / +1,326 / -136 | +15% / -669 / 0 | +0% / +0 / 0 | +5% / +87 / 0 | +26.8% / +773 / 36 |
| F3CTXCUT | -13% / -132 / 14 | +8% / +346 / 13 | +0% / -0 / 0 | +31% / +664 / 51 | -2% / +0 / 0 | +0% / +0 / 0 | -9% / -25 / 1 | +20.0% / +852 / 79 |
| GIVEBACKLOCK | -12% / -915 / -76 | +0% / +77 / -6 | +0% / +46 / 0 | +1% / +27 / 1 | +0% / +0 / 0 | +3% / -254 / -8 | -8% / -160 / 1 | -4.7% / -1,178 / -88 |
| GOVERNOR | +1% / +103 / -1 | -16% / -215 / 5 | -0% / -93 / -1 | +10% / +250 / -6 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +1.4% / +45 / -3 |
| K7FLAT45 | +2% / -229 / 63 | +7% / +220 / -15 | +4% / +255 / 1 | -8% / -449 / -2 | +14% / +226 / 0 | -9% / +60 / 0 | +4% / +23 / -1 | +13.1% / +105 / 46 |
| L2GATE | +4% / -346 / 189 | -84% / -922 / 40 | +20% / +142 / 5 | +73% / +1,431 / 56 | +37% / -64 / 0 | +6% / +33 / -2 | +8% / +47 / -2 | +52.0% / +320 / 286 |
| LOT | +9% / +189 / -2 | +19% / +282 / 9 | +3% / +52 / 0 | +9% / -2,053 / 25 | +2% / +46 / 1 | +0% / +0 / 0 | -15% / -56 / 2 | -4.2% / -1,540 / 35 |
| NTZ | -7% / -255 / 14 | -11% / +119 / -21 | +17% / +245 / -2 | +3% / -90 / 10 | +1% / -179 / 2 | +0% / +0 / 0 | -8% / +108 / 3 | +23.8% / -51 / 6 |
| OTE62 | +2% / +111 / -3 | -15% / -54 / -5 | -6% / +74 / -1 | -1% / -7 / -10 | +14% / +99 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | -2.1% / +222 / -19 |
| P7CONFIRM | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | -1% / +178 / -7 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +1.6% / +178 / -7 |
| REG | -4% / -95 / -25 | +0% / +163 / -12 | +3% / +232 / 1 | +35% / -1,304 / 4 | -4% / -77 / -3 | +0% / +0 / 0 | +7% / -13 / -3 | +6.4% / -1,095 / -38 |
| SIGQ | +4% / +120 / 24 | +5% / -251 / 11 | +8% / -509 / 2 | +21% / +305 / 10 | +13% / -122 / -2 | +0% / +0 / 0 | +0% / +0 / 0 | +9.1% / -457 / 45 |
| STACKCAP | -4% / -113 / 3 | -32% / +79 / -21 | +2% / -66 / -3 | +4% / -225 / -5 | -1% / -92 / 0 | +0% / +0 / 0 | -2% / +142 / 2 | +14.1% / -274 / -24 |
| STACKCUT | -6% / -162 / 17 | -4% / +124 / -1 | +4% / +320 / 0 | -0% / +94 / 5 | +2% / -2 / 1 | +13% / +168 / 0 | +0% / +0 / 0 | +1.4% / +543 / 22 |
| STATECUT_ALL | -46% / -580 / 49 | -11% / -498 / 126 | +5% / +217 / -1 | +8% / +102 / -4 | -61% / -193 / 8 | +2% / -35 / 3 | +20% / +185 / 0 | +8.6% / -802 / 181 |

## Table 4 (L3M) - by book: ulcer cut by layer % / change in mean $/wk base / trades ON minus OFF
Each cell uses the book's own daily path (book-level ulcer); path effects of a layer on other books show up in those books' columns. No bootstrap per book (see the CSV for every number).

| layer | K7 | M7 | U7 | P7 | H7 | A7 | O7 | total |
|--|--|--|--|--|--|--|--|--|
| A06 | +16% / -1,446 / 42 | +0% / +0 / 0 | -6% / +64 / 0 | -9% / -339 / 3 | +28% / +234 / 1 | +0% / +0 / 0 | -2% / -44 / 1 | +0.1% / -1,531 / 47 |
| ADD_P7FLAT42 | -14% / -104 / -6 | +1% / +52 / -8 | +13% / +302 / -1 | -7% / -1,492 / 10 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | -20.0% / -1,242 / -5 |
| ATRSKIP | +1% / +53 / 2 | -1% / -147 / 2 | +0% / +91 / 0 | -5% / -474 / -42 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +1.0% / -476 / -38 |
| B02 | +13% / -96 / 1 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +21 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +1.8% / -75 / 1 |
| BLACKOUT | -1% / -111 / -1 | +0% / +480 / -4 | +3% / +574 / -2 | +12% / -413 / -3 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +9.9% / +529 / -10 |
| BREADTH | +8% / +288 / 12 | -5% / +384 / 4 | +7% / +478 / 0 | +11% / +2,549 / -35 | +3% / +89 / -1 | +0% / +0 / 0 | -21% / -89 / 2 | +49.1% / +3,698 / -18 |
| CUTLINE_A7 | -14% / -93 / 0 | -2% / -97 / -1 | -18% / -496 / 0 | -2% / +96 / 1 | +0% / +0 / 0 | +14% / +172 / 5 | +0% / +0 / 0 | -8.8% / -418 / 5 |
| CUTLINE_H7 | -28% / -296 / 0 | -10% / -136 / 2 | -15% / -211 / 1 | -0% / -146 / 2 | +69% / +1,237 / 3 | -3% / -30 / 0 | +0% / +0 / 0 | +11.3% / +418 / 8 |
| CUTLINE_K7 | +12% / +469 / 52 | -10% / -154 / -4 | +1% / +274 / -1 | -2% / +165 / 0 | +0% / +91 / 1 | +0% / +0 / 0 | +1% / +137 / 1 | -3.2% / +982 / 49 |
| CUTLINE_M7 | +17% / +507 / 5 | +18% / +680 / 53 | -12% / -163 / 1 | -3% / +41 / -1 | +0% / +91 / 1 | +0% / +0 / 0 | -16% / -58 / 1 | +8.0% / +1,098 / 60 |
| CUTLINE_O7 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +10% / +116 / 0 | +0.7% / +116 / 0 |
| CUTLINE_P7 | +16% / +1,209 / 4 | -7% / +554 / -6 | -15% / +127 / -2 | +20% / +463 / 100 | +7% / +220 / -1 | -10% / -175 / 0 | -50% / -195 / 0 | +18.9% / +2,204 / 95 |
| CUTLINE_U7 | +0% / +484 / 10 | +6% / +235 / 6 | +13% / +213 / 1 | +2% / +91 / 1 | +17% / +196 / 1 | +0% / +0 / 0 | -16% / -58 / 1 | +7.4% / +1,161 / 20 |
| DAYCAPS | -3% / -220 / -10 | +2% / -66 / -6 | +0% / +0 / 0 | -24% / -664 / -20 | -1% / -120 / 2 | -33% / -405 / -6 | +0% / +0 / 0 | -0.5% / -1,475 / -40 |
| DAYDONE | +60% / +1,277 / -142 | +3% / +156 / -87 | +19% / +1,629 / -13 | +6% / +378 / -42 | +5% / -259 / -10 | +0% / +0 / 0 | +5% / +35 / -8 | +40.0% / +3,216 / -302 |
| ERLADDER | +20% / -1,518 / 104 | -2% / -865 / 5 | +62% / +1,698 / -4 | -34% / -4,430 / -27 | +71% / +378 / -6 | +0% / +0 / 0 | -50% / -85 / -2 | +21.0% / -4,823 / 70 |
| F3CTXCUT | +30% / +753 / 14 | +15% / +730 / 1 | -2% / +154 / -1 | -18% / -723 / 30 | +4% / +181 / 0 | +0% / +0 / 0 | -19% / -53 / 1 | +29.9% / +1,042 / 45 |
| GIVEBACKLOCK | -10% / -276 / -27 | -6% / -187 / 3 | +0% / +91 / 0 | -2% / -82 / 2 | +0% / +0 / 0 | +15% / +191 / -3 | -1% / +91 / 1 | +1.3% / -173 / -24 |
| GOVERNOR | +0% / +0 / 0 | -1% / -147 / 2 | +0% / +0 / 0 | +5% / -83 / -7 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +2.4% / -230 / -5 |
| K7FLAT45 | +7% / -888 / 51 | -1% / -203 / -2 | +15% / +947 / -4 | +1% / +1,042 / -6 | -0% / -27 / 0 | -3% / +29 / 0 | +0% / +0 / 0 | +17.0% / +900 / 39 |
| L2GATE | +53% / -96 / 176 | +44% / +2,082 / 19 | +56% / +1,146 / -2 | +56% / +1,097 / 89 | +81% / +697 / -4 | -1% / -37 / 0 | -104% / -236 / 1 | +70.6% / +4,652 / 279 |
| LOT | -18% / +210 / 21 | +5% / +86 / 11 | +4% / +697 / 0 | -9% / -1,424 / 11 | +0% / +91 / 1 | +0% / +0 / 0 | -20% / -102 / 2 | +14.3% / -440 / 46 |
| NTZ | -4% / -213 / 19 | +9% / +568 / 1 | +12% / +442 / -1 | +16% / +1,715 / 9 | -24% / -261 / 0 | +0% / +0 / 0 | -21% / -154 / 3 | +11.9% / +2,097 / 31 |
| OTE62 | -16% / -21 / 14 | +4% / -5 / 6 | +6% / +1,087 / 0 | -19% / -299 / 0 | +15% / +208 / 2 | +0% / +0 / 0 | -16% / -58 / 1 | +2.9% / +912 / 23 |
| P7CONFIRM | +7% / +182 / 2 | +0% / +0 / 0 | +0% / +0 / 0 | +4% / -130 / -10 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +1.3% / +53 / -8 |
| REG | +0% / +0 / 0 | +0% / +106 / 0 | +0% / +0 / 0 | -3% / -495 / -1 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +3.8% / -389 / -1 |
| SIGQ | +28% / +353 / 46 | +2% / +176 / 8 | -6% / -1,068 / -2 | -8% / +288 / 8 | +10% / +32 / 0 | +0% / +0 / 0 | -16% / -58 / 1 | +13.6% / -278 / 61 |
| STACKCAP | -2% / -715 / 1 | +10% / +221 / -12 | -0% / -191 / -2 | +1% / +359 / -3 | +0% / +0 / 0 | +0% / +0 / 0 | +0% / +0 / 0 | +12.3% / -325 / -16 |
| STACKCUT | +15% / -132 / -12 | -7% / -279 / -7 | -0% / -14 / -2 | +7% / +770 / 0 | -29% / -562 / 0 | +1% / +22 / 0 | +0% / +0 / 0 | +15.8% / -197 / -21 |
| STATECUT_ALL | +27% / +1,149 / 72 | +20% / +1,260 / 57 | +8% / +366 / 0 | -2% / +488 / 1 | +70% / +1,491 / 4 | +11% / +131 / 5 | -1% / +194 / 2 | +35.6% / +5,079 / 141 |

## Table 5 - full detail per layer and window (total; base, x1.75 live, $4.84, live x1.75 at $4.84; bootstrap; W44 removed for windows containing 2026-10-26..30)
Bootstrap = 2,000 week-clustered resamples of the paired weekly P&L (ON vs OFF), ulcer on the weekly cumulative path; P(layer helps ulcer) = share of resamples with lower ulcer ON; interval = 5th..95th percentile of the mean change per week (ON minus OFF). W44 = the week 2026-10-26..11-01 (data ends 10-30).

| layer | window | weeks | ulcer ON -> OFF (cut by layer) | max DD ON / OFF (cut by layer) | worst wk ON / OFF | d mean $/wk base | x1.75 live | @ $4.84 base | live x1.75 @ $4.84 | trades ON / OFF (changed) | P(layer helps ulcer) | P(DD shallower) | 90% int mean change base | noW44: ulcer cut / P / mean |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| A06 | L3M | 13 | 9,803 -> 9,798 (+0.1%) | -22,565 / -22,464 (-100) | -13,430 / -13,438 | -1,531 | -2,987 | -1,533 | -2,991 | 1913 / 1866 (67) | 0.68 | 0.65 | -3,208..+200 | +0.7% / 0.89 / -1,603 |
| A06 | L6M | 26 | 8,603 -> 8,356 (+2.9%) | -22,565 / -22,464 (-100) | -13,430 / -13,438 | -523 | -1,079 | -518 | -1,069 | 4161 / 4094 (155) | 0.87 | 0.74 | -1,817..+806 | +3.8% / 0.97 / -524 |
| A06 | HOLD | 26 | 26,528 -> 24,530 (+7.5%) | -74,402 / -75,811 (+1,409) | -31,211 / -31,511 | -309 | -628 | -305 | -619 | 3219 / 3158 (145) | 0.51 | 0.57 | -1,548..+984 |  |
| A06 | GAP | 13 | 20,843 -> 21,125 (-1.4%) | -55,206 / -52,210 (-2,996) | -43,527 / -45,438 | -1,290 | -2,716 | -1,282 | -2,701 | 1102 / 1096 (26) | 0.38 | 0.49 | -2,417..-40 |  |
| A06 | PREUW | 39 | 26,612 -> 24,609 (+7.5%) | -70,931 / -78,787 (+7,856) | -28,958 / -28,870 | +349 | +657 | +349 | +657 | 4201 / 4108 (149) | 0.58 | 0.56 | -335..+1,015 |  |
| A06 | X' | 78 | 18,531 -> 19,020 (-2.6%) | -73,618 / -76,481 (+2,863) | -37,052 / -41,540 | -223 | -380 | -216 | -367 | 5816 / 5805 (79) | 0.60 | 0.65 | -612..+131 |  |
| A06 | ALL43 | 187 | 21,037 -> 20,293 (+3.5%) | -74,402 / -78,787 (+4,385) | -43,527 / -45,438 | -262 | -520 | -257 | -510 | 18979 / 18750 (577) | 0.64 | 0.65 | -607..+87 | +3.6% / 0.64 / -261 |
| ADD_P7FLAT42 | L3M | 13 | 9,798 -> 11,756 (-20.0%) | -28,589 / -22,565 (-6,024) | -21,267 / -13,430 | -1,242 | -2,208 | -1,242 | -2,208 | 1908 / 1913 (65) | 0.07 | 0.07 | -2,677..+180 | -19.1% / 0.19 / -1,132 |
| ADD_P7FLAT42 | L6M | 26 | 8,356 -> 9,411 (-12.6%) | -28,589 / -22,565 (-6,024) | -21,267 / -13,430 | -669 | -1,275 | -669 | -1,276 | 4159 / 4161 (92) | 0.12 | 0.13 | -1,620..+169 | -10.5% / 0.28 / -597 |
| ADD_P7FLAT42 | HOLD | 26 | 24,530 -> 22,229 (+9.4%) | -65,168 / -74,402 (+9,234) | -30,409 / -31,211 | +376 | +605 | +375 | +603 | 3222 / 3219 (61) | 0.93 | 0.95 | -613..+1,232 |  |
| ADD_P7FLAT42 | GAP | 13 | 21,125 -> 20,703 (+2.0%) | -51,759 / -55,206 (+3,447) | -42,657 / -43,527 | +577 | +966 | +574 | +960 | 1104 / 1102 (14) | 0.57 | 0.60 | -550..+1,871 |  |
| ADD_P7FLAT42 | PREUW | 39 | 24,609 -> 21,289 (+13.5%) | -63,108 / -70,931 (+7,823) | -31,008 / -28,958 | +289 | +553 | +287 | +550 | 4211 / 4201 (96) | 0.50 | 0.51 | -424..+905 |  |
| ADD_P7FLAT42 | X' | 78 | 19,020 -> 25,558 (-34.4%) | -73,244 / -73,618 (+374) | -36,266 / -37,052 | -1,135 | -2,101 | -1,140 | -2,111 | 5889 / 5816 (251) | 0.01 | 0.08 | -1,853..-428 |  |
| ADD_P7FLAT42 | ALL43 | 187 | 20,293 -> 22,067 (-8.7%) | -73,244 / -74,402 (+1,158) | -42,657 / -43,527 | -442 | -838 | -445 | -845 | 19070 / 18979 (527) | 0.09 | 0.30 | -854..-31 | -8.7% / 0.08 / -431 |
| ATRSKIP | L3M | 13 | 9,895 -> 9,798 (+1.0%) | -22,565 / -24,164 (+1,599) | -13,430 / -13,965 | -476 | -904 | -466 | -882 | 1913 / 1951 (68) | 0.78 | 0.73 | -1,261..+359 | +5.5% / 0.88 / -509 |
| ATRSKIP | L6M | 26 | 9,958 -> 8,356 (+16.1%) | -22,565 / -32,273 (+9,708) | -13,430 / -28,781 | +1,102 | +2,170 | +1,119 | +2,202 | 4161 / 4247 (258) | 0.85 | 0.84 | -317..+2,726 | +20.0% / 0.86 / +1,140 |
| ATRSKIP | HOLD | 26 | 26,860 -> 24,530 (+8.7%) | -74,402 / -81,980 (+7,579) | -31,211 / -33,791 | +469 | +726 | +502 | +791 | 3219 / 3389 (386) | 0.84 | 0.83 | -905..+1,952 |  |
| ATRSKIP | GAP | 13 | 20,689 -> 21,125 (-2.1%) | -55,206 / -53,754 (-1,452) | -43,527 / -47,298 | -2,333 | -4,395 | -2,307 | -4,345 | 1102 / 1178 (118) | 0.55 | 0.66 | -4,977..+261 |  |
| ATRSKIP | PREUW | 39 | 19,591 -> 24,609 (-25.6%) | -70,931 / -52,386 (-18,545) | -28,958 / -30,543 | -827 | -1,518 | -797 | -1,459 | 4201 / 4452 (551) | 0.53 | 0.59 | -2,116..+467 |  |
| ATRSKIP | X' | 78 | 21,798 -> 19,020 (+12.7%) | -73,618 / -73,348 (-270) | -37,052 / -34,035 | -575 | -1,110 | -551 | -1,062 | 5816 / 6285 (785) | 0.49 | 0.47 | -1,211..+77 |  |
| ATRSKIP | ALL43 | 187 | 20,884 -> 20,293 (+2.8%) | -74,402 / -81,980 (+7,579) | -43,527 / -47,298 | -359 | -688 | -333 | -636 | 18979 / 20083 (2190) | 0.78 | 0.73 | -899..+188 | +2.9% / 0.80 / -361 |
| B02 | L3M | 13 | 9,981 -> 9,798 (+1.8%) | -22,565 / -23,230 (+665) | -13,430 / -13,430 | -75 | -150 | -73 | -146 | 1913 / 1912 (1) | 0.58 | 0.51 | -556..+377 | +2.4% / 0.55 / -80 |
| B02 | L6M | 26 | 8,464 -> 8,356 (+1.3%) | -22,565 / -23,230 (+665) | -13,430 / -13,430 | +34 | +67 | +35 | +70 | 4161 / 4160 (1) | 0.58 | 0.51 | -232..+264 | +1.5% / 0.55 / +35 |
| B02 | HOLD | 26 | 24,516 -> 24,530 (-0.1%) | -74,402 / -74,402 (+0) | -31,211 / -31,211 | -93 | -185 | -93 | -185 | 3219 / 3219 (0) | 0.15 | 0.39 | -178..+0 |  |
| B02 | GAP | 13 | 21,125 -> 21,125 (+0.0%) | -55,206 / -55,206 (+0) | -43,527 / -43,527 | +58 | +117 | +59 | +117 | 1102 / 1102 (0) | 0.81 | 0.63 | -0..+164 |  |
| B02 | PREUW | 39 | 24,234 -> 24,609 (-1.5%) | -70,931 / -70,388 (-544) | -28,958 / -28,958 | -314 | -628 | -313 | -625 | 4201 / 4201 (6) | 0.07 | 0.24 | -590..-61 |  |
| B02 | X' | 78 | 19,003 -> 19,020 (-0.1%) | -73,618 / -73,618 (+0) | -37,052 / -37,052 | +67 | +135 | +68 | +136 | 5816 / 5816 (4) | 0.54 | 0.49 | -42..+177 |  |
| B02 | ALL43 | 187 | 20,195 -> 20,293 (-0.5%) | -74,402 / -74,402 (+0) | -43,527 / -43,527 | -54 | -108 | -53 | -106 | 18979 / 18978 (11) | 0.28 | 0.40 | -140..+34 | -0.5% / 0.30 / -54 |
| BLACKOUT | L3M | 13 | 10,871 -> 9,798 (+9.9%) | -22,565 / -30,142 (+7,578) | -13,430 / -16,240 | +529 | +966 | +539 | +984 | 1913 / 1923 (124) | 0.72 | 0.72 | -860..+1,955 | +4.6% / 0.35 / +148 |
| BLACKOUT | L6M | 26 | 9,050 -> 8,356 (+7.7%) | -22,565 / -30,142 (+7,578) | -13,430 / -16,240 | +771 | +1,548 | +777 | +1,559 | 4161 / 4166 (269) | 0.82 | 0.76 | -210..+1,763 | +3.7% / 0.56 / +594 |
| BLACKOUT | HOLD | 26 | 26,135 -> 24,530 (+6.1%) | -74,402 / -77,699 (+3,297) | -31,211 / -32,498 | +89 | +248 | +91 | +253 | 3219 / 3215 (158) | 0.46 | 0.45 | -978..+1,214 |  |
| BLACKOUT | GAP | 13 | 21,118 -> 21,125 (-0.0%) | -55,206 / -55,206 (+0) | -43,527 / -43,527 | -153 | -306 | -152 | -305 | 1102 / 1105 (11) | 0.76 | 0.64 | -609..+151 |  |
| BLACKOUT | PREUW | 39 | 25,537 -> 24,609 (+3.6%) | -70,931 / -70,749 (-182) | -28,958 / -28,958 | -12 | -26 | -10 | -21 | 4201 / 4226 (205) | 0.39 | 0.47 | -1,162..+1,253 |  |
| BLACKOUT | X' | 78 | 18,816 -> 19,020 (-1.1%) | -73,618 / -71,712 (-1,906) | -37,052 / -35,146 | +23 | +56 | +22 | +55 | 5816 / 5811 (65) | 0.16 | 0.24 | -71..+134 |  |
| BLACKOUT | ALL43 | 187 | 20,713 -> 20,293 (+2.0%) | -74,402 / -77,699 (+3,297) | -43,527 / -43,527 | +103 | +221 | +105 | +225 | 18979 / 19015 (724) | 0.47 | 0.46 | -218..+443 | +1.9% / 0.38 / +76 |
| BREADTH | L3M | 13 | 19,245 -> 9,798 (+49.1%) | -22,565 / -46,786 (+24,221) | -13,430 / -12,816 | +3,698 | +6,540 | +3,728 | +6,592 | 1913 / 1931 (322) | 0.77 | 0.62 | +341..+6,886 | +54.3% / 0.93 / +4,346 |
| BREADTH | L6M | 26 | 14,442 -> 8,356 (+42.1%) | -22,565 / -46,786 (+24,221) | -13,430 / -12,816 | +2,005 | +3,247 | +2,037 | +3,302 | 4161 / 4205 (708) | 0.61 | 0.43 | -338..+4,128 | +45.7% / 0.76 / +2,261 |
| BREADTH | HOLD | 26 | 26,296 -> 24,530 (+6.7%) | -74,402 / -80,373 (+5,971) | -31,211 / -31,756 | -2 | +51 | +20 | +92 | 3219 / 3281 (666) | 0.88 | 0.89 | -2,447..+2,377 |  |
| BREADTH | GAP | 13 | 21,312 -> 21,125 (+0.9%) | -55,206 / -57,463 (+2,258) | -43,527 / -41,837 | -1,578 | -3,120 | -1,559 | -3,084 | 1102 / 1126 (164) | 0.29 | 0.34 | -4,087..+926 |  |
| BREADTH | PREUW | 39 | 22,959 -> 24,609 (-7.2%) | -70,931 / -70,494 (-437) | -28,958 / -28,671 | -693 | -1,331 | -679 | -1,307 | 4201 / 4212 (723) | 0.45 | 0.43 | -2,728..+1,379 |  |
| BREADTH | X' | 78 | 20,704 -> 19,020 (+8.1%) | -73,618 / -72,889 (-729) | -37,052 / -36,441 | +704 | +1,275 | +709 | +1,284 | 5816 / 5855 (587) | 0.93 | 0.81 | +20..+1,377 |  |
| BREADTH | ALL43 | 187 | 21,338 -> 20,293 (+4.9%) | -74,402 / -80,373 (+5,971) | -43,527 / -41,837 | +368 | +588 | +382 | +614 | 18979 / 19166 (2917) | 0.88 | 0.73 | -405..+1,076 | +4.9% / 0.90 / +396 |
| CUTLINE_A7 | L3M | 13 | 9,002 -> 9,798 (-8.8%) | -22,565 / -22,508 (-56) | -13,430 / -13,430 | -418 | -806 | -421 | -811 | 1913 / 1908 (13) | 0.29 | 0.38 | -1,109..+226 | -4.1% / 0.73 / -413 |
| CUTLINE_A7 | L6M | 26 | 8,388 -> 8,356 (+0.4%) | -22,565 / -22,508 (-56) | -13,430 / -13,430 | +191 | +402 | +188 | +396 | 4161 / 4144 (45) | 0.68 | 0.52 | -435..+863 | +4.2% / 0.89 / +214 |
| CUTLINE_A7 | HOLD | 26 | 23,649 -> 24,530 (-3.7%) | -74,402 / -72,554 (-1,848) | -31,211 / -31,388 | -129 | -259 | -127 | -254 | 3219 / 3234 (25) | 0.33 | 0.44 | -463..+171 |  |
| CUTLINE_A7 | GAP | 13 | 21,129 -> 21,125 (+0.0%) | -55,206 / -55,206 (+0) | -43,527 / -43,527 | +105 | +211 | +105 | +211 | 1102 / 1102 (0) | 0.89 | 0.64 | +32..+182 |  |
| CUTLINE_A7 | PREUW | 39 | 24,228 -> 24,609 (-1.6%) | -70,931 / -70,259 (-672) | -28,958 / -28,958 | -201 | -363 | -201 | -365 | 4201 / 4197 (16) | 0.26 | 0.34 | -408..-19 |  |
| CUTLINE_A7 | X' | 78 | 18,953 -> 19,020 (-0.4%) | -73,618 / -74,533 (+916) | -37,052 / -37,052 | -32 | -64 | -32 | -64 | 5816 / 5816 (0) | 0.38 | 0.52 | -97..+21 |  |
| CUTLINE_A7 | ALL43 | 187 | 20,045 -> 20,293 (-1.2%) | -74,402 / -74,533 (+132) | -43,527 / -43,527 | -35 | -60 | -36 | -61 | 18979 / 18973 (86) | 0.35 | 0.48 | -147..+82 | -1.2% / 0.38 / -33 |
| CUTLINE_H7 | L3M | 13 | 11,052 -> 9,798 (+11.3%) | -22,565 / -26,534 (+3,969) | -13,430 / -15,329 | +418 | +712 | +414 | +703 | 1913 / 1905 (18) | 0.98 | 0.98 | -806..+1,412 | +9.3% / 0.92 / +228 |
| CUTLINE_H7 | L6M | 26 | 9,417 -> 8,356 (+11.3%) | -22,565 / -26,534 (+3,969) | -13,430 / -15,329 | +16 | +88 | +13 | +83 | 4161 / 4150 (39) | 0.94 | 0.87 | -1,123..+1,169 | +10.0% / 0.85 / -90 |
| CUTLINE_H7 | HOLD | 26 | 25,222 -> 24,530 (+2.7%) | -74,402 / -76,521 (+2,119) | -31,211 / -33,099 | +172 | +334 | +168 | +326 | 3219 / 3206 (65) | 0.63 | 0.66 | -666..+905 |  |
| CUTLINE_H7 | GAP | 13 | 23,109 -> 21,125 (+8.6%) | -55,206 / -58,495 (+3,290) | -43,527 / -46,874 | +556 | +1,027 | +556 | +1,025 | 1102 / 1100 (8) | 0.71 | 0.73 | -13..+1,098 |  |
| CUTLINE_H7 | PREUW | 39 | 22,254 -> 24,609 (-10.6%) | -70,931 / -70,879 (-52) | -28,958 / -28,958 | -463 | -888 | -463 | -889 | 4201 / 4207 (62) | 0.09 | 0.21 | -1,094..+131 |  |
| CUTLINE_H7 | X' | 78 | 18,453 -> 19,020 (-3.1%) | -73,618 / -66,456 (-7,162) | -37,052 / -28,727 | +67 | +138 | +66 | +137 | 5816 / 5813 (11) | 0.55 | 0.54 | -278..+365 |  |
| CUTLINE_H7 | ALL43 | 187 | 19,731 -> 20,293 (-2.8%) | -74,402 / -76,521 (+2,119) | -43,527 / -46,874 | -34 | -50 | -36 | -52 | 18979 / 18956 (187) | 0.51 | 0.56 | -318..+243 | -3.0% / 0.46 / -49 |
| CUTLINE_K7 | L3M | 13 | 9,496 -> 9,798 (-3.2%) | -22,565 / -23,263 (+698) | -13,430 / -13,929 | +982 | +1,873 | +967 | +1,843 | 1913 / 1864 (187) | 0.53 | 0.61 | -1,559..+4,254 | -2.0% / 0.83 / +1,118 |
| CUTLINE_K7 | L6M | 26 | 8,210 -> 8,356 (-1.8%) | -22,565 / -23,263 (+698) | -13,430 / -13,929 | +401 | +786 | +388 | +761 | 4161 / 4074 (337) | 0.24 | 0.45 | -1,094..+2,160 | -0.8% / 0.36 / +447 |
| CUTLINE_K7 | HOLD | 26 | 25,248 -> 24,530 (+2.8%) | -74,402 / -70,192 (-4,210) | -31,211 / -32,685 | -728 | -1,456 | -732 | -1,464 | 3219 / 3190 (239) | 0.44 | 0.50 | -1,873..+522 |  |
| CUTLINE_K7 | GAP | 13 | 18,477 -> 21,125 (-14.3%) | -55,206 / -49,221 (-5,984) | -43,527 / -40,118 | -832 | -1,664 | -836 | -1,671 | 1102 / 1090 (30) | 0.06 | 0.07 | -1,515..-23 |  |
| CUTLINE_K7 | PREUW | 39 | 21,840 -> 24,609 (-12.7%) | -70,931 / -62,780 (-8,152) | -28,958 / -28,958 | -45 | -120 | -52 | -134 | 4201 / 4121 (310) | 0.40 | 0.45 | -941..+804 |  |
| CUTLINE_K7 | X' | 78 | 18,402 -> 19,020 (-3.4%) | -73,618 / -63,490 (-10,128) | -37,052 / -42,527 | -252 | -504 | -253 | -507 | 5816 / 5790 (174) | 0.50 | 0.62 | -703..+139 |  |
| CUTLINE_K7 | ALL43 | 187 | 19,279 -> 20,293 (-5.3%) | -74,402 / -70,192 (-4,210) | -43,527 / -42,527 | -234 | -476 | -238 | -485 | 18979 / 18748 (1151) | 0.38 | 0.46 | -644..+167 | -5.2% / 0.36 / -230 |
| CUTLINE_M7 | L3M | 13 | 10,646 -> 9,798 (+8.0%) | -22,565 / -27,803 (+5,238) | -13,430 / -15,701 | +1,098 | +2,272 | +1,080 | +2,236 | 1913 / 1853 (116) | 0.95 | 0.97 | -816..+2,999 | +11.5% / 0.94 / +1,147 |
| CUTLINE_M7 | L6M | 26 | 8,755 -> 8,356 (+4.6%) | -22,565 / -27,803 (+5,238) | -13,430 / -15,701 | +333 | +704 | +315 | +667 | 4161 / 4036 (261) | 0.92 | 0.91 | -1,026..+1,694 | +6.4% / 0.89 / +331 |
| CUTLINE_M7 | HOLD | 26 | 27,539 -> 24,530 (+10.9%) | -74,402 / -82,315 (+7,914) | -31,211 / -30,818 | -393 | -832 | -412 | -870 | 3219 / 3098 (299) | 0.33 | 0.31 | -2,052..+1,269 |  |
| CUTLINE_M7 | GAP | 13 | 20,124 -> 21,125 (-5.0%) | -55,206 / -52,799 (-2,406) | -43,527 / -46,116 | -1,792 | -3,583 | -1,800 | -3,600 | 1102 / 1069 (77) | 0.25 | 0.37 | -2,775..-595 |  |
| CUTLINE_M7 | PREUW | 39 | 21,218 -> 24,609 (-16.0%) | -70,931 / -57,496 (-13,435) | -28,958 / -30,779 | -236 | -533 | -248 | -556 | 4201 / 4077 (342) | 0.31 | 0.38 | -1,453..+1,043 |  |
| CUTLINE_M7 | X' | 78 | 21,193 -> 19,020 (+10.3%) | -73,618 / -72,802 (-816) | -37,052 / -30,426 | +238 | +476 | +232 | +463 | 5816 / 5679 (309) | 0.64 | 0.55 | -224..+702 |  |
| CUTLINE_M7 | ALL43 | 187 | 20,839 -> 20,293 (+2.6%) | -74,402 / -82,315 (+7,914) | -43,527 / -46,116 | -68 | -150 | -79 | -172 | 18979 / 18422 (1341) | 0.39 | 0.45 | -543..+406 | +2.7% / 0.38 / -70 |
| CUTLINE_O7 | L3M | 13 | 9,863 -> 9,798 (+0.7%) | -22,565 / -22,565 (+0) | -13,430 / -13,430 | +116 | +231 | +116 | +231 | 1913 / 1913 (0) | 0.85 | 0.64 | +42..+187 | +0.9% / 0.83 / +124 |
| CUTLINE_O7 | L6M | 26 | 8,395 -> 8,356 (+0.5%) | -22,565 / -22,565 (+0) | -13,430 / -13,430 | +91 | +181 | +91 | +181 | 4161 / 4161 (0) | 0.94 | 0.67 | +46..+138 | +0.6% / 0.93 / +94 |
| CUTLINE_O7 | HOLD | 26 | 24,565 -> 24,530 (+0.1%) | -74,402 / -74,402 (+0) | -31,211 / -31,211 | -14 | -28 | -14 | -28 | 3219 / 3219 (0) | 0.94 | 0.89 | -197..+110 |  |
| CUTLINE_O7 | GAP | 13 | 21,175 -> 21,125 (+0.2%) | -55,206 / -55,320 (+114) | -43,527 / -43,527 | -88 | -175 | -88 | -175 | 1102 / 1102 (0) | 0.82 | 0.73 | -438..+126 |  |
| CUTLINE_O7 | PREUW | 39 | 24,161 -> 24,609 (-1.9%) | -70,931 / -70,931 (+0) | -28,958 / -28,958 | -38 | -76 | -38 | -76 | 4201 / 4201 (0) | 0.79 | 0.82 | -206..+104 |  |
| CUTLINE_O7 | X' | 78 | 19,089 -> 19,020 (+0.4%) | -73,618 / -72,931 (-687) | -37,052 / -37,052 | -44 | -87 | -44 | -88 | 5816 / 5815 (1) | 0.71 | 0.79 | -147..+51 |  |
| CUTLINE_O7 | ALL43 | 187 | 20,211 -> 20,293 (-0.4%) | -74,402 / -74,402 (+0) | -43,527 / -43,527 | -17 | -35 | -17 | -35 | 18979 / 18978 (1) | 0.83 | 0.85 | -80..+41 | -0.4% / 0.82 / -17 |
| CUTLINE_P7 | L3M | 13 | 12,077 -> 9,798 (+18.9%) | -22,565 / -34,674 (+12,110) | -13,430 / -23,470 | +2,204 | +3,654 | +2,161 | +3,572 | 1913 / 1818 (271) | 0.85 | 0.92 | -3,844..+7,623 | +12.7% / 0.64 / +1,350 |
| CUTLINE_P7 | L6M | 26 | 10,627 -> 8,356 (+21.4%) | -22,565 / -34,674 (+12,110) | -13,430 / -23,470 | +3,983 | +7,152 | +3,942 | +7,073 | 4161 / 3969 (502) | 0.99 | 1.00 | +570..+6,973 | +18.5% / 0.97 / +3,631 |
| CUTLINE_P7 | HOLD | 26 | 33,570 -> 24,530 (+26.9%) | -74,402 / -95,301 (+20,900) | -31,211 / -51,962 | +1,416 | +2,745 | +1,383 | +2,684 | 3219 / 3103 (438) | 0.86 | 0.86 | -2,132..+4,752 |  |
| CUTLINE_P7 | GAP | 13 | 21,358 -> 21,125 (+1.1%) | -55,206 / -53,353 (-1,852) | -43,527 / -40,328 | -1,196 | -2,269 | -1,213 | -2,301 | 1102 / 1067 (99) | 0.30 | 0.31 | -2,905..+561 |  |
| CUTLINE_P7 | PREUW | 39 | 19,927 -> 24,609 (-23.5%) | -70,931 / -55,028 (-15,904) | -28,958 / -28,021 | -1,732 | -3,487 | -1,758 | -3,536 | 4201 / 4064 (537) | 0.24 | 0.30 | -3,795..+274 |  |
| CUTLINE_P7 | X' | 78 | 21,585 -> 19,020 (+11.9%) | -73,618 / -87,144 (+13,526) | -37,052 / -35,070 | +778 | +1,378 | +768 | +1,358 | 5816 / 5675 (417) | 0.91 | 0.82 | -57..+1,612 |  |
| CUTLINE_P7 | ALL43 | 187 | 22,594 -> 20,293 (+10.2%) | -74,402 / -95,301 (+20,900) | -43,527 / -51,962 | +621 | +1,034 | +599 | +993 | 18979 / 18339 (2048) | 0.88 | 0.77 | -262..+1,515 | +10.1% / 0.86 / +557 |
| CUTLINE_U7 | L3M | 13 | 10,581 -> 9,798 (+7.4%) | -22,565 / -24,691 (+2,126) | -13,430 / -12,143 | +1,161 | +2,261 | +1,156 | +2,249 | 1913 / 1893 (20) | 0.52 | 0.51 | -393..+2,868 | +6.6% / 0.37 / +1,157 |
| CUTLINE_U7 | L6M | 26 | 9,037 -> 8,356 (+7.5%) | -22,565 / -24,691 (+2,126) | -13,430 / -12,143 | +1,022 | +1,974 | +1,018 | +1,966 | 4161 / 4133 (58) | 0.62 | 0.54 | +32..+2,009 | +7.0% / 0.50 / +1,015 |
| CUTLINE_U7 | HOLD | 26 | 26,210 -> 24,530 (+6.4%) | -74,402 / -75,206 (+804) | -31,211 / -32,553 | +420 | +840 | +422 | +844 | 3219 / 3234 (23) | 0.87 | 0.83 | -239..+1,036 |  |
| CUTLINE_U7 | GAP | 13 | 21,588 -> 21,125 (+2.1%) | -55,206 / -56,258 (+1,052) | -43,527 / -44,579 | -666 | -1,207 | -667 | -1,208 | 1102 / 1101 (5) | 0.55 | 0.73 | -1,889..+255 |  |
| CUTLINE_U7 | PREUW | 39 | 24,180 -> 24,609 (-1.8%) | -70,931 / -68,253 (-2,678) | -28,958 / -28,958 | +15 | -9 | +17 | -5 | 4201 / 4223 (42) | 0.42 | 0.45 | -298..+302 |  |
| CUTLINE_U7 | X' | 78 | 19,212 -> 19,020 (+1.0%) | -73,618 / -73,396 (-222) | -37,052 / -37,052 | +17 | +28 | +16 | +28 | 5816 / 5816 (2) | 0.59 | 0.54 | -136..+156 |  |
| CUTLINE_U7 | ALL43 | 187 | 20,664 -> 20,293 (+1.8%) | -74,402 / -75,206 (+804) | -43,527 / -44,579 | +172 | +332 | +172 | +332 | 18979 / 18984 (133) | 0.81 | 0.71 | -34..+389 | +1.8% / 0.80 / +167 |
| DAYCAPS | L3M | 13 | 9,751 -> 9,798 (-0.5%) | -22,565 / -22,508 (-56) | -13,430 / -13,430 | -1,475 | -2,750 | -1,453 | -2,709 | 1913 / 1953 (78) | 0.35 | 0.44 | -3,317..-88 | +1.1% / 0.74 / -1,471 |
| DAYCAPS | L6M | 26 | 8,554 -> 8,356 (+2.3%) | -22,565 / -22,508 (-56) | -13,430 / -13,430 | -351 | -604 | -338 | -581 | 4161 / 4203 (158) | 0.61 | 0.54 | -1,455..+493 | +3.8% / 0.90 / -311 |
| DAYCAPS | HOLD | 26 | 23,958 -> 24,530 (-2.4%) | -74,402 / -75,097 (+696) | -31,211 / -32,183 | -320 | -690 | -317 | -685 | 3219 / 3226 (63) | 0.32 | 0.41 | -1,202..+497 |  |
| DAYCAPS | GAP | 13 | 20,946 -> 21,125 (-0.9%) | -55,206 / -53,486 (-1,720) | -43,527 / -43,527 | -403 | -807 | -401 | -801 | 1102 / 1111 (9) | 0.18 | 0.31 | -824..+11 |  |
| DAYCAPS | PREUW | 39 | 22,264 -> 24,609 (-10.5%) | -70,931 / -65,275 (-5,657) | -28,958 / -28,958 | -575 | -1,173 | -569 | -1,160 | 4201 / 4264 (87) | 0.05 | 0.14 | -1,018..-140 |  |
| DAYCAPS | X' | 78 | 18,650 -> 19,020 (-2.0%) | -73,618 / -68,928 (-4,689) | -37,052 / -37,052 | -175 | -335 | -171 | -327 | 5816 / 5899 (103) | 0.18 | 0.36 | -400..+29 |  |
| DAYCAPS | ALL43 | 187 | 19,420 -> 20,293 (-4.5%) | -74,402 / -75,097 (+696) | -43,527 / -43,527 | -296 | -592 | -290 | -580 | 18979 / 19194 (445) | 0.08 | 0.30 | -548..-76 | -4.5% / 0.10 / -291 |
| DAYDONE | L3M | 13 | 16,331 -> 9,798 (+40.0%) | -22,565 / -37,707 (+15,143) | -13,430 / -21,691 | +3,216 | +6,073 | +3,313 | +6,266 | 1913 / 2215 (304) | 0.98 | 0.98 | +672..+5,202 | +44.8% / 0.94 / +3,122 |
| DAYDONE | L6M | 26 | 12,626 -> 8,356 (+33.8%) | -22,565 / -37,707 (+15,143) | -13,430 / -21,691 | +2,555 | +5,007 | +2,660 | +5,215 | 4161 / 4826 (667) | 0.91 | 0.90 | +779..+4,266 | +36.7% / 0.77 / +2,487 |
| DAYDONE | HOLD | 26 | 28,999 -> 24,530 (+15.4%) | -74,402 / -91,945 (+17,543) | -31,211 / -46,207 | +624 | +1,355 | +679 | +1,464 | 3219 / 3574 (357) | 0.71 | 0.69 | -1,084..+2,259 |  |
| DAYDONE | GAP | 13 | 21,209 -> 21,125 (+0.4%) | -55,206 / -55,478 (+272) | -43,527 / -43,799 | -274 | -548 | -272 | -543 | 1102 / 1111 (9) | 0.49 | 0.71 | -521..-34 |  |
| DAYDONE | PREUW | 39 | 24,350 -> 24,609 (-1.1%) | -70,931 / -64,631 (-6,300) | -28,958 / -23,739 | +306 | +582 | +338 | +645 | 4201 / 4524 (323) | 0.35 | 0.33 | -535..+1,179 |  |
| DAYDONE | X' | 78 | 18,339 -> 19,020 (-3.7%) | -73,618 / -61,977 (-11,641) | -37,052 / -28,884 | -191 | -382 | -187 | -373 | 5816 / 5905 (89) | 0.28 | 0.27 | -565..+124 |  |
| DAYDONE | ALL43 | 187 | 21,021 -> 20,293 (+3.5%) | -74,402 / -91,945 (+17,543) | -43,527 / -46,207 | +413 | +820 | +444 | +882 | 18979 / 20440 (1465) | 0.66 | 0.59 | -27..+841 | +3.4% / 0.64 / +394 |
| ERLADDER | L3M | 13 | 12,406 -> 9,798 (+21.0%) | -22,565 / -29,465 (+6,900) | -13,430 / -15,373 | -4,823 | -9,322 | -4,634 | -8,995 | 1913 / 1843 (446) | 0.50 | 0.61 | -8,093..-992 | +25.6% / 0.91 / -4,448 |
| ERLADDER | L6M | 26 | 13,632 -> 8,356 (+38.7%) | -22,565 / -47,129 (+24,564) | -13,430 / -45,257 | -2,811 | -4,347 | -2,620 | -4,017 | 4161 / 3967 (1042) | 0.76 | 0.83 | -6,767..+1,240 | +42.2% / 0.91 / -2,562 |
| ERLADDER | HOLD | 26 | 33,518 -> 24,530 (+26.8%) | -74,402 / -82,570 (+8,168) | -31,211 / -60,010 | +773 | +1,005 | +919 | +1,262 | 3219 / 3183 (804) | 0.86 | 0.86 | -3,512..+4,872 |  |
| ERLADDER | GAP | 13 | 27,701 -> 21,125 (+23.7%) | -55,206 / -72,111 (+16,906) | -43,527 / -55,737 | -3,524 | -7,032 | -3,410 | -6,830 | 1102 / 1139 (249) | 0.96 | 0.98 | -8,188..+1,627 |  |
| ERLADDER | PREUW | 39 | 18,881 -> 24,609 (-30.3%) | -70,931 / -50,089 (-20,842) | -28,958 / -33,585 | -1,905 | -3,133 | -1,785 | -2,918 | 4201 / 4229 (1124) | 0.43 | 0.48 | -4,499..+670 |  |
| ERLADDER | X' | 78 | 24,561 -> 19,020 (+22.6%) | -73,618 / -67,969 (-5,649) | -37,052 / -35,670 | -1,098 | -1,766 | -1,011 | -1,608 | 5816 / 6116 (1382) | 0.77 | 0.77 | -2,447..+278 |  |
| ERLADDER | ALL43 | 187 | 24,286 -> 20,293 (+16.4%) | -74,402 / -82,570 (+8,168) | -43,527 / -60,010 | -1,301 | -2,161 | -1,182 | -1,949 | 18979 / 19125 (4762) | 0.92 | 0.86 | -2,537..-52 | +16.5% / 0.94 / -1,260 |
| F3CTXCUT | L3M | 13 | 13,985 -> 9,798 (+29.9%) | -22,565 / -33,084 (+10,519) | -13,430 / -20,928 | +1,042 | +2,284 | +1,031 | +2,261 | 1913 / 1868 (201) | 0.98 | 0.98 | -2,951..+4,647 | +30.3% / 0.93 / +615 |
| F3CTXCUT | L6M | 26 | 11,056 -> 8,356 (+24.4%) | -22,565 / -33,084 (+10,519) | -13,430 / -20,928 | +1,706 | +3,390 | +1,692 | +3,361 | 4161 / 4079 (328) | 1.00 | 1.00 | -549..+3,856 | +23.5% / 0.99 / +1,523 |
| F3CTXCUT | HOLD | 26 | 30,680 -> 24,530 (+20.0%) | -74,402 / -76,641 (+2,239) | -31,211 / -44,541 | +852 | +1,734 | +834 | +1,700 | 3219 / 3140 (283) | 0.80 | 0.84 | -1,411..+3,110 |  |
| F3CTXCUT | GAP | 13 | 22,486 -> 21,125 (+6.1%) | -55,206 / -57,300 (+2,094) | -43,527 / -45,420 | -1,806 | -3,437 | -1,809 | -3,443 | 1102 / 1092 (72) | 0.86 | 0.96 | -4,680..+1,019 |  |
| F3CTXCUT | PREUW | 39 | 15,562 -> 24,609 (-58.1%) | -70,931 / -42,349 (-28,582) | -28,958 / -30,958 | -1,947 | -3,851 | -1,953 | -3,863 | 4201 / 4158 (385) | 0.17 | 0.29 | -3,499..-345 |  |
| F3CTXCUT | X' | 74 | 32,415 -> 20,812 (+35.8%) | -73,618 / -75,730 (+2,112) | -37,052 / -35,498 | +1,282 | +2,358 | +1,283 | +2,359 | 5496 / 5496 (422) | 0.99 | 0.95 | +303..+2,222 |  |
| F3CTXCUT | ALL43 | 183 | 26,037 -> 21,022 (+19.3%) | -74,402 / -76,641 (+2,239) | -43,527 / -45,420 | +325 | +574 | +320 | +563 | 18659 / 18448 (1519) | 0.93 | 0.83 | -415..+1,076 | +19.2% / 0.93 / +293 |
| GIVEBACKLOCK | L3M | 13 | 9,927 -> 9,798 (+1.3%) | -22,565 / -22,565 (+0) | -13,430 / -12,401 | -173 | -346 | -166 | -331 | 1913 / 1937 (38) | 0.19 | 0.20 | -1,452..+1,134 | +1.7% / 0.20 / -185 |
| GIVEBACKLOCK | L6M | 26 | 8,610 -> 8,356 (+2.9%) | -22,565 / -22,565 (+0) | -13,430 / -15,310 | -405 | -804 | -383 | -762 | 4161 / 4305 (164) | 0.68 | 0.63 | -1,384..+623 | +3.5% / 0.68 / -418 |
| GIVEBACKLOCK | HOLD | 26 | 23,435 -> 24,530 (-4.7%) | -74,402 / -74,902 (+500) | -31,211 / -31,711 | -1,178 | -2,351 | -1,165 | -2,325 | 3219 / 3307 (102) | 0.05 | 0.19 | -2,366..-139 |  |
| GIVEBACKLOCK | GAP | 13 | 21,241 -> 21,125 (+0.5%) | -55,206 / -56,016 (+810) | -43,527 / -43,527 | -372 | -744 | -371 | -742 | 1102 / 1106 (4) | 0.39 | 0.40 | -1,020..+102 |  |
| GIVEBACKLOCK | PREUW | 39 | 25,965 -> 24,609 (+5.2%) | -70,931 / -72,270 (+1,339) | -28,958 / -28,958 | +59 | +118 | +68 | +137 | 4201 / 4291 (90) | 0.72 | 0.68 | -277..+407 |  |
| GIVEBACKLOCK | X' | 78 | 18,815 -> 19,020 (-1.1%) | -73,618 / -72,613 (-1,005) | -37,052 / -37,052 | -277 | -554 | -275 | -549 | 5816 / 5860 (50) | 0.25 | 0.36 | -592..-5 |  |
| GIVEBACKLOCK | ALL43 | 187 | 20,389 -> 20,293 (+0.5%) | -74,402 / -74,902 (+500) | -43,527 / -43,527 | -371 | -742 | -364 | -726 | 18979 / 19358 (419) | 0.26 | 0.43 | -636..-115 | +0.5% / 0.26 / -373 |
| GOVERNOR | L3M | 13 | 10,039 -> 9,798 (+2.4%) | -22,565 / -24,930 (+2,365) | -13,430 / -13,473 | -230 | -368 | -227 | -363 | 1913 / 1918 (15) | 0.81 | 0.80 | -1,245..+517 | +0.9% / 0.50 / -439 |
| GOVERNOR | L6M | 26 | 8,932 -> 8,356 (+6.4%) | -22,565 / -24,930 (+2,365) | -13,430 / -13,473 | +393 | +865 | +395 | +870 | 4161 / 4165 (56) | 0.80 | 0.76 | -333..+1,161 | +6.4% / 0.47 / +312 |
| GOVERNOR | HOLD | 26 | 24,887 -> 24,530 (+1.4%) | -74,402 / -74,402 (+0) | -31,211 / -31,211 | +45 | -24 | +47 | -20 | 3219 / 3222 (27) | 0.42 | 0.39 | -629..+654 |  |
| GOVERNOR | GAP | 13 | 21,125 -> 21,125 (+0.0%) | -55,206 / -55,206 (+0) | -43,527 / -43,527 | +0 | +0 | +0 | +0 | 1102 / 1102 (0) | 0.50 | 0.50 | +0..+0 |  |
| GOVERNOR | PREUW | 39 | 24,063 -> 24,609 (-2.3%) | -70,931 / -70,931 (+0) | -28,958 / -28,958 | -33 | -84 | -31 | -80 | 4201 / 4219 (22) | 0.19 | 0.34 | -190..+110 |  |
| GOVERNOR | X' | 78 | 19,020 -> 19,020 (+0.0%) | -73,618 / -73,618 (+0) | -37,052 / -37,052 | +0 | +0 | +0 | +0 | 5816 / 5816 (0) | 0.51 | 0.51 | +0..+0 |  |
| GOVERNOR | ALL43 | 187 | 20,251 -> 20,293 (-0.2%) | -74,402 / -74,402 (+0) | -43,527 / -43,527 | +55 | +101 | +56 | +103 | 18979 / 19004 (105) | 0.49 | 0.47 | -104..+204 | -0.2% / 0.42 / +42 |
| K7FLAT45 | L3M | 13 | 11,803 -> 9,798 (+17.0%) | -22,565 / -29,457 (+6,893) | -13,430 / -20,300 | +900 | +1,494 | +893 | +1,479 | 1913 / 1874 (269) | 0.98 | 0.98 | -1,611..+3,102 | +16.2% / 0.93 / +427 |
| K7FLAT45 | L6M | 26 | 9,623 -> 8,356 (+13.2%) | -22,565 / -29,457 (+6,893) | -13,430 / -20,300 | +1,298 | +2,522 | +1,283 | +2,491 | 4161 / 4042 (531) | 0.88 | 0.88 | -515..+2,932 | +11.7% / 0.68 / +1,083 |
| K7FLAT45 | HOLD | 26 | 28,226 -> 24,530 (+13.1%) | -74,402 / -74,910 (+508) | -31,211 / -29,489 | +105 | +189 | +99 | +175 | 3219 / 3173 (430) | 0.89 | 0.79 | -2,006..+2,107 |  |
| K7FLAT45 | GAP | 13 | 15,956 -> 21,125 (-32.4%) | -55,206 / -44,711 (-10,494) | -43,527 / -31,148 | -1,224 | -2,335 | -1,237 | -2,360 | 1102 / 1057 (163) | 0.35 | 0.37 | -3,167..+697 |  |
| K7FLAT45 | PREUW | 39 | 19,255 -> 24,609 (-27.8%) | -70,931 / -56,452 (-14,479) | -28,958 / -28,392 | -879 | -1,832 | -892 | -1,857 | 4201 / 4067 (570) | 0.15 | 0.30 | -2,021..+225 |  |
| K7FLAT45 | X' | 78 | 15,928 -> 19,020 (-19.4%) | -73,618 / -48,012 (-25,606) | -37,052 / -27,079 | -496 | -968 | -506 | -989 | 5816 / 5615 (827) | 0.21 | 0.23 | -1,340..+325 |  |
| K7FLAT45 | ALL43 | 187 | 18,115 -> 20,293 (-12.0%) | -74,402 / -74,910 (+508) | -43,527 / -31,148 | -272 | -556 | -284 | -578 | 18979 / 18412 (2583) | 0.35 | 0.37 | -893..+339 | -12.2% / 0.32 / -309 |
| L2GATE | L3M | 13 | 33,357 -> 9,798 (+70.6%) | -22,565 / -87,131 (+64,566) | -13,430 / -49,266 | +4,652 | +8,656 | +5,050 | +9,310 | 1913 / 1634 (793) | 0.99 | 1.00 | -4,956..+13,612 | +73.9% / 0.99 / +4,942 |
| L2GATE | L6M | 26 | 30,860 -> 8,356 (+72.9%) | -22,565 / -91,977 (+69,412) | -13,430 / -64,233 | +2,399 | +6,449 | +2,849 | +7,192 | 4161 / 3526 (1893) | 1.00 | 1.00 | -6,741..+11,340 | +75.0% / 1.00 / +2,463 |
| L2GATE | HOLD | 26 | 51,123 -> 24,530 (+52.0%) | -74,402 / -107,136 (+32,734) | -31,211 / -68,722 | +320 | +673 | +674 | +1,269 | 3219 / 2933 (1454) | 0.99 | 0.98 | -5,936..+6,271 |  |
| L2GATE | GAP | 13 | 39,913 -> 21,125 (+47.1%) | -55,206 / -108,284 (+53,078) | -43,527 / -66,425 | -1,707 | -3,976 | -1,489 | -3,608 | 1102 / 1083 (377) | 0.97 | 0.96 | -9,171..+5,911 |  |
| L2GATE | PREUW | 39 | 18,079 -> 24,609 (-36.1%) | -70,931 / -61,203 (-9,728) | -28,958 / -24,049 | -8,500 | -14,576 | -8,185 | -14,044 | 4201 / 3893 (1794) | 0.04 | 0.10 | -11,776..-4,780 |  |
| L2GATE | X' | 78 | 46,301 -> 19,020 (+58.9%) | -73,618 / -106,391 (+32,773) | -37,052 / -45,133 | -979 | -1,679 | -789 | -1,358 | 5816 / 5626 (2056) | 0.97 | 0.97 | -4,254..+2,218 |  |
| L2GATE | ALL43 | 187 | 39,811 -> 20,293 (+49.0%) | -74,402 / -108,284 (+33,882) | -43,527 / -68,722 | -1,716 | -2,621 | -1,435 | -2,150 | 18979 / 17512 (7815) | 1.00 | 0.98 | -4,111..+645 | +49.1% / 1.00 / -1,726 |
| LOT | L3M | 13 | 11,438 -> 9,798 (+14.3%) | -22,565 / -31,858 (+9,293) | -13,430 / -20,388 | -440 | +139 | -369 | +251 | 1913 / 1867 (118) | 0.64 | 0.65 | -3,313..+2,298 | +11.0% / 0.19 / -1,228 |
| LOT | L6M | 26 | 9,375 -> 8,356 (+10.9%) | -22,565 / -31,858 (+9,293) | -13,430 / -20,388 | -3,596 | -5,473 | -3,510 | -5,331 | 4161 / 4131 (188) | 0.68 | 0.71 | -5,981..-1,144 | +7.8% / 0.24 / -4,083 |
| LOT | HOLD | 26 | 23,541 -> 24,530 (-4.2%) | -74,402 / -76,296 (+1,894) | -31,211 / -56,161 | -1,540 | -2,471 | -1,500 | -2,408 | 3219 / 3184 (139) | 0.63 | 0.69 | -3,217..+632 |  |
| LOT | GAP | 13 | 21,031 -> 21,125 (-0.4%) | -55,206 / -58,472 (+3,267) | -43,527 / -45,701 | -1,655 | -2,884 | -1,621 | -2,828 | 1102 / 1097 (35) | 0.30 | 0.43 | -2,863..-292 |  |
| LOT | PREUW | 39 | 25,983 -> 24,609 (+5.3%) | -70,931 / -84,356 (+13,425) | -28,958 / -34,290 | -2,400 | -3,814 | -2,350 | -3,731 | 4201 / 4196 (235) | 0.51 | 0.62 | -3,785..-805 |  |
| LOT | X' | 78 | 18,437 -> 19,020 (-3.2%) | -73,618 / -80,049 (+6,431) | -37,052 / -40,082 | -1,462 | -2,607 | -1,427 | -2,550 | 5816 / 5785 (241) | 0.37 | 0.56 | -2,151..-698 |  |
| LOT | ALL43 | 187 | 20,219 -> 20,293 (-0.4%) | -74,402 / -84,356 (+9,954) | -43,527 / -56,161 | -1,868 | -3,052 | -1,822 | -2,976 | 18979 / 18870 (877) | 0.59 | 0.69 | -2,482..-1,205 | -0.5% / 0.58 / -1,927 |
| NTZ | L3M | 13 | 11,124 -> 9,798 (+11.9%) | -22,565 / -29,686 (+7,122) | -13,430 / -13,712 | +2,097 | +3,406 | +2,116 | +3,438 | 1913 / 1882 (163) | 0.71 | 0.71 | -141..+4,146 | +10.0% / 0.53 / +2,030 |
| NTZ | L6M | 26 | 9,282 -> 8,356 (+10.0%) | -22,565 / -29,686 (+7,122) | -13,430 / -13,712 | +196 | +91 | +215 | +123 | 4161 / 4110 (297) | 0.39 | 0.47 | -1,788..+2,178 | +8.3% / 0.17 / +100 |
| NTZ | HOLD | 26 | 32,188 -> 24,530 (+23.8%) | -74,402 / -85,364 (+10,963) | -31,211 / -40,982 | -51 | +78 | -23 | +128 | 3219 / 3213 (332) | 0.96 | 0.95 | -2,208..+2,224 |  |
| NTZ | GAP | 13 | 21,756 -> 21,125 (+2.9%) | -55,206 / -56,425 (+1,219) | -43,527 / -42,053 | -2,116 | -3,658 | -2,077 | -3,591 | 1102 / 1102 (156) | 0.57 | 0.57 | -4,616..+392 |  |
| NTZ | PREUW | 39 | 26,771 -> 24,609 (+8.1%) | -70,931 / -71,974 (+1,043) | -28,958 / -36,376 | -2,023 | -3,855 | -1,989 | -3,794 | 4201 / 4210 (479) | 0.49 | 0.60 | -3,359..-596 |  |
| NTZ | X' | 78 | 28,510 -> 19,020 (+33.3%) | -73,618 / -66,599 (-7,019) | -37,052 / -41,928 | +981 | +1,856 | +1,007 | +1,900 | 5816 / 5775 (839) | 0.99 | 0.96 | -155..+2,173 |  |
| NTZ | ALL43 | 187 | 26,204 -> 20,293 (+22.6%) | -74,402 / -85,364 (+10,963) | -43,527 / -42,053 | -136 | -250 | -108 | -202 | 18979 / 18881 (2130) | 0.97 | 0.91 | -889..+603 | +22.6% / 0.98 / -151 |
| OTE62 | L3M | 13 | 10,089 -> 9,798 (+2.9%) | -22,565 / -24,706 (+2,141) | -13,430 / -13,236 | +912 | +1,506 | +902 | +1,486 | 1913 / 1890 (53) | 0.45 | 0.42 | -886..+2,888 | +1.0% / 0.33 / +802 |
| OTE62 | L6M | 26 | 8,764 -> 8,356 (+4.7%) | -22,565 / -24,706 (+2,141) | -13,430 / -13,236 | +833 | +1,474 | +824 | +1,459 | 4161 / 4134 (77) | 0.61 | 0.52 | -170..+1,882 | +3.9% / 0.49 / +777 |
| OTE62 | HOLD | 26 | 24,025 -> 24,530 (-2.1%) | -74,402 / -71,486 (-2,916) | -31,211 / -32,410 | +222 | +378 | +219 | +374 | 3219 / 3238 (53) | 0.77 | 0.79 | -520..+956 |  |
| OTE62 | GAP | 13 | 20,956 -> 21,125 (-0.8%) | -55,206 / -54,961 (-244) | -43,527 / -44,068 | -139 | -362 | -148 | -377 | 1102 / 1104 (28) | 0.26 | 0.46 | -1,176..+1,246 |  |
| OTE62 | PREUW | 39 | 22,107 -> 24,609 (-11.3%) | -70,931 / -66,405 (-4,526) | -28,958 / -30,152 | +55 | +174 | +50 | +165 | 4201 / 4195 (126) | 0.16 | 0.27 | -597..+652 |  |
| OTE62 | X' | 78 | 18,959 -> 19,020 (-0.3%) | -73,618 / -73,618 (+0) | -37,052 / -40,638 | +169 | +207 | +164 | +200 | 5816 / 5852 (170) | 0.60 | 0.59 | -407..+693 |  |
| OTE62 | ALL43 | 187 | 19,560 -> 20,293 (-3.7%) | -74,402 / -73,618 (-784) | -43,527 / -44,068 | +311 | +506 | +305 | +496 | 18979 / 19006 (467) | 0.61 | 0.57 | -44..+678 | -3.8% / 0.58 / +301 |
| P7CONFIRM | L3M | 13 | 9,932 -> 9,798 (+1.3%) | -22,565 / -22,881 (+316) | -13,430 / -14,794 | +53 | +267 | +57 | +275 | 1913 / 1921 (66) | 0.79 | 0.79 | -1,006..+990 | +1.8% / 0.81 / +56 |
| P7CONFIRM | L6M | 26 | 8,415 -> 8,356 (+0.7%) | -22,565 / -22,881 (+316) | -13,430 / -14,794 | +194 | +470 | +197 | +475 | 4161 / 4172 (97) | 0.77 | 0.76 | -445..+758 | +0.8% / 0.80 / +201 |
| P7CONFIRM | HOLD | 26 | 24,919 -> 24,530 (+1.6%) | -74,402 / -74,842 (+440) | -31,211 / -33,455 | +178 | +284 | +179 | +286 | 3219 / 3226 (59) | 0.94 | 0.91 | -147..+497 |  |
| P7CONFIRM | GAP | 13 | 22,835 -> 21,125 (+7.5%) | -55,206 / -59,218 (+4,013) | -43,527 / -46,778 | +251 | +502 | +256 | +511 | 1102 / 1114 (40) | 0.72 | 0.73 | -475..+910 |  |
| P7CONFIRM | PREUW | 39 | 25,155 -> 24,609 (+2.2%) | -70,931 / -72,938 (+2,007) | -28,958 / -28,958 | -414 | -784 | -412 | -779 | 4201 / 4214 (161) | 0.43 | 0.56 | -1,016..+117 |  |
| P7CONFIRM | X' | 78 | 19,496 -> 19,020 (+2.4%) | -73,618 / -74,418 (+800) | -37,052 / -36,282 | -76 | -154 | -75 | -152 | 5816 / 5837 (175) | 0.38 | 0.40 | -234..+78 |  |
| P7CONFIRM | ALL43 | 187 | 20,826 -> 20,293 (+2.6%) | -74,402 / -74,842 (+440) | -43,527 / -46,778 | -41 | -73 | -39 | -69 | 18979 / 19049 (540) | 0.70 | 0.68 | -224..+139 | +2.6% / 0.72 / -42 |
| REG | L3M | 13 | 10,188 -> 9,798 (+3.8%) | -22,565 / -23,650 (+1,085) | -13,430 / -13,430 | -389 | -518 | -373 | -492 | 1913 / 1914 (3) | 0.17 | 0.28 | -1,161..+486 | +3.0% / 0.42 / -383 |
| REG | L6M | 26 | 9,195 -> 8,356 (+9.1%) | -22,565 / -23,650 (+1,085) | -13,430 / -13,430 | +671 | +1,162 | +693 | +1,199 | 4161 / 4150 (35) | 0.68 | 0.58 | -846..+2,312 | +9.7% / 0.80 / +709 |
| REG | HOLD | 26 | 26,203 -> 24,530 (+6.4%) | -74,402 / -68,396 (-6,006) | -31,211 / -31,211 | -1,095 | -1,758 | -1,064 | -1,707 | 3219 / 3257 (80) | 0.62 | 0.57 | -2,400..+462 |  |
| REG | GAP | 13 | 22,212 -> 21,125 (+4.9%) | -55,206 / -57,691 (+2,486) | -43,527 / -44,867 | +357 | +503 | +368 | +520 | 1102 / 1101 (13) | 0.91 | 0.89 | -281..+909 |  |
| REG | PREUW | 39 | 28,215 -> 24,609 (+12.8%) | -70,931 / -78,340 (+7,409) | -28,958 / -28,958 | -345 | -514 | -336 | -499 | 4201 / 4172 (45) | 0.80 | 0.84 | -1,130..+455 |  |
| REG | X' | 78 | 21,594 -> 19,020 (+11.9%) | -73,618 / -67,576 (-6,042) | -37,052 / -33,882 | -224 | -382 | -215 | -368 | 5816 / 5798 (104) | 0.40 | 0.35 | -718..+259 |  |
| REG | ALL43 | 187 | 22,562 -> 20,293 (+10.1%) | -74,402 / -78,340 (+3,938) | -43,527 / -44,867 | -212 | -341 | -198 | -318 | 18979 / 18962 (289) | 0.75 | 0.65 | -606..+203 | +10.1% / 0.73 / -211 |
| SIGQ | L3M | 13 | 11,343 -> 9,798 (+13.6%) | -22,565 / -30,750 (+8,186) | -13,430 / -21,535 | -278 | +138 | -236 | +206 | 1913 / 1852 (133) | 0.92 | 0.92 | -3,044..+2,642 | +17.0% / 0.81 / -597 |
| SIGQ | L6M | 26 | 10,058 -> 8,356 (+16.9%) | -22,565 / -30,750 (+8,186) | -13,430 / -21,535 | -456 | -320 | -400 | -225 | 4161 / 4065 (268) | 0.89 | 0.90 | -2,281..+1,408 | +19.4% / 0.80 / -616 |
| SIGQ | HOLD | 26 | 26,999 -> 24,530 (+9.1%) | -74,402 / -70,781 (-3,621) | -31,211 / -30,428 | -457 | -793 | -413 | -718 | 3219 / 3174 (157) | 0.56 | 0.52 | -1,999..+1,213 |  |
| SIGQ | GAP | 13 | 22,686 -> 21,125 (+6.9%) | -55,206 / -60,434 (+5,229) | -43,527 / -45,021 | +123 | +135 | +137 | +158 | 1102 / 1101 (31) | 0.84 | 0.89 | -2,003..+1,968 |  |
| SIGQ | PREUW | 39 | 27,022 -> 24,609 (+8.9%) | -70,931 / -81,493 (+10,562) | -28,958 / -33,788 | -782 | -1,107 | -741 | -1,035 | 4201 / 4177 (248) | 0.54 | 0.60 | -2,193..+611 |  |
| SIGQ | X' | 78 | 19,629 -> 19,020 (+3.1%) | -73,618 / -76,405 (+2,787) | -37,052 / -42,362 | -140 | -277 | -126 | -253 | 5816 / 5803 (127) | 0.71 | 0.72 | -713..+429 |  |
| SIGQ | ALL43 | 187 | 21,768 -> 20,293 (+6.8%) | -74,402 / -81,493 (+7,091) | -43,527 / -45,021 | -259 | -337 | -229 | -286 | 18979 / 18789 (856) | 0.80 | 0.74 | -804..+276 | +6.8% / 0.79 / -280 |
| STACKCAP | L3M | 13 | 11,171 -> 9,798 (+12.3%) | -22,565 / -28,205 (+5,640) | -13,430 / -13,500 | -325 | -628 | -316 | -610 | 1913 / 1929 (62) | 0.77 | 0.69 | -1,637..+947 | +15.5% / 0.93 / -328 |
| STACKCAP | L6M | 26 | 9,277 -> 8,356 (+9.9%) | -22,565 / -28,205 (+5,640) | -13,430 / -13,500 | -437 | -912 | -429 | -897 | 4161 / 4180 (115) | 0.79 | 0.64 | -1,208..+351 | +11.7% / 0.94 / -442 |
| STACKCAP | HOLD | 26 | 28,540 -> 24,530 (+14.1%) | -74,402 / -82,010 (+7,608) | -31,211 / -40,273 | -274 | -523 | -265 | -505 | 3219 / 3243 (176) | 0.92 | 0.91 | -1,559..+1,083 |  |
| STACKCAP | GAP | 13 | 20,913 -> 21,125 (-1.0%) | -55,206 / -53,741 (-1,465) | -43,527 / -43,633 | -1,036 | -1,855 | -1,029 | -1,842 | 1102 / 1112 (96) | 0.62 | 0.86 | -2,519..+291 |  |
| STACKCAP | PREUW | 39 | 26,106 -> 24,609 (+5.7%) | -70,931 / -77,015 (+6,084) | -28,958 / -32,679 | -1,470 | -2,840 | -1,459 | -2,818 | 4201 / 4250 (273) | 0.32 | 0.54 | -2,321..-599 |  |
| STACKCAP | X' | 78 | 24,609 -> 19,020 (+22.7%) | -73,618 / -80,517 (+6,899) | -37,052 / -37,052 | +555 | +1,126 | +561 | +1,137 | 5816 / 5858 (574) | 0.98 | 0.94 | -244..+1,319 |  |
| STACKCAP | ALL43 | 187 | 23,760 -> 20,293 (+14.6%) | -74,402 / -82,010 (+7,608) | -43,527 / -43,633 | -273 | -510 | -265 | -495 | 18979 / 19122 (1249) | 0.96 | 0.88 | -738..+188 | +14.6% / 0.96 / -272 |
| STACKCUT | L3M | 13 | 11,634 -> 9,798 (+15.8%) | -22,565 / -28,226 (+5,662) | -13,430 / -19,702 | -197 | -533 | -192 | -523 | 1913 / 1934 (73) | 0.98 | 0.98 | -2,743..+1,820 | +19.3% / 0.94 / -228 |
| STACKCUT | L6M | 26 | 9,353 -> 8,356 (+10.7%) | -22,565 / -28,226 (+5,662) | -13,430 / -19,702 | -398 | -848 | -393 | -838 | 4161 / 4197 (126) | 0.81 | 0.86 | -1,853..+722 | +12.3% / 0.79 / -419 |
| STACKCUT | HOLD | 26 | 24,890 -> 24,530 (+1.4%) | -74,402 / -75,339 (+937) | -31,211 / -33,282 | +543 | +1,021 | +538 | +1,012 | 3219 / 3197 (60) | 0.94 | 0.93 | +55..+958 |  |
| STACKCUT | GAP | 13 | 22,432 -> 21,125 (+5.8%) | -55,206 / -56,874 (+1,668) | -43,527 / -45,316 | -475 | -901 | -477 | -903 | 1102 / 1098 (24) | 0.56 | 0.70 | -1,489..+624 |  |
| STACKCUT | PREUW | 39 | 21,116 -> 24,609 (-16.5%) | -70,931 / -61,576 (-9,355) | -28,958 / -27,589 | -729 | -1,394 | -729 | -1,395 | 4201 / 4205 (90) | 0.13 | 0.25 | -1,513..-42 |  |
| STACKCUT | X' | 78 | 20,330 -> 19,020 (+6.4%) | -73,618 / -74,527 (+909) | -37,052 / -37,666 | +90 | +205 | +89 | +204 | 5816 / 5801 (125) | 0.41 | 0.46 | -331..+516 |  |
| STACKCUT | ALL43 | 187 | 20,208 -> 20,293 (-0.4%) | -74,402 / -75,339 (+937) | -43,527 / -45,316 | -198 | -372 | -198 | -373 | 18979 / 18983 (448) | 0.46 | 0.56 | -541..+136 | -0.4% / 0.45 / -200 |
| STATECUT_ALL | L3M | 13 | 15,220 -> 9,798 (+35.6%) | -22,565 / -38,820 (+16,255) | -13,430 / -20,565 | +5,079 | +9,962 | +5,037 | +9,877 | 1913 / 1772 (325) | 1.00 | 1.00 | +999..+9,246 | +39.6% / 1.00 / +5,127 |
| STATECUT_ALL | L6M | 26 | 11,720 -> 8,356 (+28.7%) | -22,565 / -38,820 (+16,255) | -13,430 / -20,565 | +2,132 | +4,211 | +2,096 | +4,139 | 4161 / 3916 (667) | 1.00 | 0.99 | -596..+4,941 | +30.7% / 1.00 / +2,056 |
| STATECUT_ALL | HOLD | 26 | 26,835 -> 24,530 (+8.6%) | -74,402 / -72,792 (-1,610) | -31,211 / -28,659 | -802 | -1,604 | -830 | -1,661 | 3219 / 3038 (523) | 0.49 | 0.44 | -3,090..+1,451 |  |
| STATECUT_ALL | GAP | 13 | 20,105 -> 21,125 (-5.1%) | -55,206 / -51,328 (-3,878) | -43,527 / -47,105 | -2,475 | -4,961 | -2,487 | -4,984 | 1102 / 1058 (116) | 0.28 | 0.41 | -4,526..-373 |  |
| STATECUT_ALL | PREUW | 39 | 17,003 -> 24,609 (-44.7%) | -70,931 / -47,117 (-23,814) | -28,958 / -26,866 | -267 | -636 | -286 | -674 | 4201 / 4002 (649) | 0.34 | 0.37 | -1,831..+1,249 |  |
| STATECUT_ALL | X' | 78 | 20,145 -> 19,020 (+5.6%) | -73,618 / -59,727 (-13,891) | -37,052 / -35,163 | -101 | -190 | -110 | -208 | 5816 / 5635 (475) | 0.59 | 0.54 | -674..+461 |  |
| STATECUT_ALL | ALL43 | 187 | 19,691 -> 20,293 (-3.1%) | -74,402 / -72,792 (-1,610) | -43,527 / -47,105 | -108 | -231 | -126 | -267 | 18979 / 18103 (2538) | 0.66 | 0.60 | -825..+597 | -3.1% / 0.64 / -128 |

## Section S0 - all layers together per book: JL2 book (layers ON) vs raw S0 single-book cell (no layers, native table lots, 60-pt stop / own target, book alone)
DIFFERENT BASE: the raw cells are not "JL2 with all layers off" for the stack (each book runs alone, no cross-book effects, native lots = session table lots, no halvings) so the difference is "all layers + stack interactions" together, not a sum of Table 1. Cell = ulcer JL2 -> raw (cut by layers, %) / mean $/wk base JL2 -> raw / trades JL2 -> raw. Positive cut = layers lower the ulcer. TL3_RB_S0_U7 lacks 202309 (dropped from both for X' and ALL43). X3 X4 X5 raw books are not in JL2 (shadow), not compared.

| book | L3M | L6M | HOLD | GAP | PREUW | X' | ALL43 |
|--|--|--|--|--|--|--|--|
| K7 | 6139 -> 49519 (+88%) / +3075 -> -1545 / 743 -> 800 | 5436 -> 39737 (+86%) / +4524 -> +2673 / 1622 -> 1886 | 19548 -> 58618 (+67%) / +2543 -> +1122 / 1265 -> 1374 | 10742 -> 16154 (+34%) / +2515 -> +6239 / 408 -> 361 | 13592 -> 11737 (-16%) / +1327 -> +2966 / 1655 -> 1640 | 14454 -> 25542 (+43%) / +1357 -> +2256 / 2170 -> 2001 | 16409 -> 32886 (+50%) / +2196 -> +2734 / 7304 -> 7440 |
| M7 | 10987 -> 21783 (+50%) / +784 -> +315 / 334 -> 375 | 20867 -> 40473 (+48%) / -307 -> -436 / 741 -> 848 | 12837 -> 13328 (+4%) / +103 -> +1153 / 686 -> 687 | 6635 -> 8818 (+25%) / -87 -> +803 / 237 -> 213 | 8581 -> 12293 (+30%) / +771 -> +1300 / 891 -> 860 | 27373 -> 49938 (+45%) / -329 -> -660 / 1307 -> 1190 | 27989 -> 47244 (+41%) / -20 -> +241 / 3970 -> 3899 |
| U7 | 5168 -> 14335 (+64%) / +3075 -> +584 / 117 -> 132 | 6536 -> 12375 (+47%) / +2911 -> +2538 / 266 -> 295 | 16137 -> 28665 (+44%) / +403 -> -177 / 213 -> 225 | 7174 -> 11045 (+35%) / +1292 -> +1246 / 82 -> 79 | 9778 -> 21104 (+54%) / +859 -> +3227 / 284 -> 291 | 18139 -> 34499 (+47%) / +966 -> +1060 / 425 -> 428 | 14369 -> 27557 (+48%) / +1386 -> +1846 / 1302 -> 1349 |
| P7 | 11085 -> 32395 (+66%) / +9299 -> +15316 / 453 -> 620 | 8360 -> 41608 (+80%) / +12015 -> +19861 / 952 -> 1475 | 12369 -> 46238 (+73%) / +4290 -> +6457 / 648 -> 1029 | 7242 -> 46703 (+84%) / +1792 -> +7453 / 200 -> 267 | 22502 -> 89228 (+75%) / +606 -> +94 / 837 -> 1262 | 13092 -> 80398 (+84%) / +1192 -> +2446 / 988 -> 1442 | 14651 -> 80608 (+82%) / +3171 -> +5759 / 3704 -> 5595 |
| H7 | 3089 -> 16232 (+81%) / +1069 -> +968 / 84 -> 92 | 4265 -> 18816 (+77%) / +1766 -> +1823 / 177 -> 197 | 15788 -> 16222 (+3%) / -721 -> +137 / 134 -> 141 | 6060 -> 32190 (+81%) / +1334 -> +291 / 78 -> 77 | 7013 -> 14030 (+50%) / +1542 -> +1838 / 218 -> 230 | 14428 -> 24119 (+40%) / +799 -> +1604 / 422 -> 420 | 15549 -> 24833 (+37%) / +855 -> +1283 / 1056 -> 1095 |
| A7 | 4024 -> 4571 (+12%) / -88 -> -392 / 160 -> 167 | 3761 -> 4756 (+21%) / +772 -> +603 / 353 -> 361 | 4484 -> 6096 (+26%) / +823 -> +837 / 211 -> 216 | 4182 -> 5574 (+25%) / -134 -> -312 / 64 -> 64 | 3154 -> 2284 (-38%) / +1246 -> +1332 / 208 -> 205 | 5058 -> 5753 (+12%) / +522 -> +513 / 285 -> 285 | 4390 -> 5077 (+14%) / +710 -> +685 / 1156 -> 1165 |
| O7 | 1932 -> 2506 (+23%) / +353 -> +37 / 22 -> 30 | 2530 -> 3718 (+32%) / +394 -> +319 / 50 -> 67 | 1233 -> 1717 (+28%) / +918 -> +1028 / 62 -> 73 | 1058 -> 1078 (+2%) / +879 -> +982 / 33 -> 33 | 2210 -> 2618 (+16%) / +807 -> +831 / 108 -> 118 | 7114 -> 6011 (-18%) / +161 -> +209 / 197 -> 200 | 4896 -> 4433 (-10%) / +472 -> +510 / 465 -> 506 |


## Reproduce
code/th_rebuild_s5/rb5_score.py (scoring, pickle /mnt/l2/l2vast/_rebuild/s5/s5_res.pkl), rb5_page.py (this page), rb5_s0.py (S0 section); every number in DS3_REBUILD_S5_numbers.csv (layer x window x book x pnl variant). Seal manifest sha 759f2258daac9d28 unchanged; no engine run, no spend.
