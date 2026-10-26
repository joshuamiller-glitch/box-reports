# REPORT U3 - gap-fade H1 autopsy

**NO observable known at the signal-day close separates H1's failing trades (clean-selected rule uplift in H1 stays -0.49..-0.27); the finding is structural: the 'gap fade' (Z3/W6/V3/V4/V10) is a WEEKEND-GAP fade - 534 of 598 2013-22 trades, 101 of 102 clean, 34 of 37 H1 and 101 of 101 H2 trades are Monday entries (signal on the Sunday-evening stub bar of the UTC-day series). H1 has only 37 trades in 28 weeks and two weeks make the loss: 2025-W42 (-$35.7k, 9 markets gapped together after the October-2025 tariff weekend) and 2025-W52 (-$33.6k, GC/HG/SI holiday-week breakouts). Not FOUND, not a lead improvement.**

Pre-registered in PREREG_AUTOPILOT.md ("STRUCTURAL BATCH U1-U3", 2026-10-16T15:03Z). Base book W6_0.25_h1_SCR (standalone weekly Sharpe clean 0.78, H1 -2.08, H2 1.64; trades clean/H1/H2 102/37/101; additive uplift @20% clean/H1/H2/all 0.11/-0.49/0.34/0.09). Fill model as REPORT_Y*: entry at the next UTC-day open (the Sunday stub bar's close = Monday 00:00 UTC bar open), 1 tick/side + commission, ATR20 sizing.

## Worst 5 H1 weeks of the base book
|   week |       pnl |   n | syms                        |   mean_gap |   mean_breadth |   share_with_trend |   atrp |
|-------:|----------:|----:|:----------------------------|-----------:|---------------:|-------------------:|-------:|
| 202542 | -35720.8  |   9 | 6A,6J,CL,ES,HG,HO,NQ,RTY,YM |       0.8  |              9 |               0.78 |   0.39 |
| 202552 | -33632.7  |   3 | GC,HG,SI                    |       0.54 |              3 |               0    |   0.71 |
| 202606 | -14572.3  |   6 | 6J,CL,GC,HG,HO,NG           |       0.68 |              6 |               1    |   0.86 |
| 202602 |  -5989.49 |   2 | GC,NG                       |       0.46 |              2 |               0    |   0.79 |
| 202541 |  -4759.77 |   4 | 6B,6J,CL,RB                 |       0.68 |              4 |               0.5  |   0.18 |

H1 loss by bucket (sum $, trades): class MET -43.8k (11), EN -19.3k (13), EQ -13.9k (7), FX -1.9k (6); weekday Monday -45.3k (34), Friday -33.6k (3); gap up -71.7k (21) vs gap down -7.2k (16); with-trend -35.8k (21) vs against -43.1k (16). No stable single bucket: the damage is two clustered weeks (breadth 9 and metals Christmas week), i.e. a common-shock weekend where all markets gap the same way and keep going.

## Candidate observables (23 rules, 7 observables), selection on CLEAN only, then H1/H2 read once
All 23 rules, clean/H1/H2 standalone Sharpe:
| rule              |   clean_keep |   sh_clean |   sh_H1 |   sh_H2 |
|:------------------|-------------:|-----------:|--------:|--------:|
| O1 gap>=0.25      |         1    |       0.78 |   -2.08 |    1.64 |
| O1 gap>=0.5       |         0.5  |       1.04 |   -2.16 |    1.51 |
| O1 gap>=1         |         0.11 |       0.85 |   -2.33 |    1.02 |
| O2 atrp<=0.33     |         0.25 |      -0.21 |   -1.05 |    1.16 |
| O2 atrp>=0.33     |         0.75 |       0.87 |   -2.01 |    1.54 |
| O2 atrp<=0.5      |         0.32 |      -0.05 |   -1.42 |    0.91 |
| O2 atrp>=0.5      |         0.68 |       0.87 |   -1.89 |    1.54 |
| O2 atrp<=0.67     |         0.43 |       0.09 |   -1.61 |    0.11 |
| O2 atrp>=0.67     |         0.57 |       0.89 |   -2.18 |    1.96 |
| O3 breadth<=2     |         0.44 |      -0.93 |    1.04 |    0.29 |
| O3 breadth>2      |         0.56 |       1.03 |   -2.36 |    1.62 |
| O3 breadth<=3     |         0.47 |      -0.51 |   -1.15 |    0.73 |
| O3 breadth>3      |         0.53 |       0.95 |   -1.71 |    1.56 |
| O3 breadth<=4     |         0.55 |      -0.19 |   -1.07 |   -0.49 |
| O3 breadth>4      |         0.45 |       0.87 |   -1.8  |    1.8  |
| O4 up gaps only   |         0.45 |       0.17 |   -2.08 |    1.22 |
| O4 down gaps only |         0.55 |       0.85 |   -0.52 |    1.97 |
| O5 with trend     |         0.49 |      -0.13 |   -1.68 |    1.33 |
| O5 against trend  |         0.51 |       0.93 |   -1.59 |    1.37 |
| O6 drop weekday 0 |         0.01 |       0.7  |   -1.36 |  nan    |
| O6 drop weekday 1 |         0.99 |       0.75 |   -2.08 |    1.64 |
| O6 drop weekday 2 |         1    |       0.78 |   -2.08 |    1.64 |
| O6 drop weekday 3 |         1    |       0.78 |   -2.08 |    1.64 |
| O6 drop weekday 4 |         1    |       0.78 |   -1.51 |    1.64 |
| O7 drop class EQ  |         0.79 |       0.59 |   -2.1  |    1.71 |
| O7 drop class MET |         0.89 |       0.74 |   -1.35 |    1.5  |
| O7 drop class EN  |         0.46 |       0.97 |   -1.72 |    1.97 |
| O7 drop class FX  |         0.85 |       0.66 |   -2.23 |    1.43 |

Clean-selected rule per observable (>= 60% of clean trades kept, best clean Sharpe), with additive uplift at 20% (scale from clean vol):
| rule              |   clean_keep |   sh_clean |   sh_H1 |   sh_H2 |   up_clean |   up_H1 |   up_H2 |   up_all |
|:------------------|-------------:|-----------:|--------:|--------:|-----------:|--------:|--------:|---------:|
| O2 atrp>=0.33     |         0.75 |       0.87 |   -2.01 |    1.54 |       0.13 |   -0.46 |    0.31 |     0.1  |
| O1 gap>=0.25      |         1    |       0.78 |   -2.08 |    1.64 |       0.11 |   -0.49 |    0.34 |     0.09 |
| O6 drop weekday 2 |         1    |       0.78 |   -2.08 |    1.64 |       0.11 |   -0.49 |    0.34 |     0.09 |
| O7 drop class MET |         0.89 |       0.74 |   -1.35 |    1.5  |       0.11 |   -0.27 |    0.32 |     0.12 |

Reading: the clean-selected filters change nothing in H1 (standalone H1 Sharpe -1.35..-2.01 vs base -2.08); breadth filters, which are the natural separator of the Oct-2025 week, were not preferred on clean (breadth is rarely high in clean). Selection over 23 rules on 102 clean trades has no power; a rule fitted on H1 would be overfit by construction and is NOT tested (rules are not allowed to touch H1). Monday-only (weekend) book: Sharpe 2013-22 0.78, clean 0.75, H1 -1.51, H2 1.64, pair window 0.85; non-Monday trades: -0.70 in 2013-22 (the Friday/stub cases lose): the weekend restriction is the one structural cut, and it is ex-ante (calendar), but it leaves the H1 failure intact.

## Executability
The weekend-gap fade is an NT8 Sunday-evening strategy: after the first hour of the Sunday session (18:00-19:00 ET) compare the open with Friday's close (gap >= 0.25 ATR20) and a confirming first-hour candle, enter the opposite way at 19:00 ET, exit at the Monday 17:00 ET close (hold 1 'UTC day' in the study = about 24h from 20:00 ET Sunday to 20:00 ET Monday; a real session-aligned backtest on the 1-min data is required before any use). One of the standard risks: Sunday-open liquidity.

DONE U3
