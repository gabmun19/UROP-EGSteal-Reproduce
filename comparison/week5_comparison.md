# Week 5 Reproduction: Side-by-Side Comparison

This document compares my reproduced Week 5 results with the target model results reported by the original authors.

---

## Experiment: Week 5 — Target vs. Surrogate

### **1. Metrics Comparison**

| Metric | Target Model (Paper Result) | My Surrogate Reproduction |
|--------|------------------------------|----------------------------|
| **Test Accuracy** | 0.7506 | 0.7019 |
| **Test AUC** | 0.8147 | 0.7642 |
| **Prediction Fidelity** | — | 0.8053 |
| **Order Accuracy** | — | 0.6305 |
| **Explanation Rank Correlation** | — | 0.2424 |

---

## Notes

- The target model metrics come from `week5_target_results.pt`.
- The surrogate model metrics come from `week5_surrogate_results.pt`.
- The paper reports target metrics but does not provide fidelity or explanation metrics directly; these are measured only for the surrogate model.

---

## Files Referenced
- `week5_target_results.pt`
- `week5_surrogate_results.pt`

