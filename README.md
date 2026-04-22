# QuotaGate Reviewer Reproduction Guide

This bundle reproduces the **final exact-inverse EWBE line** used in the paper.

It is designed for a reviewer who wants the **shortest reliable path** to the final results:
- headline operating point at `tau = 0.90`, `K = 10`
- strict-target evaluation at `tau = 0.95`
- synthetic multiplicative width-mismatch family with `s in {0.8, 1.0, 1.2}`
- exact reciprocal repair `c = 1 / s`

---

## 1. Folder layout

Place the notebook and these folders side by side:

```text
reviewer_bundle/
  QuotaGate_reviewer_curated_notebook.ipynb
  tables/
  records/
```

Optional read-only support folders:

```text
reviewer_bundle/
  expected_wbe_exact_inverse_round/
  final_submission_pack_final_gap_closer/
  committee_fix_round/
```

### Required folders
- `tables/`
- `records/`

The final scripts read:
- `cand_sweep_pd.csv` or `cand_sweep.csv` from `tables/`
- cached validation/test record pickles from `records/`

### Optional folders
These are useful only for browsing older supporting evidence already cited in the paper:
- `expected_wbe_exact_inverse_round/`
- `final_submission_pack_final_gap_closer/`
- `committee_fix_round/`

---

## 2. Edit one path only

At the top of the notebook, set the project root once:

```python
PROJECT_ROOT = "/path/to/reviewer_bundle"
```

Then the notebook should derive everything else from that one variable.

The important subpaths are:

```python
TABLES_DIR  = f"{PROJECT_ROOT}/tables"
RECORDS_DIR = f"{PROJECT_ROOT}/records"
```

Do **not** keep the original hardcoded path:
`/ceph/chercheurs/mirzane241/aegisrec_runs/808ac329ce0f`

Replace it everywhere with `PROJECT_ROOT`.

---

## 3. What to run

Run the notebook **top to bottom**.

The curated notebook keeps only the final paper line:
1. preflight checks
2. main EWBE run
3. exact-inverse robustness run
4. output inspection

You do **not** need to run older research-history branches such as:
- early NeuMF / heteroscedastic training
- chance-constraint branches
- OC / hybrid / RAM variants
- boundary-RDU
- transport-only intermediate repair
- Path-B / LightGCN branches

Those are historical and are not part of the final paper line.

---

## 4. Expected outputs

The final run should write a fresh output folder under `PROJECT_ROOT`, containing tables and figures for the final paper line.

### Main-setting outputs
Typical files include:
- `ewbe_inverse_main_summary.csv`
- `ewbe_inverse_main_significance.csv`
- `ewbe_inverse_main_runtime_summary.csv`
- `ewbe_inverse_lambda_sweeps.csv`

### Robustness outputs
Typical files include:
- `ewbe_inverse_robustness_summary.csv`
- `ewbe_inverse_robustness_significance.csv`
- `ewbe_inverse_robustness_tuning_table.csv`
- `ewbe_inverse_nominal_recovery_audit.csv`

### Figures
Typical files include:
- main frontier figure
- lambda frontier figure
- validation diagnostics figure
- exact-inverse repair figure
- nominal-recovery audit figure

---

## 5. What reviewers should verify first

### A. Main setting
Check that `QuotaGate-EWBE`:
- sharply reduces weighted bad exposure relative to `QuotaGate-U`
- remains essentially tied with `WBEThreshold`
- keeps compliance near target

### B. Strict target
Check that at `tau = 0.95`, `QuotaGate-EWBE`:
- substantially reduces WBE relative to `QuotaGate-U`
- remains competitive in proxy gap
- stays in the same sub-millisecond serving regime

### C. Exact-inverse robustness
Check that under the synthetic multiplicative width-mismatch family:
- raw `s = 0.8` underestimates widths and under-complies
- raw `s = 1.2` overestimates widths and becomes over-conservative
- calibrated `c = 1 / s` exactly restores the nominal trajectory

---

## 6. Minimal troubleshooting

If the notebook fails immediately:

### Check 1
Make sure `tables/` contains at least one of:
- `cand_sweep_pd.csv`
- `cand_sweep.csv`

### Check 2
Make sure `records/` contains the cached validation/test `.pkl` files.

### Check 3
Make sure `PROJECT_ROOT` is correct and points to the folder that contains:
- the notebook
- `tables/`
- `records/`

### Check 4
If plots look wrong, verify that:
- the notebook is writing to a fresh local output folder
- you are not mixing stale outputs from an older run

---

## 7. What this notebook reproduces from the paper

The reviewer notebook is intended to reproduce the final manuscript’s core claims:

- `QuotaGate-U` as the paced base controller
- `QuotaGate-EWBE` as the final severity-aware controller
- semantic validation of risk
- exact reciprocal calibration under the synthetic multiplicative width-mismatch model

It is a **reviewer notebook**, not the full research-history notebook.

---

## 8. Recommended reviewer workflow

1. Unzip the bundle.
2. Put `tables/` and `records/` beside the notebook.
3. Edit `PROJECT_ROOT` once.
4. Run all cells in order.
5. Inspect the generated summary CSVs and figures.
6. Optionally open the support folders for older supporting evidence.

---

## 9. Artifact note

For anonymous review, an artifact availability note in the paper should point to an anonymous repository, for example:

`https://anonymous.4open.science/r/QuotaGateRecSys/`

Replace the placeholder with the anonymous review repository before submission.

---

## 10. Contact between notebook and paper

If a table or figure name in the notebook differs slightly from the paper, trust the **content and values**, not the historical naming. The curated notebook is intentionally simplified to match the final paper line rather than the full internal research history.
