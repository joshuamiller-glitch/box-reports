# DS3_INST_C_DD - INSTITUTIONAL section C, cross-market state at the hour scale (30/60/120-min ES RTY YM ZN GC CL DXY residuals; NY-open day type): re-read under DRAWDOWN FIRST (F1, overnight order, written 2026-10-31 23:59Z)

DATA. On disk, nothing to buy: 1-min ES/RTY/YM/ZN/GC/CL/6x series (cache_te2), engine d-space signal rows (61,401). 693 cells = all INST-3 C keep-masks reconstructed with the c_stack.py code (skip = signals not kept); composite series tie to the stored C_stack.pkl to 0.004 (float32). The 8 NQ/ES pair-book cells are standalone books, not stack rules (not re-priced).

**Prereg** `prereg/F1_INSTDD_prereg.md` sha256 `b177b68129c4bf2e492749bdf8ac98d8f1da9bac3c6c7dc4bc5957806d03ae98`; stage-1 selection `out/inst_dd/stage1_selection.json` sha256 `8ce67ccbbedfc6a5810d8ac8d1d8710a45b1b17084b618b4f17cb5854f802763` logged in DECISIONS.md before the recent look. Capped 20260206; UNTOUCHED never read. Frames: Sunday composite (headline) and as-is stack, live lots (K6 2 / P6 7 / U6 4 / H6 4-2 / M6 2 / A6 1), one-convention engine (dd_lib/lib3, unchanged).
**Coverage.** 693 cells swept in this group; 57 carried on PRE and X' (composite maxDD cut >= 20% in BOTH and mean not beyond -MDE in both); 57 distinct fire vectors; 40 looked at once in L3M/L6M/HOLD/ALL (cap 40 by min(PRE cut, X' cut)); 84 more carry in the as-is frame only (not looked at).
**Family-wise.** 693 cells swept; program placebo false-carry rate of the PRE+X' criterion for same-volume random skips/size-cuts in this group: 28/200 draws = 14.0% (20 sampled cells x 10 draws; mean volume cut 41%), i.e. about 97 chance carries expected of 693 swept vs 57 observed. Bonferroni placebo p = min(1, placebo rank p x distinct carried).

### Baselines (weekly $, label weeks; maxDD of the weekly cumulative)
| window | frame | mean $/wk | SD | maxDD | worst-20 | Calmar | mean/\|worst-20\| |
|---|---|---|---|---|---|---|---|
| L3M | Sunday composite | 34,406 | 44,702 | 21,361 | n/a (<20 loss wks) | 1.611 | nan |
| L3M | as-is stack | 12,153 | 45,510 | 88,039 | n/a (<20 loss wks) | 0.138 | nan |
| L6M | Sunday composite | 41,137 | 42,743 | 22,892 | n/a (<20 loss wks) | 1.797 | nan |
| L6M | as-is stack | 21,715 | 43,891 | 88,039 | n/a (<20 loss wks) | 0.247 | nan |
| HOLD | Sunday composite | 38,574 | 51,791 | 96,995 | n/a (<20 loss wks) | 0.398 | nan |
| HOLD | as-is stack | 21,874 | 53,850 | 144,173 | n/a (<20 loss wks) | 0.152 | nan |
| PRE | Sunday composite | 23,095 | 55,723 | 241,199 | -875,191 | 0.096 | 0.0264 |
| PRE | as-is stack | 18,612 | 50,445 | 161,956 | -810,578 | 0.115 | 0.0230 |
| X' | Sunday composite | 7,955 | 32,632 | 120,500 | -419,642 | 0.066 | 0.0190 |
| X' | as-is stack | -3,410 | 28,974 | 316,507 | -572,111 | -0.011 | -0.0060 |
| ALL | Sunday composite | 22,258 | 50,318 | 241,199 | -1,098,057 | 0.092 | 0.0203 |
| ALL | as-is stack | 13,060 | 47,240 | 316,507 | -1,161,104 | 0.041 | 0.0112 |

### Table 1. Risk at live lots, composite frame, recent-first (maxDD cut = 1 - after/before; negative = deeper)

| cell | session mix of affected live signals | affected live | L3M cut | L6M maxDD before > after (cut) | HOLD cut | PRE cut | X' cut | ALL cut | worst-20 PRE b>a | X' b>a | ALL b>a | SD L6M b>a | Calmar L6M b>a | as-is L6M cut / PRE / X' |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| xm.res_ZN_30.le+1.0 | nyam 39%, asia 29%, london 24% | 3535 | -150% | 22,892 > 24,609 (-7%) | +30% | +33% | +30% | +33% | -875,191 > -1,080,323 | -419,642 > -380,804 | -1,098,057 > -1,218,165 | 42,743 > 34,770 | 1.80 > 1.23 | +45% / -87% / +8% |
| xm.res_RTY_30.ge-0.5 | nyam 45%, asia 27%, london 21% | 5205 | -52% | 22,892 > 32,492 (-42%) | +11% | +31% | +47% | +31% | -875,191 > -875,194 | -419,642 > -331,213 | -1,098,057 > -1,111,866 | 42,743 > 43,364 | 1.80 > 0.97 | +36% / -52% / +66% |
| xm.res_ES_120.le-0.5 | nyam 37%, london 27%, asia 27% | 8662 | -173% | 22,892 > 34,715 (-52%) | +65% | +46% | +45% | +46% | -875,191 > -755,276 | -419,642 > -354,603 | -1,098,057 > -899,273 | 42,743 > 30,118 | 1.80 > 0.58 | +11% / +7% / +59% |
| xm.raw_CL_30.ge+0.0 | nyam 41%, asia 26%, london 25% | 6128 | -64% | 22,892 > 34,996 (-53%) | +55% | +31% | +40% | +31% | -875,191 > -768,192 | -419,642 > -333,293 | -1,098,057 > -903,033 | 42,743 > 42,821 | 1.80 > 1.02 | +24% / +15% / +41% |
| xm.raw_RTY_30.ge-0.5 | nyam 63%, asia 19%, london 15% | 1731 | -4% | 22,892 > 36,406 (-59%) | +20% | +29% | +35% | +29% | -875,191 > -888,778 | -419,642 > -362,885 | -1,098,057 > -1,123,797 | 42,743 > 45,116 | 1.80 > 1.17 | -14% / -9% / +36% |
| xm.raw_RTY_60.ge-0.5 | nyam 63%, asia 20%, london 12% | 1890 | -79% | 22,892 > 38,245 (-67%) | +3% | +38% | +36% | +38% | -875,191 > -753,758 | -419,642 > -366,457 | -1,098,057 > -1,003,572 | 42,743 > 48,049 | 1.80 > 1.13 | -12% / +19% / +23% |
| xm.raw_GC_30.ge+1.0 | nyam 40%, asia 28%, london 24% | 10071 | -107% | 22,892 > 44,197 (-93%) | +26% | +52% | +31% | +52% | -875,191 > -608,392 | -419,642 > -221,606 | -1,098,057 > -737,351 | 42,743 > 37,585 | 1.80 > 0.58 | +31% / +62% / +61% |
| xm.res_ES_60.ge-1.0 | nyam 49%, asia 28%, london 18% | 3605 | -90% | 22,892 > 44,836 (-96%) | +42% | +41% | +25% | +41% | -875,191 > -716,101 | -419,642 > -437,116 | -1,098,057 > -961,505 | 42,743 > 38,832 | 1.80 > 0.63 | -4% / +13% / +41% |
| xm.res_GC_120.ge+0.5 | nyam 41%, asia 27%, london 24% | 8938 | -132% | 22,892 > 49,499 (-116%) | +31% | +44% | +26% | +32% | -875,191 > -831,709 | -419,642 > -205,714 | -1,098,057 > -1,005,963 | 42,743 > 38,522 | 1.80 > 0.55 | +44% / +20% / +62% |
| xm.raw_ZN_60.ge+1.0 | nyam 41%, asia 26%, london 24% | 10551 | +11% | 22,892 > 49,617 (-117%) | -8% | +40% | +35% | +40% | -875,191 > -548,502 | -419,642 > -295,363 | -1,098,057 > -781,784 | 42,743 > 30,122 | 1.80 > 0.23 | -12% / -17% / +65% |
| xm.raw_RTY_30.le+1.0 | nyam 35%, asia 30%, london 26% | 6376 | -153% | 22,892 > 50,157 (-119%) | +48% | +31% | +28% | +27% | -875,191 > -819,529 | -419,642 > -264,061 | -1,098,057 > -952,489 | 42,743 > 34,354 | 1.80 > 0.33 | -19% / -18% / +70% |
| xm.res_RTY_60.ge-1.0 | nyam 47%, asia 27%, london 19% | 3647 | -140% | 22,892 > 51,356 (-124%) | +41% | +54% | +36% | +51% | -875,191 > -817,875 | -419,642 > -370,630 | -1,098,057 > -1,038,025 | 42,743 > 46,576 | 1.80 > 0.59 | -32% / +33% / +46% |
| xm.raw_GC_30.ge+0.5 | nyam 40%, asia 28%, london 24% | 8514 | -141% | 22,892 > 51,375 (-124%) | -9% | +66% | +30% | +39% | -875,191 > -673,185 | -419,642 > -255,236 | -1,098,057 > -795,525 | 42,743 > 38,951 | 1.80 > 0.53 | +10% / +48% / +59% |
| xm.led_RTY_120.le+1.0 | nyam 41%, asia 28%, london 24% | 6112 | -146% | 22,892 > 52,530 (-129%) | +46% | +56% | +33% | +53% | -875,191 > -722,085 | -419,642 > -268,391 | -1,098,057 > -867,623 | 42,743 > 24,706 | 1.80 > 0.12 | -54% / -92% / +41% |
| xm.raw_RTY_120.le+1.0 | nyam 37%, asia 28%, london 27% | 5730 | -91% | 22,892 > 52,811 (-131%) | +24% | +27% | +47% | +27% | -875,191 > -742,950 | -419,642 > -334,625 | -1,098,057 > -892,867 | 42,743 > 35,504 | 1.80 > 0.45 | -11% / -3% / +17% |
| xm.risk_120.le+1.0 | nyam 39%, asia 28%, london 25% | 6149 | -111% | 22,892 > 53,071 (-132%) | -2% | +37% | +46% | +37% | -875,191 > -736,781 | -419,642 > -234,070 | -1,098,057 > -891,160 | 42,743 > 34,623 | 1.80 > 0.28 | -2% / -9% / +25% |
| xm.risk_60.le+1.0 | nyam 38%, asia 29%, london 25% | 6672 | -179% | 22,892 > 54,451 (-138%) | +44% | +27% | +40% | +27% | -875,191 > -627,888 | -419,642 > -289,138 | -1,098,057 > -847,381 | 42,743 > 33,759 | 1.80 > 0.26 | -23% / -26% / +61% |
| xm.res_RTY_30.ge-1.0 | nyam 46%, asia 28%, london 20% | 3595 | -13% | 22,892 > 54,745 (-139%) | +17% | +36% | +25% | +36% | -875,191 > -819,090 | -419,642 > -450,052 | -1,098,057 > -1,055,987 | 42,743 > 47,157 | 1.80 > 0.65 | -1% / -32% / +20% |
| xm.raw_YM_30.le+0.5 | nyam 35%, asia 30%, london 25% | 8876 | -183% | 22,892 > 60,515 (-164%) | +38% | +32% | +25% | +32% | -875,191 > -542,816 | -419,642 > -213,581 | -1,098,057 > -732,631 | 42,743 > 30,685 | 1.80 > 0.30 | +26% / +16% / +59% |
| xm.res_RTY_120.ge-1.0 | nyam 46%, asia 27%, london 20% | 3569 | -185% | 22,892 > 60,820 (-166%) | +37% | +48% | +30% | +48% | -875,191 > -770,388 | -419,642 > -381,120 | -1,098,057 > -948,135 | 42,743 > 43,761 | 1.80 > 0.40 | -2% / -29% / +66% |
| xm.res_RTY_60.ge-0.5 | nyam 45%, asia 27%, london 20% | 5263 | -185% | 22,892 > 60,859 (-166%) | +37% | +36% | +29% | +36% | -875,191 > -888,364 | -419,642 > -366,750 | -1,098,057 > -1,126,908 | 42,743 > 36,109 | 1.80 > 0.36 | -53% / +9% / +51% |
| xm.res_ZN_30.ge+0.0 | nyam 40%, asia 28%, london 24% | 6826 | -138% | 22,892 > 60,886 (-166%) | +37% | +27% | +33% | +27% | -875,191 > -816,718 | -419,642 > -346,269 | -1,098,057 > -995,217 | 42,743 > 42,630 | 1.80 > 0.37 | -27% / +13% / +71% |
| xm.ny_GC_ov.le+0.0 | nyam 57%, asia 30%, nypm 12% | 4801 | -226% | 22,892 > 69,668 (-204%) | +28% | +33% | +37% | +33% | -875,191 > -902,912 | -419,642 > -419,553 | -1,098,057 > -1,143,339 | 42,743 > 51,192 | 1.80 > 0.49 | +36% / -57% / -6% |
| xm.risk_30.le+0.5 | nyam 36%, asia 29%, london 25% | 9380 | -227% | 22,892 > 69,766 (-205%) | +28% | +61% | +39% | +49% | -875,191 > -512,874 | -419,642 > -248,903 | -1,098,057 > -714,900 | 42,743 > 32,144 | 1.80 > 0.19 | +8% / +26% / +69% |
| xm.raw_GC_120.le-1.0 | nyam 41%, asia 26%, london 25% | 10608 | -145% | 22,892 > 70,007 (-206%) | +28% | +31% | +25% | +31% | -875,191 > -545,531 | -419,642 > -262,603 | -1,098,057 > -681,026 | 42,743 > 35,699 | 1.80 > 0.17 | -3% / -35% / +55% |
| xm.raw_GC_60.ge+0.0 | nyam 41%, asia 28%, london 24% | 6597 | -164% | 22,892 > 73,678 (-222%) | +7% | +27% | +28% | +27% | -875,191 > -857,553 | -419,642 > -340,634 | -1,098,057 > -1,081,838 | 42,743 > 49,472 | 1.80 > 0.41 | +15% / +40% / +47% |
| xm.res_YM_120.ge-1.0 | nyam 48%, asia 27%, london 20% | 3667 | -252% | 22,892 > 75,262 (-229%) | +22% | +30% | +27% | +30% | -875,191 > -892,678 | -419,642 > -471,330 | -1,098,057 > -1,058,753 | 42,743 > 37,758 | 1.80 > 0.24 | -116% / -18% / +9% |
| xm.led_ES_60.le+1.0 | nyam 44%, asia 29%, london 22% | 5108 | -252% | 22,892 > 75,273 (-229%) | +22% | +50% | +25% | +50% | -875,191 > -711,799 | -419,642 > -446,736 | -1,098,057 > -960,770 | 42,743 > 35,098 | 1.80 > 0.23 | -26% / -20% / +42% |
| xm.raw_YM_30.le-0.5 | nyam 37%, asia 29%, london 25% | 12571 | -270% | 22,892 > 79,008 (-245%) | +19% | +73% | +44% | +67% | -875,191 > -287,671 | -419,642 > -208,737 | -1,098,057 > -457,414 | 42,743 > 19,168 | 1.80 > 0.03 | -45% / +72% / +72% |
| xm.risk_60.le+0.5 | nyam 37%, asia 28%, london 26% | 9107 | -289% | 22,892 > 83,196 (-263%) | +14% | +48% | +38% | +48% | -875,191 > -548,540 | -419,642 > -316,689 | -1,098,057 > -814,012 | 42,743 > 31,459 | 1.80 > 0.11 | -16% / -17% / +56% |
| xm.res_ZN_120.le+0.0 | nyam 40%, asia 27%, london 25% | 7295 | -149% | 22,892 > 84,604 (-270%) | +13% | +47% | +34% | +47% | -875,191 > -850,901 | -419,642 > -310,156 | -1,098,057 > -1,043,409 | 42,743 > 39,204 | 1.80 > 0.27 | -16% / +9% / +73% |
| xm.res_RTY_60.ge+0.0 | nyam 44%, asia 27%, london 22% | 7254 | -311% | 22,892 > 87,794 (-284%) | +9% | +34% | +25% | +34% | -875,191 > -855,371 | -419,642 > -327,026 | -1,098,057 > -1,086,647 | 42,743 > 31,548 | 1.80 > 0.15 | -63% / +2% / +63% |
| xm.res_ES_60.ge-0.5 | nyam 47%, asia 28%, london 19% | 5307 | -326% | 22,892 > 90,946 (-297%) | +6% | +53% | +37% | +53% | -875,191 > -702,187 | -419,642 > -427,920 | -1,098,057 > -945,379 | 42,743 > 44,678 | 1.80 > 0.24 | -90% / +15% / +54% |
| xm.res_YM_60.ge+0.0 | nyam 45%, asia 28%, london 22% | 7114 | -291% | 22,892 > 101,822 (-345%) | -5% | +53% | +33% | +53% | -875,191 > -861,507 | -419,642 > -348,240 | -1,098,057 > -1,070,098 | 42,743 > 37,227 | 1.80 > 0.11 | -4% / -8% / +24% |
| xm.res_DXY_120.le-1.0 | nyam 41%, asia 27%, london 24% | 10778 | -377% | 22,892 > 101,979 (-345%) | -5% | +29% | +46% | +29% | -875,191 > -671,088 | -419,642 > -240,453 | -1,098,057 > -823,858 | 42,743 > 39,741 | 1.80 > 0.13 | +11% / +34% / +71% |
| xm.ny_GC_ov.le-0.5 | nyam 52%, asia 37%, nypm 11% | 6802 | -440% | 22,892 > 115,407 (-404%) | -19% | +40% | +48% | +40% | -875,191 > -897,750 | -419,642 > -317,475 | -1,098,057 > -1,108,997 | 42,743 > 50,916 | 1.80 > 0.18 | +28% / -59% / +50% |
| xm.led_RTY_60.le+0.0 | nyam 40%, asia 27%, london 25% | 11466 | -212% | 22,892 > 115,483 (-404%) | -19% | +66% | +40% | +52% | -875,191 > -529,892 | -419,642 > -269,860 | -1,098,057 > -710,356 | 42,743 > 21,464 | 1.80 > 0.01 | -109% / +40% / +79% |
| xm.res_YM_60.ge-0.5 | nyam 46%, asia 28%, london 21% | 5305 | -445% | 22,892 > 116,458 (-409%) | -20% | +44% | +29% | +44% | -875,191 > -880,377 | -419,642 > -364,558 | -1,098,057 > -1,133,774 | 42,743 > 41,651 | 1.80 > 0.14 | -84% / -32% / +43% |
| xm.led_ES_60.le+0.5 | nyam 43%, asia 29%, london 22% | 7127 | -613% | 22,892 > 131,867 (-476%) | -36% | +66% | +27% | +45% | -875,191 > -597,724 | -419,642 > -409,126 | -1,098,057 > -863,283 | 42,743 > 29,654 | 1.80 > 0.08 | -115% / -14% / +37% |
| xm.led_RTY_60.le+0.5 | nyam 40%, asia 27%, london 25% | 9199 | -437% | 22,892 > 157,082 (-586%) | -62% | +43% | +28% | +35% | -875,191 > -597,607 | -419,642 > -362,008 | -1,098,057 > -794,443 | 42,743 > 28,386 | 1.80 > 0.03 | -121% / +33% / +47% |

### Table 2. Mean (MDE), equal-risk, placebo, gates, label ($/wk stack change vs the Sunday composite; MDE = 2.8 x SE of the paired weekly delta)

| cell | mean L3M | L6M (MDE) | HOLD | PRE | X' | ALL | equal-risk mean change L6M (c) | PRE | placebo L6M cut p95 / rank p | Bonf p | STRICT | TOL (literal) | NOW-ONLY | TOL-B / TOL-nc | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| xm.res_ZN_30.le+1.0 | -14,487 | -10,809 (16,858) | -8,885 | -9,738 | -3,645 | -7,886 | -16,623 (0.90) | -12,140 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.res_RTY_30.ge-0.5 | -5,643 | -9,458 (15,146) | -8,536 | -10,763 | 3,493 | -6,219 | -9,458 (1.00) | -10,763 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.res_ES_120.le-0.5 | -12,003 | -20,919 (22,490) | -18,872 | -6,809 | -4,112 | -8,695 | -16,686 (1.26) | -3,933 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.raw_CL_30.ge+0.0 | -2,036 | -5,339 (17,392) | -8,180 | -7,330 | 1,851 | -4,900 | -1,020 (1.22) | -5,951 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.raw_RTY_30.ge-0.5 | 3,282 | 1,559 (7,670) | 1,674 | -3,007 | 2,070 | -543 | -4,304 (0.95) | -6,084 | not run (does not meet the L6M definition) |  | n | n | Y | n / n | no |
| xm.raw_RTY_60.ge-0.5 | 2,400 | 2,045 (8,587) | 1,181 | -2,137 | 1,872 | -270 | 2,150 (1.14) | -1,122 | not run (does not meet the L6M definition) |  | n | n | Y | n / Y | no |
| xm.raw_GC_30.ge+1.0 | -2,965 | -15,537 (18,132) | -14,894 | -13,412 | -4,227 | -11,198 | -3,409 (1.55) | -8,597 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.res_ES_60.ge-1.0 | -15,540 | -12,727 (13,591) | -9,146 | -5,534 | -1,735 | -5,262 | -8,712 (1.18) | -4,405 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.res_GC_120.ge+0.5 | -6,197 | -13,736 (15,480) | -14,114 | -13,366 | 1,691 | -9,260 | -12,599 (1.13) | -13,428 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.raw_ZN_60.ge+1.0 | -21,182 | -29,710 (17,107) | -30,533 | -13,133 | -3,594 | -14,229 | -25,773 (1.46) | -10,536 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.raw_RTY_30.le+1.0 | -23,580 | -24,499 (23,354) | -21,257 | -7,910 | 2,172 | -7,906 | -22,777 (1.18) | -5,399 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.res_RTY_60.ge-1.0 | -10,224 | -10,732 (15,144) | -9,681 | -5,956 | 3,248 | -4,118 | -10,673 (1.06) | -6,492 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.raw_GC_30.ge+0.5 | -3,473 | -13,893 (17,459) | -14,429 | -9,956 | -1,501 | -8,553 | -3,580 (1.44) | -5,760 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.led_RTY_120.le+1.0 | -34,187 | -34,865 (21,551) | -29,469 | -13,911 | -193 | -13,388 | -33,259 (1.35) | -12,144 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.raw_RTY_120.le+1.0 | -16,351 | -17,262 (21,735) | -15,503 | -9,139 | -5,066 | -9,426 | -14,660 (1.24) | -7,326 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.risk_120.le+1.0 | -23,256 | -26,226 (20,855) | -25,344 | -11,087 | 1,669 | -10,531 | -23,098 (1.24) | -9,460 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.risk_60.le+1.0 | -29,222 | -26,734 (22,523) | -24,161 | -9,680 | 110 | -10,029 | -22,777 (1.30) | -6,248 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.res_RTY_30.ge-1.0 | -1,744 | -5,648 (12,626) | -4,753 | -6,395 | 1,230 | -3,877 | -7,053 (1.08) | -6,643 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.raw_YM_30.le+0.5 | -17,379 | -22,841 (23,579) | -22,143 | -10,570 | -931 | -10,351 | -15,673 (1.55) | -4,592 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.res_RTY_120.ge-1.0 | -16,997 | -16,578 (14,980) | -13,969 | -8,604 | 2,507 | -6,591 | -12,836 (1.25) | -6,292 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.res_RTY_60.ge-0.5 | -16,125 | -19,155 (16,017) | -17,122 | -9,616 | 2,626 | -7,742 | -19,155 (1.00) | -9,616 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.res_ZN_30.ge+0.0 | -14,241 | -18,753 (18,917) | -17,664 | -6,892 | -96 | -7,291 | -18,122 (1.15) | -6,314 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.ny_GC_ov.le+0.0 | -8,673 | -7,308 (19,580) | -5,261 | -5,921 | -3,403 | -5,115 | -10,573 (0.96) | -7,979 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.risk_30.le+0.5 | -25,594 | -27,906 (26,200) | -25,236 | -13,319 | -4,450 | -13,438 | -20,166 (1.58) | -7,597 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.raw_GC_120.le-1.0 | -20,404 | -29,523 (23,397) | -26,987 | -11,625 | -5,313 | -13,216 | -23,248 (1.61) | -5,529 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.raw_GC_60.ge+0.0 | -3,689 | -10,590 (19,312) | -10,093 | -8,473 | -2,018 | -7,028 | -10,457 (1.01) | -8,492 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.res_YM_120.ge-1.0 | -23,367 | -23,385 (18,732) | -20,246 | -8,936 | -3,189 | -9,788 | -23,117 (1.08) | -9,609 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.led_ES_60.le+1.0 | -24,864 | -24,144 (19,987) | -19,667 | -10,271 | -4,968 | -10,861 | -21,595 (1.18) | -9,593 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.raw_YM_30.le-0.5 | -28,419 | -38,973 (23,396) | -36,518 | -15,089 | -6,574 | -17,379 | -35,764 (2.47) | -4,737 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.risk_60.le+0.5 | -29,177 | -32,058 (24,397) | -29,072 | -10,762 | -5,295 | -13,224 | -29,674 (1.40) | -7,145 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.res_ZN_120.le+0.0 | -15,011 | -18,041 (19,337) | -16,205 | -10,739 | 251 | -8,812 | -16,255 (1.11) | -9,156 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.res_RTY_60.ge+0.0 | -24,294 | -28,381 (19,690) | -26,405 | -13,307 | 1,760 | -11,849 | -28,658 (1.01) | -13,001 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.res_ES_60.ge-0.5 | -22,266 | -19,241 (18,413) | -16,450 | -9,488 | -4,532 | -9,647 | -17,014 (1.19) | -9,229 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.res_YM_60.ge+0.0 | -26,640 | -30,193 (22,628) | -28,093 | -10,728 | -2,961 | -12,308 | -30,682 (1.03) | -10,919 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.res_DXY_120.le-1.0 | -25,526 | -27,753 (21,512) | -26,444 | -15,081 | 1,498 | -12,828 | -23,885 (1.33) | -13,719 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.ny_GC_ov.le-0.5 | -29,327 | -19,845 (19,817) | -17,534 | -12,470 | -642 | -10,232 | -19,845 (1.00) | -12,470 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.led_RTY_60.le+0.0 | -30,523 | -39,536 (21,612) | -36,144 | -16,466 | -4,539 | -17,391 | -39,595 (1.55) | -14,347 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.res_YM_60.ge-0.5 | -28,136 | -24,635 (22,608) | -22,607 | -9,442 | -2,173 | -10,250 | -24,635 (1.00) | -9,442 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.led_ES_60.le+0.5 | -30,882 | -30,822 (26,052) | -26,384 | -9,986 | -2,368 | -11,392 | -27,479 (1.32) | -6,893 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| xm.led_RTY_60.le+0.5 | -24,761 | -37,044 (25,886) | -33,292 | -15,156 | -2,068 | -15,390 | -34,955 (1.47) | -12,319 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |

### Reading

C (cross-market state at the hour scale): 693 cells swept, 57 cut the composite maxDD >= 20% in BOTH PRE and X-prime with the mean inside its MDE; 40 looked at once in L3M/L6M/HOLD/ALL: 0 meet the user's L6M definition (cut >= 20% with the mean inside MDE), median L6M maxDD change +166% (positive = deeper), 40 still cut ALL by >= 20%, STRICT 0 / TOLERANT 0 / NOW-ONLY 2 (TOL-B 0, TOL-nc 1); program placebo false-carry rate 14.0% at a 41% typical volume cut (about 97 chance carries of 693 vs 57 observed).

The PRE and X-prime cuts of the cross-market skips come from removing 10-80% of all signals (volume column in out/inst_dd/stage1_table.csv; the keep-masks are the weakest-aligned NQ signals at the hour scale); in L6M the same skips deepen the composite maxDD because the one L6M drawdown week (2026-01-19) is not in the skipped set and the skipped weeks carry the profit. Not one cell is RISK-KEEP, none is STRICT, none is literal TOLERANT.

Disclosure: 53 of the 57 carried cells were not looked at only through the cap (40); the 17 cut-off cells have the smaller min(PRE cut, X' cut) and are listed in out/inst_dd/stage1_table.csv.

### Notes
- Counts: STRICT/TOLERANT(literal)/NOW-ONLY over the looked cells: see Reading; TOL-B and TOL-nc are post-hoc, beside.
- dead_lookup (run before scoring): every cell here exists in the ledger under INST_D 1,044 / INST_E 396 / INST3C 701 / INST3F 134 / INSTG 36 / INST_H 16 (scored on the mean, 'EXACT' by name); this program re-prices them on drawdown. The new H4 (12) and H5 (4) cells and the engine-route H2 bracket rows have 0 hits. Appended after scoring with append_cells (program F1DD, tier PRICED), never rebuilt.
- Coverage gaps (not stack rules, not re-priced here): 8 NQ/ES pair-book cells (C), 24 close-window class books (F; C1 builds the close-fade sleeve), the stored INST-D/E s2 series (neighbours, shifted-state and random placebos, not scored cells).
- Single-week caveat: the composite L6M maxDD (22.9k) is one week (2026-01-19); the as-is L6M maxDD is the same week. L3M/L6M/HOLD have fewer than 20 losing weeks, so worst-20 is shown for PRE, X-prime, ALL only.
- Deviation from the prereg count: H4 has 12 cells, not 14 (counting error); swept total 2,311.
- Top-N by in-sample drawdown (the 40 cap in C) is post-hoc; nothing promoted; Shadow only.
- Code l2vast/ds3/code/inst_dd/, results l2vast/ds3/out/inst_dd/ (stage1_table.csv, stage2a_table.csv, final_rows.csv, summary.json), rows out/recent_wins/inst_dd.csv.
