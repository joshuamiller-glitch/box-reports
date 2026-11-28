# DESK_COVERAGE (generated 2026-11-28 15:18Z by code/th_algo/ar_coverage.py; order 1438Z; research only)

FAMILY STATUS: A STOP: RUNNING (10 designs, 2 done, 2 running, 6 queued); B PROFIT: RUNNING (12 designs, 4 done, 4 running, 4 queued); C LOSS: RUNNING (6 designs, 3 done, 1 running, 2 queued); D ADDS: QUEUED (2 designs, 0 done, 0 running, 2 queued); E RE-ENTRY: QUEUED (2 designs, 0 done, 0 running, 2 queued); F CONTEXT: RUNNING (6 designs, 0 done, 2 running, 4 queued); G DESK LEVEL: RUNNING (5 designs, 1 done, 0 running, 4 queued); H JOINT STAGE: QUEUED until the top 3 per family exist (see below). Status per design is read from runs_rf: done = every window month DONE for every book of that session (Asia / London 37 months, NY AM / NY PM 24 months), running = some sets exist, queued = none. Per session counts shown as books complete / books.

Results live in DESK_DESIGNS_COMPARED.md (one table, all designs, same windows, like with like, give-back columns) and DESK_JUDGE.md (best design per book, walk-forward on the trailing 12 months). New-design tags are guessed as DK<id> / DK<id>MAIN (DKA1.., DKB1.., DKG1..): tell me if the sets are named differently. Note: G (desk-level) designs act on books together; if they come as whole-mix sets they enter the table as _M rows only. The v0.16-v0.18 definitions are not in PLAYBOOK.md yet (not registered until they are).

## A. STOP FAMILY: RUNNING

| design id | one-line rule | status | where the result is |
|---|---|---|---|
| v0.4 ratchet-only | ratchet-only: own stop, no target; stop to entry at 2 units, never give back half a peak of 2+ units, structure trail, 0.9 rule | done (NY AM 4/4, Asia 3/3, London 2/2, NY PM 2/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "v0.4 ratchet-only"); judge: DESK_JUDGE.md |
| v0.4-ceiling (own target as ceiling) | v0.4 with the book's own target kept as a ceiling | done (NY AM 4/4, Asia 3/3, London 2/2, NY PM 2/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "v0.4-ceiling (own target as ceiling)"); judge: DESK_JUDGE.md |
| v0.10 (level-anchored stop) | level-anchored stop | running (NY AM 0/4, Asia 1/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "v0.10 (level-anchored stop)"); judge: DESK_JUDGE.md |
| A1 volatility stop at entry (2 x s5, same lots-risk, own target; compare in $ and DD, lots differ); post-result change 22 | A1 volatility stop at entry (2 x s5, same lots-risk, own target; compare in $ and DD, lots differ); post-result change 22 | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "A1 volatility stop at entry (2 x s5, same lots-risk, own target; compare in $ and DD, lots differ); post-result change 22"); judge: DESK_JUDGE.md |
| A2 structure stop at entry (capped at own stop, own lots); post-result change 23 | A2 structure stop at entry (capped at own stop, own lots); post-result change 23 | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "A2 structure stop at entry (capped at own stop, own lots); post-result change 23"); judge: DESK_JUDGE.md |
| A3 chandelier trail (3 x ATR5, no target); post-result change 24 | A3 chandelier trail (3 x ATR5, no target); post-result change 24 | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "A3 chandelier trail (3 x ATR5, no target); post-result change 24"); judge: DESK_JUDGE.md |
| A4 EMA21 trail once up 1 unit (no target); post-result change 25 | A4 EMA21 trail once up 1 unit (no target); post-result change 25 | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "A4 EMA21 trail once up 1 unit (no target); post-result change 25"); judge: DESK_JUDGE.md |
| A5 parabolic-SAR trail (no target); post-result change 26 | A5 parabolic-SAR trail (no target); post-result change 26 | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "A5 parabolic-SAR trail (no target); post-result change 26"); judge: DESK_JUDGE.md |
| v0.16 (the screens set the leash; post-result change 19) | v0.16 (the screens set the leash; post-result change 19) | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "v0.16 (the screens set the leash; post-result change 19)"); judge: DESK_JUDGE.md |
| REPL / qualifier books (QAS / QLO / QNP / QNY) | replacement / qualifier books on the same stop families (ls codes on _A rows) | running (queued sets exist in runs_rf) | autopilot/BOOK_SPECS_REPLACEMENT.md |

## B. PROFIT FAMILY: RUNNING

| design id | one-line rule | status | where the result is |
|---|---|---|---|
| v0.5 bank half, run half | bank half at the book target, run the other half on the ratchet | done (NY AM 4/4, Asia 3/3, London 2/2, NY PM 2/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "v0.5 bank half, run half"); judge: DESK_JUDGE.md |
| v0.7 bracket + near-target guard (pl70k50) | bracket + near-target guard: past 70% of the target the stop keeps 50% of the peak (pl70k50) | done (NY AM 4/4, Asia 3/3, London 2/2, NY PM 2/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "v0.7 bracket + near-target guard (pl70k50)"); judge: DESK_JUDGE.md |
| v0.8 (scale out in thirds) | scale out in thirds | running (NY AM 0/4, Asia 1/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "v0.8 (scale out in thirds)"); judge: DESK_JUDGE.md |
| v0.9 (volatility-sized give-back) | volatility-sized give-back | running (NY AM 0/4, Asia 1/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "v0.9 (volatility-sized give-back)"); judge: DESK_JUDGE.md |
| v0.12 (momentum roll-over) | momentum roll-over | running (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "v0.12 (momentum roll-over)"); judge: DESK_JUDGE.md |
| v0.15 (per-book winner profile) | per-book winner profile | running (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "v0.15 (per-book winner profile)"); judge: DESK_JUDGE.md |
| B1 R-multiple ladder (thirds at 1R/2R, ratchet runner); post-result change 27 | B1 R-multiple ladder (thirds at 1R/2R, ratchet runner); post-result change 27 | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "B1 R-multiple ladder (thirds at 1R/2R, ratchet runner); post-result change 27"); judge: DESK_JUDGE.md |
| B2 exhaustion take (RSI14 80/20 turn, half); post-result change 28 | B2 exhaustion take (RSI14 80/20 turn, half); post-result change 28 | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "B2 exhaustion take (RSI14 80/20 turn, half); post-result change 28"); judge: DESK_JUDGE.md |
| B3 VWAP-band take (+/-2 sd, half); post-result change 29 | B3 VWAP-band take (+/-2 sd, half); post-result change 29 | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "B3 VWAP-band take (+/-2 sd, half); post-result change 29"); judge: DESK_JUDGE.md |
| v0.18 (slow divergence at the highs; post-result change 21) | v0.18 (slow divergence at the highs; post-result change 21) | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "v0.18 (slow divergence at the highs; post-result change 21)"); judge: DESK_JUDGE.md |
| landscape codes (so0, gKKaAA, trCC, xi*, rg*, lv*, x7, l7, cbA) | no fixed target, own stop; give-back caps / trails / cross-instrument / range / level exits, whole-mix deltas | done (42 months, in-mix _M rows) | autopilot/SUNDAY_LANDSCAPE.md; best code per book also a row in DESK_DESIGNS_COMPARED.md |
| protection panel BE70 / PL / NT keys | break-even at 70% of target, peak-lock, near-target keys on the live books | done (Sunday rows) | autopilot/EXIT_MGMT_SUNDAY.md, EXIT_MGMT_KEYS.md (row-level location to be confirmed with W-DYNH) |

## C. LOSS FAMILY: RUNNING

| design id | one-line rule | status | where the result is |
|---|---|---|---|
| v0.3 (DK3 main) | book keeps its own target and own stop; desk only manages the loss side (DEFEND half, ABORT), never-bend 0.9 rule and the clock | done (NY AM 4/4, Asia 3/3, London 2/2, NY PM 2/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "v0.3 (DK3 main)"); judge: DESK_JUDGE.md; also DESK_V03_SCORECARD.md / DESK_DK3MAIN_ATTRIBUTION.md |
| v0.6 ratchet + ABORT | v0.4 ratchet + ABORT only | done (NY AM 4/4, Asia 3/3, London 2/2, NY PM 2/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "v0.6 ratchet + ABORT"); judge: DESK_JUDGE.md |
| v0.13 (tape-led defence (Asia, London only)) | tape-led defence (Asia, London only) | running (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "v0.13 (tape-led defence (Asia, London only))"); judge: DESK_JUDGE.md |
| C1 halve-and-hold (cut half at -50% of stop); post-result change 30 | C1 halve-and-hold (cut half at -50% of stop); post-result change 30 | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "C1 halve-and-hold (cut half at -50% of stop); post-result change 30"); judge: DESK_JUDGE.md |
| C2 adverse-speed cut (1 unit in 60 s); post-result change 31 | C2 adverse-speed cut (1 unit in 60 s); post-result change 31 | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "C2 adverse-speed cut (1 unit in 60 s); post-result change 31"); judge: DESK_JUDGE.md |
| loss-side keys CU / CX / SCR / NFT | early-cut, scratch and no-follow-through loss exits tested earlier | done (earlier programmes) | autopilot/EARLY_CUT_PREREG.md and DS3_DEEPEN_LOSS_*.md (exact row to be confirmed) |

## D. ADDS FAMILY: QUEUED

| design id | one-line rule | status | where the result is |
|---|---|---|---|
| D1 pyramid into a winner (+1R add half once, stop to entry, ratchet) | D1 pyramid into a winner (+1R add half once, stop to entry, ratchet) | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "D1 pyramid into a winner (+1R add half once, stop to entry, ratchet)"); judge: DESK_JUDGE.md |
| D2 scale-in entry (half first, add half if up 0.5 unit in median time) | D2 scale-in entry (half first, add half if up 0.5 unit in median time) | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "D2 scale-in entry (half first, add half if up 0.5 unit in median time)"); judge: DESK_JUDGE.md |

## E. RE-ENTRY FAMILY: QUEUED

| design id | one-line rule | status | where the result is |
|---|---|---|---|
| E1 continuation re-entry after a ratchet stop-out in profit | E1 continuation re-entry after a ratchet stop-out in profit | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "E1 continuation re-entry after a ratchet stop-out in profit"); judge: DESK_JUDGE.md |
| E2 no same-direction re-entry 15 min after a full stop | E2 no same-direction re-entry 15 min after a full stop | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "E2 no same-direction re-entry 15 min after a full stop"); judge: DESK_JUDGE.md |

## F. CONTEXT FAMILY: RUNNING

| design id | one-line rule | status | where the result is |
|---|---|---|---|
| v0.11 (trend day vs range day) | trend day vs range day | running (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "v0.11 (trend day vs range day)"); judge: DESK_JUDGE.md |
| v0.14 (time of session) | time of session (first-half release, target to 70% in last 30 min) | running (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "v0.14 (time of session)"); judge: DESK_JUDGE.md |
| F1 calendar-aware (ratchet 2 min before top-tier release, no entries -5/+5 min) | F1 calendar-aware (ratchet 2 min before top-tier release, no entries -5/+5 min) | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "F1 calendar-aware (ratchet 2 min before top-tier release, no entries -5/+5 min)"); judge: DESK_JUDGE.md |
| F2 volatility regime (high -> no target + ratchet; low -> bracket) | F2 volatility regime (high -> no target + ratchet; low -> bracket) | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "F2 volatility regime (high -> no target + ratchet; low -> bracket)"); judge: DESK_JUDGE.md |
| F3 day-of-week / opex / month-end (table first, one design only if it shows something) | F3 day-of-week / opex / month-end (table first, one design only if it shows something) | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "F3 day-of-week / opex / month-end (table first, one design only if it shows something)"); judge: DESK_JUDGE.md |
| v0.17 (the screens choose the day; post-result change 20) | v0.17 (the screens choose the day; post-result change 20) | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "v0.17 (the screens choose the day; post-result change 20)"); judge: DESK_JUDGE.md |

## G. DESK LEVEL (books managed together) FAMILY: RUNNING

| design id | one-line rule | status | where the result is |
|---|---|---|---|
| v0.2.2 (DK22 main) | desk manager v0.2.2: 1.5x safety stop, seats S1-S6 vote, PROBATION / DEFEND half / ABORT, objectives, free-trade stop, divergence, clock | done (NY AM 4/4, Asia 3/3, London 2/2, NY PM 2/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "v0.2.2 (DK22 main)"); judge: DESK_JUDGE.md; v0.2.2 also DESK_V022_SCORECARD.md / DESK_V022_ATTRIBUTION.md |
| G1 DAY PROFIT RATCHET (never give back half the session peak above 1.0x median winning day) | G1 DAY PROFIT RATCHET (never give back half the session peak above 1.0x median winning day) | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "G1 DAY PROFIT RATCHET (never give back half the session peak above 1.0x median winning day)"); judge: DESK_JUDGE.md |
| G2 same-direction crowd (3+ books in profit: bank the oldest, ratchet the rest) | G2 same-direction crowd (3+ books in profit: bank the oldest, ratchet the rest) | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "G2 same-direction crowd (3+ books in profit: bank the oldest, ratchet the rest)"); judge: DESK_JUDGE.md |
| G3 opposite books may not add | G3 opposite books may not add | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "G3 opposite books may not add"); judge: DESK_JUDGE.md |
| G4 loss-streak brake (after 3 full stops, half lots) | G4 loss-streak brake (after 3 full stops, half lots) | queued (NY AM 0/4, Asia 0/3, London 0/2, NY PM 0/2) | autopilot/DESK_DESIGNS_COMPARED.md (row "G4 loss-streak brake (after 3 full stops, half lots)"); judge: DESK_JUDGE.md |
| late-entry rule | late-entry gate on the desk entry | spec written; replay status per LATE_ENTRY_SPEC.md | autopilot/LATE_ENTRY_SPEC.md |

## H. JOINT STAGE: screen = top 3 designs per family by the drawdown-first rule (shallowest session-mix max DD among designs with income >= 70% of the live mix on the same window; the bracket is shown as the fallback), per session

| session | family | top 3 (design: income vs live, max DD vs live) |
|---|---|---|
| NY AM | B | v0.7 bracket + near-target guard (pl70k50): 2,297,634 (-19%), DD -354,064 vs -163,622 |
| NY AM | C | v0.3 (DK3 main): 2,177,072 (-24%), DD -166,714 vs -163,622 |
| London | A | v0.4-ceiling (own target as ceiling): 883,652 (+0%), DD -244,175 vs -224,333; v0.4 ratchet-only: 639,210 (-27%), DD -333,975 vs -224,333 |
| London | B | v0.5 bank half, run half: 727,136 (-17%), DD -267,977 vs -224,333 |
| London | C | v0.6 ratchet + ABORT: 625,315 (-29%), DD -348,763 vs -224,333 |
| NY PM | A | v0.4 ratchet-only: 726,210 (+10%), DD -99,650 vs -134,363; v0.4-ceiling (own target as ceiling): 605,915 (-8%), DD -109,320 vs -134,363 |
| NY PM | B | v0.5 bank half, run half: 681,839 (+4%), DD -101,387 vs -134,363; v0.7 bracket + near-target guard (pl70k50): 553,095 (-16%), DD -133,019 vs -134,363 |
| NY PM | C | v0.6 ratchet + ABORT: 727,261 (+11%), DD -99,650 vs -134,363 |

JOINT REPLAYS (stop x profit x loss x context x desk-level, each combination once, per session) and the interaction table: QUEUED; to be built with W-DYNC / the family agents once the top 3 per family exist; the walk-forward judge then runs over designs + combinations + the own bracket (ar_judge.py already takes any registered design with _A rows; combinations are registered as extra entries in desk_designs.json).

