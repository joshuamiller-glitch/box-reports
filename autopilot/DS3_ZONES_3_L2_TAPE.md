# DS3_ZONES_3_L2_TAPE - tape (order-flow) zone streams, ZL-2 (T-ZONES-3 ADDENDUM part 2)

**STATUS: OLD CAP (to 2026-02-06).** Research only; descriptive statistics only (no strategy scoring: ZL-3 does the drawdown scoring after ZL-1 and ZL-2). Prereg `autopilot/ZL2_TAPE_prereg.md` sha256 0f1e80179c277ed77c0ec38b5f7bdcb386cf088b37a9742585b35d122f4e6cc7 (logged in DECISIONS.md before any outcome statistic; disclosures inside). Cap is a PARAMETER (ZL_CAP_LD); everything below is built to the old cap and is labelled OLD CAP until REDO-1 announces the extended de-duplicated tape; the extension appends days (README_TAPE.md section 6), it does not rebuild. Code `l2vast/ds3/code/zl2/`, outputs `l2vast/ds3/out/zl/` (streams in `streams_tape/`, my other folders `fp/ desc_tape/ features_tape/ pools_tape/ audit_tape/`; ZL-1 uses `*_book`).

## PAGE 1

**DATA.** The 1-s print tape of NQ (every print: second, price, size, aggressor side) and the 1-min tables are on disk to 2026-02 (old cap) and to 2026-10 for the extension; everything below is derivable from them, nothing to buy. Built from the DE-DUPLICATED monthly copies (`out/tape_dedup/NQ_dropin`: the 11 months with the stray Sunday-open hour use the de-duplicated files), 36 months 2023-02..2026-02, 130,799,588 second x tick x aggressor rows (761 label days used, 13 roll days excluded: see section 7). Prices are in the path frame (the back-adjusted frame of the signals and of every POI stream). Tape volume equals the library 1-s volume exactly on 750 of the 761 label days used (the other 11 differ by < 1.7%, the known roll-day deficit).

**Verdict in plain words (descriptive; leads only).**
* 128 streams (871,477 rows) are written in POI format. Every row carries formed time (t_ek / ek), freshness (end, plus the 2nd and 3rd touch episode), strength (measured at formation, causal) and decay (cap). The causality audit (6 random as-of cuts, every generator re-run on a tape truncated at the cut, 15,053 rows compared) found **0 missing, 0 extra, max difference 0.0** in level and strength after two real defects the audit itself exposed were fixed (section 7).
* **The three profile lines group 10 lacks now exist on the true tick tape**: `TPF|vah|sw15` (18132 rows, 23.8/day), `TPF|lvn1|sw1h` (3059, 4.0/day), `TPF|hvn0|sw1h` (4539, 6.0/day), with the old 1-s-approximation CF-A lines for comparison (levels agree within 2 pts for 85% / 90% / 98% of rows, median difference 0.0-0.25 pts). The profile rule is the CF-A rule unchanged (tick bins 0.25, 70% value area, gaussian sigma 2 pts, HVN prominence 10%, LVN 8%, anchors = leg between consecutive confirmed fractal-2/2 pivots of 15-m / 1-h bars); only the volume is true volume at price.
* **Support / resistance hit-rate (HOLD5: after the first touch within 4 h the level holds 5 pts before it is broken 5 pts) vs the random-level and shuffled-day placebos (200 draws each), whole sample:** 5 of 119 streams rank >= 0.975 against BOTH placebos (chance expectation about 3): TCP|vah|5d, TLP|cl25|4h, TPF|hvn1|sess, TPF|lvn1|sw1h, TPF|lvn2|sw1h. They are LEADS, not findings: in the recent window (HOLD, 2025-07..2026-02) only TCP|vah|5d, TLP|cl25|4h, TPF|lvn2|sw1h of them stay above 0.95.
* **The opposite is the clear result: liquidity levels hold LESS than random levels.** 25 streams rank <= 0.025 against both placebos in the whole sample, 23 of them are measured-pool sources (swing H/L 15-m / 1-h, equal H/L, previous-session / killzone / prior-day H/L): HOLD5 0.37-0.48 against 0.50-0.55 for random levels at the same distances. Swing, equal and session extremes are RUN-THROUGH levels (they are where stops sit and they get taken), so as "resistance / support" they are worse than nothing; as magnets / sweep targets they are the thing the pool statistics measure (next bullet). Cum-delta high / bull-divergence levels behave the same way.
* **Measured liquidity pools are small.** Aggressor volume within 2 ticks beyond a broken level in the 60 s of the break: median 19 contracts for a 15-m swing, 23 for a 1-h swing, 21 for equal highs / lows (15-m), 40 for the previous NY-AM / London / pre-market highs and lows, 24 for prior-day / RTH highs and lows (P90 80-125); 10% of breaks print < 10 contracts. The pool a level is KNOWN to have at formation (the causal strength = median of the last 200 completed same-type pools) does not predict the move beyond it (top minus bottom tercile within type and quarter: median 15-min excursion -0.25 pts all history, +1.25 pts HOLD; re-claim within 5 min +0.010 / +0.026), whereas the pool actually printed in the break window does (excursion +6.50 pts, mostly mechanical: it is measured in the same minute as the break). Bigger pools are not an ex-ante filter on this evidence.
* **Density.** At the 44,370 capped signals a fresh coded line (S8) lies within 20 pts ahead for 15% and within 20 pts behind for 9% of signals (S11 with the new tape-built three: 20% / 11%); the tape zones are dense by comparison (67% / 40% of signals have a fresh tape zone within 20 pts ahead / behind, median 4 / 3 rows within 40 pts, nearest zone in any direction 9.5 pts median). Features defined and written (section 5); ZL-3 scores them.
* Nothing here is a trading result. Ranking by descriptive hold-rate rank is a LEAD label at most; ZL-3 decides with drawdown, placebo-stack and the capacity/latency frames. Multiplicity: 128 streams x 4 windows x 2 placebos in the table, no correction.

### Stream table (counts per good label day, persistence, coverage of the signals)
rows/day over 761 good label days. life = median hours from formation to decay (cap). touched = share touched at least once before decay; fresh 4h = share still untouched 4 h after formation; >=2 touches = share with a second touch episode (touch >= 60 s after the previous). cov ahead / behind 20 = share of the 44,370 capped signals with a FRESH row within 20 pts ahead / behind (density.py semantics, not limited to target/stop). Strength = measured at formation (see the family notes in section 4).

| stream | rows | /day | life h | touched | fresh 4h | >=2 touches | med s to 1st touch | cov ahead 20 | cov behind 20 | strength (median) |
|---|---|---|---|---|---|---|---|---|---|---|
| TCD|burst | 2,498 | 3.28 | 8.4 | 91% | 10% | 82% | 91 | 1% | 1% | 760.00 |
| TCD|cdhi | 9,001 | 11.83 | 16.3 | 93% | 13% | 89% | 506 | 7% | 1% | 1130.00 |
| TCD|cdlo | 7,727 | 10.15 | 15.9 | 89% | 17% | 84% | 529 | 6% | 1% | 1257.00 |
| TCD|divbear | 1,621 | 2.13 | 4.0 | 91% | 9% | 83% | 162 | 1% | 0% | 274.00 |
| TCD|divbull | 1,162 | 1.53 | 4.0 | 88% | 12% | 80% | 143 | 1% | 0% | 272.00 |
| TCP|hvn0|20d | 741 | 0.97 | 24.0 | 27% | 91% | 25% | 49,527 | 0% | 0% | 3.67 |
| TCP|hvn0|5d | 756 | 0.99 | 24.0 | 44% | 84% | 41% | 35,708 | 1% | 0% | 3.91 |
| TCP|hvn0|60d | 701 | 0.92 | 24.0 | 16% | 95% | 14% | 48,940 | 0% | 0% | 4.33 |
| TCP|hvn1|20d | 741 | 0.97 | 24.0 | 27% | 93% | 25% | 52,207 | 0% | 0% | 3.12 |
| TCP|hvn1|5d | 755 | 0.99 | 24.0 | 45% | 84% | 43% | 38,953 | 1% | 0% | 3.13 |
| TCP|hvn1|60d | 701 | 0.92 | 24.0 | 15% | 97% | 13% | 54,563 | 0% | 0% | 3.57 |
| TCP|hvn2|20d | 738 | 0.97 | 24.0 | 27% | 91% | 25% | 37,889 | 1% | 0% | 2.80 |
| TCP|hvn2|5d | 749 | 0.98 | 24.0 | 42% | 86% | 39% | 39,378 | 1% | 0% | 2.59 |
| TCP|hvn2|60d | 701 | 0.92 | 24.0 | 13% | 97% | 12% | 49,341 | 0% | 0% | 3.35 |
| TCP|lvn0|20d | 741 | 0.97 | 24.0 | 20% | 95% | 18% | 55,955 | 0% | 0% | 0.91 |
| TCP|lvn0|5d | 756 | 0.99 | 24.0 | 33% | 92% | 31% | 52,914 | 1% | 0% | 0.87 |
| TCP|lvn0|60d | 701 | 0.92 | 24.0 | 10% | 98% | 9% | 56,554 | 0% | 0% | 0.93 |
| TCP|lvn1|20d | 739 | 0.97 | 24.0 | 22% | 95% | 20% | 53,014 | 0% | 0% | 0.74 |
| TCP|lvn1|5d | 753 | 0.99 | 24.0 | 35% | 89% | 32% | 50,405 | 1% | 0% | 0.69 |
| TCP|lvn1|60d | 701 | 0.92 | 24.0 | 12% | 97% | 11% | 55,719 | 0% | 0% | 0.83 |
| TCP|lvn2|20d | 738 | 0.97 | 24.0 | 20% | 95% | 18% | 52,645 | 0% | 0% | 0.60 |
| TCP|lvn2|5d | 735 | 0.97 | 24.0 | 40% | 89% | 36% | 43,736 | 1% | 0% | 0.50 |
| TCP|lvn2|60d | 701 | 0.92 | 24.0 | 11% | 97% | 10% | 52,332 | 0% | 0% | 0.68 |
| TCP|poc|20d | 741 | 0.97 | 24.0 | 26% | 93% | 24% | 45,708 | 0% | 0% | 0.08 |
| TCP|poc|5d | 756 | 0.99 | 24.0 | 44% | 85% | 40% | 41,002 | 1% | 0% | 0.16 |
| TCP|poc|60d | 701 | 0.92 | 24.0 | 15% | 96% | 14% | 46,980 | 0% | 0% | 0.04 |
| TCP|vah|20d | 741 | 0.97 | 24.0 | 27% | 92% | 25% | 48,048 | 1% | 0% | 647.00 |
| TCP|vah|5d | 756 | 0.99 | 24.0 | 42% | 87% | 39% | 52,217 | 1% | 0% | 310.00 |
| TCP|vah|60d | 701 | 0.92 | 24.0 | 20% | 94% | 19% | 50,506 | 0% | 0% | 1126.00 |
| TCP|val|20d | 741 | 0.97 | 24.0 | 15% | 96% | 15% | 52,523 | 0% | 0% | 647.00 |
| TCP|val|5d | 756 | 0.99 | 24.0 | 33% | 91% | 31% | 46,533 | 0% | 0% | 310.00 |
| TCP|val|60d | 701 | 0.92 | 24.0 | 6% | 99% | 6% | 52,550 | 0% | 0% | 1126.00 |
| TDA|abs|15m | 320 | 0.42 | 4.0 | 93% | 7% | 86% | 52 | 0% | 0% | 2.55 |
| TDA|abs|5m | 2,248 | 2.95 | 4.0 | 96% | 4% | 89% | 16 | 1% | 0% | 2.52 |
| TLP|cl25|4h | 3,403 | 4.47 | 4.0 | 99% | 1% | 89% | 1 | 0% | 0% | 5.44 |
| TLP|p100|1h | 3,531 | 4.64 | 1.0 | 96% | 4% | 82% | 5 | 0% | 0% | 1.31 |
| TLP|p100|4h | 3,531 | 4.64 | 4.0 | 97% | 3% | 88% | 5 | 0% | 0% | 1.31 |
| TLP|p25|1h | 83,678 | 109.96 | 1.0 | 97% | 3% | 81% | 3 | 4% | 6% | 1.32 |
| TLP|p25|4h | 83,679 | 109.96 | 4.0 | 98% | 2% | 88% | 3 | 5% | 6% | 1.32 |
| TLP|p50|1h | 16,525 | 21.71 | 1.0 | 97% | 3% | 81% | 4 | 1% | 1% | 1.36 |
| TLP|p50|4h | 16,525 | 21.71 | 4.0 | 98% | 2% | 88% | 4 | 1% | 2% | 1.36 |
| TLQ|EQL|rel|15m | 5,147 | 6.76 | 24.0 | 82% | 41% | 78% | 5,217 | 4% | 1% | 20.50 |
| TLQ|EQL|rel|1h | 1,184 | 1.56 | 24.0 | 68% | 65% | 64% | 13,391 | 1% | 0% | 28.00 |
| TLQ|EQL|tight|15m | 1,023 | 1.34 | 24.0 | 86% | 37% | 83% | 5,107 | 1% | 0% | 23.00 |
| TLQ|EQL|tight|1h | 85 | 0.11 | 24.0 | 66% | 53% | 62% | 9,710 | 0% | 0% | 25.50 |
| TLQ|KZ|kz|asia | 1,546 | 2.03 | 24.0 | 87% | 45% | 84% | 10,307 | 2% | 0% | 16.00 |
| TLQ|KZ|kz|lc | 1,544 | 2.03 | 24.0 | 69% | 49% | 66% | 5,136 | 2% | 0% | 42.50 |
| TLQ|KZ|kz|london | 1,546 | 2.03 | 24.0 | 83% | 45% | 78% | 9,596 | 2% | 0% | 22.00 |
| TLQ|KZ|kz|ny | 1,548 | 2.03 | 24.0 | 70% | 43% | 66% | 1,562 | 2% | 0% | 51.75 |
| TLQ|PDX|day | 1,546 | 2.03 | 24.0 | 50% | 85% | 47% | 40,762 | 2% | 0% | 24.50 |
| TLQ|PDX|rth | 1,544 | 2.03 | 24.0 | 55% | 83% | 52% | 47,041 | 2% | 0% | 28.00 |
| TLQ|PDX|week | 312 | 0.41 | 168.0 | 52% | 94% | 49% | 99,963 | 0% | 0% | 41.50 |
| TLQ|SES|asia | 1,548 | 2.03 | 24.0 | 81% | 53% | 78% | 8,105 | 2% | 0% | 19.00 |
| TLQ|SES|close | 1,484 | 1.95 | 24.0 | 81% | 62% | 77% | 19,984 | 4% | 1% | 18.00 |
| TLQ|SES|london | 1,546 | 2.03 | 24.0 | 76% | 33% | 70% | 3,694 | 2% | 0% | 35.50 |
| TLQ|SES|nyam | 1,544 | 2.03 | 24.0 | 63% | 57% | 60% | 6,306 | 2% | 0% | 47.75 |
| TLQ|SES|nypm | 1,544 | 2.03 | 24.0 | 72% | 60% | 69% | 4,400 | 2% | 0% | 33.00 |
| TLQ|SES|on | 1,548 | 2.03 | 24.0 | 68% | 44% | 62% | 1,560 | 2% | 0% | 50.25 |
| TLQ|SES|pre | 1,548 | 2.03 | 24.0 | 84% | 22% | 77% | 237 | 1% | 0% | 55.00 |
| TLQ|SES|rth | 1,544 | 2.03 | 24.0 | 55% | 83% | 52% | 47,041 | 2% | 0% | 28.00 |
| TLQ|SWG|f3|15m | 31,061 | 40.82 | 24.0 | 87% | 30% | 83% | 2,924 | 24% | 6% | 16.50 |
| TLQ|SWG|f3|1h | 7,812 | 10.27 | 24.0 | 75% | 54% | 71% | 9,016 | 8% | 1% | 22.00 |
| TLQ|SWG|f5|15m | 18,440 | 24.23 | 24.0 | 83% | 39% | 79% | 4,599 | 16% | 3% | 18.00 |
| TLQ|SWG|f5|1h | 4,606 | 6.05 | 24.0 | 69% | 63% | 65% | 12,663 | 5% | 0% | 24.00 |
| TLQ|SWG|f7|15m | 13,178 | 17.32 | 24.0 | 80% | 44% | 77% | 5,919 | 12% | 2% | 19.00 |
| TLQ|SWG|f7|1h | 3,311 | 4.35 | 24.0 | 64% | 68% | 60% | 14,401 | 3% | 0% | 26.50 |
| TPF|hvn0|day | 761 | 1.00 | 24.0 | 76% | 62% | 71% | 13,480 | 2% | 1% | 3.41 |
| TPF|hvn0|month | 37 | 0.05 | 696.0 | 78% | 89% | 78% | 143,677 | 0% | 0% | 3.69 |
| TPF|hvn0|sess | 4,531 | 5.95 | 3.0 | 69% | 33% | 60% | 321 | 2% | 2% | 2.61 |
| TPF|hvn0|sw15 | 18,132 | 23.83 | 0.8 | 54% | 46% | 42% | 417 | 3% | 4% | 2.14 |
| TPF|hvn0|sw1h | 4,539 | 5.96 | 4.0 | 50% | 53% | 44% | 1,831 | 2% | 1% | 2.72 |
| TPF|hvn0|week | 157 | 0.21 | 168.0 | 64% | 84% | 62% | 58,969 | 0% | 0% | 3.66 |
| TPF|hvn1|day | 729 | 0.96 | 24.0 | 69% | 72% | 64% | 29,179 | 1% | 1% | 2.44 |
| TPF|hvn1|month | 37 | 0.05 | 696.0 | 81% | 95% | 78% | 115,941 | 0% | 0% | 3.11 |
| TPF|hvn1|sess | 3,624 | 4.76 | 3.0 | 59% | 44% | 51% | 541 | 2% | 1% | 1.81 |
| TPF|hvn1|sw15 | 12,052 | 15.84 | 1.0 | 48% | 53% | 37% | 438 | 3% | 2% | 1.57 |
| TPF|hvn1|sw1h | 3,879 | 5.10 | 4.0 | 47% | 56% | 41% | 1,899 | 2% | 1% | 1.94 |
| TPF|hvn1|week | 157 | 0.21 | 168.0 | 68% | 81% | 68% | 58,142 | 0% | 0% | 2.98 |
| TPF|hvn2|day | 650 | 0.85 | 24.0 | 64% | 76% | 60% | 33,497 | 1% | 0% | 1.97 |
| TPF|hvn2|month | 37 | 0.05 | 696.0 | 76% | 95% | 76% | 239,368 | 0% | 0% | 2.72 |
| TPF|hvn2|sess | 2,412 | 3.17 | 3.0 | 53% | 49% | 46% | 799 | 1% | 1% | 1.50 |
| TPF|hvn2|sw15 | 6,761 | 8.88 | 1.0 | 42% | 58% | 33% | 549 | 2% | 1% | 1.39 |
| TPF|hvn2|sw1h | 2,856 | 3.75 | 4.0 | 45% | 58% | 39% | 2,144 | 1% | 0% | 1.63 |
| TPF|hvn2|week | 157 | 0.21 | 168.0 | 66% | 83% | 63% | 60,667 | 0% | 0% | 2.44 |
| TPF|lvn0|day | 742 | 0.98 | 24.0 | 61% | 80% | 58% | 37,500 | 1% | 0% | 0.74 |
| TPF|lvn0|month | 37 | 0.05 | 696.0 | 54% | 86% | 51% | 201,653 | 0% | 0% | 0.93 |
| TPF|lvn0|sess | 3,754 | 4.93 | 3.0 | 57% | 46% | 49% | 900 | 2% | 1% | 0.56 |
| TPF|lvn0|sw15 | 12,601 | 16.56 | 1.0 | 50% | 51% | 40% | 412 | 2% | 3% | 0.50 |
| TPF|lvn0|sw1h | 3,985 | 5.24 | 4.0 | 48% | 54% | 43% | 1,849 | 2% | 1% | 0.64 |
| TPF|lvn0|week | 157 | 0.21 | 168.0 | 62% | 91% | 61% | 147,190 | 0% | 0% | 0.87 |
| TPF|lvn1|day | 683 | 0.90 | 24.0 | 61% | 77% | 57% | 36,376 | 1% | 0% | 0.49 |
| TPF|lvn1|month | 37 | 0.05 | 696.0 | 62% | 92% | 57% | 145,912 | 0% | 0% | 0.76 |
| TPF|lvn1|sess | 2,641 | 3.47 | 3.0 | 55% | 47% | 48% | 957 | 1% | 1% | 0.31 |
| TPF|lvn1|sw15 | 7,399 | 9.72 | 1.0 | 48% | 53% | 38% | 445 | 2% | 1% | 0.30 |
| TPF|lvn1|sw1h | 3,059 | 4.02 | 4.0 | 45% | 58% | 39% | 1,988 | 2% | 0% | 0.39 |
| TPF|lvn1|week | 157 | 0.21 | 168.0 | 67% | 84% | 64% | 75,608 | 0% | 0% | 0.72 |
| TPF|lvn2|day | 600 | 0.79 | 24.0 | 62% | 75% | 58% | 30,522 | 1% | 0% | 0.23 |
| TPF|lvn2|month | 37 | 0.05 | 696.0 | 54% | 92% | 51% | 325,874 | 0% | 0% | 0.59 |
| TPF|lvn2|sess | 1,728 | 2.27 | 3.0 | 54% | 49% | 47% | 1,034 | 1% | 0% | 0.14 |
| TPF|lvn2|sw15 | 4,301 | 5.65 | 1.0 | 44% | 56% | 35% | 458 | 1% | 1% | 0.18 |
| TPF|lvn2|sw1h | 2,225 | 2.92 | 4.0 | 42% | 60% | 37% | 1,910 | 1% | 0% | 0.23 |
| TPF|lvn2|week | 153 | 0.20 | 168.0 | 67% | 83% | 65% | 66,456 | 0% | 0% | 0.49 |
| TPF|poc|day | 761 | 1.00 | 24.0 | 73% | 63% | 70% | 13,899 | 2% | 1% | 0.37 |
| TPF|poc|month | 37 | 0.05 | 696.0 | 81% | 92% | 81% | 104,448 | 0% | 0% | 0.08 |
| TPF|poc|sess | 4,531 | 5.95 | 3.0 | 68% | 34% | 58% | 315 | 2% | 2% | 0.94 |
| TPF|poc|sw15 | 18,132 | 23.83 | 0.8 | 53% | 47% | 42% | 433 | 3% | 4% | 1.76 |
| TPF|poc|sw1h | 4,539 | 5.96 | 4.0 | 50% | 53% | 44% | 1,842 | 2% | 1% | 0.81 |
| TPF|poc|week | 157 | 0.21 | 168.0 | 64% | 83% | 62% | 60,649 | 0% | 0% | 0.16 |
| TPF|vah|day | 761 | 1.00 | 24.0 | 69% | 73% | 66% | 31,830 | 2% | 0% | 126.50 |
| TPF|vah|month | 37 | 0.05 | 696.0 | 78% | 95% | 78% | 312,562 | 0% | 0% | 757.50 |
| TPF|vah|sess | 4,531 | 5.95 | 3.0 | 64% | 39% | 55% | 670 | 3% | 1% | 45.00 |
| TPF|vah|sw15 | 18,132 | 23.83 | 0.8 | 48% | 52% | 38% | 465 | 4% | 4% | 26.00 |
| TPF|vah|sw1h | 4,539 | 5.96 | 4.0 | 46% | 56% | 41% | 2,100 | 2% | 1% | 57.00 |
| TPF|vah|week | 157 | 0.21 | 168.0 | 68% | 84% | 66% | 61,702 | 0% | 0% | 305.50 |
| TPF|val|day | 761 | 1.00 | 24.0 | 61% | 80% | 57% | 34,439 | 1% | 0% | 126.50 |
| TPF|val|month | 37 | 0.05 | 696.0 | 59% | 78% | 57% | 73,356 | 0% | 0% | 757.50 |
| TPF|val|sess | 4,531 | 5.95 | 3.0 | 59% | 43% | 51% | 647 | 2% | 1% | 45.00 |
| TPF|val|sw15 | 18,132 | 23.83 | 0.8 | 46% | 54% | 36% | 485 | 3% | 4% | 26.00 |
| TPF|val|sw1h | 4,539 | 5.96 | 4.0 | 44% | 59% | 39% | 2,256 | 2% | 1% | 57.00 |
| TPF|val|week | 157 | 0.21 | 168.0 | 57% | 90% | 55% | 75,521 | 0% | 0% | 305.50 |
| TVP|hvn|day | 68,421 | 89.91 | 5.8 | 71% | 31% | 64% | 173 | 13% | 12% | 2.47 |
| TVP|hvn|sess | 79,803 | 104.87 | 4.5 | 71% | 30% | 62% | 151 | 14% | 15% | 2.42 |
| TVP|lvn|day | 60,206 | 79.11 | 1.8 | 79% | 37% | 65% | 1,297 | 22% | 11% | 0.77 |
| TVP|lvn|sess | 75,626 | 99.38 | 2.8 | 74% | 31% | 60% | 792 | 24% | 14% | 0.72 |
| TVP|poc|day | 9,579 | 12.59 | 1.0 | 74% | 27% | 58% | 156 | 2% | 4% | 2.41 |
| TVP|poc|sess | 15,823 | 20.79 | 0.8 | 73% | 28% | 58% | 131 | 3% | 5% | 4.05 |
| TVP|void|day | 4,912 | 6.45 | 1.2 | 81% | 35% | 59% | 1,005 | 3% | 1% | 0.94 |
| TVP|void|sess | 3,902 | 5.13 | 4.2 | 71% | 33% | 53% | 927 | 2% | 1% | 0.95 |

### Descriptive table: support / resistance hit-rate vs the placebos (level event study)
Per stream <= 1,500 rows (seed 7) whose approach side is consistent with dr; first touch within min(decay, 4 h) of formation; HOLD5 = after the touch the price turns 5 pts back before trading 5 pts through (within 60 min; ambiguous = through). rnd / day = random-level placebo (the stream's own distances permuted) and shuffled-day placebo (distances cyclically shifted >= 20%% of the rows), 200 draws each; rank = share of draws with HOLD5 <= real (1.00 = the real level holds more than every draw). Windows (OLD CAP): X' 2023-04..2024-01, PRE 2024-02..2025-06, HOLD 2025-07..2026-02 (L1M..MID come with the extension). Only windows with >= 60 events are shown.

| stream | n | touch real / rnd | HOLD5 real | rnd | rank rnd | rank day | X' rank (n) | PRE rank (n) | HOLD rank (n) | strength terciles HOLD5 (low / mid / high) |
|---|---|---|---|---|---|---|---|---|---|---|
| TCD|burst | 1500 | 0.90 / 0.88 | 0.518 | 0.515 | 0.57 | 0.59 | 0.49/0.52 (426) | 0.21/0.18 (737) | 0.92/0.91 (281) | 0.54 / 0.48 / 0.54 |
| TCD|cdhi | 1500 | 0.87 / 0.85 | 0.477 | 0.509 | 0.00 | 0.00 | 0.40/0.38 (403) | 0.05/0.05 (716) | 0.03/0.01 (327) | 0.45 / 0.48 / 0.50 |
| TCD|cdlo | 1500 | 0.82 / 0.80 | 0.478 | 0.500 | 0.06 | 0.07 | 0.05/0.07 (441) | 0.12/0.12 (751) | 0.85/0.83 (250) | 0.47 / 0.48 / 0.48 |
| TCD|divbear | 1500 | 0.91 / 0.89 | 0.497 | 0.520 | 0.01 | 0.04 | 0.41/0.36 (440) | 0.00/0.01 (665) | 0.42/0.49 (306) | 0.50 / 0.50 / 0.49 |
| TCD|divbull | 1105 | 0.87 / 0.85 | 0.454 | 0.526 | 0.00 | 0.00 | 0.14/0.21 (361) | 0.00/0.00 (442) | 0.02/0.01 (228) | 0.45 / 0.45 / 0.46 |
| TCP|hvn0|20d | 739 | 0.08 / 0.08 | 0.475 | 0.511 | 0.28 | 0.29 | 0.34/0.29 (212) | 0.20/0.25 (356) | 0.77/0.81 (155) | 0.52 / 0.58 / 0.32 |
| TCP|hvn0|5d | 754 | 0.16 / 0.18 | 0.512 | 0.513 | 0.49 | 0.51 | 0.54/0.53 (213) | 0.94/0.91 (355) | 0.07/0.04 (155) | 0.49 / 0.49 / 0.57 |
| TCP|hvn0|60d | 701 | 0.05 / 0.04 | 0.531 | 0.526 | 0.47 | 0.56 | 0.50/0.53 (189) | 0.81/0.83 (357) | 0.12/0.10 (155) | 0.60 / 0.56 / 0.38 |
| TCP|hvn1|20d | 741 | 0.07 / 0.08 | 0.574 | 0.521 | 0.77 | 0.74 | 0.90/0.91 (213) | 0.98/0.96 (357) | 0.06/0.00 (155) | 0.56 / 0.79 / 0.40 |
| TCP|hvn1|5d | 755 | 0.16 / 0.17 | 0.575 | 0.514 | 0.92 | 0.92 | 0.14/0.14 (213) | 0.88/0.92 (356) | 0.95/0.98 (155) | 0.57 / 0.56 / 0.59 |
| TCP|hvn1|60d | 700 | 0.03 / 0.04 | 0.667 | 0.535 | 0.90 | 0.93 | 0.98/0.99 (188) | 0.94/0.92 (357) | 0.54/0.60 (155) | 1.00 / 0.71 / 0.38 |
| TCP|hvn2|20d | 737 | 0.09 / 0.09 | 0.492 | 0.515 | 0.33 | 0.42 | 0.18/0.24 (213) | 0.84/0.85 (353) | 0.14/0.19 (155) | 0.62 / 0.33 / 0.52 |
| TCP|hvn2|5d | 748 | 0.14 / 0.15 | 0.564 | 0.527 | 0.79 | 0.82 | 0.26/0.27 (210) | 0.79/0.86 (353) | 0.93/0.93 (154) | 0.63 / 0.56 / 0.50 |
| TCP|hvn2|60d | 701 | 0.03 / 0.04 | 0.565 | 0.533 | 0.64 | 0.67 | 0.57/0.65 (189) | 0.86/0.89 (357) | 0.38/0.39 (155) | 0.67 / 1.00 / 0.36 |
| TCP|lvn0|20d | 741 | 0.05 / 0.05 | 0.421 | 0.518 | 0.09 | 0.12 | 0.69/0.58 (213) | 0.10/0.06 (357) | 0.15/0.15 (155) | 0.33 / 0.56 / 0.50 |
| TCP|lvn0|5d | 756 | 0.08 / 0.09 | 0.439 | 0.524 | 0.09 | 0.09 | 0.17/0.12 (213) | 0.55/0.51 (357) | 0.06/0.09 (155) | 0.38 / 0.44 / 0.54 |
| TCP|lvn0|60d | 701 | 0.02 / 0.02 | 0.500 | 0.520 | 0.49 | 0.44 |  | 0.60/0.60 (357) | 0.30/0.23 (155) | 0.83 / 0.25 / 0.00 |
| TCP|lvn1|20d | 739 | 0.05 / 0.06 | 0.450 | 0.518 | 0.21 | 0.11 | 0.23/0.26 (213) | 0.25/0.17 (355) | 0.86/0.82 (155) | 0.41 / 0.50 / 0.46 |
| TCP|lvn1|5d | 753 | 0.11 / 0.10 | 0.593 | 0.533 | 0.85 | 0.91 | 0.80/0.83 (212) | 0.67/0.70 (355) | 0.59/0.56 (155) | 0.58 / 0.62 / 0.56 |
| TCP|lvn1|60d | 701 | 0.03 / 0.04 | 0.421 | 0.520 | 0.17 | 0.16 | 0.66/0.54 (189) | 0.14/0.20 (357) | 0.03/0.06 (155) | 0.62 / 0.25 / 0.33 |
| TCP|lvn2|20d | 738 | 0.05 / 0.06 | 0.579 | 0.524 | 0.76 | 0.71 | 0.94/0.95 (213) | 0.06/0.03 (354) | 0.81/0.78 (155) | 0.60 / 0.57 / 0.56 |
| TCP|lvn2|5d | 734 | 0.11 / 0.12 | 0.562 | 0.524 | 0.77 | 0.79 | 0.69/0.70 (208) | 0.59/0.62 (347) | 0.57/0.57 (149) | 0.60 / 0.52 / 0.53 |
| TCP|lvn2|60d | 701 | 0.03 / 0.03 | 0.333 | 0.517 | 0.07 | 0.08 | 0.36/0.39 (189) | 0.13/0.15 (357) | 0.14/0.13 (155) | 0.43 / 0.29 / 0.25 |
| TCP|poc|20d | 741 | 0.07 / 0.09 | 0.473 | 0.517 | 0.26 | 0.20 | 0.68/0.60 (213) | 0.29/0.27 (357) | 0.23/0.16 (155) | 0.43 / 0.48 / 0.50 |
| TCP|poc|5d | 754 | 0.15 / 0.17 | 0.478 | 0.517 | 0.17 | 0.27 | 0.54/0.51 (213) | 0.01/0.06 (355) | 0.57/0.70 (155) | 0.42 / 0.54 / 0.46 |
| TCP|poc|60d | 701 | 0.04 / 0.04 | 0.552 | 0.535 | 0.55 | 0.68 | 0.12/0.24 (189) | 0.92/0.97 (357) | 0.37/0.34 (155) | 0.50 / 0.53 / 0.62 |
| TCP|vah|20d | 741 | 0.08 / 0.09 | 0.500 | 0.518 | 0.42 | 0.33 | 0.24/0.17 (213) | 0.58/0.59 (357) | 0.53/0.59 (155) | 0.54 / 0.38 / 0.57 |
| TCP|vah|5d | 756 | 0.13 / 0.14 | 0.625 | 0.526 | 0.98 | 0.98 | 0.74/0.66 (213) | 0.75/0.82 (357) | 0.99/1.00 (155) | 0.57 / 0.63 / 0.69 |
| TCP|vah|60d | 700 | 0.06 / 0.06 | 0.561 | 0.516 | 0.72 | 0.75 | 0.14/0.10 (189) | 0.99/0.96 (356) | 0.15/0.14 (155) | 0.50 / 0.53 / 0.67 |
| TCP|val|20d | 741 | 0.04 / 0.03 | 0.607 | 0.515 | 0.81 | 0.76 | 0.64/0.58 (213) | 0.90/0.88 (357) | 0.56/0.57 (155) | 0.60 / 0.56 / 0.67 |
| TCP|val|5d | 756 | 0.09 / 0.10 | 0.443 | 0.528 | 0.07 | 0.06 | 0.15/0.15 (213) | 0.28/0.26 (357) | 0.11/0.09 (155) | 0.48 / 0.40 / 0.42 |
| TCP|val|60d | 701 | 0.01 / 0.01 | 0.200 | 0.533 | 0.04 | 0.02 | 0.38/0.26 (189) | 0.05/0.05 (357) | 0.88/0.95 (155) | 0.40 / 0.00 / 0.00 |
| TDA|abs|15m | 227 | 0.91 / 0.87 | 0.537 | 0.502 | 0.93 | 0.87 | 0.33/0.40 (90) | 0.99/1.00 (78) |  | 0.55 / 0.61 / 0.46 |
| TDA|abs|5m | 1438 | 0.94 / 0.93 | 0.509 | 0.503 | 0.69 | 0.72 | 0.72/0.78 (383) | 0.39/0.38 (665) | 0.78/0.80 (304) | 0.49 / 0.48 / 0.56 |
| TLP|cl25|4h | 1500 | 0.98 / 0.97 | 0.511 | 0.488 | 1.00 | 1.00 | 1.00/0.99 (617) | 0.71/0.70 (529) | 0.95/0.96 (273) | 0.49 / 0.50 / 0.55 |
| TLP|p100|1h | 1500 | 0.96 / 0.95 | 0.504 | 0.498 | 0.74 | 0.64 | 0.77/0.71 (414) | 0.85/0.73 (599) | 0.27/0.20 (468) | 0.50 / 0.48 / 0.53 |
| TLP|p100|4h | 1500 | 0.97 / 0.97 | 0.505 | 0.497 | 0.78 | 0.72 | 0.77/0.72 (414) | 0.87/0.82 (599) | 0.29/0.23 (468) | 0.50 / 0.48 / 0.53 |
| TLP|p25|1h | 1500 | 0.98 / 0.96 | 0.526 | 0.516 | 0.90 | 0.88 | 0.81/0.68 (497) | 0.71/0.77 (611) | 0.81/0.72 (319) | 0.53 / 0.56 / 0.49 |
| TLP|p25|4h | 1500 | 0.98 / 0.98 | 0.538 | 0.523 | 0.95 | 0.97 | 0.94/0.88 (498) | 0.86/0.82 (611) | 0.77/0.80 (319) | 0.55 / 0.55 / 0.51 |
| TLP|p50|1h | 1500 | 0.97 / 0.95 | 0.514 | 0.506 | 0.81 | 0.79 | 0.71/0.66 (442) | 0.70/0.76 (606) | 0.63/0.66 (404) | 0.53 / 0.48 / 0.52 |
| TLP|p50|4h | 1500 | 0.98 / 0.97 | 0.513 | 0.505 | 0.79 | 0.78 | 0.67/0.64 (442) | 0.73/0.79 (606) | 0.59/0.65 (404) | 0.53 / 0.49 / 0.52 |
| TLQ|EQL|rel|15m | 1500 | 0.58 / 0.58 | 0.411 | 0.519 | 0.00 | 0.00 | 0.06/0.04 (412) | 0.00/0.00 (737) | 0.00/0.00 (293) | 0.38 / 0.43 / 0.42 |
| TLQ|EQL|rel|1h | 1184 | 0.36 / 0.38 | 0.419 | 0.526 | 0.00 | 0.00 | 0.03/0.04 (358) | 0.00/0.00 (549) | 0.35/0.33 (224) | 0.44 / 0.47 / 0.32 |
| TLQ|EQL|tight|15m | 1023 | 0.63 / 0.61 | 0.447 | 0.516 | 0.00 | 0.00 | 0.01/0.01 (392) | 0.01/0.01 (426) | 0.41/0.41 (165) | 0.43 / 0.51 / 0.40 |
| TLQ|EQL|tight|1h | 85 | 0.47 / 0.46 | 0.475 | 0.512 | 0.30 | 0.34 |  |  |  |  |
| TLQ|KZ|kz|asia | 1500 | 0.55 / 0.54 | 0.454 | 0.510 | 0.00 | 0.00 | 0.04/0.04 (418) | 0.01/0.00 (706) | 0.46/0.50 (305) | 0.45 / 0.41 / 0.48 |
| TLQ|KZ|kz|lc | 1500 | 0.50 / 0.51 | 0.439 | 0.545 | 0.00 | 0.00 | 0.23/0.21 (415) | 0.00/0.00 (707) | 0.00/0.00 (305) | 0.41 / 0.45 / 0.45 |
| TLQ|KZ|kz|london | 1500 | 0.55 / 0.56 | 0.453 | 0.516 | 0.00 | 0.00 | 0.72/0.61 (420) | 0.00/0.00 (706) | 0.00/0.00 (304) | 0.38 / 0.43 / 0.55 |
| TLQ|KZ|kz|ny | 1500 | 0.57 / 0.58 | 0.433 | 0.557 | 0.00 | 0.00 | 0.23/0.21 (418) | 0.00/0.00 (707) | 0.00/0.00 (303) | 0.41 / 0.43 / 0.47 |
| TLQ|PDX|day | 1500 | 0.15 / 0.18 | 0.370 | 0.511 | 0.00 | 0.00 | 0.03/0.06 (420) | 0.00/0.00 (704) | 0.14/0.12 (306) | 0.41 / 0.37 / 0.32 |
| TLQ|PDX|rth | 1500 | 0.17 / 0.18 | 0.407 | 0.505 | 0.00 | 0.00 | 0.32/0.35 (418) | 0.00/0.00 (704) | 0.00/0.00 (307) | 0.35 / 0.44 / 0.44 |
| TLQ|PDX|week | 312 | 0.06 / 0.10 | 0.611 | 0.501 | 0.91 | 0.91 | 0.60/0.62 (88) | 0.94/0.96 (148) | 0.75/0.72 (62) | 0.62 / 0.67 / 0.57 |
| TLQ|SES|asia | 1500 | 0.47 / 0.49 | 0.393 | 0.506 | 0.00 | 0.00 | 0.07/0.04 (420) | 0.00/0.00 (702) | 0.07/0.03 (306) | 0.40 / 0.37 / 0.40 |
| TLQ|SES|close | 1481 | 0.38 / 0.41 | 0.423 | 0.507 | 0.00 | 0.00 | 0.06/0.07 (411) | 0.00/0.00 (700) | 0.01/0.00 (300) | 0.44 / 0.40 / 0.44 |
| TLQ|SES|london | 1500 | 0.67 / 0.66 | 0.459 | 0.514 | 0.00 | 0.00 | 0.07/0.04 (419) | 0.01/0.00 (708) | 0.14/0.12 (303) | 0.49 / 0.42 / 0.46 |
| TLQ|SES|nyam | 1500 | 0.44 / 0.45 | 0.398 | 0.547 | 0.00 | 0.00 | 0.07/0.04 (415) | 0.00/0.00 (707) | 0.00/0.00 (305) | 0.34 / 0.39 / 0.48 |
| TLQ|SES|nypm | 1500 | 0.40 / 0.43 | 0.482 | 0.539 | 0.00 | 0.00 | 0.35/0.39 (419) | 0.00/0.01 (699) | 0.10/0.09 (309) | 0.44 / 0.48 / 0.53 |
| TLQ|SES|on | 1500 | 0.56 / 0.55 | 0.484 | 0.567 | 0.00 | 0.00 | 0.00/0.01 (420) | 0.00/0.00 (703) | 0.28/0.28 (306) | 0.54 / 0.47 / 0.44 |
| TLQ|SES|pre | 1500 | 0.78 / 0.76 | 0.513 | 0.557 | 0.01 | 0.00 | 0.41/0.41 (418) | 0.00/0.00 (705) | 0.12/0.12 (307) | 0.55 / 0.48 / 0.51 |
| TLQ|SES|rth | 1500 | 0.17 / 0.18 | 0.407 | 0.505 | 0.00 | 0.00 | 0.32/0.35 (418) | 0.00/0.00 (704) | 0.00/0.00 (307) | 0.35 / 0.44 / 0.44 |
| TLQ|SWG|f3|15m | 1500 | 0.70 / 0.66 | 0.452 | 0.522 | 0.00 | 0.00 | 0.27/0.17 (419) | 0.00/0.00 (713) | 0.10/0.01 (310) | 0.41 / 0.47 / 0.48 |
| TLQ|SWG|f3|1h | 1500 | 0.45 / 0.47 | 0.405 | 0.525 | 0.00 | 0.00 | 0.12/0.10 (411) | 0.00/0.00 (728) | 0.01/0.01 (302) | 0.37 / 0.42 / 0.42 |
| TLQ|SWG|f5|15m | 1500 | 0.59 / 0.58 | 0.467 | 0.528 | 0.00 | 0.00 | 0.14/0.15 (413) | 0.00/0.00 (713) | 0.02/0.04 (316) | 0.46 / 0.46 / 0.48 |
| TLQ|SWG|f5|1h | 1500 | 0.36 / 0.39 | 0.410 | 0.529 | 0.00 | 0.00 | 0.34/0.35 (415) | 0.00/0.00 (741) | 0.02/0.01 (283) | 0.36 / 0.40 / 0.47 |
| TLQ|SWG|f7|15m | 1500 | 0.55 / 0.54 | 0.430 | 0.532 | 0.00 | 0.00 | 0.01/0.01 (415) | 0.00/0.00 (712) | 0.00/0.00 (317) | 0.42 / 0.42 / 0.45 |
| TLQ|SWG|f7|1h | 1500 | 0.31 / 0.33 | 0.394 | 0.539 | 0.00 | 0.00 | 0.01/0.01 (444) | 0.00/0.00 (706) | 0.06/0.02 (293) | 0.38 / 0.41 / 0.40 |
| TPF|hvn0|day | 758 | 0.38 / 0.40 | 0.486 | 0.499 | 0.33 | 0.34 | 0.60/0.53 (211) | 0.69/0.68 (357) | 0.15/0.20 (154) | 0.53 / 0.47 / 0.46 |
| TPF|hvn0|sess | 1500 | 0.67 / 0.66 | 0.511 | 0.514 | 0.40 | 0.38 | 0.49/0.50 (419) | 0.47/0.51 (717) | 0.27/0.21 (298) | 0.55 / 0.49 / 0.49 |
| TPF|hvn0|sw15 | 1500 | 0.51 / 0.51 | 0.509 | 0.518 | 0.31 | 0.33 | 0.03/0.04 (403) | 0.66/0.61 (698) | 0.48/0.52 (342) | 0.48 / 0.49 / 0.57 |
| TPF|hvn0|sw1h | 1500 | 0.47 / 0.47 | 0.521 | 0.521 | 0.49 | 0.48 | 0.92/0.94 (411) | 0.26/0.17 (701) | 0.06/0.10 (326) | 0.50 / 0.58 / 0.47 |
| TPF|hvn0|week | 156 | 0.15 / 0.19 | 0.375 | 0.497 | 0.09 | 0.10 |  | 0.21/0.20 (73) |  | 0.29 / 0.38 / 0.44 |
| TPF|hvn1|day | 729 | 0.28 / 0.32 | 0.530 | 0.511 | 0.74 | 0.76 | 0.53/0.53 (202) | 0.74/0.73 (344) | 0.66/0.67 (149) | 0.52 / 0.55 / 0.52 |
| TPF|hvn1|sess | 1500 | 0.57 / 0.59 | 0.554 | 0.518 | 0.99 | 0.97 | 0.99/0.98 (394) | 0.91/0.88 (736) | 0.43/0.47 (306) | 0.54 / 0.55 / 0.58 |
| TPF|hvn1|sw15 | 1500 | 0.47 / 0.50 | 0.523 | 0.520 | 0.53 | 0.59 | 0.73/0.70 (344) | 0.58/0.74 (737) | 0.43/0.45 (363) | 0.51 / 0.52 / 0.54 |
| TPF|hvn1|sw1h | 1500 | 0.45 / 0.46 | 0.518 | 0.519 | 0.49 | 0.53 | 0.53/0.47 (378) | 0.77/0.76 (735) | 0.28/0.28 (327) | 0.50 / 0.51 / 0.55 |
| TPF|hvn1|week | 157 | 0.19 / 0.23 | 0.567 | 0.474 | 0.88 | 0.83 |  | 0.91/0.87 (74) |  | 0.55 / 0.64 / 0.50 |
| TPF|hvn2|day | 646 | 0.24 / 0.26 | 0.539 | 0.516 | 0.75 | 0.76 | 0.81/0.81 (172) | 0.29/0.20 (304) | 0.75/0.77 (140) | 0.61 / 0.51 / 0.50 |
| TPF|hvn2|sess | 1500 | 0.49 / 0.50 | 0.536 | 0.530 | 0.65 | 0.65 | 0.80/0.81 (339) | 0.19/0.22 (773) | 0.83/0.79 (327) | 0.56 / 0.52 / 0.53 |
| TPF|hvn2|sw15 | 1500 | 0.42 / 0.43 | 0.566 | 0.532 | 0.96 | 0.99 | 0.87/0.89 (294) | 0.87/0.91 (778) | 0.91/0.85 (381) | 0.59 / 0.55 / 0.56 |
| TPF|hvn2|sw1h | 1500 | 0.44 / 0.43 | 0.525 | 0.530 | 0.41 | 0.40 | 0.78/0.69 (338) | 0.27/0.33 (748) | 0.23/0.20 (358) | 0.52 / 0.56 / 0.50 |
| TPF|hvn2|week | 157 | 0.17 / 0.18 | 0.556 | 0.501 | 0.71 | 0.85 |  | 0.23/0.30 (74) |  | 0.78 / 0.62 / 0.30 |
| TPF|lvn0|day | 741 | 0.20 / 0.24 | 0.520 | 0.523 | 0.45 | 0.55 | 0.54/0.52 (206) | 0.77/0.78 (349) | 0.07/0.06 (150) | 0.56 / 0.52 / 0.41 |
| TPF|lvn0|sess | 1500 | 0.53 / 0.55 | 0.517 | 0.530 | 0.20 | 0.18 | 0.83/0.81 (392) | 0.13/0.14 (744) | 0.27/0.27 (297) | 0.51 / 0.53 / 0.51 |
| TPF|lvn0|sw15 | 1500 | 0.50 / 0.50 | 0.528 | 0.519 | 0.70 | 0.60 | 0.59/0.55 (362) | 0.48/0.34 (734) | 0.51/0.55 (351) | 0.54 / 0.51 / 0.54 |
| TPF|lvn0|sw1h | 1500 | 0.46 / 0.47 | 0.539 | 0.513 | 0.93 | 0.91 | 0.64/0.58 (392) | 0.98/0.97 (705) | 0.32/0.21 (346) | 0.52 / 0.56 / 0.54 |
| TPF|lvn0|week | 157 | 0.09 / 0.11 | 0.429 | 0.518 | 0.24 | 0.17 |  | 0.58/0.59 (74) |  | 0.43 / 0.33 / 0.50 |
| TPF|lvn1|day | 683 | 0.23 / 0.25 | 0.545 | 0.519 | 0.75 | 0.80 | 0.51/0.50 (185) | 0.99/0.98 (318) | 0.25/0.26 (146) | 0.55 / 0.53 / 0.57 |
| TPF|lvn1|sess | 1500 | 0.53 / 0.53 | 0.559 | 0.532 | 0.94 | 0.94 | 0.85/0.87 (361) | 0.82/0.87 (758) | 0.85/0.81 (324) | 0.54 / 0.57 / 0.58 |
| TPF|lvn1|sw15 | 1500 | 0.46 / 0.46 | 0.552 | 0.528 | 0.91 | 0.88 | 0.59/0.52 (290) | 0.86/0.84 (780) | 0.81/0.77 (380) | 0.56 / 0.57 / 0.53 |
| TPF|lvn1|sw1h | 1500 | 0.41 / 0.43 | 0.567 | 0.525 | 0.98 | 0.98 | 0.74/0.76 (362) | 0.96/0.98 (757) | 0.60/0.61 (327) | 0.58 / 0.54 / 0.58 |
| TPF|lvn1|week | 157 | 0.16 / 0.16 | 0.600 | 0.511 | 0.82 | 0.81 |  | 0.38/0.39 (74) |  | 0.70 / 0.50 / 0.60 |
| TPF|lvn2|day | 600 | 0.25 / 0.27 | 0.493 | 0.516 | 0.27 | 0.27 | 0.90/0.85 (157) | 0.35/0.35 (286) | 0.04/0.02 (127) | 0.53 / 0.56 / 0.31 |
| TPF|lvn2|sess | 1500 | 0.51 / 0.51 | 0.528 | 0.533 | 0.42 | 0.43 | 0.99/0.98 (284) | 0.07/0.04 (800) | 0.26/0.23 (353) | 0.56 / 0.52 / 0.48 |
| TPF|lvn2|sw15 | 1500 | 0.43 / 0.44 | 0.536 | 0.523 | 0.75 | 0.70 | 0.98/0.98 (244) | 0.45/0.40 (833) | 0.28/0.34 (374) | 0.53 / 0.55 / 0.52 |
| TPF|lvn2|sw1h | 1500 | 0.39 / 0.41 | 0.608 | 0.527 | 1.00 | 1.00 | 0.93/0.95 (303) | 1.00/0.99 (785) | 0.97/0.98 (360) | 0.60 / 0.62 / 0.60 |
| TPF|lvn2|week | 153 | 0.17 / 0.18 | 0.423 | 0.501 | 0.20 | 0.26 |  | 0.41/0.47 (72) |  | 0.55 / 0.25 / 0.43 |
| TPF|poc|day | 759 | 0.37 / 0.39 | 0.473 | 0.493 | 0.23 | 0.18 | 0.51/0.49 (212) | 0.64/0.56 (356) | 0.04/0.07 (155) | 0.43 / 0.43 / 0.53 |
| TPF|poc|sess | 1500 | 0.66 / 0.67 | 0.519 | 0.519 | 0.50 | 0.55 | 0.70/0.71 (421) | 0.54/0.62 (712) | 0.06/0.07 (301) | 0.53 / 0.52 / 0.51 |
| TPF|poc|sw15 | 1500 | 0.51 / 0.52 | 0.507 | 0.523 | 0.20 | 0.23 | 0.64/0.68 (406) | 0.23/0.24 (697) | 0.12/0.14 (343) | 0.53 / 0.46 / 0.53 |
| TPF|poc|sw1h | 1500 | 0.46 / 0.46 | 0.527 | 0.522 | 0.64 | 0.57 | 0.23/0.22 (418) | 0.81/0.79 (709) | 0.47/0.52 (311) | 0.52 / 0.53 / 0.52 |
| TPF|poc|week | 156 | 0.17 / 0.18 | 0.423 | 0.488 | 0.26 | 0.24 |  | 0.66/0.53 (73) |  | 0.50 / 0.60 / 0.25 |
| TPF|vah|day | 760 | 0.27 / 0.33 | 0.507 | 0.504 | 0.55 | 0.54 | 0.33/0.29 (213) | 0.89/0.85 (357) | 0.08/0.10 (154) | 0.49 / 0.56 / 0.46 |
| TPF|vah|sess | 1500 | 0.63 / 0.63 | 0.508 | 0.518 | 0.27 | 0.27 | 0.41/0.36 (416) | 0.62/0.63 (717) | 0.20/0.24 (299) | 0.50 / 0.50 / 0.53 |
| TPF|vah|sw15 | 1500 | 0.46 / 0.49 | 0.509 | 0.515 | 0.34 | 0.38 | 0.87/0.80 (401) | 0.06/0.03 (703) | 0.80/0.77 (341) | 0.47 / 0.51 / 0.56 |
| TPF|vah|sw1h | 1500 | 0.42 / 0.45 | 0.493 | 0.525 | 0.03 | 0.04 | 0.04/0.06 (411) | 0.00/0.02 (701) | 0.97/0.94 (326) | 0.49 / 0.49 / 0.50 |
| TPF|vah|week | 157 | 0.16 / 0.17 | 0.640 | 0.515 | 0.90 | 0.95 |  | 0.66/0.63 (74) |  | 0.64 / 0.57 / 0.71 |
| TPF|val|day | 761 | 0.20 / 0.23 | 0.454 | 0.526 | 0.04 | 0.01 | 0.43/0.41 (213) | 0.08/0.06 (357) | 0.12/0.12 (155) | 0.49 / 0.47 / 0.39 |
| TPF|val|sess | 1500 | 0.56 / 0.57 | 0.529 | 0.534 | 0.36 | 0.32 | 0.17/0.11 (421) | 0.47/0.49 (727) | 0.62/0.69 (288) | 0.53 / 0.53 / 0.53 |
| TPF|val|sw15 | 1500 | 0.45 / 0.47 | 0.519 | 0.528 | 0.30 | 0.40 | 0.46/0.49 (401) | 0.45/0.42 (711) | 0.25/0.35 (335) | 0.55 / 0.47 / 0.54 |
| TPF|val|sw1h | 1500 | 0.42 / 0.43 | 0.527 | 0.525 | 0.54 | 0.55 | 0.51/0.55 (422) | 0.47/0.52 (706) | 0.79/0.86 (311) | 0.52 / 0.54 / 0.51 |
| TPF|val|week | 157 | 0.10 / 0.13 | 0.312 | 0.503 | 0.05 | 0.01 |  | 0.12/0.13 (74) |  | 0.20 / 0.40 / 0.33 |
| TVP|hvn|day | 1500 | 0.65 / 0.66 | 0.518 | 0.521 | 0.41 | 0.41 | 0.37/0.40 (293) | 0.52/0.47 (797) | 0.32/0.40 (362) | 0.57 / 0.50 / 0.47 |
| TVP|hvn|sess | 1500 | 0.70 / 0.70 | 0.508 | 0.515 | 0.28 | 0.33 | 0.07/0.09 (305) | 0.72/0.86 (789) | 0.36/0.35 (356) | 0.49 / 0.53 / 0.51 |
| TVP|lvn|day | 1500 | 0.62 / 0.53 | 0.555 | 0.529 | 0.93 | 0.90 | 0.89/0.86 (326) | 0.86/0.84 (771) | 0.70/0.66 (354) | 0.57 / 0.55 / 0.54 |
| TVP|lvn|sess | 1500 | 0.70 / 0.59 | 0.542 | 0.524 | 0.87 | 0.96 | 0.54/0.60 (317) | 0.97/0.99 (782) | 0.21/0.28 (351) | 0.51 / 0.55 / 0.57 |
| TVP|poc|day | 1500 | 0.75 / 0.73 | 0.477 | 0.480 | 0.41 | 0.36 | 0.41/0.43 (400) | 0.75/0.83 (739) | 0.19/0.15 (298) | 0.50 / 0.46 / 0.48 |
| TVP|poc|sess | 1500 | 0.72 / 0.72 | 0.498 | 0.499 | 0.48 | 0.42 | 0.85/0.86 (404) | 0.26/0.28 (725) | 0.35/0.35 (314) | 0.50 / 0.48 / 0.51 |
| TVP|void|day | 1500 | 0.65 / 0.54 | 0.526 | 0.535 | 0.34 | 0.32 | 0.45/0.45 (228) | 0.34/0.41 (913) | 0.32/0.38 (312) | 0.59 / 0.56 / 0.45 |
| TVP|void|sess | 1500 | 0.67 / 0.57 | 0.575 | 0.544 | 0.96 | 0.98 | 0.40/0.46 (185) | 0.97/0.99 (941) | 0.89/0.87 (333) | 0.59 / 0.55 / 0.59 |

## 3. Measured liquidity pools (stop volume)
Level sources are the POI-store rows (swing f3 / f5 / f7 on 15-m and 1-h, equal H/L tight and relative on 15-m and 1-h, previous-session, killzone and prior-day / RTH / week H/L). BREAK = the first second with price >= 1 tick beyond the level. POOL = aggressor volume that printed within 2 ticks beyond the level in the 60 s from the break second (buy aggressor for a high, sell aggressor for a low). opp = the opposite aggressor in the same band (liquidity that stood there); beyond = all volume beyond the level in the window.

| level type | levels | broken before decay | pool P10 | P50 | P90 | pool < 10 | pool >= 100 | pool >= 300 | opposite P50 | volume beyond P50 | median excursion 15 min (pts) | re-claimed in 5 min |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| EQL|rel|15m | 5148 | 82% | 5 | 21 | 79 | 24% | 6% | 0% | 11 | 300 | 11.2 | 47% |
| EQL|rel|1h | 1184 | 68% | 6 | 26 | 97 | 16% | 9% | 0% | 15 | 557 | 15.5 | 44% |
| EQL|tight|15m | 1024 | 86% | 5 | 21 | 76 | 21% | 6% | 0% | 9 | 205 | 9.0 | 48% |
| EQL|tight|1h | 85 | 66% | 6 | 24 | 90 | 14% | 4% | 0% | 12 | 505 | 15.0 | 32% |
| KZ|kz_asia | 1548 | 87% | 4 | 15 | 49 | 29% | 2% | 0% | 7 | 190 | 9.1 | 49% |
| KZ|kz_lc | 1544 | 70% | 9 | 38 | 106 | 11% | 12% | 0% | 27 | 1028 | 15.6 | 49% |
| KZ|kz_london | 1546 | 83% | 5 | 21 | 74 | 24% | 5% | 0% | 11 | 302 | 11.0 | 51% |
| KZ|kz_ny | 1548 | 70% | 8 | 44 | 117 | 12% | 16% | 0% | 32 | 1451 | 20.8 | 47% |
| PDX|day | 1546 | 51% | 3 | 23 | 88 | 23% | 8% | 0% | 14 | 610 | 15.8 | 42% |
| PDX|rth | 1544 | 56% | 4 | 25 | 91 | 21% | 9% | 0% | 14 | 641 | 15.5 | 44% |
| PDX|week | 312 | 52% | 2 | 30 | 103 | 20% | 10% | 0% | 17 | 990 | 20.0 | 45% |
| SES|asia | 1548 | 81% | 5 | 19 | 67 | 22% | 4% | 0% | 10 | 291 | 12.2 | 47% |
| SES|close | 1484 | 82% | 1 | 14 | 62 | 38% | 4% | 0% | 7 | 264 | 11.5 | 44% |
| SES|london | 1546 | 76% | 6 | 34 | 100 | 17% | 10% | 0% | 22 | 832 | 18.8 | 49% |
| SES|nyam | 1544 | 63% | 9 | 40 | 113 | 12% | 15% | 0% | 27 | 1132 | 15.8 | 48% |
| SES|nypm | 1544 | 73% | 5 | 29 | 99 | 18% | 10% | 0% | 18 | 614 | 15.2 | 47% |
| SES|on | 1548 | 68% | 12 | 50 | 124 | 7% | 18% | 0% | 36 | 1442 | 25.5 | 46% |
| SES|pre | 1548 | 84% | 11 | 47 | 122 | 9% | 17% | 0% | 36 | 1589 | 27.0 | 48% |
| SES|rth | 1544 | 56% | 4 | 25 | 91 | 21% | 9% | 0% | 14 | 641 | 15.5 | 44% |
| SWG|f3|15m | 31071 | 87% | 4 | 17 | 70 | 28% | 5% | 0% | 9 | 213 | 10.2 | 48% |
| SWG|f3|1h | 7813 | 75% | 5 | 21 | 81 | 23% | 7% | 0% | 11 | 361 | 12.5 | 47% |
| SWG|f5|15m | 18447 | 83% | 4 | 19 | 75 | 25% | 5% | 0% | 10 | 263 | 10.8 | 48% |
| SWG|f5|1h | 4607 | 69% | 5 | 23 | 87 | 20% | 7% | 0% | 13 | 464 | 13.8 | 46% |
| SWG|f7|15m | 13181 | 80% | 5 | 20 | 77 | 24% | 6% | 0% | 11 | 296 | 11.5 | 48% |
| SWG|f7|1h | 3311 | 64% | 6 | 26 | 93 | 17% | 9% | 0% | 15 | 578 | 15.2 | 46% |

By the D6 session of the break (aggressor pool, all types): asia P50 11 (n 20869); close P50 39 (n 5494); london P50 15 (n 25458); nyam P50 52 (n 17354); nypm P50 44 (n 9821); pre P50 21 (n 6617).

Does a bigger pool predict the move beyond it? Terciles within (level type, calendar quarter); excursion = median of the maximum move beyond the level in minutes 1-15 after the 60-s window (pts); re-claim = close 5 min after the break is back on the original side; null = 200 shuffles of the outcomes within (type, quarter) (event-level p, not cluster-adjusted: indicative only).

| pool measure | window | n | excursion bottom / mid / top tercile | top - bottom | re-claim bottom / top | top - bottom | p(excursion) | p(re-claim) |
|---|---|---|---|---|---|---|---|---|
| realised pool (same window, NOT usable ahead) | ALL | 85493 | 9.75 / 10.00 / 16.25 | +6.50 | 0.470 / 0.480 | +0.010 | 0.000 | 0.005 |
| realised pool (same window, NOT usable ahead) | HOLD | 17259 | 11.50 / 10.75 / 18.75 | +7.25 | 0.482 / 0.455 | -0.027 | 0.000 | 0.005 |
| causal expected pool (strength of the stream row) | ALL | 85467 | 11.75 / 12.00 / 11.50 | -0.25 | 0.469 / 0.479 | +0.010 | 0.335 | 0.010 |
| causal expected pool (strength of the stream row) | HOLD | 17259 | 12.00 / 13.75 / 13.25 | +1.25 | 0.460 / 0.486 | +0.026 | 0.000 | 0.015 |
| volume beyond in the window (NOT usable ahead) | ALL | 85493 | 5.25 / 10.50 / 25.25 | +20.00 | 0.616 / 0.369 | -0.247 | 0.000 | 0.000 |
| volume beyond in the window (NOT usable ahead) | HOLD | 17259 | 6.25 / 12.00 / 29.75 | +23.50 | 0.602 / 0.376 | -0.226 | 0.000 | 0.000 |

Reading: the stop pools on NQ are small in contracts (tens, not hundreds) because the 2-tick band beyond a level is thin and the aggressor tape of the break second is mostly the move itself; the realised volume beyond the level is what separates a sweep (re-claimed 60% when the volume beyond is lowest) from a real break (37% when highest) - but it is only known after the break.

## 5. Zone-density features at the signal (defined now; ZL-3 scores)
Definition (density.py docstring): a row is live at the signal second if formed (ek <= kin), not decayed (cap > kin) and fresh (end > kin). AHEAD distance = near edge in the travel direction from the entry (0 inside the zone); BEHIND = near edge on the stop side; direction-bearing rows follow poi_core. n_ah / n_bh {20,40,60} count rows (stacked lines count several times), nb_ah / nb_bh count distinct 2-pt buckets within 60 pts, d_ah / d_bh / d_any nearest distances, ratio40 = (n_ah40 + 1) / (n_bh40 + 1). Not limited to the signal's own target / stop distances. Files `features_tape/density_<set>.parquet` (row order = poi_store trades, key tid): S8 (the 8 coded lines), S11old (S8 + the CF-A 1-s profile lines), S11T (S8 + the tape-built three), TAPE (99 tape streams, no 1-h / 25-lot print lines, no pool lines), POOL30 (pool lines with expected pool >= 30 contracts), ALLZ (S11T + TAPE + POOL30). The L2 zones of ZL-1 are added as a further set when `streams_book` lands (same kernel, `density.feats`).

| set | lines | share with a fresh line <= 20 pts ahead | behind | mean rows <= 40 ahead | behind | mean rows <= 60 ahead | distinct 2-pt buckets ahead | nearest ahead median pts | nearest any median | share nearest any <= 5 pts | ratio40 median [P10, P90] | corr(n ahead 40, n behind 40) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S8 | 8 | 15% | 9% | 0.43 | 0.45 | 0.62 | 0.58 | 40.8 | 44.4 | 3% | 1.00 [0.50, 2.00] | 0.05 |
| S11old | 11 | 19% | 11% | 0.58 | 0.61 | 0.82 | 0.77 | 34.6 | 39.4 | 4% | 1.00 [0.50, 2.00] | 0.11 |
| S11T | 11 | 20% | 11% | 0.59 | 0.62 | 0.83 | 0.79 | 33.6 | 38.8 | 4% | 1.00 [0.50, 2.00] | 0.11 |
| TAPE | 99 | 67% | 40% | 5.47 | 4.38 | 8.16 | 5.60 | 11.5 | 9.5 | 27% | 1.20 [0.27, 7.00] | 0.13 |
| POOL30 | 25 | 9% | 1% | 0.58 | 0.14 | 0.93 | 0.42 | 59.2 | 67.0 | 1% | 1.00 [1.00, 3.00] | 0.26 |
| ALLZ | 135 | 70% | 41% | 6.64 | 5.14 | 9.93 | 6.30 | 10.8 | 9.0 | 29% | 1.33 [0.29, 8.00] | 0.23 |

## 4. Stream definitions, parameters and the exact LIVE definition (what D7 computes from its own print tape; what needs the daily zones file)
D7 has the live print tape (price, size, aggressor side) and the 1-s bars; none of the streams below needs the book. Live prices are the raw contract prices (the path-frame offset is a research artefact). All rows are knowable at tk = last second used + 1; D7 recomputes them at the same clock times.

| family | stream(s) | definition (parameters) | strength | decay | D7 live from its own tape | needs the daily zones file |
|---|---|---|---|---|---|---|
| TPF closed-anchor profile lines | TPF\|{poc,vah,val,hvn0-2,lvn0-2}\|{sess,day,week,month,sw15,sw1h} (54) | CF-A rule on the true tick tape: 0.25 bins, POC (ties to the volume-weighted centre), 70% value area from the POC adding the heavier 2-tick side, gaussian sigma 2 pts, HVN = peaks prominence >= 10% of max (top 3 by smoothed volume), LVN = troughs prominence >= 8% (3 lowest). Anchors: previous completed D6 session / Globex day (18:00 ET) / ISO week / label-day month / leg between consecutive confirmed fractal-2/2 pivots on 15-m (sw15) and 1-h (sw1h) bars; knowable when the segment is complete (swing: when the second pivot is confirmed by 2 closed bars). Includes the three lines group 10 lacks: **TPF\|vah\|sw15, TPF\|lvn1\|sw1h, TPF\|hvn0\|sw1h** | poc: POC share of volume (%); vah/val: value-area width (pts); hvn: smoothed peak / median; lvn: 1 - trough / median | next row of the anchor, <= 30 d | session, day, sw15, sw1h: yes (keep a tick histogram per segment, 15-m / 1-h bars from its 1-s data, fractal 2/2) | week, month: yes in principle; recommend the daily file (history at start-up) |
| TCP composite | TCP\|{poc,vah,val,hvn0-2,lvn0-2}\|{5d,20d,60d} (27) | same profile rule on the summed tick histogram of the N most recent COMPLETED label days (roll days excluded), knowable at the first second of the next label day; replaced each day roll | as TPF | 24 h (next day roll) | needs N days of tick histograms: D7 can keep a rolling per-day histogram | **daily file** (start-up history; one line per row: kind, N, price) |
| TVP developing nodes | TVP\|poc\|{day,sess}; TVP\|hvn\|…; TVP\|lvn\|…; TVP\|void\|… (8) | 1-pt bins (4 ticks) of the label day / D6 session so far; checkpoint every 15 min on the clock, >= 30 min after the segment start. POC row switches only when the max bin moves >= 2 bins. HVN: bins >= P90 of the positive bins (leave < P80). LVN: interior bins (not the 3 outer bins each end) <= P10 of the positive interior bins (leave > P20). VOID: interior bins <= 0.10 x median positive bin (leave > 0.20 x), runs >= 2 bins = single-print void. A zone = adjacent bins that entered at the same checkpoint; the row ends when its FIRST bin leaves and the rest is re-issued | HVN: bin volume / median; LVN, void: 1 - volume / median; POC: share (%) | leaves the set; if still in at the segment end: +4 h (session) / +24 h (day) | yes, completely (running bin histogram) | no |
| TDA delta-at-price | TDA\|abs\|5m, TDA\|abs\|15m | per clock window (300 / 900 s) and 1-pt bin: aggressor volume of one side >= 80 / 150 contracts and >= 2 x the window median bin volume and share of the bin >= 0.55, window extreme within 2 pts above (buy) / below (sell) the bin top / bottom, i.e. price did not progress. Buy-absorbed = resistance (dr -1), sell-absorbed = support (+1). One event per side per window | aggressive volume / median bin | 4 h | yes | no |
| TCD cum-delta | TCD\|cdhi, cdlo; divbear, divbull; burst | cdhi / cdlo: price of the second at which the label-day cumulative delta (buy - sell aggressor) made a new extreme and no new extreme followed within 300 s (day elapsed >= 30 min); div: at a 5-min bar close the bar makes a new day high (low) by >= 1 tick while cum delta at that high is >= 100 contracts below (above) its value at the previous high (low); burst: new label-day record of the rolling 60-s |delta| that is >= the P99 of the previous 20 label days, confirmed after 60 s, level = volume-weighted price of the burst | |cd| / delta gap / |delta60| | label-day end (cdhi, cdlo); 4 h (div, burst) | yes | burst threshold = P99 of 20 days of |delta60|: a constant in the daily file (or D7 keeps 20 days) |
| TLP large prints | TLP\|p25,p50,p100\|1h,4h; TLP\|cl25\|4h | every print >= 25 / 50 / 100 contracts (single print, aggressor side in sd), kept 1 h / 4 h at the print price; cluster = >= 3 prints >= 25 contracts within 5 pts and 10 min (zone min..max, strength total size) | size / k (cluster: total / 25) | 1 h / 4 h | yes | no |
| TLQ measured pools | TLQ\|{SWG f3 f5 f7 \| 15m 1h, EQL tight rel \| 15m 1h, SES, KZ, PDX day rth week}  (25) | the level rows of the corresponding price-line streams (swing H/L, equal H/L, previous session / killzone / prior-day H/L), strength = median pool of the last 200 completed same-type pools (pool = aggressor volume within 2 ticks beyond the level in the 60 s after the break) | expected pool (contracts) | as the source line | the level rows: yes (bars); the pool statistic: D7 can keep a running median per type | **daily file** (the current per-type median pool; ~25 numbers) |

## 6. Coordination, caveats and disclosures
* Z1 (`DS3_ZONES_3_S1.md`) had not landed when the profile lines were built; they follow CF-A and the order's own wording (bins, swing anchoring, value-area rule stated above). If Z1's definitions differ, the parameters are one place each in `gen_profiles.py`.
* HOLD5 uses sampled rows (<= 1,500 per stream, seed 7) and the placebos permute distances within the stream; overlapping events (levels formed in the same minutes) are not cluster-adjusted: ranks are descriptive.
* Absorption-at-price uses the tape only (no book): `TDA` is the tape version of absorption; the book version is ZL-1's.
* Strength of TLQ rows is causal (expected pool); the realised pool of the row itself is in `pools_tape/pool_events.parquet` (ex-post, known at the break, never in the stream files).

## 7. Data audit, defects found and fixed, causality audit
* **Price frame.** The path array (ds3_g2 SC) is additively back-adjusted by a constant PER LABEL DAY; an instrument can carry several offsets over its life, and on a roll day the library switches contract before the tape's front-contract rule. Offsets are therefore estimated per (4-h block, contract) as the mode of SC minus the last print of the second (share exact 99.8% on normal blocks); 7 of ~125 blocks per month on roll days fall back to the nearest well-determined block. The 13 label days with a tape/library volume ratio outside 0.97-1.03 or < 98% of prints inside the second's H/L are excluded from every stream: 20230314, 20230613, 20230912, 20231212, 20240312, 20240618, 20240619, 20240917, 20241218, 20250319, 20250617, 20250917, 20251216. An earlier version used one offset per contract (wrong on 8 days of a month); superseded, never used for a statistic.
* **Defects the truncation audit found (both fixed, streams regenerated, old files kept in `streams_tape_superseded_v0/`):** (1) the TPF strengths of the day / session / week / month anchors were taken from a dictionary keyed by the segment start second, which collided across anchors (levels were right, strengths wrong); (2) the developing-node zones (TVP) grouped adjacent bins by identical LEAVE time, so a zone's extent depended on the future; zones are now grouped by entry time only, end at the first bin that leaves, and the remainder is re-issued as a new row.
* **Causality audit** (audit_run.sh / audit_cmp.py): 6 as-of cuts drawn at random between 2023-07 and 2026-01; every generator (profiles, composites, developing nodes, delta-at-price, cum-delta, large prints, pools) re-run on a tape truncated at the cut; 150 random rows (25 per cut, all families) and ALL 15,053 rows formed in the 3 days before each cut compared with the full build: **0 missing, 0 extra, max |d lo| = max |d hi| = max |d strength| = 0.0** (table by family below). Rows formed within 2 s of the last tape second of a truncated build are excluded (the final partial anchor segment of a truncated tape is not a closed anchor). Density features use only rows with ek <= kin.

| family | rows compared | missing | extra | max d lo | max d hi | max d strength |
|---|---|---|---|---|---|---|
| TCD | 383 | 0 | 0 | 0.0 | 0.0 | 0.0 |
| TCP | 324 | 0 | 0 | 0.0 | 0.0 | 0.0 |
| TDA | 39 | 0 | 0 | 0.0 | 0.0 | 0.0 |
| TLP | 3009 | 0 | 0 | 0.0 | 0.0 | 0.0 |
| TLQ | 1865 | 0 | 0 | 0.0 | 0.0 | 0.0 |
| TPF | 3343 | 0 | 0 | 0.0 | 0.0 | 0.0 |
| TVP | 6090 | 0 | 0 | 0.0 | 0.0 | 0.0 |

## 8. Files, storage, extension
Streams `out/zl/streams_tape/<name>.parquet` (36 MB, 128 files; columns ek, t_ek, dr, lo, hi, end, end2, end3, cap, str, sd, x); footprint `fp/` 2.5 GB; `desc_tape/` (event-study pickles, stream_table.csv, strength_terciles.csv, pools_*.csv) ; `features_tape/` (density sets, coverage_by_stream.csv); `pools_tape/pool_events.parquet` (107,765 levels, 85,493 broken); `bad_days.csv`; `instr_off.json`. README: `streams_tape/README_TAPE.md`. dead_lookup: NOT FOUND for seven tape-zone specs (run before the descriptive cells were appended, after the statistics were computed: they are descriptive cells, not strategy cells) (`out/zl/dead_lookup_tape.txt`); descriptive cells appended to DEAD_CELLS as program ZL2TAPE (tier DESCRIPTIVE).

## OLD CAP interim - checkpoint (ZL-2 stopped for T-RECENT-REDO priority, ~16:30Z 2026-11-01)
**Built (all to label day 20260206, OLD CAP):** fp footprint (out/zl/fp, 36 months), bad_days.csv, instr_off.json, 128 streams (out/zl/streams_tape), desc_tape (event study, stream_table.csv, pools_*.csv), features_tape (density sets), pools_tape/pool_events.parquet, audit_tape (0 missing / 0 extra / max diff 0.0), README out/zl/streams_tape/README_TAPE.md. **Running:** nothing (no worker in flight).
**Entry points (code/zl2/):** fpbuild.py (tape -> fp; env ZL_TAPE_DIR, ZL_G2, ZL_FROM_TS, ZL_TAG), badday.py, gen_profiles.py, gen_dev.py, gen_flow.py [tda cd lp], gen_pools.py (env ZL_OUTD, ZL_CUT for audits), run_density.py, evstudy.py, desc_tables.py, audit_run.sh + audit_cmp.py, make_doc.py (regenerates this page and OVERWRITES it: append checkpoints after running it).
**Resume / extend to 2026-10-31:** (1) wait for REDO-1 to announce the de-duplicated tape months 2026-02 (after 02-06) .. 2026-10 and the extended path arrays (ds3_g2_redo); (2) set ZL_CAP_LD=20261031, ZL_G2=<redo path dir>, ZL_TAPE_DIR=<dedup dir>; run fpbuild.py 2026-02 with ZL_FROM_TS=<first second after the old cap> ZL_TAG=20261031, then 2026-03..2026-10 normally; (3) badday.py for the new days (it reads data/bars2; use the redo 1-s volume after the old cap); (4) rerun the generators into a new ZL_OUTD, keep rows with t_ek >= the old cap time, recompute end/end2/end3 of old rows on the extended path (zstream.episodes); (5) rerun evstudy / desc_tables / run_density with the new windows (L1M..MID) and audit_run / audit_cmp; (6) regenerate the page. Memory: tapelib peak ~10 GB; 2 workers max.
