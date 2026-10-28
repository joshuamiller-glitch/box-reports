# DS3_CONFIRM_B pre-holdout text (D3CFB, 2026-10-28)
Everything below was fixed before any HOLD (2025-07 onward) P&L or HOLD fill statistic was read.
- Prereg l2vast/ds3/prereg/CFB_B1.md (sha256 0b869cbf..., logged in DECISIONS.md): 24 cells (2 queue models x 3 delays x 2 lots x 2 exit bases), F=24, headline cell back / 1 s / 10 lots; verdict rule fixed ('does not exist at live latency' if WF stack-add d mean < MDE or CI contains 0 on M or T).
- Replay: rvq_direct.py on 45 months (2023-02..2026-10) plus the 6-day 2026-10 ext fix; engine exec_engine_l2 (unchanged), primary queue model 'back' (no cancel credit), sensitivity 'prop'.
- Sanity (2023-04, 15 signals): touch bid/ask at the signal tie to the 1-s tape bid/ask of the preceding second on 15 of 15 signals (adj minus offset); fills occur at the limit price; queue0 1-11 lots.
- Groups for the one-look-per-group rule: G1 = back model (6 engine rows x 2 bases), G2 = prop model (6 x 2).
