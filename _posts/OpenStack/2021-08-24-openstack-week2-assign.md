---
layout: post
title: "[OpenStack] 2주차 과제 : CLI와 친해지기"
date: 2021-08-24
categories: openstack
tags: openstack
comments: true
---

> 먼저 아래의 작업이 진행되기 전에, OpenStack CLI 프로젝트 개발 환경을 만들어줘야 하는 것을 잊지 말기  
> [OpenStack CLI 프로젝트 개발 환경 Setting](https://play.openstack-kr.org/pages/viewpage.action?pageId=12943383)

✻ 아래의 이미지와 같은 에러가 발생한 경우
<img width="1076" alt="week2-1" src="https://user-images.githubusercontent.com/56791347/130483769-02b5d866-8ade-4225-917a-7189564592cd.png">
  
1) openstack 명령어를 사용하기 위해서는 **source openrc [username] [instance name]** 을 stack에 접속 후 실행 해줘야함
명령어를 입력 후, 아래의 이미지처럼 openstack 명령어를 입력하여 실행이 되는지 확인 해보기
<img width="1103" alt="week2-2" src="https://user-images.githubusercontent.com/56791347/130483765-4ed92952-f4b8-4356-9816-ffb44d3e1b6f.png">

2) 사실 위의 링크를 진행하면서 **4)cli 실행 환경 만들기** 의 shell 실행에서 수많은 모듈들을 추가해줘야했다.
모듈을 다운 받을때는 터미널에 아래의 명령어 입력하기  

```bash
pip3 install <module name>
```

-------------------------------------------
### 2주차 과제
#### 1. cirros image로 인스턴스 생성을 cli로 해보기
```bash
    openstack server create --flavor [flavor] --image [image name] --nic net-id=[network-id] [instance name]
    > [flavor] 는 생성하고자 하는 인스턴스의 flavor를 설정해준다.
    > [network-id] 는 *openstack network list* 입력 후 보여지는 private id를 넣어주면 된다.
    > [image name] 에는 **openstack image list** 를 입력하여 보이는 이미지의 이름을 넣어주면 된다.
```
<img width="1068" alt="week2-3" src="https://user-images.githubusercontent.com/56791347/130483763-10fd0ab7-b8cb-456d-ba84-1f0a93073772.png">

생성이 완료되면 아래와 같이 명령어가 실행된다.
<img width="1249" alt="week2-4" src="https://user-images.githubusercontent.com/56791347/130483761-504dc0db-7e8d-4634-b09e-980bf318d6f9.png">


#### 2. ubuntu 이미지를 받고, root password를 설정한 다음 cli로 이미지 등록한 후 인스턴스 생성하고 접속까지 하기
##### 1) ubuntu image 다운로드 받기

```bash
stack@lja-wallaby:~/devstack$ wget https://cloud-images.ubuntu.com/focal/current/focal-server-cloudimg-amd64.img
```

##### 2) root password 변경하기
    - virt-customize 툴을 사용하기 전에, 만약 이를 사용하기 위한 툴이 없다면 다운 받기(생략 가능)

```bash
stack@lja-wallaby:~/devstack$ sudo apt-get install libguestfs-tools
```

- 설치 완료시, 아래 명령어로 root 비밀번호 customize!

```bash
stack@lja-wallaby:~/devstack$ sudo virt-customize -a focal-server-cloudimg-amd64.img --root-password password:secret
```  
<img width="884" alt="week2-5" src="https://user-images.githubusercontent.com/56791347/130483758-2fea9e3b-b5b8-49a9-b40c-9ec9b56150be.png">  

##### 3) ubuntu image 등록하기
    
```bash
stack@lja-wallaby:~/devstack$ openstack image create "ubuntu-image" --file focal-server-cloudimg-amd64.img --disk-format qcow2 --container-format bare --public
```

<img width="1205" alt="week2-6" src="https://user-images.githubusercontent.com/56791347/130483756-13eb61d3-8042-47c1-8669-c7068fd69fbe.png">

> [[참고] OpenStack Image 서비스 검증 과정](https://docs.openstack.org/newton/ko_KR/install-guide-ubuntu/glance-verify.html)

<img width="1084" alt="week2-7" src="https://user-images.githubusercontent.com/56791347/130483755-f4f2fd6b-afe0-4b62-b376-1385dd9b3181.png">

> image 등록이 완료되면 위와 같이 이미지 파일이 등록된 것을 볼 수 있음

##### 4) 인스턴스 생성

```bash
stack@lja-wallaby:~/devstack$ openstack server create --flavor m1.small --image ubuntu-image --nic net-id=94e8d679-d127-41c2-b8e7-9cb587451061 ubuntu-image1
```
<img width="1166" alt="week2-8" src="https://user-images.githubusercontent.com/56791347/130483752-7d7e35ba-3d40-449e-a7e9-ced1435ceaff.png">

생성된 인스턴스를 ```openstack server list``` 명령어를 이용해서 확인해볼 수 있음

<img width="1159" alt="week2-9" src="https://user-images.githubusercontent.com/56791347/130483751-6decab4b-4e95-43ae-bc7e-54fe87e276e3.png">

##### 5) 접속 확인 해보기
공인 ip에 접속하여 인스턴스를 확인하면 아래와 같이 생성된것을 볼 수 있다!
<img width="1232" alt="week2-10" src="https://user-images.githubusercontent.com/56791347/130483746-2fd5efac-b52a-432d-b97a-baac74745cdc.png">

콘솔창에 접속하여 id와 아까 2-2)에서 설정해준 root 비밀번호를 입력해주면 정상적으로 접속 완료
<img width="747" alt="week2-11" src="https://user-images.githubusercontent.com/56791347/130483744-bcf2b432-7440-412f-bcd3-5aae34563811.png">


#### 3. CLI로 floating IP 생성 후 인스턴스에 할당 / 해제 해보기
##### 1) floating ip 생성
    
```bash
stack@lja-wallaby:~/devstack$ openstack floating ip create --project admin --subnet public-subnet public
```
<img width="1105" alt="week2-12" src="https://user-images.githubusercontent.com/56791347/130483740-30da07a0-4a80-45f2-afdc-2cc15e2b0160.png">

##### 2) floating ip를 인스턴스에 할당 해보기
    ```openstack floating ip list``` 를 입력하여 생성된 floating ip 리스트를 확인 후, 할당 해주기
    
```bash
stack@lja-wallaby:~/devstack$ openstack server add floating ip ubuntu-image1 192.168.100.72
```

    할당이 완료되면, 아래와 같이 인스턴스 네트워크 목록에서 floating ip가 할당된 것을 확인할 수 있다.

<img width="1272" alt="week2-13" src="https://user-images.githubusercontent.com/56791347/130483733-c408f5cd-317f-48f7-a5a0-fa630934928f.png">

##### 3) 인스턴스에 할당 한 floating ip를 해제하기
    
```bash
openstack server remove floating ip ubuntu-image1 192.168.100.72
```

    아래와 같이 할당이 해제된 것을 확인해볼 수 있다
<img width="1164" alt="week2-14" src="https://user-images.githubusercontent.com/56791347/130483727-71894131-428c-498e-9ebc-0dce0ff0a953.png">


#### 4. 10.8.0.0/24 네트워크 만들고 public network와 연결하는 과정을 cli로 해보기(optional)
    - optional 부분은 좀 더 공부 후 도전 해 볼 예정