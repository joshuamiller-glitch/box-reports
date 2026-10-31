# DS3_ZONES_2_ADDENDUM - the no-trade set: isolate the information (follow-up section 6, agent ZA)
Research only; no live, execution-server or chart change; UNTOUCHED never read (own masks capped 20260206: X' 20230401..20240131, PRE 20240201..20250630, HOLD 20250701.., L6M 20250801.., L3M 20251106..). Prereg autopilot/ZONES2_ADDENDUM_prereg.md (sha256 d5e671a4ec4c61834ac28fbe0d02cf7e6c2383354d30affa5137660e921d56b5, logged in DECISIONS.md before any statistic of the 8-line set). Code l2vast/ds3/code/zones2/za_*.py, outputs l2vast/ds3/out/zones2/za_*. Machinery = ZONES-2 (zl.py): 70/30 live base (SPL), N basis, points per signal in the planned-lot unit minus the unfiltered base (all signals in the denominator), week-clustered SE, MDE = 2.8 SE; S11 cells reproduce DS3_ZONES_2 to the second decimal (dead_lookup EXACT).

## Page 1 - verdict (the line for the Sunday brief first)
**BRIEF LINE: the 8-line skip IS >= 0 in L6M and HOLD on the lock-engine stack: +28.3k / +25.7k $/wk at research lots (stack MDE +30.0k / +31.0k) and +6.6k / +6.1k $/wk at the LIVE lots (MDE +11.8k / +13.0k); PRE +1.7k / +2.0k, X' +6.2k / +4.1k; L6M / HOLD / PRE / X' are inside their MDEs (L3M research +44.3k vs MDE +40.4k, live +6.3k vs +15.1k); the 8 lines are post-hoc-selected, so it stays a shadow LEAD, nothing for D6 to turn ON.**

**What carries the information (the controls the order asked for):**
1. *Which signals fire, plus a short target, is the information; the exact line level is not (re-target L6M +0.25 = fixed-40 +0.09, + shorter-than-40 distances +0.12, + the real level +0.05).* The same fired signals with the line replaced by a fixed 40-pt target gain only +0.09 / +0.08 / +0.14 per signal in L6M / HOLD / L3M (re-target to the line +0.25 / +0.29 / +0.30; skip +0.39 / +0.41 / +0.32); a fixed 20-pt target gives +0.17 / +0.14 / +0.21. The same fired signals re-targeted to a random level (distance drawn from the real distances of the same book, 300 draws) give +0.21 / +0.23 / +0.22 in L6M / HOLD / L3M: the real line beats that by only +0.05 / +0.06 / +0.08 points per signal (rank 0.83 / 0.88 / 0.92; PRE rank 0.98, X' rank 0.53). On the lock-engine stack the permuted-distance placebo is +12.9k / +11.8k $/wk (research) and +1.3k / +1.3k (live) in L6M / HOLD against the real re-target +16.0k / +16.1k and +1.2k / +2.2k: the level adds nothing you can see (rank 0.81 research, 0.48 live in L6M). (Decomposition L6M: fixed 40 +0.09, permuted distances +0.21, real line +0.25 per signal.) (A "random level at the same distance" is the real re-target by construction in a fill simulator - only the distance enters - so the informative placebo is the permuted-distance one.)
2. *The fired signals are bad base trades and it is about location.* The 44 signals a week across the 10 research books (of 361; 31 of 246 in the 6 engine books; 15 of 102 in the live book-sessions) with a fresh S8 line within 20 pts ahead lose -3.18 pts per planned lot in L6M under the base (-3.13 HOLD, -1.38 PRE, -2.09 X'). Skip takes that to 0; re-target to the line to -1.12; fixed 40 to -2.47; fixed 20 to -1.82. Random fire sets with the same count per book x session x target-bin x side lose -0.48 / -0.37 per signal (L6M / HOLD; rank of the real skip 1.00) and signals taken from another day of the same book x side x session give -0.51 / -0.41 (rank 1.00): a plain random skip loses the base edge, and a shuffled-location skip does too, so a fresh line near the entry does mark a worse-than-average signal. The fixed-40 version does beat its own random-fire placebo (rank 0.98 L6M, 0.97 HOLD) but not in PRE (0.54), and the size is small (+0.09): the "which signals" information survives into a no-level target, weakly.
3. *Action order on the stack.* Skip is the only action that is >= 0 in all five windows on the stack at both lot sets (research +44.3k / +28.3k / +25.7k / +1.7k / +6.2k; live +6.3k / +6.6k / +6.1k / +2.0k / +4.1k); half size is +5.1k / +12.1k / +10.1k / -0.5k / +3.6k research / -0.8k / +3.1k / +3.0k / -1.4k / +2.5k live, re-target is negative in PRE (-5.5k research, -1.4k live) and X' (both lot sets). A skip removes the (negative) fired signals completely; the other actions keep trading them at a smaller size or a shorter target (windows L3M / L6M / HOLD / PRE / X').
4. *The 8 vs the 11 (live set vs the research set).* Dropping the three profile lines costs nothing in the recent windows and something in PRE: S11 skip minus S8 skip = -0.03 per signal L6M, +0.04 HOLD, +0.09 PRE, +0.00 X' (L3M +0.15); stack +1.8k / +0.9k / +7.2k / -3.0k (research, L6M / HOLD / PRE / X'). The three profile lines alone (S3, 19 signals a week; windows L3M / L6M / HOLD / PRE / X'): +0.19 / +0.07 / +0.15 / +0.19 / +0.31 per signal, stack research +14.7k L6M.
5. *Which line carries it: none alone.* Per signal L6M, each line alone: 1-h kijun +0.21, OTE 70.5 +0.20, PD mid +0.16, 4-h bar mid +0.11, RTH Cam H3 +0.09, OTE 79 +0.06, 4-h Keltner +0.02, OTE 62 -0.01. Leaving one out, the stack loses most without the 4-h bar mid (L6M +28.3k -> +17.4k, HOLD +25.7k -> +15.5k at research lots), then PD mid, OTE 62, OTE 70.5, 1-h kijun; leaving out the 4-h Keltner upper IMPROVES the L6M/HOLD stack (+33.8k / +31.1k). Table 5 has all of it, with PRE and X'.
6. *D.* Skip at D = 10 / 15 / 20 / 30 is positive on the stack in L6M and HOLD at every D (research +10.3k / +16.5k / +28.3k / +25.3k L6M); PRE is positive at 10 / 15 / 20 and negative at 30 (-3.8k research, -2.1k live); D = 20 (the ZONES-2 primary) has the largest L6M/HOLD stack gain; D = 15 is the safer neighbour (smaller, positive in all five windows at both lot sets).
7. *Forward-facing (the lines were post-hoc-selected, so this is the check that matters).* (F1) Fitting only on PRE+X': the PRE+X' sign rule (dP(target) < 0 at D = 20 and 40 in both, <= -0.025 at D = 20, n >= 50) keeps 6 of the 8 lines (drops PD mid, PRE D = 40 dP +0.010, and RTH Cam H3, X' D = 40 dP +0.009), the best of the 12 (D x action) cells on PRE+X' is D = 20 skip, and it scores +0.33 / +0.36 / +0.47 per signal in L6M / HOLD / L3M, stack +23.5k / +22.4k / +44.7k research and +4.8k / +5.4k / +7.7k live. This is still in-sample for the line choice (the 8 were picked on all windows). (F2) Quarterly walk-forward chain with the pool restricted to the 8 and the ZONES-2 rule (all four training chunks negative at D = 20 and 40): it selects 0-2 lines per quarter and earns -0.03 per signal out of sample over 2024Q2..2026-02 (L6M +0.02, HOLD +0.02, L3M -0.04, PRE-OOS -0.06; 356 fires) - nothing; the same chain over all 586 streams earned -0.26. (F3, added variant) Looser chain (dP(target) < 0 at D = 20 in both halves of the data so far) keeps 5-8 of the 8 every quarter and earns +0.25 per signal out of sample (L6M +0.36, HOLD +0.38, L3M +0.27, PRE-OOS +0.19), stack +28.1k / +25.5k / +42.3k research and +6.7k / +6.2k / +5.4k live in L6M / HOLD / L3M. So: IF the 8 lines are taken as given, the forward-applied skip holds; the discovery of the lines does not (F2 and the 586-stream chain).
**Tier:** LEAD (shadow), post-hoc-selected; recent windows positive on the stack at both lot sets, L6M / HOLD / PRE / X' inside the stack MDE (L3M research just above it); PRE and X' small-positive for skip; the exact levels carry ~nothing (permuted-distance rank 0.53-0.98 on per-signal points, 0.48 in L6M on the live stack), and the line-discovery rule fails its forward chain. DSR / PBO / RC are the ZONES-2 family values (RC best-cell p 0.50 / 0.55 L6M / HOLD, DSR 0.004, PBO 0.61; this addendum adds about 110 scored cells to a family of 5,326).

## Mapping of the coded lines to the zones2 stream names
| coded line (live) | zones2 stream |
|---|---|
| PD mid | PDX|day|M |
| 1-h kijun | MAS|ich_kijun|1h |
| 4-h Keltner upper | MAS|kc_up|4h |
| 4-h bar mid | CRT|M|4h |
| RTH Camarilla H3 | PIV|cam_H3|rth |
| 15-m OTE 62 | FIB|ote62_up|15m |
| 15-m OTE 70.5 | FIB|ote705_up|15m |
| 15-m OTE 79 | FIB|ote79_up|15m |
| (absent) value-area high, 15-m swing leg | PRF|vah|sw15 |
| (absent) LVN2, 1-h swing leg | PRF|lvn1|sw1h |
| (absent) HVN1, 1-h swing leg | PRF|hvn0|sw1h |
S8 = the 8 coded; S11 = ZONES-2 set; S3 = the three absent profile lines. Rule = FRESH line between entry and target within D pts -> skip (or the action named). Live lots (FOLLOWUP_BRIEF): P6 = PE 7 (Asia/London/NY-AM); K6 = KB 2 (Asia/London/NY-AM/NY-PM); U6 = SM 4 (Asia/London); H6 = HM 4 Asia / 2 NY-AM; S6 = ST and WT not live -> research/2.35 in every session; M6 (MV) is not in the six-book lock engine and is not scored. Sessions with live lot 0 drop out of the live stack; the lock engine runs on the planned-lot R of each book (the sized-lot variant is not needed for skip / re-target / fixed target - the multiplier is 1 - and was not run for half size, where the planned-lot variant is what is shown).

## 1. Table 1 - the controls at D = 20 on the 8 lines (per planned lot / per contract / stack; recent-first)
| cell | per planned lot, pts/signal (L3M / L6M / HOLD / PRE / X') | MDE L6M/HOLD | per contract L6M/HOLD | fires/wk L6M | stack Δ$/wk research lots (L3M / L6M / HOLD / PRE / X') | stack Δ$/wk LIVE lots (L3M / L6M / HOLD / PRE / X') | stack MDE L6M/HOLD res | live |
|---|---|---|---|---|---|---|---|
| S8 D20 skip | +0.32 / +0.39 / +0.41 / +0.19 / +0.45 | 0.82 / 0.91 | +0.90 / +0.86 | 44 | +44.3k / +28.3k / +25.7k / +1.7k / +6.2k | +6.3k / +6.6k / +6.1k / +2.0k / +4.1k | +30.0k / +31.0k | +11.8k / +13.0k |
| S8 D20 re-target to line-2t | +0.30 / +0.25 / +0.29 / +0.13 / +0.25 | 0.79 / 0.85 | +0.30 / +0.33 | 44 | +33.7k / +16.0k / +16.1k / -5.5k / -0.9k | +1.1k / +1.2k / +2.2k / -1.4k / -0.4k | +33.3k / +32.0k | +13.4k / +13.8k |
| S8 D20 half size | +0.16 / +0.19 / +0.20 / +0.09 / +0.23 | 0.41 / 0.45 | +0.42 / +0.40 | 44 | +5.1k / +12.1k / +10.1k / -0.5k / +3.6k | -0.8k / +3.1k / +3.0k / -1.4k / +2.5k | +21.0k / +20.5k | +7.9k / +8.5k |
| S8 D20 fixed 40-pt target | +0.14 / +0.09 / +0.08 / -0.06 / +0.09 | 0.50 / 0.48 | +0.09 / +0.09 | 44 | +10.3k / +7.1k / +6.6k / -3.5k / +0.7k | +0.8k / +1.2k / +1.4k / -3.2k / +0.2k | +22.2k / +20.1k | +9.4k / +8.6k |
| S8 D20 fixed 30-pt target | +0.15 / +0.13 / +0.11 / -0.00 / +0.07 | 0.67 / 0.62 | +0.14 / +0.11 | 44 | +16.8k / +9.8k / +10.1k / -2.6k / -3.4k | +2.7k / +1.9k / +2.4k / -0.6k / -1.3k | +24.0k / +21.5k | +10.6k / +9.8k |
| S8 D20 fixed 20-pt target | +0.21 / +0.17 / +0.14 / +0.04 / +0.03 | 0.73 / 0.71 | +0.18 / +0.15 | 44 | +27.5k / +11.6k / +10.6k / -3.6k / -7.4k | +2.3k / -0.4k / -0.4k / -0.5k / -1.9k | +28.4k / +26.3k | +12.6k / +11.9k |
Stack = lock engine, 6 books, $/wk Δ vs the unfiltered stack; research lots ST10 HM10 WT7 KB5.2 SM7.4 PE5.6 (base L6M 26k, HOLD 15k, PRE 35k, X' 8k $/wk), live lots as above (base 17k / 14k / 18k / 2k). Fires/wk = fired signals a week in L6M (all 10 research books, 361 signals a week; in the 6 engine books 31 of 246; in the live HM / KB / SM / PE sessions 15 of 102). The per-signal columns cover all 10 research books (MA, MV, PB, DN included); the stack columns only the 6 engine books. Per contract = points per contract of final position minus the base.

## 2. Table 2 - where the gain sits: fired-signal P&L and the placebo means (per planned lot, N basis)
| rule on the fired signals | mean P&L of fired signals L6M | mean P&L of fired signals HOLD | mean P&L of fired signals PRE | mean P&L of fired signals X' | mean P&L of fired signals L3M |
|---|---|---|---|---|---|
| base (fired signals, unchanged) | -3.18 | -3.13 | -1.38 | -2.09 | -3.13 |
| skip | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |
| re-target to line-2t | -1.12 | -0.93 | -0.42 | -0.95 | -0.24 |
| half size | -1.59 | -1.56 | -0.69 | -1.04 | -1.56 |
| fixed 40 | -2.47 | -2.48 | -1.80 | -1.68 | -1.78 |
| fixed 30 | -2.09 | -2.32 | -1.38 | -1.77 | -1.65 |
| fixed 20 | -1.82 | -2.04 | -1.07 | -1.96 | -1.07 |

| cell | per signal L3M / L6M / HOLD / PRE / X' | rank (L3M / L6M / HOLD / PRE / X') | stack research L3M / L6M / HOLD / PRE / X' | stack live L3M / L6M / HOLD / PRE / X' |
|---|---|---|---|---|
| re-target: real | +0.30 / +0.25 / +0.29 / +0.13 / +0.25 |  | +33.7k / +16.0k / +16.1k / -5.5k / -0.9k | +1.1k / +1.2k / +2.2k / -1.4k / -0.4k |
| re-target: permuted-distance placebo (same fired signals, random distance) | +0.22 / +0.21 / +0.23 / +0.08 / +0.24 | 0.92 / 0.83 / 0.88 / 0.98 / 0.53 | +30.9k (0.72) / +12.9k (0.81) / +11.8k (0.95) / -4.1k (0.19) / -3.4k (0.86) | +2.6k (0.22) / +1.3k (0.48) / +1.3k (0.75) / -1.0k (0.26) / -0.8k (0.69) |
| re-target: random fire set (same count, distances from the real pool) | -0.22 / -0.39 / -0.30 / -0.28 / -0.20 | 0.99 / 1.00 / 1.00 / 1.00 / 0.99 | -13.1k (1.00) / -18.3k (1.00) / -16.1k (1.00) / -16.8k (0.98) / -9.1k (0.96) | -11.5k (0.97) / -10.9k (1.00) / -9.4k (1.00) / -7.2k (1.00) / -3.1k (0.87) |
| re-target: shuffled-day | -0.20 / -0.40 / -0.31 / -0.27 / -0.18 | 0.98 / 1.00 / 1.00 / 1.00 / 1.00 | -11.5k (1.00) / -18.6k (1.00) / -16.6k (1.00) / -15.9k (0.98) / -8.6k (0.93) | -11.1k (0.98) / -11.1k (1.00) / -9.8k (1.00) / -7.2k (0.99) / -2.5k (0.80) |
| skip: real | +0.32 / +0.39 / +0.41 / +0.19 / +0.45 |  | +44.3k / +28.3k / +25.7k / +1.7k / +6.2k | +6.3k / +6.6k / +6.1k / +2.0k / +4.1k |
| skip: random fire set | -0.23 / -0.48 / -0.37 / -0.30 / -0.23 | 0.98 / 1.00 / 1.00 / 1.00 / 1.00 | -2.0k (0.99) / -9.2k (1.00) / -7.3k (1.00) / -10.6k (0.98) / -7.9k (1.00) | -5.9k (0.96) / -6.7k (1.00) / -5.6k (1.00) / -4.8k (1.00) / -1.4k (0.98) |
| skip: shuffled-day | -0.26 / -0.51 / -0.41 / -0.30 / -0.21 | 0.99 / 1.00 / 1.00 / 1.00 / 1.00 | +0.4k (1.00) / -8.1k (1.00) / -6.6k (1.00) / -10.5k (0.99) / -7.6k (0.98) | -4.1k (0.91) / -6.0k (1.00) / -5.0k (1.00) / -4.7k (0.99) / -0.8k (0.95) |
| fixed 40: real | +0.14 / +0.09 / +0.08 / -0.06 / +0.09 |  | +10.3k / +7.1k / +6.6k / -3.5k / +0.7k | +0.8k / +1.2k / +1.4k / -3.2k / +0.2k |
| fixed 40: random fire set | +0.02 / -0.10 / -0.09 / -0.06 / -0.02 | 0.76 / 0.98 / 0.97 / 0.54 / 0.82 | -0.3k (0.88) / -4.0k (0.98) / -3.2k (0.98) / -4.4k (0.58) / -3.6k (0.92) | -1.5k (0.70) / -2.7k (0.92) / -2.1k (0.93) / -1.7k (0.16) / -1.1k (0.84) |
| fixed 40: shuffled-day | +0.03 / -0.10 / -0.09 / -0.06 / -0.03 | 0.80 / 0.94 / 0.94 / 0.54 / 0.86 | -0.4k (0.88) / -3.8k (0.99) / -3.0k (0.99) / -4.3k (0.56) / -3.2k (0.90) | -1.8k (0.74) / -3.0k (0.94) / -2.5k (0.96) / -1.8k (0.20) / -1.1k (0.80) |
| half size: real | +0.16 / +0.19 / +0.20 / +0.09 / +0.23 |  | +5.1k / +12.1k / +10.1k / -0.5k / +3.6k | -0.8k / +3.1k / +3.0k / -1.4k / +2.5k |
| half size: random fire set | -0.13 / -0.24 / -0.19 / -0.15 / -0.11 | 0.98 / 1.00 / 1.00 / 1.00 / 1.00 | -2.8k (0.81) / -2.5k (0.99) / -2.0k (0.98) / -7.1k (0.98) / -3.4k (0.98) | -3.3k (0.67) / -2.7k (0.98) / -2.2k (0.96) / -3.0k (0.74) / +0.0k (0.94) |
| half size: shuffled-day | -0.13 / -0.25 / -0.19 / -0.16 / -0.12 | 0.98 / 1.00 / 1.00 / 1.00 / 1.00 | -1.7k (0.77) / -1.9k (0.98) / -1.4k (0.98) / -8.1k (0.99) / -3.4k (0.96) | -3.0k (0.66) / -2.6k (1.00) / -2.0k (0.99) / -3.2k (0.89) / +0.3k (0.88) |
Placebo rows show the draw MEAN (300 per-signal draws; 100 of them also run through the lock engine) and, in brackets for the stack, the share of draws the real cell beats. Rank = share of the 300 draws the real cell beats. "Random fire set": same fire count per book x session x target-bin x side stratum, distances for re-target taken from the real pool of the same book. "Permuted distance": the real fired signals, distances permuted within the book. Skip and half size do not use the distance, so the permuted-distance placebo is degenerate for them (not run).

## 3. Table 3 - stack line (weekly mean, SD, max drawdown, worst-20 weeks) at LIVE lots and at research lots, S8 D = 20
| cell | window | mean $/wk base -> rule | SD | maxDD | worst-20 weeks (sum) | weeks | Δ (MDE) |
|---|---|---|---|---|---|---|---|
| S8 skip, LIVE lots | L3M | 3k -> 9k | 64k -> 55k | 181k -> 150k | 36k -> 124k | 14 | +6.3k (+15.1k) |
| S8 skip, LIVE lots | L6M | 17k -> 24k | 63k -> 62k | 181k -> 150k | -213k -> -56k | 28 | +6.6k (+11.8k) |
| S8 skip, LIVE lots | HOLD | 14k -> 21k | 77k -> 68k | 298k -> 209k | -618k -> -366k | 32 | +6.1k (+13.0k) |
| S8 skip, LIVE lots | PRE | 18k -> 20k | 63k -> 58k | 305k -> 281k | -1169k -> -1014k | 75 | +2.0k (+8.8k) |
| S8 skip, LIVE lots | X' | 2k -> 6k | 45k -> 44k | 336k -> 329k | -778k -> -655k | 44 | +4.1k (+11.6k) |

| cell | window | mean $/wk base -> rule | SD | maxDD | worst-20 weeks (sum) | weeks | Δ (MDE) |
|---|---|---|---|---|---|---|---|
| S8 skip, research lots | L3M | -21k -> 23k | 138k -> 105k | 551k -> 331k | -298k -> 323k | 14 | +44.3k (+40.4k) |
| S8 skip, research lots | L6M | 26k -> 55k | 140k -> 127k | 551k -> 331k | -803k -> -100k | 28 | +28.3k (+30.0k) |
| S8 skip, research lots | HOLD | 15k -> 41k | 165k -> 142k | 692k -> 517k | -1700k -> -840k | 32 | +25.7k (+31.0k) |
| S8 skip, research lots | PRE | 35k -> 37k | 137k -> 130k | 739k -> 932k | -2802k -> -2521k | 75 | +1.7k (+19.0k) |
| S8 skip, research lots | X' | 8k -> 14k | 100k -> 98k | 522k -> 543k | -1575k -> -1401k | 44 | +6.2k (+22.2k) |

| cell | window | mean $/wk base -> rule | SD | maxDD | worst-20 weeks (sum) | weeks | Δ (MDE) |
|---|---|---|---|---|---|---|---|
| S8 re-target to line-2t, LIVE lots | L3M | 3k -> 4k | 64k -> 57k | 181k -> 154k | 36k -> 51k | 14 | +1.1k (+14.2k) |
| S8 re-target to line-2t, LIVE lots | L6M | 17k -> 19k | 63k -> 62k | 181k -> 154k | -213k -> -182k | 28 | +1.2k (+13.4k) |
| S8 re-target to line-2t, LIVE lots | HOLD | 14k -> 17k | 77k -> 68k | 298k -> 198k | -618k -> -476k | 32 | +2.2k (+13.8k) |
| S8 re-target to line-2t, LIVE lots | PRE | 18k -> 16k | 63k -> 60k | 305k -> 272k | -1169k -> -1102k | 75 | -1.4k (+7.7k) |
| S8 re-target to line-2t, LIVE lots | X' | 2k -> 2k | 45k -> 45k | 336k -> 344k | -778k -> -783k | 44 | -0.4k (+9.7k) |

| cell | window | mean $/wk base -> rule | SD | maxDD | worst-20 weeks (sum) | weeks | Δ (MDE) |
|---|---|---|---|---|---|---|---|
| S8 re-target to line-2t, research lots | L3M | -21k -> 12k | 138k -> 105k | 551k -> 322k | -298k -> 173k | 14 | +33.7k (+46.6k) |
| S8 re-target to line-2t, research lots | L6M | 26k -> 42k | 140k -> 127k | 551k -> 322k | -803k -> -335k | 28 | +16.0k (+33.3k) |
| S8 re-target to line-2t, research lots | HOLD | 15k -> 31k | 165k -> 142k | 692k -> 522k | -1700k -> -1083k | 32 | +16.1k (+32.0k) |
| S8 re-target to line-2t, research lots | PRE | 35k -> 29k | 137k -> 130k | 739k -> 737k | -2802k -> -2690k | 75 | -5.5k (+16.6k) |
| S8 re-target to line-2t, research lots | X' | 8k -> 7k | 100k -> 94k | 522k -> 550k | -1575k -> -1514k | 44 | -0.9k (+21.7k) |

| cell | window | mean $/wk base -> rule | SD | maxDD | worst-20 weeks (sum) | weeks | Δ (MDE) |
|---|---|---|---|---|---|---|---|
| S8 half size, LIVE lots | L3M | 3k -> 2k | 64k -> 57k | 181k -> 168k | 36k -> 24k | 14 | -0.8k (+9.8k) |
| S8 half size, LIVE lots | L6M | 17k -> 21k | 63k -> 62k | 181k -> 168k | -213k -> -138k | 28 | +3.1k (+7.9k) |
| S8 half size, LIVE lots | HOLD | 14k -> 17k | 77k -> 71k | 298k -> 240k | -618k -> -471k | 32 | +3.0k (+8.5k) |
| S8 half size, LIVE lots | PRE | 18k -> 16k | 63k -> 61k | 305k -> 333k | -1169k -> -1163k | 75 | -1.4k (+6.1k) |
| S8 half size, LIVE lots | X' | 2k -> 4k | 45k -> 43k | 336k -> 303k | -778k -> -666k | 44 | +2.5k (+7.0k) |

| cell | window | mean $/wk base -> rule | SD | maxDD | worst-20 weeks (sum) | weeks | Δ (MDE) |
|---|---|---|---|---|---|---|---|
| S8 half size, research lots | L3M | -21k -> -16k | 138k -> 124k | 551k -> 466k | -298k -> -226k | 14 | +5.1k (+32.9k) |
| S8 half size, research lots | L6M | 26k -> 38k | 140k -> 139k | 551k -> 466k | -803k -> -568k | 28 | +12.1k (+21.0k) |
| S8 half size, research lots | HOLD | 15k -> 25k | 165k -> 157k | 692k -> 617k | -1700k -> -1393k | 32 | +10.1k (+20.5k) |
| S8 half size, research lots | PRE | 35k -> 34k | 137k -> 133k | 739k -> 822k | -2802k -> -2699k | 75 | -0.5k (+11.6k) |
| S8 half size, research lots | X' | 8k -> 12k | 100k -> 96k | 522k -> 513k | -1575k -> -1480k | 44 | +3.6k (+13.8k) |

Windows: L3M 14 weeks, L6M 28, HOLD 32, PRE 75, X' 44 (calendar weeks touched). Worst-20 = sum of the 20 worst weeks. SD / maxDD are the lock-engine stack with the rule applied from day one (research lots 6 books; live lots ST/WT at research/2.35). The skip lowers SD and maxDD in L3M / L6M / HOLD at both lot sets; in PRE (research lots maxDD 739k -> 932k) and X' (522k -> 543k) the max drawdown does not improve.

## 4. Table 4 - the 8 coded lines vs the 11 vs the 3 absent profile lines (D = 20, fresh)
| cell | per planned lot, pts/signal (L3M / L6M / HOLD / PRE / X') | MDE L6M/HOLD | per contract L6M/HOLD | fires/wk L6M | stack Δ$/wk research lots (L3M / L6M / HOLD / PRE / X') | stack Δ$/wk LIVE lots (L3M / L6M / HOLD / PRE / X') | stack MDE L6M/HOLD res | live |
|---|---|---|---|---|---|---|---|
| S8 skip | +0.32 / +0.39 / +0.41 / +0.19 / +0.45 | 0.82 / 0.91 | +0.90 / +0.86 | 44 | +44.3k / +28.3k / +25.7k / +1.7k / +6.2k | +6.3k / +6.6k / +6.1k / +2.0k / +4.1k | +30.0k / +31.0k | +11.8k / +13.0k |
| S8 re-target to line-2t | +0.30 / +0.25 / +0.29 / +0.13 / +0.25 | 0.79 / 0.85 | +0.30 / +0.33 | 44 | +33.7k / +16.0k / +16.1k / -5.5k / -0.9k | +1.1k / +1.2k / +2.2k / -1.4k / -0.4k | +33.3k / +32.0k | +13.4k / +13.8k |
| S8 half size | +0.16 / +0.19 / +0.20 / +0.09 / +0.23 | 0.41 / 0.45 | +0.42 / +0.40 | 44 | +5.1k / +12.1k / +10.1k / -0.5k / +3.6k | -0.8k / +3.1k / +3.0k / -1.4k / +2.5k | +21.0k / +20.5k | +7.9k / +8.5k |
| S8 fixed 40-pt target | +0.14 / +0.09 / +0.08 / -0.06 / +0.09 | 0.50 / 0.48 | +0.09 / +0.09 | 44 | +10.3k / +7.1k / +6.6k / -3.5k / +0.7k | +0.8k / +1.2k / +1.4k / -3.2k / +0.2k | +22.2k / +20.1k | +9.4k / +8.6k |
| S11 skip | +0.47 / +0.36 / +0.45 / +0.28 / +0.45 | 0.93 / 1.03 | +1.03 / +1.06 | 56 | +52.2k / +30.1k / +26.7k / +8.9k / +3.2k | +9.3k / +5.8k / +4.9k / +4.7k / +1.8k | +29.4k / +30.7k | +10.7k / +12.0k |
| S11 re-target to line-2t | +0.49 / +0.30 / +0.42 / +0.21 / +0.33 | 0.90 / 0.98 | +0.37 / +0.48 | 56 | +35.8k / +16.0k / +14.7k / +0.4k / -3.7k | +2.9k / -0.3k / +0.1k / +1.1k / -2.7k | +29.9k / +29.3k | +11.7k / +12.2k |
| S11 half size | +0.24 / +0.18 / +0.23 / +0.14 / +0.23 | 0.47 / 0.51 | +0.47 / +0.48 | 56 | +13.7k / +17.5k / +14.9k / +2.2k / +4.0k | +0.7k / +3.6k / +3.4k / +0.8k / +1.6k | +19.0k / +19.2k | +7.9k / +8.6k |
| S11 fixed 40-pt target | +0.21 / +0.14 / +0.14 / +0.00 / +0.21 | 0.49 / 0.46 | +0.14 / +0.14 | 56 | +15.2k / +8.5k / +7.1k / -2.8k / -1.5k | +0.4k / -0.3k / -0.2k / -2.3k / -0.1k | +21.9k / +19.8k | +9.7k / +8.8k |
| S3 skip | +0.19 / +0.07 / +0.15 / +0.19 / +0.31 | 0.46 / 0.50 | +0.25 / +0.32 | 19 | +22.1k / +14.7k / +12.2k / +5.9k / -0.8k | +7.4k / +3.8k / +3.3k / +4.1k / +0.2k | +19.0k / +17.4k | +7.5k / +7.2k |
| S3 re-target to line-2t | +0.18 / +0.08 / +0.18 / +0.14 / +0.18 | 0.46 / 0.49 | +0.10 / +0.19 | 19 | +10.6k / +7.2k / +4.7k / +3.8k / -4.2k | +3.3k / +0.9k / +0.3k / +3.6k / -2.0k | +17.9k / +16.4k | +7.2k / +6.8k |
| S3 half size | +0.10 / +0.03 / +0.08 / +0.09 / +0.15 | 0.23 / 0.25 | +0.12 / +0.16 | 19 | +6.4k / +10.4k / +8.1k / +1.8k / -0.6k | +1.7k / +2.9k / +2.5k / +2.5k / -0.4k | +12.4k / +11.3k | +5.1k / +4.7k |
| S3 fixed 40-pt target | +0.11 / +0.05 / +0.06 / +0.07 / +0.15 | 0.23 / 0.22 | +0.05 / +0.06 | 19 | +3.1k / +1.3k / +0.7k / -0.9k / -1.7k | +0.4k / -1.0k / -0.7k / -0.0k / -0.1k | +7.9k / +7.2k | +3.1k / +3.4k |

## 5. Table 5 - which line carries it (D = 20 fresh, skip / re-target / half; alone and leave-one-out)
| line | alone skip, per signal L3M / L6M / HOLD / PRE / X' | alone skip, stack research L6M/HOLD/PRE/X' | alone skip, stack live L6M/HOLD/PRE/X' | fires/wk | S8 minus line, skip, stack research L6M/HOLD/PRE/X' | S8 minus line, skip, stack live L6M/HOLD/PRE/X' | S8 minus line, per signal L3M / L6M / HOLD / PRE / X' |
|---|---|---|---|---|---|---|---|
| PD mid | +0.08 / +0.16 / +0.11 / +0.02 / +0.23 | +11.4k / +9.4k / -1.9k / +2.6k | +4.8k / +4.0k / -0.7k / +2.5k | 4 | +24.1k / +22.5k / +1.8k / +4.6k | +4.8k / +5.1k / +1.6k / +3.3k | +0.39 / +0.37 / +0.39 / +0.23 / +0.36 |
| 1h kijun | +0.20 / +0.21 / +0.16 / +0.09 / +0.40 | +10.0k / +8.5k / -0.0k / +3.9k | +3.8k / +3.8k / -1.0k / +3.3k | 8 | +26.8k / +24.2k / +1.9k / +6.1k | +7.2k / +6.7k / +2.0k / +4.3k | +0.22 / +0.32 / +0.36 / +0.19 / +0.34 |
| 4h Keltner up | +0.21 / +0.02 / +0.02 / -0.01 / +0.05 | +2.1k / +1.8k / -1.2k / -3.3k | +1.1k / +1.1k / -1.0k / +0.4k | 3 | +33.8k / +31.1k / +2.7k / +6.5k | +8.3k / +7.7k / +2.0k / +3.1k | +0.28 / +0.45 / +0.46 / +0.19 / +0.44 |
| 4h bar mid | +0.01 / +0.11 / +0.15 / +0.10 / +0.10 | +12.0k / +11.9k / +3.4k / +0.1k | +4.1k / +4.3k / +1.5k / +0.9k | 6 | +17.4k / +15.5k / -1.4k / +8.2k | +2.5k / +2.3k / +0.2k / +5.9k | +0.33 / +0.33 / +0.30 / +0.12 / +0.49 |
| RTH Cam H3 | -0.06 / +0.09 / +0.12 / +0.03 / -0.00 | +3.1k / +4.4k / +0.9k / -5.8k | +2.0k / +2.3k / +1.0k / -1.7k | 5 | +27.2k / +25.2k / +2.0k / +5.9k | +6.5k / +6.3k / +2.0k / +4.3k | +0.40 / +0.34 / +0.37 / +0.19 / +0.51 |
| OTE 62 | +0.11 / -0.01 / -0.00 / +0.03 / +0.15 | +5.2k / +5.5k / -4.1k / +4.7k | -0.3k / +0.0k / -2.4k / +2.5k | 10 | +24.9k / +24.0k / +5.1k / +5.5k | +8.8k / +8.6k / +3.7k / +4.8k | +0.35 / +0.44 / +0.49 / +0.23 / +0.44 |
| OTE 70.5 | +0.22 / +0.20 / +0.22 / +0.08 / +0.03 | +14.5k / +14.0k / +3.8k / +2.1k | +5.3k / +5.8k / +1.3k / +1.1k | 9 | +25.6k / +24.0k / -1.1k / +3.1k | +6.2k / +5.5k / +0.0k / +2.2k | +0.24 / +0.32 / +0.34 / +0.14 / +0.40 |
| OTE 79 | +0.07 / +0.06 / +0.13 / +0.02 / -0.03 | +2.8k / +6.5k / -3.6k / +0.9k | -0.1k / +1.1k / -0.1k / -1.8k | 10 | +28.4k / +24.9k / +3.2k / +4.9k | +8.0k / +7.4k / +1.4k / +5.1k | +0.28 / +0.41 / +0.39 / +0.21 / +0.45 |
(Full S8 skip, for reference: per signal +0.32 / +0.39 / +0.41 / +0.19 / +0.45; stack research L6M/HOLD/PRE/X' +28.3k / +25.7k / +1.7k / +6.2k; live +6.6k / +6.1k / +2.0k / +4.1k.)

| line | action alone | per signal L3M / L6M / HOLD / PRE / X' | stack research L6M/HOLD/PRE/X' | stack live L6M/HOLD/PRE/X' |
|---|---|---|---|---|
| PD mid | re-target to line-2t | +0.12 / +0.14 / +0.11 / +0.05 / +0.24 | +5.5k / +4.2k / -1.4k / +4.2k | +2.7k / +2.2k / -0.3k / +2.4k |
| PD mid | half size | +0.04 / +0.08 / +0.05 / +0.01 / +0.11 | +4.7k / +3.4k / -1.7k / +0.9k | +2.2k / +1.8k / -1.3k / +1.4k |
| 1h kijun | re-target to line-2t | +0.22 / +0.16 / +0.13 / +0.08 / +0.26 | +5.2k / +4.7k / -1.1k / +2.6k | +1.7k / +2.1k / -1.3k / +1.7k |
| 1h kijun | half size | +0.10 / +0.11 / +0.08 / +0.04 / +0.20 | +5.0k / +3.6k / -0.2k / +0.0k | +2.3k / +2.1k / -0.8k / +1.3k |
| 4h Keltner up | re-target to line-2t | +0.19 / +0.04 / +0.04 / -0.01 / -0.00 | +1.4k / +0.3k / -0.8k / -3.3k | +0.5k / +0.4k / -0.6k / -0.7k |
| 4h Keltner up | half size | +0.10 / +0.01 / +0.01 / -0.00 / +0.03 | +1.4k / +0.5k / -1.0k / -2.8k | -0.1k / -0.0k / -1.1k / -0.1k |
| 4h bar mid | re-target to line-2t | +0.02 / +0.05 / +0.10 / +0.07 / +0.13 | +7.5k / +8.1k / +0.1k / +1.0k | +2.1k / +2.6k / +0.2k / +0.6k |
| 4h bar mid | half size | +0.01 / +0.05 / +0.07 / +0.05 / +0.05 | +4.1k / +3.8k / +1.4k / +1.1k | +1.7k / +1.5k / +0.5k / +0.9k |
| RTH Cam H3 | re-target to line-2t | -0.02 / +0.09 / +0.11 / -0.00 / +0.09 | +5.3k / +5.5k / +0.6k / -1.0k | +2.4k / +2.3k / +0.5k / +0.1k |
| RTH Cam H3 | half size | -0.03 / +0.04 / +0.06 / +0.01 / -0.00 | +2.9k / +3.7k / -0.4k / -0.9k | +1.5k / +1.7k / +0.4k / -0.7k |
| OTE 62 | re-target to line-2t | -0.08 / -0.11 / -0.08 / -0.02 / +0.06 | +2.1k / +2.9k / -7.0k / +3.0k | -0.4k / +0.1k / -3.3k / +0.7k |
| OTE 62 | half size | +0.06 / -0.00 / -0.00 / +0.02 / +0.07 | +4.3k / +4.1k / -2.9k / +4.1k | -0.1k / -0.1k / -1.4k / +1.9k |
| OTE 70.5 | re-target to line-2t | +0.21 / +0.16 / +0.17 / +0.05 / -0.09 | +9.0k / +9.9k / -0.2k / -3.3k | +2.6k / +3.7k / +0.7k / -2.4k |
| OTE 70.5 | half size | +0.11 / +0.10 / +0.11 / +0.04 / +0.02 | +9.2k / +8.4k / +2.8k / +1.5k | +3.1k / +3.1k / +0.8k / +0.2k |
| OTE 79 | re-target to line-2t | +0.03 / +0.03 / +0.09 / +0.01 / +0.00 | +1.0k / +3.0k / -3.1k / +1.2k | -0.7k / -0.1k / -0.2k / -1.9k |
| OTE 79 | half size | +0.03 / +0.03 / +0.06 / +0.01 / -0.02 | +1.8k / +4.1k / -2.2k / +1.2k | +0.6k / +1.3k / -0.4k / -1.7k |
| VAH sw15 (absent) | re-target to line-2t | +0.02 / +0.06 / +0.07 / +0.11 / +0.07 | +6.2k / +4.8k / +2.5k / -2.6k | -0.2k / -0.7k / +2.0k / +0.2k |
| VAH sw15 (absent) | half size | -0.03 / -0.01 / +0.00 / +0.07 / +0.05 | +8.2k / +7.0k / +1.0k / -1.2k | +1.7k / +1.5k / +1.4k / +0.4k |
| LVN sw1h (absent) | re-target to line-2t | -0.03 / +0.01 / +0.06 / +0.03 / +0.09 | +0.6k / +1.9k / +2.0k / -1.1k | -0.9k / -0.3k / +1.2k / -0.5k |
| LVN sw1h (absent) | half size | +0.03 / +0.02 / +0.04 / +0.02 / +0.10 | +0.9k / +1.0k / -0.2k / -1.4k | +0.0k / +0.1k / +0.6k / -0.2k |
| HVN sw1h (absent) | re-target to line-2t | +0.27 / +0.05 / +0.11 / +0.03 / -0.02 | +2.6k / +2.6k / +0.1k / -2.9k | +1.9k / +2.7k / +0.5k / -2.7k |
| HVN sw1h (absent) | half size | +0.14 / +0.04 / +0.07 / +0.01 / +0.01 | +2.6k / +0.6k / -0.6k / +2.2k | +1.3k / +1.0k / -0.3k / -0.3k |

| line (absent from live) | alone skip per signal L3M / L6M / HOLD / PRE / X' | stack research L6M/HOLD/PRE/X' | live |
|---|---|---|---|
| VAH sw15 | -0.07 / -0.01 / +0.00 / +0.15 / +0.09 | +8.3k / +6.9k / +3.6k / -1.5k | +0.3k / +0.0k / +2.3k / +1.8k |
| LVN sw1h | +0.05 / +0.04 / +0.08 / +0.05 / +0.19 | +5.1k / +5.8k / +0.6k / -0.9k | +1.2k / +1.6k / +0.9k / +0.3k |
| HVN sw1h | +0.28 / +0.09 / +0.14 / +0.01 / +0.01 | +6.8k / +4.8k / +2.9k / -0.7k | +3.5k / +3.2k / +1.6k / -1.6k |

Stack deltas of single lines and leave-one-out cells are each inside their stack MDE (5-30k research); read the leave-one-out ordering as a ranking with large error bars, not as a decomposition that adds up (lines overlap: a signal near two lines is counted once).

## 6. Table 6 - D = 10 / 15 / 20 / 30 on the 8 lines (skip / re-target / half / fixed 40 on the fired signals)
| cell | per planned lot, pts/signal (L3M / L6M / HOLD / PRE / X') | MDE L6M/HOLD | per contract L6M/HOLD | fires/wk L6M | stack Δ$/wk research lots (L3M / L6M / HOLD / PRE / X') | stack Δ$/wk LIVE lots (L3M / L6M / HOLD / PRE / X') | stack MDE L6M/HOLD res | live |
|---|---|---|---|---|---|---|---|
| S8 D10 skip | +0.13 / +0.10 / +0.19 / +0.12 / +0.20 | 0.41 / 0.48 | +0.29 / +0.36 | 20 | +18.0k / +10.3k / +12.3k / +3.0k / +4.0k | +1.8k / +2.4k / +3.0k / +1.0k / +1.4k | +24.1k / +22.8k | +9.7k / +10.0k |
| S8 D10 re-target to line-2t | +0.16 / +0.09 / +0.17 / +0.11 / +0.12 | 0.40 / 0.47 | +0.12 / +0.20 | 20 | +15.9k / +6.1k / +8.3k / -2.2k / +0.2k | +0.3k / -0.2k / +0.6k / -0.7k / -2.5k | +23.9k / +22.9k | +9.3k / +9.8k |
| S8 D10 half size | +0.07 / +0.05 / +0.09 / +0.06 / +0.10 | 0.20 / 0.24 | +0.14 / +0.18 | 20 | +2.5k / +6.5k / +6.5k / +1.3k / +3.3k | +0.1k / +2.1k / +1.9k / -0.1k / +1.2k | +18.6k / +17.0k | +6.3k / +6.5k |
| S8 D10 fixed 40-pt target | +0.02 / -0.00 / +0.03 / -0.02 / -0.02 | 0.21 / 0.22 | -0.00 / +0.03 | 20 | +1.3k / +2.0k / +2.5k / -0.3k / -1.5k | -0.8k / -0.5k / -0.3k / -0.5k / -1.2k | +15.9k / +14.2k | +4.7k / +4.7k |
| S8 D15 skip | +0.28 / +0.29 / +0.31 / +0.10 / +0.35 | 0.60 / 0.73 | +0.62 / +0.61 | 31 | +26.4k / +16.5k / +16.6k / +4.9k / +5.9k | +3.6k / +3.4k / +3.0k / +1.6k / +2.0k | +27.0k / +27.9k | +10.4k / +11.8k |
| S8 D15 re-target to line-2t | +0.21 / +0.19 / +0.20 / +0.10 / +0.17 | 0.62 / 0.69 | +0.23 / +0.24 | 31 | +17.6k / +7.5k / +8.8k / -3.0k / -0.3k | -0.1k / -0.5k / -0.2k / -0.7k / -1.8k | +24.6k / +24.9k | +10.2k / +11.3k |
| S8 D15 half size | +0.14 / +0.14 / +0.15 / +0.05 / +0.18 | 0.30 / 0.37 | +0.30 / +0.29 | 31 | +2.4k / +8.8k / +7.9k / +1.5k / +2.7k | -1.7k / +1.5k / +0.8k / -1.1k / +0.6k | +19.6k / +18.7k | +6.6k / +7.2k |
| S8 D15 fixed 40-pt target | -0.02 / +0.01 / +0.01 / -0.08 / +0.02 | 0.30 / 0.32 | +0.01 / +0.01 | 31 | +3.8k / +2.7k / +3.1k / -1.8k / +0.2k | +1.0k / -0.3k / -0.2k / -2.2k / -0.8k | +21.0k / +18.9k | +8.0k / +7.6k |
| S8 D20 skip | +0.32 / +0.39 / +0.41 / +0.19 / +0.45 | 0.82 / 0.91 | +0.90 / +0.86 | 44 | +44.3k / +28.3k / +25.7k / +1.7k / +6.2k | +6.3k / +6.6k / +6.1k / +2.0k / +4.1k | +30.0k / +31.0k | +11.8k / +13.0k |
| S8 D20 re-target to line-2t | +0.30 / +0.25 / +0.29 / +0.13 / +0.25 | 0.79 / 0.85 | +0.30 / +0.33 | 44 | +33.7k / +16.0k / +16.1k / -5.5k / -0.9k | +1.1k / +1.2k / +2.2k / -1.4k / -0.4k | +33.3k / +32.0k | +13.4k / +13.8k |
| S8 D20 half size | +0.16 / +0.19 / +0.20 / +0.09 / +0.23 | 0.41 / 0.45 | +0.42 / +0.40 | 44 | +5.1k / +12.1k / +10.1k / -0.5k / +3.6k | -0.8k / +3.1k / +3.0k / -1.4k / +2.5k | +21.0k / +20.5k | +7.9k / +8.5k |
| S8 D20 fixed 40-pt target | +0.14 / +0.09 / +0.08 / -0.06 / +0.09 | 0.50 / 0.48 | +0.09 / +0.09 | 44 | +10.3k / +7.1k / +6.6k / -3.5k / +0.7k | +0.8k / +1.2k / +1.4k / -3.2k / +0.2k | +22.2k / +20.1k | +9.4k / +8.6k |
| S8 D30 skip | +0.52 / +0.45 / +0.45 / +0.02 / +0.05 | 1.04 / 1.10 | +1.29 / +1.17 | 66 | +38.9k / +25.3k / +22.6k / -3.8k / +3.8k | +11.2k / +9.2k / +8.3k / -2.1k / +2.4k | +36.4k / +36.0k | +17.3k / +17.7k |
| S8 D30 re-target to line-2t | +0.34 / +0.32 / +0.41 / +0.03 / -0.05 | 0.97 / 1.03 | +0.38 / +0.45 | 66 | +26.1k / +15.2k / +15.5k / -7.6k / -7.1k | +2.1k / +2.2k / +3.1k / -4.7k / -3.2k | +35.9k / +34.6k | +14.7k / +15.3k |
| S8 D30 half size | +0.26 / +0.23 / +0.22 / +0.01 / +0.03 | 0.52 / 0.55 | +0.58 / +0.52 | 66 | +12.6k / +15.6k / +13.4k / -1.3k / +3.4k | +5.1k / +6.5k / +6.1k / -2.2k / +1.7k | +21.5k / +21.1k | +12.1k / +12.1k |
| S8 D30 fixed 40-pt target | +0.01 / -0.03 / -0.03 / -0.11 / -0.15 | 0.65 / 0.59 | -0.02 / -0.03 | 66 | +10.0k / +5.8k / +4.9k / -5.8k / -2.8k | +0.3k / -0.0k / +0.1k / -4.9k / -1.8k | +27.4k / +24.2k | +11.4k / +10.2k |

## 7. Table 7 - per book and session, S8 D = 20 skip, per signal (N basis; from the same cell)
| group | per signal L3M / L6M / HOLD / PRE / X' | n signals L6M | fired L6M | kept/contract L6M | fired-signal base mean L6M |
|---|---|---|---|---|---|
| ALL | +0.32 / +0.39 / +0.41 / +0.19 / +0.45 | 9741 | 1192 | +0.90 | -3.18 |
| DN | -0.93 / +0.19 / +0.12 / -0.64 / +0.33 | 701 | 83 | +0.96 | -1.59 |
| HM | +1.50 / +2.19 / +2.12 / +0.08 / -0.46 | 909 | 139 | +3.36 | -14.30 |
| KB | +1.76 / +0.70 / +0.56 / +0.09 / +0.90 | 1257 | 192 | +1.07 | -4.57 |
| MA | -3.03 / -1.94 / -1.31 / +0.35 / -2.25 | 407 | 88 | -0.79 | +8.97 |
| MV | +0.62 / +1.15 / +1.22 / +0.63 / +1.77 | 1131 | 139 | +1.63 | -9.36 |
| PB | -0.63 / -0.37 / -0.14 / -0.08 / +0.81 | 866 | 35 | -0.07 | +9.27 |
| PE | +0.20 / +0.34 / +0.25 / +0.44 / +0.33 | 1194 | 111 | +0.46 | -3.69 |
| SM | +0.52 / -0.51 / -0.71 / -0.11 / +1.88 | 314 | 70 | +0.27 | +2.28 |
| ST | +0.70 / +0.30 / +0.31 / +0.25 / +0.42 | 1256 | 113 | +0.75 | -3.33 |
| WT | -0.09 / -0.01 / +0.09 / +0.29 / +0.26 | 1706 | 222 | +0.26 | +0.10 |
| asia | +0.79 / +0.82 / +0.80 / +0.23 / +1.32 | 2678 | 521 | +2.01 | -4.23 |
| close | +18.76 / +12.25 / +10.78 / +6.02 / -2.96 | 22 | 8 | +16.05 | -33.68 |
| london | +0.02 / -0.25 / -0.35 / +0.41 / +0.56 | 2050 | 301 | +0.54 | +1.72 |
| nyam | -0.14 / +0.43 / +0.39 / -0.17 / -0.38 | 2784 | 197 | +0.65 | -6.06 |
| nypm | -0.11 / +0.08 / +0.28 / +0.08 / +0.45 | 1718 | 121 | +0.21 | -1.17 |
| pre | +2.01 / +1.02 / +1.45 / +0.92 / +0.80 | 489 | 44 | +1.34 | -11.34 |
| short | +0.19 / +0.61 / +0.63 / -0.04 / +0.83 | 4875 | 348 | +0.93 | -8.57 |
| long | +0.45 / +0.17 / +0.19 / +0.41 / +0.10 | 4866 | 844 | +0.82 | -0.96 |

Bases (S8 D20 skip, per signal, ALL): M: +0.53 / +0.63 / +0.67 / +0.34 / +0.58; N: +0.32 / +0.39 / +0.41 / +0.19 / +0.45; LIVE: +0.60 / +0.72 / +0.76 / +0.44 / +0.72 (L3M / L6M / HOLD / PRE / X').

## 8. Table 8 - forward-facing versions (fit on PRE+X', test later; chains)
| version | per signal L6M/HOLD/L3M (PRE, X' in-sample) | MDE L6M/HOLD | stack research L6M/HOLD/L3M | stack live L6M/HOLD/L3M |
|---|---|---|---|---|
| F1a: PRE+X'-filtered lines (6 of 8), best (D, action) on PRE+X' = D20 skip | +0.33 / +0.36 / +0.47 (+0.21, +0.46) | 0.81 / 0.90 | +23.5k / +22.4k / +44.7k | +4.8k / +5.4k / +7.7k |
| F1b: all 8, best (D, action) on PRE+X' = D20 skip (= the coded cell) | +0.39 / +0.41 / +0.32 (+0.19, +0.45) | 0.82 / 0.91 | +28.3k / +25.7k / +44.3k | +6.6k / +6.1k / +6.3k |
| F2 chain (pool = the 8, strict ZONES-2 rule), skip | +0.02 / +0.02 / -0.04 (PRE-OOS -0.06, 2024Q2..2026-02 -0.03) |  | +8.8k / +7.7k / +11.0k | +2.4k / +2.1k / +1.4k |
| F2 chain, re-target | +0.03 / +0.02 / +0.01 (PRE-OOS -0.04, 2024Q2..2026-02 -0.02) |  | +4.5k / +3.9k / +5.9k | +1.3k / +1.2k / +0.1k |
| F2 chain, half size | +0.01 / +0.01 / -0.02 (PRE-OOS -0.03, 2024Q2..2026-02 -0.02) |  | +2.4k / +2.1k / -0.8k | +1.4k / +1.2k / -0.1k |
| F3 chain (pool = the 8, loose rule), skip | +0.36 / +0.38 / +0.27 (PRE-OOS +0.19, 2024Q2..2026-02 +0.25) |  | +28.1k / +25.5k / +42.3k | +6.7k / +6.2k / +5.4k |
| F3 chain, re-target | +0.23 / +0.27 / +0.25 (PRE-OOS +0.08, 2024Q2..2026-02 +0.14) |  | +15.8k / +15.9k / +31.8k | +1.1k / +2.1k / -0.1k |
| F3 chain, half size | +0.18 / +0.19 / +0.14 (PRE-OOS +0.09, 2024Q2..2026-02 +0.12) |  | +12.2k / +10.2k / +4.0k | +3.2k / +3.1k / -1.3k |

PRE+X' line filter (adjusted dP(target), fresh):
| line | dP D20 X' | dP D20 PRE | dP D40 X' | dP D40 PRE | n D20 X'/PRE | kept |
|---|---|---|---|---|---|---|
| PD mid | -0.084 | -0.050 | -0.085 | +0.010 | 246 / 247 | NO |
| 1h kijun | -0.089 | -0.059 | -0.026 | -0.009 | 441 / 646 | yes |
| 4h Keltner up | -0.078 | -0.049 | -0.001 | -0.009 | 150 / 265 | yes |
| 4h bar mid | -0.028 | -0.086 | -0.022 | -0.049 | 337 / 451 | yes |
| RTH Cam H3 | -0.057 | -0.068 | +0.009 | -0.059 | 232 / 364 | NO |
| OTE 62 | -0.041 | -0.027 | -0.030 | -0.049 | 462 / 734 | yes |
| OTE 70.5 | -0.028 | -0.047 | -0.030 | -0.037 | 509 / 739 | yes |
| OTE 79 | -0.027 | -0.041 | -0.043 | -0.043 | 462 / 847 | yes |

Chain sets, strict (F2): 20240401: none; 20240701: none; 20241001: 1h kijun; 20250101: 1h kijun; 20250401: none; 20250701: none; 20251001: 4h bar mid; 20260101: 4h bar mid, RTH Cam H3

Chain sets, loose (F3) kept 5-8 lines every quarter (the lines that drop out are 4-h Keltner in 2025Q2 and 2025Q4, PD mid / OTE 70.5 / OTE 79 in the first two quarters).

F2 and F3 start 2024-04 (the first refit needs the 2023-04..2024-03 training year); PRE-OOS = 2024-04..2025-06 per signal, 2024Q2..2026-02 = the whole out-of-sample span; the stack columns are L6M / HOLD / L3M only.

## 9. For D6 and the Sunday brief
* ON: nothing from this addendum. The coded rule (8 lines, fresh, D = 20, skip) is a shadow LEAD; the numbers do not argue against leaving it as coded (>= 0 in L6M and HOLD on the stack at both lot sets, 5 of 5 windows positive for skip at D <= 20), and do not argue for treating it as a validated filter (post-hoc lines, MDE, level adds ~0, discovery chain fails).
* D6 mapping (ZONES-2 section 8 vocabulary): group entry; property poi_ahead(type in {PD mid, 1-h kijun, 4-h Keltner upper, 4-h bar mid, RTH Camarilla H3, 15-m OTE 62 / 70.5 / 79}, fresh, D = 20 pts); value skip. Milder arm: lotmult 0.5 (stack +12.1k / +10.1k research L6M / HOLD, +3.1k / +3.0k live). Re-target and fixed-target arms: OFF (the level is not the information).
* Suggested cheap hardening for the forward register (no live change): log the fired signal, its nearest fresh line and distance, and the fill-or-skip outcome of the skipped signal as a paper trade, per line, so the per-line carrier question (Table 5) is answered with forward data; the cell to beat at live lots: skip +6.6k / +6.1k $/wk L6M / HOLD, 15 fires a week in the live book-sessions (31 in the six engine books).

## 10. Notes, caveats, bookkeeping
* Scored: 87 stack cells (A/B/C families of the prereg) + 9 placebo jobs x 300 per-signal draws (100 of each also through the lock engine) + F1 (12 cells x 2 pools) + F2 + F3 chains. Multiplicity: the 8 lines are a subset of an 11-of-586 post-hoc selection; add about 110 cells to ZONES-2's 5,326.
* The skip decision uses lines known before the signal; a 1-s or 3-s delay changes nothing for skip. Re-target and fixed-target variants send a different order and were scored at the signal second only (not candidates).
* Half size is scored with the size multiplier 0.5 inside the lock engine and net points unchanged (planned-lot R locks); the ZONES-2 stack table scaled the points instead - the two agree within 1k (L6M +12.1k vs +11.6k research).
* Live stack = HM, KB, SM, PE at the stated live sessions/lots plus ST and WT at research/2.35; the four-book live-only subset is kept in the pickle (za_cellsA.pkl, key live4). The live-lot lock engine uses each book's reference live lot for its R and $ locks (HM 4 lots, so the 2-lot NY-AM trades run at multiplier 0.5 under HM's 4-lot locks).
* Files: out/zones2/za_cellsA.pkl, za_plc_<mode>_<action>.pkl, za_fwd.pkl, za_fwd3.pkl, logs za_run*.log; code zones2/za_lib.py, za_runA.py, za_runP.py, za_fwd.py, za_fwd3.py, za_report.py, za_mkreport.py.
