# DS3_REFIT_1122 - the 2026-11-22 JOINT REFIT, walked forward through 43 months (PRIORITY 12, W-RF)

VERDICT (2026-11-14 17:10Z, FIRST-ORDER stage; exact stage running, nothing here is a PASS): (1) The rolling 14-day refit of the lot-level layers (SIZER LOT SIGQ REG STACK COOL ZONE A06 B02) does NOT beat the frozen JN04 setting and is worse than random layer settings in the recent windows (L6M max DD 82% deeper, mean -$15.7k/wk, 79 refits, 9 procedure variants all negative or noise): keep those layers frozen. (2) Rolling refit over the exit/entry rule layers (existing exact one-rule cells on JN05W2, session-group slots) gives L3M/L6M max-DD cut +60%/+49% and +$6.1k/+$3.3k per week, but placebos (random options, stale fits) give about the same and PRE is -14%: the value is in the rules, not in the rolling selection; as an exact joint it is untested. (3) Exact one-layer variants on the JN04-live base (K7 flat, C22, E1, F3, P7 cap/table, ATR skip, post-stop blackout) are queued (tag RF); candidate v2.10 and the code-change list follow when they land.

Generated 2026-11-14 20:10 UTC (epoch 1794687035). Exact engine for every verdict dollar; first-order composition only to rank (always labelled). Shadow only, no PASS claims. Prereg autopilot/REFIT1122_PREREG.md (sha in DECISIONS.md). Code outputs/code/th_refit1122/; bulk /mnt/l2/l2vast/_refit1122/.

## 0. Plan (first publish, 2026-11-14 ~17:00Z)
1. Stage 1 - candidate sets per layer from existing results (DS3_JOINT top-K / pools, registered topK, the 43-month exact cells on the JN05W2 base and the survivor cells from priorities 2-11 as they reach 43 months).
2. Stage 2 - first-order scoring on the exact trade tables: for each refit date (every 14 days from 2024-01-01, training = trailing 26 weeks ending 7 days before) choose, layer by layer and session by session, the setting with the smallest equal-mean trailing max DD (worst week, stops/wk, mean after), tolerant gate (trailing mean >= 85% of base), coordinate descent from the current setting; trade the next 14 days.
3. Stage 3 - exact re-run only for the winning combination per roll (cached by setting hash; tag RF, quota 6 workers) and exact realised walk-forward = concatenation of the exact OOS pieces. FIRST-ORDER numbers stay labelled until the exact piece lands.
4. Placebos beside every number: stale-fit refits (training window shifted 11 / 23 / 37 days) and random layer settings (5 seeds). Frozen arms: LIVE_FROZEN, JN05W2J_FROZEN, BEST_SINGLE_FIT (pick once, 26 weeks before 2024-01-01) and an IN-SAMPLE hindsight pick (labelled).
5. Deliver: candidate v2.10 policy file (exact live policy-file syntax) + v2.0 code-change list with each rule's spec as scored + the session-by-session realised walk-forward table (recent windows primary).

Coordination: W-JV (a5266a6235f1c7bbb) builds the 8-32 combos of shelved candidates (A, B, C, London range, P7 Asia re-entry); this page does the full-layer refit and takes their cells as candidates when they have 43 months. Survivors of priorities 2-11 (W-LR, W-PR, W-RA, W-NT, W-PM, W-TD) enter the same way.

## 1. Layers varied together and their current values (as coded in the exact sets; the v2.9 live spec itself is not in the owned files: ~/DS7.cs v1.9a and the live trade file are the ground truth W-EV compares against, so JN05W2J is labelled an engine proxy, not the live policy)
| layer | current value in the engine reference (JN05W2J / panel) | candidate pool (stage 1) |
|--|--|--|
| LOT (P7 only) | rolling-Calmar gate: P7 shadow Calmar over the last 10 label days < 1.0 -> lots x0.5 (cell p7_other:f4181da4c118). Panel base: P7 session table 7,4,0,4,0,0, P7 day cap 8,400 | lot_tables, p7_other cells (down-only), lot-table cells of priority 11 |
| SIGQ | all books: zone distance dA >= 70th pct of previous months -> x0.5 (signal_quality:b9a6edabcd7b) | signal_quality pool |
| REG | P7 only: 5-min ATR(14) / 20-day median >= 1.3 -> x0.5 (regime:f1f4301eae70) | regime pool |
| STACK | same-side lots cap 6 in London, truncate (exposure_stack cap6_trunc sess_london) | equal_risk, equity_state, exposure_stack |
| SIZER, COOL, ZONE, A06, B02 | live = no change (m = 1) | sizer, cooldown, zone, a06_slots, b02 pools |
| ATR skip | P7 entries skipped when 5-min ATR(14) / 20-day median >= 1.6 (JN04_LIVE_SPEC D1; exact cell JQ06); NOT part of the JN05W2J reference set, so 'live' here = no skip | thresholds 1.4 / 1.6 / 1.8 (exact cells TL3J_RF_ATR*); London range-used-up cells (W-LR) |
| blackout | P7 post-stop same-side 30-minute blackout (JN04_LIVE_SPEC D2, R5_BO_3); NOT part of the JN05W2J reference set, so 'live' here = no blackout | 15 / 30 / 60 min (exact cells TL3J_RF_BO*); W-PR / W-RA re-entry cells |
| context cut | P7 cut by entry context: fresh 45 / 5x / w5 / p10, rechase 30 / 10x / w5 / p2 (F3) | F3, F4, cut cells per book |
| WL_E1 | P7, sessions asia / london / nyam / nypm: skip the 3rd+ consecutive same-side loser of a session unless new evidence (new session extreme or opposite-side entry) | WG_E1 / WL_E1 variants, re-entry cells (W-RA, W-PR) |
| C22 | skip every new entry once the stack closed >= 22 trades in the label day and the stack day P&L <= -2 R (R = $1,200) | C14 / C18 / C22 |
| breadth (BR3S) | P7: skip when breadth_ext15 == 3 | BR3S variants |
| K7 flat cut | K7 flat loss cut -45 pts | FLAT40 / 42 / 45 / 50 and per-book cuts (W-PM) |
| profit rules | no entry-side profit rule in the engine reference; THP profit lines not live (THP_POLICY_D7_N: no line passed); near-target ladders arrive from W-NT | lock ladders per book (W-NT), profit cells |
State-cut units as coded in the set json: P7 40 / 5x / w5 / p3, M7 30 / 10x / w2 / p2, U7 30 / 60x / w15 / p5, A7 30 / 60x / w15 / p3, H7 15 / 30x / w10 / p2 (35 / 20x / w2 / p1 in session 3), O7 25 / 20x / w10.

## 2. Frozen-policy reference numbers (exact, 43 months, measured fills, $4.84 RT). LPB_BASE = live panel base; JN04RM = JN04 layers as rules on the panel; JN05W2 = panel + F3 + E1 + C22 + BR3S + FLAT45K without the JN04 lot layers; JN05W2J = JN05W2 on the JN04RM base. Data end 2026-10-30; W44 = 2026-10-26..11-01. The DD-cut and d-mean columns are against LPB_BASE.

| arm | window | weeks | mean $/wk | max DD | worst wk | full stops/wk | max DD no W44 | DD cut vs LPB % | d mean vs LPB | 5 best LPB wks kept | LPB winners turned losing |
|--|--|--|--|--|--|--|--|--|--|--|--|
| LPB_BASE | L1M | 4 | 341 | 51253 | -51253 | 19.8 | 0 |  |  |  |  |
| LPB_BASE | L3M | 13 | 11957 | 77224 | -51253 | 20.8 | 77224 |  |  |  |  |
| LPB_BASE | L6M | 26 | 18697 | 77224 | -51253 | 22.7 | 77224 |  |  |  |  |
| LPB_BASE | HOLD | 52 | 15236 | 78842 | -58258 | 22.2 | 78842 |  |  |  |  |
| LPB_BASE | PRE | 75 | 11685 | 99479 | -56283 | 17.1 |  |  |  |  |  |
| LPB_BASE | X' | 44 | 1334 | 122553 | -51085 | 17.4 |  |  |  |  |  |
| LPB_BASE | GAP | 18 | 15327 | 63540 | -63540 | 17.6 |  |  |  |  |  |
| JN04RM | L1M | 4 | 3824 | 27056 | -16664 | 21.8 | 10392 | 47.2 | 3483 | 11.22 | 1/2 |
| JN04RM | L3M | 13 | 12585 | 41699 | -25704 | 22.1 | 41699 | 46.0 | 628 | 0.82 | 1/8 |
| JN04RM | L6M | 26 | 18457 | 41699 | -39092 | 23.3 | 41699 | 46.0 | -240 | 0.87 | 1/19 |
| JN04RM | HOLD | 52 | 12384 | 72757 | -49731 | 22.5 | 72757 | 7.7 | -2852 | 0.84 | 3/37 |
| JN04RM | PRE | 75 | 9247 | 66714 | -42854 | 17.2 |  | 32.9 | -2438 | 0.66 | 5/48 |
| JN04RM | X' | 44 | 1537 | 64077 | -26950 | 17.5 |  | 47.7 | 203 | 0.70 | 4/24 |
| JN04RM | GAP | 18 | 13566 | 39147 | -39147 | 17.6 |  | 38.4 | -1761 | 0.79 | 1/14 |
| JN05W2 | L1M | 4 | 606 | 36371 | -36371 | 10.0 | 0 | 29.0 | 266 | 1.78 | 0/2 |
| JN05W2 | L3M | 13 | 16015 | 36371 | -36371 | 9.7 | 30533 | 52.9 | 4059 | 0.75 | 0/8 |
| JN05W2 | L6M | 26 | 25137 | 36371 | -36371 | 10.3 | 30533 | 52.9 | 6440 | 0.77 | 2/19 |
| JN05W2 | HOLD | 52 | 17489 | 63185 | -55145 | 10.5 | 63185 | 19.9 | 2253 | 0.75 | 4/37 |
| JN05W2 | PRE | 75 | 10168 | 76186 | -52547 | 9.3 |  | 23.4 | -1518 | 0.73 | 5/48 |
| JN05W2 | X' | 44 | 3585 | 55326 | -21663 | 10.8 |  | 54.9 | 2251 | 0.87 | 3/24 |
| JN05W2 | GAP | 18 | 12376 | 68947 | -68947 | 9.7 |  | -8.5 | -2951 | 0.70 | 1/14 |
| JN05W2J | L1M | 4 | 2631 | 17862 | -14035 | 10.8 | 3827 | 65.1 | 2290 | 7.72 | 1/2 |
| JN05W2J | L3M | 13 | 14942 | 17862 | -14035 | 9.9 | 13387 | 76.9 | 2985 | 0.69 | 1/8 |
| JN05W2J | L6M | 26 | 20865 | 23965 | -23965 | 10.1 | 23965 | 69.0 | 2168 | 0.66 | 1/19 |
| JN05W2J | HOLD | 52 | 14405 | 43622 | -35078 | 10.4 | 43622 | 44.7 | -831 | 0.63 | 2/37 |
| JN05W2J | PRE | 75 | 7254 | 56843 | -33380 | 9.3 |  | 42.9 | -4431 | 0.51 | 7/48 |
| JN05W2J | X' | 44 | 3798 | 39577 | -18853 | 10.7 |  | 67.7 | 2464 | 0.67 | 2/24 |
| JN05W2J | GAP | 18 | 11987 | 47481 | -47481 | 9.9 |  | 25.3 | -3340 | 0.65 | 2/14 |

## 3. Stage 2a - lot-level layers (SIZER LOT SIGQ REG STACK COOL ZONE A06 B02), rolling refit, FIRST-ORDER on the JN05W2 exact trade table (live proxy = JN05W2 x the four JN04 cells; session-group slots)
Procedure config A: 4 session-group slots per layer (Asia / London / NY AM+pre / NY PM+close), shortlist 4 per slot, 3 coordinate-descent passes, trailing 26 weeks, 14-day refit, 79 refits 2023-10-16..2026-10-26, mean gate 85%, no hysteresis. Each cell below = max-DD cut % vs the frozen live proxy / d mean $/wk, both on the same OOS days. (+ cut = shallower.) Live-proxy check: the first-order JN05W2 x JN04 series has L6M max DD 23,355 / mean 22,719 vs the exact JN05W2J 23,965 / 20,865 (weekly correlation 0.84-0.93 across windows).

| arm | L3M | L6M | HOLD | PRE | X' | GAP |
|--|--|--|--|--|--|--|
| ROLLING (real, 14-day refit) | -173% / -10399 | -82% / -15667 | +4% / -8554 | +27% / -3279 | -51% / -6022 | +11% / -7981 |
| stale-fit placebo 11 d | -81% / -7726 | -20% / -11928 | +11% / -6425 | -1% / -2616 | -162% / -5122 | +21% / -3704 |
| stale-fit placebo 23 d | -11% / -7720 | +26% / -12276 | -15% / -6072 | +34% / -2368 | -32% / -4458 | +5% / -3736 |
| stale-fit placebo 37 d | +94% / -6883 | +57% / -9908 | -67% / -7095 | +33% / -3079 | -213% / -5310 | -3% / -5095 |
| random layers seed 1 | -12% / -2913 | +12% / -8102 | +21% / -3025 | +28% / -977 | -1% / +603 | +25% / -3027 |
| random layers seed 2 | +41% / -3438 | +61% / -4555 | -2% / -2662 | +36% / -694 | -83% / -3099 | +32% / -1631 |
| random layers seed 3 | +53% / -3052 | -28% / -9486 | +14% / -4998 | +28% / -1477 | +54% / -1125 | +11% / -2419 |
| random layers seed 4 | +6% / -155 | +38% / -3169 | -17% / -2004 | +19% / +983 | +29% / -932 | +5% / -6057 |
| random layers seed 5 | +51% / -4040 | +45% / -6009 | +21% / -2133 | +18% / -2086 | -65% / -1083 | +22% / -3078 |
| BEST_SINGLE_FIT (pick once 2023-10) | +0% / -7517 | +34% / -9262 | +26% / -7375 | -10% / -3803 | -153% / -4838 | +10% / -5809 |
| HINDSIGHT whole-sample pick (IN-SAMPLE) | +34% / -4292 | +29% / -6919 | +58% / -1844 | +62% / +594 | +7% / +1094 | +55% / -2042 |

Per-refit: 79 refits, 72% of 2-week OOS periods had a shallower period max DD than live (the program's "beat %"), mean refit changes 23.8 of 36 slots; recent 6 refits (2026-07..10): 08-03 B 08-17 L 08-31 L 09-14 B 09-28 B 10-12 L. The period-beat statistic is not the verdict: the concatenated realised series is.

### Realised rolling walk-forward vs frozen live proxy (config A), recent windows first
| window | weeks | WF mean $/wk | live mean | d mean | WF max DD | live max DD | DD cut % | equal-mean cut % | WF worst wk | live worst wk | full stops/wk WF / live | 5 best live wks kept | live winners turned losing | DD cut % no W44 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| L1M | 2 | 13504 | 16054 | -2550 | 0 | 0 |  |  | 11238 | 10481 |  | 0.84 | 0/2 |  |
| L3M | 11 | 7995 | 18394 | -10399 | 40528 | 14854 | -172.8 | -527.7 | -16884 | -11155 |  | 0.70 | 2/9 |  |
| L6M | 24 | 9919 | 25586 | -15667 | 40528 | 22316 | -81.6 | -368.5 | -22978 | -22316 |  | 0.47 | 4/20 |  |
| HOLD | 50 | 8511 | 17065 | -8554 | 53922 | 56291 | 4.2 | -92.1 | -43639 | -40603 |  | 0.58 | 8/39 |  |
| PRE | 75 | 4965 | 8244 | -3279 | 43104 | 58976 | 26.9 | -21.4 | -35114 | -33832 |  | 0.54 | 6/47 |  |
| X' | 16 | 298 | 6320 | -6022 | 27159 | 18038 | -50.6 | -3090.8 | -23071 | -9938 |  | 0.19 | 2/9 |  |
| GAP | 18 | 1630 | 9611 | -7981 | 46563 | 52245 | 10.9 | -425.6 | -46563 | -52245 |  | 0.52 | 4/13 |  |

### Session by session (same OOS days; group series are first-order sums of the chosen options)
| session group | window | WF mean | live mean | d mean | WF max DD | live max DD | DD cut % |
|--|--|--|--|--|--|--|--|
| Asia | L3M | 8907 | 16316 | -7409 | 12023 | 9800 | -22.7 |
| Asia | L6M | 8703 | 20654 | -11951 | 28242 | 19707 | -43.3 |
| Asia | HOLD | 7933 | 14179 | -6246 | 64716 | 60137 | -7.6 |
| Asia | PRE | 5252 | 7288 | -2036 | 35563 | 44074 | 19.3 |
| London | L3M | -1156 | 1311 | -2467 | 44664 | 30809 | -45.0 |
| London | L6M | -494 | 1372 | -1866 | 44664 | 31235 | -43.0 |
| London | HOLD | -35 | 1925 | -1960 | 50809 | 37160 | -36.7 |
| London | PRE | -1033 | -323 | -711 | 115943 | 86402 | -34.2 |
| NY AM + pre | L3M | 103 | 327 | -224 | 8869 | 9737 | 8.9 |
| NY AM + pre | L6M | 767 | 1638 | -871 | 10081 | 9737 | -3.5 |
| NY AM + pre | HOLD | 610 | 442 | +168 | 30453 | 60006 | 49.2 |
| NY AM + pre | PRE | 602 | 1111 | -509 | 27536 | 30336 | 9.2 |
| NY PM + close | L3M | 141 | 440 | -300 | 4666 | 4357 | -7.1 |
| NY PM + close | L6M | 942 | 1922 | -979 | 3362 | 3965 | 15.2 |
| NY PM + close | HOLD | 3 | 519 | -515 | 22692 | 26021 | 12.8 |
| NY PM + close | PRE | 145 | 168 | -23 | 13318 | 33766 | 60.6 |

### Procedure variants (family of 9 configs incl. A; groups_gate_mingain_K; reported all, none selected on these numbers)
| config | period-beat | slots changed/refit | L3M | L6M | HOLD | PRE | X' | GAP |
|--|--|--|--|--|--|--|--|--|
| all_0.85_0_4 | 66% | 6.5 | +29% / -2221 | +42% / -9894 | +15% / -4426 | +22% / -1609 | -63% / -1559 | +3% / -8284 |
| all_0.95_0_4 | 65% | 6.9 | +56% / -558 | -45% / -8796 | +3% / -4616 | +16% / -2371 | -63% / -2054 | +6% / -5319 |
| all_1_0.05_4 | 61% | 6.0 | -13% / -1553 | -2% / -8130 | -24% / -4188 | +17% / -2477 | -99% / -3695 | +21% / -5753 |
| all_1_0_4 | 56% | 6.9 | +45% / -2443 | -16% / -8518 | -12% / -5320 | -1% / -2022 | -101% / -4430 | +16% / -3879 |
| sess_0.95_0_4 | 66% | 24.2 | -68% / -8057 | -12% / -13535 | +31% / -6591 | +18% / -3558 | -2% / -5512 | +3% / -8998 |
| sess_1_0.05_4 | 67% | 13.3 | -129% / -7000 | -52% / -9408 | -8% / -4460 | +6% / -4061 | -177% / -6905 | +13% / -3547 |
| sess_1_0.1_4 | 67% | 9.4 | -129% / -7071 | -52% / -7921 | +40% / -4223 | +4% / -3631 | -113% / -6096 | +2% / -2913 |
| sess_1_0_4 | 67% | 24.1 | -82% / -8102 | -21% / -12747 | -19% / -7311 | +3% / -3577 | -45% / -3932 | +5% / -6369 |

### REFIT 2026-11-22 dry run of the lot-layer procedure (first-order; training = 26 weeks ending 2026-11-05; NOT recommended: the walk-forward above rejects the procedure)
| slot (layer/session group) | option the procedure would pick |
|--|--|
| SIZER / G0 | B:ad781ec155cd |
| SIZER / G1 | A:6f47f1aaccdd |
| SIZER / G2 | A:cdcdd4f17f1f |
| LOT / G0 | F:a68edc4be139 |
| LOT / G1 | F:15811c04e522 |
| LOT / G2 | F:e42de98e2549 |
| LOT / G3 | F:2e9c3f0fff4d |
| SIGQ / G1 | G:0990ace9a026 |
| SIGQ / G2 | G:df9af6194c0c |
| REG / G0 | H:e933d2e9378d |
| REG / G1 | H:95bbdf3611cf |
| REG / G2 | H:c00d0fcf7609 |
| REG / G3 | H:d67f7b45133a |
| STACK / G0 | D:D|consec_loss|book_k4_f0.00|P7 |
| STACK / G1 | E:E|total_lots_cap|cap6_trunc|sess_london |
| STACK / G3 | D:D|week_loss_stack|X10000_f0.50|ALL |
| COOL / G0 | L:7a1cd9c2ffeb |
| COOL / G2 | L:d2043b2b96f4 |
| COOL / G3 | L:2bb80ec16443 |
| ZONE / G1 | ZN_STRUCT_b869631b68:26b7f8fa29cf |
| ZONE / G2 | ZN_STRUCT_b869631b68:ae73d73ff5b8 |
| ZONE / G3 | ZN_STRUCT_b869631b68:2ed4ef3a671c |

## 2b. Stage 1 - candidate sets per layer, stand-alone EXACT scores vs the base JN05W2 (window shown only when all its months are DONE; cut = max-DD cut %, + shallower; dm = d mean $/wk; st = full stops/wk change; b5 = share of the 5 best base weeks kept; w2l = base winning weeks turned losing)

| layer | cell | months | L3M | L6M | HOLD | PRE | X' | GAP |
|--|--|--|--|--|--|--|--|--|
| A1E | SM_A1E_C10L | 12 | -42% / -5959 / +0.6 / 0.54 / 1 | -42% / -5318 / +0.2 / 0.79 / 1 | -40% / -4226 / +0.2 / 0.93 / 4 |  |  |  |
| A1E | SM_A1E_L0L | 12 | -1% / +1738 / +0.4 / 1.12 / 0 | -1% / -13 / -0.1 / 1.00 / 0 | -15% / +1010 / -0.1 / 0.98 / 0 |  |  |  |
| A1E | SM_A1E_XL | 43 | +0% / -673 / +0.1 / 1.01 / 0 | +0% / +508 / -0.1 / 1.00 / 0 | -5% / +468 / +0.0 / 1.01 / 0 | -2% / +106 / +0.0 / 1.00 / 0 | -3% / -155 / +0.0 / 0.98 / 1 | -3% / +40 / +0.0 / 1.01 / 0 |
| G2M7 | G2_M7_HALF | 12 | +2% / -85 / +0.2 / 0.97 / 0 | +2% / -178 / +0.1 / 1.02 / 0 | +14% / +314 / +0.0 / 1.02 / 0 |  |  |  |
| G2M7 | G2_M7_LON | 12 | -5% / -971 / -0.2 / 0.96 / 0 | -5% / -676 / -0.3 / 0.98 / 0 | +2% / -114 / -0.5 / 0.99 / 2 |  |  |  |
| G2M7 | G2_M7_NYAM | 12 | -8% / -1091 / -0.2 / 0.89 / 0 | -8% / -1178 / -0.3 / 1.00 / 1 | +26% / -315 / -0.3 / 1.01 / 2 |  |  |  |
| G2P7 | G2_P7A_BW | 12 | +16% / -1593 / +0.3 / 0.86 / 2 | +16% / +602 / +0.1 / 0.98 / 2 | -30% / -2770 / +0.1 / 0.79 / 4 |  |  |  |
| G2P7 | G2_P7A_BWD | 12 | +66% / -617 / +0.2 / 0.92 / 2 | +22% / -1874 / +0.2 / 0.79 / 3 | -22% / -2331 / +0.2 / 0.66 / 5 |  |  |  |
| G2P7 | G2_P7A_PRE | 43 | +32% / +3105 / +0.1 / 0.89 / 0 | +32% / +2636 / +0.2 / 0.78 / 0 | +14% / +956 / +0.2 / 0.78 / 3 | -15% / -361 / +0.1 / 0.97 / 6 | -11% / +1022 / +0.0 / 0.94 / 4 | +1% / +3606 / +0.1 / 1.03 / 1 |
| G3_R2 | G3_R2_all_L | 43 | -96% / -1663 / +0.0 / 1.07 / 1 | -96% / -3558 / -0.9 / 0.96 / 2 | -18% / +2357 / -0.8 / 1.07 / 2 | -37% / +1744 / -0.5 / 0.94 / 4 | -23% / +423 / -0.5 / 1.02 / 3 | -12% / -1860 / -0.3 / 0.95 / 3 |
| G3_R2 | G3_R2_ct_L | 43 | -2% / -80 / -0.2 / 1.03 / 0 | -2% / -43 / -0.5 / 0.98 / 0 | -4% / +833 / -0.5 / 1.01 / 2 | -0% / -285 / -0.3 / 0.93 / 3 | -4% / +264 / -0.5 / 1.01 / 1 | -7% / -2278 / -0.3 / 0.86 / 1 |
| G3_R2 | G3_R2_lf70_L | 43 | -2% / +483 / +0.0 / 1.00 / 0 | -2% / +393 / -0.1 / 1.02 / 0 | +1% / +444 / -0.1 / 1.01 / 0 | +2% / -24 / -0.0 / 1.01 / 1 | +0% / +62 / +0.0 / 1.00 / 0 | +0% / -84 / -0.1 / 0.99 / 0 |
| G3_R2 | G3_R2_sz15_L | 43 | -28% / -2390 / -0.2 / 1.00 / 1 | -28% / -602 / -0.5 / 0.94 / 1 | -9% / +1477 / -0.3 / 1.00 / 3 | -10% / +975 / -0.1 / 1.08 / 1 | +14% / -849 / -0.1 / 1.06 / 1 | -8% / +1735 / -0.1 / 1.11 / 1 |
| G3_R2 | G3_R2_tg90_L | 43 | -5% / +2638 / +0.5 / 1.11 / 0 | -5% / -2677 / -0.1 / 0.93 / 1 | +1% / +881 / -0.1 / 0.91 / 2 | -30% / +214 / -0.1 / 0.96 / 1 | +21% / +258 / +0.1 / 0.91 / 0 | +7% / -717 / +0.1 / 0.92 / 1 |
| G3_R3 | G3_R3_all_L | 43 | -39% / +3820 / -0.3 / 1.09 / 0 | -39% / +1000 / -0.7 / 1.02 / 1 | -5% / +3263 / -0.8 / 0.98 / 1 | -23% / +842 / -0.2 / 0.90 / 2 | -6% / -689 / -0.3 / 1.02 / 4 | -9% / -3003 / -0.2 / 0.80 / 2 |
| G3_R3 | G3_R3_ct_L | 6 | +0% / +306 / -0.3 / 1.03 / 0 | +0% / +23 / -0.3 / 0.99 / 0 |  |  |  |  |
| G3_R3 | G3_R3_lf70_L | 43 | -2% / +659 / +0.0 / 1.04 / 0 | -2% / +466 / -0.1 / 1.02 / 0 | +1% / +399 / -0.1 / 1.01 / 0 | +1% / +78 / -0.0 / 1.01 / 1 | +0% / +55 / +0.0 / 1.00 / 0 | +0% / +83 / -0.1 / 1.00 / 0 |
| G3_R3 | G3_R3_sz15_L | 43 | -20% / +544 / -0.2 / 1.02 / 0 | -20% / +1010 / -0.4 / 0.97 / 0 | -8% / +1300 / -0.3 / 0.97 / 1 | +6% / +1421 / -0.1 / 1.10 / 0 | -1% / -847 / -0.0 / 1.07 / 3 | -4% / +827 / -0.1 / 1.08 / 1 |
| G3_R3 | G3_R3_tg90_L | 43 | -15% / +2597 / +0.5 / 1.09 / 0 | -15% / -352 / +0.0 / 0.98 / 0 | -1% / +872 / -0.1 / 0.98 / 1 | -30% / -229 / -0.1 / 0.95 / 2 | +16% / -30 / +0.1 / 0.93 / 0 | +4% / +555 / -0.1 / 0.93 / 1 |
| G3_S2 | G3_S2_all_L | 43 | -61% / -1418 / -1.5 / 0.92 / 0 | -61% / -3422 / -2.0 / 0.84 / 0 | -100% / -567 / -1.6 / 0.85 / 5 | -3% / +879 / -0.9 / 0.61 / 4 | +35% / +987 / -0.7 / 0.98 / 6 | -38% / -5099 / -0.5 / 0.64 / 2 |
| G3_S2 | G3_S2_ct_L | 43 | -30% / +3078 / -1.7 / 1.11 / 0 | -30% / +65 / -1.9 / 0.97 / 0 | -13% / +132 / -1.4 / 0.95 / 1 | +16% / +304 / -1.0 / 0.78 / 4 | +21% / +2015 / -0.7 / 1.12 / 0 | -11% / -5322 / -0.6 / 0.70 / 2 |
| G3_S2 | G3_S2_lf70_L | 43 | -2% / +346 / -0.1 / 0.98 / 0 | -2% / -685 / -0.3 / 0.95 / 0 | +1% / +62 / -0.2 / 0.93 / 0 | +2% / -60 / -0.0 / 0.98 / 1 | +1% / +89 / -0.0 / 1.00 / 0 | +0% / -251 / -0.2 / 0.98 / 0 |
| G3_S2 | G3_S2_sz15_L | 43 | -18% / +3434 / -0.5 / 1.29 / 0 | -18% / -1435 / -0.7 / 0.95 / 0 | -16% / +213 / -0.5 / 1.01 / 2 | -6% / +883 / -0.2 / 1.07 / 2 | +21% / -580 / -0.0 / 1.08 / 2 | -15% / +2276 / -0.2 / 1.21 / 2 |
| G3_S2 | G3_S2_tg90_L | 6 | -5% / -6476 / +0.8 / 0.63 / 0 | -5% / -6682 / +0.3 / 0.86 / 1 |  |  |  |  |
| G3_S3 | G3_S3_all_L | 43 | -73% / -1688 / -1.3 / 0.93 / 1 | -73% / -4287 / -1.8 / 0.81 / 1 | -39% / -1544 / -1.4 / 0.81 / 4 | -8% / +1598 / -1.0 / 0.75 / 4 | +28% / +221 / -0.6 / 0.93 / 6 | -34% / -4384 / -0.4 / 0.66 / 2 |
| G3_S3 | G3_S3_ct_L | 6 | -44% / +1489 / -1.5 / 1.01 / 0 | -44% / -467 / -1.9 / 0.95 / 0 |  |  |  |  |
| G3_S3 | G3_S3_lf60_L | 43 | -4% / -53 / +0.0 / 0.99 / 0 | -4% / -199 / -0.1 / 0.98 / 0 | +1% / +128 / -0.0 / 0.96 / 0 | +1% / -133 / -0.0 / 1.01 / 0 | +0% / +43 / +0.0 / 1.00 / 0 | +0% / -260 / -0.1 / 0.98 / 0 |
| G3_S3 | G3_S3_lf70_L | 43 | -2% / +346 / -0.1 / 0.98 / 0 | -2% / -657 / -0.3 / 0.95 / 0 | +1% / +58 / -0.2 / 0.93 / 0 | +2% / -88 / -0.0 / 0.97 / 1 | +1% / +80 / -0.0 / 1.00 / 0 | +0% / -251 / -0.2 / 0.98 / 0 |
| G3_S3 | G3_S3_lf75_L | 43 | -1% / +174 / -0.1 / 0.97 / 0 | -1% / -402 / -0.3 / 0.96 / 0 | +1% / +361 / -0.2 / 0.96 / 0 | +2% / -621 / -0.1 / 0.93 / 0 | +1% / +110 / -0.0 / 1.00 / 0 | +0% / -61 / -0.2 / 0.99 / 0 |
| G3_S3 | G3_S3_sz125_L | 43 | -8% / +987 / +0.1 / 1.09 / 0 | -8% / -725 / -0.2 / 0.93 / 0 | +3% / -160 / -0.2 / 0.94 / 1 | -11% / +277 / -0.1 / 1.11 / 0 | +3% / +378 / +0.0 / 1.10 / 1 | -4% / +1205 / -0.1 / 1.07 / 0 |
| G3_S3 | G3_S3_sz15_L | 43 | -18% / +1940 / -0.5 / 1.22 / 0 | -18% / -2262 / -0.5 / 0.95 / 0 | -20% / -618 / -0.4 / 1.00 / 2 | -5% / +959 / -0.2 / 1.07 / 2 | +21% / -186 / -0.0 / 1.09 / 2 | -11% / +2660 / -0.2 / 1.21 / 1 |
| G3_S3 | G3_S3_sz20_L | 43 | -26% / +1017 / -0.5 / 1.12 / 0 | -26% / -2442 / -0.7 / 0.94 / 0 | -20% / -1427 / -0.5 / 1.04 / 2 | -11% / -87 / -0.2 / 1.08 / 4 | +18% / -208 / -0.0 / 1.10 / 2 | -15% / +2505 / -0.2 / 1.21 / 1 |
| G3_S3 | G3_S3_tg120_L | 43 | -4% / -3682 / +0.5 / 0.71 / 0 | -4% / -7280 / +0.1 / 0.73 / 1 | -14% / -1463 / -0.1 / 0.80 / 4 | +8% / +1047 / -0.1 / 0.87 / 4 | -3% / -693 / +0.0 / 0.85 / 1 | -0% / +800 / -0.1 / 1.01 / 1 |
| G3_S3 | G3_S3_tg75_L | 43 | +3% / -5178 / +0.5 / 0.66 / 0 | +3% / -4135 / +0.2 / 0.94 / 0 | -1% / -1551 / +0.1 / 0.90 / 2 | +8% / +1128 / -0.1 / 1.10 / 0 | +4% / +18 / +0.0 / 0.87 / 0 | +0% / -1291 / +0.1 / 0.87 / 1 |
| G3_S3 | G3_S3_tg90_L | 43 | +9% / -4684 / +0.5 / 0.67 / 0 | +9% / -5678 / +0.1 / 0.84 / 1 | +10% / -1812 / -0.1 / 0.80 / 3 | +6% / -360 / -0.0 / 0.81 / 3 | +6% / -136 / +0.1 / 0.85 / 1 | +4% / +740 / -0.1 / 0.92 / 1 |
| G3_S5 | G3_S5_all_L | 43 | -64% / -2207 / -1.5 / 0.92 / 0 | -64% / -7990 / -1.9 / 0.72 / 1 | -51% / -5434 / -1.3 / 0.71 / 4 | +0% / +462 / -0.8 / 0.70 / 2 | +36% / +406 / -0.4 / 1.12 / 4 | -35% / -1216 / -0.6 / 0.81 / 0 |
| G3_S5 | G3_S5_ct_L | 43 | -7% / +3899 / -1.4 / 1.14 / 0 | -7% / +516 / -1.7 / 0.98 / 0 | -0% / +17 / -1.3 / 0.91 / 2 | +14% / +934 / -0.8 / 0.87 / 1 | +17% / +789 / -0.5 / 1.05 / 2 | -12% / -3044 / -0.5 / 0.72 / 0 |
| G3_S5 | G3_S5_lf70_L | 6 | +2% / +426 / -0.1 / 0.98 / 0 | +2% / -664 / -0.3 / 0.95 / 0 |  |  |  |  |
| G3_S5 | G3_S5_sz15_L | 43 | -13% / +3056 / -0.4 / 1.25 / 0 | -13% / -2575 / -0.5 / 0.92 / 0 | +6% / -660 / -0.4 / 1.00 / 0 | +3% / +704 / -0.2 / 1.11 / 1 | +18% / +169 / -0.0 / 1.08 / 1 | -12% / +1446 / -0.2 / 1.13 / 1 |
| G3_S5 | G3_S5_tg90_L | 43 | +9% / -2455 / +0.3 / 0.79 / 0 | +9% / -4894 / -0.0 / 0.80 / 1 | +10% / -2272 / +0.0 / 0.76 / 2 | +9% / -99 / +0.1 / 0.92 / 2 | +2% / +123 / +0.1 / 0.92 / 1 | +4% / +954 / -0.3 / 0.91 / 0 |
| JV_SHELF | SM_A6_halfNP7 | 43 | +12% / -691 / +0.2 / 0.94 / 0 | +12% / +383 / +0.0 / 1.04 / 0 | +12% / +724 / -0.0 / 1.03 / 0 | -8% / -42 / -0.0 / 0.97 / 0 | +8% / +243 / +0.0 / 0.99 / 0 | +2% / -915 / -0.1 / 0.94 / 1 |
| JV_SHELF | TL3_JV_A | 43 | +12% / -691 / +0.2 / 0.94 / 0 | +12% / +383 / +0.0 / 1.04 / 0 | +12% / +724 / -0.0 / 1.03 / 0 | -8% / -42 / -0.0 / 0.97 / 0 | +8% / +243 / +0.0 / 0.99 / 0 | +2% / -915 / -0.1 / 0.94 / 1 |
| JV_SHELF | TL3_JV_AB | 12 | +25% / +636 / -0.8 / 0.99 / 0 | +24% / +946 / -0.7 / 1.01 / 0 | +16% / +1391 / -0.7 / 1.02 / 0 |  |  |  |
| JV_SHELF | TL3_JV_ABC | 7 | +23% / +2001 / -2.4 / 1.08 / 0 | +9% / +1472 / -2.2 / 1.08 / 1 |  |  |  |  |
| JV_SHELF | TL3_JV_AC | 12 | +13% / +1203 / -2.0 / 1.05 / 0 | +9% / +1116 / -2.0 / 1.09 / 1 | -20% / +604 / -2.3 / 0.98 / 1 |  |  |  |
| JV_SHELF | TL3_JV_B | 43 | +12% / +1244 / -0.9 / 1.06 / 0 | +12% / +573 / -0.6 / 0.97 / 0 | +3% / +799 / -0.6 / 0.99 / 0 | -1% / -90 / -0.3 / 1.01 / 0 | +18% / +249 / -0.1 / 0.98 / 0 | +0% / +5 / -0.1 / 1.01 / 0 |
| JV_SHELF | TL3_JV_BC | 10 | +11% / +2739 / -2.7 / 1.12 / 0 | +9% / +1217 / -2.3 / 1.05 / 1 |  |  |  |  |
| JV_SHELF | TL3_JV_C | 12 | +1% / +1746 / -2.2 / 1.08 / 0 | +1% / +712 / -2.1 / 1.07 / 1 | -16% / +145 / -2.3 / 0.97 / 2 |  |  |  |
| LR_D3C | TL3_LR_D3C_a | 3 | +12% / -1806 / +1.6 / 0.88 / 0 |  |  |  |  |  |
| LR_D3C | TL3_LR_D3C_c | 3 | -1% / -681 / +0.7 / 0.95 / 0 |  |  |  |  |  |
| LR_D5SK13F | TL3_LR_D5SK13F_a | 3 | -6% / +201 / +0.1 / 1.01 / 0 |  |  |  |  |  |
| LR_HALF | TL3_LR_LH05 | 3 | +9% / -1674 / +0.2 / 0.84 / 0 |  |  |  |  |  |
| LR_HALF | TL3_LR_LH075 | 3 | +13% / -886 / +0.2 / 0.89 / 0 |  |  |  |  |  |
| LR_HALF | TL3_LR_LH1 | 3 | +6% / +39 / +0.2 / 0.97 / 0 |  |  |  |  |  |
| LR_HALF | TL3_LR_LH125 | 3 | +5% / +323 / +0.2 / 0.98 / 0 |  |  |  |  |  |
| LR_SHRINK | TL3_LR_LT05 | 3 | -36% / -1591 / -0.2 / 0.85 / 0 |  |  |  |  |  |
| LR_SHRINK | TL3_LR_LT075 | 3 | -20% / -782 / +0.0 / 0.95 / 0 |  |  |  |  |  |
| LR_SHRINK | TL3_LR_LT1 | 3 | -14% / -134 / +0.0 / 0.97 / 0 |  |  |  |  |  |
| LR_SHRINK | TL3_LR_LT125 | 3 | -12% / +320 / +0.2 / 0.99 / 0 |  |  |  |  |  |
| LR_SKIP | TL3_LR_LS05 | 3 | +6% / -2958 / -1.0 / 0.65 / 0 |  |  |  |  |  |
| LR_SKIP | TL3_LR_LS075 | 3 | +17% / -633 / -0.8 / 0.75 / 0 |  |  |  |  |  |
| LR_SKIP | TL3_LR_LS1 | 3 | +14% / +2725 / -0.8 / 0.97 / 0 |  |  |  |  |  |
| LR_SKIP | TL3_LR_LS125 | 3 | +12% / +4154 / -0.8 / 1.03 / 0 |  |  |  |  |  |
| NC_A7 | NC_A7_T10_10F | 43 | +0% / +219 / -0.3 / 1.02 / 0 | +0% / +306 / -0.2 / 1.00 / 0 | +0% / -106 / -0.2 / 1.00 / 0 | +2% / -51 / -0.0 / 1.00 / 0 | +0% / +27 / -0.0 / 1.00 / 0 | +0% / -24 / -0.1 / 1.00 / 0 |
| NC_K7 | NC_K7_F55_45 | 12 | +0% / -334 / +0.2 / 1.01 / 0 | +0% / +105 / +0.2 / 1.01 / 0 | -6% / -22 / +0.2 / 1.01 / 0 |  |  |  |
| NC_K7 | NC_K7_T20_20RC | 43 | +24% / +1432 / +0.0 / 1.02 / 0 | +24% / -61 / -0.0 / 0.97 / 0 | +1% / +308 / -0.0 / 0.97 / 0 | +5% / -232 / -0.0 / 0.99 / 0 | +0% / -212 / -0.0 / 1.00 / 1 | +1% / +42 / +0.0 / 0.98 / 1 |
| NC_K7 | NC_K7_T30_10RC | 12 | +0% / +235 / +0.0 / 1.01 / 0 | +0% / -1164 / +0.0 / 0.98 / 1 | +3% / -435 / -0.0 / 1.00 / 1 |  |  |  |
| NC_U7 | NC_U7_T10_15F | 43 | +12% / +1244 / -0.9 / 1.06 / 0 | +12% / +573 / -0.6 / 0.97 / 0 | +3% / +799 / -0.6 / 0.99 / 0 | -1% / -90 / -0.3 / 1.01 / 0 | +18% / +249 / -0.1 / 0.98 / 0 | +0% / +5 / -0.1 / 1.01 / 0 |
| NC_U7 | NC_U7_T20_15A | 12 | +8% / +916 / -1.1 / 1.05 / 0 | +8% / -27 / -0.9 / 0.99 / 0 | -8% / +69 / -0.8 / 0.98 / 0 |  |  |  |
| NC_U7 | NC_U7_T20_15F | 43 | +4% / +931 / -0.8 / 1.05 / 0 | +4% / +510 / -0.5 / 0.98 / 0 | +1% / +641 / -0.4 / 0.99 / 0 | +0% / +178 / -0.2 / 1.01 / 0 | +5% / +31 / -0.0 / 1.00 / 0 | +0% / +0 / +0.0 / 1.00 / 0 |
| NH_M7 | NH_M7_B9_X10N60 | 43 | +3% / +1327 / -0.1 / 1.05 / 0 | +3% / +681 / -0.1 / 1.01 / 0 | +3% / +449 / -0.1 / 1.02 / 0 | -9% / -10 / +0.0 / 1.00 / 0 | -6% / +41 / -0.0 / 1.01 / 0 | -2% / +149 / -0.1 / 1.01 / 0 |
| NH_M7 | NH_M7_C9_F2 | 43 | +2% / +451 / +0.0 / 1.01 / 0 | +2% / +290 / +0.0 / 1.02 / 0 | +4% / +185 / -0.1 / 1.02 / 0 | +0% / +72 / -0.0 / 1.00 / 0 | +2% / +148 / -0.1 / 1.03 / 1 | +0% / +365 / -0.1 / 1.00 / 0 |
| NH_U7 | NH_U7_B7_X20N60 | 12 | +5% / +874 / -0.3 / 1.06 / 0 | +5% / +976 / -0.5 / 0.97 / 0 | -3% / +935 / -0.5 / 0.98 / 0 |  |  |  |
| NH_U7 | NH_U7_B7_X30N120 | 43 | -0% / +715 / -0.2 / 1.06 / 0 | -0% / +1037 / -0.4 / 1.00 / 0 | -0% / +671 / -0.4 / 1.00 / 0 | -8% / +120 / -0.2 / 0.99 / 0 | -7% / -123 / -0.2 / 0.94 / 1 | -2% / -848 / -0.2 / 0.98 / 1 |
| NT_K7 | TL3_NT_K7_3_60_10_10 | 3 | +0% / +660 / +0.0 / 1.03 / 0 |  |  |  |  |  |
| NT_M7 | TL3_NT_M7_a_90_20_3 | 4 | +0% / +742 / +0.0 / 1.03 / 0 |  |  |  |  |  |
| PM_DAYHALF | TL3_PM_G5H | 6 | +5% / -501 / -0.3 / 0.97 / 0 | +5% / +13 / -0.3 / 0.96 / 0 |  |  |  |  |
| PR_BLK | TL3_PR_BLK_ENT | 3 | +11% / +245 / +0.0 / 1.02 / 0 |  |  |  |  |  |
| PR_BLK | TL3_PR_BLK_EXT | 3 | -41% / -2905 / +0.4 / 0.99 / 1 |  |  |  |  |  |
| PR_BLK | TL3_PR_BLK_M30 | 3 | +16% / +803 / +0.0 / 1.00 / 0 |  |  |  |  |  |
| PR_BLK | TL3_PR_BLK_M60 | 3 | -14% / +194 / -0.1 / 1.02 / 0 |  |  |  |  |  |
| PR_BLK | TL3_PR_BLK_OPP | 3 | -12% / -1491 / +0.2 / 0.91 / 0 |  |  |  |  |  |
| RA_BLK | TL3_RA_BLKi | 6 | -8% / -2816 / +0.1 / 0.94 / 0 | -8% / -2151 / -0.1 / 0.97 / 1 |  |  |  |  |
| RA_BLK | TL3_RA_BLKii | 3 | -12% / -1762 / +0.2 / 0.95 / 0 |  |  |  |  |  |
| RA_BLK | TL3_RA_BLKiii120 | 3 | -20% / -2580 / +0.0 / 0.96 / 0 |  |  |  |  |  |
| RA_BLK | TL3_RA_BLKiii30 | 3 | +13% / -59 / -0.2 / 0.95 / 0 |  |  |  |  |  |
| RA_BLK | TL3_RA_BLKiii60 | 3 | -11% / +91 / -0.2 / 1.01 / 0 |  |  |  |  |  |
| RA_BLK | TL3_RA_BLKiv | 3 | -17% / -2215 / -0.2 / 0.96 / 0 |  |  |  |  |  |
| RA_BLK | TL3_RA_BLKv | 3 | +9% / -959 / -0.1 / 0.93 / 0 |  |  |  |  |  |
| RA_CAP | TL3_RA_CAP2 | 3 | -37% / -3626 / -0.6 / 1.02 / 0 |  |  |  |  |  |
| RA_CAP | TL3_RA_CAP3 | 3 | +4% / -631 / +0.2 / 0.98 / 0 |  |  |  |  |  |
| RA_HALF | TL3_RA_HALF | 3 | -0% / -676 / +0.3 / 0.98 / 0 |  |  |  |  |  |
| RA_LCAP | TL3_RA_LCAP10 | 3 | -30% / -2385 / -0.1 / 0.99 / 0 |  |  |  |  |  |
| RA_LCAP | TL3_RA_LCAP15 | 3 | -26% / -1116 / -0.2 / 0.99 / 0 |  |  |  |  |  |
| SB | SB_DUP120H | 6 | +4% / +325 / -0.1 / 0.97 / 0 | +4% / -50 / -0.0 / 1.00 / 0 |  |  |  |  |
| SB | SB_DUP120P | 43 | +17% / +199 / +0.0 / 0.97 / 0 | +17% / -754 / +0.0 / 1.00 / 0 | +8% / -247 / +0.0 / 1.00 / 0 | -9% / -417 / -0.0 / 0.95 / 0 | -0% / +217 / -0.1 / 1.01 / 0 | +6% / +258 / -0.1 / 1.01 / 0 |
| SB | SB_DUP120S | 6 | -14% / -928 / -0.1 / 0.98 / 0 | -14% / -2021 / -0.2 / 1.02 / 0 |  |  |  |  |
| SB | SB_DUP300H | 12 | +31% / -203 / +0.0 / 0.93 / 0 | +25% / -507 / +0.0 / 0.98 / 0 | -8% / -321 / +0.0 / 0.98 / 0 |  |  |  |
| SB | SB_DUP300P | 6 | +21% / +139 / -0.2 / 0.99 / 0 | +21% / -2066 / -0.2 / 0.91 / 0 |  |  |  |  |
| SB | SB_DUP300S | 6 | -46% / -3910 / -0.1 / 0.89 / 0 | -46% / -3603 / -0.6 / 0.95 / 0 |  |  |  |  |
| SB | SB_DUP60H | 6 | +4% / +131 / +0.0 / 0.99 / 0 | +4% / -76 / +0.0 / 1.00 / 0 |  |  |  |  |
| SB | SB_DUP60P | 6 | +0% / -670 / +0.1 / 0.97 / 0 | +0% / -1195 / +0.0 / 1.00 / 0 |  |  |  |  |
| SB | SB_DUP60S | 6 | +4% / -2098 / +0.1 / 0.92 / 0 | +4% / -2659 / -0.0 / 0.96 / 0 |  |  |  |  |
| SB | SB_LE_bid0_T10M | 6 | -4% / -202 / -0.1 / 1.01 / 0 | -4% / -109 / +0.0 / 0.94 / 0 |  |  |  |  |
| SB | SB_LE_bid0_T10S | 6 | -58% / -8999 / -0.3 / 0.69 / 2 | -58% / -11798 / -0.8 / 0.61 / 3 |  |  |  |  |
| SB | SB_LE_bid0_T5M | 12 | +1% / +1394 / +0.2 / 1.13 / 0 | +1% / +132 / +0.3 / 0.94 / 0 | -5% / -625 / +0.2 / 0.99 / 2 |  |  |  |
| SB | SB_LE_mid0_T10M | 6 | -8% / -722 / -0.1 / 0.99 / 0 | -8% / -1151 / +0.1 / 0.91 / 0 |  |  |  |  |
| SB | SB_LE_mid0_T10Mt | 12 | +20% / +2250 / -0.1 / 1.10 / 0 | +20% / +1158 / +0.1 / 1.02 / 0 | -5% / +283 / +0.1 / 1.03 / 2 |  |  |  |
| SB | SB_LE_mid0_T10S | 6 | -52% / -4442 / +0.0 / 0.99 / 2 | -52% / -8170 / -0.8 / 0.75 / 3 |  |  |  |  |
| SB | SB_LE_mid0_T5M | 12 | +21% / +395 / +0.0 / 0.99 / 0 | +21% / -1203 / +0.2 / 0.87 / 1 | -4% / -1654 / +0.1 / 0.91 / 3 |  |  |  |
| SB | SB_LE_pb2_T10M | 6 | -7% / -298 / -0.1 / 1.00 / 0 | -7% / -923 / +0.0 / 0.91 / 0 |  |  |  |  |
| SB | SB_LE_pb4_T20M | 12 | +19% / +308 / +0.1 / 0.97 / 0 | +19% / -1245 / +0.3 / 0.99 / 1 | -7% / -488 / +0.2 / 1.01 / 3 |  |  |  |
| SB | SB_LE_pb4_T20S | 6 | -67% / -10970 / -0.2 / 0.56 / 2 | -67% / -12711 / -0.6 / 0.61 / 2 |  |  |  |  |
| SB | SB_LE_pb8_T20S | 6 | -32% / -13060 / -1.0 / 0.36 / 2 | -32% / -15855 / -0.9 / 0.39 / 2 |  |  |  |  |
| SB | SB_LE_wide | 6 | -5% / -529 / -0.1 / 0.99 / 0 | -5% / -251 / +0.1 / 0.94 / 0 |  |  |  |  |
| SB | SB_SJ0 | 6 | -0% / +742 / -0.1 / 1.01 / 0 | -0% / +561 / -0.0 / 1.01 / 0 |  |  |  |  |
| SB | SB_SJ1 | 6 | +0% / -19 / +0.0 / 1.00 / 0 | +0% / -33 / +0.0 / 1.00 / 0 |  |  |  |  |
| SB | SB_SJ5 | 6 | +0% / -2 / +0.0 / 1.00 / 0 | +0% / -6 / +0.0 / 1.00 / 0 |  |  |  |  |
| SB | SB_SJA1 | 6 | -1% / -218 / -0.2 / 0.99 / 0 | -1% / -82 / -0.2 / 1.00 / 0 |  |  |  |  |
| SB | SB_SJA3 | 6 | -0% / -302 / -0.2 / 1.00 / 0 | -0% / +9 / -0.2 / 1.00 / 0 |  |  |  |  |
| SB | SB_SL05 | 6 | -30% / +225 / -0.1 / 1.15 / 0 | -30% / +556 / +0.0 / 1.06 / 1 |  |  |  |  |
| SB | SB_SL1 | 6 | -29% / +267 / -0.1 / 1.15 / 0 | -29% / +653 / -0.0 / 1.02 / 0 |  |  |  |  |
| SB | SB_SL5 | 6 | +3% / -1537 / -0.2 / 0.98 / 0 | +3% / -473 / -0.1 / 0.88 / 0 |  |  |  |  |
| SB | SB_SLALL | 6 | -38% / +139 / +0.1 / 1.13 / 0 | -38% / -522 / +0.0 / 1.10 / 1 |  |  |  |  |
| SB | SB_SP100 | 12 | +2% / +1328 / +0.2 / 1.12 / 0 | +2% / +1532 / +0.2 / 1.11 / 0 | -58% / -246 / -0.0 / 1.06 / 1 |  |  |  |
| SB | SB_SP50 | 6 | -12% / +359 / +0.2 / 1.12 / 0 | -12% / -413 / +0.2 / 1.02 / 1 |  |  |  |  |
| SB | SB_SP85 | 43 | +16% / +1204 / +0.1 / 1.06 / 0 | +16% / +1203 / +0.0 / 1.02 / 1 | +16% / +579 / -0.0 / 1.00 / 1 | -4% / -900 / -0.1 / 0.93 / 2 | -5% / +192 / +0.0 / 1.05 / 0 | -14% / -847 / -0.1 / 1.03 / 0 |
| SB | SB_WK1 | 6 | -4% / +181 / +0.0 / 1.01 / 0 | -4% / +807 / +0.0 / 1.00 / 0 |  |  |  |  |
| SB | SB_WK2 | 6 | -3% / -61 / +0.0 / 1.01 / 0 | -3% / +488 / +0.0 / 1.00 / 0 |  |  |  |  |
| SB | SB_WK2L | 6 | -4% / -331 / +0.0 / 1.00 / 0 | -4% / +181 / +0.0 / 0.99 / 0 |  |  |  |  |
| SB | SB_WK2S | 6 | -3% / -21 / +0.0 / 1.01 / 0 | -3% / +940 / +0.0 / 1.00 / 0 |  |  |  |  |
| SB | SB_WK2T | 6 | -1% / +209 / +0.0 / 1.01 / 0 | -1% / +758 / +0.0 / 1.00 / 0 |  |  |  |  |
| SB | SB_WK3 | 6 | -3% / -34 / +0.0 / 1.01 / 0 | -3% / +577 / +0.0 / 1.00 / 0 |  |  |  |  |
| SB | SB_WK5 | 6 | -0% / +135 / +0.0 / 1.01 / 0 | -0% / +230 / +0.0 / 1.00 / 0 |  |  |  |  |
| TD_C1 | TL3_TD_C1_ct | 3 | +0% / +104 / +0.0 / 1.01 / 0 |  |  |  |  |  |
| TD_C1 | TL3_TD_C1_tg | 3 | +0% / +279 / +0.0 / 1.01 / 0 |  |  |  |  |  |

Cell format: cut % / dm / st / b5 / w2l. Cells in a layer exclude each other; layers add first-order in the refit. Only cells whose set json differs from JN05W2 in hooklist / state / works are pooled; outside-data (UW, TICK, UR, RU), identity, placebo and layer-OFF reference cells are excluded.

## 4. Hook / exit / entry layers, rolling joint refit, base JN05W2 (no JN04 lot layers; existing 43-month exact rules)
Slots = layer x session group (Asia / London / NY AM+pre / NY PM+close); each option is an EXACT one-layer cell, deltas vs the base cell are added across layers (FIRST-ORDER additive across layers; stage 3 re-runs the winners exactly). Eligibility: an option is usable at a refit only when its months cover the training window and the OOS fortnight. Mean gate 0.85 of live, hysteresis 0. 79 refits.

| arm | L3M | L6M | HOLD | PRE | X' | GAP |
|--|--|--|--|--|--|--|
| ROLLING (real) | +60% / +6066 | +49% / +3343 | -6% / +3281 | -14% / -1312 | +29% / +1885 | -4% / +4932 |
| stale-fit placebo 11 d | +59% / +5736 | +41% / +4374 | -8% / +4413 | -48% / -1597 | +36% / +1944 | +12% / +4404 |
| stale-fit placebo 23 d | +59% / +4653 | +48% / +1992 | -5% / +3524 | -25% / -1506 | +0% / +1268 | -2% / +3939 |
| stale-fit placebo 37 d | +67% / +6662 | +49% / +1048 | +12% / +3288 | -4% / -1030 | +38% / +3852 | -3% / +4288 |
| random options seed 1 | +47% / +5695 | +38% / +3270 | -13% / +2975 | -8% / -1235 | +31% / +2280 | -9% / +4584 |
| random options seed 2 | +42% / +6420 | +42% / +3698 | -7% / +3625 | -15% / -1157 | +23% / +1159 | -0% / +4399 |
| random options seed 3 | +59% / +4739 | +35% / +2058 | -5% / +2613 | -17% / -1552 | +27% / +1101 | +5% / +4464 |
| random options seed 4 | +48% / +3803 | +48% / +1076 | -12% / +1915 | -16% / -1291 | +25% / +1570 | -13% / +4450 |
| random options seed 5 | +48% / +5372 | +43% / +3260 | -5% / +3762 | -21% / -1431 | +11% / +970 | +0% / +5206 |
| BEST_SINGLE_FIT (pick once, first refit) | +72% / -426 | +69% / +851 | +14% / +1055 | -12% / -297 | +43% / +2535 | -3% / +1980 |
| HINDSIGHT whole-sample pick (IN-SAMPLE, full-coverage cells only) | +52% / +6207 | +52% / +5356 | +29% / +5016 | +28% / +1075 | -27% / +2264 | +20% / +4922 |

Cells = max-DD cut % vs the frozen base / d mean $/wk on the same OOS days (+ = shallower). Period-beat 47%, mean slots changed per refit 17.7.

### Realised rolling walk-forward vs frozen base, recent windows first
| window | weeks | WF mean $/wk | live mean | d mean | WF max DD | live max DD | DD cut % | equal-mean cut % | WF worst wk | live worst wk | full stops/wk WF / live | 5 best live wks kept | live winners turned losing | DD cut % no W44 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| L1M | 2 | 17556 | 19398 | -1842 | 0 | 0 |  |  | 1472 | 14801 | 24.0 / 14.0 | 0.91 | 0/2 |  |
| L3M | 11 | 28299 | 22233 | 6066 | 12271 | 30533 | 59.8 | 68.4 | -12271 | -26026 | 16.7 / 10.4 | 1.01 | 1/9 |  |
| L6M | 24 | 32090 | 28747 | 3343 | 15480 | 30533 | 49.3 | 54.6 | -15480 | -26026 | 14.2 / 10.7 | 0.72 | 1/19 |  |
| HOLD | 50 | 22198 | 18916 | 3281 | 66716 | 63185 | -5.6 | 10.0 | -54503 | -55145 | 14.6 / 10.6 | 0.70 | 3/37 |  |
| PRE | 75 | 8856 | 10168 | -1312 | 87109 | 76186 | -14.3 | -31.3 | -48055 | -52547 | 12.7 / 9.3 | 0.97 | 2/48 |  |
| X' | 16 | 11093 | 9209 | 1885 | 19662 | 27795 | 29.3 | 41.3 | -17690 | -14007 | 11.6 / 10.1 | 1.04 | 1/10 |  |
| GAP | 18 | 17308 | 12376 | 4932 | 71614 | 68947 | -3.9 | 25.7 | -71614 | -68947 | 15.6 / 9.7 | 1.03 | 0/13 |  |

### Session by session
| session group | window | WF mean | live mean | d mean | WF max DD | live max DD | DD cut % |
|--|--|--|--|--|--|--|--|
| Asia | L3M | 22440 | 19997 | +2443 | 19793 | 16937 | -16.9 |
| Asia | L6M | 25928 | 23341 | +2587 | 19793 | 29256 | 32.3 |
| Asia | HOLD | 17732 | 15519 | +2213 | 72674 | 89688 | 19.0 |
| Asia | PRE | 7549 | 8976 | -1426 | 69899 | 53020 | -31.8 |
| London | L3M | 5323 | 1867 | +3456 | 39203 | 45204 | 13.3 |
| London | L6M | 2941 | 2306 | +636 | 39203 | 45204 | 13.3 |
| London | HOLD | 2281 | 2280 | +0 | 76345 | 45204 | -68.9 |
| London | PRE | -1 | 27 | -27 | 85984 | 99344 | 13.4 |
| NY AM + pre | L3M | 906 | 186 | +720 | 15581 | 12222 | -27.5 |
| NY AM + pre | L6M | 1405 | 1274 | +132 | 16649 | 13645 | -22.0 |
| NY AM + pre | HOLD | 1390 | 712 | +677 | 48488 | 59046 | 17.9 |
| NY AM + pre | PRE | 1095 | 1064 | +31 | 42077 | 34346 | -22.5 |
| NY PM + close | L3M | -370 | 183 | -553 | 4249 | 5294 | 19.7 |
| NY PM + close | L6M | 1815 | 1826 | -11 | 2920 | 3965 | 26.4 |
| NY PM + close | HOLD | 795 | 405 | +391 | 28394 | 28721 | 1.1 |
| NY PM + close | PRE | 213 | 101 | +111 | 39152 | 41399 | 5.4 |

### How often each layer moved (share of refits with a non-live option, by session group)
| layer | Asia | London | NY AM+pre | NY PM+close | options |
|--|--|--|--|--|--|
| A6HALF | 59% | 80% | 77% | 57% | SM_A6_halfNP7(935d) |
| NC_K7 | 30% | 51% | 62% | 43% | NC_K7_T20_20RC(935d) |
| NC_U7 | 65% | 90% | 14% | 0% | NC_U7_T10_15F(935d), NC_U7_T20_15F(935d) |
| NC_A7 | 30% | 4% | 16% | 32% | NC_A7_T10_10F(935d) |
| NH_M7 | 0% | 76% | 54% | 16% | NH_M7_B9_X10N60(935d), NH_M7_C9_F2(935d) |
| NH_U7 | 49% | 48% | 32% | 0% | NH_U7_B7_X30N120(935d) |
| SB | 80% | 80% | 52% | 68% | SB_SP85(935d), SB_DUP120P(935d) |
| A1E | 10% | 85% | 35% | 37% | SM_A1E_XL(935d) |
| G2P7 | 37% | 41% | 42% | 65% | G2_P7A_PRE(935d) |
| FLAT42 | 15% | 57% | 42% | 43% | FLAT42P7_JN05W2(935d) |

### REFIT 2026-11-22 (training = last 26 weeks of data, 2026-05-04..2026-10-30; first-order additive; exact stage 3 below when run)
| layer | Asia | London | NY AM+pre | NY PM+close |
|--|--|--|--|--|
| A6HALF | live | SM_A6_halfNP7 | live | live |
| NC_K7 | NC_K7_T20_20RC | live | NC_K7_T20_20RC | live |
| NC_U7 | NC_U7_T10_15F | NC_U7_T20_15F | NC_U7_T10_15F | live |
| NC_A7 | NC_A7_T10_10F | live | live | live |
| NH_M7 | live | NH_M7_B9_X10N60 | NH_M7_B9_X10N60 | live |
| NH_U7 | NH_U7_B7_X30N120 | NH_U7_B7_X30N120 | NH_U7_B7_X30N120 | NH_U7_B7_X30N120 |
| SB | SB_SP85 | SB_SP85 | SB_SP85 | SB_SP85 |
| A1E | live | SM_A1E_XL | live | live |
| G2P7 | G2_P7A_PRE | G2_P7A_PRE | G2_P7A_PRE | live |
| FLAT42 | live | FLAT42P7_JN05W2 | live | live |

## 4b. Hook / exit / entry layers, rolling joint refit, base JN05W2 (no JN04 lot layers; existing 43-month exact rules)
Slots = layer x session group (Asia / London / NY AM+pre / NY PM+close); each option is an EXACT one-layer cell, deltas vs the base cell are added across layers (FIRST-ORDER additive across layers; stage 3 re-runs the winners exactly). Eligibility: an option is usable at a refit only when its months cover the training window and the OOS fortnight. Mean gate 0.85 of live, hysteresis 0. 79 refits.

| arm | L3M | L6M | HOLD | PRE | X' | GAP |
|--|--|--|--|--|--|--|
| ROLLING (real) | +33% / +5117 | -70% / +420 | -6% / +2959 | -8% / -1249 | +16% / -136 | -10% / +3009 |
| stale-fit placebo 11 d | -69% / -1553 | -99% / -2892 | -6% / +774 | -44% / -3017 | +3% / -176 | -12% / +5129 |
| stale-fit placebo 23 d | -119% / -4804 | -167% / -4323 | -29% / +1718 | -64% / -3181 | -14% / -805 | -12% / +6792 |
| stale-fit placebo 37 d | -113% / -2525 | -161% / -3279 | -26% / +2436 | -38% / -2860 | +3% / -827 | -12% / +4619 |
| random options seed 1 | +42% / +5250 | -76% / -1536 | -21% / +1956 | -8% / -689 | +7% / -141 | -12% / +2795 |
| random options seed 2 | +38% / +6138 | -69% / -287 | -21% / +2437 | -11% / -670 | +14% / +964 | -12% / +2395 |
| random options seed 3 | +40% / +6216 | -36% / -144 | -6% / +2980 | -14% / -1329 | +14% / +801 | -10% / +2899 |
| random options seed 4 | +48% / +6349 | -36% / +131 | -21% / +2343 | -9% / -639 | +16% / +756 | -10% / +2875 |
| random options seed 5 | +42% / +2516 | -41% / -975 | -21% / +2077 | -10% / -1318 | +14% / +1044 | -12% / +2699 |
| BEST_SINGLE_FIT (pick once, first refit) | +49% / +2454 | +49% / +1551 | +22% / +1714 | -28% / -1122 | +3% / -167 | +10% / +3336 |
| HINDSIGHT whole-sample pick (IN-SAMPLE, full-coverage cells only) | +31% / +2590 | +21% / +675 | +6% / +849 | +8% / -34 | -2% / -567 | +1% / +383 |

Cells = max-DD cut % vs the frozen base / d mean $/wk on the same OOS days (+ = shallower). Period-beat 47%, mean slots changed per refit 5.7.

### Realised rolling walk-forward vs frozen base, recent windows first
| window | weeks | WF mean $/wk | live mean | d mean | WF max DD | live max DD | DD cut % | equal-mean cut % | WF worst wk | live worst wk | full stops/wk WF / live | 5 best live wks kept | live winners turned losing | DD cut % no W44 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| L1M | 2 | 25685 | 19398 | 6287 | 0 | 0 |  |  | 11183 | 14801 | 15.0 / 14.0 | 1.32 | 0/2 |  |
| L3M | 11 | 27351 | 22233 | 5117 | 20381 | 30533 | 33.2 | 45.7 | -12914 | -26026 | 10.0 / 10.4 | 1.29 | 0/9 |  |
| L6M | 24 | 29167 | 28747 | 420 | 51974 | 30533 | -70.2 | -67.8 | -51974 | -26026 | 18.5 / 10.7 | 0.85 | 1/19 |  |
| HOLD | 50 | 21875 | 18916 | 2959 | 66692 | 63185 | -5.5 | 8.7 | -56130 | -55145 | 19.2 / 10.6 | 0.93 | 2/37 |  |
| PRE | 75 | 8919 | 10168 | -1249 | 81980 | 76186 | -7.6 | -22.7 | -61488 | -52547 | 11.6 / 9.3 | 0.87 | 2/48 |  |
| X' | 16 | 9072 | 9209 | -136 | 23360 | 27795 | 16.0 | 14.7 | -23360 | -14007 | 9.9 / 10.1 | 0.96 | 1/10 |  |
| GAP | 18 | 15386 | 12376 | 3009 | 75717 | 68947 | -9.8 | 11.7 | -75717 | -68947 | 13.1 / 9.7 | 1.00 | 1/13 |  |

### Session by session
| session group | window | WF mean | live mean | d mean | WF max DD | live max DD | DD cut % |
|--|--|--|--|--|--|--|--|
| Asia | L3M | 23084 | 19997 | +3087 | 17252 | 16937 | -1.9 |
| Asia | L6M | 21687 | 23341 | -1654 | 39198 | 29256 | -34.0 |
| Asia | HOLD | 15870 | 15519 | +350 | 78418 | 89688 | 12.6 |
| Asia | PRE | 8269 | 8976 | -706 | 57770 | 53020 | -9.0 |
| London | L3M | 3519 | 1867 | +1652 | 44846 | 45204 | 0.8 |
| London | L6M | 4757 | 2306 | +2451 | 44846 | 45204 | 0.8 |
| London | HOLD | 4069 | 2280 | +1789 | 79709 | 45204 | -76.3 |
| London | PRE | -889 | 27 | -916 | 94555 | 99344 | 4.8 |
| NY AM + pre | L3M | 322 | 186 | +136 | 20864 | 12222 | -70.7 |
| NY AM + pre | L6M | 1477 | 1274 | +203 | 24255 | 13645 | -77.8 |
| NY AM + pre | HOLD | 986 | 712 | +274 | 44494 | 59046 | 24.6 |
| NY AM + pre | PRE | 1287 | 1064 | +222 | 40360 | 34346 | -17.5 |
| NY PM + close | L3M | 425 | 183 | +242 | 2024 | 5294 | 61.8 |
| NY PM + close | L6M | 1246 | 1826 | -580 | 2710 | 3965 | 31.7 |
| NY PM + close | HOLD | 950 | 405 | +545 | 20259 | 28721 | 29.5 |
| NY PM + close | PRE | 252 | 101 | +150 | 39182 | 41399 | 5.4 |

### How often each layer moved (share of refits with a non-live option, by session group)
| layer | Asia | London | NY AM+pre | NY PM+close | options |
|--|--|--|--|--|--|
| A6HALF |  |  |  |  | SM_A6_halfNP7(935d) |
| NC_K7 |  |  |  |  | NC_K7_T20_20RC(935d) |
| NC_U7 |  |  |  |  | NC_U7_T10_15F(935d), NC_U7_T20_15F(935d) |
| NC_A7 |  |  |  |  | NC_A7_T10_10F(935d) |
| NH_M7 |  |  |  |  | NH_M7_B9_X10N60(935d), NH_M7_C9_F2(935d) |
| NH_U7 |  |  |  |  | NH_U7_B7_X30N120(935d) |
| SB |  |  |  |  | SB_SP85(935d), SB_DUP120P(935d) |
| A1E |  |  |  |  | SM_A1E_XL(935d) |
| G2P7 |  |  |  |  | G2_P7A_PRE(935d) |
| FLAT42 |  |  |  |  | FLAT42P7_JN05W2(935d) |

### REFIT 2026-11-22 (training = last 26 weeks of data, 2026-05-04..2026-10-30; first-order additive; exact stage 3 below when run)
| layer | Asia | London | NY AM+pre | NY PM+close |
|--|--|--|--|--|
| A6HALF | live | live | live | live |
| NC_K7 | live | live | live | live |
| NC_U7 | live | live | live | live |
| NC_A7 | live | live | live | live |
| NH_M7 | live | live | live | live |
| NH_U7 | live | live | live | live |
| SB | live | live | live | live |
| A1E | live | live | live | live |
| G2P7 | live | live | live | live |
| FLAT42 | live | live | live | live |

## 5. Stage 2b - EXACT one-layer variants on JN05W2J (JN04 layers on), vs JN05W2J. Cell = max-DD cut % / d mean $/wk / d full stops per wk / 5 best base weeks kept / base winners turned losing / (cut % with W44 removed when W44 is in the window). Window shown only when all its months are DONE.

**K7 flat cut d (live 45)**
| cell | months | L3M | L6M | HOLD | PRE | X' | GAP | rule 2a label |
|--|--|--|--|--|--|--|--|--|
| K7F40 | 3 | +15% / +515 / -0.2 / 1.00 / 0 / -13% |  |  |  |  |  |  |
| K7F50 | 3 | +15% / +1149 / +0.3 / 1.08 / 0 / -14% |  |  |  |  |  |  |

**C22 closes n (live 22)**
| cell | months | L3M | L6M | HOLD | PRE | X' | GAP | rule 2a label |
|--|--|--|--|--|--|--|--|--|
| C22N18 | 3 | -46% / -132 / -0.4 / 1.05 / 0 / -95% |  |  |  |  |  |  |
| C22N26 | 3 | -42% / -1432 / +0.5 / 1.02 / 0 / -33% |  |  |  |  |  |  |

**C22 day P&L R (live -2)**
| cell | months | L3M | L6M | HOLD | PRE | X' | GAP | rule 2a label |
|--|--|--|--|--|--|--|--|--|
| C22R15 | 3 | +11% / +538 / -0.1 / 1.03 / 0 / -5% |  |  |  |  |  |  |
| C22R25 | 3 | +0% / -28 / +0.0 / 1.01 / 0 / -14% |  |  |  |  |  |  |

**WL_E1 loss_same_ge (live 2)**
| cell | months | L3M | L6M | HOLD | PRE | X' | GAP | rule 2a label |
|--|--|--|--|--|--|--|--|--|
| E1G1 | 3 | -35% / -2878 / +0.0 / 0.83 / 0 / -81% |  |  |  |  |  |  |
| E1G3 | 3 | -6% / -318 / -0.2 / 0.98 / 0 / +4% |  |  |  |  |  |  |

**F3 fresh cut arm (live 45)**
| cell | months | L3M | L6M | HOLD | PRE | X' | GAP | rule 2a label |
|--|--|--|--|--|--|--|--|--|
| F3F40 | 3 | -27% / -966 / -0.2 / 0.97 / 0 / -69% |  |  |  |  |  |  |
| F3F50 | 3 | -15% / -219 / +0.4 / 0.99 / 0 / -16% |  |  |  |  |  |  |

**F3 rechase cut arm (live 30)**
| cell | months | L3M | L6M | HOLD | PRE | X' | GAP | rule 2a label |
|--|--|--|--|--|--|--|--|--|
| F3R25 | 3 | +18% / -3784 / -0.1 / 0.73 / 0 / -10% |  |  |  |  |  |  |
| F3R35 | 2 |  |  |  |  |  |  |  |

**P7 day loss cap (live 8400)**
| cell | months | L3M | L6M | HOLD | PRE | X' | GAP | rule 2a label |
|--|--|--|--|--|--|--|--|--|
| DC6000 | 1 |  |  |  |  |  |  |  |

**P7 session table (live 7,4,0,4,0,0)**
| cell | months | L3M | L6M | HOLD | PRE | X' | GAP | rule 2a label |
|--|--|--|--|--|--|--|--|--|
| T5404 | 3 | +22% / -1584 / +0.0 / 0.87 / 0 / +1% |  |  |  |  |  |  |
| T7304 | 3 | +0% / +89 / +0.0 / 1.01 / 0 / +0% |  |  |  |  |  |  |
| T7403 | 3 | +0% / +55 / +0.0 / 1.00 / 0 / +0% |  |  |  |  |  |  |

**ATR skip P7 (live none in the engine reference)**
| cell | months | L3M | L6M | HOLD | PRE | X' | GAP | rule 2a label |
|--|--|--|--|--|--|--|--|--|
| ATR14 | 3 | -16% / -615 / -0.1 / 0.96 / 0 / +7% |  |  |  |  |  |  |
| ATR16 | 1 |  |  |  |  |  |  |  |
| ATR18 | 1 |  |  |  |  |  |  |  |

**post-stop blackout P7 same side (live none in the engine reference)**
| cell | months | L3M | L6M | HOLD | PRE | X' | GAP | rule 2a label |
|--|--|--|--|--|--|--|--|--|
| BO15 | 1 |  |  |  |  |  |  |  |

## 9. Candidate v2.10 (PROVISIONAL, 2026-11-14 20:15Z; exact evidence is L3M only for the one-layer variants, so nothing below is a lead yet)
- Frozen layers (no change): the JN04 lot layers LOT / SIGQ / REG / STACK, F3 context cut, WL_E1, C22, BR3S, K7 flat 45, P7 cap 14,700 live (engine 8,400 base lots, x1.75) and the P7 table 7,4,0,4,0,0. Reason: the rolling refit of the lot-level layers lost to the frozen setting and to random settings (section 3); the policy file therefore does not depend on any first-order lot layer.
- Open leads waiting for L6M/HOLD (L3M exact, W44 inside): K7 flat 40 or 50 (+15% DD cut, +$515/+$1,149 per wk), P7 table 5,4,0,4,0,0 (+22%, -$1,584 per wk), C22 pnl_r -1.5 (+11%, +$538). Rejected on L3M: C22 n 18/26, E1 ge 1, F3 fresh 40/50, F3 rechase 25 (mean -$3.8k).
- Policy-file lines that exist today (D7 syntax): `loss K7 * pct<=-0.75 cut` (flat 45 of a 60-pt stop; a flat 40 would be pct<=-0.667, 50 pct<=-0.833). Everything else (C22, E1, F3, BR3S, table, cap) is a panel/code field, not a policy line.
- Code-change list for v2.0 is the JV/LR/PR/RA specs as scored on their own pages; this page adds none until a composite lands.
