# TextFuseNet: Scene Text Detection with Richer Fused Features 

# Installation
This implementation is based on [Detectron2](https://github.com/facebookresearch/detectron2), the installation can refer to [step-by-step installation.txt](https://github.com/jimmyyuowo/TextFuseNet/blob/master/step-by-step%20installation.txt). For more details about the environment of conda, please refer to [requirements.txt](https://github.com/jimmyyuowo/TextFuseNet/blob/master/requirements.txt).

# Run demo
Download Models: [Google Driver](https://drive.google.com/drive/folders/18Ll-3bAmi4CR2eGTuM-j6fkMrSAaBV4Z?usp=sharing).
Set the path of files (include model, testing images, configs, output etc.) in demo/***_detection.py.  Then launch demo by:
    
    python demo/icdar2013_detection.py



# Results
Example results of TextFuseNet on different datasets.

* input:

    ![image](https://github.com/jimmyyuowo/TextFuseNet/blob/main/input_images/img_o_nccuunit.jpg)

* output:

    * image:

        ![image](https://github.com/jimmyyuowo/TextFuseNet/blob/main/test_totaltext/img_o_nccuunit.jpg)

    * [txt](https://github.com/jimmyyuowo/TextFuseNet/blob/main/test_totaltext/res_img_o_nccuunit.txt)


