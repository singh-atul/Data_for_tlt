# OBJECT DETECTION PIPELINE 
## Using Transfer Learning Toolkit

### Prerequisite
- Understanding of [Transfer Learning](https://blogs.nvidia.com/blog/2019/02/07/what-is-transfer-learning/)
- Understanding of [NVIDIA Transfer Learning Toolkit](https://docs.nvidia.com/tlt/tlt-user-guide/text/overview.html)
- Understaning of [Kubeflow](https://www.kubeflow.org/docs/started/kubeflow-overview/)

### Why we need this pipeline
This pipeline uses TLT which is a Python package hosted on the NVIDIA Python Package Index. It interacts with lower-level TLT dockers available from the NVIDIA GPU Accelerated Container Registry (NGC); This pipline takes the dataset, specification files and input from the user and generates the pruned and quantized model which can be deployed on the inferencing platform providing an end to end solution

### PIPELINE WORKFLOW
![Solid](https://raw.githubusercontent.com/singh-atul/Data_for_tlt/main/workflow.jpg)

1. User needs to give url to download the input yaml. Details on the creation of input yaml is discussed below
2. Dataset gets downloaded from the  url mentioned in the input yaml and gets stored in the Persistent Volume
3. Download the pretrained model from the [NGC catlog](https://ngc.nvidia.com/)
4. Convert the dataset to tf Records
5. Augment the dataset if specified 
6. Perform the training using the current dataset
7. Perform model Pruning
8. Retraing the model to over come to loss in accuaray at pruning stage 
9. Convert the model into quantized form 
10. Get the output as the Calibration cache and quantized trained model

>Note: The augmentation can be used as a seperate component with individual spec file containg the specific hyperparameters but in the current pipeline user can specify the augmentation details in the training pipeline itself so there wont be any sperate component for augmenting the data.

## Tech



