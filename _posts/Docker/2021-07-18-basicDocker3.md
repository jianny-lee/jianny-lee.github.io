---
layout: post
title: "[Docker] 2.도커 컨테이너 배포 - 컨테이너로 애플리케이션 실행하기"
date: 2021-07-18
categories: docker
tags: docker
comments: true
---
> 책 '도커/쿠버네티스를 활용한 컨테이너 개발 실전 입문'을 기반으로 공부 한 내용을 정리  

* 도커 이미지와 컨테이너의 관계  

| 도커 이미지 | 컨테이너를 구성하는 파일 시스템과 실행할 애플리케이션 설정을 하나로 합친 것으로, 컨테이너를 생성하는 템플릿 역할 |
|:----------|:-----------|
| **도커 컨테이너** | **도커 이미지를 기반으로 생성, 파일 시스템과 애플리케이션이 구체화돼 실행되는 상태** |

<img width="1098" alt="1" src="https://user-images.githubusercontent.com/56791347/126053998-5ecb6030-5c3b-4836-87fb-cbdfae91ab7e.png">

  
- 도커 이미지와 도커 컨테이너  
    - 도커 이미지 받아오기 ( $docker image pull 명령어)  
![2_1](https://user-images.githubusercontent.com/56791347/126054021-3e90032b-f1bf-46f2-859f-31c9dfd90799.png)
![2](https://user-images.githubusercontent.com/56791347/126054026-72dc47b4-abd5-454f-bfc8-00f246ad4bff.png)
  
    - 실행 ( $docker container run 명령어)
![3_1](https://user-images.githubusercontent.com/56791347/126054038-0eb3e106-30af-4355-a0de-6862254a033e.png)
![3](https://user-images.githubusercontent.com/56791347/126054039-859b08be-943d-4b98-b6e4-8c24c0411bbf.png)  
 : 옵션을 통해 포트 포워딩이 적용 되어있음. 때문에 도커 실행 환경의 포트 9000을 거쳐 HTTP 요청을 전달 받음
  
    - curl 명령으로 접근하기 ($curl http://localhost:9000/)
 ![1_1](https://user-images.githubusercontent.com/56791347/126054054-cdbeb6bd-ce98-4df1-b458-dcfcdc75e098.png)

  
		
* **간단한 애플리케이션과 도커 이미지 만들기**
    - main.go 파일 만들기  
        ```Go
        package main
        import (
            "fmt"
            "log"
            "net/http"
        )

        func main() {
            http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
                log.Println("received request")
                fmt.Fprintf(w, "Hello Docker!")
            })
            
            log.Println("Start Server")
            
            server := &http.Server{
                Addr: ":8080",
            }
            if err := server.ListenAndServe(); err != nil {
                log.Println(err)
            }
        }
        ```  
  
        - 모든 http 요청에 대해 "Hello Docker!"라는 응답을 보낸다  
        - 포트 8080로 요청을 받는 서버 애플리케이션으로 동작  
        - 클라이언트로부터 요청을 받으면 received request라는 메시지를 표준으로 출력  
  
    - Dockerfile 만들기  
        ```shell
        FROM golang:1.9
            
        RUN mkdir /echo
        COPY main.go /echo
            
        CMD ["go", "run", "echo/main.go"]
        ```
        - FROM 인스트럭션
            → 도커 이미지의 바탕이 될 베이스 이미지를 지정. Dockerfile로 이미지를 빌드할 때 먼저 FROM 인스트럭션에 지정된 이미지를 내려받음
            → FROM에서 받아오는 이미지는 도커 허브 레지스터리에 이미 공개된 것

        - RUN 인스트럭션
            → 도커 이미지를 실행할 때 컨테이너 안에서 실행할 명령어를 정의하는 인스트럭션
				
        - COPY 인스트럭션
            → 도커가 동작 중인 호스트 머신의 파일이나 디렉터리를 도커 컨테이너 안으로 복사하는 인스트럭션
				
        - CMD 인스트럭션
            → 도커 컨테이너를 실행할 때 컨테이너 안에서 실행할 프로세스를 지정
  
* 도커 이미지 빌드하기
        ```docker image build -t 이미지명[:태그명] Dockerfile의_경로```
![4](https://user-images.githubusercontent.com/56791347/126054139-6b32760c-4de4-4bc0-888e-e2f5bda08030.png)
![5](https://user-images.githubusercontent.com/56791347/126054140-a3b9e913-0c84-4bc0-bbdf-c5b65d41ea0f.png)  

  

    - 도커 컨테이너 실행  
► ```docker container run example/echo:latest```
► ```docker container run -d example/echo:latest (백그라운드로 실행)```
![6](https://user-images.githubusercontent.com/56791347/126054141-f7c4800d-a570-470b-83c2-7f8d691819c1.png)
![11](https://user-images.githubusercontent.com/56791347/126054253-e07f05a3-b206-4da4-9a1a-33f174424240.png)
  
- 포트 포워딩  
        ```curl http://localhost:8080/```
    : echo 애플리케이션은 8080 포트를 리스닝하고 있지만, 컨테이너 안에서 한정된 포트임. 때문에 컨테이너 밖에서 온 요청을 컨테이너 안에 있는 애플리케이션에 전달해줘야 함.   
    - 위에 오류가 생기는 경우 해결 방법    
        → 도커 정지   
            ```docker container stop $(docker container ls --filter "ancestor=example/echo" -q)```  
        → 호스트 포트 9000을 포트 8080에 연결하여 포트 포워딩  
            ```docker container run -d -p 9000:8080 example/echo:latest```  
        → GET 요청 보내기  
            ```curl http://localhost:9000/```
![13](https://user-images.githubusercontent.com/56791347/126054307-80a6c600-cebc-449c-b4d1-f88d7c922a40.png)