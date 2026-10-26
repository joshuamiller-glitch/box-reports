# REPORT Z6

**NO - expansion-then-compression path-resolved breakout (inside day after wide day): no cell passes the 2013-22 development screen (>= 300 trades and >= 7 of 10 positive years); best 2013-22 Sharpe -0.14 (Z6_wrid1.6_k2_M6), pair window never read; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea Z6 (moved to the path-resolved 30-min engine by pre-registration amendment): inside label day after a day with range >= 1.2/1.6 ATR20, OCO stop entry resolved on 30-min bars, stop 2/3 ATR, NQ ES RTY GC CL ZN = 4 cells. Z7 (volume dry-up) was dropped before running (needs daily-bar stop entry).

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), all 4 cells (top 10)
| cell             |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:-----------------|-----------------:|-------------:|----------:|
| Z6_wrid1.6_k2_M6 |              320 |        -0.14 |         4 |
| Z6_wrid1.6_k3_M6 |              320 |        -0.16 |         4 |
| Z6_wrid1.2_k2_M6 |              811 |        -0.18 |         4 |
| Z6_wrid1.2_k3_M6 |              811 |        -0.19 |         4 |

Mean 2013-22 Sharpe over cells -0.17; cells with positive Sharpe 0 of 4. The idea is dead on development evidence alone.


DONE Z6
