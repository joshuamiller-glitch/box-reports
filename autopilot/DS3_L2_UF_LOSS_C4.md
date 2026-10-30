# DS3_L2_UF_LOSS_C4 - L2-UNTIL-FOUND cycle 4, LOSS side: causal regime x path-trigger WALK-FORWARD (agent UF-LOSS, 2026-10-30)
Research only. UNTOUCHED (> 2026-02-06) never read. Own masks: 2026=20260101..0206 (~5 real weeks), L6M=20250801..0206, HOLD=20250701..0206, PRE=20240201..20250630, X' = chain evaluation 2023-07-01..2024-01-31 (chains need history; 7 months). Prereg `l2vast/ds3/prereg/UF_LOSS_C4_prereg.md` sha256 5ca9f061cc00902bc6f5d4e4b86fd704179b23d7d8ff08049cc79822ce7128bf; selection `out/uf/loss1/selection4_PRE.json` sha256 d18c535daf1442ba0a269d66e3ccdefa159b2d0794a18953db82d0aff045737f (PRE+X' only, N basis, logged before the single recent look). dead_lookup over 48 chain specs + 16 candidate specs: 0 hits. DS3_CAUSAL_TIMES.md did not exist; rule applied: regime tag = vol_tag_prev for entries before 09:30 ET (asia/london/pre), vol_tag_today from 09:30 ET (nyam/nypm/close); every fit uses only trades CLOSED before the refit date, trailing 3/6/12 months, refits monthly/quarterly from 2023-07-01.
**Look history.** The 16 candidates are cycle-3 cells (UFL3); cycle 3 read their recent windows for the selected cells (incl. WT L6(20,10) reg2 FULL) with two looks. Here the WT static cell is a REFERENCE row only. The walk-forward chains are new (48 cells; cumulative N = 144,988 + 48 = 145,036; each refit scans 16 candidates; n_effective 2.7); this cycle took ONE recent look, on the selected chains + controls + references.
Gate basis N + selectivity; LIVE-CAL (stop 2.45, market M, target corr 0) and M beside; credit share (LC-N)/LC. Format `mean [n fired] (MDE)`, MDE = 2.8 SE, day x ENTRY-session clusters. Action of every candidate: 100% cut at the L6(A,W) trigger second (cycle 3: remainder policy irrelevant).

## 1. Settings table (recent first). Result: no PASS. Best-available: CANDIDATE-RECENT-weak (ALL pooled chain); walk-forward does not reproduce the WT static result
| group | chain (selected on PRE+X') | fire % L6M | 2026 N | L6M N | HOLD N | PRE N | X' N | L6M M / LC (credit) | rank shuffled tags (L6M/HOLD) | rank random candidate (L6M/HOLD) | share reg2 picks L6M | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | w=6m|cad=3m|scope=pooled|crit=mean|set=reg12 | 17 | -0.16 [236] (1.31) | +0.09 [1162] (0.73) | +0.11 [1187] (0.66) | +0.22 [3098] (0.46) | +0.54 [956] (0.87) | +0.20 / +0.22 (59%) | 1.00/1.00 | 0.50/0.50 | 100% | CANDIDATE-RECENT-weak (N>=0 L6M/HOLD/PRE/X'; random-candidate placebo fails; inside MDE) |
| ST | w=6m|cad=3m|scope=pooled|crit=t|set=all16 | 11 | +0.13 [12] (1.19) | +0.15 [83] (0.84) | +0.17 [85] (0.77) | +0.45 [366] (0.79) | +0.34 [81] (1.51) | +0.19 / +0.23 (36%) | 0.70/0.60 | 0.30/0.30 | 100% | CANDIDATE-RECENT-weak (N>=0 L6M/HOLD/PRE/X'; random-candidate placebo fails; inside MDE) |
| HM | w=3m|cad=3m|scope=pooled|crit=mean|set=all16 | 17 | -0.48 [30] (3.38) | -0.20 [94] (1.25) | -0.14 [96] (1.13) | +0.70 [352] (0.93) | +0.69 [168] (2.51) | -0.11 / -0.08 (n/a) | 0.40/0.35 | 0.55/0.55 | 47% | BEST-AVAILABLE-NEGATIVE |
| WT (non-D6, reported separately) | w=3m|cad=3m|scope=book|crit=t|set=reg12 | 6 | -0.09 [12] (0.76) | -0.02 [49] (0.29) | -0.02 [50] (0.26) | +0.21 [231] (0.29) | +0.10 [125] (0.77) | -0.00 / +0.01 (n/a, LC ~ 0) | 0.20/0.25 | 0.45/0.55 | 24% | BEST-AVAILABLE-NEGATIVE |
| KB | w=6m|cad=1m|scope=book|crit=t|set=all16 | 12 | -0.00 [25] (2.06) | -0.14 [85] (0.79) | -0.07 [89] (0.73) | +0.01 [288] (0.64) | +0.19 [33] (0.84) | -0.11 / -0.06 (n/a) | 0.25/0.35 | 0.00/0.15 | 46% | BEST-AVAILABLE-NEGATIVE |
| SM | w=6m|cad=3m|scope=pooled|crit=t|set=reg12 | 12 | +0.73 [6] (0.81) | +0.78 [23] (1.32) | +0.67 [23] (1.15) | +0.65 [88] (1.15) | +0.75 [19] (1.25) | +0.80 / +0.87 (11%) | 0.90/0.90 | 0.50/0.55 | 100% | CANDIDATE-RECENT-weak (N>=0 L6M/HOLD/PRE/X'; random-candidate placebo fails; inside MDE) |
| PE | w=3m|cad=1m|scope=book|crit=mean|set=all16 | 17 | -0.39 [30] (2.51) | -0.75 [125] (1.36) | -0.58 [130] (1.26) | +0.41 [483] (0.93) | +0.09 [62] (1.40) | -0.65 / -0.63 (n/a) | 0.15/0.25 | 0.20/0.45 | 51% | BEST-AVAILABLE-NEGATIVE |
| PB | w=3m|cad=1m|scope=pooled|crit=t|set=reg12 | 5 | -0.15 [7] (1.51) | +0.08 [24] (0.51) | +0.01 [27] (0.54) | +0.08 [220] (0.80) | +0.02 [52] (1.46) | +0.09 / +0.11 (31%) | 0.85/0.65 | 0.85/0.75 | 47% | CANDIDATE-RECENT-weak (N>=0 L6M/HOLD/PRE/X'; random-candidate placebo fails; inside MDE) |
| DN | w=12m|cad=3m|scope=book|crit=mean|set=reg12 | 19 | +0.14 [10] (2.58) | +0.26 [88] (1.72) | +0.27 [90] (1.54) | +0.32 [208] (1.06) | +0.09 [58] (1.76) | +0.37 / +0.41 (35%) | 0.95/0.95 | 1.00/1.00 | 100% | CANDIDATE-RECENT |
| MV | w=3m|cad=3m|scope=pooled|crit=t|set=all16 | 13 | +0.35 [7] (0.37) | -0.15 [86] (1.01) | -0.10 [89] (0.92) | +0.42 [307] (0.72) | +0.78 [90] (1.47) | -0.10 / -0.06 (n/a) | 0.40/0.50 | 0.65/0.65 | 76% | BEST-AVAILABLE-NEGATIVE |
| MA | w=6m|cad=3m|scope=pooled|crit=mean|set=reg12 | 18 | +0.15 [15] (6.12) | +0.64 [49] (2.20) | +0.60 [50] (1.89) | +0.55 [151] (1.43) | +1.22 [49] (1.89) | +0.74 / +0.78 (18%) | 1.00/1.00 | 0.75/0.75 | 100% | CANDIDATE-RECENT-weak (N>=0 L6M/HOLD/PRE/X'; random-candidate placebo fails; inside MDE) |
| REFERENCE static WT (looked in cycle 3; not a candidate) | static WT L6(20,10) reg2 FULL | 11 | +0.78 [17] (0.80) | +0.33 [114] (0.47) | +0.30 [116] (0.42) | +0.29 [250] (0.31) | +0.11 [39] (0.45) | +0.37 / +0.41 | - | - | - | reference |
| REFERENCE static HM (looked in cycle 3; not a candidate) | static HM L6(30,10) none FULL (registered a30_w10 family) | 25 | +0.14 [30] (3.23) | -0.00 [135] (1.50) | +0.06 [149] (1.39) | +0.20 [414] (1.04) | +1.18 [60] (1.16) | +0.10 / +0.17 | - | - | - | reference |

DN (non-stack book, 12-month per-book chain, picks reg2 always): N >= 0 in all five windows, shuffled-tag rank 0.95/0.95 and random-candidate rank 1.00/1.00 - the only chain that clears both placebos - but L6M +0.26 vs MDE 1.72 (t +0.43), 88 fired trades, selected as best of 48 chains for 1 of 10 books (cumulative p 1.00); DN is outside the six stack books (no lock-engine line) and is labelled CANDIDATE-RECENT by the gate rules, not promoted.

Pooled chain (ALL, 10 books, 6m window, quarterly refit, pooled scope, mean criterion, regime-gated candidates): N 2026 -0.16 (MDE 1.31), L6M +0.09 (0.73), HOLD +0.11 (0.66), PRE +0.22 (0.46), X' +0.54 (0.87); fire 17%; LIVE-CAL L6M +0.22 (credit share 59%); $/wk N L6M +3,897. It picked the high-vol (reg2) candidate in 100% of L6M periods (the reg12 set let it choose any regime; reg2 won every refit), so it is the static reg2 rule with a calendar of "trigger" choices, not an adaptive regime switch.
**Placebos.** Shuffled day tags (20 draws, whole chain re-run): rank 1.00 in L6M and HOLD, placebo mean N -0.16 / -0.16 vs real +0.09 / +0.11: the causal vol tag carries information. **Random candidate at each refit (same calendar): rank 0.50 / 0.50** (0.9 PRE): picking a regime-gated candidate at random is as good as the walk-forward choice, i.e. the selection step adds nothing; the gain comes from restricting the path rule to a regime-conditioned subset, not from learning which one. Placebo beaten: shuffled yes, random-candidate no -> fails the stop-condition placebo test.
Reality check (i): White RC on PRE daily sums over the 48 chains (N) p = 0.38 (best loss|wf|w=3m|cad=3m|scope=pooled|crit=t|set=all16). (ii) cumulative Bonferroni with N_cum 145,036: p = 1.00 (best single L6M N t = +1.64 for SM at p1 0.05; ALL t +0.35).

## 2. WT (non-D6; reported separately) and HM-only (registered a30_w10 unaltered)
WT chain `w=3m|cad=3m|scope=book|crit=t|set=reg12`: N L6M -0.02 (0.29), HOLD -0.02, PRE +0.21 (0.29), X' +0.10, 2026 -0.09; it chooses reg2 only 24% of L6M periods and does not reproduce the static looked-at cell (N L6M +0.33, HOLD +0.30): the walk-forward WT result is -0.02 (inside MDE 0.29), shuffled-tag rank 0.20/0.25 (the real chain is below shuffled ones). The static high-vol WT result of cycle 3 is therefore NOT supported out of sample: a re-selection on the trailing 3 months of closed trades does not land on it. Stack (exact lock engine): WT chain -1.3k/wk L6M (MDE 4.4k) vs WT static reference +0.9k (MDE 2.7k).
HM-only: the registered base (static L6(30,10), no gate, FULL, unaltered) N 2026 +0.14, L6M -0.00 (MDE 1.50), HOLD +0.06, PRE +0.20, X' +1.18 (X' here 2023-07..2024-01); fire 25%. The HM chain selected on PRE+X' (`w=3m|cad=3m|scope=pooled|crit=mean|set=all16`) is N L6M -0.20 (1.25), HOLD -0.14, PRE +0.70, X' +0.69: worse than the base in the recent windows; stack -0.1k/wk L6M vs base +3.5k (MDE 6.1k). Regime gating does not improve the registered HM rule.

## 3. Grid of 48 chains (PRE and X' only; ALL pooled, medians; WT/HM columns = those books' PRE N)
By W:
|   W |   chains |   fire |   PRE_N |   PRE_N_max |   X_N |   WT_PRE_N |   HM_PRE_N |
|----:|---------:|-------:|--------:|------------:|------:|-----------:|-----------:|
|  12 |       16 |  0.18  |  -0.026 |       0.052 | 0.218 |      0.079 |      0.488 |
|   3 |       16 |  0.165 |   0.014 |       0.195 | 0.124 |      0.088 |      0.378 |
|   6 |       16 |  0.175 |   0.077 |       0.223 | 0.134 |      0.108 |      0.128 |

By cad:
|   cad |   chains |   fire |   PRE_N |   PRE_N_max |   X_N |   WT_PRE_N |   HM_PRE_N |
|------:|---------:|-------:|--------:|------------:|------:|-----------:|-----------:|
|     1 |       24 |  0.18  |  -0.001 |       0.109 | 0.185 |      0.084 |      0.193 |
|     3 |       24 |  0.176 |   0.036 |       0.223 | 0.144 |      0.096 |      0.394 |

By scope:
| scope   |   chains |   fire |   PRE_N |   PRE_N_max |   X_N |   WT_PRE_N |   HM_PRE_N |
|:--------|---------:|-------:|--------:|------------:|------:|-----------:|-----------:|
| book    |       24 |  0.168 |   -0.02 |       0.119 | 0.124 |      0.122 |      0.086 |
| pooled  |       24 |  0.18  |    0.08 |       0.223 | 0.15  |      0.07  |      0.486 |

By crit:
| crit   |   chains |   fire |   PRE_N |   PRE_N_max |   X_N |   WT_PRE_N |   HM_PRE_N |
|:-------|---------:|-------:|--------:|------------:|------:|-----------:|-----------:|
| mean   |       24 |   0.19 |   0.001 |       0.223 | 0.285 |      0.117 |      0.387 |
| t      |       24 |   0.15 |   0.012 |       0.195 | 0.134 |      0.083 |      0.164 |

By set:
| set   |   chains |   fire |   PRE_N |   PRE_N_max |   X_N |   WT_PRE_N |   HM_PRE_N |
|:------|---------:|-------:|--------:|------------:|------:|-----------:|-----------:|
| all16 |       24 |  0.185 |  -0.005 |       0.201 | 0.249 |      0.084 |      0.208 |
| reg12 |       24 |  0.17  |   0.025 |       0.223 | 0.124 |      0.106 |      0.301 |

Reading: no knob matters. Per-book chains are not better than pooled; 3-month and 12-month windows are within noise; t-stat criterion = mean criterion; reg12 and all16 give the same picks (reg2 dominates). Median chain PRE N is 0.00, so the typical walk-forward configuration earns nothing in PRE; the selected pooled chain (+0.22) is the best of 48 and sits inside its MDE (0.46).

## 4. Stack (exact 6-book lock engine, M-basis engine; $/wk delta vs base, MDE in brackets) and equal-risk scaling
| stream | 2026 d$/wk (MDE) | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| ALL_chain | +26 (23,683) | -3,263 (11,030) | -2,897 (9,735) | -4,093 (11,480) | +1,165 (8,902) |
| WT_chain | +386 (1,080) | -1,341 (4,439) | -1,173 (3,881) | +128 (1,341) | +180 (3,362) |
| HM_chain | -5,735 (32,102) | -89 (9,163) | +74 (8,011) | +4,259 (4,766) | +675 (5,372) |
| COMBO_perbook6 | -3,615 (24,915) | -3,761 (9,258) | -3,085 (8,104) | +2,113 (9,592) | +3,040 (10,499) |
| WT_static_ref | +3,086 (5,885) | +869 (2,653) | +760 (2,321) | +229 (1,372) | +40 (1,713) |
| HM_a30w10_static | +4,598 (7,549) | +3,485 (6,058) | +3,578 (5,656) | +63 (6,176) | +1,544 (3,430) |
| pooled_static_reg2_A20 | +26 (23,683) | -3,263 (11,030) | -2,897 (9,735) | -4,948 (8,833) | -111 (7,384) |
EQR first-order (worst-20 weeks matched): ALL chain c 1.037: L6M -939 / HOLD -1,052 / PRE -2,602; WT chain c 0.993: L6M -1,769 / HOLD -1,515; HM chain: L6M +296; WT static reference L6M +853; HM a30_w10 static L6M +6,494. The stack is negative or inside MDE for every adaptive chain.
Sessions (ENTRY, pooled chain, N pts/trade, MDE, n fired) L6M: asia -0.08 (0.83, 122), london +0.04 (1.57, 192), pre -0.07 (2.81, 66), nyam +0.17 (1.71, 504), nypm +0.29 (1.88, 271); PRE: asia +0.20, london +0.55, pre +0.64, nyam +0.32, nypm -0.41. All inside MDE.

## 5. Learned
1. The causal high-volatility tag carries information for the path rule (shuffled-tag placebo -0.16 vs +0.09 pooled L6M), but the walk-forward SELECTION of which regime/trigger to use adds nothing over a random regime-gated choice (rank 0.50).
2. The one static result of cycle 3 (WT L6(20,10) high-vol FULL cut) is not recovered by re-selection (WT chain L6M -0.02, picks reg2 only 24% of periods): it was a seen-data selection.
3. Per-book walk-forward is worse than pooled; short windows churn; no window length, cadence or criterion matters.
4. Pooled chain is N >= 0 in L6M/HOLD/PRE/X' but inside MDE (L6M +0.09 vs 0.73), 2026 -0.16, stack -3.3k/wk L6M: CANDIDATE-RECENT-weak, and cumulative p = 1.00.
5. After four cycles (book danger, tape/footprint recovery, scale-out remainder, regime walk-forward) the path rule's effect on N is within +-0.1 pt/trade of zero in the recent windows and no order-book or regime layer changes it reliably.

## 6. Next family (differs from 1-4)
Stop trying to improve when/how to cut a loser with state. Remaining untested LOSS structures: (a) the stop DISTANCE itself (ex-ante, per-book, per-regime: tighter initial stop in high-vol regime = the bracket side, belongs to the BRACKET agent), (b) time-in-trade (a flat-line time exit for trades that have not made progress after T), scored on N with causal features only; (c) MBO-only items not on disk (order lifetimes at best, cancel bursts). Recommend (b) as cycle 5 and handing (a) to the bracket track.

## 7. Needed in D6 (also in DS3_THL2_NEEDS.md)
Nothing new beyond the cycle-3 entries (L6 path rule on every book, causal vol tag); the walk-forward refit is a nightly job on closed trades (selection = argmax mean N over the trailing window among regime-gated candidates), not promoted.
Files: code/uf/uf4_{cells,engine,stageA,stageB,stack}.py; out/uf/loss1/{C4.npz,cells4_PRE_X.csv,selection4_PRE.json,stageB4.pkl,stack4.json}; DEAD_CELLS.csv +48 (program UFL4).
