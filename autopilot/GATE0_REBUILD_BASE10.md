# GATE0_REBUILD_BASE10 - PRE-PROOF, post-hoc, frozen live file only. NO PASS CLAIM. Gate 0 NOT passed. No gate0 JSON promoted, A-G not launched, opposite-touch fill NOT promoted, r3b rejected, config as it was live (Tue 02:55-08:20 ET excluded).
Code: DS7.cs sha 54697597... (verified); frozen file sha 424c68da... (verified); audit QA_ENGINE_REBUILD.md. New private copies l2vast/ds3/code/blind/rebuild11/ {ws11.py 3cebeb5c (mk_ws11.py from rebuild10/ws10.py), fillsim11.py efd43fe5, zl2_eval11.py f938555d, exact11.py b7cd7807}; originals untouched. Bulk /mnt/l2/l2vast/ds3_base11/. Prereg l2vast/ds3/prereg/GATE0_REBUILD11_prereg.md sha 460c06c1... logged in DECISIONS.md BEFORE scoring. Tooling regression: all fix flags off = r9 trade for trade (197 rows, +49,856). Seal: manifest_after.json sha 759f2258... unchanged; 18,638 files re-hashed start and end: 0 missing/0 changed/0 new; only read-only access to ds3_g2_blind SS/SC (as r8-r10) and tape tables.

## 1. Code facts (what was implemented)
- M1 stop modes: DS7.cs 570-583 gives K7, M7, U7, P7 one shared StStopExitMode (JoinThenMarket, 485); HmStopExitMode feeds only N7 (`hm`); H7 (h6) and A7 (a6) never assigned = enum default Native (P9_NT8_SPEC: default Native); O7 (568) and X (558) explicit Native. Join books: 3-s join then market + catastrophe 20; Native books: stop-market at StopPx, NO catastrophe (NativeStopPx 2780). Engine: JOIN_BOOKS K7,M7,U7,P7. Note: contradicts GATE0_ANSWERS s3 text (K7,H7 join; M7/U7/P7 Native) and fits the live M7 `_Stop` at +80.75.
- M6 cut basis: EntryPx, AdvExt/AdvExtTime, FavExt reset at every fill (3050-3053); evaluator (evaltrade11) applies the fill schedule print by print, no later fill or final average used. ResetTh clears PolicyLastEval (so the pol_t0 hard block is replaced by the per-fill reset); ThL2LastEval/trail/thick not reset (code).
- M2: policy stopDist = |running avg - ArmStopPx| on L2-gated books (ArmStopPx = signal -/+ 60).
- M3 add disarm: add cannot fire at/after the first minute with a time block or session lots 0 (L2Pump 1498-1499; rollover is inside the 15:00-18:04 block). Opposite-signal disarm not applicable in trade (TryEntry returns on InTrade).
- M5: U7 (BIP3) NTZ/OTE-62 line state after the 15-min BIP2 bar of the same timestamp (AddDataSeries 499-501); K7 (BIP1) and BIP0 books before.
- M8: lock/cap accounting deducts 4.84 $/contract RT (FEES.md NQ standard; the live commission schedule is not in the code - assumption); reported P&L unchanged.
- M10 CHECKED: secBip45 = 8 (504-508) is later than BIP0, so the 45-s bar closing at the signal second is processed after CfHold and evaluated (CfOnSubBar 1670-1700); implemented (bar END >= signal second). Depends on NT8's same-timestamp BIP order (not in the code file). No effect in the blind week (no tie among its 2 held P7 rows).
- M4 (confirmation proxy) not touched (not a code-fact fix).

## 2. Four gates (frozen file; G3 both ways)
| run | G1 | G2 | G3 10 s | G3 60 s | G4 | n / net |
|--|--|--|--|--|--|--|
| r9 (reference) = ws11 all-off | .717 F | .521 F | .349 F | .470 F | .269 F | 196 / +49.9k |
| **r11 PRIMARY** | **.707 F** | **.530 F** | **.347 F** | **.456 F** | **.274 F** | 197 / +48.9k |
| r11 minus M1 / M3 / M5 / M10 | = r11 (no effect in this week: 0 stop exits, no add crosses a block, no 15-min tie entry, no confirm tie) | | | | | |
| r11 minus M2 | .717 | .515 | .349 | .470 | .264 | 196 / +50.5k |
| r11 minus M6 | .707 | .533 | .347 | .456 | .278 | 197 / +48.6k |
| r11 minus M8 | .707 | .539 | .347 | .456 | .274 | 197 / +47.9k |
All fail every gate (live 187 / +104,095). Ablations are descriptive, nothing selected. M2 is the only fix that moves the numbers materially: exit types 104 ThL2Cut/1 PolicyCut -> 99/7 (the policy line pct<=-0.5 now uses a stopDist below 60 when the fill is worse than the signal price); M8 changes lock timing (P7 +945 net).

## 3. Census (r11) and net-gap decomposition
Engine-only 38 (A1 20, A2 4, B 9, C 5; net +0.4k). Live-only 28 (busy 13, lock-gated 10 [K7 9, P7 1], gated busy 1, X3 1, norow 3). Matched pairs 159.
Live 104,095 - engine 48,893 = **55,202** = (a) live-only +16,735 (28) + (b) engine-only -408 (38) + (c) matched pairs +38,875 = size -3,540, entry -4,332, **exit +49,140**, live-row residual -2,394. (r9: 54,239 = +15,535 / -1,427 / +40,131; exit +50,396.)
By book gap: P7 +59,179 (pairs exit +50.8k), K7 +3,960, A7 -5,430, U7 -7,350, M7 +356, H7/O7/X +4.6k. Top cause unchanged: engine ThL2Cut where live ran to target on matched trades (P7 pairs exit +50.8k vs +51.8k in r9); the fixes shrink the exit part by 1.3k only.

## 4. Conclusion / open
The seven code-fact fixes are faithful but do not touch the dominant gap (cut-vs-target flips from the data-side DOM reconstruction, QA s2 item 1). Next week stops will occur, where M1 matters (join vs native, catastrophe). Open: live 8-way add confirmation (M4), th_eval.csv from v1.5, live commission schedule for M8, NT8 same-timestamp BIP order for M10, opposite-touch fill question (not promoted).
