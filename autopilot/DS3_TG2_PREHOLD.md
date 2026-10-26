# DS3_TG pre-holdout text (WF-PRE selection only)
Pool: ST, HM, WT, TB1_ST_k15_P60_N, TB7_ORBNY_k3_P60_N, TB9_RENKO_c2_k1_P60_N, TE6_st10m_n10_m3.0, TE6_st10m_n7_m3.0, TE6_st10m_n14_m3.0, TE7_emax5m_f30_s50, TE7_kelt3m_n14_m1.0
Selected by greedy forward risk-parity Sharpe on WF-PRE with corr cap 0.5: TE7_kelt3m_n14_m1.0, TE6_st10m_n7_m3.0, TB7_ORBNY_k3_P60_N
{
 "ST": {
  "src": "DS2 exact per-book locks",
  "pre_sharpe": 1.6709116399257549,
  "corr_ST": 0.9999999999999999,
  "corr_HM": 0.4782449782420684,
  "corr_WT": 0.35296913222068926
 },
 "HM": {
  "src": "DS2 exact per-book locks",
  "pre_sharpe": 1.3622889881403855,
  "corr_ST": 0.4782449782420684,
  "corr_HM": 0.9999999999999999,
  "corr_WT": 0.09604801395258393
 },
 "WT": {
  "src": "DS2 exact per-book locks",
  "pre_sharpe": 0.529468547508278,
  "corr_ST": 0.3529691322206893,
  "corr_HM": 0.09604801395258393,
  "corr_WT": 1.0
 },
 "TB1_ST_k15_P60_N": {
  "src": "exact-lock (D3B)",
  "pre_sharpe": 0.5754883818731849,
  "corr_ST": 0.28594372936138307,
  "corr_HM": 0.18946252463910385,
  "corr_WT": 0.2668855248025307
 },
 "TB7_ORBNY_k3_P60_N": {
  "src": "exact-lock (D3B)",
  "pre_sharpe": 1.12206555687721,
  "corr_ST": 0.16333049200995345,
  "corr_HM": 0.21050209363414035,
  "corr_WT": 0.1229717202587825
 },
 "TB9_RENKO_c2_k1_P60_N": {
  "src": "exact-lock (D3B)",
  "pre_sharpe": 0.9170825767484974,
  "corr_ST": 0.434324984175966,
  "corr_HM": 0.5246454867139341,
  "corr_WT": 0.09700143751055668
 },
 "TE6_st10m_n10_m3.0": {
  "src": "T-ENTRY direct L2 exact-lock (D3E); 1.5x/2x approximated",
  "pre_sharpe": 1.574642453989381,
  "corr_ST": 0.011990691865413306,
  "corr_HM": -0.11335195736768584,
  "corr_WT": 0.21655002128939674
 },
 "TE6_st10m_n7_m3.0": {
  "src": "T-ENTRY direct L2 exact-lock (D3E); 1.5x/2x approximated",
  "pre_sharpe": 1.6923815511655982,
  "corr_ST": 0.09574980621066263,
  "corr_HM": -0.010330676928424104,
  "corr_WT": 0.349030660730168
 },
 "TE6_st10m_n14_m3.0": {
  "src": "T-ENTRY direct L2 exact-lock (D3E); 1.5x/2x approximated",
  "pre_sharpe": 1.3048988214135775,
  "corr_ST": 0.020659584434407654,
  "corr_HM": -0.007548579067688311,
  "corr_WT": 0.23967574110987447
 },
 "TE7_emax5m_f30_s50": {
  "src": "T-ENTRY direct L2 exact-lock (D3E); 1.5x/2x approximated",
  "pre_sharpe": 1.1380207362236727,
  "corr_ST": -0.04250421645722171,
  "corr_HM": 0.23168463168908157,
  "corr_WT": 0.11390563875342584
 },
 "TE7_kelt3m_n14_m1.0": {
  "src": "T-ENTRY direct L2 exact-lock (D3E); 1.5x/2x approximated",
  "pre_sharpe": 2.922945765181727,
  "corr_ST": 0.3295766492302964,
  "corr_HM": 0.2998676095668999,
  "corr_WT": 0.16664103661720076
 },
 "selected": [
  "TE7_kelt3m_n14_m1.0",
  "TE6_st10m_n7_m3.0",
  "TB7_ORBNY_k3_P60_N"
 ],
 "history": [
  [
   "TE7_kelt3m_n14_m1.0",
   2.7803419634384126
  ],
  [
   "TE6_st10m_n7_m3.0",
   3.2462454855096694
  ],
  [
   "TB7_ORBNY_k3_P60_N",
   3.3731707800086466
  ]
 ]
}
