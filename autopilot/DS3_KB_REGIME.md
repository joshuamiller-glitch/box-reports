# DS3_KB_REGIME - follow-up section 4, KB regime tools (agent KBR, 2026-10-31)

Research only. Prereg autopilot/KBR_prereg.md sha256 9c08d2f92c88bb79b4b68619bbd1edab52889f9a4e71a4f46a24e9ce4d8ce90b (DECISIONS.md before any scored cell); selection file out/kbregime/selection_PRE_X.json sha256 704300a3...1431 (PRE+X' only), then ONE recent look on the named cells plus the selected ones. Code l2vast/ds3/code/kbregime/ (kbr_lib, stage1-6, wf, kbr_stack), outputs l2vast/ds3/out/kbregime/. Masks capped 20260206 (Y26 = 5 weeks, sign only); UNTOUCHED never read. UF_TRIALS side followup_kbregime (n_cells 540, effective 49); DEAD_CELLS +49 rows (KBR); RECENT_WINS out/recent_wins/followup_kbregime.csv.

Unit: KB signals in the four live sessions (Asia / London / NY-AM / NY-PM; pre-market and close excluded), 42.7 signals/week (L6M). Base B2 = the 70/30@3 split, basis N (headline); B1 = market at the signal, basis N (second table). Windows own masks: X' 20230401-20240131, PRE 20240201-20250630, HOLD 20250701-20260206, L6M 20250801-20260206, L3M 20251106-20260206. "rate" = risk-matched points per planned lot (total lots unchanged; MDE = 2.8 x week-clustered SE). Stack = KB book only through the exact per-book lock engine (stack2/s2_lib -> sp_lib rows + sl_lib locks), research lots KB 5.2; live $ at KB 2 lots = research $ x 2/5.2 (locks are per book, so a KB-only rule moves only the KB line). Two lock conventions, as ordered: PLAN-R = the base governors (day/week/entry-test locks in planned-lot R); SIZED-R = the same locks multiplied by the book's largest multiplier of that day (week lock: of that week) (kbr_stack.py patches sl_lib.run_book; identity test: with all multipliers 1 it reproduces the base to the dollar).

## PAGE 1 - VERDICT
1. **No PASS.** One LEAD, three CANDIDATE-RECENT, the rest DEAD. Program White RC p 0.076 over the 34 distinct cells (cumulative Sidak 1.0), PBO 0.09; nothing survives Romano-Wolf at the program level.
2. **The only KB regime tool that is >= 0 on the lock-engine stack in every window is the ER >= 0.2 sizer (x1.5 at/above 0.20, x0.5 below) with SIZED-lot-R locks: LEAD (inside MDE; premise partly post-hoc).** 70/30 split, research lots, stack delta $/wk: X' +2.3k / PRE +3.4k / HOLD +6.5k / L6M +8.1k (MDE 12.2k) / L3M +10.9k / 2026 +11.6k; at KB 2 lots (x0.385): +0.9k / +1.3k / +2.5k / **+3.1k per week L6M**. Placebo (200 shuffled-flag draws, same multiplier mix): stack rank 1.00 L6M and HOLD, 0.94 X', 0.68 PRE; trade rate rank 0.97/0.98 L6M/HOLD; rate +1.45 pts/lot L6M (MDE 2.1), +1.42 HOLD, +0.28 PRE, +0.95 X'. Neighbours (thr 0.10/0.15/0.25/0.30): L6M +6.3k/+4.3k/+4.0k/+4.8k, PRE +4.4k/+1.7k/+2.6k/-1.0k. Mean multiplier 1.07, so this is not extra leverage (risk-matched sized-R stack: PRE +2.4k, HOLD +5.4k, L6M +6.7k, X' +2.1k). With the PLAN-R (base-lot) governors the same sizer is weaker: X' +0.8k, PRE -1.6k, HOLD +2.8k, L6M +3.1k: **the answer depends on the governor definition** (open question in MORNING.md).
3. **The TG-1 chop filter (5-min ER(20) >= 0.3) is a rate result, not a stack result.** Gate: keeps 35% of KB signals (15.0 of 42.7 per week), rate +5.8 pts/lot L6M (MDE 5.9), HOLD +5.9, L3M +6.4, 2026 +6.4, but PRE +0.5, X' +1.4; kept signals earn +7.5 per contract vs +1.7 for all (L6M). Stack: -0.3k L6M, -0.5k HOLD, **-7.4k PRE**, -0.7k X' (the skipped 65% carry the dollars). As the x0.5/x1.5 sizer: PLAN-R -0.5k/+0.2k/-0.1k/+0.3k (X'/PRE/HOLD/L6M), SIZED-R -0.2k/-1.0k/+3.5k/+4.8k: CANDIDATE-RECENT (fails PRE and X'). Threshold 0.2 beats 0.3 on PRE+X' in the same family (that is why 0.2 is the lead and 0.3 is not).
4. **Book-lean skip - the direction the directive wrote (AGAINST) is the wrong sign; the direction that works in the rate (OUR way) is not worth it on the stack.** Definition below. Skip when the book has leaned AGAINST the signal >= 3 / 5 / 15 min: rate PRE -1.0 / -0.9 / +0.1, X' -1.4 / +0.2 / +0.2, L6M +0.6 / +0.1 / +0.15; stack -4.1k / -2.8k / +0.3k L6M, -4.4k / -3.0k / +0.6k PRE: DEAD. Skip when it has leaned OUR way >= 3 min (N1 e a6, the one that was positive): rate X' +1.65, PRE +0.51, L3M +0.64, L6M +0.90, HOLD +1.15 (MDE 1.8; shuffled placebo rank 0.84/0.91/0.84 L6M/HOLD/PRE, 1.00 X'), 20% of signals (8.4 per week); stack -1.7k L6M (live -0.7k), -1.7k HOLD, -2.4k PRE, +0.9k X' (stack placebo rank 0.68): the skipped trades are profitable in dollars (their loss in volume cancels the rate gain): DEAD on the stack, rate-only LEAD (post-hoc: this cell was N1's best-of-12 KB cell). >= 5 and >= 15 min: rate ~0 and negative recent (15 min: -0.4, placebo rank 0.02): the effect lives only at 3 minutes and fades by 5 (knife edge); a 60-s-stale feature is negative in L6M (-0.8), so it is a fresh-state signal.
5. **Together (ER + lean) is worse than ER alone on the stack.** ER >= 0.2 sizer + skip OUR-way >= 3: rate L6M +2.2 (ER alone +1.45), PRE +0.5, X' +2.6; but stack PLAN-R -2.5k L6M (ER alone +3.1k), SIZED-R +2.7k (ER alone +8.1k); the lean skip subtracts about 5k/wk of KB volume from the lead. ER >= 0.3 gate + skip: rate L6M +5.4, stack -0.7k, PRE -8.9k.
6. **Walk-forward chain (monthly re-fit over the 49 cells + none, anchored and rolling-12, 2024-04 to 2026-02):** anchored chain rate PRE(2024-04..) +0.07, HOLD +5.5, L6M +5.4 (rank vs 200 random-cell chains 1.00 HOLD, 0.995 L6M, 0.40 PRE); it is the ER >= 0.3 gate in disguise (picks ER0.3 gate + skip OUR-way >= 3 every month since 2025-07). Last re-fit (data through 2026-01-31, applied to 2026-02-01..06; anchored): **ER >= 0.3 gate + skip lean OUR-way >= 3 min**; rolling-12 last re-fit: ER >= 0.3 gate + skip AGAINST >= 5. Rolling-12 chain is a random chain (rank 0.5). Chain stack (unscaled, 70/30, research lots): X' 0 (not in range), PRE -9.6k, HOLD -0.5k, L6M -0.7k, L3M +8.3k, 2026 -0.2k (rolling -8.8k/-0.8k/-1.0k): no.
7. **Per session: nothing is stable enough for a session carve-out.** ER >= 0.2 rate L6M by session: Asia +4.8 (PRE -0.1, X' -0.5), London +0.75 (PRE +3.1), NY-AM +0.1 (PRE +0.6, X' +1.6), NY-PM +4.4 (PRE -0.8, X' +4.3): recent gains are Asia and NY-PM, PRE/X' disagree in each. The lean OUR-way skip lives in London (L6M +3.2, HOLD +2.9, PRE 0.0, X' +1.0; London-only stack L6M +3.0k, PRE -0.5k) and is negative in NY-AM (L6M -0.2, stack -1.5k) = post-hoc session story, SHADOW at most.
8. **Sunday relevance:** KB has the x1.5/x0.5 ER sizer at 0.30 in the coded stack; for KB the numbers prefer a 0.20 threshold (PRE+X' choose it; sized-R stack >= 0 in all windows, vs 0.30: X' -0.2k, PRE -1.0k). That is one KB-only parameter, SHADOW until the governor question is answered; the lean skip and the chop gate should stay OFF.

## D6 LINES (group / property / value; K6 = KB, live 2 lots (Asia/London/NY-AM/NY-PM); research lots 5.2)
| status | D6 group / property / value | evidence | $/wk L6M research / live K6 2 lots |
|---|---|---|---|
| SHADOW (LEAD) | K6 / ER sizer threshold / 0.20 on 5-min Kaufman ER(20) at the signal, x1.5 at/above, x0.5 below (KB 2 lots -> 3 or 1), day/week/entry locks x the day's largest multiplier | stack >= 0 in X'/PRE/HOLD/L6M/L3M/2026, placebo 1.00/1.00, inside MDE (12.2k) | +8.1k / +3.1k |
| SHADOW if governors are planned-lot R | same, base-lot locks | X' +0.8k, PRE -1.6k, HOLD +2.8k, L6M +3.1k | +3.1k / +1.2k |
| OFF | K6 / ER gate (skip below 0.20) | rate +2.7 L6M, stack PRE -3.0k | +2.6k / +1.0k (PRE -1.2k live) |
| OFF | K6 / TG-1 chop gate (ER >= 0.3 skip) | rate +5.8, stack -0.3k L6M, -7.4k PRE | -0.3k / -0.1k |
| OFF | K6 / 0.30 sizer | PRE/X' <= 0 | PLAN-R +0.3k, SIZED-R +4.8k / +0.1k, +1.9k |
| OFF | K6 / book-lean skip (imb10 run >= 3/5/15 min, AGAINST) | PRE rate -1.0, stack -4.1k | -4.1k / -1.6k |
| OFF (rate LEAD only) | K6 / book-lean skip, OUR way >= 3 min | rate +0.9 L6M, stack -1.7k | -1.7k / -0.7k |
| OFF | K6 / ER + lean together | below ER alone | -2.5k PLAN-R / -1.0k |


## 1. DEFINITIONS (exact)
* ER: Kaufman efficiency ratio over 20 five-minute bars, |close[t]-close[t-20]| / sum |close[i]-close[i-1]|, last completed 5-minute bar at the signal (trendgate store chart_5m 5m.er20; same value D6 computes for its ER sizer). Gate = skip below the threshold; sizer = x1.5 at/above, x0.5 below. TG-1 chop filter = threshold 0.30 (5-min; 15-min and 1-min ER lift 0).
* Book lean (imb10): from the 1-second book tape, imb10 = top-10-level imbalance, signed by the signal side so that **positive = the book leans OUR way (with the trade), negative = AGAINST**. For each of the last 30 one-minute blocks before the signal second (block j = [t-60(j+1), t-60j)), mean imb10 x side (block needs >= 5 samples). run_signed = number of consecutive blocks, counted back from the signal, that share the sign of the newest block (signed). Thresholds R = 3 / 5 / 15 minutes. Directions tested: **AGAINST skip = run_signed <= -R (the directive's wording); OUR-WAY skip = run_signed >= +R (the N1 cycle e "a6" cell that was positive)**; sizer variant AGAINST x0.5. (N1 e: "leaned OUR way >= 3 min -> skip" was the positive KB cell; its mirror, skip when AGAINST, is the one in this brief.) The feature file is out/newideas/e_feat.parquet; 60-s-stale control e_feat_off60.
* Units: rate = risk-matched pts per planned lot (equal total lots, scalar from PRE+X' only); per contract of final lots = sum(m y)/sum(m lots) (gates: only kept trades); stack = KB book lock engine $/wk at research lots (KB 5.2), live = x 2/5.2.

## 2. MAIN TABLE - 70/30 split, basis N (B2), KB live sessions. Tables are STRUCTURE for the unscaled $ whenever lots change (every gate and sizer); the rate column is risk-matched, the information measure.
Lock-engine columns: PLAN-R (base governors) X'/PRE/HOLD/L6M/L3M and MDE of L6M; SIZED-R for sizers. Per-contract L6M (final lots): ER0.2 gate 4.45 vs 1.74 all, ER0.2 sizer 3.18, ER0.3 gate 7.52, ER0.3 sizer 4.13, lean OUR-way 3: 2.64, AGAINST 3: 2.33, ER0.2 gate + OUR-way 3: 5.02 (PRE 3.47 vs 3.01 all; X' 2.90 vs -0.58). Skipped signals earn -1.9 per planned lot (ER0.2 gate), -1.4 (ER0.3 gate), -1.9 (OUR-way 3) in L6M; AGAINST-3 skips earn -0.06.
Tiers: ER0.2 sizer SIZED-R = LEAD; ER0.2 gate, ER0.3 gate, ER0.3 sizer = CANDIDATE-RECENT (>= 0 in L6M and HOLD, PRE/X' mixed on the stack); lean OUR-way 3 = rate LEAD, stack DEAD; everything else DEAD. Post-hoc labels: the thresholds 0.2 / 0.3 and the lean OUR-way >= 3 cell were named from earlier looks at the recent windows (C2 note, TG-1, N1 e); the prereg here fixed them before scoring, the PRE+X' selection chose 0.2 over 0.3 and R=3 over 5/15, but they are not out-of-sample for the recent windows.


| rule | kept sig/wk (of 42.7) | skip share | rate X' | PRE | L3M | L6M | HOLD | Y26 | MDE L6M | placebo rank L6M/HOLD/PRE | quarters + | stack plan-R $/wk research X'/PRE/HOLD/L6M/L3M | MDE L6M | stack sized-R (sizers) | live KB-2 $/wk L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ER20(5m)>=0.2 gate | 24.5 | 0.43 | 1.72 | 0.53 | 2.18 | 2.71 | 2.68 | 1.76 | 4.0 | 0.97/0.98/0.67 | 10/12 | +0.5k / -3.0k / +2.3k / +2.6k / +8.0k | +13.0k | same (no sizing) | +1.0k |
| ER>=0.2 x1.5 / <0.2 x0.5 | 42.7 | 0.00 | 0.95 | 0.28 | 1.16 | 1.45 | 1.42 | 0.96 | 2.1 | 0.97/0.98/0.67 | 10/12 | +0.8k / -1.6k / +2.8k / +3.1k / +8.2k | +9.4k | +2.3k / +3.4k / +6.5k / +8.1k / +10.9k | +1.2k (+3.1k sized-R) |
| ER>=0.3 gate (TG-1 chop filter) | 15.0 | 0.65 | 1.41 | 0.54 | 6.42 | 5.81 | 5.93 | 6.37 | 5.9 | 0.99/0.99/0.60 | 8/12 | -0.7k / -7.4k / -0.5k / -0.3k / +8.1k | +11.7k | same (no sizing) | -0.1k |
| ER>=0.3 x1.5 / <0.3 x0.5 (Sunday sizer) | 42.7 | 0.00 | 0.64 | 0.23 | 2.58 | 2.40 | 2.45 | 2.47 | 2.4 | 0.99/0.99/0.60 | 8/12 | -0.5k / +0.2k / -0.1k / +0.3k / +4.7k | +11.1k | -0.2k / -1.0k / +3.5k / +4.8k / +7.3k | +0.1k (+1.9k sized-R) |
| lean OUR way >=3 min: skip | 34.3 | 0.20 | 1.65 | 0.51 | 0.64 | 0.90 | 1.15 | -0.43 | 1.8 | 0.84/0.91/0.84 | 9/12 | +0.9k / -2.4k / -1.7k / -1.7k / +0.2k | +7.9k | same (no sizing) | -0.7k |
| lean OUR way >=5 min: skip | 38.4 | 0.10 | 0.90 | 0.30 | -0.30 | -0.10 | 0.01 | -1.08 | 1.5 | 0.43/0.52/0.78 | 8/12 | +0.2k / -1.4k / -1.3k / -0.5k / +1.4k | +6.9k | same (no sizing) | -0.2k |
| lean OUR way >=15 min: skip | 42.1 | 0.01 | 0.13 | 0.19 | -0.55 | -0.43 | -0.44 | -0.85 | 0.5 | 0.02/0.01/0.95 | 6/12 | -0.0k / +0.2k / -0.9k / -0.6k / -0.4k | +2.1k | same (no sizing) | -0.2k |
| lean AGAINST >=3 min: skip | 31.9 | 0.25 | -1.44 | -0.99 | 1.96 | 0.60 | 0.18 | 1.76 | 2.4 | 0.75/0.63/0.09 | 4/12 | -3.2k / -4.4k / -5.0k / -4.1k / -0.6k | +11.7k | same (no sizing) | -1.6k |
| lean AGAINST >=5 min: skip (directive) | 37.0 | 0.13 | 0.17 | -0.92 | 1.46 | 0.10 | -0.01 | 1.79 | 1.8 | 0.61/0.56/0.01 | 5/12 | -1.2k / -3.0k / -2.5k / -2.8k / +1.1k | +7.4k | same (no sizing) | -1.1k |
| lean AGAINST >=15 min: skip (directive) | 42.4 | 0.01 | 0.16 | 0.11 | 0.09 | 0.15 | 0.19 | -0.12 | 0.3 | 0.86/0.88/0.87 | 8/12 | +0.9k / +0.6k / +0.1k / +0.3k / +0.2k | +0.9k | same (no sizing) | +0.1k |
| ER>=0.2 gate + skip OUR-way>=3 | 19.8 | 0.54 | 3.45 | 0.46 | 3.65 | 3.27 | 3.36 | 2.32 | 4.9 | 0.97/0.97/0.57 | 10/12 | +1.4k / -5.4k / -1.3k / -1.6k / +6.6k | +14.3k | same (no sizing) | -0.6k |
| ER>=0.2 sizer + skip OUR-way>=3 | 34.3 | 0.20 | 2.64 | 0.49 | 2.24 | 2.17 | 2.33 | 1.08 | 3.0 | 0.97/0.98/0.68 | 11/12 | +2.9k / -5.3k / -1.9k / -2.5k / +6.5k | +10.8k | +4.3k / +1.2k / +2.0k / +2.7k / +10.3k | -1.0k (+1.0k sized-R) |
| ER>=0.3 gate + skip OUR-way>=3 | 12.1 | 0.72 | 3.80 | 0.49 | 5.45 | 5.37 | 5.51 | 2.66 | 8.1 | 0.98/0.98/0.55 | 9/12 | +0.9k / -8.9k / -0.5k / -0.7k / +8.3k | +12.6k | same (no sizing) | -0.3k |

## 3. SECOND TABLE - market at the signal, basis N (B1), same cells
(rows as above; the full B1 table is out/kbregime/stage2.csv, stack_s2lib.csv.) Headline B1 rows: ER0.2 gate rate X'/PRE/L6M/HOLD +1.79/+0.49/+2.89/+2.93, stack PLAN-R X'/PRE/HOLD/L6M +0.9k/-6.3k/+2.6k/+2.8k; ER0.2 sizer SIZED-R X'/PRE/HOLD/L6M/L3M +1.9k/+2.5k/+6.4k/+8.0k/+9.2k; ER0.3 gate rate L6M +5.74, stack -0.5k L6M, -8.9k PRE; OUR-way 3 rate +1.83/+0.54/+0.90/+1.13, stack +2.8k/-2.5k/+0.2k/+0.2k; AGAINST 3 rate -1.61 X', -0.99 PRE, stack -4.0k L6M. Same conclusions on both bases.

## 4. PER SESSION (B2; rate = pts per planned lot; stack = rule applied in that session only, KB lock engine research lots, $k/wk PLAN-R; sizers' SIZED-R in brackets)
| session (L6M signals / MDE of rate) | rule | rate X' | PRE | L3M | L6M | HOLD | Y26 | stack X'/PRE/HOLD/L6M |
|---|---|---|---|---|---|---|---|---|
| Asia (335, 7.2) | ER>=0.2 gate | -0.45 | -0.09 | +7.09 | +4.78 | +5.05 | +5.46 | -0.5/-0.2/+2.2/+1.9 |
| Asia | ER>=0.2 sizer | -0.23 | -0.05 | +3.88 | +2.63 | +2.74 | +2.98 | -0.7/-2.4/-1.5/-1.0 [-0.8/+3.2/+1.0/+2.5] |
| Asia | ER>=0.3 gate | -6.39 | +2.19 | +13.62 | +9.67 | +9.61 | +9.35 | -3.3/-1.4/-0.3/-1.1 |
| Asia | OUR-way >=3 skip | +0.83 | -0.43 | -0.29 | +0.63 | +0.73 | -0.70 | -0.3/-1.7/+0.2/+0.5 |
| Asia | AGAINST >=3 skip | -1.46 | -1.00 | +4.91 | +3.70 | +2.98 | +2.90 | -1.2/-1.8/+2.4/+2.6 |
| London (234, 7.5) | ER>=0.2 gate | +1.16 | +3.09 | -0.17 | +0.75 | +0.32 | -3.37 | +1.4/+0.4/-1.2/-0.7 |
| London | ER>=0.2 sizer | +0.71 | +1.78 | -0.09 | +0.43 | +0.18 | -1.95 | +0.6/+0.1/+1.6/+2.7 [-0.5/+1.6/-1.4/+0.1] |
| London | ER>=0.3 gate | +4.26 | -2.71 | +8.47 | +5.91 | +5.12 | +12.76 | +1.3/+0.7/-3.8/-2.6 |
| London | OUR-way >=3 skip | +0.96 | 0.00 | +5.20 | +3.24 | +2.86 | +3.17 | -0.6/-0.5/+2.6/+3.0 |
| London | AGAINST >=3 skip | -0.28 | +0.49 | -0.40 | -4.12 | -4.44 | -4.12 | -0.9/+0.6/-4.0/-3.3 |
| NY-AM (391, 7.8) | ER>=0.2 gate | +1.62 | +0.56 | -2.17 | +0.13 | +0.06 | -4.73 | +0.4/-0.7/-0.6/-0.4 |
| NY-AM | ER>=0.2 sizer | +0.87 | +0.28 | -1.13 | +0.07 | +0.03 | -2.55 | +0.4/+1.7/-1.1/-1.3 [+2.5/+3.9/-4.9/-4.4] |
| NY-AM | ER>=0.3 gate | +2.55 | +3.35 | -0.60 | +3.10 | +2.83 | -5.82 | -0.8/-0.7/-0.4/-0.3 |
| NY-AM | OUR-way >=3 skip | +1.40 | +0.02 | -0.35 | -0.22 | +0.27 | -1.47 | +0.7/-1.2/-1.9/-1.5 |
| NY-AM | AGAINST >=3 skip | -1.39 | -1.56 | -0.35 | +0.34 | -0.38 | +5.45 | -1.3/-1.5/-0.6/+0.1 |
| NY-PM (235, 8.3) | ER>=0.2 gate | +4.34 | -0.76 | +3.80 | +4.36 | +4.33 | +14.27 | +0.3/-1.6/+0.8/+1.3 |
| NY-PM | ER>=0.2 sizer | +2.43 | -0.40 | +1.83 | +2.20 | +2.18 | +7.37 | +1.4/-1.2/+0.6/+0.9 [+1.3/+1.3/-2.5/-1.5] |
| NY-PM | ER>=0.3 gate | +4.81 | -1.09 | +3.58 | +2.70 | +4.89 | +14.04 | +0.3/-2.3/-0.2/+0.2 |
| NY-PM | OUR-way >=3 skip | +3.09 | +2.77 | -1.05 | +0.14 | +0.97 | -2.59 | +0.4/+0.3/-0.1/-0.1 |
| NY-PM | AGAINST >=3 skip | -2.03 | -1.51 | +3.77 | +1.68 | +1.88 | +0.18 | -0.2/-0.6/+0.5/+0.5 |
Session reading: every session rate lift is inside its own MDE (2-17 pts); no session is positive in X', PRE, HOLD and L6M for any rule; the session-only stacks do not add up to the pooled one (locks are per book, rule interacts with the day). KB session base stack alone (other sessions skipped), research $/wk L6M/PRE: Asia +1.2k/+2.2k, London +5.4k/+0.8k, NY-AM -2.0k/+5.1k, NY-PM -1.6k/+1.0k (HOLD: -1.1k / +4.4k / -2.4k / -2.6k) - the recent KB dollars are London.

## 5. WALK-FORWARD CHAIN (monthly re-fit, trailing window, 49 cells + none; B2; rate per planned lot; chain starts 2024-04 so "PRE" = 2024-04..2025-06)
| chain | PRE | HOLD | L6M | L3M | Y26 | rank vs 200 random-cell chains (PRE / HOLD / L6M) | last re-fit pick | stack unscaled X'/PRE/HOLD/L6M/L3M (research $k) |
|---|---|---|---|---|---|---|---|---|
| anchored (all data since 2023-04) | +0.07 | +5.51 | +5.37 | +5.45 | +2.66 | 0.40 / 1.00 / 0.995 | ER>=0.3 gate + skip OUR-way >=3 | 0 / -9.6 / -0.5 / -0.7 / +8.3 |
| rolling 12 months | -1.28 | +2.04 | +2.03 | +1.47 | +2.94 | 0.01 / 0.52 / 0.50 | ER>=0.3 gate + skip AGAINST >=5 | +1.9 / -8.8 / -0.8 / -1.0 / +4.8 |
Static comparison over the same months (B2): ER0.2 gate PRE +0.69 / L6M +2.71, ER0.3 gate +0.32 / +5.81, ER0.2 sizer +0.37 / +1.45, OUR-way 3 +0.53 / +0.90. The anchored chain is the ER >= 0.3 gate with the OUR-way skip appended: great rate in the recent windows, zero in PRE and negative on the stack in PRE.

## 6. SENSITIVITY (B2, KB live; thresholds +-25% / +-50%; gate rate, sizer SIZED-R stack)
| ER thr | keep | gate rate X'/PRE/HOLD/L6M | gate stack PLAN-R PRE / L6M | sizer SIZED-R stack X'/PRE/HOLD/L6M $k |
|---|---|---|---|---|
| 0.10 | 0.79 | +0.67/+0.18/+0.60/+0.71 | -1.3/+1.6 | +1.2/+4.4/+4.6/+6.3 |
| 0.15 | 0.68 | +0.65/-0.59/+1.62/+1.74 | -4.1/+0.4 | +2.2/+1.7/+3.0/+4.3 |
| **0.20** | 0.58 | +1.72/+0.53/+2.68/+2.71 | -3.0/+2.6 | +2.3/+3.4/+6.5/+8.1 |
| 0.25 | 0.47 | +2.37/+1.53/+4.50/+4.47 | -1.4/+1.0 | +1.1/+2.6/+2.5/+4.0 |
| 0.30 | 0.37 | +1.41/+0.54/+5.93/+5.81 | -7.4/-0.3 | -0.2/-1.0/+3.5/+4.8 |
| 0.35 | 0.29 | -0.01/+0.13/+6.81/+6.32 | -8.6/+0.0 | -1.1/-0.8/+1.8/+2.2 |
| 0.40 | 0.21 | +2.74/+3.26/+8.20/+6.18 | -6.6/-1.6 | +0.9/+0.4/+2.9/+1.5 |
| 0.45 | 0.15 | +4.70/+2.99/+6.68/+5.04 | -6.9/-6.0 | +0.6/-0.2/-1.8/-2.7 |
Reading: the rate lift grows with the threshold (a monotone regime effect, positive in every threshold in HOLD/L6M); the stack is best at 0.10-0.25 because the gate costs volume above that. So the "chop filter" is real in the rate and the dollar optimum is the soft sizer, not the hard gate. Lean R (B2 rate X'/PRE/HOLD/L6M, stack L6M $k): OUR-way R=2 +2.00/+0.55/+1.75/+1.19 (-4.1k); R=3 +1.65/+0.51/+1.15/+0.90 (-1.7k); R=4 +1.25/+0.51/+0.32/+0.15 (-0.9k); R=5 +0.90/+0.30/+0.01/-0.10 (-0.5k); R=7 +0.36/+0.32/-0.71/-0.79; R=10 +0.05/+0.20/-0.73/-0.87; R=15 +0.13/+0.19/-0.44/-0.43; R=20 -0.26 HOLD. AGAINST R=2 -3.19/-0.92/+0.18/+0.51; R=3 -1.44/-0.99/+0.18/+0.60; R=4 +0.13/-1.07/-0.41/-0.05; R=5 +0.17/-0.92/-0.01/+0.10; R>=10 ~0 (<1% of signals at 15+). The OUR-way skip is a knife edge at 2-4 minutes (fails +-50%: R=5 is 0 in the recent windows).

## 7. VALIDITY COLUMNS (the quant layer; B2, KB live)
| cell | rate [L6M] | trade placebo rank L6M/HOLD/PRE/X' (300 draws) | stack placebo rank L6M/HOLD/PRE/X' (200 draws) | 60-s-stale rate L6M | quarters + of 12 | top-5% trades | tier |
|---|---|---|---|---|---|---|---|
| ER>=0.2 sizer, SIZED-R | +1.45 | 0.97/0.98/0.67/0.89 | 1.00/1.00/0.68/0.94 | n/a | 10 | skipped-loser driven (gate: best 5% of trades = 115% of the net gain) | LEAD |
| ER>=0.2 sizer, PLAN-R | +1.45 | same | 0.99/0.99/0.48/0.66 | n/a | 10 | | CANDIDATE-RECENT |
| ER>=0.2 gate | +2.71 | 0.97/0.98/0.67/0.89 | 0.99/0.99/0.56/0.81 | n/a | 10 | | CANDIDATE-RECENT |
| ER>=0.3 gate | +5.81 | 0.99/0.99/0.60/0.76 | 1.00/0.98/0.24/0.60 | n/a | 8 | | CANDIDATE-RECENT (rate), DEAD stack |
| ER>=0.3 sizer, SIZED-R | +2.40 | 0.99/0.99/0.60/0.76 | 1.00/1.00/0.24/0.70 | n/a | 8 | | CANDIDATE-RECENT |
| OUR-way >=3 skip | +0.90 | 0.84/0.91/0.84/1.00 | 0.68/0.71/0.32/0.92 | -0.78 | 9 | | rate LEAD, stack DEAD |
| OUR-way >=5 skip | -0.10 | 0.43/0.52/0.78/1.00 | 0.73/0.66/0.34/0.66 | -0.60 | 8 | | DEAD |
| AGAINST >=3 skip | +0.60 | 0.75/0.63/0.09/0.12 | 0.57/0.41/0.13/0.21 | +0.46 | 4 | | DEAD (wrong sign in PRE) |
| AGAINST >=5 skip | +0.10 | 0.61/0.56/0.01/0.55 | 0.50/0.52/0.10/0.44 | -0.54 | 5 | | DEAD |
| ER>=0.2 sizer + OUR-way >=3 | +2.17 | 0.97/0.98/0.68/0.99 | 0.88/0.89/0.56/1.00 (SIZED-R) | +0.43 | 11 | | below ER alone on the stack |
Program: White RC p 0.076 (studentised 0.088), PBO 0.087, 34 distinct cells, cumulative Sidak over the 2.47M-cell programme 1.0; DSR/Romano-Wolf not computed per cell (nothing reaches the program RC gate). Latency: ER is a completed-bar value (no latency dependence); the lean feature uses the book up to the signal second - the 60-s-stale control is negative, so a decision on a stale book would lose the effect; 1-s / 3-s replay not run (needs the live tape at the decision second). Capacity: a skip and a x0.5 / x1.5 on 2 lots need no depth (KB 2 lots -> 1 or 3); not measured beyond that. Not filled: breakeven slippage, queue.

## 8. STACK LINE - KB book through the lock engine, 70/30 N, research lots (mean / SD / maxDD / sum of the worst 20 weeks, $k)
| rule | L6M | HOLD | PRE | X' |
|---|---|---|---|---|
| KB as it is | 9.5 / 30.8 / 148 / -105 | 7.7 / 35.6 / 148 / -273 | 9.7 / 26.7 / 110 / -466 | 0.8 / 21.7 / 146 / -340 |
| ER>=0.2 sizer, SIZED-R | 17.6 / 37.1 / 139 / +9 | 14.2 / 43.9 / 150 / -258 | 13.1 / 41.0 / 160 / -731 | 3.2 / 28.4 / 161 / -416 |
| ER>=0.2 sizer, PLAN-R | 12.6 / 28.0 / 123 / -11 | 10.5 / 34.9 / 127 / -207 | 8.1 / 31.6 / 139 / -624 | 1.6 / 22.7 / 114 / -355 |
| ER>=0.2 gate | 12.1 / 26.4 / 99 / -20 | 10.0 / 28.7 / 99 / -182 | 6.7 / 28.6 / 129 / -554 | 1.3 / 20.5 / 117 / -338 |
| ER>=0.3 gate | 9.2 / 21.8 / 58 / -21 | 7.2 / 23.6 / 68 / -154 | 2.3 / 24.1 / 122 / -520 | 0.1 / 19.1 / 143 / -330 |
| ER>=0.3 sizer, SIZED-R | 14.3 / 39.2 / 145 / -49 | 11.1 / 43.6 / 145 / -313 | 8.6 / 36.7 / 142 / -750 | 0.6 / 25.8 / 174 / -446 |
| skip OUR-way >=3 | 7.8 / 27.3 / 140 / -115 | 5.9 / 31.1 / 140 / -266 | 7.3 / 26.7 / 99 / -514 | 1.7 / 22.6 / 108 / -362 |
The SIZED-R sizer raises the mean by +8.1k in L6M and also the SD (+6k) and the PRE maxDD (160k vs 110k) and PRE worst-20 sum (-731k vs -466k): in PRE the lead is bigger mean, deeper drawdown. Live KB 2 lots: multiply every number by 0.385 (KB base L6M $3.7k/wk; with the lead $6.8k/wk).

## 9. SENTENCE
As coded, KB with an ER >= 0.2 x1.5 / x0.5 sizer and sized-lot-R locks adds +8.1k per week in L6M at research lots (MDE 12.2k), +6.5k HOLD, +3.4k PRE, +2.3k X' (live KB 2 lots: +3.1k / +2.5k / +1.3k / +0.9k); the TG-1 chop gate (ER >= 0.3 skip) lifts the rate by +5.8 pts per lot but not the stack (-0.3k L6M, -7.4k PRE); the book-lean skip works in the rate only when the book has leaned OUR way (not AGAINST) for >= 3 minutes (+0.9 L6M, +0.5 PRE) and costs -1.7k per week on the stack; the two together are worse than ER alone.

## 10. WHAT THIS DID NOT DO / OPEN
* Question (MORNING.md): D6 governors on planned-lot R or sized-lot R? It decides whether the ER sizer is a live +3.1k (sized) or +1.2k with PRE -0.6k (planned) per week at KB 2 lots; the order text says sized (multiplied by the day's largest multiplier).
* Selection caveat: thresholds 0.2/0.3 and R=3 were named from earlier recent-window looks; PRE+X' ranked 0.2 over 0.3 and 3 over 5/15 but the PRE evidence is weak (rate +0.3..+0.5, placebo rank 0.67). The SIZED-R lead has a stack PRE placebo rank 0.68.
* Not run: 1-s/3-s latency replay of the lean skip, depth/capacity at the live fills, DSR / Romano-Wolf per cell, a per-session walk-forward, the 15-min-bar and 1-min-bar ER variants (TG-1: lift 0). Stack numbers are KB-only (locks are per book); the full-stack composition with the other sizers is the Sunday-stack report's job (DS3_SUNDAY_STACK.md).
* Files: out/kbregime/ stage1.csv, stage2.csv (all cells x scopes x windows x bases), stack_s2lib.csv, stack_sess.csv, stack_wf.csv, stack_placebo.csv, placebo_rank.csv, sens.csv, wf_summary.csv, drift_q.csv, qv_program.json, stale60.csv, sess_alone.csv; code l2vast/ds3/code/kbregime/ (kbr_stack.py holds the SIZED-R lock variant).
