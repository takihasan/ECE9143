# ECE9143
Course Name: Advanced Robotic AI 
<br>
Instructor: Prof. Yoonseon Oh <br>
Author: [Taki Hasan Rafi](https://takihasan.github.io/) (Data Intelligence Lab) <br>
Student ID: 2022274322 <br>
## Improved Domain Generalization
This code base in inspired by [SWAD](https://github.com/khanrc/swad/tree/main).
### Environments

Environments that are used in this project.
```
Python: 3.8.6
PyTorch: 1.7.0+cu92
Torchvision: 0.8.1+cu92
CUDA: 9.2
CUDNN: 7603
NumPy: 1.19.4
PIL: 8.0.1
```

### Dependencies
These are the dependencies in this project.
```
prettytable==2.0.0
numpy==1.19.4
torch==1.7.0+cu92
gdown==3.12.2
imageio==2.9.0
sconf==0.2.3
torchvision==0.8.1+cu92
tqdm==4.51.0
tensorboard==2.3.0
Pillow==8.1.0
tensorboardX==2.1
```

To install all the dependencies, run this command in your local machine.
```
pip install -r requirements.txt
```
### Dataset Download
In this project we will use these datasets [PACS](https://www.eecs.qmul.ac.uk/~dl307/project_iccv2017), [Officehome](https://www.hemanthdv.org/officeHomeDataset.html), [TerraInc](https://beerys.github.io/CaltechCameraTraps/), [DomainNet](https://ai.bu.edu/M3SDA/).
To run this project, we do not encourage to train DomainNet dataset. It takes > 12 hours to run in a i9-11세대 + 128GB메모리 + 24 GB RTX3090 GPU. 
<br>
To donwload the datasets all together, run this command.
```
python -m domainbed.scripts.download --data_dir=/my/datasets/path
```

### How to Run
`train_all.py` script conducts multiple leave-one-out cross-validations for all target domain.

```
# PACS
python train_all.py PACS0 --dataset PACS --deterministic \
--trial_seed 0 --checkpoint_freq 300 --steps 5000 --data_dir your_data_dir

# OfficeHome
python train_all.py OH0 --dataset OfficeHome --deterministic \
--trial_seed 0 --steps 3000 --checkpoint_freq 300 --data_dir your_data_dir


# TerraIncognita
python train_all.py TR0 --dataset TerraIncognita --deterministic \
--trial_seed 0 --checkpoint_freq 1000 --steps 5000 --data_dir your_data_dir

