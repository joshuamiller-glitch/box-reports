# DS3_PRE_DIAGNOSIS - why the Sunday composite cuts L6M maxDD 88 -> 23 yet deepens PRE maxDD 162 -> 241, and the regime switch (B1, 2026-10-31). POST-HOC diagnosis, nothing here is a PASS, nothing live, Shadow only

Capped 20260206, no post-cap file opened, UNTOUCHED never read. Engine DS3_ONE_CONVENTION (oc_lib.py unchanged, dd_lib wrappers, per-row piece switches in `code/prediag/pd_gate.py`: ties exact, none gated = composite to 0.0, all rows gated = LOO_p to 0.0 for ER / zone / PE / Asia cut / Native; the split switch acts on non-PE rows only so it is not identical to LOO_split). Live lots, slip +0.25, parity stop, K6 70/30, running max over taken signals, lock off unless stated. Windows L3M 14 / L6M 28 / HOLD 32 / PRE 75 / X' 44 weeks (ALL 149). Preregs: `l2vast/ds3/prereg/PREDIAG_prereg.md` (sha256 c58867cc5222384194646fe4ad542f0d85aa67f89e732c56ab95c988e6dcf8b4), `..._addendum1.md` (49702fb1e2dc4b86659dbd64955a59d69b11ed0aaeaa0a59fa44209bc04263e9, written before any gated scoring), `..._addendum2.md` (0d9212d64ca6bb1d59d72a1fbc4f82828adff500dc27910f3f5ff3d27194641b, exploratory, written after the 832 family was scored); all in DECISIONS.md. dead_lookup before: NOT FOUND x3 (gate-by-state specs); cells appended after (program PREDIAG). Code `l2vast/ds3/code/prediag/`, outputs `l2vast/ds3/out/prediag/`, gate spec `out/prediag/gate_spec.json`.

**INTEGRITY, stated first.** (1) The PRE weeks were chosen BECAUSE they are bad, so the diagnosis is post-hoc by construction; the regime comparison, the piece attribution and the choice of what to test were all shaped by looking at them. (2) Effective sample: PRE 75 weeks (ESS about 55 after weekly autocorrelation), X' 44 (ESS 31), and the whole deepening is ONE drawdown path of 7 weeks (2024-08-19 .. 2024-09-30) plus a few single bad weeks: three or four independent episodes. (3) The +49% PRE deepening itself is not distinguishable from zero: composite minus as-is PRE maxDD = +79k, 4-week-block bootstrap 95% CI [-72, +233]k (P(>0) = 0.78); the L6M cut is -65k [-103, +3], X' -196k [-424, -11], ALL -75k [-200, +135]. (4) The gate below was selected on PRE + X' only (rule fixed in the prereg addendum before scoring) and judged on L6M / HOLD; the reversed check (select on HOLD, judge on PRE / X') is in section 4. (5) The L6M as-is maxDD (88k) is one week (2026-01-19), the L6M composite maxDD (23k) is also a single path.

## PAGE 1

### The answer in four lines
1. **Where the deepening is.** One 7-week path, 2024-08-19 to 2024-09-30: composite 761k -> 520k (-241k) against the as-is 365k -> 208k (-158k to that week, -162k one week later). Weeks 202436 / 202437 / 202440 alone are composite-minus-as-is -32 / -77 / -23k. Outside that path the composite also gives back 88k (2024-10-21), 79k (2025-02-10), 53k (2024-02-05) against the as-is, and takes them back in better weeks: over PRE the composite-minus-as-is weekly delta sums to -937k in losing weeks and +1273k in winning weeks.
2. **Which piece.** The ER sizer on the P6 (PE) book: on P6 rows with 5-min ER20 >= 0.3 (sized x1.5) the as-is $/row is -599 in X' (2023), +600 in PRE, -1,390 in the Sep-Oct 2024 path weeks (hit 43%) and +928 in L6M. The sizer is a bet that the ER-high edge on P6 persists; it paid in L6M, lost in 2023 and in Sep-Oct 2024. In the path weeks the ER sizer is -14.5k/wk and the PE 45-s confirm -11.5k/wk (zone skip +8.2k/wk); in the 10 worst delta weeks ER is -25.9k/wk and the zone skip -16.0k/wk (it skipped winners). Removing the ER sizer takes PRE maxDD 241 -> 140; removing ER + PE 241 -> 156; the rest of the six pieces barely move PRE.
3. **Is there a causal state (computable at the signal second) that separates PRE-bad from L6M-good weeks?** **No, not beyond chance.** The regime frame places the PRE-bad weeks in the middle of the distribution on vol, ES-NQ correlation, ER, session mix and depth; only days-since-trend (4.4 vs 8.6 days, p = 0.04) and the ER-high share (0.46 vs 0.41, p = 0.07) lean, and the one variable that separates cleanly (fill cost) is an era artefact. 832 candidate gates (104 states x 8 piece-sets) were scored on the engine: the real family's gain distribution is the same as the family of 832 RANDOM whole-day gates of the same on-share (median -6.3 vs -6.1k, p95 +93 vs +102k, max +226 vs +205k); P(best of 832 random day-gates is at least as good as the best real gate) = 0.64. The nested purged CV recovers 53k of 737k block-maxDD for the all-six gate (3 of 6 folds positive) and the reversed check does not transfer (HOLD-selected gates improve X' in 33% of cases).
4. **The regime switch.** The rule-selected gate, in D6 terms, is **G1: switch all six pieces off when the mean number of raw signals per label day over the previous 5 label days is >= 73.6** (the 67th percentile of that variable in PRE + X'); the gated composite is the as-is stack on those days. It cuts PRE maxDD 241 -> 156 (-35%), leaves X' at 121 (the state is never on in 2023, which is why X' "agrees"), costs L6M maxDD 23 -> 25 and L6M mean -3.4k/wk (MDE 10.8). It beats its own single-gate placebos (PRE+X' loss 544k vs placebo p5 649k shuffled / 619k whole-day) **but not the family-wise null**, and re-expressed on D6 books only (G1_D6, 28.6 signals/day) it breaks the recent windows (L6M maxDD 23 -> 86, L6M mean -12.3k/wk). It is an era proxy (signals/day doubled from 2023 to 2025). G3 (ER sizer + PE off when the trailing-5-day NQ range is in the bottom 20% of its own 60-day history) is the only gate that cuts PRE by 21% and leaves every other window unchanged or better (HOLD 97 -> 66), but it was picked after the look and its PRE result is at the placebo median (rank 26-44%). **It is not a signature; treat G1 / G3 as Shadow candidates at most, with the odds stated.**

### The gated risk table (lock off, recent-first; cell = maxDD $k · weekly SD $k · mean $k/wk; PRE + X' selection windows, L-windows the look)

| row | L3M maxDD · SD · mean ($k) | L6M maxDD · SD · mean ($k) | HOLD maxDD · SD · mean ($k) | PRE maxDD · SD · mean ($k) | X' maxDD · SD · mean ($k) | ALL maxDD · SD · mean ($k) |
|---|---|---|---|---|---|---|
| as-is stack (no rules) | 88 · 46 · +12.2 | 88 · 44 · +21.7 | 144 · 54 · +21.9 | 162 · 50 · +18.6 | 317 · 29 · -3.4 | 317 · 47 · +13.1 |
| Sunday composite, UNGATED | 21 · 45 · +34.4 | 23 · 43 · +41.1 | 97 · 52 · +38.6 | 241 · 56 · +23.1 | 121 · 33 · +8.0 | 241 · 50 · +22.3 |
| composite + G1 (activity gate, rule-selected) | 25 · 51 · +28.7 | 25 · 48 · +37.7 | 97 · 55 · +35.6 | 156 · 51 · +21.6 | 121 · 33 · +8.0 | 156 · 48 · +20.9 |
| composite + G1_D6 (same gate, D6-books count) | 86 · 46 · +10.9 | 86 · 47 · +28.9 | 97 · 54 · +27.8 | 156 · 53 · +22.3 | 121 · 33 · +8.0 | 156 · 49 · +19.5 |
| composite + G_ER (ER sizer off when ES-NQ corr low) | 48 · 43 · +32.7 | 48 · 40 · +38.1 | 72 · 47 · +36.9 | 142 · 56 · +25.6 | 136 · 29 · +6.6 | 142 · 49 · +22.8 |
| composite + G2 (best rank-form gate by the rule) | 45 · 49 · +24.9 | 45 · 47 · +35.8 | 97 · 55 · +33.9 | 156 · 47 · +22.5 | 156 · 31 · +4.9 | 156 · 46 · +20.1 |
| composite + G3 (quiet-range gate, ER sizer + PE off; picked AFTER the look) | 21 · 44 · +35.3 | 23 · 42 · +39.5 | 66 · 46 · +37.0 | 190 · 53 · +23.1 | 115 · 30 · +7.5 | 190 · 47 · +21.8 |

| row | worst-20 PRE | worst-20 X' | worst-20 ALL | Calmar ALL (mean/maxDD) | mean/\|worst-20\| ALL | vs ungated: mean Δ (MDE) L3M · L6M · HOLD · PRE · X' | maxDD change PRE · X' · L6M |
|---|---|---|---|---|---|---|---|
| as-is stack (columns 7-8 are as-is MINUS composite) | -811 | -572 | -1161 | 0.041 | 0.0112 | -22.3 (22.3) · -19.4 (17.5) · -16.7 (17.3) · -4.5 (13.2) · -11.4 (14.0) | -33% · +163% · +285% |
| Sunday composite, UNGATED | -875 | -420 | -1098 | 0.092 | 0.0203 | n/a · n/a · n/a · n/a · n/a | - · - · - |
| composite + G1 (activity gate, rule-selected) | -716 | -420 | -979 | 0.134 | 0.0213 | -5.7 (17.7) · -3.4 (10.8) · -3.0 (9.5) · -1.5 (9.1) · +0.0 (0.0) | -35% · +0% · +9% |
| composite + G1_D6 (same gate, D6-books count) | -767 | -420 | -1111 | 0.125 | 0.0176 | -23.5 (21.9) · -12.3 (16.9) · -10.7 (14.9) · -0.8 (9.3) · +0.0 (0.0) | -35% · +0% · +274% |
| composite + G_ER (ER sizer off when ES-NQ corr low) | -738 | -360 | -990 | 0.160 | 0.0230 | -1.7 (8.0) · -3.0 (6.8) · -1.6 (7.2) · +2.5 (5.7) · -1.4 (6.7) | -41% · +13% · +112% |
| composite + G2 (best rank-form gate by the rule) | -639 | -447 | -943 | 0.128 | 0.0213 | -9.5 (17.5) · -5.3 (10.1) · -4.7 (8.9) · -0.6 (8.9) · -3.1 (5.8) | -35% · +30% · +99% |
| composite + G3 (quiet-range gate, ER sizer + PE off; picked AFTER the look) | -786 | -391 | -937 | 0.115 | 0.0232 | +0.9 (2.5) · -1.6 (3.9) · -1.6 (7.8) · +0.0 (4.4) · -0.5 (3.8) | -21% · -5% · +0% |

| gate | equal-risk c (ALL worst-20 matched to ungated composite, verified run) | verified ALL worst-20 | equal-risk mean Δ vs ungated $k/wk: L3M · L6M · HOLD · PRE · X' | maxDD at c*: L6M · PRE · X' |
|---|---|---|---|---|
| G1 | 1.138 | -1055 (target -1098) | -5.6 · -2.0 · -1.1 · -0.5 · +0.1 | 31 · 168 · 144 |
| G1_D6 | 0.986 | -1063 (target -1098) | -21.0 · -12.7 · -10.8 · -2.0 · -1.6 | 67 · 149 · 127 |
| G_ER | 1.113 | -1079 (target -1098) | +0.4 · +2.0 · +3.3 · +2.8 · -0.4 | 46 · 173 · 150 |
| G3 | 1.183 | -1103 (target -1098) | +0.4 · +0.3 · +0.2 · +4.4 · +0.3 | 26 · 193 · 145 |


*Reading.* G1 and G1_D6 differ only in what is counted (all raw signals of the ten books in the universe vs signals of live D6 books with a session lot) and the overlap of their state-on rows is 77%; the recent windows differ by 60k of maxDD. That sensitivity is itself the finding: the PRE improvement is not a property of "high activity", it is a property of which weeks the switch happens to bite. G_ER is the cleanest economically (ER sizer off when the ES-NQ 20-min correlation at the signal second is <= 0.897, 19% of rows): PRE 241 -> 142, mean +2.5k/wk in PRE, but L6M 23 -> 48 and X' 121 -> 136. Only 3 of the 832 gates cut PRE maxDD by >= 15% without making X', L6M, HOLD or L3M worse (and the mean ok): G3 below is the cleanest of them (rank-form quiet-range state, 20% of rows, PRE 241 -> 190, HOLD 97 -> 66, L6M unchanged, mean cost -1.6k/wk in L6M inside its MDE of 3.9) and it was picked AFTER the look at L6M / HOLD, so its recent windows are no longer a clean test; 6 of the 832 RANDOM day-gates of null replicate 0 and 7 of the 832 RANDOM day-gates of null replicate 1 satisfy the same all-window criterion, so the real family is no richer in such gates than chance. RISK-KEEP (DD-1 definition: L6M maxDD cut >= 20% with the mean inside MDE and beating the placebo) is **no** for every gate (the L6M ungated maxDD is already 23k; no gate lowers it).

**The plain sentence.** If 2024-25 comes back, the gated composite's maxDD is 156k vs 241k ungated (PRE window, gate G1) -- but that number is IN-SAMPLE (the gate was picked on those very weeks, from 832 candidates), it is no better than what the best of 832 random day-gates gets (P = 0.64), and the honest purged-CV expectation is about 10% off the PRE block maxDD, not 35%.
 In plain numbers: ungated 241k, gated (G1) 156k; a single random whole-day gate with the same on-share has a median PRE maxDD of 229k (5th percentile 151k), so most of the 241 -> 156 is what choosing among many gates delivers on one path. The same sentence for the other gates: G_ER 142k, G2 156k, G3 190k (G3 also leaves L3M / L6M untouched, but its PRE result sits at the placebo median).

## 0. What was done (and what was reused)

Stored DD-1 daily series (`out/drawdown/main_*.pkl`: as-is, composite, leave-one-out per piece, lock off and 12R) for sections 1-2; the same engine re-run with per-row piece switches for section 5 (about 2,000 runs of about 4 s). Per-row dollars of the composite, the as-is and the leave-one-outs (`out/prediag/rowpnl_off.pkl`) attribute the weekly differences to signals. Regime frame: `recentedge3` / `regimestress` (day and week), rebuilt per kept signal here (`rowfeat2.parquet`).

## 1. Which weeks of PRE carry the deepening

Composite DD path, with dates (label weeks start Monday; $k):

|   ISO label wk |   week start |   as-is wk $k |   composite wk $k |   composite minus as-is $k |   as-is cum $k |   composite cum $k |   as-is DD $k |   composite DD $k |
|----------------|--------------|---------------|-------------------|----------------------------|----------------|--------------------|---------------|-------------------|
|         202433 |     20240812 |             0 |                32 |                         31 |            365 |                761 |             0 |                 0 |
|         202434 |     20240819 |           -83 |               -10 |                         73 |            282 |                751 |            83 |                10 |
|         202435 |     20240826 |           -19 |               -19 |                          0 |            263 |                732 |           102 |                28 |
|         202436 |     20240902 |           -44 |               -76 |                        -32 |            219 |                656 |           146 |               105 |
|         202437 |     20240909 |             8 |               -68 |                        -77 |            227 |                588 |           138 |               173 |
|         202438 |     20240916 |             8 |                -3 |                        -11 |            236 |                585 |           130 |               176 |
|         202439 |     20240923 |            68 |                54 |                        -14 |            304 |                639 |            61 |               122 |
|         202440 |     20240930 |           -96 |              -120 |                        -23 |            208 |                520 |           158 |               241 |
|         202441 |     20241007 |            -4 |                26 |                         30 |            203 |                545 |           162 |               216 |

The ten worst composite-minus-as-is weeks in PRE (post-hoc ranking; 1 of them are on the DD path):

|   rank |   ISO label wk |   week start |   as-is $k |   composite $k |   composite minus as-is $k |   composite DD at wk end $k | on composite DD path   |
|--------|----------------|--------------|------------|----------------|----------------------------|-----------------------------|------------------------|
|      1 |         202443 |     20241021 |         56 |            -32 |                        -88 |                         234 |                        |
|      2 |         202507 |     20250210 |         50 |            -29 |                        -79 |                          69 |                        |
|      3 |         202437 |     20240909 |          8 |            -68 |                        -77 |                         173 | yes                    |
|      4 |         202406 |     20240205 |         31 |            -23 |                        -53 |                          49 |                        |
|      5 |         202503 |     20250113 |         37 |            -11 |                        -48 |                          11 |                        |
|      6 |         202511 |     20250310 |        168 |            122 |                        -46 |                           0 |                        |
|      7 |         202525 |     20250616 |         98 |             53 |                        -45 |                           5 |                        |
|      8 |         202515 |     20250407 |         50 |              6 |                        -43 |                           0 |                        |
|      9 |         202516 |     20250414 |        -11 |            -50 |                        -40 |                          50 |                        |
|     10 |         202412 |     20240318 |         84 |             50 |                        -34 |                          21 |                        |

The composite's PRE maxDD (-241k) is a 7-week path starting at the 2024-08-12 peak; the as-is's (-162k) is the same path to the next week. The deepening is therefore not a different drawdown, it is the same drawdown made 1.5x deeper by a sizer on the book that was losing. Over PRE the composite is ahead by +336k cumulative (it is a bigger-variance stack: weekly SD 56k vs 50k, ratio 1.10; in L6M the ratio is 0.97, in X' 1.13).

## 2. Which piece is on and responsible

Piece effect per week = composite minus composite-without-the-piece (DD-1 leave-one-out series, mean $k/wk over the week cluster; "lock" = combined 12R week lock):

| lock   | piece   |   PRE path wks (7) |   PRE 10 worst-delta wks |   PRE all (75) |   L6M good tercile (10) |   L6M all (28) |
|--------|---------|--------------------|--------------------------|----------------|-------------------------|----------------|
| off    | split   |               -1.2 |                     -0.4 |            1.5 |                     6.1 |            4.6 |
| off    | zone    |                8.2 |                    -16   |            2   |                    18   |            4   |
| off    | er      |              -14.5 |                    -25.9 |            3.9 |                    30.2 |           14.1 |
| off    | pe      |              -11.5 |                     -5.8 |            0.5 |                    20.7 |            5.3 |
| off    | cut     |               -0.1 |                     -2.4 |            0.1 |                    -1   |           -0.4 |
| off    | nat     |                1.3 |                      1.6 |            1.2 |                     1.5 |            0.9 |
| 12R    | split   |                0.3 |                      1.4 |            0.9 |                     5.6 |            5.5 |
| 12R    | zone    |                0   |                     -6   |            4.5 |                    22   |            4.2 |
| 12R    | er      |                5   |                    -14.5 |            4.9 |                    34.6 |           12.2 |
| 12R    | pe      |                7.1 |                      2.8 |            0.4 |                    23   |            3.2 |
| 12R    | cut     |                2.4 |                      0.8 |           -0.1 |                    -1.3 |           -0.3 |
| 12R    | nat     |                2.2 |                      2.6 |            1.1 |                     1.2 |            0.8 |

Mechanism (as-is $ per row; hit rate; composite $ per row):

| group                          |   rows |   as-is $/row |   as-is hit rate |   composite $/row |
|--------------------------------|--------|---------------|------------------|-------------------|
| X P6 ER>=0.3                   |    285 |          -599 |             0.47 |               681 |
| X P6 ER<0.3                    |    339 |           292 |             0.53 |               312 |
| X other books ER>=0.3          |    871 |            72 |             0.52 |               116 |
| PRE P6 ER>=0.3                 |    674 |           600 |             0.54 |              1280 |
| PRE P6 ER<0.3                  |    731 |           111 |             0.51 |                96 |
| PRE other books ER>=0.3        |   1858 |           205 |             0.54 |               285 |
| HOLD P6 ER>=0.3                |    283 |           943 |             0.55 |              2350 |
| HOLD P6 ER<0.3                 |    334 |           305 |             0.51 |               218 |
| HOLD other books ER>=0.3       |    773 |           302 |             0.55 |               392 |
| L6M P6 ER>=0.3                 |    246 |           928 |             0.55 |              2358 |
| L6M P6 ER<0.3                  |    296 |           184 |             0.51 |               202 |
| L6M other books ER>=0.3        |    682 |           318 |             0.55 |               423 |
| L3M P6 ER>=0.3                 |    120 |           677 |             0.53 |              1684 |
| L3M P6 ER<0.3                  |    163 |            44 |             0.5  |               301 |
| L3M other books ER>=0.3        |    350 |           288 |             0.54 |               291 |
| PRE_path(202434-40) P6 ER>=0.3 |     61 |         -1390 |             0.43 |             -3473 |
| PRE_path(202434-40) P6 ER<0.3  |     76 |          -520 |             0.46 |               197 |
| PRE_worst10_delta P6 ER>=0.3   |    119 |           475 |             0.53 |               -28 |
| PRE_worst10_delta P6 ER<0.3    |    126 |          2273 |             0.63 |               465 |
| L6M_good_tercile P6 ER>=0.3    |     97 |          1403 |             0.58 |              4279 |
| L6M_good_tercile P6 ER<0.3     |    118 |          -796 |             0.45 |               -14 |

Quarterly as-is $/row of P6 ER>=0.3 rows: 2023Q2 -967, Q3 -509, Q4 -511, 2024Q1 -7, Q2 -330, Q3 +490, Q4 +866, 2025Q1 +906, Q2 +920, Q3 +1,336, Q4 +982, 2026Q1 -17. The ER-high P6 edge was negative through 2023 and early 2024, positive from 2024Q3, and negative again in the Aug-Sep 2024 path weeks even though 2024Q3 as a whole was positive; the sizer (x1.5 there) and the PE confirm (which turns more of those rows into entries) amplify whatever that edge is doing.

Piece removal by window (maxDD $k; lock off and 12R). Under the same 12R lock the composite is shallower than the as-is in PRE (233 vs 276) but still deeper than the UNLOCKED as-is (162); the lock does not remove the PRE deepening (241 -> 233):

| scenario           | lock   |   maxDD L3M |   L6M |   HOLD |   PRE |   X' |   worst-20 PRE |   worst-20 X' |   mean L6M |   mean PRE |   mean X' |
|--------------------|--------|-------------|-------|--------|-------|------|----------------|---------------|------------|------------|-----------|
| ASIS               | off    |          88 |    88 |    144 |   162 |  317 |           -811 |          -572 |       21.7 |       18.6 |      -3.4 |
| COMP               | off    |          21 |    23 |     97 |   241 |  121 |           -875 |          -420 |       41.1 |       23.1 |       8   |
| COMP minus er      | off    |          43 |    43 |     74 |   140 |  163 |           -684 |          -373 |       28   |       19.6 |       5.6 |
| COMP minus pe      | off    |          42 |    42 |    113 |   199 |  143 |           -963 |          -530 |       36.7 |       22.4 |       8.9 |
| COMP minus zone    | off    |          57 |    57 |    143 |   304 |  118 |           -977 |          -576 |       35.8 |       20.4 |       4.2 |
| COMP minus split   | off    |          32 |    32 |    105 |   233 |  119 |           -905 |          -422 |       36.5 |       21.6 |       7.4 |
| COMP minus cut     | off    |          24 |    37 |     73 |   240 |  151 |           -872 |          -453 |       41.5 |       23   |       7.3 |
| COMP minus nat     | off    |          24 |    24 |    103 |   250 |  125 |           -903 |          -436 |       40.2 |       21.9 |       7.2 |
| ASIS               | 12R    |         105 |   116 |    116 |   276 |  436 |           -585 |          -584 |       10.4 |        9.7 |      -7.2 |
| COMP               | 12R    |          27 |    27 |     35 |   233 |  120 |           -608 |          -468 |       32.3 |       15.1 |       1   |
| COMP minus er      | 12R    |          47 |    58 |     59 |   314 |  258 |           -586 |          -522 |       21   |        9.4 |       1.1 |
| COMP minus pe      | 12R    |          44 |    44 |     51 |   283 |  129 |           -670 |          -459 |       29.8 |       14.4 |       4   |
| COMP minus zone    | 12R    |          58 |    58 |     58 |   216 |  312 |           -571 |          -480 |       26.8 |       10.4 |      -6.6 |
| COMP minus split   | 12R    |          26 |    43 |     43 |   232 |  172 |           -638 |          -476 |       26.8 |       13.1 |      -0.4 |
| COMP minus cut     | 12R    |          28 |    28 |     33 |   249 |  159 |           -624 |          -473 |       32.6 |       15.2 |      -0.2 |
| COMP minus nat     | 12R    |          27 |    27 |     35 |   247 |  152 |           -631 |          -471 |       31.5 |       14.1 |      -0.3 |
| COMP minus er+pe   | off    |          38 |    38 |     66 |   156 |  164 |           -746 |          -358 |       28.5 |       19   |       6   |
| COMP minus er+zone | off    |          65 |    65 |    139 |   167 |  112 |           -766 |          -383 |       23.1 |       17.4 |       3.1 |

## 3. What the market was doing (regime frame)

Weekly means over kept signals of books 0-6 (ST/WT zero lots):

| variable                              |   PRE-bad (path 7 + worst-10 delta, n=16) |   PRE path 202434-40 (7) |   PRE 10 worst delta |   L6M good tercile (10) |   PRE all (75) |   L6M all (28) |   X' all (44) |
|---------------------------------------|-------------------------------------------|--------------------------|----------------------|-------------------------|----------------|----------------|---------------|
| kept signals/wk                       |                                    81.1   |                   76.7   |               84.3   |                 101.4   |         73     |         83.1   |        45.7   |
| 5-min realised vol at signal (median) |                                    17.78  |                   16.82  |               18.34  |                  18.58  |         15.94  |         16.43  |        11.43  |
| ES-NQ 20-min corr (median)            |                                     0.916 |                    0.924 |                0.911 |                   0.943 |          0.91  |          0.932 |         0.869 |
| 5-min ER20 at signal (mean)           |                                     0.292 |                    0.279 |                0.297 |                   0.281 |          0.293 |          0.288 |         0.313 |
| share of signals with ER20>=0.3       |                                     0.472 |                    0.428 |                0.493 |                   0.415 |          0.461 |          0.443 |         0.494 |
| days since last trend day             |                                     5.08  |                    5.7   |                4.23  |                   9.16  |          4     |          6     |         2.83  |
| prior-day range / ATR                 |                                     1.025 |                    0.93  |                1.106 |                   1.122 |          1.023 |          1.08  |         1.012 |
| VIX prior close                       |                                    20.2   |                   17.4   |               22     |                  17.9   |         17.7   |         16.9   |        15.4   |
| signals/day, trailing 5 d             |                                    85.1   |                   69.6   |               96.5   |                  73.5   |         67.6   |         69.6   |        40.9   |
| NQ range, trailing 5 d (pts)          |                                   471     |                  344     |              556     |                 397     |        370     |        372     |       225     |
| book depth10 (day median)             |                                    70.3   |                   67.7   |               71.3   |                  69.4   |         85.2   |         79.1   |       122.2   |
| same-day NQ range (pts)               |                                   438     |                  366     |              486     |                 462     |        385     |        410     |       240     |
| same-day 5-min ER (NQ)                |                                     0.072 |                    0.077 |                0.069 |                   0.069 |          0.082 |          0.078 |         0.084 |
| prior day = trend day (share)         |                                     0.417 |                    0.374 |                0.439 |                   0.35  |          0.428 |          0.432 |         0.417 |
| session share Asia                    |                                     0.339 |                    0.318 |                0.355 |                   0.328 |          0.315 |          0.332 |         0.26  |
| London                                |                                     0.261 |                    0.222 |                0.282 |                   0.269 |          0.249 |          0.242 |         0.209 |
| NY-AM                                 |                                     0.342 |                    0.397 |                0.308 |                   0.341 |          0.372 |          0.364 |         0.446 |
| NY-PM                                 |                                     0.058 |                    0.063 |                0.054 |                   0.063 |          0.064 |          0.063 |         0.085 |
| fill cost pts (era-dependent)         |                                     1.77  |                    1.25  |                2.09  |                   2.74  |          1.76  |          2.76  |         1.2   |

Percentile placement of the same sets among all 149 weeks is in `out/prediag/regime_pctile_by_set.csv` (PRE-bad weeks: vol 0.67, ES-NQ corr 0.60, ER 0.47-0.53, depth 0.25, signals/day 0.65-0.73, NY-AM share 0.37; L6M-good: vol 0.79, corr 0.80, depth 0.23, signals/day 0.83). Test, PRE-bad (16 weeks) vs L6M-good (10 weeks), sorted by p (28 variables tried, so p < 0.002 is the multiplicity line; none other than fill cost reaches it):

| variable                              |   median PRE-bad |   median L6M-good |   Mann-Whitney p |   boot 95% CI of median diff lo |     hi |
|---------------------------------------|------------------|-------------------|------------------|---------------------------------|--------|
| fill cost pts (era-dependent)         |            1.292 |             2.729 |            0.001 |                          -1.564 | -0.187 |
| days since last trend day             |            4.383 |             8.641 |            0.037 |                         -10.279 | -0.27  |
| share of signals with ER20>=0.3       |            0.46  |             0.411 |            0.073 |                           0.005 |  0.138 |
| kept signals/wk                       |           78     |           103     |            0.077 |                         -46.5   |  2.5   |
| ES-NQ 20-min corr (median)            |            0.928 |             0.95  |            0.087 |                          -0.052 |  0.007 |
| same-day NQ range (pts)               |          384.781 |           437.56  |            0.097 |                        -193.612 | 29.572 |
| 5-min realised vol at signal (median) |           16.647 |            18.733 |            0.179 |                          -5.298 |  0.971 |
| signals/day, same day                 |           71.332 |            94.181 |            0.216 |                         -35.181 |  6.459 |

Reading: the PRE-bad weeks are not a different market from the L6M-good weeks on the descriptive frame. Thin books (depth percentile 0.25) are common to both; the good weeks have higher relative vol and ES-NQ correlation and a longer gap since the last trend day (8.6 vs 4.4 days), the bad weeks have slightly more ER-high signals (0.46 vs 0.41). Fill cost is an era variable (1.3 vs 2.7 pts) and not a state.

## 4. Does a causal state computable at the signal second separate them

**Week-level association (fit PRE + X' = 118 weeks, one look at HOLD 32 weeks).** Spearman of the weekly mean of each candidate with the weekly composite-minus-as-is P&L:

| variable (weekly mean over kept signals)   |   n fit wks |   rho fit (PRE+X') |     p |   block-boot CI lo |    hi |   n look (HOLD) |   rho look |   p look |
|--------------------------------------------|-------------|--------------------|-------|--------------------|-------|-----------------|------------|----------|
| rk_corr                                    |         118 |              0.303 | 0.001 |              0.141 | 0.456 |              32 |      0.176 |    0.334 |
| rk_vol60                                   |         118 |              0.193 | 0.036 |              0.015 | 0.359 |              32 |      0.131 |    0.474 |
| vol60                                      |         118 |              0.188 | 0.042 |              0.03  | 0.327 |              32 |      0.148 |    0.42  |
| rk_rv5                                     |         118 |              0.185 | 0.045 |              0.016 | 0.352 |              32 |      0.276 |    0.127 |
| rk_tr5_sigday                              |         117 |              0.15  | 0.107 |             -0.044 | 0.332 |              32 |      0.082 |    0.656 |
| rk_tr5_rng                                 |         117 |              0.149 | 0.109 |             -0.046 | 0.339 |              32 |      0.106 |    0.564 |
| prev_rng_atrd                              |         118 |              0.14  | 0.132 |             -0.028 | 0.296 |              32 |      0.155 |    0.398 |
| days_since_trend                           |         118 |             -0.128 | 0.166 |             -0.293 | 0.061 |              32 |      0.367 |    0.039 |
| rk_er_eng                                  |         118 |             -0.128 | 0.168 |             -0.288 | 0.026 |              32 |     -0.427 |    0.015 |
| er_eng                                     |         118 |             -0.113 | 0.221 |             -0.269 | 0.066 |              32 |     -0.367 |    0.039 |

Rank ES-NQ correlation, volume and realised vol have a positive association in the fit set (the composite adds more in relatively hot, correlated markets: rho 0.19-0.30) that shrinks in HOLD (0.13-0.28, p 0.13-0.47); the ER-high share is negative in both (-0.11 fit, -0.47 look). Nothing is robust: rho CIs are wide (4-week block bootstrap) and 28 tests were run.

**Signal-level gate search (section 5 design).** 14 level variables + 12 trailing-60-day rank forms x 4 cuts = 104 states; 8 piece-sets; 832 gates; selection on PRE + X' block maxDD; 6 purged blocks. Gates passing the pre-stated rule (mean not worse than -0.5 MDE, beats ungated in >= 4 of 6 blocks): 172 of 832. Top eight by loss, with the recent look (the look was NOT used to choose; G1 was frozen before it was opened):

| gate (state#piece-set)           |   PRE+X' block-maxDD sum $k (ungated 737) |   held-out wins /6 |   PRE maxDD |   X' maxDD |   L3M maxDD |   L6M maxDD |   HOLD maxDD |   L6M mean Δ |   L6M MDE |   PRE mean Δ |
|----------------------------------|-------------------------------------------|--------------------|-------------|------------|-------------|-------------|--------------|--------------|-----------|--------------|
| lev:tr5_sigday / hi67#ALL6       |                                     544.4 |                  4 |       156.4 |      120.5 |        25   |        25   |         97   |         -3.4 |      10.8 |         -1.5 |
| lev:tr5_sigday / hi67#ERPE       |                                     564.3 |                  4 |       156.4 |      120.5 |        20.7 |        20.7 |         97   |         -5.3 |      10.2 |         -0.8 |
| rk60:vix_prev / hi67#ERPE        |                                     581   |                  5 |       155.8 |      156.4 |        45.5 |        45.5 |         97   |         -5.3 |      10.1 |         -0.6 |
| lev:days_since_trend / hi67#ERPE |                                     589.1 |                  5 |       163.8 |      120.5 |        38.5 |        38.5 |         99.8 |         -8.5 |      13.3 |          2.4 |
| rk60:rv5 / hi67#ALL6             |                                     591.5 |                  4 |       173.1 |       90.1 |        67.3 |        67.3 |        123.5 |        -11.5 |      16   |          1.6 |
| lev:corr / lo33#ER               |                                     593.9 |                  4 |       142.2 |      136.1 |        48.5 |        48.5 |         72   |         -3   |       6.8 |          2.5 |
| lev:days_since_trend / hi80#ERPE |                                     609.7 |                  6 |       174.6 |      116   |        33.5 |        33.5 |        105.3 |         -6.8 |      10.5 |          1.1 |
| rk60:rv5 / hi67#ER               |                                     611   |                  5 |       191.9 |       89.6 |        53.4 |        53.4 |        104.1 |        -10.4 |      11.5 |          2.2 |

**Nested purged CV (the honest estimate of the selection procedure).** For each held-out block pick the gate with the lowest training loss in the other blocks (2-week purge) and score it on the held-out block:

| piece-set   |   eligible gates (mean ok) |   nested-CV held-out block-maxDD gain $k (sum of 6 folds; ungated sum 737) |   folds with gain>0 | per fold $k (X1 X2 PRE1 PRE2 PRE3 PRE4)   |
|-------------|----------------------------|----------------------------------------------------------------------------|---------------------|-------------------------------------------|
| ALL6        |                         70 |                                                                       52.9 |                   3 | [-0.0, 0.0, -0.0, 68.1, -15.2, 0.0]       |
| CUT         |                         89 |                                                                       -4.3 |                   3 | [-0.0, 0.0, -0.0, 0.0, -4.3, 0.0]         |
| ER          |                         83 |                                                                       16.2 |                   3 | [-15.6, 5.6, -45.8, 49.3, 26.2, -3.4]     |
| ERPE        |                         84 |                                                                       30.8 |                   4 | [-35.9, 0.0, -0.0, 34.8, 31.9, 0.0]       |
| PE          |                        100 |                                                                       24.3 |                   3 | [-0.0, 0.0, 14.8, 78.2, -64.2, -4.5]      |
| SPLIT       |                         64 |                                                                      -13.1 |                   2 | [-0.4, -2.9, 18.6, -40.6, 15.9, -3.5]     |
| ZONE        |                         80 |                                                                       15.3 |                   4 | [2.1, -2.7, 34.0, -34.1, 13.9, 2.2]       |

All-six: +53k of 551k PRE block maxDD (about 10%), concentrated in one fold; ER only +16k with folds from -46 to +49. This is the number to carry, not the in-sample -35%.

**Reversed check (select on HOLD, judge on PRE / X').** Eligible gates 60 of 832; the best HOLD gate cuts HOLD maxDD 97 -> 73 and then PRE 241 -> 214 (mean -5.0), X' 121 -> 162 (worse); across eligible gates PRE improves in 62% and X' in 33%.

| gate selected on HOLD (eligible: halves not worse, mean ok)   |   HOLD maxDD (ungated 97) |   HOLD 1st half |   2nd half |   HOLD mean Δ |   MDE |   PRE maxDD (ungated 241) |   X' maxDD (ungated 121) |   PRE mean Δ |   X' mean Δ |
|---------------------------------------------------------------|---------------------------|-----------------|------------|---------------|-------|---------------------------|--------------------------|--------------|-------------|
| lev:days_since_trend / lo33#ERPE                              |                      73.3 |            73.3 |       21.4 |           0.1 |   7.4 |                     214.3 |                    162.2 |         -5   |         0.3 |
| lev:days_since_trend / lo33#ER                                |                      73.4 |            73.4 |       21.4 |           0.1 |   7.2 |                     194.4 |                    153.8 |         -2   |         0.3 |
| lev:er_eng / lo20#ER                                          |                      77.7 |            77.7 |       22.8 |           0.3 |   4.6 |                     203.2 |                    137.7 |          2.2 |         0.9 |
| lev:er_eng / lo20#ERPE                                        |                      81.2 |            81.2 |       21.3 |           0.3 |   5.6 |                     216.7 |                    146.9 |          1.9 |         0.7 |
| rk60:er_eng / lo33#ERPE                                       |                      84.4 |            84.4 |       15.6 |           1.2 |   9.2 |                     209.9 |                    140.4 |          1.5 |         0.6 |

**Exploratory P6 follow-through state (addendum 2, 18 gates, post-hoc, NOT part of the 832):** trailing 10 / 20 label-day mean as-is $ of P6 ER>=0.3 rows low or negative -> ER and/or PE off. PRE improves (241 -> 149 best) but X' worsens (121 -> 173): in 2023 the P6 ER-high edge was negative, so the state is on in X' and the composite there was better with the sizer on (the PE confirm turned those rows positive). The mechanism is real, the trailing estimate of it is not reliable at 10-20 days.

| P6 follow-through gate   |   on-share |   block-maxDD sum $k (ungated 737) |   wins/6 |   PRE maxDD |   X' maxDD |   L6M maxDD |   HOLD maxDD |   PRE mean Δ |   X' mean Δ |   L6M mean Δ |
|--------------------------|------------|------------------------------------|----------|-------------|------------|-------------|--------------|--------------|-------------|--------------|
| tfsP6_20 / lo33#ERPE     |        0.3 |                              611.9 |        5 |       148.6 |      173.3 |        22.9 |         97   |          0.8 |        -2.9 |         -3.3 |
| tfsP6_20 / neg#ER        |        0.4 |                              654.3 |        5 |       142.2 |      201   |        43.2 |         82.5 |          0   |        -3.6 |         -4.8 |
| tfsP6_20 / lo33#PE       |        0.3 |                              659.9 |        5 |       163   |      136.1 |        23.5 |         97   |          1.5 |        -1.7 |         -0.7 |
| tfsP6_20 / lo33#ER       |        0.3 |                              664.7 |        5 |       154.4 |      171.1 |        23.2 |         97   |         -0.4 |        -1.2 |         -2.1 |
| tfsP6_20 / neg#ERPE      |        0.4 |                              676.4 |        5 |       139.5 |      247.3 |        38.4 |         82.1 |          1.3 |        -4.4 |         -4.9 |
| tfsP6_20 / lo20#PE       |        0.2 |                              686.1 |        5 |       195.7 |      118.1 |        22.9 |         97   |          0.2 |        -1.2 |         -0   |
| tfsP6_20 / lo20#ERPE     |        0.2 |                              700.2 |        3 |       162.2 |      164.6 |        22.9 |         97   |          0.1 |        -2.7 |         -0   |
| tfsP6_20 / lo20#ER       |        0.2 |                              722.2 |        3 |       170   |      178.2 |        22.9 |         97   |          0.3 |        -1.5 |         -0   |

## 5. The regime switch

**Gate spec (D6 terms).** G1 (rule-selected). Inputs: the count of raw signals per label day (18:00 ET roll) of the signal generators in the universe (ten books), mean over the 5 label days strictly before today (at least 3 days). Formula: `state_on = mean(sig_count[d-5..d-1]) >= 73.6`. Threshold = 67th percentile of that variable over PRE + X' signals (2023-04 .. 2025-06). When on: split off (market entry, non-PE rows), zone skip off, ER sizer = 1.0, PE 45-s confirm off (market entry), Asia cut50 off, Native stop -> join 2.45. Piece by piece with the G1 state (maxDD $k L3M/L6M/HOLD/PRE/X'; mean change L6M/PRE): ER only 27/27/97/156/121 (-5.7/-0.6); PE only 39/39/97/182/121; zone only 53/53/97/212/121; Asia cut 23/37/97/238/121; Native 23/24/97/245/121; split 64/64/97/224/121; ER + PE 21/21/97/156/121 (-5.3/-0.8); all six 25/25/97/156/121 (-3.4/-1.5). **Most of the PRE effect comes with the ER sizer (ER only 156); PE only (182), zone only (212) and split only (224) also cut PRE but each costs L6M maxDD (39 / 53 / 64 vs 23); the Asia cut and Native stop do nothing.** On the DD path weeks the state is on in 54% / 100% / 17% / 44% of kept signals (weeks 202436 / 37 / 38 / 40) and saves 39 / 78 / 25 / 22k in those weeks.

D6 re-expression G1_D6: count only the D6 books' signals with a session lot (H6, K6, U6, P6, M6, A6); same rule gives threshold 28.6; PRE 241 -> 156 but L3M/L6M 21/23 -> 86/86 and L6M mean -12.3k/wk. Spec and caveats in `gate_spec.json`.

**Page-1 table, second half (tail, ratios, MDE):**

| row | worst-20 PRE | worst-20 X' | worst-20 ALL | Calmar ALL (mean/maxDD) | mean/\|worst-20\| ALL | vs ungated: mean Δ (MDE) L3M · L6M · HOLD · PRE · X' | maxDD change PRE · X' · L6M |
|---|---|---|---|---|---|---|---|
| as-is stack (columns 7-8 are as-is MINUS composite) | -811 | -572 | -1161 | 0.041 | 0.0112 | -22.3 (22.3) · -19.4 (17.5) · -16.7 (17.3) · -4.5 (13.2) · -11.4 (14.0) | -33% · +163% · +285% |
| Sunday composite, UNGATED | -875 | -420 | -1098 | 0.092 | 0.0203 | n/a · n/a · n/a · n/a · n/a | - · - · - |
| composite + G1 (activity gate, rule-selected) | -716 | -420 | -979 | 0.134 | 0.0213 | -5.7 (17.7) · -3.4 (10.8) · -3.0 (9.5) · -1.5 (9.1) · +0.0 (0.0) | -35% · +0% · +9% |
| composite + G1_D6 (same gate, D6-books count) | -767 | -420 | -1111 | 0.125 | 0.0176 | -23.5 (21.9) · -12.3 (16.9) · -10.7 (14.9) · -0.8 (9.3) · +0.0 (0.0) | -35% · +0% · +274% |
| composite + G_ER (ER sizer off when ES-NQ corr low) | -738 | -360 | -990 | 0.160 | 0.0230 | -1.7 (8.0) · -3.0 (6.8) · -1.6 (7.2) · +2.5 (5.7) · -1.4 (6.7) | -41% · +13% · +112% |
| composite + G2 (best rank-form gate by the rule) | -639 | -447 | -943 | 0.128 | 0.0213 | -9.5 (17.5) · -5.3 (10.1) · -4.7 (8.9) · -0.6 (8.9) · -3.1 (5.8) | -35% · +30% · +99% |
| composite + G3 (quiet-range gate, ER sizer + PE off; picked AFTER the look) | -786 | -391 | -937 | 0.115 | 0.0232 | +0.9 (2.5) · -1.6 (3.9) · -1.6 (7.8) · +0.0 (4.4) · -0.5 (3.8) | -21% · -5% · +0% |

**Equal-risk (lots re-scaled through the engine lot table so that the ALL worst-20 equals the ungated composite's, one verified run, integer rounding so the match is approximate):**

| gate | equal-risk c (ALL worst-20 matched to ungated composite, verified run) | verified ALL worst-20 | equal-risk mean Δ vs ungated $k/wk: L3M · L6M · HOLD · PRE · X' | maxDD at c*: L6M · PRE · X' |
|---|---|---|---|---|
| G1 | 1.138 | -1055 (target -1098) | -5.6 · -2.0 · -1.1 · -0.5 · +0.1 | 31 · 168 · 144 |
| G1_D6 | 0.986 | -1063 (target -1098) | -21.0 · -12.7 · -10.8 · -2.0 · -1.6 | 67 · 149 · 127 |
| G_ER | 1.113 | -1079 (target -1098) | +0.4 · +2.0 · +3.3 · +2.8 · -0.4 | 46 · 173 · 150 |
| G3 | 1.183 | -1103 (target -1098) | +0.4 · +0.3 · +0.2 · +4.4 · +0.3 | 26 · 193 · 145 |


**Placebos (200 draws each).** Shuffled-state = the gate vector permuted across signals within the same session (same on-share, breaks the day clustering); random whole-day = days switched on at random with the same on-share (keeps the clustering). Loss = PRE + X' sum of block maxDD (ungated 737k; lower is better):

| gate   |   gate PRE+X' loss $k | shuffled-state placebo p5 / median   | rank   | random whole-day gate p5 / median   | rank   | PRE maxDD: gate vs placebo                             | L6M maxDD: gate vs placebo median   |
|--------|-----------------------|--------------------------------------|--------|-------------------------------------|--------|--------------------------------------------------------|-------------------------------------|
| G1     |                   544 | 649 / 766                            | 0.0%   | 619 / 737                           | 0.0%   | 156 vs p5 157 / med 212 (shuf); p5 151 / med 229 (day) | 25 vs med 61 / 49                   |
| G1_D6  |                   570 | 636 / 768                            | 0.5%   | 608 / 742                           | 2.0%   | 156 vs p5 149 / med 204 (shuf); p5 144 / med 216 (day) | 86 vs med 63 / 56                   |
| G2     |                   581 | 623 / 741                            | 0.5%   | 608 / 702                           | 2.5%   | 156 vs p5 149 / med 195 (shuf); p5 149 / med 205 (day) | 45 vs med 43 / 38                   |
| G_ER   |                   594 | 666 / 737                            | 0.0%   | 640 / 719                           | 0.0%   | 142 vs p5 165 / med 206 (shuf); p5 180 / med 230 (day) | 48 vs med 39 / 28                   |
| G3     |                   643 | 642 / 741                            | 6.0%   | 624 / 711                           | 10.5%  | 190 vs p5 159 / med 196 (shuf); p5 159 / med 213 (day) | 23 vs med 41 / 37                   |

G1, G1_D6, G2 and G_ER beat their OWN placebos on the PRE + X' loss (rank 0-2.5%); G3 does not (rank 6-10.5%, its PRE maxDD 190 is at the placebo median 196-213). A random gate of the same on-share is on average neutral for the loss (median 702-768k vs 737k ungated) but worsens L6M maxDD (median 28-63k vs 23k). That is a single-gate test. The family-wise test is the next table.

**Family-wise null (832 random whole-day gates, one per real candidate, same piece-set and on-share; the same selection rule applied):** observed best loss 544k vs the null replicate's best 533k; bootstrap over resamples of 832 null gates: P(null best <= observed) = 0.64. Null gain distribution (median / p95 / max $k): -6.1 / 102 / 205; real family -6.3 / 93 / 226. Second null replicate: observed best 544k vs best 514k, P = 0.87, null gain median/p95/max -6.1 / 98 / 224.

| piece-set   |   best real gate loss $k |   best random day-gate (null rep0, 104 draws) |   best random day-gate (null rep1) |
|-------------|--------------------------|-----------------------------------------------|------------------------------------|
| ER          |                      594 |                                           564 |                                588 |
| ERPE        |                      564 |                                           533 |                                542 |
| PE          |                      642 |                                           666 |                                679 |
| ZONE        |                      635 |                                           626 |                                598 |
| SPLIT       |                      664 |                                           645 |                                619 |
| CUT         |                      713 |                                           712 |                                707 |
| ALL6        |                      544 |                                           546 |                                514 |

**Conclusion of the test.** The best real gate in each piece-set is no better than the best random day-gate in that piece-set. The PRE improvement of the switch is what a search over many ways of turning the ER sizer off on some days produces on one 7-week drawdown; it is not a detected state.

## 6. What this means for the A1-A4 programs and the brief

- The composite's PRE problem is the ER sizer on P6 (plus PE confirm) in one 7-week stretch where the ER-high P6 edge was negative; the combined 12R week lock does not remove it (composite 241 -> 233 with the lock; shallower than the as-is under the same lock, 276, but not than the unlocked as-is, 162).
- Untested option for A3 (sizers): a static size cap on the ER multiplier for the P6 book, priced against a same-volume placebo; this program found no state gate that beats chance.
- If the user wants a switch anyway: G1 / G_ER are Shadow items with the odds above (CV expectation about -10% of PRE block maxDD, family-wise p = 0.64); nothing is proposed for D6.

## 7. Limits

Post-hoc by construction; 3-4 independent bad episodes; 832-gate family plus 18 exploratory; thresholds from pooled PRE + X' signals (unsupervised leakage into CV folds only through the cut points); rank60 state needs 60 days of signal history in D6; the split switch acts on non-PE rows only; PB7 (A6) rows carry no flow features (state off for them in 14 of 26 variables); equal-risk c is a single interpolation plus one verification run (ALL worst-20 matched to within 4%); lock-off headline (12R lock runs of gated composites were not done: the lock interacts with the sizer's R and is a separate question).
