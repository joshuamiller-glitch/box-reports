# R13_INSTALLED_PANEL - the policy file and panel AS INSTALLED, for the Monday acceptance (REDO-R13; PRE-PROOF; first version 2026-11-09 ~22:00Z)
Single source for the engine: outputs/code/th_r13/panel_installed.json (edit there; monday_acceptance.py and r13_engine.py read nothing else). Everything below is labelled KNOWN (user statement or file on the box), DERIVED (from DS7.cs v1.4 / our pages) or ASSUMED (needs the user).

## 1. Known (user statements, DS7.cs v1.4, GATE0_ANSWERS_1106, our pages)
| item | value | source | engine switch |
|--|--|--|--|
| Session clock | 18:00-01:59 asia, 02:00-08:29 london, 08:30-09:29 pre, 09:30-11:59 nyam, 12:00-14:59 nypm, 15:00+ close; blocks 09:00-09:59, 18:00-18:04, no entries 15:00-17:59 | GATE0_ANSWERS s5 | engine default |
| Lot tables (v1.4, blind week) | K7 2,2,0,1,2,0; U7 4,4,0,0,0,0; P7 7,7,0,7,0,0; H7 4,0,0,1,0,0; M7 0,2,0,1,0,0; A7 1,0,0,0,0,0; O7 1 lot | GATE0_ANSWERS s5 | sim.SESS |
| P7 lot table from the user's Monday note | "7/4/4" | user | panel.sess.P7 = "7,4,0,4,0,0" (ASSUMED reading: asia 7, london 4, nyam 4, pre/nypm/close 0 as before) |
| U7 | 4/4 (asia, london) unchanged | R3 text | panel.sess.U7 = "4,4,0,0,0,0" |
| P7 loss cut line before the change | v2: `loss P7 * pct<=-0.7500 pulled_mult>=5 win=5 persist=10 cut` = 45 pts of the 60 stop, 5x MedLevel, 5 s window, persistence 10 s, no newMae (DS3_P7_CUT.md s10) | our page | panel.cut_lines.P7 |
| P7 loss cut line from 2026-11-09 20:30Z | 40 / 5x / w5 / p3 (noMae) | user | panel.cut_change (entries from the effective time use it; ASSUMPTION: positions open at 20:30Z keep their line) |
| P7 cut label | RECENT-ONLY under standing rule 2 / 2a (exact L6M stack maxDD -17%, PRE +25% deeper; bi-weekly WF 42% procedure, 54% / 47% fixed cell < 60%, so allowance 15%) | DS3_P7_CUT.md s9-10 | n/a |
| Other books' state cut | per-book S1b-COMB cells (K7 45/10x/w2/p3 V2; M7 30/10/2/2; U7 30/60/15/5 V2; A7 30/60/15/3; H7 15/30/10/2 newMae V1; O7 25/20/10/10) | TH_STATE_BASE_S1B.md s2 | cut_base S1-COMB |
| State cut mechanics | 1-s top-10 states, cancelled net of trades, EWMA 0.001 MedLevel, decision latency 1 s, market exit 0.80 pt | DIRECTIVE_TH_L2_S_20261108 | engine |
| Brackets | all sliced books stop 60 / target 60 from the fill average (target re-based after the add); O7 40/90, 1 lot, time exit 16:00; native stop-market 80 catastrophe beside the strategy-worked 60 (code reading, open question in MORNING_FLAGS 11-07) | GATE0_ANSWERS s3 | sim.STOPPTS / TARGETR; panel.stop_pts / target_r empty = live 60/60 |
| Stop exit mode | K7 and H7 JoinThenMarket (3 s), P7/U7/M7/A7/O7 Native | GATE0_ANSWERS s3 (our engine code JOIN_BOOKS = K7 M7 U7 P7: DISAGREES, see 3) | engine |
| Locks | day caps +5R/-2R, give-back arm +2R keep 50%, week floor -12R per book, PerBook | GATE0_ANSWERS s3 | engine |
| Bug exits | the 10 v1.5 state cuts of the night 11-08/09 (1 H7 + 9 M7): ES/RTY depth pollution, fixed in v1.5a | user | panel.bug_* (window 11-08 18:00 .. 11-09 09:00 ET, books H7/M7, cut exit names: ASSUMED window) |

## 2. Derived / adopted in the engine run
- Seven state-cut lines read as ONE LINE PER BOOK (K7 P7 M7 U7 A7 H7 O7): S1-COMB's two session overrides (P7 asia 50/5/3/3 newMae, H7 nyam 35/20/2/1) are NOT lines in the policy file as far as we know, so panel.drop_session_overrides = true replaces them by the book's own cell. ASSUMED.
- Settled configuration for a new week: PERIODS off, X books off (HIST_PRM). If X1-X5 are installed live this week they are not in the engine run: their live rows are listed as class A (they cannot be reproduced) unless the user sends the X parameter string (open since 11-07).
- Bar close = tick (F1), TrendSize half-even rounding inert after Mon 13:30 ET (ENTRY_MATCH F2).

## 3. What we need from the user (put in MORNING_FLAGS.md; none blocks the run, each changes the match)
1. The installed bracket retargets per book x session (stop / target / lotmult lines); the run uses live 60/60 (O7 40/90) until told.
2. The installed policy file text (all lines, with `win=`, `persist=`, `armusd=` fields) and its mtimes, or confirm: seven state-cut lines = one per book with the S1b-COMB cells; P7 line v2 -> 40/5x/w5/p3 at 20:30Z.
3. The installed P7 lot-table string (six numbers) and any other table change since 11-05 (K7, U7, M7, H7, A7).
4. Stop exit mode per book as installed (our code reading: JoinThenMarket on K7, M7, U7, P7; the user's answer: K7 and H7 only).
5. The exact time of the v1.5a fix (ES/RTY depth pollution) and the list of the 10 bug exits (book + exit time), so the exclusion is a list, not a window rule.
6. DS7.cs v1.5 / v1.5a source (only v1.4 is on the box): the three v1.5 fidelity items (level inside/better than the visible range, one row per session second, newMae ties) are the engine's reading, not verified.
7. The live CSV every Monday with the preceding Sunday 18:00 ET start; and the NQ mbp-10 tape for the week (pull decision) so the engine can run (see 4).

## 4. Data on the box (stated 2026-11-09 21:10Z)
- data/live/StratTrades_DS7_<acct>.csv: mtime 2026-11-08 22:05Z, last row entryTime 2026-11-06 11:36 ET, last P7 row 2026-11-05 20:28 ET exit; nt8log_latest.txt has no P7 line. **The Monday live CSV (night of 11-08/09 and the week) is NOT on the box**: nothing after 2026-11-05 20:28 ET was read, and the 11-02..11-05 rows of the unfrozen file were reconciled to the frozen reconstruction (all 187 frozen rows are in the unfrozen file with identical qty, entry/exit time, prices, P&L and exit names; 55 further unfrozen rows are after 11-05 11:05 ET or carry entryTime 0001-01-01 and were not read beyond that).
- Tape: hist day files end 2026-10-30; blind-week arrays cover 11-01..11-05; 1-s state arrays end 2026-11-05. For the 11-08 week the engine needs the NQ mbp-10 for 11-06..11-13 (day files + 1-s state days). monday_acceptance.py stops with TAPE_MISSING.txt listing the missing days and the build commands; it does not buy data.

## 5. One command
`python3 -I code/th_r13/monday_acceptance.py --live <csv> --start "2026-11-08 18:00" --end "2026-11-13 17:00" --label W46` (writes /mnt/l2/l2vast/_r13/accept/W46/ACCEPTANCE.md + acceptance.json); regression on the frozen week: see the docstring (identical to runs/u_comb, U_main .719).
