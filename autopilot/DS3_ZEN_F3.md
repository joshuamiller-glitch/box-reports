# DS3_ZEN_F3 - bracket shapes / management / vol-unit stops / entry mechanics on E1-E5 (D3ZF3)

STATUS: counts block written BEFORE the prereg hash; no cell scored yet at this point of the file.

## 2. Counts block (descriptive, NO P&L; PRE 2024-02-01..2025-06-30 = 75 weeks, PRIMARY entry window 10:00-14:00)

Signals = first hold candle (wick within tol of the line or through it, body close on the trend side) per touch episode; pool = every regime-qualified closed 1-min bar (random-in-regime candidate set).

| cell | hold signals PRE | per week | rest-limit signals (episode starts) | pool bars | FVG at level (<=5pt, touch<=2) | OB at level | fill LIM2 / LIM1 / LIM0 | fill REST | fill STOPENT | stop-entry vs line (pts) | MID fill (of zone signals) | SW target exists (median dist pts) | EQ exists | 4H FVG edge exists |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| E1 | 2543 | 33.9 | 1782 | 86252 | 81% | 45% | 74% / 69% / 65% | 70% | 63% | 14.1 | FVG 47% (2054 sig), OB 27% (1137 sig) | 100% (6.8) | 70% (24.9) | 91% (46.9) |
| E2 | 2334 | 31.1 | 1743 | 86252 | 77% | 41% | 81% / 77% / 73% | 86% | 67% | 12.3 | FVG 50% (1800 sig), OB 27% (961 sig) | 100% (6.4) | 70% (23.7) | 90% (47.4) |
| E3 | 1495 | 19.9 | 909 | 65408 | 82% | 49% | 66% / 62% / 57% | 65% | 66% | 14.2 | FVG 42% (1227 sig), OB 25% (726 sig) | 100% (7.5) | 76% (24.1) | 88% (52.3) |
| E4 | 2350 | 31.3 | 1690 | 86252 | 81% | 42% | 74% / 70% / 66% | 70% | 64% | 14.6 | FVG 47% (1905 sig), OB 26% (991 sig) | 99% (6.5) | 60% (23.8) | 91% (45.8) |
| E5 | 3695 | 49.3 | 3254 | 75075 | 84% | 44% | 73% / 68% / 64% | 67% | 63% | 14.2 | FVG 50% (3098 sig), OB 26% (1631 sig) | 100% (5.0) | 57% (17.1) | 90% (48.7) |

Invalidation-stop reference distances (entry fill at line+1pt, LIM1; entries where the structure exists; pts to the close-basis trigger): n / median / p90

| cell | body close through the level | through the stack (far of EMA200, VWAP) | past 50% of the FVG | past far edge of the OB |
|---|---|---|---|---|
| E1 | 1764 / 1.0 / 1.0 | 1764 / 1.0 / 23.6 | 968 / 3.4 / 9.0 | 593 / 4.3 / 10.9 |
| E2 | 1801 / 1.0 / 1.0 | 1801 / 1.0 / 23.8 | 972 / 3.4 / 9.6 | 596 / 4.2 / 10.2 |
| E3 | 921 / 1.0 / 1.0 | 921 / 4.9 / 28.1 | 527 / 2.9 / 8.1 | 319 / 4.1 / 10.4 |
| E4 | 1636 / 1.0 / 1.0 | 1636 / 8.5 / 43.3 | 887 / 3.7 / 9.4 | 528 / 4.6 / 10.6 |
| E5 | 2514 / 1.0 / 1.0 | 2509 / 35.9 / 99.2 | 1355 / 3.3 / 8.4 | 808 / 4.8 / 10.2 |

M1 context - what a fixed 15-pt stop is in volatility units by year (PRIMARY-window 1-min bars): 

| year | median NQ price | median ATR14 (pts) | 15 pt as % of price | 15 pt in ATR units |
|---|---|---|---|---|
| 2023 | 18037 | 8.8 | 0.083% | 1.71 |
| 2024 | 21467 | 10.5 | 0.070% | 1.43 |
| 2025 | 24152 | 13.2 | 0.062% | 1.14 |
| 2026 | 26514 | 14.3 | 0.057% | 1.05 |

Reading: the hold candle is common (20-49 per week), a limit 0-2 pt before the line fills on 57-81% of them (so a limit is not a rare event), a stop-entry 1 tick beyond the hold-candle extreme sits on average 12-15 pts from the line (the hold candle is a wide bar), the nearest 1-min swing target is on median 5-7.5 pts away (so the model bracket "15-pt stop, swing target" needs a very high win rate), and ZM3-style zones (FVG within 5 pt of the level) exist on ~80% of touches - they are not selective. 15 pt = 1.7 ATR in 2023 but 1.0 ATR in 2026, which is why M1 is a first-order question.
