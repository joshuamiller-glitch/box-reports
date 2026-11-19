# COMBO_FWD_DRYRUN (W-COMBO, 2026-11-19): forward selection from an EMPTY session stack, scorer C vs EXACT production-driver stacks (L6M 202605-202610; base lots; ulcer / maxDD / worst wk / mean $/wk)

Today JL3 L6M: {'mean_wk': 18755, 'worst_wk': -15728, 'maxdd': -31109, 'ulcer': 9416}  L3M: {'mean_wk': 16098, 'worst_wk': -15728, 'maxdd': -31109, 'ulcer': 11035} 

| stack (rest of the day = JL3) | window | exact | scorer C | error (C - exact) |
|---|---|---|---|---|
| NYAM: new L01811caa + live K7 | L6M | 8904 / -26730 / -13195 / 18399 | 8742 / -26730 / -13195 / 18495 | -162 / -0 / +0 / +97 |
| NYAM: new L01811caa + live K7 | L3M | 10091 / -26647 / -11386 / 15342 | 9787 / -25233 / -12362 / 15695 | -304 / +1414 / -976 / +353 |
| NYAM: new L01811caa + new L678ebadd | L6M | 9223 / -30249 / -16493 / 21377 | 9288 / -30249 / -16493 / 21459 | +65 / +0 / +0 / +82 |
| NYAM: new L01811caa + new L678ebadd | L3M | 10355 / -28294 / -10880 / 17954 | 10472 / -29194 / -11781 / 17979 | +117 / -901 / -901 / +25 |
| NYAM forward pick: live K7+H7 + new L01811caa, L678ebadd, Lb44a3e99 | L6M | 8797 / -27960 / -14183 / 22536 | 8107 / -27960 / -14183 / 23021 | -690 / +0 / +0 / +485 |
| NYAM forward pick: live K7+H7 + new L01811caa, L678ebadd, Lb44a3e99 | L3M | 9901 / -27422 / -13994 / 18837 | 8688 / -22940 / -13109 / 18963 | -1212 / +4483 / +885 / +126 |
| Asia: live P7 + K7 | L6M | 10594 / -32555 / -29767 / 13339 | 10235 / -49670 / -46161 / 11923 | -359 / -17115 / -16394 / -1417 |
| Asia: live P7 + K7 | L3M | 13566 / -32555 / -29767 / 10585 | 12770 / -49670 / -46161 / 10320 | -797 / -17115 / -16394 / -265 |
| Asia forward pick: live P7+K7+H7 | L6M | 10167 / -34636 / -25780 / 14739 | 10125 / -48606 / -44055 / 13170 | -42 / -13970 / -18275 / -1569 |
| Asia forward pick: live P7+K7+H7 | L3M | 12373 / -34636 / -25780 / 11575 | 12643 / -48606 / -44055 / 10966 | +270 / -13970 / -18275 / -609 |

Calibration at k = all live books (exact = JL3): NYAM scorer C ulcer 9,540 vs 9,416, mean 18,647 vs 18,755 (good); ASIA scorer C ulcer 12,758 vs 9,416, worst week -52,897 vs -15,728, 6-month total 390k vs 506k (BAD: the five Asia books interact strongly; scorer C is not usable for Asia stacks of 3+ books).
