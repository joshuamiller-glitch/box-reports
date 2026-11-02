# SIZER_LOT_ARM_SPEC: lot-bucket TH-L2 arm "P4020" (Z1, 2026-11-02) LEAD with qualifiers, post-hoc, no PASS, Shadow only

## Exact definition (no fitted parameter)
Base stack: T-SIZER base = run_v13t_ts (V13T live: take lines off, lock none, lockfix legs, xcost 0.80, stopcost 2.45) + HALF zone layer (lines kijun1h, PDmid, CRT4h, KCup4h, camH3, OTE705, OTE79 at D20 fresh, plus OTE-62 B73 D30) + ER(20) 5-minute binary ladder (x1.5 if ER >= 0.30 else x0.5) with SEQUENTIAL rounding.
Traded lots for an entry (per book, per session):
1. base = lot table value (live11 table: LN[book] x U[book, session]);
2. zone_lots = max(1, floor(base x zf + 0.5)) with zf = 0.5 if the entry is inside a HALF zone else 1.0;
3. traded_lots = max(1, floor(zone_lots x ladder + 0.5)), ladder = 1.5 if ER(20, 5-min) >= 0.30 else 0.5 (NaN -> 1.0).
TH-L2 adverse-excursion arm in points (the TH-L2 trigger/window/mult unchanged, only the arm value):
- traded_lots in 1..4 (any book): arm = 40
- traded_lots == 11 (only PE reaches it): arm = 20
- every other row (traded lots 5..10, 12+, i.e. 6 in practice): arm = 30 (the live value)
The arm is a function of traded_lots only: it uses the lots after zone half and the ER multiplier. The sequential-rounding lots must be computed before the arm is chosen; the arm does not change lots.

## Five worked rows (real rows from the engine tables)
| day | book | session | base lots (table) | zone | ER(20) 5m | ladder mult | after zone half | traded lots | arm |
|---|---|---|---|---|---|---|---|---|---|
| 2025-07-29 | PE | london | 7 | none | 0.415 | 1.5 | 7 | 11 | 20 |
| 2025-10-27 | PE | asia | 7 | none | 0.278 | 0.5 | 7 | 4 (7 x 0.5 = 3.5 -> floor(4.0) = 4) | 40 |
| 2025-04-11 | KB | london | 2 | half | 0.288 | 0.5 | 1 (2 x 0.5 = 1) | 1 (1 x 0.5 = 0.5 -> floor(1.0) = 1, min 1) | 40 |
| 2025-05-28 | SM | asia | 4 | none | 0.390 | 1.5 | 4 | 6 | 30 (6-lot rows keep the live arm) |
| 2024-11-22 | PE | london | 7 | half | 0.412 | 1.5 | 4 (7 x 0.5 = 3.5 -> 4) | 6 (4 x 1.5 = 6) | 30 |
Unit-test reading: the PE row with base 7 gets 11 lots only when there is no zone half AND ER >= 0.30; the same PE row inside a HALF zone with ER >= 0.30 trades 6 lots and keeps arm 30; with ER < 0.30 it trades 4 (no zone) or 2 (zone: 7 x 0.5 = 3.5 -> 4, then x 0.5 = 2) lots and gets arm 40.

## How often it fires live (PE 11-lot rows, 2023-04..2026-10, 43 months; one row = one PE entry)
Total 2,357 11-lot rows of 6,126 PE rows (38%). Per month (YYYYMM: rows): 202304: 25, 05: 24, 06: 28, 07: 19, 08: 52, 09: 23, 10: 34, 11: 22, 12: 20; 202401: 30, 02: 36, 03: 36, 04: 35, 05: 19, 06: 26, 07: 47, 08: 63, 09: 47, 10: 46, 11: 34, 12: 48; 202501: 71, 02: 50, 03: 68, 04: 136, 05: 64, 06: 46, 07: 37, 08: 43, 09: 32, 10: 48, 11: 88, 12: 58; 202601: 60, 02: 67, 03: 101, 04: 85, 05: 83, 06: 130, 07: 116, 08: 71, 09: 88, 10: 101. The count rises over time (about 25-35 per month in 2023, 40-70 in 2024-25, 80-130 in 2026): the arm-20 half fires on roughly 1 to 6 PE entries per trading day.
Rows with traded lots 1-4 (arm 40): 24,221 of 27,902 rows in all books (87%); 6-lot rows keep arm 30.
Evidence and caveats: see DS3_SIZER.md addenda 5, 6 and 7. The arm-20 half carries the drawdown cut and costs about $488k alone; the arm-40 half earns about +$319k and makes the pair about -$15k in total P&L. Post-hoc selected cell: price in addendum 7.
