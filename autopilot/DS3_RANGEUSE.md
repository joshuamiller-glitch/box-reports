# DS3_RANGEUSE - T-RANGEUSE: the walk-forward range forecast on D7 dials (W-RU). Rebuilt 2026-11-13T23:39Z by code/th_rangeuse/ru_loop.sh (every 3 h). Research only, NO PASS claim.
**VERDICT (plain): No scored cells yet (L3M months still running).**

Prereg: autopilot/RANGEUSE_PREREG.md (sha in DECISIONS.md, logged before scoring). Order: DIRECTIVE_UW_3PART_20261113.md PART 2. Base JN05W2 exact engine, all layers ON. Identity: TL3_RU_ID 202610 (hook path active at neutral multipliers): 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL.
Months scored (cells with all months of the window / 83 cells): L3M 0, L6M 0, HOLD 0, PREUW 0. Driver: 494 jobs wanted, 10 chains running, 1794613195.

## 0. Method (short)
- Forecast = walk-forward ridge (expanding, min 120 days, refit every 10 trading days) of the session ln range at the reading used by the trade (asia/london R0 prior close; nyam R2 09:30 before 10:00 else R3 10:00; nypm R3). (a) ATR benchmark only, (b) ATR + IV term (NDX/QQQ/SPX), (c) full UW (b + SPX/QQQ flip, SPX/ALL4 gamma, NDX/SPX IV level, tide). Forecast points = predicted ln range x last close; ratio = prediction / expanding median of the past predictions; terciles from the expanding past. First forecasts exist from ~2025-03, so PREUW (2024-10..2025-06) is mostly unscored by the rule (rule inactive without a forecast = same as JN05W2).
- Cells run in the exact engine (own hook module ru_hooks.py, no shared engine file edited) as JN05W2 + one dial. Metrics vs JN05W2 on the same months: mean $/wk change, maxDD change in % (positive = smaller drawdown), worst-week change $, full stops/wk (cell(ref)), best-5 weeks kept % (cell $ in the 5 best JN05W2 weeks / their $), winning weeks turned losing. Per session = the same run sliced by entry session (asia london nyam nypm), books interact only through the shared engine.
- Tolerant gate per window: maxDD not worse by more than 2%, worst week not worse by more than 2% of the reference worst week, mean not below -25 $/wk. A LEAD must pass in L3M, L6M AND the older windows (HOLD, PREUW where scored); a lead is only called strong when it beats placebos (forecast shifted 11/23/37 days) and the permuted family null in section 5.
- Question per dial = gain of (b) and (c) over (a), not over no rule. Section 2 shows no-rule (JN05W2 = zero row), a, then b-a and c-a.

## 1. Forecast quality (out of sample, whole history ~2025-03..2026-11; R2 vs expanding mean of the target; all three share the walk-forward)
| session (reading) | R2 a ATR | R2 b +IV term | R2 c full UW | R2 L6M a/b/c | n |
|---|---|---|---|---|---|
| asia (R0) | 0.193 | 0.393 | 0.357 | 0.072/0.255/0.260 | 428 |
| london (R0) | 0.158 | 0.297 | 0.178 | -0.166/-0.015/-0.194 | 428 |
| nyam (R2) | 0.257 | 0.269 | 0.233 | 0.202/0.146/0.078 | 428 |
| nyam2 (R3) | 0.322 | 0.311 | 0.275 | 0.262/0.204/0.164 | 428 |
| nypm (R3) | 0.258 | 0.239 | 0.128 | -0.044/-0.024/-0.159 | 414 |

Note: (c) uses many UW columns and is NOT better than (b) out of sample in most sessions here: the ridge overfits (c); the IV-term group carries almost all of the UW range signal. This is stated so that "(c) gains over (a)" is read with that in mind.

## 2. Per dial: every cell, scope all and per session (exact engine, delta vs JN05W2; b-a and c-a gain rows)
### Dial 1 target-only scaling (stop unchanged)

### Dial 2 constant dollar risk (stop scaled, lots inverse; H = half version)

### Dial 3 cut levels in forecast-range units (state-cut arm + K7 flat cut)

### Dial 4 range used up (I skip / II take profit early / III shrink target; k in name 05=0.5 075 1 125)

### Dial 5 replace atr_rel in live layers (REG half-size, skip) by the forecast ratio (A-cells = live atr_rel reference)

### Dial 6 entry distance (split-add dip MINDIP)

### Dial 7 lock levels (BookLock peak 2R threshold)

## 3. Best setting per dial and per session (drawdown first: L6M + HOLD maxDD cut, tolerant gate; status says which windows it holds in)
| dial | scope | best cell | status | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|---|---|

## 4. Strength, plainly
No data yet.

## 5. Placebo (forecast shifted 11/23/37 trading days) and family null (forecast permuted within month, seeds 1-3) beside the finalists
Finalists not chosen yet (needs L6M of the grid).

## 6. What could not be hooked
- Keltner band multiple and chase_k limit (dial 6): the live path has no limit that reads them (chase_k is only a context tag for the P7 cut; the Keltner engine X3 is a disabled book). Pullback trigger depth lives inside the signal engine (PbEngine), not hooked here; dial 6 is the split-add dip (MINDIP) only.
- Dial 3 pct thresholds: the state-cut arm (points) and the K7 flat cut d are scaled; the per-cell pct multiplier (mult) and the ctxcut rule inside wb_hooks are not scaled.
- Dial 4 uses the session range printed so far from NQ 1-min bars completed before the signal second; (ii) uses the same calculation live every second.
- Dial 8 JOINT and the PART 3 event/non-event split: appended when W-CAL flags land (autopilot/DS3_UWCAL.md) and top-3 per dial exist: section 7.

## 7. Joint (dial 8) and event/non-event split
Not built yet.