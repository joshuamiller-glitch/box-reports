# STALE_RESULTS 2026-11-20T03:04:45Z: 14016 of 121956 done leases (48 h) have inputs newer than their launch / signature changed
by basis (sig = content hash differs, reliable; mtime = lease without signature, only a file newer than the launch): {'mtime': 13460, 'sig': 556}
by family: {'ASI': 10220, 'NYE': 1530, 'STK': 1287, 'NYL': 762, 'EXE': 215, 'SWB': 2}
full list: autopilot/stale_results.csv
signature-differs by family (parked STK stacks NV1/NV2/AX/AS_/CX/AC excluded; those are "stale, parked" by lead decision 0110Z): {'STK': 86}
mtime-only Asia (~8,700) and NYE (1,530, content test: 1,530 of 1,530 identical) are false positives and excluded from the F alert.
