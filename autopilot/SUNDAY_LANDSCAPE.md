# SUNDAY_LANDSCAPE: no fixed target, own stop, exit from the current landscape (W-SUNDAY-LS, exact engine, live mix)

Every set: one book of the live mix enters with its own stop and NO target (session flatten kept, live loss-side Trade Health kept, the book's profit-side Trade Health removed); everything else live as run. Numbers are WHOLE-MIX deltas vs the live mix as run on the same months (+ = better; dd gap + = shallower weekly max DD). Dollars after 4.84 x lots. Rule text and codes: code/th_ls/ls_build.py docstring and ls_mgr.py; rules: a set is scored on every month it has (xi: from 2023-09; live row cut to the same months). PASS = max DD and worst week not worse than the live bracket, L6M DD not worse, income >= 0.97 x live, and weekly DD better-or-equal in >= 2 of 3 full years. BEST landscape per book (drawdown first): the PASS set with the most income, else the set with the shallowest max DD among sets with income >= 0.90 x live, else the set with the smallest income loss; marked WEAK when not PASS.

Codes: so0 = stop-only to session end; gKKaAA = give-back cap: stop keeps KK% of the peak once peak >= AA% of the old target distance; trCC = trail CC% of the old target behind the best from +50%; xi10all/xi15all/xi10ext/xi10tight = ES RTY YM (+ZN ZB 6J 6E NKD CL GC) turning against a winner for 5 min (1.0 / 1.5 sigma): all = leave, tight = stop to 80% of peak, ext = also needs one extra instrument; rg80/rg100 = range used so far today >= 80/100% of the UW forecast range (acts only from 2025-03); lv07t/lv13t = resting take at the first landscape level >= 0.7 / 1.3 x old target; lv07p = half off there, runner trail 0.5 x target; xi/rg/lv codes sit on g67a50; x7 / l7 / cbA (combined) sit on g67a70 (x7 + xi10tight, l7 + lv13t, cbA + tr100 + xi10tight + lv13t).


## AS-NR7 (live bracket, same months: income +915k, max DD -68k, worst week -37k; L6M income +463k, L6M DD -25k, L3M income +154k)

**VERDICT WEAK: best landscape exit = `tr100` (TL3_DX_AS_MF1_ls_tr100_M)**: income -54k (-5.9%), max DD gap -5k, worst-week gap -2k, L6M income +4k / DD gap +11k, L3M income -30k / DD gap +8k, NQ-down weeks +329k vs +364k, years better-DD 2 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| rg100 | 42 | -283k | -0k | +4k | -178k / +8k | -46k / +13k | -131k | -1k / -12k / -61k / -208k | WEAK |
| tr100 | 42 | -54k | -5k | -2k | +4k / +11k | -30k / +8k | -36k | -1k / -0k / -40k / -13k | WEAK |
| l7 | 42 | -190k | -17k | -3k | -119k / +5k | -64k / +8k | -108k | +4k / -4k / -90k / -100k | WEAK |
| so0 | 42 | -217k | -31k | -2k | -160k / +2k | -42k / -3k | -178k | +2k / +5k / -30k / -194k | WEAK |

## AS-RSI (live bracket, same months: income +915k, max DD -68k, worst week -37k; L6M income +463k, L6M DD -25k, L3M income +154k)

**VERDICT WEAK: best landscape exit = `so0` (TL3_DX_AS_MF2_ls_so0_M)**: income -42k (-4.5%), max DD gap +8k, worst-week gap +0k, L6M income -24k / DD gap -0k, L3M income -7k / DD gap +4k, NQ-down weeks +369k vs +364k, years better-DD 3 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| so0 | 42 | -42k | +8k | +0k | -24k / -0k | -7k / +4k | +4k | -2k / -17k / -53k / +30k | WEAK |
| tr100 | 42 | -18k | -4k | -2k | +34k / -3k | +13k / -1k | -11k | -3k / -19k / -31k / +36k | WEAK |
| g75a70 | 42 | +12k | -11k | -0k | +14k / +0k | -1k / +12k | +10k | +0k / -5k / -3k / +20k | WEAK |
| g67a70 | 42 | +5k | -12k | -0k | +8k / -0k | +4k / +13k | -1k | -1k / -2k / +4k / +4k | WEAK |
| l7 | 42 | +18k | -12k | -0k | +13k / -0k | +9k / +14k | +4k | -1k / +4k / +3k / +12k | WEAK |

## AS-VWAPBRK (live bracket, same months: income +915k, max DD -68k, worst week -37k; L6M income +463k, L6M DD -25k, L3M income +154k)

**VERDICT WEAK: best landscape exit = `tr100` (TL3_DX_AS_MF3_ls_tr100_M)**: income +205k (+22.4%), max DD gap +18k, worst-week gap -2k, L6M income -3k / DD gap +8k, L3M income -8k / DD gap +8k, NQ-down weeks +469k vs +364k, years better-DD 2 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| tr100 | 42 | +205k | +18k | -2k | -3k / +8k | -8k / +8k | +105k | -2k / +47k / +76k / +84k | WEAK |
| l7 | 42 | +175k | +17k | -4k | -28k / -6k | +14k / +4k | +85k | +7k / +52k / +109k / +8k | WEAK |
| g75a50 | 42 | +125k | +8k | -7k | +4k / +6k | -9k / +1k | +39k | +5k / +26k / +47k / +47k | WEAK |
| g67a30 | 42 | +2k | +6k | +7k | -27k / +9k | -8k / +4k | -15k | -28k / -6k / +12k / +24k | WEAK |
| lv13t | 42 | +163k | +5k | -8k | +6k / +4k | -3k / -2k | +52k | +1k / +47k / +74k / +41k | WEAK |
| so0 | 42 | -25k | -45k | -11k | -176k / -10k | -50k / -6k | +148k | +2k / +82k / +49k / -158k | WEAK |

## LO-CRUDE (live bracket, same months: income +914k, max DD -213k, worst week -107k; L6M income +528k, L6M DD -21k, L3M income +234k)

**VERDICT WEAK: best landscape exit = `so0` (TL3_DX_LO_MF1_ls_so0_M)**: income -139k (-15.2%), max DD gap -160k, worst-week gap +9k, L6M income -94k / DD gap -46k, L3M income +104k / DD gap +0k, NQ-down weeks -174k vs -95k, years better-DD 0 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| rg100 | 42 | -508k | -14k | +20k | -366k / -21k | -138k / +5k | -69k | -79k / -36k / -76k / -318k | WEAK |
| l7 | 42 | -221k | -27k | +16k | -125k / -5k | -27k / -5k | -47k | -53k / -52k / -89k / -27k | WEAK |
| g75a70 | 42 | -244k | -46k | +17k | -148k / -4k | -33k / -4k | -37k | -43k / -40k / -104k / -57k | WEAK |
| g67a70 | 42 | -172k | -46k | +9k | -102k / -5k | -13k / -5k | -26k | -55k / -47k / -102k / +32k | WEAK |
| so0 | 42 | -139k | -160k | +9k | -94k / -46k | +104k / +0k | -79k | +4k / +7k / -25k / -125k | WEAK |

## LO-ZB (live bracket, same months: income +914k, max DD -213k, worst week -107k; L6M income +528k, L6M DD -21k, L3M income +234k)

**VERDICT WEAK: best landscape exit = `so0` (TL3_DX_LO_MF3_ls_so0_M)**: income -19k (-2.1%), max DD gap +19k, worst-week gap -4k, L6M income +3k / DD gap -1k, L3M income +16k / DD gap -1k, NQ-down weeks -100k vs -95k, years better-DD 2 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| so0 | 42 | -19k | +19k | -4k | +3k / -1k | +16k / -1k | -6k | +2k / -59k / +55k / -17k | WEAK |
| g75a70 | 42 | -121k | +11k | +11k | +15k / +3k | +9k / +6k | -44k | -4k / -88k / -8k / -22k | WEAK |
| l7 | 42 | -161k | +0k | +2k | +8k / -2k | -0k / -3k | -98k | -0k / -104k / -27k / -30k | WEAK |

## NP-CONF (live bracket, same months: income +1572k, max DD -98k, worst week -65k; L6M income +467k, L6M DD -17k, L3M income +248k)

**VERDICT WEAK: best landscape exit = `tr100` (TL3_DX_NP_CONF_ls_tr100_M)**: income -154k (-9.8%), max DD gap +0k, worst-week gap +22k, L6M income -35k / DD gap -12k, L3M income -31k / DD gap -12k, NQ-down weeks +775k vs +790k, years better-DD 2 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| tr100 | 42 | -154k | +0k | +22k | -35k / -12k | -31k / -12k | -14k | +13k / -70k / -62k / -35k | WEAK |
| l7 | 42 | -86k | -0k | +9k | -9k / +1k | +22k / +1k | -60k | +28k / -72k / -19k / -24k | WEAK |
| g75a70 | 42 | -69k | -2k | +9k | -0k / +2k | +28k / +2k | -42k | +20k / -60k / -28k / -0k | WEAK |
| g67a70 | 42 | -92k | -3k | +9k | -14k / +1k | +24k / +1k | -63k | +24k / -78k / -17k / -21k | WEAK |
| g50a50 | 42 | -124k | -8k | +18k | -54k / -6k | +4k / -2k | -40k | +34k / -57k / -18k / -82k | WEAK |
| so0 | 42 | -152k | -12k | +0k | +23k / -10k | +8k / +0k | -22k | +33k / -31k / -139k / -16k | WEAK |

## NP-MACD (live bracket, same months: income +1210k, max DD -153k, worst week -52k; L6M income +521k, L6M DD -28k, L3M income +252k)

**VERDICT WEAK: best landscape exit = `so0` (TL3_DX_NP_MACD_ls_so0_M)**: income +306k (+25.3%), max DD gap +17k, worst-week gap -21k, L6M income -98k / DD gap -28k, L3M income -21k / DD gap -20k, NQ-down weeks +624k vs +542k, years better-DD 2 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| so0 | 42 | +306k | +17k | -21k | -98k / -28k | -21k / -20k | +82k | +22k / +143k / +98k / +44k | WEAK |
| g67a30 | 42 | -123k | +9k | -2k | -135k / -2k | -33k / +5k | +101k | -46k / -9k / -18k / -50k | WEAK |
| g50a30 | 42 | -32k | +4k | -2k | -128k / -4k | -35k / +6k | +168k | +6k / +30k / -18k / -51k | WEAK |
| l7 | 42 | -86k | -9k | -4k | -44k / -9k | -1k / +3k | -42k | -56k / -62k / +48k / -16k | WEAK |
| g67a70 | 42 | -63k | -10k | -5k | -49k / -5k | -3k / +3k | -33k | -43k / -57k / +62k / -25k | WEAK |

## NP-YM (live bracket, same months: income +1129k, max DD -127k, worst week -44k; L6M income +386k, L6M DD -23k, L3M income +199k)

**VERDICT WEAK: best landscape exit = `l7` (TL3_DX_NP_MF3_ls_l7_M)**: income -77k (-6.8%), max DD gap +20k, worst-week gap -3k, L6M income -12k / DD gap -2k, L3M income -17k / DD gap -3k, NQ-down weeks +516k vs +538k, years better-DD 2 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| l7 | 42 | -77k | +20k | -3k | -12k / -2k | -17k / -3k | -21k | +13k / -2k / -68k / -20k | WEAK |
| g75a30 | 42 | -172k | +5k | -13k | -64k / +3k | -45k / -2k | -60k | -17k / +5k / -80k / -80k | WEAK |
| g50a50 | 42 | -116k | -16k | -4k | +5k / +2k | -31k / -1k | -23k | -11k / -26k / -102k / +23k | WEAK |
| so0 | 42 | +205k | -29k | -1k | +63k / -13k | -51k / -18k | +96k | -35k / +32k / +179k / +29k | WEAK |

## NP-ZN (live bracket, same months: income +1129k, max DD -127k, worst week -44k; L6M income +386k, L6M DD -23k, L3M income +199k)

**VERDICT WEAK: best landscape exit = `g75a50` (TL3_DX_NP_MF2_ls_g75a50_M)**: income -10k (-0.9%), max DD gap +21k, worst-week gap +0k, L6M income -38k / DD gap -3k, L3M income +20k / DD gap +2k, NQ-down weeks +477k vs +538k, years better-DD 2 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| rg80 | 42 | -324k | +21k | +0k | -169k / +7k | -91k / +2k | -245k | -31k / +54k / -88k / -258k | WEAK |
| g75a50 | 42 | -10k | +21k | +0k | -38k / -3k | +20k / +2k | -60k | -48k / +80k / +33k / -74k | WEAK |
| tr100 | 42 | -119k | +7k | +0k | -36k / +3k | -45k / +0k | -61k | +15k / +12k / -77k / -69k | WEAK |
| so0 | 42 | -164k | +6k | -27k | -57k / +3k | -36k / +0k | +9k | +17k / +12k / -137k / -56k | WEAK |
| g75a70 | 42 | +2k | -7k | +0k | +9k / -5k | +38k / +0k | -51k | -25k / -15k / +48k / -5k | WEAK |
| l7 | 42 | +8k | -11k | +0k | -9k / -6k | +22k / +0k | -58k | -19k / -11k / +59k / -21k | WEAK |

## NY-FIB (live bracket, same months: income +3498k, max DD -164k, worst week -110k; L6M income +1463k, L6M DD -35k, L3M income +507k)

**VERDICT WEAK: best landscape exit = `so0` (TL3_DX_NY_MF1_ls_so0_M)**: income -21k (-0.6%), max DD gap +9k, worst-week gap +0k, L6M income -91k / DD gap -4k, L3M income -52k / DD gap +1k, NQ-down weeks +1299k vs +1353k, years better-DD 2 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| so0 | 42 | -21k | +9k | +0k | -91k / -4k | -52k / +1k | -55k | +9k / +53k / +23k / -106k | WEAK |
| g75a70 | 42 | -243k | -52k | +0k | -63k / +8k | -94k / -13k | +48k | -21k / -59k / +67k / -230k | WEAK |
| l7 | 42 | -502k | -71k | +0k | -54k / -2k | -116k / -23k | -282k | -77k / -135k / -60k / -230k | WEAK |
| lv07t | 42 | -428k | -79k | -12k | -62k / -10k | -162k / -31k | -283k | -81k / -173k / +23k / -197k | WEAK |

## NY-NODE (live bracket, same months: income +3498k, max DD -164k, worst week -110k; L6M income +1463k, L6M DD -35k, L3M income +507k)

**VERDICT WEAK: best landscape exit = `g50a30` (TL3_DX_NY_MF4_ls_g50a30_M)**: income -299k (-8.5%), max DD gap +25k, worst-week gap +20k, L6M income -265k / DD gap +12k, L3M income -46k / DD gap +1k, NQ-down weeks +1076k vs +1353k, years better-DD 3 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| g50a30 | 42 | -299k | +25k | +20k | -265k / +12k | -46k / +1k | -277k | -93k / -40k / -76k / -90k | WEAK |
| g75a70 | 42 | +5k | +25k | -4k | +2k / +2k | +37k / +5k | -117k | -37k / +46k / +85k / -90k | WEAK |
| l7 | 42 | +14k | +18k | -8k | -3k / -8k | +38k / +6k | -34k | -17k / +23k / +92k / -84k | WEAK |
| so0 | 42 | -257k | -43k | -9k | -575k / -44k | -183k / -65k | +58k | +72k / +46k / +164k / -540k | WEAK |

## NY-OFI (live bracket, same months: income +3498k, max DD -164k, worst week -110k; L6M income +1463k, L6M DD -35k, L3M income +507k)

**VERDICT WEAK: best landscape exit = `g50a50` (TL3_DX_NY_MF5_ls_g50a50_M)**: income -6k (-0.2%), max DD gap +4k, worst-week gap +7k, L6M income +37k / DD gap +5k, L3M income +26k / DD gap -2k, NQ-down weeks +1333k vs +1353k, years better-DD 0 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| g50a50 | 42 | -6k | +4k | +7k | +37k / +5k | +26k / -2k | -20k | +70k / -164k / +14k / +74k | WEAK |
| g67a70 | 42 | +21k | +2k | +10k | -30k / +0k | -7k / -0k | +77k | +16k / -12k / +36k / -20k | WEAK |
| l7 | 42 | +34k | -2k | +10k | -21k / +0k | -6k / +2k | +87k | +22k / -2k / +8k / +6k | WEAK |
| g50a30 | 42 | -127k | -4k | +8k | +32k / +9k | +23k / -7k | -53k | +97k / -202k / -63k / +41k | WEAK |
| so0 | 42 | -160k | -29k | +1k | -96k / -5k | -22k / -11k | -154k | +33k / -38k / -97k / -57k | WEAK |

## NY-VALUE (live bracket, same months: income +3498k, max DD -164k, worst week -110k; L6M income +1463k, L6M DD -35k, L3M income +507k)

**VERDICT WEAK: best landscape exit = `so0` (TL3_DX_NY_MF2_ls_so0_M)**: income -24k (-0.7%), max DD gap -5k, worst-week gap +12k, L6M income -208k / DD gap -61k, L3M income -246k / DD gap -82k, NQ-down weeks +1713k vs +1353k, years better-DD 2 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| so0 | 42 | -24k | -5k | +12k | -208k / -61k | -246k / -82k | +360k | +91k / +26k / -169k / +28k | WEAK |
| l7 | 42 | -166k | -10k | +1k | -82k / +3k | -65k / +3k | -90k | +74k / -67k / -79k / -95k | WEAK |
| g67a70 | 42 | -114k | -26k | +6k | -83k / -2k | -63k / +2k | -56k | +98k / -85k / -65k / -61k | WEAK |
