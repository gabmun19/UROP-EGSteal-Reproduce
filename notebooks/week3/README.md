# Week 3 - Data fix & Environment Setup

### Overview
This week was focused on environment debugging, since the original EGSteal pipeline could not run in Colab due to repeated version conflicts with PyTorch, PyG, NumPy, and the TU dataset loader.  

Rather than losing a full week blocked on dependency issues, I created a simulated mini-pipeline so I could:  
- Reproduce the folder structure EGSteal expects
- Test the downstream training scripts
- Generate placeholder .pt files and JSON result summaries
- Verify that model training, saving, and result logging all work end-to-end  

This let me validate the workflow logic before moving on to Weeks 4 and 5, where I run the real experiments. 

## Issues / What I Attempted  
I tried multiple PyTorch / PyG combinations, attempted manual installs, and even tried switching Python versions.
However, the TU dataset loader (TUDataset) consistently failed due to:
- PyTorch-Geometric version mismatches
- NumPy 2.x incompatibility with PyTorch 2.3+
- Colab’s Python version changing unexpectedly
- TU dataset move operation breaking (LocalFileSystem.mv() argument mismatch)  

Because of this, I switched strategies for Week 3.

### Files Included
- week3_dataFix.ipynb: notebook containing all simulated steps
- results_week3.zip: dummy dataset, model weights, and result JSON

### Summary
Week 3 was primarily environment debugging, and to keep momentum, I implemented a mock version of the pipeline. This ensured I understood the structure and execution flow before moving on to full experiments in the following weeks.
