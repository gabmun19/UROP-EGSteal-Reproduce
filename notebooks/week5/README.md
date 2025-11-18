# Week 5 — Query Sampling + Full Surrogate Training Pipeline

### Overview
Week 5 built directly on the successful full pipeline run from Week 4.
This week, I implemented the complete surrogate attack pipeline using:
- The real query sampling module (sample_query_dataset.py)
- CAM explanations from the trained target model
- Augmented query batches to train the surrogate
- Alignment loss between surrogate outputs and target outputs  

This brings the project much closer to the true reproduction of the EGSteal paper.  

### What Was Accomplished
1. Target Model Re-trained (for consistency)  
I retrained the GIN target model with the same settings as Week 4:
- GIN backbone
- 3 layers
- 128 hidden dim
- 200 epochs  

This produced a stable target performance baseline.  

2. CAM Explanations Computed  
Using target_model_inference.py, I generated:
- queried_dataset_shadow.pt
- queried_dataset_test.pt
- graph-level node importance maps  

These explanations guide the attack model.  

3. Real Query Sampling Implemented
This was the main upgrade for Week 5.  

In Week 4, I temporarily reused the shadow dataset as both train/val due to blocking bugs.  

In Week 5, I replaced that with:
- python sample_query_dataset.py --dataset_name NCI1  


This script:
- takes CAM explanations
- selects informative subgraphs
- constructs a query dataset that mimics attacker queries
- outputs:
  - queried_dataset_train.pt
  - queried_dataset_val.pt  

This matches the methodology in the EGSteal paper.  

4. Surrogate GNN Training (Full Attack)  
The surrogate model now trains on sampled queries (not placeholder data):
- Parameters used:
  - align_weight = 0.1
  - augmentation_ratio = 0.2
  - augmentation type default (drop/add/perturb mix)  

This model attempts to approximate the target GNN’s behavior.

5. Packaged Results  
Week 5 outputs include:
- real target model weights
- real surrogate weights
- sampled query dataset
- results JSON for analysis
- week5_results.zip  

### Files Included
- week5_training.ipynb
- week5_results.zip  

### Summary
Week 5 marks the first complete EGSteal reproduction including the real dataset, target model, CAM explanations, query sampling, and surrogate training.
This brings me close to the experimental setup in the original paper, and prepares me for Week 6, where I can begin side-by-side comparisons between my reproduced surrogate accuracyand the surrogate accuracy reported in the paper.
