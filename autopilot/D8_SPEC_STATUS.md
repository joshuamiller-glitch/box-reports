**NY AM STAGE 1 ONE DATE LINE (simulated mix with handoff of empty streams, fleet 13272 /h measured / 5076 /h lead / 4000 low): NY AM first looks end 2026-11-20 02:24Z; NY AM stream incl. other-book REPLACE rows ends **2026-11-20 02:24Z** (low case 2026-11-20 06:48Z); follow-ups of strict passers end 2026-11-20 01:48Z (exit rows also wait for the unbuilt exit families ~21:00Z); FLEET-WIDE stage 1 (Asia + NY AM) ends **2026-11-20 02:30Z** (2 h); combination stage: W-COMBO; LONG POLE: NY AM stream: the other-book REPLACE rows (0 set-months after the first looks).**

Updated 2026-11-20 00:30Z by W-NYENG. **RULE (order 1337Z): NO D8 build spec until the Asia AND NY AM ladders are COMPLETE**: every ladder cell has its first look, and every cell that beats a live book has prior years, controls, layers, exit run and the today / REPLACE / ADD pick. No wave dates. London and NY PM follow (stages 2 and 3). Funnel model redone at 14:00Z from landed data (order 1400Z).

## STAGE 1 COMPLETE (Asia + NY AM): THREE dates from a funnel with explicit stage pass rates, at the current rate **13878 set-months/h** (HEALTH.md fleet rate; tp_admit last hour says a different number at times; W-COMPILED factor not yet available, W-FASTLADDER share not included)

**Funnel stages and rates read from landed NY AM data:** (1) first look: 1227 of 4557 ladder cells have REPLACE last-6-month + last-3-month rows; (2) BEATER under the W-ASIA gate (a REPLACE row beats today stack on BOTH L6M and L3M: ulcer lower, mean not lower, worst week and max DD not worse): **0.7% of looked-at cells (9 of 1227); 0.4% with a REPLACE-K7 row; the looser rule (ulcer < 0 and mean >= 0 only) gives 1.8% (22)** (uncalibrated, label BETTER; calibration caveat: the whole-search null gives per-mode FDR both-side 8-25%, long-only 12-18%, i.e. a share of these yes rows is noise); (3) PASS prior years + persistence (rule B: no RED year in 2023/24/25; pooled persistence >= 0.58): **7 of 11 yes rows with all three prior years landed pass = 64%** (3 of 7 cells); the 4 REPLACE-K7 beaters: 3 pass (L01811caa, L6a25b155 pass, L0f097450 RED 2023); Asia: 8 passers among the beaters evaluated (W-ASIA); (4) only PASSERS get 30 controls (ADD and REPLACE variants: 2 x 180), layers (347, W-LAYERS cost) and exit rows (438) = 896 set-months per passer; every beater gets prior years (37 per beating REPLACE set). REPLACE ONLY (order 1407Z): ADD rows are reference, not candidates, and are no longer queued; exit rows = top 3 recipes x REPLACE x (6+37) + 30 controls x 6 = 309.

**Remaining set-months that do NOT depend on the funnel:** NY AM first looks, REPLACE rows only, 16209 (16209 queued + -1936 unbuilt cells x 6; 6493 of 4557 cells built) + NY AM REPLACE vs the other live books for alive cells 74394 + Asia useful work as W-ASIA counts it after its gate (first looks 27k + a2 35k = 62000; follow-ups 4k prior years + 20k controls + 1.6k passer controls + 8 passers x layers/exit = 31880; total ~88k+). GATE applied to NY AM in the advance step at 14:25Z (same as Asia): prior years and controls only for sets that beat today stack on BOTH L6M and L3M; other cells wait in stage A2 for their a2 rows and drop out if none beats; 6,290 prior-year/control lines of non-beating sets were PARKED (parked_gate_1415.txt, 112 cells; 76 cells returned to A2).

| scenario | NY AM beaters share / pass rate | NY AM beaters -> passers | Asia beaters share / pass | NY AM follow-ups | Asia follow-ups | TOTAL set-months | hours | **STAGE 1 COMPLETE** |
|---|---|---|---|---|---|---|---|---|
| LOW (strict gate, half the measured share) | 0.4% / 50% | 17 -> 8 | 2.2% / 50% | 8312 | 15940 | 176855 | 13 | **2026-11-20 13:14Z** |
| BASE (STRICT gate, measured share less mid FDR) | 0.6% / 64% | 28 -> 18 | 3.0% / 64% | 17291 | 21736 | 191630 | 14 | **2026-11-20 14:18Z** |
| HIGH (strict gate, 3x: the a2 other-book rows add chances) | 2.2% / 80% | 100 -> 80 | 4.4% / 80% | 76825 | 31880 | 261308 | 19 | **2026-11-20 19:20Z** |
| VARIANT: LOOSER gate (ulcer < 0 and mean >= 0 only), measured share less mid FDR | 1.5% / 64% | 68 -> 43 | 3.0% / 64% | 42266 | 21736 | 216606 | 16 | **2026-11-20 16:06Z** |
| UPPER BOUND: every REPLACE beater gets everything (10% NY AM / 6.5% Asia) | 10.0% / 100% | 456 -> 456 | 6.5% / 100% | 430788 | 47095 | 630487 | 45 | 2026-11-21 21:56Z |

Scenario assumptions (REPLACE ONLY, STRICT gate = ulcer lower, mean not lower, worst week and max DD not worse on L6M and L3M): measured strict share 0.7%; LOW = half of it, 50% pass; BASE = the measured share minus the mid FDR 16.5% (calibration), pass rate = observed on the loose REPLACE yes rows (64%); HIGH = 3x the strict share, 80% pass; the LOOSER-gate row is a variant only. SMALL SAMPLE: 1227 REPLACE looks. Asia beater share 2.4% (W-ASIA strict rule: 15 of 614) / 4.4% / 6.5% (looser rule 50 of 766), Asia pass rates as NY AM. First looks alone (NY AM 16209 + Asia 62000) end 2026-11-20 06:08Z. CAVEAT: the observed beater share comes from the cells looked at so far, which are the BEST screen-ranked ones (the ladder runs in rank order), so extrapolating it to all 9,081 cells over-states the BASE and HIGH rows; the true beater share of the tail is probably lower (LOW is the REPLACE-only bound). The biggest remaining uncertainty is the beater and pass share; the null calibration (R4) and the persistence/rule-B gates move it.

## ENGINE-SLOT SPLIT (re-proposed from remaining FIRST LOOKS, then gate-pass follow-ups; NOT applied)

Remaining first looks: Asia 62000 vs NY AM 16209 (+74394 NY AM other-book rows) => **Asia 79% / NY AM 21%** (41% / 59% with the other-book rows) = ~5638 / ~8240 set-months/h at 13878/h; with the base-case follow-ups added the work ratio is NY AM 56% / Asia 44% (NY AM follow-ups 17291 vs Asia 21736): the follow-ups only exist for cells that pass, so they come AFTER the first looks, are small until prior years land, and are taken first by the mix when they appear. Proposal: start at **Asia 79% / NY AM 21%** (remaining first looks only; the other-book REPLACE rows are ordered behind the first looks of both ladders) and re-propose when the funnel is re-measured (each refresh of this page recomputes it). W-ASIA's passer controls (_asi/first.txt) stay first, my gate-pass follow-ups stay first in pending_l.txt / the front of pending_r5.txt; the mix file puts both unmixed ahead of the interleaved block. NY AM at the order's ~120/h would leave 899 h of work. NOT applied: the QUEUES.txt edit (replace the _asi/pending.txt and _nye/pending_r5.txt lines by /mnt/l2/l2vast/_split/pending_mix.txt, built by code/th_nyeng/ny_mix.py <NYAM share>, e.g. 0.41) waits for the lead.

## Early-rung exits (4c): lines queued for cells that already left the ladder

Cells with stage "out" in the NY advance state: 677. Later-rung lines (other-book, prior-year, control) still queued for them: **20862** (the advance step queues a later rung only after the earlier one passes). Park rule: any such line goes to /mnt/l2/l2vast/_nye/parked_out_cells.txt (not deleted). Exclusion list for W-DEDUP: cell ids with stage out = L0005282f, L0018ff2b, L0044a103, L00e9ef7d, L00ef412d, L01ae185e, L01b83d93, L02307192, L027c6cc7, L02831614, L029c1536, L031c8045, L045258ba, L047eebef, L0612a129, L06306ccb, L063c1550, L064f893e, L065c2291, L066b4da5, L0705a05d, L076bc130, L08c1815f, L08c38a8a, L094ee8e5, L09c9a917, L0ae4276c, L0affdff7, L0bac981a, L0bd23639, L0cb34690, L0d7bea1f, L0ddd0c84, L0ebb3bcd, L0eeaa018, L0f097450, L0f11d2f7, L1020a386, L10d4c341, L11089f98, L121542b3, L1229e64c, L13e165bc, L143274ab, L153a9ab3, L15658e51, L1589e0b8, L15e18f8b, L16344500, L16653aa0, L175f93d1, L1801f948, L189d197c, L18ab065e, L18eca11f, L18f42af2, L1920a20b, L19c3031f, L1a10b4db, L1a9381e0, L1aa656d8, L1afa7095, L1b0fee34, L1b77a301, L1bd2be11, L1beb50d9, L1c0f69fd, L1ce5c41b, L1ce61a64, L1d01954c, L1d0a98af, L1e0094b0, L1ec8e6ba, L201241f4, L2013a2c5, L2140f591, L21bffd7e, L21f079b6, L2230e4ef, L228a2c4a, L22b5c5d1, L22cf3215, L23b82a1a, L2438b7d7, L24e2abe5, L24ec3736, L255ca251, L2645ba76, L264d7e66, L2658360c, L26d0772f, L27a925f8, L27a93ead, L280828cf, L28393d3d, L28c3922b, L28e26f99, L28e7ee31, L29e37d0c, L2b44c03d, L2bc649b6, L2becd23c, L2bf347e6, L2cc89f59, L2cd163fd, L2d1b439e, L2d406d8d, L2d60df7d, L2db980e5, L2dbb7680, L2e45679e, L2eb9ac1b, L2ed2f633, L2ed70e23, L2fa1b60e, L30ae34bf, L30e2c8aa, L31000131, L3122d86b, L312ec721, L317eb843, L32591d74, L334ee144, L3426e2ca, L34d66961, L3516aa98, L359f1868, L36dfa540, L36fefaed, L3701b464, L37897907, L384f5251, L385ef576, L38ff2b59, L39ed8ccd, L39f71c1e, L3a2694e8, L3a715e8f, L3ab5aa26, L3c82df8a, L3cf3cc92, L3d5908cd, L3dabd7b1, L3e4745d2, L3e6ebc24, L3eb6b968, L3eba69b2, L3f67e925, L3fbe0f8d, L4023189a, L40f3022e, L41042978, L413810a9, L414e1c01, L416cf628, L41d3a8da, L41eda10c, L42591c98, L42935176, L42a44cee, L439967d6, L43f0cbfb, L440aa51b, L44290ea7, L4466aa9d, L453ecfdf, L45bbaa6b, L45e72f8b, L4661e113, L46c24b4c, L474262d9, L4744d92c, L47a52047, L47e7770d, L4932c506, L4a47ecfe, L4add28dc, L4aeda76f, L4b441c50, L4c001809, L4d1c3ef6, L4d45ba78, L4d6fa935, L4dcb4c69, L4e89079d, L4ebf6aef, L4ee926f6, L4fad2a44, L4fe05261, L4fe091df, L50480de3, L50ac6ff3, L50b89fdd, L51485330, L51770ecd, L518184b0, L523f4d50, L52599445, L52d28a9a, L5328b71c, L537ea1d3, L53aaee00, L542e900e, L545ccc02, L54adb58c, L54d8b908, L54f86171, L55b31b0a, L55bd963b, L55d44545, L55ee1500, L56accca6, L56dd415f, L56e69508, L56ea5eb4, L5733d1ad, L5761ce13, L57d8c47a, L5814d305, L587b902b, L5916c8ec, L597837ab, L59855e53, L598b62a5, L59b2e323, L59bcb8a0, L59ccbd13, L59db90b2, L5a49e86d, L5a4f924e, L5bb9ae2f, L5c4c8c9a, L5c621a0e, L5ca77208, L5ce83827, L5d3f1a13, L5d9313d2, L5d98fe32, L5ea34e54, L5f405e4b, L60367862, L60936dc9, L60aed383, L6118cace, L617f2c33, L62a6a6b7, L631a8535, L632bb3c8, L638c37cf, L63b1d509, L64299ed3, L649a387a, L64a0b978, L652327d9, L65e06e99, L66b909fe, L6755b324, L6772d676, L67e9df70, L68413e62, L68f4e8d6, L69514a8f, L6af3e195, L6b5f4955, L6c027ebe, L6cb86f62, L6cdb09b8, L6cef7ca5, L6cfe503f, L6d0ae138, L6dc6bb7f, L704d02a2, L70823d25, L70fbd6a7, L70fd7253, L731f3a21, L734ab4c9, L73b20f78, L75194540, L75313db5, L755b7b45, L75ad06c2, L75c2b2e8, L75ebbf7e, L769fdf33, L76c6e684, L76f6d4d9, L77082875, L7726a37e, L775c6ba4, L7950d9dc, L7aed5f8b, L7af47322, L7b2166a5, L7ce10fc0, L7d2c80d3, L7dda4ced, L7ead5d0a, L7ebc49f8, L7f23f0d5, L7fa34284, L7fc2dbc1, L7fc96650, L803fc54c, L80601a3c, L80f5d118, L81496bc7, L815801d4, L81a1349f, L821971d5, L82db62cd, L830279e4, L8320d626, L840f5f7e, L848867d4, L8553d968, L8580e226, L861aa3a3, L862d9ab1, L87220a58, L8820726f, L887adb85, L889c761a, L8989cde7, L8a3173ce, L8a4907eb, L8a68ae23, L8a7d04c3, L8a8dd5b7, L8ab51756, L8b3681a5, L8b83a467, L8be740c3, L8c4b5096, L8d47873d, L8d78e68e, L8db3d632, L8dcfb4d2, L8dfb9b8c, L8e8dc6f4, L8eca41a9, L8f00668e, L8f47a7f4, L8fe0dc6f, L9014a4d5, L90842741, L90aedba2, L9106a04a, L9118c160, L9120c667, L928ee468, L9365ece7, L9397d8c8, L93e7f7e5, L94012503, L943b82de, L948f2a7e, L9513708b, L955779bc, L957a0544, L95b1cc17, L962501c9, L96424791, L964cfc29, L966b7824, L966b7e14, L973aa7a1, L984a3d00, L98834592, L98a567fd, L99000f8d, L9978660d, L99c985bf, L9a60042a, L9aa810ff, L9ade175b, L9c2f04fe, L9c4e7b7c, L9cb68314, L9e449cb7, L9e706c57, L9f43c17a, L9f888218, L9fc0238e, La059a8e8, La087e948, La092861b, La0e358d7, La173c238, La1ed8df7, La201dd83, La234f575, La2cff349, La372e6e4, La3e5bc8e, La3e7712e, La53db301, La583c5aa, La5a1a5ec, La6102ffc, La62b0509, La6a45b1a, La6c0ac4d, La6c7c86a, La6e1543c, La71c16a2, La767493f, La8600386, La86531b2, La872937f, La894b287, La8a5e841, La8f7d729, La96512f6, La96d4160, La9ab8331, Laa0b84bc, Laac6b61d, Lab0ec3ca, Lab7654ec, Lab808296, Lab985018, Labb60ea5, Labf3c62a, Lac62031d, Lad357def, Lad63c18b, Lad9f94cb, Laddc32be, Ladec93ae, Lae1b59ec, Laf22310b, Laf83feb6, Lb13de797, Lb1626f1e, Lb23d399b, Lb248e87c, Lb28f30c8, Lb309c9b6, Lb35e02b8, Lb37b2695, Lb3d8483f, Lb3dbcf28, Lb46d2b5d, Lb4b1526a, Lb4ee29cb, Lb4efe93c, Lb5101a28, Lb522f24c, Lb52cf323, Lb549d698, Lb5d2fb00, Lb68a4cab, Lb6ffbdd5, Lb7a000dd, Lb7db97e8, Lb809e889, Lb8da6068, Lb8fe4f02, Lb9026469, Lb9673779, Lb9818bde, Lb9c7c06a, Lba356762, Lbb00ef18, Lbb258b12, Lbb44a057, Lbb5b84f5, Lbb5e0a25, Lbb6282e1, Lbb8dc803, Lbbb39855, Lbbb92057, Lbbc4bf98, Lbbdd2890, Lbc4ad3b5, Lbcc110fa, Lbcd1ab36, Lbd1a1d57, Lbdf8bcd7, Lbe00943c, Lbe0cbeff, Lbe22da27, Lbe660734, Lbe9e3d0d, Lbf234099, Lbf545353, Lbfdb7dfe, Lc02f38c2, Lc06cbfac, Lc08f2494, Lc0aecc18, Lc0d81f93, Lc0dd72a1, Lc22d07b2, Lc2b684bb, Lc3736705, Lc38f3a49, Lc3ec3a0b, Lc43862b6, Lc4e81ec2, Lc594c76e, Lc5ff363e, Lc66b8fed, Lc723e512, Lc7333ae2, Lc7e078a6, Lc7edb246, Lc80e2b3b, Lc82a4584, Lc889083d, Lc8d51dc7, Lc988cdd9, Lca2ed2a5, Lca409c7e, Lca57ebf7, Lca715459, Lccba36a3, Lcccca0ec, Lcd1b77c9, Lcd4b0473, Lcd80dfef, Lcd9d9059, Lcdc45c44, Lcdd6a540, Lce070e31, Lce1c241f, Lce34df6d, Lce4b6104, Lcef44bf0, Lcfbaf18c, Lcfdf6a30, Lcfe53f35, Ld05d76e4, Ld0eb2c83, Ld1499727, Ld1a8a78d, Ld2339be1, Ld2537ef3, Ld2d5b852, Ld3898b7a, Ld40c5e85, Ld4434fb1, Ld4cb48d4, Ld4ffc994, Ld52800f7, Ld5c3069b, Ld62c5532, Ld6468e0c, Ld6f467f5, Ld7278aa9, Ld7a70858, Ld7b0b337, Ld87ff441, Ld95ec786, Ld9b4da69, Ld9bd4b7e, Lda27b4d8, Lda741b04, Ldaec8f96, Ldaf19410, Ldc1b06a0, Ldcdc2f39, Ldd296159, Ldd5dd7c3, Ldd6284ee, Ldda3fdd8, Lde046d66, Lde72d37e, Ldead827c, Ldecfe020, Ldf51c69e, Le0089501, Le0bf852b, Le0d695f3, Le0da99e2, Le1a69b6c, Le1b9bdf2, Le1cf849f, Le1f36da0, Le27dc486, Le30d987f, Le3193838, Le36ba157, Le3dd1918, Le494ddab, Le4bbdc2f, Le5019545, Le5148785, Le534251c, Le5457a79, Le54a1a93, Le65f7dfd, Le6693872, Le6986a73, Le6edc0a0, Le727d1fa, Le74aaf47, Le788e239, Le7ab4d85, Le8370942, Le8403d39, Le86bf5b5, Le944b0b0, Le96a00db, Lea3ea462, Lea620d76, Leac51c1d, Lec4e334f, Lec6afe3f, Lec804905, Led8d70a3, Leddd6d68, Lee8c3266, Lee8cb424, Lef1792aa, Lefa05e76, Lefe43a1e, Lf024d52e, Lf04cbe7d, Lf0aacb4f, Lf11c3d85, Lf11e08be, Lf24a84da, Lf25a4095, Lf29cffba, Lf328379c, Lf3466e88, Lf3741df0, Lf3c276f9, Lf4224a5d, Lf46de2b6, Lf4900ad5, Lf506479f, Lf63aeb97, Lf64b0403, Lf67c3049, Lf6be7f5f, Lf74144f7, Lf76e3db4, Lf837960b, Lf8cf358d, Lf8e1a552, Lf9224ca2, Lf94730bc, Lf967df3b, Lfa5912ed, Lfa59be33, Lfadf2fcc, Lfaf84902, Lfb16b890, Lfb69580e, Lfb7da229, Lfbcde421, Lfc41c8c2, Lfc8753c0, Lfc8a41f2, Lfcba7672, Lfcf3e0b2, Lfd3fc422, Lfd4c2d53, Lfd763b0d, Lfdce94ab, Lfdd046b4, Lfe00f53f, Lfe2dbc4b, Lfe4cf0cb, Lfe63b474, Lfe900eef, Lfee6ee88, Lff5bd358, Lff8cabe0, Lff9aa73b, Lffb0f715, Lffb1b796, Lffd711a2, Lffe0b8bb (file /mnt/l2/l2vast/_nye/ladder_adv_state.json, key stage starting with "out"); W-DEDUP does the sweep, I own the advance logic.


## Candidates under the persistence >= 0.58 gate and the ADD-vs-REPLACE rule (order 1324Z)

Rules (order 1407Z): REPLACE ONLY. The pick is always the REPLACE row; the ADD row is shown as a reference, not a candidate (supersedes the 1324Z ADD rule). REPLACE = the ADD stack with K7 switched off in the NY AM session, so the ADD stack WITHOUT K7 already exists as the REPLACE row: NO new "minus K7" engine set is needed (a K7-off-in-every-session set would only matter for K7's other sessions, which these rows leave untouched). Persistence = share of non-overlapping 2-week windows where the new stack is not worse than today's, POOLED over every month the set has run (last 6 months + prior years). Rule B colours from ny_ruleb (RED > 30% worse in a prior year). Stack columns are the whole stack (ulcer / max DD / worst week / mean $ per week, engine base lots, $4.84).

| cell | stack | window | ulcer | max DD | worst wk | mean $/wk | rule-B colour (worst %) |
|---|---|---|---|---|---|---|---|
| L01811caa | TODAY (JL3) | L6M | 9416 | -31109 | -15728 | +18755 | - |
| L01811caa | REPLACE (candidate) | L6M | 9342 | -29253 | -15108 | +20510 | n/a (recent window) (-1%) |
| L01811caa | ADD (reference, not a candidate) | L6M | 8963 | -27538 | -14519 | +19873 | n/a (recent window) (-5%) |
| L01811caa | TODAY (JL3) | L3M | 11035 | -31109 | -15728 | +16098 | - |
| L01811caa | REPLACE (candidate) | L3M | 10587 | -28995 | -13266 | +18707 | n/a (recent window) (-4%) |
| L01811caa | ADD (reference, not a candidate) | L3M | 10165 | -27538 | -11702 | +17640 | n/a (recent window) (-8%) |
| L01811caa | TODAY (JL3) | Y2025 | 33572 | -91441 | -38896 | +6846 | - |
| L01811caa | REPLACE (candidate) | Y2025 | 29382 | -83155 | -34691 | +7360 | GREEN (-8%) |
| L01811caa | ADD (reference, not a candidate) | Y2025 | 27815 | -78940 | -38025 | +7984 | GREEN (-2%) |
| L01811caa | TODAY (JL3) | Y2024 | 28856 | -72026 | -37355 | +4549 | - |
| L01811caa | REPLACE (candidate) | Y2024 | 24716 | -69388 | -39713 | +5169 | GREEN (+6%) |
| L01811caa | ADD (reference, not a candidate) | Y2024 | 25450 | -71363 | -38560 | +5073 | GREEN (+3%) |
| L01811caa | TODAY (JL3) | Y2023 | 18908 | -41848 | -17538 | +1797 | - |
| L01811caa | REPLACE (candidate) | Y2023 | 15029 | -46397 | -21702 | +2254 | AMBER (+24%) |
| L01811caa | ADD (reference, not a candidate) | Y2023 | 16062 | -40960 | -18785 | +2944 | GREEN (+7%) |
| L6a25b155 | TODAY (JL3) | L6M | 9416 | -31109 | -15728 | +18755 | - |
| L6a25b155 | REPLACE (candidate) | L6M | 9238 | -29945 | -16733 | +19675 | n/a (recent window) (+6%) |
| L6a25b155 | ADD (reference, not a candidate) | L6M | 8981 | -28489 | -15872 | +19216 | n/a (recent window) (+1%) |
| L6a25b155 | TODAY (JL3) | L3M | 11035 | -31109 | -15728 | +16098 | - |
| L6a25b155 | REPLACE (candidate) | L3M | 10415 | -29945 | -16733 | +17400 | n/a (recent window) (+6%) |
| L6a25b155 | ADD (reference, not a candidate) | L3M | 10159 | -28489 | -15872 | +17034 | n/a (recent window) (+1%) |
| L6a25b155 | TODAY (JL3) | Y2025 | 33572 | -91441 | -38896 | +6846 | - |
| L6a25b155 | REPLACE (candidate) | Y2025 | 34575 | -93892 | -39081 | +7356 | GREEN (+3%) |
| L6a25b155 | ADD (reference, not a candidate) | Y2025 | 31437 | -91723 | -43606 | +8231 | GREEN (+12%) |
| L6a25b155 | TODAY (JL3) | Y2024 | 28814 | -72026 | -37355 | +4549 | - |
| L6a25b155 | REPLACE (candidate) | Y2024 | 31815 | -69700 | -36113 | +5300 | GREEN (+10%) |
| L6a25b155 | ADD (reference, not a candidate) | Y2024 | 32304 | -71936 | -34960 | +5448 | GREEN (+12%) |
| L6a25b155 | TODAY (JL3) | Y2023 | 18908 | -41848 | -17538 | +1797 | - |
| L6a25b155 | REPLACE (candidate) | Y2023 | 18087 | -48220 | -18408 | +2404 | AMBER (+15%) |
| L6a25b155 | ADD (reference, not a candidate) | Y2023 | 15491 | -42932 | -16215 | +3088 | GREEN (+3%) |
| L0f097450 (twin of L21f079b6) | TODAY (JL3) | L6M | 9416 | -31109 | -15728 | +18755 | - |
| L0f097450 (twin of L21f079b6) | REPLACE (candidate) | L6M | 9358 | -29253 | -18848 | +21047 | n/a (recent window) (+20%) |
| L0f097450 (twin of L21f079b6) | ADD (reference, not a candidate) | L6M | 8621 | -25734 | -16524 | +20446 | n/a (recent window) (+5%) |
| L0f097450 (twin of L21f079b6) | TODAY (JL3) | L3M | 11035 | -31109 | -15728 | +16098 | - |
| L0f097450 (twin of L21f079b6) | REPLACE (candidate) | L3M | 10531 | -28828 | -18848 | +19000 | n/a (recent window) (+20%) |
| L0f097450 (twin of L21f079b6) | ADD (reference, not a candidate) | L3M | 9463 | -24538 | -15633 | +18174 | n/a (recent window) (-1%) |
| L0f097450 (twin of L21f079b6) | TODAY (JL3) | Y2025 | 33572 | -91441 | -38896 | +6846 | - |
| L0f097450 (twin of L21f079b6) | REPLACE (candidate) | Y2025 | 27735 | -77634 | -32511 | +6709 | GREEN (+2%) |
| L0f097450 (twin of L21f079b6) | ADD (reference, not a candidate) | Y2025 | 26308 | -76028 | -34457 | +7579 | GREEN (-11%) |
| L0f097450 (twin of L21f079b6) | TODAY (JL3) | Y2024 | 28856 | -72026 | -37355 | +4549 | - |
| L0f097450 (twin of L21f079b6) | REPLACE (candidate) | Y2024 | 26900 | -63077 | -38237 | +5219 | GREEN (+2%) |
| L0f097450 (twin of L21f079b6) | ADD (reference, not a candidate) | Y2024 | 28023 | -66257 | -35122 | +5297 | GREEN (-3%) |
| L0f097450 (twin of L21f079b6) | TODAY (JL3) | Y2023 | 19039 | -41848 | -17538 | +1797 | - |
| L0f097450 (twin of L21f079b6) | REPLACE (candidate) | Y2023 | 17341 | -46048 | -25258 | +1675 | RED (+44%) |
| L0f097450 (twin of L21f079b6) | ADD (reference, not a candidate) | Y2023 | 16744 | -46713 | -19840 | +2334 | GREEN (+13%) |
| L3701b464 (twin of L21f079b6) | TODAY (JL3) | L6M | 9416 | -31109 | -15728 | +18755 | - |
| L3701b464 (twin of L21f079b6) | REPLACE (candidate) | L6M | 9358 | -29253 | -18848 | +21047 | n/a (recent window) (+20%) |
| L3701b464 (twin of L21f079b6) | ADD (reference, not a candidate) | L6M | 8621 | -25734 | -16524 | +20446 | n/a (recent window) (+5%) |
| L3701b464 (twin of L21f079b6) | TODAY (JL3) | L3M | 11035 | -31109 | -15728 | +16098 | - |
| L3701b464 (twin of L21f079b6) | REPLACE (candidate) | L3M | 10531 | -28828 | -18848 | +19000 | n/a (recent window) (+20%) |
| L3701b464 (twin of L21f079b6) | ADD (reference, not a candidate) | L3M | 9463 | -24538 | -15633 | +18174 | n/a (recent window) (-1%) |
| L3701b464 (twin of L21f079b6) | TODAY (JL3) | Y2025 | 33572 | -91441 | -38896 | +6846 | - |
| L3701b464 (twin of L21f079b6) | REPLACE (candidate) | Y2025 | 27735 | -77634 | -32511 | +6709 | GREEN (+2%) |
| L3701b464 | ADD | Y2025 | pending | | | | |
| L3701b464 (twin of L21f079b6) | TODAY (JL3) | Y2024 | 28856 | -72026 | -37355 | +4549 | - |
| L3701b464 (twin of L21f079b6) | REPLACE (candidate) | Y2024 | 26900 | -63077 | -38237 | +5219 | GREEN (+2%) |
| L3701b464 | ADD | Y2024 | pending | | | | |
| L3701b464 (twin of L21f079b6) | TODAY (JL3) | Y2023 | 19039 | -41848 | -17538 | +1797 | - |
| L3701b464 (twin of L21f079b6) | REPLACE (candidate) | Y2023 | 17341 | -46048 | -25258 | +1675 | RED (+44%) |
| L3701b464 | ADD | Y2023 | pending | | | | |

| cell | pooled persistence REPLACE (months) | pooled persistence ADD (months) | RED years REPLACE / ADD | PICK | what is still needed |
|---|---|---|---|---|---|
| L01811caa | 0.59 (43 mo) | 0.60 (43 mo) | none / none | **REPLACE** (REPLACE: better on ulcer and mean $/wk, no RED year, pooled persistence 0.59 >= 0.58) [STRICT PASS (ulcer, mean, worst week and max DD all not worse on L6M and L3M)] | 30 date-shift controls (queued; scored in the controls section), layers one at a time then joint (not started: ~1,068 set-months, layer-set builder manual), exit run 68 recipes + engine exit rows (families unbuilt) |
| L6a25b155 | 0.59 (43 mo) | 0.65 (43 mo) | none / none | **REPLACE** (REPLACE: better on ulcer and mean $/wk, no RED year, pooled persistence 0.59 >= 0.58) [fails the STRICT criterion: WORST WEEK L6M worse by $1005; WORST WEEK L3M worse by $1005: BEST-AVAILABLE-NOT-PROVEN, Josh decides] | 30 date-shift controls (queued; scored in the controls section), layers one at a time then joint (not started: ~1,068 set-months, layer-set builder manual), exit run 68 recipes + engine exit rows (families unbuilt) |
| L0f097450 (twin of L21f079b6) | 0.55 (43 mo) | 0.58 (43 mo) | Y2023 / none | **none yet** (REPLACE: RED Y2023; persistence 0.55 < 0.58) [fails the STRICT criterion: WORST WEEK L6M worse by $3120; WORST WEEK L3M worse by $3120: BEST-AVAILABLE-NOT-PROVEN, Josh decides] | 30 date-shift controls (queued; scored in the controls section), layers one at a time then joint (not started: ~1,068 set-months, layer-set builder manual), exit run 68 recipes + engine exit rows (families unbuilt) |
| L3701b464 (twin of L21f079b6) | 0.55 (43 mo) | 0.59 (10 mo) | Y2023 / none | **none yet** (REPLACE: RED Y2023; persistence 0.55 < 0.58) [fails the STRICT criterion: WORST WEEK L6M worse by $3120; WORST WEEK L3M worse by $3120: BEST-AVAILABLE-NOT-PROVEN, Josh decides] | 30 date-shift controls (queued; scored in the controls section), layers one at a time then joint (not started: ~1,068 set-months, layer-set builder manual), exit run 68 recipes + engine exit rows (families unbuilt) |

**Candidates passing recent months + no RED year + persistence >= 0.58:** L01811caa (REPLACE), L6a25b155 (REPLACE).
**Dates:** 30 controls: queued at the front (landing as the fleet reaches them, ~06 hours at 2,000 sm/h); layers + exit run: the layer programme per candidate is ~1,068 set-months (about 0.5 h of fleet) but needs the automatic layer builder (not built, my ETA 2026-11-20 12:00Z) and the exit engine families (builder not started); so the earliest "through everything" date for L01811caa and L6a25b155 (they stay first) is 2026-11-21 ~12:00Z, later if the exit engine builder starts late. L0f097450 (= L3701b464, same stream) is judged by the same ADD/REPLACE rule.

## STRICT criterion table (Asia / D8 rule: stack ulcer LOWER, mean $/wk NOT LOWER, worst week NOT WORSE, max DD NOT WORSE; L6M with L3M beside; REPLACE-K7 vs TODAY stack; engine base lots, $4.84)
| cell | window | metric | today | REPLACE-K7 | change | pass |
|---|---|---|---|---|---|---|
| L01811caa | L6M | stack ulcer (lower = better) | +9416 | +9342 | -75 | PASS |
| L01811caa | L6M | max drawdown | -31109 | -29253 | +1857 | PASS |
| L01811caa | L6M | worst week | -15728 | -15108 | +620 | PASS |
| L01811caa | L6M | mean $/wk | +18755 | +20510 | +1755 | PASS |
| L01811caa | L3M | stack ulcer (lower = better) | +11035 | +10587 | -448 | PASS |
| L01811caa | L3M | max drawdown | -31109 | -28995 | +2114 | PASS |
| L01811caa | L3M | worst week | -15728 | -13266 | +2462 | PASS |
| L01811caa | L3M | mean $/wk | +16098 | +18707 | +2609 | PASS |
| L01811caa | both | STRICT VERDICT | | | | **PASS** |
| L6a25b155 | L6M | stack ulcer (lower = better) | +9416 | +9238 | -178 | PASS |
| L6a25b155 | L6M | max drawdown | -31109 | -29945 | +1164 | PASS |
| L6a25b155 | L6M | worst week | -15728 | -16733 | -1005 | **FAIL** |
| L6a25b155 | L6M | mean $/wk | +18755 | +19675 | +919 | PASS |
| L6a25b155 | L3M | stack ulcer (lower = better) | +11035 | +10415 | -620 | PASS |
| L6a25b155 | L3M | max drawdown | -31109 | -29945 | +1164 | PASS |
| L6a25b155 | L3M | worst week | -15728 | -16733 | -1005 | **FAIL** |
| L6a25b155 | L3M | mean $/wk | +16098 | +17400 | +1301 | PASS |
| L6a25b155 | both | STRICT VERDICT | | | | **FAIL** |
| L0f097450 (twin of L21f079b6) | L6M | stack ulcer (lower = better) | +9416 | +9358 | -58 | PASS |
| L0f097450 (twin of L21f079b6) | L6M | max drawdown | -31109 | -29253 | +1857 | PASS |
| L0f097450 (twin of L21f079b6) | L6M | worst week | -15728 | -18848 | -3120 | **FAIL** |
| L0f097450 (twin of L21f079b6) | L6M | mean $/wk | +18755 | +21047 | +2291 | PASS |
| L0f097450 (twin of L21f079b6) | L3M | stack ulcer (lower = better) | +11035 | +10531 | -504 | PASS |
| L0f097450 (twin of L21f079b6) | L3M | max drawdown | -31109 | -28828 | +2281 | PASS |
| L0f097450 (twin of L21f079b6) | L3M | worst week | -15728 | -18848 | -3120 | **FAIL** |
| L0f097450 (twin of L21f079b6) | L3M | mean $/wk | +16098 | +19000 | +2902 | PASS |
| L0f097450 (twin of L21f079b6) | both | STRICT VERDICT | | | | **FAIL** |

## SLOT OPTIONS per candidate (REPLACE of one live NY AM book; engine rows, today stack vs REPLACE; base lots, $4.84; strict = ulcer lower, mean not lower, worst week not worse, max DD not worse)
| cell | replaces | window | ulcer today -> new | mean $/wk today -> new | worst week today -> new | max DD today -> new | strict (u / m / w / dd) | rule B colour 2025 / 2024 / 2023 | pooled persistence | STRICT verdict |
|---|---|---|---|---|---|---|---|---|---|---|
| L01811caa | K7 | L6M | 9416 -> 9342 | +18755 -> +20510 | -15728 -> -15108 | -31109 -> -29253 | PASS / PASS / PASS / PASS | GREEN (-8%) / GREEN (+6%) / AMBER (+24%) | 0.59 (43 mo) |  |
| L01811caa | K7 | L3M | 11035 -> 10587 | +16098 -> +18707 | -15728 -> -13266 | -31109 -> -28995 | PASS / PASS / PASS / PASS |  |  | **PASS** |
| L01811caa | P7 | L6M | 9416 -> 8703 | +18755 -> +19469 | -15728 -> -14519 | -31109 -> -26864 | PASS / PASS / PASS / PASS | GREEN (+1%) / GREEN (+1%) / AMBER (+18%) | 0.66 (43 mo) |  |
| L01811caa | P7 | L3M | 11035 -> 9670 | +16098 -> +16931 | -15728 -> -11074 | -31109 -> -25684 | PASS / PASS / PASS / PASS |  |  | **PASS** |
| L01811caa | M7 | L6M | 9416 -> 8960 | +18755 -> +19318 | -15728 -> -13068 | -31109 -> -28070 | PASS / PASS / PASS / PASS | GREEN (-7%) / GREEN (-2%) / GREEN (-5%) | 0.60 (43 mo) |  |
| L01811caa | M7 | L3M | 11035 -> 10299 | +16098 -> +16604 | -15728 -> -11897 | -31109 -> -28070 | PASS / PASS / PASS / PASS |  |  | **PASS** |
| L01811caa | H7 | L6M | 9416 -> 9194 | +18755 -> +19509 | -15728 -> -15409 | -31109 -> -28439 | PASS / PASS / PASS / PASS | GREEN (-6%) / GREEN (+4%) / GREEN (+5%) | 0.61 (43 mo) |  |
| L01811caa | H7 | L3M | 11035 -> 10445 | +16098 -> +17094 | -15728 -> -11819 | -31109 -> -28439 | PASS / PASS / PASS / PASS |  |  | **PASS** |
| L6a25b155 | K7 | L6M | 9416 -> 9238 | +18755 -> +19675 | -15728 -> -16733 | -31109 -> -29945 | PASS / PASS / **FAIL** / PASS | GREEN (+3%) / GREEN (+10%) / AMBER (+15%) | 0.59 (43 mo) |  |
| L6a25b155 | K7 | L3M | 11035 -> 10415 | +16098 -> +17400 | -15728 -> -16733 | -31109 -> -29945 | PASS / PASS / **FAIL** / PASS |  |  | **FAIL** |
| L6a25b155 | P7 | L6M | 9416 -> 8733 | +18755 -> +18907 | -15728 -> -15244 | -31109 -> -26864 | PASS / PASS / PASS / PASS | GREEN (+12%) / GREEN (+12%) / GREEN (+15%) | 0.61 (43 mo) |  |
| L6a25b155 | P7 | L3M | 11035 -> 9649 | +16098 -> +16522 | -15728 -> -15244 | -31109 -> -26634 | PASS / PASS / PASS / PASS |  |  | **PASS** |
| L6a25b155 | M7 | L6M | 9416 -> 8807 | +18755 -> +18867 | -15728 -> -16068 | -31109 -> -29020 | PASS / PASS / **FAIL** / PASS | n/a (pending) / n/a (pending) / n/a (pending) | 0.46 (6 mo) |  |
| L6a25b155 | M7 | L3M | 11035 -> 10068 | +16098 -> +16183 | -15728 -> -16068 | -31109 -> -29020 | PASS / PASS / **FAIL** / PASS |  |  | **FAIL** |
| L6a25b155 | H7 | L6M | 9416 -> 9056 | +18755 -> +19068 | -15728 -> -15989 | -31109 -> -29389 | PASS / PASS / **FAIL** / PASS | n/a (pending) / n/a (pending) / n/a (pending) | 0.54 (6 mo) |  |
| L6a25b155 | H7 | L3M | 11035 -> 10237 | +16098 -> +16780 | -15728 -> -15989 | -31109 -> -29389 | PASS / PASS / **FAIL** / PASS |  |  | **FAIL** |

## ENGINE RULE B (prior-year gate) for the 4 NY AM K7 beaters (order 1122Z; full table also on NEW_BOOK_BEATS_LIVE_NYAM.md)

**SIGN CONVENTION (explicit).** Rule B columns below are "% WORSE than today s stack" (positive = WORSE, negative = better): ulcer % = (new-ref)/ref; max DD % and worst week % = (ref-new)/|ref|; mean $/wk % = (ref-new)/|ref| (lower mean = positive = worse). The dollar columns elsewhere on this page: "d ulcer negative = better" (lower ulcer), "d worst week +1,631 = the worst week is $1,631 LESS bad than today s stack", "d max DD positive = less deep", "d mean positive = more $/wk". RED > 30% worse, AMBER 15-30%, GREEN otherwise; cell colour = worst of the four metrics; the verdict needs no RED year; a year with no engine rows yet = pending (not fail).

**Rule B = engine (REPLACE / ADD row vs TODAY s stack, same year).** Rule A (screen: bare stream, prior-year weekly R > 30% worse than the cell s own L6M) only orders the queue and is shown in its own column from the shortlist.

| cell | variant | year | ulcer % worse | max DD % worse | worst wk % worse | mean $/wk % worse | colour | persistence (2-wk windows new stack not worse) | rule A (screen, queue order only) |
|---|---|---|---|---|---|---|---|---|---|
| L01811caa | both sides REPLACE K7 | 2023 | -21% | +11% | +24% | -25% | AMBER | 0.47 | see shortlist |
| L01811caa | both sides REPLACE K7 | 2024 | -14% | -4% | +6% | -14% | GREEN | 0.65 | see shortlist |
| L01811caa | both sides REPLACE K7 | 2025 | -12% | -9% | -11% | -8% | GREEN | 0.58 | see shortlist |
| L01811caa | both sides ADD | 2023 | -15% | -2% | +7% | -64% | GREEN | 0.58 | see shortlist |
| L01811caa | both sides ADD | 2024 | -12% | -1% | +3% | -12% | GREEN | 0.65 | see shortlist |
| L01811caa | both sides ADD | 2025 | -17% | -14% | -2% | -17% | GREEN | 0.77 | see shortlist |
| L01811caa | long-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 (twin of L21f079b6) | both sides REPLACE K7 | 2023 | -9% | +10% | +44% | +7% | RED | 0.58 | see shortlist |
| L0f097450 (twin of L21f079b6) | both sides REPLACE K7 | 2024 | -7% | -12% | +2% | -15% | GREEN | 0.62 | see shortlist |
| L0f097450 (twin of L21f079b6) | both sides REPLACE K7 | 2025 | -17% | -15% | -16% | +2% | GREEN | 0.62 | see shortlist |
| L0f097450 (twin of L21f079b6) | both sides ADD | 2023 | -12% | +12% | +13% | -30% | GREEN | 0.53 | see shortlist |
| L0f097450 (twin of L21f079b6) | both sides ADD | 2024 | -3% | -8% | -6% | -16% | GREEN | 0.54 | see shortlist |
| L0f097450 (twin of L21f079b6) | both sides ADD | 2025 | -22% | -17% | -11% | -11% | GREEN | 0.69 | see shortlist |
| L0f097450 (twin of L21f079b6) | long-only REPLACE K7 | 2023 | -14% | +3% | +29% | +1% | AMBER | 0.63 | see shortlist |
| L0f097450 (twin of L21f079b6) | long-only REPLACE K7 | 2024 | -8% | -2% | -3% | -17% | GREEN | 0.58 | see shortlist |
| L0f097450 (twin of L21f079b6) | long-only REPLACE K7 | 2025 | +11% | +12% | +17% | +10% | AMBER | 0.50 | see shortlist |
| L0f097450 (twin of L21f079b6) | long-only ADD | 2023 | -19% | -14% | +5% | -35% | GREEN | 0.68 | see shortlist |
| L0f097450 (twin of L21f079b6) | long-only ADD | 2024 | -6% | +3% | -6% | -17% | GREEN | 0.73 | see shortlist |
| L0f097450 (twin of L21f079b6) | long-only ADD | 2025 | +5% | +12% | +25% | -1% | AMBER | 0.62 | see shortlist |
| L0f097450 | short-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 (twin of L21f079b6) | both sides REPLACE K7 | 2023 | -9% | +10% | +44% | +7% | RED | 0.58 | see shortlist |
| L3701b464 (twin of L21f079b6) | both sides REPLACE K7 | 2024 | -7% | -12% | +2% | -15% | GREEN | 0.62 | see shortlist |
| L3701b464 (twin of L21f079b6) | both sides REPLACE K7 | 2025 | -17% | -15% | -16% | +2% | GREEN | 0.62 | see shortlist |
| L3701b464 | both sides ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | both sides ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | both sides ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 (twin of L21f079b6) | long-only REPLACE K7 | 2023 | -14% | +3% | +29% | +1% | AMBER | 0.63 | see shortlist |
| L3701b464 (twin of L21f079b6) | long-only REPLACE K7 | 2024 | -8% | -2% | -3% | -17% | GREEN | 0.58 | see shortlist |
| L3701b464 (twin of L21f079b6) | long-only REPLACE K7 | 2025 | +11% | +12% | +17% | +10% | AMBER | 0.50 | see shortlist |
| L3701b464 (twin of L21f079b6) | long-only ADD | 2023 | -19% | -14% | +5% | -35% | GREEN | 0.68 | see shortlist |
| L3701b464 (twin of L21f079b6) | long-only ADD | 2024 | -6% | +3% | -6% | -17% | GREEN | 0.73 | see shortlist |
| L3701b464 (twin of L21f079b6) | long-only ADD | 2025 | +5% | +12% | +25% | -1% | AMBER | 0.62 | see shortlist |
| L3701b464 | short-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | both sides REPLACE K7 | 2023 | -4% | +15% | +5% | -34% | AMBER | 0.58 | see shortlist |
| L6a25b155 | both sides REPLACE K7 | 2024 | +10% | -3% | -3% | -17% | GREEN | 0.58 | see shortlist |
| L6a25b155 | both sides REPLACE K7 | 2025 | +3% | +3% | +0% | -7% | GREEN | 0.58 | see shortlist |
| L6a25b155 | both sides ADD | 2023 | -18% | +3% | -8% | -72% | GREEN | 0.79 | see shortlist |
| L6a25b155 | both sides ADD | 2024 | +12% | -0% | -6% | -20% | GREEN | 0.54 | see shortlist |
| L6a25b155 | both sides ADD | 2025 | -6% | +0% | +12% | -20% | GREEN | 0.65 | see shortlist |
| L6a25b155 | long-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |

**Rule B verdict per row:**
- L01811caa both sides REPLACE K7: no RED year
- L01811caa both sides ADD: no RED year
- L01811caa long-only REPLACE K7: pending (no prior-year rows yet)
- L01811caa long-only ADD: pending (no prior-year rows yet)
- L01811caa short-only REPLACE K7: pending (no prior-year rows yet)
- L01811caa short-only ADD: pending (no prior-year rows yet)
- L0f097450 both sides REPLACE K7: RED year
- L0f097450 both sides ADD: no RED year
- L0f097450 long-only REPLACE K7: no RED year
- L0f097450 long-only ADD: no RED year
- L0f097450 short-only REPLACE K7: pending (no prior-year rows yet)
- L0f097450 short-only ADD: pending (no prior-year rows yet)
- L3701b464 both sides REPLACE K7: RED year
- L3701b464 both sides ADD: pending (no prior-year rows yet)
- L3701b464 long-only REPLACE K7: no RED year
- L3701b464 long-only ADD: no RED year
- L3701b464 short-only REPLACE K7: pending (no prior-year rows yet)
- L3701b464 short-only ADD: pending (no prior-year rows yet)
- L6a25b155 both sides REPLACE K7: no RED year
- L6a25b155 both sides ADD: no RED year
- L6a25b155 long-only REPLACE K7: pending (no prior-year rows yet)
- L6a25b155 long-only ADD: pending (no prior-year rows yet)
- L6a25b155 short-only REPLACE K7: pending (no prior-year rows yet)
- L6a25b155 short-only ADD: pending (no prior-year rows yet)

## NY AM ONE DATE LINE (order 1750Z, restated 1900Z: 4,557-cell ladder, other-book rows parked, id-duplicate first-look lines parked: first looks + ranked follow-ups)

**NY AM STAGE 1 ONE DATE LINE (simulated mix with handoff of empty streams, fleet 13272 /h measured / 5076 /h lead / 4000 low): NY AM first looks end 2026-11-20 02:24Z; NY AM stream incl. other-book REPLACE rows ends **2026-11-20 02:24Z** (low case 2026-11-20 06:48Z); follow-ups of strict passers end 2026-11-20 01:48Z (exit rows also wait for the unbuilt exit families ~21:00Z); FLEET-WIDE stage 1 (Asia + NY AM) ends **2026-11-20 02:30Z** (2 h); combination stage: W-COMBO; LONG POLE: NY AM stream: the other-book REPLACE rows (0 set-months after the first looks).**

| part (NY AM) | set-months left | measured last 60 min |
|---|---|---|
| first looks: stage A REPLACE-K7 lines (ladder = 4557 DISTINCT cells, all built; 2150 first-looked; the 2588 old-seed-only ids are duplicate ids of built cells; duplicate-side lines of identical-stream pairs parked) | 16193 | 1616 /h |
| other-book REPLACE rows P7/M7/H7 (0 queued + ~0 to be appended as first looks finish: 2699 cells x 52% non-negative x 18) | 0 | 0 /h |
| stage B/C of the strict passers (prior years 37 + controls 526 left for the 8 strict sets in 5 cells) | 563 | 619 /h |
| layers (0 queued, W-LAYERS + 1388 to be created for the 4 new passer cells) | 1388 | 0 /h |
| exit pairs (56 queued) + exit rows for the 5 passer cells (309 each, families unbuilt until builders W-XB1/XB2 ~21:00Z) | 1601 | 1 /h |
| follow-ups of FUTURE strict passers (about 6 more cells x 873 set-months each, at the measured passer rate 5 of 2150) | 5479 | 0 /h |

Other streams in the mix: Asia first looks 39, follow-ups total 9046 (NY AM 9031 + Asia 15).

| fleet rate | Asia first looks end | NY AM first looks end | NY AM stream (first looks + other-book rows) ends | follow-ups end | **ALL (stage 1)** |
|---|---|---|---|---|---|
| 5076 /h | 2026-11-20 00:30Z | 2026-11-20 05:30Z | 2026-11-20 05:30Z | 2026-11-20 04:00Z | **2026-11-20 05:36Z** (5 h) |
| 13272 /h | 2026-11-20 00:30Z | 2026-11-20 02:24Z | 2026-11-20 02:24Z | 2026-11-20 01:48Z | **2026-11-20 02:30Z** (2 h) |
| 4000 /h | 2026-11-20 00:30Z | 2026-11-20 06:48Z | 2026-11-20 06:48Z | 2026-11-20 04:54Z | **2026-11-20 06:54Z** (6 h) |

OWN-MERIT FOLLOW-UPS (order 1806Z: ranked, no cap): follow-ups for the top-N ranked cells per session = N x 873 set-months (prior years 37 + 30 controls 180 + layers 347 + exit rows 309); fleet 13272 /h; the stage-1 date depends on N:

| N cells per session (NY AM and Asia each) | extra follow-up set-months | ALL stage 1 ends | hours |
|---|---|---|---|
| 50 | 87300 | 2026-11-20 09:06Z | 9 |
| 100 | 174600 | 2026-11-20 15:42Z | 15 |
| 200 | 349200 | 2026-11-21 04:48Z | 28 |
| 500 | 873000 | 2026-11-22 20:18Z | 68 |

Assumptions: weights Asia first looks 41.3%% / NY AM stream 28.7%% / follow-ups 30%% with the share of an EMPTY stream handed to the others (ny_mix3.py); the other-book rows are modelled as available from the start (they are appended as first looks complete, so this is the optimistic end); strict-passer follow-ups as in the part table (8 sets in 5 cells + extrapolated future passers). The mix is applied on the dispatchers (the lead measures it).
