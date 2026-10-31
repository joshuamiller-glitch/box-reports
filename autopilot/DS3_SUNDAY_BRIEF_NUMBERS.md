# DS3_SUNDAY_BRIEF_NUMBERS - one numbers table for Sunday brief v6 (BP-1, drafted Sat 2026-10-31; no new research, every cell copied from the cited report)

Units unless stated: $k per week, live lots (K6 2, P6 7, U6 4, H6 4 Asia / 2 NY-AM, M6 2, A6 1), integer half-up min-1 ER lots, 70/30 integer split, add slip +0.25, N basis, windows capped 20260206 (L3M 14 wk, L6M 28, HOLD 32, PRE 75, X' 44). Cell = delta vs "the stack as it is" (market entries, no rules, join 2.45) with MDE in (); `*` beyond MDE. Columns recent-first: L3M / L6M / HOLD / PRE / X'. Post-hoc, nothing is a PASS. Tags: [G1]=DS3_GOVERNOR_FIDELITY, [G2]=DS3_LOCK_SWEEP, [R2]=DS3_SUNDAY_RISK_2, [D1]=DS3_SUNDAY_DECISION, [P1]=DS3_PERSISTENCE_SUNDAY, [RS]=DS3_REGIME_STRESS, [D7]=DS3_D7_FILTERS, [NP]=DS3_NYPM_END_SKIP, [AB]=DS3_ALT_BAR_IDENTITY, [U]=user reply 14:30Z, [B4]=brief v4.

## 1. D6-faithful composite: lead vs as-is under three conventions (engine = [G1] V4: running max over ALL book signals, session-lot BookR, A6 = engine PB (A6 market), Native 1.28)

| convention | L3M | L6M | HOLD | PRE | X' | source |
|---|---|---|---|---|---|---|
| C1 no combined lock (per-book locks only) vs as-is, no combined lock | +24.3* (22.7) | +22.3* (17.6) | +18.9* (17.3) | +7.0 (13.1) | +13.4 (14.7) | [G1] V4_noc; [G2] row "off"; [R2] sec 2 "OFF" |
| C2 12R combined lock on composite vs UNLOCKED as-is (= the live-code reading if as-is has no combined lock) | +17.9 (29.2) | +16.5 (21.0) | +15.3 (21.9) | +0.3 (14.8) | +2.3 (14.0) | [G1] V4_comb12; [G2] 12R col 1; [R2] sec 2 12R |
| C3 like-for-like: 12R lock on BOTH composite and as-is | +25.5 [+10.4,+42.4] | +27.8 [+16.4,+41.6] | +23.4 [+14.6,+38.6] | +8.1 [+0.7,+17.4] | +8.0 [-2.3,+18.7] | [G2] col "C(s)-A(s)"; [R2] sec 1 (CI = 4-wk block bootstrap, not MDE) |
| effect of the combined lock alone on composite (C2 minus C1) | -6.5 (11.6) | -5.8 (7.1) | -3.5 (11.7) | -6.7 (11.7) | -11.1 (11.2) | [G1] sweep F=12; [G2] |
| memo: same C1 with A6 = PB7 Asia 1 lot (V0 convention), Native | +25.5 (22.5) | +21.8 (17.6) | +18.7 (17.5) | +6.1~ (13.1) | +11.8~ (14.2) | [D1] (d) |
| memo: same, join 2.45 / A/B parity mix | +23.1 / +23.8 | +19.5 / +20.4 | +16.4~ / +17.4 | +3.6~ / +4.8~ | +10.2~ / +11.0~ | [D1] (d) |
| memo: SS-2 integer (A6 library PB all sessions, V0) | +25.0 (22.6) | +22.8 (17.6) | +19.3 (17.3) | +7.4 (13.0) | +12.9 (15.0) | [G1] V0; [P1] as-coded |
| memo: SS-2 fractional lots (the brief v4 headline) | +19.4 (24.1) | +18.5 (17.4) | +16.2 (16.8) | +4.7 (13.4) | +12.5 (14.7) | [B4] A; [D1] (0) |
| K6 at market, others 70/30 (answer 3), C2 / C1-PB7 | +16.0 / +22.7(P1,PB lib) | +16.0 / +21.1(D1 PB7) / +22.1(P1) | +15.1 / +18.3 / +18.9 | +0.9 / +5.4 / +6.8 | +1.4 / +11.9 / +13.0 | [G1] V5; [D1] (b) derived 21.8-0.7; [P1] |
| sizer on P6+K6 only (answer a), C1-PB7 | +25.0 (23.0) | +22.3 (17.3) | +18.9 (17.1) | +5.1~ (11.9) | +11.5~ (13.6) | [D1] (a); vs all six -0.5/+0.5/+0.2/-1.0/-0.4 |
| NY-PM end skip 14:40-15:00 added to composite, live lots | +0.1 (1.1) | +0.0 (0.8) | -0.0 (0.7) | -0.2 (0.3) | +0.2 (0.7) | [D1] (c); [NP] gives -0.14 (0.94) L6M, -0.15 HOLD, -0.27 PRE, +0.28 X' (A6 = library PB) |
| Sunday CANDIDATE (P6+K6 sizer, K6 mkt, NY-PM skip), C1-PB7 | +22.8 (22.6) | +21.6 (17.0) | +18.5 (16.8) | +4.3~ (11.8) | +12.0~ (13.1) | [D1]; no 12R version exists (K6 mkt at 12R only: row above) |

## 2. Persistence-shrunk and regime-faded (both WITHOUT the combined lock; neither re-run at 12R)

| number | L3M | L6M | HOLD | PRE | X' | source / convention |
|---|---|---|---|---|---|---|
| as-coded (reference, C1 V0 PB-lib) | +25.0 (22.6) | +22.8 (17.6) | +19.3 (17.3) | +7.4 (13.0) | +12.9 (15.0) | [P1] |
| **persistence-shrunk composite** (split/PE/zone/cut 0, ER 0.03, Native 0.81) | +2.1 (0.8) | +2.2 (0.6) | +2.2 (0.5) | +2.3 (1.9) | +1.8 (0.2) | [P1] honest number; 99% is the Native stop |
| shrunk + ER sizer at 100% | +9.7 (16.5) | +10.4 (9.6) | +9.6 (9.6) | +0.9 (10.7) | +5.6 (13.9) | [P1] |
| every piece at 50% (benchmark) | +13.5 (13.6) | +13.9 (9.8) | +11.8 (9.4) | +2.7 (8.2) | +8.0 (9.4) | [P1] |
| **regime-faded**: composite delta now vs 2023-24 state mix | - | +20.4 [+8.6,+32.1] now -> +9.1 [+1.9,+16.5] in 2023-24 mix | +17.4 | T1 (2023-24-like) +6.1~ | actual 2023-24 wks +9.5~ | [RS] D1 (d), A6 = PB7, A/B parity mix, V0 |
| regime-faded stack LEVEL | - | +42.2 -> +12.4 [+3.5,+20.9] | +39.3 | - | - | [RS]; as-is level now +21.7, T1 +3.3 |

Six-piece persistence verdict [P1]: none of the six is a persisting rule (6-month t 0.3-2.6); only the Native stop (t 5.5/6.1) and it is a measured cost saving (live z = 1.6, n 21 vs 8).

## 3. Risk lines (RK-2; weekly series, $k/wk; D6 vs as-is with the SAME lock; maxDD of weekly cumulative; "wk" = worst week) [R2] sec 1

| lock | row | L3M mean/maxDD/wk | L6M | HOLD | PRE | X' | ALL(149) |
|---|---|---|---|---|---|---|---|
| 12R | D6-faithful | 31.7/28/-28 | 40.5/28/-28 | 39.1/28/-28 | 18.0/274/-44 | -1.3/214/-44 | 17.1/274/-44 (worst-20 -730) |
| 12R | as-is same lock | 6.2/108/-30 | 12.7/116/-30 | 15.6/116/-30 | 9.9/268/-30 | -9.3/526/-30 | 5.6/526/-30 (-591) |
| off | D6-faithful | 38.1/21/-21 | 46.3/21/-21 | 42.6/113/-75 | 24.7/263/-121 | 9.8/126/-72 | 24.5/263/-121 (-1141) |
| off | as-is unlocked | 13.8/92/-92 | 24.0/92/-92 | 23.7/144/-92 | 17.7/210/-101 | -3.6/317/-71 | 13.0/317/-101 (-1218) |

D6 maxDD CI excludes 0 (lighter) in L3M/L6M/HOLD at 12R; PRE not distinguishable (maxDD +6 [-121,+155], worst-20 -71 [-200,+62]); over ALL the 12R worst-20 is 139k WORSE for D6 [-250,-27]. Tail benefit in L3M/L6M rests on 2026-01-19 (-91.8k as-is). Equal-worst-20 scaling (c 0.81 at 12R): +19.4 / +20.1 / +16.0 / +4.7~ / +8.2~ (L3M..X'). Lock fires 4/8/10/35/28 weeks (73/149), 57 of 73 while K6 SizeMult is 0.5 (threshold $14.4k, not $28.8k) [G2].

## 4. Per-book status and live-lot numbers (status = proposal from the reports; no report assigns ON/SHADOW/OFF per book; lead decides)

Per-book delta = Sunday CANDIDATE vs as-is, L6M / HOLD / PRE / X', $k/wk [D1 sec 6], A6 = PB7. Sizer per-book = effect of switching the sizer off on that book, L6M [D1 sec 3].

| book | live lots / sessions | candidate delta L6M/HOLD/PRE/X' | split | ER sizer | other pieces | D7 g12 + NY-PM skip |
|---|---|---|---|---|---|---|
| P6 (PE) | 7 Asia/Lon/NY-AM | +15.9/+13.7/+6.0/+7.5 | ON (5/2) | SHADOW, lean keep (off = -11.5) | PE 45-s SHADOW; zone skip SHADOW | all OFF; skip no-op live |
| K6 (KB) | 2 Asia/Lon/NY-AM/NY-PM | +1.7/+1.5/-0.9/+1.4 | ON (1/1; K6 mkt costs 0.7 L6M, inside MDE) | SHADOW, weak keep (off = -2.4) | zone skip SHADOW | OFF; skip -0.24 L6M live [NP] |
| H6 (HM) | 4 Asia / 2 NY-AM | +4.0/+3.4/-0.5/+0.8 | ON (3/1; 1/1) | OFF (off = -0.1) | cut SHADOW (~0) | OFF |
| U6 (SM) | 4 Asia/Lon | -0.1/-0.3/-0.2/+1.5 | ON (3/1) | OFF (off = +0.9) | - | OFF |
| M6 (MV) | 2 Lon/NY-AM | +0.3/+0.2/-0.0/+0.4 | ON (1/1) | OFF (off = +0.6) | - | OFF |
| A6 (PB7) | 1 Asia, market | -0.1/+0.0/-0.1/+0.3 | n/a (1 lot) | inconclusive (off = -0.9, MDE 1.4) | - | OFF |
| O6 | 1 opening drive | in no number | - | - | - | - |
Cross-book SHADOW: Native stop (+1.5 live, [B4]), NY-PM skip (ships OFF in D6, run in register [NP]), alt-bar cells L02766/L01501/L01610/L01490/L02783 (Shadow only, all fail G6; per-contract L6M M pts +5.47/+5.34/+0.76/+5.78/+9.59, 4.22/3.43/2.54/3.51/3.25 trades/wk [AB]). D7 group 12 (a)-(d): all OFF, stack L6M -6.8/-0.1/-0.7/-6.2, 0 of 19 lines ON [D7].

## 5. Inconsistencies between reports (flagged, NOT resolved)

1. Combined week lock: [G1][G2][R2] assume 12R (from the HALT-RESUME text); [U] fixes the unit (K6 BookR) but not the multiple. [D1][P1][RS][D7] contain NO combined lock. Same piece, +6k L6M apart (C1 vs C2). No report has the lock with A6 = PB7, or with persistence shrinkage, or on the Sunday CANDIDATE.
2. Which as-is/lead is "the" lead: C1 +22.3, C2 +16.5, C3 +27.8 (L6M). C3 flatters (the lock hurts as-is 2x). Brief v4 headline +18.5 is none of them (fractional lots, no combined lock).
3. A6 stack: [G1][G2][R2][P1][NP] use library PB (all sessions, "A6 market"); [D1][RS] use PB7 Asia 1 lot ([U] correction); [D7] uses library PB Asia only. Effect -1.0 L6M on the delta, and the as-is baseline itself differs (L6M 24.0 [G1][R2] vs 21.7 [D1] vs 23.0 [D7]). [NP] therefore lets A6 trade NY-PM (-0.18 L6M) which PB7 Asia-only would not; [D1] calls the skip a K6-only no-op.
4. Governor definition: [G1] V4 (running max over ALL signals, BookR on session planned lot, H6 NY-AM 2 not 4) vs [D1][P1][D7][RS] V0 (max over TAKEN signals, LN = max session lot). V4 costs -0.5 L6M (noc). [U] says BASE planned lots: ambiguous between the two.
5. Stop: [G1][G2][R2][P1][D7] Native 1.28 for everyone; [U] says the live A/B is odd day Native, even day join 2.45. Join/mix lowers the delta 1.4-2.3 L6M [D1]; [RS] uses the mix, [D1] shows all three. Native was measured on ST/HM only [B4].
6. Lot units: [B4] says live = research/2.35 (assumption, 1.6x-6x off from the engine); [G1] says engine $ = real/1.75. [B4] per-book split evidence is at research lots (K6 -3.0, U6 +3.0, H6 +0.8, P6 +0.8) while live-lot K6 is +1.7 L6M [D1] and K6 add +0.4..+0.7: sign flips with lots.
7. Integer vs fractional ER lots: +22.8 vs +18.5 (half-up raises the average lot; [D1] says more lots, not more edge). [U] says score integer as headline; [B4] kept fractional.
8. NY-PM skip: [NP] research-lot alone on old stack +4.7 L6M (MDE 4.1; placed in [B4] C as SHADOW) vs live-lot composite -0.14 / 0.0 [NP][D1]; [NP] units are $/wk (not $k) and in-text numbers differ by A6 as in 3. Both say ship OFF, but [B4] counted it as a candidate.
9. Sizer books list: [D1] all-six vs P6+K6 only differ by <=1.0 (inside MDE); but [B4] says ER gain exists only with running-max locks (planned-lot locks +2.7 six-book, composite +11.2 vs +22.8). [P1] shrinks ER to 0.03 (rounds to no lot change) while [D1] keeps it as the piece that "does the work" (+13.5 L6M).
10. Persistence-walk-forward: [B4] -9.6k/wk research at full size (RE-1/2) vs [P1] -5.5k/wk at shrunk size (RE-2). Different sizes, not contradictory, but the brief should cite both.
11. Stack-delta windows with `~`: [D1] PRE/X' inside MDE in every composite row; [G1]/[R2] C2 PRE/X' ~0; persistence-shrunk marks PRE/X' as clearing a tiny MDE (0.2-1.9) because the Native stop is steady: MDE is not comparable across rows.
12. Unit mix: $k/wk [G1][G2][R2][D1][P1][RS][D7]; $/wk [NP]; pts per planned lot [P1][D7][NP]; pts/$ per contract [AB]; CI (bootstrap) in [R2] C3 vs MDE (2.8 SE) elsewhere.
13. Unknowns still open: combined-lock multiple; SizeMult reset value before K6's first signal (1.0 assumed); gross vs net P&L in the entry test; stop pts (60 fixed vs signal stop); O6 not in any number; no report has the composite with ER sizer on P6+K6 only AND the combined lock.
