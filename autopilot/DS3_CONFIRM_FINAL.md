# DS3_CONFIRM_FINAL - confirmation program 2026-10-28 (main; from D3CFA, D3CFB, D3CFC reports)

Frozen rules, no grid, no re-tuning. Detail in DS3_CONFIRM_A.md, _B.md, _C.md, _D.md.

## Verdict lines
- **DR5m_pb1_rm0.5 X60_75 (open):** replicates: NO (0 of 3: ES +$55, YM -$114, RTY -$162 /wk WF; pooled -$221 [-795,+352], MDE 820, best-of-8 p 1.00) | executable: not tested here (target limit fills assumed; direct basis is an upper bound) | cap-survivable: ONLY at cap 60 (cap 50 fails the 2023 span: +$0.3k vs +$2.4k; cap 40 fails) | margin: unresolved (5% proxy ~$1.2M at 58.7 lots vs $700k; needs broker intraday NQ margin, fits only if < ~$11.9k/contract) | forward weeks needed: 96 (full edge) / 383 (half edge). Disposition: NQ-only = lucky fit, do not pursue; forward shadow row registered (W45).
- **RVW1|F30 v2 (close):** replicates: NO (0 of 3: ES -$14, YM -$87, RTY -$257 /wk; pooled -$359 [-986,+269], MDE 896, p 1.00) | executable: NO - "does not exist at live latency": 1-s delay, 10 lots, queue-position model: fill 89.9%, WF +$909 [-546,+2,414] (M, MDE 2,119) / +$1,768 [+180,+3,327] (T, MDE 2,279); HOLD CIs include 0; only 4 of 24 cells pass per-cell gates, all T-basis 0-s | cap-survivable: not scored (50-cap breach ~11% of entries in spec v2) | forward weeks needed: 161 (T) / 406 (M) full edge; 646 / 1,624 half edge. Disposition: do not pursue; shadow row registered (W45).
- E (Sim specs): not triggered (no rule replicated). DS3_SPEC_TOPEN_DR5m.md written anyway (NT8-complete spec, forward paper only).

## Top table regardless of verdict (never empty-handed)
| rank | cell | WF $/wk | CI / MDE | failed gates |
|---|---|---|---|---|
| 1 | RVW1 NQ ref (in-sample) | +402 | [127,677] / 393 | year_share (in-sample row) |
| 2 | DR5m NQ ref (in-sample) | +443 | [152,733] / 415 | year_share |
| 3 | RVW1 queue 0-s T, 10 lots | +2,402 | [749,4,076] / 2,324 | fails M basis; HOLD CI includes 0 |
| 4 | RVW1 queue 1-s T, 10 lots | +1,768 | [180,3,327] / 2,279 | inside MDE; HOLD CI includes 0 |
| 5 | DR5m cap 60 stack A | +5,742 | uncapped; CI +2.6k..+9.0k | program-level best-of-N; margin |
| 6 | ES RVW1 | -14 | [-263,234] / 356 | cost2x, year_share, hold, span2 |
| 7 | ES DR5m | +55 | [-216,326] / 387 | beats_a, beats_b, year_share, hold, span2, best_of_N |
| 8 | YM DR5m | -114 | [-380,152] / 380 | mean_up and 6 others |
| 9 | RTY DR5m | -162 | [-438,113] / 393 | mean_up and 6 others |
| 10 | YM RVW1 | -87 | [-341,167] / 363 | mean_up and 6 others |

## Open items for the user
Broker intraday NQ margin; whether to keep the two shadow rows (they were registered per the directive); v1.3 deploy time for DS4/DS5 files.
