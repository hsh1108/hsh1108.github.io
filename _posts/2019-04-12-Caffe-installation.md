---
layout: post
title: Caffe installation
---

진행 flow는 다음과 같다
## 1.
본인 우분투 서버 버전은 18.04.2여서 공식사이트의 Installing pre-compiled Caffe를 먼저 시도했다.

```
$ sudo apt install caffe-cuda
```

시도했으나 ModuleNotFoundError: No module named 'caffe'로 실패...

## 2.
한참을 찾다가 모르겠어서 결국  Installing Caffe from source시
Prerequisites 관련해서 먼저 해야할게 많다..

- CUDA 설치
    버전 7이상이여야 한다.
    
    ``
    $ nvcc --version
    ``
    
    로 확인 결과 본인 서버는 버전 10.0으로 설치되어있다.
    pass...

- BLAS 설치
> ``
> $ sudo apt-get install libatlas-base-dev
> ``

- General dependencies(boost, protobuf, glog, glasgs, hdf5)
> 뭐하는 것들인지는 모르겠으나...
>
> ``
> $ sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler
> $ sudo apt-get install --no-install-recommends libboost-all-dev
> ``

- Opencv 설치
> 버전 2.4 이상이여아한다.
>
> ``
> $ pkg-config --modversion opencv
> ``
>
> 로 확인 결과 본인 서버는 버전 3.2.0으로 설치되어있다.
> pass...

- MATLAB interface
> MATLAB interface를 compile 하려면 설치해야하는데 optional이므로 나는 안했다.

## 3.
Compilation

``
$ git clone https://github.com/BVLC/caffe.git
$ cd caffe
``

caffe디렉토리에 있는 Makefile.config를 내 서버의 환경에 맞게 수정해야 한다.

``
$ cp Makefile.config.example Makefile.config
``

https://github.com/BVLC/caffe/pull/1667 를 참조해서 자신의 환경에 맞게 수정하라는데..
내가 주석제거한 부분은 다음과 같다.

``
USE_CUDNN :=1

OPENCV_VERSION := 3

CUDA_DIR
``

---

여기까지 진행하다가 caffe 없이 pytorch로 pretrained된 모델 코드 발견해서 멈춤...
