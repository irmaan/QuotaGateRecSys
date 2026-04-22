Expected-WBE RDU round with exact inverse transport calibration.

Core idea
---------
Keep the same EWBE controller:
    sev = exceed * p_hat

Main setting
------------
Still tuned at width_scale = 1.0.

Exact robustness fix
--------------------
Under the synthetic global multiplicative mismatch family:
    w_eff = width_scale * cal_scale * w

Exact recovery requires:
    width_scale * cal_scale = 1

So this script uses:
    cal_scale = 1 / width_scale

with the nominal controller frozen:
    - lambda*
    - miss model
    - feature scales
    - severity scale

Main outputs
------------
- tables/ewbe_inverse_main_summary.csv
- tables/ewbe_inverse_main_significance.csv
- tables/ewbe_inverse_main_tuning_table.csv
- tables/ewbe_inverse_main_pass_check.csv
- tables/ewbe_inverse_lambda_sweeps.csv
- figs/fig_ewbe_inverse_main_frontier_with_seed_errorbars.png
- figs/fig_ewbe_inverse_lambda_frontier.png
- figs/fig_ewbe_inverse_validation_diagnostics.png

Robustness outputs
------------------
- tables/ewbe_inverse_robustness_summary.csv
- tables/ewbe_inverse_robustness_significance.csv
- tables/ewbe_inverse_robustness_tuning_table.csv
- tables/ewbe_inverse_nominal_recovery_audit.csv
- figs/fig_ewbe_inverse_miscalibration_repair_tau09.png
- figs/fig_ewbe_inverse_nominal_recovery_tau09.png

Detached run from a notebook cell
---------------------------------
!tmux new-session -d -s ewbeinverse \
"bash -lc 'python -u /mnt/data/quota_expected_wbe_exact_inverse_round.py 2>&1 | tee /ceph/chercheurs/mirzane241/aegisrec_runs/808ac329ce0f/expected_wbe_exact_inverse_round.log'"
