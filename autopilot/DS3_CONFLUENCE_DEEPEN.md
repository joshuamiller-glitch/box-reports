# DS3_CONFLUENCE_DEEPEN - squeeze / RSI / MACD state at entry and expanding what held up (W-CF3; order DIRECTIVE_CONFLUENCE_DEEPEN_20261116.md)

VERDICT (data ends 2026-10-30; FIRST PASS; nothing has landed yet): no engine result exists for this order yet. The L3 arrival-imbalance sets (Part 2 item 1) are queued first, then the P7 Asia / K7 Asia gated sets with older windows, then the Part 1 states once W-CF4 sends the passing list. Engine rules for all sets: JN05W2, every universe signal gated (taken and replacement), all layers ON, base lots with x1.75 live beside, constant stack risk where size moves, every skip against an engine random skip with the same keep share, nonsense bar per cell.

## Queue and set names (tag CF)
| item | sets | status |
|--|--|--|
| Part 2.1 L3 arrival imbalance LOW, SIZE FIRST (x1.5 lead / x0.5 not-lead) and SKIP, per book x session, with random placebos | TL3_CF_L3C_* (22 sets: ALL5, U7 Asia, P7 Asia, P7 London, P7 NY AM, O7 NY AM; 60 s and 30 s windows) | queued, first in the order |
| Part 2.1 windows 15/30/60/120 s and percentiles 10/20/30 of the previous 20 days, as SKIP of the opposite state, HALF, x1.5, x2 (U7 P7 O7 M7 A7; K7, H7 excluded: effect about zero there) | TL3_CF_L3D_W{30,60}_P{10,20,30}, W15_P20, W120_P20 x {SKIP, SKIP_RND, HALF, X15, X2} (40 sets) | queued second |
| Part 2.2 P7 Asia gated set with size: older windows (2023 negative: does that kill it under the tolerant gate), neighbour swaps, L3 item and best Part 1 state as 6th and 7th, ladder x1 / x1.5 / x2 by items agreeing | TL3_CF_G_P7A_V0all5_K / S15 over HOLD, GAP, PRE, X' plus the engine random gate TL3_CF_RS_P7A; neighbour swaps and the 6th/7th item sets are not built yet | older windows queued |
| Part 2.3 K7 Asia "at least 4" same treatment | TL3_CF_G_K7A_V0ge4_K, V0ge3_K | queued behind 2.2 |
| Part 1 states at entry (squeeze, RSI, CCI, stochastic, MACD, agreement count) with SKIP / HALF / x1.5 / WAIT N=3,6,12 | asked W-CF4 for the columns and the passing list; WAIT needs an entry-timing hook (not built) | waiting for W-CF4 |
| Part 2.4 London range-used-up skip combined with Part 1 states (with W-LR) | not started | |
| Part 2.5 nearer brackets in Asia (A7 / U7 40x40) selected by a state (with W-D10) | not started | |
| Part 2.6 every other book x session and S7, O7, X1-X8 for any item that passes | not started | |
| Part 3 ladder from passed items only vs the nonsense ladder vs a random ladder with the same lot distribution, capped at the book's live cap | not started (the table-level staircase from the library found no climb out of sample: autopilot/DS3_CONFLUENCE.md top section) | |

## D7 computability (one line per item)
| item | can D7 compute it live today? |
|--|--|
| L3 arrival imbalance low (own-side order adds minus opposite-side adds over 15-120 s, below the previous-20-day percentile) | NEEDS THE L3 (MBO) FEED. The mbp-10 (L2) proxy does not reproduce it (W-CF2: lift +$12, years -116/+86/+10/+9). |
| squeeze, RSI, CCI, stochastic, MACD states on 1/5/15/60-minute NQ bars | YES, from D7's own bars (no new feed). |
| USER_SET_V0 items (CCI 5/15-min, session levels, prior-day profile, squeeze, EMA stack) | YES, from D7's own bars and levels. |
| London range used up (W-LR) | YES with D7's own series plus the walk-forward forecast file. |
| ZN moving with the trade, gamma flip distance | NEEDS A FEED (ZN price; options data). |

Reports below are added as results land; the order of sections will be: recent windows first, then older, then failures.
