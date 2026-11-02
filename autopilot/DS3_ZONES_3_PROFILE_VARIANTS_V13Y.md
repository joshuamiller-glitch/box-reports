# DS3 ZONES-3 PROFILE-LINE VARIANT SWEEP (BASE-4, re-run on V13Y: ordering fixed), 2026-11-02T10:48Z

Episodes lookup (carrying weeks of the base): autopilot/DS3_ZONES_EPISODES_V13Y.md.

Scope (user A item): swing strength 2 (base) / 3, profile bin 1 / 2 / 4 ticks (0.25 / 0.5 / 1.0 pt), anchor shifts (leg ends at confirmation = endconf; leg starts one bar earlier = startm1), session-anchored (previous completed Asia / London / RTH session) VAH / VAL / POC; lines VAH15s, LVN1_1hs, HVN0_1hs and variants = 27 POI streams (the 3 originals + 15 swing variants + 9 session). Streams rebuilt by code/d7base/build_prf3.py (Z1 build_prf2.py recipe unchanged; features TIE to Z1 prf2_ahead.pkl at max abs diff 0.0; ds3_base4/prf3/streams/*.parquet in POI format ek/dr/lo/hi/end/cap). ek-causal audit (100 random rows per stream, audit100.csv): leg tape ends strictly before the knowable second (tk) in 100/100 rows for every stream; the level is a function of tape[a:b] only (by construction) and the stream index ek = first path second >= tk.

Scoring: AHEAD fresh (nearest fresh row between entry and target) at D 20 / 40 pts and 25% / 50% of the target distance (f25 / f50), skip or HALF, marginal-in-set on the shipped V13X layer (extra_skip / extra_mult on top of HALF D20 + OTE-62 B73), 432 engine runs per lock frame pair. HEADLINE lock = NONE (per-book locks only); 12R beside. Cut = maxDD cut vs the shipped base in the same frame (positive = shallower). Noise-band rule (DS3_ZONES_3_NOISE.md, V13X band tables by frame, flip type matched to the rows changed): a cut counts only if it exceeds the band in L6M AND in PRE or X'. Post-hoc; no PASS.

## LOCK NONE (headline): 288 cells scored, 0 pass the noise-band rule, 27 have a positive cut in L6M, HOLD, PRE and X' together

Top 12 by min(L6M cut / band, best of PRE / X' cut / band):
| stream | setting | action | rows | F9 | L3M | L6M | HOLD | MID | PRE | X' | mean d L6M $k/wk (MDE) | noise-band rule |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| POC15s_w2 | f50 | skip | 2023 | +17% | +7% | +17% | -11% | -5% | +5% | +24% | +0.4(2.3) | - |
| POC15s_w2 | D40 | skip | 2633 | +16% | +7% | +16% | -9% | +3% | -0% | +24% | +0.2(2.4) | - |
| HVN0_1hs_endconf | D40 | skip | 2940 | +11% | -13% | +11% | -7% | -20% | -14% | +20% | -1.6(5.1) | - |
| PRF|vah|sw15 | D20 | skip | 1969 | +12% | +3% | +12% | -1% | -8% | +12% | +13% | -1.0(2.4) | - |
| HVN0_15m_w2 | f50 | skip | 1987 | +11% | +6% | +11% | +1% | -6% | +7% | +17% | +0.3(2.0) | - |
| VAH15s_endconf | D20 | skip | 2456 | +10% | +5% | +10% | +2% | -47% | +9% | +22% | -0.3(2.7) | - |
| HVN0_15m_w2 | D40 | skip | 2585 | +9% | +6% | +9% | +4% | +1% | +0% | +17% | +0.7(2.3) | - |
| SESS_asia_val | D40 | skip | 1600 | +9% | -2% | +9% | +6% | -11% | +4% | +18% | +0.6(2.2) | - |
| VAH15s_endconf | D40 | skip | 3756 | +9% | +3% | +9% | -9% | -82% | +4% | +22% | -1.1(3.9) | - |
| LVN1_15m_w3 | D40 | skip | 2090 | +9% | +1% | +9% | +12% | +4% | -24% | +11% | +2.4(3.1) | - |
| VAH15s_endconf | f50 | half | 2995 | +8% | -1% | +8% | +14% | -60% | +6% | +22% | -0.9(1.9) | - |
| VAH15s_endconf | D40 | half | 3756 | +8% | -1% | +8% | +14% | -60% | +3% | +22% | -1.2(2.1) | - |

## 12R combined lock: 288 cells scored, 0 pass the noise-band rule, 13 have a positive cut in L6M, HOLD, PRE and X' together

Top 12 by min(L6M cut / band, best of PRE / X' cut / band):
| stream | setting | action | rows | F9 | L3M | L6M | HOLD | MID | PRE | X' | mean d L6M $k/wk (MDE) | noise-band rule |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HVN0_15m_w3 | D40 | skip | 2589 | +10% | +1% | +10% | +3% | +28% | +40% | +35% | +1.1(2.2) | - |
| VAH_1hs_w2 | f50 | skip | 3280 | +9% | -10% | +9% | +3% | +8% | +10% | +28% | +2.9(5.5) | - |
| HVN0_1hs_endconf | f25 | skip | 999 | +8% | -22% | +9% | +8% | +7% | +30% | +5% | -0.7(2.6) | - |
| HVN0_15m_w3 | f25 | skip | 924 | +8% | -28% | +8% | +0% | +10% | -2% | +34% | +0.9(3.9) | - |
| HVN0_1hs_endconf | D20 | skip | 1468 | -5% | -22% | +6% | +8% | -6% | +28% | +5% | -0.8(3.3) | - |
| HVN0_1hs_endconf | D40 | skip | 2940 | +6% | -27% | +6% | +13% | +10% | -1% | +6% | -0.3(4.4) | - |
| HVN0_1hs_endconf | D40 | half | 2940 | +5% | -7% | +5% | +13% | +4% | -13% | +11% | -0.1(2.3) | - |
| LVN1_1hs_w3 | f50 | half | 1900 | +3% | +6% | +4% | +0% | +2% | +30% | -1% | +0.1(0.9) | - |
| VAH15s_bin2 | D20 | skip | 1973 | +3% | -1% | +3% | +3% | +8% | +4% | -4% | +0.8(4.6) | - |
| LVN1_1hs_w3 | D40 | half | 2838 | -11% | +2% | +3% | +11% | -12% | +24% | -1% | -0.6(1.3) | - |
| HVN0_15m_w3 | f50 | skip | 1946 | +3% | -26% | +3% | -0% | +10% | +21% | +34% | +0.4(2.6) | - |
| HVN0_15m_w3 | D20 | skip | 1415 | +3% | -26% | +3% | +1% | +14% | +21% | +34% | +1.1(4.2) | - |


## Survivors (lock none, pass the noise-band rule): none


## Per book and per session (delta mean $k/wk with paired MDE, own-series maxDD cut) for the 3 closest cells, lock none, and the carrying week
| cell | window | cut by | detail |
|---|---|---|---|
| POC15s_w2|f50|skip | L6M | book | K7 +0.2(1.2) -9%; P7 -0.2(1.8) +10%; U7 +0.0(0.0) +0%; H7 +0.4(0.5) +8%; M7 +0.0(0.4) -3% |
| POC15s_w2|f50|skip | L6M | session | asia +0.2(1.8) +12%; london -0.1(1.3) +15%; nyam -0.1(0.4) +21%; nypm +0.4(0.6) +21% |
| POC15s_w2|f50|skip | PRE | book | K7 +0.1(0.4) -2%; P7 +0.4(1.3) +15%; U7 +0.0(0.1) +0%; H7 -0.2(0.4) -1%; M7 +0.0(0.1) +5% |
| POC15s_w2|f50|skip | PRE | session | asia +0.0(1.4) -4%; london -0.1(0.5) -3%; nyam +0.5(0.7) +7%; nypm -0.1(0.2) -12% |
| POC15s_w2|f50|skip | L6M | carrying week | base trough ISO 202632 depth 96.2k -> cell trough ISO 202632 depth 80.1k |
| POC15s_w2|D40|skip | L6M | book | K7 +0.4(1.3) -1%; P7 -0.5(2.0) +11%; U7 +0.0(0.0) +0%; H7 +0.4(0.6) +8%; M7 -0.1(0.6) -14% |
| POC15s_w2|D40|skip | L6M | session | asia -0.0(1.9) +13%; london -0.3(1.3) +13%; nyam +0.2(0.5) +34%; nypm +0.3(0.8) +16% |
| POC15s_w2|D40|skip | PRE | book | K7 -0.1(0.5) -1%; P7 +0.2(1.3) +10%; U7 +0.0(0.1) +0%; H7 -0.3(0.5) -1%; M7 -0.0(0.1) +5% |
| POC15s_w2|D40|skip | PRE | session | asia -0.1(1.4) -4%; london -0.1(0.6) -3%; nyam +0.3(0.7) +1%; nypm -0.2(0.3) -17% |
| POC15s_w2|D40|skip | L6M | carrying week | base trough ISO 202632 depth 96.2k -> cell trough ISO 202632 depth 80.4k |
| HVN0_1hs_endconf|D40|skip | L6M | book | K7 -0.3(1.1) -7%; P7 -1.2(2.9) +10%; U7 +0.1(2.3) +7%; H7 -0.3(0.8) +7%; M7 -0.0(0.9) -15%; A6 +0.3(0.7) +30% |
| HVN0_1hs_endconf|D40|skip | L6M | session | asia -0.6(4.0) -0%; london -1.2(1.9) -28%; nyam +0.0(0.8) +13%; nypm +0.3(0.7) +16% |
| HVN0_1hs_endconf|D40|skip | PRE | book | K7 -0.1(0.9) -13%; P7 +0.3(1.7) -16%; U7 -0.4(0.7) -38%; H7 +0.1(0.6) +6%; M7 -0.4(0.3) -8%; A6 -0.0(0.3) +14% |
| HVN0_1hs_endconf|D40|skip | PRE | session | asia +0.3(2.0) +10%; london -0.5(1.0) -9%; nyam -0.2(0.7) +4%; nypm -0.2(0.5) -19% |
| HVN0_1hs_endconf|D40|skip | L6M | carrying week | base trough ISO 202632 depth 96.2k -> cell trough ISO 202637 depth 85.3k |


Placebos (100 draws x 3 kinds): not run - they are for survivors only and no cell passes the noise-band rule in either lock frame. Noise-band source: out/zones3/s3_v13x/noise_band_off.csv / noise_band_lock12.csv (V13X), flip type matched to the number of rows changed (<=200 flip 0.5, <=400 flip 1, <=900 flip 2, else flip 5).


## Verdict
Scored 36 streams x 4 settings x 2 actions x 2 lock frames = 576 cells (288 lock none, 288 12R): profile lines: DEAD on every variant

profile lines: DEAD on every variant