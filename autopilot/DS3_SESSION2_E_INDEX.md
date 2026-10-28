# DS3_SESSION2_E_INDEX - session-cell NT8 specs for the D6 session book (D3SSE, 2026-10-28)
Scope after the D6 priority split (DIRECTIVE_D6_PRIORITY_20261028.md item 1): this agent delivered the five ICT specs below. ba2/KB, HM, SM, PB7, E1A, TB4B, TB4W (and the name-decoding task) belong to D3SSE2 and are NOT in this index. All specs: session cell, MAPPED stored basis, NOT live-eligible until D3SA's live-latency result (DS3_SESSION2_A.md); D3SA will update them.

| spec | session (ET) | tier (stored) | basis | PRE mean $/trade (MDE) | 2023 span | open items |
|---|---|---|---|---|---|---|
| DS3_SPEC_IF_30s_eb_SESSION.md | ASIA 18:05-02:00; PREOPEN 08:30-09:30 | CANDIDATE / CANDIDATE | MAPPED | 347 (202) / 406 (423) | -232 / -132 | NT8 30-s bar identity; limit-fill semantics; stop credit on 6-pt stops |
| DS3_SPEC_IF_15s_eb_SESSION.md | NY-AM 09:30-12:00 | CANDIDATE | MAPPED | 446 (267) | -128 | NT8 15-s bar identity; same |
| DS3_SPEC_CRT_M15_M1_close_ib_SESSION.md | LONDON 02:00-08:30 | SESSION-PASS (BOF_F clear) | MAPPED | 262 (138) | -322 | stop credit; 1-lot scale-out |
| DS3_SPEC_CRT_M15_M1_close_SESSION.md | LONDON | CANDIDATE | MAPPED | 170 (109) | -233 | superset of _ib |
| DS3_SPEC_CRT_H1_30s_close_SESSION.md | LONDON | CANDIDATE | MAPPED | 339 (272) | -78 | 30-s bar identity; HOLD 2026 stub 24 |

## Exact ICT definitions (from code)
- **IF = inverse FVG, entry b.** FVG on wicks: bullish low[j]-high[j-2] >= 8 ticks (2.00 pt), zone [high[j-2], low[j]]; bearish mirrored (ic_kern.k_gaps). Inverted = first close beyond the far edge of the opposite-type gap within 3,600 s (k_inv). Singular filter: no other gap overlapping within 10 bars. Entry = resting limit at the gap midpoint, trade-through fill, cancelled on a trade through the far edge, expires after 3,600 s. Stop = far edge -/+ 5.0 POINTS (not 5 ticks). Target = nearest alive liquidity (EQ4, 5-min L5 swings, Asia/London/NY session H/L, prior day H/L, trendlines) at >= max(d,2) pt (>= 1R), else 2R; single target. Risk cap 2-60 pt stop. One position; 16:55 flat.
- **CRT.** Range = previous clock-aligned M15 (or H1) candle (>= 3 / 12 one-minute bars, next candle within 90 min). Sweep bar (1-min or 30-s): wick > 1 tick beyond the extreme, close back strictly inside, no double-extreme; entry market at the bar close; stop = sweep bar extreme; targets 50% level (50%) and opposite extreme (50%) when the 50% level is > 4 pt away, else one target at the extreme; cap 4-60 pt. '_ib' = all earlier bars of the candle stayed inside the range.
- **NT8 15-s / 30-s bars:** not shown to reproduce the library bars anywhere in the repo (docs only declare NT8 Second bars native and the identity test vs a real NT8 export 'pending'); library bar open = previous close, empty seconds skipped. User-side export-and-compare check specified in each spec.

## Cross-cell finding
For the 4-8 pt-stop ICT cells the stored mapped $ credit stop-outs by about 4-6 pt in 2025-26 (loss smaller than the stop distance), a correction calibrated on 60-pt brackets. Treat stored $ as an upper bound; the MEASURED basis from D3SA decides.
