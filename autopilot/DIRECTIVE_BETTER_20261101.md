# USER ORDER T-BETTER (2026-11-01 ~15:00Z), saved verbatim

T-BETTER — find what makes D7 BETTER; all day Sunday and on (user, 2026-11-01 ~15:00Z)

This is a SEARCH program, not a gate program. The base is fixed: D7 v1.0d as it ships tonight (the six core books at live lots; 70/30 split dip 3; TH-L2 30/30 and −30/5 s/30×; PE 45-s confirmation NY; ER(20) sizer all books with running-max locks; Asia-only stack cut 50%; 8-line no-trade set skip D 20 with OTE-62 B73 at D 30; signal-state rules HM skipBot3 slope / KB skipTop3 st1_dist / PE sizeHi st1_dist; X1-X5 at 2 lots; Native stops). Nothing in the base is re-tested or killed here — the base is the user's decision. The only question for every cell: does adding or changing THIS make the base better on drawdown-first (maxDD, worst-20, Calmar, equal-risk mean) in the recent windows, and does it hold under the TOLERANT gate? Rank, don't kill. PLAN36 rules (measured fills, per contract first, session column, prereg, dead cells, placebos, three columns STRICT / TOLERANT / NOW-ONLY). 10 agents, ≥ 90%, never idle; interim ranked list every 2 h in MORNING.md; DS3_BETTER.md rolling; a BETTER section in the brief.

1. Neighbours of what survived (the cheapest better: 2 agents)

Every ON piece has a parameter the box never swept on the D7 base with the other pieces present. Sweep each in the composite, drawdown-first, per session: split 60/40, 70/30, 80/20, 90/10 × dip 2/3/5/8; ER threshold 0.25/0.30/0.35 × multipliers (0.5, 1.5) / (0.75, 1.25) / (0.5, 2.0) × ER on 3 / 5 / 15-min; PE confirmation 30 / 45 / 60-s × ThreeBar / HaThree / Engulf × NY only / + London; stack cut 25 / 50 / 75 × Asia-only / all; zone D 15 / 20 / 30 × skip / half; OTE-62 D 20 / 30 / 40 × B73 / WT, plus OTE-70.5 and 79 as the acting line; signal-state: the full EINT1 feature × template × book grid (36 features × 10 templates × 6 books, sessions as a column) on the D7 base — this is the one the user asked for "the best version" of, so rank the whole grid and give the top 10 per book; TH-L2 profit 20/30/40 × 1.5/2.0/3.0× × trail 20/30/take, loss −20/−30/−45 × 5/10 s × 10/30×. Output: per piece, the best setting vs the shipped one, with the delta and whether it is inside MDE.

2. Joint re-fit (1 agent)

The pieces were chosen one at a time. Re-fit them together: coordinate descent over the section-1 grid on PRE+X' then the ONE recent look, and the reverse (fit on L6M, check PRE/X' under TOLERANT), drawdown-first objective (max Calmar s.t. mean ≥ base mean − MDE). Report both fits, their risk lines, and the overlap — the settings both fits agree on are the better composite.

3. New books the base does not have (2 agents)

From the whole engine library (every registered cell, every session) the books NOT in D7 that are positive L3M AND L6M per contract: score each ADDED to the base at 1 / 2 / 4 lots in its best session, drawdown-first, weekly correlation to the base, marginal Sharpe, equal-risk line. Include: the Donchian 15-min resting-stop book (TR3_DON15_S — D7 has it as N7 at 0 lots; score it at real stop fills 1.4-1.7 pt), the two direct PB7 cells (HMA55 widening; W15 s−3), the RSI2 / IBS overnight sleeves (the user runs overnight sleeves separately — report, label overnight), TB4W on 10-min / Volume-500 and PE on volume bars (D7 cannot host them yet: give the NT8 spec of the pullback engine on alt bars so it can be built), the EMA-cross / Keltner / Supertrend alt-bar cells adjacent to X1-X5 (the sister cells one bar size or one parameter away, ranked), and anything in the 60%/70% lists that is runnable. Output: the ranked "ADD" table with lots, session, D7 slot or needed code.

4. Better exits — only the forms that survived, on the D7 base (1 agent)

The persistence study's one durable exit family (p70always) and the L2 clusters (price-only −45 tighten; thick-book early exit): on the D7 base, drawdown-first, as a replacement for or addition to the TH-L2 rules the user runs. Variants: take at 70 / 80 / 90% of target; lock at entry + 0 / 10 / 20 after +30 / +40; thick-book 1.5 / 2.0 / 3.0× for 10 / 20 s. Per book and session. Output: the best exit set vs the shipped TH-L2 set, risk line, equal-risk mean.

5. Lots per session, drawdown-first, as a ranking not a solve (1 agent)

For each book × session: the marginal Calmar of +1 / −1 lot on the D7 base; the five best lot moves and the five worst; the X1-X5 lot question (the user has 2 each as a placeholder: what does 1 / 2 / 3 do to the base's maxDD and mean); A7 at 1 / 2; H7 NY-AM at 2 / 3 / 4. Output: a lot table with the ten moves that improve Calmar the most, each inside/outside MDE.

6. Forward selection over everything (1 agent, continuous)

Greedy forward selection on the D7 base over the full ledger (14,741 rows + the ON/shadow lists + sections 1-5 as they land): at each step add the single rule / book / lot move that most improves Calmar at equal risk under the TOLERANT gate, re-score, repeat to 10 steps; purged walk-forward of the selection procedure itself (select on months ≤ M, score M+1..M+3, 2024-26) so the user knows whether "keep adding the best thing" works out of sample. Output: the path (step, what, Calmar before→after, mean, maxDD) and the walk-forward verdict.

7. Two new families (1 agent, after 1-6 start)

(a) Per-book SESSION re-selection on the recent windows: for each book the session table that maximises Calmar in L6M, checked PRE/X' TOLERANT — the user's session lots are from a September re-score. (b) The 14:40-15:00 drift (−13..−24 pts into the close in every window) as a SHORT-SIDE close book (fade the late-afternoon move, flat 15:55) and as a K7 NY-PM block, drawdown-first.

8. Reporting standard for this program

Every result row: what | books/sessions | base mean → new mean (MDE) | maxDD before→after | worst-20 | equal-risk mean | placebo | STRICT / TOLERANT / NOW-ONLY | D7 property or code needed. Ranked by Calmar gain at equal risk. The user wants a list to pick from, with the honest labels on each line, not a verdict that nothing clears. DS3_BETTER.md top 30 across all sections, refreshed every 2 h; DS3_BETTER_<section>.md detail; MORNING.md every 2 h with load, agents, and the current top 5.
