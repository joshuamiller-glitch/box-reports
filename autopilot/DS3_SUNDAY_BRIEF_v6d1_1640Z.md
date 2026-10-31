# DS3_SUNDAY_BRIEF v6 draft 1 (stamp 2026-10-31T16:30Z = file mtime). Deadline Sun 2026-11-01 12:00 ET = 17:00Z; D6 start Sun 18:00 ET.
Nothing here is a PASS. Post-hoc, capped 2026-02-06, UNTOUCHED never read. $k/week, delta vs "the stack as it is", MDE in (), `*` beyond MDE. Previous version: DS3_SUNDAY_BRIEF_v5_1628Z.md. Tags: K6=KB, P6=PE, U6=SM, H6=HM, M6=MV, A6=PB7 (user, 14:30Z), O6 in no number. Live lots K6 2, P6 7, U6 4, H6 4 Asia / 2 NY-AM, M6 2, A6 1.

## 1. FIRST SCREEN: what to do (lead proposal; no report assigns ON/SHADOW/OFF; you decide)
| | Rule | Numbers (DS3_ONE_CONVENTION unless named) |
|---|---|---|
| **ON in D6** | 70/30 split, dip 3 pt, all books (K6 keeps it, your answer; P6 splits, D6 ignores THP entry lines) | split leave-one-out L6M +4.1 [+0.5,+8.0], HOLD +3.9, 2023-24-like state -0.4, all inside MDE (DS3_REGIME_STRESS); K6 add +0.5 (inside MDE) |
| **ON as coded** | D6 locks: BookR = planned lots x running-max SizeMult | no change to code; multiple of the combined week lock is the open item (E1) |
| **SHADOW** | ER(20) 5-min sizer (P6 lean keep, K6 weak keep; U6 H6 M6 drop), PE 45-s confirmation, 8-line zone skip, Asia-stopped cut50, NY-PM end skip 14:40-15:00 (ships OFF in D6; run in the register), alt-bar cells L02766 L01501 L01610 L01490 L02783 | pieces in section 2; per book in section 4 |
| **A/B live** | Stop: odd day-of-month = Native, even = JoinThenMarket; first even day Mon 11-02 = B | FORWARD_STOP_AB.md |
| **OFF** | D7 group 12 (a) first-60-min skip, (b) post-loser skip, (c) KB book-lean skip, (d) ES-lead sizer; sizers on U6 H6 M6; everything in section 6 | DS3_D7_FILTERS: 0 of 19 rule-by-book lines ON; DS3_D7F_RULE_A: (a) doubles L3M/L6M maxDD (21.4 to 44.0) |

**The composite on ONE convention** (DS3_ONE_CONVENTION: A6=PB7, live lots, integer half-up min-1 ER lots, SizeMult = running max over TAKEN signals, stop by day-of-month parity, slip +0.25, K6 70/30). Recent-first:
| comparison | L3M (14 wk) | L6M (28) | HOLD (32) | PRE (75) | X' (44) |
|---|---|---|---|---|---|
| C1 no combined lock on either | +22.3 (22.3) | +19.4 (17.5)* | +16.7 (17.3) | +4.5 (13.2) | +11.4 (14.0) |
| **C2 12R lock on composite vs UNLOCKED as-is (conservative)** | +16.9 (27.4) | +10.6 (26.5) | +9.5 (26.7) | -3.5 (15.3) | +4.5 (14.1) |
| C2 20R / 30R, L6M | | +13.1 (21.9) / +16.6 (18.9) | +10.1 / +14.4 | -2.7 / -2.5 | +6.7 / +10.1 |
| C3 12R on BOTH (flatters: lock hurts as-is 11.4 vs composite 8.9) | +25.1 (21.2)* | +21.9 (27.3) | +17.7 (27.2) | +5.4 (11.9) | +8.3 (13.8) |
Which applies: C2 if today's as-is runs without the combined lock (read this); C3 if it runs the same lock; C1 if D6 has none. K6 at market (your request): C1 L6M +18.9, C2-12R +10.3 (Table D), inside MDE of the split line. Stress slip +0.45 lowers every cell 0.3-0.5 (Table C). Levels L6M: composite 41.1 no lock / 32.3 at 12R; as-is 21.7.

## 2. HAZARDS (read before the numbers)
1. **Persistence.** Positive in the last 3 and 6 months -> positive next quarter 41% (CI 36-47) vs 50% coin (DS3_PERSISTENCE, RE-1). SIXTY's 0.60 selection 51% (CI 45-57): not above a coin by the base-rate reading (SIXTY_BRIEF_SECTION.md; MORNING 16:13Z says base 50%, the section says family-mix 31%: the two disagree). No Sunday piece persists (6-month t 0.3-2.6); only the Native stop (t 5.5/6.1). **Shrunk-size composite (the honest number): +2.2 (0.6) L6M, +2.1 L3M, +2.2 HOLD, +2.3 PRE, +1.8 X'; 99% of it is the Native stop** (DS3_PERSISTENCE_SUNDAY; no combined lock). Regime-faded: delta +20.4 now vs +9.1 [+1.9,+16.5] in a 2023-24 mix; level 42.2 -> 12.4 (DS3_REGIME_STRESS).
2. **Combined week lock, multiple unknown.** It costs the composite 5-9k/wk at 12R (L6M -8.9) and 3-9k L6M from 30R to 12R; fires 8/28 L6M weeks (71/149 overall); **PRE is negative against an unlocked as-is at every multiple (-2.5 to -3.5)**; 8R is ruinous (L6M +0.6) (ONE_CONVENTION Tables A2, B, F). DS3_LOCK_SWEEP/GOVERNOR_FIDELITY (older convention) show the same lock at -5.8k and 12R C2 +16.5; the 6 vs 9 difference is A6=PB7 and parity (the bridge in ONE_CONVENTION). Not run: the lock with persistence shrinkage or on the Sunday CANDIDATE.
3. **Lock-widening is about 80% of any size-up.** Uniform x1.5 on every signal +18.6k L6M, only 3.5k if locks are not widened (DS3_NO_TRADE_C_D). The ER sizer's gain needs running-max locks; with planned-lot locks it is +2.7 six-book / -2.4 PRE (DS3_ER_SIZER_ROBUSTNESS).
4. **Post-hoc.** Five of six composite pieces were chosen after L6M/HOLD; the full-size monthly walk-forward on the D6 engine +59.4k/wk (MDE 44.2) carries 3.6x the SD and is -18.6k vs plain leverage (DS3_RECENT_EDGE_6); the research-engine walk-forward was -9.6k/wk (RE-1/2; -5.5k shrunk, DS3_PERSISTENCE_SUNDAY): different engines.
5. **Tape defect.** Replayed-hour duplicate on 11 label days (weekend-start months); lock engine, 1-s/1-min/L2 tables clean, **composite unaffected**; PE 45-s differs on 115 of 89,464 events, none in NY. Alt-bar cells (store built from the tape) are the exposed ones; the weekly ext tape 2026-10 and the 2026-11 monthly file carry it: de-duplicate first (DS3_TAPE_DEDUP, DS3_ALT_BAR_IDENTITY).
6. **Stop A/B n=21.** Join 2.45 pts/stop (n=21) vs Native 1.28 (n=8): +1.17, z 1.6, p 0.055; the three Native estimates disagree (1.28 / 2.20); ~200 stops per arm needed, 6-8 weeks with all books (FORWARD_STOP_AB). Join fill rate 0.38 live vs 0.78 replay.
7. **The ER sizer is the only piece clearing its MDE** (+14.0 (13.2) L6M on P6+K6; DS3_SUNDAY_DECISION), and only with running-max locks; whole sizer in-stack +12.5 (23.5) (ER-1). Shuffled ER never reaches it (0/200). Other pieces are inside MDE.
8. **Re-entry and slow reads.** Share of gain from lock re-entry: split 47-55%, PE 58%, Asia cut 71%, zone skip 85%, KB sizer 88% (v5, DS3_SUNDAY_STACK_2); reads need ~60 weeks (ER sizer) to ~230 (HM FVG); at 13 weeks only harm/futility and execution show.

## 3. RISK (ONE_CONVENTION Table E; $k/wk mean / maxDD / worst week; no significance claim)
| lock off | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| composite | 34.4/21/-21 | 41.1/23/-23 | 38.6/97/-68 | 23.1/241/-120 | 8.0/121/-66 |
| as-is | 12.2/88/-88 | 21.7/88/-88 | 21.9/144/-88 | 18.6/162/-96 | -3.4/317/-71 |
Recent windows are smoother for the composite and the tail benefit rests on one week (2026-01-19, as-is -91.8k). **PRE is not lighter** (maxDD 241 vs 162; worst-20 -875 vs -811). The 12R lock does not lighten the composite in recent windows (L6M maxDD 27) and only caps PRE's worst week (-46 vs -120). Over all 149 weeks the 12R worst-20 is 139k worse for D6 (DS3_SUNDAY_RISK_2).

## 4. PER BOOK (PROPOSAL ONLY, from DS3_SUNDAY_BRIEF_NUMBERS section 4; deltas = Sunday CANDIDATE (sizer P6+K6, K6 at market, NY-PM skip) vs as-is, live lots, C1-PB7 convention of DS3_SUNDAY_DECISION, no parity; L3M not split by book)
| book | split | ER sizer (off = ) | L6M / HOLD / PRE / X' | other |
|---|---|---|---|---|
| P6 7 lots | ON | SHADOW, lean keep (-11.5) | +15.9/+13.7/+6.0/+7.5 | PE 45-s, zone skip SHADOW |
| K6 2 | ON (your answer) | SHADOW, weak keep (-2.4) | +1.7/+1.5/-0.9/+1.4 | zone skip SHADOW; NY-PM skip -0.24 |
| H6 4/2 | ON | OFF (-0.1) | +4.0/+3.4/-0.5/+0.8 | cut SHADOW (~0) |
| U6 4 | ON | OFF (+0.9) | -0.1/-0.3/-0.2/+1.5 | |
| M6 2 | ON | OFF (+0.6) | +0.3/+0.2/-0.0/+0.4 | |
| A6 1 (PB7) | n/a | inconclusive (-0.9, MDE 1.4) | -0.1/+0.0/-0.1/+0.3 | |
Cross-book SHADOW: NY-PM skip with the composite 0.0 (0.8) L6M, ships OFF (DS3_NYPM_END_SKIP; its research-lot +4.7 alone is another engine). Two reports disagree on A6 in the as-is base (library PB vs PB7, L6M level 24.0 vs 21.7); this table uses PB7.

## 5. SIXTY (DS3_SIXTY, DS3_SIXTY_RUN, SIXTY_BRIEF_SECTION)
903 rules clear persistence 0.60 (382 at 0.70). Out of sample the 0.60 selection stayed positive 51% (CI 45-57) vs 41% for recent-positive rules; dollars 3 months later -2% of recent. At shrunk size the 493 streamed rules add +107.9k/wk L6M (in-sample), +11.8k PRE, PRE worst-20 -7.8% (deeper). 89 are runnable on D6 v2.3b / D7 v1.0; 16 are Shadow candidates; **none is live-eligible**; no alt-bar rule is listed. STRICT 543 / TOLERANT 167 (literal clause 5 = PRE>0). Shadow only.

## 6. OFF / CLOSED (detail in the reports)
Risk-off: hold the original stop; one CANDIDATE-RECENT AND2 stop move, +0.5..+1.1k/wk inside MDE, forward register only (DS3_RISK_OFF_FINAL). Quit-when-up: 0 PASS, 93-95% of the giveback is random order (DS3_QUIT_FINAL). Halt-resume: PE halt -10.5k L6M (DS3_HALT_FINAL). No-trade C/D: no skip rule survives, selection vs L6M correlation -0.23 (DS3_NO_TRADE_C_D). RE-5: 0 PASS, 7 CANDIDATE (5 ideas), all shadow; RE-6: 688 new recent-positive rows, 0 implemented, 2 earn "<= 25% size" at most. UF entry C8 tag multipliers are structure (C12 stopped: no new entry hypothesis); INFO-3 null (DS3_L2_UF_*, DS3_L2_INFO_3). Earlier OFF list (exits, brackets, bar types, zones, cross-day) unchanged from v5.

## 7. INSTITUTIONAL
INST agents still running: autopilot/DS3_INSTITUTIONAL.md; interim lands by Sun 11:00Z. Nothing from it is in any number above.

## 8. DO TONIGHT (FORWARD_SHADOW_RUNBOOK; D6 v2.3b has no log writer, v2.4 after Sunday)
Save the NT8 Output text each evening to incoming/d6_output_YYYYMMDD.txt; log every signal incl. SKIPPED with >= 26 pre-bars; keep 45-s bars for P6; HM weekly NQ ohlcv-1s from Sat 11-07 (~$1.15/wk, approved); raw MBO no. Answered 14:30Z and honoured: K6 split; ER half-up min 1 headline; slip +0.25 / +0.45; Stop A/B by day-of-month; paper-log books yes; leaderboard tier + capped column.

## 9. OPEN QUESTIONS (DEFAULT in brackets; rest in MORNING.md)
1. Combined week lock multiple (12R from the HALT text?) [read it from the code; assume 12R, report C2].
2. Does today's as-is run the combined lock (decides C1/C2/C3)? [no: C2].
3. SizeMult before K6's first signal of the day [1.0].
4. Entry-test P&L gross or net; stop pts the signal stop or fixed 60 [as modelled: net, 60].
5. 20-30 real D6 Output-log lines (TAKEN, SKIPPED, fill, stop; time zone) [grammar guesses].
6. ER sizer books list in D6 [log all six in shadow; P6+K6 for any later switch].
7. Alt-bar: rebuild the store from the de-duplicated tape; which Shadow mode [rebuild; 24-h engine with session slice].
8. Trade-sum programs (THPC2, THL, L2SP, EXP1, UF-LOSS, CUTWAIT) removed from the portfolio line? TOLERANT clause 5 as written? [show both; literal gate].
