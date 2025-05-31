---
title: 인프런 워밍업 클럽 4기 - DevOps | 1. 쿠버네티스 설치 구간별 상태 확인
date: 2025-06-01
categories:
- Inflearn
tags:
- Inflearn
---

인프런 워밍업클럽 4기 - 데브옵스
쿠버네티스 설치 구간별 상태 확인에 대한 포스팅입니다.

![](/assets/images/inflearn_mission_image/kubernetes_image.jpg)

# 구간별 상태 확인 (1/2)

### [1-1] 내 PC 네트워크 확인
![내 PC 네트워크 확인](/assets/images/inflearn_mission_image/1.png)

### [1-2] 내 PC 자원 확인
![내 PC 자원 확인](/assets/images/inflearn_mission_image/2.png)

### [1-3] VirtualBox 설치 버전 확인
![VirtualBox 설치 버전 확인](/assets/images/inflearn_mission_image/3.png)

### [1-4] Vagrant 설치 버전 확인
![Vagrant 설치 버전 확인](/assets/images/inflearn_mission_image/4.png)

### [1-5] 원격접속(MobaXterm) 설치 버전 확인
![원격접속(MobaXterm) 설치 버전 확인](/assets/images/inflearn_mission_image/5.png)

### [2-1] VirtualBox VM 확인
![VirtualBox VM 확인](/assets/images/inflearn_mission_image/6.png)

### [2-2] 내 VM에 적용된 NAT 확인
![내 VM에 적용된 NAT 확인](/assets/images/inflearn_mission_image/7.png)

### [2-3] 내 VM에 적용된 Host-Only Network 확인
![내 VM에 적용된 Host-Only Network 확인](/assets/images/inflearn_mission_image/8.png)

### [2-4] VirtualBox Host-Only cidr 확인
![VirtualBox Host-Only cidr 확인](/assets/images/inflearn_mission_image/9.png)

### [3-1] Rocky Linux 버전 확인
![Rocky Linux 버전 확인](/assets/images/inflearn_mission_image/10.png)

### [3-2] Hostname 확인
![Hostname 확인](/assets/images/inflearn_mission_image/11.png)

### [3-3], [3-4] Network 확인
![Network 확인](/assets/images/inflearn_mission_image/12.png)

### [3-5] 자원(cpu, memory) 확인
![자원(cpu, memory) 확인](/assets/images/inflearn_mission_image/13.png)
![자원(cpu, memory) 확인](/assets/images/inflearn_mission_image/14.png)

# 구간별 상태 확인 (2/2)

### [4] Rocky Linux 기본 설정

▶ 타임존 설정 확인 
![타임존 설정 확인 ](/assets/images/inflearn_mission_image/15.png)

### [5] kubeadm 설치 전 사전작업

▶ 방화벽 해제 확인 
![방화벽 해제 확인 ](/assets/images/inflearn_mission_image/16.png)

▶ 스왑(swap) 비활성화 확인 
![스왑(swap) 비활성화 확인 ](/assets/images/inflearn_mission_image/17.png)

## [6] 컨테이너 런타임 설치

### [6-1] 컨테이너 런타임 설치 전 사전작업

▶ iptables 세팅
![iptables 세팅](/assets/images/inflearn_mission_image/18.png)

### [6-2] 컨테이너 런타임 (containerd 설치)

▶ docker repo 설정 확인 
![docker repo 설정 확인 ](/assets/images/inflearn_mission_image/19.png)

▶ containerd 설치 확인 
![containerd 설치 확인](/assets/images/inflearn_mission_image/20.png)

▶ 설치 가능한 버전의 containerd.io 리스트 확인
![설치 가능한 버전의 containerd.io 리스트 확인](/assets/images/inflearn_mission_image/21.png)

### [6-3] 컨테이너 런타임 (CRI활성화)

▶ cri 활성화 설정 확인 
![cri 활성화 설정 확인](/assets/images/inflearn_mission_image/22.png)

▶ kubelet cgroup 확인 (configmap)
![kubelet cgroup 확인](/assets/images/inflearn_mission_image/23.png)

▶ kubelet cgroup 확인 (kubelet)
![kubelet cgroup 확인](/assets/images/inflearn_mission_image/24.png)

## [7] kubeadm 설치

▶ repo 설정 확인
![repo 설정 확인](/assets/images/inflearn_mission_image/25.png)

▶ SELinux 설정 확인
![SELinux 설정 확인](/assets/images/inflearn_mission_image/26.png)

▶ kubelet, kubeadm, kubectl 패키지 설치 

🐢 버전 보기
![버전 보기](/assets/images/inflearn_mission_image/27.png)

🐢 상태 보기
![상태 보기](/assets/images/inflearn_mission_image/28.png)

🐢 설정 파일 위치 / 로그 조회
![설정 파일 위치 / 로그 조회](/assets/images/inflearn_mission_image/29.png)

▶ 설치 가능한 버전의 kubeadm 리스트 확인
![설치 가능한 버전의 kubeadm 리스트 확인](/assets/images/inflearn_mission_image/30.png)

## [8] kubeadm으로 클러스터 생성

### [8-1] 클러스터 초기화 (Pod Network 세팅)

▶ 클러스터 상태 확인
![클러스터 상태 확인](/assets/images/inflearn_mission_image/31.png)

### [8-2] kubectl 사용 설정

▶ 인증서 설정 확인
![인증서 설정 확인](/assets/images/inflearn_mission_image/32.png)

### [8-3] CNI Plugin 설치 (calico)

▶ calico pod 설치 및 pod network cidr 적용 확인
![calico pod 설치 및 pod network cidr 적용 확인](/assets/images/inflearn_mission_image/33.png)

### [8-4] Master에 pod를 생성 할 수 있도록 설정

▶ Master Node에 Taint 해제 확인
![Master Node에 Taint 해제 확인](/assets/images/inflearn_mission_image/34.png)

## [9] 쿠버네티스 편의 기능 설치

### [9-1] kubectl 자동완성 기능

▶ kubectl 기능 설정 확인
![kubectl 기능 설정 확인](/assets/images/inflearn_mission_image/35.png)

### [9-2] Dashboard 설치

▶ dashboard 설치 확인
![dashboard 설치 확인](/assets/images/inflearn_mission_image/36.png)

### [9-3] Metrics Server 설치

▶ metrics server 설치 확인
![metrics server 설치 확인](/assets/images/inflearn_mission_image/37.png)