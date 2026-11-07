# GATE0_REBUILD_BASE8 - PRE-PROOF, post-hoc, frozen live file only. NO PASS CLAIM. Gate 0 NOT passed. No gate0 JSON, A-G not launched.
Code read: data/live_code/DS7.cs (sha 54697597..., read-only), GATE0_ANSWERS_1106.md. Frozen file sha 424c68da.... Private code l2vast/ds3/code/blind/rebuild8/ {ws8.py 33a406a2, gap8.py 9b3c99b8, fill8.py 1b3d3a66, score8.py 7f876fe0, census8.py 246f487d}. Bulk /mnt/l2/l2vast/ds3_base8/. Prereg l2vast/ds3/prereg/GATE0_REBUILD8_prereg.md (sha 9bfbd3a0..., incl. addendum 1) with lines in DECISIONS.md BEFORE scoring; iteration lines appended (>>) to GATE0_ITERATIONS.md. Config as live (old-panel skip slots ON to Mon 08:50; r3b not used; Tue 02:55-08:20 excluded; nothing tuned to the live outcome). Seal: ds3_all_ea/manifest_after.json 18,638 files re-hashed at start and end: 0 missing / 0 changed / 0 new.

## 1. SizeMult in the PRIMARY (code-exact)
DS7.cs: SizeMult field 230, reset at session roll 680, set in TrendSize 1721-1722 (mult > SizeMult, even if lots do not change) and SsSize 1158; both run in L2Arm 1469 (and OTE-through 1980) BEFORE NtzCheck (1473) and before any fill; BookR 3412 = BaseQty x max(1,SizeMult) x Stop x $20; dollar caps x max(1,SizeMult) 3463-3469. NtzCheck Half (1999-2005) halves lots AFTER the sizer (does not touch SizeMult).
ws8 rule: at every signal that passes the engine entry gates (busy, lock, blackout, Confirm at its confirm time) SizeMult(book, 18:00 ET day) = max(ER mult, P7 SizeHi 1.5), ER mult 1.5 if 5-min ER(20) >= 0.30 before Mon 13:30 ET, else 1.0; lock R and caps scaled. This replaces r7's heuristic (taken trades, lots >= 1.25 x table). Difference: P7 flagged signals 6 vs 3; other books equal. **Trade list identical to r6/r7 (198 rows, +53,753).**
| run | G1 | G2 | G3 10 s | G3 60 s | G4 | n / net |
|--|--|--|--|--|--|--|
| **r8 PRIMARY** | **.704 F** | **.484 F** | **.347 F** | **.467 F** | **.418 F** | 198 / +53.8k |
| r8a profit/take off | .704 | .477 | .347 | .467 | .418 | 198 / +54.4k |
| r8h heuristic SizeMult (=r7) | .704 | .484 | .347 | .467 | .418 | 198 / +53.8k |
| r8o DIAGNOSTIC (oracle live profit exits) | .748 | .456 | .374 | .496 | .458 | 208 / +56.6k |
| r8t DIAGNOSTIC SENSITIVITY (market entry at opposite touch, s.3) | .757 | .452 | .357 | .481 | .422 | 196 / +57.0k |
All fail every gate. Live 187 / +104,095. Profit-side exits stay diagnostic (live DOM absent).

## 2. Net gap decomposition (r8; live 104,095 - engine 53,753 = 50,342; fees none on either side, FEES.md n/a: live pnlNet = qty x pts x $20)
live minus engine = (a) live-only trades + (b) minus engine-only trades + (c) matched pairs (159).
| book | live n/$ | eng n/$ | gap | (a) live-only n/$ | (b) eng-only n / -$ | (c) pairs $ = size + entry + exit + live-row resid |
|--|--|--|--|--|--|--|
| P7 | 53 / +86,010 | 62 / +28,890 | +57,120 | 6 / +22,255 | 15 / +7,190 | +27,675 = -5,908 -2,570 +35,465 +688 |
| K7 | 64 / +16,065 | 65 / +13,590 | +2,475 | 11 / +6,335 | 12 / -1,007 | -2,853 = -2,400 -885 +417 +15 |
| M7 | 28 / +6,015 | 27 / +6,748 | -733 | 4 / -1,790 | 3 / +744 | +313 = -442 -170 +1,663 -737 |
| A7 | 23 / -1,415 | 23 / +4,243 | -5,658 | 3 / +135 | 3 / -1,775 | -4,018 |
| U7 | 6 / -1,755 | 7 / +5,595 | -7,350 | 0 | 1 / -4,800 | -2,550 (resid -2,379: live row net != qty x px x 20) |
| H7, O7, X3-X5 | | | -2,000 | | | |
| **ALL** | 187 / +104,095 | 198 / +53,753 | **+50,342** | 28 / **+27,545** | 39 / **+4,723** | 159 / **+18,074** = size -11,655, entry -4,016, exit +36,139, resid -2,394 |
Pair parts are engine-vs-live on the same trade: size = (lots difference) x live points, entry = engine entry px vs live, exit = engine exit px vs live (priced at engine lots).
**Top 3 causes (live minus engine):**
1. **Engine ThL2Cut where live ran to target on matched trades: 5 pairs +33,717** (P7 +24,419: Wed 19:27 and Thu 02:53 +12.9k each; K7 +5,584; M7 +3,714), offset by 4 pairs engine target / live cut -7,300 (net exit-type mismatch about +26k). The ZL-2 cut evaluator (mbp-10 reconstruction) fires where the live DOM did not; both-cut pairs (76) net only -440.
2. **P7 live-only +22,255 (6 trades) with 15 P7 engine-only (-7,190 of net, i.e. +7,190 to the gap)**: the Sun evening chain: engine-only 17-lot Sun 19:04 (-15.6k, class B, no code reason found) makes the engine busy so live Sun 19:11 (10 lots, +12.0k) and Sun 20:45 (+4.8k) are missing; follow-on engine-only A1 trades (Sun 19:28 -7.0k, 22:42 -6.0k) hit the same cause.
3. **K7 lock cascade: K7 live-only +6,335 (11 trades, 9 lock-gated Mon 01:45-13:54)** and K7 engine-only -1,007. SizeMult exact does not remove it (r8 = r6): the engine K7 day equity still reaches its lock/give-back; in the diagnostic r8o (oracle profit exits) 9 of 11 were removed in r7o. Cause stays the profit-side exit (live DOM).
Offsetting (they widen the gap if fixed): engine lots larger than live on matched winners **-11,655**, engine entries better than live **-4,016**.
**P7 lots on matched trades (47 pairs): 43 equal; 4 differ, all engine > live:** Sun 18:36 engine 6 / live 4 (SizeHi rank .68 borderline: live x1.0, known), Thu 10:39 7 vs 5 and Wed 07:25 7 vs 5 (= round(0.7 x 7) = 5, the 30% add unfilled in live), Wed 05:02 2 vs 1. P7 size part -5,908 (of which Thu 10:39 -2,400, Sun 18:36 -2,402, Wed 05:02 -1,200). Non-P7: 7 pairs engine 2 vs live 1 (A7 Sun 18:47, 20:12; K7 Wed 03:06, 07:42; M7 Wed 03:05, 06:00; U7 Wed 07:10), size -6.3k; engine ER (20, 5-min) is .30-.45 at these signals (live qty 1 = x0.5 or NtzCheck Half 1999-2005); cause unresolved, no fix applied (candidates: live ER below .30, or NTZ Half; needs the live log).

## 3. Entry fill (159 matched; engine px minus live px, sign = + engine paid more)
Mean -0.56 pt, median -0.50, sd 1.71, 10/90% -2.25/+1.30; 33 of 159 |d| >= 2 pt. By book (mean / median): A7 -.82/-.75, K7 -.75/-.50, M7 -.24/-.25, P7 -.46/-.50, U7 -.21/-.02, H7 -.46, X3 -2.5. Short and long alike (-.59 / -.52). Dollar value of the entry gap, lots-weighted: engine better by $4,016 (P7 2,570, K7 885, A7 265). The K7 Sun 20:09 trade (-2.75 pt) is in the tail: the engine is better than live by >= 0.25 pt in 61% of trades (>= 2 pt better in 23, >= 2 pt worse in 10 of 159).
Code (read, not inferred): entry slices and the add are MARKET orders (PumpEntry 2748, 1 lot / SliceGapMs, 70/30 split K7/P7/U7/H7/M7; add = one market order at dip >= 3 pt with a confirmation, L2AddStage 1531). fillv4 (fillsim.entry_fills) fills each slice at the **first tape print >= sig+1+2k s**, not at the opposite touch. fill8.py on the 83 single-lot matched trades (live entry within 1 s of the signal): fillv4 first print **mean -0.70 pt (engine better), median -0.50, MAE 1.25**; opposite touch of the book at sig+1 **mean +0.09, median +0.25, MAE 1.01**; 75% of engine fills are better than the opposite touch (print can sit at the near side; median table spread 1.25 pt). Same direction as FILL_MODEL_V4's known 1-lot residual (+0.50). This is a code-fact mismatch (market order pays the touch), reported as r8t (diagnostic sensitivity, not primary, not selected): G1 .757, G2 .452, G3 .357/.481, G4 .422; n 196, +57.0k; fails all.

## 4. Open items
1. Live DOM for the profit-side trigger and the cut mismatches (cause 1 and 3). 2. Live qty halving at 7 non-P7 signals and P7 5-of-7 (add unfilled): live log. 3. Whether the user wants entry_touch promoted to primary (changes G1/G2 materially; it is mechanics, not outcome-tuned, but the table's bid/ask definition is unverified). 4. Sun 19:04 P7 17-lot trade (no code reason). 5. G3 amendment unconfirmed.
Safety: only rebuild8 code, /mnt/l2/l2vast/ds3_base8/, DECISIONS.md / GATE0_ITERATIONS.md (append), prereg, this file; memory 129 GB free; no process killed.
