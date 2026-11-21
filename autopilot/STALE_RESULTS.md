# STALE_RESULTS 2026-11-21T19:46:29Z: 1469 of 553475 done leases (48 h) have inputs newer than their launch / signature changed
by basis (sig = content hash differs, reliable; mtime = lease without signature, only a file newer than the launch): {'sig': 623, 'mtime': 846}
by family: {'ALN': 603, 'STK': 333, 'ASI': 262, 'NYE': 260, 'SR': 10, 'NYL': 1}
full list: autopilot/stale_results.csv
signature-differs by family (parked STK stacks NV1/NV2/AX/AS_/CX/AC excluded; those are "stale, parked" by lead decision 0110Z): {'ALN': 603, 'SR': 10, 'STK': 10}
mtime-only Asia (~8,700) and NYE (1,530, content test: 1,530 of 1,530 identical) are false positives and excluded from the F alert.
