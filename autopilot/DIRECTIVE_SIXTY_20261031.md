# DIRECTIVE T-SIXTY (user, 2026-10-31 ~16:00Z), saved verbatim

T-SIXTY — the "over a coin flip" book: every recent edge with persistence ≥ 60%, built as a diversified portfolio (user, 2026-10-31 ~16:00Z)

Research only. PLAN36 rules (measured + live-cal fills; per contract first; session column; QUANT-LAYER; prereg; dead cells). Runs inside the 80-90% order beside the Sunday work; interim table by Sun 06:00Z, final in the Sunday brief v6 as its own section.

The user's reasoning (score it, do not argue with it)

The persistence study says the average recent edge holds 41% of the time. The user does not want the average; he wants the rules whose persistence score is ABOVE 60% — better than a coin flip — because they are working NOW, in this market, not in 2024 when the market was different. He also expects rules on different candle sizes and different methods to be less correlated with each other and with the live books, so a portfolio of them should have a better risk picture than its parts. Test exactly that.

1. The 60% list (from the RECENT-EDGE ledger, 14,741 rows)

Every row with PERSISTENCE SCORE ≥ 0.60 (and, as a second column, ≥ 0.70), de-duplicated to one row per distinct rule (same mechanic, same book, same session; different thresholds collapse to the walk-forward last re-fit). For each: family, book, session, bar type / timeframe, mechanic, per-contract L3M / L6M / HOLD / PRE / X', trades per week, 6-month t-stat, persistence score and what drives it (streak, t, placebo rank, PRE sign), shrunk expectation, STATUS (rising / stable / fading), and whether D6 or D7 can run it today (group / property) or what it needs. Sort by shrunk $ per week at live lots. Say how many there are and how many are independent exposures (section 3).

2. The regime argument, tested

For the 60% list: the monthly series since 2023 as a small table per rule; the 2024 vs 2025-26 split; which regime measures (vol tercile, trend persistence, session share, book depth, ES correlation — the 2025-26 regime description of RECENT-EDGE 5b) carry the difference; and the one sentence per rule "this works now because …" where the data supports a reason, or "no identifiable reason" where it does not. Then the question the user is really asking: within the 60% list, does the persistence score do better than 41% out of sample — the walk-forward of "take only rules scored ≥ 0.60 at month M" over 2024-26: share still positive after 3 months, shrinkage, and the $ line.

3. Diversification (the user's second point)

Pairwise weekly correlation of the 60% rules with each other and with the live stack; cluster them (same bet wearing different clothes vs truly different); the portfolio line — equal-risk weights at shrunk sizes, all rules together on the lock engine — mean, SD, maxDD, worst-20-weeks in L3M / L6M / HOLD / PRE / X', vs the live stack alone and vs the Sunday composite. State the diversification benefit explicitly: SD of the sum vs the sum of SDs; how much of the improvement comes from alt-bar / alt-method rules specifically (score the portfolio with and without them). If the alt-bar rules are just the live books' signals shifted a few seconds, say so with the correlation.

4. What to run and how

The portfolio of section 3 restricted to what D6 v2.3b / D7 v1.0 can run (D7 has generic alt-bar slots: Supertrend / Keltner / EMA-cross / HMA-VWAP on any NT8 bar type, HA optional; group-12 clock filters; the policy file): per rule the exact D7 slot settings or D6 property, the recommended size (shrunk, Kelly-capped), Shadow or Live by the 60%/70% tier, and the monitor's STOP rule for each (RE-2). Rules D7 cannot run: one line each on what is missing.

5. Also (not pasted earlier)

D7F follow-up on rule (a) first-60-min skip: add maxDD, SD, worst-20-weeks, Sharpe in every window, per session, plus the equal-risk line (lots re-scaled so worst-20 matches the composite's) — the user's question is whether it lowers drawdown, not the mean. Answer to the D7F open question: in D7 a skipped signal does NOT update SizeMult (the filter runs before the sizer).

6. Report

DS3_SIXTY.md (sections 1-4 with the plain sentences: "N rules clear 60%; M independent bets; together at shrunk size they add X $/wk at Y% lower worst-20 than the stack alone; the alt-bar rules contribute Z of that; out of sample the ≥60% selection held W% of the time vs 41% for everything"); rows to RECENT_WINS; a SIXTY section in DS3_SUNDAY_BRIEF v6; MORNING.md every 2 h.
