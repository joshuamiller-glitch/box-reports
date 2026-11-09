# DS3_TH_STATE_C - program C (L2 profit) on the TH-L2-S base S1-COMB
**INTERIM - S1 timer-close, superseded by T-TH-EXHAUST; interim (X4 partial: 31 of 33 months run, reference rows K7/M7/A7/H7/O7 incomplete; D6 composite and per-session overrides not run).**
**Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched; the per-book COMB procedure fails the out-of-sample walk-forward (DS3_TH_STATE.md section 5) so S1-COMB is an in-sample base**

Prereg: autopilot/DS3_TH_STATE_CD_PREREG.md (sha256 and addendum 1 in DECISIONS.md, logged before any S2-CD number). Research only, nothing live, no PASS claims. USD per week at the trade lots, net of the 4.84 fee proxy, carrying week dropped (single largest-|delta| ISO week of the window), selection data through 2026-10-31; windows L1M/L2M/L3M/L6M/HOLD as of 2026-10-31, MID, PRE, X'; `mean (mde)` = weekly mean delta and 2.8 sd/sqrt(n). Code: code/th_redo/state_profit.py (engine subclass), code/th_state_cd/ (screens, nulls, report). Private tree /mnt/l2/l2vast/_th_state/s2/CD/.

## 1. Answer first
**Every book gets a rule below; none of the 7 books ENTER** (ENTER = engine cascade beats S1-COMB on L6M AND PRE with the carrying week dropped and L6M above its MDE, drawdown-first not worse, placebo p<=.10, family p<=.10, purged walk-forward positive in L6M and PRE, held-out live week not negative). The S1-COMB base has **zero** profit-side exits in all 43 months (live ThL2 profit is OFF and the live policy file carries no profit lines in the replica), so S1-COMB equals "state cut + plain 60/60 brackets" and a profit rule is tested against exactly that.

| book | best C rule (engine-tested, best S = min(L6M, PRE) vs S1-COMB) | set | engine vs S1-COMB L6M / PRE (mde) | vs PLAIN6060 L6M / PRE | first-order S / nfire | placebo p / family p / WF | live week USD (fires) | verdict |
|---|---|---|---|---|---|---|---|---|
| K7 | F3 lock-to-breakeven: once unreal >= 0.8 x target the protective level is entry+2 pt, market exit when the mid touches it | C0 | +187 (1962) / -656 (1067) | +1366 / -609 | -466 / 580 | 0.003 / 1.000 / neg | -1938 (8) | no (L6M/PRE not both positive vs S1-COMB; drawdown-first worse; family p 1.000; purged walk-forward not positive; live week -1938) |
| P7 | F1 thick-book: ahead_rel >= 1.5 for 30 s once unreal >= 45 pt -> TIGHTEN, trail 20 pt behind the favourable mid extreme (ratchets) | C0 | +118 (318) / +4 (706) | +9814 / +1985 | +0 / 41 | 0.009 / 1.000 / neg | +0 (0) | no (L6M below its MDE; drawdown-first worse; family p 1.000; purged walk-forward not positive) |
| M7 | F1 thick-book: tot_rel >= 1.3 for 3 s once unreal >= 45 pt -> TIGHTEN, trail 20 pt behind the favourable mid extreme (ratchets) | C0 | +136 (1151) / -125 (558) | -175 / +66 | -186 / 310 | 0.001 / 1.000 / neg | +1008 (2) | no (L6M/PRE not both positive vs S1-COMB; drawdown-first worse; family p 1.000; purged walk-forward not positive) |
| U7 | scale-out: half of the lots (floor; inert on 1-lot positions) exits at a nominal limit at 0.8 x target | X2 | -199 (988) / -154 (585) | -80 / -87 | -11 / 638 | 1.000 / 1.000 / neg | -725 (2) | no (L6M/PRE not both positive vs S1-COMB; placebo p 1.000; family p 1.000; purged walk-forward not positive; live week -725) |
| A7 | F1 thick-book: tot_rel >= 1.5 for 30 s once unreal >= 15 pt -> TIGHTEN, trail 20 pt behind the favourable mid extreme (ratchets) | C0 | +32 (213) / +0 (221) | +266 / +15 | +8 / 107 | 0.007 / 1.000 / neg | +0 (0) | no (L6M below its MDE; family p 1.000; purged walk-forward not positive) |
| H7 | F1 thick-book: tot_rel (slow base) >= 2.5 for 30 s once unreal >= 15 pt -> TIGHTEN, trail 20 pt behind the favourable mid extreme (ratchets) | X2 | +118 (216) / +14 (100) | +1039 / -52 | +14 / 13 | 0.025 / 1.000 / neg | +0 (0) | no (L6M below its MDE; family p 1.000; purged walk-forward not positive) |
| O7 | F3 lock-to-breakeven: once unreal >= 0.7 x target the protective level is entry+2 pt, market exit when the mid touches it | C0 | +80 (268) / +26 (100) | +184 / +5 | +26 / 41 | 0.001 / 1.000 / neg | +436 (1) | no (L6M below its MDE; family p 1.000; purged walk-forward not positive) |
| X3/X4/X5 | pooled-all-books fallback: F4 scale-out half of the lots at 80% of target (nominal limit) | - | not engine-testable (no X book trades in the S1 lists; 8 X trades in the PROFIT-STATE sample) | - | S +1784 | - | - | fallback `*` line, no evidence |

Reading: the engine deltas against S1-COMB are all inside their MDEs; see section 5 for the L6M/PRE/X' split and the cross-book spill-over (the "ALL" row).

## 2. Base, reference rows and the partial-exit subclass
- Base S1-COMB: replica engine (ITER14_PRM), per-book state cut TH-L2-S, 43 months 2023-04..2026-10 (TH_STATE_BASE_S1.md). Reference rows on the same base: **S1-COMB** itself (zero profit exits in 43 months, exits: Target 9527, StateCut 6694, Stop/StopJoin 3834, StackCut 435, TimeBlock 359, BookLock 213), **S1-COMB-PO** (state cut with the engine profit side forced off; 5 months re-run, trade lists identical column by column, so S1-COMB == S1-COMB-PO), **PLAIN6060** (no TH of any kind). "No cut" is not used as a candidate or verdict.
- **Partial exit (scale-out) is now supported** in a new subclass `StateProfitRep(StateBaseRep)` in code/th_redo/state_profit.py (sim.py, adapter_replica.py, rules_replica.py, state_base.py untouched): the half position exits at a nominal limit the first print that touches entry + side x pct x target (`exec_exit` with `qty = pos_qty // 2`, no price improvement, no latency, inert on 1-lot positions); the remainder keeps the bracket and the state cut; optional runner trail (D5). The engine already carried partial-quantity bookkeeping (StackCut partial, partial target fills), so only the trigger is new. Per-book rule dispatch (rule swapped per book inside manage_th_l2/manage_policy) and the PROFIT-STATE 1-s state-feature cells (`profcut`, market exit at mid(s+1) -+ 0.80) are in the same subclass.
- **Regression (scale-out off changes nothing)**: with no candidates (REG, 202304) and with inert scale-out + inert state cells on all books (REGOFF, 202305) the trade lists equal S1-COMB in every column; with the PLAIN6060 rule + inert cells (REGPLAIN, 202305, 249 trades) equal to the stored PLAIN6060 run; with the never-cut rule + inert cells (REGNOCUT, 202305, 249 trades) equal to the stored never-cut run. Zero scale-outs / profit cuts fired in those runs.

## 3. Tier S: first order on the exact 1-s path of the S1-COMB trade list (all 715 cells; best 3 per book by tier)
Decision at the end of second s from the 1-s tape/state, 1 s latency, market exit at mid(s+1) -+ 0.80, scale-out limits nominal; delta = rule exit minus the S1-COMB exit when the rule fires before it. Tiers: E1 recents (L3M and L6M > 0, L1M/L2M not below -0.5 MDE) + tolerant (PRE and X' >= -0.5 MDE) + drawdown first; E2 tolerant + dd; E3 dd; E4 any (nfire >= 30; 10 for A7/H7/O7). `S` = min(L6M, PRE).

| book | cell | tier | rule | S | L6M | PRE | X' | nfire |
|---|---|---|---|---|---|---|---|---|
| K7 | 713 | E1 | F4 scale-out half of the lots at 70% of target (nominal limit) | -47 | +67 | -47 | +114 | 602 |
| K7 | 710 | E1 | F4 scale-out half of the lots at 40% of target (nominal limit) | -90 | +328 | -90 | +248 | 759 |
| K7 | 711 | E1 | F4 scale-out half of the lots at 50% of target (nominal limit) | -182 | +472 | -182 | +229 | 700 |
| P7 | 676 | E1 | F2 take when unreal >= 0.70 x target and pulled_mult(10 s) >= 20 | +1947 | +3343 | +1947 | -401 | 2431 |
| P7 | 714 | E1 | F4 scale-out half of the lots at 80% of target (nominal limit) | +1725 | +3151 | +1725 | +502 | 2585 |
| P7 | 664 | E1 | F2 take when unreal >= 0.70 x target and ahead_rel(slow base) >= 1.5 | +1025 | +2198 | +1025 | -1474 | 2393 |
| M7 | 399 | E1 | F1 thick-book ahead_rel >= 1.5 for 3 s once unreal >= 45 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme | -128 | +128 | -128 | -48 | 285 |
| M7 | 682 | E1 | F3 lock-to-breakeven: once unreal >= 0.2 x target move stop to entry+2 pt; market exit when mid touches | -183 | +414 | -183 | -109 | 2735 |
| M7 | 51 | E1 | F1 thick-book tot_rel >= 1.3 for 3 s once unreal >= 30 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme | -287 | +185 | -287 | +318 | 992 |
| U7 | 714 | E1 | F4 scale-out half of the lots at 80% of target (nominal limit) | -11 | +345 | -11 | -206 | 638 |
| U7 | 657 | E1 | F2 take when unreal >= 0.50 x target and ice_against >= 1 | -205 | +45 | -205 | -316 | 818 |
| U7 | 704 | E1 | F3 lock-to-breakeven: once unreal >= 0.7 x target move stop to entry+10 pt; market exit when mid touches | -254 | +858 | -254 | -352 | 262 |
| A7 | 335 | E1 | F1 thick-book ahead_rel >= 2.5 for 30 s once unreal >= 15 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme | -9 | +23 | -9 | +54 | 33 |
| A7 | 22 | E1 | F1 thick-book tot_rel >= 1.5 for 30 s once unreal >= 15 pt -> TIGHTEN trail 40 ticks (10.0 pt) behind favourable mid extreme | -35 | +188 | -35 | -137 | 126 |
| A7 | 33 | E1 | F1 thick-book tot_rel >= 2.0 for 30 s once unreal >= 15 pt -> TIGHTEN trail 20 ticks (5.0 pt) behind favourable mid extreme | -37 | +180 | -37 | -11 | 47 |
| H7 | 191 | E1 | F1 thick-book tot_rel(slow base) >= 2.5 for 30 s once unreal >= 15 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme | +14 | +111 | +14 | +117 | 13 |
| H7 | 35 | E1 | F1 thick-book tot_rel >= 2.0 for 30 s once unreal >= 15 pt -> TIGHTEN trail 80 ticks (20.0 pt) behind favourable mid extreme | -37 | +111 | -37 | +31 | 19 |
| H7 | 185 | E1 | F1 thick-book tot_rel(slow base) >= 2.5 for 10 s once unreal >= 15 pt -> TIGHTEN trail 20 ticks (5.0 pt) behind favourable mid extreme | -71 | +52 | -71 | +52 | 50 |
| O7 | 702 | E1 | F3 lock-to-breakeven: once unreal >= 0.7 x target move stop to entry+2 pt; market exit when mid touches | +26 | +80 | +26 | -19 | 41 |
| O7 | 701 | E1 | F3 lock-to-breakeven: once unreal >= 0.7 x target move stop to entry+0 pt; market exit when mid touches | +18 | +68 | +18 | -25 | 40 |
| O7 | 205 | E1 | F1 thick-book tot_rel(slow base) >= 1.5 for 3 s once unreal >= 30 pt -> TIGHTEN trail 20 ticks (5.0 pt) behind favourable mid extreme | -79 | +38 | -79 | +58 | 104 |

Nulls: placebo = k random trades with an eligible second (the cell's own arming level; mode "armed" = any later second for pull-back exits) and a random eligible exit, 1000 draws, shared world seeds; family = Westfall-Young max-stat over every full-exit cell of the book (200 worlds, each cell keeps its own fired set); scale-out cells: placebo = half-lot random exits of the same count, family by Bonferroni over the scale-out cells. Purged walk-forward = monthly, best trailing-52-week S cell among all cells applied to the next month, 2024-01..2026-10.

## 4. Engine cascade: every finalist rule on top of the S1-COMB state cut (43 months; X4 = 2024-02..2026-10 only)
Per-book rules are run together in one engine run per set (each book carries its own rule, the other books keep S1-COMB behaviour), so a book's delta is cascaded: re-entries, locks, caps and the stack cut spill across books (see the ALL row). Sets: C0 = the 8 PROFIT-STATE per-book rules (prereg), X2 = C re-screen picks (P7, H7, A7, U7) + D extras (K7, M7), D1 = the D per-book best, X4 = D extras (P7, U7) + the live reference rows (K7, M7, A7, H7, O7).

### K7
**K7 cell 706, set C0** - F3 lock-to-breakeven: once unreal >= 0.8 x target the protective level is entry+2 pt, market exit when the mid touches it

Policy-file line: `profit K7 * pct>=0.80 lock 2`

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | -423 (3192) | +136 (2530) | +213 (1781) | +187 (1962) | +34 (1421) | -774 (2053) | -656 (1067) | -236 (1214) |
| engine delta vs S1-COMB (week not dropped) | -423 (3192) | +1500 (4425) | +1152 (3097) | +657 (2299) | +283 (1558) | -1155 (2156) | -831 (1161) | -433 (1308) |
| engine delta vs PLAIN6060 | +1971 (8432) | +2094 (5206) | +1926 (3949) | +1366 (3132) | +769 (2299) | -135 (3217) | -609 (1493) | -557 (1248) |
| first order vs S1-COMB paths | +474 (3239) | +1081 (2220) | +818 (1753) | +516 (1384) | +85 (987) | -1331 (2130) | -466 (642) | -98 (748) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 40291 -> 22238, PRE 23120 -> 24630; stack ("ALL") delta L6M +542, PRE -845. Verdict: **no** (L6M/PRE not both positive vs S1-COMB; drawdown-first worse; family p 1.000; purged walk-forward not positive; live week -1938).
First order: tier E3, S -466, fires 580, placebo p 0.003 (random-exit mean S -926), family p 1.000 (random-exit-world max-cell (200 worlds, own arming level)), purged walk-forward L6M -317 / PRE -691 -> not positive; drawdown base -> rule L6M 38406 -> 27226, PRE 22555 -> 20832. By entry session (this cell): s0 L6M +155 PRE -66 n 210; s1 L6M +126 PRE -79 n 145; s3 L6M +99 PRE -101 n 135; s4 L6M -89 PRE -47 n 90.

### P7
**P7 cell 407, set C0** - F1 thick-book: ahead_rel >= 1.5 for 30 s once unreal >= 45 pt -> TIGHTEN, trail 20 pt behind the favourable mid extreme (ratchets)

Policy-file line: `profit P7 * pct>=0.75 ahead_rel>=1.5 tighten 20   # + persist=30s (field missing)`

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | +22 (63) | +1 (2) | +0 (1) | +118 (318) | -312 (757) | -107 (299) | +4 (706) | +98 (1064) |
| engine delta vs S1-COMB (week not dropped) | +22 (63) | +13 (35) | +9 (24) | -375 (1416) | -551 (999) | -439 (969) | +184 (861) | -109 (1190) |
| engine delta vs PLAIN6060 | +6236 (9884) | +2417 (11580) | +7062 (10659) | +9814 (9674) | +6658 (7061) | -1627 (13598) | +1985 (4194) | +1085 (3326) |
| first order vs S1-COMB paths | +0 (0) | +0 (0) | +0 (0) | +0 (0) | -383 (447) | +0 (0) | +63 (584) | -294 (862) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 48027 -> 48027, PRE 119255 -> 120643; stack ("ALL") delta L6M +542, PRE -845. Verdict: **no** (L6M below its MDE; drawdown-first worse; family p 1.000; purged walk-forward not positive).
First order: tier E4, S +0, fires 41, placebo p 0.009 (random-exit mean S -289), family p 1.000 (random-exit-world max-cell (200 worlds, own arming level)), purged walk-forward L6M +2348 / PRE -827 -> not positive; drawdown base -> rule L6M 48027 -> 48027, PRE 119255 -> 123858. By entry session (this cell): s0 L6M +0 PRE +116 n 29; s1 L6M +0 PRE +0 n 7; s3 L6M +0 PRE +0 n 5.

**P7 cell 676, set X2** - F2 gated take: unreal >= 0.7 x target and pulled_mult10 >= 20 -> TAKE at market

Policy-file line: `profit P7 * pct>=0.70 pulled_mult10>=20 take`

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | -4591 (11491) | -3465 (16654) | -984 (12012) | -2929 (10264) | -4136 (6238) | -3100 (6489) | +396 (4456) | -1074 (2852) |
| engine delta vs S1-COMB (week not dropped) | -4591 (11491) | +82 (17730) | +1345 (12831) | -4149 (10436) | -3254 (6597) | -657 (9050) | -262 (4766) | -1372 (2909) |
| engine delta vs PLAIN6060 | +1623 (18650) | -332 (21799) | +6243 (17077) | +4962 (14051) | +4076 (9361) | +5322 (13874) | +272 (5528) | -192 (4214) |
| first order vs S1-COMB paths | +5127 (14402) | -302 (16182) | +3944 (13214) | +3343 (9732) | +3299 (6116) | +3677 (8231) | +1947 (3819) | -401 (2955) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 48027 -> 45583, PRE 119255 -> 135093; stack ("ALL") delta L6M -6788, PRE -2102. Verdict: **no** (L6M/PRE not both positive vs S1-COMB; drawdown-first worse; placebo p 1.000; family p 1.000; purged walk-forward not positive; live week -26622).
First order: tier E1, S +1947, fires 2431, placebo p 1.000 (random-exit mean S +4937), family p 1.000 (random-exit-world max-cell (200 worlds, own arming level)), purged walk-forward L6M +2348 / PRE -827 -> not positive; drawdown base -> rule L6M 48027 -> 32052, PRE 119255 -> 73910. By entry session (this cell): s0 L6M +1810 PRE +913 n 1095; s1 L6M -179 PRE +926 n 776; s3 L6M +683 PRE -264 n 560.

### M7
**M7 cell 99, set C0** - F1 thick-book: tot_rel >= 1.3 for 3 s once unreal >= 45 pt -> TIGHTEN, trail 20 pt behind the favourable mid extreme (ratchets)

Policy-file line: `profit M7 * pct>=0.75 tot_rel>=1.3 tighten 20   # + persist=3s (field missing)`

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | +785 (2520) | +195 (2189) | +575 (1765) | +136 (1151) | -64 (706) | -309 (914) | -125 (558) | -298 (616) |
| engine delta vs S1-COMB (week not dropped) | +785 (2520) | +661 (2331) | +172 (1976) | -48 (1221) | +30 (740) | -483 (967) | -216 (607) | -165 (707) |
| engine delta vs PLAIN6060 | +1522 (2665) | +1494 (2219) | +935 (2709) | -175 (2210) | -544 (1818) | +230 (4649) | +66 (1228) | -370 (1066) |
| first order vs S1-COMB paths | +1131 (1525) | +412 (1213) | +394 (1118) | +148 (967) | -8 (639) | -236 (854) | -186 (375) | -69 (521) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 52052 -> 55658, PRE 28279 -> 29612; stack ("ALL") delta L6M +542, PRE -845. Verdict: **no** (L6M/PRE not both positive vs S1-COMB; drawdown-first worse; family p 1.000; purged walk-forward not positive).
First order: tier E4, S -186, fires 310, placebo p 0.001 (random-exit mean S -513), family p 1.000 (random-exit-world max-cell (200 worlds, own arming level)), purged walk-forward L6M -829 / PRE -781 -> not positive; drawdown base -> rule L6M 52052 -> 51635, PRE 28279 -> 31871. By entry session (this cell): s1 L6M -210 PRE -166 n 211; s3 L6M -36 PRE -70 n 99.

### U7
**U7 cell 712, set C0** - scale-out: half of the lots (floor; inert on 1-lot positions) exits at a nominal limit at 0.6 x target

Policy-file line: `profit U7 * pct>=0.60 scale 0.5   # NEW ACTION `scale <fraction>` (partial exit at a limit)`

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | +8 (3100) | -961 (2447) | -219 (1772) | -585 (1304) | -592 (981) | -1069 (1903) | -175 (795) | -132 (694) |
| engine delta vs S1-COMB (week not dropped) | +8 (3100) | -373 (2714) | -535 (1854) | -728 (1316) | -682 (994) | -1420 (1996) | -72 (836) | -216 (718) |
| engine delta vs PLAIN6060 | +647 (3776) | -892 (3008) | -804 (1821) | -1271 (1604) | -946 (1256) | -754 (2532) | -108 (846) | -150 (697) |
| first order vs S1-COMB paths | +438 (2991) | -550 (2634) | -275 (1809) | -134 (1587) | -146 (1099) | -186 (2067) | +22 (809) | -228 (726) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 24202 -> 20419, PRE 39175 -> 32097; stack ("ALL") delta L6M +542, PRE -845. Verdict: **no** (L6M/PRE not both positive vs S1-COMB; placebo p 1.000; family p 1.000; purged walk-forward not positive; live week -1445).
First order: tier E2, S -134, fires 736, placebo p 1.000 (random-exit mean S +533), family p 1.000 (Bonferroni over 6 scale-out cells), purged walk-forward L6M -291 / PRE +168 -> not positive; drawdown base -> rule L6M 28505 -> 25800, PRE 39175 -> 32029. By entry session (this cell): s0 L6M -421 PRE +15 n 393; s1 L6M +19 PRE -79 n 343.

**U7 cell 714, set X2** - scale-out: half of the lots (floor; inert on 1-lot positions) exits at a nominal limit at 0.8 x target

Policy-file line: `profit U7 * pct>=0.80 scale 0.5   # NEW ACTION `scale <fraction>` (partial exit at a limit)`

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | +731 (2321) | -71 (1907) | -162 (1134) | -199 (988) | -201 (784) | -793 (1246) | -154 (585) | -275 (507) |
| engine delta vs S1-COMB (week not dropped) | +731 (2321) | +336 (2031) | +114 (1299) | -50 (1037) | -88 (831) | -947 (1216) | -38 (662) | -177 (566) |
| engine delta vs PLAIN6060 | +1371 (2937) | -2 (2860) | +639 (1519) | -80 (1483) | -31 (1245) | -175 (2391) | -87 (697) | -293 (521) |
| first order vs S1-COMB paths | +658 (2248) | -144 (1840) | +60 (1325) | +345 (1214) | +254 (813) | -402 (1259) | -11 (593) | -206 (525) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 15198 -> 10869, PRE 39175 -> 31235; stack ("ALL") delta L6M -6788, PRE -2102. Verdict: **no** (L6M/PRE not both positive vs S1-COMB; placebo p 1.000; family p 1.000; purged walk-forward not positive; live week -725).
First order: tier E1, S -11, fires 638, placebo p 1.000 (random-exit mean S +67), family p 1.000 (Bonferroni over 6 scale-out cells), purged walk-forward L6M -291 / PRE +168 -> not positive; drawdown base -> rule L6M 15198 -> 10965, PRE 39175 -> 31237. By entry session (this cell): s0 L6M +161 PRE -163 n 343; s1 L6M +8 PRE +74 n 295.

### A7
**A7 cell 23, set C0** - F1 thick-book: tot_rel >= 1.5 for 30 s once unreal >= 15 pt -> TIGHTEN, trail 20 pt behind the favourable mid extreme (ratchets)

Policy-file line: `profit A7 * pct>=0.25 tot_rel>=1.5 tighten 20   # + persist=30s (field missing)`

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | +590 (1653) | -29 (82) | +45 (270) | +32 (213) | +63 (288) | -76 (656) | +0 (221) | -88 (388) |
| engine delta vs S1-COMB (week not dropped) | +590 (1653) | +302 (930) | +268 (673) | +144 (375) | +119 (323) | +174 (921) | -27 (231) | -28 (415) |
| engine delta vs PLAIN6060 | +287 (1409) | -154 (743) | +208 (765) | +266 (688) | +202 (443) | +68 (444) | +15 (277) | -93 (398) |
| first order vs S1-COMB paths | +351 (984) | +0 (0) | -35 (302) | +154 (308) | +94 (285) | +25 (260) | +8 (197) | -51 (384) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 8059 -> 7211, PRE 7300 -> 5954; stack ("ALL") delta L6M +542, PRE -845. Verdict: **no** (L6M below its MDE; family p 1.000; purged walk-forward not positive).
First order: tier E2, S +8, fires 107, placebo p 0.007 (random-exit mean S -194), family p 1.000 (random-exit-world max-cell (200 worlds, own arming level)), purged walk-forward L6M -133 / PRE -201 -> not positive; drawdown base -> rule L6M 8059 -> 7211, PRE 7300 -> 5954. By entry session (this cell): s0 L6M +154 PRE +8 n 107.

**A7 cell 335, set X2** - F1 thick-book: ahead_rel >= 2.5 for 30 s once unreal >= 15 pt -> TIGHTEN, trail 20 pt behind the favourable mid extreme (ratchets)

Policy-file line: `profit A7 * pct>=0.25 ahead_rel>=2.5 tighten 20   # + persist=30s (field missing)`

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | +0 (0) | +0 (0) | +27 (242) | -24 (150) | +62 (163) | +64 (179) | -41 (97) | +63 (215) |
| engine delta vs S1-COMB (week not dropped) | +0 (0) | +0 (0) | -41 (293) | +20 (189) | +16 (205) | -135 (580) | -11 (129) | +120 (264) |
| engine delta vs PLAIN6060 | -303 (1778) | -50 (852) | +204 (732) | +136 (681) | +97 (450) | -262 (639) | +32 (242) | +59 (234) |
| first order vs S1-COMB paths | +0 (0) | +0 (0) | +27 (242) | +23 (197) | +41 (133) | +0 (0) | -9 (94) | +54 (203) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 8059 -> 7211, PRE 7300 -> 7300; stack ("ALL") delta L6M -6788, PRE -2102. Verdict: **no** (L6M/PRE not both positive vs S1-COMB; family p 1.000; purged walk-forward not positive).
First order: tier E1, S -9, fires 33, placebo p 0.085 (random-exit mean S -79), family p 1.000 (random-exit-world max-cell (200 worlds, own arming level)), purged walk-forward L6M -133 / PRE -201 -> not positive; drawdown base -> rule L6M 8059 -> 7211, PRE 7300 -> 7300. By entry session (this cell): s0 L6M +23 PRE -9 n 33.

### H7
**H7 cell 714, set C0** - scale-out: half of the lots (floor; inert on 1-lot positions) exits at a nominal limit at 0.8 x target

Policy-file line: `profit H7 * pct>=0.80 scale 0.5   # NEW ACTION `scale <fraction>` (partial exit at a limit)`

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | -129 (1103) | -422 (279) | -269 (407) | -97 (410) | -55 (303) | +200 (724) | -177 (279) | +182 (537) |
| engine delta vs S1-COMB (week not dropped) | -129 (1103) | -231 (587) | -149 (503) | -158 (429) | +3 (340) | +362 (802) | -97 (355) | +363 (729) |
| engine delta vs PLAIN6060 | +2423 (2472) | +1664 (2228) | +1932 (1836) | +891 (1813) | +711 (1264) | +1612 (2669) | -117 (691) | +234 (604) |
| first order vs S1-COMB paths | +594 (2107) | -38 (658) | -13 (532) | -55 (472) | +66 (370) | +221 (763) | -55 (298) | +95 (487) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 8078 -> 8078, PRE 19246 -> 19311; stack ("ALL") delta L6M +542, PRE -845. Verdict: **no** (L6M/PRE not both positive vs S1-COMB; drawdown-first worse; placebo p 1.000; family p 1.000; purged walk-forward not positive).
First order: tier E2, S -55, fires 268, placebo p 1.000 (random-exit mean S +14), family p 1.000 (Bonferroni over 6 scale-out cells), purged walk-forward L6M -1200 / PRE -615 -> not positive; drawdown base -> rule L6M 8078 -> 8078, PRE 19246 -> 19246. By entry session (this cell): s0 L6M -55 PRE -55 n 268; s3 L6M +0 PRE +0 n 0.

**H7 cell 191, set X2** - F1 thick-book: tot_rel (slow base) >= 2.5 for 30 s once unreal >= 15 pt -> TIGHTEN, trail 20 pt behind the favourable mid extreme (ratchets)

Policy-file line: `profit H7 * pct>=0.25 tot_rel_slow>=2.5 tighten 20   # + persist=30s (field missing); slow-base feature is not in the D7 grammar`

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | +0 (0) | +0 (0) | +129 (321) | +118 (216) | +83 (124) | +0 (0) | +14 (100) | +107 (238) |
| engine delta vs S1-COMB (week not dropped) | +0 (0) | +0 (0) | -11 (492) | +48 (285) | +49 (155) | +10 (27) | -30 (157) | -22 (428) |
| engine delta vs PLAIN6060 | +2551 (1918) | +1894 (2030) | +2061 (1609) | +1039 (1689) | +757 (1105) | +1227 (2092) | -52 (613) | +158 (330) |
| first order vs S1-COMB paths | +0 (0) | +0 (0) | +115 (322) | +111 (216) | +24 (144) | +0 (0) | +14 (100) | +117 (235) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 8078 -> 8078, PRE 19246 -> 19246; stack ("ALL") delta L6M -6788, PRE -2102. Verdict: **no** (L6M below its MDE; family p 1.000; purged walk-forward not positive).
First order: tier E1, S +14, fires 13, placebo p 0.025 (random-exit mean S +nan), family p 1.000 (random-exit-world max-cell (200 worlds, own arming level)), purged walk-forward L6M -1200 / PRE -615 -> not positive; drawdown base -> rule L6M 8078 -> 8078, PRE 19246 -> 19246. By entry session (this cell): s0 L6M +111 PRE +8 n 12; s3 L6M +0 PRE +0 n 1.

### O7
**O7 cell 702, set C0** - F3 lock-to-breakeven: once unreal >= 0.7 x target the protective level is entry+2 pt, market exit when the mid touches it

Policy-file line: `profit O7 * pct>=0.70 lock 2`

| row | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| engine delta vs S1-COMB (carry week dropped) | +141 (396) | +88 (247) | +59 (165) | +80 (268) | -79 (245) | +46 (130) | +26 (100) | -19 (230) |
| engine delta vs S1-COMB (week not dropped) | +141 (396) | -111 (599) | -77 (409) | +4 (335) | -117 (262) | -109 (452) | +1 (120) | -60 (252) |
| engine delta vs PLAIN6060 | +209 (476) | +292 (307) | +228 (221) | +184 (280) | -2 (270) | +36 (526) | +5 (220) | -24 (271) |
| first order vs S1-COMB paths | +141 (396) | +88 (247) | +59 (165) | +80 (268) | -79 (245) | +46 (130) | +26 (100) | -19 (230) |

Engine drawdown (weekly, kept weeks) base -> rule: L6M 8943 -> 8923, PRE 4562 -> 3941; stack ("ALL") delta L6M +542, PRE -845. Verdict: **no** (L6M below its MDE; family p 1.000; purged walk-forward not positive).
First order: tier E1, S +26, fires 41, placebo p 0.001 (random-exit mean S -73), family p 1.000 (random-exit-world max-cell (200 worlds, own arming level)), purged walk-forward L6M +192 / PRE -39 -> not positive; drawdown base -> rule L6M 8943 -> 8923, PRE 4562 -> 3941. By entry session (this cell): s3 L6M +80 PRE +26 n 41.

## 5. Held-out live week (2026-11-01 evening .. 11-05, 187 live trades; csv sha256 424c68da934136df7124004b4b1fd9a34952a1e5e3e6ba1017ad0d972a927112)
Each rule applied on the live 1-s path from the live entry fill to the ACTUAL live exit (first order, live lots): delta = rule exit points (mid(s+1) -+ 0.80, scale-out nominal) minus live exit points, only where the rule fires before the live exit. Reported, never selected on; trades whose exit lies beyond the tape end (2026-11-05 15:25 UTC) are excluded.

| book | cell | rule | trades | fires | delta USD | better | worse | live gross USD |
|---|---|---|---|---|---|---|---|---|
| K7 | 706 | F3 lock-to-breakeven: once unreal >= 0.8 x target the protective level is entry+2 pt, market exit when the mid | 64 | 8 | -1938 | 5 | 3 | +14845 |
| P7 | 407 | F1 thick-book: ahead_rel >= 1.5 for 30 s once unreal >= 45 pt -> TIGHTEN, trail 20 pt behind the favourable mi | 52 | 0 | +0 | 0 | 0 | +79302 |
| M7 | 99 | F1 thick-book: tot_rel >= 1.3 for 3 s once unreal >= 45 pt -> TIGHTEN, trail 20 pt behind the favourable mid e | 28 | 2 | +1008 | 1 | 1 | +6738 |
| U7 | 712 | scale-out: half of the lots (floor; inert on 1-lot positions) exits at a nominal limit at 0.6 x target | 6 | 2 | -1445 | 0 | 2 | +624 |
| A7 | 23 | F1 thick-book: tot_rel >= 1.5 for 30 s once unreal >= 15 pt -> TIGHTEN, trail 20 pt behind the favourable mid  | 23 | 0 | +0 | 0 | 0 | -1415 |
| H7 | 714 | scale-out: half of the lots (floor; inert on 1-lot positions) exits at a nominal limit at 0.8 x target | 3 | 0 | +0 | 0 | 0 | -775 |
| O7 | 702 | F3 lock-to-breakeven: once unreal >= 0.7 x target the protective level is entry+2 pt, market exit when the mid | 3 | 1 | +436 | 1 | 0 | +660 |
| P7 | 676 | F2 gated take: unreal >= 0.7 x target and pulled_mult10 >= 20 -> TAKE at market | 52 | 29 | -26622 | 2 | 27 | +79302 |
| H7 | 191 | F1 thick-book: tot_rel (slow base) >= 2.5 for 30 s once unreal >= 15 pt -> TIGHTEN, trail 20 pt behind the fav | 3 | 0 | +0 | 0 | 0 | -775 |
| A7 | 335 | F1 thick-book: ahead_rel >= 2.5 for 30 s once unreal >= 15 pt -> TIGHTEN, trail 20 pt behind the favourable mi | 23 | 0 | +0 | 0 | 0 | -1415 |
| U7 | 714 | scale-out: half of the lots (floor; inert on 1-lot positions) exits at a nominal limit at 0.8 x target | 6 | 2 | -725 | 0 | 2 | +624 |
One week is not evidence; the table is a held-out sanity check only.

## 6. Policy-file grammar gaps (D7 grammar)
- `persist=<s>` (condition true for N consecutive seconds) is missing on profit lines; the per-rule pulled window (pulled_mult over 5 or 10 s per line), the slow-base relative depth features (tot_rel/ahead_rel on a ~2-day slot baseline), `scale <fraction>` (partial exit at a limit) and the entry-session scope (rules here are per book; session overrides were not searched) are not in the grammar; `lots` as a feature is not needed by these rules.

## 7. Caveats
(1) Entries are replica-engine entries, not live-matched (about 100 of 187 blind-week trades match). (2) Base S1-COMB is an in-sample base: the per-book state cut fails its out-of-sample walk-forward, so every delta here is conditional on that cut. (3) First order scores each trade on the S1-COMB path alone; re-entries after a profit exit only exist in the engine cascade. (4) Scale-out and target-shrink limits fill at the nominal level on touch (no queue); the engine target fills with cumvol, so first-order scale-out is optimistic against the live queue. (5) The engine runs per-book rules together; cross-book spill-over is in the ALL row. (6) D1 votes use 1-s mids in Tier S but 100-ms print samples in the engine. (7) Placebo/family nulls are "random exit of the same count" nulls at the cell's own arming level and are lenient for early-take rules; read them together with the engine deltas and the walk-forward. (8) The live-week table is one week (first order). (9) Per-session overrides were not searched. (10) X3/X4/X5 never trade in the S1 engine lists, the pooled fallback has no evidence.
