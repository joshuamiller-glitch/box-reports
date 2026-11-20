# STALE_RESULTS 2026-11-20T10:58:24Z: 15162 of 202585 done leases (48 h) have inputs newer than their launch / signature changed
by basis (sig = content hash differs, reliable; mtime = lease without signature, only a file newer than the launch): {'mtime': 14559, 'sig': 603}
by family: {'ASI': 11317, 'NYE': 1530, 'STK': 1292, 'NYL': 766, 'EXE': 215, 'ALN': 42}
full list: autopilot/stale_results.csv
signature-differs by family (parked STK stacks NV1/NV2/AX/AS_/CX/AC excluded; those are "stale, parked" by lead decision 0110Z): {'ALN': 42, 'STK': 91}
mtime-only Asia (~8,700) and NYE (1,530, content test: 1,530 of 1,530 identical) are false positives and excluded from the F alert.
