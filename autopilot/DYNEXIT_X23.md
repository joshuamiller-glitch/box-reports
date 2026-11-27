# DYNEXIT_X23 - liquidity targets and stops (W-DYNL). Updated 04:30Z. Research only.

## ANSWER FIRST
1. WHICH LIQUIDITY IS REAL (first table, matched-density null: same level set shifted 3-25 pts so density and distance match; 22,063 live-book entries): pools are a more likely TARGET than a random price in Asia (reach of the nearest pool ahead: running session extremes/ON/day 53% vs 43%, swing-5 62% vs 52%, swing-15 47 vs 41, VWAP and bands 56-63% vs 47-50%, equal highs/lows 33 vs 27; NY AM only +2 to +4 points: RTH open, swing-5/15, VWAP). They are NOT a barrier: through / reverse / stall at the pool and sweep-then-reverse equal random everywhere. Round numbers, LVN, 1-min FVG, order blocks, prior day/week, IB, 5/20-day profile levels = random. As STOP references: VWAP and bands (Asia) and RTH open (NY AM) are swept before the trade works MORE often than random (do not rest a stop just beyond VWAP); swing-60 (Asia) and FVG (NY AM) behind are swept LESS (the only protectors seen, z -4 and -3).
2. STRATEGY (quick screen, 17 live books, 1 lot, reference = book's own bracket; Trade Health layer is not in the quick screen): NO PASS. FIXED-RULE row (defaults committed before scoring, /mnt/l2/l2vast/_dynexit/fixed_rules_x23.json): replacing stop and target by liquidity levels loses 40-110% of income (X23a hlsw -73% L6M, X23e -112%, X23h loses money); only X23c f5 (target = far edge of 5-min FVG) and X23g (UW walls, mostly inactive = own bracket) stay near own income, not shallower in L6M/L3M. WALK-FORWARD 2/4/13: no family passes at 2 or 4 weeks; X23c NY AM passes at 13 weeks only (9/13 periods, income -6%, chained max DD equal to own), X23h Asia 13 weeks 5/13 weak. Faster re-fit does not help.
3. RANDOM-LEVEL NULL (5 shifted-level draws per set and variant, 16 sets x 3 variants, summed over books): the pool recipes are NOT distinguishable from shifted random levels except two weak leads: Asia equal-high/low STOP (stop 3 pts beyond equal highs/lows behind: L3M dd -28% income +17%, L6M dd -10% income +18%; null dd +27%/income 0%; 3 books) and 20-day composite POC/VA target+stop (L6M dd -28% income -6%, 4/4 years, but rarely active, L3M fails). Order blocks and UW walls as targets: shifted nulls do as well (an effect of a nearer random target).
4. DYNAMIC vs STATIC (order 0340Z): dynamic twins (level re-read each bar, widen caps 1.25/1.5, hysteresis 4 ticks, min 30 s) are WORSE than static: swings/equal/hlsw L6M dd +100% to +440%, FVG/profile/UW dynamic income -70% to -100%; 1-2 order changes per trade (hysteresis 4 ticks: 1.85, 30 s: 2.0). Widening does not rescue them. Reading: re-targeting to the next level every bar chases price and cuts winners.
5. OPTIONS WALLS: historical per-day NDX walls/flip exist 2024-10-01..2026-11 (528 days, scaled to NQ by the same-day NQ/NDX ratio, available from the next Globex day, STATIC per day, built from end-of-day files); true intraday wall data (W-WF1112 file /mnt/l2/l2vast/_dynexit/uw_intraday_walls.parquet) = 9 days (13-25 Nov), no overlap with the 17 books' entries in the scored sample: THIN, forward register only.
6. Candidates file (weak leads, marked): /mnt/l2/l2vast/_dynexit/x23_candidates.json. Nothing clears the first clause of SOLUTION. X23b sweep behaviour: sweep-then-reverse = null in every type (table below), so no sweep rule was built beyond it. X22 join: X23 rows are in dq_wf.load format in /mnt/l2/l2vast/_dynexit/x23/live2 (names X23*) for W-DYNQ's pick pool.
LUCK CHARGE: 22,063 entries x 38 types x 2 sessions x ahead/behind (first table); 280 recipes/book x 17 books (static a,c,e,g,h 100, nulls 240 incl P twins, dynamic 40, random-skip 12) = ~4,700 recipe-books; best-of-many correction applies to the two weak leads.

## Method (all causal)
- Subjects: /mnt/l2/l2vast/_dynexit/x8/entries3.parquet (W-DYNX8), entry bar = last 1-min bar closed <= entry-2 s (tm60 bars); distances from entry price. MINSEP 2 pts.
- Levels: prior day H/L/C, prior week H/L, overnight (to 09:30), Asia 18:00-03:00, London 03:00-09:30 (running values, only past), IB (after 10:30), day extremes, day/week/RTH open, round numbers 25/50/100, swing highs/lows size 5/15/60 minutes (CONFIRMATION LAG = n minutes; only unswept swings in the last 13 h), equal highs/lows (two size-5 swings within 1.5 pts), prior-day / 5-day / 20-day composite POC, value-area edges (70%), low-volume nodes of the prior day, day VWAP +-1/2 sigma, weekly VWAP +-1 sigma, 3-bar fair value gaps (1-min and 5-min, untouched only; edges), order blocks (last opposite bar before a >=3 ATR displacement bar, unmitigated).
- Ahead: nearest pool ahead; reached = bar high/low touches within 90 bars. At touch: through = 15 pts beyond first, reverse = 15 pts back first, stall = neither in 10 bars. Sweep = >=2 pts through in first 3 bars, then reverse vs through. Behind: nearest pool behind swept by >=1 pt before price reaches +20 pts (works).
- Null: same entry, price at distance d x U(0.7,1.3) with no same-family level within 1.5 pts, 3 draws. z = two-proportion z (naive, overlapping entries so inflate; the family-wide scan has ~38 types x 2 sessions x 2 sides, treat |z|<4 as noise).
- Per-entry-minute bars cannot order events inside one bar: touch and reaction share bars (ambiguous 'both' cases counted in reverse+through only when separable).
- Caveats: UW options walls (X23g), traded-tape clusters/absorption (X23e part), order book and MBO (X23d/f: W-DYNX8) are not in this first table. UW intraday by-strike history exists only since 18 Nov (static per day = THIN); to be added.

## Tables (first, OLD forbidden-zone null; the matched-density table is /mnt/l2/l2vast/_dynexit/x23/first_tables2.md, the one to read)

### AS - AHEAD: nearest pool ahead vs same-distance random price (null = 3 draws/entry)

| type | n pools | reach% pool | reach% null | z | thru% (of touched) pool | null | rev% pool | null | stall% pool | sweep->reverse% pool | null | dyn reach% | dyn thru% |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PDH_L | 5159 | 10.4 | 10.1 | +0.6 | 47 | 44 | 26 | 30 | 27 | 34 | 34 | - | - |
| PDC | 1448 | 41.2 | 35.7 | +3.7 | 30 | 34 | 27 | 32 | 42 | 41 | 43 | - | - |
| PWH_L | 4909 | 2.6 | 2.5 | +0.4 | 48 | 46 | 33 | 36 | 17 | 33 | 37 | - | - |
| ON | 5261 | 53.5 | 49.8 | +4.6 | 33 | 35 | 26 | 29 | 40 | 39 | 38 | - | - |
| AS | 5261 | 53.5 | 49.5 | +4.9 | 33 | 35 | 26 | 29 | 40 | 39 | 38 | - | - |
| DAY | 5261 | 53.5 | 49.8 | +4.5 | 33 | 34 | 26 | 29 | 40 | 39 | 38 | - | - |
| DOPEN | 1439 | 41.4 | 35.6 | +3.9 | 31 | 37 | 25 | 30 | 42 | 38 | 37 | - | - |
| WOPEN | 2420 | 11.7 | 10.5 | +1.7 | 37 | 38 | 29 | 34 | 33 | 43 | 40 | - | - |
| R25 | 6105 | 68.8 | 65.1 | +5.1 | 34 | 36 | 32 | 33 | 33 | 42 | 41 | - | - |
| R50 | 6105 | 51.2 | 49.0 | +3.0 | 39 | 39 | 34 | 34 | 27 | 40 | 40 | - | - |
| R100 | 6105 | 33.8 | 32.6 | +1.8 | 43 | 42 | 34 | 36 | 22 | 39 | 39 | - | - |
| SW5 | 5649 | 61.7 | 58.2 | +4.5 | 33 | 37 | 26 | 29 | 40 | 37 | 37 | - | - |
| SW15 | 5514 | 47.3 | 44.9 | +3.1 | 37 | 38 | 26 | 29 | 37 | 36 | 35 | - | - |
| SW60 | 5056 | 26.6 | 26.0 | +0.8 | 42 | 39 | 24 | 29 | 33 | 33 | 35 | - | - |
| EQ | 1667 | 32.5 | 28.2 | +3.3 | 32 | 36 | 16 | 18 | 51 | 29 | 26 | - | - |
| P1POC | 1853 | 30.1 | 27.2 | +2.4 | 33 | 40 | 35 | 33 | 32 | 43 | 38 | - | - |
| P1VAH | 2245 | 19.7 | 17.5 | +2.3 | 28 | 28 | 28 | 29 | 44 | 45 | 43 | - | - |
| P1VAL | 2679 | 9.3 | 8.6 | +1.1 | 35 | 41 | 31 | 29 | 33 | 38 | 32 | - | - |
| P5POC | 2551 | 11.1 | 10.2 | +1.2 | 37 | 40 | 32 | 31 | 29 | 40 | 35 | - | - |
| P5VAH | 2657 | 8.4 | 7.3 | +2.0 | 26 | 31 | 29 | 26 | 44 | 41 | 40 | - | - |
| P5VAL | 2807 | 7.1 | 6.8 | +0.6 | 34 | 38 | 36 | 37 | 27 | 47 | 42 | - | - |
| P20POC | 2759 | 6.2 | 5.9 | +0.4 | 34 | 36 | 35 | 37 | 31 | 45 | 42 | - | - |
| P20VAH | 2815 | 3.8 | 3.6 | +0.6 | 42 | 39 | 25 | 25 | 33 | 30 | 31 | - | - |
| P20VAL | 2883 | 3.1 | 2.6 | +1.2 | 34 | 46 | 41 | 38 | 25 | 50 | 40 | - | - |
| VW | 736 | 56.8 | 50.7 | +2.8 | 35 | 40 | 30 | 34 | 34 | 37 | 40 | 62 | 35 |
| VWp1 | 1170 | 60.3 | 52.6 | +4.4 | 27 | 33 | 31 | 33 | 42 | 47 | 43 | 64 | 26 |
| VWm1 | 1129 | 62.5 | 54.9 | +4.4 | 30 | 33 | 36 | 39 | 33 | 48 | 47 | 66 | 31 |
| VWp2 | 2470 | 52.1 | 46.3 | +4.8 | 27 | 31 | 24 | 25 | 49 | 40 | 38 | 45 | 26 |
| VWm2 | 2375 | 55.6 | 51.5 | +3.4 | 34 | 38 | 30 | 33 | 35 | 41 | 40 | 50 | 33 |
| WVW | 2137 | 14.6 | 13.2 | +1.6 | 36 | 37 | 33 | 34 | 31 | 40 | 41 | - | - |
| WVWpm1 | 3461 | 24.2 | 21.2 | +3.7 | 32 | 35 | 35 | 34 | 33 | 47 | 42 | - | - |
| LVN | 4396 | 64.6 | 53.8 | +11.8 | 30 | 32 | 30 | 30 | 40 | 42 | 41 | - | - |
| FVG1 | 3738 | 42.2 | 40.3 | +2.0 | 38 | 38 | 30 | 34 | 32 | 36 | 39 | - | - |
| FVG5 | 4157 | 28.0 | 26.0 | +2.5 | 39 | 39 | 32 | 33 | 28 | 41 | 39 | - | - |
| OB | 1599 | 22.6 | 21.2 | +1.2 | 36 | 37 | 27 | 30 | 37 | 36 | 37 | - | - |

### AS - BEHIND: nearest pool behind swept (>=1 pt) before the trade works (+20 pts), vs null

| type | n | swept-before-work% pool | null | z | swept at all% pool | null | P(works later | swept) pool | null |
|---|---|---|---|---|---|---|---|---|
| PDH_L | 5879 | 2.9 | 2.7 | +0.7 | 4 | 4 | 16 | 12 |
| PDC | 4489 | 20.4 | 18.4 | +2.9 | 27 | 25 | 18 | 16 |
| PWH_L | 5294 | 1.5 | 1.4 | +0.2 | 2 | 2 | 16 | 19 |
| ON | 6095 | 13.0 | 12.8 | +0.2 | 17 | 17 | 10 | 10 |
| AS | 6095 | 13.0 | 12.8 | +0.2 | 17 | 17 | 10 | 10 |
| DAY | 6095 | 13.0 | 12.7 | +0.4 | 17 | 17 | 10 | 10 |
| DOPEN | 4489 | 20.7 | 19.1 | +2.3 | 27 | 26 | 18 | 16 |
| WOPEN | 3613 | 8.3 | 7.5 | +1.6 | 11 | 10 | 19 | 17 |
| R25 | 6105 | 54.6 | 49.8 | +6.3 | 66 | 62 | 35 | 31 |
| R50 | 6105 | 38.5 | 35.1 | +4.7 | 49 | 47 | 29 | 27 |
| R100 | 6105 | 23.3 | 21.4 | +3.0 | 32 | 30 | 25 | 22 |
| SW5 | 6080 | 35.0 | 32.8 | +3.1 | 45 | 44 | 16 | 17 |
| SW15 | 6015 | 19.7 | 20.0 | -0.5 | 26 | 26 | 10 | 10 |
| SW60 | 5712 | 5.3 | 6.1 | -2.3 | 7 | 8 | 6 | 5 |
| EQ | 2879 | 15.3 | 14.6 | +1.0 | 18 | 18 | 8 | 8 |
| P1POC | 4143 | 15.2 | 14.0 | +1.9 | 20 | 19 | 20 | 19 |
| P1VAH | 3775 | 10.5 | 8.9 | +2.9 | 14 | 12 | 21 | 18 |
| P1VAL | 3387 | 5.5 | 4.8 | +1.6 | 7 | 6 | 18 | 15 |
| P5POC | 3505 | 6.8 | 6.1 | +1.5 | 9 | 8 | 19 | 16 |
| P5VAH | 3418 | 4.0 | 3.8 | +0.7 | 5 | 5 | 17 | 14 |
| P5VAL | 3283 | 3.7 | 3.0 | +1.8 | 5 | 5 | 20 | 21 |
| P20POC | 3316 | 4.1 | 3.6 | +1.3 | 6 | 5 | 24 | 21 |
| P20VAH | 3274 | 1.7 | 1.7 | +0.2 | 2 | 2 | 19 | 19 |
| P20VAL | 3212 | 2.1 | 1.8 | +0.9 | 3 | 2 | 26 | 22 |
| VW | 5098 | 33.5 | 30.5 | +3.9 | 43 | 41 | 20 | 20 |
| VWp1 | 4496 | 31.7 | 27.3 | +5.5 | 40 | 36 | 21 | 19 |
| VWm1 | 4563 | 32.8 | 28.5 | +5.4 | 42 | 38 | 24 | 21 |
| VWp2 | 3378 | 18.6 | 16.5 | +2.8 | 24 | 23 | 18 | 15 |
| VWm2 | 3489 | 21.9 | 19.3 | +3.3 | 27 | 24 | 22 | 20 |
| WVW | 3859 | 13.2 | 11.3 | +3.3 | 18 | 15 | 19 | 18 |
| WVWpm1 | 5033 | 18.3 | 15.5 | +4.7 | 23 | 21 | 22 | 20 |
| LVN | 5304 | 46.8 | 35.8 | +13.7 | 54 | 44 | 36 | 30 |
| FVG1 | 5381 | 34.0 | 30.6 | +4.7 | 44 | 41 | 28 | 25 |
| FVG5 | 5143 | 17.9 | 16.7 | +2.1 | 24 | 23 | 18 | 18 |
| OB | 2907 | 16.1 | 15.4 | +0.8 | 20 | 20 | 14 | 15 |

### NYAM - AHEAD: nearest pool ahead vs same-distance random price (null = 3 draws/entry)

| type | n pools | reach% pool | reach% null | z | thru% (of touched) pool | null | rev% pool | null | stall% pool | sweep->reverse% pool | null | dyn reach% | dyn thru% |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PDH_L | 12580 | 21.2 | 21.3 | -0.2 | 51 | 53 | 43 | 41 | 3 | 42 | 38 | - | - |
| PDC | 6488 | 43.8 | 42.5 | +1.7 | 50 | 47 | 43 | 45 | 5 | 41 | 44 | - | - |
| PWH_L | 12730 | 7.4 | 7.4 | -0.0 | 50 | 49 | 40 | 43 | 8 | 40 | 42 | - | - |
| ON | 12048 | 37.4 | 37.2 | +0.5 | 53 | 52 | 42 | 42 | 3 | 40 | 40 | - | - |
| AS | 9879 | 38.3 | 37.4 | +1.6 | 49 | 49 | 44 | 44 | 4 | 43 | 42 | - | - |
| LO | 10781 | 45.0 | 44.5 | +0.9 | 56 | 51 | 39 | 43 | 4 | 38 | 41 | - | - |
| IB | 3345 | 39.7 | 38.4 | +1.3 | 48 | 47 | 44 | 43 | 8 | 45 | 42 | - | - |
| DAY | 14868 | 43.7 | 42.8 | +1.9 | 50 | 48 | 43 | 44 | 5 | 43 | 43 | - | - |
| DOPEN | 6474 | 43.8 | 42.8 | +1.4 | 50 | 48 | 44 | 44 | 5 | 41 | 43 | - | - |
| WOPEN | 7169 | 23.3 | 22.8 | +0.8 | 58 | 52 | 34 | 42 | 5 | 33 | 40 | - | - |
| RTHOPEN | 5322 | 62.4 | 59.3 | +4.0 | 43 | 46 | 51 | 48 | 3 | 51 | 47 | - | - |
| R25 | 15952 | 89.5 | 87.7 | +5.8 | 46 | 46 | 47 | 47 | 4 | 46 | 46 | - | - |
| R50 | 15952 | 78.5 | 77.3 | +3.0 | 48 | 47 | 45 | 45 | 4 | 44 | 44 | - | - |
| R100 | 15952 | 61.3 | 60.6 | +1.6 | 49 | 48 | 44 | 44 | 4 | 43 | 43 | - | - |
| SW5 | 12140 | 70.8 | 69.1 | +3.5 | 49 | 48 | 45 | 45 | 4 | 45 | 43 | - | - |
| SW15 | 11444 | 59.9 | 58.8 | +2.1 | 51 | 48 | 43 | 44 | 5 | 42 | 43 | - | - |
| SW60 | 9516 | 46.7 | 46.8 | -0.1 | 51 | 49 | 42 | 43 | 5 | 42 | 42 | - | - |
| EQ | 4045 | 51.5 | 50.5 | +1.1 | 44 | 46 | 49 | 46 | 5 | 49 | 45 | - | - |
| P1POC | 6533 | 43.0 | 41.6 | +2.0 | 48 | 48 | 46 | 45 | 2 | 45 | 43 | - | - |
| P1VAH | 7364 | 37.0 | 35.8 | +1.8 | 51 | 50 | 42 | 42 | 4 | 41 | 41 | - | - |
| P1VAL | 5705 | 20.2 | 19.1 | +1.8 | 46 | 47 | 48 | 45 | 2 | 45 | 44 | - | - |
| P5POC | 7245 | 23.6 | 23.3 | +0.5 | 50 | 50 | 42 | 43 | 4 | 41 | 41 | - | - |
| P5VAH | 8137 | 17.5 | 16.6 | +1.8 | 53 | 51 | 40 | 40 | 4 | 38 | 39 | - | - |
| P5VAL | 6041 | 15.2 | 14.7 | +0.8 | 42 | 49 | 48 | 42 | 7 | 50 | 41 | - | - |
| P20POC | 7188 | 16.0 | 15.5 | +1.0 | 54 | 50 | 41 | 44 | 3 | 35 | 42 | - | - |
| P20VAH | 8353 | 9.2 | 9.0 | +0.6 | 45 | 43 | 45 | 48 | 8 | 47 | 47 | - | - |
| P20VAL | 6101 | 11.1 | 11.1 | +0.1 | 49 | 48 | 47 | 47 | 2 | 44 | 45 | - | - |
| VW | 4868 | 64.7 | 63.2 | +1.9 | 46 | 46 | 47 | 47 | 4 | 46 | 46 | 71 | 47 |
| VWp1 | 6486 | 55.3 | 53.4 | +2.8 | 46 | 47 | 46 | 45 | 5 | 45 | 44 | 59 | 46 |
| VWm1 | 4183 | 60.6 | 59.1 | +1.7 | 46 | 46 | 47 | 47 | 2 | 45 | 46 | 67 | 45 |
| VWp2 | 9383 | 43.8 | 42.6 | +2.0 | 45 | 46 | 46 | 45 | 8 | 45 | 44 | 34 | 47 |
| VWm2 | 4659 | 46.1 | 44.8 | +1.6 | 49 | 50 | 45 | 44 | 2 | 44 | 42 | 43 | 49 |
| WVW | 6406 | 35.1 | 34.6 | +0.6 | 49 | 50 | 45 | 44 | 4 | 43 | 42 | - | - |
| WVWpm1 | 10190 | 43.4 | 41.8 | +2.8 | 46 | 48 | 46 | 45 | 4 | 45 | 44 | - | - |
| LVN | 10685 | 77.8 | 70.9 | +13.4 | 46 | 46 | 47 | 47 | 4 | 46 | 46 | - | - |
| FVG1 | 7922 | 70.8 | 69.2 | +2.6 | 49 | 48 | 44 | 46 | 3 | 42 | 44 | - | - |
| FVG5 | 10724 | 51.1 | 49.6 | +2.7 | 45 | 47 | 48 | 46 | 3 | 46 | 44 | - | - |
| OB | 3580 | 47.6 | 48.0 | -0.4 | 49 | 48 | 45 | 46 | 2 | 42 | 44 | - | - |

### NYAM - BEHIND: nearest pool behind swept (>=1 pt) before the trade works (+20 pts), vs null

| type | n | swept-before-work% pool | null | z | swept at all% pool | null | P(works later | swept) pool | null |
|---|---|---|---|---|---|---|---|---|
| PDH_L | 14191 | 8.0 | 7.8 | +0.9 | 16 | 16 | 20 | 18 |
| PDC | 9279 | 19.4 | 18.5 | +2.0 | 36 | 35 | 25 | 22 |
| PWH_L | 13706 | 2.6 | 2.6 | +0.3 | 6 | 6 | 20 | 19 |
| ON | 14897 | 11.6 | 11.7 | -0.5 | 24 | 24 | 18 | 18 |
| AS | 12670 | 14.5 | 13.9 | +1.7 | 28 | 28 | 22 | 20 |
| LO | 14410 | 14.5 | 14.4 | +0.4 | 29 | 30 | 19 | 19 |
| IB | 4899 | 10.8 | 10.8 | +0.1 | 18 | 18 | 17 | 16 |
| DAY | 15919 | 10.2 | 10.7 | -1.8 | 21 | 22 | 15 | 16 |
| DOPEN | 9293 | 19.3 | 18.5 | +1.6 | 36 | 35 | 24 | 23 |
| WOPEN | 8692 | 11.7 | 11.1 | +1.5 | 21 | 21 | 26 | 23 |
| RTHOPEN | 10150 | 32.6 | 29.6 | +5.7 | 53 | 51 | 35 | 32 |
| R25 | 15952 | 67.1 | 63.5 | +8.2 | 88 | 86 | 49 | 47 |
| R50 | 15952 | 50.6 | 48.0 | +5.6 | 77 | 75 | 39 | 37 |
| R100 | 15952 | 34.1 | 32.4 | +3.8 | 60 | 59 | 30 | 28 |
| SW5 | 14764 | 21.9 | 22.3 | -1.0 | 45 | 46 | 18 | 19 |
| SW15 | 13640 | 15.3 | 15.9 | -1.5 | 32 | 33 | 15 | 16 |
| SW60 | 10436 | 10.6 | 10.9 | -0.8 | 23 | 24 | 12 | 13 |
| EQ | 4341 | 14.6 | 15.0 | -0.6 | 29 | 30 | 15 | 15 |
| P1POC | 9203 | 19.2 | 18.0 | +2.7 | 36 | 34 | 25 | 23 |
| P1VAH | 8401 | 20.9 | 19.7 | +2.5 | 36 | 35 | 26 | 24 |
| P1VAL | 10168 | 7.5 | 7.3 | +0.8 | 13 | 13 | 29 | 27 |
| P5POC | 8611 | 11.3 | 10.6 | +1.7 | 21 | 21 | 26 | 23 |
| P5VAH | 7710 | 11.3 | 10.7 | +1.3 | 19 | 18 | 27 | 25 |
| P5VAL | 9854 | 6.2 | 5.8 | +1.3 | 10 | 10 | 29 | 27 |
| P20POC | 8681 | 6.7 | 6.1 | +2.1 | 13 | 13 | 23 | 20 |
| P20VAH | 7535 | 6.8 | 6.5 | +1.0 | 11 | 10 | 27 | 25 |
| P20VAL | 9809 | 3.2 | 3.0 | +0.9 | 6 | 6 | 25 | 22 |
| VW | 10782 | 28.4 | 27.0 | +2.9 | 50 | 49 | 28 | 26 |
| VWp1 | 9132 | 30.2 | 28.1 | +3.7 | 51 | 50 | 31 | 29 |
| VWm1 | 11525 | 22.7 | 21.5 | +2.6 | 41 | 40 | 25 | 24 |
| VWp2 | 6289 | 19.4 | 17.3 | +3.8 | 34 | 32 | 29 | 25 |
| VWm2 | 11153 | 13.8 | 13.5 | +1.0 | 27 | 27 | 20 | 19 |
| WVW | 9376 | 16.2 | 15.4 | +2.0 | 29 | 28 | 27 | 24 |
| WVWpm1 | 13128 | 23.0 | 21.7 | +3.0 | 40 | 40 | 28 | 26 |
| LVN | 13078 | 52.0 | 42.2 | +18.9 | 67 | 59 | 49 | 43 |
| FVG1 | 11500 | 33.2 | 30.9 | +4.5 | 60 | 59 | 28 | 27 |
| FVG5 | 11962 | 19.7 | 18.0 | +4.1 | 35 | 34 | 24 | 21 |
| OB | 4406 | 15.8 | 15.1 | +1.1 | 32 | 33 | 20 | 18 |
## STATUS / NEXT
1. Matched-density null (levels allowed in the null, only distance matched) to settle the dense families; then reaction stats on real MFE/MAE per book exits.
2. X23g (UW walls, static per day; 2024-10 on), X23h combined score (confluence counts from a-g).
3. Walk-forward on the book menu: fixed-rule row first (fixed_rules_x23.json), then 2/4/13-week re-pick; requires each book's own bracket per entry (from W-DYNQ recorder), run on server C (niced). Candidates file /mnt/l2/l2vast/_dynexit/x23_candidates.json: not yet written (nothing cleared any clause).
Code: code/th_dynl/x23_first.py, x23_report.py; raw counts /mnt/l2/l2vast/_dynexit/x23/first/stat.json.


## Fixed-rule row (sum of 17 books, $ per 1 lot, windows vs own bracket, win = shallower dd with income >= -10% or higher income with dd not deeper)
See /mnt/l2/l2vast/_dynexit/x23/eval_live2.json (keys ALL|, Asia|, NYAM|, London|, NYPM| + family). Full-sample L6M ALL books: own income 476,592 dd 22,398; X23a hlsw TfS3 126,572 dd 34,933; X23c f5 TfarSgap 384,711 dd 22,249; X23e eset 56,183 loss dd 78,149; X23g uwall 406,345 dd 25,689; X23h ms2 rr1 -22,414 dd 58,368; D23 hlsw base -117,850 dd 120,899. Random-skip null for X23h: 3 draws each, per-window numbers in the json (rs key): the rule is below the random-skip rows in most windows.
Code: code/th_dynl (x23_first.py, x23_pools.py, x23_prof.py, dl_run.py, dl_eval.py, dl_null.py, dl_rank.py); server C live results /mnt/l2/l2vast/_dynexit/x23/live2 (copied to box 1).

## ROUND 3 (05:20Z): confirm or kill the two leads, API, UW forward register
Defaults written before scoring: /mnt/l2/l2vast/_dynexit/fixed_rules_x23_round3.json. Sample = 444 Test 5 Asia qualifier cells (random 240 of 904 (row,module) groups, counted ONLY on held weeks = non-hindsight), run on server C (results /mnt/l2/l2vast/_dynexit/x23/t5asia and r3_t5asia.json on C), plus the 3 Asia live books. Pessimistic label = weekly pts minus 1.5 pts per trade (approximation; own bracket turns negative under it for the qualifiers, so compare rule to own and to nulls, not to zero).
1. ASIA EQUAL-HIGH/LOW STOP: KILLED as an equal-pool effect. T5 Asia plain: rule vs own L6M income +51% dd -6%, L3M income +106% dd -3%, wins 5/6 windows; the 5 shifted-level null stops give L6M income 546k-692k vs rule 689k (own 457k) and win 3.0/6 windows on average (max 4). A tighter stop at a random level helps these wide-bracket cells as much: it is a bracket-shape effect, not liquidity. Pessimistic: rule 4/6 vs null max 4. On the 3 live Asia books the rule beats its nulls (5/6 vs max 3, L3M dd -28%), too few books to stand against 444 cells. The rule changes the stop on 427 of 444 cells; equal pools sit within 60 pts behind the entry in 38% of Asia entries (about 55 per month over 3 books).
2. 20-DAY COMPOSITE POC/VA: KILLED. T5 Asia plain TfS3: L6M income +9% dd -5%, but L3M income -77% (35,603 vs 155,867), 3/6 windows vs null 1.6; pessimistic 1/6. Why L3M fails: the rule fires on only 10-13% of entries (Asia live books: about 15 trades per month over 3 books; NY AM about 44 per month over 7 books), so a quarter holds roughly 45 (Asia) to 130 (NY AM) modified trades; the target-only and stop-only parts change under 2% of cells.
3. PLAN-AGENT FUNCTION: code/th_dynl/pools_api.py (documented in its docstring): pools_for(ts_ns, side, price) -> nearest pool ahead/behind (distance and price, second ahead) per entry for 13 kinds (sw5/15/60, eq, f1, f5, ob, p1/p5/p20, uwall, uwflip, hl), read at the last 1-min bar closed <= ts-2 s; confirmation lag per kind in LAG_TEXT; stop_target_refs() gives the X23 fixed-rule stop/target distances. Findings to respect: pools are reached more often than random in Asia but do nothing at the pool; only swing-60 (Asia) and FVG (NY AM) behind protect; never put a stop just beyond VWAP or the RTH open.
4. X22 JOIN: see candidates file x22_join: the other agents' finalists use different subjects/kernels; X23 legs that survived: none. No joint numbers invented.
5. UW INTRADAY WALLS: forward register only (/mnt/l2/l2vast/_dynexit/x23/FORWARD_REGISTER_UWWALLS.md, script code/th_dynl/dl_fwd_uw.py): 9 days, SPX-point walls 5-13% from spot, no NQ bars after 13 Nov on the box, nothing scored.

## ROUND 4 (06:20Z): fair-value-gap NY AM, exact stop-slippage re-score of the Asia equal-pool stop
Defaults (unchanged, written before): /mnt/l2/l2vast/_dynexit/fixed_rules_x23_round4.json (copy), fixed_rules_x23.json(.amend). Exact rescorer constants from code/th_test11/t11_lib.py (fee 4.84/lot RT vs 1.18 engine = +0.183 pt per 1-lot trade; every Stop exit slip(1 lot) = 0.85 pt worse). The quick-screen kernel stores no exit names, so Stop exits are proxied by LOSING trades (trades - wins): conservative (also charges losing time exits). Samples: held weeks only, random groups of Test 5 cells (non-hindsight), 5 shifted-level nulls (gap edges shifted together for the gap rule).
1. X23c f5 TfarSgap, NY AM, 307 cells: FAIL. Wins 2/6 windows (plain and exact; nulls 0-1). L6M: shallower dd (-7%) and better income than own (own negative) and than the nulls, but L3M income -23% (exact 26.5k vs 46.8k) with dd -16%; 2024 income -22%; 2025 income ~ -99%. The 13-week walk-forward pass of round 2 does not survive as a fixed rule. Not a candidate.
2. Asia equal-high/low stop (3 pts beyond; >= 6; <= own), 437 cells, exact label: wins 4/6 windows (misses 2023, a tiny held sample, and 2025: income -29% dd +1%). L6M income 379k vs own 165k, dd 520k vs 583k; L3M income 121k vs -26k, dd 421k vs 438k; 2024 285k vs 238k; 2026 230k vs -28k. Against the 5 shifted-level stops: L6M nulls 253-329k income and 557-619k dd, L3M nulls 40-83k and 405-424k dd: the rule is above all five in L6M and L3M and in dd; null windows won [3,2,1,1,4] vs rule 4. Plain label 5/6 vs nulls [4,2,4,3,4] (L6M 667k vs 546-622k); 1.5-pt label 4/6 vs [3,4,3,4,3] (does not separate). Round-3's 444-cell kill (rule inside the null range) is reversed in the recent windows once exact slippage is charged, because the equal-pool stop produces fewer losing exits per trade than the random-level stops. Verdict: LEAD (fixed rule), quick screen, not blind to the 3 live Asia books, no 2/4/13-week walk-forward yet; posted to candidates file and as a LEAD NOTE. Next: walk-forward of the pick including this recipe on the Asia mix; exact engine hook (stop = equal-pool level + 3 pts) would be needed for real money numbers.
3. Pools API handed to W-PLAN-AS/NY/LO in MORNING.md (offer of per-book feature table).
4. UW walls register: no new recorder days since 25 Nov (script re-run, nothing appended).

## ROUND 5 (06:55Z): walk-forward of the Asia equal-pool stop, joint with the stuck exit, exact-engine row spec
Default written first: /mnt/l2/l2vast/_dynexit/fixed_rules_x23_round5.json (EQ = stop only; SE = stuck 45 min/0.25R + winners leave 15 min before session end on the own bracket; EQSE = both as one rule; references AS8, EQAS8; nulls = shifted-level stop with the same exit). Sample 437 non-hindsight Test 5 Asia cells (held weeks), exact stress label, 5 nulls; plus the 3 live Asia books. Results r5_t5.json / r5_live.json on server C.
1. WALK-FORWARD EQ stop (rule always on per period, existing programme metric): shallower 29/55 (2 wk), 21/36 (4 wk), 9/13 (13 wk); chained income 599k vs own 337k; chained max DD 586k vs own 583k (equal). PASS at 13 wk only; FAIL at 2 and 4 wk. Same counts for the 5 shifted-level nulls: 23-30/55, 17-23/36, 8-10/13; their income 383-498k, DD 571-619k: the drawdown side is not separated from random-level stops, the income side is (+20% over the best null). The programme's pick switch cannot test a single rule here: it falls back to the own bracket in 97% of cell-periods (per-cell L6M/L3M eligibility), where it shows 'PASS' at 2/4 wk only because it ties on drawdown with +1% income: ignore it. Live 3 Asia books: fixed 5/6 windows (nulls 1-4), always-on WF too few books (shallower 1/56).
2. 2025 HOLE: the tighter stop raises trades by 12% and losing exits by 25% in 2025 (9,557 vs 8,529 trades; 4,878 vs 3,900 losers). The loss sits in Aug 2025 (rule -165k vs own -108k, null mean -133k) and Sep 2025 (-28k vs -2k), a whipsaw stretch where the wide own bracket survived; July 2025 (+83k vs 0) offsets part. Same sign in the nulls, so it is the cost of a tighter stop, not of the equal-pool choice; the equal pool is just worse than average random level in that stretch.
3. JOINT with the stuck exit: KILLED. EQSE wins 0/6 windows (L6M income 81k vs own 165k vs EQ alone 379k; DD 643k vs 583k), below all 5 nulls' DD story and below EQ alone in every window; SE alone 0/6 (L6M -109k); AS8 0/6; EQAS8 0/6. The stuck exit removes the income the equal-pool stop adds (stuck-trade exit cuts winners that were slow). On the 3 live Asia books EQSE 1/6, EQ alone 5/6. The stop leg is orthogonal in mechanism but not additive in P&L.
4. EXACT-ENGINE ROWS (W-DYNH, nothing queued; held in _dynexit/hold/): static pool stop TL3_DX_AS_MF1..MF4_eq_{A,M,N} 504 rows; joint eqj 504 rows; identity 2 rows; 36 MB on box1 for 1,008 rows (13.6 MB for 3 books static = 378 rows). Per-entry stop files /mnt/l2/l2vast/_dynexit/x23/eqstop_AS_MF1..4.parquet (195 KB total; stop tighter than own on 50/41/34/35% of MF1-4 entries). Recommendation: if anything is queued, only the static 378 (3 mapped books) or 504 rows; the joint rows are not worth the disk.
5. UW intraday walls register re-run: still 9 days (last 25 Nov), nothing new.
