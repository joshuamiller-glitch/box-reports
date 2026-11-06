# REPAIRED_BARS_PATHS - repaired 1-minute bars, paths, sha256, rule version, and helper (CHAR-C, 2026-11-06; for the REPAIRED-BARS rerun)
Originals are never modified. Rule = cc_audit v1 (code l2vast/ds3/code/find_c/cc_audit.py sha256 b2a995e9cf2489c7de3ba46dbc49a45f545796aa11ad41cef71340ebc9cc45ab; prereg l2vast/ds3/prereg/FIND_C_scope_addendum3.md): a 1-minute bar with confirmed neighbours (t-1 and t+1 exactly 60 s away, same instrument id) is BAD if its close, high or low lies outside [min(c_prev, c_next, o) - K, max(c_prev, c_next, o) + K], K = 10 sigma + 4 ticks, sigma = 1.4826 x median |close change| of the previous 240 bars (min 60, masked at id changes). Repair = clamp o/h/l/c into the band, then h = max(h,o,c), l = min(l,o,c); ts, volume, ids, roll flags untouched. Bad bars are 0.01-0.04% of bars per instrument except 6E/6J (0.4% / 0.3%, 1-2% in 2013-15).
## Helper
`import sys; sys.path.insert(0,'l2vast/ds3/code/find_c'); import repaired as R`
* `R.load_repaired(sym, feed='te2')` -> dict of arrays with EXACTLY the schema of the original file of that feed (prebuilt files, `R.repair_feed(sym, feed)` recomputes on the fly and also returns `_bad`; `R.flagged_mask(sym, feed)` = bool mask aligned to the ORIGINAL file). helper sha256 db4e42a7015dd990fb5097585c9dec4b22c582f8421fdc0b44a70dc306a92c33.
* feed `te2`: original /mnt/l2/l2vast/ds3/cache_te2/<SYM>.npz (ts,o,h,l,c,v,iid,roll; RAW per-contract) -> repaired /mnt/l2/l2vast/find_c/cache_c_feeds/te2/<SYM>.npz (byte-identical to find_c/cache_c/<SYM>.npz, same sha256).
* feed `instr1m`: original /mnt/l2/l2vast/ds3_instr/<SYM>_1m.npz (ts,o,h,l,c,v,roll + additive-adjusted oa,ha,la,ca; longer than te2: top-up to 2026-10-31) -> /mnt/l2/l2vast/find_c/cache_c_feeds/instr1m/<SYM>.npz (the raw and the adjusted quadruple are clamped with the same offsets; instrument id proxy = cumulative roll flag; flag counts differ from te2 by 0-4 bars: GC 1337, NQ 1258, CL 524, MBT 142, BTCM 192).
* feed `t2min`: original /mnt/l2/l2vast/ds3_t2/<SYM>_min.npz (S4a additive-adjusted frame: o,h,l,c adjusted, rawc, mod, ld, iid, rolldays; GC, CL) -> /mnt/l2/l2vast/find_c/cache_c_feeds/t2min/<SYM>.npz. GC equals ZL-1's ds3_t2/GC_min_repaired.npz to 1e-11 (float rounding) in every field.
## sha256 (full 64 hex)
| sym | feed | bad bars | original sha256 | repaired sha256 |
|--|--|--|--|--|
| ES | te2 | 979 | b6ac9d3aa1f8c3bfa545d8d109df3a8c0bdf5bd9773a8cf3ae2d6171003e31f6 | 3950e83c3f677de74b36ba2627be5a65e543de12019d6626b6c26245ac2a2741 |
| NQ | te2 | 1257 | 5d5c953eb7e975aefc400476f1620684f22cba0b137bf0520066cd315061ffc5 | 48d673b83b7f427010a6604bdae0cc4a1b0d5d79558fbc88b07194db57602105 |
| RTY | te2 | 801 | 25c7702b8ec626392349fd1308ed09619882529d07b7eb69a4d7b16b9a009ece | 1db0ac5de6044545b4e69a617e14e296008fac0a0a3fbd39ac6af6b1ea12192c |
| YM | te2 | 995 | aef950c99635f679fa9fe42b250f5b218896414e007014312e3aff0c3f2a3940 | 6240c5a79c73bbae7abde536ba94b6b035c88555ce8e433c430c7d136db4b6b8 |
| GC | te2 | 1334 | ddc4d6a03ccbe66dfcacf9dc5caeef1f83afb08f053475fb9483dc9f7bec9148 | 9e03f2c96559daabc9fd2b1540c2f81534c2e1d1845c815bdece11e70d306719 |
| CL | te2 | 523 | 9d301f76ab6caa76c1035be1c434cccbc169e46e5e2acca5381832de86f57ae1 | 3e5b06db2d40487b5827ef52a2a986cb5c3f28d5e02903220e4a9ce2c240c8c9 |
| ZN | te2 | 565 | 5c6dd6dd6e259edc555c1dc59af1a6ae7a88f0ac98455d72779f7ab4fbb2b4b8 | eb47a164b5c17a8e561c49ec0906b20e3e981600ec30d6ec093b48ae76ba7d77 |
| ZB | te2 | 583 | edd3248b074e45bdab520485ab68b49ca370d8ddca7dbebd6d2f4023a0dece75 | 5f8c07c5fc4ffd0a283a3c722b7d723356df5e1005b86773a0afbf92f516bfff |
| 6E | te2 | 19721 | 8d5be64812b57b9fbb85f0670eec2d528415fb6efb7165e06e0b0a3c24f9f859 | 5a9f63322b33afaea21762541249364bdbc35d26238819afff740289fe57e80d |
| 6J | te2 | 14455 | 5cd489b889a801c7db1dadb50d17d890b58ee1c666369f49ce8aef628ac32d03 | 32c8858b9d924f6a311de7693193e1d668c7baa1bb09ab6b70b259e6d86af1cc |
| MBT | te2 | 138 | 38f97f45929fbadf4045d816dd73fdae3c96f12febafd79111cab184735d3ad6 | e9748cfccae7d6caeed1a98b2f42ce3862e4b76301831985565112e4951618ad |
| BTC | te2 | 185 | 527e0953f60b3ceb1e540487e79ce6348443663cfae0b711944ed49cc22890c3 | 4b2b499d5979740dd346f08b211b846a54bb736a571cc8d3039d074b6b874111 |
| NKD | te2 | 189 | 4d0a3c9b7ad705eab8ee1bee3209e584490485f57efc0cac68ecd4955fef3863 | 921544318b65deaaefff7424af51c695be02be7a00d2aac38fb1ba1b2b349fe0 |
| BTC | instr1m |  | 674b1d88109371353831612d7592e19f2eabef2d1d5f0a128ade51f8e5960076 | e3317b6b1e558ef7d465ad0a82a212a6d66efe192f564a8999c1d0a61c0e0c30 |
| BTCM | instr1m |  | aff5248cfcdd3a632a0a4d14875234ed0b760a7a1f631943b56245672c3f0000 | 06f61dda3c0816f5b432a459b578bfe96bc5cf8f4646360cb7d44ef3253d1e61 |
| CL | instr1m |  | 5204760f42afe7d90e632f71ea321ac2ce2ae8dd08d6c0e0b614a318cf562c5e | 6734031be3b43bd2f8cc8e06969e37de1ecc8b74e8fe7dc43808c28165723271 |
| ES | instr1m |  | de3ed28e78ffec3e85bf064bf607117a21998d669d8d8631be13cf0db3e189c3 | 086ea627912d49d6cd09b60ad54a08e2413f0accd5d83551ade6d6dfc62a1596 |
| GC | instr1m |  | d70772241ed2d3337d210fc5b88bb11c0758099372a46e9a9319c795fd6f2e21 | 0b489a0a9d2edb2502b58c6984ce0b267e088c92d5b1331a67e2adaf6daec698 |
| MBT | instr1m |  | c1f31a7e59c8c48cf18331750fcf59ff21e718ced345507e69b6884b3f6d3b7c | b38dc321c809bdac73be6f3c1141af7b95e8211752a9331e1e52c1c4bef8ea33 |
| NKD | instr1m |  | 9454cd3eda7cff77db94e237453f1d7f68d96da7e56eda6219cb691cc0d9a753 | 230376b25ddfddc664908f4c5dbe99b3e884f953cbc4b4ff9ca4c0ccfb8f7ae1 |
| NQ | instr1m |  | 14c68dfc3bc597553980c44f6c002c81eba2d27da99dad3b1489e1db2c624f73 | 843e70e2a816fc70c20fe5cb4e8472c975fdf46a109cb252559aa8ab124eb711 |
| RTY | instr1m |  | 17659b733a20cf72f25710ddd3fb7d6b4462d71300725e8b10998d8cb771bac1 | cbb5c3e167b95255bdfd401a7128dc23ca3884d98ec0b5eb09ee60fa59ed5dde |
| GC | t2min |  | 618d64a41e31fc820979d42be6aee9bdaf81bd9ccb54728909d2c8546734923a | fc50d3ed3bea9a35498554ab7567bfdb322070839729cbf397b91e79f5a5d810 |
| CL | t2min |  | efdaa22d01d1254dc4deea56390b92ee3eb388f6566668f4cefa3526db922104 | fc60a9abb10698dbcf49e7ba7cbb2a8f9a986104d6d21d32cc9f3f2323b0a66d |

## How the original trade frames map to original bar files (instr2_trades/<SYM>/*.parquet, measured by matching entry_px to the bar open at entry_ts)
* T-FIND tick-map books (`T2F_<SYM>|...` / `T2F1B_...`, 'FIND_*' frames): entry_px = open of the bar at entry_ts of **te2** RAW per-contract bars (100% match ES, RTY, YM, GC, CL, ZN, ZB; 6J 'FIND#S'; NKD 'FIND#S'). Re-simulate on `load_repaired(sym,'te2')`. (T2F1B 'b_PD' bar-based rows are 1-s based, not 1-min.)
* LRS (learned-rule) frames: GC, CL on **t2min** (adjusted frame, 100%); MBT, BTC, NKD, NQ(25%), RTY(25%) on **instr1m** adjusted (`oa`, 100% where tested; NQ/RTY LRS partly other); ES, YM, 6E, 6J, ZN, ZB LRS: only 0-26% match either feed in a 4-frame sample (entry price includes slippage or the frame is built from the 1-s tables): ask the owner / treat as UNMAPPED until checked.
* Rule frames (donchian, vwap, orb, session_extreme): **te2** raw (6J, YM, GC, MBT 100%).
* T-INSTR-2 stage-2 K-grid / ATR-stop frames (`ES__K__...`, `GC K-grid`, RTY/YM `K_b..`, 6E/6J/CL `<n>_<session>_atr..`, ZN/ZB `keltner_flip`/`supertrend_flip`): these frames carry NO usable entry_px for a direct match (no column, or 0% against te2/instr1m/t2min at lag 0 and 60); they were produced by the owner's bar pipeline (GC: **t2min** adjusted frame, signals in the adjusted frame; ES/RTY/YM/NQ: the Z1 pipeline on ds3_instr 1m **instr1m**; 6E/6J/CL: the S4a/ZL-1 pipeline on **te2**/adjusted). The cell definition (family, params, session, stop, R, T) is in the cell_id and the owner's stage-2 pickle (/mnt/l2/l2vast/instr2_<sym>/stage2.pkl and GC_stage2.pkl); the rerun of those cells must regenerate signals from the repaired bars with the owner's code, not just re-exit the frame.
* Back-adjusted frames vs raw: additive offsets leave stop/target distances in points unchanged, so a bracket exit on raw or adjusted bars gives the same trades; the repaired feeds keep that property.
