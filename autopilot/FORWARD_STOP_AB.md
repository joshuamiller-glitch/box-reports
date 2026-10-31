# FORWARD_STOP_AB — stop-join forward A/B spec (lead, 2026-10-31; no research run)

Question: does JoinThenMarket (3 s) cost more per stop than Native stop-market? Live evidence so far (LIVE_STOP_JOIN.md): join 2.45 pts/stop vs nominal (n=21, CI 1.04–3.86); Native 1.28 (n=8, other books, SE 0.13); difference +1.17, z 1.6, one-sided p 0.055; join fill rate 8/21 (0.38) vs replay 0.78.

## Design
- Arms: A = Native stop-market; B = JoinThenMarket (current 3 s). Assignment by trade-date parity of the entry's session-trading-day: ODD day = A, EVEN day = B, per book, from Monday 2026-11-02 (the Sunday-open trading day 11-01 18:00 ET counts to Monday's date by the exchange trade date). Same rule for every book that has a stop; assignment is by calendar date, not by outcome, so no selection by the box or the user.
- Start with ST (U6/ST10) and HM (H6) where the evidence exists; add K6, P6, M6 if the platform owner can switch order type per book by day (DS5/DS6 joins were rejected 6 of 13 times: log rejections as their own outcome, never as 'not filled' silently).
- No other change to the books during the test (so the stop cost is the only difference). Do not mix with the Sunday ON set changes if avoidable: the split/ER/PE changes alter which stops occur, so compare arms WITHIN the same ON set only.

## Measurement (per stop, from the real fills)
- Each trade's REAL stop level (not a hard-coded 60); stop trigger time; fill price(s); slippage = signed adverse distance from the stop level in points; for B also: join order placed (time, price), join filled Y/N, fallback time, fallback fill price, join rejected Y/N; session; distance price had already run past the stop at placement (last print vs stop level at the trigger second); lots (slices at the 2-s schedule: count the VWAP of the slices).
- Aggregated tables only in the research folder; no account ids, no order-level raw text in any research file.

## Sample size to separate 1.28 from 2.45 at 95%
- Effect to detect: δ = 2.45 − 1.28 = 1.17 pt/stop. Spread: the join cost CI (n=21) implies SD ≈ 6.6 pt; Native SD unknown (assume ≈ 1.0 pt; the 8-stop SE of 0.13 suggests it is small).
- One-sided test at 95%, power 80%: n per arm ≈ ((1.645+0.84)² × (6.6² + 1.0²)) / 1.17² ≈ 200 stops per arm (400 stops total).
- Stops per week: ST+HM ≈ 19 in the lock engine (research rate; live files show ≈ 13). With a 50/50 day split that is ≈ 6–9 stops per arm per week → 22–33 weeks for ST+HM alone; with all live books ≈ 4–6x more stops/week → ~6–8 weeks. If the join SD is smaller than the CI suggests (heavy-tailed costs dominate), the sample falls; if the effect is smaller, it rises.
- Faster, cheaper secondary endpoints (report weekly): (1) join fill rate vs the 0.64 break-even (binary: n≈70 stops in B resolves 0.38 vs 0.64 at 95%); (2) median and mean slippage per arm with block-bootstrap CIs; (3) the share of stops with slippage > 3 pt per arm.
- Stopping rule: pre-stated: review at n = 30, 60 and 120 stops per arm; stop for harm if B's mean exceeds A's by > 2 pt with one-sided p < 0.01; otherwise run to the n above. Decision rule: switch to Native for a book if A's mean < B's mean and the one-sided p < 0.05 at the planned n, or at 120 per arm if the difference is > 1 pt with p < 0.10 (user's call).

## Reporting
- Weekly line in MORNING.md every Monday: 'STOP A/B week N: A n=.. mean=.. (CI), B n=.. mean=.. (CI), join fill rate .., rejected .., diff .. p ..'. The Monday scorer shares the HM forward register's machinery (same weekly slot).
- Dollar figure at live lots: Δ pts × stops/week × live lots × $20/pt (NQ) per book.
- Caveats: Native reference now rests on 8 stops from ST_Stop/WT_Stop on other books; the three Native estimates disagree (1.28 / 2.20 on the same stops), which is why the forward A/B is needed.
