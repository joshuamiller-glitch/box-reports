# REPORT Z10

**NO - vol-surge trend (ATR5/ATR20 >= 1.3/1.6): no cell passes the 2013-22 development screen (>= 300 trades and >= 7 of 10 positive years); best 2013-22 Sharpe -0.05 (Z10_1.3_20_h5_ALL26), pair window never read; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea Z10: trade the 5/20-day trend direction in vol surges, hold 3/5 = 16 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), all 16 cells (top 10)
| cell                |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:--------------------|-----------------:|-------------:|----------:|
| Z10_1.3_20_h5_ALL26 |             2446 |        -0.05 |         4 |
| Z10_1.3_20_h3_ALL26 |             3275 |        -0.05 |         4 |
| Z10_1.3_20_h3_SCR   |             2164 |        -0.11 |         6 |
| Z10_1.3_20_h5_SCR   |             1625 |        -0.21 |         6 |
| Z10_1.6_20_h3_ALL26 |              599 |        -0.21 |         2 |
| Z10_1.6_5_h3_SCR    |              416 |        -0.24 |         3 |
| Z10_1.6_5_h3_ALL26  |              597 |        -0.25 |         5 |
| Z10_1.6_5_h5_SCR    |              310 |        -0.28 |         4 |
| Z10_1.6_5_h5_ALL26  |              446 |        -0.29 |         4 |
| Z10_1.6_20_h5_ALL26 |              447 |        -0.34 |         3 |

Mean 2013-22 Sharpe over cells -0.28; cells with positive Sharpe 0 of 16. The idea is dead on development evidence alone.


DONE Z10
