# Reviewer checklist coverage

This pack addresses the strict-reviewer asks as follows:

1. Framework + calibrated extension paper:
   Covered by QuotaGate / QuotaGateV6 / OC-Quota / Guarded-OC-Quota framing.

2. Unified drift experiment for calibrated extensions:
   Covered by finalgap_seqreplay_50step.csv, finalgap_seqreplay_summary.csv,
   finalgap_seqreplay_bootstrap.csv, and fig_finalgap_seqreplay.png.

3. Robustness of the new headline metric:
   Covered by finalgap_robustness_table.csv and finalgap_robustness_bootstrap.csv
   across bad_exposure, weighted_bad_exposure, risk_weighted_miss, and
   highrisk_weighted_bad_exposure.

4. Show the calibrated extension is not just over-conservative:
   Covered by compliance_mean, hit_mean, ndcg_mean, and reward_gap_to_oracle_mean
   in finalgap_static_summary.csv.

5. Runtime for the calibrated extensions:
   Covered by finalgap_runtime.csv and fig_finalgap_runtime.png.

6. Cleaner formalism:
   Covered by finalgap_method_formalism.tex and the framework snippets.
