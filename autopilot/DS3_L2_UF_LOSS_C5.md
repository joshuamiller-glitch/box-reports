# DS3_L2_UF_LOSS_C5 - L2-UNTIL-FOUND cycle 5, LOSS side: time-in-trade STALL exits conditioned on the order book (agent UF-LOSS, 2026-10-30)
Research only. UNTOUCHED (> 2026-02-06) never read. Own masks: 2026=20260101..0206 (~5 real weeks), L6M=20250801..0206, HOLD=20250701..0206, PRE=20240201..20250630, X'=20230401..20240131. Prereg `l2vast/ds3/prereg/UF_LOSS_C5_prereg.md` sha256 869234e70b2f23fe63a9d474eb9345d3b0aa6a6f0f276fd66cc6d0e46d0623c0; selection `out/uf/loss1/selection5_PRE.json` sha256 e14e8d2f1d22174053d33059cad77466436c8232aa41213435594aba218f634a (PRE+X' only, N basis, logged before the single recent look). dead_lookup over all 576 specs: 0 EXACT/NEAR/PARTIAL (nearest catalogued: THL2 H11 MFE-armed wait of 10-300 s, best cell L6M +0.16, X' -0.62; THLB arm=TIME). Cumulative N = UF_TRIALS.json total 146,342 + 576 = 146,918; n_effective 15.7. ONE recent look. All tags causal (decision-time features only; prior-month z-scores).
Gate basis N + selectivity (fire < 50% of trades alive and underwater at T); LIVE-CAL (stop 2.45, market M, target corr 0) and M beside; credit share (LC-N)/LC. Format `mean [n fired] (MDE)`, MDE = 2.8 SE, day x ENTRY-session clusters. Underwater share at T is 96-97% of alive trades (mean upnl -7 pt at 5 min): "stalled" trades are almost all the losers.

## 1. Settings table (recent first). Result: no PASS; best-available is NEGATIVE; the book makes the rule selective but not profitable
| group | cell (selected on PRE+X') | fire % L6M (of alive underwater at T) | 2026 N | L6M N | HOLD N | PRE N | X' N | L6M M / LC (credit) | path-only stall control N L6M (fire %) | rank shuffled book (L6M/HOLD) | rank random cuts (L6M/HOLD) | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | stall=S1x20|T=5m|book=BK4|act=cut | 4 | -0.18 [32] (0.37) | -0.06 [192] (0.25) | -0.06 [196] (0.23) | +0.06 [475] (0.15) | +0.07 [52] (0.16) | -0.03 / -0.05 (n/a) | -2.09 (93) | 1.00/1.00 | 0.40/0.45 | BEST-AVAILABLE-NEGATIVE |
| ST | stall=S1x20|T=5m|book=BK4|act=cut | 4 | +0.05 [3] (0.81) | -0.07 [26] (0.60) | -0.12 [27] (0.57) | +0.34 [65] (0.38) | +0.09 [8] (0.43) | -0.04 / -0.05 (n/a) | -1.23 (90) | 0.60/0.55 | 0.45/0.35 | BEST-AVAILABLE-NEGATIVE |
| HM | stall=S2y15|T=30m|book=BK8|act=t15 | 48 | -0.52 [31] (2.88) | -0.35 [155] (1.42) | -0.53 [165] (1.35) | +0.33 [342] (0.84) | +0.22 [173] (1.60) | -0.26 / -0.32 (n/a) | -0.19 (58) | 0.50/0.55 | 0.60/0.60 | BEST-AVAILABLE-NEGATIVE |
| WT (non-D6, separate) | stall=S3|T=20m|book=BK7|act=cut | 4 | -0.24 [7] (0.70) | -0.04 [21] (0.26) | -0.07 [22] (0.25) | +0.12 [73] (0.18) | +0.09 [20] (0.25) | -0.03 / -0.03 (n/a) | -0.07 (22) | 0.15/0.05 | 0.55/0.55 | BEST-AVAILABLE-NEGATIVE |
| KB | stall=S3|T=20m|book=BK1|act=cut | 5 | +0.23 [7] (1.07) | -0.11 [25] (0.63) | -0.08 [26] (0.58) | +0.16 [61] (0.33) | +0.03 [17] (0.59) | -0.09 / -0.09 (n/a) | -0.30 (28) | 0.10/0.15 | 0.20/0.20 | BEST-AVAILABLE-NEGATIVE |
| SM | stall=S1x20|T=5m|book=BK5|act=t15 | 28 | +1.80 [12] (5.09) | +0.26 [42] (1.85) | +0.33 [43] (1.62) | +0.85 [100] (1.05) | +0.00 [34] (1.61) | +0.31 / +0.29 (12%) | +1.10 (93) | 0.15/0.30 | 0.20/0.30 | CANDIDATE-RECENT-weak (N>=0 L6M/HOLD/PRE/X'; placebo<0.9; inside MDE) |
| PE | stall=S2y15|T=20m|book=BK5|act=cut | 18 | -0.99 [22] (2.25) | -0.45 [82] (1.20) | -0.37 [85] (1.11) | +0.14 [152] (0.65) | +0.69 [47] (1.01) | -0.31 / -0.40 (n/a) | -1.02 (58) | 0.45/0.60 | 0.05/0.05 | BEST-AVAILABLE-NEGATIVE |
| PB | stall=S1x20|T=20m|book=BK7|act=cut | 17 | +1.14 [14] (2.24) | -0.59 [54] (1.35) | -0.44 [57] (1.24) | +0.45 [149] (0.84) | +0.55 [57] (1.36) | -0.48 / -0.54 (n/a) | -3.37 (82) | 0.95/0.90 | 0.40/0.45 | BEST-AVAILABLE-NEGATIVE |
| DN | stall=S3|T=10m|book=BK0|act=cut | 31 | -3.63 [18] (4.97) | -2.17 [95] (2.32) | -1.61 [105] (2.17) | +0.80 [221] (1.17) | +1.27 [89] (1.67) | -1.93 / -2.06 (n/a) | -2.17 (31) | 0.00/0.00 | 0.00/0.00 | BEST-AVAILABLE-NEGATIVE |
| MV | stall=S3|T=30m|book=BK0|act=t10 | 22 | +0.10 [26] (1.95) | -0.07 [85] (0.84) | -0.00 [102] (0.80) | +0.21 [205] (0.44) | +0.02 [100] (0.99) | -0.04 / -0.05 (n/a) | -0.07 (22) | 0.00/0.00 | 0.80/0.80 | BEST-AVAILABLE-NEGATIVE |
| MA | stall=S2y15|T=10m|book=BK7|act=cut | 17 | +4.88 [8] (4.58) | -1.48 [32] (2.48) | -0.96 [35] (2.20) | +0.40 [86] (1.35) | +0.21 [33] (1.87) | -1.28 / -1.43 (n/a) | -4.85 (74) | 0.40/0.50 | 0.50/0.65 | BEST-AVAILABLE-NEGATIVE |
Pooled selected cell `S1x20 | T=5 min | WALL0 (cum_behind10_rel <= 0.5, wall behind gone) | cut`: fires on 4% of alive underwater trades; N 2026 -0.18, L6M -0.06 (MDE 0.25), HOLD -0.06, PRE +0.06, X' +0.07; M L6M -0.03, LC -0.05; $/wk N L6M -4,239. Its PRE gain per fired trade is +3.1 pt and its L6M value per fired trade is -3.2 pt: the sign flips between PRE and the recent windows. Shuffled-book (trade-aligned within day, corrected) rank L6M/HOLD 1.00/1.00 (placebo mean -0.18): the real cell is better than a shuffled book (shuffling puts the cut on random stalled trades, which is costly); random cuts at the same per-day count: rank 0.40/0.45 - not beaten. Reality check (i) White RC on PRE daily sums (N) over the 576 cells p = 0.37 (best loss|stall=S3|T=30m|book=BK6|act=t15); restricted to the 420 selective n>=100 cells p = 0.99. (ii) cumulative Bonferroni (N_cum 146,918): 1.00 for every selected cell (best single L6M t < 0).

## 2. What the book adds to the stall rule (path-only control)
Stall-alone / path-only (BK0) cells fire on a median 63% of alive underwater trades (only 16 of 64 below 50%) and are negative: median PRE N -0.38 (fire 0.63); the selected pooled cell's own path-only control (S1x20, 5 min) is N -2.09 in L6M (fire 93%). Adding a book condition shrinks the cut to a minority of trades, which removes the damage but does not create a gain. By book condition (all 576 cells; PRE, N):
| bk   |   cells |   fire_med |   selective |   PRE_N_med |   X_N_med |   PRE_N_max |
|:-----|--------:|-----------:|------------:|------------:|----------:|------------:|
| BK0  |      64 |      0.626 |          16 |      -0.384 |    -0.172 |       0.026 |
| BK1  |      64 |      0.125 |          64 |      -0.072 |    -0.029 |       0.028 |
| BK2  |      64 |      0.013 |          64 |      -0.009 |    -0.003 |       0.006 |
| BK3  |      64 |      0.033 |          64 |      -0.007 |     0     |       0.037 |
| BK4  |      64 |      0.019 |          64 |      -0.006 |     0.012 |       0.056 |
| BK5  |      64 |      0.14  |          64 |      -0.101 |    -0.089 |       0.023 |
| BK6  |      64 |      0.01  |          64 |      -0.007 |    -0.002 |       0.029 |
| BK7  |      64 |      0.135 |          64 |      -0.08  |    -0.02  |       0.034 |
| BK8  |      64 |      0.496 |          32 |      -0.312 |    -0.097 |       0.054 |
Per fired trade, among the selective cut cells (PRE, N basis):
| bk   |   cells |   fire |   PRE_N_per_fired_trade |
|:-----|--------:|-------:|------------------------:|
| BK0  |       4 |   0.27 |                   -2.61 |
| BK1  |      16 |   0.12 |                   -1.69 |
| BK2  |      16 |   0.01 |                   -3.79 |
| BK3  |      16 |   0.03 |                   -0.86 |
| BK4  |      16 |   0.02 |                    0.09 |
| BK5  |      16 |   0.14 |                   -4.14 |
| BK6  |      16 |   0.01 |                   -2.06 |
| BK7  |      16 |   0.13 |                   -2.01 |
| BK8  |       8 |   0.34 |                   -2.13 |
Reading: BK2 (queue draining), BK3 (ES against), BK4 (wall gone) and BK6 (thin & ES) fire on 1-4% of stalled trades and are statistically indistinguishable from zero (|N| <= 0.01 pooled); the broader states BK1 (thin), BK5 (pull), BK7 (thin or drain) are N-negative (-0.07 to -0.10 PRE) and BK8 (not-SUP, the hold-through form: cut unless support is holding) is non-selective (fire ~50-80%) and -0.5. The book therefore only shrinks the cut to a small group of trades whose median value per fired trade is negative in PRE (-0.9 to -4.1 pt for every condition except BK4 wall-gone at +0.09) and never turns the stall exit positive; the one cell with a PRE gain (BK4, 5 min) flips sign recently.
By stall definition and T:
| stall   |   fire_med |   PRE_N_med |
|:--------|-----------:|------------:|
| S1x10   |      0.101 |      -0.045 |
| S1x20   |      0.156 |      -0.077 |
| S2y15   |      0.108 |      -0.063 |
| S3      |      0.051 |      -0.004 |
|   T |   fire_med |   PRE_N_med |
|----:|-----------:|------------:|
|   5 |      0.107 |      -0.06  |
|  10 |      0.088 |      -0.042 |
|  20 |      0.064 |      -0.035 |
|  30 |      0.053 |      -0.023 |
By action:
| act   |   fire_med |   PRE_N_med |   X_N_med |
|:------|-----------:|------------:|----------:|
| cut   |      0.084 |      -0.055 |    -0.023 |
| half  |      0.084 |      -0.028 |    -0.012 |
| t10   |      0.084 |      -0.042 |     0.004 |
| t15   |      0.084 |      -0.033 |     0.004 |
Top 8 selective cells by PRE N (pooled):
| cell                                    |   ALL_fire_PRE |   ALL_nfire_PRE |   ALL_PRE_N |   ALL_PRE_M |   ALL_PRE_LC |   ALL_PRE_mde |   ALL_X_N |
|:----------------------------------------|---------------:|----------------:|------------:|------------:|-------------:|--------------:|----------:|
| loss|stall=S1x20|T=5m|book=BK4|act=cut  |          0.039 |             475 |       0.056 |       0.073 |        0.074 |         0.147 |     0.074 |
| loss|stall=S3|T=30m|book=BK8|act=t15    |          0.157 |            1298 |       0.054 |       0.063 |        0.058 |         0.125 |    -0.084 |
| loss|stall=S1x10|T=5m|book=BK4|act=cut  |          0.028 |             343 |       0.038 |       0.05  |        0.051 |         0.128 |     0.057 |
| loss|stall=S3|T=5m|book=BK3|act=cut     |          0.017 |             202 |       0.037 |       0.044 |        0.046 |         0.093 |     0.041 |
| loss|stall=S3|T=20m|book=BK7|act=cut    |          0.055 |             512 |       0.034 |       0.047 |        0.056 |         0.141 |     0.086 |
| loss|stall=S3|T=5m|book=BK6|act=cut     |          0.007 |              88 |       0.029 |       0.032 |        0.033 |         0.059 |    -0.002 |
| loss|stall=S3|T=20m|book=BK1|act=cut    |          0.053 |             487 |       0.028 |       0.041 |        0.049 |         0.138 |     0.062 |
| loss|stall=S1x20|T=5m|book=BK4|act=half |          0.039 |             475 |       0.028 |       0.037 |        0.037 |         0.074 |     0.037 |

## 3. WT (non-D6, separate) and HM-only (registered a30_w10 unaltered)
WT cell `stall=S3|T=20m|book=BK7|act=cut`: N 2026 -0.24, L6M -0.04 (MDE 0.26), HOLD -0.07, PRE +0.12, X' +0.09; 21 fired in L6M, shuffled-book rank 0.15/0.05; WT stack -1,234/wk L6M (MDE 2,352). Nothing for WT.
HM-only: registered base (static L6(30,10), FULL, unaltered): N 2026 +0.14, L6M -0.00 (MDE 1.50), HOLD +0.06, PRE +0.20, X' +0.94 (fire 25%). The HM stall cell selected on PRE+X' (`stall=S2y15|T=30m|book=BK8|act=t15`; fire 48%) is N L6M -0.35 (1.42), HOLD -0.53, PRE +0.33, X' +0.22: worse than the base recently and non-selective-ish (47%); stack L6M +300/wk vs base +3,485 (MDE 6,058).

## 4. Stack (exact 6-book lock engine, M-basis engine; $/wk delta vs base, MDE in brackets), equal-risk scaling, sessions
| stream | 2026 d$/wk (MDE) | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| ALL_sel | -7,111 (19,100) | -4,315 (9,064) | -3,776 (7,945) | -15 (4,368) | +38 (1,702) |
| WT_sel | -2,196 (7,028) | -1,234 (2,352) | -1,080 (2,063) | +433 (1,618) | +167 (694) |
| HM_sel | +2,430 (11,707) | +300 (13,840) | -472 (12,234) | +1,311 (6,684) | +371 (7,695) |
| COMBO_perbook6 | +3,078 (24,417) | -2,632 (15,729) | -2,535 (13,792) | +2,938 (8,539) | +1,648 (9,048) |
| HM_a30w10_static | +4,598 (7,549) | +3,485 (6,058) | +3,578 (5,656) | +63 (6,176) | +1,544 (3,430) |
EQR first-order (worst-20 weeks matched): ALL c 1.012: L6M -3,599 / HOLD -3,208 / PRE +499; WT c 1.002: L6M -1,090; per-book six: L6M +4,909 / HOLD +3,435 / PRE +8,567. Sessions (ENTRY, pooled cell, N, MDE, n fired) L6M: asia +0.01 (0.42, 42), london -0.14 (0.41, 38), pre +0.19 (0.70, 6), nyam -0.09 (0.57, 40), nypm -0.16 (0.67, 62); PRE: asia -0.04, london +0.10, pre +0.14, nyam +0.06, nypm +0.08. All inside MDE.

## 5. Learned
1. Almost every trade that is alive after 5 minutes is underwater and "stalled" (80-94% under the MFE definitions), so a path-only stall exit is a blanket cut: N -0.4 to -0.6 pt/trade at fire 50-99% (non-selective).
2. The book conditions (thin, drain, ES, wall gone, pull) pick out 1-14% of those trades. Their effect is inside noise with large swings per trade: median PRE value per fired trade is negative for every condition but BK4, and the selected BK4 cell flips from +3.1 pt per fired trade in PRE to -3.0 in L6M (pooled L6M -0.06, 2026 -0.18, MDE 0.25).
3. The 'hold-through when support is holding' form (BK8) is non-selective and strongly negative: the book does not identify the stalled trades that recover.
4. Placebo: the cell beats a shuffled book (cutting random stalled trades is costly) but not random cuts at the same rate (rank 0.40/0.45).
5. Five cycles (book danger, tape/footprint recovery, scale-out remainder, causal regime walk-forward, time-in-trade stall) have found no order-book loss rule >= 0 on N in L6M and HOLD that is selective and beats its placebos; the only N-positive structure is the high-vol path trigger on one book (cycle 3, not reproduced out of sample in cycle 4).

## 6. Next family (differs from 1-5)
MBO items not on disk (order lifetimes at best, cancel bursts, queue position at the stop) need a rebuild, not another 10-s book rule. On existing data the untested loss-side structures are (a) entry-side avoid filters (hand-off: the entry-second pull-z >= 2 skip of cycle 3, PRE N +0.57, never looked at recent windows) and (b) bracket geometry (stop distance by regime, BRACKET track). Recommend the lead decide whether the LOSS stop condition should now be reported as unmet with the best-available-negative per cycle, rather than another 10-s rule family.

## 7. Needed in D6 (also in DS3_THL2_NEEDS.md)
Stall state at T (MFE so far, upnl, time since last adverse extreme) and the book states THIN / DRAIN / WALL0 / PULL / SUP defined in uf5_cells.py (cum_behind10_rel, cum_behind5 60 s ago, refill_ratio_behind10, cons_behind10, added_sup10, pulled_sup10 z, es_imb5). None promoted.
Files: code/uf/uf5_{cells,engine,stageA,stageB,stack}.py; out/uf/loss1/{D5.npz,P5.pkl,cells5_PRE_X.csv,selection5_PRE.json,stageB5.pkl,stack5.json}; DEAD_CELLS.csv +576 (program UFL5).
