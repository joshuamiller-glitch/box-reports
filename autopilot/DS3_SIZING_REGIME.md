# DS3_SIZING_REGIME - item F: sizing by regime (D3SZR, 2026-10-28). Research only; nothing goes live from this file (a sizing rule is live-eligible once scored).
Prereg `l2vast/ds3/prereg/D3SZR_prereg.md` sha256 079310bec8c20bcce9bf320cd85d1d5291dfa5d26d896c1271a4d44904c817d4 (DECISIONS.md), 24 cells, frozen before scoring; ONE holdout look logged (track DS3_SZR; pre-holdout text `autopilot/DS3_SIZING_REGIME_PREHOLD.md` selected the rule before HOLD was read). Code `l2vast/ds3/code/sz/` (sz_lib, sz_run, sz_report, sz_extra); outputs `l2vast/ds3/out/sz/` (pre_results.json, final_results.json, gates.json).

## Verdict line
**Best-supported sizing rule for live: week-constant vol-scaled lots on the DS2+KB10+SM10 stack (per book, lots x clip(median-so-far of the book's own trailing daily-P&L SD / current trailing SD, 0.5..2); 4-week lookback = the PRE-selected rule B1_STACK; the 8-week B2_STACK is the steadier sibling). Tier: NOT CONFIRMED and NOT LEAD under the prereg (fails G3 on HOLD: lot-matched maxDD and worst week got worse). It is the only family that is distinguishable from shifted-label placebos in both PRE and HOLD.** Lot-matched weekly deltas vs the unscaled stack (HOLD 2025-07..2026-10, 68 wk; PRE 2024-02..2025-06 in brackets): B1 mean +6,406 [+3,651] (CI +1,234..+12,004, MDE 7,804, placebo rank 0.99 [1.00]), SD +13,208 [-916], maxDD +113,459 [-112,797], worst week -48,335 [+165]; B2 (8-wk) mean +5,992 [+2,308] (CI +2,292..+9,812, MDE 5,477, boot p 0.001 which clears Bonferroni 0.05/24=0.0021; placebo 1.00 [0.99]), SD +8,899 [-2,122], maxDD +67,935 [-54,753], worst -19,080 [+13,519]. Read honestly: because lots are matched, B1/B2 run ~12% more lots in calm weeks; the same rule UNMATCHED (average lots x0.88-0.89) keeps the stack's weekly mean (HOLD d mean +173 / -508) with lower SD (-5.6k / -10.4k) and mixed drawdown (maxDD +36k / -8k; PRE -166k / -117k), i.e. its practical value is a risk trim at equal mean, not extra edge. The compression forecaster, VIX-tercile and day-of-week rules are DEAD (below). **Nothing is sizing-fixable about 2023: no rule cuts the 2023-04..2024-01 loss.**

## Baselines (unscaled, weekly $; maxDD on the daily path)
| target | window | weeks | mean | SD | maxDD | worst week |
|---|---|---|---|---|---|---|
| STACK | WFPRE | 75 | 52,717 | 134,927 | 591,503 | -232,119 |
| STACK | HOLD | 68 | 50,044 | 157,093 | 582,743 | -275,336 |
| STACK | WF | 142 | 51,808 | 145,962 | 591,503 | -275,336 |
| STACK | SPAN2 | 44 | 20,989 | 108,510 | 373,096 | -196,770 |
| DS5 | WFPRE | 75 | 42,973 | 91,366 | 254,477 | -165,116 |
| DS5 | HOLD | 68 | 50,210 | 99,685 | 369,759 | -173,403 |
| DS5 | WF | 142 | 46,741 | 95,173 | 369,759 | -173,403 |
| DS5 | SPAN2 | 44 | 9,373 | 73,604 | 263,061 | -173,810 |
STACK = ST10 HM10 WT7 + KB10 SM10 (51.8k/wk WF here vs 48.6k for the D3SL stack: no PB book, WT7, per-book locks only). DS5 = KB5 DN8 SM7 PE5 MV4 (DN is MAPPED basis, MV hybrid).

## All 24 cells, sorted by PRE placebo rank (top 10 = first ten rows). Lot-matched deltas (weekly $), paired by week vs the unscaled base; placebo = 150 shifted-label draws; MDE = 2.8 SD_diff/sqrt(n) next to every estimate
Gates (prereg, none softened): G1 delta>0 in PRE and HOLD; G2 HOLD CI(iid) low>0; G3 maxDD and worst week not worse in PRE and HOLD; G4 placebo rank >=0.95 in PRE and HOLD; G5 >=2 of 3 years positive and no year >60%. CONFIRMED = all; LEAD = G1+G3+PRE placebo; best-of-F = min HOLD p < 0.05/24. Result: **0 CONFIRMED, 0 LEAD, 24 DEAD**; best-of-F cleared by B2_STACK and E2_POOL (p 0.001) only. Year columns are summed weekly deltas.

| cell | tier | gates failed | PRE d_mean (rank) | HOLD d_mean [CI iid] (rank) | HOLD d_SD | HOLD d_maxDD | HOLD d_worst | HOLD raw d_mean | MDE HOLD | p(boot<=0) | WF by-year delta 2024/25/26 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| B1_STACK | DEAD | G3 | 3,651 (1.00) | 6,406 [1,234,12,004] (0.99) | 13,208 | 113,459 | -48,335 | 173 | 7,804 | 0.008 | 302,424/246,297/160,782 |
| B2_STACK | DEAD | G3 | 2,308 (0.99) | 5,992 [2,292,9,812] (1.00) | 8,899 | 67,935 | -19,080 | -508 | 5,477 | 0.001 | 151,290/310,422/118,870 |
| B1_DS5 | DEAD | G3,G4 | 2,304 (0.99) | 4,948 [814,9,082] (0.91) | 9,231 | 76,108 | -39,356 | -1,758 | 5,974 | 0.010 | 159,493/253,914/95,857 |
| E2_POOL | DEAD | G3 | 4,261 (0.99) | 14,828 [5,781,24,088] (1.00) | 28,843 | 90,696 | -37,112 | -4,848 | 13,301 | 0.001 | 188,880/522,674/616,342 |
| B2_DS5 | DEAD | G3,G4,G5 | 1,238 (0.95) | 4,690 [1,707,7,705] (0.95) | 6,724 | 27,060 | -5,417 | -2,327 | 4,365 | 0.001 | 86,400/260,649/64,714 |
| E1_POOL | DEAD | G2,G3,G4,G5 | 10,875 (0.93) | 10,203 [-6,093,25,736] (0.82) | 39,853 | 312,973 | -138,870 | -13,209 | 22,805 | 0.108 | 965,449/-140,845/684,817 |
| A1_STACK | DEAD | G2,G3,G4,G5 | 2,153 (0.71) | 5,359 [-4,382,15,127] (0.88) | 23,525 | 134,876 | -60,417 | -4,611 | 13,937 | 0.140 | 360,022/-21,871/187,698 |
| A2_STACK | DEAD | G2,G3,G4,G5 | 4,013 (0.69) | 11,545 [-13,333,36,562] (0.88) | 70,313 | 350,534 | -156,598 | -9,222 | 35,659 | 0.181 | 851,182/-147,121/381,982 |
| E4_POOL | DEAD | G2,G3,G4,G5 | 3,025 (0.67) | 10,139 [-5,938,23,638] (0.87) | 20,157 | 137,205 | -28,756 | -5,758 | 21,155 | 0.093 | -66,093/414,831/567,618 |
| A1_DS5 | DEAD | G3,G4,G5 | 1,235 (0.66) | 6,943 [768,13,124] (0.98) | 14,083 | 94,943 | -38,050 | -3,342 | 8,891 | 0.015 | 199,939/8,224/356,580 |
| A2_DS5 | DEAD | G3,G4,G5 | 3,165 (0.66) | 17,789 [1,967,33,627] (0.99) | 43,088 | 243,265 | -97,492 | -6,683 | 22,782 | 0.015 | 512,291/21,073/913,639 |
| A5_DS5 | DEAD | G3,G4,G5 | 2,276 (0.60) | 19,518 [2,148,37,400] (0.99) | 46,536 | 275,384 | -52,021 | 3,612 | 25,166 | 0.014 | 601,188/-80,431/977,172 |
| A5_STACK | DEAD | G2,G3,G4,G5 | 1,165 (0.59) | 10,415 [-16,380,37,746] (0.87) | 74,615 | 547,447 | -179,354 | -790 | 39,042 | 0.230 | 850,851/-174,577/119,317 |
| A4_STACK | DEAD | G2,G3,G4,G5 | 564 (0.57) | 6,188 [-8,329,21,161] (0.87) | 32,734 | 184,080 | -88,137 | 3,821 | 21,311 | 0.208 | 443,405/-20,430/40,136 |
| E3_POOL | DEAD | G3,G4,G5 | 609 (0.56) | 21,004 [1,301,40,414] (0.93) | 65,554 | 405,578 | -181,138 | -10,351 | 28,187 | 0.019 | 257,585/24,985/1,191,346 |
| A4_DS5 | DEAD | G3,G4,G5 | 900 (0.55) | 10,014 [546,19,846] (0.97) | 20,305 | 140,845 | -9,285 | 6,954 | 13,745 | 0.019 | 319,663/-63,625/492,467 |
| C2_STACK | DEAD | G1,G2,G3,G4 | -456 (0.49) | 14,706 [-3,523,32,934] (0.93) | 58,021 | 356,885 | -149,977 | 9,710 | 26,480 | 0.056 | 269,548/223,841/472,420 |
| C1_STACK | DEAD | G1,G3,G4,G5 | -538 (0.47) | 11,361 [110,22,576] (0.97) | 36,958 | 166,792 | -78,807 | -2,303 | 16,332 | 0.025 | 75,516/167,538/489,117 |
| A3_DS5 | DEAD | G1,G2,G3,G4,G5 | -140 (0.47) | 3,376 [-1,734,8,699] (0.95) | 5,715 | 49,444 | 19,829 | 10,295 | 7,480 | 0.101 | 123,508/-59,458/155,009 |
| A3_STACK | DEAD | G1,G2,G3,G4,G5 | -483 (0.46) | 2,285 [-5,776,10,606] (0.79) | 8,952 | 55,141 | -28,154 | 8,432 | 11,725 | 0.290 | 137,879/40,598/-59,280 |
| D1_DS5 | DEAD | G1,G2,G3,G4,G5 | 1,774 (0.17) | -1,709 [-7,443,3,955] (0.23) | 724 | -9,998 | 7,038 | -6,572 | 8,271 | 0.716 | 114,142/85,015/-182,271 |
| C1_DS5 | DEAD | G1,G3,G4,G5 | -2,647 (0.16) | 9,506 [1,948,17,142] (0.96) | 25,982 | 105,832 | -49,631 | -3,782 | 10,927 | 0.007 | -16,761/-14,417/479,077 |
| D1_STACK | DEAD | G1,G2,G3,G4,G5 | 3,267 (0.15) | -4,183 [-13,763,5,172] (0.24) | -885 | 63,855 | 2,020 | -8,782 | 13,812 | 0.801 | 221,000/130,481/-390,947 |
| C2_DS5 | DEAD | G1,G3,G4,G5 | -4,985 (0.14) | 14,681 [1,457,28,128] (0.97) | 45,964 | 213,485 | -84,961 | 8,620 | 19,277 | 0.013 | -49,797/43,134/631,109 |

(A = compression multiplier: A1 quiet 0.5 | A2 quiet 0 | A3 wide 1.5 | A4 quiet 0.5 + wide 1.5 | A5 quiet 0 + wide 1.5; B1/B2 vol-scaled 4/8 wk; C1 VIX high tercile 0.5; C2 low 1.5 + high 0.5; D1 halve PRE-worst weekday; E1-E4 = pooled 2023-failers MV+PE+KB20_S+3 DON widenings.)

## What each family says
- (a) Compression forecaster as lot multiplier (A1-A5): PRE matched deltas are small and statistically unlike a shifted-label draw (placebo rank 0.46-0.71 STACK, 0.47-0.66 DS5 in PRE); HOLD ranks 0.79-0.99 look better for DS5 (A1 0.98, A2/A5 0.99) but every A cell INCREASES HOLD maxDD lot-matched and all but A3_DS5 worsen the worst week (e.g. A2_STACK maxDD +350k, worst -157k), and PRE ranks (0.46-0.71) do not support the better HOLD ranks, so the HOLD gain reads as leverage in a good period rather than a regime effect. This agrees with the prior art (TR4 R5_QUIET gate cells DEAD). Zeroing quiet days (A2/A5) is the worst for tail risk. Wide x1.5 alone (A3) is negative in PRE.
- (b) Vol-scaled lots: the only consistent family (placebo >=0.95 in both windows for STACK; DS5 B1/B2 PRE 0.99/0.95 but HOLD 0.91/0.95, and DS5 fails G3). The effect is the volatility-clustering of the books' own P&L: shrink after a noisy month, grow after a calm one.
- (c) VIX tercile lots: PRE delta negative on both targets; HOLD positive (C1_DS5 +9.5k, CI +1.9k..+17.1k) but placebo rank in PRE 0.16, so not a regime effect we can trust.
- (d) Day-of-week: the weekday chosen on PRE (halve the worst mean day) does not hold: PRE placebo rank 0.15-0.17 (selection-aware re-selection on shifted labels) and HOLD delta -4.2k / -1.7k. DEAD.

## Raw (not lot-matched) risk view of the vol-scaled cells (post-hoc reading of the same runs, not a gate)
| cell | window | base mean/SD/maxDD/worst | rule RAW (lots multiplier) | d mean | d SD | d maxDD | d worst |
|---|---|---|---|---|---|---|---|
| B1_STACK | WFPRE | 52,717/134,927/591,503/-232,119 | 50,158/119,207/425,707/-206,293 (lots x0.89) | -2,559 | -15,720 | -165,795 | 25,826 |
| B1_STACK | HOLD | 50,044/157,093/582,743/-275,336 | 50,217/151,468/619,180/-287,863 (lots x0.89) | 173 | -5,625 | 36,437 | -12,527 |
| B1_STACK | SPAN2 | 20,989/108,510/373,096/-196,770 | 22,013/109,509/353,128/-196,770 (lots x0.89) | 1,024 | 998 | -19,968 | 0 |
| B2_STACK | WFPRE | 52,717/134,927/591,503/-232,119 | 48,640/117,395/474,468/-193,234 (lots x0.88) | -4,077 | -17,532 | -117,035 | 38,885 |
| B2_STACK | HOLD | 50,044/157,093/582,743/-275,336 | 49,536/146,732/575,118/-260,253 (lots x0.88) | -508 | -10,361 | -7,625 | 15,083 |
| B2_STACK | SPAN2 | 20,989/108,510/373,096/-196,770 | 20,497/109,098/373,096/-196,770 (lots x0.88) | -492 | 587 | 0 | 0 |
| B1_DS5 | WFPRE | 42,973/91,366/254,477/-165,116 | 39,773/80,936/233,434/-135,486 (lots x0.88) | -3,201 | -10,430 | -21,043 | 29,631 |
| B1_DS5 | HOLD | 50,210/99,685/369,759/-173,403 | 48,452/95,675/391,661/-186,892 (lots x0.88) | -1,758 | -4,010 | 21,902 | -13,490 |
| B1_DS5 | SPAN2 | 9,373/73,604/263,061/-173,810 | 11,369/76,161/259,858/-162,517 (lots x0.88) | 1,996 | 2,557 | -3,202 | 11,293 |
| B2_DS5 | WFPRE | 42,973/91,366/254,477/-165,116 | 38,560/80,124/229,898/-147,786 (lots x0.87) | -4,414 | -11,242 | -24,579 | 17,330 |
| B2_DS5 | HOLD | 50,210/99,685/369,759/-173,403 | 47,883/92,808/346,096/-155,962 (lots x0.87) | -2,327 | -6,877 | -23,663 | 17,440 |
| B2_DS5 | SPAN2 | 9,373/73,604/263,061/-173,810 | 9,626/74,569/289,728/-173,810 (lots x0.87) | 253 | 965 | 26,667 | 0 |
| E2_POOL | WFPRE | 97,581/240,555/890,359/-402,311 | 86,971/212,064/756,467/-350,564 (lots x0.85) | -10,611 | -28,491 | -133,893 | 51,747 |
| E2_POOL | HOLD | 119,901/265,981/1,417,018/-632,864 | 115,053/251,767/1,287,523/-572,131 (lots x0.85) | -4,848 | -14,214 | -129,495 | 60,733 |
| E2_POOL | SPAN2 | -17,804/189,194/1,955,727/-457,211 | -16,658/189,209/1,992,434/-457,211 (lots x0.85) | 1,147 | 15 | 36,708 | 0 |

## (e) The "2023 fix"
2023-04..2024-01 vs the rest (forecast-table session-open fields; ATR is the 20-day ATR; trend persistence = lag-1 autocorrelation and 5-day variance ratio of daily returns, >1 means trending):

| span | days | daily-return SD | ATR20/price | ATR20 / own 120d median | lag-1 autocorr | 5d variance ratio | share of 20d moves > 1 sd-scaled | median VIX | share quiet (P>=.6) | share wide (P<=.25) |
|---|---|---|---|---|---|---|---|---|---|---|
| 2023-04..2024-01 | 216 | 0.84% | 1.21% | 0.99 | 0.006 | 1.03 | 0.35 | 14.6 | 0.33 | 0.35 |
| 2024-02..2025-06 | 364 | 1.29% | 1.49% | 1.11 | -0.121 | 0.87 | 0.21 | 16.3 | 0.36 | 0.26 |
| 2025-07..2026-10 | 337 | 1.15% | 1.54% | 1.03 | -0.082 | 0.86 | 0.16 | 16.7 | 0.19 | 0.36 |
| 2023-02..03 (36d) | 36 | 0.95% | 1.61% | nan | -0.029 | 0.94 | 0.19 | 20.8 | 0.22 | 0.33 |

Reading: the span was CALM and TRENDING, not "quiet" as the forecaster sees it: daily SD 0.84% vs 1.29%/1.15% later, ATR20/price 1.21% vs 1.5%, VIX median 14.6 vs 16.3-16.7, variance ratio 1.03 and autocorrelation +0.006 vs 0.86-0.87 and -0.08..-0.12 afterwards (2024-26 is mean-reverting), ATR vs own 120-day median 0.99 (not compressed), while P_quiet >=0.6 is flagged on 33% of days (36% in PRE) so the forecaster does not single the span out. A vol-based rule has no handle on a persistence-structure difference.
Pooled set of the failers (MV, PE, KB20_S, DON15m_n14_S, DON10m_n14_S, DON10m_n20_S, 10 lots each, summed): SPAN2 base mean -17,804/wk. Rule results (lot-matched, SPAN2 | PRE | HOLD deltas): E1 compression quiet 0.5: +3,505 (rank 0.58, CI -10.9k..+17.1k, MDE 20.3k) | +10,875 (0.93) | +10,203; E2 8-wk vol-scale: -1,736 (0.33, MDE 14.4k) | +4,261 (0.99) | +14,828 (1.00); E3 VIX high 0.5: +1,151 (0.53, MDE 23.8k) | +609 | +21,004; E4 HAR-P compression: +4,088 (0.74, MDE 17.5k) | +3,025 | +10,139. Pooled SPAN2 weekly mean AFTER the rule stays negative in all four (-14.3k, -19.5k, -16.7k, -13.7k). **No rule CUTS the 2023 loss with placebo >=0.90 and every SPAN2 delta is far inside its MDE, so none "fixes the 2023 failure"; E2 keeps (and adds to) 2024-26 but does nothing in 2023.** (E1's SPAN2 number is optimistic: ~30% of those days carry in-sample P_quiet; the HAR sensitivity E4 is the same sign and also inside MDE.)
Per candidate, delta of weekly mean vs the same book unscaled (SPAN2 base is the 2023 loss):

| candidate | window | base wk mean | E1 (A1) | E2 (8wk vol) | E3 (VIX hi 0.5) |
|---|---|---|---|---|---|
| MV | SPAN2 | -7,546 | 1,876 | -1,279 | 238 |
| MV | WFPRE | 17,221 | 242 | 2,173 | 116 |
| MV | HOLD | 24,041 | 2,312 | 2,044 | 2,455 |
| PE | SPAN2 | 5,996 | 716 | 1,395 | 3,103 |
| PE | WFPRE | 11,859 | 1,756 | -314 | -1,369 |
| PE | HOLD | 18,374 | 617 | 3,776 | 4,880 |
| KB20_S | SPAN2 | -4,539 | 2,723 | -474 | -625 |
| KB20_S | WFPRE | 23,628 | 1,652 | -320 | 1,194 |
| KB20_S | HOLD | 21,550 | 698 | 930 | 4,646 |
| DON15n14 | SPAN2 | -6,792 | -696 | -1,052 | -1,161 |
| DON15n14 | WFPRE | 16,935 | 2,355 | 1,077 | -1,012 |
| DON15n14 | HOLD | 22,370 | 3,238 | 2,181 | 4,230 |
| DON10n14 | SPAN2 | -1,815 | -961 | 364 | -180 |
| DON10n14 | WFPRE | 12,283 | 2,418 | 795 | 1,628 |
| DON10n14 | HOLD | 14,885 | 1,509 | 2,666 | 2,394 |
| DON10n20 | SPAN2 | -3,109 | -152 | -690 | -224 |
| DON10n20 | WFPRE | 15,656 | 2,451 | 851 | 52 |
| DON10n20 | HOLD | 18,681 | 1,828 | 3,232 | 2,399 |

## Deviations and caveats (none soften a gate)
1. STACK is DS2 10/10/7 + KB10 + SM10 summed per book (the "DS2+KB10+SM10" comparator without PB and shared-lock interplay), not the D3SL stack; per-book exact locks only. Per-day lots multiply the base lots (fractional lots; the size-dependent sweep cost uses the s113 equal_risk.excess surface for library books; identity vs the stored lock-scaled rows is exact, max abs diff 0.0). Per-day variable lots assume the locks reset each day; the lock path across days with different lots is not re-run (the exact engine is validated only for constant-lot scaling).
2. The six pooled 2023-failer series come from the TR2 daily parquet at 10 lots (no trade counts), scaled linearly in lots (no size-dependent cost); MV/PE are library series.
3. P_quiet is the RTH-open (s=2) value of the label day for every book; before 2024-02 ~30% of SPAN2 days were fitted in-sample (flag insample_fit), 2024-02+ is walk-forward. The prior-art QUIET trade-gate (TR4) already found no value; this track tests it as a multiplier.
4. Primary basis is lot-matched (average lots equal to the baseline in PRE, c fixed from PRE); raw deltas are in final_results.json. Tiering and the selection of the one rule were fixed in the prereg and the pre-holdout text; the verdict wording about B2 being steadier is a post-HOLD reading, not a selection.
5. The WF-HOLD maxDD comparison is a single path (68 weeks); the worst-week delta is one week.
6. HOLD read once for all 24 cells (logged look); no other holdout reads.
