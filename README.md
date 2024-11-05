# Automatic brain tumor segmentation in 2D intra-operative ultrasound images using nnU-Net with MRI tumor annotations

The repository contains nessecary files to run inference with some models. 
The models are trained with nnUNet and the repository 



## How to use
To run inference with the models, nnUNetv2 has to

### Clone nnUNet

### Download model-files
The necassary model-files to run inference can be found under Releases. Download the zip-file of the model you want to test and un-zip the folder. Place it inside your nnUNet_results folder whereever you want.

### Modify file_paths
Some file_paths in some files have to be changed in order to make it work:

- inference_information.json
    - modify path for:
        - "postprocessing_file"
        - "some_plans_file"
### Run inference
To run inference, follow the instructions in the inference_instructions.txt-file.
