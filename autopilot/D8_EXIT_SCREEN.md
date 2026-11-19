# D8_EXIT_SCREEN - 68 exit recipes on the D8 candidates (W-D8EXIT, orders 0213Z / 0220Z / 0224Z), refreshed 2026-11-19 02:32Z
Research only. Screen = points per lot (base lots), 68 recipes (7 families) on the candidate cell's OWN entries, run on real entries and on 2 random-entry draws (same count / side mix). Pick rule (PREREG_D8EXIT.md sha in DECISIONS.md): eligible = L6M>0, L3M>0, trades L6M>=20, no prior year (2023-25) >30% worse; best = lowest ulcer then highest L6M. A cell BEATS-NULL when its best eligible recipe L6M exceeds the best eligible recipe of BOTH null draws (2 draws = screen only; finalists get more draws). Data week index 189 (as EXIT_YIELD). Fixed reference = best fixed bracket of the cell from pass-1 (p1real).
Engine support per family and build dates: autopilot/D8_EXIT_ENGINE_SUPPORT.md. Until a family is built, a recipe of that family cannot be the best TESTED exit in the D8 spec (screen result stands).

## a. progress per session (order: Asia, NY AM, London, NY PM)

| session | candidate cells | screened | pending | with an eligible exit (real) | BEATS-NULL | beat fixed ref too | ETA |
|---|---|---|---|---|---|---|---|
| Asia | 0 | 0 | 0 | 0 | 0 | 0 | done |
| NY AM | 3936 | 40 | 3896 | 12 | 11 | 11 | about 17.1 h after the sessions above (fleet 228 cells/h) |
| London | 0 | 0 | 0 | 0 | 0 | 0 | done |
| NY PM | 391 | 0 | 391 | 0 | 0 | 0 | about 18.8 h after the sessions above (fleet 228 cells/h) |

Asia and London candidates appear here when W-LONENG's engine rows land in D8_CANDIDATES (0 now = none listed yet, not "none exist").

## b. candidates with an eligible exit that beats both null draws (best first by ulcer)

| session | live book | cell id | cell | fixed ref (bracket L6M / ulcer) | best exit (family) | L6M | L3M | ulcer | persist | y23 / y24 / y25 / y26 | win / avg win / avg loss / hold min | trades L6M | null best eligible L6M (a / b) | top 2-3 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NY AM | K7 | L04f971dd | NYAM/drb_15000/trig_levels_opens/retest_native/{"M": 10, "tol": 0.5}/plain60/60/long | n/a on this host | stage=([1.0], [0.5], True) stop=('vol', 1.5) target=('R', 3.0) trail=('chand', 3.0) (staged) | +510 | +660 | 267 | 0.68 | +615 / +1302 / +1226 / +1347 | 56% / +104.4 / -118.5 / 77 | 86 | - / - | stop=('vol', 1.5) trail=('chand', 2.0) +368 (u 333) ; opp_exit=True stop=('vol', 1.5) +229 (u 365) |
| NY AM | K7 | L80ccd283 | NYAM/dib_40000/trig_trend_ichimoku/tk_cross_native/{"len": 9, "width": 0.25}/plain60/60/long | n/a on this host | stop=('swing', 4) target=('R', 2.0) (market target) | +134 | +299 | 318 | 0.59 | +1557 / +914 / +1289 / +662 | 47% / +98.1 / -83.5 / 54 | 118 | - / - | stop=('swing', 8) target=('R', 2.0) +118 (u 362) ; stop=('swing', 4) trail=('chand', 3.0) +278 (u 378) |
| NY AM | K7 | L3c6da67f | NYAM/swing_atr_0.6/trig_book_ofi/follow_sm/{"L": 200, "z": 2.0, "sm": 3}/plain60/60/both | n/a on this host | stop=('vol', 2.5) trail=('swing', 1) (trailing) | +893 | +592 | 322 | 0.69 | +1071 / +2382 / +1651 / +1287 | 39% / +94.4 / -52.1 / 34 | 191 | - / - | stop=('swing', 4) trail=('swing', 1) +800 (u 328) ; stop=('swing', 8) trail=('swing', 1) +790 (u 331) |
| NY AM | K7 | L92e46167 | NYAM/mom_20/trig_levels_profile_va/retest_native/{"M": 10, "tol": 0.5}/sym15u/long | n/a on this host | minrr=1.5 stop=('vol', 1.5) target=('mm', 1.27) (market target) | +167 | +192 | 350 | 0.52 | +229 / +253 / +253 / +269 | 30% / +64.5 / -26.9 / 6 | 364 | - / - |  |
| NY AM | K7 | L69c2a000 | NYAM/dol_500/trig_levels_profile_va/retest/{"M": 10, "tol": 0.5}/plain60/60/long | n/a on this host | stop=('swing', 4) trail=('swing', 1) (trailing) | +41 | +54 | 393 | 0.53 | +226 / +308 / +121 / +799 | 38% / +38.1 / -23.4 / 5 | 405 | - / - |  |
| NY AM | K7 | L01811caa | NYAM/tick_8000/trig_levels_open_range/break_native/{"n": 3, "k": 0.25}/plain60/60/both | n/a on this host | stop=('vol', 2.5) trail=('bricks', 3) (trailing) | +229 | +579 | 443 | 0.63 | +1413 / +2387 / +3477 / +2351 | 48% / +102.3 / -91.0 / 58 | 212 | - / - | stop=('vol', 1.5) target=('R', 2.0) +152 (u 603) |
| NY AM | K7 | Lc6be02ea | NYAM/pasl_40/trig_xmarket_fast/follow_RTY/{"w": 5, "thr": 1.0}/plain60/60/both | n/a on this host | latch=(0.85, 3.0, 20.0) stop=('vol', 1.5) target=('R', 2.0) (time / behaviour) | +182 | +1024 | 506 | 0.62 | +694 / +948 / +1950 / +2051 | 39% / +124.0 / -78.7 / 31 | 281 | - / - |  |
| NY AM | K7 | L41bfa428 | NYAM/drb_2000/trig_book_ofi/follow_sm/{"L": 100, "z": 1.5, "sm": 3}/sym15u/both | n/a on this host | stop=('vol', 2.5) target=('R', 2.0) (market target) | +1282 | +937 | 675 | 0.60 | +1816 / +4433 / +4465 / +239 | 43% / +124.3 / -84.5 / 45 | 264 | - / - |  |
| NY AM | K7 | Lcf12aa09 | NYAM/drb_10000/trig_bands_avwap0830/break_0830_native/{"clk": 12, "k": 1.0}/plain60/60/both | n/a on this host | be=(0.5, 0) stop=('vol', 1.5) target=('R', 2.0) (time / behaviour) | +107 | +246 | 884 | 0.64 | +299 / +1615 / +1642 / +100 | 28% / +129.0 / -49.1 / 39 | 270 | - / - |  |
| NY AM | K7 | Lb864d619 | NYAM/drb_10000/trig_bands_avwap0830/break_0830_native/{"clk": 3, "k": 1.0}/plain60/60/both | n/a on this host | be=(0.5, 0) stop=('vol', 1.5) target=('R', 2.0) (time / behaviour) | +107 | +246 | 884 | 0.64 | +299 / +1615 / +1642 / +100 | 28% / +129.0 / -49.1 / 39 | 270 | - / - |  |
| NY AM | K7 | Le7884733 | NYAM/vol_6000/trig_levels_profile_va/false_break_native/{"M": 1, "k": 0.5}/sym15u/both | n/a on this host | stop=('vol', 2.5) trail=('chand', 2.0) (trailing) | +196 | +430 | 992 | 0.48 | +781 / +398 / +409 / -259 | 42% / +105.5 / -74.3 / 34 | 145 | - / - |  |

## c. what the screen has found per exit family (best eligible exit of each screened cell, real vs null)

| family | cells where it is the best eligible exit (real) | same on null (mean of 2 draws) |
|---|---|---|
| market target | 4 | 1.0 |
| staged | 1 | 0.0 |
| time / behaviour | 3 | 0.0 |
| trailing | 4 | 1.0 |

Screened cells with an eligible exit: real 12 of 40 (30%), null 2.0 of 40 (5%). Null/real ratio is the false-positive reading for "best of 68": a cell that clears its own nulls and sits in a session where this ratio is low is the one to take to the engine.

## d. machines, workers, measured speed

| machine | D8-exit-screen workers (nice 7) | rows owned (crc32(row)%12) | note |
|---|---|---|---|
| A Frankfurt | 24 | 2-6 | started 02:24Z beside 36+24 grid workers and 24 EXIT_YIELD workers (nice 15) |
| B Singapore | 24 | 7-11 | same |
| server 2 Dallas | 8 | 0-1 | same |
| box 1 | 0 | - | memory guard (MemAvail > 40 GB) |


Measured: 29 groups finished, 38 cells, mean 191 s per cell (3 tags: real + 2 null) per worker.

## e. STAGE 1 work list for this pipeline stage (order 0228Z), hours on the current fleet, 02:33Z
| item | size | core-hours (measured) | workers now | wall hours at today's workers | wall hours if every A+B thread (256) |
|---|---|---|---|---|---|
| D8-candidate exit screen, Asia + NY AM (68 recipes x real + 2 null) | 3,557 NY AM cells listed (Asia 0 listed yet) | ~130 core-s per cell => ~128 | 56 (A 24, B 24, server 2 8) at nice 7 | ~2.3 h if each worker gets a full core; 4-6 h with grid / engine contention | 0.5 h |
| BROAD exit run, Asia / NY AM part (pairs ordered by Asia / NY AM pass-1 value; one simulation serves all sessions) | 8,012 of 36,026 A+B pairs have a positive best pass-1 L6M in NY AM (98 in Asia); pairs without a local pass-1 value (25,211) go after them | 3,792 core-s per pair measured => ~8,440 core-hours for the 8,012 value>0 pairs; ~37,950 core-hours for all 36,026 (+~7,600 for Dallas row groups 0-1) | 48 (A 24 + B 24, nice 11) | ~176 h (7.3 days) | ~33 h |
| BROAD run, rest (London / NY PM value, no-value pairs) | 28,014 pairs | ~29,500 core-hours | same workers, after the line above (pre-emptible filler) | ~610 h | ~115 h |
Stage-1 end date for the exit work (D8 candidates screen): ~02:24Z + 4-6 h = about 07:00-09:00Z 11-19 for the 3,557 NY AM cells (NY AM + Asia as Asia rows land). The BROAD Asia / NY AM part cannot finish before ~Nov 26 at today's allocation (48 workers at nice 11, below real pass 1, R3 / pass 2 and null 1-2); ~Nov 20 15:00Z if all A+B threads were on it - Josh decides (LEAD NOTE sent).
Changes made 02:30Z: the 24 EXIT_YIELD workers per box (nice 15, stratified 5% order) were told to stop after their current pair (STOP file; they exit within ~1 h) and replaced by 24 per box ey_job2.py workers (nice 11) that walk the pairs by Asia / NY AM pass-1 value (pairs_broad_<A|B>.csv), skipping finished pairs; their pairs are marked broad=1 in timing.csv and ey_score.py (patched, backup .bak_d8_0230) keeps them out of the 5% EXIT_YIELD sample statistics, so that page stays a fair stratified sample.
NOT built yet: fine params on cells alive on any recipe; own-stop version of the exits (per-trade records in the path simulator); a faster simulator (context rebuilt per tag now; RAM-cached stores; compiled path loop) - each needs an identity test (trade for trade) before its numbers are used; Dallas row groups 0-1 are not in the broad list (server 2 not used by the broad run).

