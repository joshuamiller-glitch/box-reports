# DS3_UWBOOKS_B1 - Unusual Whales standalone books, families 1, 2, 6, 7 (W-UB1). Updated 2026-11-13 14:31Z by code/th_uwbooks/uwb_page.py (chained every 3 h). Research, shadow, NO PASS claim.

## 0. Status
Jobs done 20 of 602 (job = family x instrument x ticker x series, all its event kinds, both directions, 5 sessions, 1,470 grid cells). Group rows stored: 2014. Null draws (shifted-time, whole event table moved by random weeks): 0.
Instruments run: ES, NQ. RTY/YM wait for IWM/DIA UW pulls (W-UB3). X' has NO UW data (history starts 2024-10-01): X' is not scored. PRE is clipped to the UW start (PREUW). Windows from 2026-11-12.

## 1. Where the signal sits (gated = mean L6M>0 and L3M>0 and HOLD>0 and n_L6M>=20)
| family | instrument | matched | groups scored | groups with any gated cell | best gated L6M Calmar | max recents $/wk over cells ((L6M+HOLD)/2) |
|--|--|--|--|--|--|--|
| F1 | NQ | False | 372 | 166 | 161.7 | 4166 |
| F1 | NQ | True | 60 | 23 | 101.6 | 1807 |
| F2 | NQ | True | 32 | 16 | 17689.4 | 5250 |
| F6 | ES | False | 16 | 8 | 34.8 | 1051 |
| F6 | ES | True | 8 | 7 | 18.1 | 1351 |
| F6 | NQ | False | 8 | 7 | 22.6 | 1386 |
| F7 | ES | True | 12 | 12 | 33.7 | 1888 |
| F7 | NQ | False | 24 | 22 | 22.0 | 1456 |
| F7 | NQ | True | 24 | 24 | 87.1 | 7922 |

## 2. Best book per session (gated; ranked by L6M Calmar = mean*52/maxDD). Window values are $/wk at the cell lots (R=$1,200 per trade at the stop, cap 10 lots), fees and measured slippage in.
| session | dir | family | instrument (matched) | trigger | cell | n L6M | L1M | L3M | L6M | HOLD | PREUW | maxDD L6M | worst wk L6M | full stops/wk L6M | pos wk L6M | WF OOS $/wk | placebo shuffle p | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| asia | short | F2 | NQ (matched) | NDX vol|magnet retest_up | Ep10_S60_Ta2_X120 | 23 | 180 | 470 | 362 | 164 | -190 | 51 | -51 | 0.12 | 0.92 | pending | pending | thin n=23; null: see section 1 |
| london | long | F1 | NQ (cross) | SPX c_oi zx_dn | Emkt_S90_T30_X30 | 24 | n/a | 5 | 282 | 133 | -241 | 361 | -361 | 0.00 | 0.82 | pending | pending | thin n=24; null: see section 1 |
| pre | short | F1 | NQ (cross) | SPX g_oi d5_dn | Emkt_S90_Ta1_X60 | 22 | 133 | 147 | 401 | 360 | 49 | 176 | -176 | 0.00 | 0.86 | pending | pending | thin n=22; null: see section 1 |
| nyam | long | F2 | NQ (matched) | NDX vol|magnet touch_dn | Eb1_Sa2_T30_X15 | 20 | 0 | 287 | 322 | 225 | -4 | 0 | 0 | 0.04 | 1.00 | pending | pending | L1M negative; thin n=20; null: see section 1 |
| nypm | short | F1 | NQ (matched) | NDX c_dir d1_dn | Ep10_S60_T30_XSE | 32 | 441 | 391 | 431 | 371 | -95 | 220 | -220 | 0.12 | 0.83 | pending | pending | thin n=32; null: see section 1 |

Spec decoding: cell Ex_Sy_Tz_Xw = entry mode x, stop y, target z, time exit w (NQ-point lists scaled by the instrument ATR ratio, a1/a2 = 1x/2x ATR14 of 5-min bars; XSE = session end, flat). Trigger names: see UWBOOKS_B1_PREREG.md.


## 4. Data honesty (lags; no-look-ahead proof, sample day per family)
LAG (spot_1m QQQ 2026-10-14): row time - start_time: min 0 s, median 58 s, max 59 s (snapshot taken inside the minute); avail used = start+60 s (>= snapshot time by construction) + EXTRA_LAG 60 s
F1 panel vs raw g_dir on 2026-10-14: 494 common minutes, max abs diff 0 (0 = identical)
F1 first d1_dn event 13:30:00 ET: decision ts 1791999000 = last used row avail 1791998940 (+60 s lag); value 5.541e+08 vs 15 min earlier 5.58e+08; entry fill path starts at ts+1 s (harness.simulate market = mid at t0+1)
  check: raw row avail <= decision ts: True ; no raw row with avail > decision ts - 60 is used
F2 gex_levels_oi SPX file 2026-10-14 computed at 2026-10-14T20:15:00.000000Z (end of day); used only for sessions starting 18:00 ET 2026-10-14 onward (label day next business day); same-day sessions of 2026-10-14 use the PRIOR file
F6 10:00 ET reading for 2026-10-14: row avail 10:00:00 ET (<= 10:00:00), value -3.161e+08; event ts = 10:00 + 60 s lag
F7 prior-close reading of 2026-10-14: row avail 16:00:00 ET (start 15:59); event 18:05 ET same date (Friday -> Sunday 18:05) + lag; London 02:00 ET next business day; pre-market 06:35 ET uses rows avail <= 06:35

## 5. Plain reading
(written after the first complete read)