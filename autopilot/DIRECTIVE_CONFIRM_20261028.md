# DIRECTIVE 2026-10-28 CONFIRMATION PROGRAM (verbatim from user)

CONFIRMATION PROGRAM 2026-10-28 — DR5m (open) and RVW1|F30 (close): independent evidence, not more cells

Research only. No live, execution-server or chart change. Never read UNTOUCHED (a separate decision; not in this file). Same V2 rules: preregs frozen before scoring, both placebos, one logged holdout look per group, equal-risk, never-empty-handed finals. FEES.md costs. Redact account ids in anything mirrored.

The two overnight candidates fail only the program-level best-of-N. That cannot be fixed with more cells on the same data. This program gets independent evidence: the frozen rule, no grid, on data and instruments the rule has never seen, plus the two execution questions that decide whether either exists at real size.

Frozen rules (copy exactly from the finals; no re-tuning anywhere in this program)
OPEN: DR5m_pb1_rm0.5 = 5-min drive from 09:30 >= 0.5 x median opening range (median as defined in DS3_OPEN_FINAL / its spec), enter the first 1-3-min pullback in the drive direction, stop 60 / target 75 (NQ pts), the exact entry/expiry/flat rules of the spec. One cell. Write the spec as DS3_SPEC_TOPEN_DR5m.md if the final's spec is not already complete to the line (it must be codeable to NT8 by someone who has not read the study).
CLOSE: RVW1|F30 v2 = VWAP reversion >= 1 sigma at 15:30, resting limit at touch, 30/30, flat 16:00, exactly per DS3_SPEC_RVW1_F30.md v2. One cell.

A. Cross-instrument replication (CPU-only, run first)
For each of ES, YM, RTY (and NQ as the reference row): the frozen rule, constants scaled by the warm-up median-range ratio k exactly as D3CX did, floors as D3CX, equal $1,000 risk, D3CX conservative fill basis (market +1 tick, stop +2 ticks, limit fills on 1-tick trade-through only). Prereg = 2 rules x 4 instruments = 8 cells, F = 8. Report per instrument: trades/wk, WF/HOLD/2023 mean with CI and MDE, both placebos (random-direction same clock; random-clock same rule), by year. Verdict line: "DR5m replicates on N of 3 instruments; RVW1 replicates on N of 3", and the pooled 3-instrument row with its best-of-8 p. Replication on >= 2 independent instruments with the same sign and CI above 0 is the pass; NQ-only is "lucky fit, do not pursue".

B. RVW1 execution reality (replay, memory-aware — the question that decides whether it exists)
On the NQ mbp-10 book, for every RVW1 signal: rest the limit at the touch price at the signal second, track queue position (volume ahead at that level at placement, minus trades at the level), fill only when the queue ahead is consumed or price trades through. Report fill rate, fill-vs-touch, and the re-scored WF/HOLD at 5 and 10 lots versus the spec v2 number (+$1.3k M / +$2.3k T). Also the 1-s and 3-s placement-delay variants (the live path is not instant). Verdict: fill rate and the surviving weekly mean with CI; if the surviving mean is inside its MDE of zero, say "does not exist at live latency".

C. DR5m at a hard position cap (CPU-only)
Re-score DR5m as a stack add with the live books at their current lots and a hard 50-contract total cap (DR5m takes only what the cap allows, 0 if nothing), and at caps 40 and 60. Report the add's weekly mean/maxDD under each cap vs uncapped, and how often it is cut to 0. Also the brokerage intraday margin number for the peak (use the margin facts in FEES.md / INSTRUMENT_INVENTORY.md if present; else state the assumption).

D. Forward register (bookkeeping)
Register both as shadow rows (paper_all) with the expectation from the finals and the weekly MDE, so paper weeks accumulate from today. State the number of forward weeks each needs at the current MDE. Add the DS5 mix row (answering the open question from MORNING.md item G: yes, add it, and fix the evaluator timezone/PE assignment). Recalibrate the TR3_DON15_S forward slippage alert to 1.7 pt (answering item C's question: yes).

E. If A passes for either rule
Write the Sim spec to the line (parameters, times in ET, ticks, fill rules, flat rule, lots), and a one-paragraph plain-English description, as DS3_SPEC_<RULE>_SIM.md. Do not widen the grid; do not test neighbours.

Reporting
DS3_CONFIRM_A.md (replication) first, then _B, _C, _D; MORNING.md every 2 h; DS3_CONFIRM_FINAL.md never-empty-handed with one verdict line per rule: replicates / does not; executable / not; cap-survivable / not; forward weeks needed.
