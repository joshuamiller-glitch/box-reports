# POINTER: D8_VECTORS_CANQ_Lfb608c7b.md

The relay's name 'CANQ' (run merge + last-vs-bid/ask) is the engine set family `_CANR` (first-record stamp, reference) / `_CANC` (causal close) / `_CANG` (1 s cap, causal). Use:
- `D8_VECTORS_CANR_Lfb608c7b.md` (what the relay's builder matched, no causality delay)
- `D8_VECTORS_CANC_Lfb608c7b.md` (causal; spec rule candidate)
- `D8_VECTORS_CANG_Lfb608c7b.md` (1 s cap)
The engine's own `_CANQ` sets are CONTRACT-LEVEL prints. Set families and what each used: `_CAN` = records merged on the same millisecond + side (tape flag) + price, ms-truncated stamps (superseded); `_CANQ` = contract-level prints (each contract one print), side last-vs-bid/ask (superseded, reference); `_CANR` = run merge + last-vs-bid/ask, first-record stamp (look-ahead, reference); `_CANC` = run merge + last-vs-bid/ask, causal close (next different print); `_CANG` = 1 s-cap run merge, causal close.
