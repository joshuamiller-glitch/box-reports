# DS3_L2SET_ENTRY_PREHOLD - PRE-only selection (2024-02-01..2025-06-30; nothing else read), 2026-10-30

prereg L2SET_ENTRY_prereg.md sha256 0e5ea9c7...; 2179 cells ({'F1': 943, 'F2': 200, 'F3': 84, 'F4': 552, 'F5': 360, 'F6': 28, 'F7': 12}); PRE weeks 75; unit = engine book (exact lock engine delta vs engine base, report $/wk) or trade-level (PB DN MV MA); STACK = sum of the 6 engine books; ALL = STACK + 4 trade-level books.

Selection rule: highest PRE mean delta $/wk among cells with >= 100 PRE fills in the unit (>= 300 for STACK/ALL). Selection on PRE only; later windows are read ONCE per group after this file is sealed.

## PRE-best cell per unit and group (PRE mean delta $/wk [95% CI] (MDE80), PRE fills)

| unit | group | cell | PRE $/wk [CI] (MDE) | PRE fills |
|--|--|--|--|--|
| ST | ALLFAM | fam=F5|F=0.7|X=5|N=0|chase=px5|veto=v4 | +5052 [+122,+9644] (6526) | 3018 |
| ST | G1 | fam=F1|X=0|b=i|prof=loose|N=3|veto=v3 | +1019 [-5724,+6926] (9372) | 2869 |
| ST | G4 | fam=F4|X=inf|chase=prt5|stop=orig | +2475 [-9202,+14352] (16860) | 1352 |
| ST | G5 | fam=F5|F=0.7|X=5|N=0|chase=px5|veto=v4 | +5052 [+122,+9644] (6526) | 3018 |
| ST | G6 | fam=F6|X=0|N=2|T=10|veto=v4 | +571 [-5835,+6527] (9611) | 2899 |
| ST | G7 | fam=F7|lgb_th=0.0|X=0 | -4055 [-13593,+5329] (13404) | 2360 |
| HM | ALLFAM | fam=F1|X=3|b=iii|prof=dflt|N=4|veto=v3 | +9442 [+33,+18489] (13171) | 2150 |
| HM | G1 | fam=F1|X=3|b=iii|prof=dflt|N=4|veto=v3 | +9442 [+33,+18489] (13171) | 2150 |
| HM | G4 | fam=F4|X=5|N=2|chase=px20|stop=fill|veto=v4 | +7964 [-1383,+17097] (13720) | 2221 |
| HM | G5 | fam=F5|F=0.5|X=15|N=0|chase=imb5|veto=v4 | +3269 [-3258,+10627] (9834) | 2242 |
| HM | G6 | fam=F6|X=0|N=1|T=10|veto=v4 | +3326 [-820,+7448] (6073) | 2238 |
| HM | G7 | fam=F7|lgb_th=0.0|X=0 | +1780 [-6540,+10964] (12759) | 1773 |
| WT | ALLFAM | fam=F1|X=15|b=iii|prof=dflt|N=2|veto=none | +6735 [+708,+12690] (8360) | 2930 |
| WT | G1 | fam=F1|X=15|b=iii|prof=dflt|N=2|veto=none | +6735 [+708,+12690] (8360) | 2930 |
| WT | G4 | fam=F4|X=inf|chase=prt8|stop=orig | +5871 [-795,+12601] (9855) | 1070 |
| WT | G5 | fam=F5|F=0.3|X=5|N=0|chase=px20|veto=v4 | +5035 [+403,+10267] (7050) | 4197 |
| WT | G6 | fam=F6|X=5|N=2|T=10|veto=v4 | +3840 [-1039,+9067] (7471) | 3400 |
| WT | G7 | fam=F7|lgb_th=0.0|X=10 | +1017 [-4969,+6710] (8461) | 1813 |
| KB | ALLFAM | fam=F1|X=5|b=ii|M=10|prof=dflt|N=3|veto=v4 | +2371 [-3109,+8043] (8145) | 2429 |
| KB | G1 | fam=F1|X=5|b=ii|M=10|prof=dflt|N=3|veto=v4 | +2371 [-3109,+8043] (8145) | 2429 |
| KB | G4 | fam=F4|X=5|N=3|chase=dlt3|stop=orig|veto=v4 | +1910 [-3690,+6979] (7194) | 2997 |
| KB | G5 | fam=F5|F=0.3|X=15|N=1|chase=imb10|veto=v4 | +939 [-3358,+5458] (6695) | 2996 |
| KB | G6 | fam=F6|X=0|N=1|T=5|veto=v4 | -886 [-3570,+1794] (3746) | 3016 |
| KB | G7 | fam=F7|lgb_th=2.0|X=0 | -3497 [-8642,+1690] (7553) | 2195 |
| SM | ALLFAM | fam=F4|X=10|N=1|chase=imb8|stop=orig|veto=v4 | +2471 [-1401,+5757] (5227) | 902 |
| SM | G1 | fam=F1|X=3|b=iii|M=10|prof=dflt|N=3|veto=v4 | +2406 [-708,+5035] (4010) | 901 |
| SM | G4 | fam=F4|X=10|N=1|chase=imb8|stop=orig|veto=v4 | +2471 [-1401,+5757] (5227) | 902 |
| SM | G5 | fam=F5|F=0.3|X=15|N=2|chase=imb10|veto=v4 | +1080 [-2398,+4285] (4749) | 892 |
| SM | G6 | fam=F6|X=0|N=2|T=10|veto=v4 | -396 [-2528,+1893] (3166) | 868 |
| SM | G7 | fam=F7|lgb_th=0.0|X=0 | +714 [-2949,+3989] (4945) | 741 |
| PE | ALLFAM | fam=F5|F=0.3|X=10|N=3|chase=px10|veto=v4 | +3394 [-1481,+8088] (6785) | 2977 |
| PE | G1 | fam=F1|X=5|b=ii|prof=dflt|N=4|veto=v3 | +1873 [-4778,+8665] (9593) | 2024 |
| PE | G4 | fam=F4|X=10|N=2|chase=2of810|stop=orig|veto=v4 | +3209 [-1834,+8063] (7196) | 3021 |
| PE | G5 | fam=F5|F=0.3|X=10|N=3|chase=px10|veto=v4 | +3394 [-1481,+8088] (6785) | 2977 |
| PE | G6 | fam=F6|X=0|N=1|T=10|veto=v4 | -1193 [-3816,+1377] (3589) | 2977 |
| PE | G7 | fam=F7|lgb_th=0.0|X=0 | -2574 [-8264,+2726] (7782) | 2504 |
| PB | ALLFAM | fam=F4|X=inf|chase=nextbar|stop=fill | +13799 [+3741,+24393] (14864) | 1136 |
| PB | G1 | fam=F2|gate=ABS3|X=10|b=i|veto=none | +9366 [-6641,+24929] (21851) | 119 |
| PB | G4 | fam=F4|X=inf|chase=nextbar|stop=fill | +13799 [+3741,+24393] (14864) | 1136 |
| PB | G5 | fam=F5|F=0.5|X=8|N=1|chase=none|veto=v4 | +2510 [-1883,+6952] (6496) | 1965 |
| PB | G6 | fam=F6|X=10|N=1|T=5|veto=v4 | +5080 [-3319,+13377] (12318) | 1902 |
| PB | G7 | fam=F7|lgb_th=2.0|X=10 | +6245 [-4384,+16787] (15421) | 1620 |
| DN | ALLFAM | fam=F5|F=0.7|X=5|N=1|chase=imb5|veto=v4 | -2174 [-4868,+180] (3582) | 1749 |
| DN | G1 | fam=F2|gate=IMBF20|X=5|b=iii|veto=v4 | -5495 [-11658,+694] (8790) | 1742 |
| DN | G4 | fam=F4|X=5|N=2|chase=px20|stop=fill|veto=v4 | -2482 [-10619,+5843] (10905) | 1726 |
| DN | G5 | fam=F5|F=0.7|X=5|N=1|chase=imb5|veto=v4 | -2174 [-4868,+180] (3582) | 1749 |
| DN | G6 | fam=F6|X=0|N=1|T=5|veto=v4 | -9794 [-14252,-6158] (5824) | 1670 |
| DN | G7 | fam=F7|lgb_th=1.0|X=5 | -12440 [-20378,-4076] (11666) | 1219 |
| MV | ALLFAM | fam=F4|X=5|N=3|chase=px10|stop=orig|veto=v4 | +5759 [-2416,+14487] (12220) | 2826 |
| MV | G1 | fam=F1|X=3|b=iii|prof=strict|N=1|veto=v3 | +5376 [-1440,+12457] (10240) | 2911 |
| MV | G4 | fam=F4|X=5|N=3|chase=px10|stop=orig|veto=v4 | +5759 [-2416,+14487] (12220) | 2826 |
| MV | G5 | fam=F5|F=0.3|X=3|N=0|chase=px20|veto=v4 | +3910 [-965,+9343] (7486) | 2914 |
| MV | G6 | fam=F6|X=10|N=3|T=10|veto=v4 | +3168 [-5950,+12110] (12839) | 2319 |
| MV | G7 | fam=F7|lgb_th=0.0|X=0 | +1351 [-4564,+7695] (8776) | 2583 |
| MA | ALLFAM | fam=F1|X=15|b=iii|prof=strict|N=2|veto=v3 | +2820 [-4345,+10278] (10056) | 1032 |
| MA | G1 | fam=F1|X=15|b=iii|prof=strict|N=2|veto=v3 | +2820 [-4345,+10278] (10056) | 1032 |
| MA | G4 | fam=F4|X=5|N=2|chase=nextbar|stop=orig|veto=v4 | +1238 [-2678,+5432] (5837) | 1071 |
| MA | G5 | fam=F5|F=0.5|X=3|N=2|chase=px20|veto=v4 | +895 [-1338,+3132] (3219) | 1077 |
| MA | G6 | fam=F6|X=0|N=3|T=10|veto=v4 | +788 [-2915,+5364] (5906) | 1024 |
| MA | G7 | fam=F7|lgb_th=1.0|X=0 | -1409 [-5559,+3021] (6423) | 991 |
| STACK | ALLFAM | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | +7644 [-163,+15811] (11248) | 15217 |
| STACK | G1 | fam=F1|X=3|b=iii|prof=dflt|N=4|veto=v3 | +4190 [-14219,+23549] (26934) | 14713 |
| STACK | G4 | fam=F4|X=10|N=1|chase=2of810|stop=orig|veto=v4 | +6965 [-8535,+23153] (23257) | 16312 |
| STACK | G5 | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | +7644 [-163,+15811] (11248) | 15217 |
| STACK | G6 | fam=F6|X=0|N=1|T=10|veto=v4 | -1264 [-9147,+7127] (11963) | 16162 |
| STACK | G7 | fam=F7|lgb_th=0.0|X=0 | -7587 [-27314,+11744] (28060) | 12343 |
| ALL | ALLFAM | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | +1731 [-6612,+10510] (12473) | 22654 |
| ALL | G1 | fam=F1|X=5|b=iii|prof=dflt|N=2|veto=none | -3880 [-23393,+13731] (26846) | 24190 |
| ALL | G4 | fam=F4|X=inf|chase=prt3|stop=orig | -3120 [-45883,+40067] (60982) | 11781 |
| ALL | G5 | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | +1731 [-6612,+10510] (12473) | 22654 |
| ALL | G6 | fam=F6|X=0|N=2|T=10|veto=v4 | -12793 [-23636,-2552] (15918) | 23567 |
| ALL | G7 | fam=F7|lgb_th=0.0|X=0 | -24994 [-52708,+3538] (41671) | 19204 |

## Best-of-N White reality check over cells with enough PRE fills (studentised, 1000 bootstrap): (max t, p)
- ST: t 2.17 p 0.616
- HM: t 2.04 p 0.676
- WT: t 2.26 p 0.512
- KB: t 0.81 p 0.981
- SM: t 1.68 p 0.838
- PE: t 1.65 p 0.894
- PB: t 3.54 p 0.084
- DN: t -0.64 p 1.000
- MV: t 1.53 p 0.852
- MA: t 1.32 p 0.905
- STACK: t 1.90 p 0.765
- ALL: t 0.39 p 1.000

## Anchor D6-LIVE-like (dip 10, 3 of 8 default, v4, basis i), PRE: STACK -19125 (29283), ALL -35495 (45843), ST -5088 (14840), HM -2538 (14632), WT -905 (8155), KB -3546 (8021), SM -2928 (5417), PE -4120 (6867)

Selection file l2vast/ds3/out/l2set/entry/pre_sel.json sha256 c6de49336e0745a4ee5494bb89bca2bc7b44f4ce7e553d278fbef269636c9575. Subgroup (book x session 49, book x vol tercile 30) selections are in the file, trade-level, PRE only.