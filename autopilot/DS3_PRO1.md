# DS3 PRO1 - T-PULLBACK PRO P1 (pullback defined by the tape) and P7 (learned pullback-end detector) - 2026-10-27T11:06Z
Research only; nothing is a live recommendation. Agent PRO1. Preregs: l2vast/ds3/prereg/PRO1_P1A..P1F.md (108 cells, 24/24/12/12/24/12) and PRO1_P7.md (9 cells), sha256 in autopilot/DECISIONS.md and in the rows file; ledger +117 (cells counted = 117; model fits and 50 permutation pipelines in the best-of-N null). Code l2vast/ds3/code/pro1/. Rows l2vast/ds3/rows/DS3_PRO1.json. Truncation audit (data cut at 62%): 108 P1 cells, 0 mismatching events.

## Verdict line
- Cells scored 114 of 117 (3 P7 theta=.65 cells had < 100 trades; DEAD, too few). Final verdicts (MAPPED basis; direct L2 replay pending): PASS 3, CANDIDATE 19, DEAD 95. Mapped-basis: PASS 3, CANDIDATE 19.
- **The tape does not improve the pullback.** Against the matched D3PB price-trigger cell (same regime, same level, trigger T1) the 108 P1 tape cells have WF weekly mean -$842/wk on average (better in 40% of cells; by family -$87 to -$1.9k); against the base cell PB_ST10_EMA5_T1 the paired per-trade delta is +2.0 pt on average (median +0.9, CI excludes 0 upward for 41 of 112 cells and downward for 22). Every P1 cell's weekly P&L is below ST10's at 10 lots (paired weekly delta vs ST negative in nearly all), exactly as the D3PB base cells. Whatever positive P&L the cells show is trend/bracket beta of 2024-26 (the same gain appears with the price trigger), and the tape end-of-pullback condition adds nothing detectable (all effects below the MDE).
- **P7 learned detector: DEAD.** WF AUC on 414k qualifying pullback bars = 0.494 PRE (week-block CI [0.47,0.51]) for the full model, 0.494 cheap, 0.492 tape-only, i.e. chance (PRED: tape AUC .50-.54); calibrated P >= .65 never reaches 100 trades; P >= .55/.60 cells fail permutation and paired-vs-ST tests. The cheap no-tape control is as good as the full model (so the tape adds nothing) and the tape-only model keeps 57% of its gain on noise columns.
- Best P1 cells by the standard V2 verdict are listed below; none is a timing improvement over ST or over its matched price-trigger cell. 14 of 83 cells with PRE>0 have placebo rank >= .95 (chance ~4).

## Method (one paragraph each)
- P1: arming/touch machinery = D3PB unchanged (regime ST10 or EMA200; level VWAP / 5-min EMA20 / 38-62% swing zone; edge touch; 30-min window; first touch); trigger = first completed 1-min bar from the touch bar on at which the tape condition holds (families ABS absorption/refill, AGG aggressor flip/run-length exhausted, IMB +-3/5-level imbalance reverts, QD counter-side queue depletion stops, LPC large-print cluster/print-size shift, SWR sweep-and-reclaim of the pullback low at 60/120 s). Variants and the one-sentence mechanism per cell are in the prereg. Tape = l2vast/tables/NQ/1min (per-minute aggregates of the 100-ms feed). Declared limitations: sweep-and-reclaim is at 60/120-s granularity (not 5-30 s); refill_n is not side-specific; no 1-s/100-ms re-aggregation was done. DS2 bracket/execution fixed (P5/P6 not varied). Pricing MAPPED for all, DIRECT L2 for non-DEAD + top 10 by mapped holdout Sharpe (26 cells).
- P7: one pooled LightGBM per feature set (full 85 cols / cheap no tape / tape only) on qualifying bars (ST10 regime and close on the counter side of the 5-min EMA20, 414k rows), 33 monthly folds 2024-02..2026-10, 7-day embargo, in-window selection vs 20 noise columns, isotonic calibration in-window, CPCV 6-choose-2 (second holdout available only as CPCV OOF), 20/20/10 label-permutation pipelines. P2-type level features were built inside PRO1 (VWAP/EMA/Keltner/flip/38-62/prior-day/session extremes, confluence): PRO2's level series (PRO_levels.parquet) was not available at freeze; P4-type trend-quality features likewise own (ER, Supertrend age, slopes, depth). Thresholds .55/.60/.65.
- Windows: selection WF-PRE 2024-02..2025-06; holdout 2025-07+ read once for the track after autopilot/DS3_PRO1_PREHOLD.md (logged DS3_PRO1; second holdout 2023-04..2024-01 looked at together; P7 second holdout = CPCV OOF, labelled). Equal-risk columns via equal_risk.py. MDE: standalone weekly mean ~$11-18k/wk (WF-PRE), paired vs ST ~8-14 pt per overlapping trade; every null below is at that MDE or worse. Trades/wk < 3 are flagged LOW-FREQUENCY (9 cells; kept).

## Family summary (mapped, WF unless stated; matched price-trigger control from D3PB)
| group | family | cells | tr/wk | WF $/wk | same-cell price trigger $/wk | HOLD $/wk | price-trigger HOLD | share WF>0 | paired vs ST pt | paired vs base cell pt | placebo>=.95 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P1A | ABS absorption/refill | 24 | 15.4 | 4,865 | 5,431 | 5,523 | 9,350 | 0.96 | +7.8 | +0.7 | 6 |
| P1B | AGG aggressor flip | 24 | 21.4 | 4,660 | 5,431 | 5,766 | 9,350 | 0.79 | +12.5 | +3.5 | 4 |
| P1C | IMB imbalance revert | 12 | 22.1 | 5,344 | 5,431 | 8,215 | 9,350 | 0.83 | +10.4 | +2.5 | 1 |
| P1D | QD queue depletion stops | 12 | 17.2 | 4,799 | 5,431 | 9,180 | 9,350 | 1.00 | +9.1 | +0.6 | 1 |
| P1E | LPC large prints | 24 | 12.5 | 4,305 | 5,431 | 7,352 | 9,350 | 0.92 | +6.9 | -1.0 | 2 |
| P1F | SWR sweep-reclaim | 12 | 22.3 | 3,494 | 5,431 | 7,586 | 9,350 | 0.75 | +18.0 | +5.8 | 0 |

## PASS / CANDIDATE cells (all that are not DEAD)
Columns: tr/wk, WF/PRE/HOLD/2023-span weekly $ (10 lots; mapped unless the direct basis is shown), WF CI, placebo (PRE), paired vs ST pt per trade [CI] (MDE, pairs), paired vs base cell PB_ST10_EMA5_T1, quiet/wide WF $/wk, long/short WF $/wk, equal-risk $/wk and lots, delta vs ST at equal risk, DS3 marginal Sharpe (direct only), executability.
| cell | verdict | basis | failed | tr/wk | WF | PRE | HOLD | 2023 | WF CI | plc | paired vs ST | paired vs base | quiet / wide | long / short | eq-risk $/wk (lots) | d vs ST eq-risk | DS3 marg. Sh | exec |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PRO1_AGG_CD2_EMA200_SWZ | CANDIDATE | mapped | plc>=.95 | 26.4 | 14,950 | 2,800 | 27,941 | 2,399 | [5,338,24,485] | 0.85 | +11.1 [8.5,14.2] (MDE 4.0, n 746) | -2.7 [-5.0,-0.4] | 2,776 / 11,609 | 6,867 / 8,084 | 13,821 (9.5) | -528 | - | EXEC-ONLY |
| PRO1_IMB_K5_EMA200_SWZ | CANDIDATE | mapped | plc>=.95 | 24.5 | 14,084 | 5,271 | 23,460 | 7,568 | [5,799,23,375] | 0.93 | +9.1 [6.0,12.5] (MDE 4.6, n 645) | -2.2 [-4.6,0.1] | 2,595 / 10,977 | 7,304 / 6,781 | 14,330 (10.5) | -20 | - | EXEC-ONLY |
| PRO1_AGG_CD3_EMA200_SWZ | CANDIDATE | mapped | plc>=.95 | 25.9 | 13,481 | 41 | 27,894 | 3,224 | [4,963,22,638] | 0.68 | +9.9 [7.2,12.8] (MDE 4.0, n 746) | -2.5 [-4.7,-0.2] | 2,393 / 10,793 | 3,530 / 9,951 | 13,646 (10.3) | -704 | - | EXEC-ONLY |
| PRO1_IMB_K3_EMA200_SWZ | CANDIDATE | mapped | plc>=.95 | 25.4 | 13,299 | 1,937 | 25,457 | 12,048 | [4,411,23,052] | 0.75 | +6.8 [4.0,9.7] (MDE 4.2, n 710) | -4.7 [-7.2,-2.3] | 3,519 / 9,588 | 8,632 / 4,667 | 13,473 (10.2) | -877 | - | EXEC-ONLY |
| PRO1_IMB_K5_ST10_SWZ | PASS | mapped | - | 24.4 | 12,915 | 6,722 | 19,459 | 5,756 | [3,533,22,686] | 0.97 | +7.8 [4.6,11.1] (MDE 4.6, n 695) | -1.8 [-4.2,0.4] | 2,147 / 9,929 | 6,978 / 5,937 | 11,977 (9.8) | -2,373 | - | EXEC-ONLY |
| PRO1_QD_R6_EMA200_SWZ | CANDIDATE | mapped | plc>=.95 | 23.6 | 11,368 | 4,862 | 18,276 | 1,045 | [2,302,20,524] | 0.82 | +9.0 [6.3,12.1] (MDE 4.1, n 719) | -4.3 [-6.8,-1.9] | 2,911 / 8,045 | 9,713 / 1,655 | 10,979 (10.0) | -3,371 | - | EXEC-ONLY |
| PRO1_AGG_RL3_ST10_SWZ | CANDIDATE | mapped | plc>=.95 | 26.4 | 10,244 | 4,376 | 16,474 | 1,204 | [1,189,19,363] | 0.88 | +8.8 [6.1,11.4] (MDE 3.8, n 794) | -3.1 [-5.6,-0.9] | 1,939 / 8,032 | 7,320 / 2,925 | 9,898 (9.9) | -4,452 | - | EXEC-ONLY |
| PRO1_AGG_RL3_EMA200_SWZ | CANDIDATE | mapped | plc>=.95 | 25.9 | 9,720 | 6,060 | 13,558 | 1,343 | [1,431,19,043] | 0.82 | +8.3 [5.5,11.2] (MDE 3.9, n 700) | -4.9 [-7.3,-2.7] | 2,584 / 7,518 | 7,087 / 2,634 | 10,623 (10.4) | -3,727 | - | EXEC-ONLY |
| PRO1_ABS_R10_EMA200_SWZ | PASS | mapped | - | 17.5 | 9,546 | 6,492 | 12,727 | 6,731 | [1,839,17,431] | 0.95 | +4.4 [0.3,8.3] (MDE 5.9, n 325) | -5.8 [-9.1,-2.3] | 2,082 / 7,906 | 6,434 / 3,112 | 12,117 (12.0) | -2,233 | - | EXEC-ONLY |
| PRO1_AGG_CD3_ST10_SWZ | CANDIDATE | mapped | plc>=.95 | 26.0 | 9,387 | 5,683 | 13,277 | 4,785 | [175,18,516] | 0.80 | +8.5 [5.7,11.3] (MDE 4.0, n 819) | -1.5 [-3.7,0.7] | 2,837 / 5,543 | 3,106 / 6,281 | 8,786 (10.4) | -5,564 | - | EXEC-ONLY |
| PRO1_ABS_V15_EMA200_SWZ | CANDIDATE | mapped | WF_CI>0 | 23.7 | 8,421 | 6,865 | 9,990 | 3,077 | [-916,17,528] | 0.95 | +7.5 [4.2,11.2] (MDE 4.9, n 629) | -2.9 [-5.2,-0.6] | 2,014 / 6,449 | 6,053 / 2,367 | 8,709 (10.2) | -5,641 | - | EXEC-ONLY |
| PRO1_LPC_Z13_EMA200_EMA5 | CANDIDATE | mapped | plc>=.95 | 17.5 | 8,001 | 3,443 | 12,839 | 214 | [576,15,056] | 0.85 | +6.3 [1.7,10.6] (MDE 6.4, n 335) | -3.0 [-5.2,-0.5] | 2,748 / 5,110 | 4,041 / 3,960 | 10,036 (12.7) | -4,314 | - | EXEC-ONLY |
| PRO1_AGG_RL3_EMA200_EMA5 | CANDIDATE | mapped | WF_CI>0 | 25.6 | 7,714 | 6,199 | 9,250 | 184 | [-1,234,17,957] | 0.95 | +11.3 [8.0,14.4] (MDE 4.6, n 658) | +2.3 [0.8,4.1] | 3,935 / 4,573 | 5,555 / 2,159 | 8,515 (9.9) | -5,835 | - | EXEC-ONLY |
| PRO1_ABS_V25_EMA200_SWZ | CANDIDATE | mapped | plc>=.95 | 17.8 | 7,543 | 4,793 | 10,422 | 1,986 | [470,15,285] | 0.85 | +6.3 [2.2,10.4] (MDE 6.0, n 376) | -2.9 [-6.0,0.3] | 3,259 / 4,417 | 7,821 / -278 | 10,009 (12.9) | -4,341 | - | EXEC-ONLY |
| PRO1_ABS_R12_EMA200_SWZ | CANDIDATE | mapped | plc>=.95 | 10.7 | 7,254 | 5,831 | 8,695 | 7,103 | [1,561,13,620] | 0.93 | +6.7 [0.6,12.4] (MDE 8.4, n 182) | -1.9 [-5.7,1.7] | 1,910 / 5,582 | 5,071 / 2,183 | 11,282 (15.2) | -3,068 | - | EXEC-ONLY |
| PRO1_QD_R4_EMA200_EMA5 | CANDIDATE | mapped | plc>=.95 | 15.2 | 7,045 | 59 | 14,535 | 6,686 | [302,13,674] | 0.47 | +5.9 [1.7,10.2] (MDE 6.2, n 352) | -0.6 [-2.5,1.4] | 1,081 / 5,920 | 3,233 / 3,812 | 9,933 (14.1) | -4,417 | - | EXEC-ONLY |
| PRO1_ABS_R10_EMA200_EMA5 | CANDIDATE | mapped | WF_CI>0 | 16.9 | 7,001 | 9,333 | 4,365 | 6,632 | [-412,13,650] | 1.00 | +7.5 [2.4,12.9] (MDE 7.9, n 281) | -0.6 [-3.3,2.1] | 1,172 / 6,149 | 5,339 / 1,662 | 10,174 (13.8) | -4,176 | - | EXEC-ONLY |
| PRO1_QD_R6_ST10_SWZ | CANDIDATE | mapped | WF_CI>0 | 23.4 | 6,177 | 3,562 | 8,931 | 732 | [-2,615,14,587] | 0.97 | +7.2 [4.1,9.8] (MDE 4.0, n 766) | -4.2 [-6.5,-1.9] | 1,629 / 4,054 | 5,720 / 457 | 6,134 (10.7) | -8,216 | - | EXEC-ONLY |
| PRO1_LPC_Z16_ST10_SWZ | CANDIDATE | mapped | plc>=.95 | 7.7 | 5,810 | 2,258 | 9,586 | 12,200 | [550,11,194] | 0.80 | +4.3 [-2.5,11.9] (MDE 10.3, n 108) | -5.2 [-10.4,-0.6] | 4,602 / 1,128 | 3,505 / 2,304 | 9,593 (17.5) | -4,757 | - | EXEC-ONLY |
| PRO1_ABS_R12_EMA200_EMA5 | PASS | mapped | - | 10.4 | 5,788 | 5,942 | 5,537 | 2,445 | [213,11,238] | 0.95 | +8.0 [1.7,14.6] (MDE 9.4, n 156) | -0.7 [-3.8,2.6] | 1,956 / 4,149 | 4,283 / 1,506 | 9,698 (16.5) | -4,652 | - | EXEC-ONLY |
| PRO1_ABS_R10_ST10_EMA5 | CANDIDATE | mapped | WF_CI>0 | 17.5 | 5,410 | 6,458 | 4,192 | 3,148 | [-2,728,13,180] | 0.95 | +6.0 [1.2,10.3] (MDE 6.4, n 327) | +1.2 [-1.2,3.4] | 900 / 4,209 | 3,953 / 1,456 | 5,899 (11.5) | -8,451 | - | EXEC-ONLY |
| PRO1_AGG_RL5_EMA200_EMA5 | CANDIDATE | mapped | WF_CI>0 | 18.5 | 4,481 | 7,742 | 872 | 1,485 | [-2,680,12,268] | 0.95 | +13.4 [9.0,17.9] (MDE 6.6, n 361) | +5.0 [2.8,7.3] | 634 / 4,402 | 2,582 / 1,898 | 6,235 (12.3) | -8,115 | - | EXEC-ONLY |

## P7 learned pullback-end detector
| set | WF AUC PRE [CI] | WF AUC WF | CPCV AUC (same rows, PRE) | BSS | ECE | P>=.55 / .60 / .65 share | noise gain share | n rows |
|---|---|---|---|---|---|---|---|---|
| full | 0.4937 [0.471,0.515] | 0.5070 | 0.5195 | -0.0102 | 0.042 | 0.039 / 0.010 / 0.0051 | 0.00 | 151809 |
| cheap | 0.4944 [0.472,0.515] | 0.5060 | 0.5146 | -0.0101 | 0.033 | 0.048 / 0.006 / 0.0044 | 0.00 | 151809 |
| tape | 0.4921 [0.473,0.509] | 0.4955 | 0.5030 | -0.0074 | 0.030 | 0.025 / 0.003 / 0.0009 | 0.57 | 151809 |

| cell | tr/wk (PRE) | PRE $/wk | HOLD $/wk | WF $/wk [CI] | paired weekly vs ST | perm rank PRE (n) | placebo | x2 WF | CPCV-OOF 2023 span | verdict | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7_full_55 | 2.2 | 2,277 | 3,776 | 3,017 [253; 5,858] | -11,495 | 0.95 (20.0) | 0.75 | 2,595 | 8,130 | DEAD | tpw>=3,dST_wf>0,plc>=.95,AUC_lo>.5 |
| P7_full_60 | 1.0 | -1,152 | 2,482 | 593 [-1,315; 2,648] | -13,919 | 0.38 (16.0) | - | 419 | - | DEAD | tpw>=3,PRE>0,WF_CI>0,dST_wf>0,SPAN2oof>0,plc>=.95,perm>=.95,AUC_lo>.5 |
| P7_full_65 | <3 | - | - | - | - | - | - | - | - | DEAD | < 100 trades (calibrated P rarely reaches theta) |
| P7_cheap_55 | 2.2 | 1,008 | 4,332 | 2,619 [-288; 5,603] | -11,893 | 0.94 (18.0) | 0.68 | 2,129 | 4,007 | DEAD | tpw>=3,WF_CI>0,dST_wf>0,plc>=.95,perm>=.95,AUC_lo>.5 |
| P7_cheap_60 | 0.9 | -493 | 3,360 | 1,363 [-346; 3,395] | -13,149 | 0.33 (15.0) | - | 1,168 | - | DEAD | tpw>=3,PRE>0,WF_CI>0,dST_wf>0,SPAN2oof>0,plc>=.95,perm>=.95,AUC_lo>.5 |
| P7_cheap_65 | <3 | - | - | - | - | - | - | - | - | DEAD | < 100 trades (calibrated P rarely reaches theta) |
| P7_tape_55 | 2.5 | -2,759 | 1,298 | -820 [-4,107; 2,570] | -15,332 | 0.00 (10.0) | - | -902 | 3,647 | DEAD | tpw>=3,PRE>0,WF_CI>0,dST_wf>0,plc>=.95,perm>=.95,x2_WF>0,AUC_lo>.5,noise<=.2 |
| P7_tape_60 | 0.7 | -3,595 | 824 | -1,488 [-3,191; 29] | -15,999 | 0.00 (9.0) | - | -1,512 | -638 | DEAD | tpw>=3,PRE>0,WF_CI>0,dST_wf>0,SPAN2oof>0,plc>=.95,perm>=.95,x2_WF>0,AUC_lo>.5,noise<=.2 |
| P7_tape_65 | <3 | - | - | - | - | - | - | - | - | DEAD | < 100 trades (calibrated P rarely reaches theta) |

P7 reading: AUC 0.49-0.51 with CIs spanning 0.5 is the PRED result again; BSS is negative (the calibrated probabilities are worse than the constant base rate); thresholds .60/.65 select < 1% of bars and the few trades are indistinguishable from permutation draws (all P7 cells trade 0.7-2.5 per week, i.e. LOW-FREQUENCY; the label-shifted pipelines reach PRE weekly means of up to $3.1k/wk (full, theta .55; 95th pct $1.6k) against the real $2.3k, so the best-of-9 line is not beaten). No model, threshold or feature set is a candidate; the cheap-model control matches the full model, so tape contributes nothing measurable. Honest MDE: classifier AUC MDE ~.01 (so a true AUC of .52+ would have been seen), economic MDE ~$11-18k/wk standalone.

## Multiplicity and honesty
- N = 117 cells (+ 99 model fits, 50 permutation pipelines). With 108 P1 cells overlapping heavily (same touch events, 6 trigger families on 6 regime/level bases), the effective N is far lower, but 14/83 placebo ranks >= .95 and 94 paired-vs-ST CIs above 0 are what a trend-beta strategy with the DS2 bracket gives to every cell of this kind (the D3PB base reports the same).
- The SWZ-level and EMA200-regime cells show the large HOLD numbers (up to $28k/wk) with ~zero PRE (e.g. AGG_CD3_EMA200_SWZ PRE $41): a 2025-26 trend-regime effect that the price-trigger version of the same cell shares, not an end-of-pullback tape effect.
- All 108 P1 cells and P7 full/tape need tape features at run time: EXECUTION-SERVER-ONLY. Nothing is deliverable to NT8 as bars; the P7 cheap control is bar-only but dead.
- Disclosures: holdout/second-holdout looked once for the track (logged; pre-text sha in DECISIONS.md); ds3_addbook/equal_risk re-read the holdout once per direct finalist (addbook_looks.jsonl). The job was interrupted overnight (processes ended 17:40Z) and resumed 09:55Z unchanged.
