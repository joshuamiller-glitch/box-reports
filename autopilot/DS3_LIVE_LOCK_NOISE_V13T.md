# LIVE LOCK SURFACE NOISE on V13T_LIVE (BASE-4, 2026-11-02T15:09Z)

Prereg: l2vast/ds3/prereg/LOCK_NOISE_prereg.md (sha256 3178b435...6d9 in DECISIONS.md). Table only, no PASS claim, no recommendation. Episodes lookup: DS3_ZONES_EPISODES_V13T.md. The audit surface is DS3_LIVE_LOCK_AUDIT_V13T.md (single path, phase 0).

## 1. Phase-averaged (9 lock-reset phases; floor-none cells 1 phase) ranks among the 60 cells (maxDD: 1 = shallowest; mean: 1 = highest)
| window | LIVE | F10N | F12N | F8N | F12 arm3 .5 | F16N |
|---|---|---|---|---|---|---|
| F9 | LIVE: PA maxDD 172k (rank 40/60), PA mean 33.7k (rank 28) | F10N: PA maxDD 135k (rank 1/60), PA mean 37.1k (rank 2) | F12N: PA maxDD 142k (rank 9/60), PA mean 36.8k (rank 3) | F8N: PA maxDD 138k (rank 4/60), PA mean 37.1k (rank 1) | F12 arm3 .5: PA maxDD 144k (rank 11/60), PA mean 35.8k (rank 13) | F16N: PA maxDD 154k (rank 24/60), PA mean 36.5k (rank 4) |
| L6M | LIVE: PA maxDD 172k (rank 40/60), PA mean 36.2k (rank 28) | F10N: PA maxDD 135k (rank 1/60), PA mean 40.0k (rank 1) | F12N: PA maxDD 142k (rank 9/60), PA mean 39.9k (rank 3) | F8N: PA maxDD 138k (rank 4/60), PA mean 39.9k (rank 2) | F12 arm3 .5: PA maxDD 144k (rank 11/60), PA mean 39.7k (rank 7) | F16N: PA maxDD 154k (rank 24/60), PA mean 39.3k (rank 13) |
| HOLD | LIVE: PA maxDD 172k (rank 37/60), PA mean 30.6k (rank 30) | F10N: PA maxDD 147k (rank 11/60), PA mean 34.4k (rank 2) | F12N: PA maxDD 156k (rank 20/60), PA mean 34.3k (rank 4) | F8N: PA maxDD 144k (rank 5/60), PA mean 34.5k (rank 1) | F12 arm3 .5: PA maxDD 148k (rank 12/60), PA mean 33.4k (rank 12) | F16N: PA maxDD 156k (rank 21/60), PA mean 34.3k (rank 3) |
| PRE | LIVE: PA maxDD 168k (rank 22/60), PA mean 17.1k (rank 12) | F10N: PA maxDD 172k (rank 26/60), PA mean 17.0k (rank 13) | F12N: PA maxDD 176k (rank 31/60), PA mean 16.9k (rank 14) | F8N: PA maxDD 187k (rank 49/60), PA mean 16.3k (rank 23) | F12 arm3 .5: PA maxDD 181k (rank 39/60), PA mean 16.6k (rank 19) | F16N: PA maxDD 179k (rank 36/60), PA mean 17.5k (rank 6) |
| X' | LIVE: PA maxDD 89k (rank 32/60), PA mean 4.5k (rank 45) | F10N: PA maxDD 83k (rank 19/60), PA mean 4.8k (rank 39) | F12N: PA maxDD 77k (rank 7/60), PA mean 5.1k (rank 31) | F8N: PA maxDD 85k (rank 24/60), PA mean 4.4k (rank 50) | F12 arm3 .5: PA maxDD 78k (rank 9/60), PA mean 5.3k (rank 25) | F16N: PA maxDD 76k (rank 5/60), PA mean 5.4k (rank 24) |

Phase spread of the live cell: F9: live maxDD over 9 phases 151-190k (mean 172k); L6M: live maxDD over 9 phases 151-190k (mean 172k); HOLD: live maxDD over 9 phases 151-190k (mean 172k); PRE: live maxDD over 9 phases 160-176k (mean 168k); X': live maxDD over 9 phases 86-98k (mean 89k)


## 2. Market-exit cost 0.58 / 0.80 / 1.02 (phase 0): maxDD (rank) / mean (rank) among the 60 cells
| window | xcost | LIVE | F10N | F12N | F8N | F12 arm3 .5 | F16N |
|---|---|---|---|---|---|---|---|
| F9 | 0.58 | 134k (#29) / 35.0k (#23) | 96k (#1) / 38.6k (#1) | 113k (#8) / 37.9k (#3) | 114k (#9) / 37.2k (#10) | 111k (#5) / 37.1k (#12) | 125k (#20) / 38.4k (#2) |
| F9 | 0.8 | 151k (#29) / 33.7k (#22) | 106k (#1) / 37.2k (#1) | 124k (#8) / 36.5k (#3) | 127k (#9) / 36.0k (#8) | 124k (#7) / 35.7k (#11) | 135k (#19) / 36.9k (#2) |
| F9 | 1.02 | 166k (#34) / 32.5k (#22) | 116k (#1) / 35.9k (#1) | 134k (#5) / 35.3k (#3) | 138k (#12) / 34.3k (#12) | 138k (#11) / 34.4k (#11) | 146k (#19) / 35.7k (#2) |
| L6M | 0.58 | 134k (#29) / 38.2k (#27) | 96k (#1) / 42.6k (#1) | 113k (#8) / 41.6k (#7) | 114k (#9) / 42.5k (#2) | 111k (#5) / 41.5k (#8) | 125k (#20) / 41.5k (#9) |
| L6M | 0.8 | 151k (#29) / 36.7k (#27) | 106k (#1) / 41.0k (#2) | 124k (#8) / 40.0k (#7) | 127k (#9) / 41.2k (#1) | 124k (#7) / 39.9k (#9) | 135k (#19) / 39.9k (#8) |
| L6M | 1.02 | 166k (#34) / 35.4k (#28) | 116k (#1) / 39.7k (#3) | 134k (#5) / 38.8k (#7) | 138k (#12) / 39.9k (#1) | 138k (#11) / 38.5k (#10) | 146k (#19) / 38.7k (#8) |
| PRE | 0.58 | 164k (#36) / 18.0k (#16) | 161k (#32) / 18.1k (#15) | 164k (#38) / 18.1k (#14) | 141k (#20) / 18.5k (#6) | 164k (#37) / 17.8k (#21) | 172k (#45) / 18.5k (#7) |
| PRE | 0.8 | 166k (#34) / 17.3k (#17) | 164k (#31) / 17.3k (#15) | 167k (#36) / 17.3k (#16) | 143k (#19) / 17.7k (#3) | 170k (#38) / 17.1k (#22) | 176k (#45) / 17.7k (#6) |
| PRE | 1.02 | 169k (#29) / 16.6k (#16) | 175k (#35) / 16.6k (#15) | 170k (#33) / 16.6k (#17) | 153k (#18) / 17.0k (#4) | 189k (#51) / 16.3k (#23) | 179k (#41) / 17.0k (#6) |


## 3. 100 lot-shuffle placebo worlds: preference of the cell over the LIVE cell (positive = cell better) vs the noise of lot assignment; rank = share of worlds with at least as large a preference
| cell | L6M mean | L6M maxDD | F9 maxDD | PRE maxDD | worst-20 ALL |
|---|---|---|---|---|---|
| F10N | real +4.3k vs placebo med +2.6k [-0.9,+6.0] rank 0.24 (n 100) | real +45.0k vs placebo med -3.3k [-30.0,+21.6] rank 0.00 (n 100) | real +45.0k vs placebo med +2.4k [-26.5,+33.2] rank 0.03 (n 100) | real +1.8k vs placebo med -3.1k [-78.1,+40.9] rank 0.41 (n 100) | real +32.5k vs placebo med -3.9k [-80.7,+45.5] rank 0.09 (n 100) |
| F12N | real +3.3k vs placebo med +2.8k [-0.2,+5.9] rank 0.41 (n 100) | real +27.2k vs placebo med -4.8k [-27.8,+16.0] rank 0.00 (n 100) | real +27.2k vs placebo med -0.7k [-24.1,+16.0] rank 0.00 (n 100) | real -1.1k vs placebo med -1.7k [-48.8,+26.4] rank 0.48 (n 100) | real -27.6k vs placebo med -34.9k [-74.1,+9.1] rank 0.41 (n 100) |
| F8N | real +4.4k vs placebo med +1.6k [-1.9,+5.8] rank 0.12 (n 100) | real +23.8k vs placebo med -0.7k [-29.7,+31.3] rank 0.10 (n 100) | real +23.8k vs placebo med +8.6k [-30.9,+48.1] rank 0.22 (n 100) | real +23.3k vs placebo med -2.4k [-78.7,+30.8] rank 0.14 (n 100) | real +80.8k vs placebo med +44.6k [-39.0,+104.4] rank 0.21 (n 100) |
| F12 arm3 .5 | real +3.2k vs placebo med +2.1k [-0.6,+4.6] rank 0.27 (n 100) | real +27.2k vs placebo med -3.5k [-25.9,+12.7] rank 0.00 (n 100) | real +27.2k vs placebo med +0.1k [-18.0,+17.6] rank 0.00 (n 100) | real -4.1k vs placebo med -3.6k [-57.9,+14.2] rank 0.52 (n 100) | real -35.0k vs placebo med -31.8k [-81.3,+5.9] rank 0.55 (n 100) |
| F16N | real +3.2k vs placebo med +2.9k [-0.2,+6.5] rank 0.46 (n 100) | real +15.7k vs placebo med -8.0k [-35.9,+17.2] rank 0.08 (n 100) | real +15.7k vs placebo med -2.6k [-36.0,+25.9] rank 0.14 (n 100) | real -9.6k vs placebo med -1.0k [-40.3,+44.8] rank 0.70 (n 100) | real -56.3k vs placebo med -53.0k [-106.8,+8.1] rank 0.52 (n 100) |


## 4. Per book own series (phase 0): mean / maxDD
| book | window | LIVE | F10N | F12N | F8N |
|---|---|---|---|---|---|
| K7 | F9 | 1.4k / DD 64k | 3.3k / DD 62k | 2.9k / DD 63k | 2.9k / DD 62k |
| K7 | L6M | 2.6k / DD 64k | 5.1k / DD 54k | 4.6k / DD 62k | 4.8k / DD 60k |
| K7 | PRE | 1.2k / DD 40k | 1.5k / DD 42k | 1.7k / DD 38k | 1.5k / DD 47k |
| P7 | F9 | 20.3k / DD 93k | 22.1k / DD 72k | 22.3k / DD 72k | 21.8k / DD 82k |
| P7 | L6M | 24.2k / DD 93k | 26.4k / DD 72k | 26.5k / DD 72k | 26.3k / DD 82k |
| P7 | PRE | 12.7k / DD 110k | 11.6k / DD 112k | 11.6k / DD 112k | 12.1k / DD 92k |
| U7 | F9 | 4.1k / DD 39k | 4.2k / DD 39k | 4.2k / DD 39k | 4.1k / DD 32k |
| U7 | L6M | 3.0k / DD 39k | 3.0k / DD 39k | 3.0k / DD 39k | 3.3k / DD 32k |
| U7 | PRE | 1.4k / DD 62k | 1.5k / DD 62k | 1.4k / DD 62k | 1.5k / DD 62k |
| H7 | F9 | 7.3k / DD 31k | 7.3k / DD 31k | 7.2k / DD 31k | 6.9k / DD 37k |
| H7 | L6M | 8.3k / DD 31k | 8.1k / DD 31k | 8.0k / DD 31k | 8.2k / DD 37k |
| H7 | PRE | 0.7k / DD 64k | 0.9k / DD 62k | 0.9k / DD 61k | 0.8k / DD 65k |
| M7 | F9 | 0.0k / DD 67k | 0.1k / DD 68k | -0.1k / DD 73k | -0.1k / DD 67k |
| M7 | L6M | -2.0k / DD 65k | -1.8k / DD 64k | -1.9k / DD 68k | -1.7k / DD 63k |
| M7 | PRE | 0.0k / DD 88k | 0.2k / DD 84k | 0.1k / DD 86k | 0.2k / DD 83k |
| A6 | F9 | 0.5k / DD 20k | 0.3k / DD 21k | 0.1k / DD 27k | 0.4k / DD 20k |
| A6 | L6M | 0.6k / DD 20k | 0.2k / DD 21k | -0.1k / DD 27k | 0.4k / DD 20k |
| A6 | PRE | 1.3k / DD 18k | 1.6k / DD 16k | 1.5k / DD 16k | 1.7k / DD 16k |
