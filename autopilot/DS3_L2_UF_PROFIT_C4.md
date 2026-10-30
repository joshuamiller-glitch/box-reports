# DS3_L2_UF_PROFIT_C4 - PROFIT side, cycle 4 (widen / hold-longer, exact lock engine from the start) - STRUCTURE, per contract (UF-PROFIT, 2026-10-30)
Research only; UNTOUCHED never read. Masks 2026=20260101..0206, L6M=20250801..0206, HOLD=20250701..0206, PRE=20240201..20250630, X'=20230401..20240131. Prereg l2vast/ds3/prereg/UF_PROFIT_C4_prereg.md (sha256 in DECISIONS.md, written before any cell was run); stack-level SEL selection sha256 c86d1fae5327a16bf2764b3395af1b848a80b31bf06e397c206badc2b729d436 logged before the one recent look. Cells 190 (168 selectable, 120 with trade-level fires PRE>=200 / X'>=50) + 2 walk-forward chains. Day-level levels per DS3_CAUSAL_TIMES.md (PDH/PDL prior label day; ONH/ONL only from 09:30 ET); path scan capped at the book flatten time (16:54:59 ET / early close). dead_lookup: 24 exact repeats of cycle-3 widen cells kept on purpose (new engine), rest new.
**Per the 2026-10-30 addendum:** the primary number is pts per trade PER CONTRACT vs hold-to-bracket (the trade-level columns below are per contract; the N6060 sub-column restricts to books with a 60/60 bracket), stack $/wk is secondary. Widening a target and replacing a target by a trailing stop are fixed-distance structure, not L2 edge; this cycle is reported as STRUCTURE and the book enters only as the trigger. A trigger is an information edge only if the book-conditioned cell beats a placebo with the same action AND is >= 0 per contract; neither holds.

## Verdict
**Null. 0 of 120 fire-eligible cells is >= 0 on the exact lock-engine stack (N and LIVE-CAL) in PRE and X' separately; weekly-stack RC on SEL p = 1.00; recent cycle RC (L6M weekly stack) p = 0.53, HOLD 0.49 (best cell t +2.3 over 120 cells, 108 effective clusters); candidate raw p 0.78; cumulative-adjusted (Sidak over 147,454 + 192) p = 1.00.** Path-only widen/trail controls are strongly negative on both the trade level and the stack (trail 20-40 after 70% of target: -1.4 to -2.8 pts per contract in L6M on N, -30k to -47k/wk in the stack); the book-conditioned versions lose less only because they fire on 2-10% of the trades. Walk-forward 6/12 months over distance, level, thin-ahead definition and confirm: inactive or noise (L6M N 0.00 to -0.02 per contract with MDE 0.3-0.5; PRE -0.37 / -0.60).

## Settings table (recent first; per contract N and LIVE-CAL, MDE in brackets; 1-lot $/trade = 20 x pts; stack secondary)
| role | cell | tier / label | 2026 N | L6M N | L6M LIVE | L6M N 60/60 books | L6M $/trade N | HOLD N | PRE N | X' N | fires L6M | stack N / LIVE L6M $/wk (MDE) | stack PRE / X' | placebo ranks L6M N: P1 causal Bernoulli / P3 shifted / P2 shuffled-day |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CYCLE CANDIDATE (best min-z; none eligible) | `UFP4|B1trail|W|hour_ahead_le0.5|esimb|pct0.7|trail30` | STRUCTURE; BEST-AVAILABLE-NEGATIVE | +0.04 (0.80) | -0.49 (0.57) | -0.59 | -0.53 (0.66) | -9.78 | -0.41 (0.52) | -0.21 (0.27) | +0.01 (0.24) | 742 | -6.4k / -11.9k (23k) | -2.3k / +2.3k | 0.24 / 0.95 / 0.00 |
| family best A1 (widen) | `UFP4|A1widen|W|z_ahead_le-1.0|queue|pct0.7|lvlpdon` | STRUCTURE; BEST-AVAILABLE-NEGATIVE | -1.34 (2.16) | -0.01 (0.77) | -0.03 | +0.07 (0.81) | -0.28 | +0.04 (0.71) | -0.34 (0.46) | +0.24 (0.70) | 546 | +1.7k / +0.8k (24k) | -3.9k / +0.9k | 0.06 / 0.38 / 0.57 |
| other family cell | `UFP4|B1trail|W|hour_ahead_le0.5|esret|pct0.7|trail30` | STRUCTURE; BEST-AVAILABLE-NEGATIVE | +0.01 (0.62) | -0.33 (0.33) | -0.38 | -0.40 (0.40) | -6.53 | -0.29 (0.30) | -0.11 (0.18) | -0.04 (0.12) | 367 | -4.8k / -7.6k (13k) | -1.9k / +0.2k | n/a |
| other family cell | `UFP4|B1trail|W|z_ahead_le-1.0|esret_queue|pct0.85|trail40` | STRUCTURE; BEST-AVAILABLE-NEGATIVE | -0.10 (0.42) | -0.14 (0.26) | -0.17 | -0.16 (0.28) | -2.80 | -0.13 (0.23) | +0.01 (0.15) | -0.03 (0.11) | 249 | -3.3k / -5.2k (16k) | -1.5k / -0.6k | n/a |
| chain | `CH4_6m` | STRUCTURE; BEST-AVAILABLE-NEGATIVE | -0.37 (0.85) | -0.02 (0.53) | -0.03 | -0.05 (0.64) | -0.30 | -0.01 (0.48) | -0.60 (0.74) | -0.16 (0.44) | 518 | -2.6k / -3.3k (10k) | -23.7k / -5.9k | n/a |
| chain | `CH4_12m` | STRUCTURE; BEST-AVAILABLE-NEGATIVE | -0.04 (1.34) | +0.00 (0.33) | -0.00 | +0.02 (0.36) | +0.07 | +0.00 (0.30) | -0.37 (0.61) | -0.16 (0.44) | 275 | -4.1k / -4.4k (10k) | -20.7k / -5.9k | n/a |

Stack P1 (12 draws of a causal random trigger at the real rate through the lock engine, candidate action): real stack delta rank vs random in L6M 0.67, HOLD 1.00, PRE 1.00, X' 1.00 (random triggers at the same rate lose -3k to -21k/wk in the stack, so the real cell is 'less bad than random', not good). Placebo detail: candidate P3 (shifted within trade) ranks SEL/L6M/HOLD 1.00, 0.95, 0.98; P1 0.80, 0.24, 0.70; P2 0.00, 0.00, 0.00. The book-conditioned trail loses less than a trail at times shifted within the same trades (the thin-ahead + ES-book state does mark better moments than random timing), but it is negative per contract in L6M/HOLD/PRE (-0.49/-0.41/-0.21) and worse than a random same-rate trigger and than a shuffled-day book in 2 of 3 comparisons: not an information edge.

## Path-only and reduced-book controls (pure structure), per contract N, L6M (MDE) | PRE | stack L6M $/wk
| control | L6M N | PRE N | X' N | stack L6M | stack PRE |
|---|---|---|---|---|---|
| `ALL|pct0.7|lvlrnd50` | -0.13 (1.93) | -0.45 (1.38) | -1.05 (2.16) | -27.1k | -17.7k |
| `ALL|pct0.85|lvlrnd50` | +0.16 (1.77) | -0.37 (1.21) | -0.92 (2.04) | -22.3k | -17.2k |
| `ALL|pct0.7|lvlrnd100` | -0.52 (2.30) | -0.42 (1.59) | -0.14 (2.50) | -13.2k | -25.9k |
| `ALL|pct0.85|lvlrnd100` | -0.15 (2.02) | -0.41 (1.37) | +0.01 (2.33) | -15.2k | -27.3k |
| `ALL|pct0.7|lvlpdon` | -0.19 (1.30) | -0.59 (0.83) | -0.48 (1.49) | -1.5k | -5.7k |
| `ALL|pct0.85|lvlpdon` | -0.00 (1.08) | -0.50 (0.75) | -0.37 (1.36) | +3.6k | -6.6k |
| `ALL|pct0.7|lvlany` | -0.20 (1.81) | -0.37 (1.34) | -1.02 (2.09) | -21.9k | -19.9k |
| `ALL|pct0.85|lvlany` | +0.07 (1.68) | -0.29 (1.17) | -0.88 (1.97) | -17.4k | -17.8k |
| `ALL|pct0.7|trail20` | -2.97 (1.29) | -1.67 (0.80) | -0.29 (1.09) | -45.3k | -43.2k |
| `ALL|pct0.85|trail20` | -2.03 (0.82) | -1.02 (0.55) | -0.50 (0.83) | -32.9k | -29.4k |
| `ALL|pct0.7|trail30` | -2.64 (1.86) | -1.38 (1.05) | -0.24 (1.57) | -47.3k | -36.7k |
| `ALL|pct0.85|trail30` | -1.66 (1.59) | -0.82 (0.87) | -0.38 (1.41) | -40.3k | -19.5k |
| `ALL|pct0.7|trail40` | -2.77 (2.05) | -1.65 (1.25) | +0.19 (2.53) | -36.3k | -43.3k |
| `ALL|pct0.85|trail40` | -1.87 (1.80) | -1.22 (1.05) | +0.12 (2.38) | -41.7k | -28.0k |
| `THIN|hour_ahead_le0.5|pct0.7|lvlany` | +0.08 (0.83) | -0.23 (0.55) | +0.05 (0.56) | -14.0k | -9.4k |
| `THIN|hour_ahead_le0.5|pct0.85|lvlany` | +0.12 (0.52) | -0.18 (0.33) | -0.03 (0.30) | -7.3k | -1.7k |
| `THIN|hour_ahead_le0.5|pct0.7|trail30` | -0.80 (0.65) | -0.49 (0.37) | -0.18 (0.40) | -5.0k | -6.8k |
| `THIN|hour_ahead_le0.5|pct0.85|trail30` | -0.42 (0.36) | -0.18 (0.18) | -0.13 (0.18) | -7.3k | -2.7k |
| `ESP|pct0.7|lvlany` | -0.25 (1.77) | -0.32 (1.24) | -0.35 (1.61) | -19.9k | -17.7k |
| `ESP|pct0.85|lvlany` | +0.17 (1.52) | -0.10 (0.99) | -0.28 (1.37) | -10.0k | -17.1k |
| `ESP|pct0.7|trail30` | -2.47 (1.73) | -1.21 (0.99) | -0.54 (1.28) | -45.6k | -31.9k |
| `ESP|pct0.85|trail30` | -1.29 (1.47) | -0.56 (0.74) | -0.36 (1.06) | -34.0k | -16.0k |
Reading: removing the target (any trail) and widening to a level without a book condition lose in every window; the stack penalty is large (target widening blocks the books' next signals: -13k..-27k/wk L6M for round-level widens, -30k..-47k for trails). THIN-only widen to 'any' level at 85% of target is +0.12 (MDE 0.52) in L6M but -0.18 in PRE, stack -7.3k. ES-price-only is negative in PRE.

## Walk-forward 6 / 12 months over extension distance, level definition, thin-ahead definition and confirm (168 cells, quarterly refits)
* CH4_6m: 20240101: W|z_ahead_le-1.0|queue|pct0.7|lvlrnd100; 20240401: W|z_ahead_le-1.0|queue|pct0.7|lvlrnd100; 20240701: W|z_ahead_le-1.0|tape|pct0.7|trail40; 20241001: W|z_ahead_le-1.0|tape|pct0.85|trail30; 20250101: W|z_ahead_le-1.0|esimb|pct0.7|lvlany; 20250401: W|z_ahead_le-1.0|esimb_tape|pct0.85|lvlrnd100; 20250701: W|hour_ahead_le0.5|esret|pct0.85|lvlrnd50; 20251001: W|z_ahead_le-1.0|esimb_tape|pct0.85|lvlrnd50; 20260101: W|z_ahead_le-1.0|esimb|pct0.85|lvlpdon
* CH4_12m: 20240101: W|z_ahead_le-1.0|queue|pct0.7|lvlrnd100; 20240401: W|z_ahead_le-1.0|queue|pct0.7|lvlrnd100; 20240701: W|z_ahead_le-1.0|esimb|pct0.7|lvlrnd100; 20241001: W|z_ahead_le-1.0|esret_queue|pct0.85|trail40; 20250101: W|z_ahead_le-1.0|esimb_tape|pct0.85|trail40; 20250401: W|hour_ahead_le0.5|esimb_tape|pct0.85|trail30; 20250701: W|hour_ahead_le0.5|esret|pct0.85|lvlany; 20251001: W|hour_ahead_le0.5|esret|pct0.85|lvlrnd50; 20260101: W|z_ahead_le-1.0|esret_queue|pct0.7|lvlrnd50
Chains: CH4_6m L6M N -0.02 (0.53), PRE -0.60 (0.74), stack L6M -2.6k, PRE -23.7k; CH4_12m L6M 0.00 (0.33), PRE -0.37, stack PRE -20.7k. The chosen cell changes every quarter between widen (rnd100/pdon/any) and trail families: no stable winner in the grid.

## Lock-engine stack lines (N, delta vs hold; LIVE adds the stop-class cost adjustment; $/wk, MDE in brackets; secondary)
* `UFP4|B1trail|W|hour_ahead_le0.5|esimb|pct0.7|trail30`: 2026 +7.3k / +2.7k (27k); L6M -6.4k / -11.9k (23k); HOLD -5.1k / -10.0k; PRE -2.3k / -6.9k; X' +2.3k / +1.4k
* `UFP4|A1widen|W|z_ahead_le-1.0|queue|pct0.7|lvlpdon`: 2026 -27.0k / -28.7k (37k); L6M +1.7k / +0.8k (24k); HOLD +2.7k / +2.0k; PRE -3.9k / -4.6k; X' +0.9k / +0.6k
* `UFP4|B1trail|W|hour_ahead_le0.5|esret|pct0.7|trail30`: 2026 +1.7k / -0.3k (27k); L6M -4.8k / -7.6k (13k); HOLD -4.2k / -6.7k; PRE -1.9k / -4.3k; X' +0.2k / -0.2k
* `UFP4|B1trail|W|z_ahead_le-1.0|esret_queue|pct0.85|trail40`: 2026 +11.6k / +10.1k (25k); L6M -3.3k / -5.2k (16k); HOLD -2.9k / -4.6k; PRE -1.5k / -2.7k; X' -0.6k / -0.8k
* `CH4_6m`: 2026 -3.2k / -3.7k (6k); L6M -2.6k / -3.3k (10k); HOLD -2.2k / -2.8k; PRE -23.7k / -33.0k; X' -5.9k / -6.1k
* `CH4_12m`: 2026 -4.2k / -5.3k (43k); L6M -4.1k / -4.4k (10k); HOLD -3.6k / -3.9k; PRE -20.7k / -23.4k; X' -5.9k / -6.1k

## Sessions / books (per contract, N, L6M | SEL; MDE) for the candidate
sessions: asia -0.18 (1.37, f281) | -0.40; london -1.36 (1.20, f217) | -0.17; pre -0.08 (1.36, f24) | -0.32; nyam -0.30 (0.52, f112) | +0.08; nypm -0.34 (0.68, f107) | -0.13; close -0.91 (2.54, f1) | +2.09
books: ST -0.21 (1.06); HM -0.41 (0.95); WT -0.31 (0.49); KB -0.40 (1.15); SM -0.41 (1.64); PE -0.68 (1.04); PB -0.66 (1.09); DN -0.57 (1.02); MV -0.90 (1.05); MA -0.40 (1.80)

## PROFIT side exhausted on mbp-10 + 1-s aggregates (summary for the lead)
Four cycles, 1,019 profit cells + walk-forward models: single book states as reversal trigger (c1), book-with-the-trade vetoes, lean-before-the-extreme and the ES gate (c2), a 60-s trajectory model on 1-s add/cancel/OFI/imbalance aggregates with ES/RTY price divergence and widen-to-liquidity (c3), widen / trail-instead-of-target on the lock engine with PDH/PDL/ON/round levels (c4). Every cell is <= 0 per contract on N and LIVE-CAL out of sample once the structure (target removal, fixed trails, scale-out) is separated from the trigger, and the trigger beats a shifted or shuffled placebo in at most 1 of 3 comparisons. What mbp-10 (10 levels = about 2.5 pts) and the 1-s aggregates cannot see, and a raw-MBO pull would add:
1. **Queue position at the target**: a resting limit sell/buy at the bracket target is 130-240 ticks away, beyond the 10 visible levels; wall_tgt/wall_stop are finite in 0.05% of profit seconds. Needed: full-depth order-level book (MBO: add/cancel/modify/trade with order id, price, size, side, ts_event, sequence) for NQ so that the size ahead of a hypothetical order at the target (and at the stop) and its evolution can be reconstructed.
2. **Level age at the target**: time since the price level at the target/stop was created or last emptied, and the age of the orders resting there (needs order ids and first-seen times).
3. **Order lifetimes and fleeting-order share at the touch and 1-5 levels**: distribution of time between add and cancel per order (cancel bursts, spoof-like flickers) - the 1-s aggregates only give counts and sizes per bucket.
4. **Hidden / iceberg refill detail**: replenishment of the same price after trades (MBO trade-add sequences with order ids), which mbp-10 sees only as a size that reappears.
5. **Same four items for ES (and RTY if the cross-index confirm is kept)**, because the only weak positive signs of the program involved ES.
Dates: the selection/validation structure needs the same windows as here, on the in-trade seconds of the 44,385 static-bracket trades (entry_ts..closed_ts; ~195 M seconds): X' 2023-04-03..2024-01-31, PRE 2024-02-01..2025-06-30, HOLD/L6M 2025-07-01..2026-02-06 (UNTOUCHED, after 2026-02-06, not requested). If a smaller pull is necessary: first 2025-07-01..2026-02-06 (L6M/HOLD, the windows the stop condition judges) plus 2024-02-01..2025-06-30 (PRE, the selection window); X' last. Per-trade windows (entry-60 s .. exit) and the book around the target/stop price levels are enough; a full-day pull is not needed.

## Counts / multiplicity
Cells 190 + 2 chains = 192. n_effective = 108 (greedy clusters of weekly SEL stack deltas at corr < 0.95 over 120 fire-eligible selectable cells). N_cum = 147,454 + 192 = 147,646. Candidate L6M weekly-stack t = -0.79; best-cell t over the pool 2.34 (RC p 0.53); HOLD RC p 0.49; SEL RC p 1.00. Cumulative Sidak p = 1.00. DEAD_CELLS +190 (+2 chains); UF_TRIALS cycle 4 profit appended.

## Next (for the lead / INFO)
Cycle 5 should be built on the INFO in-profit information map (autopilot/DS3_L2_INFO.md), not on rules. From this program the only order-book state that marked better moments than random timing within the same trades is thin-ahead + ES book/price/queue with the trade (P3 rank 0.95-1.00 for the book-conditioned trail), which INFO can test directly as an IC/AUC against the shifted placebo.
