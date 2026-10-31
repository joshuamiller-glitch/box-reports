# RHQ HALT-RESUME ADDENDUM prereg (2026-10-31) - tighter week floors
Declared AFTER HALT-RESUME stage 1 (PRE/X' columns only were printed) showed that the engine's 12R week floor fires 0 times in 149 weeks x 6 books on the S73 stack (10R: 4 fires, 8R: 21, 6R: 77, 5R: 131, 4R: 225 across the six books), so the week-floor resume cells of the main prereg are void (identical to the stack). Lead's interpretation as before (user texts never reached the lead).
This addendum tests the same resume rules at week floors of 6R and 4R. Each resume cell is measured against the SAME floor WITHOUT resume (the resume effect); the two '_noresume_vs_stack' controls measure the tighter floor itself against the stack as it is. Selection rule unchanged (PRE and X' only; a cell with no events in a window is not carried); the carried list in the main HR program was also clarified the same way (cells without events in PRE or X' are not carried) BEFORE any recent column was opened; the first hr selection hash in DECISIONS.md is superseded by the line that follows it.
Cells added: 18 (multiplicity of the HALT-RESUME program becomes 45).
* HRX_floor6_noresume_vs_stack | spec_diff={'floor': 6.0} |  | CONTROL: week floor tightened to 6R, no resume, measured vs the stack as it is (floor 12R)
* HRX_floor6_sess_rf0.5 | spec_diff={'floor': 6.0, 'res_wk': {'kind': 'session', 'rf': 0.5}} |  | week floor 6R, resume sess_rf0.5 (vs same floor no resume)
* HRX_floor6_day_rf0.5 | spec_diff={'floor': 6.0, 'res_wk': {'kind': 'day', 'rf': 0.5}} |  | week floor 6R, resume day_rf0.5 (vs same floor no resume)
* HRX_floor6_thu_rf0.5 | spec_diff={'floor': 6.0, 'res_wk': {'kind': 'thu', 'rf': 0.5}} |  | week floor 6R, resume thu_rf0.5 (vs same floor no resume)
* HRX_floor6_thu_rf1 | spec_diff={'floor': 6.0, 'res_wk': {'kind': 'thu', 'rf': 1.0}} |  | week floor 6R, resume thu_rf1 (vs same floor no resume)
* HRX_floor6_virt4R_rf0.5 | spec_diff={'floor': 6.0, 'res_wk': {'kind': 'virt', 'vthr': 4.0, 'rf': 0.5}} |  | week floor 6R, resume virt4R_rf0.5 (vs same floor no resume)
* HRX_floor6_thuvirt4R_rf0.5 | spec_diff={'floor': 6.0, 'res_wk': {'kind': 'thuvirt', 'vthr': 4.0, 'rf': 0.5}} | CANON | week floor 6R, resume thuvirt4R_rf0.5 (vs same floor no resume)
* HRX_floor6_virt0R_rf0.5 | spec_diff={'floor': 6.0, 'res_wk': {'kind': 'virt', 'vthr': 0.0, 'rf': 0.5}} |  | week floor 6R, resume virt0R_rf0.5 (vs same floor no resume)
* HRX_floor6_plc_rand_rf0.5 | spec_diff={'floor': 6.0, 'res_wk': {'kind': 'rand', 'rf': 0.5}} |  | week floor 6R, resume plc_rand_rf0.5 (vs same floor no resume)
* HRX_floor4_noresume_vs_stack | spec_diff={'floor': 4.0} |  | CONTROL: week floor tightened to 4R, no resume, measured vs the stack as it is (floor 12R)
* HRX_floor4_sess_rf0.5 | spec_diff={'floor': 4.0, 'res_wk': {'kind': 'session', 'rf': 0.5}} |  | week floor 4R, resume sess_rf0.5 (vs same floor no resume)
* HRX_floor4_day_rf0.5 | spec_diff={'floor': 4.0, 'res_wk': {'kind': 'day', 'rf': 0.5}} |  | week floor 4R, resume day_rf0.5 (vs same floor no resume)
* HRX_floor4_thu_rf0.5 | spec_diff={'floor': 4.0, 'res_wk': {'kind': 'thu', 'rf': 0.5}} |  | week floor 4R, resume thu_rf0.5 (vs same floor no resume)
* HRX_floor4_thu_rf1 | spec_diff={'floor': 4.0, 'res_wk': {'kind': 'thu', 'rf': 1.0}} |  | week floor 4R, resume thu_rf1 (vs same floor no resume)
* HRX_floor4_virt4R_rf0.5 | spec_diff={'floor': 4.0, 'res_wk': {'kind': 'virt', 'vthr': 4.0, 'rf': 0.5}} |  | week floor 4R, resume virt4R_rf0.5 (vs same floor no resume)
* HRX_floor4_thuvirt4R_rf0.5 | spec_diff={'floor': 4.0, 'res_wk': {'kind': 'thuvirt', 'vthr': 4.0, 'rf': 0.5}} |  | week floor 4R, resume thuvirt4R_rf0.5 (vs same floor no resume)
* HRX_floor4_virt0R_rf0.5 | spec_diff={'floor': 4.0, 'res_wk': {'kind': 'virt', 'vthr': 0.0, 'rf': 0.5}} |  | week floor 4R, resume virt0R_rf0.5 (vs same floor no resume)
* HRX_floor4_plc_rand_rf0.5 | spec_diff={'floor': 4.0, 'res_wk': {'kind': 'rand', 'rf': 0.5}} |  | week floor 4R, resume plc_rand_rf0.5 (vs same floor no resume)
