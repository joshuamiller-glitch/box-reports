# DS3_BARS_CAND3_DD - BARS-CAND-3 under DRAWDOWN FIRST: ST WT MV PB7 DN on the 28 dense store series, the ten engines on the Heikin-Ashi / Hull / LinReg candle series, a bracket grid; every cell priced as an ADDED BOOK on the Sunday composite and the as-is stack (agent G1, 2026-10-31/11-01). POST-HOC pricing inside a pre-registered selection; nothing here is a PASS

Research only; nothing live changes; nothing promoted. Masks capped 20260206 (X'=20230401..20240131, PRE=20240201..20250630, HOLD=20250701..20260206, L6M=20250801..20260206, L3M=20251106..20260206); UNTOUCHED never read, no post-cap file opened. Prereg `l2vast/ds3/prereg/G1_BARSCAND3DD_prereg.md` sha256 `722d97ee01d86d3fcb1d0aed5786dcdb6940900d26316c8f441ee37b9a2011d5` and ADDENDUM 1 (group S1b) sha256 `9c35953ac3761242465b892b867f0b77070a150604629f0865d6da0b1022e3b2`, both in DECISIONS.md before any scored statistic; selection files (PRE+X' only) hashed and logged before the ONE recent look of each group: S1 `81ead307...`, S2 and S1b in DECISIONS.md. Code `l2vast/ds3/code/g1/cand3/`, outputs `l2vast/ds3/out/g1c3/`, rows `l2vast/ds3/out/recent_wins/g1c3.csv`. Store = the rebuilt store (11 affected months from the de-duplicated tape, bpm frozen as TAPE-2); tie-out: ST and WT on kagi/16 re-run with this worker reproduce the stored NEWE daily tables in 27 of 27 months (trades and M sums identical).

## PAGE 1 - verdict

**Null on the risk picture. 0 RISK-KEEP confirmed in 1,976 cells.** Cells scored: S1 756 (ST WT MV PB7 DN x the 28 dense BARS-3 series x 5 sessions, native bracket; 840 registered, 84 had no trades), S2 400 (symmetric brackets 30/45/75/90 on the top-5 bar types of ST WT MV PB7), S1b 820 (all ten engines x 12 derived series: ha/10m 30m 45s 1h, hull and linreg 1m 3m 5m 15m; 840 registered). Dead_lookup: 0 hits in all three groups (out/g1c3/dead_lookup_s1.json, _s2, _s1b); DEAD_CELLS appended (program G1BARSC3DD, +1,976 rows; never rebuilt).
* **Selection (PRE+X' only, Sunday composite + book at 3 lots):** 5 / 4 / 4 cells pass the risk rule (maxDD cut > 0 and worst-20 better in PRE and in X', mean change not below -MDE in both) = 13 representatives, all tiny: best min(cut PRE, cut X') = 7.5%. Family-wise (200-draw common week-shift null of the best score over all cells of the group): null p95 0.25 / 0.26 / 0.21, the 13 scores are 0.00-0.075, family-wise p 0.57-1.00 (Sidak over the three groups: >= 0.92). Nothing exceeds what the best of ~600-800 cells does by chance.
* **Placebo (200 draws, same count, time of day, bracket and direction mix, random days):** 0 of the 13 beats it on both the L6M maxDD cut and the ALL-window worst-20 gain (ranks of the L6M cut 0.00-0.96, of the ALL worst-20 gain 0.45-1.00: the cells that rank high on one statistic rank low on the other); 1 of 13 is TOLERANT (S1b PE hull/3m pre, which deepens the L3M and L6M maxDD 16-17%).
* **The one mean-lens survivor (not a risk result):** S1b `PE hull/3m G` in the pre-open session (08:30-09:30 ET), a PRE+X'-selected representative and the only representative that is STRICT, TOLERANT and NOW-ONLY: per contract M +36.0 / +21.2 / +20.8 / +2.7 / +10.6 pts in L3M / L6M / HOLD / PRE / X' on 18 / 34 / 37 / 102 / 41 trades (MDE L6M 24.3, HOLD 23.5: inside), against a 1-min PE control of -5.4 in HOLD (D vs the 1-min engine in HOLD +7.2 [+0.6,+13.9], TW +26.2 [+7.4,+44.5]). On the composite at 3 lots it adds +1.5k/wk in L6M (MDE 1.9k) and +0.2k in PRE but DEEPENS the L6M maxDD 23k>27k (HOLD 97k>97k, PRE 241k>238k, X' 121k>116k), placebo ranks 0.41 (L6M cut) / 0.82 (ALL worst-20), family-wise p 1.00 on the risk rule. Tier LEAD (mean lens): 37 HOLD trades, one of 820 S1b cells, G6 fails, no risk benefit; PE is the P6 pullback engine (no D7 slot type) and Hull candles are not an NT8 bar type: no Shadow spec.
* **The recent look (one per group, all cells, view only):** 74 cells carry the L6M RISK-KEEP flag (maxDD cut >= 20% in L6M with the mean inside its MDE; S1 16, S2 12, S1b 46). The composite's L6M maxDD is a single 23k event; **in HOLD (the same event plus July 2025, maxDD 97k) 0 of the 74 cut by 20% and 66 deepen it**; 6 are shallower in both PRE and X'; the placebo could be run for 56 (DN is a limit-order engine: not run for its 18 flagged cells, 17 of which fail PRE-and-X' agreement): 50 beat it on the L6M cut alone (that statistic is the flag itself), **0 beat it on the L6M cut AND the ALL worst-20**.
* **Mean lens vs risk lens:** literal TOLERANT 42 cells (STRICT 98, NOW-ONLY 525; TOL-B 73 / TOL-nc 80 post-hoc beside). Read on the risk picture none of the 42 is a RISK-KEEP and only 7 are shallower in PRE and X' together; 25 of the 42 deepen the ALL worst-20 and 16 improve it (adding a book that earns on average still adds its bad weeks to the composite's bad weeks). The mean-positive cells and the risk-reducing cells are different cells.
* **Hedge value (stack worst-20, ALL, before>after when the book is added at 3 lots):** improves in 148 of 1976 cells (7.5%); the largest gain is 66k on -1,098k (6%) and comes with a deeper ALL maxDD (-10%) and a negative per-contract mean; no cell is anti-correlated enough to matter (compare DS3_HEDGE_SIDE: no sleeve is a demonstrated hedge).
* **Equal-risk:** for the 13 representatives the mean change at equal ALL worst-20 is -3.5k to +1.8k per week in L6M (MDE 1.6k-5.8k): nothing beyond MDE.
* **Plain sentence:** adding any of the new alt-bar books (ST, WT, MV, PB7, DN on dense Renko / range / Kagi / P&F / line-break / rv bars; the ten engines on Heikin-Ashi / Hull / LinReg candles; brackets 30-90) at 3 lots to the Sunday composite never lowers the maxDD or the worst-20 by more than a random same-volume book does, and the 74 recent-window flags are one-event artefacts of the 23k L6M drawdown (HOLD contradicts all of them). The bar-type search stays closed; the DRAWDOWN-FIRST measure does not reopen it.
* **Shadow / D7:** no cell earns a Shadow spec. Mapping for the record: ST and SM -> the D7 Supertrend slot; KB -> Keltner; HM -> HMA-VWAP; PE, PB, PB7, MV, WT, DN have no D7 slot type (a new D6 book type would be needed). Renko, range, Kagi, P&F, line-break, tick, volume and Heikin-Ashi are NT8-native bar types; Hull and LinReg candles are not (custom series).

## Counts by engine (Sunday composite, 3 lots)

| engine (D6 tag) | cells | eligible | pass PRE+X risk rule | RISK-KEEP flagged (L6M view) | PRE and X agree (any cut) | STRICT | TOLERANT | NOW-ONLY | hedge value > 0 |
|---|---|---|---|---|---|---|---|---|---|
| DN (N6) | 320 | 306 | 0 | 18 | 18 | 20 | 14 | 138 | 19 |
| HM (H6) | 60 | 36 | 0 | 1 | 5 | 6 | 2 | 21 | 7 |
| KB (K6) | 120 | 100 | 0 | 11 | 9 | 6 | 2 | 27 | 7 |
| MV (M6) | 300 | 286 | 5 | 14 | 20 | 8 | 2 | 66 | 18 |
| PB (library A6 variant) | 60 | 41 | 0 | 1 | 4 | 1 | 1 | 18 | 5 |
| PB7 (A6) | 286 | 230 | 0 | 10 | 15 | 18 | 7 | 81 | 26 |
| PE (P6) | 110 | 90 | 1 | 5 | 13 | 3 | 2 | 38 | 10 |
| SM (U6) | 120 | 79 | 3 | 3 | 18 | 12 | 6 | 35 | 26 |
| ST (S6) | 300 | 262 | 1 | 10 | 19 | 15 | 3 | 57 | 17 |
| WT (W6) | 300 | 264 | 3 | 1 | 28 | 9 | 3 | 44 | 13 |
| **all** | 1976 | 1694 | 13 | 74 | 149 | 98 | 42 | 525 | 148 |

### Counts per group (Sunday composite, 3 lots, view columns computed once per group after the selection file was hashed)

| group | cells scored | eligible (n PRE>=100, X>=40) | pass the PRE+X risk rule | family-wise null of the best score p50 / p95 / max | RISK-KEEP flagged (L6M view) | of which PRE and X agree | STRICT | TOLERANT (literal) | TOL-B / TOL-nc (post-hoc) | NOW-ONLY | per-contract L6M>0 | hedge value > 0 (ALL worst-20 improves) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S1 | 756 | 714 | 5 | 0.111 / 0.248 / 0.327 | 16 | 1 | 25 | 13 | 19 / 20 | 185 | 299 | 37 |
| S2 | 400 | 371 | 4 | 0.098 / 0.255 / 0.365 | 12 | 3 | 22 | 3 | 3 / 3 | 62 | 114 | 21 |
| S1b | 820 | 609 | 4 | 0.131 / 0.210 / 0.271 | 46 | 2 | 51 | 26 | 51 / 57 | 278 | 391 | 90 |

### The one table: the 13 PRE+X-selected representatives (Sunday composite + the book at 3 lots), recent-first, k$ (weekly-cumulative maxDD; worst-20 only where >= 20 losing weeks)

| group | cell (engine bracket bar variant) | session | maxDD before>after: L3M · L6M · HOLD · PRE · X' | worst-20 before>after: PRE · X' · ALL | SD / Calmar L6M before>after | mean delta k$/wk (MDE), * = beyond MDE | EQUAL-RISK mean delta L6M · PRE (c) | placebo rank (200 same-volume random-time draws): L6M cut / ALL worst-20 / PRE cut | RISK-KEEP | beats placebo | PRE and X agree | STRICT/TOL/NOW | family-wise p |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S1 | MV native lb/1m_n2 D | pre | 21>22 · 23>34 · 97>97 · 241>234 · 121>117 | -875>-858 · -420>-397 · -1098>-1079 | 42.7>43.2 / 1.80>1.18 | L3M +0.4 (3.9) · L6M -0.8 (3.4) · HOLD -0.8 (3.0) · PRE -0.0 (1.6) · X' +1.1 (1.4) | -0.1 · +0.4 (1.018) | 0.00 / 0.94 / 0.77 | no | no | yes | n/n/n (TOL-B n / TOL-nc n) | 0.97 |
| S1 | MV native lb/1m_n3 D | pre | 21>25 · 23>30 · 97>101 · 241>223 · 121>114 | -875>-858 · -420>-407 · -1098>-1087 | 42.7>44.4 / 1.80>1.33 | L3M +0.4 (3.5) · L6M -0.9 (2.5) · HOLD -0.8 (2.3) · PRE +0.6 (1.7) · X' +0.6 (1.5) | -0.5 · +0.8 (1.010) | 0.10 / 0.84 / 0.94 | no | no | yes | n/n/n (TOL-B n / TOL-nc n) | 0.89 |
| S1 | MV native lb/1m_n4 D | pre | 21>29 · 23>29 · 97>94 · 241>223 · 121>110 | -875>-854 · -420>-392 · -1098>-1078 | 42.7>44.2 / 1.80>1.38 | L3M -1.3 (3.6) · L6M -1.6 (2.3) · HOLD -1.4 (2.1) · PRE +0.3 (1.6) · X' +1.4 (1.7) | -0.8 · +0.7 (1.018) | 0.15 / 0.96 / 0.96 | no | no | yes | n/n/n (TOL-B n / TOL-nc n) | 0.79 |
| S1 | ST native lb/1m_n4 D | pre | 21>25 · 23>27 · 97>101 · 241>238 · 121>100 | -875>-874 · -420>-417 · -1098>-1107 | 42.7>43.7 / 1.80>1.53 | L3M +0.0 (2.6) · L6M -0.4 (2.2) · HOLD -0.3 (2.0) · PRE +0.0 (1.5) · X' +0.2 (1.8) | -0.7 · -0.2 (0.992) | 0.36 / 0.53 / 0.69 | no | no | yes | n/n/n (TOL-B n / TOL-nc n) | 0.99 |
| S1 | WT native lb/15m_n4 D | nyam | 21>21 · 23>24 · 97>101 · 241>240 · 121>119 | -875>-874 · -420>-417 · -1098>-1098 | 42.7>43.4 / 1.80>1.69 | L3M -0.4 (2.4) · L6M -0.6 (1.6) · HOLD -0.8 (1.6) · PRE +0.0 (1.0) · X' -0.3 (0.8) | -0.6 · +0.0 (1.000) | 0.48 / 0.68 / 0.69 | no | no | yes | n/n/n (TOL-B n / TOL-nc n) | 1.00 |
| S2 | MV b45 lb/1m_n4 D | pre | 21>30 · 23>30 · 97>97 · 241>222 · 121>112 | -875>-844 · -420>-405 · -1098>-1070 | 42.7>42.9 / 1.80>1.34 | L3M -0.6 (3.2) · L6M -0.9 (2.5) · HOLD -0.7 (2.2) · PRE +0.0 (1.3) · X' +0.7 (1.6) | +0.2 · +0.6 (1.026) | 0.04 / 1.00 / 0.99 | no | no | yes | n/n/n (TOL-B n / TOL-nc n) | 0.57 |
| S2 | MV b90 vol/10000 D | nypm | 21>18 · 23>18 · 97>100 · 241>241 · 121>112 | -875>-875 · -420>-402 · -1098>-1126 | 42.7>43.7 / 1.80>2.21 | L3M -1.1 (6.8) · L6M -1.1 (4.2) · HOLD -1.0 (3.7) · PRE -1.1 (3.2) · X' +0.8 (2.3) | -2.1 · -1.6 (0.975) | 0.96 / 0.45 / 0.48 | YES | no | yes | n/n/n (TOL-B n / TOL-nc n) | 0.93 |
| S2 | WT b75 kagi/4 D | nypm | 21>16 · 23>32 · 97>129 · 241>224 · 121>111 | -875>-871 · -420>-400 · -1098>-1110 | 42.7>42.3 / 1.80>1.19 | L3M -6.2 (9.1) · L6M -3.1 (5.8) · HOLD -3.6 (5.3) · PRE -0.2 (3.5) · X' +0.5 (2.9) | -3.5 · -0.4 (0.989) | 0.26 / 0.80 / 0.87 | no | no | yes | n/n/n (TOL-B n / TOL-nc n) | 0.57 |
| S2 | WT b75 vrb/s10 D | nypm | 21>23 · 23>23 · 97>84 · 241>230 · 121>109 | -875>-837 · -420>-402 · -1098>-1062 | 42.7>41.7 / 1.80>1.72 | L3M -1.3 (8.6) · L6M -1.2 (5.5) · HOLD -0.7 (4.9) · PRE -1.3 (3.8) · X' +0.1 (2.7) | +0.2 · -0.6 (1.034) | 0.73 / 0.99 / 0.80 | no | no | yes | n/n/n (TOL-B n / TOL-nc n) | 0.73 |
| S1b | PE native hull/3m G | pre | 21>25 · 23>27 · 97>97 · 241>238 · 121>116 | -875>-867 · -420>-398 · -1098>-1092 | 42.7>44.4 / 1.80>1.61 | L3M +2.8 (3.1) · L6M +1.5 (1.9) · HOLD +1.4 (1.8) · PRE +0.2 (1.3) · X' +0.6 (1.4) | +1.8 · +0.3 (1.006) | 0.41 / 0.82 / 0.68 | no | no | yes | Y/Y/Y (TOL-B Y / TOL-nc Y) | 1.00 |
| S1b | SM native ha/45s G | nyam | 21>21 · 23>23 · 97>85 · 241>233 · 121>109 | -875>-861 · -420>-410 · -1098>-1076 | 42.7>43.6 / 1.80>1.74 | L3M -1.3 (6.0) · L6M -0.7 (3.9) · HOLD -0.0 (3.7) · PRE +0.8 (1.6) · X' +1.1 (2.0) | +0.2 · +1.3 (1.021) | 0.77 / 0.97 / 0.75 | no | no | yes | n/n/n (TOL-B n / TOL-nc n) | 1.00 |
| S1b | SM native linreg/1m D | pre | 21>18 · 23>23 · 97>94 · 241>227 · 121>110 | -875>-842 · -420>-407 · -1098>-1058 | 42.7>41.4 / 1.80>1.74 | L3M -0.5 (3.9) · L6M -0.6 (2.6) · HOLD -0.4 (2.3) · PRE -0.1 (1.6) · X' +0.5 (1.7) | +0.9 · +0.7 (1.038) | 0.62 / 1.00 / 0.92 | no | no | yes | n/n/n (TOL-B n / TOL-nc n) | 1.00 |
| S1b | SM native linreg/5m D | london | 21>23 · 23>31 · 97>95 · 241>240 · 121>90 | -875>-844 · -420>-414 · -1098>-1107 | 42.7>45.1 / 1.80>1.40 | L3M +2.9 (5.3) · L6M +1.7 (3.1) · HOLD +1.4 (2.8) · PRE -0.3 (2.2) · X' +0.9 (2.4) | +1.3 · -0.5 (0.992) | 0.18 / 0.73 / 0.59 | no | no | yes | n/n/Y (TOL-B Y / TOL-nc Y) | 1.00 |

### The same representatives against the AS-IS stack (not the selection baseline), 3 lots

| cell | session | maxDD before>after k$: L3M · L6M · HOLD · PRE · X' | worst-20 PRE · X' · ALL | mean delta k$/wk (MDE) | RISK-KEEP | PRE and X agree | STRICT/TOL/NOW |
|---|---|---|---|---|---|---|---|
| S1 MV native lb/1m_n2 D | pre | 88>88 · 88>88 · 144>145 · 162>158 · 317>298 | -811>-816 · -572>-531 · -1161>-1164 | L3M +0.4 (3.9) · L6M -0.8 (3.4) · HOLD -0.8 (3.0) · PRE -0.0 (1.6) · X' +1.1 (1.4) | no | yes | n/n/n (TOL-B n / TOL-nc n) |
| S1 MV native lb/1m_n3 D | pre | 88>92 · 88>92 · 144>148 · 162>151 · 317>299 | -811>-804 · -572>-553 · -1161>-1150 | L3M +0.4 (3.5) · L6M -0.9 (2.5) · HOLD -0.8 (2.3) · PRE +0.6 (1.7) · X' +0.6 (1.5) | no | yes | n/n/n (TOL-B n / TOL-nc n) |
| S1 MV native lb/1m_n4 D | pre | 88>95 · 88>95 · 144>141 · 162>148 · 317>284 | -811>-814 · -572>-551 · -1161>-1169 | L3M -1.3 (3.6) · L6M -1.6 (2.3) · HOLD -1.4 (2.1) · PRE +0.3 (1.6) · X' +1.4 (1.7) | no | yes | n/n/n (TOL-B n / TOL-nc n) |
| S1 ST native lb/1m_n4 D | pre | 88>92 · 88>92 · 144>148 · 162>159 · 317>319 | -811>-803 · -572>-566 · -1161>-1171 | L3M +0.0 (2.6) · L6M -0.4 (2.2) · HOLD -0.3 (2.0) · PRE +0.0 (1.5) · X' +0.2 (1.8) | no | no | n/n/n (TOL-B n / TOL-nc n) |
| S1 WT native lb/15m_n4 D | nyam | 88>87 · 88>87 · 144>148 · 162>159 · 317>331 | -811>-818 · -572>-584 · -1161>-1186 | L3M -0.4 (2.4) · L6M -0.6 (1.6) · HOLD -0.8 (1.6) · PRE +0.0 (1.0) · X' -0.3 (0.8) | no | no | n/n/n (TOL-B n / TOL-nc n) |
| S2 MV b45 lb/1m_n4 D | pre | 88>97 · 88>97 · 144>145 · 162>141 · 317>302 | -811>-800 · -572>-561 · -1161>-1169 | L3M -0.6 (3.2) · L6M -0.9 (2.5) · HOLD -0.7 (2.2) · PRE +0.0 (1.3) · X' +0.7 (1.6) | no | yes | n/n/n (TOL-B n / TOL-nc n) |
| S2 MV b90 vol/10000 D | nypm | 88>85 · 88>85 · 144>147 · 162>177 · 317>285 | -811>-810 · -572>-566 · -1161>-1160 | L3M -1.1 (6.8) · L6M -1.1 (4.2) · HOLD -1.0 (3.7) · PRE -1.1 (3.2) · X' +0.8 (2.3) | no | no | n/n/n (TOL-B n / TOL-nc n) |
| S2 WT b75 kagi/4 D | nypm | 88>82 · 88>82 · 144>176 · 162>148 · 317>337 | -811>-778 · -572>-584 · -1161>-1141 | L3M -6.2 (9.1) · L6M -3.1 (5.8) · HOLD -3.6 (5.3) · PRE -0.2 (3.5) · X' +0.5 (2.9) | no | no | n/n/n (TOL-B n / TOL-nc n) |
| S2 WT b75 vrb/s10 D | nypm | 88>65 · 88>65 · 144>131 · 162>162 · 317>328 | -811>-878 · -572>-592 · -1161>-1146 | L3M -1.3 (8.6) · L6M -1.2 (5.5) · HOLD -0.7 (4.9) · PRE -1.3 (3.8) · X' +0.1 (2.7) | YES | no | n/n/n (TOL-B n / TOL-nc n) |
| S1b PE native hull/3m G | pre | 88>92 · 88>92 · 144>145 · 162>156 · 317>311 | -811>-803 · -572>-565 · -1161>-1154 | L3M +2.8 (3.1) · L6M +1.5 (1.9) · HOLD +1.4 (1.8) · PRE +0.2 (1.3) · X' +0.6 (1.4) | no | yes | Y/Y/Y (TOL-B Y / TOL-nc Y) |
| S1b SM native ha/45s G | nyam | 88>78 · 88>78 · 144>132 · 162>161 · 317>301 | -811>-817 · -572>-555 · -1161>-1168 | L3M -1.3 (6.0) · L6M -0.7 (3.9) · HOLD -0.0 (3.7) · PRE +0.8 (1.6) · X' +1.1 (2.0) | no | yes | n/n/n (TOL-B n / TOL-nc n) |
| S1b SM native linreg/1m D | pre | 88>85 · 88>85 · 144>141 · 162>144 · 317>305 | -811>-780 · -572>-570 · -1161>-1126 | L3M -0.5 (3.9) · L6M -0.6 (2.6) · HOLD -0.4 (2.3) · PRE -0.1 (1.6) · X' +0.5 (1.7) | no | yes | n/n/n (TOL-B n / TOL-nc n) |
| S1b SM native linreg/5m D | london | 88>89 · 88>89 · 144>143 · 162>154 · 317>285 | -811>-793 · -572>-573 · -1161>-1178 | L3M +2.9 (5.3) · L6M +1.7 (3.1) · HOLD +1.4 (2.8) · PRE -0.3 (2.2) · X' +0.9 (2.4) | no | yes | n/n/Y (TOL-B Y / TOL-nc Y) |

### The representatives as books on their own, and against the native 1-min engine (PAIRFIX, per contract M pts)

| cell | session | per contract M L3M · L6M · HOLD · PRE · X' (MDE L6M) | own book $k/wk at 1 lot L6M (MDE) | trades PRE / X' | D (day-summed, vs 1-min) HOLD [CI] | TW (trade-weighted) HOLD [CI] | D PRE | TW PRE |
|---|---|---|---|---|---|---|---|---|
| S1 MV native lb/1m_n2 D | pre | +4.14 · -7.03 · -7.30 · -0.13 · +13.21 (22.9) | -0.28 (1.13) | 169 / 61 | -1.5 [-7.1,+3.7] | -4.44 [-16.65,+9.74] | +1.9 | +3.48 |
| S1 MV native lb/1m_n3 D | pre | +3.17 · -8.82 · -8.37 · +4.73 · +9.10 (20.7) | -0.31 (0.82) | 153 / 51 | -1.5 [-6.4,+3.5] | -5.51 [-18.51,+9.17] | +3.9 | +8.34 |
| S1 MV native lb/1m_n4 D | pre | -11.85 · -14.54 · -14.09 · +2.55 · +20.59 (23.3) | -0.52 (0.78) | 133 / 51 | -3.3 [-9.0,+2.6] | -11.23 [-26.21,+5.05] | +2.8 | +6.16 |
| S1 ST native lb/1m_n4 D | pre | +0.21 · -4.28 · -4.21 · +0.12 · +2.46 (24.9) | -0.13 (0.73) | 108 / 48 | +3.0 [-2.4,+8.5] | +4.84 [-10.03,+20.53] | -0.5 | -0.87 |
| S1 WT native lb/15m_n4 D | nyam | -3.57 · -6.66 · -7.73 · +0.30 · -2.79 (16.0) | -0.20 (0.52) | 112 / 74 | -4.1 [-16.0,+8.8] | -8.19 [-19.04,+3.60] | +2.3 | +1.08 |
| S2 MV b45 lb/1m_n4 D | pre | -4.11 · -6.00 · -5.27 · +0.11 · +7.62 (14.1) | -0.30 (0.82) | 185 / 71 | -1.4 [-7.2,+5.1] | -3.67 [-14.78,+7.32] | +4.2 | +6.02 |
| S2 MV b90 vol/10000 D | nypm | -2.90 · -3.44 · -3.40 · -3.78 · +4.81 (16.3) | -0.36 (1.39) | 351 / 117 | +4.2 [-6.7,+14.2] | +4.57 [-5.54,+15.32] | -6.9 | -6.97 |
| S2 WT b75 kagi/4 D | nypm | -8.10 · -5.31 · -6.51 · -0.25 · +2.02 (10.8) | -1.02 (1.92) | 871 / 188 | -9.3 [-23.3,+5.0] | -3.88 [-14.88,+7.11] | +3.2 | +2.99 |
| S2 WT b75 vrb/s10 D | nypm | -1.99 · -2.10 · -1.27 · -2.22 · +0.58 (11.0) | -0.38 (1.82) | 725 / 169 | +0.5 [-14.1,+14.3] | +1.35 [-9.84,+12.42] | -0.5 | +1.02 |
| S1b PE native hull/3m G | pre | +36.04 · +21.18 · +20.81 · +2.69 · +10.58 (24.3) | +0.51 (0.64) | 102 / 41 | +7.2 [+0.6,+13.9] | +26.20 [+7.36,+44.54] | +2.1 | +5.46 |
| S1b SM native ha/45s G | nyam | -7.40 · -3.61 · -0.06 · +4.72 · +6.69 (18.1) | -0.22 (1.30) | 215 / 122 | -3.7 [-11.8,+4.5] | -5.89 [-18.50,+6.19] | +1.5 | +2.63 |
| S1b SM native linreg/1m D | pre | -5.64 · -6.93 · -4.10 · -1.20 · +6.79 (24.8) | -0.21 (0.87) | 151 / 58 | -0.5 [-6.9,+5.9] | +2.20 [-34.96,+37.07] | +0.6 | +5.77 |
| S1b SM native linreg/5m D | london | +10.20 · +6.77 · +5.72 · -1.22 · +6.64 (14.7) | +0.56 (1.04) | 280 / 96 | +6.0 [-2.9,+15.2] | +8.00 [-4.92,+19.90] | -0.4 | -0.43 |

### Lots ladder 1-5 on the Sunday composite (representatives): maxDD L6M / PRE / X' (k$ before>after), worst-20 ALL (k$), mean delta ALL k$/wk

| cell | session | lots | maxDD L6M | maxDD PRE | maxDD X' | worst-20 ALL | mean delta ALL | SD ALL before>after |
|---|---|---|---|---|---|---|---|---|
| S1 MV native lb/1m_n4 D | pre | 1 | 23>24 | 241>235 | 121>117 | -1098>-1088 | +0.1 | 50.3>50.1 |
| S1 MV native lb/1m_n4 D | pre | 2 | 23>26 | 241>229 | 121>114 | -1098>-1082 | +0.2 | 50.3>50.0 |
| S1 MV native lb/1m_n4 D | pre | 3 | 23>29 | 241>223 | 121>110 | -1098>-1078 | +0.3 | 50.3>49.9 |
| S1 MV native lb/1m_n4 D | pre | 4 | 23>31 | 241>217 | 121>107 | -1098>-1077 | +0.4 | 50.3>49.9 |
| S1 MV native lb/1m_n4 D | pre | 5 | 23>34 | 241>211 | 121>103 | -1098>-1080 | +0.4 | 50.3>49.9 |
| S1 MV native lb/1m_n3 D | pre | 1 | 23>25 | 241>235 | 121>118 | -1098>-1091 | +0.1 | 50.3>50.2 |
| S1 MV native lb/1m_n3 D | pre | 2 | 23>28 | 241>229 | 121>116 | -1098>-1087 | +0.2 | 50.3>50.2 |
| S1 MV native lb/1m_n3 D | pre | 3 | 23>30 | 241>223 | 121>114 | -1098>-1087 | +0.3 | 50.3>50.3 |
| S1 MV native lb/1m_n3 D | pre | 4 | 23>33 | 241>217 | 121>112 | -1098>-1090 | +0.4 | 50.3>50.3 |
| S1 MV native lb/1m_n3 D | pre | 5 | 23>35 | 241>210 | 121>109 | -1098>-1094 | +0.5 | 50.3>50.5 |
| S1 MV native lb/1m_n2 D | pre | 1 | 23>27 | 241>239 | 121>119 | -1098>-1086 | +0.0 | 50.3>50.2 |
| S1 MV native lb/1m_n2 D | pre | 2 | 23>30 | 241>236 | 121>118 | -1098>-1080 | +0.1 | 50.3>50.0 |
| S1 MV native lb/1m_n2 D | pre | 3 | 23>34 | 241>234 | 121>117 | -1098>-1079 | +0.1 | 50.3>50.0 |
| S1 MV native lb/1m_n2 D | pre | 4 | 23>38 | 241>231 | 121>116 | -1098>-1080 | +0.2 | 50.3>50.0 |
| S1 MV native lb/1m_n2 D | pre | 5 | 23>42 | 241>229 | 121>114 | -1098>-1082 | +0.2 | 50.3>50.1 |
| S1 ST native lb/1m_n4 D | pre | 1 | 23>24 | 241>240 | 121>114 | -1098>-1099 | -0.0 | 50.3>50.4 |
| S1 ST native lb/1m_n4 D | pre | 2 | 23>25 | 241>239 | 121>107 | -1098>-1102 | -0.0 | 50.3>50.5 |
| S1 ST native lb/1m_n4 D | pre | 3 | 23>27 | 241>238 | 121>100 | -1098>-1107 | -0.0 | 50.3>50.7 |
| S1 ST native lb/1m_n4 D | pre | 4 | 23>28 | 241>237 | 121>93 | -1098>-1114 | -0.0 | 50.3>50.9 |
| S1 ST native lb/1m_n4 D | pre | 5 | 23>29 | 241>237 | 121>86 | -1098>-1120 | -0.0 | 50.3>51.1 |
| S1 WT native lb/15m_n4 D | nyam | 1 | 23>23 | 241>241 | 121>120 | -1098>-1098 | -0.1 | 50.3>50.3 |
| S1 WT native lb/15m_n4 D | nyam | 2 | 23>24 | 241>240 | 121>119 | -1098>-1097 | -0.2 | 50.3>50.3 |
| S1 WT native lb/15m_n4 D | nyam | 3 | 23>24 | 241>240 | 121>119 | -1098>-1098 | -0.2 | 50.3>50.3 |
| S1 WT native lb/15m_n4 D | nyam | 4 | 23>24 | 241>239 | 121>118 | -1098>-1099 | -0.3 | 50.3>50.3 |
| S1 WT native lb/15m_n4 D | nyam | 5 | 23>25 | 241>239 | 121>118 | -1098>-1102 | -0.4 | 50.3>50.4 |
| S2 MV b45 lb/1m_n4 D | pre | 1 | 23>25 | 241>235 | 121>118 | -1098>-1087 | +0.0 | 50.3>50.0 |
| S2 MV b45 lb/1m_n4 D | pre | 2 | 23>27 | 241>228 | 121>115 | -1098>-1078 | +0.0 | 50.3>49.8 |
| S2 MV b45 lb/1m_n4 D | pre | 3 | 23>30 | 241>222 | 121>112 | -1098>-1070 | +0.1 | 50.3>49.5 |
| S2 MV b45 lb/1m_n4 D | pre | 4 | 23>33 | 241>215 | 121>109 | -1098>-1066 | +0.1 | 50.3>49.3 |
| S2 MV b45 lb/1m_n4 D | pre | 5 | 23>36 | 241>208 | 121>106 | -1098>-1064 | +0.1 | 50.3>49.2 |
| S2 WT b75 kagi/4 D | nypm | 1 | 23>26 | 241>235 | 121>117 | -1098>-1100 | -0.2 | 50.3>49.9 |
| S2 WT b75 kagi/4 D | nypm | 2 | 23>29 | 241>229 | 121>114 | -1098>-1104 | -0.5 | 50.3>49.7 |
| S2 WT b75 kagi/4 D | nypm | 3 | 23>32 | 241>224 | 121>111 | -1098>-1110 | -0.7 | 50.3>49.8 |
| S2 WT b75 kagi/4 D | nypm | 4 | 23>35 | 241>225 | 121>107 | -1098>-1121 | -0.9 | 50.3>50.0 |
| S2 WT b75 kagi/4 D | nypm | 5 | 23>38 | 241>225 | 121>104 | -1098>-1141 | -1.2 | 50.3>50.5 |
| S2 WT b75 vrb/s10 D | nypm | 1 | 23>20 | 241>238 | 121>117 | -1098>-1079 | -0.2 | 50.3>49.5 |
| S2 WT b75 vrb/s10 D | nypm | 2 | 23>17 | 241>234 | 121>113 | -1098>-1067 | -0.5 | 50.3>48.9 |
| S2 WT b75 vrb/s10 D | nypm | 3 | 23>23 | 241>230 | 121>109 | -1098>-1062 | -0.7 | 50.3>48.5 |
| S2 WT b75 vrb/s10 D | nypm | 4 | 23>32 | 241>229 | 121>105 | -1098>-1076 | -1.0 | 50.3>48.4 |
| S2 WT b75 vrb/s10 D | nypm | 5 | 23>40 | 241>229 | 121>101 | -1098>-1098 | -1.2 | 50.3>48.5 |
| S2 MV b90 vol/10000 D | nypm | 1 | 23>21 | 241>241 | 121>118 | -1098>-1106 | -0.2 | 50.3>50.0 |
| S2 MV b90 vol/10000 D | nypm | 2 | 23>19 | 241>241 | 121>115 | -1098>-1115 | -0.3 | 50.3>49.7 |
| S2 MV b90 vol/10000 D | nypm | 3 | 23>18 | 241>241 | 121>112 | -1098>-1126 | -0.5 | 50.3>49.7 |
| S2 MV b90 vol/10000 D | nypm | 4 | 23>17 | 241>242 | 121>109 | -1098>-1137 | -0.7 | 50.3>49.8 |
| S2 MV b90 vol/10000 D | nypm | 5 | 23>16 | 241>244 | 121>106 | -1098>-1155 | -0.9 | 50.3>50.0 |
| S1b SM native linreg/1m D | pre | 1 | 23>23 | 241>235 | 121>117 | -1098>-1084 | +0.0 | 50.3>49.9 |
| S1b SM native linreg/1m D | pre | 2 | 23>23 | 241>229 | 121>114 | -1098>-1071 | +0.0 | 50.3>49.6 |
| S1b SM native linreg/1m D | pre | 3 | 23>23 | 241>227 | 121>110 | -1098>-1058 | +0.0 | 50.3>49.3 |
| S1b SM native linreg/1m D | pre | 4 | 23>23 | 241>225 | 121>107 | -1098>-1048 | +0.0 | 50.3>49.1 |
| S1b SM native linreg/1m D | pre | 5 | 23>23 | 241>223 | 121>103 | -1098>-1038 | +0.0 | 50.3>48.9 |
| S1b SM native ha/45s G | nyam | 1 | 23>23 | 241>238 | 121>116 | -1098>-1087 | +0.2 | 50.3>50.5 |
| S1b SM native ha/45s G | nyam | 2 | 23>23 | 241>236 | 121>112 | -1098>-1078 | +0.5 | 50.3>50.7 |
| S1b SM native ha/45s G | nyam | 3 | 23>23 | 241>233 | 121>109 | -1098>-1076 | +0.7 | 50.3>51.0 |
| S1b SM native ha/45s G | nyam | 4 | 23>25 | 241>230 | 121>108 | -1098>-1078 | +1.0 | 50.3>51.4 |
| S1b SM native ha/45s G | nyam | 5 | 23>28 | 241>228 | 121>107 | -1098>-1081 | +1.2 | 50.3>51.8 |
| S1b PE native hull/3m G | pre | 1 | 23>24 | 241>240 | 121>119 | -1098>-1094 | +0.2 | 50.3>50.3 |
| S1b PE native hull/3m G | pre | 2 | 23>25 | 241>239 | 121>118 | -1098>-1091 | +0.4 | 50.3>50.4 |
| S1b PE native hull/3m G | pre | 3 | 23>27 | 241>238 | 121>116 | -1098>-1092 | +0.6 | 50.3>50.5 |
| S1b PE native hull/3m G | pre | 4 | 23>28 | 241>237 | 121>115 | -1098>-1096 | +0.8 | 50.3>50.6 |
| S1b PE native hull/3m G | pre | 5 | 23>29 | 241>236 | 121>114 | -1098>-1103 | +1.0 | 50.3>50.8 |
| S1b SM native linreg/5m D | london | 1 | 23>25 | 241>240 | 121>110 | -1098>-1096 | +0.1 | 50.3>50.4 |
| S1b SM native linreg/5m D | london | 2 | 23>28 | 241>238 | 121>100 | -1098>-1100 | +0.3 | 50.3>50.5 |
| S1b SM native linreg/5m D | london | 3 | 23>31 | 241>240 | 121>90 | -1098>-1107 | +0.4 | 50.3>50.8 |
| S1b SM native linreg/5m D | london | 4 | 23>33 | 241>242 | 121>82 | -1098>-1118 | +0.6 | 50.3>51.1 |
| S1b SM native linreg/5m D | london | 5 | 23>36 | 241>245 | 121>75 | -1098>-1129 | +0.7 | 50.3>51.5 |


### RISK-KEEP flagged cells (Sunday composite, 3 lots, maxDD cut >= 20% in L6M with the mean inside its MDE; ALL 74 shown by group, top 20 by L6M cut listed) - a view of the recent look, NOT a selection

74-cell check: HOLD maxDD cut >= 20% in 0 of 74; HOLD cut > 0 in 8; PRE and X' both shallower in 6; placebo run for 56 (DN is an orders engine, not run), beats the placebo on the L6M cut 50, on L6M cut AND ALL worst-20 0; same flags against the as-is stack: 66 cells, 5 with PRE and X agree.

| group | cell | session | maxDD L3M · L6M · HOLD · PRE · X' cut (+ = shallower) | composite maxDD L6M before>after k$ | mean delta L6M k$/wk (MDE) | per contract M L6M | placebo rank L6M cut / ALL worst-20 | PRE and X agree | STRICT/TOL/NOW |
|---|---|---|---|---|---|---|---|---|---|
| S2 | MV b90 vol/10000 D | nyam | +51% · +54% · -20% · -10% · +17% | 23>11 | +7.4 (6.5) | +12.7 | 1.00 / 0.01 | no | n/n/Y (TOL-B n / TOL-nc n) |
| S2 | ST b90 drb/s10 D | nyam | +51% · +54% · -22% · -11% · +11% | 23>11 | +6.1 (8.9) | +7.4 | 0.99 / 0.68 | no | Y/n/Y (TOL-B n / TOL-nc n) |
| S2 | ST b90 vrb/s30 D | nyam | +62% · +51% · -35% · +5% · +6% | 23>11 | +5.6 (7.7) | +6.9 | 0.99 / 0.20 | yes | Y/n/Y (TOL-B n / TOL-nc n) |
| S1b | DN native hull/5m G | nypm | +30% · +48% · -15% · -7% · -26% | 23>12 | +0.6 (3.7) | +2.8 | n/a / n/a | no | n/n/n (TOL-B n / TOL-nc n) |
| S1b | PB native hull/1m G | nyam | +42% · +46% · -26% · -10% · +4% | 23>12 | -0.2 (3.6) | -0.5 | 1.00 / 0.55 | no | n/n/n (TOL-B n / TOL-nc n) |
| S1b | DN native linreg/5m G | nypm | +45% · +45% · -16% · -11% · -25% | 23>13 | +1.8 (3.6) | +7.8 | n/a / n/a | no | n/n/n (TOL-B n / TOL-nc n) |
| S1b | DN native linreg/5m D | nypm | +45% · +44% · -13% · -18% · -13% | 23>13 | +0.9 (5.7) | +2.0 | n/a / n/a | no | n/n/n (TOL-B n / TOL-nc n) |
| S1 | PB7 native renko/4 G | london | +39% · +43% · -27% · -5% · +2% | 23>13 | +1.5 (4.0) | +3.2 | 1.00 / 0.00 | no | n/n/Y (TOL-B n / TOL-nc n) |
| S1 | PB7 native unirenko/4 G | london | +39% · +43% · -27% · -5% · +2% | 23>13 | +1.5 (4.0) | +3.2 | 1.00 / 0.00 | no | n/n/Y (TOL-B n / TOL-nc n) |
| S1b | DN native hull/5m D | nypm | +38% · +42% · -20% · -19% · -10% | 23>13 | +2.2 (5.9) | +4.4 | n/a / n/a | no | n/n/Y (TOL-B n / TOL-nc n) |
| S1b | SM native hull/1m D | asia | +60% · +38% · -19% · -6% · +16% | 23>14 | +0.5 (4.5) | +0.9 | 0.99 / 0.59 | no | n/n/n (TOL-B n / TOL-nc n) |
| S1 | DN native lb/1m_n2 G | nypm | +30% · +35% · -8% · -6% · -25% | 23>15 | +2.4 (2.8) | +10.0 | n/a / n/a | no | n/n/Y (TOL-B Y / TOL-nc Y) |
| S1b | MV native hull/3m D | nypm | +11% · +34% · -14% · -14% · -13% | 23>15 | -0.3 (3.6) | -0.9 | 0.99 / 0.04 | no | n/n/n (TOL-B n / TOL-nc n) |
| S1b | KB native ha/45s D | asia | -10% · +33% · -11% · -31% · -34% | 23>15 | +0.2 (7.1) | +0.3 | 0.99 / 0.00 | no | n/n/n (TOL-B n / TOL-nc n) |
| S1b | DN native hull/15m G | nypm | +47% · +33% · -7% · -13% · -12% | 23>15 | +2.2 (3.2) | +7.6 | n/a / n/a | no | n/n/Y (TOL-B n / TOL-nc n) |
| S1b | DN native hull/15m D | nypm | +47% · +33% · -7% · -13% · -12% | 23>15 | +2.2 (3.2) | +7.6 | n/a / n/a | no | n/n/Y (TOL-B n / TOL-nc n) |
| S1b | KB native hull/15m D | london | +28% · +33% · -20% · -2% · +11% | 23>15 | -1.1 (3.5) | -4.1 | 1.00 / 0.05 | no | n/n/n (TOL-B n / TOL-nc n) |
| S1b | KB native hull/15m G | london | +28% · +33% · -20% · -2% · +11% | 23>15 | -1.1 (3.5) | -4.1 | 1.00 / 0.05 | no | n/n/n (TOL-B n / TOL-nc n) |
| S1b | DN native hull/3m G | nypm | +30% · +32% · -15% · -13% · -30% | 23>16 | +0.9 (2.4) | +3.8 | n/a / n/a | no | n/n/n (TOL-B n / TOL-nc n) |
| S1b | DN native hull/1m G | nypm | +12% · +31% · -12% · -3% · -28% | 23>16 | +2.1 (3.4) | +8.6 | n/a / n/a | no | n/n/Y (TOL-B n / TOL-nc n) |

### Cells that pass the literal TOLERANT gate (per contract AND stack; the mean-lens survivors) read on the risk picture (Sunday composite, 3 lots; ALL 42)

| group | cell | session | per contract M L3M · L6M · HOLD · PRE · X' | mean delta k$/wk L6M (MDE) | maxDD cut L3M · L6M · HOLD · PRE · X' | worst-20 ALL before>after k$ | placebo rank L6M cut / ALL worst-20 | RISK-KEEP | PRE and X agree | TOL-B / TOL-nc |
|---|---|---|---|---|---|---|---|---|---|---|
| S1b | PB7 native linreg/3m G | pre | +55.6 · +16.6 · +16.6 · +15.0 · -13.4 | +0.1 (0.6) | +0% · +0% · +0% · -0% · -1% | -1098>-1097 | n/a / n/a | no | no | Y / Y |
| S1b | PB7 native linreg/5m G | asia | +55.5 · +8.8 · +10.1 · +12.7 · -4.3 | +0.3 (1.4) | +0% · -1% · -0% · +1% · -6% | -1098>-1096 | 0.40 / 0.70 | no | no | Y / Y |
| S1b | PE native hull/3m G | pre | +36.0 · +21.2 · +20.8 · +2.7 · +10.6 | +1.5 (1.9) | -17% · -16% · -0% · +1% · +3% | -1098>-1092 | 0.41 / 0.82 | no | yes | Y / Y |
| S1b | ST native ha/1h D | nyam | +36.0 · +24.0 · +19.1 · +1.3 · -3.1 | +0.5 (1.0) | +0% · +0% · -0% · +1% · -6% | -1098>-1112 | 0.86 / 0.13 | no | no | Y / Y |
| S1 | DN native lb/15m_n2 D | pre | +19.6 · +21.5 · +12.9 · +0.6 · -3.7 | +1.1 (1.5) | -17% · -9% · -8% · +3% · +3% | -1098>-1099 | n/a / n/a | no | yes | Y / Y |
| S1 | DN native lb/15m_n2 G | pre | +19.6 · +21.5 · +12.9 · +0.6 · -3.7 | +1.1 (1.5) | -17% · -9% · -8% · +3% · +3% | -1098>-1099 | n/a / n/a | no | yes | Y / Y |
| S1b | PB7 native hull/5m G | nypm | +18.5 · +17.0 · +17.0 · +1.6 · +4.8 | +0.3 (0.7) | -3% · +4% · +0% · +0% · +0% | -1098>-1098 | n/a / n/a | no | no | Y / Y |
| S1 | DN native lb/5m_n2 D | pre | +18.2 · +15.6 · +12.8 · +0.8 · -1.5 | +1.3 (2.5) | -2% · -18% · -0% · +3% · +9% | -1098>-1090 | n/a / n/a | no | yes | Y / Y |
| S1 | DN native lb/5m_n2 G | pre | +18.2 · +15.6 · +12.8 · +0.8 · -1.5 | +1.3 (2.5) | -2% · -18% · -0% · +3% · +9% | -1098>-1090 | n/a / n/a | no | yes | Y / Y |
| S1b | ST native linreg/15m D | nyam | +16.6 · +11.2 · +3.0 · +2.9 · +20.8 | +0.7 (1.9) | +0% · +0% · -14% · +4% · -7% | -1098>-1096 | 0.80 / 0.74 | no | no | Y / Y |
| S1b | PB7 native ha/10m G | asia | +16.6 · +7.5 · +12.5 · +8.6 · +6.3 | +0.3 (1.3) | +0% · -1% · +3% · -2% · -9% | -1098>-1098 | 0.39 / 0.72 | no | no | Y / Y |
| S1b | SM native hull/5m D | london | +14.7 · +3.5 · +3.8 · +1.1 · +10.7 | +0.8 (2.8) | +28% · -21% · +2% · -7% · +22% | -1098>-1114 | 0.31 / 0.66 | no | no | Y / Y |
| S2 | PB7 b90 delta/250 G | nypm | +14.7 · +5.4 · +1.8 · +3.1 · -0.9 | +0.6 (3.0) | +53% · -1% · -0% · -4% · +20% | -1098>-1129 | 0.67 / 0.28 | no | no | Y / Y |
| S1 | DN native lb/15m_n3 G | nypm | +13.8 · +10.3 · +11.5 · +7.1 · -4.5 | +0.7 (1.8) | +16% · +0% · +0% · +3% · -10% | -1098>-1112 | n/a / n/a | no | no | Y / Y |
| S1 | DN native lb/15m_n3 D | nypm | +13.8 · +10.3 · +11.5 · +7.1 · -4.5 | +0.7 (1.8) | +16% · +0% · +0% · +3% · -10% | -1098>-1112 | n/a / n/a | no | no | Y / Y |
| S1b | SM native ha/30m G | asia | +11.7 · +19.6 · +16.6 · +4.4 · +13.5 | +0.5 (1.1) | +0% · +0% · -4% · -2% · -3% | -1098>-1088 | 0.85 / 0.91 | no | no | Y / Y |
| S1b | SM native ha/30m D | asia | +11.7 · +19.6 · +16.6 · +4.4 · +13.5 | +0.5 (1.1) | +0% · +0% · -4% · -2% · -3% | -1098>-1088 | 0.85 / 0.91 | no | no | Y / Y |
| S1b | WT native ha/1h D | nyam | +10.4 · +9.1 · +8.3 · +9.2 · -5.3 | +0.3 (0.7) | +0% · -12% · -1% · +2% · -1% | -1098>-1106 | 0.15 / 0.18 | no | no | Y / Y |
| S1b | KB native ha/1h G | asia | +9.8 · +5.0 · +9.4 · +10.5 · +9.4 | +0.4 (1.6) | -2% · +5% · +7% · +1% · -6% | -1098>-1109 | 0.85 / 0.46 | no | no | Y / Y |
| S1b | KB native ha/1h D | asia | +9.8 · +5.0 · +9.4 · +10.5 · +9.4 | +0.4 (1.6) | -2% · +5% · +7% · +1% · -6% | -1098>-1109 | 0.85 / 0.46 | no | no | Y / Y |
| S1 | PB7 native lb/15m_n2 G | pre | +8.8 · +13.8 · +13.8 · +3.1 · -1.4 | +0.4 (1.0) | -17% · -9% · +0% · -0% · -0% | -1098>-1089 | 0.32 / 0.90 | no | no | Y / Y |
| S1b | WT native linreg/15m D | asia | +8.7 · +3.5 · +1.5 · +4.0 · +3.5 | +0.3 (1.7) | +16% · +8% · -5% · -2% · -1% | -1098>-1090 | 0.98 / 0.91 | no | no | Y / Y |
| S2 | MV b75 lb/5m_n2 D | nypm | +7.8 · +6.8 · +6.3 · +3.6 · -5.5 | +1.8 (3.4) | +50% · -1% · -5% · -2% · +5% | -1098>-1133 | 0.68 / 0.29 | no | no | Y / Y |
| S1b | SM native ha/45s G | asia | +7.7 · +8.8 · +8.1 · +4.7 · -0.4 | +1.0 (2.3) | -2% · -1% · +2% · +1% · -11% | -1098>-1090 | 0.61 / 0.87 | no | no | Y / Y |
| S1b | HM native linreg/1m D | asia | +7.6 · +7.9 · +6.7 · +1.7 · -0.4 | +4.3 (4.0) | -25% · -17% · -18% · -16% · -17% | -1098>-1174 | 0.56 / 0.07 | no | no | Y / Y |
| S1 | MV native lb/5m_n2 D | nypm | +6.5 · +6.6 · +5.7 · +2.5 · -4.3 | +2.1 (3.5) | +53% · -37% · -4% · +1% · -12% | -1098>-1168 | 0.10 / 0.04 | no | no | Y / Y |
| S1 | DN native lb/15m_n2 D | asia | +6.2 · +0.5 · -1.7 · +3.3 · -5.1 | +0.1 (3.1) | -3% · -3% · -16% · -4% · -7% | -1098>-1114 | n/a / n/a | no | no | Y / Y |
| S1 | DN native lb/15m_n2 G | asia | +6.2 · +0.5 · -1.7 · +3.3 · -5.1 | +0.1 (3.1) | -3% · -3% · -16% · -4% · -7% | -1098>-1114 | n/a / n/a | no | no | Y / Y |
| S1b | SM native hull/1m G | london | +4.6 · +0.0 · +0.7 · +1.8 · +4.5 | +0.0 (3.3) | -5% · -19% · -1% · +2% · +9% | -1098>-1134 | 0.32 / 0.26 | no | yes | Y / Y |
| S1b | PE native hull/1m G | pre | +4.4 · +0.4 · -1.9 · +0.6 · -3.4 | +0.1 (2.5) | +16% · -1% · -11% · +10% · +9% | -1098>-1075 | 0.67 / 0.97 | no | yes | Y / Y |
| S1b | DN native linreg/5m G | asia | +4.1 · +5.0 · +3.6 · +6.5 · +0.7 | +2.2 (5.3) | -38% · -37% · -18% · -2% · -31% | -1098>-1112 | n/a / n/a | no | no | Y / Y |
| S1 | DN native lb/5m_n2 D | nyam | +3.9 · +2.6 · +3.2 · +4.6 · +2.7 | +1.2 (4.6) | +28% · -14% · -2% · +3% · -6% | -1098>-1103 | n/a / n/a | no | no | Y / Y |
| S1 | DN native lb/5m_n2 G | nyam | +3.9 · +2.6 · +3.2 · +4.6 · +2.7 | +1.2 (4.6) | +28% · -14% · -2% · +3% · -6% | -1098>-1103 | n/a / n/a | no | no | Y / Y |
| S1b | HM native linreg/5m D | pre | +3.6 · +14.3 · +6.4 · +0.3 · -14.2 | +0.5 (1.3) | +0% · +0% · -4% · -0% · +0% | -1098>-1092 | 0.78 / 0.83 | no | no | Y / Y |
| S1b | DN native linreg/3m G | asia | +3.0 · +2.4 · +1.2 · +5.0 · +4.0 | +1.1 (5.7) | -55% · -67% · -22% · -2% · -13% | -1098>-1104 | n/a / n/a | no | no | Y / Y |
| S1b | DN native hull/3m G | asia | +2.6 · +3.3 · +2.3 · +6.5 · +3.4 | +1.5 (6.1) | -55% · -45% · -18% · -0% · -31% | -1098>-1083 | n/a / n/a | no | no | Y / Y |
| S2 | ST b75 pnf/b8_r2 D | asia | +1.9 · +4.4 · +3.2 · +3.5 · -3.6 | +2.7 (6.6) | -3% · -83% · -31% · -28% · -26% | -1098>-1173 | 0.03 / 0.27 | no | no | Y / Y |
| S1 | DN native lb/1m_n4 D | asia | +1.9 · +0.7 · -0.9 · +3.5 · +0.3 | +0.4 (5.1) | -7% · -6% · -32% · -10% · -17% | -1098>-1141 | n/a / n/a | no | no | Y / Y |
| S1b | SM native linreg/5m G | nyam | +0.9 · +0.9 · +4.4 · +4.9 · -0.4 | +0.2 (2.9) | +30% · -1% · +20% · +5% · -6% | -1098>-1101 | 0.80 / 0.78 | no | no | Y / Y |
| S1b | PB native ha/10m G | asia | +0.9 · +2.7 · -0.1 · +0.4 · +8.3 | +0.6 (2.9) | -19% · -11% · -9% · -6% · -3% | -1098>-1100 | 0.56 / 0.81 | no | no | Y / Y |
| S1b | PB7 native ha/10m G | nypm | +0.7 · +10.8 · +10.8 · +28.1 · +29.7 | +0.3 (0.8) | +0% · +3% · +0% · +0% · +3% | -1098>-1098 | n/a / n/a | no | no | Y / Y |
| S1b | WT native ha/10m D | nyam | +0.2 · +1.8 · +3.8 · +2.0 · -1.6 | +0.2 (1.8) | +16% · +3% · +12% · +8% · -4% | -1098>-1105 | 0.80 / 0.65 | no | no | Y / Y |

### HEDGE VALUE: the ten cells that improve the composite's ALL-window worst-20 the most at 3 lots (a view; the stack worst-20 before>after is in the same columns of every table)

| group | cell | session | worst-20 ALL before>after k$ | worst-20 PRE · X' before>after | maxDD ALL cut | mean delta ALL k$/wk | per contract M L6M · PRE |
|---|---|---|---|---|---|---|---|
| S1b | SM native linreg/1m D | london | -1098>-1032 | -875>-789 · -420>-413 | -10% | -1.2 | -9.0 · +0.0 |
| S1b | SM native hull/1m D | london | -1098>-1032 | -875>-788 · -420>-413 | -7% | -0.9 | -7.1 · -0.7 |
| S1b | SM native ha/45s D | london | -1098>-1043 | -875>-793 · -420>-418 | -11% | -1.1 | -11.9 · +0.1 |
| S1b | SM native linreg/1m D | pre | -1098>-1058 | -875>-842 · -420>-407 | +6% | +0.0 | -6.9 · -1.2 |
| S1b | SM native hull/1m D | pre | -1098>-1060 | -875>-853 · -420>-423 | +3% | -0.4 | -7.3 · -2.5 |
| S1 | PB7 native lb/1m_n3 G | pre | -1098>-1061 | -875>-847 · -420>-436 | +1% | +0.1 | -7.1 · +7.7 |
| S2 | WT b75 vrb/s10 D | nypm | -1098>-1062 | -875>-837 · -420>-402 | +4% | -0.7 | -2.1 · -2.2 |
| S1b | MV native hull/3m D | pre | -1098>-1062 | -875>-837 · -420>-406 | -0% | +0.1 | +5.5 · -2.1 |
| S2 | MV b45 lb/1m_n4 D | pre | -1098>-1070 | -875>-844 · -420>-405 | +8% | +0.1 | -6.0 · +0.1 |
| S2 | MV b45 lb/5m_n2 D | pre | -1098>-1072 | -875>-846 · -420>-421 | -1% | -0.2 | -11.2 · -1.2 |

Hedge value > 0 (ALL worst-20 improves when the book is added at 3 lots) in 148 of 1976 cells (7.5%); in 65 of them the ALL maxDD is also shallower. Positive-hedge cells with a per-contract L6M mean >= 0 and PRE mean >= 0: 28.


## Method notes, limits (stated, not hidden)

* **Scoring unit.** Book = L lots x 20 x daily sum of per-contract measured M points (net of the 0.242-pt fee; bracket from the fill; 1-s measured fills; busy rule per engine) on the label-day calendar; added to the DD-1 stack series (`out/hedge/stack.npz`: COMP|off Sunday composite, ASIS|off, live lots, one-convention engine). The composite's own maxDD tie to DD-1 (23k L6M / 97k HOLD / 241k PRE / 121k X'; worst-20 PRE -875k, ALL -1,098k). The added book does NOT pass through the stack's locks, ER sizer or integer-lot rounding (first-order overlay); the equal-risk line scales the whole new stack linearly (no re-run of the engine at c).
* **L-windows and worst-20.** L3M (14 wk), L6M (28) and HOLD (32) have fewer than 20 losing weeks, so worst-20 there is not a tail measure; the tail statements rest on PRE, X' and ALL. The composite's L6M maxDD (23k) is one event: RISK-KEEP defined on L6M (the standing order's label) is therefore reported with HOLD, PRE and X' beside it and never alone.
* **Placebo design.** Real trades are re-drawn on random calendar days at the same time-of-day offset from the flat time, same bracket, same number of signals, sides re-assigned with the real long share; the session is re-derived at run time (counts match within a few percent: `n_plc_mean` in PLACEBO_*.csv). It tests timing, not volume. DN (orders engine with absolute limit levels) cannot be moved to other days and is skipped; for DN cells the PRE-and-X' agreement test is the only guard (17 of the 18 DN RISK-KEEP flags fail it).
* **Family-wise correction.** The week-shift null keeps each cell's distribution and the cross-cell dependence but breaks alignment with the stack; it is a fair null for books (their effect on risk comes from alignment). 200 draws per group; p resolution 0.005.
* **S1b caveats.** The derived series have no volume column (unit volume: the HM VWAP leg is a time-weighted VWAP) and duplicate rows per decision second (last kept); Hull and LinReg candles are smoothed OHLC (no NT8 bar type).
* **Not done:** replacement of a live book's session rows inside the lock engine (b3_stack style) for the representatives (none earns it); ICT-IC entry b and liquidity-union target, SB and E1A ports (data not bar-derived; unchanged from BARS-ALL-CANDIDATES open items); latency, purged CV and capacity (no cell is positive enough on the risk measure to justify them).
* **Multiplicity.** Registered cells 840 + 400 + 840 = 2,080 (1,976 with trades) in 3 prereg groups; cumulative count for G6 (UF_TRIALS): side bars_cand3_dd, 3 entries. Every cell fails G6.

Files: `out/g1c3/{s1,s2,s1b}/{CELLS_*.parquet, REPS_*.csv, LOTS_*.parquet, SELECTION_*.csv(.sha256), SCORES_S_*.csv, PLACEBO_*.csv, PLACEBO_RK_*.csv, PLACEBO_TOL_*.csv, select_counts.json}`, `out/g1c3/report_blocks*.md`, `out/recent_wins/g1c3.csv` (all 1976 cells, per-contract and stack columns, recent first, session column, STRICT/TOLERANT/NOW-ONLY, TOL-B/TOL-nc post-hoc). Questions (non-blocking): none.
