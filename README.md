# MVSS-Baseline
This repository provides the baseline code of MVSS task, i.e., MVNet.

## Installation 

The code requires `python>=3.7`, as well as `pytorch>=1.9` and `torchvision>=0.10`. Please follow the instructions [here](https://pytorch.org/get-started/locally/) to install both PyTorch and TorchVision dependencies. Installing both PyTorch and TorchVision with CUDA support is strongly recommended. Then, please clone this repo.

1. **Clone this repo.**

   ```shell
   $ git clone https://github.com/jiwei0921/MVSS-Baseline.git
   $ cd MVSS-Baseline-main/MVNet
   ```

2. **Install dependencies.**

   ```shell
   $ conda create -n MVSS
   $ conda activate MVSS
   $ conda install pytorch torchvision torchaudio cudatoolkit=11.3 -c pytorch
   $ pip install scipy
   $ pip install tqdm
   $ pip install visdom
   $ pip install matplotlib
   ```

## Getting Started

First download the `MVSeg` [dataset](https://jiwei0921.github.io/Multispectral-Video-Semantic-Segmentation/resources/dataset.txt) and pretrained [model ckpt](https://drive.google.com/file/d/1aw2V-krnzVtMEugzd4srXKfUMetzwoeO/view?usp=sharing). Then the model can be used in just a few adaptions to start training:

1. Set your MVSeg dataset path in `datasets/mvss_dataset.py` and put the ckpt in file `save/*`.
2. Perform training from scratch, with ```bash train.sh``` in two stage. First for warm-up, second for MVNet.   
**or** Perform training based on our warm-up ckpt, with ```bash train.sh``` for second stage.

Meanwhile, the segmentation maps can be generated by loading the pretrained model ckpt, with:
1. Set your MVSeg dataset path in `datasets/mvss_dataset.py` and put the ckpt in file `save/*`.
2. Specify testset name in `test.sh`, e.g., `--split-mode test`, or `--split-mode test_night`.
3. Perform inference, with ```bash test.sh```


## Dataset ColorMap
Here is the reference for MVSeg dataset color visualization.

```
[
        (0, 0, 0),          # 0:    background(unlabeled)
        (0, 0, 142),        # 1:    Car
        (0, 60, 100),       # 2:    Bus
        (0, 0, 230),        # 3:    Motorcycle
        (119, 11, 32),      # 4:    Bicycle
        (255, 0, 0),        # 5:    Pedestrian
        (0, 139, 139),      # 6:    Motorcyclist
        (255, 165, 150),    # 7:    Bicyclist
        (192, 64, 0),       # 8:    Cart
        (211, 211, 211),    # 9:    Bench
        (100, 33, 128),     # 10:   Umbrella
        (117, 79, 86),      # 11:   Box
        (153, 153, 153),    # 12:   Pole
        (190, 122, 222),    # 13:   Street_lamp
        (250, 170, 30),     # 14:   Traffic_light
        (220, 220, 0),      # 15:   Traffic_sign
        (222, 142, 35),     # 16:   Car_stop
        (205, 155, 155),    # 17:   Color_cone
        (70, 130, 180),     # 18:   Sky
        (128, 64, 128),     # 19:   Road
        (244, 35, 232),     # 20:   Sidewalk
        (0, 0, 70),         # 21:   Curb
        (107, 142, 35),     # 22:   Vegetation
        (152, 251, 152),    # 23:   Terrain
        (70, 70, 70),       # 24:   Building
        (110, 80, 100)      # 25:   Ground
]
```



## Citation

```
@InProceedings{ji2023mvss,
      title     = {Multispectral Video Semantic Segmentation: A Benchmark Dataset and Baseline},
      author    = {Ji, Wei and Li, Jingjing and Bian, Cheng and Zhou, Zongwei and Zhao, Jiaying and Yuille, Alan L. and Cheng, Li},
      booktitle = {Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},
      month     = {June},
      year      = {2023},
      pages     = {1094-1104}
}
```


## Acknowledgement

This repository was originally built from [LMANet](https://github.com/mattpfr/lmanet). It was modified and extended to support our multispectral video setting.
