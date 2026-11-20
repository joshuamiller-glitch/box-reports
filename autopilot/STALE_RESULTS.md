# STALE_RESULTS 2026-11-20T11:36:45Z: 15265 of 208660 done leases (48 h) have inputs newer than their launch / signature changed
by basis (sig = content hash differs, reliable; mtime = lease without signature, only a file newer than the launch): {'mtime': 14619, 'sig': 646}
by family: {'ASI': 11377, 'NYE': 1530, 'STK': 1293, 'NYL': 766, 'EXE': 215, 'ALN': 84}
full list: autopilot/stale_results.csv
signature-differs by family (parked STK stacks NV1/NV2/AX/AS_/CX/AC excluded; those are "stale, parked" by lead decision 0110Z): {'ALN': 84, 'STK': 92}
mtime-only Asia (~8,700) and NYE (1,530, content test: 1,530 of 1,530 identical) are false positives and excluded from the F alert.
