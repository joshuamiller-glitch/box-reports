# USER ORDER: OVERNIGHT ORDER 2026-10-31 22:00Z -> Sun 17:00Z (saved verbatim)

OVERNIGHT ORDER 2026-10-31 22:00Z → Sun 17:00Z — DRAWDOWN FIRST, FIND WHAT WAS THROWN AWAY, BUILD THE HEDGE SIDE (user)

This is a command, not a menu. 10 agents, ≥ 90% CPU, continuously, until Sun 12:00 ET. "Queue 0" is a failure state: when a section finishes, the lead starts the next one in this list immediately, then the filler queue. Every result on the DRAWDOWN-FIRST standard (maxDD, worst-20, SD, Calmar, equal-risk line, same-volume placebo, RISK-KEEP label) with mean and MDE as columns, recent-first, session column, three columns STRICT / TOLERANT / NOW-ONLY. Rows to RECENT_WINS. MORNING.md every 2 h with load, agents, and the one sentence per section. DS3_SUNDAY_BRIEF v7 at 12:00Z and final at 17:00Z with a DRAWDOWN section and a NEW-THIS-NIGHT section. Nothing found tonight goes live Sunday; it goes into the brief as Shadow with its D6/D7 mapping.

A. DEAD-REREAD UNDER DRAWDOWN FIRST (the biggest lever; start first; 4 agents)

Every program this week killed rules on the mean. The user's measure is drawdown. Re-read the DEAD_CELLS and UF_TRIALS ledgers (all ~2.5M cells; sample by family if the full pass cannot finish by 10:00Z, state the sample) and the 14,741-row RECENT-EDGE ledger for rules that LOWER the stack's maxDD or worst-20 at live lots with the mean inside its MDE (not negative beyond MDE): these were never scored as what they are. Known candidates to pick up explicitly: vol-scaled lots (8-wk trailing SD per book, clip 0.5-2: holdout maxDD −68k, SD −8.9k — shelved for failing the mean gate), the equity-curve and halt rules (HALT-RESUME), risk-off states, the quit-when-up variants, the chop-day sizers (TG-1), the NTE states that cut tail, the L2 trade-health loss cuts (the user's live −30/5 s/30× rule included — score ITS drawdown line), the partial-exit stack rules, the day-type sizers. Output: DS3_DD_REREAD.md — the RISK-KEEP table (rule | maxDD before→after | worst-20 | mean (MDE) | equal-risk mean | placebo rank | PRE/X' agree | D6/D7 mapping), top 30 recent-first, and the composite built from the top RISK-KEEPs that do not overlap, with its full risk line vs the Sunday composite.

B. THE 2024-25 PROBLEM (1 agent, then feeds A)

The Sunday composite cuts maxDD 74% in L6M and deepens it 49% in PRE. Diagnose, don't describe: which weeks of PRE carry the deepening; which piece (zone skip / ER sizer / PE confirm) is on in those weeks; what the market was doing (vol tercile, trend persistence, ER state, session mix, book depth, ES correlation, day type); whether a causal state computable at the signal second separates the PRE-bad weeks from the L6M-good weeks. Then the REGIME SWITCH: the composite with each piece gated by that state (piece off when the 2024-25 signature is present), scored on the full history, drawdown first, with the shuffled-state placebo. Deliver: the signature in D6 terms, the gated composite's risk line in every window, and the plain sentence "if 2024-25 comes back, the gated composite's maxDD is X vs Y ungated". DS3_PRE_DIAGNOSIS.md.

C. THE HEDGE SIDE — books that make money when the stack loses (2 agents)

The stack loses 64% of its losing-day dollars on range days and all books lose together in the worst 20 weeks (DIV2 audit). Nothing in the ledger is built to be anti-correlated. Build it: (1) the VWAP-reversion family T-CLOSE found (9 PASS / 4 CANDIDATE under the harness, RVW1 F30 limit-at-touch) and its intraday cousins (VWAP band fades, IB-edge fades, failed-breakout fades, prior-value-area fades from INST A2), scored NOT on their mean but on the STACK's worst-20 and maxDD when added at 1-5 lots: the hedge value. (2) The chop-day book: ex-ante range-day tag at 10:30 (first-hour range < 0.6 × median, ER < 0.3) → run the fade book, halve the trend books; score as one regime-switched stack, drawdown first. (3) The ASSEMBLY portfolio lead (S8 RTY, B1 BTC, Q1CCO NQ, GC sleeve; PORTFOLIO-LEAD YES, clean Sharpe 7.3 is suspicious — audit it first): its weekly correlation with the stack and the stack's worst-20 with it added at the ledger's sizes. DS3_HEDGE_SIDE.md: the table "sleeve | own mean | corr to stack | stack worst-20 before→after | stack maxDD before→after | D7 spec".

D. THE PASS ROWS WE NEVER BUILT (1 agent)

RECENT_WINS carries STRUCT48 PASS rows: Asia 15-min opening-range breakout, 60-pt stop, +25-50k/wk L3M at 0.5-1.0 × Set-A weekly SD, "added beside Set A". Nothing in D6/D7 runs it. For ORB_ASIA_15 (and the 30-min CANDIDATE): the drawdown line added to the Sunday composite at live-scale lots (what lot = 0.5 × Set-A SD at our scale), per-contract L3M/L6M/HOLD/PRE/X', placebo, the exact NT8 spec (bar, window, entry mechanic, stop, target, session, flatten) for a D7 alt-bar slot or a new book, and the honest tier. DS3_ORB_ASIA_D7.md. Same for any other PASS-tier row in the ledger that has no D6/D7 implementation: list them all first (count), then the top 5 by shrunk $.

E. LOTS RE-SOLVED UNDER A DRAWDOWN CONSTRAINT (1 agent)

The live lot table (K6 2 / P6 7 / U6 4 / H6 4-2 / M6 2 / A6 1) was halved by hand. Solve it: per book × session, maximise mean s.t. maxDD ≤ the current composite's maxDD (and ≤ 0.75 × it, and ≤ 0.5 × it), total lots ≤ 20, integer, on the one-convention engine with the Sunday composite's rules, walk-forward (solve on trailing 6 months, score the next month, 2024-26). Report the three lot tables, their risk lines, and what the walk-forward says about re-solving monthly. DS3_LOTS_DD.md.

F. INSTITUTIONAL — finish the list (1 agent, continuous)

Sections C (cross-market at the hour scale), D (vol regime proxies + options quote), E (cash lead on the 1-min set + tick quote), F (flow calendar), H (minute-of-day surface and time-of-day brackets), with the DATA line first and drawdown-first scoring; A2 and the MOC finding already in: the 14:40-15:00 drift (−13..−24 pts into the close in every window) becomes a STANDALONE close-fade book scored on hedge value (section C) as well as a block. DS3_INST_<x>.md each, DS3_INSTITUTIONAL.md rolling.

G. Filler (never idle)

RE-2 section 5 cycles; NO-TRADE-EXPANDED C/D; UF-ENTRY / UF-PROFIT / UF-LOSS cycles; BARS-CAND-3; SD-GAP — each under DRAWDOWN FIRST.

Reporting

MORNING.md every 2 h: load, agents by section, one sentence per section, the RISK-KEEP count so far. Brief v7 12:00Z, final 17:00Z: section 1 = the Sunday ON set (unchanged unless A/B says otherwise, with the reason), section 2 = NEW THIS NIGHT (RISK-KEEPs, hedge side, ORB), section 3 = Shadow list with D6/D7 mapping, section 4 = purchases for the user's OK.
