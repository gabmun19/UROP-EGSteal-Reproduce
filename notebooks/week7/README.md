## Reproduced Results (Week 7)

We evaluated the explanation-guided surrogate attack on three benchmark graph datasets: **NCI109, AIDS, and Mutagenicity**. For each dataset, we trained a target GNN and then trained a surrogate model using explanation alignment.

### Key Observations
- On **AIDS**, the surrogate achieved a very high **AUC of 0.9073**, closely matching the target (**0.9574**).
- On **NCI109**, the surrogate preserved moderate fidelity (**0.7406**) with reasonable AUC (**0.7529**).
- On **Mutagenicity**, explanation alignment improved surrogate ranking behavior with **rank correlation of 0.3472**.

I have included the notebook file and the resulting zip file of the results.

Complete side-by-side comparisons are provided in the `comparison/` directory.
