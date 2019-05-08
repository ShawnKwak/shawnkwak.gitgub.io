---
title: Sublime execute on OSX
date: 2019-05-08 14:12:47 +09:00
categories: [tips]
tag: [osx, sublime, subl, install]
toc: true
comments: true
---

# Intro

서브라임2에서는 기본적으로 커맨드라인 툴로 'subl'을 제공한다.

    Shawn@ShawnKwakui-MacBook-Pro  ~  ls -l /Applications/Sublime\ Text.app/Contents/SharedSupport/bin
    total 104
    -rwxr-xr-x@ 1 Shawn  admin  50064  5 14  2018 subl

해당 툴의 사용법과 설명은 [공식 홈페이지](http://www.sublimetext.com/docs/2/osx_command_line.html) 에서 확인할 수 있다.

# 설치

공식 홈페이지에서 문서를 보면 알겠지만, Sublime Text 2에서 제공해주는 커맨드라인 툴의 이름은 'subl'로 쉽게 잘 연상되지도 않으며 기억하기도 어렵다. 그리고 PATH설정도 되지 않아서 사용하기가 번거롭다.

해당 문서에서는 이와 같은 문제점을 간단히 해결할 수 있는 설정 방법을 제공한다.

## 심볼링 링크 설정

'subl'에 대한 심볼링 링크를 /usr/local/bin에 'sublime'으로 추가한다.

    ln -s /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl /usr/local/bin/sublime

## PATH 추가

사용하고 있는 쉘의 프로파일에 PATH를 추가한다.

    export PATH=/usr/local/bin:$PATH

보통의 bash의 경우 ~/.bash_profile 을 변경하면 되고 zsh의 경우 ~/.zshrc 를 변경하면 된다. 변경한 파일을 다시 로드하기 위해 터미널을 재시작하거나 아래 커맨드를 실행시킨다.

    source ~/.bash_profile
    or
    source ~/.zshrc

# 실행

아래 커맨드가 정상적으로 실행되는지 확인한다.

    sublime filename (sublime으로 파일 열기)
    sublime foldername (sublime으로 폴더 열기)
    sublime . (현재 폴더 열기)