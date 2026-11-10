# DS3_JOINT_2 - joint, continued (T-NEXT Part C), DRAFT 2026-11-10 17:06Z

**FIRST-ORDER SCREEN ONLY unless stated; PRE-PROOF; Shadow only; no PASS claims.** Written by SZ-IJK (JOINT). Exact composes (JX01-JX07) and the exact check of the refit pick are PAUSED by the 17:15Z order (T-TRAIL-L2) until 21:30Z; they resume then.

## C3. REFIT 2026-11-22 dry run - the bi-weekly joint refit procedure and its walk-forward

**Procedure (code/th_joint/refit_proc.py).** At a refit date r: training = the 26 weeks ending 7 days before r, on the LIVE PANEL BASE trade list (the un-gated live-panel run: installed 7/4/4, 8,400 day cap, P7 cut 40/5x/w5/p3; layers = live). (1) Screen every layer (SIZER, LOT, SIGQ, REG, STACK, COOL, ZONE, A06, B02): rank its candidate cells by maxDD at equal mean on the training window (cell mean >= 50% of the live mean), keep the top 4 + live. (2) Joint: coordinate descent over the layers from the live stack (3 passes) minimising the training equal-mean maxDD of the stack. (3) One stack; OOS = the next 14 days. 74 refits from 2024-01-01. Cells that zero a whole book-session (turn-offs) and cells already inside the live panel base (the 7/4/4 table, KCAP) are excluded from the universe (standing rule 1; double counting).

Three versions: **A** = universe of 150 seeded-random down-only cells per layer (no pool-selection leak), no shrinkage; **B** = A plus shrinkage (a change is accepted only if the training equal-mean maxDD falls by at least 50% of the current value); **C** = the owners' REGISTERED candidate cells only (registry static-M cells + the four JN04 layers; the owners picked them on full history, so C carries a pool-selection leak).

| version | OOS maxDD cut (raw) | OOS cut at equal mean | OOS d mean $/wk | periods where the pick beat live (lower period maxDD) | pick P&L >= live | since 2026-05 beat | periods changed |
|---|---|---|---|---|---|---|---|
| A random universe, no shrink | +49.5 | +24.1 | -4736 | 89% | 38% | 100% | 100% |
| B random universe, 50% shrink | +22.4 | +18.0 | -750 | 81% | 47% | 85% | 99% |
| C registered cells | +54.7 | +45.9 | -2293 | 92% | 42% | 100% | 100% |

Reading: the procedure works as a mechanism but is not a free lunch. Without shrinkage (A) the training fit is absurd (training equal-mean maxDD about 2k vs 77k live) and the OOS gain at equal mean is only a fraction of it; the 50% shrinkage (B) keeps the OOS cut at equal mean at +18% with a small mean cost (-0.7k/wk) and beats live in 81% of the 74 periods. The registered-cell version (C) is the strongest OOS but its universe was chosen on full-history evidence, so treat it as an upper bound. In every version the pick beats live on P&L in fewer than half of the periods: the gain is drawdown for mean, as for the exact stacks.

**What it would change on 2026-11-22 (train = the 26 weeks to 2026-11-05) versus the installed panel and the JN04 spec:**

| version | picked stack (layers not listed stay live) | training maxDD at equal mean: pick / live / JN04 stack | training d mean: pick / JN04 |
|---|---|---|---|
| B | SIZER = VT:a5a7135ca8ed | 36391 / 77224 / 59036 | +1892 / +993 |
| C | SIZER = reg:sizer:AB_73ca99b0ec2d, A06 = reg:a06_slots:a06_greedy_down | 28766 / 77224 / 68355 | +2382 / +325 |
| A | SIZER = reg:sizer:AB_e2058312a643, LOT = F:e42de98e2549, SIGQ = G:2edee9e61577, REG = H:72968d15b1b2, STACK = E:E|corr_same_side|N30min_f0.0_ge1_others|sess_london, COOL = L:839b37a1ce91, A06 = reg:a06_slots:a06_greedy_down | 2220 / 77224 / n/a | n/a / n/a |

Reading: as of 2026-11-22 the first-order refit does NOT select JN04's four layers (P7 Calmar gate, dA gate, P7 ATR regime, same-side cap): on the 26-week training window they cut the panel-base drawdown less (training maxDD at equal mean 59-68k vs live 77k) than the picks (29-36k), mainly a volatility sizer cell (SIZER = AB / VT cell). The picks are first-order and unconfirmed: the exact check of the B / C picks is queued behind the 21:30Z pause. The refit mechanism can be relied on only with the shrinkage (B) and an exact confirmation of the pick before it goes live.

## SIGQ dA frame risk - which zone line drives the halvings, and does SIGQ keep its cut without KC_up_4h (FIRST-ORDER, S1b-COMB base)

Share of SIGQ fires by the NEAREST untouched line ahead (5,022 fires = dA >= the monthly 70th percentile, all books): KC_up_4h 40.6% (2041); Kijun_1h 22.9% (1150); RTH_camH3 15.7% (787); PD_mid 11.1% (558); OTE62_15m 4.7% (236); CRT_mid_4h 3.8% (191); OTE79_15m 0.7% (37); OTE705_15m 0.4% (22). KC_up_4h is the nearest line for 14.4% of all trades and drives 40.6% of the fires; the dA 98.7th percentile is 733 pts (the 980+ pt values of the live week are KC_up_4h).

| variant | fires | SIGQ alone: L6M cut / eq-mean L6M / PRE / X' | inside JN04 (with LOT, REG, STACK): L6M cut / eq L6M / eq PRE | JN04 d mean L6M |
|---|---|---|---|---|
| SIGQ all 8 lines (as in JN04) | 5022 | +6.2 / +13.1 / +25.3 / +7.3 | +48.4 / +46.9 / +65.2 | -766 |
| leave out line PD_mid | 4843 | +6.8 / +8.2 / +19.6 / +1.5 | +48.4 / +47.5 / +65.7 | -436 |
| leave out line RTH_camH3 | 4734 | +13.1 / +17.0 / +16.4 / +4.6 | +49.7 / +48.3 / +62.6 | -779 |
| leave out line Kijun_1h | 4850 | -3.0 / -2.7 / +16.1 / +0.2 | +45.6 / +42.3 / +64.2 | -1568 |
| leave out line CRT_mid_4h | 5021 | +4.7 / +10.3 / +24.2 / +5.9 | +46.9 / +45.0 / +65.0 | -953 |
| leave out line KC_up_4h | 4112 | -4.1 / +0.2 / +12.0 / +4.1 | +47.9 / +46.0 / +62.5 | -963 |
| leave out line OTE62_15m | 5074 | +9.5 / +18.3 / +30.3 / +9.8 | +50.5 / +49.9 / +65.8 | -344 |
| leave out line OTE705_15m | 5043 | +6.2 / +13.7 / +26.5 / +8.0 | +48.4 / +47.1 / +65.4 | -654 |
| leave out line OTE79_15m | 5073 | +4.5 / +5.1 / +16.9 / +0.6 | +45.4 / +41.9 / +62.9 | -1626 |
| drop only the fires nearest to PD_mid | 4464 | +4.5 / +11.9 / +22.7 / +7.7 | +47.5 / +46.3 / +65.2 | -606 |
| drop only the fires nearest to RTH_camH3 | 4235 | +7.7 / +11.5 / +19.6 / +4.1 | +48.4 / +47.1 / +64.2 | -669 |
| drop only the fires nearest to Kijun_1h | 3872 | +6.0 / +10.0 / +28.5 / +4.3 | +47.8 / +46.2 / +62.2 | -816 |
| drop only the fires nearest to CRT_mid_4h | 4831 | +6.2 / +13.4 / +22.5 / +7.6 | +48.4 / +47.2 / +64.4 | -616 |
| drop only the fires nearest to KC_up_4h | 2981 | -0.3 / +5.0 / +11.8 / +5.2 | +46.9 / +45.6 / +63.7 | -638 |
| drop only the fires nearest to OTE62_15m | 4786 | +6.9 / +14.3 / +22.3 / +7.9 | +46.7 / +45.6 / +65.0 | -590 |
| drop only the fires nearest to OTE705_15m | 5000 | +6.2 / +13.1 / +27.1 / +7.4 | +48.4 / +46.9 / +65.3 | -750 |
| drop only the fires nearest to OTE79_15m | 4985 | +6.2 / +12.9 / +23.9 / +7.2 | +48.4 / +46.8 / +65.2 | -801 |
| leave out both 4h lines (KC_up_4h, CRT_mid_4h) | 4087 | -2.7 / +5.4 / +12.6 / +7.9 | +46.8 / +45.6 / +63.1 | -608 |
| only PD_mid, RTH_camH3 and the three OTE lines (no 4h / 1h lines) | 3828 | -5.0 / -1.0 / +10.4 / +3.8 | +47.9 / +47.1 / +63.3 | -458 |

Reading: SIGQ ALONE depends on KC_up_4h: with that line removed its L6M cut goes from +6.2% to -4.1% and the equal-mean PRE cut halves (25.3 -> 12.0); dropping only the KC_up_4h-driven fires leaves L6M -0.3%. INSIDE JN04 the dependence is small (L6M cut 48.4 -> 47.9, equal-mean PRE 65.2 -> 62.5), because the other three layers carry the stack; SIGQ is marginal in JN04 (section C of JN04_LIVE_SPEC). The OTE lines are not interchangeable either: removing OTE79_15m or Kijun_1h costs more than removing KC_up_4h inside JN04.

**Pass criterion for the live Shadow check of SIGQ (to state before Live):** (a) frame: the strategy's own KC_up_4h, Kijun_1h, RTH_camH3, PD_mid and OTE lines must equal the research replay values at the same signal second within 2 pts on at least 95 percent of signals (inside the research the engine-vs-replay agreement is 74 percent within 1 pt, median 0.5 pt); (b) distribution: finite dA on about 65 percent of taken signals (research 64.8), nearest line = KC_up_4h on about 14 percent of signals and at most about 41 percent of the fires (research 14.4 / 40.6), halved share among finite-dA signals about 37 percent with a weekly range 10-59 percent (research mean, 5th-95th percentile; a high-volatility week can sit above it); (c) if a week of Shadow shows KC_up_4h-driven fires above 60 percent of the fires, or dA above 500 pts on more than 5 percent of signals, the KC_up_4h px is stale or in the wrong frame: leave SIGQ in Shadow and exclude KC_up_4h from the line set (SIGQ then keeps most of its JN04 contribution, table above).

## C1. Compose the leads on the live panel base (JN04 rule mode as the base) - STATUS

Sets built (code/th_joint + th_sz_ijk; set jsons under /mnt/l2/l2vast/_th_sz/ijk/exact/sets): JX01 = JN04RM + R5_BO_3 post-stop/cut P7 same-side 30-min blackout (hook, in the panel hooks par), JX02 = JN04RM + R11_any_N30_ALL_SKIP (table lead, S1b-keyed multiplier table, 6052 trades <1), JX03 = JN04RM + R7_P3 bracket policy (r7_hooks) - exact lead from REDO-R7, JX04 = JN04RM + ATR skip (table lead, S1b-keyed multiplier table, 1929 trades <1), JX05 = JN04RM + KCAP3 (table lead, S1b-keyed multiplier table, 2061 trades <1), JX06 = JN04RM + cooldown L (table lead, S1b-keyed multiplier table, 3398 trades <1), JX07 = JN04RM + VT (table lead, S1b-keyed multiplier table, 14032 trades <1). Windows planned: L6M, HOLD, PRE first, then X' and the 2025-07..10 gap for survivors; scoring against the live panel base without layers AND against JN04RM (incremental). **Launched at 17:20Z and stopped by the 17:15Z T-TRAIL-L2 pause (no results yet); resume 21:30Z.** Not yet built: flip-level skip R6_FL_LIVE (shadow lead, needs its own hook), R1 lock cells (conflict with the installed fixed day cap: R1 cells replace the panel cap, to be composed as a separate comparison), near-target winner and vol-target adaptive cells beyond the VT cell in JX07 (SZ-FGH takes the sizer / LOT-side leads).

## Driver entry for SZ-FGH and ZN-CORE (how to run a composed set exact on the live panel base)

- Driver: `code/th_sz_ijk/state_sizer_ijk.py`; run `python3 state_sizer_ijk.py jbjobs "SET1,SET2:yyyymm,yyyymm|SET3:...” <workers<=4>`; outputs go to `/mnt/l2/l2vast/_th_sz/ijk/exact/runs_rf/<SET>/<yyyymm>/trades.parquet` (month-batched: all sets of a month share one materialise/load).
- Set json (`exact/sets/<SET>.json`): `state` (the LPB state dict), `sizer` Q1-A dict, `hooks` (the panel hook: r5_hooks make_rep with par panel p7_daycap [42000, 8400], p7_sess 7,4,0,4,0,0; add `bo` for the post-stop blackout), `mtab` = path to a parquet (book7, sig_ts, m) multiplier table keyed by the S1b-COMB signal second (m < 1 rows only; applied after Q1-A, before zone HALF), `hooklist` = extra make_rep hooks [{path, module, par}] (R7), `cde` = SZ-CDE state rule (code 8 same-side cap, code 3/9 F04/F01), `jnrule` = path to jnr_cfg.json (turns on the in-engine JN04 rules LOT / SIGQ / REG), `entry` = R4 entry mixin dict (not combinable with hook subclasses), `r5bo` = blackout guard usable with entry. Base set to copy: `JN04RM.json` (JN04 in rule mode on the live panel base) or `LPB_EMPTY.json` (the base itself).
- Scoring: `exact_score_lpb.py <CELL> <out.csv>` scores `runs_rf/<CELL>` against the live panel base reference (LPB_EMPTY + SZ-CORE LPB_BASE months), windows L1M L3M L6M HOLD PRE X' with the 25%-floor rule 2a label and the contiguous bi-weekly WF when all 43 months exist.
- For ZONE x SIGQ x STACK x LOT interaction tables: zone tables go in `mtab` (product with the JN04 table or rule mode), the interaction (pair minus singles) is computed from exact_scores of the single and pair sets as in DS3_JOINT.md section "Interaction vs additive".

