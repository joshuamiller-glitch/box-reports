# DS3_THL_A_DATA - loss-side rows of the THP A dataset (T-TH-LOSS section A)
Loss rows are built and share the machinery, keys, features, audit and coverage of DS3_THP_A_DATA.md (read that file for the dictionary, load recipe, regime keys and leakage audit).
* Trees: out/thp/data/ldp1s (201,575,140 rows, every second with upnl<=0 from entry to exit), ldp10s (20,148,224), ldp1m (3,348,209 at 1-min closes); pl=0; same hive layout and 142 columns as the profit trees. Order-book features on 100% of loss rows.
* Loss features: sec_uw (time under water), sec_since_mae, recov_pts / recov_pct, dist_stop / dist_stop_R, lc1-lc3 + lc_cnt + lc_elig + lc_fired (live loss rule, approximate parameters, see dictionary), book features around the stop (liq_behind4/8 = thin-book proxy; sz_stop_lvl only when the stop is within the 10 visible levels), sz_behind1 vs sz_ahead1, big1_net30_s, pulled_sup10 / pulled_opp10, absorb10_s, delta10_s/delta60_s.
* Labels: y_tgt (target before stop), fut_dd (max further adverse excursion), t_res, rem_pts_lib / rem_pts_meas.
* Scope gaps as in the profit doc (basket legs, D6 session/O6 re-bracket cells not built).
