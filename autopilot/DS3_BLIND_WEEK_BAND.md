# DS3_BLIND_WEEK_BAND - uncertainty band of the blind prediction (ZL-2, 2026-11-06T01:19Z)
Ranges only; the point estimate is BASE-4's frozen config (composed week, 11-01 18:00 ET to 11-05 11:05 ET). Grid prereg: l2vast/ds3/prereg/BLIND_UNCERTAINTY_scope.md sha256 5b36c360dd44d9552d084c4a0716c898edf670e316db2342b82fa22a337f3dd1 (filed before any variant ran; changes from the prereg: F2 entry delay NOT RUN because the engine only has the 1-s grid switch, replaced by the single available alternative grid=1s (0-s delay); F5 done as P0 re-run with th_loss and th_profit off for entries before Mon 02:00 ET, composed in). Harness: blind_run.py unchanged, SLOTS=1, NOX=1 (Z1 X trades added by blind_week.compose), final data P2. Each variant is a full 3-period replay in a fresh process.

Centre reproduces the sealed point estimate: $34,879 on 182 closed trades (182 entries).

## Total net by variant

| variant | total net \$ | delta vs centre | trades | longs/shorts |
|--|--|--|--|--|
| centre | 34,879 | +0 | 182 | 82/100 |
| F1_stop0 | 35,060 | +181 | 182 | 82/100 |
| F1_stop1.5 | 34,955 | +76 | 182 | 82/100 |
| F1_stop3.5 | 34,795 | -84 | 182 | 82/100 |
| F3_mx0.5 | 54,257 | +19,378 | 191 | 90/101 |
| F3_mx1.2 | 33,011 | -1,868 | 182 | 82/100 |
| F4_cut+2 | 42,986 | +8,108 | 191 | 90/101 |
| F4_cut+3.5 | 18,736 | -16,142 | 182 | 82/100 |
| F2b_grid1s | 34,879 | +0 | 182 | 82/100 |
| F5_noL2_sun8h | 35,452 | +574 | 182 | 82/100 |
| CORNER_fav | 54,438 | +19,559 | 191 | 90/101 |
| CORNER_unfav | 16,785 | -18,094 | 182 | 82/100 |

## Factor swings (max minus min of total net over the factor levels)

| factor | low | high | swing |
|--|--|--|--|
| F1 stop slippage (0..3.5 pt) | 34,795 | 35,060 | 265 |
| F3 market exit (0.5..1.2 pt) | 33,011 | 54,257 | 21,246 |
| F4 cut exit cost (+0..3.5 pt) | 18,736 | 42,986 | 24,250 |
| F2b entry grid 1s vs 1sh | 34,879 | 34,879 | 0 |
| F5 L2 off first 8 h Sunday | 34,879 | 35,452 | 574 |

Dominant factor on the total: **F4 cut exit cost (+0..3.5 pt)** (swing $24,250).

Total-net range over all single-factor variants: $18,736 to $54,257; outer corners: CORNER_unfav $16,785, CORNER_fav $54,438.

## Per book (net \$, centre and range over single-factor variants; dominant = factor with the largest swing for that book)

| book | centre | min | max | dominant factor |
|--|--|--|--|--|
| A6 | 9,067 | 8,983 | 9,248 | F1 stop slippage (0..3.5 pt) |
| H6 | 9,266 | 8,034 | 20,946 | F4 cut exit cost (+0..3.5 pt) |
| K6 | 10,319 | 7,695 | 18,907 | F4 cut exit cost (+0..3.5 pt) |
| M6 | 2,490 | 750 | 2,621 | F4 cut exit cost (+0..3.5 pt) |
| P6 | 2,404 | -7,286 | 2,404 | F4 cut exit cost (+0..3.5 pt) |
| U6 | 6,675 | 5,818 | 6,711 | F4 cut exit cost (+0..3.5 pt) |
| X3 | -6,215 | -6,215 | -6,215 | F1 stop slippage (0..3.5 pt) |
| X4 | -1,517 | -1,517 | -1,517 | F1 stop slippage (0..3.5 pt) |
| X5 | 2,390 | 2,390 | 2,390 | F1 stop slippage (0..3.5 pt) |

## Per exit day (net \$)

| day | centre | min | max | dominant factor |
|--|--|--|--|--|
| Sun 11-01 | 3,673 | 3,673 | 17,344 | F3 market exit (0.5..1.2 pt) |
| Mon 11-02 | -22,606 | -25,545 | -18,047 | F4 cut exit cost (+0..3.5 pt) |
| Tue 11-03 | 24,176 | 17,743 | 24,728 | F4 cut exit cost (+0..3.5 pt) |
| Wed 11-04 | 31,247 | 27,059 | 31,623 | F4 cut exit cost (+0..3.5 pt) |
| Thu 11-05 | -1,612 | -4,194 | -1,391 | F4 cut exit cost (+0..3.5 pt) |

## Exit types in the centre and the F4/F5 variants (count / net \$)

- centre: lock 4/-3,429; other 2/1,733; stop 7/-14,338; target 84/190,459; thl2_cut 85/-139,546
- F4_cut+3.5: lock 4/-3,229; other 2/1,733; stop 7/-14,338; target 84/190,459; thl2_cut 85/-155,888
- F5_noL2_sun8h: lock 4/-3,429; stop 9/-20,317; target 86/195,364; thl2_cut 83/-136,166

## Block for the uncertainty paragraph
Over the filled-in fill-model grid the total net of the composed week stays between $16,785 and $54,438 (single-factor variants $18,736 to $54,257), versus the point estimate $34,879. The entry-delay factor (0.5 s / 2 s) could not be run in the engine; the L2 reconstruction factor covers only the first 8 h of Sunday night. These are fill-model ranges, not statistical intervals: the replay is deterministic.

## Reading the band (ZL-2)
1. The totals are NOT smooth in the cost parameters. Stop slippage (0 to 3.5 pt) moves the total by only $265 (stops are a small share of this week). Market exit 0.5 pt and the cut-cost +2 variant ADD 9 trades (191 instead of 182) and jump by +$19.4k and +$8.1k, while cut cost +3.5 pt subtracts $16.1k and market exit 1.2 pt $1.9k. The cause is the path-dependent per-book lock/day-halt rules: a small change in realised P&L moves the moment a book hits its day give-back or the +/-R day caps, which opens or removes whole trades (P6 and K6 carry the largest swings; P6 is -$7.3k at the unfavourable end). The band is therefore a statement about which lock states are reached, not a +/- cost effect; the sealed point estimate sits inside a wide, jumpy range.
2. F2b (grid=1s, a 0-s entry delay) gave exactly the centre result on every trade: the override is not taking effect in the harness (the grid switch is probably fixed by the harness config), so the entry-delay factor is NOT RUN, as BASE-4 said.
3. F5 (L2-dependent rules off for entries before Mon 02:00 ET) moves the total by +$574: the first 8 h of Sunday night hold few L2-dependent decisions in this replay, so degraded-stream risk on 2026-11-01 is small compared with the cut-cost and market-exit factors.
4. Lock exits per variant (count): centre 4, F1_stop0 4, F3_mx0.5 4, F3_mx1.2 4, F4_cut+2 4, F4_cut+3.5 4, F5_noL2_sun8h 4
5. Not covered: the L2 reconstruction itself (queue/pulled-support features) was varied only through the 8-h exclusion; the fill model for 70/30 slices and the platform-restart handling are as frozen by BASE-4. Ranges only; no probabilities.

## CORRECTION 2026-11-06T01:20:09Z (ZL-2) to item 1 and item 4 above: the jumps are NOT lock-rule effects
Lock exits are 4 in every variant (item 4), so the explanation in item 1 (lock/day-halt states) is withdrawn. A trade-level diff against the centre shows the real mechanism: F3_mx0.5, F4_cut+2 and CORNER_fav contain exactly 9 extra entries, identical in all three: H6 Sun 18:02, K6 Sun 18:03, P6 Sun 18:36, K6 Sun 18:42, P6 Sun 19:04, H6 Sun 20:32, P6 Sun 20:38, P6 Sun 21:10, P6 Mon 05:01 (net +$7,282 +$3,823 +$3,346 +$3,672 -$6,391 -$1,664 -$3,229 +$2,425 +$4,850 in F3_mx0.5, about +$14.1k together). No entry of the centre disappears. These 9 trades are absent from the centre (the sealed 182) and from F1, F3_mx1.2, F4_cut+3.5, F5 and CORNER_unfav, and present in the variants with xcost 0.5 or cut extra +2.0: non-monotone in cutx (0 no, +2 yes, +3.5 no), and a cost change on EXITS cannot causally create ENTRIES at Sunday 18:02. So the first ~11 h of the P0 period is unstable in the harness: whether the first Sunday-night trades of K6/H6/P6 appear depends on something other than the cost knob (state or ordering inside the replay, e.g. the P0 slot arrays or the order of the two passes captured by CAP names ending _r1). This is a finding about the harness, not a fill-model range; the part of the band that comes from it (F3_mx0.5 +$19.4k, F4_cut+2 +$8.1k, CORNER_fav +$19.6k) should not be quoted as fill-model uncertainty until BASE-4 explains it. The clean fill-model ranges, without the 9 trades, are: stop slippage 0..3.5 pt $34.8k to $35.1k; market exit 1.2 pt $33.0k; cut extra +3.5 pt $18.7k (a real exit-cost effect on the cut trades); L2-off-8h $35.5k; CORNER_unfav $16.8k.

## SUPERSEDED 2026-11-06T01:36:58Z (ZL-2): every number, table and reading above this line (the first version, including the 'Reading the band' items and the CORRECTION about the nine Sunday-night entries) was produced with the pre-fix blind_run.py (ledger() hard-coded the final pass as '_r1'; BASE-4 sealed code blind_run_SEALED_0ad2308f.py). It is kept for the record only. The fixed harness is blind_run.py sha256 7a1562fc... The corrected block below replaces it.
# DS3_BLIND_WEEK_BAND CORRECTED BLOCK - uncertainty band of the blind prediction (fixed harness blind_run.py sha256 7a1562fc..., supersedes the first version) (ZL-2, 2026-11-06T01:36Z)
Ranges only; the point estimate is BASE-4's frozen config (composed week, 11-01 18:00 ET to 11-05 11:05 ET). Grid prereg: l2vast/ds3/prereg/BLIND_UNCERTAINTY_scope.md sha256 5b36c360dd44d9552d084c4a0716c898edf670e316db2342b82fa22a337f3dd1 (filed before any variant ran; changes from the prereg: F2 entry delay NOT RUN because the engine only has the 1-s grid switch, replaced by the single available alternative grid=1s (0-s delay); F5 done as P0 re-run with th_loss and th_profit off for entries before Mon 02:00 ET, composed in). Harness: FIXED blind_run.py (final pass = last run_book4 call per book; ledger sum asserted equal to the engine cube sum), SLOTS=1, NOX=1 (Z1 X trades added by blind_week.compose), final data P2. Each variant is a full 3-period replay in a fresh process.

Centre reproduces the sealed point estimate: $34,879 on 182 closed trades (182 entries).

## Total net by variant

| variant | total net \$ | delta vs centre | trades | longs/shorts |
|--|--|--|--|--|
| centre | 34,879 | +0 | 182 | 82/100 |
| F1_stop0 | 35,060 | +181 | 182 | 82/100 |
| F1_stop1.5 | 34,955 | +76 | 182 | 82/100 |
| F1_stop3.5 | 34,795 | -84 | 182 | 82/100 |
| F3_mx0.5 | 36,279 | +1,401 | 182 | 82/100 |
| F3_mx1.2 | 33,011 | -1,868 | 182 | 82/100 |
| F4_cut+2 | 25,820 | -9,058 | 182 | 82/100 |
| F4_cut+3.5 | 18,736 | -16,142 | 182 | 82/100 |
| F2b_grid1s | 34,879 | +0 | 182 | 82/100 |
| F5_noL2_sun8h | 35,452 | +574 | 182 | 82/100 |
| CORNER_fav | 36,460 | +1,582 | 182 | 82/100 |
| CORNER_unfav | 16,785 | -18,094 | 182 | 82/100 |

## Factor swings (max minus min of total net over the factor levels)

| factor | low | high | swing |
|--|--|--|--|
| F1 stop slippage (0..3.5 pt) | 34,795 | 35,060 | 265 |
| F3 market exit (0.5..1.2 pt) | 33,011 | 36,279 | 3,268 |
| F4 cut exit cost (+0..3.5 pt) | 18,736 | 34,879 | 16,142 |
| F2b entry grid 1s vs 1sh | 34,879 | 34,879 | 0 |
| F5 L2 off first 8 h Sunday | 34,879 | 35,452 | 574 |

Dominant factor on the total: **F4 cut exit cost (+0..3.5 pt)** (swing $16,142).

Total-net range over all single-factor variants: $18,736 to $36,279; outer corners: CORNER_unfav $16,785, CORNER_fav $36,460.

## Per book (net \$, centre and range over single-factor variants; dominant = factor with the largest swing for that book)

| book | centre | min | max | dominant factor |
|--|--|--|--|--|
| A6 | 9,067 | 8,983 | 9,248 | F1 stop slippage (0..3.5 pt) |
| H6 | 9,266 | 8,034 | 11,546 | F5 L2 off first 8 h Sunday |
| K6 | 10,319 | 7,695 | 10,979 | F4 cut exit cost (+0..3.5 pt) |
| M6 | 2,490 | 750 | 2,639 | F4 cut exit cost (+0..3.5 pt) |
| P6 | 2,404 | -7,286 | 3,234 | F4 cut exit cost (+0..3.5 pt) |
| U6 | 6,675 | 5,818 | 6,748 | F4 cut exit cost (+0..3.5 pt) |
| X3 | -6,215 | -6,215 | -6,215 | F1 stop slippage (0..3.5 pt) |
| X4 | -1,517 | -1,517 | -1,517 | F1 stop slippage (0..3.5 pt) |
| X5 | 2,390 | 2,390 | 2,390 | F1 stop slippage (0..3.5 pt) |

## Per exit day (net \$)

| day | centre | min | max | dominant factor |
|--|--|--|--|--|
| Sun 11-01 | 3,673 | 3,673 | 6,846 | F5 L2 off first 8 h Sunday |
| Mon 11-02 | -22,606 | -25,545 | -22,354 | F4 cut exit cost (+0..3.5 pt) |
| Tue 11-03 | 24,176 | 17,743 | 24,728 | F4 cut exit cost (+0..3.5 pt) |
| Wed 11-04 | 31,247 | 27,059 | 31,623 | F4 cut exit cost (+0..3.5 pt) |
| Thu 11-05 | -1,612 | -4,194 | -1,391 | F4 cut exit cost (+0..3.5 pt) |

## Exit types in the centre and the F4/F5 variants (count / net \$)

- centre: lock 4/-3,429; other 2/1,733; stop 7/-14,338; target 84/190,459; thl2_cut 85/-139,546
- F4_cut+3.5: lock 4/-3,229; other 2/1,733; stop 7/-14,338; target 84/190,459; thl2_cut 85/-155,888
- F5_noL2_sun8h: lock 4/-3,429; stop 9/-20,317; target 86/195,364; thl2_cut 83/-136,166

## Block for the uncertainty paragraph
Over the filled-in fill-model grid the total net of the composed week stays between $16,785 and $36,460 (single-factor variants $18,736 to $36,279), versus the point estimate $34,879. The entry-delay factor (0.5 s / 2 s) could not be run in the engine; the L2 reconstruction factor covers only the first 8 h of Sunday night. These are fill-model ranges, not statistical intervals: the replay is deterministic.

## Corrected block: harness checks (2026-11-06T01:37:15Z, ZL-2)
- Fixed harness: blind_run.py sha256 7a1562fc227c... (checked on disk before the run). One fresh process per variant, 12 variants, 3 workers.
- P0-window entries (entry before Mon 08:50 ET, non-X books): 12 in the centre. In ALL 12 variants the P0-window entry set equals the centre's (True for every variant), so the nine extra Sunday-night entries of the first version do not appear: no variant has a different entry set in P0.
- Passes seen per period and variant: b, r0, r1 in every period of every variant (3 of 3); the ledger-equals-cube-sum assertion of the fixed ledger() passed in all 36 period runs (no exception).
- Why the first version showed nine extra entries: my runner called BR.ledger(r) unchanged and applied no pass or mask of its own; with the old ledger() the final pass was taken as the CAP name ending '_r1', so in runs where the U7 blackout converged in fewer passes the ledger was empty or built from a different pass (BASE-4's finding). The nine entries were a ledger-pass artefact of the old harness, not an engine result and not a runner fallback of mine; the empty P0 ledger on a second call in one process had the same cause.
- Corrected clean ranges (supersede the first version): centre +$34,879 / 182 trades; stop slippage 0..3.5 pt $34,795 to $35,060; market exit 0.5..1.2 pt $36,279 to $33,011; cut extra cost +2 pt $25,820 and +3.5 pt $18,736 (monotone now: the dominant factor, swing $16,142); L2 off in the first 8 h of Sunday $35,452; favourable corner $36,460; unfavourable corner $16,785. Entry delay not run. Sealed prediction unaffected.
