# REPORT N5

**NO - copper/gold ratio -> ES / ZN: no cell passes the 2013-22 development screen (>= 300 trades and >= 7 of 10 positive years); best 2013-22 Sharpe 0.57 (N5_10_h5_ES), pair window never read; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea N5: 10/20-day HG-GC pct change, 6 cells; clean-only selection.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), all 6 cells (top 10)
| cell          |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:--------------|-----------------:|-------------:|----------:|
| N5_10_h5_ES   |                0 |         0.57 |         0 |
| N5_20_h5_ES   |                0 |        -0.2  |         0 |
| N5_10_h5_ESZN |                0 |        -0.4  |         0 |
| N5_20_h5_ESZN |                0 |        -1.14 |         0 |
| N5_10_h5_ZN   |                0 |        -1.19 |         0 |
| N5_20_h5_ZN   |                0 |        -1.28 |         0 |

Mean 2013-22 Sharpe over cells -0.61; cells with positive Sharpe 1 of 6. The idea is dead on development evidence alone.


DONE N5
