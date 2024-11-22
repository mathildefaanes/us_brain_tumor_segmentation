# Automatic brain tumor segmentation in 2D intra-operative ultrasound images using MRI tumor annotations

The repository contains necessary files to run inference with the main models from the article: "Automatic brain tumor segmentation in 2D intra-operative ultrasound images using MRI tumor annotations". 
The models are trained with nnUNet and nnUNet is required in order to run inference with this models. 



## How to use
### Clone nnUNet
To run inference with the models, the nnUNetv2-repository has to be cloned. Please follow the installation guide from nnUNet if not yet installed (the option ii.b has to be followed):
https://github.com/MIC-DKFZ/nnUNet/blob/master/documentation/installation_instructions.md

### Add custom trainer
When the nnUNetv2-repository is cloned, a custom trainer has to be added to run inference with the models. This custom trainer was used for training of the models and is identical to the nnUNetTrainerDA5-trainer, but it has early stopping. Download the nnUNetTrainerWithESandDA5.py-file and place it here:

/PATH_TO_/nnUNet/nnunetv2/training/nnUNetTrainer/nnUNetTrainerWithESandDA5.py

### Create necessary folder and set environment variables 
Create the following folders where you want:
- nnUNet_results
- nnUNet_raw
- nnUNet_preprocessed

Set them as enviromantal variabels by:
- export nnUNet_results="/PATH_TO/nnUNet_results"
- export nnUNet_raw="/PATH_TO/nnUNet_raw"
- export nnUNet_preprocessed="/PATH_TO/nnUNet_preprocessed"

or by following the instructions from nnUNet: https://github.com/MIC-DKFZ/nnUNet/blob/master/documentation/setting_up_paths.md

### Download model-files
The necessary model-files to run inference can be found under Releases. Download the zip-file of the model you want to test and un-zip the folder. Place it inside your nnUNet_results folder. The zip-file contains the following files:

    Dataset50X_MODELNAME/
    ├── inference_information.json
    ├── inference_instructions.txt
    ├── postprocessing.json
    ├── postprocessing.pkl
    └── nnUNetTrainerWithESandDA5__nnUNetPlans__2d
    │   ├── dataset.json
    │   ├── plans.json
    │   ├── fold_0
    │   │   └── checkpoint_best.pth
    │   ├── fold_1
    │   │   └── checkpoint_best.pth
    │   ├── fold_2
    │   │   └── checkpoint_best.pth
    │   ├── fold_3
    │   │   └── checkpoint_best.pth
    │   └── fold_4
    │   │   └── checkpoint_best.pth    


### Modify file_paths
Some file_paths have to be changed in order to make it work:

- inference_information.json
    - modify path for:
        - "postprocessing_file"
        - "some_plans_file"

### Run inference
To run inference, follow the instructions in the inference_instructions.txt-file.

### Compute metrics
To compute evaluation metrics, the file compute_metrics.py can be used. Instructions are given in the file. 

## Citing
Please cite the following article:

    @misc{faanes2024automaticbraintumorsegmentation,
          title={Automatic brain tumor segmentation in 2D intra-operative ultrasound images using MRI tumor annotations}, 
          author={Mathilde Faanes and Ragnhild Holden Helland and Ole Solheim and Ingerid Reinertsen},
          year={2024},
          eprint={2411.14017},
          archivePrefix={arXiv},
          primaryClass={eess.IV},
          url={https://arxiv.org/abs/2411.14017}, 
    }

## Acknowledgements
The models are trained using nnU-Net, the repository can be found here:
- https://github.com/MIC-DKFZ/nnUNet/tree/master

Please cite the [following paper](https://www.google.com/url?q=https://www.nature.com/articles/s41592-020-01008-z&sa=D&source=docs&ust=1677235958581755&usg=AOvVaw3dWL0SrITLhCJUBiNIHCQO) when using nnU-Net:

    Isensee, F., Jaeger, P. F., Kohl, S. A., Petersen, J., & Maier-Hein, K. H. (2021). nnU-Net: a self-configuring 
    method for deep learning-based biomedical image segmentation. Nature methods, 18(2), 203-211.

The metrics are computed using seg-metrics, please find it here: https://pypi.org/project/seg-metrics/

Please cite the following paper: 

    @article{jia2024seg,
      title={seg-metrics: a Python package to compute segmentation metrics},
      author={Jia, Jingnan and Staring, Marius and Stoel, Berend C},
      journal={medRxiv},
      pages={2024--02},
      year={2024},
      publisher={Cold Spring Harbor Laboratory Press}
    }
