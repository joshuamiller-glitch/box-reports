# DS3_WORKS_C - T-WORKS Part C (P7 anatomy), W-C, page2026-11-11 15:13Z (C1 anatomy; C2-C4 running)
Label: PRE-PROOF, post-hoc, descriptive, Shadow only, no PASS claim. Prereg autopilot/WORKS_C_PREREG.md (sha in DECISIONS.md 13:35Z). Source: the exact LPB_BASE trade list (live panel base: P7 day cap 8,400, 7/4/4, P7 cut 40/5x/w5/p3, no JN04 dials), 4,958 P7 trades 2023-04..2026-10, plus the 53 P7 trades of the frozen live week 11-01..05 (data/live_frozen reconstructed file; live fees proxied at $4.84 per contract). Features are causal at the signal second (NQ 1-min bars, ER(20) on 5-min, atr_rel = 5-min ATR over its 20-day norm, LOT state = P7 shadow Calmar over the last 10 label days from the same list). Code code/th_works/c1_build.py, c1_cells.py, c1_excess.py, c1_page.py; table /mnt/l2/l2vast/_th_works/c/c1_cells.csv.

## C1 in plain sentences
1. P7 earns $897k over the 3.5 years in this base, $237k in L6M, and $0k in the live week (28 targets, 24 cuts, 1 BookLock). Its 20 worst weeks lose $552k together. Winners are targets at a flat 60 points (mean about +$4,000 per trade in L6M) and losers are StateCuts at a mean of about -$3,000 per trade; P7 wins only about 45 percent of its trades, so the week is decided by the cut rate.
2. A worst-20 week is not a busy week (26.5 P7 trades in both the worst and the other weeks). It is a week where 62 percent of trades end as StateCuts against 50 percent in other weeks, i.e. the same entries, but the trend continues through the cut instead of reverting to target.
3. Where the worst weeks sit (excess loss = worst-week net minus what the same cell earns per trade in other weeks): Asia is the largest carrier (284 trades in worst weeks, mean -$1,475 against +$580 in other weeks, 76 percent of the worst-20 loss; Asia is also where 80 percent of the 3.5-year profit comes from). By lots, 7-lot trades (all Asia in the live table) lose -$3,557 per trade in worst weeks against +$1,037 otherwise: 98 trades carry -$349k of the -$552k. 4-lot trades are flat over the whole history (-$3 per trade outside worst weeks) and lose -$1,240 in worst weeks.
4. Trend state matters, a result that matches the live week: signals taken WITH a session move of more than 1 ATR (the trend is already running in the trade direction, 3,270 trades) carry 66 percent of the worst-20 loss, and entries after a P7 loss, within 30 minutes of the last P7 exit, and with K7/U7/M7 already open on the same side are all over-represented. These are one regime seen from several sides: a trending Asia session where P7 keeps re-entering the same direction, gets cut, and re-enters. In L6M the worst 5 weeks (202644, 202631, 202636, 202635, 202621) show the same shape: with-trend, short side (87 percent of the L6M worst-5 loss is on the short side), inside 30 minutes of the last exit (96 percent), third-or-later trade of the session (72 percent).
5. What the table says about the dials: LOT state "cold" (Calmar10 < 1) is true for 3,000 of 4,958 trades, and cold trades earn MORE per trade in L6M (+$357) than warm ones (+$55) while also carrying 73 percent of the worst-20 loss. So the LOT dial (halve when cold) cuts both the winners and the losers of a state that is cold 60 percent of the time; it is a drawdown dial, not a profit dial, and in the live week all 53 P7 trades were taken cold (Calmar10 mean 0.07) so the JN04 LOT dial would have been halving lots all week while 28 targets paid +$159k (this is an inference from the LPB shadow Calmar, to be confirmed by replaying JN04RM on the live week). This is the same finding as the loss-cut page: the dials are right in chop and wrong in trend.
6. ER(20) and atr_rel do not separate the carriers cleanly. ER above 0.45 has the worst per-trade loss in worst weeks (-$2,269 against +$798 otherwise) but ER below 0.15 loses little in worst weeks (-$208 per trade); atr_rel above 1.6 is the only atr bucket negative in L6M (-$373 per trade, -$70k net) but earned +$27 per trade over 3.5 years. The live week was atr_rel above 1.6 for 27 of 53 trades and made +$39k there. So REG (atr_rel >= 1.3) is a poor stand-alone chop/trend flag for P7; the cleaner conditional flags in the table are "with-trend entry" and "same-side re-entry inside 30 minutes".
7. Side: shorts carry 54 percent of the 3.5-year worst-week loss and 87 percent in L6M; the whole L6M bad stretch is short Asia (308 trades, +$956 other weeks, -$1,175 in worst-5 weeks).
8. Live week: 53 trades, +$84.8k net of proxy fees. 24 StateCuts/PolicyCuts cost -$74k and 28 targets made +$159k. 33 of 53 trades were the 3rd or later P7 trade of the session, 29 were taken inside 30 minutes of the previous P7 exit (+$52.9k), 33 were with-trend. The with-trend and within-30-minutes cells were the winners that week; in the five worst L6M weeks the same cells were the losers. That is the regime flag problem in one sentence: the same cell wins in a trend that persists and loses when it stalls, so a causal flag must be about persistence of the session move, not about the cell.

## Worst-20 P7 weeks of the 3.5 years (LPB_BASE trades)
| ISO week | P7 trades | net $ | StateCut share % | Asia share % | mean lots | mean atr_rel |
|---|---|---|---|---|---|---|
| 202644 | 40 | -43324 | 70 | 78 | 4.0 | 1.34 |
| 202411 | 19 | -41863 | 58 | 42 | 3.6 | 1.54 |
| 202528 | 25 | -34733 | 72 | 48 | 3.2 | 1.13 |
| 202331 | 26 | -31799 | 58 | 35 | 3.7 | 1.94 |
| 202436 | 35 | -31352 | 66 | 46 | 3.3 | 1.66 |
| 202515 | 73 | -30999 | 55 | 66 | 3.5 | 2.93 |
| 202329 | 14 | -29606 | 64 | 43 | 3.4 | 1.69 |
| 202604 | 24 | -29549 | 71 | 46 | 3.5 | 1.81 |
| 202409 | 24 | -28036 | 62 | 33 | 3.0 | 1.49 |
| 202517 | 32 | -27072 | 53 | 59 | 3.8 | 0.94 |
| 202541 | 22 | -25793 | 64 | 45 | 3.8 | 1.45 |
| 202434 | 20 | -24356 | 70 | 45 | 3.3 | 1.15 |
| 202533 | 16 | -24142 | 62 | 50 | 3.2 | 1.40 |
| 202447 | 16 | -23135 | 62 | 75 | 4.6 | 1.18 |
| 202318 | 10 | -22701 | 70 | 60 | 4.9 | 1.13 |
| 202428 | 15 | -22213 | 60 | 60 | 3.6 | 1.43 |
| 202631 | 42 | -21798 | 60 | 64 | 3.8 | 1.29 |
| 202606 | 39 | -21032 | 62 | 59 | 3.7 | 2.14 |
| 202326 | 21 | -19455 | 67 | 24 | 2.7 | 1.70 |
| 202346 | 16 | -18651 | 62 | 44 | 3.3 | 1.13 |

## The P7 table (every cell: all 3.5 years, L6M, the live week, and the share of the worst-20-week loss it carries)
Cell definitions: ER bucket = ER(20) of 5-min closes at the signal; atr_rel = 5-min ATR(14) / 20-day median of daily medians; LOT cold = P7 shadow Calmar over the previous 10 label days < 1.0; P7 order = 1st / 2nd / 3rd or later P7 signal of the same session-day; since last P7 exit = minutes between the previous P7 exit and this signal; side vs session move = (signal close minus first close of the session) x side in 5-min ATRs; K7/U7/M7 open = another of those books holds lots at the signal second, same side or opposite. The "exit" rows are outcomes, not features.

| cut | cell | n 3.5y | net $k | mean $/trade | win % | n L6M | net $k | mean | win % | n live wk | net $k | mean | win % | worst-20-wk net $k | share of worst-20 loss % |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| session | asia | 2246 | +719 | +320 | 45 | 558 | +202 | +362 | 47 | 31 | +69 | +2220 | 55 | -419 | 76 |
| session | london | 1520 | +224 | +147 | 45 | 330 | +58 | +175 | 47 | 15 | +0 | +9 | 40 | -76 | 14 |
| session | nyam | 1192 | -46 | -38 | 44 | 129 | -23 | -179 | 42 | 7 | +16 | +2266 | 71 | -57 | 10 |
| lots | 1 | 879 | +154 | +175 | 49 | 145 | +46 | +317 | 54 | 1 | +1 | +1195 | 100 | +1 | -0 |
| lots | 2 | 1212 | -99 | -82 | 40 | 232 | +1 | +4 | 42 | 7 | +1 | +148 | 43 | -44 | 8 |
| lots | 3 | 245 | +485 | +1979 | 74 | 42 | +102 | +2424 | 81 | 2 | +7 | +3590 | 100 | +44 | -8 |
| lots | 4 | 1764 | -243 | -138 | 40 | 394 | -32 | -81 | 42 | 24 | +8 | +351 | 42 | -238 | 43 |
| lots | 5 | 61 | +224 | +3678 | 79 | 15 | +80 | +5323 | 93 | 3 | +12 | +3946 | 67 | +34 | -6 |
| lots | 7 | 797 | +376 | +472 | 46 | 189 | +40 | +213 | 43 | 15 | +43 | +2879 | 60 | -349 | 63 |
| ER(20) 5-min | .15-.3 | 1454 | -57 | -39 | 42 | 311 | -32 | -102 | 42 | 19 | +19 | +1000 | 47 | -127 | 23 |
| ER(20) 5-min | .3-.45 | 1158 | +282 | +243 | 45 | 223 | +67 | +302 | 46 | 10 | +39 | +3876 | 60 | -181 | 33 |
| ER(20) 5-min | <.15 | 1463 | +252 | +172 | 45 | 331 | +131 | +397 | 50 | 15 | +11 | +754 | 53 | -30 | 5 |
| ER(20) 5-min | >.45 | 882 | +415 | +471 | 48 | 152 | +70 | +459 | 47 | 9 | +16 | +1749 | 56 | -213 | 39 |
| atr_rel | .8-1 | 785 | +344 | +438 | 48 | 218 | +185 | +849 | 52 | 5 | +17 | +3382 | 60 | -65 | 12 |
| atr_rel | 1-1.3 | 920 | +262 | +285 | 46 | 272 | +56 | +206 | 48 | 15 | +14 | +944 | 47 | -148 | 27 |
| atr_rel | 1.3-1.6 | 616 | +0 | +1 | 41 | 132 | +19 | +142 | 43 | 4 | +11 | +2856 | 75 | -108 | 20 |
| atr_rel | <.8 | 850 | +247 | +291 | 46 | 208 | +47 | +224 | 45 | 2 | +3 | +1683 | 50 | -109 | 20 |
| atr_rel | >1.6 | 1774 | +49 | +28 | 44 | 187 | -70 | -373 | 41 | 27 | +39 | +1443 | 52 | -122 | 22 |
| LOT state (Calmar10 of P7) | cold | 3000 | +707 | +236 | 45 | 600 | +214 | +357 | 47 | 53 | +85 | +1600 | 53 | -400 | 73 |
| LOT state (Calmar10 of P7) | na | 10 | +7 | +701 | 50 | 0 |  |  |  | 0 |  |  |  | +0 | -0 |
| LOT state (Calmar10 of P7) | warm | 1948 | +183 | +94 | 44 | 417 | +23 | +55 | 45 | 0 |  |  |  | -152 | 27 |
| P7 order in session | 1st | 2213 | +548 | +248 | 46 | 267 | +152 | +569 | 50 | 10 | +6 | +604 | 50 | -163 | 29 |
| P7 order in session | 2nd | 1349 | +198 | +147 | 43 | 242 | -26 | -106 | 41 | 10 | +35 | +3495 | 70 | -163 | 30 |
| P7 order in session | 3rd+ | 1396 | +151 | +108 | 44 | 508 | +110 | +217 | 47 | 33 | +44 | +1328 | 48 | -226 | 41 |
| since last P7 exit | 1-2h | 597 | +102 | +171 | 45 | 105 | +22 | +210 | 44 | 6 | -1 | -178 | 50 | -57 | 10 |
| since last P7 exit | 2-6h | 332 | +27 | +82 | 45 | 39 | -16 | -400 | 46 | 3 | +8 | +2594 | 67 | -19 | 3 |
| since last P7 exit | 30-60m | 971 | +14 | +14 | 43 | 230 | +34 | +150 | 47 | 11 | +21 | +1893 | 64 | -142 | 26 |
| since last P7 exit | <30m | 2351 | +436 | +185 | 45 | 529 | +75 | +142 | 45 | 29 | +53 | +1824 | 48 | -221 | 40 |
| since last P7 exit | >6h | 706 | +313 | +443 | 47 | 114 | +121 | +1059 | 54 | 4 | +4 | +1094 | 50 | -113 | 20 |
| last P7 trade | after_loss | 2736 | +346 | +127 | 44 | 547 | +68 | +124 | 45 | 26 | +53 | +2023 | 62 | -341 | 62 |
| last P7 trade | after_win | 2221 | +546 | +246 | 46 | 470 | +169 | +360 | 48 | 27 | +32 | +1193 | 44 | -211 | 38 |
| last P7 trade | none | 1 | +5 | +4795 | 100 | 0 |  |  |  | 0 |  |  |  | +0 | -0 |
| side vs session move | against<1 | 456 | -110 | -242 | 40 | 82 | +24 | +292 | 50 | 4 | +2 | +561 | 50 | -44 | 8 |
| side vs session move | against>1atr | 486 | +62 | +127 | 42 | 110 | +14 | +130 | 45 | 11 | +14 | +1269 | 45 | -95 | 17 |
| side vs session move | with<1 | 745 | +295 | +397 | 47 | 148 | +60 | +406 | 47 | 5 | +7 | +1462 | 60 | -50 | 9 |
| side vs session move | with>1atr | 3270 | +645 | +197 | 45 | 677 | +138 | +204 | 46 | 33 | +61 | +1858 | 55 | -362 | 66 |
| K7/U7/M7 open | KUM none | 1813 | +35 | +19 | 43 | 401 | +39 | +97 | 45 | 22 | +16 | +714 | 45 | -193 | 35 |
| K7/U7/M7 open | KUM opp only | 601 | +34 | +57 | 43 | 107 | +7 | +61 | 46 | 2 | +2 | +1131 | 50 | -109 | 20 |
| K7/U7/M7 open | KUM same | 2544 | +828 | +326 | 47 | 509 | +191 | +376 | 48 | 29 | +67 | +2305 | 59 | -249 | 45 |
| any other book open | any same | 2943 | +983 | +334 | 47 | 593 | +194 | +327 | 47 | 31 | +60 | +1946 | 55 | -354 | 64 |
| any other book open | none | 1445 | -91 | -63 | 42 | 320 | +39 | +122 | 45 | 20 | +22 | +1111 | 50 | -108 | 20 |
| any other book open | opp only | 570 | +5 | +9 | 42 | 104 | +4 | +37 | 45 | 2 | +2 | +1131 | 50 | -90 | 16 |
| side | long | 2480 | +442 | +178 | 45 | 465 | +58 | +125 | 43 | 23 | +35 | +1539 | 57 | -253 | 46 |
| side | short | 2478 | +455 | +184 | 45 | 552 | +179 | +324 | 49 | 30 | +49 | +1647 | 50 | -299 | 54 |
| exit | BookLock | 22 | -47 | -2125 | 0 | 11 | -22 | -2009 | 0 | 1 | -0 | -114 | 0 | -7 | 1 |
| exit | RollFlat | 13 | +1 | +63 | 69 | 2 | -0 | -159 | 50 | 0 |  |  |  | +0 | -0 |
| exit | StackCut | 10 | -17 | -1749 | 10 | 0 |  |  |  | 0 |  |  |  | -14 | 2 |
| exit | StateCut | 2564 | -7459 | -2909 | 0 | 519 | -1590 | -3064 | 0 | 24 | -74 | -3084 | 0 | -1061 | 192 |
| exit | Stop | 13 | -30 | -2276 | 15 | 3 | -3 | -972 | 33 | 0 |  |  |  | -12 | 2 |
| exit | StopJoin | 71 | -132 | -1857 | 0 | 10 | -25 | -2493 | 0 | 0 |  |  |  | -26 | 5 |
| exit | StopJoinFallback | 39 | -74 | -1887 | 0 | 3 | -5 | -1672 | 0 | 0 |  |  |  | -12 | 2 |
| exit | Target | 2186 | +8644 | +3954 | 100 | 468 | +1883 | +4023 | 100 | 28 | +159 | +5676 | 100 | +580 | -105 |
| exit | TimeBlock | 40 | +11 | +268 | 57 | 1 | -1 | -667 | 0 | 0 |  |  |  | +0 | -0 |

## Excess-loss ranking (worst-20 weeks of 3.5 years, then L6M worst-5 weeks; excess = worst-week net minus n_worst x cell mean in other weeks)
```
ALL 3.5y, worst-20 weeks, 1-way
             cell    n  n_worst  worst_mean  other_mean    excess  worst_net
      sess_n=asia 2246      284     -1475.0       580.0 -583742.0  -418993.0
       lot_b=cold 3000      405      -988.0       426.0 -572692.0  -399988.0
trend_b=with>1atr 3270      344     -1052.0       344.0 -480290.0  -361888.0
         lots_b=7  797       98     -3557.0      1037.0 -450160.0  -348544.0
prev_b=after_loss 2736      354      -962.0       288.0 -442668.0  -340582.0
     side_b=short 2478      282     -1060.0       343.0 -395715.0  -298927.0
   kum_b=KUM same 2544      258      -966.0       471.0 -370985.0  -249355.0
      side_b=long 2480      247     -1023.0       311.0 -329547.0  -252686.0
       gap_b=<30m 2351      260      -848.0       314.0 -302180.0  -220536.0
        er_b=>.45  882       94     -2269.0       798.0 -288243.0  -213252.0
       ord_b=3rd+ 1396      183     -1233.0       310.0 -282388.0  -225567.0
 prev_b=after_win 2221      175     -1206.0       370.0 -275766.0  -211031.0
         lots_b=4 1764      192     -1240.0        -3.0 -237542.0  -238162.0
        ord_b=1st 2213      209      -779.0       355.0 -236837.0  -162714.0
ALL 3.5y, worst-20 weeks, 2-way
                              cell    n  n_worst  worst_mean  other_mean    excess  worst_net
          sess_n=asia & lot_b=cold 1364      220     -1449.0       755.0 -484876.0  -318692.0
            sess_n=asia & lots_b=7  797       98     -3557.0      1037.0 -450160.0  -348544.0
             lots_b=7 & lot_b=cold  486       80     -3608.0      1426.0 -402760.0  -288674.0
   sess_n=asia & trend_b=with>1atr 1228      161     -1620.0       704.0 -374179.0  -260899.0
   sess_n=asia & prev_b=after_loss 1312      189     -1427.0       516.0 -367182.0  -269699.0
    lot_b=cold & prev_b=after_loss 1663      269      -920.0       423.0 -361136.0  -247353.0
    lot_b=cold & trend_b=with>1atr 1960      263      -954.0       361.0 -346043.0  -251027.0
      lots_b=7 & trend_b=with>1atr  549       70     -3513.0      1142.0 -325871.0  -245914.0
        sess_n=asia & side_b=short 1129      158     -1348.0       658.0 -317066.0  -213047.0
         lot_b=cold & side_b=short 1551      219      -970.0       473.0 -316124.0  -212489.0
      sess_n=asia & kum_b=KUM same  934      108     -1676.0       941.0 -282620.0  -180976.0
  trend_b=with>1atr & side_b=short 1697      197     -1023.0       387.0 -277749.0  -201439.0
         sess_n=asia & side_b=long 1117      126     -1634.0       503.0 -269379.0  -205946.0
  prev_b=after_loss & side_b=short 1372      185     -1016.0       429.0 -267331.0  -188045.0
          lot_b=cold & side_b=long 1449      186     -1008.0       377.0 -257636.0  -187499.0
    gap_b=<30m & trend_b=with>1atr 1832      198      -890.0       399.0 -255264.0  -176280.0
       lot_b=cold & kum_b=KUM same 1532      199      -745.0       538.0 -255199.0  -148224.0
prev_b=after_loss & kum_b=KUM same 1353      167     -1045.0       458.0 -251030.0  -174556.0
L6M worst-5 weeks, 1-way
             cell   n  n_worst  worst_mean  other_mean    excess  worst_net
trend_b=with>1atr 677      122      -911.0       450.0 -166036.0  -111167.0
     side_b=short 552       97     -1049.0       616.0 -161562.0  -101776.0
       gap_b=<30m 529       80     -1399.0       416.0 -145232.0  -111916.0
      sess_n=asia 558      116      -629.0       623.0 -145176.0   -72958.0
       lot_b=cold 600      105      -642.0       568.0 -127087.0   -67405.0
       ord_b=3rd+ 508       86      -970.0       459.0 -122917.0   -83412.0
 prev_b=after_win 470       58     -1043.0       557.0  -92833.0   -60505.0
         lots_b=7 189       38     -1676.0       689.0  -89844.0   -63675.0
prev_b=after_loss 547      113      -495.0       285.0  -88141.0   -55958.0
   kum_b=KUM none 401       68      -973.0       315.0  -87606.0   -66183.0
        er_b=>.45 152       29     -1557.0       934.0  -72251.0   -45160.0
       lot_b=warm 417       66      -743.0       205.0  -62575.0   -49058.0
L6M worst-5 weeks, 2-way
                              cell   n  n_worst  worst_mean  other_mean    excess  worst_net
        sess_n=asia & side_b=short 308       65     -1175.0       956.0 -138509.0   -76382.0
    gap_b=<30m & trend_b=with>1atr 398       62     -1688.0       391.0 -128931.0  -104671.0
  trend_b=with>1atr & side_b=short 393       73     -1117.0       648.0 -128847.0   -81512.0
   sess_n=asia & trend_b=with>1atr 352       77      -871.0       736.0 -123797.0   -67099.0
          sess_n=asia & gap_b=<30m 283       55     -1622.0       614.0 -122981.0   -89221.0
          sess_n=asia & ord_b=3rd+ 311       66     -1065.0       665.0 -114204.0   -70291.0
          sess_n=asia & lot_b=cold 339       74      -663.0       863.0 -112904.0   -49035.0
trend_b=with>1atr & kum_b=KUM none 275       51     -1768.0       442.0 -112705.0   -90176.0
         lot_b=cold & side_b=short 350       63     -1069.0       693.0 -111033.0   -67366.0
    lot_b=cold & trend_b=with>1atr 390       71     -1003.0       435.0 -102081.0   -71186.0
      lots_b=7 & trend_b=with>1atr 150       30     -2426.0       876.0  -99061.0   -72781.0
         ord_b=3rd+ & side_b=short 297       54     -1182.0       636.0  -98174.0   -63814.0
P7 trades per week mean n worst20 vs other: 26.45 26.520958083832337
stop/cut rate worst vs other 0.6238185255198487 0.5044027997290584
        size                                     sum                                              
lots_b     1     2     3      4     5      7       1        2        3        4        5         7
half                                                                                              
2023H1   NaN   9.0   3.0   34.0   NaN   29.0     NaN   1628.0  -1922.0 -26218.0      NaN   -7164.0
2023H2   4.0  19.0   7.0   76.0   3.0   56.0  1670.0    518.0  -5627.0 -60299.0   2257.0   -5171.0
2024H1   1.0  18.0   8.0   86.0  11.0   60.0 -1629.0   5910.0   8593.0 -11058.0  45698.0   11054.0
2024H2   3.0  29.0   8.0  136.0  11.0   90.0  1982.0 -28992.0  28777.0  75073.0  35835.0   -4765.0
2025H1  12.0  25.0  22.0  168.0   7.0  145.0  1621.0  -1620.0  72417.0 -76278.0  21901.0  104756.0
2025H2   3.0  22.0  
```

## Open questions for the rest of Part C
Caveats: cells overlap heavily (Asia, 7 lots, cold and with-trend are mostly the same trades), so the excess ranking says where the loss sits, not which flag is causal; LOT cold uses the LPB shadow Calmar (no JN04 gating), and in the live week the Calmar history is the LPB list to 10-30 plus the 11-02..05 live trades (11-01..2 gap); live week trades have no layer features beyond what the signal second gives (no NTZ/zone state).
Running now (exact, JN04RM base, one set per job via jbjobs, 1 worker): C3 blackout sets WC3_S60, S15, S120, B30, B60, then C2 sets WC2_A5, A4, A6, L5, STKA (7/4/4 Asia lots 5/4/6, London 5, STACK on Asia+London). Next: first-order flag-conditional blackout screen from this table; rest-of-session hook; C4 spec.


# C2 / C3 / C4 - exact runs (JN04RM = dials ON on the live panel; one set per job; every row is a candidate or reference as labelled; Shadow only)
Cut = maxDD cut vs the reference (positive = shallower), d$ = change in mean $/week, both over the window; noise floor for entry/blackout-type changes is about 8 percent maxDD and about 1,200 $/wk (R4 noise probes). Windows appear only when every month is exact-run.

### C3 blackout, JN04RM base (live = 30 min same side; no-blackout = JN04RM)
| set | months | vs | L1M cut % / d$ | L6M cut % / d$ | HOLD cut % / d$ | PRE cut % / d$ | X' cut % / d$ | L6M worst-20 cell/ref $k | bi-weekly WF beat % | rule-2a label |
|---|---|---|---|---|---|---|---|---|---|---|
| WC3_S15 | 6 | JN04RM | 14.7 / +541 | -1.9 / +180 | n/a | n/a | n/a | 145/138 | n/a | PRE not yet run |
| WC3_S15 | 6 | LPB | 55.0 / -5800 | 45.0 / -1616 | n/a | n/a | n/a | 145/102 | n/a |  |
| WC3_S30 | 4 | JN04RM | -5.6 / -61 | n/a | n/a | n/a | n/a |  | n/a | PRE not yet run |
| WC3_S30 | 4 | LPB | 44.3 / -6947 | n/a | n/a | n/a | n/a |  | n/a |  |
| WC3_S60 | 6 | JN04RM | 27.1 / -1235 | 12.6 / -450 | n/a | n/a | n/a | 164/138 | n/a | PRE not yet run |
| WC3_S60 | 6 | LPB | 61.5 / -1242 | 52.8 / -1257 | n/a | n/a | n/a | 164/102 | n/a |  |
| WC3_S120 | 2 | JN04RM | 67.3 / +2065 | n/a | n/a | n/a | n/a |  | n/a | PRE not yet run |
| WC3_S120 | 2 | LPB | 82.8 / -4764 | n/a | n/a | n/a | n/a |  | n/a |  |
| WC3_B30 | 0 | not started | | | | | | | | |
| WC3_B60 | 0 | not started | | | | | | | | |
| WC3_H15S | 0 | not started | | | | | | | | |
| WC3_H30S | 6 | JN04RM | 16.1 / +322 | -3.7 / +106 | n/a | n/a | n/a | 146/138 | n/a | PRE not yet run |
| WC3_H30S | 6 | LPB | 55.7 / -6497 | 44.0 / -1993 | n/a | n/a | n/a | 146/102 | n/a |  |
| WC3_H60S | 0 | not started | | | | | | | | |
| WC3_H30B | 2 | JN04RM | 19.1 / +388 | n/a | n/a | n/a | n/a |  | n/a | PRE not yet run |
| WC3_H30B | 2 | LPB | 57.3 / -6497 | n/a | n/a | n/a | n/a |  | n/a |  |
| WC3_H30S_t11 | 0 | not started | | | | | | | | |
| WC3_H30S_t15 | 0 | not started | | | | | | | | |
| WC3_RS | 0 | not started | | | | | | | | |
| WC3_RH | 0 | not started | | | | | | | | |

### C2 P7 Asia table and STACK on Asia, JN04RM base (reference 7/4/4)
| set | months | vs | L1M cut % / d$ | L6M cut % / d$ | HOLD cut % / d$ | PRE cut % / d$ | X' cut % / d$ | L6M worst-20 cell/ref $k | bi-weekly WF beat % | rule-2a label |
|---|---|---|---|---|---|---|---|---|---|---|
| WC2_A4 | 0 | not started | | | | | | | | |
| WC2_A5 | 0 | not started | | | | | | | | |
| WC2_A6 | 0 | not started | | | | | | | | |
| WC2_L5 | 0 | not started | | | | | | | | |
| WC2_STKA | 0 | not started | | | | | | | | |

### C4 P7 45-s confirmation (live: three-bar 45 s, NY-AM/NY-PM), JN04RM base; WC4_REG proved identical to JN04RM
| set | months | vs | L1M cut % / d$ | L6M cut % / d$ | HOLD cut % / d$ | PRE cut % / d$ | X' cut % / d$ | L6M worst-20 cell/ref $k | bi-weekly WF beat % | rule-2a label |
|---|---|---|---|---|---|---|---|---|---|---|
| WC4_NONE | 0 | not started | | | | | | | | |
| WC4_T30 | 0 | not started | | | | | | | | |
| WC4_T60 | 0 | not started | | | | | | | | |
| WC4_HOT_LIVE | 2 | JN04RM | 0.0 / +0 | n/a | n/a | n/a | n/a |  | n/a | PRE not yet run |
| WC4_HOT_LIVE | 2 | LPB | 47.2 / -6886 | n/a | n/a | n/a | n/a |  | n/a |  |
| WC4_HOT_ALL | 0 | not started | | | | | | | | |
| WC4_CALM_LIVE | 0 | not started | | | | | | | | |
| WC4_CALM_ALL | 0 | not started | | | | | | | | |
| WC4_HOT_ALL_T30 | 0 | not started | | | | | | | | |

### First-order screens on the exact LPB_BASE trade list (P7 level, d $/wk vs no blackout; blocked trades removed, no follow-on)
| N min | side | flag at the blocked signal | blocked trades | blocked net $k | d L6M $/wk | d HOLD | d PRE | d X' |
|---|---|---|---|---|---|---|---|---|
| 15 | same | all | 201 | -68 | +703 | +578 | +450 | -8 |
| 15 | same | cold | 122 | -31 | +394 | +157 | +297 | -2 |
| 15 | same | warm | 79 | -38 | +309 | +420 | +153 | -6 |
| 15 | same | hot13 | 151 | -73 | +903 | +699 | +424 | -8 |
| 15 | same | calm | 51 | +1 | -200 | -121 | +74 | +0 |
| 15 | same | er_lo | 152 | -51 | +600 | +680 | +124 | +43 |
| 15 | same | er_hi | 52 | -19 | +102 | -102 | +278 | +24 |
| 15 | same | against_or_flat | 69 | -21 | -461 | +153 | +122 | -36 |
| 15 | same | with_trend | 132 | -48 | +1164 | +424 | +329 | +28 |
| 30 | same | all | 411 | -78 | +2164 | +551 | +506 | -4 |
| 30 | same | cold | 235 | -47 | +1163 | +331 | +232 | -37 |
| 30 | same | warm | 176 | -31 | +1001 | +219 | +275 | +32 |
| 30 | same | hot13 | 299 | -116 | +1990 | +995 | +592 | -4 |
| 30 | same | calm | 117 | +28 | +240 | -411 | +21 | +0 |
| 30 | same | er_lo | 328 | -19 | +979 | +396 | +57 | -52 |
| 30 | same | er_hi | 91 | -55 | +1097 | +110 | +461 | +48 |
| 30 | same | against_or_flat | 146 | -19 | +86 | +120 | +215 | -198 |
| 30 | same | with_trend | 266 | -59 | +2078 | +431 | +303 | +194 |
| 60 | same | all | 630 | -3 | +1642 | -11 | +64 | -317 |
| 60 | same | cold | 359 | -16 | +908 | +79 | +188 | -420 |
| 60 | same | warm | 271 | +13 | +734 | -90 | -124 | +103 |
| 60 | same | hot13 | 435 | -48 | +1206 | +138 | +302 | -166 |
| 60 | same | calm | 203 | +43 | +467 | -133 | -229 | -151 |
| 60 | same | er_lo | 518 | +6 | +531 | +607 | -344 | -174 |
| 60 | same | er_hi | 126 | -15 | +1232 | -557 | +439 | -143 |
| 60 | same | against_or_flat | 231 | -4 | +165 | +132 | +68 | -468 |
| 60 | same | with_trend | 407 | +1 | +1523 | -122 | -17 | +151 |
| 120 | same | all | 931 | +45 | +576 | -1507 | +181 | -180 |
| 120 | same | cold | 539 | -9 | +1281 | -515 | +392 | -289 |
| 120 | same | warm | 392 | +54 | -705 | -992 | -211 | +109 |
| 120 | same | hot13 | 609 | -67 | +1468 | -251 | +668 | -121 |
| 120 | same | calm | 332 | +97 | -940 | -1266 | -372 | -28 |
| 120 | same | er_lo | 748 | -22 | +874 | +211 | +67 | -34 |
| 120 | same | er_hi | 211 | +44 | +194 | -1605 | +168 | -47 |
| 120 | same | against_or_flat | 320 | -15 | -153 | -273 | +529 | -427 |
| 120 | same | with_trend | 628 | +53 | +702 | -1201 | -284 | +204 |
| 30 | both | all | 1017 | +106 | +1571 | -902 | +438 | -1950 |
| 30 | both | cold | 599 | +132 | +835 | -746 | +53 | -2218 |
| 30 | both | warm | 418 | -26 | +736 | -156 | +385 | +268 |
| 30 | both | hot13 | 458 | -132 | +2087 | +1249 | +569 | -9 |
| 30 | both | calm | 575 | +221 | -588 | -2187 | +50 | -1777 |
| 30 | both | er_lo | 667 | +45 | +164 | -772 | +328 | -293 |
| 30 | both | er_hi | 427 | +66 | +847 | -450 | -20 | -1542 |
| 30 | both | against_or_flat | 385 | +2 | -479 | -1137 | +832 | -719 |
| 30 | both | with_trend | 726 | +109 | +1642 | -154 | -436 | -1113 |
| 60 | both | all | 1443 | +108 | +1901 | -788 | +349 | -1957 |
| 60 | both | cold | 839 | +154 | +1191 | -967 | -47 | -2233 |
| 60 | both | warm | 604 | -46 | +710 | +179 | +396 | +276 |
| 60 | both | hot13 | 720 | -96 | +1235 | -117 | +964 | +356 |
| 60 | both | calm | 771 | +192 | +256 | -949 | -456 | -2109 |
| 60 | both | er_lo | 1005 | +35 | -92 | -953 | +343 | -22 |
| 60 | both | er_hi | 588 | +86 | +1407 | -511 | +60 | -1770 |
| 60 | both | against_or_flat | 596 | +38 | -594 | -1540 | +787 | -817 |
| 60 | both | with_trend | 1036 | +114 | +894 | -304 | -412 | -1109 |
| session | same | all | 1112 | +203 | -3837 | -4345 | +171 | -524 |
| session | same | cold | 661 | +173 | -3336 | -3315 | +58 | -461 |
| session | same | warm | 451 | +29 | -501 | -1030 | +113 | -62 |
| session | same | hot13 | 642 | -31 | +1173 | -591 | +585 | +52 |
| session | same | calm | 470 | +233 | -5009 | -3753 | -414 | -576 |
| session | same | er_lo | 795 | +51 | -453 | -1013 | +67 | +36 |
| session | same | er_hi | 317 | +152 | -3384 | -3332 | +104 | -559 |
| session | same | against_or_flat | 371 | +79 | -2397 | -1749 | +293 | -661 |
| session | same | with_trend | 741 | +124 | -1440 | -2596 | -122 | +138 |
| session | both | all | 1968 | +169 | -2145 | -5248 | +1561 | -791 |
| session | both | cold | 1160 | +205 | -1858 | -4454 | +768 | -1078 |
| session | both | warm | 808 | -36 | -287 | -794 | +793 | +287 |
| session | both | hot13 | 942 | -145 | +2775 | -349 | +1747 | +329 |
| session | both | calm | 1024 | +322 | -4920 | -4900 | -186 | -1293 |
| session | both | er_lo | 1274 | +54 | -1478 | -2804 | +921 | +506 |
| session | both | er_hi | 694 | +116 | -667 | -2444 | +640 | -1297 |
| session | both | against_or_flat | 701 | +9 | -1880 | -2618 | +1675 | -570 |
| session | both | with_trend | 1267 | +161 | -265 | -2631 | -113 | -221 |

### Flag threshold x N plateau (flag = atr_rel >= thr at the blocked signal)
| thr | N | side | blocked | d L6M | d HOLD | d PRE | d X' |
|---|---|---|---|---|---|---|---|
| 1.00 | 10 | same | 117 | +887 | +825 | +296 | +61 |
| 1.00 | 10 | both | 189 | +1030 | +694 | +496 | +427 |
| 1.00 | 15 | same | 170 | +1470 | +1016 | +450 | -8 |
| 1.00 | 15 | both | 312 | +1323 | +464 | +607 | +708 |
| 1.00 | 20 | same | 227 | +1671 | +940 | +533 | +120 |
| 1.00 | 20 | both | 421 | +1660 | +398 | +549 | +51 |
| 1.00 | 30 | same | 346 | +2538 | +1003 | +688 | -4 |
| 1.00 | 30 | both | 631 | +2633 | +832 | +384 | -202 |
| 1.00 | 45 | same | 451 | +2364 | +848 | +330 | -144 |
| 1.00 | 45 | both | 830 | +2572 | +49 | +178 | -159 |
| 1.00 | 60 | same | 524 | +2303 | +312 | +280 | -174 |
| 1.00 | 60 | both | 970 | +3267 | -135 | +543 | -117 |
| 1.00 | 90 | same | 645 | +2183 | +306 | +616 | -7 |
| 1.00 | 90 | both | 1170 | +3049 | -566 | +971 | -71 |
| 1.15 | 10 | same | 106 | +466 | +615 | +333 | +61 |
| 1.15 | 10 | both | 154 | +591 | +672 | +398 | +162 |
| 1.15 | 15 | same | 156 | +981 | +738 | +476 | -8 |
| 1.15 | 15 | both | 262 | +1158 | +546 | +668 | +190 |
| 1.15 | 20 | same | 210 | +1048 | +641 | +558 | +120 |
| 1.15 | 20 | both | 356 | +1485 | +492 | +662 | -93 |
| 1.15 | 30 | same | 319 | +1822 | +632 | +691 | -4 |
| 1.15 | 30 | both | 541 | +2043 | +693 | +783 | -460 |
| 1.15 | 45 | same | 417 | +1333 | +411 | +333 | -144 |
| 1.15 | 45 | both | 719 | +1632 | -15 | +936 | -362 |
| 1.15 | 60 | same | 479 | +628 | -424 | +333 | -174 |
| 1.15 | 60 | both | 840 | +1389 | -772 | +1350 | -266 |
| 1.15 | 90 | same | 589 | +895 | -158 | +680 | +48 |
| 1.15 | 90 | both | 1024 | +1703 | -618 | +1730 | -128 |
| 1.30 | 10 | same | 104 | +424 | +594 | +333 | +61 |
| 1.30 | 10 | both | 136 | +481 | +663 | +377 | +200 |
| 1.30 | 15 | same | 151 | +903 | +699 | +424 | -8 |
| 1.30 | 15 | both | 219 | +947 | +763 | +626 | +123 |
| 1.30 | 20 | same | 204 | +1155 | +787 | +558 | +120 |
| 1.30 | 20 | both | 302 | +1323 | +895 | +559 | +194 |
| 1.30 | 30 | same | 299 | +1990 | +995 | +592 | -4 |
| 1.30 | 30 | both | 458 | +2087 | +1249 | +569 | -9 |
| 1.30 | 45 | same | 385 | +1800 | +711 | +281 | -164 |
| 1.30 | 45 | both | 611 | +1608 | +441 | +630 | +69 |
| 1.30 | 60 | same | 435 | +1206 | +138 | +302 | -166 |
| 1.30 | 60 | both | 720 | +1235 | -117 | +964 | +356 |
| 1.30 | 90 | same | 529 | +1542 | +531 | +524 | +15 |
| 1.30 | 90 | both | 881 | +1674 | +150 | +1487 | +444 |
| 1.50 | 10 | same | 93 | +707 | +828 | +293 | +61 |
| 1.50 | 10 | both | 117 | +764 | +897 | +243 | +129 |
| 1.50 | 15 | same | 134 | +1028 | +946 | +363 | -8 |
| 1.50 | 15 | both | 181 | +948 | +900 | +445 | -61 |
| 1.50 | 20 | same | 182 | +1235 | +944 | +441 | +120 |
| 1.50 | 20 | both | 255 | +1185 | +895 | +378 | -10 |
| 1.50 | 30 | same | 265 | +1997 | +1350 | +446 | -4 |
| 1.50 | 30 | both | 392 | +1826 | +1390 | +399 | -166 |
| 1.50 | 45 | same | 338 | +2038 | +1373 | +180 | -164 |
| 1.50 | 45 | both | 518 | +1516 | +838 | +188 | +21 |
| 1.50 | 60 | same | 382 | +1733 | +861 | +194 | -166 |
| 1.50 | 60 | both | 606 | +1113 | +185 | +600 | +133 |
| 1.50 | 90 | same | 466 | +2076 | +1129 | +282 | +15 |
| 1.50 | 90 | both | 749 | +1705 | +914 | +543 | +186 |
| 1.70 | 10 | same | 78 | +88 | +576 | +188 | +61 |
| 1.70 | 10 | both | 96 | +88 | +579 | +153 | +88 |
| 1.70 | 15 | same | 112 | +514 | +748 | +217 | -8 |
| 1.70 | 15 | both | 148 | +376 | +681 | +291 | -75 |
| 1.70 | 20 | same | 149 | +729 | +679 | +224 | +120 |
| 1.70 | 20 | both | 202 | +621 | +726 | +266 | -101 |
| 1.70 | 30 | same | 220 | +1564 | +1212 | +168 | -4 |
| 1.70 | 30 | both | 315 | +1318 | +1160 | +296 | -248 |
| 1.70 | 45 | same | 283 | +1605 | +1076 | -133 | -136 |
| 1.70 | 45 | both | 419 | +1497 | +780 | -124 | -34 |
| 1.70 | 60 | same | 321 | +1268 | +594 | -93 | -139 |
| 1.70 | 60 | both | 500 | +1125 | +35 | +192 | +78 |
| 1.70 | 90 | same | 391 | +1360 | +705 | +79 | +50 |
| 1.70 | 90 | both | 624 | +1406 | +475 | +165 | +240 |
| 2.00 | 10 | same | 67 | +268 | +549 | +133 | +61 |
| 2.00 | 10 | both | 77 | +268 | +549 | +133 | +44 |
| 2.00 | 15 | same | 93 | +408 | +509 | +181 | -8 |
| 2.00 | 15 | both | 115 | +270 | +440 | +244 | -64 |
| 2.00 | 20 | same | 119 | +590 | +609 | +19 | +52 |
| 2.00 | 20 | both | 155 | +483 | +654 | +60 | -50 |
| 2.00 | 30 | same | 176 | +916 | +879 | -95 | -18 |
| 2.00 | 30 | both | 238 | +670 | +853 | -14 | -191 |
| 2.00 | 45 | same | 225 | +882 | +705 | -208 | -150 |
| 2.00 | 45 | both | 317 | +756 | +652 | -245 | -37 |
| 2.00 | 60 | same | 254 | +843 | +562 | -136 | -229 |
| 2.00 | 60 | both | 379 | +687 | +439 | +70 | +75 |
| 2.00 | 90 | same | 306 | +778 | +638 | +23 | -40 |
| 2.00 | 90 | both | 472 | +636 | +579 | +15 | +197 |

### C2 first-order: Asia lots scaled to A/7 of the live lots on a cell (stack level, d vs LPB_BASE)
| variant | cut L6M % | d L6M | cut HOLD % | d HOLD | cut PRE % | d PRE | cut X' % | d X' |
|---|---|---|---|---|---|---|---|---|
| Asia x3/7 on all asia | -11.6 | -3846 | -9.3 | -4294 | 9.0 | -1817 | 29.4 | +504 |
| Asia x3/7 on asia hot | -3.1 | -223 | -6.3 | -679 | -14.7 | -698 | 24.6 | +956 |
| Asia x3/7 on asia calm | -8.5 | -3863 | -6.3 | -3312 | 14.9 | -1060 | 4.8 | -90 |
| Asia x3/7 on asia cold | 12.6 | -3231 | -15.3 | -4015 | 7.3 | -756 | 29.5 | -275 |
| Asia x3/7 on asia warm | -24.2 | +278 | -21.7 | +199 | 1.7 | -813 | -0.1 | +1057 |
| Asia x3/7 on asia with-trend | -20.2 | -2246 | -17.7 | -3172 | 26.5 | -734 | -3.7 | -183 |
| Asia x3/7 on asia not-with-trend | 9.4 | -1029 | 11.3 | -872 | -18.9 | -955 | 34.1 | +1048 |
| Asia x3/7 on asia first | -0.6 | -1917 | 1.5 | -1002 | -39.5 | -1604 | 37.5 | +1050 |
| Asia x3/7 on asia later | -6.2 | -3334 | -4.0 | -3064 | 28.6 | -738 | -8.3 | -244 |
| Asia x4/7 on all asia | -7.0 | -2428 | -4.8 | -2925 | 13.7 | -973 | 26.4 | +597 |
| Asia x4/7 on asia hot | -3.1 | +130 | -5.2 | -277 | -5.3 | -390 | 20.2 | +812 |
| Asia x4/7 on asia calm | -3.9 | -2828 | -1.8 | -2439 | 16.6 | -530 | 6.3 | +71 |
| Asia x4/7 on asia cold | 11.6 | -2228 | -1.8 | -2992 | 11.7 | -659 | 26.3 | -58 |
| Asia x4/7 on asia warm | -18.6 | +556 | -16.1 | +465 | 1.9 | -502 | 0.1 | +878 |
| Asia x4/7 on asia with-trend | -11.9 | -1407 | -9.6 | -2179 | 23.0 | -245 | -2.5 | -107 |
| Asia x4/7 on asia not-with-trend | 5.8 | -1353 | 7.7 | -525 | -8.2 | -947 | 29.9 | +988 |
| Asia x4/7 on asia first | -0.2 | -1547 | 1.9 | -744 | -28.3 | -1100 | 31.9 | +926 |
| Asia x4/7 on asia later | -2.0 | -1974 | 0.1 | -1963 | 27.3 | -301 | -5.5 | -102 |
| Asia x5/7 on all asia | -2.8 | -1668 | -0.6 | -1930 | 7.4 | -678 | 14.0 | +235 |
| Asia x5/7 on asia hot | -1.6 | -12 | -3.2 | -269 | -6.8 | -449 | 13.0 | +498 |
| Asia x5/7 on asia calm | -1.2 | -1810 | 0.9 | -1539 | 12.7 | -395 | 0.9 | +238 |
| Asia x5/7 on asia cold | 6.4 | -1597 | 8.3 | -1914 | 6.1 | -199 | 13.7 | -148 |
| Asia x5/7 on asia warm | -9.1 | +310 | -6.9 | +224 | 1.3 | -347 | 0.3 | +522 |
| Asia x5/7 on asia with-trend | -6.0 | -992 | -3.8 | -1453 | 14.8 | -256 | -2.0 | -76 |
| Asia x5/7 on asia not-with-trend | 3.7 | -459 | 5.7 | -351 | -7.5 | -357 | 16.9 | +505 |
| Asia x5/7 on asia first | 1.3 | -924 | 3.4 | -452 | -18.7 | -671 | 18.2 | +513 |
| Asia x5/7 on asia later | -0.2 | -1494 | 1.8 | -1882 | 16.7 | -277 | -4.2 | -127 |
| Asia x6/7 on all asia | 0.6 | -693 | 2.6 | -964 | 11.0 | -295 | 13.1 | +362 |
| Asia x6/7 on asia hot | -1.6 | +93 | -2.1 | -197 | 1.5 | -123 | 7.1 | +314 |
| Asia x6/7 on asia calm | 2.1 | -979 | 4.1 | -891 | 8.6 | -136 | 6.0 | +153 |
| Asia x6/7 on asia cold | 5.2 | -631 | 7.1 | -1073 | 10.3 | -66 | 13.3 | +90 |
| Asia x6/7 on asia warm | -4.6 | +246 | -2.5 | +243 | 0.7 | -155 | -0.2 | +356 |
| Asia x6/7 on asia with-trend | -1.1 | -398 | 1.0 | -700 | 11.8 | +11 | 0.5 | -31 |
| Asia x6/7 on asia not-with-trend | 2.1 | -161 | 3.6 | -173 | -0.7 | -401 | 12.6 | +482 |
| Asia x6/7 on asia first | 3.3 | -623 | -0.5 | -292 | -9.7 | -429 | 14.4 | +414 |
| Asia x6/7 on asia later | 1.0 | -480 | 3.0 | -588 | 15.2 | -24 | -1.3 | +24 |
| Asia x8/7 on all asia | -4.6 | +693 | -7.4 | +964 | -11.0 | +295 | -13.1 | -362 |
| Asia x8/7 on asia hot | 1.6 | -93 | 2.1 | +197 | -1.5 | +123 | -7.1 | -314 |
| Asia x8/7 on asia calm | -6.2 | +979 | -9.5 | +891 | -9.6 | +136 | -6.0 | -153 |
| Asia x8/7 on asia cold | -5.2 | +631 | -7.4 | +1073 | -10.4 | +66 | -13.3 | -90 |
| Asia x8/7 on asia warm | 0.6 | -246 | 0.0 | -243 | -0.7 | +155 | 0.2 | -356 |
| Asia x8/7 on asia with-trend | -2.5 | +398 | -3.8 | +700 | -11.8 | -11 | -0.5 | +31 |
| Asia x8/7 on asia not-with-trend | -2.1 | +161 | -3.6 | +173 | 0.7 | +401 | -12.6 | -482 |
| Asia x8/7 on asia first | -3.6 | +623 | -1.5 | +292 | 8.9 | +429 | -14.4 | -414 |
| Asia x8/7 on asia later | -1.0 | +480 | -7.9 | +588 | -20.7 | +24 | 1.3 | -24 |
| Asia x9/7 on all asia | -4.5 | +1668 | -17.1 | +1930 | -8.5 | +678 | -16.8 | -235 |
| Asia x9/7 on asia hot | 1.6 | +12 | 3.2 | +269 | 6.8 | +449 | -13.0 | -498 |
| Asia x9/7 on asia calm | -6.1 | +1810 | -20.3 | +1539 | -14.7 | +395 | -3.6 | -238 |
| Asia x9/7 on asia cold | -6.4 | +1597 | -17.1 | +1914 | -7.2 | +199 | -16.5 | +148 |
| Asia x9/7 on asia warm | 1.8 | -310 | 0.0 | -224 | -1.3 | +347 | -0.3 | -522 |
| Asia x9/7 on asia with-trend | -0.8 | +992 | -9.2 | +1453 | -15.4 | +256 | 1.0 | +76 |
| Asia x9/7 on asia not-with-trend | -3.7 | +459 | -7.9 | +351 | 7.5 | +357 | -17.6 | -505 |
| Asia x9/7 on asia first | -4.8 | +924 | -3.4 | +452 | 14.0 | +671 | -23.1 | -513 |
| Asia x9/7 on asia later | 0.2 | +1494 | -13.7 | +1882 | -26.6 | +277 | 4.2 | +127 |