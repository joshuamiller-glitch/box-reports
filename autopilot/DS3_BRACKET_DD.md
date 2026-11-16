# DS3_BRACKET_DD - Part B: target by direction of the day (base TL3_EV_JN05W2JL2)
**STATUS (plain, not a PASS, no lead until controls are in): 0 of 40 Part B cells scored in HOLD; 0 pass the HOLD screen (max DD not worse than the reference, HOLD-path 2025-11-17..12-10 DD not worse, mean not more than 5% below); controls and the other windows are queued for those. L3M never ranks.**

Rule definitions. Day direction at the signal second from CLOSED 1-minute bars only (bar ts <= signal second - 60; price = last closed bar close): session open = price vs open of the first bar of the session (asia 18:00, london 02:00, nyam 09:30, nypm 12:00 ET; needs the first bar within 10 minutes); 18:00 ET open = price vs open of the 18:00 bar of the Globex day; session VWAP = price vs sum((h+l+c)/3 x volume)/sum(volume) since the session start; 60-min slope = price vs the close 60 minutes earlier; 3-of-4 vote = +1/-1 when at least 3 of the 4 agree, else no direction. WITH the day = trade side equals the direction; AGAINST = opposite; no direction = bracket unchanged. WITH: target 85 / 120 points, or trail (no target; once +30 points open a trailing exit 30 points behind the favourable extreme, via the engine trail mechanism); AGAINST: target 20 / 30 / 40 points, size x0.5, skip. Stop (60) and every other level stay at the JL2 values, lots at live values (the stop is unchanged, so constant-risk lots are the same cells). Controls per candidate: 3 placebos = the direction label taken 11 / 23 / 37 sessions earlier at the same clock; 3 matched random = random +-1 labels at the same clock (skip cells: random skip at the same share of signals as the real against-day share). W44-removed row for windows containing 2026-W44. $4.84 column beside the raw one. Dollars BASE lots, x1.75 = live.

### HOLD window (2025-11..2026-04), whole-stack, vs JL2; drawdown first; HOLD path = 2025-11-17..12-10
| cell | max DD (ref) | worst week (ref) | HOLD-path DD (ref) | d net/wk (live x1.75; $4.84) | stops/wk | screen |
|---|---|---|---|---|---|---|
| session open: WITH the day -> target 85  | not finished | | | | | |
| session open: WITH the day -> target 120  | not finished | | | | | |
| session open: WITH the day -> trail after +30 by 30  | not finished | | | | | |
| session open: AGAINST the day -> target 20  | not finished | | | | | |
| session open: AGAINST the day -> target 30  | not finished | | | | | |
| session open: AGAINST the day -> target 40  | not finished | | | | | |
| session open: AGAINST the day -> size x0.5  | not finished | | | | | |
| session open: AGAINST the day -> skip  | not finished | | | | | |
| 18:00 ET open: WITH the day -> target 85  | not finished | | | | | |
| 18:00 ET open: WITH the day -> target 120  | not finished | | | | | |
| 18:00 ET open: WITH the day -> trail after +30 by 30  | not finished | | | | | |
| 18:00 ET open: AGAINST the day -> target 20  | not finished | | | | | |
| 18:00 ET open: AGAINST the day -> target 30  | not finished | | | | | |
| 18:00 ET open: AGAINST the day -> target 40  | not finished | | | | | |
| 18:00 ET open: AGAINST the day -> size x0.5  | not finished | | | | | |
| 18:00 ET open: AGAINST the day -> skip  | not finished | | | | | |
| session VWAP: WITH the day -> target 85  | not finished | | | | | |
| session VWAP: WITH the day -> target 120  | not finished | | | | | |
| session VWAP: WITH the day -> trail after +30 by 30  | not finished | | | | | |
| session VWAP: AGAINST the day -> target 20  | not finished | | | | | |
| session VWAP: AGAINST the day -> target 30  | not finished | | | | | |
| session VWAP: AGAINST the day -> target 40  | not finished | | | | | |
| session VWAP: AGAINST the day -> size x0.5  | not finished | | | | | |
| session VWAP: AGAINST the day -> skip  | not finished | | | | | |
| 60-min slope: WITH the day -> target 85  | not finished | | | | | |
| 60-min slope: WITH the day -> target 120  | not finished | | | | | |
| 60-min slope: WITH the day -> trail after +30 by 30  | not finished | | | | | |
| 60-min slope: AGAINST the day -> target 20  | not finished | | | | | |
| 60-min slope: AGAINST the day -> target 30  | not finished | | | | | |
| 60-min slope: AGAINST the day -> target 40  | not finished | | | | | |
| 60-min slope: AGAINST the day -> size x0.5  | not finished | | | | | |
| 60-min slope: AGAINST the day -> skip  | not finished | | | | | |
| 3-of-4 vote: WITH the day -> target 85  | not finished | | | | | |
| 3-of-4 vote: WITH the day -> target 120  | not finished | | | | | |
| 3-of-4 vote: WITH the day -> trail after +30 by 30  | not finished | | | | | |
| 3-of-4 vote: AGAINST the day -> target 20  | not finished | | | | | |
| 3-of-4 vote: AGAINST the day -> target 30  | not finished | | | | | |
| 3-of-4 vote: AGAINST the day -> target 40  | not finished | | | | | |
| 3-of-4 vote: AGAINST the day -> size x0.5  | not finished | | | | | |
| 3-of-4 vote: AGAINST the day -> skip  | not finished | | | | | |

(Part D page by W-BD2: autopilot/DS3_BRACKET_DD_D.md, not yet present)
