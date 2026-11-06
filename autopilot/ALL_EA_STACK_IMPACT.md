# ALL_EA_STACK_IMPACT - unthinned PE + KB + HM + SM books on the headline stack (BASE-4, 2026-11-06). One page for the user. Research only, no PASS claim, nothing live, nothing published changed.
## What was tested
Same design as PE_EA_STACK_IMPACT.md (PE alone), now with ZL-2's all_ea tree: PE, KB, HM and SM each take every valid signal (extras PE 53,268, KB 33,823, HM 14,114, SM 747); ST, A6/pb7 and MV unchanged. Q1-A stack, 935 days to 2026-10-30, locks on, bases V0 (engine as run) and V2 (09:30-09:59 and 18:00-18:04 skipped), kfix off (published convention) and on. Prereg l2vast/ds3/prereg/ALL_EA_STACK_scope.md (sha256 6dc23671...). Seal manifest of 17,279 files unchanged, md5 guards OK.
## Result (published thinned books -> unthinned books; direction in words)
| | V0 kfix off | V0 kfix on | V2 kfix off | V2 kfix on |
|--|--|--|--|--|
| total $ | 2,520k -> 2,417k (DOWN 4.1%) | 2,505k -> 2,490k (down 0.6%) | 2,462k -> 2,476k (up 0.6%) | 2,520k -> 2,635k (UP 4.6%) |
| HOLD maxDD | 122k -> 163k (DEEPER 33%) | 131k -> 156k (deeper 19%) | 91k -> 129k (deeper 41%) | 101k -> 126k (deeper 25%) |
| HOLD Calmar | 0.185 -> 0.146 (worse) | 0.167 -> 0.156 (worse) | 0.260 -> 0.199 (worse) | 0.238 -> 0.208 (worse) |
| L6M maxDD | 105k -> 163k | 97k -> 156k | 65k -> 129k | 72k -> 126k |
| PRE maxDD | 88k -> 126k | 82k -> 119k | 94k -> 103k | 90k -> 87k |
| trades (all books) | 21,397 -> 26,654 | 21,459 -> 26,727 | 19,025 -> 24,370 | 19,112 -> 24,466 |
| lock exits | 120 -> 171 | 119 -> 167 | 115 -> 158 | 110 -> 153 |
Per book (V0 kfix off, $): KB 235k -> 338k (UP; trades 7,412 -> 10,065), HM 398k -> 445k (up, 3,287 -> 4,128 trades), PE 1,464k -> 1,282k (DOWN, 4,640 -> 6,254), SM 333k -> 261k (DOWN although only 1,370 -> 1,519 trades: a TH-L2 cut of SM blocks SM for 30 minutes (U7 rule), so the extra signals displace good ones), MV and PB7 unchanged. PE share of the total 58.1% -> 53.1%.
In words: unthinning all four books lifts the number of trades by about 25% and moves the total by -4% to +5% depending on base and kfix (no stable direction), but the worst stretch is deeper in all four cells (HOLD +19% to +41%, L6M +55% to +98%) and the Calmar is lower in all four. MID drawdown is shallower on V2 only. TH-L2 value per week (cut on minus off, V0 kfix off): post-cap +12.8k -> +15.1k, full history +1.5k -> +1.3k; the cut stays positive.
## Blind week (sealed recipe on all_ea)
Engine total 34,879 -> 69,543 on 217 trades (kfix on 57,598 on 209) against live 104,095. P7 as with PE alone (+37,107 on 63; live +86,010 on 53). K7 +10,319 on 61 -> +7,410 on 75 (live +16,065 on 64): live-only 16 -> 12 but engine-only 13 -> 23. H7 +9,266 on 19 -> +12,137 on 20 against live -770 on 3: the unthinned HM book does not reproduce the 3 live H7 trades (0 matched). U7 unchanged (7 trades +6,675 vs live 6 trades -1,755). So unthinning KB/HM/SM does not close the week's gap for those books.
## Caveats
Tie-out FAILED the same way as pe_ea: with all extras dropped the run gives 2,534,661 (V0) / 2,474,700 (V2) vs the published 2,520,149 / 2,462,264 (+0.5%): only the PE book differs (34 trades lose the 30% add leg, 2 missing) because skipping rows is not the same as the rows being absent; KB/HM/SM drop cleanly. Comparisons are published tree vs all_ea. POI streams not rebuilt; tags and profit statistics NaN for the extras (the engine does not read them); extras not tested for cap-period fidelity; the extras' nominal outcome flips sign by year (ZL-2). A baseline with unthinned books would be a new truth base: that decision is the lead's/user's.
Files: BLIND_DEFECTS_BASE4.md FOLLOW-UP-5; /mnt/l2/l2vast/ds3_base4/defects/all_ea/{allea_an.txt,*.pkl}; code allea_hist.py, allea_an.py.
