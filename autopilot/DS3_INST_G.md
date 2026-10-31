DATA: on disk and derived, nothing to buy. NQ mbp-10 1-s aggregates (add/cancel counts and sizes by level group, Cont OFI L1 and L1-5, depletions, top-10 sizes; first ~75 min of the 11 defective months masked) plus the de-duplicated trade tape (aggressor side, pre-trade BBO and size); built VPIN-50 (50-contract buckets), cancel ratio, normalised multi-level OFI, trade-to-book, hidden-liquidity rate (out/inst/G/). Not on disk: raw MBO (true spoofing/lifetimes; quote ~$953, NO purchase). Stop-placement depth is outside the displayed book (stop 60 pts away vs ~2-3 pts of 10 levels): not testable, reported as stop-hit prediction instead.

# DS3_INST_G - order-flow toxicity as a sizer (INST-2, section G of T-INSTITUTIONAL)

Research only, nothing promoted. Prereg l2vast/ds3/prereg/INST_G_prereg.md sha256 0fa1d8b78926b2f3811c2baf9a0c8e6e4b947d9db7c2ae1a8835caa2d9d32d3e (36 cells; thresholds sha256 4945d4ca...a533); PRE+X' selection out/inst/G/selection_PRE_X.json sha256 02e2bebcdcf45a3ad4ac5db3b5171a8cdccd880d60b5670bcba50a8f42c4a1a5 logged before the recent look; ONE recent look at the 6 carried cells. Engine ONE-CONVENTION; sizers via the engine multiplier (mer_fn, feeds the running-max SizeMult), skips via zone_override. Code l2vast/ds3/code/inst/G/, rows out/recent_wins/inst_G.csv.

## Page 1

**Plain sentence.** Order-flow toxicity predicts how far the market moves next (rank IC +0.25 to +0.45 against the absolute 1-30 min move for trade-to-book and OFI magnitude, +0.1 for the cancel ratio (-0.15 for its size version), +0.04 to +0.09 for the hidden rate, about 0 for VPIN; day-clustered t above 3 for all but VPIN; the volume-based ones are mostly activity) but not whether OUR signals win (signal-level IC against the sided forward move at 1/5/30 min is within +-0.04 with |t| below 3 in all but isolated cells, and the stop-hit IC is within +-0.08); as a sizer (toxic tape x0.5 or skipped, quiet tape x1.5) the 36 registered cells give: halving or skipping the toxic tape (volume-type features O, T) loses 2-11k/wk in PRE because toxic tape is where the books earn; 6 cells pass PRE and X' (cancel ratio, hidden rate, OFI-against), and every one of them fails the recent look in L3M (best, cancel ratio q0.9 half/1.5x: +0.46k/wk L3M with MDE 4.2k and -1.5 pts per contract), so STRICT 0, TOLERANT (literal) 0, NOW-ONLY 0, TOL-B and TOL-nc (post-hoc, beside) 0; nothing promoted.

| item | result |
|---|---|
| cells / carried by PRE+X' | 36 / 6 |
| STRICT / TOLERANT (literal) / NOW-ONLY | 0 / 0 / 0 |
| beside (post-hoc, never called TOLERANT): TOL-B / TOL-nc | 0 / 0 |
| best carried cell G|C|q0.9|S3 stack $k/wk (MDE) L3M / L6M / HOLD / PRE / X' | +0.46 (4.21) / +1.10 (3.84) / +1.51 (3.95) / +1.98 (5.85) / +3.19 (5.35); per contract L3M -1.5 |
| stop placement at high cancel ratio | not testable on mbp-10; cancel/hidden/OFI predict the stop being hit with IC within +-0.08 |

## 1. Stage A (all 36 cells at PRE and X' only), then the carried cells
### T1 stack delta vs the as-is composite, $k/wk (MDE in brackets, * beyond MDE)

| cell | conv | L3M | L6M | HOLD | PRE | X' | 2026 |
|---|---|---|---|---|---|---|---|
| G|C|q0.9|S3 | no lock | +0.46 (4.21) | +1.10 (3.84) | +1.51 (3.95) | +1.98 (5.85) | +3.19 (5.35) | +3.74 (8.28) |
| G|C|q0.9|S3 | 12R lock | -1.77 (3.66) | +4.51 (12.40) | +3.94 (10.91) | +2.30 (6.65) | +0.03 (6.30) | -0.39 (6.33) |
| G|C|q0.9|S3 | LIVE-CAL | +0.27 (4.32) | +1.01 (3.86) | +1.42 (3.97) | +1.86 (5.94) | +3.08 (5.36) | +3.71 (8.28) |
| G|C|q0.8|S3 | no lock | -3.11 (13.49) | -2.67 (9.72) | -0.44 (9.57) | +0.41 (7.07) | +2.34 (6.19) | -3.94 (20.12) |
| G|C|q0.8|S3 | 12R lock | -15.34 (22.02) | -5.39 (19.61) | -4.28 (17.48) | +1.95 (6.41) | +2.17 (7.28) | -8.43 (17.32) |
| G|C|q0.8|S3 | LIVE-CAL | -3.12 (13.52) | -2.14 (9.33) | +0.02 (9.23) | +0.54 (7.06) | +2.13 (6.19) | -4.02 (20.16) |
| G|H|q0.8|S3 | no lock | -2.49 (15.17) | -0.02 (9.43) | -1.30 (8.89) | +0.52 (8.73) | +1.63 (6.65) | -0.16 (27.25) |
| G|H|q0.8|S3 | 12R lock | -3.59 (18.80) | +3.69 (16.26) | +2.15 (14.69) | +0.48 (9.92) | -3.95 (8.10) | +3.67 (23.31) |
| G|H|q0.8|S3 | LIVE-CAL | -2.89 (15.26) | -0.25 (9.48) | -1.45 (8.93) | +0.43 (8.76) | +1.58 (6.67) | -0.98 (27.70) |
| G|H|q0.9|S3 | no lock | -2.09 (18.16) | +1.66 (9.89) | +0.76 (8.78) | +0.60 (8.34) | +0.77 (6.26) | +1.47 (25.75) |
| G|H|q0.9|S3 | 12R lock | -4.34 (23.59) | +2.99 (17.75) | +0.80 (16.23) | -1.12 (10.46) | -2.77 (7.81) | +7.91 (18.80) |
| G|H|q0.9|S3 | LIVE-CAL | -3.81 (19.21) | +0.80 (10.47) | +0.06 (9.25) | +0.53 (8.26) | +0.74 (6.27) | -2.11 (30.30) |
| G|Oa|q0.8|S3 | no lock | -4.03 (16.72) | -1.71 (10.28) | -1.09 (9.25) | +1.27 (5.84) | +0.07 (4.83) | -9.33 (19.05) |
| G|Oa|q0.8|S3 | 12R lock | -3.21 (23.33) | -0.24 (12.38) | +0.21 (11.02) | -2.71 (7.53) | -0.64 (5.07) | -0.15 (7.82) |
| G|Oa|q0.8|S3 | LIVE-CAL | -4.88 (17.39) | -2.15 (10.57) | -1.78 (9.56) | +0.99 (6.29) | +0.04 (4.84) | -11.05 (21.67) |
| G|Oa|q0.9|S1 | no lock | -1.42 (9.54) | -1.72 (6.16) | -1.43 (5.41) | +0.02 (4.33) | +0.31 (1.55) | +0.11 (9.86) |
| G|Oa|q0.9|S1 | 12R lock | -2.40 (16.42) | -1.53 (8.89) | -1.47 (7.75) | -1.77 (7.60) | +0.32 (0.95) | +2.06 (5.42) |
| G|Oa|q0.9|S1 | LIVE-CAL | -1.48 (9.53) | -1.75 (6.16) | -1.45 (5.41) | -0.46 (4.02) | +0.31 (1.55) | +0.00 (9.93) |

### T2 per contract of the lots added/removed (pts, + good; MDE; n)

| cell | conv | L3M | L6M | HOLD | PRE | X' | 2026 |
|---|---|---|---|---|---|---|---|
| G|C|q0.9|S3 | N parity | -1.5 (30.5) n66 | +1.8 (20.3) n167 | +3.0 (18.4) n198 | -0.8 (8.4) n1216 | +4.3 (9.5) n703 | +4.0 (44.4) n28 |
| G|C|q0.9|S3 | LIVE-CAL | -1.3 (30.6) n65 | +1.9 (20.4) n166 | +3.0 (18.4) n197 | -0.7 (8.4) n1215 | +4.2 (9.5) n703 | +3.9 (44.5) n28 |
| G|C|q0.8|S3 | N parity | +0.2 (10.6) n374 | -0.1 (9.4) n714 | +1.7 (8.8) n803 | -0.3 (5.7) n2404 | +2.8 (7.5) n1123 | -3.2 (13.2) n150 |
| G|C|q0.8|S3 | LIVE-CAL | +0.3 (10.6) n373 | -0.1 (9.4) n713 | +1.8 (8.9) n802 | -0.2 (5.7) n2401 | +2.6 (7.5) n1123 | -3.2 (13.2) n150 |
| G|H|q0.8|S3 | N parity | +2.9 (9.4) n711 | +3.2 (6.6) n1218 | +1.6 (6.4) n1338 | -1.0 (4.2) n3068 | +2.7 (7.6) n1119 | +1.3 (16.6) n261 |
| G|H|q0.8|S3 | LIVE-CAL | +2.6 (9.5) n709 | +3.0 (6.7) n1216 | +1.5 (6.4) n1336 | -1.0 (4.3) n3069 | +2.6 (7.6) n1119 | +0.5 (17.0) n260 |
| G|H|q0.9|S3 | N parity | +4.4 (11.7) n478 | +5.6 (8.1) n832 | +4.0 (7.7) n917 | +0.9 (5.2) n2092 | +1.6 (9.1) n771 | +3.5 (19.1) n177 |
| G|H|q0.9|S3 | LIVE-CAL | +4.3 (11.7) n478 | +5.5 (8.1) n832 | +3.9 (7.7) n917 | +0.8 (5.2) n2092 | +1.5 (9.1) n771 | +3.4 (19.1) n177 |
| G|Oa|q0.8|S3 | N parity | +2.5 (12.9) n216 | +2.6 (11.1) n373 | +2.1 (10.3) n413 | +2.9 (7.1) n841 | +3.6 (12.1) n347 | +6.7 (25.3) n83 |
| G|Oa|q0.8|S3 | LIVE-CAL | +2.6 (13.0) n216 | +2.7 (11.2) n373 | +2.1 (10.4) n413 | +2.8 (7.1) n843 | +3.5 (12.1) n347 | +6.7 (25.4) n83 |
| G|Oa|q0.9|S1 | N parity | +0.7 (20.5) n80 | -2.6 (17.3) n123 | -0.8 (17.1) n128 | +3.2 (12.7) n200 | +0.8 (36.1) n27 | +28.6 (39.5) n23 |
| G|Oa|q0.9|S1 | LIVE-CAL | +0.9 (20.5) n80 | -2.4 (17.3) n123 | -0.7 (17.2) n128 | +3.5 (12.8) n200 | +0.9 (36.2) n27 | +28.5 (39.5) n23 |

### T3 tiers and risk

| cell | STRICT | TOLERANT (headline, literal) | NOW-ONLY | TOL-B (post-hoc) | TOL-nc (post-hoc) | failed gates | L6M maxDD rule/as-is | PRE worst-20 rule/as-is | t(6m) | persistence | shrunk $k/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G|C|q0.9|S3 | no | NO | no | no | no | NOW(L3M/L6M stack+pc>0) | 95/95 | -914/-875 | 0.81 | 0.51 | 0.00 |
| G|C|q0.8|S3 | no | NO | no | no | no | NOW(L3M/L6M stack+pc>0) | 95/95 | -940/-875 | -0.77 | 0.51 | 0.00 |
| G|H|q0.8|S3 | no | NO | no | no | no | NOW(L3M/L6M stack+pc>0) | 88/95 | -895/-875 | -0.01 | 0.51 | 0.00 |
| G|H|q0.9|S3 | no | NO | no | no | no | NOW(L3M/L6M stack+pc>0) | 117/95 | -937/-875 | 0.47 | 0.51 | 0.00 |
| G|Oa|q0.8|S3 | no | NO | no | no | no | NOW(L3M/L6M stack+pc>0) | 92/95 | -905/-875 | -0.47 | 0.51 | 0.00 |
| G|Oa|q0.9|S1 | no | NO | no | no | no | NOW(L3M/L6M stack+pc>0) | 95/95 | -851/-875 | -0.78 | 0.51 | 0.00 |

### T4 placebo ranks (per-contract, 200 draws: G1 features from another label day, G2 random sizer same factor; stack 40 draws)

| cell | kind | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| G|C|q0.9|S3 | per-contract G1 | 0.69 | 0.73 | 0.77 | 0.85 | 0.68 |
| G|C|q0.9|S3 | stack G1 | 0.80 | 0.85 | 0.80 | 1.00 | 1.00 |
| G|C|q0.9|S3 | per-contract G2 | 0.28 | 0.60 | 0.74 | 0.28 | 0.88 |
| G|C|q0.9|S3 | stack G2 | 0.82 | 0.88 | 0.85 | 0.95 | 1.00 |
| G|C|q0.8|S3 | per-contract G1 | 0.82 | 0.83 | 0.91 | 0.89 | 0.47 |
| G|C|q0.8|S3 | stack G1 | 0.80 | 0.72 | 0.85 | 0.93 | 0.90 |
| G|C|q0.8|S3 | per-contract G2 | 0.45 | 0.41 | 0.72 | 0.41 | 0.85 |
| G|C|q0.8|S3 | stack G2 | 0.78 | 0.55 | 0.72 | 0.80 | 1.00 |
| G|H|q0.8|S3 | per-contract G1 | 0.61 | 0.50 | 0.37 | 0.21 | 0.75 |
| G|H|q0.8|S3 | stack G1 | 0.45 | 0.45 | 0.28 | 0.70 | 0.85 |
| G|H|q0.8|S3 | per-contract G2 | 0.82 | 0.92 | 0.69 | 0.19 | 0.93 |
| G|H|q0.8|S3 | stack G2 | 0.75 | 0.78 | 0.57 | 0.82 | 0.93 |
| G|H|q0.9|S3 | per-contract G1 | 0.65 | 0.62 | 0.52 | 0.54 | 0.57 |
| G|H|q0.9|S3 | stack G1 | 0.55 | 0.60 | 0.45 | 0.65 | 0.72 |
| G|H|q0.9|S3 | per-contract G2 | 0.80 | 0.87 | 0.72 | 0.52 | 0.68 |
| G|H|q0.9|S3 | stack G2 | 0.75 | 0.90 | 0.68 | 0.62 | 0.85 |
| G|Oa|q0.8|S3 | per-contract G1 | 0.75 | 0.74 | 0.71 | 0.99 | 0.93 |
| G|Oa|q0.8|S3 | stack G1 | 0.70 | 0.57 | 0.62 | 0.85 | 0.80 |
| G|Oa|q0.8|S3 | per-contract G2 | 0.61 | 0.67 | 0.64 | 0.72 | 0.79 |
| G|Oa|q0.8|S3 | stack G2 | 0.57 | 0.53 | 0.55 | 0.80 | 0.70 |
| G|Oa|q0.9|S1 | per-contract G1 | 0.79 | 0.79 | 0.89 | 1.00 | 0.71 |
| G|Oa|q0.9|S1 | stack G1 | 0.97 | 0.88 | 0.88 | 0.85 | 0.95 |
| G|Oa|q0.9|S1 | per-contract G2 | 0.65 | 0.66 | 0.79 | 0.91 | 0.64 |
| G|Oa|q0.9|S1 | stack G2 | 0.60 | 0.60 | 0.53 | 0.65 | 0.70 |

### T5 robustness

| cell | affected kept | up-sized rows: median top-5 depth / share < 10 | top-5% share | quarters + | L6M halves $k/wk | stack corr | neighbours (same feature+action) L6M/PRE/X' | stale 10 s L6M stack, pc | stale 60 s |
|---|---|---|---|---|---|---|---|---|---|
| G|C|q0.9|S3 | 2117 | 20 / 0.12 | 7.82 | 9/12 | +1.80/+0.47 | 0.03 | -2.67/+0.41/+2.34 | +0.49 (3.97), +1.4 | +0.04 (3.44), -1.7 |
| G|C|q0.8|S3 | 4330 | 19 / 0.16 | 11.15 | 7/12 | -2.54/-2.96 | -0.10 | +1.10/+1.98/+3.19 | -2.94 (9.73), +1.1 | -4.09 (11.15), -3.0 |
| G|H|q0.8|S3 | 5525 | 15 / 0.15 | 24.49 | 3/12 | +2.64/-2.69 | -0.14 | +1.66/+0.60/+0.77 | +0.07 (9.67), +3.2 | -3.61 (9.33), +1.4 |
| G|H|q0.9|S3 | 3780 | 14 / 0.17 | 5.22 | 9/12 | +5.57/-2.16 | -0.02 | -0.02/+0.52/+1.63 | +1.51 (9.58), +5.2 | -0.57 (7.83), +3.8 |
| G|Oa|q0.8|S3 | 1601 | 19 / 0.09 | 2.71 | 6/12 | +0.17/-3.69 | -0.03 | -2.03/+0.43/-0.18 | -3.75 (10.37), -4.3 | -2.03 (10.99), +0.9 |
| G|Oa|q0.9|S1 | 355 | nan / 0.00 | 4.35 | 7/12 | -1.91/-1.64 | -0.19 | -2.59/+0.17/-0.15 | -2.69 (6.78), -3.8 | -2.64 (8.40), -1.6 |

### T6 all 36 cells at PRE and X' (stack $k/wk, MDE; only the carried cells were looked at recently)

| cell | n toxic rows | PRE | X' | carried |
|---|---|---|---|---|
| G|V|q0.8|S1 | 16336 | -1.68 (5.95) | -0.35 (4.67) | no |
| G|V|q0.8|S2 | 16336 | -4.39 (9.92) | -1.35 (9.69) | no |
| G|V|q0.8|S3 | 16336 | -0.90 (6.81) | +0.35 (5.73) | no |
| G|V|q0.9|S1 | 8803 | -0.83 (4.11) | -2.14 (3.84) | no |
| G|V|q0.9|S2 | 8803 | -4.31 (6.70) | -3.62 (7.62) | no |
| G|V|q0.9|S3 | 8803 | -2.93 (5.10) | -1.12 (4.13) | no |
| G|C|q0.8|S1 | 12425 | -0.07 (5.05) | +0.04 (0.86) | no |
| G|C|q0.8|S2 | 12425 | -1.53 (8.46) | +0.02 (1.39) | no |
| G|C|q0.8|S3 | 12425 | +0.41 (7.07) | +2.34 (6.19) | yes |
| G|C|q0.9|S1 | 5511 | -0.08 (3.57) | +0.12 (0.49) | no |
| G|C|q0.9|S2 | 5511 | -1.07 (6.12) | +0.16 (0.88) | no |
| G|C|q0.9|S3 | 5511 | +1.98 (5.85) | +3.19 (5.35) | yes |
| G|O|q0.8|S1 | 24307 | -6.73 (7.01) | -1.54 (4.05) | no |
| G|O|q0.8|S2 | 24307 | -11.34 (11.27) | -2.44 (8.56) | no |
| G|O|q0.8|S3 | 24307 | -4.86 (7.79) | -0.99 (6.46) | no |
| G|O|q0.9|S1 | 15393 | -4.78 (6.28) | +0.86 (2.81) | no |
| G|O|q0.9|S2 | 15393 | -7.54 (9.48) | +1.68 (5.93) | no |
| G|O|q0.9|S3 | 15393 | -4.26 (6.88) | +0.54 (4.52) | no |
| G|Oa|q0.8|S1 | 3937 | +0.17 (4.92) | -0.15 (1.76) | no |
| G|Oa|q0.8|S2 | 3937 | +0.26 (6.41) | -0.67 (2.90) | no |
| G|Oa|q0.8|S3 | 3937 | +1.27 (5.84) | +0.07 (4.83) | yes |
| G|Oa|q0.9|S1 | 2417 | +0.02 (4.33) | +0.31 (1.55) | yes |
| G|Oa|q0.9|S2 | 2417 | -0.06 (5.31) | +0.07 (2.09) | no |
| G|Oa|q0.9|S3 | 2417 | +0.43 (4.97) | -0.18 (3.51) | no |
| G|T|q0.8|S1 | 23488 | -6.28 (7.33) | -0.88 (3.99) | no |
| G|T|q0.8|S2 | 23488 | -10.03 (11.95) | -0.03 (8.04) | no |
| G|T|q0.8|S3 | 23488 | -5.34 (7.98) | -1.55 (4.94) | no |
| G|T|q0.9|S1 | 14263 | -2.81 (6.07) | +0.24 (2.75) | no |
| G|T|q0.9|S2 | 14263 | -5.58 (10.33) | +1.15 (5.02) | no |
| G|T|q0.9|S3 | 14263 | -2.50 (6.46) | -0.74 (3.92) | no |
| G|H|q0.8|S1 | 14435 | -0.39 (6.33) | +0.24 (4.02) | no |
| G|H|q0.8|S2 | 14435 | -6.46 (11.26) | +1.11 (8.25) | no |
| G|H|q0.8|S3 | 14435 | +0.52 (8.73) | +1.63 (6.65) | yes |
| G|H|q0.9|S1 | 7082 | +0.27 (5.04) | -0.95 (3.72) | no |
| G|H|q0.9|S2 | 7082 | -2.46 (8.21) | -1.31 (7.10) | no |
| G|H|q0.9|S3 | 7082 | +0.60 (8.34) | +0.77 (6.26) | yes |

Reading. The V (VPIN) cells are negative in both PRE and X' for every action. The O (|OFI|) and T (trade-to-book) cells that skip or halve toxic tape are the largest losers because 40% of live signals fire on toxic tape (n toxic rows 15-24k of 61k) and the books' P&L is concentrated in high-activity minutes. The carried cells are the ones that touch little (cancel ratio, hidden rate) or only the against-OFI subset; sizing up the quiet 10-20% is the whole of their effect and is inside the MDE.

## 2. Information coefficient per feature, 1 / 5 / 30 min
Minute grid (RTH), feature vs the ABSOLUTE forward move (volatility), real series:

| feat | H | HOLD | L6M | PRE | X |
|---|---|---|---|---|---|
| cr5 | 1 | 0.102 | 0.092 | 0.167 | 0.031 |
| cr5 | 5 | 0.112 | 0.103 | 0.170 | 0.027 |
| cr5 | 30 | 0.127 | 0.112 | 0.169 | 0.057 |
| cr5sz | 1 | -0.127 | -0.160 | -0.216 | 0.122 |
| cr5sz | 5 | -0.116 | -0.149 | -0.213 | 0.122 |
| cr5sz | 30 | -0.113 | -0.148 | -0.200 | 0.129 |
| hid15 | 1 | 0.080 | 0.085 | 0.043 | 0.077 |
| hid15 | 5 | 0.070 | 0.075 | 0.039 | 0.080 |
| hid15 | 30 | 0.056 | 0.062 | 0.023 | 0.064 |
| ofi1abs | 1 | 0.255 | 0.258 | 0.228 | 0.153 |
| ofi1abs | 5 | 0.264 | 0.264 | 0.230 | 0.146 |
| ofi1abs | 30 | 0.245 | 0.246 | 0.213 | 0.135 |
| ofi5abs | 1 | 0.270 | 0.270 | 0.214 | 0.155 |
| ofi5abs | 5 | 0.276 | 0.274 | 0.215 | 0.147 |
| ofi5abs | 30 | 0.259 | 0.258 | 0.208 | 0.133 |
| t2b5 | 1 | 0.446 | 0.451 | 0.392 | 0.313 |
| t2b5 | 5 | 0.443 | 0.449 | 0.385 | 0.302 |
| t2b5 | 30 | 0.418 | 0.422 | 0.360 | 0.274 |
| vpin50 | 1 | 0.023 | 0.011 | -0.019 | 0.028 |
| vpin50 | 5 | 0.015 | 0.003 | -0.028 | 0.025 |
| vpin50 | 30 | -0.004 | -0.012 | -0.029 | 0.012 |

Signal level, feature vs the sided forward move of each live signal (Spearman IC; the t-stats, day-clustered, are in out/inst/G/ic.csv; |t| > 2.5 only for: cancel ratio X' 5 min t 2.8; hid15 PRE 1-5 min t 2.6/3.1 in one window with opposite sign in X'):

| feat | H | HOLD | L6M | PRE | X |
|---|---|---|---|---|---|
| cr5 | 1 | 0.018 | 0.009 | 0.010 | 0.019 |
| cr5 | 5 | 0.008 | 0.004 | -0.004 | 0.043 |
| cr5 | 30 | 0.015 | 0.013 | -0.020 | 0.013 |
| cr5sz | 1 | 0.011 | 0.008 | 0.014 | -0.007 |
| cr5sz | 5 | 0.011 | 0.016 | 0.018 | 0.016 |
| cr5sz | 30 | 0.026 | 0.028 | 0.022 | 0.047 |
| hid15 | 1 | -0.004 | 0.000 | 0.026 | -0.021 |
| hid15 | 5 | -0.009 | -0.008 | 0.032 | -0.021 |
| hid15 | 30 | -0.005 | -0.001 | 0.017 | -0.008 |
| ofi1abs | 1 | -0.031 | -0.028 | 0.006 | -0.017 |
| ofi1abs | 5 | -0.025 | -0.020 | 0.009 | 0.006 |
| ofi1abs | 30 | -0.000 | 0.008 | 0.007 | -0.005 |
| ofi5_signed_vs_side | 1 | -0.004 | 0.004 | 0.002 | -0.041 |
| ofi5_signed_vs_side | 5 | -0.018 | -0.013 | -0.000 | -0.010 |
| ofi5_signed_vs_side | 30 | 0.026 | 0.032 | 0.016 | -0.006 |
| ofi5abs | 1 | -0.010 | -0.004 | 0.002 | -0.024 |
| ofi5abs | 5 | -0.011 | -0.006 | 0.015 | -0.009 |
| ofi5abs | 30 | 0.020 | 0.031 | 0.016 | -0.014 |
| t2b5 | 1 | -0.005 | -0.001 | 0.006 | -0.017 |
| t2b5 | 5 | -0.002 | 0.001 | 0.020 | -0.013 |
| t2b5 | 30 | 0.004 | 0.014 | 0.035 | -0.007 |
| vpin50 | 1 | -0.005 | -0.001 | -0.008 | 0.007 |
| vpin50 | 5 | -0.026 | -0.019 | -0.021 | -0.039 |
| vpin50 | 30 | -0.028 | -0.022 | 0.004 | 0.022 |

Stop-hit prediction (signal level, IC with the stop indicator):

| feat | HOLD | L6M | PRE | X |
|---|---|---|---|---|
| cr5 | 0.010 | -0.003 | 0.025 | 0.020 |
| cr5sz | -0.023 | -0.015 | -0.000 | -0.026 |
| hid15 | -0.013 | -0.004 | -0.037 | -0.079 |
| ofi1abs | 0.015 | 0.023 | -0.028 | -0.046 |
| ofi5abs | 0.003 | 0.006 | -0.023 | -0.031 |
| t2b5 | -0.007 | 0.003 | -0.047 | -0.093 |
| vpin50 | -0.021 | -0.014 | -0.044 | -0.038 |

Placebo reads (ic.csv, source '60s older') match the real series to within 0.01 in IC for all features, i.e. the vol-type IC is persistent activity, not information at the second.

## 3. Capacity, latency, regimes
T5: the up-sized rows (quiet tape) have median top-5 same-side depth 14-20 contracts at the fire seconds with 9-17% of them below 10 contracts. Latency: features are frozen at the completed 10-s bucket; the 10-s and 60-s stale stress is in T5. Session and book splits are in out/inst/G/extras.pkl (by_sess, by_book).

## 4. Tiers
All six carried cells fail NOW-ONLY (L3M stack and per contract not both positive); gates listed in T3. Nothing is promoted; no forward-register row (no literal TOLERANT pass). Ledger tier DEAD for 36/36 (the six carried cells are DEAD on the recent look, the other thirty never reached it).

## 5. Caveats
Cancel ratio from mbp-10 counts is a net-of-modify aggregate, not order-level (true spoof/layering needs MBO). Hidden-liquidity rate is tiny (0.4% of volume) and noisy. VPIN uses true aggressor sides (not BVC). The volume-type IC is dominated by contemporaneous activity.
