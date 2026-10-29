# DS3_ADAPTIVE_IMPLEMENT - THP_POLICY v1 (PUB1, 2026-10-29)
Research only; UNTOUCHED never read; no live/execution change. File: autopilot/THP_POLICY.txt (copy THP_POLICY_20261029.txt). Validator + replay: autopilot/thp_policy_check.py (parser accepts imb5, imb10, wall_tgt, wall_stop as legal so v2 L2 rules drop in; nothing in v1 uses them).

## Per-section result (pts/trade vs the book's own exit/bracket; MDE = 2.8 SE)
| section | published | walk-forward number | MDE | rules | honest read |
|--|--|--|--|--|--|
| profit | EMPTY | no rule = 0.00. Best WF model chain (THPC1 logit, 3m window, weekly re-fit, take+tighten) +0.32 [-0.60,+1.24]; HOLD -0.13, PRE-span +0.54, N basis -0.98. Its 12-leaf WF-distilled rules (weekly refit on trades closed before fit, 3-class tree) -1.02 [-2.01,-0.03] | 1.32 / 1.41 | 0 | Model is ~0 and the distillation LOSES (retained gain undefined/negative; < -0.5 so EMPTY by rule). |
| loss | HM only, 1 rule | exact live-definition L6_a30_r3_w10: +1.18 [+0.16,+2.19]; X +0.06, PRE +1.37, HOLD +1.82 (replayed from hm9.npz, 1-s paths) | 1.45 (ALL), 2.65/2.04/3.05 by window | 1 | SEEN-DATA fixed rule, not WF-fitted (picked after a 158-rule search that saw X/PRE/HOLD); X is ~0. Fresh look = HM forward from 2026-11-01 only. Other books: no rule (THPC3 loss best WF HOLD -0.73, all 1,234 cells DEAD; THPC1 loss grid had not started). |
| bracket | 11 lines (one per evaluated book) | frozen abs120 stop / OR target / no time, lotmult 0.5: PRE +2.33 [-2.04,+6.70] (in-sample), HOLD +3.17 [-4.44,+10.78], X' +1.01 (ABRC2 chain; +0.22 in ABRA table) | 6.2 / 10.9 / 8.1 (6.4) | 11 (1 pattern) | >=0 in all three windows but every CI includes 0. Wide-bracket tilt (random assignment of the same bracket mix does as well; ABRC2 all 2,364 cells DEAD, RC p 0.49). Risk: weekly SD 1.9x, maxDD 1.4x at $-risk parity (3.8x/2.9x at constant lots). Best table (G1a sess ew5/1w) was passed over: PRE +4.26 but HOLD +0.57, X' +0.52, 2026 -5.1, London -3.4. |
Header wf_bracket +2.35 = n-weighted HOLD+X' (out-of-sample only, n=18,435, MDE ~6.5).

## Retained gain (distilled vs model chain)
Profit: undefined; model +0.32, distilled -1.02. Loss: no distillation (fixed rule); F8 transliteration replays only +0.17..+0.30 on 1-min bars of the THP data, i.e. ~15-25% of the exact rule - flagged in the file; use the native L6 implementation. Bracket: frozen rule, nothing distilled; ABRC2 student of the best table kept +0.30 HOLD vs teacher +0.57.

## Caveats
1. Profit LEAD to check, not published: a trailing stop 10 pts under MFE (tighten-only) scores +1.8 (CI +0.9..+2.8) on all in-profit trades and +1.9 under random assignment, +2.3 with the model; trail 6 gives +2.2..+2.6. N basis +0.5. The replay is on 1-minute rows (detect at minute close, fill at the level), so it is probably optimistic; needs a 1-s replay with measured fills before anyone trusts it. The model adds about +0.4 over random (inside MDE).
2. Profit chain starts 2024-04 (no X'). Distilled-tree training used teacher scores of the chain itself (causal).
3. Bracket "OR" target = opening-range edge as in ABRA; short-target fills untested. Per-book window splits not available; per-book all-span deltas all >= +0.84 (SM +6.3, MA +5.4 CIs exclude 0 individually, uncorrected). ST/WT/MA/CR use research names because the D6 tags were not supplied.
4. THPC1 loss grid, THPC2 and ABRC1 are unfinished; nightly re-fit will pick up their cells. I did not touch their processes.

## v1.1 note (PUB1)
Bracket section emptied, header wf_bracket=0.00 (hold 60/60). Reason (EXP2, DS3_ADAPTIVE_EXP2.md, exact lock engine): wide no-time-exit brackets block 36-78% of a book's later entries; frozen stop=120/OR gives stack weekly SD $654k vs $332k, maxDD $4.5M vs $2.9M, costs ~$51.7k/wk outside the worst weeks; joint stack 0/19; best bracket component ~0 (PRE +4.7k, HOLD -1.4k, X' -1.0k $/wk). The v1 trade-level +2.35 does not survive. Profit stays empty, HM loss rule unchanged (+1.18, fixed rule, seen data). Rules 12 -> 1 (-11). v1 files kept (THP_POLICY_20261029.txt); v1.1 copy THP_POLICY_20261029_v1.1.txt.
