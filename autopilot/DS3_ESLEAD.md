# DS3_ESLEAD - follow-up section 2: ES-leads-NQ sizer / skip, D6-ready (agent ESL, 2026-10-31)

Research only. Prereg `l2vast/ds3/prereg/ESL_prereg.md` sha256 4927a639 (DECISIONS.md before any outcome statistic); PRE+X' selection file `out/eslead/selection_PRE_X.json` sha256 fdfc7c8a (logged before the recent look); ONE recent pass (stage 2), nothing re-selected after it. Code `l2vast/ds3/code/eslead/`, outputs `l2vast/ds3/out/eslead/` (all tables in `tables.md`), RECENT_WINS `out/recent_wins/eslead.csv` (2 rows, promote_ok False), UF_TRIALS side `followup_eslead`, DEAD_CELLS +558 rows (program ESL). Masks X' 20230401-20240131, PRE 20240201-20250630 (selection), HOLD 20250701-20260206, L6M 20250801-20260206, L3M 20251106-20260206, Y26 = 20260101-20260206 (ES exists to 2026-01-31 only: Y26 = January, 4-5 weeks, sign only). UNTOUCHED never read; ES dbn files after 2026-01 never opened. The N1 cell (lag_bp30 1.5 bp) was named post-hoc (label). Universe = TG-1 trend store, 44,370 signals (ENG6 = 29,800 = 237/wk). Bases: B2 = 70/30@3 (f73_N, PRIMARY), B1 = market at the signal (mkt_N). Stack = exact lock engine (stack2/tg_stack engine, six books ST HM WT KB SM PE, `$/wk` deltas vs the plain 70/30 stack, MDE = 2.8 x SE of the weekly delta). **Sizer multipliers are scored AS CODED (x1.5 / x0.5 unscaled, mean lot factor 0.96-0.99)** with the equal-risk-scaled line beside it, because part of N1's published stack gain is the leverage of the scale-up (below).

## PAGE 1 - VERDICT

**1. A null, and the N1 lead does not deepen: no PASS, no CANDIDATE-RECENT. The ES-leads-NQ sizer is a weak, post-hoc, delay-fragile LEAD with no per-lot edge and a negative increment on top of the ER sizer. Recommendation: OFF in D6 v2.3b (paper-log only, lots 0); do not add to the Sunday ON set.**

* **Per planned lot the rule is zero.** N1 cell (ES led NQ by >= 1.5 bp in 30 s -> x1.5, NQ led -> x0.5), B2: X' +0.02, PRE +0.05, HOLD -0.02, **L6M +0.01 (MDE 0.34)**, L3M +0.05, Y26 -0.22 pts per planned lot; per contract of final lots L6M +0.05. The PRE+X'-selected winner (ES-minus-NQ lag in ATR units, 30 s, 0.5; named by the prereg rule, not by me) is **-0.09 L6M / -0.08 HOLD** (MDE 0.38 / 0.36) despite +0.11 X' / +0.15 PRE. ES alone (ES move over 15/30/60 s in ticks or ATR, no NQ term): **0 of 72 es_z cells and 2 of 72 es_tk cells (a 1%-fire x0.5) carried PRE+X'**; every carried cell (20 of 312) contains NQ's own move through the lag term, and the NQ-own-reversed controls carry at the same rate (8 of 168 = 4.8% vs 20 of 312 = 6.4%). Program RC p 0.25 (studentised 0.45), PBO 0.35, cumulative Sidak 1.0.
* **Stack, as coded: positive on average, small, inside MDE in every window** (research lots, $/wk, planned-lot R): N1 cell B2 X' -3.2k, PRE +4.1k, HOLD +3.8k, **L6M +4.9k (MDE 17.3k)**, L3M +2.0k, Y26 -3.7k; B1 -0.3k / +2.4k / +2.2k / +1.2k / +0.3k / +0.4k. PRE+X' winner lag_z30 B2: +1.7k / +8.0k / +2.9k / **+5.9k (MDE 21.8k)** / -1.2k L3M / +13.5k Y26; the equal-risk B1 line reproduces N1's (X' +2.5k, PRE +0.8k, HOLD +4.6k, L6M +3.8k, 6/6 >= 0) **but a uniform x1.044 lot scalar (the equal-risk factor) gives +2.8k / -4.1k / +3.6k / +4.0k / +7.4k / +1.2k on the same windows: N1's "6/6 >= 0" on B1 is the leverage of un-cutting 3.6% of lots, not information.**
* **ES adds nothing beyond NQ's own move, and subtracts on top of the ER sizer.** Matched-fire-rate controls (same fav/adv shares, L6M, B2, stack): NQ-own-reversed move gives rm +0.10 and stack -10.1k vs the lag_z cell -0.09 / +5.9k; ES-only gives 0.00 / +1.4k. **ES increment over the ER(20) 5-min 1.5/0.5 sizer: lag_z30 sizer -8.8k L6M / -9.0k HOLD / -13.2k L3M (+6.6k PRE, -5.2k X'), N1 cell -10.7k / -8.4k / -11.1k (planned-lot R); sized-lot R -8.7k / -5.6k / -15.4k and -7.9k / -5.7k / -16.3k; skip -10.8k / -11.2k / -25.4k.** MDE ~20k, so inside noise but negative in all four recent windows.
* **Fragile to 1 s, 3 s and a 25% threshold change.** lag_z30 sizer stack L6M +5.9k -> +0.9k with the ES feed 1 s late -> -8.3k at 3 s late; threshold x0.75 -> -6.8k, x1.25 +4.6k; N1 cell B2 L6M +4.9k -> +3.5k (D1) -> -6.5k (D3), th x0.5 -7.6k. A genuine 30-s lead should not die with a 1-3 s stale feed; this argues that the stack sign is a lock-engine / sampling effect, not information.
* **Walk-forward chain (monthly re-fit, grid w 15/30/60 s x th, 3 re-fit modes): the chain abandons the 30-s cells for 60 s / 0.5.** Last re-fit (fit on trades closed before 2026-02-01, applies to Feb 2026; ES data end 2026-01-31): anchored / roll-12 / roll-6 all **w = 60 s, lag_z >= 0.5 -> x1.5, <= -0.5 -> x0.5** (trailing fit +0.11 / +0.18 / +0.16 pts per planned lot); lag_bp chain **w = 60 s, 0.5 bp**. Chain stack (z, roll-12): X' -2.3k, PRE +5.1k, HOLD +4.3k, L6M +8.2k, all-window **+2.8k (MDE 10.5k)**; the bp chain is negative on the stack (all-window -4.4k, HOLD -9.7k) though +0.37..+0.53 per planned lot in HOLD/L6M. Increment of the 60-s / chain versions over the ER sizer: -9.1k .. +5.3k L6M (MDE 15-19k), sign varies with the version and the governor R.
* **Placebos.** Time-shifted ES, 250 draws (shifts +-15, 30, 60, 120, 300, 900, 3600 s, +-1, 2, 3, 5, 7 days + random log-uniform / +-1..60 day), N1 cell B1: trade-level rank 184/251 L6M (real BELOW most draws; positive intraday shifts use future ES and are not nulls), stack L6M 80/251; on the causal-null subset (stale + day shifts, 172 draws): trade 105/172, stack L6M 21/172. lag_z30 sizer B2: trade rank 126/181 L6M, **stack 1/181 in PRE, HOLD, L6M and all-window** (X' 52/181); shuffled-day (ES from a random other day, same clock time, 200 draws): stack 1/201 (PRE, HOLD, ALL) and 3/201 L6M, trade 148/201. The stack rank-1 is NOT ES information: the mis-timed-ES placebos turn the sizer into a sizer on NQ's own move (the common market component no longer cancels), whose stack is -10k L6M by itself (control above); the clean ES-only control (+1.4k) is inside MDE. The shuffle/shift placebo that matters for information is the trade-level one: mid-pack to below.
* **Sessions: nothing stable.** lag_z30 sizer rm per planned lot L6M: Asia +0.03, London -0.25, NY-AM -0.17, NY-PM +0.12, pre-market -0.66 (PRE: +0.40 / +0.28 / -0.09 / +0.14 / +0.01); N1 cell L6M: -0.07 / +0.17 / +0.01 / +0.08 / -0.41 (PRE -0.02 / +0.20 / +0.16 / +0.12 / -0.21). Magnitude buckets (below) are not monotone and flip sign between X', PRE and HOLD.
* **Capacity: the NQ order size is the constraint on the lag_z version, not ES depth.** NQ contracts traded in the 10 s after the signal (all outright contracts; top-5 resting depth is NOT in the research tape): lag_z up-sized signals median 39 (p10 6), N1-cell up-sized signals median 322 (p10 42); live up-sized order mean 5.7, p90/max 10.5 lots (P6 7 x 1.5); 40% of lag_z up-sized live orders exceed 25% of the 10-s volume, 20% have < 10 contracts traded in 10 s (capacity 0.25 x median = 9.8 contracts: flagged); N1 cell 10% / 0% (capacity 80).

**2. D6 line (for the Sunday brief ON / SHADOW / OFF tables):**
`entry book KB(K6),PE(P6),SM(U6),HM(H6) [ST,WT research only] sizer es_lead(lag_z, w=30 s, ATR14 of 1-min bars, th=0.5) -> lotmult 1.5 if lag_z >= +0.5, 0.5 if lag_z <= -0.5, else 1.0` | tier **LEAD, post-hoc (PRE+X'-selected winner; N1 cell named post-hoc), weak** | failed gates: per-lot lift ~0 / negative in HOLD+L6M, stack inside MDE in every window, delay and threshold fragile, negative increment over the ER sizer, program RC p 0.25, X' placebo not distinguished | **OFF (log only)**. $/wk of the as-coded rule on the stack, **research lots / LIVE lots (K6 2, P6 7 Asia/London/NY-AM, U6=SM 4 Asia/London, H6=HM 4 Asia / 2 NY-AM, ST+WT research/2.35)**, planned-lot-R governors [sized-lot R in brackets], L6M / HOLD / PRE: lag_z30 sizer **+5.9k [+6.4k] / +2.9k [+6.1k] / +8.0k [+9.3k] research; +2.2k [+5.3k] / +1.7k [+6.1k] / +5.3k [+5.3k] live** (MDE L6M 21.8k [27.0k] research, 10.2k [12.7k] live; /2.35 mapping of research: +2.5k L6M); N1 cell B2 **+4.9k [-2.0k] / +3.8k [-2.4k] / +4.1k [+9.2k] research; +2.2k [-0.2k] / +1.6k [+0.1k] / +3.0k [+3.3k] live** (B1: +1.2k [-8.9k] / +2.2k [-6.3k] / +2.4k [+5.4k] research; -0.7k [-2.9k] / -0.1k [-1.5k] / +2.6k [+2.6k] live). The N1 "+$1.6k/wk live" (equal-risk B1, planned-lot R) is +3.8k/2.35; as coded at the real live lots B1 is **-0.7k** L6M.
**ES data granularity in D6 terms:** the 30-s rule needs ES and NQ prices at the decision second plus ATR(14) of 1-min bars; D6's ES 1-min series gives the ATR and the 1-min closes but NOT a 30-s window. Scored with the closest 1-min-bar forms of the same rule (window 60 s, lag_z, sizer, B2, stack L6M / HOLD / PRE / X'): 1-s data 60 s window **+11.4k / +9.3k / +3.1k / -6.7k**; last COMPLETED 1-min bar close-to-close (up to 59 s stale) **+1.0k / -0.2k / -2.2k / -2.3k**; second-to-last completed close to the FORMING bar (last completed bar + partial bar, window 60-119 s ending at the decision second) **+11.6k / +9.7k / +1.1k / -9.4k**. So **1-min closes alone do not suffice (the effect, such as it is, disappears); the forming bar (ES last price at the decision second, i.e. a 1-s-or-faster update, not sub-second ticks) is needed, and the 60-s form tolerates a 1-3 s late feed (D1 +5.8k, D3 +12.5k L6M) while the 30-s form does not.** Sub-second ticks were not scored (the ES series is 1-s last trade). All of these are inside MDE and X' is negative: this is a statement about what the data would have to look like if the rule were ever used, not support for using it.

**3. What the box could not do / caveats.** (i) Capacity: traded volume is a liquidity proxy, no resting depth; (ii) the ES 1-s series is last trade per second (ATR from last prices is slightly understated); ES 1-min mode bars are clock minutes; (iii) lag_z uses ATR scaled by sqrt(w/60); the N1 lag_bp definition is the plain bp difference (NQ beta > ES in bp: mean lag -0.33 bp) ; (iv) live-lot stack runs use the per-book / per-session live lots with governors scaled by the same ratio (sized-lot R: x the day's / week's largest multiplier of the book's kept rows - an interpretation of the user's spec for the week floor); ST and WT are not live, so research/2.35; K6 pre-market and every unlisted book-session = 0; integer rounding of x0.5 / x1.5 at live lots is NOT in the engine (table below); (v) prereg counted 522 stage-1 cells, the run scored 558 (312 selectable + 168 NQ-own controls + 78 skip-favourable controls a6); (vi) the first time-shift placebo draw set contains future-ES shifts, flagged and re-ranked; (vii) no sub-second ES, Feb 2026+ ES not read, so the last re-fit applies to a month the ES tape does not cover.

## Exact definition (what D6 would compute)

At the NQ signal second t (decision uses data up to t-1-D, D = feed delay), side s = +1 long / -1 short:
* ES move over w in {15, 30, 60} s: dE = ES(t-1-D) - ES(t-1-D-w) (front-month last trade, same contract at both ends, max staleness 300 s); in ES ticks: es_tk = s * dE / 0.25; in ATR units: es_z = s * dE / (ATR_ES * sqrt(w/60)), ATR_ES = mean true range of the last 14 COMPLETED 1-min ES bars.
* NQ move the same way: nq_bp, nq_z. Sign: + = moved WITH the NQ signal.
* Lead-lag: lag_bp = es_bp - nq_bp (N1: bp = move / price x 1e4); lag_z = es_z - nq_z. lag > 0: ES moved more in the signal direction than NQ (ES led).
* Rule: fav = lag >= th, adv = lag <= -th. Sizer: lots x1.5 on fav, x0.5 on adv, x1 otherwise (and x1 when ES is unknown); skip: adv -> no trade. Thresholds scored: es_tk 3 / 6 / 12, es_z 0.5 / 1 / 1.5, lag_bp 0.5 / 1 / 1.5 / 2.5, lag_z 0.25 / 0.5 / 0.75; windows 15 / 30 / 60 s; actions skip-adverse, sizer, x0.5-only, x1.5-only (+ skip-favourable as a control, not selectable).
* 1-min modes (ES and NQ both sampled at the same instants): M1c = close of the last completed 1-min bar minus the close of the bar before it (ends at the minute boundary, 0-59 s stale); M1f = price at the decision second minus the close of the second-to-last completed bar (last completed bar plus the forming bar, 60-119 s).

## Stage 1 (PRE + X' only, 558 cells; selection file sha fdfc7c8a)
312 selectable cells (13 thresholds x 3 windows x 4 actions x 2 bases): trade-level rate lift > 0 in both PRE and X' in 88, lock-engine stack >= 0 in both in 25, **both in 20 (6.4%)**; 168 NQ-own-reversed control cells: 104 / 10 / 8 (4.8%). Carried by family (a1 skip / a3 sizer / a5 x0.5 / a7 x1.5): es_tk 0/0/2/0, es_z 0/0/0/0, lag_bp 2/4/1/1, lag_z 3/4/3/0. Overall top by PRE+X' stack sum: a1 and a3 lag_z30 0.5 (B2, B1). Selected for the recent look: the 11 cells in the tables (N1 cell, PRE+X' winners sizer / skip / x0.5-only, family bests lag_bp30 1.0, lag_bp60 0.5 x1.5-only, es_tk30 12).

## Magnitude buckets (30-s window; excess pts per planned lot of the bucket vs all signals in the window; B2, all books; SE week-clustered, PRE SE ~1-2, L6M ~2-4 pts)
| lag_z30 bucket | share | X' | PRE | HOLD | L6M | L3M |
|---|---|---|---|---|---|---|
| < -0.75 | 4.5% | -2.3 | -3.6 | -3.3 | -2.9 | -7.9 |
| -0.75..-0.5 | 5.1% | -3.1 | +1.7 | +2.8 | +2.6 | +9.0 |
| -0.5..-0.25 | 13.4% | -0.1 | +0.8 | -0.1 | -0.1 | -0.0 |
| -0.25..+0.25 | 57.9% | +1.0 | -0.4 | +0.2 | +0.0 | -0.3 |
| +0.25..+0.5 | 11.7% | +1.2 | +0.0 | +0.5 | +1.3 | +2.5 |
| +0.5..+0.75 | 4.0% | -2.9 | +2.5 | -2.9 | -4.2 | -3.9 |
| > +0.75 | 3.4% | -1.1 | +3.8 | -2.1 | -1.0 | -2.2 |

| lag_bp30 bucket | share | X' | PRE | HOLD | L6M | L3M |
|---|---|---|---|---|---|---|
| < -2.5 | 5.7% | -2.8 | +2.0 | -3.5 | -3.8 | -2.6 |
| -2.5..-1.5 | 7.7% | -1.3 | -3.8 | -0.4 | -1.5 | -1.1 |
| -1.5..-0.5 | 24.9% | -1.1 | +0.7 | -0.6 | -0.5 | -0.0 |
| -0.5..+0.5 | 41.8% | +1.7 | -0.2 | +0.8 | +1.1 | +0.5 |
| +0.5..+1.5 | 14.7% | -0.8 | +1.2 | +1.5 | +1.0 | +1.2 |
| +1.5..+2.5 | 3.0% | -4.6 | +1.7 | -7.6 | -8.0 | -3.5 |
| > +2.5 | 2.0% | -0.7 | -6.9 | -4.0 | -5.2 | -3.0 |

ES alone (es_z30): ES moved WITH the signal by more than 1.5 ATR units (9.9% of signals) +0.7 PRE, +0.6 HOLD, +0.1 L6M, -4.3 X'; against by more than 1.5 (2.3%): +0.3 / -0.1 / -1.1 / -1.4. es_tk30 >= +12 ticks (8.7%): -1.7 PRE, -1.8 HOLD, -3.1 L6M, -13.3 X' (chasing a big ES move is worse than average, in every window). The top lag buckets (ES led by > 1.5 bp) lose in HOLD and L6M (-7.6 / -8.0) - the opposite of what the x1.5 sizer assumes; the buckets are not monotone and their signs flip between X', PRE and HOLD.

## Weekly stack statistics (B2, as coded, L6M / HOLD / PRE; mean $/wk, SD, maxDD, mean of the worst 20 weeks)
| | research lots L6M | HOLD | PRE | live lots L6M | HOLD | PRE |
|---|---|---|---|---|---|---|
| plain 70/30 | 72.1k, SD 139.7k, DD 261k, w20 +6.6k | 61.3k, 171.6k, 610k, -39.8k | 59.5k, 135.8k, 482k, -112.9k | 39.2k, 62.0k, 102k, +11.4k | 35.6k, 78.7k, 255k, -10.0k | 28.4k, 60.8k, 171k, -45.6k |
| + lag_z30 0.5 sizer | 78.0k, 144.9k, 269k, +10.0k | 64.2k, 173.8k, 626k, -42.0k | 67.5k, 139.3k, 410k, -104.9k | 41.4k, 60.4k, 93k, +15.2k | 37.3k, 77.3k, 256k, -6.8k | 33.7k, 64.4k, 151k, -41.5k |
| + N1 cell (lag_bp30 1.5) | 77.1k, 131.5k, 258k, +14.1k | 65.1k, 162.1k, 581k, -32.7k | 63.6k, 139.9k, 570k, -111.0k | 41.4k, 61.4k, 99k, +13.7k | 37.2k, 77.8k, 256k, -9.0k | 31.4k, 62.8k, 173k, -43.3k |

## Lots at the live book (integer rounding is NOT in the engine)
x1.5 / x0.5 of the live planned lot: K6 2 -> 3 / 1; P6 7 -> 10.5 / 3.5 (round half up 11 / 4: effective x1.57 / x0.57); U6 4 -> 6 / 2; H6 4 -> 6 / 2; H6 2 (NY-AM) -> 3 / 1. Units: per planned lot = the `rm` columns; per contract of final lots = `pc`; stack = $/wk. Signals changed per week on ENG6 (237/wk, L6M): N1 cell 7.8 up + 24.9 down; lag_z cell 14.5 up + 18.0 down; skip cell 18.0 skipped. Mean lot factor 0.964 (N1), 0.993 (lag_z).

## Bottom line for the brief
ES-leads-NQ: no PASS. Per-lot edge 0 (L6M +0.01 N1 / -0.09 lag_z), stack +4.9k / +5.9k L6M inside MDE 17-22k, negative increment on top of ER, fragile to a 1-s delay and a 25% threshold step, N1's 6/6 is leverage. Answer to the D6 question: 1-min closes are not enough, the forming bar at the decision second is the minimum, and the 60-s form tolerates a 3-s late feed; but there is nothing here worth building before Sunday. **Open question: none.**

---
# APPENDIX - all tables (generated, `out/eslead/tables.md`; cells are `action|feature+window_threshold|base`: a1 skip adverse, a3 sizer, a5 x0.5-only, a7 x1.5-only)

### Trade level: risk-matched lift per planned lot, (MDE) in brackets; pc = per contract of final lots (equal-risk); up/dn = share of signals x1.5 / x0.5 or skipped

| cell                 | rm X         | rm PRE       | rm HOLD      | rm L6M       | rm L3M       | rm Y26       |   pc L6M | up%/dn% L6M   |
|:---------------------|:-------------|:-------------|:-------------|:-------------|:-------------|:-------------|---------:|:--------------|
| a3|lag_z30_th0.5|B2  | +0.11 (0.42) | +0.15 (0.25) | -0.08 (0.36) | -0.09 (0.38) | -0.13 (0.45) | +0.07 (0.34) |    -0.05 | 6.1/7.6       |
| a3|lag_z30_th0.5|B1  | +0.11 (0.42) | +0.17 (0.25) | -0.07 (0.36) | -0.08 (0.39) | -0.14 (0.44) | +0.06 (0.32) |    -0.04 | 6.1/7.6       |
| a1|lag_z30_th0.5|B2  | +0.48 (0.64) | +0.09 (0.39) | -0.00 (0.64) | -0.01 (0.63) | -0.10 (0.67) | +0.21 (0.60) |    -0.12 | 0.0/7.6       |
| a1|lag_z30_th0.5|B1  | +0.49 (0.66) | +0.08 (0.38) | +0.01 (0.64) | -0.00 (0.64) | -0.13 (0.65) | +0.18 (0.57) |    -0.10 | 0.0/7.6       |
| a5|lag_z30_th0.5|B2  | +0.22 (0.29) | +0.04 (0.18) | -0.00 (0.31) | -0.00 (0.30) | -0.05 (0.32) | +0.10 (0.29) |    -0.06 | 0.0/7.6       |
| a3|lag_bp30_th1.5|B1 | +0.02 (0.42) | +0.05 (0.27) | +0.00 (0.31) | +0.03 (0.34) | +0.07 (0.45) | -0.19 (0.74) |     0.07 | 3.3/10.5      |
| a3|lag_bp30_th1.5|B2 | +0.02 (0.42) | +0.05 (0.26) | -0.02 (0.32) | +0.01 (0.34) | +0.05 (0.48) | -0.22 (0.75) |     0.05 | 3.3/10.5      |
| a3|lag_bp30_th1|B1   | +0.11 (0.49) | +0.11 (0.34) | +0.07 (0.43) | +0.08 (0.46) | +0.22 (0.61) | -0.20 (0.79) |     0.13 | 6.6/18.6      |
| a3|lag_bp30_th1|B2   | +0.11 (0.49) | +0.09 (0.33) | +0.02 (0.44) | +0.03 (0.47) | +0.19 (0.64) | -0.22 (0.85) |     0.07 | 6.6/18.6      |
| a7|lag_bp60_th0.5|B1 | +0.15 (0.34) | +0.03 (0.20) | +0.14 (0.24) | +0.10 (0.24) | +0.11 (0.35) | -0.18 (0.34) |    -0.04 | 14.3/0.0      |
| a5|es_tk30_th12|B2   | +0.02 (0.05) | +0.03 (0.07) | +0.04 (0.07) | +0.05 (0.08) | +0.07 (0.10) | +0.02 (0.12) |     0.02 | 0.0/1.0       |

### Stack delta $/wk vs plain 70/30 stack: research lots, governors on planned-lot R, as coded (unscaled 1.5/0.5)

| cell                 | X     | PRE   | HOLD   | L6M   | L3M    | Y26    | ALL   | MDE L6M   |
|:---------------------|:------|:------|:-------|:------|:-------|:-------|:------|:----------|
| a3|lag_z30_th0.5|B2  | +1.7k | +8.0k | +2.9k  | +5.9k | -1.2k  | +13.5k | +5.2k | 21.8k     |
| a3|lag_z30_th0.5|B1  | +0.5k | +8.6k | +3.3k  | +4.7k | +2.6k  | +18.3k | +5.2k | 23.6k     |
| a1|lag_z30_th0.5|B2  | +9.9k | +5.7k | -3.4k  | -1.7k | +4.1k  | +26.5k | +5.1k | 29.8k     |
| a1|lag_z30_th0.5|B1  | +7.9k | +2.2k | -6.3k  | -5.7k | -2.5k  | +17.0k | +2.1k | 29.5k     |
| a5|lag_z30_th0.5|B2  | +6.8k | +3.1k | -0.3k  | +3.2k | -0.2k  | +18.0k | +3.5k | 18.5k     |
| a3|lag_bp30_th1.5|B1 | -0.3k | +2.4k | +2.2k  | +1.2k | +0.3k  | +0.4k  | +1.6k | 17.8k     |
| a3|lag_bp30_th1.5|B2 | -3.2k | +4.1k | +3.8k  | +4.9k | +2.0k  | -3.7k  | +1.9k | 17.3k     |
| a3|lag_bp30_th1|B1   | -0.7k | +1.1k | +2.6k  | +3.3k | +12.7k | +17.2k | +0.9k | 27.3k     |
| a3|lag_bp30_th1|B2   | -2.6k | +2.6k | -4.1k  | -2.8k | +3.2k  | +1.5k  | -0.3k | 23.3k     |
| a7|lag_bp60_th0.5|B1 | +2.7k | +3.6k | +3.0k  | +3.8k | +14.2k | +2.1k  | +3.3k | 15.3k     |
| a5|es_tk30_th12|B2   | +0.4k | +0.7k | +2.7k  | +3.1k | +6.2k  | +5.9k  | +1.0k | 5.9k      |

### Stack delta $/wk vs plain 70/30 stack: research lots, planned-lot R, equal-risk scaled

| cell                 | X     | PRE   | HOLD   | L6M    | L3M    | Y26    | ALL   | MDE L6M   |
|:---------------------|:------|:------|:-------|:-------|:-------|:-------|:------|:----------|
| a3|lag_z30_th0.5|B2  | +1.6k | +8.0k | +2.5k  | +7.1k  | +1.4k  | +16.8k | +5.1k | 21.8k     |
| a3|lag_z30_th0.5|B1  | +1.8k | +5.8k | +3.7k  | +5.0k  | +6.5k  | +22.2k | +4.2k | 24.3k     |
| a1|lag_z30_th0.5|B2  | +9.9k | +5.7k | -3.4k  | -1.7k  | +4.1k  | +26.5k | +5.1k | 29.8k     |
| a1|lag_z30_th0.5|B1  | +7.9k | +2.2k | -6.3k  | -5.7k  | -2.5k  | +17.0k | +2.1k | 29.5k     |
| a5|lag_z30_th0.5|B2  | +7.8k | +1.7k | -1.7k  | +3.7k  | -0.1k  | +19.4k | +2.8k | 18.1k     |
| a3|lag_bp30_th1.5|B1 | +2.5k | +0.8k | +4.6k  | +3.8k  | +4.4k  | +0.4k  | +2.1k | 21.9k     |
| a3|lag_bp30_th1.5|B2 | +0.2k | +2.9k | +4.7k  | +6.7k  | +3.0k  | -4.2k  | +2.5k | 17.9k     |
| a3|lag_bp30_th1|B1   | +3.1k | +2.1k | +6.9k  | +8.4k  | +18.5k | +19.2k | +3.5k | 29.4k     |
| a3|lag_bp30_th1|B2   | +0.7k | +2.1k | -2.9k  | +0.2k  | +4.5k  | +10.9k | +0.6k | 24.2k     |
| a7|lag_bp60_th0.5|B1 | +3.4k | +0.8k | +10.3k | +10.7k | +19.7k | +43.5k | +3.6k | 27.2k     |
| a5|es_tk30_th12|B2   | +0.5k | +0.6k | +3.7k  | +3.9k  | +7.2k  | +6.2k  | +1.2k | 6.1k      |

### Stack delta $/wk vs plain 70/30 stack: research lots, governors x day/week largest multiplier (sized-lot R), as coded

| cell                 | X     | PRE   | HOLD   | L6M    | L3M    | Y26    | ALL   | MDE L6M   |
|:---------------------|:------|:------|:-------|:-------|:-------|:-------|:------|:----------|
| a3|lag_z30_th0.5|B2  | +3.1k | +9.3k | +6.1k  | +6.4k  | -7.0k  | +24.3k | +6.9k | 27.0k     |
| a3|lag_z30_th0.5|B1  | +2.1k | +7.0k | +6.6k  | +3.6k  | -7.5k  | +28.3k | +5.6k | 28.7k     |
| a1|lag_z30_th0.5|B2  | +9.9k | +5.7k | -3.4k  | -1.7k  | +4.1k  | +26.5k | +5.1k | 29.8k     |
| a1|lag_z30_th0.5|B1  | +7.9k | +2.2k | -6.3k  | -5.7k  | -2.5k  | +17.0k | +2.1k | 29.5k     |
| a5|lag_z30_th0.5|B2  | +6.8k | +3.1k | -0.3k  | +3.2k  | -0.2k  | +18.0k | +3.5k | 18.5k     |
| a3|lag_bp30_th1.5|B1 | -1.2k | +5.4k | -6.3k  | -8.9k  | -11.2k | +1.4k  | +1.0k | 20.9k     |
| a3|lag_bp30_th1.5|B2 | -3.9k | +9.2k | -2.4k  | -2.0k  | -5.6k  | +1.8k  | +3.0k | 20.2k     |
| a3|lag_bp30_th1|B1   | +1.7k | +4.4k | +5.2k  | +3.5k  | +6.7k  | +19.0k | +3.8k | 29.7k     |
| a3|lag_bp30_th1|B2   | +0.0k | +9.7k | +0.1k  | +0.3k  | -0.1k  | +1.7k  | +4.9k | 26.5k     |
| a7|lag_bp60_th0.5|B1 | +3.6k | +6.2k | +9.1k  | +13.2k | +13.2k | +23.0k | +6.1k | 24.6k     |
| a5|es_tk30_th12|B2   | +0.4k | +0.7k | +2.7k  | +3.1k  | +6.2k  | +5.9k  | +1.0k | 5.9k      |

### Stack delta $/wk vs plain 70/30 stack: LIVE lots (K6 2, P6 7, U6 4, H6 4/2, ST/WT /2.35), planned-lot R, as coded

| cell                 | X     | PRE   | HOLD   | L6M   | L3M   | Y26    | ALL   | MDE L6M   |
|:---------------------|:------|:------|:-------|:------|:------|:-------|:------|:----------|
| a3|lag_z30_th0.5|B2  | +2.3k | +5.3k | +1.7k  | +2.2k | +3.5k | +7.9k  | +3.7k | 10.2k     |
| a3|lag_z30_th0.5|B1  | +0.2k | +4.3k | +2.4k  | +3.0k | +3.6k | +10.0k | +2.7k | 11.7k     |
| a1|lag_z30_th0.5|B2  | +8.3k | +3.6k | -2.6k  | -2.8k | -0.4k | +9.1k  | +3.7k | 14.0k     |
| a1|lag_z30_th0.5|B1  | +7.4k | +2.4k | -3.9k  | -4.1k | -4.4k | +1.7k  | +2.6k | 14.7k     |
| a5|lag_z30_th0.5|B2  | +5.0k | +2.8k | +0.2k  | +0.8k | +1.4k | +9.1k  | +2.9k | 8.8k      |
| a3|lag_bp30_th1.5|B1 | -0.8k | +2.6k | -0.1k  | -0.7k | -1.0k | +3.5k  | +1.0k | 9.1k      |
| a3|lag_bp30_th1.5|B2 | -1.9k | +3.0k | +1.6k  | +2.2k | +2.0k | +3.4k  | +1.3k | 7.5k      |
| a3|lag_bp30_th1|B1   | +0.5k | +2.1k | +2.4k  | +2.8k | +4.4k | +12.9k | +1.7k | 13.1k     |
| a3|lag_bp30_th1|B2   | +0.4k | +2.7k | +0.9k  | +1.7k | +3.6k | +7.0k  | +1.7k | 10.4k     |
| a7|lag_bp60_th0.5|B1 | -0.3k | +4.2k | +3.4k  | +4.3k | +6.2k | -0.8k  | +2.8k | 5.1k      |
| a5|es_tk30_th12|B2   | -0.2k | +0.7k | +1.9k  | +2.2k | +4.5k | +9.1k  | +0.7k | 4.2k      |

### Stack delta $/wk vs plain 70/30 stack: LIVE lots, sized-lot R, as coded

| cell                 | X     | PRE   | HOLD   | L6M   | L3M   | Y26    | ALL   | MDE L6M   |
|:---------------------|:------|:------|:-------|:------|:------|:-------|:------|:----------|
| a3|lag_z30_th0.5|B2  | +3.5k | +5.3k | +6.1k  | +5.3k | +3.4k | +15.9k | +5.0k | 12.7k     |
| a3|lag_z30_th0.5|B1  | +3.1k | +4.4k | +6.6k  | +5.2k | +2.7k | +16.7k | +4.5k | 12.5k     |
| a1|lag_z30_th0.5|B2  | +8.3k | +3.6k | -2.6k  | -2.8k | -0.4k | +9.1k  | +3.7k | 14.0k     |
| a1|lag_z30_th0.5|B1  | +7.4k | +2.4k | -3.9k  | -4.1k | -4.4k | +1.7k  | +2.6k | 14.7k     |
| a5|lag_z30_th0.5|B2  | +5.1k | +2.9k | +0.3k  | +0.9k | +1.4k | +9.1k  | +3.0k | 8.8k      |
| a3|lag_bp30_th1.5|B1 | +1.0k | +2.6k | -1.5k  | -2.9k | -2.4k | +6.6k  | +1.3k | 9.6k      |
| a3|lag_bp30_th1.5|B2 | -0.5k | +3.3k | +0.1k  | -0.2k | -0.0k | +6.4k  | +1.6k | 9.1k      |
| a3|lag_bp30_th1|B1   | +2.8k | +3.3k | +2.0k  | +1.0k | +0.2k | +10.7k | +2.9k | 13.4k     |
| a3|lag_bp30_th1|B2   | +1.7k | +4.7k | +0.6k  | -0.1k | -1.2k | +5.1k  | +3.0k | 11.9k     |
| a7|lag_bp60_th0.5|B1 | +1.5k | +0.8k | +2.4k  | +2.8k | +4.5k | +6.4k  | +1.4k | 10.9k     |
| a5|es_tk30_th12|B2   | -0.2k | +0.7k | +1.9k  | +2.2k | +4.5k | +9.1k  | +0.7k | 4.2k      |

### Per session (as coded, research lots, planned-lot R; rm per planned lot; stk = stack delta $/wk when the rule is applied in that session only)

|                                    |   fired% |   rm X |   rm PRE |   rm HOLD |   rm L6M | stk X   | stk PRE   | stk HOLD   | stk L6M   |   MDE rm L6M | MDE stk L6M   |
|:-----------------------------------|---------:|-------:|---------:|----------:|---------:|:--------|:----------|:-----------|:----------|-------------:|:--------------|
| ('a3|lag_bp30_th1.5|B1', 'asia')   |     5.10 |   0.05 |    -0.02 |     -0.08 |    -0.07 | +1.5k   | +0.5k     | -0.0k      | +0.1k     |         0.41 | 10.7k         |
| ('a3|lag_bp30_th1.5|B1', 'london') |     5.30 |  -0.04 |     0.20 |      0.22 |     0.17 | -1.0k   | -0.2k     | +0.0k      | +0.2k     |         0.55 | 7.1k          |
| ('a3|lag_bp30_th1.5|B1', 'nyam')   |    31.30 |   0.07 |     0.16 |     -0.04 |     0.01 | -0.9k   | -0.6k     | +1.5k      | +0.1k     |         1.10 | 14.7k         |
| ('a3|lag_bp30_th1.5|B1', 'nypm')   |     9.10 |   0.02 |     0.12 |      0.07 |     0.08 | -0.2k   | +0.6k     | +0.6k      | +1.0k     |         0.76 | 2.6k          |
| ('a3|lag_bp30_th1.5|B1', 'pre')    |    14.50 |   0.00 |    -0.21 |     -0.59 |    -0.41 | +0.0k   | -0.5k     | +1.5k      | +1.5k     |         1.51 | 6.1k          |
| ('a3|lag_z30_th0.5|B2', 'asia')    |    20.30 |   0.45 |     0.40 |     -0.09 |     0.03 | +2.3k   | +3.5k     | +0.4k      | +2.6k     |         0.76 | 16.3k         |
| ('a3|lag_z30_th0.5|B2', 'london')  |    13.60 |  -0.34 |     0.28 |     -0.19 |    -0.25 | -4.3k   | +0.8k     | +1.0k      | +0.6k     |         0.88 | 11.3k         |
| ('a3|lag_z30_th0.5|B2', 'nyam')    |    10.80 |   0.08 |    -0.09 |     -0.17 |    -0.17 | -1.0k   | +1.8k     | +0.9k      | +1.6k     |         0.87 | 8.5k          |
| ('a3|lag_z30_th0.5|B2', 'nypm')    |     7.40 |   0.06 |     0.14 |      0.24 |     0.12 | +0.7k   | +0.8k     | -0.1k      | -0.3k     |         0.63 | 2.2k          |
| ('a3|lag_z30_th0.5|B2', 'pre')     |    16.00 |   0.37 |     0.01 |     -0.44 |    -0.66 | +1.3k   | +1.4k     | +2.8k      | +2.8k     |         1.59 | 6.0k          |
| ('a1|lag_z30_th0.5|B2', 'asia')    |    10.60 |   2.04 |     0.46 |     -0.19 |     0.02 | +10.8k  | +2.7k     | -5.7k      | -3.8k     |         1.32 | 20.5k         |
| ('a1|lag_z30_th0.5|B2', 'london')  |     7.30 |  -0.49 |     0.53 |      0.37 |     0.33 | -3.8k   | +3.3k     | +1.7k      | +2.0k     |         1.40 | 13.2k         |
| ('a1|lag_z30_th0.5|B2', 'nyam')    |     7.10 |   0.45 |    -0.32 |     -0.24 |    -0.16 | +3.6k   | -0.1k     | -0.6k      | +1.1k     |         1.47 | 14.7k         |
| ('a1|lag_z30_th0.5|B2', 'nypm')    |     3.90 |   0.05 |     0.09 |      0.50 |     0.20 | -1.1k   | +0.0k     | -0.6k      | -0.4k     |         0.84 | 2.8k          |
| ('a1|lag_z30_th0.5|B2', 'pre')     |     8.00 |   0.07 |    -0.23 |     -0.80 |    -1.11 | +1.3k   | +1.6k     | +0.9k      | +0.1k     |         2.75 | 3.8k          |

### ER sizer (ER20 5m >=0.3 x1.5, below x0.5, as coded) alone, ES x ER, and the ES increment over ER ($/wk research lots)

|                                                      | X      | PRE    | HOLD   | L6M    | L3M    | Y26     | ALL    | MDE L6M   |
|:-----------------------------------------------------|:-------|:-------|:-------|:-------|:-------|:--------|:-------|:----------|
| ('B2', 'plan', 'ER only')                            | +6.7k  | -7.4k  | +18.7k | +18.6k | +42.8k | +48.8k  | +2.3k  | 41.6k     |
| ('B2', 'plan', 'a3|lag_z30_th0.5|B2 xER')            | +1.4k  | -0.8k  | +9.7k  | +9.8k  | +29.7k | +38.9k  | +2.1k  | 44.1k     |
| ('B2', 'plan', 'a3|lag_z30_th0.5|B2 incr_over_ER')   | -5.2k  | +6.6k  | -9.0k  | -8.8k  | -13.2k | -9.9k   | -0.2k  | 19.7k     |
| ('B2', 'plan', 'a1|lag_z30_th0.5|B2 xER')            | +13.1k | -1.4k  | +7.6k  | +7.8k  | +17.4k | +44.1k  | +4.8k  | 50.5k     |
| ('B2', 'plan', 'a1|lag_z30_th0.5|B2 incr_over_ER')   | +6.4k  | +5.9k  | -11.2k | -10.8k | -25.4k | -4.7k   | +2.5k  | 27.4k     |
| ('B2', 'plan', 'a5|lag_z30_th0.5|B2 xER')            | +11.1k | -1.0k  | +12.2k | +11.6k | +29.0k | +38.4k  | +5.4k  | 49.6k     |
| ('B2', 'plan', 'a5|lag_z30_th0.5|B2 incr_over_ER')   | +4.5k  | +6.4k  | -6.5k  | -7.1k  | -13.8k | -10.3k  | +3.1k  | 20.9k     |
| ('B2', 'plan', 'a3|lag_bp30_th1.5|B2 xER')           | +1.6k  | -0.8k  | +10.4k | +8.0k  | +31.8k | +49.6k  | +2.3k  | 42.8k     |
| ('B2', 'plan', 'a3|lag_bp30_th1.5|B2 incr_over_ER')  | -5.1k  | +6.6k  | -8.4k  | -10.7k | -11.1k | +0.8k   | -0.0k  | 20.8k     |
| ('B2', 'plan', 'a3|lag_bp30_th1|B2 xER')             | +3.3k  | -3.6k  | +11.7k | +10.0k | +31.0k | +47.4k  | +1.7k  | 42.4k     |
| ('B2', 'plan', 'a3|lag_bp30_th1|B2 incr_over_ER')    | -3.4k  | +3.8k  | -7.1k  | -8.6k  | -11.8k | -1.4k   | -0.6k  | 23.0k     |
| ('B2', 'plan', 'a5|es_tk30_th12|B2 xER')             | +7.1k  | -7.0k  | +20.5k | +20.7k | +44.0k | +48.4k  | +3.0k  | 40.8k     |
| ('B2', 'plan', 'a5|es_tk30_th12|B2 incr_over_ER')    | +0.4k  | +0.3k  | +1.8k  | +2.0k  | +1.2k  | -0.4k   | +0.7k  | 4.3k      |
| ('B2', 'sized', 'ER only')                           | -1.2k  | +12.7k | +35.6k | +40.9k | +46.3k | +105.7k | +13.7k | 53.1k     |
| ('B2', 'sized', 'a3|lag_z30_th0.5|B2 xER')           | +2.8k  | +14.7k | +30.0k | +32.2k | +30.9k | +91.9k  | +14.6k | 53.7k     |
| ('B2', 'sized', 'a3|lag_z30_th0.5|B2 incr_over_ER')  | +4.0k  | +2.0k  | -5.6k  | -8.7k  | -15.4k | -13.7k  | +1.0k  | 17.5k     |
| ('B2', 'sized', 'a1|lag_z30_th0.5|B2 xER')           | +8.4k  | +10.4k | +25.5k | +29.3k | +38.1k | +96.4k  | +13.2k | 54.1k     |
| ('B2', 'sized', 'a1|lag_z30_th0.5|B2 incr_over_ER')  | +9.5k  | -2.3k  | -10.1k | -11.6k | -8.2k  | -9.3k   | -0.5k  | 26.9k     |
| ('B2', 'sized', 'a5|lag_z30_th0.5|B2 xER')           | +4.1k  | +11.8k | +29.2k | +33.7k | +41.4k | +96.2k  | +13.4k | 53.0k     |
| ('B2', 'sized', 'a5|lag_z30_th0.5|B2 incr_over_ER')  | +5.3k  | -0.9k  | -6.4k  | -7.2k  | -4.9k  | -9.4k   | -0.3k  | 15.2k     |
| ('B2', 'sized', 'a3|lag_bp30_th1.5|B2 xER')          | -6.1k  | +7.4k  | +29.9k | +33.0k | +30.0k | +77.6k  | +8.3k  | 52.8k     |
| ('B2', 'sized', 'a3|lag_bp30_th1.5|B2 incr_over_ER') | -4.9k  | -5.3k  | -5.7k  | -7.9k  | -16.3k | -28.1k  | -5.4k  | 20.9k     |
| ('B2', 'sized', 'a3|lag_bp30_th1|B2 xER')            | -2.0k  | +7.8k  | +30.4k | +34.3k | +36.9k | +82.6k  | +9.9k  | 49.2k     |
| ('B2', 'sized', 'a3|lag_bp30_th1|B2 incr_over_ER')   | -0.8k  | -4.9k  | -5.2k  | -6.6k  | -9.4k  | -23.1k  | -3.8k  | 22.3k     |
| ('B2', 'sized', 'a5|es_tk30_th12|B2 xER')            | -0.7k  | +14.0k | +35.1k | +40.3k | +45.0k | +104.0k | +14.4k | 52.5k     |
| ('B2', 'sized', 'a5|es_tk30_th12|B2 incr_over_ER')   | +0.4k  | +1.3k  | -0.5k  | -0.6k  | -1.3k  | -1.6k   | +0.7k  | 2.0k      |
| ('B1', 'plan', 'ER only')                            | +7.5k  | -7.4k  | +19.8k | +17.3k | +52.7k | +54.9k  | +2.7k  | 48.3k     |
| ('B1', 'plan', 'a3|lag_z30_th0.5|B1 xER')            | +2.5k  | +1.1k  | +18.1k | +15.0k | +44.1k | +47.9k  | +5.2k  | 52.1k     |
| ('B1', 'plan', 'a3|lag_z30_th0.5|B1 incr_over_ER')   | -5.0k  | +8.5k  | -1.7k  | -2.3k  | -8.5k  | -7.0k   | +2.5k  | 24.9k     |
| ('B1', 'plan', 'a1|lag_z30_th0.5|B1 xER')            | +14.8k | +0.8k  | +9.8k  | +8.0k  | +24.0k | +41.8k  | +6.9k  | 56.1k     |
| ('B1', 'plan', 'a1|lag_z30_th0.5|B1 incr_over_ER')   | +7.3k  | +8.2k  | -10.0k | -9.3k  | -28.6k | -13.1k  | +4.1k  | 31.1k     |
| ('B1', 'plan', 'a3|lag_bp30_th1.5|B1 xER')           | +3.6k  | -3.5k  | +12.7k | +8.5k  | +41.6k | +58.4k  | +2.0k  | 49.0k     |
| ('B1', 'plan', 'a3|lag_bp30_th1.5|B1 incr_over_ER')  | -4.0k  | +3.9k  | -7.1k  | -8.8k  | -11.1k | +3.6k   | -0.7k  | 18.7k     |
| ('B1', 'plan', 'a3|lag_bp30_th1|B1 xER')             | +4.9k  | -4.4k  | +14.0k | +10.0k | +42.7k | +58.6k  | +2.2k  | 52.0k     |
| ('B1', 'plan', 'a3|lag_bp30_th1|B1 incr_over_ER')    | -2.6k  | +3.0k  | -5.8k  | -7.3k  | -10.0k | +3.7k   | -0.5k  | 21.6k     |
| ('B1', 'plan', 'a7|lag_bp60_th0.5|B1 xER')           | +5.8k  | -17.9k | +24.6k | +20.2k | +63.4k | +64.4k  | -2.0k  | 52.1k     |
| ('B1', 'plan', 'a7|lag_bp60_th0.5|B1 incr_over_ER')  | -1.7k  | -10.5k | +4.8k  | +2.9k  | +10.8k | +9.5k   | -4.8k  | 15.6k     |
| ('B1', 'sized', 'ER only')                           | +4.5k  | +7.1k  | +43.3k | +49.8k | +63.9k | +104.1k | +14.2k | 57.6k     |
| ('B1', 'sized', 'a3|lag_z30_th0.5|B1 xER')           | +6.6k  | +12.8k | +39.1k | +41.2k | +43.6k | +98.0k  | +16.8k | 58.5k     |
| ('B1', 'sized', 'a3|lag_z30_th0.5|B1 incr_over_ER')  | +2.1k  | +5.7k  | -4.1k  | -8.6k  | -20.3k | -6.1k   | +2.6k  | 14.9k     |
| ('B1', 'sized', 'a1|lag_z30_th0.5|B1 xER')           | +10.9k | +6.0k  | +31.5k | +35.2k | +46.9k | +95.0k  | +13.0k | 59.3k     |
| ('B1', 'sized', 'a1|lag_z30_th0.5|B1 incr_over_ER')  | +6.4k  | -1.1k  | -11.8k | -14.7k | -17.0k | -9.1k   | -1.2k  | 25.3k     |
| ('B1', 'sized', 'a3|lag_bp30_th1.5|B1 xER')          | +0.5k  | +6.1k  | +40.9k | +44.1k | +55.1k | +88.0k  | +12.0k | 57.6k     |
| ('B1', 'sized', 'a3|lag_bp30_th1.5|B1 incr_over_ER') | -4.0k  | -1.0k  | -2.3k  | -5.7k  | -8.8k  | -16.1k  | -2.2k  | 18.8k     |
| ('B1', 'sized', 'a3|lag_bp30_th1|B1 xER')            | +2.7k  | +7.2k  | +39.7k | +42.3k | +52.2k | +99.4k  | +12.9k | 53.5k     |
| ('B1', 'sized', 'a3|lag_bp30_th1|B1 incr_over_ER')   | -1.8k  | +0.1k  | -3.6k  | -7.5k  | -11.7k | -4.7k   | -1.3k  | 22.6k     |
| ('B1', 'sized', 'a7|lag_bp60_th0.5|B1 xER')          | +5.8k  | +11.3k | +47.4k | +55.2k | +59.0k | +109.0k | +17.6k | 58.7k     |
| ('B1', 'sized', 'a7|lag_bp60_th0.5|B1 incr_over_ER') | +1.3k  | +4.2k  | +4.1k  | +5.3k  | -5.0k  | +4.9k   | +3.4k  | 18.8k     |

### Feed delay / 1-min closes / threshold sensitivity / matched-rate controls (research lots, planned-lot R, as coded)

|                                                                 |   rm X |   rm PRE |   rm HOLD |   rm L6M | stk X   | stk PRE   | stk HOLD   | stk L6M   | stk ALL   |
|:----------------------------------------------------------------|-------:|---------:|----------:|---------:|:--------|:----------|:-----------|:----------|:----------|
| ('a3|lag_z30_th0.5|B2', 'S30 D0')                               |   0.11 |     0.15 |     -0.08 |    -0.09 | +1.7k   | +8.0k     | +2.9k      | +5.9k     | +5.2k     |
| ('a3|lag_z30_th0.5|B2', 'S30 D1 (ES feed 1 s late)')            |   0.02 |     0.14 |      0.08 |     0.05 | -6.0k   | +4.9k     | -1.7k      | +0.9k     | +0.3k     |
| ('a3|lag_z30_th0.5|B2', 'S30 D3 (ES feed 3 s late)')            |   0.17 |     0.12 |     -0.05 |    -0.07 | +4.4k   | +6.8k     | -8.4k      | -8.3k     | +2.9k     |
| ('a3|lag_z30_th0.5|B2', 'S15 D0')                               |   0.15 |     0.07 |     -0.00 |    -0.03 | -1.2k   | -5.7k     | +0.2k      | +2.1k     | -3.2k     |
| ('a3|lag_z30_th0.5|B2', 'S60 D0')                               |  -0.07 |     0.15 |      0.16 |     0.15 | -6.7k   | +3.1k     | +9.3k      | +11.4k    | +1.6k     |
| ('a3|lag_z30_th0.5|B2', 'S60 D1')                               |  -0.08 |     0.18 |      0.16 |     0.11 | -6.0k   | +3.8k     | +5.6k      | +5.8k     | +1.3k     |
| ('a3|lag_z30_th0.5|B2', 'S60 D3')                               |   0.06 |     0.13 |      0.10 |     0.15 | -6.2k   | +1.2k     | +5.9k      | +12.5k    | +0.0k     |
| ('a3|lag_z30_th0.5|B2', 'M1c 60 (last completed 1-min bar)')    |  -0.06 |    -0.01 |     -0.01 |     0.05 | -2.3k   | -2.2k     | -0.2k      | +1.0k     | -1.8k     |
| ('a3|lag_z30_th0.5|B2', 'M1f 60 (completed + forming bar)')     |  -0.15 |     0.14 |      0.09 |     0.09 | -9.4k   | +1.1k     | +9.7k      | +11.6k    | -0.2k     |
| ('a3|lag_z30_th0.5|B2', 'S30 th x0.5')                          |   0.19 |     0.11 |     -0.06 |    -0.02 | -0.7k   | +2.2k     | -3.3k      | -2.2k     | +0.2k     |
| ('a3|lag_z30_th0.5|B2', 'S30 th x0.75')                         |   0.06 |     0.16 |     -0.22 |    -0.22 | +1.9k   | +4.9k     | -7.9k      | -6.8k     | +1.3k     |
| ('a3|lag_z30_th0.5|B2', 'S30 th x1.25')                         |   0.10 |     0.13 |     -0.08 |    -0.07 | -1.1k   | +8.6k     | +3.0k      | +4.6k     | +4.6k     |
| ('a3|lag_z30_th0.5|B2', 'S30 th x1.5')                          |   0.06 |     0.15 |      0.03 |     0.03 | -1.7k   | +4.2k     | +1.2k      | +3.7k     | +1.8k     |
| ('a3|lag_z30_th0.5|B2', 'NQ-own reversed (matched fire rate)')  |   0.27 |     0.07 |      0.10 |     0.10 | +1.4k   | -1.5k     | -9.5k      | -10.1k    | -2.4k     |
| ('a3|lag_z30_th0.5|B2', 'ES-only (matched fire rate)')          |  -0.15 |    -0.03 |      0.02 |     0.00 | -2.1k   | +6.0k     | +0.8k      | +1.4k     | +2.5k     |
| ('a1|lag_z30_th0.5|B2', 'S30 D0')                               |   0.48 |     0.09 |     -0.00 |    -0.01 | +9.9k   | +5.7k     | -3.4k      | -1.7k     | +5.1k     |
| ('a1|lag_z30_th0.5|B2', 'S30 D1 (ES feed 1 s late)')            |   0.26 |     0.01 |     -0.09 |    -0.12 | -4.8k   | -0.1k     | -4.3k      | -1.4k     | -2.4k     |
| ('a1|lag_z30_th0.5|B2', 'S30 D3 (ES feed 3 s late)')            |   0.25 |     0.03 |     -0.02 |    -0.04 | +1.4k   | +3.4k     | -4.9k      | -4.8k     | +1.1k     |
| ('a1|lag_z30_th0.5|B2', 'S15 D0')                               |  -0.06 |     0.18 |      0.01 |    -0.07 | -6.7k   | -2.9k     | -0.4k      | -0.5k     | -3.5k     |
| ('a1|lag_z30_th0.5|B2', 'S60 D0')                               |  -0.17 |     0.13 |      0.20 |     0.17 | -13.3k  | +3.0k     | +7.3k      | +9.7k     | -0.8k     |
| ('a1|lag_z30_th0.5|B2', 'S60 D1')                               |  -0.30 |     0.16 |      0.14 |     0.05 | -12.0k  | +1.1k     | +2.8k      | +5.2k     | -2.4k     |
| ('a1|lag_z30_th0.5|B2', 'S60 D3')                               |  -0.04 |     0.16 |      0.03 |     0.11 | -10.0k  | +0.3k     | +1.5k      | +10.0k    | -2.5k     |
| ('a1|lag_z30_th0.5|B2', 'M1c 60 (last completed 1-min bar)')    |  -0.19 |    -0.08 |      0.09 |     0.19 | -9.0k   | -2.7k     | -3.4k      | +0.7k     | -4.8k     |
| ('a1|lag_z30_th0.5|B2', 'M1f 60 (completed + forming bar)')     |  -0.36 |     0.09 |      0.13 |     0.17 | -19.4k  | +4.5k     | +1.8k      | +6.0k     | -3.1k     |
| ('a1|lag_z30_th0.5|B2', 'S30 th x0.5')                          |   0.60 |    -0.03 |      0.02 |     0.01 | +3.1k   | -8.3k     | -13.4k     | -14.3k    | -6.1k     |
| ('a1|lag_z30_th0.5|B2', 'S30 th x0.75')                         |   0.38 |     0.07 |     -0.24 |    -0.30 | +7.0k   | +0.4k     | -9.6k      | -9.5k     | +0.2k     |
| ('a1|lag_z30_th0.5|B2', 'S30 th x1.25')                         |   0.37 |     0.13 |      0.04 |     0.02 | +5.1k   | +11.7k    | -0.2k      | +3.2k     | +7.3k     |
| ('a1|lag_z30_th0.5|B2', 'S30 th x1.5')                          |   0.20 |     0.17 |      0.13 |     0.10 | -0.2k   | +6.6k     | +0.4k      | +4.2k     | +3.3k     |
| ('a1|lag_z30_th0.5|B2', 'NQ-own reversed (matched fire rate)')  |   0.39 |     0.14 |     -0.01 |     0.00 | -2.6k   | -6.1k     | -13.5k     | -13.3k    | -6.7k     |
| ('a1|lag_z30_th0.5|B2', 'ES-only (matched fire rate)')          |   0.02 |    -0.14 |     -0.08 |    -0.10 | -4.9k   | -3.6k     | -3.0k      | -5.2k     | -3.9k     |
| ('a3|lag_bp30_th1.5|B1', 'S30 D0')                              |   0.02 |     0.05 |      0.00 |     0.03 | -0.3k   | +2.4k     | +2.2k      | +1.2k     | +1.6k     |
| ('a3|lag_bp30_th1.5|B1', 'S30 D1 (ES feed 1 s late)')           |  -0.05 |     0.05 |      0.07 |     0.10 | -4.5k   | -1.6k     | +7.4k      | +5.4k     | -0.5k     |
| ('a3|lag_bp30_th1.5|B1', 'S30 D3 (ES feed 3 s late)')           |   0.03 |    -0.09 |      0.14 |     0.15 | -2.1k   | -1.7k     | +3.8k      | +0.4k     | -0.7k     |
| ('a3|lag_bp30_th1.5|B1', 'S15 D0')                              |  -0.03 |    -0.11 |      0.14 |     0.16 | -3.1k   | -5.1k     | +6.5k      | +6.6k     | -2.1k     |
| ('a3|lag_bp30_th1.5|B1', 'S60 D0')                              |  -0.20 |     0.11 |      0.35 |     0.42 | -12.3k  | -1.6k     | -1.4k      | -0.6k     | -4.7k     |
| ('a3|lag_bp30_th1.5|B1', 'S60 D1')                              |  -0.11 |     0.10 |      0.40 |     0.47 | -9.2k   | -3.1k     | -3.9k      | -5.8k     | -5.1k     |
| ('a3|lag_bp30_th1.5|B1', 'S60 D3')                              |  -0.13 |     0.08 |      0.33 |     0.39 | -7.9k   | -3.5k     | -3.3k      | -2.7k     | -4.8k     |
| ('a3|lag_bp30_th1.5|B1', 'M1c 60 (last completed 1-min bar)')   |   0.02 |    -0.10 |      0.24 |     0.31 | +0.1k   | -12.4k    | +1.6k      | +3.6k     | -5.9k     |
| ('a3|lag_bp30_th1.5|B1', 'M1f 60 (completed + forming bar)')    |   0.28 |    -0.02 |      0.60 |     0.67 | -4.4k   | -7.9k     | +5.4k      | +5.0k     | -4.1k     |
| ('a3|lag_bp30_th1.5|B1', 'S30 th x0.5')                         |   0.10 |     0.03 |      0.14 |     0.15 | -4.6k   | -2.7k     | -3.2k      | -3.6k     | -3.4k     |
| ('a3|lag_bp30_th1.5|B1', 'S30 th x0.75')                        |   0.06 |     0.08 |     -0.10 |    -0.06 | +1.3k   | -0.0k     | +6.5k      | +6.4k     | +1.8k     |
| ('a3|lag_bp30_th1.5|B1', 'S30 th x1.25')                        |  -0.02 |     0.04 |      0.05 |     0.07 | -3.9k   | -2.4k     | +6.2k      | +6.4k     | -1.0k     |
| ('a3|lag_bp30_th1.5|B1', 'S30 th x1.5')                         |   0.01 |    -0.10 |      0.12 |     0.13 | -3.1k   | -1.2k     | +7.7k      | +7.7k     | +0.1k     |
| ('a3|lag_bp30_th1.5|B1', 'NQ-own reversed (matched fire rate)') |   0.25 |     0.04 |      0.06 |     0.09 | +3.2k   | -6.2k     | +5.0k      | +3.0k     | -1.1k     |
| ('a3|lag_bp30_th1.5|B1', 'ES-only (matched fire rate)')         |  -0.15 |    -0.14 |      0.06 |     0.04 | -4.7k   | -5.8k     | +3.3k      | +3.3k     | -3.6k     |
| ('a3|lag_bp30_th1.5|B2', 'S30 D0')                              |   0.02 |     0.05 |     -0.02 |     0.01 | -3.2k   | +4.1k     | +3.8k      | +4.9k     | +1.9k     |
| ('a3|lag_bp30_th1.5|B2', 'S30 D1 (ES feed 1 s late)')           |  -0.04 |     0.04 |      0.04 |     0.06 | -5.2k   | -0.1k     | +4.7k      | +3.5k     | -0.6k     |
| ('a3|lag_bp30_th1.5|B2', 'S30 D3 (ES feed 3 s late)')           |   0.04 |    -0.10 |      0.11 |     0.11 | -2.4k   | +0.2k     | -3.4k      | -6.5k     | -1.4k     |
| ('a3|lag_bp30_th1.5|B2', 'S15 D0')                              |  -0.02 |    -0.11 |      0.14 |     0.16 | -4.4k   | -2.6k     | +3.6k      | +3.3k     | -1.8k     |
| ('a3|lag_bp30_th1.5|B2', 'S60 D0')                              |  -0.20 |     0.09 |      0.34 |     0.40 | -16.6k  | +3.1k     | -7.9k      | -5.7k     | -5.1k     |
| ('a3|lag_bp30_th1.5|B2', 'S60 D1')                              |  -0.10 |     0.07 |      0.41 |     0.46 | -12.2k  | +2.3k     | -13.1k     | -14.7k    | -5.2k     |
| ('a3|lag_bp30_th1.5|B2', 'S60 D3')                              |  -0.13 |     0.07 |      0.33 |     0.39 | -13.5k  | +0.4k     | -10.4k     | -8.8k     | -6.0k     |
| ('a3|lag_bp30_th1.5|B2', 'M1c 60 (last completed 1-min bar)')   |   0.00 |    -0.10 |      0.24 |     0.31 | +0.6k   | -8.6k     | +4.0k      | +7.4k     | -3.3k     |
| ('a3|lag_bp30_th1.5|B2', 'M1f 60 (completed + forming bar)')    |   0.26 |    -0.03 |      0.60 |     0.65 | -7.3k   | -0.7k     | -3.1k      | -3.0k     | -3.2k     |
| ('a3|lag_bp30_th1.5|B2', 'S30 th x0.5')                         |   0.12 |     0.00 |      0.08 |     0.10 | -6.1k   | -2.2k     | -8.9k      | -7.6k     | -4.8k     |
| ('a3|lag_bp30_th1.5|B2', 'S30 th x0.75')                        |   0.05 |     0.06 |     -0.13 |    -0.10 | -2.9k   | +0.6k     | +2.7k      | +3.2k     | -0.0k     |
| ('a3|lag_bp30_th1.5|B2', 'S30 th x1.25')                        |  -0.03 |     0.04 |      0.04 |     0.05 | -4.7k   | +0.2k     | +5.2k      | +5.8k     | -0.2k     |
| ('a3|lag_bp30_th1.5|B2', 'S30 th x1.5')                         |   0.01 |    -0.10 |      0.12 |     0.13 | -2.6k   | +0.4k     | +6.5k      | +7.2k     | +0.8k     |
| ('a3|lag_bp30_th1.5|B2', 'NQ-own reversed (matched fire rate)') |   0.24 |     0.04 |      0.06 |     0.10 | +0.4k   | -1.9k     | +5.4k      | +5.9k     | +0.3k     |
| ('a3|lag_bp30_th1.5|B2', 'ES-only (matched fire rate)')         |  -0.17 |    -0.15 |      0.05 |     0.03 | -4.9k   | -4.3k     | +3.4k      | +3.3k     | -2.9k     |

### Walk-forward threshold chains (monthly re-fit from 2023-07; fit on trades closed before the re-fit; grid w 15/30/60 x th; OFF if best trailing lift <= 0)

|                     |   rm X |   rm PRE |   rm HOLD |   rm L6M | stk X   | stk PRE   | stk HOLD   | stk L6M   | stk ALL (MDE)   | stk ALL sized-R   | last re-fit                   | share active   |
|:--------------------|-------:|---------:|----------:|---------:|:--------|:----------|:-----------|:----------|:----------------|:------------------|:------------------------------|:---------------|
| ('bp_a3', 'anch')   |   0.20 |    -0.11 |      0.53 |     0.58 | -2.3k   | -5.1k     | -7.1k      | -8.2k     | -4.8k (13.0k)   | -4.0k             | w60 s, th 0.5, fit +0.21, ON  | 61%            |
| ('bp_a3', 'roll12') |   0.20 |    -0.03 |      0.37 |     0.42 | -2.3k   | -3.1k     | -9.7k      | -8.2k     | -4.4k (12.2k)   | -1.9k             | w60 s, th 0.5, fit +0.20, ON  | 37%            |
| ('bp_a3', 'roll6')  |   0.20 |     0.09 |      0.44 |     0.56 | -2.3k   | +0.8k     | -12.2k     | -10.7k    | -2.9k (11.0k)   | +0.1k             | w60 s, th 0.5, fit +0.69, ON  | 53%            |
| ('z_a3', 'anch')    |  -0.01 |     0.07 |     -0.08 |    -0.09 | -2.3k   | +5.5k     | +7.6k      | +11.3k    | +3.7k (10.8k)   | +4.6k             | w60 s, th 0.5, fit +0.11, ON  | 13%            |
| ('z_a3', 'roll12')  |  -0.01 |     0.11 |      0.04 |     0.07 | -2.3k   | +5.1k     | +4.3k      | +8.2k     | +2.8k (10.5k)   | +5.4k             | w60 s, th 0.5, fit +0.18, ON  | 18%            |
| ('z_a3', 'roll6')   |  -0.04 |    -0.04 |      0.16 |     0.15 | -1.2k   | +1.8k     | +9.3k      | +11.4k    | +2.5k (9.6k)    | +1.9k             | w60 s, th 0.5, fit +0.16, ON  | 11%            |
| ('z_a1', 'anch')    |   0.06 |    -0.07 |      0.07 |     0.06 | -1.8k   | -3.0k     | -2.2k      | -0.3k     | -2.5k (13.6k)   | -2.5k             | w30 s, th 0.75, fit +0.18, ON | 6%             |
| ('z_a1', 'roll12')  |   0.06 |     0.04 |      0.09 |     0.07 | -1.8k   | -3.7k     | +2.0k      | +3.5k     | -1.9k (11.3k)   | -1.9k             | w60 s, th 0.5, fit +0.23, ON  | 4%             |
| ('z_a1', 'roll6')   |   0.20 |     0.02 |      0.16 |     0.14 | +2.0k   | -3.0k     | -0.0k      | +0.7k     | -0.9k (10.6k)   | -0.9k             | w15 s, th 0.75, fit +0.20, ON | 4%             |

### Placebo ranks (rank 1 = real above all draws; N draws). shift = ES time-shifted (+-15..3600 s, +-1..60 days, ES only; NQ real); shuffle = ES from a random other trading day, same clock time

|                                             |   draws | trade PRE   | trade HOLD   | trade L6M   | stack X   | stack PRE   | stack HOLD   | stack L6M   | stack ALL   |
|:--------------------------------------------|--------:|:------------|:-------------|:------------|:----------|:------------|:-------------|:------------|:------------|
| ('shift_a1_lag_z30_th0.5_B2', 'shift')      |     250 | 194/251     | 151/251      | 162/251     | 11/251    | 21/251      | 34/251       | 32/251      | 21/251      |
| ('shift_a3_lag_bp30_th1.5_B1', 'shift')     |     250 | 238/251     | 174/251      | 184/251     | 202/251   | 88/251      | 74/251       | 80/251      | 88/251      |
| ('shift_a3_lag_bp30_th1.5_B2', 'shift')     |     250 | 239/251     | 190/251      | 203/251     | 233/251   | 108/251     | 38/251       | 40/251      | 99/251      |
| ('shift_a3_lag_z30_th0.5_B2', 'shift')      |     250 | 144/251     | 188/251      | 196/251     | 116/251   | 34/251      | 27/251       | 21/251      | 45/251      |
| ('shuffle_a1_lag_z30_th0.5_B2', 'shuffle')  |     200 | 141/201     | 105/201      | 121/201     | 1/201     | 1/201       | 1/201        | 1/201       | 1/201       |
| ('shuffle_a3_lag_bp30_th1.5_B1', 'shuffle') |     200 | 188/201     | 131/201      | 140/201     | 148/201   | 18/201      | 21/201       | 27/201      | 22/201      |
| ('shuffle_a3_lag_bp30_th1.5_B2', 'shuffle') |     200 | 191/201     | 151/201      | 161/201     | 184/201   | 49/201      | 4/201        | 5/201       | 34/201      |
| ('shuffle_a3_lag_z30_th0.5_B2', 'shuffle')  |     200 | 60/201      | 142/201      | 148/201     | 66/201    | 1/201       | 1/201        | 3/201       | 1/201       |

### Capacity: NQ contracts traded (all outrights) in the 2 / 10 / 60 s after the signal vs live order size

|                                       |       n |   vol2_med |   vol2_p10 |   vol10_med |   vol10_p10 |   vol60_med |   live_lots_mean |   live_lots_p90 |   live_lots_max |   share_lots_gt_25pct_vol10 |   share_vol10_lt10 |
|:--------------------------------------|--------:|-----------:|-----------:|------------:|------------:|------------:|-----------------:|----------------:|----------------:|----------------------------:|-------------------:|
| ('a3|lag_bp30_th1.5|B1', 'up x1.5')   |  1000.0 |       77.0 |       10.0 |       321.5 |        41.9 |      1582.0 |              5.7 |            10.5 |            10.5 |                         0.1 |                0.0 |
| ('a3|lag_bp30_th1.5|B1', 'down x0.5') |  3432.0 |       91.0 |       12.0 |       370.0 |        50.0 |      1653.0 |              1.8 |             3.5 |             3.5 |                         0.0 |                0.0 |
| ('a3|lag_bp30_th1.5|B1', 'all ENG6')  | 24924.0 |       24.0 |        2.0 |        98.0 |        11.0 |       472.0 |              3.7 |             7.0 |             7.0 |                         0.2 |                0.1 |
| ('a3|lag_z30_th0.5|B2', 'up x1.5')    |  1943.0 |       11.0 |        2.0 |        39.0 |         6.0 |       165.0 |              5.7 |            10.5 |            10.5 |                         0.4 |                0.2 |
| ('a3|lag_z30_th0.5|B2', 'down x0.5')  |  2757.0 |       15.0 |        2.0 |        51.0 |         8.0 |       219.0 |              1.9 |             3.5 |             3.5 |                         0.1 |                0.1 |
| ('a3|lag_z30_th0.5|B2', 'all ENG6')   | 24924.0 |       24.0 |        2.0 |        98.0 |        11.0 |       472.0 |              3.7 |             7.0 |             7.0 |                         0.2 |                0.1 |

### Leverage benchmark: uniform lot scalar vs the sizer (stack delta $/wk, research lots)

|                                                                         |     X |   PRE |   HOLD |   L6M |   L3M |   Y26 |   ALL |
|:------------------------------------------------------------------------|------:|------:|-------:|------:|------:|------:|------:|
| ('a3|lag_bp30_th1.5|B1', 'uniform lots x1.044 (the equal-risk scalar)') |  2811 | -4098 |   3599 |  4023 |  7414 |  1177 |  -459 |
| ('a3|lag_bp30_th1.5|B1', 'sizer x equal-risk scalar')                   |  2495 |   774 |   4550 |  3820 |  4364 |   437 |  2104 |
| ('a3|lag_bp30_th1.5|B1', 'sizer as coded')                              |  -328 |  2355 |   2193 |  1158 |   296 |   353 |  1559 |
| ('a3|lag_bp30_th1.5|B2', 'uniform lots x1.044 (the equal-risk scalar)') |  1395 |   712 |  -2139 |  -587 | -5141 | -8329 |   311 |
| ('a3|lag_bp30_th1.5|B2', 'sizer x equal-risk scalar')                   |   233 |  2891 |   4737 |  6692 |  3018 | -4202 |  2541 |
| ('a3|lag_bp30_th1.5|B2', 'sizer as coded')                              | -3220 |  4120 |   3773 |  4928 |  2008 | -3667 |  1933 |
| ('a3|lag_z30_th0.5|B2', 'uniform lots x1.016 (the equal-risk scalar)')  |  1359 |  -430 |   -284 |   880 |  1908 |   594 |   124 |
| ('a3|lag_z30_th0.5|B2', 'sizer x equal-risk scalar')                    |  1586 |  8049 |   2482 |  7096 |  1406 | 16811 |  5053 |
| ('a3|lag_z30_th0.5|B2', 'sizer as coded')                               |  1724 |  8012 |   2889 |  5902 | -1204 | 13483 |  5162 |

### Time-shift placebo re-ranked on causal-null subsets (positive intraday shifts use FUTURE ES and are not nulls) and single shifts

|                                                                                     |   n | trade PRE   | trade HOLD   | trade L6M   | stack X   | stack PRE   | stack HOLD   | stack L6M   | stack ALL   |
|:------------------------------------------------------------------------------------|----:|:------------|:-------------|:------------|:----------|:------------|:-------------|:------------|:------------|
| ('a3_lag_z30_th0.5_B2', 'all (as ordered)')                                         | 250 | 144/251     | 188/251      | 196/251     | 116/251   | 34/251      | 27/251       | 21/251      | 45/251      |
| ('a3_lag_z30_th0.5_B2', 'causal null: stale intraday + day shifts (no future ES)')  | 180 | 74/181      | 118/181      | 126/181     | 52/181    | 1/181       | 1/181        | 1/181       | 1/181       |
| ('a3_lag_z30_th0.5_B2', 'day shifts only (|shift|>=1 day)')                         | 101 | 28/102      | 82/102       | 82/102      | 25/102    | 1/102       | 1/102        | 1/102       | 1/102       |
| ('a3_lag_z30_th0.5_B2', 'stale intraday only (-15..-3600 s)')                       |  79 | 47/80       | 37/80        | 45/80       | 28/80     | 1/80        | 1/80         | 1/80        | 1/80        |
| ('a3_lag_z30_th0.5_B2', 'single shift +60 s (future)')                              |   1 | 1.295       | 1.005        | 1.113       | +2.3k     | +9.1k       | +1.4k        | +5.4k       | +5.5k       |
| ('a3_lag_z30_th0.5_B2', 'single shift -60 s')                                       |   1 | 0.211       | -0.129       | -0.107      | +0.0k     | -0.3k       | -5.5k        | -5.3k       | -1.3k       |
| ('a3_lag_z30_th0.5_B2', 'single shift +1 day')                                      |   1 | 0.234       | 0.010        | 0.048       | -1.1k     | -11.6k      | -9.3k        | -5.9k       | -8.1k       |
| ('a3_lag_z30_th0.5_B2', 'single shift -1 day')                                      |   1 | 0.152       | -0.262       | -0.269      | -8.0k     | -13.0k      | -18.0k       | -19.6k      | -12.8k      |
| ('a1_lag_z30_th0.5_B2', 'all (as ordered)')                                         | 250 | 194/251     | 151/251      | 162/251     | 11/251    | 21/251      | 34/251       | 32/251      | 21/251      |
| ('a1_lag_z30_th0.5_B2', 'causal null: stale intraday + day shifts (no future ES)')  | 177 | 121/178     | 78/178       | 89/178      | 1/178     | 1/178       | 1/178        | 1/178       | 1/178       |
| ('a1_lag_z30_th0.5_B2', 'day shifts only (|shift|>=1 day)')                         |  96 | 62/97       | 46/97        | 54/97       | 1/97      | 1/97        | 1/97         | 1/97        | 1/97        |
| ('a1_lag_z30_th0.5_B2', 'stale intraday only (-15..-3600 s)')                       |  81 | 60/82       | 33/82        | 36/82       | 1/82      | 1/82        | 1/82         | 1/82        | 1/82        |
| ('a1_lag_z30_th0.5_B2', 'single shift +60 s (future)')                              |   1 | 2.551       | 1.901        | 2.051       | +2.9k     | +7.8k       | -16.6k       | -14.1k      | +1.2k       |
| ('a1_lag_z30_th0.5_B2', 'single shift -60 s')                                       |   1 | 0.350       | -0.229       | -0.219      | -14.9k    | -13.7k      | -22.5k       | -21.6k      | -16.1k      |
| ('a1_lag_z30_th0.5_B2', 'single shift +1 day')                                      |   1 | 0.356       | -0.461       | -0.347      | -4.6k     | -25.3k      | -42.8k       | -42.8k      | -23.3k      |
| ('a1_lag_z30_th0.5_B2', 'single shift -1 day')                                      |   1 | 0.422       | -0.756       | -0.543      | -7.4k     | -27.1k      | -34.9k       | -35.9k      | -23.3k      |
| ('a3_lag_bp30_th1.5_B1', 'all (as ordered)')                                        | 250 | 238/251     | 174/251      | 184/251     | 202/251   | 88/251      | 74/251       | 80/251      | 88/251      |
| ('a3_lag_bp30_th1.5_B1', 'causal null: stale intraday + day shifts (no future ES)') | 171 | 159/172     | 95/172       | 105/172     | 125/172   | 19/172      | 14/172       | 21/172      | 15/172      |
| ('a3_lag_bp30_th1.5_B1', 'day shifts only (|shift|>=1 day)')                        |  94 | 89/95       | 65/95        | 69/95       | 71/95     | 17/95       | 12/95        | 17/95       | 11/95       |
| ('a3_lag_bp30_th1.5_B1', 'stale intraday only (-15..-3600 s)')                      |  77 | 71/78       | 31/78        | 37/78       | 55/78     | 3/78        | 3/78         | 5/78        | 5/78        |
| ('a3_lag_bp30_th1.5_B1', 'single shift +60 s (future)')                             |   1 | 1.506       | 0.984        | 1.015       | +15.7k    | +8.7k       | +2.6k        | +1.0k       | +9.6k       |
| ('a3_lag_bp30_th1.5_B1', 'single shift -60 s')                                      |   1 | 0.192       | 0.273        | 0.294       | +7.3k     | -6.8k       | +2.1k        | +2.8k       | -0.8k       |
| ('a3_lag_bp30_th1.5_B1', 'single shift +1 day')                                     |   1 | 0.264       | 0.017        | 0.011       | +1.0k     | +1.7k       | -7.7k        | -10.9k      | -0.5k       |
| ('a3_lag_bp30_th1.5_B1', 'single shift -1 day')                                     |   1 | 0.323       | -0.037       | -0.003      | +8.4k     | -4.8k       | -7.4k        | -8.3k       | -1.5k       |
| ('a3_lag_bp30_th1.5_B2', 'all (as ordered)')                                        | 250 | 239/251     | 190/251      | 203/251     | 233/251   | 108/251     | 38/251       | 40/251      | 99/251      |
| ('a3_lag_bp30_th1.5_B2', 'causal null: stale intraday + day shifts (no future ES)') | 168 | 157/169     | 108/169      | 121/169     | 151/169   | 32/169      | 5/169        | 6/169       | 22/169      |
| ('a3_lag_bp30_th1.5_B2', 'day shifts only (|shift|>=1 day)')                        |  88 | 84/89       | 66/89        | 69/89       | 79/89     | 24/89       | 3/89         | 3/89        | 16/89       |
| ('a3_lag_bp30_th1.5_B2', 'stale intraday only (-15..-3600 s)')                      |  80 | 74/81       | 43/81        | 53/81       | 73/81     | 9/81        | 3/81         | 4/81        | 7/81        |
| ('a3_lag_bp30_th1.5_B2', 'single shift +60 s (future)')                             |   1 | 1.374       | 0.905        | 0.956       | +13.7k    | +7.3k       | +3.9k        | +5.0k       | +8.6k       |
| ('a3_lag_bp30_th1.5_B2', 'single shift -60 s')                                      |   1 | 0.164       | 0.254        | 0.285       | +6.1k     | -3.2k       | -1.6k        | -1.7k       | -0.2k       |
| ('a3_lag_bp30_th1.5_B2', 'single shift +1 day')                                     |   1 | 0.307       | -0.038       | -0.063      | +0.2k     | +3.4k       | -16.6k       | -18.0k      | -1.8k       |
| ('a3_lag_bp30_th1.5_B2', 'single shift -1 day')                                     |   1 | 0.210       | -0.024       | 0.031       | +6.8k     | -4.8k       | -6.8k        | -6.4k       | -1.9k       |

### ES increment over the ER sizer for the 60-s / 1-min-bar / walk-forward versions ($/wk research lots, B2)

|                                      |      X |   PRE |   HOLD |   L6M |   L3M |   Y26 |   ALL |   mde_L6M |
|:-------------------------------------|-------:|------:|-------:|------:|------:|------:|------:|----------:|
| ('plan', 'S60 lag_z a3 th0.5 (B2)')  | -17077 |  2333 |    936 |   519 |   190 | 11817 | -3667 |     15197 |
| ('plan', 'M1f60 lag_z a3 th0.5')     | -16413 |  6591 |  -2430 | -1784 |   177 | 19442 | -2051 |     14758 |
| ('plan', 'M1c60 lag_z a3 th0.5')     |  -6543 |  3267 |  -7371 | -7275 | -8677 | -6889 | -1871 |     13632 |
| ('plan', 'WF chain z_a3 anch')       |  -4240 |  8127 |  -3004 | -1998 |   506 | 11817 |  2194 |     19500 |
| ('plan', 'WF chain z_a3 roll12')     |  -4240 | 11960 | -10099 | -9143 |   190 | 11817 |  2599 |     19343 |
| ('plan', 'WF chain z_a3 roll6')      |  -3459 |  4007 |    936 |   519 |   190 | 11817 |  1197 |     15197 |
| ('sized', 'S60 lag_z a3 th0.5 (B2)') |  -8794 |   569 |   2184 |   466 | -8499 | -3983 | -1841 |     19124 |
| ('sized', 'M1f60 lag_z a3 th0.5')    |  -4534 |  3760 |   4887 |  4624 | -4496 |  2123 |  1603 |     17363 |
| ('sized', 'M1c60 lag_z a3 th0.5')    |  -3577 |  2059 |   2848 |  5275 | -4849 |   350 |   592 |     16190 |
| ('sized', 'WF chain z_a3 anch')      |   3170 |  3086 |  -3009 | -5704 | -9448 | -3983 |  1843 |     16880 |
| ('sized', 'WF chain z_a3 roll12')    |   3170 |  8414 |  -1924 |   747 | -8499 | -3983 |  4758 |     19213 |
| ('sized', 'WF chain z_a3 roll6')     |   4585 |  -110 |   2184 |   466 | -8499 | -3983 |  1768 |     19124 |