# DS3_SUNDAY_BRIEF v6 draft 2 (stamp 2026-10-31T16:41Z = file mtime). Deadline Sun 2026-11-01 12:00 ET = 17:00Z; D6 start Sun 18:00 ET.
Nothing here is a PASS. Post-hoc, capped 2026-02-06, UNTOUCHED never read. $k/week vs "the stack as it is", MDE in (), `*` beyond MDE. Prior: DS3_SUNDAY_BRIEF_v6d1_1640Z.md, audit DS3_SUNDAY_BRIEF_AUDIT_v6.md. Tags K6=KB, P6=PE, U6=SM, H6=HM, M6=MV, A6=PB7; O6 in no number (NY-PM block applies per NP spec; first-60 rule exempt: confirm). Live lots K6 2, P6 7, U6 4, H6 4 Asia / 2 NY-AM, M6 2, A6 1.

## 1. FIRST SCREEN (lead proposal; no report assigns ON/SHADOW/OFF; you decide)
| | Rule | Numbers |
|---|---|---|
| ON | 70/30 split, dip 3 pt, all books (K6 keeps it, your answer; P6 splits) | split leave-one-out L6M +4.1 [+0.5,+8.0], HOLD +3.9, 2023-24-like state -0.4: inside MDE (DS3_REGIME_STRESS) |
| ON as coded | D6 locks (planned-lot R x running-max SizeMult) | multiple of combined week lock unknown (E1) |
| SHADOW | ER(20) sizer (P6 lean keep, K6 weak keep), PE 45-s, zone skip, Asia cut50, NY-PM end skip (ships OFF in D6), alt-bar cells L02766 L01501 L01610 L01490 L02783 | sections 2, 4 |
| A/B live | Stop: odd day-of-month Native, even JoinThenMarket; Mon 11-02 = B | FORWARD_STOP_AB.md; compare arms WITHIN one ON set: do not mix with ON-set changes (the split/ER/PE alter which stops occur) |
| OFF | D7 group 12 (a)-(d); sizers on U6 H6 M6; section 6 | DS3_D7_FILTERS 0 of 19 lines ON; DS3_D7F_RULE_A (a): maxDD L3M 21.4 to 44.0, L6M 22.9 to 44.0, one week, sign flips in HOLD/PRE/X' |

**WHAT THE TABLES BELOW PRICE.** C1/C2/C3 and the risk table are the SIX-PIECE composite (split, PE 45-s, zone skip, Asia cut, ER sizer on all six books, Native/join parity), NOT the ON set above (split + locks). Leave-one-out L6M (DS3_SUNDAY_DECISION sec 6): cut +0.4, PE +4.1, zone +6.4, split +3.6, sizer +13.5 (15.4)~, all inside MDE; the sizer also widens locks.
**ON set priced in DS3_ON_SET.md (ON-1 running, due ~60 min): [slot, numbers not yet available].**

DS3_ONE_CONVENTION (A6=PB7, live lots, integer half-up min-1 ER lots, running max over TAKEN signals, parity stop, slip +0.25, K6 70/30), recent-first:
| comparison | L3M (14 wk) | L6M (28) | HOLD (32) | PRE (75) | X' (44) |
|---|---|---|---|---|---|
| C1 no combined lock | +22.3 (22.3) | +19.4 (17.5)* | +16.7 (17.3) | +4.5 (13.2) | +11.4 (14.0) |
| **C2 12R on composite vs UNLOCKED as-is (conservative)** | +16.9 (27.4) | +10.6 (26.5) | +9.5 (26.7) | -3.5 (15.3) | +4.5 (14.1) |
| C2 20R | +11.6 (34.3) | +13.1 (21.9) | +10.1 (23.3) | -2.7 (15.3) | +6.7 (15.2) |
| C2 30R | +19.4 (24.9) | +16.6 (18.9) | +14.4 (18.2) | -2.5 (14.9) | +10.1 (14.4) |
| C3 12R on BOTH (flatters) | +25.1 (21.2)* | +21.9 (27.3) | +17.7 (27.2) | +5.4 (11.9) | +8.3 (13.8) |
| K6 at market, C1 / C2-12R (your request) | +20.2 / +15.5 | +18.9 / +10.3 | +16.5 / +9.5 | +3.9 / -4.3 | +11.5 / +5.1 |
Which applies: C2 if today's as-is has no combined lock; C3 if it has the same lock; C1 if D6 has none. K6 at market costs 0.5 L6M here, 0.7 in DS3_SUNDAY_DECISION (convention). Stress slip +0.45 lowers cells 0.1-0.5 (Table C). Levels L6M: composite 41.1 / 32.3 at 12R; as-is 21.7.

## 2. HAZARDS
1. **Persistence.** Positive in L3M and L6M -> positive next quarter 41% (CI 36-47) vs 50% coin (DS3_PERSISTENCE, RE-1). No Sunday piece persists (6-month t 0.3-2.6); persisting families are profit-protect exits on the take-at-70% leg (97.6%) and some sizing cells (DS3_PERSISTENCE_SUNDAY). **Shrunk-size composite: +2.2 (0.6) L6M, +2.1 L3M, +2.2 HOLD, +2.3 PRE, +1.8 X'; it assumes Native on EVERY day (library PB, no parity, no combined lock); Native OFF gives +0.0 (0.5); the saving itself is z 1.6, one-sided p 0.055, n 21 vs 8.** Regime-faded: delta +20.4 now vs +9.1 [+1.9,+16.5] in a 2023-24 mix; level 42.2 to 12.4 (DS3_REGIME_STRESS).
2. **Combined week lock, multiple unknown (12R assumed from the HALT text).** Costs the composite 8.9 L6M at 12R (ONE_CONVENTION; 5.8 in GOVERNOR_FIDELITY / LOCK_SWEEP / HALT_FINAL, library PB V4); fires 8/28 L6M weeks, 71/149. **PRE is negative against unlocked as-is at every multiple tested: 8R -6.9, 12R -3.5, 16R -1.0, 20R -2.7, 30R -2.5, 12R with m0 0.5 -7.7**; 8R L6M +0.6 (Tables B, F). Not run: lock with persistence shrinkage, or on the ON set.
3. **Lock-widening is ~80% of any size-up.** Uniform x1.5 +18.6k L6M, 3.5k if locks are not widened (DS3_NO_TRADE_C_D). ER sizer gain needs running-max locks; planned-lot locks +2.7 six-book / -2.4 PRE (DS3_ER_SIZER_ROBUSTNESS).
4. **ER sizer evidence is not established.** P6+K6 sizer +14.0 (13.2) L6M, 0.8 above MDE, L6M only; HOLD +12.6 (13.0)~, PRE +2.9 (6.7)~, X' +1.8 (7.6)~; all-six +13.5 (15.4)~ (DS3_SUNDAY_DECISION); regime report +13.4~; whole sizer in-stack +12.5 (23.5) inside MDE, six-book shuffled-ER 0/200 on the ER-1 engine (ER_SIZER_ROBUSTNESS). The Native stop is the one item above MDE in all five windows (+2.2 (0.6)...+1.8 (0.2)), and it is the unproven 1.17 pt/stop saving.
5. **Post-hoc.** Pieces chosen after seeing L6M/HOLD (v5). Full-size monthly walk-forward on the D6 engine +59.4k (MDE 44.2), 3.6x SD, -18.6k vs leverage (DS3_RECENT_EDGE_6); research-engine -9.6k/wk, -5.5k shrunk (RE-1/2 as carried in v5; not re-checked).
6. **Tape defect: 11 label days (weekend-start months); composite unaffected** (lock engine, 1-s/1-min, L2, trade library clean; PE 45-s differs on 115 of 89,464 events, none NY). Also affected: BAR-STORE (all 164 series), tick library, footprints/lsim/zen/pbx bars (flagged, not corrected). Alt-bar identity: for 20260202 use `identity_target`, not library rows. Weekly ext tape 2026-10 and the 2026-11 file carry it (DS3_TAPE_DEDUP, DS3_ALT_BAR_IDENTITY).
7. **Stop A/B n=21.** Join 2.45 pts/stop (n=21) vs Native 1.28 (n=8, other books; 2.20 on the same stops): +1.17, z 1.6, one-sided p 0.055; join fill 0.38 vs replay 0.78; ~200 stops per arm: 6-8 weeks if all books switch, 22-33 weeks for U6+H6 alone.
8. **Re-entry shares** (research lots, older engine; DS3_UNIT_AUDIT KEY POINT 4, not re-run on ONE_CONVENTION): split 47-55%, PE 58%, Asia cut 71%, zone skip 85%, KB sizer 88%, ER sizer 200% gross / 32% net; >50% of each candidate's gain in 5 weeks. Forward reads need ~60 weeks (ER sizer) to ~230 (HM FVG).

## 3. RISK (ONE_CONVENTION Table E, lock off; mean / maxDD / worst week; no significance claim)
| | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| composite | 34.4/21/-21 | 41.1/23/-23 | 38.6/97/-68 | 23.1/241/-120 | 8.0/121/-66 |
| as-is | 12.2/88/-88 | 21.7/88/-88 | 21.9/144/-88 | 18.6/162/-96 | -3.4/317/-71 |
Recent tail benefit rests on one week (2026-01-19). PRE not lighter (maxDD 241 vs 162; worst-20 -875 vs -811). With 12R on the composite: L6M maxDD 27 vs 23 unlocked; PRE worst-20 -608 vs as-is 12R -585. DS3_SUNDAY_RISK_2 (older V4 engine, library PB, same-lock comparator): D6 maxDD 28 vs as-is 108-116 in L3M-HOLD (lighter, CI excludes 0), PRE not distinguishable, over 149 weeks the 12R worst-20 is 139k worse for D6. Two comparators, two readings.

## 4. PER BOOK (PROPOSAL; DS3_SUNDAY_DECISION sec 6: deltas are the CANDIDATE = sizer P6+K6, **K6 at market**, NY-PM skip, no parity; sum 21.6 L6M includes SHADOW pieces, not the ON set)
| book | split | ER sizer (off = ) | L6M / HOLD / PRE / X' | other |
|---|---|---|---|---|
| P6 7 | ON | SHADOW, lean keep (-11.5) | +15.9/+13.7/+6.0/+7.5 | PE 45-s, zone SHADOW |
| K6 2 | ON (your answer; delta is K6 at market) | SHADOW, weak keep (-2.4) | +1.7/+1.5/-0.9/+1.4 | zone SHADOW |
| H6 4/2 | ON | OFF (-0.1) | +4.0/+3.4/-0.5/+0.8 | cut SHADOW |
| U6 4 | ON | OFF (+0.9) | -0.1/-0.3/-0.2/+1.5 | |
| M6 2 | ON | OFF (+0.6) | +0.3/+0.2/-0.0/+0.4 | |
| A6 1 | n/a | inconclusive (-0.9, MDE 1.4) | -0.1/+0.0/-0.1/+0.3 | |
NY-PM end skip 14:40-15:00, L6M market, research lots (DS3_NYPM_END_SKIP): alone +4.1 (MDE 4.05); P6 +2.0, H6 +1.2, S6 +0.9, U6 +0.2, W6 +0.1; K6 -0.6, A6 -1.1, M6 -0.5, MA6 -2.5; in the composite +0.7 L6M research lots, 0.0 (0.8) live (D1), K6 -0.24 $k live (NP engine, A6 library PB). SizeMult disagreement: NP spec says a blocked signal updates the running max; D7 (your answer) says it does NOT: confirm.
Alt-bar (DS3_ALT_BAR_IDENTITY): L6M per contract M pts L02766 +5.47, L01501 +5.34, L01610 +0.76, L01490 +5.78, L02783 +9.59; 4.22/3.43/2.54/3.51/3.25 trades/wk; all fail G6, HOLD CIs include 0; Shadow only. A6 as-is base 24.0 (library PB) vs 21.7 (PB7): two reports.

## 5. SIXTY (SIXTY_BRIEF_SECTION.md, DS3_SIXTY, DS3_SIXTY_RUN)
903 rules clear persistence 0.60 (382 at 0.70). Streamed programs: 51% positive out of sample (CI 45-57) vs base 50% = coin flip (MORNING 16:27Z correction; the 31% family-mix figure is for the whole list incl. CF-COMBO; SIXTY_BRIEF_SECTION.md and DS3_SIXTY l.9 still carry the old wording). Dollars 3 months later -2% of recent. The +107.9k/wk portfolio line is M-basis trade-sum dollars (THPC2, THL, L2SP, EXP1, UF-LOSS, CUTWAIT): not evidence. Lock-engine stack-delta streams alone: +52.5k L6M, +6.8k PRE, PRE worst-20 24.4% deeper. 89 rules runnable on D6/D7, 16 Shadow candidates, none live-eligible; no alt-bar rule listed. Shadow only.

## 6. OFF / CLOSED
Risk-off: hold the original stop; one CANDIDATE-RECENT stop move +0.5..+1.1k inside MDE, commented THP_POLICY line only (DS3_RISK_OFF_FINAL). Quit-when-up 0 PASS (DS3_QUIT_FINAL). Halt-resume: rolling-20 -3R halt on all six books -10.5k L6M (MDE 16.3k), cost not saving (DS3_HALT_FINAL). No-trade C/D: no skip survives; one size-up cell carries the prereg tag CONFIRMED-RECENT, labelled structure, not promoted (DS3_NO_TRADE_C_D). RE-5 0 PASS, RE-6 0 implemented; C8/C12 and INFO-3 null. Earlier OFF list unchanged from v5.

## 7. INSTITUTIONAL
INST agents still running: autopilot/DS3_INSTITUTIONAL.md; interim lands by Sun 11:00Z. Nothing from it is in any number here.

## 8. DO TONIGHT (FORWARD_SHADOW_RUNBOOK)
D6 v2.3b has no log writer: save the NT8 Output text nightly to incoming/d6_output_YYYYMMDD.txt plus fills.csv; week 1 from the Output log if parseable, else week 2; log every signal with >= 26 pre-bars; 45-s bars for P6; HM weekly ohlcv-1s from Sat 11-07 (~$1.15/wk, approved). Honoured from 14:30Z: K6 split, half-up min 1, slip +0.25/+0.45, day-of-month parity, paper-log books; leaderboard capped column not checked here.

## 9. OPEN QUESTIONS [DEFAULT]
1. Combined week lock multiple [read from code; assume 12R, report C2].
2. Does today's as-is run the combined lock [no: C2].
3. SizeMult before K6's first signal [1.0].
4. Entry-test P&L gross or net; stop pts signal or fixed 60 [net, 60].
5. 20-30 real D6 Output-log lines [grammar guesses].
6. ER sizer books list in D6 [log all six; P6+K6 for any switch].
7. Alt-bar: rebuild store from de-duplicated tape [yes; 24-h engine with session slice].
8. Trade-sum programs out of the portfolio line; TOLERANT clause 5 [show both; literal gate].
