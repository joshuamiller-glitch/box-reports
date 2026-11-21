# STALE_RESULTS 2026-11-21T14:10:59Z: 7634 of 515983 done leases (48 h) have inputs newer than their launch / signature changed
by basis (sig = content hash differs, reliable; mtime = lease without signature, only a file newer than the launch): {'mtime': 6586, 'sig': 1048}
by family: {'ASI': 3983, 'NYE': 1512, 'STK': 1293, 'ALN': 486, 'NYL': 360}
full list: autopilot/stale_results.csv
signature-differs by family (parked STK stacks NV1/NV2/AX/AS_/CX/AC excluded; those are "stale, parked" by lead decision 0110Z): {'ALN': 486, 'STK': 92}
mtime-only Asia (~8,700) and NYE (1,530, content test: 1,530 of 1,530 identical) are false positives and excluded from the F alert.
