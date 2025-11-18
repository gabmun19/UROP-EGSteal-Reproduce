# Week 3 - Data fix & Environment Setup

<ins> Objective </ins>
- Get dataset loaded correctly and fix issues with torch-geometric dataset download.
- Ensure environment compatibility (torch + pyg versions working in Colab).
- Save processed splits to dataset/NCI1/processed_splits.

<ins> Files Included </ins>
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
