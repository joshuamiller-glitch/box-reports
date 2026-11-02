# DS3_STACK_EXPOSURE_V13T - T-SIZER section 3.6 STACK-LEVEL EXPOSURE cells (BASE-4, 2026-11-02T18:28Z)

Base = the T-SIZER live-faithful base (run_v13t_ts): V13T_LIVE (xcost 0.80, stop 2.45, lines empty, lock none = per-book locks only) with the live ER(20) 5-min ladder (x1.5 if ER>=0.30 else x0.5) x zone HALF, SEQUENTIAL rounding (session lots -> zone half -> ER -> half-up, min 1), day / week lock R scaled by max(1, multiplier) with the governor multiplier FIXED at the base ladder value (a trim does not change the lock R). The ER sizer is a KEEP: the ladder-ON tables are the deliverable; ladder-OFF (lots_mult 1) is REFERENCE ONLY and is in the last section.
**Hook** (code/d7base/stack_expo.py): `SE.run_stack(cell, ladder=True)`; `SE.stack_cases(cell)`; `SE.CELLS`. At every signal, in engine order (entry second, book tie-break), net = signed sum over the engine positions open at that second (entry <= t < final exit of the PREVIOUS pass incl. TH-L2 cuts and per-book locks; the 70/30 position counts its 70% leg until the add fills) of the integer lots traded after sizer, zone half and EARLIER trims; the rule then gives the new entry's lots: (a) `cap=N`: lots = clip(N - s*net, 0, ladder lots) (new entry TRIMMED; 0 = signal skipped only when the cap is fully used); (b) `vol=$risk`: per-signal cap = floor($risk / (ATR14_5m x $20)), min 1 (literal formula); the `_scaled` cells use $5k/$7.5k/$10k because at $100-200k the literal cap is never reached; (c) `scale_N, scale_m`: same-direction entry x m when s*net >= N (opposite unchanged, round half-up min 1); (d) `gate_cap=C`: the ER x1.5 becomes x1.0 for that entry when |net| >= C/2. Path dependence = fixed point (pass k uses exits / taken flags of run k-1; converged when no TAKEN row changes lots). Zero lots = the signal is skipped (extra_skip). Rule off = TS base at 0.0000 $.
Scoring: weekly-cumulative maxDD, mean $/wk, worst-20 per window; "carry-drop" = carrying weeks removed (L6M 2026 W27-38, PRE 2024 W34-51, X' 2023 W21-41, as in SIZER_HARNESS). RANK key = maxDD (L6M and PRE first) among cells with mean >= the live-ladder base mean in the same window. Table only, no PASS claim.

## 1. The ten largest same-direction stacks in the signal table (live ladder, TS base)
Peak net lots after the entry; "base_open" = books and lots open at the peak; P&L = sum of the net $ of exactly those positions (whole trades, incl. their later exits).
| # | label date | dir | peak net lots | books + lots (base) | P&L of those positions $ |
|---|---|---|---|---|---|
| 1 | 20240220 | short | -28.0 | SM6, PB2, HM6, KB3, PE11 | 32,018 |
| 2 | 20240726 | long | 28.0 | HM6, SM6, PE11, KB3, PB2 | 33,913 |
| 3 | 20240926 | long | 28.0 | PE11, KB3, SM6, PB2, HM6 | 27,901 |
| 4 | 20241028 | long | 28.0 | HM6, KB3, SM6, PB2, PE11 | 31,321 |
| 5 | 20241125 | long | 28.0 | SM6, PE11, KB3, HM6, PB2 | 32,033 |
| 6 | 20250602 | short | -28.0 | KB3, SM6, PB2, HM6, PE11 | 13,384 |
| 7 | 20250618 | long | 28.0 | SM6, KB3, HM6, PB2, PE11 | 23,347 |
| 8 | 20250806 | long | 28.0 | SM6, KB3, HM6, PB2, PE11 | 30,284 |
| 9 | 20250908 | long | 28.0 | HM6, SM6, PE11, KB3, PB2 | 8,543 |
| 10 | 20251105 | long | 28.0 | HM6, SM6, PE11, KB3, PB2 | 27,942 |

## 2. Cells with the live ER ladder ON (deliverable).  Base (TS, ladder): L6M mean 38.5k maxDD 170k ; PRE mean 18.0k maxDD 161k ; F9 mean 34.8k maxDD 170k ; HOLD mean 32.2k maxDD 170k ; X' mean 5.1k maxDD 73k
| cell | passes | taken rows changed / skipped | lots vs base | L6M mean / maxDD (cut vs base) | PRE mean / maxDD (cut vs base) | F9 mean / maxDD (cut vs base) | HOLD mean / maxDD (cut vs base) | X' mean / maxDD (cut vs base) | carry-drop cut L6M / PRE | flag |
|---|---|---|---|---|---|---|---|---|---|---|
| cap8 | 4 | 2758 / 3924 | -24% | 20.6k / 75k (+56%) | 8.8k / 125k (+22%) | 20.7k / 75k (+56%) | 20.5k / 75k (+56%) | 3.0k / 53k (+27%) | +54% / +22% |  |
| cap10 | 4 | 2420 / 3088 | -17% | 23.3k / 98k (+43%) | 10.9k / 118k (+27%) | 22.9k / 98k (+43%) | 22.6k / 98k (+43%) | 4.1k / 55k (+24%) | +41% / +27% |  |
| cap12 | 4 | 1740 / 2357 | -11% | 28.8k / 116k (+32%) | 12.9k / 133k (+17%) | 26.7k / 116k (+32%) | 25.5k / 116k (+32%) | 4.5k / 61k (+16%) | +32% / +17% |  |
| cap16 | 4 | 719 / 1248 | -4% | 31.3k / 170k (-0%) | 15.3k / 162k (-1%) | 28.1k / 170k (-0%) | 27.1k / 170k (-0%) | 4.7k / 71k (+3%) | +12% / -1% |  |
| vol100k | 1 | 0 / 0 | +0% | 38.5k / 170k (+0%) | 18.0k / 161k (+0%) | 34.8k / 170k (+0%) | 32.2k / 170k (+0%) | 5.1k / 73k (+0%) | +0% / +0% |  |
| vol150k | 1 | 0 / 0 | +0% | 38.5k / 170k (+0%) | 18.0k / 161k (+0%) | 34.8k / 170k (+0%) | 32.2k / 170k (+0%) | 5.1k / 73k (+0%) | +0% / +0% |  |
| vol200k | 1 | 0 / 0 | +0% | 38.5k / 170k (+0%) | 18.0k / 161k (+0%) | 34.8k / 170k (+0%) | 32.2k / 170k (+0%) | 5.1k / 73k (+0%) | +0% / +0% |  |
| vol5k_scaled | 4 | 1834 / 1338 | -12% | 26.7k / 76k (+55%) | 12.6k / 122k (+24%) | 23.8k / 76k (+55%) | 22.2k / 94k (+45%) | 4.0k / 97k (-33%) | +59% / +38% |  |
| vol7.5k_scaled | 4 | 814 / 504 | -4% | 33.6k / 94k (+45%) | 15.6k / 145k (+10%) | 29.3k / 94k (+45%) | 27.0k / 111k (+35%) | 5.0k / 73k (-0%) | +26% / +20% |  |
| vol10k_scaled | 3 | 367 / 206 | -2% | 35.0k / 118k (+31%) | 17.4k / 153k (+5%) | 31.0k / 118k (+31%) | 29.1k / 122k (+28%) | 5.1k / 73k (+0%) | +11% / +8% |  |
| same6x0.5 | 4 | 2826 / 0 | -7% | 32.5k / 158k (+7%) | 15.7k / 149k (+7%) | 28.9k / 158k (+7%) | 27.2k / 158k (+7%) | 3.7k / 68k (+7%) | +35% / +7% |  |
| same6x0.75 | 3 | 1956 / 0 | -3% | 35.1k / 158k (+7%) | 17.1k / 152k (+5%) | 31.2k / 158k (+7%) | 29.5k / 158k (+7%) | 4.3k / 70k (+3%) | +11% / +5% |  |
| same8x0.5 | 3 | 2071 / 0 | -5% | 33.7k / 145k (+15%) | 15.0k / 157k (+3%) | 30.5k / 145k (+15%) | 28.6k / 145k (+15%) | 4.5k / 67k (+8%) | +26% / +3% |  |
| same8x0.75 | 3 | 1401 / 0 | -2% | 35.7k / 147k (+14%) | 16.0k / 158k (+2%) | 32.1k / 147k (+14%) | 30.1k / 147k (+14%) | 4.8k / 71k (+3%) | +11% / +2% |  |
| same10x0.5 | 3 | 1657 / 0 | -3% | 33.3k / 151k (+11%) | 16.0k / 150k (+7%) | 30.6k / 151k (+11%) | 28.7k / 151k (+11%) | 4.3k / 70k (+4%) | +11% / +8% |  |
| same10x0.75 | 3 | 1096 / 0 | -1% | 36.6k / 151k (+12%) | 17.3k / 151k (+6%) | 32.8k / 151k (+12%) | 30.3k / 151k (+12%) | 4.8k / 69k (+5%) | +1% / +6% |  |
| same12x0.5 | 3 | 1115 / 0 | -2% | 35.1k / 162k (+5%) | 16.2k / 158k (+2%) | 31.9k / 162k (+5%) | 29.2k / 162k (+5%) | 4.6k / 71k (+3%) | +11% / +2% |  |
| same12x0.75 | 3 | 721 / 0 | -1% | 37.3k / 156k (+9%) | 17.3k / 156k (+3%) | 33.6k / 156k (+9%) | 30.6k / 156k (+9%) | 4.9k / 72k (+2%) | +1% / +3% |  |
| gate8 | 3 | 3628 / 0 | -8% | 32.6k / 162k (+5%) | 14.5k / 143k (+11%) | 29.1k / 162k (+5%) | 27.2k / 162k (+5%) | 2.3k / 73k (+0%) | +33% / +15% |  |
| gate10 | 3 | 3114 / 0 | -6% | 32.3k / 163k (+4%) | 15.6k / 141k (+12%) | 28.7k / 163k (+4%) | 27.0k / 163k (+4%) | 2.4k / 76k (-5%) | +28% / +12% |  |
| gate12 | 3 | 2789 / 0 | -6% | 33.4k / 176k (-3%) | 16.2k / 153k (+5%) | 29.3k / 176k (-3%) | 27.5k / 176k (-3%) | 3.4k / 78k (-7%) | +26% / +5% |  |
| gate16 | 3 | 2088 / 0 | -4% | 35.0k / 149k (+13%) | 15.1k / 158k (+2%) | 31.2k / 149k (+13%) | 28.8k / 149k (+13%) | 4.1k / 72k (+1%) | +20% / +2% |  |
| cap8+gate | 5 | 3785 / 3643 | -26% | 20.5k / 77k (+55%) | 8.7k / 119k (+26%) | 20.1k / 77k (+55%) | 19.9k / 77k (+55%) | 2.4k / 51k (+30%) | +50% / +26% |  |
| cap10+gate | 4 | 3480 / 2879 | -18% | 23.2k / 97k (+43%) | 10.4k / 150k (+6%) | 22.8k / 97k (+43%) | 22.4k / 97k (+43%) | 3.0k / 55k (+25%) | +46% / +6% |  |
| cap12+gate | 4 | 2799 / 2162 | -12% | 27.6k / 135k (+21%) | 12.9k / 128k (+20%) | 25.9k / 135k (+21%) | 24.7k / 135k (+21%) | 3.3k / 66k (+9%) | +41% / +20% |  |
| cap16+gate | 3 | 2080 / 954 | -5% | 30.8k / 160k (+6%) | 15.0k / 159k (+1%) | 27.6k / 160k (+6%) | 26.5k / 160k (+6%) | 4.0k / 68k (+6%) | +23% / +1% |  |

Flag rule (SIZER KEEP): beats the live ladder on L6M AND PRE maxDD at the same or better mean in both windows AND with the carrying weeks dropped. Cells flagged: none.

## 3. Ranking by maxDD among cells with mean >= the live-ladder base mean (best 6; cells that change no lots are not ranked)
L6M: no cell has mean >= base  [base maxDD 170k]

PRE: no cell has mean >= base  [base maxDD 161k]

Literal vol cap (b) never binds: ATR14 5-min at the signal has median 22 pt (max 255), so $100-200k / (ATR x $20) is 19 to 450 lots; $100k: min cap 19 lots, share of signals with cap <= 28 lots 0.06% ; $150k: min cap 29 lots, share of signals with cap <= 28 lots 0.00% ; $200k: min cap 39 lots, share of signals with cap <= 28 lots 0.00%. The `_scaled` cells ($5k / $7.5k / $10k) are an addition to make the concept testable (caps of 11-45 lots at median ATR).

## 4. What each cell does to the ten real stacks (ladder ON): cell peak net lots and P&L of the same positions (base P&L in section 1)

| cell | #1 | #2 | #3 | #4 | #5 | #6 | #7 | #8 | #9 | #10 | sum d P&L $ |
|---|---|---|---|---|---|---|---|---|---|---|---|
| cap8 | 8 | 8 | 8 | 8 | 8 | 8 | 8 | 10 | 8 | 8 | -180,135 |
| cap10 | 10 | 10 | 10 | 10 | 10 | 10 | 10 | 12 | 10 | 10 | -161,429 |
| cap12 | 12 | 12 | 12 | 12 | 12 | 12 | 12 | 14 | 12 | 12 | -143,363 |
| cap16 | 16 | 16 | 17 | 17 | 16 | 16 | 16 | 16 | 16 | 16 | -105,824 |
| vol100k | 28 | 28 | 28 | 28 | 28 | 28 | 28 | 28 | 28 | 28 | 0 |
| vol150k | 28 | 28 | 28 | 28 | 28 | 28 | 28 | 28 | 28 | 28 | 0 |
| vol200k | 28 | 28 | 28 | 28 | 28 | 28 | 28 | 28 | 28 | 28 | 0 |
| vol5k_scaled | 27 | 25 | 26 | 13 | 21 | 20 | 11 | 17 | 18 | 8 | -59,139 |
| vol7.5k_scaled | 28 | 28 | 28 | 22 | 28 | 28 | 17 | 26 | 27 | 12 | -35,613 |
| vol10k_scaled | 28 | 28 | 28 | 28 | 28 | 28 | 23 | 28 | 28 | 16 | -16,118 |
| same6x0.5 | 18 | 18 | 20 | 18 | 18 | 19 | 18 | 19 | 18 | 18 | -85,611 |
| same6x0.75 | 23 | 23 | 25 | 23 | 23 | 24 | 23 | 24 | 23 | 23 | -40,873 |
| same8x0.5 | 18 | 21 | 20 | 19 | 23 | 19 | 19 | 22 | 21 | 21 | -66,114 |
| same8x0.75 | 23 | 24 | 25 | 24 | 26 | 24 | 24 | 25 | 24 | 24 | -31,530 |
| same10x0.5 | 19 | 21 | 20 | 22 | 23 | 19 | 22 | 22 | 21 | 21 | -63,351 |
| same10x0.75 | 23 | 24 | 25 | 25 | 26 | 24 | 25 | 25 | 24 | 24 | -31,007 |
| same12x0.5 | 22 | 21 | 21 | 22 | 23 | 20 | 22 | 22 | 21 | 21 | -57,311 |
| same12x0.75 | 24 | 24 | 26 | 25 | 26 | 24 | 25 | 25 | 24 | 24 | -28,577 |
| gate8 | 20 | 20 | 22 | 20 | 20 | 19 | 20 | 20 | 20 | 20 | -70,975 |
| gate10 | 20 | 20 | 22 | 20 | 20 | 19 | 20 | 20 | 20 | 20 | -70,975 |
| gate12 | 20 | 20 | 22 | 20 | 20 | 21 | 20 | 21 | 20 | 20 | -67,957 |
| gate16 | 20 | 22 | 22 | 21 | 24 | 21 | 21 | 23 | 22 | 22 | -53,536 |
| cap8+gate | 8 | 8 | 8 | 8 | 8 | 8 | 8 | 9 | 8 | 8 | -180,741 |
| cap10+gate | 10 | 10 | 10 | 10 | 10 | 10 | 10 | 11 | 10 | 10 | -163,372 |
| cap12+gate | 12 | 12 | 12 | 13 | 12 | 12 | 12 | 13 | 12 | 12 | -145,380 |
| cap16+gate | 16 | 16 | 17 | 16 | 16 | 16 | 16 | 16 | 16 | 16 | -103,113 |

Overnight-style example = the largest real stack, 20240220 short: base SM6, PB2, HM6, KB3, PE11 (net -28), P&L $32,018. Per cell (cell lots by book at that stack; P&L of the same positions):
| cell | lots by book | peak net | P&L $ |
|---|---|---|---|
| cap8 | SM5, PB0, HM0, KB3, PE0 | -8 | 8,146 |
| cap10 | SM6, PB1, HM0, KB3, PE0 | -10 | 10,237 |
| cap12 | SM6, PB2, HM1, KB3, PE0 | -12 | 12,640 |
| cap16 | SM6, PB2, HM5, KB3, PE0 | -16 | 17,473 |
| vol100k | SM6, PB2, HM6, KB3, PE11 | -28 | 32,018 |
| vol150k | SM6, PB2, HM6, KB3, PE11 | -28 | 32,018 |
| vol200k | SM6, PB2, HM6, KB3, PE11 | -28 | 32,018 |
| vol5k_scaled | SM6, PB2, HM6, KB3, PE10 | -27 | 30,806 |
| vol7.5k_scaled | SM6, PB2, HM6, KB3, PE11 | -28 | 32,018 |
| vol10k_scaled | SM6, PB2, HM6, KB3, PE11 | -28 | 32,018 |
| same6x0.5 | SM6, PB1, HM3, KB2, PE6 | -18 | 19,915 |
| same6x0.75 | SM6, PB2, HM5, KB2, PE8 | -23 | 25,952 |
| same8x0.5 | SM6, PB1, HM3, KB2, PE6 | -18 | 19,915 |
| same8x0.75 | SM6, PB2, HM5, KB2, PE8 | -23 | 25,952 |
| same10x0.5 | SM6, PB2, HM3, KB2, PE6 | -19 | 21,110 |
| same10x0.75 | SM6, PB2, HM5, KB2, PE8 | -23 | 25,952 |
| same12x0.5 | SM6, PB2, HM6, KB2, PE6 | -22 | 24,735 |
| same12x0.75 | SM6, PB2, HM6, KB2, PE8 | -24 | 27,160 |
| gate8 | SM6, PB1, HM4, KB2, PE7 | -20 | 22,336 |
| gate10 | SM6, PB1, HM4, KB2, PE7 | -20 | 22,336 |
| gate12 | SM6, PB1, HM4, KB2, PE7 | -20 | 22,336 |
| gate16 | SM6, PB1, HM4, KB2, PE7 | -20 | 22,336 |
| cap8+gate | SM5, PB0, HM0, KB2, PE1 | -8 | 8,137 |
| cap10+gate | SM6, PB1, HM0, KB2, PE1 | -10 | 10,228 |
| cap12+gate | SM6, PB1, HM2, KB2, PE1 | -12 | 12,645 |
| cap16+gate | SM6, PB1, HM4, KB2, PE3 | -16 | 17,486 |

## 5. REFERENCE ONLY - ladder OFF (lots_mult 1). Base: L6M 27.6k / 88k ; PRE 14.4k / 121k ; F9 21.0k / 143k ; HOLD 21.9k / 199k ; X' 4.6k / 115k
| cell | L6M mean / maxDD | PRE mean / maxDD | F9 mean / maxDD | HOLD mean / maxDD | X' mean / maxDD |
|---|---|---|---|---|---|
| cap8 | 15.1k / 101k | 10.0k / 97k | 15.8k / 101k | 14.9k / 145k | 2.4k / 77k |
| cap10 | 18.3k / 114k | 12.4k / 106k | 16.6k / 114k | 16.8k / 154k | 3.3k / 88k |
| cap12 | 22.8k / 92k | 13.2k / 118k | 18.5k / 118k | 19.1k / 189k | 3.8k / 106k |
| cap16 | 27.3k / 86k | 14.0k / 119k | 20.8k / 142k | 21.7k / 197k | 4.6k / 115k |
| vol100k | 27.6k / 88k | 14.4k / 121k | 21.0k / 143k | 21.9k / 199k | 4.6k / 115k |
| vol150k | 27.6k / 88k | 14.4k / 121k | 21.0k / 143k | 21.9k / 199k | 4.6k / 115k |
| vol200k | 27.6k / 88k | 14.4k / 121k | 21.0k / 143k | 21.9k / 199k | 4.6k / 115k |
| vol5k_scaled | 24.5k / 75k | 13.1k / 124k | 19.8k / 121k | 18.9k / 207k | 4.1k / 119k |
| vol7.5k_scaled | 25.3k / 88k | 13.5k / 121k | 19.2k / 150k | 19.4k / 228k | 4.6k / 115k |
| vol10k_scaled | 26.7k / 86k | 13.8k / 121k | 19.7k / 150k | 20.6k / 213k | 4.6k / 115k |
| same6x0.5 | 22.2k / 85k | 13.1k / 111k | 19.0k / 94k | 19.0k / 165k | 4.2k / 94k |
| same6x0.75 | 25.0k / 98k | 13.9k / 114k | 20.0k / 111k | 20.4k / 182k | 4.3k / 104k |
| same8x0.5 | 24.4k / 90k | 13.2k / 120k | 19.7k / 121k | 20.3k / 179k | 3.9k / 112k |
| same8x0.75 | 25.4k / 101k | 13.9k / 120k | 19.4k / 138k | 20.6k / 195k | 4.3k / 112k |
| same10x0.5 | 25.7k / 89k | 13.9k / 121k | 19.9k / 126k | 20.7k / 182k | 4.1k / 114k |
| same10x0.75 | 26.7k / 98k | 14.0k / 120k | 20.2k / 141k | 21.1k / 196k | 4.4k / 114k |
| same12x0.5 | 27.4k / 78k | 14.0k / 120k | 21.2k / 137k | 22.2k / 192k | 4.4k / 117k |
| same12x0.75 | 27.4k / 90k | 14.3k / 120k | 20.9k / 142k | 21.8k / 197k | 4.6k / 115k |
| gate8 | 27.6k / 88k | 14.4k / 121k | 21.0k / 143k | 21.9k / 199k | 4.6k / 115k |
| gate10 | 27.6k / 88k | 14.4k / 121k | 21.0k / 143k | 21.9k / 199k | 4.6k / 115k |
| gate12 | 27.6k / 88k | 14.4k / 121k | 21.0k / 143k | 21.9k / 199k | 4.6k / 115k |
| gate16 | 27.6k / 88k | 14.4k / 121k | 21.0k / 143k | 21.9k / 199k | 4.6k / 115k |
| cap8+gate | 15.1k / 101k | 10.0k / 97k | 15.8k / 101k | 14.9k / 145k | 2.4k / 77k |
| cap10+gate | 18.3k / 114k | 12.4k / 106k | 16.6k / 114k | 16.8k / 154k | 3.3k / 88k |
| cap12+gate | 22.8k / 92k | 13.2k / 118k | 18.5k / 118k | 19.1k / 189k | 3.8k / 106k |
| cap16+gate | 27.3k / 86k | 14.0k / 119k | 20.8k / 142k | 21.7k / 197k | 4.6k / 115k |
