# QuotaGate family framing

Recommended paper architecture:

- **QuotaGate** = uncertainty-control framework
- **QuotaGateV6** = base utility-paced controller
- **OC-Quota** = outcome-calibrated extension
- **Guarded-OC-Quota** = utility-guarded outcome-calibrated extension

Narrative:
1. QuotaGate formulates uncertainty-governed top-K recommendation as finite violation-budget allocation under a population-level target.
2. QuotaGateV6 is the base controller that is strongest on the original proxy-efficiency objective.
3. Separate semantic validation shows that higher uncertainty/risk corresponds to materially worse realized held-out recommendation quality.
4. OC-Quota uses validation-only bad-cost calibration to reduce observed bad-exposure severity.
5. Guarded-OC-Quota strengthens that extension by selecting the calibration strength under explicit utility-preservation guardrails relative to QuotaGateV6.
6. In the unified sequential replay, the calibrated variants preserve target compliance while substantially reducing severity-aware observed bad exposure.
