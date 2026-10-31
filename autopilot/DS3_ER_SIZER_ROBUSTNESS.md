# DS3_ER_SIZER_ROBUSTNESS - stress test and tune-free characterisation of THE coded ER(20) 5-min sizer (agent ER-1)

Research only. No live/execution/chart change. UNTOUCHED never read (every frame capped at label day 20260206). Own masks: L3M 20251106.., L6M 20250801.., HOLD 20250701.., PRE 20240201..20250630, X' 20230401..20240131. Code `l2vast/ds3/code/ersizer/` (erlib.py wraps `sundaystack2/ss2_lib.py`, which holds the lock engine and all governor readings; nothing of SS-2 is duplicated), outputs `l2vast/ds3/out/ersizer/`. Prereg note `autopilot/ER1_prereg.md` (written after the first grid, characterisation only, nothing selected). The coded sizer itself is post-hoc-selected (T2/TG-1, threshold 0.30 and x1.5/x0.5 chosen after looking at L6M/HOLD/L3M), so every number below is a read-out of a selected rule, not an out-of-sample test.

**Set-up.** Stack = the SS-2 lock-engine composite (70/30 split at integer live lots with 0.25-pt add slippage, A6 market entry, PE 45-s three-bar in NY-AM/NY-PM, Asia-stopped cut, 8-line zone skip, Native stop 1.28, basis N) at the user's live lots in the user's sessions (K6 2 Asia/London/NY-AM/NY-PM, P6 7 Asia/London/NY-AM, U6 4 Asia/London, H6 4 Asia / 2 NY-AM, M6 2 London/NY-AM, A6 1 every session) plus ST and WT at research/2.35 (`live+` of SS-2). Tag mapping: K6=KB, P6=PE, U6=SM, H6=HM, M6=MV, A6=PB (project tag table); ST=ST, WT=WT. The sizer acts on the six SS books (ST HM WT KB SM PE); M6 and A6 are not sized in the headline (shown in section 2e). Integer lots: effective lots = floor(session lot x multiplier + 0.5) (round half up), minimum 1 for a multiplier above 0, multiplier 0 = skip; the governors see the effective multiplier (final lots / session lots). ST/WT at research/2.35 are fractional (not live). **Every delta is $k per week of the lock-engine stack, sizer minus the SAME composite without the ER sizer ('in-stack'), MDE (2.8 x SE of the paired weekly delta) in brackets**; 'alone' = ER on the as-is stack vs the as-is stack (the SUNDAY_STACK headline reading). Governor readings (SS-2): running max (causal, the D6-implementable reading, HEADLINE), day-static sized (non-causal), planned-lot (base), opener-fixed (causal). Units per planned lot / per contract in section 5; research-lot numbers beside the live-lot numbers in section 1.

## 0. Page 1: per-book verdict and what the sizer is

**Verdict rule (fixed before the placebo draws were read, stated here so it cannot move):** per book, sizer on that book only, integer live lots, running-max governors, in-stack, L6M and HOLD. KEEP = real delta above the p95 of the shuffled-ER placebo in BOTH L6M and HOLD, both deltas positive, and PRE+X' sum not negative. DROP = at or below the placebo mean in L6M or HOLD, or non-positive in both. NO-OP = the sizer changes no live lot of the book (none at the coded x0.5/x1.5; see section 6). Otherwise INCONCLUSIVE with the lean. With MDEs of 5-25k per book most books cannot be verified either way; the table says so rather than forcing a verdict. Placebo = ER multiplier shuffled within book x session x quarter strata (same rounding, same governors), 200 draws per book.

| book | live lot | sizer on this book only, running-max, L6M / HOLD / PRE / X' (MDE L6M) | same, planned-lot governors L6M / HOLD | lot-factor-matched uniform line L6M / HOLD | shuffled-ER placebo mean L6M / HOLD (p95 L6M) | p(placebo >= real) L6M / HOLD | VERDICT | why |
|---|---|---|---|---|---|---|---|---|
| ST | research/2.35 (not live) | +3.2 / +3.8 / +4.5 / +0.2 (9.9) | -0.2 / +0.6 | -1.1 / -0.9 | -1.7 / -1.1 (+2.8) | 0.030 / 0.030 | **KEEP** | above the shuffled-ER p95 in L6M and HOLD (nominal p 0.030/0.030; x6 books 0.18), PRE+X' +4.7k; dollars inside the book's own MDE (9.9k) |
| H6 | H6 4 Asia / 2 NY-AM | -0.2 / -0.2 / +0.0 / -0.4 (3.5) | -0.2 / -0.1 | -1.1 / -0.9 | -1.4 / -1.2 (+0.7) | 0.139 / 0.189 | **DROP** | non-positive in L6M and HOLD (-0.2k / -0.2k); the shuffled placebo is -1.4k only because shuffled lots cut the average lot; real minus placebo +1.2k / +1.0k (p 0.14/0.19) is not enough to pay for it |
| WT | research/2.35 (not live) | +3.1 / +3.4 / +1.7 / +0.5 (4.5) | +2.3 / +2.1 | -0.5 / -0.4 | +0.5 / +0.9 (+2.9) | 0.050 / 0.050 | **KEEP** | above the shuffled-ER p95 in L6M and HOLD (nominal p 0.050/0.050; x6 books 0.30), PRE+X' +2.2k; dollars inside the book's own MDE (4.5k) |
| K6 | K6 2 (Asia/London/NY-AM/NY-PM) | +2.1 / +1.7 / +0.1 / +0.8 (4.7) | -0.7 / -0.7 | -0.3 / -0.2 | -0.5 / -0.5 (+1.9) | 0.035 / 0.055 | **KEEP** | above the shuffled-ER p95 in L6M and HOLD (nominal p 0.035/0.055; x6 books 0.33), PRE+X' +0.9k; dollars inside the book's own MDE (4.7k) |
| U6 | U6 4 (Asia/London) | -0.8 / -0.3 / -0.0 / +0.0 (2.9) | -0.2 / -0.1 | +0.1 / +0.1 | -0.1 / -0.1 (+1.4) | 0.766 / 0.637 | **DROP** | non-positive in L6M and HOLD (-0.8k / -0.3k); the shuffled placebo is -0.1k only because shuffled lots cut the average lot; real minus placebo -0.7k / -0.3k (p 0.77/0.64) is not enough to pay for it |
| P6 | P6 7 (Asia/London/NY-AM) | +6.0 / +6.3 / +3.2 / -0.2 (12.6) | +2.2 / +3.3 | +0.9 / +0.9 | +0.1 / +0.6 (+6.2) | 0.065 / 0.060 | **INCONCLUSIVE (lean keep)** | positive and +5.9k / +5.7k above the placebo mean but p 0.065/0.060 is not below 0.05 in both windows (x6 books 0.39); dollars inside the book's MDE (12.6k) |
| ALL six |  | +12.5 / +13.7 / +9.5 / +0.8 (23.5) | +2.7 / +4.8 | -2.0 / -1.4 | -2.8 / -1.1 (+5.7) | 0.005 / 0.005 | **KEEP** | above the shuffled-ER p95 in L6M and HOLD (nominal p 0.005/0.005; x6 books 0.03), PRE+X' +10.3k; dollars inside the book's own MDE (23.5k) |
| A6 (not in the six-book headline) | A6 1 (every session) | +2.5 / +2.1 / -0.4 / +0.3 (2.3) | +0.0 / +0.1 | n/a | n/a | n/a | **INCONCLUSIVE (no placebo run)** | +2.5k L6M is about the book's MDE (2.3k) and it is 0 with planned-lot locks (+0.0k): the whole effect is the lock multiplier on a 1-lot book; high side only: 1 -> 2 lots when ER >= 0.30, low side 0.5 rounds back to 1 |
| M6 (not in the six-book headline) | M6 2 (London/NY-AM) | -0.7 / -0.7 / +0.2 / +0.7 (2.5) | -1.1 / -1.2 | n/a | n/a | n/a | **DROP (no placebo run)** | negative in L6M/HOLD under both governor readings (-0.7k / -0.7k running-max, -1.1k planned-lot); 2 -> 1/3 |

**Reading the verdicts.** (i) The rule is applied mechanically; the per-book dollars are all INSIDE their own MDE, and with six books tested no single book clears a x6 multiplicity correction by itself; only the six-book sizer does (p 0.005 = none of 200 draws reached it). (ii) The verdicts hold only under the causal running-max lock multiplier: with planned-lot locks the whole sizer is +2.7k L6M / +4.8k HOLD / -2.4k PRE, K6 and U6 and H6 are at or below zero and only P6 (+2.2k) and WT (+2.3k) stay positive, i.e. if D6 does not multiply the day/week locks, drop the sizer on K6 U6 H6. (iii) Net of the rule and of the numbers: P6 = keep (largest and steadiest contributor, positive PRE, but p about 0.06), K6 = weak keep (running-max only), U6 = drop, H6 = drop, ST and WT = keep at research lots (not live, so no live effect); no live book is a no-op at the coded x0.5/x1.5 (A6 is a no-op on its low side).

A6 (PB, live 1) and M6 (MV, live 2) are not in the six-book sizer; their rows are in section 2e (A6 1 lot becomes 1/2 lots at the coded pair, so it is NOT a no-op on the high side; it IS a no-op on the low side, 0.5 rounds up to 1).

**What the sizer is, in six lines (all numbers $k/wk of the stack, in-stack, integer live+ lots, MDE in brackets):**
1. As coded, with the causal running-max governors: L3M +15.3 (39.8), L6M +12.5 (23.5), HOLD +13.7 (21.5), PRE +9.5 (11.8), X' +0.8 (10.9). L6M, HOLD and PRE are all INSIDE their MDEs (23.5 / 21.5 / 11.8); X' is zero. Static (non-causal) reading +14.1 (22.9) L6M; planned-lot governors +2.7 (19.6) L6M / +4.8 (17.7) HOLD / -2.4 (12.0) PRE / +3.9 (11.4) X'. About +9.8k of the +12.5k L6M gain exists only when the day/week locks are multiplied (the lock-multiplier effect), the lot ratio on planned-lot locks is worth +2.7k.
2. Information vs leverage vs lock looseness (whole sizer, running-max): lot-factor-matched uniform scaling -2.0k L6M (the sizer lowers the average lot to 0.85-1.05 of planned, so leverage alone LOSES money); shuffled-ER placebo mean -2.8k L6M (sd 5.1, p95 +5.7, p(placebo >= real) 0.005), HOLD -1.1k (p 0.005); PRE -3.6k vs real +9.5k, X' +1.2k vs +0.8k. With planned-lot governors the placebo mean is -9.2k L6M (p 0.015); with the static sized governors -2.1k (p 0.005). 200 draws.
3. Concentration and stability: 10 of 12 quarters positive, the top-5 L6M weeks carry 107% of the L6M gain (mean without them -1.1k/wk); first/second half of L6M +9.2k / +15.8k.
4. Feature-definition risk: the ER must be the ER of the 20-bar window ending at the LAST CLOSED 5-min bar; 20.8% of signals fire at the exact second a 5-min bar closes (the closing bar is then 'current'). Requiring the bar to be closed strictly before the signal second changes 3.6% of the classes and moves L6M by -0.6k. Using the FORMING bar (1-s price as its close) gives +13.2k L6M (PRE +7.9k). A one-bar-stale ER (D6 using the bar BEFORE the last closed one) gives +4.2k L6M: the sizer loses 8.3k of its +12.5k. A one-bar LOOK-AHEAD would show +21.6k, the size of an accidental leak.
5. Integer lots: at the coded x0.5/x1.5 and round-half-up the sizer is NOT a no-op for any live book: K6 2 -> 1/3, H6 NY-AM 2 -> 1/3, U6 4 -> 2/6, H6 Asia 4 -> 2/6, P6 7 -> 4/11, A6 1 -> 1/2 (low side unchanged). It IS a no-op for A6 at 0.7/1.3, 0.75/1.25 and 0.5/1.0, and for K6/H6-NY-AM/M6 on the low side at 0.75/1.25 and on the high side at 0.5/1.0. Rounding rule matters: half-up +12.5 (23.5) L6M, half-even +10.5 (22.3), floor +9.2 (24.0), fractional (no rounding) +9.7 (24.0) (ceil equals half-up here).
6. Surface: the coded cell sits near the top of its local neighbourhood in L6M/HOLD on the causal reading (mean of its 8 neighbours +8.2k vs coded +12.5k) and the gain is monotone in the threshold (lower = better) and in the upsizing side: every x0.5/x1.0 cell (down-size only) is negative; the cells that beat the coded one are listed in section 1 as POST-HOC observations only.

**Plain sentence.** The ER(20) sizer carries real information beyond leverage and beyond lock looseness (none of the 200 shuffled-ER draws reaches the real six-book delta in L6M or HOLD; the matched-leverage line loses money), but at live lots its dollar gain is inside the MDE in every window, shows up only if D6 multiplies the day/week locks by the running max of the ER multipliers, sits in a handful of weeks (top 5 = 107% of the L6M gain), is essentially P6 plus the not-live ST/WT with K6 marginal and U6/H6 doing nothing, and depends on D6 using exactly the last closed 5-minute bar (one stale bar removes two thirds of it).

## 1. The sensitivity surface (threshold 0.20..0.40 x six multiplier pairs, integer live lots, round half up min 1)

Cells: 5 thresholds x 6 pairs = 30, plus 8 extra (lo 0.4/0.5/0.6 x hi 1.4/1.5/1.6 at threshold 0.30) for a finer local view; each under 4 governor readings x 2 bases at live lots and 3 x 2 at research lots (532 scored runs). 'lo/hi' = multiplier below / at-or-above the threshold; pair 0/1.5 = skip below the threshold (a lot of 0); pair 0.5/1.0 and 1.0/1.5 are one-sided. All deltas vs the same composite without ER ($k/wk, MDE).

### 1a. The coded cell (thr 0.30, 0.5/1.5) under every governor reading, both bases, both lot sets


**live+ integer lots (K6 2 P6 7 U6 4 H6 4/2 M6 2 A6 1, ST WT research/2.35)**

| ER delta, base | governor reading | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| in-stack | causal running-max (headline) | +15.3 (39.8) | +12.5 (23.5) | +13.7 (21.5) | +9.5 (11.8) | +0.8 (10.9) |
| in-stack | day-static sized (non-causal) | +16.4 (39.1) | +14.1 (22.9) | +14.2 (21.3) | +8.1 (12.9) | +1.0 (11.0) |
| in-stack | planned-lot (base) | +1.7 (31.1) | +2.7 (19.6) | +4.8 (17.7) | -2.4 (12.0) | +3.9 (11.4) |
| in-stack | causal opener-fixed | -11.3 (33.5) | -8.7 (18.9) | -3.9 (17.9) | -0.7 (13.1) | +1.2 (9.7) |
| alone | causal running-max (headline) | +17.0 (30.9) | +15.3 (19.9) | +16.6 (18.0) | +0.6 (15.6) | +1.4 (16.1) |
| alone | day-static sized (non-causal) | +19.4 (32.6) | +18.0 (20.4) | +16.8 (19.6) | +2.6 (16.3) | +1.8 (16.4) |
| alone | planned-lot (base) | +24.1 (25.4) | +11.7 (21.4) | +12.5 (18.9) | -6.0 (12.3) | +5.1 (15.7) |
| alone | causal opener-fixed | +0.6 (28.7) | -5.7 (19.9) | -0.4 (19.3) | -2.4 (15.4) | -1.3 (14.8) |

**research lots (fractional)**

| ER delta, base | governor reading | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| in-stack | causal running-max (headline) | +11.6 (89.5) | +22.1 (54.1) | +22.5 (48.3) | +9.8 (24.7) | +3.9 (22.0) |
| in-stack | day-static sized (non-causal) | +15.9 (91.1) | +26.4 (54.0) | +24.5 (48.5) | +12.0 (26.2) | +4.1 (21.9) |
| in-stack | planned-lot (base) | -14.5 (60.0) | -9.9 (43.2) | -5.5 (38.7) | -9.5 (25.5) | +14.5 (22.2) |
| alone | causal running-max (headline) | +60.5 (87.0) | +43.2 (55.8) | +42.2 (49.6) | +0.5 (30.4) | +2.9 (32.4) |
| alone | day-static sized (non-causal) | +61.5 (90.7) | +47.4 (56.8) | +40.8 (52.5) | +5.0 (29.8) | +3.6 (32.8) |
| alone | planned-lot (base) | +53.6 (53.7) | +17.0 (47.7) | +19.5 (42.1) | -8.2 (24.7) | +9.0 (27.0) |


### 1b. The full surface, in-stack, live+ integer lots, causal running-max governors (HEADLINE reading)

| thr / lo-hi | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| 0.20 / 0.5-1.5 | +23.8 (25.0) | +22.3 (19.0) | +19.9 (18.6) | +9.8 (12.3) | +6.2 (10.1) |
| 0.20 / 0.7-1.3 | +17.5 (20.0) | +12.7 (14.7) | +11.1 (13.8) | +7.1 (7.6) | +3.6 (6.1) |
| 0.20 / 0.75-1.25 | +16.7 (19.4) | +12.1 (13.7) | +10.1 (13.2) | +7.3 (7.2) | +2.5 (5.3) |
| 0.20 / 0-1.5 | +16.9 (33.8) | +16.2 (25.3) | +13.4 (23.7) | +4.4 (17.6) | +7.4 (16.5) |
| 0.20 / 0.5-1 | +4.4 (17.9) | -0.9 (13.3) | -0.3 (11.9) | -1.4 (6.7) | +0.5 (5.8) |
| 0.20 / 1-1.5 | +28.4 (22.5) | +26.0 (16.4) | +22.6 (17.6) | +12.5 (10.2) | +4.0 (7.4) |
| 0.25 / 0.5-1.5 | +25.6 (38.5) | +22.9 (23.2) | +22.2 (21.4) | +7.2 (14.2) | +2.9 (11.2) |
| 0.25 / 0.7-1.3 | +20.5 (29.7) | +13.4 (17.7) | +12.7 (16.2) | +4.6 (9.6) | +2.4 (7.4) |
| 0.25 / 0.75-1.25 | +20.1 (28.3) | +12.9 (16.4) | +12.2 (15.3) | +6.4 (8.3) | +0.9 (6.4) |
| 0.25 / 0-1.5 | +19.3 (50.0) | +17.0 (30.7) | +16.5 (27.9) | +1.2 (19.7) | +3.2 (17.2) |
| 0.25 / 0.5-1 | +5.7 (24.4) | -1.7 (15.5) | -0.4 (13.9) | -2.6 (8.5) | -0.5 (6.6) |
| 0.25 / 1-1.5 | +32.8 (29.7) | +26.8 (18.5) | +24.9 (19.0) | +13.1 (10.7) | +3.0 (8.1) |
| 0.30 / 0.5-1.5 **(coded)** | +15.3 (39.8) | +12.5 (23.5) | +13.7 (21.5) | +9.5 (11.8) | +0.8 (10.9) |
| 0.30 / 0.7-1.3 | +11.5 (24.5) | +7.1 (15.7) | +7.6 (14.6) | +7.0 (7.7) | +0.3 (7.2) |
| 0.30 / 0.75-1.25 | +10.9 (23.0) | +7.0 (13.8) | +7.4 (13.2) | +7.9 (7.0) | -0.9 (6.2) |
| 0.30 / 0-1.5 | +5.9 (56.4) | +4.0 (35.5) | +6.0 (31.7) | +2.6 (17.5) | -0.1 (18.4) |
| 0.30 / 0.5-1 | -2.3 (21.0) | -6.7 (14.8) | -4.4 (13.6) | -1.3 (7.4) | -1.9 (7.0) |
| 0.30 / 1-1.5 | +23.0 (25.9) | +19.9 (15.5) | +19.0 (16.8) | +14.0 (9.7) | +1.4 (7.7) |
| 0.35 / 0.5-1.5 | +6.4 (39.7) | +4.4 (22.3) | +5.6 (20.8) | +4.5 (11.7) | +1.5 (10.7) |
| 0.35 / 0.7-1.3 | +4.1 (25.0) | +1.3 (14.6) | +2.1 (13.9) | +5.0 (8.4) | +0.9 (6.9) |
| 0.35 / 0.75-1.25 | +5.1 (24.6) | +2.4 (14.0) | +2.7 (13.7) | +5.9 (7.9) | +0.0 (6.1) |
| 0.35 / 0-1.5 | +3.9 (59.7) | -4.2 (36.5) | -2.2 (33.0) | -5.7 (17.3) | +0.4 (17.7) |
| 0.35 / 0.5-1 | -8.2 (22.5) | -11.3 (14.4) | -8.9 (13.6) | -2.8 (8.1) | -1.4 (7.0) |
| 0.35 / 1-1.5 | +13.1 (28.8) | +13.6 (17.3) | +12.8 (18.2) | +12.9 (10.8) | +2.3 (7.2) |
| 0.40 / 0.5-1.5 | +7.5 (33.8) | +1.4 (19.0) | +2.8 (18.0) | -0.4 (12.8) | -1.0 (11.1) |
| 0.40 / 0.7-1.3 | +1.6 (24.6) | -0.6 (13.7) | +0.6 (13.1) | +2.3 (9.4) | -1.1 (7.6) |
| 0.40 / 0.75-1.25 | +3.3 (24.5) | +1.2 (13.5) | +1.6 (13.0) | +3.8 (8.8) | -1.6 (6.7) |
| 0.40 / 0-1.5 | +10.0 (48.1) | -6.1 (30.6) | -4.0 (28.2) | -9.1 (19.0) | -4.6 (18.7) |
| 0.40 / 0.5-1 | -8.7 (21.4) | -12.0 (13.6) | -9.6 (13.2) | -5.8 (9.2) | -3.2 (7.8) |
| 0.40 / 1-1.5 | +10.2 (28.9) | +11.7 (17.0) | +11.1 (17.6) | +11.6 (10.1) | +0.8 (7.9) |


### 1c. L6M and HOLD pivots under each governor reading (in-stack, live+ integer; $k/wk, MDE of a cell about 19k L6M)

**causal running-max (headline), L6M**

| lo/hi \ thr | 0.20 | 0.25 | 0.30 | 0.35 | 0.40 |
|---|---|---|---|---|---|
| 0.5/1.5 | +22.3 | +22.9 | +12.5 | +4.4 | +1.4 |
| 0.7/1.3 | +12.7 | +13.4 | +7.1 | +1.3 | -0.6 |
| 0.75/1.25 | +12.1 | +12.9 | +7.0 | +2.4 | +1.2 |
| 0/1.5 | +16.2 | +17.0 | +4.0 | -4.2 | -6.1 |
| 0.5/1 | -0.9 | -1.7 | -6.7 | -11.3 | -12.0 |
| 1/1.5 | +26.0 | +26.8 | +19.9 | +13.6 | +11.7 |

**causal running-max (headline), HOLD**

| lo/hi \ thr | 0.20 | 0.25 | 0.30 | 0.35 | 0.40 |
|---|---|---|---|---|---|
| 0.5/1.5 | +19.9 | +22.2 | +13.7 | +5.6 | +2.8 |
| 0.7/1.3 | +11.1 | +12.7 | +7.6 | +2.1 | +0.6 |
| 0.75/1.25 | +10.1 | +12.2 | +7.4 | +2.7 | +1.6 |
| 0/1.5 | +13.4 | +16.5 | +6.0 | -2.2 | -4.0 |
| 0.5/1 | -0.3 | -0.4 | -4.4 | -8.9 | -9.6 |
| 1/1.5 | +22.6 | +24.9 | +19.0 | +12.8 | +11.1 |

**causal running-max (headline), PRE**

| lo/hi \ thr | 0.20 | 0.25 | 0.30 | 0.35 | 0.40 |
|---|---|---|---|---|---|
| 0.5/1.5 | +9.8 | +7.2 | +9.5 | +4.5 | -0.4 |
| 0.7/1.3 | +7.1 | +4.6 | +7.0 | +5.0 | +2.3 |
| 0.75/1.25 | +7.3 | +6.4 | +7.9 | +5.9 | +3.8 |
| 0/1.5 | +4.4 | +1.2 | +2.6 | -5.7 | -9.1 |
| 0.5/1 | -1.4 | -2.6 | -1.3 | -2.8 | -5.8 |
| 1/1.5 | +12.5 | +13.1 | +14.0 | +12.9 | +11.6 |

**causal running-max (headline), X'**

| lo/hi \ thr | 0.20 | 0.25 | 0.30 | 0.35 | 0.40 |
|---|---|---|---|---|---|
| 0.5/1.5 | +6.2 | +2.9 | +0.8 | +1.5 | -1.0 |
| 0.7/1.3 | +3.6 | +2.4 | +0.3 | +0.9 | -1.1 |
| 0.75/1.25 | +2.5 | +0.9 | -0.9 | +0.0 | -1.6 |
| 0/1.5 | +7.4 | +3.2 | -0.1 | +0.4 | -4.6 |
| 0.5/1 | +0.5 | -0.5 | -1.9 | -1.4 | -3.2 |
| 1/1.5 | +4.0 | +3.0 | +1.4 | +2.3 | +0.8 |

**day-static sized (non-causal), L6M**

| lo/hi \ thr | 0.20 | 0.25 | 0.30 | 0.35 | 0.40 |
|---|---|---|---|---|---|
| 0.5/1.5 | +22.6 | +23.8 | +14.1 | +7.1 | +4.3 |
| 0.7/1.3 | +14.1 | +13.9 | +8.2 | +4.3 | +2.1 |
| 0.75/1.25 | +11.9 | +13.0 | +8.4 | +4.8 | +3.2 |
| 0/1.5 | +16.2 | +17.0 | +4.0 | -4.2 | -6.1 |
| 0.5/1 | -0.6 | -1.2 | -5.9 | -9.1 | -10.2 |
| 1/1.5 | +25.6 | +27.4 | +21.4 | +17.2 | +13.6 |

**day-static sized (non-causal), HOLD**

| lo/hi \ thr | 0.20 | 0.25 | 0.30 | 0.35 | 0.40 |
|---|---|---|---|---|---|
| 0.5/1.5 | +19.2 | +22.3 | +14.2 | +7.2 | +5.0 |
| 0.7/1.3 | +12.0 | +13.2 | +8.4 | +4.4 | +3.1 |
| 0.75/1.25 | +10.0 | +12.2 | +8.5 | +4.7 | +3.4 |
| 0/1.5 | +13.4 | +16.5 | +6.0 | -2.2 | -4.0 |
| 0.5/1 | -0.6 | +0.0 | -4.0 | -7.3 | -8.0 |
| 1/1.5 | +22.2 | +25.3 | +20.2 | +16.1 | +12.8 |

**day-static sized (non-causal), PRE**

| lo/hi \ thr | 0.20 | 0.25 | 0.30 | 0.35 | 0.40 |
|---|---|---|---|---|---|
| 0.5/1.5 | +10.8 | +8.3 | +8.1 | +2.7 | -0.7 |
| 0.7/1.3 | +7.2 | +5.0 | +5.4 | +2.8 | +1.3 |
| 0.75/1.25 | +7.3 | +6.5 | +7.0 | +3.9 | +2.5 |
| 0/1.5 | +4.4 | +1.2 | +2.6 | -5.7 | -9.1 |
| 0.5/1 | -1.5 | -2.5 | -2.4 | -4.7 | -7.0 |
| 1/1.5 | +12.3 | +13.3 | +12.8 | +10.7 | +10.0 |

**day-static sized (non-causal), X'**

| lo/hi \ thr | 0.20 | 0.25 | 0.30 | 0.35 | 0.40 |
|---|---|---|---|---|---|
| 0.5/1.5 | +6.5 | +3.8 | +1.0 | +1.2 | -1.3 |
| 0.7/1.3 | +3.9 | +2.8 | +0.5 | +1.0 | -1.4 |
| 0.75/1.25 | +2.7 | +1.3 | -0.8 | -0.0 | -1.8 |
| 0/1.5 | +7.4 | +3.2 | -0.1 | +0.4 | -4.6 |
| 0.5/1 | +0.6 | -0.2 | -1.7 | -1.4 | -3.3 |
| 1/1.5 | +4.3 | +3.4 | +1.6 | +2.0 | +0.5 |

**planned-lot (base), L6M**

| lo/hi \ thr | 0.20 | 0.25 | 0.30 | 0.35 | 0.40 |
|---|---|---|---|---|---|
| 0.5/1.5 | -1.1 | +5.0 | +2.7 | +1.3 | +0.2 |
| 0.7/1.3 | -2.9 | +0.0 | -0.0 | +2.1 | +2.9 |
| 0.75/1.25 | -2.7 | -0.1 | +0.8 | +1.5 | +2.1 |
| 0/1.5 | -7.9 | +0.6 | -5.0 | -7.0 | -11.7 |
| 0.5/1 | -0.7 | -1.4 | -6.3 | -9.0 | -9.5 |
| 1/1.5 | -5.4 | +1.0 | +0.1 | -1.0 | -0.6 |

**planned-lot (base), HOLD**

| lo/hi \ thr | 0.20 | 0.25 | 0.30 | 0.35 | 0.40 |
|---|---|---|---|---|---|
| 0.5/1.5 | -1.5 | +6.0 | +4.8 | +1.5 | +0.7 |
| 0.7/1.3 | -3.1 | +0.9 | +1.2 | +1.8 | +3.1 |
| 0.75/1.25 | -3.0 | +0.1 | +1.2 | +0.7 | +1.5 |
| 0/1.5 | -7.2 | +2.8 | -1.1 | -5.2 | -8.8 |
| 0.5/1 | -0.7 | -0.2 | -4.2 | -7.1 | -7.6 |
| 1/1.5 | -6.5 | +0.3 | +0.5 | -1.5 | -1.3 |

**planned-lot (base), PRE**

| lo/hi \ thr | 0.20 | 0.25 | 0.30 | 0.35 | 0.40 |
|---|---|---|---|---|---|
| 0.5/1.5 | -0.8 | -2.4 | -2.4 | -4.1 | -7.6 |
| 0.7/1.3 | -0.6 | -0.5 | +0.9 | -0.4 | -2.7 |
| 0.75/1.25 | -0.9 | -0.5 | +1.2 | +0.3 | -1.2 |
| 0/1.5 | -0.3 | -6.5 | -2.4 | -7.9 | -10.8 |
| 0.5/1 | -1.6 | -2.3 | -2.2 | -5.2 | -8.0 |
| 1/1.5 | +1.0 | -0.6 | +0.1 | +1.1 | +3.2 |

**planned-lot (base), X'**

| lo/hi \ thr | 0.20 | 0.25 | 0.30 | 0.35 | 0.40 |
|---|---|---|---|---|---|
| 0.5/1.5 | +6.6 | +6.5 | +3.9 | +3.6 | -0.3 |
| 0.7/1.3 | +4.9 | +5.2 | +2.4 | +1.9 | -0.2 |
| 0.75/1.25 | +3.8 | +4.4 | +1.7 | +0.7 | -0.4 |
| 0/1.5 | +10.5 | +7.8 | +3.7 | +0.5 | -4.8 |
| 0.5/1 | +0.7 | -0.2 | -1.4 | -1.2 | -3.3 |
| 1/1.5 | +8.3 | +9.4 | +7.3 | +6.4 | +4.3 |

**causal opener-fixed, L6M**

| lo/hi \ thr | 0.20 | 0.25 | 0.30 | 0.35 | 0.40 |
|---|---|---|---|---|---|
| 0.5/1.5 | +1.5 | -0.7 | -8.7 | -10.6 | -9.0 |
| 0.7/1.3 | +3.1 | +1.2 | -6.6 | -7.3 | -8.6 |
| 0.75/1.25 | +3.8 | +3.7 | -3.6 | -3.9 | -5.2 |
| 0/1.5 | +16.2 | +17.0 | +4.0 | -4.2 | -6.1 |
| 0.5/1 | -7.8 | -10.2 | -16.5 | -18.7 | -18.6 |
| 1/1.5 | +17.2 | +18.3 | +9.8 | +8.8 | +7.0 |

**causal opener-fixed, HOLD**

| lo/hi \ thr | 0.20 | 0.25 | 0.30 | 0.35 | 0.40 |
|---|---|---|---|---|---|
| 0.5/1.5 | +3.9 | +2.6 | -3.9 | -7.5 | -6.4 |
| 0.7/1.3 | +3.2 | +1.7 | -4.8 | -6.3 | -7.3 |
| 0.75/1.25 | +3.3 | +3.5 | -2.4 | -3.4 | -4.8 |
| 0/1.5 | +13.4 | +16.5 | +6.0 | -2.2 | -4.0 |
| 0.5/1 | -6.3 | -8.2 | -13.2 | -16.1 | -16.5 |
| 1/1.5 | +14.6 | +16.0 | +9.1 | +7.4 | +5.5 |

**causal opener-fixed, PRE**

| lo/hi \ thr | 0.20 | 0.25 | 0.30 | 0.35 | 0.40 |
|---|---|---|---|---|---|
| 0.5/1.5 | +2.2 | -1.7 | -0.7 | -4.1 | -10.4 |
| 0.7/1.3 | +2.0 | -1.2 | -1.2 | -2.5 | -6.4 |
| 0.75/1.25 | +3.8 | +1.9 | +2.1 | +0.6 | -3.2 |
| 0/1.5 | +4.4 | +1.2 | +2.6 | -5.7 | -9.1 |
| 0.5/1 | -4.8 | -7.0 | -6.8 | -8.6 | -11.8 |
| 1/1.5 | +11.2 | +8.3 | +9.2 | +8.1 | +5.5 |

**causal opener-fixed, X'**

| lo/hi \ thr | 0.20 | 0.25 | 0.30 | 0.35 | 0.40 |
|---|---|---|---|---|---|
| 0.5/1.5 | +5.6 | +2.9 | +1.2 | +3.0 | +2.1 |
| 0.7/1.3 | +4.3 | +3.7 | +1.2 | +1.1 | +0.0 |
| 0.75/1.25 | +2.7 | +1.8 | +0.6 | +0.9 | -0.1 |
| 0/1.5 | +7.4 | +3.2 | -0.1 | +0.4 | -4.6 |
| 0.5/1 | +1.1 | +0.5 | -1.2 | -0.7 | -1.9 |
| 1/1.5 | +5.5 | +4.0 | +2.9 | +3.5 | +2.6 |


### 1d. Eight neighbours of the coded cell and their mean

Neighbour set 1 = threshold {0.25, 0.30, 0.35} x pair {0.7/1.3, 0.5/1.5, 0/1.5} (the pair axis ordered by aggressiveness) minus the coded cell; set 2 = lo {0.4, 0.5, 0.6} x hi {1.4, 1.5, 1.6} at threshold 0.30 minus the coded cell (a 3 x 3 in the multipliers; with integer lots many of these round to the same lots as the coded cell, which is itself a result). Full 30+8-cell list per governor: `out/ersizer/surface.csv`.

| lots | base | governor | window | coded | mean of 8 neighbours (thr 0.25/0.30/0.35 x 0.7-1.3 / 0.5-1.5 / 0-1.5) | worst neighbour | mean of 8 (lo 0.4/0.5/0.6 x hi 1.4/1.5/1.6 at 0.30) | MDE |
|---|---|---|---|---|---|---|---|---|
| live+ | in-stack | base | L6M | +2.7 | -0.4 | -7.0 | +1.4 | 19.6 |
| live+ | in-stack | base | HOLD | +4.8 | +1.0 | -5.2 | +3.3 | 17.7 |
| live+ | in-stack | base | PRE | -2.4 | -2.9 | -7.9 | -1.6 | 12.0 |
| live+ | in-stack | base | X' | +3.9 | +3.9 | +0.5 | +3.6 | 11.4 |
| live+ | in-stack | sized | L6M | +14.1 | +9.3 | -4.2 | +11.9 | 22.9 |
| live+ | in-stack | sized | HOLD | +14.2 | +9.5 | -2.2 | +12.2 | 21.3 |
| live+ | in-stack | sized | PRE | +8.1 | +2.8 | -5.7 | +7.1 | 12.9 |
| live+ | in-stack | sized | X' | +1.0 | +1.6 | -0.1 | +0.8 | 11.0 |
| live+ | in-stack | runmax | L6M | +12.5 | +8.2 | -4.2 | +10.2 | 23.5 |
| live+ | in-stack | runmax | HOLD | +13.7 | +8.8 | -2.2 | +11.5 | 21.5 |
| live+ | in-stack | runmax | PRE | +9.5 | +3.3 | -5.7 | +7.7 | 11.8 |
| live+ | in-stack | runmax | X' | +0.8 | +1.4 | -0.1 | +0.7 | 10.9 |
| live+ | in-stack | first | L6M | -8.7 | -0.9 | -10.6 | -9.3 | 18.9 |
| live+ | in-stack | first | HOLD | -3.9 | +0.7 | -7.5 | -4.8 | 17.9 |
| live+ | in-stack | first | PRE | -0.7 | -1.6 | -5.7 | -1.0 | 13.1 |
| live+ | in-stack | first | X' | +1.2 | +1.9 | -0.1 | +0.5 | 9.7 |
| live+ | alone | base | L6M | +11.7 | +5.8 | +1.7 | +9.8 | 21.4 |
| live+ | alone | base | HOLD | +12.5 | +6.2 | +3.0 | +10.6 | 18.9 |
| live+ | alone | base | PRE | -6.0 | -4.9 | -8.7 | -4.3 | 12.3 |
| live+ | alone | base | X' | +5.1 | +3.8 | +2.0 | +3.9 | 15.7 |
| live+ | alone | sized | L6M | +18.0 | +13.1 | +6.0 | +16.2 | 20.4 |
| live+ | alone | sized | HOLD | +16.8 | +12.5 | +6.5 | +15.2 | 19.6 |
| live+ | alone | sized | PRE | +2.6 | +0.2 | -4.3 | +2.7 | 16.3 |
| live+ | alone | sized | X' | +1.8 | +1.1 | -2.1 | +1.6 | 16.4 |
| live+ | alone | runmax | L6M | +15.3 | +12.3 | +5.0 | +14.2 | 19.9 |
| live+ | alone | runmax | HOLD | +16.6 | +12.6 | +5.6 | +15.6 | 18.0 |
| live+ | alone | runmax | PRE | +0.6 | -0.1 | -4.3 | +1.3 | 15.6 |
| live+ | alone | runmax | X' | +1.4 | +0.4 | -2.4 | +0.6 | 16.1 |
| live+ | alone | first | L6M | -5.7 | +2.5 | -8.7 | -6.4 | 19.9 |
| live+ | alone | first | HOLD | -0.4 | +4.5 | -4.7 | -1.2 | 19.3 |
| live+ | alone | first | PRE | -2.4 | -1.3 | -4.3 | -2.0 | 15.4 |
| live+ | alone | first | X' | -1.3 | +0.4 | -2.9 | -1.1 | 14.8 |
| research | in-stack | base | L6M | -9.9 | -10.9 | -27.9 | -7.7 | 43.2 |
| research | in-stack | base | HOLD | -5.5 | -6.5 | -20.3 | -4.1 | 38.7 |
| research | in-stack | base | PRE | -9.5 | -9.7 | -20.4 | -7.9 | 25.5 |
| research | in-stack | base | X' | +14.5 | +13.3 | +6.4 | +14.4 | 22.2 |
| research | in-stack | sized | L6M | +26.4 | +13.9 | -20.7 | +25.1 | 54.0 |
| research | in-stack | sized | HOLD | +24.5 | +14.3 | -14.6 | +23.4 | 48.5 |
| research | in-stack | sized | PRE | +12.0 | +1.0 | -18.1 | +11.2 | 26.2 |
| research | in-stack | sized | X' | +4.1 | +4.4 | +2.0 | +4.3 | 21.9 |
| research | in-stack | runmax | L6M | +22.1 | +10.6 | -20.7 | +19.1 | 54.1 |
| research | in-stack | runmax | HOLD | +22.5 | +11.9 | -14.6 | +20.1 | 48.3 |
| research | in-stack | runmax | PRE | +9.8 | +0.3 | -18.1 | +7.7 | 24.7 |
| research | in-stack | runmax | X' | +3.9 | +4.0 | +0.7 | +4.0 | 22.0 |
| research | alone | base | L6M | +17.0 | +12.1 | +4.7 | +16.0 | 47.7 |
| research | alone | base | HOLD | +19.5 | +13.9 | +9.9 | +17.4 | 42.1 |
| research | alone | base | PRE | -8.2 | -9.1 | -14.0 | -8.9 | 24.7 |
| research | alone | base | X' | +9.0 | +9.6 | +5.3 | +9.7 | 27.0 |
| research | alone | sized | L6M | +47.4 | +35.7 | +17.8 | +43.5 | 56.8 |
| research | alone | sized | HOLD | +40.8 | +32.5 | +19.8 | +37.7 | 52.5 |
| research | alone | sized | PRE | +5.0 | -1.6 | -11.8 | +5.0 | 29.8 |
| research | alone | sized | X' | +3.6 | +2.7 | -0.6 | +3.8 | 32.8 |
| research | alone | runmax | L6M | +43.2 | +32.1 | +14.5 | +40.9 | 55.8 |
| research | alone | runmax | HOLD | +42.2 | +30.9 | +13.9 | +40.2 | 49.6 |
| research | alone | runmax | PRE | +0.5 | -2.2 | -11.8 | +1.3 | 30.4 |
| research | alone | runmax | X' | +2.9 | +1.8 | -1.1 | +3.3 | 32.4 |


### 1e. Cells that beat the coded one: POST-HOC OBSERVATION ONLY, never a recommendation

The coded sizer is itself post-hoc-selected, so 'beats the coded cell' is a statement about 30 correlated cells on windows that have been looked at hundreds of times. None of these is tiered or proposed.

| lots | base | governor | cells (of 30 grid cells) with L6M above the coded cell | of which also above in HOLD | and PRE and X' | best cell by L6M (post-hoc) | its L6M / HOLD / PRE / X' |
|---|---|---|---|---|---|---|---|
| live+ | in-stack | runmax | 11 | 6 | 4 | thr 0.25 1/1.5 | +26.8 / +24.9 / +13.1 / +3.0 |
| live+ | in-stack | sized | 9 | 7 | 6 | thr 0.25 1/1.5 | +27.4 / +25.3 / +13.3 / +3.4 |
| live+ | in-stack | base | 2 | 1 | 1 | thr 0.25 0.5/1.5 | +5.0 / +6.0 / -2.4 / +6.5 |
| live+ | in-stack | first | 23 | 17 | 11 | thr 0.25 1/1.5 | +18.3 / +16.0 / +8.3 / +4.0 |
| live+ | alone | runmax | 8 | 4 | 1 | thr 0.25 0/1.5 | +22.3 / +21.3 / +0.0 / -2.1 |
| live+ | alone | sized | 4 | 3 | 1 | thr 0.25 0/1.5 | +22.3 / +21.3 / +0.0 / -2.1 |
| live+ | alone | base | 0 | 0 | 0 | thr 0.30 0.5/1.5 | +11.7 / +12.5 / -6.0 / +5.1 |
| live+ | alone | first | 22 | 18 | 15 | thr 0.25 0/1.5 | +22.3 / +21.3 / +0.0 / -2.1 |
| research | in-stack | runmax | 9 | 7 | 2 | thr 0.25 1/1.5 | +48.9 / +42.7 / +22.7 / +6.1 |
| research | in-stack | sized | 9 | 7 | 4 | thr 0.25 1/1.5 | +50.0 / +43.5 / +23.3 / +6.6 |
| research | in-stack | base | 15 | 12 | 2 | thr 0.35 0.7/1.3 | +2.0 / +2.3 / -1.6 / +6.4 |
| research | alone | runmax | 6 | 2 | 0 | thr 0.25 0/1.5 | +53.3 / +50.7 / -3.8 / -0.6 |
| research | alone | sized | 2 | 2 | 0 | thr 0.25 0.5/1.5 | +56.5 / +48.6 / +1.8 / +2.2 |
| research | alone | base | 6 | 2 | 1 | thr 0.40 0.75/1.25 | +21.7 / +19.7 / -13.1 / +3.1 |


### 1f. Per-book surface (sizer on one book only, in-stack, live+ integer, running-max then planned-lot; 10 cells per book)

Same book-only construction as section 2; thresholds at the coded pair and the six pairs at threshold 0.30. 'coded rank' = rank of the coded cell among the book's 10 cells (1 = best).

**running-max, L6M**

| book | thr 0.20 (0.5/1.5) | thr 0.25 (0.5/1.5) | thr 0.30 (0.5/1.5) | thr 0.35 (0.5/1.5) | thr 0.40 (0.5/1.5) | 0.7/1.3 (thr 0.30) | 0.75/1.25 (thr 0.30) | 0/1.5 (thr 0.30) | 0.5/1 (thr 0.30) | 1/1.5 (thr 0.30) | mean of the other 9 cells | coded rank among the 10 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ST | +6.4 | +7.2 | +3.2 | -2.5 | -3.7 | +1.8 | +1.4 | -0.4 | -1.6 | +4.6 | +1.5 | 4 / 10 |
| H6 | +0.7 | +0.7 | -0.2 | -1.1 | -2.3 | -0.2 | +0.4 | -2.6 | -2.6 | +2.4 | -0.5 | 5 / 10 |
| WT | +3.1 | +1.5 | +3.1 | +1.8 | +2.2 | +0.1 | +0.6 | -1.2 | -0.8 | +2.2 | +1.1 | 2 / 10 |
| K6 | +1.2 | +1.6 | +2.1 | +1.4 | +0.3 | +2.1 | +1.2 | +2.2 | -0.6 | +1.2 | +1.2 | 2 / 10 |
| U6 | +0.0 | -0.0 | -0.8 | -0.0 | -0.2 | -0.4 | -0.4 | -1.2 | -0.6 | -0.1 | -0.3 | 9 / 10 |
| P6 | +10.9 | +11.9 | +6.0 | +5.1 | +5.2 | +3.3 | +3.3 | +3.9 | -1.0 | +9.1 | +5.7 | 4 / 10 |


**running-max, HOLD**

| book | thr 0.20 (0.5/1.5) | thr 0.25 (0.5/1.5) | thr 0.30 (0.5/1.5) | thr 0.35 (0.5/1.5) | thr 0.40 (0.5/1.5) | 0.7/1.3 (thr 0.30) | 0.75/1.25 (thr 0.30) | 0/1.5 (thr 0.30) | 0.5/1 (thr 0.30) | 1/1.5 (thr 0.30) | mean of the other 9 cells | coded rank among the 10 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ST | +5.4 | +7.3 | +3.8 | -1.3 | -3.0 | +2.2 | +1.7 | +1.8 | -0.6 | +4.3 | +2.0 | 4 / 10 |
| H6 | +0.7 | +0.7 | -0.2 | -1.1 | -2.2 | -0.2 | +0.2 | -2.2 | -2.2 | +2.1 | -0.5 | 5 / 10 |
| WT | +3.4 | +2.2 | +3.4 | +2.4 | +2.5 | +0.1 | +0.5 | -1.4 | -0.3 | +1.7 | +1.2 | 1 / 10 |
| K6 | +0.8 | +1.2 | +1.7 | +1.1 | +0.8 | +1.7 | +1.0 | +1.9 | -0.5 | +1.0 | +1.0 | 2 / 10 |
| U6 | +0.3 | +0.1 | -0.3 | +0.3 | +0.4 | -0.2 | -0.2 | -0.6 | -0.4 | +0.1 | -0.0 | 8 / 10 |
| P6 | +9.4 | +10.9 | +6.3 | +4.6 | +4.7 | +3.7 | +3.7 | +3.7 | -0.6 | +9.5 | +5.5 | 4 / 10 |


**planned-lot, L6M**

| book | thr 0.20 (0.5/1.5) | thr 0.25 (0.5/1.5) | thr 0.30 (0.5/1.5) | thr 0.35 (0.5/1.5) | thr 0.40 (0.5/1.5) | 0.7/1.3 (thr 0.30) | 0.75/1.25 (thr 0.30) | 0/1.5 (thr 0.30) | 0.5/1 (thr 0.30) | 1/1.5 (thr 0.30) | mean of the other 9 cells | coded rank among the 10 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ST | -7.3 | -3.2 | -0.2 | -3.0 | -1.4 | +0.7 | +0.3 | -4.9 | -1.3 | -5.4 | -2.8 | 3 / 10 |
| H6 | +0.3 | +0.3 | -0.2 | -1.0 | -2.4 | +0.2 | +0.9 | -3.1 | -2.6 | +1.6 | -0.6 | 6 / 10 |
| WT | +2.3 | +3.6 | +2.3 | +3.0 | +3.2 | +0.1 | +0.4 | -2.2 | -0.8 | +0.9 | +1.2 | 5 / 10 |
| K6 | -1.0 | -0.3 | -0.7 | +0.4 | -0.3 | -0.7 | -0.6 | +1.2 | -0.1 | -0.6 | -0.2 | 8 / 10 |
| U6 | +0.4 | +0.3 | -0.2 | +0.0 | -0.5 | -0.1 | -0.1 | -1.0 | -0.6 | +0.2 | -0.2 | 7 / 10 |
| P6 | +3.1 | +4.4 | +2.2 | +3.4 | +2.8 | -0.0 | -0.0 | +1.6 | -0.9 | +2.7 | +1.9 | 6 / 10 |


Per-session surfaces were not run cell by cell (a 6-session x 30-cell x 4-governor surface adds 720 runs for sessions that are mostly zero-lot); the per-session effect at the coded cell is in section 4.

## 2. Information vs leverage: lot-factor-matched uniform line and shuffled-ER placebo, separately per book

Definitions. Real = the coded sizer on that book only (other books unsized). Uniform line = every lot of that book multiplied by one constant c_b equal to the book's average effective lot factor under the coded sizer over the taken trades (ST 0.93, H6 0.89, WT 0.87, K6 0.92, U6 1.10, P6 1.05 at live+ lots; fractional, so it is a leverage reference not an executable rule). Placebo = the multiplier column permuted within book x session x quarter strata (same marginal lot mix, same rounding, no information), 200 draws per book (draw count in the table). 'Information' = real minus uniform at equal average leverage; 'real minus placebo mean' = what the ER VALUE adds beyond the lot mix and the multiplied locks. Both in-stack.

### 2a. causal running-max

| book | ER sizer: L6M | HOLD | PRE | X' | uniform (lot-factor-matched) L6M | HOLD | PRE | X' | shuffled-ER placebo mean L6M (p95) | HOLD | PRE | X' | draws | real minus placebo mean L6M / HOLD | p (placebo >= real) L6M / HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ST | +3.2 (9.9) | +3.8 (8.8) | +4.5 (5.1) | +0.2 (4.2) | -1.1 | -0.9 | -0.5 | -0.1 | -1.7 (+2.8) | -1.1 | -1.0 | -0.0 | 200 | +4.9 / +4.9 | 0.030 / 0.030 |
| H6 | -0.2 (3.5) | -0.2 (3.2) | +0.0 (2.5) | -0.4 (1.7) | -1.1 | -0.9 | -0.3 | +0.0 | -1.4 (+0.7) | -1.2 | -0.1 | +0.1 | 200 | +1.2 / +1.0 | 0.139 / 0.189 |
| WT | +3.1 (4.5) | +3.4 (4.5) | +1.7 (3.4) | +0.5 (2.4) | -0.5 | -0.4 | -0.4 | -0.1 | +0.5 (+2.9) | +0.9 | -0.2 | +0.4 | 200 | +2.7 / +2.4 | 0.050 / 0.050 |
| K6 | +2.1 (4.7) | +1.7 (4.2) | +0.1 (2.3) | +0.8 (2.0) | -0.3 | -0.2 | -0.3 | +0.0 | -0.5 (+1.9) | -0.5 | +0.0 | +0.2 | 200 | +2.6 / +2.2 | 0.035 / 0.055 |
| U6 | -0.8 (2.9) | -0.3 (2.6) | -0.0 (1.7) | +0.0 (1.7) | +0.1 | +0.1 | +0.2 | +0.2 | -0.1 (+1.4) | -0.1 | +0.3 | +0.2 | 200 | -0.7 / -0.3 | 0.766 / 0.637 |
| P6 | +6.0 (12.6) | +6.3 (11.8) | +3.2 (7.2) | -0.2 (6.6) | +0.9 | +0.9 | +0.6 | +0.2 | +0.1 (+6.2) | +0.6 | -1.8 | +0.3 | 200 | +5.9 / +5.7 | 0.065 / 0.060 |
| ALL six | +12.5 (23.5) | +13.7 (21.5) | +9.5 (11.8) | +0.8 (10.9) | -2.0 | -1.4 | -0.7 | +0.3 | -2.8 (+5.7) | -1.1 | -3.6 | +1.2 | 200 | +15.4 / +14.8 | 0.005 / 0.005 |

### 2a. planned-lot governors

| book | ER sizer: L6M | HOLD | PRE | X' | uniform (lot-factor-matched) L6M | HOLD | PRE | X' | shuffled-ER placebo mean L6M (p95) | HOLD | PRE | X' | draws | real minus placebo mean L6M / HOLD | p (placebo >= real) L6M / HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ST | -0.2 (10.1) | +0.6 (8.8) | -1.5 (5.1) | +2.2 (4.4) | -1.4 | -0.9 | +0.6 | +0.4 | -4.3 (+0.3) | -3.6 | -1.7 | +0.3 | 200 | +4.1 / +4.2 | 0.109 / 0.060 |
| H6 | -0.2 (3.9) | -0.1 (3.5) | +0.2 (1.9) | -0.3 (1.7) | -1.4 | -1.2 | -0.0 | +0.0 | -1.6 (+0.2) | -1.4 | -0.0 | +0.1 | 200 | +1.4 / +1.3 | 0.144 / 0.129 |
| WT | +2.3 (5.3) | +2.1 (4.9) | +1.7 (3.1) | +0.4 (2.7) | +0.2 | -0.1 | +0.2 | -0.6 | +0.3 (+2.7) | +0.4 | +0.0 | +0.3 | 200 | +2.0 / +1.7 | 0.114 / 0.114 |
| K6 | -0.7 (4.7) | -0.7 (4.1) | +0.4 (2.2) | +0.9 (2.0) | -0.3 | -0.4 | +0.0 | +0.3 | -0.9 (+1.4) | -0.9 | -0.5 | +0.3 | 200 | +0.2 / +0.3 | 0.413 / 0.348 |
| U6 | -0.2 (2.6) | -0.1 (2.4) | -0.5 (1.8) | +0.0 (1.7) | +0.1 | +0.1 | +0.1 | +0.2 | +0.0 (+1.4) | -0.0 | +0.1 | +0.2 | 200 | -0.2 / -0.0 | 0.622 / 0.567 |
| P6 | +2.2 (11.7) | +3.3 (10.7) | -2.5 (7.3) | +0.7 (6.5) | +0.1 | +0.2 | -0.2 | -0.8 | -2.9 (+3.0) | -2.1 | -2.3 | -0.3 | 200 | +5.2 / +5.4 | 0.075 / 0.050 |
| ALL six | +2.7 (19.6) | +4.8 (17.7) | -2.4 (12.0) | +3.9 (11.4) | -3.1 | -2.6 | +0.7 | -0.6 | -9.2 (-1.0) | -7.5 | -5.6 | +0.9 | 200 | +12.0 / +12.2 | 0.015 / 0.015 |


### 2b. Day-static governors, ALL six books (the reading in which the shuffled placebo was reported to earn most)

| | L6M | HOLD | PRE | X' |
|---|---|---|---|---|
| real (static) | +14.1 | +14.2 | +8.1 | +1.0 |
| shuffled-ER placebo mean | -2.1 | -1.3 | -2.9 | +1.2 |
| placebo p95 | +5.7 | +6.3 | +2.8 | +6.2 |
| p(placebo >= real) | 0.005 | 0.005 | 0.005 | 0.532 |

Reconciliation with DS3_SUNDAY_STACK: its 'shuffled-ER placebo earns +9k live / +54k research' is the shuffled composite measured against the AS-IS stack, so it contains the five other pieces. Here the placebo is measured against the same composite WITHOUT the ER sizer. The composite without ER is itself +20.8k L6M / +18.0k HOLD / +6.8k PRE / +8.6k X' vs the as-is stack (live+ integer lots), which is where the placebo's 'earnings' come from; relative to the no-ER composite the placebo is -2.1k L6M static / -2.8k running-max.


### 2c. Alone on the as-is stack (the SUNDAY_STACK headline reading), all six books, three governor readings

| governor | real L6M / HOLD / PRE / X' | matched uniform L6M / HOLD | shuffled-ER mean L6M / HOLD / PRE / X' (p95 L6M) | draws | p(placebo >= real) L6M / HOLD |
|---|---|---|---|---|---|
| causal running-max (headline) | +15.3 / +16.6 / +0.6 / +1.4 | -1.7 / -1.1 | -0.5 / +1.2 / -6.3 / +0.1 (+9.7) | 200 | 0.015 / 0.010 |
| planned-lot (base) | +11.7 / +12.5 / -6.0 / +5.1 | +1.9 / +1.6 | -4.6 / -3.7 / -5.2 / +1.7 (+5.1) | 200 | 0.005 / 0.005 |
| day-static sized (non-causal) | +18.0 / +16.8 / +2.6 / +1.8 | n/a | -0.4 / +0.2 / -4.2 / +1.3 (+8.8) | 200 | 0.010 / 0.010 |

### 2d. Pair-by-pair: is the gain information or leverage? (all six books, in-stack, threshold 0.30; uniform line at the pair's own per-book lot factors)

For pair 0/1.5 (skip below the threshold) the lot factor is computed over the baseline trade set, because a skipped trade has no lot.

| pair lo/hi (thr 0.30) | ER sizer L3M | L6M | HOLD | PRE | X' | matched uniform line (same per-book lot factors, fractional) L6M | HOLD | PRE | X' | ER minus uniform L6M | HOLD | PRE | X' | lot factors (book: factor) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0.5/1.5 | +15.3 | +12.5 | +13.7 | +9.5 | +0.8 | -2.0 | -1.4 | -0.7 | +0.3 | +14.5 | +15.1 | +10.2 | +0.6 | ST 0.93, H6 0.89, WT 0.87, K6 0.92, U6 1.10, P6 1.05 |
| 0.7/1.3 | +11.5 | +7.1 | +7.6 | +7.0 | +0.3 | -2.0 | -1.6 | -1.0 | -0.0 | +9.1 | +9.2 | +7.9 | +0.3 | ST 0.96, H6 0.93, WT 0.93, K6 0.92, U6 1.05, P6 0.99 |
| 0.75/1.25 | +10.9 | +7.0 | +7.4 | +7.9 | -0.9 | +0.2 | +0.2 | +0.5 | -0.1 | +6.9 | +7.2 | +7.4 | -0.9 | ST 0.96, H6 1.03, WT 0.94, K6 1.22, U6 1.05, P6 0.99 |
| 0/1.5 | +5.9 | +4.0 | +6.0 | +2.6 | -0.1 | -16.3 | -13.9 | -8.7 | -2.0 | +20.3 | +19.9 | +11.4 | +1.8 | ST 0.65, H6 0.59, WT 0.61, K6 0.66, U6 0.90, P6 0.76 |
| 0.5/1 | -2.3 | -6.7 | -4.4 | -1.3 | -1.9 | -13.5 | -11.6 | -7.6 | -2.0 | +6.7 | +7.2 | +6.3 | +0.1 | ST 0.71, H6 0.70, WT 0.69, K6 0.71, U6 0.80, P6 0.78 |
| 1/1.5 | +23.0 | +19.9 | +19.0 | +14.0 | +1.4 | +11.6 | +10.3 | +7.0 | +2.2 | +8.2 | +8.7 | +6.9 | -0.9 | ST 1.22, H6 1.20, WT 1.19, K6 1.22, U6 1.30, P6 1.28 |


(planned-lot governors)

| pair lo/hi (thr 0.30) | ER sizer L3M | L6M | HOLD | PRE | X' | matched uniform line (same per-book lot factors, fractional) L6M | HOLD | PRE | X' | ER minus uniform L6M | HOLD | PRE | X' | lot factors (book: factor) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0.5/1.5 | +1.7 | +2.7 | +4.8 | -2.4 | +3.9 | -2.9 | -2.4 | +1.1 | -0.2 | +5.6 | +7.2 | -3.6 | +4.0 | ST 0.93, H6 0.89, WT 0.88, K6 0.93, U6 1.10, P6 1.06 |
| 0.7/1.3 | +0.6 | -0.0 | +1.2 | +0.9 | +2.4 | -1.7 | -1.7 | +1.3 | +1.1 | +1.7 | +2.9 | -0.4 | +1.3 | ST 0.96, H6 0.93, WT 0.93, K6 0.93, U6 1.05, P6 0.99 |
| 0.75/1.25 | -0.9 | +0.8 | +1.2 | +1.2 | +1.7 | +1.0 | +0.6 | +1.0 | +1.6 | -0.2 | +0.6 | +0.2 | +0.1 | ST 0.97, H6 1.03, WT 0.94, K6 1.22, U6 1.05, P6 0.99 |
| 0/1.5 | -1.9 | -5.0 | -1.1 | -2.4 | +3.7 | -13.5 | -11.1 | -7.9 | -2.2 | +8.5 | +10.0 | +5.4 | +5.9 | ST 0.65, H6 0.59, WT 0.61, K6 0.66, U6 0.90, P6 0.76 |
| 0.5/1 | -2.7 | -6.3 | -4.2 | -2.2 | -1.4 | -12.1 | -10.0 | -5.2 | -2.2 | +5.8 | +5.8 | +3.0 | +0.7 | ST 0.71, H6 0.70, WT 0.68, K6 0.71, U6 0.80, P6 0.78 |
| 1/1.5 | -4.3 | +0.1 | +0.5 | +0.1 | +7.3 | -1.8 | -1.9 | +1.6 | +5.7 | +1.9 | +2.4 | -1.6 | +1.7 | ST 1.22, H6 1.20, WT 1.21, K6 1.22, U6 1.30, P6 1.28 |


### 2e. M6 (MV) and A6 (PB): the sizer applied to them too (not in the headline; in-stack, running-max / planned-lot)

| sizer on | governor | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| A6 only (1 lot -> 1/2) | runmax | +3.0 (3.5) | +2.5 (2.3) | +2.1 (2.2) | -0.4 (1.8) | +0.3 (1.4) |
| A6 only (1 lot -> 1/2) | base | -0.4 (2.8) | +0.0 (2.0) | +0.1 (1.8) | -0.0 (1.6) | -0.2 (1.6) |
| A6 only (1 lot -> 1/2) | sized | +3.2 (3.7) | +2.6 (2.3) | +2.1 (2.2) | -0.5 (1.8) | +0.3 (1.4) |
| M6 only (2 -> 1/3) | runmax | -0.2 (4.3) | -0.7 (2.5) | -0.7 (2.3) | +0.2 (1.7) | +0.7 (1.7) |
| M6 only (2 -> 1/3) | base | -1.3 (3.7) | -1.1 (2.4) | -1.2 (2.2) | -0.5 (1.8) | +1.0 (1.6) |
| M6 only (2 -> 1/3) | sized | -0.5 (4.5) | -0.9 (2.5) | -0.8 (2.4) | +0.1 (1.8) | +0.7 (1.7) |
| all eight books | runmax | +17.9 (37.6) | +14.2 (22.9) | +14.9 (21.4) | +9.2 (13.0) | +1.8 (11.9) |
| all eight books | base | +0.1 (30.5) | +1.6 (20.4) | +3.6 (18.7) | -3.0 (12.8) | +4.6 (12.6) |
| all eight books | sized | +18.9 (37.4) | +15.6 (22.5) | +15.3 (21.4) | +7.7 (14.3) | +1.9 (12.0) |

### 2f. The four LIVE books only (K6 P6 U6 H6; ST and WT unsized, in-stack)

| governor | real L3M | L6M | HOLD | PRE | X' | matched uniform L6M / HOLD / PRE / X' |
|---|---|---|---|---|---|---|
| runmax | +8.3 (29.8) | +7.1 (16.4) | +7.5 (15.2) | +3.2 (8.5) | +0.2 (8.2) | -0.4 / -0.2 / +0.2 / +0.5 |
| base | -3.3 (24.6) | +1.1 (13.9) | +2.4 (12.6) | -2.4 (8.5) | +1.3 (8.2) | -1.5 / -1.2 / -0.1 / -0.3 |
| sized | +9.9 (29.9) | +8.3 (16.1) | +8.6 (14.9) | +1.6 (9.7) | +0.2 (8.1) | -0.4 / -0.2 / +0.2 / +0.5 |

## 3. ER feature definition risk (what D6 must compute)

**The coded feature, exactly.** Kaufman efficiency ratio over 20 bars of 5-minute CLOSES: ER = |C[t] - C[t-20]| / sum_{i=t-19..t} |C[i] - C[i-1]|, 0 <= ER <= 1, t = the last CLOSED 5-minute bar at the signal second. 5-minute bars are clock-aligned buckets (300k, 300k+300] built from the library's 1-minute bars (bar timestamp = closing second, partial minutes excluded); the bar close = the close of its last 1-minute bar; bars with no print are absent (the 20-bar window skips them); a bar counts as closed when its closing second <= the signal second. Tie-out: this definition rebuilt from the 1-minute bars reproduces the stored trend-store `5m.er20` on all 44,370 universe rows to 1e-6. Threshold test: ER >= 0.30 (39.7% of engine signals).

**Which bar is 'current'.** The signal is a second inside a forming bar in 79.2% of cases (bar age 1..299 s); in 20.8% the signal fires at the exact second a 5-minute bar closes (age 0): the library treats the bar closing AT that second as the last closed bar. A live D6 that computes the ER from a bar builder will see that bar only once its closing second has been processed; the 'strict' variant below (the bar must close strictly before the signal second, so the previous bar is used when age is 0) is the conservative, implementable-without-look-ahead reading. 'Forming' variants use the forming bar's provisional close (1-s price at the signal, or the last closed 1-minute bar's close) as the 21st point, i.e. ER over the 20 most recent changes including the partial one.

### 3a. ER definition variants, in-stack, live+ integer lots, causal running-max (headline) ($k/wk, MDE)

| ER definition at the signal | share >= 0.30 | signals whose class (>=0.30) differs from coded | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|---|
| coded: last closed bar (t<=sig) | 0.397 | 0.000 | +15.3 (39.8) | +12.5 (23.5) | +13.7 (21.5) | +9.5 (11.8) | +0.8 (10.9) |
| strict: bar must close before the signal second (t<sig) | 0.385 | 0.036 | +14.1 (39.9) | +11.9 (23.1) | +13.2 (21.3) | +10.0 (12.4) | +1.4 (11.0) |
| offset -1 bar (stale by one bar) | 0.394 | 0.145 | +6.2 (34.3) | +4.2 (21.1) | +4.8 (18.9) | +3.1 (13.4) | -1.2 (11.0) |
| offset -2 bars | 0.399 | 0.196 | +4.8 (40.7) | +5.7 (23.7) | +7.6 (22.3) | +0.2 (12.6) | +0.3 (10.8) |
| offset +1 bar (LOOK-AHEAD: bar closing after the signal) | 0.443 | 0.163 | +25.4 (29.5) | +21.6 (19.7) | +20.7 (19.0) | +12.8 (12.9) | +4.1 (10.3) |
| forming bar: 20 closed + provisional close = 1-s price at signal | 0.446 | 0.135 | +11.9 (29.0) | +13.2 (20.4) | +13.4 (19.4) | +7.9 (13.6) | +1.7 (10.1) |
| forming bar: provisional close = last closed 1-min bar | 0.443 | 0.134 | +11.8 (28.9) | +13.2 (20.4) | +13.4 (19.4) | +8.0 (13.7) | +1.5 (10.1) |
| signal time -60s (stale) | 0.382 | 0.043 | +13.0 (40.1) | +12.0 (23.4) | +13.4 (21.6) | +9.9 (12.4) | +1.5 (11.1) |
| gap-filled 5m grid (flat bars for empty buckets) | 0.422 | 0.046 | +5.8 (34.4) | +11.4 (18.8) | +10.7 (17.2) | +7.9 (11.8) | +2.5 (10.5) |

### 3a. ER definition variants, in-stack, live+ integer lots, planned-lot (base) ($k/wk, MDE)

| ER definition at the signal | share >= 0.30 | signals whose class (>=0.30) differs from coded | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|---|
| coded: last closed bar (t<=sig) | 0.397 | 0.000 | +1.7 (31.1) | +2.7 (19.6) | +4.8 (17.7) | -2.4 (12.0) | +3.9 (11.4) |
| strict: bar must close before the signal second (t<sig) | 0.385 | 0.036 | +6.5 (31.5) | +5.0 (19.5) | +6.0 (17.3) | -1.1 (13.0) | +4.7 (11.5) |
| offset -1 bar (stale by one bar) | 0.394 | 0.145 | +2.5 (29.9) | +4.3 (17.1) | +4.2 (15.1) | -3.4 (12.9) | +1.3 (11.8) |
| offset -2 bars | 0.399 | 0.196 | +5.0 (26.8) | +2.0 (17.1) | +2.6 (16.0) | -2.7 (12.2) | +2.4 (11.8) |
| offset +1 bar (LOOK-AHEAD: bar closing after the signal) | 0.443 | 0.163 | +17.2 (27.0) | +11.8 (18.4) | +11.1 (17.1) | +3.5 (12.2) | +4.8 (9.0) |
| forming bar: 20 closed + provisional close = 1-s price at signal | 0.446 | 0.135 | -1.2 (28.3) | +1.5 (19.5) | +1.5 (18.0) | -1.6 (13.0) | +2.6 (10.4) |
| forming bar: provisional close = last closed 1-min bar | 0.443 | 0.134 | -1.2 (28.4) | +1.5 (19.5) | +1.5 (18.0) | -1.6 (13.0) | +2.7 (10.4) |
| signal time -60s (stale) | 0.382 | 0.043 | +5.2 (31.2) | +5.8 (19.8) | +7.0 (17.6) | -1.4 (13.2) | +4.8 (11.5) |
| gap-filled 5m grid (flat bars for empty buckets) | 0.422 | 0.046 | -7.7 (25.9) | -1.3 (15.7) | -0.7 (14.0) | +2.1 (10.7) | +6.1 (10.8) |


### 3b. Same, alone on the as-is stack, running-max

| ER definition at the signal | share >= 0.30 | signals whose class (>=0.30) differs from coded | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|---|
| coded: last closed bar (t<=sig) | 0.397 | 0.000 | +17.0 (30.9) | +15.3 (19.9) | +16.6 (18.0) | +0.6 (15.6) | +1.4 (16.1) |
| strict: bar must close before the signal second (t<sig) | 0.385 | 0.036 | +20.2 (35.2) | +16.8 (21.8) | +18.0 (19.9) | +1.2 (16.7) | +0.8 (15.5) |
| offset -1 bar (stale by one bar) | 0.394 | 0.145 | +12.0 (34.6) | +11.0 (21.3) | +10.8 (19.2) | -1.1 (17.4) | -0.2 (14.5) |
| offset -2 bars | 0.399 | 0.196 | +8.8 (37.5) | +9.8 (22.2) | +11.4 (21.5) | -6.3 (16.5) | +2.4 (14.4) |
| offset +1 bar (LOOK-AHEAD: bar closing after the signal) | 0.443 | 0.163 | +27.2 (37.4) | +27.7 (24.7) | +28.0 (23.4) | +11.4 (17.8) | +11.6 (15.8) |
| forming bar: 20 closed + provisional close = 1-s price at signal | 0.446 | 0.135 | +6.9 (32.6) | +10.6 (23.2) | +12.7 (22.0) | -0.2 (18.5) | +6.6 (16.1) |
| forming bar: provisional close = last closed 1-min bar | 0.443 | 0.134 | +6.8 (32.6) | +10.6 (23.2) | +12.7 (22.0) | -0.1 (18.5) | +6.0 (16.2) |
| signal time -60s (stale) | 0.382 | 0.043 | +18.3 (36.0) | +16.3 (22.4) | +17.4 (20.4) | +1.6 (16.9) | +0.7 (15.3) |
| gap-filled 5m grid (flat bars for empty buckets) | 0.422 | 0.046 | +9.8 (29.9) | +13.0 (20.5) | +9.7 (19.7) | +2.4 (14.3) | +2.8 (14.4) |


### 3c. Information coefficient of each variant (Spearman of ER vs the S73 N outcome in pts per planned lot, six engine books, week-block bootstrap t)

| variant | IC L6M (t) | HOLD | PRE | X' |
|---|---|---|---|---|
| coded: last closed bar (t<=sig) | +0.045 (3.0) | +0.042 (2.6) | +0.019 (2.1) | +0.020 (1.2) |
| strict: bar must close before the signal second (t<sig) | +0.043 (3.0) | +0.040 (2.6) | +0.020 (2.2) | +0.019 (1.2) |
| offset -1 bar (stale by one bar) | +0.030 (2.1) | +0.027 (1.9) | +0.018 (1.9) | +0.010 (0.7) |
| offset -2 bars | +0.028 (2.0) | +0.024 (1.7) | +0.018 (2.2) | +0.009 (0.6) |
| offset +1 bar (LOOK-AHEAD: bar closing after the signal) | +0.086 (4.7) | +0.083 (5.3) | +0.060 (5.5) | +0.056 (3.6) |
| forming bar: 20 closed + provisional close = 1-s price at signal | +0.042 (2.6) | +0.039 (2.6) | +0.017 (1.6) | +0.028 (1.9) |
| forming bar: provisional close = last closed 1-min bar | +0.042 (2.7) | +0.039 (2.5) | +0.017 (1.5) | +0.027 (1.9) |
| signal time -60s (stale) | +0.042 (3.0) | +0.038 (2.7) | +0.020 (2.3) | +0.020 (1.1) |
| gap-filled 5m grid (flat bars for empty buckets) | +0.043 (2.8) | +0.035 (2.1) | +0.022 (2.4) | +0.025 (1.9) |

Reading: a one-bar-stale ER (offset -1) cuts the IC by about a third in L6M (0.045 -> 0.030) and by half in X' (0.020 -> 0.010) and removes about two thirds of the stack gain; a 60-second-stale ER loses almost nothing (the ER of a 20-bar window moves slowly inside a bar, but a whole bar is a 5% change of the window). The forming-bar ER keeps the L6M gain and loses some PRE; the +1-bar variant is a look-ahead (it uses the bar that closes after the signal) and doubles the IC, which is the size of an accidental leak: any D6 implementation whose 'current bar' includes ticks after the signal second is inflated, not better. The gap-filled grid (flat bars for empty buckets) changes 4.6% of the classes and is NOT equivalent; D6 must skip empty buckets exactly as the library does or say otherwise.

## 4. Leave-one-book-out and leave-one-session-out (and only-one)

In-stack, live+ integer lots; 'sizer on X only' = the others unsized; 'leave out X' = X unsized, the other five sized. Sessions are entry sessions; 'close' has no live lot. Sums of the 'only' rows are approximately additive.

### 4a. causal running-max (headline)

| scenario | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| all six books, all sessions (coded) | +15.3 (39.8) | +12.5 (23.5) | +13.7 (21.5) | +9.5 (11.8) | +0.8 (10.9) |
| sizer on ST only | -0.3 (13.3) | +3.2 (9.9) | +3.8 (8.8) | +4.5 (5.1) | +0.2 (4.2) |
| sizer on H6 only | +0.9 (5.4) | -0.2 (3.5) | -0.2 (3.2) | +0.0 (2.5) | -0.4 (1.7) |
| sizer on WT only | +7.1 (5.4) | +3.1 (4.5) | +3.4 (4.5) | +1.7 (3.4) | +0.5 (2.4) |
| sizer on K6 only | +2.6 (6.5) | +2.1 (4.7) | +1.7 (4.2) | +0.1 (2.3) | +0.8 (2.0) |
| sizer on U6 only | -1.4 (5.0) | -0.8 (2.9) | -0.3 (2.6) | -0.0 (1.7) | +0.0 (1.7) |
| sizer on P6 only | +6.1 (22.9) | +6.0 (12.6) | +6.3 (11.8) | +3.2 (7.2) | -0.2 (6.6) |
| leave out ST | +15.0 (32.1) | +9.6 (18.3) | +10.2 (16.6) | +5.6 (9.7) | +0.6 (8.8) |
| leave out H6 | +14.2 (36.5) | +12.6 (21.7) | +13.8 (19.9) | +9.4 (10.9) | +1.3 (10.3) |
| leave out WT | +8.0 (37.1) | +10.4 (21.0) | +11.4 (19.5) | +7.4 (10.9) | +0.4 (10.3) |
| leave out K6 | +12.8 (36.8) | +10.5 (21.8) | +12.0 (20.2) | +9.4 (11.8) | -0.0 (10.3) |
| leave out U6 | +16.6 (37.8) | +13.3 (22.9) | +14.0 (21.1) | +9.5 (11.4) | +0.8 (10.4) |
| leave out P6 | +9.3 (25.0) | +7.1 (16.2) | +7.9 (14.6) | +6.2 (7.7) | +1.1 (7.1) |
| sizer in asia only | +17.1 (29.6) | +10.7 (16.3) | +11.6 (14.8) | +5.7 (8.8) | +0.6 (7.3) |
| sizer in london only | +2.0 (14.1) | +4.8 (9.3) | +4.9 (8.9) | +0.3 (7.8) | -0.1 (5.9) |
| sizer in pre only | +2.1 (9.6) | +1.2 (5.5) | +1.7 (4.8) | +0.5 (2.7) | -0.5 (2.5) |
| sizer in nyam only | +0.3 (17.3) | +2.6 (10.7) | +1.5 (10.0) | +5.9 (8.0) | -1.3 (8.6) |
| sizer in nypm only | -3.7 (5.0) | -2.5 (4.4) | -2.0 (4.2) | +0.2 (3.1) | +1.7 (3.1) |
| leave out asia | +3.9 (18.2) | +8.0 (14.0) | +7.3 (12.9) | +4.8 (9.4) | -1.9 (8.1) |
| leave out london | +13.3 (32.6) | +9.0 (18.7) | +10.1 (16.7) | +9.2 (10.9) | +2.2 (10.7) |
| leave out pre | +14.0 (39.7) | +12.2 (23.8) | +13.2 (21.9) | +9.6 (12.0) | +0.9 (11.1) |
| leave out nyam | +11.4 (35.8) | +10.2 (20.0) | +12.1 (19.0) | +5.5 (11.0) | +3.2 (9.7) |
| leave out nypm | +13.0 (39.0) | +11.3 (22.6) | +12.4 (21.1) | +8.4 (12.3) | +0.3 (10.2) |

### 4a. planned-lot (base)

| scenario | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| all six books, all sessions (coded) | +1.7 (31.1) | +2.7 (19.6) | +4.8 (17.7) | -2.4 (12.0) | +3.9 (11.4) |
| sizer on ST only | +0.1 (13.9) | -0.2 (10.1) | +0.6 (8.8) | -1.5 (5.1) | +2.2 (4.4) |
| sizer on H6 only | +0.5 (6.2) | -0.2 (3.9) | -0.1 (3.5) | +0.2 (1.9) | -0.3 (1.7) |
| sizer on WT only | +5.8 (9.0) | +2.3 (5.3) | +2.1 (4.9) | +1.7 (3.1) | +0.4 (2.7) |
| sizer on K6 only | -0.3 (7.1) | -0.7 (4.7) | -0.7 (4.1) | +0.4 (2.2) | +0.9 (2.0) |
| sizer on U6 only | -0.3 (4.5) | -0.2 (2.6) | -0.1 (2.4) | -0.5 (1.8) | +0.0 (1.7) |
| sizer on P6 only | -3.2 (18.5) | +2.2 (11.7) | +3.3 (10.7) | -2.5 (7.3) | +0.7 (6.5) |
| leave out ST | +2.1 (28.0) | +3.2 (15.5) | +4.4 (14.1) | -0.7 (9.8) | +1.7 (8.9) |
| leave out H6 | +1.3 (27.8) | +3.0 (17.9) | +4.9 (16.2) | -2.3 (11.5) | +4.2 (10.9) |
| leave out WT | -3.2 (28.5) | +0.9 (18.5) | +3.1 (16.7) | -4.1 (10.6) | +3.5 (10.5) |
| leave out K6 | +1.4 (31.0) | +3.2 (19.3) | +5.2 (17.6) | -2.9 (11.6) | +3.0 (10.9) |
| leave out U6 | +2.2 (29.3) | +3.0 (19.2) | +4.9 (17.4) | -1.9 (11.8) | +3.9 (10.7) |
| leave out P6 | +5.7 (20.9) | +0.9 (14.6) | +1.9 (12.9) | +0.1 (7.9) | +3.2 (7.5) |
| sizer in asia only | +4.3 (24.7) | +1.0 (13.5) | +2.5 (12.2) | -1.1 (9.6) | +3.4 (8.0) |
| sizer in london only | +0.5 (15.5) | +1.7 (10.0) | +2.6 (9.3) | -3.2 (6.9) | -0.7 (5.2) |
| sizer in pre only | +2.8 (7.2) | +2.2 (4.2) | +2.6 (3.8) | +0.6 (2.5) | +0.6 (2.5) |
| sizer in nyam only | +2.9 (10.3) | -0.3 (9.9) | -1.4 (9.0) | +1.5 (6.2) | +1.8 (7.2) |
| sizer in nypm only | +0.8 (4.5) | -0.6 (3.4) | -0.6 (3.1) | +0.0 (1.7) | +0.5 (2.2) |
| leave out asia | -4.1 (19.1) | -2.5 (14.1) | -1.7 (12.5) | -1.2 (9.0) | +2.0 (8.6) |
| leave out london | +6.5 (26.6) | +2.9 (15.9) | +3.9 (14.0) | +2.1 (11.1) | +3.4 (10.5) |
| leave out pre | +0.3 (30.7) | +2.4 (19.6) | +3.9 (17.6) | -3.1 (11.8) | +4.0 (11.8) |
| leave out nyam | -1.4 (30.7) | +0.6 (18.1) | +3.4 (17.1) | -3.2 (11.1) | +3.3 (9.9) |
| leave out nypm | +0.9 (30.3) | +2.6 (19.1) | +4.6 (17.4) | -2.6 (11.7) | +3.0 (10.8) |


### 4b. Research lots (fractional, running-max)

| scenario | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| all six, all sessions (coded) | +11.6 (89.5) | +22.1 (54.1) | +22.5 (48.3) | +9.8 (24.7) | +3.9 (22.0) |
| sizer on ST only | +0.7 (32.3) | +8.3 (23.4) | +9.7 (21.0) | +10.7 (11.9) | +0.6 (9.8) |
| sizer on H6 only | -10.0 (35.2) | -1.8 (20.4) | -1.9 (18.3) | -5.0 (11.3) | +2.2 (10.8) |
| sizer on WT only | +15.0 (11.8) | +6.6 (10.2) | +7.1 (10.2) | +2.5 (7.0) | +0.8 (5.7) |
| sizer on K6 only | +5.6 (19.1) | +6.2 (12.3) | +4.8 (11.0) | +1.2 (7.0) | +1.5 (5.5) |
| sizer on U6 only | -4.6 (15.3) | -0.8 (9.2) | -0.6 (8.5) | -0.3 (3.7) | -2.1 (4.7) |
| sizer on P6 only | +4.2 (21.6) | +5.4 (11.6) | +5.4 (10.7) | +1.0 (6.4) | +1.0 (5.7) |
| leave out ST | +10.4 (70.4) | +15.0 (40.9) | +14.0 (36.2) | +0.5 (18.6) | +3.4 (16.1) |
| leave out H6 | +21.8 (64.9) | +24.0 (40.7) | +24.5 (36.8) | +14.0 (18.3) | +1.7 (18.9) |
| leave out WT | -3.6 (87.0) | +17.6 (51.0) | +17.6 (45.4) | +6.8 (23.9) | +3.2 (20.6) |
| leave out K6 | +6.1 (78.4) | +16.0 (48.8) | +17.7 (43.7) | +8.3 (23.0) | +2.4 (20.4) |
| leave out U6 | +16.1 (84.4) | +22.9 (50.8) | +23.1 (45.7) | +10.0 (24.5) | +6.0 (20.0) |
| leave out P6 | +7.1 (74.7) | +17.3 (47.4) | +17.9 (42.0) | +9.7 (22.1) | +3.0 (20.1) |
| sizer in asia only | +10.1 (68.4) | +10.4 (37.7) | +10.8 (33.3) | +12.7 (19.9) | -0.2 (14.3) |
| sizer in london only | -8.1 (31.9) | +10.1 (21.6) | +8.7 (19.1) | +0.7 (16.1) | +1.5 (12.6) |
| sizer in pre only | +3.7 (23.1) | +5.3 (14.2) | +5.7 (13.0) | -0.9 (9.2) | -1.5 (7.6) |
| sizer in nyam only | -2.4 (36.7) | +0.9 (23.2) | -2.1 (21.5) | +5.2 (16.7) | -0.5 (15.9) |
| sizer in nypm only | -18.1 (14.4) | -7.6 (14.9) | -6.1 (14.0) | -0.1 (9.7) | +4.3 (9.6) |
| leave out asia | -3.9 (43.9) | +14.7 (36.0) | +11.4 (31.7) | +4.3 (21.8) | +1.3 (18.0) |
| leave out london | +5.8 (79.5) | +9.3 (44.9) | +10.5 (39.5) | +14.8 (24.3) | +5.0 (21.4) |
| leave out pre | +9.6 (88.9) | +20.4 (55.2) | +20.0 (49.2) | +10.7 (25.0) | +4.1 (23.7) |
| leave out nyam | -5.4 (82.8) | +14.7 (48.2) | +16.7 (44.0) | +4.2 (23.7) | +5.2 (21.3) |
| leave out nypm | -4.1 (81.5) | +14.1 (49.4) | +14.2 (44.5) | +8.2 (25.5) | -1.0 (19.2) |

## 5. Stability: quarters, halves, top-5 weeks

Quarterly figure = mean $k/wk of the delta within the calendar quarter (2023Q2..2026Q1; 2026Q1 ends 2026-02-06); sign count over quarters with at least 4 weeks. Halves = first/second 14 weeks of L6M (28 ISO weeks). Top-5 share = the five best weeks of L6M divided by the L6M total (above 100% means the other 23 weeks together are negative).

| scenario | quarters positive (of N, >=4 weeks each) | L6M first half $k/wk (MDE) | L6M second half (MDE) | L6M total $k (28 wk) | top-5 weeks $k | top-5 share of L6M gain | L6M mean without the top 5 weeks $k/wk | share of L6M weeks positive |
|---|---|---|---|---|---|---|---|---|
| ALL six, running-max, in-stack | 10 / 12 | +9.2 (27.2) | +15.8 (39.2) | +351 | +375 | 107% | -1.1 | 61% |
| ALL six, static, in-stack | 10 / 12 | +11.1 (26.2) | +17.0 (38.5) | +393 | +373 | 95% | +0.9 | 61% |
| ALL six, planned-lot, in-stack | 6 / 12 | +2.4 (26.3) | +3.0 (30.0) | +76 | +269 | 353% | -8.4 | 54% |
| ALL six, running-max, alone | 9 / 12 | +15.0 (23.9) | +15.5 (32.7) | +428 | +343 | 80% | +3.7 | 64% |
| ST only, running-max | 8 / 12 | +6.4 (15.0) | +0.0 (12.9) | +90 | +143 | 159% | -2.3 | 61% |
| H6 only, running-max | 7 / 12 | -0.8 (4.0) | +0.4 (5.9) | -6 | +49 | -851% | -2.4 | 43% |
| WT only, running-max | 10 / 12 | -0.5 (6.0) | +6.7 (5.7) | +87 | +72 | 82% | +0.7 | 64% |
| K6 only, running-max | 9 / 12 | +0.8 (7.2) | +3.4 (6.2) | +59 | +74 | 126% | -0.7 | 64% |
| U6 only, running-max | 8 / 12 | -0.5 (3.1) | -1.0 (5.0) | -21 | +37 | -175% | -2.5 | 36% |
| P6 only, running-max | 10 / 12 | +6.0 (11.7) | +6.1 (22.9) | +168 | +191 | 114% | -1.0 | 61% |


### 5b. Quarterly delta $k/wk

| quarter | ALL six, running-max, in-stack | ALL six, static, in-stack | ALL six, planned-lot, in-stack | ALL six, running-max, alone |
|---|---|---|---|---|
| 2023Q2 | +0.9 | +0.6 | +6.3 | -5.8 |
| 2023Q3 | +6.1 | +6.4 | +7.1 | +13.1 |
| 2023Q4 | -9.1 | -8.9 | -10.0 | -9.5 |
| 2024Q1 | +11.5 | +12.1 | +12.2 | +3.5 |
| 2024Q2 | +7.4 | +8.6 | -7.9 | +8.8 |
| 2024Q3 | +20.2 | +18.0 | +3.0 | +11.2 |
| 2024Q4 | -0.8 | +1.2 | -2.2 | +0.2 |
| 2025Q1 | +3.3 | -0.4 | -5.0 | -14.9 |
| 2025Q2 | +15.2 | +10.2 | -3.6 | +1.9 |
| 2025Q3 | +20.5 | +20.0 | +14.2 | +24.7 |
| 2025Q4 | +0.9 | +2.3 | -6.4 | +1.2 |
| 2026Q1 | +23.0 | +23.7 | +7.4 | +28.3 |


### 5c. Per-book quarterly delta (running-max, sizer on one book)

| quarter | ST | H6 | WT | K6 | U6 | P6 |
|---|---|---|---|---|---|---|
| 2023Q2 | -0.1 | -1.0 | +0.5 | +0.7 | -0.6 | +1.7 |
| 2023Q3 | +0.5 | +1.3 | -0.5 | +0.0 | +0.7 | +4.0 |
| 2023Q4 | -0.5 | -1.8 | +0.7 | +1.1 | -1.4 | -7.3 |
| 2024Q1 | +0.0 | +0.5 | +3.7 | +1.4 | +1.1 | +4.8 |
| 2024Q2 | +4.4 | -2.2 | +2.2 | -1.2 | +0.4 | +3.8 |
| 2024Q3 | +9.0 | +2.7 | +4.3 | +2.1 | +0.3 | +0.3 |
| 2024Q4 | -1.4 | +0.1 | -0.4 | -1.2 | -1.3 | +3.5 |
| 2025Q1 | +2.1 | +1.4 | +0.1 | -2.5 | +0.6 | +3.7 |
| 2025Q2 | +11.2 | -2.5 | +0.8 | +2.8 | +0.2 | +2.1 |
| 2025Q3 | +11.9 | +0.1 | +2.4 | +0.2 | +0.3 | +6.0 |
| 2025Q4 | -7.8 | -1.6 | +1.0 | +2.9 | -1.5 | +9.6 |
| 2026Q1 | +10.9 | +2.5 | +10.0 | +1.7 | +1.1 | -2.6 |


## 6. The integer-lot issue

Lots under the coded x0.5 / x1.5 with round half up and minimum 1, per live (book, session). '=' marks a side that rounds back to the planned lot; NO-OP = both sides do. Share ER >= 0.30 is over L6M signals.

| book / session | planned lot | share ER>=0.30 (L6M signals) | 0.5 / 1.5  (lots below -> at/above) | 0.7 / 1.3  (lots below -> at/above) | 0.75 / 1.25  (lots below -> at/above) | 0 / 1.5  (lots below -> at/above) | 0.5 / 1  (lots below -> at/above) | 1 / 1.5  (lots below -> at/above) |
|---|---|---|---|---|---|---|---|---|
| K6 asia | 2 | 0.39 | 1 -> 3 | 1 -> 3 | =2 -> 3 | skip -> 3 | 1 -> =2 | =2 -> 3 |
| K6 london | 2 | 0.38 | 1 -> 3 | 1 -> 3 | =2 -> 3 | skip -> 3 | 1 -> =2 | =2 -> 3 |
| K6 nyam | 2 | 0.32 | 1 -> 3 | 1 -> 3 | =2 -> 3 | skip -> 3 | 1 -> =2 | =2 -> 3 |
| K6 nypm | 2 | 0.33 | 1 -> 3 | 1 -> 3 | =2 -> 3 | skip -> 3 | 1 -> =2 | =2 -> 3 |
| P6 asia | 7 | 0.45 | 4 -> 11 | 5 -> 9 | 5 -> 9 | skip -> 11 | 4 -> =7 | =7 -> 11 |
| P6 london | 7 | 0.48 | 4 -> 11 | 5 -> 9 | 5 -> 9 | skip -> 11 | 4 -> =7 | =7 -> 11 |
| P6 nyam | 7 | 0.34 | 4 -> 11 | 5 -> 9 | 5 -> 9 | skip -> 11 | 4 -> =7 | =7 -> 11 |
| U6 asia | 4 | 0.60 | 2 -> 6 | 3 -> 5 | 3 -> 5 | skip -> 6 | 2 -> =4 | =4 -> 6 |
| U6 london | 4 | 0.46 | 2 -> 6 | 3 -> 5 | 3 -> 5 | skip -> 6 | 2 -> =4 | =4 -> 6 |
| H6 asia | 4 | 0.36 | 2 -> 6 | 3 -> 5 | 3 -> 5 | skip -> 6 | 2 -> =4 | =4 -> 6 |
| H6 nyam | 2 | 0.39 | 1 -> 3 | 1 -> 3 | =2 -> 3 | skip -> 3 | 1 -> =2 | =2 -> 3 |
| M6 london | 2 | 0.50 | 1 -> 3 | 1 -> 3 | =2 -> 3 | skip -> 3 | 1 -> =2 | =2 -> 3 |
| M6 nyam | 2 | 0.33 | 1 -> 3 | 1 -> 3 | =2 -> 3 | skip -> 3 | 1 -> =2 | =2 -> 3 |
| A6 asia | 1 | 0.41 | =1 -> 2 | =1 -> =1 **NO-OP** | =1 -> =1 **NO-OP** | skip -> 2 | =1 -> =1 **NO-OP** | =1 -> 2 |
| A6 london | 1 | 0.51 | =1 -> 2 | =1 -> =1 **NO-OP** | =1 -> =1 **NO-OP** | skip -> 2 | =1 -> =1 **NO-OP** | =1 -> 2 |
| A6 pre | 1 | 0.56 | =1 -> 2 | =1 -> =1 **NO-OP** | =1 -> =1 **NO-OP** | skip -> 2 | =1 -> =1 **NO-OP** | =1 -> 2 |
| A6 nyam | 1 | 0.37 | =1 -> 2 | =1 -> =1 **NO-OP** | =1 -> =1 **NO-OP** | skip -> 2 | =1 -> =1 **NO-OP** | =1 -> 2 |
| A6 nypm | 1 | 0.44 | =1 -> 2 | =1 -> =1 **NO-OP** | =1 -> =1 **NO-OP** | skip -> 2 | =1 -> =1 **NO-OP** | =1 -> 2 |
| A6 close | 1 | 0.00 | =1 -> 2 | =1 -> =1 **NO-OP** | =1 -> =1 **NO-OP** | skip -> 2 | =1 -> =1 **NO-OP** | =1 -> 2 |


Summary over sessions per book and pair (L6M signal-weighted):

| book | pair lo/hi | sessions with a live lot | sessions where the sizer is a NO-OP (both sides round to the planned lot) | sessions where the LOW side is unchanged | sessions where the HIGH side is unchanged | share of L6M signals whose lots change | average lot factor |
|---|---|---|---|---|---|---|---|
| K6 | 0.5/1.5 | 4 | 0 | 0 | 0 | 1.00 | 0.852 |
| K6 | 0.7/1.3 | 4 | 0 | 0 | 0 | 1.00 | 0.852 |
| K6 | 0.75/1.25 | 4 | 0 | 4 | 0 | 0.35 | 1.176 |
| K6 | 0/1.5 | 4 | 0 | 0 | 0 | 1.00 | 0.528 |
| K6 | 0.5/1 | 4 | 0 | 0 | 4 | 0.65 | 0.676 |
| K6 | 1/1.5 | 4 | 0 | 4 | 0 | 0.35 | 1.176 |
| P6 | 0.5/1.5 | 3 | 0 | 0 | 0 | 1.00 | 0.986 |
| P6 | 0.7/1.3 | 3 | 0 | 0 | 0 | 1.00 | 0.951 |
| P6 | 0.75/1.25 | 3 | 0 | 0 | 0 | 1.00 | 0.951 |
| P6 | 0/1.5 | 3 | 0 | 0 | 0 | 1.00 | 0.651 |
| P6 | 0.5/1 | 3 | 0 | 0 | 3 | 0.59 | 0.749 |
| P6 | 1/1.5 | 3 | 0 | 3 | 0 | 0.41 | 1.237 |
| U6 | 0.5/1.5 | 2 | 0 | 0 | 0 | 1.00 | 1.039 |
| U6 | 0.7/1.3 | 2 | 0 | 0 | 0 | 1.00 | 1.019 |
| U6 | 0.75/1.25 | 2 | 0 | 0 | 0 | 1.00 | 1.019 |
| U6 | 0/1.5 | 2 | 0 | 0 | 0 | 1.00 | 0.808 |
| U6 | 0.5/1 | 2 | 0 | 0 | 2 | 0.46 | 0.769 |
| U6 | 1/1.5 | 2 | 0 | 2 | 0 | 0.54 | 1.269 |
| H6 | 0.5/1.5 | 2 | 0 | 0 | 0 | 1.00 | 0.873 |
| H6 | 0.7/1.3 | 2 | 0 | 0 | 0 | 1.00 | 0.912 |
| H6 | 0.75/1.25 | 2 | 0 | 1 | 0 | 0.72 | 1.052 |
| H6 | 0/1.5 | 2 | 0 | 0 | 0 | 1.00 | 0.560 |
| H6 | 0.5/1 | 2 | 0 | 0 | 2 | 0.63 | 0.687 |
| H6 | 1/1.5 | 2 | 0 | 2 | 0 | 0.37 | 1.187 |
| M6 | 0.5/1.5 | 2 | 0 | 0 | 0 | 1.00 | 0.901 |
| M6 | 0.7/1.3 | 2 | 0 | 0 | 0 | 1.00 | 0.901 |
| M6 | 0.75/1.25 | 2 | 0 | 2 | 0 | 0.40 | 1.200 |
| M6 | 0/1.5 | 2 | 0 | 0 | 0 | 1.00 | 0.601 |
| M6 | 0.5/1 | 2 | 0 | 0 | 2 | 0.60 | 0.700 |
| M6 | 1/1.5 | 2 | 0 | 2 | 0 | 0.40 | 1.200 |
| A6 | 0.5/1.5 | 6 | 0 | 6 | 0 | 0.43 | 1.433 |
| A6 | 0.7/1.3 | 6 | 6 | 6 | 6 | 0.00 | 1.000 |
| A6 | 0.75/1.25 | 6 | 6 | 6 | 6 | 0.00 | 1.000 |
| A6 | 0/1.5 | 6 | 0 | 0 | 0 | 1.00 | 0.866 |
| A6 | 0.5/1 | 6 | 6 | 6 | 6 | 0.00 | 1.000 |
| A6 | 1/1.5 | 6 | 0 | 6 | 0 | 0.43 | 1.433 |


**Reading.** The premise 'the sizer is a no-op for small-lot books' is false at the coded pair with round-half-up: K6 2 and H6 NY-AM 2 become 1 or 3 (a 3x swing, the largest relative change of any book), A6 1 becomes 2 on 43% of signals. The sizer is a NO-OP only for A6 at 0.7/1.3, 0.75/1.25 and 0.5/1.0 (1 lot cannot move) and one-sided no-op for the low side of A6 at every pair with lo >= 0.5. Rounding also changes the average lot: P6 7 -> 4/11 is a mean factor 0.99 (planned 1.0), K6 2 -> 1/3 is 0.85, H6 NY-AM 0.87, U6 1.04. The fractional multipliers 0.5/1.5 on the 39%/61% mix would average 0.89.

### 6b. Rounding rule (the SS-2 open question), in-stack, coded cell, running-max / planned-lot / static ($k/wk, MDE)

| rule | governor | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| round half up, min 1 (user-style) | runmax | +15.3 (39.8) | +12.5 (23.5) | +13.7 (21.5) | +9.5 (11.8) | +0.8 (10.9) |
| round half up, min 1 (user-style) | base | +1.7 (31.1) | +2.7 (19.6) | +4.8 (17.7) | -2.4 (12.0) | +3.9 (11.4) |
| round half up, min 1 (user-style) | sized | +16.4 (39.1) | +14.1 (22.9) | +14.2 (21.3) | +8.1 (12.9) | +1.0 (11.0) |
| round half to even, min 1 | runmax | +13.2 (37.6) | +10.5 (22.3) | +11.7 (20.4) | +8.0 (10.9) | +0.6 (10.3) |
| round half to even, min 1 | base | +1.5 (30.4) | +1.5 (19.6) | +3.4 (17.6) | -1.5 (11.4) | +4.2 (11.1) |
| round half to even, min 1 | sized | +14.2 (37.0) | +12.0 (21.9) | +12.2 (20.2) | +6.7 (12.0) | +0.7 (10.4) |
| floor, min 1 | runmax | +10.2 (40.8) | +9.2 (24.0) | +10.1 (21.8) | +6.6 (12.3) | +0.1 (11.0) |
| floor, min 1 | base | +3.3 (33.0) | +1.6 (21.1) | +3.7 (18.9) | -0.7 (12.2) | +3.9 (12.0) |
| floor, min 1 | sized | +11.2 (40.5) | +10.6 (23.6) | +10.8 (21.6) | +6.3 (13.1) | +0.3 (11.1) |
| ceil | runmax | +15.3 (39.8) | +12.5 (23.5) | +13.7 (21.5) | +9.5 (11.8) | +0.8 (10.9) |
| ceil | base | +1.7 (31.1) | +2.7 (19.6) | +4.8 (17.7) | -2.4 (12.0) | +3.9 (11.4) |
| ceil | sized | +16.4 (39.1) | +14.1 (22.9) | +14.2 (21.3) | +8.1 (12.9) | +1.0 (11.0) |
| no rounding (fractional lots) | runmax | +11.0 (40.9) | +9.7 (24.0) | +11.0 (21.9) | +7.3 (12.3) | +0.4 (11.0) |
| no rounding (fractional lots) | base | +1.2 (29.8) | +2.4 (19.6) | +4.3 (17.7) | -2.5 (11.5) | +4.4 (11.5) |
| no rounding (fractional lots) | sized | +12.1 (40.5) | +11.2 (23.6) | +11.5 (21.7) | +7.0 (13.2) | +0.6 (11.0) |

Half-up and ceil are identical at these lots (the only half cases are 3.5 -> 4 and 10.5 -> 11, both rounded up by either rule); half-to-even rounds 10.5 down to 10 and loses about 2k L6M; floor rounds the 0.5 side DOWN to 3 (P6) and the 1.5 side down, losing more.

### 6c. Units: per planned lot and per contract of final position, taken trades, L6M (before the lock-engine feedback)

pts/planned lot = mean outcome of a taken trade; per contract = lot-weighted (sum lots x pts / sum lots) at the planned (unsized) lots and at the sized integer lots; 'lot factor' = sized lots / planned lots. A6 and M6 are unsized in the headline (rows equal).

| book | n taken | pts/planned lot ER>=0.30 | ER<0.30 | pts per contract unsized | pts per contract sized | lot factor |
|---|---|---|---|---|---|---|
| ST | 854 | +10.66 | +3.18 | +6.37 | +8.34 | 0.926 |
| HM | 386 | +15.07 | +9.18 | +12.00 | +13.62 | 0.893 |
| WT | 1211 | +5.16 | +2.21 | +3.21 | +4.00 | 0.840 |
| KB | 819 | +10.28 | -0.32 | +3.81 | +6.64 | 0.889 |
| SM | 124 | +0.73 | +8.20 | +4.10 | +2.34 | 1.048 |
| PE | 582 | +9.67 | +3.81 | +6.56 | +7.96 | 1.041 |
| MV | 394 | -0.87 | +8.95 | +4.51 | +4.51 | 1.000 |
| PB | 630 | +8.19 | +7.00 | +7.55 | +7.55 | 1.000 |


By session:

| book | session | n taken (L6M) | share ER>=0.30 | pts/planned lot ER>=0.30 | ER<0.30 | all | pts per contract unsized | pts per contract sized (lot-weighted) | lot factor sized/planned |
|---|---|---|---|---|---|---|---|---|---|
| ST | asia | 251 | 0.39 | +12.54 | -2.04 | +3.71 | +3.71 | +7.61 | 0.894 |
| ST | london | 165 | 0.50 | +10.30 | +7.15 | +8.73 | +8.73 | +9.52 | 1.003 |
| ST | pre | 50 | 0.50 | +2.86 | -9.24 | -3.19 | -3.19 | -0.16 | 1.000 |
| ST | nyam | 276 | 0.39 | +12.42 | +7.37 | +9.33 | +9.33 | +10.68 | 0.888 |
| ST | nypm | 112 | 0.45 | +7.64 | +4.33 | +5.81 | +5.81 | +6.67 | 0.946 |
| HM | asia | 196 | 0.38 | +16.94 | +10.44 | +12.89 | +12.89 | +14.63 | 0.878 |
| HM | nyam | 190 | 0.43 | +13.37 | +7.78 | +10.16 | +10.16 | +11.64 | 0.926 |
| WT | asia | 364 | 0.41 | +7.45 | +6.33 | +6.78 | +6.78 | +7.08 | 0.907 |
| WT | london | 291 | 0.36 | +2.91 | -2.70 | -0.66 | -0.66 | +0.84 | 0.864 |
| WT | pre | 67 | 0.27 | +2.40 | +2.42 | +2.42 | +2.42 | +2.41 | 0.769 |
| WT | nyam | 309 | 0.28 | +7.27 | +5.10 | +5.72 | +5.72 | +6.28 | 0.785 |
| WT | nypm | 180 | 0.29 | +0.63 | -2.73 | -1.76 | -1.76 | -0.89 | 0.789 |
| KB | asia | 247 | 0.43 | +11.12 | +1.51 | +5.63 | +5.63 | +8.17 | 0.929 |
| KB | london | 157 | 0.40 | +20.65 | +4.20 | +10.80 | +10.80 | +15.19 | 0.901 |
| KB | nyam | 271 | 0.36 | +7.03 | -6.35 | -1.51 | -1.51 | +2.08 | 0.862 |
| KB | nypm | 144 | 0.36 | +2.12 | +3.57 | +3.04 | +3.04 | +2.66 | 0.861 |
| SM | asia | 65 | 0.60 | +9.32 | -0.28 | +5.48 | +5.48 | +7.58 | 1.100 |
| SM | london | 59 | 0.49 | -10.84 | +15.56 | +2.59 | +2.59 | -4.07 | 0.992 |
| PE | asia | 275 | 0.47 | +11.43 | +0.28 | +5.55 | +5.55 | +8.21 | 1.044 |
| PE | london | 168 | 0.53 | +3.17 | +10.74 | +6.73 | +6.73 | +5.01 | 1.101 |
| PE | nyam | 139 | 0.39 | +16.17 | +3.40 | +8.36 | +8.36 | +11.52 | 0.960 |
| MV | london | 189 | 0.52 | -1.29 | +8.50 | +3.42 | +3.42 | +3.42 | 1.000 |
| MV | nyam | 205 | 0.39 | -0.36 | +9.27 | +5.51 | +5.51 | +5.51 | 1.000 |
| PB | asia | 221 | 0.43 | +16.28 | +8.47 | +11.86 | +11.86 | +11.86 | 1.000 |
| PB | london | 164 | 0.52 | +7.71 | +12.75 | +10.14 | +10.14 | +10.14 | 1.000 |
| PB | pre | 34 | 0.59 | -24.40 | +17.19 | -7.27 | -7.27 | -7.27 | 1.000 |
| PB | nyam | 137 | 0.40 | +4.29 | +1.39 | +2.55 | +2.55 | +2.55 | 1.000 |
| PB | nypm | 74 | 0.46 | +12.01 | -0.98 | +4.99 | +4.99 | +4.99 | 1.000 |


## 7. Bookkeeping and caveats

* Runs: 532 grid + 192 + 144 decomposition + 56 uniform + 72 ER-definition + 39 rounding/extra + 120 per-book surface + 12 pair-matched + 24 final + placebo draws (200 per scope; 15 stack scopes per draw). UF_TRIALS side=followup_ersizer (about 850 distinct configurations, n_eff about 10: the cells are strongly correlated neighbours); nothing was selected, no recent look was spent beyond the windows above (all five windows are reported for every cell).
* The lock engine is SS-2's (tie-out: the fractional coded run at live+ reproduces SS-2's `s1_live+_N.pkl` FULL|runmax|1.28 to the dollar, 65,491.8 L6M). The integer-split base (0.25-pt add slippage, A6 market) is SS-2's `int_split` convention.
* MDE = 2.8 x SE of the paired weekly delta (week-level, L6M 28 weeks); placebo p = (1 + #draws >= real)/(1 + draws).
* The sizer here is applied to the six SS books; applying it to M6/A6 as well (2e) changes the whole-stack delta by about +1k.
* ST and WT are not live (research/2.35); K6 P6 U6 H6 alone = section 2f.
* Governor readings other than running-max are shown for the record; the opener-fixed reading is negative (the sizer's multiplier is not stable inside a day).
* No cell is proposed. Anything labelled post-hoc is an observation about 30 correlated cells.
* Pickles: `out/ersizer/{grid,decomp,research_decomp,unif,erdef,rounding,bookgrid,pairunif,final,plc}_w*.pkl` (key -> daily $ by book, 8 x 745 days); tables `surface.csv`, `neighbours.csv`, `int_lot_table.csv`, `rows_table.csv`, `ic_variants.csv`. Reproduce: `python3 -I run_jobs.py <jobset> <k> <n>` then `write_report.py`.
