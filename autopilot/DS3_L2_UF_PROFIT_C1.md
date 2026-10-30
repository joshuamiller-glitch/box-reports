# DS3_L2_UF_PROFIT_C1 - PROFIT side, cycle 1 of L2-UNTIL-FOUND (UF-PROFIT, 2026-10-30)
Research only; UNTOUCHED never read; masks 2026=20260101..0206, L6M=20250801..0206, HOLD=20250701..0206, PRE=20240201..20250630, X'=20230401..20240131; all frames capped at label day 20260206. Prereg l2vast/ds3/prereg/UF_PROFIT_C1_prereg.md sha256 6ccabfcdc4066463e46775ef68b5ecc88e5e14ceff1ee5985ca3c24d67dd4620 (cells csv sha256 680f7600c519a35992b94962e158fed27bc9bdef4330ee9ccd98e80b29ea9176), logged in DECISIONS.md before any outcome was read; PRE+X' selection json sha256 33a55d0ce2be707630e9a287c7263768a5c4f1610cc17d339837d623d4253a55 logged before the one recent look. Cells 376 (369 selectable + 6 ablations + REF).

## Verdict
**No PROFIT rule is found.** 0 of 369 cells is >= 0 on N AND LIVE-CAL in PRE and in X' separately (the prereg eligibility gate); White RC on PRE u X' p = 1.00; cycle RC in L6M p = 0.98 (best cell t +0.78), HOLD p = 0.9955; cumulative-adjusted (Sidak over N_cum = 143,584 prior + 376 cells; distinct specs 81,198 + 376) p = 1.00 for every cell. The PRE+X' rank-1 cell (the cycle's candidate) is a target WIDENER and is BEST-AVAILABLE-NEGATIVE: N L6M -0.08 (MDE 0.64), stack vs hold -8.5k/wk. The only cells >= 0 in the recent windows are three hold-through-retest cells gated by the ES book (F8, es_imb5 <= q20 at the NQ extreme): CANDIDATE-RECENT (label only), PRE and X' ~0, stack line negative, they fire on 1-3% of trades.

## Settings table (recent first; N basis and LIVE-CAL primary, M beside; pts/trade vs hold-to-bracket over ALL trades of the pooled scope, non-fires count 0; day-cluster; MDE = 2.8 SE in brackets)
| role | cell | tier | 2026 (~5 wk) N | L6M N | HOLD N | PRE N | X' N | L6M LIVE / M | fires L6M | stack vs hold (lock engine, N) L6M / HOLD / PRE | EQR approx L6M | placebo rank L6M N: causal random action / shuffled book | RC p cycle L6M / cumulative |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CYCLE CANDIDATE (PRE+X rank 1) | `UFP1|F7|F7|hour_ahead_le0.5|tapewith|pct0.7|widen20` | BEST-AVAILABLE-NEGATIVE | -0.45 (1.51) | -0.08 (0.64) | -0.10 (0.60) | +0.07 (0.33) | -0.26 (0.44) | -0.10 / -0.01 | 1076 | -8.5k / -8.3k / -7.3k (MDE 26k) | -16.7k | 0.15 / 0.02 | 0.98 / 1.00 |
| family best F1 | `UFP1|F1|F1|Wm80|Tb|I1|arm0.7|trail30` | BEST-AVAILABLE-NEGATIVE | -0.49 (1.97) | -0.54 (0.82) | -0.56 (0.76) | -0.31 (0.58) | +0.40 (1.00) | -0.66 / -0.23 | 1181 | -2.2k / -3.2k / -16.8k (MDE 33k) | -5.3k | 0.02 / 0.00 | 0.98 / 1.00 |
| family best F2 | `UFP1|F2|F2|cons80|ref20|arm0.7|trail40` | BEST-AVAILABLE-NEGATIVE | -0.38 (1.68) | -0.68 (0.84) | -0.68 (0.79) | -0.40 (0.63) | +0.14 (1.04) | -0.79 / -0.40 | 1170 | n/a (not run) | n/a | 0.00 / 0.00 | 0.98 / 1.00 |
| family best F3 | `UFP1|F3|F3|iceq90|ext10|arm0.7|trail40` | BEST-AVAILABLE-NEGATIVE | -0.47 (1.75) | -0.48 (0.87) | -0.51 (0.81) | -0.37 (0.64) | +0.21 (0.96) | -0.62 / -0.12 | 1548 | n/a (not run) | n/a | 0.08 / 0.00 | 0.98 / 1.00 |
| family best F4 | `UFP1|F4|F4|es10|esd30|arm0.5|trail30` | BEST-AVAILABLE-NEGATIVE | -0.04 (1.80) | -0.45 (0.84) | -0.54 (0.80) | -0.16 (0.49) | +0.05 (0.76) | -0.55 / -0.19 | 965 | n/a (not run) | n/a | 0.01 / 0.02 | 0.98 / 1.00 |
| family best F5 | `UFP1|F5|F5|d5q10|arm0.7|trail40` | BEST-AVAILABLE-NEGATIVE | -1.06 (1.85) | -0.83 (1.02) | -0.84 (0.95) | -0.45 (0.67) | +0.17 (1.05) | -0.99 / -0.41 | 1797 | n/a (not run) | n/a | 0.00 / 0.00 | 0.98 / 1.00 |
| family best F6 | `UFP1|F6|F6|B|3m|hq99|arm0.5|trail30` | BEST-AVAILABLE-NEGATIVE | -1.33 (1.68) | -0.52 (0.83) | -0.49 (0.78) | -0.31 (0.54) | +0.19 (0.34) | -0.62 / -0.27 | 1041 | n/a (not run) | n/a | 0.01 / 0.00 | 0.98 / 1.00 |
| family best F8 | `UFP1|F8|F4|es20|arm0.3|gdd12` | CANDIDATE-RECENT (label only; fails G1/G7/G8/stack) | +0.28 (0.97) | +0.11 (0.59) | +0.05 (0.55) | -0.12 (0.36) | +0.02 (0.34) | +0.13 / +0.23 | 435 | -1.9k / -1.6k / -4.3k (MDE 13k) | -3.7k | 1.00 / 1.00 | 0.98 / 1.00 |
| F8 neighbour (looked; shown because it has the recent positives) | `UFP1|F8|F4|es20|arm0.7|gdd12` | CANDIDATE-RECENT (label only; fails G1/G7/G8/stack) | +0.12 (0.72) | +0.10 (0.35) | +0.07 (0.32) | -0.01 (0.18) | -0.03 (0.15) | +0.11 / +0.16 | 188 | -3.9k / -3.5k / -3.5k (MDE 6k) | -3.9k | n/a | 0.98 / 1.00 |
| control | `UFP1|REF|plain_take70` (plain take at 70% of target) | path rule | -0.95 (1.96) | -1.25 (1.12) | -1.13 (1.06) | -0.91 (0.77) | -0.31 (1.27) | -1.16 / +0.86 | 5565 | -4.8k / -3.9k / -33.0k | -13.8k | - | M +0.86 L6M is the target-fill artefact |

Placebo: P1 = CAUSAL random action at the same rate (independent Bernoulli per armed profit row, hazard solved so the share of armed trades that fire equals the real cell's; same action; 200 draws); P2 = trigger bits shuffled within label day (aligned by index within the trade, corrected row->trade map; 60 draws). Rank = share of draws below the real cell (0.95 needed). A first, NON-causal P1 (one uniformly random armed row) gave +0.3 on N for every trail cell because uniform-in-span timing sees the end of the armed span; it was replaced and is not used. The P2 rank of F8 is not comparable (shuffling changes its fire count 8x).

## Windows, all bases, for the cycle candidate and the F8 leads (pts/trade vs hold; MDE in brackets)
| cell | window | N | LIVE-CAL | M | 2x-cost | fires | $/wk N at live lots |
|---|---|---|---|---|---|---|---|
| `UFP1|F7|F7|hour_ahead_le0.5|tapewith|pct0.7|widen20` | Y2026 | -0.45 (1.51) | -0.47 (1.52) | -0.38 (1.45) | -0.40 | 222 | -22461 |
| `UFP1|F7|F7|hour_ahead_le0.5|tapewith|pct0.7|widen20` | L6M | -0.08 (0.64) | -0.10 (0.65) | -0.01 (0.62) | -0.02 | 1076 | -3820 |
| `UFP1|F7|F7|hour_ahead_le0.5|tapewith|pct0.7|widen20` | HOLD | -0.10 (0.60) | -0.12 (0.60) | -0.03 (0.58) | -0.05 | 1117 | -4299 |
| `UFP1|F7|F7|hour_ahead_le0.5|tapewith|pct0.7|widen20` | PRE | +0.07 (0.33) | +0.06 (0.33) | +0.12 (0.32) | +0.10 | 2377 | +4248 |
| `UFP1|F7|F7|hour_ahead_le0.5|tapewith|pct0.7|widen20` | XP | -0.26 (0.44) | -0.27 (0.45) | -0.25 (0.44) | -0.26 | 408 | -9499 |
| `UFP1|F8|F4|es20|arm0.3|gdd12` | Y2026 | +0.28 (0.97) | +0.31 (0.99) | +0.41 (0.96) | +0.37 | 108 | +16095 |
| `UFP1|F8|F4|es20|arm0.3|gdd12` | L6M | +0.11 (0.59) | +0.13 (0.60) | +0.23 (0.58) | +0.18 | 435 | +3513 |
| `UFP1|F8|F4|es20|arm0.3|gdd12` | HOLD | +0.05 (0.55) | +0.07 (0.55) | +0.17 (0.53) | +0.13 | 470 | +414 |
| `UFP1|F8|F4|es20|arm0.3|gdd12` | PRE | -0.12 (0.36) | -0.10 (0.37) | -0.01 (0.35) | -0.06 | 1286 | -5975 |
| `UFP1|F8|F4|es20|arm0.3|gdd12` | XP | +0.02 (0.34) | +0.03 (0.35) | +0.03 (0.34) | +0.02 | 138 | +1151 |
| `UFP1|F8|F4|es20|arm0.7|gdd12` | Y2026 | +0.12 (0.72) | +0.13 (0.73) | +0.19 (0.71) | +0.17 | 52 | +8670 |
| `UFP1|F8|F4|es20|arm0.7|gdd12` | L6M | +0.10 (0.35) | +0.11 (0.36) | +0.16 (0.35) | +0.14 | 188 | +5384 |
| `UFP1|F8|F4|es20|arm0.7|gdd12` | HOLD | +0.07 (0.32) | +0.07 (0.33) | +0.12 (0.32) | +0.10 | 202 | +3067 |
| `UFP1|F8|F4|es20|arm0.7|gdd12` | PRE | -0.01 (0.18) | -0.00 (0.18) | +0.05 (0.18) | +0.02 | 595 | -421 |
| `UFP1|F8|F4|es20|arm0.7|gdd12` | XP | -0.03 (0.15) | -0.03 (0.16) | -0.03 (0.15) | -0.03 | 65 | -1137 |

## All eight families: family best (chosen on PRE u X' only) and the recent look
| family | best cell | SEL N | 2026 N | L6M N (MDE) | HOLD N | PRE N | X' N | L6M random-action rank | eligible cells |
|---|---|---|---|---|---|---|---|---|---|
| F1 | `UFP1|F1|F1|Wm80|Tb|I1|arm0.7|trail30` | -0.12 | -0.49 (1.97) | -0.54 (0.82) | -0.56 (0.76) | -0.31 (0.58) | +0.40 (1.00) | 0.02 | 0/72 |
| F2 | `UFP1|F2|F2|cons80|ref20|arm0.7|trail40` | -0.26 | -0.38 (1.68) | -0.68 (0.84) | -0.68 (0.79) | -0.40 (0.63) | +0.14 (1.04) | 0.00 | 0/36 |
| F3 | `UFP1|F3|F3|iceq90|ext10|arm0.7|trail40` | -0.21 | -0.47 (1.75) | -0.48 (0.87) | -0.51 (0.81) | -0.37 (0.64) | +0.21 (0.96) | 0.08 | 0/36 |
| F4 | `UFP1|F4|F4|es10|esd30|arm0.5|trail30` | -0.10 | -0.04 (1.80) | -0.45 (0.84) | -0.54 (0.80) | -0.16 (0.49) | +0.05 (0.76) | 0.01 | 0/36 |
| F5 | `UFP1|F5|F5|d5q10|arm0.7|trail40` | -0.29 | -1.06 (1.85) | -0.83 (1.02) | -0.84 (0.95) | -0.45 (0.67) | +0.17 (1.05) | 0.00 | 0/36 |
| F6 | `UFP1|F6|F6|B|3m|hq99|arm0.5|trail30` | -0.18 | -1.33 (1.68) | -0.52 (0.83) | -0.49 (0.78) | -0.31 (0.54) | +0.19 (0.34) | 0.01 | 0/72 |
| F7 | `UFP1|F7|F7|hour_ahead_le0.5|tapewith|pct0.7|widen20` | -0.02 | -0.45 (1.51) | -0.08 (0.64) | -0.10 (0.60) | +0.07 (0.33) | -0.26 (0.44) | 0.15 | 0/36 |
| F8 | `UFP1|F8|F4|es20|arm0.3|gdd12` | -0.08 | +0.28 (0.97) | +0.11 (0.59) | +0.05 (0.55) | -0.12 (0.36) | +0.02 (0.34) | 1.00 | 0/45 |

## Ablation of the three-together rule (F1abl; arm 0.5, trail 30; N basis)
| part | 2026 | L6M (MDE) | HOLD | PRE | X' |
|---|---|---|---|---|---|
| `F1abl|Wc80|arm0.5|trail30` | -1.50 (3.07) | -1.21 (1.39) | -1.22 (1.30) | -1.06 (0.95) | +0.09 (1.54) |
| `F1abl|Ta|arm0.5|trail30` | -1.76 (3.19) | -1.74 (1.60) | -1.66 (1.51) | -1.02 (1.10) | +0.15 (1.58) |
| `F1abl|I1|arm0.5|trail30` | -1.73 (3.29) | -1.69 (1.60) | -1.62 (1.50) | -1.03 (1.09) | +0.12 (1.59) |
| `F1abl|Wc80|Ta|arm0.5|trail30` | -0.74 (2.71) | -1.11 (1.23) | -1.15 (1.17) | -0.90 (0.84) | +0.08 (1.46) |
| `F1abl|Wc80|I1|arm0.5|trail30` | -1.21 (2.91) | -0.93 (1.24) | -0.96 (1.17) | -0.93 (0.87) | +0.06 (1.52) |
| `F1abl|Ta|I1|arm0.5|trail30` | -1.40 (3.12) | -1.37 (1.54) | -1.39 (1.44) | -0.88 (1.06) | +0.20 (1.58) |
Path-only control (trigger = arming, no book): tighten at arm with trail 20/30/40 is -0.84..-2.99 pts/trade on N in L6M (arm 0.7 trail 40 -0.84, MDE 1.0; arm 0.3 trail 20 -2.99); full table pathctl.json (post-hoc diagnostic). The book triggers are less negative than the path-only tighten because they fire on fewer trades; against a causal random action at the same rate they are WORSE in L6M (rank 0.00-0.08 for F1-F6).

## D6 session / book cells (N, L6M and SEL, MDE in brackets; no cell is killed on the pooled number)
* `UFP1|F7|F7|hour_ahead_le0.5|tapewith|pct0.7|widen20` sessions: asia L6M -0.05 (1.46, f367) SEL +0.03; london L6M +0.51 (1.06, f279) SEL -0.01; pre L6M -2.40 (3.40, f42) SEL -0.95; nyam L6M -0.05 (0.91, f193) SEL +0.02; nypm L6M -0.22 (0.96, f194) SEL +0.14; close L6M +0.91 (2.55, f1) SEL +1.23
  books: ST -0.48 (1.36); HM -0.47 (1.45); WT -0.14 (0.59); KB -0.31 (1.61); SM +0.87 (1.47); PE -0.12 (1.23); PB +0.20 (1.25); DN +0.50 (1.38); MV -0.50 (1.46); MA +1.92 (0.95)
* `UFP1|F8|F4|es20|arm0.7|gdd12` sessions: asia L6M -0.06 (0.16, f11) SEL +0.05; london L6M -0.06 (0.70, f40) SEL -0.20; pre L6M -0.53 (2.61, f27) SEL -0.27; nyam L6M +0.31 (0.64, f74) SEL -0.02; nypm L6M +0.43 (1.03, f34) SEL +0.15; close L6M -3.70 (9.40, f2) SEL -0.26
  books: ST +0.28 (0.71); HM +0.04 (0.66); WT -0.01 (0.19); KB +0.19 (0.67); SM +0.42 (1.38); PE +0.14 (0.71); PB -0.11 (0.67); DN +0.43 (0.95); MV -0.09 (0.68); MA -0.08 (0.16)
Reading: F7 is positive in London (+0.51, MDE 1.06) and MA (+1.92, MDE 0.95, 47 fires) in L6M but SEL is ~0 there; every session cell is inside its MDE. F8 es20 arm0.7: NY-AM +0.31 / NY-PM +0.43 in L6M (MDE 0.64 / 1.03), SEL -0.02 / +0.15 - not a session story.

## Lock-engine stack lines (6 books ST HM WT KB SM PE, plain sum at live lots; delta vs CONTROL_N = hold to bracket on N; $/wk; MDE in brackets)
* `UFP1|F7|F7|hour_ahead_le0.5|tapewith|pct0.7|widen20`: 2026 -4244 (MDE 37720); L6M -8500 (25961); HOLD -8258 (22781); PRE -7270 (12239); X' -7537 (12249); changed trades (all windows) 2044
* `UFP1|F8|F4|es20|arm0.7|gdd12`: 2026 -301 (MDE 9925); L6M -3881 (6268); HOLD -3502 (5501); PRE -3494 (5007); X' -457 (3127); changed trades (all windows) 453
* `UFP1|F8|F4|es20|arm0.3|gdd12`: 2026 -1722 (MDE 20972); L6M -1859 (12848); HOLD -1614 (11241); PRE -4318 (8586); X' -2982 (5561); changed trades (all windows) 997
* `UFP1|F1|F1|Wm80|Tb|I1|arm0.7|trail30`: 2026 +47041 (MDE 81457); L6M -2157 (32704); HOLD -3242 (28961); PRE -16759 (18944); X' -640 (18678); changed trades (all windows) 3652
* `UFP1|REF|plain_take70`: 2026 +35988 (MDE 113233); L6M -4806 (43475); HOLD -3890 (38317); PRE -32989 (21757); X' -8845 (26249); changed trades (all windows) 14381
* Equal-risk (EQR) approximation: lots scaled by c so the worst-20-weeks of the rule equals the control's on PRE (lock-engine series scale linearly with lots; sweep-surface correction not applied, the full EQR frame A was built for the split and not re-run for profit streams): F7 widen20 c 0.847 L6M -16.7k; F8 es20 arm0.7 gdd12 c 1.00 L6M -3.9k; F8 arm0.3 c 0.97 -3.7k; F1 best c 0.95 -5.3k; plain take-70% c 0.84 -13.8k. LIVE-CAL stack: trade-level LIVE minus N is -0.02..-0.14 pts/trade for the candidate and F8 cells; not re-run through the engine.

## What was learned
1. **The book triggers select CONTINUATION, not reversal.** Wall ahead + tape turned + intensity > 1 sigma, own-side queue drain, iceberg against at the extreme, ES disagreeing, 60-s imbalance change, L2P hazard: every family best is NEGATIVE on N in L6M and HOLD (-0.45..-0.83 pts/trade, MDE 0.8-1.0) and WORSE than a causal random action at the same fire rate (rank 0.00-0.08 in L6M). Tightening a winner when the book 'turns' costs more than tightening at random times. PRE is -0.2..-0.45 for the same cells; X' is the only window with positive signs (+0.05..+0.4, MDE ~1).
2. The three-together conjunction is less negative than its parts (wall only -1.21, tape only -1.74, intensity only -1.69, pairs -0.9..-1.4 at arm 0.5 trail 30; triple -0.5) only because it fires on 0.2-0.6% of profit rows; it adds no information over random timing.
3. **Widening the target (F7) is closest to zero** but not positive: N L6M -0.08 (MDE 0.64), HOLD -0.10, PRE +0.07, X' -0.26; causal random-timing rank 0.16, shuffled-book rank 0.02; stack -8.5k/wk L6M (MDE 26k). Built from the 1-s path (ds3_g2 SS/SH/SL/SC, scan with the bracket stop unchanged, 6 h or window-end timeout) for the fired trades because the 10-s store has no post-exit path. A +20 pt extension must beat a 33-60 pt stop: the P(extension) on thin-book + tape-with fires is at about break-even.
4. **Hold-through-the-retest (F8) is the only family with recent positives**: exit on a >= 8/12/16-pt retrace from MFE only when the ES book disagrees (es_imb5 <= session q20 at the NQ extreme), else hold: N 2026 +0.12..+0.28, L6M +0.10..+0.11 (MDE 0.35..0.59), HOLD +0.05..+0.07, PRE -0.01..-0.12, X' -0.03..+0.02. Fire-rate-matched random placebo rank 1.00 in L6M but 0.25 in SEL: no evidence before 2025-07. The stack line is -1.9k..-3.9k/wk L6M (MDE 6-13k): the earlier exit frees the lock and the engine takes the next signal, which removes the +0.1 pt. CANDIDATE-RECENT label only; ES is NaN for 13% of rows (before 2023-08).
5. **Defect in the previous profit program**: `l2set_profit/lp_data.shuffle_src` (and any `np.repeat(arange(T), lens)` row-to-trade map) assumes ro_start is monotone in trade order; it is NOT (only 52% of consecutive trades increase; rows are stored in another order). The L2SP shuffled-book placebo (G8 ranks 0.00/1.00) therefore shuffled against the wrong trades. The kernel itself (ro0/ro1 ranges) is correct and reproduces the published REF here: take-at-70% N PRE -0.91, L6M -1.25, M L6M +0.86. This cycle uses a sorted-ro0 map (uf_p1_common.trade_of_row). L2SP placebo statements should be redone before anyone relies on them.

## Counts / multiplicity
Cells 376 (369 selectable). n_effective = 200 (greedy clusters of daily N sums on SEL at corr < 0.95). Cumulative N_cum = 143,584 (UF_TRIALS exact) + 376 = 143,960 (distinct specs 81,198 + 376). Best cell L6M t over the cycle's 369 cells = +0.78 (cycle RC p 0.98); candidate L6M t = -0.35 (raw one-sided p 0.64). Cumulative Sidak p = 1.00. DEAD_CELLS +376 (372 DEAD, 3 CANDIDATE-RECENT leads, REF); UF_TRIALS.json cycle 1 profit appended.

## Next PROFIT family (must differ from book-as-reversal-trigger)
The book triggers point the wrong way (continuation), so cycle 2 inverts the role: book state WITH the trade as a VETO on existing profit path exits (live Jade/lock/profit-exit chain and the L2SP trail cells): 'path rule gated by the book', and 'lean before the extreme' (book states 10-30 s BEFORE each new MFE; sequence not co-occurrence); plus the F8 ES gate at other retest depths with a 3-month walk-forward to separate regime from noise (PRE and X' are 0). D6 would need es_imb5 and seconds-since-MFE for any F8 line (DS3_THL2_NEEDS.md).

## Files
code l2vast/ds3/code/uf/uf_p1_*.py (prep, cells, kern, run, select, look, stack, pathctl); outputs l2vast/ds3/out/uf/profit_c1/{selection_SEL.json,look.json,stack_out.json,stack_eqr_approx.json,pathctl.json,thresholds.json,cells.json}; candidate l2vast/ds3/out/uf/profit_cycle1_candidate.txt.

## TASK A - L2SP shuffled-book placebo redone with the correct row->trade map (2026-10-30)
Defect: `l2set_profit/lp_data.shuffle_src` built the row->trade map as `np.repeat(arange(T), lens)`, which is right only if ro_start is increasing in trade order; it is increasing for 52% of consecutive trades only, so the "shuffled" thick/thin bits came from rows of unrelated trades (any day, any index). The kernel (`ro0/ro1` ranges) and D_real are unaffected (max abs difference of re-run D vs D_real = 0.0 for every cell below). Redo: trade order sorted by ro_start, thick/thin bits taken from another trade of the SAME label day (random permutation within day, aligned by index within the trade; short source trades give 0), 100 draws, rank = share of draws with a pooled mean below the real cell (M and N basis). Output `l2vast/ds3/out/uf/profit_c1/l2sp_placebo_redo.json`; code `code/uf/uf_l2sp_placebo_redo.py`.

| cell (pooled) | PRE M rank old -> new | L6M M rank old -> new | PRE N rank new | L6M N rank new |
|---|---|---|---|---|
| G1 PRE-selected `P|t60_ahead_ge3.0|armpct0.7|d0|lock10|p70never` | 1.00 -> 1.00 | 0.20 -> 0.51 | 1.00 | 0.30 |
| REF plain take-at-70% (no book bit) | 0.00 -> 0.00 | 0.00 -> 0.00 | 0.00 | 0.00 |
| G2 `I|hour_ahead_le0.5|d0|skip_p70_if_thin` | 0.00 -> 0.79 | 0.00 -> 0.02 | 1.00 | 0.13 |
| rank-1 L6M `P|sess_tot_ge1.2|armpct0.7|d10|trail30|p70always` | 0.00 -> 0.31 | 1.00 -> 1.00 | 0.32 | 1.00 |
| rank-2 L6M `P|sess_tot_ge1.2|armpct0.7|d10|take|p70always` | 0.00 -> 0.12 | 1.00 -> 1.00 | 0.12 | 1.00 |
| rank-3 L6M `P|sess_ahead_ge1.2|armpct0.7|d30|take|p70always` | 0.00 -> 0.55 | 1.00 -> 1.00 | 0.55 | 1.00 |
| rank-1 L6M on N `P|t60_tot_ge2.0|armpct0.3|d30|trail20|p70never` | 0.00 -> 0.16 | 1.00 -> 1.00 | 0.02 | 1.00 |
| `P|hour_tot_ge1.5|armpct0.7|d10|take|p70always` | 0.00 -> 0.48 | 0.80 -> 0.81 | 0.48 | 0.82 |
| `P|hour_ahead_ge1.5|armpct0.5|d30|take|p70always` | 0.00 -> 0.89 | 1.00 -> 1.00 | 0.88 | 1.00 |

Reading. (1) The published PRE rank of 0.00 for the thick-book cells was an artefact of the broken map: with the correct map the PRE ranks are 0.12-0.55 (indistinguishable from shuffled books) for the cells chosen on L6M, and 0.79-1.00 for the PRE-selected G1 and the thin-skip cell. (2) The REF cell has no book bit, so its placebo equals the real cell and its rank is 0.00 by construction (G8 is vacuous for it; it never meant "the book is useless"). (3) The L6M-selected cells have rank 1.00 in L6M (selected on looked data, not evidence); the one PRE-selected G1 cell has PRE rank 1.00 and L6M rank 0.51 (0.30 on N). (4) The conclusion "thick-book condition adds nothing beyond the path rule" is therefore NOT established by the placebo (the 0.00 ranks did not measure it); it still stands on the N and LIVE-CAL levels: no thick-book cell is > 0 on N in PRE and HOLD (L2SP: 0 of 23,760), the L6M N-basis values are -1.0..-1.3 for the p70 'always' cells, and the gain on M is the target-fill artefact. Net: the verdict (no PASS, no usable profit rule) is unchanged, the placebo evidence is now "no information either way", and G8 ranks quoted in DS3_L2SET_PROFIT.md / DS3_L2SET_JOINT.md should be read as void.
