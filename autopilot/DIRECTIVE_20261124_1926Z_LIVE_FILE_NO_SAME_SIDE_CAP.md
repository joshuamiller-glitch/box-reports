# The live D8 file has NO same-side lots cap: answer to the 19:25Z "relay should say", and a fidelity question

Written by the relay (Claude), not typed by Josh. Information / bug report. No new test is ordered beyond the re-run that the lead's own 19:25Z line implies is needed for Josh's 1901Z order to mean what he asked.

FACT (read from the delivered code, D8Asia.cs v22 / v24b): the strategy has no rule that limits total lots on one side. Every book trades its own lots (Lots per book x its sizer / zone halving); several books can be long together at full size. The only cross-book rules are the fitted ones (StackCut when in the pick, the stack day stops, BookLock per book). So in the file the same-side cap never binds, at any lot size.

WHAT FOLLOWS:
1. The 6-lot add test (members at 6 lots, same-side cap 6) is not the file: with the cap at 6 only one book can be open per side. For Josh's question ("the fade at my real size") the cap must be off, or scaled with the lots so it cannot bind (6 x 6 = 36, as you scale it x4 in the x4 runs). Please re-run the 1-lot and 2-lot fade rows and their "without" row that way and post both tables side by side, labelled; then prior years / walk-forward / controls on the corrected basis.
2. FIDELITY QUESTION, please answer in one line each: in the 2-lot fits that are in the file now (Asia BF2_JT110 and JT6, NY AM BF2_JT68, NY PM BF2_JT209) and in the 2-lot combined table (D8_ALL_SESSIONS_COMBINED.md), was the same-side lots cap 6 (binding: 4 books x 2 lots = 8) or scaled to 12, or off? If it was binding, say how many entries it removed per session on L6M, so Josh knows how far the fitted numbers are from what the file does.
3. If the cap was binding in those fits, do NOT re-fit on your own: report the size of the effect first; Josh decides.
