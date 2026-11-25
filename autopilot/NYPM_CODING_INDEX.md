# NYPM_CODING_INDEX: NY PM (12:00-16:00 ET) coding inputs, status page

Written 2026-11-25 ~15:25Z by W-NYAMSPEC2 (relay sub-agent, not typed by Josh). Read-only; nothing queued, nothing live, nothing deleted. Sources: _combo/reselect_nypm_*_w.json, finals_ready_nypm.json (stale: 2026-11-24 16:14Z), ALL_NEW_STACK_NYPM_W_NYPM_OWN_W.md and _OWN_RECENT_W.md (15:07Z), D8_NYPM_NOTES.md, D8_LAYER_KEYS_NYPM.md, D8_BUILD_SPEC.md. No NY PM FINAL is declared: both weighted loops sit at phase final, controls pending (30 sets each); the member lists below are the picks as of 15:12Z and can change.

## 1. NY PM pool (7 books)
L2c6916a5.BRP60, L4bdd521a.BRF80_40, L52359bf4.BRP30, L6d238076.BRF90_30, L7b1adff3.BRP60, L8dff280f.BRP90, L8e0bf58c.BRS8U.

## 2. Weighted picks (sizes relative to 1 lot; whole lots x4)
| loop | final set | members (size = whole lots at x4) |
|---|---|---|
| nypm-own-w | TL3_ALN_NP_STKd81d0693ad | L2c6916a5.BRP60 1 (4), L4bdd521a.BRF80_40 1 (4) |
| nypm-own-recent-w | TL3_ALN_NP_STKd8e1d3c0ce | L6d238076.BRF90_30 1 (4), L8dff280f.BRP90 1 (4), L4bdd521a.BRF80_40 2 (8), L8e0bf58c.BRS8U 1 (4), L52359bf4.BRP30 0.5 (2) |
| equal (nypm-own, nypm-own-recent) | TL3_ALN_NP_STKd8b4bcfb9e | L6d238076.BRF90_30 + L8dff280f.BRP90 (1 lot each) |
Delivered stack in the file: STKd893133bd8 (BF2_JT9 / JT209) = L52359bf4.BRP30 + L8e0bf58c.BRS8U + L4bdd521a.BRF80_40 + L2c6916a5.BRP60 (D8_NYPM_NOTES.md; LEAD wrote 3 books: the relay must confirm which are in D8Asia.cs).

## 3. Coding status per book
| book | in the delivered stack | hand-verified spec | page |
|---|---|---|---|
| L2c6916a5 | yes | hand-written block in D8_BUILD_SPEC.md (re-implemented 23 Nov, D8_NYPM_NOTES.md); PAGE D8_NYPM_SPEC_L2c6916a5.md DONE 2026-11-25 (W-NYAMSPEC1; block confirmed correct; not in D8Asia.cs) | AUTO:BOOK:L2c6916a5 + D8_PARITY_L2c6916a5_*.md |
| L4bdd521a | yes | hand-written block; PAGE D8_NYPM_SPEC_L4bdd521a.md DONE 2026-11-25 (W-NYAMSPEC1; not in D8Asia.cs) | AUTO:BOOK:L4bdd521a + D8_PARITY_L4bdd521a_*.md |
| L52359bf4 | yes | hand-written block | AUTO:BOOK:L52359bf4 + D8_PARITY_L52359bf4_*.md |
| L8e0bf58c | yes | hand-written block + volume-book inputs | AUTO:BOOK:L8e0bf58c, D8_NYPM_VOLBOOK_INPUTS.md |
| L6d238076 | no | DONE, 2026-11-25 | autopilot/D8_NYPM_SPEC_L6d238076.md |
| L8dff280f | no | DONE, 2026-11-25 (W-NYAMSPEC1); not in D8Asia.cs | autopilot/D8_NYPM_SPEC_L8dff280f.md |
| L7b1adff3 | no | not in any weighted or equal pick; generic block only; not specified | AUTO:BOOK:L7b1adff3 (generic) |

## 4. Tape and parity inputs
- NY PM raw tape of 20261110 (148,195 records, 12:00-16:00 ET): outputs/autopilot_nomirror/D8_PARITY_TAPE_20261110_NYPM.md (kept out of the mirror), stub autopilot/D8_PARITY_TAPE_20261110_NYPM.md.
- Session-volume tables (45 days, every session code, as stored and hole-filled) are inside D8_NYPM_SPEC_L6d238076.md section 4 (and D8_NYAM_SPEC_L39287638.md Q4d); renko/profile and other inputs per book page.
- Open for all pages: stored vs hole-filled inputs (LEAD decision), TRADES for td 20261110 (engine month 202611 not landed), stack lots and the weighted joint fit, FINAL not declared.

## 5. Verification of the hand-written blocks against the engine (W-NYAMSPEC1, 2026-11-25 ~17:30Z; read-only)
- L52359bf4.BRP30 (tm120 + bands_atrchan fade_ext n40 atr14 k4.0, 30/30): my run of code/d8_spec4/check4.py logic from the stored tm120 bars = events file L52359bf4_R0_P30.parquet 6,863 of 6,863 (0 only-engine, 0 only-mine); stop = target = 30.0 on all rows. Block text correct except one wording point: the block says the bar ending exactly 16:00:00 ET is NY PM; in the stored data it is session code 5 (code/th_swap/common.py:41-44: minute >= 960 -> 5), the NY PM bars are those ending 12:00:00 ... 15:58:00 ET; no effect on signals. NOT in D8Asia.cs. No page written (block is hand-verified).
- L8e0bf58c.BRS8U (anch_PDN_B25 + ZN with_ZN w1 thr1.0, S8U): my run on the stored (plain record) anch_PDN_B25 bars = events 1,861 of 1,861 (928 long, 933 short; stop = target = 120.0 on all rows, as the block says); on the D8 _CANC anchored bars (_d8spec/bars_c/anch_PDN_B25) only 1,102 of 1,861 events are reproduced (1,860 mine, 759 only-engine, 758 only-mine): this CONFIRMS the block's key open point (engine events are on unmerged record bars). NOT in D8Asia.cs. No error found in the block.
