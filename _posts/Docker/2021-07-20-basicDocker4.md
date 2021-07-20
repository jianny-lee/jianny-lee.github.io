---
layout: post
title: "[Docker] 2.도커 컨테이너 배포 - 도커 이미지 다루기"
date: 2021-07-20
categories: docker
tags: docker
comments: true
---
> 책 '도커/쿠버네티스를 활용한 컨테이너 개발 실전 입문'을 기반으로 공부 한 내용을 정리  

* 도커 사용법  
    - 이미지를 대상으로   
    - 컨테이너를 대상으로  
	 
     		  
* 도커 이미지란?  
    - 도커 컨테이너를 만들기 위한 템플릿  
    - 운영체제로 구성된 파일 시스템 + 애플리케이션 + 의존 라이브러리 + 실행 환경의 설정 정보 => 아카이브!  
    - Dockerfile은 이미지를 구성하는 순서를 기술한 코드라서 Dockerfile 자체가 이미지라고 할 수 없음  
    - "도커 이미지를 빌드한다" == 컨테이너의 템플릿 역할을 이미지를 만드는 과정  
  
  
* docker image buile - 이미지 빌드  
    : Dockerfile에 기술된 구성을 따라 도커 이미지를 생성하는 명령어  
    ```$docker image build -t 이미지명[:태그명] Dockerfile의_경로 ```  
            ==> -t 옵션 : 이미지명과 태그명을 붙이는 것  
            ==> -f 옵션 : 파일명으로 된 Dockerfile을 사용할 때 사용   

    ```$docker image build -f Dockerfile-test -t example/echo:latest .```
            ==> --pull 옵션 : 매번 베이스 이미지를 강제로 새로 받아온다    
                레지스트리에서 받아온 도커 이미지는 일부러 삭제하지 않는 한 호스트 운영 체제에 저장되기 때문에 이미지를 빌드시 확실히 최신 베이스 이미지를 사용하고 싶다면 "--pull=true" 옵션을 사용하기  
                도커 허브 등 레지스터리에서 최신 버전이 있는지를 확인하고 빌드해서 속도 면에서는 떨어지기 때문에, 실무에서는 latest로 지정하는 것을 피하고 태그로 지정한 베이스 이미지를 사용  
    ```$docker image build --pull=true -t example/echo:latest .```


* docker search - 이미지 검색  
    - 도커 허브 : 도커 이미지 레지스터리  
    ```$ docker search [options] 검색_키워드```
    ![0](https://user-images.githubusercontent.com/56791347/126357817-321c73e1-45e4-4a39-9130-fe3437c475d0.png)
		: 첫번째 repository는 공식 repository라서 네임스페이스가 생략되어있음 --> 일률적으로 library  


* docker image pull - 이미지 내려받기  
    ```$docker image pull [options] 레포지토리명[:태그명]```
        - 인자로 지정한 레포지토리명과 태그명은 도커 허브에 이미 존재하는 것이어야 함  
        -  이 명령어로 내려받은 이미지는 그대로 도커 컨테이너를 생성하는 데 사용할 수 있음.  
	 

* docker image ls - 보유한 도커 이미지 목록 보기  
    : 현재 호스트 운영 체제(도커 데몬이 동작하는 호스트 환경)에 저장된 도커 이미지의 목록을 보여준다.  
    ```$ docker image ls [options] [리포지토리[:태그]]```  
    ![1](https://user-images.githubusercontent.com/56791347/126357819-8d989d3c-6ffa-40af-8cfe-8e7ad7e87618.png)
    : IMAGE ID는 이미지에 대한 식별자(버전 넘버 역할)--> CONTAINER ID(컨테이너를 구분하는 것)와는 별개의 것이므로 혼동하지 말기  
	

* docker image tag - 이미지에 태그 붙이기  
    : 도커 이미지의 특정 버전에 태그를 붙일 때 사용  
    ◊ 도커 이미지의 버전  
        - 애플리케이션을 수정하고 이미지를 빌드하면 매번 다른 이미지가 됨  
        즉, 수정 후에는 다른 IMAGE ID 값이 할당되는 것  
        COPY 대상이 되는 파일의 내용이 바뀌어도 IMAGE ID 값이 바뀜  
        \<none>은 이전에 있던 도커 이미지의 잔재  

    ◊ 이미지 ID에 태그 부여하기  
    ```$docker image tag 기반이미지명[:태그] 새이미지명[:태그]```  
        ex) ```$docker image tag example/echo:latest example/echo:0.1.0```
    : 이미지 ID에 태그를 부여하면 두개의 태그 이미지가 생성되지만 둘 다 같은 이미지를 가리킴  
  

* docker image push - 이미지를 외부에 공개하기  
    : 현재 저장된 도커 이미지를 도커 허브 등의 레지스터리에 등록하기 위해 사용  
    ```$docker image push [options] 리포지토리명[:태그]```
    ![2](https://user-images.githubusercontent.com/56791347/126357805-442cc85b-a205-47a0-96d5-0848d2ecfc67.png)