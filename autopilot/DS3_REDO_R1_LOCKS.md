# DS3_REDO_R1_LOCKS - T-STACK-REDO R1: locks on the state base (first version 2026-11-09 17:37Z)

> **Label: PRE-PROOF; post-hoc; Shadow only; no PASS claims. FIRST-ORDER SCREEN ONLY unless a row is in the exact table below. ROLL-EXCL: the 31 roll-artifact base trades are excluded from every number. STANDING RULE: every lock stays ON; "off" rows are reference rows only; the deliverable is the best SETTING (drawdown first at equal mean, holds OOS); if nothing beats the live setting the live setting stays.**

Method: the screen runs on the EXACT NOLOCK trade list (engine with the lock layer switched off, 33 window months; screen base = S1B-COMB) so any lock setting, tighter or looser than live, is replayed first-order (realized-only state: a lock triggers when a trade exits; the engine also marks open P&L and flattens, which the screen cannot see). Reference = the live setting = S1b-COMB exact list. Regression: the exact lock override with the live values reproduces S1-COMB 202605 trade for trade (672 trades, net 35,852). Day caps use realized P&L only (as live check_limits), give-back and week floor use realized + open P&L. R on base lots = planned lots x 60 pt x $20 (PE 8,400, KB/MV 2,400, HM/SM 4,800, PB/OD 1,200; x max(1, size mult)). Scope: PerBook = per-book values; stack ($) rows are Combined; "(+live pb)" = Combined on top of the live per-book locks. One-book scopes keep the live locks on the other books.

## Overall: top 15 settings by the joint equal-mean cut (min of L6M, PRE, X')

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed n / P&L (win/loss) | asia/london/nyam/nypm removed P&L | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_rbasis | R_on_sized_lots | ALL | +39.7/-2.8/+40.7/+22.8 | -171 | +39.4/+40.3/+22.3 | -20.8/-27.4 | 4168 / -24354 (+4600659/-4625013) | +140095/-89715/-83699/+8965 | 0.01 | +11.5 | DD |
| pb_rbasis | R_on_sized_lots | P7 | +40.5/-20.2/+34.8/+5.7 | +2874 | +45.9/+40.6/+14.2 | -34.3/-28.3 | 1416 / -38660 (+3023247/-3061906) | +135929/-117741/-58415/+1567 | 0.01 | +11.5 | DD |
| pb_daycaps | win4_loss1(arm2,keep.5,floor12) | P7 | +25.7/+8.2/+17.0/+6.1 | +384 | +26.7/+18.1/+7.3 | -21.3/-11.0 | 982 / -5626 (+2084847/-2090473) | +123917/-96041/-35069/+1567 | 0.01 | +10.4 | DD |
| pb_giveback | arm1.5_keep0.7(win5,loss2,floor12) | ALL | +5.4/+0.5/+31.2/-0.0 | +2134 | +11.8/+35.9/+6.8 | -7.3/-20.1 | 533 / -130555 (+462982/-593538) | -51362/-75405/-8237/+4449 | 0.01 | +10.9 | DD |
| pb_giveback | arm1.5_keep0.7(win5,loss2,floor12) | P7 | +3.9/+0.0/+31.2/+0.0 | +2060 | +10.2/+35.7/+6.6 | -5.2/-18.0 | 200 / -132631 (+293847/-426478) | -52613/-71604/-9980/+1567 | 0.01 | +10.9 | DD |
| pb_daycaps | win6_loss1(arm2,keep.5,floor12) | P7 | +25.7/+8.2/+17.0/+6.1 | -61 | +25.6/+16.8/+5.9 | -21.6/-9.6 | 933 / +21467 (+1990100/-1968633) | +140476/-74133/-46442/+1567 | 0.01 | +10.4 | DD |
| pb_daycaps | win5_loss1(arm2,keep.5,floor12) | P7 | +25.7/+8.2/+17.0/+6.1 | -61 | +25.6/+16.8/+5.9 | -21.6/-9.6 | 933 / +21467 (+1990100/-1968633) | +140476/-74133/-46442/+1567 | 0.01 | +10.4 | DD |
| pb_daycaps | win8_loss1(arm2,keep.5,floor12) | P7 | +25.7/+8.2/+17.0/+6.1 | -61 | +25.6/+16.8/+5.9 | -21.6/-9.6 | 933 / +21467 (+1990100/-1968633) | +140476/-74133/-46442/+1567 | 0.01 | +10.4 | DD |
| pb_combo | win5_loss2_arm2_keep0.7_floor12 | ALL | +1.5/+0.5/+0.0/+0.0 | +1014 | +4.8/+3.4/+3.4 | -0.3/-3.8 | 182 / -11881 (+136660/-148541) | -7444/-8854/-1196/+5614 | 0.01 | +27.7 | DD |
| pb_giveback | arm2_keep0.7(win5,loss2,floor12) | ALL | +1.5/+0.5/+0.0/+0.0 | +1014 | +4.8/+3.4/+3.4 | -0.3/-3.8 | 182 / -11881 (+136660/-148541) | -7444/-8854/-1196/+5614 | 0.01 | +10.9 | DD |
| pb_giveback | arm2_keep0.7(win5,loss2,floor12) | P7 | +0.0/+0.0/+0.0/+0.0 | +999 | +3.3/+3.3/+3.3 | -0.2/-3.7 | 67 / -17922 (+80321/-98243) | -7846/-2500/-9144/+1567 | 0.01 | +10.9 | DD |
| pb_combo | win5_loss2_arm2_keep0.7_floor12 | P7 | +0.0/+0.0/+0.0/+0.0 | +999 | +3.3/+3.3/+3.3 | -0.2/-3.7 | 67 / -17922 (+80321/-98243) | -7846/-2500/-9144/+1567 | 0.01 | +27.7 | DD |
| pb_giveback | arm1.5_keep0.6(win5,loss2,floor12) | ALL | +3.5/+0.0/+31.2/+0.0 | +630 | +5.5/+32.6/+2.1 | -2.7/-15.3 | 346 / -97037 (+332287/-429324) | -31529/-74314/+82/+8724 | 0.01 | +10.9 | DD |
| pb_giveback | arm1.5_keep0.6(win5,loss2,floor12) | P7 | +0.1/+0.0/+31.2/+0.0 | +592 | +2.1/+32.5/+2.0 | -1.2/-13.1 | 153 / -102366 (+231499/-333865) | -29324/-65403/-9206/+1567 | 0.01 | +10.9 | DD |
| pb_giveback | arm3_keep0.7(win5,loss2,floor12) | P7 | +0.0/+0.0/+0.0/+0.0 | +287 | +1.0/+1.0/+1.0 | -2.0/-1.0 | 28 / -9626 (+22778/-32403) | -983/-10083/-128/+1567 | 0.01 | +10.9 | DD |


## Daily caps (win R x loss R)

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed n / P&L (win/loss) | asia/london/nyam/nypm removed P&L | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_daycaps | win4_loss1(arm2,keep.5,floor12) | P7 | +25.7/+8.2/+17.0/+6.1 | +384 | +26.7/+18.1/+7.3 | -21.3/-11.0 | 982 / -5626 (+2084847/-2090473) | +123917/-96041/-35069/+1567 | 0.01 | +10.4 | DD |
| pb_daycaps | winoff_loss1(arm2,keep.5,floor12) | P7 | +25.7/+8.2/+17.0/+6.1 | -61 | +25.6/+16.8/+5.9 | -21.6/-9.6 | 933 / +21467 (+1990100/-1968633) | +140476/-74133/-46442/+1567 | na | +10.4 | DD |
| pb_daycaps | win6_loss1(arm2,keep.5,floor12) | P7 | +25.7/+8.2/+17.0/+6.1 | -61 | +25.6/+16.8/+5.9 | -21.6/-9.6 | 933 / +21467 (+1990100/-1968633) | +140476/-74133/-46442/+1567 | 0.01 | +10.4 | DD |
| pb_daycaps | win5_loss1(arm2,keep.5,floor12) | P7 | +25.7/+8.2/+17.0/+6.1 | -61 | +25.6/+16.8/+5.9 | -21.6/-9.6 | 933 / +21467 (+1990100/-1968633) | +140476/-74133/-46442/+1567 | 0.01 | +10.4 | DD |
| pb_daycaps | win8_loss1(arm2,keep.5,floor12) | P7 | +25.7/+8.2/+17.0/+6.1 | -61 | +25.6/+16.8/+5.9 | -21.6/-9.6 | 933 / +21467 (+1990100/-1968633) | +140476/-74133/-46442/+1567 | 0.01 | +10.4 | DD |
| pb_daycaps | win6_loss4(arm2,keep.5,floor12) | ALL | +0.0/+0.0/+0.0/+0.0 | +0 | +0.0/+0.0/+0.0 | +0.0/+0.0 | 0 / +0 (+0/+0) | +0/+0/+0/+0 | 0.01 | +10.4 | - |
| pb_daycaps | win6_lossoff(arm2,keep.5,floor12) | ALL | +0.0/+0.0/+0.0/+0.0 | +0 | +0.0/+0.0/+0.0 | +0.0/+0.0 | 0 / +0 (+0/+0) | +0/+0/+0/+0 | na | +10.4 | - |
| pb_daycaps | win8_loss3(arm2,keep.5,floor12) | ALL | +0.0/+0.0/+0.0/+0.0 | +0 | +0.0/+0.0/+0.0 | +0.0/+0.0 | 0 / +0 (+0/+0) | +0/+0/+0/+0 | 0.01 | +10.4 | - |


## Give-back (arm R x keep)

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed n / P&L (win/loss) | asia/london/nyam/nypm removed P&L | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_giveback | arm1.5_keep0.7(win5,loss2,floor12) | ALL | +5.4/+0.5/+31.2/-0.0 | +2134 | +11.8/+35.9/+6.8 | -7.3/-20.1 | 533 / -130555 (+462982/-593538) | -51362/-75405/-8237/+4449 | 0.01 | +10.9 | DD |
| pb_giveback | arm1.5_keep0.7(win5,loss2,floor12) | P7 | +3.9/+0.0/+31.2/+0.0 | +2060 | +10.2/+35.7/+6.6 | -5.2/-18.0 | 200 / -132631 (+293847/-426478) | -52613/-71604/-9980/+1567 | 0.01 | +10.9 | DD |
| pb_giveback | arm2_keep0.7(win5,loss2,floor12) | ALL | +1.5/+0.5/+0.0/+0.0 | +1014 | +4.8/+3.4/+3.4 | -0.3/-3.8 | 182 / -11881 (+136660/-148541) | -7444/-8854/-1196/+5614 | 0.01 | +10.9 | DD |
| pb_giveback | arm2_keep0.7(win5,loss2,floor12) | P7 | +0.0/+0.0/+0.0/+0.0 | +999 | +3.3/+3.3/+3.3 | -0.2/-3.7 | 67 / -17922 (+80321/-98243) | -7846/-2500/-9144/+1567 | 0.01 | +10.9 | DD |
| pb_giveback | arm1.5_keep0.6(win5,loss2,floor12) | ALL | +3.5/+0.0/+31.2/+0.0 | +630 | +5.5/+32.6/+2.1 | -2.7/-15.3 | 346 / -97037 (+332287/-429324) | -31529/-74314/+82/+8724 | 0.01 | +10.9 | DD |
| pb_giveback | arm1.5_keep0.6(win5,loss2,floor12) | P7 | +0.1/+0.0/+31.2/+0.0 | +592 | +2.1/+32.5/+2.0 | -1.2/-13.1 | 153 / -102366 (+231499/-333865) | -29324/-65403/-9206/+1567 | 0.01 | +10.9 | DD |
| pb_giveback | arm3_keep0.7(win5,loss2,floor12) | P7 | +0.0/+0.0/+0.0/+0.0 | +287 | +1.0/+1.0/+1.0 | -2.0/-1.0 | 28 / -9626 (+22778/-32403) | -983/-10083/-128/+1567 | 0.01 | +10.9 | DD |
| pb_giveback | arm3_keep0.7(win5,loss2,floor12) | ALL | +0.0/+0.0/+0.0/+0.0 | +153 | +0.5/+0.5/+0.5 | -1.1/-0.5 | 54 / -7517 (+38352/-45869) | -983/-12777/+1365/+4878 | 0.01 | +10.9 | DD |


## Week floor

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed n / P&L (win/loss) | asia/london/nyam/nypm removed P&L | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_weekfloor | floor8(win5,loss2,arm2/.5) | ALL | +0.0/+7.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 33 / -13521 (+26363/-39884) | +4510/-6015/-11270/-746 | na | +11.6 | - |
| pb_weekfloor | floor10(win5,loss2,arm2/.5) | ALL | +0.0/+0.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 20 / -4132 (+14381/-18513) | +3311/-8301/-709/+1567 | na | +11.6 | - |
| pb_weekfloor | floor12(win5,loss2,arm2/.5) | ALL | +0.0/+0.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 20 / -4132 (+14381/-18513) | +3311/-8301/-709/+1567 | na | +11.6 | - |
| pb_weekfloor | floor14(win5,loss2,arm2/.5) | ALL | +0.0/+0.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 20 / -4132 (+14381/-18513) | +3311/-8301/-709/+1567 | na | +11.6 | - |
| pb_weekfloor | floor20(win5,loss2,arm2/.5) | ALL | +0.0/+0.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 20 / -4132 (+14381/-18513) | +3311/-8301/-709/+1567 | na | +11.6 | - |
| pb_weekfloor | floor16(win5,loss2,arm2/.5) | ALL | +0.0/+0.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 20 / -4132 (+14381/-18513) | +3311/-8301/-709/+1567 | na | +11.6 | - |
| pb_weekfloor | flooroff(win5,loss2,arm2/.5) | ALL | +0.0/+0.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 20 / -4132 (+14381/-18513) | +3311/-8301/-709/+1567 | na | +11.6 | - |
| pb_weekfloor | floor8(win5,loss2,arm2/.5) | P7 | +0.0/+7.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 25 / -11126 (+22763/-33888) | +3311/-5998/-10006/+1567 | 0.01 | +11.6 | - |


## Lock R on base vs sized lots

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed n / P&L (win/loss) | asia/london/nyam/nypm removed P&L | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_rbasis | R_on_sized_lots | ALL | +39.7/-2.8/+40.7/+22.8 | -171 | +39.4/+40.3/+22.3 | -20.8/-27.4 | 4168 / -24354 (+4600659/-4625013) | +140095/-89715/-83699/+8965 | 0.01 | +11.5 | DD |
| pb_rbasis | R_on_sized_lots | P7 | +40.5/-20.2/+34.8/+5.7 | +2874 | +45.9/+40.6/+14.2 | -34.3/-28.3 | 1416 / -38660 (+3023247/-3061906) | +135929/-117741/-58415/+1567 | 0.01 | +11.5 | DD |
| pb_rbasis | R_on_base_lots | ALL | +0.0/+0.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 20 / -4132 (+14381/-18513) | +3311/-8301/-709/+1567 | na | +11.5 | - |
| pb_rbasis | R_on_base_lots | P7 | +0.0/+0.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 20 / -4132 (+14381/-18513) | +3311/-8301/-709/+1567 | 0.01 | +11.5 | - |
| pb_rbasis | R_on_base_lots | K7 | +0.0/+0.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 20 / -4132 (+14381/-18513) | +3311/-8301/-709/+1567 | na | +11.5 | - |
| pb_rbasis | R_on_sized_lots | K7 | -3.3/+1.6/+10.6/+8.0 | -2200 | -11.7/+3.4/+0.5 | -1.4/+2.4 | 2099 / +8073 (+1210131/-1202058) | +10446/-1039/-10299/+8965 | na | +11.5 | - |


## Intraday re-arm vs rest-of-day

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed n / P&L (win/loss) | asia/london/nyam/nypm removed P&L | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_rearm | resume_after_next_session | ALL | +0.0/+0.0/+0.0/+0.0 | -86 | -0.3/-0.3/-0.3 | +0.6/+0.3 | 13 / +2062 (+9586/-7524) | +3311/+19/-1637/+368 | 0.01 | -3.4 | - |
| pb_rearm | resume_after_next_session | K7 | +0.0/+0.0/+0.0/+0.0 | -86 | -0.3/-0.3/-0.3 | +0.6/+0.3 | 16 / -4666 (+11983/-16649) | +3311/-8294/-51/+368 | 0.01 | -3.4 | - |
| pb_rearm | resume_after_2h | P7 | +0.0/+0.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 20 / -4132 (+14381/-18513) | +3311/-8301/-709/+1567 | na | -3.4 | - |
| pb_rearm | resume_after_next_session | P7 | +0.0/+0.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 18 / +1784 (+11983/-10199) | +3311/+12/-3106/+1567 | na | -3.4 | - |
| pb_rearm | resume_after_4h | P7 | +0.0/+0.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/-0.2 | 22 / -12374 (+14381/-26755) | -4931/-8301/-709/+1567 | na | -3.4 | - |
| pb_rearm | resume_after_2h | K7 | +0.0/+0.0/+0.0/+0.0 | -257 | -0.9/-0.9/-0.9 | +1.9/+0.9 | 15 / -562 (+13182/-13744) | +4258/-8321/-96/+3596 | na | -3.4 | - |
| pb_rearm | resume_after_2h | ALL | +0.0/+0.0/+0.0/+0.0 | -257 | -0.9/-0.9/-0.9 | +1.9/+0.9 | 15 / -562 (+13182/-13744) | +4258/-8321/-96/+3596 | na | -3.4 | - |
| pb_rearm | resume_after_4h | ALL | +0.1/+0.0/-0.9/+2.7 | -175 | -0.5/-1.5/+2.1 | +1.3/+0.1 | 40 / -12976 (+25170/-38146) | -6929/-8935/-709/+3596 | na | -3.4 | - |


## Losing-streak halts (N stops -> off N hours)

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed n / P&L (win/loss) | asia/london/nyam/nypm removed P&L | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| streak_halt | 3stops_off_8h(+live) | P7 | +0.0/+0.0/+9.8/+0.0 | -108 | -0.4/+9.5/-0.4 | +0.8/-1.3 | 28 / -5526 (+30707/-36233) | +7644/-3823/-10913/+1567 | na | na | - |
| streak_halt | 3stops_off_4h(+live) | P7 | +0.0/+0.0/+9.8/+0.0 | -108 | -0.4/+9.5/-0.4 | +0.8/-1.6 | 26 / -11057 (+25175/-36233) | +5709/-3823/-14510/+1567 | na | na | - |
| streak_halt | 3stops_off_2h(+live) | P7 | +0.0/+0.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 22 / -5653 (+16778/-22431) | +5709/-12220/-709/+1567 | na | na | - |
| streak_halt | 3stops_off_1h(+live) | P7 | +0.0/+0.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 22 / -5653 (+16778/-22431) | +5709/-12220/-709/+1567 | na | na | - |
| streak_halt | 4stops_off_8h(+live) | P7 | +0.0/+0.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 20 / -4132 (+14381/-18513) | +3311/-8301/-709/+1567 | na | na | - |
| streak_halt | 4stops_off_4h(+live) | P7 | +0.0/+0.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 20 / -4132 (+14381/-18513) | +3311/-8301/-709/+1567 | na | na | - |
| streak_halt | 4stops_off_2h(+live) | P7 | +0.0/+0.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 20 / -4132 (+14381/-18513) | +3311/-8301/-709/+1567 | na | na | - |
| streak_halt | 4stops_off_1h(+live) | P7 | +0.0/+0.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 20 / -4132 (+14381/-18513) | +3311/-8301/-709/+1567 | na | na | - |


## Combos

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed n / P&L (win/loss) | asia/london/nyam/nypm removed P&L | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| pb_combo | win5_loss2_arm2_keep0.7_floor12 | ALL | +1.5/+0.5/+0.0/+0.0 | +1014 | +4.8/+3.4/+3.4 | -0.3/-3.8 | 182 / -11881 (+136660/-148541) | -7444/-8854/-1196/+5614 | 0.01 | +27.7 | DD |
| pb_combo | win5_loss2_arm2_keep0.7_floor12 | P7 | +0.0/+0.0/+0.0/+0.0 | +999 | +3.3/+3.3/+3.3 | -0.2/-3.7 | 67 / -17922 (+80321/-98243) | -7846/-2500/-9144/+1567 | 0.01 | +27.7 | DD |
| pb_combo | win8_loss3_arm3_keep0.5_floor16 | ALL | +0.0/+0.0/+0.0/+0.0 | +0 | +0.0/+0.0/+0.0 | +0.0/+0.0 | 0 / +0 (+0/+0) | +0/+0/+0/+0 | 0.01 | +27.7 | - |
| pb_combo | win5_lossoff_arm2_keep0.5_floor12 | ALL | +0.0/+0.0/+0.0/+0.0 | +0 | +0.0/+0.0/+0.0 | +0.0/+0.0 | 0 / +0 (+0/+0) | +0/+0/+0/+0 | na | +27.7 | - |
| pb_combo | win5_lossoff_arm2_keep0.5_floor12 | K7 | +0.0/+0.0/+0.0/+0.0 | +0 | +0.0/+0.0/+0.0 | +0.0/+0.0 | 3 / -6728 (+2398/-9125) | +0/-8313/+1585/+0 | na | +27.7 | - |
| pb_combo | win8_loss3_arm3_keep0.5_floor16 | K7 | +0.0/+0.0/+0.0/+0.0 | +0 | +0.0/+0.0/+0.0 | +0.0/+0.0 | 3 / -6728 (+2398/-9125) | +0/-8313/+1585/+0 | 0.01 | +27.7 | - |
| pb_combo | win6_loss3_arm2_keep0.5_floor14 | ALL | +0.0/+0.0/+0.0/+0.0 | +0 | +0.0/+0.0/+0.0 | +0.0/+0.0 | 0 / +0 (+0/+0) | +0/+0/+0/+0 | 0.01 | +27.7 | - |
| pb_combo | win6_loss3_arm2_keep0.5_floor14 | K7 | +0.0/+0.0/+0.0/+0.0 | +0 | +0.0/+0.0/+0.0 | +0.0/+0.0 | 3 / -6728 (+2398/-9125) | +0/-8313/+1585/+0 | 0.01 | +27.7 | - |


## Quit-when-up: stack day win cap (+live pb)

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed n / P&L (win/loss) | asia/london/nyam/nypm removed P&L | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| comb_quit_up | stack_win$90000(+live pb) | ALL | +0.0/+0.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 20 / -4132 (+14381/-18513) | +3311/-8301/-709/+1567 | 0.01 | -5.2 | - |
| comb_quit_up | stack_win$60000(+live pb) | ALL | +0.0/+0.0/+0.0/+0.0 | -258 | -0.9/-0.9/-0.9 | +1.1/+0.9 | 49 / -14700 (+43286/-57986) | +3311/-23101/-97/+5187 | na | -5.2 | - |
| comb_quit_up | stack_win$25000(+live pb) | ALL | +0.0/+0.0/+25.9/+0.0 | -5992 | -25.8/+6.8/-25.8 | -23.6/+17.7 | 1785 / +138000 (+1805816/-1667816) | +27342/-28024/+103805/+34877 | na | -5.2 | - |
| comb_quit_up | stack_win$40000(+live pb) | ALL | +0.0/+0.0/+0.0/+0.0 | -6436 | -28.3/-28.3/-28.3 | -33.1/+28.3 | 412 / -9212 (+401009/-410221) | -6217/-33504/+10244/+20264 | na | -5.2 | - |
| comb_quit_up | stack_win$15000(+live pb) | ALL | -36.7/-9.8/+39.3/+17.4 | -8115 | -89.3/+16.0/-14.4 | +26.4/+14.4 | 4449 / +169220 (+4442103/-4272883) | +59368/+28794/+13812/+67246 | na | -5.2 | - |


## Stack day loss cap (+live pb)

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed n / P&L (win/loss) | asia/london/nyam/nypm removed P&L | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| comb_dayloss | stack_loss$40000(+live pb) | ALL | +0.0/+0.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 30 / -3247 (+22773/-26020) | +3311/-8301/-1016/+2759 | 0.01 | -21.5 | - |
| comb_dayloss | stack_loss$25000(+live pb) | ALL | -5.4/+4.8/-0.1/+0.9 | +719 | -2.8/+2.3/+3.3 | -7.0/-1.5 | 499 / -67339 (+336095/-403433) | +3908/-31799/-22324/-17124 | na | -21.5 | - |
| comb_dayloss | stack_loss$15000(+live pb) | ALL | -7.2/+8.6/-3.3/-13.2 | -1336 | -12.4/-8.2/-18.6 | -16.6/-2.0 | 2595 / +15998 (+2417013/-2401014) | +168290/-107467/-34729/-10095 | na | -21.5 | - |
| comb_dayloss | stack_loss$8000(+live pb) | ALL | +18.2/+24.3/-17.3/-38.1 | -11154 | -32.3/-89.8/-123.4 | +53.1/+30.8 | 6571 / +468951 (+6770689/-6301738) | +438676/+88500/-59166/+941 | na | -21.5 | - |


## Stack give-back (+live pb)

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed n / P&L (win/loss) | asia/london/nyam/nypm removed P&L | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| comb_giveback | stack_arm$30000_keep0.5(+live pb) | ALL | +0.0/+0.0/+0.0/+0.0 | -32 | -0.1/-0.1/-0.1 | +1.6/+0.1 | 27 / -5971 (+17972/-23943) | +3311/-8301/-696/-284 | 0.01 | +22.5 | - |
| comb_giveback | stack_arm$45000_keep0.5(+live pb) | ALL | +0.0/+0.0/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 20 / -4132 (+14381/-18513) | +3311/-8301/-709/+1567 | 0.01 | +22.5 | - |
| comb_giveback | stack_arm$30000_keep0.7(+live pb) | ALL | +0.0/+0.0/+0.0/+0.0 | -690 | -2.4/-2.4/-2.4 | +8.5/+2.4 | 182 / +72188 (+198390/-126203) | +3311/+27900/+30338/+10639 | na | +22.5 | - |
| comb_giveback | stack_arm$45000_keep0.7(+live pb) | ALL | +0.0/+0.0/+0.0/+0.0 | -1101 | -3.9/-3.9/-3.9 | +8.2/+3.9 | 80 / +20327 (+81510/-61182) | +3311/+10068/+3554/+3394 | na | +22.5 | - |
| comb_giveback | stack_arm$20000_keep0.5(+live pb) | ALL | -8.6/+12.2/+33.9/+0.0 | -1939 | -16.3/+29.2/-7.1 | +14.6/-3.7 | 495 / -10427 (+415344/-425771) | +26262/-9456/-22601/-4631 | na | +22.5 | - |
| comb_giveback | stack_arm$20000_keep0.7(+live pb) | ALL | +5.0/+16.2/+37.5/-3.1 | -6308 | -21.2/+20.2/-31.5 | +6.0/+11.3 | 1115 / +15702 (+968532/-952830) | -962/-10428/-10487/+37580 | na | +22.5 | - |
| comb_giveback | stack_arm$10000_keep0.7(+live pb) | ALL | -29.8/-4.3/+37.1/+7.5 | -8325 | -81.6/+12.0/-29.5 | -6.6/+12.1 | 3954 / +61125 (+3713412/-3652287) | +74223/-79045/+43979/+21968 | na | +22.5 | - |
| comb_giveback | stack_arm$10000_keep0.5(+live pb) | ALL | -32.3/-6.2/+32.5/+8.3 | -8661 | -88.1/+4.1/-30.3 | -5.1/+13.3 | 2864 / +44986 (+2705351/-2660365) | +83633/-29332/+3153/-12467 | na | +22.5 | - |


## Stack week floor (+live pb)

| technique | setting | scope | (a) maxDD cut L6M/HOLD/PRE/X' | d mean L6M | (b) eq-mean cut L6M/PRE/X' | worst-20 cut (b) L6M/PRE | removed n / P&L (win/loss) | asia/london/nyam/nypm removed P&L | placebo p | WF dim eq cut | pass |
|--|--|--|--|--|--|--|--|--|--|--|--|
| comb_weekfloor | stack_floor$100000(+live pb) | ALL | +0.0/-0.2/+0.0/+0.0 | -108 | -0.4/-0.4/-0.4 | +0.8/+0.4 | 72 / -3906 (+68933/-72839) | +15772/-15924/-7724/+3970 | na | +6.8 | - |
| comb_weekfloor | stack_floor$60000(+live pb) | ALL | -15.6/+7.2/+22.0/+0.0 | -630 | -18.1/+20.2/-2.2 | +4.0/-3.8 | 661 / -59850 (+673414/-733265) | +19795/-69770/-20175/+10300 | na | +6.8 | - |
| comb_weekfloor | stack_floor$30000(+live pb) | ALL | +19.9/+20.8/+18.0/-16.1 | -3919 | +7.5/+5.3/-34.2 | +15.9/-5.3 | 2965 / -36407 (+3108600/-3145007) | +146195/-117759/-68457/+3614 | na | +6.8 | - |


## Exact-engine rows (S1b engine, ROLL-EXCL scoring; windows complete only): live, NOLOCK reference, R1 top-5

| row | set | L6M maxDD / d mean / cut vs live | PRE maxDD / d mean / cut vs live | X' maxDD / d mean / cut vs live | HOLD maxDD / d mean / cut vs live |
|--|--|--|--|--|--|
| LIVE (S1-COMB) | S1-COMB | 79907 / +0 / +0.0% | 140288 / +0 / +0.0% | 128944 / +0 / +0.0% | 99496 / +0 / +0.0% |
| NOLOCK reference | CDE_NOLOCK | not run yet | not run yet | not run yet | not run yet |
| R1/pb_rbasis/R_on_sized_lots/ALL | CDE_R1_1 | not run yet | not run yet | not run yet | not run yet |
| R1/pb_rbasis/R_on_sized_lots/P7 | CDE_R1_2 | not run yet | not run yet | not run yet | not run yet |
| R1/pb_daycaps/win4_loss1(arm2,keep.5,floor12)/P7 | CDE_R1_3 | not run yet | not run yet | not run yet | not run yet |
| R1/pb_giveback/arm1.5_keep0.7(win5,loss2,floor12)/ALL | CDE_R1_4 | not run yet | not run yet | not run yet | not run yet |
| R1/pb_giveback/arm1.5_keep0.7(win5,loss2,floor12)/P7 | CDE_R1_5 | not run yet | not run yet | not run yet | not run yet |


NOLOCK reference: the live locks are doing real work; any setting that removes them is a reference row, never a candidate.


## Summary block: setting | live value | best on the state base | holds OOS? | change recommended | panel field

| setting | live value | best on the state base (first-order screen, equal mean) | holds OOS (dim WF eq cut) | change recommended | panel field |
|--|--|--|--|--|--|
| Day profit / loss caps | +5R / -2R per book | win4_loss1(arm2,keep.5,floor12) P7 (cut +26.7/+18.1/+7.3, d mean +384) | +10.4 | candidate for exact; live stays until exact confirms | ComboLimits / MaxDayProfit, MaxDayLoss (per book) |
| Give-back arm / keep | arm 2R keep 50% | arm1.5_keep0.7(win5,loss2,floor12) ALL (cut +11.8/+35.9/+6.8, d mean +2134) | +10.9 | candidate for exact; live stays until exact confirms | GiveBackArmR / GiveBackKeepPct |
| Week floor | 12R per book | floor8(win5,loss2,arm2/.5) ALL (cut -0.4/-0.4/-0.4, d mean -108) | +11.6 | no (live stays) | ComboWeekFloorR |
| R basis | base lots | R_on_sized_lots ALL (cut +39.4/+40.3/+22.3, d mean -171) | +11.5 | candidate for exact; live stays until exact confirms | v1.6 (R on sized lots not a field) |
| Halt scope in time | rest of day | resume_after_next_session ALL (cut -0.3/-0.3/-0.3, d mean -86) | -3.4 | no (live stays) | v1.6 code (re-arm after N h / next session) |
| Stack quit-when-up | none (PerBook only) | stack_win$90000(+live pb) ALL (cut -0.4/-0.4/-0.4, d mean -108) | -5.2 | no (live stays) | v1.6 code (LockScope Combined $ cap) |
| Stack day loss cap | none | stack_loss$40000(+live pb) ALL (cut -0.4/-0.4/-0.4, d mean -108) | -21.5 | no (live stays) | v1.6 code |
| Stack give-back | none | stack_arm$30000_keep0.5(+live pb) ALL (cut -0.1/-0.1/-0.1, d mean -32) | +22.5 | no (live stays) | v1.6 code |
| Stack week floor | none | stack_floor$100000(+live pb) ALL (cut -0.4/-0.4/-0.4, d mean -108) | +6.8 | no (live stays) | v1.6 code |

WF of the picking procedure over the whole R1 grid: OOS maxDD cut -12.2% raw / -27.7% at equal mean (d mean -2010 $/wk, 148 weeks).


Worked examples (today's P7 -20,985 day halt and the K7 give-back halts): those are 2026-11-09 live trades, not in the frozen live file (ends 11-05) and not in the exact lists (end 2026-10); not reproducible here. The frozen-week and the 14 roll days: see the roll-day check below.


## Roll-day check (14 roll days; artifact = alive across the roll and exited by an artifact Target/Stop; ROLL-EXCL zeroes their P&L in all scores but the engine state in the exact runs saw them)

| run | artifact trades present | artifact trades with a large loss (<= -1R of the book) | same-book trades that followed on that label day | BookLock exits among them |
|--|--|--|--|--|
| S1-COMB live | 31 | 3 | 121 | 0 |
| CDE_NOLOCK | 0 | 0 | 0 | 0 |

Detail (S1-COMB live): K7 20230614 pnl 1199 Target then 5 trades; P7 20230614 pnl 8402 Target then 0 trades; U7 20230614 pnl 2403 Target then 1 trades; P7 20230913 pnl -425 Stop then 4 trades; K7 20230913 pnl 1199 Target then 3 trades; A7 20231213 pnl 1199 Target then 0 trades; P7 20231213 pnl 1199 Target then 1 trades; K7 20231213 pnl 1199 Target then 2 trades; K7 20240313 pnl 1199 Target then 0 trades; P7 20240313 pnl 4805 Target then 0 trades; K7 20240619 pnl 1199 Target then 0 trades; A7 20240619 pnl 1199 Target then 0 trades; P7 20240918 pnl -3178 Stop then 3 trades; K7 20240918 pnl -386 Stop then 9 trades; K7 20241219 pnl 164 Stop then 16 trades; P7 20241219 pnl 178 Stop then 8 trades; K7 20250320 pnl 1199 Target then 9 trades; P7 20250320 pnl 3601 Target then 6 trades; P7 20250618 pnl 1362 Stop then 5 trades; K7 20250618 pnl 143 Stop then 9 trades; A7 20250618 pnl -276 Stop then 1 trades; A7 20250918 pnl 1199 Target then 2 trades; H7 20250918 pnl 1199 Target then 2 trades; P7 20250918 pnl 8392 Target then 0 trades; K7 20250918 pnl 1199 Target then 6 trades; K7 20251217 pnl -186 Stop then 9 trades; P7 20251217 pnl -4169 StateCut then 4 trades; P7 20260318 pnl -16785 Stop then 5 trades; K7 20260318 pnl -4406 Stop then 11 trades; K7 20260916 pnl -6061 Stop then 0 trades; P7 20260916 pnl 4800 Target then 0 trades
