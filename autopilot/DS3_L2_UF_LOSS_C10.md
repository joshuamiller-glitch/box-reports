# DS3_L2_UF_LOSS_C10 - L2-UNTIL-FOUND cycle 10, LOSS side: STOP-TOUCH CONFIRMATION (stop-run absorption) (agent UF-LOSS, 2026-10-31)
Research only. UNTOUCHED never read. Own masks Y26 = 20260101..0206 (~5 wk), L3M = 20251106.., L6M = 20250801.., HOLD = 20250701.., PRE = 20240201..20250630, X' = 20230401..20240131. Prereg `l2vast/ds3/prereg/UF_LOSS_C10_prereg.md` sha256 bc7576fca7569f06f1cf8876ee3ea84e41bcbb9595e445d260d2a14970072a6a (logged before any outcome statistic); selection `out/uf/loss10/selection_PRE_X.json` sha256 b67edb875f6224016daecbec6294fe90fae2d7e4eaed74729e15c2e28e807dfc (PRE+X' only, basis N, lock-engine stack; EMPTY). dead_lookup: 0 hits (stop-touch / stop-delay / stop-run / soft-stop). Cumulative N = UF_TRIALS total + 52; n_effective 5.3. The ro_lib row map bug flagged in MORNING.md does not touch this cycle (engine rows and the capped 1-s arrays only).
Hypothesis: at the second the stop level is touched, hold W s (10/30) with a backstop X pts beyond (5/10); at W resume the original bracket if price is back on the right side of the stop, else exit at market; condition = L2 absorption signature of the stopped trade at the touch (6 features x 2 tails). Base: MKT, exact lock engine, planned-lot R locks; bases N (stop 1.01), NATIVE (1.28), LIVE-CAL (2.45). Cells: 4 unconditional + 48 conditioned = 52. Per contract = per planned lot (unit lots), same trades.
## Page 1 - the answer
1. **Nothing is selectable on PRE+X'**: 0 of 52 cells has a stack delta >= 0 in both PRE and X' (PRE -5,592..+2,491, X' -9,506..+1,308 $/wk; MDE 5-14k). RC / Romano-Wolf over the 52 on PRE+X' days: p 0.92 (studentised 0.93), survivors 0, PBO 0.68. The recent windows below are a labelled VIEW of an empty selection.
2. **The post-touch move is a regime, not an L2 signal.** Mean sided move of the NQ price after the stop level is touched (positive = rebound into the stop; pts): at 10 s PRE +0.13, X' +0.00, HOLD -0.24, L6M -0.28, Y26 -0.22; at 30 s PRE +0.54, X' -0.01, HOLD -0.40, L6M -0.45, L3M -0.50. In the selection data waiting looks slightly positive per contract (unconditional wait per contract +0.12..+0.16 PRE/X' on N, +0.30 on LIVE-CAL); in the last 12 months the touch is followed by continuation and waiting loses (-0.19..-0.26 per contract on N; -0.05..-0.10 on LIVE-CAL, inside MDE). The stack delta is negative in PRE and X' and in L6M/HOLD on N (unconditional W10 X5: PRE -3,840, X' -3,180, HOLD -4,087, L6M -6,928 $/wk, MDE ~15k) and about 0 on LIVE-CAL for the unconditional cells (W10 X5: L6M +0.2k, HOLD +2.5k, PRE -1.1k).
3. **L2 state at the touch carries no information about the post-touch move**: Spearman IC of the six features vs the 30-s sided move is |IC| <= 0.04 in every window (table 3); conditioned cells do not beat random subsets of stop events at the same size: 3 of 48 cells reach placebo rank >= 0.9 in both L6M and HOLD; 5 of 48 are >= 0 on the stack in L6M and HOLD on N, 0 in all of PRE, X', HOLD, L6M.
**Tier: DEAD (no selectable cell, no information in the touch state, regime-dependent drift). No further hypothesis on mbp-10 remains for the loss side (see MORNING.md).**
## 1. Unconditional references (stack d $/wk research lots; MDE beside; per contract = same trades)
| cell | basis | Y26 stack d$/wk (MDE) | L3M stack d$/wk (MDE) | L6M stack d$/wk (MDE) | HOLD stack d$/wk (MDE) | PRE stack d$/wk (MDE) | X stack d$/wk (MDE) | L6M live lots | per contract (same trades) L6M / HOLD / PRE / X' |
|---|---|---|---|---|---|---|---|---|---|
| uncond|W=10|X=5 | N | -2,604 (+31,471) | -7,955 (+21,292) | -6,928 (+15,264) | -4,087 (+15,018) | -3,840 (+10,907) | -3,180 (+8,999) | -2,258 | -0.21 / -0.19 / +0.16 / +0.12 |
| uncond|W=10|X=5 | NATIVE | -1,087 (+33,739) | -4,109 (+18,988) | -4,733 (+13,896) | -2,104 (+13,972) | -2,739 (+10,857) | -2,347 (+8,990) | -1,902 | -0.18 / -0.16 / +0.19 / +0.15 |
| uncond|W=10|X=5 | LIVE | +631 (+33,374) | +1,026 (+17,700) | +154 (+14,328) | +2,468 (+14,175) | -1,134 (+9,616) | +175 (+8,972) | -1,100 | -0.07 / -0.05 / +0.32 / +0.30 |
| uncond|W=10|X=10 | N | -3,291 (+34,545) | -3,467 (+19,805) | -3,475 (+15,241) | -1,176 (+15,272) | -4,969 (+11,644) | -3,232 (+8,816) | -1,886 | -0.22 / -0.20 / +0.15 / +0.12 |
| uncond|W=10|X=10 | NATIVE | -2,580 (+33,967) | -2,709 (+19,646) | -2,896 (+15,199) | -582 (+15,306) | -4,075 (+11,475) | -2,245 (+8,795) | -1,636 | -0.17 / -0.15 / +0.20 / +0.17 |
| uncond|W=10|X=10 | LIVE | -50 (+33,335) | +3,759 (+18,500) | +2,361 (+15,776) | +4,401 (+15,667) | +32 (+10,816) | +1,345 (+8,656) | -517 | +0.01 / +0.03 / +0.40 / +0.38 |
| uncond|W=30|X=5 | N | +12,175 (+40,621) | -3,212 (+25,147) | -6,046 (+17,215) | -1,777 (+17,027) | -1,693 (+12,865) | -5,484 (+11,482) | -2,269 | -0.30 / -0.30 / +0.15 / +0.10 |
| uncond|W=30|X=5 | NATIVE | +12,213 (+39,904) | -2,164 (+24,838) | -5,172 (+17,078) | -966 (+16,986) | -1,311 (+12,822) | -4,911 (+11,567) | -1,952 | -0.28 / -0.28 / +0.17 / +0.12 |
| uncond|W=30|X=5 | LIVE | +8,181 (+46,651) | -922 (+23,844) | -2,429 (+16,093) | +1,665 (+16,157) | -707 (+11,547) | -3,466 (+11,331) | -2,125 | -0.22 / -0.21 / +0.26 / +0.23 |
| uncond|W=30|X=10 | N | +16,328 (+54,287) | -4,799 (+30,003) | -4,489 (+20,725) | +1,070 (+20,401) | -5,592 (+13,771) | -7,783 (+12,263) | -2,064 | -0.26 / -0.22 / +0.12 / +0.11 |
| uncond|W=30|X=10 | NATIVE | +16,896 (+53,710) | -3,283 (+30,441) | -3,600 (+20,887) | +1,929 (+20,580) | -4,936 (+13,685) | -7,137 (+12,322) | -1,666 | -0.22 / -0.18 / +0.16 / +0.16 |
| uncond|W=30|X=10 | LIVE | +18,115 (+51,671) | +460 (+27,862) | -731 (+19,468) | +4,817 (+19,491) | -1,593 (+13,252) | -4,019 (+12,281) | -1,259 | -0.10 / -0.06 / +0.31 / +0.34 |
## 2. Conditioned cells (VIEW; medians over W and X per feature tail; placebo = random subsets of stop events within book-month, 100 draws, per-contract mean)
| feat      | tail     |   stackN_L6M |   stackN_HOLD |   stackN_PRE |   stackN_X |   stackLIVE_L6M |   pcN_L6M |   rank_L6M |   rank_HOLD |   rank_PRE |
|:----------|:---------|-------------:|--------------:|-------------:|-----------:|----------------:|----------:|-----------:|------------:|-----------:|
| c_cumbrel | ge_q0.67 |     -2809.7  |       -322.73 |       270.25 |   -7453.89 |         6818.26 |     -0.08 |       0    |        0.03 |       0.7  |
| c_cumbrel | lt_q0.33 |     -4954.42 |      -4199.3  |      -897.82 |     719.73 |         3744.71 |     -0.11 |       0.18 |        0.16 |       1    |
| c_delta10 | ge_q0.67 |     -4231.13 |      -1509.25 |       376.21 |   -1606.33 |         4727.69 |     -0.1  |       0.12 |        0.12 |       1    |
| c_delta10 | lt_q0.33 |       648.08 |        819.68 |     -3116.45 |    -856.96 |        10383.4  |     -0.05 |       0    |        0.04 |       0.68 |
| c_es5     | ge_q0.67 |     -2653.49 |      -1027.17 |     -1823.71 |    -992.01 |         6454.8  |     -0.05 |       0.46 |        0.58 |       0.99 |
| c_es5     | lt_q0.33 |        56.12 |        384.82 |     -1471.58 |   -1148.59 |         9246.18 |     -0.01 |       0.46 |        0.37 |       0.92 |
| c_imb10   | ge_q0.67 |     -4449.52 |      -2653.54 |       123.54 |   -2888.5  |         5437.5  |     -0.09 |       0    |        0.1  |       0.66 |
| c_imb10   | lt_q0.33 |     -2698    |      -1382.9  |     -2393.61 |    1197.29 |         6675.29 |     -0.14 |       0.02 |        0.04 |       0.99 |
| c_ofi10   | ge_q0.67 |     -1693.07 |        815.83 |       297.52 |   -1532.83 |         7451.94 |     -0.03 |       0.92 |        0.98 |       0.99 |
| c_ofi10   | lt_q0.33 |      -668.29 |        -30.69 |     -3472.85 |    -949.18 |         8188.62 |      0.01 |       0.32 |        0.36 |       0.58 |
| c_p10     | ge_q0.67 |      -753.87 |      -1206.05 |     -2189.47 |     138.73 |         8198.77 |     -0.1  |       0.24 |        0.32 |       0.81 |
| c_p10     | lt_q0.33 |     -1390.35 |       -420.86 |      -547    |   -4999.45 |         6614.17 |     -0.1  |       0.4  |        0.56 |       0.65 |
## 3. Information map at the stop touch (recent first)
Mean sided post-touch move (pts):
| what                           |   Y26 |   L3M |   L6M |   HOLD |   PRE |     X |
|:-------------------------------|------:|------:|------:|-------:|------:|------:|
| mean sided post-touch move 10s | -0.22 | -0.34 | -0.28 |  -0.24 |  0.13 |  0    |
| mean sided post-touch move 1s  | -0.07 | -0.08 | -0.16 |  -0.15 | -0.28 | -0.16 |
| mean sided post-touch move 30s | -0.24 | -0.5  | -0.45 |  -0.4  |  0.54 | -0.01 |
| mean sided post-touch move 3s  | -0.31 | -0.07 | -0.12 |  -0.09 | -0.03 | -0.03 |
IC of the stopped trade's L2 features vs the 30-s sided move:
| what                     |    Y26 |    L3M |    L6M |   HOLD |    PRE |      X |
|:-------------------------|-------:|-------:|-------:|-------:|-------:|-------:|
| IC c_cumbrel vs 30s move | -0.009 |  0.006 |  0.02  |  0.02  | -0.023 | -0.037 |
| IC c_delta10 vs 30s move | -0.037 | -0.011 | -0.007 | -0.003 | -0.001 | -0.042 |
| IC c_es5 vs 30s move     | -0.01  | -0.001 | -0.018 | -0.009 | -0.021 | -0.005 |
| IC c_imb10 vs 30s move   | -0.044 |  0.014 |  0.01  |  0.011 | -0.004 |  0.008 |
| IC c_ofi10 vs 30s move   | -0.029 |  0.04  |  0.023 |  0.013 | -0.001 | -0.043 |
| IC c_p10 vs 30s move     |  0.062 | -0.011 |  0.005 |  0.006 |  0.021 |  0.01  |
## 5. LIVE-CAL view: the positive LIVE numbers are the stop-cost credit (STRUCTURE), not L2 information (post-hoc, labelled)
On the LIVE-CAL basis (stop-class exit 2.45 pt worse than nominal) 47 of the 52 cells have a stack delta >= 0 in BOTH PRE and X' (unconditional and conditioned alike; medians over the 52: PRE +7,839, X' +5,880, HOLD +7,884, L6M +6,796 $/wk research lots; L6M MDE 6-16k), while the same cells are negative on N. The reason is mechanical: a wait that ends in a MARKET exit (0.995) replaces a stop-class fill (2.45 live, 1.01 N) and credits the 1.45 pt difference, whatever the condition. It is not selected here (selection was on N, per the prereg), the conditioned LIVE gains do not differ from the unconditional one by more than the placebo noise, and a fixed cost-model differential is STRUCTURE under the user's addendum. The clean statement of the effect - exit by market order at touch + delta instead of resting a stop order - is below (post-hoc reference, 3 delta values x 3 bases; no L2 condition):
| exit at touch + delta s (market, 0.995) instead of the stop order | basis | Y26 | L3M | L6M (MDE) | HOLD | PRE | X' | L6M live lots | per contract L6M / HOLD / PRE / X' |
|---|---|---|---|---|---|---|---|---|---|
| delta 1 s | N | +7,254 | -3,447 | +454 (+9,712) | -1,948 | -6,599 | -3,719 | +665 | -0.07 / -0.07 / -0.15 / -0.09 |
| delta 1 s | NATIVE | +8,507 | -813 | +2,516 (+9,161) | +100 | -4,537 | -1,778 | +1,509 | +0.05 / +0.05 / -0.04 / +0.03 |
| delta 1 s | LIVE | +14,745 | +8,632 | +11,933 (+10,067) | +9,182 | +5,307 | +5,312 | +4,473 | +0.56 / +0.57 / +0.47 / +0.54 |
| delta 2 s | N | -370 | -5,364 | +307 (+8,390) | -318 | -3,305 | -3,176 | +1,301 | -0.08 / -0.06 / -0.09 / -0.05 |
| delta 2 s | NATIVE | +882 | -2,731 | +2,370 (+8,204) | +1,730 | -1,243 | -1,235 | +2,145 | +0.04 / +0.06 / +0.03 / +0.07 |
| delta 2 s | LIVE | +7,120 | +6,714 | +11,786 (+8,844) | +10,812 | +8,601 | +5,855 | +5,109 | +0.56 / +0.58 / +0.54 / +0.58 |
| delta 3 s | N | -11,898 | -7,140 | -1,232 (+10,362) | -2,103 | -2,954 | -4,903 | +85 | -0.06 / -0.04 / -0.03 / -0.03 |
| delta 3 s | NATIVE | -10,645 | -4,507 | +831 (+10,016) | -55 | -892 | -2,962 | +928 | +0.06 / +0.08 / +0.09 / +0.09 |
| delta 3 s | LIVE | -4,407 | +4,938 | +10,247 (+10,597) | +9,027 | +8,952 | +4,127 | +3,892 | +0.57 / +0.59 / +0.59 / +0.60 |
Reading: on N (stop 1.01) and NATIVE (1.28) a market exit at touch + 1..3 s is worth -3..+3k $/wk (inside MDE ~9-10k); on LIVE-CAL (2.45) it is +10-12k $/wk in L6M and +4-9k in PRE / X' (>= 0 in every window for delta 1 s; per contract +0.56 per planned-lot trade, i.e. about +1.4 pt per stopped trade), because the post-touch drift in the first 1-3 s is only -0.1..-0.3 pt. **This is an EXECUTION finding about the live stop-order cost (n = 21 live stop fills, SE ~0.75; market-class exits +0.80 +/- 0.22 vs the path, n = 14), not an order-book edge; its break-even is a live stop cost of about 1.1-1.3 pt (N 1.01: 0; native 1.28: +0.04 per contract).** Passed to the lead as a cost-model item for the live join/fallback stop logic.
## 4. Learned
1. Stop-touch confirmation (waiting for a stop-run rebound) is regime-dependent: slightly positive per contract in PRE/X' (rebound +0.5 pt at 30 s), negative in the last 12 months (continuation -0.45 pt); no L2 feature separates rebound from continuation (|IC| <= 0.04).
2. Together with cycles 1-9, INFO and RO-2 this closes the loss side on mbp-10 + 1-s aggregates: the remaining open items need raw MBO (order lifetime at best, cancel bursts, queue position and full-depth resting size at the stop, level age) - pull list and free quotes in DS3_L2_UF_LOSS_C6.md section 6.
Files: code/uf10/{cells10,engine10,stageB10}.py; out/uf/loss10/{stageA10.pkl,stageA10_PRE_X.csv,selection_PRE_X.json,stageB10.pkl,info_PRE_X.csv,cond_cells_view.csv}; DEAD_CELLS.csv +52 (UFL10).
