---
title:  "How to setting GPU Driver and Cuda ? "
date:   2022-06-30 16:56:23
categories: [SetupGPU]
tags: [GPUDRIVER]
---




Tensorflow를 돌리기전에 pc에 driver와 cuda를 설치해줘야 한다. 가장 편한건 conda나 docker를 사용해 바로 tensorflow-gpu 를 돌리는 것이지만, 그 경우에도 일단 nvidia-driver는 깔려 있어야한다. 그러므로 우선, ubuntu 18.04 기준으로 driver와 cuda를 설치하는 전 과정을 기술한다. 


# Device Check


## GPU CHECK


``` ruby

update-pciids

``` 
- gpu update

``` ruby

lspci | grep -i nvidia

```

- check gpu about model name

## Driver Check

``` ruby

nvidia-smi

```

- check driver 

``` ruby

apt —installed list | grep nvidia-driver

```



- nvidia-smi가 확인되지 않거나, 그래픽 드라이버에 문제가 없다고 생각되면 위의 명령어로 드라이버가 제대로 설치 되었는지 확인한다.
- 확인 후, 드라이버가 잘못 설치되었음이 확인되면 삭제 후 재 설치 한다.
- 설치된 드라이버가 확인 되지 않으면 재 설치 한다.


## CUDA CHECK

``` ruby

nvcc —version

```



- CUDA VERSION CHECK

``` ruby

ls /usr/local/cuda/lib64

ls /usr/local/cuda/lib64

```

- 직접적으로 확인하고 싶다면, 기본적으로 cuda가 설치되는 위의 폴더에 가서 확인한다.
- 만약 폴더 안에 라이브러리들 (libcudart.{version})이 확인되고,

``` ruby

ls /usr/local

```


- 위의 명령어 출력에 cuda-{version} 폴더가 확인되면 아래와 같이 환경변수를 확인해준다.

``` ruby

vi ~/.bashrc

```

- bashrc 스크립트에 아래와 같이 내용 추가

``` ruby

export PATH=/usr/local/cuda-{version}/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda-{version}/lib64:$LD_LIBRARY_PATH

```

![image](https://user-images.githubusercontent.com/108255754/177236367-153a24e7-c621-4a41-8e1e-713733f27e11.png)


- 위와 같이 맨 아랫줄에 cuda-{version}의 경로를 환경변수에 적용 시켜준다. (마지막줄은 추가하지 않아도 된다.)


``` ruby

source ~/.bashrc

```

- 저장(ESC + : wq!) 후, 위의 명령어로 저장한다.
- 그 다음 nvcc —version으로 cuda를 확인한다.




