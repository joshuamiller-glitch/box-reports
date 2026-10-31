# DS3_CONFIRM_2 - CONFIRMATION, SECOND PASS (PLAN36 section 2), agent C2, written 2026-10-31
Prereg l2vast/ds3/prereg/CF2_prereg.md sha256 393f94ed3168f84f0ea93729e60fa1bce0099a1cfc923e2e02e66e49f8ac4af4 (DECISIONS.md, before any scored cell); selection files hashed in DECISIONS.md before each look (G1 705d17f6, G2 765033e7, G3 26d42c7d, G4 fc16108a, G5 ad107e1f, carried specs 37695b34). Code l2vast/ds3/code/confirm2/, outputs l2vast/ds3/out/confirm2/. cf_engine imported, not forked (own kernel c2_dip for the "pattern after the dip" mechanic, validated to reproduce cf_engine mech a to 0.0). Masks own, capped 20260206, UNTOUCHED never read (the 1-s book table was filtered to ts <= 2026-02-06 and only files up to 2026-02 were opened).

## Page 1 - the verdict
1. Result: 0 PASS. One family is real enough to run on paper, and it is one book: the **PE 45-s three-bar** (two down 45-s candles, then an up candle closing above the previous high; short mirrored), entered as a **limit at the body mid of the confirming candle, pure wait (the 70/30 split is dropped; no confirmation = no trade)**. Tier **LEAD** (not CANDIDATE-RECENT-PASS): per planned lot vs the plain 70/30 3-pt dip floor +2.42 L6M (MDE 3.2, inside MDE), +2.14 HOLD, +3.08 L3M, +0.97 PRE, +0.75 X'; time-matched random-timing placebo rank 1 of 201 in L6M and HOLD (and 2 in PRE); positive on the M and LIVE-P9 bases (+3.07 / +3.28 L6M); survives a 3-s decision delay (+2.56) and a +1-tick limit stress (+2.23); per contract of final position +4.64 vs +0.80 for the floor. It FAILS the multiplicity gate (White RC p 0.74 over the 2,820 catalogue cells on PRE+X' for PE; cumulative Sidak p 1.0), its lock-engine stack is mixed (+1.5k L6M, +0.65k HOLD, -1.4k PRE, +2.4k X' $/wk), the gain sits in NY-AM / NY-PM (+5.0 / +4.3 L6M; London PRE +4.2, Asia PRE -2.0; pre-market and Asia are negative), and the premise "positive in all windows" is **post-hoc** (found after looking at L6M / HOLD / L3M). The honest forward-facing check, the walk-forward re-selection chain over the catalogue, ends on exactly this cell for PE (anchored) and earns +0.36 pts per planned lot out of sample over 2024-02..2026-02 (+0.74 L6M, +0.89 HOLD, MDE 1.5; beats a random-cell chain with p = 0.09). That is a LEAD, not a rule.
2. Every other book regresses: the cells selected on PRE+X' average +0.5..+1.3 in PRE/X' and -0.5..-3.0 in L6M/HOLD for HM, SM, ST, MA, PB, MV, DN, WT (MV/DN/WT about 0 to -0.4). KB: PRE +0.65, X' +0.84, L6M +0.47, HOLD +0.48 on average over the 12 selected cells, but none beats its placebo draws AND keeps a positive stack (KB 15-s NR4 breakout limit: +0.80 L6M, placebo rank 44/201, stack -3.4k L6M: DEAD on structure + stack). Walk-forward re-selection chains over the catalogue: no anchored chain reaches the 95th percentile of a random-cell chain; 6 of 10 sit below the random-cell mean; only PE (+0.36) is positive (rolling WT +0.28, p 0.01 vs random chain, but -0.49 in L6M) (table below). Adding the conditioned cells (pool P2, 9,952 cells) makes the chain no better.
3. The information combinations add nothing: requiring the pattern to print AT a level (session extreme, prior-day mid, 1-h kijun, x50/x100, VWAP, band) lowers the PRE+X' delta by -0.24 (any level) to -0.86 (prior-day mid) vs the same pattern anywhere (7% - 28% of conditioned cells above the unconditioned one); book state in the same second (imbalance, absorption, delta turn) lowers it by -0.30 to -0.82 (the pattern bar's own delta in favour: -0.16); ER(20) 5-min >= 0.2 lowers it by -0.09, >= 0.3 by -0.32, >= 0.4 by -0.58. In the recent windows the real gain over "anywhere" is no better than the permuted-flag placebo (G2 -0.57 vs -0.54; G3 -0.32 vs -0.36). The one exception is KB x ER >= 0.2 (+0.5 .. +0.7 over anywhere in HOLD/L6M vs +0.15..0.25 placebo, PRE +0.09, X' +0.94, consistent with the TG-1 chop-filter lead); it is a regime tool, not a pattern.
4. Mechanics (f): averaged over the whole catalogue every wait mechanic is below the floor (70/30 base: market at the print -0.11, limit at body mid -0.08, at bar open -0.04, at extreme -0.05, dip AND pattern -0.11 / -0.10 / -0.20, d filter -0.77; pure-wait base -0.27 .. -0.89). Limit at the bar open / extreme is the least bad on average; for the PE three-bar on PRE+X' (selection data) body mid +0.92, bar open +0.88, extreme +0.86, market at the print +0.75, dip AND pattern +0.82, pattern as a filter -0.39; recent look (selected cells only): body mid +2.42 L6M, extreme +1.40, bar open +1.1. Pattern AFTER a pullback from the running extreme (G5) lifts PE to +2.96 L6M (X=5 pts, rank 1/201) but PRE +0.75 and X' -0.24 and the PRE stack -5.5k: refinement of the same effect, not a separate edge.
5. Latency (i): the PE cells are unchanged at 1 s and 3 s (+2.66 / +2.56); HM 15-s momentum dies at 3 s (+1.06 -> +0.07); KB 30-s engulf dies at 3 s (+0.59 -> -0.18). Sub-minute rules that need the first 1-3 s are fragile; the PE three-bar limit rests, so it is not.
6. Floor: not moved except possibly PE. Multiplicity: this agent scored 9,952 cells (G1 2,820, G2 2,368, G3 2,256, G4 1,824, G5 684; plus 80 chain settings); cumulative N = 143,584 + 9,952 + earlier cells.

## Units, bases, what the numbers mean
* Primary = pts per PLANNED lot over ALL the book's signals, paired vs the plain 70/30 3-pt dip split on the same trades (skipped / unfilled pure-wait signals earn 0, i.e. they lose their floor P&L: this is the strict, economically honest delta). Per contract of final position = sum of net pts / sum of lots actually on (cell and floor beside each other). Week-clustered SE; MDE = 2.8 SE.
* Bases from one run (identity validated against an engine run on basis M, max error 1e-14): N = no target-fill correction (selection basis), M = measured (target correction 1.4 / 1.5 / 4.2 / 4.3 pt by year), LIVE-P9 = M with every stop-class exit at 2.45 instead of 1.01. LIVE-CAL is not available. The directive's "three bases" are read as the bar bases tc (time candles) / ha (Heikin-Ashi, levels from the real candle) / hagen (generic candle rules on the HA candle) AND the three cost bases N / M / LIVE-P9.
* Dollars: "lock-engine stack $/wk" = cf_engine.stack_line with the cell replacing one engine book (ST HM WT KB SM PE only) and all other books at the floor, at the engine's research lots (ST10 HM10 WT7 KB5.2 SM7.4 PE5.6): the number to use. "$/wk at live lots (per-signal arithmetic)" = d x $20 x live lots x signals/week assumes every signal is traded independently; the lock engine (caps, locks, one book blocking another) turns +10k into +1.5k for PE, so the per-signal figure overstates and is shown only to size the arithmetic. Live lots used: PE 5, KB 3, HM 1 (from your 11:40 ET example); SM, MV, DN, ST, WT are shown per 1 live lot (question in MORNING.md).
* STRUCTURE note: all pure-wait cells and every limit at a fixed offset are partly the structure of the split / resting limit; the time-matched random-timing placebo (same calendar day, same direction, same level offsets from price) is the control for that. The PE three-bar clears it (rank 1 of 201 in L6M and HOLD); a random draw earns +0.74 mean (L6M), so about 30% of the +2.4 is structure and the rest is the pattern timing.
* Not computed (flagged): capacity (depth at fills), top-5%-of-trades share, parameter-surface neighbours, vol-tercile regime split, queue-position model for the resting limit (a body-mid limit after a reversal candle may sit behind the queue; fills are scored at touch on the measured basis, +1-tick stress shown), 200-draw placebos only for the 18 headline cells (5 draws for the rest).

## G1 - the catalogue (a, f, g): 141 specs x 20 cells
Specs: tc 15/30/45 s x 35 rules (reversal: engulf, hammer, pin 50/66, two-bar, three-bar, strict three-bar, morning star, tweezer, key reversal, 5-bar sweep, inside-bar break, doji break, outside bar; continuation: 2/3/4/5 consecutive closes, thrust, marubozu, higher-low break, 2-bar flag, pullback-resume; bar range vs the median of the prior 20 bars: 1.5x, 2x, 3x, NR4 break, big-close; close location: top 10%, top 25% on a wide bar, top-quarter break; wick ratios: rejection, no lower wick, lower wick >= 2x body, no wick) + HA 15/30/45 s x 8 + hagen x 4 = 141 specs; mechanics a / b near,mid,far / c1 X3,5,8 / c2 mid,near / d on A70 and W0 = 20 cells each = 2,820 cells x 10 books x (ALL + 5 sessions). Averages of the PRE+X' delta vs the floor (pooled over books; PE and KB in the table at the end of this section):

Catalogue averages (PRE+X' delta vs floor per planned lot, cells with pre fill >= 10%, mean over cells; "all" = 10 books pooled):
| mechanic | all A70 | all W0 | PE A70 | PE W0 | KB A70 | KB W0 |
|---|---|---|---|---|---|---|
| a market at print | -0.11 | -0.27 | -0.30 | -0.16 | -0.07 | -0.25 |
| b limit body mid | -0.08 | -0.42 | -0.16 | -0.10 | -0.10 | -0.42 |
| b limit bar open | -0.04 | -0.36 | -0.07 | 0.00 | -0.09 | -0.49 |
| b limit extreme | -0.05 | -0.42 | -0.05 | -0.02 | -0.09 | -0.53 |
| c1 dip 3 AND pattern | -0.11 | -0.39 | -0.13 | 0.00 | -0.06 | -0.32 |
| c1 dip 8 AND pattern | -0.20 | -0.71 | -0.10 | -0.31 | -0.14 | -0.77 |
| c2 limit open after dip | -0.11 | -0.56 | -0.11 | -0.14 | -0.08 | -0.59 |
| d pattern in favour at signal (filter) | -0.77 | -0.89 | -0.32 | -0.30 | -0.73 | -0.74 |
By timeframe (all A70 / W0): 15 s -0.15 / -0.46, 30 s -0.18 / -0.54, 45 s -0.18 / -0.55 (PE W0: -0.09 / -0.18 / -0.16). By family (all W0): HA -0.42, R -0.53, C -0.56, CL -0.52, RM -0.48, WK -0.58; PE rule ranking (mean over its 20 cells): R_three +0.09, R_three_strict +0.08, HA_flip +0.08, HA_three +0.06, HA_flip3 +0.04, HA_two +0.03 ... RM_wide3 -0.59, C_mom5 -0.45, R_pin66 -0.42; KB: HA_two +0.09, HA_flip +0.06, C_mom2 +0.04, RM_nr4 +0.04. Only 28% of the 2,820 x 10 pooled (cell, book) pairs are above the floor in PRE+X'. White RC on PRE+X' weekly deltas (G1 pool, per book): PE p 0.74, KB 0.80, SM 0.72, HM 1.00, MV 0.60, DN 0.96, ST 0.89, WT 0.61, PB 0.51, MA 0.85; Romano-Wolf survivors 0 in every book; cumulative Sidak p 1.0 (N_cum 158,464); DSR of the best cell 0.00 - 0.47; PBO 0.21 - 0.75; minimum backtest length 12.5 years. The same RC computed on L6M+HOLD for information (the cells ARE the same, not a selection): PE p 0.12 (2 RW survivors, tc 30s morning-star limit), KB 0.28 (1), all other books >= 0.5.

Selected cells (PRE+X' top 12 per book ALL, top 3 per book-session, top 12 pooled = 192 cells, 231 book-session triples; ONE recent look) - mean delta vs floor over the selected ALL-session cells by window (per planned lot):
| book | PRE | X' | L6M | HOLD | 2026 | L3M | share of selected cells >= 0 in both L6M and HOLD |
|---|---|---|---|---|---|---|---|
| PE | +1.14 | +0.10 | +1.53 | +1.54 | +2.40 | +1.98 | 100% |
| KB | +0.65 | +0.84 | +0.47 | +0.48 | +1.10 | +2.25 | 83% |
| MV | +0.59 | +1.96 | -0.24 | -0.14 | -1.12 | -0.26 | 58% |
| DN | +0.54 | +0.59 | -0.45 | -0.38 | +1.06 | +0.42 | 42% |
| WT | +0.36 | +1.12 | -0.60 | -0.30 | -1.11 | -0.68 | 0% |
| HM | +0.19 | +0.62 | -1.22 | -0.82 | -1.11 | -0.60 | 8% |
| SM | +0.68 | +2.25 | -2.11 | -2.49 | -6.63 | -1.17 | 8% |
| ST | +0.61 | +0.82 | -1.85 | -1.54 | -5.85 | -2.23 | 0% |
| PB | +1.33 | +1.23 | -2.68 | -1.98 | -2.97 | -3.34 | 0% |
| MA | +1.15 | +1.02 | -2.99 | -2.53 | -3.91 | -4.83 | 0% |
Tiers of the 231 selected triples (5-draw random-timing placebo + permuted rules): LEAD 13, CANDIDATE-RECENT 4, BEST-AVAILABLE-NEGATIVE 171, DEAD (placebo / per-contract) 43. All 13 LEADs are PE (3), MV (3), SM (1) plus session triples; full rows in out/confirm2/tier_G1.csv (columns: windows, MDE, per-contract, M, LIVE-P9, placebo max, delay 1 s / 3 s, +1 tick, shifted-day).

## Sunday table - head-to-head cells (200 random-timing draws for these; windows on basis N unless marked)
Rows are (i) the walk-forward last re-fit for each book (anchored chain, G8 below: "the pattern you would run Sunday") and (ii) the best cells found in G1/G5 for PE, KB, SM, DN. Tier rule: LEAD = placebo rank <= 10 of 201 in L6M and HOLD, delta >= 0 in L6M, HOLD, PRE, X', M and LIVE-P9 >= 0, 3-s delay >= 0; CANDIDATE-RECENT = >= 0 in L6M and HOLD with PRE+X' > 0 but failing another gate; else BEST-AVAILABLE-NEGATIVE. No row is a PASS (multiplicity).
| book | pattern | mechanic | base | per planned lot vs floor: L3M / L6M [MDE] / HOLD / PRE / X' | M / LIVE-P9 L6M | per contract L6M (cell / floor) | fired per wk (of signals) | random-timing placebo rank L6M / HOLD / PRE (of 201) | lock-engine stack $/wk L6M / HOLD / PRE / X' | 3-s delay L6M | +1 tick L6M | $/wk at live lots (per-signal arithmetic, NOT the stack) | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| DN | hagen 30s C_mom2 | a near | 70/30 | +1.61 / +1.13 [1.4] / +1.14 / +0.42 / +0.39 | +1.11 / +1.13 | +6.69 / +5.48 | 22.6 (25.0) | 4 / 3 / 17 | n/a (not a lock-engine book) | +0.73 |  | +564 x1 lots | LEAD |
| DN | tc 45s R_three | b near | 70/30 | +0.51 / +0.41 [1.8] / +0.36 / +0.52 / +0.61 | +0.55 / +0.57 | +6.20 / +5.48 | 16.7 (25.0) | 17 / 38 / 5 | n/a (not a lock-engine book) | +0.28 | +0.34 | +208 x1 lots | CANDIDATE-RECENT |
| HM | tc 15s C_mom4 | c1 near X3 | pure wait | +1.81 / +1.06 [3.5] / +1.37 / -0.15 / +0.87 | +1.44 / +1.59 | +6.74 / +4.32 | 25.9 (32.5) | 3 / 2 / 28 | +12297 / +9862 / -1445 / +2338 | +0.07 |  | +688 x1 lots | CANDIDATE-RECENT |
| KB | tc 15s RM_nr4 | b near | pure wait | +2.11 / +0.80 [2.2] / +1.09 / +0.46 / +1.85 | +1.25 / +1.36 | +2.64 / +1.34 | 36.2 (44.9) | 44 / 27 / 5 | -3387 / -1956 / +700 / +5276 | +0.54 | +0.61 | +2152 x3 lots | CANDIDATE-RECENT |
| KB | tc 30s R_engulf | b near | pure wait | +2.02 / +0.59 [3.0] / +0.54 / +0.88 / +0.52 | +1.16 / +1.32 | +2.60 / +1.34 | 33.2 (44.9) | 75 / 92 / 1 | -2935 / -3830 / +28 / -1466 | -0.18 | +0.41 | +1581 x3 lots | CANDIDATE-RECENT |
| KB | tc 45s R_three | b near | 70/30 | +0.49 / -0.06 [1.7] / +0.06 / -0.11 / -0.25 | +0.16 / +0.21 | +1.40 / +1.34 | 26.5 (44.9) | 144 / 114 / 61 | -3370 / -3058 / -2866 / -528 | -0.00 | -0.14 | -169 x3 lots | BEST-AVAILABLE-NEGATIVE |
| KB | tc 15s C_mom3 | b near | pure wait | +1.30 / -0.99 [3.8] / -0.86 / +1.17 / +0.37 | -0.47 / -0.36 | +0.44 / +1.34 | 35.5 (44.9) | 194 / 194 / 2 | -8709 / -8894 / +4568 / -1114 | -0.82 | -1.13 | -2663 x3 lots | BEST-AVAILABLE-NEGATIVE |
| MV | tc 45s R_three_strict | a near | pure wait | +1.02 / +0.56 [4.1] / +0.82 / +0.60 / +1.64 | +1.13 / +1.33 | +3.85 / +2.28 | 29.9 (40.4) | 20 / 16 / 2 | n/a (not a lock-engine book) | +0.79 |  | +450 x1 lots | CANDIDATE-RECENT |
| PE | tc 45s R_three | dv1 near X5 | pure wait | +5.08 / +2.96 [3.4] / +2.55 / +0.75 / -0.24 | +3.54 / +3.78 | +5.36 / +0.80 | 30.0 (42.6) | 1 / 1 / 4 | +2592 / +1950 / -5500 / +1815 | +2.15 |  | +12638 x5 lots | CANDIDATE-RECENT |
| PE | tc 45s R_three_strict | dv1 near X5 | pure wait | +4.87 / +2.80 [3.3] / +2.19 / +0.81 / -0.41 | +3.40 / +3.65 | +5.19 / +0.80 | 29.6 (42.6) | 2 / 2 / 2 | +1715 / -140 / -5083 / +2338 | +2.18 |  | +11940 x5 lots | CANDIDATE-RECENT |
| PE | tc 45s R_three_strict | b near | pure wait | +3.01 / +2.63 [3.0] / +2.20 / +1.10 / +0.03 | +3.29 / +3.52 | +5.02 / +0.80 | 29.1 (42.6) | 4 / 7 / 1 | +3146 / +1780 / -620 / +2066 | +2.69 | +2.43 | +11211 x5 lots | LEAD |
| PE | tc 45s R_three | b near | pure wait | +3.08 / +2.42 [3.2] / +2.14 / +0.97 / +0.75 | +3.07 / +3.28 | +4.64 / +0.80 | 29.6 (42.6) | 1 / 1 / 2 | +1515 / +653 / -1379 / +2414 | +2.56 | +2.23 | +10339 x5 lots | LEAD |
| PE | tc 45s R_three | b far | pure wait | +1.38 / +1.40 [2.6] / +1.68 / +1.16 / -0.04 | +2.27 / +2.49 | +3.48 / +0.80 | 27.0 (42.6) | 48 / 17 / 2 | +1241 / +2528 / -5265 / +593 | +1.42 | +1.16 | +5980 x5 lots | CANDIDATE-RECENT |
| PE | tc 45s R_three | b near | 70/30 | +0.18 / +0.04 [1.4] / -0.12 / +0.06 / +0.32 | +0.19 / +0.20 | +0.88 / +0.80 | 29.6 (42.6) | 78 / 85 / 27 | +290 / -1061 / -2204 / +1231 | +0.26 | +0.01 | +177 x5 lots | BEST-AVAILABLE-NEGATIVE |
| SM | tc 45s R_three | b near | pure wait | +1.28 / +1.44 [6.1] / +0.79 / +0.28 / +2.55 | +2.10 / +2.28 | +6.47 / +3.23 | 8.4 (11.6) | 1 / 1 / 17 | +2443 / +813 / +214 / +4079 | +0.80 | +1.44 | +334 x1 lots | LEAD |
| SM | ha 30s HA_dojiflip | b near | pure wait | +3.30 / -0.39 [7.0] / -1.12 / +1.26 / +3.00 | +0.24 / +0.40 | +3.80 / +3.23 | 8.7 (11.6) | 12 / 13 / 2 | -803 / -2599 / +1086 / +4397 | -1.42 | -0.39 | -90 x1 lots | BEST-AVAILABLE-NEGATIVE |
| ST | ha 45s HA_strong | b mid | pure wait | -1.14 / -1.17 [2.6] / -1.04 / +0.32 / +2.16 | -0.33 / -0.06 | +5.24 / +4.35 | 27.3 (44.9) | 14 / 26 / 21 | -9138 / -7454 / -8333 / +3403 | -1.58 | -1.36 | -1051 x1 lots | BEST-AVAILABLE-NEGATIVE |
| WT | tc 45s C_mom4 | b far | pure wait | -0.62 / -0.05 [1.5] / +0.22 / +0.27 / +1.37 | +1.14 / +1.41 | +3.46 / +1.88 | 32.0 (60.9) | 13 / 21 / 10 | +701 / +350 / +575 / +7688 | -0.23 | -0.32 | -60 x1 lots | BEST-AVAILABLE-NEGATIVE |
Plain sentences for the Sunday rows:
* PE: waiting for the 45-s three-bar after the PE signal and resting the whole lot as a limit at the body mid of that candle (no 70/30 split, no confirmation = no trade) adds +2.42 pts per planned lot in the last 6 months (MDE 3.2, so inside the MDE; L3M +3.08, HOLD +2.14, PRE +0.97, X' +0.75; +4.64 per contract vs +0.80), fires on 29.6 of 42.6 signals per week, beats 200 time-matched random-timing draws (rank 1 of 201 in L6M and HOLD), holds on LIVE-P9 (+3.28), a 3-s delay (+2.56) and a +1-tick stress (+2.23); the lock-engine stack is +1.5k $/wk L6M, +0.65k HOLD, -1.4k PRE, +2.4k X'; tier LEAD (fails multiplicity, post-hoc premise).
* DN: adding the 30% on the 2nd-candle-up of the HA 30-s series instead of the 3-pt dip (hagen C_mom2, market) adds +1.13 L6M (MDE 1.4), +1.14 HOLD, +0.42 PRE, +0.39 X', +1.61 L3M, rank 4 / 3 of 201, positive in all five sessions in L6M; tier LEAD; it is also DN's last walk-forward re-fit, but the anchored DN chain earned -1.32 out of sample (the chain used different picks earlier), so one cell is not a stable selection.
* HM: pure wait for four consecutive 15-s up closes after a 3-pt dip (hagen/tc C_mom4 c1) adds +1.06 L6M and +1.37 HOLD with a +12.3k / +9.9k $/wk stack at 1 live lot HM, but PRE -0.15, PRE stack -1.4k, and the effect is gone at a 3-s delay (+0.07): CANDIDATE-RECENT, shadow only if the NT8 side can act inside 1 s.
* KB: nothing: the PRE+X' winners (15-s momentum, NR4 break, engulf) earn +0.6..+0.8 L6M but their stack is -3.4k / -2.9k $/wk, 44 - 75 of 201 placebo rank; DEAD on structure + stack.
* SM / MV: the 45-s three-bar is the same family (SM +1.44 L6M MDE 6.1, rank 1 / 1, 8 fired per week; MV strict three-bar market +0.56 MDE 4.1, rank 20 / 16): MDE is 4-6x the effect; SHADOW at most.
* ST, WT, PB, MA: the catalogue has nothing; keep the plain split.

## G8 - walk-forward re-selection chain (directive h): the last re-fit is the pattern to run
Quarterly re-fits 2024-02-01 .. 2026-02-01 (nine test blocks, train = X' alone for the first, anchored or rolling 12 months afterwards, one-day embargo, selection score = mean delta vs the floor on trades entered before the re-fit, pre fill >= 10%, n >= 100), final re-fit at the cap 2026-02-06 on everything. OOS = the concatenated test blocks. "random-cell chain" = 1,000 draws that pick a random eligible cell at each re-fit. P1 = the 2,820 G1 cells; P2 = P1 + the 7,132 conditioned / dip cells. Note the final re-fit uses the recent windows by construction; the earlier blocks are honest OOS. The L6M / HOLD / L3M columns are test-block deltas, not selection looks.

| pool | book | re-fit rule | OOS d vs floor (2024-02..2026-02) [MDE] | PRE-part | HOLD | L6M | L3M | M basis OOS | random-cell chain mean / p95 | p(real<=random) | per contract L6M (chain / floor) | LAST RE-FIT (Sunday pattern) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P1 | PE | anchored | +0.36 [1.5] | +0.14 | +0.89 | +0.74 | +0.70 | +0.81 | -0.09 / +0.46 | 0.09 | +2.19 / +0.80 | tc|45s|R_three|b|near|3|W0 |
| P1 | PE | rolling | -0.36 [1.6] | -0.92 | +0.96 | +1.19 | +1.19 | +0.09 | -0.08 / +0.45 | 0.78 | +2.92 / +0.80 | tc|45s|RM_bigclose|b|mid|3|W0 |
| P1 | KB | anchored | -0.51 [1.5] | -0.54 | -0.44 | -0.53 | +2.11 | -0.12 | -0.25 / +0.37 | 0.75 | +1.01 / +1.34 | tc|15s|RM_nr4|b|near|3|W0 |
| P1 | KB | rolling | -0.90 [1.8] | -0.95 | -0.78 | -0.90 | +1.59 | -0.55 | -0.24 / +0.36 | 0.96 | +0.54 / +1.34 | tc|30s|C_mom3|c1|near|8|W0 |
| P1 | SM | anchored | -0.79 [3.0] | -0.66 | -1.12 | -0.39 | +3.30 | -0.35 | -1.17 / -0.07 | 0.32 | +3.80 / +3.23 | ha|30s|HA_dojiflip|b|near|3|W0 |
| P1 | SM | rolling | -1.65 [2.8] | -0.70 | -4.00 | -3.72 | -2.37 | -1.14 | -1.18 / -0.05 | 0.74 | -0.62 / +3.23 | hagen|45s|CL_top25w|d|near|3|W0 |
| P1 | HM | anchored | -1.41 [1.9] | -1.23 | -1.83 | -1.94 | -1.53 | -1.03 | -0.78 / -0.14 | 0.92 | +3.15 / +4.32 | tc|15s|C_mom4|c1|near|3|W0 |
| P1 | HM | rolling | -0.98 [1.8] | -1.15 | -0.60 | -0.93 | -1.53 | -0.49 | -0.78 / -0.14 | 0.69 | +4.29 / +4.32 | tc|15s|C_mom4|c1|near|3|W0 |
| P1 | MV | anchored | -0.32 [1.8] | -0.26 | -0.46 | -0.65 | -1.16 | +0.19 | -0.46 / +0.11 | 0.35 | +2.40 / +2.28 | tc|45s|R_three_strict|a|near|3|W0 |
| P1 | MV | rolling | -0.86 [1.8] | -0.85 | -0.90 | -1.14 | -0.67 | -0.44 | -0.46 / +0.10 | 0.88 | +1.59 / +2.28 | hagen|30s|C_mom3|c1|near|3|W0 |
| P1 | DN | anchored | -1.32 [1.6] | -1.20 | -1.60 | -2.05 | -0.75 | -1.00 | -1.12 / -0.24 | 0.64 | +3.89 / +5.48 | hagen|30s|C_mom2|a|near|3|A70 |
| P1 | DN | rolling | -0.27 [1.4] | -0.05 | -0.78 | -0.90 | -1.60 | +0.05 | -1.12 / -0.24 | 0.06 | +5.75 / +5.48 | tc|15s|R_keyrev|b|near|3|A70 |
| P1 | ST | anchored | -1.05 [1.9] | -0.24 | -2.83 | -3.38 | -3.43 | -0.41 | -0.76 / -0.17 | 0.80 | +1.48 / +4.35 | ha|45s|HA_strong|b|mid|3|W0 |
| P1 | ST | rolling | -0.70 [1.5] | -0.45 | -1.26 | -1.54 | -1.96 | -0.08 | -0.76 / -0.18 | 0.45 | +4.64 / +4.35 | ha|30s|HA_nolow3|b|mid|3|W0 |
| P1 | WT | anchored | +0.00 [1.1] | +0.11 | -0.24 | -0.53 | -0.62 | +0.89 | -0.16 / +0.18 | 0.21 | +2.64 / +1.88 | tc|45s|C_mom4|b|far|3|W0 |
| P1 | WT | rolling | +0.28 [1.1] | +0.53 | -0.29 | -0.49 | -0.52 | +1.07 | -0.16 / +0.17 | 0.01 | +2.39 / +1.88 | tc|15s|R_tworev|b|near|3|W0 |
| P1 | PB | anchored | -0.40 [2.0] | -0.05 | -1.21 | -1.96 | -3.36 | +0.32 | -0.21 / +0.51 | 0.67 | +9.70 / +7.56 | tc|45s|C_thrust|c1|near|3|W0 |
| P1 | PB | rolling | +0.37 [2.1] | +1.07 | -1.28 | -2.31 | -2.06 | +0.95 | -0.21 / +0.48 | 0.09 | +7.56 / +7.56 | hagen|45s|C_mom3|a|near|3|W0 |
| P1 | MA | anchored | -1.85 [2.8] | -1.33 | -3.04 | -3.33 | -4.13 | -1.44 | -0.99 / +0.04 | 0.90 | +3.39 / +6.20 | hagen|15s|RM_wide2|a|near|3|W0 |
| P1 | MA | rolling | -1.28 [2.8] | -0.95 | -2.03 | -2.84 | -3.14 | -0.76 | -0.99 / +0.04 | 0.67 | +4.38 / +6.20 | tc|15s|WK_lw2|b|mid|3|W0 |

| pool | book | re-fit rule | OOS d vs floor (2024-02..2026-02) [MDE] | PRE-part | HOLD | L6M | L3M | M basis OOS | random-cell chain mean / p95 | p(real<=random) | per contract L6M (chain / floor) | LAST RE-FIT (Sunday pattern) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P2 | PE | anchored | +0.40 [1.3] | +0.44 | +0.31 | +0.11 | -0.38 | +0.86 | -0.16 / +0.43 | 0.06 | +1.31 / +0.80 | tc|45s|R_three|b|near|3|W0 |
| P2 | PE | rolling | +0.25 [1.7] | -0.06 | +0.96 | +1.19 | +1.19 | +0.83 | -0.16 / +0.47 | 0.13 | +2.92 / +0.80 | tc|45s|RM_bigclose|b|mid|3|W0 |
| P2 | KB | anchored | -0.51 [1.7] | -1.27 | +1.20 | +1.26 | +2.75 | +0.01 | -0.45 / +0.24 | 0.57 | +3.47 / +1.34 | tc|15s|RM_nr4@BK_barD|b|near|3|W0 |
| P2 | KB | rolling | -0.73 [1.9] | -1.51 | +1.03 | +1.07 | +2.43 | -0.29 | -0.47 / +0.20 | 0.74 | +3.20 / +1.34 | tc|30s|C_mom3|dv1|near|3|W0 |
| P2 | SM | anchored | -1.53 [3.5] | -0.14 | -5.01 | -4.74 | -4.68 | -1.11 | -1.57 / -0.33 | 0.48 | -2.06 / +3.23 | ha|30s|HA_dojiflip|b|near|3|W0 |
| P2 | SM | rolling | -2.33 [3.5] | -1.73 | -3.81 | -3.35 | -2.37 | -1.80 | -1.58 / -0.38 | 0.83 | -0.16 / +3.23 | hagen|45s|CL_top25w|d|near|3|W0 |
| P2 | HM | anchored | -1.79 [2.0] | -1.63 | -2.17 | -2.54 | -1.53 | -1.42 | -0.97 / -0.28 | 0.96 | +2.28 / +4.32 | tc|15s|C_thrust|dv1|near|3|W0 |
| P2 | HM | rolling | -0.42 [1.7] | -0.35 | -0.56 | -0.93 | -1.53 | +0.04 | -0.98 / -0.27 | 0.10 | +4.29 / +4.32 | tc|15s|C_mom4|c1|near|3|W0 |
| P2 | MV | anchored | -1.02 [1.9] | -1.01 | -1.07 | -1.32 | -1.62 | -0.34 | -0.65 / -0.07 | 0.83 | +1.61 / +2.28 | tc|30s|C_mom3@ER_fade|b|near|3|W0 |
| P2 | MV | rolling | -1.46 [1.8] | -1.61 | -1.10 | -1.36 | -1.27 | -0.71 | -0.63 / -0.01 | 0.98 | +1.69 / +2.28 | tc|30s|CL_topbrk@LV_r100|c1|near|3|W0 |
| P2 | DN | anchored | -1.54 [2.0] | -1.67 | -1.24 | -1.64 | -0.07 | -1.17 | -1.24 / -0.28 | 0.70 | +4.67 / +5.48 | tc|15s|RM_nr4@ER_lt20|b|near|3|A70 |
| P2 | DN | rolling | -1.19 [2.0] | -1.40 | -0.72 | -0.83 | -1.48 | -0.84 | -1.23 / -0.27 | 0.50 | +5.82 / +5.48 | tc|15s|RM_nr4@ER_lt20|b|near|3|A70 |
| P2 | ST | anchored | -0.95 [2.0] | -0.58 | -1.76 | -2.21 | -2.19 | -0.31 | -0.94 / -0.34 | 0.52 | +2.96 / +4.35 | tc|15s|RM_nr4@ER_ge20|b|near|3|W0 |
| P2 | ST | rolling | -1.78 [1.9] | -1.94 | -1.43 | -1.54 | -1.96 | -0.95 | -0.93 / -0.32 | 0.98 | +4.64 / +4.35 | ha|30s|HA_nolow3|b|mid|3|W0 |
| P2 | WT | anchored | -0.13 [1.1] | -0.01 | -0.38 | -0.69 | -0.62 | +0.82 | -0.22 / +0.13 | 0.35 | +2.75 / +1.88 | tc|45s|C_mom4|b|far|3|W0 |
| P2 | WT | rolling | +0.31 [1.1] | +0.40 | +0.11 | -0.04 | +0.35 | +1.17 | -0.23 / +0.12 | 0.00 | +3.56 / +1.88 | hagen|45s|C_mom2|dv1|near|3|W0 |
| P2 | PB | anchored | -0.55 [2.1] | +0.05 | -1.95 | -2.81 | -3.91 | +0.10 | -0.48 / +0.29 | 0.58 | +7.85 / +7.56 | tc|30s|C_mom3@ER_fade|c2|mid|3|W0 |
| P2 | PB | rolling | +0.10 [2.4] | +0.35 | -0.47 | -0.47 | -0.16 | +0.74 | -0.46 / +0.32 | 0.13 | +10.37 / +7.56 | hagen|45s|C_mom3|a|near|3|W0 |
| P2 | MA | anchored | -0.82 [3.2] | +0.34 | -3.48 | -4.29 | -5.24 | -0.56 | -1.38 / -0.18 | 0.24 | +2.17 / +6.20 | hagen|15s|RM_wide2|dv1|near|3|W0 |
| P2 | MA | rolling | -3.30 [2.8] | -2.22 | -5.78 | -6.96 | -9.98 | -2.79 | -1.34 / -0.17 | 0.99 | -1.12 / +6.20 | tc|15s|WK_lw2|b|mid|3|W0 |

Reading: the chain is the forward-facing answer, and it is a null. Out of sample (2024-02 .. 2026-02, MDE 1.1 - 3.5) only PE is positive (+0.36 anchored with p 0.09 against a random-cell chain; the chain converges on the 45-s three-bar), WT rolling is +0.28 (p 0.01 vs random but -0.49 in L6M); every other book's chain is at or below the random-cell chain. Session-specific chains (asia / london / nyam / nypm separately) are in wf_P1_stats.csv (sessmode = sess) and were no better. In the P1 table "PRE-part" is the part of the PRE window that lies after the first re-fit.

## G2 / G3 / G4 - conditioning the pattern (directive b, c, d): the "information combination"
Carried specs: the 5 best specs per book on PRE+X' (38 specs; carried.json). Each spec restricted to events where the condition holds, 4 mechanics x 2 bases, N basis; comparison = the same spec anywhere (G1 cell) on PRE+X' (all conditioned cells, ALL sessions) and, on the selected cells in the single recent look, against 5 permuted-flag draws (same number of flagged events per day).
| condition | cells | mean PRE+X' change vs "anywhere" (per planned lot) | share of cells that improve |
|---|---|---|---|
| at session low/high (2 ticks) | 2,400 | -0.82 | 5.5% |
| at prior-day mid | 3,040 | -0.86 | 5.2% |
| at 1-h kijun | 3,040 | -0.81 | 7.6% |
| at x50 / x100 | 3,040 | -0.52 / -0.53 | 18% / 17% |
| at VWAP / VWAP band | 3,040 | -0.71 / -0.32 | 7.8% / 23% |
| any of the seven levels | 3,040 | -0.24 | 28% |
| imbalance in favour >= 0.3 / >= 0.5 (second before the bar's last print) | 3,040 | -0.60 / -0.76 | 13% / 7.5% |
| imbalance turn (against then in favour) | 3,040 | -0.66 | 10% |
| absorption 150 / 300 | 3,040 / 1,280 | -0.73 / -0.82 | 7.3% / 5.8% |
| 10-s delta turn | 3,040 | -0.30 | 26% |
| pattern bar's own delta in favour (abs(delta)/vol >= 0.2) | 3,040 | -0.16 | 34% |
| imbalance AGAINST >= 0.3 (negative control) | 3,040 | -0.52 | 17.5% |
| ER(20) 5-m >= 0.2 / 0.3 / 0.4 | 3,040 each | -0.09 / -0.32 / -0.58 | 43% / 26% / 14% |
| ER < 0.2 (chop) | 3,040 | -0.25 | 24% |
| ER improving (+0.05 in 15 min, >= 0.2) / fading | 3,040 | -0.26 / -0.15 | 30% / 34% |
(cell counts are cells x books pairs; files with fewer than 50 conditioned events were skipped, so the rare conditions have fewer cells.) The conditioned set fires on fewer signals and, because the base is pure wait, each skipped signal loses its floor P&L: conditioning is a strict loss unless the kept signals gain more than the skipped ones lose. Imbalance in favour is no better than imbalance against (the negative control): the book does not add to the candle. Selected conditioned cells in the recent look (tiers, 5-draw placebo): G2 LEAD 9 / CANDIDATE-RECENT 4, G3 5 / 9, G4 10 / 3; the recent-window gain over "anywhere" is equal to or below the permuted-flag gain, except KB x ER >= 0.2 (above) and KB x pattern-bar delta (G3: +0.36 L6M, +0.30 HOLD over anywhere vs +0.03 / +0.05 placebo; PRE 0.00, X' 0.00: not supported before 2025-07). Best conditioned rows: KB 15-s NR4 break AND ER >= 0.2, market, pure wait +1.98 L6M, +1.63 HOLD, PRE +0.69, X' +0.44 (MDE 3.6, 5-draw placebo max +0.79; LEAD at 5 draws, unchecked at 200); KB HA 15-s two no-lower-wick bars AND bar delta in favour +2.00 L6M (PRE +0.15, X' +0.65). Both are inside the MDE and are the KB trend-regime result of TG-1 again. Full rows: tier_G2/G3/G4.csv, ctrl_G*.parquet, gain_recent_G*.csv.

## G5 - the pattern after the dip from the running extreme (directive e)
dv0 market at the first pattern printing while the dip from the entry price >= X; dv1 the same with the pullback from the running favourable extreme since the signal; dv2 limit at the body mid at that pattern. PRE+X' averages (delta vs floor, 38 carried specs; A70 / W0): dv0 X3 -0.26 / -1.06, dv1 X3 -0.10 / -0.25 (PE W0 -0.02), dv2 X3 -0.32 / -1.28. The first-pullback version (dv1) is the only one near the floor, and for the PE three-bar it is the best recent row: dv1 X5 W0 +2.96 L6M (MDE 3.4), +2.55 HOLD, +5.08 L3M, PRE +0.75, X' -0.24, rank 1 / 201 in L6M and HOLD, 3-s delay +2.15, per contract +5.36, stack +2.6k L6M / +2.0k HOLD / -5.5k PRE / +1.8k X'. Because X' and the PRE stack are negative it stays CANDIDATE-RECENT. G5 selected-cell tiers: LEAD 13, CANDIDATE-RECENT 12 (mostly MV and PE pure-wait rows, all inside MDE).

## Sessions (g)
PE 45-s three-bar b-near W0, delta vs floor by entry session, L6M / PRE: asia +1.14 / -1.96, london -0.69 / +4.20, NY-AM +5.03 / +0.74, NY-PM +4.30 / +2.14, pre-market -2.29 / -1.35. The recent gain is NY; London carried PRE; Asia is negative in PRE. If run at all, restrict to NY-AM / NY-PM (post-hoc restriction: L6M +5 in both sessions, PRE +0.7 / +2.1). Per-session ranks for every book and the session top-3 are in rank_G1.parquet / tier_G1.csv (session column). KB NR4 break by session L6M: asia +3.24 / london -4.06 / pre +10.0, PRE asia +0.7 / london +1.4 / pre +1.9: not stable.

## QUANT header for the PE LEAD (columns not computed are named)
per contract after costs +4.64 (floor +0.80) | L3M +3.08 / L6M +2.42 / HOLD +2.14 / PRE +0.97 / X' +0.75 per planned lot (week-block MDE 3.2) | trades per week 29.6 of 42.6 signals | fire rate 69% | 1 of 2,820 G1 cells (9,952 CF2 cells) | RC p (program, PE, PRE+X') 0.74; Romano-Wolf survivors 0 | DSR of the PE best cell 0.24 | PBO 0.49 | placebo rank 1 / 201 (L6M), 1 / 201 (HOLD), 2 / 201 (PRE) | breakeven slippage: not computed (a 1-tick limit stress costs 0.2 of the 2.4) | capacity not computed | top-5% share not computed | stack correlation not computed (stack deltas shown) | neighbourhood: R_three_strict +2.63, b-far +1.40, b-mid about +1.1, dv1 X5 +2.96 (all positive; the mean of the 8 neighbours not computed) | regime it works in: NY-AM / NY-PM | drift sign count not computed | promote_ok = False (missing columns).

## Controls and caveats
* Premise label: the "positive in all windows" statement for the 45-s / 30-s three-bar on PE/KB is POST-HOC; only PRE, X' and the chain are out-of-selection. For PE the cell was the PRE+X' winner in G1 (rank 2 of 2,820 cells for the PE book on PRE+X', score +0.92), so the recent look confirms a PRE+X' selection rather than discovering it; X' alone is +0.75 for R_three but about 0 for the strict variant.
* Last re-fit cells were examined in the recent windows after being chosen (needed for the Sunday table); DN hagen 30-s C_mom2 and HM 15-s C_mom4 were not in the G1 selected set and are labelled chain picks. The chain's test-block deltas are honest OOS; the Sunday head table is a second look at the same windows for 18 cells (counted).
* Repeats: 5 tc and 5 HA rules at 15 / 30 / 45 s (600 cells) were scored in CONFIRM-BARS S1 with a 3,600-s pattern age and (for HA) HA-coordinate levels; here 600 s and real-candle levels. Results are not directly comparable.
* Bookkeeping: UF_TRIALS side plan36_confirm2 (G1..G8), DEAD_CELLS +9,952 rows (CF2-G1..G5, pooled PRE / X'), RECENT_WINS out/recent_wins/confirm2.csv (432 L3M-positive rows incl. a plain sentence), DS3_THL2_NEEDS.md CF2 section (exact 45-s three-bar order spec for a PE shadow).

## Open / next
* "What to switch ON Sunday 18:00 ET" from this section: nothing. SHADOW: PE 45-s three-bar limit at body mid (pure wait) and its first-pullback variant, one clip per live PE lot; DN HA-30 s second-up-candle add; HM 15-s four-up-closes only if sub-second reaction exists. OFF: the book / level / ER conditioning of any pattern, the pattern as a filter (d), KB / ST / WT / PB / MA patterns, every sub-minute rule that needs the first 1-3 s after the bar close.
* Not done in this pass (listed for the next 4-h update): capacity at fills, queue-position model, neighbour means, session-specific 200-draw ranks, section 8a entry-timing-within-the-bar, 200-draw placebos for all selected cells (5-draw only), the PE 45-s result on 5-minute bars (section 5 of the plan).


## ADDENDUM 2026-10-31 (follow-up order section 5 + own open items). Code l2vast/ds3/code/confirm2/c2_addendum.py, raw numbers out/confirm2/addendum.json
Unit as above: pts per planned lot vs the plain 70/30 dip floor on the same book (N basis); pc = per contract of final position (cell / floor); stack = lock-engine $/wk delta with only the named book/sessions replaced (engine lots HM10, PE5.6; scale by live/engine lots for a rough live figure). Decision delay = the order is issued d seconds after the bar close (limits are placed d seconds late). Everything here is a second look at windows already looked at: no selection, no new tier.

### A. HM 15-s four-up-closes after a 3-pt dip: DROP
One line: **drop** - on a market entry the L6M gain decays +1.06 (0 s) -> +0.74 (1 s) -> +0.30 (2 s) -> +0.07 (3 s), HOLD +1.37 -> +1.08 -> +0.68 -> +0.47, and no resting-limit version is positive.
| HM, tc 15s C_mom4, pure wait (delta vs floor per planned lot) | delay | L3M | L6M [MDE] | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| market at the 4th close after a 3-pt dip (c1) | 0 s | +1.81 | +1.06 [3.5] | +1.37 | -0.15 | +0.87 |
| | 1 s | +1.58 | +0.74 | +1.08 | -0.33 | +0.94 |
| | 2 s | +0.99 | +0.30 | +0.68 | -0.15 | +0.79 |
| | 3 s | +0.85 | +0.07 | +0.47 | -0.12 | +0.79 |
| limit at the 4th candle's OPEN, rests, placed after the dip (c2 mid) | 0 / 1 / 2 / 3 s | +1.21 / +1.22 / +0.89 / +0.70 | +0.47 / -0.02 / -0.07 / -0.32 | +0.63 / +0.24 / +0.20 / -0.14 | -0.86 / -0.86 / -1.23 / -1.09 | +0.15 / +0.32 / -0.02 / -0.26 |
| limit at its body MID (c2 near) | 0 / 1 / 2 / 3 s | +0.74 / +1.58 / +0.89 / +1.36 | -0.20 / -0.31 / -0.63 / -0.28 | +0.03 / -0.33 / -0.48 / -0.16 | -0.57 / -0.88 / -0.45 / -0.87 | -0.86 / -0.49 / -0.39 / -0.94 |
| limit at open / mid without the dip (b mid / b near) | 0 s | +1.38 / +1.60 | +0.10 / -0.15 | +0.13 / -0.23 | -0.24 / +0.08 | -0.49 / -0.97 |
The 70/30 base (A70) variants are +0.3 or less in L6M and negative in PRE and X' at every delay.
Per session (market, L6M / HOLD): Asia +1.12 / +0.77 at 0 s, +0.01 / -0.22 at 3 s; NY-AM +0.05 / +1.19 at 0 s (L6M -0.54 at 1 s, -1.96 at 3 s). In PRE both sessions are negative (Asia -0.41, NY-AM -0.51). Per contract (L6M, cell / floor): all sessions +6.74 / +4.32 at 0 s, +5.44 / +4.32 at 3 s; Asia +8.45 / +5.92 -> +7.01 / +5.92; NY-AM +11.3 / +7.63 -> +8.18 / +7.63. Lock-engine stack (HM replaced, market c1): +12.3k L6M / +9.9k HOLD / -1.4k PRE / +2.3k X' at 0 s, and still +9.9k / +7.8k / -0.3k / +3.7k at 3 s, almost all of it from Asia (+7.9k at 3 s; NY-AM about 0). That stack figure does not come from the entry: at 3 s the Asia per-lot delta is +0.01, so it is a lock-engine interaction (a pure-wait HM leg frees or delays lock capacity for the other books) and is not evidence for the rule; at HM live lots (Asia 4, NY-AM 2 vs engine 10) it scales to about +3k/wk Asia, which I would not rely on. Resting-limit stacks: c2 mid +7.6k L6M at 0 s but the per-lot delta is +0.47 and NY-AM is -2.6. Nothing survives a 3-s delay as an entry edge.

### B. PE 45-s three-bar entered at MARKET at the confirming candle's close (the user's Sunday spec), NY-AM + NY-PM only
Cell tc 45s R_three, mechanic a (market at the print +1 tick), pure wait (the whole planned lot at the print; no confirmation = no trade), ENTRIES in NY-AM and NY-PM only (post-hoc session restriction: the full-day cell had Asia/pre-market negative). Delta vs floor per planned lot on the same NY trades:
| variant | delay | L3M | L6M [MDE] | HOLD | PRE | X' | NY-AM L6M / HOLD | NY-PM L6M / HOLD | per contract L6M (cell / floor) | stack $/wk L6M / HOLD / PRE / X' (PE NY entries replaced, engine 5.6 lots) |
|---|---|---|---|---|---|---|---|---|---|---|
| R_three, market, pure wait | 0 s | +5.71 | +3.57 [4.9] | +3.54 | +1.58 | +0.81 | +4.83 / +4.22 | +1.63 / +2.51 | +2.71 / -1.92 | +3.6k / +3.3k / -0.4k / -0.6k |
| | 1 s | +5.35 | +3.55 | +3.53 | +1.74 | +0.64 | +4.79 / +4.18 | +1.66 / +2.54 | +2.70 / -1.92 | +4.1k / +3.8k / -0.2k / -0.6k |
| | 3 s | +5.54 | +3.57 | +3.55 | +1.75 | +0.84 | +4.69 / +4.08 | +1.85 / +2.74 | +2.71 / -1.92 | +3.4k / +3.1k / -0.6k / -0.6k |
| R_three_strict, market | 0 / 1 / 3 s | +5.59 / +5.24 / +5.42 | +3.80 / +3.80 / +3.83 | +3.76 / +3.76 / +3.79 | +1.62 / +1.79 / +1.64 | +0.56 / +0.38 / +0.59 | +5.25 / +5.24 / +5.16 (L6M) | +1.57 / +1.59 / +1.80 | +3.15 | +3.2k / +3.7k / +3.0k |
| R_three, 70/30 with the add at the pattern (A70) | 0 s | +2.17 | +0.92 [2.6] | +0.88 | +0.82 | +1.03 | +1.37 / +1.18 | +0.24 / +0.43 | -1.11 / -1.92 | +2.3k / +1.6k / -1.1k / -0.4k |
| (comparison) limit at body mid, pure wait | 0 s | +4.97 | +4.74 | +4.21 | +1.36 | +0.61 | +5.03 / +4.00 | +4.30 / +4.51 | +4.97 / -1.92 | +4.4k / +3.5k / -0.2k / -0.2k |
Reading: the market entry at the close is as good as the limit at the body mid on NY-AM and a lot weaker on NY-PM (+1.6 vs +4.3 L6M); it is completely insensitive to a 1-s or 3-s delay (+3.55 / +3.57) because the fill is the next-second print, so latency is not the risk here. Inside the MDE (4.9) like every PE row; PRE +1.6, X' +0.8, stack mixed (PRE -0.4k, X' -0.6k). NY-PM per contract is negative (-0.53) even though it beats a floor that is worse (-2.00): the NY-PM leg adds little (+0.24 L6M on the A70 version). Rough dollars: per-signal arithmetic 3.57 x $20 x 7 live lots x 20.8 NY signals/wk = +$10k/wk (overstated); the lock-engine stack is +3.6k at 5.6 engine lots, about +4.5k/wk at 7 lots for NY entries, with PRE and X' about -0.4k / -0.6k. Fires on about 12.6 of the 20.8 NY (AM+PM) signals per week (measured on the L6M window; the NY-AM-only signal count is also 12.6, so check the NY-PM share before sizing). Tier unchanged: LEAD-family, shadow only.

### C. Own open items for the PE 45-s three-bar (limit at body mid, pure wait, the LEAD cell)
* Neighbour means (8 neighbouring cells, delta vs floor L6M / HOLD): strict three-bar b-near +2.63 / +2.20; b-mid +1.11 / +1.28; b-far +1.40 / +1.68; 30-s b-near +1.77 / +1.57; 15-s b-near +1.38 / +1.47; market at print +2.58 / +2.28; c2 near +1.50 / +1.75; strict b-mid +1.15 / +1.25 -> mean +1.69 / +1.69, all eight positive in both windows (no knife edge; about 70% of the headline).
* Share of the gain from the top 5% of trades (L6M, PE, 1,194 signals, 830 fired): the top 5% (59 signals) carry 168% of the net gain (+2,895 pts in total): the gain is concentrated in a few large winners and the other 95% net negative against the floor. Treat the 29.6 trades/week as ~1.5 big events/week, MDE-limited.
* Capacity proxy (no depth at the fill seconds in the engine): the confirming 45-s candle trades median 96 contracts (p25 41, p10 21); 7 live PE lots are below the p10 volume of the confirming bar, so entry size is not the constraint; resting limits after a reversal candle may be behind a queue (not modelled).
* Still not computed: stack correlation / marginal worst-20-weeks, 200-draw placebos for the rest of the selected cells. Section 8a entry timing is N1's.
