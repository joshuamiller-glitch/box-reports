# DS3_CONFLUENCE_LIVE_CLASS_CF1: which of W-CF1 condition columns D7 can compute itself

VERDICT: of 6021 conditions (excluding the 200 nonsense controls), 5991 use only D7 own NQ bars / book state (class A), 12 need a maintained release-calendar file (F), 4 need extra live CME series (B: ES/RTY correlation and confirmation), 14 need the TICK feed (C). Per-column table: /mnt/l2/l2vast/_confl/cols_cf1_column_classification.csv. Caveats: NQ bar volume in NT8 must match the replica minute volume (parity check needed for profile / VWAP items); round-number conditions use the true traded price in D7 (the offset exists only in our spliced research series).

| class | conditions |
|---|---|
| A | 5991 |
| X | 200 |
| C | 14 |
| F | 12 |
| B | 4 |
