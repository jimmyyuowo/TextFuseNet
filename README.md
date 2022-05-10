# TextFuseNet: Scene Text Detection with Richer Fused Features 

# Installation
This implementation is based on [Detectron2](https://github.com/facebookresearch/detectron2), the installation can refer to [step-by-step installation.txt](https://github.com/jimmyyuowo/TextFuseNet/blob/master/step-by-step%20installation.txt). For more details about the environment of conda, please refer to [requirements.txt](https://github.com/jimmyyuowo/TextFuseNet/blob/master/requirements.txt).

# Run demo
Download Models: [Google Driver](https://drive.google.com/drive/folders/18Ll-3bAmi4CR2eGTuM-j6fkMrSAaBV4Z?usp=sharing).
Set the path of files (include model, testing images, configs, output etc.) in demo/***_detection.py.  Then launch demo by:
    
    python demo/icdar2013_detection.py

# Evaluation
Our detection code will save text contours to a txt file for each image. For calculating F-measure, Recall, and Precision, please refer to the following links:  
[ICDAR2013](https://rrc.cvc.uab.es/?ch=2)  
[ICDAR2015](https://rrc.cvc.uab.es/?ch=4)  
[Total-Text](https://github.com/cs-chan/Total-Text-Dataset)  
[CTW-1500](https://github.com/Yuliang-Liu/Curve-Text-Detector)  
[ICDAR2019-ArT](https://rrc.cvc.uab.es/?ch=14)

# Train a new model
Before training，please register your datasets in detectron2/data/datasets/builtin.py. Set training implementation details in configs/ocr/***.yaml.  To train a model with 4 gpus，please run:

    python tools/train_net.py --num-gpus 4 --config-file configs/ocr/icdar2013_101_FPN.yaml

# Annotation example
The annotation example can be found in [annotation_example](https://github.com/jimmyyuowo/TextFuseNet/tree/master/annotation_example).
For word-level labels and character-level labels, please see corresponding details of weakly supervised learning method in our paper. 
For semantic segmentation labels, we generate it according to the masks of text instances during training, and for more details, please see corresponding code in [seg_head.py](https://github.com/jimmyyuowo/TextFuseNet/blob/master/detectron2/modeling/roi_heads/seg_head.py).

# Results
Example results of TextFuseNet on different datasets.

input:
![image](https://github.com/jimmyyuowo/TextFuseNet/blob/main/input_images/img_o_nccuunit.jpg)

output:
image:
![image](https://github.com/jimmyyuowo/TextFuseNet/blob/main/test_totaltext/img_o_nccuunit.jpg)

txt:
![txt](https://github.com/jimmyyuowo/TextFuseNet/blob/main/test_totaltext/res_img_o_nccuunit.txt)


Evaluation of TextFuseNet on different datasets with ResNet-101/ResNeXt-101 backbone:
|Datasets|Model|Recall|Precision|F-measure|
|:------:|:------:|:------:|:------:|:------:|
|totaltext|Paper (ResNet-101)|85.3|89.0|87.1|
|totaltext|This implementation (ResNeXt-101)|__85.8__|__89.2__|__87.5__|
|ctw1500|Paper (ResNet-101)|85.4|87.8|86.6|
|ctw1500|This implementation (ResNeXt-101)|85.1|__89.7__|__87.4__|
|icdar2013|Paper (ResNet-101)|92.3|96.5|94.3|
|icdar2013|This implementation (ResNeXt-101)|92.1|__97.2__|__94.6__|
|icdar2015|Paper (ResNet-101)|89.7|94.7|92.1|
|icdar2015|This implementation (ResNeXt-101)|__90.6__|94.0|__92.2__|
|icdar2019-ArT|This implementation (ResNeXt-101)|72.8|85.4|78.6|

Evaluation of TextFuseNet on different datasets with ResNet-50 backbone:
|Datasets|Model|Recall|Precision|F-measure|
|:------:|:------:|:------:|:------:|:------:|
|totaltext|Paper|83.2|87.5|85.3|
|ctw1500|Paper|85.0|85.8|85.4|
|icdar2013|Paper|89.5|95.1|92.2|
|icdar2015|Paper|88.9|91.3|90.1|

