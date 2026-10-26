# REPORT Y1

**NO - close-streak fade/follow (N=3,4): no cell passes the 2013-22 development screen (>= 300 trades and >= 7 of 10 positive years); best 2013-22 Sharpe -0.02 (Y1_4_follow_h3_SCR), pair window never read; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea Y1: N consecutive same-direction closes, fade or follow, hold 1/3, ALL26 or SCR = 16 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), all 16 cells (top 10)
| cell                 |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:---------------------|-----------------:|-------------:|----------:|
| Y1_4_follow_h3_SCR   |             3243 |        -0.02 |         6 |
| Y1_3_follow_h3_SCR   |             6613 |        -0.19 |         5 |
| Y1_4_fade_h3_ALL26   |             5018 |        -0.25 |         3 |
| Y1_3_fade_h3_SCR     |             6613 |        -0.33 |         4 |
| Y1_4_fade_h3_SCR     |             3243 |        -0.33 |         4 |
| Y1_4_fade_h1_SCR     |             5563 |        -0.38 |         5 |
| Y1_3_follow_h3_ALL26 |            10326 |        -0.45 |         5 |
| Y1_4_follow_h1_SCR   |             5563 |        -0.47 |         3 |
| Y1_4_follow_h3_ALL26 |             5018 |        -0.49 |         2 |
| Y1_3_fade_h1_SCR     |            11384 |        -0.55 |         3 |

Mean 2013-22 Sharpe over cells -0.55; cells with positive Sharpe 0 of 16. The idea is dead on development evidence alone.


DONE Y1
