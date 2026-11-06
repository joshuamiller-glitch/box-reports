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
