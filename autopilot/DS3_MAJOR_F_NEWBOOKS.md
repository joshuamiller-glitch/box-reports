# DS3_MAJOR_F_NEWBOOKS - new London / New York books (MAJOR-CHANGES PROGRAMME part F, W-MF). FIRST PASS. Refreshed 2026-11-17 14:10Z (unattended loop, every 30 min)

> VALIDATION (W-MF, FIRST PASS): trials counted = 1324 standalone cells (wave 1: 109 configs x 4 exits, PREREG_MF.md, ledger MF1; wave 2: 222 configs x 4 exits incl. limit variants, PREREG_MF2.md, ledger MF2); correction = per-family and per-session best-of selection on 2023-04..2025-10 only, then HOLD 2025-11..2026-04 and L6M 2026-05..10 untouched; White RC over the selection cells (1,000 block bootstraps) + deflated Sharpe on the untouched year with N = cells of the group; PBO not computed (selection is a single frozen pick, rolling 12m/3m version shown); engine controls: 30 date-shifted stack controls NOT FINISHED (staged by the loop after the real months land); shifted-label standalone controls (+-11/23/37 days) shown. Data end 2026-10-30 (ES bars end 2026-10-16).

VERDICT (data ends 2026-10-30; FIRST PASS): standalone screen of 1324 London/PRE/NY cells (waves 1+2): 1 family picks pass (a), 0 pass (a)+(b); engine stack identity 202610 PASS (691 vs 691 trades, net 37159.82 vs 37159.82), 202504 PASS (637 vs 637 trades, net 41239.76 vs 41239.76); no CONFIRMED book.

## Summary (five lines)
1. TRIED: 1324 pre-registered cells (wave 1: 109 configs; wave 2: new families W1-W12, loosened near-miss grids and 0/4-point resting-limit variants with a 0.5 pt haircut) x 4 exit cells in ~60 families for London, PRE, NY AM and NY PM (open drive/fail, Asia range, 08:30 pullback, VWAP reversion, ORB break/fade, gap, drive pullback, 10:00 reversal, trend/chop day, lunch break, power hour, ES-led, mean-reversion sweeps/RSI2/failed breakouts) on a standalone 1-min simulator; selection on 2023-04..2025-10, the last 12 months untouched.
2. HOLDS: 1 of 59 family picks (both waves) are positive on the untouched year with >= 150 trades and > 60% positive months (M3_FAILED_BREAK_LON|lb=60,rj=5 E2_60_60 UNT 0.057 R n 150 (b fail: corr -0.06, worst-20-weeks $-1696)); 0 also pass the diversification test (b). Standalone survivors are LEADS only until the engine stack test and 30 shifted-date controls land. Highest untouched-year R among picks: P3_POWER_HOUR|k=0.4 E4_vol, 0.194 R on 122 trades (selection 0.063 R, below the 150-trade bar).
3. DOES NOT HOLD: most families have a selection-window mean near 0.03-0.06 R that does not survive the untouched year; no family has a White RC p below 0.05 over its selection cells; ORB, drive pullback, 10:00 reversal, RSI2 and lunch/PM VWAP reversion picks are negative on the untouched year. No cell reaches the 0.2+ R O7 has on its 506 trades. Wave 2 adds no survivor: no new family or limit variant (fill rates 0.6-0.99) passes (a), and loosening the near-miss grids does not reproduce P3 or ES-led NY AM (3e).
4. NEEDS IN DS7: nothing yet. Engine injection sets TL3_MF_* (JL3 + one injected book, tag MF1) are queued: identity 202610 PASS (691 vs 691 trades, net 37159.82 vs 37159.82), 202504 PASS (637 vs 637 trades, net 41239.76 vs 41239.76); no standalone result is used for a build until identity passes and the stack rows below fill in.
5. NEXT: engine identity and stack rows (alone; with part A vector and part B picks once their finals exist) as months land, then 30 shifted-date engine controls for the best candidate; shelf London/NY re-score is in 2b (standalone; engine-exact marginals are W-MB's).

## 1. Method and simulator fidelity
Standalone simulator: 1-min NQ bars (the engine's bars_nq_ext.npz, back-adjusted; no volume in that file so VWAP = anchored equal-weight typical price), market entry at the next bar open +1 tick, stop exit 1 tick adverse (gap -> open), target needs 1 tick through, stop wins inside a bar, flat at session end, $4.84 RT per lot, R = net points / stop points. Equal dollar risk: lots = round(1200/(stop x 20)). Daily series use $1,200 x R per trade (base lots; engine dollars scale x1.75 at live lots).

FIDELITY vs the engine on a book that exists (replay of the engine's own raw-chassis O7 and M7 NY AM entries since 2026-04, same entry price, stop/target on 1-min bars):
```
O7 76 exit-kind agree 0.855 | engine kinds {1: 51, 2: 25} | sim kinds {1: 45, 2: 30, 3: 1}
  px diff on agree stop/target: mean 1.812 max 25.0
M7 364 exit-kind agree 0.912 | engine kinds {2: 187, 1: 174, 3: 3} | sim kinds {1: 180, 2: 174, 3: 10}
  px diff on agree stop/target: mean 1.284 max 20.25
```
Reading: exit KIND (stop vs target) agrees on 91% of M7 and 85% of O7 trades (1-min bars cannot resolve intrabar order); engine stop fills slip a median -0.5 / mean +0.15..0.3 pt vs the stop level, the simulator charges 1 tick, target fills identical (0.0). The simulator is a SCREEN: every number is re-run on the exact engine for survivors (section 5). The engine also applies the live SCR gate, stack caps and day rules to an injected book, which the standalone numbers do not have (UW injection experience: harness +1,073 vs engine +159 $/wk).

## 2. Shelf (step 1)
W-MB's SHELF_INVENTORY.md is present (89536 bytes). London / NY rows quoted below (first 60; the full inventory and the marginal tests are W-MB's):

3. Session ledger store (London/NY cells): l2vast/ds3/out/ss2/trades_all.parquet (15.5 M rows, 10 lots) + tiers.parquet (361 alive cells: London 40, NY AM 154, NY PM 9, PRE 16, Asia 190). Fade events: /mnt/l2/l2vast/fade_lv/events_enriched.parquet, ds3_fade/events.parquet (96,951), ds3_disb/events.parquet, ds3_disc/events.parquet, q13/events.parquet. TICK books F1..F8: /mnt/l2/l2vast/_tickb/inj/. UW books: /mnt/l2/l2vast/_uwbooks/inject/. FLOW E3: /mnt/l2/l2vast/_flow/inject/.
| VB2NYPM_T1 | nypm 12:00-14:59 ET | MR | STRICT in audited T60 cell (L6M +17/wk at 1 lot in FADE_ROWS_LV; tiny~ | /mnt/l2/l2vast/fade_lv/events_enriched.parquet (141,979 events, 2023-~ | HARNESS-TRADES (events+spec; convertible to inject: stop=ext5+0.5ATR,~ | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| VB2NYAM_T3 | nyam 09:30-11:59 | MR | LEAD (TOLERANT) | /mnt/l2/l2vast/fade_lv/events_enriched.parquet (141,979 events, 2023-~ | HARNESS-TRADES (events+spec; convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| OR15NYAM_T2 | nyam 09:45-11:59 | MR | REGIME: 2026-only earner, 2023-25 net -21.6k | /mnt/l2/l2vast/fade_lv/events_enriched.parquet (141,979 events, 2023-~ | HARNESS-TRADES (events+spec; convertible) | UNKNOWN (REGIME; 2023-25 negative -> tolerant gate on older windows f~ |
| ORBF_B2 | nyam 10:00-14:00 | MR | CANDIDATE-RECENT: L6M +1,799/wk, HOLD +1,957/wk at 2 lots; PRE -1,403~ | /mnt/l2/l2vast/ds3_zones3_new/Z2_bg/ (check) ; <home>/... | HARNESS-TRADES | UNKNOWN: harness basis; fails tolerant gate on PRE/X'; selection N=350 |
| NQ_RSI2C_s20 | all | MR | PASS in struct48; PRE 241->212 and X' 121->78 at 6.7 lots no-lock; lo~ | l2vast/ds3_a12/ ; l2vast/ds3/out/ (struct48 per-contract series) | HARNESS-TRADES | VOID for engine claims: tied to composite/lock routing of the OLD sta~ |
| ES_RSI2_t10 | all | MR | CANDIDATE; placebo rank 0.99 PRE+X' 0.875; X' cut 121->66 at 8.6 lots~ | l2vast/ds3_a12/ ; l2vast/ds3/out/ (struct48 per-contract series) | HARNESS-TRADES | VOID for engine claims: tied to composite/lock routing of the OLD sta~ |
| NQ_IBS_4.2lots | all | MR | PRE 241->155, X' 121->79 no lock; with lock PRE 16% X' 35% cut at 20R~ | l2vast/ds3_a12/ ; l2vast/ds3/out/ (struct48 per-contract series) | HARNESS-TRADES | VOID for engine claims: tied to composite/lock routing of the OLD sta~ |
| FR:Sunday-open/sunday 18:00-20:00/entry 30 min after the open /tape-f~ | sunday 18:00-20:00 | MR/other | L1M +2742 L3M +817 L6M +793 HOLD +424 MID +699 PRE +190 X' +5 $/wk at~ | /mnt/l2/l2vast/ds3_disc/events.parquet | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_LV/NYPM/VB2/T1/b0.5 0.5R T60, 1 lot (n 523) | nypm | MR | L1M +212 L3M +128 L6M +384 HOLD +238 MID +17 PRE +38 X' +20 $/wk at s~ | (event file per source page; not located) | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_LV2/NYPM/VB2/T1/b0.5 0.5R T60 | nypm | MR | L1M +212 L3M +143 L6M +391 HOLD +240 MID +8 PRE +40 X' +11 $/wk at st~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:fade (Z1)/nyam/swing 5m fractal/failed break X=15 pt reclaim<=3 mi~ | nyam | MR | L1M +242 L3M +818 L6M +964 HOLD +566 MID +1467 PRE +67 X' -136 $/wk a~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_MZ/nyam/swing 5m fractal/failed break X=15 pt, reclaim<=3 m/s~ | nyam | MR | L1M +242 L3M +818 L6M +964 HOLD +566 MID +1467 PRE +67 X' -136 $/wk a~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:fade (Z1)/nyam/swing 5m fractal/failed break X=20 pt reclaim<=3 mi~ | nyam | MR | L1M +34 L3M +194 L6M +899 HOLD +416 MID +1075 PRE +12 X' -203 $/wk at~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_MZ/nyam/swing 5m fractal/failed break X=20 pt, reclaim<=3 m/s~ | nyam | MR | L1M +34 L3M +194 L6M +899 HOLD +416 MID +1075 PRE +12 X' -203 $/wk at~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_MZ_ZONE/london/zone kijun1h/failed break X=10 pt, reclaim<=30~ | london | MR | L1M +410 L3M +321 L6M +371 HOLD +376 MID +110 PRE +109 X' -0 $/wk at ~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_MZ_ZONE/nypm/zone CRT4h/failed break X=15 pt, reclaim<=10 /st~ | nypm | MR | L1M +4 L3M +243 L6M +378 HOLD +312 MID +460 PRE +83 X' -18 $/wk at st~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_MZ_ZONE/nypm/zone CRT4h/failed break X=5 pt, reclaim<=10 m/st~ | nypm | MR | L1M +650 L3M +813 L6M +334 HOLD +284 MID +212 PRE +292 X' +21 $/wk at~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_MZ_ZONE/nypm/zone CRT4h/failed break X=10 pt, reclaim<=10 /st~ | nypm | MR | L1M +4 L3M +412 L6M +188 HOLD +276 MID +672 PRE +45 X' +37 $/wk at st~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_MZ_ZONE/asia/zone kijun1h/failed break X=15 pt, reclaim<=10 /~ | asia | MR | L1M +452 L3M +52 L6M +336 HOLD +373 MID +790 PRE +4 X' +0 $/wk at sta~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_MZ_ZONE/asia/zone PDmid/failed break X=20 pt, reclaim<=30 /st~ | asia | MR | L1M +491 L3M +175 L6M +570 HOLD +379 MID +305 PRE +46 X' +0 $/wk at s~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:fade (Z1)/asia/prior RTH H/L/failed break X=20 pt reclaim<=30 m/st~ | asia | MR | L1M +135 L3M +237 L6M +391 HOLD +284 MID +472 PRE +80 X' +3 $/wk at s~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_MZ/asia/PD H/L/failed break X=20 pt, reclaim<=30 /stop ext+0.~ | asia | MR | L1M +135 L3M +237 L6M +391 HOLD +284 MID +472 PRE +80 X' +3 $/wk at s~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_MZ_ZONE/asia/zone PDmid/failed break X=15 pt, reclaim<=10 /st~ | asia | MR | L1M +212 L3M +69 L6M +308 HOLD +260 MID +435 PRE +27 X' +0 $/wk at st~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:tape-fade prevday/london/prevday/T1a_delta_div/tgt=vwap stop=1.00A~ | london | MR | L1M +1646 L3M +1015 L6M +1225 HOLD +685 MID +428 PRE +62 X' -343 $/wk~ | (event file per source page; not located) | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:DIS_B trend/pre/REL/P_REL_cont_m1.0/tgt=r1 stop=1.00ATR T30m | pre | MR/other | L1M +367 L3M +911 L6M +410 HOLD +707 MID +850 PRE +298 X' +517 $/wk a~ | /mnt/l2/l2vast/ds3_disb/events.parquet | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_VW RNG 15.0/nyam/RNG 15.0/T2/buf1.0/vwap/T120/re1 | nyam | MR | L1M +770 L3M +1466 L6M +879 HOLD +562 MID +404 PRE -327 X' -280 $/wk ~ | (event file per source page; not located) | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:DIS_B trend/pre/REL/P_REL_cont_m0.5/tgt=r1 stop=1.00ATR T60m | pre | MR/other | L1M +2463 L3M +1454 L6M +644 HOLD +223 MID +398 PRE +315 X' +564 $/wk~ | /mnt/l2/l2vast/ds3_disb/events.parquet | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:Sunday-open/sunday 18:00-20:00/entry 30 min after the open /tape-f~ | sunday 18:00-20:00 | MR/other | L1M +833 L3M +332 L6M +855 HOLD +352 MID +795 PRE +123 X' -89 $/wk at~ | /mnt/l2/l2vast/ds3_disc/events.parquet | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_MZ_ZONE/nypm/zone kijun1h/failed break X=5 pt, reclaim<=10 m/~ | nypm | MR | L1M +103 L3M +109 L6M +55 HOLD +47 MID +453 PRE +7 X' +193 $/wk at st~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_MZ_ZONE/nypm/zone kijun1h/failed break X=10 pt, reclaim<=3 m/~ | nypm | MR | L1M +894 L3M +403 L6M +215 HOLD +51 MID +8 PRE +45 X' +42 $/wk at sta~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_MZ_ZONE/nypm/zone ALLZ/failed break X=5 pt, reclaim<=3 mi/sto~ | nypm | MR | L1M +1403 L3M +967 L6M +35 HOLD -114 MID -155 PRE +67 X' +240 $/wk at~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:DIS_B fade/nyam/IMB/N_IMB_rev_th0.1/tgt=vwap stop=0.25ATR T120m | nyam | MR | L1M -1353 L3M +278 L6M +1131 HOLD +1591 MID +611 PRE +259 X' -312 $/w~ | /mnt/l2/l2vast/ds3_disb/events.parquet | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:DIS_B fade/nyam/REL/N_REL_rev_m0.5/tgt=mid stop=1.00ATR T120m | nyam | MR | L1M +73 L3M +322 L6M +1275 HOLD +1165 MID +305 PRE +216 X' -550 $/wk ~ | /mnt/l2/l2vast/ds3_disb/events.parquet | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:Q13/NYAM/gap B1 tercile 1 both/B1d5/b0.25 1R T30, 1 lot (n 275) | nyam | MR/other | L1M +474 L3M +957 L6M +329 HOLD +417 MID +300 PRE +52 X' -3 $/wk at s~ | /mnt/l2/l2vast/q13/events.parquet | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:DISI/london/OPEX_WEEK/FADE/SH2 | london | MR/other | L1M +704 L3M +439 L6M +347 HOLD +269 MID +564 PRE +37 X' -59 $/wk at ~ | (event file per source page; not located) | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:DIS_B fade/nyam/PMV/N_PMV_rev_a0.5/tgt=mid stop=1.00ATR T60m | nyam | MR | L1M +163 L3M +122 L6M +486 HOLD +458 MID +160 PRE +457 X' -619 $/wk a~ | /mnt/l2/l2vast/ds3_disb/events.parquet | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:DIS_B fade/nyam/PMV/N_PMV_rev_a1.0/tgt=mid stop=1.00ATR T60m | nyam | MR | L1M -348 L3M +6 L6M +431 HOLD +430 MID +160 PRE +457 X' -579 $/wk at ~ | /mnt/l2/l2vast/ds3_disb/events.parquet | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:DISI/london/OPEX_WEEK/DRIFT_L/SH2 | london | MR/other | L1M +292 L3M +596 L6M +170 HOLD +132 MID +587 PRE +188 X' -41 $/wk at~ | (event file per source page; not located) | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_MZ_ZONE/nyam/zone OTE705/failed break X=10 pt, reclaim<=3 m/s~ | nyam | MR | L1M +174 L3M +259 L6M +147 HOLD +94 MID +185 PRE +41 X' -112 $/wk at ~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:DISI/nyam/POST_HOL/FADE/SH2 | nyam | MR/other | L1M +0 L3M +183 L6M +82 HOLD +90 MID +107 PRE +35 X' -23 $/wk at stat~ | (event file per source page; not located) | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:DISI/london/MS1/CONT/SH2 | london | MR/other | L1M -257 L3M +83 L6M +129 HOLD +76 MID +173 PRE +60 X' +125 $/wk at s~ | (event file per source page; not located) | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:DISI/london/AUCT_LONG/FADE/SH1 | london | MR/other | L1M -257 L3M +153 L6M +73 HOLD +304 MID +734 PRE +45 X' +172 $/wk at ~ | (event file per source page; not located) | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:Q13/NYAM/gap B1 tercile 1 both/B1d1/b1 2R T30, 1 lot (n 292) | nyam | MR/other | L1M -230 L3M +808 L6M +957 HOLD +497 MID +68 PRE +61 X' -151 $/wk at ~ | /mnt/l2/l2vast/q13/events.parquet | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:DISI/nyam/PCE/FADE/SH1 | nyam | MR/other | L1M +244 L3M +90 L6M +129 HOLD +52 MID +142 PRE +14 X' -97 $/wk at st~ | (event file per source page; not located) | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:DISI/nyam/RETAIL/FADE/SH2 | nyam | MR/other | L1M +479 L3M +274 L6M +178 HOLD +34 MID +85 PRE +12 X' -130 $/wk at s~ | (event file per source page; not located) | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:DIS_B fade/pre/PO/P_PO_fade/tgt=r1 stop=1.00ATR T120m | pre | MR | L1M +1034 L3M +116 L6M +99 HOLD +25 MID +130 PRE +64 X' -178 $/wk at ~ | /mnt/l2/l2vast/ds3_disb/events.parquet | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:Q13/NYAM/gap B1 tercile 1 up/B1d5/b0.5 FILL T30, 1 lot (n 161) | nyam | MR/other | L1M +687 L3M +806 L6M +409 HOLD +249 MID +22 PRE +2 X' -23 $/wk at st~ | /mnt/l2/l2vast/q13/events.parquet | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:DISI/nyam/ISM/CONT/SH1 | nyam | MR/other | L1M +230 L3M +74 L6M +7 HOLD +188 MID +205 PRE +253 X' -2 $/wk at sta~ | (event file per source page; not located) | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:DISI/nyam/PPI/CONT/SH2 | nyam | MR/other | L1M -250 L3M +263 L6M +299 HOLD +152 MID -9 PRE +53 X' -25 $/wk at st~ | (event file per source page; not located) | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_LV2/NYAM/VB2/T3/b0.5 1R T120 | nyam | MR | L1M +10 L3M +631 L6M +402 HOLD +358 MID -13 PRE +15 X' -126 $/wk at s~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_LV/NYAM/VB2/T3/b0.5 1R T120, 1 lot (n 893) | nyam | MR | L1M +10 L3M +631 L6M +402 HOLD +356 MID -20 PRE +15 X' -107 $/wk at s~ | (event file per source page; not located) | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_MZ_ZONE/london/zone KCup4h/failed break X=5 pt, reclaim<=30 m~ | london | MR | L1M +824 L3M +260 L6M +57 HOLD -30 MID +147 PRE +37 X' -27 $/wk at st~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_MZ v2a/nyam/swing 5m fractal (v2a: Wilde/failed break X=20 pt~ | nyam | MR | L1M -690 L3M +377 L6M +602 HOLD -79 MID +570 PRE +218 X' +25 $/wk at ~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:DISI/nyam/MS1/FADE/SH1 | nyam | MR/other | L1M -248 L3M +113 L6M +26 HOLD -58 MID -103 PRE +63 X' -82 $/wk at st~ | (event file per source page; not located) | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:DISI/nyam/PCE/DRIFT_L/SH1 | nyam | MR/other | L1M +244 L3M +104 L6M +216 HOLD +39 MID -104 PRE +24 X' +182 $/wk at ~ | (event file per source page; not located) | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:DISI/london/OPEX_WEEK/DRIFT_S/SH1 | london | MR/other | L1M +1045 L3M +327 L6M +111 HOLD -117 MID +129 PRE +139 X' +268 $/wk ~ | (event file per source page; not located) | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:FADE_MZ/nyam/ON H/L/failed break X=20 pt, reclaim<=10 /stop ext+0.~ | nyam | MR | L1M -273 L3M +870 L6M +780 HOLD +297 MID -126 PRE +183 X' -130 $/wk a~ | /mnt/l2/l2vast/ds3_fade/events.parquet (96,951 events) ; fade_lv/even~ | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:DISI/london/RETAIL/FADE/SH2 | london | MR/other | L1M +481 L3M +266 L6M +170 HOLD +79 MID -128 PRE +44 X' -47 $/wk at s~ | (event file per source page; not located) | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |
| FR:DISI/nyam/EARLY_CLOSE/DRIFT_S/SH2 | nyam | MR/other | L1M +0 L3M +107 L6M +128 HOLD -40 MID -133 PRE +150 X' -72 $/wk at st~ | (event file per source page; not located) | HARNESS-TRADES (event list; stop/target in spec; inject-convertible) | UNKNOWN: harness basis, truncation/look-ahead audited, placebos were ~ |

| shelf family (page) | last verdict | base | still valid? |
|---|---|---|---|
| T-OPEN opening drive DR5m_pb1 (DS3_OPEN_FINAL) | only family with PASS/CANDIDATE labels (one idea), all 35 labels FAIL the program-level best-of-N; forward-register only | D3SL stack, harness M/T | no: old stack, harness fills; my N1/N3/N4 are the JL3-era standalone re-tests |
| OR breaks / gap fade / IB / PB levels (DS3_OPEN_B2_*) | 0 PASS / 0 CANDIDATE in ~8,000 cells | harness | superseded by N1/N2/N3 below |
| trend days (DS3_TREND_DAYS) | 3 tolerant-gate leads on drawdown cut, no PASS | old stack | partly: day-type filters, not books; N5 below tests it as a book |
| ORB Asia (DS3_ORB_ASIA_D7) | FAILS re-scored on PRE+X' selection | D6/D7 | Asia only, not for this order |
| close / PM (DS3_CLOSE_*, DS3_NYPM_END_SKIP) | top-15 by stack-add Sharpe; end skip is a filter | D3SL | P1-P4 below re-test PM books |
| fade / washout / RSI2 / dip (DS3_FADE*, DS3_SESSION2_B_washout, DS3_ORB_RSI2_COMPLETE) | not PASS on L6M in the pages read | harness | M2/M3 below re-test |
| chop days (DS3_CHOP_*) | chop label/forecast, actions are filters | JN05W2 | N5C below tests chop-day MR as a book |
| pullback (DS3_PULLBACK_FINAL) | provisional, leaderboard | D3PB direct replay | N3 below |

## 3. Discovery: per family, best cell chosen on 2023-04..2025-10 (frozen), then HOLD and L6M untouched

### 3.1 Wave 1 (market entries)

| family | cfg | exit | fill rate | N cells | SEL n | SEL R | SELa R | SELb R | HOLD n | HOLD R | L6M n | L6M R | L3M R | UNT n | UNT R | UNT t | UNT months+ | RC p | DSR | roll n | roll R | shift ctl mean | shift ctl max |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1_OPEN_DRIVE | L1_OPEN_DRIVE|W=60,mode=fail | E2_60_60 | 1.000 | 24 | 444.000 | 0.054 | -0.035 | 0.184 | 86.000 | -0.014 | 94.000 | -0.005 | 0.129 | 180.000 | -0.009 | -0.131 | 0.500 | 0.873 | 0.175 | 526.000 | -0.003 | -0.038 | 0.107 |
| L2_ASIA_RANGE | L2_ASIA_RANGE|b=10,mode=break | E1_40_40 | 1.000 | 16 | 324.000 | 0.048 | 0.061 | 0.027 | 61.000 | -0.132 | 64.000 | 0.054 | -0.152 | 125.000 | -0.037 | -0.415 | 0.333 | 0.771 | 0.074 | 363.000 | -0.025 | -0.091 | 0.053 |
| L3_PRENY_DRIFT | L3_PRENY_DRIFT|k=0.1,mode=fade | E4_vol | 1.000 | 16 | 405.000 | 0.002 | -0.074 | 0.118 | 82.000 | -0.012 | 87.000 | -0.233 | -0.347 | 169.000 | -0.126 | -1.770 | 0.167 | 1.000 | 0.014 | 281.000 | -0.056 | 0.055 | 0.133 |
| L5_VWAP_REV_QUIET | L5_VWAP_REV_QUIET|z=2.5 | E2_60_60 | 1.000 | 12 | 296.000 | 0.018 | -0.021 | 0.093 | 55.000 | -0.013 | 23.000 | 0.055 | -0.436 | 78.000 | 0.007 | 0.066 | 0.455 | 0.809 | 0.301 | 312.000 | 0.057 | 0.029 | 0.226 |
| L6_ES_LED_LON | L6_ES_LED_LON|L=30,bp=5,win=LON | E3_40_90 | 1.000 | 16 | 388.000 | 0.050 | 0.045 | 0.058 | 63.000 | -0.188 | 82.000 | -0.155 | -0.026 | 145.000 | -0.169 | -1.537 | 0.417 | 0.501 | 0.008 | 399.000 | 0.001 | -0.022 | 0.029 |
| L6_ES_LED_NYAM | L6_ES_LED_NYAM|L=30,bp=3,win=NYAM | E3_40_90 | 1.000 | 16 | 657.000 | 0.039 | 0.072 | -0.012 | 123.000 | 0.148 | 120.000 | 0.039 | -0.090 | 243.000 | 0.094 | 0.970 | 0.583 | 0.604 | 0.584 | 643.000 | 0.039 | -0.052 | 0.085 |
| M1_SWEEP_REJECT_NYAM | M1_SWEEP_REJECT_NYAM|lvl=pd | E2_60_60 | 1.000 | 8 | 320.000 | 0.027 | 0.017 | 0.046 | 61.000 | -0.072 | 62.000 | -0.071 | -0.043 | 123.000 | -0.072 | -0.798 | 0.333 | 0.772 | 0.051 | 351.000 | 0.077 | 0.035 | 0.164 |
| M1_SWEEP_REJECT_NYPM | M1_SWEEP_REJECT_NYPM|lvl=on | E3_40_90 | 1.000 | 8 | 317.000 | 0.035 | 0.004 | 0.094 | 53.000 | -0.215 | 51.000 | 0.066 | 0.211 | 104.000 | -0.077 | -0.542 | 0.417 | 0.706 | 0.214 | 264.000 | -0.154 | -0.076 | 0.034 |
| M2_RSI2_LON | M2_RSI2_LON|tf=1,th=10 | E2_60_60 | 1.000 | 16 | 660.000 | 0.011 | -0.032 | 0.079 | 126.000 | -0.014 | 131.000 | -0.184 | -0.149 | 257.000 | -0.101 | -1.676 | 0.250 | 0.891 | 0.010 | 668.000 | -0.029 | -0.039 | 0.104 |
| M2_RSI2_NYAM | M2_RSI2_NYAM|tf=1,th=10 | E4_vol | 1.000 | 16 | 659.000 | -0.004 | 0.036 | -0.067 | 126.000 | -0.001 | 131.000 | -0.040 | -0.086 | 257.000 | -0.021 | -0.336 | 0.417 | 0.968 | 0.169 | 630.000 | -0.092 | 0.041 | 0.116 |
| M2_RSI2_NYPM | M2_RSI2_NYPM|tf=5,th=5 | E3_40_90 | 1.000 | 16 | 614.000 | -0.018 | -0.036 | 0.009 | 113.000 | 0.170 | 119.000 | -0.236 | -0.188 | 232.000 | -0.038 | -0.416 | 0.417 | 0.987 | 0.127 | 625.000 | -0.070 | -0.064 | 0.109 |
| M3_FAILED_BREAK_LON | M3_FAILED_BREAK_LON|lb=60,rj=5 | E2_60_60 | 1.000 | 16 | 357.000 | 0.064 | -0.049 | 0.224 | 72.000 | 0.038 | 78.000 | 0.076 | 0.193 | 150.000 | 0.057 | 0.738 | 0.667 | 0.401 | 0.409 | 400.000 | -0.001 | -0.032 | 0.158 |
| M3_FAILED_BREAK_NYAM | M3_FAILED_BREAK_NYAM|lb=30,rj=10 | E2_60_60 | 1.000 | 16 | 434.000 | 0.035 | 0.107 | -0.056 | 86.000 | 0.001 | 90.000 | 0.036 | 0.155 | 176.000 | 0.019 | 0.276 | 0.417 | 0.604 | 0.352 | 389.000 | -0.030 | -0.047 | 0.007 |
| M3_FAILED_BREAK_NYPM | M3_FAILED_BREAK_NYPM|lb=30,rj=5 | E2_60_60 | 1.000 | 16 | 386.000 | 0.025 | 0.021 | 0.030 | 73.000 | 0.125 | 74.000 | -0.015 | 0.228 | 147.000 | 0.054 | 0.688 | 0.583 | 0.746 | 0.574 | 427.000 | -0.083 | 0.027 | 0.106 |
| N1_ORB | N1_ORB|OR=30,ctx=with,mode=break | E3_40_90 | 1.000 | 72 | 255.000 | 0.151 | 0.129 | 0.180 | 53.000 | -0.250 | 51.000 | -0.285 | -0.211 | 104.000 | -0.267 | -2.079 | 0.250 | 0.472 | 0.001 | 249.000 | 0.050 | -0.064 | 0.153 |
| N2_GAP | N2_GAP|k=0.3,mode=go | E3_40_90 | 1.000 | 24 | 302.000 | 0.053 | 0.037 | 0.077 | 60.000 | -0.144 | 83.000 | 0.165 | 0.102 | 143.000 | 0.035 | 0.275 | 0.667 | 0.742 | 0.205 | 394.000 | 0.000 | -0.006 | 0.118 |
| N3_DRIVE_PULLBACK | N3_DRIVE_PULLBACK|d=0.2,lvl=vwap | E2_60_60 | 1.000 | 16 | 196.000 | 0.157 | 0.085 | 0.240 | 38.000 | 0.131 | 53.000 | -0.197 | -0.272 | 91.000 | -0.060 | -0.579 | 0.417 | 0.097 | 0.031 | 223.000 | -0.024 | -0.008 | 0.096 |
| N4_1000_REVERSAL | N4_1000_REVERSAL|k=0.3,mode=cont | E3_40_90 | 1.000 | 24 | 183.000 | 0.244 | 0.196 | 0.308 | 46.000 | 0.127 | 41.000 | -0.298 | -0.392 | 87.000 | -0.073 | -0.465 | 0.417 | 0.088 | 0.001 | 261.000 | 0.158 | -0.032 | 0.313 |
| P1_LUNCH_RANGE | P1_LUNCH_RANGE|st=(11, 30),mode=fade | E4_vol | 1.000 | 16 | 363.000 | 0.014 | 0.060 | -0.058 | 69.000 | 0.082 | 71.000 | -0.077 | -0.004 | 140.000 | 0.001 | 0.014 | 0.667 | 0.982 | 0.284 | 392.000 | 0.030 | -0.018 | 0.137 |
| P2_VWAP_REV_PM | P2_VWAP_REV_PM|z=2.0 | E4_vol | 1.000 | 12 | 306.000 | -0.025 | -0.024 | -0.028 | 38.000 | -0.064 | 39.000 | -0.119 | 0.150 | 77.000 | -0.092 | -0.815 | 0.417 | 0.936 | 0.013 | 306.000 | -0.043 | -0.091 | 0.079 |
| P3_POWER_HOUR | P3_POWER_HOUR|k=0.4 | E4_vol | 1.000 | 8 | 328.000 | 0.063 | 0.102 | 0.006 | 65.000 | 0.186 | 57.000 | 0.204 | 0.092 | 122.000 | 0.194 | 2.265 | 0.667 | 0.322 | 0.951 | 332.000 | 0.085 | 0.039 | 0.232 |
| P4_LATE_EXT_FADE | P4_LATE_EXT_FADE|k=3 | E2_60_60 | 1.000 | 8 | 318.000 | 0.012 | -0.006 | 0.044 | 52.000 | -0.083 | 50.000 | 0.063 | 0.178 | 102.000 | -0.011 | -0.119 | 0.417 | 0.788 | 0.192 | 303.000 | 0.029 | -0.094 | -0.007 |

### 3.2 Wave 2 (new families, loosened near-miss grids, resting-limit variants _LIM; prereg PREREG_MF2.md)

| family | cfg | exit | fill rate | N cells | SEL n | SEL R | SELa R | SELb R | HOLD n | HOLD R | L6M n | L6M R | L3M R | UNT n | UNT R | UNT t | UNT months+ | RC p | DSR | roll n | roll R | shift ctl mean | shift ctl max |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1_OPEN_DRIVE_LIM | L1_OPEN_DRIVE_LIM|W=60,mode=fail,lim=4 | E3_40_90 | 0.747 | 24 | 309.000 | 0.044 | -0.105 | 0.245 | 74.000 | 0.120 | 83.000 | -0.086 | 0.039 | 157.000 | 0.011 | 0.096 | 0.417 | 0.694 | 0.205 | 359.000 | 0.020 | -0.096 | 0.004 |
| L2_ASIA_RANGE_LIM | L2_ASIA_RANGE_LIM|b=0,mode=fade,lim=4 | E3_40_90 | 0.687 | 16 | 188.000 | -0.025 | -0.050 | 0.005 | 39.000 | -0.026 | 41.000 | -0.098 | 0.007 | 80.000 | -0.063 | -0.387 | 0.417 | 0.876 | 0.136 | 212.000 | -0.046 | 0.073 | 0.133 |
| L5_VWAP_REV_QUIET_LIM | L5_VWAP_REV_QUIET_LIM|z=1.5,lim=4 | E2_60_60 | 0.611 | 24 | 261.000 | 0.048 | 0.048 | 0.048 | 60.000 | 0.035 | 37.000 | -0.286 | -0.570 | 97.000 | -0.088 | -0.927 | 0.417 | 0.752 | 0.034 | 209.000 | 0.012 | -0.066 | 0.064 |
| M1_SWEEP_REJECT_NYAM_LIM | M1_SWEEP_REJECT_NYAM_LIM|lvl=pd,lim=4 | E2_60_60 | 0.887 | 16 | 283.000 | 0.020 | 0.014 | 0.033 | 54.000 | -0.108 | 56.000 | -0.185 | -0.173 | 110.000 | -0.147 | -1.557 | 0.250 | 0.883 | 0.003 | 313.000 | -0.019 | 0.010 | 0.161 |
| M1_SWEEP_REJECT_NYPM_LIM | M1_SWEEP_REJECT_NYPM_LIM|lvl=on,lim=0 | E3_40_90 | 0.983 | 16 | 312.000 | 0.020 | 0.015 | 0.028 | 51.000 | -0.248 | 51.000 | 0.066 | 0.212 | 102.000 | -0.091 | -0.639 | 0.417 | 0.886 | 0.163 | 259.000 | -0.139 | -0.100 | -0.002 |
| M2_RSI2_LON_LIM | M2_RSI2_LON_LIM|tf=1,th=5,lim=4 | E3_40_90 | 0.727 | 32 | 462.000 | 0.022 | -0.036 | 0.102 | 101.000 | 0.016 | 104.000 | -0.218 | -0.088 | 205.000 | -0.103 | -1.049 | 0.333 | 0.913 | 0.034 | 544.000 | -0.064 | 0.062 | 0.229 |
| M2_RSI2_NYAM_LIM | M2_RSI2_NYAM_LIM|tf=1,th=10,lim=4 | E4_vol | 0.882 | 32 | 568.000 | -0.025 | -0.014 | -0.041 | 114.000 | 0.001 | 126.000 | -0.049 | -0.057 | 240.000 | -0.025 | -0.393 | 0.583 | 0.998 | 0.135 | 590.000 | -0.156 | 0.043 | 0.099 |
| M2_RSI2_NYPM_LIM | M2_RSI2_NYPM_LIM|tf=5,th=5,lim=4 | E3_40_90 | 0.836 | 32 | 508.000 | -0.017 | -0.027 | -0.001 | 94.000 | 0.125 | 105.000 | -0.239 | -0.141 | 199.000 | -0.067 | -0.687 | 0.583 | 0.992 | 0.054 | 556.000 | -0.076 | -0.080 | 0.120 |
| M3_FAILED_BREAK_LON_LIM | M3_FAILED_BREAK_LON_LIM|lb=60,rj=5,lim=4 | E3_40_90 | 0.751 | 32 | 250.000 | 0.081 | -0.112 | 0.325 | 64.000 | 0.028 | 67.000 | 0.067 | 0.207 | 131.000 | 0.048 | 0.380 | 0.583 | 0.469 | 0.210 | 356.000 | 0.057 | -0.042 | 0.112 |
| M3_FAILED_BREAK_NYAM_LIM | M3_FAILED_BREAK_NYAM_LIM|lb=30,rj=10,lim=4 | E2_60_60 | 0.866 | 32 | 360.000 | 0.040 | 0.109 | -0.037 | 80.000 | -0.004 | 88.000 | 0.048 | 0.150 | 168.000 | 0.023 | 0.325 | 0.500 | 0.686 | 0.305 | 371.000 | -0.032 | -0.046 | 0.070 |
| M3_FAILED_BREAK_NYPM_LIM | M3_FAILED_BREAK_NYPM_LIM|lb=30,rj=5,lim=0 | E2_60_60 | 0.987 | 32 | 380.000 | 0.008 | 0.007 | 0.011 | 72.000 | 0.140 | 74.000 | -0.016 | 0.227 | 146.000 | 0.061 | 0.769 | 0.583 | 0.911 | 0.396 | 422.000 | -0.055 | 0.009 | 0.080 |
| N1_ORB_LIM | N1_ORB_LIM|OR=5,ctx=with,mode=fade,lim=0 | E3_40_90 | 0.985 | 72 | 192.000 | 0.018 | 0.029 | -0.001 | 39.000 | -0.183 | 32.000 | -0.198 | 0.240 | 71.000 | -0.190 | -1.145 | 0.333 | 1.000 | 0.020 | 254.000 | -0.234 | -0.073 | 0.089 |
| P2_VWAP_REV_PM_LIM | P2_VWAP_REV_PM_LIM|z=2.0,lim=4 | E4_vol | 0.836 | 24 | 249.000 | 0.000 | -0.018 | 0.028 | 36.000 | -0.063 | 35.000 | -0.073 | 0.168 | 71.000 | -0.068 | -0.576 | 0.364 | 0.917 | 0.010 | 239.000 | -0.028 | -0.055 | 0.141 |
| P4_LATE_EXT_FADE_LIM | P4_LATE_EXT_FADE_LIM|k=3,lim=4 | E2_60_60 | 0.860 | 16 | 268.000 | 0.020 | 0.014 | 0.030 | 45.000 | -0.108 | 48.000 | 0.080 | 0.260 | 93.000 | -0.011 | -0.107 | 0.417 | 0.827 | 0.144 | 266.000 | 0.032 | -0.077 | 0.108 |
| W11_SESSION_EXTREME_RSI14_LON | W11_SESSION_EXTREME_RSI14_LON|r=80 | E3_40_90 | 1.000 | 8 | 151.000 | 0.162 | 0.117 | 0.217 | 32.000 | 0.105 | 24.000 | -0.248 | -0.189 | 56.000 | -0.046 | -0.255 | 0.333 | 0.030 | 0.227 | 240.000 | 0.041 | 0.159 | 0.336 |
| W11_SESSION_EXTREME_RSI14_LON_LIM | W11_SESSION_EXTREME_RSI14_LON_LIM|r=75,lim=4 | E3_40_90 | 0.733 | 16 | 237.000 | 0.098 | 0.159 | 0.028 | 57.000 | -0.012 | 49.000 | 0.217 | 0.291 | 106.000 | 0.094 | 0.684 | 0.667 | 0.102 | 0.536 | 304.000 | 0.046 | 0.027 | 0.204 |
| W11_SESSION_EXTREME_RSI14_NYAM | W11_SESSION_EXTREME_RSI14_NYAM|r=75 | E2_60_60 | 1.000 | 8 | 221.000 | -0.026 | -0.066 | 0.045 | 40.000 | -0.028 | 39.000 | 0.229 | -0.006 | 79.000 | 0.099 | 0.963 | 0.583 | 0.843 | 0.666 | 218.000 | 0.098 | -0.027 | 0.240 |
| W11_SESSION_EXTREME_RSI14_NYAM_LIM | W11_SESSION_EXTREME_RSI14_NYAM_LIM|r=75,lim=0 | E2_60_60 | 1.000 | 16 | 221.000 | -0.031 | -0.072 | 0.043 | 40.000 | -0.028 | 39.000 | 0.176 | -0.007 | 79.000 | 0.073 | 0.706 | 0.583 | 0.895 | 0.504 | 204.000 | 0.053 | -0.042 | 0.206 |
| W11_SESSION_EXTREME_RSI14_NYPM | W11_SESSION_EXTREME_RSI14_NYPM|r=75 | E2_60_60 | 1.000 | 8 | 184.000 | 0.010 | -0.118 | 0.244 | 22.000 | -0.169 | 26.000 | -0.094 | -0.312 | 48.000 | -0.128 | -0.909 | 0.333 | 0.665 | 0.092 | 130.000 | -0.033 | -0.094 | 0.065 |
| W11_SESSION_EXTREME_RSI14_NYPM_LIM | W11_SESSION_EXTREME_RSI14_NYPM_LIM|r=75,lim=4 | E3_40_90 | 0.841 | 16 | 150.000 | 0.053 | -0.015 | 0.168 | 20.000 | -0.186 | 25.000 | 0.007 | -0.217 | 45.000 | -0.079 | -0.374 | 0.500 | 0.568 | 0.173 | 121.000 | -0.019 | -0.042 | 0.218 |
| W12_RSI2_3MIN_LON | W12_RSI2_3MIN_LON|tf=3,th=5 | E2_60_60 | 1.000 | 8 | 660.000 | 0.005 | -0.013 | 0.033 | 126.000 | -0.004 | 131.000 | 0.017 | 0.009 | 257.000 | 0.007 | 0.112 | 0.583 | 0.813 | 0.250 | 669.000 | -0.008 | -0.014 | 0.105 |
| W12_RSI2_3MIN_LON_LIM | W12_RSI2_3MIN_LON_LIM|tf=3,th=10,lim=4 | E2_60_60 | 0.716 | 16 | 447.000 | 0.026 | 0.023 | 0.029 | 95.000 | -0.169 | 115.000 | -0.131 | -0.172 | 210.000 | -0.148 | -2.264 | 0.250 | 0.760 | 0.000 | 522.000 | -0.021 | -0.008 | 0.075 |
| W12_RSI2_3MIN_NYAM | W12_RSI2_3MIN_NYAM|tf=3,th=10 | E4_vol | 1.000 | 8 | 659.000 | -0.021 | -0.026 | -0.012 | 126.000 | -0.019 | 130.000 | -0.081 | -0.090 | 256.000 | -0.050 | -0.809 | 0.417 | 0.964 | 0.048 | 653.000 | -0.090 | -0.010 | 0.061 |
| W12_RSI2_3MIN_NYAM_LIM | W12_RSI2_3MIN_NYAM_LIM|tf=3,th=5,lim=4 | E1_40_40 | 0.883 | 16 | 550.000 | -0.032 | -0.046 | -0.010 | 111.000 | -0.155 | 118.000 | -0.045 | 0.091 | 229.000 | -0.099 | -1.507 | 0.500 | 0.990 | 0.007 | 597.000 | -0.097 | -0.048 | 0.030 |
| W12_RSI2_3MIN_NYPM | W12_RSI2_3MIN_NYPM|tf=3,th=5 | E2_60_60 | 1.000 | 8 | 634.000 | 0.013 | 0.011 | 0.018 | 119.000 | 0.119 | 124.000 | -0.086 | 0.070 | 243.000 | 0.015 | 0.237 | 0.583 | 0.718 | 0.306 | 638.000 | 0.005 | 0.012 | 0.143 |
| W12_RSI2_3MIN_NYPM_LIM | W12_RSI2_3MIN_NYPM_LIM|tf=3,th=5,lim=0 | E2_60_60 | 0.981 | 16 | 619.000 | 0.003 | -0.009 | 0.020 | 118.000 | 0.137 | 123.000 | -0.094 | 0.054 | 241.000 | 0.019 | 0.305 | 0.583 | 0.887 | 0.266 | 573.000 | -0.014 | -0.007 | 0.115 |
| W1_ASIA_SWEEP_TRAP | W1_ASIA_SWEEP_TRAP|dep=10,conf=5 | E2_60_60 | 1.000 | 16 | 192.000 | -0.027 | 0.010 | -0.068 | 49.000 | -0.008 | 57.000 | -0.129 | -0.131 | 106.000 | -0.073 | -0.769 | 0.417 | 0.920 | 0.056 | 300.000 | -0.076 | -0.036 | 0.162 |
| W1_ASIA_SWEEP_TRAP_LIM | W1_ASIA_SWEEP_TRAP_LIM|dep=2,conf=5,lim=4 | E3_40_90 | 0.706 | 32 | 270.000 | 0.015 | 0.045 | -0.024 | 60.000 | 0.116 | 62.000 | -0.251 | -0.264 | 122.000 | -0.070 | -0.543 | 0.417 | 0.817 | 0.065 | 281.000 | -0.064 | 0.061 | 0.170 |
| W3_QUIET_LON_VWAP_ATRREL | W3_QUIET_LON_VWAP_ATRREL|z=2.0,q=0.8 | E1_40_40 | 1.000 | 16 | 349.000 | 0.025 | -0.015 | 0.083 | 60.000 | -0.077 | 49.000 | -0.071 | -0.176 | 109.000 | -0.074 | -0.785 | 0.417 | 0.795 | 0.063 | 401.000 | -0.044 | -0.044 | 0.137 |
| W3_QUIET_LON_VWAP_ATRREL_LIM | W3_QUIET_LON_VWAP_ATRREL_LIM|z=2.0,q=0.8,lim=4 | E1_40_40 | 0.653 | 32 | 217.000 | 0.041 | 0.054 | 0.026 | 43.000 | 0.050 | 39.000 | -0.189 | -0.344 | 82.000 | -0.064 | -0.583 | 0.500 | 0.858 | 0.058 | 289.000 | -0.107 | -0.144 | 0.088 |
| W4_GAP_DAYTYPE_1030 | W4_GAP_DAYTYPE_1030|k=0.15,er=0.08,mode=go | E3_40_90 | 1.000 | 32 | 154.000 | 0.182 | 0.225 | 0.128 | 35.000 | -0.022 | 28.000 | -0.082 | -0.082 | 63.000 | -0.048 | -0.259 | 0.417 | 0.039 | 0.115 | 114.000 | -0.003 | 0.043 | 0.298 |
| W6_PULLBACK_TO_OPEN_LOOSE | W6_PULLBACK_TO_OPEN_LOOSE|d=0.1,lvl=open,wend=(11, 30) | E3_40_90 | 1.000 | 8 | 187.000 | -0.007 | -0.045 | 0.058 | 32.000 | -0.025 | 46.000 | -0.257 | -0.288 | 78.000 | -0.162 | -1.011 | 0.333 | 0.830 | 0.070 | 225.000 | -0.018 | 0.083 | 0.472 |
| W7_POWER_HOUR_LOOSE | W7_POWER_HOUR_LOOSE|t=(14, 59),k=0.3,filt=dvh | E4_vol | 1.000 | 72 | 253.000 | 0.083 | 0.122 | 0.028 | 41.000 | 0.134 | 49.000 | 0.168 | -0.140 | 90.000 | 0.153 | 1.530 | 0.500 | 0.620 | 0.593 | 394.000 | -0.019 | -0.083 | -0.023 |
| W8_ES_LED_NYALL | W8_ES_LED_NYALL|L=30,bp=5,win=NYALL | E4_vol | 1.000 | 24 | 633.000 | 0.015 | 0.051 | -0.044 | 121.000 | -0.001 | 117.000 | -0.012 | 0.000 | 238.000 | -0.006 | -0.098 | 0.500 | 0.894 | 0.177 | 632.000 | -0.018 | -0.031 | 0.103 |
| W8_ES_LED_NYAM_BP2 | W8_ES_LED_NYAM_BP2|L=30,bp=2,win=NYAM | E3_40_90 | 1.000 | 8 | 658.000 | 0.022 | 0.048 | -0.018 | 126.000 | 0.056 | 121.000 | -0.055 | -0.164 | 247.000 | 0.002 | 0.019 | 0.500 | 0.672 | 0.281 | 657.000 | 0.072 | -0.079 | 0.006 |
| W9_LATE_EXT_LOOSE | W9_LATE_EXT_LOOSE|k=1.5 | E2_60_60 | 1.000 | 8 | 554.000 | -0.020 | -0.015 | -0.029 | 98.000 | 0.016 | 103.000 | 0.026 | 0.068 | 201.000 | 0.021 | 0.323 | 0.583 | 0.904 | 0.570 | 566.000 | 0.007 | -0.005 | 0.095 |
| W9_LATE_EXT_LOOSE_LIM | W9_LATE_EXT_LOOSE_LIM|k=1.5,lim=0 | E2_60_60 | 0.987 | 16 | 545.000 | -0.026 | -0.017 | -0.043 | 97.000 | 0.005 | 103.000 | 0.026 | 0.068 | 200.000 | 0.016 | 0.241 | 0.583 | 0.970 | 0.476 | 525.000 | -0.055 | -0.004 | 0.091 |

Limit-entry fill model: resting limit at the signal-bar close minus d points (d = 0 or 4, sell mirrored), live 10 bars, fills only on a 1-tick trade-through of the limit, at the limit, with a 0.5 pt adverse-selection haircut on the entry; stop checked from the fill bar, target from the next; fill rate = share of signals that fill (unfilled = no trade, so a limit book trades less and keeps only the signals that pulled back). The engine hook cannot carry limit entries: a _LIM survivor would need a new engine path before any stack test.

R = mean net R per trade at equal risk, $4.84 RT. UNT = HOLD + L6M (2025-11..2026-10). RC p = White reality check over the family's cells on the selection window. DSR = deflated Sharpe probability on the untouched year with N = cells of the family. roll = rolling 12-month pick / 3-month hold from 2024-04 (concatenated out-of-sample). shift ctl = mean R of the same selected rule with signals moved +-11/23/37 trading days (same time of day), untouched year.

### 3b. Diversification test (b), selected cells (daily $ at $1,200 risk per trade vs the JL3 stack daily net, base lots)

| family | cfg | exit | UNT n | UNT R | months+ | book $/wk UNT (x$1,200) | corr daily (all) | corr daily (UNT) | corr weekly | $ in JL3 5 deepest DDs | $ in JL3 20 worst weeks | a | b |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1_OPEN_DRIVE | L1_OPEN_DRIVE|W=60,mode=fail | E2_60_60 | 180.000 | -0.009 | 0.500 | -32.391 | -0.104 | -0.050 | -0.025 | 10249.560 | 1970.880 | False | True |
| L1_OPEN_DRIVE_LIM | L1_OPEN_DRIVE_LIM|W=60,mode=fail,lim=4 | E3_40_90 | 157.000 | 0.011 | 0.417 | 33.056 | -0.033 | -0.029 | -0.042 | 2798.820 | -3070.980 | False | False |
| L2_ASIA_RANGE | L2_ASIA_RANGE|b=10,mode=break | E1_40_40 | 125.000 | -0.037 | 0.333 | -89.062 | 0.153 | 0.112 | 0.187 | 759.300 | -4919.100 | False | False |
| L2_ASIA_RANGE_LIM | L2_ASIA_RANGE_LIM|b=0,mode=fade,lim=4 | E3_40_90 | 80.000 | -0.063 | 0.417 | -96.808 | -0.131 | -0.097 | -0.134 | 10815.660 | 11036.820 | False | True |
| L3_PRENY_DRIFT | L3_PRENY_DRIFT|k=0.1,mode=fade | E4_vol | 169.000 | -0.126 | 0.167 | -409.337 | -0.072 | -0.070 | -0.085 | 5162.025 | 1205.135 | False | True |
| L5_VWAP_REV_QUIET | L5_VWAP_REV_QUIET|z=2.5 | E2_60_60 | 78.000 | 0.007 | 0.455 | 10.296 | -0.115 | -0.168 | -0.204 | 3176.360 | 7346.240 | False | True |
| L5_VWAP_REV_QUIET_LIM | L5_VWAP_REV_QUIET_LIM|z=1.5,lim=4 | E2_60_60 | 97.000 | -0.088 | 0.417 | -163.854 | -0.076 | -0.082 | -0.095 | -2484.600 | 5605.600 | False | False |
| L6_ES_LED_LON | L6_ES_LED_LON|L=30,bp=5,win=LON | E3_40_90 | 145.000 | -0.169 | 0.417 | -472.159 | 0.079 | 0.116 | 0.139 | -17312.820 | -13426.800 | False | False |
| L6_ES_LED_NYAM | L6_ES_LED_NYAM|L=30,bp=3,win=NYAM | E3_40_90 | 243.000 | 0.094 | 0.583 | 439.997 | 0.064 | 0.132 | 0.125 | 35150.520 | -18186.240 | False | False |
| M1_SWEEP_REJECT_NYAM | M1_SWEEP_REJECT_NYAM|lvl=pd | E2_60_60 | 123.000 | -0.072 | 0.333 | -169.236 | -0.016 | 0.052 | 0.027 | -4772.200 | 4349.120 | False | False |
| M1_SWEEP_REJECT_NYAM_LIM | M1_SWEEP_REJECT_NYAM_LIM|lvl=pd,lim=4 | E2_60_60 | 110.000 | -0.147 | 0.250 | -311.016 | -0.010 | 0.051 | 0.014 | 571.840 | 6582.840 | False | True |
| M1_SWEEP_REJECT_NYPM | M1_SWEEP_REJECT_NYPM|lvl=on | E3_40_90 | 104.000 | -0.077 | 0.417 | -153.807 | -0.045 | -0.030 | -0.014 | -7316.280 | -10946.220 | False | False |
| M1_SWEEP_REJECT_NYPM_LIM | M1_SWEEP_REJECT_NYPM_LIM|lvl=on,lim=0 | E3_40_90 | 102.000 | -0.091 | 0.417 | -178.454 | -0.047 | -0.033 | 0.015 | -10571.760 | -13113.720 | False | False |
| M2_RSI2_LON | M2_RSI2_LON|tf=1,th=10 | E2_60_60 | 257.000 | -0.101 | 0.250 | -498.219 | -0.040 | -0.045 | -0.050 | 5228.840 | 1711.000 | False | True |
| M2_RSI2_LON_LIM | M2_RSI2_LON_LIM|tf=1,th=5,lim=4 | E3_40_90 | 205.000 | -0.103 | 0.333 | -404.981 | 0.012 | 0.018 | -0.122 | 12934.140 | 14649.780 | False | True |
| M2_RSI2_NYAM | M2_RSI2_NYAM|tf=1,th=10 | E4_vol | 257.000 | -0.021 | 0.417 | -103.622 | -0.077 | -0.120 | -0.096 | 19626.946 | -8643.113 | False | False |
| M2_RSI2_NYAM_LIM | M2_RSI2_NYAM_LIM|tf=1,th=10,lim=4 | E4_vol | 240.000 | -0.025 | 0.583 | -117.113 | -0.057 | -0.083 | -0.050 | 18992.600 | -9695.298 | False | False |
| M2_RSI2_NYPM | M2_RSI2_NYPM|tf=5,th=5 | E3_40_90 | 232.000 | -0.038 | 0.417 | -168.939 | -0.065 | -0.129 | -0.056 | 16323.120 | 8460.300 | False | True |
| M2_RSI2_NYPM_LIM | M2_RSI2_NYPM_LIM|tf=5,th=5,lim=4 | E3_40_90 | 199.000 | -0.067 | 0.583 | -256.687 | -0.073 | -0.161 | -0.078 | 32968.560 | 12702.180 | False | True |
| M3_FAILED_BREAK_LON | M3_FAILED_BREAK_LON|lb=60,rj=5 | E2_60_60 | 150.000 | 0.057 | 0.667 | 165.769 | -0.064 | -0.050 | -0.014 | 10907.160 | -1695.880 | True | False |
| M3_FAILED_BREAK_LON_LIM | M3_FAILED_BREAK_LON_LIM|lb=60,rj=5,lim=4 | E3_40_90 | 131.000 | 0.048 | 0.583 | 120.336 | 0.010 | 0.052 | -0.068 | 3044.160 | -611.460 | False | False |
| M3_FAILED_BREAK_NYAM | M3_FAILED_BREAK_NYAM|lb=30,rj=10 | E2_60_60 | 176.000 | 0.019 | 0.417 | 65.115 | -0.095 | -0.127 | -0.057 | 19386.160 | 3550.240 | False | True |
| M3_FAILED_BREAK_NYAM_LIM | M3_FAILED_BREAK_NYAM_LIM|lb=30,rj=10,lim=4 | E2_60_60 | 168.000 | 0.023 | 0.500 | 75.030 | -0.097 | -0.126 | -0.107 | 19479.240 | 11539.600 | False | True |
| M3_FAILED_BREAK_NYPM | M3_FAILED_BREAK_NYPM|lb=30,rj=5 | E2_60_60 | 147.000 | 0.054 | 0.583 | 154.063 | -0.015 | -0.063 | -0.147 | 6433.760 | 3349.920 | False | True |
| M3_FAILED_BREAK_NYPM_LIM | M3_FAILED_BREAK_NYPM_LIM|lb=30,rj=5,lim=0 | E2_60_60 | 146.000 | 0.061 | 0.583 | 171.368 | -0.022 | -0.075 | -0.142 | 7608.600 | 1794.600 | False | True |
| N1_ORB | N1_ORB|OR=30,ctx=with,mode=break | E3_40_90 | 104.000 | -0.267 | 0.250 | -534.696 | 0.136 | 0.112 | 0.116 | -14339.880 | -6989.340 | False | False |
| N1_ORB_LIM | N1_ORB_LIM|OR=5,ctx=with,mode=fade,lim=0 | E3_40_90 | 71.000 | -0.190 | 0.333 | -259.463 | -0.049 | 0.002 | -0.049 | -3649.680 | 3358.020 | False | False |
| N2_GAP | N2_GAP|k=0.3,mode=go | E3_40_90 | 143.000 | 0.035 | 0.667 | 96.704 | 0.091 | 0.105 | 0.175 | -6644.160 | -14329.440 | False | False |
| N3_DRIVE_PULLBACK | N3_DRIVE_PULLBACK|d=0.2,lvl=vwap | E2_60_60 | 91.000 | -0.060 | 0.417 | -105.536 | 0.093 | 0.140 | 0.041 | 7992.200 | -2014.560 | False | False |
| N4_1000_REVERSAL | N4_1000_REVERSAL|k=0.3,mode=cont | E3_40_90 | 87.000 | -0.073 | 0.417 | -122.502 | 0.063 | 0.087 | -0.110 | 17523.060 | 31785.180 | False | True |
| P1_LUNCH_RANGE | P1_LUNCH_RANGE|st=(11, 30),mode=fade | E4_vol | 140.000 | 0.001 | 0.667 | 2.977 | -0.012 | -0.053 | -0.104 | 20483.420 | 14181.920 | False | True |
| P2_VWAP_REV_PM | P2_VWAP_REV_PM|z=2.0 | E4_vol | 77.000 | -0.092 | 0.417 | -136.459 | -0.120 | -0.085 | -0.103 | 19682.594 | 18793.103 | False | True |
| P2_VWAP_REV_PM_LIM | P2_VWAP_REV_PM_LIM|z=2.0,lim=4 | E4_vol | 71.000 | -0.068 | 0.364 | -92.598 | -0.145 | -0.109 | -0.102 | 10209.780 | 15308.480 | False | True |
| P3_POWER_HOUR | P3_POWER_HOUR|k=0.4 | E4_vol | 122.000 | 0.194 | 0.667 | 455.973 | -0.020 | -0.077 | -0.008 | 2985.979 | 12417.063 | False | True |
| P4_LATE_EXT_FADE | P4_LATE_EXT_FADE|k=3 | E2_60_60 | 102.000 | -0.011 | 0.417 | -22.174 | -0.094 | -0.140 | -0.067 | 4911.040 | 2845.920 | False | True |
| P4_LATE_EXT_FADE_LIM | P4_LATE_EXT_FADE_LIM|k=3,lim=4 | E2_60_60 | 93.000 | -0.011 | 0.417 | -19.153 | -0.097 | -0.138 | -0.126 | 6184.920 | 6815.440 | False | True |
| W11_SESSION_EXTREME_RSI14_LON | W11_SESSION_EXTREME_RSI14_LON|r=80 | E3_40_90 | 56.000 | -0.046 | 0.333 | -50.025 | -0.079 | -0.031 | -0.103 | 2364.120 | 13378.740 | False | True |
| W11_SESSION_EXTREME_RSI14_LON_LIM | W11_SESSION_EXTREME_RSI14_LON_LIM|r=75,lim=4 | E3_40_90 | 106.000 | 0.094 | 0.667 | 191.874 | -0.072 | -0.008 | -0.106 | -3422.280 | 9720.420 | False | False |
| W11_SESSION_EXTREME_RSI14_NYAM | W11_SESSION_EXTREME_RSI14_NYAM|r=75 | E2_60_60 | 79.000 | 0.099 | 0.583 | 150.443 | -0.155 | -0.114 | 0.019 | 6332.360 | 3539.960 | False | False |
| W11_SESSION_EXTREME_RSI14_NYAM_LIM | W11_SESSION_EXTREME_RSI14_NYAM_LIM|r=75,lim=0 | E2_60_60 | 79.000 | 0.073 | 0.583 | 110.539 | -0.154 | -0.104 | 0.017 | 5412.360 | 3469.960 | False | False |
| W11_SESSION_EXTREME_RSI14_NYPM | W11_SESSION_EXTREME_RSI14_NYPM|r=75 | E2_60_60 | 48.000 | -0.128 | 0.333 | -118.306 | -0.082 | -0.100 | -0.076 | 3375.120 | 2208.520 | False | True |
| W11_SESSION_EXTREME_RSI14_NYPM_LIM | W11_SESSION_EXTREME_RSI14_NYPM_LIM|r=75,lim=4 | E3_40_90 | 45.000 | -0.079 | 0.500 | -68.096 | -0.048 | -0.072 | -0.088 | -6030.780 | -1232.700 | False | False |
| W12_RSI2_3MIN_LON | W12_RSI2_3MIN_LON|tf=3,th=5 | E2_60_60 | 257.000 | 0.007 | 0.583 | 33.271 | -0.085 | -0.129 | -0.107 | -3226.160 | -10199.000 | False | False |
| W12_RSI2_3MIN_LON_LIM | W12_RSI2_3MIN_LON_LIM|tf=3,th=10,lim=4 | E2_60_60 | 210.000 | -0.148 | 0.250 | -598.099 | -0.110 | -0.142 | -0.116 | 5054.040 | -1407.360 | False | False |
| W12_RSI2_3MIN_NYAM | W12_RSI2_3MIN_NYAM|tf=3,th=10 | E4_vol | 256.000 | -0.050 | 0.417 | -246.982 | -0.112 | -0.124 | -0.052 | 11372.578 | -8047.370 | False | False |
| W12_RSI2_3MIN_NYAM_LIM | W12_RSI2_3MIN_NYAM_LIM|tf=3,th=5,lim=4 | E1_40_40 | 229.000 | -0.099 | 0.500 | -433.855 | -0.112 | 0.010 | -0.075 | 1402.260 | -6820.800 | False | False |
| W12_RSI2_3MIN_NYPM | W12_RSI2_3MIN_NYPM|tf=3,th=5 | E2_60_60 | 243.000 | 0.015 | 0.583 | 67.771 | -0.083 | -0.132 | -0.090 | 29352.880 | 14135.680 | False | True |
| W12_RSI2_3MIN_NYPM_LIM | W12_RSI2_3MIN_NYPM_LIM|tf=3,th=5,lim=0 | E2_60_60 | 241.000 | 0.019 | 0.583 | 86.596 | -0.075 | -0.131 | -0.080 | 28582.720 | 13215.360 | False | True |
| W1_ASIA_SWEEP_TRAP | W1_ASIA_SWEEP_TRAP|dep=10,conf=5 | E2_60_60 | 106.000 | -0.073 | 0.417 | -149.087 | -0.157 | -0.227 | -0.206 | 2797.840 | 4644.640 | False | False |
| W1_ASIA_SWEEP_TRAP_LIM | W1_ASIA_SWEEP_TRAP_LIM|dep=2,conf=5,lim=4 | E3_40_90 | 122.000 | -0.070 | 0.417 | -164.795 | -0.136 | -0.120 | -0.177 | 24246.660 | 10290.900 | False | True |
| W3_QUIET_LON_VWAP_ATRREL | W3_QUIET_LON_VWAP_ATRREL|z=2.0,q=0.8 | E1_40_40 | 109.000 | -0.074 | 0.417 | -154.869 | -0.123 | -0.185 | -0.137 | 11373.720 | 221.760 | False | True |
| W3_QUIET_LON_VWAP_ATRREL_LIM | W3_QUIET_LON_VWAP_ATRREL_LIM|z=2.0,q=0.8,lim=4 | E1_40_40 | 82.000 | -0.064 | 0.500 | -100.286 | -0.108 | -0.149 | -0.150 | 18537.720 | 2294.460 | False | True |
| W4_GAP_DAYTYPE_1030 | W4_GAP_DAYTYPE_1030|k=0.15,er=0.08,mode=go | E3_40_90 | 63.000 | -0.048 | 0.417 | -58.652 | 0.116 | 0.114 | 0.045 | -3162.420 | 1174.320 | False | False |
| W6_PULLBACK_TO_OPEN_LOOSE | W6_PULLBACK_TO_OPEN_LOOSE|d=0.1,lvl=open,wend=(11, 30) | E3_40_90 | 78.000 | -0.162 | 0.333 | -242.729 | 0.053 | -0.039 | 0.059 | -11016.360 | -1852.800 | False | False |
| W7_POWER_HOUR_LOOSE | W7_POWER_HOUR_LOOSE|t=(14, 59),k=0.3,filt=dvh | E4_vol | 90.000 | 0.153 | 0.500 | 264.675 | 0.067 | 0.037 | 0.070 | -2378.691 | 2519.203 | False | False |
| W8_ES_LED_NYALL | W8_ES_LED_NYALL|L=30,bp=5,win=NYALL | E4_vol | 238.000 | -0.006 | 0.500 | -29.188 | 0.035 | 0.111 | 0.065 | -615.226 | -3790.782 | False | False |
| W8_ES_LED_NYAM_BP2 | W8_ES_LED_NYAM_BP2|L=30,bp=2,win=NYAM | E3_40_90 | 247.000 | 0.002 | 0.500 | 8.282 | 0.077 | 0.128 | 0.133 | 12711.000 | -17023.500 | False | False |
| W9_LATE_EXT_LOOSE | W9_LATE_EXT_LOOSE|k=1.5 | E2_60_60 | 201.000 | 0.021 | 0.583 | 81.285 | -0.117 | -0.144 | -0.129 | 7280.640 | 21923.600 | False | True |
| W9_LATE_EXT_LOOSE_LIM | W9_LATE_EXT_LOOSE_LIM|k=1.5,lim=0 | E2_60_60 | 200.000 | 0.016 | 0.583 | 60.449 | -0.114 | -0.143 | -0.140 | 5890.480 | 20598.440 | False | True |

(a) = untouched year positive, >= 150 trades, > 60% months positive. (b) = |daily corr| < 0.15 AND book $ >= 0 inside JL3's five deepest drawdown episodes AND its 20 worst weeks. Tier: a and b = LEAD (standalone, FIRST PASS); a only = LEAD-NO-HEDGE; otherwise FAIL. CONFIRMED needs engine controls (not finished).

### 3c. Best cell per session (pool of every family cell in the session, same selection rule)

| group | N | cfg | exit | SEL_n | SEL_R | HOLD_R | L6M_R | UNT_n | UNT_R | UNT_mpos | rc_p | dsr | corr_d | dd5 | worst20 | a | b |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SESSION_LON | 388 | W11_SESSION_EXTREME_RSI14_LON|r=80 | E3_40_90 | 151.000 | 0.162 | 0.105 | -0.248 | 56.000 | -0.046 | 0.333 | 0.848 | 0.030 | -0.079 | 2364.120 | 13378.740 | False | True |
| SESSION_NYAM | 500 | N4_1000_REVERSAL|k=0.3,mode=cont | E3_40_90 | 183.000 | 0.244 | 0.127 | -0.298 | 87.000 | -0.073 | 0.417 | 0.706 | 0.004 | 0.063 | 17523.060 | 31785.180 | False | True |
| SESSION_NYPM | 396 | W7_POWER_HOUR_LOOSE|t=(14, 59),k=0.3,filt=dvh | E4_vol | 253.000 | 0.083 | 0.134 | 0.168 | 90.000 | 0.153 | 0.500 | 1.000 | 0.391 | 0.067 | -2378.691 | 2519.203 | False | False |

### 3d. Information only: top 12 cells by untouched-year R among cells with SEL R > 0 and UNT n >= 100 (best-of-1324: selection-biased, NOT a result)

| cfg | exit | SEL_n | SEL_R | UNT_n | UNT_R | UNT_t | UNT_mpos | L6M_R |
|---|---|---|---|---|---|---|---|---|
| P3_POWER_HOUR|k=0.4 | E4_vol | 328 | 0.063 | 122 | 0.194 | 2.265 | 0.667 | 0.204 |
| P3_POWER_HOUR|k=0.4 | E3_40_90 | 328 | 0.021 | 122 | 0.190 | 1.599 | 0.667 | 0.023 |
| W7_POWER_HOUR_LOOSE|t=(14, 59),k=0.2,filt=dvh | E4_vol | 293 | 0.052 | 103 | 0.161 | 1.763 | 0.583 | 0.216 |
| N2_GAP|k=0.3,mode=fill | E3_40_90 | 302 | 0.013 | 143 | 0.160 | 1.225 | 0.667 | 0.184 |
| P3_POWER_HOUR|k=0.4 | E1_40_40 | 328 | 0.002 | 122 | 0.158 | 1.817 | 0.667 | 0.185 |
| W11_SESSION_EXTREME_RSI14_LON|r=75 | E4_vol | 330 | 0.032 | 138 | 0.152 | 1.850 | 0.833 | 0.212 |
| N2_GAP|k=0.15,mode=fill | E3_40_90 | 465 | 0.050 | 204 | 0.146 | 1.348 | 0.833 | 0.167 |
| W7_POWER_HOUR_LOOSE|t=(14, 59),k=0.2,filt=day | E4_vol | 478 | 0.030 | 193 | 0.128 | 1.957 | 0.750 | 0.141 |
| P3_POWER_HOUR|k=0.2 | E4_vol | 478 | 0.030 | 193 | 0.128 | 1.957 | 0.750 | 0.141 |
| W12_RSI2_3MIN_NYPM|tf=3,th=5 | E3_40_90 | 634 | 0.011 | 243 | 0.123 | 1.300 | 0.750 | 0.065 |
| W7_POWER_HOUR_LOOSE|t=(14, 59),k=0.3,filt=day | E4_vol | 386 | 0.065 | 156 | 0.121 | 1.616 | 0.667 | 0.119 |
| M3_FAILED_BREAK_LON_LIM|lb=60,rj=5,lim=4 | E2_60_60 | 250 | 0.062 | 131 | 0.114 | 1.364 | 0.750 | 0.147 |

### 3e. Near-miss extension (order item 3): P3 power hour and ES-led NY AM re-tested on a loosened PRE-REGISTERED grid (W7, W8), exit cell per cfg = best on the selection window

| fam | cfg | exit | SEL_n | SEL_R | HOLD_n | HOLD_R | L6M_n | L6M_R | UNT_n | UNT_R | UNT_mpos |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L6_ES_LED_NYAM | L6_ES_LED_NYAM|L=15,bp=3,win=NYAM | E4_vol | 654 | -0.017 | 125 | 0.064 | 120 | -0.074 | 245 | -0.003 | 0.500 |
| L6_ES_LED_NYAM | L6_ES_LED_NYAM|L=15,bp=5,win=NYAM | E4_vol | 616 | 0.006 | 119 | -0.010 | 119 | 0.052 | 238 | 0.021 | 0.500 |
| L6_ES_LED_NYAM | L6_ES_LED_NYAM|L=30,bp=3,win=NYAM | E3_40_90 | 657 | 0.039 | 123 | 0.148 | 120 | 0.039 | 243 | 0.094 | 0.583 |
| L6_ES_LED_NYAM | L6_ES_LED_NYAM|L=30,bp=5,win=NYAM | E4_vol | 624 | 0.029 | 121 | 0.000 | 116 | -0.009 | 237 | -0.004 | 0.417 |
| P3_POWER_HOUR | P3_POWER_HOUR|k=0.2 | E4_vol | 478 | 0.030 | 95 | 0.115 | 98 | 0.141 | 193 | 0.128 | 0.750 |
| P3_POWER_HOUR | P3_POWER_HOUR|k=0.4 | E4_vol | 328 | 0.063 | 65 | 0.186 | 57 | 0.204 | 122 | 0.194 | 0.667 |
| W7_POWER_HOUR_LOOSE | W7_POWER_HOUR_LOOSE|t=(14, 0),k=0.1,filt=day | E4_vol | 547 | 0.045 | 102 | 0.046 | 115 | -0.007 | 217 | 0.018 | 0.583 |
| W7_POWER_HOUR_LOOSE | W7_POWER_HOUR_LOOSE|t=(14, 0),k=0.1,filt=dvh | E4_vol | 327 | 0.044 | 58 | -0.047 | 63 | -0.113 | 121 | -0.081 | 0.417 |
| W7_POWER_HOUR_LOOSE | W7_POWER_HOUR_LOOSE|t=(14, 0),k=0.2,filt=day | E4_vol | 468 | 0.052 | 89 | 0.048 | 97 | -0.111 | 186 | -0.035 | 0.583 |
| W7_POWER_HOUR_LOOSE | W7_POWER_HOUR_LOOSE|t=(14, 0),k=0.2,filt=dvh | E4_vol | 296 | 0.046 | 51 | -0.072 | 56 | -0.144 | 107 | -0.110 | 0.333 |
| W7_POWER_HOUR_LOOSE | W7_POWER_HOUR_LOOSE|t=(14, 0),k=0.3,filt=day | E4_vol | 374 | 0.042 | 73 | -0.023 | 83 | -0.092 | 156 | -0.060 | 0.500 |
| W7_POWER_HOUR_LOOSE | W7_POWER_HOUR_LOOSE|t=(14, 0),k=0.3,filt=dvh | E4_vol | 245 | 0.044 | 45 | -0.083 | 50 | -0.141 | 95 | -0.113 | 0.333 |
| W7_POWER_HOUR_LOOSE | W7_POWER_HOUR_LOOSE|t=(14, 30),k=0.1,filt=day | E3_40_90 | 554 | -0.044 | 104 | 0.302 | 113 | 0.033 | 217 | 0.162 | 0.500 |
| W7_POWER_HOUR_LOOSE | W7_POWER_HOUR_LOOSE|t=(14, 30),k=0.1,filt=dvh | E1_40_40 | 345 | -0.042 | 61 | 0.210 | 50 | -0.026 | 111 | 0.104 | 0.583 |
| W7_POWER_HOUR_LOOSE | W7_POWER_HOUR_LOOSE|t=(14, 30),k=0.2,filt=day | E3_40_90 | 470 | -0.062 | 90 | 0.205 | 100 | 0.072 | 190 | 0.135 | 0.500 |
| W7_POWER_HOUR_LOOSE | W7_POWER_HOUR_LOOSE|t=(14, 30),k=0.2,filt=dvh | E1_40_40 | 311 | -0.042 | 54 | 0.172 | 47 | -0.006 | 101 | 0.089 | 0.583 |
| W7_POWER_HOUR_LOOSE | W7_POWER_HOUR_LOOSE|t=(14, 30),k=0.3,filt=day | E3_40_90 | 386 | -0.046 | 76 | 0.203 | 78 | -0.017 | 154 | 0.091 | 0.500 |
| W7_POWER_HOUR_LOOSE | W7_POWER_HOUR_LOOSE|t=(14, 30),k=0.3,filt=dvh | E3_40_90 | 270 | -0.040 | 49 | 0.262 | 43 | -0.079 | 92 | 0.103 | 0.500 |
| W7_POWER_HOUR_LOOSE | W7_POWER_HOUR_LOOSE|t=(14, 59),k=0.1,filt=day | E4_vol | 546 | 0.016 | 112 | 0.083 | 114 | 0.110 | 226 | 0.096 | 0.667 |
| W7_POWER_HOUR_LOOSE | W7_POWER_HOUR_LOOSE|t=(14, 59),k=0.1,filt=dvh | E4_vol | 324 | 0.042 | 60 | 0.078 | 58 | 0.124 | 118 | 0.101 | 0.583 |
| W7_POWER_HOUR_LOOSE | W7_POWER_HOUR_LOOSE|t=(14, 59),k=0.2,filt=day | E4_vol | 478 | 0.030 | 95 | 0.115 | 98 | 0.141 | 193 | 0.128 | 0.750 |
| W7_POWER_HOUR_LOOSE | W7_POWER_HOUR_LOOSE|t=(14, 59),k=0.2,filt=dvh | E4_vol | 293 | 0.052 | 51 | 0.105 | 52 | 0.216 | 103 | 0.161 | 0.583 |
| W7_POWER_HOUR_LOOSE | W7_POWER_HOUR_LOOSE|t=(14, 59),k=0.3,filt=day | E4_vol | 386 | 0.065 | 75 | 0.124 | 81 | 0.119 | 156 | 0.121 | 0.667 |
| W7_POWER_HOUR_LOOSE | W7_POWER_HOUR_LOOSE|t=(14, 59),k=0.3,filt=dvh | E4_vol | 253 | 0.083 | 41 | 0.134 | 49 | 0.168 | 90 | 0.153 | 0.500 |
| W8_ES_LED_NYALL | W8_ES_LED_NYALL|L=15,bp=2,win=NYALL | E4_vol | 635 | -0.024 | 121 | 0.016 | 117 | -0.017 | 238 | -0.000 | 0.417 |
| W8_ES_LED_NYALL | W8_ES_LED_NYALL|L=15,bp=3,win=NYALL | E4_vol | 635 | -0.024 | 121 | 0.049 | 117 | -0.068 | 238 | -0.009 | 0.500 |
| W8_ES_LED_NYALL | W8_ES_LED_NYALL|L=15,bp=5,win=NYALL | E4_vol | 628 | 0.004 | 119 | -0.017 | 117 | 0.052 | 236 | 0.017 | 0.500 |
| W8_ES_LED_NYALL | W8_ES_LED_NYALL|L=30,bp=2,win=NYALL | E4_vol | 635 | 0.005 | 121 | -0.017 | 117 | 0.018 | 238 | -0.000 | 0.417 |
| W8_ES_LED_NYALL | W8_ES_LED_NYALL|L=30,bp=3,win=NYALL | E4_vol | 635 | 0.011 | 121 | -0.001 | 117 | 0.000 | 238 | -0.000 | 0.500 |
| W8_ES_LED_NYALL | W8_ES_LED_NYALL|L=30,bp=5,win=NYALL | E4_vol | 633 | 0.015 | 121 | -0.001 | 117 | -0.012 | 238 | -0.006 | 0.500 |
| W8_ES_LED_NYAM_BP2 | W8_ES_LED_NYAM_BP2|L=15,bp=2,win=NYAM | E4_vol | 658 | -0.011 | 125 | 0.043 | 121 | -0.015 | 246 | 0.014 | 0.417 |
| W8_ES_LED_NYAM_BP2 | W8_ES_LED_NYAM_BP2|L=30,bp=2,win=NYAM | E3_40_90 | 658 | 0.022 | 126 | 0.056 | 121 | -0.055 | 247 | 0.002 | 0.500 |

Reading: only the wave-1 grid point P3 k=0.4 (122 untouched trades) has a clearly positive untouched year; the loosened grid (earlier entries, smaller thresholds, day+VWAP+last-hour filter) does not reproduce it at >= 150 trades with >60% positive months in any cell chosen on the selection window. Status of P3: LEAD-THIN (sample too small to confirm, not extended by the loosening).

### 2b. Shelf London/NY subset re-scored (step 1, standalone, 1-min simulator, current bars; top 20 NQ london/pre/nyam/nypm shelf trade lists with >= 150 trades ranked by the SHELF's own L6M $/wk, max 4 per family, so the ranking itself favours L6M)

Cells: H = the shelf's own stop/target distances and time exit replayed on 1-min bars (only where the list carries stop prices), E1/E2/E3 = common brackets 40/40, 60/60, 40/90 on the shelf's entry times. Entry = next 1-min bar open +1 tick, $4.84 RT. SEL = 2023-04..2025-10, UNT = 2025-11..2026-10. corr = daily correlation with the JL3 stack.

| id | session | status | shelf_L6M_wk | cell | SEL_n | SEL_R | HOLD_R | L6M_n | L6M_R | UNT_n | UNT_R | UNT_mpos | corr | a |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ.FADE_LV.69b05e1f | nyam | TOLERANT | 2423.966 | E2 | 594 | -0.025 | -0.086 | 117 | 0.159 | 227 | 0.040 | 0.417 | -0.082 | False |
| NQ.FADE_LV.69b05e1f | nyam | TOLERANT | 2423.966 | H | 594 | 0.011 | -0.128 | 117 | 0.175 | 227 | 0.028 | 0.750 | -0.074 | True |
| NQ.LRS.234b08c5 | nypm | NOW-ONLY | 2221.099 | E2 | 956 | -0.028 | 0.027 | 209 | 0.042 | 413 | 0.035 | 0.667 | 0.029 | True |
| NQ.LRS.234b08c5 | nypm | NOW-ONLY | 2221.099 | H | 956 | -0.022 | 0.056 | 209 | 0.071 | 413 | 0.064 | 0.667 | 0.079 | True |
| NQ.FADE_LV.d0d74664 | nyam | top-20 S2 | 2035.846 | E2 | 711 | -0.070 | -0.009 | 151 | 0.085 | 278 | 0.042 | 0.583 | -0.068 | False |
| NQ.FADE_LV.d0d74664 | nyam | top-20 S2 | 2035.846 | H | 711 | -0.108 | 0.064 | 151 | 0.062 | 278 | 0.063 | 0.583 | 0.031 | False |
| NQ.FADE_LV.0b691b4e | nyam | top-20 S2 | 2009.813 | E2 | 709 | -0.070 | -0.004 | 151 | 0.085 | 277 | 0.045 | 0.583 | -0.068 | False |
| NQ.FADE_LV.0b691b4e | nyam | top-20 S2 | 2009.813 | H | 709 | -0.108 | 0.071 | 151 | 0.048 | 277 | 0.058 | 0.500 | 0.037 | False |
| NQ.FADE_LV.04872708 | nyam | top-20 S2 | 1926.940 | E2 | 532 | -0.067 | 0.029 | 105 | 0.084 | 202 | 0.058 | 0.500 | -0.114 | False |
| NQ.FADE_LV.04872708 | nyam | top-20 S2 | 1926.940 | H | 532 | -0.125 | 0.033 | 105 | 0.206 | 202 | 0.123 | 0.583 | -0.068 | False |
| NQ.LRS.ef7b7bdf | nypm | killed | 1715.485 | E2 | 1239 | 0.026 | -0.007 | 200 | 0.146 | 435 | 0.063 | 0.667 | 0.084 | True |
| NQ.LRS.ef7b7bdf | nypm | killed | 1715.485 | H | 1239 | 0.004 | 0.024 | 200 | 0.043 | 435 | 0.033 | 0.583 | 0.073 | False |
| NQ.DIST_DISJncent.5c9404 | nyam | lead cell of its DISCOVER | 1675.053 | E2 | 144 | 0.034 | 0.004 | 46 | 0.126 | 95 | 0.063 | 0.500 | -0.012 | False |
| NQ.DIST_DISJncent.5c9404 | nyam | lead cell of its DISCOVER | 1675.053 | H | 144 | -0.018 | 0.012 | 46 | 0.328 | 95 | 0.165 | 0.750 | 0.030 | False |
| NQ.DIST_DISGG1.d13ecf | nyam | lead cell of its DISCOVER | 1251.423 | E2 | 740 | -0.071 | 0.090 | 131 | 0.094 | 261 | 0.092 | 0.667 | -0.085 | True |
| NQ.DIST_DISGG1.d13ecf | nyam | lead cell of its DISCOVER | 1251.423 | H | 740 | -0.049 | 0.083 | 131 | 0.136 | 261 | 0.110 | 0.667 | -0.035 | True |
| NQ.T2FNQ.383340d7 | nyam | NOW-ONLY | 997.264 | E2 | 3146 | -0.038 | -0.041 | 1624 | 0.108 | 3246 | 0.034 | 0.500 | -0.018 | False |
| NQ.T2FNQ.383340d7 | nyam | NOW-ONLY | 997.264 | H | 3146 | -0.014 | -0.046 | 1624 | 0.029 | 3246 | -0.008 | 0.583 | -0.032 | False |
| NQ.T2FNQ.ce5a2a7a | nyam | NOW-ONLY | 978.766 | E2 | 1522 | -0.049 | -0.095 | 508 | 0.054 | 907 | -0.011 | 0.500 | -0.100 | False |
| NQ.T2FNQ.ce5a2a7a | nyam | NOW-ONLY | 978.766 | H | 1522 | -0.037 | -0.011 | 508 | -0.018 | 907 | -0.015 | 0.417 | -0.079 | False |
| NQ.T2FNQ.db20c9e9 | nyam | NOW-ONLY | 947.133 | E2 | 1522 | -0.049 | -0.095 | 508 | 0.054 | 907 | -0.011 | 0.500 | -0.100 | False |
| NQ.T2FNQ.db20c9e9 | nyam | NOW-ONLY | 947.133 | H | 1522 | -0.037 | -0.011 | 508 | -0.018 | 907 | -0.015 | 0.417 | -0.079 | False |
| NQ.T2FNQ.fa4aac2a | nypm | NOW-ONLY | 884.826 | E2 | 3939 | 0.041 | -0.193 | 1450 | 0.053 | 2085 | -0.022 | 0.333 | 0.069 | False |
| NQ.T2FNQ.fa4aac2a | nypm | NOW-ONLY | 884.826 | H | 3939 | -0.034 | 0.015 | 1450 | 0.001 | 2085 | 0.005 | 0.583 | 0.070 | False |
| NQ.DIST_DISBNRELrev.6628b1 | nyam | lead cell of its DISCOVER | 782.597 | E2 | 229 | -0.028 | -0.006 | 39 | 0.135 | 75 | 0.067 | 0.417 | -0.078 | False |
| NQ.DIST_DISBNRELrev.6628b1 | nyam | lead cell of its DISCOVER | 782.597 | H | 229 | 0.001 | 0.200 | 39 | 0.409 | 75 | 0.309 | 0.667 | -0.039 | False |
| NQ.DIST_DISEprevdayfailure.f82e7b | nyam | lead cell of its DISCOVER | 703.185 | E2 | 201 | 0.074 | 0.099 | 58 | 0.114 | 110 | 0.107 | 0.667 | 0.034 | False |
| NQ.DIST_DISEprevdayfailure.f82e7b | nyam | lead cell of its DISCOVER | 703.185 | H | 201 | 0.059 | 0.074 | 58 | 0.212 | 110 | 0.146 | 0.833 | 0.019 | False |
| NQ.DIST_DISKcomphi.c1e03f | nyam | lead cell of its DISCOVER | 528.621 | E2 | 204 | 0.038 | 0.037 | 44 | 0.203 | 78 | 0.131 | 0.583 | 0.096 | False |
| NQ.DIST_DISKcomphi.c1e03f | nyam | lead cell of its DISCOVER | 528.621 | H | 204 | 0.037 | 0.126 | 44 | 0.196 | 78 | 0.165 | 0.583 | 0.104 | False |
| NQ.T2F1B.e3dde7b1 | nyam | NOW-ONLY | 352.118 | E2 | 403 | -0.003 | -0.045 | 78 | 0.225 | 173 | 0.077 | 0.667 | 0.056 | True |
| NQ.T2F1B.e3dde7b1 | nyam | NOW-ONLY | 352.118 | H | 403 | 0.031 | -0.231 | 78 | 0.397 | 173 | 0.052 | 0.417 | -0.028 | False |
| NQ.T2F1B.1624de42 | nyam | NOW-ONLY | 352.118 | E2 | 403 | -0.003 | -0.045 | 78 | 0.225 | 173 | 0.077 | 0.667 | 0.056 | True |
| NQ.T2F1B.1624de42 | nyam | NOW-ONLY | 352.118 | H | 403 | 0.031 | -0.231 | 78 | 0.397 | 173 | 0.052 | 0.417 | -0.028 | False |
| NQ.LRS.69f1daac | pre | NOW-ONLY | 338.288 | E2 | 204 | -0.018 | 0.307 | 52 | 0.077 | 90 | 0.174 | 0.833 | -0.010 | False |
| NQ.LRS.69f1daac | pre | NOW-ONLY | 338.288 | H | 204 | -0.005 | 0.321 | 52 | 0.099 | 90 | 0.193 | 0.833 | -0.000 | False |
| NQ.DIST_Q13lead.ecd086 | nyam | lead cell of its DISCOVER | 307.134 | E2 | 188 | 0.066 | -0.027 | 40 | -0.106 | 87 | -0.064 | 0.167 | -0.064 | False |
| NQ.DIST_Q13lead.ecd086 | nyam | lead cell of its DISCOVER | 307.134 | H | 188 | -0.088 | -0.022 | 40 | 0.084 | 87 | 0.027 | 0.500 | -0.073 | False |
| NQ.T2F1B.9f24bfaf | nyam | NOW-ONLY | 250.715 | E2 | 403 | -0.003 | -0.045 | 78 | 0.225 | 173 | 0.077 | 0.667 | 0.056 | True |
| NQ.T2F1B.9f24bfaf | nyam | NOW-ONLY | 250.715 | H | 403 | 0.090 | -0.228 | 78 | 0.161 | 173 | -0.053 | 0.500 | -0.042 | False |

Reading: nearly every shelf book is NEGATIVE or flat on the 31-month selection window and positive only on L6M/HOLD (NOW-ONLY pattern); under the common 60/60 bracket none has SEL R above 0.075 and the untouched-year means are small (0.03-0.17 R); the (a) flag is set only where the untouched year has >= 150 trades, mean > 0 and > 60% positive months. The engine-exact marginal tests of these books are W-MB's (DS3_MAJOR_B_BOOKS.md). Dedup caveat: several ids share one trade list.

## 4. Not run / limits
- DAX not available: ES-led only (ES file ends 2026-10-16, so L6M loses its last 2 weeks for L6). No economic calendar in the simulator: the 08:30 family (L4) fires on any day with an impulse. No volume: VWAP is equal-weight. Resting-limit entries are not simulated (market entries only; the engine hook supports market only). One signal per day per config.
- Families with < 150 selection trades (L4 08:30 pullback, N5 chop/trend day at these thresholds) are listed with n; they cannot reach the >= 150 untouched-year bar.

## 5. Exact-engine stack test (JL3 + one injected book, tag MF1; uw_inject hook; sets TL3_MF_*)

Identity (inert event file, registered book): 202610 PASS (691 vs 691 trades, net 37159.82 vs 37159.82); 202504 PASS (637 vs 637 trades, net 41239.76 vs 41239.76). Reference: JL3 202610 = 691 trades net 37,159.82; 202504 = 637 / 41,239.76 (engine fee 1.18/lot). A candidate's rows are NOT USED until both identity lines say PASS.

No engine months have landed for the candidates yet (queued: _major_f/pending.txt after B in QUEUES.txt; tag MF @4; box 1 filler QL_NCH=4). Rows appear here automatically.

Candidates sent to the engine (frozen 11-17 from the standalone table: family or session pick with UNT R > 0.03, UNT n >= 100, SEL R > 0): P3_POWER_HOUR|k=0.4 E4_vol, L6_ES_LED_NYAM|L=30,bp=3,win=NYAM E3_40_90, M3_FAILED_BREAK_LON|lb=60,rj=5 E2_60_60, M3_FAILED_BREAK_NYPM|lb=30,rj=5 E2_60_60, N2_GAP|k=0.3,mode=go E3_40_90.

30 date-shifted engine controls: NOT FINISHED (the loop builds them for the best candidate once its L6M+HOLD months and the identity lines have landed).

Part A lot vector and part B shelf picks together with survivors: NOT FINISHED (needs W-MA / W-MB sets; the loop does not stack on top of their sets without their final picks).

## 6. Plain specs for the standalone leads (precise enough to code into DS7 exactly as tested)

**M3_FAILED_BREAK_LON|lb=60,rj=5 E2_60_60 [LEAD]**. Failed breakout re-entry: first 1-min close beyond the prior 60-bar high/low in the session window, then a close back inside within 5 bars: enter against the break at that close. Exit: stop 60 / target 60 points; flat at session end (LON 08:28, PRE 09:28, NYAM 11:58, NYPM 15:58 ET). Lots = round(1200/(stop x $20)), 1 to 10 (equal ~$1,200 risk); market entry at the open after the signal bar; $4.84 RT per lot. Slot: D7 has no London/NY-session mean-reversion or ES-led book; it needs a new book slot (an event-driven book like O7/H7 with its own cap) - none of K7/M7/U7/P7/H7/A7/O7 can carry it without new entry code, the hook in th_uwbooks/uw_inject shows the engine can hold one extra book.

**P3_POWER_HOUR|k=0.4 E4_vol [engine candidate (not a lead)]**. Power-hour continuation: at 14:59 ET if |close - open(09:30)| >= 0.4 x ATR14 enter with the day's direction; flat 15:58. Exit: stop = target = clip(0.12 x ATR14, 25, 90) points; flat at session end (LON 08:28, PRE 09:28, NYAM 11:58, NYPM 15:58 ET). Lots = round(1200/(stop x $20)), 1 to 10 (equal ~$1,200 risk); market entry at the open after the signal bar; $4.84 RT per lot. Slot: D7 has no London/NY-session mean-reversion or ES-led book; it needs a new book slot (an event-driven book like O7/H7 with its own cap) - none of K7/M7/U7/P7/H7/A7/O7 can carry it without new entry code, the hook in th_uwbooks/uw_inject shows the engine can hold one extra book.

**L6_ES_LED_NYAM|L=30,bp=3,win=NYAM E3_40_90 [engine candidate (not a lead)]**. ES-led catch-up: over the last 30 minutes ES (continuous) moved |r_es| > 3 bp and NQ moved less in the same direction by more than 3 bp: enter NQ with ES at that close. Window NYAM: LON 02:30-08:00 ET, NYAM 09:45-11:30 ET. One trade per day. (ES bar file ends 2026-10-16; DAX not available.) Exit: stop 40 / target 90 points; flat at session end (LON 08:28, PRE 09:28, NYAM 11:58, NYPM 15:58 ET). Lots = round(1200/(stop x $20)), 1 to 10 (equal ~$1,200 risk); market entry at the open after the signal bar; $4.84 RT per lot. Slot: D7 has no London/NY-session mean-reversion or ES-led book; it needs a new book slot (an event-driven book like O7/H7 with its own cap) - none of K7/M7/U7/P7/H7/A7/O7 can carry it without new entry code, the hook in th_uwbooks/uw_inject shows the engine can hold one extra book.

**M3_FAILED_BREAK_NYPM|lb=30,rj=5 E2_60_60 [engine candidate (not a lead)]**. Failed breakout re-entry: first 1-min close beyond the prior 30-bar high/low in the session window, then a close back inside within 5 bars: enter against the break at that close. Exit: stop 60 / target 60 points; flat at session end (LON 08:28, PRE 09:28, NYAM 11:58, NYPM 15:58 ET). Lots = round(1200/(stop x $20)), 1 to 10 (equal ~$1,200 risk); market entry at the open after the signal bar; $4.84 RT per lot. Slot: D7 has no London/NY-session mean-reversion or ES-led book; it needs a new book slot (an event-driven book like O7/H7 with its own cap) - none of K7/M7/U7/P7/H7/A7/O7 can carry it without new entry code, the hook in th_uwbooks/uw_inject shows the engine can hold one extra book.

**N2_GAP|k=0.3,mode=go E3_40_90 [engine candidate (not a lead)]**. Gap go: at 09:34 bar close, if |gap| >= 0.3 x ATR14 (prior-14-day mean RTH range) enter with the gap (go) or against it (fill). One trade per day. Exit: stop 40 / target 90 points; flat at session end (LON 08:28, PRE 09:28, NYAM 11:58, NYPM 15:58 ET). Lots = round(1200/(stop x $20)), 1 to 10 (equal ~$1,200 risk); market entry at the open after the signal bar; $4.84 RT per lot. Slot: D7 has no London/NY-session mean-reversion or ES-led book; it needs a new book slot (an event-driven book like O7/H7 with its own cap) - none of K7/M7/U7/P7/H7/A7/O7 can carry it without new entry code, the hook in th_uwbooks/uw_inject shows the engine can hold one extra book.

