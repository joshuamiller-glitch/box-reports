# DS3_REDO_R1_LOCKS - T-STACK-REDO R1: locks on the state base (first version 2026-11-10 13:58Z)

> **FINAL DRAFT 2026-11-10 13:59Z: exact ROLL-FIXED rows (ROLLFIX1 engine, patched live reference), WF% beside every label, REFIT 2026-11-22 over all exact cells. Sections: R1 locks (grid, summary block, P7 -1R decision pack), R1b StackCut, L cooldowns, G candidates, joint lines for R1_3.**

> **Label: PRE-PROOF; post-hoc; Shadow only; no PASS claims. FIRST-ORDER SCREEN ONLY unless a row is in the exact table below. ROLL-EXCL: the 31 roll-artifact base trades are excluded from every number. STANDING RULE: every lock stays ON; "off" rows are reference rows only; the deliverable is the best SETTING (drawdown first at equal mean, holds OOS); if nothing beats the live setting the live setting stays.**

Method: the screen runs on the EXACT NOLOCK trade list (engine with the lock layer switched off, 33 window months; screen base = DIR:/mnt/l2/l2vast/_th_state/s345/exact_b/runs/CDE_NOLOCK) so any lock setting, tighter or looser than live, is replayed first-order (realized-only state: a lock triggers when a trade exits; the engine also marks open P&L and flattens, which the screen cannot see). Reference = the live setting = S1b-COMB exact list. Regression: the exact lock override with the live values reproduces S1-COMB 202605 trade for trade (672 trades, net 35,852). Day caps use realized P&L only (as live check_limits), give-back and week floor use realized + open P&L. R on base lots = planned lots x 60 pt x $20 (PE 8,400, KB/MV 2,400, HM/SM 4,800, PB/OD 1,200; x max(1, size mult)). Scope: PerBook = per-book values; stack ($) rows are Combined; "(+live pb)" = Combined on top of the live per-book locks. One-book scopes keep the live locks on the other books.

## Overall: top 15 settings by the joint equal-mean cut (min of L6M, PRE, X')

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_rbasis | R_on_sized_lots | P7 | +38.5/+38.5/+68.7/-26.6/+36.1/+14.7 | +4488 | +46.7/+46.7/+72.9 | +44.6/+26.0 | -33.8/-32.4 | 2606 / -220754 (+4151936/-4372689) | +120445/-112727/-200770/-27702 | 0.01 / 0.08 | +28.3 / -2118 / 72% | OK-PRIOR (allow 25%, deeper -36%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_rbasis | R_on_sized_lots | ALL | +37.6/+37.6/+67.8/-1.1/+40.8/+30.8 | +1751 | +41.1/+41.1/+69.6 | +44.2/+34.7 | -17.3/-32.2 | 5372 / -221650 (+5736531/-5958181) | +115940/-89130/-228335/-20124 | 0.01 / 0.15 | +28.3 / -2118 / 72% | OK-PRIOR (allow 25%, deeper -41%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win4_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+45.0/+7.5/+12.9/+14.9 | +2211 | +33.7/+33.7/+48.9 | +19.1/+20.9 | -25.2/-12.9 | 2107 / -197930 (+3050331/-3248261) | +128501/-116110/-182618/-27702 | 0.01 / 0.39 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win6_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+45.0/+7.5/+12.9/+14.9 | +1690 | +32.6/+32.6/+48.0 | +17.7/+19.6 | -23.0/-11.4 | 2052 / -167932 (+2946004/-3113936) | +145059/-94801/-190489/-27702 | 0.01 / 0.45 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win8_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+45.0/+7.5/+12.9/+14.9 | +1690 | +32.6/+32.6/+48.0 | +17.7/+19.6 | -23.0/-11.4 | 2052 / -167932 (+2946004/-3113936) | +145059/-94801/-190489/-27702 | 0.01 / 0.45 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win5_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+45.0/+7.5/+12.9/+14.9 | +1672 | +32.6/+32.6/+48.0 | +17.7/+19.6 | -23.1/-11.4 | 2057 / -167484 (+2955584/-3123068) | +145059/-91941/-192901/-27702 | 0.01 / 0.46 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_combo | win3_loss1_arm1_keep0.5_floor8 | P7 | +32.6/+32.6/+83.3/+7.5/+38.7/+6.6 | -3225 | +24.2/+24.2/+81.2 | +31.0/-5.0 | -19.1/-5.0 | 2597 / -111240 (+4173208/-4284448) | +182664/-110527/-155675/-27702 | 0.03 / 0.46 | +27.9 / -2695 / 69% | OK-PRIOR (allow 25%, deeper -39%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win3_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+60.1/+7.5/+12.9/+14.9 | -315 | +27.9/+27.9/+59.7 | +12.0/+14.0 | -24.1/-5.3 | 2202 / -118223 (+3318877/-3437099) | +143211/-60801/-172932/-27702 | 0.01 / 0.47 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win4_loss1(arm2,keep.5,floor12) | ALL | +25.6/+25.6/+66.3/+13.6/+11.0/+16.1 | -1497 | +21.6/+21.6/+64.4 | +6.2/+11.5 | -24.2/-7.5 | 4394 / -118844 (+4420894/-4539738) | +167270/-63531/-176726/-45857 | 0.06 / 0.73 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -11%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win5_loss1(arm2,keep.5,floor12) | ALL | +25.6/+25.6/+60.2/+13.6/+10.6/+16.1 | -1439 | +21.8/+21.8/+58.2 | +6.0/+11.7 | -23.1/-8.0 | 4255 / -106687 (+4261297/-4367983) | +184525/-40302/-190656/-60254 | 0.08 / 0.78 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -11%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win8_loss1(arm2,keep.5,floor12) | ALL | +25.6/+25.6/+60.2/+13.6/+10.6/+16.1 | -1502 | +21.6/+21.6/+58.1 | +5.8/+11.5 | -21.9/-8.0 | 4196 / -109352 (+4219368/-4328720) | +184525/-40426/-184688/-68763 | 0.04 / 0.78 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -11%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win6_loss1(arm2,keep.5,floor12) | ALL | +25.6/+25.6/+60.2/+13.6/+10.6/+16.1 | -1555 | +21.4/+21.4/+58.0 | +5.6/+11.3 | -21.6/-7.8 | 4206 / -108265 (+4226556/-4334821) | +184525/-40426/-184688/-67676 | 0.07 / 0.78 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -11%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win3_loss1(arm2,keep.5,floor12) | ALL | +25.6/+25.6/+74.7/+11.2/+9.5/+16.1 | -4487 | +12.1/+12.1/+70.1 | -7.0/+0.8 | -20.7/+4.4 | 4707 / -12218 (+4832509/-4844727) | +183733/-15328/-156613/-24010 | 0.08 / 0.94 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -9%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_giveback | arm1_keep0.7(win5,loss2,floor12) | P7 | +6.9/+6.9/+55.5/+22.8/+30.0/-0.3 | +1823 | +12.4/+12.4/+58.1 | +34.1/+5.6 | -24.9/-20.0 | 1810 / -287060 (+2364608/-2651668) | -29272/-52294/-177792/-27702 | 0.03 / 0.98 | +38.9 / -2067 / 57% | OK-PRIOR (allow 15%, deeper -30%) [old -1k rule: OK-PRIOR] | LEAD-RECENT (bi-weekly WF 57% < 60) |
| comb_weekfloor | stack_floor$30000(+live pb) | ALL | +21.7/+21.7/+21.6/+19.5/+19.9/-7.2 | -1609 | +17.1/+17.1/+17.0 | +15.3/-13.4 | +7.2/-13.5 | 4187 / -177663 (+4262387/-4440050) | +133506/-110625/-176706/-23837 | 0.07 / 1.00 | +0.0 / -3283 / 46% | OK-PRIOR (allow 15%, deeper -20%) [old -1k rule: OK-PRIOR] | LEAD-RECENT (bi-weekly WF 46% < 60) |


## Daily caps (win R x loss R)

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_daycaps | win4_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+45.0/+7.5/+12.9/+14.9 | +2211 | +33.7/+33.7/+48.9 | +19.1/+20.9 | -25.2/-12.9 | 2107 / -197930 (+3050331/-3248261) | +128501/-116110/-182618/-27702 | 0.01 / 0.39 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | winoff_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+45.0/+7.5/+12.9/+14.9 | +1690 | +32.6/+32.6/+48.0 | +17.7/+19.6 | -23.0/-11.4 | 2052 / -167932 (+2946004/-3113936) | +145059/-94801/-190489/-27702 | na | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) [old -1k rule: OK-PRIOR] | reference row |
| pb_daycaps | win8_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+45.0/+7.5/+12.9/+14.9 | +1690 | +32.6/+32.6/+48.0 | +17.7/+19.6 | -23.0/-11.4 | 2052 / -167932 (+2946004/-3113936) | +145059/-94801/-190489/-27702 | 0.01 / 0.45 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win6_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+45.0/+7.5/+12.9/+14.9 | +1690 | +32.6/+32.6/+48.0 | +17.7/+19.6 | -23.0/-11.4 | 2052 / -167932 (+2946004/-3113936) | +145059/-94801/-190489/-27702 | 0.01 / 0.45 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win5_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+45.0/+7.5/+12.9/+14.9 | +1672 | +32.6/+32.6/+48.0 | +17.7/+19.6 | -23.1/-11.4 | 2057 / -167484 (+2955584/-3123068) | +145059/-91941/-192901/-27702 | 0.01 / 0.46 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win3_loss1(arm2,keep.5,floor12) | P7 | +28.7/+28.7/+60.1/+7.5/+12.9/+14.9 | -315 | +27.9/+27.9/+59.7 | +12.0/+14.0 | -24.1/-5.3 | 2202 / -118223 (+3318877/-3437099) | +143211/-60801/-172932/-27702 | 0.01 / 0.47 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -13%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win4_loss1(arm2,keep.5,floor12) | ALL | +25.6/+25.6/+66.3/+13.6/+11.0/+16.1 | -1497 | +21.6/+21.6/+64.4 | +6.2/+11.5 | -24.2/-7.5 | 4394 / -118844 (+4420894/-4539738) | +167270/-63531/-176726/-45857 | 0.06 / 0.73 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -11%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_daycaps | win5_loss1(arm2,keep.5,floor12) | ALL | +25.6/+25.6/+60.2/+13.6/+10.6/+16.1 | -1439 | +21.8/+21.8/+58.2 | +6.0/+11.7 | -23.1/-8.0 | 4255 / -106687 (+4261297/-4367983) | +184525/-40302/-190656/-60254 | 0.08 / 0.78 | +11.5 / -3119 / 64% | OK-PRIOR (allow 25%, deeper -11%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |


## Give-back (arm R x keep)

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_giveback | arm1_keep0.7(win5,loss2,floor12) | P7 | +6.9/+6.9/+55.5/+22.8/+30.0/-0.3 | +1823 | +12.4/+12.4/+58.1 | +34.1/+5.6 | -24.9/-20.0 | 1810 / -287060 (+2364608/-2651668) | -29272/-52294/-177792/-27702 | 0.03 / 0.98 | +38.9 / -2067 / 57% | OK-PRIOR (allow 15%, deeper -30%) [old -1k rule: OK-PRIOR] | LEAD-RECENT (bi-weekly WF 57% < 60) |
| pb_giveback | arm1_keep0.6(win5,loss2,floor12) | P7 | +6.9/+6.9/+45.6/+20.5/+30.0/-0.3 | +282 | +7.8/+7.8/+46.1 | +30.7/+0.7 | -18.3/-12.8 | 1734 / -232842 (+2238940/-2471782) | -5156/-23797/-176187/-27702 | 0.07 / 1.00 | +38.9 / -2067 / 57% | OK-PRIOR (allow 15%, deeper -30%) [old -1k rule: OK-PRIOR] | LEAD-RECENT (bi-weekly WF 57% < 60) |
| pb_giveback | arm1_keep0.8(win5,loss2,floor12) | P7 | +11.0/+11.0/+57.4/+22.8/+34.8/-6.8 | -3526 | -1.2/-1.2/+51.5 | +25.8/-21.5 | -17.1/-5.0 | 1931 / -161387 (+2705344/-2866731) | -18840/+7263/-122108/-27702 | 0.09 / 1.00 | +38.9 / -2067 / 57% | OK-PRIOR (allow 15%, deeper -35%) [old -1k rule: OK-PRIOR] | no |
| pb_giveback | arm1_keep0.3(win5,loss2,floor12) | P7 | -0.8/+3.0/+37.4/+16.5/+27.2/-0.3 | +320 | +0.3/+4.0/+38.1 | +28.0/+0.8 | -8.2/-7.1 | 1441 / -157465 (+1639138/-1796603) | -6448/+22844/-146159/-27702 | 0.10 / 1.00 | +38.9 / -2067 / 57% | OK-PRIOR (allow 15%, deeper -27%) [old -1k rule: OK-PRIOR] | no |
| pb_giveback | arm1_keep0.8(win5,loss2,floor12) | ALL | +13.3/+13.3/+51.6/+23.9/+38.9/-6.5 | -4599 | -2.9/-2.9/+42.5 | +27.5/-26.4 | +1.2/-4.6 | 3446 / -144325 (+3567381/-3711706) | +1611/-10364/-143263/+7690 | 0.21 / 1.00 | +38.9 / -2067 / 57% | OK-PRIOR (allow 15%, deeper -39%) [old -1k rule: OK-PRIOR] | no |
| pb_giveback | arm1_keep0.5(win5,loss2,floor12) | P7 | -3.5/+6.9/+45.6/+16.9/+30.0/-0.3 | -1169 | -7.8/+3.0/+43.3 | +27.1/-4.5 | -9.1/-6.8 | 1629 / -201780 (+2014806/-2216586) | +22407/-39367/-157119/-27702 | 0.21 / 1.00 | +38.9 / -2067 / 57% | OK-PRIOR (allow 15%, deeper -30%) [old -1k rule: OK-PRIOR] | no |
| pb_giveback | arm1_keep0.3(win5,loss2,floor12) | ALL | -3.0/+3.0/+33.7/+17.3/+30.0/+0.5 | -370 | -4.3/+1.7/+32.9 | +29.1/-0.8 | -1.4/-6.7 | 1937 / -152115 (+1919317/-2071432) | -9326/-3744/-139814/+769 | 0.12 / 1.00 | +38.9 / -2067 / 57% | OK-PRIOR (allow 15%, deeper -30%) [old -1k rule: OK-PRIOR] | no |
| pb_giveback | arm2_keep0.7(win5,loss2,floor12) | P7 | -0.3/+3.0/+10.2/-0.6/-0.0/+8.1 | +479 | +1.3/+4.6/+11.7 | +1.6/+9.6 | -19.9/-0.0 | 1231 / -188678 (+1143741/-1332419) | -24028/-28245/-108703/-27702 | 0.12 / 1.00 | +38.9 / -2067 / 57% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | no |


## Week floor

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_weekfloor | floor6(win5,loss2,arm2/.5) | ALL | -2.6/+5.7/+6.0/+17.6/+9.9/+7.1 | -521 | -4.5/+4.0/+4.2 | +8.2/+5.5 | -11.1/+3.1 | 1382 / -201649 (+1318167/-1519816) | +19351/-47772/-148725/-24504 | 0.19 / 1.00 | +9.9 / -2164 / 41% | OK-PRIOR (allow 15%, deeper -10%) [old -1k rule: OK-PRIOR] | no |
| pb_weekfloor | floor6(win5,loss2,arm2/.5) | P7 | -2.6/+3.0/+6.0/+17.2/+9.9/+8.1 | -666 | -5.0/+0.7/+3.8 | +7.8/+6.0 | -10.7/+4.0 | 1278 / -198418 (+1256909/-1455327) | +11401/-42284/-139833/-27702 | 0.25 / 1.00 | +9.9 / -2164 / 41% | OK-PRIOR (allow 15%, deeper -10%) [old -1k rule: OK-PRIOR] | no |
| pb_weekfloor | floor10(win5,loss2,arm2/.5) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | 0.20 / 1.00 | +9.9 / -2164 / 41% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | no |
| pb_weekfloor | floor8(win5,loss2,arm2/.5) | ALL | -5.2/+3.0/+6.0/+6.4/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1189 / -179294 (+1058584/-1237878) | -6542/-5539/-137197/-30015 | 0.28 / 1.00 | +9.9 / -2164 / 41% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | no |
| pb_weekfloor | floor14(win5,loss2,arm2/.5) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | 0.17 / 1.00 | +9.9 / -2164 / 41% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | no |
| pb_weekfloor | floor16(win5,loss2,arm2/.5) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | 0.26 / 1.00 | +9.9 / -2164 / 41% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | no |
| pb_weekfloor | floor20(win5,loss2,arm2/.5) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | 0.32 / 1.00 | +9.9 / -2164 / 41% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | no |
| pb_weekfloor | floor12(win5,loss2,arm2/.5) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | 0.24 / 1.00 | +9.9 / -2164 / 41% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | no |


## Lock R on base vs sized lots

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_rbasis | R_on_sized_lots | P7 | +38.5/+38.5/+68.7/-26.6/+36.1/+14.7 | +4488 | +46.7/+46.7/+72.9 | +44.6/+26.0 | -33.8/-32.4 | 2606 / -220754 (+4151936/-4372689) | +120445/-112727/-200770/-27702 | 0.01 / 0.08 | +28.3 / -2118 / 72% | OK-PRIOR (allow 25%, deeper -36%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_rbasis | R_on_sized_lots | ALL | +37.6/+37.6/+67.8/-1.1/+40.8/+30.8 | +1751 | +41.1/+41.1/+69.6 | +44.2/+34.7 | -17.3/-32.2 | 5372 / -221650 (+5736531/-5958181) | +115940/-89130/-228335/-20124 | 0.01 / 0.15 | +28.3 / -2118 / 72% | OK-PRIOR (allow 25%, deeper -41%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_rbasis | R_on_base_lots | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | 0.25 / 1.00 | +28.3 / -2118 / 72% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | no |
| pb_rbasis | R_on_base_lots | P7 | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | 0.29 / 1.00 | +28.3 / -2118 / 72% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | no |
| pb_rbasis | R_on_base_lots | K7 | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | 0.26 / 1.00 | +28.3 / -2118 / 72% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | no |
| pb_rbasis | R_on_sized_lots | K7 | -0.5/-0.5/+16.8/+1.0/+11.5/+16.0 | -2156 | -8.5/-8.5/+10.1 | +4.4/+9.3 | -2.3/+5.5 | 3289 / -181584 (+2256763/-2438347) | -9277/-13065/-139118/-20124 | 0.32 / 1.00 | +28.3 / -2118 / 72% | OK-PRIOR (allow 15%, deeper -11%) [old -1k rule: OK-PRIOR] | no |


## Intraday re-arm vs rest-of-day

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_rearm | resume_after_4h | P7 | -19.1/+3.0/+27.0/-5.9/-0.9/+2.9 | +335 | -17.8/+4.1/+27.9 | +0.2/+4.0 | -0.8/+1.6 | 1109 / -138853 (+930311/-1069164) | -13727/+2134/-99558/-27702 | 0.23 / 1.00 | +1.2 / -2391 / 39% | OK-PRIOR (allow 15%, deeper +1%) [old -1k rule: OK-PRIOR] | no |
| pb_rearm | resume_after_next_session | K7 | -9.4/+3.0/+4.3/-2.1/+2.7/+8.9 | -851 | -12.7/+0.1/+1.4 | -0.2/+6.2 | -6.7/+5.5 | 914 / -178590 (+896234/-1074824) | -7741/-11715/-126063/-33071 | 0.38 / 1.00 | +1.2 / -2391 / 39% | OK-PRIOR (allow 15%, deeper -3%) [old -1k rule: OK-PRIOR] | no |
| pb_rearm | resume_after_2h | P7 | -8.4/+3.0/+6.2/+2.5/-10.2/+8.5 | -1247 | -13.2/-1.3/+2.1 | -15.1/+4.4 | -7.6/+11.6 | 1056 / -113424 (+835499/-948923) | -1880/+9333/-93175/-27702 | 0.29 / 1.00 | +1.2 / -2391 / 39% | OK-PRIOR (allow 15%, deeper +10%) [old -1k rule: OK-PRIOR] | no |
| pb_rearm | resume_after_8h | K7 | -8.7/+2.4/+3.0/+2.2/+1.2/+9.4 | -1505 | -14.6/-2.9/-2.3 | -4.1/+4.5 | -5.2/+7.9 | 1242 / -143840 (+1108461/-1252302) | +7378/-16303/-121962/-12953 | 0.35 / 1.00 | +1.2 / -2391 / 39% | OK-PRIOR (allow 15%, deeper -1%) [old -1k rule: OK-PRIOR] | no |
| pb_rearm | resume_after_4h | ALL | -25.1/+5.4/+19.7/-0.5/-2.5/+6.4 | -466 | -27.1/+3.9/+18.4 | -4.2/+4.9 | +3.8/+4.8 | 998 / -122368 (+878958/-1001326) | -6739/+3449/-98533/-20546 | 0.36 / 1.00 | +1.2 / -2391 / 39% | OK-PRIOR (allow 15%, deeper +3%) [old -1k rule: OK-PRIOR] | no |
| pb_rearm | resume_after_8h | P7 | -7.1/+2.4/+2.3/+6.1/-1.5/+8.1 | -2439 | -16.9/-6.5/-6.6 | -10.7/-0.3 | +2.5/+12.6 | 1191 / -135003 (+1094036/-1229039) | -30124/+6142/-83319/-27702 | 0.38 / 1.00 | +1.2 / -2391 / 39% | OK-PRIOR (allow 15%, deeper +1%) [old -1k rule: OK-PRIOR] | no |
| pb_rearm | resume_after_2h | K7 | -17.3/+3.0/+14.3/-3.4/+0.6/+9.0 | -1870 | -25.3/-3.7/+8.4 | -6.2/+2.8 | -2.3/+10.0 | 925 / -136830 (+922115/-1058945) | -2583/-13116/-113693/-7438 | 0.48 / 1.00 | +1.2 / -2391 / 39% | OK-PRIOR (allow 15%, deeper -1%) [old -1k rule: OK-PRIOR] | no |
| pb_rearm | resume_after_4h | K7 | -11.2/-0.4/-0.5/+6.3/-3.4/+10.7 | -1771 | -18.4/-6.9/-7.0 | -10.1/+5.0 | -5.7/+10.2 | 1078 / -149054 (+1003640/-1152694) | -1430/-6510/-120568/-20546 | 0.51 / 1.00 | +1.2 / -2391 / 39% | OK-PRIOR (allow 15%, deeper +3%) [old -1k rule: OK-PRIOR] | no |


## Losing-streak halts (N stops -> off N hours)

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| streak_halt | 3stops_off_8h(+live) | ALL | -5.2/+0.8/+13.0/-3.0/+1.5/+8.1 | +616 | -3.0/+2.8/+14.8 | +3.5/+10.0 | -5.1/-1.1 | 1446 / -119245 (+1280343/-1399589) | +16027/+14291/-113300/-36264 | na | na / na / nan% | OK-PRIOR-UNKNOWN-WF (allow 15%, deeper -2%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] | reference row |
| streak_halt | 2stops_off_2h(+live) | K7 | -1.2/-1.2/-0.7/-0.5/+8.0/+12.6 | -207 | -2.0/-2.0/-1.4 | +7.3/+11.9 | -5.4/+2.6 | 1477 / -171720 (+1230465/-1402185) | -10653/-2726/-131009/-27332 | na | na / na / nan% | OK-PRIOR-UNKNOWN-WF (allow 15%, deeper -8%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] | reference row |
| streak_halt | 2stops_off_1h(+live) | K7 | +0.4/+0.4/+0.3/-1.5/+10.1/+12.8 | -835 | -2.5/-2.5/-2.6 | +7.5/+10.2 | -8.0/+4.5 | 1433 / -161539 (+1204448/-1365987) | -670/-15569/-134532/-10768 | na | na / na / nan% | OK-PRIOR-UNKNOWN-WF (allow 15%, deeper -10%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] | reference row |
| streak_halt | 2stops_off_1h(+live) | P7 | -5.2/+3.0/+10.3/-0.6/+2.3/+0.7 | -830 | -8.3/+0.2/+7.6 | -0.6/-2.2 | -12.4/+5.2 | 1200 / -160571 (+1111188/-1271759) | -12894/+20495/-140471/-27702 | na | na / na / nan% | OK-PRIOR-UNKNOWN-WF (allow 15%, deeper -2%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] | reference row |
| streak_halt | 3stops_off_1h(+live) | K7 | -5.2/+4.1/+4.5/-0.6/-1.4/+9.1 | -596 | -7.4/+2.1/+2.5 | -3.6/+7.2 | -10.5/+4.4 | 1231 / -171634 (+1078356/-1249990) | -3184/-14789/-127989/-25672 | na | na / na / nan% | OK-PRIOR-UNKNOWN-WF (allow 15%, deeper +1%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] | reference row |
| streak_halt | 3stops_off_8h(+live) | K7 | -5.2/+3.8/+8.2/-0.6/-5.8/+11.8 | -864 | -8.4/+0.9/+5.4 | -9.0/+9.1 | -12.5/+6.1 | 1389 / -179125 (+1173087/-1352211) | -19169/-12359/-111332/-36264 | na | na / na / nan% | OK-PRIOR-UNKNOWN-WF (allow 15%, deeper +6%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] | reference row |
| streak_halt | 3stops_off_2h(+live) | K7 | -5.2/+4.1/+4.5/-0.6/-2.8/+13.5 | -687 | -7.7/+1.8/+2.2 | -5.3/+11.4 | -10.5/+5.4 | 1251 / -190690 (+1081224/-1271913) | -3944/-12401/-137933/-36411 | na | na / na / nan% | OK-PRIOR-UNKNOWN-WF (allow 15%, deeper +3%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] | reference row |
| streak_halt | 3stops_off_1h(+live) | P7 | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -683 | -7.7/+0.7/+3.7 | -2.4/+5.9 | -9.9/+5.3 | 1179 / -172937 (+1048999/-1221936) | -6854/-11744/-126636/-27702 | na | na / na / nan% | OK-PRIOR-UNKNOWN-WF (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] | reference row |


## Combos

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_combo | win3_loss1_arm1_keep0.5_floor8 | P7 | +32.6/+32.6/+83.3/+7.5/+38.7/+6.6 | -3225 | +24.2/+24.2/+81.2 | +31.0/-5.0 | -19.1/-5.0 | 2597 / -111240 (+4173208/-4284448) | +182664/-110527/-155675/-27702 | 0.03 / 0.46 | +27.9 / -2695 / 69% | OK-PRIOR (allow 25%, deeper -39%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_combo | win3_loss1_arm1_keep0.5_floor8 | ALL | +11.9/+28.9/+84.7/+15.4/+48.6/+8.7 | -7700 | -19.7/+3.4/+79.3 | +30.1/-23.9 | -13.0/+6.2 | 5730 / -31027 (+6025046/-6056073) | +229428/-78973/-155272/-26210 | 0.25 / 1.00 | +27.9 / -2695 / 69% | OK-PRIOR (allow 22%, deeper -49%) [old -1k rule: OK-PRIOR] | no |
| pb_combo | win4_loss1.5_arm1.5_keep0.5_floor10 | P7 | +6.0/+6.0/+13.5/-0.3/+34.3/+6.4 | -167 | +5.5/+5.5/+13.0 | +33.9/+5.8 | -4.1/-3.0 | 1690 / -117259 (+2166556/-2283815) | +44328/-64378/-69507/-27702 | 0.13 / 1.00 | +27.9 / -2695 / 69% | OK-PRIOR (allow 16%, deeper -34%) [old -1k rule: OK-PRIOR] | CANDIDATE-RECENT (first-order screen; exact pending; family p > .10 or not yet computed: own-draw only) |
| pb_combo | win6_loss3_arm2_keep0.5_floor14 | ALL | +3.1/+12.9/+12.8/-15.2/-16.8/+10.2 | -976 | -0.3/+9.8/+9.7 | -20.9/+7.1 | -5.1/+12.7 | 471 / -102964 (+442188/-545152) | +1131/+34335/-110596/-27835 | 0.04 / 1.00 | +27.9 / -2695 / 69% | RECENT-ONLY (allow 15%, deeper +17%) [old -1k rule: RECENT-ONLY] | no |
| pb_combo | win5_loss2_arm2_keep0.7_floor12 | P7 | -0.3/+3.0/+10.2/-0.6/-0.0/+8.1 | +479 | +1.3/+4.6/+11.7 | +1.6/+9.6 | -19.9/-0.0 | 1231 / -188678 (+1143741/-1332419) | -24028/-28245/-108703/-27702 | 0.14 / 1.00 | +27.9 / -2695 / 69% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | no |
| pb_combo | win6_loss3_arm2_keep0.5_floor14 | P7 | +3.1/+12.0/+11.9/-21.2/-14.0/+6.6 | -1388 | -1.7/+7.7/+7.6 | -19.7/+1.9 | -9.1/+13.4 | 1004 / -79496 (+752811/-832307) | +8078/+42608/-102480/-27702 | 0.09 / 1.00 | +27.9 / -2695 / 69% | OK-PRIOR (allow 15%, deeper +14%) [old -1k rule: OK-PRIOR] | no |
| pb_combo | win5_loss2_arm2_keep0.7_floor12 | ALL | +1.8/+1.8/+1.7/+0.2/+0.9/+8.1 | +161 | +2.4/+2.4/+2.3 | +1.5/+8.6 | -18.9/+0.9 | 1443 / -179559 (+1269941/-1449500) | -22257/-26897/-104092/-26313 | 0.14 / 1.00 | +27.9 / -2695 / 69% | OK-PRIOR (allow 15%, deeper -1%) [old -1k rule: OK-PRIOR] | no |
| pb_combo | win3_loss1.5_arm1.5_keep0.5_floor8 | P7 | +6.0/+6.0/+28.6/+4.3/+30.9/+6.4 | -2787 | -3.9/-3.9/+21.1 | +23.6/-3.5 | +3.1/+6.6 | 1789 / -39904 (+2443484/-2483388) | +59038/-8729/-62512/-27702 | 0.19 / 1.00 | +27.9 / -2695 / 69% | OK-PRIOR (allow 16%, deeper -31%) [old -1k rule: OK-PRIOR] | no |


## Quit-when-up: stack day win cap (+live pb)

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| comb_quit_up | stack_win$40000(+live pb) | ALL | -5.2/+3.0/+27.7/-0.6/-0.0/+8.1 | -858 | -8.4/+0.1/+25.5 | -3.0/+5.3 | -15.1/+6.0 | 1638 / -152021 (+1501562/-1653583) | -17269/-20721/-117640/+3609 | 0.20 / 1.00 | +22.1 / -2763 / 49% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | no |
| comb_quit_up | stack_win$90000(+live pb) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | 0.19 / 1.00 | +22.1 / -2763 / 49% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | no |
| comb_quit_up | stack_win$60000(+live pb) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -895 | -8.5/-0.1/+3.0 | -3.2/+5.2 | -9.1/+6.1 | 1210 / -174678 (+1081506/-1256184) | -7741/-18995/-126257/-21684 | 0.14 / 1.00 | +22.1 / -2763 / 49% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | no |
| comb_quit_up | stack_win$25000(+live pb) | ALL | -5.2/+9.8/+9.7/-0.6/+26.6/+8.1 | -3733 | -20.6/-3.4/-3.5 | +15.9/-5.4 | -28.1/+10.1 | 3069 / +1109 (+3034987/-3033878) | +21343/-18887/-20004/+18657 | 0.49 / 1.00 | +22.1 / -2763 / 49% | OK-PRIOR (allow 15%, deeper -27%) [old -1k rule: RECENT-ONLY] | no |
| comb_quit_up | stack_win$15000(+live pb) | ALL | -36.7/-36.7/-36.9/-9.8/+39.3/+16.9 | -7378 | -82.9/-82.9/-83.1 | +18.8/-11.2 | +18.6/+12.6 | 5608 / +30637 (+5659548/-5628910) | +48618/+32544/-87179/+36655 | 0.91 / 1.00 | +22.1 / -2763 / 49% | OK-PRIOR (allow 15%, deeper -39%) [old -1k rule: OK-PRIOR] | no |


## Stack day loss cap (+live pb)

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| comb_dayloss | stack_loss$15000(+live pb) | ALL | -3.1/-3.1/+53.5/+4.9/-4.7/-5.1 | +262 | -2.2/-2.2/+53.9 | -3.7/-4.2 | -8.3/-4.5 | 3655 / -179903 (+3346364/-3526267) | +158374/-78700/-215449/-44128 | 0.24 / 1.00 | -18.5 / -1958 / 65% | OK-PRIOR (allow 15%, deeper +5%) [old -1k rule: OK-PRIOR] | no |
| comb_dayloss | stack_loss$25000(+live pb) | ALL | -2.4/-2.4/+21.0/+3.2/-0.1/+9.9 | +2008 | +4.2/+4.2/+26.1 | +6.3/+15.7 | -5.4/-3.0 | 1638 / -222397 (+1359205/-1581602) | -7145/-21595/-145886/-47772 | 0.14 / 1.00 | -18.5 / -1958 / 65% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | no |
| comb_dayloss | stack_loss$8000(+live pb) | ALL | +12.2/+12.2/+99.0/+25.6/-25.2/-27.9 | -8984 | -26.8/-26.8/+98.6 | -80.8/-84.8 | +41.0/+19.2 | 7489 / +207398 (+7545288/-7337890) | +443669/+74564/-274137/-36699 | 0.36 / 1.00 | -18.5 / -1958 / 65% | RECENT-ONLY (allow 22%, deeper +25%) [old -1k rule: RECENT-ONLY] | no |
| comb_dayloss | stack_loss$40000(+live pb) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1186 / -169020 (+1054993/-1224014) | -7741/-7826/-126943/-26510 | 0.20 / 1.00 | -18.5 / -1958 / 65% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | no |


## Stack give-back (+live pb)

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| comb_giveback | stack_arm$45000_keep0.5(+live pb) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | 0.23 / 1.00 | +24.5 / -3352 / 49% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | no |
| comb_giveback | stack_arm$30000_keep0.5(+live pb) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -9.6/+5.6 | 1204 / -174846 (+1062781/-1237627) | -7741/-7826/-126792/-32487 | 0.34 / 1.00 | +24.5 / -3352 / 49% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | no |
| comb_giveback | stack_arm$45000_keep0.7(+live pb) | ALL | -5.2/+3.0/+6.0/-0.6/-0.0/+8.1 | -1644 | -11.5/-2.8/+0.3 | -6.0/+2.6 | -4.5/+9.0 | 1240 / -147404 (+1116128/-1263532) | -7741/+8282/-121444/-26500 | 0.32 / 1.00 | +24.5 / -3352 / 49% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | no |
| comb_giveback | stack_arm$30000_keep0.7(+live pb) | ALL | -5.2/+3.0/+10.2/-0.6/-0.0/+8.1 | -3309 | -18.6/-9.4/-1.2 | -12.8/-3.6 | -16.2/+16.0 | 1397 / -105832 (+1272586/-1378418) | -7741/+28439/-108495/-18035 | 0.48 / 1.00 | +24.5 / -3352 / 49% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | no |
| comb_giveback | stack_arm$20000_keep0.5(+live pb) | ALL | -5.2/+3.0/+3.3/+12.8/+32.8/+8.1 | -3707 | -20.5/-11.1/-10.8 | +23.0/-5.3 | +0.2/+8.7 | 1789 / -147246 (+1612802/-1760048) | +19191/+2069/-148847/-19658 | 0.56 / 1.00 | +24.5 / -3352 / 49% | OK-PRIOR (allow 15%, deeper -33%) [old -1k rule: OK-PRIOR] | no |
| comb_giveback | stack_arm$20000_keep0.7(+live pb) | ALL | -5.2/+3.0/+11.3/+15.5/+35.8/+5.3 | -7157 | -39.4/-28.5/-17.5 | +15.0/-25.4 | -11.0/+20.6 | 2361 / -136656 (+2192540/-2329196) | -24355/+12204/-140441/+15936 | 0.73 / 1.00 | +24.5 / -3352 / 49% | OK-PRIOR (allow 15%, deeper -36%) [old -1k rule: OK-PRIOR] | no |
| comb_giveback | stack_arm$10000_keep0.7(+live pb) | ALL | -32.6/-32.6/-32.7/-6.5/+35.8/+16.5 | -6773 | -72.6/-72.6/-72.8 | +16.5/-8.8 | -4.8/+4.0 | 5187 / -139197 (+4956754/-5095951) | +45090/-64131/-121823/+1667 | 0.87 / 1.00 | +24.5 / -3352 / 49% | OK-PRIOR (allow 15%, deeper -36%) [old -1k rule: OK-PRIOR] | no |
| comb_giveback | stack_arm$10000_keep0.5(+live pb) | ALL | -35.6/-35.6/-35.7/-10.1/+32.5/+16.4 | -8398 | -90.3/-90.3/-90.5 | +5.2/-17.3 | +11.6/+17.8 | 4227 / -77438 (+4029102/-4106540) | +78525/-19842/-107543/-28578 | 0.97 / 1.00 | +24.5 / -3352 / 49% | OK-PRIOR (allow 15%, deeper -32%) [old -1k rule: OK-PRIOR] | no |


## Stack week floor (+live pb)

| technique | setting | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p own / family (whole grid) | bi-weekly WF (cut / d mean / beats live %) | prior | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| comb_weekfloor | stack_floor$30000(+live pb) | ALL | +21.7/+21.7/+21.6/+19.5/+19.9/-7.2 | -1609 | +17.1/+17.1/+17.0 | +15.3/-13.4 | +7.2/-13.5 | 4187 / -177663 (+4262387/-4440050) | +133506/-110625/-176706/-23837 | 0.07 / 1.00 | +0.0 / -3283 / 46% | OK-PRIOR (allow 15%, deeper -20%) [old -1k rule: OK-PRIOR] | LEAD-RECENT (bi-weekly WF 46% < 60) |
| comb_weekfloor | stack_floor$100000(+live pb) | ALL | -5.2/+3.0/+6.0/+0.5/-0.0/+8.1 | -746 | -7.9/+0.4/+3.5 | -2.6/+5.7 | -10.1/+5.6 | 1229 / -170984 (+1101154/-1272137) | +3415/-15448/-133652/-25299 | 0.31 / 1.00 | +0.0 / -3283 / 46% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | no |
| comb_weekfloor | stack_floor$60000(+live pb) | ALL | -9.6/-9.6/-9.7/+12.0/+22.0/+8.1 | -559 | -11.7/-11.7/-11.9 | +20.4/+6.3 | -11.4/-0.4 | 1819 / -227524 (+1709765/-1937289) | +8857/-72085/-145710/-18585 | 0.28 / 1.00 | +0.0 / -3283 / 46% | OK-PRIOR (allow 15%, deeper -22%) [old -1k rule: OK-PRIOR] | no |


## REFIT 2026-11-22: what the bi-weekly procedure picks today (trailing 26 weeks to 2026-10-30, DD-first picker over the whole R1 grid, reference = live locks)

Pick: **R1;pb_rbasis;R_on_sized_lots;P7** (live retained: False; train end 2026-11-05). Bi-weekly WF over the whole grid: OOS maxDD cut +14.7%, d mean -2078 $/wk, beats live in 70% of 74 refit periods.


> STANDING RULES 2/2a: ranking = 0.5 L6M + 0.3 L3M + 0.2 L1M equal-mean cut (recents first); bi-weekly WF (sz_core) is the primary OOS column; PRE/X' tolerant via sz_core.prior_info; materiality floor L6M cut >= 5%. The exact top-5 sets were frozen before these rules (ranking by min of L6M/PRE/X').


## Exact-engine rows (S1b engine; each cell tagged ROLL-FIXED or ROLL-EXCL; windows complete only): live, NOLOCK reference, R1 top-5

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
| Day profit / loss caps | +5R / -2R per book | win4_loss1(arm2,keep.5,floor12) P7 (cut +33.7/+19.1/+20.9, d mean +2211) | -10.0 | candidate for exact; live stays until exact confirms | P7MaxDailyLoss (DS7.cs: DayPnl <= -MaxDayLoss * max(1, SizeMult), realized day P&L); R1_3 line: P7MaxDailyLoss 16,800 -> 8,400 |
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

## R1_3 decision pack (P7 per-book daily loss cap -1R instead of -2R; exact engine rows; ROLL-FIXED where tagged)

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
DS7.cs field: **P7MaxDailyLoss** (a dollar amount; check `DayPnl <= -MaxDayLoss * max(1, SizeMult)`, REALIZED day P&L only, blocks new entries for the rest of the label day and exits an open trade). The engine (DAYCAP table) uses the same: P7 -16,800 USD = 2R with R = BASE lots x 60 pt x $20 = 7 x 1,200 = $8,400; under Q1-A the size multiplier never exceeds 1, so the cap is on BASE lots, not on the lots actually traded (the sized-lot R of R1_1/R1_2 is a different setting). **R1_3 line: P7MaxDailyLoss 16,800 -> 8,400** (all other books and the P7 daily profit cap unchanged).


## R1b. StackCut (hard-coded 50% / Asia-only in the engine): exact variants, counterfactual of the cut exits


> **Label: PRE-PROOF; post-hoc; Shadow only; no PASS claims. EXACT engine rows (patched ROLLFIX1 S1b engine), reference = patched S1-COMB. STANDING RULE: StackCut stays ON; OFF is a reference row only. Rule 2/2a labels use sz_core.prior_info; the bi-weekly walk-forward cannot be computed because the variants were run only on the L6M and PRE months (WF label suffix UNKNOWN-WF, 15% allowance).**

Live rule (replica sim.stack_on_stop): when a book is STOPPED and its entry session is Asia, every other open position on the same side is cut by 50% (rounded up; one lot = exit all) with exit name StackCut. Variants run: pct 25/75/100, sessions all / Asia+London, trigger = second same-side stop within 30 min / either side / other same-side open lots >= 4.

Identity test (live spec through the new hook vs the patched S1-COMB lists): L6M: 6 of 6 months identical to the patched S1-COMB; PRE: 17 of 17 months identical to the patched S1-COMB.

## Exact rows vs live (maxDD cut; d mean $/wk; (b) equal-mean cut; worst-20 cut; StackCut exits)

| set | variant | L6M maxDD / cut / d mean / (b) / w20 cut / n StackCut | PRE maxDD / cut / d mean / (b) / w20 cut / n StackCut | label |
|--|--|--|--|--|
| CDE_SC_LIVE | live: 50%, Asia-only, first stop, same side | 79907 / +0.0 / +0 / +0.0 / +0.0 / 67 | 140288 / +0.0 / +0 / +0.0 / +0.0 / 141 | LIVE setting |
| CDE_SC_OFF | OFF (reference row only) | 83537 / -4.5 / -4174 / -22.1 / +9.9 / 0 | 138499 / +1.3 / +192 / +2.6 / -3.9 / 0 | reference row only (standing rule: layer stays ON) |
| CDE_SC_P25 | pct 25, Asia-only | 81588 / -2.1 / -235 / -2.9 / +2.0 / 65 | 141031 / -0.5 / +151 / +0.6 / -1.0 / 137 | recent: no / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper +1%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] |
| CDE_SC_P75 | pct 75, Asia-only | 82817 / -3.6 / -383 / -5.0 / +1.3 / 123 | 138295 / +1.4 / -200 / -0.0 / +1.7 / 223 | recent: no / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper -1%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] |
| CDE_SC_P100 | pct 100, Asia-only | 85764 / -7.3 / -7619 / -45.4 / +4.4 / 179 | 138354 / +1.4 / +117 / +2.2 / +0.9 / 329 | recent: no / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper -1%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] |
| CDE_SC_ALL | 50%, ALL sessions | 90449 / -13.2 / -86 / -13.5 / +5.3 / 151 | 136290 / +2.8 / -1309 / -7.5 / -1.1 / 371 | recent: no / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper -3%) [old -1k rule: RECENT-ONLY-UNKNOWN-WF] |
| CDE_SC_AL | 50%, Asia+London | 89829 / -12.4 / -350 / -13.8 / +7.8 / 122 | 136385 / +2.8 / -836 / -3.6 / -0.8 / 247 | recent: no / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper -3%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] |
| CDE_SC_SECOND | 50%, Asia, only on the 2nd same-side stop within 30 min | 83404 / -4.4 / -4816 / -25.1 / +7.6 / 11 | 142229 / -1.4 / +195 / +0.0 / -3.3 / 26 | recent: no / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper +1%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] |
| CDE_SC_ANYSIDE | 50%, Asia, cut other books on either side | 76439 / +4.3 / +1055 / +7.7 / -8.3 / 152 | 139276 / +0.7 / +284 / +2.7 / -11.0 / 449 | RECENT-OK / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper -1%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] |
| CDE_SC_LOTS4 | 50%, Asia, only if other same-side open lots >= 4 | 80100 / -0.2 / -1073 / -4.1 / +2.7 / 28 | 139810 / +0.3 / -151 / -0.8 / -1.1 / 67 | recent: no / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper -0%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] |

## Counterfactual: what the StackCut exits would have done held to their bracket (never-cut universe path, no later state cut)

| window | StackCut exits | matched to universe | actual net P&L of those trades | same trades held to bracket (no state cut) | cut minus hold | by entry session (n / cut minus hold) |
|--|--|--|--|--|--|--|
| L6M | 67 | 60 | -56380 | -49970 | -592 | 0 58 / -719; 1 2 / +127 |
| PRE | 141 | 133 | -143243 | -131966 | -3857 | 0 111 / +1795; 1 18 / -4209; 3 4 / -1442 |
| X' | 111 | 109 | -125369 | -130364 | +7267 | 0 88 / +7129; 1 20 / -20; 3 1 / +159 |
| HOLD | 137 | 127 | -125073 | -134641 | +17685 | 0 120 / +17446; 1 6 / +597; 3 1 / -358 |
| ALL | 436 | 412 | -438915 | -438804 | +21618 | 0 360 / +28835; 1 46 / -5575; 3 6 / -1642 |

Reading: the -$439k is the P&L of the trades that ended by StackCut (they were losers: the other leg of a stopped book on the same side); the same trades held to their bracket would have made about the same (-$439k), so the cut itself is worth about +$21.6k over 43 months, all of it in Asia (+$28.8k) and slightly negative in London (-$5.6k) and NY-AM (-$1.6k): the rule is not the source of the loss, it avoided a small part of it; the loss is the stop of the first book.


## L. Cooldowns / chop pauses (SZ-L top-5, exact ROLL-FIXED; L6M, PRE, X-prime and HOLD). Label per Rule 2/2a; WF is the bi-weekly re-pick walk-forward of the cell vs live on the contiguous exact block.

### L top-5 exact rows

| set | cell | window | exact maxDD cut | d mean $/wk | equal-mean cut | tag |
|--|--|--|--|--|--|--|
| CDE_L1 | L_chop {"H": 30, "M": 1, "N": 2, "cond": "rng60_3.0", "eff": 0.0, "post": 1.0, "scope": "exKB"} | L6M | +18.9 | -2140 | +12.4 | ROLL-FIXED |
| CDE_L1 | L_chop {"H": 30, "M": 1, "N": 2, "cond": "rng60_3.0", "eff": 0.0, "post": 1.0, "scope": "exKB"} | PRE | +1.3 | -1532 | -6.5 | ROLL-FIXED |
| CDE_L1 | L_chop {"H": 30, "M": 1, "N": 2, "cond": "rng60_3.0", "eff": 0.0, "post": 1.0, "scope": "exKB"} | X' | +54.3 | +1995 | +50.6 | ROLL-FIXED |
| CDE_L1 | L_chop {"H": 30, "M": 1, "N": 2, "cond": "rng60_3.0", "eff": 0.0, "post": 1.0, "scope": "exKB"} | HOLD | +1.4 | -1403 | -6.5 | ROLL-FIXED |
| CDE_L2 | L_chop {"H": 30, "M": 1, "N": 2, "cond": "rng60_3.0", "eff": 0.0, "post": 1.0, "scope": "ALL"} | L6M | +15.5 | -4188 | +1.3 | ROLL-FIXED |
| CDE_L2 | L_chop {"H": 30, "M": 1, "N": 2, "cond": "rng60_3.0", "eff": 0.0, "post": 1.0, "scope": "ALL"} | PRE | -0.2 | -1142 | -17.0 | ROLL-FIXED |
| CDE_L2 | L_chop {"H": 30, "M": 1, "N": 2, "cond": "rng60_3.0", "eff": 0.0, "post": 1.0, "scope": "ALL"} | X' | +45.3 | +1508 | +36.1 | ROLL-FIXED |
| CDE_L2 | L_chop {"H": 30, "M": 1, "N": 2, "cond": "rng60_3.0", "eff": 0.0, "post": 1.0, "scope": "ALL"} | HOLD | -6.2 | -1820 | -24.1 | ROLL-FIXED |
| CDE_L3 | L_sessloss {"eff": 0.0, "n": 2, "sess": [1], "state": "stack"} | L6M | +26.6 | -2843 | +18.6 | ROLL-FIXED |
| CDE_L3 | L_sessloss {"eff": 0.0, "n": 2, "sess": [1], "state": "stack"} | PRE | +20.9 | -1752 | +12.3 | ROLL-FIXED |
| CDE_L3 | L_sessloss {"eff": 0.0, "n": 2, "sess": [1], "state": "stack"} | X' | +4.8 | +83 | -5.5 | ROLL-FIXED |
| CDE_L3 | L_sessloss {"eff": 0.0, "n": 2, "sess": [1], "state": "stack"} | HOLD | -10.9 | -2917 | -22.9 | ROLL-FIXED |
| CDE_L4 | L_sessloss {"eff": 0.0, "n": 3, "sess": [1], "state": "stack"} | L6M | +11.9 | +1889 | +17.3 | ROLL-FIXED |
| CDE_L4 | L_sessloss {"eff": 0.0, "n": 3, "sess": [1], "state": "stack"} | PRE | +34.5 | -827 | +38.5 | ROLL-FIXED |
| CDE_L4 | L_sessloss {"eff": 0.0, "n": 3, "sess": [1], "state": "stack"} | X' | +17.0 | +470 | +22.0 | ROLL-FIXED |
| CDE_L4 | L_sessloss {"eff": 0.0, "n": 3, "sess": [1], "state": "stack"} | HOLD | -15.2 | -1256 | -8.2 | ROLL-FIXED |
| CDE_L5 | L_chop_book {"H": 0, "M": 3, "N": 2, "cond": "rng60_3.5", "eff": 0.0, "post": 1.0, "scope": "PE"} | L6M | -2.4 | -6075 | -29.5 | ROLL-FIXED |
| CDE_L5 | L_chop_book {"H": 0, "M": 3, "N": 2, "cond": "rng60_3.5", "eff": 0.0, "post": 1.0, "scope": "PE"} | PRE | +37.5 | +2087 | +20.9 | ROLL-FIXED |
| CDE_L5 | L_chop_book {"H": 0, "M": 3, "N": 2, "cond": "rng60_3.5", "eff": 0.0, "post": 1.0, "scope": "PE"} | X' | +28.4 | +480 | +9.4 | ROLL-FIXED |
| CDE_L5 | L_chop_book {"H": 0, "M": 3, "N": 2, "cond": "rng60_3.5", "eff": 0.0, "post": 1.0, "scope": "PE"} | HOLD | +17.7 | -4558 | -4.0 | ROLL-FIXED |

| set | bi-weekly WF (block) beats live % / OOS cut / d mean | label (Rule 2/2a) |
|--|--|--|
| CDE_L1 | 33% (X-prime+PRE) / -3.3% / -1 | RECENT-OK / OK-PRIOR (allow 15%, WF 33%) [old -1k rule: RECENT-ONLY] |
| CDE_L2 | 21% (X-prime+PRE) / +0.0% / -844 | recent: no / OK-PRIOR (allow 15%, WF 21%) / HOLD deeper -6.2% [old -1k rule: RECENT-ONLY] |
| CDE_L3 | 42% (X-prime+PRE) / +0.0% / -1575 | RECENT-OK / OK-PRIOR (allow 15%, WF 42%) / HOLD deeper -10.9% [old -1k rule: RECENT-ONLY] |
| CDE_L4 | 19% (X-prime+PRE) / +0.0% / -2087 | RECENT-OK / OK-PRIOR (allow 15%, WF 19%) / HOLD deeper -15.2% [old -1k rule: OK-PRIOR] |
| CDE_L5 | 49% (X-prime+PRE) / +31.2% / +1025 | recent: no / OK-PRIOR (allow 15%, WF 49%) [old -1k rule: OK-PRIOR] |


Standard note: after a pause the engine re-enters at different seconds, so removed/exact-only trade COUNTS are churn; read net P&L and the equal-mean cuts. Frozen-week reading (first-order, SZ-L): no cooldown removes the P7 Asia/London chop losses without removing winners (best ratio: London stack-loss rule).


## G. Recents-first candidates from the E / D screens (CDE_G1-G4; G1 and G2: L6M, PRE, X-prime and HOLD; G3 and G4: L6M and PRE only)

### G exact rows

| set | cell | window | exact maxDD cut | d mean $/wk | equal-mean cut | tag |
|--|--|--|--|--|--|--|
| CDE_G1 | E;corr_same_side;N30min_f0.0_ge1_others;sess_london | L6M | +14.7 | -1872 | +8.8 | ROLL-FIXED |
| CDE_G1 | E;corr_same_side;N30min_f0.0_ge1_others;sess_london | PRE | +22.1 | -792 | +16.7 | ROLL-FIXED |
| CDE_G1 | E;corr_same_side;N30min_f0.0_ge1_others;sess_london | X' | +19.9 | +2231 | +14.3 | ROLL-FIXED |
| CDE_G1 | E;corr_same_side;N30min_f0.0_ge1_others;sess_london | HOLD | +7.8 | -345 | +1.5 | ROLL-FIXED |
| CDE_G2 | E;corr_same_side;N30min_f0.5_ge1_others;sess_london | L6M | +18.6 | -1351 | +14.7 | ROLL-FIXED |
| CDE_G2 | E;corr_same_side;N30min_f0.5_ge1_others;sess_london | PRE | -2.7 | -1131 | -7.7 | ROLL-FIXED |
| CDE_G2 | E;corr_same_side;N30min_f0.5_ge1_others;sess_london | X' | +10.0 | +764 | +5.6 | ROLL-FIXED |
| CDE_G2 | E;corr_same_side;N30min_f0.5_ge1_others;sess_london | HOLD | +11.1 | -1358 | +6.8 | ROLL-FIXED |
| CDE_G3 | E;newentry_haircut_day_dd;Y3000_f0.0;K7 | L6M | +4.7 | -5640 | -18.3 | ROLL-FIXED |
| CDE_G3 | E;newentry_haircut_day_dd;Y3000_f0.0;K7 | PRE | +9.6 | -726 | -12.2 | ROLL-FIXED |
| CDE_G4 | D;dayloss_stack$;X3000_f0.00;K7 | L6M | +1.8 | -6490 | -26.4 | ROLL-FIXED |
| CDE_G4 | D;dayloss_stack$;X3000_f0.00;K7 | PRE | +8.0 | -830 | -18.4 | ROLL-FIXED |

| set | bi-weekly WF (block) beats live % / OOS cut / d mean | label (Rule 2/2a) |
|--|--|--|
| CDE_G1 | 51% (X-prime+PRE) / +22.1% / -289 | RECENT-OK / OK-PRIOR (allow 15%, WF 51%) [old -1k rule: OK-PRIOR] |
| CDE_G2 | 51% (X-prime+PRE) / -2.7% / -718 | RECENT-OK / OK-PRIOR (allow 15%, WF 51%) [old -1k rule: RECENT-ONLY] |
| CDE_G3 | 52% (PRE only (26w train inside PRE)) / +8.2% / -2259 | recent: no / OK-PRIOR (allow 15%, WF 52%) [old -1k rule: OK-PRIOR] |
| CDE_G4 | 48% (PRE only (26w train inside PRE)) / +7.2% / -1826 | recent: no / OK-PRIOR (allow 15%, WF 48%) [old -1k rule: OK-PRIOR] |


## R1 exact top-5 with WF% and Rule-2a label (ROLL-FIXED)

### R1 exact rows (locks)

| set | cell | window | exact maxDD cut | d mean $/wk | equal-mean cut | tag |
|--|--|--|--|--|--|--|
| CDE_R1_1 | R1_1 | L6M | +32.7 | -8025 | +7.1 | ROLL-FIXED |
| CDE_R1_1 | R1_1 | PRE | +53.0 | +81 | +35.1 | ROLL-FIXED |
| CDE_R1_1 | R1_1 | X' | +7.8 | -1464 | -27.3 | ROLL-FIXED |
| CDE_R1_1 | R1_1 | HOLD | +19.5 | -6718 | -11.2 | ROLL-FIXED |
| CDE_R1_2 | R1_2 | L6M | +17.0 | -5089 | -0.6 | ROLL-FIXED |
| CDE_R1_2 | R1_2 | PRE | +48.6 | +269 | +37.7 | ROLL-FIXED |
| CDE_R1_2 | R1_2 | X' | +1.1 | -2168 | -19.9 | ROLL-FIXED |
| CDE_R1_2 | R1_2 | HOLD | -19.1 | -6309 | -44.4 | ROLL-FIXED |
| CDE_R1_3 | R1_3 | L6M | +25.7 | +492 | +27.0 | ROLL-FIXED |
| CDE_R1_3 | R1_3 | PRE | +17.0 | +1108 | +18.4 | ROLL-FIXED |
| CDE_R1_3 | R1_3 | X' | +5.7 | -1076 | +7.3 | ROLL-FIXED |
| CDE_R1_3 | R1_3 | HOLD | +7.5 | +242 | +9.1 | ROLL-FIXED |
| CDE_R1_4 | R1_4 | L6M | +25.7 | +66 | +25.9 | ROLL-FIXED |
| CDE_R1_4 | R1_4 | PRE | +17.0 | +917 | +17.2 | ROLL-FIXED |
| CDE_R1_4 | R1_4 | X' | +5.7 | -1076 | +5.9 | ROLL-FIXED |
| CDE_R1_4 | R1_4 | HOLD | +7.5 | -8 | +7.7 | ROLL-FIXED |
| CDE_R1_5 | R1_5 | L6M | +3.1 | -5048 | -17.3 | ROLL-FIXED |
| CDE_R1_5 | R1_5 | PRE | +29.2 | +81 | +14.3 | ROLL-FIXED |
| CDE_R1_5 | R1_5 | X' | +50.2 | +1608 | +39.7 | ROLL-FIXED |
| CDE_R1_5 | R1_5 | HOLD | +13.4 | -5555 | -4.7 | ROLL-FIXED |

| set | bi-weekly WF (block) beats live % / OOS cut / d mean | label (Rule 2/2a) |
|--|--|--|
| CDE_R1_1 | 60% (X-prime+PRE) / +45.0% / -302 | RECENT-OK / OK-PRIOR (allow 25%, WF 60%) [old -1k rule: OK-PRIOR] |
| CDE_R1_2 | 35% (X-prime+PRE) / +45.0% / -92 | recent: no / OK-PRIOR (allow 15%, WF 35%) / HOLD deeper -19.1% [old -1k rule: OK-PRIOR] |
| CDE_R1_3 | 56% (X-prime+PRE) / +17.0% / +273 | RECENT-OK / OK-PRIOR (allow 15%, WF 56%) [old -1k rule: OK-PRIOR] |
| CDE_R1_4 | 56% (X-prime+PRE) / +17.0% / +191 | RECENT-OK / OK-PRIOR (allow 15%, WF 56%) [old -1k rule: OK-PRIOR] |
| CDE_R1_5 | 9% (X-prime+PRE) / +31.2% / +1790 | recent: no / OK-PRIOR (allow 15%, WF 9%) [old -1k rule: OK-PRIOR] |


## Walk-forward reconciliation for R1_3

The figures differ because they are different tests: exact, R1_3 alone vs live, block A = X-prime+PRE (refit 2023-11-06..2025-06-30): beats live in 56% of 43 refit periods (OOS cut +17.0%); exact, block B = HOLD+L6M (refit 2026-05-04..2026-10-30): 58% of 12 periods; first-order screen on the NOLOCK exact list, picker over the whole pb_daycaps group (all daily-cap cells, all scopes) vs live, 74 refit periods 2024-01..2026-10: 64%. The 56% (exact block A) is the one used for the Rule 2a allowance of R1_3 itself (15%); the ~64% is the first-order group picker (whole daily-cap family) and the joint driver's figure covers a different candidate set / block. The 64% would clear the 60% bar, but it is a first-order screen of a family picker, not of the cell itself, so the exact 56% / 58% (blocks A / B) govern the label.


Roll-artifact note: the spurious RollFlat trades found in non-roll months (positions open at the monthly chunk end closed by a later roll event) were already fixed in SZ-CORE's RollRep with no effect on the references or the P7 cells; my driver and loaders carry the same fix (cde_roll.clean drops RollFlat rows that are not at that month's own roll second; new runs schedule only in-month roll events).


## Joint stacks containing R1_3 (SZ-IJK, exact ROLL-FIXED, DS3_JOINT.md)

| JP01 | JN04 + R1_3 P7 MaxDailyLoss 8400 lock | +42.6 / +42.6 / +50.8 | +49.6 | +3109 / +3822 | +49.6 / -2559 | +41.7 / -3218 | +66.2 / +1165 | 85% (91%) | RECENT-ONLY (allow 25.0%, WF 85%) |
| JP06 | JN04 x ZS_D0 + R1_3 lock + F04 | +34.6 / +38.7 / +78.0 | +30.2 | -1426 / +998 | +31.9 / -6025 | +48.6 / -3607 | n/a / n/a | 82% (82%) | RECENT-ONLY (allow 25.0%, WF 82%) |


## REFIT 2026-11-22: the bi-weekly procedure over ALL exact cells with the full 2026-05..10 block (trailing 26 weeks to 2026-10-30, DD-first, live retained when nothing is lower)

Pick: **CDE_R1_1** (live retained: False; train end 2026-11-05). Ranked (maxDD, worst-20, Ulcer, mean $/wk; prior label from exact PRE):

| cell | trailing maxDD | worst-20 | Ulcer | mean | prior |
|--|--|--|--|--|--|
| CDE_R1_1 | 53773 | 102503 | 15916 | 18272 | OK-PRIOR |
| CDE_F04 | 55751 | 169508 | 23906 | 24362 | OK-PRIOR |
| CDE_L3 | 58687 | 87906 | 25711 | 23692 | OK-PRIOR |
| CDE_F01 | 59285 | 141317 | 26294 | 25021 | OK-PRIOR |
| CDE_R1_3 | 59357 | 188078 | 20964 | 25845 | OK-PRIOR |
| CDE_R1_4 | 59357 | 183725 | 20964 | 25466 | OK-PRIOR |
| CDE_F00 | 60724 | 68782 | 29450 | 17576 | RECENT-ONLY |
| CDE_F03 | 64806 | 84953 | 26565 | 17160 | RECENT-ONLY |
| CDE_L1 | 64820 | 169775 | 24684 | 25176 | OK-PRIOR |
| CDE_G2 | 65030 | 101042 | 28578 | 23089 | OK-PRIOR |
| CDE_R1_2 | 66329 | 109214 | 19231 | 20577 | OK-PRIOR |
| CDE_L2 | 67512 | 174334 | 25645 | 24628 | OK-PRIOR |
