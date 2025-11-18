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
- week3_dataFix.ipynb: Colab notebook used for environment setup and data preparation.
- results_week3.zip: zip of dataset/NCI1/processed_splits.

<ins> Commands I ran in Colab </ins>  

**uninstall conflicting packages**  

!pip uninstall -y torch torch-geometric torch-scatter torch-sparse torch-cluster torchvision torchaudio  

**install torch that worked for me in Colab**

!pip install torch==2.2.0 torchvision==0.17.0 torchaudio==2.2.0

**install PyG and required libs (versions that matched torch)**   

!pip install torch-geometric==2.5.3 torch-scatter==2.1.2 torch-sparse==0.6.18 torch-cluster==1.6.3  

**clone repository**  

!git clone https://github.com/beanmah/EGSteal.git  
%cd EGSteal  

**prepare dataset manually (download & unzip)**    

!mkdir -p dataset/NCI1/raw  
!wget -q https://www.chrsmrrs.com/graphkerneldatasets/NCI1.zip -O dataset/NCI1/raw/NCI1.zip  
!unzip -o dataset/NCI1/raw/NCI1.zip -d dataset/NCI1/raw/  

**run data prep**  

!python data_preparation.py --dataset_name NCI1  


<ins> Key outputs </ins>
- dataset/NCI1/processed_splits/ with target_train_dataset.pt, shadow_dataset.pt, etc.
- Save results_week3.zip containing the processed_splits folder (optional).

<ins> Notes / issues </ins>
- I fixed a dataset download / move problem by manually downloading the zip and unzipping into the raw folder.
- I recorded exact package versions used in the notebook.
