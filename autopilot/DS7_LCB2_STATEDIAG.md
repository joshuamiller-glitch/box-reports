# STATEDIAG, trimmed to what settles it in ONE live evening (text only; add to ManagePolicyState after L1719, not applied)
One line per book per closed second while unreal <= -20 (about 120-400 lines per losing trade), plus ONE line at every early return of the loop, de-duplicated per book per reason:
```csharp
// after the DepthLive/MedLevel gate, inside the rule loop once pulledMult is known:
if (unreal <= -20) Print(now.ToString("HH:mm:ss") + " STATEDIAG " + b.Tag + " ver=1.9a u=" + unreal.ToString("0.0") + " entry=" + b.EntryPx.ToString("F2") + " stopPx=" + b.StopPx.ToString("F2") + " sd=" + stopDist.ToString("0.0") + " lots=" + lots
  + " arm=" + armPts.ToString("0.0") + " p5=" + StatePulled(b.Side, sec, 5).ToString("0") + " pw=" + StatePulled(b.Side, sec, win).ToString("0") + " med=" + stMedLevel.ToString("0.00") + " mult=" + pulledMult.ToString("0.0")
  + " ok=" + ok + " cnt=" + cnt + "/" + r.Persist + " nB=" + depBidN + " nA=" + depAskN + " top=" + depBidPx[0].ToString("F2") + "/" + depAskPx[0].ToString("F2") + " foreign=" + depForeign + " live=" + depthLive + " rule=[" + r.Raw + "]");
// at each early return (one Print per book per reason, re-armed when the reason changes):
//   L1711 PolicyTriggered|StCutRule|StShadowSeen -> "GATE cutset"; L1712 ThPolicyValid false -> "GATE invalid valid=" + thPolicy.ValidUntil; L1713 PolicyStateMode Off/Shadow;
//   L1719 !depthLive|stMedLevel<=0 -> "GATE nodepth nB/nA/depLast age"; rule loop continue on regime/ctx mismatch -> "GATE regime want=" + r.Regime + " have=" + DayRegime + "/" + sess + "/" + b.Ctx;
//   StateTick L1673 filter -> "GATE book ExitPending=" + b.ExitPending + " Bip=" + b.Bip + " NoBracket=" + b.NoBracket
// and Print(ex.Message) inside the two empty catch { } around StateTick (L1404, L3764).
```
Reading it (decides in one evening): (1) `gate` lines name any silent early return; (2) `mult` vs the box's port at the same second (box value for the 11-11 trades 14-23x) says whether pulled/MedLevel are off, `med` > 3 or nB/nA far from 10 says array fault; (3) `sd` and `arm` say whether the arm sits 40 or 53 pts out; (4) `foreign` rising with `nB/nA` falling says foreign Removes. Send the raw lines of one losing P7 evening trade plus the "TH-STATE CUT ... rule [..]" line.
