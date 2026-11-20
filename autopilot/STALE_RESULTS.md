# STALE_RESULTS 2026-11-20T22:12:40Z: 15887 of 333843 done leases (48 h) have inputs newer than their launch / signature changed
by basis (sig = content hash differs, reliable; mtime = lease without signature, only a file newer than the launch): {'mtime': 14839, 'sig': 1048}
by family: {'ASI': 11615, 'NYE': 1512, 'STK': 1293, 'NYL': 766, 'ALN': 486, 'EXE': 215}
full list: autopilot/stale_results.csv
signature-differs by family (parked STK stacks NV1/NV2/AX/AS_/CX/AC excluded; those are "stale, parked" by lead decision 0110Z): {'ALN': 486, 'STK': 92}
mtime-only Asia (~8,700) and NYE (1,530, content test: 1,530 of 1,530 identical) are false positives and excluded from the F alert.
