# DS3_SESSION_3_PAIRS - session-complementary pairs and singles as stack-adds (D3SS3, T-SESSION item 3 and 4), 2026-10-28

Research only; no live, execution-server or chart change; UNTOUCHED (label days after 2026-02-06) never read. Code l2vast/ds3/code/ss3/, outputs l2vast/ds3/out/ss3/ (metrics_hold.csv, tiers_all.csv, stress.csv, pairs_chosen.csv, screen_all.csv). Prereg l2vast/ds3/prereg/SS3_prereg.md sha256 b3dfb25682b02430a33780afddc4849f7b80ff17de9e336cf0d7ac6f11e67daf (DECISIONS.md, written before any pair was scored). PREHOLD autopilot/DS3_SESSION_3_PREHOLD.md sha256 fc32906c85da0dcfcd4de0b85d367d211ede4ef0c5aa16494cc006027d534890 (hashed and logged in out/ss3/looks.jsonl before HOLD/X were read; one HOLD look, one X look). DS3_SESSION_1_BOOKS.md did not exist when this ran, so the per-book session tables of D3SS1 were not used; the add is measured against the whole live stack (ST HM WT KB SM PE), which is what 'net of the books already in the stack' means here.

## 1. Verdict (plain)
- YES on the stated gates, with a basis caveat that I think decides the matter: 27 of 40 pairs are PAIR-PASS and 5 more PAIR-CANDIDATE at 20% risk (7 FAIL, 1 INFEASIBLE-LOTS); of 21 single legs 5 PASS, 8 CANDIDATE, 8 FAIL. A passing pair adds to the stack net of the books in it: HOLD add 11-32k/wk at 20% risk against a stack of 52,448/wk, HOLD Sharpe of stack 0.345 -> 0.42-0.54, correlation to the stack -0.16..+0.29 (HOLD), add dollars in the stack's 20 worst weeks (full span) positive in every passing unit (pairs +58k..+244k over those 20 weeks; the single CRT_M15 leg only +5k).
- THE CAVEAT: every passing pair is built from ICT-IC (IF_*), ICT-SF (CRT_*) cells (non-ICT legs appear only as PRO1 NY-PM, d4a and e1 partners of an IC/CRT leg). Those are MAPPED-basis rows on STORED fills: the IC source report (DS3_TICT.md) says the P9 mapping credits stop exits +2.6..+4.2 pts in 2025-26 and that IF_15s_eb's strict (CONS) verdict is negative; the pooled verdicts of IF_30s_eb is DEAD and IF_15s_eb CANDIDATE. My cost stress (section 9) shows the stack-add is fragile to exactly that size: slippage breakeven is 1.1-3.1 NQ points per trade for the passing pairs (an IF leg trades 45-55 times a week at about $390-610 mean per 10 lots, i.e. 2-3 pts), and HOLD turns negative at +2 pts per trade in 15 of 27 passing pairs (positive in 12, listed in section 9b). So the PASS is a PASS of the stored numbers, not of live fills. Nothing here is live-eligible until the legs are re-filled on the conservative basis.
- THE 2023 SPAN: reported, not a gate (user rule): the 2023-04..2024-01 add is negative in all 32 passing units (-0.6k to -14k/wk at 20% risk, MDE about 10-15k): ASIA/LONDON/IC edges did not exist in 2023 (they were 22-28% positive in D3SS2's X span). The stack itself earned 20,616/wk in that span, 52,448 in HOLD. This is an edge that appears in 2024 and is present in PRE and HOLD only; HOLD is 32 weeks (about 5.5 weeks in the 2026 stub), so '3 independent years' does not exist.
- Selection independence: all passing pairs reuse 3-4 independent rules (IF_30s/15s, CRT_M15/M30/H1, a few PRO1/e1/d4a); the 27 pair-pass verdicts are not 27 independent results. The honest count of independent session-complementary findings is: ASIA/LONDON/PRE IC-CRT block + NY-AM IC (one family, 2024+ only) and nothing independent of it.
- Best-of-F label (a label, not a gate): PRE one-sided p x F_screen (637 pairs) < 0.05 for 42 of the 61 units (all 32 PAIR-PASS); x F_ledger 18,588 < 0.05 for 22 of the 32 PAIR-PASS. Pairs counted into F: 40 scored (637 PRE-screened), 21 singles = 61 units (cap 40 pairs held).
- Session-pair view (section 5): PAIR-PASS counts by session pair: ASIA+LONDON 4, ASIA+PRE 2, ASIA+NY-AM 4, ASIA+NY-PM 4, LONDON+PRE 3, LONDON+NY-AM 4, LONDON+NY-PM 1, PRE+NY-AM 4, NY-AM+NY-PM 1, PRE+NY-PM 0 (the NY-PM pairs that fail do so on the 2026 stub half or the HOLD delta); the best pairs by the PRE rank are LONDON+NY-AM and ASIA+NY-AM. By MDE: the pass-pair HOLD deltas (11-32k) exceed their MDE (9-18k) in 26 of 27 (P15 does not); 4 of 5 passing singles exceed theirs.
- Recommendation: register the 12 cost-robust passing pairs (+2 pt still positive, section 9b) as forward SESSION PAIR BOOKS at half size (they fail only the 2023 span, which is a label), do NOT size them into the live stack, and queue the one thing that settles it: the CONS (conservative-fill) re-run of the IC/CRT legs with live-latency fills for the session windows below.

## 2. How the pairs were built (all stated in the prereg; deviations: none)
- Pool: PRE-selected cell-sessions (D3SS2, n>=100 PRE trades, PRE CI>0) minus 401 STACK-DUP cell-sessions (>=30% of PRE entries coincide, same minute and side, with a live stack book), one representative per cluster-session by PRE t, top 8 per session = 40 representatives (CLOSE has none). 637 pairs of different session and different cluster were PRE-screened (F_screen). The 40 scored pairs are the top 4 per session-pair by PRE alpha-t (intercept t of the pair book on the stack's PRE weekly series, i.e. what the stack does not already hold), at most 2 per leg.
- Book: per-leg risk parity (each leg scaled to unit PRE weekly SD), pair SD set to 10/20/30% of the stack's PRE weekly SD (the scale is fixed on PRE and applied unchanged to HOLD and X). Lots multiples per leg (x the stored 10-lot size) are in section 6 and in the PREHOLD file; one pair (P17: CRT_ib + G2, G2 needs 362x) is INFEASIBLE and a gate of 'no leg above 4x stored size' removes it (this gate was stated as a flag in the prereg and is treated as ineligible; stricter, not softer).
- Lock: LABEL = TRADE-ROW day lock, not the exact 1-s lock engine. No ledger cell has 1-s legs on disk (rows hold entry time, side, net $), so the exact engine cannot be run. The pair is one book; per label day, entries of both legs in time order are skipped once the running day P&L of earlier entries is >= +5R or <= -2R (R=12,000, the stack's per-book entry test, earlier entries treated as closed); the give-back arm and week floor are not applied. Unlocked results are in tiers_all.csv: the lock changes the tier of only 1 of 61 units at 20% risk (unlocked: 32 PASS / 12 CANDIDATE / 16 FAIL against 32 / 13 / 15), so the result does not depend on it.
- Stack: live stack weekly series (audit_lib), cut at label day 2026-02-06: stack mean/wk PRE 44,127 (SD 131,184), HOLD 52,448 (SD 151,891), X 20,616. The 45,947/wk audit baseline is the 185-week span to 2026-10-16, not read here. Weeks are ISO weeks of the label day; window-edge weeks are partial.
- Placebo: weekly sign-flip of the book (mean 0 by construction, 200 draws); rank >= 0.95 in HOLD for 42 of 61 units; D3SS2 caveats apply (sign-flip not random-in-regime).
- Limits to respect: IC/CRT/SF engines use stored fills not live-latency fills; mapped/direct labels are as the source labelled them; HOLD 2026 stub is 5.5 weeks; the cell-level HOLD of the legs had already been seen in D3SS2 (disclosed in the prereg), so the pair HOLD look is the first look at the pairs but not independent of the legs.

## Gates (prereg; none softened)
PAIR-CANDIDATE: PRE book weekly-mean CI lower > 0 and PRE alpha-t > 0; HOLD stack-add delta > 0 (20% risk); delta > 0 in both HOLD halves (2025-07..12 and 2026-01-01..02-06); HOLD Sharpe stack+add >= stack; add $ in the stack's 20 worst weeks (full span) >= 0 and in the PRE-derived worst 20 >= 0; lots multiple <= 4x. PAIR-PASS: PAIR-CANDIDATE and HOLD placebo rank >= 0.95 and PRE p x F_screen < 0.05. Failed gates of FAIL units: HOLD 2026 stub half <= 0 (P27, P33, P36, P37), HOLD delta <= 0 and stub <= 0 (P25, P35, P39; P35 and P39 also Sharpe down), full worst-20 < 0 (S05, S20). NY-PM legs (S5 sweep, FP, PRO1 as pairs with PREOPEN) carry most failures: the NY-PM leg has no stable 2026 stub.

## 3. All 40 pairs (stack-add at 20% risk, locked; sorted by PRE alpha-t, the selection order)
| uid | unit | PRE add $/wk (CI lo) | HOLD add $/wk | HOLD MDE | HOLD t | H2-2025 / 2026 stub | 2023-span add | HOLD corr to stack | HOLD Sharpe stack -> +add | add $ in stack's 20 worst wks (full span) | slip breakeven pts / HOLD $ at +2pt | max lots x | tier (failed gate) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P20 | CRT_M15_M1_close_ib[LONDON] + IF_15s_eb[NY-AM] | 21,375 (15,339) | 21,112 | 11,273 | 5.24 | 21,533 / 15,698 | -9,391 | 0.07 | 0.345 -> 0.474 | 175,722 | 1.5 / -6,742 | 2.4 | PAIR-PASS |
| P08 | IF_30s_eb[ASIA] + IF_15s_eb[NY-AM] | 20,986 (14,949) | 31,769 | 13,189 | 6.74 | 34,198 / 15,544 | -6,457 | 0.10 | 0.345 -> 0.537 | 147,087 | 2.4 / 5,287 | 0.7 | PAIR-PASS |
| P21 | CRT_M15_M1_close[LONDON] + IF_15s_eb[NY-AM] | 18,679 (12,643) | 27,399 | 10,294 | 7.45 | 27,864 / 20,739 | -10,305 | 0.12 | 0.345 -> 0.512 | 99,591 | 1.7 / -5,467 | 1.3 | PAIR-PASS |
| P22 | CRT_M15_M1_close_ib[LONDON] + IF_15s_ea[NY-AM] | 17,578 (11,542) | 15,834 | 11,439 | 3.88 | 13,951 / 21,669 | -12,271 | 0.12 | 0.345 -> 0.436 | 135,410 | 1.2 / -10,724 | 2.2 | PAIR-PASS |
| P28 | IF_30s_eb[PREOPEN] + IF_15s_eb[NY-AM] | 17,517 (11,481) | 25,464 | 11,748 | 6.07 | 26,282 / 17,542 | -5,079 | 0.06 | 0.345 -> 0.503 | 242,551 | 2.9 / 8,040 | 1.7 | PAIR-PASS |
| P36 | IF_15s_eb[NY-AM] + S5_sweep_tf3m_L5[NY-PM] | 16,923 (10,886) | 13,614 | 12,030 | 3.17 | 18,387 / -10,132 | -6,307 | 0.31 | 0.345 -> 0.410 | 166,492 | 2.2 / 1,076 | 1.2 | FAIL (HOLD half<=0) |
| P09 | IF_30s_ea[ASIA] + IF_15s_eb[NY-AM] | 18,854 (12,818) | 28,562 | 16,325 | 4.90 | 31,170 / 12,067 | -4,807 | 0.09 | 0.345 -> 0.512 | 157,492 | 2.1 / 1,714 | 0.8 | PAIR-PASS |
| P29 | IF_3m_eb[PREOPEN] + IF_15s_eb[NY-AM] | 15,482 (9,446) | 21,675 | 14,350 | 4.23 | 22,216 / 15,624 | -1,642 | 0.28 | 0.345 -> 0.457 | 186,474 | 3.1 / 7,625 | 2.4 | PAIR-PASS |
| P16 | CRT_M15_M1_close_ib[LONDON] + IF_30s_eb[PREOPEN] | 16,380 (10,343) | 12,358 | 9,352 | 3.70 | 10,505 / 18,636 | -7,790 | -0.16 | 0.345 -> 0.432 | 205,742 | 1.1 / -9,697 | 2.3 | PAIR-PASS |
| P17 | CRT_M15_M1_close_ib[LONDON] + G2_m30_r3_t12_s1[PREOPEN] | 17,300 (11,263) | 6,965 | 10,165 | 1.92 | 6,280 / 8,888 | -6,690 | -0.34 | 0.345 -> 0.406 | 93,282 | 0.1 / -164,649 | 362.2 | INFEASIBLE-LOTS |
| P00 | IF_30s_eb[ASIA] + CRT_M15_M1_close_ib[LONDON] | 17,746 (11,709) | 16,577 | 10,063 | 4.61 | 16,283 / 15,134 | -8,156 | -0.08 | 0.345 -> 0.455 | 106,295 | 1.2 / -10,840 | 2.0 | PAIR-PASS |
| P24 | CRT_M15_M1_close_ib[LONDON] + PRO1_AGG_CD3_EMA200_VWAP[NY-PM] | 15,035 (8,999) | 4,866 | 10,535 | 1.29 | 203 / 25,038 | -5,625 | -0.18 | 0.345 -> 0.383 | 225,946 | 0.6 / -11,606 | 2.2 | PAIR-CANDIDATE |
| P25 | CRT_M15_M1_close_ib[LONDON] + FP_DDdvx60_cd_5m_N_K60[NY-PM] | 16,730 (10,693) | -232 | 11,505 | -0.06 | -513 / 1,070 | -5,825 | -0.17 | 0.345 -> 0.349 | 165,425 | -0.0 / -18,515 | 2.4 | FAIL (HOLD delta<=0;HOLD half<=0) |
| P01 | IF_15s_eb[ASIA] + CRT_M15_M1_close_ib[LONDON] | 17,088 (11,052) | 19,143 | 10,117 | 5.30 | 17,422 / 23,697 | -6,428 | -0.08 | 0.345 -> 0.472 | 213,088 | 1.3 / -11,337 | 2.1 | PAIR-PASS |
| P37 | IF_15s_ea[NY-AM] + S5_sweep_tf3m_L5[NY-PM] | 14,744 (8,708) | 9,774 | 16,459 | 1.66 | 11,676 / -414 | -10,454 | 0.25 | 0.345 -> 0.380 | 156,582 | 1.5 / -3,570 | 1.2 | FAIL (HOLD half<=0) |
| P10 | IF_30s_eb[ASIA] + E1C_KEL_range_40[NY-AM] | 17,436 (11,399) | 16,112 | 15,184 | 2.97 | 16,072 / 13,608 | -738 | 0.14 | 0.345 -> 0.431 | 84,255 | 1.8 / -2,026 | 0.7 | PAIR-PASS |
| P38 | IF_15s_eb[NY-AM] + PRO1_AGG_CD3_EMA200_VWAP[NY-PM] | 14,402 (8,366) | 14,712 | 9,299 | 4.43 | 13,043 / 19,767 | -2,602 | 0.03 | 0.345 -> 0.437 | 236,323 | 2.8 / 4,221 | 1.2 | PAIR-PASS |
| P30 | IF_30s_eb[PREOPEN] + IF_15s_ea[NY-AM] | 14,760 (8,724) | 21,320 | 14,859 | 4.02 | 19,566 / 25,657 | -8,951 | 0.10 | 0.345 -> 0.468 | 214,773 | 2.4 / 3,368 | 1.7 | PAIR-PASS |
| P23 | CRT_M15_M1_close[LONDON] + IF_15s_ea[NY-AM] | 15,577 (9,541) | 23,494 | 11,776 | 5.59 | 21,641 / 27,916 | -13,882 | 0.17 | 0.345 -> 0.482 | 68,803 | 1.4 / -10,054 | 1.3 | PAIR-PASS |
| P26 | CRT_M15_M1_close[LONDON] + PRO1_AGG_CD3_EMA200_VWAP[NY-PM] | 15,087 (9,050) | 13,126 | 10,309 | 3.57 | 8,044 / 33,809 | -7,713 | -0.14 | 0.345 -> 0.436 | 174,817 | 1.1 / -11,732 | 1.4 | PAIR-PASS |
| P02 | IF_30s_eb[ASIA] + CRT_H1_30s_close[LONDON] | 17,035 (10,999) | 22,641 | 12,451 | 5.09 | 24,709 / 9,557 | -4,057 | 0.05 | 0.345 -> 0.484 | 58,174 | 1.9 / -1,061 | 1.8 | PAIR-PASS |
| P31 | IF_3m_eb[PREOPEN] + IF_15s_ea[NY-AM] | 13,364 (7,327) | 18,220 | 16,628 | 3.07 | 16,373 / 23,493 | -5,281 | 0.29 | 0.345 -> 0.429 | 162,341 | 2.4 / 3,346 | 2.5 | PAIR-PASS |
| P18 | CRT_H1_30s_close[LONDON] + IF_30s_eb[PREOPEN] | 14,910 (8,874) | 19,135 | 10,178 | 5.26 | 20,092 / 11,638 | -2,920 | -0.02 | 0.345 -> 0.468 | 159,093 | 2.3 / 2,598 | 2.1 | PAIR-PASS |
| P19 | CRT_H1_30s_close[LONDON] + IF_3m_ea[PREOPEN] | 14,174 (8,137) | 14,130 | 11,847 | 3.34 | 15,167 / 7,110 | -569 | 0.01 | 0.345 -> 0.432 | 177,997 | 2.2 / 1,200 | 2.0 | PAIR-PASS |
| P12 | IF_15s_eb[ASIA] + S5_sweep_tf3m_L5[NY-PM] | 15,983 (9,947) | 15,157 | 13,338 | 3.18 | 17,591 / 1,680 | -3,900 | 0.16 | 0.345 -> 0.427 | 244,344 | 1.5 / -4,966 | 1.2 | PAIR-PASS |
| P03 | IF_30s_ea[ASIA] + CRT_H1_30s_close[LONDON] | 15,913 (9,877) | 20,462 | 17,649 | 3.25 | 22,966 / 5,785 | -2,423 | 0.03 | 0.345 -> 0.464 | 77,280 | 1.7 / -3,769 | 1.9 | PAIR-PASS |
| P13 | IF_30s_eb[ASIA] + PRO1_IMB_K3_EMA200_VWAP[NY-PM] | 16,797 (10,760) | 16,182 | 11,291 | 4.01 | 16,106 / 13,827 | -4,601 | 0.02 | 0.345 -> 0.446 | 161,760 | 1.9 / -1,237 | 1.6 | PAIR-PASS |
| P11 | CRT_M30_M1_close[ASIA] + IF_15s_ea[NY-AM] | 15,017 (8,980) | 28,549 | 12,914 | 6.19 | 25,598 / 37,073 | -9,127 | 0.28 | 0.345 -> 0.502 | 87,927 | 2.1 / 1,887 | 1.7 | PAIR-PASS |
| P14 | IF_30s_eb[ASIA] + PRO1_AGG_CD3_EMA200_VWAP[NY-PM] | 15,237 (9,200) | 15,134 | 10,769 | 3.93 | 12,128 / 26,138 | -3,058 | -0.14 | 0.345 -> 0.449 | 209,203 | 1.9 / -795 | 1.3 | PAIR-PASS |
| P04 | PB7_PB_HMA55_EMA1_T1_W60_s+3[ASIA] + IF_3m_ea[PREOPEN] | 16,008 (9,971) | 5,418 | 17,842 | 0.85 | 4,843 / 7,103 | -1,340 | 0.34 | 0.345 -> 0.346 | 141,902 | 1.8 / -724 | 2.2 | PAIR-CANDIDATE |
| P05 | IF_30s_eb[ASIA] + IF_3m_ea[PREOPEN] | 15,232 (9,196) | 17,737 | 11,894 | 4.18 | 17,874 / 14,165 | -2,760 | -0.06 | 0.345 -> 0.461 | 194,790 | 2.0 / 425 | 1.8 | PAIR-PASS |
| P27 | CRT_H1_30s_close[LONDON] + S5_sweep_tf3m_L5[NY-PM] | 13,665 (7,629) | 6,840 | 12,997 | 1.47 | 11,659 / -15,986 | -3,756 | 0.22 | 0.345 -> 0.371 | 79,616 | 1.2 / -4,258 | 1.9 | FAIL (HOLD half<=0) |
| P06 | IF_30s_eb[ASIA] + d4a/crt_tt_be_map[PREOPEN] | 15,764 (9,728) | 19,127 | 12,391 | 4.32 | 21,194 / 6,637 | -3,278 | -0.08 | 0.345 -> 0.471 | 203,171 | 2.2 / 1,656 | 2.5 | PAIR-PASS |
| P07 | PB7_PB_HMA55_EMA1_T1_W60_s+3[ASIA] + IF_3m_eb[PREOPEN] | 15,392 (9,355) | 8,497 | 17,779 | 1.34 | 7,338 / 12,294 | -304 | 0.52 | 0.345 -> 0.351 | 73,720 | 2.4 / 1,463 | 3.0 | PAIR-CANDIDATE |
| P39 | d4a/don_tt_cons[NY-AM] + PRO1_AGG_CD3_EMA200_VWAP[NY-PM] | 15,328 (9,292) | -1,255 | 16,875 | -0.21 | -5,350 / 17,380 | 218 | 0.10 | 0.345 -> 0.322 | 119,967 | -0.6 / -5,314 | 1.6 | FAIL (HOLD delta<=0;HOLD half<=0;HOLD Sharpe down) |
| P32 | IF_3m_eb[PREOPEN] + PRO1_AGG_CD3_EMA200_VWAP[NY-PM] | 11,176 (5,139) | 6,946 | 12,302 | 1.58 | 2,057 / 27,792 | 1,548 | 0.12 | 0.345 -> 0.379 | 264,531 | 2.9 / 2,154 | 2.6 | PAIR-CANDIDATE |
| P15 | IF_30s_ea[ASIA] + PRO1_AGG_CD3_EMA200_VWAP[NY-PM] | 14,067 (8,031) | 11,399 | 12,905 | 2.47 | 8,503 / 22,529 | -1,328 | -0.10 | 0.345 -> 0.421 | 227,634 | 1.4 / -4,656 | 1.4 | PAIR-PASS |
| P33 | IF_3m_ea[PREOPEN] + PRO1_AGG_CD3_EMA200_VWAP[NY-PM] | 10,785 (4,748) | 4,138 | 10,944 | 1.06 | -173 / 22,851 | 541 | -0.16 | 0.345 -> 0.377 | 306,028 | 2.3 / 576 | 1.8 | FAIL (HOLD half<=0) |
| P34 | IF_3m_eb[PREOPEN] + PRO1_IMB_K3_EMA200_VWAP[NY-PM] | 12,172 (6,135) | 7,031 | 13,950 | 1.41 | 4,972 / 15,124 | 26 | 0.24 | 0.345 -> 0.369 | 218,961 | 2.8 / 1,998 | 2.8 | PAIR-CANDIDATE |
| P35 | IF_3m_ea[PREOPEN] + FP_DDdvx60_cd_5m_N_K60[NY-PM] | 12,056 (6,020) | -1,103 | 13,764 | -0.22 | -913 / -1,775 | 923 | -0.13 | 0.345 -> 0.341 | 252,617 | -0.5 / -5,307 | 2.0 | FAIL (HOLD delta<=0;HOLD half<=0;HOLD Sharpe down) |

## 4. The 21 single legs as stack-adds (20% risk, locked)
| uid | unit | PRE add $/wk (CI lo) | HOLD add $/wk | HOLD MDE | HOLD t | H2-2025 / 2026 stub | 2023-span add | HOLD corr to stack | HOLD Sharpe stack -> +add | add $ in stack's 20 worst wks (full span) | slip breakeven pts / HOLD $ at +2pt | max lots x | tier (failed gate) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S18 | CRT_M15_M1_close[LONDON] | 12,158 (6,121) | 16,564 | 8,157 | 5.69 | 15,125 / 20,282 | -10,449 | -0.02 | 0.345 -> 0.453 | 5,016 | 1.0 / -15,088 | 1.8 | PAIR-PASS |
| S02 | IF_15s_eb[ASIA] | 12,609 (6,572) | 23,435 | 11,722 | 5.60 | 22,356 / 24,384 | -1,173 | -0.02 | 0.345 -> 0.495 | 224,698 | 2.0 / -376 | 0.9 | PAIR-PASS |
| S09 | IF_15s_eb[NY-AM] | 14,234 (8,197) | 21,992 | 11,592 | 5.31 | 24,088 / 8,894 | -4,158 | 0.17 | 0.345 -> 0.472 | 131,375 | 3.0 / 7,408 | 0.8 | PAIR-PASS |
| S11 | CRT_M30_M1_close[ASIA] | 10,348 (4,312) | 23,204 | 14,281 | 4.55 | 20,142 / 33,114 | -3,768 | 0.16 | 0.345 -> 0.476 | 30,984 | 2.1 / 1,130 | 2.3 | PAIR-CANDIDATE |
| S00 | IF_30s_eb[ASIA] | 13,549 (7,513) | 20,063 | 12,657 | 4.44 | 21,164 / 11,764 | -4,455 | -0.02 | 0.345 -> 0.472 | 63,870 | 1.9 / -660 | 0.9 | PAIR-PASS |
| S16 | IF_30s_eb[PREOPEN] | 8,343 (2,307) | 10,887 | 8,605 | 3.54 | 9,847 / 13,752 | -2,400 | -0.13 | 0.345 -> 0.421 | 181,767 | 2.8 / 2,973 | 2.2 | PAIR-CANDIDATE |
| S03 | CRT_H1_30s_close[LONDON] | 10,400 (4,363) | 13,167 | 11,684 | 3.16 | 15,410 / 878 | -1,270 | 0.08 | 0.345 -> 0.422 | 18,225 | 2.0 / 292 | 2.6 | PAIR-CANDIDATE |
| S12 | IF_15s_ea[NY-AM] | 10,625 (4,589) | 16,265 | 15,279 | 2.98 | 15,117 / 18,716 | -9,047 | 0.19 | 0.345 -> 0.427 | 88,820 | 2.2 / 1,179 | 0.9 | PAIR-CANDIDATE |
| S04 | IF_30s_ea[ASIA] | 11,481 (5,445) | 14,823 | 16,566 | 2.51 | 16,139 / 6,428 | -2,061 | -0.00 | 0.345 -> 0.433 | 85,817 | 1.4 / -5,945 | 1.0 | PAIR-CANDIDATE |
| S01 | CRT_M15_M1_close_ib[LONDON] | 14,397 (8,361) | 6,270 | 8,645 | 2.03 | 4,737 / 12,121 | -8,415 | -0.11 | 0.345 -> 0.389 | 103,868 | 0.6 / -16,435 | 3.2 | PAIR-PASS |
| S08 | IF_3m_eb[PREOPEN] | 7,577 (1,540) | 8,542 | 12,043 | 1.99 | 7,209 / 13,117 | 1,844 | 0.30 | 0.345 -> 0.379 | 131,322 | 3.3 / 3,335 | 3.4 | PAIR-CANDIDATE |
| S06 | IF_3m_ea[PREOPEN] | 7,921 (1,884) | 5,098 | 11,919 | 1.20 | 4,195 / 8,313 | 534 | -0.06 | 0.345 -> 0.378 | 211,852 | 2.7 / 1,259 | 2.6 | PAIR-CANDIDATE |
| S07 | d4a/crt_tt_be_map[PREOPEN] | 6,721 (685) | 4,531 | 13,451 | 0.94 | 6,088 / -3,229 | 239 | -0.08 | 0.345 -> 0.374 | 197,381 | 5.2 / 2,789 | 3.2 | FAIL (HOLD half<=0) |
| S17 | G2_m30_r3_t12_s1[PREOPEN] | 7,799 (1,763) | 2,667 | 8,635 | 0.86 | 3,320 / -717 | -169 | -0.40 | 0.345 -> 0.378 | 15,816 | 0.0 / -194,817 | 464.7 | FAIL (HOLD half<=0) |
| S10 | E1C_KEL_range_40[NY-AM] | 9,035 (2,999) | 2,421 | 14,366 | 0.47 | 577 / 10,315 | 3,111 | 0.13 | 0.345 -> 0.347 | 42,184 | 1.2 / -1,488 | 0.6 | PAIR-CANDIDATE |
| S15 | PRO1_AGG_CD3_EMA200_VWAP[NY-PM] | 7,459 (1,423) | 804 | 11,256 | 0.20 | -4,442 / 24,275 | 238 | -0.15 | 0.345 -> 0.355 | 224,581 | 1.3 / -437 | 1.8 | FAIL (HOLD half<=0) |
| S05 | PB7_PB_HMA55_EMA1_T1_W60_s+3[ASIA] | 11,788 (5,752) | 1,014 | 14,850 | 0.19 | 1,219 / -77 | -2,031 | 0.55 | 0.345 -> 0.314 | -56,098 | 0.6 / -2,609 | 0.9 | FAIL (HOLD half<=0;HOLD Sharpe down;full worst20<0) |
| S14 | PRO1_IMB_K3_EMA200_VWAP[NY-PM] | 7,374 (1,338) | 95 | 11,048 | 0.02 | -1,101 / 5,460 | -1,813 | 0.05 | 0.345 -> 0.340 | 137,629 | 0.2 / -881 | 2.0 | FAIL (HOLD half<=0;HOLD Sharpe down) |
| S20 | d4a/don_tt_cons[NY-AM] | 10,455 (4,419) | -861 | 14,991 | -0.16 | -127 / -4,021 | -489 | 0.17 | 0.345 -> 0.323 | -44,351 | -0.5 / -4,535 | 1.1 | FAIL (HOLD delta<=0;HOLD half<=0;HOLD Sharpe down;full worst20<0) |
| S13 | S5_sweep_tf3m_L5[NY-PM] | 7,854 (1,818) | -4,029 | 11,301 | -1.00 | 165 / -22,233 | -3,747 | 0.26 | 0.345 -> 0.304 | 88,130 | -4.1 / -5,981 | 1.5 | FAIL (HOLD delta<=0;HOLD half<=0;HOLD Sharpe down) |
| S19 | FP_DDdvx60_cd_5m_N_K60[NY-PM] | 7,692 (1,655) | -6,527 | 11,934 | -1.53 | -5,377 / -10,612 | 660 | -0.14 | 0.345 -> 0.305 | 115,278 | -8.1 / -8,131 | 2.0 | FAIL (HOLD delta<=0;HOLD half<=0;HOLD Sharpe down) |

## 5. By session-pair (4 pairs each)
| session pair | pairs | PAIR-PASS | CANDIDATE | FAIL/INFEAS | best pair by HOLD t | its HOLD add $/wk (MDE) | median HOLD add | median 2023-span add |
|---|---|---|---|---|---|---|---|---|
| ASIA+LONDON | 4 | 4 | 0 | 0 | P01 IF_15s_eb[ASIA] + CRT_M15_M1_close_ib[LONDON] | 19,143 (10,117) | 19,803 | -5,242 |
| ASIA+PREOPEN | 4 | 2 | 2 | 0 | P06 IF_30s_eb[ASIA] + d4a/crt_tt_be_map[PREOPEN] | 19,127 (12,391) | 13,117 | -2,050 |
| ASIA+NY-AM | 4 | 4 | 0 | 0 | P08 IF_30s_eb[ASIA] + IF_15s_eb[NY-AM] | 31,769 (13,189) | 28,556 | -5,632 |
| ASIA+NY-PM | 4 | 4 | 0 | 0 | P13 IF_30s_eb[ASIA] + PRO1_IMB_K3_EMA200_VWAP[NY-PM] | 16,182 (11,291) | 15,146 | -3,479 |
| LONDON+PREOPEN | 4 | 3 | 0 | 1 | P18 CRT_H1_30s_close[LONDON] + IF_30s_eb[PREOPEN] | 19,135 (10,178) | 13,244 | -4,805 |
| LONDON+NY-AM | 4 | 4 | 0 | 0 | P21 CRT_M15_M1_close[LONDON] + IF_15s_eb[NY-AM] | 27,399 (10,294) | 22,303 | -11,288 |
| LONDON+NY-PM | 4 | 1 | 1 | 2 | P26 CRT_M15_M1_close[LONDON] + PRO1_AGG_CD3_EMA200_VWAP[NY-PM] | 13,126 (10,309) | 5,853 | -5,725 |
| PREOPEN+NY-AM | 4 | 4 | 0 | 0 | P28 IF_30s_eb[PREOPEN] + IF_15s_eb[NY-AM] | 25,464 (11,748) | 21,497 | -5,180 |
| PREOPEN+NY-PM | 4 | 0 | 2 | 2 | P32 IF_3m_eb[PREOPEN] + PRO1_AGG_CD3_EMA200_VWAP[NY-PM] | 6,946 (12,302) | 5,542 | 732 |
| NY-AM+NY-PM | 4 | 1 | 0 | 3 | P38 IF_15s_eb[NY-AM] + PRO1_AGG_CD3_EMA200_VWAP[NY-PM] | 14,712 (9,299) | 11,694 | -4,455 |

## 6. Stack-add at 10/20/30% risk, top 6 pairs by PRE alpha-t (locked)
| uid | risk | lots x per leg | HOLD add $/wk | HOLD MDE | HOLD Sharpe stack -> +add | HOLD weekly SD stack -> +add | HOLD maxDD stack -> +add | add in HOLD worst-20 wks | stack HOLD worst-20 $ -> +add | 2023-span add $/wk | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P20 | 10% | [1.1817925859870915, 0.2918927011408682] | 10,556 | 5,636 | 0.345 -> 0.412 | 151,891 -> 153,079 | -578,442 -> -565,251 | 198,977 | -742,938 -> -543,961 | -4,696 | PAIR-PASS |
| P20 | 20% | [2.363585171974183, 0.5837854022817364] | 21,112 | 11,273 | 0.345 -> 0.474 | 151,891 -> 155,095 | -578,442 -> -552,060 | 397,953 | -742,938 -> -344,984 | -9,391 | PAIR-PASS |
| P20 | 30% | [3.5453777579612735, 0.8756781034226043] | 31,668 | 16,909 | 0.345 -> 0.533 | 151,891 -> 157,909 | -578,442 -> -538,869 | 596,930 | -742,938 -> -146,008 | -14,087 | PAIR-PASS |
| P08 | 10% | [0.3529911925242984, 0.2948540253669081] | 15,885 | 6,594 | 0.345 -> 0.444 | 151,891 -> 153,743 | -578,442 -> -556,845 | 290,405 | -742,938 -> -452,533 | -3,229 | PAIR-PASS |
| P08 | 20% | [0.7059823850485968, 0.5897080507338162] | 31,769 | 13,189 | 0.345 -> 0.537 | 151,891 -> 156,709 | -578,442 -> -535,248 | 580,810 | -742,938 -> -162,128 | -6,457 | PAIR-PASS |
| P08 | 30% | [1.058973577572895, 0.884562076100724] | 47,654 | 19,783 | 0.345 -> 0.623 | 151,891 -> 160,728 | -578,442 -> -513,651 | 871,215 | -742,938 -> 128,277 | -9,686 | PAIR-PASS |
| P21 | 10% | [0.6434988358868284, 0.2775320610678049] | 13,699 | 5,147 | 0.345 -> 0.431 | 151,891 -> 153,538 | -578,442 -> -552,360 | 250,362 | -742,938 -> -492,576 | -5,152 | PAIR-PASS |
| P21 | 20% | [1.2869976717736569, 0.5550641221356098] | 27,399 | 10,294 | 0.345 -> 0.512 | 151,891 -> 155,862 | -578,442 -> -526,279 | 500,724 | -742,938 -> -242,213 | -10,305 | PAIR-PASS |
| P21 | 30% | [1.9304965076604845, 0.8325961832034144] | 41,098 | 15,441 | 0.345 -> 0.589 | 151,891 -> 158,835 | -578,442 -> -500,197 | 751,086 | -742,938 -> 8,149 | -15,457 | PAIR-PASS |
| P22 | 10% | [1.1121190649405144, 0.3131151131454045] | 7,917 | 5,720 | 0.345 -> 0.393 | 151,891 -> 153,751 | -578,442 -> -562,878 | 158,179 | -742,938 -> -584,758 | -6,135 | PAIR-PASS |
| P22 | 20% | [2.2242381298810288, 0.626230226290809] | 15,834 | 11,439 | 0.345 -> 0.436 | 151,891 -> 156,444 | -578,442 -> -547,313 | 316,359 | -742,938 -> -426,579 | -12,271 | PAIR-PASS |
| P22 | 30% | [3.3363571948215425, 0.9393453394362136] | 23,751 | 17,159 | 0.345 -> 0.476 | 151,891 -> 159,928 | -578,442 -> -531,748 | 474,538 | -742,938 -> -268,399 | -18,406 | PAIR-PASS |
| P28 | 10% | [0.8341502976088516, 0.30257026427520156] | 12,732 | 5,874 | 0.345 -> 0.426 | 151,891 -> 153,011 | -578,442 -> -553,311 | 264,336 | -742,938 -> -478,602 | -2,539 | PAIR-PASS |
| P28 | 20% | [1.6683005952177032, 0.6051405285504031] | 25,464 | 11,748 | 0.345 -> 0.503 | 151,891 -> 155,033 | -578,442 -> -528,180 | 528,672 | -742,938 -> -214,266 | -5,079 | PAIR-PASS |
| P28 | 30% | [2.5024508928265545, 0.9077107928256046] | 38,196 | 17,622 | 0.345 -> 0.574 | 151,891 -> 157,924 | -578,442 -> -503,049 | 793,008 | -742,938 -> 50,070 | -7,618 | PAIR-PASS |
| P36 | 10% | [0.2962295646736499, 0.5866918480678667] | 6,807 | 6,015 | 0.345 -> 0.380 | 151,891 -> 156,050 | -578,442 -> -568,266 | 78,475 | -742,938 -> -664,462 | -3,154 | FAIL |
| P36 | 20% | [0.5924591293472998, 1.1733836961357333] | 13,614 | 12,030 | 0.345 -> 0.410 | 151,891 -> 161,021 | -578,442 -> -558,090 | 156,950 | -742,938 -> -585,987 | -6,307 | FAIL |
| P36 | 30% | [0.8886886940209496, 1.7600755442036] | 20,422 | 18,045 | 0.345 -> 0.437 | 151,891 -> 166,731 | -578,442 -> -547,914 | 235,426 | -742,938 -> -507,512 | -9,461 | FAIL |

## 7. Worst-20 weeks and trade-off line (20% risk, locked, top 6 by PRE alpha-t)
Stack 20 worst weeks fixed on the full 2023-04-03..2026-02-06 span; PRE-derived worst 20 on PRE only. 'Given up in good weeks' = add $ in the stack's 20 best weeks when negative; here the add is a positive earner in both.
| uid | stack worst-20 $ (full) | add $ in them | add $ in stack's best 20 | PRE-derived worst-20: add $ |
|---|---|---|---|---|
| P20 | -3,534,170 | 175,722 | 287,533 | 486,137 |
| P08 | -3,534,170 | 147,087 | 410,617 | 287,180 |
| P21 | -3,534,170 | 99,591 | 274,061 | 316,586 |
| P22 | -3,534,170 | 135,410 | 218,973 | 412,981 |
| P28 | -3,534,170 | 242,551 | 275,111 | 307,524 |
| P36 | -3,534,170 | 166,492 | 123,511 | 338,798 |

## 8. By calendar year (add $ per week, 20% risk, locked; weekly sums over ISO-year of the week; 2023 = Apr-Dec span, 2026 = Jan 1-Feb 6)
| uid | 2023 | 2024 | 2025 | 2026 stub | stack $/wk 2023 | 2024 | 2025 | 2026 |
|---|---|---|---|---|---|---|---|---|
| P20 | -11,173 | 12,578 | 29,367 | 20,027 | 15,127 | 41,494 | 54,297 | 53,978 |
| P08 | -7,751 | 12,191 | 35,476 | 21,668 | 15,127 | 41,494 | 54,297 | 53,978 |
| P21 | -12,614 | 9,544 | 31,960 | 26,339 | 15,127 | 41,494 | 54,297 | 53,978 |
| P22 | -13,559 | 9,742 | 22,305 | 24,581 | 15,127 | 41,494 | 54,297 | 53,978 |
| P28 | -5,996 | 13,560 | 24,073 | 30,360 | 15,127 | 41,494 | 54,297 | 53,978 |
| P36 | -8,615 | 13,518 | 20,789 | -3,434 | 15,127 | 41,494 | 54,297 | 53,978 |

## 9. Cost stress (stored-fill fragility), HOLD, 20% risk
Extra per-trade cost in NQ points on top of the source's stored cost (1 pt = $200 at 10 lots, scaled by each leg's lots multiple). 'breakeven' = extra pts per trade at which the HOLD add goes to 0. Per-leg HOLD trades/wk and mean $/trade on the stored basis.
| uid | unit | legs trades/wk | legs mean $/trade | HOLD add | +1 pt | +2 pt | +4 pt | breakeven pts |
|---|---|---|---|---|---|---|---|---|
| P20 | CRT_M15_M1_close_ib[LONDON] + IF_15s_eb[NY-AM] | [17.9, 46.7] | [110.0, 603.0] | 21,112 | 7,185 | -6,742 | -34,595 | 1.5 |
| P08 | IF_30s_eb[ASIA] + IF_15s_eb[NY-AM] | [55.1, 46.3] | [387.0, 612.0] | 31,769 | 18,528 | 5,287 | -21,196 | 2.4 |
| P21 | CRT_M15_M1_close[LONDON] + IF_15s_eb[NY-AM] | [43.7, 46.7] | [209.0, 603.0] | 27,399 | 10,966 | -5,467 | -38,332 | 1.7 |
| P22 | CRT_M15_M1_close_ib[LONDON] + IF_15s_ea[NY-AM] | [17.9, 42.3] | [110.0, 431.0] | 15,834 | 2,555 | -10,724 | -37,282 | 1.2 |
| P28 | IF_30s_eb[PREOPEN] + IF_15s_eb[NY-AM] | [9.2, 46.7] | [550.0, 603.0] | 25,464 | 16,752 | 8,040 | -9,385 | 2.9 |
| P36 | IF_15s_eb[NY-AM] + S5_sweep_tf3m_L5[NY-PM] | [46.7, 3.2] | [603.0, -826.0] | 13,614 | 7,345 | 1,076 | -11,462 | 2.2 |
| P08 | IF_30s_eb[ASIA] + IF_15s_eb[NY-AM] | [55.1, 46.3] | [387.0, 612.0] | 31,769 | 18,528 | 5,287 | -21,196 | 2.4 |
| P28 | IF_30s_eb[PREOPEN] + IF_15s_eb[NY-AM] | [9.2, 46.7] | [550.0, 603.0] | 25,464 | 16,752 | 8,040 | -9,385 | 2.9 |

## 9b. Cost-robust passing pairs (HOLD still positive with +2 pt extra per trade): P05, P06, P08, P09, P11, P18, P19, P28, P29, P30, P31, P38 (12 of 27 passing pairs). The best by HOLD at +2 pt: P28 (+8.0k/wk), P29 (+7.6k), P08 (+5.3k), P38 (+4.2k).

## 10. Specs for anything that passed (item 4): existing spec + session window ET + flat rule + one paragraph
Common to all: entries only inside the leg's window (ET entry time: ASIA 18:00-02:00, LONDON 02:00-08:30, PREOPEN 08:30-09:30, NY-AM 09:30-12:00, NY-PM 12:00-15:00); no new entries outside it; an open position runs to the cell's own bracket exit exactly as in its source table (the engine cell spec) and the platform flat time of 16:54 ET applies (the stored rows' maximum hold was not verified from the rows, so a flat at 16:54 ET is the assumption); book-level day lock: no new entry in a label day once the earlier entries of the pair that day sum to >= +5R or <= -2R (R=12,000 at 10 lots); size at 20% SD-parity risk = the lots multiples shown, CANDIDATE sizing is half of those until the CONS re-run. Cell specs live in the source tables: IF_* = ICT-IC ifvg blocks (ds3/out/IC/trades_IF_*.parquet; DS3_TICT.md: limit at the midpoint of the gap/OB, stop beyond the far edge +5 ticks, target nearest liquidity >=1R else 2R, MAPPED basis); CRT_* = ICT-SF CRT cells (ds3/out/SF/trades_CRT_*.parquet, MAPPED); PRO1_* = T-PRO1 (ds3/out/PRO1, mapped).

- P08, ASIA + NY-AM (IF_30s_eb 18:00-02:00 ET, 0.71x of 10 lots; IF_15s_eb 09:30-12:00 ET, 0.59x): two instances of the same fair-value-gap limit-entry rule, the 30-second version trading only the overnight session and the 15-second version trading only the morning. Flat rule: no entry outside those windows, brackets as stored, day lock as above. In plain English: take the overnight gap entries of the 30 s rule and the morning gap entries of the 15 s rule as one book; it earned about 32k/wk on top of the stack in HOLD (MDE 13k, t 6.7), made money in both HOLD halves and in the stack's worst weeks, but lost about 6k/wk in the 2023 span and breaks even at +2.4 pts of extra cost per trade.
- P28, PREOPEN + NY-AM (IF_30s_eb 08:30-09:30 ET, 1.67x; IF_15s_eb 09:30-12:00 ET, 0.61x): the same family around the open. HOLD +25k/wk (MDE 12k, t 6.1), +8.0k/wk after +2 pts extra cost per trade (the most cost-robust pair), -5k/wk in 2023; breakeven 2.9 pts.
- P02, ASIA + LONDON (IF_30s_eb 18:00-02:00 ET, 0.67x; CRT_H1_30s_close 02:00-08:30 ET, 1.83x): an overnight-only book (nothing after 08:30 ET), HOLD +23k/wk (MDE 12k, t 5.1), +9.6k stub, -4k in 2023; breakeven 1.9 pts, negative at +2 pts.
- P38, NY-AM + NY-PM (IF_15s_eb 09:30-12:00 ET, 0.52x; PRO1_AGG_CD3_EMA200_VWAP 12:00-15:00 ET, 1.22x): the day-session book and the only passing pair with a non-ICT leg, HOLD +14.7k/wk (MDE 9.3k, t 4.4), +4.2k at +2 pts, -2.6k in 2023.
- All other PAIR-PASS pairs are listed in section 3 with their windows in the unit name; their spec = the same text with the cell names and windows of that row and the multiples in tiers_all.csv/metrics_hold.csv (lots_mult).

## 11. Per session-pair MDE note
HOLD MDE of the add is 9-17k/wk at 20% risk for pairs (singles 8-15k): an add below about 10-14k/wk is not distinguishable from 0 in HOLD; PRE MDE is 8.5k/wk. All PASS pairs clear their HOLD MDE except P15.
