# FLATTEN quick screen, NP (W-PLAN-AS, order 0914Z S1-S4; bare, all events one-position, 1-s NQ, no Trade Health; REF = flatten at the bell; hard flat 16:55 ET of the bell date). Raw output of code/th_planas/flatten_study.py NP on server C
NP events 20110 hard<=bell (no carry room): 0
### NP: variants vs REF = flatten at the bell, bare, all events one-position; wk/DD in $, income ratio vs REF; year incomes in $k
REF flatten                n  9805 car    0 | inc 1.00 ( 1744674) DD  -304730 (1.00) wk  -82881 | L6  642016/ -61151 L3  285162/ -61151 |  0  0  0 ---- | {2023: 347, 2024: 299, 2025: 615, 2026: 459}
S1a carry all              n  9805 car 2122 | inc 1.00 ( 1751664) DD  -255912 (0.84) wk  -85593 | L6  588736/ -69521 L3  290712/ -69521 |  4  4  7 ---- | {2023: 380, 2024: 303, 2025: 617, 2026: 452}
S1b carry if >=0           n  9805 car  866 | inc 1.06 ( 1847484) DD  -306090 (1.00) wk  -91221 | L6  616276/ -82721 L3  273732/ -82721 |  5  7  6 ---- | {2023: 336, 2024: 383, 2025: 690, 2026: 427}
S1c carry if >=.25R        n  9805 car  403 | inc 1.08 ( 1879104) DD  -279510 (0.92) wk  -81393 | L6  658306/ -65981 L3  291132/ -65981 |  7  8 10 PASS | {2023: 354, 2024: 325, 2025: 671, 2026: 499}
S1d carry all +BE          n  9805 car 2122 | inc 1.07 ( 1873584) DD  -316520 (1.04) wk  -87351 | L6  637636/ -75041 L3  272742/ -75041 |  7  7  9 PASS | {2023: 366, 2024: 374, 2025: 656, 2026: 452}
S1e carry all +half stop   n  9805 car 2122 | inc 1.00 ( 1747224) DD  -310530 (1.02) wk  -87333 | L6  630226/ -69110 L3  289152/ -64541 |  3  5  4 ---- | {2023: 352, 2024: 361, 2025: 563, 2026: 446}
S1f carry all max30        n  9805 car 2122 | inc 1.05 ( 1825614) DD  -249792 (0.82) wk  -90303 | L6  606106/ -75731 L3  284802/ -75731 |  6  6  6 ---- | {2023: 398, 2024: 312, 2025: 641, 2026: 467}
S1f carry all max60        n  9805 car 2122 | inc 1.00 ( 1751664) DD  -255912 (0.84) wk  -85593 | L6  588736/ -69521 L3  290712/ -69521 |  4  4  7 ---- | {2023: 380, 2024: 303, 2025: 617, 2026: 452}
S1f carry all max120       n  9805 car 2122 | inc 1.00 ( 1751664) DD  -255912 (0.84) wk  -85593 | L6  588736/ -69521 L3  290712/ -69521 |  4  4  7 ---- | {2023: 380, 2024: 303, 2025: 617, 2026: 452}
S1b+BE carry>=0 +BE        n  9805 car  866 | inc 1.07 ( 1870464) DD  -316100 (1.04) wk  -87651 | L6  637996/ -74771 L3  273282/ -74771 |  7  7  9 PASS | {2023: 366, 2024: 372, 2025: 654, 2026: 452}
S1c+BE carry>=.25R +BE     n  9805 car  403 | inc 1.08 ( 1881324) DD  -283520 (0.93) wk  -87861 | L6  644716/ -68681 L3  283662/ -68681 |  7  6 11 PASS | {2023: 352, 2024: 342, 2025: 672, 2026: 483}
C90_0.25 carry>=.25R max90 n  9805 car  403 | inc 1.08 ( 1879104) DD  -279510 (0.92) wk  -81393 | L6  658306/ -65981 L3  291132/ -65981 |  7  8 10 PASS | {2023: 354, 2024: 325, 2025: 671, 2026: 499}
S3 mgmt T15                n 10719 car    0 | inc 0.86 ( 1508921) DD  -280912 (0.92) wk  -81615 | L6  592756/ -71587 L3  253249/ -71587 |  8  8  6 ---- | {2023: 280, 2024: 282, 2025: 536, 2026: 393}
S3 mgmt T30                n 11260 car    0 | inc 0.67 ( 1163561) DD  -290578 (0.95) wk  -96284 | L6  564060/ -55774 L3  193050/ -55774 |  7  7  4 ---- | {2023: 191, 2024: 205, 2025: 468, 2026: 345}
S3 mgmt T60                n 12228 car    0 | inc 0.45 (  783426) DD  -276698 (0.91) wk  -78341 | L6  393414/ -65673 L3   86924/ -65673 |  9  8  2 ---- | {2023: 138, 2024: 35, 2025: 398, 2026: 252}
S4 bell +30 min            n  9805 car    0 | inc 1.05 ( 1825614) DD  -249792 (0.82) wk  -90303 | L6  606106/ -75731 L3  284802/ -75731 |  6  6  6 ---- | {2023: 398, 2024: 312, 2025: 641, 2026: 467}
S4 bell +60 min            n  9805 car    0 | inc 0.99 ( 1724124) DD  -266682 (0.88) wk  -85995 | L6  596626/ -68891 L3  291012/ -68891 |  4  6  6 ---- | {2023: 370, 2024: 269, 2025: 638, 2026: 453}
S4 bell +90 min            n  9805 car    0 | inc 0.99 ( 1724124) DD  -266682 (0.88) wk  -85995 | L6  596626/ -68891 L3  291012/ -68891 |  4  6  6 ---- | {2023: 370, 2024: 269, 2025: 638, 2026: 453}
S2 skip late (median-p50)  n  8518 car    0 | inc 1.02 ( 1772300) DD  -286002 (0.94) wk  -82881 | L6  696414/ -61818 L3  294688/ -61818 | 10 10 10 PASS | {2023: 377, 2024: 302, 2025: 621, 2026: 522}
S2 late at half size p50   n  9805 car    0 | inc 1.01 ( 1758487) DD  -295366 (0.97) wk  -82881 | L6  669215/ -61484 L3  289925/ -61484 | 11 10 10 PASS | {2023: 362, 2024: 300, 2025: 618, 2026: 490}
S2 skip late (median-p75)  n  7570 car    0 | inc 0.85 ( 1479499) DD  -284113 (0.93) wk  -82881 | L6  603073/ -66140 L3  245909/ -66140 |  9  8  6 ---- | {2023: 359, 2024: 159, 2025: 606, 2026: 408}
S2 late at half size p75   n  9805 car    0 | inc 0.92 ( 1612087) DD  -292856 (0.96) wk  -82881 | L6  622545/ -63645 L3  265535/ -63645 |  9  8  6 PASS | {2023: 353, 2024: 229, 2025: 610, 2026: 434}
### pessimistic label (stop slip by lots), reference also stressed
S1a carry all STRESS       n  9805 car 2122 | inc 1.03 ( 1187483) DD  -348813 (0.93) wk  -90464 | L6  499874/ -73204 L3  248538/ -73204 |  4  5  7 ---- | {2023: 271, 2024: 144, 2025: 446, 2026: 312}
S1b carry if >=0 STRESS    n  9805 car  866 | inc 1.11 ( 1274987) DD  -368251 (0.98) wk  -94903 | L6  525988/ -86523 L3  231082/ -86523 |  6  8  6 ---- | {2023: 225, 2024: 221, 2025: 517, 2026: 284}
S1c carry if >=.25R STRESS n  9805 car  403 | inc 1.13 ( 1298410) DD  -338079 (0.90) wk  -86264 | L6  567068/ -69783 L3  247888/ -69783 |  7  8 10 PASS | {2023: 240, 2024: 161, 2025: 496, 2026: 354}
S1d carry all +BE STRESS   n  9805 car 2122 | inc 1.13 ( 1297166) DD  -386375 (1.03) wk  -91152 | L6  546398/ -78843 L3  229380/ -78843 |  7  7  9 PASS | {2023: 253, 2024: 212, 2025: 482, 2026: 307}
S1f carry all max60 STRESS n  9805 car 2122 | inc 1.03 ( 1187483) DD  -348813 (0.93) wk  -90464 | L6  499874/ -73204 L3  248538/ -73204 |  4  5  7 ---- | {2023: 271, 2024: 144, 2025: 446, 2026: 312}
C90_0.25 carry>=.25R max90 STRESS n  9805 car  403 | inc 1.13 ( 1298410) DD  -338079 (0.90) wk  -86264 | L6  567068/ -69783 L3  247888/ -69783 |  7  8 10 PASS | {2023: 240, 2024: 161, 2025: 496, 2026: 354}
S3 mgmt T30 STRESS         n 11260 car    0 | inc 0.29 (  329585) DD  -417633 (1.11) wk -102224 | L6  432786/ -60764 L3  129373/ -60764 |  6  7  1 ---- | {2023: 31, 2024: -33, 2025: 216, 2026: 139}
S4 +30 STRESS              n  9805 car    0 | inc 1.09 ( 1257988) DD  -310960 (0.83) wk  -95174 | L6  516412/ -79414 L3  241915/ -79414 |  6  5  8 ---- | {2023: 288, 2024: 152, 2025: 469, 2026: 325}
S4 +60 STRESS              n  9805 car    0 | inc 1.01 ( 1160418) DD  -349007 (0.93) wk  -89202 | L6  508001/ -72574 L3  248956/ -72574 |  4  5  7 ---- | {2023: 260, 2024: 110, 2025: 467, 2026: 313}
S4 +90 STRESS              n  9805 car    0 | inc 1.01 ( 1160418) DD  -349007 (0.93) wk  -89202 | L6  508001/ -72574 L3  248956/ -72574 |  4  5  7 ---- | {2023: 260, 2024: 110, 2025: 467, 2026: 313}
### random-carry null (same number carried, random among the trades open at the bell under REF flatten), 40 draws
S1b carry if >=0             carried 866 of 2183 open at bell | plan inc 1847484 DD -306090 wk -91221 | null mean inc 1752177 DD -285917 wk -86111 | plan beats null: inc 0.88 DD 0.25 wk 0.17
S1c carry if >=.25R          carried 403 of 2183 open at bell | plan inc 1879104 DD -279510 wk -81393 | null mean inc 1731832 DD -298394 wk -84977 | plan beats null: inc 1.00 DD 0.85 wk 0.75
C90_0.25 carry>=.25R max90   carried 403 of 2183 open at bell | plan inc 1879104 DD -279510 wk -81393 | null mean inc 1746053 DD -294142 wk -84285 | plan beats null: inc 1.00 DD 0.78 wk 0.65
S1a carry all                carried 2122 of 2183 open at bell | plan inc 1751664 DD -255912 wk -85593 | null mean inc 1754721 DD -256570 wk -85639 | plan beats null: inc 0.50 DD 0.45 wk 0.38
### per book (income/DD/worst wk vs REF)
  S1a carry all          MACD inc 1.50 DD 0.85 wk 1.01
  S1a carry all          MF1 inc 1.00 DD 0.99 wk 1.02
  S1a carry all          MF2 inc 1.10 DD 0.93 wk 0.88
  S1a carry all          MF3 inc 0.86 DD 1.17 wk 1.18
  S1a carry all          MF4 inc 0.86 DD 1.12 wk 1.08
  S1b carry if >=0       MACD inc 1.14 DD 0.96 wk 1.00
  S1b carry if >=0       MF1 inc 1.08 DD 0.89 wk 1.00
  S1b carry if >=0       MF2 inc 1.07 DD 0.99 wk 0.98
  S1b carry if >=0       MF3 inc 0.98 DD 1.06 wk 1.00
  S1b carry if >=0       MF4 inc 1.12 DD 0.88 wk 1.08
  S1c carry if >=.25R    MACD inc 1.01 DD 1.00 wk 1.00
  S1c carry if >=.25R    MF1 inc 1.10 DD 0.92 wk 1.00
  S1c carry if >=.25R    MF2 inc 1.07 DD 1.00 wk 0.98
  S1c carry if >=.25R    MF3 inc 1.02 DD 1.01 wk 1.00
  S1c carry if >=.25R    MF4 inc 1.20 DD 0.92 wk 1.00
### REF P&L by exit kind and year ($k): 1 stop 2 target 3 bell flatten
kind       1       2      3
tx                         
2023 -2257.0  3025.0 -421.0
2024 -4429.0  5286.0 -558.0
2025 -5917.0  7055.0 -523.0
2026 -5625.0  6397.0 -313.0
bell-flatten trades: n 2183 net $-1815364 ; open R at bell median -0.07 p25 -0.30 p75 0.13 (in points -5.2)
