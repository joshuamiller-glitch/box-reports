# CAP FIDELITY AUDIT (same-side lots cap 6, 'cap6_trunc')
Written 2026-11-24 by the audit agent. Read-only plus 30 queued cap-off rows. No re-fit, no pick changed.

## 1. What the cap is (file:line)
- Set JSON field `cde` = {code 8, P [6, 0], bmask 127, smask 2, id 'E|same_side_lots_cap|cap6_trunc|sess_london'}.
- Code: code/th_sz_cde/cde_exact.py, `CdeRep.ntz_check` (line 163-169) calls `cde_mult` (line 93+). Code 8 is at line 130-132:
  `room = P[0] - same; if lots > room: m = 0 if (P[1]==1 or room<=0) else room/lots`.
- `same` = open lots (or pending entry lots) of all OTHER books on the same side, summed over the whole set (line 125).
- What is cut: the lots of the NEW entry. They are truncated to `room` (min 1 through rnd). If room <= 0 the entry is skipped ("CDE skip"). Earlier books are untouched.
- Gates (line 96): applies only if the entering book's bit is in bmask AND the session bit is in smask. smask 2 = session 1 = London only. bmask 127 = bits 0..6 = the seven old books (SB_BI K7 P7 M7 U7 A7 H7 O7).
- Every new-book stream (MF1..MF5) is registered with SB_BI = 7 (code/th_combo/mf_multi.py:30-31). Bit 7 is not in bmask 127, so `cde_mult` returns 1.0 at once. In addition, where `lin ntz = 'off'` (Asia, NY PM, London sets) mf_multi.ntz_check returns before it reaches the CdeRep (mf_multi.py:64).
- Result: the cap is structurally inert for every new-book (MF) stream in every session. It can only touch the old seven books, and those are swapped off in all D8 sets. It is also London-only in any case (D8_ASSUMPTIONS row 27 says the same).

## 2. Per delivered set (L6M 202605-202610; trades from runs_rf)
| set | cap in JSON | applies to MF books? | trades L6M | max same-side lots open incl. entry | entries with >6 |
|---|---|---|---|---|---|
| Asia J502 BF2_JT6 | 6, London, bmask 127 | no | 172 | 2 | 0 |
| Asia 4-book BF2_JT110 | same | no | 1564 | 6 | 0 |
| NY AM BF2_JT68 | same | no | 1695 | 6 | 0 |
| NY PM BF2_JT209 | same | no | 1349 | 6 | 0 |
| London bare BF2_BASE (L19201dfc) | same | no (one book, 2 lots) | 246 | 2 | 0 |
Same-side concurrency (NY AM): 1 lot 805, 2 lots 654, 3 lots 167, 4 lots 59, 5 lots 6, 6 lots 4. The nominal 4-5 books x 2 lots = 8-10 is never reached.
Entries/lots refused or truncated by the cap on L6M: 0 in every session (by construction and by the trade overlap count above).
All BF1/BF2/BF4/BF6 set JSONs carry the same `cde` (code 8, 6, smask 2). The merged/combined sets behind D8_ALL_SESSIONS_COMBINED.md are those same BF2 sets (whole-stack runs), so the same answer holds.
Corollary for the relay report: the live file's missing cap is NOT a fidelity gap for the new books. The engine cap never acted on them either.

## 3. Cap-off confirmation runs (pending)
Cap-off copies built (`cde` removed) in /mnt/l2/l2vast/_th_sz/ijk/exact/sets/: TL3_SR_AS_L385f4f2e_P2JCX502_BF2_JT6_CAPOFF, TL3_SR_AS_STKd8da2eb47b_BF2_JT110_CAPOFF, TL3_SR_NY_STKd8b76ecd35_BF2_JT68_CAPOFF, TL3_SR_NP_STKd893133bd8_BF2_JT209_CAPOFF, TL3_SR_LO_L19201dfc_R0BRF90_30_BF2_BASE_CAPOFF.
Queued 30 rows (5 sets x 202605..202610): Asia 12 rows in pending_asia_gating.txt (about 1,700 rows ahead), NY AM, NY PM and London 18 rows in pending_stack_urgent.txt.
Expected result: trades identical to the capped sets (with-cap vs cap-off L6M and L3M $/wk, ulcer and max DD equal). The prediction is NOT yet verified by the runs. Compare with `runs_rf/<set>_CAPOFF/<ym>/trades.parquet` against `runs_rf/<set>/<ym>/trades.parquet` once the rows land. A combined-set cap-off was not queued, because it adds no merged-set JSON beyond these five.

## 4. Cap-off results (updated by W-CAPAUDIT)
- Asia J502 JT6 and Asia 4-book JT110, all 6 L6M months: 12/12 month files IDENTICAL (trade count and every column equal, e.g. JT110 221/299/332/203/222/287 trades, 0 differing). With-cap = cap-off, so $/wk, ulcer and max DD differ by 0.
- NY AM, NY PM, London: 18 rows wired to _split/pending_cap_audit.txt (QUEUES line 5; the rows vanished twice from pending_stack_urgent.txt). Not landed at the time of this update.
