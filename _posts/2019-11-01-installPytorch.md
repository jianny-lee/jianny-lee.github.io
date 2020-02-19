---
layout: post
title: "Anaconda 설치 및 Pytorch & TensorFlow 설치"
date: 2019-11-01
categories: dev
tags: machinelearning
comments: true
---

### **2019.11.01 Fri**
### **1. 아나콘다 다운로드 & 설치**
`wget https://repo.anaconda.com/archive/Anaconda3-5.2.0-MacOSX-x86_64.sh`
- wget 명령어를 사용하기 위해선, homebrew를 이용하여 install을 먼저 해줘야함. (`brew install wget`)

`sh Anaconda3-5.2.0-MacOSX-x86_64.sh`
- enter 누르고 location 설정하고 기다리면 설치.
- 설치가 완료되면 새로운 terminal를 실행

### **2. 개발환경 create & activate**
`conda create -n (myDevName) python=3.7 anaconda //파이썬의 버전을 지정해줌`
- **To activate this environment, use :**
    - `source activate (myDevName)`
    - `source activate ~/anaconda3/etc/profile.d/conda.sh`
    *(둘 중 아무거나 사용해도 활성화 가능)*
- **To deactivate an active environment, use :**
    - `source deactivate`
*(여기까지 성공하면, terminal에 "(myDevName) MacBookPro:~ usrname$" 이런식으로 바뀌는데 이렇게 보이면 성공)*
###### 만약 conda 업데이트 하고싶으면 (conda update -n base conda)

### **3 - 1. Pytorch 설치 (활성화한 개발환경 내에서 설치)**
- `conda install pytorch torchvision -c pytorch`

### **3 - 2. TensorFlow 설치 (활성화한 개발환경 내에서 설치)**
- `pip install https://storage.googleapis.com/tensorflow/mac/cpu/tensorflow-1.13.1-py3-none-any.whl`

### **4. Jupyter notebook 접속**
- terminal에 `jupyter notebook` 입력 후 기다리면 됨.
