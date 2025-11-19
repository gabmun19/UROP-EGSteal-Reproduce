# Week 4 Reproduction: Side-by-Side Comparison

This document compares my reproduced Week 4 results with the target model results reported by the original authors.

---

## Experiment: Week 4 — Target vs. Surrogate

### **1. Metrics Comparison**

| Metric | Target Model (Paper Result) | My Surrogate Reproduction |
|--------|------------------------------|----------------------------|
| **Test Accuracy** | 0.7506 | 0.7494 |
| **Test AUC** | 0.8147 | 0.8094 |
| **Prediction Fidelity** | — | 0.8674 |
| **Order Accuracy** | — | 0.6660 |
| **Explanation Rank Correlation** | — | 0.3147 |

---

## Notes

- The target model metrics come from `week4_target_results.pt`.
- The surrogate model metrics come from `week4_surrogate_results.pt`.
- The paper reports target metrics but does not provide fidelity or explanation metrics directly; these are measured only for the surrogate model.

---

## Files Referenced
- `week4_target_results.pt`
- `week4_surrogate_results.pt`

