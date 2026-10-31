# DS3_RECENT_EDGE_5 - T-RECENT-EDGE section 5, next re-examination cycle (RE-5). Data to label day 20260206. Written 2026-10-31

Companions: DS3_RECENT_EDGE_3.md (RE-3), DS3_RECENT_EDGE_FINAL.md (RE-2), DS3_PERSISTENCE.md (RE-1). Prereg `l2vast/ds3/prereg/RE5_prereg.md` sha256 a6261fa34eb85d3ac74472368f26506572f88d057d578de02ea8d0220a889e49 and addendum 1 (`RE5_prereg_addendum1.md`) sha256 3c7b89e19df6926677e22ce3279583eb7ba6731d22fa8d30e7f0deab4d7c333c, both logged in autopilot/DECISIONS.md (the addendum AFTER the first pass printed counts: lookup extension and unit audit, disclosed below). Code `l2vast/ds3/code/recentedge5/`, outputs `l2vast/ds3/out/recentedge5/`. Masks capped 20260206; UNTOUCHED never read. No engine was re-run: every window value is re-read from the RE-1 ledger (compiled 2026-10-31 15:19Z). Research only; the page is a view.

## PAGE 1 - the plain answers

**Result up front.** Of the 8,939 RISING/NEW edges in the RE-1 ledger, 5,242 belong to programs RE-2 already re-examined and 8 to the RE-3 top-30, leaving 3,689 rows (3,684 distinct trade streams) not yet re-examined. **Only 1,132 of those streams are genuinely new** (not already scored in DEAD_CELLS.csv); 2,552 are repeats of dead or scored cells (numeric-key hits 353, token-spec hits 1173, token-subset hits 1027 before overlap) and were not padded into the count. Selecting on PRE and X' only, 351 of the 1,132 new streams are positive in both (G1), 330 of them also positive in L3M, L6M and HOLD (G2). **Result: 0 PASS, 7 CANDIDATE rows (= 5 distinct ideas), 1125 DEAD** among the 1,132 new streams. No new edge clears every gate: the binding gates are the minimum detectable effect (MDE; 70 of 330 selected-and-recent rows clear it), the placebo (only 31 have a ledger placebo rank >= 0.95) and the stack unit (only 61 have a stored, positive lock-engine stack unit).

**Deviation, stated plainly.** Under the prereg tiers as written, 72 new streams were CANDIDATE and 0 PASS, but 65 of those were CF-COMBO rows. That program's own report and DECISIONS.md log say its metric was corrected from per-planned-lot/fired-subset to per-contract and that the stage1B and pure-wait (F0) numbers are artefacts (planned-lot gains 0.2-0.9 against 2-3 per contract, two rows flip sign on the lock-engine stack). Their ledger values (5-25 pts per trade, positive in every window) are therefore not per-contract numbers and they carry no stack unit; addendum 1 voided them as DEAD (gate U1). The prereg tier is kept in `re5_rows.csv` (column tier_re5); the tiers below are the audited ones (tier_final).

### Table 1 - tier CANDIDATE after audit (all units: ledger primary measure; pts per contract per base trade for exit rules, $/wk for stack rows; MDE beside every row)

| program | cell | book | status | PRE | X' | L6M | HOLD | L3M | MDE (L3M) | placebo rank (ledger / program cohort) | P(next 3m>0) | shrunk L3M | units per-planned-lot / per-contract / lock-engine stack | BH q | tier | failed gates | run-size / recommendation |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| EQR lots_factor | E/SL/WT/NY/P2 @ lots x1.016 | stack | RISING | 1,099 | 377 | 2,641 | 2,422 | 4,881 | 4,321 | 0.78 / 1.00 | 0.72 | 1,444 | n/s / n/s / 4,881 | 0.0042 | CANDIDATE | G4 | shadow; run at <=25% only after a lock-engine stack unit confirms |
| META FS2 | TREE_6m/P4/pre/cfg373 | pre | RISING | 154 | 1,798 | 2,258 | 1,348 | 4,112 | 3,778 |  / 0.96 | 0.70 | 1,014 | n/s / n/s / 4,112 | 0.0060 | CANDIDATE | G4 | shadow; run at <=25% only after a lock-engine stack unit confirms |
| UF-LOSS c1 | A20/SEQ/SEQ(kS>kI>kP2)&NE/half [scope ALL] | ALL | RISING | 0.01 | 0.04 | 0.02 | 0.02 | 0.04 | 0.03 |  / 1.00 | 0.65 | 0.02 | 0.037 / 0.037 / n/s | 0.0060 | CANDIDATE | G4,G7 | shadow; run at <=25% only after a lock-engine stack unit confirms |
| UF-LOSS c1 | A20/SEQ/SEQ(kS>kI>kP2)&NE/cut [scope ALL] | ALL | RISING | 0.03 | 0.09 | 0.04 | 0.04 | 0.07 | 0.07 |  / 0.83 | 0.65 | 0.04 | 0.074 / 0.074 / n/s | 0.0068 | CANDIDATE | G4,G7 | shadow; run at <=25% only after a lock-engine stack unit confirms |
| UF-LOSS c1 | A20/SEQ/SEQ(kS>kI>kP2)&NE/t10 [scope ALL] | ALL | RISING | 0.01 | 0.03 | 0.04 | 0.03 | 0.05 | 0.05 |  / 0.67 | 0.64 | 0.03 | 0.054 / 0.054 / n/s | 0.0090 | CANDIDATE | G4,G7 | shadow; run at <=25% only after a lock-engine stack unit confirms |
| THL_HM | L6_a30_r3_w20 | HM | RISING | 1.32 | 1.39 | 2.30 | 2.30 | 3.37 | 4.86 | 1.00 / 1.00 | 0.56 | 0.77 | 3.368 / 3.368 / n/s | 0.0797 | CANDIDATE | G3,G7 | shadow; run at <=25% only after a lock-engine stack unit confirms |
| EQR lots_factor | A/H/P/M @ lots x1.203 | stack | RISING | 648 | 6,427 | 39,450 | 37,856 | 44,539 | 70,080 | 1.00 / 0.67 | 0.61 | 3,035 | n/s / n/s / 44,539 | 0.0969 | CANDIDATE | G3 | shadow; run at <=25% only after a lock-engine stack unit confirms |

Read: **THL_HM L6_a30_r3_w20** (HM loss-side cut: adverse >= 30 pt, 3 of 3 conditions over 20 s, market exit) is +3.37 pts per contract per trade in L3M against an MDE of 4.86: positive in PRE, X', HOLD and L6M and placebo rank 1.0, but below the MDE, no stack unit, the ledger note says it was looked at on seen data (9 cells) and is not a fresh test, and its persistence expectation is 0.56 with a shrunk L3M of +0.77. **EQR E|SL|WT|NY|P2 @ x1.016** is a lot factor of 1.016 on a stack row (+4.9k $/wk L3M, MDE 4.3k, placebo 0.78, shrunk +1.4k): equal-risk credit is negligible at that factor but the placebo is not cleared. **EQR A|H|P|M @ x1.203** gets +44.5k $/wk but its MDE is 70k and PRE is only +0.6k (weak selection: PRE and X' are under 0.25 of the MDE); the structure note says a rule that lowers risk gets credit for extra lots, so it is unit-inflated until re-scored at equal lots. **META FS2 TREE_6m|P4|pre** is +4.1k $/wk (MDE 3.8k) with PRE +0.15k (0.04 of its MDE, so the PRE leg of the selection is weak) and no placebo rank. **UF-LOSS c1 A20|SEQ... (cut / t10 / half)** are one idea in three exits: +0.037 to +0.074 pts per contract per base trade, MDE 0.034-0.069, no placebo, no stack unit. Nothing here is PASS and none is run above shadow size.

### Table 2 - funnel (rows / streams)

| step | rows | streams |
|---|---|---|
| ledger NEW/RISING rows (RE-1) | 8,939 | |
| excluded: program already re-examined in RE-2 section 2 | 5,242 | |
| excluded: RE-3 top-30 re-read | 8 | |
| not yet re-examined (this cycle) | 3,689 | 3,684 |
| REPEAT of DEAD_CELLS (not counted as new) | 2,557 | 2,552 |
| **genuinely new** | 1,132 | 1,132 |
| G1 selected on PRE and X' (both > 0) | 351 | 351 |
| G1 and G2 (L3M, L6M, HOLD all > 0) | 330 | 330 |
| G3 L3M >= MDE (among G1 and G2) | 70 | |
| G4 placebo rank >= 0.95 (among G1 and G2) | 31 | |
| G5 shrunk expectation > 0 and P(next 3m>0) >= 0.5 (among G1 and G2) | 128 | |
| G6 BH q <= 0.10 (among G1 and G2) | 130 | |
| G7 stack unit stored and positive, no stored unit negative (among G1 and G2) | 61 | |
| G8 causal (no look-ahead) (among G1 and G2) | 306 | |
| prereg CANDIDATE / PASS | 72 / 0 | |
| after unit audit (U1) CANDIDATE / PASS | 7 / 0 | |

Secondary selection count (window-length-weighted PRE+X' mean > 0, informational): 571 new streams.

### Table 3 - by program (genuinely new streams)

| program | streams not yet re-examined | of which REPEAT | new | new selected G1 | new G1&G2 | CANDIDATE (audited) |
|---|---|---|---|---|---|---|
| THL (THLB classic loss rules) | 631 | 631 | 0 | 0 | 0 | 0 |
| THP (THPB classic profit rules) | 598 | 456 | 142 | 15 | 15 | 0 |
| META FS2 | 399 | 344 | 55 | 5 | 5 | 1 |
| META FS1 | 336 | 289 | 47 | 9 | 7 | 0 |
| ADDUW B2 | 276 | 276 | 0 | 0 | 0 | 0 |
| EXP1 loss per-stream fixed | 224 | 0 | 224 | 40 | 40 | 0 |
| CF-COMBO POOL | 114 | 114 | 0 | 0 | 0 | 0 |
| CF-COMBO stage1ENG | 108 | 38 | 70 | 70 | 70 | 0 |
| UF-LOSS c3 | 97 | 97 | 0 | 0 | 0 | 0 |
| CUTWAIT | 95 | 86 | 9 | 2 | 1 | 0 |
| L2ENTRY-B | 58 | 58 | 0 | 0 | 0 | 0 |
| EQR lots_factor | 50 | 0 | 50 | 10 | 9 | 2 |
| THL2 L2H (hypotheses H1-H12) | 46 | 0 | 46 | 13 | 13 | 0 |
| UF-ENTRY c1 | 45 | 0 | 45 | 1 | 1 | 0 |
| UF-LOSS c5 | 43 | 43 | 0 | 0 | 0 | 0 |
| UF-ENTRY c2 | 43 | 0 | 43 | 14 | 10 | 0 |
| ABRC1 (bracket choice per entry) | 40 | 0 | 40 | 4 | 4 | 0 |
| EXP1 profit chains (v0, look-ahead vol key) | 40 | 0 | 40 | 24 | 24 | 0 |
| EXP1 profit chains (causal vol key) | 32 | 0 | 32 | 1 | 1 | 0 |
| CF-COMBO stage1B | 31 | 31 | 0 | 0 | 0 | 0 |
| UF-PROFIT c2 | 30 | 6 | 24 | 3 | 2 | 0 |
| STRUCT48 | 28 | 0 | 28 | 22 | 22 | 0 |
| UF-LOSS c1 | 26 | 0 | 26 | 7 | 6 | 3 |
| CONFIRM-BARS S1 | 23 | 0 | 23 | 17 | 16 | 0 |
| UF-LOSS c6 | 22 | 22 | 0 | 0 | 0 | 0 |
| CONFIRM-BARS S3 | 21 | 0 | 21 | 17 | 16 | 0 |
| UF-ENTRY c4 | 19 | 0 | 19 | 3 | 1 | 0 |
| CONFIRM-BARS S1c | 18 | 0 | 18 | 12 | 10 | 0 |
| CF-COMBO GREEDY | 15 | 15 | 0 | 0 | 0 | 0 |
| UF-LOSS c4 | 15 | 15 | 0 | 0 | 0 | 0 |
| STRUCT48 NM-B | 14 | 0 | 14 | 2 | 2 | 0 |
| EXP1 profit fixed | 13 | 0 | 13 | 4 | 4 | 0 |
| EXP2 (f) stack/ES-RTY state features | 13 | 13 | 0 | 0 | 0 | 0 |
| CONFIRM-BARS S2c | 13 | 0 | 13 | 9 | 8 | 0 |
| CONFIRM-BARS S2 | 11 | 0 | 11 | 9 | 6 | 0 |
| CONFIRM-BARS S2b | 11 | 0 | 11 | 10 | 10 | 0 |
| UF-PROFIT c3 | 11 | 2 | 9 | 5 | 4 | 0 |
| THL_HM | 9 | 0 | 9 | 9 | 9 | 1 |
| CONFIRM-BARS S4 | 9 | 0 | 9 | 6 | 6 | 0 |
| UF-PROFIT c4 | 9 | 0 | 9 | 2 | 2 | 0 |
| THL2 L2P (walk-forward policies on the order book) | 8 | 0 | 8 | 2 | 2 | 0 |
| UF-PROFIT c1 | 6 | 5 | 1 | 0 | 0 | 0 |
| UF-ENTRY c3 | 6 | 0 | 6 | 2 | 2 | 0 |
| L2SL loss (THL2/THP_POLICY loss) | 6 | 0 | 6 | 0 | 0 | 0 |
| L2SET-ENTRY | 5 | 2 | 3 | 0 | 0 | 0 |
| CF-COMBO FOUR | 4 | 4 | 0 | 0 | 0 | 0 |
| THP_POLICY joint (L2SE entry / L2SP profit / L2SL loss) | 4 | 0 | 4 | 1 | 1 | 0 |
| FIRST-HOUR-DELTA | 3 | 3 | 0 | 0 | 0 | 0 |
| ADDUW B1 | 2 | 0 | 2 | 0 | 0 | 0 |
| UF-LOSS c2 | 2 | 2 | 0 | 0 | 0 | 0 |
| EXP2 (d) joint stack | 1 | 0 | 1 | 0 | 0 | 0 |
| EXP1 vol_lo+ON take@50% (post-look LEAD) | 1 | 0 | 1 | 1 | 1 | 0 |

### Table 4 - best DEAD rows among new streams selected and recent-positive (G1 and G2), ranked by z3, with the gates that failed

| program | cell | book | status | PRE | X' | L6M | HOLD | L3M | MDE (L3M) | placebo rank (ledger / program cohort) | P(next 3m>0) | shrunk L3M | units per-planned-lot / per-contract / lock-engine stack | BH q | tier | failed gates | run-size / recommendation |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CONFIRM-BARS S1 | tc/45s/three_bar/c1/near/X5/W0/N | PE | NEW | 0.91 | 0.30 | 1.43 | 1.40 | 3.13 | 3.21 |  / 1.00 | 0.51 | 0.77 | n/s / 3.128 / n/s | 0.0147 | DEAD | G3,G4,G7 | no |
| CONFIRM-BARS S1 | ha/10m/three/d/near/X3/A70/N | ST | NEW | 0.20 | 1.13 | 0.32 | 0.35 | 1.87 | 1.98 |  / 0.94 | 0.50 | 0.46 | n/s / 1.871 / n/s | 0.0190 | DEAD | G3,G4,G7 | no |
| EXP1 loss per-stream fixed | CR/L6_a45_r2_w15 | CR | RISING | 0.04 | 0.08 | 0.15 | 0.13 | 0.29 | 0.31 |  / 1.00 | 0.62 | 0.17 | n/s / 0.289 / n/s | 0.0214 | DEAD | G3,G4,G7 | no |
| EXP1 loss per-stream fixed | CR/L6_a45_r2_w10 | CR | RISING | 0.05 | 0.06 | 0.17 | 0.14 | 0.32 | 0.35 |  / 0.97 | 0.62 | 0.19 | n/s / 0.322 / n/s | 0.0214 | DEAD | G3,G4,G7 | no |
| CONFIRM-BARS S2b | dib/s30/imb_sign/d/near/X3/A70/N | PE | NEW | 0.41 | 1.51 | 0.14 | 0.11 | 3.33 | 3.61 |  / 1.00 | 0.50 | 0.82 | n/s / 3.328 / n/s | 0.0214 | DEAD | G3,G4,G5,G7 | no |
| EXP1 loss per-stream fixed | CR/L6_a45_r2_w20 | CR | RISING | 0.04 | 0.05 | 0.16 | 0.14 | 0.30 | 0.33 |  / 0.95 | 0.62 | 0.18 | n/s / 0.302 / n/s | 0.0214 | DEAD | G3,G4,G7 | no |
| EXP1 loss per-stream fixed | CR/L6_a45_r2_w5 | CR | RISING | 0.03 | 0.06 | 0.15 | 0.12 | 0.27 | 0.30 |  / 0.93 | 0.61 | 0.16 | n/s / 0.270 / n/s | 0.0242 | DEAD | G3,G4,G7 | no |
| CONFIRM-BARS S1c | ha/15m/flip/d/near/X3/A70/N | PE | RISING | 0.55 | 0.40 | 1.11 | 0.86 | 1.93 | 2.27 |  / 1.00 | 0.48 | 0.48 | n/s / 1.927 / n/s | 0.0356 | DEAD | G3,G4,G5,G7 | no |
| THL2 L2H (hypotheses H1-H12) | H7P/pct0.7/with10/n3/take | 10 static books pooled | RISING | 0.43 | 0.27 | 0.89 | 0.97 | 1.14 | 1.38 |  / 1.00 | 0.59 | 0.67 | n/s / 1.138 / n/s | 0.0419 | DEAD | G3,G4,G7 | no |
| CONFIRM-BARS S3 | tc/30s/ua_fade/c2/mid/X3/W0/N | PE | NEW | 0.64 | 1.03 | 0.35 | 0.31 | 2.93 | 3.62 |  / 1.00 | 0.47 | 0.72 | n/s / 2.930 / n/s | 0.0458 | DEAD | G3,G4,G5,G7 | no |
| STRUCT48 | ES_RSI2_t10 @ ratio 0.25 | sleeve ES | RISING | 5,310 | 2,017 | 9,420 | 8,242 | 12,452 | 15,465 |  / 1.00 | 0.30 | 3,070 | n/s / n/s / 12,452 | 0.0458 | DEAD | G3,G4,G5 | no |
| STRUCT48 | ES_RSI2_t10 @ ratio 1.0 | sleeve ES | RISING | 21,238 | 8,067 | 37,679 | 32,969 | 49,807 | 61,861 |  / 0.95 | 0.30 | 12,281 | n/s / n/s / 49,807 | 0.0458 | DEAD | G3,G4,G5 | no |
| STRUCT48 | ES_RSI2_t10 @ ratio 0.5 | sleeve ES | RISING | 10,619 | 4,033 | 18,839 | 16,484 | 24,904 | 30,930 |  / 0.91 | 0.30 | 6,141 | n/s / n/s / 24,904 | 0.0458 | DEAD | G3,G4,G5 | no |
| CONFIRM-BARS S1c | ha/1m/flip/b/mid/X3/A70/N | KB | NEW | 0.10 | 0.28 | 0.71 | 0.68 | 1.50 | 1.86 |  / 0.90 | 0.47 | 0.37 | n/s / 1.496 / n/s | 0.0460 | DEAD | G3,G4,G5,G7 | no |
| UF-LOSS c1 | A20/RARE/P2&WC&ESA&NE/half [scope ALL] | ALL | RISING | 0.00 | 0.03 | 0.01 | 0.01 | 0.02 | 0.03 |  / 0.42 | 0.59 | 0.01 | 0.023 / 0.023 / n/s | 0.0483 | DEAD | G3,G4,G7 | no |
| UF-LOSS c1 | A20/RARE/P2&WC&ESA&NE/cut [scope ALL] | ALL | RISING | 0.00 | 0.06 | 0.03 | 0.03 | 0.05 | 0.06 |  / 0.42 | 0.59 | 0.03 | 0.046 / 0.046 / n/s | 0.0483 | DEAD | G3,G4,G7 | no |
| EQR lots_factor | E/SL/HM/NY/P1.5+L1.5 @ lots x1.027 | stack | NEW | 238 | 751 | 2,369 | 2,597 | 10,912 | 13,889 | 0.78 / 0.89 | 0.64 | 3,228 | n/s / n/s / 10,912 | 0.0504 | DEAD | G3,G4 | no |
| CONFIRM-BARS S2 | renkomed/m1/n2/d/near/X3/A70/N | DN | NEW | 0.94 | 0.10 | 0.22 | 0.13 | 1.37 | 1.76 |  / 1.00 | 0.46 | 0.34 | n/s / 1.374 / n/s | 0.0512 | DEAD | G3,G4,G5,G7 | no |
| CONFIRM-BARS S4 | hax/vol_2000/two/d/near/X3/A70/N | WT | NEW | 0.21 | 0.59 | 0.25 | 0.26 | 1.31 | 1.68 |  / 1.00 | 0.46 | 0.32 | n/s / 1.314 / n/s | 0.0512 | DEAD | G3,G4,G5,G7 | no |
| CONFIRM-BARS S2 | renkomed/m1/cont/d/near/X3/A70/N | DN | NEW | 0.91 | 0.10 | 0.11 | 0.02 | 1.32 | 1.71 |  / 0.83 | 0.46 | 0.33 | n/s / 1.323 / n/s | 0.0527 | DEAD | G3,G4,G5,G7 | no |

### Table 5 - CF-COMBO rows voided by the unit audit (summary)
65 new CF-COMBO streams were CANDIDATE under the prereg tiers (stages: {'CF-COMBO stage1ENG': 65}; books {'ST': 19, 'SM': 18, 'DN': 13, 'MA': 6, 'HM': 4, 'PE': 3, 'MV': 1, 'PB': 1}); all are near-duplicates (iplFVG/FVG/iFVG 15-45 s then OB, same limit placement) and most fail the placebo (median ledger placebo rank 0.38). They are in the CSV with tier_final DEAD and failed gate U1.

## Method notes and limits (read before using any row)

1. **Selection** on PRE (2024-02..2025-06) and X' (2023-04..2024-01) only: both must be > 0; the recent look (L3M 2025-11-06..2026-02-06, L6M, HOLD from 2025-07) is taken once and nothing was re-tuned. Because PRE and X' are sign tests, a row can be selected with PRE and X' far below its MDE; the weak_sel column marks rows where both are under 0.25 of the MDE.
2. **Shrunk expectation** is the ledger's L3M x the DS3_PERSISTENCE shrinkage for the family and t-bucket. That shrinkage is negative for most families (median -0.23 across the whole ledger), so only 14% of ledger rows keep a positive shrunk expectation at all; this is the single most important number for how a recent edge should be read.
3. **Statuses** (NEW/RISING) come from the RE-1 ledger. Only a few programs have a stored monthly series; for the rest the status is the RE-1 proxy (L3M against the implied months -6..-3), not a measured streak. No row here has a measured persistence score above the family base rate.
4. **Units.** Per-planned-lot is shown only where the row's own note defines the measure per base trade over all trades (exit rules; the other rows show n/s, not zero); per-contract is the ledger's L3M pts per contract; lock-engine stack is the ledger's stack $/wk or the primary when the base is the lock-engine stack. No row has all three; no engine was run in this cycle. A CANDIDATE therefore means 'worth a stack re-score', never 'run'.
5. **dead_lookup.** Before scoring: numeric key (L6M, HOLD, PRE, X' to 3 decimals) against DEAD_CELLS; token-spec dead_lookup.is_dead (tol 0.02, min_frac 1.0, program-restricted) for THL, THP, CUTWAIT; after the addendum a token-subset match for META, CF-COMBO, EXP1, EQR, UF-LOSS/ENTRY/PROFIT by cycle, THL2, ABRC1, CONFIRM-BARS, THL_HM, L2SL, ADDUW, L2ENTRY-B, L2SET-ENTRY. Programs with no DEAD_CELLS counterpart (STRUCT48 and similar older closed programs) could not be looked up and are counted as new. The method per row is in re5_rows.csv (dl_num, dl_spec, dl_tok). After scoring, the 1,132 new streams were appended with append_cells (program RE5_*, 1,125 DEAD, 7 CANDIDATE); the file was never rebuilt.
6. **Multiplicity.** BH q is over the new streams that pass G1 and G2 only (a small family); it does not include the trials of the originating programs (for example CF-COMBO 1 of 59,925 cells, META 1 of 1,330 configs). Read q as a ranking, not as a family-wise guarantee. For the same reason the CANDIDATE label here is weaker than the same label in the original programs.
7. Files: `out/recentedge5/re5_rows.csv` (every row, every gate, both tiers, lookup method), `re5_counts.txt`, `score.log`.