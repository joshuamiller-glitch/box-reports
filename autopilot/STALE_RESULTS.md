# STALE_RESULTS 2026-11-20T01:13:37Z: 12473 of 102113 done leases (48 h) have inputs newer than their launch / signature changed
by basis (sig = content hash differs, reliable; mtime = lease without signature, only a file newer than the launch): {'mtime': 11921, 'sig': 552}
by family: {'ASI': 8690, 'NYE': 1530, 'STK': 1283, 'NYL': 753, 'EXE': 215, 'SWB': 2}
full list: autopilot/stale_results.csv
signature-differs by family (parked STK stacks NV1/NV2/AX/AS_/CX/AC excluded; those are "stale, parked" by lead decision 0110Z): {'STK': 82}
mtime-only Asia (~8,700) and NYE (1,530, content test: 1,530 of 1,530 identical) are false positives and excluded from the F alert.
