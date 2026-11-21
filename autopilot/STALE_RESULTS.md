# STALE_RESULTS 2026-11-21T19:28:45Z: 2026 of 547350 done leases (48 h) have inputs newer than their launch / signature changed
by basis (sig = content hash differs, reliable; mtime = lease without signature, only a file newer than the launch): {'sig': 623, 'mtime': 1403}
by family: {'ALN': 603, 'STK': 591, 'NYE': 414, 'ASI': 407, 'SR': 10, 'NYL': 1}
full list: autopilot/stale_results.csv
signature-differs by family (parked STK stacks NV1/NV2/AX/AS_/CX/AC excluded; those are "stale, parked" by lead decision 0110Z): {'ALN': 603, 'SR': 10, 'STK': 10}
mtime-only Asia (~8,700) and NYE (1,530, content test: 1,530 of 1,530 identical) are false positives and excluded from the F alert.
