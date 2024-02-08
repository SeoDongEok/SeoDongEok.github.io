---
layout: single
title:  "Git 블러그 Typora로 이미지 업로드 방법"
categories: blog
tag: [blog,jekyll,typora]
toc: true
author_profile: false
sidebar:
  nav: "blog"
search: true
typora-root-url: ../
---



<img src="/images/2024-02-07-blog-docker/img1.daumcdn.png" alt="img1.daumcdn" style="zoom:25%;" />



### ㅁ 들어가며

 Git 블러그에서 Typora를 이용해  이미지 업로드를 간편하게 업로드 할 수 있는 방법을 정리하였다.

### ㅁ typora 이미지 설정

![typora_image_config](/images/2024-02-08-git-typora-image/typora_image_config.png)

 ㅇ 설정 > 이미지

 ㅇ 선택: 사용자 정의 폴더로 이미지 복사

 ㅇ 경로설정: ../images/${filename}



### ㅁ md파일 typora-root-url 설정

![md-root-url](/images/2024-02-08-git-typora-image/md-root-url.png)

```
typora-root-url: ../
```

ㅇ typora와 웹상에서 이미지 경로가 차이가 발생하여 root url 설정이 필요하다.

    ㄴ 경로차이는 카테고리 설정으로 /programming/ 경로가 웹상에서는 추가되기 때문이다.
    
    ㄴ 이 설정이 없을 경우 typora에서는 정상적으로 보이나, 웹에서는 상대경로로 이미지를 찾아가지 못한다.

### ㅁ 이미지 드래그 앤 드랍

![drag-drop](/images/2024-02-08-git-typora-image/drag-drop.png)

```
<img src="/images/2024-02-07-blog-docker/img1.daumcdn.png" alt="img1.daumcdn" style="zoom:25%;" />
```

 ㅇ 정상적으로 설정되었다면, 위 경로처럼 /images/...로 설정된다.

 ㅇ typora 입장에서는 

      typora-root-url: ../ 설정에 의해 ../images/... 상대경로가 되어 로컬디렉토리의 파일을 찾아가서 에디터 상에 보여진다.

 ㅇ 웹상에서는 /images/...로 호스트 루트에 기반으로 이미지의 경로를 찾아가서 웹상에 이미지를 보여준다.

### ㅁ 함께 보면 좋은 사이트

ㅇ [번외편. Typora를 활용하여 블로그에 이미지 쉽게 추가하기 (초간단 셋팅법)](https://www.youtube.com/watch?v=R3bMs8wr-jk)