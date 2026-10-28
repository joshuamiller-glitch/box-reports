# DS3_SESSION_FINAL - T-SESSION-RESCORE (main, 2026-10-28)
Research only. Cut 2026-02-06 (HOLD 2025-07-01..2026-02-06). Reports: DS3_SESSION_1_BOOKS, _2_LEDGER, _3_PAIRS (+PREHOLD files). Best-of-F is a label here (user rule).

Verdict lines per session (alive cell-sessions / independent clusters after ONE holdout look; best cell per trade vs MDE):
- ASIA: 190 / 58. IF_30s_eb +$347 (MDE $202), HOLD +$387. 2023 span negative for ~72% of alive cells.
- LONDON: 40 / 21. CRT_M15_M1_close_ib +$262 (MDE $138), HOLD +$110: the ONLY SESSION-PASS (DEAD pooled, clears best-of-F). 2023 span negative for ~78% of alive cells.
- PRE (08:30-09:30): 16 / 8. IF_30s_eb +$392 (MDE $423), inside MDE.
- NY-AM: 154 / 29. IF_15s_eb +$446 (MDE $267), HOLD +$603. 2023 span positive for 65%.
- NY-PM: 9 / 8. best a TB4B tick cell +$1,207 (MDE $1,279), inside MDE.
- CLOSE: 0 / 0 (none PRE-significant).
- Live/Sim books (item 1): no session block supported; WT NY-PM block = NOT-CONFIRMED watch (ALL +$1,835/wk [+210,+3,407], placebo rank 0.965, PRE CI includes 0); carriers PE/DN/KB ASIA, KB NY-PM, MV NY-AM = SESSION-CANDIDATE with no improvement claim.
- Pairs (item 3, 20% risk): 27 PAIR-PASS of 40 (HOLD add +$11k..+$32k/wk vs stack $52,448/wk, corr -0.16..+0.29); best P08 (IF_30s_eb ASIA + IF_15s_eb NY-AM) +$31.8k/wk, P28 (PRE + NY-AM) +$25.5k/wk, most cost-robust.
Why NOT live-eligible: all passing pairs are IC/CRT cells on MAPPED stored fills (source credits stop exits +2.6..+4.2 pts in 2025-26); slippage breakeven 1.1..3.1 pts, HOLD negative at +2 pts in 15/27 (12 stay positive); the add is negative on the 2023 span in all 32 passing units (-0.6k..-14k/wk); HOLD is 32 weeks (2026 stub 5.5); pass verdicts rest on 3-4 rules of one IC/CRT family (not independent); no 1-s legs, so trade-row day lock used, not the exact lock engine.
Register: SESSION_REGISTER.md (autopilot/forward/) holds the text entries (single cells, carriers, 12 cost-robust pairs at half size). Evaluator wiring not done.
Order the user can give: conservative-fill, live-latency re-run of IF_30s_eb, IF_15s_eb and CRT_M15 legs by session window; re-run of summary-only families (T-OPEN B2, T-BRACKET grids, T-HOLD, T-WASHOUT, T-SESSLOCK, T-PBX) with entry clocks.
