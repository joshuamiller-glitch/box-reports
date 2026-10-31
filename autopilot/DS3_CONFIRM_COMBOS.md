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



## PAGE 1 — stage1ENG: verdict per book and every candidate on three units (generated 2026-10-31 03:17Z)

Units: pc = pts per contract of final position (primary, all book signals, L6M); pl = per planned lot; stack = lock-engine $/wk difference vs the plain-dip floor (engine books only: ST HM WT KB SM PE; others n/a). Placebo = random-level (cf_engine.placebo_level_ov, same distance distribution) rank of the real gain among draws (limit variants only). "excess" = combination minus its better member in the same variant (paired week-block CI): the "beats its best single member" test. FINAL TIER: INFO-CANDIDATE needs stack>0 in L6M and HOLD (engine books), placebo beaten (95th pct), excess CI>0; otherwise STRUCTURE (the single-member resting-limit/70-30 structure explains it) or STACK-NEG.

| book | verdict |
|---|---|
| KB | 50 looked cells; {'BEST-AVAILABLE': np.int64(40), 'CANDIDATE': np.int64(10)}; stage RC(PRE+X') p=0.178; 10 unit-checked candidates -> 5 INFO-CANDIDATE, 5 STRUCTURE/STACK-NEG |
| PE | 30 looked cells; {'BEST-AVAILABLE': np.int64(23), 'CANDIDATE': np.int64(7)}; stage RC(PRE+X') p=0.002; 7 unit-checked candidates -> 1 INFO-CANDIDATE, 6 STRUCTURE/STACK-NEG |
| ST | 30 looked cells; {'BEST-AVAILABLE': np.int64(19), 'CANDIDATE': np.int64(11)}; stage RC(PRE+X') p=0.008; 11 unit-checked candidates -> 2 INFO-CANDIDATE, 9 STRUCTURE/STACK-NEG |
| HM | 30 looked cells; {'CANDIDATE': np.int64(16), 'BEST-AVAILABLE': np.int64(14)}; stage RC(PRE+X') p=0.034; 16 unit-checked candidates -> 8 INFO-CANDIDATE, 8 STRUCTURE/STACK-NEG |
| SM | 30 looked cells; {'BEST-AVAILABLE': np.int64(20), 'CANDIDATE': np.int64(10)}; stage RC(PRE+X') p=0.182; 10 unit-checked candidates -> 3 INFO-CANDIDATE, 7 STRUCTURE/STACK-NEG |
| WT | 30 looked cells; {'BEST-AVAILABLE': np.int64(30)}; stage RC(PRE+X') p=0.006; 0 unit-checked candidates -> 0 INFO-CANDIDATE, 0 STRUCTURE/STACK-NEG |
| DN | 30 looked cells; {'BEST-AVAILABLE': np.int64(30)}; stage RC(PRE+X') p=0.002; 0 unit-checked candidates -> 0 INFO-CANDIDATE, 0 STRUCTURE/STACK-NEG |
| PB | 30 looked cells; {'BEST-AVAILABLE': np.int64(24), 'CANDIDATE': np.int64(6)}; stage RC(PRE+X') p=0.006; 6 unit-checked candidates -> 0 INFO-CANDIDATE, 6 STRUCTURE/STACK-NEG |
| MV | 30 looked cells; {'BEST-AVAILABLE': np.int64(18), 'CANDIDATE': np.int64(12)}; stage RC(PRE+X') p=0.002; 12 unit-checked candidates -> 3 INFO-CANDIDATE, 9 STRUCTURE/STACK-NEG |
| MA | 30 looked cells; {'BEST-AVAILABLE': np.int64(28), 'CANDIDATE': np.int64(2)}; stage RC(PRE+X') p=0.204; 2 unit-checked candidates -> 0 INFO-CANDIDATE, 2 STRUCTURE/STACK-NEG |

| book | cell | pc L6M | pl L6M | stack $/wk L6M | stack HOLD | placebo rank (mean) | best member pc | excess [CI] | final | DSR | RW | PBO | + quarters | top5% |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SM | THEN60s(iplFVG~15s+OB~30s) / c2_mid~F0.7 | +5.19 | +1.13 | +2808 | +915 | 1/101 (+3.20) | +3.30 | +1.89 [+0.69,+3.20] | INFO-CANDIDATE | 1.00 | Y | 0.05 | 12/12 | 0.66 |
| SM | THEN60s(iplFVG~15s+OB~30s) / c2_near~F0.7 | +4.68 | +0.52 | +2634 | +750 | 2/101 (+3.14) | +2.48 | +2.20 [+1.02,+3.55] | INFO-CANDIDATE | 1.00 | Y | 0.05 | 12/12 | 0.61 |
| SM | THEN60s(iplFVG~15s+OB~30s) / c2_far~F0.7 | +4.60 | +0.20 | +1900 | +227 | 2/101 (+3.26) | +3.51 | +1.09 [+0.08,+2.18] | INFO-CANDIDATE | 1.00 | Y | 0.05 | 12/12 | 0.58 |
| MV | THEN60s(iplFVG~30s+OB~30s) / c2_mid~F0.7 | +4.13 | +0.65 | +nan | +nan | 4/101 (+3.66) | +3.44 | +0.69 [+0.23,+1.19] | INFO-CANDIDATE | 1.00 | Y | 0.03 | 12/12 | 0.57 |
| HM | THEN60s(iplFVG~30s+OB~30s) / c2_far~F0.7 | +3.68 | +0.95 | +5328 | +3392 | 1/101 (+2.77) | +2.87 | +0.81 [+0.43,+1.20] | INFO-CANDIDATE | 1.00 | Y | 0.45 | 12/12 | 0.65 |
| HM | THEN60s(iFVG~30s+OB~30s) / c2_far~F0.7 | +3.64 | +0.35 | +6511 | +4731 | 1/101 (+2.79) | +2.87 | +0.77 [+0.24,+1.30] | INFO-CANDIDATE | 1.00 | Y | 0.45 | 12/12 | 0.61 |
| MV | THEN60s(iplFVG~1m+OB~30s) / b_far~F0.7 | +3.62 | +0.53 | +nan | +nan | 5/101 (+3.16) | +2.86 | +0.76 [+0.17,+1.34] | INFO-CANDIDATE | 1.00 | Y | 0.03 | 12/12 | 0.63 |
| HM | THEN300s(iplFVG~30s+OB~30s) / c2_far~F0.7 | +3.56 | +0.85 | +7486 | +5302 | 1/101 (+2.67) | +2.87 | +0.69 [+0.28,+1.09] | INFO-CANDIDATE | 1.00 | Y | 0.45 | 12/12 | 0.66 |
| HM | THEN60s(iplFVG~30s+OB~30s) / b_far~F0.7 | +3.54 | +0.77 | +4790 | +3267 | 1/101 (+2.67) | +2.57 | +0.97 [+0.59,+1.32] | INFO-CANDIDATE | 1.00 | Y | 0.45 | 12/12 | 0.66 |
| MV | THEN60s(iplFVG~45s+OB~1m) / b_far~F0.7 | +3.50 | +0.75 | +nan | +nan | 1/101 (+2.92) | +2.58 | +0.92 [+0.26,+1.63] | INFO-CANDIDATE | 1.00 | Y | 0.03 | 12/12 | 0.70 |
| HM | THEN60s(iplFVG~30s+OB~30s) / c2_mid~F0.7 | +3.46 | +0.54 | +7173 | +5908 | 1/101 (+2.79) | +2.39 | +1.06 [+0.59,+1.56] | INFO-CANDIDATE | 1.00 | Y | 0.45 | 12/12 | 0.61 |
| HM | THEN60s(iFVG~30s+OB~30s) / b_far~F0.7 | +3.39 | +0.28 | +6324 | +4822 | 1/101 (+2.69) | +2.57 | +0.82 [+0.28,+1.40] | INFO-CANDIDATE | 1.00 | Y | 0.45 | 12/12 | 0.63 |
| HM | THEN60s(FVG~15s+OB~30s) / c2_far~F0.7 | +3.23 | +0.16 | +6647 | +4436 | 1/101 (+2.49) | +2.87 | +0.35 [+0.15,+0.66] | INFO-CANDIDATE | 1.00 | Y | 0.45 | 12/12 | 0.60 |
| HM | THEN60s(FVG~15s+OB~30s) / b_far~F0.7 | +3.11 | +0.26 | +4276 | +2876 | 1/101 (+2.33) | +2.57 | +0.54 [+0.24,+0.93] | INFO-CANDIDATE | 1.00 | Y | 0.45 | 12/12 | 0.62 |
| PE | THEN60s(iFVG~30s+OB~1m) / c2_far~F0.7 | +3.07 | +0.90 | +287 | +137 | 1/101 (+2.47) | +2.50 | +0.57 [+0.24,+0.97] | INFO-CANDIDATE | 1.00 | Y | 0.02 | 12/12 | 0.71 |
| KB | THEN60s(iplFVG~45s+iFVG~15s) / c2_far~F0.7 | +3.04 | +0.41 | +666 | +501 | 8/201 (+2.58) | +2.50 | +0.53 [+0.26,+0.84] | INFO-CANDIDATE | 1.00 | Y | 0.23 | 12/12 | 0.62 |
| KB | THEN60s(iplFVG~30s+iFVG~15s) / c2_far~F0.7 | +2.96 | +0.53 | +951 | +726 | 6/201 (+2.59) | +2.50 | +0.46 [+0.21,+0.72] | INFO-CANDIDATE | 1.00 | Y | 0.23 | 12/12 | 0.58 |
| KB | THEN60s(iFVG~15s+FVG~15s) / c2_far~F0.7 | +2.87 | +0.35 | +2288 | +2035 | 5/201 (+2.41) | +2.61 | +0.26 [+0.11,+0.41] | INFO-CANDIDATE | 1.00 | Y | 0.23 | 12/12 | 0.60 |
| KB | THEN300s(iplFVG~45s+iFVG~15s) / c2_far~F0.7 | +2.87 | +0.29 | +1417 | +1010 | 6/201 (+2.46) | +2.50 | +0.36 [+0.17,+0.59] | INFO-CANDIDATE | 1.00 | Y | 0.23 | 12/12 | 0.61 |
| KB | THEN60s(FVG~15s+FVG~2m) / c2_near~F0.7 | +2.62 | +0.45 | +1559 | +1337 | 5/201 (+2.17) | +2.01 | +0.61 [+0.23,+0.94] | INFO-CANDIDATE | 1.00 | Y | 0.23 | 12/12 | 0.68 |
| ST | THEN60s(iplFVG~15s+OB~1m) / b_mid~F0.7 | +1.91 | -0.80 | +3658 | +2248 | 4/101 (+1.63) | +1.17 | +0.74 [+0.29,+1.14] | INFO-CANDIDATE | 1.00 | Y | 0.07 | 12/12 | 0.83 |
| ST | THEN60s(iplFVG~15s+OB~1m) / b_near~F0.7 | +1.87 | -0.69 | +2265 | +1617 | 4/101 (+1.51) | +1.06 | +0.81 [+0.36,+1.18] | INFO-CANDIDATE | 1.00 | Y | 0.07 | 12/12 | 0.77 |
| SM | THEN60s(iplFVG~15s+OB~45s) / c2_mid~F0.7 | +4.35 | +0.16 | +1256 | -494 | 16/101 (+3.63) | +2.71 | +1.64 [+0.83,+2.56] | STACK-NEG | 1.00 | Y | 0.05 | 12/12 | 0.60 |
| PE | THEN60s(iplFVG~30s+FVG~15s) / c2_far~F0.7 | +3.58 | +0.59 | -99 | +2 | 1/101 (+2.85) | +2.82 | +0.76 [+0.27,+1.24] | STACK-NEG | 1.00 | Y | 0.02 | 12/12 | 0.61 |
| HM | THEN60s(BRK~15s+OB~30s) / c2_far~F0.7 | +3.04 | +0.07 | +848 | -452 | 2/101 (+2.33) | +2.87 | +0.16 [-0.15,+0.56] | STACK-NEG | 1.00 | Y | 0.45 | 12/12 | 0.65 |
| PE | THEN60s(iplFVG~30s+OB~1m) / b_far~F0.7 | +2.96 | +0.85 | -665 | -1246 | 3/101 (+2.51) | +2.29 | +0.67 [+0.06,+1.23] | STACK-NEG | 1.00 | Y | 0.02 | 12/12 | 0.72 |
| KB | THEN60s(iplFVG~45s+iFVG~15s) / c2_mid~F0.7 | +2.82 | +0.27 | -1054 | -1428 | 13/201 (+2.51) | +2.19 | +0.63 [+0.33,+0.94] | STACK-NEG | 1.00 | Y | 0.23 | 12/12 | 0.62 |
| ST | THEN60s(iplFVG~15s+OB~30s) / c2_mid~F0.7 | +2.74 | -0.82 | -1470 | -4099 | 2/101 (+2.25) | +2.01 | +0.73 [+0.38,+1.15] | STACK-NEG | 1.00 | Y | 0.07 | 12/12 | 0.66 |
| ST | THEN60s(iplFVG~15s+OB~30s) / b_mid~F0.7 | +2.68 | -0.70 | -1526 | -3995 | 4/101 (+2.18) | +1.74 | +0.94 [+0.61,+1.34] | STACK-NEG | 1.00 | Y | 0.07 | 12/12 | 0.72 |
| ST | THEN60s(iplFVG~15s+OB~30s) / c2_far~F0.7 | +2.60 | -1.05 | +2406 | -771 | 10/101 (+2.25) | +1.98 | +0.62 [+0.27,+0.96] | STACK-NEG | 1.00 | Y | 0.07 | 12/12 | 0.69 |
| ST | THEN60s(iplFVG~15s+OB~30s) / c2_near~F0.7 | +2.58 | -0.90 | -5401 | -7396 | 4/101 (+2.21) | +1.87 | +0.71 [+0.33,+1.05] | STACK-NEG | 1.00 | Y | 0.07 | 12/12 | 0.65 |
| ST | THEN60s(iplFVG~30s+OB~30s) / c2_near~F0.7 | +2.50 | -0.91 | -8473 | -8723 | 2/101 (+2.05) | +1.87 | +0.62 [+0.20,+1.07] | STACK-NEG | 1.00 | Y | 0.07 | 12/12 | 0.65 |
| PE | THEN60s(FVG~15s+FVG~2m) / c2_near~F0.7 | +2.47 | -0.27 | -173 | +241 | 61/101 (+2.52) | +1.97 | +0.50 [-0.28,+1.32] | STACK-NEG | 1.00 | Y | 0.02 | 12/12 | 0.69 |
| ST | THEN60s(iplFVG~15s+OB~30s) / b_far~F0.7 | +2.41 | -1.11 | -1251 | -3970 | 5/101 (+2.04) | +1.66 | +0.74 [+0.39,+1.09] | STACK-NEG | 1.00 | Y | 0.07 | 12/12 | 0.72 |
| ST | THEN60s(iplFVG~30s+OB~30s) / c2_mid~F0.7 | +2.40 | -1.00 | -6763 | -7451 | 1/101 (+2.00) | +2.01 | +0.39 [-0.00,+0.81] | STACK-NEG | 1.00 | Y | 0.07 | 12/12 | 0.67 |
| ST | THEN60s(iplFVG~45s+OB~30s) / c2_mid~F0.7 | +2.39 | -0.31 | +490 | -844 | 1/101 (+1.86) | +2.01 | +0.38 [-0.27,+1.09] | STACK-NEG | 1.00 | Y | 0.07 | 12/12 | 0.75 |
| KB | THEN60s(FVG~15s+FVG~2m) / b_mid~F0.7 | +2.36 | +0.43 | -1039 | -958 | 5/201 (+2.01) | +1.92 | +0.44 [+0.21,+0.69] | STACK-NEG | 1.00 | Y | 0.23 | 12/12 | 0.72 |
| PE | THEN60s(FVG~15s+FVG~2m) / b_far~F0.7 | +2.35 | +0.39 | -4 | -25 | 11/101 (+2.13) | +1.67 | +0.67 [+0.00,+1.42] | STACK-NEG | 1.00 | Y | 0.02 | 12/12 | 0.75 |
| KB | THEN60s(iplFVG~30s+FVG~2m) / b_mid~F0.7 | +2.32 | +0.92 | +377 | -488 | 4/201 (+1.97) | +1.92 | +0.40 [+0.15,+0.66] | STACK-NEG | 1.00 | Y | 0.23 | 12/12 | 0.73 |
| ST | THEN60s(iplFVG~30s+OB~30s) / b_far~F0.7 | +2.08 | -1.04 | -189 | -3153 | 3/101 (+1.76) | +1.66 | +0.41 [+0.03,+0.81] | STACK-NEG | 1.00 | Y | 0.07 | 12/12 | 0.75 |
| SM | THEN60s(iplFVG~15s+OB~45s) / c2_far~F0.7 | +4.89 | +1.12 | +3689 | +1935 | 3/101 (+3.50) | +3.69 | +1.21 [-0.21,+2.49] | STRUCTURE | 1.00 | Y | 0.05 | 12/12 | 0.66 |
| SM | THEN60s(iplFVG~30s+OB~30s) / c2_far~F0.7 | +4.18 | +0.94 | +2230 | +764 | 3/101 (+2.99) | +3.51 | +0.67 [-0.25,+1.81] | STRUCTURE | 1.00 | Y | 0.05 | 12/12 | 0.67 |
| SM | THEN300s(iplFVG~30s+OB~45s) / c2_far~F0.7 | +4.04 | +0.63 | +2120 | +671 | 1/101 (+2.90) | +3.69 | +0.35 [-0.77,+1.47] | STRUCTURE | 1.00 | Y | 0.05 | 12/12 | 0.69 |
| MV | THEN60s(iplFVG~30s+OB~30s) / c2_far~F0.7 | +3.99 | +0.25 | +nan | +nan | 32/101 (+3.89) | +3.58 | +0.41 [-0.20,+1.13] | STRUCTURE | 1.00 | Y | 0.03 | 12/12 | 0.54 |
| MV | THEN300s(iplFVG~1m+OB~30s) / c2_far~F0.7 | +3.98 | +0.67 | +nan | +nan | 1/101 (+3.44) | +3.58 | +0.40 [-0.14,+0.92] | STRUCTURE | 1.00 | Y | 0.03 | 12/12 | 0.58 |
| SM | THEN60s(iplFVG~15s+OB~45s) / b_far~F0.7 | +3.95 | +0.54 | +3526 | +1903 | 9/101 (+3.14) | +2.68 | +1.27 [-0.13,+2.59] | STRUCTURE | 1.00 | Y | 0.05 | 12/12 | 0.68 |
| MV | THEN60s(iplFVG~1m+OB~30s) / c2_far~F0.7 | +3.93 | +0.75 | +nan | +nan | 3/101 (+3.44) | +3.58 | +0.35 [-0.22,+0.92] | STRUCTURE | 1.00 | Y | 0.03 | 12/12 | 0.58 |
| MV | THEN300s(iplFVG~45s+OB~30s) / c2_far~F0.7 | +3.90 | +0.81 | +nan | +nan | 17/101 (+3.62) | +3.58 | +0.32 [+0.11,+0.52] | STRUCTURE | 1.00 | Y | 0.03 | 12/12 | 0.56 |
| MV | THEN300s(iplFVG~30s+OB~30s) / c2_far~F0.7 | +3.86 | +0.34 | +nan | +nan | 27/101 (+3.69) | +3.58 | +0.28 [-0.05,+0.65] | STRUCTURE | 1.00 | Y | 0.03 | 12/12 | 0.56 |
| MV | THEN60s(iplFVG~45s+OB~30s) / c2_far~F0.7 | +3.75 | +0.42 | +nan | +nan | 32/101 (+3.62) | +3.58 | +0.17 [-0.31,+0.64] | STRUCTURE | 1.00 | Y | 0.03 | 12/12 | 0.55 |
| SM | THEN60s(iplFVG~30s+OB~45s) / c2_far~F0.7 | +3.70 | +0.05 | +1960 | +277 | 13/101 (+3.19) | +3.69 | +0.02 [-1.83,+1.66] | STRUCTURE | 1.00 | Y | 0.05 | 12/12 | 0.79 |
| MV | THEN60s(iplFVG~45s+OB~30s) / b_far~F0.7 | +3.56 | +0.58 | +nan | +nan | 31/101 (+3.41) | +2.86 | +0.71 [+0.15,+1.36] | STRUCTURE | 1.00 | Y | 0.03 | 12/12 | 0.62 |
| MV | THEN60s(iplFVG~30s+OB~30s) / b_far~F0.7 | +3.54 | -0.05 | +nan | +nan | 71/101 (+3.63) | +2.86 | +0.68 [+0.08,+1.36] | STRUCTURE | 1.00 | Y | 0.03 | 12/12 | 0.60 |
| MV | THEN300s(iplFVG~30s+OB~30s) / b_far~F0.7 | +3.37 | +0.04 | +nan | +nan | 42/101 (+3.31) | +2.86 | +0.51 [+0.17,+0.92] | STRUCTURE | 1.00 | Y | 0.03 | 12/12 | 0.63 |
| PE | THEN60s(FVG~15s+OB~1m) / c2_far~F0.7 | +3.34 | +0.93 | +1702 | +662 | 1/101 (+2.63) | +2.82 | +0.52 [-0.35,+1.35] | STRUCTURE | 1.00 | Y | 0.02 | 12/12 | 0.67 |
| HM | THEN60s(iplFVG~30s+iFVG~30s) / c2_far~F0.7 | +3.33 | +0.17 | +2026 | +1307 | 9/101 (+3.00) | +2.74 | +0.59 [+0.06,+1.02] | STRUCTURE | 1.00 | Y | 0.45 | 12/12 | 0.65 |
| HM | THEN60s(iplFVG~30s+iFVG~30s) / c2_mid~F0.7 | +3.16 | +0.56 | +6834 | +6039 | 8/101 (+2.77) | +2.67 | +0.49 [+0.04,+0.87] | STRUCTURE | 1.00 | Y | 0.45 | 12/12 | 0.67 |
| HM | THEN300s(iFVG~30s+OB~30s) / c2_far~F0.7 | +3.08 | +0.03 | +4425 | +2778 | 2/101 (+2.50) | +2.87 | +0.20 [-0.11,+0.51] | STRUCTURE | 1.00 | Y | 0.45 | 12/12 | 0.61 |
| HM | THEN60s(iFVG~30s+OB~30s) / c2_mid~F0.7 | +3.05 | +0.06 | +4606 | +3774 | 7/101 (+2.65) | +2.67 | +0.38 [-0.15,+0.86] | STRUCTURE | 1.00 | Y | 0.45 | 12/12 | 0.57 |
| HM | THEN60s(FVG~15s+iFVG~30s) / c2_far~F0.7 | +3.04 | -0.06 | +3542 | +2522 | 12/101 (+2.74) | +2.74 | +0.30 [+0.07,+0.57] | STRUCTURE | 1.00 | Y | 0.45 | 12/12 | 0.63 |
| MA | THEN60s(FVG~15s+FVG~3m) / c2_far~F0.7 | +2.95 | -0.52 | +nan | +nan | 10/101 (+2.42) | +2.16 | +0.79 [-0.59,+2.19] | STRUCTURE | 1.00 | Y | 0.48 | 12/12 | 0.71 |
| HM | THEN60s(FVG~15s+OB~45s) / c2_far~F0.7 | +2.80 | -0.09 | +6113 | +5823 | 28/101 (+2.62) | +2.71 | +0.08 [-0.90,+1.03] | STRUCTURE | 1.00 | Y | 0.45 | 12/12 | 0.62 |
| PE | THEN60s(FVG~15s+FVG~2m) / c2_mid~F0.7 | +2.79 | +0.39 | +359 | +961 | 14/101 (+2.53) | +2.21 | +0.59 [-0.34,+1.63] | STRUCTURE | 1.00 | Y | 0.02 | 12/12 | 0.71 |
| KB | THEN60s(iplFVG~1m+iFVG~15s) / c2_far~F0.7 | +2.77 | +0.23 | +822 | +798 | 3/201 (+2.29) | +2.50 | +0.26 [-0.25,+0.81] | STRUCTURE | 1.00 | Y | 0.23 | 12/12 | 0.63 |
| SM | THEN60s(iplFVG~30s+OB~45s) / b_far~F0.7 | +2.74 | -0.70 | +1707 | +271 | 59/101 (+2.80) | +2.68 | +0.06 [-1.78,+1.72] | STRUCTURE | 1.00 | Y | 0.05 | 12/12 | 0.85 |
| HM | THEN60s(FVG~15s+OB~45s) / c2_mid~F0.7 | +2.70 | -0.07 | +2862 | +4166 | 28/101 (+2.55) | +2.49 | +0.21 [-0.85,+1.07] | STRUCTURE | 1.00 | Y | 0.45 | 12/12 | 0.59 |
| MA | THEN60s(FVG~15s+OB~1m) / c2_mid~F0.7 | +2.35 | -1.38 | +nan | +nan | 27/101 (+2.10) | +2.06 | +0.29 [-1.43,+1.93] | STRUCTURE | 1.00 | Y | 0.48 | 12/12 | 0.67 |
| PB | THEN60s(iplFVG~15s+iFVG~15s) / c2_far~F0.7 | +2.28 | -0.99 | +nan | +nan | 27/101 (+2.13) | +1.96 | +0.32 [+0.12,+0.53] | STRUCTURE | 1.00 | Y | 0.30 | 12/12 | 0.65 |
| KB | THEN60s(iFVG~15s+FVG~2m) / b_mid~F0.7 | +2.23 | +0.65 | +363 | +664 | 36/201 (+2.04) | +1.92 | +0.31 [-0.23,+0.83] | STRUCTURE | 1.00 | Y | 0.23 | 12/12 | 0.83 |
| PB | THEN60s(iplFVG~30s+iFVG~15s) / c2_far~F0.7 | +2.06 | -1.04 | +nan | +nan | 55/101 (+2.10) | +1.96 | +0.09 [-0.14,+0.29] | STRUCTURE | 1.00 | Y | 0.30 | 12/12 | 0.68 |
| PB | THEN60s(iplFVG~15s+FVG~45s) / c2_mid~F0.7 | +2.03 | -1.04 | +nan | +nan | 38/101 (+1.94) | +1.57 | +0.46 [-0.52,+1.43] | STRUCTURE | 1.00 | Y | 0.30 | 12/12 | 0.87 |
| PB | THEN300s(iplFVG~30s+iFVG~15s) / c2_far~F0.7 | +2.03 | -1.03 | +nan | +nan | 51/101 (+2.02) | +1.96 | +0.06 [-0.17,+0.25] | STRUCTURE | 1.00 | Y | 0.30 | 12/12 | 0.68 |
| PB | THEN60s(iFVG~15s+FVG~45s) / c2_far~F0.7 | +1.97 | -1.27 | +nan | +nan | 12/101 (+1.67) | +1.96 | +0.00 [-1.00,+1.12] | STRUCTURE | 1.00 | Y | 0.30 | 12/12 | 0.89 |
| PB | THEN60s(iplFVG~15s+iFVG~15s) / c2_mid~F0.7 | +1.86 | -1.26 | +nan | +nan | 69/101 (+1.97) | +1.60 | +0.26 [-0.12,+0.55] | STRUCTURE | 1.00 | Y | 0.30 | 12/12 | 0.74 |

Totals: 74 unit-checked candidate rows; INFO-CANDIDATE 22, STRUCTURE 34, STACK-NEG 18.

## Stage POOL  (2026-10-31T03:21Z)

auto


## Stage POOL  (2026-10-31T03:24Z)

auto

### SM: 1238 combinations x 17 variants = 21046 cells; PRE+X' selection, one recent look on the top 12 cells (30 cell x variant rows)
White RC over the stage's cells (PRE+X', all-signal differential vs floor): p=0.156 (K=16630). Tiers: BEST-AVAILABLE 30.

| AND-set (timeframes in the member names) | variant | fill L6M | n | add vs floor on fired L6M [per contract] | HOLD | L3M | PRE | X' | ALL-signal add L6M | best member (all-signal) L6M | placebo p | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AND(OB|45s+pd50|10m) | b_near|F0.7 | 31.5% | 99 | +12.64 (MDE 7.16) | +12.80 | +17.50 | +13.18 | +11.49 | +3.30 | +3.36 | 0.199 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|45s+pd50|10m) | c2_near|F0.7 | 31.5% | 99 | +12.64 (MDE 7.16) | +12.80 | +17.50 | +13.19 | +11.49 | +3.30 | +3.36 | 0.204 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|45s+pd50|10m) | c1|F0.7 | 31.5% | 99 | +12.51 (MDE 7.14) | +12.73 | +17.43 | +13.31 | +10.82 | +3.25 | +3.31 | 0.209 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|45s+pd50|10m) | a|F0.7 | 31.5% | 99 | +12.51 (MDE 7.14) | +12.73 | +17.43 | +13.30 | +10.77 | +3.25 | +3.31 | 0.204 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|30s+pd50|10m) | c2_near|F0.7 | 32.5% | 102 | +12.44 (MDE 6.97) | +12.56 | +17.16 | +13.43 | +11.23 | +3.36 | +3.36 | 0.204 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|30s+pd50|10m) | b_near|F0.7 | 32.5% | 102 | +12.44 (MDE 6.97) | +12.56 | +17.16 | +13.42 | +11.23 | +3.36 | +3.36 | 0.204 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|1m+pd50|10m) | c2_near|F0.7 | 29.0% | 91 | +12.43 (MDE 7.59) | +12.52 | +17.45 | +13.33 | +11.31 | +2.89 | +3.36 | 0.259 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|1m+pd50|10m) | b_near|F0.7 | 29.0% | 91 | +12.43 (MDE 7.59) | +12.52 | +17.45 | +13.32 | +11.31 | +2.89 | +3.36 | 0.254 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|45s+pd50|10m) | b_near|F0.7 | 31.8% | 100 | +12.37 (MDE 7.11) | +12.50 | +17.23 | +13.53 | +11.09 | +3.25 | +3.36 | 0.199 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|45s+pd50|10m) | c2_near|F0.7 | 31.8% | 100 | +12.37 (MDE 7.11) | +12.50 | +17.23 | +13.54 | +11.10 | +3.25 | +3.36 | 0.204 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|30s+pd50|10m) | a|F0.7 | 32.5% | 102 | +12.28 (MDE 6.96) | +12.43 | +17.07 | +13.12 | +10.57 | +3.31 | +3.31 | 0.224 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|30s+pd50|10m) | c1|F0.7 | 32.5% | 102 | +12.28 (MDE 6.96) | +12.43 | +17.07 | +13.13 | +10.62 | +3.31 | +3.31 | 0.229 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |

Plain sentence (best by all-signal gain): requiring FVG|30s AND CFA:vwap|day before the signal enters (c2_far|F0.7) adds +5.91 pts per contract on the 71.0% of signals it fires on in the last 6 months (MDE 4.04), but +4.13 pts per signal over ALL signals (the skipped signals' floor P&L counted against it) vs the best member +3.03; tier BEST-AVAILABLE.


## Stage POOL  (2026-10-31T03:28Z)

auto

### DN: 1238 combinations x 17 variants = 21046 cells; PRE+X' selection, one recent look on the top 10 cells (30 cell x variant rows)
White RC over the stage's cells (PRE+X', all-signal differential vs floor): p=0.002 (K=16370). Tiers: BEST-AVAILABLE 30.

| AND-set (timeframes in the member names) | variant | fill L6M | n | add vs floor on fired L6M [per contract] | HOLD | L3M | PRE | X' | ALL-signal add L6M | best member (all-signal) L6M | placebo p | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AND(OB|1m+pd50|5m) | c2_near|F0.7 | 27.0% | 189 | +14.40 (MDE 3.18) | +15.01 | +16.31 | +15.42 | +12.73 | +3.55 | +3.79 | 0.194 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|1m+pd50|5m) | b_near|F0.7 | 27.0% | 189 | +14.40 (MDE 3.18) | +15.01 | +16.31 | +15.36 | +12.69 | +3.55 | +3.79 | 0.194 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|1m+pd50|5m) | c1|F0.7 | 26.8% | 188 | +14.24 (MDE 3.21) | +14.79 | +16.16 | +15.24 | +12.29 | +3.49 | +3.71 | 0.169 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|1m+pd50|5m) | a|F0.7 | 26.8% | 188 | +14.24 (MDE 3.21) | +14.79 | +16.16 | +15.20 | +12.29 | +3.49 | +3.71 | 0.169 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(iFVG|2m+pd50|5m) | c2_near|F0.7 | 26.7% | 187 | +14.08 (MDE 3.08) | +14.71 | +16.47 | +15.35 | +12.92 | +3.43 | +3.79 | 0.244 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(iFVG|2m+pd50|5m) | b_near|F0.7 | 26.7% | 187 | +14.08 (MDE 3.08) | +14.71 | +16.47 | +15.32 | +12.88 | +3.43 | +3.79 | 0.244 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|30s+pd50|5m) | b_near|F0.7 | 27.1% | 190 | +14.05 (MDE 3.21) | +14.72 | +15.35 | +15.16 | +12.40 | +3.48 | +3.79 | 0.184 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|30s+pd50|5m) | c2_near|F0.7 | 27.1% | 190 | +14.05 (MDE 3.21) | +14.72 | +15.35 | +15.19 | +12.44 | +3.48 | +3.79 | 0.184 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|15s+pd50|5m) | c2_near|F0.7 | 27.1% | 190 | +13.92 (MDE 3.11) | +14.59 | +15.35 | +15.45 | +13.12 | +3.44 | +3.79 | 0.328 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|15s+pd50|5m) | b_near|F0.7 | 27.1% | 190 | +13.92 (MDE 3.11) | +14.59 | +15.35 | +15.41 | +13.08 | +3.44 | +3.79 | 0.328 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(iFVG|2m+ote705|2m) | c2_near|F0.7 | 30.5% | 214 | +13.81 (MDE 3.51) | +13.90 | +14.78 | +14.70 | +10.33 | +3.90 | +4.09 | 0.015 | BEST-AVAILABLE | <=best_member_L6M,<=best_member_PRE+X |
| AND(iFVG|2m+ote705|2m) | b_near|F0.7 | 30.5% | 214 | +13.81 (MDE 3.51) | +13.90 | +14.78 | +14.70 | +10.30 | +3.90 | +4.09 | 0.015 | BEST-AVAILABLE | <=best_member_L6M,<=best_member_PRE+X |

Plain sentence (best by all-signal gain): requiring iFVG|2m AND ote705|2m before the signal enters (c2_near|F0.7) adds +13.81 pts per contract on the 30.5% of signals it fires on in the last 6 months (MDE 3.51), but +3.90 pts per signal over ALL signals (the skipped signals' floor P&L counted against it) vs the best member +4.09; tier BEST-AVAILABLE.


## Stage POOL  (2026-10-31T03:31Z)

auto

### HM: 1238 combinations x 17 variants = 21046 cells; PRE+X' selection, one recent look on the top 11 cells (30 cell x variant rows)
White RC over the stage's cells (PRE+X', all-signal differential vs floor): p=0.008 (K=16630). Tiers: BEST-AVAILABLE 30.

| AND-set (timeframes in the member names) | variant | fill L6M | n | add vs floor on fired L6M [per contract] | HOLD | L3M | PRE | X' | ALL-signal add L6M | best member (all-signal) L6M | placebo p | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AND(FVG|15s+ote79|15s) | c1|F0.7 | 56.8% | 516 | +5.54 (MDE 1.80) | +5.64 | +6.49 | +7.84 | +5.71 | +3.02 | +2.96 | 0.408 | BEST-AVAILABLE | placebo,<=best_member_PRE+X |
| AND(FVG|15s+ote79|15s) | a|F0.7 | 56.8% | 516 | +5.54 (MDE 1.80) | +5.63 | +6.49 | +7.73 | +5.71 | +3.01 | +2.96 | 0.408 | BEST-AVAILABLE | placebo,<=best_member_PRE+X |
| AND(OB|3m+ote79|15s) | c2_near|F0.7 | 56.2% | 511 | +5.52 (MDE 1.88) | +5.58 | +6.63 | +7.92 | +5.76 | +2.97 | +3.03 | 0.313 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|3m+ote79|15s) | b_near|F0.7 | 56.2% | 511 | +5.51 (MDE 1.88) | +5.56 | +6.62 | +7.81 | +5.76 | +2.97 | +3.03 | 0.343 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|45s+ote79|15s) | c2_near|F0.7 | 57.2% | 520 | +5.45 (MDE 1.87) | +5.51 | +6.57 | +7.87 | +5.61 | +3.00 | +3.03 | 0.408 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|45s+ote79|15s) | b_near|F0.7 | 57.2% | 520 | +5.45 (MDE 1.87) | +5.49 | +6.57 | +7.76 | +5.61 | +2.99 | +3.03 | 0.438 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(BRK|30s+ote79|15s) | c2_near|F0.7 | 56.3% | 512 | +5.44 (MDE 1.91) | +5.50 | +6.62 | +7.87 | +5.58 | +2.94 | +3.03 | 0.393 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|1m+ote79|15s) | c2_near|F0.7 | 56.0% | 509 | +5.43 (MDE 1.91) | +5.49 | +6.56 | +7.87 | +5.64 | +2.91 | +3.03 | 0.398 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|30s+ote79|15s) | c2_near|F0.7 | 57.5% | 523 | +5.43 (MDE 1.87) | +5.49 | +6.61 | +7.85 | +5.63 | +3.00 | +3.03 | 0.438 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|1m+ote79|15s) | b_near|F0.7 | 56.0% | 509 | +5.42 (MDE 1.91) | +5.48 | +6.55 | +7.76 | +5.64 | +2.91 | +3.03 | 0.433 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|30s+ote79|15s) | b_near|F0.7 | 57.5% | 523 | +5.42 (MDE 1.87) | +5.48 | +6.60 | +7.74 | +5.62 | +3.00 | +3.03 | 0.468 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|3m+ote79|15s) | c1|F0.7 | 56.1% | 510 | +5.41 (MDE 1.80) | +5.48 | +6.48 | +7.94 | +5.70 | +2.91 | +2.96 | 0.363 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |

Plain sentence (best by all-signal gain): requiring FVG|15s AND ote79|15s before the signal enters (c1|F0.7) adds +5.54 pts per contract on the 56.8% of signals it fires on in the last 6 months (MDE 1.80), but +3.02 pts per signal over ALL signals (the skipped signals' floor P&L counted against it) vs the best member +2.96; tier BEST-AVAILABLE.


## Stage POOL  (2026-10-31T03:39Z)

auto

### KB: 1238 combinations x 17 variants = 21046 cells; PRE+X' selection, one recent look on the top 21 cells (30 cell x variant rows)
White RC over the stage's cells (PRE+X', all-signal differential vs floor): p=0.194 (K=16574). Tiers: BEST-AVAILABLE 30.

| AND-set (timeframes in the member names) | variant | fill L6M | n | add vs floor on fired L6M [per contract] | HOLD | L3M | PRE | X' | ALL-signal add L6M | best member (all-signal) L6M | placebo p | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AND(OB|45s+CFA:b1|avwap) | c2_far|F0.7 | 42.9% | 539 | +5.26 (MDE 1.10) | +5.24 | +5.83 | +5.79 | +4.80 | +1.75 | +1.77 | 1.000 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(iFVG|15s+CFA:vwap|avwap+CFA:vwap|day) | c2_far|F0.7 | 59.3% | 746 | +5.01 (MDE 1.30) | +5.06 | +5.90 | +4.83 | +3.89 | +2.70 | +2.50 | 0.934 | BEST-AVAILABLE | placebo |
| AND(iFVG|15s+CFA:vwap|day) | c2_far|F0.7 | 61.7% | 775 | +4.76 (MDE 1.04) | +4.81 | +5.52 | +4.94 | +3.82 | +2.69 | +2.50 | 0.902 | BEST-AVAILABLE | placebo |
| AND(FVG|2m+CFA:vwap|day) | c2_far|F0.7 | 45.3% | 569 | +4.46 (MDE 1.26) | +4.47 | +4.82 | +5.85 | +4.70 | +1.54 | +1.62 | 1.000 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(iFVG|15s+CFA:vwap|day) | c2_mid|F0.7 | 62.3% | 783 | +4.45 (MDE 0.83) | +4.35 | +5.18 | +4.81 | +3.77 | +2.53 | +2.19 | 0.951 | BEST-AVAILABLE | placebo |
| AND(iFVG|15s+CFA:vwap|avwap+CFA:vwap|day) | c2_mid|F0.7 | 60.1% | 755 | +4.43 (MDE 1.10) | +4.35 | +5.12 | +4.67 | +3.80 | +2.40 | +2.19 | 0.967 | BEST-AVAILABLE | placebo |
| AND(iFVG|15s+CFA:vwap|avwap) | c2_far|F0.7 | 66.0% | 830 | +4.32 (MDE 1.18) | +4.43 | +5.15 | +4.42 | +3.37 | +2.63 | +2.50 | 0.934 | BEST-AVAILABLE | placebo |
| AND(FVG|2m+CFA:b1|day) | c2_far|F0.7 | 49.6% | 624 | +4.22 (MDE 1.15) | +4.32 | +4.61 | +5.47 | +4.53 | +1.65 | +1.62 | 1.000 | BEST-AVAILABLE | placebo,<=best_member_PRE+X |
| AND(FVG|2m+CFA:vwap|avwap) | c2_far|F0.7 | 49.2% | 618 | +4.21 (MDE 1.34) | +4.36 | +4.61 | +5.40 | +4.65 | +1.62 | +1.80 | 0.984 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(iFVG|30s+CFA:b1|day) | c2_far|F0.7 | 62.3% | 783 | +4.14 (MDE 1.19) | +4.27 | +4.50 | +4.72 | +2.89 | +2.33 | +2.32 | 0.984 | BEST-AVAILABLE | placebo |
| AND(FVG|15s+CFA:b1|day) | c2_far|F0.7 | 64.6% | 812 | +4.11 (MDE 1.32) | +4.05 | +4.43 | +4.43 | +3.43 | +2.51 | +2.61 | 0.820 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|15s+CFA:b1|avwap) | c2_far|F0.7 | 67.6% | 850 | +4.08 (MDE 1.21) | +4.06 | +4.59 | +4.03 | +3.45 | +2.63 | +2.61 | 0.656 | BEST-AVAILABLE | placebo,<=best_member_PRE+X |

Plain sentence (best by all-signal gain): requiring iFVG|15s AND CFA:vwap|avwap AND CFA:vwap|day before the signal enters (c2_far|F0.7) adds +5.01 pts per contract on the 59.3% of signals it fires on in the last 6 months (MDE 1.30), but +2.70 pts per signal over ALL signals (the skipped signals' floor P&L counted against it) vs the best member +2.50; tier BEST-AVAILABLE.


## Stage POOL  (2026-10-31T03:46Z)

auto

### PE: 1238 combinations x 17 variants = 21046 cells; PRE+X' selection, one recent look on the top 17 cells (30 cell x variant rows)
White RC over the stage's cells (PRE+X', all-signal differential vs floor): p=0.002 (K=16718). Tiers: BEST-AVAILABLE 30.

| AND-set (timeframes in the member names) | variant | fill L6M | n | add vs floor on fired L6M [per contract] | HOLD | L3M | PRE | X' | ALL-signal add L6M | best member (all-signal) L6M | placebo p | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AND(OB|1m+CFA:val|sw15) | c2_far|F0.7 | 39.5% | 472 | +7.92 (MDE 1.86) | +8.00 | +8.67 | +8.39 | +7.31 | +2.24 | +2.50 | 0.770 | BEST-AVAILABLE | placebo,<=best_member_L6M |
| AND(OB|1m+CFA:vah|sw15) | c2_far|F0.7 | 41.2% | 492 | +7.89 (MDE 2.09) | +7.86 | +8.77 | +9.06 | +7.39 | +2.46 | +2.50 | 0.475 | BEST-AVAILABLE | placebo,<=best_member_L6M |
| AND(OB|1m+CFA:poc|sw15) | c2_far|F0.7 | 41.4% | 494 | +7.11 (MDE 1.87) | +7.13 | +7.44 | +8.76 | +7.42 | +2.15 | +2.50 | 0.820 | BEST-AVAILABLE | placebo,<=best_member_L6M |
| AND(OB|1m+CFA:vwap|avwap+CFA:vwap|day) | c2_far|F0.7 | 49.8% | 595 | +6.92 (MDE 1.70) | +6.91 | +7.45 | +7.11 | +6.17 | +2.83 | +2.50 | 0.984 | BEST-AVAILABLE | placebo,<=best_member_PRE+X |
| AND(OB|1m+CFA:vwap|day) | c2_far|F0.7 | 50.4% | 602 | +6.79 (MDE 1.64) | +6.79 | +7.46 | +6.76 | +5.59 | +2.80 | +2.50 | 0.984 | BEST-AVAILABLE | placebo |
| AND(OB|1m+CFA:vwap|avwap) | c2_far|F0.7 | 50.3% | 600 | +6.73 (MDE 1.71) | +6.69 | +7.20 | +6.50 | +5.61 | +2.77 | +2.50 | 0.984 | BEST-AVAILABLE | placebo,<=best_member_PRE+X |
| AND(OB|1m+CFA:vwap|avwap+CFA:b1|avwap) | c2_far|F0.7 | 50.3% | 600 | +6.73 (MDE 1.71) | +6.69 | +7.20 | +6.50 | +5.61 | +2.77 | +2.50 | 0.984 | BEST-AVAILABLE | placebo,<=best_member_PRE+X |
| AND(OB|1m+CFA:b1|avwap+CFA:vwap|day) | c2_far|F0.7 | 50.6% | 604 | +6.72 (MDE 1.57) | +6.70 | +7.24 | +6.82 | +5.71 | +2.78 | +2.50 | 0.967 | BEST-AVAILABLE | placebo,<=best_member_PRE+X |
| AND(FVG|2m+CFA:vah|sw15) | c2_mid|F0.7 | 44.6% | 532 | +6.58 (MDE 2.46) | +6.64 | +6.12 | +7.37 | +6.72 | +2.17 | +2.14 | 0.689 | BEST-AVAILABLE | placebo |
| AND(FVG|15s+CFA:val|sw15) | c2_far|F0.7 | 52.9% | 632 | +6.06 (MDE 1.56) | +6.31 | +6.46 | +7.43 | +7.28 | +2.62 | +2.82 | 0.820 | BEST-AVAILABLE | placebo,<=best_member_L6M |
| AND(FVG|15s+CFA:val|sw15) | c2_mid|F0.7 | 53.5% | 639 | +6.03 (MDE 1.82) | +6.26 | +6.73 | +7.18 | +7.18 | +2.64 | +2.21 | 0.705 | BEST-AVAILABLE | placebo |
| AND(FVG|15s+CFA:vah|sw15) | c2_far|F0.7 | 55.4% | 662 | +5.96 (MDE 1.91) | +6.12 | +6.98 | +7.35 | +7.03 | +2.74 | +2.82 | 0.721 | BEST-AVAILABLE | placebo,<=best_member_L6M |

Plain sentence (best by all-signal gain): requiring FVG|15s AND CFA:vwap|day before the signal enters (c2_far|F0.7) adds +4.56 pts per contract on the 73.5% of signals it fires on in the last 6 months (MDE 1.35), but +3.10 pts per signal over ALL signals (the skipped signals' floor P&L counted against it) vs the best member +2.82; tier BEST-AVAILABLE.


## Stage POOL  (2026-10-31T03:51Z)

auto

### ST: 1238 combinations x 17 variants = 21046 cells; PRE+X' selection, one recent look on the top 14 cells (30 cell x variant rows)
White RC over the stage's cells (PRE+X', all-signal differential vs floor): p=0.044 (K=16630). Tiers: BEST-AVAILABLE 30.

| AND-set (timeframes in the member names) | variant | fill L6M | n | add vs floor on fired L6M [per contract] | HOLD | L3M | PRE | X' | ALL-signal add L6M | best member (all-signal) L6M | placebo p | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AND(OB|1m+pd50|5m) | c2_near|F0.7 | 25.8% | 324 | +9.66 (MDE 2.64) | +9.66 | +10.03 | +10.42 | +11.35 | +1.56 | +1.57 | 0.055 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|30s+pd50|5m) | c2_near|F0.7 | 26.0% | 326 | +9.65 (MDE 2.62) | +9.62 | +10.06 | +10.51 | +11.26 | +1.57 | +1.87 | 0.065 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(iplFVG|30s+pd50|5m) | c2_near|F0.7 | 24.9% | 313 | +9.64 (MDE 2.72) | +9.64 | +10.13 | +10.35 | +11.43 | +1.46 | +1.57 | 0.100 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|1m+pd50|5m) | b_near|F0.7 | 25.9% | 325 | +9.62 (MDE 2.63) | +9.62 | +9.95 | +10.39 | +11.32 | +1.56 | +1.57 | 0.050 | BEST-AVAILABLE | <=best_member_L6M,<=best_member_PRE+X |
| AND(OB|45s+pd50|5m) | c2_near|F0.7 | 25.2% | 317 | +9.62 (MDE 2.74) | +9.64 | +10.01 | +10.34 | +11.18 | +1.49 | +1.57 | 0.085 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|30s+pd50|5m) | b_near|F0.7 | 26.0% | 327 | +9.61 (MDE 2.61) | +9.58 | +9.98 | +10.48 | +11.20 | +1.57 | +1.57 | 0.055 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|30s+pd50|5m) | c1|F0.7 | 25.9% | 325 | +9.61 (MDE 2.63) | +9.56 | +10.00 | +10.17 | +11.29 | +1.55 | +1.54 | 0.035 | BEST-AVAILABLE | <=best_member_PRE+X |
| AND(iplFVG|30s+pd50|5m) | c1|F0.7 | 24.8% | 312 | +9.61 (MDE 2.73) | +9.61 | +10.07 | +10.15 | +11.57 | +1.44 | +1.54 | 0.090 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|1m+pd50|5m) | c1|F0.7 | 25.7% | 323 | +9.60 (MDE 2.65) | +9.59 | +9.94 | +10.11 | +11.38 | +1.54 | +1.54 | 0.035 | BEST-AVAILABLE | <=best_member_L6M,<=best_member_PRE+X |
| AND(OB|30s+pd50|5m) | a|F0.7 | 25.9% | 325 | +9.60 (MDE 2.63) | +9.55 | +9.99 | +10.12 | +11.24 | +1.55 | +1.54 | 0.035 | BEST-AVAILABLE | <=best_member_PRE+X |
| AND(iplFVG|30s+pd50|5m) | a|F0.7 | 24.8% | 312 | +9.60 (MDE 2.73) | +9.60 | +10.05 | +10.11 | +11.55 | +1.44 | +1.54 | 0.090 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(iplFVG|30s+pd50|5m) | b_near|F0.7 | 25.0% | 314 | +9.59 (MDE 2.70) | +9.60 | +10.05 | +10.32 | +11.40 | +1.46 | +1.57 | 0.095 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |

Plain sentence (best by all-signal gain): requiring OB|30s AND CFA:vwap|avwap AND CFA:b1|avwap before the signal enters (c2_far|F0.7) adds +5.24 pts per contract on the 49.4% of signals it fires on in the last 6 months (MDE 1.61), but +2.07 pts per signal over ALL signals (the skipped signals' floor P&L counted against it) vs the best member +1.98; tier BEST-AVAILABLE.


## Stage POOL  (2026-10-31T04:00Z)

auto

### MV: 1238 combinations x 17 variants = 21046 cells; PRE+X' selection, one recent look on the top 8 cells (30 cell x variant rows)
White RC over the stage's cells (PRE+X', all-signal differential vs floor): p=0.002 (K=16590). Tiers: BEST-AVAILABLE 30.

| AND-set (timeframes in the member names) | variant | fill L6M | n | add vs floor on fired L6M [per contract] | HOLD | L3M | PRE | X' | ALL-signal add L6M | best member (all-signal) L6M | placebo p | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AND(OB|30s+rnd50) | c2_near|F0.7 | 69.9% | 791 | +9.58 (MDE 1.81) | +9.60 | +9.49 | +9.88 | +10.27 | +6.64 | +6.70 | 0.731 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|1m+rnd50) | c2_near|F0.7 | 69.5% | 786 | +9.57 (MDE 1.81) | +9.58 | +9.50 | +9.87 | +10.02 | +6.58 | +6.70 | 0.741 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|30s+rnd50) | b_near|F0.7 | 69.9% | 791 | +9.56 (MDE 1.82) | +9.58 | +9.48 | +9.84 | +10.21 | +6.63 | +6.69 | 0.716 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|1m+rnd50) | b_near|F0.7 | 69.5% | 786 | +9.55 (MDE 1.82) | +9.56 | +9.49 | +9.83 | +9.96 | +6.57 | +6.69 | 0.731 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(iFVG|1m+rnd50) | c2_near|F0.7 | 69.1% | 781 | +9.54 (MDE 1.81) | +9.55 | +9.48 | +9.77 | +10.04 | +6.51 | +6.70 | 0.697 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(iplFVG|1m+rnd50) | c2_near|F0.7 | 68.5% | 775 | +9.53 (MDE 1.82) | +9.54 | +9.52 | +9.92 | +9.82 | +6.46 | +6.70 | 0.672 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(iFVG|1m+rnd50) | b_near|F0.7 | 69.1% | 781 | +9.52 (MDE 1.82) | +9.53 | +9.47 | +9.73 | +9.98 | +6.50 | +6.69 | 0.667 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(iplFVG|1m+rnd50) | b_near|F0.7 | 68.5% | 775 | +9.51 (MDE 1.83) | +9.52 | +9.51 | +9.88 | +9.78 | +6.45 | +6.69 | 0.657 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|45s+rnd50) | c2_near|F0.7 | 69.1% | 781 | +9.47 (MDE 1.78) | +9.49 | +9.35 | +9.87 | +10.09 | +6.47 | +6.70 | 0.786 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|2m+rnd50) | c2_near|F0.7 | 68.1% | 770 | +9.46 (MDE 1.84) | +9.49 | +9.45 | +9.70 | +10.06 | +6.35 | +6.70 | 0.786 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(OB|45s+rnd50) | c2_near|F0.7 | 68.6% | 776 | +9.45 (MDE 1.78) | +9.47 | +9.40 | +9.77 | +10.18 | +6.41 | +6.70 | 0.751 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|45s+rnd50) | b_near|F0.7 | 69.1% | 781 | +9.44 (MDE 1.78) | +9.47 | +9.34 | +9.83 | +10.03 | +6.46 | +6.69 | 0.771 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |

Plain sentence (best by all-signal gain): requiring OB|30s AND rnd50 before the signal enters (c2_near|F0.7) adds +9.58 pts per contract on the 69.9% of signals it fires on in the last 6 months (MDE 1.81), but +6.64 pts per signal over ALL signals (the skipped signals' floor P&L counted against it) vs the best member +6.70; tier BEST-AVAILABLE.


## Stage POOL  (2026-10-31T04:14Z)

auto

### PB: 1238 combinations x 17 variants = 21046 cells; PRE+X' selection, one recent look on the top 10 cells (30 cell x variant rows)
White RC over the stage's cells (PRE+X', all-signal differential vs floor): p=0.002 (K=16630). Tiers: BEST-AVAILABLE 29, CANDIDATE 1.

| AND-set (timeframes in the member names) | variant | fill L6M | n | add vs floor on fired L6M [per contract] | HOLD | L3M | PRE | X' | ALL-signal add L6M | best member (all-signal) L6M | placebo p | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AND(FVG|30s+pd50|10m) | c2_near|F0.7 | 28.6% | 248 | +9.91 (MDE 3.50) | +10.00 | +7.81 | +13.45 | +12.13 | +2.14 | +2.14 | 0.682 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|30s+pd50|10m) | b_near|F0.7 | 28.6% | 248 | +9.90 (MDE 3.50) | +9.98 | +7.80 | +13.42 | +12.13 | +2.14 | +2.14 | 0.662 | BEST-AVAILABLE | placebo,<=best_member_PRE+X |
| AND(iFVG|15s+pd50|10m) | c2_near|F0.7 | 28.8% | 249 | +9.87 (MDE 3.51) | +10.03 | +7.75 | +13.66 | +12.14 | +2.14 | +2.14 | 0.697 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(iFVG|15s+pd50|10m) | b_near|F0.7 | 28.8% | 249 | +9.86 (MDE 3.50) | +10.01 | +7.74 | +13.62 | +12.14 | +2.14 | +2.14 | 0.682 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|30s+pd50|10m) | c1|F0.7 | 28.5% | 247 | +9.80 (MDE 3.50) | +9.90 | +7.44 | +13.42 | +11.88 | +2.09 | +2.10 | 0.647 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(iFVG|15s+pd50|10m) | c1|F0.7 | 28.6% | 248 | +9.77 (MDE 3.51) | +9.94 | +7.38 | +13.66 | +11.81 | +2.10 | +2.10 | 0.667 | BEST-AVAILABLE | placebo,<=best_member_PRE+X |
| AND(iFVG|15s+pd50|10m) | a|F0.7 | 28.6% | 248 | +9.76 (MDE 3.51) | +9.93 | +7.38 | +13.63 | +11.81 | +2.10 | +2.09 | 0.652 | BEST-AVAILABLE | placebo,<=best_member_PRE+X |
| AND(FVG|30s+CFA:val|sw15) | c2_mid|F0.7 | 53.5% | 463 | +5.98 (MDE 2.56) | +6.39 | +5.17 | +8.17 | +5.86 | +3.05 | +1.98 | 0.016 | CANDIDATE |  |
| AND(FVG|30s+CFA:poc|sw15+CFA:vwap|day) | c2_mid|F0.7 | 53.3% | 462 | +5.90 (MDE 2.48) | +6.35 | +5.34 | +8.30 | +5.82 | +2.88 | +1.98 | 0.328 | BEST-AVAILABLE | placebo |
| AND(FVG|30s+CFA:b1|avwap+CFA:poc|sw15) | c2_mid|F0.7 | 54.6% | 473 | +5.78 (MDE 2.57) | +6.19 | +5.07 | +8.06 | +5.73 | +2.89 | +2.48 | 0.213 | BEST-AVAILABLE | placebo |
| AND(FVG|30s+CFA:poc|sw15) | c2_mid|F0.7 | 54.8% | 475 | +5.74 (MDE 2.56) | +6.15 | +5.05 | +7.74 | +5.48 | +2.88 | +1.98 | 0.180 | BEST-AVAILABLE | placebo |
| AND(FVG|30s+CFA:vah|sw15) | c2_mid|F0.7 | 54.6% | 473 | +5.71 (MDE 2.68) | +6.03 | +4.97 | +7.83 | +5.32 | +2.84 | +1.98 | 0.148 | BEST-AVAILABLE | placebo |

Plain sentence (best by all-signal gain): requiring FVG|30s AND CFA:val|sw15 before the signal enters (c2_mid|F0.7) adds +5.98 pts per contract on the 53.5% of signals it fires on in the last 6 months (MDE 2.56), but +3.05 pts per signal over ALL signals (the skipped signals' floor P&L counted against it) vs the best member +1.98; tier CANDIDATE.


## Stage POOL  (2026-10-31T04:23Z)

auto

### MA: 1238 combinations x 17 variants = 21046 cells; PRE+X' selection, one recent look on the top 10 cells (30 cell x variant rows)
White RC over the stage's cells (PRE+X', all-signal differential vs floor): p=0.110 (K=16720). Tiers: BEST-AVAILABLE 30.

| AND-set (timeframes in the member names) | variant | fill L6M | n | add vs floor on fired L6M [per contract] | HOLD | L3M | PRE | X' | ALL-signal add L6M | best member (all-signal) L6M | placebo p | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AND(FVG|15s+ote79|2m) | c1|F0.7 | 37.8% | 154 | +10.07 (MDE 2.98) | +9.61 | +11.44 | +10.38 | +6.43 | +3.25 | +3.41 | 0.184 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|15s+ote79|2m) | a|F0.7 | 37.8% | 154 | +10.07 (MDE 2.98) | +9.61 | +11.44 | +10.38 | +6.43 | +3.25 | +3.41 | 0.184 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(CFA:b2|day+ote79|2m) | c1|F0.7 | 38.3% | 156 | +9.66 (MDE 2.69) | +9.24 | +11.12 | +10.78 | +6.24 | +3.15 | +3.41 | 0.368 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(CFA:b2|day+ote79|2m) | a|F0.7 | 38.3% | 156 | +9.66 (MDE 2.69) | +9.24 | +11.12 | +10.78 | +6.24 | +3.15 | +3.41 | 0.363 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(CFA:b2|day+ote79|2m) | b_near|F0.7 | 38.3% | 156 | +9.57 (MDE 2.63) | +9.18 | +11.15 | +10.68 | +6.25 | +3.11 | +3.47 | 0.373 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(CFA:b2|day+ote79|2m) | c2_near|F0.7 | 38.3% | 156 | +9.57 (MDE 2.63) | +9.18 | +11.15 | +10.70 | +6.27 | +3.11 | +3.47 | 0.378 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|15s+ote705|1m) | c1|F0.7 | 48.6% | 198 | +7.72 (MDE 2.75) | +7.24 | +9.04 | +7.15 | +5.31 | +3.27 | +3.25 | 0.060 | BEST-AVAILABLE | placebo,<=best_member_PRE+X |
| AND(FVG|15s+ote705|1m) | a|F0.7 | 48.6% | 198 | +7.69 (MDE 2.75) | +7.21 | +9.02 | +7.14 | +5.28 | +3.26 | +3.24 | 0.065 | BEST-AVAILABLE | placebo,<=best_member_PRE+X |
| AND(CFA:b1|day+ote705|1m) | c1|F0.7 | 45.9% | 187 | +7.67 (MDE 2.67) | +7.11 | +8.27 | +7.10 | +5.42 | +3.01 | +3.25 | 0.144 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(CFA:b1|day+ote705|1m) | a|F0.7 | 45.9% | 187 | +7.64 (MDE 2.67) | +7.08 | +8.25 | +7.10 | +5.38 | +3.00 | +3.24 | 0.149 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|15s+ote705|1m) | c2_near|F0.7 | 48.6% | 198 | +7.63 (MDE 2.71) | +7.12 | +8.91 | +6.99 | +5.10 | +3.22 | +3.25 | 0.070 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |
| AND(FVG|30s+ote705|1m) | c1|F0.7 | 47.7% | 194 | +7.61 (MDE 2.72) | +7.06 | +8.77 | +7.00 | +5.41 | +3.12 | +3.25 | 0.100 | BEST-AVAILABLE | placebo,<=best_member_L6M,<=best_member_PRE+X |

Plain sentence (best by all-signal gain): requiring FVG|15s AND ote705|1m before the signal enters (c1|F0.7) adds +7.72 pts per contract on the 48.6% of signals it fires on in the last 6 months (MDE 2.75), but +3.27 pts per signal over ALL signals (the skipped signals' floor P&L counted against it) vs the best member +3.25; tier BEST-AVAILABLE.

