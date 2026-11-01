# DS3_SUNDAY_BRIEF_AUDIT_v8 (BA-8, independent; brief not edited)
Audited: autopilot/DS3_SUNDAY_BRIEF.md (v8, byte-identical to DS3_SUNDAY_BRIEF_v8_1227Z.md, 259 lines). Diffed against DS3_SUNDAY_BRIEF_v7e2_1226Z.md. Sources opened: DS3_DD_REREAD_A11.md, DS3_ORB_RSI2_COMPLETE.md (A12), DS3_DD_REREAD_A9.md (key rows), DS3_L2_CLUSTERS.md (A10). Line numbers = lines of DS3_SUNDAY_BRIEF.md.

## VERDICT: SHIP AFTER EDITS
No wrong A11/A12 headline number found. The fold is numerically clean. But one composite-frame statement is now contradicted by A11 (F1), one sentence is unscoped (F2), one sentence misdescribes A9's 387 (F3), and the A12 Shadow rows lost caveats that the source carries (F6, F7). All are one-line edits. No PASS/proven/safe wording. Nothing reads as a recommendation except the mild Q16 "best-supported" (F12).

## Findings
| # | Sev | Line | Source | Issue | Fix |
|---|---|---|---|---|---|
| F1 | High | 91 | A11 sec 2 table, composite row: 27,960 series, RISK-KEEP 10, size-cut 10, WY p<=0.05 **2**, FINAL 0 | Row "survive a family-wise correction" says "composite frame: none (A3 1.00, A2 1, Fed 0.10, A9 0.075 / 0.085)". After A11, 2 composite-frame cells DO pass family-wise p<=0.05 (both deepen HOLD maxDD 19-20%, so 0 FINAL). A9's 0.075/0.085 are superseded by the complete-family WY. Line 92 states this correctly, so lines 91 and 92 contradict each other. Same flat "none survives" wording is at 39 (scoped to "composite frame" but not to FINAL). | Line 91 composite cell: "composite frame: none of the A1-A4 rows (A3 adj p 1.00, A2 Sidak 1, Fed 0.10); A11: 2 cells reach p<=0.05 and both deepen HOLD maxDD 19-20%, so 0 pass the full test". Line 39: "none survives all tests in the composite frame". |
| F2 | Med | 39 (col 2) | A11 sec 2: as-is 1,887 pass WY p<=0.05 | Plain sentence "no RISK-KEEP survives a family-wise correction" is unscoped, yet the same row (col 3) and lines 47, 89, 91 say 1,887 as-is series pass it. Reader gets two answers in one row. This is the composite-frame scoping item you asked about: it is scoped in col 3 and line 93 but not in the plain sentence. | "no RISK-KEEP survives a family-wise correction in the composite frame (as-is frame: see the number)". |
| F3 | Med | 47, 89 | A11 sec 1: the four A9 sampling ESTIMATES (2,575 / 2,402 / 930 / 12,505) lie inside their 95% intervals; 387 is a count of a sample, 1,097 is the exact count | "A9's sampled 387 was inside the intervals" is wrong: 387 is not an estimate and is not inside any interval (exact FINAL is 1,097; A9's L2SP FINAL estimate 930 vs exact 983 is the inside case). Line 89 "inside the 95% intervals" repeats it. | "A9's L2SP sampling estimates (e.g. FINAL 930 [767,1132] vs exact 983) fell inside their intervals; the 387 was a sample count, not an estimate". |
| F4 | Low-Med | 39, 93 | A11 sec 3: union 22 clusters; "NEW independent clusters" = 2 (5 series); A11 text itself says "22 versus 19: +2" | "22 clusters = two ideas plus the p70 take and 3 small clusters" / "3 more small clusters": the source supports 2 new clusters (5 series). 22-19=3 arithmetically but A11 attributes +2 to new and the 3rd to re-clustering; "3 small clusters" is the writer's own gloss. Line 48 already says 2 with no A10 member (5 series). | Use "22 clusters (2 new, 5 series, each just under the 0.7 line)". Also note A11 itself is inconsistent (19+2 vs 22); do not claim more than the source. |
| F5 | Med | 2 | A12 header (line 3 of source): "Composite L6M maxDD (23k) is the single week 2026-01-19"; A9/A11: as-is 88k = 2026-01-19 | Changelog says "later sources and this brief say 2025-10-20" for the composite's L6M maxDD week. A12 (08:14Z, later than the DD_REREAD merge) prints 2026-01-19 for the COMPOSITE. So not all later sources agree; A12's wording is likely the same slip as the merge. Brief body (lines 66, 84) says composite = 2025-10-20, as-is = 2026-01-19. | Changelog: "DD_REREAD merge and A12 print 2026-01-19 for the composite's L6M maxDD week; the brief uses 2025-10-20 (composite) and 2026-01-19 (as-is)". Do not edit sources. |
| F6 | Med | 106 | A12 BL 2: ES 0.990 PRE+X', **0.875 X' alone**, 0.980 PRE; NQ 0.950 (D1 0.945; re-derived excluding roll pairs); NQ fees are PROXIES, every NQ result capped CANDIDATE; ES held CANDIDATE | ES row gives only the favourable pooled 0.990. X' alone fails the 0.95 bar. NQ 0.950 sits exactly on the bar after a re-derivation moved it up from 0.945. Fee-proxy CANDIDATE ceiling dropped. | Append: "(X' alone 0.875; NQ 0.950 = on the bar, D1 0.945; NQ fees are proxies: ceiling CANDIDATE; post-hoc)". |
| F7 | Med | 107 | A12 sec 1 tiers: IBS 4.2 lots no lock = PRE/X-CUT-ONLY; 12R/20R/30R = NO (R2); R1 (blind) 12R yes, 20R/30R no | Row has the numbers but no source verdict, and its lead clause ("the only sleeve whose PRE 36% / X' 34% cuts beat the placebo with no lock") reads as a plus. Your rule: Shadow rows carry source verdicts. Also does not say the 20R/30R "35%" X' cut comes with PRE 16%/12% (<20%, so NO). | Add "verdict: 0 full RISK-KEEP; NO at every lock when the sleeve is inside the lock (R2); the cut exists only unlocked/blind". |
| F8 | Low | 49, 105 | A12 sec 1, ORB rows | "ORB 17.2 lots, 12R lock: X' 121 -> 323k" sits beside a 1-lot paper Shadow row. At 1 lot ORB moves nothing (X' 121->121 no lock, 120->121 at 12R). Reader may think the Shadow size is 17.2 lots. | Add "(17.2 lots = half-SD sizing, not the Shadow size; at 1 lot no effect)". |
| F9 | Low | 49, 105 | A12 table: 12R base is 120, not 121 (no-lock base 121); 20R 316 | "121 -> 323" mixes the no-lock base with the 12R result. MORNING already notes the 120 vs 121 slip. | "120 -> 323k at 12R (121 unlocked)". |
| F10 | Low | 206, 229-232 | n/a | "OPEN QUESTIONS (24)" includes Q21 which is closed ("done"), so 23 are open; order is 21, 24, 22, 23. Q21 default/why are fine ("closed; no extrapolation left"). | Reorder 22, 23, 24 or write "(24; Q21 closed)". |
| F11 | Low | 230 | A12 BL 3; MORNING 07:30 | Q24 "three cells ... 9,590 trades, ~6 h at 3 workers": MORNING 07:30 attributes 9,590 rows/~6 h to TB4W_10 and TR3_DON15_S only; TB4A is 2% covered ("effectively mapped"). A12 line 8 applies 9,590 to all three. Source ambiguity. "Why" is a consequence, not a why-it-matters. | "TB4W_10 + TR3_DON15_S (9,590 rows per MORNING; TB4A has 2% coverage); governor is your 2026-10-27 ruling". |
| F12 | Low | 224 | A12: 0 of 656 RISK-KEEP; value gone under lock | Q16 "best-supported unbuilt rows" is a mild recommendation and predates the A12 caveat. Default "yes" (free paper log) is fine. | "free paper log; A12: no drawdown value once the lock sees them". |
| F13 | Low | 47, 89 | A11 sec 7: RISK-KEEP series stack volume touched median 17% (1-38%); A11 text and A9: ~21% | "~21%" appears, but A11's own table says 17%. Source-internal. | "about a fifth (17-21% depending on set)". Also add "(22 clusters)" after 1,097 on lines 47 and 89 so the number never appears alone there. |
| F14 | Low | 49 | A12 BL 3 | Brief says "three program cells stay MAPPED" but omits that the other two (PB7) were run direct and direct recent means are far below mapped (L3M $834 vs 1,211; $230 vs 1,238). | Add "two PB7 cells ran direct: direct means well below mapped". |
| F15 | Low | 110 | A10 sec 5 | Cluster 11 row: "decision read at 104 weeks" without the cost: 104 weeks = about 2028-11 if t0 is 2026-11-23, and a maxDD cut is not readable at 80% power even at 416 weeks (power 63% at 104). | Add "~2 years; maxDD cut not readable at 80% power inside 416 wk". |

## Checked correct (counts)
A11 / L2SP (all verified against A11 sec 1-3):
- 23,772 eligible L2SP cells all run; 21,081 run by A11; 42,162 = 21,081 x 2 frames (derived; A11 says one row per cell and frame): 3 of 3.
- All-families as-is funnel 2,872 -> 2,720 -> 1,887 -> 1,097, strict 545: 5 of 5, in lines 47 and 89 (both agree; line 89 and 91 agree).
- By program 180 / 903 / 14 = 1,097: 3 of 3. Composite 10 / 10 / 2 / 0 / 0 (series), L2SP 10 cells (9 distinct): 5 of 5 + 2.
- "Both p survivors deepen HOLD maxDD 19-20%": correct.
- A10 re-cluster 19; 710 new; 690 join (396 into cluster 11); 20 join none (p70never/thickonly, avg rho 0.61-0.69); union 22; 2 clusters with no A10 member, 5 series; effective N 3.4: 8 of 8.
- Exact L2SP counts (2,693 / 2,466 / 1,576 / 983 / 903) are not printed in the brief (only 903 and 1,097); the A9 estimates (2,575 / 2,402 / 930 / 12,505) are not printed: no stale value. Greps: '2,575' 0 hits, 'pending' 0, '~7 h' 0, '944/707/920' 0, 'xtrapol' 1 (line 229, "no extrapolation left"), 'full L2SP' 0 stale. '387' appears 4 times (lines 47, 48, 89, 93), all as A9/A10's historical count and each contextualized (F3 aside).
- A10: 387 series, 19 clusters, effective N 3.4, rho 0.83-0.93 with p70 take, cluster 11 = 141 series, "L2 filter adds ~0", one primary cluster, interim looks 13/26 weeks, decision 104: 6 of 6.
A12 (all verified against source tables):
- 0 of 656 rows full RISK-KEEP: yes (tiers NO 593 / VOL 31 / L6M-only 24 / PRE-X-cut-only 8).
- ES RSI2_t10 0.990 PRE+X' (F6 for X' alone); NQ RSI2_t10 0.950; bar 0.95.
- NQ IBS 4.2 lots: no lock PRE 241->155 (36%), X' 121->79 (34%); R2: 20R PRE 16% / X' 35%, 30R 12% / 35%, 12R X' 120 -> 142: 6 of 6.
- ORB 17.2 lots 12R X' ->323, 20R 316 (F9 for base); ORB no value at any lot/lock: yes.
- MAPPED cells: TB4A_time_03 (2% coverage), TB4W_10, TR3_DON15_S, labelled MAPPED in lines 49 and 230: 3 of 3; no A12 'MAPPED' cell is described as direct anywhere in the brief.
- PB7 two cells direct: not stated in brief (F14).
Elsewhere:
- Purchases: $773.06 left, none bought, default none, $70.54 first, line 121 "~$811 stale": consistent across lines 113-121 and Q23 (default no). Dollar ledger itself not re-derived.
- Open questions: 24 rows, 24 distinct numbers (1-24), every row has a DEFAULT and a why: 24 of 24 (Q21 closed, F10).
- No PASS/proven/safe wording: 'PASS' hits (lines 2, 54, 189, 191, 193, 223) are all negations or "PASS-tier rows never built" / "0 PASS"; 'safe' only in line 84 ("not safe"); 'proven'/'proves' 0.
- Shadow list: 9 rows, each carries a source verdict and a stop/monitor rule, none sizes anything; header says "no source recommends sizing any row". F7/F6 are about completeness, not recommendation.
- 1,097 described as two ideas + p70 take, 22 clusters, "still ... none survives in composite frame" at lines 39, 48, 93; never as "1,097 findings" (F2/F13 minor).

## Diff v7e2 -> v8 (every changed or dropped sentence)
Only 8 hunks; lines 4-38, 64-88, 99-103 (switch list etc.) are byte-identical, so the sign legend, weak-placebo caveat ("a near-0% rank means not a volume cut, not safe", line 84; "weak null" line 47), "nothing found tonight goes live Sunday" (lines 4, 36, 99), one-week L6M/PRE caveats (lines 47, 66, 84, 91), frame matters (Q19, line 91), A5 stop-tightening + lock accounting (line 46), and vol-scaler wording (lines 42, 58, 97) are all retained. Hunk list:
1. Line 1 title: "v7e, 12:00Z delivery candidate" -> "v8, FINAL". No caveat.
2. Line 39: A9's 387 / 19 clusters -> A11's 1,097 / 22 clusters "+ 3 small clusters" (F4). Caveat kept (as-is vs composite scoping).
3. Lines 47-48: A9 row replaced by "A9 + A11 (complete)". Dropped: "135 if HOLD cut >= 20%" (replaced by 545), "composite 2 of 10,716, both fail p (0.075, 0.085)" (replaced by 10/10/2/0/0; F1), "median 21%" -> "~21%". Added: 22-cluster union, DEAD_CELLS +42,162, A9 interval sentence (F3). No caveat lost.
4. Line 49 new row ORB_RSI2_COMPLETE (A12): new, caveats "real only without the combined week lock", "ORB none", MAPPED; lost vs source: F6-F9, F14.
5. Line 89 and 91-93: A9-387 content replaced by A11; composite-frame line changed (F1). Added "22 clusters", "A10 + A11" row.
6. Line 105: dropped "deepens the PRE tail" (replaced by "no drawdown value at any lot or lock"); fine, A12 supports it, but see F8.
7. Line 106: dropped "not risk-scored here" (now A12-scored, 0 full RISK-KEEP). Source changed from ORB_ASIA_D7 to A12. Lost: X' 0.875, fee proxy (F6).
8. Line 107: size "~4 NQ" -> "4.2 NQ lots"; source DD_REREAD -> A12; verdict missing (F7).
9. Line 206 and 229-230: (23) -> (24); Q21 "Run the full L2SP sweep (~7 h) | no" -> "done"; new Q24. (F10, F11).
No sentence was dropped from any of the specifically listed caveat categories (sign legend, weak-placebo, tonight-not-Sunday, one-week caveats, frame, composite-frame scoping [see F1/F2], A5 accounting, vol-scaler).

## First screen (lines 1-35)
Risk-first: yes (section 1 title and the "earns about nothing in mean" line precede everything). Switch list ON / SHADOW / OFF: present, sums to the Appendix. Uncertainty table: present (Q1/Q2, Native-stop input, Q10/Q11, shadow reason). Not on first screen: A11/A12 (fine, tonight's items are section 2), purchases (section 5). Unchanged from v7e2, so BA-7's verification stands. One density note: line 2 is a very long header paragraph (tag mapping, lots, changelog); the changelog belongs after the switch list but is not a defect.

## Stale / contradictory cross-section check
- Cluster counts: 19 (A10's 387) and 22 (union) used consistently at 39, 48, 91, 93 (F4 aside).
- Exit-rule counts: 1,097 / 1,887 / 2,872 / 545 consistent at 47, 89, 91, 93.
- A11 composite: lines 47, 92 correct; line 91 stale (F1).
- Q21 done vs section 2 "complete": consistent. No remaining "~2,575", "extrapolated", "pending".
- A12 MAPPED labels: lines 49 and 230 consistent.
- 70% take: line 183/172 vs cluster rho 0.83-0.93: consistent.

## Not verified
$773.06 dollar ledger; "28 MB/day CSV, 6.2 MB/day gz" (comes from MORNING v7d note, not re-checked); L2SP "~21%" vs 17% is a source-internal difference.
