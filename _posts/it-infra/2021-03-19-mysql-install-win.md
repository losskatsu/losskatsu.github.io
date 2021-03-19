---
title: "[Infra] MySQL 윈도우 10에 설치하기" 
categories:
  - it-infra
tags:
  - it-infra
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# MySQL 윈도우 10에 설치하기

### 참고 링크  

* [MySQL 간단 정리, 우분투, 맥에 설치 하기](https://losskatsu.github.io/it-infra/mysql-index/)
* [파이썬, MySQL 연동](https://losskatsu.github.io/programming/py-db-conn/)
* [데이터베이스에서 널(null)과 공백의 차이](https://losskatsu.github.io/it-infra/db-null/)

## MySQL 다운로드 받기

<center><img src="/assets/images/infra/mysql-win/mysql01-02.JPG" width="800"></center>

먼저 [https://mysql.com](https://mysql.com) 에 접속해서 화면 상단의 DOWNLOADS를 클릭합니다.

<center><img src="/assets/images/infra/mysql-win/mysql02-02.JPG" width="800"></center>

“MySQL Community(GPL) Downloads”를 클릭합니다. 

<center><img src="/assets/images/infra/mysql-win/mysql03-02.JPG" width="800"></center>

“MySQL Community Server”를 클릭합니다.

<center><img src="/assets/images/infra/mysql-win/mysql04-02.JPG" width="800"></center>

그림과 같이 “Go to Download Page”를 클릭합니다. 

<center><img src="/assets/images/infra/mysql-win/mysql05-02.JPG" width="800"></center>

용량이 좀 더 큰 아래쪽 다운로드 버튼을 클릭합니다. 

<center><img src="/assets/images/infra/mysql-win/mysql06-02.JPG" width="800"></center>

“No thanks, just start my download”를 클릭하면 다운로드가 시작됩니다.



## MySQL 설치하기 

<center><img src="/assets/images/infra/mysql-win/mysql07-02.JPG" width="800"></center>

다운로드 받은 설치 파일을 실행하면 [그림 8-7]과 같은 화면이 나옵니다. “Next”버튼을 클릭합니다.

<center><img src="/assets/images/infra/mysql-win/mysql08-02.JPG" width="800"></center>

“Execute” 버튼을 누르면 설치가 시작됩니다. 

<center><img src="/assets/images/infra/mysql-win/mysql09-02.JPG" width="800"></center>

설치가 완료되면 “Next”버튼이 활성화 됩니다. “Next”를 클릭합니다. 

<center><img src="/assets/images/infra/mysql-win/mysql10-02.JPG" width="800"></center>

다음 화면은 설정 화면입니다. “Next”를 눌러줍니다. 

<center><img src="/assets/images/infra/mysql-win/mysql11-02.JPG" width="800"></center>

네트워크 설정 화면입니다. MySQL의 기본 포트는 3306으로 설정 되어 있는데, 
만약 변경하고 싶다면 해당 부분을 수정합니다. 저는 기본 포트 3306을 사용하겠습니다. 
그리고 “Next”를 클릭합니다. 

<center><img src="/assets/images/infra/mysql-win/mysql12-02.JPG" width="800"></center>

인증 방법을 설정하는 단계입니다. “Next”를 클릭합니다. 

<center><img src="/assets/images/infra/mysql-win/mysql13-02.JPG" width="800"></center>

비밀번호를 설정하는 화면입니다. 비밀번호를 정하고 “Next”를 입력합니다. 

<center><img src="/assets/images/infra/mysql-win/mysql14-02.JPG" width="800"></center>

Next를 클릭합니다. 

<center><img src="/assets/images/infra/mysql-win/mysql15-02.JPG" width="800"></center>

Excecute를 클릭합니다. 

<center><img src="/assets/images/infra/mysql-win/mysql16-02.JPG" width="800"></center>

설정 적용이 완료되면 Finish 버튼이 활성화 되는데, 클릭합니다.


<center><img src="/assets/images/infra/mysql-win/mysql17-02.JPG" width="800"></center>

다시 설정화면으로 돌아오게 되는데 Next 버튼을 클릭합니다. 

<center><img src="/assets/images/infra/mysql-win/mysql18-02.JPG" width="800"></center>

라우터 설정화면인데 따로 설정할건 없으며 Finish 버튼을 클릭합니다. 

<center><img src="/assets/images/infra/mysql-win/mysql19-02.JPG" width="800"></center>

다시 설정화면으로 돌아오는데 Next 버튼을 눌러줍니다.

<center><img src="/assets/images/infra/mysql-win/mysql20-02.JPG" width="800"></center>

서버 연결 설정을 하는 부분입니다. 
앞서 정한 비밀번호를 입력하고 Check 버튼을 클릭하면 옆에 체크 표시가 나타납니다. 
Next버튼을 클릭합니다. 

<center><img src="/assets/images/infra/mysql-win/mysql21-02.JPG" width="800"></center>

Execute 버튼을 눌러줍니다. 

<center><img src="/assets/images/infra/mysql-win/mysql22-02.JPG" width="800"></center>

Finish 버튼이 활성화되면 클릭해줍니다. 

<center><img src="/assets/images/infra/mysql-win/mysql23-02.JPG" width="800"></center>

Next를 클릭합니다. 

<center><img src="/assets/images/infra/mysql-win/mysql24-02.JPG" width="800"></center>

설치 마지막 단계입니다. Finish 버튼을 누르면 MySQL설치가 끝나게 됩니다. 

<center><img src="/assets/images/infra/mysql-win/mysql25-02.JPG" width="800"></center>

스크립트 창이 나타나는데 창을 닫아줍니다. 

<center><img src="/assets/images/infra/mysql-win/mysql26-02.JPG" width="800"></center>

MySQL Workbench가 실행되는데 
MySQL Workbench는 MySQL을 GUI(Graphical User Interface) 환경에서 좀 더 편하게 사용하기 위한 프로그램입니다. 
Local instance MySQL80을 클릭하고 비밀번호를 입력한후 OK버튼을 클릭합니다.

<center><img src="/assets/images/infra/mysql-win/mysql27-02.JPG" width="800"></center>

위와 같은 화면이 나타난다면 성공적으로 설치된 것입니다. 
