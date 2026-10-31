# DS3_ONE_CONVENTION - the D6-faithful composite on ONE stated convention (GOV-3, drafted Sat 2026-10-31 ~16:30Z). POST-HOC, nothing here is a PASS

Capped 20260206, UNTOUCHED never read. Units $k per week, delta vs the as-is stack under the same convention, MDE (2.8 x SE of the paired weekly delta) in brackets, `*` = beyond MDE. Windows L3M 14 wk / L6M 28 / HOLD 32 / PRE 75 / X' 44.

## Page 1

**Convention (one, used in every cell below).** A6 = PB7 (Asia only, 1 lot). Live lots K6 2 / P6 7 / U6 4 / H6 4 Asia + 2 NY-AM / M6 2 / A6 1 (O6 in no number). Composite = split 70/30 (K6 included, integer), PE 45-s, zone skip, Asia-stop cut, ER sizer on all six books. SizeMult = running max over the signals each book TOOK today (reset 18:00 ET). BookR = session planned lot x SizeMult x 60 pt x $20 (H6 NY-AM 2 lots). ER lots integer half-up, min 1 (governors keep the unrounded 0.5/1.0/1.5). Stop = label day-of-month parity, applied per row inside the engine (odd Native 1.28, even join 2.45). Add slip +0.25 per add lot (model, headline) / +0.45 (stress, Table C). Combined week lock = stack MTM <= -F x R_K6, R_K6 = 2 lots x K6 SizeMult x 60 x $20 (F unknown: 8/12/16/20/30 shown; SizeMult before K6's first signal of the day m0 = 1.0, variant 0.5). As-is = market entries, no D6 rules, join 2.45, same lots, per-book locks at planned-lot R (SizeMult 1.0); under a combined lock it uses the same F and m0 (its K6 SizeMult is 1.0 after the first signal). Not in the composite: NY-PM end skip, D7 filters.

**Plain sentence.** On the one convention the composite beats the as-is stack by +19.4k/wk in L6M with no combined lock (beyond MDE in L6M only) and by +10.6k / +13.1k / +16.6k with a 12R / 20R / 30R combined lock against an unlocked as-is (none beyond MDE: the lock widens the weekly noise and costs the composite 3-9k L6M (30R to 12R)); like-for-like (same lock on both) it is +21.9k / +16.1k / +16.1k, but that flatters because the lock hurts the as-is more. PRE is negative against an unlocked as-is under every combined lock (-2.5 to -3.5). Correcting A6 to PB7 is what made the combined lock expensive (lock cost on the composite -6.5k with the library PB, -9.7k with PB7, L6M).

### Bridge (moving from the earlier numbers, one change at a time, cumulative; every row re-run in one engine, rows 0-1 tie to DS3_GOVERNOR_FIDELITY V0 and DS3_SUNDAY_DECISION (d))

| # | change (cumulative) | composite level L6M | as-is level L6M | L3M | L6M | HOLD | PRE | X' | step change L6M | lock 12R effect on composite L6M |
|---|---|---|---|---|---|---|---|---|---|---|
| 0 | EARLIER (DS3_GOVERNOR_FIDELITY V0): A6 = library PB all sessions 1 lot, Native 1.28 all days, running max over taken signals, BookR on max session lot, no combined lock | 46.8 | 24.0 | +25.0 (22.6)* | +22.8 (17.6)* | +19.3 (17.3)* | +7.4 (13.0) | +12.9 (15.0) | - | -6.5 |
| 1 | + A6 = PB7 (Asia only, 1 lot), both composite and as-is | 43.5 | 21.7 | +25.5 (22.5)* | +21.8 (17.6)* | +18.7 (17.5)* | +6.1 (13.1) | +11.8 (14.2) | -1.0 | -9.7 |
| 2 | + BookR on the SESSION planned lot (H6 NY-AM 2 not 4) | 42.4 | 21.7 | +24.0 (22.9)* | +20.7 (17.7)* | +17.9 (17.4)* | +5.7 (13.1) | +12.2 (14.0) | -1.0 | -9.4 |
| 3 | + stop = day-of-month parity (odd Native 1.28 / even join 2.45) = no-combined-lock CONVENTION C1 | 41.1 | 21.7 | +22.3 (22.3) | +19.4 (17.5)* | +16.7 (17.3) | +4.5 (13.2) | +11.4 (14.0) | -1.3 | -8.9 |
| 4 | + combined 12R(K6) week lock on the composite only vs UNLOCKED as-is = C2 | 32.3 | 21.7 | +16.9 (27.4) | +10.6 (26.5) | +9.5 (26.7) | -3.5 (15.3) | +4.5 (14.1) | -8.9 | - |
| 5 | + same 12R lock on the as-is too = C3 like-for-like | 32.3 | 10.4 | +25.1 (21.2)* | +21.9 (27.3) | +17.7 (27.2) | +5.4 (11.9) | +8.3 (13.8) | +11.4 | - |

Not in the chain (checked, not adopted): running max over ALL signals (V1) instead of taken signals, parity + session-lot, no lock: +23.0 (21.9)* | +19.8 (17.3)* | +17.0 (17.1) | +4.5 (13.1) | +11.5 (13.9); with 12R: +17.1 (27.3) | +10.9 (26.3) | +10.2 (26.1) | -2.1 (14.8) | +4.9 (13.6) (vs unlocked as-is).

Same chain on the LIBRARY-PB engine for the combined lock (A6 = library PB): no lock / 12R, Native, taken, session-lot BookR:  +23.6 (23.0)* | +21.8 (17.7)* | +18.5 (17.4)* | +7.0 (13.1) | +13.2 (14.8)  //  +17.6 (29.1) | +17.0 (21.1) | +15.5 (22.4) | -0.3 (15.2) | +5.3 (13.8)

### Final table (headline: slip +0.25, K6 70/30, parity stop; combined lock multiple unknown, three shown; m0 = 1.0 and the 0.5 variant)

| row | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| C1 no combined lock: composite vs as-is (both without) | +22.3 (22.3) | +19.4 (17.5)* | +16.7 (17.3) | +4.5 (13.2) | +11.4 (14.0) |
| C2 12R(m0 1.0) on composite vs UNLOCKED as-is | +16.9 (27.4) | +10.6 (26.5) | +9.5 (26.7) | -3.5 (15.3) | +4.5 (14.1) |
| C2 20R(m0 1.0) on composite vs UNLOCKED as-is | +11.6 (34.3) | +13.1 (21.9) | +10.1 (23.3) | -2.7 (15.3) | +6.7 (15.2) |
| C2 30R(m0 1.0) on composite vs UNLOCKED as-is | +19.4 (24.9) | +16.6 (18.9) | +14.4 (18.2) | -2.5 (14.9) | +10.1 (14.4) |
| C3 like-for-like 12R(m0 1.0) on BOTH | +25.1 (21.2)* | +21.9 (27.3) | +17.7 (27.2) | +5.4 (11.9) | +8.3 (13.8) |
| C3 like-for-like 20R(m0 1.0) on BOTH | +8.8 (32.4) | +16.1 (24.4) | +12.2 (24.8) | +2.2 (14.9) | +11.6 (15.4) |
| C3 like-for-like 30R(m0 1.0) on BOTH | +18.3 (23.8) | +16.1 (18.6) | +13.8 (17.9) | -0.1 (14.5) | +10.2 (14.4) |
| C2 12R(m0 0.5) on composite vs UNLOCKED as-is | +16.8 (27.4) | +10.8 (26.4) | +10.2 (26.2) | -7.7 (15.2) | +5.4 (13.6) |
| C2 20R(m0 0.5) on composite vs UNLOCKED as-is | +11.3 (34.0) | +13.0 (21.8) | +10.0 (23.2) | -2.7 (15.6) | +6.3 (14.8) |
| C2 30R(m0 0.5) on composite vs UNLOCKED as-is | +12.4 (35.1) | +13.1 (22.4) | +12.3 (21.1) | -1.8 (14.7) | +10.0 (14.4) |
| C3 like-for-like 12R(m0 0.5) on BOTH | +28.9 (19.5)* | +23.6 (27.1) | +19.6 (26.6) | +1.6 (11.2) | +7.4 (11.7) |
| C3 like-for-like 20R(m0 0.5) on BOTH | +17.0 (22.9) | +19.3 (19.9) | +14.2 (21.9) | +4.9 (12.8) | +10.2 (15.0) |
| C3 like-for-like 30R(m0 0.5) on BOTH | +12.7 (32.0) | +13.3 (21.3) | +11.8 (20.1) | +2.6 (13.8) | +14.5 (15.8) |
| memo: effect of the combined lock on the composite alone, 12R (m0 1.0) | -5.4 (11.3) | -8.9 (14.0) | -7.2 (16.1) | -8.0 (12.0) | -6.9 (9.0) |
| memo: effect of the combined lock on the as-is alone, 12R (m0 1.0) | -8.2 (23.6) | -11.4 (14.3) | -8.2 (13.6) | -8.9 (10.4) | -3.8 (8.0) |

Reading. (1) C1 +19.4 (17.5)* L6M is the lock-free lead; L3M +22.3 (22.3) is a hair inside, HOLD/PRE/X' inside. (2) C2 (what the live lock does if the as-is has none): +10.6 / +13.1 / +16.6 at 12/20/30R, every cell inside its MDE (17-27); the looser the lock the closer to C1; 8R is ruinous (+0.6, Table B). (3) C3 is larger than C1 at 12R because the combined 12R lock costs the as-is -11.4 L6M vs the composite -8.9; use C2 as the conservative figure. (4) m0 0.5 vs 1.0 changes L6M by <= 0.2 at 12R and 20R, 30R -3.5; it matters in PRE at 12R (-7.7 vs -3.5). (5) Stress slip +0.45 lowers every cell 0.3-0.5. (6) K6 at market (answer 3): C1 +18.9, C2-12R +10.3 (Table D), inside MDE of the 70/30 line. (7) Risk (Table E): lock-free the composite is far smoother than the as-is (L6M maxDD 23 vs 88, worst week -23 vs -88); the combined lock does NOT lighten the composite in the recent windows (12R L6M maxDD 27, worst week -27) and only helps its tail in PRE (worst-20 -608 vs -875, worst week -46 vs -120). No claim of significance is made on any risk line.

## What this resolves in DS3_SUNDAY_BRIEF_NUMBERS section 5

* 1/2: one lead per lock multiple; the +22.3 / +16.5 / +27.8 spread was the A6 choice (-1.0 no lock, about -5 to -6 at 12R), the governor reading (-1.0 session lot, taken vs all +-0.4) and the stop (-1.3) plus which as-is. 3: A6 = PB7 everywhere. 4: taken signals + session-lot BookR as the reply states (all-signal max tested: +0.4 L6M, noise). 5: parity applied per row (a true in-engine parity, not the splice of two runs; no-lock result +19.4 vs spliced +19.5/+20.4). 7: integer headline. 8: NY-PM skip not in the composite. Still open: 13 (the multiple; gross vs net in the entry test; stop pts fixed 60 not the signal stop; O6 missing), 6 (lot units), 9-10, 12.

## Tables

### Table A2: levels, $k/wk (mean per week)

| row | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| as-is unlocked | 12.2 | 21.7 | 21.9 | 18.6 | -3.4 |
| as-is 12R (m0 1.0) | 3.9 | 10.4 | 13.7 | 9.7 | -7.2 |
| as-is 20R (m0 1.0) | 15.0 | 18.8 | 19.8 | 13.6 | -8.3 |
| as-is 30R (m0 1.0) | 13.3 | 22.3 | 22.5 | 16.3 | -3.4 |
| composite no combined lock | 34.4 | 41.1 | 38.6 | 23.1 | 8.0 |
| composite 12R (m0 1.0) | 29.0 | 32.3 | 31.4 | 15.1 | 1.0 |
| composite 20R (m0 1.0) | 23.8 | 34.8 | 32.0 | 15.9 | 3.3 |
| composite 30R (m0 1.0) | 31.6 | 38.4 | 36.3 | 16.1 | 6.7 |
| composite 12R (m0 0.5) | 29.0 | 32.5 | 32.1 | 11.0 | 2.0 |
| composite 20R (m0 0.5) | 23.5 | 34.7 | 31.9 | 15.9 | 2.9 |
| composite 30R (m0 0.5) | 24.5 | 34.8 | 34.2 | 16.9 | 6.6 |

### Table B: extra multiples 8R and 16R (slip +0.25, K6 70/30)

| row | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| C1 no combined lock: composite vs as-is (both without) | +22.3 (22.3) | +19.4 (17.5)* | +16.7 (17.3) | +4.5 (13.2) | +11.4 (14.0) |
| C2 8R(m0 1.0) on composite vs UNLOCKED as-is | +3.3 (32.6) | +0.6 (26.8) | +1.4 (26.8) | -6.9 (15.6) | +2.0 (12.6) |
| C2 16R(m0 1.0) on composite vs UNLOCKED as-is | +15.3 (28.3) | +15.1 (19.7) | +12.1 (21.8) | -1.0 (14.9) | +7.0 (14.8) |
| C3 like-for-like 8R(m0 1.0) on BOTH | +17.3 (26.7) | +15.7 (27.0) | +15.4 (24.0) | +4.8 (14.4) | +8.0 (7.9)* |
| C3 like-for-like 16R(m0 1.0) on BOTH | +14.9 (25.1) | +18.7 (21.3) | +14.4 (22.9) | +4.9 (15.2) | +13.1 (15.6) |
| C2 8R(m0 0.5) on composite vs UNLOCKED as-is | +3.3 (32.6) | +0.5 (26.7) | +1.6 (26.4) | -7.0 (15.0) | +0.6 (13.7) |
| C2 16R(m0 0.5) on composite vs UNLOCKED as-is | +15.3 (28.3) | +15.2 (19.6) | +12.3 (21.6) | -5.9 (15.9) | +5.9 (14.4) |
| C3 like-for-like 8R(m0 0.5) on BOTH | +21.7 (25.9) | +17.8 (26.9) | +17.5 (23.9) | +6.5 (13.2) | +5.6 (9.3) |
| C3 like-for-like 16R(m0 0.5) on BOTH | +18.1 (20.5) | +19.9 (19.3)* | +15.1 (21.2) | +2.4 (13.7) | +11.3 (13.0) |
| memo: effect of the combined lock on the composite alone, 12R (m0 1.0) | -5.4 (11.3) | -8.9 (14.0) | -7.2 (16.1) | -8.0 (12.0) | -6.9 (9.0) |
| memo: effect of the combined lock on the as-is alone, 12R (m0 1.0) | -8.2 (23.6) | -11.4 (14.3) | -8.2 (13.6) | -8.9 (10.4) | -3.8 (8.0) |

### Table C: stress slip +0.45 per add lot (K6 70/30)

| row | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| C1 no combined lock: composite vs as-is (both without) | +21.9 (22.2) | +18.9 (17.3)* | +16.3 (17.1) | +4.1 (13.2) | +11.1 (14.0) |
| C2 12R(m0 1.0) on composite vs UNLOCKED as-is | +16.6 (27.4) | +10.2 (26.3) | +9.2 (26.6) | -3.7 (15.3) | +4.3 (14.1) |
| C2 20R(m0 1.0) on composite vs UNLOCKED as-is | +11.3 (34.2) | +12.7 (21.7) | +9.8 (23.2) | -3.0 (15.3) | +6.5 (15.2) |
| C2 30R(m0 1.0) on composite vs UNLOCKED as-is | +19.0 (24.8) | +16.2 (18.7) | +14.0 (18.1) | -2.7 (14.9) | +9.9 (14.4) |
| C3 like-for-like 12R(m0 1.0) on BOTH | +24.9 (21.1)* | +21.6 (27.2) | +17.4 (27.1) | +5.2 (11.9) | +8.1 (13.7) |
| C3 like-for-like 20R(m0 1.0) on BOTH | +8.5 (32.3) | +15.7 (24.2) | +11.8 (24.6) | +2.0 (14.9) | +11.4 (15.4) |
| C3 like-for-like 30R(m0 1.0) on BOTH | +17.9 (23.7) | +15.6 (18.4) | +13.3 (17.8) | -0.4 (14.4) | +9.9 (14.4) |
| C2 12R(m0 0.5) on composite vs UNLOCKED as-is | +16.6 (27.4) | +10.4 (26.2) | +9.9 (26.0) | -7.8 (15.1) | +5.3 (13.6) |
| C2 20R(m0 0.5) on composite vs UNLOCKED as-is | +11.0 (33.9) | +12.6 (21.6) | +9.6 (23.1) | -3.0 (15.5) | +6.2 (14.8) |
| C2 30R(m0 0.5) on composite vs UNLOCKED as-is | +12.0 (35.0) | +12.7 (22.3) | +11.9 (21.0) | -3.2 (15.2) | +9.8 (14.4) |
| C3 like-for-like 12R(m0 0.5) on BOTH | +28.6 (19.4)* | +23.2 (27.0) | +19.3 (26.5) | +1.4 (11.2) | +7.3 (11.6) |
| C3 like-for-like 20R(m0 0.5) on BOTH | +16.7 (22.8) | +18.9 (19.8) | +13.9 (21.7) | +4.6 (12.8) | +10.1 (15.0) |
| C3 like-for-like 30R(m0 0.5) on BOTH | +12.4 (31.9) | +12.8 (21.1) | +11.3 (20.0) | +1.1 (13.2) | +14.3 (15.8) |
| memo: effect of the combined lock on the composite alone, 12R (m0 1.0) | -5.3 (11.2) | -8.8 (14.0) | -7.1 (16.0) | -7.8 (12.0) | -6.8 (9.0) |
| memo: effect of the combined lock on the as-is alone, 12R (m0 1.0) | -8.2 (23.6) | -11.4 (14.3) | -8.2 (13.6) | -8.9 (10.4) | -3.8 (8.0) |

### Table D: K6 at market, others 70/30 (user answer 3; slip +0.25)

| row | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| C1 no combined lock: composite vs as-is (both without) | +20.2 (21.8) | +18.9 (17.1)* | +16.5 (16.9) | +3.9 (13.1) | +11.5 (13.4) |
| C2 12R(m0 1.0) on composite vs UNLOCKED as-is | +15.5 (27.0) | +10.3 (26.2) | +9.5 (26.5) | -4.3 (15.3) | +5.1 (13.2) |
| C2 20R(m0 1.0) on composite vs UNLOCKED as-is | +9.5 (33.5) | +12.6 (21.5) | +9.8 (23.0) | -3.6 (15.1) | +6.5 (14.7) |
| C2 30R(m0 1.0) on composite vs UNLOCKED as-is | +17.4 (24.2) | +16.2 (18.5) | +14.2 (17.8) | -2.9 (14.9) | +10.0 (13.9) |
| C3 like-for-like 12R(m0 1.0) on BOTH | +23.7 (21.1)* | +21.7 (27.1) | +17.7 (27.1) | +4.7 (11.9) | +8.9 (13.7) |
| C3 like-for-like 20R(m0 1.0) on BOTH | +6.7 (31.8) | +15.5 (24.1) | +11.8 (24.6) | +1.3 (14.9) | +11.3 (14.9) |
| C3 like-for-like 30R(m0 1.0) on BOTH | +16.3 (23.2) | +15.6 (18.2) | +13.6 (17.5) | -0.6 (14.4) | +10.1 (13.9) |
| C2 12R(m0 0.5) on composite vs UNLOCKED as-is | +15.5 (27.0) | +10.6 (26.1) | +10.2 (26.0) | -8.5 (15.1) | +6.1 (12.7) |
| C2 20R(m0 0.5) on composite vs UNLOCKED as-is | +9.7 (33.7) | +12.6 (21.6) | +9.9 (23.0) | -3.1 (15.5) | +6.0 (14.3) |
| C2 30R(m0 0.5) on composite vs UNLOCKED as-is | +10.3 (34.3) | +12.6 (22.0) | +11.1 (20.6) | -2.2 (14.7) | +10.0 (13.8) |
| C3 like-for-like 12R(m0 0.5) on BOTH | +27.5 (19.5)* | +23.3 (26.9) | +19.6 (26.5) | +0.7 (11.1) | +8.1 (11.6) |
| C3 like-for-like 20R(m0 0.5) on BOTH | +15.4 (22.6) | +19.0 (19.7) | +14.2 (21.6) | +4.5 (12.8) | +9.9 (14.6) |
| C3 like-for-like 30R(m0 0.5) on BOTH | +10.6 (31.5) | +12.8 (21.0) | +10.6 (20.1) | +2.1 (13.8) | +14.4 (15.3) |
| memo: effect of the combined lock on the composite alone, 12R (m0 1.0) | -4.8 (12.2) | -8.6 (13.7) | -7.0 (15.8) | -8.2 (12.0) | -6.4 (8.8) |
| memo: effect of the combined lock on the as-is alone, 12R (m0 1.0) | -8.2 (23.6) | -11.4 (14.3) | -8.2 (13.6) | -8.9 (10.4) | -3.8 (8.0) |

### Table E: risk lines, weekly series, mean / maxDD / worst week / worst-20 sum ($k; composite and as-is with the SAME lock, m0 1.0, slip +0.25)

| lock | row | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | composite | 34.4/21/-21/482 | 41.1/23/-23/371 | 38.6/97/-68/136 | 23.1/241/-120/-875 | 8.0/121/-66/-420 |
| off | as-is | 12.2/88/-88/170 | 21.7/88/-88/58 | 21.9/144/-88/-187 | 18.6/162/-96/-811 | -3.4/317/-71/-572 |
| 12R | composite | 29.0/27/-27/406 | 32.3/27/-27/181 | 31.4/35/-27/-6 | 15.1/233/-46/-608 | 1.0/120/-45/-468 |
| 12R | as-is | 3.9/105/-30/55 | 10.4/116/-30/-260 | 13.7/116/-30/-433 | 9.7/276/-30/-585 | -7.2/436/-30/-584 |
| 20R | composite | 23.8/64/-64/333 | 34.8/64/-64/195 | 32.0/65/-64/-60 | 15.9/190/-72/-754 | 3.3/133/-58/-537 |
| 20R | as-is | 15.0/49/-49/209 | 18.8/96/-49/-24 | 19.8/127/-49/-253 | 13.6/229/-49/-955 | -8.3/463/-49/-766 |
| 30R | composite | 31.6/37/-37/442 | 38.4/37/-37/293 | 36.3/92/-68/64 | 16.1/208/-92/-888 | 6.7/133/-58/-474 |
| 30R | as-is | 13.3/73/-73/186 | 22.3/73/-73/73 | 22.5/139/-73/-166 | 16.3/145/-73/-927 | -3.4/318/-72/-573 |

### Table F: combined-lock fires (weeks fired / weeks in window; slip +0.25, K6 70/30)

| lock | row | L3M | L6M | HOLD | PRE | X' | all 149 |
|---|---|---|---|---|---|---|
| 8R m0 1.0 | composite | 7/14 | 12/28 | 14/32 | 46/75 | 30/44 | 90 |
| 8R m0 1.0 | as-is | 10/14 | 17/28 | 20/32 | 47/75 | 33/44 | 100 |
| 8R m0 0.5 | composite | 7/14 | 13/28 | 15/32 | 49/75 | 33/44 | 97 |
| 8R m0 0.5 | as-is | 11/14 | 18/28 | 21/32 | 50/75 | 33/44 | 104 |
| 12R m0 1.0 | composite | 4/14 | 8/28 | 10/32 | 38/75 | 23/44 | 71 |
| 12R m0 1.0 | as-is | 7/14 | 12/28 | 15/32 | 34/75 | 23/44 | 72 |
| 12R m0 0.5 | composite | 4/14 | 8/28 | 10/32 | 42/75 | 24/44 | 76 |
| 12R m0 0.5 | as-is | 8/14 | 13/28 | 16/32 | 38/75 | 25/44 | 79 |
| 16R m0 1.0 | composite | 4/14 | 6/28 | 8/32 | 29/75 | 17/44 | 54 |
| 16R m0 1.0 | as-is | 3/14 | 5/28 | 8/32 | 25/75 | 19/44 | 52 |
| 16R m0 0.5 | composite | 4/14 | 6/28 | 8/32 | 36/75 | 21/44 | 65 |
| 16R m0 0.5 | as-is | 6/14 | 8/28 | 11/32 | 32/75 | 24/44 | 67 |
| 20R m0 1.0 | composite | 3/14 | 5/28 | 7/32 | 28/75 | 13/44 | 48 |
| 20R m0 1.0 | as-is | 1/14 | 3/28 | 5/32 | 19/75 | 11/44 | 35 |
| 20R m0 0.5 | composite | 4/14 | 6/28 | 8/32 | 33/75 | 17/44 | 58 |
| 20R m0 0.5 | as-is | 5/14 | 7/28 | 10/32 | 27/75 | 18/44 | 55 |
| 30R m0 1.0 | composite | 1/14 | 2/28 | 3/32 | 21/75 | 8/44 | 32 |
| 30R m0 1.0 | as-is | 1/14 | 1/28 | 2/32 | 9/75 | 1/44 | 12 |
| 30R m0 0.5 | composite | 2/14 | 3/28 | 5/32 | 22/75 | 9/44 | 36 |
| 30R m0 0.5 | as-is | 2/14 | 2/28 | 5/32 | 20/75 | 12/44 | 37 |

### Where
Code `l2vast/ds3/code/oneconv/` (oc_lib.py = ls2_lib + m0 option + in-engine parity stop on top of the PB7 sundaydecision setup; run_oc.py, run_lib.py for bridge row 0 on the library-PB engine, tab_oc.py), results `l2vast/ds3/out/oneconv/` (oc_res.pkl, lib_res.pkl, tables.md, run_oc.log). Tie-outs: library-PB V0 +25.0/+22.8/+19.3/+7.4/+12.9; PB7 Native no-lock +25.5/+21.8/+18.7/+6.1/+11.8; library-PB all-signal 12R +17.9/+16.5/+15.3/+0.3/+2.3 (reproduced in the check run). Caveats: composite-minus-as-is deltas under a lock have wide MDE; the combined lock multiple, m0 and the lock basis (MTM vs realised) are guesses; everything is post-hoc.
