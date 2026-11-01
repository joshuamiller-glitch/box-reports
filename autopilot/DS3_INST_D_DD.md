# DS3_INST_D_DD - INSTITUTIONAL section D, volatility-market state (options gamma, VIX term, IV-RV, variance ratio, range compression, expiry cycle): re-read under DRAWDOWN FIRST (F1, overnight order, written 2026-10-31 23:59Z)

DATA. On disk (bought 10-16, nothing new bought): CME ES/NQ option statistics, OPRA NDX/NDXP daily + 0DTE flow, CBOE VIX family, realised-vol proxies, states_D.parquet in d space. 1,044 grid cells; composite daily series re-run and tied to the stored res_grid.npz (max diff 0.0). Options quote refresh NOT needed: no state survives the recent look, so the P-D2 ($140.05) buy stays unjustified; quotes in DS3_INSTITUTIONAL.md unchanged (free get_cost only, no purchase, no download).

**Prereg** `prereg/F1_INSTDD_prereg.md` sha256 `b177b68129c4bf2e492749bdf8ac98d8f1da9bac3c6c7dc4bc5957806d03ae98`; stage-1 selection `out/inst_dd/stage1_selection.json` sha256 `8ce67ccbbedfc6a5810d8ac8d1d8710a45b1b17084b618b4f17cb5854f802763` logged in DECISIONS.md before the recent look. Capped 20260206; UNTOUCHED never read. Frames: Sunday composite (headline) and as-is stack, live lots (K6 2 / P6 7 / U6 4 / H6 4-2 / M6 2 / A6 1), one-convention engine (dd_lib/lib3, unchanged).
**Coverage.** 1044 cells swept in this group; 31 carried on PRE and X' (composite maxDD cut >= 20% in BOTH and mean not beyond -MDE in both); 31 distinct fire vectors; 31 looked at once in L3M/L6M/HOLD/ALL (cap 40 by min(PRE cut, X' cut)); 35 more carry in the as-is frame only (not looked at).
**Family-wise.** 1044 cells swept; program placebo false-carry rate of the PRE+X' criterion for same-volume random skips/size-cuts in this group: 5/200 draws = 2.5% (20 sampled cells x 10 draws; mean volume cut 6%), i.e. about 26 chance carries expected of 1044 swept vs 31 observed. Bonferroni placebo p = min(1, placebo rank p x distinct carried).

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
| vix_minus_rv20>=2.034|skip|ALL6 | asia 43%, nyam 31%, london 20% | 7316 | +53% | 22,892 > 10,090 (+56%) | +90% | +27% | +53% | +27% | -875,191 > -746,934 | -419,642 > -159,453 | -1,098,057 > -803,718 | 42,743 > 34,382 | 1.80 > 2.04 | +65% / +10% / +67% |
| vv_240>=1.009|half|ALL6 | nyam 51%, asia 37%, london 9% | 5762 | +16% | 22,892 > 19,888 (+13%) | +50% | +37% | +21% | +37% | -875,191 > -704,468 | -419,642 > -312,204 | -1,098,057 > -904,194 | 42,743 > 38,654 | 1.80 > 1.66 | -1% / +19% / +48% |
| ndx_pc_vol>=1.087|half|ALL6 | asia 42%, nyam 32%, london 20% | 6140 | +0% | 22,892 > 21,361 (+7%) | +44% | +46% | +25% | +46% | -875,191 > -730,676 | -419,642 > -365,229 | -1,098,057 > -885,572 | 42,743 > 34,794 | 1.80 > 1.24 | +0% / -1% / +21% |
| es_zgd<=-0.007012|skip|PULL | asia 58%, nyam 24%, london 18% | 1926 | +29% | 22,892 > 22,892 (+0%) | +0% | +31% | +46% | +31% | -875,191 > -879,629 | -419,642 > -387,081 | -1,098,057 > -1,048,787 | 42,743 > 40,229 | 1.80 > 1.89 | +31% / +12% / +39% |
| es_gex_norm<=-0.05538|half|ALL6 | asia 38%, nyam 33%, london 23% | 5297 | +61% | 22,892 > 22,892 (+0%) | +0% | +27% | +46% | +27% | -875,191 > -789,534 | -419,642 > -370,280 | -1,098,057 > -985,516 | 42,743 > 40,977 | 1.80 > 1.90 | +49% / -12% / +33% |
| es_zgd<=-0.007012|skip|PE | nyam 38%, asia 33%, london 29% | 1220 | +26% | 22,892 > 22,892 (+0%) | +0% | +32% | +46% | +32% | -875,191 > -890,508 | -419,642 > -384,591 | -1,098,057 > -1,056,513 | 42,743 > 40,433 | 1.80 > 1.89 | +27% / +12% / +37% |
| es_gex_norm<=-0.05538|skip|PULL | asia 57%, nyam 24%, london 18% | 1984 | +29% | 22,892 > 22,892 (+0%) | +0% | +35% | +46% | +35% | -875,191 > -853,314 | -419,642 > -396,797 | -1,098,057 > -1,036,548 | 42,743 > 41,479 | 1.80 > 1.88 | +49% / +15% / +39% |
| es_gex_norm<=-0.05538|half|PULL | asia 57%, nyam 24%, london 18% | 1984 | -3% | 22,892 > 22,892 (+0%) | +0% | +25% | +34% | +25% | -875,191 > -850,163 | -419,642 > -395,113 | -1,098,057 > -1,042,153 | 42,743 > 41,759 | 1.80 > 1.84 | +19% / -1% / +25% |
| es_zgd<=-0.007012|half|ALL6 | asia 38%, nyam 32%, london 23% | 5119 | +61% | 22,892 > 22,892 (+0%) | +0% | +23% | +46% | +23% | -875,191 > -808,424 | -419,642 > -355,583 | -1,098,057 > -996,039 | 42,743 > 39,921 | 1.80 > 1.88 | +31% / -13% / +30% |
| nq_gex_norm<=-0.01309|skip|ALL6 | asia 38%, nyam 31%, london 23% | 4942 | +53% | 22,892 > 22,892 (+0%) | +0% | +24% | +46% | +24% | -875,191 > -802,662 | -419,642 > -286,544 | -1,098,057 > -1,014,383 | 42,743 > 39,218 | 1.80 > 1.89 | +38% / -4% / +54% |
| es_zgd<=-0.007012|skip|ALL6 | asia 38%, nyam 32%, london 23% | 5119 | +64% | 22,892 > 22,892 (+0%) | +0% | +25% | +46% | +25% | -875,191 > -794,881 | -419,642 > -300,779 | -1,098,057 > -973,504 | 42,743 > 39,837 | 1.80 > 1.95 | +77% / -3% / +46% |
| nq_zgd<=-0.003022|skip|ALL6 | asia 38%, nyam 31%, london 23% | 4803 | +10% | 22,892 > 22,892 (+0%) | +0% | +25% | +46% | +25% | -875,191 > -783,081 | -419,642 > -286,379 | -1,098,057 > -997,779 | 42,743 > 41,612 | 1.80 > 1.84 | +27% / -4% / +59% |
| es_gex_norm<=-0.05538|skip|ALL6 | asia 38%, nyam 33%, london 23% | 5297 | +64% | 22,892 > 22,892 (+0%) | +0% | +25% | +37% | +25% | -875,191 > -768,232 | -419,642 > -332,913 | -1,098,057 > -983,898 | 42,743 > 41,573 | 1.80 > 1.96 | +78% / -2% / +51% |
| es_gex_norm<=-0.05538|skip|PE | nyam 38%, asia 33%, london 29% | 1267 | +22% | 22,892 > 22,892 (+0%) | +0% | +35% | +46% | +35% | -875,191 > -853,523 | -419,642 > -393,982 | -1,098,057 > -1,038,030 | 42,743 > 41,589 | 1.80 > 1.89 | +53% / +13% / +37% |
| es_gex_norm<=-0.05538|half|PE | nyam 38%, asia 33%, london 29% | 1267 | -11% | 22,892 > 23,762 (-4%) | +0% | +24% | +35% | +24% | -875,191 > -848,259 | -419,642 > -392,378 | -1,098,057 > -1,040,368 | 42,743 > 41,945 | 1.80 > 1.77 | +17% / -2% / +24% |
| ro_ratio_vix<=0.9092|half|ALL6 | asia 47%, nyam 29%, london 18% | 6297 | +0% | 22,892 > 31,633 (-38%) | +11% | +25% | +23% | +25% | -875,191 > -750,462 | -419,642 > -320,196 | -1,098,057 > -899,708 | 42,743 > 38,292 | 1.80 > 1.09 | +0% / +6% / +25% |
| nq_skew>=0.289|half|ALL6 | asia 44%, nyam 30%, london 21% | 8523 | -50% | 22,892 > 32,087 (-40%) | +31% | +24% | +29% | +24% | -875,191 > -773,411 | -419,642 > -351,153 | -1,098,057 > -940,015 | 42,743 > 26,806 | 1.80 > 0.64 | +49% / +10% / +28% |
| vv_240>=1.009|skip|PULL | asia 56%, nyam 37%, london 7% | 2181 | -58% | 22,892 > 33,673 (-47%) | +64% | +39% | +40% | +39% | -875,191 > -741,243 | -419,642 > -352,921 | -1,098,057 > -934,501 | 42,743 > 40,201 | 1.80 > 1.01 | -2% / +15% / +39% |
| vv_240>=1.009|skip|PE | nyam 58%, asia 30%, london 11% | 1390 | -58% | 22,892 > 33,673 (-47%) | +64% | +41% | +40% | +41% | -875,191 > -749,119 | -419,642 > -354,506 | -1,098,057 > -937,221 | 42,743 > 40,858 | 1.80 > 1.00 | -2% / +17% / +36% |
| vix_over_vix3m<=0.8753|skip|PE | nyam 42%, asia 37%, london 21% | 1486 | -92% | 22,892 > 40,971 (-79%) | +56% | +20% | +38% | +20% | -875,191 > -811,480 | -419,642 > -332,171 | -1,098,057 > -946,974 | 42,743 > 30,336 | 1.80 > 0.47 | +14% / +36% / +70% |
| vv_240>=1.009|skip|ALL6 | nyam 51%, asia 37%, london 9% | 5762 | -124% | 22,892 > 47,813 (-109%) | +51% | +27% | +30% | +27% | -875,191 > -744,167 | -419,642 > -309,874 | -1,098,057 > -951,810 | 42,743 > 41,287 | 1.80 > 0.63 | +1% / +35% / +51% |
| vr30_600>=1.091|half|PULL | asia 68%, nyam 19%, london 13% | 2582 | -135% | 22,892 > 50,293 (-120%) | +48% | +24% | +34% | +24% | -875,191 > -755,669 | -419,642 > -346,390 | -1,098,057 > -969,303 | 42,743 > 41,722 | 1.80 > 0.69 | -15% / +7% / +60% |
| vr30_600>=1.091|half|PE | nyam 37%, asia 37%, london 26% | 1311 | -136% | 22,892 > 50,352 (-120%) | +47% | +23% | +35% | +23% | -875,191 > -755,315 | -419,642 > -345,639 | -1,098,057 > -966,054 | 42,743 > 41,667 | 1.80 > 0.70 | -15% / +4% / +60% |
| vr30_600>=1.091|skip|PE | nyam 37%, asia 37%, london 26% | 1311 | -175% | 22,892 > 58,788 (-157%) | +39% | +25% | +47% | +25% | -875,191 > -748,539 | -419,642 > -282,411 | -1,098,057 > -932,545 | 42,743 > 44,044 | 1.80 > 0.55 | -38% / -3% / +65% |
| vr30_600>=1.091|skip|PULL | asia 68%, nyam 19%, london 13% | 2582 | -177% | 22,892 > 59,225 (-159%) | +39% | +27% | +44% | +27% | -875,191 > -724,238 | -419,642 > -285,375 | -1,098,057 > -914,228 | 42,743 > 43,961 | 1.80 > 0.54 | -36% / -1% / +66% |
| nq_skew>=0.289|skip|ALL6 | asia 44%, nyam 30%, london 21% | 8523 | -239% | 22,892 > 64,225 (-181%) | +34% | +27% | +46% | +27% | -875,191 > -747,733 | -419,642 > -270,221 | -1,098,057 > -926,144 | 42,743 > 20,524 | 1.80 > 0.04 | +44% / +10% / +43% |
| rc_15_120>=1.184|skip|PE | nyam 58%, london 26%, asia 16% | 1385 | -215% | 22,892 > 67,313 (-194%) | +31% | +38% | +35% | +38% | -875,191 > -847,980 | -419,642 > -360,310 | -1,098,057 > -1,060,485 | 42,743 > 46,759 | 1.80 > 0.47 | -3% / +16% / +17% |
| ndx_pc_vol>=1.087|skip|ALL6 | asia 42%, nyam 32%, london 20% | 6140 | -215% | 22,892 > 67,369 (-194%) | +31% | +44% | +33% | +44% | -875,191 > -687,026 | -419,642 > -363,320 | -1,098,057 > -918,526 | 42,743 > 38,800 | 1.80 > 0.17 | +0% / -18% / +25% |
| rc_15_120>=1.184|skip|PULL | asia 47%, nyam 36%, london 17% | 2189 | -227% | 22,892 > 69,770 (-205%) | +28% | +37% | +32% | +37% | -875,191 > -860,774 | -419,642 > -355,399 | -1,098,057 > -1,075,165 | 42,743 > 47,071 | 1.80 > 0.45 | -5% / +16% / +19% |
| rc_15_120>=1.184|skip|ALL6 | nyam 49%, asia 27%, london 22% | 6007 | -228% | 22,892 > 70,091 (-206%) | +28% | +26% | +50% | +26% | -875,191 > -835,841 | -419,642 > -326,500 | -1,098,057 > -998,900 | 42,743 > 45,346 | 1.80 > 0.35 | -0% / -33% / +30% |
| rc_15_120>=1.184|half|ALL6 | nyam 49%, asia 27%, london 22% | 6007 | -229% | 22,892 > 70,250 (-207%) | +28% | +32% | +26% | +32% | -875,191 > -822,625 | -419,642 > -378,504 | -1,098,057 > -1,043,484 | 42,743 > 41,351 | 1.80 > 0.45 | +2% / +12% / +29% |

### Table 2. Mean (MDE), equal-risk, placebo, gates, label ($/wk stack change vs the Sunday composite; MDE = 2.8 x SE of the paired weekly delta)

| cell | mean L3M | L6M (MDE) | HOLD | PRE | X' | ALL | equal-risk mean change L6M (c) | PRE | placebo L6M cut p95 / rank p | Bonf p | STRICT | TOL (literal) | NOW-ONLY | TOL-B / TOL-nc | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| vix_minus_rv20>=2.034|skip|ALL6 | -11,135 | -20,596 (19,351) | -20,601 | -6,893 | 2,381 | -7,191 | -16,732 (1.42) | -1,383 | -20% / 0.000 |  | n | n | n | n / n | no |
| vv_240>=1.009|half|ALL6 | -9,342 | -8,209 (9,082) | -6,155 | -981 | 77 | -1,793 | -934 (1.19) | 2,146 | +34% / 0.090 |  | n | n | n | n / n | no |
| ndx_pc_vol>=1.087|half|ALL6 | -11,065 | -14,569 (10,929) | -12,083 | -1,709 | -3,524 | -4,496 | -8,698 (1.20) | 1,368 | +28% / 0.145 |  | n | n | n | n / n | no |
| es_zgd<=-0.007012|skip|PULL | 4,287 | 2,143 (7,228) | 1,876 | -7,123 | -744 | -3,402 | 5,142 (1.11) | -7,174 | not run (does not meet the L6M definition) |  | n | n | Y | n / n | no |
| es_gex_norm<=-0.05538|half|ALL6 | 4,707 | 2,354 (5,198) | 2,060 | -3,798 | -921 | -1,741 | 2,743 (1.16) | -2,631 | not run (does not meet the L6M definition) |  | n | n | Y | n / n | no |
| es_zgd<=-0.007012|skip|PE | 4,304 | 2,152 (6,590) | 1,883 | -6,893 | -605 | -3,244 | 1,050 (1.09) | -6,181 | not run (does not meet the L6M definition) |  | n | n | Y | n / n | no |
| es_gex_norm<=-0.05538|skip|PULL | 3,824 | 1,912 (7,080) | 1,673 | -5,192 | -1,148 | -2,593 | 5,033 (1.10) | -4,810 | not run (does not meet the L6M definition) |  | n | n | Y | n / n | no |
| es_gex_norm<=-0.05538|half|PULL | 1,762 | 881 (3,704) | 771 | -3,265 | -929 | -1,752 | 3,858 (1.12) | -2,498 | not run (does not meet the L6M definition) |  | n | n | Y | n / n | no |
| es_zgd<=-0.007012|half|ALL6 | 3,826 | 1,913 (5,806) | 1,674 | -5,081 | -475 | -2,338 | 2,526 (1.15) | -4,169 | not run (does not meet the L6M definition) |  | n | n | Y | n / n | no |
| nq_gex_norm<=-0.01309|skip|ALL6 | 4,286 | 2,143 (9,076) | 1,875 | -7,354 | -607 | -3,478 | 2,837 (1.16) | -5,814 | not run (does not meet the L6M definition) |  | n | n | Y | n / n | no |
| es_zgd<=-0.007012|skip|ALL6 | 6,787 | 3,393 (10,983) | 2,969 | -10,081 | 522 | -4,282 | 5,574 (1.17) | -8,495 | not run (does not meet the L6M definition) |  | n | n | Y | n / n | no |
| nq_zgd<=-0.003022|skip|ALL6 | 2,047 | 1,023 (9,086) | 895 | -7,140 | -516 | -3,554 | 2,063 (1.15) | -5,949 | not run (does not meet the L6M definition) |  | n | n | Y | n / n | no |
| es_gex_norm<=-0.05538|skip|ALL6 | 7,344 | 3,672 (9,536) | 3,213 | -7,811 | -289 | -3,327 | 4,387 (1.16) | -6,758 | not run (does not meet the L6M definition) |  | n | n | Y | n / n | no |
| es_gex_norm<=-0.05538|skip|PE | 4,300 | 2,150 (6,468) | 1,881 | -5,126 | -915 | -2,446 | 902 (1.09) | -4,386 | not run (does not meet the L6M definition) |  | n | n | Y | n / n | no |
| es_gex_norm<=-0.05538|half|PE | 1,963 | 982 (3,412) | 859 | -3,225 | -822 | -1,682 | 3,959 (1.12) | -2,487 | not run (does not meet the L6M definition) |  | n | n | Y | n / n | no |
| ro_ratio_vix<=0.9092|half|ALL6 | -8,981 | -6,513 (10,522) | -7,794 | -2,604 | -541 | -3,144 | -2,933 (1.22) | 468 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| nq_skew>=0.289|half|ALL6 | -22,915 | -20,595 (13,321) | -19,661 | -3,717 | 816 | -5,853 | -20,659 (1.17) | -394 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| vv_240>=1.009|skip|PULL | -8,857 | -7,256 (12,498) | -5,455 | -2,092 | -443 | -2,355 | -3,873 (1.18) | 258 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| vv_240>=1.009|skip|PE | -8,702 | -7,553 (12,843) | -5,660 | -1,897 | -552 | -2,334 | -3,954 (1.17) | 325 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| vix_over_vix3m<=0.8753|skip|PE | -17,398 | -21,897 (15,335) | -21,025 | -1,014 | -1,414 | -5,443 | -20,813 (1.17) | 1,972 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| vv_240>=1.009|skip|ALL6 | -13,705 | -11,021 (17,398) | -8,951 | -4,563 | 3,266 | -3,255 | -7,481 (1.17) | -3,164 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| vr30_600>=1.091|half|PULL | -5,732 | -6,313 (7,183) | -4,687 | -2,791 | 18 | -2,406 | -2,379 (1.17) | 135 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| vr30_600>=1.091|half|PE | -5,266 | -5,765 (6,841) | -4,214 | -2,697 | 162 | -2,215 | -1,788 (1.17) | 115 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| vr30_600>=1.091|skip|PE | -7,288 | -8,915 (10,864) | -6,708 | -5,231 | 1,918 | -3,507 | -6,649 (1.18) | -3,124 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| vr30_600>=1.091|skip|PULL | -8,121 | -8,913 (10,897) | -6,642 | -5,438 | 1,536 | -3,710 | -3,752 (1.20) | -2,341 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| nq_skew>=0.289|skip|ALL6 | -39,583 | -38,365 (22,167) | -37,248 | -8,082 | 1,816 | -11,532 | -40,707 (1.19) | -4,966 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| rc_15_120>=1.184|skip|PE | -10,325 | -9,618 (16,367) | -7,508 | -2,224 | -211 | -2,794 | -9,961 (1.08) | -2,327 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| ndx_pc_vol>=1.087|skip|ALL6 | -22,583 | -29,924 (20,774) | -25,133 | -2,506 | -5,413 | -8,258 | -26,388 (1.20) | 715 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| rc_15_120>=1.184|skip|PULL | -10,101 | -9,668 (16,741) | -7,606 | -3,491 | 474 | -3,251 | -9,704 (1.02) | -3,279 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| rc_15_120>=1.184|skip|ALL6 | -13,083 | -16,723 (19,855) | -14,296 | -6,712 | 2,720 | -5,646 | -15,755 (1.10) | -5,934 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |
| rc_15_120>=1.184|half|ALL6 | -9,539 | -9,277 (11,763) | -8,460 | -3,282 | 552 | -3,306 | -8,962 (1.09) | -2,148 | not run (does not meet the L6M definition) |  | n | n | n | n / n | no |

### Reading

D (volatility-market state): 1044 cells swept, 31 cut the composite maxDD >= 20% in BOTH PRE and X-prime with the mean inside its MDE; 31 looked at once in L3M/L6M/HOLD/ALL: 0 meet the user's L6M definition (cut >= 20% with the mean inside MDE), median L6M maxDD change +38% (positive = deeper), 31 still cut ALL by >= 20%, STRICT 0 / TOLERANT 0 / NOW-ONLY 12 (TOL-B 0, TOL-nc 0); program placebo false-carry rate 2.5% at a 6% typical volume cut (about 26 chance carries of 1044 vs 31 observed).

The states that cut PRE and X-prime are the same ones INST-D had on the mean (negative ES/NQ gamma, vol-of-vol, 15-min realised-vol ratio, NDX put/call volume): skips are mostly small (6% typical volume) and the L6M window has no negative-gamma days to act on (cut 0.0% = the rule never fires in L6M), so no recent evidence either way. The only D cell that cuts L6M by >= 20% (vix_minus_rv20 >= 2.03, skip ALL6, +56%) costs -20.6k/wk (MDE 19.4k), beyond its MDE, so it is not a RISK-KEEP; half-sizing cells deepen L6M. Options quote refresh was not needed (no purchase is justified).

### Notes
- Counts: STRICT/TOLERANT(literal)/NOW-ONLY over the looked cells: see Reading; TOL-B and TOL-nc are post-hoc, beside.
- dead_lookup (run before scoring): every cell here exists in the ledger under INST_D 1,044 / INST_E 396 / INST3C 701 / INST3F 134 / INSTG 36 / INST_H 16 (scored on the mean, 'EXACT' by name); this program re-prices them on drawdown. The new H4 (12) and H5 (4) cells and the engine-route H2 bracket rows have 0 hits. Appended after scoring with append_cells (program F1DD, tier PRICED), never rebuilt.
- Coverage gaps (not stack rules, not re-priced here): 8 NQ/ES pair-book cells (C), 24 close-window class books (F; C1 builds the close-fade sleeve), the stored INST-D/E s2 series (neighbours, shifted-state and random placebos, not scored cells).
- Single-week caveat: the composite L6M maxDD (22.9k) is one week (2026-01-19); the as-is L6M maxDD is the same week. L3M/L6M/HOLD have fewer than 20 losing weeks, so worst-20 is shown for PRE, X-prime, ALL only.
- Deviation from the prereg count: H4 has 12 cells, not 14 (counting error); swept total 2,311.
- Top-N by in-sample drawdown (the 40 cap in C) is post-hoc; nothing promoted; Shadow only.
- Code l2vast/ds3/code/inst_dd/, results l2vast/ds3/out/inst_dd/ (stage1_table.csv, stage2a_table.csv, final_rows.csv, summary.json), rows out/recent_wins/inst_dd.csv.
