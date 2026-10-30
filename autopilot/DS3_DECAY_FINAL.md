# DS3_DECAY_FINAL - T-SIGNAL-DECAY: exit when the edge is spent, not when price says so (2026-10-30)
Sections: A invalidation (DS3_DECAY_A_INVALIDATION.md, SD-A), B horizon / decay (DS3_DECAY_B_HORIZON.md, SD-B), C forecast re-score + D combinations and stack (DS3_DECAY_C_RESCORE.md, SD-C). Research only; no live, execution-server or chart change; UNTOUCHED never read; every selection on PRE+X' only with one recent look per group; masks capped 20260206; per contract (1 lot) vs hold-to-bracket on identical entries; measured fills (market exit at the path +0.995 pt; stop-class 1.01, LIVE-P9 2.45; target-fill correction removed on N); the lock-engine stack second.

## Headline
**Keying the exit on the signal instead of on price does not pay for any book. Across the three families (premise invalidation: 1,917 singles + 45,360 combinations on 5 books; horizon / decay: 68 cells x 13 streams; re-scored forecast: 93 cells x 13 scopes) 0 cells are PASS, 0 are CANDIDATE, and the one CANDIDATE-RECENT (CR in section B) is a single-leg stand-in that fails PRE and X'.** Every PRE+X'-selected exit loses to the library bracket per contract in the last 6 months and in HOLD, on M, N and LIVE-P9, and none beats a random exit with the same fire rate and the same time-since-entry distribution at 0.95. The reason is the same in all three: the premise, the age and the forecast do carry some information about how a trade ends (a re-scored P(target) has Brier 0.231 vs 0.251, calibration monotone), but the symmetric 60/60 bracket already pays for it, the exit costs 0.995 pt on 30-70% of trades, and the winners the exit forfeits are almost exactly the losses it saves: P(target | invalidated but held) is within 0-14 points of the all-trade rate. Nothing is written to THP_POLICY.txt and nothing to DS3_THL2_NEEDS.md (no rule is >= 0). D6 already computes every state a rule would need (kb_inside_channel, st_flip, hm_slope, pb_low_lost, bos_against_5m, mins_in_trade); the finding is that those states are not worth acting on, not that they are missing.

## Verdict line per book (per contract, last 6 months, N basis, MDE in brackets; best PRE+X'-selected cell of each section)
| book | A: premise-loss exit (headline rule) | B: horizon / decay (best cell) | C: forecast re-score (selected cell) | verdict |
|---|---|---|---|---|
| ST | Supertrend flip against -3.56 (3.9), touches 79% | session-end tighten -0.90 (1.7) | P(target)<0.5, in profit, exit now -1.11 (2.9); +1.44 in L3M only | BEST-AVAILABLE-NEGATIVE; hold |
| HM | HMA20 re-crosses HMA55 -5.19 (4.9), 83% | session-end market -2.43 (3.2) (PRE +0.20, X' +0.58, then HOLD -2.15) | P(target)<0.5, age>=15, tighten to entry -1.55 (3.1): the only eligible cell anywhere, flips in HOLD | BEST-AVAILABLE-NEGATIVE; hold |
| WT | not built (no WT state series) | 60 min tighten -1.10 (1.1) | P(target)<0.3, age>=5, tighten -0.21 (0.6), fires 5% | BEST-AVAILABLE-NEGATIVE, nearest to zero; hold |
| KB | 3m close back inside Keltner -3.54 (4.2), 84% | session-end tighten -1.78 (2.0) | R, age>=15, tighten -3.12 (3.0) | NEGATIVE in every section; hold |
| SM | 10m Supertrend flip against -0.22 (3.6), touches 19% | session-end tighten -0.78 (4.6) | P(target)<0.4, age>=15, exit -0.73 (3.8) | zero within MDE; hold |
| PE | pullback extreme taken out -2.64 (3.6), 66% | 120 min tighten -1.45 (2.0) | P(target)<0.3, age>=5, tighten -0.16 (1.2) | zero within MDE (nearest to zero of the large books); hold |
| PB / DN / MV / MA / CR | not built | -1.54 / -1.94 / -2.21 / -3.80 / (CR +0.22, DEAD: PRE and X' negative) | -3.84 / -3.52 / -0.18 / -4.66 / no fires | NEGATIVE (MV ~0); hold |
HOLD is the same sign as L6M in every cell above. L3M (13 weeks, view only): ST +1.44, PE +0.44, ENG6 +0.26, WT +0.15, MV +0.14 on C; each negative in HOLD and L6M and inside its MDE: "L3M only", not a rule.

## The plain sentences
* When KB's 3-min close comes back inside the Keltner channel, exiting at market costs 3.5 pts per contract on 84% of trades in the last 6 months (MDE 4.2); the trades it exits would have reached the target 45% of the time, against 50% for all KB trades. It does not "save" anything: the loss saved is paid back by the winners forfeited, and the 1-pt market cost is paid on 84% of trades. The same sign in X', PRE, HOLD and L6M.
* When ST flips against the position, exiting costs 3.6 pts per contract on 79% of trades (MDE 3.9); touched trades reach the target 43% vs 52%.
* PE's edge is not spent after any horizon in any session in the last 6 months: the mean remaining expectancy of a PE trade is still positive at 60 min (+3.8 pts M in L6M, +0.3 in PRE+X'), and there is no age at which it falls below minus the exit cost and stays there. The six stack books' median time to target is ASIA 120 min, LONDON 68, PRE 20, NY-AM 13, NY-PM 28 (P(target) 0.56 / 0.56 / 0.53 / 0.53 / 0.46), so the horizon of a 60/60 bracket is very different by session, but a time exit at any of 5-120 min or the session end costs 0.7-1.1 pts per contract on the stack books (tighten) and more as a hard exit.
* When the re-scored forecast turns against ST, exiting at market costs 2.4 pts per contract on 64% of trades (MDE 3.7); the trades it exits reach the target 51% of the time (52% for all): the forecast has no timing information as an exit trigger, although it separates final outcomes (decile calibration 0.13 -> 0.22 realised, 0.87 -> 0.77) and beats its feature-shuffled twin by 1.5-3.3 pts.
* Adding a lot when the forecast strengthens earns +0.7..+1.1 per added lot in ENG6, but adding at every trade of the same age earns +1.6..+2.1: the signal picks worse-than-random adds (rank 0.02 vs random). STRUCTURE (the drift of an open position), not information.

## Stack (exact lock engine, 6 engine books, \$/week vs hold-to-bracket; DS3_DECAY_C_RESCORE.md section D has all windows, M and N)
| variant | basis | L6M (MDE) | HOLD | PRE | X' | re-entry P&L L6M | exit-only (no re-entry) L6M | extra trades kept |
|---|---|---|---|---|---|---|---|---|
| RESC_perbook | M | -18,831 (44,674) | -19,939 | -7,697 | -7,600 | +7,593 | -26,424 | 2137 |
| RESC_perbook | N | -26,926 (53,026) | -27,215 | -15,646 | -10,652 | +9,929 | -36,855 | 2262 |
| RESC_ENG6pooled | M | -8,652 (23,454) | -13,113 | -8,107 | -3,669 | +2,316 | -10,967 | 508 |
| RESC_ENG6pooled | N | -9,769 (23,806) | -14,728 | -11,088 | -4,898 | +2,331 | -12,100 | 544 |
| DECAY_bestperbook | M | -105 (22,606) | -1,634 | -1,190 | +1,715 | +2,383 | -2,488 | 457 |
| DECAY_bestperbook | N | -2,911 (25,046) | -4,646 | -4,138 | -788 | +2,623 | -5,534 | 491 |
| INV_bestperbook | M | -21,916 (33,573) | -20,892 | -16,527 | -4,651 | +1,728 | -23,643 | 2690 |
| INV_bestperbook | N | -27,242 (34,955) | -26,094 | -22,407 | -8,725 | +3,374 | -30,616 | 2790 |
| JOINT_INV+DECAY+RESC | M | -39,182 (49,615) | -38,319 | -23,010 | -14,297 | +6,627 | -45,809 | 4281 |
| JOINT_INV+DECAY+RESC | N | -52,159 (55,383) | -50,482 | -32,717 | -19,624 | +8,772 | -60,931 | 4472 |
| JOINT_DECAY+RESC | M | -20,122 (45,098) | -21,395 | -12,301 | -9,451 | +8,913 | -29,036 | 2394 |
| JOINT_DECAY+RESC | N | -31,053 (53,707) | -31,444 | -19,950 | -13,639 | +10,418 | -41,470 | 2543 |
| LIVE_PATH_TH_JADE | M | -11,105 (52,663) | -7,296 | -34,528 | -3,427 | +15,519 | -26,624 | 6075 |
| LIVE_PATH_TH_JADE | N | -46,562 (58,932) | -40,614 | -58,964 | -12,306 | +15,474 | -62,035 | 6425 |
| L2HEALTH_loss_PRE | M | -239 (32,664) | -4,331 | +8,534 | +2,232 | -1,246 | +1,006 | 2470 |
| L2HEALTH_loss_PRE | N | +5,873 (39,243) | +3,745 | +9,163 | +1,518 | -521 | +6,394 | 2533 |
| L2HEALTH_p70_take | M | +29,613 (46,673) | +30,017 | -4,139 | +4,466 | +18,696 | +10,916 | 2351 |
| L2HEALTH_p70_take | N | -8,976 (49,986) | -6,147 | -31,698 | -6,148 | +19,813 | -28,789 | 2752 |
| L2HEALTH_loss+p70 | M | +26,052 (57,979) | +22,300 | +5,009 | +10,225 | +20,986 | +5,066 | 4271 |
| L2HEALTH_loss+p70 | N | -15,387 (62,094) | -16,375 | -23,346 | -502 | +19,994 | -35,380 | 4667 |


JOINT (best invalidation + best decay + best re-score, earliest exit per trade) is -39k/wk M and -52k/wk N in L6M (MDE ~50-55k), -38k/-50k in HOLD, -23k/-33k PRE, -14k/-20k X': the same sign in every window and basis. Re-entry P&L is separated in the table (positive, +2k..+21k/wk, but smaller than the exit loss). Against the live path TH rule (JADE): -11k M / -47k N; the user's L2 health rules (loss PRE cells + REF p70 take): +26k M but -15k N (the gain is the target-fill correction: STRUCTURE / basis). EQR scaling is reported in stack_D.csv and labelled STRUCTURE; the delta of every exit variant is anti-correlated with the stack (-0.4..-0.8 weekly): exits remove the big winning weeks.

## Section-5 header (PRE-selected rows of section C; none is promoted or CANDIDATE-RECENT, columns shown so nothing is hidden)
| scope (cell) | pts/contract N [day-block CI] | L3M / L6M / HOLD / PRE / X' | fires/wk | fire rate | 1 of N | RC p (13 scopes: own 93 cells) | Romano-Wolf | DSR | PBO | placebo rank (random exit) | neighbour mean | breakeven extra cost | capacity (median size at touch / 4-tick liq) | top-5% share | stack corr (RESC) | regime | drift sign count |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ST (P/m=0.5/age=0/pr/exit) | -1.11 [-3.088, 0.858] | +1.44 / -1.11 / -1.18 / -0.93 / -1.26 | 21.7 | 46.3% | 1 of 93 (x13 scopes) | 0.92 | N (0 survivors, ENG6/ALL) | 2e-10 | 0.00 | 0.56 | -0.89 | none (negative) | 2 / 20 contracts | n/a | -0.59 | none: negative in all regimes tried (sessions: only london/asia ~0) | 2/11 |
| HM (P/m=0.5/age=15/pr/tighten) | -1.55 [-3.557, 0.506] | -0.35 / -1.55 / -1.19 / +0.06 / +0.21 | 11.0 | 32.6% | 1 of 93 (x13 scopes) | 0.72 | N (0 survivors, ENG6/ALL) | 2e-09 | 0.00 | 0.02 | -1.21 | none (negative) | 2 / 20 contracts | n/a | -0.59 | none: negative in all regimes tried (sessions: only london/asia ~0) | 4/11 |
| WT (P/m=0.3/age=5/pr/tighten) | -0.21 [-0.593, 0.174] | +0.15 / -0.21 / -0.49 / +0.05 / -0.07 | 3.3 | 5.2% | 1 of 93 (x13 scopes) | 0.95 | N (0 survivors, ENG6/ALL) | 7e-09 | 0.00 | 0.14 | -0.41 | none (negative) | 3 / 32 contracts | n/a | -0.59 | none: negative in all regimes tried (sessions: only london/asia ~0) | 4/11 |
| KB (R/m=0/age=15/pr/tighten) | -3.12 [-5.38, -1.239] | -0.46 / -3.12 / -2.88 / -0.85 / -0.24 | 14.8 | 31.5% | 1 of 93 (x13 scopes) | 1.00 | N (0 survivors, ENG6/ALL) | 3e-17 | 0.00 | 0.00 | -2.97 | none (negative) | 2 / 17 contracts | n/a | -0.59 | none: negative in all regimes tried (sessions: only london/asia ~0) | 3/11 |
| SM (P/m=0.4/age=15/pr/exit) | -0.73 [-3.273, 1.944] | -0.34 / -0.73 / -1.75 / -0.80 / -0.50 | 2.0 | 16.9% | 1 of 93 (x13 scopes) | 0.98 | N (0 survivors, ENG6/ALL) | 3e-09 | 0.00 | 0.40 | -0.12 | none (negative) | 2 / 23 contracts | n/a | -0.59 | none: negative in all regimes tried (sessions: only london/asia ~0) | 3/11 |
| PE (P/m=0.3/age=5/pr/tighten) | -0.16 [-1.072, 0.678] | +0.44 / -0.16 / -0.76 / -0.04 / -0.41 | 4.6 | 10.4% | 1 of 93 (x13 scopes) | 0.84 | N (0 survivors, ENG6/ALL) | 6e-08 | 0.00 | 0.78 | -0.27 | none (negative) | 3 / 31 contracts | n/a | -0.59 | none: negative in all regimes tried (sessions: only london/asia ~0) | 5/11 |
| ENG6 (P/m=0.3/age=15/pr/tighten) | -0.43 [-1.073, 0.132] | +0.26 / -0.43 / -0.68 / -0.33 / -0.33 | 20.9 | 8.4% | 1 of 93 (x13 scopes) | 0.99 | N (0 survivors, ENG6/ALL) | 3e-14 | 0.00 | 0.03 | -0.67 | none (negative) | 3 / 31 contracts | n/a | -0.59 | none: negative in all regimes tried (sessions: only london/asia ~0) | 3/11 |

Sections A and B carry the same columns for their selected rows in their own reports (RC / Romano-Wolf / PBO for A and B computed by SD-A and SD-B; DSR, bootstrap CI and the 1-s/3-s latency columns are NOT computed for A and B, and latency, purged CV and 60-s shifted placebos are not computed for C; none can change a sign that is -1 to -5 pts).

## Controls and gates
Random exits at the same rate and the same time-since-entry distribution: A average -2.9 (KB) -2.4 (ST) -3.9 (HM) -2.2 (PE) in L6M, i.e. the signal-keyed exits are not better than random ones (p(random >= real) 0.70-0.99); C: rank of the selected cell vs 120 random draws 0.00-0.81 (needs 0.95). Shuffled-signal / shuffled-feature placebo: C's real model beats its twin (information real) and still loses to hold. N and LIVE-P9 bases side by side everywhere; M adds the target-fill correction (1.4-4.3 pts) which flatters early exits, so a rule must be >= 0 on N. White RC: A, B and C all p >= 0.36 per scope; Romano-Wolf: 0 survivors; PBO 0.0; DSR ~0 at 147,739 trials. Cumulative multiplicity: UF_TRIALS.json side="decay" (B n_eff 1.8, C n_eff ~1.5 per scope); DEAD_CELLS.csv +884 (B) and +1,209 (C) rows plus A's.

## What would change this (for the user to decide, nothing queued)
1. Coverage: A did not build WT, MV, DN, CR, PB7/A6, MA, iFVG or O6 state series; B and C cover all 11 books on path/regime/book state only. Those books are untested for premise exits.
2. Information, not rules: the re-scored forecast knows the final outcome (Brier gain) but not the next hour (IC with the next 1-60 min change ~0). A signal that predicts the incremental move (order-level features, the MBO question already posed) is the only thing that could make an exit pay; nothing on mbp-10 + 1-s aggregates does.
3. The cost: the exit costs 0.995 pt (M/N) and the library bracket fills stops at 1.01; a limit-at-touch exit with a measured fill basis would cut the cost but would need the live calibration of limit exits (not available).
Questions for the user: none. Everything above is reproducible from l2vast/ds3/code/decay/ (sd_state.py, sd_a_*.py, dc_*.py, sdc_*.py) and l2vast/ds3/out/decay/{A,B,C}/.
