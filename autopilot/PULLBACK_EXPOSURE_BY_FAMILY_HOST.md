# Results older than their lease launch, by family x host (ex_pullback_scan.py at 22:05Z, all done leases ever; W-GRIDOPS)

| family | host | stale_vs_code | count |
|---|---|---|---|
| TL3_ASI_ | 109.94.96.39 | False | 1 |
| TL3_ASI_ | 206.223.224.21 | False | 292 |
| TL3_ASI_ | 206.223.224.21 | True | 7 |
| TL3_ASI_ | 67.213.127.157 | False | 1 |
| TL3_NYE_ | 109.94.96.39 | False | 18 |
| TL3_NYE_ | 206.223.224.21 | False | 180 |
| TL3_NYE_ | 206.223.224.21 | True | 13 |
| TL3_NYL_ | 206.223.224.21 | False | 121 |

Hosts: 206.223.224.21 = B Singapore, 109.94.96.39 = A Frankfurt, 67.213.127.157 = C Amsterdam. stale_vs_code=True rows (20, all on B, relaunched 17:23-18:31Z) are in STALE_VS_CODE_20.tsv: their set JSON and event parquet were rewritten AFTER the old result and BEFORE the relaunch.
