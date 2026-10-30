# DS3_CONFIRM_COMBOS — T-CONFIRM-LAYER COMBINATIONS (CF-COMBO)
Prereg l2vast/ds3/prereg/CF_COMBO_prereg.md (sha256 508571c1...69be7, in DECISIONS.md). Code l2vast/ds3/code/confirm/combo/, outputs l2vast/ds3/out/confirm/combo/. Masks capped 20260206, UNTOUCHED never read; selection PRE+X' only; one recent look per stage/book; per contract = net pts per contract of final position (o0/lots); floor = plain 70/30 3-pt dip. 'add on fired' = paired gain vs the floor on the signals the combination fires on; 'ALL-signal add' = the same over every signal with skipped signals keeping their floor P&L only if not gated (i.e. skipped signals count as 0 for the gated rule and as their floor P&L in the comparison). Tier gates use the ALL-signal add (stricter and economically honest): the pure-wait (F=0) variants look like +20 pts per contract on the fired signals but that is a subset-selection effect (the floor loses ~-25 per contract on exactly those signals, the combination itself earns ~-1.5 absolute).
Caveats logged in DECISIONS.md: metric corrected from per-planned-lot to per-contract after the stage1B KB look (same selected cells re-scored, no new selection); planned-lot numbers in earlier lines are artefacts.

## Stage stage1B  (2026-10-30T17:11Z)

CF-B level items (OTE / Fib / P-D / pivots / prior / round / OR on 14 TFs), top-50 by the CF-B PRE+X' ranking; level-confluence (within 1 pt) pairs/triples; a level member supplies the limit level, non-level members gate the touch.

### KB: 2365 combinations x 17 variants = 40205 cells; PRE+X' selection, one recent look on the top 13 cells (50 cell x variant rows)
White RC over the stage's cells (PRE+X', all-signal differential vs floor): p=0.972 (K=7238). Tiers: BEST-AVAILABLE 38, DEAD 12.

| AND-set (timeframes in the member names) | variant | fill L6M | n | add vs floor on fired L6M [per contract] | HOLD | L3M | PRE | X' | ALL-signal add L6M | best member (all-signal) L6M | placebo p | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AND(pd50|2m+pd50|3m) | c1|F0.0 | 14.2% | 178 | +24.29 (MDE 4.37) | +24.51 | +25.80 | +23.77 | +18.73 | -0.55 | -0.09 | 0.005 | DEAD | L6M<0,HOLD<0,<=best_member_L6M |
| AND(pd50|2m+pd50|3m) | a|F0.0 | 14.2% | 178 | +24.29 (MDE 4.37) | +24.50 | +25.80 | +23.75 | +18.72 | -0.55 | -0.00 | 0.005 | DEAD | L6M<0,HOLD<0,<=best_member_L6M |
| AND(pd50|2m+pd50|3m) | b_near|F0.0 | 14.2% | 178 | +23.85 (MDE 4.90) | +24.27 | +24.92 | +24.19 | +19.12 | -0.61 | -0.15 | 0.005 | DEAD | L6M<0,HOLD<0,<=best_member_L6M |
| AND(pd50|2m+pd50|3m) | c2_near|F0.0 | 14.2% | 178 | +23.85 (MDE 4.90) | +24.28 | +24.92 | +24.19 | +19.12 | -0.61 | -0.24 | 0.005 | DEAD | L6M<0,HOLD<0,<=best_member_L6M |
| AND(ote79|45s+ote79|1m) | c2_near|F0.0 | 17.7% | 222 | +21.52 (MDE 5.43) | +21.62 | +24.18 | +22.66 | +18.57 | +0.43 | +0.34 | 0.005 | BEST-AVAILABLE | <=best_member_PRE+X |
| AND(ote79|45s+ote79|1m) | b_near|F0.0 | 17.7% | 222 | +21.51 (MDE 5.42) | +21.62 | +24.17 | +22.59 | +18.48 | +0.43 | +0.34 | 0.005 | BEST-AVAILABLE | <=best_member_PRE+X |
| AND(ote79|45s+ote79|1m) | c1|F0.0 | 17.7% | 222 | +20.64 (MDE 5.32) | +20.81 | +23.31 | +22.70 | +18.44 | +0.27 | +0.33 | 0.060 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(ote79|45s+ote79|1m) | a|F0.0 | 17.7% | 222 | +20.63 (MDE 5.32) | +20.81 | +23.30 | +22.65 | +18.44 | +0.27 | +0.33 | 0.055 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(pd50|1m+pd50|45s) | c1|F0.0 | 25.9% | 325 | +20.05 (MDE 5.24) | +19.77 | +25.16 | +17.12 | +15.09 | +0.07 | +0.30 | 0.005 | BEST-AVAILABLE | <=best_member_L6M,<=best_member_PRE+X |
| AND(pd50|1m+pd50|45s) | a|F0.0 | 25.9% | 325 | +20.02 (MDE 5.25) | +19.67 | +25.12 | +17.08 | +15.00 | +0.07 | +0.28 | 0.005 | BEST-AVAILABLE | <=best_member_L6M,<=best_member_PRE+X |
| AND(ote62|1m+ote62|45s) | c2_near|F0.0 | 22.8% | 286 | +19.87 (MDE 3.62) | +20.19 | +23.26 | +19.79 | +17.23 | +0.28 | +0.35 | 0.005 | BEST-AVAILABLE | <=best_member_L6M,<=best_member_PRE+X |
| AND(ote62|1m+ote62|45s) | b_near|F0.0 | 22.8% | 286 | +19.86 (MDE 3.62) | +20.18 | +23.26 | +19.74 | +17.11 | +0.28 | +0.34 | 0.005 | BEST-AVAILABLE | <=best_member_L6M,<=best_member_PRE+X |

Plain sentence (best by all-signal gain): requiring ote705|45s AND ote705|1m before the signal enters (c2_near|F0.0) adds +19.79 pts per contract on the 20.4% of signals it fires on in the last 6 months (MDE 4.73), but +0.56 pts per signal over ALL signals (the skipped signals' floor P&L counted against it) vs the best member +0.55; tier BEST-AVAILABLE.


## Stage stage1ENG  (2026-10-30T19:56Z)

CF-ENG engine streams (FVG/iFVG/implied FVG/OB/breaker x 14 TF), top-50 distinct (family, TF) by the CF-ENG PRE+X' ranking; AND / ORDERED (top-20, 60/300/900 s) / triples (top-20) / k-of-n (top-10). Placebo = state-preserving random times, 60 draws (engine-domain), 200 (level cells); metric = all-signal gain.

### KB: 3525 combinations x 17 variants = 59925 cells; PRE+X' selection, one recent look on the top 28 cells (50 cell x variant rows)
White RC over the stage's cells (PRE+X', all-signal differential vs floor): p=0.178 (K=59435). Tiers: BEST-AVAILABLE 40, CANDIDATE 10.

| AND-set (timeframes in the member names) | variant | fill L6M | n | add vs floor on fired L6M [per contract] | HOLD | L3M | PRE | X' | ALL-signal add L6M | best member (all-signal) L6M | placebo p | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| THEN60s(FVG|15s+OB|45s) | c2_far|F0.7 | 43.3% | 544 | +6.51 (MDE 1.44) | +6.45 | +7.34 | +6.22 | +5.37 | +2.33 | +2.61 | 0.525 | BEST-AVAILABLE | placebo,<=best_member_L6M |
| THEN60s(iFVG|15s+FVG|2m) | c2_mid|F0.7 | 46.3% | 582 | +6.35 (MDE 2.01) | +6.15 | +7.94 | +6.75 | +5.45 | +2.48 | +2.19 | 0.115 | BEST-AVAILABLE | placebo |
| THEN60s(iFVG|30s+FVG|2m) | c2_mid|F0.7 | 40.4% | 508 | +6.26 (MDE 2.39) | +6.23 | +7.67 | +7.40 | +6.13 | +2.01 | +2.01 | 0.967 | BEST-AVAILABLE | placebo |
| THEN60s(FVG|15s+FVG|2m) | c2_mid|F0.7 | 48.8% | 614 | +6.02 (MDE 1.87) | +5.99 | +7.08 | +6.58 | +4.99 | +2.51 | +2.05 | 0.148 | BEST-AVAILABLE | placebo |
| THEN60s(iFVG|15s+FVG|2m) | c2_far|F0.7 | 41.8% | 526 | +5.78 (MDE 1.76) | +5.89 | +7.40 | +7.39 | +6.07 | +1.92 | +2.50 | 1.000 | BEST-AVAILABLE | placebo,<=best_member_L6M |
| THEN60s(iFVG|15s+FVG|2m) | b_mid|F0.7 | 46.9% | 590 | +5.76 (MDE 1.54) | +5.53 | +7.23 | +6.53 | +5.23 | +2.23 | +1.92 | 0.016 | CANDIDATE |  |
| THEN60s(FVG|15s+FVG|2m) | b_mid|F0.7 | 49.1% | 617 | +5.71 (MDE 1.74) | +5.74 | +6.78 | +6.38 | +4.70 | +2.36 | +1.92 | 0.016 | CANDIDATE |  |
| THEN60s(iplFVG|30s+FVG|2m) | c2_mid|F0.7 | 49.7% | 625 | +5.64 (MDE 1.68) | +5.69 | +6.42 | +6.18 | +5.26 | +2.36 | +2.01 | 0.754 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|45s+FVG|2m) | c2_mid|F0.7 | 46.5% | 584 | +5.59 (MDE 1.85) | +5.50 | +6.34 | +5.88 | +5.08 | +2.13 | +2.01 | 0.918 | BEST-AVAILABLE | placebo |
| THEN60s(iFVG|15s+FVG|2m) | b_far|F0.7 | 41.7% | 524 | +5.59 (MDE 1.76) | +5.46 | +7.12 | +7.08 | +5.95 | +1.83 | +1.90 | 0.230 | BEST-AVAILABLE | placebo,<=best_member_L6M |
| THEN60s(FVG|15s+FVG|2m) | c2_far|F0.7 | 44.6% | 560 | +5.57 (MDE 1.58) | +5.80 | +6.57 | +6.70 | +5.93 | +2.01 | +2.61 | 0.918 | BEST-AVAILABLE | placebo,<=best_member_L6M |
| THEN60s(iplFVG|30s+FVG|2m) | b_mid|F0.7 | 50.0% | 629 | +5.53 (MDE 1.75) | +5.55 | +6.44 | +6.11 | +5.22 | +2.32 | +1.92 | 0.016 | CANDIDATE |  |

Plain sentence (best by all-signal gain): requiring THEN60s(iplFVG|45s AND iFVG|15s before the signal enters (c2_far|F0.7) adds +5.06 pts per contract on the 64.7% of signals it fires on in the last 6 months (MDE 1.76), but +3.04 pts per signal over ALL signals (the skipped signals' floor P&L counted against it) vs the best member +2.50; tier CANDIDATE.

