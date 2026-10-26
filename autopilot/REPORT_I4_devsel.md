# REPORT I4
**Verdict: NO** (no cell eligible on the 2013-2022 development span: 0 of 36; pair window not read). Runtime 0.0 min, 7-worker pool.

Volume-surge continuation/reversal on 5-minute bars (ES/NQ/YM/RTY): rvol vs same-slot 20-day median and a large bar, time exit 3/6/12 bars. NT8: 5-minute bar strategy. Sleeve protocol (PREREG_AUTOPILOT.md BATCH I): selection on 2013-2022, one cell read on the pair window; basket normalised to 1 ADR-dollar per trade, scaled to the pair's clean weekly sd; fill model 1-minute bar opens (entry and time exit at the open of the stated bar), 1 tick/side + $4.36 per contract RT, 2x = 2 ticks/side. Executable at NinjaTrader Brokerage via Rithmic (CME products); micros for sizing.


|   R |   K | mode   |   H |     n |   sharpe |      net |   ypos | eligible   |
|----:|----:|:-------|----:|------:|---------:|---------:|-------:|:-----------|
|   5 |   2 | follow |  12 |  3995 |   -0.593 |  -43.899 |      3 | False      |
|   5 |   1 | follow |  12 |  6413 |   -0.893 |  -66.676 |      2 | False      |
|   5 |   2 | follow |   6 |  4299 |   -1.031 |  -57.275 |      3 | False      |
|   3 |   2 | follow |  12 |  8773 |   -1.141 | -112.460 |      2 | False      |
|   5 |   2 | fade   |  12 |  3995 |   -1.156 |  -87.592 |      1 | False      |
|   5 |   2 | follow |   3 |  4609 |   -1.382 |  -62.071 |      3 | False      |
|   2 |   2 | follow |  12 | 14283 |   -1.426 | -169.674 |      2 | False      |
|   5 |   2 | fade   |   6 |  4299 |   -1.455 |  -84.512 |      1 | False      |
|   5 |   1 | follow |   6 |  7230 |   -1.603 | -104.297 |      3 | False      |
|   3 |   2 | fade   |  12 |  8773 |   -1.644 | -167.729 |      1 | False      |
|   3 |   2 | follow |   6 |  9731 |   -1.698 | -128.834 |      2 | False      |
|   5 |   1 | fade   |  12 |  6413 |   -1.800 | -141.691 |      0 | False      |
|   5 |   2 | fade   |   3 |  4609 |   -1.868 |  -90.439 |      0 | False      |
|   2 |   2 | follow |   6 | 16244 |   -1.920 | -190.985 |      2 | False      |
|   5 |   1 | fade   |   6 |  7230 |   -1.982 | -131.814 |      1 | False      |

DONE I4
