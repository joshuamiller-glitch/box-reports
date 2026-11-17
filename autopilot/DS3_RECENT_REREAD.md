# DS3_RECENT_REREAD - the live questions re-read with the user's standing selection rule (W-RECENT). Updated 2026-11-17 19:25Z

RULE USED: trailing 6 months to the newest session (3 months beside it), refit bi-weekly, validated by rolling the same procedure through history (month-end pick from 2023-09-30, trade the next 1M / 3M, also a 2-week re-pick), same procedure on the existing random controls, older years = tolerant AMBER 15-30% / RED >30% worse than the live setting. NO new engine cells were run; only results that had already landed.
PICK WINDOW END: 2026-10-31. REFIT DATE: 2026-11-22 (bi-weekly). DATA END: 2026-10-31 (last session 2026-10-30; engine months 202304..202610, nothing from 202611). PRIOR-YEAR PERCENTAGES: on every row below (ulcer / max DD / mean, % worse than the reference, rolled OOS series; "not run" where the older months of the candidate sets have not landed).

## Five-line summary
1. Tried: every landed bracket cell (stage 3 grid sets, now 15-43 landed months per candidate set, native raw chassis = reference), the W-ME against-the-day screen (30 configs, 43 months) plus its engine-exact cells (12 months) and engine random controls, a late-entry halving with a ROLLING tercile threshold, and every landed DAY-DONE / resume cell, each picked on the trailing 6M (and 3M) and walked forward month by month.
2. Brackets (Table 1): 13 of 14 cells have a trailing-6M pick that differs from native; 0 pass the user's bar (rolling persistence > 60%, OOS ulcer lower, mean not worse than -25%, beats random picking, not RED): none. The rest stay native (their recent pick does not persist or is worse than a random pick).
3. Same-side loser (Table 4): rolling trailing-6M pick through 2023-10..2026-10 gives OOS ulcer +8.9% (1M hold) / +4.0% (3M window) / +9.4% (3M hold of 6M pick) at mean +136 $/wk vs the live setting and beats random-skip nulls (percentile 0.93); share of months beating live 59% (63% when it switches); trailing-6M pick at the data end = LS_K2_M30. ENGINE-EXACT 12 months disagree (LS_K2_M30 L6M ulcer 9959 vs 9520 vs live): label WEAK-BUT-POSITIVE, needs the engine confirm cells below.
4. DAY-DONE and resume (Table 4): the trailing-6M pick does not beat the live rule going forward (grid: persistence 20%, OOS ulcer -9.9%, mean -720 $/wk; resume cells: 40%, -33.2%, -2445 $/wk): downgrade both W-DD rows to BEST-AVAILABLE-NOT-PROVEN; the L6M gains are 1-4% ulcer, inside noise. Late-entry halving with a rolling threshold is no better than random halving of the same share (6M window), mean cost 12-20%.
5. Next: this page refreshes hourly (loop pid in /mnt/l2/l2vast/_recent/loop.pid) as the stage-3 grid keeps landing older months (prior-year AMBER/RED needs them); the exact engine cells still missing to confirm are listed at the bottom and in /mnt/l2/l2vast/_recent/pending.txt (NOT added to QUEUES.txt: lead decides).

## Verdict changes under the user's rule
| cell | previous verdict | now | why |
|--|--|--|--|
| Table 1 K7 x asia | was BEST-AVAILABLE-NOT-PROVEN (pending) | BEST-AVAILABLE-NOT-PROVEN bracket K7 asia stop=40 target=40 | see tables |
| Table 1 H7 x nyam | was BEST-AVAILABLE-NOT-PROVEN (pending) | BEST-AVAILABLE-NOT-PROVEN bracket H7 nyam stop=60 target=30 | see tables |
| Table 4 same-side loser | WEAK-BUT-POSITIVE (frozen 2023-04..2025-10 pick LS_K2_M30) | WEAK-BUT-POSITIVE rolling persistence 59%, null pct 0.93 (trailing-6M pick LS_K2_M30) | see tables |

## Table 1 - brackets (rolling trailing-window pick among the landed grid sets; reference = native 60/60 raw chassis, $4.84 RT, base lots)
Procedure: at each month-end the pick = lowest trailing-window ulcer among candidate sets whose mean/wk >= native -25%, adopted only when its ulcer is lower than native (adopt-threshold 1.00; the S3 freeze rule needs 10% lower, shown as "pick@10%"); trade the pick the next month. Candidate sets per cell are the 6 priority grid brackets (40/40, 40/60, 60/30, 60/40, 60/90, 90/90) plus native; only months where a set has landed count (landed months per set: 15..43 of 43; the oldest picks need the older months to land).

| cell | trailing-6M pick (3M pick; 12M pick) | pick@10% | window 6M: pick vs native mean $/wk, ulcer | roll 6M/1M: n, switched, OOS ulcer chg, d mean $/wk | persistence strict (among switched) | null pct (random pick) | 3M window / 1M hold | 6M pick / 3M hold | 2-week re-pick | prior years (AMBER 15 / RED 30) | label |
|--|--|--|--|--|--|--|--|--|--|--|--|
| K7 asia | S040T040 (S040T040; S060T030) | S040T040 | 3486 vs 3564; 8891 vs 29319 | n=34 sw 74% ulc +27% d$ -32 | 53% (72%) | 0.97 | n=37 -19% beat 41% | n=11 +11% beat 45% | n=73 +33% beat 48% | 2024: ulc -6% dd +1% mean +1% -> ok (n=12); 2025: ulc -16% dd -33% mean +14% -> ok (n=12) (worse-than-ref %; 1 | BEST-AVAILABLE-NOT-PROVEN |
| K7 london | S040T060 (NATIVE; S040T060) | S040T060 | -121 vs -1297; 28799 vs 42276 | n=34 sw 74% ulc +10% d$ +174 | 35% (48%) | 0.74 | n=37 +14% beat 27% | n=11 -41% beat 18% | n=73 -15% beat 33% | 2024: ulc +70% dd +109% mean +11% -> RED (n=12); 2025: ulc -26% dd +4% mean +2% -> ok (n=12) (worse-than-ref % | RED (not delivered as a pick) |
| K7 nyam | S040T040 (S040T040; S060T090) | S040T040 | 160 vs -988; 5376 vs 24789 | n=34 sw 74% ulc +10% d$ +37 | 44% (60%) | 0.71 | n=37 -18% beat 35% | n=11 +7% beat 27% | n=73 +6% beat 45% | 2024: ulc +41% dd +25% mean +22% -> RED (n=12); 2025: ulc -17% dd -6% mean +38% -> RED (n=12) (worse-than-ref  | RED (not delivered as a pick) |
| K7 nypm | S060T040 (S060T040; S060T090) | S060T040 | 1623 vs 1223; 8215 vs 14047 | n=34 sw 68% ulc -47% d$ -591 | 26% (39%) | 0.69 | n=37 -41% beat 27% | n=11 -61% beat 27% | n=73 -50% beat 30% | 2024: ulc +34% dd +10% mean +62% -> RED (n=12); 2025: ulc -21% dd -19% mean -65% -> ok (n=12) (worse-than-ref  | RED (not delivered as a pick) |
| M7 london | S060T030 (NATIVE; S040T040) | S060T030 | -302 vs -888; 24433 vs 34324 | n=37 sw 73% ulc +35% d$ -87 | 41% (56%) | 0.80 | n=37 +50% beat 46% | n=12 +24% beat 25% | n=80 +10% beat 39% | 2023: ulc +0% dd +0% mean -0% -> ok (n=3); 2024: ulc -61% dd -55% mean -64% -> ok (n=12); 2025: ulc +23% dd +9 | native stays (pick does not persist) |
| M7 nyam | S060T030 (S040T060; NATIVE) | S060T030 | 418 vs 256; 6432 vs 9117 | n=37 sw 54% ulc -22% d$ -265 | 24% (45%) | 0.75 | n=37 -54% beat 35% | n=12 -33% beat 25% | n=80 -46% beat 24% | 2023: ulc -11% dd -9% mean +57% -> ok (n=3); 2024: ulc +89% dd +63% mean +79% -> RED (n=12); 2025: ulc -1% dd  | RED (not delivered as a pick) |
| P7 asia | S040T060 (NATIVE; NATIVE) | NATIVE | 15983 vs 17177; 36011 vs 38203 | n=35 sw 89% ulc -4% d$ -1272 | 49% (55%) | 0.56 | n=37 -11% beat 49% | n=11 +24% beat 55% | n=75 +17% beat 45% | 2024: ulc -55% dd -51% mean -17% -> ok (n=12); 2025: ulc +38% dd -4% mean +46% -> RED (n=12) (worse-than-ref % | RED (not delivered as a pick) |
| P7 london | S040T060 (S040T040; S040T060) | S040T060 | 2949 vs 2743; 27088 vs 34010 | n=35 sw 80% ulc -110% d$ -1198 | 31% (39%) | 0.08 | n=37 -7% beat 30% | n=11 -114% beat 18% | n=75 -27% beat 37% | 2024: ulc +15% dd +17% mean +1% -> AMBER (n=12); 2025: ulc +52% dd +40% mean +618% -> RED (n=12) (worse-than-r | RED (not delivered as a pick) |
| P7 nyam | NATIVE (NATIVE; NATIVE) | NATIVE | -331 vs -331; 54765 vs 54765 | n=35 sw 71% ulc +18% d$ -410 | 29% (40%) | 0.98 | n=37 -4% beat 38% | n=11 +26% beat 18% | n=75 +21% beat 39% | 2024: ulc +12% dd +19% mean +87% -> RED (n=12); 2025: ulc -27% dd -24% mean -103% -> ok (n=12) (worse-than-ref | native stays |
| U7 asia | S040T040 (S040T040; S040T040) | S040T040 | 3667 vs 2665; 4738 vs 10877 | n=37 sw 81% ulc +11% d$ -188 | 62% (77%) | 0.92 | n=37 +16% beat 57% | n=12 -2% beat 33% | n=80 +20% beat 55% | 2023: ulc -8% dd -10% mean -204% -> ok (n=3); 2024: ulc -1% dd -14% mean +70% -> RED (n=12); 2025: ulc +9% dd  | RED (not delivered as a pick) |
| U7 london | S040T060 (S040T060; S040T040) | S040T060 | 1055 vs -633; 11518 vs 13121 | n=37 sw 68% ulc -155% d$ -511 | 41% (60%) | 0.17 | n=37 -24% beat 46% | n=12 -185% beat 25% | n=80 -116% beat 35% | 2023: ulc +0% dd +0% mean -0% -> ok (n=3); 2024: ulc -15% dd -9% mean +112% -> RED (n=12); 2025: ulc +120% dd  | RED (not delivered as a pick) |
| H7 asia | S060T030 (S060T030; S040T060) | S060T030 | 2105 vs 1552; 13792 vs 21822 | n=37 sw 92% ulc -74% d$ -856 | 62% (68%) | 0.07 | n=37 -31% beat 54% | n=12 -31% beat 42% | n=80 -26% beat 51% | 2023: ulc -23% dd -13% mean +82% -> RED (n=3); 2024: ulc +7% dd -5% mean +22% -> AMBER (n=12); 2025: ulc +10%  | RED (not delivered as a pick) |
| H7 nyam | S060T030 (S060T030; S060T030) | S060T030 | 505 vs 567; 950 vs 1787 | n=37 sw 86% ulc -53% d$ -71 | 51% (59%) | 0.25 | n=37 -93% beat 35% | n=12 -14% beat 58% | n=80 -27% beat 39% | 2023: ulc +15% dd +12% mean -79% -> AMBER (n=3); 2024: ulc +14% dd +24% mean +8% -> AMBER (n=12); 2025: ulc -7 | BEST-AVAILABLE-NOT-PROVEN |
| A7 asia | S040T060 (S040T060; S060T030) | S040T060 | 1371 vs 648; 2748 vs 4910 | n=37 sw 86% ulc +7% d$ -26 | 73% (84%) | 0.89 | n=37 +29% beat 86% | n=12 +16% beat 92% | n=80 +9% beat 62% | 2023: ulc -52% dd -45% mean -506% -> ok (n=3); 2024: ulc -23% dd -11% mean +5% -> ok (n=12); 2025: ulc +6% dd  | RED (not delivered as a pick) |

Decay (mean $/wk difference of the 6M pick vs native, 1..6 months after the pick; share of months with higher net in brackets):
- K7 asia: +1M -47 (35%, n=34), +2M -534 (30%, n=33), +3M -860 (31%, n=32), +4M +78 (42%, n=31), +5M -401 (30%, n=30), +6M -516 (28%, n=29)
- K7 london: +1M +186 (32%, n=34), +2M -68 (33%, n=33), +3M -347 (28%, n=32), +4M -348 (23%, n=31), +5M -530 (30%, n=30), +6M -639 (24%, n=29)
- K7 nyam: +1M +35 (38%, n=34), +2M +153 (39%, n=33), +3M +37 (31%, n=32), +4M +45 (29%, n=31), +5M +14 (33%, n=30), +6M +44 (38%, n=29)
- K7 nypm: +1M -598 (18%, n=34), +2M -955 (18%, n=33), +3M -825 (22%, n=32), +4M -763 (23%, n=31), +5M -311 (23%, n=30), +6M -711 (21%, n=29)
- M7 london: +1M -100 (32%, n=37), +2M -308 (25%, n=36), +3M -491 (31%, n=35), +4M -143 (35%, n=34), +5M -223 (36%, n=33), +6M -494 (31%, n=32)
- M7 nyam: +1M -267 (16%, n=37), +2M -278 (11%, n=36), +3M -153 (20%, n=35), +4M -211 (21%, n=34), +5M -384 (12%, n=33), +6M -295 (19%, n=32)
- P7 asia: +1M -1278 (37%, n=35), +2M -1039 (38%, n=34), +3M -511 (45%, n=33), +4M +578 (50%, n=32), +5M -1634 (39%, n=31), +6M -1711 (40%, n=30)
- P7 london: +1M -1186 (26%, n=35), +2M -322 (32%, n=34), +3M -550 (33%, n=33), +4M +527 (44%, n=32), +5M +943 (45%, n=31), +6M +340 (40%, n=30)
- P7 nyam: +1M -408 (26%, n=35), +2M -476 (26%, n=34), +3M -165 (30%, n=33), +4M -502 (28%, n=32), +5M +461 (39%, n=31), +6M +237 (27%, n=30)
- U7 asia: +1M -188 (41%, n=37), +2M +328 (50%, n=36), +3M -268 (43%, n=35), +4M +52 (41%, n=34), +5M -162 (42%, n=33), +6M -426 (28%, n=32)
- U7 london: +1M -503 (24%, n=37), +2M -608 (22%, n=36), +3M -279 (23%, n=35), +4M -273 (24%, n=34), +5M +18 (27%, n=33), +6M +63 (25%, n=32)
- H7 asia: +1M -867 (38%, n=37), +2M -467 (39%, n=36), +3M -904 (34%, n=35), +4M -424 (50%, n=34), +5M -535 (42%, n=33), +6M +231 (53%, n=32)
- H7 nyam: +1M -71 (38%, n=37), +2M -69 (31%, n=36), +3M -51 (40%, n=35), +4M -18 (41%, n=34), +5M -54 (45%, n=33), +6M -8 (41%, n=32)
- A7 asia: +1M -23 (46%, n=37), +2M -114 (42%, n=36), +3M -94 (43%, n=35), +4M +102 (50%, n=34), +5M -101 (39%, n=33), +6M -201 (34%, n=32)

Bookkeeping: trials = 6 settings per cell x 14 cells + the S3 grid (497 sets) already counted in the W-S3 ledger (RB3); no multiple-comparison correction here: the random-pick null (500 draws of a random eligible set per month, same months) is the control; engine-exact random-bracket controls (S3J) have not landed, so nothing here is CONFIRMED.

## Table 4 - behaviour rules
### Same-side loser and the other W-ME screen configs (path arithmetic on JL3, 43 months; $4.84; ref = live JL3)
| family / procedure | n periods | switched | OOS ulcer chg | d mean $/wk | months beating live | beating when switched |
|--|--|--|--|--|--|--|
| LSLH 6M window, 1M hold | 37 | 95% | +8.9% | +136 | 59% | 63% |
| LSLH 3M window, 1M hold | 37 | 97% | +4.0% | +6 | 62% | 64% |
| LSLH 12M window, 1M hold | 31 | 97% | +13.1% | +6 | 65% | 67% |
| LSLH 6M window, 3M hold | 12 | 92% | +9.4% | -80 | 75% | 82% |
| LSLH 6M window, 2-week re-pick | 80 | 96% | +8.8% | +104 | 44% | 45% |
| LSLH 3M window, 2-week re-pick | 80 | 99% | +5.8% | +34 | 45% | 46% |
| ALL30 6M window, 1M hold | 37 | 95% | +12.0% | +250 | 57% | 60% |
| ALL30 3M window, 1M hold | 37 | 100% | +6.5% | +54 | 57% | 57% |
| ALL30 12M window, 1M hold | 31 | 100% | +14.2% | +26 | 61% | 61% |
| ALL30 6M window, 3M hold | 12 | 92% | +5.8% | -117 | 58% | 64% |
| ALL30 6M window, 2-week re-pick | 80 | 96% | +12.0% | +240 | 44% | 45% |
| ALL30 3M window, 2-week re-pick | 80 | 100% | +7.9% | +115 | 40% | 40% |
| VOTE(H/S/P) 6M window, 1M hold | 37 | 76% | -2.2% | -8 | 14% | 18% |
| VOTE(H/S/P) 3M window, 1M hold | 37 | 86% | +2.1% | +20 | 16% | 19% |
| VOTE(H/S/P) 12M window, 1M hold | 31 | 87% | -0.6% | +216 | 23% | 26% |
| VOTE(H/S/P) 6M window, 3M hold | 12 | 67% | -2.8% | -49 | 25% | 38% |
| VOTE(H/S/P) 6M window, 2-week re-pick | 80 | 76% | -4.3% | -93 | 9% | 11% |
| VOTE(H/S/P) 3M window, 2-week re-pick | 80 | 82% | -2.0% | -6 | 12% | 15% |

Null (same procedure on persistent random-skip / random-half controls with the same per-session share, 30 draws; adopt threshold 1.00): LSLH 6M1: ulcer chg mean -0.4% (5-95%: -8.7..+9.3), months beating 51%; LSLH 3M1: ulcer chg mean +0.6% (5-95%: -7.6..+11.0), months beating 51%; LSLH 6M3: ulcer chg mean -0.4% (5-95%: -6.3..+6.3), months beating 56%; LSLH 6M2W: ulcer chg mean -0.5% (5-95%: -7.7..+8.3), months beating 45%

Prior years (rolled OOS, LS/LH, 6M window, 1M hold): not run (older months not landed for the candidate sets)

Decay (LS/LH picks, 6M window): +1M +140 $/wk (49% months higher, n=37), +2M -52 $/wk (50% months higher, n=36), +3M +19 $/wk (57% months higher, n=35), +4M +11 $/wk (56% months higher, n=34), +5M -50 $/wk (55% months higher, n=33), +6M -59 $/wk (59% months higher, n=32). A pick is worth most in the first month: this supports the bi-weekly refit.

Trailing-6M and 3M window to the data end (ref mean $/wk, ulcer, max DD): live 19686 / 9520 / 31112; LH_K2 19442 / 9651 / 32797; LS_K2_M30 19886 / 9123 / 29229; LS_K2_M60 17837 / 10246 / 34791; LS_K2_M120 17667 / 10055 / 35337; LH_K3 19463 / 9552 / 31443; LS_K3_M30 19216 / 9567 / 30594; LS_K3_M60 18136 / 10719 / 35261; LS_K3_M120 17559 / 11702 / 38478; LH_K4 19699 / 9629 / 32002; LS_K4_M30 19948 / 9420 / 30561; LS_K4_M60 19471 / 9879 / 35011; LS_K4_M120 19341 / 10242 / 38449. Pick@10%: REF; adopt-threshold 1.00: LS_K2_M30 (6M) / LS_K2_M30 (3M).

### Engine-exact ME cells (12 months 202511..202610, JL3; 5-9 OOS months only)
| candidate set | procedure | n | switched | OOS ulcer chg | d mean $/wk | months beating live |
|--|--|--|--|--|--|--|
| LSLH4 6M1 | 5 | 80% | -5.5% | +793 | 40% | 50% |
| LSLH4 3M1 | 9 | 100% | -12.9% | -1625 | 56% | 56% |
| LSLH4 6M2W | 12 | 83% | -8.8% | -682 | 25% | 30% |
| LSLH 6M1 | 5 | 80% | -8.3% | +122 | 40% | 50% |
| LSLH 3M1 | 9 | 100% | -16.6% | -1790 | 33% | 33% |
| LSLH 6M2W | 12 | 83% | -12.5% | -598 | 17% | 20% |
| EXT_SZ 6M1 | 5 | 100% | +8.2% | -3026 | 60% | 60% |
| EXT_SZ 3M1 | 9 | 78% | +4.3% | -2134 | 44% | 57% |
| EXT_SZ 6M2W | 12 | 92% | +8.0% | -2716 | 50% | 55% |
| EXT_CUT 6M1 | 5 | 100% | -12.7% | -2380 | 20% | 20% |
| EXT_CUT 3M1 | 9 | 100% | +9.9% | -2523 | 44% | 44% |
| EXT_CUT 6M2W | 12 | 100% | -8.0% | -2751 | 42% | 42% |
| ALLENG 6M1 | 5 | 100% | -14.7% | -1797 | 20% | 20% |
| ALLENG 3M1 | 9 | 100% | +10.1% | -2411 | 44% | 44% |
| ALLENG 6M2W | 12 | 100% | -10.3% | -1649 | 33% | 33% |

Engine-exact persistent random controls (34 draws x {LS_K2_M30, LS_K2_M120, LH_K2, LH_K3}; same rolling procedure): 6M1: OOS ulcer chg mean -4.1% (5-95%: -18.6..+6.2), months beating 40%, switched 87%; 3M1: OOS ulcer chg mean -2.6% (5-95%: -16.6..+12.7), months beating 44%, switched 89%; 6M2W: OOS ulcer chg mean -5.0% (5-95%: -25.1..+7.3), months beating 33%, switched 86%. Engine-exact trailing-6M window (live 19686 / 9520 / 31112): LS_K2_M30 19205 / 9959 / 36615; LS_K2_M120 17289 / 12212 / 47779; LH_K2 19891 / 10116 / 35874; LH_K3 19694 / 9477 / 31486.

### Late-entry (extended-entry) size halving with a ROLLING tercile threshold (path arithmetic, 6 features; threshold from the trailing window, not frozen on 2023-25)
| procedure | n | switched | OOS ulcer chg | d mean $/wk (mean chg) | months beating live | null (random halving of same share, 20 draws) ulcer chg mean (5-95%) / beating | real percentile |
|--|--|--|--|--|--|--|--|
| 6M window, 1M hold | 37 | 100% | +7.4% | -1707 (-20%) | 81% | +8.3% (+5.1..+12.5) / 71% | 0.45 |
| 3M window, 1M hold | 37 | 100% | +15.5% | -1344 (-16%) | 73% | +7.2% (+3.4..+11.4) / 72% | 1.00 |
| 6M window, 2-week | 80 | 100% | +15.0% | -1507 (-17%) | 66% | +7.7% (+2.9..+12.5) / 72% | 1.00 |

Reading: halving the entries that are most extended gives a lower ulcer but it costs 12-20%% of the mean and is not clearly better than halving the same share at random; stays BEST-AVAILABLE-NOT-PROVEN (no row change). Same-side-stack-after-cut (CUT_half/CUT_tight): engine-exact cells only (12 months), rolled together with the other engine cells above; no pick survives.

### DAY-DONE settings and conditional resume (engine cells on JL3, landed months only; ref = live rule TL3_EV_JL3)
| candidate set | procedure | n | switched | OOS ulcer chg | d mean $/wk | months beating live | beating when switched |
|--|--|--|--|--|--|--|--|
| GRID+C 6M1 | 15 | 67% | -9.9% | -720 | 20% | 30% |
| GRID+C 3M1 | 20 | 70% | -8.5% | -302 | 20% | 29% |
| GRID+C 12M1 | 4 | 0% | +0.0% | +0 | 0% | - |
| GRID+C 6M3 | 4 | 50% | -9.9% | -449 | 0% | 0% |
| GRID+C 6M2W | 33 | 70% | -10.0% | -479 | 21% | 30% |
| VARIANTS 6M1 | 5 | 100% | -12.8% | -1468 | 20% | 20% |
| VARIANTS 3M1 | 9 | 78% | -2.0% | -93 | 33% | 43% |
| VARIANTS 6M3 | 1 | 100% | -29.3% | -1292 | 0% | 0% |
| VARIANTS 6M2W | 12 | 92% | -3.4% | -1058 | 33% | 36% |
| RESUME 6M1 | 5 | 100% | -33.2% | -2445 | 40% | 40% |
| RESUME 3M1 | 9 | 100% | +2.4% | -547 | 44% | 44% |
| RESUME 6M3 | 1 | 100% | -51.5% | -3030 | 0% | 0% |
| RESUME 6M2W | 12 | 100% | -36.4% | -2256 | 17% | 17% |
| WITH_OFF 6M1 | 37 | 62% | -3.6% | -519 | 30% | 48% |
| WITH_OFF 3M1 | 37 | 65% | -4.5% | -486 | 27% | 42% |
| WITH_OFF 12M1 | 31 | 35% | -3.7% | -273 | 19% | 55% |
| WITH_OFF 6M3 | 12 | 58% | -5.3% | -552 | 17% | 29% |
| WITH_OFF 6M2W | 80 | 65% | -5.5% | -508 | 19% | 29% |

Random-pick null (a random landed cell per month): GRID+C: OOS ulcer chg mean -12.0% (5-95%: -14.2..-10.6); VARIANTS: OOS ulcer chg mean -8.3% (5-95%: -25.2..+3.4); WITH_OFF: OOS ulcer chg mean -2.3% (5-95%: -2.9..-1.9). A real rolling pick that is less bad than the random pick but worse than the live rule = the live rule is already the best of the landed set.
- GRID+C, trailing windows to the data end: live (mean/ulcer/maxDD) 19686 / 9520 / 31112 (6M), 16099 / 11275 / 31112 (3M); best three by ulcer (6M): G_22_3000 9365/19722, G_22_6000 9664/19573, G_26_6000 9685/18583; pick (adopt 1.00) 6M G_22_3000, 3M G_22_3000.
- RESUME, trailing windows to the data end: live (mean/ulcer/maxDD) 19686 / 9520 / 31112 (6M), 16099 / 11275 / 31112 (3M); best three by ulcer (6M): R3_2000 9266/19517, R3_3000 9266/19517, R3_1000 9328/19602; pick (adopt 1.00) 6M R3_2000, 3M R3_2000.
- landed months per DD cell (of 43): ; resume cells R*: 12 each.

## Engine cells still missing to confirm (queue file /mnt/l2/l2vast/_recent/pending.txt, NOT in QUEUES.txt: lead decides)
60 cells missing for the picks above (29 already sit in s3_pending.txt / s3_first.txt / the W-ME pending file, so they are NOT repeated; 31 are new and written to pending.txt, recent months first). dead_lookup: specs exit|bracket|<book>|<session>|stop=|target=, skip|same_side_loser, dayhalt|stack all returned (False, []) = not dead, no similar dead cell (checked 2026-11-17). Set JSONs checked to exist in exact/sets/ before listing.

Cells already in the stage 3 queue that matter most (ask the lead to move them to the front of s3_pending): H7_S060T030, K7_S040T040 for the months 202409..202508 first (prior-year check), then 202304..202408.

## What this does NOT settle
- Brackets are one-book-alone raw-chassis cells; the exact JL3 assembly and the 30 random-bracket engine controls (S3J) are not landed, so nothing in Table 1 is CONFIRMED. Prior-year AMBER/RED is only as good as the landed older months (see coverage). "Native" is the raw-chassis 60/60, not the live THP line.
- ME and DD pick cells are screen/engine on the same JL3 trade list; freed-book effects are included for engine cells, not for the screen.
- Adopt-threshold: at 10% (the S3 freeze rule) most cells keep native; at 0% (the user's literal "best on the trailing 6M") picks switch almost every month. Both are in the pickles (_t100 = adopt-at-any-gain).

Scripts: code/th_recent/ (rr_lib, rr_brk, rr_me, rr_dd, rr_report, run_all.sh, rr_loop.sh). Prereg line: DECISIONS.md 2026-11-17T19:05Z W-RECENT.
