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
