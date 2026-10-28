# DS3_DIV2_B_PAIRS - market-neutral intraday relative value (D3D2B, T-DIVERSIFY-2 section B, 2026-10-28)

Research only; no live / execution / chart change; no download or purchase; no credentials. UNTOUCHED (trade dates after 2026-02-06) never read: the minute grids were cut at label day 2026-02-06 when built, so every window below ends there (HOLD = 2025-07-01..2026-02-06, not the 2026-10-16 end used by earlier reports). Code l2vast/ds3/code/dv2b/ (dv2b_data, dv2b_lib, dv2b_prereg, dv2b_run, dv2b_score, dv2b_pretext, dv2b_final, dv2b_report, dv2b_write, dv2b_audit); outputs l2vast/ds3/out/dv2b/. Prereg files l2vast/ds3/prereg/DV2B_G1_prereg.md (sha256 a20b13ec41611c6eb891b4b33dee5623345e32e82541dd8837ec5ece251534b7), DV2B_G2_prereg.md (24e76ecfa570fdeb82887677736765418498b17a7b01e47e98df82b6182d6cfb), DV2B_G3_prereg.md (10491e54b1b7eff201c289391cf72a5146e0d7aecb2244082b2b04bae20307c6); DECISIONS.md line 'D3D2B PREREG' (47 cells, F = 16/16/15, ledger total 68440). Pre-holdout texts DS3_DV2B_G1/G2/G3_PREHOLD.md; one logged holdout look per group (+ _SPAN2), tracks DS3_DV2B_G1..G3 in struct48/ledger/holdout_looks.jsonl. Prior work check: no pairs / relative-value study exists in LEADERBOARD, TREND_LEADERBOARD or any DS3_*.md (the only neighbours are DS3_CHOP_FINAL's pooled NQ/ES/RTY/YM overnight dip-buys and the DVX cross-market signals, neither a dollar-neutral spread), so nothing is cited instead of run.

## Verdict (headline)
**All 47 cells are DEAD; nothing replicates and nothing is CONFIRMED.** Dollar-neutral z-score mean reversion of the intraday log-ratio loses money on every one of the 8 pairs and all 4 parameter variants, in WF, in the HOLD and in the 2023 span; the loss is almost exactly the transaction cost, not a negative edge: gross P&L before costs is about zero on the index pairs (pooled primary cell +$4/trade against $298 of fees and slippage per round trip of two legs), small positive only on RTY/ES (gross +$1,250/wk WF, placebo-a effect +$1,258 [267, 2,363], rank 1.00, against $2,965/wk of cost, break-even cost multiple 0.42x) and ZN/ZB (gross +$1,760/wk against $33,546/wk), so the signal is real in sign on two pairs and uneconomic on all. The laggard catch-up has the WRONG sign: the catch-up direction is worse than a coin flip in WF and in the HOLD (pooled 11:30 gross -$556/wk WF [-1,038, -110] and -$930/wk HOLD), i.e. relative strength measured from the open CONTINUES into the close; that continuation direction is only a post-hoc LEAD, not a result (see Lead).

Power: the WF means are far outside their MDEs (e.g. NQ/ES primary -$3,667/wk [-4,546, -2,787], MDE 1,257), so these are informative nulls on the NEGATIVE side, not underpowered ones; the only cells whose CI contains 0 are the small-size laggard cells (WF MDE $100-450/wk), where a +$100/wk effect would be invisible (about 1 year of extra data per +$150/wk of MDE).

Replication rule (index pairs >= 3 of 4, commodity/rate pairs >= 2 of 4; R1 = WF mean > 0 and CI lower > 0 and HOLD mean > 0):
| group | variant | pairs with R1 (needs) | replicates | pooled-row tier | pooled years ok / halves ok | CONFIRMED |
|---|---|---|---|---|---|---|
| G1 | w120_z2.0 | 0 of 4 (needs 3)  | no | DEAD | False / False | no |
| G1 | w120_z2.5 | 0 of 4 (needs 3)  | no | DEAD | False / False | no |
| G1 | w240_z2.0 | 0 of 4 (needs 3)  | no | DEAD | False / False | no |
| G1 | w60_z2.0 | 0 of 4 (needs 3)  | no | DEAD | False / False | no |
| G2 | w120_z2.0 | 0 of 4 (needs 2)  | no | DEAD | False / False | no |
| G2 | w120_z2.5 | 0 of 4 (needs 2)  | no | DEAD | False / False | no |
| G2 | w240_z2.0 | 0 of 4 (needs 2)  | no | DEAD | False / False | no |
| G2 | w60_z2.0 | 0 of 4 (needs 2)  | no | DEAD | False / False | no |
| G3 | LAG1000 | 0 of 4 (needs 3)  | no | DEAD | False / False | no |
| G3 | LAG1130 | 0 of 4 (needs 3)  | no | DEAD | False / False | no |
| G3 | LAG1400 | 0 of 4 (needs 3)  | no | DEAD | False / False | no |

Fee grades: NQ/ES uses ES (NT-published) and NQ (proxy) at $4.84 RT per contract; every other pair has at least one WEAK-proxy leg (RTY, YM, CL, GC, ZN, ZB, RB, HO, SI at the ES value), so the ceiling there is CANDIDATE, which no cell reached anyway; 2x cost is shown on every row.

## Top cells regardless of verdict (never empty-handed)
Ranked by WF net $/wk (equal $1,000 risk per trade, conservative fills); none passes any profitability gate; the stack columns are the point of section B (neutral to NQ by construction, correlation ~0 as expected, and what they did in the stack's bad hours).
| rank | cell | WF $/wk [CI] (MDE) | HOLD $/wk | tier | failed gates | stack corr | $ in stack worst-20 wks | $ in stack loss slots |
|---|---|---|---|---|---|---|---|---|
| 1 | LAG1400_RTY/ES | -38 [-164,88] (180) | -180 | DEAD | beats_a,cost2x_pre,year_share,hold,span2,best_of_N | +0.08 | -1,297 | 0 |
| 2 | LAG1400_ALL4 | -71 [-145,3] (105) | -125 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | -0.02 | -75 | 0 |
| 3 | LAG1400_NQ/RTY | -116 [-238,6] (174) | -220 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | +0.06 | -2,621 | 0 |
| 4 | LAG1000_ALL4 | -120 [-302,62] (260) | -303 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | -0.03 | -948 | 0 |
| 5 | LAG1000_RTY/ES | -122 [-428,185] (438) | -202 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | -0.01 | -992 | 0 |
| 6 | LAG1400_NQ/ES | -133 [-231,-35] (140) | -151 | DEAD | mean_up,beats_a,cost2x_pre,year_share,hold,span2,best_of_N | -0.09 | -668 | 0 |
| 7 | LAG1400_YM/ES | -144 [-241,-47] (139) | -123 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | -0.01 | -2,958 | 0 |
| 8 | LAG1130_ALL4 | -175 [-292,-58] (167) | -304 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,best_of_N | -0.15 | 27 | -18,235 |
Reading: the best cell, LAG1400_RTY/ES, is -$38/wk [-164, 88] (MDE 180): it is inside noise, fails beats_a (the catch-up sign is not better than random), cost2x_pre, year_share, hold, span2 and best_of_N; its P&L in the stack's 20 worst weeks is -$1.3k (the stack lost $3.7M in those weeks at its own size, so a risk-parity stack-add would not move it), 0 trades in the stack's loss-slot set (14:00 is not a loss slot). The best mean-reversion cell is NQ/RTY_w240_z2.0 (-$1,146/wk [-1,971, -321], MDE 1,179; worst-20 weeks -$46k, loss slots -$15k).

## What was run
- Frozen rules (full text in the prereg files). G1/G2 (z-score MR, 16 cells each): log-ratio r = log(A/B) of 1-min closes, z against the trailing N = 120 (primary), 60, 240 minutes of the same label-day grid (02:00 on), enter at the next open when z_in (2.0 primary, 2.5 variant) <= |z| < 3.5, exit at z = 0, stop at |z| = 3.5 or 2 x the pair's prior-20-session median daily range of r (whichever first), flat 15:55; entries 09:35-15:30; no re-entry after a stop that day. Dollar-neutral, equal $1,000 risk: N_leg = $1,000 / min((3.5 - z_in) sd, 2 x median range). G3 (laggard catch-up, 15 cells): move since the 09:30 open per index, long the laggard / short the leader at 10:00, 11:30, 14:00 when the gap >= the prior-20-session median gap, stop 2 x that median gap, flat 15:55; pair cells NQ/ES, RTY/ES, YM/ES, NQ/RTY plus ALL4 (laggard vs leader among four).
- Pairs run: NQ/ES, RTY/ES, YM/ES, NQ/RTY (index), ZN/ZB, CL/RB, CL/HO, GC/SI (commodity/rate). ZF/ZN (the alternative) was not run; GC/SI, CL/RB, CL/HO use RB/HO bars that are thin overnight (grid valid-minute rule: z needs >= 0.6 N minutes with both legs); no NEEDS: all 12 symbols are on disk (1-min .v.0 bars, raw prices; all volume-roll bars fall 18:00-21:00 ET so 0 roll days dropped).
- Fills (D3CX): market +1 tick adverse per leg, stop +2 ticks per leg, signal on the close of minute t, trade at the open of the next minute with a bar in both legs. Stops are tested on 1-min ratio closes (bars cannot give the ratio's intrabar extreme), so real stop fills could be better or worse than modeled; fees $4.84 RT per contract per leg.
- Windows: X 2023-04-03..2024-01-31 (second holdout), WFPRE 2024-02-01..2025-06-30 (selection), WF 2024-02-01..2026-02-06, HOLD 2025-07-01..2026-02-06. Placebos (40 draws, week-bootstrap CI): (a) random sign at the same entries/exits; (b) random clock, same rule (MR: same number of trades per day at uniformly random minutes, fading z at that minute whatever its size; laggard: random clock 10:00-14:00).
- Identity audit (WFPRE trades, dv2b_audit.py): z agrees with an independent pandas rolling z to 4e-10 on every full-window column; six RTY/ES trades recomputed from the raw grid match the engine's gross and cost to the cent.

## G1 - index pairs, z-score mean reversion (F = 16)
| cell | tr/wk | WF $/wk [95% CI] (MDE) | HOLD $/wk [CI] (MDE) | X 2023-span $/wk [CI] (MDE) | WF 2x cost | (a) WF effect [CI] rank | (b) WF effect rank | tier | failed | R1/R2 |
|---|---|---|---|---|---|---|---|---|---|---|
| NQ/ES_w120_z2.0 | 10.1 | -3,667 [-4,546,-2,787] (1,257) | -3,852 [-5,423,-2,281] (2,244) | -2,942 [-4,265,-1,620] (1,889) | -6,886 | -368 [-1,259,553] r0.23 | -2,643 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| NQ/ES_w60_z2.0 | 18.7 | -7,670 [-9,292,-6,048] (2,317) | -8,021 [-11,003,-5,040] (4,259) | -6,463 [-8,747,-4,179] (3,263) | -15,188 | -174 [-1,815,1,463] r0.47 | -4,025 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| NQ/ES_w240_z2.0 | 7.5 | -1,998 [-2,749,-1,247] (1,073) | -2,517 [-3,782,-1,252] (1,807) | -1,755 [-2,729,-781] (1,392) | -4,068 | 107 [-684,888] r0.57 | -1,430 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| NQ/ES_w120_z2.5 | 8.3 | -3,393 [-4,624,-2,161] (1,759) | -4,724 [-7,135,-2,313] (3,445) | -3,161 [-4,899,-1,422] (2,484) | -7,324 | 676 [-525,1,915] r0.78 | -1,792 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| RTY/ES_w120_z2.0 | 11.7 | -1,715 [-2,674,-757] (1,369) | -3,737 [-5,634,-1,841] (2,709) | -3,952 [-5,295,-2,610] (1,918) | -4,681 | 1,258 [267,2,363] r1.00 | -537 r0.03 | DEAD | mean_up,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| RTY/ES_w60_z2.0 | 21.0 | -5,880 [-7,709,-4,052] (2,612) | -7,361 [-10,349,-4,373] (4,269) | -7,749 [-10,160,-5,337] (3,445) | -13,164 | 1,514 [-433,3,577] r0.93 | -2,621 r0.00 | DEAD | mean_up,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| RTY/ES_w240_z2.0 | 7.6 | -1,564 [-2,333,-794] (1,100) | -2,039 [-3,502,-576] (2,090) | -2,207 [-3,164,-1,249] (1,368) | -3,195 | 94 [-748,1,006] r0.57 | -952 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| RTY/ES_w120_z2.5 | 8.1 | -2,387 [-3,618,-1,156] (1,758) | -4,808 [-7,199,-2,417] (3,416) | -4,710 [-6,623,-2,797] (2,733) | -5,499 | 800 [-370,2,103] r0.88 | -792 r0.05 | DEAD | mean_up,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| YM/ES_w120_z2.0 | 10.3 | -4,484 [-5,482,-3,486] (1,425) | -4,375 [-5,868,-2,881] (2,134) | -5,275 [-6,711,-3,840] (2,051) | -8,393 | -671 [-1,854,434] r0.10 | -2,630 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| YM/ES_w60_z2.0 | 19.2 | -10,013 [-11,798,-8,229] (2,549) | -8,208 [-11,075,-5,341] (4,096) | -15,967 [-18,620,-13,313] (3,791) | -19,209 | -919 [-2,972,990] r0.15 | -5,176 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| YM/ES_w240_z2.0 | 7.4 | -2,450 [-3,072,-1,827] (889) | -2,565 [-3,705,-1,425] (1,629) | -2,934 [-4,097,-1,770] (1,662) | -4,749 | -98 [-789,588] r0.33 | -1,698 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| YM/ES_w120_z2.5 | 7.9 | -5,378 [-6,747,-4,008] (1,956) | -5,530 [-7,550,-3,510] (2,885) | -5,603 [-7,613,-3,593] (2,872) | -9,857 | -811 [-2,276,571] r0.10 | -3,017 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| NQ/RTY_w120_z2.0 | 10.9 | -1,735 [-2,850,-621] (1,592) | -2,077 [-4,161,7] (2,977) | -2,918 [-4,531,-1,306] (2,303) | -3,389 | -185 [-1,331,991] r0.42 | -1,231 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| NQ/RTY_w60_z2.0 | 20.7 | -3,382 [-5,090,-1,673] (2,441) | -2,867 [-6,562,827] (5,278) | -5,259 [-8,520,-1,998] (4,658) | -7,702 | 911 [-718,2,816] r0.90 | -1,933 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| NQ/RTY_w240_z2.0 | 7.5 | -1,146 [-1,971,-321] (1,179) | -1,889 [-3,220,-557] (1,902) | -1,068 [-2,125,-12] (1,509) | -2,113 | -165 [-980,704] r0.33 | -859 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| NQ/RTY_w120_z2.5 | 8.0 | -1,752 [-3,238,-266] (2,123) | -2,098 [-4,893,698] (3,994) | -3,583 [-5,633,-1,532] (2,929) | -3,564 | 156 [-1,358,1,679] r0.57 | -944 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| POOL_w120_z2.0 | 43.0 | -11,601 [-13,887,-9,315] (3,265) | -14,041 [-17,654,-10,428] (5,162) | -15,088 [-18,934,-11,242] (5,494) | -23,349 | 33 [-2,198,2,559] r0.42 | -7,041 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| POOL_w60_z2.0 | 79.5 | -26,945 [-31,589,-22,301] (6,634) | -26,458 [-34,369,-18,546] (11,302) | -35,437 [-42,861,-28,013] (10,606) | -55,263 | 1,332 [-3,104,5,960] r0.82 | -13,755 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| POOL_w240_z2.0 | 30.0 | -7,158 [-8,847,-5,469] (2,413) | -9,010 [-12,116,-5,904] (4,437) | -7,964 [-10,694,-5,234] (3,900) | -14,125 | -63 [-1,804,1,721] r0.42 | -4,939 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| POOL_w120_z2.5 | 32.3 | -12,909 [-15,966,-9,853] (4,367) | -17,159 [-21,819,-12,499] (6,657) | -17,057 [-22,197,-11,917] (7,343) | -26,244 | 822 [-2,043,3,840] r0.72 | -6,545 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |

Gross versus cost (WF window, weekly): the signal does not carry its fees.
| cell | gross $/wk (WF) | cost $/wk (WF) | gross/cost | net break-even cost multiple |
|---|---|---|---|---|
| NQ/ES_w120_z2.0 | -447 | 3,220 | -0.14 | 0.00x |
| NQ/ES_w60_z2.0 | -151 | 7,519 | -0.02 | 0.00x |
| NQ/ES_w240_z2.0 | 72 | 2,070 | 0.03 | 0.03x |
| NQ/ES_w120_z2.5 | 539 | 3,931 | 0.14 | 0.14x |
| RTY/ES_w120_z2.0 | 1,250 | 2,965 | 0.42 | 0.42x |
| RTY/ES_w60_z2.0 | 1,404 | 7,284 | 0.19 | 0.19x |
| RTY/ES_w240_z2.0 | 68 | 1,631 | 0.04 | 0.04x |
| RTY/ES_w120_z2.5 | 725 | 3,112 | 0.23 | 0.23x |
| YM/ES_w120_z2.0 | -575 | 3,909 | -0.15 | 0.00x |
| YM/ES_w60_z2.0 | -818 | 9,196 | -0.09 | 0.00x |
| YM/ES_w240_z2.0 | -150 | 2,300 | -0.07 | 0.00x |
| YM/ES_w120_z2.5 | -898 | 4,479 | -0.20 | 0.00x |
| NQ/RTY_w120_z2.0 | -81 | 1,654 | -0.05 | 0.00x |
| NQ/RTY_w60_z2.0 | 939 | 4,320 | 0.22 | 0.22x |
| NQ/RTY_w240_z2.0 | -179 | 967 | -0.19 | 0.00x |
| NQ/RTY_w120_z2.5 | 60 | 1,812 | 0.03 | 0.03x |
| POOL_w120_z2.0 | 621 | 48,450 | 0.01 | 0.01x |
| POOL_w60_z2.0 | 4,321 | 114,589 | 0.04 | 0.04x |
| POOL_w240_z2.0 | -580 | 19,843 | -0.03 | 0.00x |
| POOL_w120_z2.5 | -1,384 | 45,652 | -0.03 | 0.00x |

By calendar year / halves (the replication rule's year test; all pooled and single rows):
| cell | 2023 (Apr-Dec) | 2024 | 2025 | 2026 (5 wk) | pre-2025 half | post-2025 half | years ok | halves ok |
|---|---|---|---|---|---|---|---|---|
| NQ/ES_w120_z2.0 | -3,088 [-4,554,-1,623] (2,094) | -3,488 [-4,751,-2,225] (1,804) | -3,745 [-4,977,-2,513] (1,759) | -2,390 [-4,909,129] (3,598) | -3,319 | -3,669 | False | False |
| NQ/ES_w60_z2.0 | -6,306 [-8,859,-3,754] (3,646) | -7,985 [-10,199,-5,770] (3,164) | -7,431 [-9,771,-5,091] (3,343) | -5,731 [-11,659,197] (8,468) | -7,273 | -7,383 | False | False |
| NQ/ES_w240_z2.0 | -1,783 [-2,874,-692] (1,558) | -1,536 [-2,497,-575] (1,374) | -2,186 [-3,332,-1,040] (1,637) | -3,700 [-4,938,-2,462] (1,769) | -1,641 | -2,381 | False | False |
| NQ/ES_w120_z2.5 | -3,186 [-5,081,-1,291] (2,707) | -2,741 [-4,469,-1,013] (2,469) | -3,945 [-5,712,-2,177] (2,525) | -3,347 [-7,233,540] (5,552) | -2,930 | -3,951 | False | False |
| RTY/ES_w120_z2.0 | -4,179 [-5,516,-2,843] (1,910) | -1,151 [-2,442,140] (1,844) | -1,996 [-3,443,-549] (2,068) | -4,321 [-7,229,-1,413] (4,155) | -2,435 | -2,271 | False | False |
| RTY/ES_w60_z2.0 | -8,261 [-10,903,-5,618] (3,775) | -5,633 [-8,002,-3,264] (3,384) | -5,437 [-8,164,-2,710] (3,896) | -9,225 [-16,135,-2,316] (9,871) | -6,747 | -5,923 | False | False |
| RTY/ES_w240_z2.0 | -2,174 [-3,179,-1,170] (1,435) | -1,606 [-2,578,-633] (1,389) | -1,558 [-2,747,-369] (1,698) | -1,726 [-4,831,1,379] (4,436) | -1,847 | -1,602 | False | False |
| RTY/ES_w120_z2.5 | -5,358 [-7,163,-3,554] (2,578) | -1,406 [-3,125,312] (2,455) | -2,843 [-4,667,-1,018] (2,606) | -4,353 [-8,579,-126] (6,038) | -3,082 | -3,048 | False | False |
| YM/ES_w120_z2.0 | -5,470 [-7,030,-3,911] (2,228) | -5,021 [-6,516,-3,525] (2,137) | -3,841 [-5,146,-2,536] (1,864) | -4,065 [-7,104,-1,026] (4,342) | -5,211 | -3,930 | False | False |
| YM/ES_w60_z2.0 | -16,226 [-19,147,-13,306] (4,172) | -11,063 [-13,720,-8,406] (3,796) | -9,378 [-11,723,-7,033] (3,350) | -7,963 [-16,134,207] (11,672) | -13,252 | -9,393 | False | False |
| YM/ES_w240_z2.0 | -2,967 [-4,215,-1,718] (1,784) | -2,824 [-3,552,-2,095] (1,041) | -2,077 [-3,093,-1,060] (1,452) | -2,227 [-4,646,191] (3,455) | -2,884 | -2,128 | False | False |
| YM/ES_w120_z2.5 | -5,991 [-8,046,-3,937] (2,935) | -5,226 [-7,534,-2,918] (3,297) | -5,299 [-6,908,-3,690] (2,299) | -4,184 [-7,613,-755] (4,899) | -5,550 | -5,275 | False | False |
| NQ/RTY_w120_z2.0 | -2,850 [-4,496,-1,203] (2,352) | -1,505 [-3,171,161] (2,379) | -1,932 [-3,474,-389] (2,204) | -3,172 [-7,372,1,028] (6,000) | -2,075 | -2,094 | False | False |
| NQ/RTY_w60_z2.0 | -5,251 [-8,809,-1,692] (5,083) | -3,243 [-5,534,-953] (3,272) | -3,504 [-6,014,-993] (3,587) | -4,581 [-12,970,3,808] (11,984) | -4,094 | -3,676 | False | False |
| NQ/RTY_w240_z2.0 | -1,264 [-2,360,-168] (1,565) | -683 [-1,947,582] (1,807) | -1,392 [-2,502,-281] (1,586) | -1,541 [-2,736,-347] (1,706) | -929 | -1,431 | False | False |
| NQ/RTY_w120_z2.5 | -3,646 [-5,745,-1,548] (2,998) | -1,886 [-3,936,165] (2,930) | -1,605 [-3,775,566] (3,100) | -2,694 [-9,774,4,386] (10,114) | -2,632 | -1,745 | False | False |
| POOL_w120_z2.0 | -15,587 [-19,586,-11,589] (5,712) | -11,165 [-14,471,-7,860] (4,722) | -11,514 [-14,879,-8,149] (4,807) | -13,948 [-18,612,-9,284] (6,663) | -13,040 | -11,964 | False | False |
| POOL_w60_z2.0 | -36,044 [-44,269,-27,820] (11,749) | -27,924 [-34,744,-21,103] (9,743) | -25,749 [-32,099,-19,400] (9,071) | -27,500 [-45,778,-9,223] (26,111) | -31,366 | -26,375 | False | False |
| POOL_w240_z2.0 | -8,188 [-11,078,-5,298] (4,128) | -6,648 [-9,234,-4,062] (3,695) | -7,213 [-9,515,-4,910] (3,289) | -9,195 [-12,536,-5,854] (4,773) | -7,301 | -7,542 | False | False |
| POOL_w120_z2.5 | -18,182 [-23,201,-13,164] (7,169) | -11,258 [-15,916,-6,601] (6,654) | -13,691 [-18,050,-9,331] (6,228) | -14,578 [-23,160,-5,995] (12,260) | -14,194 | -14,019 | False | False |

Tails and blow-ups (all scored trades 2023-04-03..2026-02-06):
| cell | trades (all scored) | gross $/trade | cost $/trade | worst trade | 1% / 5% trade | worst day | worst week | stop-exit share | stop-exit mean $ | non-stop mean $ | median lots (both legs) / p95 | median leg notional |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ/ES_w120_z2.0 | 1529 | -8 | 331 | -12,816 | -4,647 / -3,020 | -11,840 | -18,567 | 32% | -1,787 | 350 | 10.9 / 25 | 1,743,338 |
| NQ/ES_w60_z2.0 | 2826 | 38 | 426 | -14,546 | -7,039 / -3,945 | -16,867 | -25,461 | 14% | -2,390 | -51 | 15.0 / 35 | 2,366,211 |
| NQ/ES_w240_z2.0 | 1137 | 30 | 284 | -5,677 | -3,905 / -2,331 | -5,356 | -11,507 | 46% | -1,423 | 738 | 9.2 / 19 | 1,444,745 |
| NQ/ES_w120_z2.5 | 1228 | 87 | 493 | -15,765 | -7,110 / -4,135 | -14,302 | -25,855 | 38% | -2,329 | 795 | 16.0 / 36 | 2,513,066 |
| RTY/ES_w120_z2.0 | 1691 | 66 | 276 | -12,779 | -4,828 / -3,065 | -12,779 | -17,182 | 24% | -1,743 | 274 | 11.7 / 27 | 901,441 |
| RTY/ES_w60_z2.0 | 3040 | 59 | 376 | -24,638 | -6,894 / -4,033 | -24,638 | -31,707 | 11% | -2,368 | -60 | 16.3 / 40 | 1,253,071 |
| RTY/ES_w240_z2.0 | 1120 | 3 | 238 | -7,178 | -3,995 / -2,364 | -6,421 | -12,242 | 41% | -1,426 | 602 | 9.4 / 21 | 715,612 |
| RTY/ES_w120_z2.5 | 1208 | 37 | 418 | -17,991 | -7,174 / -4,301 | -17,991 | -24,420 | 33% | -2,299 | 544 | 16.8 / 40 | 1,286,763 |
| YM/ES_w120_z2.0 | 1610 | -10 | 429 | -12,043 | -5,293 / -3,144 | -12,043 | -21,171 | 27% | -1,893 | 89 | 16.4 / 38 | 1,847,854 |
| YM/ES_w60_z2.0 | 2890 | -48 | 562 | -15,253 | -8,076 / -4,194 | -18,788 | -44,190 | 12% | -2,530 | -341 | 22.1 / 53 | 2,577,561 |
| YM/ES_w240_z2.0 | 1129 | 8 | 353 | -10,112 | -3,618 / -2,382 | -7,207 | -10,736 | 41% | -1,543 | 486 | 12.7 / 29 | 1,445,009 |
| YM/ES_w120_z2.5 | 1210 | -31 | 644 | -17,145 | -8,843 / -4,507 | -17,145 | -28,802 | 34% | -2,501 | 285 | 23.6 / 57 | 2,668,197 |
| NQ/RTY_w120_z2.0 | 1611 | -34 | 160 | -13,497 | -5,437 / -3,040 | -13,497 | -14,912 | 26% | -1,574 | 294 | 8.8 / 20 | 732,140 |
| NQ/RTY_w60_z2.0 | 3076 | 31 | 222 | -21,031 | -7,419 / -3,725 | -21,031 | -33,872 | 11% | -2,115 | 42 | 12.6 / 30 | 1,052,468 |
| NQ/RTY_w240_z2.0 | 1116 | -17 | 134 | -6,215 | -3,554 / -2,272 | -6,215 | -10,304 | 42% | -1,291 | 688 | 6.9 / 15 | 576,886 |
| NQ/RTY_w120_z2.5 | 1202 | -48 | 238 | -20,246 | -7,614 / -4,094 | -20,246 | -20,527 | 34% | -2,003 | 587 | 12.8 / 28 | 1,073,723 |
| POOL_w120_z2.0 | 6441 | 4 | 298 | -13,497 | -5,243 / -3,074 | -34,411 | -47,075 | 27% | -1,752 | 249 | 11.5 / 29 | 1,181,919 |
| POOL_w60_z2.0 | 11832 | 20 | 393 | -24,638 | -7,373 / -3,995 | -50,329 | -101,207 | 12% | -2,356 | -100 | 16.0 / 41 | 1,655,316 |
| POOL_w240_z2.0 | 4502 | 6 | 252 | -10,112 | -3,846 / -2,338 | -16,187 | -27,781 | 43% | -1,420 | 625 | 9.3 / 22 | 969,574 |
| POOL_w120_z2.5 | 4848 | 12 | 449 | -20,246 | -7,656 / -4,301 | -47,885 | -54,030 | 35% | -2,286 | 550 | 16.6 / 42 | 1,727,350 |

Stack comparison (stack weeks to 2026-02-06 only; the window worst-20 are the 20 lowest stack weeks up to ISO 2026-W06, 16 of the audit's 20; 'stack loss slots' are A's 12 negative half-hour entry slots, 'idle slots' A's six blocked slots, which is where the 09:35 and 15:00-15:30 MR entries fall):
| cell | weekly corr to stack | $ in stack's worst-20 weeks (window) | $ in audit's worst-20 list (weeks <= 2026-02-06) | $ in stack loss slots | $ in idle slots | weeks<0 |
|---|---|---|---|---|---|---|
| NQ/ES_w120_z2.0 | -0.16 | -58,520 | -45,640 | -68,837 | -357,457 | 116 |
| NQ/ES_w60_z2.0 | +0.04 | -141,041 | -107,415 | -236,368 | -486,468 | 120 |
| NQ/ES_w240_z2.0 | -0.03 | -33,196 | -29,185 | -4,797 | -250,085 | 104 |
| NQ/ES_w120_z2.5 | -0.17 | -46,689 | -41,329 | -80,822 | -337,232 | 111 |
| RTY/ES_w120_z2.0 | +0.15 | -81,503 | -56,221 | -35,013 | -243,148 | 104 |
| RTY/ES_w60_z2.0 | +0.22 | -262,601 | -192,161 | -266,699 | -352,418 | 112 |
| RTY/ES_w240_z2.0 | +0.17 | -57,651 | -39,224 | -11,881 | -203,985 | 107 |
| RTY/ES_w120_z2.5 | +0.17 | -119,761 | -96,325 | -18,381 | -342,178 | 103 |
| YM/ES_w120_z2.0 | +0.01 | -119,825 | -84,455 | -147,687 | -444,141 | 123 |
| YM/ES_w60_z2.0 | +0.00 | -268,396 | -215,914 | -541,862 | -702,535 | 136 |
| YM/ES_w240_z2.0 | +0.10 | -59,396 | -49,536 | -34,764 | -295,892 | 120 |
| YM/ES_w120_z2.5 | +0.05 | -145,569 | -109,042 | -75,556 | -604,767 | 120 |
| NQ/RTY_w120_z2.0 | -0.03 | -60,997 | -34,265 | -45,511 | -204,618 | 103 |
| NQ/RTY_w60_z2.0 | +0.14 | -177,374 | -133,007 | -161,685 | -258,172 | 97 |
| NQ/RTY_w240_z2.0 | -0.01 | -46,098 | -37,103 | -15,204 | -163,786 | 103 |
| NQ/RTY_w120_z2.5 | +0.04 | -91,735 | -68,201 | -24,681 | -222,805 | 97 |
| POOL_w120_z2.0 | -0.01 | -320,844 | -220,580 | -297,049 | -1,249,365 | 124 |
| POOL_w60_z2.0 | +0.15 | -849,412 | -648,497 | -1,206,614 | -1,799,593 | 134 |
| POOL_w240_z2.0 | +0.09 | -196,341 | -155,047 | -66,646 | -913,748 | 122 |
| POOL_w120_z2.5 | +0.04 | -403,753 | -314,897 | -199,439 | -1,506,982 | 123 |

## G2 - commodity and rate pairs, z-score mean reversion (F = 16)
| cell | tr/wk | WF $/wk [95% CI] (MDE) | HOLD $/wk [CI] (MDE) | X 2023-span $/wk [CI] (MDE) | WF 2x cost | (a) WF effect [CI] rank | (b) WF effect rank | tier | failed | R1/R2 |
|---|---|---|---|---|---|---|---|---|---|---|
| ZN/ZB_w120_z2.0 | 16.1 | -31,786 [-33,621,-29,951] (2,621) | -34,711 [-37,797,-31,626] (4,408) | -25,891 [-28,523,-23,258] (3,761) | -65,332 | 1,795 [650,2,906] r1.00 | -12,572 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| ZN/ZB_w60_z2.0 | 29.1 | -73,934 [-77,603,-70,265] (5,242) | -80,426 [-86,499,-74,353] (8,676) | -59,683 [-65,023,-54,342] (7,629) | -151,945 | 3,940 [2,420,5,532] r1.00 | -26,548 r0.00 | DEAD | mean_up,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| ZN/ZB_w240_z2.0 | 8.7 | -12,615 [-13,469,-11,761] (1,220) | -14,030 [-15,420,-12,640] (1,985) | -9,808 [-10,980,-8,636] (1,674) | -25,631 | 396 [-341,1,184] r0.93 | -5,351 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| ZN/ZB_w120_z2.5 | 9.9 | -29,078 [-30,946,-27,210] (2,669) | -29,532 [-32,076,-26,989] (3,634) | -24,146 [-26,849,-21,442] (3,862) | -59,781 | 1,556 [170,2,971] r1.00 | -10,128 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| CL/RB_w120_z2.0 | 13.5 | -5,812 [-7,027,-4,596] (1,736) | -6,264 [-8,383,-4,145] (3,027) | -3,338 [-4,869,-1,806] (2,188) | -12,008 | 380 [-929,1,693] r0.70 | -3,008 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| CL/RB_w60_z2.0 | 22.7 | -12,992 [-14,531,-11,452] (2,199) | -14,553 [-17,554,-11,552] (4,287) | -9,419 [-11,754,-7,085] (3,335) | -27,698 | 1,708 [8,3,349] r0.97 | -5,595 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| CL/RB_w240_z2.0 | 8.6 | -2,771 [-3,677,-1,866] (1,294) | -2,611 [-4,078,-1,143] (2,097) | -1,758 [-2,949,-566] (1,703) | -5,629 | 82 [-878,1,040] r0.53 | -1,594 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| CL/RB_w120_z2.5 | 8.7 | -6,682 [-8,154,-5,210] (2,103) | -6,976 [-9,628,-4,323] (3,789) | -3,593 [-5,656,-1,530] (2,947) | -12,898 | -493 [-2,095,986] r0.25 | -3,316 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| CL/HO_w120_z2.0 | 13.1 | -5,499 [-6,678,-4,320] (1,685) | -4,474 [-6,722,-2,227] (3,211) | -2,555 [-4,343,-768] (2,554) | -10,492 | -552 [-1,774,642] r0.17 | -3,112 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| CL/HO_w60_z2.0 | 22.6 | -12,788 [-14,618,-10,958] (2,614) | -10,194 [-13,263,-7,125] (4,384) | -7,396 [-9,908,-4,885] (3,588) | -25,078 | -406 [-2,315,1,420] r0.28 | -6,234 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| CL/HO_w240_z2.0 | 8.7 | -2,227 [-2,973,-1,480] (1,067) | -1,628 [-2,578,-677] (1,358) | -2,366 [-3,869,-862] (2,148) | -4,650 | 127 [-703,908] r0.68 | -1,093 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| CL/HO_w120_z2.5 | 8.4 | -5,619 [-7,030,-4,207] (2,017) | -5,704 [-8,537,-2,870] (4,048) | -2,294 [-4,289,-299] (2,850) | -10,544 | -845 [-2,293,699] r0.07 | -2,712 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| GC/SI_w120_z2.0 | 11.7 | -4,732 [-5,684,-3,780] (1,360) | -5,237 [-7,182,-3,292] (2,778) | -6,033 [-7,545,-4,520] (2,161) | -8,446 | -1,088 [-2,128,-42] r0.00 | -2,589 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| GC/SI_w60_z2.0 | 19.9 | -10,554 [-12,166,-8,943] (2,302) | -8,852 [-12,126,-5,578] (4,677) | -15,549 [-17,827,-13,271] (3,254) | -20,136 | -618 [-2,291,1,067] r0.17 | -5,293 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| GC/SI_w240_z2.0 | 7.1 | -2,809 [-3,491,-2,127] (974) | -3,625 [-4,958,-2,292] (1,904) | -1,280 [-2,312,-248] (1,474) | -4,354 | -1,227 [-1,963,-534] r0.00 | -1,744 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| GC/SI_w120_z2.5 | 7.7 | -5,657 [-6,854,-4,460] (1,710) | -6,742 [-9,357,-4,127] (3,735) | -5,647 [-7,675,-3,619] (2,897) | -9,466 | -1,855 [-3,190,-558] r0.03 | -2,887 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| POOL_w120_z2.0 | 54.4 | -47,828 [-50,441,-45,215] (3,733) | -50,686 [-55,103,-46,269] (6,310) | -37,816 [-42,422,-33,209] (6,580) | -96,278 | 535 [-1,657,2,783] r0.65 | -21,282 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| POOL_w60_z2.0 | 94.4 | -110,268 [-114,953,-105,582] (6,694) | -114,025 [-123,050,-104,999] (12,893) | -92,047 [-100,001,-84,093] (11,363) | -224,857 | 4,623 [881,8,005] r1.00 | -43,670 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| POOL_w240_z2.0 | 33.1 | -20,422 [-21,900,-18,944] (2,112) | -21,893 [-24,019,-19,767] (3,037) | -15,211 [-18,159,-12,264] (4,211) | -40,265 | -622 [-2,202,894] r0.23 | -9,782 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| POOL_w120_z2.5 | 34.7 | -47,036 [-50,056,-44,016] (4,314) | -48,954 [-54,045,-43,863] (7,273) | -35,679 [-40,711,-30,647] (7,189) | -92,688 | -1,637 [-4,244,1,033] r0.15 | -19,043 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |

| cell | gross $/wk (WF) | cost $/wk (WF) | gross/cost | net break-even cost multiple |
|---|---|---|---|---|
| ZN/ZB_w120_z2.0 | 1,760 | 33,546 | 0.05 | 0.05x |
| ZN/ZB_w60_z2.0 | 4,077 | 78,011 | 0.05 | 0.05x |
| ZN/ZB_w240_z2.0 | 401 | 13,016 | 0.03 | 0.03x |
| ZN/ZB_w120_z2.5 | 1,624 | 30,702 | 0.05 | 0.05x |
| CL/RB_w120_z2.0 | 385 | 6,196 | 0.06 | 0.06x |
| CL/RB_w60_z2.0 | 1,715 | 14,706 | 0.12 | 0.12x |
| CL/RB_w240_z2.0 | 86 | 2,858 | 0.03 | 0.03x |
| CL/RB_w120_z2.5 | -466 | 6,216 | -0.08 | 0.00x |
| CL/HO_w120_z2.0 | -505 | 4,994 | -0.10 | 0.00x |
| CL/HO_w60_z2.0 | -498 | 12,290 | -0.04 | 0.00x |
| CL/HO_w240_z2.0 | 197 | 2,423 | 0.08 | 0.08x |
| CL/HO_w120_z2.5 | -693 | 4,925 | -0.14 | 0.00x |
| GC/SI_w120_z2.0 | -1,018 | 3,714 | -0.27 | 0.00x |
| GC/SI_w60_z2.0 | -973 | 9,581 | -0.10 | 0.00x |
| GC/SI_w240_z2.0 | -1,264 | 1,545 | -0.82 | 0.00x |
| GC/SI_w120_z2.5 | -1,848 | 3,809 | -0.49 | 0.00x |
| POOL_w120_z2.0 | 621 | 48,450 | 0.01 | 0.01x |
| POOL_w60_z2.0 | 4,321 | 114,589 | 0.04 | 0.04x |
| POOL_w240_z2.0 | -580 | 19,843 | -0.03 | 0.00x |
| POOL_w120_z2.5 | -1,384 | 45,652 | -0.03 | 0.00x |

| cell | 2023 (Apr-Dec) | 2024 | 2025 | 2026 (5 wk) | pre-2025 half | post-2025 half | years ok | halves ok |
|---|---|---|---|---|---|---|---|---|
| ZN/ZB_w120_z2.0 | -26,616 [-29,339,-23,893] (3,891) | -31,443 [-34,184,-28,701] (3,917) | -30,875 [-33,639,-28,112] (3,948) | -27,929 [-35,033,-20,825] (10,149) | -29,397 | -31,103 | False | False |
| ZN/ZB_w60_z2.0 | -60,629 [-66,417,-54,842] (8,269) | -73,402 [-78,720,-68,083] (7,598) | -71,884 [-77,497,-66,270] (8,019) | -66,392 [-83,678,-49,105] (24,695) | -67,987 | -72,555 | False | False |
| ZN/ZB_w240_z2.0 | -10,096 [-11,373,-8,818] (1,825) | -12,192 [-13,572,-10,812] (1,971) | -12,312 [-13,428,-11,196] (1,594) | -12,715 [-15,376,-10,054] (3,801) | -11,303 | -12,566 | False | False |
| ZN/ZB_w120_z2.5 | -24,519 [-27,361,-21,677] (4,060) | -29,738 [-32,653,-26,823] (4,164) | -27,742 [-30,333,-25,150] (3,702) | -23,677 [-29,687,-17,668] (8,585) | -27,525 | -27,800 | False | False |
| CL/RB_w120_z2.0 | -3,415 [-5,103,-1,727] (2,411) | -4,678 [-6,495,-2,862] (2,595) | -6,890 [-8,368,-5,412] (2,111) | -2,765 [-8,283,2,753] (7,883) | -4,143 | -6,582 | False | False |
| CL/RB_w60_z2.0 | -9,854 [-12,369,-7,338] (3,593) | -10,327 [-12,509,-8,146] (3,117) | -14,937 [-16,765,-13,108] (2,612) | -11,379 [-22,203,-556] (15,462) | -10,127 | -14,826 | False | False |
| CL/RB_w240_z2.0 | -1,830 [-3,116,-544] (1,837) | -2,295 [-3,733,-857] (2,054) | -3,308 [-4,381,-2,234] (1,533) | -470 [-3,931,2,991] (4,944) | -2,098 | -3,071 | False | False |
| CL/RB_w120_z2.5 | -3,475 [-5,661,-1,289] (3,123) | -5,953 [-7,903,-4,003] (2,786) | -7,664 [-9,726,-5,603] (2,945) | -1,525 [-8,947,5,897] (10,603) | -4,903 | -7,161 | False | False |
| CL/HO_w120_z2.0 | -2,342 [-4,327,-356] (2,836) | -4,498 [-5,980,-3,017] (2,116) | -6,715 [-8,423,-5,007] (2,440) | -1,610 [-7,141,3,921] (7,902) | -3,584 | -6,303 | False | False |
| CL/HO_w60_z2.0 | -8,105 [-10,843,-5,367] (3,912) | -11,026 [-13,760,-8,291] (3,906) | -13,829 [-16,233,-11,425] (3,434) | -7,928 [-16,386,529] (12,082) | -9,788 | -13,457 | False | False |
| CL/HO_w240_z2.0 | -2,460 [-4,148,-772] (2,411) | -1,448 [-2,480,-416] (1,474) | -3,030 [-4,067,-1,994] (1,480) | -1,143 [-2,894,608] (2,501) | -1,877 | -2,887 | False | False |
| CL/HO_w120_z2.5 | -2,315 [-4,503,-128] (3,125) | -4,036 [-5,701,-2,371] (2,378) | -7,321 [-9,400,-5,242] (2,970) | -712 [-8,870,7,445] (11,653) | -3,306 | -6,764 | False | False |
| GC/SI_w120_z2.0 | -6,187 [-7,847,-4,527] (2,372) | -5,493 [-6,658,-4,328] (1,664) | -4,013 [-5,458,-2,568] (2,064) | -3,657 [-9,054,1,740] (7,710) | -5,787 | -4,045 | False | False |
| GC/SI_w60_z2.0 | -15,702 [-18,154,-13,249] (3,503) | -13,332 [-15,278,-11,387] (2,779) | -8,203 [-10,549,-5,857] (3,351) | -8,194 [-16,387,-0] (11,705) | -14,337 | -8,343 | False | False |
| GC/SI_w240_z2.0 | -1,479 [-2,605,-353] (1,609) | -2,645 [-3,587,-1,704] (1,345) | -2,484 [-3,443,-1,526] (1,369) | -4,090 [-7,685,-494] (5,136) | -2,151 | -2,693 | False | False |
| GC/SI_w120_z2.5 | -5,745 [-7,959,-3,532] (3,162) | -5,949 [-7,550,-4,348] (2,287) | -5,178 [-6,917,-3,439] (2,484) | -5,725 [-12,835,1,385] (10,157) | -5,863 | -5,324 | False | False |
| POOL_w120_z2.0 | -38,559 [-43,540,-33,578] (7,116) | -46,112 [-50,165,-42,059] (5,790) | -48,494 [-52,190,-44,797] (5,281) | -35,961 [-49,056,-22,865] (18,708) | -42,910 | -48,033 | False | False |
| POOL_w60_z2.0 | -94,290 [-102,813,-85,767] (12,176) | -108,087 [-114,764,-101,410] (9,538) | -108,852 [-116,058,-101,646] (10,295) | -93,894 [-127,391,-60,397] (47,853) | -102,238 | -109,181 | False | False |
| POOL_w240_z2.0 | -15,864 [-19,107,-12,621] (4,633) | -18,580 [-20,935,-16,225] (3,364) | -21,134 [-23,006,-19,262] (2,674) | -18,417 [-25,003,-11,831] (9,408) | -17,429 | -21,217 | False | False |
| POOL_w120_z2.5 | -36,055 [-41,546,-30,564] (7,845) | -45,675 [-49,931,-41,419] (6,080) | -47,905 [-52,420,-43,390] (6,450) | -31,640 [-47,391,-15,888] (22,502) | -41,597 | -47,048 | False | False |

| cell | trades (all scored) | gross $/trade | cost $/trade | worst trade | 1% / 5% trade | worst day | worst week | stop-exit share | stop-exit mean $ | non-stop mean $ | median lots (both legs) / p95 | median leg notional |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZN/ZB_w120_z2.0 | 2387 | 112 | 2,000 | -11,906 | -6,872 / -5,245 | -30,203 | -57,581 | 9% | -4,653 | -1,607 | 36.1 / 64 | 2,072,854 |
| ZN/ZB_w60_z2.0 | 4271 | 144 | 2,594 | -25,326 | -7,817 / -5,682 | -47,064 | -123,850 | 6% | -5,638 | -2,259 | 49.5 / 75 | 2,841,942 |
| ZN/ZB_w240_z2.0 | 1265 | 30 | 1,428 | -7,830 | -5,751 / -4,378 | -11,467 | -27,787 | 16% | -3,597 | -983 | 24.1 / 47 | 1,392,036 |
| ZN/ZB_w120_z2.5 | 1479 | 181 | 2,983 | -16,295 | -10,342 / -7,903 | -29,032 | -56,155 | 14% | -6,315 | -2,253 | 51.7 / 93 | 2,977,640 |
| CL/RB_w120_z2.0 | 2024 | 26 | 403 | -11,387 | -6,001 / -3,476 | -10,655 | -23,377 | 13% | -2,359 | -86 | 17.0 / 38 | 686,830 |
| CL/RB_w60_z2.0 | 3314 | 36 | 576 | -12,453 | -6,972 / -3,890 | -16,419 | -36,508 | 9% | -2,687 | -322 | 24.9 / 55 | 1,021,564 |
| CL/RB_w240_z2.0 | 1306 | 9 | 293 | -8,018 | -5,443 / -3,015 | -8,018 | -16,687 | 15% | -1,972 | 9 | 12.2 / 29 | 496,968 |
| CL/RB_w120_z2.5 | 1307 | -38 | 625 | -15,929 | -8,806 / -5,329 | -14,248 | -27,806 | 19% | -2,879 | -128 | 25.5 / 57 | 1,025,991 |
| CL/HO_w120_z2.0 | 1980 | -13 | 338 | -13,178 | -6,018 / -3,426 | -13,178 | -18,665 | 12% | -2,306 | -97 | 14.7 / 32 | 609,603 |
| CL/HO_w60_z2.0 | 3388 | -13 | 483 | -19,844 | -7,601 / -4,347 | -24,202 | -42,984 | 8% | -2,808 | -303 | 21.2 / 45 | 874,768 |
| CL/HO_w240_z2.0 | 1287 | -15 | 249 | -8,825 | -5,620 / -3,094 | -8,825 | -13,105 | 14% | -1,938 | 13 | 10.6 / 23 | 441,655 |
| CL/HO_w120_z2.5 | 1254 | -29 | 526 | -19,767 | -8,765 / -4,859 | -19,767 | -28,415 | 17% | -2,817 | -82 | 22.4 / 46 | 928,463 |
| GC/SI_w120_z2.0 | 1735 | -63 | 379 | -13,475 | -6,032 / -3,661 | -13,358 | -20,745 | 15% | -2,568 | -61 | 6.6 / 19 | 629,761 |
| GC/SI_w60_z2.0 | 3015 | -15 | 583 | -17,267 | -7,275 / -4,223 | -16,818 | -31,469 | 11% | -3,042 | -305 | 10.3 / 31 | 979,747 |
| GC/SI_w240_z2.0 | 1068 | -74 | 257 | -8,435 | -4,595 / -2,715 | -8,435 | -13,089 | 24% | -1,895 | 172 | 4.5 / 12 | 436,268 |
| GC/SI_w120_z2.5 | 1125 | -166 | 588 | -17,807 | -9,078 / -5,444 | -16,731 | -27,308 | 22% | -3,179 | -50 | 10.1 / 30 | 954,293 |
| POOL_w120_z2.0 | 8126 | 23 | 851 | -13,475 | -6,632 / -4,303 | -31,775 | -77,691 | 12% | -2,925 | -544 | 17.2 / 53 | 829,316 |
| POOL_w60_z2.0 | 13988 | 46 | 1,171 | -25,326 | -7,546 / -4,835 | -61,389 | -168,791 | 8% | -3,445 | -921 | 25.5 / 66 | 1,255,316 |
| POOL_w240_z2.0 | 4926 | -10 | 565 | -8,825 | -5,688 / -3,607 | -19,978 | -38,005 | 17% | -2,331 | -216 | 11.7 / 36 | 559,076 |
| POOL_w120_z2.5 | 5165 | -1 | 1,268 | -19,767 | -9,571 / -6,454 | -35,756 | -90,118 | 18% | -3,690 | -742 | 25.7 / 77 | 1,239,514 |

| cell | weekly corr to stack | $ in stack's worst-20 weeks (window) | $ in audit's worst-20 list (weeks <= 2026-02-06) | $ in stack loss slots | $ in idle slots | weeks<0 |
|---|---|---|---|---|---|---|
| ZN/ZB_w120_z2.0 | -0.03 | -600,712 | -479,170 | -1,487,520 | -978,512 | 149 |
| ZN/ZB_w60_z2.0 | +0.04 | -1,481,476 | -1,222,181 | -3,509,597 | -1,794,986 | 149 |
| ZN/ZB_w240_z2.0 | +0.03 | -257,745 | -198,825 | -399,316 | -717,729 | 149 |
| ZN/ZB_w120_z2.5 | -0.01 | -582,836 | -457,104 | -1,345,086 | -870,835 | 149 |
| CL/RB_w120_z2.0 | +0.15 | -116,291 | -80,959 | -169,924 | -119,305 | 120 |
| CL/RB_w60_z2.0 | +0.12 | -250,767 | -171,711 | -506,959 | -267,868 | 137 |
| CL/RB_w240_z2.0 | +0.07 | -64,013 | -52,350 | -20,469 | -148,409 | 108 |
| CL/RB_w120_z2.5 | +0.10 | -126,303 | -89,589 | -178,348 | -116,000 | 117 |
| CL/HO_w120_z2.0 | +0.02 | -128,594 | -94,769 | -202,670 | -114,868 | 117 |
| CL/HO_w60_z2.0 | +0.05 | -216,940 | -171,280 | -509,024 | -227,495 | 130 |
| CL/HO_w240_z2.0 | +0.04 | -78,208 | -59,659 | -77,705 | -106,394 | 104 |
| CL/HO_w120_z2.5 | +0.01 | -119,672 | -84,953 | -189,957 | -87,187 | 111 |
| GC/SI_w120_z2.0 | +0.00 | -110,137 | -100,079 | -202,068 | -233,915 | 126 |
| GC/SI_w60_z2.0 | +0.12 | -288,169 | -234,479 | -577,719 | -377,605 | 140 |
| GC/SI_w240_z2.0 | -0.11 | -28,302 | -23,681 | -31,685 | -182,948 | 108 |
| GC/SI_w120_z2.5 | +0.07 | -140,701 | -128,594 | -187,376 | -294,246 | 120 |
| POOL_w120_z2.0 | +0.06 | -955,735 | -754,977 | -2,062,182 | -1,446,600 | 148 |
| POOL_w60_z2.0 | +0.12 | -2,237,351 | -1,799,652 | -5,103,300 | -2,667,954 | 149 |
| POOL_w240_z2.0 | +0.03 | -428,267 | -334,516 | -529,176 | -1,155,480 | 147 |
| POOL_w120_z2.5 | +0.07 | -969,512 | -760,240 | -1,900,768 | -1,368,268 | 148 |

## G3 - laggard catch-up at 10:00 / 11:30 / 14:00 (F = 15)
| cell | tr/wk | WF $/wk [95% CI] (MDE) | HOLD $/wk [CI] (MDE) | X 2023-span $/wk [CI] (MDE) | WF 2x cost | (a) WF effect [CI] rank | (b) WF effect rank | tier | failed | R1/R2 |
|---|---|---|---|---|---|---|---|---|---|---|
| LAG1000_NQ/ES | 2.5 | -523 [-793,-253] (386) | -329 [-786,129] (653) | -248 [-645,149] (567) | -677 | -358 [-619,-90] r0.00 | -280 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| LAG1000_RTY/ES | 2.4 | -122 [-428,185] (438) | -202 [-670,267] (669) | -611 [-995,-227] (549) | -280 | -14 [-329,309] r0.47 | 56 r0.75 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| LAG1000_YM/ES | 2.4 | -332 [-597,-66] (379) | -361 [-938,215] (823) | -533 [-962,-104] (613) | -526 | -112 [-364,165] r0.17 | -169 r0.03 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| LAG1000_NQ/RTY | 2.5 | -214 [-457,30] (348) | -300 [-762,163] (661) | -436 [-771,-100] (480) | -293 | -135 [-385,119] r0.15 | -9 r0.42 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| LAG1000_ALL4 | 2.4 | -120 [-302,62] (260) | -303 [-658,52] (507) | -310 [-567,-52] (368) | -166 | -72 [-268,108] r0.23 | -26 r0.28 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| LAG1130_NQ/ES | 2.4 | -262 [-429,-96] (238) | -283 [-586,20] (432) | -87 [-302,128] (307) | -371 | -155 [-317,12] r0.07 | -16 r0.47 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| LAG1130_RTY/ES | 2.4 | -240 [-415,-65] (250) | -518 [-852,-183] (478) | -101 [-314,113] (304) | -334 | -141 [-309,17] r0.03 | -67 r0.17 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| LAG1130_YM/ES | 2.5 | -196 [-375,-17] (256) | -114 [-473,244] (512) | -482 [-750,-214] (383) | -330 | -76 [-250,97] r0.23 | -15 r0.40 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| LAG1130_NQ/RTY | 2.4 | -228 [-386,-71] (225) | -384 [-731,-37] (496) | -65 [-236,105] (244) | -284 | -183 [-360,-39] r0.00 | -28 r0.40 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| LAG1130_ALL4 | 2.4 | -175 [-292,-58] (167) | -304 [-546,-63] (345) | 7 [-115,128] (173) | -208 | -127 [-253,-8] r0.03 | -80 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,best_of_N | n/n |
| LAG1400_NQ/ES | 2.3 | -133 [-231,-35] (140) | -151 [-355,53] (291) | -133 [-261,-5] (184) | -216 | -42 [-141,64] r0.15 | 109 r1.00 | DEAD | mean_up,beats_a,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| LAG1400_RTY/ES | 2.4 | -38 [-164,88] (180) | -180 [-435,75] (364) | -8 [-187,171] (256) | -120 | 39 [-85,158] r0.72 | 138 r0.97 | DEAD | beats_a,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| LAG1400_YM/ES | 2.4 | -144 [-241,-47] (139) | -123 [-292,46] (241) | -213 [-322,-105] (155) | -249 | -34 [-130,67] r0.17 | 40 r0.75 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| LAG1400_NQ/RTY | 2.3 | -116 [-238,6] (174) | -220 [-484,44] (377) | -86 [-204,32] (168) | -162 | -82 [-202,32] r0.12 | 76 r0.88 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| LAG1400_ALL4 | 2.3 | -71 [-145,3] (105) | -125 [-286,37] (231) | -52 [-132,27] (114) | -98 | -41 [-116,34] r0.15 | 17 r0.65 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| POOL_LAG1000 | 9.8 | -1,190 [-1,839,-541] (927) | -1,192 [-2,415,31] (1,747) | -1,827 [-2,748,-906] (1,316) | -1,777 | -618 [-1,259,37] r0.03 | -402 r0.00 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| POOL_LAG1130 | 9.7 | -927 [-1,388,-465] (659) | -1,299 [-2,160,-438] (1,230) | -734 [-1,322,-147] (839) | -1,320 | -556 [-1,038,-110] r0.00 | -126 r0.10 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N | n/n |
| POOL_LAG1400 | 9.5 | -431 [-738,-124] (439) | -674 [-1,280,-69] (865) | -440 [-808,-73] (525) | -747 | -118 [-435,206] r0.17 | 364 r1.00 | DEAD | mean_up,beats_a,cost2x_pre,year_share,hold,span2 | n/n |

| cell | gross $/wk (WF) | cost $/wk (WF) | gross/cost | net break-even cost multiple |
|---|---|---|---|---|
| LAG1000_NQ/ES | -369 | 154 | -2.39 | 0.00x |
| LAG1000_RTY/ES | 36 | 158 | 0.23 | 0.23x |
| LAG1000_YM/ES | -137 | 195 | -0.70 | 0.00x |
| LAG1000_NQ/RTY | -134 | 79 | -1.69 | 0.00x |
| LAG1000_ALL4 | -74 | 46 | -1.60 | 0.00x |
| LAG1130_NQ/ES | -153 | 109 | -1.41 | 0.00x |
| LAG1130_RTY/ES | -147 | 94 | -1.57 | 0.00x |
| LAG1130_YM/ES | -62 | 134 | -0.46 | 0.00x |
| LAG1130_NQ/RTY | -172 | 56 | -3.09 | 0.00x |
| LAG1130_ALL4 | -141 | 34 | -4.20 | 0.00x |
| LAG1400_NQ/ES | -50 | 83 | -0.60 | 0.00x |
| LAG1400_RTY/ES | 44 | 82 | 0.53 | 0.53x |
| LAG1400_YM/ES | -38 | 106 | -0.36 | 0.00x |
| LAG1400_NQ/RTY | -70 | 46 | -1.54 | 0.00x |
| LAG1400_ALL4 | -44 | 27 | -1.60 | 0.00x |
| POOL_LAG1000 | -603 | 587 | -1.03 | 0.00x |
| POOL_LAG1130 | -534 | 393 | -1.36 | 0.00x |
| POOL_LAG1400 | -115 | 316 | -0.36 | 0.00x |

| cell | 2023 (Apr-Dec) | 2024 | 2025 | 2026 (5 wk) | pre-2025 half | post-2025 half | years ok | halves ok |
|---|---|---|---|---|---|---|---|---|
| LAG1000_NQ/ES | -260 [-663,143] (576) | -687 [-1,101,-274] (591) | -284 [-647,80] (519) | -784 [-1,550,-19] (1,093) | -506 | -340 | False | False |
| LAG1000_RTY/ES | -538 [-920,-157] (545) | -176 [-619,268] (633) | -205 [-653,243] (640) | 226 [-576,1,027] (1,145) | -329 | -164 | False | False |
| LAG1000_YM/ES | -416 [-885,53] (670) | -476 [-837,-116] (515) | -283 [-625,60] (489) | -356 [-2,408,1,696] (2,931) | -451 | -295 | False | False |
| LAG1000_NQ/RTY | -447 [-815,-79] (526) | -339 [-674,-4] (479) | -129 [-481,224] (503) | 65 [-465,596] (758) | -385 | -111 | False | False |
| LAG1000_ALL4 | -317 [-597,-38] (399) | -87 [-314,140] (324) | -154 [-419,111] (378) | -203 [-1,411,1,004] (1,725) | -185 | -162 | False | False |
| LAG1130_NQ/ES | -99 [-299,101] (286) | -315 [-557,-74] (345) | -225 [-472,22] (353) | 142 [-317,600] (655) | -224 | -190 | False | False |
| LAG1130_RTY/ES | -82 [-305,141] (319) | -180 [-437,77] (367) | -294 [-541,-48] (352) | -255 [-552,43] (425) | -139 | -295 | False | False |
| LAG1130_YM/ES | -558 [-841,-276] (404) | -337 [-573,-101] (337) | -20 [-270,229] (356) | -215 [-1,265,836] (1,501) | -431 | -41 | False | False |
| LAG1130_NQ/RTY | -42 [-225,140] (261) | -186 [-385,13] (284) | -269 [-514,-24] (350) | -217 [-638,204] (601) | -125 | -269 | False | False |
| LAG1130_ALL4 | 18 [-106,141] (176) | -159 [-292,-25] (191) | -177 [-371,18] (278) | -192 [-555,172] (519) | -84 | -181 | False | False |
| LAG1400_NQ/ES | -157 [-292,-22] (192) | -71 [-171,28] (142) | -207 [-374,-39] (239) | 154 [-112,420] (380) | -108 | -173 | False | False |
| LAG1400_RTY/ES | 26 [-169,220] (278) | -33 [-149,84] (166) | -65 [-287,157] (317) | -36 [-448,377] (590) | -8 | -63 | True | False |
| LAG1400_YM/ES | -225 [-343,-107] (169) | -166 [-300,-31] (192) | -130 [-263,2] (190) | -28 [-529,472] (715) | -191 | -122 | False | False |
| LAG1400_NQ/RTY | -84 [-210,42] (180) | -11 [-112,90] (144) | -222 [-441,-3] (313) | -80 [-425,266] (494) | -42 | -211 | False | False |
| LAG1400_ALL4 | -47 [-132,38] (121) | -32 [-89,24] (81) | -129 [-264,6] (193) | 96 [-86,277] (259) | -39 | -108 | True | False |
| POOL_LAG1000 | -1,662 [-2,650,-673] (1,412) | -1,678 [-2,605,-751] (1,324) | -900 [-1,820,20] (1,314) | -850 [-3,216,1,517] (3,381) | -1,671 | -910 | False | False |
| POOL_LAG1130 | -782 [-1,379,-184] (853) | -1,018 [-1,671,-365] (933) | -808 [-1,465,-151] (939) | -545 [-2,499,1,410] (2,792) | -918 | -795 | False | False |
| POOL_LAG1400 | -440 [-837,-43] (567) | -281 [-586,25] (436) | -624 [-1,158,-91] (762) | 11 [-551,572] (802) | -348 | -569 | False | False |

| cell | trades (all scored) | gross $/trade | cost $/trade | worst trade | 1% / 5% trade | worst day | worst week | stop-exit share | stop-exit mean $ | non-stop mean $ | median lots (both legs) / p95 | median leg notional |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LAG1000_NQ/ES | 365 | -116 | 66 | -1,459 | -1,306 / -1,212 | -1,459 | -4,473 | 32% | -1,136 | 257 | 2.1 / 4 | 363,712 |
| LAG1000_RTY/ES | 367 | -42 | 67 | -2,631 | -1,418 / -1,200 | -2,631 | -5,326 | 34% | -1,170 | 446 | 2.9 / 5 | 229,058 |
| LAG1000_YM/ES | 364 | -70 | 91 | -1,445 | -1,366 / -1,261 | -1,445 | -4,418 | 33% | -1,171 | 336 | 3.4 / 6 | 400,722 |
| LAG1000_NQ/RTY | 367 | -82 | 32 | -1,296 | -1,247 / -1,113 | -1,296 | -4,229 | 28% | -1,086 | 265 | 1.9 / 3 | 147,292 |
| LAG1000_ALL4 | 365 | -52 | 20 | -1,445 | -1,117 / -1,055 | -1,445 | -3,543 | 12% | -1,070 | 58 | 1.2 / 2 | 108,543 |
| LAG1130_NQ/ES | 361 | -42 | 46 | -1,152 | -1,135 / -1,086 | -1,152 | -2,817 | 10% | -1,093 | 24 | 1.7 / 3 | 280,086 |
| LAG1130_RTY/ES | 358 | -44 | 40 | -1,352 | -1,136 / -1,072 | -1,352 | -3,105 | 8% | -1,098 | 9 | 1.9 / 3 | 147,889 |
| LAG1130_YM/ES | 368 | -49 | 65 | -1,352 | -1,241 / -1,109 | -1,352 | -3,820 | 10% | -1,140 | 1 | 2.6 / 5 | 316,294 |
| LAG1130_NQ/RTY | 362 | -52 | 22 | -1,227 | -1,097 / -1,036 | -1,227 | -3,001 | 6% | -1,080 | -13 | 1.4 / 2 | 115,305 |
| LAG1130_ALL4 | 360 | -36 | 14 | -1,144 | -1,051 / -596 | -1,144 | -1,653 | 2% | -1,064 | -33 | 0.9 / 1 | 80,316 |
| LAG1400_NQ/ES | 349 | -20 | 37 | -1,110 | -1,070 / -578 | -1,110 | -1,881 | 1% | -1,088 | -42 | 1.5 / 2 | 218,033 |
| LAG1400_RTY/ES | 355 | 23 | 35 | -1,347 | -928 / -592 | -1,347 | -2,103 | 1% | -1,195 | -2 | 1.7 / 3 | 135,011 |
| LAG1400_YM/ES | 352 | -20 | 50 | -1,151 | -876 / -546 | -1,151 | -1,926 | 1% | -1,146 | -64 | 2.3 / 4 | 268,311 |
| LAG1400_NQ/RTY | 350 | -27 | 19 | -1,141 | -1,047 / -582 | -1,141 | -2,050 | 2% | -1,075 | -28 | 1.2 / 2 | 100,374 |
| LAG1400_ALL4 | 341 | -16 | 13 | -1,141 | -516 / -346 | -1,141 | -1,621 | 0% | -1,141 | -25 | 0.8 / 1 | 71,739 |
| POOL_LAG1000 | 1463 | -77 | 64 | -2,631 | -1,327 / -1,211 | -5,378 | -10,991 | 32% | -1,143 | 324 | 2.5 / 5 | 269,168 |
| POOL_LAG1130 | 1449 | -47 | 43 | -1,352 | -1,159 / -1,083 | -4,311 | -8,387 | 9% | -1,106 | 5 | 1.8 / 4 | 198,013 |
| POOL_LAG1400 | 1406 | -11 | 35 | -1,347 | -1,030 / -573 | -3,629 | -5,664 | 1% | -1,111 | -34 | 1.6 / 3 | 176,584 |

| cell | weekly corr to stack | $ in stack's worst-20 weeks (window) | $ in audit's worst-20 list (weeks <= 2026-02-06) | $ in stack loss slots | $ in idle slots | weeks<0 |
|---|---|---|---|---|---|---|
| LAG1000_NQ/ES | -0.18 | -1,529 | -3,039 | 0 | 0 | 87 |
| LAG1000_RTY/ES | -0.01 | -992 | -2,392 | 0 | 0 | 76 |
| LAG1000_YM/ES | -0.00 | -11,214 | -8,195 | 0 | 0 | 88 |
| LAG1000_NQ/RTY | +0.04 | -5,989 | -8,330 | 0 | 0 | 82 |
| LAG1000_ALL4 | -0.03 | -948 | -907 | 0 | 0 | 77 |
| LAG1130_NQ/ES | -0.16 | -2,895 | -1,879 | -31,621 | 0 | 85 |
| LAG1130_RTY/ES | +0.02 | -4,496 | -3,283 | -29,881 | 0 | 83 |
| LAG1130_YM/ES | -0.01 | -5,915 | -4,100 | -41,982 | 0 | 95 |
| LAG1130_NQ/RTY | +0.01 | -2,803 | -2,718 | -27,062 | 0 | 82 |
| LAG1130_ALL4 | -0.15 | 27 | -60 | -18,235 | 0 | 90 |
| LAG1400_NQ/ES | -0.09 | -668 | -1,338 | 0 | 0 | 90 |
| LAG1400_RTY/ES | +0.08 | -1,297 | -679 | 0 | 0 | 72 |
| LAG1400_YM/ES | -0.01 | -2,958 | -2,930 | 0 | 0 | 98 |
| LAG1400_NQ/RTY | +0.06 | -2,621 | -1,971 | 0 | 0 | 82 |
| LAG1400_ALL4 | -0.02 | -75 | -211 | 0 | 0 | 82 |
| POOL_LAG1000 | -0.06 | -19,723 | -21,956 | 0 | 0 | 98 |
| POOL_LAG1130 | -0.06 | -16,109 | -11,980 | -130,545 | 0 | 102 |
| POOL_LAG1400 | +0.02 | -7,544 | -6,918 | 0 | 0 | 94 |

The placebo-(a) effect equals the GROSS edge of the rule (random-sign draws average minus the cost). Its sign is negative for the catch-up direction, in WFPRE, WF and HOLD:
| row | (a) gross effect WFPRE | WF [CI] | HOLD | HOLD rank |
|---|---|---|---|---|
| LAG1000_NQ/ES | -423 | -358 [-619,-90] | -193 | 0.20 |
| LAG1000_RTY/ES | 40 | -14 [-329,309] | -139 | 0.35 |
| LAG1000_YM/ES | -107 | -112 [-364,165] | -119 | 0.30 |
| LAG1000_NQ/RTY | -108 | -135 [-385,119] | -195 | 0.10 |
| LAG1000_ALL4 | -0 | -72 [-268,108] | -237 | 0.07 |
| LAG1130_NQ/ES | -155 | -155 [-317,12] | -151 | 0.12 |
| LAG1130_RTY/ES | -18 | -141 [-309,17] | -427 | 0.03 |
| LAG1130_YM/ES | -109 | -76 [-250,97] | 3 | 0.47 |
| LAG1130_NQ/RTY | -107 | -183 [-360,-39] | -355 | 0.03 |
| LAG1130_ALL4 | -77 | -127 [-253,-8] | -239 | 0.00 |
| LAG1400_NQ/ES | -42 | -42 [-141,64] | -40 | 0.35 |
| LAG1400_RTY/ES | 104 | 39 [-85,158] | -113 | 0.20 |
| LAG1400_YM/ES | -37 | -34 [-130,67] | -25 | 0.28 |
| LAG1400_NQ/RTY | -26 | -82 [-202,32] | -209 | 0.05 |
| LAG1400_ALL4 | -16 | -41 [-116,34] | -98 | 0.07 |
| POOL_LAG1000 | -598 | -618 [-1,259,37] | -646 | 0.07 |
| POOL_LAG1130 | -389 | -556 [-1,038,-110] | -930 | 0.00 |
| POOL_LAG1400 | -2 | -118 [-435,206] | -388 | 0.03 |

## Spread-trend blow-ups (worst trade and tail)
The MR book has the classic profile: the non-stop exits (z = 0 or the 15:55 flat) average +$270 to +$800 per trade at windows 120 and 240 (and -$50 to -$340 at 60 minutes) while the stop exits lose $1,300-$2,900 on the index and commodity pairs (1.3-2.9 R; the excess over 1R is the 2-tick stop slippage on two legs and next-open execution through a close-based stop) and $3,600-$6,300 on ZN/ZB, with 24-32 percent of trades stopping on the index pairs at the primary window 120 (11-14 percent at 60, 41-46 percent at 240). Worst single trades are -$12k to -$25k (12-25 R) on the primary and 60-minute variants of every pair: e.g. RTY/ES 2025-07-01 (entered 09:53, stopped 11:57, -$12.8k, the first HOLD day), NQ/RTY the same day (-$13.5k), NQ/ES 2024-08-19 (entered 12:54 and held to the 15:55 flat, -$12.8k: a one-sided afternoon drift, no stop in time), YM/ES 2024-03-22 (-$12.0k), CL/RB 2024-02-01 (-$11.4k), GC/SI 2024-10-18 (-$13.5k), CL/HO 2025-05-21 (-$13.2k, entered 10:03 and held to a 15:29 z = 0 exit). Worst weeks reach -$15k to -$21k on one index pair at the primary cell and -$44k at 60 minutes (YM/ES), at $1,000 per trade (-$47k pooled primary index, -$78k pooled commodity/rate primary; ZN/ZB alone -$58k). Fractional-lot sizes are large: the primary NQ/ES cell trades about 11 contracts (both legs) with $1.7M per leg, ZN/ZB 36 contracts and $2.1M per leg, so the cost line, not the signal, sets the answer.

## Why it fails (mechanism, descriptive)
1. Cost scale: round-trip fees plus 1-tick slippage on two legs are 1.5-2.6 bp of leg notional on index pairs (4.6-5.1 bp CL/RB, CL/HO, GC/SI; 9 bp ZN/ZB) against a 4-14 bp stop distance and a 2-sigma reversion target of about 8-28 bp; break-even would need the gross edge to be 2.4x larger on RTY/ES (gross/cost 0.42, the best), and a positive gross edge at all on the other index pairs (gross/cost <= 0.05 or negative) and the commodity/rate pairs (<= 0.06).
2. Selection against extremes: placebo (b), fading at RANDOM times of the same days with the same exits, scores BETTER than the real |z| >= 2 rule in every MR cell (rank <= 0.05, effect -$0.5k to -$44k/wk): a 2-sigma deviation of a 2-hour ratio is more often the start of a drift (stopped 24-47 percent of the time) than an overshoot, and it concentrates entries at the cash open: 46-55 percent of the primary-cell index trades are entered between 09:35 and 10:00 (15-25 percent on the commodity/rate pairs), where the ratio jump between the overnight session and the cash open is not a deviation, and 41-49 percent of those early index trades are stopped (mean -$220 to -$500 per trade, against -$160 to -$370 for the later ones, so dropping the open would not rescue the book).
3. The 'tight' variants (60 minute) trade 2x more and lose 2x more; the 240 minute and 2.5 sigma variants lose less only because they trade less.

## Lead (post hoc, NOT a result; for the queue)
The laggard catch-up has the opposite sign of its mechanism: relative strength from the open continues (leader keeps leading), gross +$14 to +$358/wk per index pair at 10:00 and 11:30 in WF, pooled 11:30 +$556/wk [110, 1,038] in WF and +$930/wk in HOLD (rank 0.00 of the random-sign draws, i.e. the continuation direction beats all draws), against a pooled cost of about $370-$490/wk at the same sizes, so a continuation-at-clock book (long the leader / short the laggard at 10:00 and 11:30) would be about +$0.2-0.5k/wk net per $1,000 risk at pooled size, inside per-pair MDEs (per-pair MDE $240-$450). It was found by inverting this group's own sign after seeing WF and HOLD, so the HOLD number is NOT a clean confirmation: a continuation book needs its own prereg (<= 6 cells: clocks 10:00/11:30 x pairs pooled or ALL4), selection on WFPRE only, and the 2023 span as its only unread window (X (a) effect was not computed here). Not run (outside this prereg; gates not loosened). MORNING.md question: allow a 6-cell prereg for 'relative-strength continuation', accepting that WF and HOLD were already seen at the group level.

## Disclosures
- One logged holdout look per group (G1, G2, G3), after the WFPRE-only texts; all cells were simulated for all days at once but only WFPRE was scored before the look (PRE stage printed WFPRE only).
- Counts, cost per trade, sigma / stop distance (bp) and stop-exit share per variant were inspected BEFORE the prereg (counts.py, counts2.py, counts3.py); no P&L was computed or printed then. The stop-exit share is an outcome-adjacent statistic; it did not change any cell.
- Bug fixed before any scoring: the seed helper rng_for used zlib.crc32 on a str (TypeError on the first run of dv2b_run.py, no results written); fixed to .encode(); no result was produced under the old code.
- G1 pairs share legs (ES in three, NQ and RTY in two), so POOL rows are one book, not four independent tests; the replication count (3 of 4) is therefore weaker evidence than it looks.
- WEAK fees on RTY, YM, CL, GC, ZN, ZB, RB, HO, SI (ES proxy $4.84); ZN/ZB real fees are lower, but the 1-tick slippage (1/64 and 1/32 point) dominates its cost, so the verdict does not depend on the fee proxy. ZN/ZB is dollar-neutral as the directive says, not DV01-neutral.
- Stop and z tests use 1-min closes; stop-fill quality at news prints (EIA 10:30, Treasury auctions, FOMC) is not modeled beyond 2 ticks per leg (no print-level data for YM/RB/HO/SI/ZB; tick files exist for ES/RTY/CL/GC/ZN but were not used).
- Stack worst-20 weeks: weeks after ISO 2026-W06 are not read (4 of the audit's 20 fall after 2026-02-06); the table gives both the 20 lowest stack weeks inside the window and the audit's list restricted to the window. Weekly correlations use the 149 stack weeks 2023-W14..2026-W06 (candidate zero in weeks without trades).
- Selection decisions: none needed (fixed parameter sets, no cell dropped); every cell got its holdout look.
- Compute: 3 worker processes, well inside the 4-core / 32 GB gates.

## Hand-back numbers
- Verdict table: see 'Verdict' (47 cells, 0 PASS, 0 CANDIDATE, 47 DEAD; 0 variants replicate; 0 CONFIRMED).
- $ in the stack's 20 worst weeks (window), at $1,000 risk per trade, pooled primary books: index MR (w120 z2.0) -$321k, commodity/rate MR -$956k, laggard 10:00 -$20k, 11:30 -$16k, 14:00 -$8k; the least-bad single cells: LAG1400_ALL4 -$75, LAG1130_ALL4 +$27, LAG1000_ALL4 -$948.
- Weekly correlation to the live stack: -0.18..+0.22 on every cell (pooled primary index MR -0.01, commodity/rate +0.06), i.e. neutral as designed, but with a negative mean there is nothing to add.
