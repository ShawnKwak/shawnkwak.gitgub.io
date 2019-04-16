---
title: Ghidra Installation
date: 2019-04-16 11:18:11 +09:00
categories: [tips]
tag: [ghidra, reverse engineering, RSA USA 2019, IDA]
toc: true
comments: true
---

# Intro

얼마전 [RSA USA 2019 발표](https://www.rsaconference.com/events/us19/agenda/sessions/16608-come-get-your-free-nsa-reverse-engineering-tool)에서 NSA가 만든 리버스 엔지니어링 툴이 공개 됐다. 

![Ghidra-Installation-01](/assets/posts_img/Ghidra-Installation-01.png){: .align-center}

[발표자료](https://published-prd.lanyonevents.com/published/rsaus19/sessionsFiles/13678/PNG-T09-Come-Get-Your-Free-NSA-Reverse-Engineering-Tool%21.pdf)에서 설명하는 주요 기능은 아래와 같다.

- Collaborative Software Reverse Engineering
- Scalable / Extendable
- Generic Processor Model
- Interactive and non-GUI
- Powerful analysis to Understand Variants
- Undo / Redo

간단히 살펴본 느낌은 확장된 OllyDbg의 인터페이스와 향상된 IDA의 기능들과 버전 트래킹이다. 발표자료에 주요 기능에 대한 설명이 있으니 참고하기 바라며, 해당 툴에 대해 제대로 배우기 위해서는 Help 파일을 봐야한다.

# Installation

[Ghidra 공식 홈페이지](https://ghidra-sre.org/)에서 배포파일을 다운받아 압축을 해제하면 설치가 끝난다.(?) 실행은 윈도우 환경이라면 ghidraRun.bat를 실하면 된다. Linux나 macOS에서는 ghidraRun 파일을 실행하면 된다. 즉, 멀티플랫폼을 지원한다.

# OpenJDK 설정

Ghidra는 OpenJDK 환경에서 개발되고 테스트되었다. 그렇기 때문에 실행환경에서도 OpenJDK를 설치 되어 있어야 한다. 만약 설치되어 있지 않다면 [OpenJDK 11 Download](https://jdk.java.net/11/) 에서 다운받아 압축해제 하면 된다. 또, 추가로 PATH 환경변수 설정을 진행해야 한다.

각 플랫폼 환경에 맞게 PATH 설정을 해도 Ghidra실행시 OpenJDK 경로를 묻는다면 아래 파일에 속성을 추가한다.

1. <GhidraInstallDir/support/launch.properties> 파일에 JAVA_HOME_OVERRIDE 속성 추가

        JAVA_HOME_OVERRIDE=/Users/Shawn/OpenJDK/jdk-11.0.2.jdk/Contents/Home

2. Ghidra 실행
	- <GhidraInstallDir>/ghidraRun.bat 실행(Windows)
	- <GhidraInstallDir>/ghidraRun 실행(Linux or macOS)

아래와 같이 사용자 동의가 뜨면 정상 실행이 된 것이다.

![Ghidra-Installation-02](/assets/posts_img/Ghidra-Installation-02.png){: .align-center}

---

## Reference

[Come Get Your Free NSA Reverse Engineering Tool!](https://www.rsaconference.com/events/us19/agenda/sessions/16608-Come-Get-Your-Free-NSA-Reverse-Engineering-Tool)

[png-t09-come-get-your-free-nsa-reverse-engineering-tool_.pdf](https://www.notion.so/697f0cc1a79e4c71a88a67af611da6e5#e9f1ef31c5fd47a19a0c1924c4ede9cb)

[NationalSecurityAgency/ghidra](https://github.com/NationalSecurityAgency/ghidra)
