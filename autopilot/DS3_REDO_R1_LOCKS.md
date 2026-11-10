# DS3_REDO_R1_LOCKS - T-STACK-REDO R1: locks on the state base (first version 2026-11-10 08:17Z)

> **Label: PRE-PROOF; post-hoc; Shadow only; no PASS claims. FIRST-ORDER SCREEN ONLY unless a row is in the exact table below. ROLL-EXCL: the 31 roll-artifact base trades are excluded from every number. STANDING RULE: every lock stays ON; "off" rows are reference rows only; the deliverable is the best SETTING (drawdown first at equal mean, holds OOS); if nothing beats the live setting the live setting stays.**

Method: the screen runs on the EXACT NOLOCK trade list (engine with the lock layer switched off, 33 window months; screen base = DIR:/mnt/l2/l2vast/_th_state/s345/exact_b/runs/CDE_NOLOCK) so any lock setting, tighter or looser than live, is replayed first-order (realized-only state: a lock triggers when a trade exits; the engine also marks open P&L and flattens, which the screen cannot see). Reference = the live setting = S1b-COMB exact list. Regression: the exact lock override with the live values reproduces S1-COMB 202605 trade for trade (672 trades, net 35,852). Day caps use realized P&L only (as live check_limits), give-back and week floor use realized + open P&L. R on base lots = planned lots x 60 pt x $20 (PE 8,400, KB/MV 2,400, HM/SM 4,800, PB/OD 1,200; x max(1, size mult)). Scope: PerBook = per-book values; stack ($) rows are Combined; "(+live pb)" = Combined on top of the live per-book locks. One-book scopes keep the live locks on the other books.

## Overall: top 15 settings by the joint equal-mean cut (min of L6M, PRE, X')

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_rbasis | R_on_sized_lots | P7 | +38.5/+38.5/+68.7/-26.6/+36.1/+14.7 | +4488 | +46.7/+46.7/+72.9 | +44.6/+26.0 | -33.8/-32.4 | 2606 / -220754 (+4151936/-4372689) | +120445/-112727/-200770/-27702 | 0.01 / 0.08 | +28.3 / -2118 / 72% | OK-PRIOR (allow 25%, deeper -36%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_rbasis | R_on_sized_lots | ALL | +37.6/+37.6/+67.8/-1.1/+40.8/+30.8 | +1751 | +41.1/+41.1/+69.6 | +44.2/+34.7 | -17.3/-32.2 | 5372 / -221650 (+5736531/-5958181) | +115940/-89130/-228335/-20124 | 0.01 / 0.15 | +28.3 / -2118 / 72% | OK-PRIOR (allow 25%, deeper -41%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win4_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+45.0/+7.5/+12.9/+14.9 | +2211 | +33.7/+33.7/+48.9 | +19.1/+20.9 | -25.2/-12.9 | 2107 / -197930 (+3050331/-3248261) | +128501/-116110/-182618/-27702 | 0.01 / 0.39 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win6_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+45.0/+7.5/+12.9/+14.9 | +1690 | +32.6/+32.6/+48.0 | +17.7/+19.6 | -23.0/-11.4 | 2052 / -167932 (+2946004/-3113936) | +145059/-94801/-190489/-27702 | 0.01 / 0.45 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win8_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+45.0/+7.5/+12.9/+14.9 | +1690 | +32.6/+32.6/+48.0 | +17.7/+19.6 | -23.0/-11.4 | 2052 / -167932 (+2946004/-3113936) | +145059/-94801/-190489/-27702 | 0.01 / 0.45 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win5_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+45.0/+7.5/+12.9/+14.9 | +1672 | +32.6/+32.6/+48.0 | +17.7/+19.6 | -23.1/-11.4 | 2057 / -167484 (+2955584/-3123068) | +145059/-91941/-192901/-27702 | 0.01 / 0.46 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_combo | win3_loss1_arm1_keep0.5_floor8 | P7 | +32.6/+32.6/+83.3/+7.5/+38.7/+6.6 | -3225 | +24.2/+24.2/+81.2 | +31.0/-5.0 | -19.1/-5.0 | 2597 / -111240 (+4173208/-4284448) | +182664/-110527/-155675/-27702 | 0.03 / 0.46 | +27.9 / -2695 / 69% | OK-PRIOR (allow 25%, deeper -39%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win3_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+60.1/+7.5/+12.9/+14.9 | -315 | +27.9/+27.9/+59.7 | +12.0/+14.0 | -24.1/-5.3 | 2202 / -118223 (+3318877/-3437099) | +143211/-60801/-172932/-27702 | 0.01 / 0.47 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win4_loss1(arm2,keep.5,floor12) | ALL | +25.6/+25.6/+66.3/+13.6/+11.0/+16.1 | -1497 | +21.6/+21.6/+64.4 | +6.2/+11.5 | -24.2/-7.5 | 4394 / -118844 (+4420894/-4539738) | +167270/-63531/-176726/-45857 | 0.06 / 0.73 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -11%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win5_loss1(arm2,keep.5,floor12) | ALL | +25.6/+25.6/+60.2/+13.6/+10.6/+16.1 | -1439 | +21.8/+21.8/+58.2 | +6.0/+11.7 | -23.1/-8.0 | 4255 / -106687 (+4261297/-4367983) | +184525/-40302/-190656/-60254 | 0.08 / 0.78 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -11%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win8_loss1(arm2,keep.5,floor12) | ALL | +25.6/+25.6/+60.2/+13.6/+10.6/+16.1 | -1502 | +21.6/+21.6/+58.1 | +5.8/+11.5 | -21.9/-8.0 | 4196 / -109352 (+4219368/-4328720) | +184525/-40426/-184688/-68763 | 0.04 / 0.78 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -11%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win6_loss1(arm2,keep.5,floor12) | ALL | +25.6/+25.6/+60.2/+13.6/+10.6/+16.1 | -1555 | +21.4/+21.4/+58.0 | +5.6/+11.3 | -21.6/-7.8 | 4206 / -108265 (+4226556/-4334821) | +184525/-40426/-184688/-67676 | 0.07 / 0.78 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -11%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win3_loss1(arm2,keep.5,floor12) | ALL | +25.6/+25.6/+74.7/+11.2/+9.5/+16.1 | -4487 | +12.1/+12.1/+70.1 | -7.0/+0.8 | -20.7/+4.4 | 4707 / -12218 (+4832509/-4844727) | +183733/-15328/-156613/-24010 | 0.08 / 0.94 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -9%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_giveback | arm1_keep0.7(win5,loss2,floor12) | P7 | +6.9/+6.9/+55.5/+22.8/+30.0/-0.3 | +1823 | +12.4/+12.4/+58.1 | +34.1/+5.6 | -24.9/-20.0 | 1810 / -287060 (+2364608/-2651668) | -29272/-52294/-177792/-27702 | 0.03 / 0.98 | +38.9 / -2067 / 57% | OK-PRIOR (allow 15%, deeper -30%) | LEAD-RECENT (bi-weekly WF 57% < 60) |
| comb_weekfloor | stack_floor$30000(+live pb) | ALL | +21.7/+21.7/+21.6/+19.5/+19.9/-7.2 | -1609 | +17.1/+17.1/+17.0 | +15.3/-13.4 | +7.2/-13.5 | 4187 / -177663 (+4262387/-4440050) | +133506/-110625/-176706/-23837 | 0.07 / 1.00 | +0.0 / -3283 / 46% | OK-PRIOR (allow 15%, deeper -20%) | LEAD-RECENT (bi-weekly WF 46% < 60) |


## Daily caps (win R x loss R)

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_daycaps | win4_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+45.0/+7.5/+12.9/+14.9 | +2211 | +33.7/+33.7/+48.9 | +19.1/+20.9 | -25.2/-12.9 | 2107 / -197930 (+3050331/-3248261) | +128501/-116110/-182618/-27702 | 0.01 / 0.39 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | winoff_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+45.0/+7.5/+12.9/+14.9 | +1690 | +32.6/+32.6/+48.0 | +17.7/+19.6 | -23.0/-11.4 | 2052 / -167932 (+2946004/-3113936) | +145059/-94801/-190489/-27702 | na | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) | reference row |
| pb_daycaps | win8_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+45.0/+7.5/+12.9/+14.9 | +1690 | +32.6/+32.6/+48.0 | +17.7/+19.6 | -23.0/-11.4 | 2052 / -167932 (+2946004/-3113936) | +145059/-94801/-190489/-27702 | 0.01 / 0.45 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win6_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+45.0/+7.5/+12.9/+14.9 | +1690 | +32.6/+32.6/+48.0 | +17.7/+19.6 | -23.0/-11.4 | 2052 / -167932 (+2946004/-3113936) | +145059/-94801/-190489/-27702 | 0.01 / 0.45 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win5_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+45.0/+7.5/+12.9/+14.9 | +1672 | +32.6/+32.6/+48.0 | +17.7/+19.6 | -23.1/-11.4 | 2057 / -167484 (+2955584/-3123068) | +145059/-91941/-192901/-27702 | 0.01 / 0.46 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win3_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+60.1/+7.5/+12.9/+14.9 | -315 | +27.9/+27.9/+59.7 | +12.0/+14.0 | -24.1/-5.3 | 2202 / -118223 (+3318877/-3437099) | +143211/-60801/-172932/-27702 | 0.01 / 0.47 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win4_loss1(arm2,keep.5,floor12) | ALL | +25.6/+25.6/+66.3/+13.6/+11.0/+16.1 | -1497 | +21.6/+21.6/+64.4 | +6.2/+11.5 | -24.2/-7.5 | 4394 / -118844 (+4420894/-4539738) | +167270/-63531/-176726/-45857 | 0.06 / 0.73 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -11%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win5_loss1(arm2,keep.5,floor12) | ALL | +25.6/+25.6/+60.2/+13.6/+10.6/+16.1 | -1439 | +21.8/+21.8/+58.2 | +6.0/+11.7 | -23.1/-8.0 | 4255 / -106687 (+4261297/-4367983) | +184525/-40302/-190656/-60254 | 0.08 / 0.78 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -11%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |


## Give-back (arm R x keep)

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_giveback | arm1_keep0.7(win5,loss2,floor12) | P7 | +6.9/+6.9/+55.5/+22.8/+30.0/-0.3 | +1823 | +12.4/+12.4/+58.1 | +34.1/+5.6 | -24.9/-20.0 | 1810 / -287060 (+2364608/-2651668) | -29272/-52294/-177792/-27702 | 0.03 / 0.98 | +38.9 / -2067 / 57% | OK-PRIOR (allow 15%, deeper -30%) | LEAD-RECENT (bi-weekly WF 57% < 60) |
| pb_giveback | arm1_keep0.6(win5,loss2,floor12) | P7 | +6.9/+6.9/+45.6/+20.5/+30.0/-0.3 | +282 | +7.8/+7.8/+46.1 | +30.7/+0.7 | -18.3/-12.8 | 1734 / -232842 (+2238940/-2471782) | -5156/-23797/-176187/-27702 | 0.07 / 1.00 | +38.9 / -2067 / 57% | OK-PRIOR (allow 15%, deeper -30%) | LEAD-RECENT (bi-weekly WF 57% < 60) |
| pb_giveback | arm1_keep0.8(win5,loss2,floor12) | P7 | +11.0/+11.0/+57.4/+22.8/+34.8/-6.8 | -3526 | -1.2/-1.2/+51.5 | +25.8/-21.5 | -17.1/-5.0 | 1931 / -161387 (+2705344/-2866731) | -18840/+7263/-122108/-27702 | 0.09 / 1.00 | +38.9 / -2067 / 57% | OK-PRIOR (allow 15%, deeper -35%) | no |
| pb_giveback | arm1_keep0.3(win5,loss2,floor12) | P7 | -0.8/+3.0/+37.4/+16.5/+27.2/-0.3 | +320 | +0.3/+4.0/+38.1 | +28.0/+0.8 | -8.2/-7.1 | 1441 / -157465 (+1639138/-1796603) | -6448/+22844/-146159/-27702 | 0.10 / 1.00 | +38.9 / -2067 / 57% | OK-PRIOR (allow 15%, deeper -27%) | no |
| pb_giveback | arm1_keep0.8(win5,loss2,floor12) | ALL | +13.3/+13.3/+51.6/+23.9/+38.9/-6.5 | -4599 | -2.9/-2.9/+42.5 | +27.5/-26.4 | +1.2/-4.6 | 3446 / -144325 (+3567381/-3711706) | +1611/-10364/-143263/+7690 | 0.21 / 1.00 | +38.9 / -2067 / 57% | OK-PRIOR (allow 15%, deeper -39%) | no |
| pb_giveback | arm1_keep0.5(win5,loss2,floor12) | P7 | -3.5/+6.9/+45.6/+16.9/+30.0/-0.3 | -1169 | -7.8/+3.0/+43.3 | +27.1/-4.5 | -9.1/-6.8 | 1629 / -201780 (+2014806/-2216586) | +22407/-39367/-157119/-27702 | 0.21 / 1.00 | +38.9 / -2067 / 57% | OK-PRIOR (allow 15%, deeper -30%) | no |
| pb_giveback | arm1_keep0.3(win5,loss2,floor12) | ALL | -3.0/+3.0/+33.7/+17.3/+30.0/+0.5 | -370 | -4.3/+1.7/+32.9 | +29.1/-0.8 | -1.4/-6.7 | 1937 / -152115 (+1919317/-2071432) | -9326/-3744/-139814/+769 | 0.12 / 1.00 | +38.9 / -2067 / 57% | OK-PRIOR (allow 15%, deeper -30%) | no |
| pb_giveback | arm2_keep0.7(win5,loss2,floor12) | P7 | -0.3/+3.0/+10.2/-0.6/-0.0/+8.1 | +479 | +1.3/+4.6/+11.7 | +1.6/+9.6 | -19.9/-0.0 | 1231 / -188678 (+1143741/-1332419) | -24028/-28245/-108703/-27702 | 0.12 / 1.00 | +38.9 / -2067 / 57% | OK-PRIOR (allow 15%, deeper +0%) | no |


## Week floor

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_weekfloor | floor6(win5,loss2,arm2/.5) | ALL | -2.6/+5.7/+6.0/+17.6/+9.9/+7.1 | -521 | -4.5/+4.0/+4.2 | +8.2/+5.5 | -11.1/+3.1 | 1382 / -201649 (+1318167/-1519816) | +19351/-47772/-148725/-24504 | 0.19 / 1.00 | +9.9 / -2164 / 41% | OK-PRIOR (allow 15%, deeper -10%) | no |
| pb_weekfloor | floor6(win5,loss2,arm2/.5) | P7 | -2.6/+3.0/+6.0/+17.2/+9.9/+8.1 | -666 | -5.0/+0.7/+3.8 | +7.8/+6.0 | -10.7/+4.0 | 1278 / -198418 (+1256909/-1455327) | +11401/-42284/-139833/-27702 | 0.25 / 1.00 | +9.9 / -2164 / 41% | OK-PRIOR (allow 15%, deeper -10%) | no |
| pb_weekfloor | floor10(win5,loss2,arm2/.5) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | 0.20 / 1.00 | +9.9 / -2164 / 41% | OK-PRIOR (allow 15%, deeper +0%) | no |
| pb_weekfloor | floor8(win5,loss2,arm2/.5) | ALL | -5.2/+3.0/+6.0/+6.4/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1189 / -179294 (+1058584/-1237878) | -6542/-5539/-137197/-30015 | 0.28 / 1.00 | +9.9 / -2164 / 41% | OK-PRIOR (allow 15%, deeper +0%) | no |
| pb_weekfloor | floor14(win5,loss2,arm2/.5) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | 0.17 / 1.00 | +9.9 / -2164 / 41% | OK-PRIOR (allow 15%, deeper +0%) | no |
| pb_weekfloor | floor16(win5,loss2,arm2/.5) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | 0.26 / 1.00 | +9.9 / -2164 / 41% | OK-PRIOR (allow 15%, deeper +0%) | no |
| pb_weekfloor | floor20(win5,loss2,arm2/.5) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | 0.32 / 1.00 | +9.9 / -2164 / 41% | OK-PRIOR (allow 15%, deeper +0%) | no |
| pb_weekfloor | floor12(win5,loss2,arm2/.5) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | 0.24 / 1.00 | +9.9 / -2164 / 41% | OK-PRIOR (allow 15%, deeper +0%) | no |


## Lock R on base vs sized lots

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_rbasis | R_on_sized_lots | P7 | +38.5/+38.5/+68.7/-26.6/+36.1/+14.7 | +4488 | +46.7/+46.7/+72.9 | +44.6/+26.0 | -33.8/-32.4 | 2606 / -220754 (+4151936/-4372689) | +120445/-112727/-200770/-27702 | 0.01 / 0.08 | +28.3 / -2118 / 72% | OK-PRIOR (allow 25%, deeper -36%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_rbasis | R_on_sized_lots | ALL | +37.6/+37.6/+67.8/-1.1/+40.8/+30.8 | +1751 | +41.1/+41.1/+69.6 | +44.2/+34.7 | -17.3/-32.2 | 5372 / -221650 (+5736531/-5958181) | +115940/-89130/-228335/-20124 | 0.01 / 0.15 | +28.3 / -2118 / 72% | OK-PRIOR (allow 25%, deeper -41%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_rbasis | R_on_base_lots | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | 0.25 / 1.00 | +28.3 / -2118 / 72% | OK-PRIOR (allow 15%, deeper +0%) | no |
| pb_rbasis | R_on_base_lots | P7 | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | 0.29 / 1.00 | +28.3 / -2118 / 72% | OK-PRIOR (allow 15%, deeper +0%) | no |
| pb_rbasis | R_on_base_lots | K7 | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | 0.26 / 1.00 | +28.3 / -2118 / 72% | OK-PRIOR (allow 15%, deeper +0%) | no |
| pb_rbasis | R_on_sized_lots | K7 | -0.5/-0.5/+16.8/+1.0/+11.5/+16.0 | -2156 | -8.5/-8.5/+10.1 | +4.4/+9.3 | -2.3/+5.5 | 3289 / -181584 (+2256763/-2438347) | -9277/-13065/-139118/-20124 | 0.32 / 1.00 | +28.3 / -2118 / 72% | OK-PRIOR (allow 15%, deeper -11%) | no |


## Intraday re-arm vs rest-of-day

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_rearm | resume_after_4h | P7 | -19.1/+3.0/+27.0/-5.9/-0.9/+2.9 | +335 | -17.8/+4.1/+27.9 | +0.2/+4.0 | -0.8/+1.6 | 1109 / -138853 (+930311/-1069164) | -13727/+2134/-99558/-27702 | 0.23 / 1.00 | +1.2 / -2391 / 39% | OK-PRIOR (allow 15%, deeper +1%) | no |
| pb_rearm | resume_after_next_session | K7 | -9.4/+3.0/+4.3/-2.1/+2.7/+8.9 | -851 | -12.7/+0.1/+1.4 | -0.2/+6.2 | -6.7/+5.5 | 914 / -178590 (+896234/-1074824) | -7741/-11715/-126063/-33071 | 0.38 / 1.00 | +1.2 / -2391 / 39% | OK-PRIOR (allow 15%, deeper -3%) | no |
| pb_rearm | resume_after_2h | P7 | -8.4/+3.0/+6.2/+2.5/-10.2/+8.5 | -1247 | -13.2/-1.3/+2.1 | -15.1/+4.4 | -7.6/+11.6 | 1056 / -113424 (+835499/-948923) | -1880/+9333/-93175/-27702 | 0.29 / 1.00 | +1.2 / -2391 / 39% | OK-PRIOR (allow 15%, deeper +10%) | no |
| pb_rearm | resume_after_8h | K7 | -8.7/+2.4/+3.0/+2.2/+1.2/+9.4 | -1505 | -14.6/-2.9/-2.3 | -4.1/+4.5 | -5.2/+7.9 | 1242 / -143840 (+1108461/-1252302) | +7378/-16303/-121962/-12953 | 0.35 / 1.00 | +1.2 / -2391 / 39% | OK-PRIOR (allow 15%, deeper -1%) | no |
| pb_rearm | resume_after_4h | ALL | -25.1/+5.4/+19.7/-0.5/-2.5/+6.4 | -466 | -27.1/+3.9/+18.4 | -4.2/+4.9 | +3.8/+4.8 | 998 / -122368 (+878958/-1001326) | -6739/+3449/-98533/-20546 | 0.36 / 1.00 | +1.2 / -2391 / 39% | OK-PRIOR (allow 15%, deeper +3%) | no |
| pb_rearm | resume_after_8h | P7 | -7.1/+2.4/+2.3/+6.1/-1.5/+8.1 | -2439 | -16.9/-6.5/-6.6 | -10.7/-0.3 | +2.5/+12.6 | 1191 / -135003 (+1094036/-1229039) | -30124/+6142/-83319/-27702 | 0.38 / 1.00 | +1.2 / -2391 / 39% | OK-PRIOR (allow 15%, deeper +1%) | no |
| pb_rearm | resume_after_2h | K7 | -17.3/+3.0/+14.3/-3.4/+0.6/+9.0 | -1870 | -25.3/-3.7/+8.4 | -6.2/+2.8 | -2.3/+10.0 | 925 / -136830 (+922115/-1058945) | -2583/-13116/-113693/-7438 | 0.48 / 1.00 | +1.2 / -2391 / 39% | OK-PRIOR (allow 15%, deeper -1%) | no |
| pb_rearm | resume_after_4h | K7 | -11.2/-0.4/-0.5/+6.3/-3.4/+10.7 | -1771 | -18.4/-6.9/-7.0 | -10.1/+5.0 | -5.7/+10.2 | 1078 / -149054 (+1003640/-1152694) | -1430/-6510/-120568/-20546 | 0.51 / 1.00 | +1.2 / -2391 / 39% | OK-PRIOR (allow 15%, deeper +3%) | no |


## Losing-streak halts (N stops -> off N hours)

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| streak_halt | 3stops_off_8h(+live) | ALL | -5.2/+0.8/+13.0/-3.0/+1.5/+8.1 | +616 | -3.0/+2.8/+14.8 | +3.5/+10.0 | -5.1/-1.1 | 1446 / -119245 (+1280343/-1399589) | +16027/+14291/-113300/-36264 | na | na / na / nan% | OK-PRIOR-UNKNOWN-WF (allow 15%, deeper -2%) | reference row |
| streak_halt | 2stops_off_2h(+live) | K7 | -1.2/-1.2/-0.7/-0.5/+8.0/+12.6 | -207 | -2.0/-2.0/-1.4 | +7.3/+11.9 | -5.4/+2.6 | 1477 / -171720 (+1230465/-1402185) | -10653/-2726/-131009/-27332 | na | na / na / nan% | OK-PRIOR-UNKNOWN-WF (allow 15%, deeper -8%) | reference row |
| streak_halt | 2stops_off_1h(+live) | K7 | +0.4/+0.4/+0.3/-1.5/+10.1/+12.8 | -835 | -2.5/-2.5/-2.6 | +7.5/+10.2 | -8.0/+4.5 | 1433 / -161539 (+1204448/-1365987) | -670/-15569/-134532/-10768 | na | na / na / nan% | OK-PRIOR-UNKNOWN-WF (allow 15%, deeper -10%) | reference row |
| streak_halt | 2stops_off_1h(+live) | P7 | -5.2/+3.0/+10.3/-0.6/+2.3/+0.7 | -830 | -8.3/+0.2/+7.6 | -0.6/-2.2 | -12.4/+5.2 | 1200 / -160571 (+1111188/-1271759) | -12894/+20495/-140471/-27702 | na | na / na / nan% | OK-PRIOR-UNKNOWN-WF (allow 15%, deeper -2%) | reference row |
| streak_halt | 3stops_off_1h(+live) | K7 | -5.2/+4.1/+4.5/-0.6/-1.4/+9.1 | -596 | -7.4/+2.1/+2.5 | -3.6/+7.2 | -10.5/+4.4 | 1231 / -171634 (+1078356/-1249990) | -3184/-14789/-127989/-25672 | na | na / na / nan% | OK-PRIOR-UNKNOWN-WF (allow 15%, deeper +1%) | reference row |
| streak_halt | 3stops_off_8h(+live) | K7 | -5.2/+3.8/+8.2/-0.6/-5.8/+11.8 | -864 | -8.4/+0.9/+5.4 | -9.0/+9.1 | -12.5/+6.1 | 1389 / -179125 (+1173087/-1352211) | -19169/-12359/-111332/-36264 | na | na / na / nan% | OK-PRIOR-UNKNOWN-WF (allow 15%, deeper +6%) | reference row |
| streak_halt | 3stops_off_2h(+live) | K7 | -5.2/+4.1/+4.5/-0.6/-2.8/+13.5 | -687 | -7.7/+1.8/+2.2 | -5.3/+11.4 | -10.5/+5.4 | 1251 / -190690 (+1081224/-1271913) | -3944/-12401/-137933/-36411 | na | na / na / nan% | OK-PRIOR-UNKNOWN-WF (allow 15%, deeper +3%) | reference row |
| streak_halt | 3stops_off_1h(+live) | P7 | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -683 | -7.7/+0.7/+3.7 | -2.4/+5.9 | -9.9/+5.3 | 1179 / -172937 (+1048999/-1221936) | -6854/-11744/-126636/-27702 | na | na / na / nan% | OK-PRIOR-UNKNOWN-WF (allow 15%, deeper +0%) | reference row |


## Combos

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_combo | win3_loss1_arm1_keep0.5_floor8 | P7 | +32.6/+32.6/+83.3/+7.5/+38.7/+6.6 | -3225 | +24.2/+24.2/+81.2 | +31.0/-5.0 | -19.1/-5.0 | 2597 / -111240 (+4173208/-4284448) | +182664/-110527/-155675/-27702 | 0.03 / 0.46 | +27.9 / -2695 / 69% | OK-PRIOR (allow 25%, deeper -39%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_combo | win3_loss1_arm1_keep0.5_floor8 | ALL | +11.9/+28.9/+84.7/+15.4/+48.6/+8.7 | -7700 | -19.7/+3.4/+79.3 | +30.1/-23.9 | -13.0/+6.2 | 5730 / -31027 (+6025046/-6056073) | +229428/-78973/-155272/-26210 | 0.25 / 1.00 | +27.9 / -2695 / 69% | OK-PRIOR (allow 22%, deeper -49%) | no |
| pb_combo | win4_loss1.5_arm1.5_keep0.5_floor10 | P7 | +6.0/+6.0/+13.5/-0.3/+34.3/+6.4 | -167 | +5.5/+5.5/+13.0 | +33.9/+5.8 | -4.1/-3.0 | 1690 / -117259 (+2166556/-2283815) | +44328/-64378/-69507/-27702 | 0.13 / 1.00 | +27.9 / -2695 / 69% | OK-PRIOR (allow 16%, deeper -34%) | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_combo | win6_loss3_arm2_keep0.5_floor14 | ALL | +3.1/+12.9/+12.8/-15.2/-16.8/+10.2 | -976 | -0.3/+9.8/+9.7 | -20.9/+7.1 | -5.1/+12.7 | 471 / -102964 (+442188/-545152) | +1131/+34335/-110596/-27835 | 0.04 / 1.00 | +27.9 / -2695 / 69% | RECENT-ONLY (allow 15%, deeper +17%) | no |
| pb_combo | win5_loss2_arm2_keep0.7_floor12 | P7 | -0.3/+3.0/+10.2/-0.6/-0.0/+8.1 | +479 | +1.3/+4.6/+11.7 | +1.6/+9.6 | -19.9/-0.0 | 1231 / -188678 (+1143741/-1332419) | -24028/-28245/-108703/-27702 | 0.14 / 1.00 | +27.9 / -2695 / 69% | OK-PRIOR (allow 15%, deeper +0%) | no |
| pb_combo | win6_loss3_arm2_keep0.5_floor14 | P7 | +3.1/+12.0/+11.9/-21.2/-14.0/+6.6 | -1388 | -1.7/+7.7/+7.6 | -19.7/+1.9 | -9.1/+13.4 | 1004 / -79496 (+752811/-832307) | +8078/+42608/-102480/-27702 | 0.09 / 1.00 | +27.9 / -2695 / 69% | OK-PRIOR (allow 15%, deeper +14%) | no |
| pb_combo | win5_loss2_arm2_keep0.7_floor12 | ALL | +1.8/+1.8/+1.7/+0.2/+0.9/+8.1 | +161 | +2.4/+2.4/+2.3 | +1.5/+8.6 | -18.9/+0.9 | 1443 / -179559 (+1269941/-1449500) | -22257/-26897/-104092/-26313 | 0.14 / 1.00 | +27.9 / -2695 / 69% | OK-PRIOR (allow 15%, deeper -1%) | no |
| pb_combo | win3_loss1.5_arm1.5_keep0.5_floor8 | P7 | +6.0/+6.0/+28.6/+4.3/+30.9/+6.4 | -2787 | -3.9/-3.9/+21.1 | +23.6/-3.5 | +3.1/+6.6 | 1789 / -39904 (+2443484/-2483388) | +59038/-8729/-62512/-27702 | 0.19 / 1.00 | +27.9 / -2695 / 69% | OK-PRIOR (allow 16%, deeper -31%) | no |


## Quit-when-up: stack day win cap (+live pb)

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| comb_quit_up | stack_win$40000(+live pb) | ALL | -5.2/+3.0/+27.7/-0.6/-0.0/+8.1 | -858 | -8.4/+0.1/+25.5 | -3.0/+5.3 | -15.1/+6.0 | 1638 / -152021 (+1501562/-1653583) | -17269/-20721/-117640/+3609 | 0.20 / 1.00 | +22.1 / -2763 / 49% | OK-PRIOR (allow 15%, deeper +0%) | no |
| comb_quit_up | stack_win$90000(+live pb) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | 0.19 / 1.00 | +22.1 / -2763 / 49% | OK-PRIOR (allow 15%, deeper +0%) | no |
| comb_quit_up | stack_win$60000(+live pb) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -895 | -8.5/-0.1/+3.0 | -3.2/+5.2 | -9.1/+6.1 | 1210 / -174678 (+1081506/-1256184) | -7741/-18995/-126257/-21684 | 0.14 / 1.00 | +22.1 / -2763 / 49% | OK-PRIOR (allow 15%, deeper +0%) | no |
| comb_quit_up | stack_win$25000(+live pb) | ALL | -5.2/+9.8/+9.7/-0.6/+26.6/+8.1 | -3733 | -20.6/-3.4/-3.5 | +15.9/-5.4 | -28.1/+10.1 | 3069 / +1109 (+3034987/-3033878) | +21343/-18887/-20004/+18657 | 0.49 / 1.00 | +22.1 / -2763 / 49% | RECENT-ONLY (allow 15%, deeper -27%) | no |
| comb_quit_up | stack_win$15000(+live pb) | ALL | -36.7/-36.7/-36.9/-9.8/+39.3/+16.9 | -7378 | -82.9/-82.9/-83.1 | +18.8/-11.2 | +18.6/+12.6 | 5608 / +30637 (+5659548/-5628910) | +48618/+32544/-87179/+36655 | 0.91 / 1.00 | +22.1 / -2763 / 49% | OK-PRIOR (allow 15%, deeper -39%) | no |


## Stack day loss cap (+live pb)

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| comb_dayloss | stack_loss$15000(+live pb) | ALL | -3.1/-3.1/+53.5/+4.9/-4.7/-5.1 | +262 | -2.2/-2.2/+53.9 | -3.7/-4.2 | -8.3/-4.5 | 3655 / -179903 (+3346364/-3526267) | +158374/-78700/-215449/-44128 | 0.24 / 1.00 | -18.5 / -1958 / 65% | OK-PRIOR (allow 15%, deeper +5%) | no |
| comb_dayloss | stack_loss$25000(+live pb) | ALL | -2.4/-2.4/+21.0/+3.2/-0.1/+9.9 | +2008 | +4.2/+4.2/+26.1 | +6.3/+15.7 | -5.4/-3.0 | 1638 / -222397 (+1359205/-1581602) | -7145/-21595/-145886/-47772 | 0.14 / 1.00 | -18.5 / -1958 / 65% | OK-PRIOR (allow 15%, deeper +0%) | no |
| comb_dayloss | stack_loss$8000(+live pb) | ALL | +12.2/+12.2/+99.0/+25.6/-25.2/-27.9 | -8984 | -26.8/-26.8/+98.6 | -80.8/-84.8 | +41.0/+19.2 | 7489 / +207398 (+7545288/-7337890) | +443669/+74564/-274137/-36699 | 0.36 / 1.00 | -18.5 / -1958 / 65% | RECENT-ONLY (allow 22%, deeper +25%) | no |
| comb_dayloss | stack_loss$40000(+live pb) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1186 / -169020 (+1054993/-1224014) | -7741/-7826/-126943/-26510 | 0.20 / 1.00 | -18.5 / -1958 / 65% | OK-PRIOR (allow 15%, deeper +0%) | no |


## Stack give-back (+live pb)

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| comb_giveback | stack_arm$45000_keep0.5(+live pb) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | 0.23 / 1.00 | +24.5 / -3352 / 49% | OK-PRIOR (allow 15%, deeper +0%) | no |
| comb_giveback | stack_arm$30000_keep0.5(+live pb) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -9.6/+5.6 | 1204 / -174846 (+1062781/-1237627) | -7741/-7826/-126792/-32487 | 0.34 / 1.00 | +24.5 / -3352 / 49% | OK-PRIOR (allow 15%, deeper +0%) | no |
| comb_giveback | stack_arm$45000_keep0.7(+live pb) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -1644 | -11.5/-2.8/+0.3 | -6.0/+2.6 | -4.5/+9.0 | 1240 / -147404 (+1116128/-1263532) | -7741/+8282/-121444/-26500 | 0.32 / 1.00 | +24.5 / -3352 / 49% | OK-PRIOR (allow 15%, deeper +0%) | no |
| comb_giveback | stack_arm$30000_keep0.7(+live pb) | ALL | -5.2/+3.0/+10.2/-0.6/-0.0/+8.1 | -3309 | -18.6/-9.4/-1.2 | -12.8/-3.6 | -16.2/+16.0 | 1397 / -105832 (+1272586/-1378418) | -7741/+28439/-108495/-18035 | 0.48 / 1.00 | +24.5 / -3352 / 49% | OK-PRIOR (allow 15%, deeper +0%) | no |
| comb_giveback | stack_arm$20000_keep0.5(+live pb) | ALL | -5.2/+3.0/+3.3/+12.8/+32.8/+8.1 | -3707 | -20.5/-11.1/-10.8 | +23.0/-5.3 | +0.2/+8.7 | 1789 / -147246 (+1612802/-1760048) | +19191/+2069/-148847/-19658 | 0.56 / 1.00 | +24.5 / -3352 / 49% | OK-PRIOR (allow 15%, deeper -33%) | no |
| comb_giveback | stack_arm$20000_keep0.7(+live pb) | ALL | -5.2/+3.0/+11.3/+15.5/+35.8/+5.3 | -7157 | -39.4/-28.5/-17.5 | +15.0/-25.4 | -11.0/+20.6 | 2361 / -136656 (+2192540/-2329196) | -24355/+12204/-140441/+15936 | 0.73 / 1.00 | +24.5 / -3352 / 49% | OK-PRIOR (allow 15%, deeper -36%) | no |
| comb_giveback | stack_arm$10000_keep0.7(+live pb) | ALL | -32.6/-32.6/-32.7/-6.5/+35.8/+16.5 | -6773 | -72.6/-72.6/-72.8 | +16.5/-8.8 | -4.8/+4.0 | 5187 / -139197 (+4956754/-5095951) | +45090/-64131/-121823/+1667 | 0.87 / 1.00 | +24.5 / -3352 / 49% | OK-PRIOR (allow 15%, deeper -36%) | no |
| comb_giveback | stack_arm$10000_keep0.5(+live pb) | ALL | -35.6/-35.6/-35.7/-10.1/+32.5/+16.4 | -8398 | -90.3/-90.3/-90.5 | +5.2/-17.3 | +11.6/+17.8 | 4227 / -77438 (+4029102/-4106540) | +78525/-19842/-107543/-28578 | 0.97 / 1.00 | +24.5 / -3352 / 49% | OK-PRIOR (allow 15%, deeper -32%) | no |


## Stack week floor (+live pb)

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| comb_weekfloor | stack_floor$30000(+live pb) | ALL | +21.7/+21.7/+21.6/+19.5/+19.9/-7.2 | -1609 | +17.1/+17.1/+17.0 | +15.3/-13.4 | +7.2/-13.5 | 4187 / -177663 (+4262387/-4440050) | +133506/-110625/-176706/-23837 | 0.07 / 1.00 | +0.0 / -3283 / 46% | OK-PRIOR (allow 15%, deeper -20%) | LEAD-RECENT (bi-weekly WF 46% < 60) |
| comb_weekfloor | stack_floor$100000(+live pb) | ALL | -5.2/+3.0/+6.0/+0.5/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1229 / -170984 (+1101154/-1272137) | +3415/-15448/-133652/-25299 | 0.31 / 1.00 | +0.0 / -3283 / 46% | OK-PRIOR (allow 15%, deeper +0%) | no |
| comb_weekfloor | stack_floor$60000(+live pb) | ALL | -9.6/-9.6/-9.7/+12.0/+22.0/+8.1 | -559 | -11.7/-11.7/-11.9 | +20.4/+6.3 | -11.4/-0.4 | 1819 / -227524 (+1709765/-1937289) | +8857/-72085/-145710/-18585 | 0.28 / 1.00 | +0.0 / -3283 / 46% | OK-PRIOR (allow 15%, deeper -22%) | no |


## REFIT 2026-11-22: what the bi-weekly procedure picks today (trailing 26 weeks to 2026-10-30, DD-first picker over the whole R1 grid, reference = live locks)

Pick: **R1;pb_rbasis;R_on_sized_lots;P7** (live retained: False; train end 2026-11-05). Bi-weekly WF over the whole grid: OOS maxDD cut +14.7%, d mean -2078 $/wk, beats live in 70% of 74 refit periods.


> STANDING RULES 2/2a: ranking = 0.5 L6M + 0.3 L3M + 0.2 L1M equal-mean cut (recents first); bi-weekly WF (sz_core) is the primary OOS column; PRE/X' tolerant via sz_core.prior_info; materiality floor L6M cut >= 5%. The exact top-5 sets were frozen before these rules (ranking by min of L6M/PRE/X').


## Exact-engine rows (S1b engine, ROLL-EXCL scoring; windows complete only): live, NOLOCK reference, R1 top-5

| row | set | L6M maxDD / d mean / cut vs live | PRE maxDD / d mean / cut vs live | X' maxDD / d mean / cut vs live | HOLD maxDD / d mean / cut vs live |
|--|--|--|--|--|--|
| LIVE (S1-COMB) | S1-COMB | 79907 / +0 / +0.0% [ROLL-FIXED] | 140288 / +0 / +0.0% [ROLL-FIXED] | 137520 / +0 / +0.0% [ROLL-FIXED] | 99496 / +0 / +0.0% [ROLL-FIXED] |
| NOLOCK reference | CDE_NOLOCK | 100720 / -2521 / -26.0% [ROLL-FIXED] | 162725 / -795 / -16.0% [ROLL-FIXED] | 124998 / +480 / +9.1% [ROLL-FIXED] | 116421 / -1132 / -17.0% [ROLL-FIXED] |
| R1/pb_rbasis/R_on_sized_lots/ALL | CDE_R1_1 | 53773 / -8025 / +32.7% [ROLL-FIXED] | 65905 / +81 / +53.0% [ROLL-FIXED] | 126784 / -1464 / +7.8% [ROLL-FIXED] | 80084 / -6718 / +19.5% [ROLL-FIXED] |
| R1/pb_rbasis/R_on_sized_lots/P7 | CDE_R1_2 | 66329 / -5089 / +17.0% [ROLL-FIXED] | 72057 / +269 / +48.6% [ROLL-FIXED] | 136075 / -2168 / +1.1% [ROLL-FIXED] | 118530 / -6309 / -19.1% [ROLL-FIXED] |
| R1/pb_daycaps/win4_loss1(arm2,keep.5,floor12)/P7 | CDE_R1_3 | 59357 / +492 / +25.7% [ROLL-FIXED] | 116454 / +1108 / +17.0% [ROLL-FIXED] | 129643 / -1076 / +5.7% [ROLL-FIXED] | 92001 / +242 / +7.5% [ROLL-FIXED] |
| R1/pb_daycaps/win8_loss1(arm2,keep.5,floor12)/P7 | CDE_R1_4 | 59357 / +66 / +25.7% [ROLL-FIXED] | 116454 / +917 / +17.0% [ROLL-FIXED] | 129643 / -1076 / +5.7% [ROLL-FIXED] | 92001 / -8 / +7.5% [ROLL-FIXED] |
| R1/pb_giveback/arm1_keep0.7(win5,loss2,floor12)/P7 | CDE_R1_5 | 77439 / -5048 / +3.1% [ROLL-FIXED] | 99383 / +81 / +29.2% [ROLL-FIXED] | 68550 / +1608 / +50.2% [ROLL-FIXED] | 86135 / -5555 / +13.4% [ROLL-FIXED] |


NOLOCK reference: the live locks are doing real work; any setting that removes them is a reference row, never a candidate.


## Summary block: setting | live value | best on the state base | holds OOS? | change recommended | panel field

| setting | live value | best on the state base (first-order screen, equal mean) | holds OOS (dim WF eq cut) | change recommended | panel field |
|--|--|--|--|--|--|
| Day profit / loss caps | +5R / -2R per book | win4_loss1(arm2,keep.5,floor12) P7 (cut +33.7/+19.1/+20.9, d mean +2211) | -10.0 | candidate for exact; live stays until exact confirms | ComboLimits / MaxDayProfit, MaxDayLoss (per book) |
| Give-back arm / keep | arm 2R keep 50% | arm1_keep0.7(win5,loss2,floor12) P7 (cut +12.4/+34.1/+5.6, d mean +1823) | +20.5 | candidate for exact; live stays until exact confirms | GiveBackArmR / GiveBackKeepPct |
| Week floor | 12R per book | floor6(win5,loss2,arm2/.5) ALL (cut -4.5/+8.2/+5.5, d mean -521) | -2.5 | no (live stays) | ComboWeekFloorR |
| R basis | base lots | R_on_sized_lots P7 (cut +46.7/+44.6/+26.0, d mean +4488) | -5.2 | candidate for exact; live stays until exact confirms | v1.6 (R on sized lots not a field) |
| Halt scope in time | rest of day | resume_after_4h P7 (cut -17.8/+0.2/+4.0, d mean +335) | -20.4 | no (live stays) | v1.6 code (re-arm after N h / next session) |
| Stack quit-when-up | none (PerBook only) | stack_win$40000(+live pb) ALL (cut -8.4/-3.0/+5.3, d mean -858) | -22.4 | no (live stays) | v1.6 code (LockScope Combined $ cap) |
| Stack day loss cap | none | stack_loss$15000(+live pb) ALL (cut -2.2/-3.7/-4.2, d mean +262) | -47.1 | no (live stays) | v1.6 code |
| Stack give-back | none | stack_arm$45000_keep0.5(+live pb) ALL (cut -7.9/-2.6/+5.7, d mean -746) | +10.7 | no (live stays) | v1.6 code |
| Stack week floor | none | stack_floor$30000(+live pb) ALL (cut +17.1/+15.3/-13.4, d mean -1609) | -7.0 | no (live stays) | v1.6 code |

WF of the picking procedure over the whole R1 grid: OOS maxDD cut +13.3% raw / -12.4% at equal mean (d mean -3797 $/wk, 148 weeks).


Worked examples (today's P7 -20,985 day halt and the K7 give-back halts): those are 2026-11-09 live trades, not in the frozen live file (ends 11-05) and not in the exact lists (end 2026-10); not reproducible here. The frozen-week and the 14 roll days: see the roll-day check below.


## Roll-day check (14 roll days; artifact = alive across the roll and exited by an artifact Target/Stop; ROLL-EXCL zeroes their P&L in all scores but the engine state in the exact runs saw them)

| run | artifact trades present | artifact trades with a large loss (<= -1R of the book) | same-book trades that followed on that label day | BookLock exits among them |
|--|--|--|--|--|
| S1-COMB live | 31 | 3 | 121 | 0 |
| CDE_NOLOCK | 27 | 0 | 149 | 0 |
| CDE_R1_1 | 27 | 0 | 90 | 4 |
| CDE_R1_2 | 27 | 0 | 118 | 2 |
| CDE_R1_3 | 27 | 0 | 127 | 0 |
| CDE_R1_4 | 27 | 0 | 127 | 0 |
| CDE_R1_5 | 27 | 0 | 122 | 4 |

Detail (S1-COMB live): K7 20230614 pnl 1199 Target then 5 trades; P7 20230614 pnl 8402 Target then 0 trades; U7 20230614 pnl 2403 Target then 1 trades; P7 20230913 pnl -425 Stop then 4 trades; K7 20230913 pnl 1199 Target then 3 trades; A7 20231213 pnl 1199 Target then 0 trades; P7 20231213 pnl 1199 Target then 1 trades; K7 20231213 pnl 1199 Target then 2 trades; K7 20240313 pnl 1199 Target then 0 trades; P7 20240313 pnl 4805 Target then 0 trades; K7 20240619 pnl 1199 Target then 0 trades; A7 20240619 pnl 1199 Target then 0 trades; P7 20240918 pnl -3178 Stop then 3 trades; K7 20240918 pnl -386 Stop then 9 trades; K7 20241219 pnl 164 Stop then 16 trades; P7 20241219 pnl 178 Stop then 8 trades; K7 20250320 pnl 1199 Target then 9 trades; P7 20250320 pnl 3601 Target then 6 trades; P7 20250618 pnl 1362 Stop then 5 trades; K7 20250618 pnl 143 Stop then 9 trades; A7 20250618 pnl -276 Stop then 1 trades; A7 20250918 pnl 1199 Target then 2 trades; H7 20250918 pnl 1199 Target then 2 trades; P7 20250918 pnl 8392 Target then 0 trades; K7 20250918 pnl 1199 Target then 6 trades; K7 20251217 pnl -186 Stop then 9 trades; P7 20251217 pnl -4169 StateCut then 4 trades; P7 20260318 pnl -16785 Stop then 5 trades; K7 20260318 pnl -4406 Stop then 11 trades; K7 20260916 pnl -6061 Stop then 0 trades; P7 20260916 pnl 4800 Target then 0 trades

## R1_3 decision pack (P7 per-book daily loss cap -1R instead of -2R; exact engine rows; ROLL-EXCL)

### A. Exact numbers: stack (worst-20, Ulcer) and P7 alone, with (R1_3 / R1_4) vs without (live S1-COMB)

| window | row | stack maxDD | stack worst-20 | stack Ulcer | stack mean $/wk | P7-alone maxDD | P7-alone mean $/wk | P7 trades |
|--|--|--|--|--|--|--|--|--|
| L6M | live (S1-COMB) [ROLL-FIXED] | 79907 | 226711 | 31746 | 29090 | 91173 | 17611 | 1265 |
| L6M | R1_3 loss1R win4R [ROLL-FIXED] | 59357 | 281270 | 19552 | 29582 | 60908 | 18103 | 947 |
| L6M | R1_4 loss1R win8R [ROLL-FIXED] | 59357 | 277772 | 19552 | 29156 | 60908 | 17677 | 984 |
| PRE | live (S1-COMB) [ROLL-FIXED] | 140288 | -716998 | 39515 | 13636 | 101872 | 5822 | 1980 |
| PRE | R1_3 loss1R win4R [ROLL-FIXED] | 116454 | -645736 | 37863 | 14744 | 110528 | 6931 | 1647 |
| PRE | R1_4 loss1R win8R [ROLL-FIXED] | 116454 | -645736 | 37920 | 14553 | 110528 | 6740 | 1659 |
| X' | live (S1-COMB) [ROLL-FIXED] | 137520 | -348376 | 78096 | 2395 | 148676 | -510 | 698 |
| X' | R1_3 loss1R win4R [ROLL-FIXED] | 129643 | -353641 | 85770 | 1319 | 141195 | -1338 | 637 |
| X' | R1_4 loss1R win8R [ROLL-FIXED] | 129643 | -353641 | 85770 | 1319 | 141195 | -1338 | 637 |
| HOLD | live (S1-COMB) [ROLL-FIXED] | 99496 | -548674 | 33114 | 19942 | 91173 | 12182 | 2213 |
| HOLD | R1_3 loss1R win4R [ROLL-FIXED] | 92001 | -402068 | 27626 | 20184 | 60908 | 13109 | 1685 |
| HOLD | R1_4 loss1R win8R [ROLL-FIXED] | 92001 | -402068 | 27626 | 19934 | 60908 | 12859 | 1727 |

### B. P7 day halts at -1R vs -2R (replayed on the live ROLLFIX1 S1-COMB P7 trades: realized day P&L in exit order; R = 8,400 = 7 base lots x 60 pt x $20; followers = P7 trades signalled after the trigger on the same label day)

| window | cap | P7 days | halt days | followers n | followers net P&L | followers winners / losers P&L | by session of the follower (n / net P&L) | by session of the halting trade (days) |
|--|--|--|--|--|--|--|--|--|
| L6M | -1R | 131 | 51 | 286 | -19725 | +584459 / -604184 | asia 98 / +69367; london 118 / -69068; nyam 70 / -20024 | asia 35; london 11; nyam 5 |
| L6M | -2R | 131 | 19 | 0 | +0 | +0 / +0 |  | asia 7; london 4; nyam 8 |
| PRE | -1R | 364 | 118 | 320 | -40559 | +670776 / -711335 | asia 43 / +71770; london 144 / -40199; nyam 133 / -72130 | asia 44; london 47; nyam 27 |
| PRE | -2R | 364 | 32 | 0 | +0 | +0 / +0 |  | asia 3; london 16; nyam 13 |
| X' | -1R | 214 | 49 | 60 | +38170 | +151537 / -113366 | asia 1 / +8392; london 14 / -2440; nyam 45 / +32219 | asia 8; london 23; nyam 18 |
| X' | -2R | 214 | 7 | 0 | +0 | +0 / +0 |  | london 3; nyam 4 |
| HOLD | -1R | 258 | 97 | 491 | -29495 | +1044706 / -1074202 | asia 149 / +71892; london 214 / -58226; nyam 128 / -43161 | asia 63; london 23; nyam 11 |
| HOLD | -2R | 258 | 38 | 1 | -8313 | +0 / -8313 | london 1 / -8313 | asia 12; london 11; nyam 15 |

Reading: a NEGATIVE follower net P&L means the cap stops bleeding (the trades it removes lose); a POSITIVE one means it stops recovery. Live already halts at -2R, so the extra effect of -1R is the difference between the two cap rows (followers between the -1R and -2R triggers).

### C. Worked example on the frozen live week (11-01..11-05; the 2026-11-09 -20,985 P7 day halt is in the unfrozen live file and is NOT readable here)

| label day | P7 trades | day P&L | -1R trigger time (ET) | trades after the trigger (n / net P&L) | -2R trigger time (ET) |
|--|--|--|--|--|--|
| 20261102 | 10 | +24760 | none | 0 / +0 | none |
| 20261103 | 8 | +21160 | none | 0 / +0 | none |
| 20261104 | 19 | +9060 | 20:03:27 | 16 / +21185 | none |
| 20261105 | 16 | +31030 | none | 0 / +0 | none |

Reading: in the frozen week the -1R cap would have fired on P7 on label day 20261104 (about 20:03 ET) and removed the 16 later trades of that day, which made +21,185 (day finished +9,060): there it stops a recovery, not a bleed. Over L6M / PRE / HOLD (table B) the trades after a -1R touch net negative overall (stops bleeding: -19.7k / -35.5k / -35.1k) but positive in X-prime (+38.2k: stops a recovery), and split by session the Asia followers are positive (recovery) and London / NY-AM followers negative.


### D. Definition and panel line
The engine (and DS7 DAYCAP table: P7 +42,000 / -16,800 USD) defines the per-book daily loss cap as a fixed dollar amount = k R with R = BASE lots x 60 pt x $20 x max(1, day size multiplier): P7 base lots 7 -> 1R = $8,400; under Q1-A the size multiplier is never above 1, so R is on BASE lots, not on the lots actually traded (sized-lot R is the R1_1/R1_2 variant and is a different, riskier-to-implement setting). The check uses REALIZED day P&L only (closed trades), blocks new entries for the rest of the label day, and exits an open trade if any. Policy line: P7 daily max loss $16,800 (2R) -> $8,400 (1R), all other books and the P7 win cap (42,000 = 5R) unchanged. The exact panel field name for the per-book daily max loss is not documented in the files I can read (only ComboWeekFloorR / ComboGiveBackArmR / ComboGiveBackPct are named): to be confirmed against DS7.cs before any panel value is quoted.
