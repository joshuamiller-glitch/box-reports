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
| A20 TVP_void skip | 3497 | -32% | +0% | -24% | -37% | -32% | -6% | +14% | -5% | +5.3 (+5.4) | +2.0 (+4.2) | -1.5 (+4.8) | -YY | 1.00/1.00/0.75 (4) | ONE-WEEK, placebo rank <0.9 (volume effect, coarse n=4) |
| A40 TVP_lvn half | 39987 | -31% | -28% | -37% | -51% | -29% | -60% | -12% | -20% | +1.8 (+13.1) | +2.5 (+8.9) | -4.8 (+6.4) | --Y | 0.33/0.75/0.75 (3) | ONE-WEEK, placebo rank <0.9 (volume effect, coarse n=3) |
| A40 TPF_sessday half | 25294 | -29% | -28% | +16% | -43% | -29% | -71% | -0% | -25% | +0.7 (+11.4) | -1.9 (+10.4) | -7.5 (+7.6) | --- | 1.00/0.75/1.00 (4) | ONE-WEEK, placebo rank <0.9 (volume effect, coarse n=4) |
| A20 TLQ_swg15 half | 19762 | -28% | -13% | +2% | -28% | -28% | -39% | +10% | -13% | -1.6 (+10.1) | -1.4 (+6.1) | -6.2 (+5.7) | --- | 0.75/1.00/0.75 (4) | ONE-WEEK, placebo rank <0.9 (volume effect, coarse n=4) |
| A40 TVP_hvn skip | 23410 | -27% | -14% | +78% | -27% | -27% | -17% | +19% | -39% | +0.9 (+10.6) | -0.3 (+8.6) | -5.8 (+10.1) | --- | 1.00/0.75/0.75 (4) | ONE-WEEK, placebo rank <0.9 (volume effect, coarse n=4) |
| A40 TVP_void skip | 7284 | -26% | +0% | -24% | -26% | -26% | -48% | +59% | -37% | +7.8 (+9.6) | +6.7 (+8.5) | -3.2 (+5.9) | --Y |  | placebo pending |
| A20 TCD_ext half | 10122 | -25% | -7% | -29% | -25% | -25% | -41% | -21% | -22% | -2.5 (+9.7) | -2.3 (+6.6) | -2.2 (+3.0) | --- |  | placebo pending |
| B20 TPF_sw15 skip | 9157 | -22% | -1% | +5% | -22% | -22% | -37% | -1% | -39% | -0.1 (+5.5) | +0.7 (+5.7) | -4.2 (+7.8) | --- |  | placebo pending |
| B20 NEW3 skip | 3603 | -21% | +0% | +8% | -21% | -21% | -40% | -23% | +27% | +0.5 (+3.9) | +2.1 (+4.4) | -0.4 (+3.3) | --- |  | placebo pending |
| A40 TPF_sw15 half | 13744 | -20% | +2% | +8% | -20% | -20% | -35% | -30% | -5% | -0.8 (+4.6) | -0.8 (+4.5) | -3.9 (+5.8) | --- |  |  |
| A40 TPF_sessday skip | 25294 | -16% | -41% | +119% | -16% | -16% | -37% | +15% | -73% | -2.1 (+16.8) | +3.1 (+12.0) | -5.8 (+9.4) | --- |  |  |
| A20 TVP_lvn half | 26373 | -16% | -26% | -35% | -32% | -16% | -61% | -5% | -6% | -0.7 (+10.6) | -0.6 (+7.1) | -5.1 (+5.8) | --- | 0.50/0.00/0.50 (4) | ONE-WEEK, placebo rank <0.9 (volume effect, coarse n=4) |
| A20 TPF_sessday half | 14967 | -16% | -27% | +3% | -16% | -16% | -53% | -1% | -28% | -4.6 (+11.5) | -2.6 (+7.5) | -3.9 (+7.1) | --- |  |  |
| A20 TVP_lvn skip | 26373 | -14% | -27% | -2% | -20% | -4% | -39% | -10% | -34% | -0.0 (+13.7) | -2.0 (+9.7) | -3.1 (+8.5) | --- |  | placebo pending |
| B20 TPF_sessday skip | 3923 | -14% | +0% | -24% | -14% | -14% | -49% | +10% | -25% | -0.4 (+2.6) | +2.9 (+6.4) | -2.6 (+5.9) | --- |  |  |
| A20 TVP_hvn half | 14937 | -14% | +8% | +20% | -14% | -14% | -40% | -15% | -15% | +0.2 (+4.5) | +2.7 (+7.2) | -2.5 (+6.1) | --- |  |  |
| A40 TCD_ext half | 15965 | -14% | -29% | -37% | -25% | -14% | -11% | -2% | -28% | +0.7 (+10.9) | -1.0 (+6.7) | -4.2 (+3.6) | --Y | 0.75/0.25/0.25 (4) | ONE-WEEK, placebo rank <0.9 (volume effect, coarse n=4) |
| A20 TVP_poc skip | 2198 | -13% | +0% | -24% | -13% | -13% | -42% | -13% | +7% | +1.2 (+2.4) | +3.6 (+6.4) | +0.9 (+2.6) | --Y |  |  |
| A40 TCD_div skip | 3318 | -13% | -1% | -24% | -13% | -13% | -48% | +33% | -31% | -0.0 (+3.3) | +1.6 (+4.5) | -1.6 (+4.2) | --- |  |  |
| A40 TVP_hvn half | 23410 | -12% | +4% | +31% | -12% | -12% | -44% | -13% | -21% | +0.9 (+4.8) | +3.5 (+7.1) | -5.1 (+6.9) | --- |  |  |
| A40 TVP_poc skip | 3491 | -11% | +16% | -12% | -11% | -11% | -42% | -13% | +9% | +1.8 (+2.5) | +4.1 (+6.7) | +0.3 (+2.9) | --Y |  |  |
| A20 TCP_60d half | 1673 | -11% | +0% | -24% | -11% | -11% | -50% | +32% | +10% | +0.1 (+1.5) | -0.2 (+5.1) | -2.7 (+4.2) | --Y |  |  |
| A20 TLQ_sess half | 12397 | -9% | +0% | -23% | -9% | -9% | +8% | -11% | -2% | +2.4 (+4.1) | -0.9 (+3.0) | -2.0 (+3.9) | --Y |  |  |
| A20 TPF_wkmo half | 2109 | -9% | +0% | -24% | -9% | -9% | +3% | +6% | -27% | -0.0 (+1.4) | -1.8 (+3.4) | -1.5 (+3.2) | --- |  |  |

**Group cells all 22 groups x D20/D40 x skip/half, BEHIND-20 skip and AT x1.5 are in `cells_summary.csv` (203 cells scored in pass 1 so far); the individual-stream cells follow in the same file.**

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

### Definition sensitivity ON D7 v1.3 (D scaled 0.5 / 0.75 / 1.25 / 1.5 x the cell's D; maxDD change F9 / HOLD / PRE) - FRAGILE if the cut exists at one D only
| group / action | D | rows | F9 | HOLD | PRE | label |
|---|---|---|---|---|---|---|
| TVP_lvn half | 20 | 26373 | -8% | -8% | -22% | FRAGILE |
| TVP_lvn half | 30 | 34672 | -8% | -8% | -15% | FRAGILE |
| TVP_lvn half | 40 | 39987 | -5% | -5% | -19% | FRAGILE |
| TVP_lvn half | 50 | 43853 | -6% | -6% | -20% | FRAGILE |
| TVP_lvn half | 60 | 46847 | +8% | +8% | -23% | FRAGILE |
| TPF_sessday half | 20 | 14967 | -22% | -22% | -8% |  |
| TPF_sessday half | 30 | 21048 | -13% | -13% | +4% |  |
| TPF_sessday half | 40 | 25294 | -12% | -12% | +21% |  |
| TPF_sessday half | 50 | 28566 | -16% | -16% | -7% |  |
| TPF_sessday half | 60 | 31304 | -18% | -18% | -7% |  |
| TVP_void skip | 10 | 1411 | -1% | -1% | +22% |  |
| TVP_void skip | 15 | 2482 | -2% | -2% | -4% |  |
| TVP_void skip | 20 | 3497 | -5% | -5% | -2% |  |
| TVP_void skip | 25 | 4490 | -18% | -18% | -13% |  |
| TVP_void skip | 30 | 5415 | -18% | -18% | -26% |  |
| TVP_lvn half | 10 | 14690 | +7% | +7% | +5% | FRAGILE |
| TVP_lvn half | 15 | 21093 | -1% | -1% | -16% | FRAGILE |
| TVP_lvn half | 20 | 26373 | -8% | -8% | -22% | FRAGILE |
| TVP_lvn half | 25 | 30879 | -10% | -10% | -15% | FRAGILE |
| TVP_lvn half | 30 | 34672 | -8% | -8% | -15% | FRAGILE |
| TCD_ext skip | 10 | 5592 | +18% | +18% | -9% | FRAGILE |
| TCD_ext skip | 15 | 8086 | -4% | -4% | +39% | FRAGILE |
| TCD_ext skip | 20 | 10122 | -4% | -4% | -25% | FRAGILE |
| TCD_ext skip | 25 | 11984 | +1% | +1% | +10% | FRAGILE |
| TCD_ext skip | 30 | 13563 | +2% | +2% | +34% | FRAGILE |
| TLQ_swg15 half | 10 | 9207 | +17% | +17% | +12% | FRAGILE |
| TLQ_swg15 half | 15 | 14749 | +16% | +16% | +26% | FRAGILE |
| TLQ_swg15 half | 20 | 19762 | +11% | +11% | +3% | FRAGILE |
| TLQ_swg15 half | 25 | 24266 | -0% | -0% | +3% | FRAGILE |
| TLQ_swg15 half | 30 | 28464 | +51% | +51% | -6% | FRAGILE |
| TVP_hvn skip | 20 | 14937 | -12% | -12% | -15% |  |
| TVP_hvn skip | 30 | 20036 | +21% | +21% | -16% |  |
| TVP_hvn skip | 40 | 23410 | -27% | -20% | -36% |  |
| TVP_hvn skip | 50 | 25791 | -25% | -25% | -39% |  |
| TVP_hvn skip | 60 | 27601 | +20% | +20% | -45% |  |
| TCD_ext half | 20 | 10122 | -5% | -5% | +2% | FRAGILE |
| TCD_ext half | 30 | 13563 | -7% | -7% | +13% | FRAGILE |
| TCD_ext half | 40 | 15965 | -7% | -7% | +17% | FRAGILE |
| TCD_ext half | 50 | 17805 | -9% | -9% | +9% | FRAGILE |
| TCD_ext half | 60 | 19375 | +3% | +3% | +19% | FRAGILE |


## On D7 v1.3 (profit side = gated take lines) - finalists and the cells run so far
v1.3 base lines (maxDD / mean $k/wk): F9 94.1k / +21.4; L3M 43.6k / +8.2; L6M 94.1k / +21.3; HOLD 94.1k / +23.5; MID 43.1k / +19.7; PRE 175.1k / +2.9; X' 234.6k / -3.9. Cells run on v1.3: 152.

| cell | rows | F9 | L1M | L3M | L6M | HOLD | MID | PRE | X' | mean L6M (MDE) | mean HOLD (MDE) | S/T/N | v1.2 F9 | one-week check F9 (cut without the key week) | placebo ranks sv/rd/sd (n) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A40 TVP_lvn skip | 39987 | -28% | -4% | -46% | -28% | -4% | -8% | -19% | -18% | +8.4 (+20.0) | -0.4 (+13.6) | -YY | -43% | +12% |  |
| A40 TVP_hvn skip | 23410 | -27% | +5% | +27% | -27% | -20% | -12% | -36% | -55% | +4.4 (+11.9) | -2.1 (+10.1) | --- | -27% | -19% ONE-WEEK | 1.00/0.75/1.00 (4) |
| A50 TVP_hvn skip | 25791 | -25% | +5% | +30% | -25% | -25% | -39% | -39% | -58% | +3.5 (+12.7) | -0.0 (+8.8) | --- |  | -21% ONE-WEEK |  |
| A20 TPF_sessday half | 14967 | -22% | -4% | -41% | -22% | -22% | -29% | -8% | -21% | -1.2 (+3.5) | -5.9 (+7.3) | --- | -16% | +10% |  |
| A40 TCD_div skip | 3318 | -20% | -1% | -46% | -20% | -20% | +3% | -19% | -25% | +1.0 (+5.5) | -0.2 (+3.5) | --Y | -13% | -2% ONE-WEEK |  |
| A30 TVP_void skip | 5415 | -18% | +5% | -38% | -18% | -18% | -17% | -26% | -22% | +7.4 (+9.9) | +3.8 (+5.9) | Y-Y |  | +1% ONE-WEEK |  |
| A60 TPF_sessday half | 31304 | -18% | +6% | -45% | -18% | -18% | -32% | -7% | -37% | +1.0 (+7.1) | -4.3 (+9.8) | -YY |  | -10% ONE-WEEK |  |
| A25 TVP_void skip | 4490 | -18% | +5% | -46% | -18% | -18% | -19% | -13% | -27% | +7.3 (+9.8) | +3.7 (+5.7) | Y-Y |  | +0% ONE-WEEK |  |
| A20 TVP_poc skip | 2198 | -17% | +0% | -39% | -17% | -17% | +19% | -19% | -26% | +4.6 (+10.8) | +1.1 (+6.6) | YYY | -13% | +0% ONE-WEEK |  |
| A50 TPF_sessday half | 28566 | -16% | +6% | -41% | -16% | -16% | -37% | -7% | -35% | +1.4 (+7.1) | -4.0 (+9.8) | -YY |  | -14% ONE-WEEK |  |
| A30 TPF_sessday half | 21048 | -13% | +6% | -34% | -13% | -13% | -41% | +4% | -26% | -1.6 (+5.0) | -7.1 (+9.7) | --- |  | +5% ONE-WEEK |  |
| A40 TPF_sw15 half | 13744 | -12% | +13% | -38% | -12% | -12% | -43% | +59% | -27% | +2.3 (+11.4) | -5.2 (+11.5) | --Y | -20% | -3% ONE-WEEK |  |
| A20 TVP_hvn skip | 14937 | -12% | +7% | -46% | -12% | -12% | -9% | -15% | -56% | +4.1 (+10.4) | +1.5 (+7.0) | YYY | +7% | -6% ONE-WEEK |  |
| A40 TPF_sessday half | 25294 | -12% | +6% | -40% | -12% | -12% | -33% | +21% | -27% | +1.3 (+7.6) | -5.0 (+10.0) | -YY | -29% | -20% ONE-WEEK | 0.75/0.25/0.75 (4) |
| B20 TPF_sessday skip | 3923 | -12% | +5% | -22% | -12% | -12% | +0% | +21% | +22% | -0.9 (+2.3) | -0.7 (+1.9) | --- | -14% | +2% ONE-WEEK |  |
| A20 TCP_60d half | 1673 | -11% | +0% | -22% | -11% | -11% | +0% | +12% | -6% | +0.0 (+1.0) | -1.3 (+2.7) | --Y | -11% | +1% ONE-WEEK |  |
| A40 TVP_hvn half | 23410 | -11% | +17% | -19% | -11% | -11% | +54% | -25% | -18% | +3.6 (+9.8) | -2.5 (+9.6) | -YY | -12% | +2% ONE-WEEK |  |
| A25 TVP_lvn half | 30879 | -10% | -4% | -46% | -10% | -10% | -35% | -15% | -23% | +3.9 (+14.6) | -1.6 (+9.7) | -YY |  | -0% ONE-WEEK |  |
| A50 TCD_ext half | 17805 | -9% | -4% | -46% | -9% | -9% | +12% | +9% | +15% | +5.1 (+12.1) | -0.3 (+8.6) | -YY |  | -10% |  |
| A30 TVP_lvn half | 34672 | -8% | -4% | -46% | -8% | -8% | -33% | -15% | -24% | +3.9 (+14.7) | -1.3 (+9.7) | -YY |  | -2% |  |
| A20 TVP_lvn half | 26373 | -8% | +21% | -39% | -8% | -8% | -40% | -22% | -16% | +3.0 (+12.4) | -2.1 (+8.8) | -YY | -16% | -3% | 0.75/0.50/0.25 (4) |
| A30 TCD_ext half | 13563 | -7% | +7% | -46% | -7% | -7% | +22% | +13% | +24% | +5.8 (+13.5) | -0.0 (+9.1) | -YY |  | -13% |  |
| A40 TCD_ext half | 15965 | -7% | +7% | -46% | -7% | -7% | +14% | +17% | +12% | +5.6 (+12.3) | -0.1 (+8.6) | -YY | -14% | -13% | 0.75/1.00/0.50 (4) |
| A50 TVP_lvn half | 43853 | -6% | -4% | -46% | -6% | -6% | -50% | -20% | -34% | +2.1 (+15.3) | -0.9 (+9.9) | -YY |  | -9% |  |
| A40 TVP_lvn half | 39987 | -5% | -4% | -46% | -5% | -5% | -44% | -19% | -26% | +3.6 (+14.9) | -1.8 (+10.3) | -YY | -31% | -7% | 0.25/0.50/0.25 (4) |
| A20 TCD_ext half | 10122 | -5% | +3% | -46% | -5% | -5% | +17% | +2% | +19% | +2.4 (+12.3) | +1.0 (+7.3) | -YY | -25% | -15% |  |
| A20 TVP_void skip | 3497 | -5% | +0% | -11% | -5% | -5% | +31% | -2% | -5% | +3.1 (+4.3) | -0.3 (+5.0) | --Y | -32% | -1% | 0.50/0.75/0.50 (4) |
| A20 TCD_ext skip | 10122 | -4% | +2% | -32% | -4% | -4% | +2% | -25% | +2% | +1.4 (+17.5) | -3.2 (+13.2) | --Y | -4% | -16% | 0.50/0.50/0.75 (4) |
| A15 TCD_ext skip | 8086 | -4% | +2% | -46% | -4% | -4% | -6% | +39% | -8% | +0.9 (+17.7) | -3.5 (+13.1) | --Y |  | -17% |  |
| A40 TVP_void skip | 7284 | -3% | +5% | -46% | -3% | -3% | -34% | -21% | -17% | +10.6 (+12.3) | +5.5 (+7.3) | Y-Y | -26% | -17% |  |
| A15 TVP_void skip | 2482 | -2% | +0% | -4% | -2% | -2% | +48% | -4% | -6% | +3.1 (+4.5) | -0.7 (+4.8) | --Y |  | -8% |  |
| A40 TVP_poc skip | 3491 | -1% | +30% | -40% | -1% | -1% | +19% | -14% | -9% | +4.8 (+10.9) | +1.9 (+7.1) | -YY | -11% | -19% |  |
| A10 TVP_void skip | 1411 | -1% | +0% | -2% | -1% | -1% | +46% | +22% | -3% | +1.8 (+2.4) | -0.7 (+4.1) | --Y |  | -8% |  |
| A15 TVP_lvn half | 21093 | -1% | +30% | -28% | -1% | -1% | +92% | -16% | -5% | +3.9 (+12.3) | -3.4 (+9.2) | -YY |  | -22% |  |
| A25 TLQ_swg15 half | 24266 | -0% | -4% | -4% | -0% | -0% | +62% | +3% | -5% | -0.2 (+10.1) | -7.0 (+11.2) | --- |  | -34% |  |
| A25 TCD_ext skip | 11984 | +1% | -2% | -17% | +1% | +1% | +15% | +10% | -34% | -0.0 (+17.5) | -3.0 (+13.1) | --- |  | -16% |  |
| A30 TCD_ext skip | 13563 | +2% | +13% | -17% | +2% | +2% | -5% | +34% | -41% | +3.2 (+19.3) | -4.3 (+14.3) | --- |  | -18% |  |
| A60 TCD_ext half | 19375 | +3% | -4% | -14% | +3% | +3% | +12% | +19% | +1% | +3.7 (+12.2) | -1.3 (+8.6) | --- |  | -16% |  |
| A20 TVP_hvn half | 14937 | +4% | +15% | -46% | +4% | +4% | +3% | -0% | -11% | +0.4 (+5.2) | -2.4 (+7.4) | --- | -14% | -25% |  |
| B20 NEW3 skip | 3603 | +6% | +0% | -9% | +6% | +6% | +19% | +13% | +0% | -0.7 (+2.1) | +0.1 (+1.7) | --- | -21% | -9% |  |
| A10 TVP_lvn half | 14690 | +7% | +23% | -22% | +7% | +7% | -10% | +5% | -4% | +3.1 (+11.1) | -2.0 (+8.0) | --- |  | -20% |  |
| A60 TVP_lvn half | 46847 | +8% | -4% | -2% | +8% | +8% | -63% | -23% | -56% | +1.6 (+14.4) | -1.6 (+9.7) | --- |  | -20% |  |
| A20 TLQ_swg15 half | 19762 | +11% | -4% | +20% | +11% | +11% | +36% | +3% | +3% | +2.9 (+10.2) | -5.2 (+11.1) | --- | -28% | -24% | 0.25/0.25/0.25 (4) |
| B20 TPF_sw15 skip | 9157 | +13% | -2% | +5% | +13% | +13% | +15% | +9% | +15% | -1.6 (+3.9) | -1.6 (+3.2) | --- | -22% | -19% |  |
| A15 TLQ_swg15 half | 14749 | +16% | -4% | +34% | +16% | +16% | +13% | +26% | +3% | +1.1 (+4.5) | -2.5 (+5.9) | --- |  | -29% |  |
| A10 TLQ_swg15 half | 9207 | +17% | +2% | +21% | +17% | +17% | +5% | +12% | +11% | +0.7 (+5.0) | -2.5 (+6.2) | --- |  | -24% |  |
| A10 TCD_ext skip | 5592 | +18% | -4% | -33% | +18% | +18% | +0% | -9% | -27% | -1.0 (+15.9) | -2.5 (+9.0) | --- |  | -41% |  |
| A20 TVP_lvn skip | 26373 | +19% | +34% | +11% | +19% | +19% | +14% | -3% | -27% | +3.1 (+17.8) | -5.7 (+12.3) | --- | -14% | -41% |  |
| A60 TVP_hvn skip | 27601 | +20% | +5% | +59% | +20% | +20% | -17% | -45% | -53% | -3.3 (+16.2) | -6.9 (+10.4) | --- |  | -60% |  |
| A30 TVP_hvn skip | 20036 | +21% | +7% | +13% | +21% | +21% | -12% | -16% | -55% | +1.8 (+12.3) | -1.5 (+8.7) | --- |  | -31% |  |
| A20 NEW3 half | 5465 | +21% | -2% | -29% | +21% | +21% | +21% | +1% | +18% | +3.0 (+10.4) | -0.6 (+6.8) | --- | +8% | -37% |  |
| A20 NEW3 skip | 5465 | +37% | -4% | -5% | +37% | +37% | +7% | -11% | +9% | +2.5 (+10.3) | -4.2 (+9.8) | --- | +10% | -48% |  |
| A40 NEW3 half | 10266 | +41% | +9% | +11% | +41% | +41% | +75% | +11% | +17% | +1.1 (+10.1) | -3.2 (+7.5) | --- | +18% | -53% |  |
| A40 TPF_sessday skip | 25294 | +43% | +16% | +55% | +43% | +43% | -16% | -10% | -65% | +0.5 (+16.9) | -0.6 (+10.1) | --- | -16% | -115% |  |
| A30 TLQ_swg15 half | 28464 | +51% | -4% | +47% | +51% | +51% | +74% | -6% | -4% | -2.7 (+9.3) | -8.2 (+10.7) | --- |  | -71% |  |
| A40 NEW3 skip | 10266 | +58% | +23% | +49% | +58% | +58% | +71% | +18% | -1% | +0.0 (+10.9) | -7.9 (+10.7) | --- | +43% | -71% |  |


**On D7 v1.3** (the profit side already removes part of the Sept drawdown: base F9 maxDD 127.8k -> 94.1k): 19 of 152 v1.3 cells still cut the Feb-Oct maxDD by >= 20%; every one of the 8 v1.2 finalists shrinks (TVP developing LVN D40 half -31% -> -5%). The v1.3 placebo means (4 draws per kind) are around zero to slightly negative for the finalists: random halves/skips of the same volume cut as much or more in most cases. Sensitivity: see the D table; ONE-WEEK labels are in the v1.3 table. Reading: **no tape zone is a drawdown lead on the robustness standard; the information content of order-flow lines for the drawdown is the same as a volume cut.**

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
