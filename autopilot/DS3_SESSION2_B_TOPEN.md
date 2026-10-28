# DS3_SESSION2_B_TOPEN - T-OPEN B2 (11,953 cells) re-scored by entry session and by 09:30-11:00 sub-window with the entry clock (D3SB1, T-SESSION-2 item B1)
Written 2026-10-28T20:56Z. Research only; nothing live. Label days after 2026-02-06 never read. Prereg l2vast/ds3/prereg/SB1_prereg.md sha256 766047a36d7bc839dc20e871114ad96638957447ae05fcbaae799d6df02e99ac; PREHOLD list autopilot/DS3_SESSION2_B_TOPEN_PREHOLD.md sha256 42ad1b9b7989912835311f5d74b413d6df07df02ddc275a0ed64931028eb2267 (hashed before HOLD/X were read; one HOLD and one X look, logged in out/sb1/looks.jsonl). Code l2vast/ds3/code/sb1/, outputs l2vast/ds3/out/sb1/.

## 1. Headline
- **Session book candidates on the stored basis: 938 cell-windows (563 cells, 44 independent overlap clusters); SESSION-PASS: 0.** After the analytic MEASURED adjustment (entry +1 tick, stop slippage at the $1,000-risk lot level, no mapped stop credit): 823 cell-windows alive, 41 clusters. Every alive window is NY-AM or a sub-window of it; there is no ASIA, LONDON, PREOPEN, NY-PM or CLOSE survivor (no PRE-selected cell there).
- All 35 pooled PASS/CANDIDATE harness labels of T-OPEN were one idea (DR5m pb1/pb3 rm0.5); the session screen alive set is much broader (open-drive continuation DR and OR-break cells with 10-120 pt brackets in 09:30-10:00) but it is the same mechanism: 730 of 938 alive cell-windows (450 cells) FAIL the harness's random-direction bracket-beta gate (beats_beta). The session score here uses only the sign-flip placebo (SS2 convention), so wide-target long-hold brackets can look alive purely from bracket convexity (random-direction 09:31 entries earn +1.2k..+4.2k $/wk, README_OPEN2 section 5). Treat the wide-bracket cells as beta until the replay and a beta-adjusted comparison say otherwise.
- Best-of-F is a label: BOF_F cleared by 0 alive windows, BOF_Feff by 0; smallest PRE one-sided p = 2.03e-05 against F6 = 71,646 (p x F = 1.5). That is why no SESSION-PASS: every alive window is a CANDIDATE (half size).

## 2. Counts and multiplicity
Cells in the rows jsons: 11,953 (11,689 NQ + 264 SECONDOPENS); 11,941 have trades (12 empty in the source harness). F6 = 11,941 x 6 = 71,646; sub-windows F_sub = 47,764; F_all = 119,410. Overlap clusters (Jaccard >= 0.5 on PRE entry minute+side): 683 (F_eff6 = 4,098). PRE-selected: 1479 cell-windows (63 clusters); chance at 2.5% one-sided per independent test is about 171 cluster-windows, but cells within a cluster share trades and the 10 windows overlap (4 sub-windows nest in NY-AM), so the selected count is an upper bound on independent evidence.

### Alive per session / sub-window
|              |   tested_n100 |   selected_cellwin |   sel_clusters |   alive_stored |   alive_clusters_stored |   alive_measured |   alive_clusters_measured |
|:-------------|--------------:|-------------------:|---------------:|---------------:|------------------------:|-----------------:|--------------------------:|
| ASIA         |             0 |                  0 |              0 |              0 |                       0 |                0 |                         0 |
| LONDON       |            84 |                  0 |              0 |              0 |                       0 |                0 |                         0 |
| PREOPEN      |           102 |                  0 |              0 |              0 |                       0 |                0 |                         0 |
| NY-AM        |          7491 |                778 |             57 |            483 |                      41 |              421 |                        37 |
| NY-PM        |             0 |                  0 |              0 |              0 |                       0 |                0 |                         0 |
| CLOSE        |             0 |                  0 |              0 |              0 |                       0 |                0 |                         0 |
| W1_0930-0945 |          4853 |                433 |             35 |            297 |                      26 |              285 |                        26 |
| W2_0945-1000 |          1648 |                227 |             13 |            145 |                      10 |              109 |                         7 |
| W3_1000-1030 |           719 |                 37 |              7 |             12 |                       3 |                8 |                         2 |
| W4_1030-1100 |           309 |                  4 |              1 |              1 |                       1 |                0 |                         0 |
tested_n100 = cell-windows with >= 100 PRE trades; selected = PRE n>=100, mean>0, week-cluster CI lo>0; alive = SESSION-CANDIDATE after the one HOLD look (stored basis) / after the analytic MEASURED gates.

New session books found (stored / MEASURED, independent clusters): ASIA 0/0, LONDON 0/0, PREOPEN 0/0, NY-AM 41/37, NY-PM 0/0, CLOSE 0/0 (sub-windows W1 26/26, W2 10/7, W3 3/2, W4 1/0).

### Alive by family
| family      |   alive_cellwin |   cells |   clusters |   measured_alive |
|:------------|----------------:|--------:|-----------:|-----------------:|
| B3GRID      |             371 |     203 |          7 |              325 |
| CONF        |              32 |      18 |          4 |               29 |
| DRbase      |              24 |      17 |          8 |               21 |
| DRcond      |             284 |     169 |         15 |              263 |
| ORbase      |              47 |      30 |         13 |               41 |
| ORcond      |             122 |      84 |         20 |               93 |
| ORre        |              16 |      14 |          6 |               13 |
| PB          |              32 |      23 |          6 |               28 |
| PM          |               4 |       2 |          2 |                4 |
| SECONDOPENS |               6 |       3 |          1 |                6 |

## 3. Top 30 session-restricted cell-windows by PRE t, regardless of verdict (failed gate, MDE; $ per trade at 10 NQ lots as stored, scored basis)
| cell | window | n | tpw | PRE mean $ | MDE $ | t | HOLD n | HOLD mean | H25 | H26 | 2023 span | 2023 | 2024 | 2025 | PRE meas | HOLD meas | HOLD 2x | tier | tier MEAS | failed gate | BOF | pooled verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PB_ORX_H_F30 | NY-AM | 116 | 1.5 | 2,108 | 1,352 | 4.37 | 56 | 572 | 748 | -73 | -161 | -73 | 1,837 | 1,415 | 1,574 | -412 | 324 | DEAD-IN-HOLD | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c2_X20_120 | W2_0945-1000 | 290 | 3.9 | 2,496 | 1,736 | 4.02 | 118 | 2,024 | 1,036 | 6,587 | -408 | -388 | 2,796 | 1,289 | 1,951 | 1,917 | 1,776 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c2_X20_120 | NY-AM | 304 | 4.1 | 2,390 | 1,682 | 3.98 | 126 | 1,858 | 960 | 6,102 | -395 | -349 | 2,553 | 1,299 | 1,860 | 1,740 | 1,610 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c2_X30_90 | W2_0945-1000 | 290 | 3.9 | 2,063 | 1,493 | 3.87 | 118 | 1,100 | 427 | 4,209 | 124 | 314 | 2,173 | 910 | 1,617 | 505 | 852 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| PB_ORX_T_F60 | NY-AM | 119 | 1.6 | 3,668 | 2,657 | 3.86 | 58 | -73 | -73 | -73 | -658 | -533 | 3,749 | 1,171 | 2,879 | -1,411 | -322 | DEAD-IN-HOLD | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | DEAD |
| OR5m_stp_ge1_F45 | NY-AM | 188 | 2.5 | 2,135 | 1,558 | 3.84 | 83 | 253 | 331 | -73 | -775 | -688 | 1,758 | 1,236 | 1,735 | -294 | 4 | DEAD-IN-HOLD | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c2_X30_90 | NY-AM | 304 | 4.1 | 1,976 | 1,489 | 3.72 | 126 | 1,164 | 619 | 3,740 | 151 | 218 | 2,118 | 1,000 | 1,540 | 583 | 916 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| PB_ORX_H_F60 | NY-AM | 116 | 1.5 | 3,890 | 2,957 | 3.68 | 56 | -503 | -73 | -2,078 | -443 | -291 | 4,360 | 917 | 3,282 | -1,440 | -751 | DEAD-IN-HOLD | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | DEAD |
| DR15m_hl_mv10__c3_X60_120 | NY-AM | 261 | 3.5 | 3,755 | 2,879 | 3.65 | 105 | 847 | 345 | 2,984 | -419 | -353 | 3,115 | 2,401 | 3,639 | 442 | 599 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c3_X40_120 | NY-AM | 304 | 4.1 | 2,999 | 2,300 | 3.65 | 126 | 1,822 | 1,087 | 5,297 | 367 | 337 | 3,107 | 1,794 | 3,029 | 1,505 | 1,574 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| LV_RN_BH_F60 | NY-AM | 160 | 2.1 | 2,699 | 2,075 | 3.64 | 89 | 690 | 192 | 3,362 | 359 | -157 | 3,339 | 826 | 2,021 | 142 | 442 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c3_X40_120 | W2_0945-1000 | 290 | 3.9 | 3,025 | 2,327 | 3.64 | 118 | 1,786 | 888 | 5,935 | 337 | 466 | 3,039 | 1,713 | 2,958 | 1,472 | 1,538 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| OR15m_stp_le1_F60 | NY-AM | 179 | 2.4 | 2,579 | 1,987 | 3.63 | 72 | 1,560 | 869 | 5,393 | -1,627 | -1,595 | 2,727 | 1,326 | 2,190 | 978 | 1,312 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_hl_mv20_F60 | W2_0945-1000 | 188 | 2.5 | 2,789 | 2,162 | 3.61 | 90 | 864 | 789 | 1,129 | -399 | -439 | 2,811 | 1,559 | 2,128 | 565 | 616 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| PB_M50_B_F45 | NY-AM | 104 | 1.4 | 3,224 | 2,501 | 3.61 | 52 | 2,356 | 3,365 | -1,878 | 256 | 493 | 3,341 | 2,857 | 2,642 | 2,059 | 2,108 | DEAD-IN-HOLD | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | DEAD |
| DR5m_pb1_rm0.5__D0_SCALE | W1_0930-0945 | 115 | 1.5 | 3,295 | 2,561 | 3.60 | 53 | 2,779 | 2,109 | 5,071 | 1,175 | 951 | 2,985 | 2,995 | 3,384 | 2,248 | 2,531 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | CANDIDATE |
| DR5m_pb1_rm0.5__D0_SCALE | NY-AM | 115 | 1.5 | 3,295 | 2,561 | 3.60 | 53 | 2,779 | 2,109 | 5,071 | 1,175 | 951 | 2,985 | 2,995 | 3,384 | 2,248 | 2,531 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | CANDIDATE |
| DR15m_hl_mv20_F60 | NY-AM | 208 | 2.8 | 2,786 | 2,167 | 3.60 | 97 | 1,169 | 1,179 | 1,129 | -320 | -411 | 2,513 | 2,058 | 2,145 | 841 | 920 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_hl_mv20_F45 | W2_0945-1000 | 188 | 2.5 | 2,135 | 1,666 | 3.59 | 90 | 1,634 | 1,606 | 1,732 | -538 | -223 | 1,932 | 1,620 | 1,457 | 1,034 | 1,385 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c2_X30_120 | W2_0945-1000 | 290 | 3.9 | 2,436 | 1,908 | 3.58 | 118 | 1,150 | 306 | 5,051 | 202 | 484 | 2,940 | 592 | 2,255 | 963 | 691 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| PB_VWAP_B_ORX | NY-AM | 113 | 1.5 | 4,556 | 3,572 | 3.57 | 50 | 2,565 | 3,606 | -2,182 | -17 | 275 | 3,956 | 4,093 | 4,169 | 3,084 | 2,316 | DEAD-IN-HOLD | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | DEAD |
| OR3m_rt15_F60 | W1_0930-0945 | 131 | 1.7 | 3,366 | 2,640 | 3.57 | 54 | 1,558 | 2,129 | -73 | -286 | -297 | 4,449 | 1,510 | 2,976 | 1,842 | 1,310 | DEAD-IN-HOLD | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | DEAD |
| PB_EMA_B_ORX | NY-AM | 121 | 1.6 | 4,026 | 3,177 | 3.55 | 59 | 880 | -256 | 4,902 | 1,126 | 407 | 4,667 | 1,240 | 3,670 | 803 | 632 | DEAD-IN-HOLD | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | DEAD |
| PB_ORX_T_SCALE | NY-AM | 119 | 1.6 | 3,107 | 2,466 | 3.53 | 58 | 573 | 655 | 258 | -288 | -344 | 3,528 | 1,167 | 3,033 | 326 | 324 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c2_X30_120 | NY-AM | 304 | 4.1 | 2,388 | 1,895 | 3.53 | 126 | 1,293 | 605 | 4,546 | 294 | 419 | 2,925 | 768 | 2,208 | 1,107 | 829 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_hl_rm0.5_F60 | W2_0945-1000 | 171 | 2.3 | 2,721 | 2,194 | 3.47 | 77 | 707 | 130 | 2,599 | -736 | -687 | 2,755 | 1,072 | 2,049 | 453 | 459 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| PB_ORX_H_F45 | NY-AM | 116 | 1.5 | 2,608 | 2,112 | 3.46 | 56 | -396 | -73 | -1,578 | -327 | -210 | 2,840 | 670 | 2,055 | -916 | -644 | DEAD-IN-HOLD | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | DEAD |
| OR30m_stp_ge1_F30 | W3_1000-1030 | 155 | 2.1 | 1,676 | 1,357 | 3.46 | 65 | -551 | -682 | -73 | -73 | -335 | 1,473 | 729 | 1,485 | -1,065 | -799 | DEAD-IN-HOLD | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | DEAD |
| OR30m_stp_ge1_F30 | NY-AM | 155 | 2.1 | 1,676 | 1,357 | 3.46 | 65 | -551 | -682 | -73 | -73 | -335 | 1,473 | 729 | 1,485 | -1,065 | -799 | DEAD-IN-HOLD | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | DEAD |
| DR10m_pb1_rm0.5__c3_X40_90 | W1_0930-0945 | 201 | 2.7 | 2,480 | 2,010 | 3.46 | 90 | 4,024 | 2,866 | 8,354 | -626 | -584 | 3,147 | 1,780 | 2,041 | 3,519 | 3,776 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |

Failed gate empty = passes the PRE and HOLD gates. mde = per-trade MDE $ (2.8 x week-cluster SE). PRE meas / HOLD meas = analytic MEASURED mean $/trade.

## 4. One representative per overlap cluster (alive on the stored basis, best PRE t), top 40 of 44
| cell | window | n | tpw | PRE mean $ | MDE $ | t | HOLD n | HOLD mean | H25 | H26 | 2023 span | 2023 | 2024 | 2025 | PRE meas | HOLD meas | HOLD 2x | tier | tier MEAS | failed gate | BOF | pooled verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| DR15m_pb3_mv10__c2_X20_120 | W2_0945-1000 | 290 | 3.9 | 2,496 | 1,736 | 4.02 | 118 | 2,024 | 1,036 | 6,587 | -408 | -388 | 2,796 | 1,289 | 1,951 | 1,917 | 1,776 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_hl_mv10__c3_X60_120 | NY-AM | 261 | 3.5 | 3,755 | 2,879 | 3.65 | 105 | 847 | 345 | 2,984 | -419 | -353 | 3,115 | 2,401 | 3,639 | 442 | 599 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| LV_RN_BH_F60 | NY-AM | 160 | 2.1 | 2,699 | 2,075 | 3.64 | 89 | 690 | 192 | 3,362 | 359 | -157 | 3,339 | 826 | 2,021 | 142 | 442 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| OR15m_stp_le1_F60 | NY-AM | 179 | 2.4 | 2,579 | 1,987 | 3.63 | 72 | 1,560 | 869 | 5,393 | -1,627 | -1,595 | 2,727 | 1,326 | 2,190 | 978 | 1,312 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR5m_pb1_rm0.5__D0_SCALE | W1_0930-0945 | 115 | 1.5 | 3,295 | 2,561 | 3.60 | 53 | 2,779 | 2,109 | 5,071 | 1,175 | 951 | 2,985 | 2,995 | 3,384 | 2,248 | 2,531 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | CANDIDATE |
| PB_ORX_T_SCALE | NY-AM | 119 | 1.6 | 3,107 | 2,466 | 3.53 | 58 | 573 | 655 | 258 | -288 | -344 | 3,528 | 1,167 | 3,033 | 326 | 324 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| DR10m_pb1_rm0.5__c3_X40_90 | W1_0930-0945 | 201 | 2.7 | 2,480 | 2,010 | 3.46 | 90 | 4,024 | 2,866 | 8,354 | -626 | -584 | 3,147 | 1,780 | 2,041 | 3,519 | 3,776 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| OR10m_stp_ge1_F45 | NY-AM | 187 | 2.5 | 2,002 | 1,653 | 3.39 | 84 | 356 | 331 | 457 | 1,220 | 905 | 2,589 | 632 | 1,620 | -194 | 108 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| OR5m_stp_ge1_SCALE | NY-AM | 188 | 2.5 | 2,124 | 1,785 | 3.33 | 83 | 1,756 | 1,159 | 4,256 | -586 | -575 | 1,940 | 1,528 | 1,892 | 1,442 | 1,508 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR5m_pb3_rm0.5_SCALE | W1_0930-0945 | 150 | 2.0 | 2,803 | 2,408 | 3.26 | 68 | 2,257 | 2,259 | 2,250 | -535 | -907 | 2,716 | 2,534 | 2,562 | 2,450 | 2,009 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| OR3m_c2__O0_SCALE | W1_0930-0945 | 203 | 2.7 | 2,152 | 1,864 | 3.23 | 91 | 2,487 | 1,983 | 5,041 | 264 | 347 | 2,216 | 1,762 | 2,270 | 2,200 | 2,239 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| OR30m_stp_ge0.5_F60 | W3_1000-1030 | 297 | 4.0 | 2,181 | 1,896 | 3.22 | 125 | 887 | 598 | 2,171 | 278 | 46 | 2,645 | 905 | 1,800 | 333 | 639 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| OR5m_c2_ge1_F45 | W1_0930-0945 | 138 | 1.8 | 2,150 | 2,034 | 2.96 | 60 | 1,130 | 1,104 | 1,216 | -472 | -383 | 1,619 | 1,922 | 1,614 | 1,125 | 882 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR10m_hl_rm0.5_F60 | NY-AM | 185 | 2.5 | 2,513 | 2,394 | 2.94 | 84 | 3,646 | 2,886 | 7,142 | 970 | 783 | 3,464 | 1,869 | 2,125 | 3,009 | 3,398 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR3m_hl_mv20_SCALE | W1_0930-0945 | 137 | 1.8 | 2,491 | 2,392 | 2.92 | 65 | 2,634 | 2,457 | 3,276 | -441 | 246 | 2,079 | 2,204 | 2,243 | 2,747 | 2,385 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| OR15m_2cl_le1.5_F60 | NY-AM | 273 | 3.6 | 1,844 | 1,835 | 2.81 | 111 | 767 | 149 | 4,436 | -513 | -717 | 1,964 | 834 | 1,529 | 214 | 519 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| DR3m_pb1_mv20_SCALE | W1_0930-0945 | 180 | 2.4 | 2,155 | 2,149 | 2.81 | 94 | 2,711 | 1,757 | 7,736 | -757 | -760 | 2,401 | 1,591 | 2,362 | 2,097 | 2,463 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR5m_hl_rm0.5_F60 | W1_0930-0945 | 126 | 1.7 | 2,832 | 2,904 | 2.73 | 60 | 2,332 | 1,931 | 3,935 | 1,133 | 1,015 | 2,890 | 2,279 | 2,434 | 1,725 | 2,083 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| OR3m_rt15_T1200 | NY-AM | 160 | 2.1 | 4,329 | 4,448 | 2.73 | 63 | 2,998 | 1,871 | 6,941 | -1,814 | -1,472 | 4,161 | 2,623 | 4,245 | 3,068 | 2,749 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| PB_M50_T_STRAIL | NY-AM | 148 | 2.0 | 2,890 | 2,975 | 2.72 | 71 | 930 | 688 | 2,010 | -660 | -397 | 2,299 | 1,820 | 2,487 | 896 | 681 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| OR30s_c2_le1.5__D3_T1200 | NY-AM | 178 | 2.4 | 4,262 | 4,406 | 2.71 | 75 | 3,258 | 1,789 | 14,035 | -532 | -711 | 2,500 | 4,538 | 4,022 | 3,867 | 3,010 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| PB_VWAP_T_STRAIL | W1_0930-0945 | 123 | 1.6 | 3,158 | 3,297 | 2.68 | 57 | 2,468 | 2,463 | 2,488 | 240 | 468 | 2,426 | 3,144 | 3,032 | 2,401 | 2,219 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| PB_EMA_T_ORX | W1_0930-0945 | 102 | 1.4 | 3,159 | 3,311 | 2.67 | 44 | 2,393 | 2,566 | 1,802 | 1,182 | 1,421 | 2,365 | 3,452 | 2,631 | 1,775 | 2,144 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR3m_mark_mv15_SCALE | W1_0930-0945 | 218 | 2.9 | 1,935 | 2,031 | 2.67 | 107 | 1,896 | 1,853 | 2,124 | 189 | 152 | 2,147 | 1,630 | 1,567 | 1,738 | 1,647 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| OR15m_c5_le1.5_F60 | W2_0945-1000 | 166 | 2.2 | 2,321 | 2,441 | 2.66 | 67 | 724 | 216 | 5,080 | -1,345 | -1,658 | 2,122 | 1,500 | 1,624 | 171 | 476 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| OR30m_c2_le1_F60 | NY-AM | 147 | 2.0 | 2,104 | 2,282 | 2.58 | 50 | 473 | 532 | 109 | 385 | -423 | 2,437 | 1,559 | 1,723 | -49 | 224 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| SO_NQ0930_DRV15c_S1T1.5 | NY-AM | 269 | 3.6 | 2,290 | 2,490 | 2.57 | 111 | 2,800 | 2,573 | 3,771 | -516 | -178 | 2,070 | 2,145 | 2,290 | 2,800 | 2,723 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR5m_mark_rm0.5_T1030 | W1_0930-0945 | 170 | 2.3 | 3,126 | 3,421 | 2.56 | 80 | 1,126 | 13 | 5,580 | -246 | -420 | 2,855 | 1,576 | 3,004 | 1,046 | 878 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| OR15m_c1_le1.5_F60 | NY-AM | 286 | 3.8 | 1,537 | 1,691 | 2.55 | 120 | 715 | 30 | 4,357 | -943 | -1,269 | 1,562 | 815 | 1,318 | 277 | 467 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| DR10m_pb3_SCALE | NY-AM | 363 | 4.8 | 1,205 | 1,349 | 2.50 | 157 | 849 | 260 | 3,820 | -428 | -262 | 1,067 | 599 | 1,015 | 574 | 601 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| OR60m_stp_ge0.5_F60 | NY-AM | 201 | 2.7 | 1,804 | 2,033 | 2.48 | 94 | 298 | 171 | 917 | -170 | 296 | 2,452 | -356 | 1,608 | -233 | 50 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| PMXA_X4a_HOLD | W1_0930-0945 | 179 | 2.4 | 7,211 | 8,204 | 2.46 | 76 | 4,169 | 2,263 | 13,405 | -107 | 616 | 3,297 | 7,587 | 7,054 | 4,019 | 3,762 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| OR2m_c5p_le1.5_T1200 | NY-AM | 305 | 4.1 | 2,296 | 2,614 | 2.46 | 128 | 1,449 | 909 | 4,546 | -663 | -489 | 2,546 | 917 | 2,452 | 1,528 | 1,201 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR2m_hl_mv10_F60 | W1_0930-0945 | 182 | 2.4 | 2,086 | 2,392 | 2.44 | 77 | 1,763 | 1,407 | 3,362 | 374 | 716 | 1,392 | 2,031 | 1,523 | 1,172 | 1,514 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR3m_pb3_rm0.5_T1030 | NY-AM | 127 | 1.7 | 3,462 | 4,108 | 2.36 | 69 | 1,491 | 294 | 7,177 | -75 | -21 | 4,322 | 528 | 3,569 | 1,235 | 1,242 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR2m_pb1_mv15_T1200 | W1_0930-0945 | 189 | 2.5 | 3,416 | 4,106 | 2.33 | 94 | 3,629 | 2,105 | 12,341 | -32 | -170 | 2,264 | 3,526 | 3,293 | 3,409 | 3,381 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| OR30s_2cl_le1.5_T1200 | W1_0930-0945 | 301 | 4.0 | 2,399 | 2,916 | 2.30 | 125 | 3,238 | 2,973 | 4,632 | -343 | -227 | 1,767 | 3,035 | 2,431 | 3,161 | 2,990 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| PB_VWAP_H_ORX | NY-AM | 142 | 1.9 | 2,666 | 3,256 | 2.29 | 69 | 2,688 | 2,029 | 5,818 | 310 | 554 | 3,089 | 1,553 | 2,212 | 3,292 | 2,439 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| OR3m_2cl_T1200 | W1_0930-0945 | 277 | 3.7 | 2,620 | 3,230 | 2.27 | 117 | 1,457 | 376 | 5,876 | 308 | 595 | 2,521 | 1,267 | 2,704 | 1,383 | 1,208 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_pb1_mv20_F60 | W2_0945-1000 | 242 | 3.2 | 1,571 | 1,968 | 2.24 | 113 | 1,930 | 1,357 | 4,299 | 408 | 466 | 1,472 | 1,429 | 1,349 | 1,133 | 1,682 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |


## 5. Dead pooled, alive in a session (pooled rows verdict DEAD or pooled all-hours PRE mean <= 0, tier CANDIDATE/PASS): 883 cell-windows, 532 cells, 44 clusters
| cell | window | n | tpw | PRE mean $ | MDE $ | t | HOLD n | HOLD mean | H25 | H26 | 2023 span | 2023 | 2024 | 2025 | PRE meas | HOLD meas | HOLD 2x | tier | tier MEAS | failed gate | BOF | pooled verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| DR15m_pb3_mv10__c2_X20_120 | W2_0945-1000 | 290 | 3.9 | 2,496 | 1,736 | 4.02 | 118 | 2,024 | 1,036 | 6,587 | -408 | -388 | 2,796 | 1,289 | 1,951 | 1,917 | 1,776 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c2_X20_120 | NY-AM | 304 | 4.1 | 2,390 | 1,682 | 3.98 | 126 | 1,858 | 960 | 6,102 | -395 | -349 | 2,553 | 1,299 | 1,860 | 1,740 | 1,610 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c2_X30_90 | W2_0945-1000 | 290 | 3.9 | 2,063 | 1,493 | 3.87 | 118 | 1,100 | 427 | 4,209 | 124 | 314 | 2,173 | 910 | 1,617 | 505 | 852 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c2_X30_90 | NY-AM | 304 | 4.1 | 1,976 | 1,489 | 3.72 | 126 | 1,164 | 619 | 3,740 | 151 | 218 | 2,118 | 1,000 | 1,540 | 583 | 916 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_hl_mv10__c3_X60_120 | NY-AM | 261 | 3.5 | 3,755 | 2,879 | 3.65 | 105 | 847 | 345 | 2,984 | -419 | -353 | 3,115 | 2,401 | 3,639 | 442 | 599 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c3_X40_120 | NY-AM | 304 | 4.1 | 2,999 | 2,300 | 3.65 | 126 | 1,822 | 1,087 | 5,297 | 367 | 337 | 3,107 | 1,794 | 3,029 | 1,505 | 1,574 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| LV_RN_BH_F60 | NY-AM | 160 | 2.1 | 2,699 | 2,075 | 3.64 | 89 | 690 | 192 | 3,362 | 359 | -157 | 3,339 | 826 | 2,021 | 142 | 442 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c3_X40_120 | W2_0945-1000 | 290 | 3.9 | 3,025 | 2,327 | 3.64 | 118 | 1,786 | 888 | 5,935 | 337 | 466 | 3,039 | 1,713 | 2,958 | 1,472 | 1,538 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| OR15m_stp_le1_F60 | NY-AM | 179 | 2.4 | 2,579 | 1,987 | 3.63 | 72 | 1,560 | 869 | 5,393 | -1,627 | -1,595 | 2,727 | 1,326 | 2,190 | 978 | 1,312 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_hl_mv20_F60 | W2_0945-1000 | 188 | 2.5 | 2,789 | 2,162 | 3.61 | 90 | 864 | 789 | 1,129 | -399 | -439 | 2,811 | 1,559 | 2,128 | 565 | 616 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_hl_mv20_F60 | NY-AM | 208 | 2.8 | 2,786 | 2,167 | 3.60 | 97 | 1,169 | 1,179 | 1,129 | -320 | -411 | 2,513 | 2,058 | 2,145 | 841 | 920 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_hl_mv20_F45 | W2_0945-1000 | 188 | 2.5 | 2,135 | 1,666 | 3.59 | 90 | 1,634 | 1,606 | 1,732 | -538 | -223 | 1,932 | 1,620 | 1,457 | 1,034 | 1,385 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c2_X30_120 | W2_0945-1000 | 290 | 3.9 | 2,436 | 1,908 | 3.58 | 118 | 1,150 | 306 | 5,051 | 202 | 484 | 2,940 | 592 | 2,255 | 963 | 691 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| PB_ORX_T_SCALE | NY-AM | 119 | 1.6 | 3,107 | 2,466 | 3.53 | 58 | 573 | 655 | 258 | -288 | -344 | 3,528 | 1,167 | 3,033 | 326 | 324 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c2_X30_120 | NY-AM | 304 | 4.1 | 2,388 | 1,895 | 3.53 | 126 | 1,293 | 605 | 4,546 | 294 | 419 | 2,925 | 768 | 2,208 | 1,107 | 829 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_hl_rm0.5_F60 | W2_0945-1000 | 171 | 2.3 | 2,721 | 2,194 | 3.47 | 77 | 707 | 130 | 2,599 | -736 | -687 | 2,755 | 1,072 | 2,049 | 453 | 459 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| DR10m_pb1_rm0.5__c3_X40_90 | W1_0930-0945 | 201 | 2.7 | 2,480 | 2,010 | 3.46 | 90 | 4,024 | 2,866 | 8,354 | -626 | -584 | 3,147 | 1,780 | 2,041 | 3,519 | 3,776 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| OR15m_stp_le1.5_F60 | NY-AM | 289 | 3.9 | 2,090 | 1,696 | 3.45 | 123 | 589 | 18 | 3,534 | -1,190 | -1,362 | 1,961 | 1,028 | 1,704 | 36 | 341 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| DR15m_hl_mv15_F60 | NY-AM | 235 | 3.1 | 2,509 | 2,037 | 3.45 | 100 | 771 | 681 | 1,129 | -198 | -463 | 2,246 | 1,852 | 1,900 | 448 | 522 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c1_X15_120 | W2_0945-1000 | 290 | 3.9 | 1,992 | 1,637 | 3.41 | 118 | 1,257 | 527 | 4,630 | 51 | 26 | 2,363 | 822 | 1,917 | 942 | 1,009 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| OR10m_stp_ge1_F45 | NY-AM | 187 | 2.5 | 2,002 | 1,653 | 3.39 | 84 | 356 | 331 | 457 | 1,220 | 905 | 2,589 | 632 | 1,620 | -194 | 108 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| DR15m_hl_mv15_F60 | W2_0945-1000 | 212 | 2.8 | 2,465 | 2,045 | 3.37 | 93 | 446 | 259 | 1,129 | -362 | -505 | 2,384 | 1,365 | 1,836 | 151 | 198 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c2_X20_90 | W2_0945-1000 | 290 | 3.9 | 1,675 | 1,391 | 3.37 | 118 | 1,508 | 675 | 5,352 | -698 | -779 | 1,856 | 908 | 1,269 | 1,321 | 1,259 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c3_X40_90 | W2_0945-1000 | 290 | 3.9 | 2,243 | 1,878 | 3.35 | 118 | 1,035 | 327 | 4,306 | 508 | 601 | 2,105 | 1,277 | 2,210 | 827 | 787 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_hl_mv20_F45 | NY-AM | 208 | 2.8 | 2,009 | 1,682 | 3.34 | 97 | 1,976 | 2,039 | 1,732 | -579 | -384 | 1,705 | 1,946 | 1,353 | 1,363 | 1,727 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_hl_mv10_F60 | NY-AM | 261 | 3.5 | 2,256 | 1,892 | 3.34 | 105 | 387 | 212 | 1,129 | -482 | -751 | 1,991 | 1,539 | 1,676 | 64 | 138 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| DR15m_hl_mv10__c3_X60_60 | NY-AM | 261 | 3.5 | 2,256 | 1,892 | 3.34 | 105 | 387 | 212 | 1,129 | -482 | -751 | 1,991 | 1,539 | 1,676 | 64 | 138 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| OR5m_stp_ge1_SCALE | NY-AM | 188 | 2.5 | 2,124 | 1,785 | 3.33 | 83 | 1,756 | 1,159 | 4,256 | -586 | -575 | 1,940 | 1,528 | 1,892 | 1,442 | 1,508 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_hl_mv10__c5_AT0.5 | NY-AM | 261 | 3.5 | 4,207 | 3,543 | 3.33 | 105 | 1,414 | 511 | 5,250 | -242 | -68 | 3,898 | 2,297 | 4,296 | 1,076 | 1,165 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_hl_rm0.5_F60 | NY-AM | 189 | 2.5 | 2,628 | 2,219 | 3.32 | 82 | 1,100 | 678 | 2,599 | -630 | -640 | 2,375 | 1,666 | 1,978 | 815 | 851 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |

(full list: out/sb1/tiers.parquet filtered tier != DEAD-IN-HOLD.)

## 6. Failed-gate breakdown of the 541 PRE-selected windows that died in HOLD
| failed                                                        |   count |
|:--------------------------------------------------------------|--------:|
| HOLD 2026 stub<=0 or none                                     |     257 |
| HOLD 2025H2<=0 or none                                        |     135 |
| HOLD mean<=0;HOLD 2025H2<=0 or none                           |      60 |
| HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none |      58 |
| HOLD mean<=0;HOLD 2026 stub<=0 or none                        |      31 |

## 7. MEASURED basis (analytic) and stress
MEASURED pts = mapped (M) pts - 0.25 (entry +1 tick) - slip(lots) on every stop-type exit; slip(1 lot) 0.85, 5 lots 1.18, 10 lots 1.44 pt from DS3_DN_STOPFILL (linear in lots), lots = $1,000 risk / (stop x $20) clipped 1..10; M carries the P9 target/time correction and no stop credit. Stress label = tape-direct (T) rows (entry +1 s, stop +1 tick, strict trade-through targets). 115 alive windows fail MEASURED (PRE or a HOLD gate <= 0). Stress: 938 of 938 alive windows are positive in PRE and HOLD on the T basis (for T-scored cells T is the scored basis, so this is trivially the same number). Cost 2x (engine cm=2 formula): 931 of 938 alive windows positive in PRE and HOLD. These are analytic; the replay of out/sb1/survivors_for_A.parquet supersedes them (note the A_D6 lesson: stored/mapped overstates short-stop cells; here nearly all alive cells have stops >= 30 pt so the MEASURED haircut is small: median pts haircut vs stored shown by pre_meas vs mean in tiers.parquet).

## 8. Data integrity: reproduction of the generating rules, the PM family, the rows-json mismatch
- The harness stores t_in (entry second) and dur_s for every trade; the entry clock for the 11,677 NQ cells with trades is that stored value (no price re-simulation), cross-checked by a **true re-run of the generating rules** (event builders -> o2_score.simulate) for a sample of 1100 cells across all sub-families (out/sb1/regen_*.csv): exact (t_in, dur, pnl) for every family except PM; reproduction rate 100% outside PM, 67 of 144 inside PM.
- Stored post-lock trades vs regenerated pre-lock $: 95.9% of 10.5M post-lock trades identical (the rest are lock-truncated); on days where no lock touched a trade the daily series matches the stored day-level numbers on 99.99% of days, and 97.7% of cells match on every such day.
- SECONDOPENS (264 cells, bar basis): regenerated with b7_run's own code plus exit minute; weekly mean reproduces the rows json 264/264.
- **PM-family T-basis discrepancy resolved:** the stored PM pickles pre-date the roll-day offset fix; I regenerated all 17 PM signals x 12 brackets x M/T with the final harness (sb1_pm.py) and scored the regenerated values. The differing trades are a few percent of trades on the T basis (single trades up to 248 pts different on roll days).
- **The 1.7% rows-json vs pickle d_mean mismatch was an artefact of my check**: PM rows only carry the M-basis d_mean (d_mean_vs_live_M) and I compared it with both bases. For every other family (11,488 cells) the stored d_mean equals the rows-json d_mean to < $1 on 100% of cells.
- Duplicate pickles (489 cells in ORbase/ORbase_v2 etc.): resolved by matching the stored d_mean to the rows json; 195 are exact ties (identical numbers).
- pnl_2x = engine cm=2 formula (commission, size surcharge, mapped correction doubled and 1.0 pt slippage); it was not cross-checked against the stored x2 series (disclosed).

## 9. Limits
- $ are per trade at the stored 10 lots, not at $1,000-risk lots; ranks and signs are what matter. Entry-clock precision: the entry second; exits at the second of the exit sample.
- Sub-windows nest in NY-AM, so W1/W2 and NY-AM alive counts are not additive. Sub-window selection is a separate test family (F_sub).
- Only cells with fixed stop/target brackets (F30/45/60, X*_*; 381 of 938 alive cell-windows) can be replayed through ssa_direct (columns st, tt); the other brackets (trail, chandelier, scale-out, time exits, VWAP/ON targets, ORX/OH/AT variable stops) are flagged replayable=False in survivors_for_A.parquet and need a bracket-aware replay.
- The session sign-flip placebo cannot see bracket beta; see Headline.
- HOLD year segments: 2025H2 (~26 wk) and 2026 stub (~5.5 wk): weak test.

## 10. Files
out/sb1/trades_b2.parquet (cell, entry_et, exit_et, side, lots, pnl_1x, pnl_2x, basis, label_day, reason, instrument; 8.6M rows, 11,941 cells); cell_index2.parquet; pre_session_stats.parquet; tiers.parquet; prehold_selected.parquet; survivors_for_A.parquet (cell, session, uid, t_ent UTC ns, side, st/tt ticks, t_fl, lc, lots100, ym, replayable, bracket, tier, rows_path; 452,609 rows); regen_*.csv.
