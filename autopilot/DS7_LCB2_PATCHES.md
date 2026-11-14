# DS7 v1.9a patches proposed by W-LB2 (TEXT ONLY, ~/DS7.cs not edited; nothing applied on the execution server)
Line numbers refer to ~/DS7.cs (506,585 bytes). Only P1 is tied to a mechanism that reproduced something on the box data (see DS3_LIVE_CUT_BUG2.md section 3); P2/P3 are guards.

## P1 (only if STATEDIAG shows nB/nA collapsing or depForeign Remove leaks) - foreign Remove with price 0 / mismatching price must not touch the NQ arrays (L1403, OnMarketDepth)
```diff
-				{ double nqRef = 0; try { nqRef = Closes[0][0]; } catch { } if (nqRef > 0 && e.Price > 0 && Math.Abs(e.Price - nqRef) / nqRef > 0.05) { depForeign++; return; } }
+				{ double nqRef = 0; try { nqRef = Closes[0][0]; } catch { } if (nqRef > 0 && e.Price > 0 && Math.Abs(e.Price - nqRef) / nqRef > 0.05) { depForeign++; return; }
+				  if (e.Operation == Operation.Remove) { double[] rp = e.MarketDataType == MarketDataType.Bid ? depBidPx : depAskPx; int rn = e.MarketDataType == MarketDataType.Bid ? depBidN : depAskN; if (e.Price <= 0 || e.Position >= rn || Math.Abs(rp[e.Position] - e.Price) > 1e-6) { depForeign++; return; } } }
```
Effect on a clean book: none (a genuine NQ Remove carries the price of the level at that position).

## P2 (guard) - MedLevel cannot be inflated by a few foreign/huge levels (L1670 in StateTick)
```diff
-				if (live) { double b5 = 0, a5 = 0; ... double avg = (b5 + a5) / 10.0; stMedLevel = stMedLevel == 0 ? avg : 0.999 * stMedLevel + 0.001 * avg; }
+				if (live) { double b5 = 0, a5 = 0; ... double avg = (b5 + a5) / 10.0; if (stMedLevel > 0) avg = Math.Min(avg, 3.0 * stMedLevel); stMedLevel = stMedLevel == 0 ? avg : 0.999 * stMedLevel + 0.001 * avg; }
```
(clean-book MedLevel on the 11-11/12 nights is 1.85-2.4 and moves < 5 % per hour, so the clamp never binds on a clean book.)

## P3 (guard, one line) - arm never closer than 15 pts to the worked stop (L1737, pct condition)
```diff
-						armPts = arm; if (!(-unreal >= arm)) { ok = false; break; } continue;
+						arm = Math.Min(arm, Math.Max(15, 0.75 * stopDist)); armPts = arm; if (!(-unreal >= arm)) { ok = false; break; } continue;
```
Only matters if a book stores a stop 80 pts away (native catastrophe level) as b.StopPx: arm 0.667 x 80 = 53.3 leaves 6.7 pts to the 60-pt worked stop (clean port then cuts 9 s / 1 s / never before the stop). In JoinThenMarket books b.StopPx is the 60-pt level (M7 arm 38 = 0.5 x 75.5 confirms), so P3 is a no-op there.

## No patch for: Update-in-place not counted, depBidN/depAskN not shrinking, stale levels, top-5/top-7 visibility - none of them reproduced the silence (DS3_LIVE_CUT_BUG2.md section 3).
