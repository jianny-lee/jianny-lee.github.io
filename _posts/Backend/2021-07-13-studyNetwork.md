---
layout: post
title: "[Web] Network"
date: 2021-07-13
categories: backend
tags: web
comments: false
---

이번 네트워크 내용 정리는 **생활코딩 WEB2-Home Server강의**를 기반으로 정리했다.
아무래도 짧게 진행되는 강의라서 좀 많은 내용들이 생략된건 사실이지만,,,
자세한건 나중에 깊게 다루고 우선은 강의 들은 내용들에 대해서 내 나름대로 간단히 정리해봤다.

## Network

#### Router  
- IP Address : 다른 컴퓨터와 통신할 수 있게 해주는 주소  

- WAN(wide area network)  
    - 전세계 누구나 접속 가능 (public IP Address)  

- LAN(local area network)  
    - LAN에 연결되는 것들은 같은 영역대의 ip를 부여받음  
    - Gateway Address(Router Address)  
    - private IP Address  
  
#### NAT  
- Network Address Translation  
- 요청한 IP를 LAN을 통해서 ip가 입력되고 NAT를 통해 public IP로 변경하여 WAN으로 통신을 요청  
- 때문에 인터넷을 나갈 때만 공인 주소(유일한 IP 주소)를 가지고 나가는 방식  

#### IP 주소 알아내는 법  
- 맥은 '시스템 설정' -> '네트워크' -> '고급' -> 'TCP/IP'로 들어가기  
- 또는, terminal에서 ifconfig라고 입력하면 router 주소와 컴퓨터의 ip 주소를 찾을 수 있음  
  
#### Port  
- ip가 통신하고자 하는 공간(자리)  
  
#### Port Forwarding  
- 어떤 포트로 길을 열어줘야 하는가 확인 후, 그 포트로 전달해주는 방식  
  
#### Dynamic IP Address  
- 사용자가 사용 가능한 IP를 자동으로 새롭게 부여하는 방식  
  
#### Static IP Address  
- 고정 IP 주소로 사용자에게 전용으로 부여되는 인터넷 주소  
- 변하지 않고 사용됨  
  
#### DHCP(Dynamic Host Configuration Protocol)  
- IP와 같은 식별자는 절대 같은 주소를 부여하면 안됨