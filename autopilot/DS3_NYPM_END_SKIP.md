# DS3_NYPM_END_SKIP - NY-PM end skip 14:40:00-15:00:00 ET, register spec + per-book table + stack line (agent NP-1, 2026-10-31)

Research only; no live / execution change; UNTOUCHED never read (frames capped at label day 20260206; L3M 20251106.., L6M 20250801.., HOLD 20250701.., PRE 20240201..20250630, X' 20230401..20240131). Clock rule: nothing tuned, the window is the one the user named; edges 14:30 and 14:50 are sensitivity only. Code `l2vast/ds3/code/nypmend/` (stack_run.py, stack_tab.py, sig_table.py, mk_tabs.py, mk_report.py), outputs `l2vast/ds3/out/nypmend/` (stack_lines.csv, per_book_table.csv, placebo_signal.parquet, tabs.md, stack_tabs.md). Engine = `sundaystack2/ss2_lib.py` (tie-out reproduced: live-lot composite with causal running-max locks, fractional 70/30: 42,562 vs as-is 24,018 = +18.5k L6M, as SS-2; the integer composite 46,802 = +22.8k).

## 1. REGISTER SPEC (page 1)

**Name** R10 `NYPM_END_SKIP` (clock block). All books, all sessions, one rule. Decision is a pure function of the signal second t0 (the second the book's signal fires = when the entry would be submitted), US/Eastern wall clock incl. DST.

**Block**: `BLOCK_NYPM_END = 14:40:00 <= t0_ET < 15:00:00` (start inclusive, end exclusive; a signal at 15:00:00.0 is NOT blocked). 20 minutes, every trading day Mon-Fri. (NTE-1's `last20` mask was minute-granular, 14:40..15:00 inclusive of the 15:00 minute; numbers here use the exact seconds window, so they differ slightly from NTE-1's +4,659 / +3,790 / +975 / +1,182 [here +4,098 / +3,299 / +657 / +1,742 alone on the stack, research lots]: the stack sample and stop basis differ too, see section 3.)

**What it blocks (D6 wording)**: "Entry block, NY-PM end: from 14:40:00 to 15:00:00 ET every book (K6 P6 U6 H6 M6 A6 O6, and S6 W6 MA6 where run) evaluates the entry as usual; if the signal time is inside the block the entry is NOT sent, the signal is printed as SKIPPED with reason `NYPM_END_BLOCK` and counts as a signal of the book for the day (it still updates the running-max SizeMult as any signal does, and it does not arm the book's one-position / 30-min-after-loser memory because no trade existed)."

**Open trades**: they CONTINUE. Option A (scored, the recommended spec): block new entries only; stops, targets, trail, day / week locks and the 16:55 ET flatten work as today; a trade opened at 14:39:59 runs on. Option B (NOT scored, listed because the user asked): also flatten at 14:40, i.e. market-close every open position at 14:40:00. It changes P&L of trades that were entered before 14:40 (how many are open at 14:40 was not counted) and that evidence is not in this report; do not read the table below as support for B. Option C (not recommended): block at the ORDER time instead of the signal time - matters only for P6, where the 45-s three-bar confirmation (NY-AM / NY-PM) enters up to a few minutes after the signal; with signal-time blocking a P6 signal at 14:38 may still enter at 14:42. Scored here: signal time (as in NTE-1). A 70/30 add-leg (the 30% dip limit) working at 14:40 is NOT cancelled by the block (the trade already exists); D6 owner to confirm which the code does, the rule says it continues.

**Where it applies at today's live lots**: only books with NY-PM lots can be blocked: K6 (2 lots) and A6 (1 lot). P6 7 (Asia/London/NY-AM), U6 4 (Asia/London), H6 4/2 (Asia/NY-AM), M6 2 (London/NY-AM) take no NY-PM trades, so for them the block is a no-op live. The research books where the effect is positive (P6, U6, H6, S6, W6) are not trading NY-PM at live lots; the books that are (K6, A6) are the negative ones. **At live lots the rule is therefore a small negative or zero, not a gain** (section 3).

**Shadow log** (extra fields on `signals.csv`; no new file): `nypm_end_t0_et` (HH:MM:SS of t0, always logged), `nypm_end_block` (1 if inside the window, else 0, logged for EVERY signal incl. SKIPPED ones from other rules), `nypm_end_taken_live` (1 if the live book took the trade although block=1: the live-vs-register control; 0 expected after D6 carries it), `nypm_end_open_at_1440` (count and lots of this book's positions still open at 14:40:00, from stack_events), and the usual outcome join (`live_pts_ppl` or the tape counterfactual for blocked signals: the counterfactual P&L of a blocked signal is replayed offline from the tape with the book's real stop / target / flatten, per planned lot, so the register scores "skipped P&L" without any live fill). Scorer weekly line (Monday MORNING.md, HM forward-register slot): `SHADOW NYPM_END n=../wk blocked; skipped P&L pts/planned lot +x.xx (se), per contract; stack $/wk live-lots, research-lots; by book K6 P6 U6 H6 M6 A6 S6 W6 MA6; status TOO EARLY (<W weeks)`. Audit: block flag recomputed from t0 by the scorer must match the log (mismatch < 0.5%, else the week is void); fire rate must be within 0.5-2x the research (research: 3.8 blocked signals per week for the six live-tag books, 6.3 per week for all ten books in L6M; at live lots only K6 + A6, about 1.25 per week).

**Readiness**: needs only the signal timestamp D6 already prints; ready for the register from the first Sunday-night signal. **Evidence class**: section 4. ON is the user's decision.

### The one table: per-book, skip 14:40:00-15:00:00 ET (gain = what skipping adds; + = the skip helps). Signal-level, basis N, 6 live-tag books + research books; window = L3M / L6M / HOLD / PRE / X'. Full tables (both bases, all windows, live lots with D6 rounding, per contract, kept/skipped) in section 2.

| book (research tag) | sig/wk in window (L6M) | skipped P&L per signal / per contract, pts (L6M) | gain of skipping $/wk, research lots, MKT: L3M / L6M / HOLD / PRE / X' | same, 70/30 base: L6M / HOLD | live lots, ER half-up min-1: $/wk L6M / HOLD | placebo rank L6M (random NY-PM 20-min windows; MKT / 70-30) |
|--|--|--|--|--|--|--|
| K6 (KB) | 0.68 | +8.32 / +8.32 | -166 / -587 / -639 / +234 / +427 | -567 / -631 | -240 / -309 | 0.43 / 0.40 |
| P6 (PE) | 1.07 | -16.67 / -16.67 | +3,083 / +2,000 / +1,541 / +184 / -20 | +1,674 / +1,252 | +0 / +0 | 1.00 / 0.99 |
| U6 (SM) | 0.14 | -10.37 / -10.37 | +1,070 / +227 / +192 / +245 / +465 | +212 / +179 | +0 / +0 | 0.69 / 0.69 |
| H6 (HM) | 0.68 | -8.61 / -8.61 | +64 / +1,169 / +930 / -331 / -146 | +1,211 / +960 | +0 / +0 | 0.82 / 0.82 |
| M6 (MV) | 0.68 | +3.89 / +3.89 | +982 / -527 / -379 / +375 / +2,678 | -336 / -235 | +0 / +0 | 0.26 / 0.32 |
| A6 (PB) | 0.57 | +9.19 / +9.19 | -815 / -1,051 / -804 / -269 / +73 | -998 / -762 | -177 / -132 | 0.32 / 0.32 |
| S6 (ST) | 0.75 | -6.26 / -6.26 | +2,121 / +939 / +285 / -255 / +1,400 | +236 / -344 | +0 / +0 | 0.72 / 0.61 |
| W6 (WT) | 0.96 | -0.38 / -0.38 | +474 / +52 / +157 / +325 / -422 | +31 / +133 | +0 / +0 | 0.47 / 0.48 |
| MA6 (MA) | 0.43 | +29.51 / +29.51 | -2,497 / -2,529 / -2,290 / -1 / -688 | -3,359 / -2,905 | +0 / +0 | 0.12 / 0.06 |
| ALL6 (ALL6) | 3.82 | -3.05 / -3.05 | +4,219 / +1,223 / +841 / +436 / +3,476 | +1,189 / +764 | -417 / -441 | 0.58 / 0.57 |

*Reading*: P6 U6 H6 S6 W6 are positive in L6M and HOLD on the market base at research lots (P6 the largest); K6 A6 MA6 M6 are negative. Per signal the skipped trades are not clearly worse than the kept ones on every book (the pooled ALL6 skipped P&L is only -3.05 pts per signal in L6M against +2.92 for all signals): the stack gain is a composition effect of which books fire into the close. At today's live lots the rule is ~ -417 $/wk L6M on the signal level (K6 and A6 only).

### Stack line, skip 14:40-15:00 (block by signal second), delta $/wk, N basis, running-max locks, integer lots. MDE = 2.8 SE of the paired weekly delta

* **Alone on the stack as it is** (market entries, no rules, join stop 2.45), research lots: L6M +4,098 (MDE 4,054) ; HOLD +3,299 (MDE 3,723) ; PRE +657 (MDE 2,841) ; X' +1,742 (MDE 4,089). live + S6 W6 at research/2.35: L6M +626 (MDE 1,150) ; HOLD +473 (MDE 1,041) ; PRE +203 (MDE 710) ; X' +508 (MDE 1,078). LIVE lots: L6M +57 (MDE 574) ; HOLD -25 (MDE 545) ; PRE -72 (MDE 369) ; X' +120 (MDE 507).
* **As an add-on to the Sunday composite (integer lots, ER half-up min 1, A6 market, add slip 0.25, running-max locks, stop 1.28)**: LIVE lots: L6M -144 (MDE 935) ; HOLD -148 (MDE 824) ; PRE -266 (MDE 462) ; X' +284 (MDE 707). Live + S6 W6: L6M +423 (MDE 1,890) ; HOLD +53 (MDE 1,840) ; PRE -943 (MDE 1,310) ; X' +150 (MDE 1,669). Research lots: L6M +707 (MDE 4,787) ; HOLD -173 (MDE 4,652) ; PRE -2,481 (MDE 5,014) ; X' +2,885 (MDE 6,120).
* Composite with K6 at market, others 70/30: LIVE L6M -153 (MDE 932) ; HOLD -154 (MDE 821) ; PRE -212 (MDE 449) ; X' +427 (MDE 799).
* **Plain statement**: alone on the old stack at research lots the skip is +4.1k L6M (MDE 4.1k, on the edge), +3.3k HOLD (MDE 3.7k), +0.7k PRE, +1.7k X'; in the Sunday composite the same skip adds only +0.7k L6M, -0.2k HOLD, -2.5k PRE, +2.9k X' at research lots (all inside MDE) and about -0.1k L6M at live lots: the composite already removes most of what the skip removes (the zone skip and the ER sizer touch the same late signals), and at live lots only K6 and A6 trade NY-PM. **Recommendation for D6: do not add the block to the Sunday composite; carry it as a switchable clock block that ships OFF and run it in the shadow register.** Risk lines (weekly mean, SD, maxDD, worst-20) with / without are in section 3.


## 2. Per-book tables, placebo and sensitivity (full)

#### Per-book table, base MKT, skip 14:40:00-15:00:00 ET (gain = what skipping adds; + means skip helps). Signal-level, N basis (no target-fill correction), pts per planned lot, $ at research lots / live lots / live lots with ER half-up min-1

| book | window | wks | sig/wk in window | skipped P&L pts/wk | kept P&L pts/wk | per signal (skipped) | per contract (skipped) | gain $/wk res lots (SE) | gain $/wk live lots | gain $/wk live ER-rounded |
|--|--|--|--|--|--|--|--|--|--|--|
| K6 | L3M | 14 | 0.71 | +1.6 | -90.1 | +2.23 | +2.23 | -166 (838) | -64 | -120 |
| K6 | L6M | 28 | 0.68 | +5.6 | +68.7 | +8.32 | +8.32 | -587 (689) | -226 | -240 |
| K6 | HOLD | 32 | 0.72 | +6.1 | +37.9 | +8.55 | +8.55 | -639 (638) | -246 | -309 |
| K6 | PRE | 75 | 0.80 | -2.2 | +108.2 | -2.81 | -2.81 | +234 (543) | +90 | -143 |
| K6 | X' | 44 | 0.73 | -4.1 | -11.7 | -5.65 | -5.65 | +427 (585) | +164 | +234 |
| P6 | L3M | 14 | 1.43 | -27.5 | -76.6 | -19.27 | -19.27 | +3,083 (1,399) | +0 | +0 |
| P6 | L6M | 28 | 1.07 | -17.9 | +46.1 | -16.67 | -16.67 | +2,000 (876) | +0 | +0 |
| P6 | HOLD | 32 | 0.97 | -13.8 | +47.0 | -14.21 | -14.21 | +1,541 (816) | +0 | +0 |
| P6 | PRE | 75 | 0.96 | -1.6 | +18.1 | -1.71 | -1.71 | +184 (589) | +0 | +0 |
| P6 | X' | 44 | 0.66 | +0.2 | +30.7 | +0.28 | +0.28 | -20 (547) | +0 | +0 |
| U6 | L3M | 14 | 0.21 | -7.2 | +25.2 | -33.74 | -33.74 | +1,070 (693) | +0 | +0 |
| U6 | L6M | 28 | 0.14 | -1.5 | +27.9 | -10.37 | -10.37 | +227 (507) | +0 | +0 |
| U6 | HOLD | 32 | 0.12 | -1.3 | +43.4 | -10.37 | -10.37 | +192 (427) | +0 | +0 |
| U6 | PRE | 75 | 0.12 | -1.7 | +46.5 | -13.77 | -13.77 | +245 (298) | +0 | +0 |
| U6 | X' | 44 | 0.23 | -3.1 | +16.4 | -13.82 | -13.82 | +465 (396) | +0 | +0 |
| H6 | L3M | 14 | 0.43 | -0.3 | +102.1 | -0.75 | -0.75 | +64 (1,794) | +0 | +0 |
| H6 | L6M | 28 | 0.68 | -5.8 | +159.7 | -8.61 | -8.61 | +1,169 (1,293) | +0 | +0 |
| H6 | HOLD | 32 | 0.62 | -4.7 | +120.1 | -7.44 | -7.44 | +930 (1,138) | +0 | +0 |
| H6 | PRE | 75 | 0.61 | +1.7 | +52.7 | +2.70 | +2.70 | -331 (1,009) | +0 | +0 |
| H6 | X' | 44 | 0.48 | +0.7 | +12.7 | +1.53 | +1.53 | -146 (806) | +0 | +0 |
| M6 | L3M | 14 | 0.79 | -4.9 | +111.9 | -6.25 | -6.25 | +982 (2,980) | +0 | +0 |
| M6 | L6M | 28 | 0.68 | +2.6 | +89.5 | +3.89 | +3.89 | -527 (1,766) | +0 | +0 |
| M6 | HOLD | 32 | 0.78 | +1.9 | +57.1 | +2.43 | +2.43 | -379 (1,643) | +0 | +0 |
| M6 | PRE | 75 | 0.68 | -1.9 | +88.5 | -2.75 | -2.75 | +375 (976) | +0 | +0 |
| M6 | X' | 44 | 0.52 | -13.4 | -55.6 | -25.61 | -25.61 | +2,678 (947) | +0 | +0 |
| A6 | L3M | 14 | 0.71 | +4.1 | +227.3 | +5.70 | +5.70 | -815 (2,009) | -81 | -79 |
| A6 | L6M | 28 | 0.57 | +5.3 | +210.7 | +9.19 | +9.19 | -1,051 (1,273) | -105 | -177 |
| A6 | HOLD | 32 | 0.53 | +4.0 | +162.1 | +7.57 | +7.57 | -804 (1,122) | -80 | -132 |
| A6 | PRE | 75 | 0.67 | +1.3 | -6.6 | +2.02 | +2.02 | -269 (961) | -27 | -2 |
| A6 | X' | 44 | 0.52 | -0.4 | +33.5 | -0.70 | -0.70 | +73 (995) | +7 | +45 |
| S6 | L3M | 14 | 0.79 | -10.6 | +136.7 | -13.50 | -13.50 | +2,121 (2,269) | +0 | +0 |
| S6 | L6M | 28 | 0.75 | -4.7 | +179.6 | -6.26 | -6.26 | +939 (1,580) | +0 | +0 |
| S6 | HOLD | 32 | 0.75 | -1.4 | +131.6 | -1.90 | -1.90 | +285 (1,525) | +0 | +0 |
| S6 | PRE | 75 | 0.83 | +1.3 | +70.7 | +1.54 | +1.54 | -255 (1,038) | +0 | +0 |
| S6 | X' | 44 | 0.73 | -7.0 | +30.7 | -9.62 | -9.62 | +1,400 (1,052) | +0 | +0 |
| W6 | L3M | 14 | 1.21 | -3.4 | +102.5 | -2.79 | -2.79 | +474 (1,558) | +0 | +0 |
| W6 | L6M | 28 | 0.96 | -0.4 | +108.9 | -0.38 | -0.38 | +52 (848) | +0 | +0 |
| W6 | HOLD | 32 | 0.97 | -1.1 | +71.6 | -1.16 | -1.16 | +157 (872) | +0 | +0 |
| W6 | PRE | 75 | 1.17 | -2.3 | +34.7 | -1.98 | -1.98 | +325 (633) | +0 | +0 |
| W6 | X' | 44 | 1.00 | +3.0 | +24.0 | +3.01 | +3.01 | -422 (659) | +0 | +0 |
| MA6 | L3M | 14 | 0.64 | +12.5 | +124.1 | +19.42 | +19.42 | -2,497 (3,137) | +0 | +0 |
| MA6 | L6M | 28 | 0.43 | +12.6 | +85.8 | +29.51 | +29.51 | -2,529 (1,678) | +0 | +0 |
| MA6 | HOLD | 32 | 0.44 | +11.4 | +68.8 | +26.17 | +26.17 | -2,290 (1,546) | +0 | +0 |
| MA6 | PRE | 75 | 0.37 | +0.0 | +37.4 | +0.01 | +0.01 | -1 (766) | +0 | +0 |
| MA6 | X' | 44 | 0.30 | +3.4 | +21.1 | +11.64 | +11.64 | -688 (895) | +0 | +0 |
| DN | L3M | 14 | 0.29 | -7.2 | +155.6 | -25.06 | -25.06 | +1,432 (1,608) | +0 | +0 |
| DN | L6M | 28 | 0.32 | +0.4 | +155.8 | +1.23 | +1.23 | -79 (1,351) | +0 | +0 |
| DN | HOLD | 32 | 0.31 | +2.2 | +119.0 | +7.08 | +7.08 | -443 (1,236) | +0 | +0 |
| DN | PRE | 75 | 0.25 | +0.8 | +98.5 | +3.12 | +3.12 | -158 (717) | +0 | +0 |
| DN | X' | 44 | 0.43 | -7.7 | +14.9 | -17.80 | -17.80 | +1,537 (966) | +0 | +0 |
| ALL6 | L3M | 14 | 4.29 | -34.3 | +299.8 | -8.01 | -8.01 | +4,219 (5,294) | -145 | -199 |
| ALL6 | L6M | 28 | 3.82 | -11.6 | +602.5 | -3.05 | -3.05 | +1,223 (3,302) | -331 | -417 |
| ALL6 | HOLD | 32 | 3.75 | -7.6 | +467.6 | -2.04 | -2.04 | +841 (3,005) | -326 | -441 |
| ALL6 | PRE | 75 | 3.84 | -4.4 | +307.4 | -1.15 | -1.15 | +436 (2,301) | +63 | -145 |
| ALL6 | X' | 44 | 3.14 | -20.1 | +26.2 | -6.41 | -6.41 | +3,476 (2,481) | +172 | +279 |

#### Per-book table, base SPL, skip 14:40:00-15:00:00 ET (gain = what skipping adds; + means skip helps). Signal-level, N basis (no target-fill correction), pts per planned lot, $ at research lots / live lots / live lots with ER half-up min-1

| book | window | wks | sig/wk in window | skipped P&L pts/wk | kept P&L pts/wk | per signal (skipped) | per contract (skipped) | gain $/wk res lots (SE) | gain $/wk live lots | gain $/wk live ER-rounded |
|--|--|--|--|--|--|--|--|--|--|--|
| K6 | L3M | 14 | 0.71 | +0.7 | -96.8 | +0.98 | +1.00 | -73 (775) | -28 | -109 |
| K6 | L6M | 28 | 0.68 | +5.5 | +54.4 | +8.04 | +8.03 | -567 (677) | -218 | -242 |
| K6 | HOLD | 32 | 0.72 | +6.1 | +26.6 | +8.44 | +8.41 | -631 (629) | -243 | -314 |
| K6 | PRE | 75 | 0.80 | -2.1 | +105.5 | -2.64 | -2.64 | +220 (548) | +84 | -145 |
| K6 | X' | 44 | 0.73 | -4.0 | -11.8 | -5.52 | -5.48 | +418 (591) | +161 | +224 |
| P6 | L3M | 14 | 1.43 | -30.9 | -69.1 | -21.62 | -22.20 | +3,459 (1,464) | +0 | +0 |
| P6 | L6M | 28 | 1.07 | -14.9 | +49.1 | -13.95 | -14.11 | +1,674 (952) | +0 | +0 |
| P6 | HOLD | 32 | 0.97 | -11.2 | +48.9 | -11.54 | -11.67 | +1,252 (875) | +0 | +0 |
| P6 | PRE | 75 | 0.96 | +0.4 | +19.7 | +0.46 | +0.45 | -49 (646) | +0 | +0 |
| P6 | X' | 44 | 0.66 | +0.7 | +31.4 | +1.10 | +1.08 | -81 (554) | +0 | +0 |
| U6 | L3M | 14 | 0.21 | -7.1 | +28.9 | -33.27 | -32.72 | +1,055 (691) | +0 | +0 |
| U6 | L6M | 28 | 0.14 | -1.4 | +37.7 | -9.65 | -9.47 | +212 (511) | +0 | +0 |
| U6 | HOLD | 32 | 0.12 | -1.2 | +54.3 | -9.65 | -9.47 | +179 (430) | +0 | +0 |
| U6 | PRE | 75 | 0.12 | -1.8 | +43.2 | -15.24 | -15.50 | +271 (287) | +0 | +0 |
| U6 | X' | 44 | 0.23 | -3.5 | +14.2 | -15.27 | -15.47 | +513 (366) | +0 | +0 |
| H6 | L3M | 14 | 0.43 | -1.5 | +77.0 | -3.44 | -3.55 | +295 (1,830) | +0 | +0 |
| H6 | L6M | 28 | 0.68 | -6.1 | +146.2 | -8.93 | -8.91 | +1,211 (1,307) | +0 | +0 |
| H6 | HOLD | 32 | 0.62 | -4.8 | +112.0 | -7.68 | -7.66 | +960 (1,150) | +0 | +0 |
| H6 | PRE | 75 | 0.61 | +1.6 | +55.5 | +2.57 | +2.56 | -315 (1,015) | +0 | +0 |
| H6 | X' | 44 | 0.48 | +0.1 | +17.1 | +0.25 | +0.26 | -24 (763) | +0 | +0 |
| M6 | L3M | 14 | 0.79 | -7.3 | +105.9 | -9.26 | -9.63 | +1,456 (2,921) | +0 | +0 |
| M6 | L6M | 28 | 0.68 | +1.7 | +91.0 | +2.47 | +2.51 | -336 (1,758) | +0 | +0 |
| M6 | HOLD | 32 | 0.78 | +1.2 | +58.0 | +1.50 | +1.51 | -235 (1,638) | +0 | +0 |
| M6 | PRE | 75 | 0.68 | -2.2 | +86.0 | -3.20 | -3.20 | +436 (966) | +0 | +0 |
| M6 | X' | 44 | 0.52 | -13.6 | -52.5 | -25.94 | -25.85 | +2,712 (922) | +0 | +0 |
| A6 | L3M | 14 | 0.71 | +3.2 | +259.4 | +4.52 | +4.56 | -646 (2,166) | -65 | -64 |
| A6 | L6M | 28 | 0.57 | +5.0 | +229.2 | +8.73 | +8.71 | -998 (1,341) | -100 | -174 |
| A6 | HOLD | 32 | 0.53 | +3.8 | +178.5 | +7.17 | +7.15 | -762 (1,180) | -76 | -130 |
| A6 | PRE | 75 | 0.67 | +0.1 | -10.3 | +0.09 | +0.10 | -13 (914) | -1 | +45 |
| A6 | X' | 44 | 0.52 | +0.0 | +43.6 | +0.06 | +0.05 | -6 (1,004) | -1 | +34 |
| S6 | L3M | 14 | 0.79 | -12.8 | +143.6 | -16.34 | -16.91 | +2,568 (2,155) | +0 | +0 |
| S6 | L6M | 28 | 0.75 | -1.2 | +196.9 | -1.57 | -1.59 | +236 (1,800) | +0 | +0 |
| S6 | HOLD | 32 | 0.75 | +1.7 | +149.0 | +2.29 | +2.31 | -344 (1,698) | +0 | +0 |
| S6 | PRE | 75 | 0.83 | +0.5 | +80.0 | +0.63 | +0.64 | -104 (1,030) | +0 | +0 |
| S6 | X' | 44 | 0.73 | -6.6 | +22.6 | -9.01 | -8.86 | +1,310 (1,060) | +0 | +0 |
| W6 | L3M | 14 | 1.21 | -3.5 | +94.7 | -2.89 | -2.87 | +491 (1,562) | +0 | +0 |
| W6 | L6M | 28 | 0.96 | -0.2 | +114.2 | -0.23 | -0.23 | +31 (853) | +0 | +0 |
| W6 | HOLD | 32 | 0.97 | -1.0 | +77.3 | -0.98 | -0.97 | +133 (877) | +0 | +0 |
| W6 | PRE | 75 | 1.17 | -1.9 | +35.3 | -1.59 | -1.64 | +261 (623) | +0 | +0 |
| W6 | X' | 44 | 1.00 | +2.6 | +13.3 | +2.57 | +2.59 | -360 (661) | +0 | +0 |
| MA6 | L3M | 14 | 0.64 | +20.5 | +107.9 | +31.84 | +32.29 | -4,094 (2,999) | +0 | +0 |
| MA6 | L6M | 28 | 0.43 | +16.8 | +72.8 | +39.19 | +39.35 | -3,359 (1,629) | +0 | +0 |
| MA6 | HOLD | 32 | 0.44 | +14.5 | +57.3 | +33.20 | +34.01 | -2,905 (1,493) | +0 | +0 |
| MA6 | PRE | 75 | 0.37 | +0.2 | +37.0 | +0.65 | +0.63 | -48 (773) | +0 | +0 |
| MA6 | X' | 44 | 0.30 | +3.4 | +25.7 | +11.67 | +11.74 | -689 (901) | +0 | +0 |
| DN | L3M | 14 | 0.29 | -7.0 | +137.1 | -24.60 | -24.16 | +1,406 (1,621) | +0 | +0 |
| DN | L6M | 28 | 0.32 | +0.6 | +136.1 | +1.83 | +1.80 | -118 (1,360) | +0 | +0 |
| DN | HOLD | 32 | 0.31 | +2.4 | +99.4 | +7.84 | +7.69 | -490 (1,248) | +0 | +0 |
| DN | PRE | 75 | 0.25 | +0.5 | +72.6 | +1.82 | +1.85 | -92 (707) | +0 | +0 |
| DN | X' | 44 | 0.43 | -8.0 | +9.1 | -18.47 | -18.78 | +1,595 (945) | +0 | +0 |
| ALL6 | L3M | 14 | 4.29 | -42.8 | +305.3 | -9.99 | -10.22 | +5,546 (5,320) | -93 | -172 |
| ALL6 | L6M | 28 | 3.82 | -10.3 | +607.7 | -2.69 | -2.70 | +1,189 (3,380) | -318 | -416 |
| ALL6 | HOLD | 32 | 3.75 | -6.1 | +478.2 | -1.64 | -1.64 | +764 (3,072) | -319 | -443 |
| ALL6 | PRE | 75 | 3.84 | -4.0 | +299.6 | -1.05 | -1.05 | +549 (2,272) | +83 | -100 |
| ALL6 | X' | 44 | 3.14 | -20.2 | +42.0 | -6.43 | -6.40 | +3,533 (2,434) | +160 | +258 |

#### Sensitivity edges (no selection; MKT base, $/wk research lots, signal-level)

| edge | group | L3M | L6M | HOLD | PRE | X' | sig/wk L6M |
|--|--|--|--|--|--|--|--|
| 1440-1500 | ALL6 | +4,219 | +1,223 | +841 | +436 | +3,476 | 3.82 |
| 1440-1500 | K6 | -166 | -587 | -639 | +234 | +427 | 0.68 |
| 1440-1500 | P6 | +3,083 | +2,000 | +1,541 | +184 | -20 | 1.07 |
| 1440-1500 | U6 | +1,070 | +227 | +192 | +245 | +465 | 0.14 |
| 1440-1500 | H6 | +64 | +1,169 | +930 | -331 | -146 | 0.68 |
| 1440-1500 | A6 | -815 | -1,051 | -804 | -269 | +73 | 0.57 |
| 1440-1500 | S6 | +2,121 | +939 | +285 | -255 | +1,400 | 0.75 |
| 1440-1500 | W6 | +474 | +52 | +157 | +325 | -422 | 0.96 |
| 1440-1500 | MA6 | -2,497 | -2,529 | -2,290 | -1 | -688 | 0.43 |
| 1430-1500 | ALL6 | +5,716 | -994 | -1,308 | +1,590 | +319 | 5.82 |
| 1430-1500 | K6 | -1,020 | -1,600 | -1,361 | +656 | +840 | 1.18 |
| 1430-1500 | P6 | +2,617 | +777 | +471 | +653 | -466 | 1.46 |
| 1430-1500 | U6 | -193 | -428 | -361 | +250 | +608 | 0.21 |
| 1430-1500 | H6 | +1,074 | +679 | +502 | -779 | -1,852 | 1.11 |
| 1430-1500 | A6 | -390 | -401 | -609 | -432 | +417 | 0.79 |
| 1430-1500 | S6 | +1,349 | -1,328 | -1,698 | +309 | +1,688 | 1.25 |
| 1430-1500 | W6 | -276 | -501 | -327 | +1,182 | -635 | 1.61 |
| 1430-1500 | MA6 | -2,497 | -2,745 | -2,096 | +404 | -343 | 0.50 |
| 1450-1500 | ALL6 | -2,883 | -552 | -1,283 | -463 | +1,891 | 1.96 |
| 1450-1500 | K6 | -1,087 | -831 | -853 | -26 | -346 | 0.43 |
| 1450-1500 | P6 | +396 | +846 | +531 | -73 | -226 | 0.46 |
| 1450-1500 | U6 | +309 | -167 | -141 | -1 | +725 | 0.07 |
| 1450-1500 | H6 | -832 | +935 | +726 | -500 | -675 | 0.32 |
| 1450-1500 | A6 | -1,711 | -645 | -565 | -210 | +769 | 0.39 |
| 1450-1500 | S6 | +1,793 | +1,180 | +870 | +462 | +315 | 0.39 |
| 1450-1500 | W6 | -160 | -225 | -141 | +690 | -617 | 0.54 |
| 1450-1500 | MA6 | -811 | -1,259 | -1,178 | +342 | -263 | 0.25 |

#### Placebo: rank of the real NY-PM-end window among 20-minute windows (rank = share of placebo windows with gain <= real; 1 = real is the best). Gain $/wk research lots, MKT and SPL bases

| group | base | window | real | random NY-PM 20-min windows (12:00-15:00, 1-min grid): n, median, rank | all 20-min windows in the last 3h of each other session end (n, rank) | the 4 other session-end windows (asia 01:40, london 08:10, pre 09:10, NY-AM 11:40): values |
|--|--|--|--|--|--|--|
| ALL6 | MKT | L6M | +1,223 | 161, +766, 0.58 | 644, 0.89 | -2,545 / -4,661 / -6,009 / +370 |
| ALL6 | MKT | HOLD | +841 | 161, +948, 0.49 | 644, 0.81 | -2,600 / -3,975 / -3,881 / +3,637 |
| ALL6 | MKT | PRE | +436 | 161, +403, 0.52 | 644, 0.73 | -194 / -2,796 / -223 / -1,758 |
| ALL6 | MKT | X' | +3,476 | 161, +1,062, 0.86 | 644, 0.97 | -154 / -1,852 / +205 / -1,248 |
| RES9 | MKT | L6M | -316 | 161, -67, 0.49 | 644, 0.70 | -1,523 / -4,078 / -7,773 / -6,013 |
| RES9 | MKT | HOLD | -1,006 | 161, +314, 0.45 | 644, 0.60 | -1,706 / -3,783 / -4,412 / -2,020 |
| RES9 | MKT | PRE | +506 | 161, +1,285, 0.44 | 644, 0.73 | +762 / -3,767 / +3,584 / -1,779 |
| RES9 | MKT | X' | +3,766 | 161, +532, 0.81 | 644, 0.97 | -840 / -3,222 / +49 / -1,058 |
| PEsmhmstwt | MKT | L6M | +4,379 | 161, +145, 0.96 | 644, 0.99 | +1,414 / -3,669 / -1,852 / -2,643 |
| PEsmhmstwt | MKT | HOLD | +3,105 | 161, +517, 0.80 | 644, 0.98 | +1,237 / -3,150 / +372 / -1,572 |
| PEsmhmstwt | MKT | PRE | +168 | 161, +1,214, 0.35 | 644, 0.57 | +1,382 / -1,754 / +3,625 / -89 |
| PEsmhmstwt | MKT | X' | +1,276 | 161, +515, 0.66 | 644, 0.87 | +639 / -3,095 / -706 / +1,953 |
| KBPBMA | MKT | L6M | -4,167 | 161, -1,187, 0.09 | 644, 0.06 | -2,531 / +370 / -4,759 / -2,836 |
| KBPBMA | MKT | HOLD | -3,733 | 161, -1,070, 0.09 | 644, 0.06 | -2,588 / +413 / -3,776 / -1,129 |
| KBPBMA | MKT | PRE | -36 | 161, +191, 0.42 | 644, 0.59 | -812 / -1,252 / +1,022 / -440 |
| KBPBMA | MKT | X' | -188 | 161, +182, 0.29 | 644, 0.48 | -1,214 / -459 / +179 / -2,408 |
| KB | MKT | L6M | -587 | 161, -445, 0.43 | 644, 0.28 | -877 / +1,160 / -1,310 / -204 |
| KB | MKT | HOLD | -639 | 161, -135, 0.22 | 644, 0.23 | -767 / +1,094 / -1,141 / +25 |
| KB | MKT | PRE | +234 | 161, -212, 0.76 | 644, 0.84 | -214 / +278 / +759 / -428 |
| KB | MKT | X' | +427 | 161, +104, 0.76 | 644, 0.87 | -141 / +879 / -287 / -909 |
| PE | MKT | L6M | +2,000 | 161, -9, 1.00 | 644, 0.97 | -466 / -209 / +72 / +3,331 |
| PE | MKT | HOLD | +1,541 | 161, +184, 0.97 | 644, 0.97 | -408 / -178 / +277 / +2,705 |
| PE | MKT | PRE | +184 | 161, +276, 0.47 | 644, 0.61 | +292 / -317 / +239 / -472 |
| PE | MKT | X' | -20 | 161, +55, 0.45 | 644, 0.47 | +4 / -197 / +331 / +300 |
| SM | MKT | L6M | +227 | 161, +8, 0.69 | 644, 0.63 | -7 / +688 / -311 / +688 |
| SM | MKT | HOLD | +192 | 161, +7, 0.81 | 644, 0.63 | -6 / +580 / -263 / +580 |
| SM | MKT | PRE | +245 | 161, -77, 0.81 | 644, 0.83 | +130 / +147 / +18 / +622 |
| SM | MKT | X' | +465 | 161, +365, 0.75 | 644, 0.92 | +221 / -196 / +221 / +10 |
| HM | MKT | L6M | +1,169 | 161, -85, 0.82 | 644, 0.92 | +886 / -3,393 / -363 / -649 |
| HM | MKT | HOLD | +930 | 161, -27, 0.78 | 644, 0.89 | +775 / -2,969 / +448 / +454 |
| HM | MKT | PRE | -331 | 161, +80, 0.40 | 644, 0.32 | +183 / -749 / +725 / +252 |
| HM | MKT | X' | -146 | 161, -139, 0.50 | 644, 0.31 | +564 / -1,054 / -1,353 / +652 |
| ST | MKT | L6M | +939 | 161, +46, 0.72 | 644, 0.88 | +491 / -1,622 / -2,049 / -4,137 |
| ST | MKT | HOLD | +285 | 161, -51, 0.60 | 644, 0.73 | +430 / -1,419 / -780 / -4,153 |
| ST | MKT | PRE | -255 | 161, +135, 0.40 | 644, 0.36 | +36 / -876 / +2,508 / +318 |
| ST | MKT | X' | +1,400 | 161, +53, 0.86 | 644, 0.92 | -272 / -1,174 / -135 / +415 |
| WT | MKT | L6M | +52 | 161, +102, 0.47 | 644, 0.67 | +510 / +892 / +788 / -1,851 |
| WT | MKT | HOLD | +157 | 161, +224, 0.44 | 644, 0.70 | +446 / +836 / +690 / -1,159 |
| WT | MKT | PRE | +325 | 161, +208, 0.54 | 644, 0.79 | +741 / +41 / +136 / -808 |
| WT | MKT | X' | -422 | 161, -101, 0.24 | 644, 0.26 | +122 / -474 / +230 / +576 |
| PB | MKT | L6M | -1,051 | 161, -278, 0.32 | 644, 0.35 | -1,675 / -2,102 / -2,945 / -2,237 |
| PB | MKT | HOLD | -804 | 161, -363, 0.39 | 644, 0.36 | -1,839 / -1,457 / -2,194 / -809 |
| PB | MKT | PRE | -269 | 161, +161, 0.28 | 644, 0.43 | -777 / -1,394 / -900 / -482 |
| PB | MKT | X' | +73 | 161, +31, 0.53 | 644, 0.63 | -536 / -1,616 / +717 / -698 |
| MA | MKT | L6M | -2,529 | 161, -500, 0.12 | 644, 0.06 | +21 / +1,313 / -504 / -395 |
| MA | MKT | HOLD | -2,290 | 161, -391, 0.06 | 644, 0.08 | +19 / +775 / -441 / -345 |
| MA | MKT | PRE | -1 | 161, -1, 0.50 | 644, 0.56 | +179 / -135 / +1,163 / +470 |
| MA | MKT | X' | -688 | 161, +48, 0.25 | 644, 0.14 | -536 / +278 / -251 / -801 |
| ALL6 | SPL | L6M | +1,189 | 161, +884, 0.57 | 644, 0.93 | -2,687 / -5,314 / -6,699 / +291 |
| ALL6 | SPL | HOLD | +764 | 161, +898, 0.48 | 644, 0.86 | -2,731 / -4,565 / -4,433 / +3,556 |
| ALL6 | SPL | PRE | +549 | 161, +468, 0.54 | 644, 0.76 | -298 / -2,802 / +113 / -2,323 |
| ALL6 | SPL | X' | +3,533 | 161, +1,117, 0.86 | 644, 0.98 | -196 / -1,902 / -692 / -1,258 |
| RES9 | SPL | L6M | -1,903 | 161, -206, 0.45 | 644, 0.56 | -1,688 / -4,495 / -9,114 / -6,148 |
| RES9 | SPL | HOLD | -2,352 | 161, +207, 0.41 | 644, 0.50 | -1,857 / -4,175 / -5,535 / -2,179 |
| RES9 | SPL | PRE | +658 | 161, +1,175, 0.46 | 644, 0.76 | +753 / -3,983 / +3,933 / -2,269 |
| RES9 | SPL | X' | +3,794 | 161, +944, 0.81 | 644, 0.97 | -904 / -3,125 / -825 / -1,286 |
| PEsmhmstwt | SPL | L6M | +3,356 | 161, +49, 0.88 | 644, 0.99 | +1,368 / -4,051 / -3,074 / -3,122 |
| PEsmhmstwt | SPL | HOLD | +2,180 | 161, +218, 0.71 | 644, 0.96 | +1,197 / -3,489 / -699 / -2,030 |
| PEsmhmstwt | SPL | PRE | +64 | 161, +1,322, 0.34 | 644, 0.56 | +1,350 / -1,948 / +3,802 / -640 |
| PEsmhmstwt | SPL | X' | +1,359 | 161, +715, 0.66 | 644, 0.88 | +614 / -3,012 / -751 / +1,698 |
| KBPBMA | SPL | L6M | -4,924 | 161, -876, 0.02 | 644, 0.03 | -2,625 / +407 / -4,775 / -2,625 |
| KBPBMA | SPL | HOLD | -4,297 | 161, -976, 0.01 | 644, 0.04 | -2,676 / +438 / -3,732 / -947 |
| KBPBMA | SPL | PRE | +159 | 161, +159, 0.50 | 644, 0.68 | -770 / -1,334 / +1,210 / -368 |
| KBPBMA | SPL | X' | -277 | 161, +243, 0.23 | 644, 0.42 | -1,245 / -412 / -145 / -2,039 |
| KB | SPL | L6M | -567 | 161, -423, 0.40 | 644, 0.29 | -901 / +1,145 / -1,349 / -74 |
| KB | SPL | HOLD | -631 | 161, -149, 0.21 | 644, 0.24 | -788 / +1,079 / -1,117 / +136 |
| KB | SPL | PRE | +220 | 161, -222, 0.76 | 644, 0.82 | -232 / +312 / +816 / -470 |
| KB | SPL | X' | +418 | 161, +110, 0.78 | 644, 0.85 | -143 / +873 / -257 / -798 |
| PE | SPL | L6M | +1,674 | 161, +54, 0.99 | 644, 0.95 | -484 / -237 / -465 / +3,008 |
| PE | SPL | HOLD | +1,252 | 161, +216, 0.87 | 644, 0.94 | -423 / -206 / -193 / +2,420 |
| PE | SPL | PRE | -49 | 161, +290, 0.35 | 644, 0.42 | +126 / -354 / +252 / -797 |
| PE | SPL | X' | -81 | 161, +73, 0.43 | 644, 0.44 | +2 / -211 / +318 / +400 |
| SM | SPL | L6M | +212 | 161, +10, 0.69 | 644, 0.69 | -17 / +8 / -330 / +668 |
| SM | SPL | HOLD | +179 | 161, +8, 0.81 | 644, 0.66 | -14 / +7 / -279 / +564 |
| SM | SPL | PRE | +271 | 161, -34, 0.81 | 644, 0.91 | +123 / +127 / +7 / +445 |
| SM | SPL | X' | +513 | 161, +347, 0.88 | 644, 0.94 | +212 / -205 / +210 / +2 |
| HM | SPL | L6M | +1,211 | 161, -118, 0.82 | 644, 0.92 | +878 / -3,327 / -274 / -622 |
| HM | SPL | HOLD | +960 | 161, -31, 0.80 | 644, 0.89 | +769 / -2,911 / +527 / +471 |
| HM | SPL | PRE | -315 | 161, -74, 0.42 | 644, 0.32 | +219 / -694 / +872 / +143 |
| HM | SPL | X' | -24 | 161, -80, 0.52 | 644, 0.32 | +560 / -1,094 / -1,412 / +671 |
| ST | SPL | L6M | +236 | 161, -225, 0.61 | 644, 0.80 | +455 / -1,436 / -2,149 / -4,352 |
| ST | SPL | HOLD | -344 | 161, -394, 0.52 | 644, 0.57 | +398 / -1,257 / -870 / -4,366 |
| ST | SPL | PRE | -104 | 161, +151, 0.41 | 644, 0.40 | +59 / -810 / +2,461 / +137 |
| ST | SPL | X' | +1,310 | 161, +119, 0.83 | 644, 0.90 | -276 / -1,038 / -81 / +120 |
| WT | SPL | L6M | +31 | 161, +56, 0.48 | 644, 0.66 | +534 / +942 / +133 / -1,800 |
| WT | SPL | HOLD | +133 | 161, +219, 0.45 | 644, 0.73 | +468 / +877 / +116 / -1,119 |
| WT | SPL | PRE | +261 | 161, +260, 0.51 | 644, 0.78 | +822 / -217 / +209 / -567 |
| WT | SPL | X' | -360 | 161, -17, 0.23 | 644, 0.26 | +115 / -463 / +215 / +505 |
| PB | SPL | L6M | -998 | 161, -125, 0.32 | 644, 0.40 | -1,733 / -2,051 / -3,028 / -2,265 |
| PB | SPL | HOLD | -762 | 161, -218, 0.38 | 644, 0.41 | -1,896 / -1,411 / -2,266 / -833 |
| PB | SPL | PRE | -13 | 161, +224, 0.43 | 644, 0.48 | -707 / -1,492 / -756 / -383 |
| PB | SPL | X' | -6 | 161, -6, 0.50 | 644, 0.46 | -553 / -1,564 / +379 / -589 |
| MA | SPL | L6M | -3,359 | 161, -430, 0.06 | 644, 0.00 | +9 / +1,313 / -398 / -287 |
| MA | SPL | HOLD | -2,905 | 161, -417, 0.06 | 644, 0.03 | +8 / +770 / -348 / -251 |
| MA | SPL | PRE | -48 | 161, -133, 0.57 | 644, 0.55 | +169 / -154 / +1,150 / +485 |
| MA | SPL | X' | -689 | 161, +88, 0.19 | 644, 0.11 | -548 / +279 / -267 / -653 |

## 3. Stack lines and risk lines

#### Stack lines, skip 14:40-15:00 (block by signal second), delta $/wk (MDE 2.8 SE) [4-wk-block 95% CI]; N basis, causal running-max locks

| lots | config | window | stack mean $/wk without | with skip | delta (MDE) [CI] | SD without / with | maxDD without / with | worst-20 sum without / with |
|--|--|--|--|--|--|--|--|--|
| live | ALONE (stack as it is, +skip) | L3M | 13,808 | 13,880 | +73 (407) [-17, +206] | 47,965 / 47,786 | 98,289 / 98,289 | 193,307 / 194,325 |
| live | ALONE (stack as it is, +skip) | L6M | 24,018 | 24,074 | +57 (574) [-230, +393] | 47,167 / 46,986 | 98,289 / 98,289 | 67,973 / 71,707 |
| live | ALONE (stack as it is, +skip) | HOLD | 23,714 | 23,689 | -25 (545) [-440, +314] | 56,295 / 55,985 | 155,192 / 155,192 | -177,798 / -174,063 |
| live | ALONE (stack as it is, +skip) | PRE | 17,705 | 17,633 | -72 (369) [-312, +159] | 52,621 / 52,981 | 232,289 / 232,299 | -873,647 / -884,059 |
| live | ALONE (stack as it is, +skip) | X' | -3,569 | -3,449 | +120 (507) [-188, +491] | 29,292 / 29,254 | 329,693 / 322,018 | -588,131 / -584,204 |
| live | composite frac 70/30 + skip | L3M | 33,173 | 33,203 | +30 (1,292) [-739, +913] | 45,895 / 45,500 | 102,380 / 101,612 | 464,419 / 464,843 |
| live | composite frac 70/30 + skip | L6M | 42,562 | 42,492 | -70 (909) [-608, +494] | 42,131 / 41,940 | 102,380 / 101,612 | 401,272 / 401,079 |
| live | composite frac 70/30 + skip | HOLD | 39,892 | 39,810 | -82 (802) [-569, +404] | 51,682 / 51,422 | 109,297 / 108,745 | 165,247 / 164,986 |
| live | composite frac 70/30 + skip | PRE | 22,418 | 22,315 | -103 (479) [-364, +186] | 56,598 / 56,712 | 266,887 / 269,177 | -904,816 / -913,803 |
| live | composite frac 70/30 + skip | X' | 8,977 | 9,228 | +251 (674) [-127, +662] | 33,220 / 32,988 | 154,287 / 152,219 | -394,681 / -388,485 |
| live | composite integer lots (headline) + skip | L3M | 38,851 | 38,857 | +6 (1,267) [-724, +806] | 46,139 / 45,773 | 93,899 / 94,497 | 543,909 / 543,995 |
| live | composite integer lots (headline) + skip | L6M | 46,802 | 46,658 | -144 (935) [-725, +383] | 45,944 / 45,723 | 93,899 / 94,497 | 442,791 / 441,605 |
| live | composite integer lots (headline) + skip | HOLD | 43,025 | 42,877 | -148 (824) [-676, +323] | 55,962 / 55,681 | 118,250 / 117,704 | 182,350 / 181,710 |
| live | composite integer lots (headline) + skip | PRE | 25,109 | 24,843 | -266 (462) [-538, -2] | 58,533 / 58,672 | 288,893 / 289,243 | -911,908 / -923,429 |
| live | composite integer lots (headline) + skip | X' | 9,320 | 9,604 | +284 (707) [-102, +731] | 34,278 / 34,191 | 152,195 / 150,402 | -415,459 / -410,641 |
| live | composite integer, K6 at market + skip | L3M | 36,495 | 36,470 | -25 (1,278) [-730, +770] | 47,291 / 46,927 | 92,773 / 93,968 | 510,930 / 510,580 |
| live | composite integer, K6 at market + skip | L6M | 46,092 | 45,938 | -153 (932) [-713, +363] | 46,221 / 45,976 | 92,773 / 93,968 | 434,950 / 437,165 |
| live | composite integer, K6 at market + skip | HOLD | 42,629 | 42,475 | -154 (821) [-667, +302] | 56,386 / 56,086 | 116,601 / 116,601 | 170,303 / 169,357 |
| live | composite integer, K6 at market + skip | PRE | 24,540 | 24,327 | -212 (449) [-467, +56] | 58,504 / 58,675 | 283,970 / 284,321 | -917,500 / -929,229 |
| live | composite integer, K6 at market + skip | X' | 9,460 | 9,887 | +427 (799) [-52, +1,019] | 33,779 / 33,775 | 145,244 / 143,345 | -402,389 / -394,611 |
| live+ | ALONE (stack as it is, +skip) | L3M | 18,622 | 19,613 | +991 (1,800) [+56, +2,755] | 71,628 / 71,266 | 162,626 / 152,108 | 260,703 / 274,578 |
| live+ | ALONE (stack as it is, +skip) | L6M | 34,427 | 35,053 | +626 (1,150) [-79, +1,663] | 71,985 / 71,704 | 162,626 / 152,108 | 65,171 / 80,952 |
| live+ | ALONE (stack as it is, +skip) | HOLD | 29,958 | 30,431 | +473 (1,041) [-315, +1,425] | 88,854 / 88,531 | 305,721 / 305,721 | -403,086 / -387,305 |
| live+ | ALONE (stack as it is, +skip) | PRE | 24,594 | 24,797 | +203 (710) [-279, +686] | 70,802 / 70,982 | 311,111 / 305,786 | -1,226,051 / -1,229,858 |
| live+ | ALONE (stack as it is, +skip) | X' | -487 | 21 | +508 (1,078) [-197, +1,177] | 50,810 / 50,453 | 399,732 / 374,877 | -906,712 / -888,057 |
| live+ | composite frac 70/30 + skip | L3M | 57,239 | 57,079 | -160 (2,035) [-1,290, +985] | 66,975 / 66,347 | 160,291 / 158,218 | 801,350 / 799,113 |
| live+ | composite frac 70/30 + skip | L6M | 65,492 | 65,136 | -356 (1,297) [-1,091, +454] | 63,104 / 62,725 | 160,291 / 158,218 | 700,311 / 695,155 |
| live+ | composite frac 70/30 + skip | HOLD | 59,662 | 59,018 | -644 (1,376) [-1,683, +151] | 82,050 / 81,777 | 199,500 / 205,310 | 278,792 / 268,029 |
| live+ | composite frac 70/30 + skip | PRE | 39,506 | 38,584 | -923 (1,367) [-1,706, -132] | 79,224 / 78,989 | 280,687 / 286,057 | -1,029,446 / -1,051,208 |
| live+ | composite frac 70/30 + skip | X' | 9,456 | 10,125 | +669 (1,870) [-480, +1,930] | 54,119 / 54,016 | 301,719 / 293,683 | -743,435 / -732,810 |
| live+ | composite integer lots (headline) + skip | L3M | 58,699 | 59,365 | +666 (2,370) [-946, +2,678] | 65,355 / 64,541 | 131,556 / 119,564 | 821,786 / 831,115 |
| live+ | composite integer lots (headline) + skip | L6M | 66,999 | 67,422 | +423 (1,890) [-832, +1,792] | 62,706 / 62,302 | 131,556 / 119,564 | 708,921 / 728,520 |
| live+ | composite integer lots (headline) + skip | HOLD | 60,375 | 60,428 | +53 (1,840) [-1,254, +1,346] | 82,734 / 82,501 | 214,266 / 220,062 | 269,986 / 271,555 |
| live+ | composite integer lots (headline) + skip | PRE | 38,071 | 37,128 | -943 (1,310) [-1,605, -227] | 79,269 / 79,035 | 269,759 / 274,993 | -1,078,292 / -1,099,107 |
| live+ | composite integer lots (headline) + skip | X' | 11,356 | 11,506 | +150 (1,669) [-944, +1,155] | 52,660 / 52,607 | 285,056 / 271,929 | -688,218 / -691,390 |
| live+ | composite integer, K6 at market + skip | L3M | 56,381 | 57,016 | +635 (2,326) [-963, +2,603] | 65,940 / 65,160 | 130,415 / 118,955 | 789,338 / 798,230 |
| live+ | composite integer, K6 at market + skip | L6M | 66,439 | 66,810 | +371 (1,853) [-842, +1,738] | 62,714 / 62,317 | 130,415 / 118,955 | 700,626 / 718,695 |
| live+ | composite integer, K6 at market + skip | HOLD | 60,125 | 60,135 | +10 (1,809) [-1,289, +1,275] | 82,974 / 82,728 | 211,901 / 217,678 | 263,166 / 261,475 |
| live+ | composite integer, K6 at market + skip | PRE | 37,329 | 36,455 | -874 (1,318) [-1,555, -128] | 79,263 / 79,081 | 270,372 / 276,204 | -1,086,957 / -1,107,701 |
| live+ | composite integer, K6 at market + skip | X' | 11,278 | 11,544 | +265 (1,741) [-830, +1,279] | 52,375 / 52,469 | 287,296 / 274,063 | -687,529 / -691,071 |
| research | ALONE (stack as it is, +skip) | L3M | -1,028 | 2,595 | +3,623 (5,664) [+869, +8,925] | 140,705 / 139,508 | 417,337 / 381,496 | -14,399 / 36,323 |
| research | ALONE (stack as it is, +skip) | L6M | 49,998 | 54,096 | +4,098 (4,054) [+2,307, +7,154] | 144,595 / 143,996 | 417,337 / 381,496 | -371,575 / -267,662 |
| research | ALONE (stack as it is, +skip) | HOLD | 37,202 | 40,501 | +3,299 (3,723) [+821, +6,383] | 172,541 / 172,244 | 684,496 / 687,449 | -1,320,961 / -1,228,180 |
| research | ALONE (stack as it is, +skip) | PRE | 46,134 | 46,791 | +657 (2,841) [-928, +2,203] | 137,404 / 138,960 | 777,509 / 787,197 | -2,619,733 / -2,642,084 |
| research | ALONE (stack as it is, +skip) | X' | 7,014 | 8,757 | +1,742 (4,089) [-553, +4,243] | 104,411 / 105,911 | 559,989 / 545,156 | -1,660,862 / -1,671,862 |
| research | composite frac 70/30 + skip | L3M | 94,174 | 95,894 | +1,720 (6,853) [-2,547, +6,166] | 152,971 / 150,270 | 453,150 / 431,974 | 1,318,438 / 1,342,520 |
| research | composite frac 70/30 + skip | L6M | 129,540 | 129,812 | +272 (4,956) [-2,593, +3,468] | 144,872 / 144,273 | 453,150 / 431,974 | 1,268,444 / 1,290,039 |
| research | composite frac 70/30 + skip | HOLD | 112,146 | 111,598 | -548 (4,746) [-4,189, +2,562] | 167,682 / 167,179 | 453,150 / 431,974 | 287,788 / 286,066 |
| research | composite frac 70/30 + skip | PRE | 70,852 | 68,407 | -2,445 (5,009) [-5,809, +442] | 154,153 / 154,977 | 525,159 / 548,876 | -2,265,461 / -2,309,412 |
| research | composite frac 70/30 + skip | X' | 19,779 | 22,267 | +2,488 (6,093) [-955, +6,659] | 106,824 / 108,293 | 624,551 / 627,960 | -1,427,492 / -1,406,743 |
| research | composite integer lots (headline) + skip | L3M | 96,678 | 99,033 | +2,355 (6,251) [-1,060, +6,595] | 147,885 / 146,431 | 442,276 / 420,892 | 1,353,486 / 1,386,457 |
| research | composite integer lots (headline) + skip | L6M | 124,938 | 125,645 | +707 (4,787) [-2,093, +3,788] | 140,463 / 140,673 | 442,276 / 420,892 | 1,214,973 / 1,223,699 |
| research | composite integer lots (headline) + skip | HOLD | 107,983 | 107,811 | -173 (4,652) [-3,704, +2,918] | 164,361 / 164,398 | 442,276 / 422,007 | 245,315 / 244,316 |
| research | composite integer lots (headline) + skip | PRE | 69,227 | 66,746 | -2,481 (5,014) [-5,774, +470] | 153,574 / 154,603 | 543,152 / 566,535 | -2,294,487 / -2,330,363 |
| research | composite integer lots (headline) + skip | X' | 16,538 | 19,423 | +2,885 (6,120) [-482, +7,032] | 103,931 / 105,356 | 632,283 / 624,686 | -1,444,704 / -1,404,538 |
| research | composite integer, K6 at market + skip | L3M | 91,671 | 93,232 | +1,561 (7,139) [-2,832, +6,095] | 149,166 / 146,822 | 440,795 / 421,027 | 1,283,394 / 1,305,254 |
| research | composite integer, K6 at market + skip | L6M | 124,833 | 125,165 | +332 (5,106) [-2,550, +3,511] | 142,421 / 142,155 | 440,795 / 421,027 | 1,213,753 / 1,220,687 |
| research | composite integer, K6 at market + skip | HOLD | 107,775 | 107,280 | -495 (4,887) [-4,193, +2,643] | 165,353 / 164,998 | 440,795 / 421,027 | 225,965 / 217,344 |
| research | composite integer, K6 at market + skip | PRE | 65,885 | 63,445 | -2,439 (4,977) [-5,809, +490] | 153,050 / 154,002 | 530,759 / 555,935 | -2,346,155 / -2,384,610 |
| research | composite integer, K6 at market + skip | X' | 15,964 | 19,367 | +3,402 (6,761) [-285, +8,092] | 104,406 / 106,003 | 638,767 / 630,879 | -1,457,336 / -1,405,322 |

#### Stack delta by edge (sensitivity), L6M / HOLD / PRE / X'

| lots | config | 14:40 | 14:30 | 14:50 |
|--|--|--|--|--|
| live | ALONE (stack as it is, +skip) | +57 / -25 / -72 / +120 | -98 / -119 / -150 / +137 | -33 / -104 / -29 / +41 |
| live | composite frac 70/30 + skip | -70 / -82 / -103 / +251 | -284 / -349 / +50 / +373 | +80 / +49 / -161 / -17 |
| live | composite integer lots (headline) + skip | -144 / -148 / -266 / +284 | -422 / -373 / -198 / +400 | +71 / +41 / -157 / +28 |
| live | composite integer, K6 at market + skip | -153 / -154 / -212 / +427 | -436 / -496 / -124 / +557 | +56 / +30 / -152 / +168 |
| live+ | ALONE (stack as it is, +skip) | +626 / +473 / +203 / +508 | +364 / +285 / +113 / +564 | +426 / +298 / +226 / +136 |
| live+ | composite frac 70/30 + skip | -356 / -644 / -923 / +669 | -807 / -1,117 / -372 / +433 | +84 / -60 / -164 / +139 |
| live+ | composite integer lots (headline) + skip | +423 / +53 / -943 / +150 | -240 / -509 / -611 / +55 | +419 / +248 / -143 / -352 |
| live+ | composite integer, K6 at market + skip | +371 / +10 / -874 / +265 | -297 / -670 / -495 / +184 | +362 / +200 / -138 / -239 |
| research | ALONE (stack as it is, +skip) | +4,098 / +3,299 / +657 / +1,742 | +2,277 / +1,910 / +599 / +696 | +2,473 / +1,877 / +765 / +145 |
| research | composite frac 70/30 + skip | +272 / -548 / -2,445 / +2,488 | -2,595 / -3,114 / -1,122 / +227 | +1,372 / +881 / -426 / -11 |
| research | composite integer lots (headline) + skip | +707 / -173 / -2,481 / +2,885 | -1,951 / -2,560 / -1,477 / +543 | +1,591 / +1,053 / -478 / +189 |
| research | composite integer, K6 at market + skip | +332 / -495 / -2,439 / +3,402 | -2,532 / -3,055 / -1,301 / +1,059 | +1,417 / +906 / -449 / +486 |

## 4. Evidence class (plain)

* **Found post-hoc.** The 14:30-15:00 end of NY-PM was named from the NTE-1 map after the recent windows had been looked at (it lowers P(target) in every window: about 40% vs 53%). The 20-minute edge is the user's choice from that map, not selected on PRE u X' with one recent look. Tier: LEAD, post-hoc, forward-register only; it does not pass the program-level reality check of NTE-1 (cumulative p about 1).
* **A composition effect, not a no-trade zone.** Per signal the skip is about zero (pooled skipped P&L {-3.05:+.2f} pts vs +2.92 for all signals in L6M; random-20-min-window placebo rank for the six live-tag books 0.58 market / 0.57 70-30; the book groups: P6 rank 1.00/0.99, H6 0.82, U6 0.69; PE SM HM ST WT pooled 0.88 on the 70/30 base, 0.71 HOLD). Books split: P6 U6 H6 S6 W6 positive, K6 A6 M6 MA6 negative (MA6 and the KB+PB+MA group sit at rank 0.02-0.12, i.e. the negative side is as clear as the positive one). The stack gain exists because the books that fire into the close are the ones that lose there; it is a statement about which books are on at 14:40, and that changes with the lot table: **at today's live lots only K6 and A6 trade NY-PM, both on the negative side, and the live-lot stack delta is -0.1k to +0.1k L6M (inside MDE 0.6-0.9k)**.
* **Added to the Sunday composite it is nothing**: +0.7k L6M, -0.2k HOLD, -2.5k PRE, +2.9k X' at research lots (MDE about 4.8k); live lots -0.1k / -0.1k / -0.3k / +0.3k.
* **Weeks to a forward read** (weekly SD of the stack delta from the L6M MDE; detect the point estimate at 2.8 SE, then at half of it, the shrunk size): alone on the old stack at research lots 27 weeks (110 weeks at half the effect); live + S6 W6 lots 95 / 378 weeks; Sunday composite at research lots about 1,300 weeks, at live lots about 1,200 weeks: **a forward read on the stack line is not reachable in a year; the register can only read the per-book signal level**: P6 alone has about 1.1 blocked signals per week (skipped P&L -16.7 pts per signal in L6M, SE not yet computed for a week count), U6 0.14 per week; no per-book week count was computed, so none is claimed. Status words as the runbook: TOO EARLY for the first 13 weeks; no harm / futility call before.
* Not done: Option B (flatten at 14:40), order-time blocking for P6, and the add-leg treatment were not scored. Slippage labels (+0.25 / +0.45 per add lot) do not enter a skip of the whole entry on the market base; the composite rows use the +0.25 integer split.

