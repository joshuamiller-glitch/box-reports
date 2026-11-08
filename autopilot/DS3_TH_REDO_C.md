# DS3_TH_REDO_C - program C, PROFIT side L2, on the REPLICA engine, L2-era history 2023-04..2026-10 (TH-C)

**Header: cut-input agreement with live: 14% at 0% false (best FIT-selected convention) / literal reading 45 of 92 within +-2 s with 23 false; engine Gate 0 NOT passed; PRE-PROOF**

No PASS claim. Research only, nothing live. Private trees under /mnt/l2/l2vast/_th_redo_replica/C/ (code/, hist/, full/, out/). Seal ds3_all_ea/manifest_after.json sha 759f2258... before and after (unchanged). Prereg C sha acf18f205b996562 (+ adoption fb6d42b6, addenda 07f947b4 / 95ff9a48) logged in DECISIONS.md before any number.

## 1. Bottom line
No program C cell beats the live reference on L6M and PRE; nothing goes to MORNING.md. Of 198 grid cells, **0** have a positive S = min(L6M, PRE) in the Tier S screen. In the full replica replays of 9 finalist cells + 2 live-reference cells, one cell (C3 lock at 70% of target, buffer 4 pt) is clearly positive in every recent window (L1M +2,188 / L2M +2,816 / L3M +1,667 / L6M +2,404 $ per week, drawdown better in L6M) but is negative in HOLD (-1,349), MID (-4,360), PRE (-1,995) and X' (-541): it fails the tolerant gate and is at best a REGIME candidate. The two C5 iceberg-trail cells show the same shape (recent positive, PRE/X' negative). Everything else is negative.

## 2. What the live profit side is in the settled D7 configuration (reference definition)
DS7.cs (sha 54697597...): ThL2ProfitOn defaults to false (L443); the profit branch of ManageThL2 (L1579-1590) needs unreal >= ThL2ProfitMinPts (30), DepthLive, curDepthRel >= ThL2ThickMult (2.0) for ThL2ThickSecs (10 s), then tightens the trail to FavExt - ThL2ProfitTrailPts (code default 30 pt; the user replica input is 30 TICKS = 7.5 pt) or takes at market (ThL2ProfitTake). curDepthRel = 8-tick two-sided depth / per-half-hour EWMA baseline (L2ThSnapshot L1550-1560, 300-snapshot warm-up). In the replica the tighten is on only in the old panel (to Mon 08:50 ET) and the Monday take lines (THP_POLICY 08:05-08:15) were replaced by the loss-only line at 08:20, so **the settled live profit side is empty**. HOLD in this report = that empty profit side (the live loss cut stays). The live gated take lines and the live tighten are therefore run as REFERENCE cells added to HOLD, not as the base.
DS7.cs facts that differ from earlier assumptions: (a) ThL2ProfitTrailPts and the policy `tighten` param are POINTS; the prereg C1 `trail` axis is TICKS and is converted x0.25 (2,4,8,16 ticks = 0.5,1,2,4 pt); the live 30 ticks = 7.5 pt is not on the grid (reference cell). (b) DS7.cs has no 4-level list for C2: levels are the prereg's index into {0,1,1.5,2} (ahead_rel, tot_rel), {0,5,10,30} (pulled_mult), {0,1,2,3} (ice_against), the TH-BDG assumption. (c) ice_against in DS7.cs (L2095) counts refills seen in the last 30 s (rules_replica used 10 s; Tier S and the replays use 30 s). (d) DS7 has a policy action `lock` (L2204): protective level at entry + X, market exit on touch, checked at evaluation instants only; C3 is implemented that way (rules_replica's `be` moves the bracket stop instead - not used). (e) policy trails/locks are touch-checked only at the 1-s evaluation, ThL2 trails per print.

## 3. Does the thick-book trigger fire? (curDepthRel >= 2.0 for 10 s with unreal >= 30)
Yes - the blind-week peak of 1.52 is not typical of history. Over the 23,788 HOLD trades (4.2 yr):

| convention (depth snapshot cadence) | evals with open >= 30 pt | evals rel >= 1.5 / 2.0 / 3.0 | trades with any eval rel >= 2.0 | trades reaching the 10-s sustained trigger (2023/24/25/26) |
|--|--|--|--|--|
| literal (replica, per Last print) | 9,491,657 | 161,946 / 30,647 / 6,848 | 4,612 | **595** (76/97/215/207) |
| depth snapshot cadence 100 ms (proxy for conflated feeds) | 9,491,657 | 134,901 / 27,002 / 6,250 | 4,570 | **482** (68/92/180/142) |
| depth snapshot cadence 1000 ms (proxy for conflated feeds) | 9,491,655 | 220,234 / 43,654 / 10,359 | 5,180 | **810** (144/175/251/240) |

So the C1 cells are not inert: about 2.0-3.4% of trades reach the live trigger, 4,600-5,200 trades (19-22%) touch rel >= 2.0 at least once. Unconditionally (all prints, 970 days) rel >= 2.0 occurs on 0.42% of snapshots under the literal reading and on every day of the history. Convention note: only the depth-snapshot cadence is varied here (literal per Last print, 100-ms grid, 1-s grid; 100 ms and 1 s are PROXIES for the conflated FIT conventions, the 50-ms conflation cannot be rebuilt from the 100-ms grid). The FIT finalists' pulled-support/Med input exists only for the blind week + Oct 28-30 caches, so pulled_mult and ice_against cells are evaluated under the literal reading only across history (convention set incomplete for them). The live trigger count moves from 595 (literal) to 482 / 810 (proxies): +-35% - the C1 benefit sign is checked across the three in the table of section 5.

## 4. Method (adapted by the adoption file)
Engine: REPLICA (adapter_replica ITER14 headline, HistAdapter month chunks on the 970 validated day files; engine restarts flat at each month seam; settled D7 config assumption). Tier S = one HOLD record pass (c_rec.py: 63 M evaluation rows, one per ThL2 evaluation instant with upnl > -15; price, favourite extreme, tgt/stp distance, tot_rel, ahead_rel, pulled_mult, ice_against, min/max price since the last evaluation, replica book-walk market-exit price at decision + 1.0 s) and each of the 198 cells (+3 references) as a simulation on the rows (no re-entry cascade, stated; 1-s resolution for ThL2 trail touches). 14 units x 201 cells = 2,814 unit-cells. Windows L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' by exit label day, as-of 2026-10-30; weekly paired delta, carrying week (largest |delta| week, windows >= 8 weeks) dropped for the decision, *_nodrop shown beside; drawdown-first and policy_rules.enters predicates; placebo = same exits moved to a random in-profit evaluation row of the same trades (200 shared-seed worlds); family null = max z over all unit-cells (Westfall-Young style, 200 worlds); walk-forward by month (best trailing 12-month cell, 1-month purge): realised -211,747 $ vs random-cell choice -528,442 (negative, not positive). Shifted-trigger/random-side placebos are not defined for a side-less profit rule (not run). 1,000-draw own placebos for finalists were not run (200 worlds only).
Tier 1 (replica replays, 43 month chunks each): 11 cells, NOT 40 - cost was ~13 min per month for 11 cells, ~9 h wall on 2 workers; finalists = best Tier S cell per sub-grid with >= 50 exits (C1, C2, C2b, C2c, C3, C4, C5) + two cells chosen for activity (C5 iceberg arm 0.5, plain take at 30%) + the live tighten (2.0x/10 s/7.5 pt) and the live Monday lines. HOLD month 2026-10 re-run through the replay class = identical to the record run (917 trades, 58,115, exact). A first launch of the four policy-line cells ran inert (policy_profit_mode default 'live' = no profit lines in the loaded policy): detected on the 9-month fidelity check, results deleted and rerun with mode 'always'.

## 5. Tier 1 table (full replica replays; weekly mean delta $ vs HOLD, carrying week dropped; L6M/PRE nodrop beside)
**Header: cut-input agreement with live: 14% at 0% false (best FIT-selected convention) / literal reading 45 of 92 within +-2 s with 23 false; engine Gate 0 NOT passed; PRE-PROOF**

| cell                             |   L1M |   L2M |   L3M |    L6M |   HOLD |    MID |   PRE |    X' |   L6M_nodrop |   PRE_nodrop | DDfirst   | recent   | tolerant   |   S_L6M |   S_PRE |   p_plac |   p_fam |
|:---------------------------------|------:|------:|------:|-------:|-------:|-------:|------:|------:|-------------:|-------------:|:----------|:---------|:-----------|--------:|--------:|---------:|--------:|
| C.C1.thick5_sec2_trail2          |  2505 |  -448 |    43 |    -22 |   -355 |   -310 |  -113 |     0 |         -720 |          113 | False     | False    | True       |     -42 |    -221 |    0.005 |   0.005 |
| C.C2.gateice_against_lvl3_pct0.5 |     0 |     0 |     0 |    -18 |    -23 |      0 |    -6 |   144 |          -66 |          -42 | False     | False    | True       |      49 |     -11 |    0.119 |   1     |
| C.C2b.ahead1.5_pulled30_pct0.85  | -2829 | -1654 | -1454 |   -668 |   -597 |  -1471 |  -693 |  -283 |        -1602 |         -412 | False     | False    | False      |   -1160 |    -284 |    0.005 |   0.005 |
| C.C2c.tot2.0_ice1_pct0.5         |     0 |     0 |     0 |   -139 |   -200 |    -42 |  -547 |   -21 |         -230 |         -263 | False     | False    | False      |     -13 |    -162 |    0.015 |   1     |
| C.C3.pct0.7_buf4                 |  2188 |  2816 |  1667 |   2404 |  -1349 |  -4360 | -1995 |  -541 |         4217 |        -2423 | True      | True     | False      |    -263 |   -1868 |    1     |   1     |
| C.C4.pct0.7_runnertarget         | -2003 |  -974 |  -727 |    440 |   -509 |  -2708 |  -540 |  -356 |         -451 |         -251 | True      | False    | True       |   -1656 |    -626 |    0.005 |   0.005 |
| C.C5.trail15_stateiceberg_arm0.3 |  5985 |  4523 |  3651 |   1702 |   -138 |   2692 | -3008 | -4621 |          237 |        -4170 | False     | True     | False      |      49 |   -2394 |    1     |   1     |
| C.C5.trail15_stateiceberg_arm0.5 |  5787 |  4609 |  4094 |   1873 |   -961 |    156 | -2154 | -3329 |          426 |        -2906 | True      | True     | True       |    1291 |   -2612 |    1     |   1     |
| C.C2.gateahead_rel_lvl0_pct0.3   | -3348 | -1218 | -1299 | -12933 | -15104 | -19874 | -7681 |  1523 |       -15502 |        -6713 | False     | False    | False      |  -13103 |   -5214 |    0.881 |   1     |
| REF_LIVE_TIGHTEN_2.0x10s_30ticks | -1177 |  1636 |  1319 |  -1711 |  -2773 |    500 |  -203 |   271 |        -2611 |         -500 | False     | False    | True       |    -792 |    -865 |    0.005 |   0.005 |
| REF_LIVE_MONDAY_LINES            |  1575 | -1391 | -3715 |  -9121 | -11507 | -18096 | -4362 | -2689 |       -11345 |        -5055 | False     | False    | False      |  -18240 |   -5100 |    0.005 |   0.005 |

Columns: DDfirst = stack maxDD with the rule not worse than without in L6M and PRE; recent = L3M and L6M > 0 and L1M/L2M not below -0.5 MDE; tolerant = PRE and X' >= -0.5 MDE with sample floors; S_L6M/S_PRE/p_plac/p_fam are the TIER S values of the same cell (placebo p of a negative rule is not meaningful). Entry predicate (policy_rules.enters) is False for all 11 cells (C3 and the C5 iceberg pair pass recent but fail the tolerant gate or drawdown on PRE; C5 arm0.3 also drawdown-first fails).

Tier S vs Tier 1 fidelity (L6M weekly delta, Tier S -> Tier 1): C3 lock -263 -> +2,404; C5 iceberg 0.5 +1,291 -> +1,873; take 30% -13,103 -> -12,933; Monday lines -18,240 -> -9,121; tighten -792 -> -1,711. The screen has the right sign on the large losers but missed the C3 lock benefit (re-entry after the early exit is not in Tier S: the lock run has 1,659 more trades than HOLD). Consequence: Tier S 'no cell positive' is not proof for the 187 cells not replayed; they are untested at Tier 1.

## 6. Tier S sub-grid summary (198 cells, pooled stack, S = min(L6M, PRE))

| sub   |   cells |   S_pos |   best_S |   ddfirst |   recent_pass |   enters |
|:------|--------:|--------:|---------:|----------:|--------------:|---------:|
| C1    |      48 |       0 |      -94 |         1 |             0 |        0 |
| C2    |      64 |       0 |       -4 |        10 |             0 |        0 |
| C2b   |      24 |       0 |    -1160 |         3 |             0 |        0 |
| C2c   |      12 |       0 |        0 |        11 |             0 |        0 |
| C3    |       9 |       0 |    -1868 |         3 |             0 |        0 |
| C4    |       9 |       0 |    -1656 |         2 |             0 |        0 |
| C5    |      32 |       0 |    -2394 |         7 |             1 |        0 |

Reference cells (Tier S, pooled): live tighten (2.0x, 10 s, 7.5 pt) 498 exits/trades changed, L6M -792, PRE -865; as take 594, L6M -1,030; Monday lines 11,046 exits, L6M -18,240, PRE -5,100. Positive unit-cells exist only as 'exit early at 30% of target' in PE nyam (+465/wk L6M and PRE, placebo p 0.39, family p 1.0): a random exit does as well, so it is the earlier-exit effect, not the book condition.

## 7. Robustness and caveats
* Convention set: Tier S variants for rel/ahead_rel under snapshot cadences are in out/C_cells.parquet (conv_S_100, conv_S_1000, fragile_share_*); no cell cleared the sign test with a positive benefit, so no benefit exists to be fragile. Tier 1 replays use the literal reading only.
* Fragile-cut share and PS perturbation set of ADDENDUM_ROBUST apply to loss-cut inputs; for C the cut input is not used except the loss cut kept in HOLD.
* History config is the settled D7 config for all years (stated assumption); month-chunk seams drop carried positions; the 970 day files are PRE-PROOF; 100-ms causal book (up to 100 ms stale).
* Fill model: one (replica) fills model; 'measured/old' basis axes do not exist. Gross $ used (net_fee differs by 1.18/lot).
* Not run: 189 of the 198 grid cells in Tier 1 (budget), 1,000-draw finalist placebos, purged walk-forward on Tier 1 numbers.
