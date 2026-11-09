# DS3_REDO_R1_LOCKS - T-STACK-REDO R1: locks on the state base (first version 2026-11-09 19:09Z)

> **Label: PRE-PROOF; post-hoc; Shadow only; no PASS claims. FIRST-ORDER SCREEN ONLY unless a row is in the exact table below. ROLL-EXCL: the 31 roll-artifact base trades are excluded from every number. STANDING RULE: every lock stays ON; "off" rows are reference rows only; the deliverable is the best SETTING (drawdown first at equal mean, holds OOS); if nothing beats the live setting the live setting stays.**

Method: the screen runs on the EXACT NOLOCK trade list (engine with the lock layer switched off, 33 window months; screen base = DIR:/mnt/l2/l2vast/_th_state/s345/exact_b/runs/CDE_NOLOCK) so any lock setting, tighter or looser than live, is replayed first-order (realized-only state: a lock triggers when a trade exits; the engine also marks open P&L and flattens, which the screen cannot see). Reference = the live setting = S1b-COMB exact list. Regression: the exact lock override with the live values reproduces S1-COMB 202605 trade for trade (672 trades, net 35,852). Day caps use realized P&L only (as live check_limits), give-back and week floor use realized + open P&L. R on base lots = planned lots x 60 pt x $20 (PE 8,400, KB/MV 2,400, HM/SM 4,800, PB/OD 1,200; x max(1, size mult)). Scope: PerBook = per-book values; stack ($) rows are Combined; "(+live pb)" = Combined on top of the live per-book locks. One-book scopes keep the live locks on the other books.

## Overall: top 15 settings by the joint equal-mean cut (min of L6M, PRE, X')

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_rbasis | R_on_sized_lots | ALL | +37.6/-1.1/+40.8/+30.8 | +1751 | +41.1/+44.2/+34.7 | -17.3/-32.2 | 5372 / -221650 (+5736531/-5958181) | +115940/-89130/-228335/-20124 | 0.01 | -5.2 | DD |
| pb_rbasis | R_on_sized_lots | P7 | +38.5/-26.6/+36.1/+14.7 | +4488 | +46.7/+44.6/+26.0 | -33.8/-32.4 | 2606 / -220754 (+4151936/-4372689) | +120445/-112727/-200770/-27702 | 0.01 | -5.2 | DD |
| pb_daycaps | win4_loss1(arm2,keep.5,floor12) | P7 | +28.7/+7.5/+12.9/+14.9 | +2211 | +33.7/+19.1/+20.9 | -25.2/-12.9 | 2107 / -197930 (+3050331/-3248261) | +128501/-116110/-182618/-27702 | 0.02 | -10.0 | DD |
| pb_daycaps | win8_loss1(arm2,keep.5,floor12) | P7 | +28.7/+7.5/+12.9/+14.9 | +1690 | +32.6/+17.7/+19.6 | -23.0/-11.4 | 2052 / -167932 (+2946004/-3113936) | +145059/-94801/-190489/-27702 | 0.02 | -10.0 | DD |
| pb_daycaps | win6_loss1(arm2,keep.5,floor12) | P7 | +28.7/+7.5/+12.9/+14.9 | +1690 | +32.6/+17.7/+19.6 | -23.0/-11.4 | 2052 / -167932 (+2946004/-3113936) | +145059/-94801/-190489/-27702 | 0.02 | -10.0 | DD |
| pb_daycaps | win5_loss1(arm2,keep.5,floor12) | P7 | +28.7/+7.5/+12.9/+14.9 | +1672 | +32.6/+17.7/+19.6 | -23.1/-11.4 | 2057 / -167484 (+2955584/-3123068) | +145059/-91941/-192901/-27702 | 0.03 | -10.0 | DD |
| pb_daycaps | win3_loss1(arm2,keep.5,floor12) | P7 | +28.7/+7.5/+12.9/+14.9 | -315 | +27.9/+12.0/+14.0 | -24.1/-5.3 | 2202 / -118223 (+3318877/-3437099) | +143211/-60801/-172932/-27702 | 0.01 | -10.0 | DD |
| pb_daycaps | win4_loss1(arm2,keep.5,floor12) | ALL | +25.6/+13.6/+11.0/+16.1 | -1497 | +21.6/+6.2/+11.5 | -24.2/-7.5 | 4394 / -118844 (+4420894/-4539738) | +167270/-63531/-176726/-45857 | 0.09 | -10.0 | DD |
| pb_daycaps | win5_loss1(arm2,keep.5,floor12) | ALL | +25.6/+13.6/+10.6/+16.1 | -1439 | +21.8/+6.0/+11.7 | -23.1/-8.0 | 4255 / -106687 (+4261297/-4367983) | +184525/-40302/-190656/-60254 | 0.10 | -10.0 | DD |
| pb_daycaps | win4_loss1.5(arm2,keep.5,floor12) | P7 | +2.1/-0.3/+4.8/+6.4 | +1129 | +5.8/+8.4/+9.9 | +3.4/+1.7 | 1528 / -90513 (+1835475/-1925989) | +54133/-46940/-70004/-27702 | 0.03 | -10.0 | DD |
| pb_daycaps | win8_loss1(arm2,keep.5,floor12) | ALL | +25.6/+13.6/+10.6/+16.1 | -1502 | +21.6/+5.8/+11.5 | -21.9/-8.0 | 4196 / -109352 (+4219368/-4328720) | +184525/-40426/-184688/-68763 | 0.04 | -10.0 | DD |
| pb_giveback | arm1_keep0.7(win5,loss2,floor12) | P7 | +6.9/+22.8/+30.0/-0.3 | +1823 | +12.4/+34.1/+5.6 | -24.9/-20.0 | 1810 / -287060 (+2364608/-2651668) | -29272/-52294/-177792/-27702 | 0.03 | +20.5 | DD |
| pb_daycaps | win6_loss1(arm2,keep.5,floor12) | ALL | +25.6/+13.6/+10.6/+16.1 | -1555 | +21.4/+5.6/+11.3 | -21.6/-7.8 | 4206 / -108265 (+4226556/-4334821) | +184525/-40426/-184688/-67676 | 0.08 | -10.0 | DD |
| pb_combo | win4_loss1.5_arm1.5_keep0.5_floor10 | P7 | +6.0/-0.3/+34.3/+6.4 | -167 | +5.5/+33.9/+5.8 | -4.1/-3.0 | 1690 / -117259 (+2166556/-2283815) | +44328/-64378/-69507/-27702 | 0.03 | +15.7 | DD |
| comb_dayloss | stack_loss$25000(+live pb) | ALL | -2.4/+3.2/-0.1/+9.9 | +2008 | +4.2/+6.3/+15.7 | -5.4/-3.0 | 1638 / -222397 (+1359205/-1581602) | -7145/-21595/-145886/-47772 | 0.02 | -47.1 | DD |


## Daily caps (win R x loss R)

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_daycaps | win4_loss1(arm2,keep.5,floor12) | P7 | +28.7/+7.5/+12.9/+14.9 | +2211 | +33.7/+19.1/+20.9 | -25.2/-12.9 | 2107 / -197930 (+3050331/-3248261) | +128501/-116110/-182618/-27702 | 0.02 | -10.0 | DD |
| pb_daycaps | winoff_loss1(arm2,keep.5,floor12) | P7 | +28.7/+7.5/+12.9/+14.9 | +1690 | +32.6/+17.7/+19.6 | -23.0/-11.4 | 2052 / -167932 (+2946004/-3113936) | +145059/-94801/-190489/-27702 | na | -10.0 | DD |
| pb_daycaps | win8_loss1(arm2,keep.5,floor12) | P7 | +28.7/+7.5/+12.9/+14.9 | +1690 | +32.6/+17.7/+19.6 | -23.0/-11.4 | 2052 / -167932 (+2946004/-3113936) | +145059/-94801/-190489/-27702 | 0.02 | -10.0 | DD |
| pb_daycaps | win6_loss1(arm2,keep.5,floor12) | P7 | +28.7/+7.5/+12.9/+14.9 | +1690 | +32.6/+17.7/+19.6 | -23.0/-11.4 | 2052 / -167932 (+2946004/-3113936) | +145059/-94801/-190489/-27702 | 0.02 | -10.0 | DD |
| pb_daycaps | win5_loss1(arm2,keep.5,floor12) | P7 | +28.7/+7.5/+12.9/+14.9 | +1672 | +32.6/+17.7/+19.6 | -23.1/-11.4 | 2057 / -167484 (+2955584/-3123068) | +145059/-91941/-192901/-27702 | 0.03 | -10.0 | DD |
| pb_daycaps | win3_loss1(arm2,keep.5,floor12) | P7 | +28.7/+7.5/+12.9/+14.9 | -315 | +27.9/+12.0/+14.0 | -24.1/-5.3 | 2202 / -118223 (+3318877/-3437099) | +143211/-60801/-172932/-27702 | 0.01 | -10.0 | DD |
| pb_daycaps | win4_loss1(arm2,keep.5,floor12) | ALL | +25.6/+13.6/+11.0/+16.1 | -1497 | +21.6/+6.2/+11.5 | -24.2/-7.5 | 4394 / -118844 (+4420894/-4539738) | +167270/-63531/-176726/-45857 | 0.09 | -10.0 | DD |
| pb_daycaps | win5_loss1(arm2,keep.5,floor12) | ALL | +25.6/+13.6/+10.6/+16.1 | -1439 | +21.8/+6.0/+11.7 | -23.1/-8.0 | 4255 / -106687 (+4261297/-4367983) | +184525/-40302/-190656/-60254 | 0.10 | -10.0 | DD |


## Give-back (arm R x keep)

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_giveback | arm1_keep0.7(win5,loss2,floor12) | P7 | +6.9/+22.8/+30.0/-0.3 | +1823 | +12.4/+34.1/+5.6 | -24.9/-20.0 | 1810 / -287060 (+2364608/-2651668) | -29272/-52294/-177792/-27702 | 0.03 | +20.5 | DD |
| pb_giveback | arm2_keep0.7(win5,loss2,floor12) | ALL | +1.8/+0.2/+0.9/+8.1 | +161 | +2.4/+1.5/+8.6 | -18.9/+0.9 | 1443 / -179559 (+1269941/-1449500) | -22257/-26897/-104092/-26313 | 0.03 | +20.5 | DD |
| pb_giveback | arm2_keep0.7(win5,loss2,floor12) | P7 | -0.3/-0.6/-0.0/+8.1 | +479 | +1.3/+1.6/+9.6 | -19.9/-0.0 | 1231 / -188678 (+1143741/-1332419) | -24028/-28245/-108703/-27702 | 0.02 | +20.5 | DD |
| pb_giveback | arm1_keep0.6(win5,loss2,floor12) | P7 | +6.9/+20.5/+30.0/-0.3 | +282 | +7.8/+30.7/+0.7 | -18.3/-12.8 | 1734 / -232842 (+2238940/-2471782) | -5156/-23797/-176187/-27702 | 0.04 | +20.5 | DD |
| pb_giveback | arm1_keep0.3(win5,loss2,floor12) | P7 | -0.8/+16.5/+27.2/-0.3 | +320 | +0.3/+28.0/+0.8 | -8.2/-7.1 | 1441 / -157465 (+1639138/-1796603) | -6448/+22844/-146159/-27702 | 0.04 | +20.5 | DD |
| pb_giveback | arm1.5_keep0.3(win5,loss2,floor12) | P7 | -9.8/-0.6/+27.2/+8.1 | +1759 | -3.6/+31.4/+13.3 | -5.3/-10.7 | 1236 / -181971 (+1171339/-1353310) | -27181/+3672/-130760/-27702 | 0.04 | +20.5 | - |
| pb_giveback | arm1_keep0.3(win5,loss2,floor12) | ALL | -3.0/+17.3/+30.0/+0.5 | -370 | -4.3/+29.1/-0.8 | -1.4/-6.7 | 1937 / -152115 (+1919317/-2071432) | -9326/-3744/-139814/+769 | 0.09 | +20.5 | - |
| pb_giveback | arm1.5_keep0.8(win5,loss2,floor12) | K7 | -0.8/-6.6/+7.0/+7.2 | -1267 | -5.4/+2.8/+3.0 | -11.3/+6.1 | 1754 / -145458 (+1392416/-1537874) | -4417/-5716/-130008/-5317 | 0.03 | +20.5 | - |


## Week floor

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_weekfloor | floor6(win5,loss2,arm2/.5) | ALL | -2.6/+17.6/+9.9/+7.1 | -521 | -4.5/+8.2/+5.5 | -11.1/+3.1 | 1382 / -201649 (+1318167/-1519816) | +19351/-47772/-148725/-24504 | 0.05 | -2.5 | - |
| pb_weekfloor | floor6(win5,loss2,arm2/.5) | P7 | -2.6/+17.2/+9.9/+8.1 | -666 | -5.0/+7.8/+6.0 | -10.7/+4.0 | 1278 / -198418 (+1256909/-1455327) | +11401/-42284/-139833/-27702 | 0.07 | -2.5 | - |
| pb_weekfloor | floor10(win5,loss2,arm2/.5) | ALL | -5.2/-0.6/-0.0/+8.1 | -746 | -7.9/-2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | na | -2.5 | - |
| pb_weekfloor | floor8(win5,loss2,arm2/.5) | ALL | -5.2/+6.4/-0.0/+8.1 | -746 | -7.9/-2.6/+5.7 | -10.1/+5.6 | 1189 / -179294 (+1058584/-1237878) | -6542/-5539/-137197/-30015 | na | -2.5 | - |
| pb_weekfloor | floor14(win5,loss2,arm2/.5) | ALL | -5.2/-0.6/-0.0/+8.1 | -746 | -7.9/-2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | na | -2.5 | - |
| pb_weekfloor | floor16(win5,loss2,arm2/.5) | ALL | -5.2/-0.6/-0.0/+8.1 | -746 | -7.9/-2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | na | -2.5 | - |
| pb_weekfloor | floor20(win5,loss2,arm2/.5) | ALL | -5.2/-0.6/-0.0/+8.1 | -746 | -7.9/-2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | na | -2.5 | - |
| pb_weekfloor | floor12(win5,loss2,arm2/.5) | ALL | -5.2/-0.6/-0.0/+8.1 | -746 | -7.9/-2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | na | -2.5 | - |


## Lock R on base vs sized lots

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_rbasis | R_on_sized_lots | ALL | +37.6/-1.1/+40.8/+30.8 | +1751 | +41.1/+44.2/+34.7 | -17.3/-32.2 | 5372 / -221650 (+5736531/-5958181) | +115940/-89130/-228335/-20124 | 0.01 | -5.2 | DD |
| pb_rbasis | R_on_sized_lots | P7 | +38.5/-26.6/+36.1/+14.7 | +4488 | +46.7/+44.6/+26.0 | -33.8/-32.4 | 2606 / -220754 (+4151936/-4372689) | +120445/-112727/-200770/-27702 | 0.01 | -5.2 | DD |
| pb_rbasis | R_on_base_lots | ALL | -5.2/-0.6/-0.0/+8.1 | -746 | -7.9/-2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | na | -5.2 | - |
| pb_rbasis | R_on_base_lots | P7 | -5.2/-0.6/-0.0/+8.1 | -746 | -7.9/-2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | na | -5.2 | - |
| pb_rbasis | R_on_base_lots | K7 | -5.2/-0.6/-0.0/+8.1 | -746 | -7.9/-2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | na | -5.2 | - |
| pb_rbasis | R_on_sized_lots | K7 | -0.5/+1.0/+11.5/+16.0 | -2156 | -8.5/+4.4/+9.3 | -2.3/+5.5 | 3289 / -181584 (+2256763/-2438347) | -9277/-13065/-139118/-20124 | na | -5.2 | - |


## Intraday re-arm vs rest-of-day

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_rearm | resume_after_next_session | K7 | -9.4/-2.1/+2.7/+8.9 | -851 | -12.7/-0.2/+6.2 | -6.7/+5.5 | 914 / -178590 (+896234/-1074824) | -7741/-11715/-126063/-33071 | na | -20.4 | - |
| pb_rearm | resume_after_8h | K7 | -8.7/+2.2/+1.2/+9.4 | -1505 | -14.6/-4.1/+4.5 | -5.2/+7.9 | 1242 / -143840 (+1108461/-1252302) | +7378/-16303/-121962/-12953 | na | -20.4 | - |
| pb_rearm | resume_after_2h | P7 | -8.4/+2.5/-10.2/+8.5 | -1247 | -13.2/-15.1/+4.4 | -7.6/+11.6 | 1056 / -113424 (+835499/-948923) | -1880/+9333/-93175/-27702 | na | -20.4 | - |
| pb_rearm | resume_after_8h | P7 | -7.1/+6.1/-1.5/+8.1 | -2439 | -16.9/-10.7/-0.3 | +2.5/+12.6 | 1191 / -135003 (+1094036/-1229039) | -30124/+6142/-83319/-27702 | na | -20.4 | - |
| pb_rearm | resume_after_4h | P7 | -19.1/-5.9/-0.9/+2.9 | +335 | -17.8/+0.2/+4.0 | -0.8/+1.6 | 1109 / -138853 (+930311/-1069164) | -13727/+2134/-99558/-27702 | na | -20.4 | - |
| pb_rearm | resume_after_4h | K7 | -11.2/+6.3/-3.4/+10.7 | -1771 | -18.4/-10.1/+5.0 | -5.7/+10.2 | 1078 / -149054 (+1003640/-1152694) | -1430/-6510/-120568/-20546 | na | -20.4 | - |
| pb_rearm | resume_after_next_session | P7 | -14.7/+6.2/-6.8/+5.4 | -1952 | -22.9/-14.5/-1.3 | +1.3/+14.0 | 1065 / -89925 (+857163/-947088) | -7741/+11642/-66124/-27702 | na | -20.4 | - |
| pb_rearm | resume_after_8h | ALL | -10.6/+8.9/-0.2/+9.4 | -3199 | -24.2/-12.6/-1.7 | +8.1/+15.4 | 1257 / -108938 (+1155896/-1264834) | -15005/-2336/-78644/-12953 | na | -20.4 | - |


## Losing-streak halts (N stops -> off N hours)

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| streak_halt | 2stops_off_2h(+live) | K7 | -1.2/-0.5/+8.0/+12.6 | -207 | -2.0/+7.3/+11.9 | -5.4/+2.6 | 1477 / -171720 (+1230465/-1402185) | -10653/-2726/-131009/-27332 | na | na | - |
| streak_halt | 2stops_off_1h(+live) | K7 | +0.4/-1.5/+10.1/+12.8 | -835 | -2.5/+7.5/+10.2 | -8.0/+4.5 | 1433 / -161539 (+1204448/-1365987) | -670/-15569/-134532/-10768 | na | na | - |
| streak_halt | 3stops_off_8h(+live) | ALL | -5.2/-3.0/+1.5/+8.1 | +616 | -3.0/+3.5/+10.0 | -5.1/-1.1 | 1446 / -119245 (+1280343/-1399589) | +16027/+14291/-113300/-36264 | na | na | - |
| streak_halt | 2stops_off_4h(+live) | K7 | -4.0/-0.7/-0.4/+15.6 | -428 | -5.6/-1.9/+14.4 | -4.8/+3.5 | 1688 / -191822 (+1340837/-1532660) | -10214/-19974/-125602/-36033 | na | na | - |
| streak_halt | 3stops_off_1h(+live) | ALL | -5.2/-0.6/-1.4/+6.3 | -573 | -7.3/-3.5/+4.4 | -12.2/+3.2 | 1248 / -181137 (+1093941/-1275078) | -2441/-25015/-128008/-25672 | na | na | - |
| streak_halt | 3stops_off_1h(+live) | K7 | -5.2/-0.6/-1.4/+9.1 | -596 | -7.4/-3.6/+7.2 | -10.5/+4.4 | 1231 / -171634 (+1078356/-1249990) | -3184/-14789/-127989/-25672 | na | na | - |
| streak_halt | 3stops_off_1h(+live) | P7 | -5.2/-0.6/-0.0/+8.1 | -683 | -7.7/-2.4/+5.9 | -9.9/+5.3 | 1179 / -172937 (+1048999/-1221936) | -6854/-11744/-126636/-27702 | na | na | - |
| streak_halt | 3stops_off_2h(+live) | K7 | -5.2/-0.6/-2.8/+13.5 | -687 | -7.7/-5.3/+11.4 | -10.5/+5.4 | 1251 / -190690 (+1081224/-1271913) | -3944/-12401/-137933/-36411 | na | na | - |


## Combos

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_combo | win4_loss1.5_arm1.5_keep0.5_floor10 | P7 | +6.0/-0.3/+34.3/+6.4 | -167 | +5.5/+33.9/+5.8 | -4.1/-3.0 | 1690 / -117259 (+2166556/-2283815) | +44328/-64378/-69507/-27702 | 0.03 | +15.7 | DD |
| pb_combo | win5_loss2_arm2_keep0.7_floor12 | ALL | +1.8/+0.2/+0.9/+8.1 | +161 | +2.4/+1.5/+8.6 | -18.9/+0.9 | 1443 / -179559 (+1269941/-1449500) | -22257/-26897/-104092/-26313 | 0.02 | +15.7 | DD |
| pb_combo | win5_loss2_arm2_keep0.7_floor12 | P7 | -0.3/-0.6/-0.0/+8.1 | +479 | +1.3/+1.6/+9.6 | -19.9/-0.0 | 1231 / -188678 (+1143741/-1332419) | -24028/-28245/-108703/-27702 | 0.02 | +15.7 | DD |
| pb_combo | win3_loss1.5_arm1.5_keep0.5_floor8 | P7 | +6.0/+4.3/+30.9/+6.4 | -2787 | -3.9/+23.6/-3.5 | +3.1/+6.6 | 1789 / -39904 (+2443484/-2483388) | +59038/-8729/-62512/-27702 | 0.15 | +15.7 | - |
| pb_combo | win3_loss1_arm1_keep0.5_floor8 | P7 | +32.6/+7.5/+38.7/+6.6 | -3225 | +24.2/+31.0/-5.0 | -19.1/-5.0 | 2597 / -111240 (+4173208/-4284448) | +182664/-110527/-155675/-27702 | 0.15 | +15.7 | - |
| pb_combo | win5_lossoff_arm2_keep0.5_floor12 | K7 | -4.7/+5.1/-2.1/+9.8 | -130 | -5.2/-2.6/+9.4 | -8.5/+4.4 | 663 / -164355 (+759412/-923766) | -14065/-20999/-117415/-11876 | na | +15.7 | - |
| pb_combo | win6_loss3_arm2_keep0.5_floor14 | K7 | -3.9/+5.1/-1.9/+9.8 | -532 | -5.8/-3.8/+8.2 | -5.7/+5.8 | 732 / -174030 (+794711/-968742) | -14065/-10587/-121543/-27835 | 0.03 | +15.7 | - |
| pb_combo | win5_loss2_arm2_keep0.7_floor12 | K7 | -3.0/+0.2/+0.9/+8.1 | -1014 | -6.7/-2.6/+4.8 | -8.7/+6.4 | 1370 / -165433 (+1159609/-1325042) | -7169/-7661/-124289/-26313 | 0.07 | +15.7 | - |


## Quit-when-up: stack day win cap (+live pb)

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| comb_quit_up | stack_win$90000(+live pb) | ALL | -5.2/-0.6/-0.0/+8.1 | -746 | -7.9/-2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | na | -22.4 | - |
| comb_quit_up | stack_win$40000(+live pb) | ALL | -5.2/-0.6/-0.0/+8.1 | -858 | -8.4/-3.0/+5.3 | -15.1/+6.0 | 1638 / -152021 (+1501562/-1653583) | -17269/-20721/-117640/+3609 | na | -22.4 | - |
| comb_quit_up | stack_win$60000(+live pb) | ALL | -5.2/-0.6/-0.0/+8.1 | -895 | -8.5/-3.2/+5.2 | -9.1/+6.1 | 1210 / -174678 (+1081506/-1256184) | -7741/-18995/-126257/-21684 | na | -22.4 | - |
| comb_quit_up | stack_win$25000(+live pb) | ALL | -5.2/-0.6/+26.6/+8.1 | -3733 | -20.6/+15.9/-5.4 | -28.1/+10.1 | 3069 / +1109 (+3034987/-3033878) | +21343/-18887/-20004/+18657 | na | -22.4 | - |
| comb_quit_up | stack_win$15000(+live pb) | ALL | -36.7/-9.8/+39.3/+16.9 | -7378 | -82.9/+18.8/-11.2 | +18.6/+12.6 | 5608 / +30637 (+5659548/-5628910) | +48618/+32544/-87179/+36655 | na | -22.4 | - |


## Stack day loss cap (+live pb)

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| comb_dayloss | stack_loss$25000(+live pb) | ALL | -2.4/+3.2/-0.1/+9.9 | +2008 | +4.2/+6.3/+15.7 | -5.4/-3.0 | 1638 / -222397 (+1359205/-1581602) | -7145/-21595/-145886/-47772 | 0.02 | -47.1 | DD |
| comb_dayloss | stack_loss$15000(+live pb) | ALL | -3.1/+4.9/-4.7/-5.1 | +262 | -2.2/-3.7/-4.2 | -8.3/-4.5 | 3655 / -179903 (+3346364/-3526267) | +158374/-78700/-215449/-44128 | 0.15 | -47.1 | - |
| comb_dayloss | stack_loss$40000(+live pb) | ALL | -5.2/-0.6/-0.0/+8.1 | -746 | -7.9/-2.6/+5.7 | -10.1/+5.6 | 1186 / -169020 (+1054993/-1224014) | -7741/-7826/-126943/-26510 | na | -47.1 | - |
| comb_dayloss | stack_loss$8000(+live pb) | ALL | +12.2/+25.6/-25.2/-27.9 | -8984 | -26.8/-80.8/-84.8 | +41.0/+19.2 | 7489 / +207398 (+7545288/-7337890) | +443669/+74564/-274137/-36699 | na | -47.1 | - |


## Stack give-back (+live pb)

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| comb_giveback | stack_arm$45000_keep0.5(+live pb) | ALL | -5.2/-0.6/-0.0/+8.1 | -746 | -7.9/-2.6/+5.7 | -10.1/+5.6 | 1176 / -169905 (+1046602/-1216506) | -7741/-7826/-126636/-27702 | na | +10.7 | - |
| comb_giveback | stack_arm$30000_keep0.5(+live pb) | ALL | -5.2/-0.6/-0.0/+8.1 | -746 | -7.9/-2.6/+5.7 | -9.6/+5.6 | 1204 / -174846 (+1062781/-1237627) | -7741/-7826/-126792/-32487 | na | +10.7 | - |
| comb_giveback | stack_arm$45000_keep0.7(+live pb) | ALL | -5.2/-0.6/-0.0/+8.1 | -1644 | -11.5/-6.0/+2.6 | -4.5/+9.0 | 1240 / -147404 (+1116128/-1263532) | -7741/+8282/-121444/-26500 | na | +10.7 | - |
| comb_giveback | stack_arm$30000_keep0.7(+live pb) | ALL | -5.2/-0.6/-0.0/+8.1 | -3309 | -18.6/-12.8/-3.6 | -16.2/+16.0 | 1397 / -105832 (+1272586/-1378418) | -7741/+28439/-108495/-18035 | na | +10.7 | - |
| comb_giveback | stack_arm$20000_keep0.5(+live pb) | ALL | -5.2/+12.8/+32.8/+8.1 | -3707 | -20.5/+23.0/-5.3 | +0.2/+8.7 | 1789 / -147246 (+1612802/-1760048) | +19191/+2069/-148847/-19658 | na | +10.7 | - |
| comb_giveback | stack_arm$20000_keep0.7(+live pb) | ALL | -5.2/+15.5/+35.8/+5.3 | -7157 | -39.4/+15.0/-25.4 | -11.0/+20.6 | 2361 / -136656 (+2192540/-2329196) | -24355/+12204/-140441/+15936 | na | +10.7 | - |
| comb_giveback | stack_arm$10000_keep0.7(+live pb) | ALL | -32.6/-6.5/+35.8/+16.5 | -6773 | -72.6/+16.5/-8.8 | -4.8/+4.0 | 5187 / -139197 (+4956754/-5095951) | +45090/-64131/-121823/+1667 | na | +10.7 | - |
| comb_giveback | stack_arm$10000_keep0.5(+live pb) | ALL | -35.6/-10.1/+32.5/+16.4 | -8398 | -90.3/+5.2/-17.3 | +11.6/+17.8 | 4227 / -77438 (+4029102/-4106540) | +78525/-19842/-107543/-28578 | na | +10.7 | - |


## Stack week floor (+live pb)

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed vs NOLOCK list: n / P&L (win/loss) | removed P&L asia/london/nyam/nypm (the trades that would have followed) | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| comb_weekfloor | stack_floor$100000(+live pb) | ALL | -5.2/+0.5/-0.0/+8.1 | -746 | -7.9/-2.6/+5.7 | -10.1/+5.6 | 1229 / -170984 (+1101154/-1272137) | +3415/-15448/-133652/-25299 | 0.03 | -7.0 | - |
| comb_weekfloor | stack_floor$60000(+live pb) | ALL | -9.6/+12.0/+22.0/+8.1 | -559 | -11.7/+20.4/+6.3 | -11.4/-0.4 | 1819 / -227524 (+1709765/-1937289) | +8857/-72085/-145710/-18585 | na | -7.0 | - |
| comb_weekfloor | stack_floor$30000(+live pb) | ALL | +21.7/+19.5/+19.9/-7.2 | -1609 | +17.1/+15.3/-13.4 | +7.2/-13.5 | 4187 / -177663 (+4262387/-4440050) | +133506/-110625/-176706/-23837 | na | -7.0 | - |


## Exact-engine rows (S1b engine, ROLL-EXCL scoring; windows complete only): live, NOLOCK reference, R1 top-5

| row | set | L6M maxDD / d mean / cut vs live | PRE maxDD / d mean / cut vs live | X' maxDD / d mean / cut vs live | HOLD maxDD / d mean / cut vs live |
|--|--|--|--|--|--|
| LIVE (S1-COMB) | S1-COMB | 79907 / +0 / +0.0% | 140288 / +0 / +0.0% | 128944 / +0 / +0.0% | 99496 / +0 / +0.0% |
| NOLOCK reference | CDE_NOLOCK | 100720 / -2394 / -26.0% | 162725 / -992 / -16.0% | 117066 / +493 / +9.2% | 115787 / -817 / -16.4% |
| R1/pb_rbasis/R_on_sized_lots/ALL | CDE_R1_1 | not run yet | not run yet | not run yet | not run yet |
| R1/pb_rbasis/R_on_sized_lots/P7 | CDE_R1_2 | not run yet | not run yet | not run yet | not run yet |
| R1/pb_daycaps/win4_loss1(arm2,keep.5,floor12)/P7 | CDE_R1_3 | not run yet | not run yet | not run yet | not run yet |
| R1/pb_daycaps/win8_loss1(arm2,keep.5,floor12)/P7 | CDE_R1_4 | not run yet | not run yet | not run yet | not run yet |
| R1/pb_giveback/arm1_keep0.7(win5,loss2,floor12)/P7 | CDE_R1_5 | not run yet | not run yet | not run yet | not run yet |


NOLOCK reference: the live locks are doing real work; any setting that removes them is a reference row, never a candidate.


## Summary block: setting | live value | best on the state base | holds OOS? | change recommended | panel field

| setting | live value | best on the state base (first-order screen, equal mean) | holds OOS (dim WF eq cut) | change recommended | panel field |
|--|--|--|--|--|--|
| Day profit / loss caps | +5R / -2R per book | win4_loss1(arm2,keep.5,floor12) P7 (cut +33.7/+19.1/+20.9, d mean +2211) | -10.0 | candidate for exact; live stays until exact confirms | ComboLimits / MaxDayProfit, MaxDayLoss (per book) |
| Give-back arm / keep | arm 2R keep 50% | arm1_keep0.7(win5,loss2,floor12) P7 (cut +12.4/+34.1/+5.6, d mean +1823) | +20.5 | candidate for exact; live stays until exact confirms | GiveBackArmR / GiveBackKeepPct |
| Week floor | 12R per book | floor6(win5,loss2,arm2/.5) ALL (cut -4.5/+8.2/+5.5, d mean -521) | -2.5 | no (live stays) | ComboWeekFloorR |
| R basis | base lots | R_on_sized_lots ALL (cut +41.1/+44.2/+34.7, d mean +1751) | -5.2 | candidate for exact; live stays until exact confirms | v1.6 (R on sized lots not a field) |
| Halt scope in time | rest of day | resume_after_next_session K7 (cut -12.7/-0.2/+6.2, d mean -851) | -20.4 | no (live stays) | v1.6 code (re-arm after N h / next session) |
| Stack quit-when-up | none (PerBook only) | stack_win$90000(+live pb) ALL (cut -7.9/-2.6/+5.7, d mean -746) | -22.4 | no (live stays) | v1.6 code (LockScope Combined $ cap) |
| Stack day loss cap | none | stack_loss$25000(+live pb) ALL (cut +4.2/+6.3/+15.7, d mean +2008) | -47.1 | candidate for exact; live stays until exact confirms | v1.6 code |
| Stack give-back | none | stack_arm$45000_keep0.5(+live pb) ALL (cut -7.9/-2.6/+5.7, d mean -746) | +10.7 | no (live stays) | v1.6 code |
| Stack week floor | none | stack_floor$100000(+live pb) ALL (cut -7.9/-2.6/+5.7, d mean -746) | -7.0 | no (live stays) | v1.6 code |

WF of the picking procedure over the whole R1 grid: OOS maxDD cut +13.3% raw / -12.4% at equal mean (d mean -3797 $/wk, 148 weeks).


Worked examples (today's P7 -20,985 day halt and the K7 give-back halts): those are 2026-11-09 live trades, not in the frozen live file (ends 11-05) and not in the exact lists (end 2026-10); not reproducible here. The frozen-week and the 14 roll days: see the roll-day check below.


## Roll-day check (14 roll days; artifact = alive across the roll and exited by an artifact Target/Stop; ROLL-EXCL zeroes their P&L in all scores but the engine state in the exact runs saw them)

| run | artifact trades present | artifact trades with a large loss (<= -1R of the book) | same-book trades that followed on that label day | BookLock exits among them |
|--|--|--|--|--|
| S1-COMB live | 31 | 3 | 121 | 0 |
| CDE_NOLOCK | 27 | 3 | 152 | 0 |

Detail (S1-COMB live): K7 20230614 pnl 1199 Target then 5 trades; P7 20230614 pnl 8402 Target then 0 trades; U7 20230614 pnl 2403 Target then 1 trades; P7 20230913 pnl -425 Stop then 4 trades; K7 20230913 pnl 1199 Target then 3 trades; A7 20231213 pnl 1199 Target then 0 trades; P7 20231213 pnl 1199 Target then 1 trades; K7 20231213 pnl 1199 Target then 2 trades; K7 20240313 pnl 1199 Target then 0 trades; P7 20240313 pnl 4805 Target then 0 trades; K7 20240619 pnl 1199 Target then 0 trades; A7 20240619 pnl 1199 Target then 0 trades; P7 20240918 pnl -3178 Stop then 3 trades; K7 20240918 pnl -386 Stop then 9 trades; K7 20241219 pnl 164 Stop then 16 trades; P7 20241219 pnl 178 Stop then 8 trades; K7 20250320 pnl 1199 Target then 9 trades; P7 20250320 pnl 3601 Target then 6 trades; P7 20250618 pnl 1362 Stop then 5 trades; K7 20250618 pnl 143 Stop then 9 trades; A7 20250618 pnl -276 Stop then 1 trades; A7 20250918 pnl 1199 Target then 2 trades; H7 20250918 pnl 1199 Target then 2 trades; P7 20250918 pnl 8392 Target then 0 trades; K7 20250918 pnl 1199 Target then 6 trades; K7 20251217 pnl -186 Stop then 9 trades; P7 20251217 pnl -4169 StateCut then 4 trades; P7 20260318 pnl -16785 Stop then 5 trades; K7 20260318 pnl -4406 Stop then 11 trades; K7 20260916 pnl -6061 Stop then 0 trades; P7 20260916 pnl 4800 Target then 0 trades
