

## S1-S8 synthetic scenarios (desk_cov_synth.py)
- S1a C2 fires once, within 60 s, at an open loss of >= 1 unit: PASS (at +40s)
- S1b C2 does NOT fire on a slow loss (0.1 pt/s: 1 unit takes 100 s): PASS 
- S2a C1 cuts half once at -50% of the stop (open loss >= 20): PASS (at +199s frac 0.5)
- S2b C1 rest keeps the FULL stop (screen exit at -40 pts): PASS (exit stop at +399s)
- S2c C1 with 1 lot cannot cut half: no action (plain bracket): PASS 
- S3a B1: a third (2 of 6 lots) at +1R (40 pts = ~80 s) and a third at +2R (80 pts = ~160 s), nothing else banked: PASS [(80, 2, 'B1a'), (160, 2, 'B1b')]
- S3b B1: stop to entry right after the first third: PASS [(81, 'B1BE', 0.0)]
- S3c B1 with 2 lots: 1 lot at +1R, nothing at +2R: PASS 
- S3d B1 with 1 lot: no part, the ratchet only: PASS 
- S3e B1 with 8 lots: 2 / 2 (last third keeps the remainder: 4 runs): PASS [2, 2]
- S3f B2 takes half (frac 0.5) at the first completed minute where RSI14 is back below 80 after being >= 80 in profit (reference from the same closes): PASS (manager +1363s, reference +1363 s)
- S3g B2: stop to entry after the take: PASS 
- S3h B2 with 1 lot: stop to the larger of entry and half the peak (> 0): PASS [np.float64(5.62)]
- S3i B2 short mirror fires once with frac 0.5: PASS 
- S4a B3 takes half the first second price >= session VWAP + 2 sd (sd of 1-min closes minus VWAP since the 18:00 ET reset, completed minutes), reference loop: PASS (manager +4s, reference +4 s)
- S5a A4 exits at the first completed 1-minute close below the EMA21 once up 1 unit (reference): PASS (exit +1484s, reference +1483 s)
- S6a A5 stop levels == textbook Wilder PSAR on the same 1-minute bars (every reference level that tightened the stop appears within +-2 s and 0.25 pt): FAIL (21 manager tightens, 40 reference levels, 21 matched)
- S6b A5 exits through the SAR (screen exit type stop): PASS 
- S7a A3 last stop level == best - 3 x ATR5 (reference ATR from the same bars): PASS (manager 42.77, reference 42.77; best 59.00 ATR5 5.41)
- S7b A3 never looser than the own stop and ratchet only: PASS 
- S8a A1 stop = 2 x s5 and lots = round(6 x 40 / stop), >= 1: PASS (s5 1.95, stop 3.89, lots 62)
- S8b A2 stop <= own stop and >= 0.5 s5, lots unchanged: PASS (0.97, swing)
- S8c A2 swing rule on a hand series: last confirmed swing low = 100.5 (index 8, 2 closes each side), stop = 103 - 100.5 + 0.1 x 2: PASS (2.700)
- S8d A2 short mirror: a swing high above the entry is used: PASS (2.20 swing)

SYNTH ALL PASS: False
