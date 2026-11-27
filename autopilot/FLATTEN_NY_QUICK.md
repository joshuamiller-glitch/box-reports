# FLATTEN quick screen, NY (W-PLAN-AS, order 0914Z S1-S4; bare, all events one-position, 1-s NQ, no Trade Health; REF = flatten at the bell; hard flat 16:55 ET of the bell date). Raw output of code/th_planas/flatten_study.py NY on server C
NY events 76059 hard<=bell (no carry room): 0
### NY: variants vs REF = flatten at the bell, bare, all events one-position; wk/DD in $, income ratio vs REF; year incomes in $k
REF flatten                n 17196 car    0 | inc 1.00 ( 4353380) DD  -317125 (1.00) wk -226439 | L6 1960507/-168005 L3  885036/-159505 |  0  0  0 ---- | {2023: 423, 2024: 568, 2025: 1605, 2026: 2214}
S1a carry all              n 17196 car 3921 | inc 0.92 ( 4003620) DD  -379986 (1.20) wk -225681 | L6 1609632/-194610 L3  645821/-194610 |  3  3  5 ---- | {2023: 831, 2024: 192, 2025: 1622, 2026: 1819}
S1b carry if >=0           n 17196 car 1815 | inc 1.02 ( 4454565) DD  -396001 (1.25) wk -243434 | L6 1769602/-171595 L3  763621/-171595 |  4  2  7 ---- | {2023: 635, 2024: 472, 2025: 1760, 2026: 2013}
S1c carry if >=.25R        n 17196 car  807 | inc 1.01 ( 4416420) DD  -304545 (0.96) wk -226439 | L6 1871117/-168005 L3  812601/-152100 |  3  6  7 ---- | {2023: 507, 2024: 537, 2025: 1731, 2026: 2086}
S1d carry all +BE          n 17196 car 3921 | inc 1.00 ( 4373235) DD  -318805 (1.01) wk -229064 | L6 1872092/-167605 L3  819076/-145915 |  4  3  8 ---- | {2023: 450, 2024: 689, 2025: 1676, 2026: 2036}
S1e carry all +half stop   n 17196 car 3921 | inc 0.98 ( 4280080) DD  -314980 (0.99) wk -247109 | L6 1706082/-164395 L3  697681/-157080 |  4  3  7 ---- | {2023: 452, 2024: 630, 2025: 1759, 2026: 1940}
S1f carry all max30        n 17196 car 3921 | inc 1.01 ( 4416580) DD  -304945 (0.96) wk -233474 | L6 1672257/-174887 L3  671296/-167100 |  5  5  6 ---- | {2023: 534, 2024: 714, 2025: 1749, 2026: 1918}
S1f carry all max60        n 17196 car 3921 | inc 1.03 ( 4499225) DD  -267085 (0.84) wk -195614 | L6 1749377/-174887 L3  728081/-154815 |  4  5  7 ---- | {2023: 607, 2024: 577, 2025: 1834, 2026: 1953}
S1f carry all max120       n 17196 car 3921 | inc 1.03 ( 4464165) DD  -287935 (0.91) wk -216464 | L6 1761092/-174887 L3  707416/-167745 |  3  5  7 ---- | {2023: 665, 2024: 564, 2025: 1705, 2026: 1992}
S1b+BE carry>=0 +BE        n 17196 car 1815 | inc 1.00 ( 4371780) DD  -318985 (1.01) wk -229064 | L6 1872252/-167855 L3  819841/-145555 |  4  3  8 ---- | {2023: 450, 2024: 689, 2025: 1675, 2026: 2034}
S1c+BE carry>=.25R +BE     n 17196 car  807 | inc 1.01 ( 4391140) DD  -310570 (0.98) wk -226439 | L6 1917542/-168005 L3  844971/-141315 |  3  3  6 ---- | {2023: 437, 2024: 622, 2025: 1702, 2026: 2100}
carry>=.25R max90 [my label, not W-DYNH c90 cut rule] n 17196 car  807 | inc 1.00 ( 4351465) DD  -304545 (0.96) wk -226439 | L6 1965542/-168005 L3  912861/-155265 |  4  6  5 ---- | {2023: 391, 2024: 541, 2025: 1666, 2026: 2204}
S3 mgmt T15                n 18835 car    0 | inc 0.94 ( 4087194) DD  -286070 (0.90) wk -191062 | L6 1989733/-160297 L3  806246/-160297 |  5  4  4 ---- | {2023: 203, 2024: 458, 2025: 1606, 2026: 2168}
S3 mgmt T30                n 20583 car    0 | inc 0.87 ( 3783876) DD  -295701 (0.93) wk -177301 | L6 1994492/-160348 L3  758002/-160348 |  6  6  2 ---- | {2023: 99, 2024: 448, 2025: 1251, 2026: 2238}
S3 mgmt T60                n 24393 car    0 | inc 0.66 ( 2891291) DD  -390386 (1.23) wk -198624 | L6 1459207/-173305 L3  456074/-173305 |  5  8  1 ---- | {2023: 35, 2024: 170, 2025: 1017, 2026: 1775}
S4 bell +30 min            n 17196 car    0 | inc 1.01 ( 4416580) DD  -304945 (0.96) wk -233474 | L6 1672257/-174887 L3  671296/-167100 |  5  5  6 ---- | {2023: 534, 2024: 714, 2025: 1749, 2026: 1918}
S4 bell +60 min            n 17196 car    0 | inc 1.03 ( 4499225) DD  -267085 (0.84) wk -195614 | L6 1749377/-174887 L3  728081/-154815 |  4  5  7 ---- | {2023: 607, 2024: 577, 2025: 1834, 2026: 1953}
S4 bell +90 min            n 17196 car    0 | inc 1.04 ( 4514915) DD  -275890 (0.87) wk -204419 | L6 1827792/-179725 L3  774376/-179725 |  3  4  7 ---- | {2023: 645, 2024: 546, 2025: 1727, 2026: 2064}
S2 skip late (median-p50)  n 16225 car    0 | inc 0.99 ( 4321198) DD  -283722 (0.89) wk -200470 | L6 1977969/-171217 L3  852134/-158907 | 10  6  3 PASS | {2023: 383, 2024: 505, 2025: 1581, 2026: 2218}
S2 late at half size p50   n 17196 car    0 | inc 1.00 ( 4336275) DD  -300557 (0.95) wk -212824 | L6 1968875/-169611 L3  869419/-159086 |  9  6  3 PASS | {2023: 402, 2024: 534, 2025: 1593, 2026: 2218}
S2 skip late (median-p75)  n 15238 car    0 | inc 1.02 ( 4423556) DD  -243715 (0.77) wk -188968 | L6 1918693/-179538 L3  767466/-179538 | 10  8  4 PASS | {2023: 383, 2024: 511, 2025: 1602, 2026: 2208}
S2 late at half size p75   n 17196 car    0 | inc 1.01 ( 4379803) DD  -280546 (0.88) wk -206469 | L6 1937531/-170440 L3  823268/-170440 | 10  8  4 PASS | {2023: 398, 2024: 539, 2025: 1598, 2026: 2209}
### pessimistic label (stop slip by lots), reference also stressed
S1a carry all STRESS       n 17196 car 3921 | inc 0.94 ( 3412353) DD  -410509 (1.24) wk -234206 | L6 1498622/-201068 L3  601439/-201068 |  3  3  6 ---- | {2023: 734, 2024: 37, 2025: 1447, 2026: 1640}
S1b carry if >=0 STRESS    n 17196 car 1815 | inc 1.05 ( 3809449) DD  -430537 (1.30) wk -249317 | L6 1652138/-178318 L3  716513/-178318 |  4  2  7 ---- | {2023: 525, 2024: 301, 2025: 1569, 2026: 1823}
S1c carry if >=.25R STRESS n 17196 car  807 | inc 1.03 ( 3726216) DD  -317420 (0.96) wk -232440 | L6 1749171/-173024 L3  763279/-158988 |  3  6  7 ---- | {2023: 386, 2024: 351, 2025: 1529, 2026: 1888}
S1d carry all +BE STRESS   n 17196 car 3921 | inc 1.02 ( 3688810) DD  -331753 (1.00) wk -235065 | L6 1750364/-172506 L3  769689/-152849 |  4  3  8 ---- | {2023: 331, 2024: 506, 2025: 1475, 2026: 1838}
S1f carry all max60 STRESS n 17196 car 3921 | inc 1.06 ( 3843751) DD  -278890 (0.84) wk -201378 | L6 1633538/-178710 L3  681081/-161320 |  5  5  7 ---- | {2023: 490, 2024: 401, 2025: 1643, 2026: 1766}
carry>=.25R max90 [my label, not W-DYNH c90 cut rule] STRESS n 17196 car  807 | inc 1.01 ( 3648316) DD  -317420 (0.96) wk -232440 | L6 1843384/-173024 L3  863493/-162199 |  4  6  6 ---- | {2023: 266, 2024: 350, 2025: 1460, 2026: 2006}
S3 mgmt T30 STRESS         n 20583 car    0 | inc 0.73 ( 2652629) DD  -339969 (1.03) wk -185061 | L6 1810164/-171810 L3  677185/-171810 |  5  6  2 ---- | {2023: -101, 2024: 135, 2025: 899, 2026: 1936}
S4 +30 STRESS              n 17196 car    0 | inc 1.03 ( 3734544) DD  -316868 (0.96) wk -239357 | L6 1553908/-178710 L3  622711/-173888 |  5  5  7 ---- | {2023: 410, 2024: 530, 2025: 1550, 2026: 1726}
S4 +60 STRESS              n 17196 car    0 | inc 1.06 ( 3843751) DD  -278890 (0.84) wk -201378 | L6 1633538/-178710 L3  681081/-161320 |  5  5  7 ---- | {2023: 490, 2024: 401, 2025: 1643, 2026: 1766}
S4 +90 STRESS              n 17196 car    0 | inc 1.07 ( 3876438) DD  -288108 (0.87) wk -210183 | L6 1713654/-186230 L3  728109/-186230 |  3  4  7 ---- | {2023: 533, 2024: 375, 2025: 1540, 2026: 1879}
### random-carry null (same number carried, random among the trades open at the bell under REF flatten), 40 draws
S1b carry if >=0             carried 1815 of 3921 open at bell | plan inc 4454565 DD -396001 wk -243434 | null mean inc 4153402 DD -314219 wk -217481 | plan beats null: inc 0.97 DD 0.00 wk 0.12
S1c carry if >=.25R          carried 807 of 3921 open at bell | plan inc 4416420 DD -304545 wk -226439 | null mean inc 4284920 DD -309240 wk -220899 | plan beats null: inc 0.80 DD 0.62 wk 0.33
carry>=.25R max90 [my label, not W-DYNH c90 cut rule]   carried 807 of 3921 open at bell | plan inc 4351465 DD -304545 wk -226439 | null mean inc 4388570 DD -308066 wk -219126 | plan beats null: inc 0.47 DD 0.60 wk 0.28
S1a carry all                carried 3921 of 3921 open at bell | plan inc 4003620 DD -379986 wk -225681 | null mean inc 4003620 DD -379986 wk -225681 | plan beats null: inc 0.00 DD 0.00 wk 0.00
### per book (income/DD/worst wk vs REF)
  S1a carry all          MF1 inc 1.10 DD 1.16 wk 0.92
  S1a carry all          MF2 inc 0.35 DD 0.83 wk 1.07
  S1a carry all          MF3 inc 0.87 DD 1.09 wk 1.04
  S1a carry all          MF4 inc 0.60 DD 1.49 wk 1.23
  S1a carry all          MF5 inc 1.06 DD 0.95 wk 1.12
  S1a carry all          MF6 inc 0.88 DD 1.24 wk 1.40
  S1a carry all          MF7 inc 1.34 DD 1.13 wk 1.14
  S1a carry all          MF8 inc 0.93 DD 1.11 wk 0.91
  S1a carry all          MF9 inc 0.79 DD 1.32 wk 1.02
  S1b carry if >=0       MF1 inc 1.02 DD 1.15 wk 1.04
  S1b carry if >=0       MF2 inc 0.79 DD 0.87 wk 1.09
  S1b carry if >=0       MF3 inc 1.18 DD 1.03 wk 1.00
  S1b carry if >=0       MF4 inc 0.93 DD 0.95 wk 1.19
  S1b carry if >=0       MF5 inc 1.07 DD 0.88 wk 1.05
  S1b carry if >=0       MF6 inc 0.92 DD 1.04 wk 1.11
  S1b carry if >=0       MF7 inc 1.14 DD 0.86 wk 1.00
  S1b carry if >=0       MF8 inc 0.96 DD 0.93 wk 0.91
  S1b carry if >=0       MF9 inc 1.14 DD 0.99 wk 0.88
  S1c carry if >=.25R    MF1 inc 1.00 DD 0.98 wk 0.97
  S1c carry if >=.25R    MF2 inc 0.63 DD 0.88 wk 1.09
  S1c carry if >=.25R    MF3 inc 1.09 DD 0.96 wk 1.00
  S1c carry if >=.25R    MF4 inc 1.00 DD 1.00 wk 1.00
  S1c carry if >=.25R    MF5 inc 1.07 DD 0.88 wk 0.97
  S1c carry if >=.25R    MF6 inc 0.98 DD 1.00 wk 1.00
  S1c carry if >=.25R    MF7 inc 1.04 DD 0.97 wk 1.00
  S1c carry if >=.25R    MF8 inc 1.08 DD 0.98 wk 1.00
  S1c carry if >=.25R    MF9 inc 0.95 DD 0.97 wk 1.00
### REF P&L by exit kind and year ($k): 1 stop 2 target 3 bell flatten
kind        1        2      3
tx                           
2023  -3771.0   4673.0 -479.0
2024  -7840.0   9047.0 -638.0
2025 -11159.0  13177.0 -413.0
2026 -12906.0  15417.0 -296.0
bell-flatten trades: n 3921 net $-1827470 ; open R at bell median -0.03 p25 -0.29 p75 0.19 (in points -2.5)
