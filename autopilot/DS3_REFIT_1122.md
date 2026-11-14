# DS3_REFIT_1122 - the 2026-11-22 JOINT REFIT, walked forward through 43 months (PRIORITY 12, W-RF)

VERDICT: pending - plan and frozen references only (stage 1 running).

Generated 2026-11-14 16:42 UTC (epoch 1794674532). Exact engine for every verdict dollar; first-order composition only to rank (always labelled). Shadow only, no PASS claims. Prereg autopilot/REFIT1122_PREREG.md (sha in DECISIONS.md). Code outputs/code/th_refit1122/; bulk /mnt/l2/l2vast/_refit1122/.

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
| ATR skip | skip entries at ATR >= 1.6x reference (panel setting named in the order) | skip thresholds in the REG / skip pools; London range-used-up cells (W-LR) |
| blackout | P7 post-stop 30-minute blackout (panel setting named in the order) | session_blocks / ntz cells; W-PR re-entry cells |
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
