# DS3_ZONES_3_L2_TAPE_NEWCAP - tape zone streams on the NEW cap (to 2026-10-30), scored in the ZONES frames (ZL-2, s7)

**Base: D7 v1.2 (INTERIM; v1.3 re-run of the finalists follows).** Research only; post-hoc, Shadow only, no PASS claims. New windows only (L1M L2M VIEW, L3M L6M HOLD MID PRE X'; Feb-Oct = F9 = 2026-02-07..10-31). Old-cap results are on `DS3_ZONES_3_L2_TAPE.md` (OLD CAP). Prereg autopilot/ZL2_TAPE_prereg.md (streams) and ZL2_TAPE_SCORE_prereg.md (scoring; sha256 in DECISIONS.md). Code l2vast/ds3/code/zl2/, cells /mnt/l2/l2vast/ds3_zones3_new/ZL-2/ (cells/, cells_summary.csv, robust_f1.csv, plc_rank.csv, interim_tables.md), streams out/zl/streams_tape_new/.

## PAGE 1
**DATA.** NQ 1-s print tape from the DE-DUPLICATED months/ext weeks (`NQ_dropin_redo`) 2023-02..2026-10-30, 169,627,126 fp rows, path ds3_g2_redo; 16 roll days (13 old + 3 new: 2026-03-17, 06-16, 09-15) excluded from every stream by a tape/path coverage test. 126 streams (profile lines incl. the three missing ones, composites 5/20/60 d, developing nodes and voids, delta-at-price, cum-delta, large prints, measured pools). The pool level sources (swing/equal/session/killzone/prior-day H/L) were re-implemented on the extended path because the POI store has none of them after the old cap. Disclosure: the old-cap fp build already contained 2026-02 to 02-27 (the path array was longer than the cap); nothing scored used it.

**The base in these windows** (D7 v1.2, lock 12R, live lots): 

| window | base mean $/wk | maxDD | worst-20 | weeks |
|---|---|---|---|---|
| L1M | +18.4 | 30.2k |  | 5 |
| L3M | +13.5 | 39.6k |  | 13 |
| L6M | +26.0 | 127.8k | -61.8k | 27 |
| HOLD | +22.0 | 127.8k | -449.4k | 52 |
| MID | +11.3 | 92.1k |  | 12 |
| PRE | +13.2 | 113.8k | -479.6k | 75 |
| X' | -5.4 | 276.9k | -374.7k | 44 |
| F9 | +22.1 | 127.8k | -400.7k | 38 |

### Verdict in plain words
* **The Feb-Oct drawdown of the base is ONE episode** (maxDD 128k, carried by the weeks around 2026-09-14). Every tape-zone cell that cuts it by 20% or more is carried by that single episode: of the 8 finalists, 7 lose more than two thirds of their cut when the most influential single week is removed (ONE-WEEK label), and every month-block bootstrap 90% interval of the cut includes zero or a negative value in F9 and HOLD (table below). Nothing here is a lead on the robustness standard.
* The cells that cut most are VOLUME-heavy: developing LVN zones fire on 22-40% of the engine rows, TPF session/day lines on 17-29%; a same-volume random skip/half is in the placebo columns (ranks below; 1.00 = the real cell beats every draw). Where the rank is low the cut is a volume effect.
* **The three profile lines group 10 lacks** (TPF vah sw15, lvn1 sw1h, hvn0 sw1h as AHEAD D20/40 skip or half; BEHIND skip) do not cut the Feb-Oct maxDD in any usable way (see the NEW3 rows).
* Measured stop pools (new cap): the pool known at formation does not predict the move beyond the level; the pool printed in the break window does (mechanical). Swing/equal/session/killzone/prior-day H/L hold LESS often than random levels (run-through levels).

### Ranked tape-zone cells (AHEAD fresh within D, vs the base; maxDD change in %, mean change $k/wk with its MDE; S/T/N = STRICT / TOLERANT / NOW-ONLY gate; placebo ranks sv / rd / sd on F9 where run)
| cell | rows fired | F9 | L1M | L3M | L6M | HOLD | MID | PRE | X' | mean L6M (MDE) | mean HOLD (MDE) | mean PRE (MDE) | S/T/N | placebo rank sv/rd/sd (draws) | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A40 TVP_lvn skip | 39987 | -43% | -27% | -37% | -42% | -16% | -48% | +13% | -4% | +2.9 (+17.5) | +1.7 (+13.5) | -4.8 (+10.0) | --Y |  | placebo pending |
| A20 TVP_void skip | 3497 | -32% | +0% | -24% | -37% | -32% | -6% | +14% | -5% | +5.3 (+5.4) | +2.0 (+4.2) | -1.5 (+4.8) | -YY |  | ONE-WEEK, placebo pending |
| A40 TVP_lvn half | 39987 | -31% | -28% | -37% | -51% | -29% | -60% | -12% | -20% | +1.8 (+13.1) | +2.5 (+8.9) | -4.8 (+6.4) | --Y |  | ONE-WEEK, placebo pending |
| A40 TPF_sessday half | 25294 | -29% | -28% | +16% | -43% | -29% | -71% | -0% | -25% | +0.7 (+11.4) | -1.9 (+10.4) | -7.5 (+7.6) | --- |  | ONE-WEEK, placebo pending |
| A20 TLQ_swg15 half | 19762 | -28% | -13% | +2% | -28% | -28% | -39% | +10% | -13% | -1.6 (+10.1) | -1.4 (+6.1) | -6.2 (+5.7) | --- |  | ONE-WEEK, placebo pending |
| A40 TVP_hvn skip | 23410 | -27% | -14% | +78% | -27% | -27% | -17% | +19% | -39% | +0.9 (+10.6) | -0.3 (+8.6) | -5.8 (+10.1) | --- |  | ONE-WEEK, placebo pending |
| A40 TVP_void skip | 7284 | -26% | +0% | -24% | -26% | -26% | -48% | +59% | -37% | +7.8 (+9.6) | +6.7 (+8.5) | -3.2 (+5.9) | --Y |  | placebo pending |
| A20 TCD_ext half | 10122 | -25% | -7% | -29% | -25% | -25% | -41% | -21% | -22% | -2.5 (+9.7) | -2.3 (+6.6) | -2.2 (+3.0) | --- |  | placebo pending |
| B20 TPF_sw15 skip | 9157 | -22% | -1% | +5% | -22% | -22% | -37% | -1% | -39% | -0.1 (+5.5) | +0.7 (+5.7) | -4.2 (+7.8) | --- |  | placebo pending |
| B20 NEW3 skip | 3603 | -21% | +0% | +8% | -21% | -21% | -40% | -23% | +27% | +0.5 (+3.9) | +2.1 (+4.4) | -0.4 (+3.3) | --- |  | placebo pending |
| A40 TPF_sw15 half | 13744 | -20% | +2% | +8% | -20% | -20% | -35% | -30% | -5% | -0.8 (+4.6) | -0.8 (+4.5) | -3.9 (+5.8) | --- |  |  |
| A40 TPF_sessday skip | 25294 | -16% | -41% | +119% | -16% | -16% | -37% | +15% | -73% | -2.1 (+16.8) | +3.1 (+12.0) | -5.8 (+9.4) | --- |  |  |
| A20 TVP_lvn half | 26373 | -16% | -26% | -35% | -32% | -16% | -61% | -5% | -6% | -0.7 (+10.6) | -0.6 (+7.1) | -5.1 (+5.8) | --- |  | ONE-WEEK, placebo pending |
| A20 TPF_sessday half | 14967 | -16% | -27% | +3% | -16% | -16% | -53% | -1% | -28% | -4.6 (+11.5) | -2.6 (+7.5) | -3.9 (+7.1) | --- |  |  |
| A20 TVP_lvn skip | 26373 | -14% | -27% | -2% | -20% | -4% | -39% | -10% | -34% | -0.0 (+13.7) | -2.0 (+9.7) | -3.1 (+8.5) | --- |  | placebo pending |
| B20 TPF_sessday skip | 3923 | -14% | +0% | -24% | -14% | -14% | -49% | +10% | -25% | -0.4 (+2.6) | +2.9 (+6.4) | -2.6 (+5.9) | --- |  |  |
| A20 TVP_hvn half | 14937 | -14% | +8% | +20% | -14% | -14% | -40% | -15% | -15% | +0.2 (+4.5) | +2.7 (+7.2) | -2.5 (+6.1) | --- |  |  |
| A40 TCD_ext half | 15965 | -14% | -29% | -37% | -25% | -14% | -11% | -2% | -28% | +0.7 (+10.9) | -1.0 (+6.7) | -4.2 (+3.6) | --Y |  | ONE-WEEK, placebo pending |
| A20 TVP_poc skip | 2198 | -13% | +0% | -24% | -13% | -13% | -42% | -13% | +7% | +1.2 (+2.4) | +3.6 (+6.4) | +0.9 (+2.6) | --Y |  |  |
| A40 TCD_div skip | 3318 | -13% | -1% | -24% | -13% | -13% | -48% | +33% | -31% | -0.0 (+3.3) | +1.6 (+4.5) | -1.6 (+4.2) | --- |  |  |
| A40 TVP_hvn half | 23410 | -12% | +4% | +31% | -12% | -12% | -44% | -13% | -21% | +0.9 (+4.8) | +3.5 (+7.1) | -5.1 (+6.9) | --- |  |  |
| A40 TVP_poc skip | 3491 | -11% | +16% | -12% | -11% | -11% | -42% | -13% | +9% | +1.8 (+2.5) | +4.1 (+6.7) | +0.3 (+2.9) | --Y |  |  |
| A20 TCP_60d half | 1673 | -11% | +0% | -24% | -11% | -11% | -50% | +32% | +10% | +0.1 (+1.5) | -0.2 (+5.1) | -2.7 (+4.2) | --Y |  |  |
| A20 TLQ_sess half | 12397 | -9% | +0% | -23% | -9% | -9% | +8% | -11% | -2% | +2.4 (+4.1) | -0.9 (+3.0) | -2.0 (+3.9) | --Y |  |  |
| A20 TPF_wkmo half | 2109 | -9% | +0% | -24% | -9% | -9% | +3% | +6% | -27% | -0.0 (+1.4) | -1.8 (+3.4) | -1.5 (+3.2) | --- |  |  |

**Group cells all 22 groups x D20/D40 x skip/half, BEHIND-20 skip and AT x1.5 are in `cells_summary.csv` (115 cells scored in pass 1 so far); the individual-stream cells follow in the same file.**

### Episode-proofing of the finalists (maxDD cut; leave-one-week-out, leave-one-month-out, month-block bootstrap 90% CI)
| cell | window | cut | base maxDD week | cut without the single most influential week (min) | max | min leave-one-month-out | bootstrap 90% CI | label |
|---|---|---|---|---|---|---|---|---|
| A40 TVP_lvn half | F9 | +31% | 2026-09-14 | +4% | +59% | +4% | [-16%, +69%] | ONE-WEEK |
| A40 TVP_lvn half | HOLD | +29% | 2026-09-14 | +2% | +48% | +2% | [-11%, +65%] | ONE-WEEK |
| A40 TVP_lvn half | L3M | +37% | 2026-09-14 | -17% | +47% | +18% | [+15%, +68%] | ONE-WEEK |
| A40 TPF_sessday half | F9 | +29% | 2026-09-14 | +1% | +43% | +1% | [-44%, +66%] | ONE-WEEK |
| A40 TPF_sessday half | HOLD | +29% | 2026-09-14 | +1% | +48% | +1% | [-29%, +64%] | ONE-WEEK |
| A40 TPF_sessday half | L3M | -16% | 2026-09-14 | -30% | +12% | -16% | [-19%, +37%] |  |
| A20 TVP_void skip | F9 | +32% | 2026-09-14 | +1% | +37% | +6% | [-21%, +39%] | ONE-WEEK |
| A20 TVP_void skip | HOLD | +32% | 2026-09-14 | +1% | +36% | +6% | [-15%, +40%] | ONE-WEEK |
| A20 TVP_void skip | L3M | +24% | 2026-09-14 | +0% | +37% | +0% | [+0%, +55%] | ONE-WEEK |
| A20 TVP_lvn half | F9 | +16% | 2026-09-14 | -17% | +32% | -17% | [-61%, +55%] | ONE-WEEK |
| A20 TVP_lvn half | HOLD | +16% | 2026-09-14 | -17% | +38% | -17% | [-48%, +53%] | ONE-WEEK |
| A20 TVP_lvn half | L3M | +35% | 2026-09-14 | -33% | +40% | +18% | [-0%, +47%] | ONE-WEEK |
| A20 TCD_ext skip | F9 | +4% | 2026-09-14 | -33% | +31% | -33% | [-78%, +56%] |  |
| A20 TCD_ext skip | HOLD | +4% | 2026-09-14 | -33% | +31% | -33% | [-72%, +54%] |  |
| A20 TCD_ext skip | L3M | +37% | 2026-09-14 | +18% | +47% | +18% | [+12%, +70%] |  |
| A20 TLQ_swg15 half | F9 | +28% | 2026-09-14 | +8% | +35% | +9% | [-61%, +40%] | ONE-WEEK |
| A20 TLQ_swg15 half | HOLD | +28% | 2026-09-14 | +8% | +35% | +9% | [-42%, +41%] | ONE-WEEK |
| A20 TLQ_swg15 half | L3M | -2% | 2026-09-14 | -31% | +22% | -2% | [-2%, +9%] |  |
| A40 TVP_hvn skip | F9 | +27% | 2026-09-14 | -25% | +40% | +17% | [-38%, +55%] | ONE-WEEK |
| A40 TVP_hvn skip | HOLD | +27% | 2026-09-14 | -25% | +40% | +17% | [-37%, +54%] | ONE-WEEK |
| A40 TVP_hvn skip | L3M | -78% | 2026-09-14 | -87% | -34% | -78% | [-105%, +9%] |  |
| A40 TCD_ext half | F9 | +14% | 2026-09-14 | -20% | +25% | -20% | [-64%, +35%] | ONE-WEEK |
| A40 TCD_ext half | HOLD | +14% | 2026-09-14 | -20% | +25% | -20% | [-61%, +33%] | ONE-WEEK |
| A40 TCD_ext half | L3M | +37% | 2026-09-14 | +18% | +47% | +18% | [+18%, +72%] |  |

### Per session (F9, finalists): delta mean $/wk and maxDD, base -> cell

`A40 TVP_lvn half`

| session | base mean | delta mean | base maxDD | cell maxDD |
|---|---|---|---|---|
| asia | +19.3 | +0.8 | 88k | 49k |
| london | +1.7 | +3.2 | 85k | 62k |
| pre | +0.0 | +0.0 | 0k | 0k |
| nyam | +1.1 | -0.3 | 18k | 23k |
| nypm | -0.0 | +0.2 | 11k | 14k |
| close | +0.0 | +0.0 | 0k | 0k |

Vol terciles of the weeks (target-distance proxy): T1: 13 weeks, base -13.9, delta +6.4 $k/wk; T2: 12 weeks, base +48.0, delta +3.7 $k/wk; T3: 13 weeks, base +34.1, delta +1.2 $k/wk

`A40 TPF_sessday half`

| session | base mean | delta mean | base maxDD | cell maxDD |
|---|---|---|---|---|
| asia | +19.3 | -0.4 | 88k | 53k |
| london | +1.7 | +2.1 | 85k | 76k |
| pre | +0.0 | +0.0 | 0k | 0k |
| nyam | +1.1 | -0.1 | 18k | 13k |
| nypm | -0.0 | +0.0 | 11k | 12k |
| close | +0.0 | +0.0 | 0k | 0k |

Vol terciles of the weeks (target-distance proxy): T1: 13 weeks, base -13.9, delta +3.6 $k/wk; T2: 12 weeks, base +48.0, delta -1.8 $k/wk; T3: 13 weeks, base +34.1, delta +2.3 $k/wk

`A20 TVP_void skip`

| session | base mean | delta mean | base maxDD | cell maxDD |
|---|---|---|---|---|
| asia | +19.3 | +1.8 | 88k | 66k |
| london | +1.7 | +0.8 | 85k | 77k |
| pre | +0.0 | +0.0 | 0k | 0k |
| nyam | +1.1 | -0.3 | 18k | 15k |
| nypm | -0.0 | -0.1 | 11k | 16k |
| close | +0.0 | +0.0 | 0k | 0k |

Vol terciles of the weeks (target-distance proxy): T1: 13 weeks, base -13.9, delta -1.8 $k/wk; T2: 12 weeks, base +48.0, delta +1.1 $k/wk; T3: 13 weeks, base +34.1, delta +7.2 $k/wk

`A20 TVP_lvn half`

| session | base mean | delta mean | base maxDD | cell maxDD |
|---|---|---|---|---|
| asia | +19.3 | -0.6 | 88k | 80k |
| london | +1.7 | +0.4 | 85k | 103k |
| pre | +0.0 | +0.0 | 0k | 0k |
| nyam | +1.1 | -0.6 | 18k | 26k |
| nypm | -0.0 | -0.0 | 11k | 13k |
| close | +0.0 | +0.0 | 0k | 0k |

Vol terciles of the weeks (target-distance proxy): T1: 13 weeks, base -13.9, delta +0.9 $k/wk; T2: 12 weeks, base +48.0, delta +2.0 $k/wk; T3: 13 weeks, base +34.1, delta -5.1 $k/wk

### Definition sensitivity (D scaled 0.5 / 0.75 / 1.25 / 1.5 x the cell's D; maxDD change F9 / HOLD / PRE) - FRAGILE if the cut exists at one D only
| group / action | D | rows | F9 | HOLD | PRE | label |
|---|---|---|---|---|---|---|
| TVP_lvn half | 20 | 26373 | -16% | -16% | -5% |  |
| TVP_lvn half | 40 | 39987 | -31% | -29% | -12% |  |
| TPF_sessday half | 20 | 14967 | -16% | -16% | -1% |  |
| TPF_sessday half | 40 | 25294 | -29% | -29% | -0% |  |
| TVP_void skip | 20 | 3497 | -32% | -32% | +14% |  |
| TVP_lvn half | 20 | 26373 | -16% | -16% | -5% |  |
| TCD_ext skip | 20 | 10122 | -4% | -4% | -28% |  |
| TLQ_swg15 half | 20 | 19762 | -28% | -28% | +10% |  |
| TVP_hvn skip | 20 | 14937 | +7% | +7% | +4% |  |
| TVP_hvn skip | 40 | 23410 | -27% | -27% | +19% |  |
| TCD_ext half | 20 | 10122 | -25% | -25% | -21% |  |
| TCD_ext half | 40 | 15965 | -14% | -14% | -2% |  |

## Streams on the new cap (descriptive, new windows)
Stream table and hit-rate table: `out/zl/desc_new/stream_table.csv` (all 126 rows; ranks vs random-level and shuffled-day placebos, 200 draws each; windows ALL X' PRE HOLD MID L6M L3M L1M).
* HOLD5 rank >= 0.975 against BOTH placebos, whole sample: TCP_hvn1_60d, TCP_vah_5d, TLP_cl25_4h, TPF_hvn2_sess (chance about 3 of 117). HOLD (2025-11..2026-10): TCP_hvn1_60d, TCP_lvn1_5d, TLP_p50_1h, TLP_p50_4h, TPF_hvn1_week, TPF_hvn2_sess, TPF_lvn0_sess. L6M: TCP_hvn1_60d, TPF_lvn0_sess, TPF_vah_sw15, TPF_val_sess, TVP_lvn_day.
* Run-through levels: 27 streams rank <= 0.025 against both placebos in the whole sample, 22 of them pool sources (swing / equal / session / killzone / prior-day H/L).

| level type | levels | broken | pool P10 | P50 | P90 | pool < 10 | >= 100 | volume beyond P50 | median excursion 15 min | re-claimed 5 min |
|---|---|---|---|---|---|---|---|---|---|---|
| EQL|tight|15m | 1837 | 89% | 5 | 17 | 62 | 27% | 4% | 157 | 7.8 | 47% |
| EQL|tight|1h | 178 | 77% | 6 | 23 | 84 | 20% | 7% | 293 | 10.2 | 43% |
| KZ|kz_asia | 1928 | 84% | 4 | 15 | 48 | 31% | 2% | 206 | 10.2 | 49% |
| KZ|kz_lc | 1922 | 65% | 8 | 35 | 101 | 12% | 10% | 1014 | 17.0 | 48% |
| KZ|kz_london | 1926 | 81% | 4 | 19 | 69 | 26% | 5% | 306 | 12.5 | 51% |
| KZ|kz_ny | 1928 | 67% | 9 | 40 | 112 | 11% | 14% | 1466 | 23.5 | 48% |
| PDX|day | 1926 | 40% | 5 | 22 | 79 | 22% | 6% | 541 | 16.8 | 43% |
| PDX|rth | 1922 | 48% | 4 | 22 | 83 | 23% | 7% | 622 | 17.5 | 44% |
| PDX|week | 388 | 52% | 2 | 24 | 91 | 24% | 8% | 932 | 20.8 | 42% |
| SES|asia | 1928 | 78% | 5 | 18 | 62 | 24% | 4% | 298 | 13.5 | 47% |
| SES|close | 1852 | 64% | 3 | 13 | 59 | 38% | 3% | 252 | 12.5 | 45% |
| SES|london | 1926 | 74% | 6 | 30 | 90 | 17% | 9% | 842 | 20.5 | 50% |
| SES|nyam | 1922 | 59% | 8 | 36 | 109 | 12% | 13% | 1114 | 17.5 | 47% |
| SES|nypm | 1922 | 65% | 5 | 28 | 96 | 18% | 9% | 618 | 17.0 | 48% |
| SES|on | 1928 | 64% | 12 | 46 | 118 | 6% | 15% | 1500 | 28.5 | 47% |
| SES|pre | 1928 | 82% | 10 | 42 | 115 | 9% | 14% | 1652 | 29.2 | 49% |
| SES|rth | 1922 | 48% | 4 | 22 | 83 | 23% | 7% | 622 | 17.5 | 44% |
| SWG|f3|15m | 38772 | 86% | 4 | 16 | 65 | 31% | 4% | 225 | 11.8 | 48% |
| SWG|f3|1h | 9725 | 73% | 5 | 20 | 75 | 24% | 6% | 375 | 14.0 | 47% |
| SWG|f5|15m | 22987 | 82% | 4 | 17 | 69 | 28% | 5% | 274 | 12.2 | 48% |
| SWG|f5|1h | 5721 | 67% | 5 | 22 | 80 | 22% | 6% | 467 | 15.8 | 46% |
| SWG|f7|15m | 16447 | 79% | 4 | 18 | 71 | 27% | 5% | 311 | 13.0 | 48% |
| SWG|f7|1h | 4118 | 62% | 6 | 24 | 88 | 19% | 8% | 572 | 16.8 | 46% |

| pool measure | window | n | excursion bottom / mid / top tercile | top - bottom | re-claim top - bottom |
|---|---|---|---|---|---|
| pool_aggr | ALL | 97971 | 11.25 / 11.50 / 17.50 | +6.25 | +0.016 |
| pool_aggr | HOLD | 25841 | 18.50 / 18.00 / 26.25 | +7.75 | +0.008 |
| str_exp | ALL | 97945 | 13.25 / 13.25 / 12.75 | -0.50 | +0.004 |
| str_exp | HOLD | 25841 | 21.50 / 20.50 / 19.75 | -1.75 | -0.020 |
| vol_beyond | ALL | 97971 | 5.75 / 12.25 / 28.50 | +22.75 | -0.245 |
| vol_beyond | HOLD | 25841 | 10.00 / 19.00 / 42.75 | +32.75 | -0.236 |

## Live definitions
Unchanged from the OLD CAP page, section 4 (`DS3_ZONES_3_L2_TAPE.md`): D7 computes TPF session/day/sw lines, TVP, TDA, TCD, TLP from its own print tape; composites, the burst threshold and the per-type median pool need the daily zones file.
