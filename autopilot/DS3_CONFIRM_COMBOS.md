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


#### stage1ENG KB: quant-layer on the CANDIDATE rows (diagnostics on the same selected cells; no new selection)

Plain sentence for the top candidate: requiring a 15-s iFVG THEN a 2-m FVG within 60 s before the KB signal enters (remainder rested as a limit at the FVG CE, 70/30 base) adds +2.23 pts per contract over ALL KB signals in the last 6 months (CI day-block (1.47, 2.98), week-block (1.7, 2.74)); on the 47% of signals it fires on it adds +5.76 (MDE 1.54); the best single member in the same variant adds +1.92, i.e. the combination adds only +0.31 over its best member (not significant); most of the gain is the single-FVG resting-limit structure (STRUCTURE: 70/30 + limit), not information.

| cell | tier | ALL-signal add L6M | CI day (L6M) | NW t (weekly) | DSR | RW survives (selected, L6M) | PBO (stage) | + quarters | halves | M / N / +1tick / +1pt-cost | breakeven cost pts/fill | top-5% share |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| THEN60s(iFVG|15s+FVG|2m) b_mid|F0.7 | CANDIDATE | +2.23 | (+1.47,+2.98) | 10.3 | 0.37 | True (p 0.002) | 0.64 | 12/12 | +2.12/+2.29 | +2.23 / +4.37 / +2.14 / +2.05 | 12.4 | 0.82 |
| THEN60s(FVG|15s+FVG|2m) b_mid|F0.7 | CANDIDATE | +2.36 | (+1.68,+3.01) | 11.8 | 0.79 | True (p 0.002) | 0.64 | 12/12 | +1.94/+2.51 | +2.36 / +4.51 / +2.27 / +2.18 | 12.7 | 0.72 |
| THEN60s(iplFVG|30s+FVG|2m) b_mid|F0.7 | CANDIDATE | +2.32 | (+1.64,+2.98) | 12.2 | 0.76 | True (p 0.002) | 0.64 | 12/12 | +1.97/+2.29 | +2.32 / +4.47 / +2.13 / +2.13 | 12.3 | 0.73 |
| THEN60s(FVG|15s+FVG|2m) c2_near|F0.7 | CANDIDATE | +2.62 | (+1.88,+3.33) | 10.4 | 0.65 | True (p 0.002) | 0.64 | 12/12 | +1.85/+2.50 | +2.62 / +4.77 / +2.59 / +2.41 | 12.6 | 0.68 |
| THEN60s(iplFVG|45s+iFVG|15s) c2_far|F0.7 | CANDIDATE | +3.04 | (+2.35,+3.71) | 14.9 | 0.94 | True (p 0.002) | 0.64 | 12/12 | +1.99/+3.09 | +3.04 / +5.20 / +2.93 / +2.80 | 12.6 | 0.62 |
| THEN60s(iplFVG|1m+iFVG|15s) c2_far|F0.7 | CANDIDATE | +2.77 | (+2.06,+3.44) | 14.1 | 0.91 | True (p 0.002) | 0.64 | 12/12 | +1.90/+3.02 | +2.77 / +4.92 / +2.66 / +2.54 | 12.1 | 0.63 |
| THEN60s(iplFVG|30s+iFVG|15s) c2_far|F0.7 | CANDIDATE | +2.96 | (+2.38,+3.62) | 12.0 | 0.97 | True (p 0.002) | 0.64 | 12/12 | +1.78/+3.23 | +2.96 / +5.13 / +2.85 / +2.72 | 12.0 | 0.58 |
| THEN60s(iFVG|15s+FVG|15s) c2_far|F0.7 | CANDIDATE | +2.87 | (+2.22,+3.52) | 11.4 | 0.94 | True (p 0.002) | 0.64 | 12/12 | +2.10/+2.96 | +2.87 / +5.03 / +2.86 / +2.62 | 11.8 | 0.60 |
| THEN60s(iplFVG|45s+iFVG|15s) c2_mid|F0.7 | CANDIDATE | +2.82 | (+2.22,+3.41) | 15.4 | 0.91 | True (p 0.002) | 0.64 | 12/12 | +2.01/+2.65 | +2.82 / +4.98 / +2.81 / +2.58 | 11.6 | 0.61 |
| THEN300s(iplFVG|45s+iFVG|15s) c2_far|F0.7 | CANDIDATE | +2.87 | (+2.17,+3.55) | 13.8 | 0.88 | True (p 0.002) | 0.64 | 12/12 | +1.81/+2.97 | +2.87 / +5.02 / +2.76 / +2.61 | 11.2 | 0.61 |

Reading: positive in all quarters 2023-2026 and RW-survives inside the selected set, but DSR with the cumulative trial count (2038519 cells across programs) is < 0.95, PBO among the selected rows is 0.64 (near-duplicates: iFVG/FVG/iplFVG 15-45 s then FVG 2 m), the stage-level White RC on PRE+X' is p=0.178, and no row beats its best member by more than ~0.3 pts. Tier: CANDIDATE-RECENT, not PASS. Not run (need engine or depth support): 1 s / 3 s latency, capacity at book depth, lock-engine stack $/wk, stack correlation; simpler-rule distillation = the best member itself. Placebo ranks: 60 state-preserving random-time draws for engine cells (rank resolution 1/61), 200 for level cells; stage1B placebos used the superseded fired-subset gain.

#### stage1ENG KB: UNIT CHECK of every CANDIDATE-RECENT row (lead request): three units + random-level placebo + STRUCTURE label

Units: per contract of final position (the primary), per planned lot, and lock-engine stack $/wk (KB gated by the combination, other books at the floor; difference vs the plain-dip floor stack, L6M and HOLD). Random-level placebo = cf_engine.placebo_level_ov (same placement times, level distance drawn from the real distance distribution), 200 draws, rank of the real per-contract all-signal gain. 'excess' = combination minus its better member in the same variant (paired, week-block 95% CI).

| cell | per contract L6M | per planned lot L6M | stack $/wk L6M | stack $/wk HOLD | random-level placebo: real rank / placebo mean (max) | best member pc | excess over member [CI] | label |
|---|---|---|---|---|---|---|---|---|
| THEN60s(iFVG|15s+FVG|2m) b_mid|F0.7 | +2.23 | +0.65 | +363 | +664 | 36/201 / +2.04 (+2.46) | +1.92 (FVG|2m) | +0.31 [-0.23,+0.83] | STRUCTURE: random levels at the same distances earn +2.04 of the +2.23; combination excess over member not significant |
| THEN60s(FVG|15s+FVG|2m) b_mid|F0.7 | +2.36 | +0.43 | -1039 | -958 | 5/201 / +2.01 (+2.41) | +1.92 (FVG|2m) | +0.44 [+0.21,+0.69] | STRUCTURE: random levels at the same distances earn +2.01 of the +2.36; combination excess over member significant but small; STACK NEGATIVE -> not a candidate on the stack unit |
| THEN60s(iplFVG|30s+FVG|2m) b_mid|F0.7 | +2.32 | +0.92 | +377 | -488 | 4/201 / +1.97 (+2.37) | +1.92 (FVG|2m) | +0.40 [+0.15,+0.66] | STRUCTURE: random levels at the same distances earn +1.97 of the +2.32; combination excess over member significant but small; STACK NEGATIVE -> not a candidate on the stack unit |
| THEN60s(FVG|15s+FVG|2m) c2_near|F0.7 | +2.62 | +0.45 | +1559 | +1337 | 5/201 / +2.17 (+2.72) | +2.01 (FVG|2m) | +0.61 [+0.23,+0.94] | STRUCTURE: random levels at the same distances earn +2.17 of the +2.62; combination excess over member significant but small |
| THEN60s(iplFVG|45s+iFVG|15s) c2_far|F0.7 | +3.04 | +0.41 | +666 | +501 | 8/201 / +2.58 (+3.10) | +2.50 (iFVG|15s) | +0.53 [+0.26,+0.84] | STRUCTURE: random levels at the same distances earn +2.58 of the +3.04; combination excess over member significant but small |
| THEN60s(iplFVG|1m+iFVG|15s) c2_far|F0.7 | +2.77 | +0.23 | +822 | +798 | 3/201 / +2.29 (+2.88) | +2.50 (iFVG|15s) | +0.26 [-0.25,+0.81] | STRUCTURE: random levels at the same distances earn +2.29 of the +2.77; combination excess over member not significant |
| THEN60s(iplFVG|30s+iFVG|15s) c2_far|F0.7 | +2.96 | +0.53 | +951 | +726 | 6/201 / +2.59 (+3.17) | +2.50 (iFVG|15s) | +0.46 [+0.21,+0.72] | STRUCTURE: random levels at the same distances earn +2.59 of the +2.96; combination excess over member significant but small |
| THEN60s(iFVG|15s+FVG|15s) c2_far|F0.7 | +2.87 | +0.35 | +2288 | +2035 | 5/201 / +2.41 (+2.97) | +2.61 (FVG|15s) | +0.26 [+0.11,+0.41] | STRUCTURE: random levels at the same distances earn +2.41 of the +2.87; combination excess over member significant but small |
| THEN60s(iplFVG|45s+iFVG|15s) c2_mid|F0.7 | +2.82 | +0.27 | -1054 | -1428 | 13/201 / +2.51 (+3.06) | +2.19 (iFVG|15s) | +0.63 [+0.33,+0.94] | STRUCTURE: random levels at the same distances earn +2.51 of the +2.82; combination excess over member significant but small; STACK NEGATIVE -> not a candidate on the stack unit |
| THEN300s(iplFVG|45s+iFVG|15s) c2_far|F0.7 | +2.87 | +0.29 | +1417 | +1010 | 6/201 / +2.46 (+3.07) | +2.50 (iFVG|15s) | +0.36 [+0.17,+0.59] | STRUCTURE: random levels at the same distances earn +2.46 of the +2.87; combination excess over member significant but small |

Reading: the units disagree in size (planned-lot gain is 0.2-0.9 against 2.2-3.0 per contract) and two rows flip sign on the lock-engine stack, so per-contract alone overstates; the gain is dominated by the resting-limit/split STRUCTURE (a random-level limit at the same distance earns ~2.0-2.6 per contract; the real combination clears the 95th placebo percentile in 8 of 10 rows but by 0.2-0.6 pts). Honest tier: STRUCTURE-dominated; at best CANDIDATE-RECENT with a +0.2..+0.6 pts information excess, not PASS. Program-level (50 selected rows, qv.program_validity, week periods, cumulative trials): RC p, PBO below.

qv header (one row per candidate; promote_ok False when any column is missing; capacity, breakeven_slip, neighbourhood_mean, regime, stack_corr are not computed here):

| cell | pts_per_contract | ci_lo | ci_hi | L3M | L6M | HOLD | PRE | Xp | trades_per_week | fire_rate | n_cells | rc_p_program | rw_survives | dsr | pbo | placebo_rank | neighbourhood_mean | breakeven_slip | capacity_contracts | top5_share | stack_corr | regime | drift_sign_count | plain_sentence | promote_ok |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| THEN60s(iFVG|15s+FVG|2m) | b_mid|F0.7 | KB | 2.234 | 1.697 | 2.738 | 2.777 | 2.234 | 2.160 | 2.711 | 2.181 | 44.893 | 0.469 | 2038519 | 0.000 | Y | 1.000 | 0.226 | 36/201 | None | None | None | 0.827 | None | None | 12/12 | THEN60s(iFVG|15s+FVG|2m) then b_mid|F0.7 adds +2.23 pts/contract (all KB signals, L6M) | False |
| THEN60s(FVG|15s+FVG|2m) | b_mid|F0.7 | KB | 2.362 | 1.718 | 3.107 | 2.728 | 2.362 | 2.418 | 2.748 | 2.019 | 44.893 | 0.491 | 2038519 | 0.000 | Y | 1.000 | 0.226 | 5/201 | None | None | None | 0.721 | None | None | 12/12 | THEN60s(FVG|15s+FVG|2m) then b_mid|F0.7 adds +2.36 pts/contract (all KB signals, L6M) | False |
| THEN60s(iplFVG|30s+FVG|2m) | b_mid|F0.7 | KB | 2.320 | 1.664 | 3.107 | 2.629 | 2.320 | 2.377 | 2.672 | 2.243 | 44.893 | 0.500 | 2038519 | 0.000 | Y | 1.000 | 0.226 | 4/201 | None | None | None | 0.730 | None | None | 12/12 | THEN60s(iplFVG|30s+FVG|2m) then b_mid|F0.7 adds +2.32 pts/contract (all KB signals, L6M) | False |
| THEN60s(FVG|15s+FVG|2m) | c2_near|F0.7 | KB | 2.620 | 1.943 | 3.278 | 3.020 | 2.620 | 2.608 | 2.641 | 1.999 | 44.893 | 0.547 | 2038519 | 0.000 | Y | 1.000 | 0.226 | 5/201 | None | None | None | 0.682 | None | None | 12/12 | THEN60s(FVG|15s+FVG|2m) then c2_near|F0.7 adds +2.62 pts/contract (all KB signals, L6M) | False |
| THEN60s(iplFVG|45s+iFVG|15s) | c2_far|F0.7 | KB | 3.037 | 2.296 | 3.855 | 3.492 | 3.037 | 3.073 | 2.886 | 2.020 | 44.893 | 0.647 | 2038519 | 0.000 | Y | 1.000 | 0.226 | 8/201 | None | None | None | 0.620 | None | None | 12/12 | THEN60s(iplFVG|45s+iFVG|15s) then c2_far|F0.7 adds +3.04 pts/contract (all KB signals, L6M) | False |
| THEN60s(iplFVG|1m+iFVG|15s) | c2_far|F0.7 | KB | 2.767 | 1.941 | 3.657 | 3.105 | 2.767 | 2.877 | 2.717 | 1.941 | 44.893 | 0.617 | 2038519 | 0.000 | Y | 1.000 | 0.226 | 3/201 | None | None | None | 0.632 | None | None | 12/12 | THEN60s(iplFVG|1m+iFVG|15s) then c2_far|F0.7 adds +2.77 pts/contract (all KB signals, L6M) | False |
| THEN60s(iplFVG|30s+iFVG|15s) | c2_far|F0.7 | KB | 2.964 | 2.413 | 3.564 | 3.474 | 2.964 | 3.019 | 2.951 | 1.953 | 44.893 | 0.667 | 2038519 | 0.000 | Y | 1.000 | 0.226 | 6/201 | None | None | None | 0.579 | None | None | 12/12 | THEN60s(iplFVG|30s+iFVG|15s) then c2_far|F0.7 adds +2.96 pts/contract (all KB signals, L6M) | False |
| THEN60s(iFVG|15s+FVG|15s) | c2_far|F0.7 | KB | 2.867 | 2.293 | 3.474 | 3.150 | 2.867 | 2.844 | 2.975 | 1.879 | 44.893 | 0.656 | 2038519 | 0.000 | Y | 1.000 | 0.226 | 5/201 | None | None | None | 0.600 | None | None | 12/12 | THEN60s(iFVG|15s+FVG|15s) then c2_far|F0.7 adds +2.87 pts/contract (all KB signals, L6M) | False |
| THEN60s(iplFVG|45s+iFVG|15s) | c2_mid|F0.7 | KB | 2.822 | 2.216 | 3.453 | 3.246 | 2.822 | 2.771 | 2.703 | 2.057 | 44.893 | 0.658 | 2038519 | 0.000 | Y | 1.000 | 0.226 | 13/201 | None | None | None | 0.618 | None | None | 12/12 | THEN60s(iplFVG|45s+iFVG|15s) then c2_mid|F0.7 adds +2.82 pts/contract (all KB signals, L6M) | False |
| THEN300s(iplFVG|45s+iFVG|15s) | c2_far|F0.7 | KB | 2.866 | 2.146 | 3.644 | 3.372 | 2.866 | 2.903 | 2.828 | 1.794 | 44.893 | 0.704 | 2038519 | 0.000 | Y | 1.000 | 0.226 | 6/201 | None | None | None | 0.611 | None | None | 12/12 | THEN300s(iplFVG|45s+iFVG|15s) then c2_far|F0.7 adds +2.87 pts/contract (all KB signals, L6M) | False |

## Stage stage1ENG  (2026-10-30T20:55Z)

auto

### PE: 3525 combinations x 17 variants = 59925 cells; PRE+X' selection, one recent look on the top 18 cells (30 cell x variant rows)
White RC over the stage's cells (PRE+X', all-signal differential vs floor): p=0.002 (K=59625). Tiers: BEST-AVAILABLE 23, CANDIDATE 7.

| AND-set (timeframes in the member names) | variant | fill L6M | n | add vs floor on fired L6M [per contract] | HOLD | L3M | PRE | X' | ALL-signal add L6M | best member (all-signal) L6M | placebo p | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| THEN60s(FVG|15s+FVG|10m) | c2_mid|F0.7 | 39.1% | 467 | +7.53 (MDE 2.09) | +7.54 | +7.00 | +9.18 | +7.40 | +2.13 | +2.21 | 0.984 | BEST-AVAILABLE | placebo,<=best_member_L6M |
| THEN60s(iplFVG|30s+FVG|10m) | c2_mid|F0.7 | 37.5% | 448 | +7.39 (MDE 2.16) | +7.46 | +7.26 | +9.32 | +7.31 | +1.95 | +2.65 | 1.000 | BEST-AVAILABLE | placebo,<=best_member_L6M |
| THEN60s(FVG|15s+FVG|10m) | b_mid|F0.7 | 39.7% | 474 | +7.24 (MDE 2.08) | +7.10 | +6.81 | +8.65 | +6.88 | +2.05 | +1.05 | 0.590 | BEST-AVAILABLE | placebo |
| THEN60s(iFVG|30s+OB|1m) | c2_far|F0.7 | 49.8% | 595 | +7.19 (MDE 1.94) | +6.98 | +7.72 | +7.09 | +5.97 | +3.07 | +2.50 | 0.033 | CANDIDATE |  |
| THEN60s(iplFVG|30s+OB|1m) | b_far|F0.7 | 50.8% | 606 | +7.08 (MDE 1.70) | +6.75 | +7.05 | +7.38 | +5.65 | +2.96 | +2.29 | 0.016 | CANDIDATE |  |
| THEN60s(iplFVG|30s+OB|1m) | c2_far|F0.7 | 51.3% | 612 | +7.04 (MDE 1.77) | +6.84 | +7.16 | +7.80 | +6.20 | +3.01 | +2.50 | 0.197 | BEST-AVAILABLE | placebo |
| THEN60s(FVG|15s+OB|1m) | c2_far|F0.7 | 54.4% | 650 | +7.03 (MDE 1.65) | +6.81 | +7.70 | +7.02 | +5.15 | +3.34 | +2.82 | 0.016 | CANDIDATE |  |
| THEN300s(iplFVG|30s+FVG|10m) | c2_mid|F0.7 | 38.3% | 457 | +7.01 (MDE 2.18) | +7.14 | +6.79 | +8.88 | +7.07 | +1.86 | +2.65 | 1.000 | BEST-AVAILABLE | placebo,<=best_member_L6M |
| THEN300s(FVG|15s+FVG|10m) | c2_mid|F0.7 | 39.0% | 466 | +6.98 (MDE 1.95) | +6.94 | +6.49 | +8.63 | +7.01 | +1.81 | +2.21 | 1.000 | BEST-AVAILABLE | placebo,<=best_member_L6M |
| THEN300s(iFVG|30s+OB|1m) | c2_far|F0.7 | 51.1% | 610 | +6.97 (MDE 1.80) | +6.70 | +7.91 | +6.70 | +5.59 | +2.96 | +2.50 | 0.590 | BEST-AVAILABLE | placebo |
| THEN300s(iplFVG|30s+OB|1m) | c2_far|F0.7 | 52.5% | 627 | +6.82 (MDE 1.75) | +6.62 | +7.40 | +7.26 | +5.71 | +3.08 | +2.50 | 0.541 | BEST-AVAILABLE | placebo |
| THEN60s(iFVG|30s+FVG|2m) | c2_far|F0.7 | 47.9% | 572 | +6.35 (MDE 1.82) | +6.34 | +6.24 | +7.79 | +6.00 | +2.48 | +1.81 | 0.951 | BEST-AVAILABLE | placebo |

Plain sentence (best by all-signal gain): requiring iplFVG|30s THEN FVG|15s within 60 s before the signal enters (c2_far|F0.7) adds +5.10 pts per contract on the 73.2% of signals it fires on in the last 6 months (MDE 1.78), but +3.58 pts per signal over ALL signals (the skipped signals' floor P&L counted against it) vs the best member +2.82; tier CANDIDATE.


## Stage stage1ENG  (2026-10-30T21:32Z)

auto

### ST: 3525 combinations x 17 variants = 59925 cells; PRE+X' selection, one recent look on the top 15 cells (30 cell x variant rows)
White RC over the stage's cells (PRE+X', all-signal differential vs floor): p=0.008 (K=59685). Tiers: BEST-AVAILABLE 19, CANDIDATE 11.

| AND-set (timeframes in the member names) | variant | fill L6M | n | add vs floor on fired L6M [per contract] | HOLD | L3M | PRE | X' | ALL-signal add L6M | best member (all-signal) L6M | placebo p | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| THEN60s(iplFVG|15s+OB|1m) | c2_far|F0.7 | 39.9% | 501 | +6.85 (MDE 2.16) | +6.96 | +8.85 | +7.90 | +7.22 | +2.15 | +1.65 | 0.820 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|15s+OB|1m) | b_far|F0.7 | 40.3% | 506 | +6.11 (MDE 2.12) | +6.25 | +7.52 | +7.75 | +6.88 | +1.79 | +0.99 | 0.131 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|15s+OB|30s) | c2_far|F0.7 | 50.1% | 629 | +6.01 (MDE 1.49) | +5.93 | +6.92 | +6.82 | +6.41 | +2.60 | +1.98 | 0.016 | CANDIDATE |  |
| THEN60s(iplFVG|45s+OB|30s) | c2_far|F0.7 | 48.1% | 604 | +5.91 (MDE 1.78) | +5.86 | +6.60 | +6.38 | +6.20 | +2.22 | +1.98 | 0.328 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|30s+OB|30s) | c2_far|F0.7 | 47.8% | 600 | +5.71 (MDE 1.64) | +5.82 | +6.33 | +6.79 | +6.34 | +2.30 | +2.00 | 0.066 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|15s+OB|30s) | b_far|F0.7 | 49.8% | 625 | +5.67 (MDE 1.47) | +5.55 | +6.40 | +6.51 | +6.09 | +2.41 | +1.66 | 0.016 | CANDIDATE |  |
| THEN60s(iplFVG|15s+OB|30s) | c2_mid|F0.7 | 54.8% | 688 | +5.50 (MDE 1.52) | +5.43 | +5.63 | +5.95 | +5.11 | +2.74 | +2.01 | 0.016 | CANDIDATE |  |
| THEN60s(iplFVG|15s+OB|30s) | b_mid|F0.7 | 54.6% | 686 | +5.44 (MDE 1.49) | +5.27 | +5.67 | +5.64 | +4.76 | +2.68 | +1.74 | 0.016 | CANDIDATE |  |
| THEN60s(iplFVG|30s+OB|1m) | c2_mid|F0.7 | 44.3% | 556 | +5.41 (MDE 2.31) | +5.37 | +6.03 | +7.01 | +5.52 | +1.93 | +1.56 | 0.902 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|30s+OB|30s) | b_far|F0.7 | 46.8% | 588 | +5.38 (MDE 1.60) | +5.47 | +6.00 | +6.19 | +6.32 | +2.08 | +1.66 | 0.016 | CANDIDATE |  |
| THEN300s(iplFVG|45s+OB|30s) | c2_far|F0.7 | 51.4% | 645 | +5.37 (MDE 1.61) | +5.35 | +6.36 | +5.95 | +5.70 | +2.16 | +1.98 | 0.836 | BEST-AVAILABLE | placebo |
| THEN300s(iplFVG|15s+OB|30s) | c2_far|F0.7 | 52.1% | 655 | +5.37 (MDE 1.47) | +5.30 | +6.39 | +5.84 | +5.89 | +2.30 | +1.98 | 0.607 | BEST-AVAILABLE | placebo |

Plain sentence (best by all-signal gain): requiring iplFVG|15s THEN OB|30s within 60 s before the signal enters (c2_mid|F0.7) adds +5.50 pts per contract on the 54.8% of signals it fires on in the last 6 months (MDE 1.52), but +2.74 pts per signal over ALL signals (the skipped signals' floor P&L counted against it) vs the best member +2.01; tier CANDIDATE.


## Stage stage1ENG  (2026-10-30T22:04Z)

auto

### HM: 3525 combinations x 17 variants = 59925 cells; PRE+X' selection, one recent look on the top 21 cells (30 cell x variant rows)
White RC over the stage's cells (PRE+X', all-signal differential vs floor): p=0.034 (K=59685). Tiers: CANDIDATE 16, BEST-AVAILABLE 14.

| AND-set (timeframes in the member names) | variant | fill L6M | n | add vs floor on fired L6M [per contract] | HOLD | L3M | PRE | X' | ALL-signal add L6M | best member (all-signal) L6M | placebo p | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| THEN60s(iplFVG|30s+OB|30s) | c2_far|F0.7 | 55.2% | 502 | +7.20 (MDE 2.73) | +7.17 | +7.41 | +6.09 | +5.82 | +3.68 | +2.87 | 0.016 | CANDIDATE |  |
| THEN60s(iFVG|30s+OB|30s) | c2_far|F0.7 | 54.2% | 493 | +7.01 (MDE 2.66) | +6.97 | +7.50 | +6.67 | +5.87 | +3.64 | +2.87 | 0.016 | CANDIDATE |  |
| THEN60s(iplFVG|30s+OB|30s) | b_far|F0.7 | 55.4% | 504 | +6.91 (MDE 2.38) | +6.90 | +6.77 | +5.92 | +5.51 | +3.54 | +2.57 | 0.016 | CANDIDATE |  |
| THEN300s(iplFVG|30s+OB|30s) | c2_far|F0.7 | 58.3% | 530 | +6.57 (MDE 2.72) | +6.56 | +6.83 | +5.86 | +5.57 | +3.56 | +2.87 | 0.016 | CANDIDATE |  |
| THEN60s(iFVG|30s+OB|30s) | b_far|F0.7 | 54.7% | 497 | +6.50 (MDE 2.17) | +6.51 | +6.82 | +6.17 | +5.09 | +3.39 | +2.57 | 0.016 | CANDIDATE |  |
| THEN60s(BRK|15s+OB|30s) | c2_far|F0.7 | 53.1% | 483 | +6.05 (MDE 2.56) | +6.06 | +6.70 | +6.22 | +5.59 | +3.04 | +2.87 | 0.016 | CANDIDATE |  |
| THEN60s(iplFVG|30s+OB|30s) | c2_mid|F0.7 | 59.6% | 542 | +6.03 (MDE 1.68) | +6.00 | +5.91 | +5.76 | +4.95 | +3.46 | +2.39 | 0.016 | CANDIDATE |  |
| THEN60s(FVG|15s+OB|45s) | c2_far|F0.7 | 51.5% | 468 | +6.02 (MDE 1.84) | +6.08 | +6.74 | +6.82 | +4.98 | +2.80 | +2.71 | 0.016 | CANDIDATE |  |
| THEN60s(iplFVG|30s+iFVG|30s) | c2_far|F0.7 | 60.8% | 553 | +5.88 (MDE 1.98) | +5.83 | +7.23 | +5.42 | +5.62 | +3.33 | +2.74 | 0.016 | CANDIDATE |  |
| THEN300s(iFVG|30s+OB|30s) | c2_far|F0.7 | 57.8% | 525 | +5.79 (MDE 2.14) | +5.81 | +5.69 | +6.12 | +5.50 | +3.08 | +2.87 | 0.049 | CANDIDATE |  |
| THEN60s(iFVG|30s+OB|30s) | c2_mid|F0.7 | 56.8% | 516 | +5.65 (MDE 1.79) | +5.63 | +5.79 | +5.87 | +5.34 | +3.05 | +2.67 | 0.016 | CANDIDATE |  |
| THEN60s(FVG|15s+OB|30s) | c2_far|F0.7 | 60.1% | 546 | +5.59 (MDE 2.17) | +5.62 | +5.39 | +6.07 | +5.61 | +3.23 | +2.87 | 0.016 | CANDIDATE |  |

Plain sentence (best by all-signal gain): requiring iplFVG|30s THEN OB|30s within 60 s before the signal enters (c2_far|F0.7) adds +7.20 pts per contract on the 55.2% of signals it fires on in the last 6 months (MDE 2.73), but +3.68 pts per signal over ALL signals (the skipped signals' floor P&L counted against it) vs the best member +2.87; tier CANDIDATE.


## Stage stage1ENG  (2026-10-30T22:20Z)

auto

### SM: 3525 combinations x 17 variants = 59925 cells; PRE+X' selection, one recent look on the top 22 cells (30 cell x variant rows)
White RC over the stage's cells (PRE+X', all-signal differential vs floor): p=0.182 (K=59675). Tiers: BEST-AVAILABLE 20, CANDIDATE 10.

| AND-set (timeframes in the member names) | variant | fill L6M | n | add vs floor on fired L6M [per contract] | HOLD | L3M | PRE | X' | ALL-signal add L6M | best member (all-signal) L6M | placebo p | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| THEN60s(iplFVG|15s+OB|45s) | c2_far|F0.7 | 58.0% | 182 | +8.73 (MDE 6.31) | +8.06 | +11.25 | +7.78 | +7.84 | +4.89 | +3.69 | 0.016 | CANDIDATE |  |
| THEN60s(iplFVG|15s+OB|30s) | c2_mid|F0.7 | 62.1% | 195 | +8.58 (MDE 4.99) | +7.98 | +10.86 | +5.47 | +7.47 | +5.19 | +3.30 | 0.016 | CANDIDATE |  |
| THEN60s(iplFVG|30s+OB|45s) | c2_far|F0.7 | 53.8% | 169 | +7.92 (MDE 5.30) | +7.59 | +9.47 | +7.22 | +8.23 | +3.70 | +3.69 | 0.016 | CANDIDATE |  |
| THEN60s(iplFVG|15s+OB|30s) | c2_far|F0.7 | 61.8% | 194 | +7.67 (MDE 4.59) | +6.95 | +9.39 | +6.73 | +7.21 | +4.60 | +3.51 | 0.016 | CANDIDATE |  |
| THEN300s(iplFVG|30s+OB|45s) | c2_far|F0.7 | 55.1% | 173 | +7.67 (MDE 4.77) | +6.71 | +9.89 | +6.66 | +7.53 | +4.04 | +3.69 | 0.049 | CANDIDATE |  |
| AND(OB|45s+iplFVG|15s+OB|1m) | c2_far|F0.7 | 55.4% | 174 | +7.65 (MDE 5.36) | +7.11 | +10.43 | +6.69 | +8.19 | +4.04 | +3.69 | 0.377 | BEST-AVAILABLE | placebo |
| AND(OB|45s+iplFVG|15s+OB|30s) | c2_far|F0.7 | 57.0% | 179 | +7.63 (MDE 5.25) | +7.11 | +10.20 | +6.69 | +8.33 | +4.17 | +3.69 | 0.377 | BEST-AVAILABLE | placebo |
| AND(OB|45s+iplFVG|15s) | c2_far|F0.7 | 57.0% | 179 | +7.63 (MDE 5.25) | +7.13 | +10.20 | +6.76 | +8.29 | +4.17 | +3.69 | 0.344 | BEST-AVAILABLE | placebo |
| AND(OB|45s+FVG|30s+iplFVG|15s) | c2_far|F0.7 | 57.0% | 179 | +7.63 (MDE 5.25) | +7.13 | +10.20 | +6.72 | +8.15 | +4.17 | +3.69 | 0.410 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|15s+OB|45s) | c2_mid|F0.7 | 59.2% | 186 | +7.59 (MDE 4.59) | +7.32 | +8.75 | +6.68 | +6.61 | +4.35 | +2.71 | 0.016 | CANDIDATE |  |
| AND(OB|45s+iplFVG|15s+FVG|45s) | c2_far|F0.7 | 56.7% | 178 | +7.54 (MDE 5.30) | +7.05 | +10.20 | +6.70 | +8.15 | +4.09 | +3.69 | 0.393 | BEST-AVAILABLE | placebo |
| AND(OB|45s+iplFVG|45s) | c2_far|F0.7 | 56.4% | 177 | +7.39 (MDE 5.37) | +6.87 | +9.96 | +6.19 | +7.33 | +3.99 | +3.69 | 0.262 | BEST-AVAILABLE | placebo |

Plain sentence (best by all-signal gain): requiring iplFVG|15s THEN OB|30s within 60 s before the signal enters (c2_mid|F0.7) adds +8.58 pts per contract on the 62.1% of signals it fires on in the last 6 months (MDE 4.99), but +5.19 pts per signal over ALL signals (the skipped signals' floor P&L counted against it) vs the best member +3.30; tier CANDIDATE.


## Stage stage1ENG  (2026-10-30T22:40Z)

auto

### WT: 3525 combinations x 17 variants = 59925 cells; PRE+X' selection, one recent look on the top 15 cells (30 cell x variant rows)
White RC over the stage's cells (PRE+X', all-signal differential vs floor): p=0.006 (K=59633). Tiers: BEST-AVAILABLE 30.

| AND-set (timeframes in the member names) | variant | fill L6M | n | add vs floor on fired L6M [per contract] | HOLD | L3M | PRE | X' | ALL-signal add L6M | best member (all-signal) L6M | placebo p | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AND(OB|15s+BRK|15s) | c2_far|F0.7 | 50.1% | 855 | +4.85 (MDE 1.31) | +4.86 | +4.95 | +4.27 | +4.38 | +2.18 | +2.19 | 0.492 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|15s+iplFVG|15s) | c2_far|F0.7 | 50.4% | 859 | +4.82 (MDE 1.31) | +4.86 | +4.85 | +4.35 | +4.55 | +2.18 | +2.19 | 0.623 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|15s+BRK|30s) | c2_far|F0.7 | 49.6% | 847 | +4.81 (MDE 1.29) | +4.84 | +4.90 | +4.23 | +4.41 | +2.14 | +2.19 | 0.525 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|15s+FVG|15s) | c2_far|F0.7 | 50.5% | 862 | +4.81 (MDE 1.31) | +4.83 | +4.86 | +4.28 | +4.46 | +2.19 | +2.34 | 0.492 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|15s+iFVG|30s) | c2_far|F0.7 | 50.6% | 864 | +4.80 (MDE 1.30) | +4.81 | +4.84 | +4.28 | +4.43 | +2.19 | +2.19 | 0.525 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|15s+FVG|30s) | c2_far|F0.7 | 50.8% | 866 | +4.79 (MDE 1.30) | +4.81 | +4.85 | +4.30 | +4.37 | +2.19 | +2.27 | 0.361 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|15s+iFVG|1m) | c2_far|F0.7 | 48.5% | 828 | +4.79 (MDE 1.33) | +4.81 | +4.69 | +4.32 | +4.47 | +2.07 | +2.19 | 0.721 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|15s+OB|30s) | c2_far|F0.7 | 50.6% | 863 | +4.79 (MDE 1.31) | +4.81 | +4.84 | +4.28 | +4.43 | +2.18 | +2.19 | 0.475 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|15s+FVG|45s) | c2_far|F0.7 | 50.6% | 863 | +4.79 (MDE 1.31) | +4.80 | +4.82 | +4.26 | +4.40 | +2.18 | +2.41 | 0.541 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|15s+iFVG|45s) | c2_far|F0.7 | 50.4% | 860 | +4.79 (MDE 1.31) | +4.80 | +4.84 | +4.36 | +4.42 | +2.17 | +2.19 | 0.508 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|15s+iFVG|15s) | c2_far|F0.7 | 50.4% | 860 | +4.73 (MDE 1.32) | +4.77 | +4.88 | +4.31 | +4.44 | +2.14 | +2.19 | 0.705 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|45s+FVG|30s) | c2_far|F0.7 | 56.5% | 964 | +4.70 (MDE 1.23) | +4.65 | +4.69 | +3.64 | +3.58 | +2.41 | +2.41 | 0.066 | BEST-AVAILABLE | placebo |

Plain sentence (best by all-signal gain): requiring FVG|45s AND FVG|30s before the signal enters (c2_far|F0.7) adds +4.70 pts per contract on the 56.5% of signals it fires on in the last 6 months (MDE 1.23), but +2.41 pts per signal over ALL signals (the skipped signals' floor P&L counted against it) vs the best member +2.41; tier BEST-AVAILABLE.


## Stage stage1ENG  (2026-10-30T23:01Z)

auto

### DN: 3525 combinations x 17 variants = 59925 cells; PRE+X' selection, one recent look on the top 12 cells (30 cell x variant rows)
White RC over the stage's cells (PRE+X', all-signal differential vs floor): p=0.002 (K=59597). Tiers: BEST-AVAILABLE 30.

| AND-set (timeframes in the member names) | variant | fill L6M | n | add vs floor on fired L6M [per contract] | HOLD | L3M | PRE | X' | ALL-signal add L6M | best member (all-signal) L6M | placebo p | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| THEN60s(iplFVG|15s+OB|2m) | c2_far|F0.7 | 36.2% | 254 | +8.31 (MDE 2.52) | +9.08 | +8.69 | +9.33 | +8.24 | +2.72 | +2.72 | 1.000 | BEST-AVAILABLE | placebo,<=best_member_L6M |
| THEN60s(iplFVG|15s+OB|1m) | c2_far|F0.7 | 47.2% | 331 | +7.15 (MDE 1.91) | +7.62 | +9.06 | +8.33 | +7.02 | +3.16 | +2.88 | 1.000 | BEST-AVAILABLE | placebo |
| THEN60s(FVG|15s+OB|1m) | c2_far|F0.7 | 50.1% | 351 | +7.09 (MDE 1.98) | +7.52 | +8.77 | +7.40 | +6.10 | +3.35 | +2.88 | 0.869 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|15s+OB|1m) | c2_mid|F0.7 | 54.2% | 380 | +7.00 (MDE 2.24) | +7.24 | +8.79 | +7.33 | +7.23 | +3.62 | +2.81 | 0.672 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|15s+OB|1m) | b_far|F0.7 | 46.4% | 325 | +7.00 (MDE 1.89) | +7.42 | +8.89 | +8.04 | +6.64 | +3.02 | +2.57 | 0.951 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|15s+iFVG|3m) | c2_far|F0.7 | 45.8% | 321 | +6.90 (MDE 2.05) | +7.46 | +7.71 | +7.94 | +7.66 | +2.92 | +2.72 | 1.000 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|15s+iFVG|5m) | c2_far|F0.7 | 41.2% | 289 | +6.86 (MDE 2.64) | +7.33 | +6.59 | +9.22 | +7.49 | +2.57 | +2.72 | 1.000 | BEST-AVAILABLE | placebo,<=best_member_L6M |
| THEN300s(iplFVG|15s+OB|1m) | c2_far|F0.7 | 48.4% | 339 | +6.83 (MDE 1.91) | +7.27 | +8.66 | +7.72 | +6.44 | +3.09 | +2.88 | 0.967 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|15s+OB|1m) | b_mid|F0.7 | 53.8% | 377 | +6.79 (MDE 2.26) | +6.98 | +8.67 | +6.92 | +6.71 | +3.47 | +2.42 | 0.180 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|15s+OB|1m) | c2_near|F0.7 | 56.6% | 397 | +6.75 (MDE 2.46) | +6.87 | +7.60 | +6.95 | +7.01 | +3.65 | +2.66 | 0.590 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|15s+iplFVG|5m) | c2_far|F0.7 | 49.8% | 349 | +6.68 (MDE 2.52) | +7.49 | +5.79 | +8.04 | +6.34 | +3.12 | +2.72 | 0.967 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|15s+iFVG|3m) | c2_mid|F0.7 | 48.9% | 343 | +6.67 (MDE 1.93) | +7.23 | +7.83 | +7.53 | +6.77 | +3.04 | +2.37 | 0.984 | BEST-AVAILABLE | placebo |

Plain sentence (best by all-signal gain): requiring iplFVG|15s THEN OB|1m within 60 s before the signal enters (c2_near|F0.7) adds +6.75 pts per contract on the 56.6% of signals it fires on in the last 6 months (MDE 2.46), but +3.65 pts per signal over ALL signals (the skipped signals' floor P&L counted against it) vs the best member +2.66; tier BEST-AVAILABLE.


## Stage stage1ENG  (2026-10-31T00:05Z)

auto

### PB: 3525 combinations x 17 variants = 59925 cells; PRE+X' selection, one recent look on the top 24 cells (30 cell x variant rows)
White RC over the stage's cells (PRE+X', all-signal differential vs floor): p=0.006 (K=59685). Tiers: BEST-AVAILABLE 24, CANDIDATE 6.

| AND-set (timeframes in the member names) | variant | fill L6M | n | add vs floor on fired L6M [per contract] | HOLD | L3M | PRE | X' | ALL-signal add L6M | best member (all-signal) L6M | placebo p | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| THEN60s(iplFVG|15s+OB|3m) | c2_far|F0.7 | 37.3% | 323 | +7.22 (MDE 3.67) | +7.52 | +6.15 | +8.29 | +6.98 | +1.89 | +1.50 | 0.967 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|15s+OB|3m) | c2_mid|F0.7 | 45.6% | 395 | +5.45 (MDE 2.78) | +5.81 | +3.66 | +7.70 | +5.63 | +1.88 | +1.57 | 0.984 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|15s+OB|3m) | c2_near|F0.7 | 48.5% | 420 | +4.60 (MDE 2.78) | +4.79 | +3.08 | +7.11 | +5.05 | +1.63 | +1.38 | 0.967 | BEST-AVAILABLE | placebo |
| AND(OB|30s+iFVG|45s) | c2_far|F0.7 | 64.8% | 561 | +4.40 (MDE 2.02) | +4.48 | +3.96 | +5.02 | +4.54 | +2.62 | +2.38 | 0.410 | BEST-AVAILABLE | placebo,<=best_member_PRE+X |
| AND(OB|30s+iplFVG|45s) | c2_far|F0.7 | 64.2% | 556 | +4.11 (MDE 2.15) | +4.24 | +2.99 | +5.08 | +4.91 | +2.41 | +2.38 | 0.803 | BEST-AVAILABLE | placebo |
| AND(OB|30s+OB|45s) | c2_far|F0.7 | 65.5% | 567 | +4.02 (MDE 2.07) | +4.10 | +3.39 | +4.96 | +4.45 | +2.41 | +2.38 | 0.689 | BEST-AVAILABLE | placebo |
| AND(OB|30s+FVG|15s) | c2_far|F0.7 | 65.2% | 565 | +4.00 (MDE 2.06) | +4.11 | +3.35 | +5.05 | +4.42 | +2.39 | +2.38 | 0.574 | BEST-AVAILABLE | placebo |
| AND(OB|30s+OB|15s) | c2_far|F0.7 | 65.6% | 568 | +3.97 (MDE 2.08) | +4.07 | +3.35 | +5.03 | +4.35 | +2.38 | +2.38 | 0.541 | BEST-AVAILABLE | placebo,<=best_member_L6M |
| AND(OB|30s+iFVG|1m) | c2_far|F0.7 | 65.4% | 566 | +3.95 (MDE 2.07) | +3.97 | +3.32 | +4.98 | +4.47 | +2.35 | +2.38 | 0.689 | BEST-AVAILABLE | placebo,<=best_member_L6M |
| AND(OB|30s+iplFVG|1m) | c2_far|F0.7 | 64.4% | 558 | +3.93 (MDE 2.12) | +4.01 | +3.28 | +4.98 | +4.60 | +2.30 | +2.38 | 0.754 | BEST-AVAILABLE | placebo,<=best_member_L6M |
| THEN60s(iplFVG|15s+FVG|45s) | c2_far|F0.7 | 63.9% | 553 | +3.39 (MDE 2.58) | +3.47 | +2.24 | +5.72 | +4.71 | +2.06 | +1.54 | 0.066 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|15s+BRK|45s) | c2_far|F0.7 | 62.0% | 537 | +3.30 (MDE 2.16) | +3.42 | +3.18 | +6.14 | +4.92 | +1.93 | +1.50 | 0.066 | BEST-AVAILABLE | placebo |

Plain sentence (best by all-signal gain): requiring OB|30s AND iFVG|45s before the signal enters (c2_far|F0.7) adds +4.40 pts per contract on the 64.8% of signals it fires on in the last 6 months (MDE 2.02), but +2.62 pts per signal over ALL signals (the skipped signals' floor P&L counted against it) vs the best member +2.38; tier BEST-AVAILABLE.


## Stage stage1ENG  (2026-10-31T00:59Z)

auto

### MV: 3525 combinations x 17 variants = 59925 cells; PRE+X' selection, one recent look on the top 18 cells (30 cell x variant rows)
White RC over the stage's cells (PRE+X', all-signal differential vs floor): p=0.002 (K=59615). Tiers: BEST-AVAILABLE 18, CANDIDATE 12.

| AND-set (timeframes in the member names) | variant | fill L6M | n | add vs floor on fired L6M [per contract] | HOLD | L3M | PRE | X' | ALL-signal add L6M | best member (all-signal) L6M | placebo p | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| THEN60s(iplFVG|45s+OB|45s) | c2_far|F0.7 | 48.1% | 544 | +8.21 (MDE 2.62) | +8.27 | +9.08 | +6.86 | +7.59 | +3.59 | +3.56 | 0.754 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|1m+OB|1m) | c2_far|F0.7 | 48.4% | 547 | +8.19 (MDE 2.44) | +8.08 | +8.57 | +7.59 | +6.68 | +3.47 | +2.99 | 0.754 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|30s+OB|45s) | c2_far|F0.7 | 50.8% | 574 | +8.05 (MDE 2.21) | +8.18 | +8.05 | +6.84 | +7.12 | +3.75 | +3.56 | 0.508 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|45s+OB|1m) | b_far|F0.7 | 50.0% | 566 | +7.96 (MDE 2.20) | +7.77 | +7.54 | +7.20 | +6.79 | +3.50 | +2.58 | 0.033 | CANDIDATE |  |
| THEN60s(iplFVG|45s+OB|1m) | c2_far|F0.7 | 50.2% | 568 | +7.93 (MDE 1.97) | +7.68 | +7.74 | +7.49 | +6.93 | +3.50 | +2.99 | 0.557 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|30s+OB|1m) | c2_far|F0.7 | 50.8% | 575 | +7.79 (MDE 1.92) | +7.50 | +8.14 | +7.37 | +6.98 | +3.49 | +2.99 | 0.443 | BEST-AVAILABLE | placebo |
| THEN300s(iplFVG|45s+OB|45s) | c2_far|F0.7 | 54.1% | 612 | +7.54 (MDE 2.03) | +7.60 | +8.08 | +6.15 | +7.69 | +3.76 | +3.56 | 0.721 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|30s+FVG|3m) | c2_far|F0.7 | 49.4% | 559 | +7.45 (MDE 1.91) | +7.35 | +7.49 | +7.28 | +6.73 | +3.46 | +2.88 | 0.770 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|30s+OB|1m) | b_far|F0.7 | 51.0% | 577 | +7.33 (MDE 1.89) | +7.21 | +7.97 | +7.04 | +6.83 | +3.27 | +2.58 | 0.148 | BEST-AVAILABLE | placebo |
| THEN60s(iplFVG|1m+OB|30s) | c2_far|F0.7 | 57.9% | 655 | +7.11 (MDE 1.69) | +7.06 | +7.82 | +7.14 | +6.19 | +3.93 | +3.58 | 0.016 | CANDIDATE |  |
| THEN60s(iFVG|1m+OB|30s) | c2_far|F0.7 | 52.6% | 595 | +7.07 (MDE 2.01) | +7.06 | +7.13 | +6.71 | +6.48 | +3.50 | +3.58 | 0.492 | BEST-AVAILABLE | placebo,<=best_member_L6M |
| THEN60s(iplFVG|45s+FVG|3m) | c2_far|F0.7 | 47.7% | 539 | +7.04 (MDE 2.38) | +6.96 | +7.65 | +6.92 | +6.91 | +3.00 | +2.88 | 1.000 | BEST-AVAILABLE | placebo |

Plain sentence (best by all-signal gain): requiring iplFVG|30s THEN OB|30s within 60 s before the signal enters (c2_mid|F0.7) adds +6.68 pts per contract on the 63.8% of signals it fires on in the last 6 months (MDE 1.83), but +4.13 pts per signal over ALL signals (the skipped signals' floor P&L counted against it) vs the best member +3.44; tier CANDIDATE.


## Stage stage1ENG  (2026-10-31T01:24Z)

auto

### MA: 3525 combinations x 17 variants = 59925 cells; PRE+X' selection, one recent look on the top 19 cells (30 cell x variant rows)
White RC over the stage's cells (PRE+X', all-signal differential vs floor): p=0.204 (K=59661). Tiers: BEST-AVAILABLE 28, CANDIDATE 2.

| AND-set (timeframes in the member names) | variant | fill L6M | n | add vs floor on fired L6M [per contract] | HOLD | L3M | PRE | X' | ALL-signal add L6M | best member (all-signal) L6M | placebo p | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AND(OB|45s+iplFVG|30s) | c2_far|F0.7 | 58.0% | 236 | +6.43 (MDE 3.65) | +6.26 | +7.29 | +5.57 | +5.01 | +3.58 | +3.27 | 0.246 | BEST-AVAILABLE | placebo |
| AND(OB|45s+iplFVG|15s) | c2_far|F0.7 | 58.5% | 238 | +6.36 (MDE 3.51) | +6.01 | +7.27 | +5.67 | +4.99 | +3.56 | +3.27 | 0.393 | BEST-AVAILABLE | placebo |
| AND(OB|45s+iplFVG|45s) | c2_far|F0.7 | 57.5% | 234 | +6.20 (MDE 3.62) | +6.11 | +7.02 | +5.41 | +5.74 | +3.41 | +3.27 | 0.443 | BEST-AVAILABLE | placebo |
| THEN60s(FVG|15s+FVG|3m) | c2_far|F0.7 | 56.3% | 229 | +6.02 (MDE 2.58) | +5.48 | +6.29 | +6.13 | +4.23 | +2.95 | +2.16 | 0.016 | CANDIDATE |  |
| AND(OB|45s+iplFVG|45s) | c2_near|F0.7 | 64.4% | 262 | +5.82 (MDE 3.80) | +5.39 | +6.60 | +4.58 | +5.31 | +3.62 | +3.15 | 0.066 | BEST-AVAILABLE | placebo |
| AND(OB|45s+iplFVG|15s) | c2_near|F0.7 | 64.1% | 261 | +5.64 (MDE 3.26) | +5.23 | +6.75 | +4.78 | +5.18 | +3.49 | +3.15 | 0.295 | BEST-AVAILABLE | placebo |
| THEN60s(iFVG|30s+FVG|3m) | c2_mid|F0.7 | 55.0% | 224 | +5.54 (MDE 2.14) | +5.37 | +4.43 | +6.25 | +4.20 | +2.59 | +2.32 | 0.361 | BEST-AVAILABLE | placebo |
| AND(OB|45s+iplFVG|30s) | c2_near|F0.7 | 64.6% | 263 | +5.41 (MDE 3.26) | +5.06 | +6.76 | +4.72 | +5.21 | +3.37 | +3.15 | 0.213 | BEST-AVAILABLE | placebo |
| AND(FVG|1m+iplFVG|30s) | c2_far|F0.7 | 66.8% | 272 | +5.03 (MDE 2.65) | +4.70 | +4.80 | +4.68 | +4.18 | +3.28 | +2.82 | 0.426 | BEST-AVAILABLE | placebo |
| AND(FVG|1m+iplFVG|15s) | c2_far|F0.7 | 66.1% | 269 | +4.93 (MDE 2.44) | +4.63 | +4.15 | +4.53 | +4.51 | +3.18 | +2.82 | 0.623 | BEST-AVAILABLE | placebo |
| AND(OB|45s+iplFVG|30s) | c2_mid|F0.7 | 64.4% | 262 | +4.87 (MDE 3.28) | +4.62 | +5.30 | +4.84 | +5.27 | +3.01 | +2.69 | 0.557 | BEST-AVAILABLE | placebo |
| AND(OB|45s+iplFVG|15s) | c2_mid|F0.7 | 64.1% | 261 | +4.80 (MDE 3.40) | +4.57 | +5.27 | +4.95 | +5.03 | +2.95 | +2.69 | 0.689 | BEST-AVAILABLE | placebo |

Plain sentence (best by all-signal gain): requiring OB|45s AND iplFVG|45s before the signal enters (c2_near|F0.7) adds +5.82 pts per contract on the 64.4% of signals it fires on in the last 6 months (MDE 3.80), but +3.62 pts per signal over ALL signals (the skipped signals' floor P&L counted against it) vs the best member +3.15; tier BEST-AVAILABLE.

