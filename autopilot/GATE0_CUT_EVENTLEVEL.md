# GATE0_CUT_EVENTLEVEL (ZL-3) - PRE-PROOF, post-hoc, frozen live file only. NO PASS CLAIM. Gate 0 NOT passed. No gate0 JSON promoted, A-G not launched.
2026-11-07. Task: rebuild the live loss-cut evaluator on the raw NQZ6 mbp-10 EVENT stream (10 files, 135,325,221 records, 2,316,491 T records), 10-level feed (the 20-level explanation is withdrawn), and re-run Gate 0. Overridden/extended by T-REPLICA (acceptance: all 92 live cuts within +-2 s, no cut live did not make, residuals by trade with features). RESULT: NOT MET. Evaluator reproduces 46-47 of 92 cuts in the STRICT window (+-2 s around trigger+~1 s), 56 with the 1-s throttle phase freed; 9-10 held trades cut by the sim.
Code (l2vast/ds3/code/replica/): zl3_extract.py 2c30eb06 (records -> per-T table: book on the T record, book at packet end F_LAST, ts_recv/ts_event/sequence), zl3_stream.py (DS7.cs L2OnDepthSnapshot/L2ThSnapshot/L2OnPrint/DepthLive port + conventions), zl3_cutscore.py (ManageThL2 loss branch + ManagePolicy loss line; scoring), zl3_extract_lag.py, zl3_stream_rec.py, zl3_conflate.py (addenda A-C), zl3_feasible.py, zl3_resid.py, zl3_explain.py, zl3_gates.py. DS7.cs sha 54697597 (read, not inferred), frozen file sha 424c68da. Prereg l2vast/ds3/prereg/ZL3_prereg.md (sha in DECISIONS.md, logged BEFORE any alternative was scored; Addendum A logged before lagged variants were scored, post-hoc motivated). Bulk /mnt/l2/l2vast/_zl3/. Seal: ds3_all_ea/manifest_after.json sha 759f2258... identical before/after; only /mnt/l2/l2vast/_zl3/ written; engine runs read the same inputs as BASE-10 (ds3_g2_blind SS/SC read-only).

## 1. What was built (and checked)
- Per T record: ts_recv, ts_event, sequence, price, size, aggressor, the 10-level book ON the T record, the 10-level book at the end of the exchange packet (first following record with F_LAST=128), time of the last non-trade record (DepthLive). Facts verified on the data: T records have flags=0 and carry the PRE-trade book (the C/M records that apply the trade follow, F_LAST on the last one); 12.5% of T records share the previous record's sequence (sweeps: one T per price level); 1.2% are mergeable same (ts_event, price, side); ts_recv - ts_event median 0.28 ms; every T is at the pre-trade best bid or ask (0 between); mbp-10 A/C/M sizes are per-order (1-lot granularity).
- Literal port: snapshot at every print with >=5 levels/side; traded = prints (sgn != 0 from the pre-trade best) with time >= the previous snapshot's time at the exact price (the code's `ticks >= t0` includes the previous print and the current one); cancelled = max(0, dec - traded) per side, vanished-inside-best = 0, beyond best ignored; MedLevel EWMA 0.001 seeded at the first snapshot; pulledLog rows from the 2nd snapshot; PulledSupport own side, rows >= now-5 s including the current row; panel -unreal>=30, pulled>=30 MedLevel, now-AdvExtTime<=5 s, own 1-s throttle set only when DepthLive; policy loss line pct<=-0.50 of stop (O7 20 pt), secs_ext<=5, own 1-s throttle from Mon 08:20 ET; panel first then policy per print.
- Regression: convention S0P0C0G0 (book on the T record, one print per T, ts_recv, unique stamp per Last callback) reproduces the ZL-2 stream bit-identically (cb/ca/med max diff 0) and the engine r11 trade for trade (197 trades, +48,893; gates .707/.530/.347(.456)/.274).
- Alignment check (new): for every live exit the exact exit price prints inside the live exit second [L, L+1) in ts_recv time for 85/86 Targets, 53/53 ThL2Cut, 39/39 PolicyCut, 2/2 Stop, 7/7 other. The live clock and the owned stream agree to the second, so a clock offset is not the residual cause.

## 2. Pre-registered conventions (24, full factorial) - they do NOT explain the residual
S book snapshot (0 on the T record / 1 at packet end), P print (0 per T / 1 merge same ts_event,price,side), C clock (ts_recv / ts_event), G Globals.Now granularity (0 unique per callback / 1 ms / 15.625 ms). Window: STRICT = live exit second minus sim trigger in [-1,+3] s (trigger + ~1 s latency within +-2 s); ZL2 window [-1,+10].
| alt | MATCH strict | SIM_EARLY | MISS | FALSE_POS | MATCH ZL2 window |
|--|--|--|--|--|--|
| S0P0C0G0 | 46 | 29 | 17 | 10 | 51 |
| S0P0C0G1 | 46 | 26 | 20 | 9 | 52 |
| S0P0C0G2 | 47 | 26 | 19 | 9 | 53 |
| S0P0C1G0 | 46 | 29 | 17 | 10 | 51 |
| S0P0C1G1 | 47 | 25 | 20 | 9 | 53 |
| S0P0C1G2 | 47 | 26 | 19 | 9 | 53 |
| S0P1C0G0 | 46 | 29 | 17 | 10 | 51 |
| S0P1C0G1 | 46 | 26 | 20 | 9 | 52 |
| S0P1C0G2 | 47 | 26 | 19 | 9 | 53 |
| S0P1C1G0 | 46 | 29 | 17 | 10 | 51 |
| S0P1C1G1 | 47 | 25 | 20 | 9 | 53 |
| S0P1C1G2 | 47 | 26 | 19 | 9 | 53 |
| S1P0C0G0 | 45 | 33 | 14 | 10 | 52 |
| S1P0C0G1 | 45 | 33 | 14 | 10 | 52 |
| S1P0C0G2 | 45 | 34 | 13 | 10 | 52 |
| S1P0C1G0 | 45 | 33 | 14 | 10 | 52 |
| S1P0C1G1 | 46 | 32 | 14 | 10 | 53 |
| S1P0C1G2 | 45 | 34 | 13 | 10 | 52 |
| S1P1C0G0 | 45 | 32 | 15 | 10 | 52 |
| S1P1C0G1 | 45 | 32 | 15 | 10 | 52 |
| S1P1C0G2 | 45 | 33 | 14 | 10 | 52 |
| S1P1C1G0 | 45 | 32 | 15 | 10 | 52 |
| S1P1C1G1 | 46 | 31 | 15 | 10 | 53 |
| S1P1C1G2 | 45 | 33 | 14 | 10 | 52 |
Selection rule (fixed beforehand): max STRICT MATCH, ties min errors, then S,P,C,G order -> **S0P0C0G2** (47 MATCH, 26 EARLY, 19 MISS, 9 FALSE_POS). The spread across all 24 is 45-47: no convention separates; the winner is a tie-break, not evidence for a 15.6 ms clock. Packet-end snapshots (S1) trade 5 MISS for 7 EARLY. Clock choice and print merging change <=1 trade. 
Addendum A (depth-vs-Last skew 50/100/250/500 ms; post-hoc motivated, pre-registered before scoring): MATCH 49/47/46/48. Addendum C (Last conflation 10/50/100/250/1000 ms): 49/49/52/48/25 (best 52 at 100 ms). Addendum B (snapshot cadence = every mbp-10 record, not every print): MISS falls 17 -> 4 but SIM_EARLY rises 29 -> 44 (MATCH 44): every armed evaluation then shows pulled_mult 100-500 (label-0 median 296), no discrimination. None of the discrete conventions moves agreement above 52/92.

## 3. Fill-anchored feasibility (decision window)
f = first print at exactly the live exit price inside the live exit second. The live decision print lay in [f-2.5 s, f]. Ignoring the throttle, the sim satisfies all conditions (unreal armed, secs_ext<=5, DepthLive, pulled_mult>=30) somewhere in that window for 77 of 92 cuts (literal S0P0C0G0 stream; the 15 listed below are from that stream); the other 15 have sim pulled_mult 11.7-29.2 on every armed print of the window (live needed >=30), e.g. idx 170/171 M7/P7 Thu 03:48:37 (11.7/12.8), 14 X5 Mon 04:06:50 (14.0), 13 U7 (17.1), 105/110 K7 (21.6/21.4), 55 K7 (21.9). So per print-cadence snapshots the owned book shows too little cancelled size for these decisions. Per-record cadence on idx 170 (raw events 08:48:28-38 UTC): per-print pulled bid 23-38 contracts in the 5 s window vs 93-249 per-record, against the 90 needed (30 x MedLevel ~3.0). The cancels exist in the event stream; the live DOM saw them at the print cadence, i.e. in the live feed the snapshot/Last cadence and/or depth delivery differs from the owned T-record cadence in a way no tested convention reproduces.
Opposite direction: evaluation-level dataset (every 1-s armed evaluation with newMae, 928 evals in 185 trades outside the Tue outage; 160 in a live decision window [f-2,f], 768 before/in held trades): pulled_mult >=30 in 76% of decision evals but also in 34% of non-decision evals (label-0 median 24 vs label-1 median 46; the distributions overlap, they are not separated at 30 or at any other level). That is what 26 SIM_EARLY + 9 FALSE_POS are made of; 27 of the 34 (non-outage) carry pm 30-40 and 30 carry <50 (marginal); the large ones are idx 28 P7 (pm 121, 254 s before the live fill), 31 H7 (56, 335 s), 33 M7 (59, 515 s), 45 P7 (55, 3.3 s = within the throttle tolerance).

## 4. Engine plug and the four gates (ws11 via its stream hook; originals untouched; Tue 02:55-08:20 ET excluded; G3 10 s spec / 60 s labelled alternative)
| stream | G1 | G2 | G3 10 s | G3 60 s | G4 | trades | net | cuts (thl2/policy) |
|--|--|--|--|--|--|--|--|--|
| r11 (ZL-2 stream) | .707 F | .530 F | .347 F | .456 F | .274 F | 197 | +48,893 | 99/7 |
| ZL-3 S0P0C0G0 (literal, = r11) | .707 F | .530 F | .347 F | .456 F | .274 F | 197 | +48,893 | 99/7 |
| ZL-3 S0P0C0G2 (pre-registered winner) | .615 F | .371 F | .328 F | .391 F | .002 P* | 165 | +65,478 | 81/5 |
*G4 0.002 passes by coincidence of totals (cut dollars net), G1-G3 fail; it is not a validation: the convention that wins the 92-cut table makes the engine WORSE on G1/G2 (165 vs 187 live trades; more day-lock halts, 75 lock gates vs 36) because it removes 20 cuts. Live: 187 trades, +104,095.

## 5. Residuals (selected stream S0P0C0G2): every cut not MATCH and every held trade the sim cuts (54 of 105 scored)
Columns: live side from the frozen file (live exit unreal from exit price); sim side from the stream at its trigger print (pulled in contracts, MedLevel, pulled_mult, unreal, secs_ext; DepthLive is 1 at every trigger by construction; throttle phase: sim triggers only at throttle-passing prints, and the phase-free column gives live exit second minus the earliest print satisfying all conditions with no throttle). Live-side pulled/MedLevel/DepthLive/phase are not observable without th_eval.csv (v1.5); the live decision print satisfies pm>=30, unreal<=-arm, secs_ext<=5, DepthLive by the code.
| # | book | side | entry ET | live exit ET | live kind | live exit unreal | class | sim trig (s before live second) | sim rule | sim pulled | sim Med | sim pm | sim unreal | sim secs_ext | DepthLive | phase-free trig d | window best pm armed [f-2.5,f] | cause |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 6 | P7 | L | 11-01 20:45 | 11-01 23:02:27 | Target | 60.1 | FALSE_POS | 7345.9 | panel | 83 | 2.67 | 31.0 | -32.13 | 2.81 | 1 | 7346.9 |  | DATA (sim pm 31.0 >= 30 while live held) |
| 8 | H7 | L | 11-01 22:50 | 11-02 01:21:10 | ThL2Cut | -34.4 | MISS |  |  |  |  |  |  |  | 1 |  | 18.1 | DATA (sim best armed pm 18.1 < 30 in [f-2.5,f]; live saw >=30) |
| 9 | P7 | L | 11-01 23:03 | 11-02 01:21:10 | ThL2Cut | -35.2 | MISS |  |  |  |  |  |  |  | 1 |  | 18.1 | DATA (sim best armed pm 18.1 < 30 in [f-2.5,f]; live saw >=30) |
| 13 | U7 | S | 11-02 02:40 | 11-02 03:01:49 | ThL2Cut | -32.5 | MISS |  |  |  |  |  |  |  | 1 |  | 15.2 | DATA (sim best armed pm 15.2 < 30 in [f-2.5,f]; live saw >=30) |
| 14 | X5 | S | 11-02 04:00 | 11-02 04:06:50 | ThL2Cut | -35.2 | SIM_EARLY | 11.4 | panel | 100 | 2.35 | 42.6 | -30.50 | 0.00 | 1 | 11.4 | 12.3 | DATA (sim pm 42.6 >= 30 at 11 s before live fill; live pm < 30 then) |
| 15 | M7 | S | 11-02 02:35 | 11-02 04:18:39 | ThL2Cut | -40.6 | SIM_EARLY | 169.2 | panel | 71 | 2.33 | 30.5 | -32.08 | 0.08 | 1 | 169.2 | 41.7 | DATA (sim pm 30.5 >= 30 at 169 s before live fill; live pm < 30 then) |
| 16 | P7 | S | 11-02 03:23 | 11-02 04:18:39 | ThL2Cut | -51.4 | SIM_EARLY | 2318.1 | panel | 79 | 2.40 | 32.9 | -30.62 | 0.08 | 1 | 2318.2 | 41.7 | DATA (sim pm 32.9 >= 30 at 2318 s before live fill; live pm < 30 then) |
| 17 | X4 | L | 11-02 04:39 | 11-02 07:06:08 | ThL2Cut | -44.4 | SIM_EARLY | 487.9 | panel | 90 | 2.87 | 31.3 | -31.38 | 0.00 | 1 | 487.9 | 25.9 | DATA (sim pm 31.3 >= 30 at 488 s before live fill; live pm < 30 then) |
| 22 | X3 | S | 11-02 08:31 | 11-02 08:36:46 | PolicyCut | -42.2 | SIM_EARLY | 15.1 | panel | 87 | 2.67 | 32.6 | -30.25 | 0.36 | 1 | 15.5 | 77.0 | DATA (sim pm 32.6 >= 30 at 15 s before live fill; live pm < 30 then) |
| 28 | P7 | S | 11-02 10:02 | 11-02 10:09:42 | PolicyCut | -35.9 | SIM_EARLY | 253.8 | panel | 330 | 2.73 | 120.8 | -31.19 | 0.02 | 1 | 254.1 | 123.7 | DATA (sim pm 120.8 >= 30 at 254 s before live fill; live pm < 30 then) |
| 31 | H7 | L | 11-02 10:25 | 11-02 10:38:19 | PolicyCut | -30.0 | SIM_EARLY | 335.1 | panel | 233 | 4.13 | 56.4 | -30.25 | 0.34 | 1 | 346.4 | 49.2 | DATA (sim pm 56.4 >= 30 at 335 s before live fill; live pm < 30 then) |
| 33 | M7 | L | 11-02 10:22 | 11-02 10:47:27 | ThL2Cut | -35.8 | SIM_EARLY | 515.2 | panel | 201 | 3.41 | 59.0 | -30.00 | 0.17 | 1 | 515.3 | 77.9 | DATA (sim pm 59.0 >= 30 at 515 s before live fill; live pm < 30 then) |
| 45 | P7 | S | 11-02 18:47 | 11-02 20:29:16 | PolicyCut | -30.1 | SIM_EARLY | 3.3 | panel | 114 | 2.07 | 55.0 | -30.87 | 0.23 | 1 | 3.9 | 64.4 | THROTTLE-PHASE (phase-free trigger within window) |
| 47 | K7 | L | 11-02 20:09 | 11-02 22:36:58 | PolicyCut | -40.2 | SIM_EARLY | 8724.5 | panel | 68 | 2.12 | 32.0 | -30.50 | 0.50 | 1 | 8726.8 | 36.5 | DATA (sim pm 32.0 >= 30 at 8725 s before live fill; live pm < 30 then) |
| 51 | A7 | S | 11-03 00:36 | 11-03 00:42:01 | ThL2Cut | -40.2 | SIM_EARLY | 12.6 | panel | 70 | 2.29 | 30.5 | -34.50 | 0.91 | 1 | 31.5 | 37.9 | DATA (sim pm 30.5 >= 30 at 13 s before live fill; live pm < 30 then) |
| 55 | K7 | L | 11-03 01:36 | 11-03 01:47:31 | ThL2Cut | -51.5 | SIM_EARLY | 115.3 | panel | 80 | 2.01 | 39.8 | -35.25 | 0.72 | 1 | 116.2 | 21.4 | DATA (sim pm 39.8 >= 30 at 115 s before live fill; live pm < 30 then) |
| 57 | M7 | S | 11-03 02:04 | 11-03 02:47:29 | Stop | -80.8 | FALSE_POS | 1089.8 | panel | 87 | 2.17 | 40.2 | -50.75 | 0.00 | 1 | 1091.5 |  | DATA (sim pm 40.2 >= 30 while live held) |
| 58 | K7 | S | 11-03 01:48 | 11-03 02:55:35 | Stop | -83.0 | FALSE_POS | 1574.7 | panel | 115 | 2.16 | 53.1 | -46.00 | 0.00 | 1 | 1575.8 |  | OUTAGE window (trade open across Tue 02:55-08:20; excluded from gates) |
| 62 | P7 | L | 11-03 10:20 | 11-03 10:23:25 | ThL2Cut | -34.4 | MISS |  |  |  |  |  |  |  | 1 | 1.8 | 103.4 | THROTTLE-PHASE/newMae (feasible in window) |
| 69 | A7 | L | 11-03 18:13 | 11-03 18:31:21 | PolicyCut | -28.2 | MISS |  |  |  |  |  |  |  | 1 |  | 27.2 | DATA (sim best armed pm 27.2 < 30 in [f-2.5,f]; live saw >=30) |
| 73 | K7 | S | 11-03 18:57 | 11-03 19:04:10 | PolicyCut | -43.5 | MISS |  |  |  |  |  |  |  | 1 | 15.5 | 22.8 | DATA (sim best armed pm 22.8 < 30 in [f-2.5,f]; live saw >=30) |
| 74 | P7 | S | 11-03 18:56 | 11-03 19:04:10 | PolicyCut | -35.2 | MISS |  |  |  |  |  |  |  | 1 |  | 22.8 | DATA (sim best armed pm 22.8 < 30 in [f-2.5,f]; live saw >=30) |
| 76 | P7 | S | 11-03 20:03 | 11-03 20:03:27 | ThL2Cut | -30.4 | MISS |  |  |  |  |  |  |  | 1 | 0.4 | 88.4 | THROTTLE-PHASE/newMae (feasible in window) |
| 82 | A7 | S | 11-03 20:40 | 11-03 20:41:30 | PolicyCut | -42.5 | SIM_EARLY | 7.1 | panel | 59 | 1.86 | 31.6 | -30.25 | 0.00 | 1 | 7.1 | 44.6 | DATA (sim pm 31.6 >= 30 at 7 s before live fill; live pm < 30 then) |
| 91 | P7 | S | 11-03 22:15 | 11-03 22:16:23 | ThL2Cut | -30.6 | SIM_EARLY | 18.0 | panel | 59 | 1.71 | 34.5 | -30.81 | 1.86 | 1 | 20.6 | 25.7 | DATA (sim pm 34.5 >= 30 at 18 s before live fill; live pm < 30 then) |
| 94 | P7 | S | 11-03 23:07 | 11-03 23:09:26 | PolicyCut | -34.1 | SIM_EARLY | 11.2 | panel | 61 | 1.72 | 35.5 | -31.37 | 0.00 | 1 | 11.7 | 25.5 | DATA (sim pm 35.5 >= 30 at 11 s before live fill; live pm < 30 then) |
| 102 | A7 | L | 11-04 00:24 | 11-04 00:27:18 | ThL2Cut | -26.0 | MISS |  |  |  |  |  |  |  | 1 | 1.5 | 39.0 | THROTTLE-PHASE/newMae (feasible in window) |
| 104 | A7 | L | 11-04 00:31 | 11-04 00:43:18 | Target | 60.0 | FALSE_POS | 615.6 | panel | 70 | 1.79 | 39.1 | -34.00 | 0.00 | 1 | 616.2 |  | DATA (sim pm 39.1 >= 30 while live held) |
| 105 | K7 | L | 11-04 01:06 | 11-04 01:19:12 | ThL2Cut | -34.1 | MISS |  |  |  |  |  |  |  | 1 |  | 20.0 | DATA (sim best armed pm 20.0 < 30 in [f-2.5,f]; live saw >=30) |
| 109 | M7 | L | 11-04 02:13 | 11-04 02:16:07 | PolicyCut | -33.0 | MISS |  |  |  |  |  |  |  | 1 | -0.3 | 76.5 | THROTTLE-PHASE/newMae (feasible in window) |
| 110 | K7 | L | 11-04 02:12 | 11-04 02:21:31 | ThL2Cut | -32.8 | MISS |  |  |  |  |  |  |  | 1 |  | 21.4 | DATA (sim best armed pm 21.4 < 30 in [f-2.5,f]; live saw >=30) |
| 116 | K7 | L | 11-04 03:36 | 11-04 04:02:07 | PolicyCut | -54.8 | SIM_EARLY | 180.5 | panel | 74 | 2.32 | 31.8 | -30.25 | 1.70 | 1 | 180.5 | 40.6 | DATA (sim pm 31.8 >= 30 at 181 s before live fill; live pm < 30 then) |
| 117 | M7 | L | 11-04 03:57 | 11-04 04:02:07 | PolicyCut | -43.8 | SIM_EARLY | 39.1 | panel | 73 | 2.26 | 32.2 | -33.00 | 0.00 | 1 | 39.1 | 40.6 | DATA (sim pm 32.2 >= 30 at 39 s before live fill; live pm < 30 then) |
| 118 | P7 | L | 11-04 03:36 | 11-04 04:02:07 | PolicyCut | -51.4 | SIM_EARLY | 60.0 | panel | 69 | 2.28 | 30.2 | -30.13 | 0.00 | 1 | 60.0 | 40.6 | DATA (sim pm 30.2 >= 30 at 60 s before live fill; live pm < 30 then) |
| 119 | K7 | S | 11-04 04:03 | 11-04 04:08:30 | ThL2Cut | -38.0 | SIM_EARLY | 14.2 | panel | 66 | 2.19 | 30.1 | -30.50 | 1.59 | 1 | 27.3 | 28.9 | DATA (sim pm 30.1 >= 30 at 14 s before live fill; live pm < 30 then) |
| 125 | K7 | L | 11-04 05:42 | 11-04 05:45:01 | ThL2Cut | -39.2 | SIM_EARLY | 5.0 | panel | 85 | 2.12 | 40.1 | -32.00 | 0.28 | 1 | 5.7 | 93.7 | DATA (sim pm 40.1 >= 30 at 5 s before live fill; live pm < 30 then) |
| 143 | K7 | L | 11-04 14:09 | 11-04 14:17:26 | ThL2Cut | -29.2 | MISS |  |  |  |  |  |  |  | 1 | 1.5 | 56.9 | THROTTLE-PHASE/newMae (feasible in window) |
| 148 | K7 | S | 11-04 19:27 | 11-04 19:30:26 | ThL2Cut | -32.5 | SIM_EARLY | 10.9 | panel | 73 | 2.35 | 31.0 | -36.00 | 0.50 | 1 | 11.4 | 23.8 | DATA (sim pm 31.0 >= 30 at 11 s before live fill; live pm < 30 then) |
| 149 | A7 | S | 11-04 19:40 | 11-04 19:44:04 | ThL2Cut | -34.2 | SIM_EARLY | 5.8 | panel | 81 | 2.19 | 36.9 | -30.00 | 3.70 | 1 | 5.8 | 26.4 | DATA (sim pm 36.9 >= 30 at 6 s before live fill; live pm < 30 then) |
| 150 | P7 | S | 11-04 19:27 | 11-04 19:57:29 | Target | 59.9 | FALSE_POS | 1633.9 | panel | 73 | 2.35 | 31.0 | -34.07 | 0.50 | 1 | 1634.4 |  | DATA (sim pm 31.0 >= 30 while live held) |
| 155 | P7 | L | 11-04 21:31 | 11-04 21:34:08 | ThL2Cut | -33.3 | SIM_EARLY | 3.9 | panel | 69 | 2.16 | 32.0 | -31.31 | 0.12 | 1 | 22.4 | 46.0 | DATA (sim pm 32.0 >= 30 at 4 s before live fill; live pm < 30 then) |
| 158 | K7 | S | 11-04 21:51 | 11-04 22:53:11 | Target | 60.0 | FALSE_POS | 2779.2 | panel | 85 | 2.14 | 39.7 | -30.50 | 0.00 | 1 | 2779.2 |  | DATA (sim pm 39.7 >= 30 while live held) |
| 162 | A7 | S | 11-05 00:52 | 11-05 01:13:43 | ThL2Cut | -44.5 | SIM_EARLY | 131.6 | panel | 74 | 2.01 | 36.7 | -33.00 | 0.00 | 1 | 785.6 | 44.5 | DATA (sim pm 36.7 >= 30 at 132 s before live fill; live pm < 30 then) |
| 163 | P7 | S | 11-05 01:34 | 11-05 01:47:21 | ThL2Cut | -45.5 | SIM_EARLY | 11.6 | panel | 61 | 2.03 | 30.1 | -35.00 | 3.62 | 1 | 20.9 | 44.6 | DATA (sim pm 30.1 >= 30 at 12 s before live fill; live pm < 30 then) |
| 166 | U7 | L | 11-05 02:10 | 11-05 02:16:10 | ThL2Cut | -33.1 | MISS |  |  |  |  |  |  |  | 1 | 5.0 | 27.6 | DATA (sim best armed pm 27.6 < 30 in [f-2.5,f]; live saw >=30) |
| 168 | P7 | L | 11-05 02:53 | 11-05 03:17:20 | Target | 59.9 | FALSE_POS | 805.1 | panel | 70 | 2.07 | 33.9 | -30.58 | 0.44 | 1 | 805.6 |  | DATA (sim pm 33.9 >= 30 while live held) |
| 169 | M7 | L | 11-05 02:53 | 11-05 03:17:20 | Target | 60.0 | FALSE_POS | 805.1 | panel | 70 | 2.07 | 33.9 | -32.00 | 0.44 | 1 | 1255.9 |  | DATA (sim pm 33.9 >= 30 while live held) |
| 170 | M7 | L | 11-05 03:41 | 11-05 03:48:37 | ThL2Cut | -32.0 | MISS |  |  |  |  |  |  |  | 1 |  | 11.7 | DATA (sim best armed pm 11.7 < 30 in [f-2.5,f]; live saw >=30) |
| 171 | P7 | L | 11-05 03:33 | 11-05 03:48:37 | ThL2Cut | -32.4 | MISS |  |  |  |  |  |  |  | 1 |  | 12.8 | DATA (sim best armed pm 12.8 < 30 in [f-2.5,f]; live saw >=30) |
| 175 | K7 | S | 11-05 04:27 | 11-05 04:35:14 | BookLock | -42.8 | FALSE_POS | 10.4 | panel | 94 | 2.59 | 36.3 | -44.25 | 0.27 | 1 | 10.6 |  | DATA (sim pm 36.3 >= 30 while live held) |
| 178 | M7 | L | 11-05 05:08 | 11-05 07:22:47 | ThL2Cut | -37.5 | SIM_EARLY | 9.3 | panel | 81 | 2.49 | 32.6 | -35.75 | 0.00 | 1 | 9.5 | 27.9 | DATA (sim pm 32.6 >= 30 at 9 s before live fill; live pm < 30 then) |
| 181 | P7 | S | 11-05 07:58 | 11-05 08:04:52 | PolicyCut | -32.1 | MISS |  |  |  |  |  |  |  | 1 | 0.1 | 52.2 | THROTTLE-PHASE/newMae (feasible in window) |
| 182 | U7 | S | 11-05 07:50 | 11-05 08:04:52 | ThL2Cut | -32.0 | MISS |  |  |  |  |  |  |  | 1 | -0.2 | 52.2 | THROTTLE-PHASE/newMae (feasible in window) |
| 183 | P7 | S | 11-05 08:09 | 11-05 08:18:12 | PolicyCut | -31.2 | MISS |  |  |  |  |  |  |  | 1 |  | 28.3 | DATA (sim best armed pm 28.3 < 30 in [f-2.5,f]; live saw >=30) |

## 6. Cause classes (concrete)
- THROTTLE-PHASE (8 trades): conditions hold in the window but the throttled sim trigger is outside +-2 s; the live chain phase (first eval after the first fill, then +1 s hops at the next print) depends on the exact live print arrival times for every hop since entry and cannot be reproduced from the owned stream (e.g. idx 76 P7 20:03:27: pm 84-100 at 20:03:26.0 and 27.1 but unreal -24/-29 and the next throttle slot 28.09 lies after the window).
- DATA, live pulled > owned per-print pulled (15 cuts): idx 170/171, 14, 13, 8/9, 55, 105/110, 17, 148, 149, 178, 91, 94 - sim best armed pulled_mult 11.7-29.2 in the exact decision window. The per-record cancel volume exists in the event stream (idx 170: 93-249 vs 90 needed) but not at print cadence.
- DATA, sim pulled > live (SIM_EARLY 26 + FALSE_POS 9): sim pm 30-40 in 27 of 34 (marginal), <50 in 30; held-to-target examples idx 6 P7 Sun 20:58, 104 A7, 150 P7, 158 K7, 168/169 P7/M7 (pm 31-40); the four pm>=50 cases are idx 28, 31, 33 (121/56/59, 254-515 s before the live fill) and 45.
- ENTRY BASIS (fill schedule): idx 62 P7 10:23:25: live exit price 28318.0 (-34.4) but the owned prints are above 28322.5 until after the live second; with the 30% add unfilled the running average is ~0.9 pt worse than the file average and unreal -29.9 would arm. The fill schedule belongs to REPLICA-ENG (ResetTh at every fill, AdvExt reset); the file carries only the final average and the first fill time.
- OUTAGE: idx 57/58 (M7/K7 stops 02:47/02:55) cut by the sim at 02:29 inside the Tue gap window; excluded from the gates by rule.

## 7. Conclusion
The literal event-level port is exact against the code and reproduces the previous ZL-2 numbers when the Last stamps are unique; no NT8 convention (snapshot timing within the packet, print merging, ts_recv vs ts_event, 1 ms / 15.6 ms Now, depth skew 50-500 ms, Last conflation 10-250 ms) lifts the 92-cut agreement above 52, the 20-level hypothesis being withdrawn. The disagreement is two-sided and tied to how much cancelled size the live DOM registered between consecutive Last events (live saw >=3x more than the owned per-print book in 15 cuts and less in about 26+9 others). Concrete candidate causes that the owned data cannot settle: (1) the live Last/snapshot cadence differs from the Databento T cadence; (2) the CQG depth delivery (position Add/Update/Remove, conflation) differs from the CME book the stream shows; (3) the live throttle chain phase; (4) the live fill schedule. A th_eval.csv from v1.5 (pulled, MedLevel, DepthLive per evaluation) is the only item that separates (1)-(3). The DS7.cs code itself was read, not inferred; no stub, no calibration factor, no injected live exit was used.
