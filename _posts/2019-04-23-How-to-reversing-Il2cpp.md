---
title: How to reversing Il2cpp
date: 2019-04-23 10:57:39 +09:00
categories: [tech]
tag: [android, unity, il2cpp, reversing, game, il2cppdumper]
toc: true
comments: true
---

# Intro

Unity에서 Il2cpp로 빌드된 바이너리를 분석할때 디버그 정보를 포함시킬 수 있다면 분석에 큰 도움이 될 것이다.

해당 문서에서는 이런 분석을 도와주는 Il2CppDumper의 사용법을 소개한다.

# Il2cpp

C#으로 작성된 Unity 게임은 공식적으로 보안성 향상과 iOS 64bit 지원을 명목으로 Il2cpp로 빌드하는 것을 권장한다. 실용성에 대한 이야기는 잠시 접어두고 쉽게 생각하면 바이너리를 C# → IL → C++로 컴파일된 것으로 변경한 것이다.

![How-to-reversing-Il2cpp-01](/assets/posts_img/How-to-reversing-Il2cpp-01.png){: .align-center}

# Il2CppDumper

C++로 컴파일된 Il2cpp에 디버그 정보를 포함시키는 방법으로는 
GitHub에 공개된 [Il2CppDumper](https://github.com/Perfare/Il2CppDumper)를 이용하면 쉽게 가능하다.

지원하는 기능은 아래와 같다.

- ELF, ELF64, Mach-O, PE format 지원
- global-metadata 16, 19-24 버전 지원
- .NET Metadata에 포함된 types, fields, properties, methods, attributes 추출 가능
- IDA 스크립트 자동 생성
- Dummy DLL을 생성하여 .NET 디컴파일러로 확인 가능

## Il2CppDumper Usage

[Il2CppDumper release page](https://github.com/Perfare/Il2CppDumper/releases)에서 최신 버전의 Il2CppDumper.exe를 다운받아 실행할 수 있다. Il2CppDumper.exe를 실행하면 2개의 파일 입력을 받는다.

첫 번째로는 il2cpp 실행파일을 선택한다. il2cpp 실행파일은 ELF나 Mach-O, PE 포맷으로 존재할 수 있으니 분석 대상 앱(APK or IPA)따라 대상을 선택하면 된다.

두 뻔재로는 global-metadata.dat 파일을 선택한다. 보통 Data/Managed/Metadata 등의 경로에 존재한다.

파일 선택을 마치면 CMD창에서 추출 모드를 선택해야 한다. 권장하는 모드는 '4.Auto(Plus)'이다.  나머지 모드에서는 Android에 의존적이거나 몇 가지 수작업이 필요하다. 자세한 내용은 [Extraction Modes](https://github.com/Perfare/Il2CppDumper#extraction-modes)에서 확인 가능하다.

![How-to-reversing-Il2cpp-02](/assets/posts_img/How-to-reversing-Il2cpp-02.png){: .align-center}

추출 작업이 완료되면 아래와 같은 output file이 생성된다.

- dump.cs : C# pseudocode로 텍스트 편집기로 볼 수 있다.
- script.py : IDA와 IDA Pyhon을 이용해 IDA에서 로딩할 수 있다.
- DummyDll : .NET 디컴파일러로 메타데이터 정보를 확인할 수 있다. 코드는 포함되어 있지 않다.

# Load to IDA with script

il2cpp 파일을 IDA통해 분석을 시작한다. 분석이 완료 되면  File - Script file - Script.py 선택하여 디버그 정보를 로딩할 수 있다.

![How-to-reversing-Il2cpp-03](/assets/posts_img/How-to-reversing-Il2cpp-03.png){: .align-center}