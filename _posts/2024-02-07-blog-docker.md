---
layout: single
title:  "Jekyll 블로그 Docker로 만들기"
categories: blog
tag: [blog, jekyll, docker]
toc: true
author_profile: false
sidebar:
  nav: "blog"
search: true
typora-root-url: ../
---



<img src="/images/2024-02-07-blog-docker/img1.daumcdn.png" alt="img1.daumcdn" style="zoom:25%;" />



### ㅁ 들어가며

무료 개인 사이트를 구축하기 위해 Jekyll로 기동하는 minimal-mistakes 테마는 개인 블러그들 사이에서 자주 볼 수 있다. 나의 peterica.github.io도 이 테마를 이용하여 사이트를 운영 중인데, 로컬 환경에서 다른 개발과 충돌이 일어날 때가 많았다. 그래서  minimal-mistakes 테마를 git clone하여 docker로 만드는 과정을 정리하였다.

#### ㅁ Git Clone

```
$ git clone https://github.com/mmistakes/minimal-mistakes.git
```

#### ㅁ Dockerfile 작성

```
# 폴더 이동
$ cd ./minimal-mistakes

# Dockerfile 작성
$ cat Dockerfile
FROM ruby:3.0

WORKDIR /srv/jekyll

VOLUME /srv/jekyll
```

 ㅇ 최초 ruby와 워크경로만 지정하여 컨테이너를 구성한다.

#### ㅁ Docker build

```
# blog 이름으로 이미지를 만든다.
$ docker build -t blog .
[+] Building 44.9s (7/7) FINISHED                                                                                                                                                             docker:desktop-linux
 => [internal] load build definition from Dockerfile                                                                                                                                                          0.0s
.....................                                                                                                                                                                  0.0s
View build details: docker-desktop://dashboard/build/desktop-linux/desktop-linux/w63krlkr4x1ab72wt9t42926m

# 이미지 확인
$ docker image ls | grep blog
blog                           latest    975c3049afdb   2 hours ago     881MB
```

 ㅇ 이미지를 빌드업한다. 

#### ㅁ docker blog 컨테이너 bundle install 수행

```
# minimal-mistakes 현재 폴더 기준으로 bundle install한다.
$ docker run --volume="./:/srv/jekyll" -it blog bundle install
```

 ㅇ jekyll를 하기 위해서는 bundle install 과정이 필요하다. 

 ㅇ 도커환경에서 빌드를 완료하고 이를 다시 도커이미지로 만들어야 한다.

![bundle_install](/images/2024-02-07-blog-docker/bundle_install.png)

 ㅇ 정상적으로 bundle install이 완료되었다.

#### ㅁ install된 파일을 합쳐 이미지화

```
# bundle config를 지정하여 bundle install을 하기 위해 
# Dockerfile 수정
$ cat Dockerfile
FROM ruby:3.0

RUN bundle config --global frozen 1

WORKDIR /srv/jekyll

COPY Gemfile Gemfile.lock minimal-mistakes-jekyll.gemspec ./

RUN bundle install

VOLUME /srv/jekyll

# 빌드
$ docker build -t blog .
```

 ㅇ 빌드까지 완료된 이미지를 완성하였다.

 ㅇ 이제 실행을 위한 docker-compose.yml을 작성한다.

### ㅁ Docker 실행을 위한 docker-compose.yml 생성

```
$ cat docker-compose.yml
version: "3.0"

services:
  dev:
    container_name: blog
    image: blog
    command: ["jekyll", "serve", "--incremental", "--livereload"]
    ports:
      - "4000:4000"
      - "35729:35729"
    volumes:
      - ./:/srv/jekyll
```

### ㅁ \_config.yml에 서버 port와 host 추가

```
port: 4000
host: "0.0.0.0"
```

### ㅁ docker run

```
# docker를 실행한다.
# 로그를 바로 확인하기 위해 -d(백그라운드) 옵션은 추가하지 않았다.
$ docker-compose up

# 백그라운드 모드 기동
$ docker-compose up -d
[+] Running 1/1
 ✔ Container minimal-mistakes-dev-1  Started
```

#### ㅁ 접속테스트

 ![test_page](/images/2024-02-07-blog-docker/test_page.png)

 ㅇ localhost:4000접속 테스트를 진행하였다.

### ㅁ 함께 보면 좋은 사이트

ㅇ [Minimal Mistakes github](https://mmistakes.github.io/minimal-mistakes/)