---
title: "[github] 깃헙(github) 기본 사용법 " 
categories:
  - programming
tags:
  - github
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# 깃헙(github) 기본 사용법

참고: [소스트리를 이용해 깃헙 작업흐름 알아보기](https://losskatsu.github.io/programming/git-path/)

깃헙 사이트 [github.com](github.com) 에 가서 가입 후 다음을 진행

## 1. Git 설치 

깃 설치 전 사전 설치 프로그램 설치 후 깃 설치.

```bash
// 페도라(Fedora)인 경우
$ sudo dnf install git-all

// 우분투 계열의 데비안(Debian)인 경우
$ sudo apt install git-all
```

자세한 사항은 아래 링크 참조

[깃 설치하는 법](https://git-scm.com/book/ko/v1/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EC%84%A4%EC%B9%98)
<br />

## 2. 초기 설정

깃 설치 후 가장 먼저 해야할일은 아이디와 이메일 주소 등록이다. 
예를들어 아이디가 abcde 이고, 이메일이 asdf@asdf.net 인 경우, 

```bash
$ git config --global user.name "abced"
$ git config --global user.email asdf@asdf.net
```

설정확인

```bash
$ git config --list
```

유저네임을 확인하고 싶다면

```bash
$ git config user.name
```

## 3. 로컬 저장소 설정

특정 폴더로 이동 후 해당 폴더를 버전 관리 하고 싶다면 그 폴더를 저장소로 만들자.

```bash
// 현재 디렉터리를 로컬 저장소로 지정 
$ git init
```

이후 해당 폴더에서 ls -al 을 입력해보면 .git이라는 디렉터리가 생성되었음을 볼 수 있고, 
그 디렉터리 안에서 버전 관리가 되고 있다. 

참고사항으로 만약 로컬 저장소를 취소하고 싶다면 아래와 같이 하자

```bash
// 현재 디렉터리를 로컬 저장소에서 취소 
$ rm -r .git
```

로컬 저장소의 현재 상태를 보고 싶다면 아래 참조. 

```bash
// 로컬 저장소의 현재 상태 
$ git status
```

## 4. 원하는 파일을 로컬 저장소로 올려봅시다.

그럼 해당 디렉터리 안에 있는 파일들을 인터넷 상에 있는 깃헙 저장소에 올려보자. 
만약 a.cpp, b.cpp, c.cpp이라는 파일을 올리고 싶다면 add를 통해서 로컬 저장소에 올리고 커밋합시다. 

```bash
$ git add  a.cpp   b.cpp   c.cpp
$ git commit -m "20190112"

//참고
//해당 디렉토리내 파일 전부 올리고 싶을때 
$ git add .
$ git commit -m "messege"
```

이 때 -m 옵션은 해당 커밋에 대한 메시지이다. 

참고로 커밋 로그를 보고 싶다면 아래와 같이 입력

```bash
// 커밋 이력 조회
$ git log

// 특정 파일의 변경 커밋 조회
$ git log -- abcd.py
```

## 5. 원격 저장소 연결 및 push

커밋을 했으니 인터넷 어디에 올릴 것인지 등록해야한다. 
만약 내가 올리고자 하는 저장소 주소가 https://github.com/abc/abc.git 라면

```bash
$ git remote add origin https:github.com/abc/abc.git
$ git push -u origin master
```

여기서 origin 이라는 것은 단축이름이다. 딱히 의미가 있는건 아니다. 
본인이 짓고 싶은 이름으로 지으면 됨. 여기까지가 깃헙 저장소에 파일 올리는 법.
위에서 u 옵션을 사용하면 최초에 한번만 <저장소명> <브랜치명>을 쓰고, 
두 번째 부터는 인자를 생략할 수 있습니다. 
만약 현재 연결된 원격저장소를 확인하고 싶다면 


## 참고1. 브랜치(branch) 관련 작업

```bash
// 브랜치 확인
$ git branch

// 브랜치 생성
$ git branch abcd

// abcd 브랜치를 efgh 브랜치로 바꿈
$ git branch -m abcd efgh

// 브랜치 삭제
$ git branch -d abcd
```

## 참고2. 체크아웃(checkout) - 로컬 디렉토리 소스를 해당 브랜치로 변경

제가 현재 작업중인 디렉터리의 소스코드를 특정 브랜치 또는 커밋으로 변경하는 방법

```bash
// 작업중인 디렉터리의 코드를 특정 브랜치로 변경
$ git checkout abcd

// 작업중인 디렉터리의 코드를 특정 커밋으로 변경
$ git checkout [commit ID]

// 특정 파일을 다른 브랜치 또는 커밋 상태로 롤백
$ git checkout [롤백 하고 싶은 commit ID] -- [파일경로]

// 브랜치 생성 및 체크아웃을 동시에
$ git checkout -b develop
```

## 참고3. 병합(merge)

```bash
$ git checkout master
$ git merge develop
```

## 참고4. 깃 리모트를 변경하고 싶을때

기존 리포지토리 remote 제거

```bash
$ git remote remove origin
```

새로운 리포지토리 remote 추가(예: https://github.com/abc/def.git)

```bash
$ git remote add origin https://github.com/abc/def.git
```

현재 리포지토리 확인법

```bash
$ git remote -v
```

## 참고4. 저장소에 잘못올린 파일을 지우고 싶을때

a.cpp라는 파일을 지우고 

```bash
$ git rm --cached a.cpp
$ git commit -m "itsmistake"
$ git push origin master
```

## 브랜치(branch) 따서 원격 저장소에 올리기

브랜치 확인. 현재는 마스터 브랜치 하나만 있는 것을 알 수 있다.

```bash
$ git branch
* master
```

브랜치 생성. modify01 이라는 브랜치를 만들자.

```bash
$ git branch modify01
  modify01
* master
```

방금 만든 modify01 브랜치로 이동하자.

```bash
$ git checkout modify01
* modify01
  master
```

수정이 끝난 파일(new01.txt)을 add 하자.

```bash
$ git add new01.txt
```

commit 하자

```bash
$ git commit -m "수정했습니당"
```

원격 저장소로 올리자. 현재 내가 만든 브랜치는 내 로컬에만 존재하므로 
원격 저장소에도 동일한 브랜치가 필요하다. 따라서 아래 명령처럼 --set-upstream 옵션을 걸어주면 
원격 저장소에도 동일하게 modify01 브랜치가 생성되어 있다.

```bash
$ git push --set-upstream origin modify01
```

(아래는 확인 필요)

원격 저장소의 master 브랜치로 이동

```bash
$ git checkout origin/master
```

머지(merge)

```bash
$ git merge origin/modify
$ git push
$ git branch -d origin/modify
```

# 실제 테스트 

일단 작업을 원하는 폴더로 가자.
그리고 아래와 같이 git clone 명령어를 이용하면 폴더를 통째로 들고 온다.
즉 폴더이름을 내가 미리 만들 필요 없다는 소리다.
폴더 이름은 깃 레퍼지토리 이름과 동일하다. 
해당 폴더에 들어가면 .git 파일도 생성되어있다.
(git init 명령 안쳐도 된다는 뜻이다.)
(아마 remote도 설정되어 있을 것이다.)

```bash
$ git clone "http주소"
```


로컬에서 작업할 브랜치 생성

```bash
$ git branch mody01
$ git checkout mody01
```
만약 위 문장을 한줄로 치고 싶다면 아래와 같이 입력하자.

```bash
$ git checkout -b mody01
```

리모트 저장소에도 똑같이 브랜치를 만들어 줍시다.

```bash
$ git push origin mody01
```

로컬과 리모트 저장소의 브랜치를 연동시킵니다. (이건 사실 안해도 됨) 

```bash
$ git branch --set-upstream-to origin/mody01
```

작업을 합니다. test01.txt라는 파일을 만들었다고 칩시다.
올리고 커밋합시다.

```bash
$ git add .
$ git commit -m "수정"
```

push!

```bash
$ git push origin mody01
```

홈피가서 pull request 버튼 누르고, merge하고 브랜치 삭제까지하자.

그리고 로컬에서도 merge 해줌

```bash
$ git checkout main
$ git merge mody02
```

여기까지.

만약 추후에 인터넷상에서 업데이트 된 코드 가져오고 싶다면?

```bash
$ git pull origin main
```

그리고 브랜치 따고 작업 작업....이하 동일 
