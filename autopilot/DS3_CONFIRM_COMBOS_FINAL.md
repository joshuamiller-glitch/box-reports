# DS3_CONFIRM_COMBOS_FINAL — CF-COMBO (rewritten 2026-10-31 05:16Z)

## 0. Verdict (CF-COMBO, 2026-10-31)
- **Nothing is PASS.** Cumulative-trial DSR < 0.95 for every row; stage-level White RC on PRE+X' is p<0.05 for PE, ST, HM, WT, DN, PB, MV but 0.18 (KB), 0.18 (SM), 0.20 (MA) on stage1ENG.
- **Most of every gain is STRUCTURE** (70/30 base + a resting limit / waiting for the dip): random-level limits at the same distances earn +2.0..+3.7 per contract, shuffled-day pairs +1..+3, and a dip-only learned model (no confirmation feature) earns within 0.6 pts of the full learned model in all six books tested (confirmation features add +0.42 SM, +0.28 PE, +0.07 KB, -0.10 HM, -0.23 DN, -0.57 ST per contract L6M).
- **What survives the unit check** (stack > 0 in L6M and HOLD, random-level placebo beaten, excess over the better member CI>0): 22 ordered/simultaneous array pairs on stage1ENG (KB 5, PE 1, ST 2, HM 8, SM 3, MV 3; 'iplFVG / iFVG / FVG then OB or FVG within 60 s', mostly mechanic c2/b at the far or mid of the second array) plus 1 on the pooled cross-stage (PB: 30-s FVG AND CF-A weekly-swing VAL). The information part is the excess over the single array: +0.4..+3.6 per contract vs A alone, +0.3..+1.9 vs B alone; lead rows HM 'implied FVG 30 s then OB 30 s, limit at the far edge', SM 'implied FVG 15 s then OB 30 s, limit at the mean', MV, PE.
- **Pooled cross-stage (ENG+CF-A+CF-B+bars+C2) added almost nothing** beyond the single-source stages: 1 INFO row of 10 books (PB). Greedy-forward (<=5 conditions) rarely adds beyond 2: the dominant single member is a level (pd50 / VWAP) on the F0.7 bases. Four-legged (location+momentum+flow+context) on SM and DN: the flow/context legs are filters that remove P&L (negative single gains), no INFO rows.
- **Not measured:** capacity at book depth, 1-s latency for the market mechanics beyond the shifted-event approximation (delay 1 s / 3 s changes the gain by < 0.15 pt), submin streams (summaries only, not combinable), live-lot $ uses an assumed tag map and 20 $/pt.

Masks capped 20260206, UNTOUCHED never read; selection on PRE+X' only; one recent look per stage x book (logs: out/confirm/combo/looks.jsonl, DECISIONS.md); floor = plain 70/30 3-pt dip; every gain is the ALL-signal paired gain vs the floor (skipped/unconfirmed signals keep the floor). Units: per planned lot (engine o0), per contract of final position (o0/lots, primary), lock-engine stack $/wk (research lots, engine books ST HM WT KB SM PE only), and $/wk at the user's live lots (20 $/pt; assumed tag map K6=KB P6=PE U6=SM H6=HM M6=MV A6=PB; research 1 lot where the live lot is 0 is shown separately). Page-1 detail and all stage sections: DS3_CONFIRM_COMBOS.md.

## 1. Sunday table — ordered / simultaneous array combinations that survived the unit check (INFO-CANDIDATE: stack>0, random-level placebo beaten, excess over best member CI>0)

One row per (book, array pair, window) with its best mechanic; the other mechanics of the same pair are in section 2. Tiers: nothing is PASS (cumulative-trial DSR < 0.95); "CANDIDATE-RECENT" = positive L6M and HOLD, placebo-beaten, beats its better member; the mechanic is a resting-limit / 70-30 structure, so the INFORMATION part is the excess over the single array (columns A / B alone).

| book | rule (A then B within W) | mechanic | base | per planned lot L6M | per contract L6M (HOLD) | stack $/wk L6M (HOLD) | $/wk at live lots (1 lot) | trades/wk (of signals/wk) | random-level placebo rank (mean) | shuffled-day +3/+7/+11 d | 3-s delay | excess vs A alone [CI] | excess vs B alone [CI] | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HM | THEN60s(iplFVG~30s+OB~30s) | c2_far | 70/30 | +0.95 | +3.68 (+3.58) | +5328 (+3392) | +3911 (+2392) | 17.9 (32.5) | 1/101 (+2.77) | +1.65/+2.81/+1.25 | +3.59 | +1.65 [+0.93,+2.43] | +0.81 [+0.43,+1.20] | CANDIDATE-RECENT |
| HM | THEN60s(iFVG~30s+OB~30s) | c2_far | 70/30 | +0.35 | +3.64 (+3.50) | +6511 (+4731) | +3615 (+2365) | 17.6 (32.5) | 1/101 (+2.79) | +1.57/+2.45/+1.14 | +3.55 | +0.91 [+0.32,+1.52] | +0.77 [+0.24,+1.30] | CANDIDATE-RECENT |
| HM | THEN300s(iplFVG~30s+OB~30s) | c2_far | 70/30 | +0.85 | +3.56 (+3.46) | +7486 (+5302) | +3794 (+2311) | 18.9 (32.5) | 1/101 (+2.67) | +1.81/+3.00/+1.21 | +3.44 | +1.52 [+0.80,+2.27] | +0.69 [+0.28,+1.09] | CANDIDATE-RECENT |
| HM | THEN60s(FVG~15s+OB~30s) | c2_far | 70/30 | +0.16 | +3.23 (+3.13) | +6647 (+4436) | +3322 (+2094) | 19.5 (32.5) | 1/101 (+2.49) | +1.57/+2.14/+1.15 | +3.21 | +0.51 [-0.11,+1.16] | +0.35 [+0.15,+0.66] | CANDIDATE-RECENT (weak: beats A alone fails) |
| KB | THEN60s(iplFVG~45s+iFVG~15s) | c2_far | 70/30 | +0.41 | +3.04 (+3.07) | +666 (+501) | +5231 (+2726) | 29.0 (44.9) | 8/201 (+2.58) | +1.29/+2.52/+1.25 | +3.02 | +0.75 [-0.07,+1.56] | +0.53 [+0.26,+0.84] | CANDIDATE-RECENT (weak: beats A alone fails) |
| KB | THEN60s(iplFVG~30s+iFVG~15s) | c2_far | 70/30 | +0.53 | +2.96 (+3.02) | +951 (+726) | +5116 (+2661) | 30.0 (44.9) | 6/201 (+2.59) | +1.35/+2.26/+1.23 | +3.14 | +0.84 [+0.33,+1.32] | +0.46 [+0.21,+0.72] | CANDIDATE-RECENT |
| KB | THEN60s(iFVG~15s+FVG~15s) | c2_far | 70/30 | +0.35 | +2.87 (+2.84) | +2288 (+2035) | +4735 (+2574) | 29.5 (44.9) | 5/201 (+2.41) | +1.47/+2.29/+1.16 | +2.84 | +0.36 [-0.13,+0.94] | +0.26 [+0.11,+0.41] | CANDIDATE-RECENT (weak: beats A alone fails) |
| KB | THEN300s(iplFVG~45s+iFVG~15s) | c2_far | 70/30 | +0.29 | +2.87 (+2.90) | +1417 (+1010) | +4953 (+2573) | 31.6 (44.9) | 6/201 (+2.46) | +1.23/+2.56/+1.34 | +2.86 | +0.58 [-0.14,+1.27] | +0.36 [+0.17,+0.59] | CANDIDATE-RECENT (weak: beats A alone fails) |
| KB | THEN60s(FVG~15s+FVG~2m) | c2_near | 70/30 | +0.45 | +2.62 (+2.61) | +1559 (+1337) | +4001 (+2352) | 24.6 (44.9) | 5/201 (+2.17) | +0.86/+2.27/+1.33 | +2.50 | +1.07 [+0.38,+1.87] | +0.61 [+0.23,+0.94] | CANDIDATE-RECENT |
| MV | THEN60s(iplFVG~30s+OB~30s) | c2_mid | 70/30 | +0.65 | +4.13 (+4.09) | +nan (+nan) | +3356 (+3339) | 25.8 (40.4) | 4/101 (+3.66) | +1.20/+3.13/+1.14 | +4.01 | +2.02 [+1.27,+2.92] | +0.69 [+0.23,+1.19] | CANDIDATE-RECENT |
| MV | THEN60s(iplFVG~1m+OB~30s) | b_far | 70/30 | +0.53 | +3.62 (+3.75) | +nan (+nan) | +2574 (+2921) | 23.2 (40.4) | 5/101 (+3.16) | +1.04/+2.75/+0.93 | +3.55 | +2.02 [+1.19,+2.94] | +0.76 [+0.17,+1.34] | CANDIDATE-RECENT |
| MV | THEN60s(iplFVG~45s+OB~1m) | b_far | 70/30 | +0.75 | +3.50 (+3.54) | +nan (+nan) | +2242 (+2826) | 20.2 (40.4) | 1/101 (+2.92) | +1.15/+2.56/+0.98 | +3.71 | +1.57 [+0.92,+2.23] | +0.92 [+0.26,+1.63] | CANDIDATE-RECENT |
| PB | AND(FVG~30s+CFA:val~sw15) | c2_mid | 70/30 | -1.33 | +3.05 (+3.38) | +nan (+nan) | +1878 (+1889) | 16.5 (30.9) | 1/101 (+2.46) | +0.82/+2.36/+1.31 | +1.60 | +1.08 [+0.38,+1.83] | +3.05 [+2.31,+3.77] | CANDIDATE-RECENT |
| PE | THEN60s(iFVG~30s+OB~1m) | c2_far | 70/30 | +0.90 | +3.07 (+3.11) | +287 (+137) | +15115 (+2617) | 21.2 (42.6) | 1/101 (+2.47) | +1.16/+2.43/+0.60 | +3.06 | +1.26 [+0.38,+2.21] | +0.57 [+0.24,+0.97] | CANDIDATE-RECENT |
| SM | THEN60s(iplFVG~15s+OB~30s) | c2_mid | 70/30 | +1.13 | +5.19 (+4.74) | +2808 (+915) | +2051 (+1207) | 7.2 (11.6) | 1/101 (+3.20) | +0.76/+2.88/+0.23 | +5.18 | +3.60 [+2.20,+5.02] | +1.89 [+0.69,+3.20] | CANDIDATE-RECENT |
| ST | THEN60s(iplFVG~15s+OB~1m) | b_mid | 70/30 | -0.80 | +1.91 (+1.92) | +3658 (+2248) | +0 (+1717) | 21.2 (44.9) | 4/101 (+1.63) | +0.02/+1.32/-0.22 | +2.16 | +1.14 [+0.35,+1.99] | +0.74 [+0.29,+1.14] | CANDIDATE-RECENT |

Live-lot $/wk = sum over the book's L6M signals of (per-contract gain x live lot of the signal's session) x 20 $/pt / weeks (live lots per autopilot/FOLLOWUP_BRIEF.md; PE 7 Asia/London/NY-AM, KB 2, SM 4 Asia/London, HM 4 Asia / 2 NY-AM, MV 2 London/NY-AM; sessions with live lot 0 contribute 0; the bracket value is the same sum at 1 lot in every session). Engine caveat: the stack column is the lock-engine difference at research lots, ST/MV have partly NaN or non-live stacks.

## 2. Rule dossiers (exact rule as a D6 confirmation)

### KB: THEN60s(FVG~15s+FVG~2m)  [stage1ENG]

**Rule.** FIRST a fair-value gap (3-bar gap >= 1 pt) forms in favour on the 15s bar close (FVG|15s), THEN within 60 s a fair-value gap (3-bar gap >= 1 pt) forms in favour on the 2m bar close (FVG|2m); the entry second is the first print second at which the second array is knowable (closed bar) after the first started. Base: 70% of the planned lot at the signal (the usual 3-pt dip split base), the remaining 30% risk-sized (<=2 lots total, target re-based on the average). Mechanic: once the dip >= 3 pts has started, remainder as a resting limit at the near edge (the edge facing price) of the second array's zone. Hold dies at the original stop level.

Mechanics tested (per contract L6M / HOLD): c2_near +2.62/+2.61.

Controls on the best mechanic (c2_near|F0.7): random-level placebo rank 5/201 (placebo mean +2.17); shuffled-day pair (+3/+7/+11 d) +0.86, +2.27, +1.33; delay 1 s +2.60, 3 s +2.50 (the array becomes knowable and the order is placed that many seconds later); leave-one-out: A alone +1.55, B alone +2.01, combination +2.62 (excess vs A +1.07, vs B +0.61, so the second array adds over the first and the first adds over the second).

Per session (L6M per contract): {'asia': 1.62, 'london': 2.78, 'nyam': 2.1, 'nypm': 3.34, 'pre': 8.4}. Fill: 55% of signals fire (24.6/wk of 44.9); lots at the fill median 1.10, max 2.00 (capacity at book depth was not measured: it needs L2 depth at the fill; the position is at most 2 lots per signal).

Walk-forward chain (book level: monthly re-selection among the book's 50 PRE+X'-selected cell x variants on closed trades only, >=13 weeks history): OOS L6M +2.87, HOLD +2.88 per contract; last re-fit 202602 picked ('054bda81ef8d', 'c2_far|F0.7') (trailing +2.79); 32 monthly re-fits.

### KB: THEN60s(iplFVG~45s+iFVG~15s)  [stage1ENG]

**Rule.** FIRST an implied FVG (body gap, wicks overlap) forms in favour on the 45s bar close (iplFVG|45s), THEN within 60 s an inverse FVG (an FVG closed through) forms in favour on the 15s bar close (iFVG|15s); the entry second is the first print second at which the second array is knowable (closed bar) after the first started. Base: 70% of the planned lot at the signal (the usual 3-pt dip split base), the remaining 30% risk-sized (<=2 lots total, target re-based on the average). Mechanic: once the dip >= 3 pts has started, remainder as a resting limit at the far edge of the second array's zone. Hold dies at the original stop level.

Mechanics tested (per contract L6M / HOLD): c2_far +3.04/+3.07.

Controls on the best mechanic (c2_far|F0.7): random-level placebo rank 8/201 (placebo mean +2.58); shuffled-day pair (+3/+7/+11 d) +1.29, +2.52, +1.25; delay 1 s +3.01, 3 s +3.02 (the array becomes knowable and the order is placed that many seconds later); leave-one-out: A alone +2.28, B alone +2.50, combination +3.04 (excess vs A +0.75, vs B +0.53, so the second array does not significantly add over the first and the first adds over the second).

Per session (L6M per contract): {'asia': 3.29, 'london': 2.02, 'nyam': 2.7, 'nypm': 4.39, 'pre': 2.65}. Fill: 65% of signals fire (29.0/wk of 44.9); lots at the fill median 1.08, max 2.00 (capacity at book depth was not measured: it needs L2 depth at the fill; the position is at most 2 lots per signal).

Walk-forward chain (book level: monthly re-selection among the book's 50 PRE+X'-selected cell x variants on closed trades only, >=13 weeks history): OOS L6M +2.87, HOLD +2.88 per contract; last re-fit 202602 picked ('054bda81ef8d', 'c2_far|F0.7') (trailing +2.79); 32 monthly re-fits.

### KB: THEN60s(iplFVG~30s+iFVG~15s)  [stage1ENG]

**Rule.** FIRST an implied FVG (body gap, wicks overlap) forms in favour on the 30s bar close (iplFVG|30s), THEN within 60 s an inverse FVG (an FVG closed through) forms in favour on the 15s bar close (iFVG|15s); the entry second is the first print second at which the second array is knowable (closed bar) after the first started. Base: 70% of the planned lot at the signal (the usual 3-pt dip split base), the remaining 30% risk-sized (<=2 lots total, target re-based on the average). Mechanic: once the dip >= 3 pts has started, remainder as a resting limit at the far edge of the second array's zone. Hold dies at the original stop level.

Mechanics tested (per contract L6M / HOLD): c2_far +2.96/+3.02.

Controls on the best mechanic (c2_far|F0.7): random-level placebo rank 6/201 (placebo mean +2.59); shuffled-day pair (+3/+7/+11 d) +1.35, +2.26, +1.23; delay 1 s +3.03, 3 s +3.14 (the array becomes knowable and the order is placed that many seconds later); leave-one-out: A alone +2.12, B alone +2.50, combination +2.96 (excess vs A +0.84, vs B +0.46, so the second array adds over the first and the first adds over the second).

Per session (L6M per contract): {'asia': 2.42, 'london': 2.1, 'nyam': 3.36, 'nypm': 4.12, 'pre': 2.41}. Fill: 67% of signals fire (30.0/wk of 44.9); lots at the fill median 1.08, max 2.00 (capacity at book depth was not measured: it needs L2 depth at the fill; the position is at most 2 lots per signal).

Walk-forward chain (book level: monthly re-selection among the book's 50 PRE+X'-selected cell x variants on closed trades only, >=13 weeks history): OOS L6M +2.87, HOLD +2.88 per contract; last re-fit 202602 picked ('054bda81ef8d', 'c2_far|F0.7') (trailing +2.79); 32 monthly re-fits.

### KB: THEN60s(iFVG~15s+FVG~15s)  [stage1ENG]

**Rule.** FIRST an inverse FVG (an FVG closed through) forms in favour on the 15s bar close (iFVG|15s), THEN within 60 s a fair-value gap (3-bar gap >= 1 pt) forms in favour on the 15s bar close (FVG|15s); the entry second is the first print second at which the second array is knowable (closed bar) after the first started. Base: 70% of the planned lot at the signal (the usual 3-pt dip split base), the remaining 30% risk-sized (<=2 lots total, target re-based on the average). Mechanic: once the dip >= 3 pts has started, remainder as a resting limit at the far edge of the second array's zone. Hold dies at the original stop level.

Mechanics tested (per contract L6M / HOLD): c2_far +2.87/+2.84.

Controls on the best mechanic (c2_far|F0.7): random-level placebo rank 5/201 (placebo mean +2.41); shuffled-day pair (+3/+7/+11 d) +1.47, +2.29, +1.16; delay 1 s +2.83, 3 s +2.84 (the array becomes knowable and the order is placed that many seconds later); leave-one-out: A alone +2.50, B alone +2.61, combination +2.87 (excess vs A +0.36, vs B +0.26, so the second array does not significantly add over the first and the first adds over the second).

Per session (L6M per contract): {'asia': 2.04, 'london': 2.23, 'nyam': 2.88, 'nypm': 4.18, 'pre': 4.64}. Fill: 66% of signals fire (29.5/wk of 44.9); lots at the fill median 1.09, max 2.00 (capacity at book depth was not measured: it needs L2 depth at the fill; the position is at most 2 lots per signal).

Walk-forward chain (book level: monthly re-selection among the book's 50 PRE+X'-selected cell x variants on closed trades only, >=13 weeks history): OOS L6M +2.87, HOLD +2.88 per contract; last re-fit 202602 picked ('054bda81ef8d', 'c2_far|F0.7') (trailing +2.79); 32 monthly re-fits.

### KB: THEN300s(iplFVG~45s+iFVG~15s)  [stage1ENG]

**Rule.** FIRST an implied FVG (body gap, wicks overlap) forms in favour on the 45s bar close (iplFVG|45s), THEN within 300 s an inverse FVG (an FVG closed through) forms in favour on the 15s bar close (iFVG|15s); the entry second is the first print second at which the second array is knowable (closed bar) after the first started. Base: 70% of the planned lot at the signal (the usual 3-pt dip split base), the remaining 30% risk-sized (<=2 lots total, target re-based on the average). Mechanic: once the dip >= 3 pts has started, remainder as a resting limit at the far edge of the second array's zone. Hold dies at the original stop level.

Mechanics tested (per contract L6M / HOLD): c2_far +2.87/+2.90.

Controls on the best mechanic (c2_far|F0.7): random-level placebo rank 6/201 (placebo mean +2.46); shuffled-day pair (+3/+7/+11 d) +1.23, +2.56, +1.34; delay 1 s +2.86, 3 s +2.86 (the array becomes knowable and the order is placed that many seconds later); leave-one-out: A alone +2.28, B alone +2.50, combination +2.87 (excess vs A +0.58, vs B +0.36, so the second array does not significantly add over the first and the first adds over the second).

Per session (L6M per contract): {'asia': 3.08, 'london': 1.92, 'nyam': 2.79, 'nypm': 3.81, 'pre': 2.31}. Fill: 70% of signals fire (31.6/wk of 44.9); lots at the fill median 1.07, max 2.00 (capacity at book depth was not measured: it needs L2 depth at the fill; the position is at most 2 lots per signal).

Walk-forward chain (book level: monthly re-selection among the book's 50 PRE+X'-selected cell x variants on closed trades only, >=13 weeks history): OOS L6M +2.87, HOLD +2.88 per contract; last re-fit 202602 picked ('054bda81ef8d', 'c2_far|F0.7') (trailing +2.79); 32 monthly re-fits.

### PE: THEN60s(iFVG~30s+OB~1m)  [stage1ENG]

**Rule.** FIRST an inverse FVG (an FVG closed through) forms in favour on the 30s bar close (iFVG|30s), THEN within 60 s an order block (last opposite bar before a >=1-ATR displacement bar, within 3 bars) forms in favour on the 1m bar close (OB|1m); the entry second is the first print second at which the second array is knowable (closed bar) after the first started. Base: 70% of the planned lot at the signal (the usual 3-pt dip split base), the remaining 30% risk-sized (<=2 lots total, target re-based on the average). Mechanic: once the dip >= 3 pts has started, remainder as a resting limit at the far edge of the second array's zone. Hold dies at the original stop level.

Mechanics tested (per contract L6M / HOLD): c2_far +3.07/+3.11.

Controls on the best mechanic (c2_far|F0.7): random-level placebo rank 1/101 (placebo mean +2.47); shuffled-day pair (+3/+7/+11 d) +1.16, +2.43, +0.60; delay 1 s +3.13, 3 s +3.06 (the array becomes knowable and the order is placed that many seconds later); leave-one-out: A alone +1.81, B alone +2.50, combination +3.07 (excess vs A +1.26, vs B +0.57, so the second array adds over the first and the first adds over the second).

Per session (L6M per contract): {'asia': 3.4, 'london': 6.82, 'nyam': 1.15, 'nypm': 2.3, 'pre': 1.79}. Fill: 50% of signals fire (21.2/wk of 42.6); lots at the fill median 1.13, max 2.00 (capacity at book depth was not measured: it needs L2 depth at the fill; the position is at most 2 lots per signal).

Walk-forward chain (book level: monthly re-selection among the book's 50 PRE+X'-selected cell x variants on closed trades only, >=13 weeks history): OOS L6M +3.01, HOLD +3.06 per contract; last re-fit 202602 picked ('183d2224494a', 'c2_far|F0.7') (trailing +3.69); 32 monthly re-fits.

### ST: THEN60s(iplFVG~15s+OB~1m)  [stage1ENG]

**Rule.** FIRST an implied FVG (body gap, wicks overlap) forms in favour on the 15s bar close (iplFVG|15s), THEN within 60 s an order block (last opposite bar before a >=1-ATR displacement bar, within 3 bars) forms in favour on the 1m bar close (OB|1m); the entry second is the first print second at which the second array is knowable (closed bar) after the first started. Base: 70% of the planned lot at the signal (the usual 3-pt dip split base), the remaining 30% risk-sized (<=2 lots total, target re-based on the average). Mechanic: remainder as a RESTING LIMIT at the mean / CE of the second array's zone, placed at the entry second, resting until the hold dies (original stop / target second, opposite signal, session lots 0, flatten). Hold dies at the original stop level.

Mechanics tested (per contract L6M / HOLD): b_mid +1.91/+1.92; b_near +1.87/+1.97.

Controls on the best mechanic (b_mid|F0.7): random-level placebo rank 4/101 (placebo mean +1.63); shuffled-day pair (+3/+7/+11 d) +0.02, +1.32, -0.22; delay 1 s +2.10, 3 s +2.16 (the array becomes knowable and the order is placed that many seconds later); leave-one-out: A alone +0.78, B alone +1.17, combination +1.91 (excess vs A +1.14, vs B +0.74, so the second array adds over the first and the first adds over the second).

Per session (L6M per contract): {'asia': 2.28, 'london': 1.83, 'nyam': 1.17, 'nypm': 2.21, 'pre': 4.43}. Fill: 47% of signals fire (21.2/wk of 44.9); lots at the fill median 1.12, max 2.00 (capacity at book depth was not measured: it needs L2 depth at the fill; the position is at most 2 lots per signal).

Walk-forward chain (book level: monthly re-selection among the book's 50 PRE+X'-selected cell x variants on closed trades only, >=13 weeks history): OOS L6M +2.60, HOLD +2.53 per contract; last re-fit 202602 picked ('a024d66df3e6', 'c2_far|F0.7') (trailing +3.09); 32 monthly re-fits.

### HM: THEN60s(iplFVG~30s+OB~30s)  [stage1ENG]

**Rule.** FIRST an implied FVG (body gap, wicks overlap) forms in favour on the 30s bar close (iplFVG|30s), THEN within 60 s an order block (last opposite bar before a >=1-ATR displacement bar, within 3 bars) forms in favour on the 30s bar close (OB|30s); the entry second is the first print second at which the second array is knowable (closed bar) after the first started. Base: 70% of the planned lot at the signal (the usual 3-pt dip split base), the remaining 30% risk-sized (<=2 lots total, target re-based on the average). Mechanic: once the dip >= 3 pts has started, remainder as a resting limit at the far edge of the second array's zone. Hold dies at the original stop level.

Mechanics tested (per contract L6M / HOLD): c2_far +3.68/+3.58; b_far +3.54/+3.42; c2_mid +3.46/+3.46.

Controls on the best mechanic (c2_far|F0.7): random-level placebo rank 1/101 (placebo mean +2.77); shuffled-day pair (+3/+7/+11 d) +1.65, +2.81, +1.25; delay 1 s +3.61, 3 s +3.59 (the array becomes knowable and the order is placed that many seconds later); leave-one-out: A alone +2.04, B alone +2.87, combination +3.68 (excess vs A +1.65, vs B +0.81, so the second array adds over the first and the first adds over the second).

Per session (L6M per contract): {'asia': 4.53, 'london': 4.36, 'nyam': 1.76, 'nypm': 3.74, 'pre': 5.17}. Fill: 55% of signals fire (17.9/wk of 32.5); lots at the fill median 1.11, max 2.00 (capacity at book depth was not measured: it needs L2 depth at the fill; the position is at most 2 lots per signal).

Walk-forward chain (book level: monthly re-selection among the book's 50 PRE+X'-selected cell x variants on closed trades only, >=13 weeks history): OOS L6M +3.23, HOLD +3.13 per contract; last re-fit 202602 picked ('257c11746c9d', 'c2_far|F0.7') (trailing +3.29); 32 monthly re-fits.

### HM: THEN60s(iFVG~30s+OB~30s)  [stage1ENG]

**Rule.** FIRST an inverse FVG (an FVG closed through) forms in favour on the 30s bar close (iFVG|30s), THEN within 60 s an order block (last opposite bar before a >=1-ATR displacement bar, within 3 bars) forms in favour on the 30s bar close (OB|30s); the entry second is the first print second at which the second array is knowable (closed bar) after the first started. Base: 70% of the planned lot at the signal (the usual 3-pt dip split base), the remaining 30% risk-sized (<=2 lots total, target re-based on the average). Mechanic: once the dip >= 3 pts has started, remainder as a resting limit at the far edge of the second array's zone. Hold dies at the original stop level.

Mechanics tested (per contract L6M / HOLD): c2_far +3.64/+3.50; b_far +3.39/+3.24.

Controls on the best mechanic (c2_far|F0.7): random-level placebo rank 1/101 (placebo mean +2.79); shuffled-day pair (+3/+7/+11 d) +1.57, +2.45, +1.14; delay 1 s +3.57, 3 s +3.55 (the array becomes knowable and the order is placed that many seconds later); leave-one-out: A alone +2.74, B alone +2.87, combination +3.64 (excess vs A +0.91, vs B +0.77, so the second array adds over the first and the first adds over the second).

Per session (L6M per contract): {'asia': 3.99, 'london': 3.33, 'nyam': 2.08, 'nypm': 4.82, 'pre': 6.53}. Fill: 54% of signals fire (17.6/wk of 32.5); lots at the fill median 1.10, max 2.00 (capacity at book depth was not measured: it needs L2 depth at the fill; the position is at most 2 lots per signal).

Walk-forward chain (book level: monthly re-selection among the book's 50 PRE+X'-selected cell x variants on closed trades only, >=13 weeks history): OOS L6M +3.23, HOLD +3.13 per contract; last re-fit 202602 picked ('257c11746c9d', 'c2_far|F0.7') (trailing +3.29); 32 monthly re-fits.

### HM: THEN300s(iplFVG~30s+OB~30s)  [stage1ENG]

**Rule.** FIRST an implied FVG (body gap, wicks overlap) forms in favour on the 30s bar close (iplFVG|30s), THEN within 300 s an order block (last opposite bar before a >=1-ATR displacement bar, within 3 bars) forms in favour on the 30s bar close (OB|30s); the entry second is the first print second at which the second array is knowable (closed bar) after the first started. Base: 70% of the planned lot at the signal (the usual 3-pt dip split base), the remaining 30% risk-sized (<=2 lots total, target re-based on the average). Mechanic: once the dip >= 3 pts has started, remainder as a resting limit at the far edge of the second array's zone. Hold dies at the original stop level.

Mechanics tested (per contract L6M / HOLD): c2_far +3.56/+3.46.

Controls on the best mechanic (c2_far|F0.7): random-level placebo rank 1/101 (placebo mean +2.67); shuffled-day pair (+3/+7/+11 d) +1.81, +3.00, +1.21; delay 1 s +3.45, 3 s +3.44 (the array becomes knowable and the order is placed that many seconds later); leave-one-out: A alone +2.04, B alone +2.87, combination +3.56 (excess vs A +1.52, vs B +0.69, so the second array adds over the first and the first adds over the second).

Per session (L6M per contract): {'asia': 4.31, 'london': 4.01, 'nyam': 1.91, 'nypm': 3.56, 'pre': 5.56}. Fill: 58% of signals fire (18.9/wk of 32.5); lots at the fill median 1.09, max 2.00 (capacity at book depth was not measured: it needs L2 depth at the fill; the position is at most 2 lots per signal).

Walk-forward chain (book level: monthly re-selection among the book's 50 PRE+X'-selected cell x variants on closed trades only, >=13 weeks history): OOS L6M +3.23, HOLD +3.13 per contract; last re-fit 202602 picked ('257c11746c9d', 'c2_far|F0.7') (trailing +3.29); 32 monthly re-fits.

### HM: THEN60s(FVG~15s+OB~30s)  [stage1ENG]

**Rule.** FIRST a fair-value gap (3-bar gap >= 1 pt) forms in favour on the 15s bar close (FVG|15s), THEN within 60 s an order block (last opposite bar before a >=1-ATR displacement bar, within 3 bars) forms in favour on the 30s bar close (OB|30s); the entry second is the first print second at which the second array is knowable (closed bar) after the first started. Base: 70% of the planned lot at the signal (the usual 3-pt dip split base), the remaining 30% risk-sized (<=2 lots total, target re-based on the average). Mechanic: once the dip >= 3 pts has started, remainder as a resting limit at the far edge of the second array's zone. Hold dies at the original stop level.

Mechanics tested (per contract L6M / HOLD): c2_far +3.23/+3.13; b_far +3.11/+3.00.

Controls on the best mechanic (c2_far|F0.7): random-level placebo rank 1/101 (placebo mean +2.49); shuffled-day pair (+3/+7/+11 d) +1.57, +2.14, +1.15; delay 1 s +3.24, 3 s +3.21 (the array becomes knowable and the order is placed that many seconds later); leave-one-out: A alone +2.71, B alone +2.87, combination +3.23 (excess vs A +0.51, vs B +0.35, so the second array does not significantly add over the first and the first adds over the second).

Per session (L6M per contract): {'asia': 3.54, 'london': 2.59, 'nyam': 2.2, 'nypm': 4.07, 'pre': 6.43}. Fill: 60% of signals fire (19.5/wk of 32.5); lots at the fill median 1.09, max 2.00 (capacity at book depth was not measured: it needs L2 depth at the fill; the position is at most 2 lots per signal).

Walk-forward chain (book level: monthly re-selection among the book's 50 PRE+X'-selected cell x variants on closed trades only, >=13 weeks history): OOS L6M +3.23, HOLD +3.13 per contract; last re-fit 202602 picked ('257c11746c9d', 'c2_far|F0.7') (trailing +3.29); 32 monthly re-fits.

### SM: THEN60s(iplFVG~15s+OB~30s)  [stage1ENG]

**Rule.** FIRST an implied FVG (body gap, wicks overlap) forms in favour on the 15s bar close (iplFVG|15s), THEN within 60 s an order block (last opposite bar before a >=1-ATR displacement bar, within 3 bars) forms in favour on the 30s bar close (OB|30s); the entry second is the first print second at which the second array is knowable (closed bar) after the first started. Base: 70% of the planned lot at the signal (the usual 3-pt dip split base), the remaining 30% risk-sized (<=2 lots total, target re-based on the average). Mechanic: once the dip >= 3 pts has started, remainder as a resting limit at the mean / CE of the second array's zone. Hold dies at the original stop level.

Mechanics tested (per contract L6M / HOLD): c2_mid +5.19/+4.74; c2_near +4.68/+4.26; c2_far +4.60/+4.06.

Controls on the best mechanic (c2_mid|F0.7): random-level placebo rank 1/101 (placebo mean +3.20); shuffled-day pair (+3/+7/+11 d) +0.76, +2.88, +0.23; delay 1 s +5.11, 3 s +5.18 (the array becomes knowable and the order is placed that many seconds later); leave-one-out: A alone +1.59, B alone +3.30, combination +5.19 (excess vs A +3.60, vs B +1.89, so the second array adds over the first and the first adds over the second).

Per session (L6M per contract): {'asia': 3.61, 'london': 4.12, 'nyam': 4.67, 'nypm': 9.21, 'pre': 14.82}. Fill: 62% of signals fire (7.2/wk of 11.6); lots at the fill median 1.10, max 2.00 (capacity at book depth was not measured: it needs L2 depth at the fill; the position is at most 2 lots per signal).

Walk-forward chain (book level: monthly re-selection among the book's 50 PRE+X'-selected cell x variants on closed trades only, >=13 weeks history): OOS L6M +4.89, HOLD +4.12 per contract; last re-fit 202602 picked ('18395cc91e15', 'c2_far|F0.7') (trailing +4.25); 30 monthly re-fits.

### MV: THEN60s(iplFVG~45s+OB~1m)  [stage1ENG]

**Rule.** FIRST an implied FVG (body gap, wicks overlap) forms in favour on the 45s bar close (iplFVG|45s), THEN within 60 s an order block (last opposite bar before a >=1-ATR displacement bar, within 3 bars) forms in favour on the 1m bar close (OB|1m); the entry second is the first print second at which the second array is knowable (closed bar) after the first started. Base: 70% of the planned lot at the signal (the usual 3-pt dip split base), the remaining 30% risk-sized (<=2 lots total, target re-based on the average). Mechanic: remainder as a RESTING LIMIT at the far edge of the second array's zone, placed at the entry second, resting until the hold dies (original stop / target second, opposite signal, session lots 0, flatten). Hold dies at the original stop level.

Mechanics tested (per contract L6M / HOLD): b_far +3.50/+3.54.

Controls on the best mechanic (b_far|F0.7): random-level placebo rank 1/101 (placebo mean +2.92); shuffled-day pair (+3/+7/+11 d) +1.15, +2.56, +0.98; delay 1 s +3.58, 3 s +3.71 (the array becomes knowable and the order is placed that many seconds later); leave-one-out: A alone +1.93, B alone +2.58, combination +3.50 (excess vs A +1.57, vs B +0.92, so the second array adds over the first and the first adds over the second).

Per session (L6M per contract): {'asia': 4.7, 'london': 5.73, 'nyam': 0.78, 'nypm': 3.46, 'pre': 4.02}. Fill: 50% of signals fire (20.2/wk of 40.4); lots at the fill median 1.12, max 2.00 (capacity at book depth was not measured: it needs L2 depth at the fill; the position is at most 2 lots per signal).

Walk-forward chain (book level: monthly re-selection among the book's 50 PRE+X'-selected cell x variants on closed trades only, >=13 weeks history): OOS L6M +3.99, HOLD +3.98 per contract; last re-fit 202602 picked ('0380818a97f6', 'c2_far|F0.7') (trailing +4.18); 32 monthly re-fits.

### MV: THEN60s(iplFVG~30s+OB~30s)  [stage1ENG]

**Rule.** FIRST an implied FVG (body gap, wicks overlap) forms in favour on the 30s bar close (iplFVG|30s), THEN within 60 s an order block (last opposite bar before a >=1-ATR displacement bar, within 3 bars) forms in favour on the 30s bar close (OB|30s); the entry second is the first print second at which the second array is knowable (closed bar) after the first started. Base: 70% of the planned lot at the signal (the usual 3-pt dip split base), the remaining 30% risk-sized (<=2 lots total, target re-based on the average). Mechanic: once the dip >= 3 pts has started, remainder as a resting limit at the mean / CE of the second array's zone. Hold dies at the original stop level.

Mechanics tested (per contract L6M / HOLD): c2_mid +4.13/+4.09.

Controls on the best mechanic (c2_mid|F0.7): random-level placebo rank 4/101 (placebo mean +3.66); shuffled-day pair (+3/+7/+11 d) +1.20, +3.13, +1.14; delay 1 s +4.13, 3 s +4.01 (the array becomes knowable and the order is placed that many seconds later); leave-one-out: A alone +2.11, B alone +3.44, combination +4.13 (excess vs A +2.02, vs B +0.69, so the second array adds over the first and the first adds over the second).

Per session (L6M per contract): {'asia': 3.62, 'london': 4.53, 'nyam': 3.98, 'nypm': 5.0, 'pre': 3.41}. Fill: 64% of signals fire (25.8/wk of 40.4); lots at the fill median 1.11, max 2.00 (capacity at book depth was not measured: it needs L2 depth at the fill; the position is at most 2 lots per signal).

Walk-forward chain (book level: monthly re-selection among the book's 50 PRE+X'-selected cell x variants on closed trades only, >=13 weeks history): OOS L6M +3.99, HOLD +3.98 per contract; last re-fit 202602 picked ('0380818a97f6', 'c2_far|F0.7') (trailing +4.18); 32 monthly re-fits.

### MV: THEN60s(iplFVG~1m+OB~30s)  [stage1ENG]

**Rule.** FIRST an implied FVG (body gap, wicks overlap) forms in favour on the 1m bar close (iplFVG|1m), THEN within 60 s an order block (last opposite bar before a >=1-ATR displacement bar, within 3 bars) forms in favour on the 30s bar close (OB|30s); the entry second is the first print second at which the second array is knowable (closed bar) after the first started. Base: 70% of the planned lot at the signal (the usual 3-pt dip split base), the remaining 30% risk-sized (<=2 lots total, target re-based on the average). Mechanic: remainder as a RESTING LIMIT at the far edge of the second array's zone, placed at the entry second, resting until the hold dies (original stop / target second, opposite signal, session lots 0, flatten). Hold dies at the original stop level.

Mechanics tested (per contract L6M / HOLD): b_far +3.62/+3.75.

Controls on the best mechanic (b_far|F0.7): random-level placebo rank 5/101 (placebo mean +3.16); shuffled-day pair (+3/+7/+11 d) +1.04, +2.75, +0.93; delay 1 s +3.62, 3 s +3.55 (the array becomes knowable and the order is placed that many seconds later); leave-one-out: A alone +1.60, B alone +2.86, combination +3.62 (excess vs A +2.02, vs B +0.76, so the second array adds over the first and the first adds over the second).

Per session (L6M per contract): {'asia': 3.99, 'london': 4.92, 'nyam': 2.04, 'nypm': 3.63, 'pre': 5.4}. Fill: 57% of signals fire (23.2/wk of 40.4); lots at the fill median 1.12, max 2.00 (capacity at book depth was not measured: it needs L2 depth at the fill; the position is at most 2 lots per signal).

Walk-forward chain (book level: monthly re-selection among the book's 50 PRE+X'-selected cell x variants on closed trades only, >=13 weeks history): OOS L6M +3.99, HOLD +3.98 per contract; last re-fit 202602 picked ('0380818a97f6', 'c2_far|F0.7') (trailing +4.18); 32 monthly re-fits.

### PB: AND(FVG~30s+CFA:val~sw15)  [POOL]

**Rule.** a fair-value gap (3-bar gap >= 1 pt) forms in favour on the 30s bar close (FVG|30s) AND CFA:val on the sw15 bar close (CFA:val|sw15) simultaneously active. Base: 70% of the planned lot at the signal (the usual 3-pt dip split base), the remaining 30% risk-sized (<=2 lots total, target re-based on the average). Mechanic: once the dip >= 3 pts has started, remainder as a resting limit at the mean / CE of the second array's zone. Hold dies at the original stop level.

Mechanics tested (per contract L6M / HOLD): c2_mid +3.05/+3.38.

Controls on the best mechanic (c2_mid|F0.7): random-level placebo rank 1/101 (placebo mean +2.46); shuffled-day pair (+3/+7/+11 d) +0.82, +2.36, +1.31; delay 1 s +1.60, 3 s +1.60 (the array becomes knowable and the order is placed that many seconds later); leave-one-out: A alone +1.98, B alone +0.01, combination +3.05 (excess vs A +1.08, vs B +3.05, so the second array adds over the first and the first adds over the second).

Per session (L6M per contract): {'asia': 3.67, 'london': 5.22, 'nyam': 1.27, 'nypm': 2.73, 'pre': 0.36}. Fill: 53% of signals fire (16.5/wk of 30.9); lots at the fill median 1.11, max 2.00 (capacity at book depth was not measured: it needs L2 depth at the fill; the position is at most 2 lots per signal).

Walk-forward chain (book level: monthly re-selection among the book's 50 PRE+X'-selected cell x variants on closed trades only, >=13 weeks history): OOS L6M +2.49, HOLD +2.71 per contract; last re-fit 202602 picked ('338b733b6ec8', 'c2_mid|F0.7') (trailing +4.17); 32 monthly re-fits.

## GREEDY DN: 10 looked cells, tiers {'DEAD': np.int64(10)}; top by all-signal L6M gain

| spec                                                        | var         | tier   |   add_all_L6M |   add_HOLD |   best_member_L6M |   plac_p |
|:------------------------------------------------------------|:------------|:-------|--------------:|-----------:|------------------:|---------:|
| AND(FVG|30m+ote705|2m)                                      | c2_mid|F0.0 | DEAD   |        -2.873 |     28.062 |            -3.463 |    0.174 |
| AND(FVG|30m+ote705|2m+C2:ha|30s|HA_three+iFVG|3m+iplFVG|1h) | c2_mid|F0.0 | DEAD   |        -3.099 |     28.104 |            -2.37  |    0.055 |
| AND(FVG|30m+ote705|2m+C2:ha|30s|HA_three)                   | c2_mid|F0.0 | DEAD   |        -3.324 |     26.897 |            -3.463 |    0.199 |
| AND(FVG|30m+ote705|2m+C2:ha|30s|HA_three+iFVG|3m)           | c2_mid|F0.0 | DEAD   |        -3.426 |     27.363 |            -2.37  |    0.204 |
| AND(ote705|2m+C2:ha|30s|HA_three+iFVG|3m)                   | c2_mid|F0.0 | DEAD   |        -3.87  |     27.308 |            -2.37  |    0.667 |

## GREEDY SM: 17 looked cells, tiers {'DEAD': np.int64(12), 'BEST-AVAILABLE': np.int64(3), 'CANDIDATE': np.int64(2)}; top by all-signal L6M gain

| spec                             | var         | tier           |   add_all_L6M |   add_HOLD |   best_member_L6M |   plac_p |
|:---------------------------------|:------------|:---------------|--------------:|-----------:|------------------:|---------:|
| AND(CFA:vwap|avwap+CFA:vwap|day) | b_mid|F0.7  | CANDIDATE      |         3.283 |      8.951 |             2.723 |    0.033 |
| AND(CFA:vwap|avwap+CFA:vwap|day) | c2_mid|F0.7 | BEST-AVAILABLE |         2.943 |      8.478 |             2.798 |    0.098 |
| AND(CFA:b1|avwap+CFA:vwap|avwap) | c2_mid|F0.7 | BEST-AVAILABLE |         2.65  |     10.79  |             2.798 |    0.361 |
| AND(pd50|15s+iplFVG|15s)         | a|F0.7      | CANDIDATE      |         2.595 |      4.227 |             2.534 |    0.025 |
| AND(CFA:b1|avwap+CFA:vwap|avwap) | b_mid|F0.7  | BEST-AVAILABLE |         2.239 |      9.468 |             2.723 |    0.295 |

## FOUR DN: 30 looked cells, tiers {'BEST-AVAILABLE': np.int64(30)}; top by all-signal L6M gain

| spec                                            | var          | tier           |   add_all_L6M |   add_HOLD |   best_member_L6M |   plac_p |
|:------------------------------------------------|:-------------|:---------------|--------------:|-----------:|------------------:|---------:|
| AND(CFA:b1|avwap+MOM:RSI2<10|1m+FLOW:thick_q33) | c2_mid|F0.7  | BEST-AVAILABLE |         2.526 |     12.23  |             3.168 |    0.033 |
| AND(CFA:b1|avwap+MOM:RSI2<10|1m+FLOW:thick_q33) | c2_near|F0.7 | BEST-AVAILABLE |         2.526 |     12.23  |             3.168 |    0.033 |
| AND(CFA:b1|avwap+MOM:RSI2<10|1m+FLOW:thick_q33) | c2_far|F0.7  | BEST-AVAILABLE |         2.526 |     12.23  |             3.168 |    0.033 |
| AND(CFA:b1|avwap+MOM:RSI2<10|1m+FLOW:thick_q33) | b_far|F0.7   | BEST-AVAILABLE |         2.505 |     11.893 |             3.108 |    0.016 |
| AND(CFA:b1|avwap+MOM:RSI2<10|1m+FLOW:thick_q33) | b_mid|F0.7   | BEST-AVAILABLE |         2.505 |     11.893 |             3.108 |    0.016 |

## FOUR SM: 30 looked cells, tiers {'CANDIDATE': np.int64(16), 'BEST-AVAILABLE': np.int64(14)}; top by all-signal L6M gain

| spec                                        | var          | tier           |   add_all_L6M |   add_HOLD |   best_member_L6M |   plac_p |
|:--------------------------------------------|:-------------|:---------------|--------------:|-----------:|------------------:|---------:|
| AND(OB|30s+MOM:RSI2<10|1m+FLOW:thick_q33)   | c2_near|F0.7 | CANDIDATE      |         3.719 |     11.249 |             2.481 |    0.016 |
| AND(OB|30s+MOM:RSI2<10|1m+FLOW:imb5_ge_q20) | c2_near|F0.7 | CANDIDATE      |         3.61  |     11.406 |             2.481 |    0.016 |
| AND(OB|30s+MOM:RSI2<10|1m+FLOW:imb5_ge_q20) | c2_mid|F0.7  | CANDIDATE      |         3.469 |     11.476 |             3.305 |    0.016 |
| AND(OB|30s+MOM:RSI2<10|1m+FLOW:imb5_ge_q20) | c2_far|F0.7  | BEST-AVAILABLE |         3.201 |     10.902 |             3.512 |    0.016 |
| AND(OB|30s+MOM:RSI2<10|1m+FLOW:imb5_ge_q20) | b_near|F0.7  | CANDIDATE      |         3.126 |     10.286 |             0.978 |    0.016 |

## LEARNED DN (LightGBM depth<=4, monotone, monthly re-fit, last re-fit 202602)

OOS all-signal gain per contract: PRE +2.70 [+2.15,+3.25] fire 83%, X +2.61 [+1.70,+3.52] fire 85%, HOLD +3.55 [+2.53,+4.58] fire 86%, L6M +3.63 [+2.53,+4.73] fire 85%, L3M +3.59 [+2.38,+4.80] fire 85%. Dip-only structure control (no confirmation features): PRE +3.05, X +1.94, HOLD +3.83, L6M +3.86, L3M +3.95. Shuffled-feature placebo L6M mean -1.08, max +0.28, real rank 1/9. Retained gain of the 6 extracted rules: {'L6M': 4.100040039377239, 'HOLD': 4.409099174871836, 'PRE': 4.194581579727928, 'X': 3.8993084743412596}.

Top rules at the last re-fit (in words): +0.40 pts (4833 rows) dip_pts<=13.6 AND dip_pts>-8.9 AND dip_pts>1.1 AND dip_pts>6.1 || +0.40 pts (4597 rows) dip_pts<=16.4 AND dip_pts>-8.9 AND dip_pts>2.9 AND dip_pts>7.4 || +0.21 pts (5622 rows) dip_pts<=16.4 AND dip_pts<=7.4 AND dip_pts>-8.9 AND dip_pts>2.9 || +0.41 pts (2888 rows) dip_pts<=16.4 AND dip_pts>-11.4 AND dip_pts>1.1 AND dip_pts>6.1 || +0.42 pts (2637 rows) dip_pts<=15.1 AND dip_pts>-8.9 AND dip_pts>2.4 AND dip_pts>6.1 || +0.71 pts (1455 rows) dip_pts<=26.6 AND dip_pts>-8.9 AND dip_pts>13.6 AND sess_pre<=0.0

Last re-fit importance (gain): dip_pts 38403165, sec_since 2300832, MOM:RSI7<30|1m|seen 913980, log_sec 754453, pd50|5m|now 718941, ote705|2m|seen 599173, MOM:RSI7<30|15s|now 580013, MOM:RSI2<10|1m|now 462448, MOM:Stoch14x|1m|seen 425320, pd50|5m|seen 375181

## LEARNED HM (LightGBM depth<=4, monotone, monthly re-fit, last re-fit 202602)

OOS all-signal gain per contract: PRE +3.15 [+2.63,+3.67] fire 86%, X +1.89 [+0.68,+3.10] fire 81%, HOLD +2.30 [+1.82,+2.78] fire 87%, L6M +2.23 [+1.79,+2.68] fire 87%, L3M +2.58 [+2.04,+3.11] fire 88%. Dip-only structure control (no confirmation features): PRE +2.87, X +2.32, HOLD +2.40, L6M +2.32, L3M +2.72. Shuffled-feature placebo L6M mean -0.82, max -0.23, real rank 1/9. Retained gain of the 6 extracted rules: {'L6M': 5.160872298235074, 'HOLD': 5.110046800973186, 'PRE': 5.584536208906512, 'X': 5.6209683477512575}.

Top rules at the last re-fit (in words): +1.03 pts (1584 rows) dip_pts<=34.9 AND dip_pts>-5.6 AND dip_pts>11.4 AND dip_pts>17.6 || +0.95 pts (1581 rows) dip_pts<=33.1 AND dip_pts>-5.1 AND dip_pts>11.4 AND dip_pts>17.1 || +0.73 pts (1957 rows) dip_pts<=21.4 AND dip_pts<=34.4 AND dip_pts>-6.9 AND dip_pts>11.4 || +0.37 pts (3506 rows) dip_pts<=12.1 AND dip_pts>-6.6 AND dip_pts>1.4 AND dip_pts>4.9 || +1.18 pts (1016 rows) dip_pts<=34.4 AND dip_pts>-6.9 AND dip_pts>11.4 AND dip_pts>21.4 || +1.11 pts (1080 rows) dip_pts<=29.1 AND dip_pts>-6.6 AND dip_pts>12.1 AND dip_pts>18.6

Last re-fit importance (gain): dip_pts 44509598, ote79|15s|now 2187755, sec_since 1544100, fib79|30s|now 797074, log_sec 699399, ote79|15s|seen 655731, MOM:RSI7<30|15s|now 466281, ote62|2m|now 325908, MOM:RSI2<10|15s|now 319892, MOM:RSI7<30|1m|seen 260799

## LEARNED KB (LightGBM depth<=4, monotone, monthly re-fit, last re-fit 202602)

OOS all-signal gain per contract: PRE +3.38 [+2.86,+3.90] fire 86%, X +1.95 [+1.47,+2.42] fire 83%, HOLD +3.28 [+2.62,+3.94] fire 87%, L6M +3.34 [+2.63,+4.04] fire 87%, L3M +3.87 [+2.93,+4.81] fire 88%. Dip-only structure control (no confirmation features): PRE +3.03, X +2.20, HOLD +3.21, L6M +3.27, L3M +3.76. Shuffled-feature placebo L6M mean -0.45, max -0.22, real rank 1/9. Retained gain of the 6 extracted rules: {'L6M': 4.1034440337859275, 'HOLD': 4.035440074904693, 'PRE': 4.105207494371091, 'X': 2.880858476512783}.

Top rules at the last re-fit (in words): +1.08 pts (1536 rows) dip_pts<=28.9 AND dip_pts>-10.1 AND dip_pts>13.1 AND dip_pts>18.1 || +0.31 pts (5177 rows) dip_pts<=13.1 AND dip_pts>-9.4 AND dip_pts>1.1 AND dip_pts>4.9 || +0.97 pts (1533 rows) dip_pts<=28.9 AND dip_pts>-9.1 AND dip_pts>13.9 AND dip_pts>18.1 || +0.23 pts (6352 rows) dip_pts<=13.9 AND dip_pts<=9.6 AND dip_pts>-9.1 AND dip_pts>2.9 || +0.92 pts (1559 rows) dip_pts<=29.6 AND dip_pts>-9.4 AND dip_pts>13.1 AND dip_pts>18.1 || +0.24 pts (5566 rows) dip_pts<=13.1 AND dip_pts<=8.1 AND dip_pts>-10.1 AND dip_pts>2.9

Last re-fit importance (gain): dip_pts 57710933, fib62|15s|now 2465734, sec_since 1393428, log_sec 778579, MOM:RSI2<10|1m|seen 730960, MOM:RSI7<30|15s|now 654308, MOM:RSI7<30|1m|seen 491333, MOM:RSI2<10|15s|now 461769, MOM:RSI2<10|1m|now 395169, fib50|2m|now 365564

## LEARNED PE (LightGBM depth<=4, monotone, monthly re-fit, last re-fit 202602)

OOS all-signal gain per contract: PRE +3.40 [+2.80,+4.01] fire 86%, X +3.23 [+2.16,+4.30] fire 84%, HOLD +3.18 [+2.46,+3.91] fire 86%, L6M +3.11 [+2.34,+3.88] fire 87%, L3M +3.03 [+2.08,+3.98] fire 87%. Dip-only structure control (no confirmation features): PRE +3.31, X +2.43, HOLD +2.90, L6M +2.83, L3M +3.16. Shuffled-feature placebo L6M mean -0.39, max +0.58, real rank 1/9. Retained gain of the 6 extracted rules: {'L6M': 6.522613908388321, 'HOLD': 6.509019111143839, 'PRE': 6.43311728251549, 'X': 5.61659487229288}.

Top rules at the last re-fit (in words): +0.73 pts (2916 rows) dip_pts<=24.9 AND dip_pts<=32.9 AND dip_pts>-12.4 AND dip_pts>12.4 || +0.69 pts (2907 rows) dip_pts<=24.9 AND dip_pts<=30.9 AND dip_pts>-6.1 AND dip_pts>12.4 || +0.35 pts (5418 rows) dip_pts<=12.4 AND dip_pts>-0.0 AND dip_pts>-12.4 AND dip_pts>4.4 || +0.81 pts (2305 rows) MOM:RSI2<10|1m has fired since the signal AND ote62|45s is active now AND sess_nyam<=0.0 [absent MOM:RSI7<30|5m|now] || +0.56 pts (3229 rows) dip_pts<=21.6 AND dip_pts<=30.9 AND dip_pts>-9.6 AND dip_pts>10.4 || +1.15 pts (1470 rows) FLOW:thin_q67 has fired since the signal AND log_sec>5.3 AND ote62|45s is active now AND sess_asia<=0.0

Last re-fit importance (gain): dip_pts 53252771, ote62|45s|now 8312726, sec_since 2564621, MOM:RSI7<30|1m|now 1561032, ote62|45s|seen 1263434, log_sec 1177530, MOM:RSI7<30|1m|seen 697931, MOM:Stoch14x|1m|seen 673586, MOM:RSI7<30|15s|now 627623, MOM:RSI2<10|1m|seen 505476

## LEARNED SM (LightGBM depth<=4, monotone, monthly re-fit, last re-fit 202602)

OOS all-signal gain per contract: PRE +3.24 [+1.98,+4.50] fire 86%, X +3.45 [+1.87,+5.02] fire 82%, HOLD +3.41 [+1.95,+4.88] fire 85%, L6M +3.86 [+2.24,+5.49] fire 86%, L3M +4.99 [+2.78,+7.19] fire 86%. Dip-only structure control (no confirmation features): PRE +3.28, X +2.91, HOLD +3.06, L6M +3.44, L3M +4.24. Shuffled-feature placebo L6M mean -1.80, max -0.53, real rank 1/9. Retained gain of the 6 extracted rules: {'L6M': 7.589584938297654, 'HOLD': 7.314137108292488, 'PRE': 8.529781975680457, 'X': 7.730783912967775}.

Top rules at the last re-fit (in words): +0.75 pts (1089 rows) MOM:RSI2<10|1m has fired since the signal AND pd50|15s is active now AND sess_asia<=0.0 [absent pd50|10m|seen] || +1.08 pts (688 rows) dip_pts>-8.9 AND dip_pts>10.9 AND dip_pts>29.4 || +0.75 pts (904 rows) dip_pts<=20.6 AND dip_pts<=29.4 AND dip_pts>-8.9 AND dip_pts>10.9 || +0.70 pts (878 rows) dip_pts<=27.6 AND dip_pts>-8.9 AND dip_pts>12.1 AND sec_since>45.0 || +0.65 pts (928 rows) MOM:RSI7<30|15s has fired since the signal AND pd50|15s is active now [absent CTX:sess_nyam|now ; MOM:RSI2<10|5m|now] || +1.00 pts (595 rows) MOM:RSI2<10|1m has fired since the signal AND pd50|15s is active now AND sess_asia<=0.0 [absent MOM:RSI7<30|1m|now]

Last re-fit importance (gain): dip_pts 21056376, pd50|15s|now 2401344, sec_since 696650, log_sec 543743, pd50|10m|seen 321500, MOM:RSI2<10|1m|seen 229104, fib50|15s|now 218803, CTX:sess_nyam|now 217243, MOM:RSI7<30|15s|seen 195976, CFA:vah|sess|now 189621

## LEARNED ST (LightGBM depth<=4, monotone, monthly re-fit, last re-fit 202602)

OOS all-signal gain per contract: PRE +3.13 [+2.63,+3.62] fire 86%, X +1.81 [+1.31,+2.31] fire 83%, HOLD +2.77 [+2.07,+3.46] fire 87%, L6M +2.87 [+2.12,+3.62] fire 87%, L3M +2.96 [+1.99,+3.93] fire 86%. Dip-only structure control (no confirmation features): PRE +3.47, X +1.82, HOLD +3.32, L6M +3.44, L3M +3.58. Shuffled-feature placebo L6M mean -0.83, max -0.48, real rank 1/9. Retained gain of the 6 extracted rules: {'L6M': 4.945606251888412, 'HOLD': 5.048702077859618, 'PRE': 4.995178397189717, 'X': 3.877559305992169}.

Top rules at the last re-fit (in words): +0.41 pts (4352 rows) dip_pts<=13.9 AND dip_pts>-9.9 AND dip_pts>2.4 AND dip_pts>5.6 || +0.28 pts (6062 rows) dip_pts<=12.4 AND dip_pts>-1.6 AND dip_pts>-13.4 AND dip_pts>3.6 || +0.43 pts (3806 rows) dip_pts<=12.4 AND dip_pts>-10.1 AND dip_pts>0.9 AND dip_pts>5.6 || +0.34 pts (4808 rows) dip_pts<=15.6 AND dip_pts>-8.9 AND dip_pts>2.4 AND dip_pts>5.6 || +0.97 pts (1650 rows) dip_pts<=33.1 AND dip_pts>-9.6 AND dip_pts>12.4 AND dip_pts>18.9 || +0.71 pts (2207 rows) dip_pts<=21.4 AND dip_pts<=30.6 AND dip_pts>-9.9 AND dip_pts>12.4

Last re-fit importance (gain): dip_pts 61873661, fib79|15s|now 1796166, sec_since 995768, pd50|5m|now 809125, MOM:RSI7<30|1m|now 728492, log_sec 572061, MOM:RSI2<10|15s|now 325852, FVG|5m|now 304748, MOM:RSI7<30|15s|now 293280, fib50|5m|now 291640

