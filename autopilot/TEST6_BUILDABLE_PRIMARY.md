# TEST 6: does the Test 5 primary survive on books we can actually BUILD, and what would it hold today (W-TEST6)

Written 2026-11-27 08:24Z. **QUICK SCREEN label on every number below** unless it says EXACT: grid weekly arrays (th_grid tape walk, not the exact engine), 1 NQ lot per book at $20/point, grid cost in, no stack rules, no account layers. Order: autopilot/DIRECTIVE_TEST6_2023Z.md (relay design under Josh's 18:22Z standing order, not Josh's words). The rule is the Test 5 primary EXACTLY as named (N>=100, t>=4 on weekly P&L, >=75% of fully-past half-years profitable, family share >=70%, trailing 26 weeks profitable, re-qualify every 13 weeks, hold ALL qualifiers equal weight); no new version. Code code/th_test6 (walk6.py is walk5.py with the candidate set cut and nothing else changed; with the full set it reproduces Test 5 to the dollar: Asia 178.5, London -79.6, NY AM 172.5, NY PM 190.4, four summed 135.3 $/lot/wk). Data: server C /mnt/l2/l2vast/_test6/out, copies on box 1 /mnt/l2/l2vast/_test6. Same span as Test 5 (160 weeks, 2023-10-01 to 2026-10-25). Because this is a robustness check of one named rule, no best-of penalty; p = plain one-sided block bootstrap vs zero (block 4 weeks, 2,000 draws), PASS = above zero with p <= 0.10, as in Test 5.

## ANSWER FIRST

1. **The pass survives on buildable books, in the sum and in Asia; it is thinner in NY AM.** Candidate set (3) (print-rule bar types dropped AND stale level cells dropped): four sessions summed **+139 $/lot/wk, p 0.072, PASS** (full set +135, p 0.072); Asia **+148, p 0.070, PASS** (full +178, p 0.026); **NY AM +166, p 0.106, FAIL by 0.006** (full +172, p 0.096 PASS: the pass is on the edge in both); NY PM +276, p 0.091 (flips to PASS from +190, p 0.138; 8 to 29 books, do not lean on it); London -127, p 0.86 FAIL (as before). So only the NY AM single-session pass is lost, and only by a hair; nothing else disappears. Recent first, four summed, set (3) vs full: L3M +248 vs +221, L6M +124 vs +76, 2026 (Jan-Oct) +24 vs -5, 2025 +271 vs +275, 2024 +142 vs +154, 2023 Q4 -34 vs -55; max drawdown 12,227 vs 11,774 $/lot. Asia set (3): L3M +277, L6M +475, 2026 +301, 2025 +80, 2024 +106 (full set: 2025 130, 2024 167): the Asia recent half-year is the same or better, the earlier years are weaker.
2. **Print-rule bar types are NOT what carries the result.** Dropping them alone (set 1) keeps the basket at 2,149 books ever (of 4,075) and changes the sum to +147 (p 0.062); the dropped types were 46% of the Asia candidate cells and 39% of the NY AM cells but were not what earned the result. **Stale level cells hardly matter either** (set 2: about 2% of candidate cells dropped; sum +132, p 0.077; Asia +176, NY AM +166, NY PM +185).
3. **BUT the result depends on one module family: the level modules (trig_levels_*).** In the full-set primary the levels are 52-53% of the books held and **91% of the four-session P&L (Asia 70%, NY AM 85%, London 68%, NY PM 106%)**. With the levels removed from the held baskets (static removal, no refilling) the sum falls to **+79 (p 0.26, L6M -90)** on the full set and **+97 (p 0.21, L6M -32)** on set (3); Asia to +139 (p 0.096) full / +108 (p 0.147) set (3); NY AM to +90 (p 0.28) / +108 (p 0.25). The pass disappears without the levels. The largest BAR TYPE is not a dependence: removing tsf (the largest bar type in the sum, 8-15% of the books, 2% of the P&L) leaves the sum at +136 (p 0.073) full / +147 (p 0.067) set (3). The levels are also the family most affected by the 18 Nov module fixes (grid results older than 2026-11-18 06:00Z are stale), which is why part A (2) matters: only about 2% of candidate cells were stale, so that exposure is small in this basket, but the family fix is still unfinished for the whole level result and the 13 modules were NOT re-verified here (dropped instead).
4. **THE LIST TODAY (set 3, the books the primary holds from the last re-qualify date, week 182, 2026-10-04 to 2026-10-25): Asia 197 books (150 near-twin groups, 138 long only, all with L6M above zero, 175 with L3M above zero, 128 still qualify at the last data date), NY AM 76 books (67 with L6M > 0, 60 with L3M > 0, 53 still qualify).** Marks: Asia 12 share module+variant with a D8Asia.cs book, 4 are twins of the live Asia book vwap break, 181 new; NY AM 6 twins of live books, 70 new; none is a cell-for-cell match of a live book (the relay confirms the D8Asia.cs ones). Exact numbers for these books come from Q1 as it lands (marked EXACT in the table when all 42 months have landed; none had at the time of writing).
5. **SIX STACKS FIXED TODAY (seed 20261127, never re-drawn, autopilot/FORWARD_REGISTER_STACKS.md): Asia A1, A2, A3 and NY AM N1, N2, N3, six books each, at most one per module family and per near-twin group.** Quick-screen $/lot/wk of the equal-weight six, 2023-04 to 2026-10, in sample (hindsight list, all books were picked from their own past): A1 518, A2 597, A3 461, N1 995, N2 974, N3 986. These are in-sample for the whole history; the register scores them from now on, forward only.
6. **EXACT (part D): rows QUEUED; stacks 504 of 504 set-months landed, primary held cells (set 3) 10145 of 10145 set-months landed (status at 2026-11-27 08:24Z).** Rows are appended the moment Test 5's rows are queued (waiter queue_chain6.sh polls every 5 s, before W-Q0's 60 s poll), ahead of Q0's NY AM / NY PM / London rows and Q1. Measured ETA in MORNING.md.

## PART A: the primary re-run on the buildable candidate sets (QUICK SCREEN)

| session | candidate set | $/lot/wk | plain bootstrap p (one-sided, no best-of penalty) | verdict | L3M | L6M | max DD $/lot | 2023 Q4 | 2024 | 2025 | 2026 | books held first / mean / last | books ever |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | full set (the Test 5 primary) | 178 | 0.026 | **PASS** | 221 | 428 | 7083 | 88 | 167 | 130 | 283 | 18 / 163 / 388 | 1641 |
| Asia | (1) buildable bar types only (print-rule types dropped) | 160 | 0.054 | **PASS** | 287 | 485 | 9504 | 98 | 140 | 82 | 303 | 9 / 73 / 196 | 716 |
| Asia | (2) verified modules only (level cells with a pre-2026-11-18 06:00Z grid file dropped) | 176 | 0.027 | **PASS** | 215 | 423 | 7013 | 88 | 161 | 129 | 282 | 16 / 162 / 389 | 1634 |
| Asia | (3) both | 148 | 0.070 | **PASS** | 277 | 475 | 9493 | 102 | 106 | 80 | 301 | 7 / 72 / 197 | 712 |
| London | full set (the Test 5 primary) | -80 | 0.833 | **FAIL** | -231 | -26 | 14344 | -198 | -20 | -120 | -65 | 146 / 29 / 11 | 330 |
| London | (1) buildable bar types only (print-rule types dropped) | -129 | 0.863 | **FAIL** | -467 | -175 | 22482 | -213 | -57 | -157 | -155 | 78 / 17 / 7 | 192 |
| London | (2) verified modules only (level cells with a pre-2026-11-18 06:00Z grid file dropped) | -79 | 0.831 | **FAIL** | -231 | -26 | 14260 | -188 | -21 | -120 | -65 | 147 / 29 / 11 | 334 |
| London | (3) both | -127 | 0.856 | **FAIL** | -467 | -175 | 22108 | -193 | -55 | -157 | -155 | 79 / 17 / 7 | 196 |
| NY AM | full set (the Test 5 primary) | 172 | 0.096 | **PASS** | 251 | -87 | 22269 | 21 | 243 | 382 | -133 | 231 / 222 / 125 | 1900 |
| NY AM | (1) buildable bar types only (print-rule types dropped) | 177 | 0.088 | **PASS** | 338 | 20 | 20767 | 62 | 207 | 358 | -51 | 142 / 129 / 80 | 1124 |
| NY AM | (2) verified modules only (level cells with a pre-2026-11-18 06:00Z grid file dropped) | 166 | 0.100 | **PASS** | 181 | -119 | 22163 | 21 | 246 | 375 | -153 | 231 / 221 / 121 | 1894 |
| NY AM | (3) both | 166 | 0.106 | **FAIL** | 225 | -29 | 20533 | 62 | 209 | 346 | -82 | 142 / 128 / 76 | 1118 |
| NY PM | full set (the Test 5 primary) | 190 | 0.138 | **FAIL** | 243 | 516 | 23441 | -36 | 37 | 595 | -59 | 43 / 22 / 11 | 204 |
| NY PM | (1) buildable bar types only (print-rule types dropped) | 284 | 0.087 | **PASS** | 180 | 693 | 26279 | -72 | -52 | 935 | -12 | 29 / 13 / 8 | 117 |
| NY PM | (2) verified modules only (level cells with a pre-2026-11-18 06:00Z grid file dropped) | 185 | 0.144 | **FAIL** | 243 | 516 | 23441 | -57 | 26 | 595 | -59 | 43 / 22 / 11 | 204 |
| NY PM | (3) both | 276 | 0.091 | **PASS** | 180 | 693 | 26279 | -103 | -69 | 935 | -12 | 29 / 13 / 8 | 117 |
| Four sessions summed | full set (the Test 5 primary) | 135 | 0.072 | **PASS** | 221 | 76 | 11774 | -55 | 154 | 275 | -5 | 438 / 436 / 535 | 4075 |
| Four sessions summed | (1) buildable bar types only (print-rule types dropped) | 147 | 0.062 | **PASS** | 289 | 142 | 12484 | -35 | 147 | 280 | 34 | 258 / 232 / 291 | 2149 |
| Four sessions summed | (2) verified modules only (level cells with a pre-2026-11-18 06:00Z grid file dropped) | 132 | 0.077 | **PASS** | 198 | 65 | 11651 | -54 | 153 | 269 | -11 | 437 / 434 / 532 | 4066 |
| Four sessions summed | (3) both | 139 | 0.072 | **PASS** | 248 | 124 | 12227 | -34 | 142 | 271 | 24 | 257 / 231 / 288 | 2143 |

How the sets are cut (walk6.py, same walk as Test 5; only the candidate cells change): (1) **buildable bar types**: grid cells whose bar type is a print-rule type (vol, vsess, tick, dlt, dol, cdr, dib, tib, vib, drb, trb, vrb, mom, cusum, vnorm, trend, wrenko; the AFF list of ROTATION_STAGE_B.md, whose exact events are NOT live-identical) are removed from the candidates; (2) **verified modules**: every trig_levels_* grid file written before 2026-11-18 06:00Z (the UNVER rule of stage B / SURVIVOR_COUNTS: "13 of 17 level modules differ on a fresh re-run") is removed; this is per grid file (the module list of the 13 is not published as such, so every pre-cutoff level file was dropped, which covers them); re-verification (a fresh grid run of those files) was NOT done (not cheap: it is the fleet's stale-level re-run, still in progress), so they are dropped, not re-verified; (3) both. The family share (>=70% of a family's cells profitable) is computed over the cells that remain in the set, the one-cell-per-book and one-book-per-family steps are unchanged. Candidate cells: full 14.5M (Asia), set 1 7.8M, set 2 14.2M, set 3 7.5M.

Reading: the pass is not an artefact of print-rule bar types or of stale level files. Per-session verdicts flip only at the edge (NY AM 0.096 -> 0.106, NY PM 0.138 -> 0.091). The basket for set (3) is about half the size (about 231 books held on average, 288 at the last date) and equally spread over the same module families.

## PART B: does it depend on a few modules (QUICK SCREEN)

Static removal: the primary's held books of the largest group are removed from every basket and the rest is re-averaged per lot (the walk is NOT re-run without the group, so no refilling by other books; this is the dependence of the realised basket, not a new rule).

### Full set (the Test 5 primary): without the largest group

| session | cut | largest group by share of books (share of books / share of P&L) | $/lot/wk without it | plain p | L3M | L6M | max DD | 2026 | books held mean | full-set value $/lot/wk |
|---|---|---|---|---|---|---|---|---|---|---|
| Asia | largest module family removed | trig_levels (52% / 70%) | 139 | 0.096 | 98 | 287 | 10901 | 137 | 72.8 | 178 |
| Asia | largest bar type removed | tsf (14% / 9%) | 177 | 0.026 | 220 | 415 | 7075 | 283 | 130.2 | 178 |
| Asia | largest bar type removed (largest by P&L) | dol (4% / 11%) | 165 | 0.037 | 213 | 395 | 7335 | 256 | 145.1 | 178 |
| London | largest module family removed | trig_levels (50% / 68%) | -54 | 0.744 | -260 | -103 | 14437 | -113 | 14.6 | -80 |
| London | largest module family removed (largest by P&L) | trig_barnative (1% / -12%) | -92 | 0.864 | -231 | -26 | 16307 | -65 | 29.2 | -80 |
| London | largest bar type removed | tsf (8% / 23%) | -67 | 0.781 | -223 | -12 | 13395 | 5 | 27.4 | -80 |
| London | largest bar type removed (largest by P&L) | dol (5% / -16%) | -91 | 0.866 | -458 | -204 | 14503 | -141 | 28.2 | -80 |
| NY AM | largest module family removed | trig_levels (51% / 85%) | 90 | 0.279 | 122 | -296 | 26025 | -280 | 109.3 | 172 |
| NY AM | largest bar type removed | swing (6% / 11%) | 163 | 0.107 | 132 | -172 | 22771 | -195 | 214.4 | 172 |
| NY PM | largest module family removed | trig_levels (79% / 106%) | -179 | 0.924 | 0 | 0 | 35564 | -426 | 7.6 | 190 |
| NY PM | largest bar type removed | tick (11% / 4%) | 210 | 0.134 | 190 | 578 | 26189 | -75 | 20.1 | 190 |
| NY PM | largest bar type removed (largest by P&L) | dchg (7% / 38%) | 130 | 0.198 | 351 | 369 | 23137 | -119 | 21.0 | 190 |
| Four sessions summed | largest module family removed | trig_levels (53% / 91%) | 79 | 0.262 | 104 | -90 | 16603 | -138 | 201.7 | 135 |
| Four sessions summed | largest bar type removed | tsf (8% / 2%) | 136 | 0.073 | 232 | 71 | 12317 | -17 | 397.8 | 135 |
| Four sessions summed | largest bar type removed (largest by P&L) | kagi (3% / 17%) | 133 | 0.071 | 210 | 70 | 11539 | -8 | 416.9 | 135 |

### Full set: share of the basket and of its P&L by module family and by bar type (all re-qualify dates pooled, top 8)

| session | cut | group | share of books (all dates) | share of P&L ($, dollar-weighted by basket size) |
|---|---|---|---|---|
| Asia | module family | trig_levels | 52% | 70% |
| Asia | module family | trig_bands | 14% | 8% |
| Asia | module family | trig_momentum | 14% | 21% |
| Asia | module family | trig_trend | 7% | 3% |
| Asia | module family | trig_tape | 3% | 2% |
| Asia | module family | trig_structure | 3% | 2% |
| Asia | module family | trig_book | 2% | -7% |
| Asia | module family | trig_pullback | 1% | 1% |
| Asia | bar type | tsf | 14% | 9% |
| Asia | bar type | tick | 8% | 10% |
| Asia | bar type | vol | 7% | 6% |
| Asia | bar type | time | 6% | 6% |
| Asia | bar type | vsess | 5% | 4% |
| Asia | bar type | cdr | 4% | 1% |
| Asia | bar type | dol | 4% | 11% |
| Asia | bar type | dlt | 4% | -1% |
| London | module family | trig_levels | 50% | 68% |
| London | module family | trig_bands | 15% | -4% |
| London | module family | trig_xmarket | 9% | 7% |
| London | module family | trig_book | 7% | 34% |
| London | module family | trig_tape | 5% | 3% |
| London | module family | trig_momentum | 5% | 5% |
| London | module family | trig_trend | 4% | 1% |
| London | module family | trig_structure | 3% | -1% |
| London | bar type | tsf | 8% | 23% |
| London | bar type | typ | 6% | -5% |
| London | bar type | dol | 5% | -16% |
| London | bar type | trb | 4% | 7% |
| London | bar type | vol | 4% | 14% |
| London | bar type | t3 | 4% | 10% |
| London | bar type | vrb | 4% | 8% |
| London | bar type | time | 4% | 5% |
| NY AM | module family | trig_levels | 51% | 85% |
| NY AM | module family | trig_book | 16% | 6% |
| NY AM | module family | trig_bands | 15% | 9% |
| NY AM | module family | trig_momentum | 6% | 1% |
| NY AM | module family | trig_structure | 4% | -0% |
| NY AM | module family | trig_tape | 2% | -1% |
| NY AM | module family | trig_pullback | 2% | 1% |
| NY AM | module family | trig_trend | 2% | -2% |
| NY AM | bar type | swing | 6% | 11% |
| NY AM | bar type | vsess | 6% | 3% |
| NY AM | bar type | time | 5% | 10% |
| NY AM | bar type | tick | 4% | 9% |
| NY AM | bar type | kagi | 4% | 2% |
| NY AM | bar type | tsf | 4% | 1% |
| NY AM | bar type | pnf | 4% | 8% |
| NY AM | bar type | vrb | 4% | 1% |
| NY PM | module family | trig_levels | 79% | 106% |
| NY PM | module family | trig_book | 6% | -8% |
| NY PM | module family | trig_tape | 5% | 6% |
| NY PM | module family | trig_xmarket | 3% | -8% |
| NY PM | module family | trig_momentum | 3% | 5% |
| NY PM | module family | trig_trend | 2% | 1% |
| NY PM | module family | trig_bands | 2% | -2% |
| NY PM | module family | trig_confluence | 0% | 0% |
| NY PM | bar type | tick | 11% | 4% |
| NY PM | bar type | dchg | 7% | 38% |
| NY PM | bar type | time | 6% | -5% |
| NY PM | bar type | vsess | 6% | 9% |
| NY PM | bar type | kagi | 6% | 38% |
| NY PM | bar type | tsf | 5% | 4% |
| NY PM | bar type | vol | 5% | 14% |
| NY PM | bar type | rng | 4% | 1% |
| Four sessions summed | module family | trig_levels | 53% | 91% |
| Four sessions summed | module family | trig_bands | 14% | 6% |
| Four sessions summed | module family | trig_book | 10% | -9% |
| Four sessions summed | module family | trig_momentum | 9% | 9% |
| Four sessions summed | module family | trig_trend | 4% | 1% |
| Four sessions summed | module family | trig_structure | 3% | 1% |
| Four sessions summed | module family | trig_tape | 3% | 2% |
| Four sessions summed | module family | trig_pullback | 1% | 1% |
| Four sessions summed | bar type | tsf | 8% | 2% |
| Four sessions summed | bar type | tick | 6% | 8% |
| Four sessions summed | bar type | vol | 5% | 7% |
| Four sessions summed | bar type | time | 5% | 3% |
| Four sessions summed | bar type | vsess | 5% | 7% |
| Four sessions summed | bar type | swing | 4% | 5% |
| Four sessions summed | bar type | vrb | 3% | -0% |
| Four sessions summed | bar type | dchg | 3% | 16% |

### Set (3): without the largest group

| session | cut | largest group by share of books (share of books / share of P&L) | $/lot/wk without it | plain p | L3M | L6M | max DD | 2026 | books held mean | full-set value $/lot/wk |
|---|---|---|---|---|---|---|---|---|---|---|
| Asia | largest module family removed | trig_levels (54% / 62%) | 108 | 0.147 | 172 | 385 | 10043 | 202 | 32.7 | 148 |
| Asia | largest bar type removed | tsf (31% / 23%) | 149 | 0.067 | 305 | 471 | 10404 | 314 | 45.2 | 148 |
| London | largest module family removed | trig_levels (42% / 49%) | -107 | 0.821 | -414 | -148 | 20006 | -139 | 10.2 | -127 |
| London | largest module family removed (largest by P&L) | trig_bands (23% / -1%) | -113 | 0.819 | -467 | -175 | 24745 | -155 | 13.5 | -127 |
| London | largest bar type removed | tsf (13% / 31%) | -109 | 0.806 | -781 | -298 | 21644 | -81 | 15.6 | -127 |
| London | largest bar type removed (largest by P&L) | rng (4% / -15%) | -161 | 0.909 | -478 | -140 | 25816 | -274 | 17.0 | -127 |
| NY AM | largest module family removed | trig_levels (50% / 81%) | 108 | 0.245 | 54 | -263 | 24012 | -283 | 64.1 | 166 |
| NY AM | largest bar type removed | swing (10% / 20%) | 149 | 0.129 | 11 | -175 | 21634 | -187 | 117.6 | 166 |
| NY PM | largest module family removed | trig_levels (75% / 102%) | -152 | 0.904 | 0 | 0 | 37592 | -426 | 6.1 | 276 |
| NY PM | largest bar type removed | dchg (11% / 44%) | 201 | 0.145 | 318 | 556 | 25714 | -69 | 12.3 | 276 |
| NY PM | largest bar type removed (largest by P&L) | kagi (9% / 44%) | 191 | 0.157 | 211 | 532 | 25707 | -83 | 12.5 | 276 |
| Four sessions summed | largest module family removed | trig_levels (52% / 96%) | 97 | 0.214 | 114 | -32 | 15322 | -125 | 107.9 | 139 |
| Four sessions summed | largest bar type removed | tsf (15% / 2%) | 147 | 0.067 | 282 | 132 | 13545 | 13 | 195.5 | 139 |
| Four sessions summed | largest bar type removed (largest by P&L) | kagi (6% / 28%) | 136 | 0.072 | 229 | 115 | 11904 | 20 | 214.5 | 139 |

### Set (3): shares

| session | cut | group | share of books (all dates) | share of P&L ($, dollar-weighted by basket size) |
|---|---|---|---|---|
| Asia | module family | trig_levels | 54% | 62% |
| Asia | module family | trig_bands | 14% | 9% |
| Asia | module family | trig_momentum | 11% | 20% |
| Asia | module family | trig_trend | 8% | 7% |
| Asia | module family | trig_structure | 4% | 4% |
| Asia | module family | trig_tape | 2% | 4% |
| Asia | module family | trig_book | 1% | -7% |
| Asia | module family | trig_manual | 1% | -3% |
| Asia | bar type | tsf | 31% | 23% |
| Asia | bar type | time | 13% | 14% |
| Asia | bar type | renko | 8% | 8% |
| Asia | bar type | lbrk | 6% | 4% |
| Asia | bar type | frenko | 5% | 12% |
| Asia | bar type | swing | 5% | 5% |
| Asia | bar type | dchg | 5% | 2% |
| Asia | bar type | urenko | 4% | 3% |
| London | module family | trig_levels | 42% | 49% |
| London | module family | trig_bands | 23% | -1% |
| London | module family | trig_tape | 8% | 8% |
| London | module family | trig_xmarket | 8% | 18% |
| London | module family | trig_book | 7% | 16% |
| London | module family | trig_momentum | 6% | 6% |
| London | module family | trig_trend | 5% | 5% |
| London | module family | trig_manual | 1% | -1% |
| London | bar type | tsf | 13% | 31% |
| London | bar type | typ | 11% | -6% |
| London | bar type | time | 7% | 6% |
| London | bar type | t3 | 7% | 12% |
| London | bar type | dchg | 4% | 2% |
| London | bar type | rng | 4% | -15% |
| London | bar type | bmsg | 4% | 3% |
| London | bar type | kagi | 4% | -0% |
| NY AM | module family | trig_levels | 50% | 81% |
| NY AM | module family | trig_book | 17% | 5% |
| NY AM | module family | trig_bands | 14% | 9% |
| NY AM | module family | trig_momentum | 6% | 4% |
| NY AM | module family | trig_structure | 4% | 3% |
| NY AM | module family | trig_tape | 2% | -1% |
| NY AM | module family | trig_trend | 2% | -3% |
| NY AM | module family | trig_pullback | 2% | 2% |
| NY AM | bar type | swing | 10% | 20% |
| NY AM | bar type | time | 8% | 18% |
| NY AM | bar type | kagi | 7% | 4% |
| NY AM | bar type | tsf | 7% | 3% |
| NY AM | bar type | pasl | 6% | 0% |
| NY AM | bar type | lbrk | 6% | 10% |
| NY AM | bar type | dchg | 6% | 2% |
| NY AM | bar type | pnf | 5% | 5% |
| NY PM | module family | trig_levels | 75% | 102% |
| NY PM | module family | trig_book | 8% | -9% |
| NY PM | module family | trig_tape | 6% | 7% |
| NY PM | module family | trig_xmarket | 4% | -6% |
| NY PM | module family | trig_momentum | 3% | 6% |
| NY PM | module family | trig_trend | 2% | 1% |
| NY PM | module family | trig_bands | 1% | -1% |
| NY PM | module family | trig_confluence | 1% | 0% |
| NY PM | bar type | dchg | 11% | 44% |
| NY PM | bar type | time | 10% | -4% |
| NY PM | bar type | kagi | 9% | 44% |
| NY PM | bar type | tsf | 8% | 3% |
| NY PM | bar type | rng | 6% | 2% |
| NY PM | bar type | swing | 6% | 2% |
| NY PM | bar type | vfp | 6% | 16% |
| NY PM | bar type | frenko | 5% | 6% |
| Four sessions summed | module family | trig_levels | 52% | 96% |
| Four sessions summed | module family | trig_bands | 14% | 6% |
| Four sessions summed | module family | trig_book | 11% | -10% |
| Four sessions summed | module family | trig_momentum | 7% | 10% |
| Four sessions summed | module family | trig_trend | 4% | 0% |
| Four sessions summed | module family | trig_structure | 3% | 2% |
| Four sessions summed | module family | trig_tape | 3% | 3% |
| Four sessions summed | module family | trig_xmarket | 1% | -8% |
| Four sessions summed | bar type | tsf | 15% | 2% |
| Four sessions summed | bar type | time | 10% | 7% |
| Four sessions summed | bar type | swing | 8% | 10% |
| Four sessions summed | bar type | dchg | 6% | 27% |
| Four sessions summed | bar type | kagi | 6% | 28% |
| Four sessions summed | bar type | lbrk | 5% | 3% |
| Four sessions summed | bar type | pasl | 5% | -2% |
| Four sessions summed | bar type | renko | 5% | 3% |

Reading: **the levels (trig_levels_*) carry the result** (about half the books, 70-106% of the P&L per session, 91-96% of the summed P&L); without them the four-session sum is +79 / +97 $/lot/wk with a negative L6M and p 0.21-0.26. No single bar type does (tsf, kagi, dchg, swing, tick are the largest; removing any leaves the sum within +/-10 $). Static removal overstates the loss a refilled basket would show (a re-run without levels would refill from the other families), and the levels' share of P&L is also a share of the books, so part of this is just that most qualifiers are level books; but the order is clear: this result is a levels result, and the levels are the family with the unfinished staleness fix. "Share of P&L" is the group's contribution to the equal-weight per-lot series (group P&L divided by the books held that date), pooled over the 13-week hold periods; shares above 100% mean the other families lost money in total (NY PM). The "largest by P&L" extra rows appear when the largest group by P&L differs from the largest by books.

## PART C: the list today and the six fixed stacks

Rule of the list: the books the primary (unchanged) holds on set (3) from the last re-qualify date (week 182, hold 2026-10-04 to 2026-10-25, the last data date); "still qualifies at the last data date" is a separate flag (Asia 128 of 197, NY AM 53 of 76 re-pass the cell rule one more time at the end). Columns: trades and t are over the whole 186 weeks (QUICK SCREEN, 1 lot, $20/pt, weekly t-stat incl. zero weeks); $/lot/wk by calendar year 2023 (from April), 2024, 2025, 2026 (to Oct); L6M / L3M = last 26 / 13 weeks. **Source "EXACT" = bare R0, 1 lot, all 42 months landed in the engine (Q1 or this test's rows); else "quick".** Near-twin groups (T..) = same module, variant, side and bar type (different size / bracket / params) or same module family and side with weekly P&L correlation >= 0.9; the number in brackets is the group size. Marks: "new" / "twin of live book X" (same module, variant and side as a live book of the session, different bar or params) / "module+variant also in D8Asia.cs" (Asia only; the relay confirms the book) / "LIVE-CELL" (identical grid cell to a live book; none found). **Caveats the reader needs:** (a) the list is hindsight-chosen on the same history it is scored on (full-history columns are in sample; the forward register is the test); (b) 70% of the Asia list is long only (138 of 197) and the span is a rising market, so the long-only books ride it; (c) 2026 is above zero for 197 of 197 Asia books and 75 of 76 NY AM books, which is partly what the trailing-26-week gate selects; (d) the 76 NY AM books are dominated by levels (23), bands (21) and book (15) modules; the Asia list by levels (111 of 197), bands (31), momentum (15), trend (14).

**Draw (seed 20261127, fixed):** numpy default_rng(20261127); books sorted by book id; per stack a fresh permutation from the same generator, A1, A2, A3, then N1, N2, N3; scan the permutation and take a book if its module family (trig_levels, trig_bands, ...) and its near-twin group are not yet in the stack, stop at 6; later stacks avoid books used by earlier ones (disjoint) unless six distinct families cannot be completed, which happened once: **N3 shares one book (We52cf06e, pullback_ema count) with N1**, because NY AM has only 7 module families and two of them have a single book. Nothing is re-drawn or swapped.

### The six stacks (details and book ids: autopilot/FORWARD_REGISTER_STACKS.md)

| stack | session | book ids (module, variant, bar type and size, bracket, side) | quick-screen $/lot/wk of the 6 books (equal weight, 2023-04..2026-10, no stack rules) | exact 42-month sets |
|---|---|---|---|---|
| A1 | Asia | Wabef8f99 (bands_donchian, break, time m_5, fixed40/80, long); W5d77f657 (trend_ma_sma, price, dchg 28, fixed90/30, long); Wa7df403e (levels_ob15, false_break_native, tsf 10_60, plain60/60, both); W450ab188 (momentum_mvote, v3of5, time m_3, fixed45/45, both); W57c26903 (pullback_ema, depth_native, tsf 25_40, plain60/60, both); W6d582cbb (confluence_xfam, bandflow, tsf 5_100, plain60/60, long) | 518 (L6M 1156, L3M 901) | TL3_SR_AS_T6A1_BARE / _LY |
| A2 | Asia | W109eb056 (bands_regchan, break_stderr_native, frenko 28, plain60/60, long); W852ce40a (levels_channel, break, frenko 28, fixed60/120, long); Wd116f43b (trend_ma_kama, price, renko 28, fixed40/80, long); W38c5305e (tape_sizemix, small_follow, swing atr_0.4, fixed45/45, both); W7c41e0e4 (structure_fvg, cont, tsf 5_100, plain60/60, long); Wbc4f3415 (barnative_avwap, cross, tsf 10_120, plain60/60, both) | 597 (L6M 1130, L3M 734) | TL3_SR_AS_T6A2_BARE / _LY |
| A3 | Asia | W5c3bfff6 (momentum_rsi, mom_native, tsf 25_20, plain60/60, long); W98254c75 (bands_keltner, walk, swing pct_5, fixed30/90, long); W142a885f (xmarket_es, confirm, renko 56, fixed90/30, long); W527709cc (manual_macd, zero, renko 28, fixed90/30, long); W0fe67991 (levels_vwap, break, lbrk 3_10, plain60/60, both); Wef2e1364 (trend_ma_kama, cross_native, pasl 10, fixed90/90, long) | 461 (L6M 859, L3M 519) | TL3_SR_AS_T6A3_BARE / _LY |
| N1 | NY AM | W43af5f5a (book_ofi, follow, pnf 14, fixed90/30, short); Wbcfa80fb (levels_prior_day, false_break, swing atr_0.25, fixed120/120, both); Wc0f0a762 (momentum_roc, break_native, swing atr_0.15, asym10u/20u, both); W3f23fbd1 (structure_level, sopen_cross, t3 bmsgq_B200, sym15u, long); W2b1bc7e6 (bands_keltner, walk_native, tm20 , fixed120/60, both); We52cf06e (pullback_ema, count, volor B030, fixed120/60, long) | 995 (L6M 1215, L3M 1077) | TL3_SR_NY_T6N1_BARE / _LY |
| N2 | NY AM | W6a8993ed (bands_atrchan, break_ema, bmsg B030, fixed60/120, both); Wbc90b09f (momentum_stoch, zone_break_native, swing atr_0.15, asym10u/20u, both); W01dfc899 (levels_ob5, break_native, pasl 14, fixed90/90, long); W2d6065cd (book_ofi, follow_sm, tsf 25_40, sym15u, both); W27c4dbd9 (structure_level, sopen_cross, kal volor_B200, asym10u/20u, long); W20980087 (live_seven, O7, renko 14, fixed30/90, both) | 974 (L6M 682, L3M 361) | TL3_SR_NY_T6N2_BARE / _LY |
| N3 | NY AM | Wf74d00e3 (levels_prior_day, false_break, dchg 20, fixed120/120, both); Wa3f069eb (book_ofi, follow_sm, swing atr_0.9, fixed120/60, both); We52cf06e (pullback_ema, count, volor B030, fixed120/60, long); W02b31e1f (bands_regchan, break_stderr_native, micro B030, fixed30/30, short); Waaa5a0bf (momentum_stoch, zone_break, swing atr_0.15, sym15u, both); W29a0680a (structure_level, sopen_cross, volor B080, sym15u, both) | 986 (L6M 1469, L3M 1060) | TL3_SR_NY_T6N3_BARE / _LY |

## The list (sorted by L3M; quick screen unless the source column says EXACT)

### Asia: 197 books held at the last re-qualify date (week 182, hold to 2026-10-25), set (3), near-twin groups 150; exact (42 months landed): 0 of 197

| book id | module | variant | bar type and size | bracket | side | trades | t | $/lot/wk full history | 2023 / 2024 / 2025 / 2026 $/lot/wk | L6M | L3M | source | twin group (size) | mark | stack |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Wd3a72355 | trig_levels_mmove | retest | tsf 5_400 | plain60/60 | both | 987 | 4.7 | 680 | 138 / 335 / 440 / 1914 | 2360 | 2732 | quick | T175 (2) | new |  |
| W16b75d89 | trig_levels_mmove | retest_native | tsf 5_400 | plain60/60 | both | 987 | 4.7 | 680 | 138 / 335 / 440 / 1914 | 2360 | 2732 | quick | T175 (2) | new |  |
| W601363ff | trig_levels_stack | break_native | tsf 5_50 | plain60/60 | both | 1771 | 4.3 | 1023 | -84 / 447 / 1283 / 2434 | 3072 | 2659 | quick | T78 (1) | new |  |
| We0dbec32 | trig_levels_fibr_pd | break_native | lbrk 5_10 | fixed60/120 | both | 1421 | 4.1 | 1191 | -175 / 816 / 1424 / 2628 | 3118 | 2160 | quick | T39 (1) | new |  |
| Wf06d4bb3 | trig_levels_vwap | retest | swing atr_0.1 | sym30u | both | 1140 | 4.2 | 1065 | 475 / -232 / 1233 / 3010 | 2729 | 2105 | quick | T129 (1) | new |  |
| W734be63f | trig_levels_channel | break_native | tsf 10_60 | plain60/60 | both | 1316 | 4.7 | 814 | 79 / 610 / 835 / 1724 | 1823 | 2045 | quick | T154 (1) | new |  |
| W73585da1 | trig_levels_vwap | retest | pnf 7 | fixed120/120 | both | 1078 | 4.6 | 988 | 340 / -61 / 1046 / 2817 | 2618 | 2026 | quick | T109 (1) | new |  |
| We9465e26 | trig_xmarket_es | confirm | tm900  | fixed60/120 | both | 1375 | 4.2 | 984 | -185 / 432 / 1041 / 2682 | 2836 | 2001 | quick | T151 (1) | new |  |
| W450ab188 | trig_momentum_mvote | v3of5 | time m_3 | fixed45/45 | both | 1303 | 4.5 | 635 | 118 / 333 / 495 / 1666 | 1985 | 1972 | quick | T139 (2) | new | A1 |
| W44df5e4b | trig_momentum_mvote | v3of5_native | time m_3 | fixed45/45 | both | 1303 | 4.5 | 635 | 118 / 333 / 495 / 1666 | 1985 | 1972 | quick | T139 (2) | new |  |
| W3b27190e | trig_xmarket_rty | confirm | tm900  | fixed30/90 | both | 1305 | 3.8 | 604 | -2 / 527 / 365 / 1565 | 1938 | 1876 | quick | T150 (1) | new |  |
| W7b547d88 | trig_barnative_speed | burst_go | tsf 2_200 | sym15u | both | 1101 | 4.0 | 935 | 196 / 505 / 1036 / 2026 | 1913 | 1866 | quick | T165 (1) | new |  |
| Wa5114ebe | trig_levels_swsr5 | break_native | pnf 5 | asym10u/20u | long | 794 | 4.1 | 736 | 320 / 565 / 894 / 1137 | 1261 | 1855 | quick | T108 (1) | new |  |
| W7bd2e40a | trig_levels_fibr_on | false_break | renko 14 | sym30u | long | 109 | 4.4 | 374 | 75 / 324 / 178 / 960 | 1390 | 1752 | quick | T117 (2) | new |  |
| W420ce4c8 | trig_levels_round | break | tsf 5_100 | plain60/60 | long | 852 | 4.5 | 696 | 177 / 508 / 776 / 1308 | 1739 | 1745 | quick | T76 (3) | new |  |
| W38c5305e | trig_tape_sizemix | small_follow | swing atr_0.4 | fixed45/45 | both | 2676 | 4.2 | 831 | 99 / 628 / 949 / 1613 | 2104 | 1716 | quick | T130 (1) | new | A2 |
| Wf2c8d1b2 | trig_levels_sdx3 | retest | lbrk 3_20 | sym15u | long | 170 | 4.7 | 401 | -56 / 115 / 500 / 1053 | 1600 | 1689 | quick | T95 (1) | new |  |
| W2f37513b | trig_levels_fibr_on | false_break_native | renko 14 | sym30u | long | 105 | 4.3 | 352 | 87 / 298 / 178 / 886 | 1208 | 1649 | quick | T117 (2) | new |  |
| Wef2e1364 | trig_trend_ma_kama | cross_native | pasl 10 | fixed90/90 | long | 188 | 4.3 | 357 | 26 / 130 / 371 / 929 | 1440 | 1626 | quick | T103 (1) | new | A3 |
| Wd115806b | trig_momentum_er | trend | mrenko 20 | fixed60/120 | long | 741 | 4.4 | 809 | 280 / 620 / 724 / 1639 | 2090 | 1624 | quick | T98 (1) | new |  |
| W5cb84492 | trig_levels_round | break_native | tsf 5_100 | plain60/60 | long | 843 | 4.9 | 736 | 164 / 535 / 861 / 1360 | 1707 | 1611 | quick | T76 (3) | new |  |
| W659b8ce2 | trig_levels_sdx_rng28 | break | tsf 5_200 | plain60/60 | long | 900 | 4.2 | 622 | 98 / 665 / 487 / 1228 | 1227 | 1580 | quick | T178 (1) | new |  |
| Wae48a33c | trig_bands_regchan | break_linreg_native | frenko 28 | plain60/60 | long | 414 | 4.5 | 489 | -21 / 347 / 447 / 1194 | 1497 | 1557 | quick | T88 (1) | new |  |
| W590b2e06 | trig_levels_zones | break | tsf 2_400 | plain60/60 | long | 291 | 4.4 | 353 | 34 / 236 / 283 / 882 | 1154 | 1477 | quick | T168 (1) | new |  |
| W48f5f9df | trig_bands_keltner | break_native | time m_2 | sym30u | long | 713 | 4.3 | 599 | 54 / 702 / 474 / 1137 | 1513 | 1446 | quick | T138 (1) | new |  |
| W1539c680 | trig_levels_swsr5 | break_native | tsf 10_30 | plain60/60 | both | 1954 | 4.1 | 927 | 385 / 635 / 1013 / 1682 | 1936 | 1437 | quick | T32 (4) | new |  |
| W1d985827 | trig_levels_fibr_on | false_break_native | urenko 14 | fixed120/120 | long | 120 | 4.2 | 355 | 162 / 367 / 188 / 728 | 954 | 1431 | quick | T182 (1) | new |  |
| Wda135d16 | trig_levels_swsr5 | retest_native | tsf 25_20 | plain60/60 | long | 704 | 4.3 | 512 | 22 / 315 / 480 / 1252 | 1344 | 1425 | quick | T67 (1) | new |  |
| Wc91c258f | trig_levels_sdx_vol1100 | break | tsf 10_250 | plain60/60 | both | 944 | 4.1 | 644 | -6 / 507 / 670 / 1383 | 997 | 1424 | quick | T62 (1) | new |  |
| W81b59ffd | trig_levels_vwap | break_native | tsf 5_100 | plain60/60 | long | 817 | 4.3 | 593 | 29 / 704 / 704 / 839 | 1062 | 1419 | quick | T80 (1) | new |  |
| W7af015ca | trig_levels_fibr_on | false_break | urenko 14 | sym30u | both | 170 | 4.1 | 449 | -15 / 300 / 408 / 1117 | 1272 | 1410 | quick | T181 (1) | new |  |
| Wc213e45a | trig_levels_vwap | retest_native | swing atr_0.15 | fixed120/120 | long | 560 | 4.7 | 704 | 262 / 316 / 1102 / 1095 | 1003 | 1403 | quick | T20 (1) | new |  |
| W9c431d46 | trig_tape_delta | follow_native | tsf 25_20 | plain60/60 | both | 775 | 4.2 | 548 | -18 / 375 / 548 / 1289 | 1328 | 1346 | quick | T70 (1) | new |  |
| Wdad4ebaf | trig_levels_vwap | retest_native | dchg 10 | fixed120/120 | long | 586 | 4.8 | 780 | 125 / 517 / 946 / 1505 | 1141 | 1330 | quick | T08 (4) | new |  |
| W2a7c2533 | trig_levels_vwap | retest_native | kagi 10 | fixed120/120 | long | 586 | 4.7 | 778 | 123 / 515 / 944 / 1502 | 1138 | 1327 | quick | T08 (4) | new |  |
| Wa7df403e | trig_levels_ob15 | false_break_native | tsf 10_60 | plain60/60 | both | 210 | 4.7 | 311 | 157 / 65 / 348 / 710 | 1090 | 1322 | quick | T155 (4) | new | A1 |
| W94288f12 | trig_levels_vwap | break | rng 28 | fixed90/90 | long | 681 | 3.4 | 612 | -175 / 860 / 765 / 846 | 826 | 1317 | quick | T124 (1) | twin of live book L9c2622b0_R0_P45 (same module+variant+side) |  |
| Wbc4f3415 | trig_barnative_avwap | cross | tsf 10_120 | plain60/60 | both | 373 | 4.2 | 420 | 48 / 108 / 573 / 958 | 1342 | 1308 | quick | T153 (1) | new | A2 |
| Wa1bc8c6d | trig_live_seven | A7 | tm300  | plain60/60 | both | 715 | 4.4 | 530 | -25 / 538 / 518 / 1051 | 1075 | 1272 | quick | T57 (1) | new |  |
| Wb7866527 | trig_levels_mmove | break_native | tsf 5_200 | plain60/60 | both | 1437 | 4.0 | 630 | 305 / 397 / 654 / 1189 | 1779 | 1265 | quick | T176 (1) | new |  |
| Wf5779582 | trig_levels_ob15 | false_break | tsf 10_60 | plain60/60 | both | 211 | 4.4 | 304 | 157 / 59 / 348 / 688 | 945 | 1249 | quick | T155 (4) | new |  |
| W7852bb2d | trig_levels_profile_nodes | break_native | urenko 56 | fixed30/90 | long | 789 | 4.4 | 582 | -58 / 490 / 619 / 1243 | 1811 | 1235 | quick | T83 (2) | new |  |
| Wacc2a650 | trig_structure_level | round_break | tsf 25_150 | plain60/60 | both | 761 | 4.7 | 670 | 28 / 507 / 747 / 1374 | 1260 | 1170 | quick | T30 (1) | new |  |
| W914b0179 | trig_levels_opens | false_break_native | swing atr_0.1 | fixed60/120 | long | 679 | 4.4 | 675 | 2 / 841 / 476 / 1347 | 1076 | 1166 | quick | T46 (2) | new |  |
| W10d7ad74 | trig_levels_vwap | false_break | mrenko 80 | asym10u/20u | long | 361 | 4.5 | 594 | 106 / 561 / 475 / 1238 | 1492 | 1157 | quick | T41 (2) | new |  |
| Wa4485338 | trig_levels_opens | false_break | swing atr_0.1 | fixed60/120 | long | 681 | 4.2 | 647 | -83 / 822 / 417 / 1398 | 1229 | 1147 | quick | T46 (2) | new |  |
| W156d8a50 | trig_levels_vwap | break | tsf 5_100 | plain60/60 | long | 800 | 4.3 | 575 | 8 / 683 / 757 / 737 | 998 | 1142 | quick | T79 (1) | twin of live book L9c2622b0_R0_P45 (same module+variant+side) |  |
| W925b6ec0 | trig_levels_piv_floor | break_native | urenko 10 | asym15u/30u | long | 589 | 3.6 | 618 | 100 / 388 / 686 / 1297 | 1368 | 1128 | quick | T183 (1) | module+variant also in D8Asia.cs (relay confirms the book) |  |
| W4a911926 | trig_levels_ob15 | break | tsf 10_60 | plain60/60 | both | 218 | 4.5 | 314 | 146 / 65 / 294 / 803 | 993 | 1127 | quick | T155 (4) | new |  |
| W4ebf9569 | trig_levels_ob15 | break_native | tsf 10_60 | plain60/60 | both | 218 | 4.5 | 314 | 146 / 65 / 294 / 803 | 993 | 1127 | quick | T155 (4) | new |  |
| W54c07fed | trig_bands_vwap | walk | dchg 10 | asym20u/10u | long | 696 | 4.2 | 696 | 40 / 610 / 885 / 1173 | 1212 | 1110 | quick | T84 (2) | new |  |
| W72663fc9 | trig_bands_vwap | walk | kagi 10 | asym20u/10u | long | 696 | 4.2 | 693 | 37 / 608 / 883 / 1170 | 1209 | 1107 | quick | T84 (2) | new |  |
| W3a3821c8 | trig_levels_profile_nodes | break | time m_90 | fixed80/40 | both | 880 | 4.1 | 455 | 37 / 321 / 580 / 850 | 1275 | 1100 | quick | T145 (1) | new |  |
| W8f73fa08 | trig_levels_profile_nodes | break | urenko 56 | fixed30/90 | long | 807 | 4.1 | 544 | 0 / 490 / 542 / 1116 | 1608 | 1083 | quick | T83 (2) | new |  |
| Wdeb9ef78 | trig_levels_fibr_pd | break | lbrk 5_10 | fixed60/120 | long | 720 | 3.9 | 674 | -174 / 754 / 583 / 1479 | 1699 | 1066 | quick | T97 (1) | new |  |
| W9ca25f37 | trig_levels_vwap | false_break_native | mrenko 80 | asym10u/20u | long | 357 | 4.2 | 572 | 115 / 624 / 440 / 1098 | 1129 | 1062 | quick | T41 (2) | new |  |
| Wf4cd333f | trig_structure_libpattern | nr | tsf 25_40 | plain60/60 | both | 616 | 4.6 | 615 | 43 / 411 / 659 / 1344 | 827 | 1059 | quick | T31 (1) | module+variant also in D8Asia.cs (relay confirms the book) |  |
| W313e08c3 | trig_momentum_roc | break_native | tsf 25_20 | plain60/60 | long | 588 | 4.2 | 482 | -127 / 405 / 505 / 1111 | 914 | 1032 | quick | T69 (1) | module+variant also in D8Asia.cs (relay confirms the book) |  |
| W57c26903 | trig_pullback_ema | depth_native | tsf 25_40 | plain60/60 | both | 1233 | 4.2 | 787 | 41 / 353 / 1024 / 1720 | 1360 | 1024 | quick | T163 (1) | new | A1 |
| W12ca4e36 | trig_levels_vwap | break | mrenko 80 | fixed120/60 | long | 419 | 4.6 | 512 | 162 / 341 / 643 / 885 | 932 | 1018 | quick | T16 (1) | twin of live book L9c2622b0_R0_P45 (same module+variant+side) |  |
| W9ebc3217 | trig_levels_vwap | retest | dchg 10 | sym30u | long | 596 | 4.7 | 744 | 182 / 545 / 890 / 1327 | 905 | 952 | quick | T08 (4) | new |  |
| Wd51f7b8b | trig_levels_vwap | retest | kagi 10 | sym30u | long | 596 | 4.7 | 741 | 179 / 542 / 887 / 1325 | 903 | 949 | quick | T08 (4) | new |  |
| W852ce40a | trig_levels_channel | break | frenko 28 | fixed60/120 | long | 880 | 4.4 | 810 | -5 / 800 / 1163 / 1132 | 1291 | 936 | quick | T04 (1) | new | A2 |
| W6a59ce2b | trig_levels_piv_floor | break | renko 20 | sym8u | long | 616 | 3.8 | 559 | 103 / 190 / 638 / 1339 | 1594 | 935 | quick | T120 (2) | new |  |
| W8249eaa3 | trig_levels_piv_floor | break_native | renko 20 | sym8u | long | 616 | 3.8 | 559 | 103 / 190 / 638 / 1339 | 1594 | 935 | quick | T120 (2) | module+variant also in D8Asia.cs (relay confirms the book) |  |
| Wfd3c25bd | trig_bands_bollinger | break_native | tsf 10_120 | plain60/60 | both | 989 | 4.9 | 767 | 294 / 508 / 944 / 1301 | 1767 | 919 | quick | T58 (1) | new |  |
| W6dd45bc4 | trig_bands_regchan | break_stderr | swing atr_0.25 | sym30u | long | 677 | 3.8 | 738 | 121 / 762 / 930 / 1039 | 1452 | 913 | quick | T128 (1) | new |  |
| W09ce65c4 | trig_levels_fibr_ib | false_break_native | urenko 56 | fixed90/90 | both | 272 | 4.4 | 449 | 129 / 129 / 739 / 776 | 989 | 912 | quick | T180 (1) | new |  |
| W7aa2d347 | trig_levels_channel | break | renko 40 | asym15u/30u | long | 615 | 4.3 | 776 | 4 / 749 / 879 / 1397 | 1173 | 906 | quick | T18 (2) | new |  |
| Wca9b8f51 | trig_levels_channel | break_native | renko 40 | asym15u/30u | long | 615 | 4.3 | 776 | 4 / 749 / 879 / 1397 | 1173 | 906 | quick | T18 (2) | new |  |
| W3e82c655 | trig_levels_swsr5 | break | tsf 5_400 | plain60/60 | both | 1458 | 4.2 | 632 | 170 / 212 / 949 / 1180 | 920 | 895 | quick | T32 (4) | new |  |
| W1770c756 | trig_bands_bollinger | break | tsf 10_120 | plain60/60 | both | 966 | 4.1 | 623 | 284 / 463 / 709 / 1029 | 1441 | 877 | quick | T152 (1) | new |  |
| Wf307094f | trig_levels_piv_floor | break | urenko 56 | fixed90/90 | long | 498 | 4.4 | 568 | -8 / 425 / 899 / 864 | 839 | 867 | quick | T82 (1) | new |  |
| W65dc0e76 | trig_levels_fib15 | break_native | tsf 5_400 | plain60/60 | both | 1428 | 3.8 | 663 | 25 / 178 / 1163 / 1223 | 1292 | 861 | quick | T174 (1) | new |  |
| W0cd9d50d | trig_bands_bollinger | walk | pasl 28 | plain60/60 | long | 216 | 4.4 | 317 | 92 / 422 / 197 / 546 | 770 | 858 | quick | T99 (1) | new |  |
| W701737d6 | trig_levels_channel | break | lbrk 3_20 | fixed30/90 | long | 1072 | 4.3 | 661 | -116 / 507 / 971 / 1181 | 1464 | 853 | quick | T15 (4) | new |  |
| Wb9323973 | trig_levels_channel | break_native | lbrk 3_20 | fixed30/90 | long | 1076 | 4.1 | 652 | -50 / 512 / 928 / 1126 | 1405 | 846 | quick | T15 (4) | new |  |
| W8d2897df | trig_structure_breakout | brk | time m_5 | fixed40/80 | long | 671 | 4.6 | 523 | 6 / 647 / 447 / 946 | 1312 | 812 | quick | T52 (1) | new |  |
| Wa1810e2f | trig_levels_piv_floor | break | tsf 25_150 | plain60/60 | both | 484 | 4.6 | 517 | 128 / 378 / 643 / 890 | 870 | 796 | quick | T05 (3) | new |  |
| Waf483534 | trig_levels_piv_floor | break_native | tsf 25_150 | plain60/60 | both | 484 | 4.6 | 517 | 128 / 378 / 643 / 890 | 870 | 796 | quick | T05 (3) | module+variant also in D8Asia.cs (relay confirms the book) |  |
| W60c8d896 | trig_levels_piv_floor | break | tsf 5_50 | sym15u | long | 529 | 4.0 | 572 | 46 / 292 / 638 / 1325 | 1642 | 795 | quick | T60 (5) | new |  |
| W0e7037ba | trig_levels_profile_nodes | retest | lbrk 3_40 | fixed120/60 | both | 454 | 5.1 | 596 | 181 / 529 / 705 / 926 | 649 | 785 | quick | T01 (1) | new |  |
| Wd438d2d7 | trig_levels_profile_nodes | break_native | time m_90 | fixed80/40 | both | 889 | 4.5 | 524 | 132 / 433 / 687 / 797 | 1051 | 781 | quick | T24 (1) | new |  |
| W8da69b05 | trig_levels_ob5 | false_break | tsf 2_700 | sym15u | both | 506 | 3.9 | 541 | -3 / 177 / 735 / 1254 | 964 | 772 | quick | T71 (2) | new |  |
| Wff6cb74e | trig_levels_ob5 | false_break_native | tsf 2_700 | sym15u | both | 506 | 3.9 | 541 | -3 / 177 / 735 / 1254 | 964 | 772 | quick | T71 (2) | new |  |
| W3f6ee1e9 | trig_bands_bollinger | walk_native | pnf 5 | sym15u | long | 116 | 4.1 | 385 | 6 / 331 / 444 / 729 | 871 | 760 | quick | T111 (1) | new |  |
| W5fa32c4a | trig_momentum_roc | zero | tsf 25_20 | plain60/60 | long | 469 | 4.0 | 410 | -6 / 86 / 678 / 859 | 533 | 754 | quick | T68 (1) | new |  |
| W45d82380 | trig_momentum_er | trend_z_native | tsf 5_400 | plain60/60 | long | 439 | 4.2 | 360 | 69 / 350 / 191 / 858 | 822 | 753 | quick | T179 (1) | module+variant also in D8Asia.cs (relay confirms the book) |  |
| Wbbbd7252 | trig_momentum_er | trend | time m_4 | fixed45/45 | both | 1192 | 4.6 | 580 | 203 / 410 / 679 / 1015 | 1003 | 723 | quick | T25 (2) | new |  |
| W632d99eb | trig_momentum_er | trend_native | time m_4 | fixed45/45 | both | 1192 | 4.6 | 580 | 203 / 410 / 679 / 1015 | 1003 | 723 | quick | T25 (2) | new |  |
| W7d9b395f | trig_levels_profile_va | break | time s_20 | fixed30/30 | long | 1133 | 4.1 | 358 | 106 / 191 / 427 / 712 | 908 | 701 | quick | T146 (2) | new |  |
| Wd71f63ad | trig_levels_profile_va | break_native | time s_20 | fixed30/30 | long | 1133 | 4.1 | 358 | 106 / 191 / 427 / 712 | 908 | 701 | quick | T146 (2) | new |  |
| W64b49d16 | trig_structure_breakout | brk_native | time m_5 | fixed40/80 | both | 1499 | 4.4 | 679 | -242 / 841 / 660 / 1359 | 1931 | 692 | quick | T142 (1) | new |  |
| W109eb056 | trig_bands_regchan | break_stderr_native | frenko 28 | plain60/60 | long | 594 | 4.3 | 607 | -21 / 352 / 1027 / 978 | 654 | 679 | quick | T11 (1) | new | A2 |
| W968e8502 | trig_levels_prior_day | break_native | frenko 28 | fixed80/40 | long | 719 | 3.9 | 482 | 184 / 506 / 715 / 435 | 343 | 646 | quick | T03 (1) | new |  |
| W893b9c52 | trig_barnative_profile | va_fade | tsf 2_400 | plain60/60 | long | 128 | 4.0 | 265 | -41 / 250 / 144 / 720 | 871 | 643 | quick | T164 (1) | new |  |
| W882190cd | trig_levels_channel | false_break | pnf 5 | fixed60/120 | long | 893 | 3.9 | 755 | 58 / 722 / 665 / 1557 | 1838 | 630 | quick | T105 (2) | new |  |
| W5a82966e | trig_levels_channel | false_break_native | pnf 5 | fixed60/120 | long | 893 | 3.9 | 755 | 58 / 722 / 665 / 1557 | 1838 | 630 | quick | T105 (2) | new |  |
| W29089748 | trig_levels_channel | break | lbrk 4_20 | fixed90/90 | long | 731 | 4.3 | 749 | -68 / 578 / 1380 / 923 | 1196 | 625 | quick | T15 (4) | new |  |
| Wabef8f99 | trig_bands_donchian | break | time m_5 | fixed40/80 | long | 687 | 4.6 | 544 | -13 / 682 / 575 / 850 | 1220 | 615 | quick | T137 (2) | new | A1 |
| Wca5641ac | trig_bands_donchian | break | tm300  | fixed40/80 | long | 686 | 4.6 | 549 | -12 / 687 / 587 / 849 | 1219 | 612 | quick | T137 (2) | new |  |
| We7eba185 | trig_levels_fibr_pd | break | tsf 25_40 | plain60/60 | both | 944 | 4.2 | 675 | 112 / 507 / 876 / 1152 | 1186 | 612 | quick | T28 (2) | new |  |
| W4ad3a33c | trig_levels_fibr_pd | break_native | tsf 25_40 | plain60/60 | both | 944 | 4.2 | 675 | 112 / 507 / 876 / 1152 | 1186 | 612 | quick | T28 (2) | new |  |
| Wdf5eec5e | trig_bands_keltner | walk_native | pasl 14 | fixed60/120 | long | 491 | 3.8 | 532 | 31 / 633 / 533 / 873 | 1220 | 608 | quick | T101 (1) | new |  |
| W509306a5 | trig_trend_libstack | ema_hold | pasl 20 | fixed120/120 | long | 503 | 4.1 | 683 | 227 / 739 / 856 / 820 | 966 | 605 | quick | T102 (1) | new |  |
| Wf9528b08 | trig_levels_fib15 | ema_hold | pnf 14 | fixed120/120 | long | 503 | 4.1 | 683 | 227 / 739 / 856 / 820 | 966 | 605 | quick | T110 (1) | new |  |
| W32a76794 | trig_levels_piv_floor | break | frenko 40 | fixed80/40 | long | 729 | 3.7 | 470 | 18 / 484 / 270 / 1128 | 1002 | 604 | quick | T89 (2) | new |  |
| W2eb595d9 | trig_levels_piv_floor | break_native | frenko 40 | fixed80/40 | long | 729 | 3.7 | 470 | 18 / 484 / 270 / 1128 | 1002 | 604 | quick | T89 (2) | module+variant also in D8Asia.cs (relay confirms the book) |  |
| Wa9e30772 | trig_momentum_rsi | mom | lbrk 4_20 | sym15u | long | 582 | 3.7 | 758 | 203 / 620 / 596 / 1651 | 1605 | 593 | quick | T96 (1) | new |  |
| Wf894a501 | trig_levels_channel | false_break | swing pct_5 | fixed60/120 | long | 880 | 4.0 | 735 | 108 / 613 / 731 / 1471 | 1631 | 579 | quick | T131 (2) | new |  |
| W93b79d91 | trig_levels_channel | false_break_native | swing pct_5 | fixed60/120 | long | 880 | 4.0 | 735 | 108 / 613 / 731 / 1471 | 1631 | 579 | quick | T131 (2) | new |  |
| W0fe67991 | trig_levels_vwap | break | lbrk 3_10 | plain60/60 | both | 1836 | 4.2 | 960 | 510 / 795 / 715 / 1891 | 1593 | 579 | quick | T37 (1) | new | A3 |
| W8bb2b359 | trig_trend_macd | zero | urenko 80 | plain60/60 | long | 209 | 4.4 | 294 | 36 / 253 / 312 / 563 | 734 | 578 | quick | T186 (2) | new |  |
| Wc59c43ec | trig_trend_macd | zero_native | urenko 80 | plain60/60 | long | 209 | 4.4 | 294 | 36 / 253 / 312 / 563 | 734 | 578 | quick | T186 (2) | new |  |
| W78fb6038 | trig_levels_prior_day | break | frenko 28 | fixed80/40 | long | 721 | 3.9 | 442 | 197 / 418 / 745 / 318 | 294 | 575 | quick | T02 (1) | new |  |
| W553e3183 | trig_trend_libstack | ema_hold | time m_4 | fixed45/45 | both | 1885 | 4.6 | 807 | 282 / 616 / 900 / 1412 | 1168 | 574 | quick | T23 (1) | new |  |
| Wfac9ed8a | trig_levels_fibr_on | false_break | frenko 40 | fixed30/90 | both | 322 | 4.4 | 401 | 108 / 525 / 247 / 715 | 821 | 564 | quick | T33 (2) | new |  |
| W0778abb1 | trig_levels_fibr_on | false_break_native | frenko 40 | fixed30/90 | both | 322 | 4.4 | 401 | 108 / 525 / 247 / 715 | 821 | 564 | quick | T33 (2) | new |  |
| W0177408f | trig_levels_profile_nodes | false_break_native | renko 40 | fixed40/80 | both | 1357 | 4.2 | 756 | -204 / 538 / 648 / 2054 | 1690 | 564 | quick | T112 (1) | new |  |
| W5fbe35af | trig_bands_bollinger | walk_native | frenko 28 | fixed90/90 | long | 629 | 4.5 | 784 | -13 / 690 / 1071 / 1277 | 1812 | 560 | quick | T10 (1) | new |  |
| W15e78c34 | trig_bands_regchan | break_stderr_native | rng 56 | asym10u/20u | long | 110 | 3.8 | 369 | -32 / 114 / 517 / 868 | 1075 | 556 | quick | T125 (1) | new |  |
| Wcc0c8d33 | trig_bands_bollinger | walk | time m_10 | plain60/60 | long | 593 | 4.0 | 389 | 15 / 404 / 591 / 464 | 436 | 556 | quick | T136 (1) | new |  |
| W7a4e9a6f | trig_levels_piv_floor | break | swing pct_5 | sym15u | long | 538 | 3.8 | 587 | 177 / 813 / 591 / 682 | 618 | 529 | quick | T133 (2) | new |  |
| W858a3b0b | trig_levels_piv_floor | break_native | swing pct_5 | sym15u | long | 538 | 3.8 | 587 | 177 / 813 / 591 / 682 | 618 | 529 | quick | T133 (2) | module+variant also in D8Asia.cs (relay confirms the book) |  |
| Wbd8ebf34 | trig_bands_keltner | walk | pasl 14 | fixed40/80 | long | 394 | 4.4 | 465 | 82 / 588 / 502 / 622 | 908 | 527 | quick | T100 (1) | new |  |
| W98254c75 | trig_bands_keltner | walk | swing pct_5 | fixed30/90 | long | 419 | 3.9 | 409 | -42 / 468 / 495 / 648 | 891 | 516 | quick | T135 (1) | new | A3 |
| Wbcbe1d2e | trig_levels_piv_floor | break | tsf 10_250 | plain60/60 | long | 415 | 4.7 | 445 | 112 / 430 / 344 / 903 | 872 | 511 | quick | T60 (5) | new |  |
| Wc009b850 | trig_levels_piv_floor | break_native | tsf 10_250 | plain60/60 | long | 415 | 4.7 | 445 | 112 / 430 / 344 / 903 | 872 | 511 | quick | T60 (5) | module+variant also in D8Asia.cs (relay confirms the book) |  |
| Wf65b0846 | trig_bands_keltner | walk | time m_5 | fixed30/90 | long | 960 | 4.1 | 533 | 92 / 608 / 377 / 1047 | 1313 | 504 | quick | T51 (1) | new |  |
| Wbbe16a55 | trig_momentum_er | trend_z | tsf 2_400 | plain60/60 | long | 496 | 4.0 | 385 | 31 / 564 / 237 / 680 | 789 | 502 | quick | T169 (1) | new |  |
| W90a705bc | trig_structure_fvg | retest | time m_20 | fixed90/90 | long | 139 | 3.7 | 246 | 17 / 226 / 205 / 534 | 760 | 500 | quick | T143 (1) | new |  |
| W0ba0d70e | trig_levels_round | retest | tsf 25_150 | plain60/60 | long | 289 | 4.2 | 372 | 49 / 262 / 516 / 626 | 557 | 496 | quick | T65 (1) | new |  |
| W0e0ba8a6 | trig_levels_channel | break | mrenko 14 | fixed60/120 | long | 897 | 4.4 | 800 | -92 / 710 / 1176 / 1263 | 1083 | 478 | quick | T40 (1) | new |  |
| W68089a3e | trig_levels_piv_floor | break_native | tsf 5_400 | plain60/60 | both | 942 | 4.1 | 573 | 99 / 86 / 1071 / 988 | 664 | 473 | quick | T05 (3) | module+variant also in D8Asia.cs (relay confirms the book) |  |
| W1fdfc452 | trig_tape_libvol | force | tsf 10_250 | plain60/60 | long | 353 | 3.6 | 306 | -3 / 228 / 359 / 622 | 730 | 467 | quick | T159 (1) | new |  |
| We7d7da15 | trig_levels_fvg5 | false_break_native | tsf 25_20 | fixed120/60 | long | 206 | 3.7 | 299 | -39 / 254 / 278 / 695 | 449 | 455 | quick | T64 (1) | new |  |
| W1f39dbd9 | trig_levels_swsr5 | break_native | tsf 2_200 | asym10u/20u | long | 808 | 4.3 | 803 | 140 / 746 / 827 / 1459 | 1043 | 413 | quick | T167 (1) | new |  |
| Wb1b55fa4 | trig_levels_piv_floor | break | dchg 28 | fixed80/40 | long | 964 | 4.1 | 562 | 71 / 553 / 590 / 996 | 1200 | 412 | quick | T86 (1) | new |  |
| W41f3d0a7 | trig_bands_keltner | break | time m_4 | fixed40/80 | long | 860 | 4.5 | 634 | -208 / 885 / 528 / 1240 | 1387 | 389 | quick | T50 (1) | new |  |
| W142a885f | trig_xmarket_es | confirm | renko 56 | fixed90/30 | long | 764 | 3.9 | 409 | -30 / 498 / 543 / 538 | 801 | 366 | quick | T116 (1) | new | A3 |
| W276d304d | trig_levels_channel | break_native | lbrk 4_20 | fixed90/90 | long | 733 | 4.0 | 671 | -77 / 552 / 1217 / 826 | 1044 | 364 | quick | T15 (4) | new |  |
| W59549e38 | trig_bands_bollinger | walk | tsf 5_200 | plain60/60 | long | 387 | 4.1 | 359 | 7 / 415 / 495 / 445 | 455 | 360 | quick | T172 (1) | new |  |
| W5c3bfff6 | trig_momentum_rsi | mom_native | tsf 25_20 | plain60/60 | long | 422 | 3.5 | 310 | -25 / 309 / 354 / 568 | 351 | 342 | quick | T162 (1) | new | A3 |
| W18b1bab1 | trig_trend_libstack | ema_hold | tsf 5_50 | plain60/60 | long | 985 | 4.2 | 627 | 88 / 723 / 579 / 1070 | 1104 | 313 | quick | T81 (1) | new |  |
| W5d77f657 | trig_trend_ma_sma | price | dchg 28 | fixed90/30 | long | 557 | 4.0 | 386 | 72 / 254 / 693 / 451 | 587 | 294 | quick | T87 (1) | new | A1 |
| Wa603f98e | trig_bands_vwap | break_native | time m_4 | sym30u | long | 616 | 3.9 | 715 | 305 / 981 / 558 / 964 | 256 | 289 | quick | T21 (1) | new |  |
| W84be3ba2 | trig_bands_atrchan | break_ema | time m_4 | fixed40/80 | long | 794 | 4.1 | 549 | -177 / 747 / 574 / 946 | 899 | 275 | quick | T48 (1) | new |  |
| Wdd474052 | trig_levels_swsr5 | break | tsf 25_150 | plain60/60 | both | 630 | 4.3 | 497 | 47 / 416 / 537 / 964 | 501 | 270 | quick | T32 (4) | new |  |
| W3aaf3468 | trig_levels_swsr5 | break_native | tsf 25_150 | plain60/60 | both | 630 | 4.3 | 497 | 47 / 416 / 537 / 964 | 501 | 270 | quick | T32 (4) | new |  |
| W03dfa607 | trig_bands_envelope | break_ema | time m_2 | fixed30/90 | long | 179 | 4.2 | 316 | -27 / 117 / 492 / 660 | 418 | 264 | quick | T49 (2) | new |  |
| Wd608629e | trig_bands_envelope | break_ema | tm120  | fixed30/90 | long | 179 | 4.2 | 317 | -27 / 117 / 492 / 662 | 420 | 264 | quick | T49 (2) | new |  |
| W8a83a80e | trig_levels_round | break_native | tsf 25_20 | plain60/60 | long | 556 | 3.9 | 462 | -49 / 470 / 450 / 943 | 840 | 251 | quick | T76 (3) | new |  |
| W62fdfb81 | trig_levels_vwap | false_break | renko 28 | asym15u/30u | long | 509 | 3.9 | 617 | -24 / 569 / 482 / 1441 | 1610 | 241 | quick | T113 (2) | new |  |
| W5938af5c | trig_levels_vwap | false_break_native | renko 28 | asym15u/30u | long | 509 | 3.9 | 617 | -24 / 569 / 482 / 1441 | 1610 | 241 | quick | T113 (2) | new |  |
| W7c41e0e4 | trig_structure_fvg | cont | tsf 5_100 | plain60/60 | long | 604 | 3.7 | 421 | -36 / 464 / 501 / 691 | 814 | 232 | quick | T171 (2) | new | A2 |
| Wde3b3a39 | trig_trend_ma_ema | price_native | time m_60 | plain60/60 | both | 354 | 4.0 | 351 | 170 / 76 / 324 / 893 | 871 | 232 | quick | T144 (1) | new |  |
| We9a08b18 | trig_book_wall | pull_follow | pnf 7 | fixed90/30 | both | 103 | 4.5 | 166 | 54 / 39 / 313 / 242 | 283 | 229 | quick | T104 (1) | new |  |
| W6d582cbb | trig_confluence_xfam | bandflow | tsf 5_100 | plain60/60 | long | 552 | 4.2 | 444 | 51 / 646 / 367 / 654 | 692 | 181 | quick | T173 (1) | new | A1 |
| Wa20de091 | trig_levels_prior_day | break | rng 28 | fixed120/60 | long | 567 | 3.4 | 457 | 162 / 476 / 874 / 182 | 173 | 178 | quick | T123 (1) | new |  |
| Wdb715f92 | trig_manual_cci | zero | urenko 28 | fixed90/30 | long | 597 | 3.8 | 351 | -7 / 308 / 495 / 554 | 693 | 177 | quick | T185 (1) | new |  |
| Wb625def6 | trig_tape_delta | follow | pnf 10 | asym15u/30u | long | 560 | 4.2 | 712 | 91 / 767 / 771 / 1147 | 803 | 171 | quick | T17 (1) | new |  |
| W64d94287 | trig_levels_swsr5 | break | tsf 2_400 | fixed120/60 | long | 914 | 3.9 | 709 | 189 / 577 / 979 / 1016 | 690 | 168 | quick | T166 (1) | new |  |
| Waed46e2f | trig_bands_bollinger | walk_native | tsf 5_200 | plain60/60 | long | 521 | 4.0 | 405 | -84 / 442 / 538 / 644 | 553 | 138 | quick | T73 (1) | new |  |
| W7e9b3d24 | trig_momentum_stoch | zone_break_native | tsf 2_1200 | plain60/60 | long | 700 | 3.8 | 412 | -18 / 638 / 462 / 470 | 418 | 118 | quick | T170 (1) | new |  |
| Wda20ec41 | trig_levels_piv_floor | false_break | frenko 40 | fixed80/40 | long | 803 | 3.4 | 470 | -6 / 475 / 236 / 1199 | 931 | 116 | quick | T90 (1) | new |  |
| W2f8f26d1 | trig_bands_regchan | break_stderr | tsf 25_20 | plain60/60 | long | 392 | 4.0 | 385 | -148 / 354 / 560 / 697 | 588 | 95 | quick | T63 (1) | new |  |
| Wc171ec63 | trig_levels_profile_nodes | retest_native | lbrk 3_40 | fixed120/60 | both | 276 | 3.8 | 338 | 88 / 194 / 471 / 580 | 295 | 82 | quick | T94 (1) | new |  |
| Wce2943a9 | trig_levels_vwap | false_break_native | frenko 40 | sym15u | long | 531 | 4.3 | 686 | 41 / 781 / 533 / 1360 | 1120 | 62 | quick | T12 (1) | new |  |
| W4e8adcb3 | trig_bands_bollinger | walk_native | lbrk 3_20 | asym10u/20u | both | 130 | 4.0 | 356 | 89 / 286 / 572 / 418 | 468 | 49 | quick | T36 (1) | new |  |
| W0f2127df | trig_trend_ichimoku | cloud_break | rng 40 | fixed90/30 | long | 554 | 3.6 | 343 | 113 / 319 / 695 / 140 | 65 | 39 | quick | T126 (2) | new |  |
| Wb332fd44 | trig_trend_ichimoku | cloud_break_native | rng 40 | fixed90/30 | long | 554 | 3.6 | 343 | 113 / 319 / 695 / 140 | 65 | 39 | quick | T126 (2) | new |  |
| W0fcbb72f | trig_levels_fibr_dev | retest_native | tsf 25_20 | fixed120/60 | long | 543 | 3.2 | 369 | 35 / 149 / 263 / 1086 | 1167 | 37 | quick | T161 (1) | new |  |
| Waef6fc5e | trig_bands_envelope | break_ema_native | tm20  | fixed120/60 | long | 502 | 3.6 | 416 | 32 / 461 / 512 / 597 | 840 | 37 | quick | T55 (2) | new |  |
| Wdad50dee | trig_bands_envelope | break_ema_native | time s_20 | fixed120/60 | long | 504 | 3.6 | 426 | 33 / 470 / 513 / 628 | 885 | 35 | quick | T55 (2) | new |  |
| Weeefc143 | trig_trend_ichimoku | cloud_break | dchg 20 | fixed90/30 | long | 572 | 3.9 | 349 | 173 / 341 / 518 / 308 | 291 | 5 | quick | T85 (1) | new |  |
| W0c7df6cc | trig_momentum_er | trend_z | time m_2 | plain60/60 | long | 721 | 3.8 | 445 | 183 / 622 / 577 / 303 | 348 | -13 | quick | T53 (2) | new |  |
| W050f4766 | trig_momentum_er | trend_z_native | time m_2 | plain60/60 | long | 721 | 3.8 | 445 | 183 / 622 / 577 / 303 | 348 | -13 | quick | T53 (2) | module+variant also in D8Asia.cs (relay confirms the book) |  |
| W9adebc39 | trig_levels_fib15 | break_native | pnf 7 | sym30u | long | 667 | 3.8 | 677 | 377 / 770 / 848 / 626 | 286 | -64 | quick | T107 (1) | new |  |
| W7073918c | trig_levels_fibr_dev | retest | tsf 25_20 | fixed120/60 | long | 470 | 2.9 | 324 | 74 / 174 / 285 / 789 | 813 | -73 | quick | T160 (1) | new |  |
| W3c37763d | trig_levels_vwap | break | tm600  | fixed90/90 | long | 647 | 3.8 | 543 | 67 / 778 / 780 / 395 | 217 | -79 | quick | T27 (1) | twin of live book L9c2622b0_R0_P45 (same module+variant+side) |  |
| W9c031517 | trig_levels_piv_floor | break | tsf 2_400 | sym15u | long | 497 | 3.3 | 507 | 37 / 344 / 910 / 635 | 633 | -87 | quick | T60 (5) | new |  |
| Web5e8429 | trig_levels_piv_floor | break_native | tsf 2_400 | sym15u | long | 497 | 3.3 | 507 | 37 / 344 / 910 / 635 | 633 | -87 | quick | T60 (5) | module+variant also in D8Asia.cs (relay confirms the book) |  |
| W18dc9b06 | trig_pullback_ema | depth_native | time m_120 | plain60/60 | both | 308 | 4.0 | 396 | 13 / 279 / 669 / 552 | 355 | -90 | quick | T141 (1) | new |  |
| Wf36b14b4 | trig_momentum_roc | zero_native | lbrk 3_40 | sym15u | long | 405 | 4.0 | 614 | 73 / 330 / 811 / 1220 | 1348 | -100 | quick | T38 (1) | new |  |
| W34814971 | trig_levels_channel | break | tsf 5_50 | sym15u | long | 759 | 4.1 | 736 | -78 / 625 / 889 / 1434 | 1464 | -144 | quick | T74 (2) | new |  |
| W1236f546 | trig_levels_channel | break_native | tsf 5_50 | sym15u | long | 759 | 4.1 | 736 | -78 / 625 / 889 / 1434 | 1464 | -144 | quick | T74 (2) | new |  |
| W8329a1ab | trig_trend_ma_kama | cross_native | renko 28 | plain60/60 | both | 584 | 3.8 | 397 | 210 / 330 / 566 / 443 | 228 | -184 | quick | T44 (1) | new |  |
| We81a08d6 | trig_structure_fvg | cont | tsf 2_400 | sym15u | long | 158 | 3.5 | 347 | 70 / 304 / 357 / 643 | 527 | -188 | quick | T171 (2) | new |  |
| W56c2c4d6 | trig_bands_keltner | break_native | rng 40 | fixed90/90 | long | 461 | 3.8 | 618 | -1 / 319 / 1050 / 1019 | 1442 | -200 | quick | T45 (1) | new |  |
| W527709cc | trig_manual_macd | zero | renko 28 | fixed90/30 | long | 598 | 3.6 | 318 | 94 / 413 / 597 / 59 | 80 | -311 | quick | T119 (1) | new | A3 |
| Wc3edf002 | trig_trend_ma_kama | price_native | renko 28 | fixed40/80 | long | 710 | 3.6 | 449 | 104 / 211 / 797 / 625 | 523 | -416 | quick | T43 (1) | new |  |
| Wc0c1ba7c | trig_levels_fib15 | break_native | tsf 10_60 | fixed90/30 | long | 930 | 3.6 | 419 | 79 / 704 / 467 / 323 | 284 | -452 | quick | T59 (1) | new |  |
| Wd116f43b | trig_trend_ma_kama | price | renko 28 | fixed40/80 | long | 737 | 3.7 | 493 | 129 / 190 / 834 / 777 | 578 | -468 | quick | T122 (1) | new | A2 |
| Wc3787abf | trig_tape_speed | follow | renko 10 | sym30u | long | 742 | 3.9 | 784 | 208 / 945 / 690 / 1237 | 851 | -523 | quick | T115 (1) | new |  |
| W995e01d9 | trig_levels_vwap | false_break | frenko 40 | sym15u | both | 1097 | 4.0 | 1004 | 349 / 295 / 821 / 2718 | 2434 | -596 | quick | T35 (1) | new |  |
| W6063426c | trig_levels_mmove | break_native | tsf 2_400 | plain60/60 | long | 914 | 3.6 | 492 | 151 / 575 / 822 / 288 | 35 | -689 | quick | T07 (1) | new |  |
| Wa1dbe371 | trig_structure_fvg | cont | time m_2 | sym15u | long | 376 | 3.9 | 482 | 56 / 413 / 720 / 662 | 387 | -707 | quick | T22 (1) | new |  |

### NY AM: 76 books held at the last re-qualify date (week 182, hold to 2026-10-25), set (3), near-twin groups 61; exact (42 months landed): 0 of 76

| book id | module | variant | bar type and size | bracket | side | trades | t | $/lot/wk full history | 2023 / 2024 / 2025 / 2026 $/lot/wk | L6M | L3M | source | twin group (size) | mark | stack |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| W1c18e21f | trig_bands_atrchan | break_ema | ha micro_B080 | asym10u/20u | both | 1114 | 4.3 | 1326 | 1246 / 144 / 2001 / 2013 | 2325 | 3862 | quick | T48 (2) | new |  |
| Wfe48041c | trig_bands_atrchan | break_ema | ha qmid_B080 | asym10u/20u | both | 1116 | 4.4 | 1333 | 1300 / 234 / 2012 / 1868 | 2090 | 3862 | quick | T48 (2) | new |  |
| Wbb4ef729 | trig_levels_vwap | break | swing pct_5 | sym15u | both | 1618 | 4.9 | 1861 | 1658 / 447 / 2426 / 3089 | 2715 | 3708 | quick | T11 (1) | new |  |
| Wbcfa80fb | trig_levels_prior_day | false_break | swing atr_0.25 | fixed120/120 | both | 1045 | 4.9 | 1527 | 760 / 238 / 2562 / 2530 | 3554 | 3470 | quick | T24 (3) | new | N1 |
| Wa4b747b2 | trig_levels_prior_day | false_break_native | swing atr_0.25 | fixed120/120 | both | 1045 | 4.9 | 1527 | 760 / 238 / 2562 / 2530 | 3554 | 3470 | quick | T24 (3) | new |  |
| W835b7e31 | trig_structure_level | round_break | t3 dltor_B200 | sym15u | both | 2233 | 3.9 | 1935 | 666 / 1557 / 3351 / 1797 | 1480 | 3332 | quick | T64 (1) | new |  |
| W131e3f70 | trig_bands_atrchan | break_ema | typ qmid_B080 | asym10u/20u | both | 858 | 4.2 | 1252 | 767 / 344 / 2114 / 1740 | 2014 | 3299 | quick | T67 (1) | new |  |
| Wb1ab799c | trig_levels_vwap | break | dchg 28 | asym15u/30u | both | 1624 | 4.5 | 1675 | 1618 / 926 / 1840 / 2449 | 1243 | 3072 | quick | T46 (2) | new |  |
| W050c781f | trig_levels_vwap | break | kagi 28 | asym15u/30u | both | 1624 | 4.5 | 1674 | 1617 / 925 / 1838 / 2447 | 1241 | 3070 | quick | T46 (2) | new |  |
| W10e7f4cd | trig_levels_prior_day | false_break_native | dchg 14 | sym8u | both | 1412 | 4.1 | 1272 | 901 / 145 / 1733 / 2431 | 3815 | 2985 | quick | T47 (2) | new |  |
| Wca8c5296 | trig_levels_prior_day | false_break_native | kagi 14 | sym8u | both | 1412 | 4.1 | 1271 | 900 / 144 / 1731 / 2430 | 3814 | 2984 | quick | T47 (2) | new |  |
| Wf74d00e3 | trig_levels_prior_day | false_break | dchg 20 | fixed120/120 | both | 1043 | 4.5 | 1385 | 692 / 269 / 2440 / 2076 | 2809 | 2640 | quick | T24 (3) | new | N3 |
| W170cb5a0 | trig_levels_prior_day | false_break_native | renko 20 | fixed120/60 | both | 1362 | 3.9 | 1155 | 355 / 395 / 2359 / 1321 | 2152 | 2453 | quick | T59 (3) | new |  |
| W3b484778 | trig_levels_prior_day | false_break | urenko 20 | fixed120/60 | both | 1370 | 4.1 | 1219 | 377 / 562 / 2199 / 1578 | 2151 | 2359 | quick | T59 (3) | new |  |
| Wc1c42940 | trig_levels_prior_day | false_break_native | urenko 20 | fixed120/60 | both | 1367 | 4.1 | 1187 | 377 / 562 / 2246 / 1378 | 2059 | 2267 | quick | T59 (3) | new |  |
| W3e503490 | trig_levels_prior_day | false_break_native | pnf 5 | sym8u | both | 1677 | 4.1 | 1222 | 984 / 573 / 1795 / 1524 | 2750 | 2229 | quick | T58 (1) | new |  |
| W39b600c0 | trig_momentum_willr | break_native | swing atr_0.15 | asym10u/20u | both | 2789 | 4.1 | 1891 | 1086 / 1305 / 2059 / 3154 | 1546 | 2208 | quick | T35 (1) | new |  |
| W33efa8dc | trig_momentum_willr | break | swing atr_0.15 | sym15u | both | 2546 | 4.2 | 1759 | 695 / 1958 / 2022 / 2171 | 1959 | 2068 | quick | T10 (2) | new |  |
| Waaa5a0bf | trig_momentum_stoch | zone_break | swing atr_0.15 | sym15u | both | 2532 | 4.2 | 1819 | 750 / 1800 / 2460 / 2025 | 2143 | 1976 | quick | T10 (2) | new | N3 |
| W27eceb02 | trig_bands_envelope | break_sma_native | typ micro_B080 | fixed60/120 | both | 985 | 4.8 | 1077 | 1059 / 890 / 1281 / 1066 | 1265 | 1864 | quick | T14 (2) | new |  |
| Wf8c9672b | trig_bands_envelope | break_sma_native | typ qmid_B080 | fixed60/120 | both | 989 | 4.8 | 1057 | 1006 / 883 / 1279 / 1037 | 1172 | 1864 | quick | T14 (2) | new |  |
| Wbc90b09f | trig_momentum_stoch | zone_break_native | swing atr_0.15 | asym10u/20u | both | 2794 | 4.2 | 2019 | 1339 / 1241 / 1975 / 3668 | 2129 | 1817 | quick | T33 (1) | new | N2 |
| W483477dd | trig_bands_bollinger | walk_native | t3 bmsgq_B200 | sym15u | both | 2025 | 4.5 | 1653 | 807 / 1538 / 1763 / 2444 | 2133 | 1778 | quick | T37 (1) | new |  |
| W9d19166d | trig_bands_avwap0930 | walk_0930 | tm45  | fixed90/30 | long | 1185 | 4.6 | 688 | 373 / 693 / 550 / 1147 | 1352 | 1767 | quick | T39 (1) | new |  |
| W7959e8dc | trig_bands_atrchan | break_ema | entropy B080 | fixed120/120 | both | 868 | 4.2 | 1176 | 717 / 771 / 2243 / 759 | 910 | 1665 | quick | T25 (1) | new |  |
| We3999e99 | trig_levels_fibr_dev | reject | pnf 7 | asym15u/30u | both | 617 | 4.1 | 946 | 948 / 1120 / 569 / 1207 | 1542 | 1632 | quick | T56 (1) | new |  |
| W05611e0a | trig_bands_keltner | break | bmsg B030 | fixed60/120 | both | 608 | 4.5 | 901 | 691 / 761 / 1204 / 886 | 1108 | 1590 | quick | T15 (1) | new |  |
| Wc0f0a762 | trig_momentum_roc | break_native | swing atr_0.15 | asym10u/20u | both | 2778 | 4.8 | 2315 | 914 / 2171 / 3095 / 2807 | 1359 | 1397 | quick | T22 (1) | new | N1 |
| Wd9d9d0c3 | trig_structure_level | sopen_cross | time m_4 | fixed120/60 | long | 533 | 4.3 | 693 | 240 / 433 / 1056 / 978 | 851 | 1352 | quick | T65 (1) | new |  |
| Wd5038cce | trig_levels_prior_day | false_break | kagi 28 | sym15u | both | 1050 | 4.5 | 1313 | 831 / 366 / 2058 / 1993 | 2327 | 1321 | quick | T27 (1) | new |  |
| Wd49ae15e | trig_levels_fib5 | pullback_native | swing pct_20 | fixed120/60 | long | 637 | 4.2 | 735 | 672 / 490 / 644 / 1209 | 419 | 1276 | quick | T61 (1) | new |  |
| Wccc3fcb5 | trig_bands_atrchan | break_ema | t3 entropy_B200 | sym15u | both | 836 | 4.2 | 1212 | 948 / 176 / 2325 / 1338 | 1355 | 1164 | quick | T38 (3) | new |  |
| W614e1e1c | trig_book_cancel | canc_follow | pnf 5 | sym8u | both | 4762 | 3.8 | 1657 | 1482 / 1159 / 1959 / 2054 | 2721 | 1071 | quick | T55 (1) | new |  |
| W9d0b10a3 | trig_book_ice | fade_sm | pasl 28 | fixed60/120 | both | 1411 | 3.8 | 1013 | 464 / 1062 / 1237 / 1179 | 574 | 944 | quick | T54 (1) | new |  |
| W468eca22 | trig_bands_atrchan | break_ema | t3 rngor_B200 | sym15u | both | 635 | 3.9 | 1020 | 353 / 504 / 2114 / 897 | 1403 | 917 | quick | T38 (3) | new |  |
| Wecd63112 | trig_bands_vwap | walk_native | pasl 10 | sym8u | long | 696 | 4.2 | 907 | 316 / 633 / 1142 / 1500 | 806 | 914 | quick | T29 (2) | new |  |
| Wfa0dc58a | trig_bands_avwap0930 | walk_0930_native | pasl 10 | sym8u | long | 686 | 4.1 | 894 | 328 / 647 / 1018 / 1568 | 1015 | 847 | quick | T29 (2) | new |  |
| Wb41d7d15 | trig_bands_atrchan | break_ema | t3 sessrng_B200 | sym15u | both | 585 | 4.0 | 990 | 341 / 407 / 2003 / 1035 | 996 | 836 | quick | T38 (3) | new |  |
| Wa2265a5c | trig_structure_level | sopen_reject | t3 dltor_B200 | sym15u | long | 451 | 4.0 | 847 | 360 / 71 / 1499 / 1438 | 691 | 835 | quick | T63 (1) | new |  |
| W3f23fbd1 | trig_structure_level | sopen_cross | t3 bmsgq_B200 | sym15u | long | 486 | 4.0 | 833 | 522 / 365 / 923 / 1587 | 1040 | 795 | quick | T62 (1) | new | N1 |
| W20980087 | trig_live_seven | O7 | renko 14 | fixed30/90 | both | 529 | 4.1 | 491 | -97 / 512 / 952 / 431 | 505 | 763 | quick | T60 (1) | new | N2 |
| W29a0680a | trig_structure_level | sopen_cross | volor B080 | sym15u | both | 1143 | 4.0 | 1158 | 265 / 1068 / 1123 / 2143 | 2087 | 728 | quick | T71 (1) | new | N3 |
| We52cf06e | trig_pullback_ema | count | volor B030 | fixed120/60 | long | 183 | 4.3 | 361 | 312 / 282 / 403 / 453 | 839 | 669 | quick | T70 (1) | new | N3 |
| W4a101899 | trig_book_ofi | follow_sm | pasl 28 | fixed90/90 | both | 1839 | 4.5 | 1475 | 947 / 1269 / 1565 / 2108 | 1923 | 647 | quick | T30 (1) | twin of live book Lf0346d55.BRP60 (same module+variant+side) |  |
| W65834bac | trig_book_cancel | canc_follow | time m_15 | fixed120/60 | both | 1552 | 4.3 | 1282 | 443 / 1171 / 1932 / 1378 | 205 | 586 | quick | T12 (1) | new |  |
| Wad63ffee | trig_bands_vwap | walk | pasl 10 | sym8u | long | 654 | 4.2 | 848 | 411 / 653 / 793 / 1564 | 873 | 534 | quick | T53 (1) | new |  |
| W2d6065cd | trig_book_ofi | follow_sm | tsf 25_40 | sym15u | both | 1445 | 4.0 | 1365 | 939 / 1246 / 1880 / 1256 | 688 | 491 | quick | T13 (2) | twin of live book Lf0346d55.BRP60 (same module+variant+side) | N2 |
| W96a06db2 | trig_levels_vwap | break_native | tsf 5_100 | sym15u | both | 1604 | 4.8 | 2033 | 1123 / 1702 / 2364 / 2871 | 2995 | 470 | quick | T43 (1) | new |  |
| W36556086 | trig_structure_level | sopen_reject | pnf 56 | sym30u | long | 142 | 4.7 | 503 | 342 / 517 / 514 / 622 | 485 | 419 | quick | T09 (1) | new |  |
| Wa3f069eb | trig_book_ofi | follow_sm | swing atr_0.9 | fixed120/60 | both | 1444 | 4.3 | 1041 | 294 / 846 / 1497 / 1401 | 874 | 402 | quick | T36 (1) | twin of live book Lf0346d55.BRP60 (same module+variant+side) | N3 |
| W5955381d | trig_bands_bollinger | walk_native | entropy B080 | fixed45/45 | both | 551 | 3.7 | 398 | 516 / 327 / 455 / 304 | 262 | 336 | quick | T16 (1) | new |  |
| W24cfa010 | trig_levels_vwap | break | pnf 7 | sym30u | both | 1587 | 4.1 | 1434 | 1778 / 906 / 2221 / 775 | 613 | 323 | quick | T02 (2) | new |  |
| Wc7c3f9c5 | trig_levels_vwap | break_native | pnf 7 | sym30u | both | 1587 | 4.1 | 1434 | 1778 / 906 / 2221 / 775 | 613 | 323 | quick | T02 (2) | new |  |
| W2b1bc7e6 | trig_bands_keltner | walk_native | tm20  | fixed120/60 | both | 185 | 4.4 | 328 | 10 / 490 / 324 / 429 | 627 | 317 | quick | T40 (2) | new | N1 |
| Wd6d093e9 | trig_bands_keltner | walk_native | time s_20 | fixed120/60 | both | 180 | 4.2 | 304 | 30 / 461 / 252 / 429 | 626 | 315 | quick | T40 (2) | new |  |
| W6a8993ed | trig_bands_atrchan | break_ema | bmsg B030 | fixed60/120 | both | 246 | 4.1 | 558 | 605 / 505 / 651 / 464 | 263 | 169 | quick | T01 (1) | new | N2 |
| W8a491884 | trig_structure_level | sopen_cross | lbrk 3_10 | fixed40/80 | long | 1008 | 3.9 | 698 | 429 / 788 / 625 / 929 | 754 | 165 | quick | T51 (1) | new |  |
| W9168008f | trig_book_ofi | follow_sm | urenko 56 | fixed90/30 | long | 1809 | 4.2 | 808 | 1074 / 842 / 946 / 343 | 270 | 120 | quick | T45 (1) | new |  |
| W5ba295af | trig_levels_piv_wf | retest | urenko 40 | sym30u | both | 1237 | 4.1 | 1269 | 686 / 946 / 1572 / 1827 | 2483 | 10 | quick | T44 (1) | new |  |
| W77fdbf23 | trig_structure_breakout | brk | t3 dltor_B200 | sym15u | both | 837 | 4.0 | 1144 | 199 / 787 / 2170 / 1167 | 229 | 7 | quick | T23 (1) | new |  |
| W6be33734 | trig_levels_ob5 | break | pasl 14 | fixed90/90 | long | 398 | 4.1 | 610 | 532 / 762 / 705 / 372 | -17 | 0 | quick | T07 (1) | new |  |
| W02b31e1f | trig_bands_regchan | break_stderr_native | micro B030 | fixed30/30 | short | 158 | 4.1 | 152 | 172 / 237 / 112 / 80 | 63 | -56 | quick | T05 (1) | new | N3 |
| W9fd5ca5d | trig_levels_piv_floor | reject | pnf 10 | fixed60/120 | both | 658 | 4.0 | 784 | 1365 / 969 / 670 / 159 | 106 | -97 | quick | T57 (1) | new |  |
| W43af5f5a | trig_book_ofi | follow | pnf 14 | fixed90/30 | short | 894 | 4.0 | 608 | 688 / 432 / 1041 / 207 | -128 | -189 | quick | T19 (1) | new | N1 |
| W0e119686 | trig_bands_regchan | break_linreg_native | micro B030 | plain60/60 | short | 118 | 3.7 | 220 | 206 / 309 / 343 / -34 | -98 | -284 | quick | T18 (1) | new |  |
| W01dfc899 | trig_levels_ob5 | break_native | pasl 14 | fixed90/90 | long | 398 | 4.1 | 613 | 552 / 708 / 762 / 367 | -116 | -449 | quick | T08 (1) | new | N2 |
| W27c4dbd9 | trig_structure_level | sopen_cross | kal volor_B200 | asym10u/20u | long | 488 | 3.9 | 798 | 630 / 431 / 1075 / 1058 | 621 | -625 | quick | T28 (1) | new | N2 |
| W2c33138b | trig_structure_level | sopen_cross | renko 14 | fixed40/80 | long | 995 | 3.9 | 720 | 300 / 654 / 1028 / 802 | 590 | -639 | quick | T20 (1) | new |  |
| W6dd6f4c3 | trig_book_ofi | follow | tm240  | fixed40/80 | both | 3945 | 4.1 | 1243 | 983 / 2076 / 1423 / 225 | 472 | -660 | quick | T04 (1) | new |  |
| W3959b53a | trig_book_ofi | follow_sm | rng 80 | plain60/60 | both | 2555 | 3.7 | 1091 | 652 / 1361 / 1800 / 269 | -113 | -673 | quick | T21 (1) | twin of live book Lf0346d55.BRP60 (same module+variant+side) |  |
| W5b6fa37d | trig_levels_vwap | break | tsf 5_100 | sym15u | both | 1562 | 4.9 | 1813 | 940 / 1140 / 3390 / 1468 | 1401 | -937 | quick | T06 (1) | new |  |
| Wf0a3a4f9 | trig_book_ofi | follow | frenko 28 | plain60/60 | both | 4396 | 4.0 | 1417 | 479 / 1746 / 2444 / 582 | 113 | -943 | quick | T17 (1) | new |  |
| W716b78f6 | trig_book_ofi | follow_sm | frenko 40 | asym20u/10u | both | 2267 | 3.8 | 1459 | 1204 / 1176 / 2986 / 118 | -400 | -1035 | quick | T26 (1) | twin of live book Lf0346d55.BRP60 (same module+variant+side) |  |
| W44ad27a6 | trig_book_ofi | follow_native | tm240  | fixed40/80 | both | 3909 | 3.9 | 1248 | 969 / 2167 / 1397 / 182 | -437 | -1073 | quick | T41 (1) | new |  |
| W806b6ade | trig_book_ofi | follow | tsf 5_1200 | sym15u | both | 1557 | 3.7 | 1380 | 869 / 1115 / 2359 / 950 | -892 | -1531 | quick | T42 (1) | new |  |
| Wb42295fb | trig_book_ofi | follow_sm | tsf 5_400 | sym15u | both | 1564 | 3.5 | 1254 | 668 / 1878 / 1915 / 189 | -1280 | -1551 | quick | T13 (2) | twin of live book Lf0346d55.BRP60 (same module+variant+side) |  |

## PART D: exact

**Status: stacks (bare + layers, 42 months): 504 of 504 set-months landed; primary held cells on set (3), bare R0 held periods: 10145 of 10145 set-months landed (2026-11-27 08:24Z).**

What is queued (all bare R0 or the stack rows of the engine, no engine or gate change):
1. **The primary's held cells restricted to set (3), all four sessions** (Asia 712 cells, London 196, NY AM 1,118, NY PM 117 = 2,143 cells, 2,140 built; 3 cells failed to build (module errors ema_hold, ema_hold, fade) and are excluded), bare R0, 1 lot, own bracket, the months touched by each hold period: **10,145 set-months** (names TL3_ALN_<AS|NY|LO|NP>_W<hash>_R0RT, the same names as Test 5 / Q1 for the same cell, so any row Test 5 or Q1 already has is reused; rows already DONE or in the gating file are skipped at append). Rows file /mnt/l2/l2vast/_test6/rows_T6.txt, cells json cells_T6.json (scoring: th_test3/th_test5 score code on picks_set3_test6.json; exact vs quick comparison to be added when they land).
2. **The six named stacks A1-A3, N1-N3, bare and with each session's live ACCOUNT layers, all 42 months:** 12 sets x 42 = **504 set-months** (rows_STK.txt). Sets TL3_SR_<AS|NY>_T6<A1..N3>_BARE and _LY on events TL3_ALN_<AS|NY>_T6<k> (6 streams, 1 lot per book, cap 12000/4800, fill through, as Q2). Layers (as Q2): Asia = the JT275 account layers STK8, SZW3, CGB1, DLA4, DLB14, DLC4; NY AM = the JT162 account layers BL6, CAP6, STK7, SZW2, NTS2, CGB2 (D8_LAYER_KEYS_ASIA_4BOOK_JT275.md, D8_LAYER_KEYS_NYAM_NYAMW_JT162.md). Per-book Trade Health (LOCK / TAKE / ZONE / LOSS) is fitted per named book and is NOT applied to the drawn books (as Q2). Names carry no _BF1/_BF4 tag, so park_non2lot does not touch them (no exemption needed).
3. Queue position: appended right after Test 5's rows ('P queued'), before Q0's NY AM / NY PM / London and Q1 (waiter queue_chain6.sh, writes "T6 queued" to /mnt/l2/l2vast/_test6/queue.log).

## EXACT RESULTS (bare R0, 1 lot, fees in)

### Part D (1) held cells, set (3)

| session | held periods landed | weeks | exact $/lot/wk | exact max DD | exact worst wk | exact L6M | exact L3M | exact 2023 Q4 / 2024 / 2025 / 2026 | quick $/lot/wk (same periods) | quick max DD | quick L6M | quick L3M | exact / quick |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 740 of 743 (3 without an exact set) | 160 | 155 | 12796 | -5269 | 325 | 177 | 41 / 244 / 75 / 151 | 148 | 9493 | 474 | 275 | 1.05 |
| London | 195 of 196 (1 without an exact set) | 160 | -80 | 20012 | -8635 | -114 | -370 | -59 / 42 / -169 / -95 | -127 | 22108 | -175 | -467 | 0.63 |
| NYAM | 1156 of 1156 | 160 | 264 | 15481 | -6060 | 203 | 376 | 122 / 219 / 348 / 184 | 166 | 20533 | -29 | 225 | 1.59 |
| NYPM | 120 of 120 | 160 | 292 | 23976 | -4828 | 858 | 188 | -33 / 45 / 772 / 131 | 276 | 26279 | 693 | 180 | 1.06 |
| Four summed | 2211 of 2215 (4 without an exact set) | 160 | 189 | 11360 | -5648 | 171 | 224 | 47 / 166 / 261 / 144 | 139 | 12258 | 123 | 247 | 1.36 |

### Part D (2) the six stacks

| stack | version | months landed | exact $/wk (6 books, 1 lot each) | per book per lot $/wk | exact max DD | exact worst wk | exact L6M | exact L3M | 2023 Q4 / 2024 / 2025 / 2026 (per book per lot) | quick $/lot/wk (equal weight 6, in sample) | exact / quick |
|---|---|---|---|---|---|---|---|---|---|---|---|
| A1 | bare R0 | 42 of 42 | 2790 | 465 | 16595 | -9735 | 6585 | 4624 | 38 / 415 / 439 / 957 | 518.0 | 0.90 |
| A1 | live account layers | 42 of 42 | 2619 | 437 | 17119 | -8933 | 5970 | 3875 | 37 / 402 / 423 / 869 | 518.0 | 0.84 |
| A2 | bare R0 | 42 of 42 | 2920 | 487 | 40444 | -25499 | 5913 | 4083 | -11 / 439 / 599 / 870 | 597.0 | 0.82 |
| A2 | live account layers | 42 of 42 | 2659 | 443 | 33107 | -18951 | 6866 | 4576 | -13 / 409 / 412 / 949 | 597.0 | 0.74 |
| A3 | bare R0 | 42 of 42 | 2803 | 467 | 18166 | -15925 | 5442 | 3235 | 88 / 408 / 493 / 863 | 461.0 | 1.01 |
| A3 | live account layers | 42 of 42 | 2462 | 410 | 16988 | -13456 | 4669 | 3007 | 89 / 409 / 402 / 721 | 461.0 | 0.89 |
| N1 | bare R0 | 42 of 42 | 5160 | 860 | 27926 | -20473 | 6159 | 5972 | 565 / 492 / 1248 / 1118 | 995.0 | 0.86 |
| N1 | live account layers | 42 of 42 | 5226 | 871 | 25633 | -18249 | 7293 | 6217 | 520 / 510 / 1229 / 1209 | 995.0 | 0.88 |
| N2 | bare R0 | 42 of 42 | 5532 | 922 | 31655 | -22327 | 5097 | 3224 | 719 / 712 / 1037 / 1234 | 974.0 | 0.95 |
| N2 | live account layers | 42 of 42 | 5212 | 869 | 29776 | -21496 | 4750 | 2898 | 638 / 700 / 1043 / 1079 | 974.0 | 0.89 |
| N3 | bare R0 | 42 of 42 | 5757 | 959 | 44519 | -21498 | 9813 | 6028 | 429 / 669 / 1231 / 1482 | 986.0 | 0.97 |
| N3 | live account layers | 42 of 42 | 5490 | 915 | 47388 | -20358 | 8838 | 6617 | 425 / 668 / 1147 / 1394 | 986.0 | 0.93 |

Part D (1): primary held cells on candidate set (3), bare R0, own bracket, 1 lot per cell, fees in, equal weight over the books held that week; only held periods whose months ALL have DONE; quick screen restricted to the same periods; weeks 26..185 (2023-10-01 on). "Four summed" is pooled equal weight over every book held in any session that week (as the quick screen in part A). Code code/th_test6/exact6.py.

Part D (2): six stacks, 1 lot per book, all 42 months (2023-04..2026-10 without 2025-11), BARE vs the session account layers (Asia JT275: STK8 SZW3 CGB1 DLA4 DLB14 DLC4; NY AM JT162: BL6 CAP6 STK7 SZW2 NTS2 CGB2); per-book Trade Health NOT applied. Max DD / worst week are on the 6-book weekly $ (not per lot). Quick column is the in-sample equal-weight per-lot mean from the stacks table; the stacks were picked from their own past, so exact vs quick is NOT a calibration of the rule.

