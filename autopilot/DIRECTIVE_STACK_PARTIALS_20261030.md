# T-STACK-PARTIALS — user directive pasted 2026-10-30 (verbatim)

T-STACK-PARTIALS — when the books stack up on one side, manage the STACK's risk: partials, exposure caps, correlated sizing (2026-10-30)

Research only. No live, execution-server or chart change. UNTOUCHED never read. MEASURED fills; exact lock engine (this is a stack-level program: every number is the stack's weekly series with locks, re-entries and blocked entries real); per contract per book reported beside it; session as a column; RECENT FIRST; prereg per section; placebos.

The question
Today at 11:40 ET the stack was short 12 lots in one move (P6 5, K6 3, M6 3, H6 1), each book with its own full 60-pt stop: 720 pts of combined open risk on one idea, and when the move fails they all stop together. Nothing has tested managing that as ONE position: taking partials off the stack when it is up, capping the same-side exposure, sizing later entrants down when earlier books are already on, or closing the weakest book when the stack turns. Per-trade partials (two-leg, take-half) were dead; the stack-level version is untested.

A. The stack state (compute at every in-trade second)
Net same-side lots across books; number of books on the same side; combined unrealised in pts-per-lot and in R (R = one book's full stop); combined MFE / MAE of the stack position; time since the first entry; the weakest / strongest book's own unrealised; whether the books entered within 1 / 3 / 5 min of each other (the same impulse) or separately.

B. Rules (each vs the stack as it is; lot-matched entries; the freed lots' re-entry effect counted)
STACK PARTIAL ON PROFIT: when the combined open profit reaches X R (X = 1 / 1.5 / 2 / 3) or X pts per lot (20 / 30 / 40), take P% (25 / 33 / 50) off EVERY book at market (pro-rata), keep the rest to the brackets; variants: take the whole weakest book / the latest entrant instead of pro-rata; move the remaining books' stops to the stack's average entry (stack breakeven) / to MAE + k; and the staged version (another P% at 2X).
SAME-SIDE EXPOSURE CAP: net same-side lots capped at C (C = 6 / 8 / 10 / 12 / the sum of two books): later signals enter at the remaining room only / are skipped; the cap per session; the cap in R rather than lots (each book's lots × stop).
CORRELATED-ENTRY SIZING: when ≥ 1 / 2 books are already on the same side, the next book enters at 50% / 67% (risk-matched report) / full; when a book is on the OTHER side, the next enters at 150% / skips (the netting case).
STACK STOP / STACK CUT: when the combined position is at −X R (X = 1 / 2 / 3) or every book is under water by ≥ Y pts, close the weakest book / close the latest entrant / close P% pro-rata (vs letting each book's own stop and TH work); the "first book stopped → cut the rest to half" rule.
STACK TRAIL: a single trail on the combined position's average entry (20 / 30 / 40 behind the stack's MFE) applied pro-rata, vs the books' own brackets.
RE-ENTRY: lots freed by a partial may re-enter on the next signal (the lock engine does this exactly); report the re-entry P&L separately so the partial is not credited with it.
CONFLUENCE INTERACTION: the EINT1 confluence cells (size up when books agree) re-run WITH the stack partial, since "size up on agreement + take partials on the stack" is the pair a desk would actually run. All on the 70/30 split base and the market base; per session; recent-first; the placebo = random partials at the same rate and time-since-entry; the random-cap control.

C. Report
DS3_STACK_PARTIALS.md: stack weekly mean, SD, maxDD, worst-20-weeks, per rule, recent-first; the equal-risk frame reported but labelled structure; per book per contract beside it (what each book loses by being cut as part of the stack); one verdict per rule: "taking 33% off every book when the stack is +2R keeps X% of the stack's mean and cuts worst-20-weeks by Y% in the last 6 months"; the "run this" table. Anything ≥ 0 on the stack mean at lower risk, or ≥ 0 at equal risk with the lot factor stated: a stack section in THP_POLICY.txt (new format line: "stack cond action [param]" — D6 computes the stack state live: other books' positions, combined unrealised, R) named in DS3_THL2_NEEDS.md for adding. MORNING.md every 2 h.
