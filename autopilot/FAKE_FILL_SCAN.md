# FAKE_FILL_SCAN (W-FAKEFILL, order 1156Z item 1; written 12:4xZ 2026-11-19; scan definition PREREG_FAKEFILL.md, sha in DECISIONS.md)
Scope: EVERY trades.parquet under /mnt/l2/l2vast on box 1 (230,677 files, 119,439,203 trades, 82 trees; the other hosts' results are pulled into this tree). Read-only, nice 10. Results: autopilot/fakefill/*.csv.
Flags: F1 entry_px < 1000 | F2 exit_px < 1000 | F3 |gross|/lot > $20,000 | F4 exit more than 600 s after the last tape print at or before it (engine tape cache, per-trade month + neighbour-month recheck). Trades whose exit month has no tape (42,515 trades whose exit instant is outside the tape cache's range, 2023-04..2026-11) are counted 'no tape' and NOT flagged.
SCAN ERROR DISCLOSED: my first F4 pass used the tape of the first exit's month for a whole file and produced 16,233 false hits (K7/P7 'Target' exits 0.0003 s after a print); fixed before any number was used; the F4 numbers below are the corrected pass.

## 1. Headline
- **F1 7, F2 183, F3 176, F4 1,750** flagged trades in total (1,752 distinct rows).
- **The artefact is ONE market event: a 10.76 h hole in the tape on 2025-11-28, 02:44:14Z -> 13:30:00Z (a market halt: no prints at all).** Everything fake-priced is a trade whose entry or exit instant falls inside it:
  - 176 TL3_ASI set-months (MF1 exit 2025-11-28 07:00:01Z at -0.25, gross about -506k; one SHORT +506,890 at +0.25) = F2+F3+F4;
  - 7 other trades in 202511, all small: UW1 TL3_UW_FA3P11/P23 (entry at -0.25/+0.25, exit 08:00:02Z: -$40 each, also copies nf_TL3_UW_* in merged_lpb), TL3_MB_FADELV4edbfdf0_L2_P23 (-$10), TL3_UW_INJ_MFC_LDN_P23 (UW1 entered at 0.25 on 07:00:01Z, 'Target' at 60.25 at 13:30:00Z: **+$1,200 fake gain on 1 lot**, also merged_lpb copy).
  - No other F2/F3 anywhere (all other trees: 0 found).
- **F4-only (exit time after the last print, price not garbage): 1,569 trades in 991 flagged set-months (see table 4)**: all 'UWTime'/'ExhCut' exits on early-close / holiday days (2026-09-07 Labor Day, 2026-06-19, 2026-07-03, 2026-05-25, 2025-12-14 etc.): the engine holds the position through the closure and fills at the NEXT print (reopen) instead of the last print before the closure. Median price move vs the last print +2 pts, spread +-16 pts, max -176 / +108 pts. Net effect if they exited at the last print: summed over set-months (the SAME trade repeats in every set of its month, so this is a size indicator, not a P&L): about +516k USD net / 551k gross moved across 809 set-months; per set-month the effect is small (tens to a few hundred USD, up to ~$50k over L6M for the TL3_MB FADELV sets, whose trades hold overnight into the early-close days).

## 2. Counts per tree (every tree; '0 found' stated explicitly)
| tree | trade files | trades | F1 entry<1000 | F2 exit<1000 | F3 gross/lot>20k | F4 exit>600 s after last print | verdict |
|---|---|---|---|---|---|---|---|
| _th_sz/ijk/exact/runs_rf | 106199 | 58617708 | 4 | 180 | 176 | 1481 | FLAGGED |
| _th_sz/ijk/exact/merged_lpb | 98235 | 46479239 | 3 | 3 | 0 | 254 | FLAGGED |
| _th_state/s345/exact_b/runs | 19198 | 10389325 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/merged_ptr | 1648 | 997568 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/merged_rf | 1297 | 659084 | 0 | 0 | 0 | 0 | 0 found |
| _th_exh/stage2/runs | 885 | 481245 | 0 | 0 | 0 | 15 | FLAGGED |
| _th_state/s345/exact_b/runs_rollexcl | 400 | 220141 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs | 412 | 198312 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_rf_void_cde | 309 | 186861 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_id_fastb | 217 | 154345 | 0 | 0 | 0 | 0 | 0 found |
| _th_state/base_b | 233 | 112998 | 0 | 0 | 0 | 0 | 0 found |
| _engvslive/exact/runs_rf | 157 | 104651 | 0 | 0 | 0 | 0 | 0 found |
| _th_state/s2/CD/runs | 169 | 92683 | 0 | 0 | 0 | 0 | 0 found |
| _th_state/base_b_rollfix | 172 | 83867 | 0 | 0 | 0 | 0 | 0 found |
| _th_state/base | 138 | 63942 | 0 | 0 | 0 | 0 | 0 found |
| _th_state/s345/exact_b/quarantine_keybug | 115 | 63376 | 0 | 0 | 0 | 0 | 0 found |
| _th_state/s345/exact/runs | 104 | 63339 | 0 | 0 | 0 | 0 | 0 found |
| _th_p7cut/exact/runs | 67 | 43000 | 0 | 0 | 0 | 0 | 0 found |
| _th_state/s2/CD | 2 | 42134 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/oldbase | 86 | 41261 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_id_fast | 52 | 37386 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/old_nowkey | 37 | 30679 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_id_K | 38 | 28463 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_id_M | 35 | 26510 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_pair_ex | 39 | 26230 | 0 | 0 | 0 | 0 | 0 found |
| (root) | 1 | 23989 | 0 | 0 | 0 | 0 | 0 found |
| _th_redo_replica/G | 43 | 23788 | 0 | 0 | 0 | 0 | 0 found |
| _th_redo_replica/C | 43 | 23788 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_pair_fast | 31 | 20922 | 0 | 0 | 0 | 0 | 0 found |
| _th_state/s345/exact_b/runs_rollexcl_r7 | 32 | 20283 | 0 | 0 | 0 | 0 | 0 found |
| _engvslive/exact_store/runs_rf | 16 | 8178 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_time_base | 9 | 6465 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_time_fast | 9 | 6465 | 0 | 0 | 0 | 0 | 0 found |
| _reentry_all/ev1113b/runs_rf | 15 | 6082 | 0 | 0 | 0 | 0 | 0 found |
| _reentry_all/ev1113/runs_rf | 16 | 5700 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tp/ijk/runs_rf | 6 | 4204 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tp/szx/runs | 5 | 3711 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_recheck | 5 | 3399 | 0 | 0 | 0 | 0 | 0 found |
| _recents | 6 | 2033 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fastprof | 3 | 1994 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tp4/ijk/runs_rf | 2 | 1627 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tp4/szx/runs | 2 | 1592 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/ref/szx/runs | 2 | 1240 | 0 | 0 | 0 | 0 | 0 found |
| _th_state/s345/exact | 2 | 1168 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw12_1/ijk/runs_rf | 1 | 858 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw8_1/ijk/runs_rf | 1 | 858 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw12_9/ijk/runs_rf | 1 | 858 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw4_1/ijk/runs_rf | 1 | 858 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw8_5/ijk/runs_rf | 1 | 858 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw12_5/ijk/runs_rf | 1 | 858 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw4_4/szx/runs | 1 | 823 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw8_8/szx/runs | 1 | 823 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw12_8/szx/runs | 1 | 823 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw8_4/szx/runs | 1 | 823 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw12_12/szx/runs | 1 | 823 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw12_4/szx/runs | 1 | 823 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw12_11/szx/runs | 1 | 769 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw4_3/szx/runs | 1 | 769 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw8_3/szx/runs | 1 | 769 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw4_2/ijk/runs_rf | 1 | 769 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw12_7/szx/runs | 1 | 769 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw12_6/ijk/runs_rf | 1 | 769 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw8_6/ijk/runs_rf | 1 | 769 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw12_2/ijk/runs_rf | 1 | 769 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw12_10/ijk/runs_rf | 1 | 769 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw12_3/szx/runs | 1 | 769 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw8_7/szx/runs | 1 | 769 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/tpw8_2/ijk/runs_rf | 1 | 769 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_vf2 | 1 | 658 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_nx1 | 1 | 658 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_nx2 | 1 | 658 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_prof3 | 1 | 658 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_nx4 | 1 | 658 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_fastprof2 | 1 | 658 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_fast2 | 1 | 658 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_fast3 | 1 | 658 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_fast | 1 | 658 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_base | 1 | 658 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_fastprof | 1 | 658 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_nx3 | 1 | 658 | 0 | 0 | 0 | 0 | 0 found |
| _th_sz/ijk/exact/runs_fl_nx5 | 1 | 658 | 0 | 0 | 0 | 0 | 0 found |
| _th_tp/id/ref/ijk/runs_rf | 1 | 360 | 0 | 0 | 0 | 0 | 0 found |

Flagged families (all others: 0 found):
| tree | set family | files | trades | F1 | F2 | F3 | F4 |
|---|---|---|---|---|---|---|---|
| _th_sz/ijk/exact/runs_rf | TL3_MB | 1053 | 607907 | 1 | 1 | 0 | 570 |
| _th_sz/ijk/exact/runs_rf | TL3_NYE | 2733 | 1830469 | 0 | 0 | 0 | 366 |
| _th_sz/ijk/exact/runs_rf | TL3_UW | 1261 | 744581 | 3 | 3 | 0 | 275 |
| _th_sz/ijk/exact/merged_lpb | nf | 5298 | 2834575 | 3 | 3 | 0 | 254 |
| _th_sz/ijk/exact/runs_rf | TL3_ASI | 17261 | 10512444 | 0 | 176 | 176 | 176 |
| _th_sz/ijk/exact/runs_rf | TL3_NYW | 2405 | 1477625 | 0 | 0 | 0 | 67 |
| _th_sz/ijk/exact/runs_rf | TL3_TKB | 662 | 336251 | 0 | 0 | 0 | 13 |
| _th_sz/ijk/exact/runs_rf | TL3_FR | 50 | 35601 | 0 | 0 | 0 | 11 |
| _th_exh/stage2/runs | phi | 130 | 71937 | 0 | 0 | 0 | 8 |
| _th_exh/stage2/runs | N | 139 | 112487 | 0 | 0 | 0 | 4 |
| _th_sz/ijk/exact/runs_rf | TL3_FL | 984 | 652983 | 0 | 0 | 0 | 3 |
| _th_exh/stage2/runs | ldef | 91 | 48596 | 0 | 0 | 0 | 2 |
| _th_exh/stage2/runs | nt | 129 | 56982 | 0 | 0 | 0 | 1 |

## 3. Which verdicts told to Josh used a month with such a trade (scan, not argument)
- Asia / NY AM / NY PM / London LADDER cells in the 18 beats-live candidates (autopilot/D8_CANDIDATES.txt yes rows): **13 of the 14 Asia candidates carry the 11-28 artefact in 202511 ONLY** (L05222ff9, L0a809c2e, L0b1d7882, L17ce266f, L1edb9fab, L5c9e11b3, L5d9e7166, L7c368a4f, La5b5d03a, Lcb276f27, Lda55d973, Ledfbf4d2, Lf77e374b; 2-4 set-months each); the 4 NY AM candidates (L6a25b155, L01811caa, L0f097450, L3701b464) and the 14th Asia candidate L63ff9ae8 have NO flagged trade in any month.
- **L6M / L3M rows (202605-202610): 0 flagged trades in ANY ladder-cell set (TL3_ASI/NYE/NYW/LON_L<hex>/M<hex>) in those months: the Asia and NY AM L6M/L3M verdict rows are CLEAN by scan.** The Asia rule-B 2025 colours were the contaminated ones (W-ASIA's F sets re-run those months).
- F4-only flags in 202605-202610 exist in OTHER families: TL3_MB FADELV / O7V1000 (L2 P11/P23/P37), TL3_UW INJ (MFB1/MFC), NY PM lead sets TL3_NYE_*WP10*/WP1/NP2/NP4/NP5/NP6 (about 12 trades per set; +-$1k per set). Pages using them: NY PM WP10/WP1 pages (NEW_BOOK_SHORTLIST WP10 rows), the MB/UW (UW event book) pages: their numbers moved by well under $1,100 per NY PM set but up to ~$50k for the TL3_MB FADELV sets over L6M (table 4): **re-check TL3_MB FADELV and TL3_UW INJ rows before they are quoted.**
- Near-target (TL3_NT_), ORB (TL3_MF_ORB*), XA3 and its layer sets (TL3_NYL_), exit-engine (TL3_EXE_), controls, JL3/EV baselines, AX/AB lead cells (in runs_rf): 0 found.

## 4. F4-only trades: price impact (exit at the last print instead of the next print), per tree/family
| tree | family | F4-only trades | sets | net $ if exited at the last print | gross $ moved |
|---|---|---|---|---|---|
| _th_exh/stage2/runs | N | 4 | 4 | +89 | 135 |
| _th_exh/stage2/runs | ldef | 2 | 2 | +1622 | 1622 |
| _th_exh/stage2/runs | nt | 1 | 1 | -39 | 39 |
| _th_exh/stage2/runs | phi | 8 | 3 | -775 | 3398 |
| _th_sz/ijk/exact/merged_lpb | nf | 252 | 11 | +76590 | 76590 |
| _th_sz/ijk/exact/runs_rf | TL3_FL | 3 | 3 | +550 | 550 |
| _th_sz/ijk/exact/runs_rf | TL3_FR | 11 | 11 | -110 | 110 |
| _th_sz/ijk/exact/runs_rf | TL3_MB | 569 | 19 | +317680 | 317910 |
| _th_sz/ijk/exact/runs_rf | TL3_NYE | 366 | 82 | +36950 | 50180 |
| _th_sz/ijk/exact/runs_rf | TL3_NYW | 67 | 12 | +2975 | 6695 |
| _th_sz/ijk/exact/runs_rf | TL3_TKB | 13 | 4 | +8185 | 8185 |
| _th_sz/ijk/exact/runs_rf | TL3_UW | 273 | 13 | +72050 | 85860 |
Set-months containing at least one flagged trade (any flag): 991 (table 5 by tree/family):
| tree | family | set-months containing >=1 flagged trade |
|---|---|---|
| _th_exh/stage2/runs | N | 4 |
| _th_exh/stage2/runs | ldef | 2 |
| _th_exh/stage2/runs | nt | 1 |
| _th_exh/stage2/runs | phi | 7 |
| _th_sz/ijk/exact/merged_lpb | nf | 104 |
| _th_sz/ijk/exact/runs_rf | TL3_ASI | 176 |
| _th_sz/ijk/exact/runs_rf | TL3_FL | 3 |
| _th_sz/ijk/exact/runs_rf | TL3_FR | 11 |
| _th_sz/ijk/exact/runs_rf | TL3_MB | 144 |
| _th_sz/ijk/exact/runs_rf | TL3_NYE | 349 |
| _th_sz/ijk/exact/runs_rf | TL3_NYW | 60 |
| _th_sz/ijk/exact/runs_rf | TL3_TKB | 11 |
| _th_sz/ijk/exact/runs_rf | TL3_UW | 119 |

## 5. Convention (lead decision) and builders (item c)
ONE convention N = 120 s everywhere (DECISIONS.md 'FAKE-FILL CONVENTION'): if no print follows the scheduled exit instant within 120 s, the event exits at the LAST print at or before it (floored to the second, never earlier than entry + 1 s). Reference implementation: code/th_fakefill/cap_exit.py (matches th_asia/asia_fix.py).
| builder | file | rule today | status |
|---|---|---|---|
| Asia (F sets) | th_asia/asia_fix.py | next-print gap > 120 s -> last print (floored) | OK (was 600 s until 12:00Z; backup .bak_gap600_1200). Differs from cap_exit.py on one early-close NY PM test event (asia_fix left it uncapped) |
| NY / London / Asia ladder events | th_nyeng/ny_build.py events() (used by lx_build.py, lon_build.py, asia_ladder.py) | NONE: exit_ts = sess_end_ns(t) | NOT capped: exposed on every NY PM early-close day and any halt; patch below |
| exit-engine | th_exiteng/ex_events.py | gap BEFORE the exit > 120 s -> last print - 1 s | different criterion and 1 s offset; equivalent on the 11-28 case; align to cap_exit.py |
EXACT PATCH for ny_build.py (not applied; owner W-NYENG): in events(), replace line `ev = ev[ev.ts < ev.exit_ts].sort_values('ts').reset_index(drop=True)` by
`import sys; sys.path.insert(0, 'code/th_fakefill'); import cap_exit; ev, _ncap = cap_exit.cap_events(ev); ev = ev[ev.ts < ev.exit_ts].sort_values('ts').reset_index(drop=True)`
(and for ex_events.py replace the inline last-print cap block by the same two calls).
**Engine behaviour (not changed):** an exit with no print is filled at about -0.25 (and an ENTRY with no print at -0.25/+0.25: the UW1 trades above): it must never be possible to land such a month. GUARD (item c): code/th_fakefill/guard_check.py: opt-in post-check; `guard_or_fail(T, outdir, ym)` writes FAILED_FAKEFILL.json and RAISES before DONE; CLI exit code 2. Tested: the known bad month TL3_ASI_AB1_ADD/202511 -> 1 offender (MF1, exit_px -0.25, gross -506,445, gap 15,346 s) -> RAISED; clean month TL3_ASI_L514776c8_ADD/202304 -> 0. EXACT LAUNCHER EDIT (not applied; the launchers are other agents' files): in th_sz_ijk/state_sizer_ijk_wg.py, directly BEFORE each `T.to_parquet(O + 'trades.parquet')` (lines 132 and 184) insert
`import sys; sys.path.insert(0, 'code/th_fakefill'); import guard_check; guard_check.guard_or_fail(T, O, ym)`
so a set-month with a fake fill raises (the existing except path reports ERR) and never writes trades.parquet/DONE. FAKEFILL_GUARD=0 = log only. Add the same call in the S2/S3 engine runner and th_fastladder/fl_launch.py if they write DONE elsewhere (grep 'DONE' showed only the two sites above in th_sz_ijk; the TL3 runs_rf trees are written there).

## 6. Exposed session ends 2023-04..2026-10 (item d; code/th_fakefill/expo.py; exposed_session_ends.csv)
Exposed = the last print at or before the ET session end (Asia 02:00, London 08:30, NY AM 12:00, NY PM 16:00) is > 120 s early and not before the session start. **34 exposed ends: Asia 1, NY PM 33, London 0, NY AM 0.** (Weekend/holiday sessions with no print at all, 1,526, carry no trades.)
| session | date | end (UTC) | last print (UTC) | seconds early |
|---|---|---|---|---|
| NY PM | 2023-05-29 | 2023-05-29 20:00 | 2023-05-29 16:59:57 | 10802 |
| NY PM | 2023-06-19 | 2023-06-19 20:00 | 2023-06-19 16:59:59 | 10800 |
| NY PM | 2023-07-03 | 2023-07-03 20:00 | 2023-07-03 17:14:58 | 9901 |
| NY PM | 2023-07-04 | 2023-07-04 20:00 | 2023-07-04 16:59:59 | 10800 |
| NY PM | 2023-09-04 | 2023-09-04 20:00 | 2023-09-04 16:59:59 | 10800 |
| NY PM | 2023-11-23 | 2023-11-23 21:00 | 2023-11-23 17:59:56 | 10804 |
| NY PM | 2023-11-24 | 2023-11-24 21:00 | 2023-11-24 18:14:59 | 9900 |
| NY PM | 2024-01-15 | 2024-01-15 21:00 | 2024-01-15 17:59:59 | 10800 |
| NY PM | 2024-02-19 | 2024-02-19 21:00 | 2024-02-19 17:59:59 | 10801 |
| NY PM | 2024-05-27 | 2024-05-27 20:00 | 2024-05-27 16:59:59 | 10801 |
| NY PM | 2024-06-19 | 2024-06-19 20:00 | 2024-06-19 16:59:59 | 10801 |
| NY PM | 2024-07-03 | 2024-07-03 20:00 | 2024-07-03 17:14:59 | 9900 |
| NY PM | 2024-07-04 | 2024-07-04 20:00 | 2024-07-04 16:59:59 | 10800 |
| NY PM | 2024-09-02 | 2024-09-02 20:00 | 2024-09-02 16:59:59 | 10801 |
| NY PM | 2024-11-28 | 2024-11-28 21:00 | 2024-11-28 17:59:59 | 10800 |
| NY PM | 2024-11-29 | 2024-11-29 21:00 | 2024-11-29 18:14:59 | 9900 |
| NY PM | 2024-12-24 | 2024-12-24 21:00 | 2024-12-24 18:14:59 | 9900 |
| NY PM | 2025-01-20 | 2025-01-20 21:00 | 2025-01-20 17:59:59 | 10800 |
| NY PM | 2025-02-17 | 2025-02-17 21:00 | 2025-02-17 17:59:59 | 10800 |
| NY PM | 2025-05-26 | 2025-05-26 20:00 | 2025-05-26 16:59:59 | 10801 |
| NY PM | 2025-06-19 | 2025-06-19 20:00 | 2025-06-19 16:59:59 | 10801 |
| NY PM | 2025-07-03 | 2025-07-03 20:00 | 2025-07-03 17:14:59 | 9900 |
| NY PM | 2025-07-04 | 2025-07-04 20:00 | 2025-07-04 16:59:59 | 10800 |
| NY PM | 2025-09-01 | 2025-09-01 20:00 | 2025-09-01 16:59:59 | 10800 |
| NY PM | 2025-11-27 | 2025-11-27 21:00 | 2025-11-27 17:59:59 | 10801 |
| Asia | 2025-11-28 | 2025-11-28 07:00 | 2025-11-28 02:44:14 | 15345 |
| NY PM | 2025-11-28 | 2025-11-28 21:00 | 2025-11-28 18:14:59 | 9900 |
| NY PM | 2025-12-24 | 2025-12-24 21:00 | 2025-12-24 18:14:58 | 9901 |
| NY PM | 2026-01-19 | 2026-01-19 21:00 | 2026-01-19 17:59:59 | 10800 |
| NY PM | 2026-02-16 | 2026-02-16 21:00 | 2026-02-16 17:59:59 | 10800 |
| NY PM | 2026-05-25 | 2026-05-25 20:00 | 2026-05-25 16:59:58 | 10801 |
| NY PM | 2026-06-19 | 2026-06-19 20:00 | 2026-06-19 16:59:59 | 10800 |
| NY PM | 2026-07-03 | 2026-07-03 20:00 | 2026-07-03 16:59:59 | 10801 |
| NY PM | 2026-09-07 | 2026-09-07 20:00 | 2026-09-07 16:59:59 | 10801 |
Re-run needs (set-months that can contain an exit at an exposed end; only sets with trades in that session): Asia: 2025-11-28 (202511): the 176 TL3_ASI sets (W-ASIA's F sets, 157 queued/landing) + TL3_UW_FA3P11/P23, TL3_UW_INJ_MFC_LDN_P23, TL3_MB_FADELV4edbfdf0_L2_P23 (202511) and the merged_lpb nf_ copies; NY PM: every NY PM set (TL3_NYE/NYW NY PM cells and the WP10/WP1/NP lead sets, TL3_MB, TL3_UW INJ) in the 33 months containing those dates: the flagged set-months in table 5 are the ones with an actual trade at such an end (F4 flag); cells that never held to the NY PM end on those days are unaffected. Months to re-run after the cap_exit patch: 2025-11, 2026-05/06/07/09 first (L6M window), then 2023-05..2025-12 holidays.
