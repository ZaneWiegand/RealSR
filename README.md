## [Toward Real-World Single Image Super-Resolution (RealSR)](https://csjcai.github.io/papers/RealSR.pdf)


### Dataset:

#### Raw images can be downloaded [HERE](https://drive.google.com/file/d/1Iqx3AbUlLjR_JglsQIq9y9BEcrNLcOCU/view)

#### Captured device: (Canon 5D3 and Nikon D810) +  (24∼105mm, f/4.0 zoom lens) [Dataset](https://drive.google.com/file/d/1ngJERYGcc4cJFX6MDWe6a0HsTxyelchn/view?usp=sharing)
> A part of this dataset was used in the RealSR challenge in [NTIRE 2019 (in conjunction with CVPR 2019)](http://www.vision.ee.ethz.ch/ntire19/).

#### Version 1: 234 scenes (204 scenes for training & 30 scenes for testing), as reported in [the original paper](https://csjcai.github.io/papers/RealSR.pdf) (HR has the same resolution as LR). 
Link: [Google Drive](https://drive.google.com/open?id=1gKnm9BdgyqISCTDAbGbpVitT-QII_unw), [Baidu Drive](https://pan.baidu.com/s/18OrLbVMg3dCGKUlNrN9uWQ) (code: n77c)

#### Version 2: 559 scenes (459 scenes for training & 100 scenes for testing), the extended version (HR has the same resolution as LR). 
Link: [Google Drive](https://drive.google.com/open?id=1dEBRo_1HH6Yk9zrchEg_JTRi-Uhmd-sj), [Baidu Drive](https://pan.baidu.com/s/1MHqJwAyJWlGa519-P5AqQQ) (byyz)

 |Methods    |PSNR|      2      |      3      |      4      |SSIM|      2      |      3      |      4      |  
 |-----------|----|:-----------:|:-----------:|:-----------:|----|:-----------:|:-----------:|:-----------:|
 |KPN(K=5)   |    |    33.41    |    30.47    |    28.80    |    |    0.913    |    0.860    |    0.826    |           
 |KPN(K=7)   |    |    33.42    |    30.49    |    28.84    |    |    0.913    |    0.861    |    0.826    |  
 |KPN(K=13)  |    |    33.44    |    30.52    |    28.92    |    |    0.913    |    0.863    |    0.829    |  
 |KPN(K=19)  |    |    33.45    |    30.57    |    28.99    |    |    0.914    |    0.864    |    0.832    |
 |LP-KPN(K=5)|    |    33.49    |    30.60    |    29.05    |    |    0.917    |    0.865    |    0.834    | 
                        

#### Version 3: 559 scenes (459 scenes for training & 100 scenes for testing), the extended version (HR and LR have different resolution). 
Link: [Google Drive](https://drive.google.com/open?id=17ZMjo-zwFouxnm_aFM6CUHBwgRrLZqIM), [Baidu Drive](https://pan.baidu.com/s/1dn4q-7E2_iJkNXx4MPdVng)(code: 2n93)
> Detail for training & testing: Trained on the RGB domain and tested on Y channel (images from [Version 3](https://drive.google.com/open?id=17ZMjo-zwFouxnm_aFM6CUHBwgRrLZqIM)). 

 |Methods       |PSNR|      2      |      3      |      4      |SSIM|      2      |      3      |      4      |  
 |--------------|----|:-----------:|:-----------:|:-----------:|----|:-----------:|:-----------:|:-----------:|
 |Bicubic       |    |      -      |    28.6284  |   27.2378   |    |      -      |    0.8088   |    0.7643   |
 |Baseline (Our)|    |      -      |    30.6003  |   28.6508   |    |      -      |    0.8630   |    0.8206   |

> Visualization (zooming factor: 4) <br>
> More results can be downloaded [here](https://drive.google.com/open?id=1D6opSY-KmXRLSRgDb5LhTfKcOGkinsYd).

<div align="center">
        <img src="https://github.com/csjcai/RealSR/blob/master/Sample1.png"/>
        <img src="https://github.com/csjcai/RealSR/blob/master/Sample2.png"/>
</div>

### Code:
#### Model: Pretrained Caffe models
1. [Models for PSNR/SSIM](https://github.com/csjcai/RealSR/tree/master/Test/Models)
2. [Models for Visualization](https://github.com/csjcai/RealSR/tree/master/Test/Models4Visualize)

> The above provided models (for quantitative metrics and visual quality) are both trained with the loss ratio in 1:1:1. <br>
> We select different models at different epochs for different purposes.

#### Caffe: training code & testing code
1. Download the new layers in folder ['Layer'](https://github.com/csjcai/RealSR/tree/master/Layer)
2. Modify the caffe.proto (Path: caffe/src/caffe/proto/)
3. Compile Caffe and Matcaffe ([installation](https://caffe.berkeleyvision.org/installation.html))

-- Training --

4. Generate the training data
5. run [*solver.prototxt](https://github.com/csjcai/RealSR/blob/master/Train/LP-KPN_solver.prototxt) to train the network

-- Testing --

6. run [Test.m](https://github.com/csjcai/RealSR/blob/master/Test/Test.m) 



#### Alignment code:
1. Put your own image pairs in the folder and modify the path
2. run [Demo.m](https://github.com/csjcai/RealSR/blob/master/Alignment/Demo.m) in folder ['Alignment'](https://github.com/csjcai/RealSR/tree/master/Alignment)
3. Central region crop

##### Pipeline:<br>
>(1) coarse align the image pairs;<br>
>(2) central crop the image pairs;<br>
>(3) finer align the cropped image pairs;<br>
>(4) discard those misaligned image pairs.


### Citation:
If you find this work useful for your research, please cite:

```
@inproceedings{cai2019toward,
  title={Toward real-world single image super-resolution: A new benchmark and a new model},
  author={Cai, Jianrui and Zeng, Hui and Yong, Hongwei and Cao, Zisheng and Zhang, Lei},
  booktitle={Proceedings of the IEEE International Conference on Computer Vision},
  year={2019}
}
```

```
@inproceedings{cai2019ntire,
  title={Ntire 2019 challenge on real image super-resolution: Methods and results},
  author={Cai, Jianrui and Gu, Shuhang and Timofte, Radu and Zhang, Lei},
  booktitle={Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition Workshops},
  year={2019}
}
```

### Contact:
Please contact me if there is any question (Jianrui CAI: csjcai@comp.polyu.edu.hk).
