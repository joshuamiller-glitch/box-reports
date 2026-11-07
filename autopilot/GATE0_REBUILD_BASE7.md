# GATE0_REBUILD_BASE7 - PRE-PROOF, post-hoc, frozen live file only. NO PASS CLAIM. Gate 0 is NOT passed. No gate0 JSON written, A-G not launched.
Code read from data/live_code/DS7.cs (sha256 54697597...), GATE0_ANSWERS_1106.md. Frozen file sha 424c68da... Private code l2vast/ds3/code/blind/rebuild7/ {stream7.py e7ad578c, zl2_eval7.py 1eb9f0d5, ws7.py (final sha in DECISIONS.md addenda), score7, census7, explain7, busy7, g3_exact7, val7, manifest7}. Bulk /mnt/l2/l2vast/ds3_base7/. Prereg l2vast/ds3/prereg/GATE0_REBUILD7_prereg.md sha 96ede8b0... (+ addenda 1-3), lines in DECISIONS.md BEFORE scoring; every iteration appended (>>) to GATE0_ITERATIONS.md. Config as live (old-panel skip slots ON to Mon 08:50; no tuning to live outcomes; r3b not used). Outage Tue 02:55-08:20 excluded. Seal: manifest_after.json (18,638 files) re-hashed at start and end: 0 missing, 0 changed, 0 new; derived scripts grepped (only the inherited read-only ds3_g2_blind SS/SC mmap).

## 1. Profit side of ManageThL2 (DS7.cs line numbers)
- 1572-1575 entry guards (ExitPending, Bip, NoBracket); unreal from b.EntryPx (fill average).
- 1577 **trail touch tested on EVERY print, before and independent of DepthLive and the 1-s gate**: long price<=ThL2TrailPx, short >=; clears the trail, exits market, name **ThL2Trail**.
- 1579 DepthLive (depth event <120 s, >=5 levels/side); 1580 ThL2LastEval 1-s gate, shared by profit and loss branches.
- 1581-1590 `unreal>0` -> profit branch: needs ThL2ProfitOn (default false, 443; **old panel ON, user ruling: until Mon 08:05**), unreal >= ThL2ProfitMinPts 30, curDepthRel not NaN, else ThickSince reset (1583); curDepthRel >= ThickMult 2.0 starts/keeps ThickSince, below resets (1584-1585); fires after ThickSecs 10 (1586). ThL2ProfitTake false (443) -> **tighten** (1588-1589): trail = RoundTick(FavExt -/+ 30), set/ratchet only in the trade's favour; persists until touched. (Take variant 1587 'ThL2Take' is not used; none in the live file.)
- FavExt/AdvExt 3159-3162: running extremes of the print price, reset to EntryPx at each fill (3050). Trail distance ThL2ProfitTrailPts 30 (443).
- curDepthRel 1547-1559: (bid 8-tick + ask 8-tick depth within 7.5 ticks of each own touch) / EWMA baseline per ET half hour (alpha .02 for the first 300 snapshots of the slot, then .002, per print), NaN until 300 snapshots; cold at strategy start.
- Policy (ManagePolicy 2170-2205, Feature 2076-2097): profit rules first-match per book; pct = unreal / TARGET distance; ahead_rel = own exit-side 8-tick depth / (0.5 x slot normal total); tot_rel = curDepthRel; actions take->'PolicyTake', tighten->PolicyTrailPx ('PolicyTrail'), 1-s PolicyLastEval gate. Mon 08:05-08:15: K7 tighten 30, P7 take pct>=.5 ahead>=1.5, H7 .3/1.5, U7 .17 tot_rel>=1.5, * .7/1.2 (operators >= assumed; K7 conditions not given).
- **Live exits named ThL2Trail / take in the frozen file (4 of 187):** A7 Sun 20:12 -> 21:54:37 ThL2Trail (+505, exit 28757.00); K7 Sun 20:09:01 -> 21:54:37 ThL2Trail (+540, 28756.50); X5 Mon 07:20 -> 08:05:09 PolicyTake (+44 pts, +1,765); M7 Mon 06:58 -> 08:05:20 PolicyTake (+42 pts = 0.70 of target, +840). No ThL2Take, no PolicyTrail, no PolicyTake outside the window. ThL2Trail: only trigger is thick book (rel>=2 for 10 s) at >=+30 pts then a 30-pt give-back from FavExt (K7 FavExt ~28788 -> trail ~28758, touched 28756.5).
- K7 'tighten 30' line is NOT modelled: unconditioned it would have set trail = FavExt+30 = 28713 on the short K7 (07:54) and exited it at ~08:09 (tape 28715.5); live held it to 08:36, so the line has conditions I do not have.

## 2. Implementation and what it does
ws7 = ws6 + zl2_eval7.evaltrade7 (loss branch unchanged; profit tighten, trail touch, shared gate, 08:05-08:15 take lines) over a new per-print depth stream rebuilt from raw mbp-10 (stream7: identical prints/MedLevel to the ZL-2 stream, plus rel/ahead; 8-tick depth is exactly recoverable from 10 levels). **Tie-out: with profit/take off ws7 reproduces the ws6 r5 trade list exactly (199 rows, 56,720.20).**
**Finding (negative validation, not tuned):** on the 187 live trades the profit-side evaluator fires on **none** of the 4 live exits and on no other trade. With the mbp-10 depth, rel>=2 sustained >=10 s occurs once in the whole week (>=1.5: 18; >=1.3: 52 episodes); in the live K7 window rel peaked 1.4-1.6 at >=+30 pts. At Mon 08:05 ahead_rel was 0.5-1.2 for the X5/M7 shorts (needs >=1.2). The live NT8/Rithmic DOM is thicker/more volatile than the Databento book relative to its own baseline (cold vs warm baseline from the Oct 29-30 files: identical, so the baseline is not the cause). The 8-tick depth ratio cannot be reproduced from mbp-10; the thick-book trigger needs the live DOM log (v1.5 th_eval.csv) or an L2 export.
In the engine r6 one model take fires: X5 Mon 07:20 PolicyTake 08:07:03 (+1,705 vs live +1,765 at 08:05:09). No ThL2Trail.

## 3. Four gates (frozen file; G3 10 s spec / 60 s proposed, unconfirmed)
| run | G1 | G2 | G3 10 s | G3 60 s | G4 | n / net |
|--|--|--|--|--|--|--|
| BASE-6 r5 (reference) | .704 | .477 | .347 | .467 | .418 | 198 / +54.4k |
| **r6 PRIMARY** (profit tighten + 08:05-08:15 take lines, cold baseline) | **.704 F** | **.484 F** | **.347 F** | **.467 F** | **.418 F** | 198 / +53.8k |
| r6 optional windows excluded | .710 | .471 | .352 | .474 | .409 | |
| r6w warm baseline (sensitivity) | identical to r6 | | | | | |
| r7 = r6 + SizeMult lock scaling (code fact, s.4) | .704 | .484 | .347 | .467 | .418 | 198 / +53.8k (no trade changes) |
| r7a = r5 + SizeMult | .704 | .477 | .347 | .467 | .418 | 198 / +54.4k |
| r6o DIAGNOSTIC: live profit exits injected | .716 | .514 | .354 | .474 | .430 | 199 / +50.6k |
| r7o DIAGNOSTIC: injected + SizeMult | .748 | .456 | .374 | .496 | .458 | 208 / +56.6k (live 187 / +104.1k) |
All fail every gate. Evaluator-exact G3 subset (136 live trades, 51 cuts): r6/r7 pairs 114, engine cuts 42, **G3_exact .691 (10 s) / .722 (60 s)**; r7o .764 / .796. Evaluator ceiling with perfect entries unchanged .405 (10 s) / .539 (60 s).
**Census r6 = r5:** engine-only 39 (A1 15, A2 4, **B 12**, C 8); live-only 28 (busy 12, lock-gated 11 [K7 9], gated busy 1, X3 1, no row 3). r7o: engine-only 39, live-only 18 (busy 11, lock-gated 2, busy-gated 1, X3 1, no row 3).

## 4. K7 cascade: two causes, only one was the profit side
(a) Profit side (as asked): live K7/A7 exited ThL2Trail at 21:54:37; the engine exits at target 21:40:46. Note the engine K7 entry fill is 28726.75 vs live 28729.5 (-2.75 pts): the engine target 28786.75 was touched (max print 28788) while the live target 28789.5 was missed by 1.5 pts, so even a perfect trail model must first reproduce the 2.75-pt entry fill difference.
(b) **New, code fact not previously modelled: BookR (DS7.cs 3412) = BaseQty x max(1,SizeMult) x stop x $20, SizeMult = day's largest sizer multiplier (230, 680, 1056, 1158, 1722; dollar caps 3463-3469).** Until Mon 13:30 the ER ladder is x1.5, so K7's Sunday label day has R 3,600 / give-back arm 7,200, not 2,400 / 4,800. The BASE-6 live-path replay shows K7 give-back at Mon 01:12:57 (peak 5,625) that the live did not take; with SizeMult it would not arm. ws6/ws7 never set size_mult (daycaps supports it); r7 sets it (no effect on the engine path alone because the engine K7 peak is higher after its different day, but in r7o it removes 9 of 11 lock gates: K7 18.5k vs live 16.1k, lock-gated 11 -> 2). The two causes together close the K7 cascade; neither alone does.

## 5. Residual by cause (r6; class B and live-only)
- Class B 12 (unchanged): P7 Sun 19:04 (17 lots, -15.6k; no code reason found, rank .99), P7 Tue 02:16, P7 Tue 19:15, U7 Tue 19:20, A7 Tue 19:21/31/37 (Tue 19:15-19:52 4 books silent pre-restart: needs NT8 log), K7 Tue 12:09/13:09/14:12 (K7 day cap), X3 Mon 08:47, X5 Mon 04:20. NtzCheck skips (library flag) cover P7 20:38/20:42, M7 04:51; M7 Mon 11:17 none found.
- Live-only busy 12: A same entry/exit timing only (M7 Mon 08:20 [live PolicyTake 08:05:20 vs engine target 08:31, not reproduced by the depth data], A7 Wed 00:17/00:31, P7 Thu 04:01) 4; B engine entered where live flat (P7 19:04, M7 11:17, X4 02:17/04:35) 4; C cascades from earlier differences (K7 21:42, P7 20:25/22:42, M7 Thu 03:17) 4.
- Live-only lock-gated 11 (K7 9): cause (a)+(b) above.
- Largest dollar gap is not these: P7 engine +28.9k vs live +86.0k.

## 6. Open items
1. Live DOM for the thick-book trigger (v1.5 th_eval.csv or a DOM log) - without it profit-side TH-L2 and the take lines cannot be reproduced. 2. Policy file text for 08:05-08:15 (K7 tighten conditions, operators). 3. Whether SizeMult counting in r7 (taken trades only) matches the live sizer calls (TrendSize runs at L2Arm before several gates). 4. Entry-fill level (2.75 pt on K7 20:09) vs target touch. 5. G3 amendment unconfirmed. 6. NT8 log Tue 19:15-19:52 and optional windows.
Safety: only rebuild7 code, /mnt/l2/l2vast/ds3_base7/, DECISIONS.md/GATE0_ITERATIONS.md/prereg (append), this file. Memory 129 GB free; no processes killed.
