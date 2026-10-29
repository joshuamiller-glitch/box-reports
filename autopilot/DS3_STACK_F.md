# DS3 T-STACK F - combine (D3SKF)

**Verdict: CANDIDATE (not PASS). Admitted set A06 + HM5 REPL + B02 (D_L40s rejected at the HOLD look; B1_CONS2 had PRE d_mean < 0 and was never stacked). Failed gates: F6 (HOLD mean CI includes 0), F7 (best-of-F), F8 (no admitted rule passed its own section: A06 DEAD, B02 DEAD, HM5 LEAD).**

prereg `l2vast/ds3/prereg/STK_F_prereg.md` sha256 392cad1b74b0583a9e39827d9dea708697aebbe15ae6f9624ec589c14a882df1; PREHOLD `autopilot/DS3_STACK_F_PREHOLD.md` sha256 885917b4dec7a664412c9c09738ddf4766008f82257d13e227452b47f29d67b0; one HOLD+X look (track STK_F, hold-look log); F = 95 section cells + <=5 combination steps = 100. Label days <= 2026-02-06 only; weekly dollars at the 10-lot scale.

Plain sentence: **these rules would have turned the worst 20 weeks (fixed all-window set, 149 label weeks) from -$3,534,170 to -$2,502,987 (+$1,031,183) and cost $6,629/wk in the other 129 weeks.** The whole-span mean change is +$1,182/wk (MDE 16,545, CI -10,671..+13,005): the tail is cut and the mean is statistically unchanged, but HOLD (-$10,264/wk, MDE 34,726) and the 2023 span (-$8,790/wk, MDE 23,298) lose mean; the PRE gain (+$13,218/wk, MDE 25,631) is what carries WF (+$6,129, MDE 20,857). Nothing in the mean is distinguishable from zero.

Caveats (disclosed, not softened): (1) the stack weekly vector adds measured-on-unchanged-stack deltas (A06 engine, HM5 trade-level swap, B02 trade level); overlap is APPROXIMATE, B02 x HM5 is exact at trade level. (2) A06 halves 24% of entries (volume cut), so part of the tail gain is a lot cut, not selection; no lot-matched version was run here (section A: A06 LM rank 0.465, DEAD). (3) HM5 trade-level swap PRE +2,681/wk vs engine-level fixed +2,315/wk (see reconciliation). (4) The directive's entry condition (only cells that pass A-E individually) was not met by any rule; F ran on best-lead-per-section as declared in the prereg.

## HM5 PRE reconciliation (+2,315 vs +1,138)
`stke_lib.stack_parts` assigns `WDAY[nm]=WDAY[b]*wm` in place. MIX gets leg weights 0.5/0.25 and each MIX/LM call leaves WDAY[HM] scaled for every later cell of the process (mean 1.000 -> 0.500 after HM3 -> 0.346 at HM5). Replaying E's order (D then M basis per cell) reproduces HM5 +1,138 exactly, and also KB10 -2,250, PE15 -855, ST5 -7,805, HM3 -2,992 from E's table. Fresh process, base first, fixed: base 41,912 (live HM on the direct basis; official 44,127), HM5 REPL +2,314.9, MIX +1,157.5 (E reported -553), ADD +6,858.7. Consequence: section E REPL/MIX/ADD/LM numbers and gates for every cell except KB5 (the first) are corrupt; DS3_STACK_E.md is NOT edited; HM5's REPL sign on PRE stays positive but magnitudes, HOLD and 2023 columns need a rerun with `code/stk_f/f_fix_stke.py` (a corrected stack_parts). The sealed extract used here was taken in a fresh process before any variants() call and is clean.

## Standalone (unchanged stack, paired by week; d_mean $/wk (MDE); delta on worst-quintile of the base within the window)
| rule | PRE | HOLD | X (2023 span) | HOLD worst-quintile $ |
|---|---|---|---|---|
| A03 | +1,923 (3,168) | +4,124 (5,410) | -804 (2,754) | +27,005 |
| A06 | +10,563 (12,104) | -4,378 (15,304) | -9,764 (12,475) | +121,701 |
| B02 | +514 (5,947) | +955 (8,813) | +3,377 (7,873) | +62,529 |
| D40 | +2,197 (6,417) | +172 (5,690) | -5,670 (7,026) | +12,314 |
| C1 | -6,811 (10,613) | -1,153 (17,810) | -5,859 (10,279) | +204,681 |
| HM5R | +2,681 (19,962) | -4,456 (25,181) | -3,858 (18,099) | +272,664 |
| HM5M | +1,340 (9,981) | -2,228 (12,591) | -1,929 (9,049) | +136,332 |

Section picks (PRE d_mean): {'A': 'A06', 'B': 'B02', 'C': 'C1', 'D': 'D40', 'E': 'HM5R'}; stack order A06, HM5R, D40, B02 (C1 PRE -6,811, not stacked; A03 lost to A06 on PRE; HM5M lost to HM5R).

## Admission at the HOLD look (HOLD = 32 weeks, W20F weeks inside HOLD = 4)
| step | HOLD worst-quintile $ before -> after | HOLD W20F $ before -> after | HOLD mean increment (MDE) | admitted |
|---|---|---|---|---|
| A06 | +0 -> +121,701 | -914,949 -> -848,650 | -4,378 (15,304) | yes |
| HM5R | +121,701 -> +394,365 | -848,650 -> -740,512 | -4,456 (25,181) | yes |
| D40 | +394,365 -> +406,678 | -740,512 -> -757,307 | +172 (5,690) | NO (W20F in HOLD gets worse) |
| B02 | +394,365 -> +441,310 | -740,512 -> -694,136 | -1,430 (6,409) | yes |

## Stack A06 + HM5R + B02 vs unchanged stack
| window | n wk | mean base -> stack | SD base -> stack | maxDD base -> stack | worst wk base -> stack | d_mean (MDE) [95% CI] | worst-quintile d | W20F $ base -> stack |
|---|---|---|---|---|---|---|---|---|
| PRE | 74 | 43,808 -> 57,026 | 132,383 -> 106,229 | 409,229 -> 224,737 | -306,664 -> -200,826 | +13,218 (25,631) [-4,716,+31,385] | +1,357,288 | -1,490,274 -> -765,710 (n=8) |
| HOLD | 32 | 53,670 -> 43,406 | 153,219 -> 124,661 | 578,442 -> 512,198 | -318,557 -> -325,947 | -10,264 (34,726) [-34,335,+13,153] | +441,310 | -914,949 -> -694,136 (n=4) |
| X | 43 | 21,762 -> 10,747 | 113,859 -> 92,784 | 460,909 -> 403,212 | -157,300 -> -205,338 | -11,015 (24,950) [-28,522,+5,833] | +229,066 | -1,128,947 -> -1,043,141 (n=8) |
| WF | 106 | 46,785 -> 52,914 | 138,333 -> 111,683 | 578,442 -> 512,198 | -318,557 -> -325,947 | +6,129 (20,857) [-8,620,+20,258] | +1,715,693 | -2,405,223 -> -1,459,846 (n=12) |
| ALL | 149 | 39,564 -> 40,745 | 131,851 -> 107,980 | 578,442 -> 512,198 | -318,557 -> -325,947 | +1,182 (16,545) [-10,670,+13,005] | +1,922,505 | -3,534,170 -> -2,502,987 (n=20) |

By year:
| year | n | d_mean (MDE) | worst-quintile d | worst wk base -> stack |
|---|---|---|---|---|
| 2023 | 39 | -8,790 (23,298) | +85,807 | -157,300 -> -205,338 |
| 2024 | 52 | +12,610 (29,993) | +993,143 | -306,664 -> -200,826 |
| 2025 | 52 | -3,424 (30,376) | +657,394 | -318,557 -> -325,947 |
| 2026 | 6 | +6,864 (100,947) | +53,853 | -185,098 -> -118,303 |

## Placebo (3 random-placement rules, each delta permuted within the evaluated window, 200 draws)
| statistic | observed | placebo mean | placebo p95 | rank |
|---|---|---|---|---|
| PRE_W20P | +1,415,268 | +283,213 | +812,311 | 1.000 |
| HOLD_Q | +441,310 | -62,496 | +172,382 | 1.000 |
| X_Q | +229,066 | -97,690 | +146,115 | 0.980 |

Permutation keeps each rule's total, so the rank tests whether the rules land on the bad weeks; the PRE rank is in-sample for the rules (each was chosen on PRE in its own section). HOLD rank 1.000 and X 0.980 are the out-of-sample evidence. HOLD mean bootstrap P(d<=0) = 0.794; best-of-F (F=100) p = 1.000.

## Gates
| gate | result |
|---|---|
| F1 admitted set non-empty, WF d_mean >= -MDE | pass (+6,129 vs -20,857) |
| F2 HOLD worst-quintile > 0, HOLD W20F > 0, HOLD mean >= -MDE | pass (+441,310; +220,813 on 4 weeks; -10,264 vs -34,726) |
| F3 PRE W20P delta > 0 | pass (+1,415,268; in-sample) |
| F4 placebo rank >= 0.95 PRE and HOLD | pass (1.000 / 1.000) |
| F5 X d_mean >= -MDE and X worst-quintile > 0 | pass (-11,015 vs -24,950; +229,066) |
| F6 HOLD mean CI lower bound > 0 | FAIL ([-34,335, +13,153]) |
| F7 best-of-F p <= 0.05 | FAIL (1.000) |
| F8 admitted rules each PASS/CANDIDATE in own section | FAIL (A06 DEAD, B02 DEAD, HM5 LEAD) |

CANDIDATE per prereg (F1,F2,F3,F5 pass; F4 passes; F6,F7,F8 fail). It is a tail-risk layer with no demonstrated mean gain, and HOLD and 2023 mean are both negative. Not a PASS.

Never-empty-handed: best single rule by HOLD worst-quintile is HM5R (+272,664, HOLD mean -4,456, MDE 25,181) then C1 (+204,681, HOLD -1,153, MDE 17,810, but PRE mean -6,811). Files: out `l2vast/ds3/out/stk_f/{pre,final}.json`; code `l2vast/ds3/code/stk_f/{f_lib,f_run,f_fix_stke}.py`.
