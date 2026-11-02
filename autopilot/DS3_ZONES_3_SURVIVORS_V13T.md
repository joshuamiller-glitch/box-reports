# DS3_ZONES_3_SURVIVORS_V13T - survivors re-based on V13T_LIVE, walk-forward, change table

Shadow only. No PASS claims. Z3, 2026-11-02. Base V13T_LIVE (V13Z lines empty, lock none, xcost 0.80, stopcost 2.45, tshort 0, lockfix legs). Details: DS3_ZONES_3_V13T_LIVE.md (layers, 15 leads), DS3_ZONES_3_NOISE_V13T_FINAL.md (band).

## 1. Survivors (top-15 leads + NONE + ALL7 skip), rule applied on V13T_LIVE
Rule: PA cut (9 shifts) > 2%-flip band in L6M AND (PRE or X') above band, same sign; no-harm in PRE and MID (cut not below minus band); placebo rank >= 0.95; equal-risk; carrying-episode drop.
| lead | band gate (L6M and PRE/X') | no-harm PRE/MID | placebo on V13T | label |
|---|---|---|---|---|
| BT swing flip D40 | fail (L6M .142 < .188) | ok | not run | NOISE / MEAN-ONLY (MID -.089) |
| LP_AGAINST natural | fail (L6M -.005) | ok | not run | NOISE |
| LP any-side A40 TLP p25 4h | fail (.130) | ok | not run | NOISE |
| EQL_tight 5m D40 | fail PRE/X' (L6M .385, PRE .051, X' -.184) | ok | not run | ONE-WINDOW (no PRE/X' support) |
| camH3 40 fw8 | fail (.036) | ok | not run | NOISE |
| PDmid 40 fw1 | fail (-.038) | ok | not run | NOISE |
| S5 sopen40 half | pass (.192; PRE .348) | ok | V13Y: VOLUME, size-matched null; not re-run | VOLUME (CVaR L6M +22k, L3M -.35) |
| S5 sA40>=1 skip | pass (.502; PRE .219) | FAIL (MID -.323, X' -.585) | not run | FRAGILE |
| S5 nA60>=1 skip | pass (.504; PRE .126) | FAIL (MID -.377, X' -.595) | not run | FRAGILE |
| S5 rho60>=2 skip | L6M only (.469; PRE -.045, X' .025) | ok | V13Y: VOLUME | L6M-ONLY |
| ZL-3 G2 TVP-confirmed skip Dl60 | L6M only (.525; PRE -.071, X' .092) | ok | not run | L6M-ONLY (carrying episode suspected) |
| SWG f3L 15s D40 half | L6M only (.239; PRE -.001, X' -.089) | ok | V13Y: VOLUME | L6M-ONLY / VOLUME |
| ARR iplFVG 15s D20 skip | L6M only (.337) | FAIL (PRE -.340, MID -.562) | not run | FRAGILE |
| DEV on_L D20 half | fail L6M (.187 < .188) | FAIL (PRE -.130) | not run | NOISE / FRAGILE |
| ALL7 skip (HALF->SKIP) | fail (.142) | FAIL (MID -.694) | not run | HARM in MID |
Bottom line: NO SURVIVOR on V13T_LIVE; nothing is RISK-KEEP. The shipped layer itself does not beat random same-size half layers (ranks .23-.79, all below .95) and has no equal-risk edge. Placebos, equal-risk and episode-drop for the leads are carried from V13Y verdicts and were not re-run on V13T_LIVE.

## 2. Monthly-refit walk-forward on V13T_LIVE (lock none; real engine composites, 2024-01..2026-10, purged 5 days)
Cut vs shipped fixed layer (negative = refit has larger maxDD):
| series | WF | PRE | MID | L6M | HOLD | L3M |
|---|---|---|---|---|---|---|
| WF6 (trailing 6m) | -.444 | -.078 | -.613 | -.592 | -.592 | -.512 |
| WF12 (trailing 12m) | -.661 | -.075 | +.192 | -.831 | -.831 | -.926 |
| WF6 shrink | .000 | .000 | .000 | +.006 | +.006 | .000 |
| WF12 shrink | -.007 | -.007 | .000 | .000 | .000 | .000 |
| no zone layer | -.051 | -.051 | -.279 | -.077 | -.077 | -.024 |
Random monthly picks (5 chains): mean cut WF -.17, L6M -.24. Verdict: the unrestricted refits are worse than the fixed layer (rank 0.00 vs random picks in WF/L6M/HOLD), the shrink variants collapse to the fixed layer (they almost never move off SHIP: 5-10 of 306 unit-months). Monthly refit does not beat the fixed layer. n=5 random chains is small.

## 3. What changed V13Z -> V13T_LIVE (Z3's outputs)
V13Z: nfix basis-N take deltas, five take lines active, lock-12 reference available. V13T: V13Z with take lines empty, lock none, lockfix legs. V13T_LIVE: + xcost 0.80, stopcost 2.45, tshort 0.
| item | V13Y (last full Z3 set; V13Z not fully re-run by Z3) | V13T_LIVE |
|---|---|---|
| noise band PA, 2% flip L6M / PRE / X' / HOLD / MID | 15.7 / 11.4 / 15.9 / 14.5 / 26 % | 18.8 / 7.8 / 14.5 / 18.2 / 21.2 % |
| noise band PA, 5% flip L6M / PRE / X' / HOLD / MID | 19.9 / 17.4 / 23.0 / 19.1 / 37 % | 21.9 / 9.9 / 18.2 / 20.5 / 32.2 % |
| shipped-layer L6M maxDD (mean over 9 shifts) | see SURVIVORS_V13Y | 172k, SD 14k across shifts (134k at xcost 0.58, 166k at 1.02) |
| shipped layer vs random layers | not distinguishable in L6M/HOLD, better in PRE | not distinguishable in any window (ranks .23-.79); PRE +.107 vs band .078 (rank .79) |
| survivors | none | none |
| monthly-refit walk-forward | fails | fails (worse than fixed, -44% to -83% in WF/L6M) |
Net: PRE band is much tighter (7.8 vs 11.4 %), L6M band is wider (18.8 vs 15.7 %), the verdict does not change.
Caveat: the V13Z->V13T_LIVE comparison above is via V13Y numbers because Z3 did not run a full band on V13Z; any V13Z-specific figure belongs to S5/BASE-4.
