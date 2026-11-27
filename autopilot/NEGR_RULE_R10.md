# NEGATIVE-R management rule R_10 (W-PLAN-AS): leave if best excursion < +5 pts 10 min after entry and under water; quick screen on the same race, server C
### AS: +10 target, safety stop S, rule R_N = leave if best excursion < +5 pts N minutes after entry and under water (N=10 fixed in advance). 1 lot, fee 0.24 pt, market exit slip 0.25, stop slip 0.25 (pessimistic +0.85); all events independent (no slot), exits at the bell
--- stop -60, normal fills
plain (no management)              n  18677 EV/trade $ +1.86 | win  75.9% stop  7.2% rule-exit  0.0% | avg win  +9.5 pts avg loser  -29.5 pts worst  -64.0
R_10 (N=10 min, fixed rule)        n  18677 EV/trade $ -7.63 | win  51.7% stop  2.9% rule-exit 42.7% | avg win  +9.4 pts avg loser  -10.8 pts worst  -64.0
null: same count random exits      n  18677 EV/trade $ -1.92 | win  67.2% stop  5.3% rule-exit 17.4% | avg win  +9.4 pts avg loser  -19.6 pts worst  -64.0
  sensitivity N=5 (not chosen)     n  18677 EV/trade $ -8.94 | win  44.2% stop  2.3% rule-exit 52.7% | avg win  +9.2 pts avg loser   -8.1 pts worst  -64.0
  sensitivity N=15 (not chosen)    n  18677 EV/trade $ -6.21 | win  56.0% stop  3.3% rule-exit 36.8% | avg win  +9.4 pts avg loser  -12.7 pts worst  -64.0
  sensitivity N=20 (not chosen)    n  18677 EV/trade $ -5.56 | win  59.1% stop  3.7% rule-exit 32.2% | avg win  +9.4 pts avg loser  -14.4 pts worst  -64.0
  sensitivity N=30 (not chosen)    n  18677 EV/trade $ -3.15 | win  63.3% stop  4.2% rule-exit 26.2% | avg win  +9.5 pts avg loser  -16.8 pts worst  -64.0
   2023  plain EV $ +1.05 | R_10 EV $-11.63 (stops 2.0% -> 0.4%) | null EV $ -5.34
   2024  plain EV $ -4.13 | R_10 EV $ -8.97 (stops 5.4% -> 1.4%) | null EV $ -4.44
   2025  plain EV $ +3.94 | R_10 EV $-10.13 (stops 8.2% -> 3.3%) | null EV $ -2.57
   2026  plain EV $ +6.16 | R_10 EV $ -0.81 (stops 11.8% -> 5.8%) | null EV $ +3.69
   L6M   plain EV $ +8.56 | R_10 EV $ +2.11 (stops 12.2% -> 6.2%) | null EV $ +6.89
   L3M   plain EV $+10.84 | R_10 EV $ -6.80 (stops 12.1% -> 5.7%) | null EV $+11.42
   book MF1   plain EV $ -2.62 win 73.5% | R_10 EV $-11.22 win 46.1% rule-exit 48.8% | null EV $ -6.04
   book MF2   plain EV $+25.70 win 82.1% | R_10 EV $ +3.08 win 61.8% rule-exit 33.0% | null EV $+11.99
   book MF3   plain EV $ +2.87 win 80.0% | R_10 EV $ -5.16 win 60.6% rule-exit 32.7% | null EV $ -0.50
   book MF4   plain EV $+18.64 win 75.2% | R_10 EV $ +3.92 win 53.5% rule-exit 39.9% | null EV $+16.02
--- stop -60, PESSIMISTIC fills
plain (no management)              n  18677 EV/trade $ +0.63 | win  75.9% stop  7.2% rule-exit  0.0% | avg win  +9.5 pts avg loser  -29.8 pts worst  -64.8
R_10 (N=10 min, fixed rule)        n  18677 EV/trade $ -8.13 | win  51.7% stop  2.9% rule-exit 42.7% | avg win  +9.4 pts avg loser  -10.8 pts worst  -64.8
null: same count random exits      n  18677 EV/trade $ -1.91 | win  67.1% stop  5.1% rule-exit 17.3% | avg win  +9.4 pts avg loser  -19.5 pts worst  -64.8
--- stop -90, normal fills
plain (no management)              n  18677 EV/trade $ -1.30 | win  77.1% stop  3.8% rule-exit  0.0% | avg win  +9.5 pts avg loser  -32.1 pts worst -120.7
R_10 (N=10 min, fixed rule)        n  18677 EV/trade $ -8.32 | win  52.1% stop  1.4% rule-exit 43.1% | avg win  +9.4 pts avg loser  -11.0 pts worst -120.7
null: same count random exits      n  18677 EV/trade $ -3.84 | win  67.9% stop  2.7% rule-exit 18.0% | avg win  +9.4 pts avg loser  -20.5 pts worst -120.7
  sensitivity N=5 (not chosen)     n  18677 EV/trade $-10.03 | win  44.6% stop  1.2% rule-exit 52.9% | avg win  +9.2 pts avg loser   -8.3 pts worst -120.7
  sensitivity N=15 (not chosen)    n  18677 EV/trade $ -6.86 | win  56.5% stop  1.6% rule-exit 37.3% | avg win  +9.4 pts avg loser  -13.0 pts worst -120.7
  sensitivity N=20 (not chosen)    n  18677 EV/trade $ -6.27 | win  59.6% stop  1.7% rule-exit 32.9% | avg win  +9.5 pts avg loser  -14.7 pts worst -120.7
  sensitivity N=30 (not chosen)    n  18677 EV/trade $ -3.79 | win  63.9% stop  2.0% rule-exit 27.0% | avg win  +9.5 pts avg loser  -17.3 pts worst -120.7
   2023  plain EV $ +2.32 | R_10 EV $-11.95 (stops 0.4% -> 0.1%) | null EV $ -1.94
   2024  plain EV $ -7.19 | R_10 EV $ -8.72 (stops 2.2% -> 0.5%) | null EV $ -8.98
   2025  plain EV $ +3.05 | R_10 EV $-11.61 (stops 4.1% -> 1.7%) | null EV $ -1.37
   2026  plain EV $ -2.66 | R_10 EV $ -1.83 (stops 7.5% -> 3.0%) | null EV $ -2.71
   L6M   plain EV $ +6.28 | R_10 EV $ +6.99 (stops 7.7% -> 3.1%) | null EV $ +8.39
   L3M   plain EV $+18.56 | R_10 EV $ +2.34 (stops 6.9% -> 2.7%) | null EV $+15.39
   book MF1   plain EV $ -4.47 win 74.4% | R_10 EV $-12.06 win 46.4% rule-exit 49.1% | null EV $ -6.84
   book MF2   plain EV $+15.97 win 83.4% | R_10 EV $ +1.26 win 62.4% rule-exit 33.5% | null EV $+12.20
   book MF3   plain EV $ -0.53 win 81.6% | R_10 EV $ -4.79 win 61.3% rule-exit 33.4% | null EV $ -4.43
   book MF4   plain EV $+10.10 win 75.7% | R_10 EV $ +1.01 win 53.7% rule-exit 40.3% | null EV $+12.27
--- stop -90, PESSIMISTIC fills
plain (no management)              n  18677 EV/trade $ -1.94 | win  77.1% stop  3.8% rule-exit  0.0% | avg win  +9.5 pts avg loser  -32.2 pts worst -121.6
R_10 (N=10 min, fixed rule)        n  18677 EV/trade $ -8.56 | win  52.1% stop  1.4% rule-exit 43.1% | avg win  +9.4 pts avg loser  -11.1 pts worst -121.6
null: same count random exits      n  18677 EV/trade $ -3.36 | win  67.9% stop  2.7% rule-exit 18.1% | avg win  +9.4 pts avg loser  -20.4 pts worst -121.6### NY: +10 target, safety stop S, rule R_N = leave if best excursion < +5 pts N minutes after entry and under water (N=10 fixed in advance). 1 lot, fee 0.24 pt, market exit slip 0.25, stop slip 0.25 (pessimistic +0.85); all events independent (no slot), exits at the bell
--- stop -60, normal fills
plain (no management)              n  74594 EV/trade $ -5.50 | win  83.5% stop 12.6% rule-exit  0.0% | avg win  +9.7 pts avg loser  -50.9 pts worst  -61.7
R_10 (N=10 min, fixed rule)        n  74594 EV/trade $ -6.76 | win  79.5% stop  9.6% rule-exit  8.5% | avg win  +9.7 pts avg loser  -39.4 pts worst  -61.7
null: same count random exits      n  74594 EV/trade $ -5.44 | win  83.4% stop 12.4% rule-exit  0.4% | avg win  +9.7 pts avg loser  -50.3 pts worst  -61.7
  sensitivity N=5 (not chosen)     n  74594 EV/trade $ -7.70 | win  75.6% stop  7.7% rule-exit 14.9% | avg win  +9.7 pts avg loser  -31.7 pts worst  -61.7
  sensitivity N=15 (not chosen)    n  74594 EV/trade $ -6.48 | win  81.1% stop 10.6% rule-exit  5.7% | avg win  +9.7 pts avg loser  -43.5 pts worst  -61.7
  sensitivity N=20 (not chosen)    n  74594 EV/trade $ -6.61 | win  81.9% stop 11.2% rule-exit  4.0% | avg win  +9.7 pts avg loser  -45.9 pts worst  -61.7
  sensitivity N=30 (not chosen)    n  74594 EV/trade $ -6.20 | win  82.8% stop 11.8% rule-exit  2.2% | avg win  +9.7 pts avg loser  -48.4 pts worst  -61.7
   2023  plain EV $ -3.24 | R_10 EV $ -7.17 (stops 11.4% -> 6.6%) | null EV $ -3.57
   2024  plain EV $ -6.19 | R_10 EV $ -7.36 (stops 12.3% -> 8.4%) | null EV $ -5.96
   2025  plain EV $ -8.01 | R_10 EV $ -7.15 (stops 13.0% -> 10.6%) | null EV $ -7.89
   2026  plain EV $ -3.77 | R_10 EV $ -5.23 (stops 13.5% -> 12.5%) | null EV $ -3.61
   L6M   plain EV $ +1.00 | R_10 EV $ -0.07 (stops 13.3% -> 12.3%) | null EV $ +1.10
   L3M   plain EV $ +1.61 | R_10 EV $ +2.25 (stops 12.8% -> 11.1%) | null EV $ +1.57
   book MF1   plain EV $ -8.35 win 83.6% | R_10 EV $ -8.56 win 80.0% rule-exit 7.9% | null EV $ -8.23
   book MF2   plain EV $ -6.68 win 82.6% | R_10 EV $ -7.19 win 78.2% rule-exit 9.8% | null EV $ -6.72
   book MF3   plain EV $ -1.81 win 84.4% | R_10 EV $ -1.91 win 80.3% rule-exit 8.6% | null EV $ -1.44
   book MF4   plain EV $-11.19 win 83.3% | R_10 EV $-12.20 win 79.3% rule-exit 8.5% | null EV $-10.94
   book MF5   plain EV $ -0.21 win 83.8% | R_10 EV $ -2.63 win 79.7% rule-exit 8.1% | null EV $ -0.61
   book MF6   plain EV $+13.71 win 85.1% | R_10 EV $ +9.59 win 81.1% rule-exit 7.9% | null EV $+13.28
   book MF7   plain EV $+16.10 win 82.9% | R_10 EV $ +4.17 win 75.9% rule-exit 12.8% | null EV $+16.20
   book MF8   plain EV $ -5.80 win 84.1% | R_10 EV $-12.95 win 79.5% rule-exit 8.7% | null EV $ -5.91
   book MF9   plain EV $ +4.47 win 82.9% | R_10 EV $ +0.71 win 76.6% rule-exit 12.2% | null EV $ +4.02
--- stop -60, PESSIMISTIC fills
plain (no management)              n  74594 EV/trade $ -7.64 | win  83.5% stop 12.6% rule-exit  0.0% | avg win  +9.7 pts avg loser  -51.6 pts worst  -62.6
R_10 (N=10 min, fixed rule)        n  74594 EV/trade $ -8.39 | win  79.5% stop  9.6% rule-exit  8.5% | avg win  +9.7 pts avg loser  -39.8 pts worst  -62.6
null: same count random exits      n  74594 EV/trade $ -7.78 | win  83.3% stop 12.4% rule-exit  0.5% | avg win  +9.7 pts avg loser  -50.9 pts worst  -62.6
--- stop -90, normal fills
plain (no management)              n  74594 EV/trade $ -4.09 | win  86.6% stop  7.6% rule-exit  0.0% | avg win  +9.7 pts avg loser  -64.0 pts worst  -92.7
R_10 (N=10 min, fixed rule)        n  74594 EV/trade $ -5.84 | win  81.3% stop  4.8% rule-exit 10.7% | avg win  +9.7 pts avg loser  -43.7 pts worst  -92.7
null: same count random exits      n  74594 EV/trade $ -3.93 | win  86.2% stop  7.4% rule-exit  0.9% | avg win  +9.7 pts avg loser  -62.3 pts worst  -92.7
  sensitivity N=5 (not chosen)     n  74594 EV/trade $ -7.33 | win  77.0% stop  3.9% rule-exit 16.5% | avg win  +9.7 pts avg loser  -34.2 pts worst  -92.7
  sensitivity N=15 (not chosen)    n  74594 EV/trade $ -5.52 | win  83.1% stop  5.5% rule-exit  7.8% | avg win  +9.7 pts avg loser  -49.4 pts worst  -92.7
  sensitivity N=20 (not chosen)    n  74594 EV/trade $ -5.39 | win  84.1% stop  5.9% rule-exit  6.1% | avg win  +9.7 pts avg loser  -53.0 pts worst  -92.7
  sensitivity N=30 (not chosen)    n  74594 EV/trade $ -4.96 | win  85.2% stop  6.6% rule-exit  4.0% | avg win  +9.7 pts avg loser  -57.4 pts worst  -92.7
   2023  plain EV $ -4.51 | R_10 EV $-10.45 (stops 6.2% -> 2.9%) | null EV $ -4.74
   2024  plain EV $ -7.40 | R_10 EV $ -8.11 (stops 7.3% -> 4.0%) | null EV $ -6.86
   2025  plain EV $ -5.42 | R_10 EV $ -3.53 (stops 8.0% -> 5.3%) | null EV $ -5.38
   2026  plain EV $ +1.78 | R_10 EV $ -1.71 (stops 8.7% -> 7.0%) | null EV $ +1.97
   L6M   plain EV $ +4.08 | R_10 EV $ +1.67 (stops 8.7% -> 7.2%) | null EV $ +4.28
   L3M   plain EV $+19.34 | R_10 EV $+15.42 (stops 7.3% -> 5.3%) | null EV $+19.66
   book MF1   plain EV $ -7.95 win 86.6% | R_10 EV $ -7.91 win 81.8% rule-exit 10.0% | null EV $ -8.10
   book MF2   plain EV $ -6.96 win 85.3% | R_10 EV $ -7.88 win 79.5% rule-exit 12.1% | null EV $ -6.14
   book MF3   plain EV $ -3.69 win 87.3% | R_10 EV $ -1.45 win 82.0% rule-exit 10.9% | null EV $ -3.12
   book MF4   plain EV $ -9.23 win 86.5% | R_10 EV $-10.65 win 81.2% rule-exit 10.6% | null EV $ -9.00
   book MF5   plain EV $ +0.59 win 86.7% | R_10 EV $ -1.86 win 81.3% rule-exit 10.5% | null EV $ +0.04
   book MF6   plain EV $+22.95 win 88.2% | R_10 EV $+11.08 win 82.8% rule-exit 9.6% | null EV $+23.45
   book MF7   plain EV $+26.03 win 85.3% | R_10 EV $ +9.23 win 77.2% rule-exit 14.3% | null EV $+24.81
   book MF8   plain EV $ -2.23 win 87.6% | R_10 EV $ -8.82 win 81.5% rule-exit 11.2% | null EV $ -1.06
   book MF9   plain EV $ +8.70 win 85.7% | R_10 EV $ +5.02 win 78.0% rule-exit 14.1% | null EV $ +9.36
--- stop -90, PESSIMISTIC fills
plain (no management)              n  74594 EV/trade $ -5.38 | win  86.6% stop  7.6% rule-exit  0.0% | avg win  +9.7 pts avg loser  -64.5 pts worst  -93.6
R_10 (N=10 min, fixed rule)        n  74594 EV/trade $ -6.66 | win  81.3% stop  4.8% rule-exit 10.7% | avg win  +9.7 pts avg loser  -43.9 pts worst  -93.6
null: same count random exits      n  74594 EV/trade $ -5.88 | win  86.2% stop  7.4% rule-exit  0.9% | avg win  +9.7 pts avg loser  -62.6 pts worst  -93.6### LO: +10 target, safety stop S, rule R_N = leave if best excursion < +5 pts N minutes after entry and under water (N=10 fixed in advance). 1 lot, fee 0.24 pt, market exit slip 0.25, stop slip 0.25 (pessimistic +0.85); all events independent (no slot), exits at the bell
--- stop -60, normal fills
plain (no management)              n  31594 EV/trade $ -4.01 | win  78.9% stop  9.3% rule-exit  0.0% | avg win  +9.6 pts avg loser  -36.8 pts worst  -63.2
R_10 (N=10 min, fixed rule)        n  31594 EV/trade $ -7.08 | win  62.1% stop  4.1% rule-exit 29.1% | avg win  +9.5 pts avg loser  -16.6 pts worst  -62.2
null: same count random exits      n  31594 EV/trade $ -3.40 | win  74.8% stop  7.6% rule-exit  8.0% | avg win  +9.6 pts avg loser  -29.2 pts worst  -62.2
  sensitivity N=5 (not chosen)     n  31594 EV/trade $ -8.64 | win  54.1% stop  3.3% rule-exit 39.8% | avg win  +9.5 pts avg loser  -12.1 pts worst  -62.2
  sensitivity N=15 (not chosen)    n  31594 EV/trade $ -6.27 | win  66.1% stop  4.7% rule-exit 23.4% | avg win  +9.6 pts avg loser  -19.6 pts worst  -63.2
  sensitivity N=20 (not chosen)    n  31594 EV/trade $ -5.91 | win  68.5% stop  5.2% rule-exit 19.8% | avg win  +9.6 pts avg loser  -21.8 pts worst  -63.2
  sensitivity N=30 (not chosen)    n  31594 EV/trade $ -5.21 | win  71.7% stop  5.9% rule-exit 14.8% | avg win  +9.6 pts avg loser  -25.2 pts worst  -63.2
   2023  plain EV $ -1.52 | R_10 EV $ -7.09 (stops 5.9% -> 1.6%) | null EV $ -3.24
   2024  plain EV $ -1.66 | R_10 EV $ -6.35 (stops 8.6% -> 3.3%) | null EV $ -0.06
   2025  plain EV $ -7.68 | R_10 EV $-10.79 (stops 10.6% -> 5.4%) | null EV $ -6.28
   2026  plain EV $ -5.14 | R_10 EV $ -3.08 (stops 12.5% -> 6.4%) | null EV $ -4.35
   L6M   plain EV $ -1.78 | R_10 EV $ +3.28 (stops 12.5% -> 6.2%) | null EV $ -2.07
   L3M   plain EV $ +5.81 | R_10 EV $ +7.51 (stops 12.0% -> 5.7%) | null EV $ +3.34
   book MF1   plain EV $+12.97 win 81.8% | R_10 EV $ +3.87 win 67.4% rule-exit 23.8% | null EV $+12.84
   book MF2   plain EV $ +0.26 win 81.0% | R_10 EV $ -3.98 win 65.1% rule-exit 26.9% | null EV $ +0.42
   book MF3   plain EV $ -7.55 win 77.6% | R_10 EV $ -9.53 win 60.2% rule-exit 30.7% | null EV $ -6.66
--- stop -60, PESSIMISTIC fills
plain (no management)              n  31594 EV/trade $ -5.60 | win  78.9% stop  9.3% rule-exit  0.0% | avg win  +9.6 pts avg loser  -37.2 pts worst  -64.1
R_10 (N=10 min, fixed rule)        n  31594 EV/trade $ -7.78 | win  62.1% stop  4.1% rule-exit 29.1% | avg win  +9.5 pts avg loser  -16.6 pts worst  -63.1
null: same count random exits      n  31594 EV/trade $ -5.42 | win  74.9% stop  7.7% rule-exit  7.9% | avg win  +9.6 pts avg loser  -29.7 pts worst  -64.1
--- stop -90, normal fills
plain (no management)              n  31594 EV/trade $ -5.21 | win  80.4% stop  4.8% rule-exit  0.0% | avg win  +9.6 pts avg loser  -40.6 pts worst  -96.0
R_10 (N=10 min, fixed rule)        n  31594 EV/trade $ -6.98 | win  62.7% stop  2.0% rule-exit 29.7% | avg win  +9.5 pts avg loser  -17.0 pts worst  -96.0
null: same count random exits      n  31594 EV/trade $ -5.57 | win  76.0% stop  3.9% rule-exit  8.4% | avg win  +9.6 pts avg loser  -31.4 pts worst  -96.0
  sensitivity N=5 (not chosen)     n  31594 EV/trade $ -9.12 | win  54.7% stop  1.7% rule-exit 40.1% | avg win  +9.5 pts avg loser  -12.4 pts worst  -91.2
  sensitivity N=15 (not chosen)    n  31594 EV/trade $ -6.03 | win  66.8% stop  2.2% rule-exit 24.2% | avg win  +9.6 pts avg loser  -20.2 pts worst  -96.0
  sensitivity N=20 (not chosen)    n  31594 EV/trade $ -5.47 | win  69.3% stop  2.3% rule-exit 20.8% | avg win  +9.6 pts avg loser  -22.5 pts worst  -96.0
  sensitivity N=30 (not chosen)    n  31594 EV/trade $ -5.10 | win  72.5% stop  2.7% rule-exit 16.0% | avg win  +9.6 pts avg loser  -26.2 pts worst  -96.0
   2023  plain EV $ -3.79 | R_10 EV $ -8.90 (stops 2.1% -> 0.7%) | null EV $ -5.52
   2024  plain EV $ +3.14 | R_10 EV $ -5.18 (stops 3.6% -> 1.4%) | null EV $ +2.38
   2025  plain EV $-13.20 | R_10 EV $-10.46 (stops 6.1% -> 2.8%) | null EV $-12.01
   2026  plain EV $ -7.62 | R_10 EV $ -2.60 (stops 7.7% -> 3.3%) | null EV $ -7.97
   L6M   plain EV $ +5.63 | R_10 EV $ +8.44 (stops 7.2% -> 2.7%) | null EV $ +7.24
   L3M   plain EV $ +8.32 | R_10 EV $+13.23 (stops 7.0% -> 2.5%) | null EV $ +8.83
   book MF1   plain EV $+16.00 win 83.2% | R_10 EV $ +3.75 win 68.1% rule-exit 24.2% | null EV $+15.97
   book MF2   plain EV $ +0.41 win 82.8% | R_10 EV $ -4.28 win 65.9% rule-exit 27.7% | null EV $ -0.68
   book MF3   plain EV $ -9.77 win 78.9% | R_10 EV $ -9.21 win 60.7% rule-exit 31.2% | null EV $ -9.80
--- stop -90, PESSIMISTIC fills
plain (no management)              n  31594 EV/trade $ -6.03 | win  80.4% stop  4.8% rule-exit  0.0% | avg win  +9.6 pts avg loser  -40.8 pts worst  -96.8
R_10 (N=10 min, fixed rule)        n  31594 EV/trade $ -7.32 | win  62.7% stop  2.0% rule-exit 29.7% | avg win  +9.5 pts avg loser  -17.0 pts worst  -96.8
null: same count random exits      n  31594 EV/trade $ -6.31 | win  75.9% stop  3.9% rule-exit  8.5% | avg win  +9.6 pts avg loser  -31.4 pts worst  -96.8### NP: +10 target, safety stop S, rule R_N = leave if best excursion < +5 pts N minutes after entry and under water (N=10 fixed in advance). 1 lot, fee 0.24 pt, market exit slip 0.25, stop slip 0.25 (pessimistic +0.85); all events independent (no slot), exits at the bell
--- stop -60, normal fills
plain (no management)              n  19513 EV/trade $ +0.65 | win  82.1% stop 10.6% rule-exit  0.0% | avg win  +9.7 pts avg loser  -44.3 pts worst  -63.0
R_10 (N=10 min, fixed rule)        n  19513 EV/trade $ -1.99 | win  71.6% stop  5.7% rule-exit 18.7% | avg win  +9.7 pts avg loser  -24.8 pts worst  -63.0
null: same count random exits      n  19513 EV/trade $ +1.91 | win  80.7% stop  9.6% rule-exit  2.9% | avg win  +9.7 pts avg loser  -40.2 pts worst  -63.0
  sensitivity N=5 (not chosen)     n  19513 EV/trade $ -3.46 | win  65.1% stop  4.5% rule-exit 27.5% | avg win  +9.7 pts avg loser  -18.6 pts worst  -61.5
  sensitivity N=15 (not chosen)    n  19513 EV/trade $ -0.29 | win  74.8% stop  6.4% rule-exit 14.2% | avg win  +9.7 pts avg loser  -28.8 pts worst  -63.0
  sensitivity N=20 (not chosen)    n  19513 EV/trade $ +0.48 | win  76.7% stop  7.1% rule-exit 11.4% | avg win  +9.7 pts avg loser  -31.8 pts worst  -63.0
  sensitivity N=30 (not chosen)    n  19513 EV/trade $ +1.92 | win  78.8% stop  7.9% rule-exit  7.7% | avg win  +9.7 pts avg loser  -35.7 pts worst  -63.0
   2023  plain EV $ -8.61 | R_10 EV $ -8.70 (stops 9.1% -> 3.5%) | null EV $ -8.86
   2024  plain EV $ +2.97 | R_10 EV $ -0.49 (stops 10.3% -> 5.0%) | null EV $ +7.07
   2025  plain EV $ +5.06 | R_10 EV $ +4.67 (stops 10.7% -> 6.3%) | null EV $ +4.84
   2026  plain EV $ +0.56 | R_10 EV $ -6.22 (stops 11.9% -> 7.4%) | null EV $ +1.71
   L6M   plain EV $ +3.10 | R_10 EV $ -1.57 (stops 11.6% -> 7.1%) | null EV $ +5.91
   L3M   plain EV $ +3.19 | R_10 EV $ +7.41 (stops 11.2% -> 5.3%) | null EV $ +7.50
   book MACD  plain EV $ -5.18 win 82.3% | R_10 EV $-10.26 win 72.0% rule-exit 18.1% | null EV $ -6.11
   book MF1   plain EV $ +7.80 win 83.0% | R_10 EV $ +5.38 win 71.9% rule-exit 19.4% | null EV $+11.01
   book MF2   plain EV $ -1.25 win 81.9% | R_10 EV $-11.67 win 72.1% rule-exit 16.6% | null EV $ -2.13
   book MF3   plain EV $+20.01 win 85.8% | R_10 EV $+13.29 win 75.7% rule-exit 16.7% | null EV $+19.01
   book MF4   plain EV $ -8.44 win 80.1% | R_10 EV $ -6.47 win 69.9% rule-exit 19.5% | null EV $ -6.83
--- stop -60, PESSIMISTIC fills
plain (no management)              n  19513 EV/trade $ -1.14 | win  82.1% stop 10.6% rule-exit  0.0% | avg win  +9.7 pts avg loser  -44.8 pts worst  -63.8
R_10 (N=10 min, fixed rule)        n  19513 EV/trade $ -2.95 | win  71.6% stop  5.7% rule-exit 18.7% | avg win  +9.7 pts avg loser  -25.0 pts worst  -63.8
null: same count random exits      n  19513 EV/trade $ -0.99 | win  80.7% stop  9.7% rule-exit  2.8% | avg win  +9.7 pts avg loser  -40.7 pts worst  -63.8
--- stop -90, normal fills
plain (no management)              n  19513 EV/trade $ +1.59 | win  84.1% stop  5.7% rule-exit  0.0% | avg win  +9.7 pts avg loser  -51.0 pts worst  -92.0
R_10 (N=10 min, fixed rule)        n  19513 EV/trade $ -1.32 | win  72.5% stop  2.6% rule-exit 19.8% | avg win  +9.7 pts avg loser  -25.8 pts worst  -92.0
null: same count random exits      n  19513 EV/trade $ +0.58 | win  82.5% stop  5.2% rule-exit  3.3% | avg win  +9.7 pts avg loser  -45.6 pts worst  -92.0
  sensitivity N=5 (not chosen)     n  19513 EV/trade $ -2.94 | win  65.9% stop  2.2% rule-exit 28.1% | avg win  +9.7 pts avg loser  -19.1 pts worst  -92.0
  sensitivity N=15 (not chosen)    n  19513 EV/trade $ -0.28 | win  75.8% stop  3.0% rule-exit 15.5% | avg win  +9.7 pts avg loser  -30.4 pts worst  -92.0
  sensitivity N=20 (not chosen)    n  19513 EV/trade $ +0.48 | win  77.8% stop  3.4% rule-exit 12.8% | avg win  +9.7 pts avg loser  -33.8 pts worst  -92.0
  sensitivity N=30 (not chosen)    n  19513 EV/trade $ +2.10 | win  80.1% stop  3.8% rule-exit  9.2% | avg win  +9.7 pts avg loser  -38.5 pts worst  -92.0
   2023  plain EV $-11.06 | R_10 EV $-10.61 (stops 4.3% -> 1.6%) | null EV $-12.95
   2024  plain EV $+10.06 | R_10 EV $ +3.41 (stops 5.2% -> 2.1%) | null EV $ +9.35
   2025  plain EV $ +2.63 | R_10 EV $ +6.00 (stops 6.1% -> 3.0%) | null EV $ +1.51
   2026  plain EV $ +1.57 | R_10 EV $ -7.84 (stops 7.0% -> 3.7%) | null EV $ +1.12
   L6M   plain EV $ +6.77 | R_10 EV $ -3.48 (stops 6.4% -> 3.5%) | null EV $ +7.26
   L3M   plain EV $+13.95 | R_10 EV $ +5.67 (stops 5.1% -> 2.4%) | null EV $+17.65
   book MACD  plain EV $ +3.40 win 84.7% | R_10 EV $ -5.06 win 73.1% rule-exit 19.3% | null EV $ +1.29
   book MF1   plain EV $ +7.96 win 84.9% | R_10 EV $ +5.02 win 72.6% rule-exit 20.2% | null EV $ +5.27
   book MF2   plain EV $ +3.26 win 84.3% | R_10 EV $ -7.58 win 73.4% rule-exit 17.8% | null EV $ +1.80
   book MF3   plain EV $ +9.77 win 87.4% | R_10 EV $ +8.44 win 76.6% rule-exit 17.9% | null EV $+11.14
   book MF4   plain EV $ -9.37 win 82.0% | R_10 EV $ -6.95 win 70.8% rule-exit 20.6% | null EV $ -8.28
--- stop -90, PESSIMISTIC fills
plain (no management)              n  19513 EV/trade $ +0.62 | win  84.1% stop  5.7% rule-exit  0.0% | avg win  +9.7 pts avg loser  -51.3 pts worst  -92.8
R_10 (N=10 min, fixed rule)        n  19513 EV/trade $ -1.78 | win  72.5% stop  2.6% rule-exit 19.8% | avg win  +9.7 pts avg loser  -25.9 pts worst  -92.8
null: same count random exits      n  19513 EV/trade $ -0.34 | win  82.2% stop  5.1% rule-exit  3.6% | avg win  +9.7 pts avg loser  -45.0 pts worst  -92.8