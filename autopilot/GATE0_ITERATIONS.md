# GATE0_ITERATIONS (append-only; one line per gate0_check.py run; gates per GATE0_SPEC.md)
| time | label | tree/config sha | prediction sha | trades m/u | net gap | cuts m/u | cut $ gap | GATE 0 |
|---|---|---|---|---|---|---|---|---|
| 2026-11-06 18:59Z | VALID V1 sealed list | sealed_0ad2308f | pred sha b739a9aad0f8 | 0.494 F | 0.665 F | 0.180 F | 0.006 P | FAIL |
| 2026-11-06 18:59Z | VALID V2 variant allea+kfix+1s | dd11dcd834735846 | pred sha 4af884e17819 | 0.496 F | 0.484 F | 0.176 F | 0.179 F | FAIL |
| 2026-11-06 18:59Z | VALID control live-as-engine | - | pred sha 056398df8481 | 1.000 P | 0.000 P | 1.000 P | 0.000 P | PASS |
| 2026-11-06 19:06Z | I1-preview N1_lat0 (fabricated cols) | v3run:c6cf22d3|a | pred sha a8bfed80b98b | 0.500 F | 0.439 F | 0.178 F | 0.077 P | FAIL |
| 2026-11-06 19:06Z | I1-preview N1 (fabricated cols) | v3run:c6cf22d3|a | pred sha 5862c7634584 | 0.493 F | 0.461 F | 0.194 F | 0.068 P | FAIL |
| 2026-11-06 19:06Z | I1-preview N2 (fabricated cols) | v3run:c6cf22d3|a | pred sha 7ba0039ca984 | 0.504 F | 0.424 F | 0.201 F | 0.070 P | FAIL |
| 2026-11-06 19:06Z | I1-preview N3 (fabricated cols) | v3run:c6cf22d3|a | pred sha 219f97b4e7d9 | 0.483 F | 0.467 F | 0.221 F | 0.022 P | FAIL |
| 2026-11-06 19:06Z | I1-preview N5 (fabricated cols) | v3run:c6cf22d3|a | pred sha 5d98b0967d0c | 0.521 F | 0.433 F | 0.197 F | 0.088 P | FAIL |
| 2026-11-06 19:08Z | I2-preview N1 + fillsim reprice (fabricated K cols; uncalibrated stop) | v3run:c6cf22d3|r | pred sha 7b1088a93556 | 0.493 F | 0.552 F | 0.188 F | 0.137 F | FAIL |
| 2026-11-06 19:11Z | I3-preview i3_p0nopro (fabricated K cols; diagnostic) | v3run:harness2|a | pred sha d5bd23bc57da | 0.510 F | 0.362 F | 0.196 F | 0.109 F | FAIL |
| 2026-11-06 19:11Z | I3-preview i3_p0nopro_nozone (fabricated K cols; diagnostic) | v3run:harness2|a | pred sha 53679e0529ad | 0.504 F | 0.436 F | 0.192 F | 0.156 F | FAIL |
| 2026-11-06 19:15Z | WS3-a sequential sim N1 (rows from v2 engine run; preview series; no locks; uncalibrated stop) | ws3:v0 | pred sha 5ffabe82ba25 | 0.502 F | 0.334 F | 0.235 F | 0.460 F | FAIL |
| 2026-11-06 19:16Z | WS3 ws3_N2 (preview series; no locks; uncalibrated stop; fill in-sample) | ws3:v0 | pred sha e447b79e675d | 0.497 F | 0.339 F | 0.227 F | 0.472 F | FAIL |
| 2026-11-06 19:16Z | WS3 ws3_N3 (preview series; no locks; uncalibrated stop; fill in-sample) | ws3:v0 | pred sha 2bdd8457abc7 | 0.507 F | 0.286 F | 0.219 F | 0.450 F | FAIL |
| 2026-11-06 19:16Z | WS3 ws3_N5 (preview series; no locks; uncalibrated stop; fill in-sample) | ws3:v0 | pred sha 2fce0097e9b9 | 0.507 F | 0.288 F | 0.220 F | 0.469 F | FAIL |
| 2026-11-06 19:16Z | WS3 ws3_N10 (preview series; no locks; uncalibrated stop; fill in-sample) | ws3:v0 | pred sha 8e2b60de56f0 | 0.511 F | 0.377 F | 0.165 F | 0.526 F | FAIL |
| 2026-11-06 19:16Z | WS3 ws3_N1_cap10 (preview series; no locks; uncalibrated stop; fill in-sample) | ws3:v0 | pred sha dc7608418484 | 0.502 F | 0.346 F | 0.235 F | 0.460 F | FAIL |
| 2026-11-06 19:17Z | WS3 ORACLE exits from live (DIAGNOSTIC, never a pass) | ws3:v0 | pred sha 00d0048c4d8f | 0.544 F | 0.284 F | 0.466 F | 0.112 F | FAIL |
| 2026-11-06 19:19Z | WS3 ws3_noslots (P0 skip slots off diagnostics; no locks; uncalibrated stop; in-sample fills) | ws3:v0 | pred sha dd3e032a2c32 | 0.528 F | 0.455 F | 0.249 F | 0.559 F | FAIL |
| 2026-11-06 19:19Z | WS3 ws3_noslots_nope (P0 skip slots off diagnostics; no locks; uncalibrated stop; in-sample fills) | ws3:v0 | pred sha 81b925466bc3 | 0.515 F | 0.414 F | 0.246 F | 0.724 F | FAIL |
| 2026-11-06 19:19Z | WS3 ws3_noslots_nope_nozone (P0 skip slots off diagnostics; no locks; uncalibrated stop; in-sample fills) | ws3:v0 | pred sha 0d927020e61d | 0.505 F | 0.464 F | 0.236 F | 0.745 F | FAIL |
| 2026-11-06 19:22Z | I1-real-series engine v3 (kfix+all_ea+real ZL-2 series N1 lat1, K cols z/sh/ice/swp/wg/imbf zero-filled; uncalibrated stop) | v3run:ee86dc64|s | pred sha 864ebdf898d1 | 0.493 F | 0.458 F | 0.194 F | 0.068 P | FAIL |
| 2026-11-06 19:53Z | WS3 on tree v3 (MV/ST/MA unthinned, PB7 loss rows; live default rule N1; no locks; uncalibrated stop; fills in-sample) | ws3:v0|tree:v3 | pred sha 858b1666cc08 | 0.493 F | 0.264 F | 0.234 F | 0.459 F | FAIL |
| 2026-11-06 19:57Z | I-engine v3 tree v3 + real 1-s series for ALL layers (ZL-2 span files; live default rule N1 lat1; uncalibrated stop; fills = engine kernel) | v3run:harness4|t | pred sha ddb43c2e8d84 | 0.491 F | 0.483 F | 0.206 F | 0.135 F | FAIL |
| 2026-11-06 21:11Z | WS3b N1 tree v3c (+O7 book arm20 hyp, +X3/X4/X5 engine book 2 lots; live default rule; no locks; uncalibrated stop; fills in-sample) | ws3b:b8cd7be8|tr | pred sha 72da4323b71c | 0.507 F | 0.222 F | 0.244 F | 0.525 F | FAIL |
| 2026-11-06 21:11Z | WS3b N2 tree v3c (+O7 book arm20 hyp, +X3/X4/X5 engine book 2 lots; live default rule; no locks; uncalibrated stop; fills in-sample) | ws3b:b8cd7be8|tr | pred sha 53f54a2e657b | 0.500 F | 0.264 F | 0.236 F | 0.536 F | FAIL |
| 2026-11-06 21:14Z | I-engine v3c tree (kfix + real 1-s series N1 lat1; engine harness core books = v3 identical, O7/X not in harness; X rows = Z1-file P0 trades; uncalibrated stop) | v3run:engine_v3_ | pred sha bb06379a3a99 | 0.491 F | 0.483 F | 0.206 F | 0.135 F | FAIL |
| 2026-11-06 21:14Z | I-engine v3c harness core books + ws3b O7/X books (real 1-s series N1; O7 arm20 hyp; uncalibrated stop) | comb:engine_v3_r | pred sha 2faced04f649 | 0.505 F | 0.441 F | 0.217 F | 0.201 F | FAIL |
| 2026-11-06 22:11Z | REPRO V1 sealed list (frozen file) | - | pred sha b739a9aad0f8 | 0.494 F | 0.665 F | 0.180 F | 0.006 P | FAIL |
| 2026-11-06 22:11Z | REPRO V2 variant (frozen file) | - | pred sha 4af884e17819 | 0.496 F | 0.484 F | 0.176 F | 0.179 F | FAIL |
| 2026-11-06 22:11Z | REPRO control live-as-engine (frozen file) | - | pred sha 056398df8481 | 1.000 P | 0.000 P | 1.000 P | 0.000 P | PASS |
| 2026-11-06 22:11Z | RERUN of WS3b N1 on FROZEN blind-week live copy (identity check, source-path switch only) | ws3b:7797c603|tr | pred sha 72da4323b71c | 0.507 F | 0.222 F | 0.244 F | 0.525 F | FAIL |
| 2026-11-06 22:17Z | REPRO2 V1 (frozen_path) | - | pred sha b739a9aad0f8 | 0.494 F | 0.665 F | 0.180 F | 0.006 P | FAIL |
| 2026-11-06 22:17Z | REPRO2 V2 (frozen_path) | - | pred sha 4af884e17819 | 0.496 F | 0.484 F | 0.176 F | 0.179 F | FAIL |
| 2026-11-06 22:17Z | REPRO2 control (frozen_path) | - | pred sha 056398df8481 | 1.000 P | 0.000 P | 1.000 P | 0.000 P | PASS |
| 2026-11-07 00:31Z | Z1 FILL_MODEL_V4_CODE PRE-PROOF (fillv4 code-faithful fills; frozen file tie-out only; no gate0_check run) | fillsim 0c8b1ed2 | - | - | - | - | - | n/a (PRE-PROOF, no PASS claim) |
| 2026-11-07 S4a | PRE-PROOF daycaps module + harness update (outage exclusion, policy line, --excl-optional) - no gate run; see GATE0_DAYCAPS_S4A.md | live code sha 54697597 | frozen live sha 424c68da | - | - | - | - | n/a |
- 2026-11-07T00:37Z ZL-2 LIVE-EXACT CUT evaluator (raw mbp-10 per-print, PRE-PROOF, post-hoc; code l2vast/ds3/code/gate0/zl2_cut_*.py): vs frozen blind week 92 live cuts + 13 held-at-(-30): sim triggers on 75/92 live cuts (51 within 10 s of the live fill, median lag 0.6 s; 60 within 20 s), 17 misses, 10 of 13 held trades cut by sim (false pos); no PASS; details autopilot/GATE0_CUT_LIVEEXACT.md
| 2026-11-07 00:39Z | REBUILD4 r1 (HM5+locks+blackout+ZL2 live-exact cut+fillv4; PRE-PROOF; post-hoc) | ec7534f57f06 | pred sha 1cc0f4b3e6b4 | 0.631 F | 0.270 F | 0.329 F | 0.252 F | FAIL |
| 2026-11-07 00:41Z | REBUILD4 r2 (r1 + P7 NYAM live Confirm ThreeBar 45s from tape; PRE-PROOF; post-hoc) | 56a49efdfa87 | pred sha 76ae97e9c0e1 | 0.621 F | 0.070 P | 0.316 F | 0.256 F | FAIL |
| 2026-11-07 00:41Z | REBUILD4 r3 (r2 + P0 K7/P7 skip slots OFF (rows noslots); PRE-PROOF; post-hoc) | 56a49efdfa87 | pred sha 7d5bd89269f0 | 0.654 F | 0.336 F | 0.320 F | 0.369 F | FAIL |
- 2026-11-07T01:05Z BASE-4 CORRECTION: the two lines above labelled 'REBUILD4 r2' and 'REBUILD4 r3' (00:4xZ) were produced by ws4.py with a bug (the Confirm flag leaked as NaN=truthy to non-PE rows: H7/O7/X rows were sent through the P7 Confirm resolver and dropped). They are void; re-run lines follow as r2b/r3b with the fixed ws4.py. r1 is unaffected (no Confirm code in it).
| 2026-11-07 00:42Z | REBUILD4 r2b (r1 + P7 NYAM live Confirm (ThreeBar 45s, from tape); P0 slots as tree; PRE-PROOF; post-hoc) | 419e800525f2 | pred sha 423b90f85164 | 0.653 F | 0.080 P | 0.342 F | 0.291 F | FAIL |
| 2026-11-07 00:42Z | REBUILD4 r3b (r2b with P0 K7/P7 skip slots OFF (rows noslots); PRE-PROOF; post-hoc) | 419e800525f2 | pred sha 2ead4aeeed23 | 0.687 F | 0.346 F | 0.347 F | 0.403 F | FAIL |
| 2026-11-07 00:43Z | REBUILD4 ablation a_nolocks (r3b with locks OFF; PRE-PROOF; diagnostic) | 419e800525f2 | pred sha 52dff76db038 | 0.705 F | 0.298 F | 0.353 F | 0.456 F | FAIL |
| 2026-11-07 00:43Z | REBUILD4 ablation b_noblackout (r3b with U7 blackout OFF; PRE-PROOF; diagnostic) | 419e800525f2 | pred sha c93107de574f | 0.687 F | 0.346 F | 0.347 F | 0.403 F | FAIL |
| 2026-11-07 00:43Z | REBUILD4 ablation c_nohm5 (r3b with H7 on the 1-min library rows (old HM); PRE-PROOF; diagnostic) | 419e800525f2 | pred sha 41781f3a5f23 | 0.615 F | 0.205 F | 0.323 F | 0.507 F | FAIL |
| 2026-11-07 00:43Z | REBUILD4 ablation d_nocf (r3b without live Confirm (library PE rows); PRE-PROOF; diagnostic) | 419e800525f2 | pred sha 34e1347460e5 | 0.664 F | 0.536 F | 0.333 F | 0.364 F | FAIL |
| 2026-11-07 00:43Z | REBUILD4 r2b WITH optional windows excluded (Mon 14:01-18:21, Tue 13:08-18:06; unconfirmed; PRE-PROOF; post-hoc) | 419e800525f2 [excl-optional] | pred sha 423b90f85164 | 0.661 F | 0.079 P | 0.347 F | 0.282 F | FAIL |
| 2026-11-07 00:43Z | REBUILD4 r3b WITH optional windows excluded (Mon 14:01-18:21, Tue 13:08-18:06; unconfirmed; PRE-PROOF; post-hoc) | 419e800525f2 [excl-optional] | pred sha 2ead4aeeed23 | 0.696 F | 0.345 F | 0.352 F | 0.394 F | FAIL |
