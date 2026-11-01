# USER ORDER T-ZONES-3 (2026-11-01 ~15:00Z), saved verbatim

T-ZONES-3 — expand the zone skip, the one piece that lowers drawdown in every window (user, 2026-11-01 ~15:00Z)

Base = D7 v1.0d as it ships (group 10: the 8 coded lines, fresh, D 20, skip; group 10b OTE-62 B73 at D 30). DRAWDOWN FIRST on every cell (maxDD, worst-20, Calmar, equal-risk mean, same-volume placebo, RISK-KEEP label), recent-first, per book and per session, three columns STRICT / TOLERANT / NOW-ONLY, measured fills, prereg per section, dead cells. This is a search for a BETTER zone layer, not a re-test of the one that ships. 3 agents now, more as T-BETTER sections finish; interim ranked list every 2 h; DS3_ZONES_3.md rolling; the ZONES line in the brief.

0. Why

DS3_DRAWDOWN: the 8-line zone skip takes the composite's L6M maxDD 57k → 23k, HOLD 143 → 97k, PRE 304 → 241k, X' flat, beats the placebo (rank 2%) — the only piece that helps the tail in 2024-25 as well as now. It was built from 8 of 11 lines, one distance, one action, one freshness rule, chosen post-hoc. Nobody has asked which lines carry the drawdown cut, what the right distance is per line, whether the action should differ per line, or what the 183 other POI streams do on THIS measure. Do all of that.

1. Which lines carry it (first; 1 agent, 2 h)

The shipped 8 lines, leave-one-out and one-at-a-time, on the D7 base: maxDD / worst-20 / mean per line, per book, per session, L3M / L6M / HOLD / PRE / X'. Then the 3 uncoded lines (15-m-swing VAH, 1-h-swing LVN1, HVN0) added — with the exact tape-built profile definition D7 would need (bins, swing anchoring, value-area rule) so the profile engine can be built if they carry weight. Output: the line table ranked by drawdown contribution; the lines that add nothing (candidates to drop so the skip costs less volume).

2. Distance and freshness per line (1 agent)

D = 10 / 15 / 20 / 30 / 40 / 60 pts and D as 25 / 50 / 75 % of the target distance, per line (not one D for all); freshness = fresh / touched once / any / "fresh within N hours"; line age (formed < 1 h / 1-4 h / > 4 h ago); line confluence (two set lines within 5 pts = stacked; three = cluster). Drawdown first. Output: the per-line (D, freshness) table that maximises Calmar, and the stacked-POI rule's own line.

3. Action per line (1 agent)

For each line: skip / re-target to line − 2 ticks / half lots / B73 (70% now, 30% through the line) / WT (wait, whole lot through the line) / delay N min / "enter the 70% and rest the 30% BEHIND the line" (after the reclaim) — the OTE-62 result says the right action is not always skip. Drawdown first, placebo = random-level same count. Output: the action table per line; the composite with the best action per line vs the shipped all-skip.

4. The other 183 streams, on the drawdown measure, on the D7 base (2 agents)

DS3_POI_MAP scored every stream on dP(target) pooled. Re-score every stream (FVG / iFVG / OB / breaker on 14 TFs, profile POC / VAH / VAL / HVN / LVN on every anchor, VWAP bands, prior day / RTH / week / month H L C O 50%, pivots, session and killzone H/L, developing extremes, opens, gaps, OR edges and extensions, fractal swings, equal H/L, CRT, Fibonacci, dealing range, BOS/CHoCH, HTF MAs / Bollinger / Keltner / Donchian / Supertrend / Ichimoku, Wyckoff edges, round numbers, book walls) as an AHEAD line at D 20 and 40, fresh, skip, on the D7 base, drawdown first, per session. Rank by maxDD cut at equal risk with the placebo beaten. Then the BEHIND frame (line between entry and stop: stop placement / skip / size) and the AT frame (signal at the line: take-only / size-up) for the top 20. Output: the new lines worth adding to the set, with exact D7-computable definitions (most are already in the group-10 vocabulary).

5. Zone density as a regime (1 agent)

Not one line but how many: the count of set lines within 20 / 40 / 60 pts ahead and behind at the signal (congestion); the distance to the nearest line in any direction (open space); the ratio ahead/behind. As skip / size / re-target rules, drawdown first. Also the "no-man's land" state from NTE-1 (middle third of the prior-day / overnight / session range) scored on the same measure.

6. The learned zone rule (1 agent, after 1-5)

Walk-forward classifier of P(target) from ALL line features at the signal (line type, distance, freshness, age, confluence, ahead/behind counts, session), policy skip / half / full by predicted P(target) buckets, 3-month weekly re-fit, shuffled-feature placebo, calibration; the extracted ≤ 6-rule tree; drawdown first. Output: the tree in words and its D7 mapping (a per-line table D7 can read as a daily file: line | D | freshness | action).

7. Sessions and books (all sections)

Every result per book × session. The box found Asia / pre-market behaviour differs from NY for the confirmation layer; check whether the zone layer wants a per-session D or line set (e.g. prior-day lines in Asia, OR/VWAP lines in NY).

8. Deliver

DS3_ZONES_3.md: (1) the line table (section 1), (2) the per-line D / freshness / action table = the proposed group-10 v2 (a daily file zones_policy.txt: line | D pts | freshness | action | books | sessions), (3) the new lines to add with definitions, (4) the density regime rule, (5) the learned rule in words, (6) the composite with the proposed zone layer vs the shipped one: maxDD, worst-20, Calmar, mean, equal-risk, every window — and the plain sentence "the expanded zone layer takes the composite's L6M maxDD from X to Y and PRE from A to B at the same mean / at equal risk". Rows to RECENT_WINS; MORNING.md every 2 h.
