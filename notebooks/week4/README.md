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

### Files Included
- Week4Results.zip
- Week4_training.ipynb
