# STALE_RESULTS 2026-11-20T06:55:06Z: 14717 of 163697 done leases (48 h) have inputs newer than their launch / signature changed
by basis (sig = content hash differs, reliable; mtime = lease without signature, only a file newer than the launch): {'mtime': 14160, 'sig': 557}
by family: {'ASI': 10922, 'NYE': 1530, 'STK': 1288, 'NYL': 762, 'EXE': 215}
full list: autopilot/stale_results.csv
signature-differs by family (parked STK stacks NV1/NV2/AX/AS_/CX/AC excluded; those are "stale, parked" by lead decision 0110Z): {'STK': 87}
mtime-only Asia (~8,700) and NYE (1,530, content test: 1,530 of 1,530 identical) are false positives and excluded from the F alert.
