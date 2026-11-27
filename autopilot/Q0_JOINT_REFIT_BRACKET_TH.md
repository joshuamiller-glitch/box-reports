# Q0: re-fitting every layer together on the LIVE mixes (W-Q0). Status 27 Nov 02:50Z: LIVE ASIA SCREEN VERDICTS, joint stage queued

## ANSWER FIRST (live Asia mix: STKd8da2eb47b, 4 books MF1..MF4, 2 lots, exact engine; DRAWDOWN AND WORST WEEK FIRST)
1. Re-fitting does NOT beat holding for almost every Asia layer. Of 30 layer groups, 1 is RE-FIT (ZONE on book MF3, refit max DD 5,518 shallower than bare, hold 1,665; refit shallower than held in 77% of 13-week blocks); the drawdown-lowering layers are SET ONCE AND HOLD: DLA, DLB, DLC (day-loss stops), SC, SZW (ER sizer), STK (session stop), CAP, CG on the mix; LOCK / TAKE on books MF2, MF3, MF4 and TAKE on MF1. Bracket (17) re-fitting: no layer, no book (hold is deeper than bare in MF1, MF2, MF4; MF3 hold P30 shallower by 7,386 but weak).
2. Drawdown cut vs the bare mix (all layers off = reference only, never delivered): held DLA +17,083 / worst week +12,643 (income -439 $/wk), STK +13,053 / +20,854 (-702), SZW +14,454 / +8,544 (-755), SC +11,786 / +8,025 (-296), DLC +8,198 (-742), TAKE MF1 +8,577 (-753). Bare mix: max DD -59,220, worst week -36,212, +5,164 $/wk. Every drawdown cut costs income; none raises it (CG +182 $/wk is the only plus).
3. Per book: MF1 SET ONCE (TAKE FR_TAKE4), MF2 SET ONCE (LOCK LK9 weak, TAKE TK11), MF3 RE-FIT (ZONE) + SET ONCE (LOCK, bracket), MF4 SET ONCE (LOCK LK4). No book is LEAVE BARE in Asia on this screen. Per mix: all mix layers except NTS (NO EFFECT) are SET ONCE AND HOLD.
4. THIS IS A SINGLE-LAYER walk-forward (one layer varied on the bare mix, all settings of the layer as the menu, prior-year filter via pick_filtered.hist_pass on data to date). The JOINT stage (13 dates x 80 combos, top 3 + off per factor, seed 20261126) is queued (43,680 rows); the joint verdict replaces these when it lands. Live books are hindsight-chosen. Best-of-6 penalty (6 versions: 2/4/13 weeks x 3M/6M) not yet applied; the versions are reported as their mean here. Layer settings that fail the filter are shown as WEAK, never as off.

## Method as run (mine, flagged)
Walk-forward from 2023-10-01 (week 26); dates every 2/4/13 weeks; trailing 3 or 6 months; score = ulcer (drawdown first) with guard (worst week and max DD not >15% worse than off, income >= 90% of off); hold = setting chosen at the first date kept. Verdict thresholds: NO EFFECT = all four changes < 1,500; RE-FIT = refit DD at least 1,500 shallower than hold AND shallower than hold in >= 60% of 13-week blocks; SET ONCE AND HOLD = hold DD >= 1,500 shallower than bare. Code code/th_q0 (build_q0.py, wf_layer.py, verdict_q0.py, build_joint_q0.py).

## Tables
Bare mix (all layers off, reference only), walk-forward span from 2023-10-01: max DD -59220, worst week -36212, $/wk 5164; L6M max DD -59220, L3M max DD -21112.

Per layer (dDD / dWorstWk = change vs bare, positive = shallower; dInc = change in $/wk; refit = mean of 6 versions (2/4/13 wk x 3M/6M), hold = setting chosen at first date, kept):

| layer | verdict | refit dDD / dWW / dInc | hold dDD / dWW / dInc | L6M dDD refit / hold | L3M dDD refit / hold | refit shallower than hold (13-wk blocks) | setting rule picks today |
|---|---|---|---|---|---|---|---|
| LOSS.MF1 | NO EFFECT | +0 / +0 / -116 | +0 / +0 / +0 | +0 / +0 | -416 / +0 | 8% | LOSSMF1_CU4 |
| LOCK.MF1 | NO EFFECT (hold deeper than bare) | +4752 / +4074 / -124 | +1465 / +1465 / +91 | +4752 / +1465 | -1902 / +1620 | 42% | LOCKMF1_LK2 |
| TAKE.MF1 | SET ONCE AND HOLD | +1972 / +2100 / -326 | +8577 / +9076 / -753 | +1972 / +8577 | +1743 / -1506 | 46% | TAKEMF1_FR_TAKE4  [WEAK: fails the prior-year filter / guard] |
| ZONE.MF1 | NO EFFECT (hold deeper than bare) | +4353 / +3154 / -271 | +805 / +0 / -71 | +4353 / +805 | +2664 / -565 | 50% | ZONEMF1_ZONE3 |
| LOSS.MF2 | NO EFFECT | +753 / +753 / -128 | +223 / +223 / +46 | +753 / +223 | -2475 / -1809 | 19% | LOSSMF2_CU4 |
| LOCK.MF2 | SET ONCE AND HOLD | -355 / +0 / -133 | +6580 / +1540 / -217 | -355 / +6580 | -377 / -1887 | 15% | LOCKMF2_LK9  [WEAK: fails the prior-year filter / guard] |
| TAKE.MF2 | SET ONCE AND HOLD | +1313 / -1600 / -115 | +3860 / -2355 / -81 | +1313 / +3860 | -206 / -66 | 0% | TAKEMF2_TK11 |
| ZONE.MF2 | NO EFFECT | +0 / +0 / -110 | +0 / +0 / -265 | +0 / +0 | +0 / +0 | 15% | ZONEMF2_ZONE1 |
| LOSS.MF3 | NO EFFECT | +623 / +407 / +65 | +0 / +0 / -9 | +623 / +0 | +949 / +0 | 58% | LOSSMF3_CX3 |
| LOCK.MF3 | SET ONCE AND HOLD | +2884 / -1182 / -37 | +6656 / +1650 / +35 | +2884 / +6656 | -3615 / -3615 | 0% | LOCKMF3_LK3  [WEAK: fails the prior-year filter / guard] |
| TAKE.MF3 | NO EFFECT | +0 / +0 / -29 | +0 / +0 / +0 | +0 / +0 | +0 / +0 | 0% | TAKEMF3_NRT1 |
| ZONE.MF3 | RE-FIT | +5518 / +3884 / -233 | +1665 / +0 / -24 | +5518 / +1665 | +961 / -895 | 77% | ZONEMF3_ZONE1 |
| LOSS.MF4 | NO EFFECT | +0 / +0 / -10 | +0 / +0 / -0 | +0 / +0 | +0 / +0 | 23% | LOSSMF4_CU3 |
| LOCK.MF4 | SET ONCE AND HOLD | +1145 / +1145 / -68 | +6050 / +6925 / -246 | +1145 / +6050 | +0 / +0 | 31% | LOCKMF4_LK4 |
| TAKE.MF4 | NO EFFECT | +1460 / +1460 / -104 | +1460 / +1460 / -47 | +1460 / +1460 | +0 / +0 | 23% | TAKEMF4_NRT1 |
| ZONE.MF4 | NO EFFECT | -595 / +0 / -33 | -1190 / +0 / -95 | -595 / -1190 | +20 / -1156 | 46% | ZONEMF4_ZONE1 |
| DLA | SET ONCE AND HOLD | +1385 / +1385 / -633 | +17083 / +12643 / -439 | +1385 / +21102 | -7625 / -8538 | 35% | DLA_DLA11 |
| DLB | SET ONCE AND HOLD | +3621 / +12125 / -586 | +2759 / +16912 / -937 | +7077 / +18101 | -1683 / -3429 | 27% | DLB_DLB14 |
| DLC | SET ONCE AND HOLD | +4809 / +7212 / -594 | +8198 / +7546 / -742 | +4810 / +8198 | -6457 / -5029 | 54% | DLC_DLC4 |
| SC | SET ONCE AND HOLD | +11786 / +8025 / -296 | +11786 / +8025 / -296 | +11786 / +11786 | +807 / +807 | 0% | SC_SC3  [WEAK: fails the prior-year filter / guard] |
| BL | NO EFFECT | -1721 / +1680 / -294 | -1682 / +1719 / -590 | -1721 / -1682 | +0 / +0 | 23% | BL_BL8 |
| CAP | SET ONCE AND HOLD | +0 / +0 / -100 | +3244 / +12241 / -583 | +0 / +3244 | +0 / -2287 | 15% | CAP_CAP1 |
| STK | SET ONCE AND HOLD | -119 / +0 / -401 | +13053 / +20854 / -702 | -119 / +13053 | +1994 / +2991 | 8% | STK_STK8 |
| SZW | SET ONCE AND HOLD | +11094 / +5696 / -378 | +14454 / +8544 / -755 | +11094 / +14454 | +1253 / +7517 | 4% | SZW_SZW3 |
| NTS | NO EFFECT | +0 / +0 / -31 | +0 / +0 / +0 | +0 / +0 | +0 / +0 | 8% | NTS_NTS2 |
| CG | SET ONCE AND HOLD | -975 / -975 / +24 | +2868 / +3139 / +182 | -975 / +2868 | -1401 / -1401 | 8% | CG_CGB3 |
| BRK.MF1 | NO EFFECT (hold deeper than bare) | +4151 / +13177 / -1706 | -9203 / +6104 / -1435 | +16346 / +13448 | -1104 / -20191 | 54% | BRKMF1_F80_40  [WEAK: fails the prior-year filter / guard] |
| BRK.MF2 | NO EFFECT (hold deeper than bare) | +11020 / +3730 / -131 | +865 / +860 / -60 | +11020 / +865 | -1877 / +3005 | 31% | BRKMF2_F80_40  [WEAK: fails the prior-year filter / guard] |
| BRK.MF3 | SET ONCE AND HOLD | +5217 / +3407 / -925 | +7386 / +2798 / -211 | +5217 / +7386 | -32134 / +941 | 35% | BRKMF3_P30  [WEAK: fails the prior-year filter / guard] |
| BRK.MF4 | NO EFFECT | -11828 / -6431 / -102 | -11663 / +1688 / -292 | -11828 / -11663 | -3095 / -2520 | 46% | BRKMF4_F80_40  [WEAK: fails the prior-year filter / guard] |

Per book (strongest layer decides; a book is LEAVE BARE when none of its five groups moves drawdown or worst week by 1,500):

| book | verdict | layers | held setting(s) today |
|---|---|---|---|
| MF1 | SET ONCE | LOSS NO EFFECT, LOCK NO EFFECT (hold deeper than bare), TAKE SET ONCE AND HOLD, ZONE NO EFFECT (hold deeper than bare), BRK NO EFFECT (hold deeper than bare) | LOCKMF1_LK2; TAKEMF1_FR_TAKE4  [WEAK: fails the prior-year filter / guard]; ZONEMF1_ZONE3; BRKMF1_F80_40  [WEAK: fails the prior-year filter / guard] |
| MF2 | SET ONCE | LOSS NO EFFECT, LOCK SET ONCE AND HOLD, TAKE SET ONCE AND HOLD, ZONE NO EFFECT, BRK NO EFFECT (hold deeper than bare) | LOCKMF2_LK9  [WEAK: fails the prior-year filter / guard]; TAKEMF2_TK11; BRKMF2_F80_40  [WEAK: fails the prior-year filter / guard] |
| MF3 | RE-FIT | LOSS NO EFFECT, LOCK SET ONCE AND HOLD, TAKE NO EFFECT, ZONE RE-FIT, BRK SET ONCE AND HOLD | LOCKMF3_LK3  [WEAK: fails the prior-year filter / guard]; ZONEMF3_ZONE1; BRKMF3_P30  [WEAK: fails the prior-year filter / guard] |
| MF4 | SET ONCE | LOSS NO EFFECT, LOCK SET ONCE AND HOLD, TAKE NO EFFECT, ZONE NO EFFECT, BRK NO EFFECT | LOCKMF4_LK4 |
