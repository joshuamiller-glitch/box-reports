# DS3_ZONES_3_ZL2_SUMMARY - the TAPE zone families (ZL-2): cells, V13Y result under the PA band, final label

Base D7 V13Y (the fixed base); lock none headline (user's literal frame), 12R beside. Noise band = Z3's V13Y phase-averaged (PA) band: lock-off flip 2% / 5%: L6M 15.5 / 20, PRE 11.5 / 16.1, X' 14.1 / 22.4; rule = PA cut above the band in L6M AND (PRE or X'), plus a NO-HARM column (PRE and MID not worse than minus the flip-2% band). Everything post-hoc, Shadow only, no PASS. 126 tape streams (OLD CAP build + extension to 2026-10-30, causality audit 865k rows 0/0/0.0, 16 roll days excluded, TCD stream checked for a data-regime break: none).

## Families
| family | what | cells scored (V13Y lock none) | single-path band rule (flip2 / flip5) | + no-harm | phase-averaged cells | PA band rule | PA band + no-harm | final label |
|---|---|---|---|---|---|---|---|---|
| TPF | profile lines (closed anchors, incl. the 3 lines group 10 lacked) | 197 | 4 / 2 | 1 | 10 | 2 | 0 | DEAD / NOISE: the three missing lines carry no row-level information (effects within +-9 pts, ranks 0.2-0.99); drawdown cuts are volume-equivalent in PRE. |
| TCP | composite 5/20/60-day profiles | 93 | 2 / 0 | 2 | 2 | 1 | 1 | NOISE: the one band + no-harm cell (hvn1_60d half, 652 rows) clears the PA band by <1 pt, PRE placebo rank 0.02, ONE-WEEK in F9 and X'. |
| TVP | developing day/session POC, HVN, LVN, voids | 81 | 1 / 0 | 0 | 5 | 1 | 0 | DEAD: the day-POC D40 12R lead is gone on V13Y (F9 -23% -> 0%); lock none absent; LVN/HVN/void cells are volume effects. |
| TDA | delta-at-price absorption | 8 | 0 / 0 | 0 | 0 | 0 | 0 | DEAD: 2-3k events, no cell passes any gate. |
| TCD | cumulative-delta extremes / divergences / bursts | 39 | 8 / 5 | 0 | 10 | 8 | 0 | FAIL (regime): passes the PA band through L6M and X' (+52..67% L6M) but PA PRE -25..-78% and MID -12..-36%; not a data break (checked); worse than random in PRE. |
| TLP | large prints (>=25/50/100 lots, 1h/4h, clusters) | 36 | 0 / 0 | 0 | 7 | 0 | 0 | LEAD-weak (mean-type, row level): rows with a large print ahead lose in 2024-26 (any side -$676 / -$467 per taken row L6M / HOLD, AGAINST -$790 / -$554), X' flat; fails the PA rule (L6M +16..19%, PRE +3..9%) and the best-of-N bar (rank 0.004 on min(L6M,HOLD,PRE), 0.20 with X'; adjusted p ~0.95). |
| TLQ | measured liquidity pools (swing/equal/session/killzone/prior-day H/L) | 116 | 3 / 2 | 0 | 5 | 2 | 0 | FAIL: the levels are run-through levels (hold less than random); skip cells harm X'/MID; the Asia-line cell is volume-equivalent in PRE/HOLD and its V13Y HOLD is +14% (worse). |
| other | NEW3 groups, LP grid (36 cells), POC sensitivity (13), freshness/strength variants, interactions | 58 | 2 / 1 | 0 | 10 | 1 | 0 | see LP_AGAINST, POC pages |

Totals: 628 cells scored on V13Y lock none (583 screen + 22 groups + variants); phase-averaged 49; **PA band rule passes 15 (flip2) / 9 (flip5); band + no-harm 1 / 0; none survives the 100-draw row-level placebo in PRE.**

## Flag #2 (LP_AGAINST_25_4h_D40) - LEAD-weak
Skip a fresh >= 25-lot print of the last 4 h whose aggressor is OPPOSITE to the trade within 40 pts ahead (2,614 rows). V13Y taken trades: rows lose -$594 / -$373 / -$318 per row in L6M / HOLD / PRE (X' neutral); saved $k lock none 77 / 91 / 73 / -4; null rank 0.004 (min L6M,HOLD,PRE) and 0.20 (with X'); adjusted p ~0.95 over ~760 definitions; Jaccard with ZL-1's BT swing flip 0.04, union saves the sum; PA L6M +16% / PRE +3% / X' -16% (fails the band). Page DS3_ZONES_3_L2_TAPE_LP_AGAINST.md.

## LP_FLIP (pre-registered, sha256 3de31519515e09f3aeba1c4dd357d10d0172d5e27b6ab35ca24f7047d45cc3e8 in DECISIONS.md): large-print levels just broken through by >= 10 pts, fresh flip level ahead within 40
One cell: 91,194 of the ~102k >= 25-lot prints are broken by >= 10 pts within 4 h (so the rule is volume-heavy: 13,610 engine rows = 15%). V13Y saved dollars of the skipped taken trades ($k): lock none L6M +71 / HOLD +111 / PRE -232 / X' +7; per year 2023 +23, 2024 -172, 2025 -152, 2026 +108; 12R L6M +133 / HOLD +203 / PRE -109 / X' +46.
Null (400 families: price-offset and shuffled-day, thinned to the same row count): min(L6M,HOLD,PRE) real -232.2 vs null median -46.2 / p95 29.0, rank 0.973; min(L6M,HOLD,PRE,X') real -232.2, null median -48.0 / p95 22.3, rank 0.973. PRE is -232 $k (the rows it skips WIN in 2024-25). Overlap: Jaccard with BT 0.064 (35% of BT's rows are inside it), with LP_AGAINST 0.084. **Label: DEAD** (PRE and 2024-25 strongly negative; fails the prereg success rule).

## Pages
DS3_ZONES_3_L2_TAPE_V13Y.md (leads V13X->V13Y, screen), _V13Y_PA.md (phase-averaged re-flag, side table), _LP_AGAINST.md, _LARGEPRINT_V13Y.md, _POC.md (V13X, defect base), _LOCKNONE.md (V13X), ROW_LEVEL(_V13Y).md, B7_ASIA_CUBE.md (V13X), _REGIME.md; chain files chain_V13Y_*_{nolock,12R}.csv in /mnt/l2/l2vast/ds3_zones3_new/ZL-2/ for the register; forward-shadow spec lines for the large-print rule in FORWARD_SHADOW_ZONES_SPEC.md.
