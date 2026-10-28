# DS3_CLOSE_FINAL - the T-CLOSE study (cash close / MOC window), blocks 1-4 - D3CL1, 2026-10-28
Research only. NQ direct 1-s path (shared harness open2, patched in-process; harness untouched), fees 4.84 RT NQ (proxy), WEAK fee labels for non-NQ instruments. Sources: DS3_CLOSE_BLOCK1/2/3.md, this file (block 4), DS3_SPEC_RVW1_F30.md (v2).

## 1. Verdict line
**Close: 9 PASS, 4 CANDIDATE (primary, harness rules) over 1,707 scored NQ-traded cells (+96 other-instrument cells, +12 classifier cells, +1 pooled sleeve); every PASS / CANDIDATE belongs to ONE signal family (NQ VWAP reversion, z 0.75-2.0, entry 15:15-15:30, plus its bar-type duplicates), and ALL of them FAIL the secondary per-bracket-class best-of-N column. Best NQ close book: RVW1|F30 (VWAP reversion >= 1 sigma at 15:30, 30/30, flat 16:00), 3.19 trades/wk, +$2,144/wk direct (M; +$1,725 T), vs same-rule-random-clock +6.60 pts [2.95, 10.17] (200 draws; T +5.10 [1.02, 8.98]), stack-add Sharpe +0.12 (T +0.09), maxDD change -$6.2k (T -$3.6k), weekly paired MDE $2.25k (not distinguishable from zero at the weekly level; about 157 forward weeks). Best overnight-hold cell: PC15|H0930 (post-close 16:00-16:15 move held to the next 09:30), d Sharpe +0.22/+0.25 but DEAD (bracket beta, year share, rank vs (b) .77), d mean +$5.9-6.6k/wk against an MDE of $9.8k. Un-block comparison: un-blocking ST/HM/WT/KB/SM in 15:01-16:54 is -$2.1k/wk (Sharpe 2.41 -> 2.28), so RVW1 beats it by about $4.3k/wk.**
Primary-vs-secondary: the harness best-of-N is computed over the prereg group's family; the 36-cell RVW1 surface family and the 14-cell bar-type family are small and highly correlated (null p95 5.0 pts), which is why they print PASS; over the block-1 family (201 cells) the same cell is CANDIDATE (null p95 129), and under the user-adopted secondary null (per bracket class, pooled over all NQ cells with >= 100 PRE trades: FIX class p95 11.1 pts M / 11.6 T) its effect 6.84 / 5.37 fails. Treat it as a CANDIDATE for a PAPER forward test, not as a proven edge. Counts of cells by block (primary tier of the worse basis): B1 0/1/200, B2 0/0/184, B3 0/0/180, RS surface 2/1/33, GRID 0/2/1090, BARS 7/0/7 (PASS/CANDIDATE/DEAD).

## 2. Top 15 by stack-add Sharpe delta regardless of verdict (WF 142 weeks; NQ cells with >= 100 PRE trades; duplicates of one event set / bracket collapsed)
Time-exit and overnight-hold cells (T1600, NOSTOP, H1805, H0930) earn a positive stack-add from bracket beta (random-direction entries do too); they only count if they also beat placebo (b) AND the beta placebo (d). Every cell below has |d mean| at or below its weekly MDE.
| # | cell (block) | primary | secondary (class null) | trades/wk | stack-add d Sharpe (WF, min M/T) | d mean $/wk | MDE $/wk | fwd weeks to settle | (b) effect pts (min M/T) | HOLD $/wk | 2023-24 $/wk | failed gates (M ; T) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | PC15|H0930 (B2) | DEAD | DEAD | 3.93 | +0.22 | +5,886 | 9,794 | 393 | +3.5 | +7,155 | +940 | beats_b,beats_beta,stack_add_pre,year_share,best_of_N ; beats_b,beats_beta,stack_add_pre,year_share,best_of_N |
| 2 | F2|H0930 (B3) | DEAD | DEAD | 2.50 | +0.19 | +5,189 | 7,861 | 326 | +4.6 | +6,823 | -2,329 | beats_b,beats_beta,stack_add_pre,span2,best_of_N ; beats_b,beats_beta,stack_add_pre,span2,best_of_N |
| 3 | RVW1|T1600 (B1) | DEAD | DEAD | 3.19 | +0.13 | +3,086 | 4,259 | 271 | +6.9 | +2,013 | +1,092 | beats_beta,year_share,best_of_N ; beats_beta,stack_add_pre,year_share,best_of_N |
| 4 | MOC10|NOSTOP (B1) | DEAD | DEAD | 2.20 | +0.13 | +2,351 | 2,758 | 195 | +8.1 | +1,611 | -641 | beats_b,span2,best_of_N ; beats_b,span2,best_of_N |
| 5 | MOC5|NOSTOP (B1) | DEAD | DEAD | 3.40 | +0.13 | +2,046 | 3,270 | 363 | +6.3 | +1,384 | -1,165 | beats_beta,stack_add_pre,span2,best_of_N ; beats_beta,stack_add_pre,span2,best_of_N |
| 6 | RVW1|NOSTOP (B1) | DEAD | DEAD | 3.19 | +0.13 | +3,109 | 4,782 | 336 | +6.2 | +2,813 | +1,187 | beats_b,beats_beta,stack_add_pre,year_share,best_of_N ; beats_b,beats_beta,stack_add_pre,year_share,best_of_N |
| 7 | RSI2D|H1805 (B2) | DEAD | DEAD | 2.75 | +0.13 | +2,759 | 4,595 | 394 | +5.0 | +1,940 | -603 | beats_b,beats_beta,stack_add_pre,span2,best_of_N ; beats_b,beats_beta,stack_add_pre,year_share,span2,best_of_N |
| 8 | MOC5|T1600 (B1) | DEAD | DEAD | 3.40 | +0.12 | +1,754 | 3,280 | 497 | +5.0 | +1,507 | -971 | beats_b,beats_beta,stack_add_pre,year_share,span2,best_of_N ; beats_b,beats_beta,stack_add_pre,span2,best_of_N |
| 9 | MOC10|T1600 (B1) | DEAD | DEAD | 2.20 | +0.12 | +1,966 | 2,756 | 279 | +6.4 | +1,720 | -448 | beats_b,beats_beta,stack_add_pre,span2,best_of_N ; beats_b,beats_beta,stack_add_pre,span2,best_of_N |
| 10 | MOC10|H0930 (B1) | DEAD | DEAD | 2.20 | +0.11 | +4,132 | 7,593 | 479 | +1.8 | +1,367 | -2,329 | beats_b,beats_beta,stack_add_pre,year_share,hold,span2,best_of_N ; beats_b,beats_beta,stack_add_pre,year_share,hold,span2,best_of_N |
| 11 | MOC10|STRAIL (B1) | DEAD | DEAD | 2.20 | +0.11 | +1,993 | 2,521 | 227 | +7.0 | +1,237 | -511 | beats_b,span2,best_of_N ; beats_b,beats_beta,span2,best_of_N |
| 12 | v10000|F30 (B4BARS) | PASS | DEAD | 2.96 | +0.11 | +2,074 | 2,289 | 173 | +5.4 | +1,344 | +1,068 |  ;  |
| 13 | RVW1|STRAIL (B1) | DEAD | DEAD | 3.19 | +0.10 | +2,673 | 3,705 | 273 | +6.9 | +1,078 | +1,049 | beats_beta,year_share,best_of_N ; beats_beta,year_share,best_of_N |
| 14 | RVW1|T1614 (B1) | DEAD | DEAD | 3.19 | +0.10 | +3,111 | 4,963 | 361 | +8.3 | +1,862 | +1,445 | beats_beta,year_share,best_of_N ; beats_beta,stack_add_pre,year_share,hold,best_of_N |
| 15 | RVW2|NOSTOP (B1) | DEAD | DEAD | 1.56 | +0.10 | +1,999 | 3,787 | 510 | +9.3 | +1,614 | +1,050 | beats_b,beats_beta,stack_add_pre,best_of_N ; beats_b,beats_beta,stack_add_pre,year_share,best_of_N |

Block-4 per-bracket-class null (secondary column, pooled over all blocks): 
| basis / class | p95 of null max (pts) | n cells | best cell | best effect |
|---|---|---|---|---|
| M/FIX | 11.12 | 796 | RVW2_gB|G45S60 | 9.89 |
| M/STRUCT | 6.29 | 15 | MOC5|DAYHL | 5.68 |
| M/TIME | 20.17 | 82 | RVW2|NOSTOP | 11.73 |
| M/OVN | 57.41 | 58 | X6M|H0930 | 10.79 |
| M/TRAIL | 13.23 | 61 | RVW2|STRAIL | 10.62 |
| M/ALL | 57.41 | 1012 | RVW2|NOSTOP | 11.73 |
| T/FIX | 11.55 | 796 | RVZ125T1515|F40 | 9.19 |
| T/STRUCT | 6.65 | 15 | MOC5|DAYHL | 5.30 |
| T/TIME | 20.47 | 82 | XZS|NOSTOP | 11.20 |
| T/OVN | 62.82 | 58 | XRL|H1805 | 10.41 |
| T/TRAIL | 13.14 | 61 | RVW2|STRAIL | 7.52 |
| T/ALL | 62.82 | 1012 | XZS|NOSTOP | 11.20 |

## 3. RECOMMENDED-FOR-SIM close book: RVW1|F30, resting-limit-at-touch variant
DS3_SPEC_RVW1_F30.md (v2) is the spec: rule, window, lots, own locks, concurrency, expectation, caveats, forward-register entry (ds3_TCLOSE_RVW1_F30_LMT; machine entry l2vast/ds3/out/tclose_b1/forward_entry_ds3_TCLOSE_RVW1_F30_LMT.json). It is recommended for forward PAPER trading even though not promotable: it is the only family of the study that beats the random-clock placebo, the beta placebo and the random-in-regime placebo on both bases, is positive in the holdout and in 2023-04..2024-01 on its own, is negatively correlated with every live book (-0.14 to +0.16) and has a plateau in z, bracket and entry time. It is execution-fragile and thin (about +2.2 pts per trade net); see 4.
### Execution evidence (prereg EXEC; same events)
| variant | basis | pts/trade | WF $/wk | HOLD $/wk | 2023-24 $/wk | 2x-cost HOLD | stack d mean [CI] | d Sharpe |
|---|---|---|---|---|---|---|---|---|
| fixed(block1) | M | +2.95 | +2,144 | +900 | +1,107 | -1,378 | +2,144 [560, 3,774] | +0.12 |
| fixed(block1) | T | +2.62 | +1,725 | +577 | +1,325 | -223 | +1,725 [53, 3,393] | +0.09 |
| Q | M | +2.95 | +2,144 | +900 | +1,107 | -1,378 | +2,144 [560, 3,774] | +0.12 |
| Q | T | +2.23 | +1,396 | +62 | +1,292 | -738 | +1,396 [-238, 3,106] | +0.08 |
| DELAY1s | M | +1.26 | +632 | -929 | +1,136 | -3,077 | +632 [-928, 2,237] | +0.04 |
| DELAY1s | T | +2.22 | +1,384 | +228 | +1,305 | -572 | +1,384 [-340, 3,115] | +0.07 |
| DELAY2s | M | +1.29 | +652 | -915 | +1,153 | -3,093 | +652 [-952, 2,299] | +0.03 |
| DELAY2s | T | +2.01 | +1,259 | -52 | +1,217 | -852 | +1,259 [-478, 2,948] | +0.07 |
| DELAY5s | M | +0.50 | +241 | -1,161 | +638 | -3,302 | +241 [-1,357, 1,764] | +0.01 |
| DELAY5s | T | +1.53 | +788 | -621 | +1,411 | -1,421 | +788 [-1,001, 2,497] | +0.05 |
| LMT300 | M | +2.00 | +1,332 | +502 | +654 | -1,590 | +1,332 [-186, 2,836] | +0.08 |
| LMT300 | T | +3.32 | +2,270 | +1,597 | +986 | +856 | +2,270 [671, 3,896] | +0.13 |
### Robustness of RVW1|F30 (M / T unless stated)
- Windows WF (M): mean $2,144, SD $9,585, Sharpe 1.61, maxDD $56,317, worst week $-24,194, win 0.60 vs required 0.54, PF 1.31; HOLD $900; 2023-04..2024-01 $1,107; L8W $-2,720.
- By year (WF weekly mean, M): 2024: $2,486, 2025: $2,701, 2026: $940; T: 2024: $1,068, 2025: $2,742, 2026: $1,125. VIX tercile low / mid / high (M): $1,834, $864, $3,484.
- Cost sweep M (WF / HOLD $/wk): 1x +2,144 / +900; 1.5x +362 / -1,139; 2x +125 / -1,378; 3x -348 / -1,856. Mirror (reversed side) PRE $-5,107/wk.
- Day-block (5-day) bootstrap of the stack-add maxDD change, WF: M -26,029 [CI -105,244, 25,985], P(worse) 0.19; HOLD -12,244 [-68,650, 30,578].
- Weekly correlation to every live book (WF, M): ST -0.11, HM -0.09, WT +0.08, KB -0.11, SM +0.16, PB -0.07, PS -0.14, K4_base_series -0.09, live_stack -0.07.
- Concurrency replay (live books' open lots at the RVW1 entries): mean 16.5 lots open, p95 50, max 67; the 50-contract cap would bind on 11% of entries. With those skipped (cap 50): M WF $2,036/wk, HOLD $465, d Sharpe +0.11; T WF $1,773, HOLD $400. (The directive's statement that the 50-cap is not binding assumed a flat stack: the books are NOT flat at 15:30.)
- Sizing (R6k = 10 lots here):
| cell | sizing | basis | lots | WF $/wk | maxDD | worst wk | HOLD | stack d mean [CI] | d Sharpe | d maxDD |
|---|---|---|---|---|---|---|---|---|---|---|
| RVW1|F30 | fixed10 | M | 10 | +2,144 | 56,317 | -24,194 | +900 | +2,144 [560, 3,774] | +0.12 | -6,220 |
| RVW1|F30 | fixed10 | T | 10 | +1,725 | 69,769 | -24,394 | +577 | +1,725 [53, 3,393] | +0.09 | -3,614 |
| RVW1|F30 | R12k | M | 20 | +3,877 | 119,331 | -48,902 | +1,386 | +3,877 [724, 7,125] | +0.21 | -11,280 |
| RVW1|F30 | R12k | T | 20 | +3,039 | 150,100 | -49,302 | +740 | +3,039 [-312, 6,360] | +0.14 | -6,070 |
| RVW1|BE10 | fixed10 | M | 10 | +3,286 | 61,349 | -18,242 | +2,582 | +3,286 [1,332, 5,501] | +0.19 | -9,262 |
| RVW1|BE10 | fixed10 | T | 10 | +1,337 | 101,161 | -18,492 | +225 | +1,337 [-512, 3,264] | +0.06 | -3,173 |
| RVW1|BE10 | R12k | M | 20 | +6,212 | 155,821 | -37,128 | +4,628 | +6,212 [2,342, 10,356] | +0.34 | -17,365 |
| RVW1|BE10 | R12k | T | 20 | +2,233 | 212,248 | -37,628 | -145 | +2,233 [-1,553, 6,219] | +0.07 | -5,187 |
### Full parameter surface (prereg RS1/RS2, 36 cells; basis M / T). Harness verdicts (worse of M/T): 2 PASS (RVZ100T1530|F30 = RVW1|F30 and RVZ125T1530|F30), 1 CANDIDATE (RVZ075T1530|F30), 33 DEAD; per base: M 4 PASS / 0 CANDIDATE, T 4 PASS / 1 CANDIDATE.
Stack-add d Sharpe (WF):
**Entry 15:15** - rows z, columns bracket (M / T)

| z | F20 | F30 | F40 |
|---|---|---|---|
| 0.75 | -0.02 / +0.03 | +0.03 / +0.07 | +0.07 / +0.13 |
| 1.00 | -0.01 / +0.03 | +0.03 / +0.07 | +0.07 / +0.12 |
| 1.25 | +0.01 / +0.05 | +0.05 / +0.09 | +0.09 / +0.13 |
| 1.50 | +0.00 / +0.03 | +0.02 / +0.04 | +0.04 / +0.07 |

**Entry 15:30** - rows z, columns bracket (M / T)

| z | F20 | F30 | F40 |
|---|---|---|---|
| 0.75 | +0.02 / +0.05 | +0.13 / +0.10 | +0.10 / +0.09 |
| 1.00 | +0.02 / +0.05 | +0.12 / +0.09 | +0.09 / +0.08 |
| 1.25 | +0.02 / +0.06 | +0.12 / +0.10 | +0.10 / +0.09 |
| 1.50 | +0.02 / +0.04 | +0.09 / +0.06 | +0.05 / +0.04 |

**Entry 15:45** - rows z, columns bracket (M / T)

| z | F20 | F30 | F40 |
|---|---|---|---|
| 0.75 | -0.08 / -0.03 | -0.03 / -0.01 | -0.05 / -0.02 |
| 1.00 | -0.09 / -0.05 | -0.04 / -0.02 | -0.06 / -0.04 |
| 1.25 | -0.07 / -0.05 | -0.03 / -0.02 | -0.04 / -0.02 |
| 1.50 | -0.05 / -0.04 | -0.01 / -0.00 | -0.01 / +0.00 |

Per-trade (b) effect in pts (PRE):
**Entry 15:15** - rows z, columns bracket (M / T)

| z | F20 | F30 | F40 |
|---|---|---|---|
| 0.75 | +2.2 / +2.1 | +3.7 / +3.0 | +6.1 / +6.4 |
| 1.00 | +2.0 / +1.7 | +4.3 / +3.3 | +7.0 / +7.5 |
| 1.25 | +3.0 / +2.8 | +5.1 / +4.5 | +8.5 / +9.2 |
| 1.50 | +2.2 / +2.1 | +4.9 / +3.8 | +8.1 / +8.1 |

**Entry 15:30** - rows z, columns bracket (M / T)

| z | F20 | F30 | F40 |
|---|---|---|---|
| 0.75 | +2.9 / +2.5 | +6.4 / +5.1 | +6.8 / +4.5 |
| 1.00 | +2.6 / +2.3 | +6.8 / +5.4 | +7.1 / +4.9 |
| 1.25 | +2.8 / +2.9 | +7.2 / +6.0 | +7.2 / +5.0 |
| 1.50 | +3.3 / +2.8 | +7.0 / +6.0 | +6.7 / +4.5 |

**Entry 15:45** - rows z, columns bracket (M / T)

| z | F20 | F30 | F40 |
|---|---|---|---|
| 0.75 | +0.4 / +0.6 | +0.9 / +0.6 | -0.0 / -0.2 |
| 1.00 | +0.1 / +0.1 | +0.6 / +0.2 | -0.8 / -1.0 |
| 1.25 | +0.7 / -0.0 | +0.7 / +0.3 | -0.4 / -0.6 |
| 1.50 | +1.4 / +0.9 | +2.4 / +2.1 | +1.8 / +1.6 |

Reading: a plateau in z (0.75-1.5 all positive at 15:15 and 15:30), strongest for bracket F40 at 15:15 and F30/F40 at 15:30, weak for F20; **the effect is absent at 15:45 (every cell has d Sharpe <= 0 and (b) effect ~0)**: the reversion needs about 30 minutes before the close. Neighbouring z cells agree in sign. On the block-4 target x stop grid (RVW1 and RVW2 signals, d Sharpe averaged over stops): targets 5-15 pts ~0, 20 pts +0.02, 30-60 pts +0.05 to +0.08; stops (10-60) matter little. Bar-type check (sigma sampled on 3m / 5m / 15m / volume 1,000 / 2,500 / 10,000): same events on 94-100% of days, F30 PASS on all seven (identical verdicts), BE10 DEAD on all (the harness family is 14 cells; secondary DEAD).

## 4. The un-block answer (does any close book beat un-blocking the existing books 15:00-16:54?)
Un-blocking (ST, HM, WT, KB, SM regenerated with entries 15:01-16:54, identity 0 mismatches outside the window; PB/PS not regenerated; mapped basis) = **-$2.1k/wk WF** (44,867 -> 42,726; Sharpe 2.41 -> 2.28; PRE -$3.0k, 2023-24 -$3.0k, HOLD -$1.1k [CI -2.8k, +0.3k]; WT -$1.6k, SM -$0.5k, ST/HM/KB ~0). Every close cell with a positive stack-add beats it; of the study's cells only RVW1-family cells do so with placebo support: RVW1|F30 +$2.1k (M) / +$1.7k (T) => +$3.9-4.3k/wk better than un-blocking.

## 5. MOC-proxy validity (how well the 15:50 reaction predicts the 16:00 print)
Reaction = sign of price(15:50:29) - price(15:49:59) (the only proxy available; no imbalance feed). Continuation of that sign to 16:00 hits 55.5% (PRE, n=346; 57.1% when |reaction| >= 5 pts, n=247; 53.7% on 2023-24). Agreement with the day's direction is only 46% / 42% (the reaction is NOT aligned with the day's flow, contrary to the usual MOC assumption); after agreement with the day direction continuation is 58.1% vs 53.2% after disagreement. The reaction sign is weakly predictable at 14:30 (AUC 0.54, permutation p 0.02, 0.08 Bonferroni over 4 labels; lead feature the 3-day direction), i.e. it is partly a function of the prior days' trend. Tape confirmations (L1 book imbalance, L4 sweeps, F3 1-s delta) do not improve the continuation (agreeing subsets are no better than the no-signal subset). Every MOC-proxy cell is DEAD (MOC5/MOC10/FAD/U55/U58/RFAD: 0 beat the beta placebo with a positive stack-add). A real imbalance feed would plausibly sharpen the reaction signal (the proxy is a price impulse, 55-57% directional), but nothing in the proxy cells indicates a near-miss: the best MOC-proxy cells (MOC10 time exits) have d Sharpe +0.12 only through bracket beta, rank vs (b) .84-.86 and fail the 2023-24 span. NEEDS.md carries the vendor options; nothing was bought.

## 6. Structural read
- Day types / direction: continuation of the day's direction into the close (C1500, C1530, CTR, PIV, LEXT, XAG3) never beats the placebos; reversal toward the session VWAP does (RVW1/RVW2, plus RSI2DS-type dip buying that needs the SMA200 filter). Reversal needs >= 30 minutes: entries at 15:15-15:30 work, 15:45 does not; the 15:50 publication window is the most expensive second of the book (10 lots cost 2.25 pts RT).
- Targets: the edge lives in targets of 30-60 pts (any stop 10-60), not in small brackets; time-exit cells earn it through bracket beta.
- Instruments: the VWAP reversion is a US equity-index effect (ES, YM, RTY: 6 of 6 brackets beat (b) each; CL, GC, SI, ZN, 6E: nothing). The four index series are one factor (ES-YM weekly correlation 0.70). NQ-ES 0.50, NQ-YM 0.29, NQ-RTY 0.39, ES-YM 0.70, ES-RTY 0.55, YM-RTY 0.63; pooled vs live books: ST -0.06, HM +0.04, WT +0.00, KB -0.04, SM +0.15, PB -0.06, PS -0.04, K4 -0.14, live_stack -0.00.
- Tape and book (3.9/3.10): aggressor delta, sweeps, book imbalance, depth asymmetry and pulled liquidity add nothing as triggers (0 of 180 cells beat the placebos with stack-add) or as confirmations.
- Post-close (3.6): the 16:00-16:15 move continued overnight has the largest raw overnight stack-add (PC15|H0930 +$5.9-6.6k/wk) but is bracket beta + long bias (2025 negative, 2026 dominates): DEAD.
- Learned classifier (3.11, 72 features at 15:30 / 15:50, LightGBM + isotonic, V2 guards): no skill (AUC 0.42-0.50 on the 15:30-16:00 and 15:50-16:00 labels, permutation p 0.45-0.76; the overnight label shows a base-rate hit of 54-58% with AUC < 0.50). The 12 entry cells are DEAD:
| cell | basis | n events | PRE own $/wk | stack d Sharpe PRE | stack d mean PRE [lo] | HOLD $/wk | verdict | failed |
|---|---|---|---|---|---|---|---|---|
| CLC_1530_y_a_F30_p55 | M | 371 | -2,644 | -0.16 | -2,644 [-4,386] | -1,833 | DEAD | mean_up,stack_add_pre,cost2x,not_better_than_hand_rule,hold |
| CLC_1530_y_a_F30_p55 | T | 371 | -2,187 | -0.14 | -2,187 [-4,050] | -1,217 | DEAD | mean_up,stack_add_pre,cost2x,not_better_than_hand_rule,hold |
| CLC_1530_y_a_F30_p60 | M | 156 | -439 | -0.03 | -439 [-1,692] | -498 | DEAD | mean_up,stack_add_pre,cost2x,not_better_than_hand_rule,hold |
| CLC_1530_y_a_F30_p60 | T | 156 | -154 | -0.02 | -154 [-1,416] | -599 | DEAD | mean_up,stack_add_pre,cost2x,not_better_than_hand_rule,hold |
| CLC_1530_y_a_T1600_p55 | M | 371 | -1,676 | -0.10 | -1,676 [-4,825] | -2,038 | DEAD | mean_up,stack_add_pre,cost2x,not_better_than_hand_rule,hold |
| CLC_1530_y_a_T1600_p55 | T | 371 | -1,731 | -0.11 | -1,731 [-4,865] | -1,966 | DEAD | mean_up,stack_add_pre,cost2x,not_better_than_hand_rule,hold |
| CLC_1530_y_a_T1600_p60 | M | 156 | -1,031 | -0.06 | -1,031 [-2,919] | -543 | DEAD | mean_up,stack_add_pre,cost2x,not_better_than_hand_rule,hold |
| CLC_1530_y_a_T1600_p60 | T | 156 | -950 | -0.05 | -950 [-2,916] | -555 | DEAD | mean_up,stack_add_pre,cost2x,not_better_than_hand_rule,hold |
| CLC_1550_y_a_F30_p55 | M | 448 | -527 | -0.02 | -527 [-2,626] | -2,443 | DEAD | mean_up,stack_add_pre,cost2x,hold |
| CLC_1550_y_a_F30_p55 | T | 448 | -1,579 | -0.11 | -1,579 [-3,601] | -2,158 | DEAD | mean_up,stack_add_pre,cost2x,hold |
| CLC_1550_y_a_F30_p60 | M | 221 | -786 | -0.04 | -786 [-2,262] | -773 | DEAD | mean_up,stack_add_pre,cost2x,hold |
| CLC_1550_y_a_F30_p60 | T | 221 | -1,480 | -0.09 | -1,480 [-2,727] | -1,054 | DEAD | mean_up,stack_add_pre,cost2x,hold |
| CLC_1550_y_a_T1600_p55 | M | 448 | -1,593 | -0.11 | -1,593 [-4,684] | -3,752 | DEAD | mean_up,stack_add_pre,cost2x,hold |
| CLC_1550_y_a_T1600_p55 | T | 448 | -2,096 | -0.13 | -2,096 [-4,705] | -4,246 | DEAD | mean_up,stack_add_pre,cost2x,hold |
| CLC_1550_y_a_T1600_p60 | M | 221 | -1,780 | -0.11 | -1,780 [-4,327] | -877 | DEAD | mean_up,stack_add_pre,cost2x,hold |
| CLC_1550_y_a_T1600_p60 | T | 221 | -1,853 | -0.11 | -1,853 [-4,166] | -986 | DEAD | mean_up,stack_add_pre,cost2x,hold |
| CLC_1530_y_o_H0930_p55 | M | 589 | +931 | +0.02 | +931 [-5,942] | +4,964 | DEAD | stack_add_pre,cost2x |
| CLC_1530_y_o_H0930_p55 | T | 589 | +890 | +0.01 | +890 [-6,014] | +4,481 | DEAD | stack_add_pre,hold |
| CLC_1530_y_o_H0930_p60 | M | 273 | +2,804 | +0.13 | +2,804 [-2,620] | +177 | DEAD | stack_add_pre,hold |
| CLC_1530_y_o_H0930_p60 | T | 273 | +2,749 | +0.12 | +2,749 [-2,658] | -131 | DEAD | stack_add_pre,hold |
| CLC_1550_y_o_H0930_p55 | M | 543 | +4,132 | +0.20 | +4,132 [-3,109] | +3,597 | DEAD | stack_add_pre |
| CLC_1550_y_o_H0930_p55 | T | 543 | +4,445 | +0.16 | +4,445 [-2,325] | +3,403 | DEAD | stack_add_pre |
| CLC_1550_y_o_H0930_p60 | M | 314 | +4,572 | +0.25 | +4,572 [-1,011] | +2,697 | DEAD | stack_add_pre |
| CLC_1550_y_o_H0930_p60 | T | 314 | +3,382 | +0.16 | +3,382 [-1,649] | +2,006 | DEAD | stack_add_pre |

## 7. Cross-instrument and overnight tables
Other instruments at their own closes (conservative 1-min-bar fills, R6k, no locks, WEAK fee labels; 96 cells all DEAD):
| instrument | family | n | trades/wk | brackets beating (b) (of 6) | best d Sharpe WF | best d mean $/wk |
|---|---|---|---|---|---|---|
| 6E | CN | 412 | 2.25 | 0 | -0.01 | -102 |
| 6E | RV | 561 | 2.91 | 0 | -0.04 | -771 |
| CL | CN | 447 | 2.39 | 0 | -0.00 | -31 |
| CL | RV | 610 | 3.12 | 2 | +0.01 | +267 |
| ES | CN | 438 | 2.39 | 0 | -0.00 | -26 |
| ES | RV | 630 | 3.31 | 6 | +0.05 | +1,155 |
| GC | CN | 446 | 2.36 | 0 | -0.00 | -54 |
| GC | RV | 563 | 2.90 | 0 | +0.02 | -32 |
| RTY | CN | 434 | 2.33 | 0 | +0.00 | +32 |
| RTY | RV | 608 | 3.13 | 6 | +0.02 | +448 |
| SI | CN | 441 | 2.37 | 0 | -0.01 | -189 |
| SI | RV | 561 | 2.88 | 0 | -0.02 | -127 |
| YM | CN | 439 | 2.42 | 0 | +0.00 | +91 |
| YM | RV | 593 | 3.08 | 6 | +0.06 | +1,243 |
| ZN | CN | 438 | 2.37 | 1 | -0.01 | -131 |
| ZN | RV | 596 | 3.09 | 0 | -0.18 | -3,247 |
Pooled US-equity-index VWAP-reversion sleeve (NQ RVW1|F30 + ES / YM / RTY RV|B10, prereg POOL, ONE cell): WF stack-add d mean +$4,260/wk (PRE +$6,280 [CI 961, 12,565], HOLD +$1,969, 2023-04..2024-01 $-744), d Sharpe WF +0.19, d maxDD WF +20,406 (PRE -48,020), MDE $5,731; pooled own WF mean $4,260/wk SD $24,391 maxDD $203,405; pooled (b) placebo (64 draws, no locks) effect +$11,016/wk rank 1.00 CI [5,347, 16,936]; 2x-cost HOLD $-2,605; by year 2024: $2,231, 2025: $7,170, 2026: $2,752; year share 0.63; failed gates ['year_share', 'span2']; day-block bootstrap maxDD change WF mean -33,539 CI [-202,542, 104,724], P(worse) 0.33. Verdict: DEAD (year share 0.63 > .60 and 2023-24 negative; weak-fee cap would apply anyway). Component weekly correlations: NQ-ES 0.50, NQ-YM 0.29, NQ-RTY 0.39, ES-YM 0.70, ES-RTY 0.55, YM-RTY 0.63; pooled vs live books: ST -0.06, HM +0.04, WT +0.00, KB -0.04, SM +0.15, PB -0.06, PS -0.04, K4 -0.14, live_stack -0.00.
Overnight holds (H1805 / H0930), best six by stack-add d Sharpe: 
| cell | verdict | d Sharpe WF | d mean $/wk | MDE | failed gates |
|---|---|---|---|---|---|
| PC15|H0930 (B2) | DEAD | +0.22 | +5,886 | 9,794 | beats_b,beats_beta,stack_add_pre,year_share,best_of_N |
| F2|H0930 (B3) | DEAD | +0.19 | +5,189 | 7,861 | beats_b,beats_beta,stack_add_pre,span2,best_of_N |
| RSI2D|H1805 (B2) | DEAD | +0.13 | +2,759 | 4,595 | beats_b,beats_beta,stack_add_pre,span2,best_of_N | T: beats_b,beats_beta,stack_add_pre,year_share,span2,best_of_N |
| MOC10|H0930 (B1) | DEAD | +0.11 | +4,132 | 7,593 | beats_b,beats_beta,stack_add_pre,year_share,hold,span2,best_of_N |
| CTR|H0930 (B1) | DEAD | +0.09 | +2,628 | 5,947 | beats_b,beats_beta,stack_add_pre,year_share,best_of_N |
| RSI2D|H0930 (B2) | DEAD | +0.07 | +3,873 | 9,043 | beats_b,beats_beta,stack_add_pre,year_share,span2,best_of_N |
K4 overlap: weekly correlation of the overnight cells with the K4 base series is -0.09 to +0.07 (see robustness table); K4 holds overnight from 16:17, so any overnight close cell would add to K4's overnight exposure: margin step-up from intraday to overnight is NOT verified on disk (T4 reports assume about $22,000 per NQ contract initial overnight margin, unverified) => 10 lots overnight = about $220,000 margin (assumption). Gap risk: worst 16:15 -> 18:05 move in the sample is -995.8 pts (up +387.5; 1st / 99th percentile -128 / +194 pts, 733 days) = -$199,000 per 10 lots.
## 8. Fill cost by second and capacity
Strict round-trip points (spread + both-side impact), median over days, by clip size:
| lots | 15:30:00 | 15:50:00 | 15:58:00 | 16:00:00 | 16:00:01 | 16:05:00 | 16:10:00 |
|---|---|---|---|---|---|---|---|
| 1 | 0.75 | 1.00 | 0.75 | 0.75 | 0.75 | 0.75 | 0.75 |
| 5 | 0.75 | 1.25 | 0.75 | 0.75 | 0.75 | 0.75 | 0.75 |
| 10 | 1.00 | 2.25 | 1.00 | 1.25 | 1.25 | 1.38 | 1.38 |
| 20 | 2.00 | 4.00 | 2.00 | 2.00 | 2.00 | 2.25 | 2.25 |
| 40 | 3.50 | 6.75 | 3.50 | 3.50 | 3.50 | 3.50 | 3.50 |
Capacity (largest clip in {1,5,10,20,40} with extra RT cost <= half the RVW1|F30 edge): 20 lots at 15:30 and 16:00 on the M edge (2.95 pts), 10 lots on the quote-based T edge (2.23 pts). The closing-book depth at 16:00:01-16:10 is not thinner than at 15:58 in the medians.
## 9. Power per family (blocks 1-3 NQ cells; PRE = 2024-02..2025-06, 74 weeks)
| family | signals | PRE trades min / median / max | weekly paired MDE $/wk (min / median over cells) |
|---|---|---|---|
| 3.1 | 6 | 5 / 150 / 248 | 300 / 1,669 |
| 3.10 | 3 | 38 / 92 / 110 | 492 / 1,004 |
| 3.2 | 5 | 1 / 105 / 119 | 169 / 2,417 |
| 3.3 | 6 | 1 / 38 / 234 | 169 / 1,408 |
| 3.4 | 6 | 14 / 236 / 300 | 370 / 2,418 |
| 3.5 | 6 | 4 / 78 / 201 | 189 / 1,239 |
| 3.6 | 3 | 37 / 274 / 293 | 1,182 / 3,457 |
| 3.7 | 3 | 16 / 96 / 109 | 526 / 2,006 |
| 3.8 | 8 | 4 / 134 / 211 | 324 / 2,446 |
| 3.9 | 4 | 29 / 84 / 181 | 682 / 1,852 |
Per-trade MDE vs zero on 15-60 pt brackets is 3-15 pts (prereg tables): nulls mean "could not see an effect smaller than the MDE", not "no effect". Even the RVW1 stack-add (~$2.1k/wk) is below its weekly MDE ($2.25k).
## 10. Robustness block on the top 10 by stack-add (regardless of verdict; both bases; concurrency, correlations, bootstrap, cost, mirror, by year, VIX)
| cell | basis | d mean WF | MDE | d Sharpe | d maxDD | P(maxDD worse) day-block bootstrap | max |corr| to a live book / K4 | share of entries with stack open + cell > 50 lots | 2x-cost HOLD | mirror PRE | by year (WF) | VIX terc 0/1/2 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F2|H0930 | M | +5,779 | 7,861 | +0.20 | -13,506 | 0.40 | 0.14 / -0.07 | 0.10 | +6,628 | +877 | 2024:5686 2025:3817 2026:8089 | 0:7970 1:2446 2:5905 |
| F2|H0930 | T | +5,189 | 7,533 | +0.19 | -19,564 | 0.41 | 0.11 / -0.04 | 0.10 | +6,246 | +1,703 | 2024:4511 2025:3810 2026:7472 | 0:7283 1:5021 2:2967 |
| MOC10|H0930 | M | +4,175 | 7,490 | +0.12 | -18,102 | 0.46 | 0.17 / +0.02 | 0.04 | +1,151 | -663 | 2024:3106 2025:8099 2026:270 | 0:1925 1:2470 2:8021 |
| MOC10|H0930 | T | +4,132 | 7,593 | +0.11 | -18,302 | 0.46 | 0.16 / +0.02 | 0.04 | +839 | -1,714 | 2024:3479 2025:7743 2026:140 | 0:1997 1:2478 2:7811 |
| MOC10|NOSTOP | M | +2,351 | 2,754 | +0.13 | -11,942 | 0.24 | 0.16 / -0.00 | 0.04 | +663 | -4,889 | 2024:2408 2025:1591 2026:3131 | 0:744 1:3942 2:2919 |
| MOC10|NOSTOP | T | +2,579 | 2,758 | +0.14 | -13,355 | 0.22 | 0.16 / -0.00 | 0.04 | +1,166 | -4,493 | 2024:2258 2025:2483 2026:2950 | 0:826 1:4132 2:3341 |
| MOC10|T1600 | M | +1,966 | 2,746 | +0.12 | -11,942 | 0.24 | 0.20 / +0.03 | 0.04 | +809 | -3,585 | 2024:1657 2025:1014 2026:3435 | 0:466 1:3970 2:2096 |
| MOC10|T1600 | T | +2,141 | 2,756 | +0.12 | -13,355 | 0.23 | 0.19 / +0.02 | 0.04 | +1,247 | -3,326 | 2024:1495 2025:1787 2026:3240 | 0:502 1:4128 2:2440 |
| MOC5|NOSTOP | M | +2,046 | 3,268 | +0.13 | -13,477 | 0.25 | 0.15 / -0.05 | 0.07 | -113 | -5,216 | 2024:2125 2025:837 2026:3381 | 0:1092 1:2257 2:2952 |
| MOC5|NOSTOP | T | +2,388 | 3,270 | +0.15 | -16,463 | 0.23 | 0.14 / -0.05 | 0.07 | +817 | -4,642 | 2024:1917 2025:2174 2026:3094 | 0:1328 1:2591 2:3420 |
| MOC5|T1600 | M | +1,754 | 3,276 | +0.12 | -13,477 | 0.25 | 0.22 / -0.01 | 0.07 | +48 | -3,695 | 2024:1470 2025:401 2026:3708 | 0:839 1:2500 2:2202 |
| MOC5|T1600 | T | +2,047 | 3,280 | +0.13 | -16,463 | 0.23 | 0.21 / -0.01 | 0.07 | +919 | -3,285 | 2024:1270 2025:1601 2026:3418 | 0:1032 1:2787 2:2612 |
| PC15|H0930 | M | +6,638 | 9,794 | +0.25 | +46,691 | 0.48 | 0.09 / -0.09 | 0.05 | +7,024 | +1,487 | 2024:5178 2025:-1958 2026:18872 | 0:2352 1:6409 2:11625 |
| PC15|H0930 | T | +5,886 | 9,639 | +0.22 | +45,982 | 0.50 | 0.09 / -0.09 | 0.05 | +6,271 | +1,410 | 2024:4203 2025:-1765 2026:17223 | 0:1186 1:6122 2:10978 |
| RSI2D|H1805 | M | +2,759 | 4,595 | +0.13 | -1,430 | 0.43 | 0.11 / +0.03 | 0.08 | +1,964 | -3,829 | 2024:1409 2025:3773 2026:2922 | 0:4140 1:904 2:2647 |
| RSI2D|H1805 | T | +2,799 | 4,275 | +0.15 | -2,811 | 0.37 | 0.13 / +0.07 | 0.08 | +1,255 | -4,106 | 2024:1394 2025:5571 2026:807 | 0:2060 1:2166 2:4119 |
| RVW1|NOSTOP | M | +3,654 | 4,782 | +0.16 | -4,275 | 0.36 | 0.13 / -0.13 | 0.11 | +1,758 | -5,062 | 2024:300 2025:6752 2026:3483 | 0:3215 1:1434 2:5869 |
| RVW1|NOSTOP | T | +3,109 | 4,781 | +0.13 | -4,614 | 0.37 | 0.12 / -0.11 | 0.11 | +2,015 | -3,456 | 2024:-409 2025:6671 2026:2569 | 0:2923 1:901 2:5029 |
| RVW1|T1600 | M | +3,844 | 4,194 | +0.18 | -4,275 | 0.32 | 0.10 / -0.05 | 0.11 | +1,177 | -3,540 | 2024:1412 2025:7090 2026:2402 | 0:2792 1:2670 2:5936 |
| RVW1|T1600 | T | +3,086 | 4,259 | +0.13 | -4,614 | 0.36 | 0.09 / -0.04 | 0.11 | +1,214 | -2,540 | 2024:598 2025:6735 2026:1237 | 0:2197 1:1726 2:5138 |

## 11. Deviations, disclosures, and what was NOT done
1. Harness `o2_run.cell_gates` min_n gate was added by an agent other than D3CL1 (author not recorded; file mtime 2026-10-27T23:20:41Z; DECISIONS.md carries the disclosure); block 1 was scored before it. Harness primary unchanged throughout; the per-class null is a SEPARATE secondary column (c3_secondary.py), computed over cells with >= 100 PRE trades and >= 64 draws.
2. Block-2 placebo-(b) double-shift bug for 9 scan-type signals found and fixed (details in DS3_CLOSE_BLOCK2.md); block-1 text corrected for a substring count slip (27 of 402 cell-bases beat (b)); one correction in DECISIONS.md (RVW1 PRE trades 234, not 248).
3. Prereg slips: CL19-26 text says 168 cells (actual 180). The classifier AUC/permutation (PRE) were read before the CLC prereg was hashed (no skill, disclosed in the prereg). Grid selection (top 3 per family) used PRE-stage d Sharpe only.
4. Grid: 1,134 prereg'd cells, 1,092 scored (42 empty: post-close signals with no valid exits at 16:14 etc.), one logged look per group (54) and per other group; every holdout look logged before the HOLD column was read.
5. Not done: range / Renko / tick / dollar / 15-s footprint bars; resting-limit and MOC-equivalent exits for families other than RVW1; latency 5 / 50 / 150 ms (below the 1-s path resolution, bounded by the 1-5 s delays); mega-cap earnings reaction beyond EARN05 (n=93, EDGAR coverage ends 2026-10-15); stop-entry for the non-break families; the Friday-to-Monday variants; the 15-s footprint and stacked-imbalance triggers (tick tape exists only 15:45-16:15); the real MOC imbalance cells (feed not on disk, NEEDS.md); the 15:30 quote-fill check was done only for RVW1 (variant Q).
6. Other-instrument books: no lock engine, R6k sizing, no poison audit of c3_xi (trigger reads bars < anchor by construction), WEAK fee labels (RTY YM CL GC SI ZN = ES 4.84; 6E 5.30).
7. UNTOUCHED never read; no downloads; memory gate (32 GB) and corepool respected; no worker kills or retries; no deletions (superseded files kept with _bak / _v1 suffixes); no credentials added; no live, chart or execution-server change.
## 12. Files
Reports: autopilot/DS3_CLOSE_BLOCK1.md, DS3_CLOSE_BLOCK2.md, DS3_CLOSE_BLOCK3.md, DS3_CLOSE_FINAL.md, DS3_SPEC_RVW1_F30.md (v2). Preregs: l2vast/ds3/prereg/TCLOSE_B1_*, B2_*, B3_*, B4_* (hashes in DECISIONS.md). Code: l2vast/ds3/code/close3/. Results: l2vast/ds3/out/tclose_b1/ (cells_all.csv = every cell-basis with primary and secondary verdicts; cells_all_cellLevel.csv; top15_all.csv; robust_top10.csv; classnull_all.json; pool_result.pkl; exec_rvw1_*.csv; fillcost_by_second.csv; predcls_*.json), per-variant pickles out/topen_b2/grp_TCLOSE_B*.
