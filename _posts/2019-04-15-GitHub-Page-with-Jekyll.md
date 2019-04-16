---
title: GitHub Page with Jekyll
date: 2019-04-15 16:14:01 +09:00
categories:
  - "tips"
tag:
  - "github" 
  - "blog"
  - "jekyll"
toc: true
comments: true
---

## [Quick-Start Guide](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)

### [GitHub Pages 생성하기](https://pages.github.com/)

GitHub에서 설명하는 가이드에 따라 페이지를 생성한다.

### [minimal-mistakes 테마 fork하기](https://github.com/mmistakes/minimal-mistakes)

Jekyll에서 제공하는 [여러 테마](http://jekyllthemes.org/)중에서 원하는 테마의 깃 저장소를 fork한다.

### 저장소 설정

fork한 저장소의 이름을 [username].github.io 형태로 변경한다.

### 저장소 내 필요없는 파일 삭제

- `.editorconfig`
- `.gitattributes`
- `.github`
- `/docs`
- `/test`
- `CHANGELOG.md`
- `minimal-mistakes-jekyll.gemspec`
- `README.md`
- `screenshot-layouts.png`
- `screenshot.png`

## [Customization](https://mmistakes.github.io/minimal-mistakes/docs/configuration/)

1. Configuration : _config.yml 파일을 사용자 구성에 맞게 변경하고 필요한 옵션들을 활성화 시킨다.
2. Navigation Setting : 페이지 상단 네비게이션 메뉴 활성화
3. Layouts Setting : 기본 포스트 레이아웃과 페이지 레이아웃 설정