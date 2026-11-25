# LONDON_CODING_INDEX: London (02:00-08:30 ET) coding inputs, status page

Written 2026-11-25 ~18:00Z by W-NYAMSPEC2 (relay sub-agent, not typed by Josh). Read-only; nothing queued, nothing live, nothing deleted. W-NYAMSPEC1 adds the row for L74274eca.

## 1. London pool (4 books) and weighted picks (reselect_london_*_w.json, phase done)
Pool: L12842dde.BRP45, L19201dfc.BRF90_30, L74274eca.BRF120_60, Lc78f2492.BRF90_30.
| loop | final set | members (size; whole lots x4) |
|---|---|---|
| london-own-w | TL3_ALN_LO_L19201dfc_R0BRF90_30 | L19201dfc.BRF90_30 x1 (4) |
| london-stay-w | TL3_ALN_LO_L74274eca_R0BRF120_60 | L74274eca.BRF120_60 x1 (4) |
| london-own-recent-w | TL3_ALN_LO_STKd8e4ab42ac | L19201dfc.BRF90_30 x1 (4), L12842dde.BRP45 x0.5 (2), L74274eca.BRF120_60 x0.25 (1) |
Lc78f2492 is a near-twin of L19201dfc (D8_LONDON_NOTES.md) and is in no weighted pick.

## 2. Coding status per book
| book | in D8Asia.cs | hand-verified spec | page |
|---|---|---|---|
| L19201dfc | yes (bk10, needs CL) per LEAD | hand-written block, 1,768 of 1,768 events re-implemented 23 Nov (D8_LONDON_NOTES.md); not re-verified today | AUTO:BOOK:L19201dfc, D8_PARITY_L19201dfc_*.md |
| L12842dde | no | DONE 2026-11-25 (bar, trigger, feature, events verified on full stored data) | autopilot/D8_LONDON_SPEC_L12842dde.md |
| L74274eca | no | assigned to W-NYAMSPEC1 | autopilot/D8_LONDON_SPEC_L74274eca.md (row to be added by W-NYAMSPEC1) |
| Lc78f2492 | no | not in any weighted pick; not specified | D8_LONDON_NOTES.md section 1 |

## 3. Tape and book inputs
- London raw tape 20261110: outputs/autopilot_nomirror/D8_PARITY_TAPE_20261110_LONDON.md (stub autopilot/D8_PARITY_TAPE_20261110_LONDON.md).
- Level-1 book snapshots for the book-imbalance feature (L12842dde): outputs/autopilot_nomirror/D8_PARITY_BOOKL1_20261110_LONDON.md.
- Scale rows (s_rng, box), 45 days, stored and hole-filled: inside each spec page (L12842dde section 4).
- Open for all London pages: stored vs hole-filled inputs (LEAD decision), TRADES for td 20261110 (engine month 202611 not landed), stack lots and fit.
