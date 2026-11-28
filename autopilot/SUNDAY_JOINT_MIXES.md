# SUNDAY JOINT MIXES (W-SUNDAY-MX) 28 Nov 10:52Z

## Answer

- NY AM (42 months): lowest max DD = drift at 1 lot / reference (no treatment) (-$185,152 vs live -$200,647), income $2,779,825 vs live $3,498,291; best income = live / reference (no treatment) ($3,498,291, DD -$200,647).
- Asia (42 months): lowest max DD = drift removed / reference (no treatment) (-$66,365 vs live -$67,941), income $909,638 vs live $914,998; best income = replacement book / reference (no treatment) ($1,044,530, DD -$66,418).
- NY PM (37 months): lowest max DD = drift removed / reference (no treatment) (-$55,701 vs live -$134,363), income $882,039 vs live $1,047,175; best income = replacement book / reference (no treatment) ($1,050,341, DD -$73,880).
- London (42 months): lowest max DD = drift removed / reference (no treatment) (-$137,970 vs live -$224,333), income $711,979 vs live $913,621; best income = live / reference (no treatment) ($913,621, DD -$224,333).

Exact engine, p484. Treatments: NY AM node = NY-NODE (MF4) g67a70 no target; Asia vwap = AS-VWAPBRK (MF3) tr100 no target (trail 1.0 x S0 armed at best >= 50% of old target); NY PM zn = NP-ZN xi15all, conf = NP-CONF (MF5, added book as in the CONF set) xi10tight; late50 = half lots on entries whose planned hold is under the p50 of past winners holds; London late50/late75 on the live mix. Bases: live / drift books removed / drift books at 1 lot / replacement (Asia Ma1 in place of MF4; NY PM Z1 in place of MF1, flagged: the REPL2 page supports only Asia Ma1). Layer dollar caps NOT re-fitted. London drift-removed = the mix without MF2.

## NY AM (42 months, 2023-04 to 2026-10; Nov 2025 excluded)
| base | treatment | income | max DD | worst week | weekly st.dev | L3M inc | L3M DD | L6M inc | L6M DD | NQ-down wks income | NQ-down worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|
| live | reference (no treatment) | $3,498,291 | -$200,647 | -$110,130 | $49,934 | $506,856 | -$54,493 | $1,463,415 | -$69,974 | $1,348,100 | -$110,130 |
| drift removed | reference (no treatment) | $2,234,172 | -$217,943 | -$92,427 | $41,861 | $339,389 | -$56,176 | $990,095 | -$79,159 | $1,238,417 | -$88,432 |
| drift at 1 lot | reference (no treatment) | $2,779,825 | -$185,152 | -$94,476 | $43,543 | $418,681 | -$50,546 | $1,186,230 | -$65,993 | $1,319,979 | -$94,476 |
| live | node | pending |||||||||
| live | late50 | pending |||||||||
| live | nodelate50 | pending |||||||||
| drift removed | node | pending |||||||||
| drift removed | late50 | pending |||||||||
| drift removed | nodelate50 | pending |||||||||
| drift at 1 lot | node | pending |||||||||
| drift at 1 lot | late50 | pending |||||||||
| drift at 1 lot | nodelate50 | pending |||||||||

## Asia (42 months, 2023-04 to 2026-10; Nov 2025 excluded)
| base | treatment | income | max DD | worst week | weekly st.dev | L3M inc | L3M DD | L6M inc | L6M DD | NQ-down wks income | NQ-down worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|
| live | reference (no treatment) | $914,998 | -$67,941 | -$37,409 | $17,867 | $154,302 | -$36,934 | $462,565 | -$36,934 | $378,957 | -$37,409 |
| drift removed | reference (no treatment) | $909,638 | -$66,365 | -$35,545 | $17,072 | $141,925 | -$34,250 | $458,635 | -$34,250 | $355,436 | -$35,545 |
| drift at 1 lot | reference (no treatment) | $908,189 | -$66,943 | -$35,476 | $17,250 | $145,805 | -$34,615 | $459,319 | -$34,615 | $360,891 | -$35,476 |
| live | vwap | pending |||||||||
| live | late50 | pending |||||||||
| live | vwaplate50 | pending |||||||||
| drift removed | vwap | pending |||||||||
| drift removed | late50 | pending |||||||||
| drift removed | vwaplate50 | pending |||||||||
| drift at 1 lot | vwap | pending |||||||||
| drift at 1 lot | late50 | pending |||||||||
| drift at 1 lot | vwaplate50 | pending |||||||||
| replacement book | vwap | pending |||||||||
| replacement book | vwaplate50 | pending |||||||||
| replacement book | reference (no treatment) | $1,044,530 | -$66,418 | -$36,185 | $17,850 | $175,276 | -$29,282 | $519,179 | -$29,282 | $404,397 | -$36,185 |

## NY PM (37 months, 2023-09 to 2026-10; Nov 2025 excluded)
| base | treatment | income | max DD | worst week | weekly st.dev | L3M inc | L3M DD | L6M inc | L6M DD | NQ-down wks income | NQ-down worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|
| live | reference (no treatment) | $1,047,175 | -$134,363 | -$44,139 | $16,915 | $199,258 | -$20,350 | $386,078 | -$30,613 | $486,530 | -$35,057 |
| drift removed | reference (no treatment) | $882,039 | -$55,701 | -$32,018 | $12,119 | $135,645 | -$11,840 | $242,779 | -$33,802 | $435,781 | -$18,793 |
| drift at 1 lot | reference (no treatment) | $710,863 | -$59,887 | -$27,216 | $11,587 | $142,406 | -$9,553 | $242,215 | -$18,032 | $322,214 | -$15,625 |
| live | zn | pending |||||||||
| live | znconf | pending |||||||||
| live | late50 | pending |||||||||
| live | znconflate50 | pending |||||||||
| drift removed | zn | pending |||||||||
| drift removed | znconf | pending |||||||||
| drift removed | late50 | pending |||||||||
| drift removed | znconflate50 | pending |||||||||
| drift at 1 lot | zn | pending |||||||||
| drift at 1 lot | znconf | pending |||||||||
| drift at 1 lot | late50 | pending |||||||||
| drift at 1 lot | znconflate50 | pending |||||||||
| replacement book | znconf | pending |||||||||
| replacement book | znconflate50 | pending |||||||||
| replacement book | reference (no treatment) | $1,050,341 | -$73,880 | -$27,163 | $12,783 | $123,310 | -$19,162 | $288,148 | -$24,714 | $554,715 | -$19,437 |

## London (42 months, 2023-04 to 2026-10; Nov 2025 excluded)
| base | treatment | income | max DD | worst week | weekly st.dev | L3M inc | L3M DD | L6M inc | L6M DD | NQ-down wks income | NQ-down worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|
| live | reference (no treatment) | $913,621 | -$224,333 | -$107,350 | $22,877 | $234,166 | -$39,760 | $528,187 | -$39,760 | $6,885 | -$107,350 |
| drift removed | reference (no treatment) | $711,979 | -$137,970 | -$57,078 | $17,501 | $182,567 | -$40,586 | $400,932 | -$40,586 | $324,485 | -$53,813 |
| drift at 1 lot | reference (no treatment) | $796,513 | -$148,226 | -$65,207 | $18,195 | $200,096 | -$38,610 | $439,157 | -$38,610 | $259,385 | -$65,207 |
| live | late50 | pending |||||||||
| live | late75 | pending |||||||||
| drift removed | late50 | pending |||||||||
| drift removed | late75 | pending |||||||||
| drift at 1 lot | late50 | pending |||||||||
| drift at 1 lot | late75 | pending |||||||||

