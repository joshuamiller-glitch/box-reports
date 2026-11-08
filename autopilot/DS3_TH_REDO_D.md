# DS3_TH_REDO_D - program D, PROFIT side L1 (PhMin/PhReq/PhTrail, chandelier, ATR trail, time-decay, scale-out) on the REPLICA engine, 2023-04..2026-10

**cut-input agreement with live: 14% at 0% false (best FIT-selected convention) / literal reading 45 of 92 within +-2 s with 23 false; engine Gate 0 NOT passed; PRE-PROOF**

Status: PRE-PROOF research, Shadow only, no PASS claim, nothing live. Written 2026-11-08 by TH-D.

## Live definition (what a rule must beat)
Live L1 profit rule = none: PhOn=false on every book (DS7.cs L382-385, L478 'v1.5a OFF', L532-545), the ThL2 profit tighten is off in the settled configuration, so the live profit side is hold-to-bracket (60/60 style target/stop, plus the L2 loss cut). The "live Ph defaults on" cell (20/3/8, all books) is shown as a control.

## Method (as preregistered, adapted by ADOPTION_REPLICA2)
* Engine: REPLICA over the 970 HIST-PIPE day files, month chunks (engine starts flat each month), hist config, same parameters as TH-A's HOLD pass (HOLD trade list reproduced exactly: 43 months, 23788 HOLD trades). Delta = rule minus HOLD, weekly sums by exit label day, 14 units (core six books), carrying week (largest |delta| ISO week) dropped in windows >= 8 weeks, gross basis (replica headline); net_fee computed beside in tier1_stats.json.
* Stage 1 (Tier S): a numba port replays all 250 D1-D5 rule cells on the recorded price path of every HOLD trade (23788) and every NOCUT trade (18880); rule decision, 0.5 s cancel, 0.175 s book fill, book walk on the 100-ms grid. Placebo: random exit instants on the same fired trades (200 shared-seed worlds); family max-stat over 3417 screened unit-cells. Engineering check (2023-06): rule decisions agree with the full replica on ~99% of matched trades with an exact 1.0 s decision-to-fill offset; dollars differ where the HOLD cut interferes. No re-entry cascade in Tier S.
* Convention set: D rules do not use the cut input, so the convention enters only through the entry/exit chain. Only two members could be run on 3.5 years: HOLD (literal reading of the code) and NOCUT (L2 loss cut absent, the extreme bound of any cut convention). The three FIT-finalist conventions exist only for the blind week and could not be run on the history. A rule's benefit sign is therefore reported in the two worlds (S hold / nocut column). Fragile share = share of the rule's Tier S dollars sitting on trades whose HOLD exit is a cut or that do not exist in the NOCUT world.
* Tier 1: 12 finalists (rule logged in DECISIONS.md before any number: top S=min(L6M,PRE) among cells passing drawdown-first with S>0 in the NOCUT world, <=2 per sub-grid/first-two-parameter/scope group) plus the live-Ph-default control, full replica replay of all 43 months each (559 runs). Scale-out on 1-lot books is inert (patched in a subclass; the original rules_replica turns 1-lot runner cells into a full-lot trail). Tier 1 limited to 13 of the allowed 40 by compute (~11 h on 2 workers).
* D6 (D x C combinations): NOT run - program C finalists did not exist when D finished.

## Stage 1 result
Pooled rule (same cell on all 14 units): 0 of 250 cells has S = min(L6M, PRE) > 0 in either world (best pooled S about -1.8k per week). Per-unit cells: 543 of 3500 have S>0 in the HOLD world, 63 in both worlds with >= 20 firings; the positives sit on two units only (PE nyam for D1/D4, MV london for D5 scale-outs). PE-nyam D1 cells are not different from random exits (placebo p 0.13-0.6): any early exit helps a unit whose HOLD result is cut-dominated.

## Tier 1 (full replica) - all windows, mean weekly delta in $ vs HOLD, carrying week dropped
cut-input agreement with live: 14% at 0% false (best FIT-selected convention) / literal reading 45 of 92 within +-2 s with 23 false; engine Gate 0 NOT passed; PRE-PROOF

| key | rule | scope | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | L6M nodrop | PRE nodrop | recents | tolerant | DD-first | p placebo | p family | TierS S hold / nocut | fragile share |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| F01_c068_PE_nyam | D1 {"phmin": 15, "phreq": 2, "phtrail": 20} | PE_nyam | -1854 | +1575 | +1949 | -1034 | -1947 | -1495 | +596 | -142 | -1666 | +329 | False | True | False | 0.179 | 1.000 | 1252 / 45 | 11.9 |
| F02_c000_PE_nyam | D1 {"phmin": 5, "phreq": 2, "phtrail": 2} | PE_nyam | -2531 | +152 | -7 | -199 | -831 | +203 | -248 | -151 | -869 | -625 | False | True | True | 0.547 | 1.000 | 1202 / 498 | 8.2 |
| F03_c001_PE_nyam | D1 {"phmin": 5, "phreq": 2, "phtrail": 3} | PE_nyam | -2583 | +70 | -88 | -282 | -940 | -128 | -129 | -188 | -949 | -508 | False | True | True | 0.557 | 1.000 | 1176 / 439 | 8.4 |
| F04_c035_PE_nyam | D1 {"phmin": 10, "phreq": 2, "phtrail": 10} | PE_nyam | -857 | +1780 | +2985 | -601 | -1288 | +247 | -177 | -1412 | -1101 | -509 | False | False | True | 0.134 | 1.000 | 1032 / 425 | 13.5 |
| F05_c033_PE_nyam | D1 {"phmin": 10, "phreq": 2, "phtrail": 6} | PE_nyam | -453 | +1949 | +3199 | -363 | -962 | +628 | -331 | -1407 | -910 | -681 | False | False | False | 0.189 | 1.000 | 804 / 265 | 13.5 |
| F06_c210_PE_nyam | D4 {"after_min": 10, "below_pct": 0.2, "act": "market"} | PE_nyam | -194 | +1761 | +2345 | -179 | +744 | +2023 | +502 | +584 | -609 | +213 | False | True | True | 0.896 | 1.000 | 489 / 372 | 17.0 |
| F07_c219_PE_nyam | D4 {"after_min": 60, "below_pct": 0.5, "act": "market"} | PE_nyam | +589 | +0 | +245 | +328 | +99 | +0 | +238 | +54 | +632 | +394 | True | True | True | 0.289 | 1.000 | 339 / 74 | 5.2 |
| F08_c216_PE_nyam | D4 {"after_min": 45, "below_pct": 0.2, "act": "market"} | PE_nyam | +0 | +174 | +350 | +168 | +301 | +485 | +401 | +293 | +312 | +272 | True | True | True | 0.015 | 0.886 | 312 / 591 | 5.3 |
| F09_c232_MV_london | D5 {"pct": 0.2, "runner": "trail8"} | MV_london | +608 | +1008 | +708 | -332 | -408 | -1730 | +150 | +101 | -61 | +34 | False | True | False | 0.005 | 0.010 | 272 / 518 | 6.1 |
| F10_c233_MV_london | D5 {"pct": 0.2, "runner": "trail15"} | MV_london | +370 | +645 | +571 | +385 | -287 | -1772 | -69 | -82 | +119 | +27 | True | True | True | 0.005 | 0.010 | 251 / 470 | 6.7 |
| F11_c231_MV_london | D5 {"pct": 0.2, "runner": "trail4"} | MV_london | +889 | +950 | +783 | -235 | -665 | -2110 | +21 | +34 | +84 | -82 | False | True | False | 0.005 | 0.010 | 242 / 500 | 6.0 |
| F12_c240_MV_london | D5 {"pct": 0.4, "runner": "trail8"} | MV_london | +7 | +28 | -368 | -331 | -573 | -623 | +185 | +286 | -66 | +90 | False | True | False | 0.005 | 0.005 | 231 / 312 | 6.0 |
| F13_c104_ALL | D1 {"phmin": 20, "phreq": 3, "phtrail": 8} | all books | -5107 | -16669 | -16350 | -14758 | -16445 | -16533 | -6323 | +1906 | -16981 | -7047 | False | False | False | nan | nan | - / - | - |

Walk-forward (monthly refit over all screened cells, 12-month trailing, 1-month purge, Tier S series): 30 months, realised delta -24375 vs random-cell mean -149768, p 0.109, positive: False.

## Reading in plain sentences
1. The Tier S winners mostly did not survive the full engine: nine of twelve finalists have L6M <= 0 on the replica (re-entry and locking after an early exit give back what the path screen saw).
2. Three finalists pass recents + tolerant gate + drawdown-first (F07, F08 on PE nyam; F10 on MV london; the F13 control fails all). None passes the walk-forward, and none enters: ENTER needs all of recents, tolerant, DD, placebo, family and walk-forward.
3. F08 (PE nyam, exit at 45 min if below 20% of target): L6M +168, PRE +401, no-drop positive, placebo p 0.015, but family p 0.89 (best-of-F) and the walk-forward fails. F10 (MV london scale-out at 20%, trail 15): placebo and family clean in Tier S but PRE is -69 on the replica. F07 placebo p 0.29.
4. Fragile-cut cap: every finalist's Tier S benefit sits on cut-dependent trades (fragile share 5x to 17x of the claimed benefit; benefit on robust trades alone is negative), so the robustness cap (<=30%) fails for all of them. The sign in the NOCUT world is positive for all twelve, but that world is a different trade set, not a robustness pass.
5. The live default Ph rule (20/3/8) on all books costs about -15k to -17k per week in L2M..HOLD on the replica: clearly worse than hold-to-bracket.
6. Nothing qualifies for the top of MORNING.md. Profit side L1 stays empty (hold-to-bracket), as the live code has it. Reason: no rule beats HOLD on L6M and PRE with the carrying week dropped, placebo-clean, family-clean, walk-forward-positive and fragile-cap-clean.

## Files
Code /mnt/l2/l2vast/_th_redo_replica/D/code (dkern.py 9811dd26, dprep.py f4af60d5, dstage1.py 9b0ea998, dtier1.py, dreport.py, dfinal.py); outputs /mnt/l2/l2vast/_th_redo_replica/D/out (D_pooled.parquet, D_unitcells.parquet, D_cand_stage1.csv, finalists.json, tier1_stats.json, fragile.json, walkforward.json). Seal manifest_after.json 759f2258 unchanged; private trees only; nothing killed.
