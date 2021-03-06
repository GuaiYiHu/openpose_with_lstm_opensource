# tf-et-assist-opensource
This is an Implement of openpose with lstm module using TensorFlow.

The original openpose project based on caffe is <a href="https://github.com/ZheC/Realtime_Multi-Person_Pose_Estimation">here</a>. 

Only basic python is used, so the code is easy to understand.

The Dataloader and Post-processing code is from [tf-pose-estimation](https://github.com/ildoonet/tf-pose-estimation).

## Content

1. [Set up](#set-up)
2. [Test](#test)

## Set up
### Environment
- Ubuntu 16.04
- Cuda 10.0
- CuDNN 7.6.5
- Anaconda

### Install
Clone the repo and install 3rd-party libraries.

```
$ git clone https://github.com/GuaiYiHu/tf-et-assist-opensource
$ cd tf-et-assist-opensource
$ conda create -n py37 python=3.7
$ conda activate py37
$ pip3 install -r requirements.txt
```

Setup COCO API

```
$ git clone https://github.com/cocodataset/cocoapi.git
$ cd cocoapi/PythonAPI/
$ make
$ python setup.py install
$ cd ../../
```

Build c++ library for post processing.

```
$ sudo apt-get install swig
$ cd pafprocess
$ swig -python -c++ pafprocess.i && python3 setup.py build_ext --inplace
```

Download data.zip and checkpoints.zip from the link below.

BaiduNetDisk: Link: https://pan.baidu.com/s/1G3lJAsM0g_IkhwydRhTheg Password: bn7x

Google Drive: Link: https://drive.google.com/drive/folders/12v_Zw6kGxNDqHsP8hRqBGyFGjNJdgLZT?usp=sharing
## Test

To run test on single  video in "data/" directory, run exp_signal_processing_single.py.
Specify --video to the single video in "data/" directory in exp_signal_processing_single.py.　

+ For example,  run `python exp_signal_processing_single.py --video 'data/1/平举.mp4'`

If the environment is correct, the result of 'data/1/平举.mp4' will be the same as the picture below.
![Result single](pics/result_single.jpg)

To run test on all videos in "data/" directory, run exp_signal_processing.py.
Specify --mode or -m to the folder includes checkpoint files in exp_signal_processing.py.　　
+ To run on calculate mode,  run `python exp_signal_processing.py --mode cal`　
+ To run on data test mode, run `python exp_signal_processing.py --mode test`

If the environment is correct, the result of test mode will be the same as the picture below.
![Result all](pics/result_all.jpg)