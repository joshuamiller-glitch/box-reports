# DS3_CUTWAIT - cut at -X, entry blackout of N minutes, fresh signal re-enters (T-CUT-WAIT, 2026-10-29)
Research only; no live/execution change; UNTOUCHED (> 2026-02-06) never read (windows capped at 20260206; audit logged in DECISIONS.md). Prereg l2vast/ds3/prereg/CUTWAIT_prereg.md sha256 3ede3b6aefe48d53c93c3b25d540beec153ad575294f6e35881c469c9a291372 (cells.csv sha 5429c12c..., logged in DECISIONS.md before scoring). Code l2vast/ds3/code/cutwait/ (cw_lib, cw_sig, cw_cells, cw_run, cw_ana, cw_report), results l2vast/ds3/out/cutwait/. Fees $4.84/contract RT identical in both arms. MEASURED fills (cut = market exit at the close of the first second with unrealised <= -X, minus 1 tick; stop walk by year; P9 target correction), exact per-book lock engine (sl_lib.run_book: day -2R/+5R, give-back arm, week floor), SEQUENCE evaluation with re-entries, paired against the same book with its 60-pt (WT 45) stop and no cut. Cut-without-wait is THLB (dead) and is not altered; the HM retest a30_w10 is untouched.

## Verdict (V2 rules, one line per book)
* **HM** (live/D6): cells DEAD (0 PASS / 0 CAND / 60 DEAD of 60); best-PRE cell x30 N10 any PRE +3,250 / HOLD -5,775 / X +4,126 $/wk, failed holdout_sign,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p; RC p 0.65; WF (13wk, with-hold) WF-DEAD; cells ALL>0: 24/60.
* **KB** (live/D6): cells DEAD (0 PASS / 0 CAND / 60 DEAD of 60); best-PRE cell x25 N15 same PRE -4,868 / HOLD -26,228 / X +4,222 $/wk, failed mean_up,holdout_sign,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p; RC p 0.99; WF (13wk, with-hold) WF-DEAD; cells ALL>0: 0/60.
* **SM** (live/D6): cells DEAD (0 PASS / 0 CAND / 60 DEAD of 60); best-PRE cell x25 N60 same PRE -1,966 / HOLD +5,539 / X +2,090 $/wk, failed mean_up,placebo<0.95,CI,cost,year_share,neighbours,RC_p; RC p 0.90; WF (13wk, with-hold) WF-DEAD; cells ALL>0: 17/60.
* **MV** (live/D6): cells DEAD (0 PASS / 0 CAND / 60 DEAD of 60); best-PRE cell x30 N60 any PRE -3,203 / HOLD -3,860 / X +6,644 $/wk, failed mean_up,holdout_sign,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p; RC p 0.97; WF (13wk, with-hold) WF-DEAD; cells ALL>0: 1/60.
* **PE** (live/D6 [TAKEN-SIGNAL basis]): cells DEAD (0 PASS / 0 CAND / 60 DEAD of 60); best-PRE cell x30 N30 same PRE +239 / HOLD -9,970 / X +2,531 $/wk, failed holdout_sign,placebo<0.95,CI,cost,year_share,neighbours,RC_p; RC p 0.81; WF (13wk, with-hold) WF-DEAD; cells ALL>0: 0/60.
* **PB** (live/D6 [TAKEN-SIGNAL basis]): cells DEAD (0 PASS / 0 CAND / 60 DEAD of 60); best-PRE cell x30 N30 any PRE +5,821 / HOLD -4,020 / X -1,433 $/wk, failed holdout_sign,SPAN2,placebo<0.95,CI,cost,year_share,RC_p; RC p 0.26; WF (13wk, with-hold) WF-DEAD; cells ALL>0: 11/60.
* **DN** (live/D6 [TAKEN-SIGNAL basis]): cells DEAD (0 PASS / 0 CAND / 60 DEAD of 60); best-PRE cell x10 N30 any PRE -3,010 / HOLD -5,479 / X -2,282 $/wk, failed mean_up,holdout_sign,SPAN2,placebo<0.95,CI,cost,year_share,neighbours,RC_p; RC p 0.94; WF (13wk, with-hold) WF-DEAD; cells ALL>0: 0/60.
* **CR** (live/D6 [TAKEN-SIGNAL basis]): cells DEAD (0 PASS / 0 CAND / 36 DEAD of 36); best-PRE cell q25 N30 same PRE +1,294 / HOLD +4,226 / X -867 $/wk, failed SPAN2,placebo<0.95,CI,year_share,neighbours,RC_p; RC p 0.36; WF (13wk, with-hold) WF-DEAD; cells ALL>0: 18/36.
* **D6_HM_t75_s90_NYAM** (live/D6 [TAKEN-SIGNAL basis]): cells DEAD (0 PASS / 0 CAND / 84 DEAD of 84); best-PRE cell q50 N60 same PRE -3,456 / HOLD +4,753 / X -4,761 $/wk, failed mean_up,SPAN2,placebo<0.95,CI,cost,year_share,neighbours,RC_p; RC p 0.97; WF (13wk, with-hold) WF-DEAD; cells ALL>0: 0/84.
* **D6_KB_t60_s75_ASIA** (live/D6 [TAKEN-SIGNAL basis]): cells DEAD (0 PASS / 0 CAND / 84 DEAD of 84); best-PRE cell q50 N10 any PRE -6,614 / HOLD -1,330 / X -1,718 $/wk, failed mean_up,holdout_sign,SPAN2,placebo<0.95,CI,cost,year_share,neighbours,RC_p; RC p 1.00; WF (13wk, with-hold) WF-DEAD; cells ALL>0: 0/84.
* **D6_PB7_PB5_ASIA** (live/D6 [TAKEN-SIGNAL basis]): cells DEAD (0 PASS / 0 CAND / 60 DEAD of 60); best-PRE cell x30 N5 any PRE -3,986 / HOLD +919 / X +458 $/wk, failed mean_up,placebo<0.95,CI,cost,year_share,neighbours,RC_p; RC p 0.98; WF (13wk, with-hold) WF-DEAD; cells ALL>0: 0/60.
* **D6_SM_t60_sst_ASIA** (live/D6 [TAKEN-SIGNAL basis]): cells DEAD (0 PASS / 0 CAND / 36 DEAD of 36); best-PRE cell x15 N10 any PRE +741 / HOLD +141 / X +364 $/wk, failed placebo<0.95,CI,cost,year_share,neighbours,RC_p; RC p 0.40; WF (13wk, with-hold) WF-DEAD; cells ALL>0: 16/36.
* **D6_TB4B_ASIA** (live/D6 [TAKEN-SIGNAL basis]): cells DEAD (0 PASS / 0 CAND / 60 DEAD of 60); best-PRE cell x25 N30 any PRE -2,339 / HOLD +3,697 / X +2,336 $/wk, failed mean_up,placebo<0.95,CI,cost,year_share,neighbours,RC_p; RC p 0.93; WF (13wk, with-hold) WF-DEAD; cells ALL>0: 19/60.
* **D6_TB4W_03_ASIA** (live/D6 [TAKEN-SIGNAL basis]): cells DEAD (0 PASS / 0 CAND / 60 DEAD of 60); best-PRE cell x30 N60 same PRE -2,613 / HOLD -2,849 / X +317 $/wk, failed mean_up,holdout_sign,placebo<0.95,CI,cost,year_share,neighbours,RC_p; RC p 0.91; WF (13wk, with-hold) WF-DEAD; cells ALL>0: 0/60.
* **ST** (research non-D6): cells DEAD (0 PASS / 0 CAND / 60 DEAD of 60); best-PRE cell x15 N10 same PRE -538 / HOLD -8,011 / X -4,415 $/wk, failed mean_up,holdout_sign,SPAN2,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p; RC p 0.94; WF (13wk, with-hold) WF-DEAD; cells ALL>0: 0/60.
* **WT** (research non-D6): cells DEAD (0 PASS / 0 CAND / 84 DEAD of 84); best-PRE cell x30 N30 same PRE -792 / HOLD -1,094 / X -4,754 $/wk, failed mean_up,holdout_sign,SPAN2,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p; RC p 0.95; WF (13wk, with-hold) WF-DEAD; cells ALL>0: 0/84.
* **MA** (research non-D6): cells DEAD (0 PASS / 0 CAND / 60 DEAD of 60); best-PRE cell x30 N5 same PRE -1,018 / HOLD +2,977 / X +70 $/wk, failed mean_up,placebo<0.95,CI,cost,year_share,neighbours,RC_p; RC p 0.89; WF (13wk, with-hold) WF-DEAD; cells ALL>0: 14/60.

## Plain sentence
Across 1044 arming family cells in 17 books, 0 cells beat the stop (ALL-seen paired CI above 0), 718 tie it (CI spans 0) and 326 lose to it (CI below 0); 0 cells reach CANDIDATE or PASS. The wait increment over the same-X no-wait reference is positive in 478 of 1044 cells (median +0 $/wk). No X/N beats the stop; the best ones at most tie it.

## Per book detail

### HM (live/D6; lots 10, stop 60, TF 1m; signals 14529, baseline rows 3835, kept by locks 2750; baseline rows PRE/HOLD/X 1478/609/663)
| cell | PRE $/wk [CI] (MDE) | HOLD | X | PRE pts/tr | HOLD pts/tr | P1 rank PRE/HOLD | wait inc PRE/HOLD ($/wk) | tier | failed |
|---|---|---|---|---|---|---|---|---|---|
| x30 N10 any | +3,250 [-5,911,+12,339] (MDE 12,986) | -5,775 [-21,298,+9,600] (MDE 22,725) | +4,126 [-5,982,+14,390] (MDE 14,498) | +0.82 | -1.52 | 0.75/0.00 | +3,748/-1,715 | DEAD | holdout_sign,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p |
| x30 N5 any | +2,997 [-5,986,+11,554] (MDE 12,573) | -5,569 [-21,077,+10,119] (MDE 22,705) | +4,026 [-5,607,+13,819] (MDE 13,933) | +0.76 | -1.46 | 0.65/0.00 | +3,495/-1,509 | DEAD | holdout_sign,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p |
| x30 N60 same | +2,456 [-7,084,+11,989] (MDE 13,835) | +3,244 [-14,332,+19,988] (MDE 25,399) | +821 [-10,618,+12,322] (MDE 16,356) | +0.62 | +0.85 | 0.90/0.05 | +1,523/+3,295 | DEAD | placebo<0.95,CI,maxDD,RC_p |
| x25 Nbar same (best ALL) | +1,759 [-8,718,+11,936] (MDE 15,077) | +4,337 [-13,744,+22,034] (MDE 26,129) | +2,472 [-7,642,+12,273] (MDE 14,517) | +0.45 | +1.14 | 0.80/0.20 | +0/+0 | DEAD | placebo<0.95,CI,cost,neighbours,RC_p |

Same X, N=0 reference (any): PRE -498 [-8,934,+8,151] (MDE 12,359), HOLD -4,060 [-19,383,+11,683] (MDE 22,822), X +3,988 [-6,234,+14,434] (MDE 14,841).
Best-PRE cell decomposition (pre-lock pts, net of fee), PRE|HOLD|X: cuts 1353|586|567; common-trade delta -1,214|+592|+623; lost baseline trades 748:-2,110|332:-148|250:+105; added re-entries 685:+467|307:-866|314:+185; signals skipped during the wait/direction rule (standalone bracket P&L) 1851:-3,495|875:-4,975|859:+3,418.
By entry session (delta $, all seen): 0:-13,833, 1:+99,074, 2:+169,236, 3:+319,044, 4:-332,942, 5:-100 (0 ASIA,1 LONDON,2 PRE,3 NY-AM,4 NY-PM,5 CLOSE); by year: 2023:+73,782, 2024:+411,107, 2025:-318,295, 2026:+73,885.
Walk-forward ($/wk vs stop): w13_True: WF-PRE -3,529 [-12,672,+5,649] rank 0.42, WF-HOLD -71 [-4,701,+4,373] rank 0.65, WF-DEAD; w13_False: WF-PRE -3,529 [-12,775,+5,449] rank 0.42, WF-HOLD +3,888 [-14,748,+22,459] rank 0.90, WF-DEAD; exp_True: WF-PRE -1,228 [-10,606,+8,239] rank 0.81, WF-HOLD -5,473 [-23,097,+12,070] rank 0.28, WF-DEAD; exp_False: WF-PRE -1,228 [-10,420,+8,372] rank 0.81, WF-HOLD -5,473 [-22,416,+11,826] rank 0.28, WF-DEAD

### KB (live/D6; lots 10, stop 60, TF 3m; signals 30126, baseline rows 5034, kept by locks 3150; baseline rows PRE/HOLD/X 1653/712/785)
| cell | PRE $/wk [CI] (MDE) | HOLD | X | PRE pts/tr | HOLD pts/tr | P1 rank PRE/HOLD | wait inc PRE/HOLD ($/wk) | tier | failed |
|---|---|---|---|---|---|---|---|---|---|
| x25 N15 same | -4,868 [-16,293,+6,668] (MDE 16,648) | -26,228 [-45,559,-6,381] (MDE 28,081) | +4,222 [-7,341,+15,339] (MDE 16,140) | -1.10 | -5.89 | 0.65/0.30 | +1,719/-4,485 | DEAD | mean_up,holdout_sign,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p |
| x25 N5 same | -5,791 [-16,787,+5,924] (MDE 16,458) | -20,511 [-38,600,-1,605] (MDE 27,424) | +3,272 [-8,218,+14,457] (MDE 16,400) | -1.31 | -4.61 | 0.65/0.50 | +795/+1,233 | DEAD | mean_up,holdout_sign,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p |
| x25 N10 same | -6,449 [-17,939,+5,098] (MDE 16,496) | -21,856 [-40,472,-2,887] (MDE 26,762) | +3,258 [-7,930,+14,635] (MDE 16,113) | -1.46 | -4.91 | 0.45/0.25 | +138/-112 | DEAD | mean_up,holdout_sign,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p |
| x30 N15 same | -6,548 [-18,049,+4,202] (MDE 16,160) | -26,935 [-43,670,-9,264] (MDE 25,201) | +6,142 [-5,381,+17,074] (MDE 16,198) | -1.49 | -6.05 | 0.75/0.10 | +1,760/-4,781 | DEAD | mean_up,holdout_sign,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p |
| x30 N60 same (best ALL) | -7,491 [-18,863,+4,115] (MDE 16,588) | -18,401 [-35,713,-368] (MDE 25,609) | +5,349 [-5,640,+16,171] (MDE 15,694) | -1.70 | -4.14 | 0.90/0.15 | +817/+3,753 | DEAD | mean_up,holdout_sign,placebo<0.95,CI,cost,year_share,neighbours,RC_p |

Same X, N=0 reference (same): PRE -6,587 [-17,991,+4,610] (MDE 16,527), HOLD -21,744 [-39,485,-2,926] (MDE 27,293), X +3,098 [-9,097,+14,318] (MDE 16,820).
Best-PRE cell decomposition (pre-lock pts, net of fee), PRE|HOLD|X: cuts 1425|641|584; common-trade delta -2,118|-1,976|+1,614; lost baseline trades 1338:-665|600:+118|399:-60; added re-entries 818:+26|392:+647|377:+143; signals skipped during the wait/direction rule (standalone bracket P&L) 4226:-6,894|2047:-3,869|1812:-4,472.
By entry session (delta $, all seen): 0:-176,790, 1:-409,515, 2:-42,318, 3:-174,360, 4:-215,941, 5:+252 (0 ASIA,1 LONDON,2 PRE,3 NY-AM,4 NY-PM,5 CLOSE); by year: 2023:+229,245, 2024:-310,992, 2025:-939,229, 2026:+2,303.
Walk-forward ($/wk vs stop): w13_True: WF-PRE -8,824 [-18,548,+616] rank 0.94, WF-HOLD -21,688 [-38,452,-5,849] rank 0.70, WF-DEAD; w13_False: WF-PRE -7,439 [-17,884,+2,651] rank 0.99, WF-HOLD -29,530 [-46,829,-12,724] rank 0.17, WF-DEAD; exp_True: WF-PRE -12,552 [-23,450,-2,112] rank 0.75, WF-HOLD +0 [+0,+0] rank 1.00, WF-DEAD; exp_False: WF-PRE -14,345 [-25,511,-2,979] rank 0.57, WF-HOLD -33,631 [-50,583,-15,973] rank 0.05, WF-DEAD

### SM (live/D6; lots 10, stop 60, TF 10m; signals 2126, baseline rows 1504, kept by locks 1412; baseline rows PRE/HOLD/X 749/280/383)
| cell | PRE $/wk [CI] (MDE) | HOLD | X | PRE pts/tr | HOLD pts/tr | P1 rank PRE/HOLD | wait inc PRE/HOLD ($/wk) | tier | failed |
|---|---|---|---|---|---|---|---|---|---|
| x25 N60 same | -1,966 [-8,895,+4,733] (MDE 9,797) | +5,539 [-2,700,+13,959] (MDE 11,632) | +2,090 [-4,418,+8,502] (MDE 9,553) | -0.98 | +3.16 | 0.95/0.55 | +250/-539 | DEAD | mean_up,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x25 N30 same | -2,077 [-8,885,+4,858] (MDE 9,882) | +6,078 [-1,918,+13,992] (MDE 11,675) | +2,797 [-3,658,+9,005] (MDE 9,324) | -1.04 | +3.47 | 0.95/0.55 | +139/+0 | DEAD | mean_up,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x25 N10 same | -2,146 [-8,922,+4,816] (MDE 9,894) | +6,078 [-1,845,+14,055] (MDE 11,675) | +2,565 [-4,135,+8,894] (MDE 9,493) | -1.07 | +3.47 | 0.95/0.55 | +70/+0 | DEAD | mean_up,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x25 N15 same | -2,146 [-9,461,+4,715] (MDE 9,894) | +6,078 [-1,979,+14,044] (MDE 11,675) | +2,680 [-3,943,+9,111] (MDE 9,347) | -1.07 | +3.47 | 0.95/0.55 | +70/+0 | DEAD | mean_up,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x30 N60 same (best ALL) | -2,891 [-9,216,+3,501] (MDE 9,245) | +6,595 [-452,+13,283] (MDE 10,145) | +3,956 [-2,064,+10,118] (MDE 8,619) | -1.45 | +3.77 | 0.80/0.65 | +446/-508 | DEAD | mean_up,placebo<0.95,CI,cost,year_share,neighbours,RC_p |

Same X, N=0 reference (same): PRE -2,216 [-9,116,+4,413] (MDE 9,885), HOLD +6,078 [-1,905,+13,682] (MDE 11,675), X +2,565 [-4,331,+8,934] (MDE 9,493).
Best-PRE cell decomposition (pre-lock pts, net of fee), PRE|HOLD|X: cuts 429|158|231; common-trade delta -1,259|+377|+954; lost baseline trades 161:-324|57:-410|47:-58; added re-entries 55:+67|18:+48|38:-85; signals skipped during the wait/direction rule (standalone bracket P&L) 257:-1,595|93:-431|122:-395.
By entry session (delta $, all seen): 0:-14,581, 1:-106,019, 2:-8,683, 3:+41,918, 4:+209,098 (0 ASIA,1 LONDON,2 PRE,3 NY-AM,4 NY-PM,5 CLOSE); by year: 2023:+105,408, 2024:-40,778, 2025:+37,627, 2026:+19,476.
Walk-forward ($/wk vs stop): w13_True: WF-PRE -7,543 [-13,389,-1,953] rank 0.01, WF-HOLD +3,783 [-2,037,+9,960] rank 0.54, WF-DEAD; w13_False: WF-PRE -5,034 [-12,086,+1,893] rank 0.41, WF-HOLD +5,859 [-1,806,+13,583] rank 0.81, WF-DEAD; exp_True: WF-PRE -2,589 [-8,903,+3,282] rank 0.97, WF-HOLD +4,347 [-1,091,+9,783] rank 0.58, WF-DEAD; exp_False: WF-PRE -2,891 [-9,174,+3,749] rank 0.94, WF-HOLD +5,537 [-2,192,+12,968] rank 0.78, WF-DEAD

### MV (live/D6; lots 10, stop 60, TF 1m; signals 38294, baseline rows 5181, kept by locks 3094; baseline rows PRE/HOLD/X 1692/650/752)
| cell | PRE $/wk [CI] (MDE) | HOLD | X | PRE pts/tr | HOLD pts/tr | P1 rank PRE/HOLD | wait inc PRE/HOLD ($/wk) | tier | failed |
|---|---|---|---|---|---|---|---|---|---|
| x30 N60 any | -3,203 [-13,498,+7,140] (MDE 15,183) | -3,860 [-17,569,+10,011] (MDE 19,781) | +6,644 [-4,600,+18,075] (MDE 16,159) | -0.71 | -0.95 | 0.90/0.65 | +4,441/+1,370 | DEAD | mean_up,holdout_sign,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p |
| x25 Nbar any | -3,365 [-14,568,+7,702] (MDE 16,327) | -1,958 [-20,486,+16,118] (MDE 26,612) | +2,946 [-7,684,+14,349] (MDE 15,487) | -0.75 | -0.48 | 0.45/0.85 | +0/+0 | DEAD | mean_up,holdout_sign,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p |
| x25 N10 any | -4,180 [-15,499,+7,153] (MDE 16,110) | -5,075 [-20,892,+11,246] (MDE 23,265) | +2,968 [-7,195,+13,394] (MDE 14,941) | -0.93 | -1.25 | 0.30/0.15 | -814/-3,116 | DEAD | mean_up,holdout_sign,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p |
| x30 N10 any | -4,228 [-14,592,+6,205] (MDE 14,886) | -2,371 [-16,555,+12,687] (MDE 21,379) | +3,663 [-6,780,+14,123] (MDE 15,493) | -0.94 | -0.58 | 0.05/0.40 | +3,417/+2,859 | DEAD | mean_up,holdout_sign,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p |
| x30 N30 any (best ALL) | -4,630 [-15,050,+6,250] (MDE 15,178) | +391 [-14,561,+14,948] (MDE 21,594) | +8,953 [-3,075,+20,746] (MDE 16,958) | -1.03 | +0.10 | 0.35/0.10 | +3,014/+5,621 | DEAD | mean_up,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p |

Same X, N=0 reference (any): PRE -7,645 [-18,523,+3,353] (MDE 15,870), HOLD -5,230 [-20,090,+10,246] (MDE 22,086), X +3,265 [-7,270,+13,498] (MDE 15,346).
Best-PRE cell decomposition (pre-lock pts, net of fee), PRE|HOLD|X: cuts 2114|911|784; common-trade delta -2,437|-90|+2,491; lost baseline trades 755:+1,381|323:-495|253:-828; added re-entries 1158:+696|507:-116|509:+590; signals skipped during the wait/direction rule (standalone bracket P&L) 2315:-3,216|1130:-3,883|861:-523.
By entry session (delta $, all seen): 0:+126,063, 1:+128,759, 2:+117,038, 3:-552,167, 4:+108,845 (0 ASIA,1 LONDON,2 PRE,3 NY-AM,4 NY-PM,5 CLOSE); by year: 2023:+244,091, 2024:-26,807, 2025:-431,054, 2026:+142,309.
Walk-forward ($/wk vs stop): w13_True: WF-PRE -13,573 [-24,854,-2,708] rank 0.02, WF-HOLD -4,531 [-20,962,+11,752] rank 0.71, WF-DEAD; w13_False: WF-PRE -14,935 [-26,932,-2,662] rank 0.00, WF-HOLD -4,531 [-20,300,+11,130] rank 0.71, WF-DEAD; exp_True: WF-PRE -13,250 [-23,554,-3,224] rank 0.04, WF-HOLD -3,746 [-16,819,+9,973] rank 0.76, WF-DEAD; exp_False: WF-PRE -12,436 [-23,385,-2,187] rank 0.10, WF-HOLD -4,096 [-17,505,+9,433] rank 0.73, WF-DEAD

### PE (live/D6 [TAKEN-SIGNAL basis]; lots 10, stop 60, TF 5m; signals 5361, baseline rows 5361, kept by locks 3153; baseline rows PRE/HOLD/X 1637/727/789)
| cell | PRE $/wk [CI] (MDE) | HOLD | X | PRE pts/tr | HOLD pts/tr | P1 rank PRE/HOLD | wait inc PRE/HOLD ($/wk) | tier | failed |
|---|---|---|---|---|---|---|---|---|---|
| x30 N30 same | +239 [-9,822,+10,147] (MDE 14,371) | -9,970 [-23,467,+4,048] (MDE 20,255) | +2,531 [-8,876,+12,868] (MDE 15,494) | +0.05 | -2.19 | 0.85/0.40 | +207/-297 | DEAD | holdout_sign,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x30 N5 same | -32 [-9,492,+10,018] (MDE 14,438) | -9,093 [-22,775,+4,231] (MDE 20,163) | +2,925 [-8,185,+13,165] (MDE 15,668) | -0.01 | -2.00 | 0.85/0.45 | -64/+580 | DEAD | mean_up,holdout_sign,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x30 N60 same | -57 [-10,937,+10,166] (MDE 15,000) | -11,155 [-24,380,+2,284] (MDE 19,829) | +2,387 [-8,468,+13,010] (MDE 15,312) | -0.01 | -2.46 | 0.60/0.45 | -89/-1,483 | DEAD | mean_up,holdout_sign,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p |
| x30 Nbar same | -114 [-10,143,+9,986] (MDE 14,426) | -9,283 [-22,587,+4,940] (MDE 20,145) | +2,925 [-8,086,+13,682] (MDE 15,668) | -0.03 | -2.04 | 0.85/0.45 | -147/+389 | DEAD | mean_up,holdout_sign,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x30 N10 any (best ALL) | -2,838 [-12,526,+7,049] (MDE 14,325) | -7,517 [-19,739,+4,890] (MDE 17,579) | +8,823 [-1,760,+19,126] (MDE 15,305) | -0.65 | -1.65 | 0.90/0.10 | +697/+624 | DEAD | mean_up,holdout_sign,placebo<0.95,CI,cost,year_share,neighbours,RC_p |

Same X, N=0 reference (same): PRE +32 [-10,332,+10,444] (MDE 14,557), HOLD -9,672 [-23,716,+3,926] (MDE 20,342), X +2,925 [-8,935,+13,151] (MDE 15,668).
Best-PRE cell decomposition (pre-lock pts, net of fee), PRE|HOLD|X: cuts 1910|830|610; common-trade delta +1,483|-460|-5; lost baseline trades 57:-3|26:-432|8:+111; added re-entries 0:+0|0:+0|0:+0; signals skipped during the wait/direction rule (standalone bracket P&L) 57:-3|26:-432|8:+111.
By entry session (delta $, all seen): 0:-2,168, 1:+59,809, 2:-40,417, 3:-132,136, 4:-88,877, 5:+14,095 (0 ASIA,1 LONDON,2 PRE,3 NY-AM,4 NY-PM,5 CLOSE); by year: 2023:-24,974, 2024:+540,003, 2025:-699,417, 2026:-5,306.
Walk-forward ($/wk vs stop): w13_True: WF-PRE +951 [-6,907,+8,788] rank 1.00, WF-HOLD -390 [-1,171,+0] rank 0.99, WF-DEAD; w13_False: WF-PRE -5,467 [-15,875,+4,705] rank 0.66, WF-HOLD -13,533 [-28,223,+1,867] rank 0.03, WF-DEAD; exp_True: WF-PRE -4,447 [-15,606,+6,066] rank 0.79, WF-HOLD -9,318 [-22,140,+3,101] rank 0.36, WF-DEAD; exp_False: WF-PRE -4,447 [-15,718,+6,151] rank 0.79, WF-HOLD -10,719 [-23,564,+1,452] rank 0.19, WF-DEAD

### PB (live/D6 [TAKEN-SIGNAL basis]; lots 10, stop 60, TF 10m; signals 4049, baseline rows 4049, kept by locks 2879; baseline rows PRE/HOLD/X 1489/693/697)
| cell | PRE $/wk [CI] (MDE) | HOLD | X | PRE pts/tr | HOLD pts/tr | P1 rank PRE/HOLD | wait inc PRE/HOLD ($/wk) | tier | failed |
|---|---|---|---|---|---|---|---|---|---|
| x30 N30 any | +5,821 [-2,365,+14,139] (MDE 12,027) | -4,020 [-17,368,+9,549] (MDE 19,560) | -1,433 [-9,545,+6,269] (MDE 11,784) | +1.47 | -0.93 | 0.85/0.85 | +1,798/+981 | DEAD | holdout_sign,SPAN2,placebo<0.95,CI,cost,year_share,RC_p |
| x30 N10 any | +4,529 [-4,271,+12,616] (MDE 12,158) | -5,001 [-17,959,+7,698] (MDE 18,918) | -1,911 [-9,751,+6,094] (MDE 11,388) | +1.14 | -1.15 | 0.60/0.85 | +506/+0 | DEAD | holdout_sign,SPAN2,placebo<0.95,CI,cost,year_share,RC_p |
| x30 N60 any | +4,523 [-3,679,+12,545] (MDE 11,739) | -6,317 [-20,088,+7,225] (MDE 19,700) | -1,954 [-10,230,+6,309] (MDE 11,992) | +1.14 | -1.46 | 0.45/0.85 | +500/-1,316 | DEAD | holdout_sign,SPAN2,placebo<0.95,CI,cost,year_share,RC_p |
| x30 N5 any | +4,507 [-4,068,+13,024] (MDE 12,164) | -5,001 [-17,778,+8,146] (MDE 18,918) | -1,911 [-9,466,+6,034] (MDE 11,388) | +1.14 | -1.15 | 0.60/0.85 | +484/+0 | DEAD | holdout_sign,SPAN2,placebo<0.95,CI,cost,year_share,RC_p |

Same X, N=0 reference (any): PRE +4,023 [-4,402,+12,681] (MDE 12,292), HOLD -5,001 [-18,069,+7,801] (MDE 18,918), X -1,911 [-9,674,+6,027] (MDE 11,388).
Best-PRE cell decomposition (pre-lock pts, net of fee), PRE|HOLD|X: cuts 1437|586|511; common-trade delta +2,418|-1,434|-735; lost baseline trades 8:+100|0:+0|0:+0; added re-entries 0:+0|0:+0|0:+0; signals skipped during the wait/direction rule (standalone bracket P&L) 8:+100|0:+0|0:+0.
By entry session (delta $, all seen): 0:+58,803, 1:-66,007, 2:+57,343, 3:+249,208, 4:-66,886, 5:+12,408 (0 ASIA,1 LONDON,2 PRE,3 NY-AM,4 NY-PM,5 CLOSE); by year: 2023:-149,347, 2024:+728,697, 2025:-351,261, 2026:+16,779.
Walk-forward ($/wk vs stop): w13_True: WF-PRE +5,121 [-1,681,+12,202] rank 0.98, WF-HOLD -3,562 [-19,125,+10,814] rank 0.64, WF-DEAD; w13_False: WF-PRE +4,101 [-4,663,+12,799] rank 0.93, WF-HOLD -2,270 [-17,903,+13,199] rank 0.72, WF-DEAD; exp_True: WF-PRE -1,173 [-9,439,+6,801] rank 0.37, WF-HOLD -4,020 [-17,577,+9,024] rank 0.55, WF-DEAD; exp_False: WF-PRE +1,821 [-7,287,+10,785] rank 0.74, WF-HOLD -4,020 [-17,109,+9,862] rank 0.55, WF-DEAD

### DN (live/D6 [TAKEN-SIGNAL basis]; lots 10, stop 60, TF 15m; signals 3272, baseline rows 3272, kept by locks 2529; baseline rows PRE/HOLD/X 1333/556/640)
| cell | PRE $/wk [CI] (MDE) | HOLD | X | PRE pts/tr | HOLD pts/tr | P1 rank PRE/HOLD | wait inc PRE/HOLD ($/wk) | tier | failed |
|---|---|---|---|---|---|---|---|---|---|
| x10 N30 any | -3,010 [-11,578,+5,462] (MDE 12,426) | -5,479 [-21,337,+10,131] (MDE 22,874) | -2,282 [-12,554,+7,757] (MDE 14,409) | -0.85 | -1.58 | 0.00/0.25 | +412/+1,671 | DEAD | mean_up,holdout_sign,SPAN2,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x15 N30 any | -3,215 [-11,381,+5,209] (MDE 11,952) | -9,806 [-25,273,+5,514] (MDE 22,562) | -1,786 [-11,024,+7,789] (MDE 13,113) | -0.90 | -2.82 | 0.50/0.65 | +446/+456 | DEAD | mean_up,holdout_sign,SPAN2,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x10 Nbar any | -3,280 [-12,228,+5,634] (MDE 12,731) | -7,501 [-23,390,+7,991] (MDE 22,877) | -2,315 [-12,055,+8,022] (MDE 14,330) | -0.92 | -2.16 | 0.00/0.25 | +141/-350 | DEAD | mean_up,holdout_sign,SPAN2,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x10 N5 any | -3,289 [-12,121,+5,589] (MDE 12,674) | -7,501 [-22,703,+8,578] (MDE 22,877) | -2,315 [-12,235,+7,698] (MDE 14,330) | -0.93 | -2.16 | 0.00/0.25 | +133/-350 | DEAD | mean_up,holdout_sign,SPAN2,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x30 N5 any (best ALL) | -5,374 [-13,886,+3,426] (MDE 12,326) | -950 [-13,787,+11,928] (MDE 19,147) | +190 [-7,133,+7,407] (MDE 10,827) | -1.51 | -0.27 | 0.70/0.40 | -591/-150 | DEAD | mean_up,holdout_sign,placebo<0.95,CI,maxDD,cost(not top10),year_share,neighbours,RC_p |

Same X, N=0 reference (any): PRE -3,421 [-12,218,+4,992] (MDE 12,691), HOLD -7,150 [-23,041,+9,418] (MDE 23,100), X -2,315 [-12,330,+7,321] (MDE 14,330).
Best-PRE cell decomposition (pre-lock pts, net of fee), PRE|HOLD|X: cuts 1078|481|451; common-trade delta -1,570|-916|+590; lost baseline trades 11:+276|1:+56|1:-61; added re-entries 0:+0|0:+0|0:+0; signals skipped during the wait/direction rule (standalone bracket P&L) 11:+276|1:+56|1:-61.
By entry session (delta $, all seen): 0:-402,848, 1:-154,937, 2:-80,701, 3:+6,324, 4:-10,387, 5:+141,101 (0 ASIA,1 LONDON,2 PRE,3 NY-AM,4 NY-PM,5 CLOSE); by year: 2023:-89,154, 2024:-267,728, 2025:+71,478, 2026:-216,044.
Walk-forward ($/wk vs stop): w13_True: WF-PRE -5,500 [-11,863,+1,077] rank 0.57, WF-HOLD -9,166 [-25,350,+7,547] rank 0.10, WF-DEAD; w13_False: WF-PRE -7,077 [-15,940,+1,844] rank 0.28, WF-HOLD -9,527 [-25,412,+7,505] rank 0.07, WF-DEAD; exp_True: WF-PRE -5,265 [-11,834,+1,700] rank 0.63, WF-HOLD +0 [+0,+0] rank 0.97, WF-DEAD; exp_False: WF-PRE -8,674 [-17,012,-309] rank 0.10, WF-HOLD -4,917 [-20,231,+10,021] rank 0.61, WF-DEAD

### CR (live/D6 [TAKEN-SIGNAL basis]; lots 10, stop 11.5, TF 5m; signals 2694, baseline rows 2691, kept by locks 1897; baseline rows PRE/HOLD/X 887/367/643)
| cell | PRE $/wk [CI] (MDE) | HOLD | X | PRE pts/tr | HOLD pts/tr | P1 rank PRE/HOLD | wait inc PRE/HOLD ($/wk) | tier | failed |
|---|---|---|---|---|---|---|---|---|---|
| q25 N30 same | +1,294 [-1,297,+4,011] (MDE 3,829) | +4,226 [+7,+8,543] (MDE 6,258) | -867 [-4,263,+2,461] (MDE 4,932) | +0.55 | +1.84 | 0.30/0.80 | +79/+106 | DEAD | SPAN2,placebo<0.95,CI,year_share,neighbours,RC_p |
| q25 N60 same (best ALL) | +1,275 [-1,306,+3,877] (MDE 3,799) | +4,190 [-158,+8,526] (MDE 6,262) | -736 [-4,170,+2,694] (MDE 4,949) | +0.54 | +1.83 | 0.30/0.80 | +60/+70 | DEAD | SPAN2,placebo<0.95,CI,year_share,neighbours,RC_p |
| q25 N15 same | +1,248 [-1,343,+3,981] (MDE 3,831) | +4,171 [+22,+8,392] (MDE 6,283) | -883 [-4,342,+2,523] (MDE 4,931) | +0.53 | +1.82 | 0.30/0.80 | +33/+51 | DEAD | SPAN2,placebo<0.95,CI,year_share,neighbours,RC_p |
| q25 N10 same | +1,235 [-1,431,+3,929] (MDE 3,831) | +4,120 [-307,+8,240] (MDE 6,283) | -899 [-4,290,+2,516] (MDE 4,937) | +0.52 | +1.80 | 0.25/0.80 | +20/+0 | DEAD | SPAN2,placebo<0.95,CI,year_share,neighbours,RC_p |

Same X, N=0 reference (same): PRE +1,215 [-1,332,+3,838] (MDE 3,832), HOLD +4,120 [-339,+8,409] (MDE 6,283), X -899 [-4,359,+2,522] (MDE 4,937).
Best-PRE cell decomposition (pre-lock pts, net of fee), PRE|HOLD|X: cuts 782|350|450; common-trade delta -209|+1,088|-505; lost baseline trades 435:-1,232|177:-649|223:-608; added re-entries 1:+16|0:+0|0:+0; signals skipped during the wait/direction rule (standalone bracket P&L) 437:-1,259|177:-649|223:-608.
By entry session (delta $, all seen): 0:+109,854, 1:+102,947, 2:-62,474, 3:+71,885, 4:-28,107 (0 ASIA,1 LONDON,2 PRE,3 NY-AM,4 NY-PM,5 CLOSE); by year: 2023:-32,587, 2024:+17,394, 2025:+186,590, 2026:+22,708.
Walk-forward ($/wk vs stop): w13_True: WF-PRE -97 [-2,373,+2,186] rank 0.49, WF-HOLD +1,479 [-1,594,+4,560] rank 0.22, WF-DEAD; w13_False: WF-PRE +17 [-2,412,+2,477] rank 0.55, WF-HOLD +1,479 [-1,650,+4,541] rank 0.22, WF-WEAK; exp_True: WF-PRE -175 [-2,061,+1,680] rank 0.47, WF-HOLD +4,190 [-218,+8,391] rank 0.92, WF-DEAD; exp_False: WF-PRE +1,275 [-1,334,+3,882] rank 0.97, WF-HOLD +4,190 [-198,+8,290] rank 0.92, WF-WEAK

### D6_HM_t75_s90_NYAM (live/D6 [TAKEN-SIGNAL basis]; lots 10, stop 90, TF 1m; signals 780, baseline rows 780, kept by locks 770; baseline rows PRE/HOLD/X 425/189/156)
| cell | PRE $/wk [CI] (MDE) | HOLD | X | PRE pts/tr | HOLD pts/tr | P1 rank PRE/HOLD | wait inc PRE/HOLD ($/wk) | tier | failed |
|---|---|---|---|---|---|---|---|---|---|
| q50 N60 same | -3,456 [-9,580,+2,345] (MDE 8,581) | +4,753 [-3,235,+12,962] (MDE 11,622) | -4,761 [-10,398,+941] (MDE 8,146) | -3.05 | +4.02 | 0.30/0.40 | +820/-288 | DEAD | mean_up,SPAN2,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| q50 N5 same | -4,155 [-10,404,+1,950] (MDE 8,643) | +5,041 [-2,776,+12,854] (MDE 11,519) | -4,761 [-10,378,+844] (MDE 8,146) | -3.67 | +4.27 | 0.20/0.35 | +121/+0 | DEAD | mean_up,SPAN2,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| q50 N10 same | -4,155 [-10,038,+1,765] (MDE 8,643) | +5,349 [-2,367,+13,162] (MDE 11,317) | -4,761 [-10,281,+814] (MDE 8,146) | -3.67 | +4.53 | 0.10/0.45 | +121/+308 | DEAD | mean_up,SPAN2,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| q50 N15 same | -4,227 [-10,268,+1,613] (MDE 8,557) | +5,349 [-2,230,+13,155] (MDE 11,317) | -4,761 [-10,374,+957] (MDE 8,146) | -3.73 | +4.53 | 0.10/0.45 | +50/+308 | DEAD | mean_up,SPAN2,placebo<0.95,CI,cost,year_share,neighbours,RC_p |

Same X, N=0 reference (same): PRE -4,277 [-10,408,+1,422] (MDE 8,599), HOLD +5,041 [-2,827,+13,067] (MDE 11,519), X -4,761 [-10,361,+752] (MDE 8,146).
Best-PRE cell decomposition (pre-lock pts, net of fee), PRE|HOLD|X: cuts 204|83|85; common-trade delta -1,921|+9|-973; lost baseline trades 45:-74|26:-744|7:+75; added re-entries 0:+0|0:+0|0:+0; signals skipped during the wait/direction rule (standalone bracket P&L) 45:-74|26:-744|7:+75.
By entry session (delta $, all seen): 3:-316,636 (0 ASIA,1 LONDON,2 PRE,3 NY-AM,4 NY-PM,5 CLOSE); by year: 2023:-260,691, 2024:-159,056, 2025:+84,334, 2026:+18,777.
Walk-forward ($/wk vs stop): w13_True: WF-PRE -2,687 [-7,919,+2,080] rank 1.00, WF-HOLD +247 [-8,256,+8,343] rank 0.40, WF-DEAD; w13_False: WF-PRE -7,312 [-14,202,-817] rank 0.77, WF-HOLD +1,413 [-7,632,+10,134] rank 0.59, WF-DEAD; exp_True: WF-PRE +0 [+0,+0] rank 1.00, WF-HOLD +0 [+0,+0] rank 0.36, WF-DEAD; exp_False: WF-PRE -6,206 [-12,777,+70] rank 0.95, WF-HOLD +4,753 [-2,929,+12,770] rank 0.96, WF-DEAD

### D6_KB_t60_s75_ASIA (live/D6 [TAKEN-SIGNAL basis]; lots 10, stop 75, TF 1m; signals 1268, baseline rows 1259, kept by locks 1204; baseline rows PRE/HOLD/X 671/291/242)
| cell | PRE $/wk [CI] (MDE) | HOLD | X | PRE pts/tr | HOLD pts/tr | P1 rank PRE/HOLD | wait inc PRE/HOLD ($/wk) | tier | failed |
|---|---|---|---|---|---|---|---|---|---|
| q50 N10 any | -6,614 [-12,480,-895] (MDE 8,360) | -1,330 [-10,727,+8,237] (MDE 13,907) | -1,718 [-8,248,+4,460] (MDE 9,189) | -3.70 | -0.73 | 0.80/0.50 | +269/-460 | DEAD | mean_up,holdout_sign,SPAN2,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| q50 N5 any (best ALL) | -6,667 [-12,581,-986] (MDE 8,333) | -870 [-10,668,+9,556] (MDE 14,344) | -1,718 [-8,020,+4,518] (MDE 9,189) | -3.73 | -0.48 | 0.75/0.50 | +216/+0 | DEAD | mean_up,holdout_sign,SPAN2,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x25 N60 any | -6,727 [-14,003,+103] (MDE 10,280) | -6,101 [-16,563,+4,404] (MDE 15,306) | -225 [-7,642,+7,388] (MDE 10,781) | -3.76 | -3.35 | 0.30/0.50 | +614/+1,390 | DEAD | mean_up,holdout_sign,SPAN2,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p |
| q50 N60 any | -6,804 [-13,056,-671] (MDE 8,669) | -1,679 [-11,740,+8,170] (MDE 14,528) | -1,986 [-8,124,+4,013] (MDE 9,050) | -3.80 | -0.92 | 0.15/0.50 | +79/-810 | DEAD | mean_up,holdout_sign,SPAN2,placebo<0.95,CI,cost,year_share,neighbours,RC_p |

Same X, N=0 reference (any): PRE -6,883 [-12,644,-1,205] (MDE 8,307), HOLD -870 [-11,049,+9,482] (MDE 14,344), X -1,718 [-7,987,+4,621] (MDE 9,189).
Best-PRE cell decomposition (pre-lock pts, net of fee), PRE|HOLD|X: cuts 378|172|150; common-trade delta -3,090|-478|-485; lost baseline trades 49:+170|33:-13|1:+59; added re-entries 2:+18|1:-39|0:+0; signals skipped during the wait/direction rule (standalone bracket P&L) 51:+282|33:-13|1:+59.
By entry session (delta $, all seen): 0:-614,188 (0 ASIA,1 LONDON,2 PRE,3 NY-AM,4 NY-PM,5 CLOSE); by year: 2023:-173,019, 2024:-170,336, 2025:-201,559, 2026:-69,275.
Walk-forward ($/wk vs stop): w13_True: WF-PRE -5,560 [-9,729,-1,425] rank 1.00, WF-HOLD -249 [-4,344,+4,586] rank 0.99, WF-DEAD; w13_False: WF-PRE -9,720 [-15,881,-3,477] rank 0.19, WF-HOLD -2,002 [-12,412,+8,784] rank 0.96, WF-DEAD; exp_True: WF-PRE -4,032 [-8,322,-31] rank 1.00, WF-HOLD +0 [+0,+0] rank 1.00, WF-DEAD; exp_False: WF-PRE -9,203 [-16,146,-2,158] rank 0.28, WF-HOLD -4,413 [-14,216,+6,290] rank 0.61, WF-DEAD

### D6_PB7_PB5_ASIA (live/D6 [TAKEN-SIGNAL basis]; lots 10, stop 60, TF 1m; signals 671, baseline rows 667, kept by locks 660; baseline rows PRE/HOLD/X 339/184/137)
| cell | PRE $/wk [CI] (MDE) | HOLD | X | PRE pts/tr | HOLD pts/tr | P1 rank PRE/HOLD | wait inc PRE/HOLD ($/wk) | tier | failed |
|---|---|---|---|---|---|---|---|---|---|
| x30 N5 any | -3,986 [-8,732,+533] (MDE 6,514) | +919 [-4,121,+6,293] (MDE 7,748) | +458 [-3,286,+4,100] (MDE 5,359) | -4.41 | +0.80 | 0.75/0.80 | +0/+0 | DEAD | mean_up,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x30 Nbar any | -3,986 [-8,556,+501] (MDE 6,514) | +919 [-4,497,+6,223] (MDE 7,748) | +458 [-3,215,+4,180] (MDE 5,359) | -4.41 | +0.80 | 0.75/0.80 | +0/+0 | DEAD | mean_up,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x30 N15 any | -4,049 [-8,820,+311] (MDE 6,509) | +919 [-4,420,+6,283] (MDE 7,748) | +458 [-3,243,+4,211] (MDE 5,359) | -4.48 | +0.80 | 0.75/0.85 | -63/+0 | DEAD | mean_up,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x30 N60 same | -4,121 [-8,834,+357] (MDE 6,477) | +349 [-6,189,+6,843] (MDE 9,178) | +610 [-3,152,+4,360] (MDE 5,512) | -4.56 | +0.30 | 0.80/0.40 | +196/-506 | DEAD | mean_up,placebo<0.95,CI,cost,year_share,neighbours,RC_p |

Same X, N=0 reference (any): PRE -3,986 [-8,768,+492] (MDE 6,514), HOLD +919 [-4,512,+6,108] (MDE 7,748), X +458 [-3,282,+4,074] (MDE 5,359).
Best-PRE cell decomposition (pre-lock pts, net of fee), PRE|HOLD|X: cuts 178|100|77; common-trade delta -1,499|+457|+129; lost baseline trades 24:-47|25:+338|4:-5; added re-entries 0:+0|1:-31|0:+0; signals skipped during the wait/direction rule (standalone bracket P&L) 24:-47|25:+338|4:-5.
By entry session (delta $, all seen): 0:-249,443 (0 ASIA,1 LONDON,2 PRE,3 NY-AM,4 NY-PM,5 CLOSE); by year: 2023:+16,243, 2024:-61,201, 2025:-212,261, 2026:+7,776.
Walk-forward ($/wk vs stop): w13_True: WF-PRE -2,986 [-6,125,-82] rank 1.00, WF-HOLD -1,386 [-5,200,+2,279] rank 0.28, WF-DEAD; w13_False: WF-PRE -6,230 [-11,371,-1,006] rank 0.72, WF-HOLD -117 [-6,371,+5,944] rank 0.63, WF-DEAD; exp_True: WF-PRE -3,567 [-7,061,-255] rank 1.00, WF-HOLD +0 [+0,+0] rank 0.67, WF-DEAD; exp_False: WF-PRE -5,078 [-10,083,-398] rank 0.94, WF-HOLD +919 [-4,493,+6,343] rank 0.89, WF-DEAD

### D6_SM_t60_sst_ASIA (live/D6 [TAKEN-SIGNAL basis]; lots 10, stop 20, TF 1m; signals 524, baseline rows 524, kept by locks 499; baseline rows PRE/HOLD/X 247/116/136)
| cell | PRE $/wk [CI] (MDE) | HOLD | X | PRE pts/tr | HOLD pts/tr | P1 rank PRE/HOLD | wait inc PRE/HOLD ($/wk) | tier | failed |
|---|---|---|---|---|---|---|---|---|---|
| x15 N10 any | +741 [-1,054,+2,561] (MDE 2,645) | +141 [-3,955,+3,767] (MDE 5,609) | +364 [-1,552,+2,067] (MDE 2,657) | +1.13 | +0.19 | 0.50/0.20 | +86/-350 | DEAD | placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x15 N5 any | +699 [-1,061,+2,507] (MDE 2,645) | +492 [-3,690,+4,038] (MDE 5,556) | +478 [-1,423,+2,187] (MDE 2,607) | +1.06 | +0.68 | 0.50/0.30 | +43/+0 | DEAD | placebo<0.95,CI,year_share,neighbours,RC_p |
| x15 Nbar any (best ALL) | +655 [-1,195,+2,491] (MDE 2,633) | +492 [-3,576,+3,957] (MDE 5,556) | +745 [-1,142,+2,480] (MDE 2,591) | +1.00 | +0.68 | 0.45/0.30 | +0/+0 | DEAD | placebo<0.95,CI,year_share,neighbours,RC_p |
| x15 N15 any | +585 [-1,316,+2,548] (MDE 2,695) | +238 [-3,819,+3,824] (MDE 5,641) | +364 [-1,541,+2,151] (MDE 2,657) | +0.89 | +0.33 | 0.55/0.25 | -71/-253 | DEAD | placebo<0.95,CI,cost,year_share,neighbours,RC_p |

Same X, N=0 reference (any): PRE +655 [-1,171,+2,541] (MDE 2,633), HOLD +492 [-3,557,+3,968] (MDE 5,556), X +745 [-1,177,+2,441] (MDE 2,591).
Best-PRE cell decomposition (pre-lock pts, net of fee), PRE|HOLD|X: cuts 179|89|97; common-trade delta +9|+215|+118; lost baseline trades 4:+68|2:+27|4:+155; added re-entries 0:+0|0:+0|0:+0; signals skipped during the wait/direction rule (standalone bracket P&L) 4:+68|2:+27|4:+155.
By entry session (delta $, all seen): 0:+76,139 (0 ASIA,1 LONDON,2 PRE,3 NY-AM,4 NY-PM,5 CLOSE); by year: 2023:+20,808, 2024:+58,027, 2025:-31,771, 2026:+29,075.
Walk-forward ($/wk vs stop): w13_True: WF-PRE -348 [-2,503,+1,782] rank 0.36, WF-HOLD -164 [-2,647,+2,265] rank 0.65, WF-DEAD; w13_False: WF-PRE -348 [-2,472,+1,777] rank 0.36, WF-HOLD -1,251 [-5,711,+2,644] rank 0.15, WF-DEAD; exp_True: WF-PRE -4 [-1,973,+2,047] rank 0.60, WF-HOLD +492 [-3,444,+4,018] rank 0.85, WF-DEAD; exp_False: WF-PRE -4 [-2,008,+2,032] rank 0.60, WF-HOLD +492 [-3,828,+3,970] rank 0.85, WF-DEAD

### D6_TB4B_ASIA (live/D6 [TAKEN-SIGNAL basis]; lots 10, stop 60, TF 1m; signals 843, baseline rows 837, kept by locks 831; baseline rows PRE/HOLD/X 442/196/193)
| cell | PRE $/wk [CI] (MDE) | HOLD | X | PRE pts/tr | HOLD pts/tr | P1 rank PRE/HOLD | wait inc PRE/HOLD ($/wk) | tier | failed |
|---|---|---|---|---|---|---|---|---|---|
| x25 N30 any | -2,339 [-7,325,+2,648] (MDE 7,182) | +3,697 [-3,879,+10,886] (MDE 10,588) | +2,336 [-3,248,+7,751] (MDE 7,830) | -1.98 | +3.02 | 0.30/0.35 | +70/+0 | DEAD | mean_up,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x25 N5 any | -2,409 [-7,332,+2,453] (MDE 7,179) | +3,697 [-3,560,+11,022] (MDE 10,588) | +2,336 [-3,204,+7,750] (MDE 7,830) | -2.04 | +3.02 | 0.35/0.35 | +0/+0 | DEAD | mean_up,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x25 Nbar any | -2,409 [-7,458,+2,779] (MDE 7,179) | +3,697 [-3,870,+11,196] (MDE 10,588) | +2,336 [-2,955,+7,499] (MDE 7,830) | -2.04 | +3.02 | 0.35/0.35 | +0/+0 | DEAD | mean_up,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x25 N15 any | -2,410 [-7,278,+2,414] (MDE 7,170) | +3,697 [-3,702,+10,998] (MDE 10,588) | +2,336 [-3,325,+7,627] (MDE 7,830) | -2.04 | +3.02 | 0.35/0.35 | -1/+0 | DEAD | mean_up,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x25 N30 same (best ALL) | -2,430 [-7,441,+2,425] (MDE 7,095) | +4,728 [-1,893,+12,050] (MDE 10,412) | +1,929 [-3,416,+7,177] (MDE 7,678) | -2.06 | +3.86 | 0.45/0.25 | +1/+0 | DEAD | mean_up,placebo<0.95,CI,cost,neighbours,RC_p |

Same X, N=0 reference (any): PRE -2,409 [-7,507,+2,510] (MDE 7,179), HOLD +3,697 [-3,384,+11,012] (MDE 10,588), X +2,336 [-3,077,+7,617] (MDE 7,830).
Best-PRE cell decomposition (pre-lock pts, net of fee), PRE|HOLD|X: cuts 256|132|125; common-trade delta -598|+483|+481; lost baseline trades 32:+392|18:-289|3:+56; added re-entries 1:+56|0:+0|0:+0; signals skipped during the wait/direction rule (standalone bracket P&L) 34:+390|19:-233|3:+56.
By entry session (delta $, all seen): 0:+45,669 (0 ASIA,1 LONDON,2 PRE,3 NY-AM,4 NY-PM,5 CLOSE); by year: 2023:+65,563, 2024:-149,298, 2025:+83,372, 2026:+46,031.
Walk-forward ($/wk vs stop): w13_True: WF-PRE -3,435 [-7,312,+292] rank 0.74, WF-HOLD +3,061 [-3,265,+9,355] rank 0.10, WF-DEAD; w13_False: WF-PRE -4,812 [-10,196,+588] rank 0.28, WF-HOLD +2,450 [-5,486,+9,814] rank 0.02, WF-DEAD; exp_True: WF-PRE -3,476 [-7,932,+662] rank 0.74, WF-HOLD +617 [-2,794,+5,111] rank 0.00, WF-DEAD; exp_False: WF-PRE -3,472 [-8,758,+1,637] rank 0.74, WF-HOLD +3,618 [-3,508,+10,714] rank 0.18, WF-DEAD

### D6_TB4W_03_ASIA (live/D6 [TAKEN-SIGNAL basis]; lots 10, stop 60, TF 1m; signals 1421, baseline rows 1418, kept by locks 1273; baseline rows PRE/HOLD/X 701/321/251)
| cell | PRE $/wk [CI] (MDE) | HOLD | X | PRE pts/tr | HOLD pts/tr | P1 rank PRE/HOLD | wait inc PRE/HOLD ($/wk) | tier | failed |
|---|---|---|---|---|---|---|---|---|---|
| x30 N60 same | -2,613 [-8,789,+3,668] (MDE 9,181) | -2,849 [-10,223,+4,634] (MDE 11,025) | +317 [-4,495,+5,129] (MDE 6,955) | -1.40 | -1.42 | 0.65/0.70 | +175/-809 | DEAD | mean_up,holdout_sign,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x20 N5 same | -2,675 [-10,003,+4,578] (MDE 10,404) | -5,156 [-14,997,+4,389] (MDE 14,001) | +2,238 [-3,876,+8,346] (MDE 8,973) | -1.43 | -2.57 | 0.20/0.45 | +0/+0 | DEAD | mean_up,holdout_sign,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x20 N10 same | -2,675 [-9,841,+4,802] (MDE 10,404) | -5,156 [-14,620,+4,580] (MDE 14,001) | +2,238 [-4,388,+8,194] (MDE 8,973) | -1.43 | -2.57 | 0.20/0.45 | +0/+0 | DEAD | mean_up,holdout_sign,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x20 Nbar same | -2,675 [-9,907,+4,554] (MDE 10,404) | -5,156 [-15,331,+4,472] (MDE 14,001) | +2,238 [-4,002,+8,127] (MDE 8,973) | -1.43 | -2.57 | 0.20/0.45 | +0/+0 | DEAD | mean_up,holdout_sign,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x30 N5 any (best ALL) | -3,129 [-8,931,+2,657] (MDE 8,278) | -233 [-7,152,+7,149] (MDE 10,207) | +2,007 [-2,994,+6,740] (MDE 7,044) | -1.67 | -0.12 | 0.60/0.85 | +258/+0 | DEAD | mean_up,holdout_sign,placebo<0.95,CI,cost(not top10),year_share,neighbours,RC_p |

Same X, N=0 reference (same): PRE -2,788 [-9,172,+3,273] (MDE 8,965), HOLD -2,040 [-8,955,+4,642] (MDE 9,941), X +585 [-4,321,+5,331] (MDE 6,909).
Best-PRE cell decomposition (pre-lock pts, net of fee), PRE|HOLD|X: cuts 492|229|162; common-trade delta -1,612|+632|+383; lost baseline trades 3:-68|0:+0|0:+0; added re-entries 1:+56|1:+56|0:+0; signals skipped during the wait/direction rule (standalone bracket P&L) 3:-68|0:+0|0:+0.
By entry session (delta $, all seen): 0:-291,686, 1:+18,472 (0 ASIA,1 LONDON,2 PRE,3 NY-AM,4 NY-PM,5 CLOSE); by year: 2023:-42,567, 2024:-177,463, 2025:-31,431, 2026:-21,753.
Walk-forward ($/wk vs stop): w13_True: WF-PRE -2,702 [-8,565,+2,774] rank 0.86, WF-HOLD +1,696 [-1,077,+5,591] rank 1.00, WF-DEAD; w13_False: WF-PRE -2,411 [-8,956,+4,074] rank 0.92, WF-HOLD -623 [-9,275,+8,379] rank 0.96, WF-DEAD; exp_True: WF-PRE -4,093 [-9,481,+613] rank 0.41, WF-HOLD +1,389 [-2,164,+6,122] rank 1.00, WF-DEAD; exp_False: WF-PRE -3,729 [-9,903,+2,296] rank 0.55, WF-HOLD -3,802 [-12,025,+5,235] rank 0.44, WF-DEAD

### ST (research non-D6; lots 10, stop 60, TF 1m; signals 23801, baseline rows 4871, kept by locks 3020; baseline rows PRE/HOLD/X 1601/666/753)
| cell | PRE $/wk [CI] (MDE) | HOLD | X | PRE pts/tr | HOLD pts/tr | P1 rank PRE/HOLD | wait inc PRE/HOLD ($/wk) | tier | failed |
|---|---|---|---|---|---|---|---|---|---|
| x15 N10 same | -538 [-10,670,+9,732] (MDE 14,614) | -8,011 [-24,575,+9,649] (MDE 24,932) | -4,415 [-15,962,+7,455] (MDE 16,865) | -0.13 | -1.92 | 0.90/0.45 | +1,872/+4,478 | DEAD | mean_up,holdout_sign,SPAN2,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p |
| x15 N15 same | -1,023 [-10,991,+9,048] (MDE 14,217) | -8,730 [-25,976,+9,424] (MDE 26,042) | -8,355 [-20,566,+3,702] (MDE 17,923) | -0.24 | -2.10 | 0.95/0.45 | +1,387/+3,759 | DEAD | mean_up,holdout_sign,SPAN2,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x15 N5 same | -1,331 [-11,772,+8,817] (MDE 14,782) | -11,892 [-29,976,+6,699] (MDE 26,890) | -6,855 [-18,392,+4,363] (MDE 16,600) | -0.31 | -2.86 | 0.80/0.35 | +1,079/+598 | DEAD | mean_up,holdout_sign,SPAN2,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p |
| x15 N5 any | -1,674 [-12,733,+9,123] (MDE 15,749) | -12,637 [-32,199,+7,411] (MDE 29,086) | -6,397 [-21,379,+8,616] (MDE 21,883) | -0.39 | -3.04 | 0.30/0.55 | +4,092/+4,225 | DEAD | mean_up,holdout_sign,SPAN2,placebo<0.95,CI,maxDD,cost,neighbours,RC_p |

Same X, N=0 reference (same): PRE -2,410 [-12,880,+8,272] (MDE 15,613), HOLD -12,489 [-28,855,+5,276] (MDE 25,089), X -7,500 [-18,905,+3,832] (MDE 16,251).
Best-PRE cell decomposition (pre-lock pts, net of fee), PRE|HOLD|X: cuts 4042|1796|1562; common-trade delta -2,218|-701|-1,080; lost baseline trades 295:-391|132:-588|134:+708; added re-entries 2800:+830|1239:-2,015|1225:+1,332; signals skipped during the wait/direction rule (standalone bracket P&L) 701:-1,842|320:-1,637|260:+35.
By entry session (delta $, all seen): 0:-141,347, 1:+8,039, 2:-202,900, 3:+269,018, 4:-425,063, 5:+1,302 (0 ASIA,1 LONDON,2 PRE,3 NY-AM,4 NY-PM,5 CLOSE); by year: 2023:-170,221, 2024:-158,596, 2025:-233,454, 2026:+71,319.
Walk-forward ($/wk vs stop): w13_True: WF-PRE -8,901 [-17,390,-547] rank 0.28, WF-HOLD -7,518 [-20,964,+5,644] rank 0.85, WF-DEAD; w13_False: WF-PRE -11,639 [-21,486,-1,903] rank 0.06, WF-HOLD -16,380 [-32,619,+656] rank 0.28, WF-DEAD; exp_True: WF-PRE -4,893 [-13,266,+3,382] rank 0.71, WF-HOLD +0 [+0,+0] rank 0.99, WF-DEAD; exp_False: WF-PRE -7,433 [-16,023,+1,021] rank 0.47, WF-HOLD -12,926 [-26,608,+1,073] rank 0.47, WF-DEAD

### WT (research non-D6; lots 7, stop 45, TF 1m; signals 25561, baseline rows 6840, kept by locks 4373; baseline rows PRE/HOLD/X 2327/953/1093)
| cell | PRE $/wk [CI] (MDE) | HOLD | X | PRE pts/tr | HOLD pts/tr | P1 rank PRE/HOLD | wait inc PRE/HOLD ($/wk) | tier | failed |
|---|---|---|---|---|---|---|---|---|---|
| x30 N30 same | -792 [-7,215,+5,484] (MDE 9,083) | -1,094 [-10,156,+7,681] (MDE 13,054) | -4,754 [-11,616,+2,436] (MDE 10,207) | -0.18 | -0.26 | 0.45/0.75 | +873/-1,397 | DEAD | mean_up,holdout_sign,SPAN2,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p |
| x30 N60 any (best ALL) | -930 [-5,958,+4,028] (MDE 7,224) | -3,333 [-10,940,+4,553] (MDE 11,081) | +375 [-6,568,+7,174] (MDE 9,869) | -0.21 | -0.80 | 0.40/0.50 | +6,684/-517 | DEAD | mean_up,holdout_sign,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p |
| x30 N10 same | -1,447 [-7,848,+4,720] (MDE 9,083) | +1,178 [-8,079,+10,014] (MDE 13,504) | -5,760 [-12,994,+1,665] (MDE 10,314) | -0.33 | +0.28 | 0.65/0.75 | +219/+875 | DEAD | mean_up,SPAN2,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p |
| x30 N5 same | -1,466 [-7,868,+5,001] (MDE 9,203) | +540 [-9,152,+9,260] (MDE 13,394) | -5,240 [-12,090,+1,793] (MDE 9,972) | -0.34 | +0.13 | 0.70/0.75 | +200/+237 | DEAD | mean_up,SPAN2,placebo<0.95,CI,maxDD,cost,year_share,neighbours,RC_p |

Same X, N=0 reference (same): PRE -1,665 [-8,184,+4,717] (MDE 9,297), HOLD +303 [-9,268,+8,889] (MDE 13,424), X -4,945 [-11,974,+2,492] (MDE 10,283).
Best-PRE cell decomposition (pre-lock pts, net of fee), PRE|HOLD|X: cuts 1673|703|659; common-trade delta -1,288|+101|+179; lost baseline trades 1377:-2,379|645:+18|477:+1,133; added re-entries 917:-1,435|390:-380|388:-1,180; signals skipped during the wait/direction rule (standalone bracket P&L) 2649:-5,536|1326:-1,616|1128:+1,005.
By entry session (delta $, all seen): 0:-54,029, 1:-230,483, 2:-90,105, 3:-111,529, 4:+184,168, 5:-1,646 (0 ASIA,1 LONDON,2 PRE,3 NY-AM,4 NY-PM,5 CLOSE); by year: 2023:-163,612, 2024:+70,247, 2025:-132,383, 2026:-77,875.
Walk-forward ($/wk vs stop): w13_True: WF-PRE -5,865 [-11,820,-72] rank 0.26, WF-HOLD -2,489 [-10,872,+5,626] rank 0.84, WF-DEAD; w13_False: WF-PRE -5,865 [-11,726,+203] rank 0.26, WF-HOLD -3,658 [-12,596,+4,840] rank 0.74, WF-DEAD; exp_True: WF-PRE -2,331 [-7,308,+2,588] rank 0.92, WF-HOLD +0 [+0,+0] rank 0.96, WF-DEAD; exp_False: WF-PRE -2,742 [-7,809,+2,233] rank 0.86, WF-HOLD -3,333 [-11,016,+4,048] rank 0.79, WF-DEAD

### MA (research non-D6; lots 10, stop 60, TF 10m; signals 4045, baseline rows 2089, kept by locks 1776; baseline rows PRE/HOLD/X 915/404/457)
| cell | PRE $/wk [CI] (MDE) | HOLD | X | PRE pts/tr | HOLD pts/tr | P1 rank PRE/HOLD | wait inc PRE/HOLD ($/wk) | tier | failed |
|---|---|---|---|---|---|---|---|---|---|
| x30 N5 same | -1,018 [-7,984,+5,832] (MDE 9,900) | +2,977 [-7,203,+13,198] (MDE 14,700) | +70 [-7,103,+7,600] (MDE 10,843) | -0.42 | +1.18 | 0.60/0.05 | +0/+0 | DEAD | mean_up,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x30 Nbar same | -1,018 [-7,869,+5,775] (MDE 9,900) | +2,977 [-6,907,+12,929] (MDE 14,700) | +70 [-7,402,+7,850] (MDE 10,843) | -0.42 | +1.18 | 0.60/0.05 | +0/+0 | DEAD | mean_up,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x30 Nbar any | -1,122 [-8,521,+5,958] (MDE 10,412) | +1,807 [-9,389,+13,071] (MDE 16,946) | +2,455 [-5,641,+10,494] (MDE 11,775) | -0.46 | +0.72 | 0.75/0.20 | +0/+0 | DEAD | mean_up,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x30 N10 same | -1,175 [-7,942,+5,679] (MDE 9,929) | +2,977 [-6,703,+13,103] (MDE 14,700) | +70 [-7,378,+7,368] (MDE 10,843) | -0.48 | +1.18 | 0.55/0.05 | -157/+0 | DEAD | mean_up,placebo<0.95,CI,cost,year_share,neighbours,RC_p |
| x25 N15 same (best ALL) | -1,761 [-9,434,+5,906] (MDE 10,878) | +4,854 [-6,446,+16,477] (MDE 16,505) | +1,939 [-5,983,+9,378] (MDE 11,299) | -0.72 | +1.92 | 0.25/0.35 | +331/+0 | DEAD | mean_up,placebo<0.95,CI,cost,neighbours,RC_p |

Same X, N=0 reference (same): PRE -1,018 [-7,853,+5,911] (MDE 9,900), HOLD +2,977 [-7,346,+13,180] (MDE 14,700), X +70 [-7,757,+7,515] (MDE 10,843).
Best-PRE cell decomposition (pre-lock pts, net of fee), PRE|HOLD|X: cuts 692|294|362; common-trade delta -1,014|+208|+935; lost baseline trades 221:-430|99:+199|77:+469; added re-entries 200:+1,086|92:+271|118:-137; signals skipped during the wait/direction rule (standalone bracket P&L) 459:-1,551|194:-622|170:+629.
By entry session (delta $, all seen): 0:+135,776, 1:-53,244, 2:+87,327, 3:-103,462, 4:-44,458 (0 ASIA,1 LONDON,2 PRE,3 NY-AM,4 NY-PM,5 CLOSE); by year: 2023:-47,918, 2024:-7,471, 2025:-23,185, 2026:+100,512.
Walk-forward ($/wk vs stop): w13_True: WF-PRE -6,157 [-12,416,-259] rank 0.24, WF-HOLD -5,134 [-16,055,+5,654] rank 0.07, WF-DEAD; w13_False: WF-PRE -5,543 [-13,393,+2,272] rank 0.34, WF-HOLD -2,376 [-14,416,+9,442] rank 0.34, WF-DEAD; exp_True: WF-PRE -6,576 [-12,938,-325] rank 0.17, WF-HOLD -182 [-11,520,+10,866] rank 0.57, WF-DEAD; exp_False: WF-PRE -5,653 [-12,775,+1,947] rank 0.33, WF-HOLD -408 [-12,428,+10,932] rank 0.54, WF-DEAD


## Sequence effects: the blocked and re-entered signals (all seen windows, summed over cells of a tier; pre-lock pts net of fee, MEASURED)
Columns: mean paired $/wk per cell, mean wait increment over the same-X N=0 reference, signals skipped during the wait/direction rule with their standalone-bracket P&L per signal, re-entries the baseline never took (added) and baseline trades lost, per trade.

| tier | N | variant | cells | delta $/wk | wait inc $/wk | skipped n | skipped pts/signal | added n | added pts/trade | lost n | lost pts/trade |
|---|---|---|---|---|---|---|---|---|---|---|---|
| A | 10 | any | 37 | -5,618 | +357 | 53,829 | -1.37 | 109,477 | -0.67 | 19,830 | +0.02 |
| A | 10 | same | 37 | -4,096 | +123 | 234,621 | -0.88 | 72,378 | -0.51 | 62,980 | -0.32 |
| A | 15 | any | 37 | -5,494 | +481 | 73,724 | -1.28 | 100,645 | -0.68 | 22,233 | -0.16 |
| A | 15 | same | 37 | -4,030 | +189 | 243,258 | -0.88 | 68,307 | -0.49 | 64,117 | -0.31 |
| A | 30 | any | 37 | -5,726 | +250 | 123,101 | -0.92 | 83,387 | -0.63 | 30,223 | +0.37 |
| A | 30 | same | 37 | -4,485 | -267 | 262,738 | -0.77 | 61,239 | -0.73 | 67,647 | -0.34 |
| A | 5 | any | 37 | -5,810 | +166 | 31,775 | -1.82 | 119,787 | -0.72 | 17,331 | -0.66 |
| A | 5 | same | 37 | -4,236 | -18 | 224,419 | -0.88 | 77,418 | -0.58 | 61,804 | -0.39 |
| A | 60 | any | 37 | -5,689 | +287 | 195,799 | -0.48 | 65,968 | -0.68 | 45,819 | +0.27 |
| A | 60 | same | 37 | -4,608 | -389 | 296,266 | -0.82 | 51,902 | -0.97 | 74,147 | -0.41 |
| A | bar | any | 37 | -5,976 | +0 | 0 | +0.00 | 136,555 | -0.76 | 15,474 | -0.70 |
| A | bar | same | 37 | -4,219 | +0 | 217,053 | -0.89 | 81,318 | -0.55 | 61,248 | -0.44 |
| B | 10 | any | 50 | -3,360 | -10 | 781 | -0.49 | 97 | +5.29 | 778 | -0.46 |
| B | 10 | same | 50 | -3,217 | +25 | 30,688 | +0.02 | 47 | +18.33 | 30,635 | +0.03 |
| B | 15 | any | 50 | -3,384 | -34 | 1,539 | -3.29 | 97 | +5.29 | 1,536 | -3.28 |
| B | 15 | same | 50 | -3,192 | +50 | 30,971 | -0.12 | 47 | +18.33 | 30,918 | -0.11 |
| B | 30 | any | 50 | -3,294 | +56 | 4,712 | -1.56 | 97 | +5.29 | 4,709 | -1.55 |
| B | 30 | same | 50 | -3,152 | +90 | 32,065 | -0.15 | 47 | +18.33 | 32,012 | -0.15 |
| B | 5 | any | 50 | -3,352 | -2 | 308 | -0.38 | 97 | +5.29 | 305 | -0.29 |
| B | 5 | same | 50 | -3,221 | +22 | 30,535 | +0.01 | 47 | +18.33 | 30,482 | +0.02 |
| B | 60 | any | 50 | -3,355 | -5 | 12,034 | +0.13 | 82 | +0.79 | 12,016 | +0.06 |
| B | 60 | same | 50 | -3,181 | +62 | 34,574 | -0.18 | 45 | +18.08 | 34,519 | -0.18 |
| B | bar | any | 50 | -3,355 | -5 | 155 | +10.68 | 100 | +4.92 | 155 | +10.68 |
| B | bar | same | 50 | -3,233 | +9 | 30,458 | +0.03 | 47 | +18.33 | 30,405 | +0.04 |

Reading. (1) The signals that a blackout skips would on average have LOST money on their own bracket (tier A: -0.5 to -1.8 pts/signal, e.g. -1.4 for N10 any), and the re-entries that a cut frees (added) average -0.5 to -1.0 pts/trade: re-entering right after a cut is a bad trade, so waiting helps relative to cutting and re-entering at once (wait increment +250 to +480 $/wk per cell for N10-60 any, mean, CIs spanning 0; the same-direction variant ranges -390 to +190). (2) That does not rescue the cut: the cut itself costs about -4k to -6k $/wk per cell in tier A (cut trades forfeit the recoveries; the later stop is not avoided often enough), so every cell is still below the stop in sum. (3) "Until the next signal-series bar" is equivalent to N=0 by construction in tier A (fresh signals only fire at bar boundaries, so the first signal after a cut is never blocked): its wait increment is exactly 0; it is kept in the family as pre-registered (12 of the 1,044 cells per book are therefore duplicates of N=0). (4) Tier B books carry the TAKEN-SIGNAL flag: their re-entry set is the baseline's own entries, so the freeing effect is not measured and their numbers are the THLB cut effect plus a small blackout; do not read them as a re-entry result.

## Gates, multiplicity, power
Best-of-N: per-book White reality check on PRE over the book's arming cells: p from 0.26 (PB) to 1.00; no book below 0.05. Pooled-cell RC across books was not run separately (every book already fails). Placebo P1 (random cuts at the same rate, 20 draws, same blackout and engine): no cell reaches rank 0.95 in both PRE and HOLD. Costs: the cost gate (N, MW, C all PRE and HOLD > 0) was evaluated for the best 10 PRE cells per book and fails for 30 of the 39 top-10 cells that have PRE > 0 (the other 9 fail other gates; see per-cell failed lists). MDE is printed beside every $/wk (typical per-cell MDE of a book is several thousand $/wk, larger than any positive HOLD or PRE number found); a TIES verdict therefore means undetectable, not zero.

## Candidates / refit
32 cells have PRE > 0 and HOLD >= 0 (selected on PRE, HOLD out of sample); all are DEAD on the gates (best-of-N noise: 478 of 1,044 cells have a positive wait increment and 326 lose significantly). Two walk-forward chains (CR, FORCED policy, 13-week and expanding) are >= 0 in WF-PRE and WF-HOLD; the primary with-hold chains are WF-DEAD for every book. Lines: l2vast/ds3/out/cutwait/policy_candidate.txt (NOT for live); nightly re-fit script l2vast/ds3/code/cutwait/cw_refit.py (writes policy_candidate_refit.txt, hard-capped at 20260206 until the user extends the window; the res_*.pkl series must be rebuilt with cw_run.py when new trades exist).

## Caveats
Engine uses the book's own baseline rows with MEASURED prices, so absolute $ differ from the P9-priced stack numbers; all deltas are paired. Signal timeframes for PE, CR and the D6 cells are assumed (only affects the 'bar' cells, which are N=0). Same-direction restriction lasts to the end of the label day or the next accepted entry (prereg). EM, O6, B3, ES/RTY not scored. Cut X >= median stop never arms (SM_t60_sst: only 6 of 7 levels arm below 20 pts; CR median stop 11.5): those cells are excluded from the family counts. The pooled-over-books walk-forward chain was not computed (per-book chains only).
