# DS3 ZONES-3 PROFILE-LINE VARIANT SWEEP (BASE-4, re-run on V13Z: ordering fixed + basis N), 2026-11-02T12:20Z

Episodes lookup (carrying weeks of the base): autopilot/DS3_ZONES_EPISODES_V13Y.md.

Scope (user A item): swing strength 2 (base) / 3, profile bin 1 / 2 / 4 ticks (0.25 / 0.5 / 1.0 pt), anchor shifts (leg ends at confirmation = endconf; leg starts one bar earlier = startm1), session-anchored (previous completed Asia / London / RTH session) VAH / VAL / POC; lines VAH15s, LVN1_1hs, HVN0_1hs and variants = 27 POI streams (the 3 originals + 15 swing variants + 9 session). Streams rebuilt by code/d7base/build_prf3.py (Z1 build_prf2.py recipe unchanged; features TIE to Z1 prf2_ahead.pkl at max abs diff 0.0; ds3_base4/prf3/streams/*.parquet in POI format ek/dr/lo/hi/end/cap). ek-causal audit (100 random rows per stream, audit100.csv): leg tape ends strictly before the knowable second (tk) in 100/100 rows for every stream; the level is a function of tape[a:b] only (by construction) and the stream index ek = first path second >= tk.

Scoring: AHEAD fresh (nearest fresh row between entry and target) at D 20 / 40 pts and 25% / 50% of the target distance (f25 / f50), skip or HALF, marginal-in-set on the shipped V13X layer (extra_skip / extra_mult on top of HALF D20 + OTE-62 B73), 432 engine runs per lock frame pair. HEADLINE lock = NONE (per-book locks only); 12R beside. Cut = maxDD cut vs the shipped base in the same frame (positive = shallower). Noise-band rule (DS3_ZONES_3_NOISE.md, V13X band tables by frame, flip type matched to the rows changed): a cut counts only if it exceeds the band in L6M AND in PRE or X'. Post-hoc; no PASS.

## LOCK NONE (headline): 288 cells scored, 0 pass the noise-band rule, 35 have a positive cut in L6M, HOLD, PRE and X' together

Top 12 by min(L6M cut / band, best of PRE / X' cut / band):
| stream | setting | action | rows | F9 | L3M | L6M | HOLD | MID | PRE | X' | mean d L6M $k/wk (MDE) | noise-band rule |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| VAH15s_endconf | D20 | skip | 2456 | +14% | +10% | +14% | +14% | -24% | -8% | +21% | +1.1(3.4) | - |
| VAH15s_endconf | D40 | skip | 3756 | +13% | +11% | +13% | +13% | -43% | -4% | +27% | -0.1(4.7) | - |
| SESS_asia_vah | D40 | skip | 2000 | +11% | -7% | +11% | +11% | +12% | +12% | +14% | -0.1(3.0) | - |
| LVN1_15m_w2 | D40 | half | 1936 | +12% | -4% | +12% | +12% | -4% | +14% | +3% | +1.4(2.6) | - |
| VAH15s_endconf | f50 | skip | 2995 | +11% | +7% | +11% | +11% | -41% | -10% | +31% | +0.7(4.0) | - |
| SESS_asia_val | D40 | skip | 1600 | +10% | -7% | +10% | +10% | +5% | -4% | +23% | +1.1(2.8) | - |
| SESS_rth_val | D40 | skip | 1482 | +10% | +24% | +10% | +10% | +0% | +18% | -68% | +0.3(2.2) | - |
| SESS_asia_val | f50 | skip | 1092 | +10% | -3% | +10% | +10% | +5% | +2% | +18% | +0.7(2.5) | - |
| VAH15s_endconf | D20 | half | 2456 | +9% | +1% | +9% | +9% | -22% | +2% | +18% | +0.7(2.4) | - |
| SESS_rth_val | f25 | skip | 335 | +5% | +11% | +5% | +5% | +0% | +6% | -23% | +0.3(0.9) | - |
| VAH15s_endconf | D40 | half | 3756 | +9% | -1% | +9% | +9% | -38% | +9% | +23% | -0.0(2.7) | - |
| VAH15s_endconf | f50 | half | 2995 | +9% | +0% | +9% | +9% | -38% | +6% | +24% | +0.3(2.6) | - |

## 12R combined lock: 288 cells scored, 0 pass the noise-band rule, 30 have a positive cut in L6M, HOLD, PRE and X' together

Top 12 by min(L6M cut / band, best of PRE / X' cut / band):
| stream | setting | action | rows | F9 | L3M | L6M | HOLD | MID | PRE | X' | mean d L6M $k/wk (MDE) | noise-band rule |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LVN1_15m_w2 | D40 | skip | 1936 | +27% | +7% | +27% | -3% | -7% | +20% | -19% | +2.5(3.6) | - |
| VAH_1hs_w2 | f50 | skip | 3280 | +22% | -9% | +22% | +9% | +2% | +9% | +26% | +3.8(5.2) | - |
| HVN0_1hs_startm1 | D20 | skip | 1975 | +13% | +17% | +13% | +7% | -5% | +15% | -5% | +1.6(2.0) | - |
| LVN1_1hs_w3 | f50 | half | 1900 | +13% | +14% | +13% | +2% | +2% | +21% | +10% | +0.5(1.2) | - |
| POC15s_w2 | f50 | skip | 2023 | +11% | +14% | +11% | +3% | +13% | +19% | -2% | +0.2(1.8) | - |
| LVN1_15m_w2 | D20 | skip | 1095 | +11% | +13% | +11% | -2% | -8% | +16% | +1% | +1.5(2.1) | - |
| SESS_rth_val | D40 | skip | 1482 | +12% | +27% | +12% | -4% | -4% | +8% | -12% | +0.2(1.9) | - |
| POC15s_w2 | D40 | skip | 2633 | +11% | +12% | +11% | +8% | +21% | +19% | -7% | +0.4(1.8) | - |
| LVN1_15m_w2 | f50 | skip | 1438 | +10% | +10% | +10% | -1% | -4% | +19% | -20% | +1.7(2.3) | - |
| LVN1_1hs_endconf | f50 | skip | 2308 | +10% | +9% | +10% | +4% | +5% | +11% | +2% | +0.5(2.2) | - |
| POC15s_w2 | D20 | skip | 1619 | +9% | +15% | +9% | +8% | +23% | +16% | -10% | -0.0(1.7) | - |
| HVN0_1hs_startm1 | f25 | skip | 1291 | +9% | +8% | +9% | +2% | -0% | +18% | -5% | +1.1(1.6) | - |


## Survivors (lock none, pass the noise-band rule): none


## Per book and per session (delta mean $k/wk with paired MDE, own-series maxDD cut) for the 3 closest cells, lock none, and the carrying week
| cell | window | cut by | detail |
|---|---|---|---|
| VAH15s_endconf|D20|skip | L6M | book | K7 -0.3(1.0) -8%; P7 +1.6(2.9) +13%; U7 -0.1(0.1) -3%; H7 +0.2(0.5) +1%; M7 -0.3(0.8) -22%; A6 +0.0(0.0) -0% |
| VAH15s_endconf|D20|skip | L6M | session | asia +0.5(1.4) +13%; london +0.7(2.9) +17%; nyam -0.1(0.7) +10%; nypm +0.0(0.3) +2% |
| VAH15s_endconf|D20|skip | PRE | book | K7 +0.1(0.8) -32%; P7 -0.7(1.9) -1%; U7 +0.0(0.1) -1%; H7 -0.1(0.4) -11%; M7 +0.0(0.2) -0%; A6 -0.0(0.1) +0% |
| VAH15s_endconf|D20|skip | PRE | session | asia -0.7(1.9) +4%; london +0.4(0.8) +7%; nyam -0.1(1.0) -2%; nypm -0.1(0.4) -33% |
| VAH15s_endconf|D20|skip | L6M | carrying week | base trough ISO 202634 depth 182.8k -> cell trough ISO 202637 depth 157.5k |
| VAH15s_endconf|D40|skip | L6M | book | K7 -0.0(1.2) +10%; P7 +0.2(3.6) +10%; U7 -0.1(0.1) -3%; H7 +0.2(0.8) -3%; M7 -0.4(1.0) -27%; A6 +0.0(0.0) -0% |
| VAH15s_endconf|D40|skip | L6M | session | asia +0.5(1.6) +14%; london -0.6(3.4) +12%; nyam -0.3(0.7) -19%; nypm +0.3(0.5) +16% |
| VAH15s_endconf|D40|skip | PRE | book | K7 +0.2(0.9) -38%; P7 -0.4(1.8) +8%; U7 +0.0(0.1) +2%; H7 -0.5(0.7) -33%; M7 +0.0(0.2) +3%; A6 -0.0(0.1) +0% |
| VAH15s_endconf|D40|skip | PRE | session | asia -0.9(2.2) +7%; london +0.3(0.9) +6%; nyam +0.0(1.1) +5%; nypm -0.1(0.4) -35% |
| VAH15s_endconf|D40|skip | L6M | carrying week | base trough ISO 202634 depth 182.8k -> cell trough ISO 202637 depth 158.9k |
| SESS_asia_vah|D40|skip | L6M | book | K7 -0.5(0.9) -10%; P7 +0.1(2.1) +11%; U7 +0.1(1.1) +8%; H7 +0.0(0.0) +0%; M7 +0.2(0.9) +16%; A6 +0.0(0.0) +0% |
| SESS_asia_vah|D40|skip | L6M | session | asia -0.1(0.3) -3%; london -0.0(2.9) +10%; nyam +0.1(0.7) +27%; nypm -0.1(0.4) -8% |
| SESS_asia_vah|D40|skip | PRE | book | K7 +0.0(0.3) -2%; P7 +0.3(0.9) -2%; U7 -0.2(0.5) +12%; H7 -0.0(0.1) -4%; M7 +0.2(0.3) +11%; A6 -0.1(0.2) +0% |
| SESS_asia_vah|D40|skip | PRE | session | asia -0.1(0.3) +0%; london +0.5(1.3) +6%; nyam -0.0(0.6) +0%; nypm -0.1(0.2) -9% |
| SESS_asia_vah|D40|skip | L6M | carrying week | base trough ISO 202634 depth 182.8k -> cell trough ISO 202634 depth 161.8k |


Placebos (100 draws x 3 kinds): not run - they are for survivors only and no cell passes the noise-band rule in either lock frame. Noise-band source: out/zones3/s3_v13x/noise_band_off.csv / noise_band_lock12.csv (V13X), flip type matched to the number of rows changed (<=200 flip 0.5, <=400 flip 1, <=900 flip 2, else flip 5).


## Verdict
Scored 36 streams x 4 settings x 2 actions x 2 lock frames = 576 cells (288 lock none, 288 12R): profile lines: DEAD on every variant

profile lines: DEAD on every variant