# ADDENDUM 1 to ZL_S4A_PREREG_EXIT_N_LOSS.md (sha256 1ba0d3c23f262eeec067abc9b9f1dafddd7b938923e9ed5efa49d7f77159254f), written before any cell below is scored
F-B2 FLOW-GATED LOSS CUT on the 1-s path (the named gap 'delta-turn' of the prereg, now possible with S4b's shared arrays /mnt/l2/l2vast/ds3_flow1s/, README there): the shipped TH-L2 cut is REPLACED (th_loss off); the cut is an injected market exit (V13T.inject kind 'cut', cost xcost 0.80, resting add cancelled by the engine) at the FIRST path second k after the entry second and before the library exit second where (adverse = side*(E - SC[k])) >= arm AND the flow condition holds. Long convention; a short mirrors buy/sell and bid/ask.
* DT delta turn against: side*delta5[k] < 0 AND side*delta30[k] > 0.
* BIG2 large print against: opposing aggressor volume of prints >= 25 contracts over the last 30 s > 0 (long: big2_sell30, short: big2_buy30).
* SWPF sweep against: long swp_sell30 >= 1, short swp_buy30 >= 1.
* ICEF iceberg on the ahead side: long ice_ask30 >= 10, short ice_bid30 >= 10.
* DTB delta turn AND large print against.
arm in {15, 20, 25, 30, 35, 40} pts: 5 conditions x 6 arms = 30 cells. Same scores, gates, placebos (random trades reaching the same adverse threshold, same count per day, same cost model) as the prereg.
