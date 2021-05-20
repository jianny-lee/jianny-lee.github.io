---
layout: post
title: "[Error] curl: (7) Failed to connect to localhost port 8080: Connection refused"
date: 2021-05-20
categories: Containers
comments: false
---

## 포트 포워딩이 실패한 경우
<img width="545" alt="스크린샷 2021-05-20 22 50 41" src="https://user-images.githubusercontent.com/56791347/118990397-cfba9080-b9bd-11eb-8484-c0a81e073a2b.png">

echo 애플리케이션은 8080 포트를 리스닝하고 있지만, 컨테이너 안에서 한정된 포트임. 때문에 컨테이너 밖에서 온 요청을 컨테이너 안에 있는 애플리케이션에 전달해줘야 함.
1) 실행중인 컨테이너 정지
```shell
docker container stop $(docker container ls --filter "ancestor=example/echo" -q)
```
2) 호스트 포트 9000을 포트 8080에 연결하여 포트 포워딩
```shell
docker container run -d -p 9000:8080 example/echo:latest
```
3) GET 요청 보내기
```shell
curl http://localhost:9000/
```