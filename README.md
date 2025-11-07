<h1 align="center">[AAAI 2026]Strip R-CNN: Large Strip Convolution for Remote Sensing Object Detection</h1>

<div align="center">
<b>
  <a href="https://github.com/YXB-NKU">Xinbin Yuan</a>, 
  <a href="https://scholar.google.com.hk/citations?hl=zh-CN&user=0X71NDYAAAAJ">ZhaoHui Zheng</a>, 
  <a href="https://scholar.google.com.hk/citations?hl=zh-CN&user=vKnUqmMAAAAJ">Yuxuan Li</a>, 
  <a href="">Xialei Liu</a>, 
  <a href="">Li Liu</a>, 
  <a href="">Xiang Li</a>, 
  <a href="">Qibin Hou*</a>, 
  <a href="">Ming-Ming Cheng</a>
</b>


[![arXiv](https://img.shields.io/badge/arXiv-red)](https://arxiv.org/abs/2501.03775)
<a href='https://zhuanlan.zhihu.com/p/17342348259'><img src='https://img.shields.io/badge/Zhihu-blue.svg?logo=zhihu&logoColor=white'></a>
<a href='https://mp.weixin.qq.com/s/T4ABbbuJ-b7-g6QgiT5_3Q'><img src='https://img.icons8.com/?size=100&id=5tk64ASe7tdw&format=png&color=000000' width='24' height='24'></a>

<p>If you find our work helpful, please consider giving us a ⭐!</p>

</div>



[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/strip-r-cnn-large-strip-convolution-for/object-detection-in-aerial-images-on-dota-1)](https://paperswithcode.com/sota/object-detection-in-aerial-images-on-dota-1?p=strip-r-cnn-large-strip-convolution-for)
![image](https://github.com/user-attachments/assets/0afd4bbe-c538-4e28-9158-a2ed79379f41)


![Strip-R-CNN](DotaStatis.png)


Offical implementation of "Strip R-CNN: Large Strip Convolution for Remote Sensing Object Detection"

we also add our config in https://github.com/zcablii/LSKNet and https://github.com/YXB-NKU/Strip-R-CNN. 

If you encounter any issues while using our code, please check the relevant repositories for related issues first. If none exist, feel free to ask me!


## Update[22/2/2025] 
---
## Jittor implementation at [github.com/NK-JittorCV/nk-remote](https://github.com/NK-JittorCV/nk-remote) ##
博客<a href='https://mp.weixin.qq.com/s/T4ABbbuJ-b7-g6QgiT5_3Q'><img src='https://img.icons8.com/?size=100&id=5tk64ASe7tdw&format=png&color=000000' width='24' height='24'></a>
---


## Abstract

While witnessed with rapid development, remote sensing object detection remains challenging for detecting high aspect ratio objects.
This paper shows that large strip convolutions are good feature representation learners for remote sensing object detection and can detect objects of various aspect ratios well.
Based on large strip convolutions, we build a new network architecture called Strip R-CNN, which is simple, efficient, and powerful.
Unlike recent remote sensing object detectors that leverage large-kernel convolutions with square shapes, our Strip R-CNN takes advantage of sequential orthogonal large strip convolutions to capture spatial information.
In addition, we enhance the localization capability of remote-sensing object detectors by decoupling the detection heads and equipping the localization head with strip convolutions to better localize the target objects.
Extensive experiments on several benchmarks, for example DOTA, FAIR1M, HRSC2016, and DIOR, show that our Strip R-CNN can greatly improve previous work.
In particular, our 30M model achieves 82.75\% mAP on DOTA-v1.0, setting a new state-of-the-art record.

## Introduction

This repository is the official implementation of "Strip R-CNN: Large Strip Convolution for Remote Sensing Object Detection" at: [arxiv](https://arxiv.org/abs/2501.03775)

The master branch is built on MMRotate which works with **PyTorch 1.6+**.

StripNet backbone code is placed under mmrotate/models/backbones/, and the train/test configure files are placed under configs/strip_rcnn/ 


## Results and models

Imagenet 300-epoch pre-trained Strip R-CNN-T backbone: [Download](https://drive.google.com/uc?export=download&id=1Le4QoQPMUlFEssq7BFXGmaYfHoMktvju)

Imagenet 300-epoch pre-trained Strip R-CNN-S backbone: [Download](https://drive.google.com/uc?export=download&id=1_c2aXANKHl0cIBb370LNIkCyDmQpA3_o)

Please note that the Exponential Moving Average (EMA) strategy was not utilized during the ImageNet pretraining stage.
DOTA1.0

|                           Model                            |  mAP  | Angle | lr schd | Batch Size |                                   Configs                                    |                                                               Download                                                               |     note     |
| :--------------------------------------------------------: | :---: | :---: | :-----: | :--------: | :--------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------------------------: | :----------: |
| [RTMDet-l](https://arxiv.org/abs/2212.07784) | 81.33 |   -   | 3x-ema  |     8      |                                      -                                       |                                                                  -                                                                   |  Prev. Best  |
|                  Strip R-CNN-T          | 81.40 | le90  |   1x    |    1\*8    |     [strip_rcnn_t_fpn_1x_dota_le90](./configs/strip_rcnn/strip_rcnn_t_fpn_1x_dota_le90.py)     | [model](https://drive.google.com/uc?export=download&id=1Le4QoQPMUlFEssq7BFXGmaYfHoMktvju)  |              |
|                  Strip R-CNN-S          | 82.28 | le90  |   1x    |    1\*8    |     [strip_rcnn_s_fpn_1x_dota_le90](./configs/strip_rcnn/strip_rcnn_s_fpn_1x_dota_le90.py)     | [model](https://drive.google.com/file/d/1gt3vi-Ks0ie4GEYBWWJlIJVSsYmJrvCx/view?usp=drive_link)  |              |
|                  Strip R-CNN-S*          | 82.75 | le90  |   1x    |    1\*8    |     [strip_rcnn_s_fpn_1x_dota_le90](./configs/strip_rcnn/strip_rcnn_s_fpn_1x_dota_le90.py)     | [model](https://drive.google.com/uc?export=download&id=1_c2aXANKHl0cIBb370LNIkCyDmQpA3_o)  |    [MoCAE](https://drive.google.com/file/d/1Y5brQ7cJN_mUHC-lPWYtDkuQgP8vblve/view?usp=drive_link)           |
|                  StripNet-S + Roi_Trans      | 81.72 | le90  |   1x    |    1\*8    |   [strip_rcnn_s_roitrans_fpn_1x_dota](./configs/strip_rcnn/strip_rcnn_s_roitrans_fpn_1x_dota.py)   | [model]()  |                  |

FAIR1M-1.0

|         Model         |  mAP  | Angle | lr schd | Batch Size |                                                    Configs                                                     |                                                                                                                                                                              Download     | note                                                                                                                                                                         |
| :----------------------: | :---: | :---: | :-----: | :------: | :------------------------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :--------: |

| Strip R-CNN-S | 48.26 | le90  |   1x    |    1*8     |            [strip_rcnn_s_fpn_1x_dota_le90](./configs/strip_rcnn/strip_rcnn_s_fpn_1x_dota_le90.py)             |         [model](https://drive.google.com/file/d/1rQI-L6zzTn-Kd8_Z1KweguiBubivZygY/view?usp=drive_link)  | |

HRSC2016 

|                    Model                     | mAP(07) | mAP(12) | Angle | lr schd | Batch Size |                                      Configs                                      |                                                               Download                                                               |    note    |
| :------------------------------------------: | :-----: | :-----: | :---: | :-----: | :--------: | :-------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------------------------: | :--------: |
| [RTMDet-l](https://arxiv.org/abs/2212.07784) |  90.60  |  97.10  | le90  |   3x    |     -      |                                         -                                         |                                                                  -                                                                   | Prev. Best |
|  [ReDet](https://arxiv.org/abs/2103.07733)   |  90.46  |  97.63  | le90  |   3x    |    2\*4    | [redet_re50_refpn_3x_hrsc_le90](./configs/redet/redet_re50_refpn_3x_hrsc_le90.py) |                                                                  -                                                                   | Prev. Best |
|                   Strip R-CNN-S                   |  90.60  |  98.70  | le90  |   3x    |    1\*8    |       [strip_rcnn_s_fpn_3x_hrsc_le90](./configs/strip_rcnn/strip_rcnn_s_fpn_3x_hrsc_le90.py)        | [model](https://drive.google.com/uc?export=download&id=1_c2aXANKHl0cIBb370LNIkCyDmQpA3_o)  |            |

## Installation

MMRotate depends on [PyTorch](https://pytorch.org/), [MMCV](https://github.com/open-mmlab/mmcv) and [MMDetection](https://github.com/open-mmlab/mmdetection).
Below are quick steps for installation.
Please refer to [Install Guide](https://mmrotate.readthedocs.io/en/latest/install.html) for more detailed instruction.

```shell
conda create --name openmmlab python=3.8 -y
conda activate openmmlab
conda install pytorch==1.8.0 torchvision==0.9.0 cudatoolkit=10.2 -c pytorch
pip install -U openmim
mim install mmcv-full
mim install mmdet
git clone https://github.com/YXB-NKU/Strip-R-CNN.git
cd Strip-R-CNN
pip install -v -e .
```

## Get Started

Please see [get_started.md](docs/en/get_started.md) for the basic usage of MMRotate.
We provide [colab tutorial](demo/MMRotate_Tutorial.ipynb), and other tutorials for:

- [learn the basics](docs/en/intro.md)
- [learn the config](docs/en/tutorials/customize_config.md)
- [customize dataset](docs/en/tutorials/customize_dataset.md)
- [customize model](docs/en/tutorials/customize_models.md)
- [useful tools](docs/en/tutorials/useful_tools.md)


## Acknowledgement

MMRotate is an open source project that is contributed by researchers and engineers from various colleges and companies. We appreciate all the contributors who implement their methods or add new features, as well as users who give valuable feedbacks. We wish that the toolbox and benchmark could serve the growing research community by providing a flexible toolkit to reimplement existing methods and develop their own new methods.

## Citation

If you use this toolbox or benchmark in your research, please cite this project.

If you like our work, don't hesitate to reach out! Let's work on it and see how far it would go!
```bibtex
@article{yuan2025strip,
  title={Strip R-CNN: Large Strip Convolution for Remote Sensing Object Detection},
  author={Yuan, Xinbin and Zheng, ZhaoHui and Li, Yuxuan and Liu, Xialei and Liu, Li and Li, Xiang and Hou, Qibin and Cheng, Ming-Ming},
  journal={arXiv preprint arXiv:2501.03775},
  year={2025}
}
```

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=HVision-NKU/Strip-R-CNN&type=Date)](https://star-history.com/#YXB-NKU/Strip-R-CNN&Date)
## License
Licensed under a [Creative Commons Attribution-NonCommercial 4.0 International](https://creativecommons.org/licenses/by-nc/4.0/) for Non-commercial use only.
Any commercial use should get formal permission first.
