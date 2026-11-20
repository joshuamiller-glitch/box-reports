# D8_FEED_CHECK: tape statistics for trading date 2026-11-10 (Asia and NY AM), to compare with an NT8 (CQG) tick export (W-D8SPEC, order 1424Z item 1)

Source: engine trade tape (exchange MBO trade records, action T, front-month NQ, `/mnt/l2/l2vast/_bars/trades/`). Trading date 2026-11-10: Asia = 18:00 ET Nov 9 to 02:00 ET Nov 10 (23:00 UTC Nov 9 to 07:00 UTC Nov 10, EST); NY AM = 09:30 to 12:00 ET (14:30 to 17:00 UTC) Nov 10. Aggressor side: +1 buy aggressor (Buy volume), -1 sell aggressor, 0 none (3 records on the whole UTC day).

**Definitions.** Record = one tape row (one fill of one resting order). DISTINCT timestamps = number of different ts values (ns). Order group = records merged when ts and side are equal (what a per-aggressor-order feed shows); 'order groups (ts,side,price)' additionally requires equal price (a sweep across price levels stays several groups). Timestamps are exchange event times in ns; an NT8/CQG export will have its own (coarser) timestamps, so for comparison use totals and the 15-minute tables; to compare counts, merge your export's rows with identical timestamp and side.

Bucket labels are UTC start of the 15-minute bucket (ET = UTC - 5 h).


## Asia, trading date 2026-11-10

| item                                | value                         |
|:------------------------------------|:------------------------------|
| trade records                       | 51093                         |
| total volume (contracts)            | 64484                         |
| buy-aggressor volume                | 32185                         |
| sell-aggressor volume               | 32296                         |
| no-side volume                      | 3                             |
| DISTINCT timestamps                 | 41142                         |
| order groups (ts,side)              | 41243                         |
| order groups (ts,side,price)        | 50354                         |
| first record UTC                    | 2026-11-09T23:00:00.000000000 |
| last record UTC                     | 2026-11-10T06:59:54.116239701 |
| records per distinct ts             | 1.242                         |
| mean size per record                | 1.262                         |
| mean size per order group (ts,side) | 1.564                         |

### Asia: 15-minute buckets (UTC)

| bucket_start_utc   |   records |   volume |   buy_volume |   sell_volume |   delta |   distinct_ts |
|:-------------------|----------:|---------:|-------------:|--------------:|--------:|--------------:|
| 23:00              |      1129 |     1457 |          732 |           722 |      10 |           903 |
| 23:15              |      1041 |     1296 |          622 |           674 |     -52 |           839 |
| 23:30              |      1427 |     1831 |          944 |           887 |      57 |          1097 |
| 23:45              |       956 |     1149 |          722 |           427 |     295 |           783 |
| 00:00              |      2011 |     2632 |         1331 |          1301 |      30 |          1574 |
| 00:15              |      1509 |     1987 |         1030 |           957 |      73 |          1199 |
| 00:30              |      1778 |     2216 |         1073 |          1143 |     -70 |          1371 |
| 00:45              |      2422 |     2951 |         1347 |          1604 |    -257 |          1948 |
| 01:00              |      4646 |     5951 |         2926 |          3025 |     -99 |          3485 |
| 01:15              |      2568 |     3262 |         1623 |          1639 |     -16 |          1931 |
| 01:30              |      2234 |     3349 |         1965 |          1384 |     581 |          1654 |
| 01:45              |      1066 |     1263 |          610 |           653 |     -43 |           890 |
| 02:00              |      1479 |     1962 |         1003 |           959 |      44 |          1137 |
| 02:15              |      1234 |     1607 |          766 |           841 |     -75 |           921 |
| 02:30              |      1368 |     1635 |          782 |           853 |     -71 |          1120 |
| 02:45              |      1208 |     1538 |          754 |           784 |     -30 |           967 |
| 03:00              |      1201 |     1516 |          684 |           832 |    -148 |           955 |
| 03:15              |      1166 |     1396 |          685 |           711 |     -26 |           978 |
| 03:30              |      2641 |     3387 |         1355 |          2032 |    -677 |          2123 |
| 03:45              |      2383 |     2951 |         1548 |          1403 |     145 |          2037 |
| 04:00              |      1608 |     1995 |          979 |          1016 |     -37 |          1416 |
| 04:15              |      2050 |     2561 |         1381 |          1180 |     201 |          1643 |
| 04:30              |       930 |     1150 |          564 |           586 |     -22 |           755 |
| 04:45              |       832 |     1043 |          550 |           493 |      57 |           677 |
| 05:00              |      1329 |     1647 |          814 |           833 |     -19 |          1065 |
| 05:15              |      1003 |     1218 |          637 |           581 |      56 |           849 |
| 05:30              |      1779 |     2267 |         1242 |          1025 |     217 |          1492 |
| 05:45              |      1121 |     1351 |          655 |           696 |     -41 |           958 |
| 06:00              |      1276 |     1559 |          660 |           899 |    -239 |          1097 |
| 06:15              |      1441 |     1711 |          846 |           865 |     -19 |          1283 |
| 06:30              |      1202 |     1382 |          696 |           686 |      10 |          1050 |
| 06:45              |      1055 |     1264 |          659 |           605 |      54 |           945 |

## NY AM, trading date 2026-11-10

| item                                | value                         |
|:------------------------------------|:------------------------------|
| trade records                       | 234912                        |
| total volume (contracts)            | 292676                        |
| buy-aggressor volume                | 144634                        |
| sell-aggressor volume               | 148042                        |
| no-side volume                      | 0                             |
| DISTINCT timestamps                 | 203788                        |
| order groups (ts,side)              | 204087                        |
| order groups (ts,side,price)        | 232358                        |
| first record UTC                    | 2026-11-10T14:30:00.000021317 |
| last record UTC                     | 2026-11-10T16:59:59.904831323 |
| records per distinct ts             | 1.153                         |
| mean size per record                | 1.246                         |
| mean size per order group (ts,side) | 1.434                         |

### NY AM: 15-minute buckets (UTC)

| bucket_start_utc   |   records |   volume |   buy_volume |   sell_volume |   delta |   distinct_ts |
|:-------------------|----------:|---------:|-------------:|--------------:|--------:|--------------:|
| 14:30              |     43202 |    52811 |        26090 |         26721 |    -631 |         37287 |
| 14:45              |     34811 |    43356 |        21636 |         21720 |     -84 |         30428 |
| 15:00              |     32077 |    40047 |        20091 |         19956 |     135 |         27825 |
| 15:15              |     23839 |    29449 |        14553 |         14896 |    -343 |         20787 |
| 15:30              |     20536 |    25823 |        12296 |         13527 |   -1231 |         17820 |
| 15:45              |     22861 |    29134 |        14578 |         14556 |      22 |         19419 |
| 16:00              |     16783 |    21456 |        10521 |         10935 |    -414 |         14419 |
| 16:15              |     15548 |    19306 |         9342 |          9964 |    -622 |         13542 |
| 16:30              |     12948 |    16065 |         7965 |          8100 |    -135 |         11353 |
| 16:45              |     12307 |    15229 |         7562 |          7667 |    -105 |         10908 |

## 3. Sensitivity of the stack bars and triggers to print grouping (order item 2)

**Method.** From the same tape, records were merged and the bar kernels re-run with the engine's own thresholds (`D8_BAR_DEFS.md`). Two merges, because the relay's rule (same timestamp and same side) can join fills at different prices of one sweep: **A** = same ts + same side, merged record keeps the LAST fill price (so intermediate sweep prices vanish); **B** = same ts + same side + same price (pure size aggregation, no price information lost). Which of A or B resembles a CQG tick stream is unknown until Josh's export is compared. Merged bars were built for all six sessions of trading dates 2026-11-05 to 11-11; the trigger was run on the same series built from the engine's stored bars (unmerged) and from the merged bars, with the same warm-up prefix (first 2000 stored bars for the native variants, as the engine uses). The unmerged run reproduces the earlier engine raw-signal counts exactly (42 / 188 / 14 / 7), so the comparison is like for like. Signal comparison on the 3 sample days in the book's own session (Asia for Ldcdb0b6e and Lfb608c7b, NY AM for the other two): same = identical time (ns) and side; moved = same side within 120 s; missing = in unmerged only; extra = in merged only.

### Bars per session and close times (merged versus engine)

"closes_same_time" = engine bar closes that also exist at the identical timestamp on the merged bars; "max nearest diff" = largest distance (s) from an engine close to the nearest merged close.

| book | bar | merge | td | bars_unmerged | bars_merged | closes_same_time | max_nearest_diff_s |
|---|---|---|---|---|---|---|---|
| Ldcdb0b6e | cdr_100 | A: same ts+side (last price) | 20261109 | 135 | 135 | 129 | 51.531 |
| Ldcdb0b6e | cdr_100 | A: same ts+side (last price) | 20261110 | 80 | 78 | 74 | 57.774 |
| Ldcdb0b6e | cdr_100 | A: same ts+side (last price) | 20261111 | 114 | 113 | 108 | 4.205 |
| Ldcdb0b6e | cdr_100 | B: same ts+side+price | 20261109 | 135 | 135 | 134 | 0.003 |
| Ldcdb0b6e | cdr_100 | B: same ts+side+price | 20261110 | 80 | 80 | 80 | 0.0 |
| Ldcdb0b6e | cdr_100 | B: same ts+side+price | 20261111 | 114 | 114 | 113 | 0.277 |
| Lfb608c7b | vsess_600 | A: same ts+side (last price) | 20261109 | 840 | 832 | 70 | 52.632 |
| Lfb608c7b | vsess_600 | A: same ts+side (last price) | 20261110 | 448 | 442 | 16 | 90.828 |
| Lfb608c7b | vsess_600 | A: same ts+side (last price) | 20261111 | 527 | 521 | 46 | 74.331 |
| Lfb608c7b | vsess_600 | B: same ts+side+price | 20261109 | 840 | 840 | 703 | 9.638 |
| Lfb608c7b | vsess_600 | B: same ts+side+price | 20261110 | 448 | 448 | 417 | 21.883 |
| Lfb608c7b | vsess_600 | B: same ts+side+price | 20261111 | 527 | 527 | 257 | 41.371 |
| L7cc56d99 | lbrk_3_40 | A: same ts+side (last price) | 20261109 | 31 | 31 | 23 | 71.988 |
| L7cc56d99 | lbrk_3_40 | A: same ts+side (last price) | 20261110 | 33 | 33 | 12 | 8.785 |
| L7cc56d99 | lbrk_3_40 | A: same ts+side (last price) | 20261111 | 21 | 21 | 9 | 88.09 |
| L7cc56d99 | lbrk_3_40 | B: same ts+side+price | 20261109 | 31 | 31 | 31 | 0.0 |
| L7cc56d99 | lbrk_3_40 | B: same ts+side+price | 20261110 | 33 | 33 | 33 | 0.0 |
| L7cc56d99 | lbrk_3_40 | B: same ts+side+price | 20261111 | 21 | 21 | 21 | 0.0 |
| L488784d8 | swing_atr_0.25 | A: same ts+side (last price) | 20261109 | 308 | 308 | 306 | 1.213 |
| L488784d8 | swing_atr_0.25 | A: same ts+side (last price) | 20261110 | 448 | 448 | 448 | 0.0 |
| L488784d8 | swing_atr_0.25 | A: same ts+side (last price) | 20261111 | 236 | 236 | 236 | 0.0 |
| L488784d8 | swing_atr_0.25 | B: same ts+side+price | 20261109 | 308 | 308 | 308 | 0.0 |
| L488784d8 | swing_atr_0.25 | B: same ts+side+price | 20261110 | 448 | 448 | 448 | 0.0 |
| L488784d8 | swing_atr_0.25 | B: same ts+side+price | 20261111 | 236 | 236 | 236 | 0.0 |

### Trigger signals (merged versus unmerged)

| book | bar | trigger | merge | n_unmerged | n_merged | same | moved | max_moved_s | missing | extra |
|---|---|---|---|---|---|---|---|---|---|---|
| Ldcdb0b6e | cdr_100 | trig_momentum_mvote/v3of5 | A: same ts+side (last price) | 42 | 43 | 35 | 1 | 7.35 | 6 | 7 |
| Ldcdb0b6e | cdr_100 | trig_momentum_mvote/v3of5 | B: same ts+side+price | 42 | 42 | 42 | 0 | 0.0 | 0 | 0 |
| Lfb608c7b | vsess_600 | trig_pullback_ema/depth_native | A: same ts+side (last price) | 188 | 183 | 16 | 137 | 119.97 | 35 | 30 |
| Lfb608c7b | vsess_600 | trig_pullback_ema/depth_native | B: same ts+side+price | 188 | 190 | 143 | 43 | 103.15 | 2 | 4 |
| L7cc56d99 | lbrk_3_40 | trig_levels_vwap/break | A: same ts+side (last price) | 14 | 14 | 5 | 9 | 0.21 | 0 | 0 |
| L7cc56d99 | lbrk_3_40 | trig_levels_vwap/break | B: same ts+side+price | 14 | 14 | 14 | 0 | 0.0 | 0 | 0 |
| L488784d8 | swing_atr_0.25 | trig_momentum_roc/break_native | A: same ts+side (last price) | 7 | 7 | 7 | 0 | 0.0 | 0 | 0 |
| L488784d8 | swing_atr_0.25 | trig_momentum_roc/break_native | B: same ts+side+price | 7 | 7 | 7 | 0 | 0.0 | 0 | 0 |

**Reading.**
- Under merge B (no price information lost) cdr_100 (Ldcdb0b6e), lbrk_3_40 (L7cc56d99) and swing_atr_0.25 (L488784d8) are essentially unchanged: bar closes identical to within 0.3 s and every signal identical. Under merge A the cdr and line-break bars move (a sweep's intermediate prices are lost), cdr_100 gives 6 missing / 7 extra signals of 42 and lbrk 9 of 14 signals move (at most 0.2 s); swing bars are unaffected.
- **vsess_600 (Lfb608c7b) is sensitive in both merges**: the volume clock closes on the first record that takes the cumulative volume to the threshold, and the closing record keeps its overshoot, so a different record grouping shifts every later boundary of the session (cascade). Only 703 / 417 / 257 of 840 / 448 / 527 engine closes remain at the same instant under merge B, and nearest close differences reach 41 s; its signals under B: 143 same, 43 moved (up to 103 s), 2 missing, 4 extra of 188; under A: 16 same, 137 moved, 35 missing, 30 extra. This is the same mechanism as NT8's native Volume bar splitting the closing print. The same applies to every volume, tick and session-volume book in the pool (vol_*, tick_500, vsess_*, dib/vrb/drb), which I did not run.
- Caveat: signals are raw signals on closed bars (not the traded results), 3 days only.

### PROPOSAL (not queued; waiting for the lead's go)
Do not run until the CQG comparison (section 1) shows what the feed looks like: if CQG ticks equal merge B (or the engine's records), only the volume-clock family needs a re-run; if they equal A, cdr and line-break books need one too.
Proposed re-run on merged bars, last 6 months (2026-05..2026-10) only, new set names `TL3_ALN_AS_<id>_MGB` / `_MGA` (B / A merge), the pool books whose bar is count/volume-clock or state-based: Asia vsess (Lbe5ac95b, L29b1bc3f, La6f6f7ad, L40bde9ea, Lfb608c7b), vol (L11152f7a, Lda55d973, Lcae177ba), tick (Lc4584864), dib (M3f6f752c), vrb (L86781ac0), drb (Le9bd7276), dlt (Lc849eb8c), cdr (Ldcdb0b6e, L7ea48296) = 15 books x 6 months = **90 set-months** per merge variant; NY AM: dib L2176f633, vol B2010fec9, lbrk L7cc56d99, = 3 books x 6 = 18 set-months. For the whole 37-book pool: 222 set-months per variant. The bars themselves would be rebuilt with a merge flag in the (unchanged) kernels into a separate store directory; cost is the bar rebuild of 6 months (about the time of the existing W-BAR monthly build, a few CPU-hours) plus the engine set-months above. Before any run I would also check the 6-month signal drift with the raw-signal comparison used here (cheap).

## 4. L578701ed (book_dwm dev_follow, time_m_1, Asia stack): depth inputs (order item 4)

**Inputs (code: `th_grid/triggers_c/defs.py` book_dwm, `featc.py` grid_feats / day_features).**
- Data: top 10 price levels on each side: bid prices and sizes (contracts at the level), ask prices and sizes. **Nothing else**: no order counts per level, no per-order queue, no message counts. (`g_bpx, g_bsz, g_apx, g_asz` arrays, 10 columns each.) Source for the engine: the MBO-derived mbp-10 history, final snapshot on a 100 ms grid (`g_ts_recv`, receive time), including Asia.
- Per grid record: valid if best bid > 0, best ask > best bid, best bid size > 0 and best ask size > 0 (uncrossed, both sides non-empty). bw = sum_k(bid_px_k x bid_sz_k) / sum_k bid_sz_k over the 10 bid levels; aw = same over the 10 ask levels; DWM = (bw + aw)/2; mid = (best bid + best ask)/2; deviation x = DWM - mid in ticks (sign: positive when depth centre of mass sits above the mid).
- Timing: for each 1-minute bar (time_m_1, known at the clock minute boundary) the value used is the last VALID grid record with receive time <= the bar's known time, i.e. the book as of at most 100 ms before the minute boundary (the engine requires stored known_ts == bar close, else the feature is NaN and no signal). Nothing after the bar close is used (a no-look-ahead test with a shifted book clock exists in the code).
- Signal: z-score of x over the last 200 one-minute bars (rolling sample std ddof 1, at least 66 bars), long when x/sd >= 2.0, short when <= -2.0; edge-triggered; follow direction. 200 minutes of history (about 3.3 h): at the Asia open the series continues from the previous sessions' bars (continuous series, `D8_TRIGGER_DEFS.md` 3.12).

**Does a feed with 10 price levels but no per-order data lose anything for this book?** By the code, **no**: the feature uses only level prices and aggregate level sizes, which a 10-level price-aggregated depth feed (CQG via NT8 OnMarketDepth) provides. What can differ, and should be checked on a recorded day rather than assumed:
1. Level size definition: CQG sizes should equal the exchange's aggregate quantity per price, but implied (spread-derived) quantities, if CQG includes or excludes them, change sizes at some levels.
2. Update timing and sampling: the engine snapshot is a 100 ms grid on receive time; NT8 depth events arrive in order and can be sampled exactly at the bar boundary (slightly fresher than the engine's, by up to 100 ms). Because the signal is a 200-bar z-score of a smooth centre-of-mass reading, a 100 ms difference should move x a little, not flip many signals; the sensitivity was not measured.
3. Level count: all 10 levels must really be delivered (a feed with fewer levels changes bw/aw directly; DWM weights deep levels by size).
4. Validity: crossed or empty-side records must be skipped as the engine does (use the last valid snapshot).
5. Not measured here: the effect of replacing the 100 ms grid by event-time sampling, and of any CQG depth gaps. The per-order data the engine's Level-3 history has (add/cancel counts) are used by OTHER book triggers (book_cancel, book_queue, ofi), not by dwm.
Bar side: time_m_1 needs only trades. So L578701ed needs L2 (OnMarketDepth, 10 levels) plus the trade stream for the bar clock.

## 5. NT8/CQG export versus our tape, Asia td 20261110 (orders 1432Z A and 1438Z B; NT8 numbers are the relay's counts from Josh's file, which is not on this box)

**Plainly: volume matches exactly in every one of the 32 fifteen-minute buckets (64,484 both). Aggressor side matches exactly in every bucket when our side is taken the NT8 way (last >= ask buy, last <= bid sell, using the book quote at the print): buy 32,187 / sell 32,297 = NT8's 32,187 / 32,297. Our tape's own aggressor flag differs from that by 2 contracts on the buy side and 1 on the sell side (32,185 / 32,296). Records differ: NT8 59,887 versus our 51,093 (NT8 splits finer; ratio 1.172).**

Per-print side agreement on our tape (flag versus quote-rule side, using the book state stored with each trade record; the stored records align one to one with the tape trade rows): 2 of 51,093 records disagree (4 contracts of 64,484); one record has flag 0; no record falls strictly between bid and ask. Other sample days: 11-09 side agreement by volume 99.82% (a 1,000-contract-scale difference concentrated in a few records, delta 1,543 by quote versus 1,348 by flag), 11-11 99.99%.

| td | records | side_agree_volume | quote_buy_vol | quote_sell_vol | flag_buy_vol | flag_sell_vol | quote_delta | flag_delta |
|---|---|---|---|---|---|---|---|---|
| 20261109 | 89439 | 0.9982 | 55597 | 54054 | 55402 | 54054 | 1543 | 1348 |
| 20261110 | 51093 | 0.9999 | 32187 | 32297 | 32185 | 32296 | -110 | -111 |
| 20261111 | 58727 | 0.9999 | 38996 | 36839 | 38991 | 36839 | 2157 | 2152 |

### 5.1 Fifteen-minute table side by side (UTC, td 20261110 Asia)
nt = NT8/CQG export, our = our tape. d_ = NT8 minus ours with our QUOTE-rule side. Records ratio = NT8/our.

| lab | nt_rec | our_rec | rec_ratio_nt_over_our | nt_vol | our_vol | d_vol | nt_buy | our_buy_flag | our_buy_quote | d_buy_vs_quote | nt_sell | our_sell_flag | our_sell_quote | d_sell_vs_quote | our_canonical_prints |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 09 23:00 | 1260 | 1129 | 1.116 | 1457 | 1457 | 0 | 735 | 732 | 735 | 0 | 722 | 722 | 722 | 0 | 1072 |
| 09 23:15 | 1207 | 1041 | 1.159 | 1296 | 1296 | 0 | 622 | 622 | 622 | 0 | 674 | 674 | 674 | 0 | 994 |
| 09 23:30 | 1713 | 1427 | 1.2 | 1831 | 1831 | 0 | 944 | 944 | 944 | 0 | 887 | 887 | 887 | 0 | 1338 |
| 09 23:45 | 1105 | 956 | 1.156 | 1149 | 1149 | 0 | 722 | 722 | 722 | 0 | 427 | 427 | 427 | 0 | 889 |
| 10 00:00 | 2416 | 2011 | 1.201 | 2632 | 2632 | 0 | 1331 | 1331 | 1331 | 0 | 1301 | 1301 | 1301 | 0 | 1885 |
| 10 00:15 | 1788 | 1509 | 1.185 | 1987 | 1987 | 0 | 1030 | 1030 | 1030 | 0 | 957 | 957 | 957 | 0 | 1371 |
| 10 00:30 | 2059 | 1778 | 1.158 | 2216 | 2216 | 0 | 1073 | 1073 | 1073 | 0 | 1143 | 1143 | 1143 | 0 | 1642 |
| 10 00:45 | 2778 | 2422 | 1.147 | 2951 | 2951 | 0 | 1347 | 1347 | 1347 | 0 | 1604 | 1604 | 1604 | 0 | 2237 |
| 10 01:00 | 5559 | 4646 | 1.197 | 5951 | 5951 | 0 | 2926 | 2926 | 2926 | 0 | 3025 | 3025 | 3025 | 0 | 4405 |
| 10 01:15 | 3105 | 2568 | 1.209 | 3262 | 3262 | 0 | 1623 | 1623 | 1623 | 0 | 1639 | 1639 | 1639 | 0 | 2446 |
| 10 01:30 | 2717 | 2234 | 1.216 | 3349 | 3349 | 0 | 1965 | 1965 | 1965 | 0 | 1384 | 1384 | 1384 | 0 | 2094 |
| 10 01:45 | 1202 | 1066 | 1.128 | 1263 | 1263 | 0 | 610 | 610 | 610 | 0 | 653 | 653 | 653 | 0 | 1015 |
| 10 02:00 | 1789 | 1479 | 1.21 | 1962 | 1962 | 0 | 1003 | 1003 | 1003 | 0 | 959 | 959 | 959 | 0 | 1384 |
| 10 02:15 | 1497 | 1234 | 1.213 | 1607 | 1607 | 0 | 766 | 766 | 766 | 0 | 841 | 841 | 841 | 0 | 1152 |
| 10 02:30 | 1570 | 1368 | 1.148 | 1635 | 1635 | 0 | 782 | 782 | 782 | 0 | 853 | 853 | 853 | 0 | 1301 |
| 10 02:45 | 1459 | 1208 | 1.208 | 1538 | 1538 | 0 | 754 | 754 | 754 | 0 | 784 | 784 | 784 | 0 | 1155 |
| 10 03:00 | 1419 | 1201 | 1.182 | 1516 | 1516 | 0 | 684 | 684 | 684 | 0 | 832 | 832 | 832 | 0 | 1133 |
| 10 03:15 | 1315 | 1166 | 1.128 | 1396 | 1396 | 0 | 685 | 685 | 685 | 0 | 711 | 711 | 711 | 0 | 1087 |
| 10 03:30 | 3129 | 2641 | 1.185 | 3387 | 3387 | 0 | 1355 | 1355 | 1355 | 0 | 2032 | 2032 | 2032 | 0 | 2469 |
| 10 03:45 | 2768 | 2383 | 1.162 | 2951 | 2951 | 0 | 1547 | 1548 | 1547 | 0 | 1404 | 1403 | 1404 | 0 | 2158 |
| 10 04:00 | 1836 | 1608 | 1.142 | 1995 | 1995 | 0 | 979 | 979 | 979 | 0 | 1016 | 1016 | 1016 | 0 | 1488 |
| 10 04:15 | 2416 | 2050 | 1.179 | 2561 | 2561 | 0 | 1381 | 1381 | 1381 | 0 | 1180 | 1180 | 1180 | 0 | 1921 |
| 10 04:30 | 1096 | 930 | 1.178 | 1150 | 1150 | 0 | 564 | 564 | 564 | 0 | 586 | 586 | 586 | 0 | 886 |
| 10 04:45 | 959 | 832 | 1.153 | 1043 | 1043 | 0 | 550 | 550 | 550 | 0 | 493 | 493 | 493 | 0 | 789 |
| 10 05:00 | 1547 | 1329 | 1.164 | 1647 | 1647 | 0 | 814 | 814 | 814 | 0 | 833 | 833 | 833 | 0 | 1255 |
| 10 05:15 | 1137 | 1003 | 1.134 | 1218 | 1218 | 0 | 637 | 637 | 637 | 0 | 581 | 581 | 581 | 0 | 951 |
| 10 05:30 | 2136 | 1779 | 1.201 | 2267 | 2267 | 0 | 1242 | 1242 | 1242 | 0 | 1025 | 1025 | 1025 | 0 | 1678 |
| 10 05:45 | 1292 | 1121 | 1.153 | 1351 | 1351 | 0 | 655 | 655 | 655 | 0 | 696 | 696 | 696 | 0 | 1074 |
| 10 06:00 | 1484 | 1276 | 1.163 | 1559 | 1559 | 0 | 660 | 660 | 660 | 0 | 899 | 899 | 899 | 0 | 1211 |
| 10 06:15 | 1623 | 1441 | 1.126 | 1711 | 1711 | 0 | 846 | 846 | 846 | 0 | 865 | 865 | 865 | 0 | 1405 |
| 10 06:30 | 1336 | 1202 | 1.111 | 1382 | 1382 | 0 | 696 | 696 | 696 | 0 | 686 | 686 | 686 | 0 | 1151 |
| 10 06:45 | 1170 | 1055 | 1.109 | 1264 | 1264 | 0 | 659 | 659 | 659 | 0 | 605 | 605 | 605 | 0 | 988 |

Totals: NT8 records 59,887 vs ours 51,093; volume 64,484 both; NT8 buy/sell 32,187/32,297 vs ours by quote 32,187/32,297, by flag 32,185/32,296.

### 5.2 s_vol exact definition (order 1432Z item 3)
`s_vol` is NOT the average print size. It is the scale `s_vol = tr_vol / r0_vol`, where `tr_vol` = median of the daily total traded volume (all sessions of the Globex trading date, contracts) over the previous 20 trading-date rows of the stats table (rows strictly before the day) and `r0_vol = 610,702` (median daily volume of the first 60 rows, 2023-04-03 to 2023-06-23). For td 20261110: tr_vol = 678,505.5, s_vol = 1.11103, so cdr_100 threshold = 100 x 1.11103 = 111.10 contracts (Asia, same value for all sessions of that day; also 110.0 on 11-09 and 110.6 on 11-11). The similarity of NT8 volume/records = 1.077 to 1.11 is a coincidence. These scales depend on volume only, so they do not change with print splitting (the print-count scale s_n, used by tick, dib, vrb, drb, would).

### 5.3 Canonical-print count (order 1438Z item 1)
Rule tested: consecutive records, same millisecond (timestamp truncated), same aggressor side, same price merged. Our tape, Asia td 20261110: **48,024 canonical prints** (NT8: 47,600; difference +424, +0.9%). Other keys on our tape: consecutive ms+side groups 35,985 (NT8 34,458), distinct milliseconds 35,015 (NT8 33,019), distinct (ms, side, price) keys 47,915 (NT8 47,373), merge on ms+price only 47,799, ms only 35,015. So volume, side and the price/side structure agree but **the NT8 file has about 6% fewer distinct millisecond stamps than ours** (33,019 vs 35,015). Therefore CQG timestamps are coarser or jittered relative to the exchange event times in our tape (CQG stamps at its own clock). Scanning time-bin widths on our tape: a 1 ms floor gives (35,015 / 35,985 / 48,024); a 2.5 ms bin 33,174 / 34,523 / 47,646; a 3 ms bin 32,929 / 34,324 / 47,610 (targets 33,019 / 34,458 / 47,600). A 3 ms bin is close but not a rule (bin phase unknown, no per-print alignment possible without the file). **Conclusion: the canonical count is reproducible to about 1% but not exactly from our tape; an exact match needs the export file itself (print by print alignment of CQG stamps with the tape).** If Josh copies it to this box (any path under /mnt/l2/l2vast/, read only) I will align the prints and find the rule. Fallback until then: the volume and side are identical, so bars whose boundaries depend only on cumulative volume/delta at coarse thresholds (cdr, lbrk, swing) are stable (section 6), but the volume-clock bar (vsess_600) is not.

## 6. Fidelity test on our tape (order 1432Z item 2), Asia sample days
Variants: (a) timestamps truncated to ms, tape order kept; (b) a + side from last-vs-bid/ask (our quotes); (c) canonical merge (ms+side(flag)+price); (d) canonical with quote side. Baseline = engine bars/signals as before. Signals are the raw signals on the book's own session of the 3 sample days. "identical" would need equal ns time, which truncation precludes, so "within 2 ms" is the same signal.

### Bar closes
| variant | bar | td | bars_engine | bars_variant | closes_identical | closes_within_2ms | closes_moved_over_2ms | max_nearest_diff_s |
|---|---|---|---|---|---|---|---|---|
| (a) ms-truncated timestamps, tape order | cdr_100 | 20261109 | 135 | 135 | 0 | 135 | 0 | 0.001 |
| (a) ms-truncated timestamps, tape order | cdr_100 | 20261110 | 80 | 80 | 0 | 80 | 0 | 0.001 |
| (a) ms-truncated timestamps, tape order | cdr_100 | 20261111 | 114 | 114 | 0 | 114 | 0 | 0.001 |
| (a) ms-truncated timestamps, tape order | vsess_600 | 20261109 | 840 | 840 | 1 | 840 | 0 | 0.001 |
| (a) ms-truncated timestamps, tape order | vsess_600 | 20261110 | 448 | 448 | 0 | 448 | 0 | 0.001 |
| (a) ms-truncated timestamps, tape order | vsess_600 | 20261111 | 527 | 527 | 0 | 527 | 0 | 0.001 |
| (a) ms-truncated timestamps, tape order | time_m_1 | 20261109 | 480 | 480 | 479 | 480 | 0 | 0.001 |
| (a) ms-truncated timestamps, tape order | time_m_1 | 20261110 | 480 | 480 | 479 | 480 | 0 | 0.0 |
| (a) ms-truncated timestamps, tape order | time_m_1 | 20261111 | 480 | 480 | 479 | 480 | 0 | 0.001 |
| (b) a + side from last-vs-bid/ask (our quotes) | cdr_100 | 20261109 | 135 | 136 | 0 | 135 | 0 | 0.001 |
| (b) a + side from last-vs-bid/ask (our quotes) | cdr_100 | 20261110 | 80 | 80 | 0 | 80 | 0 | 0.001 |
| (b) a + side from last-vs-bid/ask (our quotes) | cdr_100 | 20261111 | 114 | 114 | 0 | 114 | 0 | 0.001 |
| (b) a + side from last-vs-bid/ask (our quotes) | vsess_600 | 20261109 | 840 | 840 | 1 | 840 | 0 | 0.001 |
| (b) a + side from last-vs-bid/ask (our quotes) | vsess_600 | 20261110 | 448 | 448 | 0 | 448 | 0 | 0.001 |
| (b) a + side from last-vs-bid/ask (our quotes) | vsess_600 | 20261111 | 527 | 527 | 0 | 527 | 0 | 0.001 |
| (b) a + side from last-vs-bid/ask (our quotes) | time_m_1 | 20261109 | 480 | 480 | 479 | 480 | 0 | 0.001 |
| (b) a + side from last-vs-bid/ask (our quotes) | time_m_1 | 20261110 | 480 | 480 | 479 | 480 | 0 | 0.0 |
| (b) a + side from last-vs-bid/ask (our quotes) | time_m_1 | 20261111 | 480 | 480 | 479 | 480 | 0 | 0.001 |
| (c) canonical: ms+side(flag)+price consecutive merge | cdr_100 | 20261109 | 135 | 135 | 0 | 135 | 0 | 0.002 |
| (c) canonical: ms+side(flag)+price consecutive merge | cdr_100 | 20261110 | 80 | 80 | 0 | 80 | 0 | 0.001 |
| (c) canonical: ms+side(flag)+price consecutive merge | cdr_100 | 20261111 | 114 | 114 | 0 | 112 | 2 | 0.277 |
| (c) canonical: ms+side(flag)+price consecutive merge | vsess_600 | 20261109 | 840 | 840 | 1 | 211 | 629 | 50.43 |
| (c) canonical: ms+side(flag)+price consecutive merge | vsess_600 | 20261110 | 448 | 448 | 0 | 165 | 283 | 55.637 |
| (c) canonical: ms+side(flag)+price consecutive merge | vsess_600 | 20261111 | 527 | 527 | 0 | 98 | 429 | 105.672 |
| (c) canonical: ms+side(flag)+price consecutive merge | time_m_1 | 20261109 | 480 | 480 | 479 | 480 | 0 | 0.001 |
| (c) canonical: ms+side(flag)+price consecutive merge | time_m_1 | 20261110 | 480 | 480 | 479 | 480 | 0 | 0.0 |
| (c) canonical: ms+side(flag)+price consecutive merge | time_m_1 | 20261111 | 480 | 480 | 479 | 480 | 0 | 0.001 |
| (d) canonical with quote side | cdr_100 | 20261109 | 135 | 136 | 0 | 135 | 0 | 0.002 |
| (d) canonical with quote side | cdr_100 | 20261110 | 80 | 80 | 0 | 80 | 0 | 0.001 |
| (d) canonical with quote side | cdr_100 | 20261111 | 114 | 114 | 0 | 112 | 2 | 0.277 |
| (d) canonical with quote side | vsess_600 | 20261109 | 840 | 840 | 1 | 211 | 629 | 50.43 |
| (d) canonical with quote side | vsess_600 | 20261110 | 448 | 448 | 0 | 165 | 283 | 55.637 |
| (d) canonical with quote side | vsess_600 | 20261111 | 527 | 527 | 0 | 98 | 429 | 105.672 |
| (d) canonical with quote side | time_m_1 | 20261109 | 480 | 480 | 479 | 480 | 0 | 0.001 |
| (d) canonical with quote side | time_m_1 | 20261110 | 480 | 480 | 479 | 480 | 0 | 0.0 |
| (d) canonical with quote side | time_m_1 | 20261111 | 480 | 480 | 479 | 480 | 0 | 0.001 |

### Triggers
| n_engine | n_variant | identical | same_within_2ms | moved | max_moved_s | missing | extra | variant | book | bar | trigger |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 42 | 42 | 0 | 42 | 0 | 0.0 | 0 | 0 | (a) ms-truncated timestamps, tape order | Ldcdb0b6e | cdr_100 | trig_momentum_mvote/v3of5 |
| 188 | 188 | 0 | 188 | 0 | 0.0 | 0 | 0 | (a) ms-truncated timestamps, tape order | Lfb608c7b | vsess_600 | trig_pullback_ema/depth_native |
| 42 | 42 | 0 | 38 | 1 | 2.4 | 3 | 3 | (b) a + side from last-vs-bid/ask (our quotes) | Ldcdb0b6e | cdr_100 | trig_momentum_mvote/v3of5 |
| 188 | 188 | 0 | 188 | 0 | 0.0 | 0 | 0 | (b) a + side from last-vs-bid/ask (our quotes) | Lfb608c7b | vsess_600 | trig_pullback_ema/depth_native |
| 42 | 43 | 0 | 42 | 0 | 0.0 | 0 | 1 | (c) canonical: ms+side(flag)+price consecutive merge | Ldcdb0b6e | cdr_100 | trig_momentum_mvote/v3of5 |
| 188 | 198 | 0 | 51 | 116 | 116.06 | 21 | 31 | (c) canonical: ms+side(flag)+price consecutive merge | Lfb608c7b | vsess_600 | trig_pullback_ema/depth_native |
| 42 | 42 | 0 | 38 | 1 | 2.4 | 3 | 3 | (d) canonical with quote side | Ldcdb0b6e | cdr_100 | trig_momentum_mvote/v3of5 |
| 188 | 198 | 0 | 51 | 116 | 116.06 | 21 | 31 | (d) canonical with quote side | Lfb608c7b | vsess_600 | trig_pullback_ema/depth_native |

**Reading.** (a) Millisecond truncation changes nothing but the sub-millisecond timestamp (all closes within 1 ms, all 42 and 188 signals the same). (b) Quote-rule side: cdr_100 (side-dependent) closes within 1 ms except one extra bar on 11-09; Ldcdb0b6e signals: 38 same, 1 moved 2.4 s, 3 missing, 3 extra of 42 (a handful of delta-driven shifts); Lfb608c7b unaffected (volume bar). (c)/(d) Canonical merge: cdr_100 closes unchanged (2 bars on 11-11 move up to 0.28 s), Ldcdb0b6e: 1 extra signal; **vsess_600 closes change for most bars (e.g. 211 of 840 closes identical on 11-09, differences up to 106 s) and Lfb608c7b signals: 51 same, 116 moved, 21 missing, 31 extra of 188** (the overshoot cascade: the closing record is the merged print, bigger than the old per-order record). The time bar time_m_1 (L578701ed): 479 of 480 closes bit-identical in all variants (the 480th is the truncated last bar): it needs no rebuild; its trigger needs only the depth inputs (section 4).
