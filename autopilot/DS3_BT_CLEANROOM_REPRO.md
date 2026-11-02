# DS3_BT_CLEANROOM_REPRO - independent (clean-room) reproduction of ZL-1's BT swing flip flag (S4b, 2026-11-02)
Built ONLY from the live definition text in DS3_BT_SWING_FLIP_CANDIDATE.md section 2 (ZL-1's code was not opened). Code l2vast/ds3/code/zones3/cleanroom/bt_flip.py (flag) and score_bt.py (taken trades, V13Y lock none); masks and tables in /mnt/l2/l2vast/ds3_zones3_new/s4b/cleanroom/. Tape = de-duplicated 1-s print path (ds3_g2_redo SS/SH/SL: per print-second high/low, so a "print >= L+10" is "second high >= L+10"), flagged on the 88,490 engine rows of out/zl/d_rows.npz.

## Verdict
**The lead reproduces.** Literal reading of the text: 3,038 flagged rows vs ZL-1's 2,819; Jaccard 0.917 over all rows and **0.983 from 2023-08 on** (2,831 flagged, 30 extra, 18 missing). Saved dollars on V13Y taken trades (lock none, 18,827 taken trades, same as ZL-1; net of all taken trades ties to the run total 2,563,277):

| mask | flagged taken | L3M | L6M | HOLD | MID | PRE | X' (saved $k) |
|---|---|---|---|---|---|---|---|
| ZL-1 mask | 1,035 | +30.4 (n 94) | +69.8 (n 204) | +74.9 (n 359) | +17.9 (n 84) | +103.4 (n 416) | +50.1 (n 155) |
| clean-room, literal text | 1,104 | +33.0 (n 96) | +71.6 (n 204) | +76.1 (n 360) | +17.9 (n 84) | +97.7 (n 414) | +33.7 (n 225) |
| clean-room, literal text, label day >= 2023-08-01 | 1,035 | +33.0 | +71.6 | +76.1 | +17.9 | +97.7 | +49.6 (n 156) |
| clean-room, return counted in the break second | 1,072 | +32.0 | +67.0 | +70.8 | +16.5 | +91.7 | +29.1 |
| clean-room, lenient freshness at the signal second | 1,109 | +32.2 | +70.7 | +75.3 | +17.9 | +101.7 | +33.7 |
| clean-room, require 5 contiguous bars | 1,096 | +33.3 | +71.3 | +74.7 | +17.9 | +103.0 | +31.9 |

L3M, L6M, HOLD and MID agree within 2 to 5% (L6M +71.6 vs +69.8, HOLD +76.1 vs +74.9, MID identical); PRE is -5.5% (97.7 vs 103.4); X' differs only because of coverage (below) and agrees once 2023-04..07 is dropped (49.6 vs 50.1). Flagged taken trades: 1,035 in both once the same start date is applied.

## Every ambiguity that changed a result
1. **Coverage start (not a wording ambiguity, the largest single difference).** ZL-1's main stream has no events before 2023-08 (text, point 8: "events start 2023-08 ... a path-based version covers 2023-04..07"); a literal implementation of the definition also flags 2023-04..07 (207 of the 237 extra rows; 78+32+50+47 in April-July 2023). Effect: X' saved +33.7k instead of +50.1k, taken flagged 1,104 vs 1,035. The definition is silent on this; D7 live has no such gap. Whether the 2023-04..07 flags are real is a separate result (they lower the X' number and are in the x' window).
2. **Does the break second itself count for the "return to L" test?** The text: fresh until "price returns to L ... at the break price is 10+ pts away, so fresh ends at the first return". I start the return scan at the second AFTER the break second. Counting the break second removes 18 of the 30 residual extra rows but also drops 72 rows ZL-1 flags, so ZL-1 is not using that convention uniformly; it is the biggest wording effect on dollars (PRE 97.7 -> 91.7, L6M 71.6 -> 67.0).
3. **"Keep the last 3 swing highs/lows".** Interpreted as: a swing is dropped when the 3rd newer swing of the same kind becomes known, and a dropped swing can no longer be broken. This matters hugely: keep 1 -> Jaccard 0.79, no limit -> 0.83 (542 extra rows). The text fixes 3 but does not say whether a dropped swing can still flip; my reading matches ZL-1 (nokeep adds only 3 of the 18 missing rows).
4. **Freshness at the signal second ("state at the end of the signal second").** A return in the signal second itself: I count the level as no longer fresh (strict); the lenient variant adds 16 rows with a negligible dollar effect (+0.1 to -0.9k).
5. **Gaps in the bar series.** The text does not say whether the 5-bar fractal window must be contiguous in time (no missing 5-min bars). Requiring contiguity changes 15 flags and moves the dollars by less than 1k except PRE (+5k); the no-check reading is closer to ZL-1 (Jaccard 0.983 vs 0.977).
6. Level life 4 h is exact: 3 h changes the flags a lot (Jaccard 0.72), so the text's 4 h is binding. The "print" vs "close" break is explicit in the text and the 1-s per-second high is the same thing at the available resolution.

## What is NOT explained
After 2023-08, 12 extra and 18 missing rows (0.6% of flagged) are not removed or added by any variant I tried (contiguity, lenient/strict freshness, break-second return, keep rule, life). Candidate causes: second-boundary handling of the signal second, tick rounding of L+10, or ZL-1's tape stream; no dollar consequence beyond about +-1k per window.

## Not done
Second-order effect (re-running the engine with the mask as extra_skip), lock=12R, the 1-3 s detection delay test, and the "last 12 months per book x session" counts of section 3.

# UPDATE (S4b, after the lead's follow-up order): engine dollars, detection delay, pinned definition, residual rows, early period
## A. Engine run with the mask as extra_skip (second-order: sizing, locks, U7 interplay), V13Y
Cells = maxDD $k / mean $k per wk / worst-20 $k, per window. Source: cleanroom/engine_bt.txt.
**Lock none (V13Y; headline)**
| mask | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|
| base | 31 / +19.7 / 256 | 96 / +28.8 / 90 | 103 / +24.6 / -480 | 30 / +16.4 / 197 | 130 / +12.1 / -648 | 70 / +1.6 / -400 |
| ZL-1 mask | 28 / +21.1 / 274 | 91 / +31.1 / 148 | 95 / +27.0 / -400 | 21 / +20.2 / 243 | 128 / +13.2 / -634 | 77 / +2.0 / -383 |
| clean-room, literal (from first bar) | 28 / +21.3 / 277 | 91 / +30.9 / 146 | 95 / +26.9 / -400 | 21 / +20.2 / 243 | 132 / +13.2 / -635 | 83 / +1.7 / -387 |
| clean-room, label day >= 2023-08-01 | 28 / +21.3 / 277 | 91 / +30.9 / 146 | 95 / +26.9 / -400 | 21 / +20.2 / 243 | 132 / +13.2 / -635 | 77 / +2.0 / -384 |
| clean-room, 2023-04..07 only | 31 / +19.7 / 256 | 96 / +28.8 / 90 | 103 / +24.6 / -480 | 30 / +16.4 / 197 | 130 / +12.1 / -648 | 75 / +1.3 / -403 |
**Lock 12R (V13Y)**
| mask | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|
| base | 27 / +13.8 / 179 | 53 / +21.2 / -59 | 90 / +16.4 / -396 | 52 / +6.7 / 80 | 282 / +5.9 / -514 | 132 / -1.1 / -304 |
| ZL-1 mask | 22 / +14.8 / 193 | 48 / +24.8 / 9 | 58 / +20.9 / -366 | 42 / +9.7 / 117 | 215 / +9.1 / -500 | 132 / +0.5 / -303 |
| clean-room, literal | 22 / +15.0 / 196 | 48 / +24.6 / 9 | 58 / +20.8 / -366 | 42 / +9.7 / 117 | 219 / +9.0 / -500 | 102 / +1.0 / -322 |
| clean-room, >= 2023-08 | 22 / +15.0 / 196 | 48 / +24.6 / 9 | 58 / +20.8 / -366 | 42 / +9.7 / 117 | 219 / +9.0 / -500 | 132 / +0.4 / -304 |
Reading: the engine result (mean +2.2 to +2.4k/wk in L6M/HOLD at lock none, maxDD L6M 96 -> 91k, MID 30 -> 21k) is the same for the clean-room and the ZL-1 mask in every window except X' (coverage start) and PRE maxDD (132 vs 128k at lock none, 219 vs 215k at 12R: the 30 extra / 18 missing rows). It is a MEAN effect with small maxDD cuts (L6M -5%, HOLD -8% at lock none; HOLD -36% and PRE -24% at 12R, where it again looks lock-linked). The literal 2023-04..07 flags alone change nothing in L3M..PRE and make X' slightly worse at lock none (+1.3 vs +1.6 mean).
## B. Detection delay (first-order saved $k on V13Y taken trades, lock none, label day >= 2023-08-01)
Processing delay after the 5-min bar close (the swing becomes known at bar close + 1/3/5 s) and break-detection lag (the level is usable by a signal only 1/3/5 s after the break print): the flagged set and the dollars do NOT change (L6M +71.6, HOLD +76.1 to +76.7, PRE +97.7 to +98.6, X' +49.6, MID +17.9); 2,831 flagged rows fall to 2,795 at a 5 s lag. The edge persists with a realistic 1-5 s delay. An entry latency of 1-3 s changes fills, not the flag; its dollar effect is not simulated here (the first-order saved dollars are fill-independent). File cleanroom/delay_table.md.
## C. Pinned definition (agreed with ZL-1 in messages; both implementations coincide on every point)
1. 5-min bars clock-aligned, high/low of prints in the bar (per-second print highs/lows). 2. Swing = bar high (low) strictly above (below) the 2 bars before and the 2 after; known at the close of the 2nd following bar. No contiguity requirement for the 5 bars. 3. Keep the last 3 swing highs and 3 swing lows by known time; a swing is dropped the moment the 3rd newer swing of the same kind becomes known and a dropped swing can no longer break. 4. Break = first print >= L+10 (<= L-10) after the swing is known and before it is dropped. 5. Flip level at L valid 4 h from the break second; fresh until a print returns to L (SL <= L for a broken high, SH >= L for a broken low), scanning from the second AFTER the break second. 6. A signal in second s sees the state at the end of s: the level counts iff break second <= s and end-of-fresh second > s and s <= break + 4 h. 7. Flag iff 0 <= (L-E long | E-L short) <= min(40, td). 8. Coverage: events from the first available bar (no calendar start); the 2023-08 start of ZL-1's stream was a build artefact of the L2 1-s table months, not part of the rule.
## D. The residual 30 + 18 rows (after 2023-08)
Not month-start warm-up artefacts: only 7 of the 30 and 2 of the 18 fall in the first 6 days of a month; 4 of the 30 are on 2023-08-01 (ZL-1's first day with a warm-up). The rest sit on ~20 scattered label days, 6 of which appear in BOTH lists (2024-12-18, 2025-06-17, 2025-12-16, 2026-06-15/16, 2026-09-16: large-move days), i.e. rows decided by a within-second or tick-level difference between the two tape sources (L2 1-s table hi/lo vs the path SH/SL) around the L+10 break or the return to L. No definitional cause remains.
## E. The early period 2023-04..07 (literal reading, taken trades V13Y lock none)
69 flagged taken trades of 983 (7.0%, vs 5.8% in 2023-08..2026-10), saved -15.9k (flagged mean +230 per trade vs unflagged -22; later flagged -191 vs unflagged +165). Flag-minus-unflag mean difference in the early period +252 per trade, 90% bootstrap CI [-265, +762]: it includes zero and cannot be told apart from the later -356 only by its sign. Per month: April -11.1k (25 flagged, mean +446), May +0.1k, June -3.7k, July -1.2k. By book: KB 36 flagged (-5.5k), HM 10 (-7.3k), PE 18 (-4.4k). Tape density is the same (36-39k print-seconds per day in 2023-04..07 vs 38-43k in 2023-08..2024-03), and the flag rate is similar; the early base is also a weak regime for the whole stack (X' era: unflagged mean -22/trade). Reading: NOT a tape artefact (thin tape, instrument ids, Sunday hours are not visible), but a small sample (69 trades, one bad April) whose sign is inside noise; it is out-of-regime in the sense that the base itself had no edge then. It halves nothing that matters: with the early rows the pooled X' saved is +33.7k instead of +49.6k.
