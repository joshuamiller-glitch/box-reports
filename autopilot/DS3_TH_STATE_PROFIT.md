# DS3_TH_STATE_PROFIT - best PROFIT rule per book (TH-L2-S state book), PRE-PROOF
Label: **base = replica trade lists, exact 1-s state; entries not live-matched** (about 100 of 187 blind-week trades match). No PASS words. Prereg: autopilot/DS3_TH_STATE_PROFIT_PREREG.md sha256 a805981f4734c46590a27fe53f59dccab43925b022b9581bdc6c5268522684df (logged in DECISIONS.md before any result was read; two logged addenda: u forward-fill on 20251128, placebo redesign).
Deltas are USD per week at the trade-set lots vs plain 60/60 hold-to-bracket (O7 40/90) on the same trades (stop at level, target nominal, time exit with 0.80 pt), carrying week dropped, selection data through 2026-10-31; windows L1M/L2M/L3M/L6M/HOLD as of 2026-10-31, MID, PRE, X'. `mean (mde)` = weekly mean delta and 2.8 sd/sqrt(n).
Execution: decision at the end of second s from the 1-s state, 1 s latency, market exit at mid(s+1) -/+ 0.80 pt, no phantom slippage credit; scale-out limits and targets are nominal (touch).

## 1. Answer first
A profit rule is delivered for every book (table below). **None of the eight ENTERS** (ENTER = tier E1 + placebo p<=.10 + family p<=.10 + purged walk-forward positive in L6M and PRE): the monthly walk-forward selection is negative in PRE for K7, P7, M7, A7, H7, O7 and U7 and L6M-positive only for K7 and H7. Best-cell first-order effects are +0 to +160 USD/week against MDEs of 200-2000 (only the K7 and O7 lock-to-breakeven cells beat their placebo, p=0.001). Cascade (Stage 2): the profit rule adds to the state loss rule in L6M for K7 (+114), P7 (+118), M7 (+136), A7 (+32), O7 (+80) but is negative in PRE for K7 (-597) and M7 (-125); U7/H7 carry no profit rule in the cascade (F4 scale-out needs a partial exit). Reading: delivered, labelled non-ENTER; plain 60/60 and these rules are not separable on this base.

| book | rule | tier | S=min(L6M,PRE) | L6M | PRE | nfire | placebo p | family p | WF L6M/PRE | ENTER |
|---|---|---|---|---|---|---|---|---|---|---|
| K7 | F3 lock-to-breakeven: once unreal >= 0.8 x target move stop to entry+2 pt; market exit when mid touches | E1 | +111 | +111 | +162 | 794 | 0.001 | 0.028 | +50/-843 | no |
| P7 | F1 thick-book ahead_rel >= 1.5 for 30 s once unreal >= 45 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme | E2 | -1 | +0 | -1 | 53 | 0.038 | 0.952 | -1426/-2450 | no |
| M7 | F1 thick-book tot_rel >= 1.3 for 3 s once unreal >= 45 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme | E1 | -29 | +142 | -29 | 383 | 0.469 | 1.000 | -268/-288 | no |
| U7 | F4 scale-out half of the lots at 60% of target (nominal limit) | E1 | +68 | +448 | +68 | 813 | 1.000 | 1.000 | -676/-319 | no |
| A7 | F1 thick-book tot_rel >= 1.5 for 30 s once unreal >= 15 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme | E1 | +18 | +200 | +18 | 112 | 0.288 | 0.476 | -9/-137 | no |
| H7 | F4 scale-out half of the lots at 80% of target (nominal limit) | E1 | -86 | +139 | -86 | 305 | 1.000 | 1.000 | +282/-473 | no |
| O7 | F3 lock-to-breakeven: once unreal >= 0.7 x target move stop to entry+2 pt; market exit when mid touches | E1 | +93 | +163 | +93 | 57 | 0.001 | 0.028 | -8/-116 | no |
| X3/X4/X5 (8 trades) | pooled-all-books best: F1 thick-book ahead_rel(slow base) >= 2.5 for 30 s once unreal >= 45 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme | E2 | - | - | - | 0 | - | - | - | no |

## 2. Policy-file lines (D7 grammar) and what the grammar lacks
- K7: `profit K7 * pct>=0.80 lock 2`  -- missing: none: `lock` and `pct` exist (the touch is checked once per ThEvalFrequencySecs on the last price; scored on the 1-s mid with 1 s latency)
- P7: `profit P7 * pct>=0.75 ahead_rel>=1.5 tighten 20   # + persist=30s (field missing)`  -- missing: `persist=<s>` (condition true for 30 consecutive seconds); baseline updated once per second (live: every depth event) - same family, not the same numbers
- M7: `profit M7 * pct>=0.75 tot_rel>=1.3 tighten 20   # + persist=3s (field missing)`  -- missing: `persist=<s>` (condition true for 3 consecutive seconds); baseline updated once per second (live: every depth event) - same family, not the same numbers
- U7: `(no D7 line: partial exit) profit U7 * pct>=0.60 scale 0.5   <- needs a new action`  -- missing: new action `scale <fraction>` (partial exit at a limit price at pct x target); inert on 1-lot books
- A7: `profit A7 * pct>=0.25 tot_rel>=1.5 tighten 20   # + persist=30s (field missing)`  -- missing: `persist=<s>` (condition true for 30 consecutive seconds); baseline updated once per second (live: every depth event) - same family, not the same numbers
- H7: `(no D7 line: partial exit) profit H7 * pct>=0.80 scale 0.5   <- needs a new action`  -- missing: new action `scale <fraction>` (partial exit at a limit price at pct x target); inert on 1-lot books
- O7: `profit O7 * pct>=0.70 lock 2`  -- missing: none: `lock` and `pct` exist (the touch is checked once per ThEvalFrequencySecs on the last price; scored on the 1-s mid with 1 s latency)
- X3/X4/X5 and `*` fallback: `profit * * pct>=0.75 ahead_rel_slow>=2.5 tighten 20   # + persist=30s (field missing)`
Grammar notes: `pct` on the profit side = unreal / target distance (60 pt; O7 90), `tighten X` = trail X pt behind the favourable extreme (1 tick = 0.25 pt, so 80 ticks = 20 pt), `lock X` = stop at entry+X pt, market exit on touch. Session field `*` for all books (no per-session override qualified, see 4). The five old live take lines are not carried over (they used ahead_rel/tot_rel with the per-event DS7 baseline).

## 3. Definitions (state-based book only)
depth8 = sum of sizes of resting levels within 7.5 ticks of the best price, per side, from the 1-s top-10 state; tot8 = bid8+ask8. Slot baseline: 48 ET half-hour slots, EWMA of tot8 over valid seconds (both sides >=5 levels), alpha .02 for the first 300 samples of a slot then .002 (**fast** = DS7 numbers) or .0003 (**slow**, ~2-day memory per slot), carried across days, no look-ahead, NaN for the first 300 samples of a slot. tot_rel = tot8/base; ahead_rel = (ask8 for a long, bid8 for a short)/(0.5 base). pulled_mult = own-side cancelled (net of trades) over the last 5 (10) s / MedLevel (0.001 EWMA of top-5 average). ice_against = number of refill events on the against-side best level in the last 30 s: best price unchanged s-1 -> s, a trade printed at that price in the second, level size larger than at s-1.
F1 thick tighten/take: once unreal >= arm, if the measure >= thick for `secs` consecutive seconds -> TAKE (market) or TIGHTEN (trail = running favourable mid extreme - X; ratchets while thick; exit when mid touches). F2: first second with unreal >= pct x target and the feature >= threshold -> market take. F3: once unreal >= pct x target the protective level = entry+buffer; market exit when mid <= level. F4: floor(lots/2) lots exit at pct x target (nominal limit; touch of the second's favourable print extreme before the bracket second); inert on 1-lot books (A7, O7, X; 14,634 of 23,989 trades are 1-lot).
Grid: 576 F1 + 105 F2 + 28 F3 + 6 F4 = 715 cells; kernel checked against a python reference (0 mismatches in 75,000 cell-trade pairs).

## 4. Per-book detail (Stage 1, first order)

### K7  - F3 lock-to-breakeven: once unreal >= 0.8 x target move stop to entry+2 pt; market exit when mid touches  (tier E1)
Policy line: `profit K7 * pct>=0.80 lock 2`
| window | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| delta vs 60/60 mean (mde) | -1388 (4044) | +1030 (4205) | +72 (3156) | +111 (2147) | -503 (1408) | -1520 (2854) | +162 (816) | -171 (790) |
| walk-forward OOS mean (mde) | -132 (1622) | -174 (1158) | -16 (931) | +50 (671) | -38 (385) | -295 (604) | -843 (1797) | -355 (526) |
Stack maxDD weekly base -> with rule: L6M 38227 -> 24102, PRE 33038 -> 32420. recents=True tolerant=True drawdown-first=True. Fires 794 of 8691 trades. Placebo p 0.001 (random-exit mean S -1380); family p 0.028 (Bonferroni over family cells). Walk-forward positive: False.
Top-4 cells by S (nfire>=30), for transparency: [705] F3 lock-to-breakeven: once unreal >= 0.8 x target move stop to entry+0 pt; market exit when mid touches S=+131 L6M=+131 PRE=+160 tier-flags r/t/d=110; [706] F3 lock-to-breakeven: once unreal >= 0.8 x target move stop to entry+2 pt; market exit when mid touches S=+111 L6M=+111 PRE=+162 tier-flags r/t/d=111; [121] F1 thick-book tot_rel >= 2.0 for 3 s once unreal >= 45 pt -> TIGHTEN trail 20 ticks (5.0 pt) behind favourable mid extreme S=+62 L6M=+130 PRE=+62 tier-flags r/t/d=001; [250] F1 thick-book tot_rel(slow base) >= 1.3 for 30 s once unreal >= 45 pt -> TIGHTEN trail 40 ticks (10.0 pt) behind favourable mid extreme S=+32 L6M=+328 PRE=+32 tier-flags r/t/d=100
By entry session (the same cell): s0 L6M +659 PRE -67 S -67 nfire 261; s1 L6M -608 PRE +124 S -608 nfire 198; s3 L6M -10 PRE -34 S -34 nfire 178; s4 L6M +122 PRE +172 S +122 nfire 157

### P7  - F1 thick-book ahead_rel >= 1.5 for 30 s once unreal >= 45 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme  (tier E2)
Policy line: `profit P7 * pct>=0.75 ahead_rel>=1.5 tighten 20   # + persist=30s (field missing)`
| window | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| delta vs 60/60 mean (mde) | +0 (0) | +0 (0) | +0 (0) | +0 (0) | -501 (502) | -145 (405) | -1 (760) | -456 (1002) |
| walk-forward OOS mean (mde) | +0 (0) | +0 (0) | -330 (925) | -1426 (2428) | -1649 (2215) | +246 (3333) | -2450 (4203) | +27 (2279) |
Stack maxDD weekly base -> with rule: L6M 169540 -> 169540, PRE 243799 -> 243799. recents=False tolerant=True drawdown-first=True. Fires 53 of 6080 trades. Placebo p 0.038 (random-exit mean S -308); family p 0.952 (shift-world max-cell). Walk-forward positive: False.
Top-4 cells by S (nfire>=30), for transparency: [23] F1 thick-book tot_rel >= 1.5 for 30 s once unreal >= 15 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme S=+199 L6M=+199 PRE=+624 tier-flags r/t/d=110; [21] F1 thick-book tot_rel >= 1.5 for 30 s once unreal >= 15 pt -> TIGHTEN trail 20 ticks (5.0 pt) behind favourable mid extreme S=+102 L6M=+453 PRE=+102 tier-flags r/t/d=010; [20] F1 thick-book tot_rel >= 1.5 for 30 s once unreal >= 15 pt -> TAKE (market) S=+60 L6M=+322 PRE=+60 tier-flags r/t/d=010; [407] F1 thick-book ahead_rel >= 1.5 for 30 s once unreal >= 45 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme S=-1 L6M=+0 PRE=-1 tier-flags r/t/d=011
By entry session (the same cell): s0 L6M +0 PRE +97 S +0 nfire 34; s1 L6M +0 PRE +0 S +0 nfire 11; s3 L6M +0 PRE -45 S -45 nfire 8

### M7  - F1 thick-book tot_rel >= 1.3 for 3 s once unreal >= 45 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme  (tier E1)
Policy line: `profit M7 * pct>=0.75 tot_rel>=1.3 tighten 20   # + persist=3s (field missing)`
| window | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| delta vs 60/60 mean (mde) | +1841 (2171) | +529 (1507) | +877 (1497) | +142 (1217) | +141 (765) | +181 (1076) | -29 (534) | -201 (628) |
| walk-forward OOS mean (mde) | +344 (1712) | -390 (1263) | -117 (983) | -268 (787) | -48 (612) | -135 (1024) | -288 (679) | -76 (161) |
Stack maxDD weekly base -> with rule: L6M 76581 -> 76140, PRE 41262 -> 38933. recents=True tolerant=True drawdown-first=True. Fires 383 of 4814 trades. Placebo p 0.469 (random-exit mean S -52); family p 1.000 (shift-world max-cell). Walk-forward positive: False.
Top-4 cells by S (nfire>=30), for transparency: [710] F4 scale-out half of the lots at 40% of target (nominal limit) S=+11 L6M=+235 PRE=+11 tier-flags r/t/d=010; [714] F4 scale-out half of the lots at 80% of target (nominal limit) S=+8 L6M=+99 PRE=+8 tier-flags r/t/d=001; [259] F1 thick-book tot_rel(slow base) >= 1.5 for 10 s once unreal >= 45 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme S=+3 L6M=+3 PRE=+10 tier-flags r/t/d=010; [711] F4 scale-out half of the lots at 50% of target (nominal limit) S=+2 L6M=+92 PRE=+2 tier-flags r/t/d=011
By entry session (the same cell): s1 L6M -230 PRE -43 S -230 nfire 246; s3 L6M -172 PRE -30 S -172 nfire 137

### U7  - F4 scale-out half of the lots at 60% of target (nominal limit)  (tier E1)
Policy line: `(no D7 line: partial exit) profit U7 * pct>=0.60 scale 0.5   <- needs a new action`
| window | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| delta vs 60/60 mean (mde) | +811 (3279) | +1056 (2483) | +1217 (1665) | +448 (1668) | +139 (1210) | +115 (2755) | +68 (948) | -212 (942) |
| walk-forward OOS mean (mde) | +1274 (3225) | +92 (2601) | -414 (1930) | -676 (1222) | -10 (995) | +311 (1837) | -319 (1976) | +105 (380) |
Stack maxDD weekly base -> with rule: L6M 21436 -> 16314, PRE 38615 -> 29452. recents=True tolerant=True drawdown-first=True. Fires 813 of 1490 trades. Placebo p 1.000 (random-exit mean S 3849); family p 1.000 (Bonferroni over family cells). Walk-forward positive: False.
Top-4 cells by S (nfire>=30), for transparency: [647] F2 take when unreal >= 0.50 x target and tot_rel >= 2 S=+274 L6M=+274 PRE=+414 tier-flags r/t/d=001; [653] F2 take when unreal >= 0.50 x target and pulled_mult(5 s) >= 20 S=+156 L6M=+1086 PRE=+156 tier-flags r/t/d=101; [656] F2 take when unreal >= 0.50 x target and pulled_mult(10 s) >= 35 S=+102 L6M=+504 PRE=+102 tier-flags r/t/d=110; [167] F1 thick-book tot_rel(slow base) >= 1.5 for 30 s once unreal >= 15 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme S=+72 L6M=+72 PRE=+137 tier-flags r/t/d=010
By entry session (the same cell): s0 L6M -311 PRE -30 S -311 nfire 415; s1 L6M -69 PRE +7 S -69 nfire 398

### A7  - F1 thick-book tot_rel >= 1.5 for 30 s once unreal >= 15 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme  (tier E1)
Policy line: `profit A7 * pct>=0.25 tot_rel>=1.5 tighten 20   # + persist=30s (field missing)`
| window | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| delta vs 60/60 mean (mde) | +346 (970) | +0 (0) | +36 (360) | +200 (328) | +100 (308) | -67 (491) | +18 (225) | -64 (426) |
| walk-forward OOS mean (mde) | -67 (187) | +0 (0) | -19 (53) | -9 (26) | +15 (121) | +147 (553) | -137 (351) | -45 (92) |
Stack maxDD weekly base -> with rule: L6M 10263 -> 8731, PRE 7274 -> 7274. recents=True tolerant=True drawdown-first=True. Fires 112 of 1252 trades. Placebo p 0.288 (random-exit mean S -35); family p 0.476 (shift-world max-cell). Walk-forward positive: False.
Top-4 cells by S (nfire>=30), for transparency: [165] F1 thick-book tot_rel(slow base) >= 1.5 for 30 s once unreal >= 15 pt -> TIGHTEN trail 20 ticks (5.0 pt) behind favourable mid extreme S=+97 L6M=+97 PRE=+124 tier-flags r/t/d=011; [164] F1 thick-book tot_rel(slow base) >= 1.5 for 30 s once unreal >= 15 pt -> TAKE (market) S=+87 L6M=+87 PRE=+119 tier-flags r/t/d=011; [166] F1 thick-book tot_rel(slow base) >= 1.5 for 30 s once unreal >= 15 pt -> TIGHTEN trail 40 ticks (10.0 pt) behind favourable mid extreme S=+48 L6M=+48 PRE=+66 tier-flags r/t/d=011; [179] F1 thick-book tot_rel(slow base) >= 2.0 for 30 s once unreal >= 15 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme S=+32 L6M=+80 PRE=+32 tier-flags r/t/d=011
By entry session (the same cell): s0 L6M +200 PRE +18 S +18 nfire 112

### H7  - F4 scale-out half of the lots at 80% of target (nominal limit)  (tier E1)
Policy line: `(no D7 line: partial exit) profit H7 * pct>=0.80 scale 0.5   <- needs a new action`
| window | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| delta vs 60/60 mean (mde) | +870 (2574) | -34 (1082) | +16 (840) | +139 (711) | +87 (430) | +39 (860) | -86 (357) | +6 (480) |
| walk-forward OOS mean (mde) | -1420 (1793) | -106 (2083) | -491 (2144) | +282 (1892) | +130 (1002) | -244 (307) | -473 (805) | -170 (312) |
Stack maxDD weekly base -> with rule: L6M 23170 -> 22013, PRE 19462 -> 19462. recents=True tolerant=True drawdown-first=True. Fires 305 of 1145 trades. Placebo p 1.000 (random-exit mean S 1250); family p 1.000 (Bonferroni over family cells). Walk-forward positive: False.
Top-4 cells by S (nfire>=30), for transparency: [653] F2 take when unreal >= 0.50 x target and pulled_mult(5 s) >= 20 S=+54 L6M=+110 PRE=+54 tier-flags r/t/d=100; [674] F2 take when unreal >= 0.70 x target and pulled_mult(5 s) >= 20 S=+15 L6M=+516 PRE=+15 tier-flags r/t/d=100; [617] F2 take when unreal >= 0.17 x target and ice_against >= 4 S=-9 L6M=-9 PRE=+40 tier-flags r/t/d=010; [75] F1 thick-book tot_rel >= 2.0 for 3 s once unreal >= 30 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme S=-25 L6M=+34 PRE=-25 tier-flags r/t/d=100
By entry session (the same cell): s0 L6M +139 PRE -86 S -86 nfire 305; s3 L6M +0 PRE +0 S +0 nfire 0

### O7  - F3 lock-to-breakeven: once unreal >= 0.7 x target move stop to entry+2 pt; market exit when mid touches  (tier E1)
Policy line: `profit O7 * pct>=0.70 lock 2`
| window | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| delta vs 60/60 mean (mde) | +177 (496) | +111 (310) | +136 (257) | +163 (332) | -54 (293) | -101 (514) | +93 (128) | -103 (317) |
| walk-forward OOS mean (mde) | +0 (0) | +0 (0) | +0 (0) | -8 (24) | -102 (157) | +0 (0) | -116 (223) | -62 (122) |
Stack maxDD weekly base -> with rule: L6M 7489 -> 7489, PRE 5097 -> 4343. recents=True tolerant=True drawdown-first=True. Fires 57 of 509 trades. Placebo p 0.001 (random-exit mean S -116); family p 0.028 (Bonferroni over family cells). Walk-forward positive: False.
Top-4 cells by S (nfire>=30), for transparency: [702] F3 lock-to-breakeven: once unreal >= 0.7 x target move stop to entry+2 pt; market exit when mid touches S=+93 L6M=+163 PRE=+93 tier-flags r/t/d=111; [701] F3 lock-to-breakeven: once unreal >= 0.7 x target move stop to entry+0 pt; market exit when mid touches S=+85 L6M=+150 PRE=+85 tier-flags r/t/d=111; [707] F3 lock-to-breakeven: once unreal >= 0.8 x target move stop to entry+5 pt; market exit when mid touches S=+62 L6M=+62 PRE=+100 tier-flags r/t/d=111; [703] F3 lock-to-breakeven: once unreal >= 0.7 x target move stop to entry+5 pt; market exit when mid touches S=+55 L6M=+100 PRE=+55 tier-flags r/t/d=010
By entry session (the same cell): s3 L6M +163 PRE +93 S +93 nfire 57

Per-session overrides: none qualified (rule: unit-best in tier E1, placebo p<=.10, S gain >= 1 MDE over the book cell): `[]`.
X3/X4/X5: 8 trades in the whole sample; the pooled cell is delivered as the `*` fallback and has no evidence behind it.

## 5. Held-out live week (2026-11-01 evening .. 11-05, 187 live trades, csv sha256 424c68da934136df7124004b4b1fd9a34952a1e5e3e6ba1017ad0d972a927112)
Each book rule applied on the live path from the live entry fill to the ACTUAL live exit (state features, first-order, live lots); delta = rule exit pts (mid(s+1)-+0.80) minus live exit pts, only if the rule fires before the live exit. Reported, never selected on.
| book | rule | trades | fires | delta USD | better | worse | live gross USD |
|---|---|---|---|---|---|---|---|
| A7 | F1 thick-book tot_rel >= 1.5 for 30 s once unreal >= 15 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme | 23 | 0 | +0 | 0 | 0 | -1415 |
| H7 | F4 scale-out half of the lots at 80% of target (nominal limit) | 3 | 0 | +0 | 0 | 0 | -775 |
| K7 | F3 lock-to-breakeven: once unreal >= 0.8 x target move stop to entry+2 pt; market exit when mid touches | 64 | 8 | -1939 | 5 | 3 | +14845 |
| M7 | F1 thick-book tot_rel >= 1.3 for 3 s once unreal >= 45 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme | 28 | 2 | +1008 | 1 | 1 | +6738 |
| O7 | F3 lock-to-breakeven: once unreal >= 0.7 x target move stop to entry+2 pt; market exit when mid touches | 3 | 1 | +436 | 1 | 0 | +660 |
| P7 | F1 thick-book ahead_rel >= 1.5 for 30 s once unreal >= 45 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme | 53 | 0 | +0 | 0 | 0 | +85302 |
| U7 | F4 scale-out half of the lots at 60% of target (nominal limit) | 6 | 2 | -1445 | 0 | 2 | +624 |
| X3 | F1 thick-book ahead_rel(slow base) >= 2.5 for 30 s once unreal >= 45 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme | 3 | 0 | +0 | 0 | 0 | -910 |
| X4 | F1 thick-book ahead_rel(slow base) >= 2.5 for 30 s once unreal >= 45 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme | 2 | 0 | +0 | 0 | 0 | -175 |
| X5 | F1 thick-book ahead_rel(slow base) >= 2.5 for 30 s once unreal >= 45 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme | 2 | 0 | +0 | 0 | 0 | +350 |
Total delta -1939 USD on live gross +105243 (one week; K7 lock 0.8 cost 3 worse of 8 fires; a single week is not evidence).

## 6. E = best loss rule x best profit rule vs loss-only vs plain 60/60
Loss rules: STATE-SCORE per-book finalists (loss_finalists.json, incl. session overrides P7_0 and H7_3, lot-scaled ARM variants). First event of the two rules wins per trade (tie -> loss). First-order on the Stage-1 trade set (same windows, carrying week dropped); `E-loss` = what the profit rule adds on top of the loss rule.
| book | loss-only vs 60/60 L6M / PRE | profit-only vs 60/60 L6M / PRE | E vs 60/60 L6M / PRE | E - loss-only L6M (mde) / PRE (mde) / X' | S gain | p (feature-shift worlds) |
|---|---|---|---|---|---|---|
| K7 | +1401 / +31 | +111 / +162 | +1406 / -397 | +142 (1437) / +2 (730) / -231 | +2 | n/a (no book input; see placebo) |
| P7 | +7383 / +468 | +0 / -1 | +7165 / +678 | +0 (0) / +33 (593) / -214 | +0 | 0.048 |
| M7 | +1281 / +285 | +142 / -29 | +1213 / +75 | -68 (933) / -183 (378) / -94 | -183 | 0.286 |
| U7 | +905 / +121 | +448 / +68 | +261 / +92 | +142 (1500) / +50 (933) / -307 | +50 | n/a (no book input; see placebo) |
| A7 | +731 / +41 | +200 / +18 | +782 / +33 | +178 (312) / +14 (222) / -64 | +14 | 0.190 |
| H7 | +1530 / +51 | +139 / -86 | +1608 / -26 | -58 (546) / -135 (311) / +80 | -135 | n/a (no book input; see placebo) |
| O7 | +129 / +15 | +163 / +93 | +165 / +50 | +112 (281) / +60 (107) / -79 | +60 | n/a (no book input; see placebo) |
| XP | +0 / +0 | +0 / +0 | +0 / +0 | +0 (0) / +0 (0) / +0 | +0 | 1.000 |
| ALL | +10655 / +250 | -252 / +295 | +10150 / +260 | +78 (2235) / -172 (1759) / -754 | -172 | n/a (no book input; see placebo) |
Full E window tables (all eight windows, drawdown) are in /mnt/l2/l2vast/_th_state/profit/E_res.json.

## 7. Stage 2: cascade through the replica engine (ITER14 settings, re-entries/locks live)
Runs: L = loss rules by unit only; P = profit rules only (U7 and H7 are F4 scale-outs: the replica adapter has no partial exit, so P/E carry no profit rule for them: E = L there); E = both; reference = engine never-cut (A2 nocut) and live-cut HOLD. Months 2023-04..2026-10, trades by exit label day, carrying week dropped. Delta USD/week.
| book | P - nocut L6M / PRE / X' | L - nocut L6M / PRE | E - nocut L6M / PRE | **E - L** L6M (mde) / PRE (mde) / X' | trades P/L/E | profit cuts in E |
|---|---|---|---|---|---|---|
| K7 | +441 / -291 / -286 | -178 / -347 | +409 / -1560 | +114 (1679) / -597 (1116) / -314 | 6778/7482/7900 | 613 |
| P7 | -399 / +30 / -364 | +8946 / +1035 | +9064 / +1219 | +118 (318) / +19 (838) / +71 | 4667/5325/5356 | 43 |
| M7 | +307 / +88 / -641 | -125 / +285 | -175 / +66 | +136 (1151) / -125 (558) / -298 | 3876/4516/4649 | 327 |
| U7 | +0 / -4 / +0 | +202 / +75 | +211 / +61 | +8 (24) / -9 (13) / +0 | 1368/1375/1374 | 0 |
| A7 | +115 / -27 / -88 | +57 / +46 | +207 / +23 | +32 (213) / +5 (224) / -88 | 1169/1159/1182 | 110 |
| H7 | +0 / -1 / -1 | +670 / -24 | +670 / -28 | +0 (0) / -1 (2) / -1 | 1093/1106/1106 | 0 |
| O7 | +117 / +58 / -61 | +90 / +3 | +184 / +5 | +80 (268) / +26 (100) / -19 | 506/506/506 | 41 |
| XP | +0 / +0 / +0 | +0 / +0 | +0 / +0 | +0 (0) / +0 (0) / +0 | 0/0/0 | 0 |
| ALL | -169 / -417 / -1056 | +3761 / +635 | +4550 / +1155 | +1186 (2292) / -1030 (1499) / -511 | 19457/21469/22073 | 1134 |
Full window/drawdown tables: /mnt/l2/l2vast/_th_state/profit/stage2_res.json (also vs HOLD).

## 8. Caveats
(1) Entries are replica-engine entries, not live-matched. (2) Stage 1 scores each trade alone; a profit exit frees the book for re-entries only in Stage 2. (3) Stops in Stage 1 are at the level; the engine charges stop slippage, so Stage 2 hold values differ. (4) 3 trades on 2025-11-28 (half-day, book feed ends) use a forward-filled last price. (5) Placebo draws 1000, family worlds 20 (minimum p = 1/21 = 0.048 for the family test), walk-forward is monthly 2024-01..2026-10 so PRE is covered from 2024-02 only and X' not at all. (6) F3 and F4 have no book input; their family null is Bonferroni over their cells (28 / 6) and the F4 null permutes which lots>=2 trades are scaled. (7) The live grammar evaluates once per ThEvalFrequencySecs on the last price; the scored rule is once per exchange second on the 1-s mid with 1 s latency.

Data/code: /mnt/l2/l2vast/_th_state/profit/ (rows.npy 221M path-seconds, F.npy, tabs.pkl, stage1_res.json, E_res.json, stage2/), code/th_state_profit/.