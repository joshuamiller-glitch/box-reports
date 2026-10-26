# REPORT I5
**Verdict: NO** (no cell eligible on the 2013-2022 development span: 0 of 54; pair window not read). Runtime 0.0 min, 7-worker pool.

ES-NQ 1-minute lead-lag catch-up: z-scored relative return over m minutes, trade the laggard, time exit 2/5/10 min. NT8: needs both instruments in one strategy (multi-instrument). Sleeve protocol (PREREG_AUTOPILOT.md BATCH I): selection on 2013-2022, one cell read on the pair window; basket normalised to 1 ADR-dollar per trade, scaled to the pair's clean weekly sd; fill model 1-minute bar opens (entry and time exit at the open of the stated bar), 1 tick/side + $4.36 per contract RT, 2x = 2 ticks/side. Executable at NinjaTrader Brokerage via Rithmic (CME products); micros for sizing.


|   m |   thr |   h | T   |     n |   sharpe |      net |   ypos | eligible   |
|----:|------:|----:|:----|------:|---------:|---------:|-------:|:-----------|
|   1 |     4 |   5 | NQ  |  4798 |   -2.210 |  -49.058 |      0 | False      |
|   1 |     4 |  10 | NQ  |  4086 |   -2.229 |  -61.886 |      1 | False      |
|   1 |     4 |  10 | ES  |  4086 |   -2.236 |  -56.067 |      0 | False      |
|   3 |     4 |  10 | NQ  |  4502 |   -2.501 |  -72.271 |      0 | False      |
|   5 |     4 |  10 | NQ  |  4414 |   -2.558 |  -76.289 |      0 | False      |
|   5 |     4 |  10 | ES  |  4414 |   -2.602 |  -69.978 |      0 | False      |
|   1 |     3 |  10 | NQ  |  9310 |   -2.740 | -110.170 |      0 | False      |
|   3 |     4 |  10 | ES  |  4502 |   -2.828 |  -74.152 |      0 | False      |
|   5 |     3 |  10 | NQ  |  8752 |   -2.838 | -108.797 |      0 | False      |
|   3 |     4 |   5 | NQ  |  5336 |   -2.874 |  -68.613 |      0 | False      |
|   3 |     3 |  10 | NQ  |  9351 |   -2.875 | -111.327 |      0 | False      |
|   5 |     4 |   5 | NQ  |  5246 |   -3.093 |  -69.868 |      0 | False      |
|   1 |     4 |   2 | NQ  |  5587 |   -3.398 |  -53.950 |      0 | False      |
|   3 |     4 |   2 | NQ  |  6274 |   -3.449 |  -61.337 |      0 | False      |
|   1 |     3 |   5 | NQ  | 11532 |   -3.634 | -124.270 |      0 | False      |

DONE I5
