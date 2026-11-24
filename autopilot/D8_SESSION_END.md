# D8_SESSION_END: run to 17:00 ET (or a variant) versus flatten at the session end, EXACT engine, 2-lot basis (W-STATUS scorer, 2026-11-24 ~05:00Z)

Research only. Scored from the landed engine rows (code/th_sessend sets, hook se_hooks.py, no engine edit). Reference row = FLATTEN at the scheduled session end (Asia 02:00 ET, NY AM 12:00 ET; executed +1.0 s). Everything below is per 2 lots per book, net of $4.84 per lot, daily P&L by Globex day (exit time +7 h ET date), weeks Mon-Fri, ulcer = RMS of the daily drawdown. L6M = 2026-05..10, L3M = 2026-08..10. Scorer files (scratch): scratchpad/se_xs/se_score.py, se_null.py, se_md.py, se_book.py.

## REVISION (prior years and London / NY PM landed; scorer scratchpad/se_xs/se_score2.py)
- PRIOR YEARS (36 months, fixed setting, six finalists; table in the addendum below): NO variant holds up. Asia SEB1 (the L6M best on the pick): 2023 ulcer x1.03 / $/wk x0.90, 2024 x1.02 / x1.03, 2025 x0.86 / x1.45; blocks over all history 36 win / 57 lose = 0.39 (gate 0.58 FAIL). Asia SEA1 (plain RUN) is clearly worse in 2023-2024 (ulcer x1.62-1.70) and SEC4 loses $/wk 45% in 2023. NY AM SED2: 2023 x0.93 / x0.78, 2024 x1.16 / x0.99, 2025 x1.02 / x1.08, blocks 35/58 = 0.38 FAIL. NY AM SEC5 41/50. So the L6M improvements of SEB1 and SED2 do not persist: LABELS DOWNGRADED to BEST-AVAILABLE-NOT-PROVEN; FLATTEN STAYS the D8 rule for Asia and NY AM. (2026 Jan-Apr ratios in the table are on a near-zero base and should be ignored.)
- LONDON bare (77 of 78 L6M set-months landed): no variant helps: every run variant raises ulcer (SEB1 x1.10, SEA1 x1.28) and cuts $/wk (x0.82-0.99); the profit-conditional ones (SEC) and tighten ones (SED) are neutral (ulcer 1.00, $/wk 0.98-1.00). Best = none (flatten). Label none.
- NY PM pick JT209 (56 of 78 set-months landed, 22 still missing or blocked; partial rows are compared on their own months): plain RUN is clearly bad (SEA1 ulcer x1.46, DD x1.34, $/wk x0.81, 2 win / 11 lose blocks); the least bad are SED2 (4 months: ulcer x1.00, DD x0.98, $/wk x1.02, 5/7 blocks) and SEC6 (neutral). Best = none (flatten); label none, partial. No prior years queued for London / NY PM (nothing to confirm).
- EARLY-CLOSE EXIT-GAP MONTHS = UNSCORABLE (rule): Asia 202605 (6 sets), NY AM 202605/06/09 (11 sets), NY AM SEA1 prior-year 202309, 202401, 202501 (Labor Day 09-04-2023, MLK 01-15-2024, 01-20-2025 are holidays; consistent with the guard cause), London SEA1 202609 and NY PM SEA1 202609 (Labor Day 2026-09-07), and the NY PM months listed at the bottom (some may still be running). They are excluded, not imputed; the 14-day block tallies use only landed months.
- The earlier table's "BEST SETTING PER SESSION" and labels above remain as the L6M reading; read them with this revision: nothing is WEAK-BUT-POSITIVE after prior years, flatten is the answer for all four sessions.

## STATUS AND WHAT IS NOT IN THIS PAGE
- Two sessions were run: Asia (5-book TL3_ALN_AS_STKd8106b26ef) and NY AM (5-book TL3_ALN_NY_STKd8b76ecd35), each 13 settings on (a) the delivered 2-lot pick (SK sets; Asia BF2_JT19, NY AM BF2_JT68; this is what D8 carries) and (b) the bare 2-lot base (SE sets, BF2_BASE; reference for the layer-free effect). London (bare) and NY PM (bare) were NEVER run: no set, no row. To run them: 13 settings x 6 months x 2 sessions = 156 rows plus 2 identity rows each (about 160 rows total; the hook and set generator exist, se_gen2.py needs the London/NY PM pick name). I have NOT queued anything; LEAD to say yes/no. Rate ~3.9k rows/h fleet-wide, but these ride rank 4.5 (share 0.15-0.35), so ETA 1-3 h after a yes (my estimate, not measured).
- 17 of the 312 L6M set-months did not land and are not queued or leased anywhere (checked pending_sr_fit.txt, _s2/leases, the parked file): Asia SE_SEA1/SEC1/SEC2/SEC3 and SK_SEC1/SK_SEC3 202605 (6 rows; 202605 contains Memorial Day 2026-05-25); NY AM SE_SEB4 202605/06/09, SE_SEC1 202606, SK_SEA1 202605/06/09, SK_SEB4 202605/06/09, SK_SEC1 202606 (11 rows; 202605/06/09 are exactly the months with the CME early-close holidays 05-25, 06-19, 09-07; W-NYENG's 08:14Z diagnosis in MORNING.md names the same months failing on the exit-at-last-print guard for other NY AM sets). The probable cause is the guard failing a hook that carries a trade past an early close (variants that run to 17:00); I did NOT verify that for these sets. Where a setting lacks months, it is compared with the reference on the SAME months (the reference column shows them), so ratios are comparable but a 3- or 5-month row is thinner. The status file's "all rows landed" was wrong on this point. Count to re-run: 17 rows, minutes of fleet once the guard cause is fixed.
- PRIOR YEARS: no SE row exists for any prior-year month, so prior-year bands cannot be scored for any variant. For the three finalists per session on the delivered pick: 3 settings x 36 prior months x 2 sessions = 216 rows (+ the reference months already exist: BF2_JT19/JT68/BASE have all 42). Same ETA caveat; NY AM prior months with CME early-close holidays (several per year) and Asia months with early closes would hit the same guard failure. NOT queued; LEAD to say yes/no.
- WALK-FORWARD: a true rolling pick needs prior years. What is here is the FIXED-setting version over the L6M only: share of 14-day blocks (13-14 blocks) in which the setting beats the reference, drawdown first (lower block max drawdown, dollars on ties). Gate is >= 0.58. Thin (13-14 periods), and many settings differ in few blocks.
- BEST-OF-MANY NULL (EMULATED, no engine rows): for each session x family the 13 settings are the search. Under the null every day on which a setting changes anything gets its delta (variant minus flatten) sign-flipped with probability 1/2 (same flip for all 13 settings on that day, so their correlation is kept), the pick rule is applied (lowest L6M ulcer among settings with total $ >= flatten), 1000 draws; the real pick must beat >= 80% of the draws (4 of 5). This tests "is the best-of-13 gain bigger than luck-signed deltas would give", a symmetric-noise null, not the random-entry null of the 1810Z order; the real random-entry null needs engine rows (13 settings x 6 months x 5 random-entry streams ~ 400 rows per session) and I did not queue it.

## ANSWER IN ONE PARAGRAPH
Running to 17:00 ET (SEA1) is NOT a free win. ASIA: on the bare base it adds about +11% $/wk at equal or slightly lower ulcer (x0.98) and max DD (x0.96), but on the DELIVERED PICK it adds +12% $/wk and +13% ulcer, +6% max DD (L3M ulcer +35%): the pick's own layers (BookLock, StackCut, policy take/trail) already manage those trades and the extra exposure just adds drawdown. NY AM: running loses money and adds drawdown on both bases ($/wk -2% pick, -8% bare; ulcer +17% pick, +14% bare; the carried NY AM trades go from -$9k to -$39k bare). So flatten is right for NY AM, and for Asia the plain RUN is wrong for risk. Variants that keep drawdown: Asia pick best = SEB1 (flatten 15 minutes later) WEAK-BUT-POSITIVE; NY AM pick best = SED2 (lock half the open profit at noon, target stays) WEAK-BUT-POSITIVE. On the bare Asia base the profit-conditional / breakeven variants SEC4 and SED1 are a real effect (ulcer -22%, DD -11%, $/wk +7-8%, blocks 11 of 14, null 100%) but that effect does NOT survive on the delivered pick (SEC4 on the pick: ulcer +1%, DD -3%, $ +2%). No variant reaches CONFIRMED (prior years missing for all).

## BEST SETTING PER SESSION (drawdown first; "none" = flatten = the reference row)
| session / basis | best setting | L6M ulcer / max DD / $/wk / worst week vs flatten | L3M ulcer / $/wk | blocks win/lose/same of 14 | null (>= 80%) | label |
|---|---|---|---|---|---|---|
| ASIA, delivered pick JT19 (D8 file) | SEB1 RUN with hard flat 15 min after the end, no new entries | 0.99 / 1.03 / 1.10 / 0.85 (9,849 -> 10,802 $/wk; ulcer 2,733 -> 2,696; max DD -8,694 -> -8,984; worst week -3,660 -> -3,100) | 0.93 / 1.22 (L3M $/wk 8,862 -> 10,797; ulcer 2,013 -> 1,865) | 5/8/1 (fails 0.58; dollars better in 8 of 14) | 66% FAIL | WEAK-BUT-POSITIVE (dollars up in L6M and L3M, risk about unchanged, fails walk-forward and null; no prior years). Flatten stays the reference. |
| NY AM, delivered pick JT68 (D8 file) | SED2 tighten: at noon lock half the open profit (losers stop at breakeven = out at once), target stays, hard flat 17:00 ET | 0.96 / 0.93 / 1.02 / 1.00 (6,076 -> 6,182; ulcer 3,514 -> 3,388; max DD -10,218 -> -9,520) | 0.95 / 1.06 | 4/10/0 (fails) | 66% FAIL | WEAK-BUT-POSITIVE (all four numbers right-signed but the gain, 3.6% ulcer, is inside the null: median best-of-13 gain 1.8%). |
| ASIA, bare base (reference only, not in D8) | SEC4 (keep a trade running if open profit >= 0 and move the stop to breakeven; losers closed) or SED1 (stop to breakeven at the end) | SEC4 0.78 / 0.89 / 1.08 / 0.86; SED1 0.78 / 0.89 / 1.07 / 0.88 | 0.69 / 1.10 | 11/2/1 | 100% PASS | LEAD (bare only; prior years missing; not carried to the pick) |
| NY AM, bare base (reference only) | SED2 or SEC5 | SED2 0.96 / 1.01 / 1.02 / 1.00; SEC5 0.98 / 1.02 / 0.98 | 0.94-0.99 / 0.99-1.04 | 7/7/0 | 69% FAIL | BEST-AVAILABLE-NOT-PROVEN (inside noise) |
| LONDON bare, NY PM bare | not run | | | | | no rows exist |

Exact rule wording the relay can code (all variants: no new entries after the end, as today; a running trade keeps its own stop and target resting and stays under every other layer; every runner that is still open is flattened at the next 17:00 ET Globex close, exit name SessFlat, also before a contract roll as today):
- FLATTEN (reference, today): at the scheduled session end +1 s (Asia 02:00:01 ET, NY AM 12:00:01 ET) send a market exit for every open trade of the book (exit UWTime).
- SEB1 (Asia pick): at 02:00:01 ET do not send the exit; if the trade is still open at min(02:15:01 ET, next 17:00 ET) send a market exit (SessFlat). Stop and target stay as set. Only the scheduled session-end exit is replaced; the per-book time limit (xmin) is untouched.
- SED2 (NY AM pick): at 12:00:01 ET read the open profit in points against the liquidation side (bid for a long, ask for a short). If the trade is in profit move the stop to entry + side x 0.5 x open-profit points; if flat or losing move the stop to the entry price (breakeven; already through the market, so it stops out at once as a normal Stop). Target stays. Prices rounded to 0.25. Then flatten at the next 17:00 ET.
- SEA1 (plain RUN): no action at the session end, flatten at the next 17:00 ET. SEB2-4: same with 30 / 60 / 120 minutes. SEC1-3: close at the end unless open profit >= 0 / 0.25 / 0.5 x target distance (target distance = trade target points if set, else stop points x target R), otherwise run to 17:00 ET; SEC4-6 the same plus stop to breakeven for the runner. SED1: stop to breakeven at the end (losers out at once).
- Interplay with the one-position rule and the stack: a running trade keeps its book "in trade", so that book takes no new entry until it closes; in these 6 months the set of entries was IDENTICAL to flatten in every setting (0 entries added or removed in all 52 pick and bare sets: the Asia book next trades the following evening, NY AM the next morning). The runner remains subject to the stack-level and book-level layers of the pick (StackCut, BookLock, policy take/trail, day stops); in the bare sets there are none. Not tested: the runner interacting with a LATER session's stack (Asia runner past 03:00 ET London open or into NY AM): none occurred as a rule violation but that case is not isolated.
- Why the pick differs from the bare base is NOT verified; the plausible reason is that the pick's layers already cut the same trades (its flatten-exited trades fall from 328 to 202 over L6M).


## PER SESSION AND STACK, ALL 13 SETTINGS (L6M, with L3M beside; the reference is on the same months)

Note 1: "open at end" = trades whose exit differs from flatten (the trades that were open at the session end). For the delivered pick that is 202 trades in L6M for Asia (7.7 per week) and 147 for NY AM (5.6 per week), 2 lots each. Note 2: months column below 6 = months that did not land (see status).

### ASIA, delivered 2-lot pick BF2_JT19 (reference row = the pick with flatten at 02:00 ET)

Cells: $/wk / ulcer / max DD / worst week / worst day (net of $4.84, per 2 lots per book). The reference row is on the SAME months as the setting. Ratios: variant / reference (ulcer, max DD, $/wk, worst week, worst day; below 1.00 on risk = better). Open-at-end = trades whose exit differs from flatten, per week, with their P&L flatten -> variant. Blocks = 14-day blocks the setting beats the reference (drawdown first, dollars on ties) / loses / identical.

| setting | months | reference L6M | variant L6M | ulcer x | maxDD x | $/wk x | wk-worst x | day-worst x | L3M ulcer x / $/wk x | open at end /wk, P&L flatten -> variant | blocks win/lose/same | blocks $ better |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SEA1 RUN to 17:00 ET | 6 | 9,849/2,733/-8,694/-3,660/-7,635 | 11,039/3,095/-9,225/-1,110/-8,226 | 1.13 | 1.06 | 1.12 | 0.30 | 1.08 | 1.35 / 1.16 | 7.7, 52,240 -> 84,348 | 3/10/1 | 9 of 14 |
| SEB1 RUN, flat +15 min | 6 | 9,849/2,733/-8,694/-3,660/-7,635 | 10,802/2,696/-8,984/-3,100/-7,635 | 0.99 | 1.03 | 1.10 | 0.85 | 1.00 | 0.93 / 1.22 | 7.7, 52,240 -> 77,947 | 5/8/1 | 8 of 14 |
| SEB2 RUN, flat +30 min | 6 | 9,849/2,733/-8,694/-3,660/-7,635 | 10,855/2,725/-8,859/-3,500/-7,635 | 1.00 | 1.02 | 1.10 | 0.96 | 1.00 | 1.07 / 1.18 | 7.7, 52,240 -> 79,379 | 5/8/1 | 10 of 14 |
| SEB3 RUN, flat +60 min | 6 | 9,849/2,733/-8,694/-3,660/-7,635 | 10,887/2,776/-8,559/-2,100/-7,635 | 1.02 | 0.98 | 1.11 | 0.57 | 1.00 | 1.17 / 1.16 | 7.7, 52,240 -> 80,264 | 4/9/1 | 10 of 14 |
| SEB4 RUN, flat +120 min | 6 | 9,849/2,733/-8,694/-3,660/-7,635 | 10,862/3,110/-8,934/-1,110/-7,706 | 1.14 | 1.03 | 1.10 | 0.30 | 1.01 | 1.36 / 1.12 | 7.7, 52,240 -> 79,578 | 1/12/1 | 8 of 14 |
| SEC1 keep if open profit >= 0 x tgt | 5 | 8,923/2,883/-8,694/-3,660/-7,635 | 9,512/3,217/-8,848/-1,110/-8,226 | 1.12 | 1.02 | 1.07 | 0.30 | 1.08 | 1.33 / 1.04 | 5.0, 66,492 -> 79,443 | 5/6/0 | 8 of 11 |
| SEC2 keep if >= 0.25 x tgt | 6 | 9,849/2,733/-8,694/-3,660/-7,635 | 10,085/3,096/-10,164/-2,580/-7,635 | 1.13 | 1.17 | 1.02 | 0.70 | 1.00 | 1.26 / 1.02 | 2.9, 66,286 -> 72,647 | 4/9/1 | 7 of 14 |
| SEC3 keep if >= 0.5 x tgt | 5 | 8,923/2,883/-8,694/-3,660/-7,635 | 9,080/2,870/-8,694/-3,660/-7,635 | 1.00 | 1.00 | 1.02 | 1.00 | 1.00 | 0.99 / 1.05 | 1.1, 29,960 -> 33,405 | 5/4/2 | 5 of 11 |
| SEC4 as SEC1 + stop to BE | 6 | 9,849/2,733/-8,694/-3,660/-7,635 | 10,034/2,749/-8,429/-3,220/-7,635 | 1.01 | 0.97 | 1.02 | 0.88 | 1.00 | 1.07 / 1.02 | 4.9, 75,451 -> 80,432 | 5/8/1 | 7 of 14 |
| SEC5 as SEC2 + stop to BE | 6 | 9,849/2,733/-8,694/-3,660/-7,635 | 10,011/2,906/-9,999/-4,100/-7,635 | 1.06 | 1.15 | 1.02 | 1.12 | 1.00 | 1.01 / 1.05 | 2.9, 66,286 -> 70,641 | 5/8/1 | 7 of 14 |
| SEC6 as SEC3 + stop to BE | 6 | 9,849/2,733/-8,694/-3,660/-7,635 | 10,070/2,730/-8,694/-3,660/-7,635 | 1.00 | 1.00 | 1.02 | 1.00 | 1.00 | 0.99 / 1.05 | 1.0, 32,316 -> 38,261 | 6/5/3 | 6 of 14 |
| SED1 stop to BE at end | 6 | 9,849/2,733/-8,694/-3,660/-7,635 | 9,920/2,940/-8,838/-3,220/-7,635 | 1.08 | 1.02 | 1.01 | 0.88 | 1.00 | 1.06 / 1.02 | 7.7, 51,665 -> 53,582 | 4/9/1 | 6 of 14 |
| SED2 lock half open profit at end | 6 | 9,849/2,733/-8,694/-3,660/-7,635 | 9,933/2,808/-8,483/-2,840/-7,635 | 1.03 | 0.98 | 1.01 | 0.78 | 1.00 | 0.99 / 1.02 | 7.7, 51,665 -> 53,922 | 4/9/1 | 6 of 14 |

Best-of-13 null (emulation, see method): pick rule = lowest L6M ulcer among settings with total $ >= reference; real best SEB1 gains 1.4% ulcer; null best-of-13 median 0.0%, 80th pct 3.7%, 95th pct 7.5%; real beats 66% of 1000 null draws (gate: >= 80%, i.e. 4 of 5): FAIL.

### ASIA, bare 2-lot base BF2_BASE (reference = bare flatten)

Cells: $/wk / ulcer / max DD / worst week / worst day (net of $4.84, per 2 lots per book). The reference row is on the SAME months as the setting. Ratios: variant / reference (ulcer, max DD, $/wk, worst week, worst day; below 1.00 on risk = better). Open-at-end = trades whose exit differs from flatten, per week, with their P&L flatten -> variant. Blocks = 14-day blocks the setting beats the reference (drawdown first, dollars on ties) / loses / identical.

| setting | months | reference L6M | variant L6M | ulcer x | maxDD x | $/wk x | wk-worst x | day-worst x | L3M ulcer x / $/wk x | open at end /wk, P&L flatten -> variant | blocks win/lose/same | blocks $ better |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SEA1 RUN to 17:00 ET | 5 | 23,489/6,709/-21,015/-6,171/-13,215 | 26,094/6,558/-20,145/-5,874/-13,605 | 0.98 | 0.96 | 1.11 | 0.95 | 1.03 | 0.89 / 1.20 | 12.4, 132,277 -> 189,582 | 4/7/0 | 8 of 11 |
| SEB1 RUN, flat +15 min | 6 | 20,495/7,070/-21,015/-19,862/-13,215 | 21,575/6,337/-21,667/-21,667/-13,745 | 0.90 | 1.03 | 1.05 | 1.09 | 1.04 | 0.83 / 1.11 | 12.5, 152,695 -> 181,865 | 9/4/1 | 8 of 14 |
| SEB2 RUN, flat +30 min | 6 | 20,495/7,070/-21,015/-19,862/-13,215 | 21,692/6,538/-18,960/-18,407/-13,725 | 0.92 | 0.90 | 1.06 | 0.93 | 1.04 | 0.84 / 1.10 | 12.5, 152,695 -> 185,030 | 9/4/1 | 8 of 14 |
| SEB3 RUN, flat +60 min | 6 | 20,495/7,070/-21,015/-19,862/-13,215 | 21,984/7,022/-26,397/-26,397/-14,097 | 0.99 | 1.26 | 1.07 | 1.33 | 1.07 | 0.80 / 1.11 | 12.5, 152,695 -> 192,900 | 8/5/1 | 9 of 14 |
| SEB4 RUN, flat +120 min | 6 | 20,495/7,070/-21,015/-19,862/-13,215 | 22,308/7,567/-26,387/-26,387/-14,097 | 1.07 | 1.26 | 1.09 | 1.33 | 1.07 | 0.86 / 1.14 | 12.5, 152,695 -> 201,670 | 5/8/1 | 8 of 14 |
| SEC1 keep if open profit >= 0 x tgt | 5 | 23,489/6,709/-21,015/-6,171/-13,215 | 25,592/5,784/-24,296/-5,274/-13,160 | 0.86 | 1.16 | 1.09 | 0.85 | 1.00 | 0.83 / 1.11 | 8.3, 189,523 -> 235,778 | 6/5/0 | 8 of 11 |
| SEC2 keep if >= 0.25 x tgt | 5 | 23,489/6,709/-21,015/-6,171/-13,215 | 24,460/5,598/-19,916/-4,544/-13,215 | 0.83 | 0.95 | 1.04 | 0.74 | 1.00 | 0.82 / 1.07 | 5.1, 164,016 -> 185,371 | 7/4/0 | 6 of 11 |
| SEC3 keep if >= 0.5 x tgt | 5 | 23,489/6,709/-21,015/-6,171/-13,215 | 23,388/6,004/-17,805/-5,224/-13,215 | 0.89 | 0.85 | 1.00 | 0.85 | 1.00 | 0.86 / 1.01 | 2.0, 90,469 -> 88,249 | 8/3/0 | 6 of 11 |
| SEC4 as SEC1 + stop to BE | 6 | 20,495/7,070/-21,015/-19,862/-13,215 | 22,069/5,504/-18,755/-17,082/-13,160 | 0.78 | 0.89 | 1.08 | 0.86 | 1.00 | 0.69 / 1.10 | 8.3, 222,874 -> 265,384 | 11/2/1 | 10 of 14 |
| SEC5 as SEC2 + stop to BE | 6 | 20,495/7,070/-21,015/-19,862/-13,215 | 21,567/6,028/-19,382/-19,382/-13,215 | 0.85 | 0.92 | 1.05 | 0.98 | 1.00 | 0.80 / 1.06 | 5.0, 191,492 -> 220,447 | 10/3/1 | 9 of 14 |
| SEC6 as SEC3 + stop to BE | 6 | 20,495/7,070/-21,015/-19,862/-13,215 | 20,794/6,451/-19,862/-19,862/-13,215 | 0.91 | 0.95 | 1.01 | 1.00 | 1.00 | 0.86 / 1.02 | 2.0, 103,257 -> 111,342 | 9/4/1 | 8 of 14 |
| SED1 stop to BE at end | 6 | 20,495/7,070/-21,015/-19,862/-13,215 | 22,027/5,528/-18,755/-17,392/-13,155 | 0.78 | 0.89 | 1.07 | 0.88 | 1.00 | 0.69 / 1.10 | 12.6, 151,535 -> 192,910 | 11/2/1 | 10 of 14 |
| SED2 lock half open profit at end | 6 | 20,495/7,070/-21,015/-19,862/-13,215 | 21,963/5,814/-19,380/-16,272/-13,155 | 0.82 | 0.92 | 1.07 | 0.82 | 1.00 | 0.79 / 1.07 | 12.6, 151,535 -> 191,190 | 10/3/1 | 10 of 14 |

Best-of-13 null (emulation, see method): pick rule = lowest L6M ulcer among settings with total $ >= reference; real best SEC4 gains 22.2% ulcer; null best-of-13 median 1.1%, 80th pct 6.7%, 95th pct 12.0%; real beats 100% of 1000 null draws (gate: >= 80%, i.e. 4 of 5): PASS.

### NY AM, delivered 2-lot pick BF2_JT68 (reference = the pick with flatten at 12:00 ET)

Cells: $/wk / ulcer / max DD / worst week / worst day (net of $4.84, per 2 lots per book). The reference row is on the SAME months as the setting. Ratios: variant / reference (ulcer, max DD, $/wk, worst week, worst day; below 1.00 on risk = better). Open-at-end = trades whose exit differs from flatten, per week, with their P&L flatten -> variant. Blocks = 14-day blocks the setting beats the reference (drawdown first, dollars on ties) / loses / identical.

| setting | months | reference L6M | variant L6M | ulcer x | maxDD x | $/wk x | wk-worst x | day-worst x | L3M ulcer x / $/wk x | open at end /wk, P&L flatten -> variant | blocks win/lose/same | blocks $ better |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SEA1 RUN to 17:00 ET | 3 | 5,456/3,342/-9,508/-4,550/-5,379 | 5,342/3,899/-12,268/-2,875/-8,114 | 1.17 | 1.29 | 0.98 | 0.63 | 1.51 | 1.04 / 1.27 | 5.5, 103 -> -1,603 | 3/5/0 | 4 of 8 |
| SEB1 RUN, flat +15 min | 6 | 6,076/3,514/-10,218/-4,550/-5,504 | 6,320/3,547/-10,948/-3,783/-7,234 | 1.01 | 1.07 | 1.04 | 0.83 | 1.31 | 1.00 / 1.01 | 5.6, -4,624 -> 1,956 | 6/8/0 | 7 of 14 |
| SEB2 RUN, flat +30 min | 6 | 6,076/3,514/-10,218/-4,550/-5,504 | 5,941/3,765/-12,268/-5,579/-7,184 | 1.07 | 1.20 | 0.98 | 1.23 | 1.31 | 1.05 / 0.97 | 5.6, -4,624 -> -8,272 | 6/8/0 | 7 of 14 |
| SEB3 RUN, flat +60 min | 6 | 6,076/3,514/-10,218/-4,550/-5,504 | 5,843/3,827/-12,540/-6,124/-6,744 | 1.09 | 1.23 | 0.96 | 1.35 | 1.23 | 1.06 / 0.93 | 5.6, -4,624 -> -10,918 | 4/10/0 | 6 of 14 |
| SEB4 RUN, flat +120 min | 3 | 5,456/3,385/-9,508/-4,550/-5,379 | 4,927/3,989/-12,268/-3,720/-8,114 | 1.18 | 1.29 | 0.90 | 0.82 | 1.51 | 1.16 / 0.94 | 5.5, 103 -> -7,833 | 3/5/0 | 3 of 8 |
| SEC1 keep if open profit >= 0 x tgt | 5 | 5,570/3,780/-10,218/-4,550/-5,504 | 4,742/5,142/-15,284/-5,695/-8,114 | 1.36 | 1.50 | 0.85 | 1.25 | 1.47 | 1.44 / 0.80 | 2.8, 31,491 -> 12,449 | 4/9/0 | 5 of 13 |
| SEC2 keep if >= 0.25 x tgt | 6 | 6,076/3,514/-10,218/-4,550/-5,504 | 5,643/3,948/-11,603/-4,550/-5,504 | 1.12 | 1.14 | 0.93 | 1.00 | 1.00 | 1.14 / 0.99 | 1.4, 32,471 -> 20,776 | 6/6/2 | 5 of 14 |
| SEC3 keep if >= 0.5 x tgt | 6 | 6,076/3,514/-10,218/-4,550/-5,504 | 5,946/3,615/-10,218/-4,550/-5,504 | 1.03 | 1.00 | 0.98 | 1.00 | 1.00 | 1.03 / 1.04 | 0.5, 16,082 -> 12,557 | 6/2/6 | 6 of 14 |
| SEC4 as SEC1 + stop to BE | 6 | 6,076/3,514/-10,218/-4,550/-5,504 | 5,989/3,467/-9,510/-4,550/-5,699 | 0.99 | 0.93 | 0.99 | 1.00 | 1.04 | 0.97 / 1.03 | 2.7, 38,287 -> 35,927 | 5/9/0 | 5 of 14 |
| SEC5 as SEC2 + stop to BE | 6 | 6,076/3,514/-10,218/-4,550/-5,504 | 6,042/3,423/-9,510/-4,550/-5,504 | 0.97 | 0.93 | 0.99 | 1.00 | 1.00 | 0.96 / 1.04 | 1.4, 32,471 -> 31,536 | 6/6/2 | 6 of 14 |
| SEC6 as SEC3 + stop to BE | 6 | 6,076/3,514/-10,218/-4,550/-5,504 | 6,137/3,544/-10,218/-4,550/-5,504 | 1.01 | 1.00 | 1.01 | 1.00 | 1.00 | 1.01 / 1.05 | 0.5, 16,082 -> 17,727 | 6/2/6 | 6 of 14 |
| SED1 stop to BE at end | 6 | 6,076/3,514/-10,218/-4,550/-5,504 | 5,966/3,477/-9,520/-4,550/-5,699 | 0.99 | 0.93 | 0.98 | 1.00 | 1.04 | 0.98 / 1.03 | 5.6, -4,624 -> -7,614 | 4/10/0 | 5 of 14 |
| SED2 lock half open profit at end | 6 | 6,076/3,514/-10,218/-4,550/-5,504 | 6,182/3,388/-9,520/-4,550/-5,544 | 0.96 | 0.93 | 1.02 | 1.00 | 1.01 | 0.95 / 1.06 | 5.6, -4,624 -> -1,764 | 4/10/0 | 6 of 14 |

Best-of-13 null (emulation, see method): pick rule = lowest L6M ulcer among settings with total $ >= reference; real best SED2 gains 3.6% ulcer; null best-of-13 median 1.8%, 80th pct 5.6%, 95th pct 9.6%; real beats 66% of 1000 null draws (gate: >= 80%, i.e. 4 of 5): FAIL.

### NY AM, bare 2-lot base BF2_BASE (reference = bare flatten)

Cells: $/wk / ulcer / max DD / worst week / worst day (net of $4.84, per 2 lots per book). The reference row is on the SAME months as the setting. Ratios: variant / reference (ulcer, max DD, $/wk, worst week, worst day; below 1.00 on risk = better). Open-at-end = trades whose exit differs from flatten, per week, with their P&L flatten -> variant. Blocks = 14-day blocks the setting beats the reference (drawdown first, dollars on ties) / loses / identical.

| setting | months | reference L6M | variant L6M | ulcer x | maxDD x | $/wk x | wk-worst x | day-worst x | L3M ulcer x / $/wk x | open at end /wk, P&L flatten -> variant | blocks win/lose/same | blocks $ better |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SEA1 RUN to 17:00 ET | 6 | 14,123/9,149/-34,859/-33,890/-15,819 | 13,023/10,463/-34,534/-31,535/-18,804 | 1.14 | 0.99 | 0.92 | 0.93 | 1.19 | 1.35 / 0.92 | 7.4, -9,058 -> -38,748 | 5/9/0 | 8 of 14 |
| SEB1 RUN, flat +15 min | 6 | 14,123/9,187/-34,859/-33,890/-15,819 | 14,164/9,242/-30,024/-28,280/-15,861 | 1.01 | 0.86 | 1.00 | 0.83 | 1.00 | 1.04 / 0.95 | 7.4, -9,058 -> -7,928 | 8/6/0 | 7 of 14 |
| SEB2 RUN, flat +30 min | 6 | 14,123/9,187/-34,859/-33,890/-15,819 | 13,346/9,414/-30,984/-28,705/-15,974 | 1.02 | 0.89 | 0.95 | 0.85 | 1.01 | 1.08 / 0.88 | 7.4, -9,058 -> -30,013 | 8/6/0 | 8 of 14 |
| SEB3 RUN, flat +60 min | 6 | 14,123/9,187/-34,859/-33,890/-15,819 | 13,443/9,840/-33,949/-31,535/-18,804 | 1.07 | 0.97 | 0.95 | 0.93 | 1.19 | 1.14 / 0.92 | 7.4, -9,058 -> -27,418 | 6/8/0 | 5 of 14 |
| SEB4 RUN, flat +120 min | 3 | 13,384/7,199/-26,590/-6,945/-13,496 | 11,303/9,173/-30,760/-11,825/-15,861 | 1.27 | 1.16 | 0.84 | 1.70 | 1.18 | 1.43 / 0.87 | 7.5, 6,017 -> -25,208 | 3/5/0 | 3 of 8 |
| SEC1 keep if open profit >= 0 x tgt | 5 | 14,733/7,846/-26,590/-6,945/-14,238 | 12,988/8,960/-23,745/-14,433/-13,543 | 1.14 | 0.89 | 0.88 | 2.08 | 0.95 | 1.22 / 0.89 | 3.6, 81,995 -> 41,855 | 4/9/0 | 6 of 13 |
| SEC2 keep if >= 0.25 x tgt | 6 | 14,123/9,187/-34,859/-33,890/-15,819 | 13,013/9,776/-37,919/-36,950/-18,422 | 1.06 | 1.09 | 0.92 | 1.09 | 1.16 | 1.12 / 0.97 | 2.1, 85,887 -> 55,922 | 6/8/0 | 4 of 14 |
| SEC3 keep if >= 0.5 x tgt | 6 | 14,123/9,187/-34,859/-33,890/-15,819 | 13,533/9,406/-34,859/-33,890/-15,819 | 1.02 | 1.00 | 0.96 | 1.00 | 1.00 | 1.05 / 0.99 | 1.0, 47,943 -> 32,028 | 6/4/4 | 5 of 14 |
| SEC4 as SEC1 + stop to BE | 6 | 14,123/9,187/-34,859/-33,890/-15,819 | 13,805/9,056/-35,594/-34,625/-16,097 | 0.99 | 1.02 | 0.98 | 1.02 | 1.02 | 0.99 / 0.99 | 3.5, 99,415 -> 90,830 | 7/7/0 | 6 of 14 |
| SEC5 as SEC2 + stop to BE | 6 | 14,123/9,187/-34,859/-33,890/-15,819 | 13,802/9,006/-35,594/-34,625/-16,097 | 0.98 | 1.02 | 0.98 | 1.02 | 1.02 | 0.99 / 0.99 | 2.1, 85,887 -> 77,227 | 9/5/0 | 6 of 14 |
| SEC6 as SEC3 + stop to BE | 6 | 14,123/9,187/-34,859/-33,890/-15,819 | 14,193/9,235/-34,859/-33,890/-15,819 | 1.01 | 1.00 | 1.01 | 1.00 | 1.00 | 1.02 / 1.02 | 1.0, 47,943 -> 49,853 | 6/4/4 | 5 of 14 |
| SED1 stop to BE at end | 6 | 14,123/9,187/-34,859/-33,890/-15,819 | 13,800/9,073/-35,644/-34,835/-16,147 | 0.99 | 1.02 | 0.98 | 1.03 | 1.02 | 0.99 / 0.99 | 7.4, -9,058 -> -17,763 | 6/8/0 | 6 of 14 |
| SED2 lock half open profit at end | 6 | 14,123/9,187/-34,859/-33,890/-15,819 | 14,408/8,854/-35,109/-34,300/-15,819 | 0.96 | 1.01 | 1.02 | 1.01 | 1.00 | 0.94 / 1.04 | 7.4, -9,058 -> -1,348 | 7/7/0 | 8 of 14 |

Best-of-13 null (emulation, see method): pick rule = lowest L6M ulcer among settings with total $ >= reference; real best SED2 gains 3.6% ulcer; null best-of-13 median 0.8%, 80th pct 5.3%, 95th pct 9.6%; real beats 69% of 1000 null draws (gate: >= 80%, i.e. 4 of 5): FAIL.

## PER BOOK (trades that were open at the session end, P&L flatten vs variant, net of $4.84, over the months shown)

| basis | setting | book | trades open at end (diff exit) | P&L flatten | P&L variant | change |
|---|---|---|---|---|---|---|
| Asia pick (6 mo) | SEA1 | MF1 | 61 | 30,462 | 39,332 | +8,870 |
| Asia pick (6 mo) | SEA1 | MF2 | 29 | 4,901 | 1,131 | -3,770 |
| Asia pick (6 mo) | SEA1 | MF3 | 19 | -2,351 | -716 | +1,635 |
| Asia pick (6 mo) | SEA1 | MF4 | 37 | 4,042 | 18,380 | +14,338 |
| Asia pick (6 mo) | SEA1 | MF5 | 56 | 15,186 | 26,221 | +11,035 |
| Asia pick | SEA1 | ALL | 202 | 52,240 | 84,348 | +32,108 |
| Asia pick (6 mo) | SEB1 | MF1 | 61 | 30,462 | 37,472 | +7,010 |
| Asia pick (6 mo) | SEB1 | MF2 | 29 | 4,901 | 5,871 | +970 |
| Asia pick (6 mo) | SEB1 | MF3 | 19 | -2,351 | 3,229 | +5,580 |
| Asia pick (6 mo) | SEB1 | MF4 | 37 | 4,042 | 10,704 | +6,662 |
| Asia pick (6 mo) | SEB1 | MF5 | 56 | 15,186 | 20,671 | +5,485 |
| Asia pick | SEB1 | ALL | 202 | 52,240 | 77,947 | +25,707 |
| NY AM pick (3 mo) | SEA1 | MF1 | 11 | -918 | -1,054 | -136 |
| NY AM pick (3 mo) | SEA1 | MF2 | 23 | -2,606 | 4,844 | +7,450 |
| NY AM pick (3 mo) | SEA1 | MF3 | 29 | 585 | -7,525 | -8,110 |
| NY AM pick (3 mo) | SEA1 | MF4 | 1 | 35 | 20 | -15 |
| NY AM pick (3 mo) | SEA1 | MF5 | 9 | 3,006 | 2,111 | -895 |
| NY AM pick | SEA1 | ALL | 73 | 103 | -1,603 | -1,706 |
| NY AM pick (6 mo) | SED2 | MF1 | 26 | -4,245 | -4,720 | -475 |
| NY AM pick (6 mo) | SED2 | MF2 | 48 | -9,351 | -6,986 | +2,365 |
| NY AM pick (6 mo) | SED2 | MF3 | 57 | 2,735 | 4,600 | +1,865 |
| NY AM pick (6 mo) | SED2 | MF4 | 1 | 35 | 35 | +0 |
| NY AM pick (6 mo) | SED2 | MF5 | 15 | 6,202 | 5,307 | -895 |
| NY AM pick | SED2 | ALL | 147 | -4,624 | -1,764 | +2,860 |
| Asia bare (5 mo) | SEA1 | MF1 | 73 | 51,488 | 71,478 | +19,990 |
| Asia bare (5 mo) | SEA1 | MF2 | 33 | 10,771 | 12,036 | +1,265 |
| Asia bare (5 mo) | SEA1 | MF3 | 36 | 12,312 | 287 | -12,025 |
| Asia bare (5 mo) | SEA1 | MF4 | 47 | 400 | 22,255 | +21,855 |
| Asia bare (5 mo) | SEA1 | MF5 | 83 | 57,307 | 83,527 | +26,220 |
| Asia bare | SEA1 | ALL | 272 | 132,277 | 189,582 | +57,305 |
| Asia bare (6 mo) | SEC4 | MF1 | 63 | 69,030 | 83,455 | +14,425 |
| Asia bare (6 mo) | SEC4 | MF2 | 26 | 20,983 | 21,633 | +650 |
| Asia bare (6 mo) | SEC4 | MF3 | 27 | 24,909 | 19,199 | -5,710 |
| Asia bare (6 mo) | SEC4 | MF4 | 26 | 21,133 | 33,823 | +12,690 |
| Asia bare (6 mo) | SEC4 | MF5 | 75 | 86,819 | 107,274 | +20,455 |
| Asia bare | SEC4 | ALL | 217 | 222,874 | 265,384 | +42,510 |
| NY AM bare (6 mo) | SEA1 | MF1 | 41 | -18,077 | -27,442 | -9,365 |
| NY AM bare (6 mo) | SEA1 | MF2 | 65 | -8,024 | 5,151 | +13,175 |
| NY AM bare (6 mo) | SEA1 | MF3 | 62 | -5,580 | -28,860 | -23,280 |
| NY AM bare (6 mo) | SEA1 | MF4 | 2 | 1,026 | 41 | -985 |
| NY AM bare (6 mo) | SEA1 | MF5 | 24 | 21,598 | 12,363 | -9,235 |
| NY AM bare | SEA1 | ALL | 194 | -9,058 | -38,748 | -29,690 |
| NY AM bare (6 mo) | SED2 | MF1 | 41 | -18,077 | -18,007 | +70 |
| NY AM bare (6 mo) | SED2 | MF2 | 65 | -8,024 | -3,079 | +4,945 |
| NY AM bare (6 mo) | SED2 | MF3 | 62 | -5,580 | -500 | +5,080 |
| NY AM bare (6 mo) | SED2 | MF4 | 2 | 1,026 | 576 | -450 |
| NY AM bare (6 mo) | SED2 | MF5 | 24 | 21,598 | 19,663 | -1,935 |
| NY AM bare | SED2 | ALL | 194 | -9,058 | -1,348 | +7,710 |

## WHAT I COULD NOT VERIFY
- Prior-year bands, a true rolling walk-forward and the random-entry null (no rows; counts above).
- Whether the missing 17 set-months fail on the holiday exit guard (inferred from the months only).
- London and NY PM (never run).
- That the live relay/NinjaTrader can place the replaced exit at +15 min / the stop move at the second; the engine prices the exits as a market walk of the book at the event time.
- Fees: the engine carries $1.18/lot; every number here is re-based to $4.84/lot all-in by the scorer (gross minus 4.84 x lots), same as XSESS_EXACT.

# SE addendum (scorer se_score2.py): London bare, NY PM pick JT209 (L6M) and prior years of the six finalists

### LONDON bare: TL3_SR_LO_L19201dfc_R0BRF90_30_BF2_BASE (reference = flatten, same months). Cells ratios variant/flatten L6M: ulcer / max DD / $/wk / worst week / worst day | L3M ulcer / $/wk | blocks win/lose/same

| setting | months | flatten $/wk / ulcer / max DD | ulcer x | DD x | $/wk x | worst wk x | worst day x | L3M ulcer x / $/wk x | blocks |
|---|---|---|---|---|---|---|---|---|---|
| SEA1 | 5 | 3,050/2,766/-7,836 | 1.28 | 1.33 | 0.98 | 0.65 | 1.08 | 1.41 / 0.68 | 6/5/2 |
| SEB1 | 6 | 3,265/2,673/-7,836 | 1.10 | 1.10 | 0.85 | 0.81 | 0.89 | 1.13 / 0.70 | 8/5/1 |
| SEB2 | 6 | 3,265/2,673/-7,836 | 1.15 | 1.07 | 0.82 | 0.79 | 0.94 | 1.17 / 0.68 | 6/7/1 |
| SEB3 | 6 | 3,265/2,673/-7,836 | 1.11 | 0.98 | 0.99 | 0.65 | 1.08 | 1.14 / 0.85 | 7/6/1 |
| SEB4 | 6 | 3,265/2,673/-7,836 | 1.27 | 1.33 | 0.98 | 0.65 | 1.08 | 1.38 / 0.82 | 6/7/1 |
| SEC1 | 6 | 3,265/2,673/-7,836 | 1.01 | 1.00 | 0.97 | 1.00 | 1.00 | 1.01 / 0.86 | 4/2/8 |
| SEC2 | 6 | 3,265/2,673/-7,836 | 1.00 | 1.00 | 0.99 | 1.00 | 1.00 | 1.01 / 0.94 | 2/1/11 |
| SEC3 | 6 | 3,265/2,673/-7,836 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 / 1.00 | 0/0/14 |
| SEC4 | 6 | 3,265/2,673/-7,836 | 1.01 | 1.00 | 0.98 | 1.00 | 1.00 | 1.01 / 0.97 | 0/6/8 |
| SEC5 | 6 | 3,265/2,673/-7,836 | 1.00 | 1.00 | 0.98 | 1.00 | 1.00 | 1.00 / 0.98 | 0/3/11 |
| SEC6 | 6 | 3,265/2,673/-7,836 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 / 1.00 | 0/0/14 |
| SED1 | 6 | 3,265/2,673/-7,836 | 1.00 | 0.99 | 0.98 | 1.00 | 1.00 | 1.00 / 0.98 | 5/8/1 |
| SED2 | 6 | 3,265/2,673/-7,836 | 1.00 | 0.99 | 0.99 | 1.00 | 1.00 | 0.99 / 0.99 | 5/8/1 |

### NY PM delivered pick JT209: TL3_SR_NP_STKd893133bd8_BF2_JT209 (reference = flatten, same months). Cells ratios variant/flatten L6M: ulcer / max DD / $/wk / worst week / worst day | L3M ulcer / $/wk | blocks win/lose/same

| setting | months | flatten $/wk / ulcer / max DD | ulcer x | DD x | $/wk x | worst wk x | worst day x | L3M ulcer x / $/wk x | blocks |
|---|---|---|---|---|---|---|---|---|---|
| SEA1 | 5 | 5,326/3,293/-9,660 | 1.46 | 1.34 | 0.81 | 1.09 | 1.14 | 1.14 / 0.89 | 2/11/0 |
| SEB1 | 3 | 6,063/2,046/-7,740 | 1.03 | 1.02 | 1.03 | 1.02 | 1.05 | 1.03 / 1.03 | 3/4/0 |
| SEB2 | 2 | 4,814/2,112/-7,740 | 1.12 | 1.09 | 1.07 | 1.10 | 1.06 | 1.12 / 1.07 | 2/4/0 |
| SEB3 | 5 | 5,669/3,097/-9,660 | 1.46 | 1.34 | 0.85 | 1.09 | 1.14 | 1.12 / 0.83 | 0/11/0 |
| SEB4 | 2 | 4,814/2,353/-7,740 | 1.14 | 1.08 | 0.89 | 1.09 | 1.15 | 1.14 / 0.89 | 1/5/0 |
| SEC1 | 3 | 5,296/2,454/-7,740 | 1.36 | 1.29 | 0.91 | 1.31 | 1.17 | 1.33 / 0.92 | 1/8/0 |
| SEC2 | 6 | 5,871/2,949/-9,660 | 1.21 | 1.21 | 0.97 | 1.24 | 1.05 | 1.18 / 0.98 | 6/7/1 |
| SEC3 | 6 | 5,871/2,894/-9,660 | 1.06 | 1.00 | 0.97 | 1.24 | 1.00 | 1.17 / 0.99 | 6/3/5 |
| SEC4 | 4 | 6,118/2,200/-7,740 | 1.07 | 1.11 | 1.02 | 1.11 | 1.07 | 1.06 / 0.98 | 3/7/0 |
| SEC5 | 6 | 5,871/2,883/-9,660 | 1.05 | 1.02 | 1.00 | 1.07 | 1.05 | 1.03 / 1.00 | 6/7/1 |
| SEC6 | 6 | 5,871/2,894/-9,660 | 1.01 | 1.00 | 1.00 | 1.07 | 1.00 | 1.04 / 1.01 | 6/3/5 |
| SED1 | 4 | 4,949/3,400/-9,660 | 1.07 | 1.09 | 1.05 | 1.07 | 1.05 | 1.05 / 0.97 | 2/8/0 |
| SED2 | 4 | 5,662/2,307/-8,397 | 1.00 | 0.98 | 1.02 | 1.00 | 1.02 | 1.00 / 0.97 | 5/7/0 |

### PRIOR YEARS, six finalists on the 2-lot pick (fixed setting, per year, matched months; ratio variant/flatten: ulcer, $/wk; 14-day blocks over all landed months win/lose/same)

| session | setting | months landed of 36 | 2023 | 2024 | 2025 | 2026 Jan-Apr | all history blocks |
|---|---|---|---|---|---|---|---|
| AS | SEB1 | 36 | 1.03, 0.90 (9 mo) | 1.02, 1.03 (12 mo) | 0.86, 1.45 (11 mo) | 0.96, 1.09 (4 mo) | 36/57/0 |
| AS | SEA1 | 36 | 1.62, 1.80 (9 mo) | 1.70, 1.12 (12 mo) | 1.13, 0.89 (11 mo) | 1.14, 1.09 (4 mo) | 24/69/0 |
| AS | SEC4 | 36 | 1.10, 0.55 (9 mo) | 1.05, 1.09 (12 mo) | 0.92, 1.28 (11 mo) | 1.21, 0.70 (4 mo) | 33/60/0 |
| NY | SED2 | 36 | 0.93, 0.78 (9 mo) | 1.16, 0.99 (12 mo) | 1.02, 1.08 (11 mo) | 1.07, 0.53 (4 mo) | 35/58/0 |
| NY | SEA1 | 33 | 0.77, 1.02 (8 mo) | 1.95, 0.66 (11 mo) | 1.10, 1.18 (10 mo) | 1.01, 3.40 (4 mo) | 31/53/0 |
| NY | SEC5 | 36 | 0.89, 0.95 (9 mo) | 1.21, 0.92 (12 mo) | 1.01, 1.00 (11 mo) | 1.10, -0.11 (4 mo) | 41/50/2 |

UNSCORABLE months (not landed; early-close exit-gap rule, or still running): 
- LO SEA1 months not landed: 202609
- NP SEA1 months not landed: 202609
- NP SEB1 months not landed: 202605,202606,202607
- NP SEB2 months not landed: 202605,202606,202607,202609
- NP SEB3 months not landed: 202605
- NP SEB4 months not landed: 202605,202606,202607,202609
- NP SEC1 months not landed: 202605,202607,202609
- NP SEC4 months not landed: 202605,202607
- NP SED1 months not landed: 202605,202609
- NP SED2 months not landed: 202607,202609
- NY SEA1 prior-year months UNSCORABLE (not landed): 202309,202401,202501
