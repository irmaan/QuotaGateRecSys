# Claim-safe results paragraph

Recommended wording:

QuotaGateV6 remains the strongest controller on the original objective of tight target tracking and near-oracle proxy-utility efficiency under drift. We additionally validate that higher slate uncertainty/risk corresponds to materially worse realized held-out recommendation quality, establishing that the controlled signal has operational meaning. Building on this validation, we introduce outcome-calibrated extensions that keep the same QuotaGate pacing skeleton and compliant-slate solver but replace raw utility-gap prioritization with validation-only bad-cost-aware prioritization. Across all three datasets, the calibrated variants substantially reduce severity-aware observed bad exposure while preserving target compliance and leaving held-out recommendation quality nearly unchanged. The utility-guarded calibrated variant provides the cleanest end-to-end compromise between proxy efficiency and observed failure reduction.

Claims to avoid:
- “QuotaGateV6 alone dominates all observed-outcome metrics.”
- “The uncertainty width is a calibrated probability of user harm.”
- “The calibrated extension universally improves Hit/NDCG.”
- “This proves online causal impact.”
