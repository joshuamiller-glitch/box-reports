# REPORT I2
**Verdict: NO** (no cell eligible on the 2013-2022 development span: 0 of 18; pair window not read). Runtime 0.0 min, 7-worker pool.

RTH opening gap (ES/NQ/YM/RTY): fade/follow of the 09:30 ET gap vs prior 15:59 close, entry 09:31, time exit 30/120/360 min (no later than 15:55). NT8: simple session-open strategy. Sleeve protocol (PREREG_AUTOPILOT.md BATCH I): selection on 2013-2022, one cell read on the pair window; basket normalised to 1 ADR-dollar per trade, scaled to the pair's clean weekly sd; fill model 1-minute bar opens (entry and time exit at the open of the stated bar), 1 tick/side + $4.36 per contract RT, 2x = 2 ticks/side. Executable at NinjaTrader Brokerage via Rithmic (CME products); micros for sizing.


|   thr | mode   |   H |    n |   sharpe |      net |   ypos | eligible   |
|------:|:-------|----:|-----:|---------:|---------:|-------:|:-----------|
| 0.500 | fade   | 120 | 1612 |    0.019 |    1.670 |      4 | False      |
| 0.500 | fade   |  30 | 1612 |   -0.035 |   -2.266 |      4 | False      |
| 0.500 | fade   | 360 | 1612 |   -0.123 |  -15.220 |      5 | False      |
| 0.250 | follow | 360 | 4211 |   -0.126 |  -24.029 |      4 | False      |
| 0.500 | follow | 360 | 1612 |   -0.257 |  -31.889 |      4 | False      |
| 0.100 | follow | 360 | 6905 |   -0.376 |  -89.440 |      4 | False      |
| 0.250 | fade   | 120 | 4211 |   -0.390 |  -53.638 |      5 | False      |
| 0.100 | fade   | 360 | 6905 |   -0.444 | -105.699 |      4 | False      |
| 0.250 | follow | 120 | 4211 |   -0.487 |  -66.959 |      4 | False      |
| 0.250 | fade   | 360 | 4211 |   -0.503 |  -96.567 |      2 | False      |
| 0.100 | fade   | 120 | 6905 |   -0.530 |  -86.972 |      3 | False      |
| 0.500 | follow | 120 | 1612 |   -0.537 |  -48.779 |      4 | False      |
| 0.250 | follow |  30 | 4211 |   -0.601 |  -53.865 |      5 | False      |
| 0.100 | follow | 120 | 6905 |   -0.658 | -108.168 |      3 | False      |
| 0.500 | follow |  30 | 1612 |   -0.678 |  -44.843 |      3 | False      |

DONE I2
