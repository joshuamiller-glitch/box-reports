# DS3_D7_FILTERS - D7 group-12 recent filters, scored as D7 has them (agent D7F, 2026-10-31)

Research only. No live/execution/chart change. UNTOUCHED never read (every frame capped at label day 20260206; ES tape 2023-04..2026-01 only). Prereg `l2vast/ds3/prereg/D7F_prereg.md` sha256 82b2737ef6c2ddb24cb18ccdb9905b5db6612b58f5ef3fd45c1209ad8ce59a73 (DECISIONS.md, before the scored run; one smoke run disclosed in it). Engine `l2vast/ds3/code/sundaystack2/ss2_lib.py` (D6 running-max locks) driven by `l2vast/ds3/code/d7filters/` (outputs `l2vast/ds3/out/d7filters/`). Windows: L3M 20251106-, L6M 20250801-, HOLD 20250701-, PRE 20240201-20250630, X' 20230401-20240131 (own masks, capped 20260206). MDE = 2.8 x SE of the paired weekly delta. Stack = lock engine at LIVE lots with the Sunday composite underneath (70/30@3 integer split with +0.25/lot add slip, PE confirm, ER(20) x1.5/x0.5 at 0.30 rounded half-up min 1, Asia-stopped cut, 8-line zone skip, Native stop 1.28, running-max locks); delta = composite + rule minus composite.

## PAGE 1

**Verdict: 0 of 19 rule-by-book lines are ON. All four D7 group-12 rules ship OFF.** No rule has a stack gain above its MDE in L6M or in HOLD for any book, and the stack total of each rule is <= 0 in L6M (a -6.8, b -0.1, c -0.7, d -6.2 $k/wk; MDE 14.6 / 2.6 / 1.2 / 12.2). The two rules with a positive trade-level rate in L6M ((a) first-60 skip: +2.01 pts per planned lot, rank 0.98 vs random skips; (b) post-loser skip: +0.21) lose it on the stack because the signals they remove are profitable in dollars (the volume lost exceeds the rate gained) and because the first 60 minutes flip sign in PRE (-1.39). The composite itself is unchanged by D7 with every rule Off: 45.4 $k/wk L6M (as-is stack 23.0; composite delta +22.4, MDE 17.9).

One line per rule per book. State = D7F rule: OFF when in BOTH L6M and HOLD the book's stack delta is <= 0 or inside its MDE (D7 ships it Off); else ON with the default shown. Stack columns: delta $k/wk at live lots vs the composite (MDE in brackets for L6M/HOLD), A6 from the stand-alone PB7 book (2 decimals). Rate = risk-matched pts per planned lot, L6M (MDE); per contract = change in pts per contract of the final live lots, L6M. Placebo rank = share of >= 200 random draws (same count per book x session x half-year; (d) = shuffled ES multiplier) that the real cell beats on the stack (L6M / HOLD); 1.00 = better than every draw, which for a skip rule only says the removed signals are worse than average, not that skipping pays. Touched = signals per week removed (a b c) or resized (d), L6M.

| rule | book | state | stack L6M (MDE) | stack HOLD (MDE) | PRE | X' | L3M | rate L6M /planned lot (MDE) | per contract d L6M | placebo rank L6M / HOLD | touched /wk |
|---|---|---|---|---|---|---|---|---|---|---|---|
| (a) skip first 60 min of each session | K6 | **OFF** (watch: + in L6M and HOLD, inside MDE) | +0.5 (4.5) | +0.9 (4.4) | -2.5 | +0.5 | +0.9 | +3.10 (3.62) | +4.15 | 0.96 / 0.96 | 11.9 |
| (a) skip first 60 min of each session | P6 | **OFF** | -4.8 (10.8) | -4.4 (11.8) | -4.5 | -0.7 | -4.4 | +1.20 (3.95) | +1.20 | 0.94 / 0.94 | 6.5 |
| (a) skip first 60 min of each session | U6 | **OFF** (watch: + in L6M and HOLD, inside MDE) | +0.0 (2.6) | +0.5 (2.5) | -0.5 | -0.7 | +0.7 | -1.07 (5.95) | +0.06 | 0.53 / 0.80 | 0.7 |
| (a) skip first 60 min of each session | H6 | **OFF** | -2.4 (4.4) | -2.3 (4.2) | -1.2 | +1.3 | -1.8 | +1.76 (6.03) | +3.47 | 0.91 / 0.85 | 5.9 |
| (a) skip first 60 min of each session | M6 | **OFF** | -0.2 (2.3) | +0.0 (2.4) | -1.4 | +0.5 | +1.0 | -0.82 (5.93) | -0.28 | 0.59 / 0.69 | 6.0 |
| (a) skip first 60 min of each session | A6 | **OFF** | -0.35 (1.2) | -0.26 (1.0) | -0.17 | -0.07 | -0.50 | -3.83 (4.52) | -2.64 | 0.49 / 0.49 | 0.9 |
| (b) skip next signal <=30 min after own loser | K6 | **OFF** (watch: + in L6M and HOLD, inside MDE) | +0.1 (2.0) | +0.3 (1.8) | -0.5 | -0.2 | -0.2 | +0.53 (1.41) | +0.41 | 0.64 / 0.82 | 1.7 |
| (b) skip next signal <=30 min after own loser | P6 | **OFF** (watch: + in L6M and HOLD, inside MDE) | +0.4 (1.9) | +0.3 (1.6) | -0.6 | -0.5 | -0.1 | +0.43 (0.76) | +0.28 | 0.80 / 0.79 | 0.4 |
| (b) skip next signal <=30 min after own loser | U6 | **OFF** | +0.0 (0.0) | +0.0 (0.0) | +0.0 | +0.0 | +0.0 | +0.00 (0.00) | +0.00 | 0.31 / 0.32 | 0.0 |
| (b) skip next signal <=30 min after own loser | H6 | **OFF** (watch: + in L6M and HOLD, inside MDE) | +0.1 (0.7) | +0.1 (0.6) | -0.2 | -0.0 | +0.2 | +0.19 (1.63) | +0.33 | 0.82 / 0.77 | 0.3 |
| (b) skip next signal <=30 min after own loser | M6 | **OFF** | -0.6 (0.9) | -0.6 (0.8) | +0.0 | -0.2 | -1.0 | -0.70 (2.33) | -0.87 | 0.10 / 0.10 | 0.9 |
| (b) skip next signal <=30 min after own loser | A6 | **OFF** | +0.00 (0.0) | +0.00 (0.0) | +0.00 | +0.00 | +0.00 | +0.00 (0.00) | +0.00 | 0.50 / 0.50 | 0.0 |
| (c) KB book-lean skip, imb10 AGAINST >=5 min | K6 | **OFF** | -0.7 (1.2) | -0.6 (1.1) | -0.0 | -0.2 | -1.1 | -0.44 (0.89) | -0.45 | 0.17 / 0.19 | 0.5 |
| (d) ES-lead sizer, last 1-min bar >=2 ticks x1.5 with / x0.5 against | K6 | **OFF** | -3.8 (5.4) | -2.5 (5.1) | +1.8 | -0.6 | -2.9 | -1.31 (1.71) | -1.53 | 0.00 / 0.01 | 21.8 |
| (d) ES-lead sizer, last 1-min bar >=2 ticks x1.5 with / x0.5 against | P6 | **OFF** | -2.0 (11.4) | -1.8 (10.8) | +4.8 | -0.5 | -8.6 | -0.51 (1.94) | -0.55 | 0.38 / 0.30 | 13.3 |
| (d) ES-lead sizer, last 1-min bar >=2 ticks x1.5 with / x0.5 against | U6 | **OFF** (watch: + in L6M and HOLD, inside MDE) | +0.2 (2.3) | +0.3 (2.1) | -0.3 | -0.0 | +0.6 | +0.17 (4.79) | +0.84 | 0.56 / 0.55 | 2.3 |
| (d) ES-lead sizer, last 1-min bar >=2 ticks x1.5 with / x0.5 against | H6 | **OFF** (watch: + in L6M and HOLD, inside MDE) | +0.9 (4.1) | +0.7 (3.8) | +0.3 | -1.0 | +1.5 | -0.88 (2.28) | -1.07 | 0.22 / 0.23 | 8.9 |
| (d) ES-lead sizer, last 1-min bar >=2 ticks x1.5 with / x0.5 against | M6 | **OFF** | -0.5 (3.8) | -0.4 (3.4) | -0.6 | +0.6 | +2.0 | -0.19 (2.98) | -0.38 | 0.29 / 0.30 | 12.2 |
| (d) ES-lead sizer, last 1-min bar >=2 ticks x1.5 with / x0.5 against | A6 | **OFF** | -0.47 (0.7) | -0.48 (0.7) | -0.16 | +0.03 | -0.51 | -1.47 (2.88) | -1.23 | 0.09 / 0.06 | 2.6 |

(c) is a KB-only rule (the D6 sign convention: skip when imb10 is AGAINST the signal for >= 5 consecutive minute samples, 5% dead band). The mirror (skip when the book leans OUR way, the direction KBR found positive in the rate) is scored in section 3: also OFF.

**D7 group 12 defaults (ships Off, all four):**

| group 12 rule | default | reason in one line |
|---|---|---|
| (a) skip first 60 min of each session | **OFF** | stack -6.8 / -5.3 $k/wk L6M / HOLD (MDE 14.6 / 17.2), PRE -10.5, X' +0.6; the rate gain (+2.01 pts/lot L6M) is paid for with volume |
| (b) skip own next signal <= 30 min after a loser | **OFF** | stack -0.1 / +0.1 (MDE 2.6 / 2.4), PRE -1.3, X' -0.9; touches 3.4 signals/wk (2%) |
| (c) KB book-lean skip (imb10 against >= 5 min) | **OFF** | stack -0.7 / -0.6 (MDE 1.2 / 1.1); 0.5 KB signals/wk touched, all in the wrong direction on the stack |
| (d) ES-lead sizer (last 1-min bar >= 2 ticks, x1.5 / x0.5) | **OFF** | stack -6.2 / -4.6 (MDE 12.2 / 12.1), PRE +5.5, X' -2.0; rate -1.15 pts/lot L6M; K6 rank 0.00 vs shuffled ES |

If all four were switched ON together the stack would be -10.5 / -8.1 / -6.4 / -5.7 / +0.3 $k/wk (L3M / L6M / HOLD / PRE / X') vs the composite (MDE 16.4 L6M).

**Tier (honest):** all four DEAD for D7 purposes on the stack (0 of 19 rule-by-book lines clear MDE in L6M or HOLD); (a) first-60 skip is a rate LEAD only (positive per planned lot in L3M/L6M/HOLD, negative in PRE, stack <= 0), (d) is DEAD at live lots (K6 and the total are below their shuffled-ES draws). Post-hoc status: all four rules were fixed by the user's text, not selected here; earlier looks at the same families exist (N1c, N1b, N1e, KBR, ESL; EINT2 exclfirst60), so nothing here is a first look and nothing is promoted.

## 1. Method, ties and units

* **Engine and tie-out.** ss2_lib (SS-2 lock engine, D6 running-max locks: BookR = base lots x running max of the day's multipliers x stop pts x $20, reset at the 18:00 ET label day; per-book day arm, entry test and week floor) reproduces the SS-2 headline to the dollar before any rule is added (live lots, fractional split, running max, Native 1.28: +19.4 / +18.5 / +16.2 / +4.7 / +12.5 $k/wk L3M/L6M/HOLD/PRE/X', MDE 24.1 / 17.4 / 16.8 / 13.4 / 14.7; run t0.py). The composite used here adds the integer 70/30 split (K6 1/1, U6 3/1, H6 3/1 and 1/1, P6 5/2, M6 1/1, add slip +0.25/lot), the ER lots rounded half-up min 1 (Math.Max(1, Floor(lots*mult+0.5))) and A6 at 1 lot in Asia only: **+26.2 / +22.4 / +19.1 / +7.0 / +12.7 vs the stack as it is ($k/wk)** (L3M/L6M/HOLD/PRE/X'; MDE 24.1 / 17.9 / 17.5 / 12.9 / 14.4); SS-2 has +25.0 / +22.8 / +19.3 / +7.4 / +12.9 with A6 in every session. Not in this engine: the D6 combined (stack) week lock found by GOV-1; section 4 repeats the four rules on the GOV-1 D6-faithful engine (running max over all signals, session-lot R, combined 12R lock).

* **Cross-check against an earlier look.** The first-60 skip on the plain six-book research stack (70/30 split only, no ER, no cut, no zone, research lots, base governors) in this engine gives +11.2k L6M / +18.3k HOLD / -28.8k PRE / +14.5k X' (N1c: +15.7k / +23.5k / -32.2k / +13.9k). The sign pattern ties; the gain lives in the books and settings that are not in the live composite: with the composite (ER sizer, cut, zone, PE confirm, running-max locks) the same rule is -15.7 L6M at research lots and -6.8 at live lots (section 4).

* **Rules as coded here.** (a) a signal is skipped when its ET entry minute is < 60 min after its session start (asia 18:00, london 02:00, pre 08:30 [whole session], nyam 09:30, nypm 12:00, close 15:00); only sessions with live lots matter. (b) skip when the book's previous TAKEN trade of the same side lost (post-lock $) and the signal comes 0-1800 s after that trade's rule-sim exit; the previous trade is the last taken one, so a skipped re-entry does not become the new anchor (research anchor = previous trade close, per SH-2 / FORWARD_SHADOW_RUNBOOK). (c) KB only: imb10 (top-10 imbalance, 1-s tape) sampled at the last 5 minute boundaries before the signal (the newest is 0-59 s old), side-signed; a sample is AGAINST when side*imb10 < -0.05 (dead band 0.05; 28% of KB signal-time samples fall inside it, 40% are AGAINST, 33% OUR-way); skip when all 5 are AGAINST. (d) ES last completed 1-min bar close minus the prior bar close (1-s ES last-price tape, dominant contract), x side, in ticks of 0.25: >= +2 -> x1.5 with, <= -2 -> x0.5 against, else x1; the multiplier multiplies the ER multiplier (lots = session lot x ER x ES, half-up, min 1) and enters the running-max SizeMult (engine multiplier route; variant d0: governors see the ER multiplier only). ES covers 2023-04..2026-01-31 only (multiplier 1 afterwards, 3 weeks of L3M).
* **Rules act on all books at once; the per-book line is the book's own lock-engine line** (books are independent in the engine except the Asia-stopped cut). Eligible signals = baseline-kept signals with live lots > 0: 11069 over the whole window; touched by rule: (a) 4154, (b) 342, (c) 59 [OUR-way 34], (d) 7709 resized.
* **A6 = PB7.** PB7 (PB5 depth ATR 0.5, W15, s+0, Asia, stop 60 / target 60, 671 trades 2023-04..2026-02, cid 45 of the ssa members) has no series in the trade library, so it is simulated as a stand-alone book on the same 1-s tape (market +1 tick adverse, scan_from, SS-2 cost model, stop cost 1.28), with its own per-book lock engine (entry test, day arm, week floor, running max, 1 lot, ER(20) 5m recomputed from the tape: matches the store on the 44,370 library rows at corr 0.9999, threshold agreement 99.97%). Its stack line is +1.98 $k/wk L6M at 1 lot. The cut-rule interplay with the other books is NOT modelled for A6; the library PB series (all sessions in the engine, Asia only in the live table) stays inside the 'ALL BOOKS' total as the proxy; the A6 PB7 deltas are at most 0.5k/wk, so the totals do not depend on the choice.

* **Units.** Stack = lock-engine $/wk at live lots (post-lock per-trade pnl x 20 x research lots for the session lines; per-book daily series for the book lines). Rate = risk-matched pts per planned lot: sum(m y)/sum(m) - mean(y) over the live-lot signals (m = lots after the rule / lots before, 0 for a skip; equal total lots), y = pts per planned lot after costs of the rule-sim outcome. Per contract = sum(lots y)/sum(lots) over the final integer live lots, before -> after. MDE of the rate and of the per-contract delta = 2.8 x SD of a 1,000-draw week-block bootstrap.

* **Placebos.** Skip rules: 200 stack draws and 2,000 trade-level draws of a random skip with the same count per book x session x half-year (the stack placebo is an all-books draw read on each line; (c) uses KB only); (d): the ES multiplier shuffled within book x session x half-year (same multiplier mix). Rank = share of draws the real value beats (ties half). Because any random skip of profitable signals lowers the stack (placebo mean -18k L6M for (a)), a high rank for a skip rule does not make the rule pay; it says the removed signals are worse than random ones.

## 2. Rule by rule: per book and per session (stack, rate, per contract)

### 2.1 (a) skip first 60 min of each session

Stack delta vs the composite, $k/wk at live lots (MDE in brackets), by book then by session:

| line | L3M | L6M | HOLD | PRE | X' | placebo rank L6M / HOLD / PRE (200 draws) |
|---|---|---|---|---|---|---|
| ALL BOOKS (stack total, A6 = PB library proxy inside) | -3.2 (20.2) | -6.8 (14.6) | -5.3 (17.2) | -10.5 (11.9) | +0.6 (10.7) | 1.00 / 1.00 / 0.41 |
| K6 (KB) | +0.9 (5.5) | +0.5 (4.5) | +0.9 (4.4) | -2.5 (3.0) | +0.5 (2.4) | 0.96 / 0.96 / 0.10 |
| P6 (PE) | -4.4 (15.6) | -4.8 (10.8) | -4.4 (11.8) | -4.5 (9.8) | -0.7 (8.0) | 0.94 / 0.94 / 0.59 |
| U6 (SM) | +0.7 (4.6) | +0.0 (2.6) | +0.5 (2.5) | -0.5 (1.7) | -0.7 (1.8) | 0.53 / 0.80 / 0.59 |
| H6 (HM) | -1.8 (7.4) | -2.4 (4.4) | -2.3 (4.2) | -1.2 (2.3) | +1.3 (2.6) | 0.91 / 0.85 / 0.45 |
| M6 (MV) | +1.0 (2.9) | -0.2 (2.3) | +0.0 (2.4) | -1.4 (1.9) | +0.5 (2.0) | 0.59 / 0.69 / 0.36 |
| A6 = PB7 (stand-alone book) | -0.50 (1.8) | -0.35 (1.2) | -0.26 (1.0) | -0.17 (0.7) | -0.07 (1.0) | 0.49 / 0.49 / 0.70 |

| line | L3M | L6M | HOLD | PRE | X' | placebo rank L6M / HOLD / PRE (200 draws) |
|---|---|---|---|---|---|---|
| Asia (all books) | +0.5 (17.4) | -1.3 (10.9) | -1.7 (11.5) | -5.6 (8.5) | -0.1 (10.2) | 0.99 / 0.98 / 0.28 |
| London | -1.6 (8.8) | -1.5 (5.8) | -1.1 (5.3) | -1.8 (4.4) | +1.6 (4.5) | 0.67 / 0.75 / 0.16 |
| NY-AM | -3.4 (11.2) | -4.7 (9.9) | -3.3 (10.2) | -3.3 (5.9) | -1.0 (8.8) | 0.74 / 0.85 / 0.88 |
| NY-PM | +1.4 (2.2) | +0.8 (2.1) | +0.8 (1.8) | +0.2 (1.7) | +0.2 (1.3) | 0.84 / 0.81 / 0.76 |

Rate, risk-matched pts per planned lot (MDE):

| line | L3M | L6M | HOLD | PRE | X' | rate rank L6M / HOLD |
|---|---|---|---|---|---|---|
| ALL BOOKS (stack total, A6 = PB library proxy inside) | +2.12 (2.60) | +2.01 (2.01) | +2.30 (2.36) | -1.39 (2.11) | +1.84 (4.17) | 0.98 / 0.99 |
| K6 (KB) | +2.35 (4.17) | +3.10 (3.62) | +3.53 (3.74) | -1.48 (3.29) | +1.53 (4.97) | 0.90 / 0.95 |
| P6 (PE) | +1.18 (5.72) | +1.20 (3.95) | +1.58 (3.87) | -1.82 (3.14) | +1.68 (7.52) | 0.73 / 0.79 |
| U6 (SM) | -1.34 (7.30) | -1.07 (5.95) | +0.12 (5.86) | -0.06 (4.06) | -0.10 (7.04) | 0.34 / 0.49 |
| H6 (HM) | +2.63 (6.31) | +1.76 (6.03) | +1.92 (6.87) | -1.40 (4.17) | +3.96 (8.79) | 0.74 / 0.75 |
| M6 (MV) | +0.10 (6.48) | -0.82 (5.93) | -0.20 (5.38) | -2.18 (2.94) | +1.15 (6.46) | 0.40 / 0.52 |
| A6 = PB7 | -4.43 (3.75) | -3.83 (4.52) | -3.15 (4.39) | -0.01 (4.26) | -0.58 (9.83) | 0.04 / 0.06 |

| line | L3M | L6M | HOLD | PRE | X' | rate rank L6M / HOLD |
|---|---|---|---|---|---|---|
| Asia (all books) | +4.64 (6.29) | +4.59 (5.09) | +4.60 (5.05) | -1.14 (3.67) | +4.74 (9.28) | 1.00 / 1.00 |
| London | +0.80 (4.06) | -0.43 (3.49) | +0.01 (3.31) | -0.81 (2.00) | +1.74 (4.22) | 0.31 / 0.47 |
| NY-AM | -0.43 (10.28) | +1.13 (7.00) | +1.60 (7.11) | -1.68 (4.09) | +0.46 (7.92) | 0.68 / 0.76 |
| NY-PM | -2.30 (13.88) | -0.94 (8.44) | -0.39 (7.88) | +1.91 (7.16) | +1.82 (9.06) | 0.42 / 0.47 |

Trade-level units (signals per week, touched per week, mean pts per planned lot of skipped vs all signals, per contract of final lots before -> after):

| line | window | sig/wk | touched/wk | skipped-signal mean pts/lot | all-signal mean pts/lot | per contract before -> after (delta, MDE) |
|---|---|---|---|---|---|---|
| ALL BOOKS (stack total, A6 = PB library proxy inside) | L6M | 91.1 | 33.9 | +2.63 | +6.03 | +7.37 -> +9.21 (+1.84, 2.68) |
| ALL BOOKS (stack total, A6 = PB library proxy inside) | HOLD | 87.4 | 32.8 | +1.71 | +5.53 | +7.14 -> +9.13 (+2.00, 3.01) |
| ALL BOOKS (stack total, A6 = PB library proxy inside) | PRE | 81.1 | 28.9 | +6.44 | +3.93 | +4.49 -> +3.36 (-1.14, 2.55) |
| K6 (KB) | L6M | 29.2 | 11.9 | -1.27 | +3.27 | +5.89 -> +10.05 (+4.15, 4.12) |
| K6 (KB) | HOLD | 27.6 | 11.2 | -2.43 | +2.72 | +5.09 -> +9.31 (+4.22, 4.21) |
| K6 (KB) | PRE | 24.8 | 9.2 | +6.63 | +4.13 | +4.48 -> +2.17 (-2.31, 3.57) |
| P6 (PE) | L6M | 20.4 | 6.5 | +3.67 | +6.22 | +7.78 -> +8.97 (+1.20, 4.08) |
| P6 (PE) | HOLD | 19.6 | 6.4 | +3.19 | +6.45 | +7.93 -> +9.29 (+1.36, 4.16) |
| P6 (PE) | PRE | 17.7 | 5.9 | +7.31 | +3.71 | +4.70 -> +3.71 (-0.99, 3.50) |
| U6 (SM) | L6M | 4.4 | 0.7 | +9.38 | +3.49 | +1.72 -> +1.79 (+0.06, 6.59) |
| U6 (SM) | HOLD | 4.4 | 0.7 | +2.64 | +3.34 | +2.72 -> +3.90 (+1.19, 6.29) |
| U6 (SM) | PRE | 4.7 | 1.0 | +6.76 | +6.53 | +5.92 -> +6.15 (+0.23, 4.42) |
| H6 (HM) | L6M | 13.8 | 5.9 | +8.73 | +11.10 | +13.05 -> +16.52 (+3.47, 6.24) |
| H6 (HM) | HOLD | 13.2 | 5.7 | +7.50 | +10.03 | +12.02 -> +15.06 (+3.04, 7.27) |
| H6 (HM) | PRE | 12.7 | 5.0 | +6.13 | +3.99 | +3.91 -> +2.68 (-1.23, 4.71) |
| M6 (MV) | L6M | 16.0 | 6.0 | +5.38 | +4.00 | +2.02 -> +1.74 (-0.28, 5.98) |
| M6 (MV) | HOLD | 15.4 | 5.8 | +4.33 | +4.00 | +1.96 -> +2.52 (+0.56, 5.93) |
| M6 (MV) | PRE | 14.3 | 5.4 | +7.57 | +4.03 | +3.79 -> +1.97 (-1.82, 3.77) |
| A6 = PB7 | L6M | 6.0 |  | +27.11 | +6.32 | +11.08 -> +8.43 (-2.64, 4.47) |
| A6 = PB7 | HOLD | 5.9 |  | +20.64 | +4.49 | +8.93 -> +6.85 (-2.08, 4.07) |
| A6 = PB7 | PRE | 4.5 |  | +11.80 | +11.77 | +11.60 -> +11.26 (-0.34, 4.41) |

### 2.2 (b) skip a book's next signal <= 30 min after its own loser

Stack delta vs the composite, $k/wk at live lots (MDE in brackets), by book then by session:

| line | L3M | L6M | HOLD | PRE | X' | placebo rank L6M / HOLD / PRE (200 draws) |
|---|---|---|---|---|---|---|
| ALL BOOKS (stack total, A6 = PB library proxy inside) | -1.2 (4.7) | -0.1 (2.6) | +0.1 (2.4) | -1.3 (2.1) | -0.9 (1.3) | 0.76 / 0.79 / 0.34 |
| K6 (KB) | -0.2 (3.7) | +0.1 (2.0) | +0.3 (1.8) | -0.5 (0.9) | -0.2 (0.5) | 0.64 / 0.82 / 0.28 |
| P6 (PE) | -0.1 (2.6) | +0.4 (1.9) | +0.3 (1.6) | -0.6 (1.4) | -0.5 (1.0) | 0.80 / 0.79 / 0.44 |
| U6 (SM) | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) | 0.31 / 0.32 / 0.96 |
| H6 (HM) | +0.2 (1.1) | +0.1 (0.7) | +0.1 (0.6) | -0.2 (0.5) | -0.0 (0.1) | 0.82 / 0.77 / 0.23 |
| M6 (MV) | -1.0 (1.5) | -0.6 (0.9) | -0.6 (0.8) | +0.0 (1.1) | -0.2 (0.5) | 0.10 / 0.10 / 0.68 |
| A6 = PB7 (stand-alone book) | +0.00 (0.0) | +0.00 (0.0) | +0.00 (0.0) | +0.00 (0.0) | +0.00 (0.0) | 0.50 / 0.50 / 0.50 |

| line | L3M | L6M | HOLD | PRE | X' | placebo rank L6M / HOLD / PRE (200 draws) |
|---|---|---|---|---|---|---|
| Asia (all books) | -0.5 (2.9) | +0.2 (1.8) | +0.3 (1.6) | -0.2 (0.9) | -0.3 (0.9) | 0.67 / 0.68 / 0.41 |
| London | +0.1 (2.1) | +0.0 (1.1) | +0.0 (0.9) | -0.6 (0.9) | -0.2 (0.3) | 0.65 / 0.66 / 0.10 |
| NY-AM | +0.1 (2.4) | +0.1 (1.3) | +0.2 (1.2) | -0.4 (1.6) | -0.4 (0.9) | 0.78 / 0.78 / 0.62 |
| NY-PM | -0.8 (2.4) | -0.4 (1.2) | -0.3 (1.1) | -0.0 (0.5) | -0.0 (0.2) | 0.14 / 0.15 / 0.50 |

Rate, risk-matched pts per planned lot (MDE):

| line | L3M | L6M | HOLD | PRE | X' | rate rank L6M / HOLD |
|---|---|---|---|---|---|---|
| ALL BOOKS (stack total, A6 = PB library proxy inside) | +0.29 (0.85) | +0.21 (0.55) | +0.20 (0.51) | -0.25 (0.37) | -0.32 (0.40) | 0.69 / 0.72 |
| K6 (KB) | +0.40 (2.20) | +0.53 (1.41) | +0.61 (1.33) | -0.26 (0.78) | -0.38 (0.97) | 0.78 / 0.85 |
| P6 (PE) | +0.70 (1.13) | +0.43 (0.76) | +0.40 (0.71) | +0.00 (0.68) | -0.30 (0.73) | 0.86 / 0.83 |
| U6 (SM) | +0.00 (0.00) | +0.00 (0.00) | +0.00 (0.00) | +0.00 (0.00) | +0.00 (0.00) | 0.50 / 0.50 |
| H6 (HM) | +0.41 (2.43) | +0.19 (1.63) | +0.02 (1.48) | -0.24 (0.90) | -0.18 (0.48) | 0.67 / 0.54 |
| M6 (MV) | -0.55 (3.11) | -0.70 (2.33) | -0.64 (2.14) | -0.90 (1.13) | -0.76 (1.59) | 0.15 / 0.16 |
| A6 = PB7 | +0.00 (0.00) | +0.00 (0.00) | +0.00 (0.00) | +0.00 (0.00) | +0.00 (0.00) | 0.50 / 0.50 |

| line | L3M | L6M | HOLD | PRE | X' | rate rank L6M / HOLD |
|---|---|---|---|---|---|---|
| Asia (all books) | +0.22 (0.81) | +0.17 (0.55) | +0.21 (0.51) | +0.09 (0.40) | -0.09 (0.24) | 0.74 / 0.79 |
| London | +0.21 (1.18) | +0.12 (0.71) | +0.12 (0.62) | -0.75 (0.65) | -0.27 (0.50) | 0.65 / 0.66 |
| NY-AM | +0.48 (2.30) | +0.22 (1.50) | +0.21 (1.40) | -0.42 (0.88) | -0.61 (1.03) | 0.58 / 0.58 |
| NY-PM | -1.45 (8.74) | -0.16 (4.54) | -0.13 (4.18) | +0.95 (2.45) | -0.19 (1.71) | 0.46 / 0.46 |

Trade-level units (signals per week, touched per week, mean pts per planned lot of skipped vs all signals, per contract of final lots before -> after):

| line | window | sig/wk | touched/wk | skipped-signal mean pts/lot | all-signal mean pts/lot | per contract before -> after (delta, MDE) |
|---|---|---|---|---|---|---|
| ALL BOOKS (stack total, A6 = PB library proxy inside) | L6M | 91.1 | 3.4 | +0.66 | +6.03 | +7.37 -> +7.55 (+0.18, 0.39) |
| ALL BOOKS (stack total, A6 = PB library proxy inside) | HOLD | 87.4 | 3.0 | +0.01 | +5.53 | +7.14 -> +7.34 (+0.20, 0.37) |
| ALL BOOKS (stack total, A6 = PB library proxy inside) | PRE | 81.1 | 2.8 | +11.01 | +3.93 | +4.49 -> +4.32 (-0.18, 0.32) |
| K6 (KB) | L6M | 29.2 | 1.7 | -5.37 | +3.27 | +5.89 -> +6.30 (+0.41, 1.34) |
| K6 (KB) | HOLD | 27.6 | 1.5 | -7.66 | +2.72 | +5.09 -> +5.69 (+0.60, 1.34) |
| K6 (KB) | PRE | 24.8 | 1.2 | +9.50 | +4.13 | +4.48 -> +4.30 (-0.18, 0.75) |
| P6 (PE) | L6M | 20.4 | 0.4 | -15.90 | +6.22 | +7.78 -> +8.06 (+0.28, 0.65) |
| P6 (PE) | HOLD | 19.6 | 0.3 | -15.90 | +6.45 | +7.93 -> +8.18 (+0.25, 0.61) |
| P6 (PE) | PRE | 17.7 | 0.5 | +3.66 | +3.71 | +4.70 -> +4.58 (-0.12, 0.52) |
| U6 (SM) | L6M | 4.4 | 0.0 | - | +3.49 | +1.72 -> +1.72 (+0.00, 0.00) |
| U6 (SM) | HOLD | 4.4 | 0.0 | - | +3.34 | +2.72 -> +2.72 (+0.00, 0.00) |
| U6 (SM) | PRE | 4.7 | 0.0 | - | +6.53 | +5.92 -> +5.92 (+0.00, 0.00) |
| H6 (HM) | L6M | 13.8 | 0.3 | +3.18 | +11.10 | +13.05 -> +13.38 (+0.33, 1.18) |
| H6 (HM) | HOLD | 13.2 | 0.3 | +9.04 | +10.03 | +12.02 -> +12.26 (+0.24, 1.06) |
| H6 (HM) | PRE | 12.7 | 0.3 | +12.44 | +3.99 | +3.91 -> +3.70 (-0.21, 0.75) |
| M6 (MV) | L6M | 16.0 | 0.9 | +15.44 | +4.00 | +2.02 -> +1.15 (-0.87, 1.71) |
| M6 (MV) | HOLD | 15.4 | 0.8 | +15.44 | +4.00 | +1.96 -> +1.18 (-0.78, 1.65) |
| M6 (MV) | PRE | 14.3 | 0.8 | +19.67 | +4.03 | +3.79 -> +3.08 (-0.71, 0.97) |
| A6 = PB7 | L6M | 6.0 |  | - | +6.32 | +11.08 -> +11.08 (+0.00, 0.00) |
| A6 = PB7 | HOLD | 5.9 |  | - | +4.49 | +8.93 -> +8.93 (+0.00, 0.00) |
| A6 = PB7 | PRE | 4.5 |  | - | +11.77 | +11.60 -> +11.60 (+0.00, 0.00) |

### 2.3 (c) KB book-lean skip, imb10 AGAINST >= 5 min

Stack delta vs the composite, $k/wk at live lots (MDE in brackets), by book then by session:

| line | L3M | L6M | HOLD | PRE | X' | placebo rank L6M / HOLD / PRE (200 draws) |
|---|---|---|---|---|---|---|
| ALL BOOKS (stack total, A6 = PB library proxy inside) | -1.1 (2.4) | -0.7 (1.2) | -0.6 (1.1) | -0.0 (0.5) | -0.3 (0.5) | 0.17 / 0.20 / 0.56 |
| K6 (KB) | -1.1 (2.4) | -0.7 (1.2) | -0.6 (1.1) | -0.0 (0.5) | -0.2 (0.5) | 0.17 / 0.19 / 0.60 |

| line | L3M | L6M | HOLD | PRE | X' | placebo rank L6M / HOLD / PRE (200 draws) |
|---|---|---|---|---|---|---|
| Asia (all books) | -0.4 (1.0) | -0.2 (0.5) | -0.2 (0.4) | +0.0 (0.3) | -0.1 (0.3) | 0.12 / 0.14 / 0.77 |
| London | -0.5 (1.5) | -0.3 (0.8) | -0.3 (0.7) | -0.1 (0.1) | -0.1 (0.4) | 0.33 / 0.34 / 0.17 |
| NY-AM | +0.3 (1.1) | +0.1 (0.6) | +0.1 (0.5) | -0.0 (0.3) | +0.1 (0.2) | 0.62 / 0.64 / 0.39 |
| NY-PM | -0.6 (1.4) | -0.2 (0.7) | -0.2 (0.6) | +0.1 (0.2) | -0.1 (0.2) | 0.15 / 0.15 / 0.69 |

Rate, risk-matched pts per planned lot (MDE):

| line | L3M | L6M | HOLD | PRE | X' | rate rank L6M / HOLD |
|---|---|---|---|---|---|---|
| ALL BOOKS (stack total, A6 = PB library proxy inside) | -0.08 (0.44) | -0.12 (0.29) | -0.12 (0.26) | -0.01 (0.11) | -0.06 (0.24) | 0.10 / 0.09 |
| K6 (KB) | -0.31 (1.34) | -0.44 (0.89) | -0.41 (0.82) | -0.02 (0.39) | -0.22 (0.83) | 0.10 / 0.09 |

| line | L3M | L6M | HOLD | PRE | X' | rate rank L6M / HOLD |
|---|---|---|---|---|---|---|
| Asia (all books) | -0.19 (0.48) | -0.16 (0.31) | -0.15 (0.29) | +0.05 (0.29) | +0.01 (0.36) | 0.11 / 0.12 |
| London | +0.16 (1.51) | +0.02 (0.92) | +0.02 (0.87) | -0.04 (0.23) | -0.29 (0.79) | 0.64 / 0.66 |
| NY-AM | -0.13 (0.35) | -0.13 (0.22) | -0.12 (0.20) | -0.02 (0.15) | -0.02 (0.27) | 0.13 / 0.13 |
| NY-PM | +0.00 (0.00) | -0.42 (1.20) | -0.39 (1.15) | -0.17 (0.47) | -0.13 (1.43) | 0.20 / 0.21 |

Trade-level units (signals per week, touched per week, mean pts per planned lot of skipped vs all signals, per contract of final lots before -> after):

| line | window | sig/wk | touched/wk | skipped-signal mean pts/lot | all-signal mean pts/lot | per contract before -> after (delta, MDE) |
|---|---|---|---|---|---|---|
| ALL BOOKS (stack total, A6 = PB library proxy inside) | L6M | 91.1 | 0.5 | +28.41 | +6.03 | +7.37 -> +7.30 (-0.07, 0.13) |
| ALL BOOKS (stack total, A6 = PB library proxy inside) | HOLD | 87.4 | 0.4 | +28.41 | +5.53 | +7.14 -> +7.07 (-0.07, 0.12) |
| ALL BOOKS (stack total, A6 = PB library proxy inside) | PRE | 81.1 | 0.4 | +5.07 | +3.93 | +4.49 -> +4.48 (-0.01, 0.08) |
| K6 (KB) | L6M | 29.2 | 0.5 | +28.41 | +3.27 | +5.89 -> +5.44 (-0.45, 0.75) |
| K6 (KB) | HOLD | 27.6 | 0.4 | +28.41 | +2.72 | +5.09 -> +4.66 (-0.43, 0.69) |
| K6 (KB) | PRE | 24.8 | 0.4 | +5.07 | +4.13 | +4.48 -> +4.40 (-0.08, 0.48) |

### 2.4 (d) ES-lead sizer, last completed 1-min bar

Stack delta vs the composite, $k/wk at live lots (MDE in brackets), by book then by session:

| line | L3M | L6M | HOLD | PRE | X' | placebo rank L6M / HOLD / PRE (200 draws) |
|---|---|---|---|---|---|---|
| ALL BOOKS (stack total, A6 = PB library proxy inside) | -8.9 (21.2) | -6.2 (12.2) | -4.6 (12.1) | +5.5 (12.2) | -2.0 (8.5) | 0.05 / 0.06 / 0.98 |
| K6 (KB) | -2.9 (8.4) | -3.8 (5.4) | -2.5 (5.1) | +1.8 (3.2) | -0.6 (2.0) | 0.00 / 0.01 / 0.78 |
| P6 (PE) | -8.6 (16.7) | -2.0 (11.4) | -1.8 (10.8) | +4.8 (9.8) | -0.5 (6.1) | 0.38 / 0.30 / 0.99 |
| U6 (SM) | +0.6 (3.7) | +0.2 (2.3) | +0.3 (2.1) | -0.3 (1.3) | -0.0 (1.4) | 0.56 / 0.55 / 0.18 |
| H6 (HM) | +1.5 (5.2) | +0.9 (4.1) | +0.7 (3.8) | +0.3 (1.7) | -1.0 (1.3) | 0.22 / 0.23 / 0.32 |
| M6 (MV) | +2.0 (5.5) | -0.5 (3.8) | -0.4 (3.4) | -0.6 (1.6) | +0.6 (1.8) | 0.29 / 0.30 / 0.05 |
| A6 = PB7 (stand-alone book) | -0.51 (0.9) | -0.47 (0.7) | -0.48 (0.7) | -0.16 (0.5) | +0.03 (0.4) | 0.09 / 0.06 / 0.50 |

| line | L3M | L6M | HOLD | PRE | X' | placebo rank L6M / HOLD / PRE (200 draws) |
|---|---|---|---|---|---|---|
| Asia (all books) | +1.8 (15.6) | -1.0 (7.5) | -1.2 (7.2) | +1.5 (7.4) | +0.3 (3.2) | 0.20 / 0.10 / 0.60 |
| London | -7.5 (12.2) | -2.3 (7.1) | -2.0 (6.4) | +1.2 (6.2) | -1.9 (4.4) | 0.14 / 0.16 / 0.95 |
| NY-AM | -3.5 (11.2) | -2.9 (7.6) | -1.6 (7.5) | +2.2 (5.4) | -0.1 (5.7) | 0.12 / 0.14 / 0.77 |
| NY-PM | +0.3 (1.8) | -0.0 (1.7) | +0.2 (1.7) | +0.6 (1.7) | -0.3 (1.0) | 0.56 / 0.79 / 0.74 |

Rate, risk-matched pts per planned lot (MDE):

| line | L3M | L6M | HOLD | PRE | X' | rate rank L6M / HOLD |
|---|---|---|---|---|---|---|
| ALL BOOKS (stack total, A6 = PB library proxy inside) | -1.35 (1.47) | -1.15 (1.10) | -0.94 (1.09) | +0.20 (0.97) | -1.37 (1.55) | 0.05 / 0.12 |
| K6 (KB) | -1.83 (2.01) | -1.31 (1.71) | -0.92 (1.88) | +0.08 (1.16) | -1.79 (1.87) | 0.12 / 0.24 |
| P6 (PE) | -1.12 (2.14) | -0.51 (1.94) | -0.68 (2.00) | +1.78 (1.37) | -0.07 (2.52) | 0.21 / 0.16 |
| U6 (SM) | +1.01 (6.01) | +0.17 (4.79) | -0.35 (4.35) | -1.01 (2.89) | -0.63 (4.24) | 0.55 / 0.43 |
| H6 (HM) | -0.69 (2.87) | -0.88 (2.28) | -0.84 (2.38) | -0.34 (1.84) | -2.18 (2.60) | 0.28 / 0.34 |
| M6 (MV) | +0.63 (3.33) | -0.19 (2.98) | +0.15 (2.96) | -0.30 (1.95) | +0.81 (3.88) | 0.26 / 0.38 |
| A6 = PB7 | -1.51 (4.23) | -1.47 (2.88) | -1.74 (2.45) | -0.48 (2.17) | +0.10 (2.49) | 0.29 / 0.16 |

| line | L3M | L6M | HOLD | PRE | X' | rate rank L6M / HOLD |
|---|---|---|---|---|---|---|
| Asia (all books) | -2.52 (2.44) | -2.18 (1.70) | -2.04 (1.60) | +0.22 (1.31) | -0.35 (1.89) | 0.00 / 0.00 |
| London | +0.26 (4.36) | +0.76 (2.76) | +0.63 (2.57) | +0.71 (1.77) | -1.70 (2.90) | 0.78 / 0.78 |
| NY-AM | -1.41 (1.83) | -1.43 (1.25) | -1.00 (1.50) | -0.41 (1.39) | -1.14 (2.46) | 0.07 / 0.19 |
| NY-PM | +3.19 (5.61) | +2.03 (3.68) | +1.72 (3.78) | +0.82 (2.30) | -2.27 (4.16) | 0.93 / 0.90 |

Trade-level units (signals per week, touched per week, mean pts per planned lot of skipped vs all signals, per contract of final lots before -> after):

| line | window | sig/wk | touched/wk | skipped-signal mean pts/lot | all-signal mean pts/lot | per contract before -> after (delta, MDE) |
|---|---|---|---|---|---|---|
| ALL BOOKS (stack total, A6 = PB library proxy inside) | L6M | 91.1 | 62.6 | - | +6.03 | +7.37 -> +6.50 (-0.87, 1.14) |
| ALL BOOKS (stack total, A6 = PB library proxy inside) | HOLD | 87.4 | 59.7 | - | +5.53 | +7.14 -> +6.31 (-0.83, 1.13) |
| ALL BOOKS (stack total, A6 = PB library proxy inside) | PRE | 81.1 | 58.7 | - | +3.93 | +4.49 -> +5.44 (+0.94, 1.00) |
| K6 (KB) | L6M | 29.2 | 21.8 | - | +3.27 | +5.89 -> +4.36 (-1.53, 1.65) |
| K6 (KB) | HOLD | 27.6 | 20.3 | - | +2.72 | +5.09 -> +4.09 (-1.00, 1.86) |
| K6 (KB) | PRE | 24.8 | 19.6 | - | +4.13 | +4.48 -> +4.94 (+0.46, 1.07) |
| P6 (PE) | L6M | 20.4 | 13.3 | - | +6.22 | +7.78 -> +7.23 (-0.55, 2.23) |
| P6 (PE) | HOLD | 19.6 | 12.8 | - | +6.45 | +7.93 -> +7.15 (-0.78, 2.34) |
| P6 (PE) | PRE | 17.7 | 12.1 | - | +3.71 | +4.70 -> +6.82 (+2.11, 1.66) |
| U6 (SM) | L6M | 4.4 | 2.3 | - | +3.49 | +1.72 -> +2.56 (+0.84, 4.68) |
| U6 (SM) | HOLD | 4.4 | 2.3 | - | +3.34 | +2.72 -> +3.27 (+0.55, 4.15) |
| U6 (SM) | PRE | 4.7 | 2.8 | - | +6.53 | +5.92 -> +5.07 (-0.85, 2.95) |
| H6 (HM) | L6M | 13.8 | 8.9 | - | +11.10 | +13.05 -> +11.98 (-1.07, 2.68) |
| H6 (HM) | HOLD | 13.2 | 8.6 | - | +10.03 | +12.02 -> +11.08 (-0.94, 2.69) |
| H6 (HM) | PRE | 12.7 | 9.1 | - | +3.99 | +3.91 -> +3.92 (+0.01, 1.83) |
| M6 (MV) | L6M | 16.0 | 12.2 | - | +4.00 | +2.02 -> +1.64 (-0.38, 4.27) |
| M6 (MV) | HOLD | 15.4 | 11.5 | - | +4.00 | +1.96 -> +1.94 (-0.01, 4.10) |
| M6 (MV) | PRE | 14.3 | 11.2 | - | +4.03 | +3.79 -> +3.69 (-0.10, 2.18) |
| A6 = PB7 | L6M | 6.0 |  | - | +6.32 | +11.08 -> +9.85 (-1.23, 3.32) |
| A6 = PB7 | HOLD | 5.9 |  | - | +4.49 | +8.93 -> +7.33 (-1.60, 2.80) |
| A6 = PB7 | PRE | 4.5 |  | - | +11.77 | +11.60 -> +11.01 (-0.59, 2.50) |

### 2.5 Reading across the four rules

* (a) The signals in the first hour of a session are worse per planned lot than the rest in L3M/L6M/HOLD (skipped mean +2.63 vs all +6.03 pts/lot L6M; K6 +3.1, P6 +1.2, H6 +1.8 rate) and better in PRE (rate -1.39), and the random-skip placebo ranks it 1.00 on the stack in L6M/HOLD, but 38% of live-lot signals are in that hour and removing that volume costs more than the lower per-signal quality saves (stack -6.8 $k/wk L6M). By book only K6 and U6 are positive in L6M and HOLD on the stack (+0.5 / +0.9 and +0.0 / +0.5, both far inside MDE 4-5k and 2.5k) and K6 is -2.5k in PRE. By session the stack is -1.3 (Asia), -1.5 (London), -4.7 (NY-AM), +0.8 (NY-PM) $k/wk L6M: no session carve-out clears MDE either.
* (b) Skipping the same-side re-entry <= 30 min after a loser touches 3.4 signals/wk (2%) and moves the stack by -0.1 / +0.1 $k/wk (L6M / HOLD), MDE 2.6 / 2.4; the rate is +0.21 pts/lot L6M (rank vs random skips 0.69) and flips to -0.25 in PRE, the same shape as N1b and S2's first-stop rule (recent-only, PRE negative). It is not an A6 rule at all (PB7 never re-enters the same side inside 30 min after a loser).
* (c) With the D6 convention (AGAINST >= 5 min, 5% dead band, minute samples) the rule fires on 0.5 KB signals/wk (1.7% of KB signals) and is negative on the stack in L6M and HOLD (-0.7 / -0.6, MDE 1.2 / 1.1), rate -0.12; the book-lean information that KBR saw lives in the sign-run version with no dead band, 3-minute blocks (section 3).
* (d) The 2-tick threshold fires on 80% of signals (50% x1.5, 20% x0.5, 30% unchanged): ES moves with the signal in most NQ signals (they are momentum signals), so the sizer is mostly a 1.5x leverage on the signal that already has momentum. Rate -1.15 pts/lot L6M (MDE 1.10), stack -6.2 / -4.6 L6M / HOLD, positive in PRE (+5.5) and negative in X' (-2.0): the sign flips with the window; K6 (-3.8 / -2.5, rank 0.00 / 0.01) and the total sit below the shuffled-ES draws in L6M. Variant d0 (governors see the ER multiplier only) is -4.6 L6M / +7.9 PRE; neither reading is positive in both L6M and HOLD.

## 3. (c) both directions and the run length (KB, D6 convention vs KBR's)

D6 convention (this report): sign of imb10 x side beyond the 5% dead band at minute samples; run = consecutive samples. **AGAINST = D7's rule** (skip when the book leans against the signal); **OUR-way = the mirror (skip when it leans with the signal), the direction KBR / N1e found positive in the rate** (KBR: AGAINST >= 3 min rate PRE -1.0, OUR-way >= 3 min rate L6M +0.90, stack -1.7k). Stack delta $k/wk vs the composite, total (= KB: no other book is touched), MDE in brackets:

| variant | direction | run (samples) | KB signals touched /wk L6M | L3M | L6M | HOLD | PRE | X' | rate L6M | per contract d L6M |
|---|---|---|---|---|---|---|---|---|---|---|
| c_against3 | AGAINST (D7 rule) | 3 | 1.8 | -2.1 (3.9) | -1.3 (2.4) | -0.8 (2.3) | -0.0 (1.2) | -0.1 (1.3) | -0.94 | -0.71 |
| c_against5 (headline) | AGAINST (D7 rule) | 5 | 0.5 | -1.1 (2.4) | -0.7 (1.2) | -0.6 (1.1) | -0.0 (0.5) | -0.3 (0.5) | -0.44 | -0.45 |
| c_against6 | AGAINST (D7 rule) | 6 | 0.3 | -0.5 (1.6) | -0.4 (0.8) | -0.3 (0.7) | +0.1 (0.3) | -0.0 (0.4) | -0.26 | -0.29 |
| c_our3 | OUR way (KBR positive direction) | 3 | 1.9 | -0.4 (2.8) | -0.7 (1.8) | -0.6 (1.6) | -0.3 (0.8) | +0.2 (0.6) | -0.14 | -0.15 |
| c_our5 | OUR way (KBR positive direction) | 5 | 0.4 | +0.3 (0.9) | -0.1 (0.7) | -0.1 (0.6) | -0.1 (0.5) | -0.1 (0.2) | +0.05 | +0.01 |
| c_our6 | OUR way (KBR positive direction) | 6 | 0.2 | +0.4 (0.7) | -0.1 (0.7) | -0.1 (0.6) | +0.0 (0.3) | +0.0 (0.0) | +0.10 | +0.00 |

Reading: AGAINST is <= 0 on the stack in L6M and HOLD at every run length (3 / 5 / 6 samples) and OUR-way is ~0 (+-0.1k at 5-6 samples, -0.7k at 3); with the dead band and minute sampling the OUR-way rate is also ~0 at 5 and 6 (KBR's +0.9 was a 3-minute block-mean sign run without a dead band and fired on 20% of signals; here the 5% dead band removes 28% of samples and the run must be 5 consecutive minute samples, so the same idea fires on 1-2% of KB signals). Neither direction is worth a D7 default. The 3-sample variants are sensitivities (counted in the 24 stack-level cells of the prereg), not a re-selection.

## 4. Sensitivities and robustness (total stack, $k/wk vs the composite, MDE in brackets)

**D6-faithful engine** (GOV-1 gf_lib: running max over ALL signals, BookR on the session lot, + combined week lock 12R(K6); noisier because the combined lock fires in about half of the weeks):

| rule | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| (a) skip first 60 min of each session | -3.1 (20.4) | -3.5 (19.7) | -4.5 (18.8) | -4.2 (11.5) | +5.2 (12.8) |
| (b) skip next signal <=30 min after own loser | -2.2 (3.5) | -1.1 (1.9) | -0.8 (1.8) | -0.7 (1.6) | -0.4 (0.5) |
| (c) KB book-lean skip, imb10 AGAINST >=5 min | -0.1 (0.7) | -0.2 (0.4) | -0.1 (0.4) | +0.1 (0.6) | +0.2 (0.8) |
| (d) ES-lead sizer, last 1-min bar >=2 ticks x1.5 with / x0.5 against | -12.7 (21.7) | -9.5 (13.2) | -7.6 (12.4) | +5.3 (9.2) | -4.7 (12.3) |
| (c) mirror: KB OUR-way >= 5 | +0.1 (0.9) | -0.2 (0.7) | -0.2 (0.6) | -0.0 (0.3) | +0.0 (0.1) |
| (d0) governors see the ER multiplier only (main engine) | -6.8 (17.7) | -4.6 (11.9) | -3.0 (11.8) | +7.9 (8.8) | -1.3 (9.7) |

**Other lots / governors (main engine):**

| lots, governor | rule | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| LIVE + ST, WT at research/2.35 | (a) a | -1.2 (28.9) | -8.9 (21.8) | -6.0 (24.2) | -19.5 (15.3) | +2.9 (15.5) |
| LIVE + ST, WT at research/2.35 | (b) b | -0.8 (4.8) | +0.1 (2.6) | +0.3 (2.4) | -1.4 (2.1) | -0.9 (1.2) |
| LIVE + ST, WT at research/2.35 | (c) c_against5 | -0.6 (2.1) | -0.6 (1.1) | -0.5 (1.0) | -0.1 (0.6) | -0.2 (0.5) |
| LIVE + ST, WT at research/2.35 | (d) d | -2.0 (25.4) | +1.6 (15.2) | +1.9 (16.1) | +11.8 (14.9) | -5.1 (11.5) |
| LIVE + ST, WT at research/2.35 | (c) c_our5 | +0.3 (0.9) | -0.1 (0.8) | -0.1 (0.7) | -0.1 (0.5) | -0.0 (0.2) |
| RESEARCH lots (six books) | (a) a | +4.5 (64.8) | -15.7 (50.8) | -8.3 (48.0) | -33.9 (31.6) | +11.7 (29.6) |
| RESEARCH lots (six books) | (b) b | +1.0 (12.3) | +1.4 (6.5) | +1.9 (5.9) | -3.0 (4.2) | -0.8 (1.6) |
| RESEARCH lots (six books) | (c) c_against5 | -1.1 (3.0) | -1.2 (1.8) | -1.0 (1.6) | -0.6 (2.0) | -0.5 (1.5) |
| RESEARCH lots (six books) | (d) d | +1.3 (71.7) | +18.6 (44.3) | +16.1 (43.2) | +22.7 (25.2) | -11.1 (20.8) |
| RESEARCH lots (six books) | (c) c_our5 | +0.8 (2.5) | -0.5 (2.0) | -0.4 (1.8) | -0.4 (1.1) | -0.1 (0.5) |
| LIVE lots, base-lot governors (no multiplier on the locks) | (a) a | +3.9 (29.4) | -4.1 (16.2) | -3.7 (16.6) | -5.0 (11.2) | +0.3 (11.3) |
| LIVE lots, base-lot governors (no multiplier on the locks) | (b) b | -0.2 (6.8) | -0.1 (3.4) | +0.1 (3.0) | -1.4 (2.7) | -0.9 (1.3) |
| LIVE lots, base-lot governors (no multiplier on the locks) | (c) c_against5 | -1.3 (2.5) | -0.7 (1.7) | -0.6 (1.5) | -0.2 (0.7) | -0.4 (0.7) |
| LIVE lots, base-lot governors (no multiplier on the locks) | (d) d | +0.0 (17.9) | -2.2 (11.4) | -1.2 (10.5) | +7.0 (8.5) | -1.0 (9.7) |
| LIVE lots, base-lot governors (no multiplier on the locks) | (c) c_our5 | +0.4 (1.1) | +0.1 (0.7) | +0.1 (0.6) | -0.1 (0.5) | -0.3 (0.8) |

**Combinations (all rules on together, main engine):** a+b+c+d: -10.5 / -8.1 / -6.4 / -5.7 / +0.3; a+b+c: -4.5 / -6.7 / -5.0 / -11.7 / -0.5; b+c+d: -8.6 / -5.8 / -4.0 / +4.3 / -3.3; b+c: -2.0 / -0.6 / -0.3 / -1.2 / -1.2 ($k/wk L3M / L6M / HOLD / PRE / X'; MDE of a+b+c+d 16.4 L6M). Nothing is positive in L6M or HOLD.

## 5. What can be said about the group-12 defaults

All four are OFF. If D7 later wants a watch list for the Shadow log (not a default): (a) K6 (+0.5 / +0.9 L6M / HOLD, rate +3.1 pts/lot, placebo 0.96; PRE -2.5), (b) K6 and P6 (+0.1..0.4k, rate +0.4..0.5, PRE negative). These are inside MDE and PRE-negative: Shadow only, not a setting.

## 6. Limits and open questions

* A6 is PB7 stand-alone (no cut-rule interplay); the library PB is the proxy inside the total. MV/M6 and PB use the S73 split cell; the live splits are the integer forms (K6 1/1 etc.).
* Rule (b) uses the baseline post-lock pnl of the previous taken trade and its rule-sim exit second (a lock exit can be earlier); skipping a signal can free the book for a later one (the engine's busy filter handles that for the lots, the rule mask does not re-run the chain after unblocking). Second-order.
* Skipped signals do not feed the running-max SizeMult here (they are removed from the engine); D6 as coded may count a SKIPPED-but-logged signal toward the day's maximum. For the ER x1.5 signals this would raise the lock R after a skip. Open question in MORNING.md: does a D7-skipped signal still update SizeMult? (The default I used is no.)
* The sizer (d) is run through the engine multiplier route (governors see the product); the ES multiplier changes lots after rounding: K6 2 lots x ER 1.5 x ES 1.5 = 4.5 -> 5, x0.5 -> 2 (half-up) so integer effects are visible in the K6 line.
* Question for MORNING.md: D7 group 12 'first 60 min' - is the session boundary the ET clock list above (Asia 18:00, London 02:00, NY-AM 09:30, NY-PM 12:00) or the book's first live session minute? The numbers above use the clock list; the 09:00-10:00 block is not applied here.
* ES tape ends 2026-01-31: L3M has ~12 of 13 weeks of ES; 2026 (5 weeks) is one real week of Feb: not used.

## 7. Files and reproduce

`l2vast/ds3/code/d7filters/`: feats.py (features), d7lib.py (scenario wrapper over ss2_lib), rules.py (masks), evalcore.py (stack and trade metrics), run_main.py (real runs), placebo.py (200 stack / 2,000 trade draws per rule), pb7.py + run_a6.py (A6 = PB7), run_rob.py, run_all4.py, report.py (this file). Outputs `l2vast/ds3/out/d7filters/`: main.pkl, main_gf.pkl, placebo_*.pkl, a6_pb7.pkl, robust_lots.pkl, all4.pkl, lines.csv (every line), page1.csv. Run with OMP/MKL=1, `python3 -I`; D7_GF=1 for the GOV-1 engine.
