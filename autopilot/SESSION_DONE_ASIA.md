# SESSION DONE: ASIA (2026-11-24T16:12Z)
STATUS: FROZEN until the next 2-week refit. No further widening, no new first looks, no further null draws (parked rows stay parked). Compiled by W-ASIAFINAL from files; sources named per line. Numbers not in a file are marked.

## 1. Candidates judged and passed (step a)
- 1,374 first-look candidates (L6M and L3M > 0 on the all-new base): 735 unaffected-bar books (BASE set) + 639 affected-bar books (judged on the _CANC set). ASIA_STEPA_RECONCILED.md (03:55Z): affected 639 fully judged (216 rejected at first look, 167 passed prior years, all 167 with 30 controls); unaffected 735: 532 had all 42 months at 03:55Z, 208 passed prior years, 190 controls decided then. Final unaffected counts after 05:57Z: NOT IN ONE FILE. aln_state.json (13:03Z): 1,063 Asia books judged, 380 pass, 380 have control sets, 378 decided.
- Feed pending_asia_all.txt = 0 since 05:57Z (step a drained). Last 17 books (598 rows) landed 11:50-12:59Z, judged: 0 of 17 pass. No Asia leases running; no lost rows.
- Pool: 87 books, hash 0d89b81689, unchanged since 06:08:26Z. Controls = 30 date-shift sets per passing book (L6M); 532 control families complete. 31 bracket books were early-stopped by W-BRKT (lost >3 of the first 10-20 controls): not lost rows. The loop counters "waiting_on 30 sets", "waiting for controls 28" and "fitted 1 of 87" are display artifacts / not gates (details in autopilot/ASIA_FINAL_STATUS.md).

## 2. Final stacks and sizes (W-COMBO loops, all done, finals_ready_asia.json)
| option | members (size) | set | controls (L6M DD-first / L3M / ulcer-only) |
|---|---|---|---|
| A (RECOMMENDED) | L385f4f2e.J502 (1) | TL3_ALN_AS_L385f4f2e_P2JCX502 | 30 / 27 / 30 |
| B (more dollars, about 3x drawdown) | Lb0e6dfa3.BRF40_80, L385f4f2e.J502, L9c2622b0.BRP45, L4aaacdb2.BRP30 (1 each) | TL3_ALN_AS_STKd8da2eb47b | 30 / 26 / 30 |
Other loop finals (information): asia-stay and asia-stay-w = Lb0e6dfa3.BRF40_80 alone (controls 29/20/30).
The file's five: STAY = Lb0e6dfa3.BRF40_80 (in B) and L385f4f2e.J502 (in A and B). GO (in no FINAL) = L92a90948, L6b373671.BRP60, L578701ed.

## 3. Bare against bare vs the bare D7 Asia stack (BARE_D7_YARDSTICK.md, TL3_ALN_AS_STKLIVE_BARE; 1 lot; cells ulcer / maxDD / worst wk / $ per wk)
Bare D7 Asia stack: L6M 13,133 / -32,277 / -21,126 / 5,654; L3M 12,212 / -27,920 / -17,823 / 3,191; 2023 -$160, 2024 $1,386, 2025 $1,273 per wk; persistence 0.63; beats 22 of 30 luck controls (29 ulcer-only).
Scaled to the same L6M max drawdown (W-LAYERS2): A bare J502 $2,071/wk vs D7 $337 = 6.1x; A with layers $1,259 vs $222 = 5.7x. B bare $7,217 vs D7 $1,849 = 3.9x; B with layers $3,783 vs $661 = 5.7x.
Unfitted loop-page numbers (1 lot): A L6M ulcer 469, $2,157/wk, L3M $2,514, 2023/24/25 $40/$217/$179, persistence 0.65; B L6M ulcer 2,604, $7,107/wk, L3M $5,884, 2023/24/25 $727/$1,214/$890, persistence 0.71.

## 4. Fitted 2-lot picks (W-LAYERS2, BAREFIT_AS_*_R200_L2.md; cells ulcer / maxDD / worst wk / worst day / $ per wk, bare -> pick)
- A: J502 alone, pick BF2_JT6 (TL3_SR_AS_L385f4f2e_P2JCX502_BF2_JT6; STC-free JT206 is the same pick). L6M 530 / -1,922 / -1,617 / -1,922 / 2,071 -> 315 / -1,267 / -800 / -1,240 / 1,259. L3M 615 / -1,922 / -992 / -1,922 / 2,410 -> 373 / -1,267 / -102 / -1,240 / 1,392. 2023 $42 -> $19, 2024 $235 -> $180, 2025 $160 -> $159 per wk (ulcer lower in all three: 2,262->1,080, 4,476->2,446, 4,428->1,728). Year bands GREEN/GREEN/GREEN. Rolling walk-forward 0.846 over 78 periods; persistence 0.902.
- B: 4-book, pick BF2_JT110 (TL3_SR_AS_STKd8da2eb47b_BF2_JT110; STC-free JT210 same pick). L6M 2,943 / -10,556 / -5,111 / -6,858 / 7,217 -> 1,000 / -3,776 / -2,249 / -2,251 / 3,783. L3M 3,470 / -10,556 / 456 / -6,858 / 6,037 -> 993 / -3,237 / 253 / -2,222 / 3,017. 2023 $902 -> $253, 2024 $1,187 -> $674, 2025 $1,285 -> $553 per wk. Bands RED/GREEN/AMBER (2023 RED: gives up most 2023 dollars). Walk-forward 0.875 over 80 periods; persistence 0.839.
- NULL (2-lot basis, gate 4 of 5; "1-lot screen" in the poster text is a stale label): A real best-of L6M ulcer cut -36.8% vs null draws -67.3 / -35.3 / -46.3% = beats 1 of 3 = FAIL. B real -42.9% vs -72.4 / -63.2% = beats 0 of 2 = FAIL. LABEL FOR BOTH: WEAK-BUT-POSITIVE / NOT PROVEN. Layers stay ON as fitted (standing rule). The pick is unchanged by the label.

## 5. Exit verdicts: NO EXIT KEPT (bare brackets)
J502 and Lb0e6dfa3: all 8 exit families fail stage 1 (exit ulcer not below bare on L6M and L3M). L9c2622b0 and L4aaacdb2: only flowp_v15_t2 passes stage 1, but its L6M mean collapses ($244 vs $1,845; $15 vs $531) and every prior year is negative (-$48/-$111/-$302; -$25/-$123/-$108) = not kept (my reading; W-EXITENG posted no stage-2 line). Brackets to code: J502 60/60, Lb0e6dfa3 40/80, L9c2622b0 45/45, L4aaacdb2 30/30, session-end flat 02:00 ET, 1 lot, bare.

## 6. Layer keys and defaults pages (what the relay reads for the layer settings)
A: D8_LAYER_KEYS_ASIA_J502_JT6.md, D8_LAYER_DEFAULTS_ASIA_J502_JT6.md (STC-free twin: D8_LAYER_KEYS_ASIA_J502_STCFREE_JT206.md, D8_LAYER_DEFAULTS_ASIA_J502_STCFREE_JT206.md).
B: D8_LAYER_KEYS_ASIA_4BOOK_JT110.md, D8_LAYER_DEFAULTS_ASIA_4BOOK_JT110.md (STC-free twin: D8_LAYER_KEYS_ASIA_4BOOK_STCFREE_JT210.md, D8_LAYER_DEFAULTS_ASIA_4BOOK_STCFREE_JT210.md). Neither pick contains an STC cancel-tape rule.

## 7. Coding specs (D8_BUILD_SPEC.md; parity packs D8_PARITY_<id>_20261027.md / _20261110.md)
- L385f4f2e.J502: option A section ("2A. OPTION A [POOL 28]", about line 53): volume bar 2,600 (_CANC), trigger momentum RSI 14 / level 60, J502 entry filter (C1 setting 5 + C3 window 2), 60/60 bracket, 815 events, both sides.
- Lb0e6dfa3.BRF40_80: book block line 311 (tm240 libpattern nr n7, 40/80, 11,058 events, both sides).
- L9c2622b0.BRP45: lines 492-508 (pnf_7, VWAP-line break n 3 k 0.5, 45/45, 5,845 events, both sides, trigger verified 5,845/5,845).
- L4aaacdb2.BRP30: lines 511-530 (vsess_30 _CANC, session-VWAP band break minbars 20 k 1.0, 30/30, 1,485 events, both sides, verified 1,485/1,485).

## 8. What the relay must code / parity pending
Code option A (J502 + BF2_JT6 layers); option B only if Josh picks it. Parity pending: the 20261110 TRADES block for L9c2622b0 and L4aaacdb2 was OPEN at last read (engine month not landed); layer parity pack for the relay (listed "to follow" in the 16:15Z line). Not verified here: whether those parity blocks have since filled.

## 9. Not in the files / to follow
Per-book fitted layer values beyond the keys pages; the 2-lot numbers for the stay final; a W-EXITENG stage-2 PASS/FAIL line.
