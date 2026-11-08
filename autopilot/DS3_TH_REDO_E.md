# DS3_TH_REDO_E - program E (loss x profit combined), REPLICA engine, 2023-04..2026-10 (TH-E, 2026-11-08)
**cut-input agreement with live: 14% at 0% false (best FIT-selected convention) / literal reading 45 of 92 within +-2 s with 23 false; engine Gate 0 NOT passed; PRE-PROOF**

No PASS claims, research only, nothing live, no policy-file change. Prereg E a32a651d + ADOPTION fb6d42b6 + ROBUST 95ff9a48 + REPLICA 07f947b4; each choice was logged in DECISIONS.md before the numbers it affects. Windows as of 2026-10-30; deltas are USD/week, paired against HOLD (live cell: L2 loss cut, empty profit side) on the same replica, 14 live units, carrying week dropped (nodrop columns beside).

## Plain result
1. No combination qualifies; nothing goes to MORNING.md. Ten combinations were carried to all 43 months. None clears the family test (best p_family 0.28), the purged walk-forward is not positive (p 0.83), every delta is below its own MDE (L6M MDE 3.5k-13k vs deltas 1k-8k), and none clears the fragile-cut cap.
2. Combining helps only where the loss side already helps. On L6M the ten combos beat both of their components (that was the staging rule), but against the additive prediction (loss-only + profit-only) the interaction is +0.0k to +4.1k on L6M and -2.7k to +0.3k on PRE. The L6M gain is concentrated: the top 3 weeks carry 0.7x to 3.2x of the L6M total. The profit side adds nothing robust: C3 lock and C5 iceberg stay recent-only (PRE -2.0k and -2.2k alone), D time-decay is below 0.6k/week.
3. Closest: A:P10 + D:F07 / D:F08 (L6M +8.0k / +7.3k, PRE +5.4k / +5.1k, recents and drawdown-first pass) but the tolerant gate FAILS (X' -4.1k / -3.8k), family p 0.28 / 0.32, and P10 itself is NEGATIVE on the 8 tape days under the literal reading and all three FIT conventions (literal -4.9k, robust-only -6.0k), so it fails the convention test. B:F07 + C4 (L6M +3.9k, PRE +4.6k; recents, tolerant and drawdown-first all pass) is the only combo passing all three deterministic gates, but family p 0.71, B:F07 fragile share 1.08 in dollars (cap 0.30) and its top-3-week share of L6M is 2.65.
4. Combining does not add fragility, it inherits it: A:P10 fails the convention/robust test, B:F07 fragile 0.26 by count / 1.08 by dollars, D rules 5-17x (cap 0.30), C rules were scored on the literal reading only. A combined rule carries the worst component.
5. Held-out blind week (replica headline, HOLD 201 trades +55,890): A:P10+D:F07 170 trades +63,545 (+7.7k); A:P10+D:F08 +61,555 (+5.7k); B:F07+C4 +56,035 (+0.1k). The loss rule alone did better in each case (A:P10 +66,120, B:F07 +63,010): adding the profit rule cost 2.6k, 4.6k and 7.0k. The blind week overlaps the L1M window, so this is a consistency check, not new evidence; the comparison of the cut/take list with the 187 live trades was not made (counts only: 51-71 loss exits).
6. Plain 60/60 and loss-only references: loss-only (A:P10, B:F07) already carries almost all of the benefit. Plain 60/60 (no TH of any kind) was not re-run on the replica (E0 references not scored).

## What was run
- Constituents (rule logged before numbers): loss 9 = A P05,P06,P07 (sturdy) + P10,P02,P24; B F07,F05,F10. Profit 6 = C: C3 lock 70%/4pt, C5 iceberg trail15 arm0.5, C4 scale-out 70% to target; D: F07, F08 (PE nyam time-decay 60/45 min), F10 (MV london scale-out 20% trail15). 9x6 = 54 combos = family size. Tier 1 limit 40: top 40 by additive min(L6M,PRE) from the published A-D tables (the 14 cut include P05/P06/P07 + C3 lock and B:F10 + C3/C5).
- Engine: dispatcher class E/code/ecls.py gives each component its own book/unit scope. Validated first: A P05, B F10, C3 lock, D F08, D F10 alone reproduce the stored A-D replays exactly (trades, exit times, gross) on 2023-04, and a combo equals the additive sum there. Month-chunk replica, 10 warm-up days, ITER14 settings. A first version silently ran inert because the loader cache copied the first run's rule parts; caught by the validation and fixed before any number was used.
- Staging (A-style; logged after the 7-month stage and before any PRE/X'/HOLD-year number): all 40 on 2026-04..10 (L1M..L6M); 10 with L3M>0, L6M>0, recents pass and L6M above the better component went to all 43 months. The other 30 never saw PRE (stage-1 table: out/s1_table.pkl).
- Placebo/family: real random-exit worlds cannot be re-run on a combination; the constituents' own placebos are quoted (A:P10 p 0.00; D F07 .29, F08 .015). E's own null is a 200-world weekly sign-flip of the paired delta (statistic: t of min(L6M,PRE)), family = max over all 40 (non-survivors enter with the L6M-only t). This is weaker than a random-exit placebo. Walk-forward: monthly purged, best trailing 12 months among the 10 vs random choice (realised +311.6k vs random mean +446.3k, p 0.83).
- Not done: perturbation set on combos, E0 references on the engine, 1,000-draw own placebos, the 14 combos below the Tier-1 cut, PRE for the 30 stage-1 non-survivors, convention-set re-runs of combos.
- Dead ledger: dead_lookup before (no match), 10 rows appended after (program THE_REPLICA_PREPROOF); ledger not rebuilt. Seal manifest_after.json sha 759f2258 unchanged. Code and tables: /mnt/l2/l2vast/_th_redo_replica/E/ (code/, out/, runs/).

## Table 1 - the 10 combinations on all 43 months, then their components (USD/week vs HOLD)
**cut-input agreement with live: 14% at 0% false (best FIT-selected convention) / literal reading 45 of 92 within +-2 s with 23 false; engine Gate 0 NOT passed; PRE-PROOF**
| id | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | L6M nodrop | PRE nodrop | L6M MDE | recents | tolerant | dd first |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| B:F07+C:C3lock70b4 | -1886 | +1696 | +6857 | +8263 | +3012 | -4483 | +570 | -2719 | +5936 | +1448 | +12038 | True | True | False |
| A:P10+D:F07_PEny_decay60 | -8567 | -2138 | +2912 | +8016 | +2408 | -6421 | +5369 | -4104 | +5901 | +6483 | +10805 | True | False | True |
| A:P10+D:F08_PEny_decay45 | -8650 | -2189 | +1737 | +7313 | +1819 | -5768 | +5128 | -3776 | +5244 | +6037 | +10408 | True | False | True |
| A:P10+C:C5ice_arm0.5 | -7267 | -1669 | +3553 | +6358 | +688 | -5556 | +660 | -3431 | +4342 | +1852 | +12688 | True | True | True |
| A:P10+C:C4run_target70 | -6339 | +1056 | +4688 | +6309 | +483 | -7855 | +3813 | -3419 | +4244 | +4764 | +11217 | True | False | True |
| B:F07+C:C5ice_arm0.5 | +943 | +9264 | +8155 | +6038 | +2345 | -2467 | +377 | -3716 | +8026 | +1392 | +13096 | True | True | True |
| B:F07+C:C4run_target70 | -2909 | +147 | +3411 | +3862 | +3088 | -3937 | +4557 | -2098 | +1696 | +5747 | +11294 | True | True | True |
| A:P02+D:F08_PEny_decay45 | -3280 | +2022 | +1040 | +3530 | -27 | -5748 | +3851 | -2670 | +1314 | +4899 | +11942 | True | True | True |
| B:F07+D:F08_PEny_decay45 | +1182 | +5433 | +3411 | +2658 | +2868 | -1779 | +5340 | -2453 | +4099 | +6326 | +10427 | True | True | True |
| B:F10+D:F10_MVlon_scale20t15 | +1533 | +2259 | +2176 | +1107 | +866 | -1460 | +1765 | -1061 | +2132 | +1474 | +3505 | True | False | False |

| id | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | L6M nodrop | PRE nodrop | L6M MDE | recents | tolerant | dd first |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| A:P02 | -3792 | -6153 | +776 | +3350 | -311 | -6585 | +3449 | -2063 | +1141 | +4502 | +11608 | True | True | False |
| A:P10 | -8588 | -3304 | +1131 | +3632 | +1731 | -6789 | +4790 | -3225 | +5235 | +5912 | +10587 | True | False | True |
| B:F07 | +1182 | +1129 | +2763 | +2569 | +3289 | -941 | +5219 | -2926 | +4019 | +6390 | +9930 | True | False | True |
| B:F10 | +1298 | +2552 | +2166 | +911 | +1355 | +1003 | +1608 | -440 | +2026 | +1399 | +3539 | True | True | False |
| C:C3lock70b4 | +2188 | +2816 | +1667 | +2404 | -1349 | -4360 | -1995 | -541 | +4217 | -2423 | +8643 | True | False | True |
| C:C4run_target70 | -2003 | -974 | -727 | +440 | -509 | -2708 | -540 | -356 | -451 | -251 | +6032 | False | True | True |
| C:C5ice_arm0.5 | +5787 | +4609 | +4094 | +1873 | -961 | +156 | -2154 | -3329 | +426 | -2906 | +5315 | True | True | True |
| D:F07_PEny_decay60 | +589 | +0 | +245 | +328 | +30 | +0 | +238 | +82 | +632 | +519 | +561 | True | True | True |
| D:F08_PEny_decay45 | +0 | +174 | +350 | +168 | +232 | +485 | +528 | +321 | +312 | +396 | +345 | True | True | True |
| D:F10_MVlon_scale20t15 | +235 | +320 | +554 | -190 | -675 | -1866 | -21 | -32 | +106 | +74 | +1545 | False | True | True |

## Table 2 - interaction, nulls and concentration (survivors)
**cut-input agreement with live: 14% at 0% false (best FIT-selected convention) / literal reading 45 of 92 within +-2 s with 23 false; engine Gate 0 NOT passed; PRE-PROOF**
| combo | L6M interaction (combo - loss - profit) | PRE interaction | additive L6M | additive PRE | t(min L6M,PRE) | p_plc | p_fam | top3-week share L6M | top3 share PRE | positive months |
|--|--|--|--|--|--|--|--|--|--|--|
| B:F07+C:C3lock70b4 | +3290 | -2654 | +4973 | +3224 | 0.23 | 0.20 | 0.96 | 0.79 | 1.65 | 0.52 |
| A:P10+D:F07_PEny_decay60 | +4056 | +341 | +3960 | +5028 | 2.08 | 0.00 | 0.28 | 0.79 | 0.41 | 0.63 |
| A:P10+D:F08_PEny_decay45 | +3513 | -190 | +3800 | +5318 | 1.97 | 0.00 | 0.32 | 0.83 | 0.38 | 0.59 |
| A:P10+C:C5ice_arm0.5 | +853 | -1976 | +5505 | +2636 | 0.23 | 0.18 | 0.96 | 1.03 | 1.54 | 0.35 |
| A:P10+C:C4run_target70 | +2237 | -437 | +4072 | +4250 | 1.46 | 0.00 | 0.51 | 0.94 | 0.56 | 0.43 |
| B:F07+C:C5ice_arm0.5 | +1596 | -2689 | +4442 | +3065 | 0.14 | 0.21 | 0.98 | 0.73 | 1.87 | 0.39 |
| B:F07+C:C4run_target70 | +853 | -123 | +3009 | +4679 | 0.96 | 0.02 | 0.71 | 2.65 | 0.46 | 0.52 |
| A:P02+D:F08_PEny_decay45 | +12 | -126 | +3518 | +3977 | 0.83 | 0.04 | 0.79 | 3.24 | 0.46 | 0.50 |
| B:F07+D:F08_PEny_decay45 | -79 | -407 | +2737 | +5747 | 0.71 | 0.06 | 0.84 | 1.00 | 0.38 | 0.65 |
| B:F10+D:F10_MVlon_scale20t15 | +386 | +177 | +721 | +1587 | 0.88 | 0.03 | 0.74 | 0.87 | 0.48 | 0.54 |

(add_* = loss-only + profit-only; int_* = combo minus add; t = sign-flip statistic of min(L6M,PRE); p_plc = sign-flip p; p_fam = max-stat over 40; top-3 share = share of the window total carried by its 3 best weeks.)

## CORRECTION: L6M under three bases (TH-FIX, 2026-11-08; PRE-PROOF, label as above; Gate 0 NOT passed; no PASS claim)
Weekly mean USD delta vs HOLD, L6M (2026-05-02..2026-10-30), recomputed from stored parquets (hist/F_A2/P10, E/runs/*).
| combo | 14 units, carrying week DROPPED (prereg decision basis) | 14 units, week KEPT | ALL trades, week dropped | ALL trades, week kept |
|---|---|---|---|---|
| A:P10 (loss only) | 3632 | 5235 | 3506 | 5153 |
| A:P10+D:F07 | 8016 | 5901 | 4151 | 5818 |
| A:P10+D:F08 | 7313 | 5244 | 7241 | 5161 |
Which basis the ENTER test uses: prereg E (a32a651d) Unit line = the 14 live book x session units; "Carrying-week column: ... carrying week dropped (decision) and WITHOUT dropping it (shown beside)". So the ENTER/decision basis is 14 units with the carrying week dropped (first column). Note that this column is the least stable for the D:F07 combo: dropping the week RAISES L6M from 5.9k to 8.0k there (dropping the largest-|delta| week removes a negative week), and the ALL basis gives 4.2k. Treat the L6M as 4-8k, not 8k; no combo clears the full ENTER test.
