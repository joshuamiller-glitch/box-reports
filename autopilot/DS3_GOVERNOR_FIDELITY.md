# DS3_GOVERNOR_FIDELITY - GOV-1 task A: the research lock engine vs D6 as coded (user facts 2026-10-31 14:30Z)

Research only. UNTOUCHED never read (capped 20260206); windows L3M 20251106.., L6M 20250801.., HOLD 20250701.., PRE 20240201..20250630, X' 20230401..20240131. N basis, Native 1.28, live lots (K6 2, P6 7, U6 4, H6 4/2, M6 2, A6 1; 70/30 integer split, add slip +0.25, A6 market, ER lots half-up min 1). Code `l2vast/ds3/code/govfid/gf_lib.py` (extends ss2_lib in place), outputs `l2vast/ds3/out/govfid/`. TIE-OUT: with no options gf_lib returns the SS-2 headline to the dollar (+19.4k / +18.5k / +16.2k / +4.7k / +12.5k vs as-is, L3M/L6M/HOLD/PRE/X') and the integer composite +25.0/+22.8/+19.3/+7.4/+12.9. Label day = 18:00 ET rollover verified on all 44,370 rows (0 mismatches).

## Page 1

**Plain sentence.** The SS-2 engine already matches D6 on every per-book lock (entry test +5R/-2R, day arm 2R keep 50%, per-book week floor 12R, R = base lot x running-max SizeMult x 60 pt x $20, reset at the 18:00 ET label day, per book not stack). The ONE real difference is that it has NO combined (stack) week lock. Adding it in K6's BookR (K6 base 2 lots x SizeMult x 60 x 20 = $2,400 per R, i.e. 12R = $28.8k at SizeMult 1, $14.4k at 0.5) costs money and fires in about half of all weeks: the Sunday composite falls from +46.8k to +40.5k $/wk (L6M) and the D6-faithful delta vs the stack as it is becomes +17.9k / +16.5k / +15.3k / +0.3k / +2.3k (L3M/L6M/HOLD/PRE/X'; MDE 29/21/22/15/14k): positive in the recent windows, nothing in PRE and X'. The size of the combined lock is the key unknown: **the multiple (12R? 8R?) of the combined week lock is not in any text I have**; the table sweeps 4..30R. Lead assumption used for the headline: same 12R as the per-book floor.

**D6-faithful composite (integer half-up min-1 lots, live lots, Native 1.28, N basis, combined 12R lock in K6 R), $k/wk, delta vs the stack as it is (MDE):**

| | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| SS-2 engine, as coded composite (no combined lock) | +25.0 (22.6) | +22.8 (17.6) | +19.3 (17.3) | +7.4 (13.0) | +12.9 (15.0) |
| D6-faithful: all-signal running max, session-lot R, per-book locks, + combined 12R(K6) | +17.9 (29.2) | +16.5 (21.0) | +15.3 (21.9) | +0.3 (14.8) | +2.3 (14.0) |
| same, K6 at market / others 70-30 | +16.0 (29.1) | +16.0 (20.9) | +15.1 (21.8) | +0.9 (15.1) | +1.4 (13.8) |
| effect of the combined lock alone (D6-faithful minus no combined) | see sweep, F=12: -6.5 (11.6) | -5.8 (7.1) | -3.5 (11.7) | -6.7 (11.7) | -11.1 (11.2) |

Reading: the combined lock loses in every window (L6M -5.8k with MDE 7.1k, i.e. at the edge; X' -11.1k inside MDE 11.2k); it fires 4 / 8 / 10 / 35 / 28 times (L3M/L6M/HOLD/PRE/X' = weeks, of 14/28/32/75/44) and 73 of 149 weeks overall. Tighter (4-8R) is ruinous (L6M -14k to -38k); looser than 30R is inert. Whether it lowers risk is not scored here (no maxDD claim): see the weekly stats columns in out/govfid/. Tier: STRUCTURE / measurement (fidelity), not a candidate.

## Differences list (research engine vs D6 facts)

| # | item | D6 as coded (user) | research engine (ss2_lib run_book3) | status / effect |
|---|---|---|---|---|
| 1 | COMBINED week lock | exists; threshold in R = K6 BookR | NOT in the engine (per-book locks only) | added in gf_lib. Fires in 73/149 weeks at 12R; -5.8k L6M. Multiple unknown (assumed 12R) |
| 2 | BookR | BASE lots x SizeMult x stop pts x $20 | LN (max session lot) x running max x 60 x 20 (WT 45) | same, except H6: engine uses 4 lots in NY-AM where the planned lot is 2 (V2: using the session lot costs -1.0k L6M) |
| 3 | SizeMult | running max of the book's sized signals today, set at each sized signal, reset 18:00 ET | cummax over the signals the book TOOK (passes zone skip, one-position rule); entry-test-skipped signals count; zone-skipped and busy-blocked do not; threshold updated only at taken entries | V1 (all signals feed the max): +0.4k L6M, noise |
| 4 | reset time | 18:00 ET | label day = 18:00 ET rollover (verified); the multiplier in force between 18:00 and the first entry of the new day is the previous day's (stale) for the week floor | small; D6 reset value (1.0 or none) unknown |
| 5 | day entry test +5R / -2R | x SizeMult | realised net of the book's closed trades of the label day (after slippage 0.5 pt + commission), threshold Rb x running max INCLUDING the current signal | same units; D6 may use gross P&L (platform) |
| 6 | day arm 2R keep 50% | x SizeMult | peak MTM of the book's label-day group >= 2 x R x mult(latest entry) and e <= 50% peak -> flatten, cancel later entries | same |
| 7 | per-book week floor 12R | R = own BookR | MTM since week start (ISO week of label day = Sunday 18:00 start) <= -12 x R x mult of the latest entered trade | same; fires: KB 10, PB 17, MV 4, PE 3, HM 2, SM 1, ST/WT 0 over 149 weeks |
| 8 | locks per book or stack | per book day/week; stack-level combined week | per book only | = item 1 |
| 9 | units | $; day locks x SizeMult, week lock same BookR | engine $ = real/1.75, R/1.75; identity-tested | same |
| 10 | stop pts | per D6 | fixed 60 (WT 45) regardless of signal stop | unknown if D6 uses the signal stop |
| 11 | mult on rounded lots | SizeMult = trend mult (1.5/0.5) | governors use the unrounded mult; lots are rounded | same |


## Tables

### Composite under each governor reading ($k/wk, mean; delta vs the SS-2 engine V0 (MDE in brackets))
| config | mean L3M | L6M | HOLD | PRE | X' | d vs V0: L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|---|
| stack as it is (no D6 rules; join 2.45) | 13.8 | 24.0 | 23.7 | 17.7 | -3.6 | -25.0 (22.6) | -22.8 (17.6) | -19.3 (17.3) | -7.4 (13.0) | -12.9 (15.0) |
| SS-2 headline (fractional lots, running max) | 33.2 | 42.6 | 39.9 | 22.4 | 9.0 | -5.7 (10.2) | -4.2 (6.0) | -3.1 (5.5) | -2.7 (4.2) | -0.3 (2.4) |
| V0 SS-2 engine, integer half-up min-1 lots (as coded composite) | 38.9 | 46.8 | 43.0 | 25.1 | 9.3 | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) | +0.0 (0.0) |
| V1 running max over ALL the book signals (also zone-skipped / busy-blocked / unconfirmed) | 39.3 | 47.2 | 43.2 | 25.1 | 9.5 | +0.5 (1.1) | +0.4 (0.7) | +0.2 (0.7) | -0.0 (0.6) | +0.1 (0.6) |
| V2 BookR on the SESSION planned lot (H6 NY-AM 2 not 4) | 37.4 | 45.8 | 42.2 | 24.8 | 9.7 | -1.5 (2.4) | -1.0 (1.5) | -0.8 (1.3) | -0.4 (1.0) | +0.3 (0.7) |
| V4 = V1+V2, no combined lock | 38.1 | 46.3 | 42.6 | 24.7 | 9.8 | -0.7 (2.9) | -0.5 (1.6) | -0.5 (1.4) | -0.4 (1.2) | +0.5 (1.0) |
| V3 = V0 + COMBINED week lock 12R(K6) | 33.1 | 40.3 | 38.6 | 15.8 | 1.6 | -5.8 (10.5) | -6.5 (7.8) | -4.4 (12.7) | -9.3 (13.3) | -7.8 (9.4) |
| V4+comb12 = D6-faithful (headline) | 31.7 | 40.5 | 39.1 | 18.0 | -1.3 | -7.2 (10.5) | -6.3 (6.6) | -4.0 (11.6) | -7.1 (12.2) | -10.6 (11.2) |
| K6 at market, V0 | 36.5 | 46.1 | 42.6 | 24.5 | 9.5 | -2.4 (3.7) | -0.7 (2.4) | -0.4 (2.2) | -0.6 (1.1) | +0.1 (1.1) |
| K6 at market, D6-faithful comb12 | 29.8 | 40.0 | 38.8 | 18.6 | -2.2 | -9.0 (11.0) | -6.8 (7.0) | -4.3 (11.9) | -6.5 (12.1) | -11.5 (11.4) |

### D6-faithful (V4+comb12) minus ASIS, and V0 minus ASIS
| | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| V0_SS2 vs ASIS | +25.0 (22.6) | +22.8 (17.6) | +19.3 (17.3) | +7.4 (13.0) | +12.9 (15.0) |
| V4_noc vs ASIS | +24.3 (22.7) | +22.3 (17.6) | +18.9 (17.3) | +7.0 (13.1) | +13.4 (14.7) |
| V4_comb12 vs ASIS | +17.9 (29.2) | +16.5 (21.0) | +15.3 (21.9) | +0.3 (14.8) | +2.3 (14.0) |
| V5_K6mkt_V4 vs ASIS | +16.0 (29.1) | +16.0 (20.9) | +15.1 (21.8) | +0.9 (15.1) | +1.4 (13.8) |

### Combined week lock threshold sweep (V4 engine; F x R_K6; delta vs V4 without the combined lock, MDE; weeks fired / weeks in window)
| F (R of K6) | d L3M | L6M | HOLD | PRE | X' | fired L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|---|
| 4 | -35.9 (36.2) | -38.2 (25.5) | -30.9 (26.1) | -18.6 (17.3) | -14.6 (13.2) | 11/14 | 21/28 | 23/32 | 60/75 | 40/44 |
| 6 | -33.7 (37.3) | -31.1 (24.9) | -24.9 (25.1) | -17.8 (16.6) | -15.4 (13.3) | 9/14 | 17/28 | 19/32 | 56/75 | 37/44 |
| 8 | -11.2 (17.0) | -13.8 (16.0) | -10.0 (17.6) | -14.4 (15.3) | -16.0 (13.4) | 5/14 | 11/28 | 13/32 | 49/75 | 34/44 |
| 10 | -6.3 (11.1) | -11.7 (15.0) | -8.6 (16.8) | -8.6 (12.9) | -15.7 (13.0) | 4/14 | 10/28 | 12/32 | 40/75 | 33/44 |
| 12 | -6.5 (11.6) | -5.8 (7.1) | -3.5 (11.7) | -6.7 (11.7) | -11.1 (11.2) | 4/14 | 8/28 | 10/32 | 35/75 | 28/44 |
| 16 | -7.6 (12.7) | -4.7 (6.9) | -2.9 (11.3) | -7.7 (12.0) | -11.1 (11.0) | 4/14 | 6/28 | 8/32 | 32/75 | 22/44 |
| 20 | -11.4 (19.9) | -6.8 (10.4) | -6.7 (12.1) | -7.7 (11.2) | -5.4 (8.1) | 4/14 | 6/28 | 8/32 | 28/75 | 14/44 |
| 30 | +0.0 (0.0) | -1.4 (4.0) | +0.1 (4.9) | -9.3 (10.7) | -2.9 (5.0) | 0/14 | 1/28 | 3/32 | 21/75 | 9/44 |

### Fire counts, D6-faithful V4+comb12 (events in window; book-days / book-weeks). entry test = SIGNALS skipped (+5R hit / -2R hit); day arm = book-days flattened; week floor = book-weeks flattened
| lock | book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| window days / weeks | - | 67 / 14 | 136 / 28 | 159 / 32 | 368 / 75 | 218 / 44 |
| entry +5R skips | KB | 1 | 2 | 2 | 38 | 0 |
| entry -2R skips | KB | 64 | 91 | 104 | 232 | 34 |
| day arm | KB | 14 | 20 | 21 | 48 | 7 |
| week floor | KB | 1 | 2 | 2 | 5 | 3 |
| entry +5R skips | PE | 0 | 0 | 0 | 11 | 0 |
| entry -2R skips | PE | 28 | 36 | 37 | 108 | 10 |
| day arm | PE | 14 | 22 | 24 | 38 | 7 |
| week floor | PE | 0 | 0 | 0 | 2 | 0 |
| entry +5R skips | SM | 0 | 0 | 0 | 0 | 0 |
| entry -2R skips | SM | 2 | 3 | 3 | 4 | 0 |
| day arm | SM | 0 | 0 | 0 | 0 | 0 |
| week floor | SM | 0 | 0 | 0 | 1 | 0 |
| entry +5R skips | HM | 5 | 8 | 8 | 9 | 0 |
| entry -2R skips | HM | 21 | 36 | 38 | 89 | 33 |
| day arm | HM | 15 | 17 | 19 | 50 | 17 |
| week floor | HM | 0 | 0 | 0 | 2 | 0 |
| entry +5R skips | MV | 0 | 0 | 0 | 7 | 0 |
| entry -2R skips | MV | 38 | 43 | 45 | 87 | 17 |
| day arm | MV | 5 | 10 | 10 | 12 | 2 |
| week floor | MV | 1 | 1 | 2 | 2 | 0 |
| entry +5R skips | PB | 15 | 17 | 18 | 75 | 1 |
| entry -2R skips | PB | 64 | 96 | 116 | 419 | 76 |
| day arm | PB | 36 | 58 | 63 | 94 | 40 |
| week floor | PB | 2 | 3 | 4 | 10 | 3 |
| COMBINED week lock (12R of K6) | stack | 4 | 8 | 10 | 35 | 28 |

combined-lock fires: weeks fired 73 of 149; mean open positions flattened at the fire 2.2; entries cancelled for the rest of week (rows) mean 55.0

### Per-book week floor 12R fires (V0 engine, per-book BookR with running max); same without sizing (ASIS) for contrast
| book | L3M | L6M | HOLD | PRE | X' | all |
|---|---|---|---|---|---|---|
| KB | 1 | 2 | 2 | 5 | 3 | 10 |
| PE | 0 | 0 | 1 | 2 | 0 | 3 |
| SM | 0 | 0 | 0 | 1 | 0 | 1 |
| HM | 0 | 0 | 0 | 2 | 0 | 2 |
| MV | 1 | 1 | 2 | 2 | 0 | 4 |
| PB | 2 | 3 | 4 | 10 | 3 | 17 |

## Notes
- Fire counts are counts of events in the final lock_all pass of the composite run (entry-test lines are SIGNALS skipped; day arm = book-days; week = book-weeks).
- Open questions: (1) the combined week lock multiple and whether it is measured on MTM or realised; (2) does the combined lock also have a day level; (3) D6 SizeMult reset value. All answered by default above; queue not paused.
