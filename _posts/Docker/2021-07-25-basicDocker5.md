---
layout: post
title: "[Docker] 2.도커 컨테이너 배포 - 도커 컨테이너 다루기(1)"
date: 2021-07-25
categories: docker
tags: docker
comments: true
---
> 책 '도커/쿠버네티스를 활용한 컨테이너 개발 실전 입문'을 기반으로 공부 한 내용을 정리  

* 도커 컨테이너의 생애주기  
        - 실행 중, 정지, 파기의 3가지 상태를 가짐
        - docker container run 명령으로 컨테이너를 최초 실행한 시점의 상태는 '실행 중' 
        - 각 컨테이너는 같은 이미지로 생성했다고 하더라도 별개의 상태를 가짐 --> 상태 갖지않는 도커 이미지와 큰 차이 중 하나
  

    * 실행 중 상태  
        - 도커 이미지 기반으로 컨테이너가 생성되면 이 이미지를 생성했던 Dockerfile에 포함된 CMD 및 ENTRYPOINT 인스트럭션에 정의된 애플리케이션이 실행
        - 실행된 애플리케이션의 상태 == 컨테이너의 실행 중 상태
        - 서버 애플리케이션이면 오류로 인해 종료되지 않는 한, 실행 중 상태가 지속되어 실행 기간이 김
        - 반면, 명령행 도구 등의 컨테이너는 실행 중 상태가 길게 유지 X

	* 정지 상태
		- 실행 중 상태의 컨테이너를 사용자가 docker container stop 명령어로 정지하거나 컨테이너에서 실행된 애플리케이션이 정상/오류 여부를 떠나 종료된 경우, 컨테이너가 자동으로 정지 상태가 됨
		- 컨테이너 정지 시 가상환경으로서는 더 이상 동작 X, 디스크에 컨테이너가 종료되던 시점의 상태가 저장돼 남음 --> 정지시킨 컨테이너를 재가동 가능 의미함
			
	* 파기 상태
		- 명시적으로 파기하지 않는 이상, 정지 상태의 경우 디스크에 그대로 남음 --> 디스크 차지하는 용량이 늘어나므로 불필요한 컨테이너 완전 삭제가 바람직
	
* docker container run - 컨테이너 생성 및 실행  
: 도커 이미지로부터 컨테이너를 생성하고 실행하는 명령 --> 컨테이너를 실행 중 상태로 만들기 위해 사용
```shell
docker container run [options] 이미지명[:태그] [명령] [명령인자...]
docker container run [options] 이미지ID [명령] [명령인자...]
```
	
- example/echo:latest 이미지를 기반으로 컨테이너를 백그라운드 실행 방법
```$ docker container run -d -p 9000:8080 example/echo:latest```
![1](https://user-images.githubusercontent.com/56791347/126893927-7a74e52a-f236-4e72-884f-e2d72963dcdc.png)  
: -p 옵션 사용하여 호스트 쪽 포트 9000을 컨테이너 쪽 포트 8080으로 포트 포워딩함
![2](https://user-images.githubusercontent.com/56791347/126893930-a41e417c-a5e7-4275-bfe1-32b3d47ba5f9.png)    

* docker container run 명령의 인자
        : docker container run 명령에 명령 인자를 전달하면, Dockerfile에서 정의했던 CMD 인스트럭션을 오버라이드 할 수 있음
![3](https://user-images.githubusercontent.com/56791347/126893933-faef104e-3322-4006-acfe-55d7945d0f73.png)
<img width="1209" alt="4" src="https://user-images.githubusercontent.com/56791347/126893937-eba762ba-47ae-4df4-a552-942988908c13.png">
![5](https://user-images.githubusercontent.com/56791347/126893940-358aa3b7-3bad-450b-8f57-349c2d95e360.png)
![6](https://user-images.githubusercontent.com/56791347/126893942-35548f96-b420-4d1a-8b53-ed4e905bfefd.png)


* 컨테이너에 이름 붙이기  
    : NAMES column에 이름이 무작위로 들어간 것을 볼 수 있음 --> 명령어를 이용하여 이름 붙이기 가능    
![7](https://user-images.githubusercontent.com/56791347/126893950-f33b683e-4781-4a1f-987d-6bdbd7990767.png)

    
```$ docker container run --name [컨테이너명] [이미지명]:[태그]```
![8](https://user-images.githubusercontent.com/56791347/126893951-d4017676-55ae-4454-9feb-108fee60b1ad.png)		
<img width="1344" alt="9" src="https://user-images.githubusercontent.com/56791347/126893957-342c331b-23fe-40d5-813d-c996019439fb.png">

		
	
