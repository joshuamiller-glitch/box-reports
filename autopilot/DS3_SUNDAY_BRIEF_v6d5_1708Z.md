# DS3_SUNDAY_BRIEF v6 draft 5 (from draft 4 = DS3_SUNDAY_BRIEF_v6d4_1656Z.md). Deadline Sun 2026-11-01 12:00 ET = 17:00Z; D6 start Sun 18:00 ET.
Nothing here is a PASS. Post-hoc. Masks capped 20260206; TAPE-1 disclosed a timestamp/key-column-only scan of post-cap tape months (no price or volume used). $k/week vs "the stack as it is", MDE in (), `*` beyond MDE; report names drop DS3_. Audits: DS3_SUNDAY_BRIEF_AUDIT_v6.md, _v6d3.md. Tags K6=KB, P6=PE, U6=SM, H6=HM, M6=MV, A6=PB7; O6 in no number. Live lots K6 2, P6 7, U6 4, H6 4 Asia / 2 NY-AM, M6 2, A6 1. TOLERANT = the literal gate only.

## 1. FIRST SCREEN: WHAT THE PROPOSED ON SET EARNS (ON_SET.md on the ONE_CONVENTION engine; lead proposal, you decide)
**The ON set (70/30 split on the five split books, A6 at market per ON-1; D6 locks; parity stop; no ER sizer, PE 45-s, zone skip or Asia cut) earns about nothing over the as-is stack.** D6 has the combined week lock (your answer): as-coded line C2 12R: **-5.4 (15.8) L6M**; C1 (no combined lock) is +0.5 (9.8). All L6M gain at C1 is the Native stop: join 2.45 everywhere gives -0.8 (K6 split) / +0.4 (K6 market). It assumes the A/B on all six books; FORWARD_STOP_AB starts with U6, H6 (join rejected 6 of 13, fill 8/21).
Recent-first, 14 / 28 / 32 / 75 / 44 weeks:
| set (K6 split unless noted) | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| **ON set, C2 12R vs UNLOCKED as-is (as coded)** | **-3.5 (27.0)** | **-5.4 (15.8)** | **-3.2 (14.7)** | **-8.9 (10.8)** | **-1.4 (8.7)** |
| ON set, C1 no combined lock | +0.6 (17.0) | +0.5 (9.8) | +0.7 (8.8) | +0.4 (4.1) | +3.3 (4.6) |
| ON set, K6 market, C1 / C2 12R | +1.9 / -3.4 | +1.8 / -4.7 | +1.5 / -2.8 | +0.8 / -8.5 | +3.2 / -1.6 |
| ON + ER sizer P6+K6, C1 | +8.9 (14.0) | +10.1 (9.6)* | +9.2 (9.5) | +0.9 (9.3) | +4.1 (14.0) |
| ON + ER sizer P6+K6, C2 12R | +3.6 | +1.7 | +4.3 | -6.2 | +1.8 |
| *memo, not the ON set:* six-piece, C1 / C2 12R | +22.3 / +16.9 | +19.4* / +10.6 | +16.7 / +9.5 | +4.5 / -3.5 | +11.4 / +4.5 |
ER sizer P6+K6 beyond MDE (DS3_ON_SET Table 1): C1 L6M; with K6 at market C1 L6M and HOLD (+9.6 (8.9)*); C3 12R rows L6M and HOLD. Its step over the ON set, +9.6 (12.1), and the all-six sizer in DS3_REGIME_STRESS (+13.4~) are inside MDE. The six-piece +19.4 (old headline, not the ON set) splits: ON set +0.5, ER P6+K6 +9.6, other pieces +9.3 (12.1). C2 conservative; C3 (same lock on both) flatters.
K6 market minus split (sign differs by convention, inside MDE; K6 keeps the split, your answer):
| ON set | six-piece composite (C1 +18.9 vs +19.4) | SUNDAY_DECISION |
|---|---|---|
| +1.2 (2.9) | -0.5 | -0.7 |
**Switch list:** ON split (group 05; dip 3 pt) and D6 locks as coded. A/B stop (odd day-of-month Native, even JoinThenMarket; Mon 11-02 = B; compare within one ON set). SHADOW: ER sizer (P6 lean keep, K6 weak keep), PE 45-s, zone skip, Asia cut50, NY-PM end skip, alt-bar cells. OFF: D7 group 12 (a)-(d) (0 of 19 lines ON; maxDD L6M 22.9 to 44.0 on one week, D7F_RULE_A), sizers on U6/H6/M6. D6 lines: Appendix A.

## 2. HAZARDS
1. **Persistence.** Positive in L3M and L6M -> positive next quarter 41% (CI 36-47) vs 50%; no Sunday piece persists (6-month t 0.3-2.6). Shrunk-size six-piece +2.2 (0.6) L6M (+2.1/+2.2/+2.3/+1.8) is an older engine (Native daily, library PB, no combined lock), not the ON set's +0.5; Native OFF +0.0 (0.5). Regime-faded delta +20.4 now vs +9.1 [+1.9,+16.5] in 2023-24.
2. **Combined week lock, multiple unknown (12R assumed).** Costs the six-piece 8.9 L6M at 12R (5.8 older engine); PRE vs unlocked as-is negative at every multiple:
| multiple | 8R | 12R | 16R | 20R | 30R | 12R m0 0.5 |
|---|---|---|---|---|---|---|
| PRE | -6.9 | -3.5 | -1.0 | -2.7 | -2.5 | -7.7 |
3. **Lock-widening is ~80% of any size-up** (x1.5 +18.6k, 3.5k if not widened); ER gain needs running-max locks (planned-lot +2.7 / -2.4 PRE).
4. **Post-hoc.** Full-size walk-forward -18.6k vs leverage; re-entry shares, ER sizer 200% gross / 32% net: UNIT_AUDIT KEY POINT 4.
5. **Tape defect: 11 label days; composite unaffected** (lock engine, L2, trade library clean; PE 45-s 115 of 89,464 events, none NY). Affected: BAR-STORE, tick library, footprint/lsim/zen bars; `identity_target` for 20260202.
6. **Alt-bar identity.** Edges need the engine running all sessions as a ghost; armed in-window only, trades change (L01610 HOLD n 74 vs 175, +1.1 vs -6.2); L02783 is a 4-minute chart.
7. **Stop A/B n=21:** join 2.45 vs Native 1.28 (n=8, other books; 2.20 on the same stops): +1.17, z 1.6, one-sided p 0.055; ~200 stops per arm: 6-8 weeks all books, 22-33 for U6+H6.

## 3. RISK (ONE_CONVENTION Table E, ON_SET Table 5; no significance claim)
| L6M, no lock | mean / maxDD / worst week | PRE worst-20 (PRE maxDD) |
|---|---|---|
| six-piece | 41.1 / 23 / -23 | -875 vs -811 as-is (maxDD 241 vs 162 unlocked); 12R -608 vs -585 |
| ON set | maxDD 73 / -71 | |
| ON + ER P6+K6 | maxDD 75 | -1009 vs -811 |
| as-is | 21.7 / 88 / -88 | -811 |
12R: six-piece maxDD 27 vs as-is 116; no set has a PRE tail advantage; the recent benefit rests on one week (2026-01-19). SUNDAY_RISK_2 (older engine, same-lock comparator): maxDD 28 vs 108-116 in L3M-HOLD, 149-week 12R worst-20 139k worse: two comparators, two readings.

## 4. PER BOOK (ON set, L6M; ON_SET; proposal)
U6 +1.5 and M6 +0.5 are the only positive; K6 split -1.0; A6 0.0; P6 ER gain +6.5. 
| older six-piece-candidate delta L6M/HOLD/PRE/X', K6 market, no parity (SUNDAY_DECISION sec 6) | P6 | K6 | H6 |
|---|---|---|---|
| delta | +15.9/+13.7/+6.0/+7.5 | +1.7/+1.5/-0.9/+1.4 | +4.0/+3.4/-0.5/+0.8 |
**NY-PM end skip:** +4.1 (MDE 4.05) L6M is a research-lot figure; at live lots only K6, A6 trade NY-PM (-0.1k..+0.1k). INST-2 reads 14:40-15:00 signals as adverse drift (-13..-24 pts), NP-1 as composition (K6 skipped +8.3 pts each): they disagree. SizeMult on a blocked signal: NP updates, D7 (your answer) does not: confirm.
| NY-PM skip, research lots L6M | P6 | H6 | S6 | U6 | W6 | K6 | A6 | M6 | MA6 |
|---|---|---|---|---|---|---|---|---|---|
| by book | +2.0 | +1.2 | +0.9 | +0.2 | +0.1 | -0.6 | -1.1 | -0.5 | -2.5 |
**Alt-bar** (ALT_BAR_IDENTITY; M pts/contract): all fail G6, HOLD CIs include 0; Shadow only.
| cell | L3M | L6M | trades/wk | tier |
|---|---|---|---|---|
| L02766 | +11.00 | +5.47 | 4.22 | LEAD |
| L01501 | +5.80 | +5.34 | 3.43 | LEAD |
| L01610 | +2.90 | +0.76 | 2.54 | CANDIDATE-RECENT |
| L01490 | +11.88 | +5.78 | 3.51 | LEAD |
| L02783 | +9.72 | +9.59 | 3.25 | LEAD |

## 5. SIXTY (SIXTY_RUN v2)
903 rules clear 0.60; 206 independent clusters among 493 streamed (SD ratio 0.27); streamed programs 51% positive out of sample (CI 45-57) vs 50%: coin flip (old wording: SIXTY_BRIEF_SECTION.md, SIXTY l.9). +107.9k/wk is trade-sum M-basis dollars, not evidence; lock-engine stack-delta streams +52.5k L6M, +6.8k PRE, PRE worst-20 24.4% deeper. 89 of 903 runnable, 0 Live-eligible, 16 Shadow candidates; no alt-bar rule.

## 6. CLOSED / NULL
Risk-off (NTE-2, RO-2): hold the stop; one CANDIDATE-RECENT stop move (+0.5..+1.1k, inside MDE), forward register only. Quit-when-up 0 PASS; halt-resume (six books) -10.5k L6M. No-trade C/D: no skip survives; one size-up cell CONFIRMED-RECENT, labelled structure, not promoted. L2 loops closed (INFO-3 null; entry C8, C10, C12); RE-5 0 PASS; RE-6 0 implemented.

## 7. INSTITUTIONAL (Shadow only; INST-4 pending: INSTITUTIONAL.md; interim by Sun 11:00Z)
INST-1: best idea (skip K6 NY-PM/close after interior single prints) +1.2k L6M at MDE, RW p 0.17, PRE negative at 12R; auction books flip sign; minute-of-day rules fail. INST-2: working buyer/seller in 4.2% of RTH minutes, books already trade with it; WITH x1.5 / AGAINST x0.5 +1.35k (MDE 2.48k) fails literal TOLERANT; toxicity predicts move size, not direction. INST-3:
| section | literal TOLERANT | stack L6M (MDE) | PRE | placebo cell / program p |
|---|---|---|---|---|
| C cross-market | 0 (YM-60 passes only post-hoc TOL-B) | +7.3k (12.8k) inside MDE | -2.2k | 0.32 / 0.41 |
| F flow calendar | 1 | +1.6k (3.3k) | | 0.16 / 0.83 |

## 8. DO TONIGHT (D6 v2.3b has no log writer)
Save NT8 Output nightly to incoming/d6_output_YYYYMMDD.txt plus fills.csv (week 1 if parseable, else 2). 45-s bars and >= 26 pre-bars: v2.4. HM weekly ohlcv-1s from Sat 11-07 (~$1.15/wk, approved). Honoured: K6 split, half-up min 1, slip +0.25/+0.45, day-of-month parity, paper-log books.

## 9. OPEN QUESTIONS [DEFAULT]
1. Combined week lock multiple [12R, C2, read from code]. 2. Does today's as-is run it [no: C2]. 3. SizeMult before K6's first signal [1.0]. 4. Entry-test gross or net; stop pts signal or 60 [net, 60]. 5. 20-30 real Output-log lines [grammar guesses]. 6. ER sizer books list [log six; P6+K6 for any switch]. 7. Alt-bar store rebuild [yes]. 8. Trade-sum programs out of the portfolio line [show both; literal gate]. 9. D6 property names for the ON set (Appendix A) [D6 owner supplies].

## Appendix A (not counted in body). E9: D6 lines for the ON set as they stand in THP v2 and the spec
Sources: THP_POLICY.txt (v2, fit 2026-10-30T01:42Z; "ENTRY FIELDS" names follow the L2SE vocabulary, "the exact property labels were not visible to the box, map by meaning"), FORWARD_SHADOW_SPEC.md l.6 and l.13, SUNDAY_WORK_BRIEF.md l.2, d6_book_defaults.json (l2vast/ds3/code/shadow/), DIRECTIVE_USER_REPLY_20261031_1430.md. Property names below are THP field names, not D6 panel labels. Nothing invented.
| D6 group | property (as named in repo) | value for the ON set | source | status |
|---|---|---|---|---|
| 05 (entry) | split % (THP field split_F) | 0.7 (70/30); ONE panel setting for all gated books | THP default line; SPEC l.13 | in repo; per-book split = code change |
| 05 | dip (THP dip_X) | 3 pt from signal price (long below, short above) | THP default line | in repo (THP name; D6 label not in repo) |
| 05 | basis (basis) | i (from signal price) | THP default line | in repo (THP name) |
| 05 | confirmations (confirmations_N), gates | 1 of default8 | THP default line | in repo (THP name) |
| 05 | veto (veto_imb5) | -0.40 | THP default line | in repo (THP name) |
| 05 | chase (chase_Y), limit join (limit_join_s), eval | off, 0, 1s | THP default line | in repo (THP name) |
| 05 | K6 split | kept (split at 0.7, not market) | SPEC l.13; user 14:30Z | in repo |
| 05 | P6 | splits 70/30 like the others (live_entry_mode = split70_30); THP P6 market-entry line NOT read | SPEC l.13; user 14:30Z; d6_book_defaults.json | in repo |
| 05 | A6 at market | A6 entry at market | brief draft 4 / ON-1 | not in repo: D6 owner to supply (SPEC l.13: split is one setting for all gated books; THP lists PB/A6 under the default split line, no A6 market line) |
| ? | stop A/B parity (R7) | day-of-month of the exchange trade date; odd = Native stop-market A, even = JoinThenMarket (3 s) B; Mon 2026-11-02 = B | SPEC l.6 (code: fills_join.ARM_PARITY = 'dom') | rule in repo; D6 group/property: not in repo: D6 owner to supply |
| ? | D6 locks (day / week) | as coded; week lock R = K6 BookR; per-book week locks use own BookR; SizeMult = running max, reset 18:00 ET | SUNDAY_WORK_BRIEF l.2 | rule in repo; group/property/value: not in repo: D6 owner to supply |
| ? | lots per book / session | K6 2, P6 7, U6 4, H6 4 Asia / 2 NY-AM, M6 2, A6 1 (by session in d6_book_defaults.json) | d6_book_defaults.json; SUNDAY_WORK_BRIEF | values in repo; D6 property name: not in repo: D6 owner to supply |
| ? | stop / target distance per book | null for every live book in d6_book_defaults.json | d6_book_defaults.json | not in repo: D6 owner to supply |
| 12 (D7) | filters (a)-(d) | OFF | brief section 1 | switch is OFF; property names not in repo |
