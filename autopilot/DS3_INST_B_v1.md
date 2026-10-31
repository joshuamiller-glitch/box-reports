DATA: on disk and derived, nothing to buy. NQ trade tape with aggressor side and pre-trade BBO (tables/NQ/tape; 11 defective months replaced by the de-duplicated drop-in files), 1-s mbp-10 aggregates, raw mbp-10 dbn to 2026-10; built 10-s buckets, 50-contract VPIN buckets, minute grid (out/inst/B/). Not on disk: order-level MBO (algo child orders, true lifetimes; quote on file ~$953 for the three research spans, NO purchase) and the NYSE closing-imbalance feed (15:50 ET; not quoted here, proxy used).

# DS3_INST_B - institutional execution footprints (working algos) and the MOC window (INST-2, section B of T-INSTITUTIONAL)

Research only, nothing promoted. Prereg l2vast/ds3/prereg/INST_B_prereg.md sha256 ccf85f1293ad0033ac2b355594c85e3729e86410e531c409b953185280720364 (92 cells; thresholds sha256 92852e43...d5bd); PRE+X' selection out/inst/B/selection_PRE_X.json sha256 464324dd2faf4354a74193abd230f5f5bc7cc6c5c0d9c8d9e36c001f31eaa575 logged before the recent look; ONE recent look at the 8 carried cells. Masks capped 20260206, UNTOUCHED never read. Engine: ONE-CONVENTION (live lots, 70/30, parity stop, running-max SizeMult, integer lots); sizers through the engine multiplier. Code l2vast/ds3/code/inst/B/, out l2vast/ds3/out/inst/B/, rows out/recent_wins/inst_B.csv.

## Page 1

**Plain sentence.** Working-algo footprint: a buyer or seller is detectable in 4.2% of RTH minutes (15-min, 80th-percentile definition, L6M; 1.7% for the 30-min 90th-percentile definition the PRE+X' selection kept); signals taken WITH that footprint pay +23.3 pts per contract (n=68, MDE 24.4) against +6.5 with no footprint (n=2,374, MDE 5.3) in L6M, but the books are trend followers that already trade with the flow (91% of fired states are WITH, AGAINST had 1 signal in L6M), PRE is +3.3 vs +4.4 and placebo ranks are 0.97 (random same-count, L6M) but 0.35 (PRE); as the registered WITH x1.5 / AGAINST x0.5 sizer on the stack it is +1.35k/wk in L6M (MDE 2.48k, inside), positive in all five windows (STRICT yes) but TOLERANT NO (PRE worst-20 weeks -904k vs the stack's -875k) and every cell is inside its MDE; the standalone "ride the algo" books lose 1.0-1.6 pts per trade (the cost of acting; -0.4k to -3.1k $/wk at 1 contract in PRE, several beyond MDE), fading its end loses, exiting on its end loses in L3M/L6M/HOLD, and the 15:50 MOC rules have no edge (C1 +0.07 PRE / -2.75 X' per trade). Nothing promoted.

| item | result |
|---|---|
| cells registered / carried by PRE+X' | 92 / 8 (22 pass PRE>=0 and X'>=0; 14 of those are zero or tiny effects) |
| carried cells: STRICT / TOLERANT (literal) / NOW-ONLY | 1 / 0 / 1 (F1 W30 c0.9 sm0 A4); other 7 fail L3M/L6M |
| beside (labelled post-hoc, never TOLERANT): TOL-B / TOL-nc | 0 / 0 |
| best cell stack delta no lock, $k/wk (MDE) | L3M +0.69 (4.47), L6M +1.35 (2.48), HOLD +1.24 (2.25), PRE +0.97 (2.26), X' +0.50 (1.74) |
| same, 12R combined lock | L3M +0.80 (3.77), L6M +6.58 (13.97), HOLD +5.68 (12.27), PRE +0.04 (3.58), X' -0.19 (0.98) |
| standalone F2 (32 cells) PRE / X' | all 32 negative in PRE and in X'; 8 more standalone cells (F3b fade, F4 MOC) also non-positive in PRE or X' except F4 C1 PRE +0.006k |
| IC of net flow x agreement, 1 / 5 / 30 min | +0.00..+0.01 (|t| <= 1.4), the price-momentum control is as large |
| the 14:40-15:00 skip | signals fired there are followed by -13 to -24 pts (sided) into 15:50/16:00 in PRE, HOLD and L6M (3-5 SE), not in X'; footprint prevalence there is unremarkable |

## 1. State detector and prevalence
Definition in the prereg (net aggressor imbalance, agreement of 1-min signs, uncentred 10-s autocorrelation, optional small-print share; thresholds = per-session PRE u X' quantiles, no returns). Share of RTH minutes in a footprint (small-print variant sm=1 omitted):

| W | c | win | buyer_pct_RTH | seller_pct_RTH | any_pct_RTH |
|---|---|---|---|---|---|
| 5 | 0.80 | L6M | 2.91 | 3.24 | 6.14 |
| 5 | 0.80 | PRE | 3.54 | 3.84 | 7.38 |
| 5 | 0.80 | X | 5.64 | 4.98 | 10.62 |
| 5 | 0.90 | L6M | 1.61 | 1.65 | 3.26 |
| 5 | 0.90 | PRE | 1.94 | 1.96 | 3.91 |
| 5 | 0.90 | X | 3.16 | 2.69 | 5.85 |
| 15 | 0.80 | L6M | 1.86 | 2.38 | 4.24 |
| 15 | 0.80 | PRE | 2.85 | 3.11 | 5.97 |
| 15 | 0.80 | X | 5.12 | 4.15 | 9.27 |
| 15 | 0.90 | L6M | 0.92 | 1.23 | 2.15 |
| 15 | 0.90 | PRE | 1.56 | 1.65 | 3.21 |
| 15 | 0.90 | X | 2.97 | 2.28 | 5.26 |
| 30 | 0.80 | L6M | 1.14 | 1.92 | 3.06 |
| 30 | 0.80 | PRE | 2.16 | 2.57 | 4.73 |
| 30 | 0.80 | X | 4.06 | 3.25 | 7.32 |
| 30 | 0.90 | L6M | 0.55 | 1.10 | 1.65 |
| 30 | 0.90 | PRE | 1.21 | 1.44 | 2.65 |
| 30 | 0.90 | X | 2.47 | 1.79 | 4.26 |

Control: net flow correlates 0.73 (Spearman, minute grid) with the trailing 15-min return, so every state is shown beside the same-quantile momentum state (tables below).

## 2. Direction filter on the live books (F1) - carried cells, one recent look
### T1 stack delta vs the as-is composite, $k/wk (MDE 2.8 SE of the paired weekly delta in brackets; * = beyond MDE), ONE-CONVENTION live lots

| cell | conv | L3M | L6M | HOLD | PRE | X' | 2026 |
|---|---|---|---|---|---|---|---|
| F1|W30|c0.9|sm0|A4 | no lock | +0.69 (4.47) | +1.35 (2.48) | +1.24 (2.25) | +0.97 (2.26) | +0.50 (1.74) | +1.40 (2.99) |
| F1|W30|c0.9|sm0|A4 | 12R lock | +0.80 (3.77) | +6.58 (13.97) | +5.68 (12.27) | +0.04 (3.58) | -0.19 (0.98) | +0.67 (1.12) |
| F1|W30|c0.9|sm0|A4 | LIVE-CAL stop 2.45 | +0.68 (4.48) | +1.35 (2.47) | +1.24 (2.24) | +0.92 (2.27) | +0.48 (1.74) | +1.40 (2.99) |
| F1|W5|c0.8|sm0|A4 | no lock | -4.10 (10.47) | -0.94 (5.45) | -0.73 (4.78) | +0.07 (2.06) | +0.81 (1.72) | +1.94 (2.58) |
| F1|W5|c0.8|sm0|A4 | 12R lock | -1.60 (9.20) | -0.22 (4.66) | -0.21 (4.07) | -0.11 (2.13) | +1.41 (3.16) | +1.52 (2.55) |
| F1|W5|c0.8|sm0|A4 | LIVE-CAL stop 2.45 | -4.16 (10.51) | -0.98 (5.48) | -0.77 (4.80) | +0.04 (2.10) | +0.60 (1.94) | +1.92 (2.61) |
| F3a|W30|c0.8 | no lock | -7.40 (12.68) | -5.99 (7.80) | -5.97 (6.86) | +0.61 (3.03) | +0.06 (2.67) | -1.79 (10.82) |
| F3a|W30|c0.8 | 12R lock | -8.68 (15.86) | -5.03 (8.86) | -4.52 (7.78) | +2.98 (4.68) | -0.04 (3.71) | -0.59 (7.10) |
| F3a|W30|c0.8 | LIVE-CAL stop 2.45 | -7.40 (12.68) | -5.95 (7.79) | -5.93 (6.86) | +0.66 (3.05) | +0.10 (2.68) | -1.78 (10.84) |
| F3a|W30|c0.9 | no lock | -1.34 (4.30) | -1.52 (4.88) | -1.55 (4.29) | +0.20 (2.79) | +0.38 (1.92) | -0.69 (8.53) |
| F3a|W30|c0.9 | 12R lock | -0.67 (2.77) | +0.40 (3.32) | +0.20 (2.96) | +2.02 (4.12) | -0.18 (3.54) | +0.78 (1.42) |
| F3a|W30|c0.9 | LIVE-CAL stop 2.45 | -1.35 (4.30) | -1.51 (4.89) | -1.54 (4.30) | +0.23 (2.81) | +0.40 (1.91) | -0.69 (8.54) |
| F1|W5|c0.8|sm0|A1 | no lock | -3.72 (8.97) | -1.86 (4.51) | -1.63 (3.95) | +0.28 (1.34) | +0.18 (0.45) | -0.37 (2.66) |
| F1|W5|c0.8|sm0|A1 | 12R lock | -5.57 (14.88) | -2.79 (7.45) | -2.44 (6.52) | -0.11 (1.21) | -0.00 (0.34) | -0.39 (2.71) |
| F1|W5|c0.8|sm0|A1 | LIVE-CAL stop 2.45 | -3.72 (8.97) | -1.86 (4.52) | -1.63 (3.95) | +0.28 (1.36) | +0.18 (0.46) | -0.38 (2.72) |
| F1|W5|c0.9|sm1|A4 | no lock | +0.19 (1.96) | -0.21 (1.18) | -0.18 (1.03) | +0.15 (0.71) | +0.19 (0.66) | +1.47 (3.05) |
| F1|W5|c0.9|sm1|A4 | 12R lock | +0.53 (1.39) | +0.10 (0.85) | +0.09 (0.75) | -0.37 (0.97) | +0.30 (0.46) | +1.07 (3.15) |
| F1|W5|c0.9|sm1|A4 | LIVE-CAL stop 2.45 | +0.16 (1.97) | -0.23 (1.18) | -0.20 (1.03) | +0.15 (0.72) | -0.01 (1.09) | +1.46 (3.05) |
| F1|W5|c0.9|sm0|A1 | no lock | -0.09 (0.24) | -0.04 (0.12) | -0.04 (0.11) | +0.18 (0.59) | +0.09 (0.41) | +0.00 (0.00) |
| F1|W5|c0.9|sm0|A1 | 12R lock | -0.09 (0.24) | -0.04 (0.12) | -0.04 (0.11) | -0.09 (0.24) | -0.00 (0.34) | +0.00 (0.00) |
| F1|W5|c0.9|sm0|A1 | LIVE-CAL stop 2.45 | -0.09 (0.24) | -0.04 (0.12) | -0.04 (0.11) | +0.17 (0.61) | +0.09 (0.42) | +0.00 (0.00) |
| F1|W5|c0.8|sm0|A2 | no lock | -2.80 (7.78) | -1.40 (3.89) | -1.22 (3.40) | +0.20 (0.76) | +0.06 (0.16) | +0.16 (0.62) |
| F1|W5|c0.8|sm0|A2 | 12R lock | -2.71 (7.79) | -1.35 (3.89) | -1.19 (3.41) | +0.01 (0.69) | -0.00 (0.11) | +0.16 (0.62) |
| F1|W5|c0.8|sm0|A2 | LIVE-CAL stop 2.45 | -2.79 (7.78) | -1.40 (3.89) | -1.22 (3.40) | +0.21 (0.76) | +0.06 (0.17) | +0.16 (0.63) |

### T2 per contract (pts per contract of the lots the rule adds or removes, + = good; MDE 2.8 day-clustered SE; n = affected kept signals)

| cell | conv | L3M | L6M | HOLD | PRE | X' | 2026 |
|---|---|---|---|---|---|---|---|
| F1|W30|c0.9|sm0|A4 | N parity | +27.0 (24.4) n34 | +21.9 (23.3) n69 | +22.4 (21.6) n80 | +3.3 (18.0) n170 | +11.2 (26.3) n85 | +34.4 (43.9) n11 |
| F1|W30|c0.9|sm0|A4 | LIVE-CAL | +27.0 (24.4) n34 | +21.8 (23.4) n69 | +22.4 (21.7) n80 | +3.0 (18.1) n170 | +11.0 (26.4) n85 | +34.3 (44.0) n11 |
| F1|W5|c0.8|sm0|A4 | N parity | -12.5 (30.8) n58 | -0.5 (25.4) n94 | +1.4 (24.5) n101 | +1.7 (14.2) n247 | +13.5 (20.2) n107 | +20.2 (31.3) n21 |
| F1|W5|c0.8|sm0|A4 | LIVE-CAL | -12.7 (30.8) n58 | -0.7 (25.4) n94 | +1.3 (24.5) n101 | +1.5 (14.3) n245 | +13.4 (20.3) n107 | +20.1 (31.6) n21 |
| F3a|W30|c0.8 | N parity | -26.3 (22.1) n61 | -22.7 (19.4) n111 | -23.2 (18.3) n124 | +1.8 (14.1) n291 | -1.2 (17.8) n121 | -18.1 (27.9) n18 |
| F3a|W30|c0.8 | LIVE-CAL | -26.3 (22.1) n61 | -22.6 (19.5) n111 | -23.1 (18.5) n124 | +2.1 (14.3) n285 | -0.9 (17.9) n121 | -17.9 (28.0) n18 |
| F3a|W30|c0.9 | N parity | -10.6 (27.1) n33 | -15.1 (29.3) n66 | -15.3 (27.1) n76 | +0.2 (18.8) n170 | +2.6 (19.5) n74 | -15.0 (23.4) n12 |
| F3a|W30|c0.9 | LIVE-CAL | -10.7 (27.1) n33 | -15.0 (29.5) n66 | -15.2 (27.2) n76 | +0.5 (19.3) n164 | +2.9 (19.5) n74 | -14.9 (23.4) n12 |
| F1|W5|c0.8|sm0|A1 | N parity | -37.1 (49.1) n5 | -37.1 (49.1) n5 | -37.1 (49.1) n5 | +15.1 (52.5) n12 | +27.8 (61.8) n5 | +21.9 (52.5) n2 |
| F1|W5|c0.8|sm0|A1 | LIVE-CAL | -37.0 (49.4) n5 | -37.0 (49.4) n5 | -37.0 (49.4) n5 | +15.3 (52.8) n12 | +28.8 (62.3) n5 | +22.3 (53.5) n2 |
| F1|W5|c0.9|sm1|A4 | N parity | +3.6 (52.7) n16 | +0.9 (44.8) n23 | +0.9 (44.8) n23 | +12.0 (36.3) n38 | +16.6 (82.6) n7 | +20.0 (57.2) n8 |
| F1|W5|c0.9|sm1|A4 | LIVE-CAL | +3.5 (52.7) n16 | +0.8 (44.8) n23 | +0.8 (44.8) n23 | +12.6 (36.7) n37 | +16.5 (83.0) n7 | +19.8 (57.4) n8 |
| F1|W5|c0.9|sm0|A1 | N parity | -61.1 (0.0) n1 | -61.1 (0.0) n1 | -61.1 (0.0) n1 | +40.7 (42.9) n4 | +20.9 (94.5) n3 | n0 |
| F1|W5|c0.9|sm0|A1 | LIVE-CAL | -61.1 (0.0) n1 | -61.1 (0.0) n1 | -61.1 (0.0) n1 | +40.7 (45.3) n4 | +21.3 (95.0) n3 | n0 |
| F1|W5|c0.8|sm0|A2 | N parity | -37.1 (49.1) n5 | -37.1 (49.1) n5 | -37.1 (49.1) n5 | +15.1 (52.5) n12 | +27.8 (61.8) n5 | +21.9 (52.5) n2 |
| F1|W5|c0.8|sm0|A2 | LIVE-CAL | -37.0 (49.4) n5 | -37.0 (49.4) n5 | -37.0 (49.4) n5 | +15.3 (52.8) n12 | +28.8 (62.3) n5 | +22.3 (53.5) n2 |

### T3 tiers (T-SIXTY columns) and risk lines (no lock, parity; maxDD and worst-20 in $k, rule vs as-is)

| cell | STRICT | TOLERANT (headline) | NOW-ONLY | TOL-B (post-hoc) | TOL-nc (post-hoc) | failed gates | L6M SD rule/as-is | L6M maxDD rule/as-is | PRE worst-20 rule/as-is | t(6m) | persistence | shrunk $k/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F1|W30|c0.9|sm0|A4 | yes | NO | yes | no | no | TOL(PRE worst-20 vs stack) | 43.7/42.7 | 106/95 | -904/-875 | 1.52 | 0.50 | 0.00 |
| F1|W5|c0.8|sm0|A4 | no | NO | no | no | no | NOW(L3M/L6M stack+pc>0) | 42.8/42.7 | 110/95 | -910/-875 | -0.48 | 0.50 | -0.00 |
| F3a|W30|c0.8 | no | NO | no | no | no | NOW(L3M/L6M stack+pc>0) | 41.7/42.7 | 93/95 | -852/-875 | -2.15 | 0.45 | -0.00 |
| F3a|W30|c0.9 | no | NO | no | no | no | NOW(L3M/L6M stack+pc>0) | 42.6/42.7 | 95/95 | -870/-875 | -0.87 | 0.45 | -0.00 |
| F1|W5|c0.8|sm0|A1 | no | NO | no | no | no | NOW(L3M/L6M stack+pc>0) | 44.3/42.7 | 95/95 | -862/-875 | -1.15 | 0.50 | -0.00 |
| F1|W5|c0.9|sm1|A4 | no | NO | no | no | no | NOW(L3M/L6M stack+pc>0) | 42.7/42.7 | 96/95 | -864/-875 | -0.49 | 0.50 | 0.00 |
| F1|W5|c0.9|sm0|A1 | no | NO | no | no | no | NOW(L3M/L6M stack+pc>0) | 42.7/42.7 | 95/95 | -872/-875 | -1.00 | 0.50 | -0.00 |
| F1|W5|c0.8|sm0|A2 | no | NO | no | no | no | NOW(L3M/L6M stack+pc>0) | 43.8/42.7 | 95/95 | -869/-875 | -1.01 | 0.50 | -0.00 |

### T4 placebo ranks (share of 200 draws with a smaller per-contract effect; stack-level share of 40 draws with a smaller $/wk delta); P1 shuffled 1-min blocks within day x session (carries the session direction in hindsight: a harsh null), P2 state of the same minute from another label day, P3 random action same count per book x session

| cell | kind | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| F1|W30|c0.9|sm0|A4 | per-contract P1 | 0.67 | 0.61 | 0.60 | 0.16 | 0.36 |
| F1|W30|c0.9|sm0|A4 | per-contract P2 | 0.87 | 0.93 | 0.96 | 0.76 | 0.79 |
| F1|W30|c0.9|sm0|A4 | per-contract P3 | 0.98 | 0.97 | 0.98 | 0.35 | 0.83 |
| F1|W30|c0.9|sm0|A4 | stack P1 (40) | 0.68 | 0.95 | 0.85 | 0.85 | 0.55 |
| F1|W30|c0.9|sm0|A4 | stack P3 (40) | 0.50 | 0.78 | 0.72 | 0.90 | 0.80 |
| F1|W5|c0.8|sm0|A4 | per-contract P1 | 0.15 | 0.40 | 0.45 | 0.43 | 0.82 |
| F1|W5|c0.8|sm0|A4 | per-contract P2 | 0.17 | 0.36 | 0.46 | 0.73 | 0.86 |
| F1|W5|c0.8|sm0|A4 | per-contract P3 | 0.07 | 0.19 | 0.32 | 0.38 | 0.95 |
| F1|W5|c0.8|sm0|A4 | stack P1 (40) | 0.05 | 0.17 | 0.17 | 0.45 | 0.93 |
| F1|W5|c0.8|sm0|A4 | stack P3 (40) | 0.03 | 0.17 | 0.17 | 0.55 | 0.95 |
| F1|W5|c0.8|sm0|A1 | per-contract P1 | 0.04 | 0.01 | 0.01 | 0.90 | 0.96 |
| F1|W5|c0.8|sm0|A1 | per-contract P2 | 0.06 | 0.04 | 0.03 | 0.97 | 0.97 |
| F1|W5|c0.8|sm0|A1 | per-contract P3 | 0.26 | 0.20 | 0.18 | 0.80 | 0.76 |
| F1|W5|c0.8|sm0|A1 | stack P1 (40) | 0.03 | 0.10 | 0.07 | 0.62 | 0.62 |
| F1|W5|c0.8|sm0|A1 | stack P3 (40) | 0.00 | 0.00 | 0.00 | 0.65 | 0.62 |
| F1|W5|c0.9|sm1|A4 | per-contract P1 | 0.45 | 0.46 | 0.46 | 0.68 | 0.61 |
| F1|W5|c0.9|sm1|A4 | per-contract P2 | 0.52 | 0.43 | 0.43 | 0.80 | 0.65 |
| F1|W5|c0.9|sm1|A4 | per-contract P3 | 0.54 | 0.40 | 0.38 | 0.77 | 0.74 |
| F1|W5|c0.9|sm1|A4 | stack P1 (40) | 0.68 | 0.42 | 0.35 | 0.72 | 0.97 |
| F1|W5|c0.9|sm1|A4 | stack P3 (40) | 0.68 | 0.35 | 0.30 | 0.72 | 0.88 |
| F1|W5|c0.9|sm0|A1 | per-contract P1 | 0.01 | 0.00 | 0.00 | 1.00 | 0.80 |
| F1|W5|c0.9|sm0|A1 | per-contract P2 | 0.02 | 0.01 | 0.00 | 1.00 | 0.90 |
| F1|W5|c0.9|sm0|A1 | per-contract P3 | 0.12 | 0.10 | 0.10 | 0.83 | 0.50 |
| F1|W5|c0.9|sm0|A1 | stack P1 (40) | 0.50 | 0.47 | 0.50 | 0.65 | 0.60 |
| F1|W5|c0.9|sm0|A1 | stack P3 (40) | 0.23 | 0.28 | 0.30 | 0.88 | 0.78 |
| F1|W5|c0.8|sm0|A2 | per-contract P1 | 0.04 | 0.01 | 0.01 | 0.90 | 0.96 |
| F1|W5|c0.8|sm0|A2 | per-contract P2 | 0.06 | 0.04 | 0.03 | 0.97 | 0.97 |
| F1|W5|c0.8|sm0|A2 | per-contract P3 | 0.25 | 0.18 | 0.18 | 0.79 | 0.77 |
| F1|W5|c0.8|sm0|A2 | stack P1 (40) | 0.00 | 0.03 | 0.03 | 0.62 | 0.70 |
| F1|W5|c0.8|sm0|A2 | stack P3 (40) | 0.00 | 0.00 | 0.00 | 0.80 | 0.80 |

### T5 robustness of carried cells

| cell | affected kept signals | median top-5 depth at fire (contracts) / share < 10 | top-5% share of gain | quarters positive | L6M first half / second half $k/wk | stack corr (weekly, 2024-26) | neighbours mean $k/wk L6M / PRE / X' (diagnostic) | stale feature 10 s: L6M stack, pc | stale 60 s: L6M stack, pc |
|---|---|---|---|---|---|---|---|---|---|
| F1|W30|c0.9|sm0|A4 | 335 | 19 / 0.10 | 1.04 | 10/12 | +2.06 / +0.71 | -0.01 | +0.09 / -0.10 / +0.17 | +0.83 (2.38), +27.8 | +2.36 (2.85), +32.6 |
| F1|W5|c0.8|sm0|A4 | 455 | 19 / 0.10 | 2.66 | 9/12 | +2.29 / -4.23 | 0.01 | +0.30 / -0.01 / +0.14 | +0.54 (2.06), +19.5 | -0.33 (2.31), +2.1 |
| F3a|W30|c0.8 | n/a | nan / nan | nan | 5/12 | -4.46 / -7.88 | -0.16 | -1.19 / -0.17 / +0.23 | -5.86 (7.70), n/a | n/a |
| F3a|W30|c0.9 | n/a | nan / nan | nan | 6/12 | -1.75 / -1.38 | -0.14 | -2.68 / -0.03 / +0.12 | -1.50 (4.89), n/a | n/a |
| F1|W5|c0.8|sm0|A1 | 22 | 16 / 0.09 | 0.90 | 6/10 | +0.00 / -3.83 | -0.07 | +0.08 / +0.05 / +0.07 | -0.03 (0.61), +28.1 | -0.15 (1.73), +6.9 |
| F1|W5|c0.9|sm1|A4 | 68 | 15 / 0.10 | 1.13 | 6/12 | -0.53 / +0.10 | -0.09 | +0.23 / -0.02 / +0.20 | -0.09 (1.08), +10.0 | -0.31 (0.86), -13.0 |
| F1|W5|c0.9|sm0|A1 | 8 | 16 / 0.00 | 0.55 | 4/6 | +0.00 / -0.09 | -0.12 | -0.08 / +0.06 / +0.08 | +0.00 (0.00), n/a | +0.41 (1.10), +30.1 |
| F1|W5|c0.8|sm0|A2 | 22 | 16 / 0.09 | 0.90 | 6/9 | +0.00 / -2.88 | -0.04 | +0.01 / +0.03 / +0.02 | +0.03 (0.13), +28.1 | -0.12 (0.92), +6.9 |

### T6 sessions of the effect (per contract, L6M | PRE | X'; n affected) for the F1 carried cells

| cell | session | L6M | PRE | X' |
|---|---|---|---|---|
| F1|W30|c0.9|sm0|A4 | asia | +29.1 n32 | -0.9 n59 | +19.1 n21 |
| F1|W30|c0.9|sm0|A4 | london | +16.5 n18 | -1.2 n43 | -3.0 n17 |
| F1|W30|c0.9|sm0|A4 | nyam | +10.7 n15 | +19.3 n57 | +18.7 n38 |
| F1|W30|c0.9|sm0|A4 | nypm | +8.9 n4 | -3.1 n11 | -36.9 n9 |
| F1|W5|c0.8|sm0|A4 | asia | -2.7 n32 | +6.8 n80 | +29.3 n16 |
| F1|W5|c0.8|sm0|A4 | london | -5.6 n30 | -13.2 n55 | +42.8 n16 |
| F1|W5|c0.8|sm0|A4 | nyam | +2.9 n27 | +11.6 n91 | +7.7 n61 |
| F1|W5|c0.8|sm0|A4 | nypm | +48.5 n5 | +3.7 n21 | -40.4 n14 |
| F1|W5|c0.8|sm0|A1 | asia | -60.5 n1 | +50.9 n2 | n/a n0 |
| F1|W5|c0.8|sm0|A1 | london | -11.3 n4 | -3.8 n6 | +62.3 n2 |
| F1|W5|c0.8|sm0|A1 | nyam | n/a n0 | +63.3 n4 | +2.0 n3 |
| F1|W5|c0.9|sm1|A4 | asia | -6.3 n9 | +24.3 n14 | -60.0 n1 |
| F1|W5|c0.9|sm1|A4 | london | +19.3 n8 | +14.6 n7 | +50.8 n3 |
| F1|W5|c0.9|sm1|A4 | nyam | -37.7 n5 | +2.0 n11 | +62.4 n2 |
| F1|W5|c0.9|sm1|A4 | nypm | +62.6 n1 | -23.2 n6 | +61.9 n1 |
| F1|W5|c0.9|sm0|A1 | asia | n/a n0 | +61.5 n1 | n/a n0 |
| F1|W5|c0.9|sm0|A1 | london | -61.1 n1 | +35.9 n2 | +62.3 n2 |
| F1|W5|c0.9|sm0|A1 | nyam | n/a n0 | +61.8 n1 | -61.8 n1 |
| F1|W5|c0.8|sm0|A2 | asia | -60.5 n1 | +50.9 n2 | n/a n0 |
| F1|W5|c0.8|sm0|A2 | london | -11.3 n4 | -3.8 n6 | +62.3 n2 |
| F1|W5|c0.8|sm0|A2 | nyam | n/a n0 | +63.3 n4 | +2.0 n3 |

Reading. The footprint state is rare on signals (3-7%) and the books already enter with it: AGAINST rows are 1-6 per window, so skip/halve-AGAINST (A1/A2) cannot be measured (per-contract n 1-12 in every window, MDE 40-120 pts) and the "take only WITH" action A3 deletes 95% of the volume (-22k/wk PRE, all 12 A3 cells). The one sizer with weight is A4 at W30/c0.9: it up-sizes 335 kept signals, but 104% of its gain sits in the top 5% of them, and its P1 (shuffled-minute, carries the session direction in hindsight) rank is 0.16 in PRE. Placebo ranks are on the T4 rows; the per-contract and stack effects are inside the MDE in every window. Sessions (T6): the W30 A4 gain is Asia and London in L6M, NY-AM in PRE and X' - not one place. 1-s and 3-s decision delay change nothing in the state (only completed 10-s buckets are used); the 10-s and 60-s stale-state stress is in T5 (W30 cell stays positive: +0.83k and +2.36k L6M).

### Class tables (kept live signals, per contract, N parity; WITH / NONE / AGAINST = signal side vs footprint sign)
| tag | win | cls | n | pc | mde |
|---|---|---|---|---|---|
| W30c0.9sm0 | L3M | WITH | 33 | 30.4 | 27.1 |
| W30c0.9sm0 | L3M | NONE | 1354 | 4.5 | 7.1 |
| W30c0.9sm0 | L3M | AGAINST | 1 | 60.9 | 0.0 |
| W30c0.9sm0 | L6M | WITH | 68 | 23.3 | 24.4 |
| W30c0.9sm0 | L6M | NONE | 2374 | 6.5 | 5.3 |
| W30c0.9sm0 | L6M | AGAINST | 1 | 60.9 | 0.0 |
| W30c0.9sm0 | HOLD | WITH | 78 | 25.0 | 22.4 |
| W30c0.9sm0 | HOLD | NONE | 2600 | 6.2 | 5.2 |
| W30c0.9sm0 | HOLD | AGAINST | 2 | 60.7 | 0.2 |
| W30c0.9sm0 | PRE | WITH | 170 | 3.3 | 18.0 |
| W30c0.9sm0 | PRE | NONE | 5554 | 4.4 | 3.9 |
| W30c0.9sm0 | PRE | AGAINST | 0 |  |  |
| W30c0.9sm0 | X | WITH | 83 | 10.4 | 26.7 |
| W30c0.9sm0 | X | NONE | 2020 | 2.1 | 5.5 |
| W30c0.9sm0 | X | AGAINST | 2 | -62.0 | 0.9 |
| MOM_W30c0.9sm0 | L3M | WITH | 532 | 8.7 | 10.1 |
| MOM_W30c0.9sm0 | L3M | NONE | 851 | 3.1 | 8.3 |
| MOM_W30c0.9sm0 | L3M | AGAINST | 5 | -58.3 | 11.2 |
| MOM_W30c0.9sm0 | L6M | WITH | 791 | 11.6 | 8.2 |
| MOM_W30c0.9sm0 | L6M | NONE | 1646 | 4.7 | 6.3 |
| MOM_W30c0.9sm0 | L6M | AGAINST | 6 | -59.0 | 9.8 |
| MOM_W30c0.9sm0 | HOLD | WITH | 830 | 10.7 | 8.1 |
| MOM_W30c0.9sm0 | HOLD | NONE | 1844 | 5.0 | 6.2 |
| MOM_W30c0.9sm0 | HOLD | AGAINST | 6 | -59.0 | 9.8 |
| MOM_W30c0.9sm0 | PRE | WITH | 1662 | 2.3 | 6.5 |
| MOM_W30c0.9sm0 | PRE | NONE | 4045 | 5.3 | 4.4 |
| MOM_W30c0.9sm0 | PRE | AGAINST | 17 | 5.9 | 37.1 |
| MOM_W30c0.9sm0 | X | WITH | 147 | -2.6 | 19.5 |
| MOM_W30c0.9sm0 | X | NONE | 1958 | 2.8 | 5.7 |
| MOM_W30c0.9sm0 | X | AGAINST | 0 |  |  |
| W15c0.8sm0 | L3M | WITH | 49 | 1.4 | 27.6 |
| W15c0.8sm0 | L3M | NONE | 1337 | 5.2 | 7.2 |
| W15c0.8sm0 | L3M | AGAINST | 2 | 25.5 | 62.1 |
| W15c0.8sm0 | L6M | WITH | 82 | 6.0 | 24.6 |
| W15c0.8sm0 | L6M | NONE | 2359 | 7.0 | 5.3 |
| W15c0.8sm0 | L6M | AGAINST | 2 | 25.5 | 62.1 |
| W15c0.8sm0 | HOLD | WITH | 96 | 8.4 | 22.7 |
| W15c0.8sm0 | HOLD | NONE | 2581 | 6.7 | 5.2 |
| W15c0.8sm0 | HOLD | AGAINST | 3 | 36.2 | 52.4 |
| W15c0.8sm0 | PRE | WITH | 208 | -0.7 | 16.5 |
| W15c0.8sm0 | PRE | NONE | 5511 | 4.6 | 3.9 |
| W15c0.8sm0 | PRE | AGAINST | 5 | -31.5 | 63.4 |
| W15c0.8sm0 | X | WITH | 93 | -6.2 | 22.9 |
| W15c0.8sm0 | X | NONE | 2006 | 2.7 | 5.6 |
| W15c0.8sm0 | X | AGAINST | 6 | -15.8 | 72.3 |

## 3. Stage A, all 92 cells at PRE and X' only (uncarried cells were never looked at recently)
| fam | cells | PRE_pos | X_pos | both_nonneg |
|---|---|---|---|---|
| F1 | 48 | 16 | 27 | 20 |
| F2 | 32 | 0 | 0 | 0 |
| F3a | 4 | 2 | 4 | 2 |
| F3b | 4 | 0 | 0 | 0 |
| F4 | 4 | 1 | 2 | 0 |

Full per-cell PRE / X' table (stack $k/wk or book $k/wk at 1 contract, MDE in brackets):

| id | PRE $k/wk (MDE) | X' $k/wk (MDE) | carried |
|---|---|---|---|
| F1|W5|c0.8|sm0|A1 | +0.28 (1.34) | +0.18 (0.45) | True |
| F1|W5|c0.8|sm0|A2 | +0.20 (0.76) | +0.06 (0.16) | True |
| F1|W5|c0.8|sm0|A3 | -22.33 (17.54) | -6.31 (13.48) | False |
| F1|W5|c0.8|sm0|A4 | +0.07 (2.06) | +0.81 (1.72) | True |
| F1|W5|c0.8|sm1|A1 | -0.03 (0.92) | +0.03 (0.08) | False |
| F1|W5|c0.8|sm1|A2 | -0.03 (0.49) | +0.00 (0.00) | False |
| F1|W5|c0.8|sm1|A3 | -23.14 (17.79) | -7.68 (13.54) | False |
| F1|W5|c0.8|sm1|A4 | -0.01 (1.37) | +0.19 (0.70) | False |
| F1|W5|c0.9|sm0|A1 | +0.18 (0.59) | +0.09 (0.41) | True |
| F1|W5|c0.9|sm0|A2 | +0.13 (0.28) | +0.03 (0.14) | True |
| F1|W5|c0.9|sm0|A3 | -23.02 (17.41) | -7.05 (13.39) | False |
| F1|W5|c0.9|sm0|A4 | -0.29 (1.50) | +0.51 (1.57) | False |
| F1|W5|c0.9|sm1|A1 | +0.21 (0.51) | +0.00 (0.00) | True |
| F1|W5|c0.9|sm1|A2 | +0.12 (0.28) | +0.00 (0.00) | True |
| F1|W5|c0.9|sm1|A3 | -22.93 (18.01) | -7.71 (13.50) | False |
| F1|W5|c0.9|sm1|A4 | +0.15 (0.71) | +0.19 (0.66) | True |
| F1|W15|c0.8|sm0|A1 | +0.10 (0.29) | +0.09 (0.53) | True |
| F1|W15|c0.8|sm0|A2 | +0.05 (0.14) | +0.04 (0.21) | True |
| F1|W15|c0.8|sm0|A3 | -23.26 (17.40) | -8.27 (14.17) | False |
| F1|W15|c0.8|sm0|A4 | -0.55 (2.10) | -0.23 (1.64) | False |
| F1|W15|c0.8|sm1|A1 | +0.04 (0.22) | +0.14 (0.32) | True |
| F1|W15|c0.8|sm1|A2 | +0.02 (0.10) | +0.07 (0.16) | True |
| F1|W15|c0.8|sm1|A3 | -22.93 (17.87) | -8.08 (13.89) | False |
| F1|W15|c0.8|sm1|A4 | -0.14 (1.49) | -0.02 (0.33) | False |
| F1|W15|c0.9|sm0|A1 | -0.02 (0.05) | +0.14 (0.32) | False |
| F1|W15|c0.9|sm0|A2 | +0.00 (0.00) | +0.07 (0.16) | True |
| F1|W15|c0.9|sm0|A3 | -22.69 (17.51) | -8.05 (14.15) | False |
| F1|W15|c0.9|sm0|A4 | -0.02 (1.47) | -0.13 (1.26) | False |
| F1|W15|c0.9|sm1|A1 | -0.02 (0.05) | +0.14 (0.32) | False |
| F1|W15|c0.9|sm1|A2 | +0.00 (0.00) | +0.07 (0.16) | True |
| F1|W15|c0.9|sm1|A3 | -22.80 (18.05) | -7.99 (13.80) | False |
| F1|W15|c0.9|sm1|A4 | +0.19 (0.84) | +0.04 (0.21) | True |
| F1|W30|c0.8|sm0|A1 | +0.17 (0.68) | -0.09 (0.82) | False |
| F1|W30|c0.8|sm0|A2 | +0.08 (0.32) | -0.09 (0.42) | False |
| F1|W30|c0.8|sm0|A3 | -22.73 (18.24) | -6.24 (14.02) | False |
| F1|W30|c0.8|sm0|A4 | -0.26 (4.09) | +0.56 (2.32) | False |
| F1|W30|c0.8|sm1|A1 | -0.06 (0.18) | +0.06 (0.25) | False |
| F1|W30|c0.8|sm1|A2 | -0.03 (0.09) | +0.03 (0.08) | False |
| F1|W30|c0.8|sm1|A3 | -23.10 (18.15) | -8.01 (13.92) | False |
| F1|W30|c0.8|sm1|A4 | -0.07 (1.43) | +0.00 (0.53) | False |
| F1|W30|c0.9|sm0|A1 | +0.00 (0.00) | +0.11 (0.25) | True |
| F1|W30|c0.9|sm0|A2 | +0.00 (0.00) | +0.03 (0.08) | True |
| F1|W30|c0.9|sm0|A3 | -21.90 (17.86) | -6.49 (13.96) | False |
| F1|W30|c0.9|sm0|A4 | +0.97 (2.26) | +0.50 (1.74) | True |
| F1|W30|c0.9|sm1|A1 | +0.00 (0.00) | +0.08 (0.24) | True |
| F1|W30|c0.9|sm1|A2 | +0.00 (0.00) | +0.03 (0.08) | True |
| F1|W30|c0.9|sm1|A3 | -22.45 (18.14) | -7.92 (13.80) | False |
| F1|W30|c0.9|sm1|A4 | -0.11 (1.21) | -0.03 (0.47) | False |
| F2|W15|c0.8|M|E|S30 | -3.04 (0.97) | -3.84 (1.43) | False |
| F2|W15|c0.8|M|E|S60 | -3.13 (0.98) | -3.75 (1.32) | False |
| F2|W15|c0.8|M|T|S30 | -1.68 (1.80) | -1.08 (1.93) | False |
| F2|W15|c0.8|M|T|S60 | -1.53 (2.24) | -1.55 (1.80) | False |
| F2|W15|c0.8|P|E|S30 | -1.66 (0.39) | -2.04 (0.62) | False |
| F2|W15|c0.8|P|E|S60 | -1.67 (0.40) | -2.01 (0.58) | False |
| F2|W15|c0.8|P|T|S30 | -1.45 (1.21) | -1.60 (1.49) | False |
| F2|W15|c0.8|P|T|S60 | -1.37 (1.42) | -1.69 (1.60) | False |
| F2|W15|c0.9|M|E|S30 | -1.73 (0.75) | -2.40 (0.74) | False |
| F2|W15|c0.9|M|E|S60 | -1.75 (0.75) | -2.36 (0.72) | False |
| F2|W15|c0.9|M|T|S30 | -1.77 (1.60) | -0.87 (1.79) | False |
| F2|W15|c0.9|M|T|S60 | -1.62 (1.57) | -0.77 (1.72) | False |
| F2|W15|c0.9|P|E|S30 | -0.92 (0.29) | -1.24 (0.42) | False |
| F2|W15|c0.9|P|E|S60 | -0.88 (0.29) | -1.20 (0.41) | False |
| F2|W15|c0.9|P|T|S30 | -1.08 (0.96) | -1.17 (0.94) | False |
| F2|W15|c0.9|P|T|S60 | -0.99 (1.05) | -0.94 (1.03) | False |
| F2|W30|c0.8|M|E|S30 | -1.21 (0.85) | -2.40 (1.34) | False |
| F2|W30|c0.8|M|E|S60 | -1.36 (0.87) | -2.37 (1.42) | False |
| F2|W30|c0.8|M|T|S30 | -0.95 (1.21) | -1.66 (1.49) | False |
| F2|W30|c0.8|M|T|S60 | -1.01 (1.40) | -1.37 (1.46) | False |
| F2|W30|c0.8|P|E|S30 | -0.43 (0.37) | -0.79 (0.60) | False |
| F2|W30|c0.8|P|E|S60 | -0.48 (0.39) | -0.79 (0.62) | False |
| F2|W30|c0.8|P|T|S30 | -0.66 (0.89) | -1.26 (1.62) | False |
| F2|W30|c0.8|P|T|S60 | -0.84 (1.04) | -1.30 (1.81) | False |
| F2|W30|c0.9|M|E|S30 | -1.13 (0.60) | -1.53 (0.88) | False |
| F2|W30|c0.9|M|E|S60 | -1.17 (0.62) | -1.46 (0.87) | False |
| F2|W30|c0.9|M|T|S30 | -1.37 (1.01) | -0.78 (1.19) | False |
| F2|W30|c0.9|M|T|S60 | -1.62 (1.19) | -0.48 (1.26) | False |
| F2|W30|c0.9|P|E|S30 | -0.43 (0.24) | -0.40 (0.36) | False |
| F2|W30|c0.9|P|E|S60 | -0.40 (0.25) | -0.39 (0.35) | False |
| F2|W30|c0.9|P|T|S30 | -0.60 (0.71) | -0.11 (0.89) | False |
| F2|W30|c0.9|P|T|S60 | -0.87 (0.83) | -0.13 (0.96) | False |
| F3a|W15|c0.8 | -0.47 (1.94) | +0.14 (1.52) | False |
| F3a|W15|c0.9 | -0.24 (1.63) | +0.17 (1.34) | False |
| F3a|W30|c0.8 | +0.61 (3.03) | +0.06 (2.67) | True |
| F3a|W30|c0.9 | +0.20 (2.79) | +0.38 (1.92) | True |
| F3b|W15|c0.8 | -2.44 (1.22) | -3.99 (2.94) | False |
| F3b|W15|c0.9 | -1.29 (1.02) | -2.60 (2.42) | False |
| F3b|W30|c0.8 | -0.82 (1.16) | -2.23 (1.75) | False |
| F3b|W30|c0.9 | -0.62 (0.91) | -2.05 (1.98) | False |
| F4|C1 | +0.01 (0.60) | -0.36 (0.42) | False |
| F4|C2 | -0.28 (0.60) | +0.03 (0.37) | False |
| F4|C3 | -0.08 (0.65) | -0.34 (0.52) | False |
| F4|C4 | -0.19 (0.65) | +0.02 (0.47) | False |

## 4. Standalone books: "ride the algo" (F2), fade at the end (F3b), MOC (F4)
1 contract, 1-s path, decision delay 1 s, costs market in +0.25, fee 0.242, market out 0.995, stop-fill 1.28 (N) / 2.45 (LIVE-CAL). Pts per trade, weekly $ with MDE, top-5-depth at entry (contracts, median; share < 10 contracts is 4-7%). PRE and X' only (no recent look: none carried).

| id | n | per_wk | pts_N_PRE | pts_L_PRE | pts_N_X | pts_L_X | usd_wk_PRE | mde_PRE | usd_wk_X | mde_X | depth5_median |
|---|---|---|---|---|---|---|---|---|---|---|---|
| F2|W15|c0.8|M|E|S30 | 15837 | 106.29 | -1.58 | -1.61 | -1.50 | -1.51 | -3043.35 | 969.28 | -3840.00 | 1428.17 | 21.00 |
| F2|W15|c0.8|M|E|S60 | 15837 | 106.29 | -1.62 | -1.63 | -1.49 | -1.49 | -3130.07 | 977.64 | -3745.49 | 1316.26 | 21.00 |
| F2|W15|c0.8|M|T|S30 | 9174 | 61.57 | -1.48 | -1.88 | -0.68 | -0.95 | -1676.32 | 1797.08 | -1076.31 | 1931.13 | 21.00 |
| F2|W15|c0.8|M|T|S60 | 8524 | 57.21 | -1.46 | -1.61 | -1.18 | -1.26 | -1525.48 | 2235.90 | -1549.73 | 1797.02 | 21.00 |
| F2|W15|c0.8|P|E|S30 | 8608 | 57.77 | -1.58 | -1.60 | -1.56 | -1.57 | -1662.52 | 390.75 | -2037.12 | 617.72 | 20.00 |
| F2|W15|c0.8|P|E|S60 | 8608 | 57.77 | -1.59 | -1.59 | -1.54 | -1.55 | -1674.97 | 402.85 | -2008.08 | 581.15 | 20.00 |
| F2|W15|c0.8|P|T|S30 | 5979 | 40.13 | -1.96 | -2.34 | -1.68 | -1.95 | -1446.44 | 1209.95 | -1603.80 | 1490.01 | 19.00 |
| F2|W15|c0.8|P|T|S60 | 5706 | 38.30 | -1.96 | -2.09 | -1.85 | -1.93 | -1374.64 | 1421.52 | -1687.86 | 1597.34 | 19.00 |
| F2|W15|c0.9|M|E|S30 | 9979 | 66.97 | -1.42 | -1.44 | -1.54 | -1.55 | -1734.66 | 752.51 | -2395.52 | 736.64 | 21.00 |
| F2|W15|c0.9|M|E|S60 | 9979 | 66.97 | -1.44 | -1.44 | -1.52 | -1.52 | -1750.63 | 754.59 | -2358.13 | 723.11 | 21.00 |
| F2|W15|c0.9|M|T|S30 | 6529 | 43.82 | -2.22 | -2.58 | -0.98 | -1.23 | -1768.02 | 1600.99 | -865.60 | 1788.95 | 21.00 |
| F2|W15|c0.9|M|T|S60 | 6209 | 41.67 | -2.15 | -2.28 | -1.04 | -1.11 | -1621.97 | 1574.16 | -766.14 | 1716.21 | 21.00 |
| F2|W15|c0.9|P|E|S30 | 5166 | 34.67 | -1.44 | -1.45 | -1.58 | -1.59 | -920.44 | 290.69 | -1244.55 | 424.30 | 19.00 |
| F2|W15|c0.9|P|E|S60 | 5165 | 34.66 | -1.37 | -1.37 | -1.54 | -1.55 | -877.01 | 285.31 | -1204.48 | 407.61 | 19.00 |
| F2|W15|c0.9|P|T|S30 | 3956 | 26.55 | -2.19 | -2.54 | -2.05 | -2.32 | -1078.12 | 962.45 | -1170.53 | 938.32 | 19.00 |
| F2|W15|c0.9|P|T|S60 | 3836 | 25.74 | -2.08 | -2.20 | -1.57 | -1.64 | -991.58 | 1047.69 | -935.07 | 1028.76 | 19.00 |
| F2|W30|c0.8|M|E|S30 | 8965 | 60.17 | -1.12 | -1.16 | -1.54 | -1.55 | -1213.48 | 845.76 | -2404.55 | 1335.28 | 21.00 |
| F2|W30|c0.8|M|E|S60 | 8965 | 60.17 | -1.25 | -1.26 | -1.49 | -1.49 | -1359.57 | 874.82 | -2371.13 | 1420.07 | 21.00 |
| F2|W30|c0.8|M|T|S30 | 5812 | 39.01 | -1.34 | -1.72 | -1.65 | -1.92 | -951.11 | 1206.63 | -1662.91 | 1486.14 | 21.00 |
| F2|W30|c0.8|M|T|S60 | 5541 | 37.19 | -1.49 | -1.63 | -1.56 | -1.64 | -1009.74 | 1399.55 | -1370.67 | 1462.77 | 21.00 |
| F2|W30|c0.8|P|E|S30 | 3697 | 24.81 | -0.97 | -0.99 | -1.17 | -1.18 | -426.01 | 371.09 | -785.33 | 598.92 | 20.00 |
| F2|W30|c0.8|P|E|S60 | 3697 | 24.81 | -1.08 | -1.08 | -1.15 | -1.15 | -475.48 | 386.33 | -788.68 | 616.86 | 20.00 |
| F2|W30|c0.8|P|T|S30 | 2941 | 19.74 | -1.86 | -2.21 | -1.94 | -2.20 | -655.37 | 885.61 | -1262.31 | 1619.83 | 20.00 |
| F2|W30|c0.8|P|T|S60 | 2892 | 19.41 | -2.41 | -2.55 | -1.95 | -2.03 | -838.23 | 1043.54 | -1303.11 | 1805.28 | 20.00 |
| F2|W30|c0.9|M|E|S30 | 5822 | 39.07 | -1.57 | -1.60 | -1.52 | -1.53 | -1128.85 | 595.46 | -1526.44 | 879.22 | 21.00 |
| F2|W30|c0.9|M|E|S60 | 5822 | 39.07 | -1.62 | -1.63 | -1.45 | -1.45 | -1166.76 | 615.11 | -1464.11 | 868.47 | 21.00 |
| F2|W30|c0.9|M|T|S30 | 4046 | 27.15 | -2.74 | -3.12 | -1.18 | -1.45 | -1373.01 | 1006.45 | -784.15 | 1185.85 | 21.00 |
| F2|W30|c0.9|M|T|S60 | 3888 | 26.09 | -3.36 | -3.50 | -0.64 | -0.71 | -1615.18 | 1185.50 | -478.67 | 1257.77 | 21.00 |
| F2|W30|c0.9|P|E|S30 | 2223 | 14.92 | -1.56 | -1.59 | -1.09 | -1.09 | -433.37 | 240.54 | -399.77 | 359.59 | 19.00 |
| F2|W30|c0.9|P|E|S60 | 2223 | 14.92 | -1.44 | -1.44 | -1.08 | -1.09 | -399.05 | 253.14 | -388.50 | 350.75 | 19.00 |
| F2|W30|c0.9|P|T|S30 | 1895 | 12.72 | -2.57 | -2.89 | -0.01 | -0.27 | -599.56 | 707.90 | -106.28 | 893.95 | 19.00 |
| F2|W30|c0.9|P|T|S60 | 1869 | 12.54 | -3.77 | -3.90 | -0.13 | -0.20 | -871.39 | 827.09 | -131.86 | 959.85 | 19.00 |
| F3b|W15|c0.8 | 11601 | 77.86 | -1.72 | -1.99 | -1.97 | -2.16 | -2442.81 | 1217.61 | -3988.86 | 2937.24 | 20.00 |
| F3b|W15|c0.9 | 7793 | 52.30 | -1.36 | -1.60 | -1.70 | -1.87 | -1288.04 | 1018.16 | -2602.38 | 2423.42 | 21.00 |
| F3b|W30|c0.8 | 6906 | 46.35 | -0.98 | -1.23 | -1.83 | -2.00 | -820.45 | 1159.98 | -2234.13 | 1748.07 | 21.00 |
| F3b|W30|c0.9 | 4593 | 30.83 | -1.09 | -1.33 | -2.32 | -2.49 | -619.33 | 912.60 | -2052.51 | 1975.18 | 21.00 |
| F4|C1 | 738 | 4.95 | 0.07 | 0.07 | -2.75 | -2.75 | 6.40 | 604.38 | -358.23 | 419.09 | 20.00 |
| F4|C2 | 738 | 4.95 | -3.04 | -3.04 | -0.22 | -0.22 | -281.60 | 604.51 | 31.09 | 367.18 | 21.00 |
| F4|C3 | 739 | 4.96 | -0.91 | -0.91 | -2.55 | -2.55 | -84.52 | 653.44 | -343.91 | 519.62 | 20.00 |
| F4|C4 | 739 | 4.96 | -2.07 | -2.07 | -0.43 | -0.43 | -192.26 | 652.91 | 16.77 | 473.72 | 21.00 |

Purged 6-fold with 1-day (adjacent week) embargo on the PRE u X' span, F2 cell chosen on the training folds, scored on the held-out fold:

| fold | weeks | chosen | train_mean | oos_mean | oos_n |
|---|---|---|---|---|---|
| 0 | 2023-04-03/2023-04-09..2023-08-14/2023-08-20 | F2|W30|c0.8|P|E|S30 | -1.05 | -1.09 | 553 |
| 1 | 2023-08-21/2023-08-27..2024-01-01/2024-01-07 | F2|W30|c0.8|P|E|S30 | -1.01 | -1.31 | 500 |
| 2 | 2024-01-08/2024-01-14..2024-05-20/2024-05-26 | F2|W30|c0.8|P|E|S30 | -1.16 | -0.69 | 591 |
| 3 | 2024-05-27/2024-06-02..2024-10-07/2024-10-13 | F2|W30|c0.9|P|T|S30 | -0.84 | -4.95 | 217 |
| 4 | 2024-10-14/2024-10-20..2025-02-17/2025-02-23 | F2|W15|c0.8|M|T|S60 | -0.99 | -2.22 | 1093 |
| 5 | 2025-02-24/2025-03-02..2025-06-30/2025-07-06 | F2|W15|c0.8|M|T|S30 | -0.96 | -1.92 | 827 |

Every fold's out-of-sample mean is negative (about -1 to -2 pts per trade): the footprint-onset entries lose the round-trip cost and no more. The gross edge before costs is near zero, so exit choice (footprint end, 60-min, stop 30/60) and entry choice (market, pullback to the footprint average) only change how the cost is paid.

## 5. End of the footprint as an exit (F3a)
Trades entered WITH the state exit at market at the first minute the footprint has been off for 2 minutes (add-leg resolved rows only). W30 c0.8 / c0.9 were carried by PRE+X' (+0.6k/+0.2k PRE, +0.06k/+0.38k X'), then fail the recent look: L6M -6.0k (MDE 7.8) and -1.5k (4.9), per contract -22.7 and -15.1. NOW-ONLY fails.

## 6. The 14:40-15:00 skip and the MOC window (descriptive, not cells)
Volume and print rate in 14:40-15:00 are not distinctive (L6M volume per minute 645 vs 647 in the prior block and 640 in the next; the volume spike is 15:40 onward, 1,008 per min). What is distinctive is what follows signals fired there:

| win | block | n_signals | n_live | n_kept | pc_kept | sided_fwd_to_1550 | sided_fwd_to_1600 | se_1600 |
|---|---|---|---|---|---|---|---|---|
| L6M | 12:00-14:40 | 2092 | 216 | 128 | -0.8 | -5.4 | -6.6 | 2.3 |
| L6M | 14:40-15:00 | 224 | 19 | 10 | -0.2 | -21.6 | -23.8 | 5.9 |
| L6M | 15:00-15:50 | 66 | 0 | 0 |  | -23.0 | -26.4 | 8.5 |
| HOLD | 12:00-14:40 | 2292 | 233 | 137 | -0.6 | -5.2 | -5.9 | 2.1 |
| HOLD | 14:40-15:00 | 248 | 23 | 12 | 1.4 | -19.0 | -21.1 | 5.3 |
| HOLD | 15:00-15:50 | 70 | 0 | 0 |  | -21.4 | -25.9 | 8.1 |
| PRE | 12:00-14:40 | 5870 | 602 | 316 | 0.5 | 10.5 | 11.2 | 2.3 |
| PRE | 14:40-15:00 | 631 | 60 | 27 | 19.8 | -13.1 | -14.3 | 3.7 |
| PRE | 15:00-15:50 | 170 | 0 | 0 |  | -20.3 | -17.4 | 8.1 |
| X | 12:00-14:40 | 2593 | 202 | 144 | -0.0 | -0.4 | -4.4 | 1.4 |
| X | 14:40-15:00 | 367 | 32 | 25 | -10.7 | -0.4 | -3.5 | 2.7 |
| X | 15:00-15:50 | 155 | 0 | 0 |  | -1.2 | -1.5 | 3.2 |

Sided forward move (pts, signal direction) from the signal second to 15:50 and 16:00. Signals fired 14:40-15:00 are followed by an adverse drift into the MOC window in L6M, HOLD and PRE (-13 to -24 pts, 2.4-5 SE below zero) and about flat in X'; signals fired 12:00-14:40 are not. Day-level sequences (n days per window 129/150/350/207):

| win | n | corr_r1_r2 | corr_r1_r3 | corr_r0_r3 | corr_flow0_r3 | corr_flow1_r2 | mean_abs_r3 | mean_abs_r1 | mean_abs_r2 | sign_agree_r0_r3 |
|---|---|---|---|---|---|---|---|---|---|---|
| L6M | 129 | -0.058 | 0.149 | 0.015 | 0.068 | -0.142 | 23.847 | 22.083 | 37.603 | 0.496 |
| HOLD | 150 | -0.061 | 0.171 | 0.025 | 0.047 | -0.157 | 22.955 | 22.243 | 34.900 | 0.520 |
| PRE | 350 | -0.113 | 0.058 | -0.037 | -0.013 | -0.116 | 29.804 | 24.299 | 39.924 | 0.457 |
| X | 207 | 0.029 | 0.156 | -0.015 | -0.069 | 0.025 | 15.772 | 17.679 | 24.277 | 0.502 |

14:40-15:00 moves are slightly reversed over 15:00-15:50 (corr -0.06/-0.06/-0.11/+0.03) and flow into 15:00 is negatively related to the 15:00-15:50 move (-0.14/-0.16/-0.12/+0.03), i.e. an exhaustion read; the move continues into the last ten minutes (corr r1,r3 +0.15/+0.17/+0.06/+0.16). The 15:30-15:50 direction has no relation to the 15:50-16:00 move (corr 0.02 / 0.03 / -0.04 / -0.02; sign agreement 46-52%). The four MOC rules therefore have no edge (F4 table above). So the skip is explained by the signals' own adverse afternoon drift (a late-session reversal), not by a detectable MOC imbalance proxy; the NYSE imbalance feed itself is not on disk, so a true imbalance-direction test is open. The live consequence in the NY-PM note stands: only K6 (2 lots) and A6 (1) trade there, and for them the skip was a small negative.

## 7. Information (IC) at 1 / 5 / 30 min, minute grid RTH, day-clustered; D = descriptive
| feat | H | HOLD | L6M | PRE | X |
|---|---|---|---|---|---|
| net15 | 1 | 0.0014 | 0.0036 | 0.0000 | 0.0014 |
| net15 | 5 | 0.0065 | 0.0089 | -0.0002 | 0.0095 |
| net15 | 30 | -0.0183 | -0.0208 | 0.0006 | 0.0014 |
| netxagree15 | 1 | 0.0016 | 0.0039 | 0.0000 | 0.0013 |
| netxagree15 | 5 | 0.0079 | 0.0105 | -0.0002 | 0.0098 |
| netxagree15 | 30 | -0.0184 | -0.0204 | 0.0007 | 0.0024 |
| ret15(control) | 1 | 0.0051 | 0.0084 | 0.0027 | -0.0026 |
| ret15(control) | 5 | 0.0105 | 0.0147 | 0.0031 | 0.0011 |
| ret15(control) | 30 | -0.0070 | -0.0069 | 0.0161 | -0.0056 |

t-stats of net15 vs its placebos (real, 60-s older, shuffled days):

| feat | H | HOLD | L6M | PRE | X |
|---|---|---|---|---|---|
| net15 | 1 | 0.3 | 0.8 | 0.0 | 0.4 |
| net15 | 5 | 0.8 | 1.0 | -0.0 | 1.4 |
| net15 | 30 | -1.3 | -1.4 | 0.1 | 0.1 |
| net15(60s older) | 1 |  | 1.6 | 0.9 | 1.7 |
| net15(60s older) | 5 |  | 1.4 | 0.2 | 1.6 |
| net15(60s older) | 30 |  | -1.3 | 0.1 | 0.1 |

## 8. Tiers with failed gates, persistence, shrunk size
See T3. One cell is STRICT (F1 W30 c0.9 sm0 A4: positive in every window, stack and per contract) and fails the literal TOLERANT only on clause 3 (PRE worst-20 weeks -904k vs the stack's -875k; the cell is a size-up and its L6M maxDD is 106k vs 95k). TOL-B and TOL-nc (post-hoc, clause 5 loosened / dropped) also fail, for the same reason. Tier label for the ledger: NOW-ONLY (inside MDE), placebo-mixed -> CANDIDATE-RECENT at best, no forward-register row (no TOLERANT pass). Persistence 0.50 (t(6m)=1.52, family base), shrunk size 0 (the RE-1 kept share for entry-filter/sizing rules is ~0).

## 9. Caveats
(1) Only completed 10-s buckets enter the state; 1-s/3-s delay is therefore a fill question, not a state question. (2) F3a modifies rows whose add leg is resolved at the exit second; rows with an unresolved add are left unchanged. (3) P1 shuffles 1-min blocks within day x session and keeps the session's direction in hindsight, so it is a harsh null; P2/P3 are the causal nulls. (4) During testing one whole-sample sum of 8 F1 stack deltas was printed (disclosed in DECISIONS.md). (5) Neighbour means (T5) use recent windows of uncarried cells as a diagnostic, not a selection. (6) The IC table and the class tables are descriptive looks at all windows.
