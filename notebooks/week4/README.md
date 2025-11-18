# Week 4 - Full Real Execution (Target + Surrogate Training)

### Overview
Week 4 was the first week where I successfully ran the real EGSteal pipeline end-to-end on the NCI1 dataset. After resolving all dependency issues in Week 3, I rebuilt the environment and executed:
- Real dataset loading
- Target GNN training (GIN, 3 layers, 128 hidden dim)
- CAM explanation extraction
- Surrogate GNN training with augmentation  

This is the first week where I obtained actual accuracies, AUC scores, and model weights from the real system.

### Issues solved
Several major blockers from earlier weeks were fully resolved:
- NumPy 2.x vs PyTorch incompatibility
  - Downgrading to numpy==1.26.4 fixed the
  - RuntimeError: Numpy is not available crash.

- TUDataset download failing (LocalFileSystem.mv bug)
  - Using a manual download + unzip bypassed the broken auto-downloader.

- Version mismatches with PyTorch-Geometric
  - Pinned compatible versions:
    PyTorch 2.2.0
    PyG 2.4.0
    torch-scatter 2.1.1
    torch-sparse 0.6.18
    torch-cluster 1.6.3  

This allowed CAM and the whole pipeline to run without exception.

### What Was Accomplished
1. Dataset Preparation  
Successfully processed NCI1 into:
  - target_train_dataset.pt
  - target_val_dataset.pt
  - shadow_dataset.pt
  - test_dataset.pt  

2. Target Model Training  
GIN (3 layers, 128 hidden dims) trained for 200 epochs, producing:
  - Target accuracy
  - Target AUC
  - Saved model weights + metrics  

3. Explanation Extraction  
Generated CAM explanations over both:
  - shadow dataset
  - test dataset  

4. Surrogate Model Training  
Trained surrogate GIN using:
  - augmentation_ratio = 0.2
  - operation_ratio = 0.2
  - align_weight = 0.1
  - augmentation_type = combined  

This produced:
  - surrogate model weights
  - surrogate training logs
  - side-by-side relevance scores  

### Files Included
- Week4Results.zip
- Week4_training.ipynb

### Summary
Week 4 marks the first complete, fully functioning run of EGSteal on Colab. After multiple weeks of dependency failures, this week produced the first real experimental results for both the target and surrogate models.  

These outputs set the stage for Week 5, where I implement the real sampling logic and begin comparing surrogate performance to the results in the published paper.
