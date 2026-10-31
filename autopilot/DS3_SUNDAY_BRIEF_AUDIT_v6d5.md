# DS3_SUNDAY_BRIEF_AUDIT_v6d5 - BA-4 final independent audit of DS3_SUNDAY_BRIEF.md (v6 draft 5, mtime 2026-10-31 17:01:57Z) - brief NOT edited

Brief line numbers = lines of DS3_SUNDAY_BRIEF.md (d5). Severity H/M/L as in BA-2/BA-3. Sources read: DS3_ON_SET (all), ONE_CONVENTION (plain sentence, bridge, final table, Table B), SUNDAY_RISK_2 p1, SIXTY / SIXTY_RUN / SIXTY_BRIEF_SECTION, INSTITUTIONAL (+INST_B), NYPM_END_SKIP (per-book + stack lines), TAPE_DEDUP, LOCK_SWEEP, FORWARD_STOP_AB, FORWARD_SHADOW_SPEC, THP_POLICY.txt, d6_book_defaults.json, SUNDAY_DECISION (l.321), DIRECTIVE_INSTITUTIONAL.

## 1. Status of the 26 (BA-2, v6) and 27 (BA-3, v6d3) findings in draft 5

CLOSED = fixed or correctly moot; PARTLY = main point fixed, residual named; OPEN = not fixed.

### BA-2 v6 (26)
| # | Status | Where in d5 |
|---|---|---|
| 1 ER sizer "only piece clears MDE" | CLOSED | l15: beyond-MDE cells listed, step +9.6 (12.1) and all-six +13.4~ inside MDE. Residual L: the cell list is not exhaustive (also market C2 30R HOLD +11.2 (10.5)*, C3 30R market HOLD, stress rows) |
| 2 SIXTY +107.9k | CLOSED | l62 "trade-sum M-basis dollars, not evidence; lock-engine streams +52.5k / +6.8k / 24.4% deeper" |
| 3 composite is not the ON set | CLOSED | l5, l14 "memo, not the ON set", l15 split 0.5 / 9.6 / 9.3 |
| 4 shrunk composite convention | CLOSED | l23 older engine (Native daily, library PB, no lock), Native OFF +0.0 (0.5). Residual L: "+2.1/+2.2/+2.3/+1.8" unlabelled (= L3M/HOLD/PRE/X'); parity halving not said |
| 5 SIXTY 51% resolution | CLOSED | l62 "51% vs 50%: coin flip (old wording ...)" |
| 6 RISK_2 convention | CLOSED | l41 "older engine, same-lock comparator ... two comparators, two readings" |
| 7 PRE range | CLOSED | l24-27 five multiples + m0 0.5 (but see new N2: table not labelled six-piece) |
| 8 re-entry-share citation | CLOSED (pointer) | l29 UNIT_AUDIT KEY POINT 4, 200% gross / 32% net; the 47-88% shares themselves dropped |
| 9 tape scope | CLOSED | l30 affected stores + identity_target (but see N3) |
| 10 fold-in items 2, 3, 5 | PARTLY | l52-59 alt-bar table, l49-51 NY-PM per-book table; persistence family list (70-83% rules) not in brief, only "no Sunday piece persists" l23 |
| 11 NY-PM +4.7 / K6 / SizeMult | CLOSED | l48 +4.1 (4.05), research-lot label, SizeMult conflict "confirm" |
| 12 section 4 K6 label | CLOSED | l45-47 header "K6 market, no parity"; sum 21.6 not warned (L) |
| 13 D7F omissions | PARTLY | l20 "on one week"; engine difference and sign flip in HOLD/PRE/X' not stated |
| 14 halt scope | CLOSED | l65 "(six books) -10.5k"; MDE 16.3k and "cost" label dropped (L) |
| 15 8.9 vs 5.8 | CLOSED | l24 |
| 16 stress slip range | MOOT | sentence removed |
| 17 C2 20R/30R row | MOOT | row removed (but see N1: ON set vs multiple not shown) |
| 18 K6 market five-window | CLOSED | l11 five-window row, l16-19 sign table |
| 19 stop A/B details | CLOSED | l5 (U6/H6 first, rejected 6 of 13, fill 8/21), l32 (one-sided p, other books, same stops, 6-8 / 22-33 wk), l20 "within one ON set" |
| 20 leaderboard / fills.csv | CLOSED | l75 fills.csv + week-1/2 rule; leaderboard claim deleted |
| 21 RE-5/RE-6 | CLOSED | l65 |
| 22 CONFIRMED-RECENT D cell | CLOSED | l65 "one size-up cell CONFIRMED-RECENT, labelled structure, not promoted" (no +13.8 (11.7), no 64% widening: L) |
| 23 0/200 scope | MOOT | removed |
| 24 -9.6k/-5.5k source | MOOT | removed; -18.6k kept without its MDE 43.0k (L, = BA-3 #19) |
| 25 O6 under NY-PM / rule (a) | OPEN (trivial) | l2 "O6 in no number" only |
| 26 DST / deadline | CLOSED | l1 12:00 ET = 17:00Z correct |

### BA-3 v6d3 (27)
| # | Status | Where in d5 |
|---|---|---|
| 1 H ER sizer sentence | CLOSED | l15 |
| 2 H INST-3 TOLERANT | CLOSED | l71-72 C = 0 literal (YM-60 only post-hoc TOL-B), F = 1; cell and program placebos separated (0.32/0.41, 0.16/0.83 verified) |
| 3 INST-1 stale | CLOSED | l68 +1.2k, RW p 0.17, PRE negative at 12R |
| 4 C2 as lead row | CLOSED | l5, l9 bold C2 12R; C1 second |
| 5 K6 market sign | CLOSED | l16-19 table (+1.2 / -0.5 / -0.7) |
| 6 12R risk row | PARTLY | l41 gives six-piece 12R maxDD 27 vs 116 and PRE worst-20 -608 vs -585; ON set / ON+ER 12R rows (maxDD 59 / 53, worst week -29 / -44) not given; ON-set lock-off PRE cell left blank in l38 although it is lighter than as-is (maxDD 114 vs 162, w20 -737 vs -811). Omission runs against the ON set, so conservative |
| 7 per-book sentence | PARTLY | l44 "only positive" fixed; P6 -0.3, H6 -0.1 not given; "P6 ER gain +6.5" is the P6 book vs as-is with sizer (sizer step +6.8) |
| 8 A6 market / D6 group-property | PARTLY | Appendix A added (good). But l5 still says "A6 at market per ON-1" as if a setting; see section 4 below. Sizer-books list not in the appendix; Q6 [log six] |
| 9 Native on all six books | CLOSED | l5 |
| 10 risk-off / D cell | CLOSED | l65 |
| 11 Native "beyond MDE" is an engine unit effect | PARTLY | warning sentence not in brief, but the starred Native rows are not printed either; z 1.6 / p 0.055 in l32; K6-market Native OFF +0.4 given, X' +2.3 not |
| 12 NY-PM live lots, INST-2 vs NP-1 | CLOSED | l48 |
| 13 alt-bar L3M, tiers | CLOSED | l52-59 table with L3M, L6M, trades/wk, tier; "all fail G6, HOLD CIs include 0" |
| 14 shrunk composite label | PARTLY | see #4 above; no bridge +2.2 vs +0.5 beyond "older engine" |
| 15 "UNTOUCHED never read" | CLOSED | l2 TAPE-1 disclosure. Open question "de-dup ext/post-cap tape after Sunday" not added |
| 16 SIXTY directive sentence | PARTLY | 206 clusters, ratio 0.27 present; effective N 47, 41% pool vs 33% all, -2% dollars missing |
| 17 DO TONIGHT v2.3b | CLOSED | l75 |
| 18 20R / 30R = C1 | OPEN (L) | brief shows ON set only at 12R and C1; 20R -1.7 and "30R = C1 (no fire in L6M)" gone; multiple is unknown (Q1) so the reader sees two points, not the range |
| 19 -18.6k without MDE | OPEN (L) | l29 |
| 20 label D1 CANDIDATE, Native 1.28 all days | PARTLY | l45 "older six-piece-candidate ... K6 market, no parity"; Native 1.28 not said |
| 21 P6+K6 +14.0 (13.2) / minus all six | MOOT/OPEN (L) | D1 line removed; "P6+K6 minus all six +0.5 (5.5)" (user decision (a)) not shown |
| 22 HALT_FINAL named | MOOT | |
| 23 halt MDE / tier | OPEN (L) | |
| 24 INST-2 best-of-carried | OPEN (L) | "best of carried cells" absent; "fails literal TOLERANT" present |
| 25 purchase pointer, interim time | OPEN (L) | l67 still "interim by Sun 11:00Z"; DIRECTIVE_INSTITUTIONAL says "Sun 12:00Z" (and the deadline is 17:00Z). Time basis unclear |
| 26 Q7 "[yes, after Sunday]" | OPEN (L) | l78 Q7 still "[yes]" |
| 27 O6 line | OPEN (trivial) | |

Count after d5: 0 H open, 1 M-level issue (A6, section 4), 3 M/L new (N1-N3), remaining open items are L.

## 2. Spot-check of 40 numbers (value, window, unit, convention)

All against the cited cell. 40 checked, 0 wrong values, 0 wrong windows. Three label/scope notes (N1-N3 in section 3).

| # | Brief cell | Source cell | Result |
|---|---|---|---|
| 1-5 | ON set C2 12R: -3.5 (27.0), -5.4 (15.8), -3.2 (14.7), -8.9 (10.8), -1.4 (8.7) | ON_SET T1 row 2 | OK |
| 6-10 | ON set C1: +0.6 (17.0), +0.5 (9.8), +0.7 (8.8), +0.4 (4.1), +3.3 (4.6) | ON_SET T1 row 1 | OK |
| 11 | K6 market C1/C2 12R L6M +1.8 / -4.7 | T1 | OK |
| 12 | K6 market PRE +0.8 / -8.5 | T1 | OK |
| 13 | ON+ER C1 L6M +10.1 (9.6)* | T1 | OK |
| 14 | ON+ER C1 PRE +0.9 (9.3); X' +4.1 (14.0) | T1 | OK |
| 15 | ON+ER C2 12R PRE -6.2, L6M +1.7 | T1 | OK |
| 16 | six-piece C1 L6M +19.4*; C2 12R +10.6 | T1 = ONE_CONVENTION final | OK |
| 17 | six-piece PRE +4.5 / -3.5; X' +11.4 / +4.5 | T1 | OK |
| 18 | Native OFF -0.8 split / +0.4 market | T2 | OK |
| 19 | beyond-MDE list (market C1 HOLD +9.6 (8.9)*, C3 12R L6M+HOLD) | T1 | OK, list not exhaustive (L) |
| 20 | six-piece no lock 41.1 / maxDD 23 / worst -23 | T5 | OK |
| 21 | as-is 21.7 / 88 / -88 | T5 | OK |
| 22 | ON set maxDD 73 / -71 | T5 | OK |
| 23 | ON+ER maxDD 75; PRE w20 -1009 vs -811 | T5 | OK |
| 24 | six-piece PRE maxDD 241 vs 162, w20 -875 vs -811 | T5 | OK |
| 25 | 12R PRE w20 -608 vs -585 | T5 | OK |
| 26 | 12R six-piece maxDD 27 vs as-is 116 | T5 | OK |
| 27 | K6 market minus split +1.2 (2.9) | T7 | OK |
| 28 | -0.5 (18.9 vs 19.4) | T6 / ONE_CONV D | OK |
| 29 | step +9.6 (12.1); other pieces +9.3 (12.1) | T7 | OK |
| 30 | U6 +1.5, M6 +0.5, K6 -1.0, A6 0.0, P6 +6.5 | T6 | OK; P6 +6.5 is the book total with sizer (sizer part +6.8) |
| 31 | PRE 8R -6.9, 16R -1.0 | ONE_CONV Table B | OK |
| 32 | PRE 12R -3.5, 20R -2.7, 30R -2.5, m0 0.5 -7.7 | final table | OK (six-piece composite, table not labelled, N2) |
| 33 | lock costs six-piece 8.9 L6M | memo row -8.9 | OK |
| 34 | RISK_2 maxDD 28 vs 108-116 L3M-HOLD | RISK_2 p1 | OK |
| 35 | RISK_2 149-wk 12R worst-20 139k worse | -139 | OK |
| 36 | SIXTY 903 / 206 clusters / 493 streamed / ratio 0.27 | SIXTY p5, l314 | OK |
| 37 | +107.9k, +52.5k L6M, +6.8k PRE, 24.4% deeper, 51% (45-57) | SIXTY, BRIEF_SECTION | OK |
| 38 | 89 of 903 runnable, 0 Live-eligible, 16 Shadow | SIXTY_RUN p1 | OK |
| 39 | NY-PM +4.1 (4.05) L6M; per-book P6 +2.0, H6 +1.2, S6 +0.9, U6 +0.2, W6 +0.1, K6 -0.6, A6 -1.1, M6 -0.5, MA6 -2.5 | NYPM per-book table (research lots, N basis) | OK |
| 40 | K6 skipped +8.3 pts/signal; INST-2 -13..-24 pts | NYPM table; INST_B l423 | OK |
| 41 | live-lot "-0.1k..+0.1k" | NYPM stack line: alone +57/-25/-72/+120 $/wk; as add-on to composite -144/-148/-266/+284 | OK for "alone"; range understates the composite add-on (N-L, label) |
| 42 | INST-1 +1.2k, RW p 0.17; INST-2 4.2%, +1.35k (2.48k) | INSTITUTIONAL | OK |
| 43 | INST-3 C +7.3k (12.8k), PRE -2.2k, 0.32 / 0.41; F +1.6k (3.3k), 0.16 / 0.83 | INSTITUTIONAL | OK; F PRE +1.1k omitted |
| 44 | tape: 11 label days, 115 of 89,464, none NY | TAPE_DEDUP | OK |
| 45 | stop A/B 2.45 vs 1.28, +1.17, z 1.6, one-sided p 0.055, 8/21, 6 of 13, ~200 per arm, 2.20 same stops | FORWARD_STOP_AB, LIVE_STOP_JOIN | OK |
| 46 | D7 (a) maxDD L6M 22.9 to 44.0 | D7F_RULE_A | OK |
| 47 | lots K6 2 / P6 7 / U6 4 / H6 4+2 / M6 2 / A6 1 | d6_book_defaults.json, SPEC | OK |
| 48 | "5.8 older engine" | LOCK_SWEEP / GOVERNOR_FIDELITY | OK |

(48 cells rows; 40+ individual values.) Nothing wrong. Conventions: C1/C2 labels, parity, slip +0.25, windows 14/28/32/75/44 all consistent with the sources.

## 3. Trim review: d4 (v6d4_1656Z) vs d5 - every dropped sentence

Dropped, and whether the loss matters:
1. "other agents' procedural notes: DS3_INSTITUTIONAL.md" and "Prior: v6d3 file" - no.
2. "Whether the live as-is stack also carries the combined lock is open (E2)" - small; it stays as Q2 (l78) and the row label says "vs UNLOCKED as-is". Matters slightly: the headline -5.4 rests on this assumption and l5 no longer says so. L.
3. "stop evidence z 1.6, one-sided p 0.055 (n 21 vs 8)" from l5 - no, kept in hazard 7 (l32).
4. "C1 if D6 had no combined lock" and "The six-piece row is the old headline: not what the ON set earns" - no, replaced by "memo, not the ON set" (l14) and "old headline, not the ON set" (l15).
5. "Other D6 group/property/value settings: not tabulated in any report yet (open item E9)" - no, replaced by Appendix A and Q9.
6. Hazard 1 "in a 2023-24 mix" -> "in 2023-24": slightly stronger; the REGIME_STRESS comparison is a normalised mix on a V0 + parity engine without the combined lock. L (restore "mix").
7. Hazard 5 "Alt-bar identity: use identity_target for 20260202; weekly ext 2026-10 and 2026-11 files carry it": the instruction is cut to a bare "`identity_target` for 20260202" at the end of the Affected list (l30). The 2026-11 clause was unsupported (BA-3) so dropping it is right, but the sentence now does not say what to do. M-L (N3).
8. Section 3: "Recent tail benefit rests on one week" -> "the recent benefit rests on one week" (l41): "tail" lost; a reader can take it as return benefit. L.
9. Section 4: "SHADOW, lean keep; K6 weak keep; sizers on U6 H6 M6 OFF" after P6 ER gain: moved to Switch list. No.
10. Section 4 pointer "(DS3_NYPM_END_SKIP)", "H6/P6 ON-set lines: DS3_ON_SET": sources gone from the line; no.
11. Section 5 "MORNING 16:27Z" correction pointer; "Shadow only." closing: heading context keeps it. No.
12. Section 6 "cost" after halt-resume -10.5k and "(DS3_RISK_OFF_FINAL)": sign reads as a cost anyway. L.
13. Section 7 INST-2 "inside MDE" (MDE 2.48k printed) and "Shadow only." trailer (heading says Shadow only): no.
14. Section 8 "(FORWARD_SHADOW_RUNBOOK ...)" source - no. "Honoured from 14:30Z" -> "Honoured": no.
15. Section 9 Q1 wording order, Q9 default changed to "D6 owner supplies" - consistent with Appendix.
16. Cite names (PERSISTENCE, REGIME_STRESS, NO_TRADE_C_D, ER_SIZER_ROBUSTNESS, RECENT_EDGE_6, ALT_BAR_IDENTITY, TAPE_DEDUP, D7_FILTERS): the reader loses the pointers, no number changes. L (one-line "report names drop DS3_" is in the header, but the report names themselves are gone in hazards 1, 3, 4, 6).

New overclaims or lost caveats introduced by the trim:
- N1 (L-M): the brief gives the ON set only at C1 and C2 12R. The multiple is unknown (Q1). ON set by multiple (ON_SET T1, L6M / PRE): 12R -5.4 / -8.9; 20R -1.7 / -4.6; 30R +0.5 / -0.2 (30R = C1, 0 of 28 fires in L6M). Without it the reader cannot see that "turns negative" depends on the multiple. d4 had no more, so not new, but the trim could have afforded one row.
- N2 (L-M): hazard 2 table (l25-27) "PRE" row is the six-piece composite (8R -6.9 ... 30R -2.5), not the ON set (12R -8.9, 20R -4.6, 30R -0.2). The row follows "Costs the six-piece 8.9" but the table header does not say six-piece, and section 1 is about the ON set. Label it.
- N3 (see 7 above).
- No new "clears MDE", "PASS" or "confirmed" claim anywhere. "Nothing here is a PASS" present. The word CONFIRMED-RECENT appears once, negated (l65).
- "no set has a PRE tail advantage" (l41, at 12R) is true to rounding (ON+ER PRE w20 -577 vs -585 is 8k lighter, noise). OK.
- Appendix A row 92 cites "brief draft 4 / ON-1" as the source for "A6 at market": circular (the brief is the source). Fix with the section 4 text.

## 4. A6 market vs the group-05 split: are the ON-set numbers valid for live D6?

Facts:
- Brief l5: "70/30 split on the five split books, A6 at market per ON-1".
- FORWARD_SHADOW_SPEC REG-1: "Split % is ONE panel setting (group 05) for all gated books: K6 keeps the split ... D6 does not read THP entry lines". So live D6 cannot hold A6 at market and the others at 70/30 without a code change (per-book split).
- THP_POLICY.txt has no A6 market line. Explicit market lines exist for P6, N6, MA6, CR only. For A6 the THP says "POOLED SPLIT on this book ... (= the default line applies)" (research lots L6M +3.4k (7.0k)). THP therefore splits A6.
- DS3_ON_SET prices A6 as market in every set ("A6 is market in every set and is identical to the as-is except for the stop parity (book delta 0.0)"). The A6 book delta is +0.0 (0.0) in all five windows in the ON set and ON+ER (Table 6). At 12R it is -0.1 L6M. In the six-piece A6 is +0.9 (1.5) from the other pieces, not from a split. No report prices A6 split.
- A6 has 1 lot (Asia). 70/30 of 1 lot: with D6's half-up min-1 rule on the market leg, Max(1, Floor(1 x 0.7 + 0.5)) = 1, and a remainder of 0, so the order is 1 lot at market. That equals ON-1's A6. But D6's rounding of the split is not specified (SUNDAY_DECISION l.321, "D6's rounding of 70% of a sized lot count is not specified"; K6 2 lots = 1/1 is the only documented case). Other readings: min-1 on both legs gives 1 market + 1 resting = 2 lots (A6 exposure doubles); Floor on the market leg gives 0 market + 1 resting dip order (A6 becomes a 3 pt dip-limit entry with confirmation).

Verdict on the numbers: valid for live D6 if and only if D6 turns 1 lot at 70/30 into 1 market lot and no resting leg. This is plausible, not verified. If so the ON-set numbers apply unchanged (A6 contribution 0.0 either way, which is what the lead flagged). If D6 produces a second lot or a resting-only entry, the A6 line is unpriced; its size is bounded only by A6's own book scale (A6 book MDE 1.5 L6M, 0.7 at 12R; six-piece A6 +0.9), small against the ON-set MDE 9.8 and does not change "about nothing", but it is a different trade, not a rounding. The combined week lock uses K6's R so it is not touched; A6's own day and week locks are.

What the brief should say (replace "A6 at market per ON-1" in l5, and Appendix row 92):
"ON-1 prices A6 at market (A6 delta 0.0 by construction). Live D6 has one split setting (group 05) for all gated books, so A6 splits too. A6 is 1 lot: if D6 rounds 70% of 1 lot to 1 market lot and no resting leg, A6 stays at market and the ON-set numbers hold; D6's rounding is unspecified and nothing prices A6 split (A6 book MDE 1.5). D6 owner to confirm the 1-lot split result before 18:00 ET; THP's default line also splits A6." Add Q10: "D6 split rounding for 1-lot A6 [expect 1 market / 0 resting; confirm in the D6 test]". Appendix row 92 source should be SPEC l.13 + THP default line, not the brief.

## 5. Verdict

SAFE TO READ as the Sunday brief after three small required edits. No number is wrong; no H finding is open; every H from v6 and v6d3 is closed.

Required edits (all text, no re-run):
1. A6 line (section 4 above): rewrite l5 "A6 at market per ON-1", fix Appendix row 92 source, add the Q10 on 1-lot split rounding.
2. Hazard 2 (l25-27): label the PRE row "six-piece composite, PRE vs unlocked as-is" and add ON set by multiple (L6M / PRE: 12R -5.4 / -8.9, 20R -1.7 / -4.6, 30R +0.5 / -0.2) because the multiple is unknown.
3. Hazard 5 (l30): restore the instruction "use `identity_target` for 20260202 in the identity CSVs, not library rows"; Q7 [yes, after Sunday]; l67 interim time "11:00Z" vs the directive's "12:00Z" (fix or state the basis).

Optional (L): restore "mix" in the 2023-24 comparison; "tail benefit" wording in l41; state that the live-lot NY-PM range -0.1..+0.1k is the stack alone (as an add-on to the composite -0.27..+0.28k); ON-set lock-off PRE cell (maxDD 114 vs 162, w20 -737 vs -811) and 12R rows for ON / ON+ER; -18.6k with MDE 43.0k; halt MDE 16.3k; effective N 47 and 41% / 33% in SIXTY; P6 line "-0.3 split, +6.8 sizer".

Re-run triggers: an answer to Q1-Q3, or the D6 1-lot split result for A6.
