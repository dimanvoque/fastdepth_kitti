# fastdepth_kitti

============================

This repo offers trained models and evaluation code for the [FastDepth](http://fastdepth.mit.edu/) project at MIT trained on the KITTI Odometry dataset.

## Contents
0. [Requirements](#requirements)
0. [Dataset](#dataset)
0. [Training](#training)
0. [Resume from a particular checkpoint](#resume-from-a-particular-checkpoint)
0. [Evaluation](#evaluation)
0. [Inference](#inference)

## Requirements
- Install CUDA 11.7.0
- Programming language: Python 3.7.9
- Install all the requirements **pip install -r requirements.txt**

##Dataset
Download the preprocessed KITTI Odometry dataset in HDF5 format and place it under a `kitti` folder inside the repo directory. The KITTI Odometry dataset requires 82G of storage space.
```bash
	mkdir kitti; cd kitti
	wget http://datasets.lids.mit.edu/sparse-to-dense/data/kitti.tar.gz
	tar -xvf kitti.tar.gz && rm -f kitti.tar.gz
	cd ..
	```
##Training
arch - architecture 
epoch - number of epochs
b - batch size 
data - dataset name
t - train 

To train the MobileNetSkipAdd architecture:
     ```bash
     python main.py -t train --arch MobileNetSkipAdd --epoch 10 -b 8 --data kitti
     ```

##Resume from a particular checkpoint
resume - resume training from a particular checkpoint

To resume from a particular checkpoint use the following command:
```bash
     python main.py --resume results/kitti.samples=0.modality=rgb.arch=MobileNetSkipAdd.decoder=nnconv.criterion=l1.lr=0.01.bs=8.pretrained=True/checkpoint-8.pth.tar
```
     
##Evaluation
evaluation - start the evaluation process 

To evaluate the model use the following command:
      
     ```bash
     python main.py --evaluate results/kitti.samples=0.modality=rgb.arch=MobileNetSkipAdd.decoder=nnconv.criterion=l1.lr=0.01.bs=8.pretrained=True/model_best.pth.tar
     ```

##Inference
model - the name of the trained model

To run the real-time inference use the following command:
     ```bash
     python inference.py 
     ```





