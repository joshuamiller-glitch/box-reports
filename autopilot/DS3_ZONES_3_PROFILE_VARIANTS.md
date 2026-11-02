# DS3 ZONES-3 PROFILE-LINE VARIANT SWEEP (BASE-4 took over from Z1), 2026-11-02T06:22Z

Episodes lookup (carrying weeks of the base): autopilot/DS3_ZONES_EPISODES.md.

Scope (user A item): swing strength 2 (base) / 3, profile bin 1 / 2 / 4 ticks (0.25 / 0.5 / 1.0 pt), anchor shifts (leg ends at confirmation = endconf; leg starts one bar earlier = startm1), session-anchored (previous completed Asia / London / RTH session) VAH / VAL / POC; lines VAH15s, LVN1_1hs, HVN0_1hs and variants = 27 POI streams (the 3 originals + 15 swing variants + 9 session). Streams rebuilt by code/d7base/build_prf3.py (Z1 build_prf2.py recipe unchanged; features TIE to Z1 prf2_ahead.pkl at max abs diff 0.0; ds3_base4/prf3/streams/*.parquet in POI format ek/dr/lo/hi/end/cap). ek-causal audit (100 random rows per stream, audit100.csv): leg tape ends strictly before the knowable second (tk) in 100/100 rows for every stream; the level is a function of tape[a:b] only (by construction) and the stream index ek = first path second >= tk.

Scoring: AHEAD fresh (nearest fresh row between entry and target) at D 20 / 40 pts and 25% / 50% of the target distance (f25 / f50), skip or HALF, marginal-in-set on the shipped V13X layer (extra_skip / extra_mult on top of HALF D20 + OTE-62 B73), 432 engine runs per lock frame pair. HEADLINE lock = NONE (per-book locks only); 12R beside. Cut = maxDD cut vs the shipped base in the same frame (positive = shallower). Noise-band rule (DS3_ZONES_3_NOISE.md, V13X band tables by frame, flip type matched to the rows changed): a cut counts only if it exceeds the band in L6M AND in PRE or X'. Post-hoc; no PASS.

## LOCK NONE (headline): 288 cells scored, 0 pass the noise-band rule, 39 have a positive cut in L6M, HOLD, PRE and X' together

Top 12 by min(L6M cut / band, best of PRE / X' cut / band):
| stream | setting | action | rows | F9 | L3M | L6M | HOLD | MID | PRE | X' | mean d L6M $k/wk (MDE) | noise-band rule |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| VAH15s_startm1 | f50 | half | 2440 | +14% | +26% | +14% | +7% | -2% | +13% | -8% | +0.6(2.1) | - |
| VAH15s_endconf | D40 | half | 3756 | +17% | +11% | +17% | +17% | -29% | +13% | +6% | -0.6(2.2) | - |
| PRF|vah|sw15 | D20 | skip | 1969 | +10% | +9% | +10% | +7% | +0% | +12% | +3% | -0.8(2.4) | - |
| SESS_rth_vah | D20 | skip | 715 | +7% | +9% | +7% | +7% | +0% | +11% | -10% | +0.1(1.6) | - |
| SESS_rth_val | f25 | skip | 335 | +6% | +14% | +6% | +6% | +0% | +7% | -20% | +0.4(1.0) | - |
| VAH_1hs_w2 | f25 | skip | 1386 | +10% | +6% | +10% | +10% | +3% | +11% | +3% | +1.4(1.5) | - |
| VAH15s_endconf | f50 | half | 2995 | +15% | +12% | +15% | +15% | -29% | +11% | +9% | -0.3(2.0) | - |
| SESS_rth_val | D20 | skip | 533 | +6% | +16% | +6% | +6% | +0% | +12% | -34% | -0.1(1.5) | - |
| HVN0_1hs_endconf | D20 | skip | 1468 | +9% | -8% | +9% | +9% | -8% | +3% | +12% | -0.7(3.7) | - |
| PRF|vah|sw15 | f50 | half | 2512 | +9% | +1% | +9% | +4% | -6% | +12% | +4% | -0.4(1.7) | - |
| VAH15s_endconf | f25 | half | 1743 | +11% | +11% | +11% | +11% | -18% | +9% | +3% | -0.2(1.5) | - |
| VAH15s_bin4 | f50 | half | 2515 | +8% | -2% | +8% | +5% | -9% | +12% | +5% | -0.4(1.8) | - |

## 12R combined lock: 288 cells scored, 0 pass the noise-band rule, 50 have a positive cut in L6M, HOLD, PRE and X' together

Top 12 by min(L6M cut / band, best of PRE / X' cut / band):
| stream | setting | action | rows | F9 | L3M | L6M | HOLD | MID | PRE | X' | mean d L6M $k/wk (MDE) | noise-band rule |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LVN1_15m_w2 | D40 | skip | 1936 | -7% | +6% | +24% | -3% | -7% | +20% | -26% | +1.3(2.3) | - |
| LVN1_15m_w2 | f50 | skip | 1438 | -3% | +12% | +20% | -1% | -3% | +20% | -29% | +1.3(1.8) | - |
| HVN0_1hs_endconf | D20 | skip | 1468 | +2% | +34% | +19% | +9% | +2% | +18% | +27% | +0.4(3.5) | - |
| HVN0_1hs_endconf | D40 | skip | 2940 | +14% | +19% | +19% | +20% | +14% | +1% | +31% | +0.3(4.6) | - |
| VAH15s_endconf | D40 | half | 3756 | +23% | +11% | +18% | +20% | +30% | +14% | -18% | -0.2(1.8) | - |
| HVN0_1hs_startm1 | D20 | skip | 1975 | -4% | +21% | +16% | +5% | -4% | +0% | +13% | +0.5(1.8) | - |
| HVN0_1hs_startm1 | f25 | skip | 1291 | -0% | +21% | +15% | +1% | -0% | +13% | +2% | +0.3(1.6) | - |
| LVN1_15m_w2 | D20 | skip | 1095 | -5% | +15% | +15% | -1% | -5% | +16% | -11% | +1.1(1.1) | - |
| SESS_asia_val | f25 | skip | 459 | +2% | +1% | +12% | +1% | +2% | +4% | +8% | +0.2(0.9) | - |
| SESS_asia_val | D20 | skip | 732 | +2% | +1% | +12% | +1% | +2% | +6% | +19% | +0.2(0.9) | - |
| LVN1_15m_w2 | D40 | half | 1936 | -5% | +7% | +13% | -3% | -5% | +17% | -16% | +0.6(1.0) | - |
| PRF|hvn0|sw1h | D40 | skip | 3940 | +7% | +13% | +13% | +39% | +7% | -18% | +20% | -0.7(4.5) | - |


## Survivors (lock none, pass the noise-band rule): none


## Per book and per session (delta mean $k/wk with paired MDE, own-series maxDD cut) for the 3 closest cells, lock none, and the carrying week
| cell | window | cut by | detail |
|---|---|---|---|
| VAH15s_startm1|f50|half | L6M | book | K7 -0.1(0.3) -3%; P7 +0.6(1.6) +11%; U7 +0.0(0.2) +0%; H7 +0.0(0.5) +16%; M7 -0.0(0.5) -11%; A6 +0.0(0.0) +0% |
| VAH15s_startm1|f50|half | L6M | session | asia +0.9(1.8) +22%; london -0.4(0.7) -10%; nyam +0.0(0.7) +18%; nypm +0.0(0.0) +0% |
| VAH15s_startm1|f50|half | PRE | book | K7 +0.1(0.3) +17%; P7 +0.4(1.1) +4%; U7 -0.0(0.1) +0%; H7 -0.1(0.4) +1%; M7 -0.0(0.1) +0%; A6 +0.0(0.0) +0% |
| VAH15s_startm1|f50|half | PRE | session | asia -0.2(0.9) +2%; london +0.7(0.8) +9%; nyam -0.2(0.7) -4%; nypm +0.0(0.2) +2% |
| VAH15s_startm1|f50|half | L6M | carrying week | base trough ISO 202634 depth 132.6k -> cell trough ISO 202634 depth 113.5k |
| VAH15s_endconf|D40|half | L6M | book | K7 -0.5(1.0) -5%; P7 +0.1(1.8) +9%; U7 +0.0(0.0) +0%; H7 +0.1(0.5) -3%; M7 -0.0(0.6) -11%; A6 -0.2(0.5) -26% |
| VAH15s_endconf|D40|half | L6M | session | asia -0.0(0.9) +6%; london -0.6(2.0) +4%; nyam +0.1(0.8) +14%; nypm +0.0(0.2) +1% |
| VAH15s_endconf|D40|half | PRE | book | K7 +0.1(0.3) +12%; P7 -0.1(1.2) +4%; U7 +0.0(0.0) +0%; H7 -0.3(0.5) -7%; M7 -0.0(0.2) +4%; A6 -0.0(0.1) +0% |
| VAH15s_endconf|D40|half | PRE | session | asia -0.4(1.2) +4%; london +0.3(0.6) +6%; nyam -0.3(0.8) -15%; nypm +0.0(0.2) +4% |
| VAH15s_endconf|D40|half | L6M | carrying week | base trough ISO 202634 depth 132.6k -> cell trough ISO 202634 depth 110.3k |
| PRF|vah|sw15|D20|skip | L6M | book | K7 -0.2(1.4) +7%; P7 -0.3(1.3) +3%; U7 -0.0(0.1) +0%; H7 +0.1(0.6) +5%; M7 -0.3(0.9) -10%; A6 +0.0(0.0) +0% |
| PRF|vah|sw15|D20|skip | L6M | session | asia +0.2(1.4) +10%; london -0.7(1.4) -3%; nyam -0.3(1.0) -4%; nypm -0.0(0.3) -2% |
| PRF|vah|sw15|D20|skip | PRE | book | K7 +0.3(0.7) -6%; P7 -0.5(1.6) -10%; U7 -0.1(0.1) -1%; H7 +0.1(0.4) -1%; M7 +0.1(0.2) +1%; A6 +0.0(0.1) +0% |
| PRF|vah|sw15|D20|skip | PRE | session | asia -0.6(1.5) +7%; london +0.2(0.7) +4%; nyam +0.3(1.1) -3%; nypm -0.0(0.4) -13% |
| PRF|vah|sw15|D20|skip | L6M | carrying week | base trough ISO 202634 depth 132.6k -> cell trough ISO 202634 depth 119.2k |


Placebos (100 draws x 3 kinds): not run - they are for survivors only and no cell passes the noise-band rule in either lock frame. Noise-band source: out/zones3/s3_v13x/noise_band_off.csv / noise_band_lock12.csv (V13X), flip type matched to the number of rows changed (<=200 flip 0.5, <=400 flip 1, <=900 flip 2, else flip 5).


## Verdict
Scored 36 streams x 4 settings x 2 actions x 2 lock frames = 576 cells (288 lock none, 288 12R): profile lines: DEAD on every variant

profile lines: DEAD on every variant