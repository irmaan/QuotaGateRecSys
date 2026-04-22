Committee-fix round.

What this package is for
------------------------
This package addresses the committee-style reviewer requests:
1. show that risk adds signal beyond utility,
2. add seeds/significance/robustness,
3. export fair tuning logs,
4. report runtime overhead clearly.

Start from these files:
- tables/committee_main_setting_summary.csv
- tables/committee_pairwise_significance.csv
- tables/risk_beyond_utility_cv.csv
- tables/risk_within_utility_bins.csv
- tables/committee_seed_summary.csv
- figs/fig_risk_within_utility_bins.png
- figs/fig_risk_beyond_utility_auc_gain.png
- figs/fig_main_frontier_with_seed_errorbars.png

Notebook detached run:
!tmux new-session -d -s committeefix \
"bash -lc 'python -u /mnt/data/quota_committee_fix_round.py 2>&1 | tee /ceph/chercheurs/mirzane241/aegisrec_runs/808ac329ce0f/committee_fix_round.log'"
